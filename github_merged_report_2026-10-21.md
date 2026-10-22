# GitHub Stars 合并报告 - 2026-10-21

**合并日期**: 2026-10-22
**监控日期**: 2026-10-21
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


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2257
- **最后更新**: 2026-10-21T15:30:05Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zeren Chen

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

这是一次**性能优化**兼具**功能增强**的提交。从提交标签 `[ops, perf]` 和 `feat:` 前缀可以看出，主要目标是优化 Flex-FA4（Flex Flash Attention 4）在掩码（masks）和动态序列长度（dynamic lengths）处理上的效率，属于底层算子（ops）层面的改进。

---

### 2. 关键变更点及与项目整体方向的关系

- **Flex-FA4 掩码优化**：优化了 Flex-FA4 内核中掩码（mask）的处理逻辑。在多模态训练中，不同模态（文本、图像、视频、音频）的序列结构差异很大，掩码机制对注意力计算的正确性和效率至关重要。这次优化直接针对这一核心瓶颈进行改进。

- **动态长度支持优化**：改进了对可变序列长度的处理能力。VeOmni 作为一个支持任意模态模型训练的框架，不同模态数据的序列长度天然不一致，动态长度的支持是实现高效多模态混合训练的关键基础。

- **与项目方向的关联**：VeOmni 的核心目标是"以模型为中心的分布式配方"来扩展任意模态模型训练。Flash Attention 系列优化是高效训练的核心组件之一，此次优化直接增强了框架在注意力计算层面的性能上限，与项目"Scaling Any Modality Model Training"的愿景高度一致。

---

### 3. 对项目的影响和潜在意义

- **训练效率提升**：通过优化掩码和动态长度处理，可以减少注意力计算中的冗余操作和内存占用，从而提升整体训练吞吐量，降低多模态训练的时间和计算成本。

- **多模态场景适配增强**：更好的掩码处理意味着在不同模态混合训练时，跨模态的注意力计算更加高效和准确；动态长度优化则直接提升了对不规则序列数据的处理能力。

- **生产可用性增强**：此类底层优化表明项目正在从"能跑通"向"跑得好、跑得快"演进，是项目成熟度提升的重要标志。

---

### 4. 值得关注的技术点

- **Flex-FA4**：作为 Flash Attention 4 的弹性变体，其设计本身就很值得关注。它如何在保持 Flash Attention 高效性的同时支持更灵活的掩码模式和动态长度，是多模态注意力优化中的前沿方向。

- **掩码优化策略**：在多模态训练中，掩码的构建和应用往往是性能瓶颈之一。本次优化可能涉及掩码的稀疏化处理、延迟计算或融合策略，值得深入查看代码细节。

- **动态长度的实现方式**：如何在 GPU 内核层面高效支持可变长度序列（如使用 varlen 接口或分桶策略），是理解本次优化技术含量的关键。

---

### 5. 对项目发展的整体影响

结合项目背景，VeOmni 定位为面向多模态大规模训练的分布式框架。此类底层算子优化虽然看似细节，但对项目的核心竞争力至关重要：

- **性能是多模态训练框架的核心竞争力**，底层注意力算子的每一次优化都能为用户带来直接的成本节约。
- **多模态训练的特殊性**（变长序列、异构掩码）决定了这类优化是项目能否真正实现"Any Modality"目标的关键技术支柱。
- 该提交属于项目持续迭代优化的一部分，说明团队正在系统性地打磨训练性能，为更大规模、更多模态的模型训练奠定基础。

## 详细提交记录

### [856941f](https://github.com/ByteDance-Seed/VeOmni/commit/856941f055e03f86b1f8bf3c0836663b2300e1c4)

- **作者**: Zeren Chen
- **时间**: 2026-10-21T08:25:57Z
- **提交信息**: [ops, perf] feat: optimize Flex-FA4 masks and dynamic lengths (#1328)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2935
- **最后更新**: 2026-10-21T17:03:32Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

## LightX2V 昨日提交分析

**提交信息：** `docs: streamline supported model ecosystem in READMEs (#1644)`

---

### 1. 主要更新类型

**文档更新**。该提交为纯文档改动，旨在精简和优化 README 中关于支持模型生态系统的描述，不涉及代码逻辑、功能或性能变更。

---

### 2. 关键变更点及其与项目整体方向的关系

- **变更核心**：整理了 README 中"支持的模型列表/生态系统"的呈现方式，使其更加精炼、清晰。
- **与项目方向的关联**：LightX2V 的定位是"轻量级视频生成推理框架"，其核心竞争力之一就是对多种视频生成模型的广泛支持。README 是用户了解框架能力的第一窗口，模型支持列表的准确性与可读性直接影响用户的评估和选型决策。精简模型生态系统描述意味着项目可能在做两件事：一是随着支持模型增多，原列表冗余杂乱需要优化；二是可能对支持范围做了聚焦，去除过时或边缘化的模型引用，使文档更贴近当前实际能力。

---

### 3. 对项目的影响和潜在影响

- **对用户体验**：降低新用户了解框架支持范围的认知成本，提升文档质量。
- **对项目维护**：精简后的模型列表更容易保持与代码实际支持状态同步，减少文档与实现脱节的风险。
- **对生态定位**：通过清晰呈现模型生态，有助于向潜在用户和贡献者传达项目的定位边界——哪些模型是核心支持的，哪些是社区贡献的，增强项目的透明度和可信度。
- **潜在信号**：若此次精简移除了部分模型引用，可能暗示项目正从"广泛兼容"向"深度优化主流模型"的策略转变。

---

### 4. 值得关注的技术点

- **PR #1644** 是通过 Pull Request 流入的变更，说明项目已有规范的协作和审查流程。
- 单独的 `docs` 类型提交表明团队遵循了良好的提交规范（如 Conventional Commits），将文档变更与代码变更分离，便于追溯。
- 模型生态的"streamline"（精简）过程值得关注后续是否伴随代码层面的模型支持范围调整——即是否有模型支持的正式移除或新增计划。

---

### 5. 对项目发展的综合影响

从 README 来看，LightX2V 致力于成为一个高效、轻量的视频生成推理框架，同时提供了中英文双语文档和完善的徽章标识，说明项目重视国际化和开源社区体验。此次文档精简提交虽然表面上影响有限，但它反映了项目团队在**成熟度管理**上的持续投入：随着框架支持的模型不断增多，定期梳理和优化文档是项目走向稳定的标志。对于一个推理框架而言，"支持哪些模型"是其核心价值主张，清晰准确地传达这一信息有助于吸引目标用户（如需要快速部署视频生成能力的开发者），也能为后续可能的模型版本淘汰或新增提供文档层面的铺垫。总体而言，这是项目健康运营和社区协作规范化的体现。

## 详细提交记录

### [19c1961](https://github.com/ModelTC/LightX2V/commit/19c19614b067f1746ac24350dfd097e1c0b48591)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-21T11:14:19Z
- **提交信息**: docs: streamline supported model ecosystem in READMEs (#1644)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2310
- **最后更新**: 2026-10-21T11:55:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6735
- **最后更新**: 2026-10-22T00:40:35Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 11
- **主要提交者**: Jonathan Dierksen, Bo Li, Zhong Zheng

## AI分析总结

# FlashInfer 昨日提交综合分析（共 34 个提交）

## 一、主要更新
以**性能优化**为主，辅以功能新增、代码去重重构、Bug 修复与 CI 改进。功能覆盖注意力、MoE、通信原语、量化与训练算子；平台横跨 SM80 至 SM107/SM110，涵盖 Hopper、Blackwell GB200/GB300 与 Rubin。

## 二、关键变更
**通信与计算融合**：QKV 归一化、RoPE 与 Ulysses 交换合并为单内核；MNNVL all-reduce 由多次 launch 压缩为一次 persistent kernel，并新增 NVFP4 all-reduce 与 RMSNorm、残差相加三算子融合，以负零哨兵实现无 grid barrier 的就绪判定，每 rank 仅需一个常驻 CTA。

**低精度谱系完善**：新增 NVFP4 QSA 稀疏分页注意力（配合 vLLM）、NVFP4 MLA 分页解码、E4M3 主流输出格式、4over6 块缩放、MXFP8 分组量化 CUDA 后端，以及 MiniMax-H3 的 NVFP4-QK + FP8-PV 混合模式；QSA 直接解码为 mma.sync 碎片，仅用 SM80 指令覆盖 8.0–9.0 架构。

**MoE 健壮性与通用化**：修复 SM90 MegaMoE 在 single_active_dispatch_warp 模式下 workspace 被空专家计数清理、残留 stale 数据的缺陷（H20 上 97–128 token/Rank，CUDA Graph 捕获时会引发 launch 失败）；专家数从三个精调几何形状扩展到任意可整除数量，支持 Kimi-K2、DeepSeek-V3、GLM-4.x、Qwen3；H200 按 M 分桶启用 push dispatch，每次调用省约 10 µs，提速 1.03–1.16 倍。

**GEMM 微优化**：双 scale 乘积融合进 CuTe-DSL epilogue，以 kernel 内标量加载替代 host 端 torch op，消除每次调用的额外 launch，使 bmm_fp8_cute_dsl 在 autotuner 中与 cuBLAS、cuDNN、CUTLASS 的比较更公平，小 M 场景收益显著。

**算子扩张与代码治理**：TRTLLM-Gen 滑动窗口 FMHA、MiniMax 稀疏注意力、Gated DeltaProduct 解码（最高近 4 倍提速）、Mamba2 SSD、RMSNorm 训练梯度、因果卷积反向、统一 Frost 低延迟 MoE 后端相继落地；多轮去重将 34 个 BMM 源折叠为 6 个、81 个重复主机绑定收敛为 6 个、43 个共享 launcher 收敛为 9 个，净删数万行，并把 NVFP4 稀疏 MLA、DeepGEMM 派生 FP8 GEMM 打包为自包含模块。

**修复与集成**：修复 host 张量错误处理顺序、CUDA 13.3 寄存器溢出、A10G 单 nvcc 编译导致的 2.6–4.5× 慢速、MNNVL 句柄类型不一致挂起；补充 MegaMoESymmBuffer.prewarm() 钩子与 MoE 权重转换说明。

## 三、技术关注点
多数改动以 bitwise-identical 输出为正确性标准，升级风险低；MegaMoE planner 检查完整 shared-memory 布局，不匹配时自动降级、完全不支持则抛出 ValueError，避免静默出错；scale 融合不改变编译缓存 key，不触发重编译且 CUDA Graph 行为不变；按架构与形状分发的 JIT 注册表、显式精度权衡 API，以及冷 L2、CUDA graph 中位数、SASS 对比等实验方法学体现工程纪律。

## 四、项目影响
性能收益可验证：通信重叠提速最高 11.3%，E4M3 较 NVFP4 基线快 17–18%，NVFP4 QSA 比 FP8 Triton 快 10–19%；Hopper 首次获得 Cake 稀疏注意力，Rubin 获得 NVFP4 MLA 与 SSD 加速，量化 API 补齐 vLLM MXFP8 MoE 在 DeepEP 低延迟路径的拼图，TRTLLM-Gen CUBIN 锁定 36,964 个工件。项目双轨推进：一方面以架构级微调、通信计算融合与低精度深化维持推理内核 SOTA，另一方面通过深度融入 NVIDIA Cake、去重打包与 CI 分片（节约约 90 runner 小时）控制多后端复杂度，最终成长为面向多架构 GPU、多精度、多算子的端到端内核生态，为 vLLM 等下游框架奠定生产就绪基础。

## 详细提交记录

### [4d69fbc](https://github.com/flashinfer-ai/flashinfer/commit/4d69fbce710c1c7e2cf6eff8dd06a8957f698d0c)

- **作者**: eigen
- **时间**: 2026-10-21T23:44:53Z
- **提交信息**: perf(cake_comm): QkvNormRopeExchangeOverlap SM90 eight-rank plans use one readiness word per destination (#6964)

`QkvNormRopeExchangeOverlap` combines the QKV projection, per-head QK
RMSNorm and RoPE with the Ulysses QKV all-to-all exchange in one kernel
(BF16 activations and weights, fp32 accumulation). Its producer has four
builds: the shipped build, `ow256`, `bulk_ow256` and `bulk`. The
exchange has two-, four- and eight-rank plans. This PR changes only the
SM90 eight-rank plan default. Every SM90 eight-rank plan now publishes
one readiness word per destination. Before this change, the plan used
one word per destination only for M ≤ 4096 rows. Above that, it used one
word per 128-row m-tile, up to 512. No kernel program changes. At S =
65536 and S = 131072, the one-word plan is faster than the previous
default plan for every H, with speedups of 1.009 to 1.113. At S ≤ 32768
(M ≤ 4096), both plans already publish one word per destination, and the
speedup is 0.998 to 1.003. The previous plan stays selectable through
`FLASHINFER_QKV_EXCHANGE_SHAPE_GATES=words_capacity_small_m=4096`.

Eight-rank kernel latency on 8 × NVIDIA H100 (`sm_90a`), CUDA 13.3;
values are CUPTI medians, cold L2 cache, same node and process for both
arms. Rows per rank M = S / 8; speedup = previous / new.

| H | S | previous default plan (ms) | one-word plan (ms) | speedup |
|---:|---:|---:|---:|---|
| 3072 | 4096 | 0.090336 | 0.090384 | 0.999 |
| 3072 | 8192 | 0.145344 | 0.145439 | 0.999 |
| 3072 | 16384 | 0.255167 | 0.254350 | 1.003 |
| 3072 | 32768 | 0.495004 | 0.494782 | 1.000 |
| 3072 | 65536 | 1.086619 | 1.021176 | 1.064 |
| 3072 | 131072 | 2.327154 | 2.090496 | 1.113 |
| 4096 | 4096 | 0.128383 | 0.127936 | 1.003 |
| 4096 | 8192 | 0.190655 | 0.190895 | 0.999 |
| 4096 | 16384 | 0.356367 | 0.356206 | 1.000 |
| 4096 | 32768 | 0.689194 | 0.689099 | 1.000 |
| 4096 | 65536 | 1.367430 | 1.335943 | 1.024 |
| 4096 | 131072 | 2.709351 | 2.637223 | 1.027 |
| 6144 | 4096 | 0.246126 | 0.246062 | 1.000 |
| 6144 | 8192 | 0.397070 | 0.395744 | 1.003 |
| 6144 | 16384 | 0.700779 | 0.701386 | 0.999 |
| 6144 | 32768 | 1.418235 | 1.420469 | 0.998 |
| 6144 | 65536 | 2.902214 | 2.830646 | 1.025 |
| 6144 | 131072 | 5.877919 | 5.688383 | 1.033 |
| 8192 | 4096 | 0.325230 | 0.325582 | 0.999 |
| 8192 | 8192 | 0.616779 | 0.616988 | 1.000 |
| 8192 | 16384 | 1.218851 | 1.220023 | 0.999 |
| 8192 | 32768 | 2.469178 | 2.470904 | 0.999 |
| 8192 | 65536 | 5.089398 | 4.985157 | 1.021 |
| 8192 | 131072 | 10.553268 | 10.461146 | 1.009 |

The family ships BF16 producer programs for `sm_90a` (H100 / H200),
`sm_100a` (B200), `sm_103a` (B300) and `sm_107a` (R200) with two-, four-
and eight-rank plans (eight-rank not on SM107); the per-destination
readiness-word plan is now the SM90 eight-rank default, while the two-
and four-rank SM90 plans and every SM100 / SM103 / SM107 plan keep their
previous defaults.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added architecture- and world-size-specific defaults for QKV exchange
shape gates.
- Added the `pair_off_large_m=N` gate for selecting a single-CTA
producer on applicable 256-column calls.
- Added support for `all` row thresholds and per-world-size gate
overrides.
  - Added clearer gate reporting and configuration spelling.

- **Documentation**
- Updated QKV exchange guidance with SM90 eight-rank behavior, gate
scope, supported syntax, and producer-selection rules.
- Clarified validation and error behavior for unsupported
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6e91361](https://github.com/flashinfer-ai/flashinfer/commit/6e91361a6b6dd1e175d8e8420ee3a275f0997e3f)

- **作者**: eigen
- **时间**: 2026-10-21T23:20:07Z
- **提交信息**: fix(msa_ops): let a host tensor reach the out= refusal of msa_sparse_decode_attention (#6962)

## 📌 Description

#6252 (8a93c9b83) routed the MSA surfaces through `is_sm90a_device()` in
`flashinfer/msa_ops/_sm90_dispatch.py`. In `msa_sparse_decode_attention`
(`flashinfer/msa_ops/sparse_decode.py`), it also moved the `out=`
`NotImplementedError` from before the device probe into the SM120/SM121
branch. `is_sm90a_device()` calls `flashinfer.utils.is_sm90a_supported`,
which calls `get_compute_capability`. For a non-CUDA device,
`get_compute_capability` raises `ValueError("device must be a cuda
device")`. As a result, a call with host (CPU) tensors fails with that
`ValueError` before the surface's own raise rules run.

This breaks
`tests/msa_ops/test_msa_nvfp4_decode_sm100.py::test_out_on_a_route_that_cannot_honour_it_raises_instead_of_copying`,
which uses CPU inputs and expects a `NotImplementedError` matching
`"out="`. It failed on the `JIT Unittest (H100)` lane in the PR Test run
of #6403 (run 39640462785: 1 failed, 63789 passed, 101657 skipped). CI
for #6252 ran only a scoped `Targeted Unittest (H100)` lane, which did
not include this file.

**Changes** (3 files, +28/-9)

- `flashinfer/msa_ops/_sm90_dispatch.py`: `is_sm90a_device()` now
returns `False` for a non-CUDA device before it imports or calls
`is_sm90a_supported`. This matches `is_blackwell_msa_device()` in
`_blackwell_sm100.py`, which already checks `device.type == "cuda"`
first. All four MSA surfaces use this predicate (sparse decode, sparse
prefill, proxy score, top-k select), so for host tensors their own raise
rules now run first. CUDA devices get the same result as before, and the
`lru_cache` key is unchanged.
- `flashinfer/msa_ops/sparse_decode.py`: on any non-SM90 route,
`msa_sparse_decode_attention` now raises the `out=`
`NotImplementedError` right after computing `sm90` and before the
`RuntimeError` device check. The message is the same as on main, and
this is the order used before #6252. The duplicate check in the
SM120/SM121 branch is removed. The `out` docstring now names the compute
capability 9.0 route, which honours `out=` since #6252.
- `tests/msa_ops/test_msa_sm90.py`: adds
`test_sm90_predicate_is_false_for_a_host_tensor`, which asserts
`is_sm90a_device(torch.device("cpu")) is False`. It has no `sm90_only`
marker, so it runs on every lane.

**Behaviour of `msa_sparse_decode_attention`**

| Case | This PR | Compared with main / pre-#6252 |
|---|---|---|
| CPU tensor, `out=` given | `NotImplementedError("out= ...")` |
Restored. Main (after #6252) raises `ValueError` |
| CPU tensor, no `out` | `ValueError("device must be a cuda device")`
from `is_sm12x_supported` | Same as before #6252 |
| Non-SM90/SM12x CUDA (e.g. sm_86), `out=` given | `NotImplementedError`
| Restored. Main raises `RuntimeError` ("requires SM90, SM120 or SM121")
|
| SM90 | `out=` validated and written in place | Unchanged vs main |
| SM120/SM121, `out=` given | Same `NotImplementedError` text, raised
before the q/q2k shape checks | Pre-#6252 order |
| Compute capability 10.0/10.3/10.7 | Early return | Unchanged |

**Verification** (CPU-only host, no GPU: Python 3.12.15, torch
2.14.1+cu130, `torch.cuda.is_available()` is `False`)

- Unpatched main `cd6c1885a`: the failing test gives 1 failed
(`ValueError: device must be a cuda device`).
- This branch: the same test gives 1 passed.
`tests/msa_ops/test_msa_nvfp4_decode_sm100.py
tests/msa_ops/test_msa_sm90.py` gives 64 passed, 242 skipped. The
skipped items are GPU-only and skip on a host without a GPU.
- The other 11 files under `tests/msa_ops/` give identical results on
both trees: 30 failed, 430 passed, 195 skipped. Every failure is
`RuntimeError: Found no NVIDIA driver on your system` from a test that
assumes a GPU, so none relate to this change.

## 🔍 Related Issues

Regression from #6252; surfaced on the `JIT Unittest (H100)` lane of
#6403.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The ruff hooks' pinned `ruff` (0.12.8) `check` and `format --check` were
run on the three changed files and are clean; the full `pre-commit run
--all-files` was not run.

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

- Verification was done only on a host without a GPU. The GPU lanes will
run in CI on this PR, and `JIT Unittest (H100)` is the lane that showed
the failure.
- The predicate change only affects non-CUDA devices. For CUDA devices,
`is_sm90a_device()` returns the same result with the same cache key.
- On CUDA, the visible ordering changes are confined to
`msa_sparse_decode_attention` calls that pass `out=` on a non-SM90
route. These now raise the `out=` `NotImplementedError` before the
device `RuntimeError` and the SM120/SM121 q/q2k shape checks, which is
the order used before #6252.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Bug Fixes**
- Improved device validation for non-CUDA devices, including host
tensors, to avoid unsupported capability checks.
- Added clearer handling for the `out=` parameter in SM90 sparse decode
attention.
  - Prevented duplicate `out=` validation in the SM120/SM121 backend.

- **Documentation**
- Documented `out=` support for the SM90 route and the behavior of
device validation.

- **Tests**
- Added regression coverage confirming host devices are safely
identified as non-SM90 devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [53f175d](https://github.com/flashinfer-ai/flashinfer/commit/53f175d7d74319e47131424547cb9427c0297c20)

- **作者**: SeongJun Lee
- **时间**: 2026-10-21T23:00:05Z
- **提交信息**: feat(qsa_nvfp4): add NVFP4 QSA sparse paged attention (#6804)

<!-- .github/pull_request_template.md -->

## 📌 Description

This adds `flashinfer.sparse.qsa_sparse_paged_attention`, an
experimental API for the main attention of the Qwen4Exp QSA layer over
an NVFP4 KV cache on SM80 through SM90. It takes the same arguments as
vLLM's Triton `qsa_sparse_paged_attention` plus the NVFP4 block scales
`k_sf` / `v_sf`, and reads the paged layout written by
`nvfp4_quantize_append_paged_kv_cache_with_slot_mapping`, so vLLM keeps
its existing NVFP4 cache allocation and writer. vLLM's QSA layers take
BF16 and FP8 KV today; with NVFP4 one token's K or V head is 144 bytes
instead of 256.

The backend is in `flashinfer/experimental/qsa_nvfp4/`: a split-K kernel
with one CTA per (row, KV head, split) over 64-token tiles, and an LSE
merge that also applies the sigmoid output gate. NVFP4 is decoded
straight into `mma.sync` fragments, and QK and PV both run on BF16
operands with FP32 accumulation. Only SM80 instructions are used, so one
JIT module covers 8.0 through 9.0. Outside the package, the change is
the thin entry point in `flashinfer/sparse.py` and one package-data
line.

Decode attention on sm_80 with a 250 W power limit, against vLLM's
Triton kernel on an FP8 cache: 24 query heads, 2 KV heads, head_dim 256,
2,051 selected tokens from an 8K context per row, CUDA graph replay. The
step covers index mapping, attention and the output gate; KV cache
writes are not included. The 64- and 128-row points ran at the power
limit.

| rows | NVFP4, this PR (µs) | FP8, Triton (µs) | ratio |
| ---: | ---: | ---: | ---: |
| 1 | 14.5 | 13.2 | 1.10 |
| 2 | 17.1 | 14.1 | 1.21 |
| 4 | 20.2 | 17.9 | 1.13 |
| 8 | 28.4 | 32.0 | 0.89 |
| 16 | 47.4 | 58.5 | 0.81 |
| 32 | 86.3 | 94.6 | 0.91 |
| 64 | 158.1 | 165.3 | 0.95 |
| 128 | 304.2 | 336.7 | 0.90 |

## 🔍 Related Issues

Tracking issue: #6803

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

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #6803
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/test_qsa_nvfp4.py
```

## Reviewer Notes

The tests check every output element against a reference that follows
the kernel's split and tile order and its BF16 rounding, within an error
bound derived from that order, and against exact FP32 attention with a
2^-6 limit relative to the softmax-weighted |V|. Cases cover 1 to 2,048
rows, GQA groups of 1, 12 and 16, NHD and HND caches, rows with zero or
one valid entry, CUDA graph replay with new indices, and rejected
inputs. They pass on sm_80; sm_86, sm_89 and sm_90a are compiled and
checked for register spills (none). A follow-up vLLM PR routes QSA
layers with `kv_cache_dtype="nvfp4"` on SM80 through SM90 to this API.
The experimental CI lane does not pick up these tests on its own; they
run on H100 when a maintainer names the test path for the bot.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental sparse paged attention for NVFP4 key/value caches
on supported NVIDIA GPUs, with output gating and optional scaling.
* Added an example demonstrating cache preparation and operation
execution.
* **Documentation**
* Documented the API, supported hardware, tensor formats, and handling
of invalid or empty selections.
* **Tests**
* Added coverage for varied cache layouts, selection edge cases, CUDA
graph replay, and invalid inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [da54553](https://github.com/flashinfer-ai/flashinfer/commit/da54553e29e64ca256a94396a9e385f6a3fbb9f1)

- **作者**: eigen
- **时间**: 2026-10-21T22:55:02Z
- **提交信息**: deslop(cake_kimi_k3_moe): fold clone and per-arch kernel sources, share one launcher per launch shape (#6960)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of the Cake Kimi-K3 MoE code for SM100 /
SM103, tracked in #6668. It covers three experimental packages: the
latent MoE front / tail projections, the TP12 fused communication tail
and the fused router. Commit 1 drops two unused planner definitions and
an empty marker. Commits 2-6 fold the knob variants (early trigger, L2
evict-first hint, ring depth, accumulator capacity, cluster rows) and
three per-architecture kernel pairs onto one kept kernel source each.
Every former kernel symbol stays defined for its program. Commit 7 keeps
one host launcher per launch shape: nine of the 43 launchers that shared
a shape stay and serve all their records, and the other 34 are deleted.
In total, 48 files are deleted: 38 launchers, 9 kernel sources and one
empty marker. Kernel symbols, device code, launch parameters, the public
entry points and the tests do not change; the latent dispatch table
re-points five keys to the kept programs (see below).

Behaviour changes:
- **New module names for five latent keys.** `tail_norm:e1`,
`front:i6144e1`, `front:i768e1`, `tail_gemm:tp8e1f0t1` and
`tail_gemm:tp1e1f1s6t1` now route to the kept programs. They build under
new JIT module names, and their internal `Run` symbol lives in the kept
launcher's host-shim namespace. The kernel symbol inside, the exported
`run` entry, every argument and every launch parameter are the former
ones.
- **One rebuild on an existing JIT workspace.** Every record whose
kernel source or launcher changed rebuilds once under its unchanged
module name. These are the k23:c8 module, the three SM103 router
modules, the LC:8 module and the 43 shared-launcher modules (most
records are in several of these sets). The five re-pointed keys also
build once under their new names. A fresh workspace is not affected.
- **Host backtraces.** A failing host-side argument check reports the
shared launcher's file and line in its traceback, where it used to
report the former per-program launcher's. Message texts and exception
kinds do not change.
- **Nothing else.** No reachable input changes a launch, an argument, a
route, a kernel symbol, an export or a test result.

## Changes

Base: upstream main `8a93c9b83` (2026-10-21). Head:
`4f1f1410d9f8d4f82f2f4e4884e5d9b26ff9fa9f` (7 commits). 75 files, +1,210
/ -20,705 (0 added, 48 deleted, 27 modified).

- **Family.** This is the exporter-generated Kimi-K3 MoE code for SM100
(B200, compute capability 10.0) and SM103 (GB300, compute capability
10.3). It lives in three experimental packages:
- `flashinfer/experimental/kimi_k3_latent_moe`, the latent MoE front /
tail projections. It has 35 dispatch keys and 32 programs at the base
(28 at head), with one JIT module per (key, architecture), so 35 per
architecture.
- `flashinfer/experimental/kimi_k3_tp12_tail`, the TP12 fused
communication tail. It has 9 programs, and each one is a single module
built for both architectures.
- `flashinfer/experimental/kimi_k3_fused_router`, the fused router. It
has 14 programs, 11 per architecture, and each is built for the route
block alignments 8 and 16, so 22 modules per architecture.

Every program is a kernel source plus a host launcher (binding), and a
registry record in the package's `cake_jit.py` names both.
- **Unchanged.**
- The public entry points: `flashinfer.kimi_k3_latent_moe`,
`flashinfer.kimi_k3_tp12_tail` and
`flashinfer.fused_moe.kimi_k3_fused_router` /
`prepare_kimi_k3_fused_router`.
- The host planners, which are the `cake_backend.py` files of TP12 and
the router. The latent planner only loses two unused definitions.
- The loaders' Python logic, with one exception: the latent loader's
`kernel_defines(key)` now also merges the new `KERNEL_SYMBOLS` table
into the `CAKE_PROGRAM_KERNEL` definition. The module-name salt keeps
using the `SPECIALIZATIONS` constants only.
- The module name of every kept record, every kernel symbol and every
launch parameter.
- The router and TP12 dispatch tables. The latent `KERNELS` table
re-points the five keys above to the kept programs.
- The three test files, the benchmarks, the docs outside the packages,
`pyproject.toml` and the pre-commit configuration.
- **Fold form.** All folds use one spelling:
- The kept kernel source names its kernel through the compile definition
`CAKE_PROGRAM_KERNEL`, with its own symbol as the guarded default. A
program folded onto it compiles the same source with its former kernel
symbol defined, so every kernel symbol of the base stays defined for its
program. The SASS gate compares each former symbol with no symbol
mapping.
- The knob arms reproduce each former source's text byte for byte. The
folded program's arm comes first (`#if KNOB == <member value>`), the
kept text sits in `#else`, and an `#ifndef KNOB` default sets the kept
value. The knobs are `EARLY_TRIGGER`, `B_EVICT_FIRST`, `NUM_STAGES`,
`K23_CAPACITY` and `ROWS`.
- The per-architecture arms use `#if __CUDA_ARCH__ == 1000`, with the
SM100 text first.
- **Device code.** Every change is mechanical and preserves behaviour
for every input (see Validation):
- the gates compile both sides to identical SASS from the loaders' exact
compile definitions;
- the preprocessed kernel and launcher texts match after the declared
normalisation;
- every module builds and loads through its real loader on both trees
with the same kernel inside;
- the public entry points give bit-identical outputs over the tests'
shapes.
- **Generated files.** The PR edits 23 kept generated files: 20 CUDA
sources and the three registries. Each one replaces its exporter "do not
edit" banner with this one-line statement:
`Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The generated `csrc/README.md` files of the latent and TP12 packages
replace their "do not edit" sentence with a sentence that names the
hand-edited files. No untouched generated file changes.

### Commit 1 (9a1027044) - cake_kimi_k3_moe: drop two unused definitions
and an empty marker (2 files, +0 / -5)

- **Unused.** The latent planner `cake_backend.py` defined a helper
`tail_gemm_block_n` and a constant `TAIL_N_TILES` that nothing in the
repository reads. Whole-tree searches find only their definitions,
neither is in `__all__`, and no test, benchmark or README names them.
The router package also tracked a 0-byte `csrc/.gitkeep` next to 30
generated sources.
- **Deleted.** The five Python lines and the marker.
- **Consequence:** none. No kernel source, launcher, registry, compile
definition or launch argument changes. The latent test file and its 53
items (10 CPU-only, 43 GPU) are unchanged.

### Commit 2 (4d53850dd) - cake_kimi_k3_latent_moe: fold the e1 variants
into their base programs (14 files, +178 / -3,518)

- **Variants.** Three latent programs were copies of a sibling except
for one knob:
- `tail_norm:e1` puts the early-trigger block before the norm, not after
it;
- `front:i6144e1` / `front:i768e1` add the L2 evict-first cache hint to
the weight-tile TMA loads;
  - `tail_gemm:tp8e1f0t1` adds the same hint to its two weight loads.
- **Kept sources.** `tail_norm:e0`, `front:i6144` / `front:i768` and
`tail_gemm:tp8e0f0t1` now hold both texts behind `#if EARLY_TRIGGER ==
1` / `#if B_EVICT_FIRST == 1` arms (both default to 0) and name their
kernel through `CAKE_PROGRAM_KERNEL`. Their three launchers
(`tail_norm`, `front`, `tail_gemm` TP8) spell the kernel symbol through
the same definition in the declaration, the launch argument and the
launch-error message. All four former kernel symbols therefore stay.
- **Registry.** The four keys route to the kept programs through two
tables:
  - `SPECIALIZATIONS`, which holds the knob values;
- a new companion table `KERNEL_SYMBOLS`, which maps each key to its
former kernel symbol.

`kernel_defines(key)` gains four lines that merge `KERNEL_SYMBOLS` into
the key's compile definitions. The module-name salt is unchanged (the
`SPECIALIZATIONS` constants), so no other key's module name changes. The
records of the three folded programs and their sources (kernel +
launcher, 3,363 lines) are deleted.
- **Disclosed:**
- The four re-pointed keys build under new JIT module names: the kept
record's digest plus the knob. The former records' module names
disappear. The kernel inside keeps its former symbol. An existing JIT
workspace builds those four modules once per architecture.
- The host-side `Run` symbol of those keys now lives in the kept
launcher's namespace (`cake_host_shim_<kept id>::Run`). This is an
internal symbol. The exported entry `run` and every argument are
unchanged.
- The launch-error message text is unchanged. The kernel name is spelled
by stringizing the definition, which produces the same string.
  - No kernel body, launch parameter or accepted input changes.

### Commit 3 (e52ff421c) - cake_kimi_k3_latent_moe: fold the 6-stage
tail GEMM into the 7-stage one (5 files, +148 / -1,493)

- **Ring depth.** `tail_gemm:tp1e1f1s6t1` (TP1, up to 256 tokens)
differed from `tail_gemm:tp1e1f1t1` only in the depth of its TMA ring: 6
stages, not 7. Everything else that differed follows from the depth:
  - the derived shared-memory offsets;
  - the mbarrier addresses and their unrolled initialisation;
  - the TMEM slot;
  - the four ring-depth loop bounds.

That makes 24 differing regions, and every literal in them is an affine
function of the depth.
- **Kept source.** The 7-stage source names its kernel through
`CAKE_PROGRAM_KERNEL` and holds both texts behind `#if NUM_STAGES == 6`
arms (default 7). Its launcher reads the same definition by design and
selects the matching dynamic shared-memory size (230,528 / 197,760
bytes).
- **Registry.** The 6-stage key routes to the kept program with
`NUM_STAGES: 6` in `SPECIALIZATIONS` and an entry in `KERNEL_SYMBOLS`.
The folded program's two sources are deleted.
- **Consequence:** the same as commit 2, for this key: a new module
name, the former kernel symbol and the kept launcher's `Run` namespace.
The SASS of both symbols is compared on both architectures, because a
missed arm would compile and would not match. The gate makes this
comparison mandatory (see Validation).

### Commit 4 (0051119b6) - cake_kimi_k3_tp12_tail: fold the k23:c8
kernel source onto k23:c4 (4 files, +41 / -820)

- **Pair.** The two fused K23 programs differed only in two things:
- the accumulator capacity define `K23_CAPACITY` (4 / 8), which the body
reads at 28 sites;
- three derived shared-memory size defines (1,920 / 3,840 bytes), which
the body does not read.
- **One source.** The k23:c4 source is now the only source.
`K23_CAPACITY` and `CAKE_PROGRAM_KERNEL` get guarded defaults, and the
three derived defines sit in `#if K23_CAPACITY == 8` / `#else` arms. The
k23:c8 kernel source is deleted.
- **Record.** The k23:c8 record keeps its name, key, launch facts,
closure and (until commit 7) its own launcher. It compiles the shared
source with `K23_CAPACITY=8` and its own `CAKE_PROGRAM_KERNEL`, so both
kernel symbols, both module names and every launch parameter stay. The
registry's header comment and the sources README describe the hand-made
fold.
- **Consequence:** none for any input. The k23:c8 module rebuilds once
on an existing JIT workspace, because its sources and compile
definitions changed while its name did not.

### Commit 5 (559f7f224) - cake_kimi_k3_fused_router: merge the L, LP
and M per-arch kernel pairs (8 files, +150 / -1,893)

- **Pairs.** The router arms L, LP and M each shipped one kernel source
per architecture. The two sources of an arm differed only in:
- L and LP: schedule lines, namely the phase-2 prefix publish and the
warp-sum loops of the emit and owner passes (6 regions, 29 / 18 lines
each);
- M: the owner-scratch constants (256 rows on SM100, 2,048 on SM103; 11
constants).
- **Shared source.** Each pair now uses the SM100 source. The
architecture-specific lines sit behind `#if __CUDA_ARCH__ == 1000` /
`#else` arms. The kernel symbol is spelled through
`CAKE_PROGRAM_KERNEL`, with the SM100 symbol as its default. The SM103
record keeps its name, launch facts, kernel symbol and (until commit 7)
its launcher, and compiles the shared source with its own symbol
defined.
- **Deleted.** The three SM103 kernel sources (1,878 lines). The package
README's bullet on the shared sources is reworded: the L, LP and M arms
keep one program per architecture, and the LC arm keeps one source per
token count.
- **Consequence:** none for any input. The SASS gate compares every
(symbol, architecture, block alignment) of the six programs, which is 12
rows. The three SM103 modules rebuild once on an existing JIT workspace.

### Commit 6 (c868f8974) - cake_kimi_k3_fused_router: fold LC:8 kernel
source onto LC:4 via ROWS (4 files, +47 / -591)

- **Pair.** The four- and eight-token cluster programs (LC:4 / LC:8)
differed in six kernel lines:
  - the `ROWS` define;
  - two shared-memory layout defines;
  - the cluster dimension (`__cluster_dims__(4|8, 1, 1)`);
  - the two grid divisors derived from the cluster dimension.
- **Kept source.** The four-token source keeps those lines behind `#if
ROWS == 8` arms, with an `#ifndef ROWS` default of 4. It names its
kernel through `CAKE_PROGRAM_KERNEL`, whose default is the four-token
symbol. The eight-token kernel source is deleted.
- **Record.** The eight-token record keeps its name, key, launch
geometry, kernel symbol and (until commit 7) its launcher. Its compile
definitions carry `ROWS=8` and its symbol. The registry comment and the
README describe the shared source.
- **Consequence:** none for any input. The SASS gate compares each
symbol per architecture and block alignment, which is 8 rows. The LC:8
module rebuilds once on an existing workspace. This PR does not fold the
LC:2 / LC:16 pair (see **Not in this PR**).

### Commit 7 (4f1f1410d) - cake_kimi_k3_moe: share one host launcher per
launch shape (49 files, +721 / -12,460)

- **Launchers.** 43 host launchers across the three packages shared a
launch shape with other launchers. Within a shape they differed only in:
  - the kernel symbol they declare and launch;
  - the id of their host-shim namespace;
- one or two launch literals: dynamic shared memory, cluster size or the
TMA box extents.
- **Kept.** One launcher per shape is kept, nine files in all (latent 3,
router 3, TP12 3). Each takes those values from compile definitions:
`CAKE_PROGRAM_KERNEL`, `CAKE_PROGRAM_SHIM`, `CAKE_BINDING_SMEM`,
`CAKE_BINDING_CLUSTER`, `CAKE_BINDING_BOX_Z` and `CAKE_BINDING_N_PAD`.
Each definition has an `#error` guard, so a launcher cannot build
without its program's values. The cluster-size check keeps its literal
text per arm. The other 34 launchers (12,233 lines at the base) are
deleted.
- **Records.** Every record keeps its name, key, kernel symbol, launch
facts and module name. Its second source is now the shared launcher, and
its compile definitions carry its values. The tail GEMM keys take the
kernel symbol from `KERNEL_SYMBOLS`, which gains three entries (8 in
all). The two sources READMEs and the router README describe the
sharing. No Python logic or test changes.
- **Disclosed:**
- Every record keeps its own host-shim namespace, because the definition
carries the record's former id. Every internal
`cake_host_shim_<id>::Run` symbol is therefore unchanged. The exceptions
are the five re-pointed latent keys, which already moved to the kept
record's namespace in commits 2 / 3. Every exported `run` entry is
unchanged.
- A failing host-side argument check now reports the shared launcher's
file and a shifted line number in its traceback. Message texts and
exception kinds are unchanged.
- The 43 modules whose launcher changed rebuild once on an existing JIT
workspace, under their unchanged names. Fresh workspaces are not
affected.
- No kernel source changes in this commit. The inertness rows of the
host gate check that the kernel sources preprocess identically with and
without the new definitions (see Validation).

## Validation

The compile-only rows (device gate, host gate and kernel-source
inertness) are compiled on one node with one CUDA toolkit for both
architectures. Each row's result gives the toolkit version. The GPU rows
run on a B200 (SM100, compute capability 10.0, 148 SMs) and a GB300
(SM103, compute capability 10.3, 152 SMs).

- Device gate, 46 rows (every kernel this PR re-spells, per architecture
and, for the router, per block alignment: the 11 latent kernels of
commits 2 / 3 -- the kept and the folded program of each pair --, the
two TP12 K23 kernels of commit 4 from one fat build per side, the six
router L / LP / M kernels of commit 5 and the two LC kernels of commit
6; cubin + SASS + preprocessed text): all 46 rows identical. For every
row the SASS of the former kernel symbol matches between the base and
this branch with no symbol mapping, both sides carry exactly the
expected function set (46 of 46 rows), and the preprocessed device texts
match after dropping line markers and blank lines (46 identical, 0
differ; the two TP12 K23 rows come from one fat build per side). Both
sides were compiled on one node with one CUDA 13.4 toolkit (nvcc build
cuda_13.4.r13.4/compiler.38855100_0)
- **Rows.** Each row compares the former program's source at the base
with the kept source at head.
- **Compilation.** Both sides are compiled with the loader's exact
compile definitions and include order, from one staged path, in one
environment.
  - **Pass criteria.** A row passes when all of these hold:
    - the cubin sha256 is equal;
- the SASS is identical for the former kernel symbol, with no symbol
mapping;
    - resource usage is identical;
    - each side has exactly one kernel function;
- the preprocessed device texts are identical after dropping line
markers and blank lines.
- Host gate and kernel-source inertness, 138 + 104 rows (the launcher of
every (program, architecture[, block alignment]) the base shipped
against the launcher head builds for it under that record's compile
definitions -- 22 latent rows of commits 2 / 3, 12 rows showing the
untouched launchers of commits 4 / 5 / 6 preprocess identically with and
without the new definitions, 104 rows of commit 7; preprocessed text +
compiled host object -- and, per kernel source head compiles, its
preprocessed device text for its architecture with and without the
compile definitions commit 7 adds to its record): host gate 138 of 138
rows identical after the declared normalisation (12 flag-inertness rows,
12 + 10 fold-launcher rows of the kept and the folded latent keys, 26 +
78 shared-launcher rows; sm_100a 66 of 66, sm_103a 72 of 72; the
host-shim namespace id masked on the 14 rows of the re-pointed latent
keys); the check macros' file / line arguments matched the expected
count on all 138 rows (0 mismatched); every compiled host object pair
exports the same global symbol set (138 of 138). Kernel-source inertness
104 of 104 rows identical (52 per architecture) with no normalisation
beyond line markers and blank lines (raw-identical 104 of 104). One
node, the same CUDA 13.4 toolkit
- **Launcher rows (138).** The preprocessed texts must be identical
after the declared normalisation, which covers:
    - line markers and blank lines;
- the file / line arguments of the check macros, with the expected count
per launcher;
- the join of the stringized kernel name into the launch-error message;
- the host-shim namespace id, on the rows of the five re-pointed latent
keys only.

On both sides, the compiled host objects must export the same symbol set
(after the same namespace mask on those rows) and reference the same
undefined kernel symbol.
- **Inertness rows (104).** These must be identical, with no
normalisation beyond line markers and blank lines.
- Module build and load through the real loaders (per architecture: the
35 latent modules, one per dispatch key; the 9 TP12 modules; the 22
router modules, 11 programs x 2 block alignments; both trees, fresh JIT
workspaces): 66 modules per tree built and loaded through the real
loaders on each device (B200 and GB300; the test runs built 63 / 62 of
them and the module check the rest; the load-all lists are equal);
kernel sets identical for 66 of 66 modules; exported symbol sets
identical after the host-shim namespace mask for 66 of 66; the raw
export sets differ on exactly the five re-pointed latent keys (expected
5: their Run symbol lives in the kept record's namespace). Byte-equality
of the libraries is not claimed (host objects embed per-compile names)
- Each module must be built by its loader and must load with every entry
point callable.
- Each module's device kernel set must be exactly the former kernel
symbol. Its exported symbol set must be identical to the base-tree
module's after masking the host-shim namespace id. By design, the raw
sets differ on exactly the five re-pointed latent keys per architecture,
by their `Run` namespace.
- Bitwise before / after (torch.equal) on B200 and GB300: the latent
front over 8 token counts x TP 1 / 8 (16 cells: logits, latent, shared
activation), the latent tail over the same 16 cells plus the TP8
rank-slice, the two between-wave token counts and the 4 x 2 decode
partial-sum cells (27 cells: y and out), and the fused router over the
14 measured and 17 arbitrary token counts x block alignment 8 / 16 (62
cells: the eight route-plan tensors); seeded inputs built with the
tests' own helpers and shared by both trees: all 105 cells bit-identical
(torch.equal) on both devices: latent 43 of 43 and router 62 of 62 on
B200 (compute capability 10.0, 148 SMs) and on GB300 (compute capability
10.3, 152 SMs); 598 output tensors compared per device, 0 differing
- Tests on B200 and GB300 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: on B200 and on GB300, both trees:
latent 53 passed / 0 skipped / 0 failed of 53, TP12 7 passed of 7 (the
twelve-rank item deselected), router 83 passed of 83, with the same
counts on the base tree; with CUDA hidden, on both GPU nodes and on a
CPU node, both trees: latent 10 passed / 43 skipped, TP12 6 passed / 1
skipped, router 10 passed / 73 skipped, 0 failed everywhere
  - **The three files:**
    - `tests/experimental/test_cake_kimi_k3_latent_moe.py` (53 items);
- `tests/experimental/test_cake_kimi_k3_tp12_tail.py` (7 items, run with
`-k 'not twelve'`; the twelve-rank item is listed under **Not run**);
    - `tests/experimental/test_cake_kimi_k3_fused_router.py` (83 items).
- **Both trees.** The passed / skipped / failed counts and the skipped
ids must be identical on both trees.
- **CUDA hidden.** The three files run on both trees, with these
expected passed / skipped counts: latent 10 / 43, TP12 6 / 1, router 10
/ 73.
- CPU checks: all passed on a CPU node. pre-commit --all-files on both
full checkouts: rc 0, 16 hooks (15 passed, 1 skipped), identical
per-hook results, an empty patch on both; pre-commit on the 27 touched
files: 12 passed, 4 skipped, 0 failed, empty patch; ruff check and ruff
format clean on the 4 changed Python files with the repository config,
py_compile ok; the registries re-read at head: latent 28 records / 35
keys / 11 specializations / 8 kernel-symbol entries (base 32 / 35 / 10 /
none), TP12 9 records, router 14 records with 11 routes per
architecture; every strict launcher carries its #error guards and its
expected number of check sites; none of the 47 deleted .cu file names is
referenced at head; 27 touched files, 'do not edit' in none, the
statement in 23 of them; chain diff 75 files, +1,210 / -20,705,
name-status as recorded; the seven edits re-applied in order to a
snapshot of the base reproduce the branch byte for byte (replay rc 0)
and every unit tool equals its recorded result at its own state (42
rows, 0 differing); collection identical on both trees (latent 53 / 53,
TP12 8 / 8, router 83 / 83 ids, 0 differing); commit messages: 0 banned
words, trailer last on all 7, no line over 72 columns, equal to the
recorded copies
- pre-commit on both full checkouts, which must give identical per-hook
results and an empty patch, and on the 27 modified files.
- The registries are re-read: latent 28 records, 35 keys, 11
specializations and 8 kernel-symbol entries; TP12 9 records; router 14
records.
  - Every strict launcher carries its `#error` guards.
- No deleted kernel or launcher file name is referenced anywhere, and no
touched file contains "do not edit".
- Re-applying the seven edits to a snapshot of the base must reproduce
the branch byte for byte. The text proofs of every fold must equal their
recorded results. These proofs are preprocess-level renders against the
former sources, with negative controls.
  - Test collection must be identical on both trees.
  - Commit message checks.

**Not run.** By design, this PR's validation does not run the following.
Each item gives its proof of record.
- **`test_tail_matches_reference_on_twelve_ranks`** in
`tests/experimental/test_cake_kimi_k3_tp12_tail.py`.
- It needs a twelve-rank launch over three NVL72 compute trays, and it
skips everywhere else by its own condition.
- Other rows cover the kernels it would exercise: the device gate rows
of the K23 pair, the inertness rows of all nine TP12 kernel sources, the
module build / load of all nine programs and the file's single-GPU
compile test.
- **Benchmarks.** This is a mechanical PR with identical SASS per kernel
symbol, so there is nothing new to measure. None of the three benchmark
files is run.
- **H100 / SM90.** No kernel of the three packages serves SM90: the
loaders accept only compute capability 10.0 and 10.3. Nothing in this PR
executes there.

Experimental test scope for CI:

```experimental-tests
tests/experimental/test_cake_kimi_k3_latent_moe.py
tests/experimental/test_cake_kimi_k3_tp12_tail.py
tests/experimental/test_cake_kimi_k3_fused_router.py
```

## Not in this PR

- **The router's LC:2 / LC:16 cluster pair.** The same `ROWS` form
applies, but this pair also differs in `__launch_bounds__`, in a
route-words constant and in the non-portable-cluster attribute call of
the LC:16 launcher. The LC:16 record also owns the occupancy query. This
is for a second tranche, once this PR's LC:4 / LC:8 rows are in.
- **The exact-shape programs** `tail_gemm:tp8e0f0s9n128` (T == 512) and
the TP12 `k1_twoshot:grouped` and `k3_persist:grouped` (M == 256). By
design they are reachable at exactly those shapes. Removing them changes
which kernel runs, which is a performance trade, so they are left to an
owner / performance round.
- **The issue's assertion that `tail_gemm:tp8e0f0s9n128` is reached only
at T == 512.** This is a test addition and is not taken here, because
this PR leaves the three test files unchanged.
- **Kernel ABI and launcher items for the exporter.** These change the
kernel ABI (signature, argument plan, SASS parameter space) and host
behaviour, so they are exporter items:
- launcher regeneration beyond this PR's sharing (a compact launcher
with cached tensor maps and fewer argument checks per launch);
- the unused `tl` kernel argument (64 KiB per device, read by no kernel
body);
  - the `out_r` placeholder of the 13 tail decode kernels;
  - the dummy front-route arguments.
- **The 1,492 unused `#define` lines of the generated kernel sources.**
They are exporter-emitted layout metadata, and the next export would
overwrite a hand edit. This is an exporter item.
- **The 23 decode instances of the latent decode template** (23 x 1,196
lines), `QUALIFIED_SM_COUNTS = (148, 152)` and the compiled-in strides.
These are generator / product changes for the exporter and the owner.
- **The test-only helpers and the M arm's SM103 scratch.** This covers
the test-only helpers `front_grid`, `tail_gemm_num_stages` and
`tail_gemm_final_ts` (public in `__all__`) and
`cake_jit.registered_arches`. It also covers a 256-row owner scratch for
the M arm on SM103 (2,048 rows in this PR, as at the base). These are
API / behaviour changes with callers, so they are an owner call.
- **Packaging and formatting configuration.** This covers the
`pyproject.toml` package-data entries for the three `csrc/` trees, the
pre-commit exclude line and the two `.clang-format` stubs (both in
effect, kept). The owner keeps this configuration out of package PRs.
`pyproject.toml` is unchanged and names none of the three packages.
Their sources never shipped as wheel data, and the loaders read `csrc/`
from the checkout. Three other experimental packages have the same gap.
- **The stale `<arch>/` path in the latent `README.md`** (one line). It
is a documentation nit unrelated to the folds and is left as is.
- **Host-path items.** This covers the `kernel_declaration` / occupancy
rendering per record and every other host-path item of the issue: plan
caching, per-call overhead, identity checks and API kwargs. They change
behaviour or timing, so they belong in separate PRs.
- **Exporter requests**, which are requests rather than PR changes. They
are addressed to the exporter owners in the issue comment:
- emit knob-folded kernel sources through `SPECIALIZATIONS` / per-record
compile definitions, in the symbol-preserving `CAKE_PROGRAM_KERNEL`
form;
  - emit per-architecture arms for same-schedule pairs;
- emit one host launcher per launch shape with the `CAKE_PROGRAM_SHIM` /
`CAKE_BINDING_*` parametrisation, which also covers the issue's shared
TMA-encoder helper;
  - drop the disclosure line on regeneration;
  - prune the unused defines at the source;
  - emit the READMEs' "one pair per program" sentence from the registry.

Part of #6668

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c104d45](https://github.com/flashinfer-ai/flashinfer/commit/c104d45566f163682d2a6319bd94f8c0025505a5)

- **作者**: eigen
- **时间**: 2026-10-21T22:22:53Z
- **提交信息**: feat(cake_minimax_h3): E4M3 destination-major output for the MiniMax-H3 NVFP4 pre-attention (SM100 / SM103) (#6956)

`flashinfer.diffusion_ops.prepare_minimax_h3_nvfp4_pre_attention` /
`MiniMaxH3Nvfp4PreAttention` (module `cake_minimax_h3_nvfp4`) is the
public entry for the MiniMax-H3 NVFP4 pre-attention. It runs in two
launches. Stage 1 does RMSNorm, AdaLN and NVFP4 activation quantization.
Stage 2 is the fused QKV GEMM with Q/K RMSNorm, split-half RoPE and the
output epilogue. The fused GEMM has two output-format variants.
`out_format="nvfp4"` shipped before this PR and writes destination-major
NVFP4 codes and block scales. This PR adds `out_format="e4m3"`. It
writes a destination-major `float8_e4m3fn` tensor of shape `[P, M, 56/P,
3, 128]` using per-tensor `qkv_scales` that the caller provides. There
is one program per architecture: a 16-warp K=96 program on SM103 and an
eight-warp program on SM100. The default `out_format="nvfp4"` programs
and outputs are unchanged byte for byte. The baseline is the previously
shipped NVFP4 output mode followed by a separate streaming requantize
launch that produces the same E4M3 tensor. The speedup is min 1.172x and
geomean 1.177x on GB300, and min 1.125x and geomean 1.144x on GB200.
Latencies are medians in ms of the two-launch pre-attention span (stage
1 + fused QKV GEMM), measured with CUPTI on a cold L2. The baseline also
includes its requantize launch, and speedup is the baseline time divided
by the E4M3 mode time.

**NVIDIA GB300, `sm_103a`, driver 580.159.03, CUDA 13.0 runtime (torch
2.14.1+cu130), programs compiled with nvcc 13.4**

| Shape | E4M3 mode ms | NVFP4 mode ms | requantize ms | NVFP4 mode +
requantize ms | speedup |
|---|---|---|---|---|---|
| center_p1_4s_m33472 | 1.28637 | 1.29933 | 0.22467 | 1.52401 | 1.185 |
| center_p2_4s_m16736 | 0.64599 | 0.64527 | 0.11427 | 0.75954 | 1.176 |
| center_p4_4s_m8368 | 0.33123 | 0.33075 | 0.05946 | 0.39021 | 1.178 |
| center_p8_4s_m4184 | 0.18042 | 0.18000 | 0.03194 | 0.21194 | 1.175 |
| center_p1_5s_m38592 | 1.47914 | 1.48378 | 0.25840 | 1.74218 | 1.178 |
| center_p2_5s_m19296 | 0.73831 | 0.74151 | 0.13101 | 0.87252 | 1.182 |
| center_p4_5s_m9648 | 0.37299 | 0.37231 | 0.06784 | 0.44015 | 1.180 |
| center_p8_5s_m4824 | 0.19856 | 0.19802 | 0.03638 | 0.23440 | 1.181 |
| center_p1_6s_m48768 | 1.86730 | 1.86718 | 0.32509 | 2.19226 | 1.174 |
| center_p2_6s_m24384 | 0.92820 | 0.93085 | 0.16403 | 1.09489 | 1.180 |
| center_p4_6s_m12192 | 0.48394 | 0.48355 | 0.08464 | 0.56819 | 1.174 |
| center_p8_6s_m6096 | 0.24525 | 0.24451 | 0.04435 | 0.28887 | 1.178 |
| center_p1_8s_m58944 | 2.25566 | 2.25831 | 0.39187 | 2.65019 | 1.175 |
| center_p2_8s_m29472 | 1.11944 | 1.12072 | 0.19725 | 1.31797 | 1.177 |
| center_p4_8s_m14736 | 0.56743 | 0.56810 | 0.10115 | 0.66925 | 1.179 |
| center_p8_8s_m7368 | 0.28906 | 0.28832 | 0.05242 | 0.34074 | 1.179 |
| center_p1_10s_m74240 | 2.85140 | 2.85271 | 0.49213 | 3.34484 | 1.173 |
| center_p2_10s_m37120 | 1.43009 | 1.43376 | 0.24723 | 1.68100 | 1.175 |
| center_p4_10s_m18560 | 0.72282 | 0.72352 | 0.12586 | 0.84938 | 1.175 |
| center_p8_10s_m9280 | 0.36234 | 0.36186 | 0.06470 | 0.42656 | 1.177 |
| center_p1_15s_m109952 | 4.24242 | 4.26447 | 0.72650 | 4.99096 | 1.176
|
| center_p2_15s_m54976 | 2.10983 | 2.10878 | 0.36355 | 2.47233 | 1.172 |
| center_p4_15s_m27488 | 1.04013 | 1.04482 | 0.18429 | 1.22911 | 1.182 |
| center_p8_15s_m13744 | 0.53346 | 0.53251 | 0.09366 | 0.62618 | 1.174 |

**NVIDIA GB200, `sm_100a`, driver 580.126.20, CUDA 13.0 runtime (torch
2.14.1+cu130), programs compiled with nvcc 13.4**

| Shape | E4M3 mode ms | NVFP4 mode ms | requantize ms | NVFP4 mode +
requantize ms | speedup |
|---|---|---|---|---|---|
| center_p1_4s_m33472 | 1.67151 | 1.67773 | 0.23283 | 1.91057 | 1.143 |
| center_p2_4s_m16736 | 0.82112 | 0.82258 | 0.11846 | 0.94104 | 1.146 |
| center_p4_4s_m8368 | 0.41584 | 0.41683 | 0.06198 | 0.47882 | 1.151 |
| center_p8_4s_m4184 | 0.21994 | 0.22045 | 0.03334 | 0.25379 | 1.154 |
| center_p1_5s_m38592 | 1.91431 | 1.93169 | 0.26736 | 2.19905 | 1.149 |
| center_p2_5s_m19296 | 0.93111 | 0.94039 | 0.13589 | 1.07628 | 1.156 |
| center_p4_5s_m9648 | 0.48295 | 0.48259 | 0.07059 | 0.55319 | 1.145 |
| center_p8_5s_m4824 | 0.25024 | 0.25048 | 0.03795 | 0.28843 | 1.153 |
| center_p1_6s_m48768 | 2.48613 | 2.48647 | 0.33693 | 2.82340 | 1.136 |
| center_p2_6s_m24384 | 1.25500 | 1.25984 | 0.17024 | 1.43008 | 1.140 |
| center_p4_6s_m12192 | 0.61978 | 0.62519 | 0.08794 | 0.71312 | 1.151 |
| center_p8_6s_m6096 | 0.31379 | 0.30907 | 0.04627 | 0.35535 | 1.132 |
| center_p1_8s_m58944 | 2.97242 | 3.05156 | 0.40631 | 3.45787 | 1.163 |
| center_p2_8s_m29472 | 1.49063 | 1.51258 | 0.20439 | 1.71697 | 1.152 |
| center_p4_8s_m14736 | 0.73735 | 0.74067 | 0.10509 | 0.84576 | 1.147 |
| center_p8_8s_m7368 | 0.37306 | 0.37064 | 0.05466 | 0.42530 | 1.140 |
| center_p1_10s_m74240 | 3.85294 | 3.88624 | 0.50986 | 4.39609 | 1.141 |
| center_p2_10s_m37120 | 1.90077 | 1.88513 | 0.25629 | 2.14141 | 1.127 |
| center_p4_10s_m18560 | 0.93492 | 0.93765 | 0.13082 | 1.06847 | 1.143 |
| center_p8_10s_m9280 | 0.46435 | 0.46288 | 0.06739 | 0.53027 | 1.142 |
| center_p1_15s_m109952 | 5.60914 | 5.71368 | 0.75211 | 6.46579 | 1.153
|
| center_p2_15s_m54976 | 2.81418 | 2.83510 | 0.37683 | 3.21193 | 1.141 |
| center_p4_15s_m27488 | 1.39693 | 1.38071 | 0.19126 | 1.57197 | 1.125 |
| center_p8_15s_m13744 | 0.68203 | 0.67048 | 0.09734 | 0.76783 | 1.126 |

FlashInfer also ships the other Cake MiniMax-H3 pre-attention variants:
BF16 (SM103 #4690, SM100 #5137), MXFP8 (#5060), the NVFP4 W4A4
pre-attention that this PR extends (#5496), and a separate SM120
FP8/NVFP4 fused pre-attention module (#5493); this NVFP4 family and its
new E4M3 output mode ship on `sm_100a` (GB200 / B200) and `sm_103a`
(GB300 / B300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added E4M3 output support alongside NVFP4 for MiniMax-H3 pre-attention
operations.
- Added per-Q/K/V scaling for E4M3 outputs, including float8 results and
format-specific output shapes.
- Added support for additional CUDA architecture targeting, including
compute capability 12.0.
- Added generated ahead-of-time execution programs with improved input
validation and launch handling.

- **Bug Fixes**
- Improved validation for tensor formats, devices, dimensions, memory
layout, and launch parameters.
- Expanded coverage for numerical accuracy, saturation, repeated
execution, CUDA graphs, and invalid inputs.

- **Breaking Changes**
- Replaced legacy runtime routing and JIT-loading paths with generated
programs.
- Removed previously available pre-attention kernel variants and legacy
routing interfaces.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c952a5b](https://github.com/flashinfer-ai/flashinfer/commit/c952a5bcffde71768bdb1969116ee1fa5a8ecf99)

- **作者**: Vincent
- **时间**: 2026-10-21T22:19:38Z
- **提交信息**: feat(comm): MNNVL CuTe DSL fused BT all-reduce, dynamic FP8 output, and the mnnvl-cutedsl backend (#6603)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extends the MNNVL CuTe DSL all-reduce backend
(`flashinfer/comm/mnnvl_cutedsl*`) so it covers TP4 at hidden size 8192
end to end and can be selected through the unified all-reduce API.

**Kernels**
- **One-launch fused BT all-reduce** (`BTAllReduceTuning(fused=True)`,
`kernel_bt/device_kernels.py::_FusedAllReduceDeviceKernel`). A
persistent kernel replaces BT's three launches (publish, owner reduce,
materialize). Work is cut into tickets claimed in order from a per-call
counter: each ticket publishes a token slice to its owner, reduces an
owned slice `lag` rounds behind, broadcasts it, and materializes a token
(optional residual + RMSNorm + FP8 output) further behind. Payloads go
through shared memory and one `cp.async.bulk` copy per destination.
Readiness uses the existing negative-zero Lamport sentinels, so there is
no grid barrier; because every ticket, including a CTA's first, is
claimed from the counter, the call makes progress with as little as one
resident CTA per rank.
- **Dynamic per-token FP8 output** (patterns
`kARResidualRMSNormDynamicFP8Quant` and
`kARResidualRMSNormOutDynamicFP8Quant`) for LL, three-launch BT, fused
BT and HT, in a new shared `dynamic_fp8_epilogue.py`. Semantics follow
the TRT-LLM MNNVL `kDynamicFP8` epilogue (scale = max(amax / 448,
min-subnormal / 448) over the FP32 norm); quantization multiplies by a
per-token reciprocal, so results match TRT-LLM up to FP32 rounding.
- **LL small-message improvements**: an opt-in publish that splits each
token between the multicast store and per-CTA bulk copies to each peer,
and a new one-launch Lamport two-shot (`two_shot=True`). Bulk-copy
helpers are shared by LL and BT in `cute_dsl_primitives.py`.

**Routing**
- `StaticProfile` gains an optional `compute_capability`; `resolve()`
prefers an exact-architecture profile over an architecture-agnostic one
and never matches a different architecture. Existing profiles keep
`None` and behave as before.
- New TP4 / hidden 8192 / top_k 10 / bf16 profiles in `DEFAULT_CONFIG`
(AR + residual + RMSNorm, also used for static and dynamic FP8) and
`NO_NORM_CONFIG` (plain all-reduce), with separate route tables for
SM100-class GB300 (10.3) and SM107 (10.7), each measured on its
hardware.

**API**
- `create_allreduce_fusion_workspace(backend="mnnvl-cutedsl", ...)` with
keyword-only compile-time settings (`rms_eps`, `weight_bias`, `top_k`,
residual/norm flags, `output_dtype`, `dynamic_fp8`, ...). Other backends
reject these keywords; `backend="auto"` is unchanged and never selects
this backend.
- `allreduce_fusion(pattern=kAllReduce)` works on a CuTe workspace built
with `apply_rms_norm=False, add_residual=False`.
- `flashinfer.comm.is_mnnvl_cutedsl_supported(...)`: a non-raising local
support probe sharing the constructor's checks (callers must agree on
the result across ranks before constructing).
- `docs/api/comm.rst`: new "MNNVL CuTe DSL backend" section
(compile-time restrictions, the probe, plain all-reduce usage, residual
and concurrency requirements).

**Performance** (GB300, 4 GPUs, hidden 8192, bf16; CUDA graph of 20
back-to-back calls, median over 30 replays of the slowest rank; every
result checked against an FP32 reference; TRT-LLM MNNVL twoshot timed in
the same job), µs:

| Operation | Tokens | TRT-LLM MNNVL twoshot | MNNVL CuTe DSL (this PR)
|
|---|---|---|---|
| All-reduce | 64 | 6.97 | 6.83 |
| All-reduce | 2048 | 86.03 | 79.60 |
| All-reduce | 16384 | 659.77 | 585.07 |
| AR + residual + RMSNorm | 64 | 8.61 | 7.76 |
| AR + residual + RMSNorm | 2048 | 103.49 | 81.54 |
| AR + residual + RMSNorm | 16384 | 841.09 | 587.01 |
| AR + residual + RMSNorm + dynamic FP8 | 2048 | 109.13 | 84.92 |

The final review fixes (counter-claimed first tickets, per-route LL
two-shot mailboxes) were A/B'd against these numbers in the same job and
are equal or faster (0.95-1.003x). Known gaps on GB300: a few mid-size
ranges are 5-8% slower than TRT-LLM twoshot (plain all-reduce around
192-384 tokens, AR + RMSNorm around 160-256 tokens); no CuTe candidate
measured was faster there.

Shipped TP8 hidden-8192 profiles are unaffected: on two GB300 nodes (8
ranks) the numerical contract test passes and AR + RMSNorm / MoE
finalize performance is within 0.99-1.01x of `main`.

## 🔍 Related Issues

Part of #5325 (expand MNNVL CuTe DSL all-reduce profiles).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> Ran the hook versions directly on the changed files: ruff 0.12.8
(check + format) and mypy 1.17.1 are clean, and
`scripts/check_pr_api_diff.py` reports no findings. A full `pre-commit
run --all-files` is still pending.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New: `tests/comm/test_mnnvl_cutedsl_dynamic_fp8.py`,
`tests/comm/test_mnnvl_cutedsl_api.py` (host-side factory/probe checks),
`tests/comm/test_mnnvl_cutedsl_allreduce_api.py` (4 ranks through the
factory), plus fused-BT, LL two-shot and route-table cases in the
existing
`test_mnnvl_cutedsl_{no_rms_norm,numerical_contract,config,static_fp8}.py`,
including a test that launches the fused kernel with more CTAs than can
be resident. The two new multi-rank files are added to
`TORCHRUN_TEST_FILES`.

Passing at 4 ranks on GB300 and on SM107 hardware: every
`tests/comm/test_mnnvl_cutedsl_*.py` file and
`tests/comm/test_allreduce_unified_api.py` (`mpirun -np 4`, 161 passed).
On two GB300 nodes (8 ranks): `test_mnnvl_cutedsl_numerical_contract.py`
25 passed.

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

- The fused BT kernel (`kernel_bt/device_kernels.py`) is the largest and
most delicate piece: a persistent kernel that spins on peer data. Its
docstring argues deadlock freedom; the key properties are in-order
ticket claims, publish-before-wait, and bounded look-back. Two such
full-GPU spinning collectives must not run concurrently on different
streams (documented).
- All CuTe protocols other than the LL one-shot add only the owner's
residual, so `residual_in` must be identical on every rank (now stated
in the docs; it was already true for BT and HT).
- `BTAllReduceTuning` exposes only `fused` and `fused_lag`; bulk copies,
the ticket schedule and the early PDL trigger are always on in the fused
path.
- No public benchmark routine for this backend is added here; the
numbers above come from a standalone timing script using the method
described.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added the MNNVL CuTe DSL backend for fused and plain all-reduce,
residual addition, and RMS normalization.
* Added dynamic per-token FP8 output with optional scaling and norm
outputs.
* Added architecture-aware profile routing and support checks for
compatible configurations.
* **Documentation**
* Documented backend configuration, supported fusion patterns, routing
behavior, and workspace requirements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ce49ee0](https://github.com/flashinfer-ai/flashinfer/commit/ce49ee0645b1b1c21511b08ad2cd803838d75846)

- **作者**: eigen
- **时间**: 2026-10-21T22:18:47Z
- **提交信息**: refactor(cake_nvfp4_sparse_mla_decode): ship the NVFP4 sparse MLA decode programs as a self-contained package (#6933)

`flashinfer.mla.nvfp4_sparse_mla_decode` runs sparse MLA decode over an
NVFP4 (`nvfp4_ds_mla`) KV cache. It takes E4M3 queries `[T, 16, 576]`,
352-byte NVFP4 cache rows and int32 top-k row indices `[T, topk]` (-1 =
empty slot), and it writes BF16 output `[T, 16, 512]`. Each query token
gets one thread-block cluster of C CTAs (grid (T, C, 1), 448 threads per
CTA, 32-key stages, up to 2048 keys per CTA). The CTAs in a cluster
merge their fp32 partials through distributed shared memory, and C = 1
writes its output directly. The public API has two backends:
`backend="cuda"` is the hand-written kernel and `backend="cake"` runs
the generated programs. This PR delivers the Cake backend's seven
programs, one for each cluster size C in {1, 2, 3, 4, 5, 6, 8}, as a
build-manifest package, and the host planner picks C for each launch
from the device's live cluster capacity. The baseline is the previous
Cake version of the same seven programs as shipped before this PR,
measured on the same input shapes in the same interleaved runs. Against
it, the new build is about the same speed with a small overall gain:
speedups across the 96 timed rows range from 0.993 to 1.014, and the
geomean for each (arch, program) pair is between 1.0007 and 1.0087.

### Summary per (arch, program)

| arch | GPU | cluster | program | timed rows | geomean speedup | min |
max |
|---|---|---|---|---:|---:|---:|---:|
| sm_103a | GB300 | cluster 1 | b321ca1b7dfea243bca6 | 2 | 1.0034 |
1.0006 | 1.0062 |
| sm_103a | GB300 | cluster 2 | 9db88fc2ce17eaf2d27e | 4 | 1.0037 |
1.0026 | 1.0051 |
| sm_103a | GB300 | cluster 3 | 525c3da3db366af4b77c | 10 | 1.0043 |
1.0000 | 1.0061 |
| sm_103a | GB300 | cluster 4 | b5c9cbf01c57fe28ab5c | 10 | 1.0033 |
0.9974 | 1.0070 |
| sm_103a | GB300 | cluster 5 | 79fa77f600e1320149dd | 5 | 1.0038 |
1.0019 | 1.0058 |
| sm_103a | GB300 | cluster 6 | 5339f8b94959bd44e7f4 | 7 | 1.0025 |
0.9962 | 1.0056 |
| sm_103a | GB300 | cluster 8 | 79fc3ddfe4254b845585 | 10 | 1.0029 |
0.9963 | 1.0093 |
| sm_100a | GB200 | cluster 1 | b321ca1b7dfea243bca6 | 2 | 1.0087 |
1.0054 | 1.0121 |
| sm_100a | GB200 | cluster 2 | 9db88fc2ce17eaf2d27e | 4 | 1.0079 |
1.0063 | 1.0094 |
| sm_100a | GB200 | cluster 3 | 525c3da3db366af4b77c | 10 | 1.0044 |
1.0015 | 1.0069 |
| sm_100a | GB200 | cluster 4 | b5c9cbf01c57fe28ab5c | 10 | 1.0007 |
0.9948 | 1.0037 |
| sm_100a | GB200 | cluster 5 | 79fa77f600e1320149dd | 5 | 1.0038 |
1.0019 | 1.0054 |
| sm_100a | GB200 | cluster 6 | 5339f8b94959bd44e7f4 | 7 | 1.0011 |
0.9968 | 1.0043 |
| sm_100a | GB200 | cluster 8 | 79fc3ddfe4254b845585 | 10 | 1.0023 |
0.9927 | 1.0136 |

Row sets: P = production token counts T in {5, 10, ..., 45} x top-k in
{2048, 1024, 512}; W = the device's wave-boundary token counts; S =
suffix-padded top-k 2048; C = the forced coverage row (cluster 1);
kernel-test case = the kernel test suite's T=45, top-k 2048 case. Every
row uses the uniform64k index regime: each token's indices are a prefix
of a random permutation of a 65,536-row pool. The planner routes each
row to a program, so the programs have different row counts. Times are
the median GPU kernel time via CUPTI with cold L2, from 3 interleaved
groups x 128 iterations per arm.

### sm_103a — NVIDIA GB300

NVIDIA GB300 (compute capability 10.3, sm_103a), driver 580.167.08. Both
arms were JIT-compiled with nvcc 13.4.92 (CUDA 13.4) and run on CUDA
runtime 13.0 (torch 2.14.1+cu130).

#### cluster 1 — cake_nvfp4_sparse_mla_decode_b321ca1b7dfea243bca6

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| C-t8-k512-none-uniform64k-c1 | 8 | 512 | none | 15.616 | 15.520 |
1.006 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 53.185 | 53.152 |
1.001 |

#### cluster 2 — cake_nvfp4_sparse_mla_decode_9db88fc2ce17eaf2d27e

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| W-t47-k2048-none-uniform64k | 47 | 2048 | none | 31.232 | 31.136 |
1.003 |
| W-t64-k2048-none-uniform64k | 64 | 2048 | none | 31.584 | 31.456 |
1.004 |
| W-t128-k2048-none-uniform64k | 128 | 2048 | none | 61.216 | 61.056 |
1.003 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 31.264 | 31.104 |
1.005 |

#### cluster 3 — cake_nvfp4_sparse_mla_decode_525c3da3db366af4b77c

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t40-k2048-none-uniform64k | 40 | 2048 | none | 23.664 | 23.520 |
1.006 |
| P-t45-k2048-none-uniform64k | 45 | 2048 | none | 23.744 | 23.616 |
1.005 |
| P-t40-k1024-none-uniform64k | 40 | 1024 | none | 14.816 | 14.752 |
1.004 |
| P-t45-k1024-none-uniform64k | 45 | 1024 | none | 14.992 | 14.912 |
1.005 |
| P-t40-k512-none-uniform64k | 40 | 512 | none | 10.816 | 10.816 | 1.000
|
| P-t45-k512-none-uniform64k | 45 | 512 | none | 10.944 | 10.912 | 1.003
|
| W-t37-k2048-none-uniform64k | 37 | 2048 | none | 23.552 | 23.456 |
1.004 |
| W-t46-k2048-none-uniform64k | 46 | 2048 | none | 23.776 | 23.680 |
1.004 |
| S-t45-k2048-suffix-uniform64k | 45 | 2048 | suffix | 23.744 | 23.616 |
1.005 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 23.745 | 23.617 |
1.005 |

#### cluster 4 — cake_nvfp4_sparse_mla_decode_b5c9cbf01c57fe28ab5c

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t30-k2048-none-uniform64k | 30 | 2048 | none | 18.816 | 18.768 |
1.003 |
| P-t35-k2048-none-uniform64k | 35 | 2048 | none | 19.008 | 18.881 |
1.007 |
| P-t30-k1024-none-uniform64k | 30 | 1024 | none | 12.352 | 12.384 |
0.997 |
| P-t35-k1024-none-uniform64k | 35 | 1024 | none | 12.544 | 12.576 |
0.997 |
| P-t25-k512-none-uniform64k | 25 | 512 | none | 9.024 | 8.992 | 1.004 |
| P-t30-k512-none-uniform64k | 30 | 512 | none | 9.248 | 9.184 | 1.007 |
| P-t35-k512-none-uniform64k | 35 | 512 | none | 9.344 | 9.296 | 1.005 |
| W-t29-k2048-none-uniform64k | 29 | 2048 | none | 18.784 | 18.720 |
1.003 |
| W-t36-k2048-none-uniform64k | 36 | 2048 | none | 19.040 | 18.944 |
1.005 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 35.744 | 35.569 |
1.005 |

#### cluster 5 — cake_nvfp4_sparse_mla_decode_79fa77f600e1320149dd

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t25-k2048-none-uniform64k | 25 | 2048 | none | 16.448 | 16.416 |
1.002 |
| P-t25-k1024-none-uniform64k | 25 | 1024 | none | 11.648 | 11.616 |
1.003 |
| W-t24-k2048-none-uniform64k | 24 | 2048 | none | 16.448 | 16.352 |
1.006 |
| W-t28-k2048-none-uniform64k | 28 | 2048 | none | 16.625 | 16.544 |
1.005 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 31.281 | 31.168 |
1.004 |

#### cluster 6 — cake_nvfp4_sparse_mla_decode_5339f8b94959bd44e7f4

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t20-k2048-none-uniform64k | 20 | 2048 | none | 14.880 | 14.848 |
1.002 |
| P-t20-k1024-none-uniform64k | 20 | 1024 | none | 10.848 | 10.816 |
1.003 |
| P-t20-k512-none-uniform64k | 20 | 512 | none | 8.320 | 8.352 | 0.996 |
| W-t16-k2048-none-uniform64k | 16 | 2048 | none | 14.656 | 14.624 |
1.002 |
| W-t23-k2048-none-uniform64k | 23 | 2048 | none | 15.040 | 14.976 |
1.004 |
| S-t20-k2048-suffix-uniform64k | 20 | 2048 | suffix | 14.816 | 14.752 |
1.004 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 28.512 | 28.352 |
1.006 |

#### cluster 8 — cake_nvfp4_sparse_mla_decode_79fc3ddfe4254b845585

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t5-k2048-none-uniform64k | 5 | 2048 | none | 11.744 | 11.680 | 1.005
|
| P-t10-k2048-none-uniform64k | 10 | 2048 | none | 12.064 | 12.000 |
1.005 |
| P-t15-k2048-none-uniform64k | 15 | 2048 | none | 12.512 | 12.480 |
1.003 |
| P-t5-k1024-none-uniform64k | 5 | 1024 | none | 8.544 | 8.576 | 0.996 |
| P-t10-k1024-none-uniform64k | 10 | 1024 | none | 8.928 | 8.928 | 1.000
|
| P-t15-k1024-none-uniform64k | 15 | 1024 | none | 9.313 | 9.312 | 1.000
|
| P-t5-k512-none-uniform64k | 5 | 512 | none | 6.944 | 6.880 | 1.009 |
| P-t10-k512-none-uniform64k | 10 | 512 | none | 7.168 | 7.136 | 1.004 |
| P-t15-k512-none-uniform64k | 15 | 512 | none | 7.488 | 7.488 | 1.000 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 34.736 | 34.560 |
1.005 |

### sm_100a — NVIDIA GB200

NVIDIA GB200 (compute capability 10.0, sm_100a), driver 595.84.01. Both
arms were JIT-compiled with nvcc 13.4.92 (CUDA 13.4) and run on CUDA
runtime 13.0 (torch 2.14.1+cu130).

#### cluster 1 — cake_nvfp4_sparse_mla_decode_b321ca1b7dfea243bca6

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| C-t8-k512-none-uniform64k-c1 | 8 | 512 | none | 16.064 | 15.872 |
1.012 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 53.793 | 53.504 |
1.005 |

#### cluster 2 — cake_nvfp4_sparse_mla_decode_9db88fc2ce17eaf2d27e

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| W-t47-k2048-none-uniform64k | 47 | 2048 | none | 30.464 | 30.272 |
1.006 |
| W-t64-k2048-none-uniform64k | 64 | 2048 | none | 31.008 | 30.720 |
1.009 |
| W-t128-k2048-none-uniform64k | 128 | 2048 | none | 59.488 | 59.040 |
1.008 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 30.464 | 30.208 |
1.008 |

#### cluster 3 — cake_nvfp4_sparse_mla_decode_525c3da3db366af4b77c

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t40-k2048-none-uniform64k | 40 | 2048 | none | 23.280 | 23.136 |
1.006 |
| P-t45-k2048-none-uniform64k | 45 | 2048 | none | 23.552 | 23.392 |
1.007 |
| P-t40-k1024-none-uniform64k | 40 | 1024 | none | 14.784 | 14.752 |
1.002 |
| P-t45-k1024-none-uniform64k | 45 | 1024 | none | 14.944 | 14.880 |
1.004 |
| P-t40-k512-none-uniform64k | 40 | 512 | none | 10.800 | 10.784 | 1.001
|
| P-t45-k512-none-uniform64k | 45 | 512 | none | 10.944 | 10.912 | 1.003
|
| W-t37-k2048-none-uniform64k | 37 | 2048 | none | 23.136 | 23.088 |
1.002 |
| W-t46-k2048-none-uniform64k | 46 | 2048 | none | 23.537 | 23.424 |
1.005 |
| S-t45-k2048-suffix-uniform64k | 45 | 2048 | suffix | 23.488 | 23.328 |
1.007 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 23.552 | 23.408 |
1.006 |

#### cluster 4 — cake_nvfp4_sparse_mla_decode_b5c9cbf01c57fe28ab5c

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t30-k2048-none-uniform64k | 30 | 2048 | none | 19.425 | 19.392 |
1.002 |
| P-t35-k2048-none-uniform64k | 35 | 2048 | none | 19.680 | 19.648 |
1.002 |
| P-t30-k1024-none-uniform64k | 30 | 1024 | none | 12.768 | 12.736 |
1.003 |
| P-t35-k1024-none-uniform64k | 35 | 1024 | none | 12.976 | 12.928 |
1.004 |
| P-t25-k512-none-uniform64k | 25 | 512 | none | 9.184 | 9.232 | 0.995 |
| P-t30-k512-none-uniform64k | 30 | 512 | none | 9.408 | 9.440 | 0.997 |
| P-t35-k512-none-uniform64k | 35 | 512 | none | 9.568 | 9.568 | 1.000 |
| W-t29-k2048-none-uniform64k | 29 | 2048 | none | 19.360 | 19.328 |
1.002 |
| W-t36-k2048-none-uniform64k | 36 | 2048 | none | 19.760 | 19.712 |
1.002 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 36.512 | 36.448 |
1.002 |

#### cluster 5 — cake_nvfp4_sparse_mla_decode_79fa77f600e1320149dd

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t25-k2048-none-uniform64k | 25 | 2048 | none | 16.960 | 16.881 |
1.005 |
| P-t25-k1024-none-uniform64k | 25 | 1024 | none | 11.904 | 11.840 |
1.005 |
| W-t24-k2048-none-uniform64k | 24 | 2048 | none | 16.864 | 16.800 |
1.004 |
| W-t28-k2048-none-uniform64k | 28 | 2048 | none | 17.152 | 17.120 |
1.002 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 31.904 | 31.808 |
1.003 |

#### cluster 6 — cake_nvfp4_sparse_mla_decode_5339f8b94959bd44e7f4

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t20-k2048-none-uniform64k | 20 | 2048 | none | 15.264 | 15.264 |
1.000 |
| P-t20-k1024-none-uniform64k | 20 | 1024 | none | 11.152 | 11.104 |
1.004 |
| P-t20-k512-none-uniform64k | 20 | 512 | none | 8.481 | 8.480 | 1.000 |
| W-t16-k2048-none-uniform64k | 16 | 2048 | none | 15.040 | 15.088 |
0.997 |
| W-t23-k2048-none-uniform64k | 23 | 2048 | none | 15.488 | 15.424 |
1.004 |
| S-t20-k2048-suffix-uniform64k | 20 | 2048 | suffix | 15.232 | 15.217 |
1.001 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 29.057 | 29.008 |
1.002 |

#### cluster 8 — cake_nvfp4_sparse_mla_decode_79fc3ddfe4254b845585

| row label | T | top-k (K) | padding | previous (µs) | new (µs) |
speedup (previous/new) |
|---|---:|---:|---|---:|---:|---:|
| P-t5-k2048-none-uniform64k | 5 | 2048 | none | 12.064 | 11.984 | 1.007
|
| P-t10-k2048-none-uniform64k | 10 | 2048 | none | 12.480 | 12.448 |
1.003 |
| P-t15-k2048-none-uniform64k | 15 | 2048 | none | 12.928 | 12.896 |
1.002 |
| P-t5-k1024-none-uniform64k | 5 | 1024 | none | 8.768 | 8.832 | 0.993 |
| P-t10-k1024-none-uniform64k | 10 | 1024 | none | 9.216 | 9.200 | 1.002
|
| P-t15-k1024-none-uniform64k | 15 | 1024 | none | 9.600 | 9.553 | 1.005
|
| P-t5-k512-none-uniform64k | 5 | 512 | none | 7.136 | 7.040 | 1.014 |
| P-t10-k512-none-uniform64k | 10 | 512 | none | 7.392 | 7.424 | 0.996 |
| P-t15-k512-none-uniform64k | 15 | 512 | none | 7.744 | 7.744 | 1.000 |
| kernel-test case (T=45, K=2048) | 45 | 2048 | none | 35.408 | 35.328 |
1.002 |

Cake ships no other data type, layout or fused form of this decode
kernel: the seven cluster-size programs above are its variants, and the
family ships on `sm_100a` (B200/GB200) and `sm_103a` (B300/GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added packaged NVFP4 sparse MLA decode programs for SM 100a and SM
103a GPUs.
  * Added automatic selection by device architecture and cluster size.
* Added validation for CUDA versions, device compatibility, tensor
inputs, launch parameters, and packaged artifacts.
* Added JIT fallback when compatible prebuilt programs are unavailable.
  * Added support for CUDA Toolkit 12.8 and newer.

* **Documentation**
* Updated guidance on generated package layouts, validation, and device
availability.

* **Tests**
* Expanded coverage for device mapping, launch planning, manifest
integrity, and program selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cd6c188](https://github.com/flashinfer-ai/flashinfer/commit/cd6c1885a897c95a3728aae6eb7a2d14ca88aa16)

- **作者**: Zhong Zheng
- **时间**: 2026-10-21T21:07:10Z
- **提交信息**: fix(cake_mega_moe): [SM120] MegaMoE register spill with CUDA 13.3 headers; compile-check every EP (#6770)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes #6755: with CUDA 13.3, the SM120 Cake MegaMoE
(`sm120_mxfp4_mxfp8_bf16_cake`) device instances spilled one register at
DeepSeek-V4.1-Flash / DeepSeek-V3 EP8, and `_build_workspace` refused to
load them.

The description has two parts. **Part A** is the fix for #6755 and the
checks that keep it fixed. **Part B** is related changes that ride
along, each with a one-line reason. Every commit stands alone, so Part B
can be split out if reviewers prefer. In total: 11 commits, 21 files,
+1177 / -261, of which about 600 lines are regenerated kernel source.

### Part A — fix for #6755

**Root cause.** From CUDA 13.2 on, the libcu++ (CCCL) headers add an
automatic-storage test to every `cuda::atomic_ref` operation on a
generic pointer: an `isspacep.local` check plus a local-memory fallback.
The 13.0 / 13.1 headers compile it out
(`_LIBCUDACXX_ATOMIC_UNSAFE_AUTOMATIC_STORAGE`).
- NCCL's Device API uses `cuda::atomic_ref` for its GIN proxy queues,
signals and counters. With the fallback, the persistent kernel needs
about 10 more registers.
- With 13.3, the instances at the 168-register cap then spill.
- In the issue I attributed this to ptxas. That was wrong: 13.0's PTX
assembled by 13.3's ptxas is spill-free.

**Commits**

| commit | change | why |
|---|---|---|
| 5d574e46 | The generated source defines
`_CCCL_ATOMIC_UNSAFE_AUTOMATIC_STORAGE` before `nccl_device.h`. | The
fix. NCCL's atomics only address NCCL-owned device / host-pinned memory,
never automatic storage. |
| 0b092cf9 | `validate_init` compile-checks the candidate instances at
every EP size. Spill errors name the instance, REG / stack / local
bytes, the nvcc release and the validated releases. | Previously the
check was skipped up to 16 ranks, so a toolkit-dependent spill surfaced
only at the first `warmup()`. |
| e2fa91f7 | The macro is also passed on the `nvcc` command line. A host
test compiles one `cuda::atomic_ref` op with the active toolkit and
fails if the device flags no longer remove the check. | The macro is
internal to libcu++: a rename, or an earlier libcu++ include, would
otherwise reintroduce the spill silently. The test skips on 13.0 / 13.1,
whose headers have no such check. |

Cubins are byte-identical with and without the extra flag, on 13.0.88
and 13.3.73. The source macro is unused on 13.0 / 13.1: under 13.0.88,
5d574e46 is SASS- and cubin-identical to the merged source (64 / 64
instances checked).

**Before / after** (offline compile, sm_120a). Shapes: the shipped test
geometries plus V4.1-Flash, both variants, every copier count the tables
select. That gives 352 instances at EP 4 / 8 / 16 and 128 at EP 32.
Spilling instances with nvcc 13.3.73:

| source | EP 4 / 8 / 16 | EP 32 |
|---|---|---|
| before the fix (7647aea6, kernel source as merged in #6346) | 34 / 352
| — |
| + 5d574e46 (macro) | 0 / 352 | 1 / 128 (fixed in Part B, 5be8dc06) |
| HEAD, each GIN backend | 0 / 352 | 0 / 128 |

### Part B — related changes

| commit | change | why |
|---|---|---|
| 5be8dc06 | `m128` instances issue one MMA K step per main-loop
iteration; above 16 ranks the task builder keeps its per-source tables
in the `tb_pub` workspace instead of register arrays. | After Part A,
CUDA 13.1 still spilled 9 / 352 instances and 13.4 spilled 80 / 352,
because `m128` ran at the 168-register cap. EP 32 spilled with 13.2 /
13.3. The EP 8 four-step unroll gained < 1 % on 13.0 (A/B below); `m64`
keeps it. |
| 5ce94130 | Device modules are built for the session's NCCL GIN backend
only (`NCCL_GIN_{PROXY,GDAKI,GPI}_ENABLE`). Module names carry the
backend; AOT packages each. `validate_init` checks all three. | Every
GIN call otherwise inlines all three backends behind a runtime switch,
which costs 10-20 registers. The proxy / GDAKI builds also lose the GPI
fence's 8 B stack frame. Most of the diff is the regenerated `part007`.
|
| 338a2b49 | The native session registry is never destroyed at exit.
`TransportSession.close()` only marks a session closed once its process
group is gone. | The #6755 reproduction calls
`dist.destroy_process_group()` with the layer alive. Once the workspace
loaded, every rank crashed at exit deregistering windows of the freed
communicator. Pre-existing, but it is the next thing the reporter hits.
|
| 1946c4cd | Open #6346 review comments: `max_rows` cap 32640 (signed
32-bit `active_rows`), `probe_round` rejects `chunk_bytes` outside [1,
2^32), lazy AOT import, benchmark warmup ≤ capacity. | Leftovers from
the #6346 review. The fifth comment (GIN agreement across ranks) was
already handled before the merge. |
| 48812ad1, 0b95fc2d, 7647aea6 | Module unload on workspace destroy and
in a failed build; smem opt-in under the launch lock; argument-width
range check; `tune.py --shared-expert` guard; runbook note. | Post-merge
hardening of #6346, small and self-contained. |
| 15818d81 (+ benchmark shape in e2fa91f7) | `v41flash` (E384 / H5120 /
I2304 / top-k 6, both variants) in the multi-GPU test matrix and the
benchmark. | The #6755 geometry was not covered. |

**Compile matrix at HEAD.** 11 CUDA 13 releases (13.0.48, 13.0.88,
13.1.80, 13.1.115, 13.2.51, 13.2.78, 13.2.86, 13.3.33, 13.3.73, 13.4.59,
13.4.92) × 3 GIN backends × 480 instances (EP 4 / 8 / 16 / 32): **no
spills**. Every instance uses 130-168 registers and 0 B of local memory;
the stack is 0 B for proxy / GDAKI and 8 B for GPI.

For comparison, after Part A alone the EP 4 / 8 / 16 / 32 spill counts
per release were:

| | 13.0.x | 13.1.x | 13.2.x | 13.3.x | 13.4.x |
|---|---|---|---|---|---|
| EP 4 / 8 / 16 | 0 | 9 | 0 | 0 | 80 |
| EP 32 | 0 | 0 | 1 | 1 | 0 |

The same HEAD matrix was also run through the FlashInfer JIT loader with
13.0.88 and 13.4.92: 1440 instances each, none spilling. The README
lists all eleven releases as checked; 13.0.88 and 13.3.73 were also run
on GPUs (see Tests).

**Performance of Part B** (5be8dc06 + 5ce94130 change the generated
code). GPU A/B against the Part A tree, CUDA 13.0.88, 110-SM sm_120a
GPUs. Shapes: DeepSeek-V4-Flash and DeepSeek-V3 (EP 16: V4-Flash only),
noshared and fp8shared, 512-8192 tokens per rank. Rounds alternate the
order of the two trees. Mean kernel-time change (new vs old):

| EP | transport table | rounds | mean | range |
|---|---|---|---|---|
| 4 | all GIN | 2 | -0.74 % | -3.3 … +2.0 % |
| 4 | LSA where reachable | 4 | -0.28 % | -2.6 … +1.2 % |
| 8 | all GIN | 2 | -0.33 % | -2.5 … +1.1 % |
| 8 | LSA where reachable | 4 | +0.80 % | -4.0 … +8.0 % |
| 16 (2 hosts) | all GIN | 4 | +0.01 % | -0.4 … +0.8 % |
| 16 (2 hosts) | LSA where reachable | 4 | -0.26 % | -2.1 … +1.2 % |

- The +8 % point (EP 8, LSA where reachable, DeepSeek-V3 noshared, 2048
tokens) is session drift of about ±4 %. A three-way rotation at that
point (old / new / new with all backends compiled in, 200 iterations, 4
rounds) measured new -3.0 % and all-backends -3.3 %.
- The `m128` unroll change alone measured EP 8 all GIN -0.04 % and LSA
where reachable -0.65 %.

**Toolkit note.** Code built by releases after 13.0 runs slower, with or
without spills, and the amount depends on shape and GPU:
- 110-SM GPUs, EP 8, DeepSeek-V4-Flash, 13.1-13.4: 5-15 % slower at
512-1024 tokens per rank, 0-3 % at 4096.
- 188-SM GPUs, EP 4, 13.3.73: DeepSeek-V4-Flash and V4.1-Flash 10-15 %
slower at 1024-4096 tokens per rank; DeepSeek-V3 on par.

The README recommends 13.0 for the device build.

## 🔍 Related Issues

Fixes #6755.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The repository's pinned hooks were run on the changed files: ruff 0.12.8
(check + format) and mypy 1.17.1, all clean. The generated sources are
excluded from clang-format.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/moe_ep/test_sm120_w4a8_cake_host.py`: 42 passed, 1 skipped with
13.0.88. The skip is the libcu++ check test, which passes with 13.2.86,
13.3.73 and 13.4.92.

Hosts with 8 sm_120a GPUs (110 SMs) each over PCIe, NCCL 2.30.7, GDAKI
build:

| nvcc | run | result |
|---|---|---|
| 13.0.88 | EP 8: real-weight fixture (bit-exact),
`test_moe_ep_sm120_w4a8_cake_mega.py` (11 cases incl.
`v41flash:noshared` / `v41flash:fp8shared`), `_tables`, `_eplb` | 2 /
176 / 2 / 2 passed on every rank |
| 13.0.88 | EP 4: same four suites | 2 / 176 / 2 / 2 passed on every
rank |
| 13.0.88 | EP 16 (two hosts): mega, tables, eplb | 176 / 2 / 2 passed
on every rank |
| 13.3.73 | EP 8: mega `-k v41flash` | 32 passed |
| 13.3.73 | EP 8: the #6755 reproduction, `all_gin` and
`lsa_where_reachable` | warmup OK, rc 0 (`all_lsa` needs a load/store
path across the PCIe switches, which these hosts lack) |
| 13.0.88 | EP 8: teardown with `layer.destroy()` before / after /
without `destroy_process_group()` | rc 0 on every rank in all three
(before 338a2b49 the last crashed every rank) |

An independent run on a second host with 8 sm_120a GPUs (188 SMs) at
5ce94130, EP 8:
- with 13.3.73: the `v41flash` cases passed 32 / 32 with each of
`all_lsa`, `lsa_where_reachable` and `all_gin`, and the full `mega`
suite passed;
- with 13.0.88: the full `mega` suite passed.

The other toolkits, the proxy / GPI builds and EP 32 were checked by
compilation only.

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

- `validate_init` runs before the transport session exists, so it
compile-checks all three GIN backends. On a cold JIT cache, construction
pays the `nvcc` time of the candidate flavor(s) × 3 backends; the builds
run in parallel and are cached. The workspace loads only its own
backend, and AOT packages three device modules per parameter set and
flavor.
- An unknown `ncclGinType_t` (a future NCCL backend) raises at workspace
creation instead of loading a build without it.
- Not addressed here, both pre-existing: the transport probe's `auto`
choice (scored per transport in isolation), and first-launch / slow-NIC
behaviour on other PCIe topologies. I'll follow up on these separately.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
  - Added support for the DeepSeek-V4.1-Flash model geometry.
- Added compatibility for multiple communication backends and CUDA
toolkit detection.
- Improved diagnostics for resource usage, memory spills, and workspace
validation.

- **Bug Fixes**
  - Prevented warmup workloads from exceeding configured capacity.
  - Improved cleanup when distributed process groups are already closed.
  - Added safer handling when local tooling is unavailable.

- **Documentation**
- Updated runtime requirements, capacity limits, supported
configurations, and validation procedures.

- **Validation**
- Added broader coverage for model sizes, backend compatibility,
resource limits, and session cleanup.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Zhong Zheng <zhongz@nvidia.com>
Co-authored-by: Yingyi Huang <yingyihuang2000@outlook.com>

### [067b369](https://github.com/flashinfer-ai/flashinfer/commit/067b36956da21f9cb6cfbdad9fd6326c52fa3655)

- **作者**: eigen
- **时间**: 2026-10-21T20:17:48Z
- **提交信息**: perf(cake_comm): per-architecture programs and a permuted pass-1 sum of squares for the NVFP4-transport all-reduce + RMSNorm (SM100 / SM103 / SM107) (#6954)

The NVFP4-transport tensor-parallel all-reduce in
`flashinfer.comm.cake_fp4_allreduce` has ten variants:

- TP2 one-shot all-reduce, with BF16 input and with pre-quantized NVFP4
input.
- TP4 two-shot all-reduce, with BF16 input and with NVFP4 input.
- Six TP2 all-reduces fused with residual add + Gemma RMSNorm. These
take BF16 or NVFP4 input and produce BF16, NVFP4 or MXFP8 output.

Before this PR, one program of each TP2 variant served all three
architectures. With this PR, the family ships one program per
architecture wherever a build form measured faster on that architecture.
The registry now holds 37 programs, 20 per architecture; 22 program
names are new and 16 are retired.

This PR changes:

- the TP2 one-shot all-reduce with BF16 input on `sm_103a` and
`sm_107a`;
- five of the six fused variants on `sm_100a` and `sm_103a` (all except
NVFP4 -> BF16);
- all six fused variants on `sm_107a`.

The baseline is the previous Cake version of these kernels, as shipped
in FlashInfer by PR #6875 (the programs this PR replaces). Against it,
the geometric-mean speedup (previous / this PR) over the five shapes
(1K, 2K, 4K, 8K and 16K rows x 6144) is:

- `sm_100a`: fused BF16 -> BF16 1.0320, BF16 -> NVFP4 1.0566, BF16 ->
MXFP8 1.0499, NVFP4 -> NVFP4 1.0718, NVFP4 -> MXFP8 1.0657.
- `sm_103a`: one-shot BF16 1.0336; fused BF16 -> BF16 1.0300, BF16 ->
NVFP4 1.0552 (chained across two sessions), BF16 -> MXFP8 1.0502
(chained across two sessions), NVFP4 -> NVFP4 1.0718, NVFP4 -> MXFP8
1.0644.
- `sm_107a`: one-shot BF16 1.0121; fused BF16 -> BF16 1.0323, BF16 ->
NVFP4 1.0346, BF16 -> MXFP8 1.0321, NVFP4 -> BF16 1.0258, NVFP4 -> NVFP4
1.0256, NVFP4 -> MXFP8 1.0271.

The changed programs use these new forms, named by program-name suffix:

- `_rso` (TP2 one-shot, BF16 input, `sm_103a`): the decode reads the
peer packet's per-row scale word in flight during its first sweep over
the packet's data. Before, a separate poll read it and completed before
the sweep began.
- `_rst` (TP2 one-shot, BF16 input, `sm_107a`): the in-kernel reset of
the consumed Lamport slot uses ordinary per-thread stores instead of a
bulk store.
- `_qp` (fused, BF16 input with NVFP4 or MXFP8 output, `sm_100a` and
`sm_103a`): the quantizing pass 2 uses packed two-wide arithmetic
instead of the scalar FP32 quantization tree. `sm_107a` does not use
`_qp`, because packed quantization was not faster there.
- `_sop` (fused; on `sm_100a` and `sm_103a` every fused variant except
NVFP4 -> BF16, on `sm_107a` all six): pass 1 sums each row's squares in
the lane's loaded chunk order instead of the row's natural order. The
two orders are two FP32 roundings of the same sum. Combined with `_qp`,
the name is `_qp_sop`.

Each fused program has a `_pf` twin (residual prefetch) that the host
selects at 4K rows. The 4K row of every fused table below was run by
that twin.

Latencies are GPU time per call in microseconds (lower is better),
measured with CUPTI under CUDA-graph replay (10 calls per graph, 200
replays, interleaved ABBA pairs), with the previous Cake version and
this PR's version interleaved on the same GPUs in the same session,
world size 2 on 2 GPUs of one node.

### `sm_100a`: NVIDIA B200 (HGX node; 2 GPUs for world size 2), CUDA
13.4

**TP2 all-reduce + residual add + Gemma RMSNorm (fused)**

| Shape (rows x 6144) | Input -> Output | Previous Cake us | This PR us
| Speedup (previous / this PR) |
|---|---|---:|---:|---:|
| 1K x 6144 | BF16 -> BF16 | 18.30 | 17.80 | 1.0281 |
| 2K x 6144 | BF16 -> BF16 | 29.88 | 29.21 | 1.0229 |
| 4K x 6144 | BF16 -> BF16 | 51.46 | 50.33 | 1.0225 |
| 8K x 6144 | BF16 -> BF16 | 92.76 | 89.04 | 1.0418 |
| 16K x 6144 | BF16 -> BF16 | 175.21 | 167.71 | 1.0447 |
| 1K x 6144 | BF16 -> NVFP4 | 20.13 | 19.36 | 1.0398 |
| 2K x 6144 | BF16 -> NVFP4 | 31.74 | 30.30 | 1.0475 |
| 4K x 6144 | BF16 -> NVFP4 | 53.06 | 50.47 | 1.0513 |
| 8K x 6144 | BF16 -> NVFP4 | 101.09 | 94.19 | 1.0733 |
| 16K x 6144 | BF16 -> NVFP4 | 192.07 | 179.27 | 1.0714 |
| 1K x 6144 | BF16 -> MXFP8 | 19.83 | 19.10 | 1.0382 |
| 2K x 6144 | BF16 -> MXFP8 | 31.03 | 30.01 | 1.0340 |
| 4K x 6144 | BF16 -> MXFP8 | 52.86 | 50.70 | 1.0426 |
| 8K x 6144 | BF16 -> MXFP8 | 100.59 | 94.37 | 1.0659 |
| 16K x 6144 | BF16 -> MXFP8 | 190.38 | 178.01 | 1.0695 |
| 1K x 6144 | NVFP4 -> NVFP4 | 18.33 | 17.77 | 1.0315 |
| 2K x 6144 | NVFP4 -> NVFP4 | 30.90 | 28.56 | 1.0819 |
| 4K x 6144 | NVFP4 -> NVFP4 | 49.15 | 45.23 | 1.0867 |
| 8K x 6144 | NVFP4 -> NVFP4 | 77.36 | 70.70 | 1.0942 |
| 16K x 6144 | NVFP4 -> NVFP4 | 140.27 | 131.60 | 1.0659 |
| 1K x 6144 | NVFP4 -> MXFP8 | 18.07 | 17.70 | 1.0209 |
| 2K x 6144 | NVFP4 -> MXFP8 | 31.35 | 28.98 | 1.0818 |
| 4K x 6144 | NVFP4 -> MXFP8 | 48.63 | 45.04 | 1.0797 |
| 8K x 6144 | NVFP4 -> MXFP8 | 77.63 | 71.07 | 1.0923 |
| 16K x 6144 | NVFP4 -> MXFP8 | 140.18 | 132.84 | 1.0553 |

### `sm_103a`: NVIDIA GB300 (NVL72 node; 2 GPUs for world size 2), CUDA
13.4

**TP2 one-shot all-reduce, BF16 input**

| Shape (rows x 6144) | Previous Cake us | This PR us | Speedup
(previous / this PR) |
|---|---:|---:|---:|
| 1K x 6144 | 12.99 | 12.04 | 1.0789 |
| 2K x 6144 | 18.72 | 18.28 | 1.0241 |
| 4K x 6144 | 32.15 | 32.14 | 1.0003 |
| 8K x 6144 | 57.02 | 55.29 | 1.0313 |
| 16K x 6144 | 103.30 | 99.81 | 1.0350 |

**TP2 all-reduce + residual add + Gemma RMSNorm (fused)**

| Shape (rows x 6144) | Input -> Output | Previous Cake us | This PR us
| Speedup (previous / this PR) |
|---|---|---:|---:|---:|
| 1K x 6144 | BF16 -> BF16 | 17.57 | 17.12 | 1.0263 |
| 2K x 6144 | BF16 -> BF16 | 29.47 | 28.79 | 1.0236 |
| 4K x 6144 | BF16 -> BF16 | 50.02 | 48.89 | 1.0231 |
| 8K x 6144 | BF16 -> BF16 | 88.27 | 85.16 | 1.0365 |
| 16K x 6144 | BF16 -> BF16 | 163.19 | 156.80 | 1.0408 |
| 1K x 6144 | NVFP4 -> NVFP4 | 17.29 | 16.71 | 1.0347 |
| 2K x 6144 | NVFP4 -> NVFP4 | 29.27 | 27.26 | 1.0737 |
| 4K x 6144 | NVFP4 -> NVFP4 | 47.36 | 43.75 | 1.0825 |
| 8K x 6144 | NVFP4 -> NVFP4 | 73.63 | 67.48 | 1.0911 |
| 16K x 6144 | NVFP4 -> NVFP4 | 133.32 | 123.68 | 1.0779 |
| 1K x 6144 | NVFP4 -> MXFP8 | 16.92 | 16.59 | 1.0199 |
| 2K x 6144 | NVFP4 -> MXFP8 | 29.54 | 27.31 | 1.0817 |
| 4K x 6144 | NVFP4 -> MXFP8 | 46.45 | 43.31 | 1.0725 |
| 8K x 6144 | NVFP4 -> MXFP8 | 73.26 | 67.78 | 1.0808 |
| 16K x 6144 | NVFP4 -> MXFP8 | 134.07 | 125.49 | 1.0684 |

**Fused BF16 -> NVFP4 and BF16 -> MXFP8, chained across two sessions.**
The two BF16-input quantizing fused variants (BF16 -> NVFP4, BF16 ->
MXFP8) were never measured end to end in one session. This table shows
both legs:

- Session 1: the previous Cake version vs an intermediate form.
- Session 2: the intermediate form vs this PR's program, on another node
of the same type.

The speedup is the product of the two same-session ratios. The
intermediate forms, `tp2_rmsnorm_bf16_nvfp4_qp` and
`tp2_rmsnorm_bf16_mxfp8_qp` (`_qp` without `_sop`), were never shipped.

| Shape (rows x 6144) | Input -> Output | Previous Cake us (session 1) |
Intermediate form us (session 1) | Intermediate form us (session 2) |
This PR us (session 2) | Speedup = (prev/inter, session 1) x (inter/this
PR, session 2) |
|---|---|---:|---:|---:|---:|---:|
| 1K x 6144 | BF16 -> NVFP4 | 19.37 | 19.16 | 19.21 | 18.64 | 1.0419 |
| 2K x 6144 | BF16 -> NVFP4 | 31.60 | 31.30 | 31.67 | 30.74 | 1.0401 |
| 4K x 6144 | BF16 -> NVFP4 | 52.49 | 51.98 | 52.11 | 49.92 | 1.0541 |
| 8K x 6144 | BF16 -> NVFP4 | 94.92 | 93.98 | 94.44 | 89.12 | 1.0703 |
| 16K x 6144 | BF16 -> NVFP4 | 176.54 | 174.73 | 175.14 | 165.37 |
1.0701 |
| 1K x 6144 | BF16 -> MXFP8 | 19.36 | 19.16 | 19.14 | 18.55 | 1.0426 |
| 2K x 6144 | BF16 -> MXFP8 | 30.83 | 30.67 | 30.85 | 29.82 | 1.0399 |
| 4K x 6144 | BF16 -> MXFP8 | 51.21 | 50.97 | 51.32 | 49.28 | 1.0463 |
| 8K x 6144 | BF16 -> MXFP8 | 93.45 | 92.98 | 93.08 | 88.19 | 1.0608 |
| 16K x 6144 | BF16 -> MXFP8 | 174.38 | 173.53 | 173.01 | 163.79 |
1.0615 |

### `sm_107a`: SM107 (2 GPUs for world size 2), CUDA 13.5

**TP2 one-shot all-reduce, BF16 input**

| Shape (rows x 6144) | Previous Cake us | This PR us | Speedup
(previous / this PR) |
|---|---:|---:|---:|
| 1K x 6144 | 9.73 | 9.65 | 1.0083 |
| 2K x 6144 | 13.83 | 13.69 | 1.0102 |
| 4K x 6144 | 20.36 | 20.14 | 1.0109 |
| 8K x 6144 | 34.42 | 33.63 | 1.0235 |
| 16K x 6144 | 60.00 | 59.54 | 1.0077 |

**TP2 all-reduce + residual add + Gemma RMSNorm (fused)**

| Shape (rows x 6144) | Input -> Output | Previous Cake us | This PR us
| Speedup (previous / this PR) |
|---|---|---:|---:|---:|
| 1K x 6144 | BF16 -> BF16 | 14.92 | 14.48 | 1.0304 |
| 2K x 6144 | BF16 -> BF16 | 19.40 | 18.99 | 1.0216 |
| 4K x 6144 | BF16 -> BF16 | 32.86 | 32.16 | 1.0218 |
| 8K x 6144 | BF16 -> BF16 | 56.09 | 53.80 | 1.0426 |
| 16K x 6144 | BF16 -> BF16 | 102.64 | 98.20 | 1.0452 |
| 1K x 6144 | BF16 -> NVFP4 | 15.98 | 15.63 | 1.0224 |
| 2K x 6144 | BF16 -> NVFP4 | 20.59 | 20.14 | 1.0223 |
| 4K x 6144 | BF16 -> NVFP4 | 34.59 | 33.77 | 1.0243 |
| 8K x 6144 | BF16 -> NVFP4 | 60.18 | 57.25 | 1.0512 |
| 16K x 6144 | BF16 -> NVFP4 | 110.52 | 104.94 | 1.0532 |
| 1K x 6144 | BF16 -> MXFP8 | 15.75 | 15.42 | 1.0214 |
| 2K x 6144 | BF16 -> MXFP8 | 20.63 | 20.22 | 1.0203 |
| 4K x 6144 | BF16 -> MXFP8 | 34.47 | 33.71 | 1.0225 |
| 8K x 6144 | BF16 -> MXFP8 | 59.24 | 56.57 | 1.0472 |
| 16K x 6144 | BF16 -> MXFP8 | 108.86 | 103.73 | 1.0495 |
| 1K x 6144 | NVFP4 -> BF16 | 12.64 | 12.27 | 1.0302 |
| 2K x 6144 | NVFP4 -> BF16 | 20.12 | 19.51 | 1.0313 |
| 4K x 6144 | NVFP4 -> BF16 | 31.42 | 30.48 | 1.0308 |
| 8K x 6144 | NVFP4 -> BF16 | 48.63 | 47.71 | 1.0193 |
| 16K x 6144 | NVFP4 -> BF16 | 86.24 | 84.77 | 1.0173 |
| 1K x 6144 | NVFP4 -> NVFP4 | 14.02 | 13.65 | 1.0271 |
| 2K x 6144 | NVFP4 -> NVFP4 | 21.76 | 21.20 | 1.0264 |
| 4K x 6144 | NVFP4 -> NVFP4 | 32.76 | 32.00 | 1.0237 |
| 8K x 6144 | NVFP4 -> NVFP4 | 50.27 | 49.06 | 1.0247 |
| 16K x 6144 | NVFP4 -> NVFP4 | 87.56 | 85.34 | 1.0260 |
| 1K x 6144 | NVFP4 -> MXFP8 | 13.90 | 13.53 | 1.0273 |
| 2K x 6144 | NVFP4 -> MXFP8 | 21.56 | 20.96 | 1.0286 |
| 4K x 6144 | NVFP4 -> MXFP8 | 32.52 | 31.61 | 1.0288 |
| 8K x 6144 | NVFP4 -> MXFP8 | 50.18 | 48.98 | 1.0245 |
| 16K x 6144 | NVFP4 -> MXFP8 | 88.86 | 86.58 | 1.0263 |

Programs whose schedule is unchanged by this PR (the TP2 one-shot with
NVFP4 input on all three architectures, every TP4 two-shot program on
all three, and the fused NVFP4 -> BF16 program on `sm_100a` and
`sm_103a`) have their generated sources regenerated by the generator
with the same arithmetic and are not re-measured side by side in this
PR; the family ships on `sm_100a`, `sm_103a` and `sm_107a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added support for additional FP4 all-reduce and fused RMSNorm
execution variants, including BF16, NVFP4, and MXFP8 quantization paths.
- Added configurable natural and permuted sum-of-squares ordering for
fused normalization.
- Added launch-time validation and clearer runtime reporting for invalid
configurations and CUDA failures.

- **Tests**
- Expanded coverage across GPU targets, quantization modes, polling,
stream ordering, and reference accuracy.

- **Documentation**
- Clarified how available execution variants are selected and
registered.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ddba2f4](https://github.com/flashinfer-ai/flashinfer/commit/ddba2f4b2c2b8f6852a565774bc31c2ace39a5c7)

- **作者**: eigen
- **时间**: 2026-10-21T19:22:04Z
- **提交信息**: feat(cake_minimax_h3): opt-in NVFP4-QK / FP8-PV packed-varlen attention for MiniMax-H3 SM120 (#6936)

`flashinfer.diffusion_ops.minimax_h3_sm120_varlen_attention_nvfp4(...,
pv_mode="fp4")` is the public SM120 NVFP4 entry for MiniMax-H3
packed-varlen attention. This PR adds the opt-in `pv_mode="fp8"` variant
(called "hybrid" below). It uses NVFP4 Q/K and FP8 P·V in three
launches. The default `pv_mode="fp4"` is unchanged byte for byte. The
baseline is the previously delivered FP8 operator
`minimax_h3_sm120_varlen_attention_fp8`. The hybrid is faster than that
operator on every gated row. On RTX 5090 the speedup is min 1.3632x and
geomean 1.3814x. On RTX PRO 6000 Blackwell Server Edition it is min
1.1806x and geomean 1.1876x. The min and geomean cover two sessions per
GPU, and the tables show session 1. The variant exists for accuracy. On
the gated rows, its rel-L2 against the FP32 oracle is 0.136-0.143,
compared with 0.186-0.193 for the default route. The default route is
still faster, as the default / hybrid column shows.

Latencies are whole-operator medians in ms (BF16 in to BF16 out,
including quantization) of the packed-varlen attention. Shapes are the
production center / tail / padding token counts at P=1.

**NVIDIA GeForce RTX 5090, `sm_120a`, driver 620.62, CUDA 13.0 toolkit
for the JIT, nvcc 13.0.88**

| Shape | hybrid ms | FP8 operator ms | speedup vs FP8 operator |
default `pv_mode="fp4"` ms | default / hybrid |
|---|---|---|---|---|---|
| center_4s_p1_m33472 | 55.1978 | 75.2480 | 1.3632 | 41.6412 | 0.7544 |
| tail_5s_p1_m38531 | 73.0696 | 100.1189 | 1.3702 | 55.3445 | 0.7574 |
| center_5s_p1_m38592 | 73.0156 | 100.6726 | 1.3788 | 55.7971 | 0.7642 |
| tail_5s_p1_m38629 | 73.0198 | 100.7391 | 1.3796 | 56.2832 | 0.7708 |
| center_6s_p1_m48768 | 115.2190 | 159.2777 | 1.3824 | 89.2569 | 0.7747
|
| center_8s_p1_m58944 | 167.2685 | 231.9048 | 1.3864 | 129.6428 | 0.7751
|
| center_10s_p1_m74240 | 263.8216 | 365.4598 | 1.3853 | 203.6492 |
0.7719 |
| center_15s_p1_m109952 | 573.6273 | 796.9718 | 1.3894 | 441.8644 |
0.7703 |
| pad_15s_p1_used109901_total109952 | 573.9956 | 797.1831 | 1.3888 |
441.0108 | 0.7683 |

**NVIDIA RTX PRO 6000 Blackwell Server Edition, `sm_120a`, driver
595.84.01, CUDA 13.0 toolkit for the JIT, nvcc 13.0.88**

| Shape | hybrid ms | FP8 operator ms | speedup vs FP8 operator |
default `pv_mode="fp4"` ms | default / hybrid |
|---|---|---|---|---|---|
| center_4s_p1_m33472 | 40.2044 | 47.7775 | 1.1884 | 37.3651 | 0.9294 |
| tail_5s_p1_m38531 | 53.9199 | 64.0017 | 1.1870 | 49.8555 | 0.9246 |
| center_5s_p1_m38592 | 54.0714 | 64.0569 | 1.1847 | 49.8878 | 0.9226 |
| tail_5s_p1_m38629 | 54.2219 | 64.0224 | 1.1807 | 49.8444 | 0.9193 |
| center_6s_p1_m48768 | 85.2030 | 100.7248 | 1.1822 | 78.9925 | 0.9271 |
| center_8s_p1_m58944 | 123.8312 | 147.2781 | 1.1893 | 114.6144 | 0.9256
|
| center_10s_p1_m74240 | 195.3989 | 232.0127 | 1.1874 | 179.7568 |
0.9199 |
| center_15s_p1_m109952 | 424.0433 | 505.4736 | 1.1920 | 390.3084 |
0.9204 |
| pad_15s_p1_used109901_total109952 | 421.9906 | 505.4639 | 1.1978 |
390.0197 | 0.9242 |

FlashInfer also ships the other Cake SM120 variants of this operator
(`minimax_h3_sm120_varlen_attention_fp8`,
`minimax_h3_sm120_varlen_attention_nvfp4` with `pv_mode="fp4"`, and
`minimax_h3_sm120_varlen_attention_nvfp4_nodelta`); this hybrid family
ships on `sm_120a` only, while the BF16 / FP8 MiniMax-H3 attention
family covers `sm_100a` / `sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an opt-in FP8 value path for SM120 NVFP4 variable-length
attention, while retaining FP4 as the default.
* Added runtime mode selection, validation, workspace sizing,
scheduling, and launch support.
* Added generated SM120a attention programs and CUDA execution support.
  * Added benchmark output identifying the selected processing mode.

* **Tests**
* Expanded coverage for FP4 and FP8 modes, routing, accuracy, workspace
sizing, invalid inputs, and concurrent streams.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [da1e9f4](https://github.com/flashinfer-ai/flashinfer/commit/da1e9f4bc29629724cc4de618085938743beb65a)

- **作者**: eigen
- **时间**: 2026-10-21T19:21:20Z
- **提交信息**: perf(cake_xqa): faster SM110 XQA tree and decode routes as a vendorable cake-build package (#6945)

The SM110 XQA family has two kernels. The D512 speculative-decode (tree)
attention has two tcgen05 schedules, "tmem" and "pair", and
`kernel="auto"` selects between them. It is instantiated per cache
precision (FP16 / E4M3), cache layout (contiguous / page128) and GQA
ratio (2 / 4 / 8 / 16). The D128 FP16 single-token decode has three
programs that differ by KV partition count. This PR delivers all 43
programs as a self-contained package, with faster routes for every
variant. The public entry points `flashinfer.sm110_xqa.prepare` and
`attention` are unchanged. The table compares representative shapes
against the previous Cake package on FlashInfer main (9c68e44f).

Latency on NVIDIA Jetson AGX Thor (sm_110a, 20 SMs) with CUDA 13.4.
Values are kernel time in µs with the L2 cache flushed before every
launch, as the median over at least three processes, on two units (A /
B). Speedup = baseline / this PR, so a value above 1 means faster. Tree
rows use batch 1, 20 draft tokens, 32 query heads, 4 KV heads, capacity
256 and a causal tree mask.

| Shape | Baseline µs (A / B) | This PR µs (A / B) | Speedup (A / B) |
|---|---:|---:|---:|
| D512 tree, FP16 KV, contiguous | 19.552 / 19.376 | 17.376 / 17.376 |
1.125 / 1.115 |
| D512 tree, FP16 KV, paged (page 128) | 18.672 / 18.672 | 17.360 /
17.472 | 1.076 / 1.069 |
| D512 tree, FP8 (E4M3) KV, contiguous | 17.408 / 17.184 | 16.192 /
16.128 | 1.075 / 1.065 |
| D512 tree, FP8 (E4M3) KV, paged (page 128) | 17.440 / 17.472 | 16.064
/ 16.000 | 1.086 / 1.092 |
| D128 decode, FP16, batch 1, capacity 1024 | 17.584 / 17.824 | 11.616 /
11.584 | 1.514 / 1.539 |
| D128 decode, FP16, batch 2, capacity 512 | 17.440 / 17.760 | 11.968 /
12.096 | 1.457 / 1.468 |
| D128 decode, FP16, batch 4, capacity 256 | 15.968 / 16.416 | 11.520 /
11.488 | 1.386 / 1.429 |

The other Cake variants of this family, such as the other GQA ratios of
the tree kernel, are also in this PR but not in the table, and the
family ships on sm_110a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added Cake-packaged SM110 XQA support with automatic schedule
selection.
- Added `tmem` and `pair` tree schedules, plus `tcgen05` support for
D128 decode.
- Added launch-grid visibility and stronger input, alignment, workspace,
and partition validation.
- Added prebuilt-library loading with JIT fallback and CUDA
compatibility checks.

- **Bug Fixes**
- Unsupported benchmark schedules are now reported as unsupported rows
instead of stopping execution.

- **Documentation**
- Expanded usage, routing, workspace, validation, and benchmark coverage
documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d438333](https://github.com/flashinfer-ai/flashinfer/commit/d4383335bae57d307edfcb58dce07bc78af2dece)

- **作者**: Aurelien Chartier
- **时间**: 2026-10-21T18:58:07Z
- **提交信息**: feat: integrate TRTLLM-Gen sliding-window FMHA (#4905)

## 📌 Description

Integrates the TRTLLM-Gen sliding-window FMHA metadata and runtime
contract into
FlashInfer.

This change:

- adds fixed left/right window propagation for the direct TRTLLM-Gen
context API;
- adds per-query-token inclusive `VariableWindow` start/end bounds;
- updates paged and ragged launcher parameter plumbing and trace
schemas;
- selects and hashes the new mask metadata while preserving the existing
causal fast path when a
  configured left window covers the complete KV sequence;
- centralizes C++ validation for causal, non-causal, fixed-window,
variable-window,
  and chunked-attention combinations;
- preserves compatibility with generated metadata headers that spell the
FP16-softmax/Spcompress slots either semantically or as
`mReserved1/mReserved2`;
- adds Python validation and regression coverage for unsupported or
malformed
  configurations; and
- preserves existing dense, causal, MLA-generation, and
chunked-attention behavior.

The public wrapper continues to reject non-causal sliding-window
attention for
the TRTLLM-Gen paged backend. The direct context API supports explicit
two-sided non-causal windows. `VariableWindow` requires an inclusive
start/end
pair for every packed query token.

### Artifact dependency

The ABI-matched FMHA artifact has been promoted to FlashInfer's public
kernel
repository and is pinned atomically with the host ABI changes in this
PR.

- TRTLLM-Gen producer revision:
`e047937e3225e0ab26bd4a3ac1de771db3852441`
- Public artifact path:
  `35cb99413a3ebce2e87a03fc04196e528e22c8d5/fmha/trtllm-gen/`
- Public `checksums.txt` SHA-256:
  `d7cfe9b3cd53bf197641d0ad0a04450130958206544604a17c3c6745095d851e`
- Rollback artifact path:
  `2d6a5a029eefcc388ec0ceb87efb55d8bcce5c3c/fmha/trtllm-gen/`
- Rollback manifest SHA-256:
  `d79b5c51fc8597fac57dae0da4afa114fb2014575e4ec3df099ad856d97cabc3`

The promoted manifest contains 36,964 FMHA CUBINs, including 1,424
`VariableWindow` CUBINs across SM100a, SM103a, and SM107a. Its generated
metadata header has SHA-256
`bbcb4aaac5127fd2ae6dadc02c2eafd8b6419b60c39bb4fae2c20c54cb298179`.
That promoted header declares the semantic `mFp16Softmax` and
`mUsesSpcompress` fields, so the legacy `mReserved1/mReserved2` adapter
is not
exercised by the pinned artifact. The adapter remains for older
supported
generated headers, and an explicit compile-time diagnostic now rejects a
header that provides neither spelling instead of failing through opaque
overload resolution.

## Backwards compatibility

- `trtllm_ragged_attention_deepseek` now raises for a non-causal request
with
`window_left >= 0`; the old behavior silently ignored the requested
window.
- `BatchPrefillWithPagedKVCacheWrapper` rejects an unsupported
TRTLLM-Gen
non-causal sliding window during `plan()` instead of deferring the
exception
  until `run()`.
- `window_right` remains after `backend` in the direct context function
signature to avoid shifting the positional meaning of existing
arguments.

## 🔍 Related Issues

- TRTLLM-Gen producer change: sliding-window, two-sided-window, and
  VariableWindow FMHA export support
- Follow-up tracker to be opened: version/standardize the public
TRTLLM-Gen
  FMHA metadata fields currently exposed as either
  `mFp16Softmax/mUsesSpcompress` or `mReserved1/mReserved2`

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Pre-commit is installed and configured.
- [x] Clang-format, mypy, Ruff, whitespace, and merge-conflict hooks
pass on
      every modified file.

## 🧪 Tests

- [x] Tests were added for fixed and variable windows, supported
dtype/layout
combinations, input validation, wrapper/dispatch rejection behavior, and
      run-closure argument forwarding.
- [x] TRTLLM-Gen producer VariableWindow CTests: 27/27 on B200/SM100 and
27/27
      on B300/SM103.
- [x] ABI-matched candidate FlashInfer correctness suite: 14/14 on
B200/SM100
      and 14/14 on B300/SM103.
- [x] B200 stability run: 70/70 cases across five consecutive runs.
- [x] Review follow-up suite on B300/SM103: all focused VariableWindow,
MLA,
      dispatch, and validation cases passed after the final changes.
- [x] Promoted public artifact on a clean unauthenticated B200 cache:
artifact tests 10/10, retained VariableWindow/two-sided/validation suite
      14/14, and representative existing TRTLLM-native MLA causal/dense
      numerical launches 2/2.
- [x] Post-rebase validation against current `main` on B300/SM103:
artifact
      tests 17/17, all 18 newly added sliding-window cases, and both
      TRTLLM-Gen MLA planned-backend oracle cases passed.
- [x] Review-remediation validation on a non-oversubscribed B300/SM103:
Cake
      FMHA 151/151; focused variable/two-sided/validation prefill 18/18;
binding/non-binding decode boundary 2/2; causal/non-causal trace
reference
      4/4; and TRTLLM-Gen MLA planned-backend oracle 2/2.
- [x] `flashinfer-cubin` full public-artifact enumeration and wheel
build passed;
the 1.6-GiB wheel passed a complete ZIP CRC scan and contains all 36,964
      promoted FMHA CUBINs and all 1,424 VariableWindow CUBINs.

Representative standard-node latency smoke test
(`B=8,Q=512,KV=4096,Hq=16,Hkv=4,D=128,P=16`, BF16/HND):

| GPU | Fixed window | VariableWindow | Delta |
|---|---:|---:|
| B300 / SM103 | 29.438 µs | 30.667 µs | +4.17% |
| B200 / SM100 | 35.520 µs | 36.831 µs | +3.69% |

The unconditional sliding-kernel selection called out during review was
removed. A finite causal window now selects the existing causal fast
path when
`max_kv_len <= window_left + 1`, matching the pre-change behavior. On
the
non-oversubscribed B300, the repository TRTLLM FMHA benchmark measured
the
same 4.2624 µs for unbounded decode and non-binding `window_left=127` at
`B=8,KV=128,Hq=16,Hkv=4,D=128,P=16`; a binding `window_left=127` decode
at
`KV=4096` measured 4.4736 µs. Because dispatch parity was restored,
there is no
remaining before/after selection change for existing sliding-window
workloads.

## Reviewer Notes

Please focus on:

1. the mask/window validation contract in
   `csrc/trtllm_fmha_kernel_launcher.cu`;
2. kernel selection and split-KV heuristics in
   `include/flashinfer/trtllm/fmha/fmhaKernels.cuh`;
3. the direct API versus paged-wrapper behavior in
`flashinfer/prefill.py`; and
4. the `VariableWindow` reference and negative tests in
   `tests/attention/test_trtllm_gen_attention_prefill.py`.

The field-presence adapter for `mFp16Softmax/mUsesSpcompress` versus
`mReserved1/mReserved2` is deliberate compile-time compatibility code. A
separate producer-owned tracker will establish whether the metadata
schemas
converge or the adapter becomes permanent.

The removal of the trailing `mChunkedAttentionSizeLog2 = 0` assignment
also
fixes a latent downstream bug: that assignment overwrote the value
computed
for enabled chunked attention. FlashInfer itself continues to disable
chunked
attention with the producer's new `0` sentinel.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for two-sided sliding windows and per-token visibility
bounds in TRT-LLM context attention.
* Added window options to attention tracing, including non-causal
attention.
* Extended sliding-window support to eligible decode and context
attention paths.

* **Bug Fixes**
* Unsupported finite-window configurations now return clear validation
errors instead of being silently ignored.
* Improved attention kernel selection for bounded windows, including
cases where the window does not restrict the available sequence.

* **Tests**
* Expanded coverage for sliding windows, variable per-token bounds,
validation, and trace-reference correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d892cd4](https://github.com/flashinfer-ai/flashinfer/commit/d892cd4197149d60c0e86ca0026a3df9dfe111fb)

- **作者**: eigen
- **时间**: 2026-10-21T18:44:58Z
- **提交信息**: perf(cake_rmsnorm): faster H1536 / H4096 grad by row-count window and SM107 H1536 fwd (SM100 / SM103 / SM107) (#6939)

`cake_rmsnorm_train` is Cake's RMSNorm training kernel: one data type
(BF16 activations and weight, FP32 `rstd` and deterministic FP32
`dweight`) in four variants, plain and residual-fused, each forward and
backward. This PR changes the plain backward (`dx`, `dweight`) at H=1536
and H=4096 on sm_100a, sm_103a and sm_107a, and the plain forward at
H=1536 on sm_107a for row counts above T=12288. The baseline is the
previous Cake version, PR #6842, which runs one cooperative persistent
backward program per hidden size and architecture above a row-count
threshold and the row-wise programs below it. The backward now ships as
row-count windows, each window instance folding the cross-chunk
`dweight` reduction as a fixed-order tree and synchronizing the grid
with a self-resetting flip barrier; the changed sm_107a forward moves to
a bulk-copy producer/consumer program. The numerical contract is
unchanged (BF16 I/O, FP32 products and sums, `dx` rounded once, `rstd`
in FP32, and `dweight` in FP32, deterministic and atomics-free); the
tree fold regroups the cross-chunk `dweight` sum, so `dweight` bits
differ from #6842 within the same tolerance, while the new sm_107a
forward's `y` and `rstd` are bitwise identical to those of the previous
forward program. Speedups (previous / new) of the changed rows on GB300
(sm_103a) are 1.008x–1.073x bwd and 1.006x–1.071x step at H=1536, and
1.021x–1.075x bwd and 1.014x–1.058x step at H=4096 for T ≤ 4096; on B200
(sm_100a) they are 1.010x–1.118x bwd and 1.006x–1.089x step at H=1536,
and 1.040x–1.077x bwd and 1.030x–1.051x step at H=4096 for T ≤ 4096; on
R200 (sm_107a) they are 1.011x–1.084x bwd, 1.021x–1.101x step and
1.035x–1.079x fwd (above T=12288) at H=1536, and 1.007x–1.134x bwd and
1.009x–1.117x step at H=4096. The H=4096 rows above T=4096 on sm_100a
and sm_103a run the unchanged previous program on both sides, so their
ratios are measurement noise around 1.000x (GB300 0.995x–1.011x bwd and
1.000x–1.007x step; B200 0.994x–1.011x bwd and 0.977x–1.005x step).

Both versions run in the same process on the same GPU. Latencies are
CUPTI kernel-active times (T x H input, cold L2 before every launch),
each the median of 3 counterbalanced paired groups. In the Pass column,
`bwd` is the backward, `step` is forward + backward and `fwd` is the
forward. Speedup is previous / new latency; above 1.000x the new version
is faster. Both versions are compiled with CUDA 13.4 (previous Cake: the
shipped FlashInfer build of #6842, nvcc 13.4; new Cake: NVRTC 13.4). The
host runs PyTorch 2.14.1+cu130, the same on all three boards.

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 5.47 | 5.12 | 1.069x |
| 1536 | 256 | step | 7.78 | 7.30 | 1.066x |
| 1536 | 1024 | bwd | 7.20 | 6.72 | 1.071x |
| 1536 | 1024 | step | 9.95 | 9.44 | 1.054x |
| 1536 | 4096 | bwd | 11.78 | 10.98 | 1.073x |
| 1536 | 4096 | step | 17.95 | 16.77 | 1.071x |
| 1536 | 14928 | bwd | 27.62 | 26.82 | 1.030x |
| 1536 | 14928 | step | 42.66 | 41.73 | 1.022x |
| 1536 | 15288 | bwd | 27.78 | 27.36 | 1.015x |
| 1536 | 15288 | step | 43.74 | 42.91 | 1.019x |
| 1536 | 15566 | bwd | 28.35 | 27.78 | 1.021x |
| 1536 | 15566 | step | 44.45 | 43.52 | 1.021x |
| 1536 | 15590 | bwd | 28.10 | 27.58 | 1.019x |
| 1536 | 15590 | step | 44.16 | 43.31 | 1.020x |
| 1536 | 16114 | bwd | 28.90 | 28.38 | 1.018x |
| 1536 | 16114 | step | 45.38 | 44.48 | 1.020x |
| 1536 | 16132 | bwd | 28.83 | 28.35 | 1.017x |
| 1536 | 16132 | step | 45.50 | 44.45 | 1.024x |
| 1536 | 16164 | bwd | 28.83 | 28.29 | 1.019x |
| 1536 | 16164 | step | 45.34 | 44.54 | 1.018x |
| 1536 | 16263 | bwd | 29.09 | 28.61 | 1.017x |
| 1536 | 16263 | step | 45.50 | 44.54 | 1.022x |
| 1536 | 32768 | bwd | 52.26 | 51.81 | 1.009x |
| 1536 | 32768 | step | 83.01 | 82.24 | 1.009x |
| 1536 | 65536 | bwd | 96.87 | 96.10 | 1.008x |
| 1536 | 65536 | step | 155.78 | 154.78 | 1.006x |
| 4096 | 256 | bwd | 6.85 | 6.37 | 1.075x |
| 4096 | 256 | step | 9.31 | 8.80 | 1.058x |
| 4096 | 1024 | bwd | 10.08 | 9.54 | 1.057x |
| 4096 | 1024 | step | 14.30 | 13.66 | 1.047x |
| 4096 | 4096 | bwd | 21.54 | 21.09 | 1.021x |
| 4096 | 4096 | step | 33.41 | 32.96 | 1.014x |
| 4096 | 14928 | bwd | 62.21 | 62.50 | 0.995x |
| 4096 | 14928 | step | 98.78 | 98.56 | 1.002x |
| 4096 | 15288 | bwd | 63.87 | 63.33 | 1.009x |
| 4096 | 15288 | step | 100.06 | 100.00 | 1.001x |
| 4096 | 15566 | bwd | 65.31 | 64.61 | 1.011x |
| 4096 | 15566 | step | 102.37 | 101.95 | 1.004x |
| 4096 | 15590 | bwd | 65.25 | 64.90 | 1.005x |
| 4096 | 15590 | step | 102.53 | 101.82 | 1.007x |
| 4096 | 16114 | bwd | 65.92 | 66.24 | 0.995x |
| 4096 | 16114 | step | 104.58 | 104.61 | 1.000x |
| 4096 | 16132 | bwd | 66.34 | 66.21 | 1.002x |
| 4096 | 16132 | step | 104.54 | 104.38 | 1.002x |
| 4096 | 16164 | bwd | 66.24 | 66.21 | 1.000x |
| 4096 | 16164 | step | 104.90 | 104.77 | 1.001x |
| 4096 | 16263 | bwd | 66.85 | 66.62 | 1.003x |
| 4096 | 16263 | step | 105.60 | 105.57 | 1.000x |
| 4096 | 32768 | bwd | 125.63 | 125.62 | 1.000x |
| 4096 | 32768 | step | 201.79 | 201.76 | 1.000x |
| 4096 | 65536 | bwd | 241.25 | 241.15 | 1.000x |
| 4096 | 65536 | step | 391.46 | 391.62 | 1.000x |

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 6.02 | 5.57 | 1.080x |
| 1536 | 256 | step | 8.57 | 8.03 | 1.068x |
| 1536 | 1024 | bwd | 7.87 | 7.04 | 1.118x |
| 1536 | 1024 | step | 11.01 | 10.11 | 1.089x |
| 1536 | 4096 | bwd | 12.48 | 11.62 | 1.074x |
| 1536 | 4096 | step | 19.07 | 17.89 | 1.066x |
| 1536 | 14928 | bwd | 28.67 | 27.94 | 1.026x |
| 1536 | 14928 | step | 44.67 | 43.62 | 1.024x |
| 1536 | 15288 | bwd | 28.90 | 28.19 | 1.025x |
| 1536 | 15288 | step | 45.35 | 44.26 | 1.025x |
| 1536 | 15566 | bwd | 29.41 | 28.83 | 1.020x |
| 1536 | 15566 | step | 46.14 | 45.34 | 1.018x |
| 1536 | 15590 | bwd | 29.92 | 29.22 | 1.024x |
| 1536 | 15590 | step | 46.66 | 45.66 | 1.022x |
| 1536 | 16114 | bwd | 30.53 | 29.92 | 1.020x |
| 1536 | 16114 | step | 47.65 | 46.59 | 1.023x |
| 1536 | 16132 | bwd | 30.69 | 29.92 | 1.026x |
| 1536 | 16132 | step | 47.65 | 46.37 | 1.028x |
| 1536 | 16164 | bwd | 30.56 | 29.89 | 1.022x |
| 1536 | 16164 | step | 47.62 | 46.46 | 1.025x |
| 1536 | 16263 | bwd | 30.21 | 29.47 | 1.025x |
| 1536 | 16263 | step | 47.90 | 46.88 | 1.022x |
| 1536 | 32768 | bwd | 54.37 | 53.82 | 1.010x |
| 1536 | 32768 | step | 86.02 | 85.54 | 1.006x |
| 1536 | 65536 | bwd | 102.02 | 99.78 | 1.022x |
| 1536 | 65536 | step | 162.85 | 160.32 | 1.016x |
| 4096 | 256 | bwd | 7.20 | 6.72 | 1.071x |
| 4096 | 256 | step | 9.89 | 9.41 | 1.051x |
| 4096 | 1024 | bwd | 10.69 | 9.92 | 1.077x |
| 4096 | 1024 | step | 14.98 | 14.37 | 1.042x |
| 4096 | 4096 | bwd | 23.04 | 22.14 | 1.040x |
| 4096 | 4096 | step | 35.74 | 34.72 | 1.030x |
| 4096 | 14928 | bwd | 64.32 | 63.62 | 1.011x |
| 4096 | 14928 | step | 101.70 | 101.28 | 1.004x |
| 4096 | 15288 | bwd | 65.54 | 65.54 | 1.000x |
| 4096 | 15288 | step | 103.78 | 103.94 | 0.998x |
| 4096 | 15566 | bwd | 67.33 | 67.46 | 0.998x |
| 4096 | 15566 | step | 105.83 | 105.82 | 1.000x |
| 4096 | 15590 | bwd | 67.17 | 67.42 | 0.996x |
| 4096 | 15590 | step | 106.46 | 106.30 | 1.002x |
| 4096 | 16114 | bwd | 68.54 | 68.74 | 0.997x |
| 4096 | 16114 | step | 108.38 | 109.22 | 0.992x |
| 4096 | 16132 | bwd | 67.81 | 68.22 | 0.994x |
| 4096 | 16132 | step | 108.32 | 108.74 | 0.996x |
| 4096 | 16164 | bwd | 69.15 | 69.12 | 1.000x |
| 4096 | 16164 | step | 109.79 | 109.60 | 1.002x |
| 4096 | 16263 | bwd | 68.58 | 68.74 | 0.998x |
| 4096 | 16263 | step | 110.14 | 109.63 | 1.005x |
| 4096 | 32768 | bwd | 129.70 | 129.25 | 1.003x |
| 4096 | 32768 | step | 208.10 | 208.13 | 1.000x |
| 4096 | 65536 | bwd | 249.41 | 248.48 | 1.004x |
| 4096 | 65536 | step | 403.14 | 412.83 | 0.977x |

### NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU for the two versions of a row)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 1536 | 256 | bwd | 5.06 | 4.83 | 1.046x |
| 1536 | 256 | step | 7.68 | 7.07 | 1.086x |
| 1536 | 1024 | bwd | 5.92 | 5.86 | 1.011x |
| 1536 | 1024 | step | 8.86 | 8.32 | 1.065x |
| 1536 | 4096 | bwd | 8.70 | 8.03 | 1.084x |
| 1536 | 4096 | step | 12.90 | 11.71 | 1.101x |
| 1536 | 14928 | bwd | 17.31 | 16.70 | 1.036x |
| 1536 | 14928 | step | 27.14 | 25.57 | 1.061x |
| 1536 | 15288 | bwd | 17.86 | 16.90 | 1.057x |
| 1536 | 15288 | step | 27.62 | 26.21 | 1.054x |
| 1536 | 15566 | bwd | 17.89 | 16.96 | 1.055x |
| 1536 | 15566 | step | 28.03 | 26.21 | 1.070x |
| 1536 | 15590 | bwd | 17.86 | 17.15 | 1.041x |
| 1536 | 15590 | step | 28.06 | 26.46 | 1.060x |
| 1536 | 16114 | bwd | 18.59 | 17.70 | 1.051x |
| 1536 | 16114 | step | 28.90 | 27.20 | 1.062x |
| 1536 | 16132 | bwd | 18.75 | 17.98 | 1.043x |
| 1536 | 16132 | step | 28.74 | 27.33 | 1.052x |
| 1536 | 16164 | bwd | 18.43 | 17.70 | 1.042x |
| 1536 | 16164 | step | 28.90 | 27.30 | 1.059x |
| 1536 | 16263 | bwd | 18.43 | 17.66 | 1.043x |
| 1536 | 16263 | step | 29.01 | 27.30 | 1.063x |
| 1536 | 32768 | bwd | 30.18 | 29.22 | 1.033x |
| 1536 | 32768 | step | 48.93 | 47.20 | 1.037x |
| 1536 | 65536 | bwd | 53.19 | 52.54 | 1.012x |
| 1536 | 65536 | step | 87.52 | 85.70 | 1.021x |
| 4096 | 256 | bwd | 6.02 | 5.54 | 1.087x |
| 4096 | 256 | step | 8.88 | 7.97 | 1.115x |
| 4096 | 1024 | bwd | 8.38 | 7.39 | 1.134x |
| 4096 | 1024 | step | 11.94 | 10.69 | 1.117x |
| 4096 | 4096 | bwd | 14.27 | 13.02 | 1.096x |
| 4096 | 4096 | step | 22.94 | 21.25 | 1.080x |
| 4096 | 14928 | bwd | 35.04 | 34.11 | 1.027x |
| 4096 | 14928 | step | 56.70 | 55.36 | 1.024x |
| 4096 | 15288 | bwd | 36.06 | 34.91 | 1.033x |
| 4096 | 15288 | step | 58.18 | 56.77 | 1.025x |
| 4096 | 15566 | bwd | 37.28 | 36.48 | 1.022x |
| 4096 | 15566 | step | 59.71 | 58.40 | 1.022x |
| 4096 | 15590 | bwd | 37.15 | 36.90 | 1.007x |
| 4096 | 15590 | step | 59.52 | 58.82 | 1.012x |
| 4096 | 16114 | bwd | 37.12 | 36.51 | 1.017x |
| 4096 | 16114 | step | 60.29 | 59.20 | 1.018x |
| 4096 | 16132 | bwd | 36.80 | 36.13 | 1.019x |
| 4096 | 16132 | step | 60.00 | 58.66 | 1.023x |
| 4096 | 16164 | bwd | 37.44 | 36.23 | 1.034x |
| 4096 | 16164 | step | 60.70 | 59.10 | 1.027x |
| 4096 | 16263 | bwd | 37.44 | 36.32 | 1.031x |
| 4096 | 16263 | step | 60.93 | 59.23 | 1.029x |
| 4096 | 32768 | bwd | 69.15 | 68.51 | 1.009x |
| 4096 | 32768 | step | 112.67 | 111.62 | 1.009x |
| 4096 | 65536 | bwd | 128.58 | 126.02 | 1.020x |
| 4096 | 65536 | step | 213.78 | 210.98 | 1.013x |
| 1536 | 14928 | fwd | 10.18 | 9.50 | 1.071x |
| 1536 | 15288 | fwd | 10.11 | 9.60 | 1.053x |
| 1536 | 15566 | fwd | 10.30 | 9.63 | 1.070x |
| 1536 | 15590 | fwd | 10.43 | 9.66 | 1.079x |
| 1536 | 16114 | fwd | 10.50 | 9.92 | 1.058x |
| 1536 | 16132 | fwd | 10.50 | 9.95 | 1.055x |
| 1536 | 16164 | fwd | 10.37 | 10.02 | 1.035x |
| 1536 | 16263 | fwd | 10.59 | 9.98 | 1.061x |
| 1536 | 32768 | fwd | 18.88 | 17.86 | 1.057x |
| 1536 | 65536 | fwd | 34.14 | 32.99 | 1.035x |

Cake also ships the residual-fused forward and backward (which reject
H=1536 and H=4096) and hidden sizes 512, 2048 and 6144; the family
covers sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added optimized CUDA implementations for bfloat16 RMSNorm training,
including forward and backward computation.
- Added architecture-specific kernel selections for newer GPU
generations.
- Improved gradient reduction and asynchronous processing for supported
workloads.

- **Bug Fixes**
  - Added validation to reject invalid chunk counts before execution.
- Improved handling of boundary-sized inputs and backward route
selection.

- **Tests**
- Expanded coverage for forward and backward kernel selection
boundaries.
  - Verified results against high-precision reference calculations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7808983](https://github.com/flashinfer-ai/flashinfer/commit/7808983872ee3961f142bce3227d7ecc2afa7253)

- **作者**: eigen
- **时间**: 2026-10-21T18:41:07Z
- **提交信息**: perf(cake_vsa_sm90): faster persistent kernel and a compact static program (#6949)

This PR updates Cake's variable block-sparse attention forward kernel
for Hopper (sm_90a), which is used through
`flashinfer.sparse.VariableBlockSparseAttentionWrapper(backend="cake")`.
The kernel takes BF16 Q/K/V/O in HND layout with head_dim 128, 64-token
blocks and 1 to 64 KV blocks per query block. It supports ragged and
uniform masks and any finite softmax scale. Planning is separate from
running, and each run is one kernel launch that can be captured in a
CUDA graph. The kernel has 18 programs. The persistent kernel has three:
one with static tile lists, one with a device tile queue, and a new
compact static program for uniform pair plans of short tiles with many
tiles per CTA. The small-selection kernel has 15 variants: direct k1 /
k3 / k4 / k6; DSM-cluster k2c4 / k3c3 / k3c6 / k4c2 / k4c4 / k6c2;
split-KV k4s / k6s; and split-cluster k6sc3 / k6sc4 / k6sc8. This PR
delivers all 18 programs (the 17 existing ones updated in place, the
compact program new) and keeps the package layout and public API of the
previous version. The baseline is the previous Cake version of this
kernel, which is FlashInfer main before this PR.

Kernel times on NVIDIA H100 SXM 80GB HBM3 (sm_90a), CUDA 13.4, SM clock
1980 MHz: median over 9 interleaved groups × 256 samples with a cold L2
per sample, previous Cake and this PR measured in the same process;
speedup = the paired ratio previous / this PR over all samples (not the
ratio of the two medians).

**b20 (the 20 shapes of PR 5470)**

| shape | previous Cake (µs) | this PR (µs) | speedup |
|---|---|---|---|
| h1-m64-n64-k1-ragged0-scale0 | 2.944 | 2.880 | 1.0222 |
| h4-m256-n256-k1-ragged0-scale0 | 3.360 | 3.288 | 1.0242 |
| h8-m256-n256-k3-ragged0-scale0 | 5.312 | 5.184 | 1.0247 |
| h8-m1024-n1024-k4-ragged0-scale0 | 7.360 | 7.200 | 1.0222 |
| h8-m1024-n1024-k12-ragged0-scale0 | 11.039 | 10.624 | 1.0391 |
| h8-m2048-n2048-k8-ragged0-scale0 | 14.688 | 14.224 | 1.0338 |
| h8-m2048-n2048-k16-ragged0-scale0 | 22.560 | 21.216 | 1.0642 |
| h8-m4096-n4096-k16-ragged0-scale0 | 38.880 | 37.072 | 1.0510 |
| h8-m4096-n4096-k32-ragged0-scale0 | 64.479 | 60.832 | 1.0600 |
| h4-m512-n1024-k4-ragged0-scale0 | 6.208 | 6.016 | 1.0319 |
| h4-m1024-n512-k4-ragged1-scale0 | 5.856 | 5.664 | 1.0339 |
| h4-m1024-n1024-k8-ragged1-scale0 | 7.232 | 6.720 | 1.0762 |
| h7-m4096-n4096-k16-ragged1-scale0 | 24.160 | 23.696 | 1.0203 |
| h4-m512-n512-k4-ragged0-scale1 | 5.632 | 5.441 | 1.0351 |
| h1-m1024-n1024-k16-ragged0-scale0 | 6.432 | 5.952 | 1.0806 |
| h7-m16384-n16384-k32-ragged0-scale0 | 233.792 | 225.607 | 1.0362 |
| h7-m32768-n32768-k64-ragged0-scale0 | 927.755 | 908.548 | 1.0235 |
| h7-m65536-n65536-k64-ragged0-scale0 | 1993.692 | 1948.805 | 1.0318 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3487.571 | 3422.797 | 1.0285 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1788.126 | 1720.910 | 1.0323 |

**ext33 (banded H=1 shapes)**

| shape | previous Cake (µs) | this PR (µs) | speedup |
|---|---|---|---|
| h16-m1024-n8192-k1-ragged0-scale0 | 9.920 | 9.664 | 1.0265 |
| h8-m512-n4096-k2-ragged0-scale0 | 5.985 | 5.888 | 1.0165 |
| h4-m2048-n4096-k6-ragged0-scale0 | 9.472 | 9.312 | 1.0172 |
| h2-m4096-n4096-k5-ragged0-scale0 | 8.128 | 7.936 | 1.0243 |
| h1-m2048-n4096-k20-ragged0-scale0 | 10.751 | 10.304 | 1.0434 |
| h1-m1024-n4096-k24-ragged0-scale0 | 10.880 | 9.232 | 1.1806 |
| h1-m512-n8192-k48-ragged0-scale0 | 13.472 | 10.680 | 1.2624 |
| h1-m512-n8192-k64-ragged0-scale0 | 15.136 | 14.768 | 1.0260 |
| h1-m256-n8192-k64-ragged0-scale0 | 15.040 | 14.256 | 1.0538 |
| h1-m1024-n2048-k7-ragged0-scale0 | 5.600 | 5.184 | 1.0802 |
| h1-m2048-n2048-k7-ragged0-scale0 | 6.592 | 6.080 | 1.0840 |
| h1-m1024-n2048-k8-ragged0-scale0 | 5.568 | 5.184 | 1.0741 |
| h1-m4096-n4096-k8-ragged0-scale0 | 7.552 | 7.008 | 1.0778 |
| h1-m4096-n4096-k7-ragged1-scale0 | 7.200 | 6.704 | 1.0714 |
| h1-m1024-n4096-k9-ragged0-scale0 | 6.624 | 6.176 | 1.0725 |
| h1-m1024-n4096-k12-ragged0-scale0 | 7.840 | 7.264 | 1.0793 |
| h1-m512-n4096-k16-ragged0-scale0 | 6.847 | 6.368 | 1.0753 |
| h1-m512-n4096-k18-ragged0-scale0 | 6.880 | 6.464 | 1.0644 |
| h1-m1024-n4096-k16-ragged0-scale0 | 7.104 | 6.624 | 1.0725 |
| h2-m1024-n4096-k8-ragged0-scale0 | 7.519 | 7.008 | 1.0729 |
| h1-m1024-n4096-k12-ragged0-scale0-uneven | 7.456 | 6.880 | 1.0837 |
| h1-m2048-n4096-k20-ragged0-scale0-uneven | 9.872 | 9.488 | 1.0423 |
| h4-m2048-n4096-k6-ragged0-scale0-uneven | 8.992 | 8.832 | 1.0181 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven | 25.120 | 24.608 | 1.0208 |
| h32-m2048-n2048-k8-ragged0-scale0 | 43.840 | 42.144 | 1.0402 |
| h16-m4096-n16384-k16-ragged0-scale0 | 86.464 | 85.320 | 1.0135 |
| h8-m1024-n32768-k64-ragged0-scale0 | 56.191 | 55.968 | 1.0028 |
| h8-m2048-n32768-k48-ragged1-scale0 | 56.640 | 56.144 | 1.0091 |
| h32-m8192-n8192-k24-ragged0-scale0 | 397.614 | 387.062 | 1.0246 |
| h16-m8192-n8192-k5-ragged0-scale0 | 62.752 | 61.504 | 1.0208 |
| h8-m8192-n8192-k2-ragged0-scale0 | 28.928 | 27.776 | 1.0415 |
| h8-m4096-n4096-k64-ragged0-scale1 | 114.736 | 107.008 | 1.0713 |
| h8-m4096-n4096-k20-ragged1-scale0 | 29.952 | 29.240 | 1.0241 |

**real39 (serving envelope)**

| shape | previous Cake (µs) | this PR (µs) | speedup |
|---|---|---|---|
| h8-m512-n512-k1-ragged0-scale0 | 4.352 | 4.256 | 1.0226 |
| h8-m512-n1024-k2-ragged0-scale0 | 5.536 | 5.488 | 1.0058 |
| h16-m256-n512-k2-ragged1-scale0 | 5.440 | 5.345 | 1.0180 |
| h8-m1024-n2048-k4-ragged0-scale0 | 8.352 | 8.240 | 1.0117 |
| h8-m1024-n4096-k6-ragged0-scale0 | 11.392 | 11.264 | 1.0114 |
| h4-m2048-n2048-k5-ragged0-scale0 | 7.968 | 7.776 | 1.0247 |
| h8-m256-n4096-k8-ragged0-scale0 | 8.320 | 7.872 | 1.0569 |
| h8-m256-n2048-k8-ragged0-scale0 | 7.904 | 7.440 | 1.0647 |
| h4-m256-n2048-k7-ragged0-scale0 | 6.304 | 5.887 | 1.0708 |
| h8-m512-n4096-k8-ragged0-scale0 | 10.400 | 9.984 | 1.0417 |
| h16-m256-n2048-k7-ragged1-scale0 | 9.088 | 8.576 | 1.0597 |
| h8-m256-n4096-k9-ragged0-scale0 | 8.799 | 8.384 | 1.0495 |
| h4-m512-n2048-k9-ragged0-scale0 | 7.456 | 6.960 | 1.0737 |
| h8-m512-n4096-k12-ragged0-scale0 | 12.192 | 11.712 | 1.0410 |
| h8-m256-n2048-k10-ragged0-scale0 | 8.480 | 8.032 | 1.0558 |
| h8-m256-n4096-k16-ragged0-scale0 | 12.800 | 12.384 | 1.0336 |
| h4-m256-n4096-k14-ragged0-scale0 | 7.840 | 7.360 | 1.0652 |
| h4-m256-n8192-k18-ragged0-scale0 | 9.472 | 9.200 | 1.0314 |
| h8-m128-n4096-k17-ragged0-scale0 | 8.928 | 8.544 | 1.0449 |
| h4-m256-n8192-k24-ragged0-scale0 | 13.120 | 11.136 | 1.1782 |
| h8-m256-n16384-k32-ragged0-scale0 | 23.008 | 19.968 | 1.1522 |
| h4-m512-n16384-k20-ragged0-scale0 | 15.200 | 14.968 | 1.0161 |
| h8-m128-n32768-k64-ragged0-scale0 | 35.360 | 28.912 | 1.2237 |
| h4-m256-n8192-k48-ragged0-scale0 | 16.352 | 15.904 | 1.0282 |
| h8-m256-n4096-k12-ragged0-scale0-uneven | 8.352 | 7.808 | 1.0697 |
| h8-m512-n8192-k24-ragged0-scale0-uneven | 14.752 | 14.288 | 1.0313 |
| h8-m256-n4096-k8-ragged0-scale1 | 8.320 | 7.872 | 1.0569 |
| h32-m2048-n2048-k8-ragged0-scale0 | 43.840 | 42.144 | 1.0402 |
| h16-m4096-n16384-k16-ragged0-scale0 | 86.464 | 85.320 | 1.0135 |
| h8-m1024-n32768-k64-ragged0-scale0 | 56.191 | 55.968 | 1.0028 |
| h8-m2048-n32768-k48-ragged1-scale0 | 56.640 | 56.144 | 1.0091 |
| h32-m8192-n8192-k24-ragged0-scale0 | 397.614 | 387.062 | 1.0246 |
| h16-m8192-n8192-k5-ragged0-scale0 | 62.752 | 61.504 | 1.0208 |
| h8-m4096-n4096-k64-ragged0-scale1 | 114.736 | 107.008 | 1.0713 |
| h8-m4096-n4096-k20-ragged1-scale0 | 29.952 | 29.240 | 1.0241 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven | 25.120 | 24.608 | 1.0208 |
| h16-m1024-n8192-k12-ragged0-scale0 | 31.999 | 31.440 | 1.0183 |
| h32-m512-n8192-k16-ragged0-scale0 | 45.152 | 44.896 | 1.0057 |
| h16-m1024-n8192-k1-ragged0-scale0 | 9.920 | 9.664 | 1.0265 |

**long45 (long-context shapes)**

| shape | previous Cake (µs) | this PR (µs) | speedup |
|---|---|---|---|
| h3-m32768-n32768-k32-ragged0-scale0 | 208.991 | 206.207 | 1.0137 |
| h3-m32768-n32768-k64-ragged0-scale0 | 395.136 | 386.528 | 1.0218 |
| h3-m32768-n32768-k64-ragged1-scale0 | 207.167 | 204.103 | 1.0149 |
| h3-m75648-n75648-k32-ragged0-scale0 | 511.759 | 504.127 | 1.0147 |
| h3-m75648-n75648-k64-ragged0-scale0 | 981.340 | 962.956 | 1.0231 |
| h3-m75648-n75648-k64-ragged1-scale0 | 502.431 | 497.727 | 1.0078 |
| h3-m109632-n109632-k32-ragged0-scale0 | 772.204 | 762.365 | 1.0092 |
| h3-m109632-n109632-k64-ragged0-scale0 | 1477.359 | 1457.807 | 1.0238 |
| h3-m109632-n109632-k64-ragged1-scale0 | 743.677 | 728.821 | 1.0177 |
| h7-m32768-n32768-k32-ragged0-scale0 | 486.128 | 478.999 | 1.0152 |
| h7-m32768-n32768-k64-ragged0-scale0 | 927.755 | 908.548 | 1.0235 |
| h7-m32768-n32768-k64-ragged1-scale0 | 477.246 | 469.318 | 1.0154 |
| h7-m75648-n75648-k32-ragged0-scale0 | 1224.495 | 1208.703 | 1.0184 |
| h7-m75648-n75648-k64-ragged0-scale0 | 2301.032 | 2268.289 | 1.0215 |
| h7-m75648-n75648-k64-ragged1-scale0 | 1185.455 | 1165.687 | 1.0154 |
| h7-m109632-n109632-k32-ragged0-scale0 | 1807.738 | 1791.674 | 1.0133 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3487.571 | 3422.797 | 1.0285 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1788.126 | 1720.910 | 1.0323 |
| h8-m32768-n32768-k32-ragged0-scale0 | 556.799 | 548.607 | 1.0153 |
| h8-m32768-n32768-k64-ragged0-scale0 | 1066.108 | 1042.933 | 1.0234 |
| h8-m32768-n32768-k64-ragged1-scale0 | 552.719 | 541.936 | 1.0182 |
| h8-m75648-n75648-k32-ragged0-scale0 | 1366.043 | 1343.900 | 1.0169 |
| h8-m75648-n75648-k64-ragged0-scale0 | 2675.661 | 2624.654 | 1.0278 |
| h8-m75648-n75648-k64-ragged1-scale0 | 1347.692 | 1326.836 | 1.0138 |
| h8-m109632-n109632-k32-ragged0-scale0 | 2100.351 | 2065.631 | 1.0224 |
| h8-m109632-n109632-k64-ragged0-scale0 | 4087.012 | 3990.692 | 1.0286 |
| h8-m109632-n109632-k64-ragged1-scale0 | 2042.477 | 1965.382 | 1.0296 |
| h10-m32768-n32768-k32-ragged0-scale0 | 697.582 | 693.350 | 1.0075 |
| h10-m32768-n32768-k64-ragged0-scale0 | 1346.062 | 1313.798 | 1.0269 |
| h10-m32768-n32768-k64-ragged1-scale0 | 688.974 | 675.630 | 1.0172 |
| h10-m75648-n75648-k32-ragged0-scale0 | 1742.173 | 1719.405 | 1.0204 |
| h10-m75648-n75648-k64-ragged0-scale0 | 3314.084 | 3246.142 | 1.0292 |
| h10-m75648-n75648-k64-ragged1-scale0 | 1670.012 | 1628.693 | 1.0213 |
| h10-m109632-n109632-k32-ragged0-scale0 | 2625.750 | 2587.167 | 1.0170
|
| h10-m109632-n109632-k64-ragged0-scale0 | 5200.534 | 5056.648 | 1.0333
|
| h10-m109632-n109632-k64-ragged1-scale0 | 2556.535 | 2443.007 | 1.0324
|
| h12-m32768-n32768-k32-ragged0-scale0 | 842.062 | 827.527 | 1.0155 |
| h12-m32768-n32768-k64-ragged0-scale0 | 1608.202 | 1566.771 | 1.0263 |
| h12-m32768-n32768-k64-ragged1-scale0 | 832.655 | 814.662 | 1.0204 |
| h12-m75648-n75648-k32-ragged0-scale0 | 2092.904 | 2053.928 | 1.0213 |
| h12-m75648-n75648-k64-ragged0-scale0 | 4054.568 | 3973.066 | 1.0260 |
| h12-m75648-n75648-k64-ragged1-scale0 | 2033.672 | 1980.665 | 1.0219 |
| h12-m109632-n109632-k32-ragged0-scale0 | 3158.986 | 3091.379 | 1.0225
|
| h12-m109632-n109632-k64-ragged0-scale0 | 6222.597 | 6017.016 | 1.0352
|
| h12-m109632-n109632-k64-ragged1-scale0 | 3120.538 | 2996.410 | 1.0316
|

This family (`cake_vsa_sm90`) ships for sm_90a only and in BF16 only;
Cake's separate `cake_vsa` family covers SM100 / SM103 (Blackwell) with
its own program variants (blk64 persistent, blk128 compact, fp16 direct,
GQA mask, head64 / head96 native, and long-sequence and ultra-sparse BSR
forms).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added an optimized attention execution path for uniform workloads with
short tiles and high tile density.
* Improved KV-cache memory behavior by selecting eviction hints based on
access patterns.

* **Compatibility**
* Expanded SM90 backend support with the new compact attention route
while preserving existing queued and standard execution paths.

* **Reliability**
* Added validation and test coverage for compact-route selection, cache
hints, and backend stage configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c785284](https://github.com/flashinfer-ai/flashinfer/commit/c78528451fcd327e6f81fb5586445106cd11abe3)

- **作者**: eigen
- **时间**: 2026-10-21T18:40:18Z
- **提交信息**: deslop(cake_minimax_h3): dedupe the varlen helpers, drop stubs and unused macros, share the norm+AdaLN kernels (#6947)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of the Cake MiniMax-H3 code for SM100 /
SM103, tracked in #6667. It covers these parts of the family:
- the varlen attention package;
- three hand-written single-source operators: the MLP block, FC1 +
SwiGLU and the output projection;
- the hand-written BF16 pre-attention operator;
- the generated NVFP4 pre-attention and QKV quantize-and-pack
directories.

The four mechanical commits do the following:
- drop the 30 device-helper headers that the varlen package vendored as
token-identical copies of repository headers, so that its includes
resolve to the repository copies;
- drop two `.clang-format` stubs that repeat the top-level pre-commit
exclude;
- drop 112 unreferenced macro definitions (84 distinct names) and their
`#undef` partners from the four hand-written operator translation units
(TUs);
- move the three RMSNorm + indexed AdaLN kernels, which were duplicated
byte for byte in the MLP and FC1 + SwiGLU TUs, into one shared header
each.

Device code, kernel symbols, module names, loaders, registries,
dispatch, launch parameters, exports, tests and docs do not change. No
Python file changes.

Behaviour changes:
- **Host backtraces.** In the four hand-written operator TUs, the
backtrace line number of a failing host-side argument check changes. The
deleted macro lines shift the host section, and in the MLP and FC1 +
SwiGLU TUs the header moves shift it too. Message texts, exception
kinds, exports and device code do not change.
- **One rebuild on an existing JIT workspace.** Module names stay the
same. The 21 varlen modules rebuild once because their recorded header
dependencies name the deleted package copies. The 7 operator modules
rebuild once because their sources changed. A fresh workspace is not
affected.
- **Direct clang-format calls.** Calling clang-format directly on a file
in the two formerly stubbed directories now uses the repository style.
The hooks continue to skip these directories through the top-level
exclude.
- **Nothing else.** No reachable input changes a launch, an argument, a
route, an export, a module name or a test result.

## Changes

Base: upstream main `da992ed99` (2026-10-21). Head:
`1a9709616d5047927fd7ee7a59611f26f3e366b7` (4 commits). 39 files, +829 /
-2,598 (3 added, 32 deleted, 4 modified).

- **Family.** The MiniMax-H3 code for SM100 (compute capability 10.0)
and SM103 (compute capability 10.3). This PR touches:
- the varlen attention package
`flashinfer/experimental/minimax_h3_varlen_attention`. Its registry
(exporter output) has 11 programs, which make 21 (program, architecture)
JIT modules: 11 on SM100 and 10 on SM103, one kernel each;
- the hand-written single-source MLP block
`csrc/cake_minimax_h3_mlp_sm10x.cu` (`minimax_h3_mlp`, `_mxfp8`,
`_nvfp4`), with modules `minimax_h3_mlp_sm100a_v1` / `_sm103a_v1` and 9
kernels;
- the hand-written single-source FC1 + SwiGLU
`csrc/cake_minimax_h3_fc1_swiglu_sm10x.cu` (`minimax_h3_fc1_swiglu`,
`_mxfp8`, `_nvfp4`), with one module per target and 6 kernels;
- the hand-written single-source output projection
`csrc/cake_minimax_h3_out_proj_sm10x.cu` (`minimax_h3_out_proj`,
`_mxfp8`, `_nvfp4`), with one module per target and 5 kernels;
- the hand-written `csrc/cake_minimax_h3_bf16_pre_attention_sm103a.cu`
(`minimax_h3_bf16_pre_attention`), with one module,
`minimax_h3_bf16_pre_attention_sm100a_sm103a_v1`, built for both
targets, and 2 kernels;
- the generated directories `csrc/cake_minimax_h3_nvfp4_pre_attention`
and `csrc/cake_minimax_h3_qkv_quantize_pack`. The only change there is
the deletion of their `.clang-format` stubs. Their sources, loaders and
tests are unchanged.

This PR does not touch the sibling directory
`csrc/cake_minimax_h3_mxfp8_pre_attention`.
- **Unchanged.** No Python file changes. Loaders, registries, module
names, kernel symbols, exported entry points, launch parameters,
dispatch, the public APIs, the tests, the benchmarks, the docs and the
pre-commit configuration are byte-identical to the base.
- **Device code.** Every change is mechanical and preserves behaviour
for every input. No kernel's device code changes:
- the gates compile both sides to identical SASS from the same compile
definitions;
- the preprocessed texts match after the declared normalisation (see
Validation).
- **Generated files.** No exporter-generated file is edited (two are
deleted). No "do not edit" file is edited. No disclosure line is added:
the three new headers carry an ordinary header comment.

### Commit 1 (8647cdb8b) - cake_minimax_h3: drop vendored helper copies
of the varlen package (30 files, +0 / -904)

- **Duplicates.** The varlen package vendored 32 device-helper headers
under
`flashinfer/experimental/minimax_h3_varlen_attention/csrc/cake_device_helpers/`.
30 of them duplicate the repository headers of the same name in
`csrc/cake_device_helpers/`, which has 81 files and is unchanged. Each
pair is token-identical: the repository copy differs only in
indentation, line wrapping and comment text.
- **Deleted.** The 30 package copies are deleted. The two helpers that
have no repository copy, `make_sf_cp_desc_lo_sbo256` and
`mma_ts_step_cg2`, stay in the package.
- **Resolution.** No include line changes:
- The package's device preamble,
`cake_minimax_h3_varlen_attention_device_common.cuh`, is the only
reader. It has 32 quoted includes of the form
`"cake_device_helpers/<name>.cuh"` and does not change.
- The loader's include list puts the package csrc directory first and
the repository csrc directory after the package directories. Each quoted
include therefore now resolves to the repository copy.
  - No helper uses `__FILE__` or `__LINE__`.
- **Unchanged:** the registry, module names, closure digests, launch
parameters, tests and docs.
- **Wheel.** The wheel ships the repository `csrc/` as package data but
not the package's own `csrc/`. After this commit, the 30 helpers can
therefore also be resolved from an installed wheel. The rest of the
package's `csrc/` content is a separate packaging item (see **Not in
this PR**).
- **Consequence:** none for any input. The token stream is the same,
from another path, and so are the 21 kernels and their SASS (see
Validation). An existing JIT workspace rebuilds the 21 varlen modules
once, because the dependency records that ninja kept for them name the
deleted package copies.

### Commit 2 (4852cd311) - cake_minimax_h3: drop two redundant
.clang-format stubs (2 files, +0 / -4)

- **Stubs.** `csrc/cake_minimax_h3_nvfp4_pre_attention/.clang-format`
and `csrc/cake_minimax_h3_qkv_quantize_pack/.clang-format` were two
identical two-line files (`DisableFormat: true` / `SortIncludes:
Never`). They were added with the generated NVFP4 pre-attention and QKV
quantize-and-pack sources.
- **Redundant.** The top-level exclude of `.pre-commit-config.yaml`
already names both directories, so every hook, including clang-format,
skips every file in them. The stubs repeated that exclusion. The same
line excludes the family's sibling MXFP8 pre-attention directory, which
never had a stub.
- **Readers.** Nothing reads the two files: no test, script, CI
configuration, manifest or document names them. Apart from the stubs,
the two directories are byte-identical to the base, with 6 and 17 files
remaining.
- **Consequence:** none for the hooks. pre-commit on both full checkouts
gives identical per-hook results and leaves both trees clean (see
Validation).
- **Disclosed:** if clang-format is called directly on a file in these
directories (for example from an editor, not through the hooks), it now
uses the repository style instead of a disabled one. This is already how
it behaves for the MXFP8 directory.

### Commit 3 (20fd9346a) - cake_minimax_h3: drop unreferenced macros
from the single-source TUs (4 files, +0 / -224)

- **Unused macros.** The four hand-written single-source operators
define object-like macros that they never use. There are 84 distinct
names in 112 definitions: 23 in the MLP TU, 25 in FC1 + SwiGLU, 38 in
the output projection and 26 in the BF16 pre-attention. For each of
these definitions, the macro name is tokenised on no other line of its
translation unit and in none of the repository headers that the unit
includes.
- **Deleted.** Those `#define` lines and their `#undef` partners are
deleted: 224 lines, 46 / 50 / 76 / 52 per TU. No other line changes: no
line is re-wrapped and no blank line changes.
- **TU lengths at head:**
- MLP 6,838 → 6,062 and FC1 + SwiGLU 3,794 → 3,014 (these include commit
4);
  - output projection 3,090 → 3,014;
  - BF16 pre-attention 1,454 → 1,402.
- **Disclosed:**
- A macro that is never expanded emits no token, so device and host code
are the same text after preprocessing (the gates prove this).
- The only difference is the line number that a failing host-side
argument check reports in its backtrace. The deleted lines sat above the
host section, which has 38 / 35 / 36 / 27 check sites per TU. Message
texts, exception kinds, exports and device code are unchanged.
- An existing JIT workspace rebuilds the 7 operator modules once, under
their unchanged names. These are the MLP, FC1 + SwiGLU and
output-projection modules on each target, and the BF16 pre-attention
module.

### Commit 4 (1a9709616) - cake_minimax_h3: move the norm+AdaLN kernels
into shared headers (5 files, +829 / -1,466)

- **Duplicate.** The MLP TU and the FC1 + SwiGLU TU each had a
byte-identical copy of the three RMSNorm + indexed AdaLN kernels:
  - `kernel_minimax_h3_norm_adaln_bf16` (BF16 output);
- `kernel_minimax_h3_norm_adaln_mxfp8` (MXFP8 activation quantization);
- `kernel_minimax_h3_norm_adaln_nvfp4` (NVFP4 activation quantization).

That is 733 lines duplicated between two hand-maintained translation
units.
- **Headers.** Each kernel now lives once, in
`csrc/cake_minimax_h3_norm_adaln_{bf16,mxfp8,nvfp4}_sm10x.cuh` (220 /
308 / 295 lines). Each header holds the kernel's helper compile-time
constants, the `extern "C"` kernel and the matching undefinitions,
behind an `#ifndef` include guard.
- **Position.** Both TUs include each header exactly where the kernel
used to be: MLP lines 254 / 1,960 / 3,511 and FC1 + SwiGLU lines 238 /
804 / 1,547. As a result, declaration order, linkage, the lifetime of
every macro and every kernel symbol are unchanged. The constants that
are specific to each TU stay in place around the include.
- **Reach.** The headers sit next to the TUs in `csrc/`, and the
loaders' include list already has `csrc/`. The loaders, the source tree
and the wheel therefore reach the headers the same way as before.
- **Unchanged:** the symbols of the 9 MLP kernels and the 6 FC1 + SwiGLU
kernels.
- **Consequence:** none for any input. The 15 kernels are the same and
have the same SASS per target. The preprocessed texts are identical
after dropping line markers and blank lines. The only shift is in the
line numbers of the host check sites: the same disclosure as commit 3,
for the same two TUs. The MLP and FC1 + SwiGLU modules rebuild once on
an existing JIT workspace. They are already counted in commit 3's seven
modules.

## Validation

The compile-only rows (device gate and host gate) are compiled on one
node with one CUDA toolkit for both architectures. Each row's result
gives the toolkit version. The GPU rows run on a B200 (SM100, compute
capability 10.0) and a GB300 (SM103, compute capability 10.3).

- Device gate, 65 rows (every kernel this PR re-spells or re-resolves,
per architecture: the 21 varlen kernels, one per (program, architecture)
module, compiled from the unchanged kernel source with the helpers
resolved from the package copies at the base and from the repository
headers at head; the 5 output-projection and 2 BF16 pre-attention
kernels on SM100 and SM103 after the macro deletions; and the 9 MLP and
6 FC1 + SwiGLU kernels on SM100 and SM103 after the macro deletions and
the header moves; cubin + SASS + preprocessed text): all 65 rows
identical on both sides (33 SM100 rows, 32 SM103 rows, from 29
translation-unit builds per side: 15 SM100 and 14 SM103, each compiled
on one node with one CUDA 13.4 toolkit): cubin sha256 equal, SASS
identical for every kernel symbol, resource usage identical and exactly
the expected function set in all 29 of 29 builds, no fallback rule used;
the preprocessed texts match by the declared rule on every row: the 21
varlen rows are token-identical (0 differing tokens, 21 of 21; the only
line-wise difference is the re-indent / re-wrap of the repository helper
copies, and the whitespace-free streams are identical on all 29 builds)
and the 8 operator rows are identical after dropping line markers, blank
lines and the check macros' file / line arguments, with the shifted
check-site lines equal to the TU's own check sites on both sides (38 /
35 / 36 / 27 for the MLP, FC1 + SwiGLU, output-projection and BF16
pre-attention TUs, 8 of 8).
  - **Rows.** Each row compares the TU at the base with the TU at head.
- **Compilation.** Both sides are compiled with the loader's exact
compile definitions and include order, from one staged path, in one
environment.
  - **Pass criteria.** A row passes when all of these hold:
    - the cubin sha256 is equal;
    - the SASS is identical per kernel symbol;
    - resource usage is identical;
    - each side has exactly the expected function set;
- the preprocessed texts pass the rule for their row. Varlen rows must
be token-identical (0 differing tokens); their only line-wise difference
is the re-indent / re-wrap of the repository helper copies. Operator
rows must be identical after dropping line markers, blank lines and the
file / line arguments of the check macros. The number of changed
check-site lines must equal the TU's check sites (38 / 35 / 36 / 27).
- Host gate, 29 rows (the 21 varlen (program, architecture) builds and
the four operator TUs on SM100 and SM103, preprocessed on both sides
with the loader's compile definitions): all 29 rows pass (15 SM100 rows,
14 SM103 rows; the same CUDA 13.4 toolkit): the 21 varlen rows are
token-identical (0 differing tokens, 21 of 21) with identical
whitespace-free streams, the line-wise difference being the recorded
re-indent / re-wrap (189 / 177 changed lines on the rows that report it,
against the 182 / 170 the gate had declared as an informational
estimate; the token stream is the verdict); the 8 operator rows are
identical after the declared normalisation (line markers, blank lines,
the check macros' file / line arguments; the blank-line class was needed
on 6 of them), no adjacent-literal join or any other class was needed,
the shifted check-site count equals the TU's own sites on both sides (38
/ 35 / 36 / 27, 8 of 8, 0 mismatched), and every kernel symbol is
present in the preprocessed candidate text.
- **Varlen rows (21).** These must be token-identical after dropping
line markers and blank lines. The declared line-wise re-wrap is
recorded.
- **Operator rows (8).** These must be identical after the declared
normalisation, which covers:
    - line markers and blank lines;
    - the file / line arguments of the check macros.

No adjacent-literal join is needed. The number of shifted check sites
must equal the TU's own sites, and every kernel symbol must be present
on both sides.
- Module build and load through the real loaders (the 11 varlen modules
+ the 4 operator modules on B200, the 10 varlen modules + the 4 operator
modules on GB300; both trees, fresh JIT workspaces): every module builds
through its loader and loads with every entry point callable on both
trees (15 of 15 on B200, 14 of 14 on GB300, each tree in a fresh JIT
workspace); for every module the exported symbol set and the device
kernel set equal the base-tree module's (15 / 15 on B200, 14 / 14 on
GB300), the varlen registry yields the same module list on both trees
(11 and 10 (program, architecture) modules), and every module carries
exactly its expected kernels (1 per varlen module; 9, 6, 5 and 2 for the
MLP, FC1 + SwiGLU, output-projection and BF16 pre-attention modules).
- Each module must be built by its loader (for varlen, the registry's
own generator per (program, architecture); for the operators, the four
loaders), and it must load with every entry point callable.
- Each module's exported symbol set and device kernel set must be
identical to those of the base-tree module.
- Bitwise before / after (torch.equal) on B200 and GB300: the MLP block
over 4 row counts and 3 variants (12 cells), FC1 + SwiGLU over 4 row
counts and 3 variants (12 cells), the output projection over 4 row
counts, 4 sequence-parallel degrees and 3 variants (48 cells), the BF16
pre-attention over the 4 smoke shapes plus one production shape (5
cells); seeded inputs built with the tests' own helpers and shared by
both trees: bit-exact: 12 / 12 MLP cells, 12 / 12 FC1 + SwiGLU cells, 48
/ 48 output-projection cells and 5 / 5 BF16 pre-attention cells equal on
B200 (CC 10.0) and again on GB300 (CC 10.3), 77 of 77 on each device, 0
differing; the NVFP4 intermediates of the FC1 path (the FC1 output, the
global scale and alpha) are identical as well (4 / 4 on each device,
informational).
- Tests on B200 and GB300 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: identical results on both trees on
each device: on B200 and on GB300 the varlen attention file 653 passed,
the QKV quantize-and-pack file 74 passed, the NVFP4 pre-attention file
22 passed, the MXFP8 pre-attention file 19 passed, the MLP file 27
passed, the FC1 + SwiGLU file 22 passed, the output-projection file 61
passed, the BF16 pre-attention file 50 passed / 44 skipped (exactly the
environment-gated full-correctness items), 0 failed anywhere; with CUDA
hidden, on both devices and both trees, the four operator files give 2
passed / 25 skipped, 1 / 21, 2 / 59 and 31 / 63 and the host-side
subsets of the varlen, MXFP8 and QKV files pass (7, 4 and 9 items); the
skipped id sets are identical on both trees in every cell. One run was
repeated: the base tree's MXFP8 file on B200 first hit a transient
filesystem fault (stale file handle in 15 fixture setups / teardowns)
while this branch's run of the same file had passed 19 / 19 minutes
earlier; the repeat of both pre-attention files on both trees gave 22 /
22 and 19 / 19 each.
  - **The eight files:**
- `tests/experimental/test_cake_minimax_h3_varlen_attention.py` (653
items);
    - `tests/test_minimax_h3_qkv_quantize_pack.py` (74 items);
    - `tests/test_minimax_h3_nvfp4.py` (22 items);
    - `tests/test_minimax_h3_mxfp8.py` (19 items);
    - `tests/diffusion_ops/test_minimax_h3_mlp.py` (27 items);
    - `tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py` (22 items);
    - `tests/diffusion_ops/test_minimax_h3_out_proj.py` (61 items);
- `tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py` (94 items:
50 run, and the 44 items of its full-correctness shape list skip by the
file's own environment gate).
- **Both trees.** The passed / skipped / failed counts and the skipped
ids must be identical on both trees.
- **CUDA hidden.** On both trees, the four operator files run in full,
with these expected skipped / passed counts: MLP 25 / 2, FC1 + SwiGLU 21
/ 1, output projection 59 / 2, BF16 pre-attention 63 / 31. The host-side
subsets of the varlen, QKV and MXFP8 files run as well.
- CPU checks: all pass: pre-commit on both full checkouts gives
identical per-hook results (16 hooks: 15 passed, 1 skipped on each tree)
and an empty patch on each (0 bytes), and 0 failed hooks on the 7 added
/ modified files; all 16 hooks skip every one of the 23 remaining files
of the two formerly stubbed directories on both trees; every
stale-reference search returns its expected count (the 30 deleted helper
copies each have a token-identical repository twin, 30 / 30, and only
the unchanged device preamble names them with its 32 quoted includes on
both trees, 0 path references to the package helper directory; the two
stub paths are named nowhere; the 112 deleted macro names hit 0 times in
their TUs at head against 46 / 50 / 76 / 52 definition and undefinition
lines at the base; the three header names appear only in the two
including TUs); no 'do not edit' line in any of the 7 touched files; the
four edits re-applied to a snapshot of the base reproduce all 39 changed
paths byte for byte and a second application of each edit is refused
without writing; the gate tables regenerate identically from the branch;
collection is identical on both trees (653 / 74 / 22 / 19 / 27 / 22 / 61
/ 94 ids) and the CUDA-hidden runs match on both trees (2 / 25, 1 / 21,
2 / 59, 31 / 63 passed / skipped for the four operator files; 7 / 9 / 4
passed for the varlen, QKV and MXFP8 subsets); the four commit messages
match their records.
- pre-commit on both full checkouts, which must give identical per-hook
results and an empty patch, and on the 7 added / modified files.
- On both trees, every hook must skip every remaining file of the two
formerly stubbed directories.
  - Stale-reference searches, each with an expected count:
- the 30 deleted helper names: referenced only by the unchanged device
preamble;
    - the two stub paths: referenced nowhere;
- the names of the 112 deleted macro definitions: nowhere in their own
TUs;
    - the three header names: only in the two TUs.
  - No touched file contains "do not edit".
- Re-applying the four edits to a snapshot of the base must reproduce
the branch byte for byte.
  - Test collection must be identical on both trees.
  - Commit message checks.

**Not run.** By design, this PR's validation does not run the following.
Each item gives its proof of record.
- **The 44 shapes of `test_blackwell_full_correctness`** in
`tests/diffusion_ops/test_minimax_h3_bf16_pre_attention.py`.
- The file gates them behind an environment variable by design, and they
skip identically on both trees.
- The smoke shapes always run. Together with the bitwise comparison
above, which includes one production shape, they cover the kernel that
this PR touches.
- **H100 / SM90.** No kernel of this family serves SM90: the varlen
registry and the four operator loaders accept only compute capability
10.0 and 10.3. Nothing in this PR executes there.

Experimental test scope for CI:

```experimental-tests
tests/experimental/test_cake_minimax_h3_varlen_attention.py
```

## Not in this PR

- **The two package-only helpers, the shared host-common header and the
DeepGEMM notice.** This covers moving `make_sf_cp_desc_lo_sbo256` and
`mma_ts_step_cg2` into the repository helper directory, the header and
the notice. These are cross-family exporter territory and are left to
the exporter owners.
- **Shipping the package's own `csrc/` in the wheel** (the kernel /
binding sources and the two kept helpers). It is not package data today,
which makes it a packaging item for the package owner. This PR only
makes the 30 shared helpers resolvable from the wheel's repository
`csrc/`.
- **The unreferenced macros in the family's exporter-generated files**
(the varlen kernel TUs and the QKV, NVFP4 and MXFP8 pre-attention
sources: 408 lines). This is exporter output, so it is edited only
through the exporter, in a second tranche.
- **The 17 other duplicated helper blocks shared by the operator TUs**,
beyond the three norm + AdaLN kernels. They are for a second header
tranche, once this PR's kernel headers are in.
- One shared header for all four TUs was considered and rejected. It
would add 3 kernel symbols to the output-projection and BF16
pre-attention TUs and reorder every TU.
- Only this PR's position-preserving form keeps the preprocessed text
identical.
- **The QKV quantize-and-pack clone fold over the heads-per-destination
constant, and the BF16 pre-attention retrace fold.** Both depend on a
decision about runtime parameters for the generated sources, so they are
for a second tranche.
- **Behaviour or timing changes.** These are left for separate PRs, each
with a benchmark gate or a per-item A/B of the host path. Each one
changes something observable: an allocation count, an error text or the
kwargs. They are:
- the dense / split attention program folds. Dropping the dense NVFP4
pair is a performance decision: the split programs measure 1-3 % slower
on the dense shapes;
  - descriptor caching;
  - the plan cache / shared setup;
  - the per-call host overhead;
- the remaining host-path items: identity checks, `zero_()` calls,
workspace allocations, strides, API kwargs, a shared base class and
debug outputs.
- **The dense-attention loader's `_SUPPORTED_MAJOR_VERSIONS = [9, 10,
12]`**, and whether it should build only for major 12. The SM120 sibling
PRs own this list (#6906, #6541 add the SM120 dense-attention source),
and changing it here would conflict with them. The decision comes after
they merge and after the usage check that the issue asks for.
- **The `*_KWARGS` tables of the generated loaders**, which can be
derived from `arg_plan`. They hold the same values, but the explicit
tables are the exporter's self-check: the equality is the check. They
are not deleted.
- **The `PROGRAMS` / `CakeProgram` factoring of the generated QKV
loader.** The loader is "do not edit" exporter output, and its test pins
8 module-level names by identity. A compact form has to come from the
exporter.
- **The same-file-only names** (`_fake` functions, `BF16SegmentPlan`,
`_partial_workspace`, `combine_kwargs`, `PackedSegmentPlan`). They are
referenced in their own file or registered as fake ops, so they are not
dead code and there is nothing to delete.
- **The MXFP8 runtime row-count variant and the static BF16 route
table.** The route table is owned by the export and is kept as is. The
runtime variant is a design change.
- **Sharing Python-side helpers between the operator hosts, and the API
cleanup** (duplicate wrappers; the obsolete output-projection reference
path was already removed before this base). These are not mechanical and
are owner decisions.
- **Test-file merges and the BF16 test file rename.** These are
coordination items. This PR keeps the test inventories byte-identical.
- **The NVFP4 workspace-size helper `nvfp4_workspace_bytes`.** It is a
public name of an experimental module with zero references across the
repository. Removing it is an owner decision, so it is not deleted here.
- **The 14 other `.clang-format` stubs** of other families, covered by
the same top-level exclude line (4 of them are documented by their
READMEs, none is named by any manifest), get the same mechanical
deletion in each family's own round.
- **Exporter requests**, which are requests rather than PR changes. They
are addressed to the exporter owners in the issue comment:
- stop vendoring repository helper copies into exported packages, and
resolve them from `csrc/cake_device_helpers`;
- emit no `.clang-format` stub for a directory that the top-level
exclude already covers;
  - emit only the macros that a translation unit uses.

Part of #6667

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Consolidated normalization and activation-quantization implementations
into dedicated kernel components.
* Simplified GPU execution configurations and scale-buffer handling
while preserving existing model operator entry points.
* Retained BF16, MXFP8, and NVFP4 processing paths, including indexed
AdaLN behavior and quantized outputs.

* **Chores**
* Removed obsolete generated GPU helper components and unused
configuration definitions.
* Removed local formatting overrides from selected GPU kernel
directories.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2995461](https://github.com/flashinfer-ai/flashinfer/commit/2995461e872e030b364a1a84d8ca94181f857876)

- **作者**: Yang Xu
- **时间**: 2026-10-21T18:40:01Z
- **提交信息**: feat(moe): add unified Frost low-latency MoE backend (#6626)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add an opt-in `frost_low_latency` backend to the unified `MoELayer` API for tiny routed batches on SM100, SM103 and SM107. It supports MXFP4/MXFP8 weights with MXFP8 activations and SwiGLU, plus unquantized BF16 weights/activations with ten typed activations. Output is BF16; routing is precomputed.

Expert IDs directly address weights. MX has low-latency Tensor Core and scalar FMA tactics sharing prepared weights and one activation/quantization/combine contract. The FMA device bodies previously embedded in `cudnn_frost` now have one owner, with compatibility adapters preserving legacy entry points and numerical behavior. The TC pipeline builds on FlashInfer's existing low-latency blockscaled GEMM and uses PDL; it remains multiple kernels.

BF16 reuses the shared FMA kernels, fuses activation into FC1 and finalized combine into FC2, and tunes FC1/FC2 output widths independently across 16 combinations. Its BF16 intermediate/expert outputs and ordered separate FP32 multiply/add remain distinct from the MX contract. Supported BF16 activations are SwiGLU, SiTU, GeGLU, GeGLUTanh, SwiGLUStep, GELU, ReLU, ReLU2, SiLU and Identity. SwiGLU alpha/beta/limit and SwiGLUStep limit can vary; SiTU requires default scales.

Frost uses the existing FlashInfer autotuner and `MoELayer` selection policy. The generic individual-call graph timer and its MoE policy integration are deferred to separate autotuner work; this PR does not modify `flashinfer/autotuner/` or `tests/autotuner/`. Prepared native backends remain candidates for less favorable shapes. Default token admission is T≤2; users can explicitly configure up to T=8. This candidate is not added to the default backend list.

### B300 BF16 kernel GPU time

These are benchmark-selected, fixed-tactic measurements from the recorded pre-split revisions. The split preserves device kernels and numerical contracts, but ordinary autotuning can choose different tactics; these numbers are not a guarantee for the default automatic selection. The benchmark scripts retain their independent event timing and tactic sweeps.

| Activation | H / I / E / K | T | Cache / reuse | Fastest tested original | Original µs | Frost µs | Speedup |
|---|---|---:|---|---|---:|---:|---:|
| swiglu | 2048 / 512 / 512 / 10 | 1 | warm / disjoint | trtllm_default | 27.736 | 15.460 | 1.794× |
| swiglu | 2048 / 512 / 512 / 10 | 2 | warm / disjoint | trtllm | 44.144 | 31.872 | 1.385× |
| situ | 2048 / 1408 / 64 / 6 | 2 | warm / disjoint | cutlass | 60.424 | 46.056 | 1.312× |

Each row uses the same GPU, shape, activation, cache and expert reuse. These are complete local routed-MoE GPU calls, including adapters/combine, not model throughput or distributed communication. For SwiGLU the admitted native set is TRT-LLM, CUTLASS, Prims-TS and cuDNN grouped GEMM; SiTU admits only CUTLASS on this B300/software configuration. The benchmark searches their runner-advertised tactics and defaults, freezes selection, then validates in separate normal/reverse processes with independent A/A controls. Only qualified comparisons are shown; the full backend set is recorded per case and is not an all-FlashInfer optimum claim.

The separate clamped-SwiGLU MX cohort established B300 gains of 1.608× for W4/T1 (native CuTe default 21.616 → Frost 13.440 µs), 1.472× for W4/T4 (TRT 31.852 → 21.632 µs, without native CuTe in that qualified cohort), and 1.257× for W8/T4 (TRT 40.008 → 31.816 µs). Do not mix these ratios with the BF16 cohort. Usage, diagrams, scripts, numerical contracts, exact candidate sets and exclusions are in [the guide](https://github.com/YangXu1990uiuc/flashinfer/blob/9800c0797cf53c052da08ef88e93a8c630f646b1/docs/frost_low_latency_moe.md), [BF16 evidence](https://github.com/YangXu1990uiuc/flashinfer/blob/bfba3cee8c6c8b0158f8244c316b5da89c191ff0/docs/frost_low_latency_bf16_b300.json) and [the broader MX evidence](https://github.com/YangXu1990uiuc/flashinfer/blob/bfba3cee8c6c8b0158f8244c316b5da89c191ff0/docs/frost_low_latency_b300_native.json).


## 🔍 Related Issues

Follow-up work on the low-latency routed-MoE backend and shared legacy FMA implementation.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit` (or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] Changed-file hooks passed for the complete local batch, following the repository self-review guidance.

> If you are unsure about how to set up `pre-commit`, see [the pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- Split revision `9800c0797`: **290 host tests passed / 5 skipped**, covering unified MoE registration, pack contracts, per-call packing during selection, compiler gates and autotuner config serialization. Changed-file pre-commit passed.
- `flashinfer/autotuner/` and `tests/autotuner/` now match upstream `140f9fc4c` exactly. `MoELayer._select_winner` also matches upstream; its remaining changes only register Frost. All **169 backend files other than the host runner** are byte-identical to pre-split `50d7fcc7e`.
- No local CUDA device is available for this split. The cache-v2 tests that query CUDA capture state cannot execute on this host; they are included in the requested GPU CI scope. Real cross-backend tuning, changing-input graph replay and BF16 native-fallback tests remain in the PR.
- [Targeted public CI for this split](https://github.com/flashinfer-ai/flashinfer/actions/runs/39644707426) is running on `9800c0797`. The preceding run on `50d7fcc7e` was cancelled after the user requested extraction; it does not validate this split.

Historical GPU validation at pre-split `bfba3cee8` (unchanged device kernels, different host selection policy): B300 **244 passed / 12 skipped**, SM107 **248 / 8**, independent local B200 **242 / 8**, and [hosted GB300 / DSL 4.8](https://gitlab-master.nvidia.com/dl/flashinfer/flashinfer-ci/-/jobs/494701007) **242 / 8**. All 46 BF16 cases executed on those target architectures. B300 memcheck and synccheck each covered 32 output-contract cases with **0 device errors** (API-error reporting disabled). These historical runs do not certify the new automatic selection policy.

The [earlier public CI](https://github.com/flashinfer-ai/flashinfer/actions/runs/39128385480) passed H100 **182 / 68**, six x64/arm64 AOT build/import jobs and its summary. H100 skips unsupported device cases and does not qualify BF16 GPU execution.

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

- No public API removal; the BF16 weight helper is additive. Legacy kernel adapters retain their original signatures, defaults and numerical contracts.
- Local expert compute only: TP slices are supported; EP sharding/communication, router selection and shared experts are outside this backend.
- CUDA Graphs require warmup. Each call owns scratch; compiled caches contain executables and metadata, not bound input pointers.
- Winner caches do not track changing expert-ID values. Tune representative route distributions and retain prepared native fallbacks. Cross-backend TRT inputs require unique top-k IDs within each token.
- CuTe DSL >=4.8 is checked before kernel import. GELU/GeGLU additionally require compiler erf support.
- Default BF16 FC1/FC2 widths remain 1/4; measured gains from other widths are obtained by tuning. MX default remains TC128.
- Shared individual-call timing is deferred. Frost cache identity is advanced to avoid consuming winners from that timing mode. Device kernels, default tactics and numerical contracts are unchanged by the split; fresh automatic selection may pick different tactics.

### [a509a27](https://github.com/flashinfer-ai/flashinfer/commit/a509a27181cbbc22887384c8780cbd5e6bc7b7ca)

- **作者**: eigen
- **时间**: 2026-10-21T18:39:44Z
- **提交信息**: deslop(cake_small_gemms): fold router and BMM clones, share quantized-base LoRA bindings, hoist PROGRAMS (#6946)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of three of the four small Cake GEMM
families tracked in #6666. They are the Cake router GEMM, the Cake BF16
batched GEMM behind `bmm_bf16(backend="cake")`, and the quantized-base
LoRA GEMM behind `mm_fp8_lora` / `mm_nvfp4_lora`. The five mechanical
commits do the following:
- hoist the repeated values of the quantized-base LoRA program table
into constants;
- fold the 32 router sources onto one shared body;
- fold 32 of the 34 BMM sources onto six bodies;
- fold the two quantized-base LoRA hint kernels onto their partners;
- share one quantized-base LoRA launcher per family through compile
definitions.

Device code, kernel symbols, module names, dispatch rules, launch
geometry, exports and test inventories do not change. One test assertion
is updated in commit 5. The NVFP4 SVDQuant package is not touched.

Behaviour changes:
- **Host backtraces.** For the six re-pointed quantized-base LoRA
programs, the backtrace text (file / line) of a failing host check
changes: it now names the shared launcher. Message texts, exception
kinds, exports and device code do not change.
- **One rebuild for the changed modules.** Some JIT modules have changed
sources or compile definitions: the router module, the two BMM modules
and 14 of the 18 quantized-base LoRA modules. On an existing JIT
workspace, these rebuild once under their unchanged names.
- **Nothing else.** No reachable input changes a launch, an argument, a
route, an export, a module name or a test result.

## Changes

Base: upstream main `edfb3f7f8`. Head:
`65dbd71d4b795a419d39bc8b2111a540b43663bf` (5 commits). 89 files, +2,759
/ -19,641 (7 added, 8 deleted, 74 modified).

- **Families.** This PR touches three generated families:
- `csrc/cake_router_gemm`, the Cake router GEMM. It has one JIT module,
`cake_router_gemm`, and 32 kernels,
`kernel_cake_blackwell_router_gemm_m<1..16>_k<6144|7168>`. They are
served on SM100 / SM103 through `mm_M1_16_K7168_N128`,
`mm_M1_16_K7168_N256` and `mm_M1_16_K6144_N256`.
- `csrc/cake_bf16_bmm`, the Cake BF16 batched GEMM behind
`bmm_bf16(backend="cake")`. It has one module per architecture
(`blackwell_bf16_bmm_cake_sm100a` / `_sm103a`) and 34 kernels, and it is
also registered for AOT.
- `csrc/cake_quant_lora_gemm` +
`flashinfer/jit/cake_quant_lora_gemm.py`, the quantized-base LoRA GEMM
behind `mm_fp8_lora` / `mm_nvfp4_lora`. It has 11 programs in the
`PROGRAMS` table and 18 (program, architecture) JIT modules: 2 on SM90
(compute capability 9.0), 8 on SM100 (10.0) and 8 on SM103 (10.3).

The issue's fourth family, the NVFP4 SVDQuant package, is not touched
(see **Not in this PR**).
- **Unchanged:** kernel symbols, module names, shim namespaces, exported
entry points, dispatch rules, launch geometry, the public APIs and the
test inventories.
- **Device code.** Every change is mechanical and preserves behaviour
for every reachable input. No kernel's device code changes:
  - the folded bodies expand back to their former sources;
  - the preprocessed texts match after the declared normalisation;
  - the gates compile both sides to identical SASS (see Validation).
- **Disclosure.** This PR touches 80 generated files: 33 router files,
41 BMM files, 5 quantized-base LoRA sources and the Python table. Each
one now carries this line after its licence block, in place of any "do
not edit" claim, with a one- or two-line hand-edit note beside it. The
Python file uses the `#` form.
`// Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The four untouched quantized-base LoRA files keep their claim: the pair
and prepared-path bindings and the two common headers.
- **One test pin.** One assertion changes in commit 5.
`test_fp8_blackwell_tile_m_rule` pins the fields in which two FP8
Blackwell records differ. Both records now share the binding and differ
in their compile definitions, so the pin names `compile_flags` in place
of `binding` (+3 / -2 lines; no item added or removed).

### Commit 1 (531a3f475) - cake_quant_lora_gemm: hoist the shared
PROGRAMS values into constants (1 file, +400 / -1,352)

- **Duplicates.** The 11 records of `PROGRAMS` in
`flashinfer/jit/cake_quant_lora_gemm.py` repeated three values verbatim:
- the per-family dispatch constants: 3 distinct values over 11 records,
847 duplicated lines;
  - the kernel argument order: 5 distinct values, 143 lines;
  - the compile flags: 2 distinct values, 9 lines.
- **Constants.** Each distinct value now lives once in a module-level
constant above the table: 10 constants, named `_COMPILE_FLAGS_*`,
`_ARG_PLAN_*` and `_DISPATCH_*`. Every record references these constants
by name.
- **Same table.** Every record keeps every key, in the same order. The
record order is unchanged. The table's value is the same: this commit
does not change the canonical-JSON digest of `PROGRAMS` (see
Validation).
- **Readers.** Every reader takes the table by value (subscripts,
`.items()`, membership, `==`, `str()`). None compares identity, copies a
record or mutates one.
- **Header.** The table's "do not edit by hand" header is replaced by
the disclosure statement, with a note on the hand edit.
- **Consequence:** none. This is a Python-only change. The 40 host-side
table tests run identically on both trees.

### Commit 2 (4a473c13d) - cake_router_gemm: fold the 32 device sources
onto one shared body (33 files, +354 / -4,832)

- **Clones.** The 32 generated router GEMM device sources (16 token
counts × 2 hidden sizes) were clones. They were identical on their first
45 lines and differed at only twelve sites:
  - the kernel name;
- on the token count: the accumulator size, three loop bounds and one
lane test;
  - on the hidden size: the main-loop trip count and two strides;
  - three unused shared-memory defines.
- **Wrappers and body.** Each source is now a 22-line wrapper that keeps
its file name. It defines `CAKE_ROUTER_GEMM_M`, `CAKE_ROUTER_GEMM_K` and
`CAKE_ROUTER_GEMM_KERNEL_SYMBOL` and includes the new
`cake_router_gemm_device_body.cuh`. The body holds the kernel text once
and derives the trip count from the hidden size. Its `#error` guards
reject a missing or wrong definition.
- **Dead text.** The body also drops the dead text that every source
carried:
  - unused typedefs;
  - the tensor-map structs;
  - seven unused defines, and the header that they needed;
  - three unused kernel locals.
- **Unchanged:** every `extern "C"` kernel symbol, the binding, its
program table, the launch and the loader's source list.
- **Consequence:** none for any input. The kernels are the same 32
kernels with the same SASS (see Validation). The sources of the one JIT
module changed, so it rebuilds once on an existing workspace.

### Commit 3 (7623e5a10) - cake_bf16_bmm: fold 32 clone kernel sources
onto 6 shared bodies (41 files, +1,709 / -6,962)

- **Groups.** The 34 generated kernel sources fall into eight text
skeletons:
- six groups (7 / 7 / 6 / 6 / 3 / 3 sources), whose text differs only in
the kernel symbol and the shape constants;
  - two singletons.
- **Bodies.** Each group now has one body header,
`cake_bf16_bmm_body_<k>_<tile>_<predicated|full>.cuh`. It spells the
kernel symbol as `CAKE_BMM_PROGRAM_KERNEL` and the shape constants as
`CAKE_BMM_*`. The 32 member sources keep their file names and become
wrappers (licence, definitions, include).
- **Preamble.** Every source had 34 unused preamble lines. The six
bodies and the two singletons drop them; the `<cuda_fp8.h>` include
stays.
- **Binding.** Three changes:
- Three `SelectLaunch` clauses are removed. Each one's condition set
strictly contains that of a later clause that returns the same launch.
- The always-true PDL flag of `LaunchSpec` is removed, with its
never-taken `cudaLaunchKernel` branch. As a result, 34 initialisers lose
their trailing `true`.
  - The unreachable final throw is kept, with a comment.
- **Unchanged:** every kernel symbol, every surviving dispatch clause,
the launch geometry, the declarations header, the Python loader, the AOT
registration and the tests. The directory stays excluded from
clang-format as a generated artifact.
- **Consequence:** none for any reachable input:
- each removed clause selected the same kernel and launch as the clause
that now catches its shapes;
- the PDL attribute path was the only path taken before, and it is the
only path now.

  The two JIT modules rebuild once on an existing workspace.

### Commit 4 (f176e94f4) - cake_quant_lora_gemm: fold the two hint
kernels onto their partners (5 files, +142 / -3,814)

- **Copies.** The `fp8_sm90_hint` and `nvfp4_blackwell_n192h` kernel
sources were copies of their partner programs' sources (`fp8_sm90`,
`nvfp4_blackwell_n192`). They differed in a few regions:
- The SM90 hint adds two declarations and a strip-raster tile walk in
two places. It also sets different TMA L2 cache-policy operands on its
twelve loads.
- The NVFP4 hint issues its seven TMA loads with an L2 evict-last cache
hint.
- **Arms.** Each partner source now carries those regions behind
compile-definition arms (`CAKE_QLG_FP8_SM90_HINT`,
`CAKE_QLG_NVFP4_N192_HINT`). The twelve SM90 cache-policy operands read
two body-local macros, which the same arm selects.
- **Kernel symbol.** Each partner spells its kernel symbol through
`CAKE_QLG_PROGRAM_KERNEL`, which defaults to the partner's own name.
- **Deleted.** The two hint sources are deleted.
- **Table.** The hint records of `PROGRAMS` point at the partner source.
Each adds two definitions to its own compile-flag list.
- **Unchanged:** both kernel symbols, both bindings, every record key
and every dispatch rule. Each program therefore builds the same kernel
from the same text as before.
- **Consequence:** none for any input. The kernels are the same, with
the same SASS (see Validation). The two hint modules rebuild once on an
existing workspace, because each has another source file and two more
definitions. Their module names are unchanged.

### Commit 5 (65dbd71d4) - cake_quant_lora_gemm: share one binding per
family via definitions (11 files, +162 / -2,689)

- **Families.** The eleven generated host bindings formed three families
of near-identical launchers, plus two standalone bindings.
- **Kept launchers.** One launcher per family is kept and parameterised
with `#ifndef` defaults:
- the four FP8 Blackwell programs share the `fp8_blackwell_n256`
binding;
- the three raw NVFP4 programs (`n192`, `n192h`, `n256`) share the
`nvfp4_blackwell_n192` binding;
  - the two SM90 FP8 programs share the `fp8_sm90` binding.

  The other six binding files (2,638 lines) are deleted.
- **Definitions.** Compile definitions select the family member. They
set:
  - the kernel symbol;
  - the host-shim namespace;
  - the launch's dynamic shared memory;
  - the TMA box rows of the B and LORA_B descriptors;
  - the L2 promotion of the A / B / SFA / SFB descriptors.

Every default is the kept program's own value, so a launcher built
without definitions is its former self.
- **Table.** The `PROGRAMS` records of the six re-pointed programs name
the kept binding and carry their definitions. The pair and prepared-path
bindings stay as they are.
- **Exactness.** Within a family, the bindings differed only in those
tokens, so each program's launcher text is reproduced exactly. The
launch-failure message is spelled by stringising the kernel symbol, and
the compiler concatenates the pieces into identical message bytes.
- **Test pin.**
`tests/gemm/test_cake_quant_lora_gemm.py::test_fp8_blackwell_tile_m_rule`
asserts the set of fields in which two records differ: the gated record
(`fp8_blackwell_n256_clc_blocked`) and the composition record
(`fp8_blackwell_n256_m256_clc_blocked`).
- Both records now name the shared binding and differ in their compile
definitions. The set therefore names `compile_flags` in place of
`binding`.
- The test's comment now names the compile definitions as part of each
record's identity.
- The change is +3 / -2 lines, with no item added or removed. The 40
host items and the rest of the 164-item file are untouched.
- **Disclosed (host-only):**
- A failing host check is a tensor shape / stride / dtype assertion of
the launcher. For the six re-pointed programs, its backtrace text now
reports the shared binding's file name and line instead of the former
binding's. Message texts, exception kinds, exports and device code are
unchanged.
- The nine re-pointed (program, architecture) builds compile their
binding from another source file with more definitions. The five builds
of the three kept launchers compile a parameterised text. Module names
are unchanged, so an existing JIT workspace rebuilds those 14 modules
once. The four pair / prepared-path modules are untouched.

## Validation

The compile-only rows (device gate and host gate) are compiled on one
node with one CUDA toolkit for all three architectures. Each row's
result gives the toolkit version. The GPU rows run on:
- a B200 (SM100, compute capability 10.0);
- a GB300 (SM103, compute capability 10.3);
- an H100 (SM90, compute capability 9.0), for the quantized-base LoRA
SM90 programs only.

- Device gate, 143 rows (every kernel this PR re-spells, per
architecture: the 32 router kernels on SM100 and SM103 against the
former sources, the 34 BMM kernels on SM100 and SM103 against the former
sources, and the eleven quantized-base LoRA hint-fold builds: the two
SM90 FP8 programs, and the 192-wide NVFP4 program on SM100 and SM103
together with its SM100-only hint sibling, three rank instantiations
each; cubin + SASS + preprocessed text): all 143 rows identical on both
sides (72 SM100 rows, 69 SM103 rows, 2 SM90 rows; one CUDA 13.4
toolkit): cubin sha256 equal, SASS identical, resource usage identical
and exactly the expected function set in every cubin; the preprocessed
texts match by the family rule on every row (the 64 router rows differ
by exactly the removed dead declarations, the 68 BMM rows are identical
over the whole kernel region, the 11 quantized-base LoRA rows are
identical after dropping line markers and blank lines). A second device
table of 21 rows (the 9 SM100 and 12 SM103 quantized-base LoRA kernel
builds whose records gain compile definitions in commit 5, each kernel
source compiled with and without those definitions) is identical in
cubin, SASS and preprocessed text on all 21 rows, so the launcher
definitions are inert in the kernel translation units.
- **Rows.** Each row compares a kernel source at the base with the one
at head. The base side is the former file, and the head side is the
wrapper or the fold body.
- **Compilation.** Both sides are compiled with the loader's exact flag
set, from one staged path, in one environment.
  - **Pass criteria.** A row passes when all of these hold:
    - the cubin sha256 is equal;
    - the SASS is identical;
    - resource usage is identical;
    - each side has exactly the expected function set;
- the preprocessed texts pass the family's rule. Quantized-base LoRA
rows must be identical after dropping line markers. BMM rows must be
identical over the whole kernel region, where only the dropped preamble
differs. Router rows must differ by exactly the removed dead
declarations.
- Host gate, 16 rows (the 14 quantized-base LoRA (program, architecture)
launcher builds: the program's former binding at the base against the
shared launcher compiled with the program's definitions; and the BMM
binding on SM100 and SM103 against the base): all 16 rows pass (one CUDA
13.4 toolkit): no device code in any binding object; the 14
quantized-base LoRA rows are identical after the declared normalisation,
every file / line change is matched to one of the launcher's own check
sites (14 of 14 with a location) and the exported symbol sets are
identical with the own host shim and entry point present and no foreign
shim; the two BMM rows differ by exactly the declared edits (21 removed,
34 edited, 0 added, in order) with equal check-site counts, identical
exports and 34 identical undefined kernel references.
  - No binding object may contain device code.
- **Quantized-base LoRA rows (14).** The preprocessed text must be
identical after the declared normalisation, which covers:
    - line markers and blank lines;
    - adjacent string literals, joined on both sides;
    - the file / line arguments of the check macros.

The file / line changes are counted against the launcher's own check
sites. Exported symbol sets must be identical: the program's own host
shim and entry point are present, and no foreign shim is.
- **BMM rows (2).** These rows claim no identity. The preprocessed text
must differ by exactly the declared removed and edited lines: 21
removed, 34 edited, 0 added, in order. Check-site counts must be equal,
and exports and kernel references must be identical.
- Program table identity (the value of PROGRAMS through a real import,
canonical-JSON digest, base vs each commit): the 11 records keep their
count and order on every commit; the digest is 8db19e41... at the base
and after commit 1 (unchanged by the hoist), 700dd58d... after commit 4
and 6d4490f3... at head, each equal to the digest predicted from the
documented record edits alone.
  - Commit 1 must not change the digest.
- Commits 4 and 5 must change it by exactly the documented record edits:
the device file and compile definitions of the hint records, and the
binding and compile definitions of the six re-pointed records.
- Module build and load through the real loaders (router 1 + BMM 1 +
quantized-base LoRA 8 modules on B200 and on GB300, the 2 quantized-base
LoRA SM90 modules on H100; both trees, fresh JIT workspaces): every
module builds through its loader and loads with a callable entry point
on both trees (10 of 10 on B200, 10 of 10 on GB300, 2 of 2 on H100); for
every module the exported symbol set and the device kernel set equal the
base-tree module's (10 / 10, 10 / 10, 2 / 2), each quantized-base LoRA
module exports its own host shim and no re-pointed module carries the
former binding's shim.
- Each module must be built by its loader and must load with a callable
entry point.
- Each module's exported symbol set (own host shim, no foreign shim) and
device kernel set must be identical to those of the base-tree module.
- Bitwise before / after (torch.equal) on B200 and GB300: the three
Cake-served router functions over 16 token counts and both PDL settings
(96 cells) and the BMM fixed shapes over the three output types (33
cells), seeded inputs shared by both trees: bit-exact: 96 / 96 router
cells and 33 / 33 BMM cells equal on B200 (CC 10.0) and again on GB300
(CC 10.3), 0 differing.
- The H100 is not part of this row, because neither family runs a Cake
kernel on SM90 (see **Not run**).
- Tests on B200, GB300 and H100 (both the base and this branch, fresh
JIT workspaces) and with CUDA hidden: identical results on both trees on
every device: on B200 and on GB300 the router file 312 passed, the BMM
file 129 passed, the quantized-base LoRA file 160 passed / 4 skipped
(exactly the four `test_tp_nccl` items) / 0 failed; on H100 the
quantized-base LoRA file 82 passed / 82 skipped (the 78 NVFP4-gated
items and the four `test_tp_nccl` items) / 0 failed; with CUDA hidden
the 40 host-side table tests and the 10 AOT registration tests pass on
both trees; the skipped id sets are identical on both trees and nothing
fails anywhere.
  - **The three files.**
- `tests/model_optimizations/test_router_gemms.py` (312 items) and
`tests/gemm/test_bmm_bf16.py -k cake` (129 items), on B200 and GB300.
- `tests/gemm/test_cake_quant_lora_gemm.py` (the whole file, 164 items),
on H100, B200 and GB300.
  - **Expected counts for `tests/gemm/test_cake_quant_lora_gemm.py`.**
- On B200 and GB300: 160 items pass, and the four `test_tp_nccl` items
skip.
- On H100: 82 pass and 82 skip. The skips are the 78 NVFP4-gated items,
which that device does not serve, and the four `test_tp_nccl` items.
- **Both trees.** The passed / skipped / failed counts and the skipped
ids must be identical on both trees.
- **CUDA hidden.** The 40 host-side table tests and the 10 AOT
registration tests run on both trees.
- CPU checks: all pass: pre-commit on both full checkouts gives
identical per-hook results and an empty patch on each (0 bytes), and 0
failed hooks on the 80 touched files; ruff (repository configuration) is
clean on the two changed Python files; every stale-reference and
macro-placement search returns its expected count (the 8 deleted file
names are referenced nowhere, the new macros appear only in the
wrappers, bodies, launchers and the table); the disclosure line appears
exactly once in each of the 80 touched generated files and "do not edit"
survives only in the 4 untouched quantized-base LoRA files; the five
edits re-applied to a snapshot of the base reproduce all 89 changed
paths byte for byte and a second application of each edit is refused
without writing; the gate tables regenerate identically from the branch;
the table digests match the expected values; collection is identical on
both trees (312 / 129 / 40 / 10 ids) and the 40 host-side table tests
and 10 AOT registration tests pass on both trees with CUDA hidden; the
five commit messages match their records.
- pre-commit on both full checkouts, which must give identical results
and an empty patch, and on the 80 touched files.
  - Stale-reference searches, each with an expected count:
    - the 8 deleted file names: referenced nowhere;
- the new macros: only in the wrappers, bodies, launchers and the table.
- The disclosure line appears exactly once in each of the 80 touched
generated files, and no touched file contains "do not edit".
- Re-applying the five edits to a snapshot of the base must reproduce
the branch byte for byte.
  - Test collection must be identical on both trees.
  - Commit message checks.

**Not run.** By design, this PR's validation does not run the following.
Each item gives its proof of record.
- **`test_tp_nccl`**, four items of
`tests/gemm/test_cake_quant_lora_gemm.py`.
- It needs a two-process launch and otherwise skips by its own marker.
It skips identically on both trees on every device, and that is the
record for this PR.
- The tensor-parallel path shares the launchers this PR touches. The
single-GPU TP-shard tests, which do run, exercise it.
- **`tests/model_optimizations/test_router_gemms.py` and
`tests/gemm/test_bmm_bf16.py` on H100.**
- The Cake router kernels serve SM100 / SM103 only; on SM90 the router
functions use the reference kernel.
  - The BMM Cake backend admits SM100 / SM103 only.

Nothing from commits 2 and 3 executes on SM90. The record for those
commits is the SM100 / SM103 rows above.
- **The NVFP4 SVDQuant package and its tests.** No file of that package
changes.

## Not in this PR

- **The NVFP4 SVDQuant package**, which covers the issue's exact-shape
keys, the benchmark-gated variants, the Cake benchmark arm, and the
clone folds of its 15 kernels / bindings. The package converged and
re-shipped shortly before this base (#6878). Re-sealing its manifest and
hand-editing its "do not edit" bindings is not mechanical enough for
this round, so the work goes to the package owner.
- **The issue's router template form** (`template <int kNumTokens, int
kHiddenDim>` with 32 explicit instantiations in one source). This PR
uses 32 wrappers plus one body instead, so that each former source's
preprocessed text is reproduced. The template form is a declaration
change whose proof can only be SASS, so it belongs to the exporter.
- **One dead local in the router body** (`const int bid = blockIdx.x;`):
left in place for a one-line follow-up.
- **The BMM exact-shape path.** This covers deleting the 31 exact-shape
kernels, their clauses and `_KERNELS` entries, and relaxing the
exact-stride check. The fold keeps every kernel and clause. Deleting
them needs two arguments that are not measured here:
- a bitwise before / after comparison of the generic kernels at the
historical shapes;
  - the performance delta at the ten benchmark points.
- **The quantized-base LoRA hint fold as `template <bool kHints>`.**
This PR uses compile-definition arms with unchanged symbols instead,
which come with an exact text proof. The template form is an exporter
change.
- **Sharing the TMA descriptor encoders** (`EncodeTma_*`, four to eight
per launcher) through `cake_quant_lora_gemm_host_common.cuh`, which is
the rest of the binding step. Each kept launcher keeps its own encoders,
so that its preprocessed text stays identical to the former binding.
This host-text change is for a later tranche. `SetMaxDynamicSmem` is
already shared through that header at this base, so that part of the
issue's finding is obsolete.
- **Host cleanup**, which covers:
  - one router custom-op wrapper instead of three;
- the per-call TMA tensor-map re-encoding of the quantized-base LoRA and
SVDQuant launchers (four to eight encodes per call);
  - caching `_templates_for`.

These change behaviour or timing and are unmeasured. They belong in a
separate PR with a host-overhead measurement. The issue's
`cudaSetDevice` finding is obsolete at this base: both families already
gate it once per thread and device.
- **Trimming the quantized-base LoRA `PROGRAMS` schema** (dropping
unread record fields): no record field is unread at this base, so there
is nothing to remove.
- **The SVDQuant registry's `MODULES` value hoist.** The argument plans
and the logical / launch / plan blobs are value-identical across the
rank groups, which makes 518 redundant lines. That registry is rendered
by the exporter, so this is listed for the package owner and not taken
here.
- **The SVDQuant `tactic14_m64` bias / no-bias `#if` fold** (a 49-line
arm): feasible, but part of the SVDQuant tranche above, so not taken
here.
- **Generating the test table** (`CONTRACT_ROWS`): the rows are not one
regular product, because the adapter-switch and TP rows are hand-picked.
Only a partial generator is possible, so this is not taken.
- **The issue's owner decisions**: consolidating the quantized-base LoRA
prepared SVDQuant path with the SVDQuant package, and retiring or
extending the Cake router. These are decisions, not text changes.
- **Exporter requests**, which are requests rather than PR changes. They
are addressed to the exporter owners in the issue comment:
  - emit the wrapper / shared-body form for clone groups;
  - emit the per-family launcher with definitions at export time.

  Until then, the disclosure line marks the hand edits.

Part of #6666

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved GPU matrix multiplication execution across BF16, FP8, and
NVFP4 workloads through specialized shape and output configurations.
* Added shared implementations for router GEMM variants, supporting FP32
and BF16 results.

* **Compatibility**
* Expanded configurable support for quantized LoRA GEMM variants,
including specialized Blackwell and SM90 execution modes.

* **Reliability**
* Standardized kernel launching and stream synchronization behavior for
more consistent execution.

* **Maintenance**
* Consolidated duplicated kernel and dispatch configuration, simplifying
ongoing optimization and reducing inconsistencies across supported
workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c21f621](https://github.com/flashinfer-ai/flashinfer/commit/c21f621ae75ed3cf28cae7745281533e1bf78065)

- **作者**: eigen
- **时间**: 2026-10-21T18:39:14Z
- **提交信息**: perf(cake_sage): stage softmax metadata one step ahead on SM100/SM103 (#6951)

The Cake Sage-FP8 block-sparse attention backend
(`flashinfer/cake_sage_block_sparse_attention_backend`) has three kinds
of program. The first is the attention forward kernel: head_dim 128,
E4M3 Q/K/V with per-token Q scales, per-16-token K scales and
per-channel V scales, 64-row query blocks attending to selected 64-token
KV blocks (MHA or GQA), and BF16 output with optional LSE. The other two
are the fused QK quantizer with V amax (`quantize_qk_vamax`) and the V
quantizer (`quantize_v`). The attention kernel ships as one SM100/SM103
kernel and 20 SM120 specializations (RTX PRO 6000 class). This PR
updates only the SM100/SM103 attention kernel (sm_100a on B200, sm_103a
on GB300). Two warps that were idle before now load the block metadata
and K scales for each softmax step into shared memory one step early.
The softmax no longer has to wait at every step for a chain of dependent
global loads. Outputs (O and LSE) are bit-identical to the previous
version. The two quantizers and the 20 SM120 specializations are
unchanged and use the same code as before. The baseline is the previous
Cake version of this kernel on FlashInfer main, shipped by PR #6872
(`bsa_attn_sm100_blk64_fwd(..., backend="cake")`). Against that
baseline, attention is 1.01–1.03× faster on GB300 and 1.01–1.08× faster
on B200. The quantizer row is unchanged (1.00×).

Every shape uses S_q = S_k = 4096, head_dim 128, MHA and no LSE. `sel`
is how many of the 64 KV blocks (64 tokens each) each 64-row query block
selects. Q1 times the two quantizers together on B8 H32 S4096. On both
sides it reports the sum of its three launches: the zero fill of the
V-amax scratch and the two quantizer kernels. Times are CUPTI
kernel-time sums in ms (cold L2, both sides in one process, medians of
three interleaved groups). Both versions use a single launch per
attention call. Speedup = previous ÷ this PR.

**GB300 (sm_103a), CUDA 13.4**

| Shape | B | H | sel | Previous Cake (ms) | This PR (ms) | Speedup |
|---|---:|---:|---:|---:|---:|---:|
| A1 | 8 | 32 | 6 | 0.2922 | 0.2824 | 1.03× |
| A2 | 8 | 32 | 32 | 0.8459 | 0.8246 | 1.03× |
| A3 | 8 | 32 | 58 | 1.3791 | 1.3523 | 1.02× |
| A4 | 1 | 8 | 6 | 0.0154 | 0.0152 | 1.01× |
| A5 | 1 | 8 | 32 | 0.0358 | 0.0351 | 1.02× |
| A6 | 1 | 8 | 58 | 0.0558 | 0.0550 | 1.01× |
| Q1 (quantizers) | 8 | 32 | – | 0.2127 | 0.2126 | 1.00× |

**B200 (sm_100a), CUDA 13.4**

| Shape | B | H | sel | Previous Cake (ms) | This PR (ms) | Speedup |
|---|---:|---:|---:|---:|---:|---:|
| A1 | 8 | 32 | 6 | 0.3552 | 0.3288 | 1.08× |
| A2 | 8 | 32 | 32 | 1.0953 | 1.0629 | 1.03× |
| A3 | 8 | 32 | 58 | 1.8315 | 1.7916 | 1.02× |
| A4 | 1 | 8 | 6 | 0.0174 | 0.0169 | 1.03× |
| A5 | 1 | 8 | 32 | 0.0452 | 0.0443 | 1.02× |
| A6 | 1 | 8 | 58 | 0.0726 | 0.0716 | 1.01× |
| Q1 (quantizers) | 8 | 32 | – | 0.2197 | 0.2195 | 1.00× |

Apart from the 20 SM120 attention specializations, Cake ships no other
variants of this kernel, its quantizers implement only the fused Sage
recipe (Q per token, K per 16 tokens, V per channel), and the family
ships on sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Performance**
- Increased dynamic shared-memory allocation for the Sage block-sparse
attention backend.
  - Refreshed generated build metadata for supported GPU architectures.

- **Maintenance**
- Simplified internal CUDA kernel calculations and generated code
structure without changing numerical behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Hu <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7601d0b](https://github.com/flashinfer-ai/flashinfer/commit/7601d0bb7e92390aae5276951f0e4b7c8a2b5c14)

- **作者**: eigen
- **时间**: 2026-10-21T18:38:57Z
- **提交信息**: perf(cake_ssd_combined): faster sm_107a look-back chunk-parallel SSD programs (#6943)

`cake_ssd_combined` holds FlashInfer's Mamba2 SSD combined chunk-scan
kernels. The state update comes in three program kinds: exact scan,
three-phase chunk-parallel and look-back chunk-parallel. Each kind is
built for bf16, f16 and f32 state dtypes, in batched and varlen layouts.
This PR updates only the six sm_107a look-back chunk-parallel programs
(bf16/f16/f32 × batched/varlen). The baseline is the previous Cake
version of the same programs on FlashInfer main. Across the seven shapes
below, the geometric-mean speedup is 1.0215 at call level and 1.0839 for
the main kernel. The largest call-level gain is 1.196 on
perf_batched_1x256. At call level, the other six shapes range from 0.975
to 1.002.

**NVIDIA R200 (sm_107a, Rubin), CUDA 13.4.** FlashInfer call-level
latency and main-kernel time, with the look-back chunk-parallel route
forced for every shape. Speedup = previous / this PR.

| Shape | Previous (µs) | This PR (µs) | Speedup | Main kernel previous
(µs) | Main kernel this PR (µs) | Main kernel speedup |
|---|---:|---:|---:|---:|---:|---:|
| perf_batched_1x256 | 92.1 | 77.0 | 1.196 | 84.1 | 73.8 | 1.140 |
| perf_batched_4x64 | 80.3 | 80.2 | 1.002 | 83.7 | 83.4 | 1.004 |
| perf_batched_1x64 | 35.7 | 35.7 | 1.000 | 34.3 | 34.4 | 0.998 |
| perf_batched_4x16 | 34.1 | 34.3 | 0.995 | 28.8 | 25.9 | 1.114 |
| perf_batched_1x16 | 22.1 | 22.2 | 0.997 | 17.1 | 17.2 | 0.998 |
| cp_b1h32c16 | 32.2 | 33.1 | 0.975 | 28.4 | 26.0 | 1.091 |
| cp_b4h8c16 | 34.2 | 34.2 | 1.001 | 33.3 | 26.2 | 1.268 |

This PR leaves the kernel's other Cake variants unchanged: exact scan
and three-phase chunk-parallel, plus the look-back programs for sm_100a
and sm_103a (Blackwell); the family as a whole covers sm_100a, sm_103a
and sm_107a (Rubin).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated internal support for batched and variable-length
chunk-parallel operations using BF16, F16, and F32 on supported
hardware. These changes do not alter public interfaces or control flow,
and no new user-facing functionality is included.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6e04c4e](https://github.com/flashinfer-ai/flashinfer/commit/6e04c4e961ae2b649b487c98b4a548b57fc8c715)

- **作者**: Jonathan Dierksen
- **时间**: 2026-10-21T18:10:49Z
- **提交信息**: ci: run targeted A10G scopes on the bare-run shard scripts (#6953)

<!-- .github/pull_request_template.md -->

## 📌 Description

A scoped `@flashinfer-bot run <paths>` on A10G currently runs as one
`task_run_unit_tests.sh` job. That job compiles JIT kernels **one nvcc
at a
time**:

- `scripts/test_utils.sh` budgets 12 GB per nvcc plus an 8 GB reserve.
That
  budget was sized for an H100 OOM in #3078.
- On g5.2xlarge (8 vCPU, 29 GiB available) it resolves to
`MAX_JOBS=(29-8)/12=1`.
- The bare-run shard scripts `task_jit_run_tests_part{1..5}.sh` run the
same
  files on the same instances with `MAX_JOBS=nproc=8`.

Measured over all 272 `Targeted Unittest (A10G)` jobs since the lane was
added
(2026-09-04 → 2026-10-21):

- **Slowdown:** compile-heavy files run **2.6–4.5× slower** than in a
full run.
  Compile-light files are only 1.1–1.3× slower.
- **Prefill:** `test_batch_prefill_kernels.py` never finishes its first
test
  inside the runner's 2 h unit timeout.
  - 0 of 21 g5.2xlarge targeted jobs that included it have passed since
    2026-09-23.
- Each either hit the 6 h matrix timeout or reported ~1,600 never-run
nodes as
    failed.
- The only large scopes that ever passed landed on g5.8xlarge
(`MAX_JOBS=9`).
- **Cost:** 15 jobs ran out the 6 h clock, using **90 of the lane's 164
  runner-hours**.
- **Not the cause:** Docker pull and runner/collection overhead match
the full
  run to within a minute.
- **Memory is not the constraint on A10G:**
- A 9-way compile of `test_batch_prefill_kernels.py` peaked at 12.3 GiB
of
    process-tree RSS.
  - None of the 10,615 A10G part jobs (8-way compile) failed from OOM.

**Changes**

1. **Targeted A10G runs on the bare-run shard scripts.**
- `pr-test.yml` intersects the request with each
`task_jit_run_tests_partN.sh`
     separately, using `targeted_lane_scope.py`.
- It schedules a `Targeted Unittest N (A10G)` job only for shards left
with
     files.
   - Each job runs its shard script unchanged, with
     `JIT_TEST_SCOPE=<comma-separated files>`.
- The `pytest` wrapper in `scripts/jit_test_logging.sh` skips
invocations of
     files outside the scope.
- Part 1 skips its `tests/moe_ep/run_tests.sh` wrapper run whenever a
scope is
     set. That run was never targetable.
- Targeted A10G therefore inherits the shard scripts' `MAX_JOBS=nproc`,
their
     compile-group balancing, and their `-k` split of
     `test_batch_prefill_kernels.py`.
- It also uploads junit like a full run. Previously targeted A10G
uploaded
     none.
2. **Targeted T4 gets `MAX_JOBS=$(nproc)`.**
   - T4 keeps `task_run_unit_tests.sh` and gets `-e MAX_JOBS $(nproc)`.
- Its runner, g4dn.2xlarge (8 vCPU, 29 GiB), had the same `MAX_JOBS=1`
     problem.
   - `task_jit_run_tests_t4.sh` already uses `nproc`.

H100 and full (unscoped) runs are unchanged. The 12 GB default in
`test_utils.sh` is left alone; the H100 lane is the one with evidence
behind it.

**Expected effect**

Estimates come from per-shard file times in 6 recent full runs, plus
about
6.5 min of setup per job.

| Request | Before | After |
|---|---|---|
| `tests/attention` | 1 job, 6 h timeout or false failures | shards 1–5,
~52 min wall |
| `test_batch_prefill_kernels.py` | false failure at the 2 h unit
timeout | shards 3–5, ~47 min |
| `test_batch_decode_kernels.py test_sliding_window.py` | 1 job, 176 min
(run 39512581548) | shards 1–2, ~46 min |
| `tests/utils/test_topk.py` | 1 A10G job | shard 3 only |
| `tests/kda` | not scheduled | not scheduled |

## 🔍 Related Issues

- #3078 / #3030: origin of the 12 GB-per-nvcc budget, which was an H100
GDN
  prefill OOM.
- #4880: introduced the targeted lanes. #5476: per-lane scope
intersection.
- #6810: GPU-lane sccache. It edits the same "Run Test" step, so
whichever lands
second needs a small merge fix. sccache does not change Ninja
parallelism, so
  it does not address this issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on the changed files; all pass.)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

- **New test:**
`tests/test_sharding/test_a10g_shards.py::test_logging_skips_files_outside_targeted_scope`
checks that `JIT_TEST_SCOPE` runs only in-scope files and keeps their
`-k`.
  The file passes 7/7.
- **Selftest:** `targeted_lane_scope.py --selftest` passes.
- **Matrix step, run locally:** checked for the requests in the table
above.
  Each produced the expected per-shard entries.
- **Run Test step, run locally:** run against the real `ci/bash.sh` with
a stub
  `docker`.
- Targeted shard jobs get `-e JIT_TEST_SCOPE=a.py,b.py` and no
arguments.
  - Full-run shards get nothing extra.
  - Targeted T4 gets `MAX_JOBS=8`, and H100 is unchanged.
- **Not yet verified on CI.** A scoped bot run on this PR will follow.

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

- **Job names:** scoped A10G jobs become `Targeted Unittest N (A10G)`
instead
of one `Targeted Unittest (A10G)`. Nothing in the repo keys on the old
name.
- **What gets skipped:** a scoped shard runs its whole script, but every
  `pytest` invocation outside `JIT_TEST_SCOPE` is skipped and logged as
  `SKIP (outside targeted scope)`. Setup and install still run once per
  scheduled shard, at about 6.5 min each.
- **Artifacts:** scoped A10G shards upload
`junit-task_jit_run_tests_partN.sh-*`
artifacts, the same names as full runs. A scoped run and a full run
never
  share a run ID, so the names cannot collide.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved targeted GPU test runs by scheduling only relevant shards and
avoiding unrelated test execution.
* Preserved correct behavior for unrestricted test runs while ensuring
scoped runs produce results only for selected tests.
* Improved T4 test execution by automatically using available CPU
capacity inside the test environment.

* **Tests**
* Added coverage verifying that out-of-scope tests are skipped and
in-scope tests execute successfully.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [140f9fc](https://github.com/flashinfer-ai/flashinfer/commit/140f9fc4c5fea322de9de2e520e88cc1ef976d7a)

- **作者**: Haobin Guo
- **时间**: 2026-10-21T16:20:33Z
- **提交信息**: feat(quantization): add CUDA backend for masked MXFP8 grouped quantization, optionally fused with SiLU-and-mul (#6437)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds the two MXFP8 quantization steps of a masked MoE built on
`grouped_gemm_nt_masked`, for vLLM's MXFP8 MoE on the DeepEP low-latency
path, where each expert's bf16 activations come with a row count on the
device. They mirror the NVFP4 steps vLLM runs there.

- **`flashinfer.silu_and_mul_mxfp8_experts_quantize(a, mask)`** (new):
fused SiLU-and-mul + MXFP8 quantization between the two GEMMs; the
counterpart of `silu_and_mul_scaled_nvfp4_experts_quantize`.
- **`mxfp8_grouped_quantize(..., backend="cuda")`** (new): the same
kernel without SiLU-and-mul, for the GEMM1 input. The default stays
`"cutile"`.

Both need SM100+ and a contiguous, 32-byte aligned `a`, read `mask` on
the device (CUDA-graph capturable), quantize only the first
`min(mask[e], M)` rows of each expert, and write the 128x4-swizzled
UE8M0 scales `grouped_gemm_nt_masked` consumes.

**Numerics vs `cutile` / `cake`:** valid-row values and scale bytes
match bit for bit when the quantized values (`silu(gate) * up` for the
fused API) are finite, except possibly in bf16 blocks whose largest
magnitude is at most `448 * 2**-117`. Both new APIs quantize NaN and
infinities to 448, as `mxfp8_quantize` does; `cutile` and `cake` keep
NaN, so blocks that hold NaN or an infinity can differ.

### Performance

Kernel time (µs) on B200, CUDA 13.1, for DeepSeek-V3 decode under DeepEP
low-latency, EP=8: `E=32` local experts of 1024-row capacity, bf16,
`valid` rows per expert. Cold L2, one call per CUDA-graph replay, CUPTI
from first kernel start to last kernel end; SM clock locked, HBM fixed
at 3996 MHz; one process per implementation, median of 12 alternating
rounds (two jobs of 6), between-round CV ≤ 1.1% everywhere.

| step | valid | new | existing |
|---|---:|---:|---:|
| GEMM1 input `[32, 1024, 7168]`: `cuda` vs `cutile` | 16 | **5.90** |
59.17 |
| | 128 | **20.18** | 94.58 |
| Between GEMMs `[32, 1024, 2 × 2048]`: fused vs `silu_and_mul` +
`cutile` | 16 | **4.88** | 91.22 |
| | 128 | **11.70** | 99.81 |

Skewed `mask`, GEMM1 input `[32, 1024, 7168]`:

| valid rows per expert | total | `cuda` | `cake` | `cutile` (default) |
|---|---:|---:|---:|---:|
| 32 each | 1024 | **8.34** | 37.84 | 63.07 |
| 512 in one expert, 0 in the others | 512 | **5.76** | 38.42 | 30.75 |
| 1024 in one expert, 0 in the others | 1024 | **8.19** | 39.97 | 35.29
|
| 128 each | 4096 | **20.18** | 38.21 | 94.58 |
| Zipf: in proportion to `1 / (e + 1)`, 1009 in the busiest | 4096 |
**20.32** | 41.90 | 105.64 |
| 1024 in one expert, 99 in the others | 4093 | **20.03** | 40.32 |
96.00 |

The fused step also beats `silu_and_mul` + `cake`: 11.70 vs 83.65 µs at
128 each.

<details><summary>Benchmark script</summary>

```python
# bench.py <leg>: one leg per process. Driver for 6 alternating rounds:
#   for r in $(seq 6); do for leg in inq-cuda inq-cake inq-cutile mid-fused mid-unfused-cake \
#       mid-unfused-cutile; do python bench.py $leg; done; done
import statistics, sys, torch, flashinfer
from flashinfer.testing import bench_gpu_time

E, CAP, HIDDEN, INTER = 32, 1024, 7168, 2048


def zipf(total):  # largest-remainder split of `total` rows in proportion to 1 / (e + 1)
    weights = [1 / (e + 1) for e in range(E)]
    shares = [total * w / sum(weights) for w in weights]
    rows = [int(s) for s in shares]
    for e in sorted(range(E), key=lambda e: rows[e] - shares[e])[: total - sum(rows)]:
        rows[e] += 1
    return rows


masks = {
    "16 each": [16] * E, "32 each": [32] * E, "128 each": [128] * E,
    "512 + 0": [512] + [0] * (E - 1), "1024 + 0": [1024] + [0] * (E - 1),
    "1024 + 99": [1024] + [99] * (E - 1), "zipf 4096": zipf(4096),
}
inq = lambda backend: lambda a, m: flashinfer.mxfp8_grouped_quantize(a, m, backend=backend)
mid = lambda backend: lambda a, m: flashinfer.mxfp8_grouped_quantize(
    flashinfer.silu_and_mul(a), m, backend=backend)
legs = {
    "inq-cuda": (HIDDEN, inq("cuda")),
    "inq-cake": (HIDDEN, inq("cake")),
    "inq-cutile": (HIDDEN, inq("cutile")),
    "mid-fused": (2 * INTER, flashinfer.silu_and_mul_mxfp8_experts_quantize),
    "mid-unfused-cake": (2 * INTER, mid("cake")),
    "mid-unfused-cutile": (2 * INTER, mid("cutile")),
}
name = sys.argv[1]
k, fn = legs[name]
a = torch.randn(E, CAP, k, device="cuda", dtype=torch.bfloat16)
for label, rows in masks.items():
    mask = torch.tensor(rows, device="cuda", dtype=torch.int32)
    fn(a, mask)
    t = bench_gpu_time(fn, input_args=(a, mask), use_cuda_graph=True, cold_l2_cache=True,
                       enable_cupti=True, dry_run_iters=50, repeat_iters=200)
    print(name, label, statistics.median(t) * 1e3, "us")
```

</details>

## 🔍 Related Issues

#3362

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

New tests in `tests/utils/test_fp8_quantize.py` check bit-exactness
against the MXFP8 reference of `silu_and_mul(a)` and across backends,
and cover NaN and infinity against `mxfp8_quantize`, `mask` outside `[0,
M]`, 32 to 1024 experts with the rows spread or all in the first or last
expert, empty batches, rejected strided and unaligned views, a
non-current device, CUDA-graph replay after a `mask` update, and
`grouped_gemm_nt_masked` on the outputs. The existing correctness,
empty-group, int32-offset, CUDA-graph and GEMM-layout tests of
`mxfp8_grouped_quantize` also run on `cuda`.

On B200, `tests/utils/test_fp8_quantize.py`, `tests/trace` and
`tests/jit/test_aot_sm103_modules.py`: 2687 passed, 449 skipped. The two
`test_top_k_varlen_reference_correctness` cases fail to build against a
local `3rdparty/cccl` that differs from the pinned commit; this PR does
not touch top-k.

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

- `cvt_fp16_to_mxfp8_expert` quantizes with the existing
`cvt_warp_fp16_to_mxfp8` (two threads per 32-value scale block) and
supports PDL. Its one-wave grid strides over the valid rows of all
experts, so a skewed `mask` still uses every block. Each warp finds a
row's expert from a prefix sum of `mask`, kept in registers for up to 32
experts and in shared memory otherwise.
- Known limit: with every row valid, `cuda` is 18–20% slower than `cake`
on B200, e.g. 37.6 vs 31.9 µs for `[32, 1024, 2048]` and 124.6 vs 104.0
µs for `[32, 1024, 7168]` (kernel only, preallocated outputs, same
clocks and rounds as above).
- The module builds with `-use_fast_math`, so bf16 values below
`2**-126` flush to zero, as in `mxfp8_quantize`.
`cvt_warp_fp16_to_mxfp8` relies on that flush to treat scale byte 0 as a
zero scale.
- `benchmarks/bench_grouped_mxfp8_quantize_backend_comparison.py` adds a
`cuda` arm and launches `cake` through
`cake_grouped_mxfp8_quantize_launch`, since `cake_module.run(...)`
raises `TypeError` on the generated entry.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added masked MXFP8 quantization for expert workloads, with optional
fused SiLU-and-multiply processing.
- Added a CUDA backend for grouped MXFP8 quantization on compatible
SM100+ GPUs.
  - Added public Python exports for the expert quantization API.
  - Added padded and swizzled outputs for grouped GEMM workflows.

- **Documentation**
- Updated quantization API documentation with architecture, backend, and
shape requirements.

- **Tests**
- Expanded correctness and backend coverage, including masking, graph
capture, edge cases, and output parity.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3821440](https://github.com/flashinfer-ai/flashinfer/commit/3821440929ee342fe9f939dbf5186c3e667a851c)

- **作者**: SeongJun Lee
- **时间**: 2026-10-21T16:05:10Z
- **提交信息**: perf(page): stop syncing the host on every NVFP4 slot-mapping append (#6204)

<!-- .github/pull_request_template.md -->

## 📌 Description

Outside CUDA graph capture,
`nvfp4_quantize_append_paged_kv_cache_with_slot_mapping` copies CUDA
`k_scale`/`v_scale` tensors to the host to check that they are positive
and finite. That `.cpu()` waits for the stream, so every eager append
synchronizes the host. A runtime calls the writer once per attention
layer per forward pass, so a step that runs outside a CUDA graph, such
as a prefill chunk, stalls the CPU once per attention layer.

The append kernel already reads both scales and traps on a non-positive
or non-finite value before it writes anything, so the host copy only
repeated that check. This drops the host read for CUDA scales. Float and
CPU scales are still checked on the host and raise `ValueError`, and the
capture-time checks are unchanged.

What changes for callers is how a bad CUDA scale is reported: eager mode
now gets the kernel's CUDA error, as graph replay already did, instead
of an immediate `ValueError`, and that error can leave the CUDA context
unusable. When there is nothing to write (an empty slot mapping or zero
heads), the kernel does not launch, so a bad CUDA scale goes unchecked
in that case. The docstring states both.

## 🔍 Related Issues

The host check came with #3740. vLLM PR 46963 uses this writer for its
NVFP4 KV cache on SM8x and SM12x.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files with `pre-commit run
--files flashinfer/page.py tests/attention/test_page.py` and fixed any
reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On SM80, `pytest tests/attention/test_page.py -k slot_mapping`: 50
passed, 1 skipped (the two-GPU case, with one GPU visible). The eager
`ValueError` test for a bad CUDA scale is now the eager half of the
existing bad-scale subprocess test, which covers 0, -1 and NaN in eager
mode and 0 under graph replay and now passes only on the kernel's CUDA
error, not on a host `ValueError` or an unrelated crash. The capture
test also checks that an eager append does not synchronize. With the old
host check, the three eager cases fail on its `ValueError` and the
synchronization check fails at the `.cpu()` call; with the kernel's
`trap;` removed, all four bad-scale cases fail.

In vLLM on SM80 (Qwen3.6-35B-A3B NVFP4, TP=1, eager, prefix caching), a
turn that reuses an 18,640-token cached prefix and recomputes 2,860
tokens makes 20 appends. Swapping only this helper in an otherwise
identical FlashInfer build, the same prompt took 499.4 ms (median of 12)
with the current check and 451.7 ms with this change, and the ranges
(495.5–516.0 and 447.5–464.5 ms) do not overlap. The next token matched
in every run. Its top-5 logprobs already vary from run to run without
the change (largest spread 0.177 there, 0.117 with it), so this
measurement shows no added numeric change. Not run: SM12x, multi-GPU, or
with torch.compile and CUDA graphs around the prefill.

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

* **Behavior Changes**
* CUDA-resident scale values are now checked during append operations
rather than being read back to the host first. Invalid values may
surface as a CUDA error, which can leave the CUDA context unusable.
* During CUDA graph capture, host scalar values remain unsupported. CUDA
scale tensors must be contiguous float32 scalars on the target device;
host floats and CPU tensors continue to be validated on the host.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [595bc57](https://github.com/flashinfer-ai/flashinfer/commit/595bc5746cd57efc0006ff888b4bf8144f8235b9)

- **作者**: eigen
- **时间**: 2026-10-21T13:15:39Z
- **提交信息**: refactor(cake_deepgemm_batched_gemm): ship the DeepGEMM-derived batched projection GEMM as a self-contained vendorable package (#6928)

`flashinfer.fp8_batched_gemm.prepare_fp8_batched_gemm` dispatches the
DeepGEMM-derived batched projection GEMM (`bhr,hdr->bhd`: per-head
projection of T tokens over H heads from rank K=4096 to N=1024; FP8
variants take e4m3 operands with UE8M0 block scales) to one of six
variants. This PR delivers all six as one self-contained package:

- `cake_deepgemm_batched_gemm_1931777936a4c257b75f`: FP8 operands,
scaled (alpha) epilogue, BF16 output (general tile config)
- `cake_deepgemm_batched_gemm_8b30436f526588de8d13`: FP8 operands,
N-tile 256 config, FP8 output
- `cake_deepgemm_batched_gemm_e8aa7f5b9aa0575db281`: FP8 operands,
swapped-AB layout, M-tile 16 (small T), FP8 output
- `cake_deepgemm_batched_gemm_7e76dfdd9b10af2f8359`: FP8 operands,
swapped-AB layout, M-tile 64, FP8 output
- `cake_deepgemm_batched_gemm_94affe3b74cd7c5a6422`: BF16 operands,
T≥128 config, BF16 output
- `cake_deepgemm_batched_gemm_d9a9c12ba43e831e0a02`: BF16 operands,
small-T (T=4) config, BF16 output

The baseline is the previous Cake version of the same kernels, as
shipped before this PR through the previous loader. Speedup is previous
time / new time, using the median GPU kernel time with a cold L2 over 3
interleaved groups of 128 iterations per side. Both sides were
JIT-compiled with CUDA 13.4 (nvcc 13.4.92) and run on the CUDA 13.0
runtime (PyTorch 2.14.1+cu130). A speedup of about 1.00 means the
re-packaged kernels run at the same speed as before.

**`cake_deepgemm_batched_gemm_1931777936a4c257b75f` (FP8, alpha
epilogue, BF16 output): NVIDIA GB300, sm_103a (compute capability 10.3,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| alpha T=4 (H=8, K=4096, N=1024) | 13.776 | 13.728 | 1.003 |
| alpha T=128 (H=8, K=4096, N=1024) | 14.688 | 14.528 | 1.011 |
| alpha T=1 (H=8, K=4096, N=1024) | 13.664 | 13.696 | 0.998 |
| alpha T=17 (H=8, K=4096, N=1024) | 13.856 | 13.792 | 1.005 |
| alpha T=1000 (H=8, K=4096, N=1024) | 39.488 | 39.328 | 1.004 |

**`cake_deepgemm_batched_gemm_1931777936a4c257b75f` (FP8, alpha
epilogue, BF16 output): NVIDIA GB200, sm_100a (compute capability 10.0,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| alpha T=4 (H=8, K=4096, N=1024) | 14.112 | 14.032 | 1.006 |
| alpha T=128 (H=8, K=4096, N=1024) | 15.104 | 14.960 | 1.010 |
| alpha T=1 (H=8, K=4096, N=1024) | 14.432 | 14.336 | 1.007 |
| alpha T=17 (H=8, K=4096, N=1024) | 14.176 | 14.240 | 0.996 |
| alpha T=1000 (H=8, K=4096, N=1024) | 41.760 | 41.632 | 1.003 |

**`cake_deepgemm_batched_gemm_8b30436f526588de8d13` (FP8, N-tile 256,
FP8 output): NVIDIA GB300, sm_103a (compute capability 10.3, 152 SMs),
CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=512 (H=8, K=4096, N=1024) | 19.328 | 19.296 | 1.002 |
| fp8 T=4096 (H=8, K=4096, N=1024) | 76.897 | 76.736 | 1.002 |
| fp8 T=500 (H=8, K=4096, N=1024) | 19.296 | 19.265 | 1.002 |
| fp8 T=1000 (H=8, K=4096, N=1024) | 29.536 | 29.520 | 1.001 |

**`cake_deepgemm_batched_gemm_8b30436f526588de8d13` (FP8, N-tile 256,
FP8 output): NVIDIA GB200, sm_100a (compute capability 10.0, 152 SMs),
CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=512 (H=8, K=4096, N=1024) | 19.680 | 19.617 | 1.003 |
| fp8 T=4096 (H=8, K=4096, N=1024) | 95.936 | 95.361 | 1.006 |
| fp8 T=500 (H=8, K=4096, N=1024) | 19.520 | 19.520 | 1.000 |
| fp8 T=1000 (H=8, K=4096, N=1024) | 30.801 | 30.735 | 1.002 |

**`cake_deepgemm_batched_gemm_e8aa7f5b9aa0575db281` (FP8, swapped-AB,
M-tile 16, FP8 output): NVIDIA GB300, sm_103a (compute capability 10.3,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=1 (H=8, K=4096, N=1024) | 9.760 | 9.760 | 1.000 |
| fp8 T=4 (H=8, K=4096, N=1024) | 9.728 | 9.745 | 0.998 |
| fp8 T=16 (H=8, K=4096, N=1024) | 9.856 | 9.792 | 1.007 |
| fp8 T=2 (H=8, K=4096, N=1024) | 9.728 | 9.727 | 1.000 |
| fp8 T=8 (H=8, K=4096, N=1024) | 9.792 | 9.728 | 1.007 |
| fp8 T=17 (H=8, K=4096, N=1024) | 11.040 | 11.072 | 0.997 |
| fp8 T=32 (H=8, K=4096, N=1024) | 11.248 | 11.200 | 1.004 |

**`cake_deepgemm_batched_gemm_e8aa7f5b9aa0575db281` (FP8, swapped-AB,
M-tile 16, FP8 output): NVIDIA GB200, sm_100a (compute capability 10.0,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=1 (H=8, K=4096, N=1024) | 9.824 | 9.824 | 1.000 |
| fp8 T=4 (H=8, K=4096, N=1024) | 9.856 | 9.856 | 1.000 |
| fp8 T=16 (H=8, K=4096, N=1024) | 9.920 | 9.952 | 0.997 |
| fp8 T=2 (H=8, K=4096, N=1024) | 9.856 | 9.824 | 1.003 |
| fp8 T=8 (H=8, K=4096, N=1024) | 9.888 | 9.856 | 1.003 |
| fp8 T=17 (H=8, K=4096, N=1024) | 11.072 | 11.040 | 1.003 |
| fp8 T=32 (H=8, K=4096, N=1024) | 11.136 | 11.168 | 0.997 |

**`cake_deepgemm_batched_gemm_7e76dfdd9b10af2f8359` (FP8, swapped-AB,
M-tile 64, FP8 output): NVIDIA GB300, sm_103a (compute capability 10.3,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=128 (H=8, K=4096, N=1024) | 12.992 | 12.896 | 1.007 |
| fp8 T=100 (H=8, K=4096, N=1024) | 12.736 | 12.832 | 0.993 |
| fp8 T=127 (H=8, K=4096, N=1024) | 13.024 | 12.960 | 1.005 |

**`cake_deepgemm_batched_gemm_7e76dfdd9b10af2f8359` (FP8, swapped-AB,
M-tile 64, FP8 output): NVIDIA GB200, sm_100a (compute capability 10.0,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| fp8 T=128 (H=8, K=4096, N=1024) | 12.928 | 12.896 | 1.002 |
| fp8 T=100 (H=8, K=4096, N=1024) | 12.704 | 12.672 | 1.003 |
| fp8 T=127 (H=8, K=4096, N=1024) | 12.832 | 12.928 | 0.993 |

**`cake_deepgemm_batched_gemm_94affe3b74cd7c5a6422` (BF16, T≥128 config,
BF16 output): NVIDIA GB300, sm_103a (compute capability 10.3, 152 SMs),
CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| bf16 T=128 (H=8, K=4096, N=1024) | 12.032 | 12.032 | 1.000 |

**`cake_deepgemm_batched_gemm_94affe3b74cd7c5a6422` (BF16, T≥128 config,
BF16 output): NVIDIA GB200, sm_100a (compute capability 10.0, 152 SMs),
CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| bf16 T=128 (H=8, K=4096, N=1024) | 12.096 | 12.064 | 1.003 |

**`cake_deepgemm_batched_gemm_d9a9c12ba43e831e0a02` (BF16, small-T
config, BF16 output): NVIDIA GB300, sm_103a (compute capability 10.3,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| bf16 T=4 (H=8, K=4096, N=1024) | 10.448 | 10.368 | 1.008 |

**`cake_deepgemm_batched_gemm_d9a9c12ba43e831e0a02` (BF16, small-T
config, BF16 output): NVIDIA GB200, sm_100a (compute capability 10.0,
152 SMs), CUDA 13.0 runtime, CUDA 13.4 JIT**

| Shape | Previous (µs) | New (µs) | Speedup (previous / new) |
|---|---:|---:|---:|
| bf16 T=4 (H=8, K=4096, N=1024) | 10.544 | 10.560 | 0.998 |

Cake ships this family with exactly these six variants and no other data
types, layouts or fused forms, on `sm_100a` (B200/GB200) and `sm_103a`
(B300/GB300).

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [597e3a6](https://github.com/flashinfer-ai/flashinfer/commit/597e3a67ca36e1d2f3820acc9b0e3ca6817c8d2e)

- **作者**: eigen
- **时间**: 2026-10-21T11:36:17Z
- **提交信息**: refactor(cake_deepgemm_fp8_gemm): ship the DeepGEMM-derived FP8 1D1D GEMM as a self-contained vendorable package (#6927)

The DeepGEMM-derived FP8 1D1D GEMM behind
`flashinfer.experimental.deepgemm_fp8_gemm.prepare_fp8_gemm_1d1d` takes
FP8 e4m3 operands with per-128-block UE8M0 scales and produces BF16
output. It has two variants: the forward GEMM, which writes a fresh
output, and the weight-gradient GEMM, which accumulates into the
existing output. This PR delivers both variants as one self-contained
package. The baseline is the previous Cake version of these kernels,
meaning the same kernels as shipped before this PR through the previous
loader. Speedup is previous / new, and timings are median GPU kernel
time with a cold L2 over 3 interleaved groups of 128 iterations per
side. It is ≈1.00 on every shape (0.972 to 1.019), so the re-packaged
kernels run at the same speed.

**Forward GEMM on NVIDIA GB300 (sm_103a, compute capability 10.3), CUDA
runtime 13.0, kernels JIT-compiled with CUDA 13.4 (13.4.92)**

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4096 N=7168 K=4096 | 66.880 | 66.801 | 1.001 |
| M=1024 N=2048 K=1024 | 6.656 | 6.656 | 1.000 |
| M=3000 N=4000 K=1152 | 12.992 | 12.960 | 1.002 |
| M=128 N=1024 K=512 | 5.600 | 5.504 | 1.017 |
| M=300 N=7168 K=2048 | 9.904 | 9.888 | 1.002 |
| M=2048 N=224 K=4096 | 12.368 | 12.384 | 0.999 |

**Forward GEMM on NVIDIA GB200 (sm_100a, compute capability 10.0), CUDA
runtime 13.0, kernels JIT-compiled with CUDA 13.4 (13.4.92)**

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4096 N=7168 K=4096 | 87.872 | 87.264 | 1.007 |
| M=1024 N=2048 K=1024 | 6.976 | 6.960 | 1.002 |
| M=3000 N=4000 K=1152 | 14.129 | 14.080 | 1.003 |
| M=128 N=1024 K=512 | 5.616 | 5.728 | 0.980 |
| M=300 N=7168 K=2048 | 10.528 | 10.496 | 1.003 |
| M=2048 N=224 K=4096 | 12.800 | 12.656 | 1.011 |

**Weight-gradient GEMM (accumulate) on NVIDIA GB300 (sm_103a, compute
capability 10.3), CUDA runtime 13.0, kernels JIT-compiled with CUDA 13.4
(13.4.92)**

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4096 N=7168 K=4096 | 81.409 | 81.440 | 1.000 |
| M=1024 N=2048 K=1024 | 7.840 | 7.760 | 1.010 |
| M=3000 N=4000 K=1152 | 23.792 | 23.760 | 1.001 |
| M=128 N=1024 K=512 | 6.592 | 6.784 | 0.972 |
| M=300 N=7168 K=2048 | 11.072 | 11.040 | 1.003 |
| M=2048 N=224 K=4096 | 13.553 | 13.568 | 0.999 |

**Weight-gradient GEMM (accumulate) on NVIDIA GB200 (sm_100a, compute
capability 10.0), CUDA runtime 13.0, kernels JIT-compiled with CUDA 13.4
(13.4.92)**

| shape | previous (µs) | new (µs) | speedup |
|---|---:|---:|---:|
| M=4096 N=7168 K=4096 | 98.144 | 97.377 | 1.008 |
| M=1024 N=2048 K=1024 | 8.224 | 8.256 | 0.996 |
| M=3000 N=4000 K=1152 | 24.240 | 24.336 | 0.996 |
| M=128 N=1024 K=512 | 6.880 | 6.752 | 1.019 |
| M=300 N=7168 K=2048 | 11.744 | 11.744 | 1.000 |
| M=2048 N=224 K=4096 | 14.032 | 13.889 | 1.010 |

Cake ships only these two variants of this family (forward and
accumulate, FP8 e4m3 in and BF16 out), on `sm_100a` (B200/GB200) and
`sm_103a` (B300/GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added a manifest-driven DeepGEMM FP8 GEMM backend supporting NVIDIA
`sm_100a` and `sm_103a` architectures.
- Added automatic loading of prebuilt libraries with fallback to JIT
compilation.
- Added runtime architecture detection, launch planning, CUDA
compatibility checks, and input validation.
  - Added support for forward and weight-gradient FP8 GEMM routes.

- **Documentation**
- Documented supported dimensions, build requirements, package layout,
licensing, and GPU-independent tests.

- **Tests**
- Expanded coverage for kernel plans, launch geometry, manifests,
validation, and build metadata.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2852797](https://github.com/flashinfer-ai/flashinfer/commit/28527974293499a21687feccc2c6ebf10f1009d1)

- **作者**: eigen
- **时间**: 2026-10-21T11:18:02Z
- **提交信息**: deslop(cake_dense_projection_gemm): fold bindings and clone kernels, drop dead arms, derive test template set (#6938)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

This PR is the round-2 deslop of the Cake dense-projection GEMM package
`cake_dense_projection_gemm`, tracked in #6665. The package has 87
programs: 84 `dense_proj_gemm_*` K1 templates and 3 FP32 router
programs. They make 104 (program, architecture) builds, 47 for SM100 and
57 for SM107. The PR has four mechanical commits. The first folds 81
duplicate host bindings into 6 shared ones. The second folds 10 clone
kernel sources into 7 bodies. The third drops architecture arms and a
check helper that no build reaches. The fourth derives the test's
exported-template set from the registry instead of keeping it as a
literal. Device code, routes, launch arguments, exports, module names
and the test's collected items do not change.

Behaviour changes:
- **Host backtraces.** For the 81 re-pointed programs, a failing host
check's backtrace text (file / line) now names the shared binding.
Message texts, exception kinds, exports and device code do not change.
- **One rebuild for the re-pointed builds.** The 97 re-pointed binding
builds and the 14 re-pointed kernel builds change their source file and
/ or compile definitions. That is 111 compile commands in all; each of
the 104 builds has two. Module names are unchanged, so an existing JIT
cache rebuilds those modules once.
- **Nothing else.** No reachable input changes a launch, an argument, a
route, an export, a module name or a test result.

## Changes

Base: upstream main `75b30ffdb` (2026-10-20). Head:
`112dc41a82a5eef281b0e1d9090b1337bb8a481d` (4 commits). 135 files,
+2,650 / -23,297 (0 added, 91 deleted, 44 modified).

- **Package.** 87 programs (84 `dense_proj_gemm_*` K1 templates + 3 FP32
router programs) and 104 (program, architecture) builds: 47 for SM100
(compute capability 10.0) and 57 for SM107 (compute capability 10.7).
The loader compiles from the manifest `build.json`. It has one entry per
build, and each entry has two sources, one flag list, per-source digests
and a closure digest.
- **Unchanged:** program names, module names, kernel symbols, shim
namespaces, exported entry points, routes, launch arguments, argument
plans and the test's collected items.
- **Device code.** Every change is mechanical and preserves behaviour
for every reachable input. No kernel's device code changes:
- the folded kernel bodies expand back to their former files byte for
byte;
- the kernels without the dead arms preprocess to the same device text
for each architecture;
  - the gates compile both sides to identical SASS (see Validation).
- **Disclosure.** This PR touches 42 generated files: the 6 shared
bindings, the 7 fold bodies, the 28 kernel sources of commit 3 and the
check header. Each one carries this line after its licence block, with a
one- or two-line hand-edit note beside it, instead of any "do not edit"
claim:
`// Generated by Cake for FlashInfer. Exporter output, hand-edited here
pending exporter support.`

The untouched generated files keep their claim. These are the 16 device
helpers, the device / host common headers, the loader and the registry.

### Commit 1 (97f40d281) - cake_dense_projection_gemm: fold 81 duplicate
bindings into 6 shared (88 files, +1,437 / -14,339)

- **Shapes.** The 87 generated host bindings come in six launcher
shapes: cluster, single-CTA, oversized shared memory, FP32 router, and
templated forms of the first two. Within a shape, the bindings were
byte-identical once these values were masked:
- the kernel symbol (for the templated forms: the templated name, knob,
knob type and instantiation value);
  - the host-shim namespace;
  - the two or four TMA encoder names;
  - the dynamic shared-memory literal.
- **Kept bindings.** Each shape keeps one binding, its lexicographically
first member. That binding now sets defaults for those values with
`#ifndef` blocks and uses the macros in these places:
  - the declaration;
  - the two kernel-pointer casts;
  - the launch-name literal;
  - the shared-memory opt-in and launch literal;
  - the encoder calls;
  - the namespace open, close and export.
- **Manifest.** The other 81 bindings are deleted. Their 97 `build.json`
entries now name the shared binding as their second source and carry the
member's values as compile definitions (767 definition lines). The
source digests are re-sealed, and the closure digests stay as exported.
The 7 builds of the kept bindings pass no definition and take the
defaults.
- **Disclosed (host-only):**
- For the 81 re-pointed programs, a failing host check now reports the
shared binding's file name and line in its backtrace text instead of the
member's. These checks are the launcher's tensor shape / stride / dtype
assertions. Message texts, exception kinds, exports and device code are
unchanged.
- The 97 re-pointed builds compile their binding from another source
file. Each build has one flag list, and it now carries more definitions.
Module names are unchanged, so an existing JIT cache rebuilds these
modules once.

### Commit 2 (2f8196616) - cake_dense_projection_gemm: fold 10 clone
kernel sources into 7 bodies (18 files, +1,089 / -8,680)

- **Groups.** Seven groups of generated kernel sources, 17 translation
units in all, were clones of one another:
  - the pro7 / pro15 twins of four programs;
- the half-tile (`ht`) variants of four programs (the kk/kn × ±`ht` ×
pro7/pro15 lattice forms one five-member group);
  - the templated `nn_n128_m64` pair.

Within a group, the text differed only in a few dozen line ranges:
shared-memory layout constants, barrier offsets, a prologue or cleanup
statement, and one stage-release tail.
- **Bodies.** In each group, the lexicographically first member's source
becomes the body. Every line range that differs goes behind `#if` /
`#elif` / `#else` arms keyed on the member's compile definition. The
templated pair uses the member unit's existing selector definition. A
macro spells the kernel symbol, and an `#ifndef` sets its default to the
kept program's symbol. Guards reject a build that selects two programs,
or a selected member without its kernel symbol. The kept program is the
default, so its own builds pass no group definition.
- **Manifest.** The 10 other sources are deleted. Their 14 `build.json`
entries now name the shared body as their first source, with re-sealed
digests and the member's definition appended (12 new definition lines).
The 10 kept-body entries are re-sealed. Closure digests are unchanged.
- **Proof.** A static expansion check covers 24 of 24 (module,
architecture) expansions: expanding a body with a member's definitions
reproduces that member's former kernel file byte for byte. The
disclosure line is the only addition. The device gate gives the
compiler-side proof (see Validation).
- **Disclosed:** the 14 member builds compile their kernel from another
source file with one more definition. Module names and SASS are the same
(see Validation). An existing JIT cache rebuilds these modules once.

### Commit 3 (bfba323de) - cake_dense_projection_gemm: drop dead arch
arms and an unused check (30 files, +121 / -200)

- **Unreachable text.** No build of the package can reach this text:
- the SM100 shared-memory address arm (`#if __CUDA_ARCH__ == 1000`, 5
lines each) in the 27 kernel sources whose manifest entries all target
SM107;
- the two pre-SM90 `#error` guards, which never fire, in the one
SM100-only kernel that has them;
- `check_dense_leading_dims` in `csrc/cake_ffi_checks.h`, which no
launcher of this package calls. The sibling packages keep their own
copies of the header, and their bindings do call it.

The kept `#else` bodies become unconditional text. The 35 kernel sources
with SM100 builds keep their arm.
- **Check header.** The disclosure statement replaces the blank line
after the licence block, and the hand-edit note sits where the removed
definition was. As a result, the four remaining check sites keep their
line numbers (34 / 40 / 48 / 53).
- **Manifest.** `build.json` re-seals the digests of the 28 edited
kernel sources. Closures, flags, sources and layout are unchanged.
- **Consequence:** none for any reachable input:
- the removed lines were never tokenised for the architectures the
manifest builds;
  - an unused inline function emits no code or symbol;
  - a failed tensor check reports the same header line as before.

### Commit 4 (112dc41a8) - cake_dense_projection_gemm: derive the test's
exported-template set (1 file, +15 / -90)

- **Derivation.**
`tests/experimental/test_cake_dense_projection_gemm.py` replaces its
84-entry `EXPORTED_TEMPLATES` literal with a derivation from the
registry that the literal mirrors. The set is the union of the
`dense_proj_gemm_*` templates in the registry's kernel table over all
architectures (SM100 44 + SM107 54 - 14 shared = 84). This is the same
filter that the test's per-architecture helper applies.
- **Why.** The literal had one reader, a check of `registered <=
EXPORTED_TEMPLATES`. Against a hand-copied literal, that check was a
tautology.
- **Pin.** One import-time pin, `assert len(EXPORTED_TEMPLATES) == 84`,
keeps the suite tied to the size of the delivered export. If the
registry has a different number of templates, the module fails at
import.
- **Unchanged.** The measured planner tables and the generated-table
markers stay. The collected items are unchanged: 63 tests, 166 items
(141 host-side + 25 GPU).
- **Consequence:** none. This is a test-only change, and the counts are
identical on both trees.

## Validation

The compile-only rows (device gate and host gate) are compiled on one
node with a CUDA 13.4 toolkit, for both architectures. The GPU rows run
on a B200 (SM100, compute capability 10.0; 47 modules) and on an R200
(SM107, compute capability 10.7; 57 modules). A GB300 (SM103) registers
no program of this package, so its 25 GPU items skip there by design
(see **Not run**).

- Device gate, 104 rows (every (program, architecture) build's kernel:
34 SM107 kernels that lost their SM100 arm, 1 SM100 kernel that lost its
pre-SM90 guards, 14 folded members and 10 fold bodies with their compile
definitions, 45 unchanged kernels whose flag list newly carries the
binding definitions; cubin + SASS + preprocessed text): all 104 rows
identical (SASS and cubin digests equal, one function per side, 0
differences, 0 accepted fallbacks; 47 SM100 + 57 SM107 rows; CUDA 13.4
toolkit)
- **Rows.** Every build compares its kernel source at the base with the
one at head. For the folded rows, the base side is the member's former
file and the head side is the fold body.
- **Compilation.** Both sides are compiled with the loader's exact flag
set, from one staged path, in one environment.
  - **Pass criteria.** A row passes when all of these hold:
    - the cubin sha256 is equal;
    - the SASS is identical after masking addresses and encodings;
    - resource usage is identical;
    - the build's kernel is the only function;
- the preprocessed texts are identical after dropping line markers. The
markers differ because the body is another file with other line numbers,
and the sources without the dead arms have fewer lines. For the 45
unchanged kernels, the texts must be identical without this step.
- Host gate, 104 rows (every build's binding: the 97 re-pointed builds
(the 81 deleted bindings, 16 of which served both architectures) against
the shared binding compiled with their definitions, the 7 shared
bindings against themselves at the base; compile-only, SM100 and SM107):
all 104 rows identical (no device code in any object; preprocessed text
identical after the declared normalisation on every row; the check-site
file / line counts matched on all 104 rows; exported symbol sets
identical on all 104; 7 SM100-shared + 97 re-pointed rows, 47 SM100 + 57
SM107; CUDA 13.4 toolkit)
- **Rows.** For each of the 97 re-pointed builds, the base side is the
deleted binding and the head side is the shared binding compiled with
that build's definitions. The 7 builds of the six kept bindings are
compared with their own text at the base.
  - No binding object may contain device code.
- The preprocessed text must be identical after the declared
normalisation, which covers:
    - line markers and blank lines;
    - the file / line arguments of the check macros;
- the removed `check_dense_leading_dims` definition, dropped from the
base side.
- On each row, the file / line changes are counted against the binding's
own check sites (17, 16 or 11 per shape).
- Exported symbol sets must be identical, and no object may name the
removed helper.
- Module build and load through the package loader (47 SM100 modules on
B200, 57 SM107 modules on R200, both trees): all 47 SM100 modules on
B200 and all 57 SM107 modules on R200 built and loaded on both trees
(104 of 104 per tree), each with its entry point and build_cuda_version
export; exported symbol sets, device kernel sets and build_cuda_version
identical to the base-tree modules for all 104
  - Spec names, flags and sources must match what the manifest records.
- The loader must build every module, and each module must load with a
callable entry point and its `build_cuda_version` export.
- Exported symbol sets and device kernel sets must be identical to the
base-tree modules.
- Tests on B200 and R200 (both the base and this branch, fresh JIT
workspaces) and with CUDA hidden: 166 items on both trees on every
route: B200 166 passed / 0 skipped / 0 failed on both trees; R200 152
passed / 14 skipped / 0 failed on both trees with identical skipped ids;
CUDA hidden 141 passed / 25 skipped / 0 failed on both trees on both
routes; the host-overhead benchmark ran on both trees on both devices
(informational)
- **The test file.**
`tests/experimental/test_cake_dense_projection_gemm.py` has 166 items.
- **GPU items.** Each of the 25 GPU items passes or skips depending on
whether the device registers its planner-routed template. Both trees
must give the same passed / skipped / failed counts and the same skipped
ids.
- **CUDA hidden.** Expected result on both trees: 141 passed / 25
skipped.
- **Host overhead.** The host-overhead benchmark runs on both trees, for
information.
- CPU checks: all passed: pre-commit on both full checkouts and on the
modified files (identical results, no changes); the manifest check
script 0 findings; stale-reference searches at the expected counts
(deleted bindings and kernel files referenced nowhere, the removed
helper 0 in the package); the disclosure line exactly once in each
touched generated file and no "do not edit" in touched files; build.json
digests, closures and layout verified (104 entries, closures unchanged);
the four edits re-applied to a snapshot of the base reproduce the branch
byte for byte (135 of 135 paths, 91 deletions); collection 166 items on
both trees (141 CPU / 25 GPU); the derived test table equals the former
literal (84 of 84); commit-message checks passed
- pre-commit on both full checkouts, which must give identical results,
and on the 44 modified files.
  - A manifest consistency check, which must report 0 findings.
  - Stale-reference searches, each with an expected count:
- the 81 deleted bindings and the 10 deleted kernel files: referenced
nowhere;
    - the removed helper: 0 in the package;
    - the SM100 arm: kept in 35 kernel sources.
- The disclosure line appears exactly once in each of the 42 touched
generated files, and no touched file contains "do not edit".
  - The digest / closure / layout check of `build.json`.
- Re-applying the four edits to a snapshot of the base must reproduce
the branch byte for byte.
  - Test collection: 166 items on both trees.
  - Commit message checks.

**Not run.** By design, this PR's validation includes no GPU tests on
GB300 (SM103, compute capability 10.3). The package registers no SM103
program. `build.json` lists only SM100 and SM107 builds, and a compute
capability 10.3 device maps to an architecture with no program. The test
file therefore skips its 25 GPU items on GB300 on both trees, and none
of this change runs there. The proof of record is the compile-only
device and host rows, which cover both shipped architectures.

## Not in this PR

- **Exporter regeneration of the bindings** (issue step 1 as written):
this PR parameterises the six shapes inside the repository with
`#ifndef` defaults and compile definitions. Emitting one shim per shape
at export time is a request to the exporter owners.
- **The issue's binding form** (one parametrised macro shim in
`host_common.cuh` plus a ~12-line stub per module): not taken, for three
reasons. The form taken keeps every launcher line inside digested `.cu`
sources and touches no header.
- A macro expands onto one logical line. The `__LINE__` that every check
site embeds would become the invocation line, so the preprocessed text
would no longer be line-identical to the former binding.
- The stubs would be 38-43 lines (licence, includes, declaration,
namespace, invocation, exports), not 12.
- The shim would live in a header that no `build.json` entry digests.
That moves the launcher text out of the loader's fail-closed digest set,
unless the headers join it (the cross-package manifest change of step
9).
- **Raising `min_cuda` to 13.4 for the three oversized-shared-memory
programs, and removing the SM103 text in `__init__.py`** (the rest of
step 2): these are a manifest / loader-skip change and a documentation
change, not dead text. They belong in a separate small PR.
- **Planner reachability sweep** over the full row × op × dtype × T ×
arch grid (step 3): this is a CPU study, not a text change. Its result
decides which templates may be deleted.
- **Four of the eight pro7 ↔ pro15 twins of step 4** (`kk_n128_hen`,
`kk_n256`, `kk_n256_cg`, `kn_n256_f32_tma1`): their pro7 side is a
templated source that already serves two programs through `if constexpr`
knob sites.
- An exact arm would hold the whole template body as one arm and the
plain pro15 source as the other, which saves nothing.
- Adding the plain program as a third instantiation is a template fold
(a declaration merge), which is exporter work.

Commit 2 folds the other four pro twins (`kn_n256`, `kn_n256_tma2_pd2`,
`nn_n256_f32_v8`, `kn_n256_m256_ov_ht`).
- **The remaining clone families** (steps 4 and 7): the 13-source kk/kn,
the 9-source nn/kn tma1, `kn_n256_f32_v8`, `m256_ov_ht`, the router
trio, `kn_n256_tma*_pd2` and `kn_n256_tma1`. Exact `#if` arms are
feasible here, and the same per-member SASS rows can prove them.
However, each body would carry 30-74 differing regions. These families
are left for a second tranche or an exporter regeneration (about 22,900
more lines, by the map's estimate).
- **Knob-surface trim** of the planner / `instance_key` /
`instance_symbol`, and the CC 10.3 → `None` mapping (step 5): a
public-surface change that the package owner must confirm. Plan-dump
equality before and after is the gate.
- **Per-program argument plans** that drop the two unused TMA
descriptors per launch, and one-time encoding of the dummy descriptors
(step 6): exporter changes that need a host-overhead measurement first.
- **The router's per-launch FP32 → BF16x3 split**
(`split_fp32_to_bf16x3_`) and its `torch.sum` split-K reduction, and
**caching TMA descriptors across launches** (the issue's findings next
to step 6): these change behaviour or timing and are unmeasured. A
host-overhead and parity measurement on B200 and R200 comes first.
- **The rest of the test slimming** (step 8): replacing the 22
round-mirror tests with one table, cutting `test_instance_symbols` to
one case per suffix, and dropping the registry-literal layout test. This
PR takes only the `EXPORTED_TEMPLATES` derivation.
- **Cross-package follow-ups** (step 9: shared device helpers, a compact
manifest schema, headers in the digest map) and **the core entry-point
decision** (step 10).
- **`host_common.cuh`'s own launch / encoder helpers versus the
repository's shared helper header** (a finding): a host-text change that
needs its own host rows.
- **Exporter requests** (requests, not PR changes):
  - emit one shim per launcher shape;
- emit one kernel body per clone group, selected by compile definitions.

Experimental test scope for CI:

```experimental-tests
tests/experimental/test_cake_dense_projection_gemm.py
```

Part of #6665

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [adca7b8](https://github.com/flashinfer-ai/flashinfer/commit/adca7b87d23d426e7ae0eae6df3992d6b44532e8)

- **作者**: eigen
- **时间**: 2026-10-21T10:38:43Z
- **提交信息**: feat(cake_rubin_mla_nvfp4_decode): NVFP4 MLA paged decode for Rubin (sm_107a) from cake (#6931)

This PR adds the Rubin (SM107, `sm_107a`) variant of the Cake NVFP4 MLA
paged decode. Cake is NVIDIA's kernel generator. It already ships this
decode for SM100 / SM103 (B200 / B300) as `cake_mla_nvfp4_paged_decode`.
This PR adds the Rubin package,
`flashinfer/experimental/cake_rubin_mla_nvfp4_decode`. On compute
capability 10.7, `flashinfer.mla.cake_mla_nvfp4_paged_decode` routes to
it. The package contains mixed-tile and full-tile decode programs, three
split-KV merge programs and the NVFP4 query quantizer. It decodes BF16
queries against the paged NVFP4 MLA KV cache and writes BF16 output. The
baseline is TokenSpeed MLA 2 (2.0.3), a non-Cake kernel measured in the
same process on the same board. Over the 16 configurations below, the
geometric mean of MLA 2 / Cake is 1.044: 1.104 on the Q4 rows and 0.987
on the Q8 rows. Cake is faster in 9 of 16 configurations. On the Q4 rows
it is faster at batch 4 and above, and it is slower at batch 1.

*NVIDIA R200 (pre-release board, reported as "NVIDIA Graphics Device",
compute capability 10.7 / `sm_107a`, 208 SMs, 120 MiB L2), driver
615.71.09, CUDA 13.4 (runtime 13.4.92), PyTorch 2.14.1+cu130. H = 96
heads, page size 64. Configurations are named H96-Q{query
length}-B{batch}-KV{keys per sequence}. Each latency is per decode call
in µs, taken as the median over two runs of (median of 15 replays of a
20-launch CUDA graph). Lower is better. Each kernel uses its own cold-L2
KV copies. A "MLA 2 / Cake" value above 1 means Cake is faster.*

| Configuration | Cake (µs) | MLA 2 (µs) | MLA 2 / Cake |
|---|---:|---:|---:|
| H96-Q4-B1-KV64K | 25.1 | 23.6 | 0.94 |
| H96-Q4-B4-KV64K | 52.8 | 57.4 | 1.09 |
| H96-Q4-B16-KV64K | 185.7 | 213.3 | 1.15 |
| H96-Q4-B64-KV64K | 674.9 | 805.5 | 1.19 |
| H96-Q4-B1-KV128K | 36.6 | 32.9 | 0.90 |
| H96-Q4-B4-KV128K | 89.7 | 104.5 | 1.17 |
| H96-Q4-B16-KV128K | 346.6 | 417.3 | 1.20 |
| H96-Q4-B64-KV128K | 1300.8 | 1623.8 | 1.25 |
| H96-Q8-B1-KV64K | 32.1 | 29.0 | 0.91 |
| H96-Q8-B4-KV64K | 82.0 | 85.6 | 1.04 |
| H96-Q8-B16-KV64K | 283.9 | 280.5 | 0.99 |
| H96-Q8-B64-KV64K | 1094.5 | 1076.7 | 0.98 |
| H96-Q8-B1-KV128K | 50.0 | 45.5 | 0.91 |
| H96-Q8-B4-KV128K | 150.1 | 159.9 | 1.07 |
| H96-Q8-B16-KV128K | 554.7 | 546.9 | 0.99 |
| H96-Q8-B64-KV128K | 2151.7 | 2205.3 | 1.02 |

*On the large configurations, both kernels ran at the board's power cap
under the same conditions. During the timed replays the SM clock stayed
below the 2424 MHz maximum, dropping to about 1.7 GHz for MLA 2 at batch
16 and 64.*

The existing `cake_mla_nvfp4_paged_decode` package ships this Cake
decode on `sm_100a` and `sm_103a`, and with this PR it also ships on
`sm_107a`, where the Rubin package also carries the
decode-context-parallel form.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
  * Added experimental NVFP4 MLA decode support for Rubin/SM107 GPUs.
* Added dense and packed decode workflows, query quantization, split-KV
merging, LSE output, and context-parallel execution.
* Added prepared and direct decode APIs with workspace planning and CUDA
Graph-compatible launches.
* Existing SM100/SM103 devices continue using their established
implementations.

* **Documentation**
* Added usage guidance, supported configurations, requirements, API
contracts, and limitations for the experimental backend.

* **Tests**
* Added comprehensive coverage for accuracy, validation, planning,
quantization, context parallelism, and end-to-end execution.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fd4de5a](https://github.com/flashinfer-ai/flashinfer/commit/fd4de5acce18fd1c747c8425555f082dd4452cc3)

- **作者**: eigen
- **时间**: 2026-10-21T09:33:58Z
- **提交信息**: perf(cake_stepfun_moe): pair-raster BF16 FC1 and two-CTA per-token NVFP4 FC2 for the StepFun fused MoE (sm_100a, sm_103a) (#6934)

Cake's StepFun SwiGLU fused MoE (hidden 4096, intermediate 1536, 64
experts, top-k 8) comes in five data-type variants: bf16, fp8 (e4m3),
mxfp8, nvfp4 and per-token NVFP4 (`nvfp4_bf16tok`). It is built from 111
kernels per architecture. This PR regenerates all five families. The
BF16 FC1 tile-128 kernel now rasterizes its tiles in pairs, and the
per-token NVFP4 FC2 tile-256 kernel is now a two-CTA kernel that
replaces the one-CTA kernel. The baseline is the previous Cake version
of this kernel, which is the package on FlashInfer main from #6801 and
#6871. Both versions were measured with whole-graph CUDA-graph replay,
on the same node and GPU, in interleaved pairs. Overall performance is
unchanged. The only consistent gain is the per-token NVFP4 family at
1024–2048 tokens (about 2–3 %). Everything else is within about ±0.5 %
on GB300, except nvfp4 at 8 tokens (1.012x–1.015x). On B200, the
large-token bf16, fp8 and mxfp8 rows move in both directions
(0.995x–1.011x). Latencies are whole-graph medians in µs. Speedup =
previous / this PR, the median over the interleaved pairs, so >1.000x
means this PR is faster. Shapes: 5 families × tokens {8, 64, 512, 1024,
2048} × limit {7, 16} = 50 rows per GPU.

**NVIDIA GB300, sm_103a, CUDA 13.4 (nvcc), driver 580.159.03** (6
interleaved pairs per row)

| precision | tokens | limit | previous Cake (µs) | this PR (µs) |
speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|
| bf16 | 8 | 7 | 227.4 | 227.6 | 1.000x |
| bf16 | 8 | 16 | 227.4 | 227.5 | 1.000x |
| bf16 | 64 | 7 | 365.2 | 365.0 | 1.001x |
| bf16 | 64 | 16 | 365.0 | 365.1 | 1.000x |
| bf16 | 512 | 7 | 387.2 | 386.8 | 1.001x |
| bf16 | 512 | 16 | 387.2 | 386.8 | 1.001x |
| bf16 | 1024 | 7 | 411.6 | 412.3 | 0.998x |
| bf16 | 1024 | 16 | 411.5 | 412.5 | 0.998x |
| bf16 | 2048 | 7 | 538.4 | 539.6 | 0.997x |
| bf16 | 2048 | 16 | 539.8 | 540.9 | 0.998x |
| fp8 | 8 | 7 | 130.1 | 129.9 | 1.002x |
| fp8 | 8 | 16 | 130.0 | 129.9 | 1.001x |
| fp8 | 64 | 7 | 201.8 | 201.6 | 1.001x |
| fp8 | 64 | 16 | 201.8 | 201.5 | 1.002x |
| fp8 | 512 | 7 | 218.1 | 218.2 | 0.999x |
| fp8 | 512 | 16 | 218.2 | 218.1 | 1.000x |
| fp8 | 1024 | 7 | 235.1 | 235.6 | 0.998x |
| fp8 | 1024 | 16 | 235.1 | 235.7 | 0.998x |
| fp8 | 2048 | 7 | 310.5 | 311.0 | 0.998x |
| fp8 | 2048 | 16 | 310.8 | 311.5 | 0.998x |
| mxfp8 | 8 | 7 | 133.7 | 134.0 | 0.998x |
| mxfp8 | 8 | 16 | 133.9 | 134.0 | 1.000x |
| mxfp8 | 64 | 7 | 223.6 | 223.8 | 1.000x |
| mxfp8 | 64 | 16 | 223.9 | 223.6 | 1.001x |
| mxfp8 | 512 | 7 | 227.9 | 227.8 | 1.001x |
| mxfp8 | 512 | 16 | 227.8 | 227.7 | 1.001x |
| mxfp8 | 1024 | 7 | 260.2 | 260.2 | 1.000x |
| mxfp8 | 1024 | 16 | 260.3 | 260.3 | 1.000x |
| mxfp8 | 2048 | 7 | 350.9 | 350.0 | 1.002x |
| mxfp8 | 2048 | 16 | 350.5 | 350.0 | 1.001x |
| nvfp4 | 8 | 7 | 79.5 | 78.5 | 1.012x |
| nvfp4 | 8 | 16 | 79.5 | 78.4 | 1.015x |
| nvfp4 | 64 | 7 | 128.9 | 128.6 | 1.001x |
| nvfp4 | 64 | 16 | 128.9 | 128.6 | 1.002x |
| nvfp4 | 512 | 7 | 139.6 | 140.0 | 0.997x |
| nvfp4 | 512 | 16 | 139.7 | 139.9 | 0.999x |
| nvfp4 | 1024 | 7 | 170.4 | 171.0 | 0.997x |
| nvfp4 | 1024 | 16 | 170.4 | 170.9 | 0.997x |
| nvfp4 | 2048 | 7 | 230.6 | 230.9 | 0.999x |
| nvfp4 | 2048 | 16 | 230.6 | 230.9 | 0.999x |
| nvfp4_bf16tok | 8 | 7 | 85.4 | 85.0 | 1.004x |
| nvfp4_bf16tok | 8 | 16 | 85.4 | 85.1 | 1.004x |
| nvfp4_bf16tok | 64 | 7 | 135.2 | 135.2 | 1.000x |
| nvfp4_bf16tok | 64 | 16 | 135.3 | 135.2 | 1.000x |
| nvfp4_bf16tok | 512 | 7 | 151.5 | 151.8 | 0.998x |
| nvfp4_bf16tok | 512 | 16 | 151.5 | 151.8 | 0.998x |
| nvfp4_bf16tok | 1024 | 7 | 196.8 | 192.1 | 1.025x |
| nvfp4_bf16tok | 1024 | 16 | 196.7 | 192.2 | 1.024x |
| nvfp4_bf16tok | 2048 | 7 | 276.3 | 271.0 | 1.019x |
| nvfp4_bf16tok | 2048 | 16 | 276.3 | 271.0 | 1.020x |

**NVIDIA B200, sm_100a, CUDA 13.4 (nvcc), driver 580.82.07** (24
interleaved pairs per row)

| precision | tokens | limit | previous Cake (µs) | this PR (µs) |
speedup (previous / this PR) |
|---|---:|---:|---:|---:|---:|
| bf16 | 8 | 7 | 231.4 | 230.7 | 1.003x |
| bf16 | 8 | 16 | 231.5 | 230.7 | 1.004x |
| bf16 | 64 | 7 | 375.2 | 374.6 | 1.002x |
| bf16 | 64 | 16 | 375.2 | 374.6 | 1.002x |
| bf16 | 512 | 7 | 397.3 | 396.3 | 1.002x |
| bf16 | 512 | 16 | 397.1 | 396.6 | 1.002x |
| bf16 | 1024 | 7 | 440.7 | 437.6 | 1.001x |
| bf16 | 1024 | 16 | 460.9 | 439.3 | 1.009x |
| bf16 | 2048 | 7 | 646.7 | 645.4 | 0.997x |
| bf16 | 2048 | 16 | 645.4 | 644.4 | 1.003x |
| fp8 | 8 | 7 | 132.9 | 132.5 | 1.003x |
| fp8 | 8 | 16 | 132.9 | 132.5 | 1.003x |
| fp8 | 64 | 7 | 207.6 | 206.9 | 1.003x |
| fp8 | 64 | 16 | 207.5 | 206.8 | 1.003x |
| fp8 | 512 | 7 | 224.1 | 223.2 | 1.004x |
| fp8 | 512 | 16 | 224.1 | 223.2 | 1.004x |
| fp8 | 1024 | 7 | 247.1 | 247.4 | 1.000x |
| fp8 | 1024 | 16 | 247.7 | 248.0 | 1.000x |
| fp8 | 2048 | 7 | 348.5 | 348.6 | 0.995x |
| fp8 | 2048 | 16 | 350.8 | 351.4 | 1.000x |
| mxfp8 | 8 | 7 | 137.1 | 136.8 | 1.002x |
| mxfp8 | 8 | 16 | 137.1 | 136.8 | 1.002x |
| mxfp8 | 64 | 7 | 229.3 | 229.2 | 1.001x |
| mxfp8 | 64 | 16 | 229.4 | 229.2 | 1.001x |
| mxfp8 | 512 | 7 | 235.7 | 234.7 | 1.004x |
| mxfp8 | 512 | 16 | 235.8 | 234.8 | 1.004x |
| mxfp8 | 1024 | 7 | 284.1 | 281.6 | 1.011x |
| mxfp8 | 1024 | 16 | 285.3 | 282.6 | 1.004x |
| mxfp8 | 2048 | 7 | 403.5 | 405.0 | 1.004x |
| mxfp8 | 2048 | 16 | 405.7 | 401.5 | 1.003x |
| nvfp4 | 8 | 7 | 80.7 | 80.5 | 1.002x |
| nvfp4 | 8 | 16 | 80.7 | 80.6 | 1.002x |
| nvfp4 | 64 | 7 | 132.1 | 132.0 | 1.001x |
| nvfp4 | 64 | 16 | 132.2 | 131.9 | 1.002x |
| nvfp4 | 512 | 7 | 146.2 | 146.3 | 1.000x |
| nvfp4 | 512 | 16 | 146.2 | 146.2 | 1.000x |
| nvfp4 | 1024 | 7 | 186.9 | 186.7 | 1.001x |
| nvfp4 | 1024 | 16 | 186.9 | 186.8 | 1.001x |
| nvfp4 | 2048 | 7 | 249.4 | 249.9 | 0.999x |
| nvfp4 | 2048 | 16 | 250.1 | 251.5 | 0.999x |
| nvfp4_bf16tok | 8 | 7 | 87.7 | 87.3 | 1.004x |
| nvfp4_bf16tok | 8 | 16 | 87.7 | 87.3 | 1.004x |
| nvfp4_bf16tok | 64 | 7 | 137.6 | 137.6 | 1.001x |
| nvfp4_bf16tok | 64 | 16 | 137.6 | 137.7 | 1.000x |
| nvfp4_bf16tok | 512 | 7 | 157.9 | 158.2 | 0.998x |
| nvfp4_bf16tok | 512 | 16 | 157.9 | 158.2 | 0.998x |
| nvfp4_bf16tok | 1024 | 7 | 211.0 | 204.4 | 1.032x |
| nvfp4_bf16tok | 1024 | 16 | 211.0 | 204.4 | 1.032x |
| nvfp4_bf16tok | 2048 | 7 | 301.9 | 294.0 | 1.027x |
| nvfp4_bf16tok | 2048 | 16 | 301.8 | 294.1 | 1.026x |

Cake ships this kernel in the five data-type families above (bf16, fp8
e4m3, mxfp8, nvfp4, per-token NVFP4) for sm_100a (B200) and sm_103a
(GB300), and there are no other layouts or fused forms.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added opt-in per-token NVFP4 precision support for benchmark
scenarios, including per-token scaling and precision reporting.
- Added a new optimized execution path for 256-wide per-token NVFP4
workloads.
  - Expanded default benchmark coverage to include 1,024-token cases.
- **Bug Fixes**
- Improved launch validation and error reporting, including dynamic
shared-memory checks and CUDA configuration validation.
- **Documentation**
- Updated package and generated-code licensing, provenance, and launch
metadata documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8a93c9b](https://github.com/flashinfer-ai/flashinfer/commit/8a93c9b833761c75939f176a58268ad77ac304f1)

- **作者**: eigen
- **时间**: 2026-10-21T08:35:33Z
- **提交信息**: feat(cake_msa): Cake Hopper (SM90) programs behind the four MSA operations (#6252)

The MiniMax sparse attention (MSA) kernel family on Hopper has four
operations. Sparse decode uses bf16 q and fp8 e4m3 KV pages and covers
every admitted coordinate. Sparse prefill uses bf16 q, supports GQA
groups 4 / 8 / 16 and handles up to 4096 pages per sequence. Proxy score
has two regimes. The decode regime takes fp8 and bf16 q, a one-head
index cache, Hq in {1,2,4} and max_seqlen_q <= 4. The prefill regime
takes fp8 q with both accumulation precisions. Top-k block select has
one form per planner coordinate: columns per CTA, tile groups, index
bits and mask form. One route table serves 89 generated programs: 22
sparse-decode, 6 sparse-prefill (3 prefill_v1 + 3 prefill_v2), 24
proxy-decode, 5 proxy-prefill and 32 top-k.

This PR delivers the Hopper (sm_90a) variant of the Cake MSA family.
That covers all four operations and all 89 programs, compiled with
FlashInfer's sm_90a flags. No earlier Cake version of this family ships
on sm_90a. So in every row the baseline (`fi_sm90`) is FlashInfer's
existing SM90 CuTe DSL kernel for the same operation and shape, measured
in the same session on the same GPU. Speedup = fi_sm90 latency / Cake
latency, so a value > 1.000 means Cake is faster. All rows were measured
on an NVIDIA H100 80GB HBM3 (compute capability 9.0, sm_90a, 132 SMs)
with CUDA 13.3 and torch 2.13.0a0+9186a08b2c.nv26.07.

*NVIDIA H100 80GB HBM3 (compute capability 9.0, sm_90a, 132 SMs), CUDA
13.3, torch 2.13.0a0+9186a08b2c.nv26.07; same-session interleaved CUPTI
medians (cold L2, 3 reps) of the Cake kernel and the fi_sm90 CuTe DSL
kernel of the same shape; speedup = fi_sm90 / Cake (> 1.000 = Cake
faster); correctness-only shapes carry no timing.*

### Top-k block select (MSA indexer) (28 shapes)

| shape | Cake (us) | fi_sm90 (us) | speedup fi_sm90 / Cake |
|---|---|---|---|
| topk_plain_h1_tiles64_tq1 | 2.112 | 2.560 | 1.212x |
| topk_nvp_forced_h1_tiles64_tq1 | 2.368 | 2.687 | 1.135x |
| topk_plain_h1_tiles64_tq32 | 2.304 | 2.240 | 0.972x |
| topk_nvp_forced_h1_tiles64_tq32 | 2.464 | 2.656 | 1.078x |
| topk_plain_h1_tiles64_tq256 | 2.368 | 2.336 | 0.986x |
| topk_nvp_forced_h1_tiles64_tq256 | 2.528 | 2.848 | 1.127x |
| topk_plain_h1_tiles64_tq4096 | 3.232 | 3.296 | 1.020x |
| topk_nvp_forced_h1_tiles64_tq4096 | 3.360 | 3.456 | 1.029x |
| topk_plain_h1_tiles512_tq1 | 2.592 | 2.656 | 1.025x |
| topk_nvp_forced_h1_tiles512_tq1 | 2.816 | 2.752 | 0.977x |
| topk_plain_h1_tiles512_tq32 | 2.848 | 3.296 | 1.157x |
| topk_nvp_forced_h1_tiles512_tq32 | 3.072 | 3.424 | 1.115x |
| topk_plain_h1_tiles512_tq256 | 3.360 | 3.872 | 1.152x |
| topk_nvp_forced_h1_tiles512_tq256 | 4.032 | 4.032 | 1.000x |
| topk_plain_h1_tiles512_tq4096 | 8.896 | 8.928 | 1.004x |
| topk_nvp_forced_h1_tiles512_tq4096 | 9.951 | 9.536 | 0.958x |
| topk_plain_h1_tiles2048_tq1 | 2.592 | 2.656 | 1.025x |
| topk_nvp_forced_h1_tiles2048_tq1 | 2.848 | 2.816 | 0.989x |
| topk_plain_h1_tiles2048_tq32 | 3.808 | 3.808 | 1.000x |
| topk_nvp_forced_h1_tiles2048_tq32 | 6.880 | 3.936 | 0.572x |
| topk_plain_h1_tiles2048_tq256 | 5.920 | 5.088 | 0.859x |
| topk_nvp_forced_h1_tiles2048_tq256 | 5.696 | 5.472 | 0.961x |
| topk_plain_h1_tiles2048_tq4096 | 21.736 | 22.656 | 1.042x |
| topk_nvp_forced_h1_tiles2048_tq4096 | 21.216 | 24.031 | 1.133x |
| topk_plain_h4_tiles512_tq1 | 2.560 | 2.656 | 1.037x |
| topk_nvp_forced_h4_tiles512_tq1 | 2.720 | 2.752 | 1.012x |
| topk_plain_h4_tiles512_tq256 | 4.832 | 14.079 | 2.914x |
| topk_nvp_forced_h4_tiles512_tq256 | 4.256 | 13.775 | 3.237x |

### Proxy score (MSA indexer) (72 shapes)

| shape | Cake (us) | fi_sm90 (us) | speedup fi_sm90 / Cake |
|---|---|---|---|
| pxp_h1_chunk1536_ctx8K | 6.528 | 5.664 | 0.868x |
| pxp_h1_chunk1536_ctx64K | 23.168 | 18.496 | 0.798x |
| pxp_h1_chunk1536_ctx256K | 78.335 | 62.688 | 0.800x |
| pxp_h1_chunk8K_ctx8K | 16.448 | 10.048 | 0.611x |
| pxp_h1_chunk8K_ctx64K | 105.215 | 82.224 | 0.781x |
| pxp_h1_chunk8K_ctx256K | 398.671 | 325.423 | 0.816x |
| pxp_h1_chunk16K_ctx64K | 190.928 | 150.736 | 0.789x |
| pxp_h1_chunk16K_ctx256K | 812.159 | 718.447 | 0.885x |
| pxp_h1_chunk32K_ctx64K | 308.592 | 256.016 | 0.830x |
| pxp_h1_chunk32K_ctx256K | 1631.447 | 1466.039 | 0.899x |
| pxp_h4_chunk1536_ctx8K | 14.496 | 12.352 | 0.852x |
| pxp_h4_chunk1536_ctx64K | 84.144 | 62.688 | 0.745x |
| pxp_h4_chunk1536_ctx256K | 300.575 | 245.880 | 0.818x |
| pxp_h4_chunk8K_ctx8K | 33.888 | 26.784 | 0.790x |
| pxp_h4_chunk8K_ctx64K | 383.775 | 312.720 | 0.815x |
| pxp_h4_chunk8K_ctx256K | 1722.342 | 1431.982 | 0.831x |
| pxp_h4_chunk16K_ctx64K | 733.904 | 595.976 | 0.812x |
| pxp_h4_chunk16K_ctx256K | 3409.222 | 2995.999 | 0.879x |
| pxp_h4_chunk32K_ctx64K | 1289.815 | 1078.296 | 0.836x |
| pxp_h4_chunk32K_ctx256K | 6651.685 | 5863.438 | 0.881x |
| pxd_fp8_h1_q1_b1_ctx8K | 3.200 | 3.072 | 0.960x |
| pxd_fp8_h1_q1_b1_ctx64K | 6.592 | 6.496 | 0.985x |
| pxd_fp8_h1_q1_b1_ctx100K | 8.448 | 8.640 | 1.023x |
| pxd_fp8_h1_q1_b1_ctx200K | 13.440 | 14.720 | 1.095x |
| pxd_fp8_h1_q1_b1_ctx256K | 16.160 | 17.952 | 1.111x |
| pxd_fp8_h1_q1_b16_ctx8K | 9.856 | 10.368 | 1.052x |
| pxd_fp8_h1_q1_b16_ctx64K | 53.216 | 55.264 | 1.038x |
| pxd_fp8_h1_q1_b16_ctx100K | 80.160 | 79.519 | 0.992x |
| pxd_fp8_h1_q1_b16_ctx200K | 146.879 | 146.807 | 1.000x |
| pxd_fp8_h1_q1_b16_ctx256K | 185.375 | 184.704 | 0.996x |
| pxd_fp8_h1_q1_b32_ctx8K | 16.192 | 17.920 | 1.107x |
| pxd_fp8_h1_q1_b32_ctx64K | 98.688 | 98.527 | 0.998x |
| pxd_fp8_h1_q1_b32_ctx100K | 146.944 | 146.688 | 0.998x |
| pxd_fp8_h1_q1_b32_ctx200K | 282.832 | 282.304 | 0.998x |
| pxd_fp8_h1_q1_b32_ctx256K | 358.719 | 358.175 | 0.998x |
| pxd_fp8_h1_q1_b128_ctx8K | 53.264 | 55.264 | 1.038x |
| pxd_fp8_h1_q1_b128_ctx64K | 358.351 | 357.887 | 0.999x |
| pxd_fp8_h1_q1_b128_ctx100K | 552.831 | 552.431 | 0.999x |
| pxd_fp8_h1_q1_b128_ctx200K | 1093.838 | 1092.798 | 0.999x |
| pxd_fp8_h1_q1_b128_ctx256K | 1398.222 | 1396.238 | 0.999x |
| pxd_fp8_h4_q1_b1_ctx8K | 3.200 | 3.136 | 0.980x |
| pxd_fp8_h4_q1_b1_ctx256K | 16.224 | 17.983 | 1.108x |
| pxd_fp8_h4_q1_b32_ctx8K | 16.160 | 18.016 | 1.115x |
| pxd_fp8_h4_q1_b32_ctx256K | 360.095 | 359.967 | 1.000x |
| pxd_bf16_h1_q1_b1_ctx8K | 4.000 | 3.936 | 0.984x |
| pxd_bf16_h1_q1_b1_ctx64K | 10.208 | 10.176 | 0.997x |
| pxd_bf16_h1_q1_b1_ctx100K | 13.952 | 13.856 | 0.993x |
| pxd_bf16_h1_q1_b1_ctx200K | 23.983 | 24.160 | 1.007x |
| pxd_bf16_h1_q1_b1_ctx256K | 29.440 | 29.664 | 1.008x |
| pxd_bf16_h1_q1_b16_ctx8K | 16.864 | 16.800 | 0.996x |
| pxd_bf16_h1_q1_b16_ctx64K | 98.399 | 104.896 | 1.066x |
| pxd_bf16_h1_q1_b16_ctx100K | 146.592 | 158.656 | 1.082x |
| pxd_bf16_h1_q1_b16_ctx200K | 281.519 | 304.543 | 1.082x |
| pxd_bf16_h1_q1_b16_ctx256K | 356.656 | 385.983 | 1.082x |
| pxd_bf16_h1_q1_b32_ctx8K | 29.408 | 29.696 | 1.010x |
| pxd_bf16_h1_q1_b32_ctx64K | 184.432 | 199.615 | 1.082x |
| pxd_bf16_h1_q1_b32_ctx100K | 282.159 | 304.575 | 1.079x |
| pxd_bf16_h1_q1_b32_ctx200K | 550.631 | 590.031 | 1.072x |
| pxd_bf16_h1_q1_b32_ctx256K | 701.631 | 746.719 | 1.064x |
| pxd_bf16_h1_q1_b128_ctx8K | 98.400 | 105.216 | 1.069x |
| pxd_bf16_h1_q1_b128_ctx64K | 701.967 | 748.799 | 1.067x |
| pxd_bf16_h1_q1_b128_ctx100K | 1088.735 | 1151.375 | 1.058x |
| pxd_bf16_h1_q1_b128_ctx200K | 2167.103 | 2266.759 | 1.046x |
| pxd_bf16_h1_q1_b128_ctx256K | 2771.567 | 2891.727 | 1.043x |
| pxd_bf16_h4_q1_b1_ctx8K | 4.000 | 3.968 | 0.992x |
| pxd_bf16_h4_q1_b1_ctx256K | 29.632 | 30.176 | 1.018x |
| pxd_bf16_h4_q1_b32_ctx8K | 29.537 | 30.496 | 1.032x |
| pxd_bf16_h4_q1_b32_ctx256K | 704.446 | 751.454 | 1.067x |
| pxd_fp8_h1_q4_b1_ctx8K | 3.169 | 3.136 | 0.990x |
| pxd_fp8_h1_q4_b1_ctx256K | 16.192 | 17.952 | 1.109x |
| pxd_fp8_h1_q4_b32_ctx8K | 16.160 | 17.953 | 1.111x |
| pxd_fp8_h1_q4_b32_ctx256K | 360.223 | 360.255 | 1.000x |

### Sparse attention, decode (single query token) (77 shapes)

| shape | Cake (us) | fi_sm90 (us) | speedup fi_sm90 / Cake |
|---|---|---|---|
| dec_g8x1_q1_b1_ctx8K | 5.632 | 5.696 | 1.011x |
| dec_g8x1_q1_b1_ctx64K | 5.729 | 5.888 | 1.028x |
| dec_g8x1_q1_b1_ctx100K | 5.728 | 5.760 | 1.006x |
| dec_g8x1_q1_b1_ctx200K | 5.792 | 5.856 | 1.011x |
| dec_g8x1_q1_b1_ctx256K | 5.760 | 5.824 | 1.011x |
| dec_g8x1_q1_b16_ctx8K | 9.568 | 9.439 | 0.987x |
| dec_g8x1_q1_b16_ctx64K | 9.568 | 9.408 | 0.983x |
| dec_g8x1_q1_b16_ctx100K | 9.376 | 9.152 | 0.976x |
| dec_g8x1_q1_b16_ctx200K | 9.312 | 9.184 | 0.986x |
| dec_g8x1_q1_b16_ctx256K | 9.503 | 9.280 | 0.976x |
| dec_g8x1_q1_b32_ctx8K | 12.800 | 13.248 | 1.035x |
| dec_g8x1_q1_b32_ctx64K | 13.184 | 13.376 | 1.015x |
| dec_g8x1_q1_b32_ctx100K | 12.920 | 13.216 | 1.023x |
| dec_g8x1_q1_b32_ctx200K | 13.312 | 13.472 | 1.012x |
| dec_g8x1_q1_b32_ctx256K | 13.216 | 13.376 | 1.012x |
| dec_g8x1_q1_b128_ctx8K | 31.872 | 35.200 | 1.104x |
| dec_g8x1_q1_b128_ctx64K | 31.951 | 35.424 | 1.109x |
| dec_g8x1_q1_b128_ctx100K | 31.904 | 35.456 | 1.111x |
| dec_g8x1_q1_b128_ctx200K | 31.744 | 35.136 | 1.107x |
| dec_g8x1_q1_b128_ctx256K | 31.872 | 35.392 | 1.110x |
| dec_g8x1_q2_b1_ctx8K | 5.984 | 6.080 | 1.016x |
| dec_g8x1_q2_b1_ctx100K | 6.080 | 6.144 | 1.011x |
| dec_g8x1_q2_b1_ctx256K | 6.112 | 6.144 | 1.005x |
| dec_g8x1_q2_b32_ctx8K | 19.040 | 19.008 | 0.998x |
| dec_g8x1_q2_b32_ctx100K | 19.872 | 20.847 | 1.049x |
| dec_g8x1_q2_b32_ctx256K | 19.872 | 20.864 | 1.050x |
| dec_g8x1_q4_b1_ctx8K | 6.240 | 6.304 | 1.010x |
| dec_g8x1_q4_b1_ctx100K | 6.656 | 6.623 | 0.995x |
| dec_g8x1_q4_b1_ctx256K | 6.752 | 6.688 | 0.991x |
| dec_g8x1_q4_b32_ctx8K | 26.560 | 27.776 | 1.046x |
| dec_g8x1_q4_b32_ctx100K | 31.775 | 34.880 | 1.098x |
| dec_g8x1_q4_b32_ctx256K | 31.712 | 35.311 | 1.114x |
| dec_g8x1_q8_b1_ctx8K | 6.465 | 6.496 | 1.005x |
| dec_g8x1_q8_b1_ctx100K | 7.808 | 7.520 | 0.963x |
| dec_g8x1_q8_b1_ctx256K | 7.935 | 7.520 | 0.948x |
| dec_g8x1_q8_b32_ctx8K | 34.432 | 36.288 | 1.054x |
| dec_g8x1_q8_b32_ctx100K | 56.151 | 55.648 | 0.991x |
| dec_g8x1_q8_b32_ctx256K | 57.152 | 57.200 | 1.001x |
| dec_g8x2_q1_b1_ctx8K | 6.016 | 6.080 | 1.011x |
| dec_g8x2_q1_b1_ctx64K | 6.080 | 6.176 | 1.016x |
| dec_g8x2_q1_b1_ctx256K | 6.176 | 6.176 | 1.000x |
| dec_g8x2_q1_b32_ctx8K | 20.000 | 20.896 | 1.045x |
| dec_g8x2_q1_b32_ctx64K | 19.808 | 20.896 | 1.055x |
| dec_g8x2_q1_b32_ctx256K | 20.400 | 21.184 | 1.038x |
| dec_g8x2_q1_b128_ctx8K | 57.599 | 58.176 | 1.010x |
| dec_g8x2_q1_b128_ctx64K | 57.376 | 58.384 | 1.018x |
| dec_g8x2_q1_b128_ctx256K | 56.816 | 57.583 | 1.014x |
| dec_g16x4_q1_b1_ctx8K | 6.560 | 6.623 | 1.010x |
| dec_g16x4_q1_b1_ctx64K | 6.720 | 6.551 | 0.975x |
| dec_g16x4_q1_b1_ctx256K | 6.688 | 6.624 | 0.990x |
| dec_g16x4_q1_b32_ctx8K | 31.791 | 35.057 | 1.103x |
| dec_g16x4_q1_b32_ctx64K | 31.648 | 35.648 | 1.126x |
| dec_g16x4_q1_b32_ctx256K | 31.872 | 35.072 | 1.100x |
| dec_g16x4_q1_b128_ctx8K | 104.704 | 101.744 | 0.972x |
| dec_g16x4_q1_b128_ctx64K | 105.296 | 102.400 | 0.973x |
| dec_g16x4_q1_b128_ctx256K | 105.984 | 102.975 | 0.972x |
| dec_g64x4_q1_b1_ctx8K | 7.616 | 7.521 | 0.988x |
| dec_g64x4_q1_b1_ctx64K | 7.760 | 7.504 | 0.967x |
| dec_g64x4_q1_b1_ctx256K | 7.808 | 7.584 | 0.971x |
| dec_g64x4_q1_b32_ctx8K | 32.288 | 35.616 | 1.103x |
| dec_g64x4_q1_b32_ctx64K | 32.431 | 36.159 | 1.115x |
| dec_g64x4_q1_b32_ctx256K | 32.736 | 35.760 | 1.092x |
| dec_g64x4_q1_b128_ctx8K | 106.432 | 103.375 | 0.971x |
| dec_g64x4_q1_b128_ctx64K | 106.080 | 103.344 | 0.974x |
| dec_g64x4_q1_b128_ctx256K | 106.848 | 103.808 | 0.972x |
| decc_tail_g8x1_q1_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q2_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q3_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q4_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q5_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q6_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q7_b3_ctx4173 | correctness only | correctness only | -
|
| decc_tail_g8x1_q8_b3_ctx4173 | correctness only | correctness only | -
|
| decc_shared_g8x2_q1_b4_ctx16397 | correctness only | correctness only
| - |
| decc_shared_g16x4_q1_b4_ctx16397 | correctness only | correctness only
| - |
| decc_shared_g64x4_q1_b4_ctx16397 | correctness only | correctness only
| - |
| decc_short_g8x1_q1_b2_ctx257 | correctness only | correctness only | -
|

### Sparse attention, prefill (20 shapes)

| shape | Cake (us) | fi_sm90 (us) | speedup fi_sm90 / Cake |
|---|---|---|---|
| pf_g8x1_s8K | 335.456 | 447.440 | 1.334x |
| pf_g8x1_s32K | 2492.605 | 1979.765 | 0.794x |
| pf_g8x1_s64K | 5554.444 | 4085.373 | 0.736x |
| pf_g8x1_s100K | 9077.189 | 6526.109 | 0.719x |
| pf_g8x1_s128K | 11959.958 | 8426.599 | 0.705x |
| pf_g8x1_s256K | 26272.024 | 18360.241 | 0.699x |
| pf_chunk_g8x1_chunk8K_ctx256K | 807.760 | 728.248 | 0.902x |
| pf_g64x4_s8K | 2461.272 | 1550.680 | 0.630x |
| pf_g64x4_s32K | 13420.194 | 7872.513 | 0.587x |
| pf_g64x4_s64K | 28531.109 | 16504.274 | 0.578x |
| pf_g64x4_s100K | 44867.449 | 26336.886 | 0.587x |
| pf_g64x4_s128K | 58337.045 | 34103.559 | 0.585x |
| pf_g64x4_s256K | 127636.202 | 76446.968 | 0.599x |
| pf_chunk_g64x4_chunk8K_ctx256K | 4035.297 | 3224.160 | 0.799x |
| pfc_g8x1_s4173_b2 | correctness only | correctness only | - |
| pfc_g8x1_s102405_b2 | correctness only | correctness only | - |
| pfc_g8x1_s133121_b2 | correctness only | correctness only | - |
| pfc_g16x4_s4173_b2 | correctness only | correctness only | - |
| pfc_g16x4_s102405_b2 | correctness only | correctness only | - |
| pfc_g16x4_s133121_b2 | correctness only | correctness only | - |

The family's only other Cake variant is the Blackwell MSA set, already
on main, with 32 generated programs for sm_100a and sm_103a; with this
PR, which ships only the sm_90a programs, the family covers sm_90a,
sm_100a and sm_103a, and there are no sm_80 or sm_120 variants.

---------

Co-authored-by: Rajas Mhaskar <rmhaskar@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [a48bf8a](https://github.com/flashinfer-ai/flashinfer/commit/a48bf8af3cdfb2da60ad5bbaefe2f9754f494c70)

- **作者**: Bo Li
- **时间**: 2026-10-21T08:28:25Z
- **提交信息**: refactor(comm): choose MNNVL handle types collectively and confirm them by allocating (#6734)

## 📌 Description

`MnnvlMemory` and `SymmDeviceMemory` choose between FABRIC handles and
POSIX file descriptors in different ways, and neither checks that FABRIC
handles actually work:

- `MnnvlMemory` AND-reduces a per-rank probe (FABRIC attribute plus NVML
fabric state).
- `SymmDeviceMemory` lets each rank decide on its own, which hangs if
ranks disagree.
- The FABRIC attribute alone is not enough. The user-mode driver 595,
for example, reports 1 without an IMEX channel, and
`cuMemCreate(FABRIC)` then fails with `CUDA_ERROR_NOT_PERMITTED`. Such
failures surface late, on one rank, while the others wait in a
collective.

This PR gives both classes one path, as proposed in the review of #5765.
There is no separate probe: on every allocation, a collective precheck
picks the type and the allocation itself confirms it. Nothing is cached
between allocations, so ranks that allocate over different groups cannot
disagree.

```text
choose_mnnvl_handle_type(comm, dev)     collective, stateless
    gather (host, FABRIC support, NVML fabric cluster UUID) from every rank
    one host:   FABRIC if every GPU supports it, else POSIX
    many hosts: FABRIC if every GPU supports it and all report the same
                non-zero cluster UUID; otherwise raise with each rank's reason + IMEX hint

allocate_mnnvl_handles(comm, dev, make_prop)     on every allocation
    attempt: create + export -> vote -> exchange -> import every peer -> vote
             (errors are collected per rank, nothing is mapped, a failed attempt
              releases everything it created)
    FABRIC failed on one host: warn (once per process) with the per-rank errors,
             retry this allocation with POSIX
    otherwise a failure raises with the per-rank errors (+ IMEX hint for FABRIC)
```

Changes:
- **`MnnvlMemory`**
  - Allocates through `allocate_mnnvl_handles`.
- Records each allocation's handle type; a checkpoint remap
(`remap_mnnvl_memory`) allocates again and records the type it ends
with.
- Sizes allocations with a granularity that fits both handle types,
since it places them in its address reservation before the type is
settled.
- Exposes `MnnvlMemory.uses_fabric_handles(comm, dev_id)` (the precheck)
and `MnnvlMemory(...).fabric_handles` (what an allocation uses).
- Removes `_resolve_fabric_support` / `_probe_fabric_supported` /
`_fabric_supported`, and the duplicated hostname check before the fd
exchange.
- **`SymmDeviceMemory`**
  - Allocates its unicast buffers through the same path.
- Builds the multicast exchange on the type the unicast buffers settled
on.
  - `make_handle_exchanger`, its per-rank decision, is removed.
- **`NVLinkOneSidedAlltoAll` CFT**
- The capability check follows the collective precheck instead of
probing FABRIC per rank.
- `_bind_cft` disables CFT if the workspace fell back to POSIX file
descriptors.
- `is_mnnvl_fabric_supported` is unchanged.
- **Docs**: new `docs/design_docs/symmetric_memory.md` describes what
`MnnvlMemory` and `SymmDeviceMemory` each provide, the allocation
protocol above, and the CFT interaction; linked from `docs/api/comm.rst`
and the moe_ep architecture doc.

Behavior:
- On a single host, FABRIC is still preferred when it works, including
8xB200 nodes whose `clusterUuid` is all zeros.
- On a single host where FABRIC is advertised but unusable, the result
is POSIX with a warning instead of a hang or late error.
- Across hosts without one NVLink domain, there is an early error that
names each rank's problem.

## 🔍 Related Issues

- Alternative to #5765 (see the review there).

## 🧪 Tests

- New `tests/comm/test_mnnvl_handle_type.py` (single process, scripted
peers):
- the choice on one host and across hosts, including each rejection
reason;
- single-host fallback on every allocation (warning once) and the
no-fallback cases;
  - the granularity that fits both handle types;
- the attempt's votes and cleanup, including a failed file descriptor
exchange.
- `tests/moe_ep/test_communication.py`: the CFT gate follows the handle
type.
- On 4x B300 (driver 620.22, CUDA 13.5) at 48f257472, each with and
without the IMEX channel (FABRIC and POSIX respectively, confirmed via
`MnnvlMemory.fabric_handles`):
  - `mpirun -np 4 tests/comm/test_mnnvl_memory.py`: 2 passed.
- `mpirun -np 4 tests/comm/test_trtllm_mnnvl_allreduce.py`
(SymmDeviceMemory with multicast): 276 passed.
  - `mpirun -np 4 tests/comm/test_mnnvl_moe_alltoall.py`: 17 passed.
- `torchrun 4 tests/moe_ep/test_moe_ep_communication_multirank.py`
(includes checkpoint remap): 13 passed.
- `tests/moe_ep/test_nvlink_one_sided.py`: 26 passed, 18 skipped with
FABRIC; 25 passed, 19 skipped with POSIX (the extra skip is the CFT
case).
- Across hosts at `48f257472` on 2x GB200 nodes (8 ranks, one NVL72
rack, driver 580.126.20, CUDA 13.1, `srun --mpi=pmix`), i.e. the
multi-host FABRIC path with a shared cluster UUID, all on every rank:
  - `test_mnnvl_memory.py`: 2 passed.
  - `test_trtllm_mnnvl_allreduce.py`: 276 passed.
  - `test_mnnvl_moe_alltoall.py`: 17 passed.
- `test_moe_ep_communication_multirank.py` (the MPI-launchable copy from
#6621): 13 passed.
- `pre-commit run mypy --all-files` passes.

## Reviewer Notes

- The single-host fallback on a FABRIC failure is unit-tested only. The
machines available here report the FABRIC attribute as 0 when there is
no IMEX channel, so they take the POSIX path directly.
- Like `is_mnnvl_fabric_supported`, the NVML query uses the CUDA device
index.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved symmetric-memory setup by coordinating handle selection and
allocation across participating ranks, with cleanup of partial
allocations on failure.
* Single-host setups can fall back to POSIX handles if FABRIC allocation
fails. Multi-host setups require compatible FABRIC support and report
rank-specific errors when requirements are not met.
* Prevented CFT from being selected for workspaces using POSIX handles,
and added a warning when CFT is disabled for this reason.
* **Documentation**
* Added guidance on symmetric memory, handle selection, allocation
fallback, and NVLink communication behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [7c866e8](https://github.com/flashinfer-ai/flashinfer/commit/7c866e85d3bb8095ebb247cdca42a56c2a4cab19)

- **作者**: eigen
- **时间**: 2026-10-21T08:12:58Z
- **提交信息**: perf(cake_causal_conv1d): with grad add channel-selected backward programs for C=512 (sm_103a, sm_107a) and C >= 2048 (sm_107a) (#6930)

The `cake_causal_conv1d_train` kernel, a packed width-4 depthwise causal
conv fused with SiLU, has one data-type variant (BF16 in/out with FP32
math) and a forward and a backward program per architecture; #6874 added
a second, channel-selected backward program. This PR adds more
channel-selected backward programs, which the host selects by channel
count C, and changes no forward program. On sm_103a (GB300), one new
backward program covers 512 <= C < 768 (the eight C=512 shapes); all
other shapes keep the previous programs. On sm_107a (R200), two new
backward programs cover 512 <= C < 1024 (the eight C=512 shapes) and C
>= 2048 (three shapes); shapes with C < 512 and with 1024 <= C < 2048
keep the previous programs. On sm_100a (B200) no program changes, and
every shape keeps the previous compiled kernel. Against the previous
Cake version of this backward (the programs shipped in #6874), the
geomean speedup (previous latency / this PR's latency) across all 14
shapes is 1.0094 on GB300, 1.0008 on B200 (unchanged kernels, run-to-run
noise) and 1.0264 on R200. On the shapes the host routes to a new
program, the per-shape speedup ranges from 1.0027 to 1.0233 on GB300
(eight shapes, geomean 1.0164). On R200 the eleven routed shapes have a
geomean of 1.0331: the eight C=512 shapes range from 0.9908 to 1.0513
(one shape, S=249866, is 0.9 % slower), and the three C >= 2048 shapes
range from 1.0316 to 1.0347.

**Backward latency, NVIDIA GB300 (sm_103a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 145.2 | 142.5 | 1.0189 |
| 245028 | 512 | 149.8 | 147.9 | 1.0132 |
| 249866 | 512 | 152.2 | 148.7 | 1.0233 |
| 250340 | 512 | 150.5 | 148.0 | 1.0168 |
| 258574 | 512 | 155.3 | 152.8 | 1.0168 |
| 259042 | 512 | 157.0 | 153.4 | 1.0232 |
| 259584 | 512 | 156.5 | 154.0 | 1.0163 |
| 261393 | 512 | 156.0 | 155.6 | 1.0027 |
| 250340 | 128 | 60.3 | 60.3 | 0.9995 |
| 250340 | 256 | 94.4 | 94.4 | 0.9997 |
| 250340 | 1024 | 272.4 | 271.6 | 1.0027 |
| 250340 | 2048 | 545.6 | 546.1 | 0.9991 |
| 250340 | 4096 | 1053.5 | 1053.3 | 1.0002 |
| 250340 | 8192 | 2060.9 | 2060.5 | 1.0002 |

Rows other than the eight C=512 shapes keep the previous program (same
compiled kernel), so their latency is unchanged.

**Backward latency, NVIDIA B200 (sm_100a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 157.8 | 157.9 | 0.9998 |
| 245028 | 512 | 161.2 | 160.9 | 1.0020 |
| 249866 | 512 | 166.1 | 166.0 | 1.0006 |
| 250340 | 512 | 164.6 | 164.1 | 1.0030 |
| 258574 | 512 | 169.0 | 168.0 | 1.0061 |
| 259042 | 512 | 169.8 | 169.8 | 0.9995 |
| 259584 | 512 | 171.9 | 172.1 | 0.9990 |
| 261393 | 512 | 166.1 | 166.3 | 0.9988 |
| 250340 | 128 | 62.6 | 62.4 | 1.0028 |
| 250340 | 256 | 102.3 | 102.3 | 0.9997 |
| 250340 | 1024 | 295.8 | 295.9 | 0.9999 |
| 250340 | 2048 | 611.0 | 610.8 | 1.0003 |
| 250340 | 4096 | 1181.7 | 1181.6 | 1.0000 |
| 250340 | 8192 | 2438.3 | 2438.3 | 1.0000 |

Every sm_100a shape keeps the previous program (same compiled kernel);
the differences are run-to-run noise.

**Backward latency, NVIDIA R200 (sm_107a), CUDA 13.4**

| S | C | previous (us) | this PR (us) | ratio (previous / this PR) |
|---:|---:|---:|---:|---:|
| 239718 | 512 | 97.7 | 95.3 | 1.0247 |
| 245028 | 512 | 99.3 | 95.4 | 1.0418 |
| 249866 | 512 | 101.6 | 102.6 | 0.9908 |
| 250340 | 512 | 101.3 | 96.4 | 1.0513 |
| 258574 | 512 | 104.0 | 99.8 | 1.0417 |
| 259042 | 512 | 104.6 | 100.2 | 1.0436 |
| 259584 | 512 | 105.2 | 101.9 | 1.0320 |
| 261393 | 512 | 105.4 | 101.4 | 1.0403 |
| 250340 | 128 | 39.8 | 39.4 | 1.0093 |
| 250340 | 256 | 57.9 | 57.9 | 0.9989 |
| 250340 | 1024 | 176.1 | 176.3 | 0.9985 |
| 250340 | 2048 | 356.7 | 345.6 | 1.0323 |
| 250340 | 4096 | 673.8 | 651.2 | 1.0347 |
| 250340 | 8192 | 1312.4 | 1272.2 | 1.0316 |

Rows with C < 512 and with 1024 <= C < 2048 keep the previous program
(same compiled kernel), so their latency is unchanged.

In Cake, the `cake_causal_conv1d_train` family ships the forward and the
backward on sm_100a, sm_103a and sm_107a, and has no other data-type or
layout variants.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added causal Conv1D training backward support for newer GPU
architectures, including SM103 and SM107.
- Added architecture- and channel-specific execution paths for broader
hardware compatibility.
- Added optimized bfloat16 gradient processing, including
document-boundary handling.

- **Bug Fixes**
- Improved selection of the appropriate backward execution path for each
channel configuration.

- **Tests**
- Expanded validation of architecture routing, channel thresholds,
fallback behavior, and boundary conditions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [fc1790f](https://github.com/flashinfer-ai/flashinfer/commit/fc1790f4ec33a4df84ae9e6d1dcc9231fde7fd10)

- **作者**: eigen
- **时间**: 2026-10-21T08:10:05Z
- **提交信息**: feat(cake_gdp): add Gated DeltaProduct decode backend for Nemotron 4 (sm_100a, sm_103a) (#6883)

This PR adds Cake's Gated DeltaProduct (GDP) decode kernel for Nemotron
4 as `flashinfer.cake_gdp.cake_gated_delta_product_mtp`. GDP is the
DeltaNet recurrence with n Householder sub-steps per token, where n = 1
is Gated DeltaNet. The kernel handles single-token decode and
multi-token-prediction decode with 1 ≤ T ≤ 16, K = 128, V = 64, BF16
q/k/v/o, an FP32 recurrent state in a state pool addressed by
per-sequence slot indices, and fused gating. In Cake, this decode kernel
has:
- two bodies chosen by shape: a body where each thread owns state rows,
used for T ≥ 4 and for T = 1 when batch × heads > 160, and a split-V
body for T = 1 when batch × heads ≤ 160;
- fixed programs for T = 1 / 4 / 8 with n = 3, plus one run-time program
for any T ≤ 16 and n = 1..4;
- one data-type form: BF16 activations with FP32 state.

This PR delivers the whole decode variant (both bodies and all programs)
for sm_100a (B200 / GB200) and sm_103a (GB300). The baseline is
FlashInfer PR #6198 / #6250 (faster of the two per row), run on the same
GPU and shapes with cold L2. Against it, Cake is faster on 47 of 48
Nemotron 4 decode shapes on GB300 (0.98–3.95×; the only row below 1.0 is
HV = 10, B = 64, T = 1) and on 48 of 48 on GB200 (1.01–3.99×). The
shapes are HV ∈ {80, 20, 10, 24} (80 = Nemotron 4 Ultra, 24 = Nemotron 4
Nano) × B ∈ {1, 16, 64, 256} × T ∈ {1, 4, 8}. Latencies are median µs
per launch, and speedup = FlashInfer / Cake.

### NVIDIA GB300 (sm_103a), CUDA 13.4 — 48 rows, Cake faster on 47/48

| Heads (HV) | Batch (B) | Tokens (T) | FlashInfer (µs) | Cake (µs) |
Speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 5.5 | 5.1 | 1.08 |
| 80 | 1 | 4 | 14.3 | 6.4 | 2.23 |
| 80 | 1 | 8 | 24.7 | 8.3 | 2.98 |
| 80 | 16 | 1 | 20.7 | 20.0 | 1.03 |
| 80 | 16 | 4 | 68.2 | 26.0 | 2.62 |
| 80 | 16 | 8 | 159.4 | 43.4 | 3.67 |
| 80 | 64 | 1 | 66.2 | 62.3 | 1.06 |
| 80 | 64 | 4 | 243.5 | 80.8 | 3.01 |
| 80 | 64 | 8 | 547.0 | 142.2 | 3.85 |
| 80 | 256 | 1 | 248.4 | 226.5 | 1.10 |
| 80 | 256 | 4 | 924.6 | 301.4 | 3.07 |
| 80 | 256 | 8 | 2105.4 | 541.2 | 3.89 |
| 20 | 1 | 1 | 5.1 | 4.2 | 1.21 |
| 20 | 1 | 4 | 7.0 | 6.0 | 1.17 |
| 20 | 1 | 8 | 10.5 | 7.9 | 1.33 |
| 20 | 16 | 1 | 9.9 | 8.3 | 1.19 |
| 20 | 16 | 4 | 22.9 | 11.6 | 1.97 |
| 20 | 16 | 8 | 58.2 | 18.2 | 3.20 |
| 20 | 64 | 1 | 20.8 | 20.4 | 1.02 |
| 20 | 64 | 4 | 67.8 | 26.2 | 2.59 |
| 20 | 64 | 8 | 159.5 | 43.3 | 3.68 |
| 20 | 256 | 1 | 66.3 | 60.7 | 1.09 |
| 20 | 256 | 4 | 243.5 | 80.9 | 3.01 |
| 20 | 256 | 8 | 552.1 | 142.2 | 3.88 |
| 10 | 1 | 1 | 4.8 | 4.2 | 1.14 |
| 10 | 1 | 4 | 6.5 | 5.9 | 1.10 |
| 10 | 1 | 8 | 9.5 | 7.8 | 1.22 |
| 10 | 16 | 1 | 8.7 | 6.0 | 1.45 |
| 10 | 16 | 4 | 20.2 | 8.9 | 2.27 |
| 10 | 16 | 8 | 31.3 | 12.3 | 2.54 |
| 10 | 64 | 1 | 12.5 | 12.7 | 0.98 |
| 10 | 64 | 4 | 41.4 | 17.2 | 2.41 |
| 10 | 64 | 8 | 84.9 | 27.1 | 3.13 |
| 10 | 256 | 1 | 36.7 | 33.4 | 1.10 |
| 10 | 256 | 4 | 127.8 | 43.9 | 2.91 |
| 10 | 256 | 8 | 296.6 | 75.1 | 3.95 |
| 24 | 1 | 1 | 5.3 | 4.3 | 1.23 |
| 24 | 1 | 4 | 7.2 | 6.0 | 1.20 |
| 24 | 1 | 8 | 10.8 | 7.9 | 1.37 |
| 24 | 16 | 1 | 10.5 | 8.5 | 1.24 |
| 24 | 16 | 4 | 24.0 | 12.1 | 1.98 |
| 24 | 16 | 8 | 58.9 | 18.7 | 3.15 |
| 24 | 64 | 1 | 27.4 | 23.4 | 1.17 |
| 24 | 64 | 4 | 83.9 | 30.3 | 2.77 |
| 24 | 64 | 8 | 186.4 | 50.8 | 3.67 |
| 24 | 256 | 1 | 78.7 | 70.8 | 1.11 |
| 24 | 256 | 4 | 289.0 | 95.4 | 3.03 |
| 24 | 256 | 8 | 662.2 | 169.3 | 3.91 |

### NVIDIA GB200 (sm_100a), CUDA 13.4 — 48 rows, Cake faster on 48/48

| Heads (HV) | Batch (B) | Tokens (T) | FlashInfer (µs) | Cake (µs) |
Speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 5.6 | 5.2 | 1.08 |
| 80 | 1 | 4 | 14.5 | 6.4 | 2.27 |
| 80 | 1 | 8 | 25.2 | 8.4 | 3.00 |
| 80 | 16 | 1 | 21.8 | 20.2 | 1.08 |
| 80 | 16 | 4 | 68.9 | 26.4 | 2.61 |
| 80 | 16 | 8 | 161.2 | 43.7 | 3.69 |
| 80 | 64 | 1 | 69.2 | 63.0 | 1.10 |
| 80 | 64 | 4 | 245.4 | 83.0 | 2.96 |
| 80 | 64 | 8 | 541.8 | 142.3 | 3.81 |
| 80 | 256 | 1 | 255.3 | 227.1 | 1.12 |
| 80 | 256 | 4 | 931.0 | 304.2 | 3.06 |
| 80 | 256 | 8 | 2064.7 | 540.2 | 3.82 |
| 20 | 1 | 1 | 5.2 | 4.2 | 1.24 |
| 20 | 1 | 4 | 6.9 | 5.9 | 1.17 |
| 20 | 1 | 8 | 10.6 | 7.9 | 1.34 |
| 20 | 16 | 1 | 10.1 | 8.4 | 1.20 |
| 20 | 16 | 4 | 23.3 | 11.8 | 1.97 |
| 20 | 16 | 8 | 58.9 | 18.1 | 3.25 |
| 20 | 64 | 1 | 21.6 | 20.6 | 1.05 |
| 20 | 64 | 4 | 68.8 | 26.6 | 2.59 |
| 20 | 64 | 8 | 161.7 | 43.4 | 3.73 |
| 20 | 256 | 1 | 69.3 | 61.2 | 1.13 |
| 20 | 256 | 4 | 245.2 | 83.2 | 2.95 |
| 20 | 256 | 8 | 548.8 | 142.4 | 3.85 |
| 10 | 1 | 1 | 5.0 | 4.2 | 1.19 |
| 10 | 1 | 4 | 6.4 | 5.9 | 1.08 |
| 10 | 1 | 8 | 9.7 | 7.8 | 1.24 |
| 10 | 16 | 1 | 9.0 | 6.2 | 1.45 |
| 10 | 16 | 4 | 20.8 | 8.9 | 2.34 |
| 10 | 16 | 8 | 31.9 | 12.6 | 2.53 |
| 10 | 64 | 1 | 13.0 | 12.9 | 1.01 |
| 10 | 64 | 4 | 42.8 | 17.4 | 2.46 |
| 10 | 64 | 8 | 86.9 | 27.3 | 3.18 |
| 10 | 256 | 1 | 38.4 | 33.7 | 1.14 |
| 10 | 256 | 4 | 130.0 | 44.7 | 2.91 |
| 10 | 256 | 8 | 301.4 | 75.5 | 3.99 |
| 24 | 1 | 1 | 5.5 | 4.3 | 1.28 |
| 24 | 1 | 4 | 7.2 | 5.9 | 1.22 |
| 24 | 1 | 8 | 11.0 | 7.9 | 1.39 |
| 24 | 16 | 1 | 10.8 | 8.6 | 1.26 |
| 24 | 16 | 4 | 24.8 | 12.4 | 2.00 |
| 24 | 16 | 8 | 60.5 | 18.7 | 3.24 |
| 24 | 64 | 1 | 28.8 | 23.5 | 1.23 |
| 24 | 64 | 4 | 85.4 | 30.5 | 2.80 |
| 24 | 64 | 8 | 189.8 | 51.0 | 3.72 |
| 24 | 256 | 1 | 83.1 | 70.8 | 1.17 |
| 24 | 256 | 4 | 292.6 | 98.4 | 2.97 |
| 24 | 256 | 8 | 642.9 | 169.4 | 3.80 |

With this PR, Cake ships this kernel family on sm_100a and sm_103a; the
chunked varlen prefill variant of the same family
(`chunk_gated_delta_product` with `backend="cake"`) follows in a
separate PR, and an sm_90a port is planned.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added Cake GDP decode and multi-token verification for compatible CUDA
GPUs.
- Exposed a public API with gated decay, state updates, optional
normalization, scaling, scatter indices, output buffering, and
configurable state writeback.
  - Added capability detection and FP16/BF16 input support.
  - Added architecture-specific prebuilt and JIT kernel loading.

- **Documentation**
- Added API documentation for Cake GDP decode and multi-token
verification.

- **Tests**
- Added comprehensive coverage for outputs, state updates, indexing,
layouts, validation, reproducibility, and unsupported devices.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [52fbbd0](https://github.com/flashinfer-ai/flashinfer/commit/52fbbd090ca9c85b69c3a94420e360d27779b366)

- **作者**: SeongJun Lee
- **时间**: 2026-10-21T07:40:20Z
- **提交信息**: feat(page): add 4over6 block scales to the NVFP4 slot-mapping KV writer (#6013)

<!-- .github/pull_request_template.md -->

## 📌 Description

`nvfp4_quantize_append_paged_kv_cache_with_slot_mapping` (added in
`#3740`) always uses the standard `amax / 6` block scale. vLLM's
`nvfp4_4over6` KV cache dtype also tries `amax / 4` for each 16-value
block and keeps whichever reconstructs the block with less squared
error, so it cannot use this writer today.

This PR adds an opt-in `nvfp4_4over6: Optional[NVFP44Over6Config] =
None` to that writer, reusing the existing recipe class:

- The second candidate is `sf * 1.5`, as in the existing 4over6
quantizer, and is kept only on a strictly lower MSE (ties keep 6). The
stored format is unchanged, so readers need no change.
- Only `err_mode=MSE` without `err_use_fast_math` is implemented; other
recipes raise. `e4m3_max` only pins a per-tensor global scale, which
this writer takes from the caller.
- The default is `None` rather than reading `FLASHINFER_NVFP4_4OVER6*`,
so existing callers do not change when those variables are set for GEMM
quantization.
- 4over6 is compiled only into a separate `page_nvfp4_4over6` JIT module
(`-DFLASHINFER_NVFP4_APPEND_4OVER6`), built on the first 4over6 call.
The default `page` module keeps the same flags and build time (24 s on
SM80), its 51 kernels have the same SASS as `main` (`cuobjdump -sass`),
and default outputs are byte-identical. `csrc/` is unchanged.

Only the slot-mapping writer selects the 4over6 module; every other page
API keeps using the default module. The new module is JIT-only. If it is
not already cached, `FLASHINFER_DISABLE_JIT` causes
`MissingJITCacheError`; the call never falls back to standard
quantization.

Cost on SM80 (bf16, 8 KV heads, head_dim 128, 16384 tokens): 0.51 ms
with the default recipe, 1.49 ms with 4over6, plus a one-time 31 s build
of `page_nvfp4_4over6`.

## 🔍 Related Issues

Follow-up to `#3740`.

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

`test_nvfp4_quantize_append_paged_kv_cache_with_slot_mapping_4over6`
checks that 4over6 never raises a block's squared error and lowers it
for some blocks. On SM80, `tests/attention/test_page.py` and
`tests/attention/test_mla_page.py`: 171 passed, 1 skipped. `tests/trace
-k "page or slot or append"`: 221 passed, 31 skipped.

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


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional 4-over-6 quantization mode for NVFP4 slot-mapped
paged KV cache append. When enabled, it selects the scaling option with
lower measured reconstruction error.
* The new mode supports MSE configuration without fast math; the
standard quantization behavior remains the default.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>

### [da992ed](https://github.com/flashinfer-ai/flashinfer/commit/da992ed9919604c5eb6dc255c63f5e89a466452c)

- **作者**: XuechengW
- **时间**: 2026-10-21T07:09:47Z
- **提交信息**: [SM90] MegaMoE: fix workspace cleanup; enable push dispatch on H200; support other models (#6517)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #6343 (SM90 FP4 MegaMoE):

1. **Cleanup fix:** with `single_active_dispatch_warp`, the inactive
dispatch warp cleaned the workspace with empty expert counts and left
pool blocks ≥ 32 of hot experts stale, so the next launch failed (H20,
97–128 tokens per rank, e.g. CUDA-graph capture); it now fetches the
counts first (outputs bitwise unchanged, timing within noise).
2. **H200 push dispatch:** add measured H200 EP8 buckets that enable
push for M ≤ 32 on DeepSeek-V4-Flash and MiMo-V2.5-Pro, and M ≤ 64 on
DeepSeek-V4-Pro (rotated pool at M 33–64), saving about 10 µs per call
(1.03–1.16x kernel time, bitwise-identical outputs; H20 and EP4 plans
unchanged).
3. **Other models:** accept any expert count that divides across ranks,
keep the selected plans compilable for untuned geometries (H20 buckets
match the full geometry; the planner checks the full fused shared-memory
layout, which grows with the expert count, and falls back to the next
legal smaller tile when the chosen one does not fit; unsupported shapes
raise `ValueError`), and allow push only on validated plans, so Kimi-K2,
DeepSeek-V3, GLM-4.x and Qwen3 shapes now run correctly while plans of
the three tuned geometries are unchanged.
4. **Usage docs:** the weight-preparation docs now state what callers
must convert before `transform_{nvfp4,mxfp4}_weights_for_mega_moe`:
Marlin byte order (checkpoints are usually low-nibble-first), scales
inside the decoder range (NVFP4 `6 * scale <= 448`; MXFP4 `2^-5`–`2^6`
for groups with nonzero codes, otherwise outputs silently saturate or
flush), and the excess moved into per-expert global scales passed at run
time; the module example shows the full flow.
5. **Framework hooks:** add `MegaMoESymmBuffer.prewarm()`, which builds
every NVFP4 module `nvfp4_mega_moe` can select up to capacity (sharded
across ranks, before CUDA graph capture), and `commit_staged()`, which
accepts rows a producer wrote directly into the now-documented staging
views (`x`, `x_sf`, `topk_idx`, `topk_weights`), so integrations no
longer reach into JIT internals or buffer fields.

**How to use:** FlashInfer only provides the kernels and the layout
transforms; frameworks convert checkpoint tensors to the format above at
load time, call `prewarm()` once, and stage inputs with `stage()` or in
place plus `commit_staged()` (the SGLang integration does this for
`nvidia/DeepSeek-V4-Flash-NVFP4`, where about 51% of blocks would
saturate without rebalancing).

## 🔍 Related Issues

Follow-up to #6343.

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

- `test_hot_expert_workspace_cleanup` reproduces fix 1: it fails before
the fix on 8×H20 and passes after.
- New CPU tests cover the H200 buckets, the counter-dispatch limits and
plan legality for other geometries, including 2048 and 8192 experts
(every plan fits shared memory); every fused and split plan selected for
12 geometries (the three tuned models, six common shapes, 1024 / 2048 /
8192 experts) compiles on SM90, and plans of the tuned and previously
validated geometries are unchanged.
- `test_nvfp4_prewarm_and_direct_staging` checks that after `prewarm()`
no fused or split call compiles a new module, that in-place staging plus
`commit_staged()` gives correct results under CUDA graphs, and that
out-of-range counts are rejected.
- `tests/moe/test_megamoe_fp4_{sm90,ep,weights}.py`: 73 passed on
8×H200.

## Reviewer Notes


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional JIT prewarming for NVFP4 workloads across supported
token counts.
* Added direct staging support for efficiently preparing dispatch
inputs.
* Added support for transformed NVFP4 weights with per-expert global
scales.
* Improved dispatch planning across supported hardware configurations
and workload shapes.

* **Bug Fixes**
* Fixed workspace cleanup for inactive dispatch paths, improving
repeated CUDA Graph execution reliability.
  * Improved expert-count handling during dispatch cleanup.

* **Documentation**
* Clarified supported weight formats, scale requirements, dispatch
behavior, and configuration limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: ouershua2299 <180947746+ouershua2299@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bf044ba](https://github.com/flashinfer-ai/flashinfer/commit/bf044ba86e8ec7ff5af11034378c6ff6568e4a8d)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-21T07:07:54Z
- **提交信息**: perf(gemm): fuse the a_scale * b_scale product into the CuTe-DSL bmm_fp8 epilogue (#6800)

<!-- .github/pull_request_template.md -->

## 📌 Description

Small follow-up to #6521 for the SM107 (Rubin) CuTe-DSL `bmm_fp8`
backend, split out of #6713 so it can merge on its own.

FP8 GEMM output is multiplied by two per-tensor dequantization scales.
The Rubin CuTe-DSL kernel already applies a scale in its epilogue (the
stage that converts the fp32 accumulator to the output type), but it
expected one combined scale, so `bmm_fp8_cute_dsl` computed `(a_scale *
b_scale).float().view(1)` with a torch op on every call. That is one
extra kernel launch per GEMM (two when a scale is not fp32 and needs a
cast), pure launch latency that matters most at the small-M end, and it
is counted inside the time the autotuner attributes to this backend when
it races it against cuBLAS/cuDNN/CUTLASS.

The kernel now takes `a_scale_tensor` and `b_scale_tensor` and forms the
product itself at the point where it already read the combined scale
(`output_scale = a_scale_tensor[0] * b_scale_tensor[0]`: two scalar
loads and one multiply per CTA). The wrapper only reshapes each scale to
a 1-element view, which is free, and casts only when a scale is not
already fp32. CUDA-graph behaviour is unchanged: both scales are still
read on device at kernel time.

The Blackwell base kernel class (`bmm_fp8_blackwell.py`) shares the
compiled `bmm` CuTe-JIT entry point with the Rubin subclass, so its
`__call__`/`kernel` signatures change the same way; it has no other
callers in the repo. Compiled-kernel cache keys never included the
scales, so nothing recompiles because of this change.

On the Rubin Core-Models study this backend is already the fastest
kernel for the 9216x8192x1280 `bmm_fp8` shape; this removes a fixed
per-call cost from it.

## 🔍 Related Issues

Split out of #6713. Follow-up to #6521.

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

No new test: the existing `tests/gemm/test_bmm_fp8.py` cute-dsl cases
(autotune on/off, all three output dtypes) and
`tests/trace/test_bmm_fp8_reference_correctness.py` check the kernel
output against a reference and therefore exercise the in-kernel scale
product directly. They run in the VR NVL72 lane. Pre-commit (mypy, ruff)
passes locally.

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

Before/after kernel-level speedup for this backend on GR100 will be
posted as a follow-up comment once a node is available; the change
removes one launch per call and does not alter the GEMM itself.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* FP8 batched matrix multiplication now accepts separate scaling factors
for the A and B inputs. The factors are combined during output scaling,
so callers can provide each input’s scale directly instead of supplying
a precombined output scale. This option is available for supported
Blackwell and Rubin operations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4675
- **最后更新**: 2026-10-22T00:46:13Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

### 1. 主要更新类型
此提交属于功能新增（feat），专注于在Apple Silicon平台上集成和优化新模型支持，未涉及Bug修复或文档重构。

### 2. 关键变更点及其与项目整体方向的关系
- **新增内容**：引入FastH3 Omni (Ref2VA)模型，利用MLX框架在Apple Silicon（M系列芯片）上实现高效运行。PR #2000标志着项目在跨平台兼容性上的重要扩展。
- **与项目方向关系**：FastVideo作为视频AI推理平台，其README强调快速入门和多平台文档，此更新直接响应了项目对易用性和硬件适配的追求，推动从通用加速向Apple生态的深度融合，体现了项目“高效视频生成”的核心目标。

### 3. 对项目的影响和潜在意义
- **直接影响**：扩展了项目在macOS设备上的可用性，用户无需依赖Windows或Linux硬件即可运行高级视频模型，降低了入门门槛。
- **潜在意义**：增强项目社区吸引力，可能引发更多Apple用户贡献；长期看，支持MLX可提升能效和电池友好性，优化模型在边缘设备上的部署，为视频AI的移动化应用铺平道路。

### 4. 值得关注的技术点
- **MLX框架利用**：Apple的MLX专为Apple Silicon设计，支持动态图和内存优化，此提交突出了其在视频生成中的高效推理能力。
- **Ref2VA技术**：参考到视频对齐（Ref2VA）机制，结合Omni（全能）设计，可能涉及多模态输入处理，值得深入研究其在零样本视频生成中的作用。
- **性能权衡**：在有限资源（如统一内存）下实现H3模型的变体，体现了对Apple硬件特性的针对性优化。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
README显示FastVideo是聚焦文档、快速入门和协作的视频AI项目，强调用户友好和持续迭代（如每周开发会议）。此提交通过添加Apple Silicon支持，直接强化了Quick Start指南，提升了项目在多样化硬件环境下的竞争力。它不仅丰富了 Cookbook资源，还可能激励开发者在会议上讨论跨平台优化，从而加速项目向普惠化、高性能视频生成方向演进，确保在AI视频领域的领先地位。总体而言，这一功能将推动项目从核心推理向生态扩展，吸引更多硬件敏感的用户群体。

## 详细提交记录

### [fa2d132](https://github.com/hao-ai-lab/FastVideo/commit/fa2d1324c60050cd65209c6aaeac470e7fb412f5)

- **作者**: Aryan Kumar
- **时间**: 2026-10-21T19:01:54Z
- **提交信息**: [feat]: FastH3 Omni (Ref2VA) on Apple Silicon MLX (#2000)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34773
- **最后更新**: 2026-10-22T00:48:22Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Sayak Paul, Christopher, Muhammad Usman Mateen

## AI分析总结

# HuggingFace Diffusers 昨日提交分析

## 1. 主要更新类型

- **功能新增**：为 LTX-2 视频生成管线引入 `motion_speed` 参数，支持慢动作控制
- **Bug 修复**：修复 torchao 旧版本导入模型失败的问题、修复 CI 流水线命名错误
- **CI 优化**：调整测试步骤命名、切换 Python 版本至 3.11
- **文档更新**：为 LTX-2 添加端到端的 `motion_speed` 使用示例

## 2. 关键变更点及与项目方向的关系

- **LTX-2 `motion_speed` 支持**（核心提交）：这是最具实质性的功能变更。开发过程中经历了从 `conditioning_frame_rate` 到 `motion_speed` 的命名演进，最终选择了更直观的语义——`motion_speed` 默认为 1.0，表示相对真实时间的运动速度，位置时间轴基于 `frame_rate / motion_speed` 条件化。这直接对接 LTX-2.5 Slow-Motion-Control LoRA 等适配器的需求，使项目在**可控视频生成**领域保持竞争力。
- **两阶段生成一致性提示**：文档中特别指出多阶段生成时需向两个阶段传递相同的 `motion_speed`，反映了 diffusers 对**生成管线可用性和用户体验**的关注。
- **torchao 兼容性修复**：`torchao_quantizer.py` 无条件导入 `FqnToConfig`，但该类仅在 torchao ≥ 0.15 中存在，导致旧版用户（包括 Google Colab 平台）无法导入任何模型。这是一个影响面较广的兼容性 bug，修复体现了项目对**广泛部署环境**的重视。有趣的是，该提交先添加测试再移除，反映了开发者的审慎态度。
- **CI 修正**：修复 `push_tests.yml` 中的步骤命名错误和移除 xformers 引用，同时将元数据操作的 Python 版本统一至 3.11，保障持续集成的可靠性。

## 3. 对项目的影响和潜在意义

- `motion_speed` 参数的引入使 diffusers 在 **LTX-2 生态系统**中的集成更加完善，用户无需手动计算帧率即可实现慢动作视频生成，大幅降低使用门槛。
- torchao 修复消除了大量用户（尤其 Colab 用户）的阻塞性导入错误，对项目**可访问性**有直接正面影响。
- 向后兼容性处理得当：`motion_speed` 默认 1.0、`conditioning_frame_rate` 默认 `None` 解析为 `frame_rate`，确保**现有输出完全不变**。
- LTX-2 作为视频生成模型的代表，该项目的持续完善表明 diffusers 正在积极布局**视频生成**赛道，与文本/图像生成并重。

## 4. 值得关注的技术点

- **参数命名的 API 设计迭代**：从描述性的 `conditioning_frame_rate`（"条件帧率"）到语义化的 `motion_speed`（"运动速度"），体现了良好的 API 设计哲学——选择对最终用户更直观的抽象。
- **RoPE 位置编码与条件化**：LTX-2 在时间轴上以秒为单位放置视频 token（`pixel_frame / fps`），通过改变 fps 条件实现慢动作，这是对 Transformer 位置编码的巧妙利用。
- **模块化架构扩展**：变更同时覆盖 classic 管线和模块化 block，表明 diffusers 的模块化设计在功能扩展时的灵活性。
- **torchao 条件导入模式**：使用 `try/except` 处理版本依赖的导入策略值得关注，但提交中移除了对应测试，可能留下回归风险。

## 5. 对项目发展的整体影响

结合 diffusers 作为 HuggingFace 生态中核心扩散模型库的定位，这批提交体现了三条发展主线：**第一**，在视频生成方向持续深化 LTX-2 的集成能力，通过 `motion_speed` 等参数丰富用户的控制手段；**第二**，注重生产环境的健壮性，修复关键兼容性问题确保不同平台和依赖版本下的可用性；**第三**，维护 CI 基础设施的健康运行。这些变更虽然单个规模不大，但共同保障了项目在快速迭代中保持功能先进性与工程稳定性之间的平衡，有助于巩固 diffusers 在扩散模型推理领域的领先地位。

## 详细提交记录

### [7e4383c](https://github.com/huggingface/diffusers/commit/7e4383c0a2aeb384f3d3e0003b013a40c9b1e843)

- **作者**: Christopher
- **时间**: 2026-10-21T21:23:46Z
- **提交信息**: [LTX-2] Add `motion_speed` to condition the positional time base apart from the playback frame rate (#14967)

* [LTX-2] Add `conditioning_frame_rate` to decouple the positional time base from the playback frame rate

LTX-2 places video tokens on a time axis in seconds (`pixel_frame / fps`
in the RoPE coordinates), derived from `frame_rate`. Adapters such as the
LTX-2.5 Slow-Motion-Control LoRA are conditioned on a different rate
(`fps / speed`) than the video plays at. Add an optional
`conditioning_frame_rate` to the LTX-2 classic pipelines and modular
blocks: it drives the video, keyframe and reference coordinates and the
transformer's `fps`, while the audio length, the duration head and the
returned video keep following `frame_rate`. `None` resolves to
`frame_rate`, leaving current outputs unchanged.

* [LTX-2] Replace `conditioning_frame_rate` with `motion_speed`

`frame_rate` keeps one meaning, the playback rate; `motion_speed` (default
1.0, must be positive) is the speed of the motion relative to real time, and
the positional time axis is conditioned on `frame_rate / motion_speed`.

* [LTX-2] Add an end-to-end `motion_speed` example to the LTX-2 doc

Image-to-video with the LTX-2.5 Slow-Motion-Control LoRA at motion_speed 1.0
and 0.2 (same seed and caption), plus a note that two-stage generation must
pass the same motion_speed to both stages.

### [0c7d56d](https://github.com/huggingface/diffusers/commit/0c7d56d6f4ea28c684d563cfae96fa375e0a6d4c)

- **作者**: Sayak Paul
- **时间**: 2026-10-21T13:55:00Z
- **提交信息**: [ci] fix misnamed test steps in push_tests.yml (#15094)

* [ci] fix misnamed test steps in push_tests.yml

* remove xformers.

### [a68262b](https://github.com/huggingface/diffusers/commit/a68262b0e95a3f424b5fa73e0a16defef619a8dc)

- **作者**: Sayak Paul
- **时间**: 2026-10-21T13:49:25Z
- **提交信息**: [ci] use python 3.11 when using metadata. (#15093)

use python 3.11 when using metadata.

### [3421fed](https://github.com/huggingface/diffusers/commit/3421fed4a1655508436a5ca0c5179e88b0ec0afd)

- **作者**: Muhammad Usman Mateen
- **时间**: 2026-10-21T12:26:24Z
- **提交信息**: Fix model imports when torchao is older than 0.15 (#15095)

* Add a test for importing models with torchao older than 0.15

* Only import FqnToConfig from torchao 0.15 on

torchao_quantizer.py imported FqnToConfig whenever torchao was installed,
but it only exists from torchao 0.15. With an older torchao, importing any
model failed, including on Google Colab.

* Remove the torchao import test

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
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


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13284
- **最后更新**: 2026-10-22T00:12:36Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

# DiffSynth-Studio 昨日提交分析

## 1. 主要更新类型
**性能优化与量化支持**：该提交为量化框架 Entropack 增加了 int8 卷积（convrot）配置支持，属于模型推理加速相关的优化类更新。

## 2. 关键变更点及其与项目整体方向的关系

- **变更核心**：在 DiffSynth-Studio 中集成 Entropack 的 int8 量化配置，针对卷积操作进行 8-bit 量化，降低模型推理时的显存占用与计算开销。
- **与项目方向的关系**：DiffSynth-Studio 是一个扩散模型合成工作室（面向图像/视频生成的扩散模型），其 README 强调高性能推理与模型可用性。量化是降低大模型部署门槛、提升端侧/消费级硬件可用性的关键手段。该提交将项目的优化方向从"模型质量与训练"扩展到"部署效率与推理优化"，符合开源生成式 AI 项目追求更低资源消耗、更广泛可运行环境的普遍趋势。

## 3. 对项目的影响和潜在意义

- **直接影响**：用户在使用 DiffSynth 进行推理时，可以通过 int8 量化显著减少显存需求，使得部分原本需要高端 GPU 的模型能在更普通的硬件上运行。
- **间接影响**：引入 Entropack 表明项目正在与更多量化生态对接，可能为后续支持更多量化后端（如 GPTQ、AWQ、SmoothQuant 等）奠定基础。
- **生态意义**：降低使用门槛有利于扩大用户群和社区贡献者数量，对一个在 Trendshift 上已有关注度的项目而言，这是提升竞争力的重要一步。

## 4. 值得关注的技术点

- **Entropack 框架**：这是一个相对小众但针对性强的量化框架，选择它而非主流方案（如 bitsandbytes）可能意味着项目对量化精度或特定硬件适配有更高要求，值得跟踪其后续集成深度。
- **int8 卷积量化**：在扩散模型中卷积占比较高（尤其 U-Net 结构），对卷积做 int8 量化能在不显著影响生成质量的前提下获得可观的速度提升。
- **单提交、单文件级变更**：改动范围较小（仅第 1/1 批提交），说明是一次谨慎的增量式接入，而非大规模重构，风险较低。

## 5. 对项目发展的影响

结合 README 中"DiffSynth-Studio"的定位——一个集训练、微调、推理于一体的扩散模型工作室——可以看出项目已进入**功能完善后的优化阶段**。在早期提交通常聚焦于新增模型支持、训练管线搭建之后，当前提交转向**推理效率优化**，这符合开源 AI 项目"先能用、再好用、最后高效用"的典型演进路径。持续的量化与部署优化将使 DiffSynth-Studio 不仅是研究工具，更接近可落地的生产级推理方案，有助于在与同类项目（如 ComfyUI、Diffusers 生态）的竞争中建立差异化优势。

## 详细提交记录

### [f39d731](https://github.com/modelscope/DiffSynth-Studio/commit/f39d731a3e318d25b725eb3389cfddb184619842)

- **作者**: Hong Zhang
- **时间**: 2026-10-21T09:20:51Z
- **提交信息**: support int8 convrot config for entropack (#1777)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37577
- **最后更新**: 2026-10-22T00:37:13Z

## 提交统计

- **昨日提交总数**: 68
- **提交者数量**: 35
- **主要提交者**: pllimax, Kangrui Du, Shiyang Lyu

## AI分析总结

# SGLang 昨日（68 个提交）总结

## 一、主要更新类型
- **性能优化**（约15条）：集中在 DeepSeek V4/V4.1 推理链路、投机解码、CUDA Graph 等核心加速路径。
- **Bug 修复**（约29条）：覆盖量化、路由调度、分布式同步、CUDA 流时序、依赖安全及跨硬件（NPU/AMD/Intel/Apple）模块。
- **功能新增**（约14条）：GLM-5.3 Flash、ComfyUI Flux ControlNet 与在线 INT8 量化、rust-server 改进、NIXL UCX 选择、扩散调度插件化等。
- **测试/CI/文档/重构**（约14条）：新增 NPU 部署 Cookbook，精简 CPU 测试套件，并重构 radix-tree 与扩散 Rollout 控制器。

## 二、关键变更与项目方向
- **DeepSeek V4/V4.1 深度适配**：近 15 条提交涉及 MXFP8 量化融合、request-window 优化、prefill 图优化、SWA 存储布局修复等，表明团队正将 SGLang 打造为 DeepSeek 新一代模型的首选高性能推理引擎。
- **投机解码并行化**：EAGLE KV index 按 token block 并行，覆盖 flashinfer/aiter 多后端，降低 host 开销，契合"快速推理"定位。
- **多硬件生态扩张**：NPU 大量 Cookbook 与修复、AMD ROCm 10.1 与 gfx1250 构建方案、Intel XPU KV 传输、Apple MLX 修复持续跟进，体现多后端战略。
- **生产稳定性**：PD 分离式角色切换、KV 同步、Mooncake 失败探测、sgl-router 与 rust-server 健康探针、uvicorn tokenizer 负载均衡（SO_REUSEPORT）均在完善大规模部署能力。

## 三、项目影响与潜在意义
DeepSeek V4.1 优化集中落地将显著提升吞吐与延迟表现；CUDA-graph 流对齐修复、rustls-webpki 安全升级、FPM 时序修正提升了生产可靠性与指标可信度；多硬件文档降低了上手门槛。整体推动项目从高性能研究框架向**可落地的多硬件生产级推理平台**演进。

## 四、值得关注的技术点
- **量化进入逐 kernel 手工优化阶段**：deep_gemm 的 block-FP8、BF16 NaN 保留、per-row q_norm 融合、ComfyUI 在线 INT8。
- **消除 host-device 同步**：Mamba 混合批调度与 request-window history 缓存均针对同步开销。
- **CUDA 多流协作**：glm-5.2 在 join 前记录侧流工作，涉及多流同步与图捕获的微妙交互。
- **架构演进**：扩散调度从 mixin 继承转为 scheduler-step 插件（组合优于继承），radix-tree 组件化重构支持自定义 tree core 复用。
- **模型覆盖拓宽**：GLM-5.2/5.3、Qwen-Image-2.1 等国产大模型与多模态模型持续适配。

## 五、整体影响
这些提交延续 SGLang "Fast inference for LLMs and multimodal models" 的核心目标，呈现三线并进：**深度优化单模型**（DeepSeek V4 系列）、**广度覆盖多硬件**（NPU/AMD/Intel/Apple/ComfyUI）、**强化工程稳定性**（安全、可观测性、调度插件化），在巩固国产大模型推理领先性能的同时，为长期生态建设与生产级落地奠定了扎实基础。

## 详细提交记录

### [ed89693](https://github.com/sgl-project/sglang/commit/ed89693c4ac3f187792494723a240345eac440cf)

- **作者**: Khoa Pham
- **时间**: 2026-10-21T23:56:45Z
- **提交信息**: [Perf] dsv41: Fuse the q_norm MXFP8 quantize for wq_b at every row count (#45633)

### [da7b97a](https://github.com/sgl-project/sglang/commit/da7b97a737aad1dfcf7cf8721494e58174485b14)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T23:29:28Z
- **提交信息**: [Perf] dsv4: Publish prefill read-done under the request window and on V4.1 (#45582)

### [3438ed6](https://github.com/sgl-project/sglang/commit/3438ed660dad26a83ed93f6c066f2a50d76507b0)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T23:02:47Z
- **提交信息**: [Test] cpu: prune mirror and tautology cases from the per-commit CPU suite (#45672)

### [ed1f56f](https://github.com/sgl-project/sglang/commit/ed1f56fead70bdcd454aa74a687f41489dcaf599)

- **作者**: Leo
- **时间**: 2026-10-21T22:54:49Z
- **提交信息**: [Fix] [Apple] mlx: Give the stub model a shared-expert layout (#45419)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: R0CKSTAR <yeahdongcn@gmail.com>

### [f4035ca](https://github.com/sgl-project/sglang/commit/f4035cab0be4dd54099eeb044a701ad9aeecb5b4)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-21T22:51:28Z
- **提交信息**: [Feat] cp: Enable GLM-5.3 Flash interleave BCG with batched prefill and DFlash2 (#43182)

### [42db2db](https://github.com/sgl-project/sglang/commit/42db2db4a8605fa5e787bd30369a0aac8d673e4d)

- **作者**: metamergebot
- **时间**: 2026-10-21T22:50:13Z
- **提交信息**: [Fix] rust-server: Check only a client-sent max_new_tokens against the context window (#45460)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [991b846](https://github.com/sgl-project/sglang/commit/991b8462278503fbdfcdd30213bc0bd5c7662eb9)

- **作者**: Brandon Zhang
- **时间**: 2026-10-21T22:26:35Z
- **提交信息**: [Perf] speculative: Parallelize EAGLE spec-decode KV index building over token blocks (flashinfer draft decode; verify/draft-extend for flashinfer, flashinfer_mla, aiter) (#42803)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: YAMY1234 <74099316+YAMY1234@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [4b9936b](https://github.com/sgl-project/sglang/commit/4b9936b5e35f2f6ff03afe4f50f8fd2471e3f276)

- **作者**: maocheng23
- **时间**: 2026-10-21T22:21:31Z
- **提交信息**: [Fix] deepseek_v4: Fix mHC prewarm when chunked prefill is disabled (#43448)

### [99cf403](https://github.com/sgl-project/sglang/commit/99cf403c9e84272b80cf36e7cca953d83be4b1d5)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T22:18:34Z
- **提交信息**: [Fix] dsv4: Write idle SWA stores to an idle request-window layout (#45586)

### [aa5880e](https://github.com/sgl-project/sglang/commit/aa5880e2b8f7807543a6d4745f96bd7a50821b2c)

- **作者**: em-dreyer
- **时间**: 2026-10-21T21:53:58Z
- **提交信息**: [Fix] bailing: Renormalize top-k routing weights by default for Ling-2.5/2.6 (#45662)

### [51baa1f](https://github.com/sgl-project/sglang/commit/51baa1f6e95a8be516b37c38806a7f96f45a3b97)

- **作者**: Michael
- **时间**: 2026-10-21T21:49:53Z
- **提交信息**: [Test] [AMD] debug-utils: Opt TestCrashDump into expect_server_exit (#45408)

### [f3f0f7b](https://github.com/sgl-project/sglang/commit/f3f0f7b68c9a8a062b63855bc86bb95de181f134)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T21:44:21Z
- **提交信息**: [Perf] dsv4: Let the decoder tail leave the prefill graph under DP attention with MegaMoE (#45581)

### [f5eca05](https://github.com/sgl-project/sglang/commit/f5eca05b0500055d1c85394a90788cdc69a6eab8)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T21:42:50Z
- **提交信息**: [Fix] [SM100] quantization: Honor `deep_gemm` for 32x32 block-FP8 linears (#45585)

### [29e7804](https://github.com/sgl-project/sglang/commit/29e78045fba1b4616e21e3d828b2c58df5e27879)

- **作者**: ssJ
- **时间**: 2026-10-21T21:37:55Z
- **提交信息**: [Fix] dsv4: Skip DP-attention pad rows in the engram hasher and low-ratio sources (#40424)

Co-authored-by: jiashuai <jiashuai@baidu.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [68623ca](https://github.com/sgl-project/sglang/commit/68623cae9256ad8ee00269c8c1d52e4c2915daa5)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T21:33:48Z
- **提交信息**: [Fix] test: Gather Mamba track indices from `track_position` in the mixed-batch track test (#45670)

### [f7d4f06](https://github.com/sgl-project/sglang/commit/f7d4f06242b76615a2cc95e87426b7123a90c7f6)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T21:01:19Z
- **提交信息**: [Perf] dsv4: Compute request-window history rows once per batch (#45579)

### [bc41221](https://github.com/sgl-project/sglang/commit/bc412213c17cecfa826716e23d5ae00748bbe528)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T21:00:35Z
- **提交信息**: [Perf] dsv4: Gather V4.1 index-K slots once per forward and cache the prefill index plan (#45577)

### [620718c](https://github.com/sgl-project/sglang/commit/620718c8ea67d8f1ef827f6be78a77b3a7830b41)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T20:58:44Z
- **提交信息**: [Fix] moe: Keep the DeepSeek V4.1 vision router off the packed-ids path under routing simulation (#45575)

### [9794583](https://github.com/sgl-project/sglang/commit/97945831f9ec29755099284243ab7d91336d314f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T20:54:32Z
- **提交信息**: [Perf] dsv4: Restore sparse prefill for request-window rows (#45573)

### [2c7a9e3](https://github.com/sgl-project/sglang/commit/2c7a9e3b50828720951a5f7e71f42563d2df1b47)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T20:53:37Z
- **提交信息**: [Fix] radix-cache: Order linker offloads behind the forward that writes the pages (#45559)

Co-authored-by: lixiufei-leo <294029388+lixiufei-leo@users.noreply.github.com>

### [028de2c](https://github.com/sgl-project/sglang/commit/028de2c5d485385bee3b68f6463a0a887f42e4d2)

- **作者**: Khoa Pham
- **时间**: 2026-10-21T20:35:56Z
- **提交信息**: [Perf] dsv41: Use tuned MXFP8 tactics at decode sizes (#45630)

### [a2e4ffb](https://github.com/sgl-project/sglang/commit/a2e4ffbcea182496700fd9329d0363ddf9c78985)

- **作者**: Yoni Gozlan
- **时间**: 2026-10-21T20:04:15Z
- **提交信息**: [Fix] parser: Accept whole-number floats for integer tool arguments (#43941)

Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [7e0e259](https://github.com/sgl-project/sglang/commit/7e0e259435a4cc73df71e096607d5fd219458c7b)

- **作者**: Michael
- **时间**: 2026-10-21T19:47:42Z
- **提交信息**: [CI] [AMD] disaggregation: Register Mooncake KV buffers without HIP dmabuf (#45519)

### [a3d00ef](https://github.com/sgl-project/sglang/commit/a3d00eff58b6c22ea7539f882cc10c537634200b)

- **作者**: metamergebot
- **时间**: 2026-10-21T18:58:25Z
- **提交信息**: [Perf] srt: Record on the host whether an extend batch completes a prompt (#45487)

Co-authored-by: Lu Fang <116399278+luccafong@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [7e5256d](https://github.com/sgl-project/sglang/commit/7e5256d1ba3aaa628bb8b756fafb904a76a1123a)

- **作者**: metamergebot
- **时间**: 2026-10-21T18:57:26Z
- **提交信息**: [Feat] srt: Balance uvicorn tokenizer workers with per-worker SO_REUSEPORT listeners (#45482)

Co-authored-by: luccafong <116399278+luccafong@users.noreply.github.com>
Co-authored-by: joshuadeng <joshuadeng@users.noreply.github.com>

### [f06d1bb](https://github.com/sgl-project/sglang/commit/f06d1bb1f45df617aa455c103ce5ede2bc6c6a47)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-21T18:57:23Z
- **提交信息**: [Perf] cuda-graph: Capture FlashInfer KDA prefill  (#45473)

### [740d5f9](https://github.com/sgl-project/sglang/commit/740d5f9f9e33aeebc6b5bcb1ba73f25bf6db062b)

- **作者**: metamergebot
- **时间**: 2026-10-21T18:56:50Z
- **提交信息**: [Perf] scheduler: Plan hybrid Mamba extend batches without host-device syncs (#45472)

Co-authored-by: Lu Fang <116399278+luccafong@users.noreply.github.com>
Co-authored-by: Shiyan Deng <20773414+842974287@users.noreply.github.com>

### [5e79333](https://github.com/sgl-project/sglang/commit/5e79333c95c162abf079548fe40a6a2bca6c5409)

- **作者**: metamergebot
- **时间**: 2026-10-21T17:53:26Z
- **提交信息**: [Refactor] radix-tree: Reuse the insert walk, component hooks and bindings for custom tree cores (#45439)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [b57b5e2](https://github.com/sgl-project/sglang/commit/b57b5e22867f110ff577a9da18a9ff7e6619100c)

- **作者**: paulzhang-tm
- **时间**: 2026-10-21T17:37:28Z
- **提交信息**: [Fix] disaggregation: Synchronize deferred decode KV release across TP ranks (#45453)

### [ed268dd](https://github.com/sgl-project/sglang/commit/ed268dd32097ed44a83b260250defb82256602e2)

- **作者**: Khoa Pham
- **时间**: 2026-10-21T17:00:15Z
- **提交信息**: [Fix] moe: Apply SGLANG_SIMULATE_* routing on DeepSeek-V4.1 vision-biased gates (#45628)

### [6e98c84](https://github.com/sgl-project/sglang/commit/6e98c84c601a6a18405403c12ce047f167a054b4)

- **作者**: vorapolsiloai
- **时间**: 2026-10-21T16:37:47Z
- **提交信息**: [Perf] [AMD] quark: Add opt-in AITER ASM FP4 GEMM for Quark dense linear (#39598)

### [4b1a44b](https://github.com/sgl-project/sglang/commit/4b1a44bc77c8f473b543468016cecbb6c3fbb794)

- **作者**: Michael
- **时间**: 2026-10-21T16:11:08Z
- **提交信息**: [Test] [AMD] diffusion: Avoid Python 3.11-only enterContext in test_usp_ring_replicated (#45409)

### [75878f2](https://github.com/sgl-project/sglang/commit/75878f27c88c2ffd296425d94226d0dc9bd42518)

- **作者**: zijiexia
- **时间**: 2026-10-21T15:58:16Z
- **提交信息**: [Doc] cookbook: Add Recursive Flint cookbook (#45625)

### [cdbd478](https://github.com/sgl-project/sglang/commit/cdbd4784226925515abc03cd3e77ac5129644dae)

- **作者**: Shiyang Lyu
- **时间**: 2026-10-21T14:59:37Z
- **提交信息**: [Doc] [NPU] cookbook: add tested A2 deployment and A3 reference for MiniMax-M2.5 (#40120)

### [af49ada](https://github.com/sgl-project/sglang/commit/af49ada16d9b4e7535fd6ff542247f50b8c92c9f)

- **作者**: Huang Long
- **时间**: 2026-10-21T14:58:29Z
- **提交信息**: [Fix] pd: Allow runtime role switching with DP and DP attention (#44215)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [7163e97](https://github.com/sgl-project/sglang/commit/7163e974622656a73013c67c2c8187ea55413212)

- **作者**: Peng Xingchen
- **时间**: 2026-10-21T14:44:08Z
- **提交信息**: [Doc] [NPU] GLM: Add Ascend cookbook deployment recipes (#45597)

### [8e3e298](https://github.com/sgl-project/sglang/commit/8e3e2980db83a1b020a6d273a2b653891af81bfc)

- **作者**: kpjeeja
- **时间**: 2026-10-21T14:09:04Z
- **提交信息**: [Feat] [Intel] disaggregation: Support XPU for staging-buffer KV transfer (#40861)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [7e5d378](https://github.com/sgl-project/sglang/commit/7e5d3780ef06bcd56756e31df27a3b4bb125568b)

- **作者**: pllimax
- **时间**: 2026-10-21T13:48:12Z
- **提交信息**: [Fix] [NPU] tests: Run the HiCache Mamba case with bfloat16 SSM kernels (#45593)

### [dd9ea06](https://github.com/sgl-project/sglang/commit/dd9ea06c00d561333afbffc2cb58b9d59cfc2202)

- **作者**: Shawn Yang
- **时间**: 2026-10-21T13:40:08Z
- **提交信息**: [Fix] rust: Format health probe handle setup (#45606)

### [e109bc1](https://github.com/sgl-project/sglang/commit/e109bc1832eebfe776a7fe87ad69c9b6550ae009)

- **作者**: unclezhou
- **时间**: 2026-10-21T13:16:49Z
- **提交信息**: [Doc] [NPU] deepseek-v4: Add A3/950 single-node cookbook recipes (#45602)

### [2815eed](https://github.com/sgl-project/sglang/commit/2815eed49c94dbc3266fb5dc4b01c61fc8eb73ca)

- **作者**: amote-i
- **时间**: 2026-10-21T11:44:30Z
- **提交信息**: [Fix] [NPU] pre_warm_nccl: init npu backend before the parallel runtime touches a device (#43039)

### [fda84f8](https://github.com/sgl-project/sglang/commit/fda84f80b7f9ab3516cd612fc68b6219f17d493f)

- **作者**: amote-i
- **时间**: 2026-10-21T11:38:17Z
- **提交信息**: [Doc] [NPU] docs: reference released Qwen3.8-Max W4A8 checkpoint in tutorial (#45574)

### [a175e39](https://github.com/sgl-project/sglang/commit/a175e39b8464fd357b745e06753164a709430d67)

- **作者**: Shangming Cai
- **时间**: 2026-10-21T11:32:22Z
- **提交信息**: [CI] cuda: Rebuild workspace crates when the shared Cargo target dir came from another rust/ tree (#45557)

### [62b4127](https://github.com/sgl-project/sglang/commit/62b41276688ee363fd1b9b5d970b34799812bc1b)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-21T11:29:43Z
- **提交信息**: [Feat] comfyui: Apply ControlNet residuals in Flux integrated mode (#43698)

Co-authored-by: niehen6174 <1639206518@qq.com>

### [43a3f95](https://github.com/sgl-project/sglang/commit/43a3f956cb0c9fe9b7b7a042af8d8743176b9dba)

- **作者**: Shangming Cai
- **时间**: 2026-10-21T11:04:26Z
- **提交信息**: [Fix] sgl-router: Wait for the detached PD prefill in routing tests (#45502)

### [4372829](https://github.com/sgl-project/sglang/commit/43728298fe288648b944b7a897ec71c08109879c)

- **作者**: pllimax
- **时间**: 2026-10-21T10:43:30Z
- **提交信息**: [Fix] [NPU] qwen3_6: Set accuracy cases to greedy decoding and tune retries (#40889)

### [ca72dad](https://github.com/sgl-project/sglang/commit/ca72dad953171ea4f580d89f70f999fc89501067)

- **作者**: metamergebot
- **时间**: 2026-10-21T10:41:36Z
- **提交信息**: [Fix] rust-server: Answer health probes a busy scheduler skipped on the response ring (#45475)

Co-authored-by: Lu Fang <116399278+luccafong@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [5bf10d4](https://github.com/sgl-project/sglang/commit/5bf10d4c79a55a12f4503a1e03407e5cab9215f1)

- **作者**: Jimmy Shong
- **时间**: 2026-10-21T10:38:35Z
- **提交信息**: [Fix] nemotron: Correct weight-export failures and GEMV dispatch (#45082)

### [2e7c9d8](https://github.com/sgl-project/sglang/commit/2e7c9d851c868678ddfcd93b4e8000cd23e1f779)

- **作者**: Jzz1943
- **时间**: 2026-10-21T09:54:11Z
- **提交信息**: [Feat] NIXL: Support per-GPU UCX device selection (#43482)

### [9c10e0d](https://github.com/sgl-project/sglang/commit/9c10e0dd61f0cea9d8ecdcfd3fb352d5ef0723cc)

- **作者**: bz f
- **时间**: 2026-10-21T09:37:24Z
- **提交信息**: [Doc] [NPU] cookbook: add NPU (A3 series) deployment scenarios for Qwen3.6 (#38678)

### [7554be5](https://github.com/sgl-project/sglang/commit/7554be5a69bf678da0421fba5aca695a0bb13041)

- **作者**: Shangming Cai
- **时间**: 2026-10-21T09:28:21Z
- **提交信息**: [CI] codeowners: Add owners for the top-level sgl-router (#45564)

### [131c42b](https://github.com/sgl-project/sglang/commit/131c42ba339b5e83d6d0772060a97f426ca2e33a)

- **作者**: kangwangamd
- **时间**: 2026-10-21T09:25:02Z
- **提交信息**: [Perf] [AMD] aiter: Update ROCm AITER pin to 285579b62 (gfx942/gfx950 only) (#45498)

### [be65391](https://github.com/sgl-project/sglang/commit/be65391abd01f711cdc443a3fe8f508b0c960357)

- **作者**: Shangming Cai
- **时间**: 2026-10-21T09:16:19Z
- **提交信息**: [Feat] mooncake: Enable the failed-session probe by default with backoff and idle pruning (#45338)

### [1278087](https://github.com/sgl-project/sglang/commit/127808733667e7b5b9be38f9dbb72acc6464bab4)

- **作者**: Thomas Wang
- **时间**: 2026-10-21T09:02:03Z
- **提交信息**: [Fix] [AMD] mono-kernel: Update sgl-amd-mono version (#45546)

### [2c9d919](https://github.com/sgl-project/sglang/commit/2c9d9190713285552d7ea2bb264664c90639c824)

- **作者**: metamergebot
- **时间**: 2026-10-21T08:59:03Z
- **提交信息**: [Fix] srt: Pin the source address of TCP ZMQ connects for the peer allowlist (#45437)

Co-authored-by: Lu Fang <116399278+luccafong@users.noreply.github.com>
Co-authored-by: fei-xx <fei-xx@users.noreply.github.com>

### [21f775c](https://github.com/sgl-project/sglang/commit/21f775cd9786566576066c7b1155183ee77722c2)

- **作者**: metamergebot
- **时间**: 2026-10-21T08:58:34Z
- **提交信息**: [Feat] rust-server: Let the launcher set the default max_new_tokens for /generate (#45431)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [7a632cf](https://github.com/sgl-project/sglang/commit/7a632cf998d437b0541700dd0b4f808c1f275ed5)

- **作者**: Aurick Qiao
- **时间**: 2026-10-21T08:52:28Z
- **提交信息**: [Fix] quantization: Preserve BF16 NaNs in per-token FP8 quantization (#42689)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [8bd6aa9](https://github.com/sgl-project/sglang/commit/8bd6aa9a6ce5395b91be7c0da9dcc9d64e10664f)

- **作者**: Yoni Gozlan
- **时间**: 2026-10-21T08:46:26Z
- **提交信息**: [Feat] parser: Enrich chat_parsing streaming events (#40478)

Co-authored-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [dbe0a9a](https://github.com/sgl-project/sglang/commit/dbe0a9a7c9c82641c0d3636c0030f2b6920d00f3)

- **作者**: Alex
- **时间**: 2026-10-21T08:40:51Z
- **提交信息**: [Fix] nemotron_vl: Preserve tokenized prompts during media expansion (#44184)

Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [6efdd33](https://github.com/sgl-project/sglang/commit/6efdd33d071eca7d51983f19ae01d10b11b9f1b2)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-21T08:22:16Z
- **提交信息**: [Refactor] spec: Move platform dispatch and Triton kernels into `kernels/ops` (#45504)

### [6cac4dc](https://github.com/sgl-project/sglang/commit/6cac4dc3fe9a4bf15009f300132c3c7a1853c210)

- **作者**: Kangrui Du
- **时间**: 2026-10-21T08:04:33Z
- **提交信息**: [Refactor] diffusion: Rollout controller as a scheduler-step plugin instead of mixins (#44603)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>
Co-authored-by: JingwenGu0829 <75733630+JingwenGu0829@users.noreply.github.com>

### [fee32a5](https://github.com/sgl-project/sglang/commit/fee32a5c1fbb47a7c78a2b75decff64037d2ef9b)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-21T08:01:18Z
- **提交信息**: [Feat] ComfyUI: Add online INT8 quantization for BF16 Qwen-Image-2.1 single files (#44865)

Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>

### [a361f0c](https://github.com/sgl-project/sglang/commit/a361f0c410b5f6c56b840fbf01e3ba21a58748e1)

- **作者**: Jzz1943
- **时间**: 2026-10-21T07:58:34Z
- **提交信息**: [Fix] kda: Align graph tracking branch dtype with the recurrent state pool (#44886)

### [f7b8c6f](https://github.com/sgl-project/sglang/commit/f7b8c6fe404ca4f29c3188cb50692f7735d45a99)

- **作者**: Shu Wang
- **时间**: 2026-10-21T07:36:54Z
- **提交信息**: [Fix] glm-5.2: Record side-stream work right before its join to keep CUDA-graph replay on one stream (#45349)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [8acfabb](https://github.com/sgl-project/sglang/commit/8acfabbd676862234990fd8c3c0ad92c083641ff)

- **作者**: Hongkuan Zhou
- **时间**: 2026-10-21T07:31:18Z
- **提交信息**: [Fix] observability: Correct speculative FPM timing and decode lengths (#38711)

Signed-off-by: hongkuanz <hongkuanz@nvidia.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [cd61db4](https://github.com/sgl-project/sglang/commit/cd61db49c713b8e02cd2a5f5436f37789b4bd16c)

- **作者**: Shangming Cai
- **时间**: 2026-10-21T07:24:11Z
- **提交信息**: [Fix] sgl-router: Bump rustls-webpki and webpki-roots for emSign advisories (#45526)

### [132836b](https://github.com/sgl-project/sglang/commit/132836b369e2da8273b9273d21cf4deda12b08dc)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-21T07:14:24Z
- **提交信息**: [Fix] [AMD] docker: Build Triton from source for ROCm 10.1 gfx1250 (#45329)

### [4449d7e](https://github.com/sgl-project/sglang/commit/4449d7ecb0a3b1cee77ec8c5bbf71ebcf833e0ef)

- **作者**: Peng Xingchen
- **时间**: 2026-10-21T07:02:58Z
- **提交信息**: [Doc] [NPU] GLM: Add GLM-5.3 and GLM-5.3-Flash deployment tutorials (#43372)

Co-authored-by: pengxingchen0810 <pengxingchen0810@noreply.gitcode.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1293
- **最后更新**: 2026-10-21T13:35:43Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 提交分析：vipshop/cache-dit（commit 082fa15）

### 1. 主要更新类型
- **功能新增为主**，同时包含**性能优化**与**Bug修复**：新增 MiniMax-H3 模型支持，配套缓存、并行、量化能力，以及通用层间 offload 修复。

### 2. 关键变更点及与项目方向的关系
- **新增 MiniMax-H3 模块化推理管线**：该模型将文本、关键帧、音频、视频打包成单一序列，经 50 个 block 去噪，无 cross-attention、无 CFG。模型体量极大（checkpoint 62 GiB + 条件器 63 GiB），单张 72 GiB 卡放不下——这正好呼应 cache-dit README 中"Cache / Parallelism / Quantization / CPU Offload"四大核心卖点。
- **缓存**：minimax_h3_adapter 只缓存 transformer_blocks（Pattern_3），token refiner 每步仅运行一次，复用项目既有的稀疏注意力缓存框架。
- **AdaLN host residency（新增 CLI 开关）**：将 AdaLN 表从常驻显存改为 pinned host memory 流式加载，配合文本编码器卸载。88.9 s、49.4 GiB，且与未优化路径**位精确一致**（相同 mp4 输出），体现项目对"无损加速"的追求。
- **并行（CP/TP）**：CP 在首层切分 packed buffer，携带 rope/adaln 索引并在输出头 gather；TP 切分 q/k/v、to_out、融合 SwiGLU 及 AdaLN/输出表，输出布局用 Replicate 保证 `chunk(6)` 兼容。56 heads 支持 tp2/tp4。
- **量化**：`--quantize-exclude-layers` 改为扩展默认排除表而非替换，支持混合精度 checkpoint（fp32 proj_in/proj_out 等保留、其余量化）。
- **Offload 通用修复**：层间 offload 现能处理挂在非叶子模块上的孤儿状态（如 ViT 风格结构），是普适性健壮性改进。

### 3. 对项目的影响和潜在意义
- 将 cache-dit 的适配范围扩展到**新一代超大 MoE/多模态 DiT 架构**，验证了项目抽象（缓存模式、并行切分、量化排除、offload）对新模型的可复用性。
- AdaLN host residency 是一类新的**显存换带宽**手段，为未来支持 AdaLN 规模更大的模型提供了模板。
- 混合精度量化与 offload 修复降低了用户适配真实（非干净）checkpoint 的门槛。

### 4. 值得关注的技术点
- **位精确性保证**：host residency 路径与基线输出 bit-exact，说明流式传输未引入数值偏差，是工程严谨性的体现。
- **TP 与 view 兼容性**：用 Replicate 输出布局维持 `view(-1, 6*hidden).chunk(6)` 的有效性，处理了 AdaLN 表切分后形状约束的巧妙问题。
- **CP 与 TP 的交互校验**：对 Ulysses 并行度与 TP 后 head 数做一致性检查，防止静默错误。
- **--parallel/--quantize 下 host residency 自动退化**为"仅卸载文本编码器"，避免与已有切分/量化机制冲突。

### 5. 对项目发展的整体影响
cache-dit 定位为 PyTorch 原生的 DiT 推理引擎，本次提交表明项目正沿着**"主流大模型快速适配 + 多技术协同（cache×并行×量化×offload）"**的路线演进。对 MiniMax-H3 这种单卡装不下的模型实现完整且无损的推理，强化了项目"让超大 DiT 在消费级/单卡服务器上可推理"的核心价值，同时也沉淀了一批可复用的机制（AdaLN host residency、量化排除表扩展、非叶子模块 offload），为后续适配更多异构 DiT 架构降低了边际成本。

## 详细提交记录

### [082fa15](https://github.com/vipshop/cache-dit/commit/082fa15084eb1f54362782758f864fd716a1dd15)

- **作者**: DefTruth
- **时间**: 2026-10-21T13:21:28Z
- **提交信息**: feat: support MiniMax-H3 (cache, CP, TP, AdaLN host residency) (#1129)

* feat: support MiniMax-H3 modular pipeline (cache, CP, TP, AdaLN host residency)

MiniMax-H3 denoises one packed sequence (text + keyframe + audio + video rows) through a
single stack of 50 blocks, with per-row AdaLN modulation, no cross-attention, no mask and no
CFG. The checkpoint is 62 GiB (24 GiB of it AdaLN tables) plus a 63 GiB Qwen3-VL conditioner,
so neither fits a 72 GiB card on its own.

Cache
  minimax_h3_adapter caches `transformer_blocks` only (the token refiner runs once per step over
  the text stream), Pattern_3, has_separate_cfg=False.

AdaLN host residency (--adaln-host-residency)
  Keeps the transformer resident minus its AdaLN tables and streams those from a pinned host
  mirror, plus the text encoder. 256x448/124f/50 steps: 88.9 s and 49.4 GiB, bit-exact against
  the unoptimized run (identical mp4). Degenerates to "stream the text encoder only" under
  --parallel tp or --quantize, where the tables are already divided or small enough to stay.

Parallelism
  CP: splits the packed buffer at the first block (the root forward scatters with global row
  indices), carries rope output / adaln_indices / timestep_indices, gathers both output heads,
  and validates the post-TP head count against the Ulysses degree.
  TP: shards q/k/v, to_out, the fused SwiGLU projection (rearranged up-first, as diffusers'
  SwiGLU puts up in the first half) and the AdaLN + output tables with a Replicate output layout
  so `view(-1, 6*hidden).chunk(6)` stays valid. 56 heads divide for tp2/tp4.

Quantization
  `--quantize-exclude-layers` now extends the default table instead of replacing it, an explicit
  `None` falls back to that table, and the per-row fp8 bf16 check honours exclusions so
  mixed-precision checkpoints (float32 proj_in/proj_out/time_embedder) quantize the rest.

Offload fixes (generic)
  Layerwise offload now moves orphan state that hangs directly on a non-leaf module (a ViT-style
  VAE decoder's register tokens) while leaving unselected leaves alone, and advertises the
  execution device through a marker that no longer disables the forward-pattern check.

Attention fixes (generic)
  ffpa's NHD fast path falls back to the HND permute when the kernel declines a shape (short
  packed sequences) instead of raising, and non-fp16/bf16 inputs (a float32 VAE decoder reached
  by a pipeline-wide backend setting) fall back to SDPA, refusing context parallelism there.

CLI
  `minimax_h3` example with workflow=t2va pruning, ExampleType.T2VA, audio+video muxing at the
  native 24 fps, and the conditioner's tied LM head dropped at load.

Tests: cache/CP/TP invariants, the offload state bookkeeping, and the quantization exclusion
table (66 CPU/GPU tests).

* docs: list MiniMax-H3 (T2VA) in the supported DiT models table

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 94867
- **最后更新**: 2026-10-22T00:47:39Z

## 提交统计

- **昨日提交总数**: 49
- **提交者数量**: 35
- **主要提交者**: bzsuni, Alex Brooks, roigarnettNvidia

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型分布

- **性能优化**：约 12 项，涉及 DeepSeek-V4.1-Flash、mHC TileLang、Cohere2MoE、MiniMax-M3 等模型的内核与调度优化
- **Bug 修复**：约 15 项，覆盖图形别名、图片归一化、KV Offload、MoE 路由、量化参数替换等
- **Rust 前端补齐**：约 9 项，是一个集中攻坚方向
- **CI/测试**：约 8 项，主要面向 ROCm 和 XPU 平台
- **文档与流程**：约 4 项

## 二、关键变更点与项目方向的关系

1. **硬件多元化持续深化**：NVIDIA（GB300/B200）、AMD ROCm（MI355X、WideEP EP16/DP16）、Intel XPU 均有专项优化，体现了 vLLM "为所有人提供廉价快速的 LLM 服务" 的核心目标——通过多硬件适配降低部署门槛。

2. **Rust 前端快速成熟**：Bugen Zhao 主导的系列提交集中对齐 Rust 前端与 Python 前端的行为一致性（`--tokenizer`、`response_format`、`return_token_ids`、环境变量支持、超长对话 500 修复等），并更新了 `rust/AGENTS.md` 设计规范，说明 Rust 前端正从实验性组件走向生产可用。

3. **前沿模型适配**：DeepSeek-V4.1-Flash（GB300 特化解码、target-token scoring 修复）、Cohere2MoE（双流注意力+单 all-reduce）、MiniMax-M3（稀疏 lightning indexer、MXFP4 MonoKernel decode）等，保持对 SOTA 模型的快速跟进。

4. **AI 代理协作工作流成熟化**：近 40 个提交出现 Claude、Cursor、vllm-agent 等 AI 协作者签名，且提交 #62601 明确提高了 agent 编写测试的质量门槛，#62599 要求用户可见变更必须附带文档，显示项目正在系统化地管理 AI 生成代码的质量。

## 三、对项目的影响

- **稳定性提升**：进程 fork 前释放 libgomp worker、图形别名 clone 消除保护、分组分类保留等修复降低了复杂推理场景下的隐蔽故障风险。
- **多模态与 EPD 管线完善**：音频视频元数据请求、chunked embeddings 多模态拒绝、derender 输出模式，扩展了服务场景覆盖。
- **LoRA 扩展**：新增 BERT token classification head 和 Step5 支持，增强微调场景灵活性。
- **可观测性**：新增引擎/Worker 监控 Watchdog、Rust 侧自定义直方图桶，服务运维能力增强。

## 四、值得关注的技术点

- **mHC TileLang 内核**：跳过非有限 padding 行的 Sinkhorn 迭代 + ≤4 token 时单 pass 融合前后处理，是稀疏注意力内核工程化的典型案例。
- **Cohere2MoE 双流架构**：将 attention/MoE 拆为双流并将每层 all-reduce 从两次降为一次，配合 add+RMSNorm 融合，是模型级性能优化的范式。
- **NIXL KV Connector**：共享 GPU 上先启动 prefiller 再启动 accuracy decoder，体现了 disaggregated 架构下调度顺序的细微影响。
- **replace_parameter 量化修复**：`process_weights_after_loading` 中重建的参数需正确替换注册，否则会导致量化模型权重不生效，是一类隐蔽且影响面广的问题。

## 五、对项目发展的整体意义

结合 README 的定位——"Easy, fast, and cheap LLM serving for everyone"——这批提交从三个维度推进了项目：**速度**（多硬件内核优化）、**广度**（前沿模型与多模态覆盖、Rust 前端功能对齐）、**可靠度**（大量生产级 bug 修复和流程规范化）。Rust 前端的密集迭代暗示项目可能在中期将 Rust 入口提升为一等公民；而 AI 代理深度参与开发并配套质量规范，则为大型开源项目如何规模化使用 AI 辅助开发提供了可参考的实践。

## 详细提交记录

### [d0787e4](https://github.com/vllm-project/vllm/commit/d0787e48394b214f78694fce3520a8c11eca045c)

- **作者**: Yaoyao Ding
- **时间**: 2026-10-21T23:45:12Z
- **提交信息**: [Perf][DSv4.1] DeepSeek-V4.1-Flash specialized decode on GB300 (#61868)

Signed-off-by: Yaoyao Ding <yaoyaod@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0746329](https://github.com/vllm-project/vllm/commit/0746329d2abe3546a1fd805fba44b1838cf23b29)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-21T22:52:02Z
- **提交信息**: [CI] Auto-apply the hisparse label (#62989)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0eea5ac](https://github.com/vllm-project/vllm/commit/0eea5aca8451b25bf3419cd9460125a3132d3169)

- **作者**: C-C-Hao
- **时间**: 2026-10-21T22:45:06Z
- **提交信息**: [Bugfix] Resolve eager_break_during_capture at call time, not import time (#59941)

Signed-off-by: C-C-Hao <csdxzard@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [57d9bf7](https://github.com/vllm-project/vllm/commit/57d9bf768e0e3e2153acc3b01ae3fda3b7393ded)

- **作者**: Ao Tang
- **时间**: 2026-10-21T22:17:03Z
- **提交信息**: [Perf][Kernel] mHC TileLang: skip Sinkhorn on non-finite padding rows; single-pass fused post+pre for <=4 tokens (#62745)

Signed-off-by: Ao Tang <aot@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d29702f](https://github.com/vllm-project/vllm/commit/d29702fd75531ea5dec046a478101f66f390aa5d)

- **作者**: Alex Brooks
- **时间**: 2026-10-21T22:15:10Z
- **提交信息**: [Bugfix] Don't Eliminate Clones for graph I/O Aliases (#60318)

### [0d34366](https://github.com/vllm-project/vllm/commit/0d34366b14e5eef6b1f3c7b799e71cab155ce44a)

- **作者**: XiaochunTong-Cohere
- **时间**: 2026-10-21T21:46:36Z
- **提交信息**: [Perf][Model] Cohere2MoE: attention/MoE dual stream, single TP all-reduce per layer, fused add + RMSNorm (#62101)

Signed-off-by: Xiaochun Tong <xiaochun.tong@cohere.com>
Signed-off-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aa4ec20](https://github.com/vllm-project/vllm/commit/aa4ec2093fe963e77adf26ddd7004dcdb2838722)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-21T20:52:45Z
- **提交信息**: [Doc] DeepSeek-V4.1-Flash: document B200 AgentX router and drop removed c64 points (#62954)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [fc9b7e6](https://github.com/vllm-project/vllm/commit/fc9b7e654643844c1fd17fd54fcd86be86f67e2b)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-21T20:00:58Z
- **提交信息**: [XPU][Test] Relax streaming/non-streaming equality in mistral tool_choice=none test (#62638)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [90c4a1a](https://github.com/vllm-project/vllm/commit/90c4a1a73eecea0428ee4303ad96c9fdeaac3f80)

- **作者**: Hao Wang
- **时间**: 2026-10-21T18:34:23Z
- **提交信息**: [Bugfix] Preserve image normalization constants during dummy loading (#62767)

Signed-off-by: Hao Wang <haowan@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>

### [550c1cb](https://github.com/vllm-project/vllm/commit/550c1cbb8b0a366f1bb2b5aea560a1d8e70f04cb)

- **作者**: Kapil Arya
- **时间**: 2026-10-21T17:58:03Z
- **提交信息**: [KV Offload] Preserve group classification on placeholder events (#59703)

Signed-off-by: Kapil Arya <kapila@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [40210d8](https://github.com/vllm-project/vllm/commit/40210d8317bbad8d05124b260e75677daf33e091)

- **作者**: Jared Wen
- **时间**: 2026-10-21T17:11:09Z
- **提交信息**: [Bugfix][Core] Release libgomp workers before forking engine processes (#62884)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a3ee9a](https://github.com/vllm-project/vllm/commit/4a3ee9a0f6a2958f2712ceb3c9f60fe48cd764b3)

- **作者**: Muti Chung
- **时间**: 2026-10-21T16:26:02Z
- **提交信息**: [Bugfix][Model] Enable ModelOpt support for Cosmos3-Edge (#57393)

Signed-off-by: Mu-Ti Chung <mutic@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [fc84883](https://github.com/vllm-project/vllm/commit/fc84883989269c6d7cfd1281b1c35af584ad95d8)

- **作者**: Misha Goin
- **时间**: 2026-10-21T16:03:52Z
- **提交信息**: [Misc] Say when to use the IMA, microbenchmark, and Triton skills (#60284)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1c87991](https://github.com/vllm-project/vllm/commit/1c879919786497217b3b5fb0258d1d72f2442cb0)

- **作者**: wenjinhust
- **时间**: 2026-10-21T15:47:37Z
- **提交信息**: [Feat][Frontend] Add Watchdog for Engine and Worker Monitoring (#55700)

Signed-off-by: wenjinhust <wenjin.sh@huawei.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [817fa35](https://github.com/vllm-project/vllm/commit/817fa3518cd4bcc94b31e044c534c002e701c801)

- **作者**: Martin Hickey
- **时间**: 2026-10-21T15:20:46Z
- **提交信息**: [Frontend] Add derender output mode to generate (#60082)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [c1210cc](https://github.com/vllm-project/vllm/commit/c1210ccbe5eab9ad5ee1213f0fc09c3ff13e4bea)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T15:01:01Z
- **提交信息**: [Rust Frontend] Support --custom-histogram-buckets (#62826)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b607802](https://github.com/vllm-project/vllm/commit/b6078025b4e10508426ab784752d1de0c827b66c)

- **作者**: Misha Goin
- **时间**: 2026-10-21T14:55:26Z
- **提交信息**: [Docs] Point users at --disable-flashinfer-autotune (#61489)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [85752a4](https://github.com/vllm-project/vllm/commit/85752a43c3cee76d9234704e189cc2ca69f24712)

- **作者**: Linze Shi
- **时间**: 2026-10-21T14:51:16Z
- **提交信息**: [Bugfix][Model] Preserve target-token scoring rows during DeepSeek-V4.1 replay (#62652)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [65a886c](https://github.com/vllm-project/vllm/commit/65a886c69f44cf446d6afa03315f39590ccd843e)

- **作者**: bzsuni
- **时间**: 2026-10-21T14:39:46Z
- **提交信息**: [Bugfix][Pooling] Reject multimodal inputs in chunked embeddings (#62859)

Signed-off-by: bzsuni <bingzhe.sun@daocloud.io>

### [8333491](https://github.com/vllm-project/vllm/commit/833349105b9581d19487295454c19c924e8a3b37)

- **作者**: qli88
- **时间**: 2026-10-21T14:38:03Z
- **提交信息**: [ROCm][Perf] HY4 preview perf boost (#58509)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [a0a645a](https://github.com/vllm-project/vllm/commit/a0a645abdad134bafbc1a8954dd436e4fb0a5e61)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-21T14:25:23Z
- **提交信息**: [CI][KV Connector] Start NIXL accuracy decoders after prefillers on shared GPUs (#62879)

### [35d0166](https://github.com/vllm-project/vllm/commit/35d01660ff3644de128253950b8fcb4b7705668f)

- **作者**: Yan Ma
- **时间**: 2026-10-21T14:19:15Z
- **提交信息**: [XPU] Enable spec-decode adaptive verification without a confidence head (#62244)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c84edac](https://github.com/vllm-project/vllm/commit/c84edac4cba45476755f9c462425ffc8290ab6aa)

- **作者**: djramic
- **时间**: 2026-10-21T14:18:29Z
- **提交信息**: [ROCm][CI] Enable batch invariance for eagle3 scheduling accuracy (#62893)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [18e8791](https://github.com/vllm-project/vllm/commit/18e8791134e8e46134f982c8263d5fa0a50548c0)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T14:04:54Z
- **提交信息**: [Rust Frontend] Apply response_format over structured_outputs like Python (#62823)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2916b4b](https://github.com/vllm-project/vllm/commit/2916b4b4a6b7e9ae552e661b365fec65117134ac)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T14:03:52Z
- **提交信息**: [Rust Frontend] Carry return_token_ids through render like Python (#62822)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bc4794e](https://github.com/vllm-project/vllm/commit/bc4794ef9a9fea5f8a003ef4dc5a49bbe8145241)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T14:03:12Z
- **提交信息**: [Rust Frontend] Support VLLM_LOG_STATS_INTERVAL and VLLM_DISABLE_REQUEST_ID_RANDOMIZATION (#62825)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8a21d0a](https://github.com/vllm-project/vllm/commit/8a21d0a328bb3cbb9c73ca0ae65d83465768cca4)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T14:01:55Z
- **提交信息**: [Rust Frontend] Support `--tokenizer`, `--tokenizer-revision`, and `--hf-config-path` (#62416)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e0ca7d9](https://github.com/vllm-project/vllm/commit/e0ca7d9cc11da2011389c725e5d31c54c3b47259)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T14:00:48Z
- **提交信息**: [Rust Frontend] Report prompts over max_model_len like Python (#62824)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f143f65](https://github.com/vllm-project/vllm/commit/f143f65d7c74b59072ac0f085577aafd75fa7d25)

- **作者**: stefankoncarevic
- **时间**: 2026-10-21T13:43:43Z
- **提交信息**: [CI][ROCm] Set the FP8 MLA prefill scale cache in the test double (#62882)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [db3b0f0](https://github.com/vllm-project/vllm/commit/db3b0f0fae4bc98492b3863685e541e62bc59576)

- **作者**: Mir Mustafa Ali
- **时间**: 2026-10-21T12:11:16Z
- **提交信息**: [Bugfix][KV Connector][ROCm] MoRIIO READ: await every read before the forward (#60808)

Signed-off-by: Mir Mustafa Ali <miali@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4f6a4e2](https://github.com/vllm-project/vllm/commit/4f6a4e2b9d6f5ddbbf429bbc5c29b7c74d31d6bf)

- **作者**: Ziyang Ma
- **时间**: 2026-10-21T11:44:31Z
- **提交信息**: [XPU][UT] Deflake GPT2 score tests with reruns (#57862)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d7ada3a](https://github.com/vllm-project/vllm/commit/d7ada3aace051fecec553c185225db2259c2ac6a)

- **作者**: stefankoncarevic
- **时间**: 2026-10-21T10:51:43Z
- **提交信息**: [CI][ROCm] Give the M3 embed-sharing fixture a kernel_config (#62869)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [96e59c6](https://github.com/vllm-project/vllm/commit/96e59c60e025071476b3567f482cbd18066b25ce)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-21T10:46:37Z
- **提交信息**: [CI] Run the remaining 4xL4 steps nightly only (#62883)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e8e43c6](https://github.com/vllm-project/vllm/commit/e8e43c6a09e4a5fd047cf02b5923db9b2d88ded9)

- **作者**: linitra24
- **时间**: 2026-10-21T10:19:26Z
- **提交信息**: [LoRA] Support BERT token classification heads (#61391)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>

### [9db0da8](https://github.com/vllm-project/vllm/commit/9db0da83f55cc731972238baeca75432bbe4fca2)

- **作者**: aoshen02
- **时间**: 2026-10-21T10:02:57Z
- **提交信息**: [Doc] Raise the bar for agent-written tests (#62601)

Signed-off-by: aoshen02 <281812371+aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <281812371+aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e9cc624](https://github.com/vllm-project/vllm/commit/e9cc6244a0095ba6525230b49a8ecdc2cf7b0f01)

- **作者**: Bugen Zhao
- **时间**: 2026-10-21T09:37:44Z
- **提交信息**: [Rust Frontend] Refresh rust/AGENTS.md with ownership and design conventions (#62721)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6ae1051](https://github.com/vllm-project/vllm/commit/6ae1051bd9120c9e2974a8ad502b4c9716db6b9f)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-21T09:37:10Z
- **提交信息**: [Rust Frontend] Support --exclude-tools-when-tool-choice-none (#62741)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b0e1f80](https://github.com/vllm-project/vllm/commit/b0e1f8052abb3de7c2fa8dc6234733104e829804)

- **作者**: roigarnettNvidia
- **时间**: 2026-10-21T09:27:31Z
- **提交信息**: [Bugfix][MoE] Support simulated routing in monolithic MoE backends (#52780)

Signed-off-by: Roi Garnett <rgarnett@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: tomeras91 <57313761+tomeras91@users.noreply.github.com>

### [5ea2c7f](https://github.com/vllm-project/vllm/commit/5ea2c7ff1e64b36b45bf6bd502367c85633b2d8c)

- **作者**: Martin Hickey
- **时间**: 2026-10-21T09:27:25Z
- **提交信息**: [Frontend] Share ChatStreamProcessor between chat streaming and derender (#62706)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [64c5f14](https://github.com/vllm-project/vllm/commit/64c5f14f6a89aff63bb9ea729a906a055caf00a7)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-10-21T09:05:09Z
- **提交信息**: [ROCm][DI][CI] Enable WideEP EP16/DP16 tests  (#59266)

Signed-off-by: lcskrishna <lollachaitanya@gmail.com>
Signed-off-by: Tej Kiran <kiran.tej@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Tej Kiran <kiran.tej@amd.com>
Co-authored-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: Avinash Paul <Avinash.Paul@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [153b76b](https://github.com/vllm-project/vllm/commit/153b76b304ee6fc176c6ff442f0822764557e255)

- **作者**: Peyman Razaghi
- **时间**: 2026-10-21T09:03:46Z
- **提交信息**: [ROCm][Model][MiniMax-M3] Context-parallel sparse lightning indexer (Triton, opt-in) (#57832)

Signed-off-by: Peyman Razaghi <prazaghi@amd.com>
Co-authored-by: Cursor Grok 4.6 <noreply@cursor.com>
Co-authored-by: Claude Sonnet 4 <noreply@anthropic.com>
Co-authored-by: Cursor Agent <agent@cursor.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [385d1da](https://github.com/vllm-project/vllm/commit/385d1dab3ba489a9f50f7eee704faab49cf760c4)

- **作者**: Micah Williamson
- **时间**: 2026-10-21T08:58:11Z
- **提交信息**: [ROCm][Perf][MiniMax-M3] MonoKernel decode for M3 MXFP4 on MI355X (#62712)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Signed-off-by: <>
Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [1f5514e](https://github.com/vllm-project/vllm/commit/1f5514ec46c2b4d12237282ace0869393e26e0d7)

- **作者**: ly989264
- **时间**: 2026-10-21T08:55:58Z
- **提交信息**: [Bugfix][Rust Frontend] Fix HTTP 500 on long conversations: fuel-limit only request templates (#62374)

Signed-off-by: ly989264 <ly989264@163.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dc61c6d](https://github.com/vllm-project/vllm/commit/dc61c6d027655fb0a427463e1e4cceb86d577eae)

- **作者**: Tianyu Guo
- **时间**: 2026-10-21T08:51:42Z
- **提交信息**: [EPD] Support metadata-only audio-in-video requests (#62573)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [e410466](https://github.com/vllm-project/vllm/commit/e410466a2a301dbc83ee0cf93caae1da102754fe)

- **作者**: aoshen02
- **时间**: 2026-10-21T08:40:56Z
- **提交信息**: [Doc] Require docs for user-visible changes (#62599)

Signed-off-by: aoshen02 <281812371+aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <281812371+aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9353ea5](https://github.com/vllm-project/vllm/commit/9353ea5fdad9c9e0e854d9acae5ffcd1222965c8)

- **作者**: Yejing Lai
- **时间**: 2026-10-21T08:34:19Z
- **提交信息**: [Bugfix][XPU] Fix INC ARK weight loading for small TP shards (#61354)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f4c07f3](https://github.com/vllm-project/vllm/commit/f4c07f326c7c7c56dbb86857404e26a6ef7c065f)

- **作者**: Chaojun Zhang
- **时间**: 2026-10-21T08:19:42Z
- **提交信息**: [XPU][CI] Skip test_bench_forward on XPU (#62829)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fc377f7](https://github.com/vllm-project/vllm/commit/fc377f77714b42f706640d5857a0f2a5f233758d)

- **作者**: aoshen02
- **时间**: 2026-10-21T08:08:57Z
- **提交信息**: [Quantization] Use replace_parameter for params re-created in process_weights_after_loading (#62405)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e2d3340](https://github.com/vllm-project/vllm/commit/e2d3340087699a8a5d2d06683ca3fe33a5e450b2)

- **作者**: aoshen02
- **时间**: 2026-10-21T08:08:05Z
- **提交信息**: [LoRA][Step5] Support LoRA for Step5 (#62498)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-22
**监控日期**: 2026-10-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7292
- **最后更新**: 2026-10-22T00:09:33Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 8
- **主要提交者**: NumberWan, aayc123, mooncake2026

## AI分析总结

# vllm-omni 昨日提交分析

## 1. 主要更新类型

- **功能新增**：Ming3-Audio 新模型支持、FastH3 系列模型加入
- **Bug修复**：ROCm/HIP 平台 Qwen-Image QK-norm 断言、duplex 请求 ID 清理、FlashAttention Hopper 绑定
- **CI/Build**：ROCm MI300 nightly 测试扩展、准确率记录增强、MiniCPM-o 评估隔离
- **文档更新**：FastH3 部署指南

## 2. 关键变更点与项目方向的关系

- **多模态生态扩展**：新增 Ming3-Audio（音频-视觉多模态）和 FastH3 系列模型，直接契合项目"omni-modality model serving"的定位，持续扩大可服务模型覆盖面。
- **硬件平台多元化**：多条提交针对 ROCm（AMD GPU）平台修复和测试（Qwen-Image、HunyuanImage3 LoRA、HunyuanVideo-1.5），表明项目在积极拓展 NVIDIA 之外的硬件支持，降低部署门槛。
- **全双工（Duplex）语音交互深化**：duplex 请求 ID 清理和 Omni-DuplexEval 音轨混音修复，说明全双工语音对话功能已进入稳定化和评测完善阶段。
- **评测基础设施成熟化**：准确率 JSON 记录分支信息、release 分支启用 GHA、TTS 评估 GPU 隔离，体现项目对质量保障体系的重视。

## 3. 对项目的影响和潜在意义

- **平台兼容性提升**：ROCm 相关修复和 CI 扩展使 AMD MI300 用户获得更可靠的体验，扩大潜在用户群。
- **模型覆盖加速**：新模型（Ming3-Audio、FastH3）快速接入反映社区贡献活跃，项目作为统一 omni 服务引擎的地位在加强。
- **生产可用性增强**：duplex 资源泄漏修复和评估流程标准化，为商业场景部署全双工语音服务扫清障碍。
- **发布流程改进**：release 分支 CI 启用意味着项目开始重视稳定版本的质量管控。

## 4. 值得关注的技术点

- **HIP 平台兼容策略**：通过条件跳过而非适配 QK-norm 断言，反映跨平台适配中的务实取舍——优先保证可用性，后续再补全功能对齐。
- **fa3-fwd Hopper 可选绑定**：说明 FlashAttention 3 在不同 GPU 架构上的集成仍需灵活处理，提示 Hopper 用户注意配置。
- **UTMOS 评估隔离**：将 TTS 主观质量指标（UTMOS）与 SIM 评估分离到独立 GPU，避免资源竞争影响评测准确性，是评估系统设计的细节优化。
- **Cursor AI 协作痕迹**：多条提交 Co-authored-by Cursor，显示 AI 辅助开发在该项目中已被常态化采用。

## 5. 基于项目背景的发展影响

vllm-omni 定位为"人人可用的快速廉价 omni 模型服务"。本批提交从三个维度推动这一愿景：**横向**扩展模型与硬件支持（Ming3-Audio、FastH3、ROCm 优化），降低使用门槛；**纵向**深化全双工语音交互的稳定性和评测能力，提升核心差异化功能的成熟度；**基础层**完善 CI 和发布流程，为规模化应用奠定工程质量基础。项目正处于功能快速扩张与工程稳定化并行的阶段，多模态服务引擎的定位日益清晰。

## 详细提交记录

### [c04bef8](https://github.com/vllm-project/vllm-omni/commit/c04bef8e5fd5b47e5559384a2fb0907a79574d36)

- **作者**: haic0
- **时间**: 2026-10-21T22:29:47Z
- **提交信息**: [Bugfix][ROCm] Skip Qwen-Image fused QK-norm assertions on HIP (#9229)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [6b35bca](https://github.com/vllm-project/vllm-omni/commit/6b35bca6ffff3c6bee4723984704fa39c9ac2af0)

- **作者**: Yuanheng Zhao
- **时间**: 2026-10-21T18:46:57Z
- **提交信息**: [New Model] Ming3-Audio (inclusionAI/Ming-3.0-audio-flash) Support (#9130)

Signed-off-by: Yuanheng <jonathan.zhaoyh@gmail.com>
Signed-off-by: 禾波 <yangrunhe.yrh@antgroup.com>
Signed-off-by: vito.yy <vito.yy@antgroup.com>
Co-authored-by: 禾波 <yangrunhe.yrh@antgroup.com>
Co-authored-by: vito.yy <vito.yy@antgroup.com>
Co-authored-by: weiyi.wyf <weiyi.wyf@antgroup.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [325d571](https://github.com/vllm-project/vllm-omni/commit/325d5713503dc6a64a773d8afdc372838568a94d)

- **作者**: haic0
- **时间**: 2026-10-21T16:45:09Z
- **提交信息**: [CI/Build][ROCm] Add HunyuanImage3 LoRA accuracy to MI300 nightly (#9127)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [841cb06](https://github.com/vllm-project/vllm-omni/commit/841cb06be2a987c99bceb77abdede8e2ee3d5fc2)

- **作者**: haic0
- **时间**: 2026-10-21T13:10:04Z
- **提交信息**: [CI/Build][ROCm] Add HunyuanVideo-1.5 accuracy to MI300 nightly (#9125)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [b950ef7](https://github.com/vllm-project/vllm-omni/commit/b950ef7d1a6ef38fab8d222b671ae71bff9638ba)

- **作者**: aayc123
- **时间**: 2026-10-21T13:09:50Z
- **提交信息**: [Bugfix] Retain duplex request IDs until cleanup succeeds (#7708)

Signed-off-by: aayc123 <2803023760@qq.com>
Signed-off-by: aayc123 <115020989+aayc123@users.noreply.github.com>
Signed-off-by: 曾妮 <2803023760@qq.com>

### [1c11eef](https://github.com/vllm-project/vllm-omni/commit/1c11eef1a5a093f064562c47c9cae8b0b5dfbd49)

- **作者**: wangyu
- **时间**: 2026-10-21T12:42:18Z
- **提交信息**: [CI/Build] Record branch in accuracy JSON and enable GHA on release/v* (#9211)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0278901](https://github.com/vllm-project/vllm-omni/commit/0278901f864614ec8f0a0e79e96bc072f7456c6c)

- **作者**: amy-why-3459
- **时间**: 2026-10-21T11:45:28Z
- **提交信息**: [BugFix][Duplex][Benchmark] Add soundtrack mix for Omni-DuplexEval sessions (#9175)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0fc38ce](https://github.com/vllm-project/vllm-omni/commit/0fc38ce3b49482e570586e8ea3d25a930fd5978e)

- **作者**: amy-why-3459
- **时间**: 2026-10-21T11:24:38Z
- **提交信息**: [CI/Build] Gate MiniCPM-o Seed-TTS SIM and isolate UTMOS on the eval GPU (#9160)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [bea9b9e](https://github.com/vllm-project/vllm-omni/commit/bea9b9e9ecb980d3cbdbf0ee061a42f325b83e75)

- **作者**: NumberWan
- **时间**: 2026-10-21T09:06:00Z
- **提交信息**: [Bugfix] Optionally bind fa3-fwd dense FlashAttention on Hopper (#9201)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [95b1d97](https://github.com/vllm-project/vllm-omni/commit/95b1d97f2ec2dc1d93a3e9743bf962b2faaad47b)

- **作者**: SYLAR
- **时间**: 2026-10-21T07:47:15Z
- **提交信息**: [Model] Add FastH3 series (#9167)

Signed-off-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [251fe48](https://github.com/vllm-project/vllm-omni/commit/251fe48f9ed6b960fe6a3e32e52cb99f83540406)

- **作者**: mooncake2026
- **时间**: 2026-10-21T07:43:05Z
- **提交信息**: [Doc] Add FastH3 deployment guidance to MiniMax-H3 recipe (#9204)

Signed-off-by: mooncake2026 <284529637+mooncake2026@users.noreply.github.com>
Co-authored-by: mooncake2026 <284529637+mooncake2026@users.noreply.github.com>

---
