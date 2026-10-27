# GitHub Stars 合并报告 - 2026-10-26

**合并日期**: 2026-10-27
**监控日期**: 2026-10-26
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


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2265
- **最后更新**: 2026-10-26T12:02:51Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: YLlllllllllll, Coach257, Bin Jia

## AI分析总结

## ByteDance-Seed/VeOmni 昨日提交分析

### 1. 主要更新类型

- **Bug修复**：修复 dense attention 模型中 `prepare_dense_attention_inputs` 的不一致问题
- **性能优化**：在 Ascend 平台上复用 compact QSA 整数元数据以减少计算开销；简化 CI 加速器测试用例同时保留关键覆盖率
- **功能新增**：为 MoE 训练添加 deepgemm FP8 支持
- **重构/CI**：统一接口、精简测试流程

### 2. 关键变更点与项目方向的关系

VeOmni 的核心定位是"以模型为中心的分布式训练配方库"，支持任意模态的大规模训练。本次提交从以下维度与项目方向紧密关联：

- **`bb08aae`** 统一了所有 dense attention 模型的输入准备函数，消除了不同模型间的接口分裂，直接服务于项目"标准化分布式训练配方"的愿景，降低维护成本并提升可扩展性。
- **`798ee98`** 针对华为 Ascend NPU 平台进行 QSA 元数据的整数化复用优化，体现了项目对**多硬件后端**的持续适配，这是"任意模态、任意硬件"训练基础设施的关键一环。
- **`a8b348e`** 引入 DeepGEMM 的 FP8 MoE 训练支持，深度契合 MoE 架构在大规模模型训练中的核心地位，同时 FP8 量化训练是当前降低显存和提升吞吐的主流技术路线。
- **`6e78605`** 精简 CI 加速器测试用例，减少流水线开销同时保证覆盖度，属于工程效率优化，有助于加快迭代节奏。

### 3. 对项目的影响和潜在意义

- **架构一致性提升**：统一 attention 输入接口使后续新增模型可以遵循单一规范，减少"配方"间的碎片化。
- **多平台竞争力增强**：Ascend 优化使 VeOmni 在国产芯片生态中更具实用性，对于企业级部署和合规场景具有战略意义。
- **训练效率显著提升**：DeepGEMM + FP8 MoE 的结合可在不牺牲精度的前提下大幅提升 MoE 模型的训练吞吐，降低大规模训练的成本门槛。
- **CI 健壮性改善**：更精简的加速器测试矩阵意味着更快的 PR 合入速度和更低的基础设施成本。

### 4. 值得关注的技术点

- **DeepGEMM FP8 MoE 集成**：DeepGEMM 是 DeepSeek 开源的高性能 FP8 GEMM 库，其与 VeOmni MoE 训练管道的融合值得关注其在不同 MoE 路由策略下的表现。
- **Ascend QSA 整数元数据优化**：整数化处理通常用于减少 host-device 通信开销和内存占用，这种优化手法对其他 NPU 平台也有借鉴价值。
- **AI 辅助开发**：提交标注 `Co-authored-by: Cursor`，表明项目团队已开始将 AI 编码助手纳入开发工作流，值得关注其对项目迭代速度的影响。

### 5. 对项目整体发展的推动

结合 VeOmni"Scaling Any Modality Model Training"的定位，这批提交从**正确性**（接口统一）、**效率**（FP8 + Ascend 优化）、**工程实践**（CI 精简）三个维度同步推进，体现了项目已从早期的功能搭建阶段转向**性能调优和多平台成熟化**阶段。统一接口为后续扩展更多模态模型铺路，DeepGEMM FP8 支持降低了大规模 MoE 训练的资源门槛，Ascend 适配则拓宽了硬件生态。这些改动共同强化了 VeOmni 作为"一站式分布式训练基础设施"的竞争力，尤其在多模态大模型训练场景下具有持续的技术积累价值。

## 详细提交记录

### [bb08aae](https://github.com/ByteDance-Seed/VeOmni/commit/bb08aae42b2da6c9dfa360afffd25d3f0aa45259)

- **作者**: Coach257
- **时间**: 2026-10-26T12:02:45Z
- **提交信息**: [model, ci] fix: unify prepare_dense_attention_inputs across dense attention models (#1368)

### [798ee98](https://github.com/ByteDance-Seed/VeOmni/commit/798ee9894f2f70fd93c94ab0b977a5b0f1fc819c)

- **作者**: YLlllllllllll
- **时间**: 2026-10-26T12:01:04Z
- **提交信息**: [model, perf] refactor: reuse compact QSA integer metadata on Ascend (#1348)

### [a8b348e](https://github.com/ByteDance-Seed/VeOmni/commit/a8b348ed57ad670fb8603a759b1aaab0cd1fd00a)

- **作者**: Bin Jia
- **时间**: 2026-10-26T09:09:15Z
- **提交信息**: [ops] feat: add deepgemm fp8 moe training (#1356)

### [6e78605](https://github.com/ByteDance-Seed/VeOmni/commit/6e78605bcc935a1890ba4da636c1131254ff9d31)

- **作者**: Zeren Chen
- **时间**: 2026-10-26T08:57:32Z
- **提交信息**: [ci, perf] test: simplify accelerator cases and retain key coverage (#1351)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2958
- **最后更新**: 2026-10-26T13:46:39Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bilang ZHANG, Shiqiao Gu (谷石桥)

## AI分析总结

## 昨日提交分析（共2条）

### 1. 主要更新类型
- **性能优化**（1条）：针对 MiniMax-H3 因果流式推理的性能调优
- **功能新增 + 重构**（1条）：统一原生 runner 并优化 KV 缓存推理，同时附带多项新特性

### 2. 关键变更点及与项目方向的关系
- 两条提交均直接服务于项目核心目标——**轻量化视频生成推理**，聚焦"推理速度"和"实时性"两个关键维度。
- 第一条（MiniMax-H3）引入了新的 768p 预设（含实时 FP8 选项）、流式视频输出、参考图与音频复用、以及音频编码/视频解码/注意力的加速路径，属于面向特定模型的深度优化。
- 第二条（AR 自回归）将原生 runner 进行统一，并优化 KV 缓存推理，是一次架构层面的整合与提速，配套发布了详尽的 RTX 5090 实测性能基线。
- 两条提交均涉及预设/默认值更新（提示词漫游服务器切换新预设，旧 BF16 实时预设下线），体现出向 FP8/更高性能预设的迁移趋势。

### 3. 对项目的影响和潜在意义
- **实时能力显著提升**：实测显示 Self-Forcing 1.3B、Matrix-Game-4、EdenLive 5B 三款模型在单张 RTX 5090 上即可达到实时（推理 FPS 超过播放帧率，RTF < 1），大模型在 8 卡 SP8 配置下也能实时运行，这为交互式视频生成应用（如虚拟人、直播、游戏 NPC）提供了工程可行性。
- **工程标准化**：统一原生 runner 降低了多模型接入的维护成本，KV 缓存优化直接减少重复计算，长期看有利于框架扩展更多模型。
- **流式输出 + 资源复用**（参考图/音频复用）使端到端延迟进一步降低，更贴近真实产品的低延迟需求。
- 预设体系的迭代（FP8 替代 BF16）表明项目在精度与速度的权衡上逐步走向默认高性能配置。

### 4. 值得关注的技术点
- **FP8 实时预设**：以半精度以下的量化换取实时能力，需关注精度损失情况。
- **KV 缓存推理优化**：自回归视频生成中 KV 缓存是显存与延迟的主要瓶颈，此次优化的收益可从首帧延迟（首块延迟 300–2700ms 不等）和块间 P95 间隙（50–610ms）数据中评估。
- **因果流式推理**：结合流式输出，实现边生成边播放，块间 P95 指标是衡量播放流畅度的关键。
- **严谨的基准方法**：提交附带了排除模型加载/编译/IO 的纯净推理 FPS 统计口径，数据可信度较高。
- 首块延迟差异较大（Matrix-Game-4 达 2.7s），提示不同模型的冷启动体验仍有优化空间。

### 5. 对项目发展的影响
结合 README 中"Light Video Generation Inference Framework"的定位，这两条提交把项目从"能跑"推向"能实时跑、能产品化"：
- 性能基线的公开使项目在推理框架竞争中有了可量化的对比依据；
- 多模型实时达标的成果强化了框架"轻量、通用"的卖点；
- runner 统一与预设体系收敛为后续版本发布和文档化奠定了基础。
总体而言，这批提交是项目向**生产级实时视频生成推理**迈进的重要一步。

## 详细提交记录

### [100ecfe](https://github.com/ModelTC/LightX2V/commit/100ecfec4be2956539f41688cbd7bc96f0528cca)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-26T11:47:21Z
- **提交信息**: perf: optimize MiniMax-H3 causal streaming inference (#1650)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
  * Added new 768p MiniMax H3 presets, including a real-time FP8 option.
* Added support for streaming video output and reusing reference images
and audio during generation.
* Added faster processing options for audio encoding, video decoding,
and attention.

* **Updates**
* Updated the prompt-travel server and runner defaults to use the new
presets.
  * The previous real-time BF16 presets are no longer available.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: zhangbilang <2045966653@qq.com>

### [58b8e25](https://github.com/ModelTC/LightX2V/commit/58b8e2592519711457e9fface5a804d7c337a1ae)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-10-26T07:08:35Z
- **提交信息**: feat(ar): unify native runners and optimize KV-cached inference (#1646)

## Performance

Real-weight warm-request measurements on NVIDIA RTX 5090 GPUs. Only
profiles whose full inference throughput exceeds their configured
playback frame rate are included. Inference FPS covers input preparation
through the last decoded GPU chunk; model loading, compilation, warmup,
final MP4 assembly, and disk I/O are excluded. Each result uses one
formal request after warmup.

Three models run in real time on a single RTX 5090. Realtime-Video and
LingBot-Fast reach real time with 8× RTX 5090 using SP8.

| Model | GPUs | Output case | Target FPS | Generation FPS ↑ | Inference
FPS ↑ | Real-time headroom ↑ | First-chunk latency ms ↓ | Inter-chunk
gap P95 ms ↓ | RTF@target ↓ |
| --- | ---: | --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| Self-Forcing 1.3B | 1× RTX 5090 | 81 frames, 832×480 | 16 | 35.36 |
**34.64** | **2.17×** | 300.47 | 402.12 | **0.4619** |
| Matrix-Game-4 | 1× RTX 5090 | 241 frames, 864×480 | 24 | 79.48 |
**42.81** | **1.78×** | 2692.68 | 50.63 | **0.5606** |
| EdenLive 5B | 1× RTX 5090 | 717 frames, 1280×704 | 24 | 25.28 |
**25.17** | **1.05×** | 509.70 | 511.91 | **0.9534** |
| Realtime-Video 14B | 8× RTX 5090, SP8 | 102 frames, 832×480 | 16 |
24.42 | **24.17** | **1.51×** | 445.31 | 476.75 | **0.6621** |
| LingBot-Fast v2 | 8× RTX 5090, SP8 | 261 frames, 832×464 | 16 | 19.86
| **18.28** | **1.14×** | 1688.13 | 609.13 | **0.8752** |

Real-time headroom is `Inference FPS / target FPS`; values above 1 and
RTF values below 1 indicate faster-than-playback generation.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
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


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6793
- **最后更新**: 2026-10-27T00:34:46Z

## 提交统计

- **昨日提交总数**: 62
- **提交者数量**: 24
- **主要提交者**: Yihua Wei, Yaxing Cai, Enwei Zhu

## AI分析总结

# FlashInfer 昨日 62 个提交综合分析

## 一、主要更新类型

- **性能优化（主导，约占 80% 以上）**：覆盖 MoE 路由与 GEMM、MLA/注意力解码、量化、归一化、采样、线性循环（Mamba2/KDA/GDN）、视觉塔及序列并行通信等核心算子。
- **正确性与 Bug 修复（约十余条）**：重点是 Blackwell 内存一致性、路由越界、数值精度与测试稳定性。
- **工程与基础设施（少量）**：CI 测试调度、构建缓存、打包与 CPU-only 测试迁移。

## 二、关键变更

**1. Cake 后端持续成熟，覆盖前沿模型。** 该后端已支持 Kimi-K3（FP8 MLA、NVFP4 投影、MoonViT-3D 视觉塔、896 专家 top-16 融合路由器）、StepFun MoE、MiniMax-H3、DeepSeek 系列与 NVFP4 GEMM 等端到端算子族。性能成果包括：融合 FP8 MoE 提速 1.037x–1.154x、NVFP4 量化 GEMM 链 L2 权重预取在 B200 上最高 1.076x、Kimi-K3 视觉塔全线 shape 提速 1.011x–1.074x、masked batched FP8 GEMM 实现 164 个形状零回退优化，均附严谨的多 GPU 交替测量基准。

**2. MLA 与注意力解码大幅提速。** 新增 `softmax_rescale_threshold_log2` 参数，B200 上 FP8/BF16 场景最高提速约 10%；FP8 MLA 2CTA 解码修复页表读取阻塞关键路径后，大 batch 加速高达 2.40x；新增 NVFP4 短工作单元解码与通用 split-KV 合并程序（小批量最高 1.11x）；PrimTS 解码将指数运算分流至 FMA 管线。

**3. MoE、GEMM 与训练算子优化。** CuTe-DSL 融合 MoE 新增 MXFP8 模式，Nemotron ≥2k token 时比 TRT-LLM 快 13–21%；分组 MXFP8 量化在稀疏场景提速超 1.35x；BF16×FP4 GEMM 优化 tcgen05 张量内存释放时机，小 M 形状提速 1.2x；KDA 状态遍历引入双 CTA 拆分；RMSNorm 训练反向采用分阶段 dweight 归约（SM107 约 1.18x）；Gated DeltaNet 利用上三角结构跳过零值 MMA tile，并通过编译期注入 stride 将索引态慢 3.2 倍的缺口补齐，小 batch decode 延迟从 4.96µs 降至 1.95µs；Mamba2 selective state update 新增 P-split、TMA-ring、持久化等多执行方案（B200 最多 1.16x）；DeepSeek-V3 融合路由修复组索引越界。

**4. 主机侧与通信延迟优化。** prepared fused grouped FP8 launch 支持每次调用传入不同操作数与 -1 padding，可被 CUDA Graph 捕获；cuDNN 页表矩形快路径将 plan 延迟从 375µs 降至 178µs；Ulysses 序列并行改用对称内存集体分配直写，通信延迟降低 5%–11%。

**5. 正确性与工程加固。** 多条提交统一修复 SM100/SM103/SM120 上异步代理读取共享内存需用 `fence.proxy.async.shared::cta` 显式排序的 PTX 未定义行为隐患，其中 SM120 注意力内核接受约 3% 回退换取确定性；另修复 tcgen05.st 地址 lane 编码、FP4 fused norm swizzled padding 未清零、SM120 次正规 scale 误清零、32 位 memref 描述符导致 >2 GiB 权重溢出、Kimi K3 CUDA 源文件未打进 wheel、Rubin（SM107）autotune 失败等问题。CI 将 main 分支 push 触发改为每日三次定时全量测试，削减约 70% 浪费；sccache 修复使 JIT 编译从约 44s 降至 6s。

## 三、技术关注点

- **异步代理栅栏**成为 Blackwell 新硬件正确性核心课题，体现对 PTX 内存模型的深入理解。
- **TMEM lane quarter 布局**适配 tcgen05 softmax 统计存储，以及 TMA ring、持久化线程块、寄存器窗口预取页表等微架构特性的系统性运用。
- **细粒度按形状路由**：内核普遍内建按批量、链长与架构选择程序变体的启发式调度，调优高度数据驱动。
- **可重绑定 prepared launch** 将 tensor map 即时编码为纯 host 工作，实现 kernel/host 接口的巧妙解耦。
- **PDL 友好的 padding 清零**在生产者-消费者链内部完成，避免打断异步流水线。
- **严谨正确性保障**：多条提交声明未改内核字节级相同、输出 bit-for-bit 一致。

## 四、整体影响

FlashInfer 正从注意力核库演进为覆盖 MoE、量化、采样、线性注意力与训练算子的端到端推理平台。项目同时推进三条主线：向 Blackwell 全系（SM100/103/107/120）迁移并建立内存序实践标准；为 Kimi-K3、Nemotron、MiniMax-H3 等前沿模型提供完整算子套件；通过 CI 与通信优化降低大规模部署成本。所有加速均以严格 opt-in、默认行为不变的方式交付，逐位一致承诺与详尽基准文化提升工程可信度，为 vLLM、SGLang 等下游框架提供更稳定的数值行为与更低的升级摩擦，巩固其作为 NVIDIA 生态内 Blackwell 平台首选高性能推理内核基础设施的地位。

## 详细提交记录

### [810c470](https://github.com/flashinfer-ai/flashinfer/commit/810c47021c26e2c1127e3a0d2bda6230b644e5f4)

- **作者**: Yaxing Cai
- **时间**: 2026-10-26T23:52:29Z
- **提交信息**: fix(kda): support singular tvm-ffi detail headers (#7337)

<!-- .github/pull_request_template.md -->

## 📌 Description

The generated direct-M128 KDA launcher currently names
`tvm::ffi::details::ObjectUnsafe` directly. Select `base_detail.h` and
the singular `tvm::ffi::detail` namespace when that header is available,
falling back to `base_details.h` and `tvm::ffi::details` for older
tvm-ffi releases.

The opaque Python launcher's owned-handle transfer remains unchanged.
This lets the binding compile after tvm-ffi removes its temporary plural
namespace compatibility alias, while retaining older-version source
support.

## 🔍 Related Issues

Compatibility follow-up to apache/tvm-ffi#872, included in tvm-ffi
v0.1.15.post1.

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

No local builds, tests, or pre-commit runs were performed, as requested
by the author. Static source review and `git diff --check` completed.
Existing CI targets: `tests/jit/test_flash_kda_generated_registry.py`,
`tests/kda/test_flash_kda_indexed_prefill.py`, and
`tests/kda/test_kda_prefill_plan_cache.py`. Validation should include
both older tvm-ffi headers and v0.1.15.post1+ headers.

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

The header is shared by the `direct_m128` and `vtile_m128` ABI families.
The namespace alias is local to `flashinfer::flash_kda_generated`; no
dependency-floor bump, generated device-kernel change, or ownership
change is included. The generated header is excluded from automatic
formatting in the existing pre-commit configuration.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Compatibility**
* Improved compatibility with TVM FFI versions that use either supported
header and namespace convention. This helps the binding build across a
broader range of TVM FFI configurations without changing its public
interface.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Tianqi Chen <tqchen@users.noreply.github.com>

### [9c4aacf](https://github.com/flashinfer-ai/flashinfer/commit/9c4aacf1bfd66f8eea15e24731b2c58c4afa0bc4)

- **作者**: Theodore-Liu
- **时间**: 2026-10-26T23:48:17Z
- **提交信息**: fix(moe): static-wrap SM12x W4A16 weight banks to fix >2 GiB host marshalling overflow (#4738)

<!-- .github/pull_request_template.md -->

## 📌 Description

A flat expert weight bank larger than 2 GiB kills the SM12x W4A16 fused
MoE on
the host side, before the kernel is ever launched:

```
OverflowError: Value overflow: 2684354560 exceeds range of l
```

### What happens

`_w4a16_fused_moe_launch_flat` flattens each expert bank to rank-1 and
hands
the raw torch tensor to `fused.compiled(...)`:

```python
w13_arg = prepared.w13.view(torch.uint8).view(-1)   # 2,684,354,560 elements
...
fused.compiled(make_ptr(a...), w13_arg, w2_arg, ...)
```

A raw tensor at that boundary is converted implicitly by the DSL's
`TensorAdapter`, which does `from_dlpack(arg).mark_layout_dynamic()`.
Dynamic
sizes are packed 32-bit by the runtime when the memref descriptor is
built, so
any bank past `2**31 - 1` overflows in `build_memref_desc`.

### Why it went unnoticed

Two things have to line up:

* **The uint8 view.** `prepare_w4a16_packed_weights` always produces
`weight_layout="packed"`, whose flat view is int32 — a 2.5 GiB bank is
only
671M elements there. The `modelopt` layout flattens to uint8, so the
element
count *is* the byte count. That is the path in the report (b12x /
modelopt
  weights consumed zero-copy).
* **A bank that big.** Consumer SM120 cards usually shard below the
boundary;
the report is on GB10 with 128 GB unified memory, where the full bank
for
  Qwen3.6-35B-A3B-NVFP4 (256 experts) crosses it.

### Why the fix is a type correction, not a workaround

The kernel is compiled against **static-shape** fakes for exactly these
two
parameters — the geometry is part of the compile cache key:

```python
w13_fake = cute.runtime.make_fake_compact_tensor(
    cutlass.Uint8,
    (num_experts * fc1_cols * (hidden_size // 2),),   # compile-time int
    assumed_align=16,
)
```

So the compiled signature and what the call site actually passes are
different
MLIR types:

```
fake / compiled signature : !cute.memref<i8, gmem, align<16>, "(N):(1)">
static from_dlpack        : !cute.memref<i8, gmem, align<16>, "(N):(1)">   # matches
implicit TensorAdapter    : !cute.memref<i8, gmem, align<16>, "(?):(1)">   # mismatch
```

The dynamic wrapper was never type-accurate here; it only worked because
the
descriptors are ABI-compatible and the kernel indexes with compile-time
constants rather than reading the runtime size slot. The 2 GiB boundary
is
where that coincidence runs out.

The fix wraps the two banks explicitly:

```python
w13_arg = cute.runtime.from_dlpack(w13_arg, assumed_align=16)
w2_arg = cute.runtime.from_dlpack(w2_arg, assumed_align=16)
```

This restores the type the kernel was compiled for, and as a consequence
the
size never goes through the 32-bit packing path at all — it stays a
compile-time constant, as the fakes already declared. `assumed_align=16`
mirrors the fake declaration.

### Scope

Only `w13_arg` / `w2_arg` are wrapped. Their runtime shape is a
deterministic
function of the compile cache key (`num_experts`, `hidden_size`,
`intermediate_size`, `weight_layout`, `scale_format`), so pinning them
static
costs no flexibility.

The scratch and intermediate-cache arguments are also passed flat and
could in
principle cross `2**31` at extreme batch sizes, but their runtime size
is only
required to be *at least* the compile-time sample (`numel() >= ...`), so
static-wrapping them would assert a shape that may not hold. Left
untouched
deliberately; happy to follow up if maintainers want a guard there.

## 🔍 Related Issues

Fixes #4706

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Added `tests/moe/test_b12x_w4a16_large_bank.py`. It builds a
`modelopt`-layout
`W4A16PackedWeights` whose w13 bank is exactly 2,684,354,560 uint8
elements
(`E=64`, `2n=8192`, `k/2=5120` — the value from the report) and runs
`run_w4a16_moe` end to end. It skips unless SM120/SM121 and ~6 GiB of
free
VRAM are available.

Verified on an RTX 5090 (SM120), flashinfer 0.6.17 / nvidia-cutlass-dsl
4.6.2:

| layout | bank | before | after |
| --- | --- | --- | --- |
| modelopt | 2,684,354,560 (2.5 GiB) | `OverflowError`, traceback
frame-for-frame identical to the report | passes |
| modelopt | 8,388,608 (8 MiB) | passes | passes |
| packed | 2,147,483,648 (2 GiB) | passes | passes |
| packed | 8,388,608 (8 MiB) | passes | passes |

Output equivalence: for the two small configurations I captured the
output
tensors before and after the change and compared them bit-for-bit
(viewed as
uint16) — identical, as expected since the kernel body and its compile
cache
key are untouched.

## Reviewer Notes

* The root cause — dynamic sizes packed 32-bit in `build_memref_desc` —
lives
in the CUTLASS DSL runtime, not in FlashInfer. This PR fixes the call
site so
  it stops relying on the dynamic path for parameters that were declared
  static; it does not change or work around the DSL itself.
* The regression test needs a real >2 GiB allocation, so it is gated on
free
VRAM as well as architecture. On a 32 GB SM120 card it runs in a few
seconds
  once the kernel is cached.
* The reporter offered to validate on DGX Spark (GB10). This PR was
confirmed
on consumer SM120 with the exact bank size from the report; an
independent
  check on GB10 would be welcome.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed an issue that could prevent large fused mixture-of-experts
models from running when expert weight banks exceeded 2 GiB.
* Large expert weight banks now retain their full size during
processing, avoiding overflow errors.

* **Tests**
* Added regression coverage for large-bank W4A16 fused
mixture-of-experts workloads.
* The test verifies successful execution and finite output on supported
hardware.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Jingze Liu <110184138+Theodore-Liu@users.noreply.github.com>

### [a1fbb4e](https://github.com/flashinfer-ai/flashinfer/commit/a1fbb4e0c4703c65a108bff1a17be5067a72adf0)

- **作者**: Yihua Wei
- **时间**: 2026-10-26T23:45:39Z
- **提交信息**: Resolve MXFP8 x MXFP4 Performance Issue (#7445)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

* **Performance**
* Updated SM120 MXFP8 × MXFP4 kernel settings with 128-byte L2 promotion
for data transfers. Other data-type combinations retain their existing
settings.
* Adjusted mixed-precision stage memory budgeting to account for each
operand’s row size independently.
* Refreshed kernel selections using cold-cache measurements across the
full MoE pipeline, including uniform and skewed routing profiles. Added
coverage for a 1,024-token bucket.

* **Documentation**
* Clarified the cuDNN Frontend revisions and mixed-input kernel
characteristics used for SM120.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8725541](https://github.com/flashinfer-ai/flashinfer/commit/872554187e41987c61852cef8bf5341b2b6499f3)

- **作者**: Lee Nau
- **时间**: 2026-10-26T21:19:29Z
- **提交信息**: fix(benchmarks): refresh owned outputs before graph validation (#7193)

<!-- .github/pull_request_template.md -->

## 📌 Description

Graph-study tactics can share an output buffer. A selected tactic that
never writes its output can therefore pass correctness validation using
the default graph’s previous result.

Add an optional fixture-owned `prepare_validation(output, inputs)`
callback before each final correctness replay, after all timing samples.
The built-in FP8 fixture fills its separately allocated output with NaNs
under inference mode. The report records whether a refresh callback was
available.

Extend the existing shared-output regression to cover correct,
wrong-result and no-write graphs with ordinary and inference tensors.
Custom fixtures opt in and remain responsible for preserving read
operands and workspace.

## 🔍 Related Issues

Follow-up to the graph-selection benchmark in #7155.

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

Scoped hooks passed: `pre-commit run --files
benchmarks/bench_autotuner_accuracy.py
benchmarks/README_autotuner_accuracy.md
tests/autotuner/test_accuracy_harness.py`. `git diff --check` also
passed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated commit `e28cb383cd8de1fe105a65aee6935a1920155da6` on H100 NVL
with PyTorch `2.14.1+cu130` / CUDA 13.0:

- `python -m pytest -q -ra tests/autotuner/test_accuracy_harness.py`:
**14 passed, 0 skipped**.
- Negative control: remove only the `prepare_validation(output, inputs)`
invocation and run `-k 'validates_shared_output and no_write'`. Both
cases fail with `DID NOT RAISE`, confirming that omitting refresh
accepts stale output.

The regressions use actual tuner/cache and CUDA Graph paths with
controlled profiling times and `torch.add` runners. They cover ordinary
and inference tensors, correct and incorrect output, and callback-free
fixtures. GitHub CI is pending at submission.

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

This is a benchmark correctness fix. Output refresh runs outside timed
samples. No serving-performance claim is made.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Benchmark correctness checks can now refresh fixture-owned outputs
before each validation replay, helping distinguish fresh results from
stale output.
* Reports indicate whether output refresh was performed or unavailable.
The built-in FP8 fixture clears its output before validation.
* **Documentation**
* Updated benchmark guidance with callback requirements, including
preserving inputs and workspace.
* **Tests**
* Expanded coverage for validation callbacks, output-writing behavior,
and inference-mode restoration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1290367](https://github.com/flashinfer-ai/flashinfer/commit/1290367e8d116098e5e617e2d148441eb6607c3e)

- **作者**: eigen
- **时间**: 2026-10-26T20:59:59Z
- **提交信息**: perf(cake_grouped_fp8_fused_silu_quant): faster pair and tail kernels for large-M MoE gate_up on SM100 / SM103 (#7454)

FlashInfer's Cake grouped FP8 GEMM family has four forms. Two are
contiguous: one uses FP32 scales, the other packed UE8M0 scales
(block-scaled MMA). One fuses the MoE gate_up GEMM with SwiGLU and
per-token-group FP8 quantization. One is masked batched. This PR
delivers the fused form and replaces the two kernels of its pair + tail
route. The route choice and the other routes are unchanged. The baseline
is the previous Cake version of this kernel on FlashInfer main. Three
shapes take the pair + tail route (rows 1, 6 and 7). On all three GPUs,
their speedup is 1.037x–1.154x with CUDA graphs and 1.050x–1.146x eager.
The other 12 shapes run the same programs in both columns:
0.984x–1.008x.

Latency per call in microseconds (median), with CUDA graph replay and
with eager launch, cold L2. "main" = the programs on FlashInfer main;
"PR" = this PR. Speedup = main / PR, the median over 3 runs of the
paired per-run ratio, so it can differ in the last digit from the
quotient of the two latencies. "program changed" = yes on the rows that
take the pair + tail route, whose two kernels this PR replaces; the
other rows run the same programs in both columns. 2H = the gate_up
output width; rows per expert = the routed rows of each expert, in
expert order. GPUs: NVIDIA B200 (sm_100a); NVIDIA GB300 (sm_103a), where
GPU a and GPU b are two different boards. CUDA 13.4, PyTorch
2.14.1+cu130.

**NVIDIA B200 (sm_100a)**

| # | M | K | 2H | experts | rows per expert | program changed | graph
main us | graph PR us | graph speedup | eager main us | eager PR us |
eager speedup |
|---:|---:|---:|---:|---:|---|---|---:|---:|---:|---:|---:|---:|
| 1 | 4096 | 4096 | 2048 | 16 | 256 x 16 | yes | 35.86 | 34.29 | 1.045x
| 38.69 | 34.19 | 1.130x |
| 2 | 4096 | 4096 | 2048 | 16 |
256/0/512/0/384/640/128/384/256/0/128/128/384/384/512/0 | no | 40.94 |
40.90 | 1.000x | 40.76 | 40.75 | 1.000x |
| 3 | 4096 | 4096 | 2048 | 16 |
384/384/384/384/384/384/384/384/128/128/128/128/128/128/128/128 | no |
45.05 | 44.96 | 1.002x | 44.81 | 44.86 | 0.999x |
| 4 | 2048 | 4096 | 2048 | 16 | 128 x 16 | no | 29.94 | 29.98 | 0.998x |
29.69 | 29.70 | 0.999x |
| 5 | 4096 | 4096 | 2048 | 16 |
640/128/384/0/896/128/384/256/128/0/384/128/256/128/128/128 | no | 42.50
| 42.47 | 1.000x | 42.28 | 42.26 | 1.001x |
| 6 | 4096 | 4096 | 2048 | 16 |
128/384/256/256/256/256/256/256/256/256/256/256/256/256/256/256 | yes |
39.66 | 34.37 | 1.154x | 39.17 | 35.36 | 1.108x |
| 7 | 8192 | 4096 | 2048 | 16 | 512 x 16 | yes | 62.91 | 59.68 | 1.054x
| 63.09 | 59.68 | 1.056x |
| 8 | 128 | 512 | 256 | 1 | 128 x 1 | no | 7.44 | 7.45 | 1.002x | 28.98
| 29.09 | 1.001x |
| 9 | 256 | 512 | 256 | 2 | 128 x 2 | no | 7.46 | 7.42 | 1.004x | 29.75
| 29.70 | 1.000x |
| 10 | 256 | 1024 | 512 | 1 | 256 x 1 | no | 8.06 | 8.07 | 0.998x |
30.28 | 30.26 | 1.001x |
| 11 | 1152 | 512 | 512 | 4 | 384/128/0/640 | no | 7.66 | 7.60 | 1.007x
| 30.94 | 30.86 | 1.001x |
| 12 | 484 | 1024 | 256 | 6 | 0/256/0/0/128/100 | no | 8.22 | 8.23 |
1.001x | 19.86 | 19.87 | 0.998x |
| 13 | 416 | 2048 | 768 | 5 | 128/0/0/256/32 | no | 9.98 | 10.02 |
0.998x | 20.70 | 20.77 | 0.999x |
| 14 | 96 | 512 | 256 | 17 | 0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/96 | no |
7.87 | 7.97 | 0.989x | 33.22 | 33.22 | 0.999x |
| 15 | 8192 | 4096 | 2048 | 16 |
640/640/640/640/640/640/640/640/384/384/384/384/384/384/384/384 | no |
71.02 | 71.06 | 1.000x | 72.06 | 72.08 | 0.999x |

**NVIDIA GB300 (sm_103a), GPU a**

| # | M | K | 2H | experts | rows per expert | program changed | graph
main us | graph PR us | graph speedup | eager main us | eager PR us |
eager speedup |
|---:|---:|---:|---:|---:|---|---|---:|---:|---:|---:|---:|---:|
| 1 | 4096 | 4096 | 2048 | 16 | 256 x 16 | yes | 33.86 | 32.56 | 1.039x
| 36.22 | 32.43 | 1.120x |
| 2 | 4096 | 4096 | 2048 | 16 |
256/0/512/0/384/640/128/384/256/0/128/128/384/384/512/0 | no | 37.85 |
37.79 | 1.000x | 37.67 | 37.65 | 1.000x |
| 3 | 4096 | 4096 | 2048 | 16 |
384/384/384/384/384/384/384/384/128/128/128/128/128/128/128/128 | no |
42.98 | 42.99 | 0.999x | 42.78 | 42.75 | 1.001x |
| 4 | 2048 | 4096 | 2048 | 16 | 128 x 16 | no | 29.69 | 29.62 | 1.000x |
29.35 | 29.34 | 1.001x |
| 5 | 4096 | 4096 | 2048 | 16 |
640/128/384/0/896/128/384/256/128/0/384/128/256/128/128/128 | no | 39.69
| 39.63 | 1.001x | 39.49 | 39.43 | 1.001x |
| 6 | 4096 | 4096 | 2048 | 16 |
128/384/256/256/256/256/256/256/256/256/256/256/256/256/256/256 | yes |
36.50 | 33.05 | 1.105x | 43.81 | 41.74 | 1.050x |
| 7 | 8192 | 4096 | 2048 | 16 | 512 x 16 | yes | 55.67 | 52.87 | 1.052x
| 60.01 | 52.54 | 1.143x |
| 8 | 128 | 512 | 256 | 1 | 128 x 1 | no | 6.86 | 6.87 | 1.000x | 54.88
| 55.17 | 1.000x |
| 9 | 256 | 512 | 256 | 2 | 128 x 2 | no | 6.89 | 6.86 | 1.001x | 55.70
| 55.99 | 1.000x |
| 10 | 256 | 1024 | 512 | 1 | 256 x 1 | no | 7.66 | 7.68 | 1.000x |
54.33 | 54.29 | 0.997x |
| 11 | 1152 | 512 | 512 | 4 | 384/128/0/640 | no | 7.32 | 7.33 | 0.998x
| 56.27 | 56.38 | 1.005x |
| 12 | 484 | 1024 | 256 | 6 | 0/256/0/0/128/100 | no | 7.87 | 7.86 |
1.002x | 36.66 | 36.82 | 1.007x |
| 13 | 416 | 2048 | 768 | 5 | 128/0/0/256/32 | no | 9.34 | 9.34 | 1.001x
| 37.53 | 37.63 | 1.000x |
| 14 | 96 | 512 | 256 | 17 | 0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/96 | no |
7.52 | 7.65 | 0.984x | 58.81 | 59.26 | 0.988x |
| 15 | 8192 | 4096 | 2048 | 16 |
640/640/640/640/640/640/640/640/384/384/384/384/384/384/384/384 | no |
64.55 | 64.58 | 0.999x | 67.12 | 66.90 | 1.008x |

**NVIDIA GB300 (sm_103a), GPU b**

| # | M | K | 2H | experts | rows per expert | program changed | graph
main us | graph PR us | graph speedup | eager main us | eager PR us |
eager speedup |
|---:|---:|---:|---:|---:|---|---|---:|---:|---:|---:|---:|---:|
| 1 | 4096 | 4096 | 2048 | 16 | 256 x 16 | yes | 33.91 | 32.72 | 1.037x
| 36.18 | 32.33 | 1.118x |
| 2 | 4096 | 4096 | 2048 | 16 |
256/0/512/0/384/640/128/384/256/0/128/128/384/384/512/0 | no | 38.42 |
38.48 | 1.000x | 38.22 | 38.18 | 1.002x |
| 3 | 4096 | 4096 | 2048 | 16 |
384/384/384/384/384/384/384/384/128/128/128/128/128/128/128/128 | no |
43.10 | 43.06 | 1.001x | 42.85 | 42.96 | 0.999x |
| 4 | 2048 | 4096 | 2048 | 16 | 128 x 16 | no | 29.69 | 29.65 | 1.001x |
29.38 | 29.38 | 1.000x |
| 5 | 4096 | 4096 | 2048 | 16 |
640/128/384/0/896/128/384/256/128/0/384/128/256/128/128/128 | no | 40.57
| 40.57 | 1.000x | 40.34 | 40.28 | 1.001x |
| 6 | 4096 | 4096 | 2048 | 16 |
128/384/256/256/256/256/256/256/256/256/256/256/256/256/256/256 | yes |
37.10 | 33.11 | 1.122x | 44.58 | 42.03 | 1.056x |
| 7 | 8192 | 4096 | 2048 | 16 | 512 x 16 | yes | 56.02 | 53.11 | 1.055x
| 60.38 | 52.76 | 1.146x |
| 8 | 128 | 512 | 256 | 1 | 128 x 1 | no | 6.98 | 6.98 | 1.000x | 60.22
| 60.00 | 1.006x |
| 9 | 256 | 512 | 256 | 2 | 128 x 2 | no | 6.96 | 7.01 | 0.992x | 60.23
| 60.56 | 1.001x |
| 10 | 256 | 1024 | 512 | 1 | 256 x 1 | no | 7.65 | 7.62 | 1.002x |
60.58 | 60.66 | 1.000x |
| 11 | 1152 | 512 | 512 | 4 | 384/128/0/640 | no | 7.38 | 7.37 | 1.000x
| 62.92 | 63.11 | 0.998x |
| 12 | 484 | 1024 | 256 | 6 | 0/256/0/0/128/100 | no | 7.76 | 7.77 |
1.000x | 40.10 | 40.36 | 0.986x |
| 13 | 416 | 2048 | 768 | 5 | 128/0/0/256/32 | no | 9.42 | 9.40 | 1.003x
| 39.97 | 40.09 | 1.005x |
| 14 | 96 | 512 | 256 | 17 | 0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/0/96 | no |
7.71 | 7.78 | 0.992x | 65.48 | 66.22 | 0.998x |
| 15 | 8192 | 4096 | 2048 | 16 |
640/640/640/640/640/640/640/640/384/384/384/384/384/384/384/384 | no |
64.94 | 64.95 | 1.000x | 72.88 | 73.16 | 0.999x |

The other Cake variants are `cake_grouped_fp8_gemm` (contiguous, FP32 or
UE8M0 scales) and `cake_batch_deepgemm_fp8` (masked batched), and this
kernel covers `sm_100a` (B200) and `sm_103a` (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated execution for grouped FP8 fused SiLU quantization workloads,
including paired and tail cases.
* Added stricter validation for supported tensor inputs and launch
configurations, with clearer errors for invalid inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [492fb01](https://github.com/flashinfer-ai/flashinfer/commit/492fb0128bfa3df5910c546c4156f81d787ba8fb)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T20:54:51Z
- **提交信息**: feat(cake_grouped_fp8_gemm): per-call operands and -1 padding rows for the prepared fused grouped FP8 SiLU-quant launch (SM100 / SM103) (#6049)

## Summary

The Cake grouped FP8 bindings encode their tensor maps from the call
arguments and pass them by value (since #5993). A prepared launch
therefore owns no descriptor storage, and the per-token tensors no
longer have to be fixed at preparation. This PR exposes that in the
prepared fused gate_up GEMM + SwiGLU + FP8 quantization launch. A MoE
runner can then keep one prepared object per layer and run it on
whatever buffers the dispatcher produced, with no staging copies and no
persistent buffer arena. The same change for the plain grouped GEMM is
part of #6048. This PR does not depend on #6048: it was tested against
both the current and the #6048 version of the GEMM host.

-
`prepare_group_gemm_fp8_nt_groupwise_contiguous_silu_quant(...).launch(a=,
a_scale=, m_indices=, out_q=, out_s=)` replaces the per-token operands
of every stage for one call.
- Replacement tensors must keep the prepared shape, dtype, device and
alignment.
- Rebinding is host work only (no copy, no device allocation) and can be
captured in a CUDA graph.
  - `launch()` without operands is unchanged.
- `fill_padding=True` accepts `-1` padding rows in `m_indices`, i.e. the
compact MoE layout where each expert is padded to the next 128-row
boundary.
- Before the route runs, the prepared object forward-fills the indices
into its own `(M,)` scratch with two small graph-capturable kernels.
- A padding row is computed with the preceding expert's weights, and its
output row is unspecified.
- `validate_indices=True` checks the padded contract: range `-1 <= i <
G`, routed rows nondecreasing, and 128-row aligned internal boundaries
after the fill.
- The small-M route still uses the grouped GEMM only through
`prepare(...).launch()`. If its operands are rebound, the GEMM is
prepared again on them, which is host work only.

Kernels, bindings and the JIT registry are unchanged, and so are the
numerics.

## Tests

- Per-call rebinding on every route:
  - small-M with the Cake GEMM
  - small-M with the CuTe-DSL GEMM
  - pair + tail
  - mixed schedule

Each case includes a captured rebound launch replayed onto the rebound
tensors.
- Compact-layout `-1` padding on the small-M and pair + tail routes,
including graph capture of the forward fill, and rejection of unsorted
routed rows.

Results on GB300 (SM103a), at current main and with #6048 applied:
-
`tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`:
60 passed.
- `tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous.py`:
unchanged, 45 passed, 3 skipped.
- ruff check, ruff format and mypy are clean.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Prepared grouped GEMM launches can now use compatible, same-shaped
input and output tensors on each launch without changing the tensors
originally bound during preparation.
* Optional padding support lets routing indices use `-1` rows, which are
assigned to the preceding expert; leading padding rows are assigned to
expert 0. Padding rows count toward that expert, and their output values
are unspecified.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c93782c](https://github.com/flashinfer-ai/flashinfer/commit/c93782c53232fed4e78f8aca2383fbae64a427fc)

- **作者**: eigen
- **时间**: 2026-10-26T20:52:22Z
- **提交信息**: perf(cake_lm_head_loss): log-probability kernels, split-tail dX and lower per-call host overhead (#7449)

The Cake chunked LM-head + loss backend in FlashInfer
(`flashinfer.chunked_lm_head`) fuses the chunked large-vocabulary
projection (BF16 GEMM, FP32 accumulation) with log-sum-exp and the loss,
and has a memory-bounded backward. It ships one data type (BF16 X/W,
FP32 statistics and loss) in three entry forms: cross-entropy
(`chunked_lm_head_loss(..., objective="ce")`), clipped policy-gradient
(`chunked_lm_head_loss(..., objective="policy")`) and differentiable
per-token log-probability (`chunked_lm_head_logprob`). This PR updates
the backend on both architectures. It adds two new log-probability
kernels, splits the last dX GEMM wave and lowers per-call host overhead.
Against the previous Cake version on FlashInfer main, with
bitwise-identical outputs:

- **log-probability** (9 shapes): 1.024x-1.068x on GB300 and
1.023x-1.051x on B200.
- **loss, cross-entropy and policy** (22 shapes, 5 % ignored rows):
1.000x-1.041x on GB300 and 1.001x-1.024x on B200. Some large-T rows are
at parity (about 1.000x).
- **other shapes** (6): T=1 is 1.156x on GB300 and 1.099x on B200.
T=4095/4097 is 1.019x-1.034x. The 0 % and 30 % ignored-row shapes are
1.004x-1.005x. The T=16231, chunk-1024 cross-entropy shape is 0.998x on
GB300 (slightly slower) and 0.999x on B200.

| entry | T | chunk | H | V | ignored rows | GB300 previous (ms) | GB300
this PR (ms) | GB300 speedup | B200 previous (ms) | B200 this PR (ms) |
B200 speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|
| loss, ce | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 47.414 | 47.227
| 1.004x | 58.980 | 58.721 | 1.004x |
| loss, policy | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 46.473 |
46.351 | 1.003x | 57.928 | 57.726 | 1.004x |
| loss, ce | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 47.328 | 47.210
| 1.002x | 58.910 | 58.728 | 1.003x |
| loss, policy | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 46.388 |
46.207 | 1.004x | 57.882 | 57.606 | 1.005x |
| loss, ce | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 6.489 | 6.312 |
1.028x | 7.862 | 7.715 | 1.019x |
| loss, policy | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 6.479 | 6.224
| 1.041x | 7.788 | 7.605 | 1.024x |
| loss, ce | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 24.507 | 24.097 |
1.017x | 30.273 | 29.972 | 1.010x |
| loss, policy | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 24.160 |
23.665 | 1.021x | 29.729 | 29.386 | 1.012x |
| loss, ce | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 99.919 | 99.102
| 1.008x | 124.349 | 124.054 | 1.002x |
| loss, policy | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 97.571 |
96.837 | 1.008x | 121.062 | 120.968 | 1.001x |
| loss, ce | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 206.653 |
206.606 | 1.000x | 260.973 | 260.258 | 1.003x |
| loss, policy | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 201.991 |
201.938 | 1.000x | 255.459 | 254.724 | 1.003x |
| loss, ce | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 49.150 | 48.910
| 1.005x | 61.283 | 61.033 | 1.004x |
| loss, policy | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 48.210 |
47.939 | 1.006x | 60.193 | 59.869 | 1.005x |
| loss, ce | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 47.734 | 47.395
| 1.007x | 59.462 | 59.139 | 1.006x |
| loss, policy | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 46.962 |
46.519 | 1.010x | 58.487 | 58.127 | 1.006x |
| loss, ce | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 12.631 | 12.315 |
1.026x | 15.427 | 15.153 | 1.018x |
| loss, policy | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 12.526 |
12.098 | 1.035x | 15.233 | 14.928 | 1.020x |
| loss, ce | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 46.323 | 45.801
| 1.011x | 57.798 | 57.311 | 1.008x |
| loss, policy | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 45.599 |
45.012 | 1.013x | 56.773 | 56.333 | 1.008x |
| loss, ce | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 52.554 | 52.272
| 1.005x | 65.393 | 65.008 | 1.006x |
| loss, policy | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 51.426 |
51.161 | 1.005x | 64.141 | 63.820 | 1.005x |
| logprob | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 64.623 | 62.677 |
1.031x | 79.181 | 77.430 | 1.023x |
| logprob | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 64.643 | 62.720 |
1.031x | 79.095 | 77.103 | 1.026x |
| logprob | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 10.107 | 9.466 |
1.068x | 11.807 | 11.230 | 1.051x |
| logprob | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 33.870 | 32.326 |
1.048x | 41.431 | 39.935 | 1.038x |
| logprob | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 134.344 |
130.280 | 1.031x | 166.247 | 160.909 | 1.033x |
| logprob | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 274.808 |
268.473 | 1.024x | 344.944 | 333.287 | 1.035x |
| logprob | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 66.640 | 64.517 |
1.033x | 81.180 | 79.218 | 1.025x |
| logprob | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 65.086 | 63.111 |
1.031x | 79.797 | 77.649 | 1.028x |
| logprob | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 18.446 | 17.415 |
1.059x | 21.904 | 21.004 | 1.043x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (5 %) | 1.684 | 1.457 | 1.156x
| 1.592 | 1.448 | 1.099x |
| loss, ce | 4095 | 4096 | 6144 | 154880 | 205 (5 %) | 12.792 | 12.410 |
1.031x | 15.465 | 15.176 | 1.019x |
| loss, ce | 4097 | 4096 | 6144 | 154880 | 205 (5 %) | 12.863 | 12.436 |
1.034x | 15.521 | 15.192 | 1.022x |
| loss, ce | 16231 | 1024 | 6144 | 154880 | 812 (5 %) | 56.518 | 56.628
| 0.998x | 70.216 | 70.293 | 0.999x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 0 (0 %) | 49.843 | 49.655 |
1.004x | 62.029 | 61.794 | 1.004x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 4869 (30 %) | 34.880 |
34.729 | 1.004x | 43.317 | 43.111 | 1.005x |

Each time covers one forward + backward call: the GPU span from the
first to the last kernel, measured with CUPTI with a cold L2 and the GPU
idle-cooled before each call. Each value is the median pooled over 64
interleaved A/B rounds per shape on GB300 (sm_103a) and B200 (sm_100a)
with CUDA 13.4, and speedup = previous / this PR.

Cake ships no other data type, layout or fused form of this kernel, and
the backend covers sm_100a (B200/GB200) and sm_103a (B300/GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added configurable log-probability forward and backward paths,
including options for fused gradient and label-logit computation.
* Added split-tail gradient variants and a tuning option to control
split scheduling.
* Expanded kernel support for newer GPU architectures and added an
early-launch path for smaller batches.
* Reuse valid-row indices between forward and backward passes where
applicable, with host-side counting for smaller inputs.

* **Documentation**
* Updated the experimental guide with details on computation paths,
tuning options, pipeline configurations, and supported kernel variants.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c7f1e3d](https://github.com/flashinfer-ai/flashinfer/commit/c7f1e3dfe588e2c82b9e31b877bab0a7b1db39ba)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T20:47:39Z
- **提交信息**: fix(cake_dsv4): keep the BF16 H128 softmax statistics in each warp's TMEM lane quarter (#6895)

The Cake DeepSeek-V4 sparse-MLA backend (`backend="cake"`) ships BF16
and FP8 KV programs for 8 to 128 heads plus the NVFP4 KV decode family.
This PR changes the nine BF16 H128 programs (`bf16_h128_prefill_v42`,
`bf16_h128_prefill_v42_snake` and `bf16_h128_topk4x_v52` on each
architecture, and the `bf16_h128_topk128x` split4, row-first and
row-first V-split programs). Their per-row softmax statistics are now
stored and read back in each warp's own TMEM lane quarter, which
`tcgen05.ld` / `tcgen05.st` require. Outputs are bitwise identical to
the previous build, and speed is unchanged. The table compares against
the previous Cake version of the same programs on NVIDIA GB300 (SM103),
CUDA 13.3. Each latency is one BF16 H128 decode call (SWA 128 +
compressed cache, cold L2), the best of 12 alternating processes per
side; "cooled" adds an idle delay before every call.

| shape (tokens, sparse top-k, program) | before (us) | after (us) |
speedup | before, cooled (us) | after, cooled (us) | speedup, cooled |
|---|---|---|---|---|---|---|
| 3 tokens, top-k 1152, topk4x_v52 | 12.77 | 12.74 | 1.002x | 12.80 |
12.74 | 1.005x |
| 16 tokens, top-k 1152, topk4x_v52 | 22.18 | 22.18 | 1.000x | 22.14 |
22.18 | 0.999x |
| 64 tokens, top-k 1152, prefill_v42 | 22.05 | 22.05 | 1.000x | 22.08 |
22.05 | 1.001x |
| 120 tokens, top-k 1152, prefill_v42_snake | 33.76 | 33.76 | 1.000x |
33.79 | 33.79 | 1.000x |
| 3 tokens, top-k 384, topk128x split4 | 10.66 | 10.66 | 1.000x | 10.66
| 10.69 | 0.997x |
| 32 tokens, top-k 384, topk128x row-first V-split | 12.03 | 12.05 |
0.999x | 12.03 | 12.03 | 1.000x |
| 64 tokens, top-k 384, topk128x row-first | 14.56 | 14.56 | 1.000x |
14.56 | 14.56 | 1.000x |

The other Cake variants of this backend (BF16 and FP8 KV for 8 to 64
heads, FP8 H128, NVFP4 KV decode) are unchanged; the BF16 and FP8
programs ship for SM100 and SM103.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Corrected internal row addressing for softmax metadata and correction
processing.
- Improved alignment between score rows, output rows, and intermediate
metadata across supported GPU configurations.
- Helps ensure more reliable results during softmax and correction
stages without changing public interfaces.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6137d20](https://github.com/flashinfer-ai/flashinfer/commit/6137d204762766e58c7fe2a91e74dee79c6e23a8)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T20:46:07Z
- **提交信息**: fix(cake_deepseek_fused_routing): keep the selected group index below n_group by construction (#7111)

The Cake DeepSeek-V3 fused routing backend has one grouped kernel per
score/bias dtype pair (f32, f16, bf16 scores; f32, f16, bf16 bias), with
a DeepSeek-V3 specialization (E=256, 8 groups, top-4 groups, top-8) and
multi-token-per-CTA variants on SM 10.7. This PR changes the grouped
kernel's group selection so the selected group index stays below
`n_group` for every input. It is measured here against the previous Cake
version of the same kernel.

GB300 (sm_103a), CUDA 13.3, f32 scores and bias, PDL off, CUPTI median
latency (us); both versions loaded in one process and timed in
alternating order, the median of 8 rounds; "cooled" adds a delay kernel
before each call.

| T | E | top-k | n_group | topk_group | previous Cake (us) | this PR
(us) | ratio | previous Cake, cooled (us) | this PR, cooled (us) |
ratio, cooled |
|---|---|---|---|---|---|---|---|---|---|---|
| 4096 | 256 | 8 | 8 | 4 | 7.904 | 7.872 | 0.996x | 7.904 | 7.872 |
0.996x |
| 1024 | 256 | 8 | 8 | 4 | 3.488 | 3.488 | 1.000x | 3.488 | 3.488 |
1.000x |
| 1 | 256 | 8 | 8 | 4 | 2.784 | 2.784 | 1.000x | 2.784 | 2.784 | 1.000x
|
| 16 | 256 | 2 | 8 | 2 | 2.560 | 2.560 | 1.000x | 2.560 | 2.560 | 1.000x
|
| 32 | 96 | 5 | 3 | 2 | 2.656 | 2.656 | 1.000x | 2.656 | 2.656 | 1.000x
|
| 2 | 4 | 2 | 2 | 1 | 2.176 | 2.176 | 1.000x | 2.176 | 2.176 | 1.000x |

The other Cake variants of this kernel (the single-group kernel and the
SM 10.7 multi-token kernels) are unchanged; the family ships on sm_100a,
sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of tied routing group scores, helping ensure
consistent group selection when multiple groups share the highest score.
This update affects routing behavior only; no user-facing settings or
workflows have changed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8653fb0](https://github.com/flashinfer-ai/flashinfer/commit/8653fb02aa91e63ca7df0cfcf0bad05a5df474aa)

- **作者**: nvamyt
- **时间**: 2026-10-26T20:37:42Z
- **提交信息**: fix(tests): make Frost FMA routing nonzero (#7105)

<!-- .github/pull_request_template.md -->

## 📌 Description
The shared test config assigns a zero FC1 or FC2 input scale to every
even
expert. For the single-token FMA case, the seeded random routing can
select
only even experts, making the reference output identically zero before
any
Frost kernel is launched.

Use routes `0..k-1` for the single-token FMA case so the test retains
zero-scale coverage while guaranteeing nonzero-scale routes.
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
- make the single-token legacy Frost FMA routing deterministic
- cover both zero-scale and nonzero-scale experts
- prevent a seed-dependent all-zero reference result
## 🔍 Related Issues

<!-- Link any related issues here -->
#7096
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

* **Tests**
* Made the single-token test case use consistent expert assignments
instead of random routing.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [46d67ef](https://github.com/flashinfer-ai/flashinfer/commit/46d67ef62f8adeb3a50d13f5c143fdaba0f33396)

- **作者**: Adrian
- **时间**: 2026-10-26T20:13:17Z
- **提交信息**: test: add shared framework for CPU-only test relocation (#7465)

<!-- .github/pull_request_template.md -->

## 📌 Description

Create `tests/cpu/__init__.py` and register `@pytest.mark.cpu_only` in
`pytest.ini` as the foundation for the CPU-only test relocation series.

The configuration comment explicitly states that this marker only
identifies tests that do not use any GPU; it does not change test
behavior or execution. Registration in `pytest.ini` also works when the
parent `conftest.py` is excluded. Callers may select marked tests with
`-m cpu_only` or exclude them with `-m "not cpu_only"`.

Directory-specific tests, fixtures, reference data, and helpers remain
in their respective relocation PRs. Merge this PR first; all other CPU
test relocation PRs can then merge in any order.

## 🔍 Related Issues

Foundation for the CPU-only test relocation series.

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

This foundation contains no test functions. Independent collection
confirms no CPU tests are collected until a relocation PR is applied.
The relocation branches together collect the same 6,000 distinct CPU
cases with GPUs hidden and strict `cpu_only` marker selection.

Pre-commit checks passed for the relocation source changes; the two
additional import fixes passed Ruff checking and formatting
verification. The full repository test suite was not run.
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

This PR contains the CPU test package initializer and informational
marker registration. Test functions, fixtures, reference data, and
helpers are kept in their owning relocation PRs. AI-assisted test
refactoring.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded CPU-only validation for backend selection, host-side
operations, and related test fixtures.
* Improved test handling across environments with different hardware and
runtime support.
* Added expected-result checks for additional GPU-related operation
cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e400000](https://github.com/flashinfer-ai/flashinfer/commit/e400000d1cb112e7f2a3ce4f2a20feb618e726eb)

- **作者**: eigen
- **时间**: 2026-10-26T19:46:41Z
- **提交信息**: perf(cake_qsa_nvfp4): early block-table loads and the direct partial epilogue for the tcgen05 decode on compute capability 10.0 / 10.3 (#7460)

### [2751459](https://github.com/flashinfer-ai/flashinfer/commit/2751459afeb6c0771153fd50b09e9e3f4128dd01)

- **作者**: eigen
- **时间**: 2026-10-26T19:46:25Z
- **提交信息**: perf(cake_minimax_h3): faster NVFP4 pre-attention norm stage for four destinations on SM103 (#7458)

### [32f46c2](https://github.com/flashinfer-ai/flashinfer/commit/32f46c223fb2256e8e9e3440618ba0acb965801e)

- **作者**: eigen
- **时间**: 2026-10-26T19:46:07Z
- **提交信息**: perf(cake_grouped_mxfp8_quantize): per-K row-tiled programs exit CTAs past the valid rows, prefetch partial groups (#7457)

### [050e270](https://github.com/flashinfer-ai/flashinfer/commit/050e27087d9167284cf6ff6b4d340c0519e377f3)

- **作者**: eigen
- **时间**: 2026-10-26T19:44:41Z
- **提交信息**: perf(cake_fp8_attention): fold the K-mean bias into the exp2 argument and unroll the finalize (#7429)

### [1769ac7](https://github.com/flashinfer-ai/flashinfer/commit/1769ac747403630799e4b5b62e193054cde18980)

- **作者**: eigen
- **时间**: 2026-10-26T19:44:01Z
- **提交信息**: perf(cake_trtllm_mla_blackwell): faster aligned dense MLA decode programs for sm_100a and sm_103a (#7427)

### [bdd7215](https://github.com/flashinfer-ai/flashinfer/commit/bdd721538c2f4bd0f0ff13ec263da0d94e0ff0f0)

- **作者**: eigen
- **时间**: 2026-10-26T19:30:17Z
- **提交信息**: perf(cake_kimi_k3_fused_router): update router programs and dispatch on sm_100a/sm_103a (#7441)

`flashinfer.fused_moe.kimi_k3_fused_router` (package
`flashinfer/experimental/kimi_k3_fused_router/`) is FlashInfer's
experimental Kimi-K3 fused MoE router. It takes FP32 gate logits and an
FP32 bias for the Kimi-K3 MoE layer (896 experts, top-16). It selects
the top-16 experts per token and builds the expert-aligned route plan
(the `moe_align_block_size` layout) that grouped MoE GEMMs consume, all
in one launch. The router has one data type (FP32 logits and bias) and
two route block alignments (`block_m` 8 and 16). Each architecture has a
dispatch table over 28 measured cells (`num_tokens` 1, 2, 4, ..., 8192 x
`block_m` 8 / 16). This PR changes the router programs and the dispatch.
The API is the same and the outputs are bit-identical: the same top-16
ids, weights and route plan. The 1-token program now builds its route
plan in closed form. From 2 to 16 tokens, a cluster program gives each
token row its own CTA. The 32-token cell runs a new program with one
cluster of 16 CTAs that serves up to 32 token rows. The 256-token cell
launches with an explicit one-CTA cluster on both architectures, and on
sm_100a the 64- and 128-token cells do too. From 512 to 2048 tokens, the
dispatch now uses the number of clusters that can be co-resident on the
device to pick between the one-row-per-CTA program and the multi-row
program. From about twice that capacity it uses a warp-per-row
selection, on both sm_100a and sm_103a. The 4096- and 8192-token cells
run the grid as CTA pairs. On sm_100a every cell runs a changed program.
The baseline, labeled "FlashInfer main" below, is the previous Cake
version of this kernel, which is the set of router programs FlashInfer
main ships today.

NVIDIA GB300 (sm_103a), CUDA 13.4, median kernel latency; speedup =
FlashInfer main / this PR. The 64-, 128- and 512-token cells keep
FlashInfer main's programs (same machine code), so their speedup is
about 1.00x.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|
| 1 | 8 | 3.55 | 3.10 | 1.14x |
| 1 | 16 | 3.52 | 3.14 | 1.12x |
| 2 | 8 | 3.22 | 2.96 | 1.09x |
| 2 | 16 | 3.26 | 2.91 | 1.12x |
| 4 | 8 | 3.15 | 2.82 | 1.12x |
| 4 | 16 | 3.12 | 2.94 | 1.06x |
| 8 | 8 | 3.25 | 2.91 | 1.12x |
| 8 | 16 | 3.22 | 3.10 | 1.04x |
| 16 | 8 | 3.34 | 3.17 | 1.06x |
| 16 | 16 | 3.30 | 3.17 | 1.04x |
| 32 | 8 | 4.98 | 3.87 | 1.29x |
| 32 | 16 | 5.02 | 3.84 | 1.31x |
| 64 | 8 | 5.15 | 5.18 | 0.99x |
| 64 | 16 | 5.15 | 5.15 | 1.00x |
| 128 | 8 | 5.57 | 5.57 | 1.00x |
| 128 | 16 | 5.54 | 5.54 | 1.00x |
| 256 | 8 | 6.48 | 6.00 | 1.08x |
| 256 | 16 | 6.40 | 6.02 | 1.06x |
| 512 | 8 | 7.46 | 7.46 | 1.00x |
| 512 | 16 | 7.46 | 7.49 | 1.00x |
| 1024 | 8 | 9.68 | 9.47 | 1.02x |
| 1024 | 16 | 9.73 | 9.54 | 1.02x |
| 2048 | 8 | 13.54 | 12.38 | 1.09x |
| 2048 | 16 | 13.36 | 12.27 | 1.09x |
| 4096 | 8 | 17.36 | 16.82 | 1.03x |
| 4096 | 16 | 17.18 | 16.83 | 1.02x |
| 8192 | 8 | 22.83 | 22.62 | 1.01x |
| 8192 | 16 | 22.46 | 22.42 | 1.00x |

NVIDIA B200 (sm_100a), CUDA 13.4, median kernel latency; speedup =
FlashInfer main / this PR.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
|---:|---:|---:|---:|---:|
| 1 | 8 | 3.90 | 3.49 | 1.12x |
| 1 | 16 | 3.87 | 3.47 | 1.11x |
| 2 | 8 | 3.55 | 3.28 | 1.08x |
| 2 | 16 | 3.58 | 3.23 | 1.11x |
| 4 | 8 | 3.47 | 3.14 | 1.11x |
| 4 | 16 | 3.44 | 3.28 | 1.05x |
| 8 | 8 | 3.57 | 3.23 | 1.10x |
| 8 | 16 | 3.54 | 3.46 | 1.02x |
| 16 | 8 | 3.42 | 3.36 | 1.02x |
| 16 | 16 | 3.52 | 3.20 | 1.10x |
| 32 | 8 | 5.34 | 4.06 | 1.32x |
| 32 | 16 | 5.28 | 4.03 | 1.31x |
| 64 | 8 | 5.47 | 5.31 | 1.03x |
| 64 | 16 | 5.44 | 5.41 | 1.01x |
| 128 | 8 | 5.78 | 5.70 | 1.01x |
| 128 | 16 | 5.81 | 5.70 | 1.02x |
| 256 | 8 | 6.83 | 6.19 | 1.10x |
| 256 | 16 | 6.69 | 6.22 | 1.07x |
| 512 | 8 | 9.01 | 7.90 | 1.14x |
| 512 | 16 | 8.99 | 7.84 | 1.15x |
| 1024 | 8 | 12.08 | 10.24 | 1.18x |
| 1024 | 16 | 12.08 | 10.27 | 1.18x |
| 2048 | 8 | 17.02 | 12.96 | 1.31x |
| 2048 | 16 | 17.02 | 12.83 | 1.33x |
| 4096 | 8 | 18.32 | 17.79 | 1.03x |
| 4096 | 16 | 18.14 | 17.87 | 1.02x |
| 8192 | 8 | 23.98 | 23.84 | 1.01x |
| 8192 | 16 | 23.97 | 23.74 | 1.01x |

Cake ships no other data type, layout or fused form of this router, and
the family ships on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded Kimi K3 fused-router support with additional routing options
and dispatch across supported GPU architectures.
* Routing selection now accounts for device cluster capacity and launch
constraints, including clearer errors when available capacity is
insufficient.
* **Bug Fixes**
* Improved routing behavior across token counts and cluster
configurations, with updated validation and execution paths.
* **Tests**
* Added coverage for new routing options, capacity thresholds, launch
constraints, and device-based selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [215f83c](https://github.com/flashinfer-ai/flashinfer/commit/215f83cb27e39b6b973c0691b93fc378a53a10e4)

- **作者**: Yang Xu
- **时间**: 2026-10-26T18:04:53Z
- **提交信息**: perf(moe): overlap grouped activation staging on Ampere and Hopper (#7368)

<!-- .github/pull_request_template.md -->

## 📌 Description

Grouped low-token MoE projections spend part of their latency gathering
small activation rows before the weight/MMA pipeline can advance. This
change distributes gathering across the CTA and overlaps independent
work:

- Ampere K128 uses aligned CUTLASS 128-bit `cp.async` activation copies,
with scalar fallback and explicit zero filling for missing routes.
- Hopper distributes activation rows across four warps. BF16/FP16 issue
weight TMA before gathering; FP8 preserves gather-before-TMA ordering.
All activation writers publish stores and synchronize before
consumption.

The existing candidate domains, quantized layouts, numerical boundaries,
workspace ownership and untuned defaults are preserved. Dtype/activation
extensions will follow separately.

Scoped source checks and target-GPU suites pass. Independent review now
supplies the bounded baseline/head kernel measurements below, including
the stage-8 disjoint-route slowdown. These are kernel GPU times, not
serving throughput.

### Observed kernel GPU times

The [independent native
review](https://github.com/flashinfer-ai/flashinfer/pull/7368#issuecomment-6411766808)
compared merge-base `f83439d2a6e3` with unchanged head `8169674c3939`
using the existing `tc.runtime.launch` composition. Common workload:
BF16 SwiGLU, T4/H2048/I512, 40 experts, top-k10, K128. Each row fixes
the same tactic and routes on both revisions. Values are FC1 + FC2 +
ordered-combine GPU replay time in microseconds; compilation,
preparation and host submission are excluded.

| GPU / tactic `(group, stages)` | Routing | Warm base → head |
L2-flushed base → head |
|---|---|---:|---:|
| A100 `(4,4)` | shared | 70.53 → 59.52 | 90.11 → 78.85 |
| A100 `(4,4)` | disjoint | 205.15 → 191.14 | 226.30 → 211.97 |
| H100 `(2,4)` | shared | 49.19 → 42.68 | 59.01 → 52.80 |
| H100 `(2,4)` | disjoint | 90.91 → 88.20 | 104.80 → 102.43 |
| H100 `(2,8)` | disjoint | **137.62 → 142.47** | **150.75 → 156.58** |

A100 PCIe 40GB and H100 NVL used Python 3.12, PyTorch 2.13.0+cu130 and
CuTe DSL 4.8.0. Each entry is the median of 11 alternating base/head
samples. Warm measurements use 32-call graph chains; cold measurements
flush 128 MiB before a single-call graph, outside its timed interval.
Shared routes use ten common experts; disjoint routes use forty
different experts.

The H100 stage-8 disjoint configuration is slower: about 3.5% warm and
3.9–4.5% cold, reproduced in a second process. Retain this tradeoff
alongside the gains. These fixed-tactic comparisons do not establish an
autotuned-winner/default regression or universal improvement. Numerical
references and four output-poisoned replays passed; the unchanged A100
T8/K64 control stayed within 0.3%. See the linked review for the
complete scope and validation method.

## 🔍 Related Issues

Builds on #7194, #7204 and #7212.

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

- Scoped pre-commit hooks and `git diff --check` pass for all changed
files.
- Targeted GPU suites: `tests/moe/test_frost_low_latency_grouped_tc.py`,
`test_frost_low_latency_grouped_fp8.py`, and
`test_frost_low_latency_grouped_block_fp8.py`.
- Current head `8169674c3939305b60403b5b56c2faaaad7fd800`: the three
targeted suites passed with 194 passed / 20 skipped on SM90. Staged
source hashes were verified before and after execution against the clean
PR branch.
- The independent native follow-up additionally reports A100 grouped-TC
**153 passed, zero skipped**, H100 **194 passed, 20 expected skips**,
and bounded stage-reuse racecheck probes with zero
hazards/errors/warnings on both GPUs. These are the reviewer's
already-public results, separate from CI skips below.

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


### CI execution scope

CI job status is not counted as kernel execution evidence. The public
targeted H100 job completed successfully, but its JUnit report contains
**214 skips and zero executed tests** because the image has CuTe DSL
4.7.0 and these tests require 4.8 or newer.

The internal H100 job also used **CuTe DSL 4.7.0 and skipped all 214
tests**. It is therefore **not counted as kernel validation**. The
same-head local H100 run reported above used CuTe DSL 4.8.0 and executed
**194 passing tests, with 20 expected architecture skips**.

All six public AOT/import CI jobs have now passed. These build/import
checks are separate from GPU kernel execution coverage.

## Reviewer Notes

Please check stage acquisition before cooperative writes, publication of
activation stores, async-copy completion participation, and
producer/consumer stage reuse. The weight TMA completion barrier does
not by itself publish activation stores from other warps.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved grouped projection data loading on supported Ampere and
Hopper configurations, including more efficient activation gathering and
weight loading.
* Ampere K128 copies use an optimized path for 16-byte-aligned inputs;
unaligned inputs and other tile sizes retain the existing fallback
behavior.

* **Documentation**
* Added details on grouped projection staging, synchronization
requirements, and the existing K64 schedule.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [801fcd0](https://github.com/flashinfer-ai/flashinfer/commit/801fcd0a52ccf40bd28d15de25eda663887d5a58)

- **作者**: Krrety
- **时间**: 2026-10-26T18:03:15Z
- **提交信息**: perf(gdn): skip all-zero MMA tiles in SM12x prefill (#6371)

<!-- .github/pull_request_template.md -->

## 📌 Description

SM12x GDN non-CP prefill currently issues dense MMA sequences for NewV
and the O2 output contribution, although their right operands are upper
triangular. Skip the K16/N8 tiles that lie entirely below the diagonal.
For each M16 row tile, the 64×64 right operand is divided into 4×8
K16/N8 tiles; skipping the 12 all-zero tiles reduces the number of
M16×N8×K16 tile multiply-accumulates from 32 to 20.

In an upper-triangular matrix, entries with a row index greater than
their column index are zero. A right-operand tile spans row indices
`16*k` through `16*k+15` and column indices `8*n` through `8*n+7`. If
the tile's minimum row index exceeds its maximum column index (`16*k >
8*n+7`), the entire tile lies below the main diagonal and can be
skipped. Tiles intersecting the main diagonal are still computed, and
each output retains increasing K accumulation order.

![K16/N8 tiles of the upper-triangular right operand: keep 20, skip
12](https://raw.githubusercontent.com/ZYHSGTC/flashinfer-gdn-triangular/727125bb4d6cfa4e48c3537a2b00b6faacec0019/pr-assets/gdn-triangular/triangular_mma_tiles_en.png)

[SVG
version](https://raw.githubusercontent.com/ZYHSGTC/flashinfer-gdn-triangular/727125bb4d6cfa4e48c3537a2b00b6faacec0019/pr-assets/gdn-triangular/triangular_mma_tiles_en.svg)

Median per-call GPU time:

| Dtype | B | S | Initial state | CTAs | Main ms | PR ms | Time
reduction |
|---|---:|---:|---|---:|---:|---:|---:|
| BF16 | 32 | 64 | None | 512 | 0.175810 | 0.174033 | 1.01% |
| BF16 | 1 | 512 | None | 16 | 0.066301 | 0.062508 | 5.72% |
| BF16 | 4 | 512 | None | 64 | 0.204610 | 0.191068 | 6.62% |
| BF16 | 32 | 512 | None | 512 | 1.189631 | 1.112037 | 6.52% |
| BF16 | 32 | 512 | FP32 | 512 | 1.357690 | 1.265710 | 6.77% |
| BF16 | 64 | 512 | None | 1024 | 2.331671 | 2.189030 | 6.12% |
| BF16 | 128 | 512 | None | 2048 | 4.604309 | 4.338683 | 5.77% |
| BF16 | 4 | 8192 | None | 64 | 3.084980 | 2.908633 | 5.72% |
| FP16 | 32 | 64 | None | 512 | 0.173133 | 0.172345 | 0.46% |
| FP16 | 32 | 512 | None | 512 | 1.178832 | 1.114246 | 5.48% |
| FP16 | 32 | 512 | FP32 | 512 | 1.359507 | 1.269153 | 6.65% |
| FP16 | 128 | 512 | None | 2048 | 4.601099 | 4.353029 | 5.39% |
| FP16 | 4 | 2048 | None | 64 | 0.777453 | 0.734873 | 5.48% |

Compared with main `c0e62fa7b18cbf051f729214984c235eb521a551` on RTX
5060 (SM120, 30 SMs). Hq=Hk=Hv=16, D=128, alpha/beta enabled, scale=1.0,
FP32 final state. Initial state is absent or random FP32 state scaled by
0.01, as indicated in the table. Times are median per-call GPU times
measured with CUDA events over 21 paired rounds with alternating
execution order, after 10 warmup calls and at least 0.6 s of graph
warmup; each CUDA Graph contains 40 calls and is replayed twice per
round, with at least 0.25 s of additional warmup before each paired
comparison. Measurements use shared output/state buffers. PyTorch
2.12.0+cu130, CUTLASS DSL 4.7.0; seed=123, q/v scaled by 0.1, normalized
k, and uniform random FP32 alpha/beta. Outputs and final states are
bitwise identical to the baseline for all configurations shown.

The 11 multi-chunk configurations above show 5.39–6.77% lower GPU time.
Single-chunk short sequences have limited benefit and are sensitive to
measurement conditions. Performance measurements are for the non-CP path
with FP32 final-state storage and scale=1.0 on this SM120 GPU; they do
not establish gains on SM121, CP, or other state-storage formats.

## 🔍 Related Issues

N/A.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validation on RTX 5060:

```bash
pytest -q tests/gdn/test_prefill_delta_rule.py
```

2,760 passed, 868 skipped, zero failures. Skips follow the existing test
rules. Changed-file pre-commit hooks passed.

For FP16/BF16 with and without FP32 initial state, normalized PTX, SASS
instructions, CUBIN executable bytes, and resource usage match
`e1898c49860eaacabd31848af25661094e489371`.

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

* **Performance Improvements**
* Delta-rule processing on supported SM120 hardware now avoids
calculations in triangular regions that would produce zero values. This
reduces redundant computation and can improve prefill performance, while
preserving the existing results and behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Krrety <zyhsgtc@outlook.com>

### [f45e1d6](https://github.com/flashinfer-ai/flashinfer/commit/f45e1d6fdd62833ff8aa922f9eb139d590002ff8)

- **作者**: Thien Tran
- **时间**: 2026-10-26T18:02:33Z
- **提交信息**: fix(gdn): accept element-size-aligned gate and parameter views in decode wrappers (#6337)

## 📌 Description

The GDN decode wrappers wrap the scalar-loaded operands (`a`, `b`,
`A_log`, `dt_bias`) with `from_dlpack(..., assumed_align=16)` (`32` on
the BF16-state path). Contiguous views whose base pointer is only
element-size aligned are valid inputs but get rejected at launch:

```python
gates = torch.randn(B, 2 * HV, dtype=torch.bfloat16, device="cuda")
b, a = gates.chunk(2, dim=-1)   # a's base is HV * 2 = 8 bytes in when HV % 8 != 0
# gated_delta_rule_decode_pretranspose(..., a=a, ...) raises:
# RuntimeError: Tensor data pointer is not aligned to 16 bytes.
```

All four operands are read exclusively through scalar indexed,
dtype-converting loads in every affected kernel body:

```python
r_A_log   = cutlass.Float32(A_log[i_hv])
r_a       = cutlass.Float32(a[i_n, i_t, i_hv])
r_dt_bias = cutlass.Float32(dt_bias[i_hv])
r_b       = cutlass.Float32(b[i_n, i_t, i_hv])
```

so element-size alignment is the true requirement — which is also the
`from_dlpack` default (`assumed_align=None` → element size). Changes:

- `gdn_decode_pretranspose.py`, `gdn_decode_nontranspose.py`,
`gdn_decode_mtp.py`: drop the `assumed_align=16` argument on
`a`/`b`/`A_log`/`dt_bias`.
- `gdn_decode_bf16_state.py`: give `a`/`b` explicit
`assumed_align=element_size()` at the three compile sites (the shared
`_mark_batch_dynamic` helper defaults to 32 and is also used for the
vectorized `q`/`k`/`v`/`o`, which are unchanged). Same style as #4583's
`dt_bias` handling; this covers the gate operands that PR does not.
- `q`/`k`/`v`/`o`, state pools, and index tensors keep their existing
alignment declarations.

**No codegen change.** Fresh compiles on sm_103a with all caches
disabled (`FLASHINFER_CUTE_DSL_DISABLE_CACHE=1`,
`CUTE_DSL_DISABLE_FILE_CACHING=1`):

| Path | align=16/32 vs element-size |
|---|---|
| pretranspose (fp32, T=1) | cubin byte-identical |
| nontranspose (fp32, T=1) | cubin byte-identical |
| MTP (fp32, T>1) | SASS identical; only the mangled symbol name differs
(`gmemalign16` in the descriptor) |
| BF16-state T=1 and MTP | SASS identical; cubins differ by 12 bytes in
embedded debug sections only |

CUPTI timing (`bench_gpu_time_with_cupti`, cold L2, GB300, median of 200
iters) is unchanged, e.g. fp32 pretranspose at B=64/HV=32: 45.41 µs
(before) vs 45.34 µs (after); B=256: 167.46 µs vs 167.49 µs.

Adds a regression test comparing misaligned gate/param views against
contiguous clones bit-for-bit; it fails before this change
(`RuntimeError: ... not aligned to 16 bytes`) and passes after.

Downstream motivation: vLLM's opt-in FlashInfer GDN decode integration
(vllm-project/vllm#60403) currently works around this by cloning the
gates when `num_v_heads % 8 != 0`; this fix lets it drop the clone.

AI-assisted change.

## 🔍 Related Issues

- #4582 (same bug class on the BF16-state path parameters; #4583 covers
`A_log`/`dt_bias` there, this PR covers the `a`/`b` gates)
- vllm-project/vllm#60403

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

(Note: ran `pre-commit run --files <changed files>`; all hooks pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On GB300 (SM103), torch 2.13/cu130:

- New: `pytest
tests/gdn/test_decode_delta_rule.py::test_decode_pretranspose_accepts_scalar_aligned_views`
— fails without the fix, passes with it.
- Regression: `pytest tests/gdn/test_decode_delta_rule.py -k "packed_qkv
or scalar_aligned or (nontranspose and not full)"` — 20 passed.

## Reviewer Notes

- The BF16-state hunk sits two lines above #4583's `A_log`/`dt_bias`
hunks; whichever lands second should rebase cleanly.
- WY kernels (`gdn_decode_bf16_wy_*`) are not wired into the
`gdn_decode.py` dispatch and were left untouched.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Decode operations now handle parameter tensors that are aligned to
their element size, including offset views, without relying on stricter
alignment assumptions.
* Added coverage confirming that decoding with these views produces the
same outputs and updated state as decoding with contiguous parameters.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1257bb4](https://github.com/flashinfer-ai/flashinfer/commit/1257bb40fd11a4f89abc13e87f38e84083697157)

- **作者**: cyanseek
- **时间**: 2026-10-26T18:01:56Z
- **提交信息**: perf(sampling): defer last-valid-index reduction until fallback (#5352)

<!-- .github/pull_request_template.md -->

## 📌 Description

Probability sampling currently performs an integer block-max reduction
for the last valid token on every scanned vocabulary tile, although that
index is only consumed if the CDF scan fails to select a token. Retain
each thread's candidate across tiles and reduce it only when the scan
ends without a selection. This removes the fallback collective from the
normal path while preserving the probability accumulation, CDF, RNG
progression, predicates, and final shared-storage barrier. Each
rejection round starts with a fresh candidate; the speculative residual
scan does the same.

The included benchmark measures the sampler alone and Torch softmax
followed by sampling (FP32 Gaussian logits, std=1, seed=42, top-k=50).
Results below use the revised benchmark: an independent Python RNG
shuffles all 10 sampler/softmax combinations per shape with
`--order-seed 42`, and every row records its execution index. Each A/B/A
run uses the same permutation, matching inputs within each mode, and
separate JIT caches. These are same-GPU CUDA-graph medians; “before” is
the mean of the two baseline medians. Five warmups and 30 timed replays;
compilation and input creation are excluded.

| GPU | B | V | top-k + Torch softmax, before | after | latency
reduction |
| --- | ---: | ---: | ---: | ---: | ---: |
| RTX 4090 | 1 | 151936 | 311.65 us | 287.54 us | 7.7% |
| RTX 4090 | 16 | 151936 | 370.33 us | 342.94 us | 7.4% |
| RTX 4090 | 128 | 151936 | 619.65 us | 589.52 us | 4.9% |
| A100 80GB PCIe | 1 | 151936 | 537.34 us | 474.11 us | 11.8% |
| A100 80GB PCIe | 16 | 151936 | 553.83 us | 486.71 us | 12.1% |
| A100 80GB PCIe | 128 | 151936 | 1023.59 us | 902.40 us | 11.8% |

These are sampling-stage latencies. The affected probability APIs can
run at each non-greedy decoding step; gains depend on the sampler and
shape. Model-forward and serving-throughput measurements are outside
this benchmark.

Reproduce with the same benchmark file on both revisions, each installed
from source with its pinned submodules and its own
`FLASHINFER_WORKSPACE_BASE`:

```bash
python benchmarks/bench_sampling_fallback.py --vocab-sizes 111 4096 151936
python benchmarks/bench_sampling_fallback.py --cold-l2
python benchmarks/bench_sampling_fallback.py --vocab-sizes 111 4096 151936 --non-deterministic
```

Cold-L2 runs rotate enough input buffers to exceed the device's cache
and visit every buffer before replay. For the six top-k + softmax rows
at V=151936, cold-L2 latency reductions ranged from 3.7% to 12.4%. The
complete comparison covers 420 GPU/shape/sampler/mode combinations,
including small-vocabulary controls and both deterministic settings.


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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- `pytest tests/utils/test_sampling.py -q`: **1,889 passed, 120
skipped** on both baseline and patch on A100 80GB PCIe with the final
test parameters. The 120 skips are existing parameter guards; no tests
were deselected for these full runs. The unchanged kernel was also
previously validated with the original 60-case regression version on RTX
5090: 1,857 passed, 120 skipped on each revision.
- The final targeted regression suite passes **92 cases** on baseline
and patch on RTX 4090 as well: 20 indexed/boundary/invalid-row cases, 40
normal-selection graph cases, and 32 tiny-mass graph fallback cases for
plain/top-k/top-p/joint. Graph replay changes the nonzero positions
while retaining the selected mass. Min-p keeps mass=1 because it scales
its uniform by the eligible mass.
- An isolated, uncommitted fault-injection check forces the fallback
candidate to token 0: all 32 tiny-mass graph cases fail, while all 40
normal-selection cases pass. The top-k and joint fixtures use k=2 so a
retry cannot mask that wrong zero-probability fallback.
- Additional 1,848-case baseline/patch output comparisons from the
unchanged kernel validation were bitwise identical on each of RTX 5090
and A100, including plain/top-k/top-p/min-p/joint and chain speculative
sampling, both deterministic settings and multiple offsets of seed 42.
- Compute Sanitizer synccheck and racecheck: all 92 final regression
cases pass with zero errors/hazards on each of RTX 4090 and A100. The
earlier 12 speculative boundary cases also pass memcheck, synccheck, and
racecheck with zero errors/hazards.
- RTX 5090 memcheck: the original 60-case regression suite passed with
zero reported errors on both baseline and patch.
- All applicable `pre-commit run --all-files` hooks pass.

CUDA compiler 12.8 throughout. The revised measurements use Torch
2.11.0+cu128, with driver 580.126.09 on RTX 4090 and 570.133.20 on A100.
The earlier RTX 5090 validation used Torch 2.13.0+cu130 / driver
610.57.04. Comparisons are within each environment.

Sanitizer limitation: default unsuppressed Compute Sanitizer 2025.1
memcheck reports one `CUDA_ERROR_INVALID_HANDLE` from
`cuKernelGetFunction` at the first sampling launch, identically on
baseline and patch: in the earlier 60-case A100 run and the final
92-case RTX 4090 run. All test assertions pass and no device-memory
errors were reported. The A100 report also reproduced with both LAZY and
EAGER module loading; these are not counted as clean memcheck runs.

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

AI-assisted implementation and validation. Please focus review on the
block-uniform fallback condition and candidate lifetime across rejection
rounds. The last-valid predicate still excludes out-of-range vector
lanes; an empty/NaN row retains the existing invalid-result behavior.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved probability sampling when cumulative probability is
insufficient, ensuring a valid fallback token is selected across
sampling modes and edge cases.
- Preserved correct results for deterministic and nondeterministic
sampling, including very small or invalid probability values.

- **Tests**
- Added regression coverage for vocabulary sizes near processing
boundaries and multiple index types.
- Expanded CUDA graph replay coverage across plain, top-k, top-p, min-p,
and combined sampling scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: cyanseek <cyanseek@outlook.com>

### [55b2e33](https://github.com/flashinfer-ai/flashinfer/commit/55b2e33697c45fd0b92659711631d35a2e6ecec0)

- **作者**: Guoming Zhang
- **时间**: 2026-10-26T17:59:26Z
- **提交信息**: fix(gdn): keep state stride alignment for indexed SM100 prefill (#5492)

## 📌 Description

With `state_indices`, the SM100/SM103 GDN prefill kernel
(`GatedDeltaNetChunkedKernel`) runs up to ~3.2x slower than with a
packed initial state. Both paths produce bitwise-identical results.

**Cause.** In pool mode, `_mark_state_layout` applies only
`mark_layout_dynamic()` so that padded slot strides are accepted. That
drops the stride divisibility the packed path gets from
`mark_compact_shape_dynamic(..., divisibility=DK)`. The per-(sequence,
head) state load/store in `_load_initial_state` / `_store_final_state`
then vectorizes narrower. The cost is fixed per work item, so it
dominates when a call holds many short sequences, e.g. chunked prefill
at high concurrency.

**Fix.** The wrapper computes the largest power of two (at most the head
size) that divides the slot, head and V strides of the initial and
output state. It adds that value to the compiled-kernel cache key and
kernel name, and the kernel applies it with `cute.assume()` when it
builds the state view. This covers compact and padded pools. Packed mode
and the CP path are unchanged.

### How to trigger

All of these must hold:
- SM100/SM103, non-CP path: `use_cp=False`, or `use_cp="auto"` with
`num_seqs * num_heads * 4 >= num_sms`.
- `state_indices` is passed, with the state pool as `initial_state` and
`output_state`.
- The call holds several sequences. The slowdown grows with the sequence
count and shrinks as sequences get longer.

The script below uses only the public API and times
`GatedDeltaNetChunkedKernel` with `torch.profiler`:

<details><summary>repro_gdn_indexed_state.py</summary>

```python
"""Minimal repro: SM100 GDN prefill is slower with state_indices than with a packed state.

Both variants compute bit-identical results; only the state I/O differs.
Run on an SM100/SM103 GPU: python repro_gdn_indexed_state.py
"""

import torch
import torch.nn.functional as F
from torch.profiler import ProfilerActivity, profile

from flashinfer.gdn_prefill import chunk_gated_delta_rule

HQ, HV, D, TOTAL, N_POOL = 16, 48, 128, 2048, 512
dev = torch.device("cuda")


def kernel_us(fn, iters=20):
    """Median GatedDeltaNetChunkedKernel time in microseconds (host overhead excluded)."""
    for _ in range(3):
        fn()
    torch.cuda.synchronize()
    with profile(activities=[ProfilerActivity.CUDA]) as prof:
        for _ in range(iters):
            fn()
        torch.cuda.synchronize()
    times = sorted(
        e.device_time_total for e in prof.events() if "GatedDeltaNetChunkedKernel" in e.name
    )
    return times[len(times) // 2]


def make_pool(layout):
    if layout == "compact":  # [N_pool, H, V, K]
        return torch.zeros(N_POOL, HV, D, D, dtype=torch.bfloat16, device=dev)
    # 4 same-shape layers coalesced into each slot: slot stride = 4 * H * V * K
    return torch.zeros(N_POOL, 4, HV, D, D, dtype=torch.bfloat16, device=dev)[:, 1]


torch.manual_seed(0)
q = F.normalize(torch.randn(TOTAL, HQ, D, device=dev), dim=-1).bfloat16()
k = F.normalize(torch.randn(TOTAL, HQ, D, device=dev), dim=-1).bfloat16()
v = torch.randn(TOTAL, HV, D, device=dev).bfloat16()
g = 0.9 + 0.1 * torch.rand(TOTAL, HV, device=dev)  # linear-space decay
beta = torch.rand(TOTAL, HV, device=dev)
out = torch.empty(TOTAL, HV, D, dtype=torch.bfloat16, device=dev)

print(f"{'pool':<9}{'seqs':>5}{'packed us':>11}{'indexed us':>12}{'ratio':>7}  bitwise")
for layout in ("compact", "coalesced"):
    for num_seqs in (1, 16, 128):
        cu = torch.arange(0, TOTAL + 1, TOTAL // num_seqs, dtype=torch.int32, device=dev)
        pool = make_pool(layout)
        pool.copy_(0.05 * torch.randn_like(pool))
        idx = torch.arange(num_seqs, dtype=torch.int32, device=dev) * 3
        rows = idx.long()
        pool0 = pool.clone()

        def packed():
            state = pool[rows]  # gather into [num_seqs, H, V, K]
            final = torch.empty_like(state)
            chunk_gated_delta_rule(
                q, k, v, g, beta, initial_state=state, output_final_state=True,
                cu_seqlens=cu, output=out, output_state=final, use_cp=False,
            )
            pool[rows] = final  # scatter back

        def indexed():
            chunk_gated_delta_rule(
                q, k, v, g, beta, initial_state=pool, output_final_state=True,
                cu_seqlens=cu, output=out, output_state=pool, state_indices=idx,
                use_cp=False,
            )

        pool.copy_(pool0)
        packed()
        ref_out, ref_state = out.clone(), pool[rows].clone()
        pool.copy_(pool0)
        indexed()
        same = torch.equal(out, ref_out) and torch.equal(pool[rows], ref_state)

        t_packed, t_indexed = kernel_us(packed), kernel_us(indexed)
        print(
            f"{layout:<9}{num_seqs:>5}{t_packed:>11.1f}{t_indexed:>12.1f}"
            f"{t_indexed / t_packed:>7.2f}  {same}"
        )
```

</details>

Indexed / packed kernel time. Outputs and final states are
bitwise-identical in every case.

| pool layout | seqs | before | after |
|---|---|---|---|
| compact | 1 | 1.40 | 0.99 |
| compact | 16 | 3.20 | 0.96 |
| compact | 128 | 3.17 | 0.89 |
| 4 layers per slot | 1 | 1.40 | 0.99 |
| 4 layers per slot | 16 | 3.29 | 0.95 |
| 4 layers per slot | 128 | 3.18 | 0.90 |

## 🔍 Related Issues

Found while adopting `state_indices` in NVIDIA/TensorRT-LLM#17365.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files and fixed any reported
issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- `test_state_stride_divisibility`: divisibility derived from compact,
coalesced, padded and non-unit-K layouts.
- `test_prefill_state_indices_compact_and_padded_pools_in_one_process`:
alternates compact and padded pools with identical shapes in one process
and checks every call against the packed baseline bitwise.
- `test_prefill_name_varies_with_every_argument`: covers the new
cache-key component.
- `test_blackwell_prefill_workspace_not_in_compile_cache`: passes the
new key component when it rebuilds the cache key.
- [x] All tests are passing on SM100 for
`tests/gdn/test_prefill_delta_rule.py`,
`test_prefill_qk_normalization.py`, `test_prefill_state_indices.py`,
`test_cute_dsl_kernel_cache.py`, `test_prefill_cp_delta_rule.py`,
`test_prefill_auto_backend.py`, `test_multistream_overlap.py` and
`test_gdn_device_target.py`: 3422 passed, 866 skipped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved Blackwell prefill handling of recurrent state buffers with
different stride alignments, including compact and padded layouts used
within the same process.
* Kernel selection now accounts for state-buffer alignment, helping
maintain correct results when switching between layouts across supported
low-precision data types.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Guoming Zhang <137257613+nv-guomingz@users.noreply.github.com>

### [84fb433](https://github.com/flashinfer-ai/flashinfer/commit/84fb433aaec9ef3e978fbb7874c729257626d599)

- **作者**: Sam Mausberg
- **时间**: 2026-10-26T17:58:18Z
- **提交信息**: perf(activation): split act_and_mul rows across blocks for small batches (#5614)

## Description

`silu_and_mul`, `gelu_and_mul` and `gelu_tanh_and_mul` run
`act_and_mul_kernel`, which launches one block of `min(d / vec_size,
256)` threads per token. Each thread walks its share of the row in a
loop, and every iteration waits for its two 16-byte loads before it
computes, stores and issues the next loads. At decode batch sizes this
leaves the GPU mostly idle. With 16 tokens and d = 14336 in bf16, 16
blocks run on 16 of the 132 SMs of a GH200, and each thread makes 7
dependent round trips to memory. The kernel takes 4.96 us for 1.4 MB,
about 280 GB/s.

This PR adds `act_and_mul_split_kernel`. It computes the same thing, but
the blocks of one row are consecutive in the grid (`blockIdx.x = row *
split + chunk`), and when a thread has more than one vector it issues
the loads for both before converting and computing. The launcher picks
it only when there are fewer tokens than 2 blocks per SM and a row needs
more than one block. It then splits each row across enough blocks for
about 2 per SM, or more, up to 4 per SM in total, until each thread
handles at most 2 vectors. For the example above that is 7 blocks per
row, 112 blocks in all, and one load round trip per thread: 1.95 us.

Batches of at least 2 x num_SMs tokens (264 on this GPU), and rows that
fit in one block (d <= 2048 in fp16/bf16), keep the existing
`act_and_mul_kernel`, which is unchanged. I stopped at 2 tokens per SM
because from 264 to 527 tokens the rule would only ever pick the
unrolled one-block-per-row launch, and that launch was not reliably
faster there: bf16 `gelu_tanh_and_mul` at 512 tokens and d = 3584 to
8192 was 2 to 7% slower (5 repeated interleaved runs), while silu gained
up to 1.18x. The element math and the fp32 conversions are the same as
before, so outputs are bitwise identical; the A/B sweep below compared
every output with the old kernel's.

### Performance

NVIDIA GH200 480GB (sm_90a, 132 SMs), CUDA 12.8, driver 570, torch
2.11.0+cu128, bf16. Times are per call from
`flashinfer.testing.bench_gpu_time` with CUDA graphs (100 calls per
graph); cold L2 rotates input buffers larger than L2. Each cell is the
median of 3 runs of the benchmark, alternating between main (8589d49b)
and this branch. The GPU was shared with other jobs, and a few
individual runs were up to 2x slow, which is why I report medians of
alternating runs.

Cold L2, before / after in us:

| tokens | silu d=4096 | silu d=14336 | silu d=28672 | gelu d=14336 |
gelu_tanh d=14336 |
|---:|---:|---:|---:|---:|---:|
| 1 | 1.28 / 1.00 | 3.00 / 1.12 | 5.23 / 1.14 | 5.46 / 1.27 | 2.82 /
1.10 |
| 16 | 1.70 / 1.27 | 4.96 / 1.95 | 8.93 / 2.29 | 9.06 / 2.52 | 4.92 /
1.93 |
| 64 | 2.39 / 1.97 | 5.74 / 3.10 | 10.34 / 4.62 | 9.72 / 4.34 | 5.72 /
3.25 |
| 128 | 2.66 / 2.39 | 6.65 / 4.61 | 12.04 / 7.77 | 10.81 / 5.57 | 6.63 /
4.58 |
| 256 | 3.46 / 3.28 | 8.97 / 7.75 | 16.48 / 14.13 | 12.76 / 9.75 | 8.97
/ 7.88 |
| 512 (unchanged kernel) | 5.04 / 5.04 | 14.04 / 14.07 | 26.70 / 26.71 |
17.53 / 17.38 | 14.08 / 14.06 |
| 1024 (unchanged kernel) | 8.61 / 8.61 | 26.48 / 26.46 | 51.78 / 51.81
| 31.38 / 31.37 | 26.47 / 26.50 |
| 16384 (unchanged kernel) | 110.45 / 110.40 | 385.51 / 385.44 | 776.49
/ 776.41 | 408.64 / 409.05 | 385.32 / 385.53 |

Hot L2 (one buffer reused), same benchmark: silu d=14336 goes from 3.17
to 1.17 us at 16 tokens and from 3.52 to 2.31 us at 128 tokens; gelu
d=14336 goes from 5.61 to 1.43 us at 16 tokens. Hot-L2 runs of the
larger shapes (512 tokens and up) varied by up to 2x between runs on the
shared GPU, so I do not report them from this benchmark; the interleaved
sweep below covers them.

Reproduce (run once on main and once on this branch):

```bash
python benchmarks/bench_act_and_mul.py --acts silu gelu gelu_tanh \
    --num-tokens 1 16 64 128 256 512 1024 16384 --hidden-sizes 4096 14336 28672
python benchmarks/bench_act_and_mul.py --acts silu gelu gelu_tanh \
    --num-tokens 1 16 64 128 256 512 1024 16384 --hidden-sizes 4096 14336 28672 --hot
```

I also ran a wider A/B sweep with a separate harness that builds the old
kernel next to the new one and replays both in CUDA graphs, alternating,
in one process: silu, gelu and gelu_tanh; fp16 and bf16; hot and cold
L2; tokens 1, 2, 4, ..., 16384 plus 96, 150, 200, 240, 263, 264 and 400;
d = 768, 1024, 1408, 1536, 2048, 3584, 4096, 5632, 8192, 11008, 12288,
14336, 16384, 18432 and 28672 (3456 points). All outputs were bitwise
equal to the old kernel's.

- The 1500 points that take the new kernel measured 0.996x to 7.15x
(geometric mean 1.73x). The lowest were bf16 gelu at 256 tokens and d =
14336 with hot L2 (7.225 vs 7.252 us, 0.996x after 5 repeated runs) and
bf16 gelu_tanh at 256 tokens and d = 4096 with cold L2 (0.997x).
- Gains shrink as the batch approaches the threshold. From 200 to 263
tokens the new-kernel points range from 1.00x to 1.57x, with a geometric
mean of 1.16x at each token count measured; for example, silu at 200
tokens and d = 14336 goes from 7.94 to 6.40 us cold and from 4.08 to
3.71 us hot.
- The 1956 points that keep the old kernel (d <= 2048, or 264 tokens and
more) measured 0.974x to 1.047x. They run the same code before and
after, so this is the noise of the harness on the shared GPU.

In eager mode, back-to-back calls through the Python API take about 4.5
to 6 us each for most decode shapes, before and after, because host
overhead dominates; the change shows up there only when the old kernel
was slower than that, for example gelu 1 x 28672 goes from 10.55 to 5.20
us per call (single runs, not interleaved). Calling the compiled op
directly back to back, which removes the Python wrapper, shows the
kernel change: silu 16 x 14336 goes from 3.16 to 1.37 us per call and
gelu 1 x 28672 from 10.39 to 1.55 us (median of 9 alternating runs).

## Related Issues

None.

## Pull Request Checklist

### Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

`pre-commit run --all-files` passes on the whole repository at the PR
head.

## Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On the GH200, `pytest tests/utils/test_activation.py` gives 2737 passed
and 0 skipped: the 2700 existing cases plus the 37 new ones. Two earlier
runs of the same file, while other jobs held GPU memory, skipped 1 and 3
cases through the OOM handler in `tests/conftest.py`. I did not run the
rest of the test suite.

The new `test_act_and_mul_small_batch_split` covers the three
activations, fp16 and bf16, and d = 855, 1710, 3420 (vector widths 1, 2
and 4), 4096, 14336 and 28672. It launches 8 x num_SMs rows once, which
uses the unchanged kernel, and checks the result against an fp32 torch
reference. It then launches the first 1, 3, num_SMs - 1, num_SMs,
num_SMs + 1, 2 x num_SMs - 1 and 2 x num_SMs rows on their own and
requires the output to match those rows bitwise. As a check that the
test reaches the new kernel, I offset the split kernel's thread index by
one on purpose, and all 36 cases of this test failed.
`test_act_and_mul_cuda_graph` captures `silu_and_mul` followed by
`gelu_and_mul` on the first output in one CUDA graph, so one split
launch waits on another through PDL, and compares both outputs with
eager results.

A separate check built main and this branch side by side and compared
outputs bitwise on 2400 cases: fp16 and bf16, all three activations, 25
values of d from 1 to 28672 (including odd d and d = 3420, 4100, 8191),
and 1 to 300 tokens across the 131-133 and 263-265 boundaries, with
`enable_pdl` both on and off; all matched, and guard regions around the
output were left untouched. `compute-sanitizer --tool memcheck` over
split and unrolled launches (fp16 and bf16, d = 855 to 28672, 1 to 263
tokens) reported 0 errors.

## Reviewer Notes

- `act_and_mul_kernel<T, Activation, vec_size>` keeps its signature and
its launch contract (one block per row, arguments `(out, input, d)`), so
code that instantiates it directly still compiles and behaves the same.
- PDL: the new kernel has the same `griddepcontrol.wait` /
`launch_dependents` placement as the old one. Every block waits before
its first global load and signals after its last store, so splitting a
row across blocks does not change the ordering.
- The thresholds (2 blocks per SM for the switch; about 2, and up to 4,
blocks per SM for the split) are expressed in terms of the SM count but
were tuned and measured only on this GH200 (132 SMs). I have not
measured them on other GPUs or SM counts.
- The launcher now calls
`cudaDeviceGetAttribute(cudaDevAttrMultiProcessorCount)` on each call.
The eager numbers above include it.
- Empty inputs (`num_tokens == 0` or `d == 0`) still fail with the same
launch error as before.
- Each vector width gets two extra kernel instantiations (`kUnroll` 1
and 2), which adds to the JIT compile time of the three activation
modules.

Developed in combination with Claude Code.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved SiLU, GELU, and tanh-GELU activation-and-multiply operations
for workloads with fewer rows, helping make better use of available GPU
compute resources.
* **New Features**
* Added a benchmark for activation-and-multiply operations, with
configurable workload sizes and options to measure cold or reusable
data.
* **Bug Fixes**
* Added coverage across supported data types and dimensions to verify
activation results remain consistent for different token counts and when
operations are chained.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b2b2bfe](https://github.com/flashinfer-ai/flashinfer/commit/b2b2bfe89219717751e8d1f93d5e6cb6d7fb4bdc)

- **作者**: 0z5a
- **时间**: 2026-10-26T17:54:13Z
- **提交信息**: fix(norm): zero swizzled scale padding and reject strided buffers in FP4 norms (#7008)

## 📌 Description

Two output-buffer problems in the fused RMSNorm + FP4 quantization APIs
(`rmsnorm_fp4quant`, `add_rmsnorm_fp4quant`), found with a
caller-owned-output contract test on B300 (SM103):

**1. The padding of a swizzled scale-factor buffer is never written.**
With `is_sf_swizzled_layout=True` the kernels store the block scales of
real rows and k-blocks only. The 128x4-tile padding (rows past `M` in
the last 128-row tile, and k-blocks past `H // block_size` in the last
4-wide k tile) keeps whatever the buffer held; when the API allocates
the buffer itself that is `torch.empty` content. `fp4_quantize`
zero-fills the same layout
(`csrc/nv_internal/tensorrt_llm/kernels/quantization.cuh`), and the
GEMMs consuming it read those bytes, so the fused norms now produce the
same bytes as `fp4_quantize`.

The kernels now zero the padding themselves, after `griddepcontrol.wait`
and before `griddepcontrol.launch_dependents`, so no extra launch sits
between a PDL producer and the norm:
- each row's threads zero its padded k-blocks (at most 3 bytes per row);
- when the layout is swizzled, the grid covers `ceil(M / 128) * 128`
rows, and the CTAs past `M` only zero their rows of the padding (one
32-bit store per row and k tile). All global reads and writes of the
norm itself were already guarded by `row < M`.

Zeroing every padded row from the CTA that owns row `M - 1` cost +1–2 µs
at `M = 1` on B300 (~57 KB of stores on one SM at H = 7168, even with
coalesced 16-byte stores), so each padded row is zeroed by its own CTA
instead (numbers below).

**2. Strided caller buffers are silently ignored.** A non-contiguous
row-major `block_scale`, `block_scale_unswizzled` or in-place `residual`
went through `.contiguous()` / `.flatten()`, so the kernel wrote a
temporary copy and the caller's buffer kept its old contents, without an
error. These buffers (and `y_fp4`, which TVM-FFI's stride check already
rejected) are now checked with `is_contiguous()` and rejected with a
message, following the existing `y_out` check. The read-only `input`,
`weight` and `global_scale` are unchanged.

## 🔍 Related Issues

None filed; found while writing output-contract tests for the norm APIs
(RFC #3605 norm slice).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff check / ruff format on the changed
files)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New `tests/norm/test_fp4quant_norm_output_buffers.py` (26 cases):
swizzled padding is zero and the scale buffer is identical to the
auto-allocated call under 0xFF and 0x00 poison, at (M, H) = (1, 2048),
(129, 2048), (129, 64), (256, 4096) for both APIs and NVFP4 / MXFP4;
strided `y_fp4` / `block_scale` / `residual` are rejected.

B300 (SM103), CUDA 13.3, torch 2.14.0+cu130, nvidia-cutlass-dsl 4.8.0,
main `0179e5b3`:

| | main | this PR |
|---|---|---|
| `test_fp4quant_norm_output_buffers.py` | 22 failed, 4 passed | 26
passed |
| `test_rmsnorm_fp4_quant_cute_dsl.py` | 1007 passed | 1007 passed |
| `test_add_rmsnorm_fp4_quant_cute_dsl.py` | 1225 passed | 1225 passed |

(The 4 passes on main are the strided `y_fp4` cases, already rejected by
TVM-FFI.)

Kernel time, NVFP4, BF16, CUDA graph of the same call
(`bench_gpu_time(use_cuda_graph=True)`), median µs, two interleaved
rounds each:

| API | M | H | main | this PR |
|---|---:|---:|---:|---:|
| `rmsnorm_fp4quant` | 1 | 4096 | 3.14 / 3.14 | 3.32 / 3.31 |
| `rmsnorm_fp4quant` | 1 | 7168 | 3.56 / 3.54 | 3.55 / 3.54 |
| `rmsnorm_fp4quant` | 127 | 4096 | 3.56 / 3.59 | 3.59 / 3.70 |
| `rmsnorm_fp4quant` | 4096 | 4096 | 12.36 / 12.35 | 12.38 / 12.36 |
| `rmsnorm_fp4quant` | 8192 | 7168 | 46.16 / 46.21 | 46.55 / 46.54 |
| `add_rmsnorm_fp4quant` | 1 | 4096 | 2.93 / 2.92 | 2.92 / 2.92 |
| `add_rmsnorm_fp4quant` | 1 | 7168 | 3.31 / 3.32 | 3.33 / 3.32 |
| `add_rmsnorm_fp4quant` | 127 | 4096 | 3.35 / 3.35 | 3.35 / 3.39 |
| `add_rmsnorm_fp4quant` | 4096 | 4096 | 18.92 / 18.91 | 18.91 / 18.92 |
| `add_rmsnorm_fp4quant` | 8192 | 7168 | 71.86 / 71.78 | 71.84 / 71.84 |

Row-major scale outputs (`is_sf_swizzled_layout=False`, grid unchanged)
stay within ±0.1 µs at every shape above. The broader output-contract
file that found both problems (caller-owned outputs, poison, strided
buffers, PDL ordering; 102 cases, not part of this PR) goes from 18
failed / 84 passed on main to 102 passed.

## Reviewer Notes

- The grid grows only for the swizzled layout and only up to the next
multiple of 128 rows; the row-major path is unchanged.
- `zero_swizzled_sf_padding` lives in `fp4_common.py` and is shared by
both kernels; the add kernel also calls it for `output_both_sf_layouts`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Swizzled scale-buffer padding is now initialized consistently,
including rows added to align processing, improving output reliability
for RMSNorm and add-RMSNorm FP4 quantization.
* **Input Validation**
* Caller-provided output and residual buffers must be contiguous.
Non-contiguous buffers are rejected with an error rather than being
processed.
* **Tests**
* Added coverage for swizzled scale-buffer padding and validation of
non-contiguous buffers across supported FP4 quantization modes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: 0z5a <0z5a@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [90ac2ee](https://github.com/flashinfer-ai/flashinfer/commit/90ac2eeb7e0c9e8670034389382082fa1dac4a3e)

- **作者**: Yang Xu
- **时间**: 2026-10-26T17:48:54Z
- **提交信息**: perf: stage full rectangular cuDNN page tables with one copy (#7050)

<!-- .github/pull_request_template.md -->

## 📌 Description

When every request fills one complete row of the paged KV block table,
`plan()` still clears the table and creates per-row tensor views for
staging. Detect that exact rectangle and copy the flat indices into the
existing table in one operation. This preserves the table address
retained by older CUDA Graphs. Nonzero input offsets and strided
input/output storage remain supported; larger retained capacities and
unequal row lengths use the existing tail-clearing path.

**#6231 has merged; this PR now targets main.** The review diff is two
files: one small plan-time fast path and expanded cases in the existing
regression file. No dispatch rule or public API changes.

### Performance

Current-source H100 NVL / SM90 host-component measurement: baseline
`03092ec2b953`, candidate `d9cbd60e26c7`; cuDNN 9.27.0.42, development
FE `cfcb846a295f` with its matching native extension, CuTeDSL 4.8, Torch
2.14.0+cu130 and CUDA toolkit 13.2. BF16, HND, D128, Hq/Hkv=16/4, Q128,
KV8192, page16, uniform page counts, pinned CPU planning metadata.
Explicit cuDNN selected the same backend plan in all four processes.

Four independent processes in baseline/candidate/candidate/baseline
order; 100 samples per case/process after warmup. Values below pool the
two processes per version. Synchronization is outside the host
submission measurements. `plan + run` means host submission, not
completed GPU execution or serving throughput.

| Batch | Warm plan before / after (us) | Plan + run submission before /
after (us) |
|---:|---:|---:|
| 1 | 165.41 / 153.32 | 228.17 / 215.72 |
| 2 | 173.14 / 153.37 | 235.56 / 216.21 |
| 16 | 220.07 / 159.48 | 286.02 / 224.40 |
| 64 | 374.83 / 178.17 | 445.52 / 247.78 |

Unchanged FA2 plan controls vary from -0.71% to +0.50%. cuDNN warm run
submission changes by -0.37 to +0.18 us; GPU replay changes by -0.008%
to +0.22%, with the same execution path. This optimization targets
plan-time staging for rectangles; it does not claim a main-kernel or
end-to-end serving speedup.

Reproduce on the baseline and candidate checkouts, with the same
runtime:

```bash
for b in 1 2 16 64; do
  python benchmarks/bench_cudnn_wrapper_host.py --kind paged --batch "$b" \
    --q 128 --kv 8192 --qo-heads 16 --kv-heads 4 --layout HND \
    --backends fa2 cudnn --replan --output "table-copy-b${b}.json"
done
```


## 🔍 Related Issues

Builds on merged #6231, which supplies reusable page-table capacity and
the retained-capture contract.

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

Scoped `pre-commit run --files flashinfer/prefill.py
tests/attention/test_cudnn_wrapper_regressions.py` passed. The all-files
checkbox is intentionally not claimed.

## 🧪 Tests

Post-merge integration (`f84cf1706588`): current main was merged without
rewriting branch history. The staging helper is AST-identical to the
reviewed head; all other production AST matches current main. The
existing staging test passed 20 CPU-adapted configurations, plus 64
guarded parent/candidate comparisons including transposed, broadcast and
strided storage. These CPU checks do not replace GPU capture validation.
Scoped hooks passed; fresh focused GPU CI is requested for this
integration head. Earlier GPU/performance results below retain their
stated source scope.

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).


H100 qualification on the final production source: 72 focused cases
passed, followed by 24 expanded capture/replan cases. Twelve capture
cases overlap the first run, giving 84 distinct configurations. No new
test file was added. Coverage includes CPU/GPU and strided indices,
nonzero offsets, exact and oversized output capacities, untouched guard
columns, FP16/BF16 O/LSE, retained captures with changed mappings,
external tables, and no-readback planning.

The host benchmark completed all 32 case/provider/process runs. Each
checked sampled independent math, cuDNN output against FA2, and
poisoned/timed CUDA Graph replay within one output ULP. Shutdown emitted
the previously observed nanobind reference-leak diagnostics; all
processes exited zero, and this change does not attribute or fix those
diagnostics. Upstream CI is requested separately.

```bash
pytest -q tests/attention/test_cudnn_wrapper_regressions.py \
  -k 'page_table_staging_capacity_and_strided_indices or paged_capture_replan_changes_indices_and_lengths or paged_prefill_plan_stages_device_lengths_without_sync or paged_prefill_default_scale_layout_lse'
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

Please focus on the exact-full-table predicate: the fast path must
overwrite every destination cell while keeping its pointer and strides.
Oversized retained capacity must continue clearing unused rows/columns.
Tests check data and capture behavior, without timing thresholds, a
required helper-call count or a heuristic winner.

This PR is Ready for review against main. The current head merges main
after #6231; its diff remains exactly the original two-file staging/test
increment.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved handling of batches with equal page counts, reducing overhead
when preparing page tables.
* **Tests**
* Expanded validation for page-table layouts, starting offsets, and
updated metadata during replanning. Checks also confirm that values
outside the logical table remain unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a81c6a0](https://github.com/flashinfer-ai/flashinfer/commit/a81c6a0f7c6b11e7c839e7abeedd0aa3277e0b24)

- **作者**: kangbintNV
- **时间**: 2026-10-26T17:46:48Z
- **提交信息**: docs: resolve blocking and P1 documentation findings (#6505)

<!-- .github/pull_request_template.md -->

## 📌 Description

Resolve the five blocking findings and prioritized documentation-review
findings from the 2026-10-26 report for
`flashinfer_v0.7.2.post1_vs_main_aa3d76f9b`.

Blocking fixes:

- Add `cake_causal_conv1d_kcp` to the API autosummary.
- Add complete parameter documentation to `fp8_rowwise_gemm_allreduce`
and `prepare_fp8_rowwise_gemm_allreduce`.
- Document `FLASHINFER_DISABLE_TINYGEMM2_TCGEN05` and
`FLASHINFER_MEGAMOE_SPIN_DEBUG` in `CLAUDE.md`.

P1 and follow-up review fixes:

- Give `BatchAttentionWithAttentionSinkWrapper.__init__` an explicit
parameter table matching its real signature instead of inheriting
parent-only parameters.
- Correct the `fused_add_rmsnorm_quant` formula to write to `out` and
divide by `scale` before FP8 conversion.
- Clarify that `msa_proxy_score` supports SM90/SM120/SM121, while
`msa_proxy_score_fp4` remains SM120/SM121-only. Preserve the original
`docs/api/sparse.rst` lines 51–52 exactly.
- Document XQA KV-cache dtype as coming from `k_cache.dtype`.
- Move the long `QkvNormRopeExchangeOverlap` explanation into a proper
NumPy `Notes` section so it is not parsed as bogus parameters.
- Fix RST list spacing/indentation in `concat_mla_k` and both
green-context API docstrings.
- Explain that package metadata can accept CuTe DSL 4.6.2 even though
the cuDNN FROST runtime check currently requires 4.7.0 or newer.
- Repair the repeated RoPE segment sentence. Current `rope.py` contains
eight affected public APIs: four `indptr` variants now use the corrected
segment template, and four `pos_ids` variants now describe their actual
`pos_ids` argument instead of nonexistent `indptr` input.

This is a documentation-only change; runtime behavior is unchanged.

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

- Targeted `pre-commit run --files ...` for all changed files — passed.
- `python3 scripts/check_pr_document.py --base origin/main --head HEAD
--strict` — passed, 0 new findings.
- Repository docstring-parser validation — sink-wrapper parameters
exactly match all 17 signature parameters; QKV overlap exposes only its
11 real parameters and a separate `Notes` section.
- Source-level format assertions — all RoPE templates use their real
`indptr`/`pos_ids` inputs; each repaired RST list has the required
blank-line structure; original `docs/api/sparse.rst` lines 51–52 match
`origin/main` exactly.
- `git diff --check origin/main...HEAD` — passed.
- Sphinx was not run locally because it is unavailable in this
environment; GitHub Actions runs Build Docs.
- GPU tests were not run because runtime code is unchanged.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends".
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

The report was generated from `main` at `aa3d76f9b`. The PR is rebased
onto newer `main` at `364b53a4b`; the newer base independently contains
three findings not present in the linked report (`sampling_softmax`,
`FLASHINFER_CAKE_STEPFUN_FULL_PATH`, and
`FLASHINFER_TRTLLM_MOE_OVERLAP_RESERVED_SMS`). They are outside this
PR's report scope and remain base findings, so the PR-level strict
checker reports 0 new findings.

The report grouped the repeated RoPE wording as six findings, while the
current source contains eight copies of the same root problem. All eight
are fixed so the identical defect is not left in the two remaining
generated pages.

The existing MegaMoE template defines `DG_SPIN_DEBUG_TAGS`, while the
kernel checks `FI_MEGAMOE_SPIN_DEBUG_TAGS`. The
`FLASHINFER_MEGAMOE_SPIN_DEBUG` row documents the current
Python-to-template behavior without claiming that the kernel debug path
is active.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Summary by CodeRabbit

* **Documentation**
* Documented the `FLASHINFER_MEGAMOE_SPIN_DEBUG` and
`FLASHINFER_DISABLE_TINYGEMM2_TCGEN05` environment variables.
* Added `cake_causal_conv1d_kcp` to the Mamba API reference and expanded
FP8 rowwise GEMM all-reduce parameter and return-value details.
* Clarified supported hardware for MSA operations, including
`msa_proxy_score` support on SM90 and `msa_proxy_score_fp4` limits.
* Added batch attention constructor details and clarified RoPE position
and segment mapping.
* Corrected descriptions of quantized RMS normalization outputs and
XQA’s KV cache dtype.
* Clarified cuDNN decode’s FROST runtime requirement and fallback
behavior.
* Added notes to the QKV normalization, RoPE, and exchange
documentation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [063604b](https://github.com/flashinfer-ai/flashinfer/commit/063604bfc14fab81dd90b110cda0e97b97acbd9c)

- **作者**: Yang Xu
- **时间**: 2026-10-26T17:42:21Z
- **提交信息**: fix(moe): preserve FP16 NVFP4 subnormal scales on SM120 (#7433)

<!-- .github/pull_request_template.md -->

## 📌 Description

SM120 FP16 W4A16 preparation currently clears valid NVFP4 E4M3 subnormal
block scales: after multiplying by 128, it clamps every value below 2 to
zero. This silently changes checkpoint weights for scales below 1/64.

Forward the activation dtype into packed-scale preparation and preserve
these values for FP16, whose existing packed decoder represents them
exactly. Add an exhaustive finite nonnegative E4M3 encoding regression
and subnormal-scale coverage for direct/packed routes and live
CUDA-graph replay.

## 🔍 Related Issues

Found while validating the native SM120 W4A16 backend as a
correctness-checked comparison for low-latency MoE work.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped `pre-commit run --files` passed for both changed files. The
all-files item is intentionally unchecked.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted physical SM120 validation: **139 passed, 0 skipped** across the
four files below. The new subnormal GPU regression fails its existing
numerical assertion with the original preparation code and passes with
this fix.

```bash
pytest -q tests/moe/test_b12x_w4a16_fp16_direct.py \
  tests/moe/test_b12x_w4a16_bf16_tc_decode.py \
  tests/moe/test_b12x_w4a16_scratch.py \
  tests/moe/test_b12x_w4a16_route_pack.py
```

The encoding test covers all 127 finite nonnegative E4M3 values,
including all seven subnormals. GPU cases cover FP16 T=7/8, gated SiLU
and ReLU2, two shapes, direct and packed routing, and changed live
inputs under graph replay. Reference arithmetic and tolerances are
unchanged.

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

This changes host weight preparation only; the device decoder and GPU
kernel arithmetic are unchanged. The existing BF16 packing policy is
retained. The private helper keeps its BF16 default for existing
callers.

The separately maintained experimental b12x preparation copy is outside
this bounded fix and needs a corresponding independently tested
follow-up. This PR makes no performance claim.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* FP16 execution now preserves packed scale values below the previous
cutoff, including subnormal values. This improves handling of small
scales across supported direct-route workloads while retaining existing
behavior for other activation types.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9954bfb](https://github.com/flashinfer-ai/flashinfer/commit/9954bfb09acdb4882baa98d6a7e41b617c88f166)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-26T17:36:04Z
- **提交信息**: ci: route GPU test lane JIT compiles through sccache (#6810)

<!-- .github/pull_request_template.md -->

## 📌 Description

The PR GPU test lanes (H100, A10G parts 1–5, T4) JIT-compile every
module from scratch on every run: no sccache, no precompiled kernels
(`JIT_ARCH` is unset, and the H100 log reports `Not compiled: 681`). The
AOT lanes already use sccache, and recent PR runs hit about 100% (15,926
nvcc and 530 C++ compiles per lane). Their stats put a cached nvcc call
at about 6 s and an uncached one at about 44 s.

This PR runs each GPU lane's test script through a new wrapper,
`scripts/run_with_test_sccache.sh`:

- It reuses `setup_sccache` / `collect_sccache_stats` from
`scripts/jit_cache_build_common.sh`, with the same S3 bucket and the
same `cuda<ver>-<arch>` prefix as the AOT lanes. Read-write when the
SCCACHE AWS secrets are available, anonymous read-only otherwise (for
example, fork PRs).
- It adds the JIT workspace cache dir (`$FLASHINFER_WORKSPACE_BASE` or
`$HOME`, plus `/.cache/flashinfer`) to `SCCACHE_BASEDIRS`, so cache keys
don't depend on the container's HOME.
- **It fails open.** The lane runs uncached instead of failing if the
sccache download or checksum fails, if `nvcc` is missing or its version
can't be read, or if the sccache server (and its S3 check) fails to
start. Cache read and write errors already fall back to local
compilation inside sccache.
- It passes the lane's exit code through unchanged and writes stats to
`sccache-stats/`. Those are uploaded as
`sccache-stats-<kind>-<cuda>-<job-index>`. AOT artifact names are
unchanged.

**Toggle:** on by default. Setting the repository variable
`FLASHINFER_GPU_TEST_SCCACHE=0` turns it off with no code change, for
A/B timing or as a kill switch.

Smaller changes:
- `setup_sccache` skips the download when `sccache --version` already
matches the pinned `SCCACHE_VERSION`. The CI image's `ci` stage does not
include sccache; only the devcontainer `dev` stage does. So CI lanes
still download it, which took about 1 s in the AOT logs.
- The three sccache stats steps in `pr-test.yml` move after both Run
Test steps. They now run for AOT lanes, or for GPU lanes when the toggle
is on.
- `CLAUDE.md` documents the wrapper, the toggle, and the caveats below.

### Results on this PR

All numbers below come from scoped runs of
`tests/attention/test_batch_decode_kernels.py
tests/attention/test_sliding_window.py` (2,924 tests), using the lane
setup PRs actually get today. Since #6953, a scoped A10G run uses the
same part scripts as a full run, with 8 parallel compiles.

**A10G** (pytest-reported test time; same test counts in every run; the
Docker pull is excluded):

| Lane | Tests | Uncached | Warm cache (run 1 / run 2) | Change |
sccache hit rate |
|---|---|---|---|---|---|
| Targeted Unittest 1 (A10G) | 2,233 passed, 52 skipped | 39m16s | 8m24s
/ 8m28s | −79% (4.7×) | 100% / 100% (321 compiles) |
| Targeted Unittest 2 (A10G) | 639 passed | 17m31s | 5m26s / 5m28s |
−69% (3.2×) | 100% / 100% (306 compiles) |

**H100** (test phase, first `PYTEST START` to `TEST SUMMARY`; 8
workers):

| Lane | Uncached | Warm cache (run 1 / run 2) | Change | sccache hit
rate |
|---|---|---|---|---|
| Targeted Unittest (H100) | 16m36s | 10m20s / 7m09s | −38% to −57% |
99.86% / 100% (731 compiles) |

Runs:
- **A10G uncached:** run 39637956508 from #6953. It used the same part
scripts but had no sccache.
- **H100 uncached:** run 39512581548 on this PR, with
`FLASHINFER_GPU_TEST_SCCACHE=0`.
- **Warm:** runs 39654229541 and 39667178704.

The H100 runs on a shared node, so its times vary more between runs than
A10G's.

**Why an earlier warm run hit only 37%.** A `pull_request` run tests the
PR merged with the current `main`, not the PR branch alone. Hit rates on
the H100 lane across five runs of this scope went 26.9% (first run with
sccache) → 37.2% → 99.86% → 100%:
- Between the first two sccache runs, `main` advanced 33 commits. One
added 20 lines to `include/flashinfer/page.cuh`, which the decode and
prefill kernels include, so their cache keys correctly changed. Those
were real misses, not unstable keys.
- Between the next pair of runs, `main` advanced 7 commits that touched
none of these headers, and the hit rate went to 99.86%.

To rule out unstable cache keys, a temporary diagnostics commit
(71c075078, reverted in 41abb1892) archived the H100 lane's JIT
workspace and a per-file sccache log on two runs. The generated sources
(350 modules) and all 91 `build.ninja` files were byte-identical between
the runs.

**What to expect in practice:**
- A lane re-run on a PR, or two PRs that don't touch shared kernel
headers, should see near-100% hits and the times above.
- A change to a widely included header (e.g. `page.cuh`) on `main` or in
the PR invalidates every module that includes it, so the first run after
it pays full compile cost and writes new entries. That is correct
behavior.
- Cold runs cost a little: 0.05–0.1 s per cache write, with no write
errors observed.

**Superseded measurements.** Earlier in this PR, scoped A10G runs
compiled one file at a time (`MAX_JOBS=1`) because of a 12 GB-per-nvcc
memory budget. #6953 fixed that, so those A10G timings no longer
describe any real pipeline and are omitted. The first small-scope runs
(about 90 compiles) are also omitted in favor of the larger scope.

### Full-suite results

Two unscoped runs (`@flashinfer-bot run`) on this PR, compared with the
uncached baseline:
- **Run 1:** 39684501125, the first full run with sccache. A10G parts 1
and 2 were already partly warm from the scoped runs above.
- **Warm:** 39718757787.
- **Baseline:** medians over the 15 most recent full-suite PR runs (Oct
20–21) that ran without sccache, counting only lanes that passed (12 for
H100).

Times are the lane's `Run Test` step, which includes the Docker pull and
setup but not the wait for a runner.

| Lane | Uncached median (range) | Run 1 | Warm | Warm vs uncached |
Warm hit rate (nvcc compiles) |
|---|---|---|---|---|---|
| JIT Unittest (H100) | 111.2 min (100.4–117.5) | 92.4 min (27.3% hits)
| **62.2 min** | −44% | 99.98% (8,291) |
| JIT Unittest 1 (A10G) | 47.1 min (43.0–53.1) | 15.7 min | **17.5 min**
| −63% | 100% (400) |
| JIT Unittest 2 (A10G) | 44.2 min (22.5–45.2) | 23.6 min | **17.8 min**
| −60% | 100% (582) |
| JIT Unittest 3 (A10G) | 58.0 min (27.4–60.3) | 48.7 min | **19.2 min**
| −67% | 100% (547) |
| JIT Unittest 4 (A10G) | 51.0 min (29.9–52.1) | 46.8 min | **9.7 min**
| −81% | 100% (209) |
| JIT Unittest 5 (A10G) | 37.4 min (35.9–47.3) | 37.5 min | **12.3 min**
| −67% | 100% (159) |
| JIT Unittest (T4) | 21.3 min (15.5–21.6) | 21.6 min | **17.0 min** |
−20% | 100% (7) |

- **A10G:** 237.7 lane-minutes per full run drop to 76.5 (−68%). The
slowest A10G part drops from 58.0 to 19.2 minutes.
- **T4:** this lane compiles almost nothing (7 compiles), so it gains
little.
- **H100:** as the slowest lane, it sets a full run's GPU wall time,
which drops from about 111 to about 62 minutes once warm. Run 1, with
27% hits, still saved 17%.
- **Expected range:** most real runs will fall between run 1 and the
warm run, depending on how much of the kernel headers `main` changed
since the cache was last filled.
- **Unrelated failure:** in both runs all 165,646 H100 tests ran, and
exactly one failed.
`tests/msa_ops/test_msa_nvfp4_decode_sm100.py::test_out_on_a_route_that_cannot_honour_it_raises_instead_of_copying`
gets `ValueError: device must be a cuda device`, because
`msa_sparse_decode_attention` calls `is_sm90a_supported()` on a CPU
tensor before the `out=` check. That fail-fast also cancelled two arm64
AOT lanes in the warm run.

### H100 capacity

The H100 pool is two 8-GPU machines, each split into two 4-GPU runners
(`flashinfer-h100-4gpu-a` and `-b`), so 4 runners. Over 53 hours (Oct
19–21), they ran 303 H100 jobs (full and scoped), totalling 142
runner-hours: about 64 runner-hours per day, or 68% of the pool.

I replayed those 303 jobs at their observed start times, first-in
first-out, onto 2–4 runners. "Warm" scales full-suite H100 jobs by 0.56
(the measured 62.2 / 111.2) and scoped H100 jobs by 0.5 (scoped H100
went from 16.6 to 7–10 minutes above). Waits are queue time before a job
starts.

| Scenario | Runners | Utilization | Mean wait | p90 wait | Max wait |
|---|---|---|---|---|---|
| Today (uncached) | 4 | 68% | 22.7 min | 98.7 min | 143 min |
| Warm cache | 4 | 37% | 0.6 min | 0 min | 20 min |
| Warm cache | 3 | 49% | 4.7 min | 19.1 min | 61 min |
| Warm cache | 2 | 74% | 44.5 min | 148.8 min | 183 min |
| Warm cache, no `main`-push H100 runs | 3 | 37% | 2.2 min | 4.0 min |
39 min |
| Warm cache, no `main`-push H100 runs | 2 | 55% | 23.2 min | 93.4 min |
136 min |

**`main`-push runs are a large share of H100 time.** 50 of the 303 H100
jobs came from `main` push runs, and none succeeded: 47 were cancelled
by the next push and 3 failed. They used 35.8 runner-hours, 25% of the
pool's H100 time.

What this supports:
- **With sccache alone,** 3 runners would give shorter queues than
today's 4 (mean 4.7 vs 22.7 min). Runners come in pairs per machine,
though, so that frees capacity without retiring hardware.
- **Dropping to one machine (2 runners)** gives queues about like
today's (mean 23 vs 23 min, p90 93 vs 99 min) only if `main` pushes also
stop running the H100 lane. A cold cache after a widely included header
changes would push those numbers up.
- **Cost in dollars isn't computed here.** I couldn't confirm the
instance type from the job logs. At your hourly rate, the saving is
about 30–50% of the H100 runner-hours above, or one 8-GPU machine if
both changes land.

**Limits of the model:**
- The observed start times already include today's queueing, so today's
waits are understated.
- Cancellations are replayed as observed, not re-simulated.
- It assumes warm-cache hit rates for every run.

### Post-merge verification

The results above were measured on this PR. After merge, confirm them on
real traffic.

- **Use full-suite PR runs, not `main` push runs.** Most `main` push
runs are cancelled by the next push: 57 of the last 60. The uncached
baseline is already recorded above (medians of 15 full-suite PR runs).
- **Expect a fill-up period.** The first full-suite runs after merge
fill the cache, and so does the first run after any widely included
kernel header changes. Hit rates and times should land between the run-1
and warm columns above.
- **Track, per lane, from the `sccache-stats-*` artifacts and job
logs:** `Run Test` time, `Cache hits rate`, `Compile requests`, and any
cache read/write errors or timeouts.
- **A/B check:** set the repository variable
`FLASHINFER_GPU_TEST_SCCACHE=0` for a run or two if a regression needs
ruling out, then delete the variable. Only `pr-test.yml` from this PR
onward reads it.
- **Success criteria:**
- median H100 and A10G `Run Test` times clearly below the uncached
medians above;
  - no failures attributable to sccache;
  - warm runs hitting above 90%.
- **Stop conditions:** set the variable to `0` if any of these appear:
  - higher flake or timeout rates;
  - per-unit timeout kills leaving compiles orphaned;
  - S3 errors that slow lanes down.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. *(I ran pre-commit on the changed files
only; it passed.)*

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Shell-level tests in `tests/jit/test_jit_cache_providers.py` use fake
`sccache`, `nvcc`, `curl`, `tar` and `uname` binaries:
- **Enabled path:** launchers are set, the prefix is `cuda129-x86_64`,
`SCCACHE_BASEDIRS` holds both the source root and the JIT cache root,
arguments and the exit code pass through, and the stats file is written.
- **Fail-open paths:** a failed download, a checksum mismatch (asserting
`tar` never runs, so an unverified binary is never extracted), a missing
`nvcc`, and a failed server start each still run the lane, with no
launchers set. Each of these fails against the wrapper as first written.
- **Isolation:** the shell tests strip the enclosing lane's `SCCACHE_*`,
`AWS_*` and launcher variables. The existing
`test_sccache_setup_uses_server_side_compilation` now asserts that it
leaves a simulated lane stats directory untouched; before, it overwrote
the H100 lane's `sccache-metadata.txt`.

All six passed under pytest on the H100 lane in run 39501132697, a
scoped run that included `tests/jit/test_jit_cache_providers.py`. The
test file hasn't changed since. They were also run locally through a
standalone harness, with the wrapped lane's environment simulated.

Workflow checks: shellcheck on the wrapper is clean. `actionlint` gives
the same findings before and after this change; all of them are
pre-existing SC2086/SC2046/SC2129 notes in unrelated steps.

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

- **Process ownership (please weigh in).** sccache runs in server-side
mode, the same as the AOT/provider builds. As a result:
- Compiles run as children of the sccache server, not of the pytest
worker. A unit-timeout `killpg` won't stop in-flight compiles; the
container's `docker run --rm` is the final cleanup.
- Per-unit host-memory telemetry no longer includes nvcc RSS. That
matters for the measured peaks behind the `host_memory_heavy` /
`node_exclusive` markers. Ninja's `-j` budget still limits how many
compiles run at once.
- If either matters, client-side mode (`SCCACHE_CLIENT_SIDE=1`) would
keep compiles in the worker's process tree. It is untested here and was
measured slower for provider builds.
- **Credentials.** The SCCACHE AWS secrets now also reach the GPU test
containers. That's the same exposure as the AOT lanes, which already run
PR code with them. They are forwarded to `ci/bash.sh` by name, so their
values are never echoed.
- **Cache sharing.** GPU lanes share the AOT lanes' S3 prefix. Hits are
content-keyed, but AOT provider builds and JIT builds use different
generated-source paths and flags, so I don't expect cross-hits between
them. The main gain is GPU runs reusing earlier GPU runs.
- **Follow-up idea.** The H100 nodes are long-lived, so a per-runner
local disk cache in front of S3 could cut S3 latency further. Each
runner must have its own directory, because sccache's local cache
supports only one server. That is not part of this PR.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional shared caching for GPU test runs, enabled by default
except for AOT jobs.
* Added cache statistics, metadata, and diagnostics for enabled test
lanes.
  * Added local support for running tests with the shared cache wrapper.
  * Added an option to disable GPU test caching when needed.

* **Bug Fixes**
* GPU tests now fall back to uncached execution when cache setup or CUDA
detection fails.
  * Compatible cache installations are reused when available.

* **Tests**
* Added coverage for cache setup, integrity checks, statistics
collection, and fallback behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f825b05](https://github.com/flashinfer-ai/flashinfer/commit/f825b05ff0b4c7419deeb0d151453351d9875dba)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-26T17:35:00Z
- **提交信息**: ci: replace per-merge PR Test runs on main with a scheduled full suite (#6968)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replaces the per-merge PR Test runs on `main` with a scheduled
full-suite run.

**Why.** Every push to `main` triggered PR Test. All of these runs
shared one `cancel-in-progress` concurrency group, so each merge
cancelled the run before it. From 2026-09-23 to 10-21 there were 852
main runs:
- 769 (90%) were cancelled, 61 passed and 21 failed, so about 3 runs a
day finished.
- 111 of the cancelled runs had been going for over an hour.
- Cancelled runs alone used about 2,950 runner-hours: about 1,430 AOT,
1,060 A10G, 300 H100 and 160 T4.

The runs that did finish caught real breakage on main that PR CI missed,
and nobody was notified:
- `tests/moe_ep/test_sm107_torch_staging.py` failed on A10G (Oct 14–15)
- `tests/msa_ops/test_msa_nvfp4_decode_sm100.py` failed on H100 (Oct
20–21)
- `test_cute_dsl_bf16_gather_grouped_gemm` failed on H100 (Sep 26–28)
- an AOT cu130 build failed

**Changes** (`.github/workflows/pr-test.yml`):
- Removes `push: branches: [main]` and adds `schedule: '17 4,12,20 * *
*'`. These times stay clear of the 00:00 UTC nightly-release.
- Scheduled runs get their own concurrency group without
cancel-in-progress. A run that is still going delays the next one
instead of being cancelled.
- `fail-fast` is off for scheduled runs, so every broken lane reports.
PRs keep fail-fast.
- A new `report-main-status` job (`issues: write`) opens or comments on
the issue "Scheduled PR Test is failing on main" when a scheduled run
fails, and closes it on the next green run. It ignores a late re-run of
an older scheduled run if a newer one has already finished, and the cron
is at minute 17 because GitHub may delay or drop top-of-hour schedules.
- AOT lanes keep warming the sccache S3 cache three times a day.

**Expected cost.** A full run is about 11.8 runner-hours, so three a day
comes to about 1,000 runner-hours per 4 weeks. Today it is about 3,840
(−74%). H100 use drops from about 450 h to about 160 h.

## 🔍 Related Issues

Follow-up to the CI cost work in #6810.

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

- [ ] Tests have been added or updated as needed. (Workflow-only change;
no tests apply.)
- [x] All tests are passing (`unittest`, etc.). PR CI ran with
`@flashinfer-bot run tests/utils/test_activation.py` (run 39719172478):
all 6 AOT Build Import lanes and Targeted Unittest (H100) passed. That
only confirms the PR path still works; it does not exercise the
scheduled path.

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

- The scheduled run and the issue job have not run yet. `schedule` only
fires from the default branch, so this can only be verified after merge,
or with a `workflow_dispatch` run (which has no issue reporting).
- `workflow_dispatch` still runs the full suite on demand.
- Possible follow-ups: skip a scheduled run when `main` HEAD hasn't
changed since the last one; Slack notification (needs a webhook secret).
- actionlint: no new findings relative to main.

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Automated test runs now run three times daily at 04:17, 12:17, and
20:17 UTC; pull request-triggered runs remain available.
* Scheduled runs operate independently, and older runs are ignored when
a newer scheduled run has completed.
* Failed scheduled runs are tracked in a single issue, updated while
failures persist and closed after a successful run.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [392ae13](https://github.com/flashinfer-ai/flashinfer/commit/392ae13fc33077e1ed4f29401949fdfc79bf1dfc)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-26T17:34:06Z
- **提交信息**: ci: build JIT-cache wheels without a PEP 517 isolated environment (#6896)

<!-- .github/pull_request_template.md -->

## 📌 Description

Nightly and release JIT-cache provider builds (42 shards: 3 CUDA
versions × 2 CPU archs × 7 SM archs) missed sccache for about 30% of
their compiles every night, even when the sources hadn't changed. They
also installed torch twice per shard. This PR fixes two independent
causes of the misses.

**1. A random include path from the PEP 517 isolated build
environment.** `scripts/build_jit_cache_wheel.py` built each wheel in
`build.env.DefaultIsolatedEnv`, which:
- installed torch a second time (about 1.7 min, after the ~2.1 min
install into the container interpreter);
- lived at a random `/tmp/build-env-XXXX` path. That path reached every
nvcc command as `-isystem .../tvm_ffi/include` and the line markers of
every translation unit that includes tvm_ffi headers (via
`csrc/tvm_ffi_utils.h`: all bindings and launchers, about 1,600 of about
3,500 on the larger shards). Those files got new sccache keys on every
run.

The wheel is now built in the container's interpreter, which is already
torch-pinned and discarded after each shard. The backend's build
requirements are installed there through the existing pip retry logic,
under the existing `PIP_CONSTRAINT` torch pin, and the build runs with
`ProjectBuilder` in `sys.executable`.

**2. Header timestamps changing GCC's `#pragma once` decisions.** GCC's
`#pragma once` treats two files as the same when their size, contents
and mtime (whole seconds) match. torch ships byte-identical `#pragma
once` headers at several paths (the empty `ATen/ops/*_native.h` stubs
pulled in through `<ATen/ATen.h>`), and pip stamps each file with its
install time. Which duplicate GCC keeps therefore depended on pip's
timing, so files that include torch preprocessed differently from build
to build. With CUDA 12.8+, cudafe++ also gets a random module ID per
run, so a cudafe++ miss cascades into cicc and ptxas misses: whole
recompiles of 5–18 minutes for files like
`csrc/trtllm_batched_gemm_runner.cu` and the generated `flash_kda`
bindings.

Before compiling, `build_jit_cache_wheel.py` now sets every installed
header under the interpreter's site-packages to one fixed mtime
(1980-01-01, the earliest ZIP timestamp). Python sources are left alone.
GCC then keeps exactly one copy of each duplicate, whatever the install
timing.

Comments in `jit_cache_build_common.sh` and
`build_flashinfer_jit_cache_whl.sh`, and the release-build paragraph in
`CLAUDE.md`, are updated to match.

### Results

The baseline is nightly run
[39370143519](https://github.com/flashinfer-ai/flashinfer/actions/runs/39370143519)
(2026-10-20). The comparison is this PR's latest `release.yml` run
([39527758815](https://github.com/flashinfer-ai/flashinfer/actions/runs/39527758815)),
which builds all 42 providers without publishing. Numbers come from each
shard's `jit-cache-diagnostics-*` artifact (sccache stats and ninja log)
and the job timings.

| All 42 provider shards | Oct 20 nightly | This PR |
|---|---|---|
| Median / slowest shard | 27.8 / 40.1 min | 14.7 / 21.2 min |
| Total provider runner time | 18.5 h | 10.8 h |
| sccache hit rate, median (lowest) | 71.3% (69.6%) | 100.0% (99.2%) |
| cicc / ptxas misses per shard, median | 813 / 168 | 0 / 0 |
| Compile CPU-hours, all shards | 514 | 176 |

| Two representative shards | Oct 20 nightly | This PR |
|---|---|---|
| cu129 x86_64 sm100a: ninja wall time | 17.9 min | 8.7 min |
| cu129 aarch64 sm103a: ninja wall time | 27.1 min | 8.1 min |
| `trtllm_batched_gemm_runner.cu` compile (aarch64 sm103a) | 17.6 min |
0.1 min |
| Setup from "Building wheel" to first ninja line (4 cu129 shards) |
2.3–4.3 min | 0.7–2.2 min |

How to read these:
- **Best case, not a typical night.** This run's kernel sources were
identical to the previous run on this PR, so the hit rate is an upper
bound. A real nightly will still miss on files changed that day, roughly
the 160–220 per shard that ptxas also missed before. What's gone is the
systematic part: front-end misses on files whose device code hadn't
changed, 211–1,218 per shard (median 645, about 29,000 a night across
all 42).
- **The two causes were measured separately.** With only the first fix,
a rebuild of the same commit hit 100% on x86_64 sm100a and 99.0% on
aarch64 sm103a. The remaining 35 sm103a misses were exactly the
torch-including files the second fix addresses. Per-step numbers are in
[this
comment](https://github.com/flashinfer-ai/flashinfer/pull/6896#issuecomment-6305403020).
- **Job wall time also depends on the runner.** A runner that already
has the `pytorch/manylinux` image skips a ~5 min pull. Ninja time and
compile CPU-hours are the clean comparisons.

## 🔍 Related Issues

None. Found while measuring nightly wheel-build time.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. *(I ran pre-commit on the changed files;
it passed.)*

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/test_build_jit_cache_wheel.py`: the three existing retry tests
are unchanged, and five new tests cover the change:
- installing into a stand-in interpreter, including a retry after an
interrupted pip run;
- skipping an empty requirement set;
- `build_wheel()` building in `sys.executable` with no isolated
environment;
- `pin_header_mtimes` touching only headers (never Python sources or
symlinks);
- GCC preprocessing a `#pragma once` duplicate identically once mtimes
are pinned.

The scoped H100 run on the final commit passed. I also built the shim
wheel locally with the old and new drivers: same wheel name and file
list, and byte-identical contents including METADATA and RECORD.
Provider wheels need CUDA; this PR's `release.yml` runs built all 42
successfully on both commits.

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

- **The build requirements now go into the container's interpreter.**
That covers the `[build-system]` requires (setuptools, wheel, ninja,
numpy, apache-tvm-ffi, …) and the backend's
`get_requires_for_build_wheel` extras, such as nvidia-cutlass-dsl. The
provider build already installed torch there. The container is discarded
after each shard, and `pip install --force-reinstall --no-deps
dist/*.whl` already ran in that interpreter.
- **The header mtime pin only affects the build container.** It rewrites
timestamps under that interpreter's site-packages after the last pip
install. The torch-pinned interpreter is discarded with the container,
so nothing outside the build sees it.
- **Still unexplained:** in the latest run, three sm100a shards (cu129
aarch64, cu134 aarch64, cu134 x86_64) missed about 28 compiles each,
including generated `flash_kda` sm100a sources. It may be a one-time key
shift from the mtime pin, or another source of nondeterminism. The first
nightlies after merge will show which.
- **Not addressed here:**
- The roughly 5-minute `pytorch/manylinux` image pull per shard (about
3.5 runner-hours a night).
- The shim jobs spending 7 of their 8 minutes on that image pull and a
torch install they don't need.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Build Improvements**
* Nightly JIT-cache wheel builds now use the container’s torch-pinned
Python environment.
* Build dependencies are installed into the active interpreter, with
automatic retries for interrupted downloads.
* Header timestamps are standardized before compilation to improve build
reproducibility and caching.
  * Builds remain protected by a 90-minute no-output watchdog.

* **Tests**
* Expanded coverage for current-interpreter builds, dependency
installation, retry behavior, header handling, and deterministic
preprocessing.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fc933c5](https://github.com/flashinfer-ai/flashinfer/commit/fc933c5bdd11292c30a87db38e44f1ae4dc74984)

- **作者**: eigen
- **时间**: 2026-10-26T17:32:43Z
- **提交信息**: perf(cake_mm_fp4): entry L2 weight prefetch in the NVFP4 per-token quantize + GEMM chain (#7424)

`cake_mm_fp4` (`flashinfer.experimental.cake_nvfp4_per_token`,
experimental) quantizes activations to NVFP4 per token, then runs an
NVFP4 x NVFP4 GEMM. The family has two kernels and one fused form:

- The activation quantizer has three variants: bf16 activations, bf16
with the GEMM output scale folded into the per-token scale, and fp16
activations (K = 7168).
- The GEMM uses block-16 scales and a per-token alpha epilogue. It has
two variants: bf16 output and fp16 output.
- The fused form is the quantize -> GEMM chain, launched back to back
with programmatic dependent launch.

This PR changes the fused form for both GEMM variants (bf16 and fp16
output) on SM100 (`sm_100a`, B200) and SM103 (`sm_103a`, GB300). In the
chain, the GEMM starts while the quantizer still runs. Before it waits
for the quantizer's output, the GEMM now prefetches the weight tiles and
their scales of the CTA's first 4 K tiles into L2. The weight loads thus
overlap the quantizer. The activation operand is not prefetched. The
change applies on 12 small-M cells per architecture (one-CTA and split-K
GEMM tiles for M = 1 to 32, one-CTA tiles at M = 128), where the chain
picks a prefetching copy of the tile it already uses. The baseline is
the previous Cake version as shipped in `main` (`backend="cake"`). The
changed rows (64 quant+GEMM rows on B200, 56 on GB300) show a speedup of
1.010x to 1.076x on B200 and 1.012x to 1.081x on GB300. Every other
shape of the shape list keeps `main`'s programs on B200 and GB300, and
the GEMM-alone rows and the quantizer do not change.

**NVIDIA B200 (sm_100a), CUDA 13.4**: latency in µs of the quantize ->
GEMM chain (quant+GEMM, CUDA-graph replay of both kernels); median over
interleaved groups, mean of two GPUs; speedup = median of the paired
per-group ratios previous Cake / this PR, mean of two GPUs. dtype = GEMM
output dtype.

|kind|K|N|M|dtype|previous Cake µs|this PR µs|speedup|
|---|--:|--:|--:|---|--:|--:|--:|
|quant+GEMM|7168|1536|1|bf16|7.017|6.739|1.043|
|quant+GEMM|7168|1536|1|fp16|7.016|6.735|1.040|
|quant+GEMM|7168|1536|8|bf16|7.162|6.713|1.068|
|quant+GEMM|7168|1536|8|fp16|7.154|6.712|1.066|
|quant+GEMM|7168|1536|17|bf16|7.464|7.102|1.054|
|quant+GEMM|7168|1536|17|fp16|7.461|7.070|1.056|
|quant+GEMM|7168|1536|32|bf16|7.770|7.302|1.065|
|quant+GEMM|7168|1536|32|fp16|7.894|7.575|1.043|
|quant+GEMM|7168|2112|1|bf16|7.288|7.007|1.040|
|quant+GEMM|7168|2112|1|fp16|7.288|7.022|1.038|
|quant+GEMM|7168|2112|8|bf16|7.476|6.934|1.076|
|quant+GEMM|7168|2112|8|fp16|7.479|6.954|1.075|
|quant+GEMM|7168|2112|17|bf16|8.123|7.835|1.038|
|quant+GEMM|7168|2112|17|fp16|7.995|7.650|1.046|
|quant+GEMM|7168|2112|32|bf16|8.082|7.703|1.051|
|quant+GEMM|7168|2112|32|fp16|8.088|7.697|1.051|
|quant+GEMM|7168|18432|8|bf16|18.21|17.81|1.024|
|quant+GEMM|7168|18432|8|fp16|18.21|17.83|1.022|
|quant+GEMM|7168|18432|17|bf16|18.38|17.85|1.028|
|quant+GEMM|7168|18432|17|fp16|18.39|17.89|1.028|
|quant+GEMM|7168|18432|32|bf16|18.50|17.93|1.031|
|quant+GEMM|7168|18432|32|fp16|18.47|17.94|1.030|
|quant+GEMM|7168|18432|128|bf16|19.67|19.08|1.031|
|quant+GEMM|7168|18432|128|fp16|19.68|19.12|1.032|
|quant+GEMM|8192|8192|1|bf16|12.11|11.67|1.037|
|quant+GEMM|8192|8192|1|fp16|12.09|11.68|1.035|
|quant+GEMM|8192|8192|8|bf16|12.31|11.66|1.055|
|quant+GEMM|8192|8192|8|fp16|12.30|11.68|1.053|
|quant+GEMM|8192|8192|17|bf16|12.63|12.02|1.050|
|quant+GEMM|8192|8192|17|fp16|12.64|12.03|1.050|
|quant+GEMM|8192|8192|32|bf16|12.78|12.16|1.053|
|quant+GEMM|8192|8192|32|fp16|12.75|12.12|1.052|
|quant+GEMM|8192|8192|128|bf16|13.64|13.29|1.027|
|quant+GEMM|8192|8192|128|fp16|13.64|13.29|1.027|
|quant+GEMM|8192|28672|8|bf16|27.47|26.93|1.021|
|quant+GEMM|8192|28672|8|fp16|27.42|26.85|1.022|
|quant+GEMM|8192|28672|17|bf16|27.79|27.10|1.025|
|quant+GEMM|8192|28672|17|fp16|27.86|27.20|1.026|
|quant+GEMM|8192|28672|32|bf16|27.57|26.90|1.025|
|quant+GEMM|8192|28672|32|fp16|27.57|26.87|1.025|
|quant+GEMM|16384|7168|1|bf16|17.03|16.61|1.024|
|quant+GEMM|16384|7168|1|fp16|17.03|16.63|1.024|
|quant+GEMM|16384|7168|8|bf16|17.17|16.63|1.032|
|quant+GEMM|16384|7168|8|fp16|17.17|16.62|1.034|
|quant+GEMM|16384|7168|17|bf16|17.54|17.02|1.030|
|quant+GEMM|16384|7168|17|fp16|17.53|17.04|1.029|
|quant+GEMM|16384|7168|128|bf16|20.19|19.73|1.024|
|quant+GEMM|16384|7168|128|fp16|20.20|19.79|1.021|
|quant+GEMM|18432|7168|1|bf16|18.92|18.41|1.029|
|quant+GEMM|18432|7168|1|fp16|18.90|18.35|1.030|
|quant+GEMM|18432|7168|8|bf16|19.01|18.41|1.031|
|quant+GEMM|18432|7168|8|fp16|19.02|18.42|1.033|
|quant+GEMM|18432|7168|17|bf16|19.64|19.04|1.029|
|quant+GEMM|18432|7168|17|fp16|19.61|19.03|1.030|
|quant+GEMM|18432|7168|128|bf16|21.80|21.36|1.021|
|quant+GEMM|18432|7168|128|fp16|21.84|21.35|1.023|
|quant+GEMM|28672|8192|1|bf16|27.69|27.00|1.026|
|quant+GEMM|28672|8192|1|fp16|27.66|26.99|1.025|
|quant+GEMM|28672|8192|8|bf16|27.71|27.04|1.024|
|quant+GEMM|28672|8192|8|fp16|27.70|27.02|1.026|
|quant+GEMM|28672|8192|17|bf16|28.66|28.03|1.022|
|quant+GEMM|28672|8192|17|fp16|28.68|28.09|1.021|
|quant+GEMM|28672|8192|128|bf16|31.45|31.13|1.010|
|quant+GEMM|28672|8192|128|fp16|31.46|31.10|1.012|

**NVIDIA GB300 (sm_103a), CUDA 13.4**: latency in µs of the quantize ->
GEMM chain (quant+GEMM, CUDA-graph replay of both kernels); median over
interleaved groups, mean of two GPUs; speedup = median of the paired
per-group ratios previous Cake / this PR, mean of two GPUs. dtype = GEMM
output dtype.

|kind|K|N|M|dtype|previous Cake µs|this PR µs|speedup|
|---|--:|--:|--:|---|--:|--:|--:|
|quant+GEMM|7168|1536|1|bf16|6.740|6.390|1.055|
|quant+GEMM|7168|1536|1|fp16|6.761|6.397|1.054|
|quant+GEMM|7168|1536|8|bf16|6.868|6.391|1.073|
|quant+GEMM|7168|1536|8|fp16|6.883|6.384|1.075|
|quant+GEMM|7168|1536|17|bf16|7.075|6.604|1.072|
|quant+GEMM|7168|1536|17|fp16|7.080|6.599|1.073|
|quant+GEMM|7168|1536|32|bf16|7.301|6.753|1.078|
|quant+GEMM|7168|1536|32|fp16|7.316|6.759|1.081|
|quant+GEMM|7168|2112|1|bf16|7.133|6.754|1.056|
|quant+GEMM|7168|2112|1|fp16|7.156|6.762|1.059|
|quant+GEMM|7168|2112|8|bf16|7.256|6.729|1.078|
|quant+GEMM|7168|2112|8|fp16|7.278|6.726|1.081|
|quant+GEMM|7168|2112|17|bf16|7.597|7.220|1.053|
|quant+GEMM|7168|2112|17|fp16|7.588|7.238|1.052|
|quant+GEMM|7168|2112|32|bf16|7.743|7.266|1.063|
|quant+GEMM|7168|2112|32|fp16|7.735|7.277|1.063|
|quant+GEMM|7168|18432|8|bf16|17.52|17.21|1.018|
|quant+GEMM|7168|18432|8|fp16|17.49|17.20|1.016|
|quant+GEMM|7168|18432|17|bf16|17.61|17.24|1.024|
|quant+GEMM|7168|18432|17|fp16|17.66|17.21|1.026|
|quant+GEMM|7168|18432|32|bf16|17.70|17.25|1.026|
|quant+GEMM|7168|18432|32|fp16|17.71|17.22|1.028|
|quant+GEMM|7168|18432|128|bf16|18.64|18.11|1.030|
|quant+GEMM|7168|18432|128|fp16|18.67|18.08|1.031|
|quant+GEMM|8192|8192|1|bf16|11.68|11.22|1.041|
|quant+GEMM|8192|8192|1|fp16|11.68|11.21|1.041|
|quant+GEMM|8192|8192|8|bf16|11.88|11.26|1.056|
|quant+GEMM|8192|8192|8|fp16|11.89|11.24|1.057|
|quant+GEMM|8192|8192|17|bf16|12.27|11.66|1.053|
|quant+GEMM|8192|8192|17|fp16|12.24|11.66|1.050|
|quant+GEMM|8192|8192|32|bf16|12.35|11.94|1.033|
|quant+GEMM|8192|8192|32|fp16|12.34|11.94|1.035|
|quant+GEMM|8192|28672|1|bf16|25.81|25.32|1.019|
|quant+GEMM|8192|28672|1|fp16|25.84|25.33|1.020|
|quant+GEMM|8192|28672|8|bf16|26.02|25.39|1.025|
|quant+GEMM|8192|28672|8|fp16|26.06|25.36|1.027|
|quant+GEMM|8192|28672|17|bf16|26.72|26.39|1.012|
|quant+GEMM|8192|28672|17|fp16|26.68|26.36|1.013|
|quant+GEMM|16384|7168|1|bf16|16.43|16.01|1.026|
|quant+GEMM|16384|7168|1|fp16|16.43|16.05|1.024|
|quant+GEMM|16384|7168|8|bf16|16.57|16.04|1.033|
|quant+GEMM|16384|7168|8|fp16|16.57|16.05|1.032|
|quant+GEMM|16384|7168|17|bf16|16.96|16.42|1.033|
|quant+GEMM|16384|7168|17|fp16|16.95|16.41|1.032|
|quant+GEMM|18432|7168|1|bf16|18.29|17.65|1.037|
|quant+GEMM|18432|7168|1|fp16|18.25|17.69|1.032|
|quant+GEMM|18432|7168|8|bf16|18.33|17.72|1.034|
|quant+GEMM|18432|7168|8|fp16|18.37|17.71|1.037|
|quant+GEMM|18432|7168|17|bf16|18.59|17.99|1.034|
|quant+GEMM|18432|7168|17|fp16|18.59|18.02|1.032|
|quant+GEMM|28672|8192|1|bf16|27.10|26.44|1.024|
|quant+GEMM|28672|8192|1|fp16|27.16|26.43|1.027|
|quant+GEMM|28672|8192|8|bf16|27.17|26.52|1.024|
|quant+GEMM|28672|8192|8|fp16|27.21|26.51|1.026|
|quant+GEMM|28672|8192|17|bf16|27.60|26.98|1.023|
|quant+GEMM|28672|8192|17|fp16|27.62|26.97|1.024|

Cake ships no other data type, layout or fused form of this kernel; the
family ships on `sm_100a` (B200, GB200) and `sm_103a` (GB300, B300)
only, and GB200 and B300 take the new chain programs on the same cells.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized per-token NVFP4 matrix multiplication paths for
supported GPU architectures and workloads.
* Selected chained GEMM operations can prefetch data into cache, while
standalone GEMM behavior remains unchanged.
* **Bug Fixes**
* Added checks to avoid writing beyond the output boundary on partial
tiles.
* **Tests**
* Added coverage for tactic selection and verified that chained results
match standalone GEMM results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6785a48](https://github.com/flashinfer-ai/flashinfer/commit/6785a485ac9ff5b129662b9b4ec6523d8d21ccf8)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T17:26:00Z
- **提交信息**: fix(cake_kimi_k3_fp8_projection): take the resident decode slot modulo the ring (#6900)

The Cake Kimi-K3 FP8 block-scaled projection (`kimi_k3_fp8_projection`)
ships a GEMM stage, a quantization stage, and a decode stage with many
dispatch-table instances. This PR changes the four resident-token-tile
decode programs: they now take the resident slot of the current token
tile modulo the 4-slot ring. Before, they took the slot one before the
cursor after it advanced, which would be slot −1 for a CTA's fourth
token tile. This is a defensive fix. The dispatch table selects the
resident programs only on cells whose CTAs hold at most two token tiles,
so no shipped route reached the bad slot. Outputs are unchanged and
speed is unchanged. The table compares against the previous Cake version
on NVIDIA GB300 (SM103), CUDA 13.3. Each entry is the per-call latency
of one projection at cold L2, the median of 6 alternating processes per
side; "cooled" adds an idle delay before every call.

| shape (N, K, M) | before (us) | after (us) | speedup | before, cooled
(us) | after, cooled (us) | speedup, cooled |
|---|---|---|---|---|---|---|
| 1536, 128, 256 | 4.19 | 4.19 | 1.000x | 4.19 | 4.19 | 1.000x |
| 1536, 128, 200 | 4.16 | 4.16 | 1.000x | 4.16 | 4.16 | 1.000x |
| 12288, 128, 256 | 6.69 | 6.69 | 1.000x | 6.69 | 6.69 | 1.000x |
| 12288, 128, 77 | 5.63 | 5.63 | 1.000x | 5.70 | 5.73 | 0.994x |
| 12288, 128, 64 | 5.12 | 5.12 | 1.000x | 5.12 | 5.12 | 1.000x |

The GEMM and quantization stages and the non-resident decode programs
are unchanged. The family ships for SM100 and SM103.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
  - Fixed residual-buffer slot selection in the Kimi K3 FP8 projection.
- Corrected wraparound behavior when processing the first buffer stage,
preventing invalid indexing and ensuring the previous slot is selected
consistently.
- Preserved all other projection behavior while improving reliability
across supported kernel variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4bd511a](https://github.com/flashinfer-ai/flashinfer/commit/4bd511ac3d20724d78b0da92fee9dae6caf1a8b5)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T17:25:00Z
- **提交信息**: fix(cake_kimi_k3_mla): keep the wide kernel's TMEM scrub address the same in every lane (#6899)

The Cake Kimi-K3 MLA FP8 paged-attention backend (`backend="cake"`)
ships five swapped-AB row-tile decode programs, a two-CTA wide program
for long-KV rows, and four split-KV reduce programs. This PR changes the
wide program: its TMEM scrub now gives `tcgen05.st` the warp's own lane
quarter as the address in every lane, as the instruction requires;
before, it added the lane index to the lane field. Outputs are unchanged
and speed is unchanged. The table compares against the previous Cake
version of the wide program on NVIDIA GB300 (SM103), CUDA 13.3: per-call
latency at cold L2, the median of 9–10 alternating processes per side;
"cooled" adds an idle delay before every call.

| shape (heads, q lens, KV lens) | before (us) | after (us) | speedup |
before, cooled (us) | after, cooled (us) | speedup, cooled |
|---|---|---|---|---|---|---|
| 96, [1], [9000] | 18.18 | 18.02 | 1.009x | 18.21 | 18.19 | 1.001x |
| 96, [1, 1], [20000, 16385] | 18.82 | 19.02 | 0.989x | 19.07 | 18.77 |
1.016x |
| 96, [1], [76800] | 23.46 | 23.49 | 0.999x | 23.46 | 23.46 | 1.000x |
| 96, [4, 3], [20000, 16385] | 22.27 | 22.26 | 1.001x | 22.30 | 22.27 |
1.001x |

The row-tile and reduce programs of this backend are unchanged; all
programs ship for SM100 and SM103.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected an internal memory cleanup operation to target the intended
base row, improving reliability of the related processing path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9cce378](https://github.com/flashinfer-ai/flashinfer/commit/9cce37835f0e5dcf613a8088ee001cbf25fb7aaa)

- **作者**: eigen
- **时间**: 2026-10-26T17:21:41Z
- **提交信息**: perf(cake_kimi_k3_vision_tower): faster vision tower programs on SM100 / SM103 (#7422)

This PR delivers a faster version of the Cake Kimi-K3 vision tower
(`kimi_k3_vision_tower`). The package runs the whole tower: the
MoonViT-3D encoder (27 layers) followed by the PatchMergerV2 merge. The
kernel comes in one data type (BF16 activations and weights, FP32
accumulation) and one layout (packed variable-length token sequences for
images, document pages, batches and video frames). This PR delivers a
faster version of that variant on sm_100a and sm_103a. The table
compares it with the previous Cake version of this package as shipped on
FlashInfer main `5e4555094c`. Every shape is faster on both GPUs: 1.011x
to 1.074x on B200 and 1.007x to 1.058x on B300.

| shape | B200 baseline (ms) | B200 this PR (ms) | B200 speedup | B300
baseline (ms) | B300 this PR (ms) | B300 speedup |
|---|---:|---:|---:|---:|---:|---:|
| img_224 | 0.937 | 0.896 | 1.045x | 0.908 | 0.858 | 1.058x |
| img_336 | 1.295 | 1.243 | 1.042x | 1.228 | 1.176 | 1.044x |
| img_448 | 1.510 | 1.485 | 1.017x | 1.406 | 1.391 | 1.011x |
| img_640x480 | 2.393 | 2.340 | 1.022x | 2.189 | 2.122 | 1.031x |
| img_800x600 | 3.597 | 3.350 | 1.074x | 3.332 | 3.196 | 1.043x |
| img_1024x768 | 6.093 | 6.000 | 1.015x | 5.811 | 5.768 | 1.007x |
| img_1280x720 | 7.433 | 7.300 | 1.018x | 7.096 | 6.963 | 1.019x |
| img_1920x1080 | 23.811 | 23.250 | 1.024x | 21.931 | 21.444 | 1.023x |
| doc_1240x1754 | 25.741 | 25.247 | 1.020x | 23.651 | 23.006 | 1.028x |
| img_2560x1440 | 60.607 | 59.711 | 1.015x | 54.548 | 53.816 | 1.014x |
| img_3840x2160 | 263.120 | 259.476 | 1.014x | 229.554 | 227.975 |
1.007x |
| img_max_4096sq | 598.164 | 591.914 | 1.011x | 522.614 | 515.871 |
1.013x |
| batch4_1024x768 | 23.103 | 22.534 | 1.025x | 21.408 | 20.745 | 1.032x
|
| batch8_448 | 7.615 | 7.412 | 1.028x | 7.477 | 7.288 | 1.026x |
| mixed_1080p_xga_448_336 | 30.830 | 30.132 | 1.023x | 28.476 | 27.744 |
1.026x |
| video_720p_4f | 59.423 | 58.745 | 1.012x | 53.108 | 52.364 | 1.014x |
| video_1080p_4f | 259.328 | 255.426 | 1.015x | 223.835 | 222.019 |
1.008x |
| video_720p_32f | 475.379 | 462.440 | 1.028x | 423.062 | 416.124 |
1.017x |
| video_480p_64f | 166.101 | 162.011 | 1.025x | 151.919 | 148.493 |
1.023x |

Measured on NVIDIA B200 (sm_100a, driver 580.82.07) and NVIDIA B300 SXM6
AC (sm_103a, driver 580.126.09) with CUDA 13.4. Each number is a
whole-tower forward pass under CUDA graph replay with a cold L2. Each ms
value is the mean of three session medians on three GPUs of one node,
and each speedup is the mean of the per-session median ratios (baseline
/ this PR).

Cake ships no other data type, layout or fused form of this tower, and
the package targets only sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-aware execution paths for the Kimi K3 vision tower,
including attention and GEMM routing tuned for different workloads.
* Added support for selecting prebuilt or just-in-time compiled
libraries, with compatibility checks for the local CUDA environment.
* **Performance**
* Expanded kernel coverage and refined tile selection for
out-projection, FC1, and normalization workloads.
* Improved handling of split attention work on supported GPU
architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6bd679e](https://github.com/flashinfer-ai/flashinfer/commit/6bd679e419be65e18c552edf3c7ab00a613f06d1)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T17:19:45Z
- **提交信息**: fix(cake_stepfun_moe): proxy fence before the MXFP8 tile-256 FC1 tcgen05.cp scale reads (#7428)

`flashinfer.experimental.cake_stepfun_moe` ships the StepFun SwiGLU-Step
routed MoE in five precision families (BF16, per-tensor FP8, MXFP8,
NVFP4 and per-token NVFP4) on sm_100a and sm_103a, each with FC1
programs for several token tiles. This PR changes one program: the MXFP8
tile-256 FC1 kernel (`cake_stepfun_moe_c16c727913eac39c7f25`), on both
architectures.

It fixes a memory-ordering bug. The kernel's scale-factor loader fills
the B scale factors in shared memory with `cp.async`, which writes
through the generic proxy. The leader CTA then copies them into tensor
memory with `tcgen05.cp`, which reads shared memory through the async
proxy. The PTX ISA (tcgen05 memory consistency model, "Shared Memory
Accesses") requires a `fence.proxy.async` between generic-proxy writes
to shared memory and a `tcgen05.cp` that reads them. The loader had no
such fence between its `cp.async.wait_group` and the mbarrier arrival
that publishes the stage to the leader. This PR adds
`fence.proxy.async.shared::cta` after each `cp.async.wait_group` (the
in-loop `wait_group 1` and the tail `wait_group 0`) and updates the
unit's two `build.json` digests. No other program changes.

The fence costs a little on the FC1 launch (MXFP8, tile 256, T = 2048,
64 experts, top-8, H 4096, I 1536; median of 4 interleaved runs of 500
launches; GB300 sm_103a, CUDA 13.3):

| L2 | Previous (us) | This PR (us) | Speedup |
|---|---:|---:|---:|
| hot | 211.9 | 213.3 | 0.993x |
| cold | 200.8 | 201.0 | 0.999x |

`tests/experimental/test_cake_stepfun_moe.py` passes in full on sm_103a
(299 passed), including the three MXFP8 tile-256 FC1 stage cells against
the fp32 reference, and the 88 MXFP8 cases of
`tests/experimental/test_cake_stepfun_moe_api.py` (full path against the
native TRT-LLM pipeline) pass.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization while loading data in the StepFun MoE GPU
workload, ensuring pending asynchronous transfers are visible before
processing advances between stages. This update affects the underlying
execution of the workload; it does not add user-facing controls or
change how the feature is used. No other behavior changes are included
in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [05e4258](https://github.com/flashinfer-ai/flashinfer/commit/05e425835b0abc8ee57852ee1815e67e937f0ccc)

- **作者**: eigen
- **时间**: 2026-10-26T17:18:21Z
- **提交信息**: fix(cake_minimax_h3): fence the stage release of the SM120 out-projection CTA-epilogue programs (#7437)

`flashinfer.diffusion_ops.cake_minimax_h3_sm120_quant_out_proj` computes
the MiniMax-H3 out-projection on SM120 (`sm_120a`) in two variants: FP8
per-token (`minimax_h3_fp8_out_proj`) and NVFP4
(`minimax_h3_nvfp4_out_proj`). Each variant runs as one persistent
launch that does the activation quantization, the GEMM and the
gate/residual epilogue. Each quantization has two programs. The
warp-epilogue program runs on the 188-SM RTX PRO 6000 Blackwell. The
CTA-epilogue program runs on every other `sm_120a` device, such as the
RTX 5090. This PR changes only the CTA-epilogue programs. Every MMA lane
now issues `fence.proxy.async.shared::cta` after its `ldmatrix` /
`ld.shared` reads of a shared-memory ring stage and before the warp
releases that stage to the TMA producer. The fence is needed because the
TMA refill is an async-proxy write, and the release arrive alone does
not order the earlier generic-proxy reads before that write. The
warp-epilogue programs already had this fence. The host code and the
arithmetic are unchanged, and the output is bitwise equal. This fixes
ordering and is not meant to speed anything up. Compared with FlashInfer
main on the RTX 5090, the six FP8 shapes are unchanged within
measurement noise (0.998x to 1.003x) and the six NVFP4 shapes run about
0.2 % slower (0.995x to 0.999x).

NVIDIA GeForce RTX 5090 (`sm_120a`, 170 SMs), CUDA 13.4. Time of the
complete operator (activation quantization + GEMM + gated residual),
cold L2, interleaved rounds; before = FlashInfer main, two independent
arms. Each value is the geometric mean over 8 sessions on one board,
because single sessions on this board vary by more than the difference.
M = rows.

| quantization | M | before (µs) | after (µs) | speedup |
|---|---:|---:|---:|---:|
| FP8 | 33472 | 4330.3 | 4319.6 | 1.002x |
| FP8 | 38592 | 4992.4 | 5000.0 | 0.998x |
| FP8 | 48768 | 6325.4 | 6331.0 | 0.999x |
| FP8 | 58944 | 7694.6 | 7713.9 | 0.998x |
| FP8 | 74240 | 9776.5 | 9770.1 | 1.001x |
| FP8 | 109952 | 14563.8 | 14526.3 | 1.003x |
| NVFP4 | 33472 | 2302.9 | 2310.2 | 0.997x |
| NVFP4 | 38592 | 2670.9 | 2674.3 | 0.999x |
| NVFP4 | 48768 | 3423.5 | 3430.0 | 0.998x |
| NVFP4 | 58944 | 4197.0 | 4202.2 | 0.999x |
| NVFP4 | 74240 | 5368.2 | 5394.5 | 0.995x |
| NVFP4 | 109952 | 8059.8 | 8080.7 | 0.997x |

The SM100/SM103 module `flashinfer.diffusion_ops.minimax_h3_out_proj`
ships BF16, MXFP8 and NVFP4 variants of the same projection on `sm_100a`
and `sm_103a`; with this module the family covers `sm_100a`, `sm_103a`
and `sm_120a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization in FP8 and NVFP4 fused GEMM operations to
help ensure reliable execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [dc50add](https://github.com/flashinfer-ai/flashinfer/commit/dc50addf12a0bda0d63941024b06c5c6be2f1ae5)

- **作者**: eigen
- **时间**: 2026-10-26T17:16:47Z
- **提交信息**: perf(cake_ulysses): direct-write NVLink all-to-all into registered outputs (#7440)

Cake's Ulysses all-to-all for `flashinfer.comm` sequence parallelism
(scatter heads / gather heads over NVLink) has 48 programs: bf16 / f16 /
f32 × world sizes 2 / 4 / 6 / 8 × both directions × two routes. This PR
adds the 24-program direct route: when the output was allocated by
`allocate_output` on NVLink, which now allocates collectively and
registers symmetric memory, each rank writes its stripes straight into
the peers' outputs with no staging buffer or copy (outputs from plain
`torch.empty` keep the staged route). The baseline is the previous Cake
version, the staged route that ships today, on the same shapes.

**NVIDIA B300 SXM6 AC (sm_103a), 8 GPUs, CUDA 13.4, PyTorch
2.14.1+cu130.** bf16, batch 1, global sequence length 32760, head dim
128 (local sequence 16380 / 8190 / 5460 / 4095 at world 2 / 4 / 6 / 8).
Latency is in us per call, taken as the median of the slowest rank per
iteration. Speedup = previous Cake / this PR.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---:|---:|---|---:|---:|---:|
| 2 | 40 | scatter heads | 147.14 | 140.80 | 1.045x |
| 2 | 40 | gather heads | 147.67 | 139.49 | 1.059x |
| 4 | 40 | scatter heads | 118.02 | 109.44 | 1.078x |
| 4 | 40 | gather heads | 117.92 | 109.52 | 1.077x |
| 6 | 48 | scatter heads | 113.58 | 102.54 | 1.108x |
| 6 | 48 | gather heads | 114.96 | 103.84 | 1.107x |
| 8 | 40 | scatter heads | 86.02 | 79.12 | 1.087x |
| 8 | 40 | gather heads | 86.13 | 78.72 | 1.094x |

**NVIDIA B200 (sm_100a), 8 GPUs, CUDA 13.4, PyTorch 2.14.1+cu130.** Same
shapes, metric and ratio as above.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---:|---:|---|---:|---:|---:|
| 2 | 40 | scatter heads | 144.91 | 137.50 | 1.054x |
| 2 | 40 | gather heads | 144.06 | 137.49 | 1.048x |
| 4 | 40 | scatter heads | 116.93 | 108.72 | 1.075x |
| 4 | 40 | gather heads | 116.16 | 108.45 | 1.071x |
| 6 | 48 | scatter heads | 112.16 | 100.90 | 1.112x |
| 6 | 48 | gather heads | 114.66 | 102.86 | 1.115x |
| 8 | 40 | scatter heads | 82.85 | 75.86 | 1.092x |
| 8 | 40 | gather heads | 83.50 | 76.00 | 1.099x |

For outputs that are not registered, Cake also ships the staged route
for the same data types (bf16, f16, f32), world sizes (2, 4, 6, 8) and
both directions, and the whole family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added registered-output support for eligible NVLink Cake communication
routes. Allocated outputs can be reused across scatter and gather
operations, while caller-provided outputs continue to use the existing
path.
* Registered outputs are released when the communicator closes. Allocate
each output shape before CUDA graph capture.
* **Documentation**
  * Clarified registered-output behavior and route availability.
* **Benchmarks**
* Added registered-output results, including speedups when the route is
available and clear unavailable-route reporting.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [396ffba](https://github.com/flashinfer-ai/flashinfer/commit/396ffbad724d8864b55090435026d2c48833218a)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T17:16:03Z
- **提交信息**: fix(cake_kda): fence the BF16 BT16 prepare's tail repair before the next raw TMA fill (#7170)

**Proxy fence.** In the BF16 BT16 KDA prefill prepare kernels
(`csrc/kda/cake_flashkda_bf16_bt16_prepare.cu`,
`cake_flashkda_bf16_bt16_prepare_beta_tma.cu`,
`flashkda_generated_bf16_bt16_prepare_0d8e6c8011.cu`), a partial chunk
zeroes the invalid tail of the raw Q, K and gate tiles in shared memory
with generic stores. Two `__syncthreads()` later, the elected thread
issues the next chunk's TMA load into the same tiles, and that load
writes through the async proxy. The chunk's first
`fence.proxy.async.shared::cta` comes after the load is issued, so the
PTX memory model does not order the generic tail stores before the
async-proxy write that overwrites them. Each thread now fences after its
tail stores and before the barrier that precedes the refill. Only
partial chunks run it.

**Code change.** One `fence.proxy.async.shared::cta` on the
partial-chunk path in each of the three kernels. Nothing else changes.

**Validation.** The three translation units compile for sm_100a and
sm_103a. The same change was validated on GB300, with sm_103a builds of
the same kernel:
- Output matches the FP32 reference.
- compute-sanitizer synccheck is clean.
- Timing, back to back and cooled: identical at H1 T8192 (15.94 µs). On
a varlen batch where about 44% of chunks are partial (H12, 256 sequences
of 9 to 47 tokens) it is +0.29% (55.17 vs 55.00 µs).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of partial and tail chunks across supported
processing paths. Zero-filled values are now made visible before
processing continues, helping prevent incorrect results when input
lengths do not align with full chunks. This update applies consistently
across the affected execution paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6ba6bdf](https://github.com/flashinfer-ai/flashinfer/commit/6ba6bdf377ebffc01ebe2a80ca8b06c38fe76c72)

- **作者**: yunruis
- **时间**: 2026-10-26T17:14:57Z
- **提交信息**: feat(prims-ts): opt-in Add skip correction for dense and sparse MLA decode (#7026)

## 📌 Description

**Impact:** Adds an opt-in `softmax_rescale_threshold_log2` to PrimTS
dense and sparse MLA decode, passed through a new compile-time tuning
struct `MLAAttentionTuning`. The name and the FP8 P scale (`448 *
2**-T`) follow the existing PrimTS FMHA decode option of the same name.
The bounds follow the trtllm-gen FMHA `skipCorrThreshold`, and at T=0
and T=8 the FP8 P scale equals trtllm-gen's `getSoftmaxPScale`.

- **Default unchanged.** `tuning=None` (the default) keeps dense on
exact rescale and sparse on each schedule's existing behavior (including
the fixed six-binade BF16 deferral from #5434). The default adds no
kernel variant: it builds the same kernels as main. Dense SASS is also
identical to main for FP8/BF16 `throughput_2cta` and for the 1CTA swaps
and keeps variants.
- **Speedup, FP8 (T=8 vs default, B200).** DSV4 sparse MLA: generation
1.000-1.050x, context 1.068-1.097x (H128 Q4096: 680.18 to 619.79 us).
DeepSeek-R1 dense MLA: H128 generation 1.010-1.039x, context
1.037-1.057x; H16 generation at most 1.008x.
- **Speedup, BF16.** Sparse 2CTA schedules gain 1.017-1.063x at T=6 or
8. Sparse schedules that already defer by six binades by default are
unchanged; an explicit 0 there is 3-5.5% slower. Dense BF16 is
1.000-1.034x.
- **FP8 precision cost.** A positive T quantizes FP8 P at `448 * 2**-T`
instead of 448. At T=8 (scale 1.75, the trtllm-gen value) this costs
precision on rows with an attention sink and a long low-probability
tail; smaller T costs much less (see Accuracy). Check model accuracy
before enabling it for FP8.

### User-facing API

One new opt-in argument, `tuning`, on every PrimTS MLA entry point. It
applies to context (multi-token Q, causal) and generation alike: both
phases run through the same wrappers, despite the `Decode` in their
names. It takes a frozen `MLAAttentionTuning` (exported from
`flashinfer.attention.prims_ts`); its only field today is
`softmax_rescale_threshold_log2` (`T`, in binades). Later compile-time
knobs become new fields, not new arguments.

```python
from flashinfer.attention.prims_ts import (
    BatchMLADecodePagedTSWrapper,
    BatchSparseMLADecodePagedTSWrapper,
    MLAAttentionTuning,
    batch_mla_decode_with_paged_kv_cache,
)

# 1. Default: omit tuning. Same kernels and outputs as before this PR.
wrapper = BatchMLADecodePagedTSWrapper()
wrapper.plan(device, batch, heads, 512, 64, page_size, max_kv_len,
             max_seq_len_q=1, packed_query=False,
             q_data_type=torch.float8_e4m3fn, kv_data_type=torch.float8_e4m3fn,
             o_data_type=torch.bfloat16)

# 2. Dense FP8 with skip correction at T = 8 (trtllm-gen's FP8 setting; P scale 1.75).
wrapper.plan(..., tuning=MLAAttentionTuning(softmax_rescale_threshold_log2=8.0))

# 3. Smaller T: less skipping, much smaller FP8 precision cost (P scale 448 * 2**-4 = 28).
out = batch_mla_decode_with_paged_kv_cache(
    query, kv_cache, block_tables, seq_lens,
    tuning=MLAAttentionTuning(softmax_rescale_threshold_log2=4.0))

# 4. Sparse: None keeps each schedule's default (some BF16 schedules already defer by 6);
#    an explicit value replaces it on every schedule, and 0.0 forces exact rescale.
sparse = BatchSparseMLADecodePagedTSWrapper()
sparse.plan(device, batch, heads, max_topk=2048, q_data_type=torch.bfloat16,
            tuning=MLAAttentionTuning(softmax_rescale_threshold_log2=6.0))
```

| `tuning` / `softmax_rescale_threshold_log2` | Dense | Sparse |
|---|---|---|
| `None` (default) | exact rescale (unchanged) | each schedule's
existing behavior (unchanged) |
| `0.0` | exact rescale | exact rescale on every schedule |
| `0 < T <= 8` (FP8) / `<= 32` (BF16) | skip rescale while the row max
rises by `<= T` binades; FP8 P scale `448 * 2**-T` | same, on every
schedule |
| out of range, NaN/inf | `ValueError` from `plan()`, also with
`validate=False` | same |
| not an `MLAAttentionTuning` | `TypeError` | same |

`T` is compiled into the kernel, so each distinct value builds its own
kernel; a deployment normally picks one. The same `tuning` argument is
accepted by `batch_sparse_mla_decode_with_paged_kv_cache` and
`get_prims_ts_sparse_mla_decode_workspace_size`. The benchmark exposes
it as `--mla_softmax_rescale_threshold_log2`.

**What it does.**
`BatchMLADecodePagedTSWrapper.plan(tuning=MLAAttentionTuning(softmax_rescale_threshold_log2=T))`,
`batch_mla_decode_with_paged_kv_cache(...)`,
`BatchSparseMLADecodePagedTSWrapper.plan(...)`,
`batch_sparse_mla_decode_with_paged_kv_cache(...)` and
`get_prims_ts_sparse_mla_decode_workspace_size(...)` take
`tuning=MLAAttentionTuning(...)` (frozen dataclass, exported from
`flashinfer.attention.prims_ts`; later compile-time knobs extend it
instead of every signature). `T` is in binades (log2 units);
`tuning=None` or a `None` field keeps each entry point's default.
- **Skip.** A positive `T` keeps a row's softmax anchor while a K tile
raises the row maximum by at most `T`: `(m_new - m_old) *
softmax_scale_log2 <= T`. The O rescale (correction) for that tile is
then skipped through the existing exact-equality skip path.
- **Re-anchor.** A tile that raises the maximum by more than `T`
re-anchors the row and rescales O as before.
- **FP8 P scale.** Probabilities can then reach `2**T`, so FP8 P uses
`448 * 2**-T`, which keeps the scaled P within 448 (as
`FmhaDecodeConfig.fp8_p_quant_scale` does for the PrimTS FMHA decode
path). This gives 448 at T=0 and 1.75 at T=8, both equal to trtllm-gen;
trtllm-gen uses 1.75 for every T > 0, and its `getSoftmaxPScale` comment
allows any scale with `scale * 2**T <= 448`. The matching reciprocal is
used for LSE and attention sinks.
- **Bounds.** `T <= 8` for FP8 QKV and `T <= 32` for BF16 QKV, as
trtllm-gen checks; out-of-range values raise rather than clamp. `plan()`
always enforces them, including with `validate=False`, and so do the
kernel constructors. The value is canonicalized to float32; a positive
value that rounds to zero, a non-real value, NaN and inf are rejected.
- **Coverage.** Both `throughput_2cta` and `throughput_latency_1cta`
support it, for dense and sparse attention. Sparse reuses the same
kernels and P-scale helpers, so the sparse change is API plumbing.
- **Sparse default.** Sparse `None` keeps each schedule's behavior:
several BF16 schedules already keep the anchor within six binades
(`defer_sparse_max_update`, #5434, matching FlashMLA). An explicit value
replaces that deferral on every schedule: `0.0` restores exact maxima
(3-5.5% slower on those schedules, so callers forwarding a
trtllm-gen-style 0 should pass `None`), and a positive value applies the
threshold.

**Why compile-time.** `T` is part of the kernel config and compile key,
and is compared in the log2 domain. An earlier version passed `T` as a
runtime kernel scalar and divided it by the softmax scale in-kernel.
Under the 128-register cap that cost an extra spill slot, reloaded every
softmax tile, plus an fdiv slow path. FP8 2CTA then ran up to 19%
*slower*, even with the freeze inactive.

**Also in this PR.**
- The wrapper trace adds a `_rescale_thr<T>` name suffix (shortest
float32 text) and a tag for nonzero thresholds; zero keeps existing
names.
- The one-shot trace template gains the optional scalar input.
- `benchmarks/flashinfer_benchmark.py` gains
`--mla_softmax_rescale_threshold_log2` for the prims-ts dense MLA
routine; the result column is written only when it is nonzero. The
sparse numbers below come from the standalone script in the details
block.

**Performance.** Measured with an earlier revision of this PR that used
a fixed FP8 P scale of 1.75 for every T > 0. The timed kernels are the
same as in the final version: at T=8, `448 * 2**-8` is exactly 1.75, and
BF16 P is unscaled. B200 (umb-b200-263, 148 SMs), CUPTI, random inputs.
Each value is the median of 5 rounds with the variant order rotated, at
200 iterations per round (50 warmup) for generation and 100 (20 warmup)
for context. Every shape was compiled and its inputs built before any
timing started, and timing ran one process at a time. *spread* is the
largest (max - min) / median over the variants. Rows marked * have a
spread above 2% (mostly the long, compute-heavy launches); treat their
differences as within noise. In an earlier run of the same matrix, three
of them changed sign: dense BF16 H128 generation at B128 and B256
(0.970x and 0.985x there) and sparse BF16 H128 B16 (1.017x there).

*DSV4 sparse MLA* (`BatchSparseMLADecodePagedTSWrapper`, D512, primary
source = SWA window 128, extra source = CSA top-k or HCA compressed
slots, random indices into 65536-row pools, Q/KV `0.15 * randn`, BF16
output). "default" is `None`; for FP8 it is the exact rescale (same
kernel as T=0). "deferred" marks BF16 schedules whose default already
keeps the anchor within six binades.

| phase | dtype | H | B | Q | extra | schedule | default (us) | T=0 (us)
| T=6 (us) | T=8 (us) | best vs default | spread |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| gen | FP8 | 128 | 16 | 1 | CSA 1024 | 2CTA | 15.90 | - | - | 15.14 |
1.050x (T=8) | 0.1% |
| gen | FP8 | 128 | 64 | 1 | CSA 1024 | 2CTA | 18.21 | - | - | 17.57 |
1.036x (T=8) | 0.4% |
| gen | FP8 | 128 | 128 | 1 | CSA 1024 | 2CTA | 28.90 | - | - | 28.03 |
1.031x (T=8) | 0.3% |
| gen | FP8 | 128 | 256 | 1 | CSA 1024 | 2CTA | 48.96 | - | - | 47.17 |
1.038x (T=8) | 0.2% |
| gen | FP8 | 128 | 64 | 1 | HCA 512 | 2CTA | 14.11 | - | - | 13.92 |
1.014x (T=8) | 0.7% |
| gen | FP8 | 128 | 256 | 1 | HCA 512 | 2CTA | 35.20 | - | - | 34.15 |
1.031x (T=8) | 0.4% |
| gen | FP8 | 64 | 16 | 1 | CSA 512 | 1CTA keep split 5 | 14.14 | - | -
| 14.14 | 1.000x (T=8) | 0.3% |
| gen | FP8 | 64 | 64 | 1 | CSA 512 | 1CTA keep | 17.92 | - | - | 17.60
| 1.018x (T=8) | 0.2% |
| gen | FP8 | 64 | 128 | 1 | CSA 512 | 1CTA keep | 19.52 | - | - | 18.94
| 1.031x (T=8) | 0.2% |
| gen | FP8 | 64 | 256 | 1 | CSA 512 | 1CTA keep | 32.16 | - | - | 30.82
| 1.043x (T=8) | 0.2% |
| gen | BF16 | 128 | 16 | 1 | CSA 1024 | 1CTA keep split 4, deferred |
20.16 | 20.99 | 20.38 | 20.54 | 0.989x (T=6) | 2.7% * |
| gen | BF16 | 128 | 64 | 1 | CSA 1024 | 2CTA | 29.50 | 29.09 | 28.80 |
28.85 | 1.024x (T=6) | 0.4% |
| gen | BF16 | 128 | 128 | 1 | CSA 1024 | 2CTA | 53.57 | 53.86 | 52.70 |
52.70 | 1.017x (T=6) | 0.2% |
| gen | BF16 | 128 | 256 | 1 | CSA 1024 | 2CTA | 91.52 | 91.30 | 89.20 |
89.07 | 1.028x (T=8) | 2.6% * |
| gen | BF16 | 128 | 64 | 1 | HCA 512 | 2CTA | 21.31 | 21.25 | 20.96 |
20.99 | 1.017x (T=6) | 0.3% |
| gen | BF16 | 128 | 256 | 1 | HCA 512 | 2CTA | 63.07 | 62.91 | 61.55 |
61.34 | 1.028x (T=8) | 0.2% |
| gen | BF16 | 64 | 16 | 1 | CSA 512 | 1CTA keep split 5 | 16.10 | 16.03
| 16.19 | 16.02 | 1.005x (T=8) | 0.2% |
| gen | BF16 | 64 | 64 | 1 | CSA 512 | 2CTA | 21.44 | 21.28 | 20.77 |
20.86 | 1.032x (T=6) | 0.5% |
| gen | BF16 | 64 | 128 | 1 | CSA 512 | 1CTA keep, deferred | 31.04 |
32.83 | 31.20 | 31.07 | 0.999x (T=8) | 0.2% |
| gen | BF16 | 64 | 256 | 1 | CSA 512 | 1CTA keep, deferred | 48.96 |
50.40 | 48.93 | 48.98 | 1.001x (T=6) | 0.2% |
| context | FP8 | 128 | 1 | 1024 | CSA 1024 | 2CTA | 150.08 | - | - |
140.38 | 1.069x (T=8) | 0.2% |
| context | FP8 | 128 | 1 | 4096 | CSA 1024 | 2CTA | 680.18 | - | - |
619.79 | 1.097x (T=8) | 4.4% * |
| context | FP8 | 64 | 1 | 1024 | CSA 512 | 1CTA keep | 90.56 | - | - |
84.83 | 1.068x (T=8) | 0.2% |
| context | FP8 | 64 | 1 | 4096 | CSA 512 | 1CTA keep | 324.08 | - | - |
300.59 | 1.078x (T=8) | 0.3% |
| context | BF16 | 128 | 1 | 1024 | CSA 1024 | 2CTA | 307.86 | 309.84 |
298.11 | 299.99 | 1.033x (T=6) | 1.6% |
| context | BF16 | 128 | 1 | 4096 | CSA 1024 | 2CTA | 1388.79 | 1385.57
| 1306.03 | 1344.45 | 1.063x (T=6) | 6.8% * |
| context | BF16 | 64 | 1 | 1024 | CSA 512 | 1CTA keep, deferred |
142.62 | 148.70 | 142.69 | 142.45 | 1.001x (T=8) | 0.1% |
| context | BF16 | 64 | 1 | 4096 | CSA 512 | 1CTA keep, deferred |
529.10 | 556.47 | 530.77 | 530.51 | 0.997x (T=8) | 4.1% * |

*DeepSeek-R1 dense MLA* (`BatchMLADecodePagedTSWrapper`, latent 512 +
RoPE 64, page 32, causal mask, random page table, Q/KV `0.5 * randn`,
BF16 output). Context rows are one request whose Q tokens are the last Q
positions of a KV-4096 sequence (chunked prefill for Q1024, full prefill
for Q4096). H128 is DP attention and H16 is TP8.

| phase | dtype | H | B | Q | KV len | kernel | T=0 (us) | T=8 (us) |
speedup | spread |
|---|---|---|---|---|---|---|---|---|---|---|
| gen | FP8 | 128 | 16 | 1 | 8192 | 2CTA split 4 | 31.04 | 30.72 |
1.010x | 0.3% |
| gen | FP8 | 128 | 64 | 1 | 8192 | 2CTA | 71.39 | 70.46 | 1.013x | 0.3%
|
| gen | FP8 | 128 | 128 | 1 | 8192 | 2CTA | 196.56 | 190.59 | 1.031x |
0.4% |
| gen | FP8 | 128 | 256 | 1 | 8192 | 2CTA | 411.26 | 395.74 | 1.039x |
2.6% * |
| gen | FP8 | 16 | 64 | 1 | 8192 | 2CTA | 69.50 | 69.34 | 1.002x | 0.2%
|
| gen | FP8 | 16 | 256 | 1 | 8192 | 1CTA | 224.10 | 222.32 | 1.008x |
0.2% |
| gen | BF16 | 128 | 16 | 1 | 8192 | 2CTA split 4 | 52.26 | 52.19 |
1.001x | 0.5% |
| gen | BF16 | 128 | 64 | 1 | 8192 | 2CTA | 136.93 | 136.35 | 1.004x |
0.8% |
| gen | BF16 | 128 | 128 | 1 | 8192 | 2CTA | 277.52 | 275.44 | 1.008x |
15.3% * |
| gen | BF16 | 128 | 256 | 1 | 8192 | 2CTA | 583.31 | 571.09 | 1.021x |
4.0% * |
| gen | BF16 | 16 | 64 | 1 | 8192 | 2CTA | 134.47 | 134.30 | 1.001x |
0.2% |
| gen | BF16 | 16 | 256 | 1 | 8192 | 1CTA | 462.35 | 461.31 | 1.002x |
0.1% |
| context | FP8 | 128 | 1 | 1024 | 4096 | 2CTA | 588.37 | 560.14 |
1.050x | 1.4% |
| context | FP8 | 128 | 1 | 4096 | 4096 | 2CTA | 1531.15 | 1448.58 |
1.057x | 8.0% * |
| context | FP8 | 16 | 1 | 1024 | 4096 | 2CTA | 93.28 | 89.94 | 1.037x |
0.4% |
| context | FP8 | 16 | 1 | 4096 | 4096 | 2CTA | 197.41 | 189.41 | 1.042x
| 0.2% |
| context | BF16 | 128 | 1 | 1024 | 4096 | 2CTA | 724.85 | 724.61 |
1.000x | 10.5% * |
| context | BF16 | 128 | 1 | 4096 | 4096 | 2CTA | 1875.76 | 1813.86 |
1.034x | 7.7% * |
| context | BF16 | 16 | 1 | 1024 | 4096 | 2CTA | 95.50 | 92.67 | 1.031x
| 40.2% * |
| context | BF16 | 16 | 1 | 4096 | 4096 | 2CTA | 210.90 | 205.07 |
1.028x | 10.9% * |


How the gain scales: it grows with work per CTA (larger batch, longer Q
or more selected slots), where the per-tile O rescale is a larger share
of the softmax/correction critical path. H16 generation and small grids
gain little. Random inputs raise the row maximum by tiny steps on most
tiles, so T=0 rescales often; real activations may skip more or less
often.

<details><summary>Benchmark script (R1 dense and DSV4 sparse)</summary>

```python
"""Rescale-threshold timing on DeepSeek-R1 dense MLA and DSV4 sparse MLA shapes.

usage: bench_models.py <workers> <rounds> <spec> [<spec> ...]
  dense  spec = d:<B>:<Q>:<H>:<K>:<dtype>        (latent 512 + RoPE 64, page 32, causal;
                                                  Q query tokens per request at the end of K)
  sparse spec = s:<B>:<Q>:<H>:<extra>:<dtype>    (D512, primary = SWA window 128, plus
                                                  <extra> compressed slots; extra 0 = SWA only)
Variants: dense 0 / 8; sparse FP8 None / 8; sparse BF16 None / 0 / 6 / 8.
Compilation is CPU-bound, so <workers> processes plan their shapes concurrently;
every worker then waits at a barrier, so timing starts only after all
compilation and input setup, and a shared lock times one process at a time. Each round times
every variant once (CUPTI median of 100 iterations after 20 warmups; 200/50 for
gen shapes) in rotated order. Prints
kind,phase,B,Q,H,K_or_extra,dtype,variant,schedule,median_us,sd_us,min_us,max_us.
"""

import multiprocessing as mp
import statistics
import sys
import time
import traceback

DENSE_VARIANTS = {"fp8": (0.0, 8.0), "bf16": (0.0, 8.0)}
SPARSE_VARIANTS = {"fp8": (None, 8.0), "bf16": (None, 0.0, 6.0, 8.0)}
PAGE, D_QK, POOL_ROWS, SWA = 32, 576, 65536, 128


def dense_runs(spec, torch, dev):
    from flashinfer.attention.prims_ts import BatchMLADecodePagedTSWrapper, MLAAttentionTuning

    _, b, q_len, h, k, dname = spec.split(":")
    b, q_len, h, k = int(b), int(q_len), int(h), int(k)
    dtype = {"fp8": torch.float8_e4m3fn, "bf16": torch.bfloat16}[dname]
    g = torch.Generator(device=dev).manual_seed(0)
    pages = (k + PAGE - 1) // PAGE
    q = (torch.randn(b, q_len, h, D_QK, device=dev, generator=g) * 0.5).to(dtype)
    kv = (torch.randn(b * pages, PAGE, D_QK, device=dev, generator=g) * 0.5).to(dtype)
    bt = torch.randperm(b * pages, device=dev, generator=g).to(torch.int32).view(b, pages)
    sl = torch.full((b,), k, device=dev, dtype=torch.int32)
    out = torch.empty(b, q_len, h, 512, device=dev, dtype=torch.bfloat16)
    runs = {}
    for t in DENSE_VARIANTS[dname]:
        w = BatchMLADecodePagedTSWrapper()
        extra = {"tuning": MLAAttentionTuning(softmax_rescale_threshold_log2=t)} if t > 0 else {}
        w.plan(dev, b, h, 512, 64, PAGE, k, max_seq_len_q=q_len, packed_query=False,
               q_data_type=dtype, kv_data_type=dtype, o_data_type=torch.bfloat16,
               mask_type="causal", **extra)
        pol = dict(w._plan_state.policy)

        def fn(w=w):
            w.run(q, kv, bt, sl, bmm1_scale=1.0 / D_QK**0.5, out=out, validate=False)

        runs[t] = (fn, f"{pol['kernel']}/split{pol['split_kv']}")
    keep = (q, kv, bt, sl, out)
    return ("dense", b, q_len, h, k, dname), runs, keep


def sparse_runs(spec, torch, dev):
    sys.path.insert(0, "tests/attention")
    from test_attention_ts_sparse_mla import prepare_sparse_mla_indices

    from flashinfer.attention.prims_ts import BatchSparseMLADecodePagedTSWrapper, MLAAttentionTuning
    from flashinfer.attention.prims_ts.mla_decode import _resolve_sparse_mla_plan

    _, b, q_len, h, extra, dname = spec.split(":")
    b, q_len, h, extra = int(b), int(q_len), int(h), int(extra)
    dtype = {"fp8": torch.float8_e4m3fn, "bf16": torch.bfloat16}[dname]
    torch.manual_seed(0)
    q = (torch.randn(b, q_len, h, 512, device=dev) * 0.15).to(dtype)
    swa = (torch.randn(POOL_ROWS, 1, 512, device=dev) * 0.15).to(dtype)
    si = torch.randint(0, POOL_ROWS, (b, q_len, SWA), device=dev, dtype=torch.int32)
    ckv = (torch.randn(POOL_ROWS, 1, 512, device=dev) * 0.15).to(dtype) if extra else None
    ci = (
        torch.randint(0, POOL_ROWS, (b, q_len, extra), device=dev, dtype=torch.int32)
        if extra
        else None
    )
    out = torch.empty(b, q_len, h, 512, device=dev, dtype=torch.bfloat16)
    runs = {}
    for t in SPARSE_VARIANTS[dname]:
        kwargs = dict(max_topk=SWA, max_extra_topk=extra, max_seq_len_q=q_len,
                      q_data_type=dtype, tuning=MLAAttentionTuning(softmax_rescale_threshold_log2=t))
        w = BatchSparseMLADecodePagedTSWrapper()
        w.plan(dev, b, h, **kwargs)
        _, p, *_ = _resolve_sparse_mla_plan(dev, b, h, **kwargs)
        meta = prepare_sparse_mla_indices(w, q, swa, si, extra_kv_cache=ckv, extra_indices=ci)

        def fn(w=w, meta=meta):
            w.run(q, swa, **meta, extra_kv_cache=ckv, out=out, validate=False)

        sched = f"{p.family}/split{p.split_kv}" + ("/deferred" if p.defer_max_update else "")
        runs[t] = (fn, sched)
    keep = (q, swa, si, ckv, ci, out)
    return ("sparse", b, q_len, h, extra, dname), runs, keep


def worker(specs, rounds, lock, barrier, queue):
    import torch

    from flashinfer.testing import bench_gpu_time

    dev = torch.device("cuda")
    built = []
    # Phase 1: compile and build inputs for every shape. No timing runs until
    # every worker has finished, so no other process touches the GPU then.
    for spec in specs:
        try:
            t0 = time.time()
            key, runs, keep = (dense_runs if spec[0] == "d" else sparse_runs)(spec, torch, dev)
            for fn, _ in runs.values():
                fn()
            torch.cuda.synchronize()
            built.append((spec, key, runs, keep))
            queue.put(f"# {spec} compile {time.time() - t0:.0f}s")
        except Exception:
            queue.put(f"# {spec} FAILED " + traceback.format_exc().replace("\n", " | ")[-600:])
    barrier.wait()
    # Phase 2: timing, one process at a time.
    for spec, key, runs, keep in built:
        gen = key[2] == 1
        warm, iters = (50, 200) if gen else (20, 100)
        meds = {v: [] for v in runs}
        order = list(runs)
        with lock:
            for r in range(rounds):
                for v in order[r % len(order):] + order[: r % len(order)]:
                    t = bench_gpu_time(runs[v][0], enable_cupti=True,
                                       dry_run_iters=warm, repeat_iters=iters)
                    meds[v].append(statistics.median(t) * 1e3)
        kind, b, q_len, h, k, dname = key
        for v in order:
            m = meds[v]
            queue.put(
                f"{kind},{'gen' if gen else 'ctx'},{b},{q_len},{h},{k},{dname},{v},"
                f"{runs[v][1]},{statistics.median(m):.2f},{statistics.pstdev(m):.3f},"
                f"{min(m):.2f},{max(m):.2f}"
            )
    queue.put(None)


def main():
    workers, rounds, specs = int(sys.argv[1]), int(sys.argv[2]), sys.argv[3:]
    print("kind,phase,B,Q,H,K_or_extra,dtype,variant,schedule,"
          "median_us,sd_us,min_us,max_us", flush=True)
    ctx = mp.get_context("spawn")
    lock, queue = ctx.Lock(), ctx.Queue()
    shards = [s for s in (specs[i::workers] for i in range(workers)) if s]
    barrier = ctx.Barrier(len(shards))
    procs = [
        ctx.Process(target=worker, args=(s, rounds, lock, barrier, queue)) for s in shards
    ]
    for p in procs:
        p.start()
    done = 0
    while done < len(procs):
        line = queue.get()
        if line is None:
            done += 1
        else:
            print(line, flush=True)
    for p in procs:
        p.join()


if __name__ == "__main__":
    main()
```

Run from the repository root (the sparse path imports the test's index
preparer):

`python bench_models.py 12 5 d:16:1:128:8192:fp8 d:64:1:128:8192:fp8
d:128:1:128:8192:fp8 d:256:1:128:8192:fp8 d:64:1:16:8192:fp8
d:256:1:16:8192:fp8 d:1:1024:128:4096:fp8 d:1:4096:128:4096:fp8
d:1:1024:16:4096:fp8 d:1:4096:16:4096:fp8 s:16:1:128:1024:fp8
s:16:1:64:512:fp8 s:64:1:128:1024:fp8 s:64:1:64:512:fp8
s:128:1:128:1024:fp8 s:128:1:64:512:fp8 s:256:1:128:1024:fp8
s:256:1:64:512:fp8 s:64:1:128:512:fp8 s:256:1:128:512:fp8
s:1:1024:128:1024:fp8 s:1:1024:64:512:fp8 s:1:4096:128:1024:fp8
s:1:4096:64:512:fp8 d:16:1:128:8192:bf16 d:64:1:128:8192:bf16
d:128:1:128:8192:bf16 d:256:1:128:8192:bf16 d:64:1:16:8192:bf16
d:256:1:16:8192:bf16 d:1:1024:128:4096:bf16 d:1:4096:128:4096:bf16
d:1:1024:16:4096:bf16 d:1:4096:16:4096:bf16 s:16:1:128:1024:bf16
s:16:1:64:512:bf16 s:64:1:128:1024:bf16 s:64:1:64:512:bf16
s:128:1:128:1024:bf16 s:128:1:64:512:bf16 s:256:1:128:1024:bf16
s:256:1:64:512:bf16 s:64:1:128:512:bf16 s:256:1:128:512:bf16
s:1:1024:128:1024:bf16 s:1:1024:64:512:bf16 s:1:4096:128:1024:bf16
s:1:4096:64:512:bf16`

</details>

**Accuracy** (relative L2 against FP32 attention on the same stored
inputs; FP8; public wrapper; measured at b3d9cb20c on a GB100 bring-up
board, which is fine for numerics).
- **Random data.** Latent Q/K are `0.5 * randn`.
- **Sink + tail g.** Token 0 sits `g` nats above the other keys and has
V = 0, so the output is the tail's weighted V.
- **Split-KV.** The loss covers the KV range that shares the sink's
split. Without split-KV (`split 1`, typical at large batch) it covers
the whole row.
- T=8 uses the trtllm-gen scale 1.75 (`448 * 2**-8`); smaller T keeps
more precision.

| shape | pattern | T=0 | T=1 | T=2 | T=4 | T=8 |
|---|---|---|---|---|---|---|
| 2CTA H128 B64 K4096 (split 1) | random | 2.20% | 2.24% | 2.24% | 2.24%
| 2.24% |
| | sink + tail 4 nats | 2.28% | 2.28% | 2.28% | 2.28% | 2.28% |
| | sink + tail 6 nats | 2.27% | 2.27% | 2.27% | 2.27% | 10.4% |
| | sink + tail 8 nats | 2.24% | 2.24% | 2.24% | 4.76% | 87.2% |
| | sink + tail 10.5 nats | 4.28% | 8.54% | 18.6% | 82.8% | 100% |
| 2CTA H128 B8 K4096 (split 8) | sink + tail 6 nats | 2.23% | - | 2.25%
| 2.25% | 4.17% |
| | sink + tail 8 nats | 2.23% | - | 2.25% | 2.69% | 30.1% |
| 1CTA H64 B128 K4096 (split 1) | sink + tail 6 nats | 2.27% | - | 2.27%
| 2.27% | 10.4% |
| | sink + tail 8 nats | 2.24% | - | 2.24% | 4.77% | 87.2% |
| 1CTA H16 B128 K4096 (split 1) | sink + tail 6 nats | 2.24% | - | 2.26%
| 2.26% | 7.45% |
| | sink + tail 8 nats | 2.23% | - | 2.25% | 3.73% | 60.4% |

BF16 P is not scaled; an earlier run measured BF16 at 0.26% for T=0 and
T=8 on every pattern.

**Why the sink case degrades.** At scale `448 * 2**-T`, E4M3 P loses
mantissa bits from about `10.3 - 0.69 * T` nats below the anchor and
flushes to zero below about `13 - 0.69 * T` nats (4.7 and 7.5 at T=8).
The FP32 row sum keeps the exact values, so the tail's weight is biased
low.

<details><summary>Accuracy script (public wrapper only)</summary>

```python
"""Accuracy of PrimTS MLA decode vs exact FP32 attention for several softmax rescale thresholds.

Patterns per (dtype, heads):
  random: latent Q/K ~ 0.5*randn (benchmark-like, nearly flat attention)
  sink<g>: token 0 of every request is an attention sink g nats above a long tail
           (RoPE channels carry the gap; V of the sink is zero, the tail's V is random)
Reports relative L2 error of the kernel output vs FP32 attention on the stored
(dtype-rounded) inputs.

usage: accuracy_probe.py <fp8|bf16> <heads> <batch> <kv_len> <gaps,comma> <thresholds,comma>
(prints CSV rows)
"""

import sys

import torch

from flashinfer.attention.prims_ts import BatchMLADecodePagedTSWrapper, MLAAttentionTuning

PAGE, LATENT, ROPE = 32, 512, 64
SCALE = 1.0 / 24.0


def make(batch, heads, kv_len, dtype, pattern, seed=0):
    g = torch.Generator(device="cuda").manual_seed(seed)
    pages = (kv_len + PAGE - 1) // PAGE
    q = torch.randn(batch, 1, heads, LATENT + ROPE, device="cuda", generator=g) * 0.5
    kv = torch.randn(batch * pages, PAGE, LATENT + ROPE, device="cuda", generator=g) * 0.5
    if pattern.startswith("sink"):
        gap = float(pattern[4:])
        q[..., LATENT:] = 1.0
        kv[..., LATENT:] = 0.0
        # token 0 of each request: rope . q_rope = 64 * a, logit gap = 64 * a * SCALE
        first_pages = torch.arange(batch, device="cuda") * pages
        kv[first_pages, 0, LATENT:] = gap / (64.0 * SCALE)
        kv[first_pages, 0, :LATENT] = 0.0
    bt = torch.arange(batch * pages, device="cuda", dtype=torch.int32).view(batch, pages)
    sl = torch.full((batch,), kv_len, device="cuda", dtype=torch.int32)
    return q.to(dtype), kv.to(dtype), bt, sl


def exact(q, kv, bt, sl):
    out = []
    for b in range(q.shape[0]):
        keys = kv[bt[b].long()].reshape(-1, kv.shape[-1])[: int(sl[b])].float()
        logits = q[b, 0].float() @ keys.T * SCALE
        p = torch.softmax(logits, dim=-1)
        out.append(p @ keys[:, :LATENT])
    return torch.stack(out)  # [B, H, 512]


def run(q, kv, bt, sl, dtype, heads, kv_len, threshold, want_split=False):
    w = BatchMLADecodePagedTSWrapper()
    extra = {"tuning": MLAAttentionTuning(softmax_rescale_threshold_log2=threshold)} if threshold > 0 else {}
    w.plan(torch.device("cuda"), q.shape[0], heads, LATENT, ROPE, PAGE, kv_len,
           max_seq_len_q=1, packed_query=False, q_data_type=dtype, kv_data_type=dtype,
           o_data_type=torch.bfloat16, mask_type="causal", **extra)
    out = w.run(q, kv, bt, sl, bmm1_scale=SCALE, validate=False)
    pol = dict(w._plan_state.policy)
    return out[:, 0].float(), f"{pol['kernel']}/split{pol['split_kv']}"


def main():
    # argv: dtype heads batch kv_len gaps(comma) thresholds(comma)
    dname, heads, batch, kv_len = sys.argv[1], int(sys.argv[2]), int(sys.argv[3]), int(sys.argv[4])
    gaps = sys.argv[5].split(","); ts = [float(t) for t in sys.argv[6].split(",")]
    dtype = {"fp8": torch.float8_e4m3fn, "bf16": torch.bfloat16}[dname]
    for g in gaps:
        pattern = "random" if g == "random" else f"sink{g}"
        q, kv, bt, sl = make(batch, heads, kv_len, dtype, pattern)
        ref = exact(q, kv, bt, sl)
        for t in ts:
            out, kernel = run(q, kv, bt, sl, dtype, heads, kv_len, t)
            err = (out - ref).norm() / ref.norm()
            print(f"{dname},H{heads},B{batch},K{kv_len},{pattern},T={t:g},{kernel},{err:.4e}", flush=True)


if __name__ == "__main__":
    sys.exit(main())
```

Each table row is `python accuracy_probe.py fp8 <H> <B> <K> <gaps>
<thresholds>` (for example `random,4,6,8,10.5 0,1,2,4,8`).

</details>

## 🔍 Related Issues

Experimental PrimTS API tracking: #5082 and #5229. Reuses the PrimTS
FMHA decode option `softmax_rescale_threshold_log2`
(`fmha_decode_config.py`, `block_sparse.py`) and its `448 * 2**-T` FP8 P
scale; bounds follow the trtllm-gen FMHA `skipCorrThreshold`
(TensorRT-LLM `FmhaOptions.h::checkSkipCorrThreshold`,
`KernelConfigBase.h::getSoftmaxPScale`). The FMHA decode option allows
0-8 for every P dtype and defaults to 8; this MLA option defaults to 0
(dense) / `None` (sparse) and allows up to 32 for BF16, as trtllm-gen
does.

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

New tests in `tests/attention/test_attention_ts_mla_decode.py`:
- `test_attention_ts_mla_decode_softmax_rescale_threshold` (5 cases:
2CTA and 1CTA, BF16 and FP8, T=8): against the protocol oracle, the
exact plan and the one-shot entry point. For FP8 it also checks that the
output is much closer to a freezing oracle than to one that re-anchors
on every new maximum, so an ignored threshold fails; this is required
for the 2CTA case and an unsplit 1CTA case (B128 H16).
- `..._softmax_rescale_threshold_reanchors_when_max_jumps` (6 cases:
2CTA, 1CTA, 1CTA keeps-MMA-AB; BF16 and FP8): spiked late keys raise the
maximum by more than a small `T` after earlier tiles froze, forcing the
re-anchor path; compared against the oracle and the T=0 kernel.
- `..._wrapper_trace_names_softmax_rescale_threshold_log2`: CPU-only
trace naming.

New tests in `tests/attention/test_attention_ts_sparse_mla.py`:
- `test_softmax_rescale_threshold_log2` (BF16 and FP8): with
`softmax_scale = ln 2`, successive 256-slot groups raise the maximum by
T-2, then above T, then T-2 again. Checks the output against FP64
attention with sinks (FP8 bound derived for the `448 * 2**-T` scale),
the LSE, that the one-shot helper matches the wrapper bitwise, and that
exactly one of the explicit plans (`0.0` or `T`) reproduces the `None`
default, so an explicit value always replaces the schedule default.
- `test_softmax_rescale_threshold_log2_rejected`: FP8 above 8 and a
negative value.

Local results at b3d9cb20c (GB100 bring-up boards, CC 10.0, 148 SMs):
- `tests/attention/test_attention_ts_mla_decode.py -k "rescale or
compile_oriented or frozen_state or trace"`: 15 of 16 passed on board
2u2g-spr-0085. That board rejects the remaining `1cta-fp8-t8` launch
with `cudaErrorInvalidClusterSize` for T=0 as well (split-KV 17 cluster
reduction), so that is the board, not this change; the case passes on
another board (2u2g-spr-0424).
- `tests/attention/test_attention_ts_sparse_mla.py -k
rescale_threshold`: 4 passed. The 98 existing sparse tests passed in a
full run at fd08ffa83; the default (`None`) path is unchanged since.
- `tests/trace`: same failure set as main (81 environment-only nvcc/CCCL
JIT failures on both; 1688 passed).

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5082 (and #5229). It adds a keyword-only,
backward-compatible `tuning` option (`MLAAttentionTuning`) to the
existing PrimTS MLA decode `plan()` / one-shot API.
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_experimental_api.py
```

## Reviewer Notes

- **Real coverage.** The experimental lane target follows earlier PrimTS
PRs (#6774). The real coverage is
`tests/attention/test_attention_ts_mla_decode.py` and
`tests/attention/test_attention_ts_sparse_mla.py` on SM100 in the normal
lane.
- **Register and SASS evidence (measured on the earlier fixed-1.75
revision, whose T=0 and T=8 kernels are the same as the final
version's).** The six kernels checked are FP8 and BF16 `throughput_2cta`
(B64 H128), 1CTA swaps (B32 H32) and 1CTA keeps (B128 H64), each FP8 and
BF16.
  - At T=0, their SASS is identical to main.
  - At T=8, their REG/STACK and STL/LDL counts equal T=0.
- Reproduce by planning the same shape on both trees with
`CUTE_DSL_KEEP=cubin CUTE_DSL_DUMP_DIR=<dir>`, then diffing `cuobjdump
-sass` output with the encodings stripped.
- **Attention sinks.** The sparse API passes sinks; the sink paths use
the selected P scale, and the new sparse test runs with sinks, including
a sink above every logit.
- **Older 1CTA option.** The 1CTA sparse path's fixed 6-binade
`defer_sparse_max_update` (#5434) stays the sparse default; an explicit
threshold turns it off and takes its place. Folding the deferral into
this threshold (`T=6` by default on those schedules) would remove one
softmax branch but changes the default sparse compile identity, so it is
left as follow-up.
- **Tuning struct vs. FMHA.** Per review, the knob is passed as
`MLAAttentionTuning` rather than a flat kwarg. The PrimTS FMHA
`block_sparse.plan` still takes `softmax_rescale_threshold_log2` as a
flat kwarg (default 8); aligning it is left as follow-up. Wrapper traces
name a nonzero threshold (`_rescale_thr<T>`); the one-shot trace does
not record tuning.
- **Compiled kernels.** Each distinct nonzero threshold compiles its own
kernel; a deployment normally uses one value. The new GPU tests add 11
dense and 4 sparse parametrizations.
- **With #7019.** The FP8 page-ID prefetch PR #7019 removes a larger
K-loader stall, which otherwise masks part of this gain. With both
applied (earlier revision, T=8), FP8 2CTA is 1.019-1.035x faster than
with #7019 alone; for example, B128 K8192 goes from 134.56 to 129.95 us
and B256 K4096 from 141.31 to 137.09 us.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional softmax rescaling threshold for dense and sparse MLA
decode, with dtype-specific supported ranges. The default preserves
exact rescaling; positive values can defer rescaling and adjust FP8
probability scaling.
* Added threshold selection to MLA benchmark runs and included the
setting in benchmark results.
* **Documentation**
* Documented threshold behavior, supported limits, FP8 precision
considerations, and dense versus sparse attention API limitations.
* **Tests**
* Added coverage for threshold behavior, supported values, and FP8/BF16
results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [966dcfd](https://github.com/flashinfer-ai/flashinfer/commit/966dcfd6b66323bb64fd5fb4cb6979fdc02252c0)

- **作者**: eigen
- **时间**: 2026-10-26T17:13:06Z
- **提交信息**: fix(cake_nvfp4_attention): add the async-proxy fences before the SM120 attention TMA stores (#7430)

This Cake attention kernel family has three variants. All three do dense
non-causal MHA with D = 128, take BF16 in, give BF16 out and use FP32
softmax. They accept any strides (NHD or HND views). Each variant is one
call that runs a chain of statistics, quantization and attention
kernels. Two variants, NVFP4 QK + NVFP4 PV on SM100 / SM103 and INT8 QK
+ NVFP4 PV on SM120, are in `flashinfer/experimental/nvfp4_attention`.
The third, INT8 QK + FP8 E4M3 PV on SM90, is in
`flashinfer/experimental/cake_fp8_attention`. This PR changes only the
SM120 attention kernel of the already shipped
`flashinfer/experimental/nvfp4_attention` package. The API stays the
same, `flashinfer.prefill.prepare_nvfp4_attention(q, k, v, out,
backend="cake")` and `nvfp4_attention_workspace_bytes`, and the SM100 /
SM103 kernels are unchanged. The change is a correctness fix that adds
the required asynchronous-proxy fences between the kernel's
shared-memory writes and the TMA reads that follow them. The fix costs a
little time. We measured the complete BF16-in / BF16-out call under
CUDA-graph replay against the previous Cake version, currently on
FlashInfer main. Both sides ran the same script in the same session on
the same GPU. Against that version, this PR is 0.97x–0.98x on every row
R1–R7 on both layouts, about 3 % slower.

**NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a), CUDA 13.0
runtime, kernels JIT-compiled with CUDA 13.4: this PR vs the previous
Cake version, D = 128**

*HND layout*

| Shape | Batch | Seq len | Heads | Cake, this PR (ms) | Cake, previous
version (ms) | Speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|---:|
| R1 | 1 | 4800 | 40 | 1.0324 | 1.0072 | 0.98x |
| R2 | 1 | 32760 | 40 | 33.1919 | 32.2172 | 0.97x |
| R3 | 1 | 75600 | 40 | 170.0287 | 165.2497 | 0.97x |
| R4 | 1 | 32760 | 5 | 4.2230 | 4.0982 | 0.97x |
| R5 | 1 | 75600 | 5 | 21.4896 | 20.8760 | 0.97x |
| R6 | 2 | 32760 | 40 | 66.2292 | 64.3272 | 0.97x |
| R7 | 1 | 32760 | 12 | 10.2136 | 9.9059 | 0.97x |

*NHD layout*

| Shape | Batch | Seq len | Heads | Cake, this PR (ms) | Cake, previous
version (ms) | Speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|---:|
| R1 | 1 | 4800 | 40 | 1.0375 | 1.0118 | 0.98x |
| R2 | 1 | 32760 | 40 | 33.2706 | 32.2793 | 0.97x |
| R3 | 1 | 75600 | 40 | 170.1429 | 165.5841 | 0.97x |
| R4 | 1 | 32760 | 5 | 4.2252 | 4.0990 | 0.97x |
| R5 | 1 | 75600 | 5 | 21.5166 | 20.8599 | 0.97x |
| R6 | 2 | 32760 | 40 | 66.2459 | 64.3838 | 0.97x |
| R7 | 1 | 32760 | 12 | 10.2196 | 9.9096 | 0.97x |

The other Cake variants are NVFP4 QK + NVFP4 PV on SM100 / SM103, in the
same package, and INT8 QK + FP8 E4M3 PV on SM90
(`flashinfer/experimental/cake_fp8_attention`). This PR leaves both
unchanged, and the family ships on sm_90a, sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated NVFP4 attention execution on supported hardware. The change
affects synchronization during attention calculations; no changes to
public interfaces or listed library support requirements were reported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b92f112](https://github.com/flashinfer-ai/flashinfer/commit/b92f1129554c2dfc5c9c993867ddc50f4b6aedd5)

- **作者**: danisereb
- **时间**: 2026-10-26T16:45:09Z
- **提交信息**: feat(moe): MXFP8 x MXFP8 mode for the CuTe-DSL fused MoE (for Nemotron models) (#6793)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds `quant_mode="mxfp8"` (E4M3 weights and activations, E8M0 block-32
scales) to `cute_dsl_fused_moe` on
SM100/SM103. It reuses the W4A8 kernels with an FP8 B operand. It is
also wired into the unified MoE API
(`QuantConfig(MXFP8, MXFP8)` with `CuteDslConfig`) and the `unified_moe`
benchmark.

**Why CuTe-DSL:** new activations are simple to add to this kernel, and
they are planned for future Nemotron models.

**Changes**
- MXFP8 weight dtype through `_moe_core_impl` and the tuner.
- `convert_row_major_sf_to_mma_layout` for checkpoint scales.
- Unified-API runner, weight and activation preparers.
- Tuner fix: GEMM2 K for unpacked weights.
- Benchmark: `trtllm` and `cute_dsl` backends; pass the runner launch
state.
- GEMM1 N=192 tiles for non-gated activations, only when the
intermediate size is a multiple of 192 (separate commit).

This PR was tested with Nemotron 3.5 Super (non-gated ReLU² MoE), end to
end in vLLM and with unit tests on synthetic ReLU² shapes. Gated
activations (SwiGLU, GeGLUTanh) run on the same kernels as W4A8 and
should work, but are not yet tested with MXFP8 weights; SiTU is not
supported.

### Where CuTe-DSL wins

1. **Large MoE calls (>= 2k tokens per call): 13-21% faster than TRT-LLM
MXFP8** (GB200, Super 3.5 MoE shape,
table below). Its 128/256-row tiles (2-CTA at 256) and fused GEMM2
finalize pay off once each expert gets
enough rows. TRT-LLM stays faster below ~1k tokens: it pads each
expert's tokens to 8-64-row tiles, while
   CuTe-DSL pads to 128.
2. **Expert parallelism (EP >= 16): faster than TRT-LLM at every batch
size, 4-47%** (one GPU = one EP rank,
dispatched tokens; table below). At large batch (>= 2048 rows/expert)
both use 128/256-row tiles: a kernel win.
At small batch part of the gap is TRT-LLM's tile heuristic, which
estimates rows/expert from all routes
(incl. other ranks' experts) and so picks 128-row tiles at EP32-64 even
for 8 rows/expert (8-row tile at EP1).
3. **GEMM1 N=192 tiles: -3% to -14% MoE latency at 4k-16k tokens.**
GEMM1 has no partial-N
tile, so for expert width 2688 (not a multiple of 256) only N=128 was
valid: 21 column tiles, each re-gathering
the same token rows. 2688 = 14 x 192, so N=192 needs 14 tiles: 1/3 less
activation traffic. Non-gated
activations only, offered to the autotuner only when the width divides
by 192; gated modes are unchanged.

### Kernel: MXFP8 MoE on GB200

MoE layer of `nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A12B-BF16`:
hidden (latent) 1024, intermediate 2688,
512 experts (all on one GPU), top-22, ReLU2. One GB200.
`flashinfer_benchmark.py --routine unified_moe --quant-variant mxfp8`:
checked against a BF16 reference.

Median latency in ms.

| tokens | CuTe-DSL (this PR) | TRT-LLM | CUTLASS | CuTe-DSL vs TRT-LLM
|
|---|---|---|---|---|
| 1 | 0.037 | **0.035** | 0.061 | +6% |
| 4 | 0.096 | **0.087** | 0.115 | +10% |
| 16 | 0.332 | **0.287** | 0.335 | +16% |
| 64 | 0.492 | **0.416** | 0.480 | +18% |
| 256 | 0.482 | **0.429** | 0.540 | +12% |
| 1024 | 0.520 | **0.475** | 0.757 | +9% |
| 2048 | **0.529** | 0.611 | 1.053 | **-13%** |
| 4096 | **0.769** | 0.973 | 1.801 | **-21%** |
| 8192 | **1.327** | 1.587 | 3.213 | **-16%** |
| 16384 | **2.136** | 2.712 | 6.146 | **-21%** |

**Expert parallelism.** One GPU modelled as one EP rank: 512/EP local
experts, tokens dispatched to the rank
(routes to other ranks' experts keep their global ids), uniform top-22
routing; both backends autotuned per
shape, 5 paired rounds (CuTe-DSL won 5/5 at every point below 1.0).

CuTe-DSL time / TRT-LLM time:

| rows per local expert | 8 | 32 | 128 | 512 | 2048 | 8192 |
|---|---|---|---|---|---|---|
| EP1 (512 experts/GPU) | 1.10 | 1.15 | 0.93 | 0.79 | 0.82 | |
| EP8 (64) | 1.05 | 0.96 | 0.85 | 0.70 | 0.64 | |
| EP16 (32) | 0.96 | 0.90 | 0.83 | 0.66 | 0.60 | |
| EP32 (16) | 0.83 | 0.76 | 0.82 | 0.71 | 0.58 | |
| EP64 (8) | 0.75 | 0.76 | 0.80 | 0.63 | 0.62 | 0.53 |

Skewed routing (expert popularity ~ rank^-0.5, hottest rank): same
pattern; TRT-LLM ahead only at EP1-8 with 8-32
rows per expert. Empty cells exceed 64k tokens per call.

GEMM1 N=192 vs N=128 only. Paired, interleaved, 2 GPUs x 2 seeds, 6
rounds each:

| tokens | latency change | rounds won |
|---|---|---|
| 2048 | +2% to +3.5% (autotuner keeps N=128) | 3/24 |
| 4096 | -7% to -13% | 24/24 |
| 8192 | -3% to -9% | 23/24 |
| 16384 | -9% to -14% | 20/24 |

### End to end: vLLM,
`nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A12B-BF16`

**Setup**

Hardware and parallelism:
- 4x GB200, one node (NVLink).
- TP4/EP4 (`--tensor-parallel-size 4 --enable-expert-parallel`): 128 of
the 512 experts per GPU.
- Plain TP4 is not supported by the CuTe-DSL path: 2688/4 = 672 is not a
multiple of 128.
- The BF16 model (~240 GB) does not fit on one GPU, so a single-GPU
baseline is not possible.

Models and backends:
- BF16: `nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A12B-BF16`. Default
MoE backend (FlashInfer TRT-LLM BF16).
- MXFP8: the same model with only the MoE quantized to MXFP8 (routed
experts of all MoE layers, ModelOpt);
  all other layers stay BF16.
  - `--moe-backend flashinfer_cutedsl` (using custom vLLM branch), or
  - the default MXFP8 backend (FlashInfer TRT-LLM).

Server: `vllm serve <model> --tensor-parallel-size 4
--enable-expert-parallel --language-model-only
--trust-remote-code --max-model-len 17408 --no-enable-prefix-caching
[--moe-backend flashinfer_cutedsl]`.
Chunked prefill is on (`max_num_batched_tokens` 16384) and CUDA graphs
use the defaults.

Client (example: the best point, concurrency 64; other points change
only `--max-concurrency` and
`--num-prompts` = 4 x concurrency):

```bash
vllm bench serve --model nvidia/NVIDIA-Nemotron-3.5-Super-VL-120B-A12B-BF16 --trust-remote-code \
    --dataset-name random --random-input-len 1024 --random-output-len 1024 --ignore-eos \
    --max-concurrency 64 --num-prompts 256 --seed 0
```

MXFP8 here means only the MoE is MXFP8 (all MoE layers); the rest of the
model is BF16.

**ISL/OSL 1024/1024, TP4/EP4, BF16 vs MXFP8 with the CuTe-DSL MoE (this
PR).** Output throughput in tok/s,
mean TPOT and TTFT in ms:

| concurrency | BF16 tok/s | MXFP8 tok/s | gain | TPOT BF16 / MXFP8 |
TTFT BF16 / MXFP8 |
|---|---|---|---|---|---|
| 1 | 256.5 | 246.1 | -4.1% | 3.86 / 4.02 | 44.5 / 44.6 |
| 4 | 795.0 | 876.9 | +10.3% | 4.92 / 4.43 | 119.0 / 136.3 |
| 16 | 2,120.0 | 2,260.6 | +6.6% | 7.34 / 6.84 | 215.0 / 249.5 |
| 64 | 5,598.3 | **6,796.8** | **+21.4%** | 11.00 / 8.86 | 446.5 / 567.3
|
| 128 | 9,100.1 | **10,580.2** | **+16.3%** | 13.40 / 11.47 | 681.3 /
645.4 |
| 256 | 13,238.7 | 13,035.0 | -1.5% | 17.72 / 18.08 | 1,631.2 / 1,577.4
|

### Accuracy (lm-eval against the vLLM server, greedy, prefix caching
off)

| | GSM8K 5-shot strict / flexible | HellaSwag acc_norm | MMLU-Pro
5-shot CoT |
|---|---|---|---|
| BF16 | 0.8491 / 0.9204 | 0.8728 | 0.7963 |
| MXFP8, TRT-LLM | 0.8544 / 0.9196 | 0.8738 | 0.7913 |
| MXFP8, CuTe-DSL (this PR) | 0.8461 / 0.9181 | 0.8726 | 0.7924 |

Stderr: GSM8K ~0.010 / 0.0075, HellaSwag 0.0033, MMLU-Pro 0.0036.
CuTe-DSL and TRT-LLM agree within
1 stderr on every eval.

**AI assistance was used in this PR.**

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

**Tests:** `tests/moe/test_cute_dsl_mxfp8_moe.py` (new, 10 tests). On
GB200, all pass together with the existing
CuTe-DSL MoE suite (`test_cute_dsl_fused_moe.py`: 703 passed),
`test_cute_dsl_moe_can_implement.py`,
`test_unified_moe_activation_matrix.py`, and the unified MoE, fuzz and
activation tests.

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

**Limits:** SM100/103 only, BF16 output, fused finalize only, no SiTU,
hidden and intermediate sizes
multiples of 128.

**GEMM1 N=192 is a separate commit and can be dropped.** It adds N=192
GEMM1 tactics for all non-gated
(ReLU2) modes, including W4A8; gated modes see no new tactics.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added MXFP8×MXFP8 support for fused Mixture-of-Experts workloads,
including weight preparation, activation packing, autotuning,
validation, and tracing.
  - Added TRTLLM and CuTe-DSL MXFP8 benchmark backends.
- Added support for non-gated ReLU² execution and GEMM1 configurations
using 192 intermediate tiles.
- Added conversion support for row-major scale factors into
MMA-compatible layouts.

- **Documentation**
- Updated MoE API documentation and supported activation/quantization
combinations for MXFP8.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Daniel Serebrenik <daserebrenik@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5240384](https://github.com/flashinfer-ai/flashinfer/commit/5240384d8f79887783622980490f022490138a7f)

- **作者**: Vincent
- **时间**: 2026-10-26T16:44:25Z
- **提交信息**: feat(moe): unfused (deterministic) finalize path for the Rubin CuTe DSL fused MoE (#6950)

## 📌 Description

The Rubin (SM107) CuTe DSL fused-MoE finalize grouped GEMM only
implemented the fused atomic scatter-add, so `cute_dsl_fused_moe(...,
use_fused_finalize=False)` raised `NotImplementedError` on SM107. SGLang
now defaults to the unfused finalize (sgl-project/sglang#40105) and its
`--enable-deterministic-inference` mode forces it, so the
`flashinfer_cutedsl` MoE runner failed at autotune warmup on every rank
on Rubin (Qwen3.5 NVFP4, 2x Vera Rubin NVL72).

This adds the unfused path to the SM107 finalize kernel, mirroring the
Blackwell kernel:

- `Sm107BlockScaledContiguousGroupedGemmFinalizeFusionKernel` takes
`use_fused_finalize` (default `True`). When `False`, the epilogue writes
each unscaled permuted row to its expanded `(token, top-k slot)` row
with a `cp.async.bulk` store instead of the bf16 atomic reduce into the
token row, and the output tensor is sized `num_tokens * top_k`. The
fused path is unchanged.
- The dispatcher passes the flag through instead of raising. The caller
already allocates the expanded output and runs the fixed-order
`moe_unpermute` reduction for any arch, so the deterministic contract of
#3976 now holds on SM107.
- The locality-domain (two-die) path remains fused-only, as before.
- The SM107 test skips for the unfused path are removed, so
`test_deterministic_finalize_numerical_accuracy` runs on Rubin.

Not changed: the SM107 kernel still has no PDL path, Float32-only router
scales and no per-token activation scale.

## Validation on Rubin (CUTLASS DSL 4.8)

- `tests/moe/test_cute_dsl_fused_moe.py`, deterministic-finalize /
route-tile-boundary / cluster-padding / wrapper accuracy / CUDA graph /
EP subsets: 106 passed, 0 failed. Remaining skips are the pre-existing
per-token-scale and custom-SwiGLU gaps.
- `tests/moe/test_cute_dsl_moe_can_implement.py`: 18 passed.
- NVFP4 SwiGLU, hidden 4096, intermediate 1536, 128 local experts, top-k
8, at 1 / 64 / 1024 tokens: the unfused output matches the float
reference within tolerance, is within one bf16 ulp of the fused output,
and is bit-identical across repeated runs (the fused output is not, as
expected for atomics).
- Whole-op time, unfused relative to fused, default tactic: 1.00x at 1
and 1024 tokens.

## 🔍 Related Issues

- #3976 (deterministic CuTe DSL NVFP4 finalize mode, Blackwell)
- sgl-project/sglang#40105

## 🚀 Pull Request Checklist

- [x] pre-commit hooks run
- [x] Existing tests cover the change (SM107 skips removed)

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for choosing fused or unfused finalization on Rubin
hardware. Unfused finalization preserves expanded token outputs, while
fused finalization combines scaled results into token outputs.
* **Bug Fixes**
* Corrected output handling across both finalization modes on Rubin
hardware.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [182159e](https://github.com/flashinfer-ai/flashinfer/commit/182159eb7af057b6ca37b9b4640d04809771d961)

- **作者**: eigen
- **时间**: 2026-10-26T15:12:28Z
- **提交信息**: perf(cake_warp_decode): fused route-pack FC1 with K512 MMA-U2 FC2 on more sm_103a rows, linear-grid FC2 for H3072 I384 (#7415)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens. It is called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), five activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR changes only
the per-row schedule selection. It adds and removes no kernel program:
every changed row runs programs that FlashInfer main already ships.

On sm_103a, 100 rows move to the fused route-pack FC1 and the K512
MMA-U2 device-workfeed FC2. The fused FC1 builds the route tables in its
prologue, which removes the separate route-pack launch. Each row keeps
the workfeed that we measured for it: 144 CTAs or one CTA per SM. Of
these rows, the 20 `e512_i1024_k10` rows also take the packed fixed
top-10 vector finalize program instead of the runtime-k scalar finalize.
It sums the routes in the same order with the same rounding, so the
output does not change. On each architecture, 24 `h3072_e256_i384_k8`
rows (8 and 10 to 32 tokens) move from the pool K256 FC2 program to the
linear-grid K256 FC2 program that the H4096 E512 rows already use. In
total, 124 rows change on sm_103a (100 + 24) and 24 rows change on
sm_100a. All changed geometries use SwiGLU. All other rows run the same
programs as FlashInfer main.

On every measured row, the outputs are bit-identical to the previous
version's. Against the previous Cake version on FlashInfer main, the
changed rows of each geometry run up to these speedups (memset flush /
read flush):

On sm_103a:

- `e60_i1536_k4`, 12 to 32 tokens (21 rows): 1.14x / 1.05x
- `e512_i1024_k10`, 6 to 25 tokens (20 rows): 1.13x / 1.04x
- `e256_i512_k8`, 16, 17, 19 to 29 and 32 tokens (14 rows): 1.12x /
1.02x
- `e128_i1536_k8`, 6 to 32 tokens (27 rows): 1.10x / 1.02x
- `e256_i1536_k8`, 15 to 32 tokens (18 rows): 1.04x / 1.02x
- `h3072_e256_i384_k8`, 8 and 10 to 32 tokens (24 rows): 1.04x / 1.03x

On sm_100a:

- `h3072_e256_i384_k8`, 8 and 10 to 32 tokens (24 rows): 1.03x / 1.02x

Every changed row is faster in both flush modes. In the tables, bold
`num_tokens` values mark the changed rows.

The "memset" and "read" column groups are two cold-L2 modes: before
every call, we flush L2 with a memset of a large buffer or a read of
one.

**sm_100a** (NVIDIA GB200, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows whose schedule this PR changes.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.98|14.03|1.003|12.58|12.55|0.997|
|2|19.21|18.99|0.989|16.93|16.73|0.988|
|3|22.58|22.76|1.008|19.20|19.26|1.003|
|4|26.47|26.37|0.996|21.62|21.79|1.008|
|5|30.41|30.56|1.005|24.77|24.70|0.997|
|6|33.78|33.72|0.998|26.78|26.82|1.001|
|7|36.78|36.56|0.994|29.21|29.38|1.006|
|8|39.70|39.80|1.002|31.53|31.64|1.004|
|9|42.99|42.88|0.997|33.89|34.05|1.005|
|10|46.26|46.27|1.000|36.71|36.53|0.995|
|11|49.23|49.35|1.002|39.18|39.30|1.003|
|12|52.42|52.52|1.002|41.71|41.82|1.002|
|13|55.66|55.41|0.996|44.03|44.10|1.002|
|14|58.92|58.86|0.999|46.60|46.45|0.997|
|15|62.03|61.85|0.997|49.15|49.14|1.000|
|16|65.57|65.47|0.999|51.98|51.90|0.999|
|17|67.71|67.74|1.000|53.74|53.88|1.003|
|18|70.25|70.39|1.002|56.17|56.20|1.001|
|19|72.33|72.30|1.000|57.90|57.97|1.001|
|20|71.52|71.55|1.000|57.30|57.21|0.998|
|21|71.53|71.61|1.001|57.30|57.27|0.999|
|22|71.63|71.49|0.998|57.30|57.41|1.002|
|23|71.52|71.57|1.001|57.44|57.33|0.998|
|24|71.54|71.49|0.999|57.30|57.28|1.000|
|25|71.63|71.67|1.001|57.52|57.42|0.998|
|26|71.74|71.82|1.001|57.50|57.37|0.998|
|27|71.54|71.77|1.003|57.59|57.42|0.997|
|28|71.80|71.83|1.000|57.62|57.46|0.997|
|29|71.72|71.65|0.999|57.60|57.51|0.998|
|30|71.74|71.74|1.000|57.40|57.49|1.002|
|31|71.71|71.64|0.999|57.57|57.46|0.998|
|32|72.70|72.67|1.000|58.38|58.36|1.000|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.84|16.72|0.993|15.56|15.61|1.003|
|2|22.34|22.41|1.003|20.22|20.34|1.006|
|3|26.29|26.25|0.998|23.81|23.78|0.999|
|4|31.83|31.77|0.998|28.69|28.88|1.007|
|5|36.30|36.22|0.998|32.72|32.86|1.004|
|6|41.19|41.15|0.999|37.57|37.43|0.996|
|7|46.07|46.10|1.001|41.50|41.68|1.004|
|8|50.47|50.70|1.004|45.41|45.76|1.008|
|9|55.79|55.85|1.001|50.68|50.64|0.999|
|10|60.13|60.18|1.001|54.58|54.44|0.997|
|11|65.14|65.14|1.000|59.06|59.36|1.005|
|12|69.58|69.90|1.005|62.90|63.27|1.006|
|13|74.34|74.38|1.001|67.43|67.70|1.004|
|14|79.19|79.14|0.999|71.54|71.59|1.001|
|15|83.86|83.81|0.999|76.74|76.19|0.993|
|16|88.33|88.39|1.001|80.14|79.90|0.997|
|17|92.91|93.19|1.003|84.28|84.26|1.000|
|18|97.65|97.45|0.998|88.46|88.59|1.001|
|19|101.96|101.84|0.999|92.72|92.92|1.002|
|20|106.49|106.52|1.000|96.77|96.64|0.999|
|21|111.05|111.00|1.000|100.79|101.39|1.006|
|22|115.74|115.75|1.000|105.26|105.02|0.998|
|23|119.88|119.82|1.000|109.01|109.12|1.001|
|24|124.46|124.46|1.000|113.07|113.34|1.002|
|25|129.09|129.13|1.000|117.70|117.32|0.997|
|26|133.62|133.51|0.999|121.73|121.86|1.001|
|27|137.99|138.01|1.000|125.64|125.70|1.000|
|28|142.06|142.13|1.000|129.99|130.15|1.001|
|29|146.63|146.75|1.001|134.09|134.06|1.000|
|30|151.23|151.14|0.999|138.17|138.09|0.999|
|31|155.65|155.56|0.999|142.21|142.06|0.999|
|32|160.03|160.02|1.000|146.32|145.98|0.998|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.25|14.30|1.004|13.41|13.32|0.993|
|2|16.56|16.62|1.004|15.31|15.23|0.995|
|3|19.45|19.54|1.005|18.02|17.98|0.997|
|4|23.04|22.90|0.994|20.68|20.90|1.010|
|5|25.32|25.25|0.997|23.01|23.15|1.006|
|6|27.71|27.62|0.997|25.22|25.42|1.008|
|7|30.52|30.45|0.998|27.68|27.67|1.000|
|8|33.38|33.21|0.995|30.34|30.48|1.004|
|9|36.20|36.09|0.997|32.89|33.06|1.005|
|10|38.56|38.62|1.002|35.26|35.28|1.001|
|11|41.17|41.15|1.000|37.62|37.66|1.001|
|12|43.75|43.66|0.998|40.34|40.32|1.000|
|13|46.38|46.54|1.003|42.61|42.67|1.002|
|14|48.98|48.86|0.998|45.30|45.39|1.002|
|15|51.63|51.62|1.000|47.80|47.73|0.998|
|16|53.76|53.98|1.004|50.10|49.89|0.996|
|17|56.45|56.31|0.998|52.48|52.38|0.998|
|18|59.14|58.97|0.997|54.92|54.89|0.999|
|19|61.58|61.62|1.001|57.34|57.06|0.995|
|20|63.87|63.86|1.000|59.16|59.46|1.005|
|21|66.19|66.30|1.002|61.78|61.74|0.999|
|22|69.10|69.10|1.000|64.33|64.54|1.003|
|23|71.61|71.52|0.999|66.79|66.78|1.000|
|24|74.12|73.87|0.997|69.04|68.73|0.995|
|25|76.36|76.28|0.999|71.41|71.82|1.006|
|26|78.86|78.96|1.001|73.78|73.60|0.998|
|27|81.34|81.25|0.999|76.28|76.22|0.999|
|28|83.67|83.65|1.000|78.78|78.28|0.994|
|29|86.53|86.07|0.995|81.40|80.82|0.993|
|30|88.70|88.67|1.000|83.01|82.89|0.999|
|31|91.43|91.21|0.998|85.69|85.66|1.000|
|32|93.33|93.44|1.001|87.90|88.14|1.003|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.31|16.51|1.012|14.76|14.65|0.992|
|2|21.98|21.82|0.993|19.89|19.95|1.003|
|3|25.32|25.30|0.999|22.87|22.78|0.996|
|4|29.30|29.34|1.002|26.47|26.43|0.998|
|5|34.34|34.42|1.002|30.87|30.75|0.996|
|6|38.63|38.65|1.000|34.56|34.54|0.999|
|7|42.98|43.03|1.001|38.18|38.27|1.002|
|8|47.01|47.02|1.000|41.91|42.28|1.009|
|9|51.55|51.66|1.002|45.78|45.89|1.002|
|10|55.55|55.58|1.000|49.62|49.54|0.998|
|11|59.51|59.58|1.001|53.28|53.21|0.999|
|12|63.43|63.40|0.999|56.94|56.82|0.998|
|13|67.63|67.65|1.000|60.38|60.38|1.000|
|14|71.36|71.42|1.001|64.04|64.14|1.001|
|15|75.36|75.31|0.999|67.74|67.82|1.001|
|16|75.33|75.28|0.999|67.71|67.69|1.000|
|17|75.32|75.50|1.002|67.93|67.65|0.996|
|18|75.34|75.37|1.000|67.87|67.74|0.998|
|19|75.43|75.45|1.000|67.78|67.77|1.000|
|20|75.46|75.52|1.001|67.78|67.82|1.001|
|21|75.31|75.43|1.002|67.88|67.86|1.000|
|22|75.27|75.43|1.002|67.81|67.68|0.998|
|23|75.33|75.38|1.001|67.90|67.86|0.999|
|24|75.26|75.38|1.002|67.75|67.86|1.002|
|25|75.62|75.64|1.000|67.90|67.84|0.999|
|26|75.65|75.74|1.001|67.98|67.91|0.999|
|27|75.53|75.68|1.002|67.93|67.99|1.001|
|28|75.41|75.60|1.003|67.86|67.87|1.000|
|29|75.63|75.58|0.999|67.86|67.98|1.002|
|30|75.66|75.66|1.000|67.82|68.05|1.003|
|31|75.59|75.61|1.000|67.93|67.95|1.000|
|32|75.58|75.58|1.000|67.90|67.95|1.001|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.10|14.10|1.000|13.18|13.09|0.993|
|2|16.75|16.74|1.000|15.33|15.34|1.001|
|3|19.46|19.39|0.997|17.57|17.67|1.006|
|4|21.94|21.90|0.998|20.06|19.97|0.995|
|5|24.33|24.32|1.000|22.23|22.21|0.999|
|6|26.77|26.69|0.997|24.12|24.14|1.001|
|7|29.23|29.29|1.002|26.26|26.26|1.000|
|**8**|31.51|30.78|0.977|28.37|27.98|0.986|
|9|33.58|33.46|0.996|30.30|30.27|0.999|
|**10**|35.89|35.38|0.986|32.31|31.90|0.987|
|**11**|38.12|37.38|0.980|34.55|33.84|0.979|
|**12**|40.26|39.32|0.977|36.42|35.67|0.980|
|**13**|42.26|41.30|0.977|38.14|37.50|0.983|
|**14**|44.43|43.38|0.976|40.30|39.56|0.982|
|**15**|46.47|45.38|0.976|42.16|41.37|0.981|
|**16**|46.57|45.32|0.973|42.22|41.30|0.978|
|**17**|46.72|45.47|0.973|42.33|41.56|0.982|
|**18**|46.63|45.54|0.976|42.33|41.56|0.982|
|**19**|46.78|45.58|0.974|42.40|41.64|0.982|
|**20**|46.78|45.54|0.973|42.39|41.58|0.981|
|**21**|46.74|45.52|0.974|42.39|41.58|0.981|
|**22**|46.64|45.50|0.975|42.36|41.57|0.981|
|**23**|46.65|45.59|0.977|42.40|41.68|0.983|
|**24**|46.63|45.47|0.975|42.26|41.59|0.984|
|**25**|47.01|45.68|0.972|42.68|41.86|0.981|
|**26**|46.87|45.76|0.976|42.56|41.82|0.983|
|**27**|47.01|45.77|0.974|42.65|41.77|0.979|
|**28**|46.99|45.78|0.974|42.73|41.76|0.977|
|**29**|46.97|45.69|0.973|42.64|41.79|0.980|
|**30**|47.01|45.76|0.973|42.58|41.82|0.982|
|**31**|46.89|45.75|0.976|42.52|41.83|0.984|
|**32**|46.92|45.74|0.975|42.62|41.74|0.980|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.14|14.18|1.002|12.68|12.66|0.999|
|2|18.82|18.74|0.995|16.22|16.39|1.011|
|3|21.83|21.88|1.002|18.49|18.40|0.995|
|4|25.86|25.98|1.005|21.62|21.58|0.998|
|5|28.41|28.41|1.000|22.76|22.83|1.003|
|6|31.74|31.95|1.007|25.82|25.66|0.994|
|7|34.45|34.49|1.001|27.31|27.28|0.999|
|8|37.08|37.20|1.003|29.42|29.43|1.000|
|9|39.95|39.98|1.001|31.25|31.38|1.004|
|10|42.70|42.82|1.003|33.76|33.81|1.001|
|11|45.57|45.59|1.001|35.83|35.82|1.000|
|12|48.20|48.23|1.001|38.21|38.26|1.001|
|13|50.98|50.98|1.000|40.01|40.18|1.004|
|14|53.78|53.90|1.002|42.62|42.62|1.000|
|15|56.50|56.47|1.000|44.77|44.70|0.999|
|16|59.13|59.02|0.998|47.00|46.96|0.999|
|17|61.70|61.88|1.003|49.22|49.42|1.004|
|18|64.26|64.42|1.003|51.41|51.68|1.005|
|19|66.59|66.68|1.001|53.64|53.74|1.002|
|20|68.98|69.12|1.002|55.94|56.02|1.001|
|21|71.40|71.29|0.998|58.44|58.46|1.000|
|22|73.62|73.82|1.003|60.42|60.57|1.002|
|23|75.98|76.11|1.002|62.50|62.50|1.000|
|24|78.49|78.58|1.001|64.70|64.80|1.002|
|25|80.93|80.90|1.000|67.22|67.03|0.997|
|26|83.38|83.34|0.999|69.54|69.20|0.995|
|27|85.88|85.85|1.000|71.64|71.62|1.000|
|28|88.28|88.29|1.000|73.82|73.84|1.000|
|29|90.90|90.86|1.000|76.08|76.06|1.000|
|30|93.39|93.54|1.002|78.30|78.43|1.002|
|31|96.00|96.01|1.000|80.70|80.64|0.999|
|32|98.59|98.44|0.998|82.95|82.78|0.998|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.91|13.75|0.988|12.58|12.64|1.005|
|2|17.45|17.31|0.992|15.41|15.50|1.006|
|3|21.37|21.40|1.001|18.02|18.13|1.006|
|4|23.84|23.93|1.004|19.77|20.03|1.013|
|5|27.51|27.53|1.001|22.38|22.42|1.002|
|6|30.19|30.22|1.001|23.93|24.14|1.009|
|7|32.95|33.08|1.004|26.08|26.00|0.997|
|8|35.70|35.76|1.002|28.34|28.30|0.999|
|9|37.92|38.08|1.004|29.66|29.85|1.006|
|10|40.42|40.44|1.001|31.77|31.73|0.999|
|11|42.52|42.55|1.001|33.18|33.09|0.997|
|12|44.39|44.45|1.001|34.51|34.56|1.001|
|13|46.51|46.48|0.999|35.92|35.93|1.000|
|14|48.70|48.72|1.000|37.61|37.48|0.997|
|15|49.08|49.16|1.002|38.76|38.86|1.002|
|16|50.78|50.80|1.000|40.05|40.14|1.002|
|17|52.78|52.85|1.001|41.64|41.66|1.001|
|18|54.65|54.43|0.996|43.46|43.20|0.994|
|19|56.30|56.34|1.001|44.65|44.58|0.998|
|20|58.19|58.14|0.999|46.05|45.97|0.998|
|21|59.83|59.76|0.999|47.30|47.48|1.004|
|22|61.54|61.66|1.002|48.78|48.82|1.001|
|23|63.20|63.23|1.001|50.26|50.26|1.000|
|24|64.89|64.83|0.999|51.70|51.67|0.999|
|25|66.89|66.91|1.000|53.22|53.23|1.000|
|26|68.63|68.59|0.999|54.61|54.67|1.001|
|27|68.51|68.50|1.000|54.65|54.63|1.000|
|28|68.66|68.49|0.998|54.58|54.68|1.002|
|29|68.54|68.49|0.999|54.70|54.68|1.000|
|30|68.64|68.58|0.999|54.78|54.71|0.999|
|31|68.59|68.50|0.999|54.76|54.66|0.998|
|32|68.51|68.56|1.001|54.62|54.75|1.002|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|20.10|20.21|1.005|17.86|17.90|1.002|
|2|25.90|25.96|1.002|21.22|21.20|0.999|
|3|31.41|31.33|0.997|25.32|25.29|0.999|
|4|38.48|38.54|1.002|30.39|30.58|1.006|
|5|43.00|43.37|1.009|33.50|33.65|1.004|
|6|47.78|47.87|1.002|37.26|37.44|1.005|
|7|54.65|54.71|1.001|42.49|42.41|0.998|
|8|59.40|59.46|1.001|46.21|46.30|1.002|
|9|63.88|63.92|1.001|50.08|50.03|0.999|
|10|69.07|69.11|1.001|55.18|55.30|1.002|
|11|73.21|73.17|0.999|59.10|59.05|0.999|
|12|77.36|77.58|1.003|62.94|63.14|1.003|
|13|82.34|82.30|1.000|67.90|68.06|1.002|
|14|86.98|86.95|1.000|72.27|72.50|1.003|
|15|91.24|91.14|0.999|76.13|76.43|1.004|
|16|95.72|95.97|1.003|81.14|81.22|1.001|
|17|100.18|100.10|0.999|85.04|85.41|1.004|
|18|104.36|104.33|1.000|89.61|89.27|0.996|
|19|109.16|109.53|1.003|93.58|93.70|1.001|
|20|113.37|113.67|1.003|98.31|98.34|1.000|
|21|117.33|117.51|1.002|102.31|102.46|1.001|
|22|122.79|122.55|0.998|106.92|106.62|0.997|
|23|127.05|126.83|0.998|111.09|111.14|1.001|
|24|130.73|131.12|1.003|114.98|115.40|1.004|
|25|135.42|135.55|1.001|119.60|119.70|1.001|
|26|140.18|139.70|0.997|123.89|123.58|0.997|
|27|144.50|144.47|1.000|128.06|128.00|1.000|
|28|149.13|149.18|1.000|132.61|132.59|1.000|
|29|153.09|153.61|1.003|136.58|136.91|1.002|
|30|157.43|157.87|1.003|140.97|141.18|1.002|
|31|161.95|162.05|1.001|145.18|145.21|1.000|
|32|166.66|166.26|0.998|149.79|149.62|0.999|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.17|12.16|0.999|11.17|11.10|0.994|
|2|14.78|14.78|1.000|13.46|13.41|0.996|
|3|17.11|17.13|1.001|15.07|15.11|1.003|
|4|19.57|19.58|1.000|17.27|17.35|1.005|
|5|21.14|21.16|1.001|18.53|18.40|0.993|
|6|23.18|23.20|1.001|19.45|19.36|0.995|
|7|25.86|25.86|1.000|21.70|21.52|0.992|
|8|27.47|27.43|0.999|22.52|22.49|0.999|
|9|29.26|29.25|1.000|23.73|23.62|0.996|
|10|31.30|31.36|1.002|25.97|25.98|1.001|
|11|32.89|32.89|1.000|26.82|26.95|1.005|
|12|34.52|34.70|1.005|27.60|27.50|0.997|
|13|36.41|36.30|0.997|29.34|29.20|0.995|
|14|37.78|38.04|1.007|30.27|30.39|1.004|
|15|39.71|39.70|1.000|31.70|31.45|0.992|
|16|41.30|41.29|1.000|32.81|32.74|0.998|
|17|42.87|42.85|0.999|34.02|34.06|1.001|
|18|44.54|44.70|1.003|35.18|35.30|1.003|
|19|46.38|46.35|0.999|36.73|36.75|1.001|
|20|47.97|47.86|0.998|38.02|37.90|0.997|
|21|49.78|49.72|0.999|39.15|39.17|1.000|
|22|51.66|51.59|0.999|40.72|40.55|0.996|
|23|53.39|53.45|1.001|42.08|42.11|1.001|
|24|55.23|55.16|0.999|43.20|43.41|1.005|
|25|56.78|56.81|1.000|44.71|44.69|0.999|
|26|58.70|58.63|0.999|46.08|46.05|0.999|
|27|60.09|60.10|1.000|47.30|47.31|1.000|
|28|61.68|61.70|1.000|48.59|48.64|1.001|
|29|63.31|63.29|1.000|50.06|50.25|1.004|
|30|64.76|64.70|0.999|51.43|51.38|0.999|
|31|66.23|66.18|0.999|52.78|52.74|0.999|
|32|67.64|67.66|1.000|54.16|54.12|0.999|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|26.38|26.59|1.008|22.43|22.53|1.004|
|2|40.48|40.74|1.007|32.42|32.34|0.998|
|3|53.42|53.45|1.000|42.23|42.14|0.998|
|4|65.31|65.28|1.000|52.14|51.98|0.997|
|5|76.42|76.56|1.002|62.22|62.24|1.000|
|6|87.44|87.55|1.001|72.42|72.24|0.998|
|7|98.22|97.92|0.997|82.90|82.66|0.997|
|8|108.48|108.63|1.001|92.44|92.62|1.002|
|9|118.81|119.17|1.003|102.61|102.94|1.003|
|10|128.94|129.10|1.001|112.35|112.81|1.004|
|11|139.07|138.78|0.998|122.47|122.44|1.000|
|12|149.15|148.98|0.999|132.20|132.10|0.999|
|13|158.78|158.69|0.999|141.86|141.84|1.000|
|14|168.83|168.77|1.000|151.63|151.62|1.000|
|15|178.28|178.45|1.001|161.35|161.48|1.001|
|16|188.24|187.99|0.999|171.04|170.94|0.999|
|17|195.29|195.37|1.000|178.49|178.51|1.000|
|18|202.48|202.46|1.000|185.54|185.38|0.999|
|19|209.50|209.33|0.999|192.39|192.38|1.000|
|20|209.27|209.59|1.002|192.38|192.47|1.001|
|21|209.49|209.45|1.000|192.74|192.59|0.999|
|22|209.47|209.36|0.999|192.67|192.66|1.000|
|23|209.59|209.62|1.000|192.68|192.69|1.000|
|24|209.57|209.62|1.000|192.82|192.73|1.000|
|25|210.20|210.26|1.000|193.51|193.68|1.001|
|26|210.26|210.36|1.000|193.62|193.58|1.000|
|27|210.15|210.44|1.001|193.66|193.55|0.999|
|28|210.38|210.35|1.000|193.70|193.75|1.000|
|29|210.40|210.38|1.000|193.89|193.86|1.000|
|30|210.66|210.57|1.000|193.86|193.87|1.000|
|31|210.60|210.69|1.000|193.90|194.00|1.000|
|32|210.69|210.58|1.000|194.07|193.89|0.999|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.74|12.71|0.998|11.65|11.68|1.003|
|2|16.58|16.58|1.000|14.49|14.46|0.998|
|3|19.80|19.77|0.998|17.01|17.09|1.005|
|4|22.07|22.04|0.999|18.49|18.46|0.998|
|5|25.26|25.28|1.001|20.71|20.78|1.003|
|6|27.42|27.54|1.004|22.00|22.14|1.006|
|7|29.66|29.71|1.002|23.22|23.32|1.004|
|8|32.34|32.06|0.992|25.68|25.60|0.997|
|9|34.18|34.19|1.000|26.98|26.92|0.998|
|10|36.58|36.58|1.000|29.06|29.04|0.999|
|11|38.98|39.07|1.002|30.06|30.22|1.005|
|12|41.21|41.14|0.998|31.68|31.58|0.997|
|13|43.29|43.15|0.997|33.90|34.04|1.004|
|14|45.37|45.38|1.000|35.53|35.59|1.002|
|15|47.30|47.34|1.001|37.41|37.44|1.001|
|16|48.44|48.51|1.001|38.14|38.16|1.000|
|17|48.59|48.57|1.000|38.26|38.38|1.003|
|18|48.50|48.54|1.001|38.30|38.40|1.002|
|19|48.62|48.54|0.998|38.25|38.28|1.001|
|20|48.56|48.47|0.998|38.21|38.21|1.000|
|21|48.64|48.50|0.997|38.32|38.39|1.002|
|22|48.51|48.61|1.002|38.41|38.35|0.999|
|23|48.62|48.65|1.000|38.34|38.34|1.000|
|24|48.56|48.62|1.001|38.29|38.39|1.003|
|25|48.76|48.69|0.999|38.52|38.64|1.003|
|26|48.82|48.68|0.997|38.55|38.38|0.996|
|27|48.63|48.80|1.003|38.48|38.39|0.998|
|28|48.70|48.73|1.001|38.53|38.69|1.004|
|29|48.66|48.78|1.002|38.60|38.62|1.000|
|30|48.71|48.92|1.004|38.55|38.66|1.003|
|31|48.80|48.80|1.000|38.50|38.47|0.999|
|32|48.61|48.62|1.000|38.60|38.64|1.001|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.49|25.68|1.008|21.87|22.11|1.011|
|2|37.22|36.98|0.994|30.42|30.19|0.992|
|3|47.86|47.89|1.000|38.10|37.99|0.997|
|4|58.81|58.84|1.001|46.32|46.23|0.998|
|5|68.86|68.72|0.998|54.60|54.46|0.997|
|6|78.58|78.73|1.002|63.30|63.34|1.001|
|7|88.10|88.16|1.001|72.02|72.06|1.000|
|8|96.73|96.66|0.999|80.88|80.91|1.000|
|9|105.50|105.54|1.000|89.68|89.58|0.999|
|10|114.49|114.49|1.000|98.13|97.85|0.997|
|11|123.18|123.10|0.999|106.54|106.29|0.998|
|12|131.58|131.61|1.000|114.96|114.95|1.000|
|13|140.07|140.10|1.000|123.26|123.25|1.000|
|14|148.70|148.44|0.998|131.81|131.52|0.998|
|15|157.05|156.80|0.998|139.90|139.76|0.999|
|16|165.46|165.44|1.000|148.32|148.10|0.999|
|17|174.25|173.98|0.998|156.88|156.79|0.999|
|18|182.46|182.64|1.001|165.26|165.60|1.002|
|19|190.89|190.97|1.000|173.82|173.82|1.000|
|20|199.29|199.31|1.000|182.02|182.02|1.000|
|21|207.79|207.78|1.000|190.49|190.60|1.001|
|22|215.99|216.09|1.000|198.84|198.82|1.000|
|23|224.41|224.47|1.000|207.10|207.08|1.000|
|24|232.85|232.83|1.000|215.62|215.59|1.000|
|25|241.48|241.47|1.000|224.30|224.39|1.000|
|26|250.05|250.21|1.001|232.93|232.97|1.000|
|27|258.41|258.38|1.000|241.20|241.17|1.000|
|28|266.73|266.75|1.000|249.60|249.72|1.000|
|29|274.92|275.01|1.000|257.74|257.98|1.001|
|30|283.35|283.36|1.000|266.35|266.17|0.999|
|31|291.62|291.91|1.001|274.68|274.89|1.001|
|32|299.56|299.88|1.001|282.52|282.76|1.001|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.67|22.70|1.001|19.57|19.61|1.002|
|2|33.09|33.01|0.998|26.53|26.58|1.002|
|3|43.23|43.20|0.999|34.22|34.05|0.995|
|4|52.83|52.72|0.998|41.51|41.50|1.000|
|5|61.99|62.00|1.000|48.94|48.84|0.998|
|6|70.42|70.48|1.001|56.45|56.42|0.999|
|7|78.88|79.05|1.002|64.30|64.49|1.003|
|8|87.34|87.19|0.998|72.15|72.12|1.000|
|9|94.95|95.07|1.001|79.69|79.61|0.999|
|10|102.71|102.77|1.001|87.22|87.18|1.000|
|11|110.45|110.33|0.999|94.71|94.62|0.999|
|12|118.18|118.39|1.002|102.15|102.17|1.000|
|13|126.01|125.95|1.000|109.66|109.72|1.001|
|14|133.75|133.66|0.999|117.09|117.14|1.000|
|15|141.35|141.15|0.999|124.58|124.63|1.000|
|16|141.84|141.70|0.999|125.05|125.08|1.000|
|17|142.19|142.02|0.999|125.45|125.30|0.999|
|18|142.02|142.06|1.000|125.19|125.39|1.002|
|19|142.02|142.00|1.000|125.45|125.41|1.000|
|20|142.19|142.12|0.999|125.36|125.41|1.000|
|21|142.08|142.26|1.001|125.55|125.46|0.999|
|22|142.17|142.22|1.000|125.54|125.44|0.999|
|23|142.39|142.24|0.999|125.65|125.55|0.999|
|24|142.38|142.39|1.000|125.68|125.61|0.999|
|25|142.78|142.81|1.000|126.06|126.06|1.000|
|26|142.83|142.74|0.999|126.18|126.06|0.999|
|27|142.66|142.73|1.000|125.92|125.91|1.000|
|28|142.75|142.64|0.999|126.06|125.82|0.998|
|29|142.99|142.87|0.999|126.22|126.18|1.000|
|30|142.74|142.90|1.001|126.04|126.21|1.001|
|31|142.86|143.06|1.001|126.26|126.34|1.001|
|32|142.86|142.91|1.000|126.31|126.30|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|36.45|36.11|0.991|29.30|28.94|0.988|
|2|52.57|52.61|1.001|40.25|40.31|1.002|
|3|67.93|67.90|1.000|53.35|53.41|1.001|
|4|82.42|82.39|1.000|66.90|66.97|1.001|
|5|95.15|94.98|0.998|79.13|79.04|0.999|
|6|108.55|108.62|1.001|92.25|91.99|0.997|
|7|121.46|121.55|1.001|105.29|104.77|0.995|
|8|134.28|134.14|0.999|117.38|117.30|0.999|
|9|148.02|148.06|1.000|130.38|130.57|1.001|
|10|160.27|160.41|1.001|142.84|143.00|1.001|
|11|172.89|173.00|1.001|155.37|155.34|1.000|
|12|185.75|185.62|0.999|167.96|168.08|1.001|
|13|198.35|198.13|0.999|181.02|180.64|0.998|
|14|210.43|210.66|1.001|193.31|193.22|1.000|
|15|223.21|223.38|1.001|205.86|205.62|0.999|
|16|236.11|235.89|0.999|218.26|218.16|1.000|
|17|250.27|250.38|1.000|232.92|233.12|1.001|
|18|262.55|262.38|0.999|245.42|245.27|0.999|
|19|274.85|274.86|1.000|257.82|257.94|1.000|
|20|283.49|283.18|0.999|266.12|266.02|1.000|
|21|291.54|291.66|1.000|274.23|274.54|1.001|
|22|300.07|300.02|1.000|282.69|282.83|1.001|
|23|308.28|308.23|1.000|291.26|291.06|0.999|
|24|316.38|316.64|1.001|299.35|299.47|1.000|
|25|325.46|325.46|1.000|308.03|307.99|1.000|
|26|334.08|333.94|1.000|316.51|316.61|1.000|
|27|342.30|342.26|1.000|324.78|325.04|1.001|
|28|350.68|350.58|1.000|333.20|333.06|1.000|
|29|359.02|358.86|1.000|341.41|341.36|1.000|
|30|367.32|367.10|0.999|349.98|349.82|1.000|
|31|375.72|375.72|1.000|358.31|358.12|0.999|
|32|383.97|383.91|1.000|366.48|366.65|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.37|24.38|1.000|19.84|20.02|1.009|
|2|37.82|37.78|0.999|29.51|29.42|0.997|
|3|50.11|50.04|0.999|38.51|38.60|1.002|
|4|61.53|61.35|0.997|48.26|48.14|0.998|
|5|72.46|72.51|1.001|58.10|58.20|1.002|
|6|82.54|82.59|1.001|67.46|67.46|1.000|
|7|94.90|94.90|1.000|79.54|79.45|0.999|
|8|104.83|104.78|1.000|89.38|89.34|1.000|
|9|115.80|115.76|1.000|99.86|99.87|1.000|
|10|124.96|125.12|1.001|108.91|109.00|1.001|
|11|134.14|134.08|1.000|117.80|117.53|0.998|
|12|144.10|144.01|0.999|127.50|127.35|0.999|
|13|152.90|152.94|1.000|136.06|136.02|1.000|
|14|163.15|163.13|1.000|145.77|145.80|1.000|
|15|172.74|172.90|1.001|155.43|155.36|1.000|
|16|172.80|172.90|1.001|155.79|155.66|0.999|
|17|173.48|173.41|1.000|156.09|155.99|0.999|
|18|173.68|173.51|0.999|156.28|156.20|0.999|
|19|173.59|173.58|1.000|156.14|156.28|1.001|
|20|173.78|173.76|1.000|156.65|156.71|1.000|
|21|173.72|173.71|1.000|156.70|156.74|1.000|
|22|173.70|173.75|1.000|156.25|156.24|1.000|
|23|172.76|172.81|1.000|155.74|155.80|1.000|
|24|173.92|173.96|1.000|156.46|156.56|1.001|
|25|174.98|174.98|1.000|157.87|157.87|1.000|
|26|174.86|174.62|0.999|157.37|157.31|1.000|
|27|174.94|174.98|1.000|157.55|157.32|0.999|
|28|174.91|175.10|1.001|157.57|157.53|1.000|
|29|175.23|175.10|0.999|158.45|158.59|1.001|
|30|175.34|175.32|1.000|158.66|158.86|1.001|
|31|175.03|175.01|1.000|158.03|157.81|0.999|
|32|173.92|173.79|0.999|156.81|156.97|1.001|

<!-- rows: 480; changed rows: 24 -->

**sm_103a** (NVIDIA GB300, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens = rows whose schedule this PR changes.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.86|13.97|1.008|12.46|12.54|1.006|
|2|18.93|18.91|0.999|16.67|16.66|0.999|
|3|22.58|22.67|1.004|19.21|19.16|0.998|
|4|26.38|26.42|1.002|21.92|21.93|1.000|
|5|30.13|30.13|1.000|24.84|24.82|0.999|
|6|33.48|33.44|0.999|27.14|27.11|0.999|
|7|37.07|37.10|1.001|29.70|29.56|0.995|
|8|36.24|36.20|0.999|32.14|32.08|0.998|
|9|39.83|39.89|1.001|35.41|35.42|1.000|
|10|42.54|42.52|0.999|37.79|37.87|1.002|
|11|45.06|45.01|0.999|40.21|40.18|0.999|
|12|47.58|47.50|0.998|42.45|42.48|1.001|
|13|50.00|50.09|1.002|44.94|44.94|1.000|
|14|52.79|52.76|0.999|47.38|47.31|0.998|
|15|55.57|55.59|1.000|49.87|49.91|1.001|
|16|58.29|58.21|0.999|52.27|52.26|1.000|
|17|60.47|60.46|1.000|54.14|54.15|1.000|
|18|62.24|62.18|0.999|55.76|55.81|1.001|
|19|64.14|64.16|1.000|57.64|57.55|0.998|
|20|64.95|64.99|1.001|57.89|57.85|0.999|
|21|65.24|65.38|1.002|58.33|58.47|1.002|
|22|65.42|65.27|0.998|58.31|58.27|0.999|
|23|64.99|65.03|1.001|57.99|58.08|1.002|
|24|65.04|65.03|1.000|57.95|58.00|1.001|
|25|65.13|65.25|1.002|58.17|58.09|0.999|
|26|65.56|65.60|1.001|58.48|58.52|1.001|
|27|65.63|65.49|0.998|58.44|58.56|1.002|
|28|65.49|65.46|1.000|58.38|58.39|1.000|
|29|65.53|65.54|1.000|58.46|58.48|1.000|
|30|65.58|65.64|1.001|58.54|58.51|1.000|
|31|65.57|65.53|0.999|58.50|58.47|0.999|
|32|65.52|65.57|1.001|58.55|58.48|0.999|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.36|16.23|0.992|15.25|15.01|0.984|
|2|22.34|22.38|1.001|20.68|20.90|1.010|
|3|25.98|26.01|1.001|23.93|23.88|0.998|
|4|31.62|31.58|0.999|29.05|29.02|0.999|
|5|36.14|35.98|0.996|33.14|33.20|1.002|
|6|41.47|41.32|0.996|37.91|37.92|1.000|
|7|45.89|45.92|1.001|41.74|42.02|1.007|
|8|50.59|50.63|1.001|46.34|46.44|1.002|
|9|55.67|55.90|1.004|51.02|50.82|0.996|
|10|60.60|60.43|0.997|55.03|55.12|1.002|
|11|65.45|65.42|1.000|60.20|60.20|1.000|
|12|70.10|70.17|1.001|64.18|64.05|0.998|
|13|75.06|74.98|0.999|68.53|68.69|1.002|
|14|79.88|79.95|1.001|73.06|73.30|1.003|
|15|84.70|84.66|0.999|77.66|77.60|0.999|
|16|89.11|89.24|1.001|81.87|81.74|0.998|
|17|94.18|94.17|1.000|86.15|85.98|0.998|
|18|98.75|98.72|1.000|90.31|90.43|1.001|
|19|103.32|103.37|1.000|94.73|94.54|0.998|
|20|108.10|107.92|0.998|98.67|98.78|1.001|
|21|112.38|112.70|1.003|103.30|103.46|1.001|
|22|117.20|116.94|0.998|107.49|107.52|1.000|
|23|121.76|121.82|1.001|112.02|111.94|0.999|
|24|126.38|126.42|1.000|116.17|115.76|0.996|
|25|131.24|131.13|0.999|120.66|120.46|0.998|
|26|135.86|135.70|0.999|124.48|124.72|1.002|
|27|140.13|140.13|1.000|129.03|129.06|1.000|
|28|144.82|144.72|0.999|133.22|133.18|1.000|
|29|149.35|149.42|1.000|137.50|137.44|1.000|
|30|153.87|153.93|1.000|141.94|141.54|0.997|
|31|158.35|158.50|1.001|145.94|145.85|0.999|
|32|163.10|162.61|0.997|150.12|150.30|1.001|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.13|14.08|0.997|13.33|13.33|1.000|
|2|16.26|16.30|1.002|15.24|14.97|0.982|
|3|19.48|19.45|0.998|18.02|17.91|0.994|
|4|22.50|22.58|1.004|20.73|20.80|1.003|
|5|24.85|24.90|1.002|22.94|23.03|1.004|
|6|27.27|27.26|0.999|25.20|25.22|1.001|
|7|29.83|29.98|1.005|27.51|27.54|1.001|
|8|32.98|32.86|0.997|30.43|30.34|0.997|
|9|35.58|35.55|0.999|32.92|32.83|0.997|
|10|38.06|37.95|0.997|35.19|35.20|1.000|
|11|40.74|40.75|1.000|37.74|37.83|1.002|
|12|43.57|43.60|1.001|40.41|40.58|1.004|
|13|45.95|45.86|0.998|42.70|42.63|0.998|
|14|48.62|48.84|1.005|45.21|45.10|0.998|
|15|51.43|51.37|0.999|47.82|47.72|0.998|
|16|53.74|53.85|1.002|50.11|50.12|1.000|
|17|56.26|56.42|1.003|52.51|52.50|1.000|
|18|58.77|58.82|1.001|54.89|54.81|0.999|
|19|61.68|61.52|0.997|57.26|57.33|1.001|
|20|63.86|63.98|1.002|59.70|59.63|0.999|
|21|66.46|66.46|1.000|62.13|61.82|0.995|
|22|68.88|69.09|1.003|64.51|64.17|0.995|
|23|71.65|71.74|1.001|66.98|66.93|0.999|
|24|74.00|73.82|0.998|69.23|69.37|1.002|
|25|76.45|76.50|1.001|71.54|71.62|1.001|
|26|79.10|79.25|1.002|74.10|74.08|1.000|
|27|81.70|81.79|1.001|76.32|76.48|1.002|
|28|84.12|83.96|0.998|78.69|78.94|1.003|
|29|86.47|86.40|0.999|81.26|81.16|0.999|
|30|89.06|88.88|0.998|83.94|83.60|0.996|
|31|91.60|91.60|1.000|85.71|85.74|1.000|
|32|93.94|93.90|1.000|88.50|88.74|1.003|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|15.98|15.94|0.997|14.54|14.51|0.998|
|2|21.63|21.50|0.994|19.50|19.53|1.001|
|3|25.34|25.36|1.001|22.83|23.02|1.008|
|4|29.43|29.48|1.002|26.71|26.85|1.005|
|5|34.32|34.36|1.001|31.04|31.02|0.999|
|6|38.50|38.42|0.998|34.70|34.70|1.000|
|7|42.83|42.87|1.001|38.80|38.93|1.003|
|8|47.02|46.99|0.999|42.51|42.62|1.002|
|9|51.25|51.30|1.001|46.49|46.42|0.999|
|10|55.64|55.65|1.000|50.43|50.47|1.001|
|11|59.77|59.65|0.998|54.14|54.02|0.998|
|12|63.78|63.98|1.003|58.02|57.82|0.997|
|13|68.14|67.99|0.998|61.58|61.68|1.002|
|14|72.05|72.06|1.000|65.43|65.40|1.000|
|15|76.31|76.22|0.999|69.14|69.21|1.001|
|16|76.23|76.36|1.002|68.96|69.11|1.002|
|17|76.53|76.37|0.998|69.27|69.37|1.001|
|18|76.45|76.26|0.997|69.28|69.34|1.001|
|19|76.34|76.42|1.001|69.26|69.22|1.000|
|20|76.43|76.40|1.000|69.24|69.22|1.000|
|21|76.35|76.31|0.999|69.33|69.15|0.997|
|22|76.44|76.43|1.000|69.30|69.35|1.001|
|23|76.34|76.47|1.002|69.17|69.14|1.000|
|24|76.63|76.41|0.997|68.97|69.20|1.003|
|25|76.68|76.56|0.998|69.34|69.33|1.000|
|26|76.57|76.52|0.999|69.34|69.41|1.001|
|27|76.70|76.52|0.998|69.33|69.40|1.001|
|28|76.61|76.54|0.999|69.22|69.34|1.002|
|29|76.66|76.55|0.999|69.39|69.52|1.002|
|30|76.58|76.63|1.001|69.46|69.29|0.997|
|31|76.58|76.69|1.001|69.34|69.28|0.999|
|32|76.66|76.66|1.000|69.46|69.34|0.998|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.74|13.70|0.998|12.78|12.90|1.009|
|2|16.15|16.25|1.006|14.96|15.09|1.009|
|3|19.09|19.10|1.000|17.33|17.34|1.001|
|4|21.46|21.46|1.000|19.64|19.66|1.001|
|5|23.77|23.82|1.002|21.86|21.87|1.000|
|6|26.21|26.18|0.999|23.90|23.91|1.001|
|7|29.10|29.11|1.000|26.27|26.22|0.998|
|**8**|31.06|30.41|0.979|28.14|27.70|0.984|
|9|33.44|33.40|0.999|30.19|30.17|0.999|
|**10**|35.54|35.10|0.987|32.37|31.96|0.987|
|**11**|38.07|37.13|0.975|34.52|33.71|0.977|
|**12**|40.06|38.98|0.973|36.32|35.66|0.982|
|**13**|42.18|41.08|0.974|38.42|37.63|0.979|
|**14**|44.38|43.27|0.975|40.54|39.54|0.976|
|**15**|46.38|45.30|0.977|42.40|41.33|0.975|
|**16**|46.43|45.16|0.973|42.45|41.38|0.975|
|**17**|46.62|45.36|0.973|42.50|41.54|0.977|
|**18**|46.52|45.27|0.973|42.42|41.42|0.977|
|**19**|46.66|45.34|0.972|42.48|41.47|0.976|
|**20**|46.52|45.30|0.974|42.48|41.49|0.977|
|**21**|46.69|45.29|0.970|42.38|41.57|0.981|
|**22**|46.76|45.35|0.970|42.50|41.46|0.976|
|**23**|46.73|45.32|0.970|42.53|41.48|0.975|
|**24**|46.59|45.25|0.971|42.39|41.44|0.978|
|**25**|46.87|45.35|0.968|42.83|41.62|0.972|
|**26**|46.92|45.48|0.969|42.80|41.54|0.970|
|**27**|46.82|45.42|0.970|42.55|41.58|0.977|
|**28**|46.84|45.34|0.968|42.62|41.56|0.975|
|**29**|46.90|45.38|0.968|42.80|41.64|0.973|
|**30**|47.05|45.43|0.966|42.83|41.65|0.972|
|**31**|46.82|45.58|0.973|42.66|41.63|0.976|
|**32**|46.86|45.46|0.970|42.88|41.55|0.969|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.08|14.15|1.005|12.68|12.64|0.997|
|2|18.60|18.68|1.004|16.17|16.44|1.017|
|3|21.50|21.58|1.004|18.35|18.36|1.000|
|4|25.39|25.55|1.006|21.30|21.31|1.000|
|5|28.07|28.19|1.004|22.94|23.02|1.003|
|6|31.51|31.58|1.002|25.82|25.81|1.000|
|7|34.31|34.14|0.995|27.41|27.42|1.001|
|8|37.07|37.34|1.007|29.62|29.64|1.001|
|9|40.03|39.81|0.994|31.71|31.57|0.995|
|10|42.67|42.76|1.002|34.18|34.34|1.005|
|11|45.44|45.53|1.002|36.36|36.17|0.995|
|12|48.20|48.30|1.002|38.72|38.73|1.000|
|13|50.87|50.97|1.002|40.74|40.78|1.001|
|14|53.85|53.92|1.001|43.02|43.12|1.002|
|15|56.82|56.78|0.999|45.55|45.46|0.998|
|16|59.32|59.46|1.002|47.94|47.85|0.998|
|17|61.78|61.97|1.003|50.03|50.25|1.004|
|18|64.42|64.53|1.002|52.27|52.34|1.001|
|19|67.06|67.20|1.002|54.69|54.72|1.001|
|20|69.67|69.66|1.000|56.98|57.06|1.002|
|21|72.05|72.10|1.001|59.31|59.30|1.000|
|22|74.39|74.62|1.003|61.53|61.58|1.001|
|23|76.85|77.06|1.003|63.84|63.85|1.000|
|24|79.69|79.66|1.000|66.26|66.15|0.998|
|25|81.97|82.06|1.001|68.58|68.29|0.996|
|26|84.26|84.28|1.000|70.99|70.70|0.996|
|27|86.75|86.78|1.000|73.23|73.25|1.000|
|28|89.22|89.18|1.000|75.36|75.37|1.000|
|29|91.88|91.76|0.999|77.74|77.66|0.999|
|30|94.38|94.50|1.001|80.10|80.20|1.001|
|31|97.07|97.01|0.999|82.43|82.44|1.000|
|32|99.46|99.43|1.000|84.64|84.66|1.000|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.99|13.12|1.010|11.65|11.74|1.008|
|2|16.56|16.54|0.999|14.68|14.79|1.008|
|3|20.43|20.56|1.006|17.58|17.70|1.007|
|4|23.33|23.24|0.996|19.92|19.74|0.991|
|5|26.30|26.46|1.006|21.41|21.50|1.004|
|6|29.33|29.35|1.001|23.39|23.22|0.993|
|7|32.11|32.09|0.999|25.29|25.28|1.000|
|8|34.66|34.80|1.004|27.50|27.61|1.004|
|9|37.33|37.29|0.999|28.90|28.99|1.003|
|10|40.04|40.09|1.001|31.12|31.18|1.002|
|11|41.47|41.46|1.000|33.28|33.28|1.000|
|**12**|43.34|38.80|0.895|35.14|34.38|0.978|
|**13**|45.44|40.50|0.891|36.93|35.82|0.970|
|**14**|47.37|42.06|0.888|38.61|37.24|0.965|
|**15**|49.44|43.48|0.879|40.44|38.65|0.956|
|**16**|50.99|45.23|0.887|41.42|40.03|0.966|
|**17**|52.98|46.97|0.887|42.88|41.55|0.969|
|**18**|54.76|48.66|0.889|44.23|43.10|0.974|
|**19**|56.74|50.21|0.885|45.58|44.48|0.976|
|**20**|58.22|51.74|0.889|46.65|45.70|0.980|
|**21**|60.02|53.29|0.888|47.99|47.09|0.981|
|**22**|62.10|54.70|0.881|49.78|48.50|0.974|
|**23**|63.78|56.37|0.884|51.08|49.76|0.974|
|**24**|65.44|58.02|0.887|52.63|51.25|0.974|
|**25**|67.53|59.84|0.886|54.28|52.94|0.975|
|**26**|69.06|61.33|0.888|55.60|54.15|0.974|
|**27**|69.12|61.42|0.889|55.59|54.14|0.974|
|**28**|69.20|61.35|0.887|55.73|54.15|0.972|
|**29**|69.12|61.32|0.887|55.74|54.25|0.973|
|**30**|69.14|61.44|0.889|55.64|54.15|0.973|
|**31**|69.13|61.40|0.888|55.77|54.14|0.971|
|**32**|69.07|61.34|0.888|55.70|54.19|0.973|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|20.08|20.12|1.002|17.66|17.69|1.001|
|2|25.91|25.78|0.995|21.16|20.94|0.989|
|3|31.26|31.49|1.007|25.38|25.19|0.993|
|4|38.70|38.86|1.004|30.90|30.81|0.997|
|5|43.33|43.42|1.002|34.60|34.37|0.993|
|6|48.38|48.32|0.999|38.17|38.14|0.999|
|7|55.27|55.21|0.999|43.56|43.66|1.002|
|8|59.94|59.96|1.000|47.37|47.17|0.996|
|9|64.79|64.62|0.997|51.13|51.14|1.000|
|10|69.86|69.79|0.999|56.33|56.31|1.000|
|11|74.22|74.26|1.000|60.10|60.38|1.005|
|12|78.54|78.64|1.001|64.35|64.51|1.002|
|13|83.45|83.37|0.999|69.58|69.39|0.997|
|14|88.13|88.00|0.999|74.06|74.35|1.004|
|15|92.46|92.30|0.998|77.94|77.92|1.000|
|16|97.17|97.00|0.998|82.70|82.62|0.999|
|17|101.26|101.38|1.001|87.18|87.14|1.000|
|18|106.11|105.99|0.999|91.25|91.66|1.004|
|19|110.89|110.82|0.999|95.62|95.58|0.999|
|20|115.03|115.18|1.001|100.55|100.10|0.995|
|21|119.70|119.36|0.997|104.77|104.64|0.999|
|22|124.49|124.41|0.999|108.91|109.22|1.003|
|23|129.02|128.98|1.000|113.62|113.28|0.997|
|24|133.37|133.74|1.003|117.83|117.72|0.999|
|25|137.78|138.02|1.002|122.22|122.16|1.000|
|26|142.37|142.49|1.001|126.60|126.49|0.999|
|27|147.02|146.97|1.000|130.87|131.02|1.001|
|28|151.13|151.22|1.001|135.45|135.42|1.000|
|29|155.99|155.46|0.997|139.68|140.30|1.004|
|30|160.66|160.23|0.997|143.93|144.30|1.003|
|31|164.69|164.50|0.999|148.89|148.67|0.999|
|32|169.02|169.23|1.001|153.23|152.97|0.998|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|11.74|11.86|1.010|10.77|10.86|1.009|
|2|14.45|14.54|1.007|13.09|13.10|1.001|
|3|16.65|16.72|1.004|14.88|15.07|1.013|
|4|19.17|19.19|1.001|16.99|17.10|1.006|
|5|21.01|20.82|0.991|18.04|18.07|1.002|
|6|22.99|23.02|1.001|19.43|19.48|1.002|
|7|25.62|25.43|0.993|21.47|21.40|0.997|
|8|27.37|27.40|1.001|22.70|22.79|1.004|
|9|29.14|29.10|0.999|23.89|23.82|0.997|
|10|31.51|31.54|1.001|25.94|26.07|1.005|
|11|33.24|32.98|0.992|26.99|26.90|0.996|
|12|34.81|35.01|1.006|28.09|28.02|0.997|
|13|36.73|36.58|0.996|29.91|29.79|0.996|
|14|38.41|38.31|0.998|31.02|30.90|0.996|
|15|39.84|39.95|1.003|31.94|31.85|0.997|
|16|41.57|41.80|1.006|33.21|33.32|1.003|
|17|43.13|43.12|1.000|34.58|34.58|1.000|
|18|44.94|44.90|0.999|35.78|35.92|1.004|
|19|46.65|46.72|1.002|37.21|37.38|1.005|
|20|48.31|48.34|1.001|38.50|38.52|1.000|
|21|50.02|50.06|1.001|40.12|40.04|0.998|
|22|51.87|51.71|0.997|41.40|41.43|1.001|
|23|53.78|53.60|0.997|42.82|42.74|0.998|
|24|55.32|55.19|0.998|44.10|44.26|1.003|
|25|57.13|57.12|1.000|45.58|45.54|0.999|
|26|58.70|58.73|1.001|47.14|46.99|0.997|
|27|60.35|60.31|0.999|48.34|48.44|1.002|
|28|61.69|61.81|1.002|49.62|49.81|1.004|
|29|63.44|63.57|1.002|51.29|51.22|0.999|
|30|65.10|65.19|1.001|52.72|52.75|1.001|
|31|66.82|66.83|1.000|54.02|54.23|1.004|
|32|68.30|68.36|1.001|55.46|55.58|1.002|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|26.82|27.10|1.010|22.65|22.51|0.994|
|2|40.84|40.80|0.999|32.80|32.67|0.996|
|3|53.64|53.79|1.003|42.75|42.74|1.000|
|4|65.76|65.62|0.998|53.03|52.84|0.996|
|5|77.38|77.49|1.001|63.34|63.41|1.001|
|**6**|88.26|79.98|0.906|73.70|72.83|0.988|
|**7**|99.19|90.59|0.913|84.39|82.85|0.982|
|**8**|110.12|101.22|0.919|94.83|92.74|0.978|
|**9**|120.73|112.57|0.932|105.00|103.29|0.984|
|**10**|131.14|123.33|0.940|115.44|113.56|0.984|
|**11**|141.18|134.18|0.950|125.45|123.21|0.982|
|**12**|151.46|144.57|0.955|135.37|133.11|0.983|
|**13**|161.89|155.51|0.961|145.67|143.34|0.984|
|**14**|171.54|166.02|0.968|155.52|153.10|0.984|
|**15**|181.78|176.35|0.970|165.70|163.04|0.984|
|**16**|191.84|186.86|0.974|175.69|173.18|0.986|
|**17**|199.34|194.62|0.976|183.26|180.48|0.985|
|**18**|206.73|202.26|0.978|190.64|187.69|0.985|
|**19**|213.64|209.54|0.981|197.70|194.62|0.984|
|**20**|213.77|209.63|0.981|197.81|194.79|0.985|
|**21**|213.90|209.61|0.980|197.98|194.61|0.983|
|**22**|213.86|209.66|0.980|197.87|194.71|0.984|
|**23**|213.90|209.51|0.980|197.94|194.68|0.984|
|**24**|213.93|209.55|0.980|197.96|194.69|0.983|
|**25**|214.50|210.22|0.980|198.74|195.48|0.984|
|**26**|214.72|210.28|0.979|198.81|195.47|0.983|
|**27**|214.63|210.22|0.979|198.81|195.51|0.983|
|**28**|214.68|210.25|0.979|198.86|195.44|0.983|
|**29**|214.66|210.38|0.980|198.90|195.57|0.983|
|**30**|214.73|210.33|0.980|198.94|195.31|0.982|
|**31**|214.90|210.42|0.979|199.07|195.50|0.982|
|**32**|214.83|210.46|0.980|199.01|195.41|0.982|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.74|12.68|0.995|11.59|11.65|1.005|
|2|16.12|16.23|1.007|14.22|14.37|1.011|
|3|19.51|19.62|1.005|17.01|17.13|1.007|
|4|21.72|21.58|0.994|18.30|18.34|1.002|
|5|24.86|24.88|1.001|20.92|20.86|0.997|
|6|27.33|27.24|0.997|22.35|22.18|0.992|
|7|29.24|29.18|0.998|23.63|23.70|1.003|
|8|32.06|32.26|1.006|25.90|26.03|1.005|
|9|34.24|34.27|1.001|27.30|27.41|1.004|
|10|36.58|36.67|1.002|29.27|29.26|1.000|
|11|38.71|38.71|1.000|30.64|30.78|1.005|
|12|40.88|40.87|1.000|32.54|32.60|1.002|
|13|42.88|42.99|1.003|34.07|34.18|1.003|
|14|45.21|45.38|1.004|35.86|35.97|1.003|
|15|47.14|47.10|0.999|37.86|37.63|0.994|
|**16**|48.59|43.18|0.889|38.78|38.35|0.989|
|**17**|48.74|43.67|0.896|39.08|38.71|0.991|
|18|48.86|48.82|0.999|38.98|39.04|1.002|
|**19**|48.80|43.55|0.892|39.22|38.62|0.985|
|**20**|48.78|43.67|0.895|39.10|38.62|0.988|
|**21**|48.88|43.74|0.895|39.06|38.70|0.991|
|**22**|48.86|43.82|0.897|39.19|38.66|0.987|
|**23**|48.84|43.72|0.895|39.22|38.55|0.983|
|**24**|48.85|43.76|0.896|39.20|38.63|0.986|
|**25**|49.00|43.82|0.894|39.20|38.77|0.989|
|**26**|49.02|43.90|0.896|39.35|38.74|0.984|
|**27**|48.98|43.90|0.896|39.25|38.72|0.987|
|**28**|48.90|43.87|0.897|39.40|38.71|0.983|
|**29**|48.98|44.00|0.898|39.22|38.79|0.989|
|30|49.09|48.94|0.997|39.36|39.17|0.995|
|31|49.04|49.03|1.000|39.30|39.18|0.997|
|**32**|49.06|43.89|0.895|39.32|38.62|0.982|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|25.22|25.33|1.004|22.20|22.14|0.997|
|2|37.62|37.67|1.001|31.23|31.46|1.007|
|3|48.52|48.66|1.003|39.51|39.60|1.002|
|4|59.13|59.14|1.000|48.18|48.18|1.000|
|5|69.70|69.66|0.999|57.20|57.18|1.000|
|**6**|80.05|70.63|0.882|66.34|64.26|0.969|
|**7**|89.80|80.18|0.893|75.61|72.83|0.963|
|**8**|99.06|89.18|0.900|84.03|81.23|0.967|
|**9**|107.15|98.70|0.921|91.86|90.32|0.983|
|**10**|116.09|108.06|0.931|100.55|98.57|0.980|
|**11**|124.84|117.15|0.938|109.34|107.35|0.982|
|**12**|133.64|126.54|0.947|117.74|115.79|0.983|
|**13**|142.36|135.66|0.953|126.47|124.10|0.981|
|**14**|151.23|144.78|0.957|135.10|132.70|0.982|
|**15**|159.75|153.82|0.963|143.92|141.51|0.983|
|**16**|168.86|163.04|0.966|152.86|149.94|0.981|
|**17**|177.58|172.37|0.971|161.40|158.45|0.982|
|**18**|186.19|181.80|0.976|170.08|166.99|0.982|
|**19**|194.70|190.62|0.979|178.64|175.42|0.982|
|**20**|203.13|199.46|0.982|187.25|184.03|0.983|
|**21**|211.99|208.73|0.985|195.74|192.74|0.985|
|**22**|220.70|217.50|0.986|204.64|201.07|0.983|
|**23**|229.37|226.58|0.988|213.13|209.57|0.983|
|**24**|237.59|235.34|0.991|221.60|217.91|0.983|
|**25**|246.80|244.78|0.992|230.67|227.15|0.985|
|26|255.34|255.34|1.000|239.14|239.30|1.001|
|27|263.93|263.96|1.000|247.75|247.58|0.999|
|28|272.70|272.87|1.001|256.45|256.59|1.001|
|29|281.30|281.28|1.000|265.10|265.22|1.000|
|30|289.98|289.84|1.000|274.02|273.70|0.999|
|31|298.49|298.44|1.000|282.34|282.09|0.999|
|32|307.13|306.90|0.999|290.92|290.70|0.999|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|22.59|22.54|0.998|19.38|19.36|0.999|
|2|33.44|33.42|1.000|26.86|26.91|1.002|
|3|43.41|43.39|1.000|34.70|34.67|0.999|
|4|53.38|53.40|1.000|42.22|42.34|1.003|
|5|62.34|62.25|0.998|50.00|49.85|0.997|
|6|71.30|71.30|1.000|57.86|57.91|1.001|
|7|79.95|79.94|1.000|65.84|65.74|0.999|
|8|88.24|88.12|0.999|73.64|73.65|1.000|
|9|96.38|96.29|0.999|81.49|81.44|0.999|
|10|104.24|104.36|1.001|89.14|89.26|1.001|
|11|112.26|112.39|1.001|96.99|97.02|1.000|
|12|120.27|120.26|1.000|104.69|104.65|1.000|
|13|128.28|128.10|0.999|112.50|112.54|1.000|
|14|136.22|135.87|0.997|120.30|120.18|0.999|
|**15**|143.66|138.78|0.966|127.86|125.94|0.985|
|**16**|144.34|138.69|0.961|128.51|125.84|0.979|
|**17**|144.81|139.12|0.961|128.81|126.29|0.980|
|**18**|144.70|139.07|0.961|128.79|126.25|0.980|
|**19**|144.83|139.11|0.961|128.92|126.37|0.980|
|**20**|144.71|139.14|0.962|128.98|126.17|0.978|
|**21**|144.71|139.06|0.961|129.03|126.12|0.977|
|**22**|144.96|139.15|0.960|129.18|126.21|0.977|
|**23**|144.82|139.22|0.961|129.09|126.22|0.978|
|**24**|144.84|139.13|0.961|129.04|126.18|0.978|
|**25**|145.25|139.70|0.962|129.57|126.78|0.979|
|**26**|145.40|139.70|0.961|129.51|126.72|0.978|
|**27**|145.46|139.70|0.960|129.69|126.76|0.977|
|**28**|145.26|139.67|0.962|129.69|126.70|0.977|
|**29**|145.56|139.84|0.961|129.79|126.81|0.977|
|**30**|145.42|139.78|0.961|129.81|126.74|0.976|
|**31**|145.45|139.77|0.961|129.76|126.86|0.978|
|**32**|145.60|139.76|0.960|129.87|126.74|0.976|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|36.62|36.86|1.007|29.58|29.72|1.005|
|2|53.19|53.18|1.000|41.02|40.90|0.997|
|3|68.82|68.61|0.997|54.27|54.61|1.006|
|4|83.02|82.87|0.998|68.07|67.96|0.998|
|5|96.11|96.05|0.999|80.71|80.67|1.000|
|6|109.74|109.76|1.000|93.99|93.89|0.999|
|7|123.08|123.12|1.000|106.96|106.95|1.000|
|8|136.35|136.26|0.999|120.00|120.66|1.005|
|9|150.36|150.46|1.001|133.86|133.85|1.000|
|10|163.26|163.22|1.000|146.90|146.78|0.999|
|11|176.33|176.46|1.001|159.86|159.80|1.000|
|12|189.32|189.61|1.002|172.74|172.94|1.001|
|13|202.54|202.47|1.000|185.61|185.89|1.002|
|14|215.54|215.48|1.000|198.86|198.58|0.999|
|15|228.39|228.44|1.000|211.80|211.77|1.000|
|16|241.42|241.49|1.000|224.64|224.62|1.000|
|17|255.77|255.86|1.000|239.45|239.54|1.000|
|18|268.93|268.94|1.000|252.41|252.46|1.000|
|19|281.57|281.70|1.000|265.18|265.24|1.000|
|20|290.30|290.19|1.000|274.14|274.04|1.000|
|21|298.60|298.74|1.000|282.68|282.53|0.999|
|22|307.28|307.26|1.000|291.21|291.44|1.001|
|23|315.99|316.13|1.000|299.78|299.82|1.000|
|24|324.60|324.66|1.000|308.28|308.30|1.000|
|25|333.33|333.67|1.001|317.22|317.56|1.001|
|26|342.04|342.22|1.001|326.02|326.02|1.000|
|27|350.66|350.78|1.000|334.40|334.62|1.001|
|28|359.34|359.17|1.000|343.26|343.18|1.000|
|29|367.72|367.85|1.000|351.79|351.74|1.000|
|30|376.56|376.55|1.000|360.35|360.34|1.000|
|31|385.02|384.98|1.000|368.98|369.02|1.000|
|32|394.02|393.81|0.999|377.78|377.67|1.000|

<!-- rows: 448; changed rows: 124 -->

This PR doesn't change the kernel's Cake variants: SwiGLU, SwiGLU with
alpha/beta/limit, SiLU and SiTU on sm_100a and sm_103a, plus clamped
SwiGLU (limit 10) on sm_100a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated GPU MoE decode kernel selection across several model
configurations and token counts, including expanded coverage for
additional batch sizes.
* Revised scheduling for selected configurations to use fused route
packing and updated matrix-multiplication paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e1cc284](https://github.com/flashinfer-ai/flashinfer/commit/e1cc2840a22a20c042920fef0ab6cca49dfb45a7)

- **作者**: Cindy Zhang
- **时间**: 2026-10-26T15:10:44Z
- **提交信息**: fix(ci): avoid cubin build tmp quota failures (#7420)

<!-- .github/pull_request_template.md -->

## 📌 Description

Nightly Release
[#422](https://github.com/flashinfer-ai/flashinfer/actions/runs/40161685799)
failed to build `flashinfer-cubin` in all three attempts with:

  ```text
  OSError: [Errno 122] Disk quota exceeded
```
  The failure occurred while PEP 517 was creating an isolated build environment under /tmp/build-env-* and installing torch==2.14.1 together with its CUDA dependencies.

  The preceding cubin build in Nightly Release #421 (https://github.com/flashinfer-ai/flashinfer/actions/runs/40061880291) succeeded on Ubuntu 24.04. All #422 attempts ran on Ubuntu 26.04, where /tmp is a quota-limited tmpfs. This behavior is tracked in actions/runner-images#14777(https://github.com/actions/runner-images/issues/14777).

  This PR applies the workaround to both nightly and official release workflows:

  - Pin build-flashinfer-cubin to ubuntu-24.04 for an immediately known-good environment.
  - Set TMPDIR to ${{ runner.temp }}/flashinfer-cubin-build, keeping the large PEP 517 environment off /tmp.
  - Create the temporary directory before invoking python -m build.
  - Log filesystem and /tmp mount information to make future capacity failures easier to diagnose.
  - Apply the same protection to release.yml, which used the same runner and isolated build path.

  The change only affects temporary build-file placement and runner selection. It does not change the downloaded cubin inventory, wheel contents, package metadata,or downstream test jobs.

## 🔍 Related Issues

Fix https://github.com/flashinfer-ai/flashinfer/issues/7414

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit` (or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files` and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy (CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under `flashinfer/experimental/` and/or an `@flashinfer_experimental_api`. Tracking issue: #
  - [ ] The tracking issue names an owner, the reason for the experimental path, and a graduation plan with a target release.
  - [ ] Core changes are limited to a thin entry point (signature, shared validation, feature-gate check, backend selection, handoff).
  - [ ] Tests live in `tests/experimental/` and were validated on the intended hardware; a runnable example is included.
  - [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental backend is reachable from `backend="auto"` without `FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an `@flashinfer_experimental_api` or naming a backend explicitly is itself the opt-in and needs no environment variable.)
  - [ ] **Test scope declared below.** The experimental CI lane runs exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below with your targets.
     Do not delete the fence or change its `experimental-tests` tag — the experimental-track
     watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is
not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add
yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means
every
# experimental PR pays for every other feature's tests, in every matrix
cell.
```

## Reviewer Notes
The Ubuntu 24.04 pin is intended as a short-term safety measure. Once the updated runner behavior has been validated, the job can return to ubuntu-latest while retaining the step-scoped TMPDIR override.

Please confirm that applying the same workaround to both nightly and official release workflows is the desired scope.

### Long-term follow-up

  This PR intentionally keeps the existing PEP 517 build behavior unchanged and focuses on restoring the nightly and release pipelines safely.

  The longer-term fix is to avoid installing the complete CUDA-enabled PyTorch dependency stack inside a fresh PEP 517 isolated environment for every `flashinfer-cubin` build. The cubin wheel build currently resolves `torch` together with large CUDA packages such as cuBLAS, cuDNN, cuSPARSE, and NCCL, even though the primary build operation is downloading and packaging precompiled cubin artifacts.

Potential follow-up approaches include:
  - Prepare a controlled build environment once and build with:
  - 
    ```bash
    python -m build --no-isolation --wheel
```
- Use a CPU-only Torch build if Torch is still required by the current
artifact discovery/import path.

- Preferably, decouple the cubin downloader and packaging backend from
Torch so that Torch is no longer a build-system dependency of
flashinfer-cubin.

- Add post-build wheel validation for the expected cubin inventory,
checksums, and package metadata.

Those changes require separate dependency and artifact-validation
review. They are intentionally left out of this PR so the
runner-capacity regression can be fixed with minimal behavioral change.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated the build environment used for nightly and standard releases.
* Release builds now use a dedicated temporary workspace and record
additional storage environment details.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0af9594](https://github.com/flashinfer-ai/flashinfer/commit/0af9594727aff41f4e02a052d88912c44260e766)

- **作者**: Zihao Ye
- **时间**: 2026-10-26T12:15:36Z
- **提交信息**: fix(cake_all_gather_matmul): wait for the peer CTA's last stage releases before the CTA-pair load warp exits (#6885)

**Race.** In the CTA-pair (`cta_group::2`) main programs of the Cake
all-gather matmul, the leader CTA's MMA warp releases each stage of the
TMA load ring with a multicast `tcgen05.commit` to the `mma_done`
mbarrier of both CTAs. The peer CTA's load warp waits on that barrier
only before a refill. So after its last refill, it can leave the tile
loop and the CTA can exit while the arrive-ons for the last ring-depth
stages are still in flight toward its shared memory. An async arrive on
the shared memory of a CTA that has exited is undefined (PTX ISA
§2.2.2). PTX does not order one `tcgen05.commit` after another
(§9.7.18.6), so the later accumulator commit that the epilogue waits on
does not cover them.

**Change.** After its tile loop, the load warp waits on `mma_done` for
the last ring-depth stages, advancing its stage index and phase exactly
as the main loop does (a producer tail, as in CUTLASS's
`producer_tail`). The tart kernels carry the same tail (kitchen/flour
fc9e1cf5d).

**Affected programs.** The 7 CTA-pair main programs in
`csrc/cake_all_gather_matmul/`.

**Tests.** On GB300 (sm_103a), world size 2:
- `tests/comm/test_all_gather_matmul_cake.py` and
`test_all_gather_matmul_cake_e2e.py`: 375 passed.
- The three CTA-pair shapes below match a torch reference on both ranks.
- compute-sanitizer racecheck reports 0 hazards and synccheck 0 errors
on those shapes (cake kernels only).

**Timing.** NVIDIA GB300 ×2 (NVLink), sm_103a, CUDA 13.3, world size 2.
Each run is a separate process.
- Each run times 200 back-to-back calls per rank with CUPTI and takes
the main kernel's median span.
- The figure is the mean of the two ranks' medians. Peer arrival order
shifts time between the ranks, but not their mean.
- There are 12 runs in ABBA order (6 before, 6 after), all under one
hold of both GPUs' benchmark locks with no other GPU users. The table
shows the median over runs.

| rows per rank | N | B layout | main program | before (us) | after (us)
| change | before, range of runs | after, range of runs |
|---|---|---|---|---|---|---|---|---|
| 1024 | 2048 | k_major | d0fc2abec5d93b9a81ec | 74.90 | 74.70 | -0.27%
| 74.2..76.6 | 74.5..75.3 |
| 2048 | 2048 | n_major | 06c1f7cb4aa36c5918bd | 100.07 | 100.22 |
+0.15% | 98.8..100.6 | 99.7..100.7 |
| 4096 | 1280 | n_major | 06c1f7cb4aa36c5918bd | 151.49 | 151.04 |
-0.30% | 150.6..151.7 | 150.5..151.6 |

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved completion handling for matrix multiplication operations by
ensuring all remaining pipeline stages finish before processing ends.
* Increased synchronization reliability across supported workloads,
reducing the risk of incomplete or inconsistent results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [32a26fe](https://github.com/flashinfer-ai/flashinfer/commit/32a26fe723d119a3c615c3058bc5685222151278)

- **作者**: eigen
- **时间**: 2026-10-26T12:13:05Z
- **提交信息**: feat(cake_vsa_sm90): retune the FP8 grouped-query compact and shared-transposer queue programs (prefetch distance, transposer batch depth) (#7412)

FlashInfer's Cake backend for variable block-sparse attention on Hopper
(`VariableBlockSparseAttentionWrapper(backend="cake")`, sm_90a) supports
two data types: BF16 and Sage-FP8 (E4M3 inputs with per-head scales,
BF16 output). Each data type has multi-head (MHA) programs and
grouped-query programs (num_qo_heads = g × num_kv_heads, g ∈ {2, 4, 8}).
#7167 added the grouped-query programs, and #7185 updated the FP8
grouped-query shared-transposer queue program (8 V^T chunks per
hand-off). This PR updates two Sage-FP8 grouped-query programs in place.
The compact static program now prefetches K/V into L2 one ring position
ahead instead of two, and its V transposer now keeps one ldmatrix chunk
in flight per batch instead of four. The shared-transposer queue
program, which is the persistent queue program for the long FP8
grouped-query rows, no longer prefetches K/V into L2 (previously
distance 1). Every other delivered kernel is byte-identical to the
previous version, compared per unit at the machine-code level: all 40
multi-head kernel units and the remaining 38 grouped-query units,
including every small-selection program. The baseline is the previous
Cake version of this backend as shipped by #7185, measured on the same
node in the same run form: two processes, a and b, each 9 groups × 256
samples, CUPTI kernel-sum, cold L2, both interleaving orders. Speedup =
previous / this. The two changed programs serve 29 of the 142 shapes, or
33 of the 284 rows because 4 of those rows are shared-set duplicates.
Their geometric-mean speedup is 1.0029 in process a and 1.0020 in
process b. In process a, the compact program goes from 51.456 to 50.015
µs (1.0288) on `h16-m8192-n8192-k5-ragged0-scale0-g4` and from 51.824 to
49.824 µs (1.0402) on `h16-m8192-n8192-k5-ragged0-scale0-g8`; process b
reads 1.0301 and 1.0309. The queue program's 27 shapes (29 rows) have a
geometric mean of 0.9986 (a) / 0.9981 (b), with a range of 0.9949–1.0074
(a) / 0.9955–1.0014 (b), which is within the noise of the previous
version in this run form. The other 251 rows run byte-identical machine
code, and their geometric mean is 0.9999 in both processes (range
0.9808–1.0096 in process a), which is the measurement noise of the same
bytes. Over all 284 rows the geometric mean is 1.0002 in both processes.

Kernel-only time on NVIDIA H100 80GB HBM3 (Hopper, sm_90a), CUDA 13.4
toolkit (JIT-compiled; torch 2.14.1+cu130), driver 535.216.03: the
previous Cake version of this backend (shipped by #7185) and this
version, both measured on the same node in the same two-process run form
(CUPTI kernel-sum per forward, cold L2, 9 groups × 256 samples, both
interleaving orders); the table shows one process; speedup = previous /
this. Shapes are named h<num_qo_heads>-m<query tokens>-n<key/value
tokens>-k<KV blocks per query block>-ragged<0|1>-scale0-g<group size>;
dtype e4m3 means Sage-FP8 and bf16 means BF16.

| shape | dtype | previous µs | this µs | speedup |
|---|---|---|---|---|
| h4-m1024-n1024-k8-ragged1-scale0-g4 | bf16 | 6.177 | 6.177 | 1.0000 |
| h4-m1024-n1024-k8-ragged1-scale0-g4 | e4m3 | 5.601 | 5.600 | 1.0001 |
| h4-m1024-n512-k4-ragged1-scale0-g4 | bf16 | 5.472 | 5.472 | 1.0000 |
| h4-m1024-n512-k4-ragged1-scale0-g4 | e4m3 | 4.864 | 4.864 | 1.0000 |
| h4-m256-n256-k1-ragged0-scale0-g4 | bf16 | 3.073 | 3.104 | 0.9900 |
| h4-m256-n256-k1-ragged0-scale0-g4 | e4m3 | 2.944 | 2.944 | 1.0000 |
| h4-m512-n1024-k4-ragged0-scale0-g4 | bf16 | 5.152 | 5.152 | 1.0000 |
| h4-m512-n1024-k4-ragged0-scale0-g4 | e4m3 | 4.864 | 4.864 | 1.0000 |
| h4-m512-n512-k4-ragged0-scale1-g4 | bf16 | 5.152 | 5.152 | 1.0000 |
| h4-m512-n512-k4-ragged0-scale1-g4 | e4m3 | 4.800 | 4.800 | 1.0000 |
| h8-m1024-n1024-k12-ragged0-scale0-g4 | bf16 | 10.272 | 10.304 | 0.9969
|
| h8-m1024-n1024-k12-ragged0-scale0-g4 | e4m3 | 10.016 | 10.016 | 1.0000
|
| h8-m1024-n1024-k12-ragged0-scale0-g8 | bf16 | 10.240 | 10.239 | 1.0001
|
| h8-m1024-n1024-k12-ragged0-scale0-g8 | e4m3 | 9.952 | 10.016 | 0.9936
|
| h8-m1024-n1024-k4-ragged0-scale0-g4 | bf16 | 6.496 | 6.496 | 1.0000 |
| h8-m1024-n1024-k4-ragged0-scale0-g4 | e4m3 | 5.664 | 5.665 | 0.9998 |
| h8-m1024-n1024-k4-ragged0-scale0-g8 | bf16 | 6.304 | 6.304 | 1.0000 |
| h8-m1024-n1024-k4-ragged0-scale0-g8 | e4m3 | 5.504 | 5.504 | 1.0000 |
| h8-m2048-n2048-k16-ragged0-scale0-g4 | bf16 | 20.160 | 20.160 | 1.0000
|
| h8-m2048-n2048-k16-ragged0-scale0-g4 | e4m3 | 18.656 | 18.624 | 1.0017
|
| h8-m2048-n2048-k16-ragged0-scale0-g8 | bf16 | 19.904 | 19.873 | 1.0016
|
| h8-m2048-n2048-k16-ragged0-scale0-g8 | e4m3 | 18.688 | 18.752 | 0.9966
|
| h8-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 12.896 | 12.896 | 1.0000
|
| h8-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 11.712 | 11.712 | 1.0000
|
| h8-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 12.577 | 12.608 | 0.9975
|
| h8-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 11.393 | 11.616 | 0.9808
|
| h8-m256-n256-k3-ragged0-scale0-g4 | bf16 | 4.735 | 4.736 | 0.9998 |
| h8-m256-n256-k3-ragged0-scale0-g4 | e4m3 | 4.416 | 4.447 | 0.9930 |
| h8-m256-n256-k3-ragged0-scale0-g8 | bf16 | 4.736 | 4.736 | 1.0000 |
| h8-m256-n256-k3-ragged0-scale0-g8 | e4m3 | 4.384 | 4.352 | 1.0074 |
| h8-m4096-n4096-k16-ragged0-scale0-g4 | bf16 | 33.440 | 33.472 | 0.9990
|
| h8-m4096-n4096-k16-ragged0-scale0-g4 | e4m3 | 32.321 | 32.320 | 1.0000
|
| h8-m4096-n4096-k16-ragged0-scale0-g8 | bf16 | 33.312 | 33.376 | 0.9981
|
| h8-m4096-n4096-k16-ragged0-scale0-g8 | e4m3 | 32.161 | 32.272 | 0.9965
|
| h8-m4096-n4096-k32-ragged0-scale0-g4 | bf16 | 57.856 | 57.793 | 1.0011
|
| h8-m4096-n4096-k32-ragged0-scale0-g4 | e4m3 | 56.064 | 56.049 | 1.0003
|
| h8-m4096-n4096-k32-ragged0-scale0-g8 | bf16 | 57.024 | 56.961 | 1.0011
|
| h8-m4096-n4096-k32-ragged0-scale0-g8 | e4m3 | 55.136 | 55.136 | 1.0000
|
| h16-m1024-n8192-k1-ragged0-scale0-g4 | bf16 | 6.656 | 6.656 | 1.0000 |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | e4m3 | 5.281 | 5.312 | 0.9942 |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | bf16 | 6.464 | 6.464 | 1.0000 |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | e4m3 | 5.152 | 5.152 | 1.0000 |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | bf16 | 59.297 | 59.232 |
1.0011 |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | e4m3 | 57.056 | 57.088 |
0.9994 |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | bf16 | 59.008 | 59.009 |
1.0000 |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | e4m3 | 57.536 | 57.088 |
1.0078 |
| h16-m8192-n8192-k5-ragged0-scale0-g4 | bf16 | 52.353 | 52.320 | 1.0006
|
| h16-m8192-n8192-k5-ragged0-scale0-g4 | e4m3 | 51.456 | 50.015 | 1.0288
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | bf16 | 52.032 | 52.064 | 0.9994
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | e4m3 | 51.824 | 49.824 | 1.0402
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 38.688 | 38.688 | 1.0000
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 37.056 | 37.120 | 0.9983
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 37.056 | 37.089 | 0.9991
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 36.513 | 36.352 | 1.0044
|
| h32-m8192-n8192-k24-ragged0-scale0-g4 | bf16 | 342.178 | 343.267 |
0.9968 |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | e4m3 | 311.169 | 312.641 |
0.9953 |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | bf16 | 347.937 | 344.626 |
1.0096 |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | e4m3 | 310.881 | 312.257 |
0.9956 |
| h4-m2048-n4096-k6-ragged0-scale0-g4 | bf16 | 7.712 | 7.712 | 1.0000 |
| h4-m2048-n4096-k6-ragged0-scale0-g4 | e4m3 | 7.136 | 7.136 | 1.0000 |
| h4-m2048-n4096-k6-ragged0-scale0-uneven-g4 | bf16 | 7.520 | 7.520 |
1.0000 |
| h4-m2048-n4096-k6-ragged0-scale0-uneven-g4 | e4m3 | 6.528 | 6.528 |
1.0000 |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | bf16 | 36.129 | 36.160 |
0.9991 |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | e4m3 | 32.032 | 32.032 |
1.0000 |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | bf16 | 33.664 | 33.696 |
0.9991 |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | e4m3 | 31.872 | 31.904 |
0.9990 |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | bf16 | 31.616 | 31.616 |
1.0000 |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | e4m3 | 28.800 | 28.801 |
1.0000 |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | bf16 | 30.401 | 30.368 |
1.0011 |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | e4m3 | 29.568 | 29.632 |
0.9978 |
| h8-m4096-n4096-k20-ragged1-scale0-g4 | bf16 | 25.841 | 25.856 | 0.9994
|
| h8-m4096-n4096-k20-ragged1-scale0-g4 | e4m3 | 24.576 | 24.576 | 1.0000
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | bf16 | 25.152 | 25.184 | 0.9987
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | e4m3 | 24.512 | 24.576 | 0.9974
|
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | bf16 | 22.496 | 22.496 |
1.0000 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | e4m3 | 22.208 | 22.176 |
1.0014 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | bf16 | 26.816 | 26.816 |
1.0000 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | e4m3 | 25.920 | 25.937 |
0.9994 |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | bf16 | 106.305 | 106.944 |
0.9940 |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | e4m3 | 101.536 | 101.472 |
1.0006 |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | bf16 | 106.944 | 106.912 |
1.0003 |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | e4m3 | 101.280 | 101.217 |
1.0006 |
| h8-m512-n4096-k2-ragged0-scale0-g4 | bf16 | 4.896 | 4.896 | 1.0000 |
| h8-m512-n4096-k2-ragged0-scale0-g4 | e4m3 | 4.256 | 4.256 | 1.0000 |
| h8-m512-n4096-k2-ragged0-scale0-g8 | bf16 | 4.672 | 4.641 | 1.0067 |
| h8-m512-n4096-k2-ragged0-scale0-g8 | e4m3 | 4.096 | 4.096 | 1.0000 |
| h8-m8192-n8192-k2-ragged0-scale0-g4 | bf16 | 19.616 | 19.648 | 0.9984
|
| h8-m8192-n8192-k2-ragged0-scale0-g4 | e4m3 | 16.288 | 16.288 | 1.0000
|
| h8-m8192-n8192-k2-ragged0-scale0-g8 | bf16 | 18.176 | 18.208 | 0.9982
|
| h8-m8192-n8192-k2-ragged0-scale0-g8 | e4m3 | 15.649 | 15.776 | 0.9919
|
| h12-m109632-n109632-k32-ragged0-scale0-g4 | bf16 | 2623.365 | 2621.412
| 1.0007 |
| h12-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 2006.650 | 2004.731
| 1.0010 |
| h12-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 4970.064 | 4969.711
| 1.0001 |
| h12-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 3862.463 | 3870.719
| 0.9979 |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 2567.641 | 2555.016
| 1.0049 |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 2000.922 | 2008.427
| 0.9963 |
| h12-m32768-n32768-k32-ragged0-scale0-g4 | bf16 | 704.612 | 707.924 |
0.9953 |
| h12-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 596.483 | 598.691 |
0.9963 |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 1374.822 | 1374.405 |
1.0003 |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 1130.903 | 1128.518 |
1.0021 |
| h12-m32768-n32768-k64-ragged1-scale0-g4 | bf16 | 700.004 | 707.652 |
0.9892 |
| h12-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 | 595.139 | 594.995 |
1.0002 |
| h12-m75648-n75648-k32-ragged0-scale0-g4 | bf16 | 1766.264 | 1767.448 |
0.9993 |
| h12-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 1353.879 | 1350.168 |
1.0027 |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 3328.482 | 3321.842 |
1.0020 |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 2608.122 | 2611.003 |
0.9989 |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1721.639 | 1724.663 |
0.9982 |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 1366.791 | 1365.303 |
1.0011 |
| h8-m109632-n109632-k32-ragged0-scale0-g4 | bf16 | 1715.832 | 1718.042
| 0.9987 |
| h8-m109632-n109632-k32-ragged0-scale0-g4 | e4m3 | 1344.660 | 1345.684
| 0.9992 |
| h8-m109632-n109632-k32-ragged0-scale0-g8 | bf16 | 1698.663 | 1698.806
| 0.9999 |
| h8-m109632-n109632-k32-ragged0-scale0-g8 | e4m3 | 1323.350 | 1326.373
| 0.9977 |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 3280.818 | 3295.908
| 0.9954 |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | e4m3 | 2575.399 | 2556.361
| 1.0074 |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | bf16 | 3303.806 | 3288.734
| 1.0046 |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | e4m3 | 2530.443 | 2539.340
| 0.9965 |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 1658.954 | 1659.306
| 0.9998 |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | e4m3 | 1327.285 | 1323.285
| 1.0030 |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | bf16 | 1634.679 | 1637.944
| 0.9980 |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | e4m3 | 1292.566 | 1289.815
| 1.0021 |
| h8-m32768-n32768-k32-ragged0-scale0-g4 | bf16 | 456.227 | 455.939 |
1.0006 |
| h8-m32768-n32768-k32-ragged0-scale0-g4 | e4m3 | 401.857 | 402.769 |
0.9977 |
| h8-m32768-n32768-k32-ragged0-scale0-g8 | bf16 | 463.058 | 463.683 |
0.9987 |
| h8-m32768-n32768-k32-ragged0-scale0-g8 | e4m3 | 401.970 | 404.050 |
0.9949 |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 893.941 | 890.245 |
1.0042 |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | e4m3 | 753.283 | 755.283 |
0.9974 |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | bf16 | 902.356 | 900.996 |
1.0015 |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | e4m3 | 748.323 | 750.068 |
0.9977 |
| h8-m32768-n32768-k64-ragged1-scale0-g4 | bf16 | 454.691 | 453.603 |
1.0024 |
| h8-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 | 402.433 | 403.234 |
0.9980 |
| h8-m32768-n32768-k64-ragged1-scale0-g8 | bf16 | 465.538 | 464.835 |
1.0015 |
| h8-m32768-n32768-k64-ragged1-scale0-g8 | e4m3 | 411.538 | 411.842 |
0.9993 |
| h8-m75648-n75648-k32-ragged0-scale0-g4 | bf16 | 1133.798 | 1132.006 |
1.0016 |
| h8-m75648-n75648-k32-ragged0-scale0-g4 | e4m3 | 902.114 | 901.746 |
1.0004 |
| h8-m75648-n75648-k32-ragged0-scale0-g8 | bf16 | 1137.685 | 1138.197 |
0.9995 |
| h8-m75648-n75648-k32-ragged0-scale0-g8 | e4m3 | 895.605 | 897.604 |
0.9978 |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 2188.619 | 2185.084 |
1.0016 |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | e4m3 | 1724.806 | 1728.694 |
0.9978 |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | bf16 | 2197.673 | 2197.913 |
0.9999 |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | e4m3 | 1715.720 | 1718.137 |
0.9986 |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1108.662 | 1109.862 |
0.9989 |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | e4m3 | 902.996 | 906.179 |
0.9965 |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | bf16 | 1110.949 | 1116.389 |
0.9951 |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | e4m3 | 889.189 | 892.437 |
0.9964 |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | bf16 | 6.656 | 6.656 | 1.0000 |
| h16-m1024-n8192-k1-ragged0-scale0-g4 | e4m3 | 5.281 | 5.312 | 0.9942 |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | bf16 | 6.464 | 6.464 | 1.0000 |
| h16-m1024-n8192-k1-ragged0-scale0-g8 | e4m3 | 5.152 | 5.152 | 1.0000 |
| h16-m1024-n8192-k12-ragged0-scale0-g4 | bf16 | 16.800 | 16.800 |
1.0000 |
| h16-m1024-n8192-k12-ragged0-scale0-g4 | e4m3 | 15.232 | 15.232 |
1.0000 |
| h16-m1024-n8192-k12-ragged0-scale0-g8 | bf16 | 16.032 | 15.936 |
1.0060 |
| h16-m1024-n8192-k12-ragged0-scale0-g8 | e4m3 | 15.008 | 15.040 |
0.9979 |
| h16-m256-n2048-k7-ragged1-scale0-g4 | bf16 | 6.720 | 6.720 | 1.0000 |
| h16-m256-n2048-k7-ragged1-scale0-g4 | e4m3 | 5.952 | 5.952 | 1.0000 |
| h16-m256-n2048-k7-ragged1-scale0-g8 | bf16 | 6.176 | 6.176 | 1.0000 |
| h16-m256-n2048-k7-ragged1-scale0-g8 | e4m3 | 5.696 | 5.696 | 1.0001 |
| h16-m256-n512-k2-ragged1-scale0-g4 | bf16 | 4.577 | 4.576 | 1.0002 |
| h16-m256-n512-k2-ragged1-scale0-g4 | e4m3 | 4.064 | 4.032 | 1.0079 |
| h16-m256-n512-k2-ragged1-scale0-g8 | bf16 | 4.544 | 4.544 | 1.0000 |
| h16-m256-n512-k2-ragged1-scale0-g8 | e4m3 | 4.000 | 4.000 | 1.0000 |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | bf16 | 59.297 | 59.232 |
1.0011 |
| h16-m4096-n16384-k16-ragged0-scale0-g4 | e4m3 | 57.056 | 57.088 |
0.9994 |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | bf16 | 59.008 | 59.009 |
1.0000 |
| h16-m4096-n16384-k16-ragged0-scale0-g8 | e4m3 | 57.536 | 57.088 |
1.0078 |
| h16-m8192-n8192-k5-ragged0-scale0-g4 | bf16 | 52.353 | 52.320 | 1.0006
|
| h16-m8192-n8192-k5-ragged0-scale0-g4 | e4m3 | 51.456 | 50.015 | 1.0288
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | bf16 | 52.032 | 52.064 | 0.9994
|
| h16-m8192-n8192-k5-ragged0-scale0-g8 | e4m3 | 51.824 | 49.824 | 1.0402
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | bf16 | 38.688 | 38.688 | 1.0000
|
| h32-m2048-n2048-k8-ragged0-scale0-g4 | e4m3 | 37.056 | 37.120 | 0.9983
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | bf16 | 37.056 | 37.089 | 0.9991
|
| h32-m2048-n2048-k8-ragged0-scale0-g8 | e4m3 | 36.513 | 36.352 | 1.0044
|
| h32-m512-n8192-k16-ragged0-scale0-g4 | bf16 | 20.352 | 20.352 | 1.0000
|
| h32-m512-n8192-k16-ragged0-scale0-g4 | e4m3 | 18.784 | 18.785 | 0.9999
|
| h32-m512-n8192-k16-ragged0-scale0-g8 | bf16 | 19.072 | 19.041 | 1.0016
|
| h32-m512-n8192-k16-ragged0-scale0-g8 | e4m3 | 17.984 | 17.984 | 1.0000
|
| h32-m8192-n8192-k24-ragged0-scale0-g4 | bf16 | 342.178 | 343.267 |
0.9968 |
| h32-m8192-n8192-k24-ragged0-scale0-g4 | e4m3 | 311.169 | 312.641 |
0.9953 |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | bf16 | 347.937 | 344.626 |
1.0096 |
| h32-m8192-n8192-k24-ragged0-scale0-g8 | e4m3 | 310.881 | 312.257 |
0.9956 |
| h4-m2048-n2048-k5-ragged0-scale0-g4 | bf16 | 7.392 | 7.392 | 1.0000 |
| h4-m2048-n2048-k5-ragged0-scale0-g4 | e4m3 | 6.752 | 6.752 | 1.0000 |
| h4-m256-n2048-k7-ragged0-scale0-g4 | bf16 | 5.024 | 5.024 | 1.0000 |
| h4-m256-n2048-k7-ragged0-scale0-g4 | e4m3 | 4.703 | 4.672 | 1.0066 |
| h4-m256-n4096-k14-ragged0-scale0-g4 | bf16 | 6.049 | 6.048 | 1.0002 |
| h4-m256-n4096-k14-ragged0-scale0-g4 | e4m3 | 5.792 | 5.792 | 1.0000 |
| h4-m256-n8192-k18-ragged0-scale0-g4 | bf16 | 7.424 | 7.424 | 1.0000 |
| h4-m256-n8192-k18-ragged0-scale0-g4 | e4m3 | 7.072 | 7.072 | 1.0000 |
| h4-m256-n8192-k24-ragged0-scale0-g4 | bf16 | 8.960 | 8.960 | 1.0000 |
| h4-m256-n8192-k24-ragged0-scale0-g4 | e4m3 | 8.288 | 8.288 | 1.0000 |
| h4-m256-n8192-k48-ragged0-scale0-g4 | bf16 | 12.448 | 12.448 | 1.0000
|
| h4-m256-n8192-k48-ragged0-scale0-g4 | e4m3 | 10.784 | 10.784 | 1.0000
|
| h4-m512-n16384-k20-ragged0-scale0-g4 | bf16 | 10.304 | 10.304 | 1.0000
|
| h4-m512-n16384-k20-ragged0-scale0-g4 | e4m3 | 9.536 | 9.535 | 1.0001 |
| h4-m512-n2048-k9-ragged0-scale0-g4 | bf16 | 6.096 | 6.081 | 1.0025 |
| h4-m512-n2048-k9-ragged0-scale0-g4 | e4m3 | 5.664 | 5.664 | 1.0000 |
| h8-m1024-n2048-k4-ragged0-scale0-g4 | bf16 | 6.688 | 6.688 | 1.0000 |
| h8-m1024-n2048-k4-ragged0-scale0-g4 | e4m3 | 5.856 | 5.825 | 1.0053 |
| h8-m1024-n2048-k4-ragged0-scale0-g8 | bf16 | 6.464 | 6.464 | 1.0000 |
| h8-m1024-n2048-k4-ragged0-scale0-g8 | e4m3 | 5.665 | 5.665 | 1.0000 |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | bf16 | 36.129 | 36.160 |
0.9991 |
| h8-m1024-n32768-k64-ragged0-scale0-g4 | e4m3 | 32.032 | 32.032 |
1.0000 |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | bf16 | 33.664 | 33.696 |
0.9991 |
| h8-m1024-n32768-k64-ragged0-scale0-g8 | e4m3 | 31.872 | 31.904 |
0.9990 |
| h8-m1024-n4096-k6-ragged0-scale0-g4 | bf16 | 7.968 | 7.937 | 1.0039 |
| h8-m1024-n4096-k6-ragged0-scale0-g4 | e4m3 | 7.296 | 7.296 | 1.0000 |
| h8-m1024-n4096-k6-ragged0-scale0-g8 | bf16 | 7.712 | 7.712 | 1.0000 |
| h8-m1024-n4096-k6-ragged0-scale0-g8 | e4m3 | 7.104 | 7.104 | 1.0000 |
| h8-m128-n32768-k64-ragged0-scale0-g4 | bf16 | 21.280 | 21.248 | 1.0015
|
| h8-m128-n32768-k64-ragged0-scale0-g4 | e4m3 | 18.048 | 18.080 | 0.9982
|
| h8-m128-n32768-k64-ragged0-scale0-g8 | bf16 | 20.544 | 20.512 | 1.0016
|
| h8-m128-n32768-k64-ragged0-scale0-g8 | e4m3 | 17.824 | 17.856 | 0.9982
|
| h8-m128-n4096-k17-ragged0-scale0-g4 | bf16 | 6.976 | 6.944 | 1.0046 |
| h8-m128-n4096-k17-ragged0-scale0-g4 | e4m3 | 6.528 | 6.528 | 1.0000 |
| h8-m128-n4096-k17-ragged0-scale0-g8 | bf16 | 6.656 | 6.688 | 0.9952 |
| h8-m128-n4096-k17-ragged0-scale0-g8 | e4m3 | 6.304 | 6.304 | 1.0000 |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | bf16 | 31.616 | 31.616 |
1.0000 |
| h8-m2048-n32768-k48-ragged1-scale0-g4 | e4m3 | 28.800 | 28.801 |
1.0000 |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | bf16 | 30.401 | 30.368 |
1.0011 |
| h8-m2048-n32768-k48-ragged1-scale0-g8 | e4m3 | 29.568 | 29.632 |
0.9978 |
| h8-m256-n16384-k32-ragged0-scale0-g4 | bf16 | 17.920 | 17.920 | 1.0000
|
| h8-m256-n16384-k32-ragged0-scale0-g4 | e4m3 | 17.409 | 17.440 | 0.9982
|
| h8-m256-n16384-k32-ragged0-scale0-g8 | bf16 | 17.376 | 17.376 | 1.0000
|
| h8-m256-n16384-k32-ragged0-scale0-g8 | e4m3 | 17.408 | 17.409 | 0.9999
|
| h8-m256-n2048-k10-ragged0-scale0-g4 | bf16 | 6.976 | 6.976 | 1.0000 |
| h8-m256-n2048-k10-ragged0-scale0-g4 | e4m3 | 6.528 | 6.528 | 1.0000 |
| h8-m256-n2048-k10-ragged0-scale0-g8 | bf16 | 6.784 | 6.784 | 1.0000 |
| h8-m256-n2048-k10-ragged0-scale0-g8 | e4m3 | 6.432 | 6.432 | 1.0000 |
| h8-m256-n2048-k8-ragged0-scale0-g4 | bf16 | 6.272 | 6.272 | 1.0000 |
| h8-m256-n2048-k8-ragged0-scale0-g4 | e4m3 | 5.760 | 5.760 | 1.0000 |
| h8-m256-n2048-k8-ragged0-scale0-g8 | bf16 | 6.016 | 6.016 | 1.0000 |
| h8-m256-n2048-k8-ragged0-scale0-g8 | e4m3 | 5.600 | 5.568 | 1.0057 |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g4 | bf16 | 6.976 | 6.976 |
1.0000 |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g4 | e4m3 | 6.432 | 6.432 |
1.0000 |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g8 | bf16 | 6.752 | 6.752 |
1.0000 |
| h8-m256-n4096-k12-ragged0-scale0-uneven-g8 | e4m3 | 6.368 | 6.368 |
1.0000 |
| h8-m256-n4096-k16-ragged0-scale0-g4 | bf16 | 9.568 | 9.568 | 1.0000 |
| h8-m256-n4096-k16-ragged0-scale0-g4 | e4m3 | 8.480 | 8.480 | 1.0000 |
| h8-m256-n4096-k16-ragged0-scale0-g8 | bf16 | 9.248 | 9.247 | 1.0001 |
| h8-m256-n4096-k16-ragged0-scale0-g8 | e4m3 | 8.288 | 8.288 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale0-g4 | bf16 | 6.432 | 6.432 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale0-g4 | e4m3 | 5.760 | 5.760 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale0-g8 | bf16 | 6.208 | 6.208 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale0-g8 | e4m3 | 5.568 | 5.568 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale1-g4 | bf16 | 6.401 | 6.400 | 1.0001 |
| h8-m256-n4096-k8-ragged0-scale1-g4 | e4m3 | 5.824 | 5.824 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale1-g8 | bf16 | 6.208 | 6.208 | 1.0000 |
| h8-m256-n4096-k8-ragged0-scale1-g8 | e4m3 | 5.599 | 5.600 | 0.9998 |
| h8-m256-n4096-k9-ragged0-scale0-g4 | bf16 | 6.464 | 6.463 | 1.0002 |
| h8-m256-n4096-k9-ragged0-scale0-g4 | e4m3 | 5.888 | 5.888 | 1.0000 |
| h8-m256-n4096-k9-ragged0-scale0-g8 | bf16 | 6.144 | 6.145 | 0.9998 |
| h8-m256-n4096-k9-ragged0-scale0-g8 | e4m3 | 5.632 | 5.632 | 1.0000 |
| h8-m4096-n4096-k20-ragged1-scale0-g4 | bf16 | 25.841 | 25.856 | 0.9994
|
| h8-m4096-n4096-k20-ragged1-scale0-g4 | e4m3 | 24.576 | 24.576 | 1.0000
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | bf16 | 25.152 | 25.184 | 0.9987
|
| h8-m4096-n4096-k20-ragged1-scale0-g8 | e4m3 | 24.512 | 24.576 | 0.9974
|
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | bf16 | 22.496 | 22.496 |
1.0000 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g4 | e4m3 | 22.208 | 22.176 |
1.0014 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | bf16 | 26.816 | 26.816 |
1.0000 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven-g8 | e4m3 | 25.920 | 25.937 |
0.9994 |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | bf16 | 106.305 | 106.944 |
0.9940 |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | e4m3 | 101.536 | 101.472 |
1.0006 |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | bf16 | 106.944 | 106.912 |
1.0003 |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | e4m3 | 101.280 | 101.217 |
1.0006 |
| h8-m512-n1024-k2-ragged0-scale0-g4 | bf16 | 4.768 | 4.768 | 1.0000 |
| h8-m512-n1024-k2-ragged0-scale0-g4 | e4m3 | 4.127 | 4.128 | 0.9999 |
| h8-m512-n1024-k2-ragged0-scale0-g8 | bf16 | 4.576 | 4.576 | 1.0000 |
| h8-m512-n1024-k2-ragged0-scale0-g8 | e4m3 | 4.032 | 4.063 | 0.9924 |
| h8-m512-n4096-k12-ragged0-scale0-g4 | bf16 | 7.936 | 7.936 | 1.0000 |
| h8-m512-n4096-k12-ragged0-scale0-g4 | e4m3 | 7.328 | 7.328 | 1.0000 |
| h8-m512-n4096-k12-ragged0-scale0-g8 | bf16 | 7.712 | 7.712 | 1.0000 |
| h8-m512-n4096-k12-ragged0-scale0-g8 | e4m3 | 7.168 | 7.168 | 1.0000 |
| h8-m512-n4096-k8-ragged0-scale0-g4 | bf16 | 7.072 | 7.072 | 1.0000 |
| h8-m512-n4096-k8-ragged0-scale0-g4 | e4m3 | 6.240 | 6.240 | 1.0000 |
| h8-m512-n4096-k8-ragged0-scale0-g8 | bf16 | 6.688 | 6.688 | 1.0000 |
| h8-m512-n4096-k8-ragged0-scale0-g8 | e4m3 | 6.048 | 6.048 | 1.0000 |
| h8-m512-n512-k1-ragged0-scale0-g4 | bf16 | 3.744 | 3.744 | 1.0000 |
| h8-m512-n512-k1-ragged0-scale0-g4 | e4m3 | 3.264 | 3.265 | 0.9997 |
| h8-m512-n512-k1-ragged0-scale0-g8 | bf16 | 3.616 | 3.616 | 1.0000 |
| h8-m512-n512-k1-ragged0-scale0-g8 | e4m3 | 3.200 | 3.200 | 1.0000 |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g4 | bf16 | 10.432 | 10.464 |
0.9969 |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g4 | e4m3 | 9.248 | 9.248 |
1.0000 |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g8 | bf16 | 10.240 | 10.240 |
1.0000 |
| h8-m512-n8192-k24-ragged0-scale0-uneven-g8 | e4m3 | 8.928 | 8.896 |
1.0035 |

The other Cake variants of this kernel are unchanged here: the BF16 and
Sage-FP8 multi-head programs and the BF16 grouped-query programs. The
family runs only on sm_90a (Hopper), and other architectures have their
own Cake block-sparse attention backends.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated GPU kernel memory-access behavior. Existing data loading and
processing paths remain unchanged.
* **Compatibility**
  * Supported GPU architecture and CUDA requirements are unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4f14b25](https://github.com/flashinfer-ai/flashinfer/commit/4f14b25dc64fc10a66a715b0c165d464c4547aeb)

- **作者**: eigen
- **时间**: 2026-10-26T10:09:22Z
- **提交信息**: perf(cake_kda): two-CTA records of the context-parallel state walks, selected per launch (#7436)

The Cake packed KDA chunked training backend, for documents packed into
one sequence (head dim 128, chunk 64, 1 to 64 heads per call, BF16
q/k/v/beta/out, FP32 gate, FP32 recurrent state), has two Cake variants:
a single-device packed training forward and backward with a
saved-context and a checkpoint-replay backward, and a context-parallel
variant that splits the sequence over the ranks of a torch.distributed
group, passes state across ranks through affine state summaries in FP32,
supports three partition layouts (contiguous, zigzag, per-document
zigzag + ragged) with both backward modes, and includes the halo variant
of the width-4 causal conv1d + SiLU training backend. This PR delivers
the context-parallel variant with faster fragment state walks. Its four
fragment state walks (the forward and the backward state recurrence over
each fragment's chunk chain, each in an offset form that carries the
state from segment to segment and a tape form that writes the per-chunk
state tape) gain a two-CTA record beside the previous full-width record:
two CTAs per (segment, head), each over one 64-column half of the FP32
128 x 128 recurrent state and two resident per SM, in place of one
full-width CTA per (segment, head) and per SM. The two tape walks always
launch the two-CTA record (the full-width tape records remain as
test-only programs); the two offset walks select the record per launch
by a fit rule on the chain lengths, so launches of one or two long
chains per rank split and launches of many short chains keep the
full-width record. M, B, the states and the tapes keep FP32 storage;
every other kernel, the single-device path, the partition layouts, the
transfer walk and both backward modes are unchanged, and results are
bitwise identical to the previous version. The baseline is the previous
Cake version of the same kernels, the context-parallel variant as merged
in PR #7176, measured as an interleaved arm in the same sessions. Across
the 144 table rows (one per pack, CP degree, partition layout and
boundary), the speedup over that baseline ranges from 0.9906x to 1.0742x
in session 1, from 1.0143x to 1.0754x in session 2 and from 0.9906x to
1.0754x over both sessions. In both sessions, 102 of 144 rows are more
than 2 % faster than the previous version, 31 of 144 are within
0.98-1.02 and 0 of 144 are more than 2 % slower, and the remaining rows
are more than 2 % faster in one session and within 0.98-1.02 in the
other. Over both sessions, the 72 B3 rows (forward, checkpoint replay
and backward) range from 1.0158x to 1.0512x and the 72 B1 rows (module
forward) range from 0.9906x to 1.0754x.

All latencies are in ms on NVIDIA GB300 (sm_103a, 152 SMs) with CUDA
13.0, driver 580.159.03, NCCL 2.30.7 and PyTorch 2.14.1+cu130. Each
latency is the median over steady iterations of the slowest rank, with
the two arms interleaved in one process group, and each cell gives the
values of two independent sessions, s1 / s2; the speedup is previous
version ms / this PR ms in each session. CP2 and CP4 run on one node of
4 GPUs, CP8 on 2 nodes and CP16 on 4 nodes of one NVL72 domain. B1 is
the module forward (conv halo, conv, KDA state passing and recurrence,
communication included) and B3 is forward plus checkpoint replay plus
backward. The previous-version column is the previous Cake version of
the same kernels, the context-parallel variant as merged in PR #7176,
run as the interleaved arm with its full-width records for every walk
launch and every other kernel identical.

| pack | CP | layout | boundary | previous version ms (s1 / s2) | this
PR ms (s1 / s2) | speedup vs previous version (s1 / s2) |
|---|---|---|---|---|---|---|
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B1 = forward | 15.411 /
15.433 | 15.022 / 15.030 | 1.0259 / 1.0268 |
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 63.254 / 63.334 | 61.749 / 61.864 | 1.0244 / 1.0238
|
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B1 = forward | 15.545 /
15.576 | 15.223 / 15.257 | 1.0212 / 1.0209 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.753 / 63.761 | 62.546 / 62.615 | 1.0193 / 1.0183
|
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.565 / 15.646 | 15.231 / 15.311 | 1.0219 / 1.0219 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 63.750 / 63.883 | 62.556 /
62.739 | 1.0191 / 1.0182 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B1 = forward | 14.174 /
14.213 | 13.905 / 13.962 | 1.0193 / 1.0180 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 57.490 / 57.499 | 56.482 / 56.550 | 1.0178 / 1.0168
|
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B1 = forward | 14.649 /
14.679 | 14.367 / 14.414 | 1.0196 / 1.0184 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 59.374 / 59.381 | 58.276 / 58.325 | 1.0188 / 1.0181
|
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 14.426 / 14.437 | 13.982 / 13.991 | 1.0318 / 1.0319 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 58.823 / 58.879 | 57.165 /
57.181 | 1.0290 / 1.0297 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B1 = forward | 15.967 /
15.998 | 15.612 / 15.646 | 1.0227 / 1.0225 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 65.698 / 65.676 | 64.464 / 64.517 | 1.0191 / 1.0180
|
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B1 = forward | 15.794 /
15.819 | 15.485 / 15.500 | 1.0200 / 1.0206 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 65.341 / 65.357 | 64.098 / 64.176 | 1.0194 / 1.0184
|
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.549 / 16.591 | 16.216 / 16.274 | 1.0205 / 1.0195 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 67.540 / 67.638 | 66.264 /
66.335 | 1.0193 / 1.0196 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B1 = forward | 14.510 /
14.550 | 14.259 / 14.282 | 1.0176 / 1.0188 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 60.134 / 60.142 | 59.074 / 59.208 | 1.0179 / 1.0158
|
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B1 = forward | 14.680 /
14.758 | 14.385 / 14.400 | 1.0205 / 1.0249 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 60.417 / 60.540 | 59.207 / 59.332 | 1.0204 / 1.0204
|
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.240 / 15.299 | 14.910 / 14.992 | 1.0221 / 1.0205 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 62.256 / 62.414 | 61.034 /
61.273 | 1.0200 / 1.0186 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B1 = forward | 15.541 /
15.571 | 15.122 / 15.139 | 1.0277 / 1.0285 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 63.981 / 64.008 | 62.515 / 62.641 | 1.0235 / 1.0218
|
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B1 = forward | 15.426 /
15.509 | 15.113 / 15.177 | 1.0207 / 1.0219 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.827 / 63.838 | 62.587 / 62.677 | 1.0198 / 1.0185
|
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.966 / 16.011 | 15.638 / 15.726 | 1.0210 / 1.0181 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 65.373 / 65.434 | 64.158 /
64.227 | 1.0189 / 1.0188 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B1 = forward | 15.559 /
15.580 | 15.216 / 15.224 | 1.0225 / 1.0234 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 63.557 / 63.499 | 62.230 / 62.293 | 1.0213 / 1.0194
|
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B1 = forward | 15.771 /
15.828 | 15.448 / 15.480 | 1.0209 / 1.0225 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 64.429 / 64.430 | 63.020 / 63.101 | 1.0224 / 1.0211
|
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.214 / 16.280 | 15.731 / 15.770 | 1.0307 / 1.0323 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 66.157 / 66.246 | 64.234 /
64.401 | 1.0299 / 1.0286 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B1 = forward | 8.045 /
8.034 | 7.828 / 7.831 | 1.0277 / 1.0259 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 32.500 / 32.489 | 31.819 / 31.812 | 1.0214 / 1.0213
|
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B1 = forward | 8.175 / 8.172
| 8.020 / 8.033 | 1.0193 / 1.0173 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 32.997 / 32.991 | 32.377 / 32.394 | 1.0191 / 1.0184
|
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.045 / 8.052 | 7.795 / 7.794 | 1.0321 / 1.0331 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 32.731 / 32.728 | 31.926 /
31.903 | 1.0252 / 1.0259 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B1 = forward | 7.427 /
7.421 | 7.278 / 7.293 | 1.0205 / 1.0176 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 29.611 / 29.613 | 29.076 / 29.084 | 1.0184 / 1.0182
|
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B1 = forward | 7.552 / 7.548
| 7.394 / 7.403 | 1.0214 / 1.0196 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 30.266 / 30.260 | 29.708 / 29.709 | 1.0188 / 1.0185
|
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 7.504 / 7.528 | 7.274 / 7.253 | 1.0316 / 1.0379 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 30.278 / 30.262 | 29.396 /
29.382 | 1.0300 / 1.0300 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B1 = forward | 8.312 /
8.314 | 8.111 / 8.115 | 1.0248 / 1.0245 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.889 / 33.890 | 33.160 / 33.156 | 1.0220 / 1.0221
|
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B1 = forward | 8.544 / 8.547
| 8.366 / 8.373 | 1.0213 / 1.0208 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.512 / 34.500 | 33.892 / 33.851 | 1.0183 / 1.0192
|
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.466 / 8.458 | 8.268 / 8.274 | 1.0239 / 1.0222 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.445 / 34.434 | 33.754 /
33.754 | 1.0205 / 1.0201 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B1 = forward | 7.893 /
7.900 | 7.769 / 7.753 | 1.0160 / 1.0190 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 31.556 / 31.550 | 31.029 / 30.991 | 1.0170 / 1.0180
|
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B1 = forward | 7.921 / 7.923
| 7.736 / 7.721 | 1.0239 / 1.0262 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 31.873 / 31.864 | 31.242 / 31.240 | 1.0202 / 1.0200
|
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.066 / 8.076 | 7.914 / 7.928 | 1.0192 / 1.0187 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 32.345 / 32.363 | 31.761 /
31.737 | 1.0184 / 1.0197 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B1 = forward | 8.122 /
8.140 | 7.912 / 7.924 | 1.0265 / 1.0273 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.008 / 33.039 | 32.320 / 32.346 | 1.0213 / 1.0214
|
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B1 = forward | 8.348 / 8.379
| 8.182 / 8.209 | 1.0203 / 1.0207 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 33.748 / 33.797 | 33.147 / 33.178 | 1.0181 / 1.0187
|
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.194 / 8.239 | 8.020 / 8.035 | 1.0217 / 1.0254 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.531 / 33.589 | 32.799 /
32.836 | 1.0223 / 1.0229 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B1 = forward | 8.091 /
8.115 | 7.948 / 7.985 | 1.0180 / 1.0163 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 32.578 / 32.596 | 32.033 / 32.057 | 1.0170 / 1.0168
|
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B1 = forward | 8.182 / 8.206
| 8.042 / 8.043 | 1.0174 / 1.0203 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 32.940 / 32.998 | 32.391 / 32.416 | 1.0169 / 1.0180
|
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.399 / 8.433 | 8.146 / 8.164 | 1.0311 / 1.0329 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.761 / 33.819 | 32.767 /
32.792 | 1.0303 / 1.0313 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B1 = forward | 4.480 /
4.507 | 4.347 / 4.367 | 1.0306 / 1.0321 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.438 / 17.461 | 17.045 / 17.061 | 1.0231 / 1.0234
|
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B1 = forward | 4.448 / 4.461
| 4.257 / 4.266 | 1.0449 / 1.0457 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.453 / 17.480 | 16.669 / 16.680 | 1.0470 / 1.0480
|
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.505 / 4.544 | 4.397 / 4.416 | 1.0246 / 1.0290 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 17.793 / 17.809 | 17.391 /
17.381 | 1.0231 / 1.0246 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.191 /
4.180 | 4.089 / 4.099 | 1.0249 / 1.0198 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 16.060 / 16.036 | 15.732 / 15.753 | 1.0208 / 1.0180
|
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.122 / 4.132
| 3.918 / 3.940 | 1.0521 / 1.0487 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 15.990 / 16.006 | 15.283 / 15.303 | 1.0463 / 1.0459
|
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.133 / 4.141 | 3.967 / 3.985 | 1.0418 / 1.0391 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 16.158 / 16.136 | 15.636 /
15.651 | 1.0334 / 1.0310 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B1 = forward | 4.657 /
4.657 | 4.559 / 4.567 | 1.0215 / 1.0197 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.172 / 18.198 | 17.854 / 17.873 | 1.0178 / 1.0182
|
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B1 = forward | 4.642 / 4.659
| 4.441 / 4.445 | 1.0453 / 1.0481 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.264 / 18.288 | 17.449 / 17.490 | 1.0467 / 1.0456
|
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.727 / 4.726 | 4.623 / 4.629 | 1.0225 / 1.0210 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.702 / 18.676 | 18.301 /
18.288 | 1.0219 / 1.0212 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B1 = forward | 4.364 /
4.348 | 4.217 / 4.210 | 1.0349 / 1.0328 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 16.881 / 16.888 | 16.467 / 16.473 | 1.0251 / 1.0252
|
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B1 = forward | 4.312 / 4.320
| 4.353 / 4.259 | 0.9906 / 1.0143 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 16.856 / 16.857 | 16.113 / 16.126 | 1.0461 / 1.0453
|
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.326 / 4.322 | 4.192 / 4.196 | 1.0320 / 1.0300 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 16.982 / 16.986 | 16.539 /
16.543 | 1.0268 / 1.0268 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B1 = forward | 4.576 /
4.637 | 4.471 / 4.472 | 1.0235 / 1.0369 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.781 / 17.759 | 17.438 / 17.428 | 1.0197 / 1.0190
|
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B1 = forward | 4.554 / 4.554
| 4.355 / 4.361 | 1.0457 / 1.0443 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.879 / 17.887 | 17.098 / 17.087 | 1.0457 / 1.0468
|
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.679 / 4.696 | 4.585 / 4.542 | 1.0205 / 1.0339 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.548 / 18.563 | 18.130 /
18.056 | 1.0231 / 1.0281 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.493 /
4.506 | 4.400 / 4.410 | 1.0211 / 1.0218 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.476 / 17.470 | 17.174 / 17.139 | 1.0176 / 1.0193
|
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.454 / 4.463
| 4.253 / 4.256 | 1.0473 / 1.0486 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.459 / 17.462 | 16.691 / 16.677 | 1.0460 / 1.0471
|
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.507 / 4.468 | 4.367 / 4.331 | 1.0321 / 1.0316 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 17.769 / 17.736 | 17.250 /
17.208 | 1.0301 / 1.0307 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B1 = forward | 2.658 /
2.667 | 2.478 / 2.480 | 1.0726 / 1.0754 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.634 / 9.631 | 9.165 / 9.165 | 1.0512 /
1.0508 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B1 = forward | 2.577 / 2.591
| 2.475 / 2.481 | 1.0412 / 1.0443 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.498 / 9.538 | 9.101 / 9.096 | 1.0436 / 1.0486 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.823 / 2.769 | 2.682 / 2.697 | 1.0526 / 1.0267 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.098 / 10.108 | 9.865 / 9.893
| 1.0236 / 1.0217 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.481 /
2.470 | 2.386 / 2.370 | 1.0398 / 1.0422 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 8.896 / 8.876 | 8.538 / 8.544 | 1.0419 /
1.0389 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.450 / 2.416
| 2.324 / 2.321 | 1.0542 / 1.0409 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 8.779 / 8.780 | 8.427 / 8.421 | 1.0418 / 1.0426 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.507 / 2.496 | 2.425 / 2.413 | 1.0338 / 1.0344 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 9.321 / 9.275 | 9.013 / 9.004 |
1.0342 / 1.0301 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B1 = forward | 2.746 /
2.749 | 2.640 / 2.631 | 1.0402 / 1.0448 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.022 / 10.019 | 9.623 / 9.623 | 1.0415
/ 1.0412 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B1 = forward | 2.692 / 2.690
| 2.576 / 2.568 | 1.0450 / 1.0475 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.895 / 9.916 | 9.513 / 9.495 | 1.0402 / 1.0443 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.950 / 2.940 | 2.879 / 2.861 | 1.0247 / 1.0276 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.851 / 10.842 | 10.633 /
10.624 | 1.0205 / 1.0205 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B1 = forward | 2.592 /
2.593 | 2.413 / 2.414 | 1.0742 / 1.0742 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.331 / 9.316 | 9.006 / 8.866 | 1.0361 /
1.0508 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B1 = forward | 2.543 / 2.539
| 2.452 / 2.431 | 1.0371 / 1.0444 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.327 / 9.284 | 8.901 / 8.880 | 1.0479 / 1.0455 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.671 / 2.672 | 2.595 / 2.597 | 1.0293 / 1.0289 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 9.784 / 9.808 | 9.552 / 9.545 |
1.0243 / 1.0276 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B1 = forward | 2.700 /
2.708 | 2.631 / 2.586 | 1.0262 / 1.0472 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.849 / 9.825 | 9.393 / 9.400 | 1.0485 /
1.0452 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B1 = forward | 2.635 / 2.629
| 2.521 / 2.524 | 1.0452 / 1.0416 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.680 / 9.701 | 9.281 / 9.272 | 1.0430 / 1.0463 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.858 / 2.859 | 2.794 / 2.783 | 1.0229 / 1.0273 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.518 / 10.507 | 10.280 /
10.292 | 1.0232 / 1.0209 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.651 /
2.634 | 2.535 / 2.553 | 1.0458 / 1.0317 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.582 / 9.591 | 9.187 / 9.194 | 1.0430 /
1.0432 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.579 / 2.588
| 2.481 / 2.481 | 1.0395 / 1.0431 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.510 / 9.497 | 9.093 / 9.124 | 1.0459 / 1.0409 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.725 / 2.656 | 2.593 / 2.570 | 1.0509 / 1.0335 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.040 / 9.990 | 9.738 / 9.692
| 1.0310 / 1.0307 |

The kernel's other Cake variant is the single-device packed training
forward and backward with saved-context and checkpoint-replay backward,
and the family ships on sm_100a, sm_103a and sm_107a, with the two-CTA
records built for all three.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added automatic, full-width, and split walk options for KDA training,
with selection based on workload characteristics.
  - Added training kernel variants for additional GPU architectures.
- **Bug Fixes**
- Improved handling of oversized tensor dimensions and stride
calculations by reporting errors instead of allowing integer overflow.
  - Corrected panel indexing in a training kernel’s data-loading path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9e656ab](https://github.com/flashinfer-ai/flashinfer/commit/9e656abf0229df4cca7fdf555ae161bf33c00f4c)

- **作者**: eigen
- **时间**: 2026-10-26T10:09:13Z
- **提交信息**: perf(cake_minimax_h3): faster NVFP4 pre-attention on SM100 / SM103 (#7434)

The kernel behind `MiniMaxH3Nvfp4PreAttention`
(`flashinfer.cake_minimax_h3`) is the MiniMax-H3 fused pre-attention
with NVFP4 input. It has two stages: a norm stage (RMSNorm, AdaLN, NVFP4
quantize) and an NVFP4 QKV GEMM with a fused epilogue (Q/K RMSNorm, NeoX
RoPE, destination-major pack). It has 4 variants: 2 output formats
(`out_format="nvfp4"`, the default, and `out_format="e4m3"`) on 2
architectures (sm_100a and sm_103a). This PR delivers all 4 variants on
sm_100a and sm_103a, with a faster norm stage and a lower-overhead
launch. The baseline is the previous Cake version of the kernel, which
is the current FlashInfer route of this entry point. On GB300 the
speedup is 1.0257x to 1.1198x with nvfp4 output and 1.0274x to 1.1140x
with e4m3 output. On GB200 it is 1.0010x to 1.0526x with nvfp4 output
and 1.0139x to 1.0603x with e4m3 output.

**NVIDIA GB300, sm_103a, CUDA 13.4 toolkit, PyTorch cu130, power limit
1400 W.** The tables show GPU kernel time per operator call, which is
the busy time of the call's kernels with launch gaps excluded. Each
implementation is timed in its own back-to-back runs, interleaved with
the other, with a cold L2. M is the number of tokens per destination and
P is the number of destinations, so M x P is the step's total token
count.

`out_format="nvfp4"` (default)

| M | P | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|
| 33472 | 1 | 1.29891 | 1.24192 | 1.0458x |
| 16736 | 2 | 0.65009 | 0.61368 | 1.0591x |
| 8368 | 4 | 0.33473 | 0.30630 | 1.0928x |
| 4184 | 8 | 0.18267 | 0.16354 | 1.1170x |
| 38592 | 1 | 1.46108 | 1.42450 | 1.0257x |
| 19296 | 2 | 0.73672 | 0.70122 | 1.0506x |
| 9648 | 4 | 0.37759 | 0.35044 | 1.0775x |
| 4824 | 8 | 0.20148 | 0.18114 | 1.1123x |
| 48768 | 1 | 1.88025 | 1.81416 | 1.0362x |
| 24384 | 2 | 0.93838 | 0.88784 | 1.0565x |
| 12192 | 4 | 0.49081 | 0.44666 | 1.0988x |
| 6096 | 8 | 0.24813 | 0.22159 | 1.1198x |
| 58944 | 1 | 2.27480 | 2.20588 | 1.0309x |
| 29472 | 2 | 1.12672 | 1.08723 | 1.0360x |
| 14736 | 4 | 0.57390 | 0.53497 | 1.0726x |
| 7368 | 8 | 0.29367 | 0.26569 | 1.1053x |
| 74240 | 1 | 2.87275 | 2.77780 | 1.0335x |
| 37120 | 2 | 1.42200 | 1.37255 | 1.0356x |
| 18560 | 4 | 0.71675 | 0.66819 | 1.0710x |
| 9280 | 8 | 0.36550 | 0.33922 | 1.0774x |
| 109952 | 1 | 4.28667 | 4.13776 | 1.0357x |
| 54976 | 2 | 2.11720 | 2.04456 | 1.0352x |
| 27488 | 4 | 1.05377 | 1.01598 | 1.0372x |
| 13744 | 8 | 0.53816 | 0.49578 | 1.0855x |
| 32640 | 1 | 1.25028 | 1.20922 | 1.0335x |

`out_format="e4m3"`

| M | P | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|
| 33472 | 1 | 1.29045 | 1.23146 | 1.0475x |
| 16736 | 2 | 0.64738 | 0.61130 | 1.0589x |
| 8368 | 4 | 0.33137 | 0.30474 | 1.0874x |
| 4184 | 8 | 0.18114 | 0.16294 | 1.1117x |
| 38592 | 1 | 1.45865 | 1.41559 | 1.0304x |
| 19296 | 2 | 0.73734 | 0.69884 | 1.0543x |
| 9648 | 4 | 0.37399 | 0.34797 | 1.0748x |
| 4824 | 8 | 0.20003 | 0.18102 | 1.1050x |
| 48768 | 1 | 1.85796 | 1.80178 | 1.0311x |
| 24384 | 2 | 0.93276 | 0.88334 | 1.0557x |
| 12192 | 4 | 0.48640 | 0.44346 | 1.0968x |
| 6096 | 8 | 0.24611 | 0.22092 | 1.1140x |
| 58944 | 1 | 2.24683 | 2.18361 | 1.0274x |
| 29472 | 2 | 1.12254 | 1.08176 | 1.0373x |
| 14736 | 4 | 0.56934 | 0.52962 | 1.0750x |
| 7368 | 8 | 0.29026 | 0.26459 | 1.0970x |
| 74240 | 1 | 2.84316 | 2.76080 | 1.0298x |
| 37120 | 2 | 1.40642 | 1.36453 | 1.0307x |
| 18560 | 4 | 0.71497 | 0.66562 | 1.0741x |
| 9280 | 8 | 0.36242 | 0.33813 | 1.0718x |
| 109952 | 1 | 4.23390 | 4.10726 | 1.0308x |
| 54976 | 2 | 2.10774 | 2.03639 | 1.0350x |
| 27488 | 4 | 1.04696 | 1.00509 | 1.0411x |
| 13744 | 8 | 0.53546 | 0.49516 | 1.0814x |
| 32640 | 1 | 1.23582 | 1.19494 | 1.0342x |

**NVIDIA GB200, sm_100a, CUDA 13.4 toolkit, PyTorch cu130, power limit
1200 W.** The tables show GPU kernel time per operator call, which is
the busy time of the call's kernels with launch gaps excluded. Each
implementation is timed in its own back-to-back runs, interleaved with
the other, with a cold L2. M is the number of tokens per destination and
P is the number of destinations, so M x P is the step's total token
count.

`out_format="nvfp4"` (default)

| M | P | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|
| 33472 | 1 | 1.64018 | 1.61574 | 1.0151x |
| 16736 | 2 | 0.79794 | 0.79275 | 1.0066x |
| 8368 | 4 | 0.40169 | 0.38686 | 1.0383x |
| 4184 | 8 | 0.21819 | 0.20736 | 1.0520x |
| 38592 | 1 | 1.87433 | 1.84895 | 1.0131x |
| 19296 | 2 | 0.91494 | 0.91400 | 1.0010x |
| 9648 | 4 | 0.45371 | 0.44143 | 1.0278x |
| 4824 | 8 | 0.23946 | 0.22835 | 1.0487x |
| 48768 | 1 | 2.38890 | 2.33906 | 1.0213x |
| 24384 | 2 | 1.16577 | 1.16124 | 1.0036x |
| 12192 | 4 | 0.59287 | 0.56603 | 1.0466x |
| 6096 | 8 | 0.29787 | 0.28446 | 1.0471x |
| 58944 | 1 | 2.91074 | 2.84691 | 1.0224x |
| 29472 | 2 | 1.40755 | 1.40012 | 1.0052x |
| 14736 | 4 | 0.70642 | 0.68445 | 1.0316x |
| 7368 | 8 | 0.35706 | 0.33909 | 1.0526x |
| 74240 | 1 | 3.67492 | 3.58790 | 1.0233x |
| 37120 | 2 | 1.79969 | 1.77314 | 1.0139x |
| 18560 | 4 | 0.88206 | 0.87838 | 1.0042x |
| 9280 | 8 | 0.44696 | 0.43106 | 1.0369x |
| 109952 | 1 | 5.47269 | 5.32046 | 1.0286x |
| 54976 | 2 | 2.68426 | 2.63019 | 1.0204x |
| 27488 | 4 | 1.31710 | 1.31217 | 1.0036x |
| 13744 | 8 | 0.66650 | 0.63749 | 1.0428x |
| 32640 | 1 | 1.59298 | 1.56399 | 1.0185x |

`out_format="e4m3"`

| M | P | baseline (ms) | this PR (ms) | speedup |
|---:|---:|---:|---:|---:|
| 33472 | 1 | 1.64140 | 1.61220 | 1.0168x |
| 16736 | 2 | 0.80451 | 0.79316 | 1.0139x |
| 8368 | 4 | 0.41028 | 0.38802 | 1.0573x |
| 4184 | 8 | 0.21561 | 0.20642 | 1.0445x |
| 38592 | 1 | 1.87140 | 1.83778 | 1.0142x |
| 19296 | 2 | 0.92851 | 0.91020 | 1.0201x |
| 9648 | 4 | 0.46614 | 0.44255 | 1.0526x |
| 4824 | 8 | 0.23898 | 0.22794 | 1.0485x |
| 48768 | 1 | 2.39183 | 2.33108 | 1.0260x |
| 24384 | 2 | 1.17793 | 1.15416 | 1.0206x |
| 12192 | 4 | 0.59793 | 0.56655 | 1.0554x |
| 6096 | 8 | 0.30162 | 0.28518 | 1.0576x |
| 58944 | 1 | 2.88703 | 2.79906 | 1.0314x |
| 29472 | 2 | 1.41523 | 1.38940 | 1.0186x |
| 14736 | 4 | 0.71460 | 0.68263 | 1.0468x |
| 7368 | 8 | 0.35941 | 0.33898 | 1.0603x |
| 74240 | 1 | 3.63677 | 3.55390 | 1.0233x |
| 37120 | 2 | 1.79984 | 1.76592 | 1.0146x |
| 18560 | 4 | 0.88683 | 0.87164 | 1.0167x |
| 9280 | 8 | 0.45191 | 0.43072 | 1.0492x |
| 109952 | 1 | 5.43586 | 5.29642 | 1.0237x |
| 54976 | 2 | 2.69126 | 2.61050 | 1.0296x |
| 27488 | 4 | 1.31783 | 1.29938 | 1.0142x |
| 13744 | 8 | 0.66496 | 0.63618 | 1.0452x |
| 32640 | 1 | 1.58382 | 1.55758 | 1.0140x |

The other Cake variants of this pre-attention have separate entry
points: they take BF16 or MXFP8 input on sm_100a / sm_103a, or FP8 E4M3
or NVFP4 input on sm_120a, and the family ships on sm_100a, sm_103a and
sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* NVFP4 pre-attention now supports writing output scale factors to the
provided scale buffer.
* **Bug Fixes**
* Prepared operations now run on the output tensor’s device and its
current CUDA stream, including when another device is active.
* Preparation rejects output scale buffers that are not 8-byte aligned.
* Invalid descriptor calculations now report errors instead of
proceeding with overflowing arithmetic.
* **Documentation**
  * Clarified the output scale buffer’s alignment requirement.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a8d23b2](https://github.com/flashinfer-ai/flashinfer/commit/a8d23b20bfc4f4660db2bb80aa0e43c1d13245fe)

- **作者**: eigen
- **时间**: 2026-10-26T10:05:22Z
- **提交信息**: perf(cake_rmsnorm): staged dweight reduce and chunk tapers in the backward pairs on SM100 / SM103 / SM107 (#7417)

`cake_rmsnorm_train` is Cake's RMSNorm training kernel: one data type
(BF16 activations and weight, FP32 `rstd` and deterministic FP32
`dweight`) in four variants, plain and residual-fused, each forward and
backward. This PR changes the backward pairs of both the plain and the
residual-fused variant on sm_100a, sm_103a and sm_107a. The baseline is
the previous Cake version, the shipped FlashInfer build of PR #7200. The
new backward pair's speedup over the previous Cake version, for the
plain variant at T >= 14928 and for the residual-fused variant at every
measured T, is:

- sm_103a: 1.00–1.07x at H = 512, 1.00–1.02x at H = 1536, 0.99–1.01x at
H = 2048, 1.00–1.04x at H = 4096, 0.99–1.01x at H = 6144; 1.00–1.01x for
the residual-fused variant
- sm_100a: 1.00–1.01x at H = 512, 1.00–1.07x at H = 1536, 1.00–1.05x at
H = 2048, 1.00–1.01x at H = 4096, 1.00–1.01x at H = 6144; 1.00–1.02x for
the residual-fused variant
- sm_107a: 1.02–1.09x at H = 512, 1.05–1.10x at H = 1536, 1.13–1.18x at
H = 2048, 1.03–1.07x at H = 4096, 1.04–1.05x at H = 6144; 0.99–1.01x for
the residual-fused variant

The backward pair has two kernels under programmatic dependent launch: a
chunk-claiming main kernel and a `dweight` reduce kernel. On the (H, T)
windows whose programs this PR replaces, the `dweight` reduce runs
deeper waves: on sm_107a a staged slab reduction (8 or 16 trips per
wave) instead of the register-resident form, on sm_100a and sm_103a
deeper tree waves. Each main program now carries its own chunk taper,
and the host cuts the chunk tables with the same tapers. The large-row
windows stop two halving rounds early, and the small and mid windows cut
the tail finer, so fewer, fuller chunks reach the reduce. Several
windows move to main programs that drop the row cascade, use row-group
issuers and group sync, or use a store-side dependent-launch trigger. On
sm_107a, the H = 4096 mid window (1024 < T <= 4096) reduces over 1024
threads, twice as many as the main kernel, and the H = 512 pair gets its
own sm_107a programs. `dweight` stays deterministic (bitwise identical
across launch grids and repeats), but its summation order differs from
#7200's on the replaced windows because the chunk tapers and reduce
geometries changed.

Both versions run in the same process on the same GPU and are compiled
with CUDA 13.4.92 through the same FlashInfer build path. Latencies are
CUPTI kernel-active times for a T x H input (T rows of hidden size H),
with cold L2 before every launch. A kernel-active time is the union of
the call's kernel intervals, so a dependent-launch overlap counts once.
Each latency is the median of 3 counterbalanced paired groups. Speedup
is previous / new latency. Below 1.000x the new version is slower; the
lowest speedup is 0.987x on sm_103a, 0.988x on sm_100a and 0.981x on
sm_107a. In the Pass column, `bwd` is the backward pair of the plain
variant and `bwd (residual)` is the backward pair of the residual-fused
variant. Forward programs are unchanged and therefore not listed.

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4.92 (previous Cake: the
shipped FlashInfer build of #7200; new Cake: this PR's build; same
process, same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 6.03 | 6.03 | 1.000x |
| 512 | 1024 | bwd | 6.42 | 6.48 | 0.990x |
| 512 | 4096 | bwd | 10.35 | 10.38 | 0.997x |
| 512 | 14928 | bwd | 16.19 | 15.36 | 1.054x |
| 512 | 15288 | bwd | 16.38 | 15.30 | 1.071x |
| 512 | 15566 | bwd | 16.32 | 15.36 | 1.062x |
| 512 | 15590 | bwd | 16.27 | 15.38 | 1.058x |
| 512 | 16114 | bwd | 16.45 | 15.49 | 1.062x |
| 512 | 16132 | bwd | 16.50 | 15.49 | 1.065x |
| 512 | 16164 | bwd | 16.45 | 15.52 | 1.060x |
| 512 | 16263 | bwd | 16.50 | 15.55 | 1.061x |
| 512 | 32768 | bwd | 23.01 | 23.01 | 1.000x |
| 512 | 65536 | bwd | 40.40 | 39.10 | 1.033x |
| 1536 | 256 | bwd | 6.24 | 6.24 | 1.000x |
| 1536 | 1024 | bwd | 8.27 | 8.30 | 0.996x |
| 1536 | 4096 | bwd | 15.23 | 13.79 | 1.104x |
| 1536 | 14928 | bwd | 29.78 | 29.63 | 1.005x |
| 1536 | 15288 | bwd | 31.42 | 30.86 | 1.018x |
| 1536 | 15566 | bwd | 31.63 | 31.12 | 1.016x |
| 1536 | 15590 | bwd | 31.60 | 31.02 | 1.019x |
| 1536 | 16114 | bwd | 31.94 | 31.36 | 1.018x |
| 1536 | 16132 | bwd | 31.82 | 31.38 | 1.014x |
| 1536 | 16164 | bwd | 32.08 | 31.65 | 1.014x |
| 1536 | 16263 | bwd | 32.06 | 31.46 | 1.019x |
| 1536 | 32768 | bwd | 54.53 | 53.60 | 1.017x |
| 1536 | 65536 | bwd | 99.62 | 99.12 | 1.005x |
| 2048 | 256 | bwd | 7.44 | 7.47 | 0.996x |
| 2048 | 1024 | bwd | 9.41 | 9.39 | 1.002x |
| 2048 | 4096 | bwd | 17.26 | 17.01 | 1.015x |
| 2048 | 14928 | bwd | 36.10 | 36.43 | 0.991x |
| 2048 | 15288 | bwd | 37.94 | 37.76 | 1.005x |
| 2048 | 15566 | bwd | 38.05 | 37.90 | 1.004x |
| 2048 | 15590 | bwd | 37.71 | 37.90 | 0.995x |
| 2048 | 16114 | bwd | 39.15 | 39.38 | 0.994x |
| 2048 | 16132 | bwd | 39.49 | 39.47 | 1.000x |
| 2048 | 16164 | bwd | 39.58 | 39.92 | 0.992x |
| 2048 | 16263 | bwd | 39.31 | 39.14 | 1.004x |
| 2048 | 32768 | bwd | 69.55 | 69.01 | 1.008x |
| 2048 | 65536 | bwd | 127.84 | 127.57 | 1.002x |
| 4096 | 256 | bwd | 7.34 | 7.30 | 1.007x |
| 4096 | 1024 | bwd | 13.34 | 12.34 | 1.082x |
| 4096 | 4096 | bwd | 26.85 | 24.10 | 1.114x |
| 4096 | 14928 | bwd | 69.78 | 68.50 | 1.019x |
| 4096 | 15288 | bwd | 69.31 | 68.86 | 1.007x |
| 4096 | 15566 | bwd | 70.42 | 70.50 | 0.999x |
| 4096 | 15590 | bwd | 70.46 | 70.30 | 1.002x |
| 4096 | 16114 | bwd | 72.88 | 72.53 | 1.005x |
| 4096 | 16132 | bwd | 72.67 | 72.30 | 1.005x |
| 4096 | 16164 | bwd | 72.45 | 72.43 | 1.000x |
| 4096 | 16263 | bwd | 72.99 | 72.70 | 1.004x |
| 4096 | 32768 | bwd | 133.95 | 134.40 | 0.997x |
| 4096 | 65536 | bwd | 259.15 | 250.18 | 1.036x |
| 6144 | 256 | bwd | 8.78 | 8.62 | 1.019x |
| 6144 | 1024 | bwd | 16.69 | 16.80 | 0.993x |
| 6144 | 4096 | bwd | 33.34 | 33.47 | 0.996x |
| 6144 | 14928 | bwd | 93.09 | 94.00 | 0.990x |
| 6144 | 15288 | bwd | 95.92 | 96.21 | 0.997x |
| 6144 | 15566 | bwd | 97.14 | 98.38 | 0.987x |
| 6144 | 15590 | bwd | 97.17 | 97.50 | 0.997x |
| 6144 | 16114 | bwd | 99.68 | 100.27 | 0.994x |
| 6144 | 16132 | bwd | 99.68 | 99.79 | 0.999x |
| 6144 | 16164 | bwd | 99.31 | 99.81 | 0.995x |
| 6144 | 16263 | bwd | 99.78 | 99.22 | 1.006x |
| 6144 | 32768 | bwd | 199.92 | 199.78 | 1.001x |
| 6144 | 65536 | bwd | 380.45 | 380.67 | 0.999x |
| 6144 | 256 | bwd (residual) | 9.73 | 9.74 | 0.998x |
| 6144 | 1024 | bwd (residual) | 20.32 | 20.35 | 0.998x |
| 6144 | 4096 | bwd (residual) | 48.19 | 47.86 | 1.007x |
| 6144 | 14928 | bwd (residual) | 138.18 | 138.27 | 0.999x |
| 6144 | 15288 | bwd (residual) | 140.74 | 140.72 | 1.000x |
| 6144 | 15566 | bwd (residual) | 144.42 | 144.46 | 1.000x |
| 6144 | 15590 | bwd (residual) | 144.70 | 144.70 | 1.000x |
| 6144 | 16114 | bwd (residual) | 147.89 | 147.70 | 1.001x |
| 6144 | 16132 | bwd (residual) | 147.95 | 148.06 | 0.999x |
| 6144 | 16164 | bwd (residual) | 148.02 | 148.30 | 0.998x |
| 6144 | 16263 | bwd (residual) | 148.91 | 148.86 | 1.000x |
| 6144 | 32768 | bwd (residual) | 285.63 | 285.55 | 1.000x |
| 6144 | 65536 | bwd (residual) | 557.04 | 556.91 | 1.000x |

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4.92 (previous Cake: the
shipped FlashInfer build of #7200; new Cake: this PR's build; same
process, same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 5.84 | 5.82 | 1.003x |
| 512 | 1024 | bwd | 6.43 | 6.43 | 1.000x |
| 512 | 4096 | bwd | 10.21 | 10.22 | 0.998x |
| 512 | 14928 | bwd | 16.75 | 16.58 | 1.011x |
| 512 | 15288 | bwd | 16.94 | 16.83 | 1.007x |
| 512 | 15566 | bwd | 17.13 | 17.06 | 1.005x |
| 512 | 15590 | bwd | 17.10 | 17.15 | 0.997x |
| 512 | 16114 | bwd | 17.55 | 17.60 | 0.997x |
| 512 | 16132 | bwd | 17.57 | 17.57 | 1.000x |
| 512 | 16164 | bwd | 17.60 | 17.62 | 0.999x |
| 512 | 16263 | bwd | 17.66 | 17.60 | 1.004x |
| 512 | 32768 | bwd | 24.58 | 24.29 | 1.012x |
| 512 | 65536 | bwd | 41.01 | 40.45 | 1.014x |
| 1536 | 256 | bwd | 6.94 | 6.94 | 1.000x |
| 1536 | 1024 | bwd | 8.38 | 8.38 | 1.000x |
| 1536 | 4096 | bwd | 16.02 | 14.59 | 1.098x |
| 1536 | 14928 | bwd | 32.02 | 31.12 | 1.029x |
| 1536 | 15288 | bwd | 31.79 | 29.79 | 1.067x |
| 1536 | 15566 | bwd | 32.22 | 30.43 | 1.059x |
| 1536 | 15590 | bwd | 32.41 | 30.30 | 1.070x |
| 1536 | 16114 | bwd | 33.04 | 31.26 | 1.057x |
| 1536 | 16132 | bwd | 33.09 | 30.99 | 1.068x |
| 1536 | 16164 | bwd | 33.15 | 31.09 | 1.066x |
| 1536 | 16263 | bwd | 33.14 | 31.07 | 1.066x |
| 1536 | 32768 | bwd | 56.66 | 55.14 | 1.028x |
| 1536 | 65536 | bwd | 105.78 | 105.94 | 0.998x |
| 2048 | 256 | bwd | 7.10 | 7.10 | 1.000x |
| 2048 | 1024 | bwd | 9.22 | 9.28 | 0.993x |
| 2048 | 4096 | bwd | 17.69 | 17.63 | 1.004x |
| 2048 | 14928 | bwd | 38.40 | 37.66 | 1.020x |
| 2048 | 15288 | bwd | 38.72 | 37.71 | 1.027x |
| 2048 | 15566 | bwd | 39.42 | 38.27 | 1.030x |
| 2048 | 15590 | bwd | 39.42 | 38.18 | 1.033x |
| 2048 | 16114 | bwd | 40.26 | 39.42 | 1.021x |
| 2048 | 16132 | bwd | 40.45 | 39.49 | 1.024x |
| 2048 | 16164 | bwd | 40.51 | 39.34 | 1.030x |
| 2048 | 16263 | bwd | 41.76 | 39.76 | 1.050x |
| 2048 | 32768 | bwd | 72.45 | 72.72 | 0.996x |
| 2048 | 65536 | bwd | 130.48 | 130.38 | 1.001x |
| 4096 | 256 | bwd | 7.95 | 8.05 | 0.988x |
| 4096 | 1024 | bwd | 13.52 | 12.48 | 1.083x |
| 4096 | 4096 | bwd | 28.01 | 24.88 | 1.126x |
| 4096 | 14928 | bwd | 69.20 | 68.98 | 1.003x |
| 4096 | 15288 | bwd | 72.02 | 71.94 | 1.001x |
| 4096 | 15566 | bwd | 73.09 | 72.69 | 1.005x |
| 4096 | 15590 | bwd | 73.25 | 72.58 | 1.009x |
| 4096 | 16114 | bwd | 75.58 | 74.96 | 1.008x |
| 4096 | 16132 | bwd | 75.53 | 74.54 | 1.013x |
| 4096 | 16164 | bwd | 75.41 | 74.90 | 1.007x |
| 4096 | 16263 | bwd | 75.30 | 74.51 | 1.011x |
| 4096 | 32768 | bwd | 134.89 | 134.08 | 1.006x |
| 4096 | 65536 | bwd | 251.47 | 250.67 | 1.003x |
| 6144 | 256 | bwd | 9.47 | 9.54 | 0.993x |
| 6144 | 1024 | bwd | 16.80 | 16.77 | 1.002x |
| 6144 | 4096 | bwd | 33.78 | 33.38 | 1.012x |
| 6144 | 14928 | bwd | 95.21 | 94.90 | 1.003x |
| 6144 | 15288 | bwd | 98.19 | 97.92 | 1.003x |
| 6144 | 15566 | bwd | 99.12 | 98.96 | 1.002x |
| 6144 | 15590 | bwd | 99.04 | 98.72 | 1.003x |
| 6144 | 16114 | bwd | 101.92 | 101.25 | 1.007x |
| 6144 | 16132 | bwd | 102.34 | 101.47 | 1.009x |
| 6144 | 16164 | bwd | 102.30 | 101.94 | 1.004x |
| 6144 | 16263 | bwd | 104.93 | 104.17 | 1.007x |
| 6144 | 32768 | bwd | 205.76 | 205.17 | 1.003x |
| 6144 | 65536 | bwd | 392.32 | 392.00 | 1.001x |
| 6144 | 256 | bwd (residual) | 10.18 | 10.21 | 0.997x |
| 6144 | 1024 | bwd (residual) | 21.31 | 20.80 | 1.025x |
| 6144 | 4096 | bwd (residual) | 50.11 | 49.44 | 1.014x |
| 6144 | 14928 | bwd (residual) | 144.34 | 143.69 | 1.004x |
| 6144 | 15288 | bwd (residual) | 148.96 | 148.40 | 1.004x |
| 6144 | 15566 | bwd (residual) | 151.10 | 150.48 | 1.004x |
| 6144 | 15590 | bwd (residual) | 151.58 | 150.70 | 1.006x |
| 6144 | 16114 | bwd (residual) | 154.75 | 153.78 | 1.006x |
| 6144 | 16132 | bwd (residual) | 155.47 | 154.77 | 1.005x |
| 6144 | 16164 | bwd (residual) | 155.09 | 154.46 | 1.004x |
| 6144 | 16263 | bwd (residual) | 155.57 | 154.97 | 1.004x |
| 6144 | 32768 | bwd (residual) | 299.41 | 298.29 | 1.004x |
| 6144 | 65536 | bwd (residual) | 581.42 | 579.53 | 1.003x |

### NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4.92 (previous Cake: the
shipped FlashInfer build of #7200; new Cake: this PR's build; same
process, same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 5.47 | 5.41 | 1.012x |
| 512 | 1024 | bwd | 5.82 | 5.86 | 0.995x |
| 512 | 4096 | bwd | 8.38 | 7.78 | 1.078x |
| 512 | 14928 | bwd | 12.42 | 11.39 | 1.090x |
| 512 | 15288 | bwd | 12.51 | 11.49 | 1.089x |
| 512 | 15566 | bwd | 12.46 | 11.42 | 1.091x |
| 512 | 15590 | bwd | 12.51 | 11.46 | 1.092x |
| 512 | 16114 | bwd | 12.48 | 11.52 | 1.083x |
| 512 | 16132 | bwd | 12.45 | 11.50 | 1.082x |
| 512 | 16164 | bwd | 12.48 | 11.49 | 1.086x |
| 512 | 16263 | bwd | 12.51 | 11.46 | 1.092x |
| 512 | 32768 | bwd | 17.33 | 16.99 | 1.020x |
| 512 | 65536 | bwd | 26.77 | 25.18 | 1.063x |
| 1536 | 256 | bwd | 5.81 | 5.82 | 0.997x |
| 1536 | 1024 | bwd | 7.44 | 7.09 | 1.050x |
| 1536 | 4096 | bwd | 10.85 | 10.69 | 1.015x |
| 1536 | 14928 | bwd | 20.61 | 19.41 | 1.062x |
| 1536 | 15288 | bwd | 21.10 | 19.78 | 1.067x |
| 1536 | 15566 | bwd | 21.66 | 20.05 | 1.081x |
| 1536 | 15590 | bwd | 21.66 | 20.06 | 1.080x |
| 1536 | 16114 | bwd | 22.53 | 20.46 | 1.101x |
| 1536 | 16132 | bwd | 22.50 | 20.42 | 1.102x |
| 1536 | 16164 | bwd | 22.53 | 20.64 | 1.091x |
| 1536 | 16263 | bwd | 22.59 | 20.54 | 1.100x |
| 1536 | 32768 | bwd | 35.62 | 33.71 | 1.056x |
| 1536 | 65536 | bwd | 59.58 | 56.69 | 1.051x |
| 2048 | 256 | bwd | 6.05 | 5.95 | 1.016x |
| 2048 | 1024 | bwd | 8.46 | 7.33 | 1.155x |
| 2048 | 4096 | bwd | 13.09 | 11.26 | 1.162x |
| 2048 | 14928 | bwd | 25.57 | 22.59 | 1.132x |
| 2048 | 15288 | bwd | 26.27 | 22.74 | 1.156x |
| 2048 | 15566 | bwd | 26.08 | 23.09 | 1.130x |
| 2048 | 15590 | bwd | 26.11 | 23.04 | 1.133x |
| 2048 | 16114 | bwd | 27.60 | 23.62 | 1.169x |
| 2048 | 16132 | bwd | 27.68 | 23.54 | 1.176x |
| 2048 | 16164 | bwd | 27.68 | 23.66 | 1.170x |
| 2048 | 16263 | bwd | 27.76 | 23.73 | 1.170x |
| 2048 | 32768 | bwd | 44.54 | 39.20 | 1.136x |
| 2048 | 65536 | bwd | 77.97 | 68.26 | 1.142x |
| 4096 | 256 | bwd | 7.02 | 7.04 | 0.998x |
| 4096 | 1024 | bwd | 10.03 | 10.22 | 0.981x |
| 4096 | 4096 | bwd | 17.54 | 15.68 | 1.118x |
| 4096 | 14928 | bwd | 40.46 | 37.84 | 1.069x |
| 4096 | 15288 | bwd | 41.33 | 38.85 | 1.064x |
| 4096 | 15566 | bwd | 41.47 | 38.83 | 1.068x |
| 4096 | 15590 | bwd | 41.38 | 38.86 | 1.065x |
| 4096 | 16114 | bwd | 42.62 | 40.21 | 1.060x |
| 4096 | 16132 | bwd | 42.46 | 40.24 | 1.055x |
| 4096 | 16164 | bwd | 42.40 | 40.19 | 1.055x |
| 4096 | 16263 | bwd | 42.56 | 40.18 | 1.059x |
| 4096 | 32768 | bwd | 73.09 | 69.59 | 1.050x |
| 4096 | 65536 | bwd | 132.26 | 128.51 | 1.029x |
| 6144 | 256 | bwd | 8.21 | 8.32 | 0.987x |
| 6144 | 1024 | bwd | 11.76 | 11.42 | 1.029x |
| 6144 | 4096 | bwd | 23.47 | 22.53 | 1.042x |
| 6144 | 14928 | bwd | 55.01 | 52.80 | 1.042x |
| 6144 | 15288 | bwd | 56.24 | 53.81 | 1.045x |
| 6144 | 15566 | bwd | 57.02 | 54.51 | 1.046x |
| 6144 | 15590 | bwd | 56.93 | 54.34 | 1.048x |
| 6144 | 16114 | bwd | 58.38 | 55.79 | 1.046x |
| 6144 | 16132 | bwd | 58.46 | 55.94 | 1.045x |
| 6144 | 16164 | bwd | 58.46 | 55.89 | 1.046x |
| 6144 | 16263 | bwd | 58.50 | 56.13 | 1.042x |
| 6144 | 32768 | bwd | 105.02 | 100.35 | 1.047x |
| 6144 | 65536 | bwd | 197.65 | 190.58 | 1.037x |
| 6144 | 256 | bwd (residual) | 8.51 | 8.56 | 0.994x |
| 6144 | 1024 | bwd (residual) | 14.91 | 14.77 | 1.010x |
| 6144 | 4096 | bwd (residual) | 33.18 | 33.28 | 0.997x |
| 6144 | 14928 | bwd (residual) | 84.98 | 84.96 | 1.000x |
| 6144 | 15288 | bwd (residual) | 88.08 | 88.21 | 0.999x |
| 6144 | 15566 | bwd (residual) | 89.44 | 89.39 | 1.001x |
| 6144 | 15590 | bwd (residual) | 89.39 | 89.30 | 1.001x |
| 6144 | 16114 | bwd (residual) | 91.10 | 91.20 | 0.999x |
| 6144 | 16132 | bwd (residual) | 91.20 | 91.23 | 1.000x |
| 6144 | 16164 | bwd (residual) | 91.25 | 91.30 | 0.999x |
| 6144 | 16263 | bwd (residual) | 91.57 | 91.50 | 1.001x |
| 6144 | 32768 | bwd (residual) | 169.66 | 169.94 | 0.998x |
| 6144 | 65536 | bwd (residual) | 327.28 | 327.26 | 1.000x |

Cake ships this kernel in the four variants above (plain and
residual-fused, forward and backward, BF16 with FP32 `rstd` / `dweight`)
for sm_100a, sm_103a and sm_107a; there are no other data types or
layouts.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated RMSNorm training execution across supported CUDA
architectures, including revised work partitioning and gradient
reduction.
* Added per-kernel chunk tuning to better adapt training workloads to
different row counts.

* **Bug Fixes**
* Improved reliability when reusing backward workspaces across changing
batch sizes, including cases with residual gradients.

* **Tests**
* Expanded checks for chunk scheduling, workspace reuse, and
backward-result accuracy across varied workload sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [fdd121f](https://github.com/flashinfer-ai/flashinfer/commit/fdd121f46bfcc98369a1cb618424dbb761a077c3)

- **作者**: eigen
- **时间**: 2026-10-26T10:02:21Z
- **提交信息**: perf(cake_selective_state_update): P-split, TMA-ring and persistent decode programs on sm_100a and sm_103a (#7407)

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
This PR changes three of these variants on sm_100a (B200) and sm_103a
(GB300). For BF16-state single-token decode with head dim 64 (two heads
per 128-row program) or head dim 128, new programs split each 128-row
program head over 2 or 4 CTAs along the head dimension, so more, smaller
CTAs fill the GPU; the route picks them per architecture and SM count.
For short multi-token (speculative) decode with 1 or 2 tokens, 64 heads
and 8 groups, one new program streams the state through a ring of TMA
stages and another is a pass program without a proxy fence; the route
picks between them by batch. For z-gated BF16-state single-token decode
with head dim 128, a persistent program keeps two heads in flight per
CTA and is routed inside the measured batch x heads bands. Every other
shape keeps main's program. The baseline is the previous Cake version
(`backend="cake"` on main), over 122 shapes. On B200, 38 shapes take a
new program and run 1.002x to 1.159x faster; on GB300, 32 shapes take a
new program and run 1.001x to 1.093x faster. The other shapes run main's
program unchanged, and their ratios (0.991x to 1.009x on both GPUs) are
run-to-run noise between two builds of the same program.

*NVIDIA B200 (sm_100a, 148 SMs); PyTorch 2.14.1+cu130 with the CUDA
13.4.92 runtime; programs compiled with nvcc 13.4. Timer: CUPTI kernel
time with a cold L2; times are medians over 2 runs x 9 interleaved
rounds (us); speedup = main / this PR; the program column says whether
this PR routes the shape to a new program (`new`) or keeps main's
(`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.408 | 39.415 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 77.247 | 77.223 | 1.000x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 41.904 | 40.944 | 1.023x | new |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 39.504 | 39.488 | 1.000x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 41.968 | 41.040 | 1.023x | new |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.224 | 7.856 | 1.047x | new |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.408 | 39.439 | 0.999x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 156.622 | 156.174 | 1.003x | new |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 78.911 | 78.927 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 40.383 | 37.840 | 1.067x | new |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 44.863 | 41.328 | 1.086x | new |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.712 | 3.712 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1189.587 | 1184.204 | 1.005x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.816 |
2.816 | 1.000x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.976 |
2.976 | 1.000x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.192 |
3.184 | 1.003x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.800 |
3.808 | 0.998x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.808 |
3.808 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.728 | 3.744 | 0.996x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.720 | 4.736 | 0.997x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.016 | 6.016 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.624 | 6.624 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.912 |
3.920 | 0.998x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.968 |
4.976 | 0.998x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.208 |
6.207 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.848 |
6.848 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.224 | 7.840 | 1.049x | new |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.408 | 39.447 | 0.999x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 78.904 | 78.919 | 1.000x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 39.368 | 39.360 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 313.853 | 312.829 | 1.003x | new |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 77.344 | 77.336 | 1.000x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 40.264 | 37.992 | 1.060x | new |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 44.888 | 41.328 | 1.086x | new |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.712 | 3.712 | 1.000x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 39.568 | 39.584 | 1.000x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.816 | 2.816 | 1.000x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 4.128 | 4.128 |
1.000x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.184 | 3.176 | 1.003x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.808 | 3.784 | 1.006x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.808 | 3.808 | 1.000x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.712 | 3.712 |
1.000x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 4.128 |
4.128 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.104 | 3.088 | 1.005x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.104 | 3.104 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.616 | 3.616 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.616 | 3.616 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.312 | 4.896 | 1.085x | new |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 5.256 | 4.928 | 1.067x | new |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.152 | 7.168 | 0.998x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 7.120 | 7.104 | 1.002x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 11.544 | 10.816 | 1.067x |
new |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 11.552 | 11.032 | 1.047x | new |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 20.544 | 19.808 | 1.037x |
new |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 20.448 | 19.776 | 1.034x | new |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.624 | 39.616 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 39.639 | 39.648 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 79.168 | 78.935 | 1.003x |
new |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 79.207 | 79.031 | 1.002x |
new |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 157.022 | 156.399 | 1.004x |
new |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 157.246 | 156.566 | 1.004x |
new |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.464 | 6.144 | 1.052x | new |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.504 | 9.088 | 1.046x | new
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 15.224 | 13.136 | 1.159x |
new |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 15.192 | 15.216 | 0.998x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 30.095 | 30.032 | 1.002x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.648 | 3.648 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.456 | 3.464 | 0.998x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.848 | 10.864 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.816 | 10.832 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 75.584 | 75.583 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 76.015 | 76.008 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 306.933 | 307.205 |
0.999x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 306.421 | 306.333 | 1.000x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.695 | 4.672 | 1.005x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.800 | 6.808 | 0.999x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 18.288 | 18.256 | 1.002x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 37.344 | 37.344 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.928 | 2.936 | 0.997x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.880 | 2.880 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 20.536 | 19.808 | 1.037x | new |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 20.416 | 19.776 | 1.032x | new |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 79.071 | 78.760 | 1.004x |
new |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 79.047 | 78.719 | 1.004x |
new |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.136 | 3.136 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.615 | 3.592 | 1.006x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 5.312 | 4.896 | 1.085x | new |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.136 | 7.136 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 11.616 | 10.912 | 1.065x | new |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.680 | 39.656 | 1.001x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.648 | 2.624 | 1.009x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.760 | 2.783 | 0.992x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 11.584 | 10.880 | 1.065x | new |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 11.616 | 10.912 | 1.065x | new |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.511 | 39.552 | 0.999x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.584 | 39.608 | 0.999x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.136 | 3.136 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.616 | 3.616 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.312 | 4.896 | 1.085x | new |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.136 | 7.168 | 0.996x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 20.495 | 19.808 | 1.035x |
new |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.040 | 3.048 | 0.997x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.168 | 3.168 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 7.104 | 7.104 | 1.000x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 7.104 | 7.104 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 39.544 | 39.559 | 1.000x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 39.648 | 39.663 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 156.918 | 156.246 | 1.004x |
new |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 156.927 | 156.295 | 1.004x |
new |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.743 | 2.736 | 1.003x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.817 | 2.816 | 1.000x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 15.104 | 15.112 | 0.999x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 15.096 | 15.127 | 0.998x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 5.248 | 4.896 | 1.072x | new |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 39.575 | 39.560 | 1.000x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 196.271 | 195.310 | 1.005x | new |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 75.823 | 75.848 | 1.000x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.424 | 3.455 | 0.991x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.616 | 3.616 | 1.000x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 39.648 | 39.656 | 1.000x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.848 | 10.848 | 1.000x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 11.552 | 10.847 | 1.065x |
new |

*NVIDIA GB300 (sm_103a, 152 SMs); PyTorch 2.14.1+cu130 with the CUDA
13.4.92 runtime; programs compiled with nvcc 13.4. Timer: CUPTI kernel
time with a cold L2; times are medians over 2 runs x 9 interleaved
rounds (us); speedup = main / this PR; the program column says whether
this PR routes the shape to a new program (`new`) or keeps main's
(`same`).*

| case | batch | tokens | heads | groups | head dim | state dim | state
| inputs | options | main (us) | this PR (us) | speedup | program |
|---|---:|---:|---:|---:|---:|---:|---|---|---|---:|---:|---:|---|
| sample_stp_bf16 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.824 | 37.832 | 1.000x | same |
| sample_stp_state_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32
dt/D, int64 index | - | 74.816 | 74.856 | 0.999x | same |
| sample_stp_z | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | z gate | 39.912 | 39.096 | 1.021x | new |
| sample_stp_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | softplus | 37.888 | 37.912 | 0.999x | same |
| sample_stp_z_softplus | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | z gate, softplus | 39.944 | 39.296 | 1.016x | new |
| sample_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.032 | 7.600 | 1.057x | new |
| sample_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.792 | 37.824 | 0.999x | same |
| sample_stp_b256 | 256 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 151.400 | 151.408 | 1.000x | same |
| sample_stp_b128 | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 75.832 | 75.848 | 1.000x | same |
| sample_mtp1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 38.656 | 36.376 | 1.063x | new |
| sample_mtp2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D, int64
index | - | 42.288 | 38.704 | 1.093x | new |
| sweep_bfloat16_vertical_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | softplus, state cache, no state write,
algorithm=vertical | 3.616 | 3.616 | 1.000x | same |
| sweep_bfloat16_horizontal_b1024 | 1024 | 6 | 64 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus, state cache, no state write,
algorithm=horizontal | 1100.592 | 1100.560 | 1.000x | same |
| dynamic_dump_b1_t1_prev0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.752 |
2.752 | 1.000x | same |
| dynamic_dump_b1_t2_prev1 | 1 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 2.880 |
2.880 | 1.000x | same |
| dynamic_dump_b1_t4_prev2 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.104 |
3.096 | 1.003x | same |
| dynamic_dump_b1_t8_prev4 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.680 |
3.680 | 1.000x | same |
| dynamic_dump_b1_t8_prev8 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.712 |
3.712 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b1 | 1 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 3.584 | 3.584 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b2 | 2 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 4.672 | 4.672 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b3 | 3 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 5.504 | 5.504 | 1.000x | same |
| granite_ngram_t6_c4_legacy_adapted_graph_b4 | 4 | 6 | 64 | 1 | 64 |
128 | BF16 | FP32 dt/D, int64 index | softplus, state cache, no state
write, algorithm=vertical | 6.488 | 6.496 | 0.999x | same |
| granite_ngram_t6_c4_sglang_raw_b1 | 1 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 3.872 |
3.872 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b2 | 2 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 4.808 |
4.800 | 1.002x | same |
| granite_ngram_t6_c4_sglang_raw_b3 | 3 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 5.744 |
5.744 | 1.000x | same |
| granite_ngram_t6_c4_sglang_raw_b4 | 4 | 6 | 64 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus, state cache, no state write | 6.704 |
6.704 | 1.000x | same |
| fitest_stp_ratio1 | 32 | 1 | 16 | 16 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 8.024 | 7.600 | 1.056x | new |
| fitest_stp_ratio8 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.824 | 37.808 | 1.000x | same |
| fitest_stp_ratio8_sat | 128 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 75.888 | 75.832 | 1.001x | same |
| fitest_stp_ratio16 | 32 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 37.792 | 37.784 | 1.000x | same |
| fitest_stp_persistent | 257 | 1 | 128 | 8 | 128 | 128 | BF16 | FP32
dt/D, int64 index | - | 303.936 | 303.968 | 1.000x | same |
| fitest_stp_fp32 | 64 | 1 | 64 | 8 | 128 | 128 | FP32 | FP32 dt/D,
int64 index | - | 74.872 | 74.817 | 1.001x | same |
| fitest_mtp_short1 | 64 | 1 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 38.880 | 36.472 | 1.066x | new |
| fitest_mtp_short2 | 64 | 2 | 64 | 8 | 128 | 128 | BF16 | FP32 dt/D,
int64 index | - | 42.296 | 38.720 | 1.092x | new |
| fitest_mtp_cache | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D, int64
index | softplus, state cache, no state write, algorithm=vertical |
3.648 | 3.648 | 1.000x | same |
| fitest_mtp_horizontal | 32 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write,
algorithm=horizontal | 36.704 | 36.704 | 1.000x | same |
| fitest_dynamic0 | 1 | 1 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 2.752 | 2.752 | 1.000x |
same |
| fitest_dynamic0_b8 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | softplus, dst slots, algorithm=simple | 3.856 | 3.856 |
1.000x | same |
| fitest_dynamic1 | 1 | 4 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.096 | 3.104 | 0.997x |
same |
| fitest_dynamic3 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.680 | 3.680 | 1.000x |
same |
| fitest_dynamic7 | 1 | 8 | 16 | 1 | 64 | 128 | FP32 | FP32 dt/D, int64
index | softplus, dst slots, algorithm=simple | 3.704 | 3.712 | 0.998x |
same |
| sweep_bfloat16_auto_b1 | 1 | 6 | 64 | 8 | 64 | 128 | BF16 | FP32 dt/D,
int64 index | softplus, state cache, no state write | 3.640 | 3.648 |
0.998x | same |
| dynamic_dump_b8_t2_prev1 | 8 | 2 | 16 | 1 | 64 | 128 | FP32 | FP32
dt/D, int64 index | softplus, dst slots, algorithm=simple | 3.872 |
3.872 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.008 | 3.008 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.168 | 3.168 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.520 | 3.520 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b2 | 2 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 3.552 | 3.552 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 5.216 | 4.808 | 1.085x | new |
| nemotron_h_tp1_hd64_canonical_b4 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 5.088 | 4.864 | 1.046x | new |
| nemotron_h_tp1_hd64_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.928 | 6.928 | 1.000x | same |
| nemotron_h_tp1_hd64_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 6.904 | 6.896 | 1.001x | same |
| nemotron_h_tp1_hd64_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.976 | 10.336 | 1.062x |
new |
| nemotron_h_tp1_hd64_canonical_b16 | 16 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.912 | 10.368 | 1.052x | new |
| nemotron_h_tp1_hd64_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.744 | 19.088 | 1.034x |
new |
| nemotron_h_tp1_hd64_canonical_b32 | 32 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.544 | 18.776 | 1.041x | new |
| nemotron_h_tp1_hd64_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.872 | 37.872 | 1.000x |
same |
| nemotron_h_tp1_hd64_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 37.896 | 37.888 | 1.000x | same |
| nemotron_h_tp1_hd64_sglang_raw_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.768 | 75.816 | 0.999x |
same |
| nemotron_h_tp1_hd64_canonical_b128 | 128 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.976 | 75.984 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 151.704 | 151.543 | 1.001x |
new |
| nemotron_h_tp1_hd64_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 151.744 | 151.360 | 1.003x |
new |
| nemotron_h_tp1_hd64_sglang_raw_b6 | 6 | 1 | 128 | 8 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.288 | 5.976 | 1.052x | new |
| nemotron_h_tp1_hd64_sglang_raw_b12 | 12 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 9.104 | 8.720 | 1.044x | new
|
| nemotron_h_tp1_hd64_sglang_raw_b20 | 20 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 13.632 | 12.472 | 1.093x |
new |
| nemotron_h_tp1_hd64_sglang_raw_b24 | 24 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 14.336 | 14.336 | 1.000x |
same |
| nemotron_h_tp1_hd64_sglang_raw_b48 | 48 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 28.528 | 28.544 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 3.552 | 3.552 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_canonical_b1 | 1 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 3.360 | 3.360 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 10.288 | 10.272 | 1.002x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b8 | 8 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 10.368 | 10.360 | 1.001x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b64 | 64 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 73.336 | 73.280 | 1.001x |
same |
| nemotron_h_tp1_hd64_fp32_canonical_b64 | 64 | 1 | 128 | 8 | 64 | 128 |
FP32 | FP32 dt/D, int64 index | softplus | 73.216 | 73.312 | 0.999x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b256 | 256 | 1 | 128 | 8 | 64 |
128 | FP32 | BF16 dt/D, int32 index | softplus | 299.887 | 299.840 |
1.000x | same |
| nemotron_h_tp1_hd64_fp32_canonical_b256 | 256 | 1 | 128 | 8 | 64 | 128
| FP32 | FP32 dt/D, int64 index | softplus | 299.344 | 299.376 | 1.000x
| same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b2 | 2 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 4.512 | 4.512 | 1.000x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b4 | 4 | 1 | 128 | 8 | 64 | 128 |
FP32 | BF16 dt/D, int32 index | softplus | 6.544 | 6.560 | 0.998x | same
|
| nemotron_h_tp1_hd64_fp32_sglang_raw_b16 | 16 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 17.248 | 17.248 | 1.000x |
same |
| nemotron_h_tp1_hd64_fp32_sglang_raw_b32 | 32 | 1 | 128 | 8 | 64 | 128
| FP32 | BF16 dt/D, int32 index | softplus | 35.760 | 35.752 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.848 | 2.848 | 1.000x | same |
| nemotron_h_tp2_hd64_canonical_b1 | 1 | 1 | 64 | 4 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.720 | 2.744 | 0.991x | same |
| nemotron_h_tp2_hd64_sglang_raw_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 19.576 | 19.104 | 1.025x | new |
| nemotron_h_tp2_hd64_canonical_b64 | 64 | 1 | 64 | 4 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 19.448 | 18.728 | 1.038x | new |
| nemotron_h_tp2_hd64_sglang_raw_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 75.784 | 75.840 | 0.999x |
same |
| nemotron_h_tp2_hd64_canonical_b256 | 256 | 1 | 64 | 4 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 75.928 | 75.920 | 1.000x |
same |
| nemotron_h_tp2_hd64_sglang_raw_b2 | 2 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.072 | 3.072 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b4 | 4 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.488 | 3.488 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b8 | 8 | 1 | 64 | 4 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 5.184 | 4.800 | 1.080x | new |
| nemotron_h_tp2_hd64_sglang_raw_b16 | 16 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.944 | 6.944 | 1.000x | same |
| nemotron_h_tp2_hd64_sglang_raw_b32 | 32 | 1 | 64 | 4 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 10.944 | 10.336 | 1.059x | new |
| nemotron_h_tp2_hd64_sglang_raw_b128 | 128 | 1 | 64 | 4 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.840 | 37.872 | 0.999x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.592 | 2.576 | 1.006x | same |
| nemotron_h_tp4_hd64_canonical_b1 | 1 | 1 | 32 | 2 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.704 | 2.696 | 1.003x | same |
| nemotron_h_tp4_hd64_sglang_raw_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 11.008 | 10.368 | 1.062x | new |
| nemotron_h_tp4_hd64_canonical_b64 | 64 | 1 | 32 | 2 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 10.944 | 10.304 | 1.062x | new |
| nemotron_h_tp4_hd64_sglang_raw_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.832 | 37.832 | 1.000x |
same |
| nemotron_h_tp4_hd64_canonical_b256 | 256 | 1 | 32 | 2 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 38.000 | 38.048 | 0.999x |
same |
| nemotron_h_tp4_hd64_sglang_raw_b4 | 4 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.072 | 3.072 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b8 | 8 | 1 | 32 | 2 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 3.520 | 3.520 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b16 | 16 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 4.960 | 4.768 | 1.040x | new |
| nemotron_h_tp4_hd64_sglang_raw_b32 | 32 | 1 | 32 | 2 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.960 | 6.960 | 1.000x | same |
| nemotron_h_tp4_hd64_sglang_raw_b128 | 128 | 1 | 32 | 2 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 19.528 | 19.040 | 1.026x |
new |
| granite_h_small_hd64_sglang_raw_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 3.040 | 3.040 | 1.000x | same |
| granite_h_small_hd64_canonical_b1 | 1 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 3.072 | 3.072 | 1.000x | same |
| granite_h_small_hd64_sglang_raw_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 6.928 | 6.944 | 0.998x | same |
| granite_h_small_hd64_canonical_b8 | 8 | 1 | 128 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 6.928 | 6.912 | 1.002x | same |
| granite_h_small_hd64_sglang_raw_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 37.856 | 37.840 | 1.000x |
same |
| granite_h_small_hd64_canonical_b64 | 64 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 37.904 | 37.912 | 1.000x |
same |
| granite_h_small_hd64_sglang_raw_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 151.576 | 151.424 | 1.001x |
new |
| granite_h_small_hd64_canonical_b256 | 256 | 1 | 128 | 1 | 64 | 128 |
BF16 | FP32 dt/D, int64 index | softplus | 151.752 | 151.368 | 1.003x |
new |
| granite_h_tiny_hd64_sglang_raw_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
BF16 dt/D, int32 index | softplus | 2.672 | 2.672 | 1.000x | same |
| granite_h_tiny_hd64_canonical_b1 | 1 | 1 | 48 | 1 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | softplus | 2.752 | 2.768 | 0.994x | same |
| granite_h_tiny_hd64_sglang_raw_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| BF16 dt/D, int32 index | softplus | 14.360 | 14.368 | 0.999x | same |
| granite_h_tiny_hd64_canonical_b64 | 64 | 1 | 48 | 1 | 64 | 128 | BF16
| FP32 dt/D, int64 index | softplus | 14.336 | 14.328 | 1.001x | same |
| fitest_stp_hd64_rows_bf16 | 4 | 1 | 128 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 5.056 | 4.864 | 1.039x | new |
| fitest_stp_hd64_paired_rows | 64 | 1 | 128 | 8 | 64 | 128 | BF16 |
FP32 dt/D, int64 index | - | 37.856 | 37.840 | 1.000x | same |
| fitest_stp_hd64_paired_rows_b320 | 320 | 1 | 128 | 8 | 64 | 128 | BF16
| FP32 dt/D, int64 index | - | 189.616 | 189.208 | 1.002x | new |
| fitest_stp_hd64_fp32 | 64 | 1 | 128 | 8 | 64 | 128 | FP32 | FP32 dt/D,
int64 index | - | 73.264 | 73.192 | 1.001x | same |
| fitest_stp_hd64_odd_pairs | 8 | 1 | 24 | 8 | 64 | 128 | BF16 | FP32
dt/D, int64 index | - | 3.392 | 3.392 | 1.000x | same |
| fitest_stp_hd64_raw_rows | 2 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 3.600 | 3.616 | 0.996x | same |
| fitest_stp_hd64_raw_paired | 64 | 1 | 128 | 8 | 64 | 128 | BF16 | BF16
dt/D, int32 index | softplus | 37.872 | 37.848 | 1.001x | same |
| fitest_stp_hd64_raw_fp32 | 8 | 1 | 128 | 8 | 64 | 128 | FP32 | BF16
dt/D, int32 index | softplus | 10.296 | 10.288 | 1.001x | same |
| fitest_stp_hd64_raw_paired_four_cta | 16 | 1 | 128 | 8 | 64 | 128 |
BF16 | BF16 dt/D, int32 index | softplus | 10.976 | 10.336 | 1.062x |
new |

Cake has no variants of this kernel beyond the dimensions above, and it
ships the kernel only on sm_100a and sm_103a, both of which this PR
covers.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added GPU-accelerated selective state update options, including
support for short sequences and varied batch sizes.
* Added optional timestep softplus processing and output gating, with
padded state slots and disabled state updates handled during
computation.
  * Added support for multiple index and coefficient formats.

* **Bug Fixes**
* Expanded coverage for split-grid layouts, architecture-specific
selection, and equivalence between program variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [328e862](https://github.com/flashinfer-ai/flashinfer/commit/328e862b3427fce51a3a846d98db0620326c9016)

- **作者**: eigen
- **时间**: 2026-10-26T10:00:39Z
- **提交信息**: perf(cake_blackwell_bf16_fp4): faster tcgen05 and small-M programs on SM100/SM103 (#7419)

FlashInfer's `mm_bf16_fp4` multiplies BF16 activations by FP4 (E2M1)
weights that carry E4M3 block scales, with FP32 accumulation. Cake ships
it as two backend variants that differ in operand layout:
`blackwell-native` (cuDNN-ABI layouts, BF16 or FP16 output) and
`blackwell-tiled` (CuTe-ABI prepared-tile layouts, BF16 output). This PR
regenerates 10 of the kernel's 97 Cake programs, with bit-identical
outputs. The three two-CTA M=128 tcgen05 programs for 768/2112/2048
(`blackwell-native` with and without alpha, `blackwell-tiled` with
alpha) now free the pair's tensor memory while the last stores are in
flight, instead of after a final cluster-wide barrier. The other seven
are `blackwell-tiled` register-streaming small-M programs. The split-K
ones (4-CTA mailbox, 8-CTA reduce-scatter, 6-way, each with and without
alpha) now load and convert all their block scales once before the main
loop, and the single-CTA and mailbox programs with alpha read alpha
right after the dependent-launch wait. Speedup is the previous Cake
generation's time on `main` (#7376) divided by this PR's time, both from
the same GPU in one job. On GB300 / B200 it is 1.099x / 1.085x for
`blackwell-native` and 1.074x / 1.070x for `blackwell-tiled` at
768/2112/2048. The other `blackwell-tiled` rows measure 1.106x / 1.135x
at 16/1024/1024 with alpha=None and 1.166x / 1.205x with a
caller-provided `out`, 1.042x / 1.046x at 1/4096/4096, 1.030x / 1.032x
at 17/3072/3072, 1.045x / 1.044x at 7/4160/192, and 1.014x / 1.010x at
13/11008/128. Rows on unchanged programs measure 0.999x-1.000x on GB300
and 0.999x-1.001x on B200.

**NVIDIA GB300 (sm_103a), CUDA 13.4:** mean over separate processes of
the per-process median CUPTI kernel time in us (two processes per side;
four for the 1/4096/4096 `blackwell-tiled` and 13/11008/128 rows), cold
L2, PDL on; alpha passed and BF16 output unless the variant column notes
otherwise.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 6.994 | 6.992 | 1.000x |
| 1/4096/4096 | blackwell-tiled | 6.824 | 6.552 | 1.042x |
| 768/2112/2048 | blackwell-native | 9.552 | 8.694 | 1.099x |
| 768/2112/2048 | blackwell-tiled | 10.184 | 9.480 | 1.074x |
| 7/4160/192 | blackwell-tiled | 2.870 | 2.746 | 1.045x |
| 13/11008/128 | blackwell-tiled | 3.032 | 2.990 | 1.014x |
| 17/3072/3072 | blackwell-tiled | 7.472 | 7.256 | 1.030x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 3.264 | 2.950 | 1.106x |
| 16/1024/1024 | blackwell-native, FP16 output | 2.820 | 2.822 | 0.999x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 2.824 | 2.826
| 0.999x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 3.423 | 2.936
| 1.166x |

**NVIDIA B200 (sm_100a), CUDA 13.4:** mean over separate processes of
the per-process median CUPTI kernel time in us (two processes per side;
four for the 1/4096/4096 `blackwell-tiled` and 13/11008/128 rows), cold
L2, PDL on; alpha passed and BF16 output unless the variant column notes
otherwise.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 7.252 | 7.252 | 1.000x |
| 1/4096/4096 | blackwell-tiled | 7.208 | 6.888 | 1.046x |
| 768/2112/2048 | blackwell-native | 10.264 | 9.464 | 1.085x |
| 768/2112/2048 | blackwell-tiled | 11.122 | 10.393 | 1.070x |
| 7/4160/192 | blackwell-tiled | 3.072 | 2.944 | 1.044x |
| 13/11008/128 | blackwell-tiled | 3.206 | 3.176 | 1.010x |
| 17/3072/3072 | blackwell-tiled | 7.912 | 7.664 | 1.032x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 3.479 | 3.064 | 1.135x |
| 16/1024/1024 | blackwell-native, FP16 output | 3.076 | 3.072 | 1.001x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 3.076 | 3.080
| 0.999x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 3.616 | 3.000
| 1.205x |

Cake has no other variants of this kernel: FP16 output is only on
`blackwell-native`, there are no fused forms, and every program ships
for sm_100a (B200) and sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance Improvements**
* Updated BF16×FP4 processing to handle scale data and tensor operations
in separate stages, improving coordination during computation.
* Refined output processing across supported tile sizes while preserving
alpha scaling and BF16 output conversion.
* **Reliability**
* Strengthened synchronization around data transfers, output completion,
and memory cleanup to help ensure processing stages finish in the
correct order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bdaa240](https://github.com/flashinfer-ai/flashinfer/commit/bdaa2401ad4b78a5731750a8a73a2bbe1523b78a)

- **作者**: eigen
- **时间**: 2026-10-26T09:48:47Z
- **提交信息**: perf(cake_grouped_mxfp8_quantize): per-K row-tiled programs for K = 4096 and 2048, integer scale bytes at K = 7168 (#7431)

`cake_grouped_mxfp8_quantize` takes a BF16 or F16 `x[B, M, K]` and an
int32 `mask[B]` that gives the valid rows per group. It writes FP8 E4M3
values and UE8M0 block scales, one per 32 elements, in the 128x4
grouped-GEMM scale layout. This PR adds two row-tiled programs chosen by
K, each for BF16 and F16 input. The K = 4096 program runs 256-thread
CTAs that each cover two rows. The K = 2048 program runs 128-thread
CTAs. Both keep BF16/F16 values as packed pairs and compute the UE8M0
scale byte with integer operations. The existing K = 7168 program (224
threads) now computes the same scale byte with integer operations
instead of an FP32 divide. Inputs above 4 MiB with at least 16,384 rows
(B·M) now pick the row-tiled program by K. Other K values keep the
128-thread row-tiled program. Bulk-copy and row-2D routing is unchanged,
and the host still never reads the mask.

The baseline is the previous Cake version of this kernel, already in
FlashInfer main (#7391). For K = 4096 and K = 2048 it ran the 128-thread
row-tiled program. Each pair of numbers below is GB300 / GB200. On [32,
1024, 4096], 16 rows per group is 1.3552x / 1.3632x faster. 128 rows per
group is 1.0492x / 1.0493x faster. The full mask is 1.0092x / 1.0115x
faster, beyond the A/A noise band. On [32, 1024, 7168], the sparse and
medium masks are 1.0161–1.0233x / 1.0165–1.0235x faster. The [32, 1024,
7168] full mask is 1.0011x on GB300, above the A/A noise band. On GB200
it is 1.0006x, which is parity, not a gain. The [32, 1024, 2048] full
mask is 1.0006x / 1.0003x, which is parity on both GPUs, not a gain. The
‡ sparse rows at K = 2048 are 1.0464–1.0960x / 1.0521–1.1061x faster.
The 6 shapes marked † keep their program. Their ratios of 0.9993–1.0013
/ 0.9996–1.0017 are A/A pairs of that unchanged program. No row is
slower than before beyond noise.

Speedup = previous µs / this PR µs, the median of paired per-round
ratios over 12 interleaved rounds with a cold L2; above 1 is faster.
† Same program before and after, so the two columns are an A/A pair of
that program. ‡ Extra sparse-mask rows at K = 2048, beyond the standard
shape list.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | program (previous → this
PR) | previous (µs) | this PR (µs) | speedup |
|---|---|---|---:|---|---:|---:|---:|
| [2, 256, 4096] † | BF16 | full | 512 | bulk-copy | 3.466 | 3.467 |
0.9997 |
| [2, 256, 4096] † | F16 | full | 512 | bulk-copy | 3.464 | 3.464 |
1.0000 |
| [2, 128, 4096] † | BF16 | full | 256 | bulk-copy | 2.800 | 2.799 |
0.9993 |
| [3, 256, 2048] † | BF16 | full | 768 | bulk-copy | 3.100 | 3.097 |
1.0013 |
| [8, 512, 2048] † | BF16 | full | 4096 | row-2D | 6.806 | 6.807 |
0.9993 |
| [64, 128, 4096] † | BF16 | full | 8192 | row-2D | 19.005 | 18.998 |
1.0005 |
| [32, 1024, 7168] | BF16 | 16 / group | 512 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 12.547 | 12.261 | 1.0233 |
| [32, 1024, 7168] | BF16 | 32 / group | 1024 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 13.587 | 13.275 | 1.0233 |
| [32, 1024, 7168] | BF16 | 128 / group | 4096 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 21.409 | 21.055 | 1.0170 |
| [32, 1024, 7168] | BF16 | 512 in group 0 | 512 | 224-thread row-tiled
→ 224-thread row-tiled, integer scale | 11.392 | 11.166 | 1.0202 |
| [32, 1024, 7168] | BF16 | 1024 in group 0 | 1024 | 224-thread
row-tiled → 224-thread row-tiled, integer scale | 13.324 | 13.076 |
1.0190 |
| [32, 1024, 7168] | BF16 | 1024 in group 0, 99 in others | 4093 |
224-thread row-tiled → 224-thread row-tiled, integer scale | 22.134 |
21.768 | 1.0166 |
| [32, 1024, 7168] | BF16 | Zipf, 4096 total | 4096 | 224-thread
row-tiled → 224-thread row-tiled, integer scale | 22.851 | 22.470 |
1.0172 |
| [32, 1024, 7168] | BF16 | full | 32768 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 104.693 | 104.574 | 1.0011 |
| [32, 1024, 7168] | F16 | 128 / group | 4096 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 21.436 | 21.092 | 1.0161 |
| [32, 1024, 4096] | BF16 | 16 / group | 512 | 128-thread row-tiled → K
= 4096 row-tiled (256 threads) | 10.864 | 8.017 | 1.3552 |
| [32, 1024, 4096] | BF16 | 128 / group | 4096 | 128-thread row-tiled →
K = 4096 row-tiled (256 threads) | 13.023 | 12.408 | 1.0492 |
| [32, 1024, 4096] | BF16 | full | 32768 | 128-thread row-tiled → K =
4096 row-tiled (256 threads) | 63.031 | 62.457 | 1.0092 |
| [32, 1024, 2048] | BF16 | full | 32768 | 128-thread row-tiled → K =
2048 row-tiled (128 threads) | 34.454 | 34.432 | 1.0006 |
| [32, 1024, 2048] ‡ | BF16 | 16 / group | 512 | 128-thread row-tiled →
K = 2048 row-tiled (128 threads) | 6.846 | 6.495 | 1.0542 |
| [32, 1024, 2048] ‡ | BF16 | 128 / group | 4096 | 128-thread row-tiled
→ K = 2048 row-tiled (128 threads) | 8.240 | 7.872 | 1.0464 |
| [32, 1024, 2048] ‡ | BF16 | Zipf, 4096 total | 4096 | 128-thread
row-tiled → K = 2048 row-tiled (128 threads) | 8.554 | 7.801 | 1.0960 |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | program (previous → this
PR) | previous (µs) | this PR (µs) | speedup |
|---|---|---|---:|---|---:|---:|---:|
| [2, 256, 4096] † | BF16 | full | 512 | bulk-copy | 3.554 | 3.549 |
1.0006 |
| [2, 256, 4096] † | F16 | full | 512 | bulk-copy | 3.547 | 3.543 |
1.0017 |
| [2, 128, 4096] † | BF16 | full | 256 | bulk-copy | 2.844 | 2.844 |
1.0007 |
| [3, 256, 2048] † | BF16 | full | 768 | bulk-copy | 3.170 | 3.172 |
1.0003 |
| [8, 512, 2048] † | BF16 | full | 4096 | row-2D | 6.982 | 6.982 |
0.9996 |
| [64, 128, 4096] † | BF16 | full | 8192 | row-2D | 19.015 | 19.025 |
0.9996 |
| [32, 1024, 7168] | BF16 | 16 / group | 512 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 12.963 | 12.665 | 1.0235 |
| [32, 1024, 7168] | BF16 | 32 / group | 1024 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 14.080 | 13.759 | 1.0231 |
| [32, 1024, 7168] | BF16 | 128 / group | 4096 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 22.089 | 21.721 | 1.0172 |
| [32, 1024, 7168] | BF16 | 512 in group 0 | 512 | 224-thread row-tiled
→ 224-thread row-tiled, integer scale | 11.788 | 11.584 | 1.0174 |
| [32, 1024, 7168] | BF16 | 1024 in group 0 | 1024 | 224-thread
row-tiled → 224-thread row-tiled, integer scale | 13.752 | 13.522 |
1.0170 |
| [32, 1024, 7168] | BF16 | 1024 in group 0, 99 in others | 4093 |
224-thread row-tiled → 224-thread row-tiled, integer scale | 22.645 |
22.254 | 1.0178 |
| [32, 1024, 7168] | BF16 | Zipf, 4096 total | 4096 | 224-thread
row-tiled → 224-thread row-tiled, integer scale | 23.242 | 22.843 |
1.0173 |
| [32, 1024, 7168] | BF16 | full | 32768 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 103.828 | 103.769 | 1.0006 |
| [32, 1024, 7168] | F16 | 128 / group | 4096 | 224-thread row-tiled →
224-thread row-tiled, integer scale | 22.142 | 21.782 | 1.0165 |
| [32, 1024, 4096] | BF16 | 16 / group | 512 | 128-thread row-tiled → K
= 4096 row-tiled (256 threads) | 11.297 | 8.288 | 1.3632 |
| [32, 1024, 4096] | BF16 | 128 / group | 4096 | 128-thread row-tiled →
K = 4096 row-tiled (256 threads) | 13.524 | 12.891 | 1.0493 |
| [32, 1024, 4096] | BF16 | full | 32768 | 128-thread row-tiled → K =
4096 row-tiled (256 threads) | 62.787 | 62.078 | 1.0115 |
| [32, 1024, 2048] | BF16 | full | 32768 | 128-thread row-tiled → K =
2048 row-tiled (128 threads) | 34.456 | 34.457 | 1.0003 |
| [32, 1024, 2048] ‡ | BF16 | 16 / group | 512 | 128-thread row-tiled →
K = 2048 row-tiled (128 threads) | 7.108 | 6.743 | 1.0540 |
| [32, 1024, 2048] ‡ | BF16 | 128 / group | 4096 | 128-thread row-tiled
→ K = 2048 row-tiled (128 threads) | 8.546 | 8.127 | 1.0521 |
| [32, 1024, 2048] ‡ | BF16 | Zipf, 4096 total | 4096 | 128-thread
row-tiled → K = 2048 row-tiled (128 threads) | 8.837 | 7.990 | 1.1061 |


The kernel's other Cake variants in FlashInfer are row-2D, bulk-copy and
128-thread row-tiled, each for BF16 and F16 input; all 12 programs ship
for sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized grouped MXFP8 quantization options for padded K values
of 2048 and 4096, supporting both float16 and bfloat16 inputs.
* Quantization now selects a K-specific option when applicable and
retains general tiled and fallback options for other supported shapes.
* **Bug Fixes**
* Updated scale calculation for one quantization path to handle
non-finite magnitudes more consistently.
* **Tests**
* Expanded coverage for program selection, grid calculations, and exact
outputs at K values of 2048 and 4096.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5e8921c](https://github.com/flashinfer-ai/flashinfer/commit/5e8921c0d534f35b00c1abcd5cfd673fbad9ab2e)

- **作者**: eigen
- **时间**: 2026-10-26T09:47:05Z
- **提交信息**: perf(cake_nvfp4_mla_decode): short-unit decode and general split-KV combine on SM100 / SM103 (#7418)

This PR speeds up `cake_nvfp4_mla_decode`
(`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla`,
experimental), the MLA decode with NVFP4 queries and KV cache. The
kernel has one variant. This PR adds two programs to it on SM100 and
SM103. A decode program for short work units is picked when every unit
holds at most 4096 KV tokens on SM100 or 8192 on SM103. On SM100, the
existing QK-ahead program still takes priority. A new combine program is
used when some row has three or more KV splits. Plans with at most two
splits per row keep the existing combine. The existing programs are
unchanged. The baseline is the previous version of this kernel in
`main`. Speedup is `main` latency divided by this PR's latency. Each
latency is the median of one complete call.

On GB300, 2 requests reach 1.109x with a forced 3-way split and 1.066x
with a forced 2-way split. 3 requests with 8 heads reach 1.035x. 4
requests with 1 query token and no sink reach 1.016x. Batch 24 with 8320
keys each reaches 1.006x. On B200, these four cases reach 1.116x,
1.052x, 1.038x and 1.017x, and batch 32 with 4096 keys each reaches
1.007x.

**NVIDIA GB300 (sm_103a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 11.94 | 11.20 | 1.066x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 24.74 |
23.90 | 1.035x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 32.00 | 31.50 | 1.016x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 82.24 | 82.34 |
1.000x (unchanged) |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 143.38 | 143.58 |
1.000x (unchanged) |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 263.26 | 263.30 |
1.000x (unchanged) |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 511.78 | 511.79 |
1.000x (unchanged) |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1014.99 | 1015.70
| 1.000x (unchanged) |
| batch 24, 8320 keys each, 64 heads, 6 query tokens | 67.42 | 67.01 |
1.006x |
| batch 24, 8384 keys each, 64 heads, 6 query tokens | 68.22 | 68.26 |
1.000x (unchanged) |
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 3-way
split | 12.53 | 11.30 | 1.109x |

**NVIDIA B200 (sm_100a), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 2-way
split | 12.32 | 11.71 | 1.052x |
| 3 requests (1000, 8192, 5000 keys), 8 heads, 6 query tokens | 26.18 |
25.22 | 1.038x |
| 4 requests (64, 65, 4096, 777 keys), 64 heads, 1 query token, no sink
| 36.03 | 35.42 | 1.017x |
| batch 32, 8K keys each, 64 heads, 6 query tokens | 96.73 | 96.83 |
1.000x (unchanged) |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 173.97 | 173.89 |
1.000x (unchanged) |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 386.69 | 386.75 |
1.000x (unchanged) |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 764.64 | 764.54 |
1.000x (unchanged) |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1519.92 | 1519.79
| 1.000x (unchanged) |
| batch 32, 51200 keys each, 64 heads, 6 query tokens | 608.94 | 608.90
| 1.000x (unchanged) |
| batch 32, 52224 keys each, 64 heads, 6 query tokens | 606.66 | 606.53
| 1.000x (unchanged) |
| batch 32, 4096 keys each, 64 heads, 6 query tokens | 75.52 | 75.01 |
1.007x |
| batch 32, 4160 keys each, 64 heads, 6 query tokens | 77.76 | 77.73 |
1.000x (unchanged) |
| batch 23, 8448 keys each, 64 heads, 6 query tokens | 76.03 | 75.98 |
1.000x (unchanged) |
| 2 requests (256, 300 keys), 64 heads, 6 query tokens, forced 3-way
split | 13.04 | 11.68 | 1.116x |

"1.000x (unchanged)" means this PR runs the same programs with the same
plan as `main` on that shape.

Cake has no other variants of this decode (no other data type, layout or
fused form), and the kernel covers sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded experimental NVFP4 MLA decoding support for short workloads
and balanced workloads on supported NVIDIA architectures.
* Added support for combining results when a query is split into more
than two parts.
* Added specialized execution paths for supported workloads, with
bitwise-identical outputs across programs within the same processing
stage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f03f104](https://github.com/flashinfer-ai/flashinfer/commit/f03f104024663397f54c064f7b134ffb67899516)

- **作者**: Yang Xu
- **时间**: 2026-10-26T09:46:05Z
- **提交信息**: ci: retain pytest collection diagnostics (#7416)

<!-- .github/pull_request_template.md -->

## 📌 Description

Keep pytest collection stdout/stderr under the JUnit directory and
include it in the public CI artifact. Collection can succeed after a
best-effort prewarm warning, but its temporary log currently disappears;
this makes later serial-compilation timeouts difficult to diagnose.

Each collector writes to a unique directory, preserving earlier
diagnostics across concurrent collection or retries. Collection metadata
remains temporary; test selection, deadlines and result handling are
unchanged.

## 🔍 Related Issues

Follow-up to the [H100 compilation-timeout investigation on
#7050](https://github.com/flashinfer-ai/flashinfer/pull/7050#issuecomment-6408296781).
This supplies missing evidence for a future run; it does not classify
the incomplete unit as passing or establish the prewarm failure cause.

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

Scoped checks: `pre-commit run --files scripts/test_sharding/runner.py
tests/test_sharding/test_runner_cli.py .github/workflows/pr-test.yml
CLAUDE.md` passes. Whole-repository formatting was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

- The three retention checks fail on the original runner because
persistent logs are absent (success, collection error, deadline
termination).
- Patched `test_runner_cli.py`: 73 tests pass in the lightweight CPU
environment; the three existing communication-collection tests pass
separately in the Torch environment with a dedicated writable cache. All
76 test IDs pass across these two runs. Initial missing-Torch and
read-only-cache failures were retained.
- Tests exercise actual pytest subprocesses, preservation of
warning/error output, repeated failed collection and completed-manifest
reuse. No GPU execution is needed for this change.

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

The only new retained files are collection logs. Per-partition JSON
still uses the temporary directory. The public upload uses the existing
30-day telemetry retention. This is a diagnostic change, with no
attention or Mamba implementation changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Test collection output is now saved in separate logs for each
collection run, including standard output, standard error, warnings, and
errors.
* Collection logs are included with CI test and telemetry artifacts,
making them available for review after a run.
* Logs are preserved across retries; successful collections reuse the
completed plan without creating an additional collection log. Collection
metadata continues to use temporary storage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yang Xu <yanxu@nvidia.com>

### [e23951f](https://github.com/flashinfer-ai/flashinfer/commit/e23951f1995770969d5c169807ed29afe42942d7)

- **作者**: eigen
- **时间**: 2026-10-26T09:45:51Z
- **提交信息**: perf(cake_batch_deepgemm_fp8): faster masked batched FP8 GEMM on SM100 / SM103 (#7425)

FlashInfer's Cake grouped FP8 GEMM family has four forms. Two are
contiguous: one uses FP32 scales and the other packed UE8M0 scales
(block-scaled MMA). One fuses gate/up with SwiGLU and FP8
re-quantisation. One is masked batched. This PR delivers the masked
batched form. It updates the masked batch variant's kernels and routing.
The baseline is the previous Cake version of this kernel on FlashInfer
main. Across 164 shapes, the PR is faster on 51 (B200), 54 (GB300 #1)
and 51 (GB300 #2). It is slower on none. On the remaining shapes, it
either runs the same programs and grids as main or ties within
run-to-run spread. The largest gains are on the N=512, K=128 shapes,
where PR/main latency is between 0.2804 and 0.8869.

B200: NVIDIA B200 (sm_100a), driver 580.82.07, CUDA 13.4; GB300 #1:
NVIDIA GB300 (sm_103a), driver 580.167.08, CUDA 13.4; GB300 #2: NVIDIA
GB300 (sm_103a), driver 580.159.03, CUDA 13.4; PyTorch 2.14.1+cu130. In
the GB300 #1 columns, rows b1_m128_n128_k512, b4_m128_n128_k512 and
sglang_p90_b32_m256_em1_n4096_k7168_ep8 were re-measured with 9 runs on
a second NVIDIA GB300 (sm_103a), driver 580.159.03. expected_m a / b:
B200 / GB300 (sm_100a / sm_103a); the group sizes of those rows are
drawn on each architecture. The PR/main ratio is the median of the
per-run ratios (3 runs; 9 runs on the 14 re-measured cells), so it need
not equal the quotient of the two latencies. (same) marks rows where the
PR runs the same programs and grids as main. (tie) marks rows whose
ratio lies within that row's run-to-run spread.

| row | B | M | N | K | expected_m | B200 main us | B200 PR us | B200
PR/main | GB300 #1 main us | GB300 #1 PR us | GB300 #1 PR/main | GB300
#2 main us | GB300 #2 PR us | GB300 #2 PR/main |

|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| b1_m128_n128_k512 | 1 | 128 | 128 | 512 | 42 | 4.27 | 4.45 | 1.0412
(tie) | 4.16 | 4.26 | 1.0231 (tie) | 4.13 | 4.16 | 1.0078 (tie) |
| b1_m128_n512_k128 | 1 | 128 | 512 | 128 | 42 | 5.06 | 3.58 | 0.7152 |
4.83 | 3.33 | 0.6887 | 4.86 | 3.30 | 0.6733 |
| b1_m128_n4096_k7168 | 1 | 128 | 4096 | 7168 | 102 / 26 | 14.58 | 13.22
| 0.9088 | 13.66 | 12.45 | 0.9110 | 13.82 | 12.38 | 0.8958 |
| b1_m128_n7168_k2048 | 1 | 128 | 7168 | 2048 | 81 / 96 | 8.05 | 7.90 |
0.9801 | 7.55 | 7.17 | 0.9492 | 7.50 | 7.17 | 0.9552 |
| b1_m256_n128_k512 | 1 | 256 | 128 | 512 | 42 | 4.45 | 4.43 | 0.9929
(tie) | 4.29 | 4.00 | 0.9328 | 4.32 | 4.19 | 0.9704 (tie) |
| b1_m256_n512_k128 | 1 | 256 | 512 | 128 | 42 | 5.06 | 3.57 | 0.7103 |
4.77 | 3.30 | 0.6913 | 4.82 | 3.26 | 0.6800 |
| b1_m256_n4096_k7168 | 1 | 256 | 4096 | 7168 | 141 / 230 | 17.82 |
14.18 | 0.7899 | 16.56 | 13.18 | 0.7977 | 16.62 | 13.25 | 0.7969 |
| b1_m256_n7168_k2048 | 1 | 256 | 7168 | 2048 | 209 / 96 | 8.94 | 8.70 |
0.9732 | 7.57 | 7.17 | 0.9471 | 7.55 | 7.17 | 0.9492 |
| b1_m1024_n128_k512 | 1 | 1024 | 128 | 512 | 810 | 4.51 | 4.42 | 0.9789
| 4.35 | 4.26 | 0.9779 | 4.38 | 4.26 | 0.9708 |
| b1_m1024_n512_k128 | 1 | 1024 | 512 | 128 | 810 | 5.28 | 3.68 | 0.6970
| 4.96 | 3.46 | 0.6968 | 4.94 | 3.46 | 0.6990 |
| b1_m1024_n4096_k7168 | 1 | 1024 | 4096 | 7168 | 816 / 1017 | 25.25 |
23.68 | 0.9391 | 23.60 | 23.49 | 0.9973 (same) | 23.54 | 23.52 | 0.9993
(same) |
| b1_m1024_n7168_k2048 | 1 | 1024 | 7168 | 2048 | 630 / 721 | 13.41 |
12.58 | 0.9379 | 14.50 | 12.64 | 0.8707 | 14.40 | 12.45 | 0.8656 |
| b1_m8192_n128_k512 | 1 | 8192 | 128 | 512 | 5116 | 4.93 | 4.90 |
0.9936 (same) | 4.83 | 4.70 | 0.9767 | 4.82 | 4.75 | 0.9867 |
| b1_m8192_n512_k128 | 1 | 8192 | 512 | 128 | 810 | 5.25 | 4.13 | 0.7866
| 5.04 | 4.00 | 0.7962 | 5.06 | 3.98 | 0.8032 |
| b1_m8192_n4096_k7168 | 1 | 8192 | 4096 | 7168 | 6270 / 475 | 145.37 |
117.17 | 0.8070 | 16.96 | 15.17 | 0.8952 | 16.98 | 15.17 | 0.8935 |
| b1_m8192_n7168_k2048 | 1 | 8192 | 7168 | 2048 | 3469 / 5862 | 43.01 |
37.89 | 0.8799 | 73.86 | 50.22 | 0.6807 | 75.38 | 48.32 | 0.6430 |
| b1_m16384_n128_k512 | 1 | 16384 | 128 | 512 | 10597 | 5.60 | 5.66 |
1.0114 (same) | 5.38 | 5.38 | 1.0000 (same) | 5.34 | 5.34 | 1.0000
(same) |
| b1_m16384_n512_k128 | 1 | 16384 | 512 | 128 | 12074 | 7.87 | 6.21 |
0.7878 | 9.70 | 5.92 | 0.6126 | 9.76 | 5.95 | 0.6098 |
| b1_m16384_n4096_k7168 | 1 | 16384 | 4096 | 7168 | 16043 / 3834 |
360.78 | 298.97 | 0.8287 | 88.99 | 64.72 | 0.7291 | 93.57 | 62.77 |
0.6708 |
| b1_m16384_n7168_k2048 | 1 | 16384 | 7168 | 2048 | 14387 / 1946 |
168.14 | 127.65 | 0.7593 | 24.72 | 22.53 | 0.9113 | 24.74 | 22.05 |
0.8925 |
| b4_m128_n128_k512 | 4 | 128 | 128 | 512 | 70 | 4.74 | 4.58 | 0.9661 |
4.58 | 4.45 | 0.9720 | 4.51 | 4.42 | 0.9787 |
| b4_m128_n512_k128 | 4 | 128 | 512 | 128 | 70 | 5.34 | 3.90 | 0.7305 |
5.17 | 3.65 | 0.7043 | 5.22 | 3.71 | 0.7117 |
| b4_m128_n4096_k7168 | 4 | 128 | 4096 | 7168 | 50 / 43 | 23.94 | 23.89
| 0.9973 (tie) | 23.62 | 23.82 | 1.0088 (same) | 23.26 | 23.23 | 0.9972
(same) |
| b4_m128_n7168_k2048 | 4 | 128 | 7168 | 2048 | 21 / 68 | 14.99 | 14.46
| 0.9669 | 13.47 | 13.47 | 1.0000 (same) | 13.57 | 13.57 | 0.9976 (same)
|
| b4_m256_n128_k512 | 4 | 256 | 128 | 512 | 102 | 4.74 | 4.66 | 0.9832 |
4.51 | 4.38 | 0.9716 | 4.50 | 4.38 | 0.9716 |
| b4_m256_n512_k128 | 4 | 256 | 512 | 128 | 102 | 5.38 | 3.74 | 0.6963 |
5.09 | 3.62 | 0.7107 | 5.12 | 3.74 | 0.7358 |
| b4_m256_n4096_k7168 | 4 | 256 | 4096 | 7168 | 141 / 146 | 28.74 |
28.77 | 1.0017 (same) | 28.50 | 28.46 | 0.9983 (same) | 28.43 | 28.43 |
0.9994 (same) |
| b4_m256_n7168_k2048 | 4 | 256 | 7168 | 2048 | 115 / 21 | 17.06 | 15.52
| 0.9099 | 13.50 | 13.60 | 1.0071 (same) | 13.47 | 13.42 | 0.9976 (same)
|
| b4_m1024_n128_k512 | 4 | 1024 | 128 | 512 | 487 | 4.74 | 4.70 | 0.9932
(same) | 4.58 | 4.46 | 0.9755 | 4.58 | 4.48 | 0.9790 |
| b4_m1024_n512_k128 | 4 | 1024 | 512 | 128 | 806 | 5.55 | 4.83 | 0.8754
| 5.23 | 4.64 | 0.8869 | 5.34 | 4.67 | 0.8769 |
| b4_m1024_n4096_k7168 | 4 | 1024 | 4096 | 7168 | 593 / 303 | 78.08 |
56.10 | 0.7184 | 44.14 | 33.89 | 0.7681 | 44.26 | 33.68 | 0.7603 |
| b4_m1024_n7168_k2048 | 4 | 1024 | 7168 | 2048 | 735 / 533 | 43.14 |
35.90 | 0.8354 | 28.94 | 26.03 | 0.8994 | 28.48 | 25.76 | 0.9040 |
| b8_m128_n128_k512 | 8 | 128 | 128 | 512 | 62 | 5.07 | 4.96 | 0.9809 |
4.86 | 4.77 | 0.9803 | 4.80 | 4.72 | 0.9833 |
| b8_m128_n512_k128 | 8 | 128 | 512 | 128 | 62 | 5.73 | 3.94 | 0.6872 |
5.41 | 3.78 | 0.6982 | 5.44 | 3.79 | 0.7000 |
| b8_m128_n4096_k7168 | 8 | 128 | 4096 | 7168 | 53 / 55 | 43.38 | 41.44
| 0.9557 | 41.82 | 41.14 | 0.9836 | 41.92 | 40.86 | 0.9733 |
| b8_m128_n7168_k2048 | 8 | 128 | 7168 | 2048 | 44 / 83 | 24.69 | 21.57
| 0.8730 | 22.19 | 22.19 | 1.0000 (same) | 22.19 | 22.18 | 0.9993 (same)
|
| b8_m256_n128_k512 | 8 | 256 | 128 | 512 | 110 | 5.18 | 5.09 | 0.9815 |
4.90 | 4.77 | 0.9739 | 4.90 | 4.77 | 0.9739 |
| b8_m256_n512_k128 | 8 | 256 | 512 | 128 | 110 | 5.76 | 4.91 | 0.8528 |
5.44 | 4.70 | 0.8713 | 5.46 | 4.67 | 0.8563 |
| b8_m256_n4096_k7168 | 8 | 256 | 4096 | 7168 | 175 / 101 | 57.28 |
55.46 | 0.9670 | 50.06 | 43.22 | 0.8629 | 50.05 | 43.17 | 0.8628 |
| b8_m256_n7168_k2048 | 8 | 256 | 7168 | 2048 | 117 / 44 | 28.77 | 25.71
| 0.8938 | 20.85 | 20.54 | 0.9854 | 20.58 | 20.46 | 0.9946 (tie) |
| b8_m1024_n128_k512 | 8 | 1024 | 128 | 512 | 380 | 5.09 | 5.09 | 1.0032
(same) | 4.93 | 4.85 | 0.9837 | 4.99 | 4.86 | 0.9744 |
| b8_m1024_n512_k128 | 8 | 1024 | 512 | 128 | 590 | 6.83 | 5.60 | 0.8174
| 6.40 | 5.34 | 0.8350 | 6.46 | 5.31 | 0.8218 |
| b8_m1024_n4096_k7168 | 8 | 1024 | 4096 | 7168 | 318 / 595 | 77.28 |
68.38 | 0.8849 | 113.70 | 92.30 | 0.8130 | 112.05 | 89.82 | 0.8020 |
| b8_m1024_n7168_k2048 | 8 | 1024 | 7168 | 2048 | 437 / 316 | 51.65 |
43.15 | 0.8371 | 38.11 | 33.57 | 0.8808 | 37.70 | 33.42 | 0.8856 |
| b64_m128_n128_k512 | 64 | 128 | 128 | 512 | 64 | 7.33 | 7.30 | 0.9956
(same) | 6.94 | 6.90 | 0.9909 (same) | 6.88 | 6.91 | 1.0093 (same) |
| b64_m128_n512_k128 | 64 | 128 | 512 | 128 | 66 | 14.43 | 7.68 | 0.5322
| 17.98 | 7.28 | 0.4048 | 18.02 | 7.25 | 0.4027 |
| b64_m128_n4096_k7168 | 64 | 128 | 4096 | 7168 | 76 / 56 | 322.48 |
291.60 | 0.9026 | 305.87 | 280.88 | 0.9181 | 305.28 | 281.76 | 0.9228 |
| b64_m128_n7168_k2048 | 64 | 128 | 7168 | 2048 | 68 | 162.91 | 146.54 |
0.8978 | 159.04 | 144.88 | 0.9103 | 159.09 | 144.13 | 0.9054 |
| b64_m256_n128_k512 | 64 | 256 | 128 | 512 | 133 | 8.03 | 8.06 | 1.0000
(same) | 7.71 | 7.78 | 1.0083 (same) | 7.71 | 7.74 | 1.0041 (same) |
| b64_m256_n512_k128 | 64 | 256 | 512 | 128 | 132 | 21.18 | 10.21 |
0.4804 | 25.92 | 10.34 | 0.3988 | 25.95 | 10.30 | 0.3971 |
| b64_m256_n4096_k7168 | 64 | 256 | 4096 | 7168 | 134 / 137 | 379.90 |
335.02 | 0.8819 | 357.71 | 317.97 | 0.8889 | 356.51 | 316.83 | 0.8887 |
| b64_m256_n7168_k2048 | 64 | 256 | 7168 | 2048 | 125 / 122 | 193.18 |
170.88 | 0.8846 | 176.98 | 160.42 | 0.9055 | 176.27 | 160.32 | 0.9093 |
| b128_m128_n128_k512 | 128 | 128 | 128 | 512 | 58 | 9.28 | 9.23 |
0.9948 (same) | 8.99 | 9.02 | 1.0071 (same) | 8.99 | 9.01 | 1.0017
(same) |
| b128_m128_n512_k128 | 128 | 128 | 512 | 128 | 65 | 34.62 | 14.11 |
0.4076 | 49.38 | 13.86 | 0.2806 | 49.41 | 13.86 | 0.2804 |
| b128_m128_n4096_k7168 | 128 | 128 | 4096 | 7168 | 64 / 67 | 645.45 |
575.96 | 0.8912 | 605.82 | 561.38 | 0.9266 | 607.30 | 562.03 | 0.9255 |
| b128_m128_n7168_k2048 | 128 | 128 | 7168 | 2048 | 59 / 60 | 327.21 |
308.14 | 0.9404 | 309.81 | 288.74 | 0.9320 | 309.43 | 286.70 | 0.9262 |
| sglang_p10_b64_m256_em1_n4096_k7168 | 64 | 256 | 4096 | 7168 | 1 |
18.62 | 14.46 | 0.7767 | 18.14 | 14.46 | 0.7972 | 18.21 | 14.53 | 0.7963
|
| sglang_p10_b64_m256_em1_n7168_k2048 | 64 | 256 | 7168 | 2048 | 1 |
13.02 | 12.85 | 0.9841 (same) | 12.16 | 12.19 | 1.0026 (same) | 12.22 |
12.16 | 0.9948 (same) |
| sglang_p50_b64_m256_em1_n4096_k7168 | 64 | 256 | 4096 | 7168 | 1 |
32.35 | 30.19 | 0.9342 | 31.87 | 29.06 | 0.9142 | 31.47 | 28.91 | 0.9191
|
| sglang_p50_b64_m256_em1_n7168_k2048 | 64 | 256 | 7168 | 2048 | 1 |
17.60 | 17.60 | 1.0000 (same) | 16.45 | 16.58 | 1.0078 (same) | 16.58 |
16.48 | 0.9961 (same) |
| sglang_p90_b64_m256_em1_n4096_k7168 | 64 | 256 | 4096 | 7168 | 1 |
59.45 | 58.94 | 0.9914 | 59.10 | 58.21 | 0.9859 | 59.49 | 58.90 | 0.9900
|
| sglang_p90_b64_m256_em1_n7168_k2048 | 64 | 256 | 7168 | 2048 | 1 |
32.82 | 32.72 | 0.9995 (same) | 31.87 | 31.82 | 0.9985 (same) | 32.00 |
31.95 | 0.9985 (same) |
| sglang_p10_b64_m256_em2_n4096_k7168 | 64 | 256 | 4096 | 7168 | 2 |
96.21 | 96.29 | 1.0008 (same) | 91.38 | 91.36 | 0.9995 (same) | 91.20 |
91.30 | 1.0007 (same) |
| sglang_p10_b64_m256_em2_n7168_k2048 | 64 | 256 | 7168 | 2048 | 2 |
49.38 | 49.34 | 0.9993 (same) | 47.66 | 47.58 | 0.9983 (same) | 47.49 |
47.57 | 1.0030 (same) |
| sglang_p50_b64_m256_em2_n4096_k7168 | 64 | 256 | 4096 | 7168 | 2 |
128.54 | 128.70 | 1.0011 (same) | 123.84 | 123.81 | 0.9999 (same) |
123.73 | 123.66 | 0.9992 (same) |
| sglang_p50_b64_m256_em2_n7168_k2048 | 64 | 256 | 7168 | 2048 | 2 |
65.06 | 65.02 | 0.9995 (same) | 63.82 | 63.84 | 1.0002 (same) | 64.00 |
63.97 | 1.0000 (same) |
| sglang_p90_b64_m256_em2_n4096_k7168 | 64 | 256 | 4096 | 7168 | 2 |
179.65 | 179.68 | 1.0006 (same) | 176.66 | 176.53 | 1.0000 (same) |
176.59 | 176.50 | 0.9996 (same) |
| sglang_p90_b64_m256_em2_n7168_k2048 | 64 | 256 | 7168 | 2048 | 2 |
90.86 | 90.97 | 1.0012 (same) | 89.92 | 89.98 | 1.0009 (same) | 89.22 |
89.30 | 1.0009 (same) |
| sglang_p10_b64_m256_em3_n4096_k7168 | 64 | 256 | 4096 | 7168 | 3 |
179.68 | 179.87 | 1.0010 (same) | 175.81 | 176.13 | 1.0018 (same) |
176.24 | 176.21 | 0.9999 (same) |
| sglang_p10_b64_m256_em3_n7168_k2048 | 64 | 256 | 7168 | 2048 | 3 |
90.54 | 90.43 | 0.9981 (same) | 89.82 | 89.89 | 1.0002 (same) | 89.70 |
89.90 | 1.0020 (same) |
| sglang_p50_b64_m256_em3_n4096_k7168 | 64 | 256 | 4096 | 7168 | 3 |
202.57 | 202.56 | 0.9998 (same) | 203.28 | 203.30 | 1.0002 (same) |
203.14 | 203.01 | 0.9992 (same) |
| sglang_p50_b64_m256_em3_n7168_k2048 | 64 | 256 | 7168 | 2048 | 3 |
103.22 | 103.06 | 0.9989 (same) | 101.74 | 101.95 | 1.0017 (same) |
101.54 | 101.63 | 1.0009 (same) |
| sglang_p90_b64_m256_em3_n4096_k7168 | 64 | 256 | 4096 | 7168 | 3 |
232.38 | 232.37 | 0.9999 (same) | 229.47 | 229.49 | 1.0001 (same) |
229.84 | 229.90 | 1.0002 (same) |
| sglang_p90_b64_m256_em3_n7168_k2048 | 64 | 256 | 7168 | 2048 | 3 |
118.13 | 118.08 | 0.9996 (same) | 116.37 | 116.38 | 1.0015 (same) |
116.45 | 116.16 | 0.9979 (same) |
| sglang_p10_b64_m256_em4_n4096_k7168 | 64 | 256 | 4096 | 7168 | 4 |
194.99 | 194.86 | 0.9998 (same) | 194.82 | 194.75 | 0.9995 (same) |
195.07 | 195.02 | 0.9998 (same) |
| sglang_p10_b64_m256_em4_n7168_k2048 | 64 | 256 | 7168 | 2048 | 4 |
99.07 | 98.94 | 0.9987 (same) | 97.60 | 97.68 | 1.0008 (same) | 97.41 |
97.52 | 1.0005 (same) |
| sglang_p50_b64_m256_em4_n4096_k7168 | 64 | 256 | 4096 | 7168 | 4 |
218.89 | 219.04 | 1.0008 (same) | 217.78 | 217.89 | 1.0006 (same) |
218.54 | 218.53 | 0.9998 (same) |
| sglang_p50_b64_m256_em4_n7168_k2048 | 64 | 256 | 7168 | 2048 | 4 |
111.90 | 111.85 | 0.9999 (same) | 109.60 | 109.74 | 1.0006 (same) |
109.51 | 109.52 | 1.0001 (same) |
| sglang_p90_b64_m256_em4_n4096_k7168 | 64 | 256 | 4096 | 7168 | 4 |
248.89 | 249.04 | 1.0006 (same) | 247.57 | 247.82 | 1.0005 (same) |
247.89 | 247.79 | 0.9996 (same) |
| sglang_p90_b64_m256_em4_n7168_k2048 | 64 | 256 | 7168 | 2048 | 4 |
126.91 | 126.85 | 0.9985 (same) | 123.71 | 123.71 | 0.9994 (same) |
124.22 | 124.11 | 0.9992 (same) |
| sglang_p10_b64_m256_em5_n4096_k7168 | 64 | 256 | 4096 | 7168 | 5 |
192.25 | 192.33 | 1.0005 (same) | 191.97 | 191.74 | 0.9989 (same) |
191.49 | 191.55 | 1.0003 (same) |
| sglang_p10_b64_m256_em5_n7168_k2048 | 64 | 256 | 7168 | 2048 | 5 |
98.48 | 98.53 | 1.0007 (same) | 96.62 | 96.91 | 1.0035 (same) | 96.30 |
96.22 | 0.9992 (same) |
| sglang_p50_b64_m256_em5_n4096_k7168 | 64 | 256 | 4096 | 7168 | 5 |
218.77 | 218.73 | 0.9996 (same) | 220.19 | 220.16 | 1.0006 (same) |
219.06 | 219.12 | 1.0003 (same) |
| sglang_p50_b64_m256_em5_n7168_k2048 | 64 | 256 | 7168 | 2048 | 5 |
112.61 | 112.54 | 0.9994 (same) | 110.00 | 110.14 | 1.0007 (same) |
110.10 | 110.40 | 1.0003 (same) |
| sglang_p90_b64_m256_em5_n4096_k7168 | 64 | 256 | 4096 | 7168 | 5 |
246.13 | 246.06 | 0.9997 (same) | 245.87 | 245.76 | 0.9993 (same) |
245.28 | 245.17 | 0.9995 (same) |
| sglang_p90_b64_m256_em5_n7168_k2048 | 64 | 256 | 7168 | 2048 | 5 |
124.90 | 124.90 | 1.0005 (same) | 122.67 | 122.67 | 0.9997 (same) |
123.09 | 122.85 | 0.9980 (same) |
| sglang_p10_b64_m256_em6_n4096_k7168 | 64 | 256 | 4096 | 7168 | 6 |
199.25 | 199.37 | 1.0007 (same) | 199.89 | 199.84 | 0.9995 (same) |
199.34 | 199.39 | 1.0005 (same) |
| sglang_p10_b64_m256_em6_n7168_k2048 | 64 | 256 | 7168 | 2048 | 6 |
101.52 | 101.47 | 0.9994 (same) | 100.18 | 100.03 | 0.9984 (same) |
100.13 | 99.89 | 0.9976 (same) |
| sglang_p50_b64_m256_em6_n4096_k7168 | 64 | 256 | 4096 | 7168 | 6 |
230.33 | 230.08 | 0.9991 (same) | 230.29 | 230.27 | 1.0003 (same) |
229.86 | 230.03 | 1.0008 (same) |
| sglang_p50_b64_m256_em6_n7168_k2048 | 64 | 256 | 7168 | 2048 | 6 |
118.38 | 118.37 | 0.9996 (same) | 115.74 | 115.70 | 0.9996 (same) |
115.62 | 115.68 | 1.0005 (same) |
| sglang_p90_b64_m256_em6_n4096_k7168 | 64 | 256 | 4096 | 7168 | 6 |
255.93 | 255.85 | 0.9997 (same) | 255.74 | 255.60 | 0.9994 (same) |
255.36 | 255.60 | 1.0008 (same) |
| sglang_p90_b64_m256_em6_n7168_k2048 | 64 | 256 | 7168 | 2048 | 6 |
131.15 | 131.25 | 1.0007 (same) | 128.21 | 128.29 | 1.0006 (same) |
128.03 | 128.13 | 1.0011 (same) |
| sglang_p10_b64_m256_em7_n4096_k7168 | 64 | 256 | 4096 | 7168 | 7 |
214.88 | 214.77 | 0.9995 (same) | 214.19 | 214.32 | 1.0006 (same) |
214.69 | 214.51 | 0.9994 (same) |
| sglang_p10_b64_m256_em7_n7168_k2048 | 64 | 256 | 7168 | 2048 | 7 |
110.02 | 110.43 | 1.0038 (same) | 108.21 | 108.16 | 1.0000 (same) |
107.94 | 108.11 | 1.0015 (same) |
| sglang_p50_b64_m256_em7_n4096_k7168 | 64 | 256 | 4096 | 7168 | 7 |
239.02 | 239.01 | 0.9999 (same) | 237.92 | 238.05 | 1.0005 (same) |
238.58 | 238.51 | 0.9995 (same) |
| sglang_p50_b64_m256_em7_n7168_k2048 | 64 | 256 | 7168 | 2048 | 7 |
123.36 | 123.33 | 0.9997 (same) | 119.83 | 119.92 | 1.0008 (same) |
119.63 | 119.50 | 0.9984 (same) |
| sglang_p90_b64_m256_em7_n4096_k7168 | 64 | 256 | 4096 | 7168 | 7 |
260.24 | 260.03 | 0.9994 (same) | 257.73 | 257.90 | 1.0010 (same) |
257.87 | 257.84 | 0.9999 (same) |
| sglang_p90_b64_m256_em7_n7168_k2048 | 64 | 256 | 7168 | 2048 | 7 |
131.45 | 131.44 | 0.9992 (same) | 128.64 | 128.64 | 0.9996 (same) |
128.56 | 128.58 | 0.9996 (same) |
| sglang_p10_b64_m256_em8_n4096_k7168 | 64 | 256 | 4096 | 7168 | 8 |
215.81 | 216.01 | 1.0010 (same) | 215.78 | 215.74 | 0.9999 (same) |
214.99 | 215.14 | 1.0002 (same) |
| sglang_p10_b64_m256_em8_n7168_k2048 | 64 | 256 | 7168 | 2048 | 8 |
110.81 | 110.77 | 0.9988 (same) | 108.80 | 108.64 | 0.9996 (same) |
108.32 | 108.48 | 1.0024 (same) |
| sglang_p50_b64_m256_em8_n4096_k7168 | 64 | 256 | 4096 | 7168 | 8 |
246.35 | 246.35 | 1.0006 (same) | 245.86 | 246.03 | 1.0008 (same) |
245.76 | 245.70 | 0.9997 (same) |
| sglang_p50_b64_m256_em8_n7168_k2048 | 64 | 256 | 7168 | 2048 | 8 |
127.20 | 127.09 | 0.9997 (same) | 124.13 | 124.11 | 0.9994 (same) |
123.98 | 123.89 | 0.9992 (same) |
| sglang_p90_b64_m256_em8_n4096_k7168 | 64 | 256 | 4096 | 7168 | 8 |
265.20 | 265.05 | 0.9994 (same) | 263.97 | 263.65 | 0.9993 (same) |
263.84 | 264.05 | 1.0009 (same) |
| sglang_p90_b64_m256_em8_n7168_k2048 | 64 | 256 | 7168 | 2048 | 8 |
136.13 | 136.10 | 0.9995 (same) | 133.17 | 133.12 | 0.9996 (same) |
132.50 | 132.62 | 1.0005 (same) |
| sglang_p10_b64_m512_em8_n4096_k7168 | 64 | 512 | 4096 | 7168 | 8 |
221.63 | 221.68 | 1.0002 (same) | 222.03 | 221.95 | 0.9999 (same) |
222.03 | 221.97 | 0.9999 (same) |
| sglang_p10_b64_m512_em8_n7168_k2048 | 64 | 512 | 7168 | 2048 | 8 |
114.78 | 114.78 | 0.9989 (same) | 111.79 | 112.19 | 1.0032 (same) |
112.48 | 112.32 | 0.9983 (same) |
| sglang_p50_b64_m512_em8_n4096_k7168 | 64 | 512 | 4096 | 7168 | 8 |
245.42 | 245.55 | 1.0005 (same) | 243.78 | 244.11 | 1.0014 (same) |
245.20 | 245.25 | 1.0002 (same) |
| sglang_p50_b64_m512_em8_n7168_k2048 | 64 | 512 | 7168 | 2048 | 8 |
126.78 | 126.67 | 0.9981 (same) | 122.56 | 122.56 | 1.0010 (same) |
122.82 | 122.50 | 0.9984 (same) |
| sglang_p90_b64_m512_em8_n4096_k7168 | 64 | 512 | 4096 | 7168 | 8 |
267.34 | 267.36 | 0.9989 (same) | 267.90 | 267.84 | 0.9998 (same) |
267.25 | 267.34 | 1.0005 (same) |
| sglang_p90_b64_m512_em8_n7168_k2048 | 64 | 512 | 7168 | 2048 | 8 |
137.79 | 137.71 | 0.9995 (same) | 133.86 | 134.08 | 1.0017 (same) |
134.70 | 134.58 | 0.9999 (same) |
| sglang_p10_b32_m256_em1_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 1 |
5.18 | 2.46 | 0.4753 | 4.99 | 2.40 | 0.4808 | 4.99 | 2.40 | 0.4808 |
| sglang_p10_b32_m256_em1_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 1 |
5.18 | 5.17 | 0.9938 (same) | 5.02 | 2.40 | 0.4777 | 4.96 | 2.38 |
0.4806 |
| sglang_p50_b32_m256_em1_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 1 |
19.17 | 18.19 | 0.9482 | 18.78 | 17.47 | 0.9302 | 18.66 | 17.54 | 0.9400
|
| sglang_p50_b32_m256_em1_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 1 |
13.20 | 13.09 | 0.9916 (same) | 12.67 | 12.45 | 0.9823 | 12.78 | 12.38 |
0.9687 |
| sglang_p90_b32_m256_em1_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 1 |
38.59 | 38.34 | 0.9934 | 37.94 | 37.63 | 0.9924 | 38.35 | 38.00 | 0.9925
|
| sglang_p90_b32_m256_em1_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 1 |
22.67 | 22.34 | 0.9851 (same) | 21.25 | 21.18 | 0.9925 | 21.22 | 21.06 |
0.9924 (tie) |
| sglang_p10_b32_m256_em2_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 2 |
46.98 | 46.86 | 0.9976 (same) | 46.74 | 46.53 | 0.9945 (same) | 46.98 |
47.06 | 1.0004 (same) |
| sglang_p10_b32_m256_em2_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 2 |
24.40 | 24.43 | 1.0013 (same) | 24.38 | 23.68 | 0.9699 (same) | 23.36 |
23.46 | 1.0027 (same) |
| sglang_p50_b32_m256_em2_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 2 |
79.06 | 79.02 | 0.9996 (same) | 74.40 | 74.50 | 1.0002 (same) | 74.72 |
74.59 | 0.9985 (same) |
| sglang_p50_b32_m256_em2_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 2 |
40.26 | 40.29 | 1.0008 (same) | 39.81 | 39.60 | 0.9948 (same) | 39.52 |
39.58 | 1.0016 (same) |
| sglang_p90_b32_m256_em2_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 2 |
83.89 | 83.94 | 1.0006 (same) | 84.00 | 84.02 | 1.0015 (same) | 83.57 |
83.70 | 1.0015 (same) |
| sglang_p90_b32_m256_em2_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 2 |
44.37 | 44.58 | 1.0032 (same) | 43.73 | 43.52 | 0.9963 (same) | 43.78 |
43.55 | 0.9945 (same) |
| sglang_p10_b32_m256_em3_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 3 |
87.34 | 87.26 | 0.9989 (same) | 87.02 | 86.94 | 0.9991 (same) | 87.26 |
87.20 | 0.9989 (same) |
| sglang_p10_b32_m256_em3_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 3 |
46.90 | 46.70 | 0.9959 (same) | 45.01 | 44.86 | 0.9964 (same) | 45.34 |
45.39 | 1.0018 (same) |
| sglang_p50_b32_m256_em3_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 3 |
99.84 | 99.70 | 0.9989 (same) | 100.48 | 100.51 | 1.0003 (same) | 100.18
| 100.16 | 1.0000 (same) |
| sglang_p50_b32_m256_em3_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 3 |
52.75 | 52.98 | 1.0030 (same) | 51.41 | 51.20 | 0.9978 (same) | 51.94 |
51.55 | 0.9932 (same) |
| sglang_p90_b32_m256_em3_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 3 |
130.67 | 130.72 | 0.9998 (same) | 131.62 | 131.65 | 1.0002 (same) |
132.43 | 132.56 | 1.0010 (same) |
| sglang_p90_b32_m256_em3_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 3 |
66.59 | 66.42 | 0.9973 (same) | 66.06 | 66.03 | 0.9995 (same) | 65.86 |
66.19 | 1.0051 (same) |
| sglang_p10_b32_m256_em4_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 4 |
100.16 | 100.13 | 1.0000 (same) | 99.70 | 99.92 | 1.0014 (same) | 99.44
| 99.49 | 1.0005 (same) |
| sglang_p10_b32_m256_em4_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 4 |
52.64 | 52.58 | 0.9988 (same) | 52.13 | 51.68 | 0.9914 (same) | 51.36 |
51.44 | 1.0009 (same) |
| sglang_p50_b32_m256_em4_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 4 |
115.79 | 115.82 | 1.0004 (same) | 115.90 | 115.76 | 0.9983 (same) |
115.58 | 115.68 | 1.0011 (same) |
| sglang_p50_b32_m256_em4_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 4 |
61.47 | 61.34 | 0.9974 (same) | 58.96 | 59.33 | 1.0062 (same) | 58.56 |
58.69 | 1.0005 (same) |
| sglang_p90_b32_m256_em4_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 4 |
119.68 | 119.81 | 1.0005 (same) | 119.17 | 119.23 | 1.0005 (same) |
119.14 | 119.20 | 1.0005 (same) |
| sglang_p90_b32_m256_em4_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 4 |
62.14 | 62.16 | 1.0005 (same) | 61.39 | 61.63 | 1.0034 (same) | 61.70 |
61.50 | 0.9974 (same) |
| sglang_p10_b32_m256_em5_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 5 |
96.78 | 96.70 | 0.9988 (same) | 96.21 | 96.18 | 0.9995 (same) | 96.19 |
96.18 | 0.9993 (same) |
| sglang_p10_b32_m256_em5_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 5 |
50.69 | 50.51 | 0.9968 (same) | 49.14 | 49.18 | 0.9997 (same) | 48.96 |
48.85 | 0.9990 (same) |
| sglang_p50_b32_m256_em5_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 5 |
110.83 | 110.80 | 1.0003 (same) | 110.06 | 110.10 | 1.0003 (same) |
110.35 | 110.40 | 1.0004 (same) |
| sglang_p50_b32_m256_em5_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 5 |
57.17 | 57.07 | 0.9972 (same) | 54.86 | 54.99 | 1.0047 (same) | 54.96 |
54.88 | 1.0026 (same) |
| sglang_p90_b32_m256_em5_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 5 |
126.99 | 127.04 | 1.0001 (same) | 126.18 | 126.18 | 0.9997 (same) |
126.30 | 126.21 | 0.9995 (same) |
| sglang_p90_b32_m256_em5_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 5 |
65.12 | 65.07 | 0.9980 (same) | 63.20 | 63.14 | 0.9975 (same) | 63.02 |
63.17 | 1.0025 (same) |
| sglang_p10_b32_m256_em6_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 6 |
87.42 | 87.39 | 1.0007 (same) | 87.26 | 87.31 | 0.9994 (same) | 87.22 |
87.20 | 0.9996 (same) |
| sglang_p10_b32_m256_em6_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 6 |
46.98 | 47.49 | 1.0109 (same) | 44.77 | 44.82 | 1.0007 (same) | 44.83 |
44.86 | 1.0007 (same) |
| sglang_p50_b32_m256_em6_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 6 |
123.95 | 124.00 | 1.0003 (same) | 123.41 | 123.30 | 0.9997 (same) |
123.39 | 123.44 | 1.0003 (same) |
| sglang_p50_b32_m256_em6_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 6 |
64.29 | 63.81 | 0.9945 (same) | 61.82 | 61.89 | 1.0010 (same) | 61.84 |
61.78 | 0.9990 (same) |
| sglang_p90_b32_m256_em6_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 6 |
137.41 | 137.33 | 0.9991 (same) | 137.06 | 137.18 | 1.0009 (same) |
137.01 | 136.70 | 0.9981 (same) |
| sglang_p90_b32_m256_em6_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 6 |
69.69 | 69.66 | 0.9998 (same) | 68.78 | 68.75 | 1.0012 (same) | 68.93 |
68.93 | 1.0000 (same) |
| sglang_p10_b32_m256_em7_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 7 |
112.35 | 112.51 | 1.0011 (same) | 112.45 | 112.42 | 1.0009 (same) |
112.14 | 112.21 | 0.9997 (same) |
| sglang_p10_b32_m256_em7_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 7 |
58.34 | 58.16 | 0.9978 (same) | 57.58 | 57.54 | 0.9970 (same) | 57.25 |
57.49 | 1.0042 (same) |
| sglang_p50_b32_m256_em7_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 7 |
119.68 | 119.52 | 0.9987 (same) | 119.55 | 119.49 | 0.9993 (same) |
119.17 | 119.26 | 1.0009 (same) |
| sglang_p50_b32_m256_em7_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 7 |
62.53 | 62.70 | 1.0028 (same) | 61.81 | 61.65 | 0.9992 (same) | 61.55 |
61.57 | 1.0003 (same) |
| sglang_p90_b32_m256_em7_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 7 |
129.06 | 129.38 | 1.0022 (same) | 128.69 | 128.56 | 0.9990 (same) |
128.54 | 128.50 | 1.0005 (same) |
| sglang_p90_b32_m256_em7_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 7 |
66.43 | 66.24 | 0.9966 (same) | 65.65 | 65.52 | 0.9976 (same) | 65.82 |
65.89 | 1.0005 (same) |
| sglang_p10_b32_m256_em8_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 8 |
110.58 | 110.51 | 0.9991 (same) | 110.11 | 110.18 | 1.0004 (same) |
109.89 | 110.19 | 1.0028 (same) |
| sglang_p10_b32_m256_em8_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 8 |
57.41 | 57.42 | 1.0003 (same) | 54.85 | 54.82 | 0.9994 (same) | 54.98 |
54.66 | 0.9968 (same) |
| sglang_p50_b32_m256_em8_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 8 |
119.50 | 119.54 | 1.0005 (same) | 119.58 | 119.58 | 0.9995 (same) |
119.22 | 119.14 | 0.9993 (same) |
| sglang_p50_b32_m256_em8_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 8 |
63.33 | 63.52 | 1.0030 (same) | 61.38 | 61.22 | 0.9979 (same) | 61.20 |
61.12 | 0.9989 (same) |
| sglang_p90_b32_m256_em8_n4096_k7168_ep8 | 32 | 256 | 4096 | 7168 | 8 |
135.90 | 135.90 | 1.0000 (same) | 135.60 | 135.63 | 0.9999 (same) |
135.39 | 135.36 | 0.9995 (same) |
| sglang_p90_b32_m256_em8_n7168_k2048_ep8 | 32 | 256 | 7168 | 2048 | 8 |
70.85 | 70.62 | 0.9975 (same) | 68.91 | 69.02 | 1.0005 (same) | 68.82 |
68.78 | 1.0005 (same) |
| sglang_p10_b32_m512_em8_n4096_k7168_ep8 | 32 | 512 | 4096 | 7168 | 8 |
117.50 | 117.41 | 0.9990 (same) | 116.94 | 116.74 | 0.9981 (same) |
117.04 | 116.96 | 0.9993 (same) |
| sglang_p10_b32_m512_em8_n7168_k2048_ep8 | 32 | 512 | 7168 | 2048 | 8 |
61.44 | 61.66 | 1.0036 (same) | 59.04 | 59.12 | 1.0019 (same) | 59.22 |
58.98 | 0.9962 (same) |
| sglang_p50_b32_m512_em8_n4096_k7168_ep8 | 32 | 512 | 4096 | 7168 | 8 |
127.38 | 127.18 | 0.9985 (same) | 126.16 | 126.16 | 1.0000 (same) |
126.53 | 126.48 | 1.0006 (same) |
| sglang_p50_b32_m512_em8_n7168_k2048_ep8 | 32 | 512 | 7168 | 2048 | 8 |
65.63 | 65.46 | 0.9980 (same) | 63.10 | 63.15 | 1.0008 (same) | 63.12 |
63.06 | 1.0008 (same) |
| sglang_p90_b32_m512_em8_n4096_k7168_ep8 | 32 | 512 | 4096 | 7168 | 8 |
132.93 | 132.88 | 0.9996 (same) | 131.98 | 131.97 | 1.0000 (same) |
131.71 | 131.81 | 1.0012 (same) |
| sglang_p90_b32_m512_em8_n7168_k2048_ep8 | 32 | 512 | 7168 | 2048 | 8 |
67.79 | 67.89 | 0.9998 (same) | 67.30 | 67.20 | 1.0005 (same) | 67.39 |
67.47 | 1.0000 (same) |

The other Cake variants are `cake_grouped_fp8_gemm` (contiguous, FP32 or
UE8M0 scales) and `cake_grouped_fp8_fused_silu_quant` (gate/up + SwiGLU
+ FP8 quant), and this kernel covers `sm_100a` (B200) and `sm_103a`
(GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added and updated CUDA-accelerated FP8 batched matrix multiplication
options, including support for varied shapes and group-wise workloads.
* Serving plans can now select architecture-specific programs, with a
fallback to generic programs.

* **Bug Fixes**
* Updated serving configuration for a specific workload and improved
routing and grid sizing for selected matrix shapes.

* **Tests**
* Added coverage for multiple grouped matrix shapes, including checks
that valid output rows match the reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [445980c](https://github.com/flashinfer-ai/flashinfer/commit/445980cc611a92c83805d18dec0c14e6fdaed220)

- **作者**: eigen
- **时间**: 2026-10-26T09:42:59Z
- **提交信息**: perf(cake_gdn): faster forward prep, tape stores and dqkg kernels (#7423)

Cake's context-parallel GDN training kernel has one data-type variant
(BF16 q/k/v/out/dout, FP32 g and beta) and three partition layouts:
contiguous, whole-buffer zigzag, and per-document zigzag + ragged. Its
fused forms are forward, backward from the saved set, checkpoint replay
(non-reentrant and reentrant), and an optional causal-conv1d halo
exchange. This PR delivers the same variant with three faster kernels:
forward prep, the tape-writing forward kernels, and the fused dq/dk/dg
kernel. Its outputs are bit for bit identical to the previous version.
Against the previous version of this package (FlashInfer PR #7169 as
merged), the geometric-mean speedups are 1.064x forward and 1.042x per
training step on GB300, each over 60 rows. On GB200 they are 1.067x and
1.043x, and the tables below give every row with absolute latencies.
Measured latencies, slowest rank, median over repeats:

**NVIDIA GB300 (sm_103a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats). Forward = module
forward; training step = forward + checkpoint recompute + backward,
communication included. Baseline: the previous version of this package
(#7169) on the same layout.

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | previous ms
| Speedup | Training step: this PR ms | previous ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 8.590 | 9.127 | 1.06x
| 26.872 | 28.179 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 8.624 | 9.187 | 1.07x |
27.098 | 28.461 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
8.968 | 9.456 | 1.05x | 27.774 | 28.946 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 4.791 | 5.244 | 1.09x
| 14.839 | 15.830 | 1.07x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 4.926 | 5.393 | 1.09x |
15.163 | 16.191 | 1.07x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
4.822 | 5.088 | 1.06x | 14.866 | 15.512 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.700 | 2.938 | 1.09x
| 8.183 | 8.597 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 2.945 | 3.171 | 1.08x |
8.660 | 9.157 | 1.06x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
2.889 | 3.005 | 1.04x | 8.557 | 8.879 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 2.237 | 2.355 | 1.05x
| 7.224 | 7.274 | 1.01x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 1.892 | 1.998 | 1.06x |
6.069 | 6.098 | 1.00x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
2.199 | 2.240 | 1.02x | 7.256 | 7.225 | 1.00x |
| P2 (261,987 / 3) | 2 | contiguous | 9.222 | 9.855 | 1.07x | 29.155 |
30.599 | 1.05x |
| P2 (261,987 / 3) | 2 | zigzag | 9.364 | 10.090 | 1.08x | 29.350 |
31.011 | 1.06x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 9.419 | 10.114 |
1.07x | 29.804 | 31.423 | 1.05x |
| P2 (261,987 / 3) | 4 | contiguous | 4.825 | 5.137 | 1.06x | 14.911 |
15.667 | 1.05x |
| P2 (261,987 / 3) | 4 | zigzag | 5.083 | 5.531 | 1.09x | 15.732 |
16.731 | 1.06x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.425 | 5.883 |
1.08x | 16.533 | 17.551 | 1.06x |
| P2 (261,987 / 3) | 8 | contiguous | 2.806 | 2.951 | 1.05x | 8.345 |
8.695 | 1.04x |
| P2 (261,987 / 3) | 8 | zigzag | 3.165 | 3.413 | 1.08x | 9.290 | 9.853
| 1.06x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 3.047 | 3.351 |
1.10x | 9.091 | 9.709 | 1.07x |
| P2 (261,987 / 3) | 16 | contiguous | 2.207 | 2.274 | 1.03x | 7.190 |
7.306 | 1.02x |
| P2 (261,987 / 3) | 16 | zigzag | 1.977 | 2.092 | 1.06x | 6.172 | 6.252
| 1.01x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 2.029 | 2.161 |
1.06x | 6.675 | 6.783 | 1.02x |
| P3 (259,174 / 2) | 2 | contiguous | 7.869 | 8.191 | 1.04x | 28.903 |
29.728 | 1.03x |
| P3 (259,174 / 2) | 2 | zigzag | 10.122 | 10.810 | 1.07x | 31.696 |
33.302 | 1.05x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 9.089 | 9.730 |
1.07x | 28.719 | 30.258 | 1.05x |
| P3 (259,174 / 2) | 4 | contiguous | 5.094 | 5.466 | 1.07x | 15.908 |
16.757 | 1.05x |
| P3 (259,174 / 2) | 4 | zigzag | 5.508 | 6.057 | 1.10x | 16.911 |
18.107 | 1.07x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 5.401 | 5.947 |
1.10x | 16.622 | 17.681 | 1.06x |
| P3 (259,174 / 2) | 8 | contiguous | 2.908 | 2.953 | 1.02x | 8.377 |
8.554 | 1.02x |
| P3 (259,174 / 2) | 8 | zigzag | 3.287 | 3.399 | 1.03x | 9.261 | 9.785
| 1.06x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 3.180 | 3.407 |
1.07x | 9.256 | 9.878 | 1.07x |
| P3 (259,174 / 2) | 16 | contiguous | 2.281 | 2.388 | 1.05x | 7.230 |
7.334 | 1.01x |
| P3 (259,174 / 2) | 16 | zigzag | 1.974 | 2.092 | 1.06x | 6.182 | 6.222
| 1.01x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 2.028 | 2.183 |
1.08x | 6.432 | 6.404 | 1.00x |
| P4 (254,976 / 1) | 2 | contiguous | 9.063 | 9.567 | 1.06x | 28.419 |
29.759 | 1.05x |
| P4 (254,976 / 1) | 2 | zigzag | 9.264 | 9.986 | 1.08x | 29.063 |
30.733 | 1.06x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 9.308 | 10.048 |
1.08x | 29.181 | 30.869 | 1.06x |
| P4 (254,976 / 1) | 4 | contiguous | 4.681 | 5.002 | 1.07x | 14.519 |
15.282 | 1.05x |
| P4 (254,976 / 1) | 4 | zigzag | 4.701 | 5.042 | 1.07x | 14.605 |
15.359 | 1.05x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 4.856 | 5.216 |
1.07x | 15.092 | 15.893 | 1.05x |
| P4 (254,976 / 1) | 8 | contiguous | 2.757 | 2.856 | 1.04x | 8.061 |
8.326 | 1.03x |
| P4 (254,976 / 1) | 8 | zigzag | 3.108 | 3.357 | 1.08x | 9.162 | 9.660
| 1.05x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 3.140 | 3.421 |
1.09x | 9.264 | 9.916 | 1.07x |
| P4 (254,976 / 1) | 16 | contiguous | 2.201 | 2.239 | 1.02x | 7.133 |
7.198 | 1.01x |
| P4 (254,976 / 1) | 16 | zigzag | 1.997 | 2.127 | 1.06x | 6.196 | 6.276
| 1.01x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.446 | 2.454 |
1.00x | 7.594 | 7.615 | 1.00x |
| P5 (249,856 / 4) | 2 | contiguous | 8.874 | 9.575 | 1.08x | 28.186 |
29.770 | 1.06x |
| P5 (249,856 / 4) | 2 | zigzag | 9.553 | 10.368 | 1.09x | 30.123 |
31.718 | 1.05x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 9.077 | 9.768 |
1.08x | 28.517 | 29.999 | 1.05x |
| P5 (249,856 / 4) | 4 | contiguous | 4.924 | 5.259 | 1.07x | 15.330 |
16.122 | 1.05x |
| P5 (249,856 / 4) | 4 | zigzag | 5.253 | 5.759 | 1.10x | 16.121 |
17.248 | 1.07x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 4.942 | 5.245 |
1.06x | 15.229 | 15.956 | 1.05x |
| P5 (249,856 / 4) | 8 | contiguous | 2.737 | 2.850 | 1.04x | 8.399 |
8.444 | 1.01x |
| P5 (249,856 / 4) | 8 | zigzag | 3.060 | 3.275 | 1.07x | 8.913 | 9.450
| 1.06x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 2.851 | 3.043 |
1.07x | 8.527 | 8.949 | 1.05x |
| P5 (249,856 / 4) | 16 | contiguous | 2.266 | 2.361 | 1.04x | 7.352 |
7.361 | 1.00x |
| P5 (249,856 / 4) | 16 | zigzag | 1.917 | 2.074 | 1.08x | 6.142 | 6.300
| 1.03x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.047 | 2.126 |
1.04x | 6.816 | 6.987 | 1.03x |

Geometric mean speedup over the 60 forward rows: 1.064x; over the 60
training-step rows: 1.042x.

**NVIDIA GB200 (sm_100a, CUDA 13.4)** — context-parallel GDN layer,
`(H_qk, HV) = (16, 48)`, head dim 128, CP = 2, 4, 8, 16; latency per
call of the slowest rank (median over repeats). Forward = module
forward; training step = forward + checkpoint recompute + backward,
communication included. Baseline: the previous version of this package
(#7169) on the same layout.

| Pack (tokens / docs) | CP | Layout | Forward: this PR ms | previous ms
| Speedup | Training step: this PR ms | previous ms | Speedup |
|---|---:|---|---:|---:|---:|---:|---:|---:|
| P1 (241,817 tokens / 6 docs) | 2 | contiguous | 8.738 | 9.297 | 1.06x
| 27.441 | 28.804 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 2 | zigzag | 8.759 | 9.342 | 1.07x |
27.628 | 29.030 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 2 | per-document zigzag + ragged |
9.127 | 9.630 | 1.06x | 28.341 | 29.565 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 4 | contiguous | 4.882 | 5.305 | 1.09x
| 15.109 | 16.095 | 1.07x |
| P1 (241,817 tokens / 6 docs) | 4 | zigzag | 5.018 | 5.474 | 1.09x |
15.452 | 16.484 | 1.07x |
| P1 (241,817 tokens / 6 docs) | 4 | per-document zigzag + ragged |
4.918 | 5.168 | 1.05x | 15.172 | 15.795 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 8 | contiguous | 2.735 | 2.958 | 1.08x
| 8.279 | 8.697 | 1.05x |
| P1 (241,817 tokens / 6 docs) | 8 | zigzag | 2.979 | 3.203 | 1.08x |
8.788 | 9.276 | 1.06x |
| P1 (241,817 tokens / 6 docs) | 8 | per-document zigzag + ragged |
2.904 | 3.048 | 1.05x | 8.694 | 9.052 | 1.04x |
| P1 (241,817 tokens / 6 docs) | 16 | contiguous | 2.174 | 2.280 | 1.05x
| 7.073 | 7.274 | 1.03x |
| P1 (241,817 tokens / 6 docs) | 16 | zigzag | 1.881 | 2.010 | 1.07x |
5.927 | 6.054 | 1.02x |
| P1 (241,817 tokens / 6 docs) | 16 | per-document zigzag + ragged |
2.148 | 2.228 | 1.04x | 7.049 | 7.163 | 1.02x |
| P2 (261,987 / 3) | 2 | contiguous | 9.400 | 10.029 | 1.07x | 29.776 |
31.269 | 1.05x |
| P2 (261,987 / 3) | 2 | zigzag | 9.522 | 10.257 | 1.08x | 29.920 |
31.666 | 1.06x |
| P2 (261,987 / 3) | 2 | per-document zigzag + ragged | 9.604 | 10.325 |
1.08x | 30.516 | 32.178 | 1.05x |
| P2 (261,987 / 3) | 4 | contiguous | 4.923 | 5.234 | 1.06x | 15.224 |
15.990 | 1.05x |
| P2 (261,987 / 3) | 4 | zigzag | 5.186 | 5.619 | 1.08x | 16.055 |
17.082 | 1.06x |
| P2 (261,987 / 3) | 4 | per-document zigzag + ragged | 5.488 | 5.928 |
1.08x | 16.831 | 17.872 | 1.06x |
| P2 (261,987 / 3) | 8 | contiguous | 2.821 | 2.978 | 1.06x | 8.409 |
8.775 | 1.04x |
| P2 (261,987 / 3) | 8 | zigzag | 3.197 | 3.414 | 1.07x | 9.397 | 9.932
| 1.06x |
| P2 (261,987 / 3) | 8 | per-document zigzag + ragged | 3.069 | 3.335 |
1.09x | 9.187 | 9.772 | 1.06x |
| P2 (261,987 / 3) | 16 | contiguous | 2.196 | 2.359 | 1.07x | 7.198 |
7.356 | 1.02x |
| P2 (261,987 / 3) | 16 | zigzag | 1.959 | 2.079 | 1.06x | 6.037 | 6.126
| 1.01x |
| P2 (261,987 / 3) | 16 | per-document zigzag + ragged | 2.012 | 2.155 |
1.07x | 6.478 | 6.563 | 1.01x |
| P3 (259,174 / 2) | 2 | contiguous | 8.058 | 8.377 | 1.04x | 29.438 |
30.301 | 1.03x |
| P3 (259,174 / 2) | 2 | zigzag | 10.263 | 10.964 | 1.07x | 32.214 |
33.852 | 1.05x |
| P3 (259,174 / 2) | 2 | per-document zigzag + ragged | 9.222 | 9.881 |
1.07x | 29.331 | 30.909 | 1.05x |
| P3 (259,174 / 2) | 4 | contiguous | 5.164 | 5.546 | 1.07x | 16.201 |
17.087 | 1.05x |
| P3 (259,174 / 2) | 4 | zigzag | 5.586 | 6.158 | 1.10x | 17.141 |
18.429 | 1.08x |
| P3 (259,174 / 2) | 4 | per-document zigzag + ragged | 5.481 | 6.028 |
1.10x | 16.882 | 18.132 | 1.07x |
| P3 (259,174 / 2) | 8 | contiguous | 2.847 | 2.977 | 1.05x | 8.417 |
8.725 | 1.04x |
| P3 (259,174 / 2) | 8 | zigzag | 3.181 | 3.414 | 1.07x | 9.340 | 9.905
| 1.06x |
| P3 (259,174 / 2) | 8 | per-document zigzag + ragged | 3.119 | 3.412 |
1.09x | 9.356 | 10.000 | 1.07x |
| P3 (259,174 / 2) | 16 | contiguous | 2.173 | 2.223 | 1.02x | 7.092 |
7.202 | 1.02x |
| P3 (259,174 / 2) | 16 | zigzag | 1.965 | 2.074 | 1.06x | 6.059 | 6.150
| 1.02x |
| P3 (259,174 / 2) | 16 | per-document zigzag + ragged | 2.016 | 2.210 |
1.10x | 6.321 | 6.410 | 1.01x |
| P4 (254,976 / 1) | 2 | contiguous | 9.164 | 9.732 | 1.06x | 29.014 |
30.402 | 1.05x |
| P4 (254,976 / 1) | 2 | zigzag | 9.384 | 10.128 | 1.08x | 29.600 |
31.337 | 1.06x |
| P4 (254,976 / 1) | 2 | per-document zigzag + ragged | 9.419 | 10.177 |
1.08x | 29.669 | 31.412 | 1.06x |
| P4 (254,976 / 1) | 4 | contiguous | 4.753 | 5.089 | 1.07x | 14.797 |
15.604 | 1.05x |
| P4 (254,976 / 1) | 4 | zigzag | 4.796 | 5.110 | 1.07x | 14.887 |
15.662 | 1.05x |
| P4 (254,976 / 1) | 4 | per-document zigzag + ragged | 4.955 | 5.295 |
1.07x | 15.398 | 16.217 | 1.05x |
| P4 (254,976 / 1) | 8 | contiguous | 2.775 | 2.874 | 1.04x | 8.211 |
8.473 | 1.03x |
| P4 (254,976 / 1) | 8 | zigzag | 3.129 | 3.366 | 1.08x | 9.247 | 9.766
| 1.06x |
| P4 (254,976 / 1) | 8 | per-document zigzag + ragged | 3.138 | 3.432 |
1.09x | 9.374 | 10.021 | 1.07x |
| P4 (254,976 / 1) | 16 | contiguous | 2.152 | 2.178 | 1.01x | 7.077 |
7.044 | 1.00x |
| P4 (254,976 / 1) | 16 | zigzag | 1.974 | 2.098 | 1.06x | 6.042 | 6.048
| 1.00x |
| P4 (254,976 / 1) | 16 | per-document zigzag + ragged | 2.269 | 2.418 |
1.07x | 7.456 | 7.496 | 1.01x |
| P5 (249,856 / 4) | 2 | contiguous | 9.051 | 9.754 | 1.08x | 28.742 |
30.381 | 1.06x |
| P5 (249,856 / 4) | 2 | zigzag | 9.708 | 10.547 | 1.09x | 30.682 |
32.360 | 1.05x |
| P5 (249,856 / 4) | 2 | per-document zigzag + ragged | 9.239 | 9.941 |
1.08x | 29.110 | 30.664 | 1.05x |
| P5 (249,856 / 4) | 4 | contiguous | 4.988 | 5.338 | 1.07x | 15.611 |
16.455 | 1.05x |
| P5 (249,856 / 4) | 4 | zigzag | 5.320 | 5.853 | 1.10x | 16.345 |
17.542 | 1.07x |
| P5 (249,856 / 4) | 4 | per-document zigzag + ragged | 5.000 | 5.333 |
1.07x | 15.514 | 16.291 | 1.05x |
| P5 (249,856 / 4) | 8 | contiguous | 2.798 | 2.916 | 1.04x | 8.255 |
8.482 | 1.03x |
| P5 (249,856 / 4) | 8 | zigzag | 3.063 | 3.284 | 1.07x | 9.009 | 9.503
| 1.05x |
| P5 (249,856 / 4) | 8 | per-document zigzag + ragged | 2.891 | 3.069 |
1.06x | 8.682 | 9.075 | 1.05x |
| P5 (249,856 / 4) | 16 | contiguous | 2.244 | 2.328 | 1.04x | 7.321 |
7.250 | 0.99x |
| P5 (249,856 / 4) | 16 | zigzag | 1.920 | 2.028 | 1.06x | 6.038 | 6.035
| 1.00x |
| P5 (249,856 / 4) | 16 | per-document zigzag + ragged | 2.011 | 2.067 |
1.03x | 6.743 | 6.811 | 1.01x |

Geometric mean speedup over the 60 forward rows: 1.067x; over the 60
training-step rows: 1.043x.

Cake's GDN inference kernels for chunked prefill and decode ship
separately, the KDA context-parallel training sibling
`flashinfer/experimental/cake_kda_train` covers the per-channel-gate
form, and this kernel ships on sm_100a, sm_103a and sm_107a.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7ccb13b](https://github.com/flashinfer-ai/flashinfer/commit/7ccb13b8e781c3afde3daef8ceac9fbd75842ac6)

- **作者**: Yuhang He
- **时间**: 2026-10-26T08:36:38Z
- **提交信息**: perf(prims-ts): shorter Keeps softmax chain and grouped-Q paged selection for decode (#6937)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR makes PrimTS decode (`fmha_decode`) faster in two ways: the
kernel spends less time waiting on the softmax, and the paged planner
picks a much better tile for multi-token decode.

### 1. Kernel: keep the tensor core busy while the softmax runs

In a two-instance Q128/KV128 Keeps tile, P overwrites S in TMEM. Each
instance can therefore start its next QK only after its PV has consumed
P, and the softmax of the next tile in turn waits for that QK. The
result is a serial chain in which the tensor core sits idle while the
softmax runs. This PR breaks up that chain:

- **16-bit K/V**: the softmax hands P to the PV MMA in four K32
fragments instead of one full row, so PV starts as soon as the first
fragment is ready. On SM100, part of the exponentials move to the FMA
pipe, and the kernel spills far fewer registers.
- **8-bit K/V (FP8 and Sage)**: P goes to SMEM instead of TMEM, and the
softmax keeps the scores in registers. S is freed right after the max
pass, so the next QK is issued before the current PV and runs alongside
the exponentials.
- **Masking**: tiles that load the full score row now choose between the
masked and unmasked load path before reading S, so fully visible tiles
skip the masking work altogether.
- **Rescaling**: every Keeps tile keeps its softmax anchor when the row
maximum grows only slightly, which avoids most in-place rescales of O.

These changes speed up dense `BlockSparseTSWrapper` plans and paged
launches that use a Q128 Keeps tile. Block-sparse Q128/KV128 routes only
pick up the larger FMA share of the exponentials on SM100 (about 1%
faster on B200); block-sparse KV256 (Q64), Q64 Keeps and Swaps kernels
are untouched.

### 2. Planner: use grouped Keeps Q128 for paged multi-token decode

For unpinned, fixed multi-token paged launches with page size 32, a cost
model chooses the Q tile, but until now it only ran for causal masks.
Dense launches fell back to a Swaps tile per query token, which re-reads
the K/V cache once for every token. On top of that, FP16/BF16 had no
grouped Keeps Q128 recipe for paged K/V at all.

With this PR, the cost model also covers dense launches, and 16-bit
paged K/V can use the grouped Keeps Q128 tile. No new kernel is needed:
the tile reuses the existing contiguous 16-bit Q128 kernel together with
the paged K/V loads of the FP8 path. The 16-bit recipe is chosen
automatically only where the cost model scores it; single-token,
variable-length and other page-size launches keep their current plans.

### 3. Sage follow-ups to #6617

The last commit applies the review comments of #6617 to the shared Sage
code. Both kernels now read `sfQ` through one helper in `sage/index.py`,
the helpers in `sage/` carry `sage` in their names (`flat_scale_numel`
becomes `sage_flat_scale_numel`), `SageKTransport` names its values
`GMEM` and `SMEM`, and the context plan's prepared-scale state moves to
`sage/plan.py`. The decode and context Sage kernels compile to the same
SASS as before.

The commit messages include before/after measurements for each change.

## 📈 Performance

All measurements are on B200 and GB300.

### Kernel changes

Compared with `main` (`3bf6d3202`), using ncu `sm__cycles_elapsed.max`
(`--clock-control none`), averaged over two runs with the GPUs rotated.

**Dense layer** (Mcycles): B=2, S=75600, H=40, D=128 through the dense
`BlockSparseTSWrapper` plan (Q128/KV128). Sage uses FP8 Q/K/V with K
smoothing; kN is the K block size in tokens.

| plan | B200 before → after | speedup | GB300 before → after | speedup
|
| --- | ---: | ---: | ---: | ---: |
| BF16 | 336.6 → 261.9 | 1.29x | 293.6 → 206.5 | 1.42x |
| Sage k16 | 275.7 → 253.4 | 1.09x | 203.4 → 187.4 | 1.09x |
| Sage k4 | 287.2 → 258.4 | 1.11x | 216.6 → 191.1 | 1.13x |
| Sage k1 | 319.7 → 252.8 | 1.26x | 258.0 → 198.2 | 1.30x |

**Paged decode** on the Q128 Keeps tile (kcycles): 8 K/V heads, 8192 K/V
tokens per request, page size 32. Hr is the number of Q heads per K/V
head, Sq the query tokens per request, and B the batch size.

| launch | B200 before → after | speedup | GB300 before → after |
speedup |
| --- | ---: | ---: | ---: | ---: |
| BF16, Hr128 Sq1 B32 | 313.1 → 288.1 | 1.09x | 321.4 → 313.4 | 1.03x |
| FP8, Hr8 Sq256 B64 | 5442 → 4925 | 1.11x | 3950 → 3845 | 1.03x |
| FP8 causal, Hr8 Sq256 B64 | 5545 → 4980 | 1.11x | 4140 → 3955 | 1.05x
|
| FP8 head dim 64, Hr8 Sq256 B64 | 5413 → 4773 | 1.13x | 3983 → 3667 |
1.09x |
| FP8, Hr128 Sq1 B32 | 226.3 → 206.9 | 1.09x | 178.8 → 182.3 | 0.98x |

The BF16 dense layer gains the most, since PV now overlaps the softmax
and far fewer registers spill. The 8-bit and Sage tiles benefit from
issuing the next QK early and from skipping the mask pass on fully
visible tiles; Sage k1 additionally stops writing its dequantized scores
back to TMEM. On GB300 the paged FP8 gains are smaller, and the
single-token Hr128 launch (one Q128 tile per K/V head and request) is 2%
slower. Paged Q64 Keeps, Swaps and KV256 launches stay within run-to-run
noise (-2.1% to +0.7%).

### Plan selection

To isolate the selection change, both plans run with this PR's kernels:
the previous automatic plan is pinned and timed against the new one,
interleaved in the same process (CUPTI median in µs, averaged over two
runs on different GPUs). Paged decode with 8 K/V heads, 8192 K/V tokens
per request and page size 32; Hq/Hkv is the number of Q heads per K/V
head. FP8 already had a grouped Keeps Q128 recipe, but dense launches
never reached the cost model, so dense FP8 benefits as well.

| launch (mask, dtype, Hq/Hkv, Sq, batch) | plan before → after | B200
before → after (µs) | speedup | GB300 before → after (µs) | speedup |
| --- | --- | ---: | ---: | ---: | ---: |
| dense BF16, 8, 64, 16 | Swaps Q8 → Keeps Q128 | 2016 → 596 | 3.4x |
2129 → 778 | 2.7x |
| dense BF16, 8, 256, 64 | Swaps Q8 → Keeps Q128 | 26372 → 4786 | 5.5x |
25797 → 4626 | 5.6x |
| dense BF16, 32, 32, 64 | Swaps Q32 → Keeps Q128 | 5278 → 2997 | 1.8x |
5862 → 3411 | 1.7x |
| dense FP8, 8, 128, 64 | Swaps Q8 → Keeps Q128 | 8780 → 2708 | 3.2x |
8928 → 3105 | 2.9x |
| dense FP8, 32, 32, 64 | Swaps Q32 → Keeps Q128 | 4056 → 2701 | 1.5x |
4474 → 3115 | 1.4x |
| causal BF16, 8, 64, 64 | Keeps Q64/KV256 → Keeps Q128 | 2292 → 2175 |
1.05x | 2967 → 2814 | 1.05x |
| causal BF16, 8, 256, 64 | Keeps Q64/KV256 → Keeps Q128 | 5327 → 4932 |
1.08x | 5247 → 4680 | 1.12x |

On a wider grid of 84 automatic launches (both dtypes and masks; Hq/Hkv
8 with Sq 16-256 and Hq/Hkv 32 with Sq 8-32; batch 4-64), 57 launches
switch plans, 55 of them to grouped Keeps Q128. Their latency changes by
-82.0% to -0.2% on B200 and by -81.9% to +1.2% on GB300. FP8 causal
launches keep their plans.

## 🔍 Related Issues

The query-paired decode topology (draft #6859) will build on top of this
PR.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
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

- **Tests**: the decode-side suites (decode, block-sparse, Q-token
block-sparse metadata, Sage, features and decode backend; 1252 tests)
pass on both B200 (1250 passed, 1 skipped) and GB300 (1242 passed, 9
skipped). The only failure,
`test_attention_ts_features.py::test_public_attention_disk_cache_in_fresh_processes`,
also fails on `main`.
- **Numerics**: keeping the softmax anchor changes the numerics of Keeps
tiles with 16-bit P and of dense wrapper plans with 8-bit P; the latter
now quantize P against the anchor headroom, as block-sparse plans
already do. Paged FP8 plans keep exact anchors, and the test reference
uses the same anchor rule.
- **Unchanged kernels**: kernels described as unchanged (BF16 Q128, Q64
Keeps, Swaps, block-sparse Sage) were verified by comparing normalized
SASS before and after the corresponding commit.
- **Cost model**: the 16-bit Q128 mainloop factor in the cost model
(3.2) was calibrated before the kernel changes made that tile faster, so
the planner may now pick it less often than it should.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded automatic decode selection for supported paged, multi-token
attention workloads, including 16-bit Q128 profiles.
* Added Sage attention support for dense Q128/KV128 profiles, with
scaling behavior based on block size.

* **Improvements**
* Updated score processing and softmax handling across supported decode
profiles, including dense and block-sparse attention.
* Refined decode execution for different query and key/value precision
combinations.

* **Documentation**
* Clarified supported profiles, scaling behavior, and decode arithmetic.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b669461](https://github.com/flashinfer-ai/flashinfer/commit/b6694615b3a280e7526de79f5aa5ddcf56bbb4fb)

- **作者**: yunruis
- **时间**: 2026-10-26T08:34:44Z
- **提交信息**: perf(prims-ts): prefetch page IDs for FP8 2CTA dense MLA K/V loaders (#7019)

## 📌 Description

**Impact:** FP8 PrimTS dense MLA decode served by `throughput_2cta`
(auto-selected when `num_heads * seq_len_q > 64`, e.g. 128 heads, or
when it avoids a 1CTA split-KV) no longer slows down super-linearly at
large batch.

| Measured on B200, H128, K8192 | Speedup |
|---|---|
| B128, page 16 | **2.40x** |
| B128-256, page 32 | **1.43-1.46x** |
| B128, pages 64/128 | 1.00-1.02x (main did not have the problem) |
| B32-64 | 1.01-1.08x |
| B ≤ 8 | within ±1% |

Outputs are bitwise identical to main. No API change. BF16 2CTA and the
1CTA kernel compile to SASS identical to main.

**Problem.** The FP8 split-MMA schedule's K and V loader warps read each
K tile's page IDs from the block table in global memory. They do this
*after* acquiring a free SMEM slot, and only then issue the TMA. Every K
tile therefore pays a full global-load latency between slot release and
TMA issue, on the critical path to the QK MMA. The cost grows with pages
per tile (128 / page size).
- FP8 B128 K8192 page 32 took 198 us on main, against about 2 × 73 us
expected from B64.
- ncu (B64 K8192 page 32): the QK MMA warp waits for K 49% of the time,
and the K loader is stalled on the page-table load 19% of the time.
- Other dense paths already avoid this: the BF16 loader caches a
32-entry page-ID window in registers, and the 1CTA kernel prefetches
page offsets into SMEM.

**Change.**
- The dense FP8 K/V loaders take page IDs from a per-lane register
window (one table entry per lane, 32 per warp;
`PageOffsetWindowResource.read_dense_{k,v}_window`), the same window
shape as BF16. The K and V loaders each keep their own window.
- The window is read before the slot wait. The next window's load is
issued at the start of the current window, only when the next window
starts inside the current work tile. The first window of each work tile
is loaded synchronously.
- `SmemKResource.tma_load_paged` / `SmemVResource.tma_load_paged` now
take the IDs (`cached_page_ids`). The per-tile GMEM lookups and the
dense schedules without a window are removed.
- `make_mla_decode_config` checks the window geometry for every dense
path, BF16 and FP8: a window holds whole K tiles, so `pages_per_k_tile`
must divide 32. Every supported page size (16/32/64/128) meets this with
the 128-token K tile. The sparse page-size-1 path is unchanged.

**Performance.** B200 (1965 MHz max SM clock),
`benchmarks/flashinfer_benchmark.py --routine
BatchMLAPagedAttentionWrapper --backends prims-ts`, CUDA graph + CUPTI,
`--num_iters 200 --dry_run_iters 50`, s_qo 1, fixed KV lengths, randomly
permuted page tables. Times are medians of 3 rounds, alternating main /
this PR (main = 6a2f2661d). Each row is one testlist line:

`--routine BatchMLAPagedAttentionWrapper --backends prims-ts --page_size
P --s_qo 1 --num_kv_heads 1 --head_dim_ckv 512 --head_dim_kpe 64
--num_iters 200 --dry_run_iters 50 --batch_size B --s_kv K
--num_qo_heads H --q_dtype D --kv_dtype D`

Page 32:

| dtype | kernel | H | B | KV len | main (us) | this PR (us) | speedup |
|---|---|---|---|---|---|---|---|
| FP8 | 2CTA | 128 | 1 | 8192 | 17.34 | 18.18 | 0.954x* |
| FP8 | 2CTA | 128 | 8 | 8192 | 22.48 | 22.35 | 1.006x |
| FP8 | 2CTA | 128 | 16 | 4096 | 22.11 | 22.05 | 1.003x |
| FP8 | 2CTA | 128 | 32 | 8192 | 49.36 | 47.90 | 1.030x |
| FP8 | 2CTA | 128 | 64 | 4096 | 44.16 | 42.53 | 1.038x |
| FP8 | 2CTA | 128 | 64 | 8192 | 72.75 | 70.82 | 1.027x |
| FP8 | 2CTA | 128 | 128 | 8192 | 198.31 | 135.78 | 1.461x |
| FP8 | 2CTA | 128 | 148 | 8192 | 202.00 | 141.79 | 1.425x |
| FP8 | 2CTA | 128 | 256 | 4096 | 204.82 | 142.11 | 1.441x |
| BF16 (control) | 2CTA | 128 | 64 | 4096 | 79.39 | 79.54 | 0.998x |
| BF16 (control) | 2CTA | 128 | 128 | 8192 | 274.40 | 268.98 | 1.020x |
| BF16 (control) | 1CTA | 32 | 32 | 8192 | 86.14 | 87.46 | 0.985x |
| FP8 (control) | 1CTA | 32 | 32 | 8192 | 48.91 | 49.04 | 0.997x |

FP8, H 128, other page sizes:

| page | B | KV len | main (us) | this PR (us) | speedup |
|---|---|---|---|---|---|
| 16 | 8 | 8192 | 23.36 | 22.69 | 1.030x |
| 16 | 64 | 4096 | 47.25 | 43.65 | 1.082x |
| 16 | 128 | 8192 | 339.73 | 141.71 | 2.397x |
| 64 | 8 | 8192 | 22.78 | 22.29 | 1.022x |
| 64 | 64 | 4096 | 43.10 | 42.53 | 1.014x |
| 64 | 128 | 8192 | 136.06 | 135.87 | 1.001x |
| 128 | 8 | 8192 | 22.50 | 22.37 | 1.006x |
| 128 | 64 | 4096 | 43.52 | 42.82 | 1.016x |
| 128 | 128 | 8192 | 137.30 | 134.34 | 1.022x |

The controls (BF16 2CTA and the 1CTA kernel do not use the changed
loaders) show this session's noise floor, about ±1.5%.

\* FP8 B1 varies by ±1.5 us per round in this harness. A longer CUPTI
measurement (7 rounds of 200 iterations, main/PR/main/PR, FP8 H128 page
32) puts B ≤ 8 within ±1%:

| B | KV len | main (us) | this PR (us) | change |
|---|---|---|---|---|
| 1 | 8192 | 19.52 / 19.55 | 19.36 / 19.41 | -0.7% |
| 2 | 8192 | 19.49 / 19.49 | 19.46 / 19.46 | 0.0% |
| 4 | 8192 | 20.66 / 20.67 | 20.80 / 20.80 | +0.7% |
| 8 | 8192 | 22.38 / 22.37 | 22.27 / 22.27 | -0.5% |
| 1 | 32768 | 23.63 / 23.63 | 23.86 / 23.84 | +0.9% |

## 🔍 Related Issues

Experimental PrimTS API tracking: #5082 and #5229.

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

New test: `test_attention_ts_mla_decode_fp8_2cta_page_window` (split-KV
page 16, page 16, page 128). In every case the longest request's work
tiles span more than one window, so the loaders swap in the prefetched
window. The existing 2CTA page-size test stays within one window per
work tile.

Local SM100 run on this head (688e04b2e):
`tests/attention/test_attention_ts_mla_decode.py` +
`tests/attention/test_attention_ts_sparse_mla.py`, 245 passed.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5082 (and #5229). It changes kernel internals behind
the existing PrimTS MLA decode API, with no API change.
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/test_experimental_api.py
```

## Reviewer Notes

- **Real coverage.** The experimental lane target above follows earlier
PrimTS PRs (#6774), but it does not import PrimTS. The coverage for this
change is `tests/attention/test_attention_ts_mla_decode.py` on SM100 in
the normal lane.
- **Prefetch slack.** ptxas copies the loop-carried next-window register
at the start of the following K tile, so the prefetch has one K tile of
slack rather than a full window. Measured B128 matches or beats an
identity-page-table probe (no page-table loads at all), so one tile
covers the load latency.
- **Registers.** The FP8 loader warps run at 32 registers. Local-memory
traffic is unchanged versus main.
- **Out-of-table fragments.** These now read the clamped last table
column, as the BF16 window does, instead of page 0. The runtime length
masks them either way.
- **BF16.** The BF16 window keeps its synchronous refresh at each window
boundary. Sharing one window implementation between BF16 and FP8 (and
giving BF16 the prefetch) changes BF16 SASS and is left to a follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* FP8 2-CTA decoding now reuses and prefetches page-ID windows for dense
paged K/V inputs across supported page sizes and batch sizes.
* Page-table boundaries are handled safely during decoding, with
out-of-range entries clamped and masked by runtime sequence length.
* BF16 page-window refresh behavior and supported page-size constraints
are documented.
* **Bug Fixes**
* Dense page configurations that exceed the supported page-window
geometry now raise a clear error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [39c34ab](https://github.com/flashinfer-ai/flashinfer/commit/39c34abafcf224bbc1de904d61f1bfad0333d9c1)

- **作者**: Wookje Han
- **时间**: 2026-10-26T08:09:06Z
- **提交信息**: perf(gemm): SM107 SMEM and split-K 8 for the BF16 cluster split-K GEMM (#7064)

## 📌 Description

**Depends on #6833** (stacked on its head `ba7cf1920`); this PR will be
rebased onto `main` once #6833 lands, leaving only the last commit.

SM107 has more shared memory per CTA than SM100/SM103. This PR lets the
BF16 cluster split-K kernel (`dense_bf16_gemm_sm100_splitk.py`, the
`cute-dsl` backend of `mm_bf16` for M <= 32) use it and adds a cluster-K
split of 8 there:

- `_arch(device)` returns the CuTeDSL arch whose per-CTA SMEM the device
provides (`"sm_107"` on SM107, else `"sm_100"`). The SMEM capacity that
`autotune_tactics` and `validate_tactic` use when `smem_capacity` is not
given (the current device's), the capacity `run_splitk_dense` validates
against (the input's device), and the dynamic SMEM requested at launch
follow it.
- `autotune_tactics` enumerates `split_k=8` on SM107 only, where it was
measured; `validate_tactic` accepts it on any arch (cluster size 8 is
portable).
- `_MAX_AB_STAGES` 12 -> 18. On SM100/SM103 the SMEM capacity still caps
every tactic at 12 stages, so their tactic space is unchanged.
- For long K (`K > 4 * CTA_K`), `autotune_tactics` no longer limits
stages to the three just below the SMEM cap; the existing
`_WEIGHT_BYTES_IN_FLIGHT` floor in `_keep_autotune_tactic` prunes the
shallow ones. With SM107's higher cap the old window (e.g. 16-18 stages)
dropped the best depths (e.g. 11). The list is a superset of the
previous one wherever the cap is unchanged; on SM100/SM103 it only adds
9-stage tactics for 64-row tiles.

On SM100/SM103, `default_tactic` and launches are unchanged; the
autotune list gains only the 9-stage tactics noted above (a superset of
the previous list). The warp split-K and direct kernels are not touched:
a full per-tactic sweep on SM107 showed no gain for warp split-K from
the larger SMEM (best tactic with SM107 SMEM vs within the SM100 limit:
geomean 0.9996), and the direct kernel has no SMEM pipeline.

### Performance (SM107)

Setup: one SM107 GPU. For every (N, K, M) cell, each tactic in the
autotune list is timed with `flashinfer.testing.bench_gpu_time` under
`flashinfer_benchmark.py`'s `mm_bf16` settings (CUPTI, CUDA graphs, cold
L2, 5 dry-run + 30 timed iterations); the table shows the best tactic of
the list, i.e. what `--autotune` selects. Before = #6833's
`autotune_tactics` run through #6833's `run_splitk_dense`; after = this
PR's, same node, same job. bf16 in/out, no bias.

Median µs, before -> after:

| shape (N×K) | M=1 | M=2 | M=4 | M=8 | M=16 | M=24 | M=32 | geomean |
|---|---|---|---|---|---|---|---|---|
| muse-spark o_proj TP4 (8192×2048) | 6.14 → 6.08 | 6.02 → 5.98 | 6.18 →
6.08 | 6.03 → 6.05 | 6.38 → 6.30 | 6.18 → 6.18 | 6.46 → 6.43 | 0.993 |
| muse-spark o_proj TP8 (8192×1024) | 4.38 → 4.38 | 4.51 → 4.48 | 4.45 →
4.45 | 4.51 → 4.51 | 4.48 → 4.48 | 4.64 → 4.56 | 4.56 → 4.54 | 0.996 |
| muse-spark pooler_slice TP4 (1024×8192) | 4.82 → 4.54 | 4.83 → 4.58 |
4.99 → 4.67 | 4.94 → 4.61 | 5.20 → 5.06 | 5.31 → 5.31 | 5.50 → 5.38 |
0.958 |
| muse-spark qkvg TP4 (4608×8192) | 9.66 → 9.65 | 9.62 → 9.50 | 9.54 →
9.54 | 9.57 → 9.54 | 9.73 → 9.70 | 10.14 → 10.06 | 10.18 → 10.16 | 0.996
|
| muse-spark qkvg TP8 (2304×8192) | 6.80 → 6.62 | 6.75 → 6.72 | 6.98 →
6.90 | 6.53 → 6.53 | 6.91 → 6.93 | 7.17 → 7.15 | 7.14 → 7.15 | 0.994 |
| muse-spark unpooler_slice TP4 (2048×4096) | 4.50 → 4.50 | 4.54 → 4.51
| 4.48 → 4.48 | 4.53 → 4.54 | 4.80 → 4.80 | 5.06 → 5.10 | 5.09 → 5.10 |
1.001 |
| muse-spark unpooler_slice TP8 (1024×4096) | 4.03 → 3.78 | 4.03 → 3.82
| 4.13 → 3.81 | 4.05 → 3.82 | 4.10 → 4.10 | 4.38 → 4.35 | 4.38 → 4.42 |
0.964 |
| deepseek-v3 o_proj TP8 (7168×2048) | 5.76 → 5.78 | 5.63 → 5.60 | 5.74
→ 5.79 | 5.66 → 5.63 | 5.97 → 6.00 | 5.89 → 5.89 | 6.14 → 6.05 | 0.998 |
| deepseek-v3 q_b_proj TP8 (3072×1536) | 3.90 → 3.87 | 3.82 → 3.81 |
3.87 → 3.81 | 3.97 → 3.87 | 3.98 → 4.03 | 4.13 → 4.14 | 4.18 → 4.22 |
0.996 |
| llama3-8b down_proj (4096×14336) | 12.88 → 12.91 | 12.85 → 12.82 |
12.93 → 12.83 | 12.90 → 12.88 | 13.17 → 13.10 | 13.76 → 13.39 | 13.76 →
13.50 | 0.992 |
| llama3-8b gate_up_proj (28672×4096) | 23.97 → 24.02 | 24.18 → 24.14 |
24.03 → 23.98 | 24.10 → 24.10 | 24.34 → 24.46 | 25.70 → 25.66 | 25.66 →
25.82 | 1.001 |
| llama3-8b o_proj (4096×4096) | 6.21 → 6.18 | 6.27 → 6.26 | 6.08 → 6.10
| 6.34 → 6.30 | 6.27 → 6.24 | 6.62 → 6.51 | 6.64 → 6.54 | 0.993 |
| llama3-8b qkv_proj (6144×4096) | 7.34 → 7.30 | 7.36 → 7.34 | 7.46 →
7.33 | 7.33 → 7.36 | 7.50 → 7.46 | 7.63 → 7.54 | 7.63 → 7.54 | 0.992 |

Overall geomean 0.990 over 91 cells; 8 cells are >=3% faster (up to 8%),
no cell is >=2% slower (worst +1.2%).

- **split_k=8** wins the narrow, long-K shapes (N=1024, K=4096/8192) at
M <= 8 by 5-8%: with split <= 4 they cannot fill the GPU.
- **Deeper stages** help long K at M=24-32 by 1-3%.
- `default_tactic` (no-autotune path) is unchanged by design: geomean
after/before 0.999.
- split_k 12 and 16 (non-portable cluster sizes) were also measured on
SM107 and never won: their best tactic was 1.3x-11x slower than the best
without them, so they are not added.

## 🔍 Related Issues

Depends on #6833.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on the changed file; all hooks
pass.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (No new tests;
`mm_bf16(backend="cute-dsl")` tests autotune over the SM107 tactic space
on SM107.)
- [x] All tests are passing (`unittest`, etc.).

On SM107:
- `pytest tests/gemm/test_mm_bf16.py -k cute`: 10 passed.
- Every tactic in the sweep above (8,719 timings, splits 1/2/3/4/8,
stages up to 18) was checked against an FP32 reference: max relative
error 3.6e-3.

Not run on SM100/SM103. There, launches and `default_tactic` are
unchanged by construction, and the autotune list is a superset of the
previous one (checked on SM107 with the SM100 capacity forced), so
autotune can only find the same or a faster tactic.

## Reviewer Notes

- This PR does not change `_keep_autotune_tactic` (#6833's pruning
rules); it only widens the stage window `autotune_tactics` generates for
long K, which those rules then prune. One observation for #6833 itself
from the SM107 sweep: the `_WEIGHT_BYTES_IN_FLIGHT` stage floor does not
account for the K tiles each CTA actually processes (`K / 128 /
split_k`), so for small per-CTA K it can drop the best (shallower) ring;
capping the floor at the per-CTA K tile count recovered every such cell
in our data. This affects SM100 as well and is left to #6833.
- AI-assisted: the change and the measurements were prepared with Claude
Code and reviewed by the author.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance Improvements**
* Improved BF16 matrix multiplication tactic selection across a wider
range of shapes, with tuning that adapts to device capabilities.
* Refined kernel selection for small and narrow workloads to better
match their size.

* **Hardware Support**
* Added support for an additional split-K configuration on SM107
devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f810e74](https://github.com/flashinfer-ai/flashinfer/commit/f810e74b5e4d8b902d56bcd98314165ad48aba84)

- **作者**: Enwei Zhu
- **时间**: 2026-10-26T07:22:30Z
- **提交信息**: fix: package Kimi K3 MoE and router JIT sources (#7107)

<!-- .github/pull_request_template.md -->

## 📌 Description

Include the existing CUDA sources and shared headers for
`kimi_k3_latent_moe` (MoE front/tail) and `kimi_k3_fused_router` in
`flashinfer-python` distributions.

Both JIT loaders resolve sources under their installed package's `csrc/`
directory. With `include-package-data = false` and no entries for these
packages, wheels omit those files and the loaders cannot compile their
kernels. This adds the two missing package-data entries; kernel code and
dispatch are unchanged.

## 🔍 Related Issues

Related: #6205 addresses the same packaging issue for a different
experimental backend.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validation performed with temporary CPU packaging checks; no test file
is included in this PR:

- Both package checks fail with the original package-data configuration.
- All four build-output and wheel-content checks pass with the change.
- Built a non-editable wheel with native EP builds disabled and verified
all 49 registered CUDA source paths and four shared headers are
included, byte-for-byte identical to the checkout.
- `pre-commit run --all-files` passes.

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

Packaging-only fix. No changes to kernels, SM support, or runtime
behavior beyond making the existing JIT sources available in the
installed package.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Package distributions now include the supporting files for
experimental components, improving their availability when the package
is installed or distributed. No user-facing behavior changes are
included in this update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Enwei Zhu <21126786+syuoni@users.noreply.github.com>

### [f2ebfdc](https://github.com/flashinfer-ai/flashinfer/commit/f2ebfdc8c4431586c793149483c913a12ffb2d7c)

- **作者**: Wookje Han
- **时间**: 2026-10-26T07:19:32Z
- **提交信息**: perf(gemm): SM107 TGV tactics with deeper A/B pipelines (#7049)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

SM107 has more shared memory compared to SM100/SM103. The TGV cute_ext
kernel always launched with the SM100 capacity, so on SM107 its A/B
pipelines were sized for the smaller part.

This PR appends 18 SM107-only TGV tactics (ids 29–46). They reuse the
existing 18 tile shapes, each with the deepest A/B pipeline that fits
the SM107 SMEM, and launch with the SM107 capacity:

- `tgv_gemm_cute_ext.py`:
- the new tactic entries after the existing ones, so tactic ids 0–28
keep their meaning on every arch;
- `TgvGemmCuteExtKernel(arch=...)`, stored as `self.arch`, picks the
launch SMEM (`get_smem_capacity_in_bytes(self.arch)`). `arch` is also
part of the compile-cache key;
- `get_tgv_cute_ext_valid_tactics(device)` returns ids 0–46 on SM107 and
0–28 elsewhere. `run_tgv_cute_ext` raises if an SM107-only tactic is
requested on another arch.
- `gemm_base.py`: the TGV runner's `get_valid_tactics` uses
`get_tgv_cute_ext_valid_tactics(inputs[0].device)`.

Tactics 0–28 keep their SMEM request on SM107 too (232,448 B), so the
existing SM107 behaviour is unchanged. On SM100/SM103 the generated
kernels and the tactic space are identical to `main`.


Setup:
- SM107
- `benchmarks/flashinfer_benchmark.py --routine mm_bf16 --backends tgv
--autotune --refcheck` (CUPTI, CUDA graphs, cold L2).
- Before = `main` TGV, after = this PR, same node, same job.

`flashinfer_benchmark.py` keeps one autotune cache per process and the
BF16 GEMM tuner buckets M (next power of 2 up to 256). Each side
therefore ran as two processes whose M values sit in distinct buckets
(1,2,4,…,1024 and 24,48,96,192,384), so no M reuses another M's tactic.
13 shapes × 17 M values (1–1024), bf16 in/out.

after/before per shape (geomean over the 17 M values):

| shape | N | K | geomean after/before | min | max |
|---|---|---|---|---|---|
| llama3-8b down_proj | 4096 | 14336 | 0.938 | 0.86 | 1.01 |
| muse-spark pooler_slice TP4 | 1024 | 8192 | 0.966 | 0.92 | 1.02 |
| muse-spark qkvg TP4 | 4608 | 8192 | 0.953 | 0.89 | 1.01 |
| llama3-8b gate_up_proj | 28672 | 4096 | 0.970 | 0.94 | 1.01 |
| llama3-8b o_proj | 4096 | 4096 | 0.985 | 0.93 | 1.05 |
| llama3-8b qkv_proj | 6144 | 4096 | 0.990 | 0.95 | 1.01 |
| muse-spark unpooler_slice TP4 | 2048 | 4096 | 0.991 | 0.94 | 1.02 |
| gpt-oss-120b qkv_proj TP4 (bias) | 1280 | 2880 | 1.003 | 0.94 | 1.10 |
| deepseek-v3 o_proj TP8 | 7168 | 2048 | 1.006 | 0.99 | 1.03 |
| muse-spark o_proj TP4 | 8192 | 2048 | 1.013 | 0.98 | 1.06 |
| deepseek-v3 q_b_proj TP8 | 3072 | 1536 | 0.997 | 0.96 | 1.04 |
| gpt-oss-120b o_proj TP4 (bias) | 2880 | 1024 | 1.022 | 0.99 | 1.05 |
| muse-spark o_proj TP8 | 8192 | 1024 | 1.017 | 0.99 | 1.04 |

Overall geomean 0.988 over 221 cells. 62 cells are ≥3% faster, 16 are
≥3% slower.

Median µs, before → after:

| shape (N×K) | M=1 | M=8 | M=32 | M=64 | M=128 | M=256 | M=512 | M=1024
|
|---|---|---|---|---|---|---|---|---|
| llama3-8b down_proj (4096×14336) | 15.97 → 14.54 | 15.90 → 14.43 |
16.53 → 15.09 | 17.66 → 16.53 | 20.08 → 19.30 | 24.48 → 23.79 | 40.05 →
34.35 | 70.16 → 67.31 |
| muse-spark pooler_slice (1024×8192) | 7.81 → 7.17 | 7.71 → 7.15 | 7.68
→ 7.17 | 7.81 → 7.55 | 8.34 → 8.18 | 9.38 → 9.38 | 11.34 → 11.57 | 15.36
→ 15.23 |
| muse-spark qkvg (4608×8192) | 10.64 → 9.97 | 10.66 → 9.98 | 10.88 →
10.50 | 11.52 → 11.17 | 13.38 → 12.75 | 16.67 → 16.88 | 26.48 → 24.48 |
45.42 → 44.85 |
| llama3-8b gate_up_proj (28672×4096) | 24.69 → 24.69 | 24.80 → 24.58 |
26.14 → 25.22 | 27.84 → 26.32 | 31.18 → 30.53 | 52.48 → 50.93 | 93.06 →
88.61 | 173.20 → 165.89 |
| llama3-8b o_proj (4096×4096) | 6.48 → 6.14 | 6.34 → 6.02 | 6.82 → 6.37
| 7.17 → 7.04 | 8.22 → 8.19 | 10.35 → 10.45 | 15.62 → 15.26 | 24.98 →
24.87 |
| muse-spark o_proj TP4 (8192×2048) | 6.26 → 6.14 | 6.24 → 6.40 | 6.40 →
6.56 | 6.69 → 7.12 | 7.60 → 7.68 | 10.64 → 10.78 | 17.39 → 17.90 | 25.87
→ 25.92 |
| gpt-oss-120b qkv_proj (1280×2880) | 4.54 → 4.70 | 4.62 → 4.54 | 4.64 →
5.09 | 4.74 → 4.80 | 5.09 → 5.17 | 5.79 → 5.92 | 7.03 → 7.17 | 9.76 →
9.90 |

- **Long K (≥ 4096, i.e. ≥ 32 K tiles) is the target.** The deeper
pipeline keeps more weight bytes in flight per SM, giving 3–14% lower
latency there.
- **Short K (≤ 2880, at most 23 K tiles) is neutral.** 14 of the 16
cells that are 3–10% slower are short-K; the other two are llama3-8b
o_proj (K=4096) at M=48 (1.05) and M=192 (1.04). They come from the
autotuner choosing among near-equal tactics (the slower cells are about
1–2 run-to-run std apart), not from a slower kernel: the new tactic set
contains every old tactic unchanged.
- **A per-tactic sweep (cold L2, CUDA graph) of 11 such cells confirms
this.** It shows the best tactic of the new set is never slower than the
best old one, and a fresh autotune picks the best tactic or one within
about 2% of it.

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

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On SM107:
- `pytest tests/gemm/test_tgv_gemm.py tests/gemm/test_mm_bf16.py
tests/gemm/test_bmm_bf16.py -k tgv`: 112 passed, 32 skipped. The skips
are by design: "bmm_bf16 with TGV backend only supports bfloat16
output".
- A per-tactic check of all 47 tactics through `run_tgv_cute_ext`
against an fp32 reference passed (423/423 cases). Coverage: M ∈ {1, 5,
8, 37, 64, 130, 200, 256, 1024}, Muse-Spark / Llama-style shapes, and
bias.

Not run on SM100/SM103. The tactic space and generated kernels there are
unchanged by construction.

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
  * Added support for additional GEMM configurations on SM107 GPUs.
* **Improvements**
* Available GEMM tactics now match the device architecture, helping
prevent incompatible selections. Existing devices continue to use their
supported configurations.
  * In debug mode, 2D inputs can use the C++ runner’s tactic options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0aec993](https://github.com/flashinfer-ai/flashinfer/commit/0aec9936bd044650c65c8efa7d674da52dec95e3)

- **作者**: eigen
- **时间**: 2026-10-26T07:19:04Z
- **提交信息**: perf(cake_kimi_k3_attn_res): held-release K = 5 dense and K = 1 snapshot-write programs on SM103 (#7411)

This PR changes routes of the Cake AttnRes operator,
`flashinfer.experimental.cake_kimi_k3_attn_res`. It is exposed as
`flashinfer.kimi_k3_attn_res.prepare_kimi_k3_attn_res` and
`kimi_k3_attn_res`. The operator runs residual add, an optional snapshot
write, K+1 candidate scoring, softmax, mix and output RMSNorm in one
launch. It takes BF16 inputs with hidden size 7168 and K in [0, 8]. It
has one data type, one layout and two fused forms: dense and snapshot
write. This PR changes the routes of 4 cells, all on sm_103a, at both
PDL modes each. The new programs hold the release of the consumed buffer
until the end of the chunk ("held release"). The old programs released
it early.

- **B300 and GB300, dense M 1024, K 5:** both GPUs now use one new
held-release K = 5 program with the BF16 prefix add (fast math,
three-deep chunk ring). It replaces the early-release K = 5 program
(fast math, three-deep chunk ring).
- **B300, snapshot write M 1024, K 1 (block 1):** each PDL mode gets its
own new held-release write program with a three-deep chunk ring, the
register carry and the packed output-norm cache. The PDL-on program also
has the expanded output-norm cache. Both are built without fast math.
- **GB300, snapshot write M 4096, K 1 (block 1):** each PDL mode gets
its own new held-release write program with the register carry and the
packed output-norm cache. The PDL-on program also has the expanded
output-norm cache. Both are built with fast math.

The new write programs replace early-release write programs. Those stay
shipped because other cells still use them. The program set goes from
180 programs (210 libraries: 96 sm_100a, 114 sm_103a) to 184 programs
(214 libraries: 96 sm_100a, 118 sm_103a). The PR adds the 5 held-release
sm_103a programs above. It removes the early-release K = 5 program
because no route reaches it any more.

The baseline is the previous Cake version of this operator, merged in PR
#7374. Two shapes change on each GPU. On B300 they are M 1024, K 5
(dense) and M 1024, K 1 (snapshot write, block 1). On GB300 they are M
1024, K 5 (dense) and M 4096, K 1 (snapshot write, block 1). All 4
changed shapes are faster at both PDL modes. The ratios are 1.0054 to
1.0216 on B300 and 1.0145 to 1.0236 on GB300. Times are CUPTI kernel
times with cold L2, from paired interleaved ABBA sampling with 3 groups
× 300 samples per arm; the ratio is the geometric mean, over the three
groups, of the per-group median ratio previous / new.

B200 (sm_100a) routes do not change, so there is no B200 table. Every
other shape runs the same program as the previous version, and the other
209 program/library pairs have identical SASS to the previous version.
Their timings are the ones listed in PRs #6980, #7014, #7338 and #7374.

NVIDIA B300 SXM6 AC (sm_103a, 148 SMs), driver 580.126.09, CUDA 13.4.92,
torch 2.14.1+cu130.
| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 1024, K 5 (dense) | 26.784 | 26.209 | 1.0216 | 26.753 | 26.208 |
1.0208 |
| M 1024, K 1 (snapshot write, block 1) | 18.049 | 17.952 | 1.0054 |
17.984 | 17.808 | 1.0087 |

NVIDIA GB300 (sm_103a, 152 SMs), driver 580.159.03, CUDA 13.4.92, torch
2.14.1+cu130.
| Shape | Previous µs (PDL off) | New µs (PDL off) | Ratio | Previous µs
(PDL on) | New µs (PDL on) | Ratio |
|---|---|---|---|---|---|---|
| M 1024, K 5 (dense) | 25.856 | 25.248 | 1.0232 | 25.888 | 25.248 |
1.0236 |
| M 4096, K 1 (snapshot write, block 1) | 57.408 | 56.544 | 1.0145 |
57.408 | 56.288 | 1.0195 |

Cake ships no other data types or layouts for this operator, since the
dense and snapshot-write forms are the whole family, and 184 programs
(214 libraries: 96 sm_100a, 118 sm_103a) cover B200 (sm_100a, 148 SMs),
B300 (sm_103a, 148 SMs) and GB300 (sm_103a, 152 SMs).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized Kimi K3 attention-residual processing for supported
GPU configurations.
* Added support for selecting held-release kernel variants, including
routes that vary by programmatic-dependent launch mode.
* **Bug Fixes**
* Improved selection of compatible persistent-kernel variants for
supported configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4743
- **最后更新**: 2026-10-27T00:54:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34821
- **最后更新**: 2026-10-27T01:26:33Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: YiYi Xu, Wang, Yi, Gorka Dabó

## AI分析总结

## huggingface/diffusers 昨日提交分析（3 条）

### 1. 主要更新类型
- **文档/开发规范更新**：1 条
- **Bug 修复**：1 条（LoRA 相关）
- **测试增强**：1 条（CLI 命令多设备适配）

无大规模功能新增，整体属于日常维护迭代。

### 2. 关键变更点与项目方向的关系
- **Agent 编码规范调整**（#15129）：在贡献者指南中新增"优先使用命名参数而非嵌套字典"的规则，并将其移入编码风格章节，同时补充了 pipeline 层面的对应规范。这条提交体现了 diffusers 社区正在**应对 AI 编码助手（agent）参与贡献的趋势**——Claude 等工具生成的代码常使用嵌套 dict 传参，明确规范有助于保持代码库可读性一致性。
- **共享 LoRA 组件权重广播修复**（#15128）：修复了多个 pipeline 共享同一 LoRA 组件时，权重广播（broadcasting）逻辑出错的问题。LoRA 是 diffusers 生态中最核心的轻量微调方案，跨 pipeline 共享 LoRA 是用户常见用法（如 SDXL 多变体复用），此修复直接关系到**推理正确性**。
- **CLI 测试扩展至其他设备**（#15039）：将 `diffusers-cli run` 的 compile 参数和 attention backend 参数测试从原有设备扩展到 Intel XPU 等硬件，体现了项目对**多硬件后端（Intel GPU/加速器）持续支持**的承诺。

### 3. 对项目的影响和潜在意义
- LoRA 权重广播修复可避免用户在共享 LoRA 场景下得到错误的生成结果，属于高优先级的正确性修复，**提升核心功能可靠性**。
- 多设备测试扩展降低硬件适配的回归风险，为 Intel XPU 等新兴加速器提供持续保障，有利于扩大部署生态。
- Agent 编码规范的明确，预示着社区对 AI 生成代码的**质量治理机制**正在成型，对未来大规模 agent 辅助开发的代码一致性有长期价值。

### 4. 值得关注的技术点
- **LoRA 权重广播机制**：多 pipeline 共享单个 LoRA adapter 时的权重分发与设备/形状对齐逻辑，这类隐蔽 bug 通常只在特定组合下暴露，修复体现了维护者对细节场景的覆盖能力。
- **注意力后端多设备抽象**：测试覆盖 compile 参数与 attention backend（如 SDPA、xformers、Intel 扩展）的组合，说明 diffusers 的后端抽象层仍在持续完善。
- **命名参数编码规范**：对 API 设计风格的约束，长期看会让 diffusers 的 pipeline 调用接口更加显式、易读，降低误用概率。

### 5. 结合项目背景的整体评价
diffusers 作为 HuggingFace 的扩散模型推理/训练库，核心目标是**易用性、可扩展性与生态兼容**。这三条提交虽规模不大，但分别对应三大支柱：LoRA 修复保障核心推理功能的正确性，多设备测试巩固生态广度，agent 编码规范则面向未来的开发流程治理。这种"小步快跑"式的维护节奏，正是该开源项目保持高质量社区协作和快速跟进前沿研究（如新 LoRA 变体、新硬件后端）的关键所在。

## 详细提交记录

### [6dcb307](https://github.com/huggingface/diffusers/commit/6dcb307d1249daa30de102570aeba6eb40ea351a)

- **作者**: YiYi Xu
- **时间**: 2026-10-26T19:42:59Z
- **提交信息**: [agent docs] prefer named arguments over nested dicts (#15129)

* [agent docs] prefer named arguments over nested dicts

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

* [agent docs] move the named-arguments rule to coding style, add the pipeline counterpart

Co-Authored-By: Claude Opus 5 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [3b56af0](https://github.com/huggingface/diffusers/commit/3b56af0c5268049588cf470e38955f4c18002498)

- **作者**: Gorka Dabó
- **时间**: 2026-10-26T12:04:45Z
- **提交信息**: Fix shared LoRA component weight broadcasting (#15128)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [74a2fdd](https://github.com/huggingface/diffusers/commit/74a2fddea5060391cca123e36d55bccb887630f7)

- **作者**: Wang, Yi
- **时间**: 2026-10-26T08:55:32Z
- **提交信息**: extend tests/others/test_cli_commands.py::TestRunCommand::test_compil… (#15039)

* extend tests/others/test_cli_commands.py::TestRunCommand::test_compile_arg and
tests/others/test_cli_commands.py::TestRunCommand::test_attention_backend_arg to other device

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* update xpu expectation

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* update

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* revert the change in test_marigold

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

* make style

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>

---------

Signed-off-by: Wang, Yi A <yi.a.wang@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
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


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13309
- **最后更新**: 2026-10-26T21:53:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38220
- **最后更新**: 2026-10-27T01:23:44Z

## 提交统计

- **昨日提交总数**: 54
- **提交者数量**: 34
- **主要提交者**: pllimax, Mick, Jinwei

## AI分析总结

# sgl-project/sglang 昨日提交分析（共54条）

## 1. 主要更新类型分布
- **性能优化（Perf）**：约14条，占比最大
- **Bug修复（Fix）**：约17条
- **重构（Refactor）**：约6条
- **功能新增（Feat）**：约8条
- **CI/测试**：约7条
- **文档更新（Doc）**：约4条

## 2. 关键变更点与项目方向的关系
- **扩散模型（diffusion）模块大爆发**：约10+条提交集中在diffusion，包括CuTe-DSL norm kernel优化、VAE tile seam融合、Ulysses并行通信隐藏、请求清理与原子化输入发布等。这表明SGLang正从纯LLM推理向多模态/视觉生成推理大力扩展，符合README中"multimodal models"的定位。
- **硬件生态多元化**：AMD（gfx950/KDA、iter统一注意力）、NPU（昇腾）、Intel XPU、CPU（Grok-2在Xeon上启用）均有针对性修复和优化，体现项目对多后端异构硬件的战略布局。
- **推理性能持续深挖**：QSA长前缀prefill索引优化、DeepSeek-V4.1 MegaAttention默认条件细化、函数调用避免重复扫描GLM工具调用等，直击大模型推理吞吐与延迟痛点。

## 3. 对项目的影响和潜在意义
- **扩散模型服务成熟化**：从kernel级优化到请求生命周期管理（取消/拒绝请求清理、实时清理路由、测试独立性），说明diffusion serving正走向生产就绪。
- **rust-server补全**：聊天层模板/流式/错误处理对齐Python实现，以及通过sglang-processor渲染聊天，表明项目在推进Rust高性能服务层，提升部署一致性。
- **推理-预填充分离架构演进**：多个"caller-allocated buffer"重构（attention LSE、bcg输出、qwen4 QSA、dsv41 engram等）暗示正在系统性地将内存管理权交给调用方，减少拷贝、为 disaggregation/TBO 铺路。
- **KV缓存生态扩展**：hicache暴露Mooncake L3对象键布局给外部KV路由器、空辅助传输跳过，强化了分层KV缓存生态集成能力。

## 4. 值得关注的技术点
- **AI辅助开发痕迹明显**：多条提交由 Claude Opus 5.5、Cursor 协作完成，反映AI编程已深度融入该项目开发流程。
- **投机解码（speculative decoding）新思路**：在无draft模型情况下于target端捕获辅助隐藏状态（#43449），可能简化投机解码流程。
- **sgl-router冷提示优化**：confirmed-first pending prefixes + follower cap（#46505），解决路由层冷启动前缀匹配的效率问题。
- **DeepSeek-V4.1非EP TBO修复**（attention TP > 1），对大规模部署的正确性至关重要。
- **Beam模型kernel支持**（#45254），大幅扩展多路输出场景的适用范围。

## 5. 对项目发展的整体影响
结合README定位（"LLM和多模态模型的快速推理"），这批提交呈现三条清晰主线：**（一）** 多模态/扩散模型推理能力从实验走向成熟，成为第二增长曲线；**（二）** 硬件后端从NVIDIA单极向AMD/Intel/NPU/CPU全栈覆盖，扩大生态护城河；**（三）** 通过内存所有权重构、rust-server对齐和分层KV缓存集成，夯实高吞吐低延迟的核心竞争力。整体上，项目正从"LLM推理加速库"演进为"覆盖全硬件、全模态的统一高性能推理平台"，这些变更将显著提升其在生产环境中的可靠性与部署广度。

## 详细提交记录

### [e732f5d](https://github.com/sgl-project/sglang/commit/e732f5d41e9d279c1be7e5818ce9fd8bd425c0b2)

- **作者**: maocheng23
- **时间**: 2026-10-26T23:18:44Z
- **提交信息**: [Feat] spec: Capture aux hidden states on the target without a speculative draft (#43449)

### [eb8c2a4](https://github.com/sgl-project/sglang/commit/eb8c2a40ef492b68397544b11691fb9b8b555124)

- **作者**: Bryan Shan
- **时间**: 2026-10-26T23:09:58Z
- **提交信息**: [Fix] [AMD] MiniMax-M3: default SGLANG_MINIMAX_M3_INDEX_TOPK_FREQ to 1 (#46340)

Co-authored-by: functionstackx <47992694+functionstackx@users.noreply.github.com>

### [01759f0](https://github.com/sgl-project/sglang/commit/01759f0a686c13599746466cdb1539b935c1f3f0)

- **作者**: karverma-amd
- **时间**: 2026-10-26T22:39:42Z
- **提交信息**: [Perf] [AMD] dsv4: fp8 target lm_head GEMM for DSPARK verify logits (#39622)

gfx95 specific

### [d41fbdc](https://github.com/sgl-project/sglang/commit/d41fbdc64793460455d7c8e9e66921f4feb6e9f7)

- **作者**: Kan Wu
- **时间**: 2026-10-26T21:57:18Z
- **提交信息**: [Doc] sgl-router: Add GLM-5.3-Flash and DeepSeek-V4.1-Flash deployment examples (#46668)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [642e9c1](https://github.com/sgl-project/sglang/commit/642e9c1448ccb1f95c3d0fd1153e4f3b8cb478f1)

- **作者**: Shunkangz
- **时间**: 2026-10-26T21:51:50Z
- **提交信息**: [Perf] QSA: Optimize prefill indexer in long cached prefixes (#45791)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4fb422b](https://github.com/sgl-project/sglang/commit/4fb422b9feed898a681da7cc40ef035aec2d92b2)

- **作者**: Kan Wu
- **时间**: 2026-10-26T21:48:27Z
- **提交信息**: [Fix] rust-server: Match Python's chat layer on templates, streaming and lowered-chat errors (#45659)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [d4939cc](https://github.com/sgl-project/sglang/commit/d4939cc267a5a2ee6bdabaed4e183d6c2c4f654d)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-26T20:44:29Z
- **提交信息**: [Refactor] bcg: Write the debug-mode forward's output buffer inside its eager break (#46553)

### [5aeb6df](https://github.com/sgl-project/sglang/commit/5aeb6dfdb64895c7ef17fd385aba3a6ef28ed92a)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-26T20:40:23Z
- **提交信息**: [Refactor] nemotron_h: Read the prefill shared expert's output from the caller's holder (#46551)

### [2c25056](https://github.com/sgl-project/sglang/commit/2c250563ae03c546ab1121ecf27196c8ed69ae24)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-26T20:39:47Z
- **提交信息**: [Refactor] attention: Write the eager break's LSE into a caller-allocated buffer (#46535)

### [5e420a1](https://github.com/sgl-project/sglang/commit/5e420a1258679719f88bee2b2cd5d19cde2da8dc)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-26T20:34:28Z
- **提交信息**: [Refactor] qwen4: Write QSA top-k and PLE batch breaks into caller-held outputs (#46543)

### [5a1f174](https://github.com/sgl-project/sglang/commit/5a1f174700972605a4fa955e80eba1b36b1b12fd)

- **作者**: Rayan Hatout
- **时间**: 2026-10-26T20:32:29Z
- **提交信息**: [Fix] utils: Fix CPU engine detection under torch.compile fullgraph (#46640)

### [66f79f1](https://github.com/sgl-project/sglang/commit/66f79f1a9070ea7ae8f8e5d9b3381340ea0ec83e)

- **作者**: Jimmy Shong
- **时间**: 2026-10-26T19:28:56Z
- **提交信息**: [Feat] kernels: Beam model support (#45254)

Signed-off-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Florent Gbelidji <florentgbelidji@Florents-MacBook-Pro.local>
Co-authored-by: iaroslav-reflection <iaroslav@reflection.ai>
Co-authored-by: Jinze Xue <jinzex@nvidia.com>
Co-authored-by: mloh <mloh@nvidia.com>
Co-authored-by: neilkg <33635204+neilkg@users.noreply.github.com>
Co-authored-by: thibautbar <t.barroyer@icloud.com>
Co-authored-by: Florent Gbelidji <florent@reflection.ai>
Co-authored-by: Florent Gbelidji <florentgbelidji@florents-macbook-pro1.home>
Co-authored-by: Florent Gbelidji <florentgbelidji@Host-002.lan>
Co-authored-by: Jiajun Li <jiajun.li@radixark.ai>
Co-authored-by: Kaiwu <kai@reflection.ai>
Co-authored-by: Neil Gollapudi <neil@reflection.ai>
Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>
Co-authored-by: Renault Young <renault@reflection.ai>
Co-authored-by: Yoni Gozlan <yoni@reflection.ai>
Co-authored-by: zhihengy <andy.ye@radixark.ai>
Co-authored-by: AymenKallala <aymen.kallala@gmail.com>
Co-authored-by: Florent Gbelidji <florentgbelidji@Mac.lan>
Co-authored-by: Jinze Xue <155670984+jinzex@users.noreply.github.com>
Co-authored-by: mreso <13337103+mreso@users.noreply.github.com>
Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>
Co-authored-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Yoni Gozlan <74535834+yonigozlan@users.noreply.github.com>

### [7ec4c0d](https://github.com/sgl-project/sglang/commit/7ec4c0d790ef80e6e53c059cb27bb824317c18b6)

- **作者**: Michael
- **时间**: 2026-10-26T19:23:47Z
- **提交信息**: [CI] [AMD] diffusion: Skip the CUDA-only gpu-idle and Z-Image RoPE cache unit tests on ROCm (#46449)

### [11550a5](https://github.com/sgl-project/sglang/commit/11550a58459bfe092db6283fe40654c14009c0ad)

- **作者**: Michael
- **时间**: 2026-10-26T19:16:04Z
- **提交信息**: [CI] [AMD] diffusion: Skip the Wan CuTe DSL q/k norm RoPE imports on ROCm (#46396)

### [911693e](https://github.com/sgl-project/sglang/commit/911693e3f816b32c40ee1cd8a98f390da3a18297)

- **作者**: Kan Wu
- **时间**: 2026-10-26T17:20:15Z
- **提交信息**: [Feat] rust-server: Render, tokenize and serve chat through sglang-processor (#45449)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [3a62cdf](https://github.com/sgl-project/sglang/commit/3a62cdfb3d0bc70f4eb980c7ded1d80545cea6c1)

- **作者**: Peng Wu
- **时间**: 2026-10-26T16:50:56Z
- **提交信息**: [Fix] scheduler: Make a Req's "__req__" self-reference weak (#45923)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1596e88](https://github.com/sgl-project/sglang/commit/1596e88edaf5c62b69323cb3df8a7d1a460dc472)

- **作者**: Aurick Qiao
- **时间**: 2026-10-26T16:38:02Z
- **提交信息**: [Fix] hicache: Skip empty auxiliary transfers (#45673)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>

### [ae579c5](https://github.com/sgl-project/sglang/commit/ae579c5e00300e77f446b5f33996121c15a9c78d)

- **作者**: Michael Feil
- **时间**: 2026-10-26T15:53:29Z
- **提交信息**: [Fix] multimodal: Preserve caller hashes and offsets for precomputed inputs (#44160)

### [9f6678a](https://github.com/sgl-project/sglang/commit/9f6678aa3d6b8fd4e898fe0fc0b11b932126cf61)

- **作者**: Mick
- **时间**: 2026-10-26T14:43:47Z
- **提交信息**: [Fix] ci: Add executable entry point to Muse Spark router test (#45830)

### [fe4ccb3](https://github.com/sgl-project/sglang/commit/fe4ccb37e4397e50f371a972334650590571853a)

- **作者**: Mick
- **时间**: 2026-10-26T14:40:31Z
- **提交信息**: [Fix] diffusion/api: Publish image inputs atomically (#46060)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [d3e84c3](https://github.com/sgl-project/sglang/commit/d3e84c32e554c474a041235b2554d825fc47c67f)

- **作者**: Mick
- **时间**: 2026-10-26T14:40:07Z
- **提交信息**: [Fix] diffusion/disaggregation: Preserve GLM pixels for the head (#46193)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [ce77d5e](https://github.com/sgl-project/sglang/commit/ce77d5e93de6722cfe033fbe64b43cf49ea6a6a1)

- **作者**: Mick
- **时间**: 2026-10-26T14:39:42Z
- **提交信息**: [Fix] diffusion/server: Clean up rejected and cancelled video requests (#46057)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [095750b](https://github.com/sgl-project/sglang/commit/095750baf9fcd44381c07a6da5e7feffbe008b8e)

- **作者**: Mick
- **时间**: 2026-10-26T14:38:19Z
- **提交信息**: [Perf] diffusion: Walk several row chunks per warp in the CuTe-DSL norm kernels (#46227)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [042dc54](https://github.com/sgl-project/sglang/commit/042dc54cbf961c39455b5f30af6c0e259a6e84fb)

- **作者**: Mick
- **时间**: 2026-10-26T14:35:29Z
- **提交信息**: [Fix] diffusion: Route realtime cleanup to the session owner (#46249)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [bd03d33](https://github.com/sgl-project/sglang/commit/bd03d33f6b4480d3c66a79fb383d4592d7f8fb7d)

- **作者**: Mick
- **时间**: 2026-10-26T14:34:59Z
- **提交信息**: [Test] diffusion: Make restoration tests independent of execution order (#46254)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [9841183](https://github.com/sgl-project/sglang/commit/9841183827e1da52668ca337aaf4113a7398a136)

- **作者**: Mick
- **时间**: 2026-10-26T14:34:28Z
- **提交信息**: [Perf] diffusion: Hide the pipelined Ulysses own-row copies behind the exchange (#46308)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [316ff4d](https://github.com/sgl-project/sglang/commit/316ff4dce2f09ba04b09d5a910061ee89243a6d1)

- **作者**: Chen
- **时间**: 2026-10-26T12:54:03Z
- **提交信息**: [Perf] function_call: stop rescanning unclosed GLM tool calls per chunk (#45143)

### [af21e2b](https://github.com/sgl-project/sglang/commit/af21e2b989e482cfdce39689126562f2209d53ac)

- **作者**: ashwini rathi
- **时间**: 2026-10-26T12:08:24Z
- **提交信息**: [Fix] [Intel] diffusion/wan: Guard the CuTe DSL q/k norm RoPE imports on XPU (#46393)

### [ef11eb3](https://github.com/sgl-project/sglang/commit/ef11eb3b76354ffbabd9f17a2343e79522e41cf2)

- **作者**: Michael Gschwind
- **时间**: 2026-10-26T11:34:02Z
- **提交信息**: [Fix] deepseek-v4: Fix DeepSeek-V4 non-EP TBO for attention TP > 1 (#33250)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>

### [fb40bdc](https://github.com/sgl-project/sglang/commit/fb40bdcff3b5a0975b87f99d339c39dbd105f64e)

- **作者**: sglang-bot
- **时间**: 2026-10-26T11:24:15Z
- **提交信息**: [Chore] ci: Update test est_time values (#46481)

### [c4e335f](https://github.com/sgl-project/sglang/commit/c4e335f84e342999c1c20ae4ad1e5ec44d74692d)

- **作者**: Mick
- **时间**: 2026-10-26T11:10:14Z
- **提交信息**: [Perf] diffusion: Build spatial-parallel causal conv inputs in one pass (#46174)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick <mickqian@radixark.ai>

### [d72664d](https://github.com/sgl-project/sglang/commit/d72664d903cbd4cd1d238d092961d3dd55dea027)

- **作者**: Mick
- **时间**: 2026-10-26T10:49:51Z
- **提交信息**: [Perf] diffusion: Blend VAE tile seams in one pass (#46240)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c25c24d](https://github.com/sgl-project/sglang/commit/c25c24d78322a623293ae3c097270b1316af0bcc)

- **作者**: pllimax
- **时间**: 2026-10-26T10:31:59Z
- **提交信息**: [CI] [NPU] registry: Downsize nightly test registrations to the cards each test actually uses (#46561)

### [5ef9901](https://github.com/sgl-project/sglang/commit/5ef99013ac3e3e7d180c39d1fb4a882cd00cf6fb)

- **作者**: weireweire
- **时间**: 2026-10-26T09:48:40Z
- **提交信息**: [Fix] grammar: Give grammar accept failures an error status (#46049)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [c23f1cc](https://github.com/sgl-project/sglang/commit/c23f1ccce1ccdfb476a6df3689e8941a149d4c29)

- **作者**: Cheng Wan
- **时间**: 2026-10-26T09:43:42Z
- **提交信息**: [Test] hicache: Accept session_ids in the L3 object-layout test's put stubs (#46570)

### [d19f19d](https://github.com/sgl-project/sglang/commit/d19f19d68cbd959619c19ce1cd3192bd38b67888)

- **作者**: Michael
- **时间**: 2026-10-26T09:08:49Z
- **提交信息**: [CI] [AMD] pr-test: list tags with ls-remote, 8 small shards (#46453)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>

### [ccfb2b3](https://github.com/sgl-project/sglang/commit/ccfb2b32078a50441781ccb63060a92289fb4210)

- **作者**: shun8686
- **时间**: 2026-10-26T09:02:57Z
- **提交信息**: [CI] [NPU] workflow: Fix indentation of branches filter in pr-test-npu.yml (#46558)

Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [9f594d5](https://github.com/sgl-project/sglang/commit/9f594d586b8029da4a5533e89b187fe9650e39c3)

- **作者**: Jeongho Shin
- **时间**: 2026-10-26T09:02:10Z
- **提交信息**: [Fix] hicache: Delegate on_host_pools_registered in the failure injector (#46501)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [d96c386](https://github.com/sgl-project/sglang/commit/d96c38633540842602acf768f9cdd599f75e7878)

- **作者**: Siliang Chen
- **时间**: 2026-10-26T08:44:32Z
- **提交信息**: [Fix] [AMD] attention: Pass the layer softcap to aiter unified-attention decode (#45531)

Signed-off-by: siliangchen-amd <SiLiang.Chen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [a9bf8c7](https://github.com/sgl-project/sglang/commit/a9bf8c76a0115f5e2672bfdfc61d70a2b7936744)

- **作者**: Ke Bao
- **时间**: 2026-10-26T08:42:30Z
- **提交信息**: [Feat] minimax: Support MiniMax-M3.1-Flash (#45925)

Co-authored-by: Denji-kk <51020465+Denji-kk@users.noreply.github.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: zhongyu <zhongyu@minimaxi.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: maocheng23 <35615230+maocheng23@users.noreply.github.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Qi Wang <wqstu1@gmail.com>
Co-authored-by: Yan Huang <yan.huang@radixark.ai>
Co-authored-by: Thanhhao <31717833+thanhhao98@users.noreply.github.com>
Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [6a28c96](https://github.com/sgl-project/sglang/commit/6a28c96a493318b09dd1ff6f42ae04c056b291aa)

- **作者**: Jinwei
- **时间**: 2026-10-26T08:40:27Z
- **提交信息**: [Perf] [AMD] kda: Use a HIP fused decode kernel by default for KDA (Kimi-K3) on gfx950 (#45713)

Co-authored-by: Yao <jiyao@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [c8398cb](https://github.com/sgl-project/sglang/commit/c8398cb3a3994bd145ba8e6270dd8809a60855dc)

- **作者**: Jinwei
- **时间**: 2026-10-26T08:39:54Z
- **提交信息**: [Perf] [AMD] kda: Use a HIP chunked-prefill kernel for KDA on gfx950 (#45710)

Co-authored-by: Yao <jiyao@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [d42e1ee](https://github.com/sgl-project/sglang/commit/d42e1ee7e10a8aab3942f6d820dea47e08889e85)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-26T08:36:15Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches with MiniMax-M3.1-Flash B200 / GB200 HiCache points (#46547)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e1c4b27](https://github.com/sgl-project/sglang/commit/e1c4b273afd94f1a7c4ff7e311b328f441ad9a6b)

- **作者**: zijiexia
- **时间**: 2026-10-26T08:20:43Z
- **提交信息**: [Doc] cookbook: MiniMax-M3.1 GB200 recipes and B200 Low-Latency (MonoKernel) (#46546)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [144bcdf](https://github.com/sgl-project/sglang/commit/144bcdfe3470e3378b00d602bb928b8ff4605828)

- **作者**: Xinguo Zhu
- **时间**: 2026-10-26T08:19:23Z
- **提交信息**: [Feat] [CPU] Grok-model: enable grok-2 model on xeon cpu (#43341)

Co-authored-by: Akatydid <xinguojoe@gmail.com>
Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [64fc5f0](https://github.com/sgl-project/sglang/commit/64fc5f0bdbee035d3341a809a81c41a9f7208eb4)

- **作者**: Jundong Liu
- **时间**: 2026-10-26T08:04:11Z
- **提交信息**: [Feat] hicache: Expose the Mooncake L3 object-key layout for external KV routers (#40467)

Signed-off-by: littledgg <1658565283@qq.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [d1bbcbd](https://github.com/sgl-project/sglang/commit/d1bbcbdc0db5d18585666a696b76fd672478f810)

- **作者**: Youduo Liu
- **时间**: 2026-10-26T08:02:48Z
- **提交信息**: [Doc] [NPU] cookbook: add A3 deployment scenarios to GLM-5.2 (#45642)

### [2b84393](https://github.com/sgl-project/sglang/commit/2b843931240233925c8507faaba6f806964ae556)

- **作者**: Sage
- **时间**: 2026-10-26T07:56:34Z
- **提交信息**: [Chore] sgl-router: use `api.v1` typed generate response (#46432)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [52a6f70](https://github.com/sgl-project/sglang/commit/52a6f7049f99ce471be4d77a633bcf464becc095)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-26T07:27:43Z
- **提交信息**: [Refactor] dsv41: Write engram hash ids and embeddings into caller-allocated prefill graph outputs (#46530)

### [60d9412](https://github.com/sgl-project/sglang/commit/60d941293e3af27a12c6eb64e2c3e2e1a17f100f)

- **作者**: Mick
- **时间**: 2026-10-26T07:18:44Z
- **提交信息**: [Perf] diffusion/worker: Move cyclic GC out of request execution (#46493)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [f3a86ef](https://github.com/sgl-project/sglang/commit/f3a86ef2bc2fbfbfa0e1c9f2b38b07c9e1fbb349)

- **作者**: Yuwei An
- **时间**: 2026-10-26T07:17:56Z
- **提交信息**: [CI] deepep: Add release workflow for sgl-deep-ep-v25 (DeepEP 2.5) (#46533)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [eabb11a](https://github.com/sgl-project/sglang/commit/eabb11a4c15ae90531deb33bf23616d59c032589)

- **作者**: Shangming Cai
- **时间**: 2026-10-26T07:15:30Z
- **提交信息**: [Feat] sgl-router: Confirmed-first pending prefixes for cold prompts, with a follower cap (#46505)

### [655c2cd](https://github.com/sgl-project/sglang/commit/655c2cdd6411467f05649bef0324f21ff7dec16b)

- **作者**: weireweire
- **时间**: 2026-10-26T07:14:16Z
- **提交信息**: [Perf] [NVIDIA] deepseek-v4.1: Default aggregated servers to MegaAttention only when each rank holds 64 query heads (#46263)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3b058f2](https://github.com/sgl-project/sglang/commit/3b058f28c28d9f9d8015d10b24dcaa344de87295)

- **作者**: vstone-w
- **时间**: 2026-10-26T07:09:38Z
- **提交信息**: [Refactor] [NPU] communicator: remove redundant npu communicator (#45950)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1296
- **最后更新**: 2026-10-26T17:57:19Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Zeyu Yang, DefTruth

## AI分析总结

# 提交分析总结

**仓库背景**：cache-dit 是面向 DiT（Diffusion Transformer）的 PyTorch 原生推理引擎，核心能力包括缓存（Cache）、并行（CP/TP）、量化与 CPU Offload。

## 1. 主要更新类型
- **功能新增**：Motif-Video（T2V/I2V）模型的全面支持，是本批提交的主体。
- **文档更新**：统一 "Huawei Ascend NPU" 品牌命名；补充性能分析参考资料。

## 2. 关键变更点及与项目方向的关系
- 新增 **MotifVideoPatchFunctor**，将单流 encoder/decoder 块循环拆分并与上游 forward 逐位对齐（bit-exact），保证缓存接管时结果不变——直接服务于引擎"缓存加速且不损质量"的核心目标。
- **并行规划器（CP/TP planner）**：CP 采用 transformer_blocks.0 单点切分 + RoPE 输出切分 + proj_out gather；TP v1 仅覆盖双流块，规避头切分形状冲突。这扩展了引擎的并行适配矩阵，覆盖新架构。
- **TE-P 并行**：T5Gemma2Encoder 的张量并行白名单支持，扩展文本编码器并行能力。
- **量化/Offload 验证**：fp8、svdq-nvfp4、layerwise offload 均在新模型上跑通，与 README 宣称的量化和 CPU Offload 能力对齐。

## 3. 对项目的影响和潜在意义
- Motif-Video-2B 实测 **cache 1.81x @ PSNR 41.4**，CP2 1.80x、TP2 1.15x，且 layerwise offload 达 SSIM 1.000——证明引擎的加速手段可无损迁移到新模型，增强了"通用 DiT 推理引擎"的定位与生态覆盖。
- 文档命名统一提升品牌一致性，对 PyPI/ReadTheDocs 首页展示有正向影响。

## 4. 值得关注的技术点
- **Ulysses 非对称注意力**处理 cross-attention，并显式拒绝 "ulysses-anything"（依赖等分 mask 假设），体现对并行正确性的严格把关。
- **processor patch 分 armed/unarmed 两态**及对应 mask 数学测试，设计上防呆。
- **TP v1 的形状约束**（单流 pre_only attn 输出为 head-sharded、Rowwise cross 为全宽）说明混合块内并行的复杂度，是后续 TP v2 的关键待解问题。
- 7 个 CPU 回归测试覆盖位精确性、块调用计数、计划解析等，回归体系完善。

## 5. 对项目发展的意义
这两个提交分别强化了 cache-dit 的两条主线：**横向扩展模型覆盖**（Motif-Video 作为新架构，验证了缓存、并行、量化、offload 全套手段的通用性，方法论上可复用到后续模型接入）与**文档/品牌打磨**（Ascend 命名统一，呼应国产 NPU 支持的战略方向）。整体上，项目正从"支持若干模型"向"可扩展的多架构推理平台"演进，而本次提交同时贡献了工程模板（functor/planner/测试三位一体的接入模式）和生态可见性。

## 详细提交记录

### [6ece378](https://github.com/vipshop/cache-dit/commit/6ece37835c703d91d2c507c3afcdd1c9656789a2)

- **作者**: Zeyu Yang
- **时间**: 2026-10-26T12:16:11Z
- **提交信息**: docs: rename "Ascend NPU" to "Huawei Ascend NPU" for consistent branding (#1144)

Make the Huawei Ascend naming consistent across the docs site and READMEs:
- mkdocs nav labels (Documentation / Supported Matrix / Benchmark)
- H1 titles of the three ASCEND_NPU docs pages
- OVERVIEWS body sentence and TOC link
- Root README (PyPI long_description source) and docs/README (RTD Home)

The in-image text in assets/arch_v2.png is unchanged (no drawio/svg source in repo).

Co-authored-by: WorkBuddy <workbuddy@tencent.com>

### [b8f8a5d](https://github.com/vipshop/cache-dit/commit/b8f8a5d2de8a1409265a9e23a5a6be45bb512757)

- **作者**: DefTruth
- **时间**: 2026-10-26T08:39:39Z
- **提交信息**: Add Motif-Video (T2V/I2V) support (#1142)

* Add Motif-Video (T2V/I2V) support

- MotifVideoPatchFunctor: split the sliced single-stream loops into
  _motif_single_encoder_blocks / _motif_single_decoder_blocks and mirror the
  upstream forward (bit-exact); permute the attention mask into all-to-all
  order and chunk the DDT decoder query stream under context parallelism
- motif_video_adapter: three block lists (dual / single-encoder /
  single-decoder), Pattern_0 x3, has_separate_cfg derived from
  guider.num_conditions (AdaptiveProjectedGuidance, two sequential passes)
- MotifVideo CP planner: single-point split at transformer_blocks.0 +
  rope output-split + proj_out gather; class-level processor patches with
  unarmed fallback; cross-attention rides Ulysses as asymmetric attention;
  ulysses-anything rejected (even-split mask assumption)
- MotifVideo TP planner (v1): dual-stream blocks only (single-stream
  pre_only attn output is head-sharded while the Rowwise cross output is
  full width - mixing them inside the block would break shapes)
- TE-P: T5Gemma2Encoder support in GemmaTensorParallelismPlanner
  (text_model nesting + T5Gemma2EncoderLayer whitelist, vision tower
  untouched)
- CLI: motif_video_t2v / motif_video_i2v examples + MOTIF_VIDEO_DIR
- tests: 7 CPU regressions (functor bit-exact, cache takeover block-call
  counting, CP plan resolution, processor patch unarmed/armed mask math,
  UAA guard)

Verified on Motif-Video-2B (480x832x81f x30 steps, RTX PRO 5000):
cache 1.81x @ PSNR 41.4 / SSIM 0.971; CP2 1.80x @ 42.3; TP2 1.15x @ 42.8;
TP2+TEP+VAEP @ 42.3; CP2+compile @ 42.4; fp8+compile @ 35.5;
svdq-nvfp4-r64+compile @ 32.2; layerwise offload bit-exact (SSIM 1.000)

* docs: update readme

* docs: update readme

* docs: update readme

* docs: update readme

* docs: update readme

* docs(skill): add FLOPs-budget perf analysis reference (attn vs gemm share, ffpa case)

* docs(skill): add perf_analysis entries (routing row + attention-dominated pitfall)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95633
- **最后更新**: 2026-10-27T01:35:52Z

## 提交统计

- **昨日提交总数**: 82
- **提交者数量**: 70
- **主要提交者**: Tony Lin, BaoYunkai, CharlesWu

## AI分析总结

# vLLM 昨日提交总结（共 82 条）

## 一、主要更新类型

本日提交以 **Bug 修复（约 40%）** 和 **性能优化（约 1/3）** 为主，辅以功能新增与 CI/文档完善。功能新增集中在新模型支持（Gemma 4、Lfm2Bidirectional、DeepSeek-V4.1 PCP+DSpark）、RL ParamMeta 元数据等；文档涵盖 Kimi-K3 部署、Muse Spark、Kolibri 1 推理解析等内容。

## 二、关键变更点

**1. KV Offload 存储体系密集修复（十余条，本日最突出主题）**
涵盖前缀保留、P2P 非阻塞发送、NIXL 注册回滚、LRU 批次、滑动窗口空块、同步加载策略、发送队列溢出防止重放截断、ConnectAck 失败标记会话死亡等。该模块正从快速迭代进入生产化打磨阶段，团队集中攻克分布式卸载的边界问题。

**2. 投机解码持续活跃迭代**
Draft logits 分片、Triton 内核替代 torch.compile、DFlash dtype 修复、DSpark PCP 支持等，表明投机解码正逐步走向成熟。

**3. DeepSeek-V4/V4.1 深度适配**
ROCm 上 MXFP4 索引器 K 缓存默认化、FP8 共享专家 FSE 兼容性修复、MI355X AgentX 调度配置文档更新，体现 vLLM 对 AMD 硬件上最新大模型的持续加码。

**4. 多硬件生态并进**
- **NVIDIA**：DeepGEMM、H100/H200 调优配置。
- **AMD/ROCm**：AITER、MI300 相关推进。
- **Intel XPU**：FP8 动态量化、MoE tile 调整、融合 RMSNorm 量化测试、PEFT/LoRA 依赖支持、MLA 缓存算子参数修复，功能完整性与测试覆盖持续补齐。

**5. 核心性能优化**
MXFP4 激活量化 3x 内核加速、MRV2 缓冲区优化、MoE 对称缓冲尺寸修正；Kimi-K3 的 KV-balanced FP8 MLA decode 与 FlashInfer 融合内核路由也带来直接收益。

**6. 稳定性加固**
Radix barrier 同步、SSL watcher 清理、ZMQ 非阻塞等大量竞态与资源泄漏修复，显著降低长时间服务的故障率。

**7. 可扩展性改进**
允许注册 OOT block-scaled FP8 线性内核，批量不变性 matmul 表扩充，降低社区贡献定制内核门槛。

**8. Rust 前端功能完善**
请求体大小可配置、P/D 预填充缓存命中统计、thinker_config 适配，预示 Rust 引擎逐步走向生产。

## 三、值得关注的技术点

- **MXFP4 成为 DeepSeek-V4 默认索引器缓存格式**：4-bit 量化在索引器场景中走向成熟默认路径。
- **KV Offload 同步加载优化**：小的 CPU 层命中改为步骤内同步加载，可降低小缓存命中的延迟开销。
- **精度与性能平衡**：WNA16 MoE 在批量不变性下的 dispatch 保留、persistent TopK 候选溢出精确化，体现对数值正确性的严格要求。
- **AI 辅助开发常态化**：近半数提交带有 Claude/Codex 等 AI 工具联合署名，vLLM 已成为 AI 协作开发的标杆实践。

## 四、对项目发展的影响

结合 vLLM"让所有人都能快速低成本地服务 LLM"的定位，本日提交从三个维度推进了项目：

1. **稳定性与可靠性**：KV Offload 密集修复和大量竞态消除，为分布式大规模部署夯实基础设施，是迈向生产级可靠性的关键一步。
2. **生态位强化**：DeepSeek-V4、Kimi-K3 等前沿模型与 ROCm/XPU 硬件的并行适配，巩固其"多硬件多模型统一推理引擎"的地位。
3. **质量保障**：测试覆盖与 CI 增强为快速迭代提供支撑。

总体而言，vLLM 正处于"广度扩平台、深度抠性能、厚度补稳定性"的成熟迭代期：从功能扩张稳步过渡到生产加固，同时为下一代模型和硬件做好前瞻布局。

## 详细提交记录

### [26cbb47](https://github.com/vllm-project/vllm/commit/26cbb47d48e6b1de8ab2b4bc1c839821ffcfd56b)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-26T23:59:04Z
- **提交信息**: [Spec Decode][Sampling] Batch-sharded draft logits (#63554)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b82393b](https://github.com/vllm-project/vllm/commit/b82393b77315692f390880d2e931fdc1fbd13928)

- **作者**: Ankur Singh
- **时间**: 2026-10-26T23:34:50Z
- **提交信息**: [Doc] Kimi-K3: refresh the GB300 AgentX xPyD preset and add the 3P1D DEP16 preset (#63852)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>

### [6597cea](https://github.com/vllm-project/vllm/commit/6597ceafbc50d4a7fde9d8ef2d207989732758f7)

- **作者**: Wei Zhao
- **时间**: 2026-10-26T23:32:38Z
- **提交信息**: [Perf][Kimi K3] Opt-in KV-balanced FP8 MLA decode for agentic workloads (#63638)

Signed-off-by: Wei Zhao <weizha@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [967c39f](https://github.com/vllm-project/vllm/commit/967c39f89e31d1c99a9cee752a7305c2497f50b0)

- **作者**: Oxana Korzh
- **时间**: 2026-10-26T23:15:29Z
- **提交信息**: [CI] List one test path per line in Buildkite pytest commands to avoid merge conflicts (#63408)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7a1ebe4](https://github.com/vllm-project/vllm/commit/7a1ebe4ef5887989bb167e247304360ba0150cf6)

- **作者**: Jie Hao
- **时间**: 2026-10-26T22:41:40Z
- **提交信息**: [NIXL] Bump NIXL version to 1.5.1 (#63817)

Signed-off-by: Jie Hao <jihao@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [938be2d](https://github.com/vllm-project/vllm/commit/938be2d83d1815433ee0e825d2f01349a0fc6a89)

- **作者**: Artem Perevedentsev
- **时间**: 2026-10-26T22:30:20Z
- **提交信息**: [Tool Calling] Migrate llama3_json parser to parser engine (#63569)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [70d67f1](https://github.com/vllm-project/vllm/commit/70d67f19dcf822b97b5f8863b7590edd73a59b23)

- **作者**: djramic
- **时间**: 2026-10-26T22:24:42Z
- **提交信息**: [ROCm][CI] Release checkpoint page cache between language generation … (#63828)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [25ba0af](https://github.com/vllm-project/vllm/commit/25ba0af777533ea930ae3403f67eb9846e8aa5de)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-26T22:15:34Z
- **提交信息**: [CI][Frontend] Let the SSL refresher test's fake server accept peer_loads (#63840)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2feedbe](https://github.com/vllm-project/vllm/commit/2feedbe8dc5c71ac3f6933bd4486d83efa154dfb)

- **作者**: mispa-ms
- **时间**: 2026-10-26T22:14:55Z
- **提交信息**: [Perf][MoE] Size the DeepGEMM MegaMoE symmetric buffer for one sequence-parallel shard (#63541)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [537a79f](https://github.com/vllm-project/vllm/commit/537a79f0fc5ba564d2bef43d54915b2f80f9f77d)

- **作者**: Oxana Korzh
- **时间**: 2026-10-26T21:57:18Z
- **提交信息**: [CI] Add missing `&&` in the Multi-Modal Models (Standard) 3 command (#63422)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4eb5df8](https://github.com/vllm-project/vllm/commit/4eb5df80389a4dc16e468b11cfd2ed70dc731f85)

- **作者**: Brandon Zhang
- **时间**: 2026-10-26T21:49:47Z
- **提交信息**: [Kimi-K3] Route the fp8 chunked-context K/V pack through FlashInfer where it has a fused kernel (#61527)

Signed-off-by: Brandon Zhang <31413216+brandonfzhang@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Co-authored-by: Wei Zhao <weizha@nvidia.com>

### [41f5146](https://github.com/vllm-project/vllm/commit/41f5146b5b3a5b3c89ceee6f804e5e535a72ccbb)

- **作者**: Misha Goin
- **时间**: 2026-10-26T21:25:23Z
- **提交信息**: [Spec Decode] Replace torch.compile'd AV draft-budget selection with a Triton kernel (#63421)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1fd6337](https://github.com/vllm-project/vllm/commit/1fd6337e22243f40bf4b1cd307c68faf150aaf7d)

- **作者**: yifanFengg
- **时间**: 2026-10-26T21:12:10Z
- **提交信息**: [Bugfix] Keep legacy WNA16 MoE dispatch on Triton under batch invariance (#61038)

Signed-off-by: Yifan Feng <evanfengff@gmail.com>
Signed-off-by: yifanFengg <yifanfen@amazon.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [eb703fb](https://github.com/vllm-project/vllm/commit/eb703fbb3db3c2ea24656d1f737abf6a5a42f6d7)

- **作者**: rasmith
- **时间**: 2026-10-26T21:10:53Z
- **提交信息**: [BugFix] [Build] Fix for where setup.py fails with MAX_JOBS invalid literal error (#45188)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [3f45273](https://github.com/vllm-project/vllm/commit/3f45273050ac38b705eeac9c1e4d5e5f0330034c)

- **作者**: Zhiqi Zhang
- **时间**: 2026-10-26T21:03:03Z
- **提交信息**: [Bugfix][Tool Parser] Anchor Jamba streamed tool arguments to what was sent (#55669)

Signed-off-by: Zhiqi Zhang <zhiqizhangg@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [2841f08](https://github.com/vllm-project/vllm/commit/2841f08b4a93f12a28428425061c368e912fa4b8)

- **作者**: Yuhan Zhou
- **时间**: 2026-10-26T21:02:18Z
- **提交信息**: [KVConnector][Mooncake] Coalesce descending block ids to reduce descriptor number for Mooncake TE (#63142)

Signed-off-by: Yuhan Zhou <zhouyuhan_@outlook.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5339065](https://github.com/vllm-project/vllm/commit/533906528c901e048473df8224d5e54c3aec75c9)

- **作者**: azaidy
- **时间**: 2026-10-26T20:58:41Z
- **提交信息**: [Bugfix][Spec Decode] DFlash: run the aux hidden state FC in the draft dtype (#63436)

Signed-off-by: Aliasger Zaidy <aliasger.zaidy@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [12d54c2](https://github.com/vllm-project/vllm/commit/12d54c2948534a12eb5e6a91a8983ca11bc26f1c)

- **作者**: Lena Onyshchenko
- **时间**: 2026-10-26T20:57:18Z
- **提交信息**: [XPU][MoE] Resize batched Triton MoE tiles and change grid order (#51605)

Signed-off-by: Lena Onyshchenko <xonyshch@gmail.com>
Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [f3bdb0e](https://github.com/vllm-project/vllm/commit/f3bdb0e02515b972372a50844a2d7ca65eed209b)

- **作者**: Ilya Markov
- **时间**: 2026-10-26T20:51:55Z
- **提交信息**: [Perf][MXFP4] Optimize activation quant for mxfp4. 3x kernel speedup, 5% throughput improvement (#63101)

Signed-off-by: ilmarkov <markovilya197@gmail.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [01b05cd](https://github.com/vllm-project/vllm/commit/01b05cd69d788c87f8bcc80fe811e1011806ac74)

- **作者**: jxj
- **时间**: 2026-10-26T20:48:13Z
- **提交信息**: [Bugfix][Frontend] Stop SSL certificate watchers when HTTP serving exits (#55699)

Signed-off-by: git-jxj <65210887+git-jxj@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [a2ecc8a](https://github.com/vllm-project/vllm/commit/a2ecc8ac4d3fc814464e173f9d6e6bd5d9e93f9d)

- **作者**: Itay Etelis
- **时间**: 2026-10-26T20:44:15Z
- **提交信息**: [Perf][HiSparse] Reduce residency hash probes (#61263)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3090266](https://github.com/vllm-project/vllm/commit/3090266d88b6c3abbe18483fa5bbc7de293d8ef0)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T20:40:32Z
- **提交信息**: [Bugfix][Kernel] persistent_topk: sync the CTA around radix barrier arrivals (#63475)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [89f0c8c](https://github.com/vllm-project/vllm/commit/89f0c8c668b45151aa0ee28b2510a9be9f868b97)

- **作者**: Blaze-DSP
- **时间**: 2026-10-26T20:37:03Z
- **提交信息**: [MoE][Model] Gemma 4: skip CUDA-graph padding rows in the routing kernel (#62525)

Signed-off-by: Blaze-DSP <devsp0703@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0a95e4d](https://github.com/vllm-project/vllm/commit/0a95e4d73c3a6f81ecdfff7c7fdc7b55fc0bf311)

- **作者**: liuzhenwei
- **时间**: 2026-10-26T20:35:40Z
- **提交信息**: [XPU][FP8] Use per-token dynamic FP8 activation quantization (#61362)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [c13d4a5](https://github.com/vllm-project/vllm/commit/c13d4a5a46c2c663b728aa21af7eb00ece6bd698)

- **作者**: Moein Khazraee
- **时间**: 2026-10-26T20:31:19Z
- **提交信息**: [KV Offload] Expose the processed prefix at request finalization (#57646)

Signed-off-by: Moein Khazraee <moein@nvidia.com>

### [af6665b](https://github.com/vllm-project/vllm/commit/af6665b5dd2098898dce52b9e1c5005863738024)

- **作者**: Chauncey
- **时间**: 2026-10-26T19:34:57Z
- **提交信息**: [Spec Decode] Support PCP with DSpark for DeepSeek-V4.1 (#61994)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [78e2f79](https://github.com/vllm-project/vllm/commit/78e2f796019384b07c9f9b6d8a371e3ea958b33a)

- **作者**: Nick Hill
- **时间**: 2026-10-26T19:00:58Z
- **提交信息**: [Perf][MRV2] Stage buffer contents by reference and copy straight into UVA (#63633)

Signed-off-by: Yibai Meng <yibaim@nvidia.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Yibai Meng <yibaim@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: leopck <4161783+leopck@users.noreply.github.com>
Co-authored-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Co-authored-by: Juntian Liu <Juntianl777@gmail.com>

### [9633997](https://github.com/vllm-project/vllm/commit/9633997299f29d54f1da38fb4a37e7d1a6535005)

- **作者**: liranschour
- **时间**: 2026-10-26T18:54:31Z
- **提交信息**: [KV Offload][P2P] Fail faster: per-mode load timeout, shorter abort-ack and lookup timeouts (#63781)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9e3db48](https://github.com/vllm-project/vllm/commit/9e3db48873b87a3c232f16991675d33abb49b72b)

- **作者**: Qidong Su
- **时间**: 2026-10-26T18:37:01Z
- **提交信息**: [MoE] Add locality-domain allocation for FlashInfer CuTeDSL NVFP4 (#61685)

Signed-off-by: Qidong Su <qidongs@nvidia.com>
Signed-off-by: Max Hu <hyoung2991@gmail.com>
Co-authored-by: Max Hu <maxhu@nvidia.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Bolin Sun <bolins@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Max Hu <hyoung2991@gmail.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [4135590](https://github.com/vllm-project/vllm/commit/4135590ffe0119dab806d78a7eee6dff3be2618e)

- **作者**: Lucas Wilkinson
- **时间**: 2026-10-26T17:59:24Z
- **提交信息**: [Bugfix][MRV2] Skip adaptive verification cost profiling in the CUDA graph memory-profiling pass (#63431)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [442f3d9](https://github.com/vllm-project/vllm/commit/442f3d989efc97bcdd5f48caa826b4aae1e7c7f1)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T17:41:43Z
- **提交信息**: [CI][ROCm] Take NIXL PD accuracy side-channel ports from below the ephemeral range (#63557)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ad42b45](https://github.com/vllm-project/vllm/commit/ad42b456f9d32dfda85f6c1cac381caf47aca8a3)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T17:41:40Z
- **提交信息**: [CI][ROCm] Take MoRIIO P/D test port blocks from below the ephemeral range (#63453)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [088e6a4](https://github.com/vllm-project/vllm/commit/088e6a4d6855deef1b980dffa890f03cd6c9967f)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T17:41:29Z
- **提交信息**: [CI][ROCm] Skip the AITER MoE garbage-rows test for fp8 per-tensor until the AITER fix (#63559)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [94b35f3](https://github.com/vllm-project/vllm/commit/94b35f37804e1ced80eccdb7bbc4a2db6b0879c1)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T17:40:53Z
- **提交信息**: [Bugfix][ROCm] Keep the AITER GDN decode fast path off for the DS conv-state layout (#63558)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9744ada](https://github.com/vllm-project/vllm/commit/9744ada58292af77f97d2b18e0266b06e71b2e8a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-26T17:40:43Z
- **提交信息**: [Bugfix][ROCm][DSv4.1] Await krdy before K2's combine reads klen in index-source launches (#63576)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [eca54bd](https://github.com/vllm-project/vllm/commit/eca54bd1d937e778a939c240a2ed966fbcb12f85)

- **作者**: Kai Hoang
- **时间**: 2026-10-26T17:19:57Z
- **提交信息**: [Bugfix][Tool Parser] Keep Step3 parameter values that contain '<' (#60968)

Signed-off-by: hpdkhoa <hpdkhoa2311@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [29be2f2](https://github.com/vllm-project/vllm/commit/29be2f256006f274f2b94d6963c7ab1c64e86309)

- **作者**: Zhang Bowen
- **时间**: 2026-10-26T17:15:12Z
- **提交信息**: [Bugfix][Spec Decode] Preserve DP replica index for standalone draft models (#62301)

Signed-off-by: MuonChaser <zbw.init@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [20bf65a](https://github.com/vllm-project/vllm/commit/20bf65ad333834440b82390c43b30de93137b9ee)

- **作者**: Diao Shengjia
- **时间**: 2026-10-26T17:03:29Z
- **提交信息**: [Bugfix][Rust Frontend] Read the text config under `thinker_config` (#61128)

Signed-off-by: GoDiao <diaoshengjia@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c361547](https://github.com/vllm-project/vllm/commit/c36154742ef6377d49e884c06a3df2b7a6ccf7eb)

- **作者**: Thuongvu Ho
- **时间**: 2026-10-26T17:02:52Z
- **提交信息**: [Bugfix][Rust Frontend] Use prefiller cache hits for P/D usage (#58885)

Signed-off-by: Thuongvu Ho <thuongvuho@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9da5ba7](https://github.com/vllm-project/vllm/commit/9da5ba7e49cfb5e04fe66fed67bf965de012070b)

- **作者**: Yifan Qiao
- **时间**: 2026-10-26T17:01:57Z
- **提交信息**: [Rust Frontend] Make HTTP request body limit configurable via VLLM_HTTP_MAX_REQUEST_BODY_SIZE (#47840)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3e75ccb](https://github.com/vllm-project/vllm/commit/3e75ccba298d0c7f045f35c39078cec74184b799)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-26T16:41:28Z
- **提交信息**: [Bugfix][DCP] Finalize the NIXL DCP interleave size before profiling (#62330)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>
Co-authored-by: Andy Lo <andy@mistral.ai>
Co-authored-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>

### [5be249d](https://github.com/vllm-project/vllm/commit/5be249d0ad6763e23a375dd26df73b5faeed91df)

- **作者**: Rehan Khan
- **时间**: 2026-10-26T16:36:48Z
- **提交信息**: [Kernel] Allow registering OOT block-scaled FP8 linear kernels (#62026)

Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c84ff6b](https://github.com/vllm-project/vllm/commit/c84ff6b3f4f10a12788fdd091306ba76dd510a86)

- **作者**: Monishver
- **时间**: 2026-10-26T16:36:04Z
- **提交信息**: [Kernel][Perf] Add H100 tuned configs for Llama-3.1-8B and Qwen3-8B to the batch-invariant matmul table (#62219)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4f140a2](https://github.com/vllm-project/vllm/commit/4f140a23de19dfc61056d321dd42ca461b49d316)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-26T16:31:41Z
- **提交信息**: [Bugfix] Initialize valid ModelOpt NVFP4 MoE dummy scales (#63698)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [33a73da](https://github.com/vllm-project/vllm/commit/33a73daf1771eaa1014d1f272b4ae6815ee62d7e)

- **作者**: Roberto L. Castro
- **时间**: 2026-10-26T16:25:16Z
- **提交信息**: [2/N][Bugfix] Make persistent TopK exact on candidate overflow (#62936)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>

### [536854b](https://github.com/vllm-project/vllm/commit/536854bf106a87e5df4ab62a3af151d4fa583749)

- **作者**: Rohan Potdar
- **时间**: 2026-10-26T16:18:35Z
- **提交信息**: [ROCm] Enable expert parallelism for AITER Triton W4A16 MoE (#59255)

Signed-off-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7f56f45](https://github.com/vllm-project/vllm/commit/7f56f453ede3fabd7311dcb6099ca6b6d8c49770)

- **作者**: Luu Bao Long
- **时间**: 2026-10-26T16:05:29Z
- **提交信息**: [Bugfix][Core][MRV2] Profile the sampler with the params the warm-up actually uses (#57926)

Signed-off-by: Luu Bao Long <longbaoluu68@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [df8b5d3](https://github.com/vllm-project/vllm/commit/df8b5d37819c11d70cf948b904faa537f489f56d)

- **作者**: djramic
- **时间**: 2026-10-26T15:59:23Z
- **提交信息**: [ROCm][CI] Raise MI300 Core Operation Kernels timeout to 90 min (#63760)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [50a184f](https://github.com/vllm-project/vllm/commit/50a184f43583dec8942a0494d1fec4f4acc4a2e9)

- **作者**: Aaron Hao
- **时间**: 2026-10-26T15:42:30Z
- **提交信息**: [RL] Declare weight ownership and layout on ParamMeta (#63256)

Signed-off-by: Aaron Hao <aaronhao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [61b2527](https://github.com/vllm-project/vllm/commit/61b2527bdb9ae565548ce6b7fbf49f0e92cf84b9)

- **作者**: Chen Cheng
- **时间**: 2026-10-26T15:39:00Z
- **提交信息**: [Perf][MoE] Add H200 FP8 fused MoE config for Beam-1.0 TP8 (#62763)

Signed-off-by: Chen Cheng <85005591+ischencheng@users.noreply.github.com>

### [0abec73](https://github.com/vllm-project/vllm/commit/0abec7309ecf0cccb2547bec263a118558a48628)

- **作者**: Li Wang
- **时间**: 2026-10-26T15:31:39Z
- **提交信息**: [Model] Add native support for Lfm2BidirectionalModel (#62201)

Signed-off-by: wangli <wangli858794774@gmil.com>
Co-authored-by: wangli <wangli858794774@gmil.com>

### [e113018](https://github.com/vllm-project/vllm/commit/e113018f5067045ac92de3949b8c302439abb226)

- **作者**: ztysth
- **时间**: 2026-10-26T15:30:22Z
- **提交信息**: [Bugfix][KV Offload] Preserve running request prefixes across LRU store batches (#61050)

Signed-off-by: Jack Brown <rnk.liulw@gmail.com>
Co-authored-by: Jack Brown <rnk.liulw@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [14d5931](https://github.com/vllm-project/vllm/commit/14d593115d9b46bc623372726ec1c1e9955d2ba6)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-26T15:20:59Z
- **提交信息**: [Bugfix][LoRA] Fix double pinning of 3D MoE LoRA and EP dummy LoRA sizing (#61636)

Signed-off-by: onepunchmonk <aggarwal.avaya@yahoo.com>
Signed-off-by: OnePunchMonk <aggarwal.avaya@yahoo.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [51d2a85](https://github.com/vllm-project/vllm/commit/51d2a855942907366bc15ba72d76130d0fc4346b)

- **作者**: liranschour
- **时间**: 2026-10-26T14:55:56Z
- **提交信息**: [Bugfix][KV Offload][P2P] Never block in ZmqConnection.send() (#63708)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [14aefcd](https://github.com/vllm-project/vllm/commit/14aefcd4f907ff91cb29b9e80bd9c6a5568944bb)

- **作者**: javieratomic
- **时间**: 2026-10-26T14:55:43Z
- **提交信息**: [Bugfix][KV Offload] Hold promotions after a cache reset until jobs report (#62929)

Signed-off-by: Javier López <59578422+javieratomic@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8a4b018](https://github.com/vllm-project/vllm/commit/8a4b018f1c1b5ebf195072a00196a915c4e534b3)

- **作者**: Sun
- **时间**: 2026-10-26T14:54:54Z
- **提交信息**: [Bugfix][KV Offload] Roll back failed P2P NIXL registration (#63628)

Signed-off-by: levius <2114377220@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [74340c7](https://github.com/vllm-project/vllm/commit/74340c7300cbf1c497eb7264ff33b964e01438ae)

- **作者**: Tony Lin
- **时间**: 2026-10-26T14:16:11Z
- **提交信息**: [docs] correct NIXL hybrid SSM heterogeneous TP support (#63036)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [8c6e770](https://github.com/vllm-project/vllm/commit/8c6e770a1ca9a522fa32f91995ba241e21e5a88c)

- **作者**: Vedant Agarwal
- **时间**: 2026-10-26T14:15:53Z
- **提交信息**: [Bugfix][KV Offload][OBJ] Namespace object keys by blocks_per_chunk (#63655)

Signed-off-by: Vedant Agarwal <vedantagwl10@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2f1cb15](https://github.com/vllm-project/vllm/commit/2f1cb151fd9b036422cc27f0ad82f5f66edec879)

- **作者**: sudhanshu shukla
- **时间**: 2026-10-26T13:45:35Z
- **提交信息**: [Bugfix] Preserve fp16 in legacy fused MoE LoRA (#59931)

Signed-off-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Co-authored-by: sudhanshu shukla <sudhanshu112233shukla@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fcb7870](https://github.com/vllm-project/vllm/commit/fcb787055e85b3c9620b47c531b3de4b9453c45f)

- **作者**: Misha Goin
- **时间**: 2026-10-26T13:37:42Z
- **提交信息**: [Perf][DeepSeek V4] Declare MXFP8 MoE activations and run them as block FP8 on Hopper (#61875)

### [d0d681e](https://github.com/vllm-project/vllm/commit/d0d681e40def0f526e605bd41a7678d8b2bce12d)

- **作者**: Shanshan Shen
- **时间**: 2026-10-26T13:14:55Z
- **提交信息**: [ROCm][Perf] Make MXFP4 the default indexer K cache dtype for DeepSeek-V4 (#63669)

Signed-off-by: shen-shanshan <467638484@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [373614f](https://github.com/vllm-project/vllm/commit/373614f66dc8dc678faaf33223256f814238b7cb)

- **作者**: Sy03
- **时间**: 2026-10-26T12:56:11Z
- **提交信息**: [Bugfix][Multimodal] Release consumed MRV2 CPU inputs (#57368)

Signed-off-by: Sy03 <1370724210@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a64fc94](https://github.com/vllm-project/vllm/commit/a64fc94081cfa3f0061a87e6c0646ed472552a1b)

- **作者**: Vegetog
- **时间**: 2026-10-26T12:51:12Z
- **提交信息**: [Bugfix][KV Offload] Preserve new loads during same-step resume (#60574)

Signed-off-by: Vegetog <110553275+Vegetog@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [f682f1d](https://github.com/vllm-project/vllm/commit/f682f1dc32586f43c3917c4516b8f95f7bf0471d)

- **作者**: Nili Guy
- **时间**: 2026-10-26T12:50:55Z
- **提交信息**: [Bugfix][KV Offload][P2P] Mark the session dead when its ConnectAck send fails (#63664)

Signed-off-by: nilig <nili.ifergan@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5b06b5f](https://github.com/vllm-project/vllm/commit/5b06b5f8e9d0dce0000c6c7039b5011899bebf2b)

- **作者**: Amir Friedman
- **时间**: 2026-10-26T12:50:06Z
- **提交信息**: [Metrics][KV Offload] Fill vllm:kv_offload_config_info with the CPU cache capacity (#53902)

Signed-off-by: Amir Friedman <Amir.Friedman1@ibm.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [51d43b3](https://github.com/vllm-project/vllm/commit/51d43b368355e74fe78357bb020d2b7868a9af47)

- **作者**: CharlesWu
- **时间**: 2026-10-26T12:47:10Z
- **提交信息**: [Test][UMBP][4/10] Cover async lookup, hybrid cache, events, and metrics (#61792)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [ffcabb8](https://github.com/vllm-project/vllm/commit/ffcabb8c7ab3e066e1c77b55d7673e5d08cf26cc)

- **作者**: snadampal
- **时间**: 2026-10-26T10:51:30Z
- **提交信息**: [docker] add vllm-openai-efa target (#58768)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>
Co-authored-by: Erez Zarum <erezz@amazon.com>
Co-authored-by: Sean Westfall <sean.westfall@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [71294c2](https://github.com/vllm-project/vllm/commit/71294c2e9ac41ed710b6eb4ca41cba3793705345)

- **作者**: Nili Guy
- **时间**: 2026-10-26T10:32:31Z
- **提交信息**: [Bugfix][KV Offload][P2P] Exclude rc_gda lanes from the P2P NIXL agent (#63498)

Signed-off-by: nilig <nili.ifergan@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c3941c0](https://github.com/vllm-project/vllm/commit/c3941c032d1571745dbaa644b1aa8182c8b50553)

- **作者**: BaoYunkai
- **时间**: 2026-10-26T10:21:24Z
- **提交信息**: [Bugfix][ROCm] Match the DeepSeek-V4.1 FP8 config in the shared-expert FSE compatibility check (#63099)

Signed-off-by: BaoYunkai <269084791+BaoYunkai@users.noreply.github.com>
Co-authored-by: BaoYunkai <269084791+BaoYunkai@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [1d3f05a](https://github.com/vllm-project/vllm/commit/1d3f05aadb9c100c9665dabc3bb188fcd3e7d0e8)

- **作者**: Stan
- **时间**: 2026-10-26T10:20:21Z
- **提交信息**: [Bugfix][KV Offload] Do not store sliding-window chunks with null blocks (#63652)

Signed-off-by: Stan <273962421+pepmach@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fe5fe8b](https://github.com/vllm-project/vllm/commit/fe5fe8ba5fb9412ac6deafd192ae8b7c466b96c5)

- **作者**: Kfir Toledo
- **时间**: 2026-10-26T09:16:30Z
- **提交信息**: [KV Offload] Load small CPU-tier hits synchronously within the step (#61961)

Signed-off-by: Kfir Toledo <kfir.toledo@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [d26d5db](https://github.com/vllm-project/vllm/commit/d26d5db01fa2d1a8579acca572e221bc4fab2fe7)

- **作者**: Yejing Lai
- **时间**: 2026-10-26T09:08:09Z
- **提交信息**: [XPU][CI] Enable test_fusion_rmsnorm_quant on XPU (#63658)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f1ac0cf](https://github.com/vllm-project/vllm/commit/f1ac0cf20d6eed1518f78ccf694bae03a437e258)

- **作者**: Ziyang Ma
- **时间**: 2026-10-26T09:08:05Z
- **提交信息**: [XPU][UT] Allow HF reference models to load LoRA adapters by adding PEFT to XPU test dependencies (#63694)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Signed-off-by: Ziyang Ma <ziyang.ma@intel.com>

### [beeed65](https://github.com/vllm-project/vllm/commit/beeed65c103a0d6109495749aee4b72ca0cfd3b0)

- **作者**: Juntian Liu
- **时间**: 2026-10-26T09:05:40Z
- **提交信息**: [Bugfix][KV Connector] Report every transfer group as loaded in DecodeBenchConnector (#62242)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d7aa93b](https://github.com/vllm-project/vllm/commit/d7aa93b378b40081aa421904e9d39666f005d3a7)

- **作者**: Isotr0py
- **时间**: 2026-10-26T08:57:41Z
- **提交信息**: [Rust Frontend] Update multimodal video frames sampling API (#63661)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Isotr0py <mozf@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [330c5bf](https://github.com/vllm-project/vllm/commit/330c5bffeeb48725c0502a351e8ead2b54bd81eb)

- **作者**: Jeffrey Wang
- **时间**: 2026-10-26T08:52:58Z
- **提交信息**: [Bugfix][KV Events] Prevent replay truncation when the send queue fills (#63224)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [256d8b4](https://github.com/vllm-project/vllm/commit/256d8b40d0864aa694e3dc236d9b351886a4a94a)

- **作者**: Sascha Wirges
- **时间**: 2026-10-26T08:27:15Z
- **提交信息**: [Doc] Kolibri 1 reasoning and tool-call parsing via HF response template (#62885)

Signed-off-by: Sascha Wirges <sascha.wirges@aleph-alpha-research.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6674eed](https://github.com/vllm-project/vllm/commit/6674eedd28d785bed1daf6309615ba337e791aa6)

- **作者**: Tony Lin
- **时间**: 2026-10-26T07:59:00Z
- **提交信息**: [XPU] Fix MLA cache op arguments (#63530)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9bea474](https://github.com/vllm-project/vllm/commit/9bea474d656a3569c5e95a0575e6da50b68cd832)

- **作者**: Mikko Tukiainen
- **时间**: 2026-10-26T07:43:18Z
- **提交信息**: [ROCm][Perf] Use AITER FlyDSL INT4 QuickReduce when INT4 QuickReduce is selected (#59478)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>

### [4b1c04e](https://github.com/vllm-project/vllm/commit/4b1c04e76fe9ac3ca8b7e541dd423e7d5f38dc60)

- **作者**: Jee Jee Li
- **时间**: 2026-10-26T07:19:41Z
- **提交信息**: [Doc] Update Muse Spark Open  (#63651)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [ae3bc68](https://github.com/vllm-project/vllm/commit/ae3bc684e021f4b8c17c86a42e149b4482bc4ebe)

- **作者**: Chun Fang
- **时间**: 2026-10-26T07:01:19Z
- **提交信息**: [Doc][ROCm] Update DeepSeek-V4.1-Flash MI355X AgentX scheduling profiles (#63665)

Signed-off-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [2f34dce](https://github.com/vllm-project/vllm/commit/2f34dce5833ff8b83ab625f2b27df7e807865a09)

- **作者**: Chun Fang
- **时间**: 2026-10-26T07:01:07Z
- **提交信息**: [Doc][ROCm] Update Kimi-K3 MI355X AgentX scheduling cells (#63657)

Signed-off-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-27
**监控日期**: 2026-10-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7373
- **最后更新**: 2026-10-27T01:16:01Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 21
- **主要提交者**: wy17003, Nick Cao, Wenbo Ji　嵇文博

## AI分析总结

## vllm-omni 昨日提交分析（26 条）

### 1. 主要更新类型
- **Bug修复**：约 11 条，是最大类别，覆盖引擎参数、调度、评测基准、音频处理等
- **CI/Build**：约 7 条，持续补齐各硬件与模型的回归测试
- **硬件支持**：约 4 条，集中于 Intel XPU、华为 Ascend NPU、ROCm
- **性能优化/重构**：约 4 条，包括编译哈希优化、调度器重构、INT4 量化模型

### 2. 关键变更点与项目方向的关系
- **多硬件覆盖加速**：SageAttention 在 XPU 上适配新版本 auto-round、SeedVR2 与 MOSS-TTS 登陆 Ascend NPU、ROCm 上新增 Qwen3-Omni 压测——直接服务 README 中"为所有人提供 omni 模型服务"的跨平台愿景。
- **评测体系严格化**：Omni-DuplexEval 参考音频与评分校准、audio_ttfp goodput SLO、SenseNova/H100 准确率回归恢复，表明项目正把全模态（语音-视觉-文本）延迟与质量指标制度化。
- **引擎健壮性**：修复 from_cli_args 丢失扩散并行参数（两条相似提交）、非致命请求错误后离线引擎存活、拒绝非法 prompt ids——提升服务端稳定性，符合生产可用目标。
- **调度重构推进**：`[3/N Scheduler]` 将模型元数据解释从调度器内部抽离为类型化适配契约，是分阶段架构现代化的一环。

### 3. 对项目的影响与潜在意义
- 多后端一致性与测试基线的完善，显著降低多模态服务在不同加速卡上的行为漂移风险；参数与资源校验类修复减少了静默错误带来的线上故障。
- 评测对齐官方标准使 vllm-omni 的延迟/质量数据更可信，有助于吸引对全双工对话有严格 SLA 的用户。

### 4. 值得关注的技术点
- **wakeup_scope UUID 排除出 Torch Compile 哈希**：避免无效重编译，属于编译缓存层的精细优化。
- **Drama 3 解码步重放为 FULL graph**（Ascend）与 **Drama-3-int4 混合 INT4 checkpoint**（CUDA SM80+）：同一模型在两类硬件上的量化与图优化配套推进，是异构部署能力的体现。
- **组块交互延迟修复**（#8810）与 vocoder 移除虚假 `SupportsPP` 声明：涉及流水线并行与交互式语音的底层语义，值得后续关注回归表现。
- 同一模式的修复出现重复提交（如扩散并行参数），提示 merge 流程中可能存在竞争。

### 5. 对项目发展的整体影响
结合 README，vllm-omni 的目标是"简单、快速、低成本的全模态模型服务"。本批提交呈现**三条主线并进**：以 XPU/NPU/ROCm 适配扩展"简单可用"的硬件面；以编译哈希、图捕获、INT4 支撑"快速低成本"的性能面；以严格评测、CI 基线、引擎鲁棒性夯实"人人可用"的可靠性面。短期内项目成熟度稳步提升，长期看，跨模态评测标准化与多后端收敛是其差异化竞争力的关键。

## 详细提交记录

### [888d1a1](https://github.com/vllm-project/vllm-omni/commit/888d1a101460eba886aef0bfb0dcf6e56091db60)

- **作者**: Tomasz Zielinski
- **时间**: 2026-10-26T23:25:01Z
- **提交信息**: [Bugfix][XPU] Support auto-round-lib >= 0.15 in SageAttention backend (#9255)

Signed-off-by: Tomasz Zielinski <tomasz.zielinski@intel.com>
Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a69c429](https://github.com/vllm-project/vllm-omni/commit/a69c429f9069305aa2b82828ab57ae4a932bfd4b)

- **作者**: lm10-arg
- **时间**: 2026-10-26T23:17:12Z
- **提交信息**: [CI/Build][ROCm] Add Qwen3-Omni scale and performance burn-in (#9427)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [c84638f](https://github.com/vllm-project/vllm-omni/commit/c84638f3208f0fffd872200adfc5860103a6244b)

- **作者**: Qing7364
- **时间**: 2026-10-26T17:29:17Z
- **提交信息**: [CI/Build] Restore SenseNova-U1 smoke and H100 accuracy coverage (#8759)

Signed-off-by: Qing <vera.xpq@gmail.com>

### [0bce034](https://github.com/vllm-project/vllm-omni/commit/0bce034b7bbe3d9937103300bc794e6b4620d0b6)

- **作者**: Alex Brooks
- **时间**: 2026-10-26T17:15:48Z
- **提交信息**: [Perf] Exclude wakeup_scope UUIDs from Torch Compile Hash Key (#8899)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [934a3ab](https://github.com/vllm-project/vllm-omni/commit/934a3ab4ab8b0acc29c5a3bb354da6f5e3757223)

- **作者**: Yufeng He
- **时间**: 2026-10-26T17:09:56Z
- **提交信息**: [Bugfix][Engine] Preserve non-parallel diffusion engine args across from_cli_args (#8585)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [6935183](https://github.com/vllm-project/vllm-omni/commit/69351837af2e11aa63bee577528ee5afc7d8ca3d)

- **作者**: Nick Cao
- **时间**: 2026-10-26T16:45:26Z
- **提交信息**: [CI/Build] Re-enable turn-based server VAD realtime test (#9300)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [b9f93ed](https://github.com/vllm-project/vllm-omni/commit/b9f93ed6e0217c6383ce73d62efe5daf7d3972a8)

- **作者**: ZacheryAU
- **时间**: 2026-10-26T16:42:30Z
- **提交信息**: [Bugfix][Benchmark] Enable audio_ttfp goodput SLOs on the current bench CLI (#9322)

### [a46f860](https://github.com/vllm-project/vllm-omni/commit/a46f860b79e63bff6ea9f2c5fc5a88f3172b89d0)

- **作者**: Rakesh Kariya
- **时间**: 2026-10-26T16:28:23Z
- **提交信息**: [Bugfix] Stop vocoder stages from declaring SupportsPP without make_empty_intermediate_tensors (#6860)

Signed-off-by: rk9595 <rakesh.kariya@somaiya.edu>
Signed-off-by: Rakesh Kariya <rakesh.kariya@somaiya.edu>

### [3ca10fb](https://github.com/vllm-project/vllm-omni/commit/3ca10fb809a99a04e38e2ef99c9ae4e0886b58ef)

- **作者**: amy-why-3459
- **时间**: 2026-10-26T16:08:45Z
- **提交信息**: [Bugfix] Align MiniCPM-o reference audio with Transformers while retaining vision SDPA (#9386)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [bf98347](https://github.com/vllm-project/vllm-omni/commit/bf98347c9ccd5b96be6620ccc4a63df72c63b49e)

- **作者**: RyanYun09
- **时间**: 2026-10-26T15:43:12Z
- **提交信息**: [Bugfix][Benchmark] Match official Omni-DuplexEval GT reference handling (#9056)

Signed-off-by: RyanYun09 <ryanyun0911@gmail.com>

### [7147cb9](https://github.com/vllm-project/vllm-omni/commit/7147cb935e395e91492d797f31e6c1558d703ca5)

- **作者**: Binbin Zhang
- **时间**: 2026-10-26T15:29:45Z
- **提交信息**: [Bugfix] Preserve the diffusion parallel knobs when engine args come from parsed CLI args (#8041)

Signed-off-by: Binbin Zhang <binbin36520@gmail.com>

### [441b2c7](https://github.com/vllm-project/vllm-omni/commit/441b2c7adc6c2ea28141b2f1bea38b17f15c310f)

- **作者**: Nick Cao
- **时间**: 2026-10-26T15:28:37Z
- **提交信息**: [Tests] Add tiny model test for StableDiffusionXLPipeline (#6169)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [ad3a730](https://github.com/vllm-project/vllm-omni/commit/ad3a730e870cdaf4d4856d08b34052159e772725)

- **作者**: Zhou Taichang
- **时间**: 2026-10-26T14:38:02Z
- **提交信息**: [Bugfix] Reject oversized stage budgets on integrated GPUs (#9404)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>

### [150bcf5](https://github.com/vllm-project/vllm-omni/commit/150bcf56a524a49b935118ff4142ea0aae16a034)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-26T13:57:23Z
- **提交信息**: [Bugfix] Keep the offline Omni engine alive after a non-fatal request error (#8450)

Signed-off-by: Wenbo Ji <36562829+fusheng-ji@users.noreply.github.com>

### [d689720](https://github.com/vllm-project/vllm-omni/commit/d689720c244f51794346bf605a012114b46d7786)

- **作者**: NumberWan
- **时间**: 2026-10-26T13:57:15Z
- **提交信息**: [CI/Build] Install fa3-fwd 0.0.3 with the dev extra (#9393)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [5b5eb49](https://github.com/vllm-project/vllm-omni/commit/5b5eb49cdc95af80d4d2c1270055096e32ad87da)

- **作者**: Zeng Chuang
- **时间**: 2026-10-26T13:48:15Z
- **提交信息**: [Hardware][NPU] Support SeedVR2 video restoration on Ascend NPU (#8737)

Signed-off-by: zengchuang <zengchuang3@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [b5bd597](https://github.com/vllm-project/vllm-omni/commit/b5bd597fbe85cf35e3fb139ea58e9f99fd42d941)

- **作者**: wangyu
- **时间**: 2026-10-26T13:22:49Z
- **提交信息**: [Bugfix] Reuse one Qwen3-Omni fault payload across concurrent requests (#9407)

Signed-off-by: yenuo26 <410167048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b392851](https://github.com/vllm-project/vllm-omni/commit/b392851aae1acf7295eb3b4069332ba67c1d4fc9)

- **作者**: Wallbreazzz
- **时间**: 2026-10-26T13:06:33Z
- **提交信息**: [Hardware][Ascend] Enable NPU reference encoding for MOSS-TTS Local (#9067)

Signed-off-by: zechen <houzechen1997@outlook.com>
Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [efdad4c](https://github.com/vllm-project/vllm-omni/commit/efdad4cf075c04d0e968cdf4a0423f5b3c8c3ef4)

- **作者**: amy-why-3459
- **时间**: 2026-10-26T12:55:19Z
- **提交信息**: [Perf][Ascend] Replay Drama 3 decode steps as FULL graphs (#9308)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [817d4c1](https://github.com/vllm-project/vllm-omni/commit/817d4c17feb702289a2d2b2cbacfd594c262b7a7)

- **作者**: Weiming Liao
- **时间**: 2026-10-26T12:07:32Z
- **提交信息**: [Model] Support fishaudio/drama-3-int4 hybrid INT4 checkpoint on CUDA SM80+ (#9391)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [949d3ce](https://github.com/vllm-project/vllm-omni/commit/949d3cef16d15bad1c181c6d3f7f844e96b28fbd)

- **作者**: wy17003
- **时间**: 2026-10-26T10:33:47Z
- **提交信息**: [Refactor][3/N Scheduler]Move model metadata interpretation out of scheduler internals into a typed adapter contract. (#6161)

Signed-off-by: wy17003 <yaow17003@gmail.com>

### [066d835](https://github.com/vllm-project/vllm-omni/commit/066d8355e03debf7bc675c0e50f3632622dc5599)

- **作者**: amy-why-3459
- **时间**: 2026-10-26T09:35:01Z
- **提交信息**: [CI/Build] Update MiniCPM-o A3 C8 TTFT baseline (#9388)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [13c1e82](https://github.com/vllm-project/vllm-omni/commit/13c1e82284ac5c97789a712238094f3f0ae495d2)

- **作者**: amy-why-3459
- **时间**: 2026-10-26T09:08:48Z
- **提交信息**: [CI/Build] Avoid busy polling in stage memory lifecycle tests (#9406)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [0b7f07c](https://github.com/vllm-project/vllm-omni/commit/0b7f07c85a534bb4265376bed9d178ecce2d111f)

- **作者**: psv666
- **时间**: 2026-10-26T08:37:21Z
- **提交信息**: [Bugfix] Reject invalid Omni-DuplexEval judge scores (#9390)

Signed-off-by: psv666 <2693925048@qq.com>

### [2c32448](https://github.com/vllm-project/vllm-omni/commit/2c324487942a04fb29ee82d74781292080b070b9)

- **作者**: maithilijoshi20
- **时间**: 2026-10-26T07:49:15Z
- **提交信息**: [Bugfix] Fix grouped chunk interaction latency (#8810)

Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>
Signed-off-by: windyskr <54269955+windyskr@users.noreply.github.com>
Co-authored-by: windyskr <54269955+windyskr@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0f7a408](https://github.com/vllm-project/vllm-omni/commit/0f7a408c3f930a35c3ea4d243714014233a610a3)

- **作者**: Wenbo Ji　嵇文博
- **时间**: 2026-10-26T07:11:28Z
- **提交信息**: [Bugfix][Diffusion] Reject unsupported pre-tokenized prompt ids at engine admission (#8448)

Signed-off-by: Wenbo Ji <36562829+fusheng-ji@users.noreply.github.com>

---
