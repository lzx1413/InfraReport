# GitHub Stars 合并报告 - 2026-09-10

**合并日期**: 2026-09-11
**监控日期**: 2026-09-10
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


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2203
- **最后更新**: 2026-09-10T16:53:42Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

# VeOmni 昨日提交分析（共 3 条）

## 1. 主要更新类型

本批次提交以**重构（refactor）**为绝对主导，且其中两条被明确标记为 **BREAKING**（破坏性变更），涉及分布式（dist）、训练器（trainer）与配置（config）三大核心模块。无 Bug 修复或文档更新，属于一次面向架构的集中式调整。

## 2. 关键变更点与项目方向的关系

- **ParallelState 改由 AcceleratorConfig 构建**（#1178）：将并行状态的构造入口统一收敛到加速器配置，减少分散的初始化逻辑。
- **AcceleratorConfig 自解析且按模型作用域划分**（#1090）：让配置具备"自我解析"能力，并将作用域绑定到具体模型，提升配置的自治性与可复用性。
- **异步 offload 主机缓冲池改为注入式**（#1175）：把 host buffer pool 从内部隐式创建改为依赖注入，解耦资源管理与使用方。

这三者共同指向 VeOmni 的核心目标——**"Model-Centric Distributed Recipe Zoo"**（以模型为中心的分布式配方库）。项目要支持任意模态模型的规模化训练，就必须让分布式配置与并行策略足够模块化、可组合。本次重构正是在为"配方"的灵活拼装打地基。

## 3. 对项目的影响与潜在意义

- **BREAKING 变更意味着 API 不兼容**：现有用户若直接依赖旧的 ParallelState 构造方式或 AcceleratorConfig 行为，升级时需适配，短期有迁移成本。
- **长期收益是架构清晰度**：配置自解析 + 模型作用域 + 依赖注入，三者叠加使分布式训练的资源生命周期更可控，便于扩展新并行策略与新模态。
- 对以"配方库"为卖点的项目而言，**配置层的规范化是支撑多配方复用的前提**，这次重构可视为基础设施升级。

## 4. 值得关注的技术点

- **配置自解析（self-resolving）**：配置对象能根据上下文自行推导参数，减少调用方手工拼装，是提升易用性的关键设计。
- **model-scoped 作用域**：将配置粒度下沉到模型级，契合多模态/多模型混合训练场景。
- **异步 offload 缓冲池注入**：显式注入便于测试、复用与内存策略定制，对显存受限的大模型训练尤为重要。
- 三条提交均由 Cursor 协作完成，反映 AI 辅助编码在核心重构中的参与度。

## 5. 结合项目背景的发展影响

VeOmni 定位为"用模型中心的分布式配方扩展任意模态模型训练"。本次重构虽不直接新增功能，但**强化了配置与分布式基础设施的模块化程度**，使"配方"更易组合、更易维护。对追求多模态、大规模训练的用户而言，这是提升可扩展性与可维护性的必要一步；但 BREAKING 属性也提示社区需关注升级指南与迁移路径，以避免生态碎片化。总体看，这是项目从"能用"走向"易扩展、可复用"的架构演进信号。

## 详细提交记录

### [e6c46a9](https://github.com/ByteDance-Seed/VeOmni/commit/e6c46a9a3ba5723061738bdc31dbf16da7e4c89b)

- **作者**: Coach257
- **时间**: 2026-09-10T12:15:46Z
- **提交信息**: [BREAKING][dist, trainer] refactor: build ParallelState from AcceleratorConfig (#1178)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [f1af3f5](https://github.com/ByteDance-Seed/VeOmni/commit/f1af3f58a9283e2fec14acf0f307f048b37a5e25)

- **作者**: Coach257
- **时间**: 2026-09-10T09:06:14Z
- **提交信息**: [BREAKING][config, trainer, dist] refactor: make AcceleratorConfig self-resolving and model-scoped (#1090)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [427b971](https://github.com/ByteDance-Seed/VeOmni/commit/427b97135c393dad2f2779c335d0e56f6d616adc)

- **作者**: Coach257
- **时间**: 2026-09-10T07:24:23Z
- **提交信息**: [dist] refactor: inject the async-offload host buffer pool (#1175)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2803
- **最后更新**: 2026-09-10T14:34:40Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bilang ZHANG, STwangyingrui

## AI分析总结

## 1. 主要更新类型

- **重构（Breaking Change）**：统一推理参数接口，移除 RIFE 相关功能。
- **性能优化**：为 minimax_h3 的 VAE 编码器引入 channels-last 与 FP8 Conv3D 加速路径。
- 附带配置、文档与 checkpoint 转换支持，属于“优化+配套工程化”组合。

## 2. 关键变更点及与项目方向的关系

- **统一推理参数**：LightX2V 定位为轻量视频生成推理框架，参数接口长期存在多套风格。此次统一降低了调用方心智负担，是走向规范化 API 的关键一步；移除 RIFE 表明项目在收敛功能边界，聚焦核心视频生成链路。
- **VAE 编码器加速**：针对 H3 VAE 编码器增加 channels-last 与 SM120 CUTLASS FP8 Conv3D，并支持 FP32/FP16 累加与进程内自动调优。这与项目“Light（轻量、高效推理）”的核心目标高度一致，直接服务于降低显存占用、提升吞吐。

## 3. 对项目的影响和潜在意义

- 统一参数是**破坏性变更**，现有用户脚本可能需迁移，但长期利于生态统一与文档维护。
- 移除 RIFE 会缩小功能面，但减少维护负担，避免非核心模块拖累主线。
- FP8 Conv3D 加速对 **REF2AV** 收益最大，**I2AV** 次之，**T2AV** 不受影响（不执行编码器），说明优化精准命中视频参考类任务这一高价值场景。
- 自动调优机制意味着不同硬件可自适应选择最优路径，提升框架在异构环境下的可用性。

## 4. 值得关注的技术点

- **SM120 架构 + CUTLASS FP8 Conv3D**：面向新一代 GPU 的低精度卷积实现，是推理加速的前沿方向。
- **FP32/FP16 累加可选**：精度与速度可权衡，但 FP16 累加需输出质量验证，存在精度风险。
- **进程内自动调优（in-process autotuning）**：运行时自动选择最优 kernel 配置，兼顾通用性与性能。
- **channels-last 内存布局**：对卷积类算子通常有显著加速，但需确认与现有算子的兼容性。

## 5. 基于项目背景的发展影响

LightX2V 主打“轻量视频生成推理”，这两笔提交分别从**接口规范化**和**底层算子加速**两个维度推进：前者让框架更易用、更易维护，后者让推理更快、更省显存。二者共同强化了项目作为高效视频生成推理框架的定位，尤其巩固了在 REF2AV 等参考视频生成任务上的性能优势。同时，破坏性重构与 FP8 精度验证需求也提示：项目正处于快速迭代期，用户在升级时需关注兼容性与输出质量回归。

## 详细提交记录

### [fabad30](https://github.com/ModelTC/LightX2V/commit/fabad30491f232a6131577b9d28be94989a65914)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-10T13:10:42Z
- **提交信息**: refactor(api)!: unify inference parameters and remove RIFE (#1511)

### [e108827](https://github.com/ModelTC/LightX2V/commit/e1088278f1f34547731cfd7405952e67ed36b695)

- **作者**: STwangyingrui
- **时间**: 2026-09-10T08:19:47Z
- **提交信息**: perf(minimax_h3): accelerate VAE encoder with channels-last and FP8 Conv3D (#1506)

Add optional channels-last and SM120 CUTLASS FP8 Conv3D paths for the H3
VAE encoder, with FP32/FP16 accumulation and automatic in-process
autotuning. Includes checkpoint conversion, configuration and
documentation.

Primarily benefits REF2AV, with smaller impact on I2AV. T2AV does not
execute the encoder. FP16 accumulation requires output-quality
validation.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2244
- **最后更新**: 2026-09-10T02:33:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6370
- **最后更新**: 2026-09-11T00:05:49Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 11
- **主要提交者**: Jiahan Chang (Cyrus), Ka-Hyun Nam, Mingyang Wang

## AI分析总结

# FlashInfer 昨日提交总结

## 一、主要更新类型

昨日共 14 个提交，涵盖性能优化、功能新增、Bug 修复、重构清理、文档与基准测试五类。性能优化聚焦 attention 行检查跳过、topk_varlen 的 gvr_2 调度、SM90 混合输入 CUTLASS MoE 后端提速；功能新增包括 SM100 BF16 rank-major MegaMoE 后端、NVFP4 SVDQuant GEMM 的 CAKE 后端（SM100/SM103）、NVFP4 warp decode 与独立 SiLU；Bug 修复涉及激活函数向量对齐崩溃、MoE 路由缓冲区越界、BF16 Split-K 可用性守卫；重构方面将 KDA 未发布接口实验化并移除其训练/反向 API 家族；此外补全了 MiniMax-H3 运行参数文档，并新增 DeepSeek MoE 对比纯 TRTLLM BF16 的基准脚本。

## 二、关键变更点

**性能与调度**：attention 默认启用 `skip_all_rows_active_check=True`，修复 #3779 引入的 host 同步回退，B200 实测 2.495× 加速；gvr_2 调度补齐 4K–8K 压缩宽度盲区并支持无 hint 运行；SM90 MoE 新增 N64 tactic 与预构建输出描述符，仅对 78 SM 设备（H20）启用。

**新硬件后端**：MegaMoE SM100 后端面向 B200 提供固定容量低延迟专家并行坐标，含 11 阶段生成式 CUDA 源码与 SHA-256 校验；CAKE 后端为 `mm_nvfp4_svdquant` 融合量化 GEMM、低秩修正与可选 bias，要求 CUDA 13.0+；NVFP4 warp decode 精确支持 SM100，保留 SM103 生产契约。

**正确性修复**：激活内核将 `vec_size` 改为模板参数，按 `hidden_size` 选取最大可整除的 2 的幂，解决 Qwen2.5-VL 视觉 MLP（`intermediate_size=3420`）的 `cudaErrorMisalignedAddress`；MoE 路由在 C++ 与 Python 校验器中补充 `dim0 >= num_tokens` 下界检查，防止短缓冲区越界写入。

**API 收敛**：KDA 训练/反向由 cuDNN Frontend 提供，FlashInfer 仅保留推理面（含 `recurrent_kda` 预填充与检查点变体），`__all__` 回退至 v0.6.18 状态，为 0.7 版本 API 统一铺路。

## 三、项目影响

性能回退修复与调度优化直接提升主流推理场景吞吐，降低框架接入成本。MegaMoE、SM90 优化与 NVFP4 CAKE/warp decode 强化了项目在 MoE 推理与 Blackwell 低精度推理上的竞争力。对齐与越界修复提升了真实模型（Qwen2.5-VL、MoE 推理）的鲁棒性。KDA 实验化与训练面移除收敛了 API 边界，减少维护负担与发布风险。基准脚本为 W4A16/W4A4 与 BF16 对比提供统一口径，利于社区复现与选型。

## 四、技术关注点

默认快路径要求每行 query/KV 长度为正，属隐式契约，需注意边界。MegaMoE 采用生成式 CUDA 源码加 SHA-256 校验，工程化程度高。gvr_2 无 hint 模式在 CUDA graph 捕获下被拒绝，需预热预分配。SM90 预构建 D 描述符按 SM 数量编译期切换，避免 JIT 缓存冲突。模板化 `vec_size` 与“最大可整除 2 的幂”策略是处理非对齐维度的通用范式，尾循环移除依赖 `vec_size | d` 的整除保证。CAKE 后端 `backend="auto"` 不选它，需显式指定，体现保守默认策略。MoE 校验区分“下界必须满足、上界可放宽”，正确兼顾安全性与 CUDA Graph 固定最大批次需求。

## 五、整体方向

结合 README“高性能 GPU 推理内核”的定位，本批提交高度契合：一方面修复性能回退、对齐与越界问题，巩固推理可靠性与性能领先；另一方面通过 MegaMoE、CAKE、warp decode 深化 Blackwell 上的低精度、高吞吐推理支持；同时以实验化收敛与训练面移除保持推理专注度。整体显示项目正从“单点内核优化”走向“多硬件、多场景、可维护”的成熟推理库。

## 详细提交记录

### [6bab433](https://github.com/flashinfer-ai/flashinfer/commit/6bab433c080aa419e97f06cc89d7d54d2c1d7366)

- **作者**: Mingyang Wang
- **时间**: 2026-09-10T23:57:09Z
- **提交信息**: fix(attention): default skip_all_rows_active_check to true (#5039)

<!-- .github/pull_request_template.md -->

## 📌 Description

PR #3779 introduced a host synchronization when CPU sequence-length
mirrors are absent. PR #4931 made that check skippable, but left it
enabled by
default, so frameworks must opt in to recover the previous performance.

This changes `skip_all_rows_active_check` to default to `True`. Paired
CPU
length mirrors still take precedence for checked empty-row compaction,
while
explicit `False` without mirrors retains device-derived checking. Calls
using
the default fast path must have positive query and KV lengths for every
row.

On B200/SM100, the new default measured 38.051 µs/call versus 94.927
µs/call
for the checked path (2.495× faster), using batch 32, query length 4, KV
length
512, 16 heads, BF16, and the median of 9 randomized trials.

## 🔍 Related Issues

Fixes #4928. Follow-up to #4931; regression from #3779.

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

Focused B200/SM100 validation passed 14 ragged-attention tests and 4
trace
tests. Scoped pre-commit hooks and diff hygiene also passed.

Full GPU CI is gated until an authorized contributor comments
`@flashinfer-bot run`; the repository-wide suite was not run locally.

Signed-off-by: mingyangw <mingyangw@nvidia.com>

### [dc8148b](https://github.com/flashinfer-ai/flashinfer/commit/dc8148ba9d620b01ce6f952510497145d590258d)

- **作者**: eigen
- **时间**: 2026-09-10T23:16:20Z
- **提交信息**: feat(cake_mega_moe): add SM100 BF16 rank-major MegaMoE backend (#4810)

## 📌 Description

This PR adds an SM100 BF16 rank-major MegaMoE backend for one
fixed-capacity,
low-latency expert-parallel coordinate. Each launch accepts an active
prefix of
1 to 128 token rows per rank while retaining a 128-row workspace
capacity. It
includes:

- an 11-stage generated CUDA source bundle and checksum-pinned manifest;
- a session that owns compilation, workspace allocation, tensor-map
descriptors, and ordered launches;
- the FlashInfer MegaMoE adapter, active-row staging, and weight-layout
conversion;
- host-side contract and validation tests.

### Supported coordinate

| Property | Value |
|---|---:|
| Architecture | SM100 (B200) |
| World size | 8 |
| Maximum tokens per rank | 128 |
| Active tokens per rank per launch | 1–128 |
| Hidden size | 7168 |
| Intermediate size | 2048 |
| Global / local experts | 256 / 32 |
| Top-k | 8 |
| Input / weight / output dtype | BF16 / BF16 / BF16 |
| Layout | rank-major |
| Algorithm | low-latency |

Unsupported capacities and coordinates fail during configuration
validation
rather than silently selecting this backend. All eight EP ranks must use
the
same active-row count, and each rank's runtime inputs must have matching
leading
extents within the supported 1–128 active-row range.

## 🧪 Tests

### Source identity

| Artifact | SHA-256 |
|---|---|
| Direct generated CUDA |
`05d6489228da48a207de6e2e34685d12542badaed694732387375469d6dc3321` |
| Vendored CUDA |
`cc75390cde89d3ba89829a4cad6d811a67565bead4b8226c779858ec89b17ac7` |
| Vendored manifest |
`1ca5fd0f602583ef586f59bcf87a126821723327e055b775038475720dd92168` |

The clean export check at PR head
`466998f16191cda80fb531f0268ccd536b3def16` verified all 11 expected
kernel
symbols and the exact generated, vendored-source, and manifest hashes
shown
above.

### Host-side and CI tests

| Gate | Result |
|---|---|
| Focused lowering/export test | 1 passed |
| FlashInfer host tests | 63 passed |
| Generated-source helper tests | 7 passed, 1 skipped |
| Full PR Test workflow | **Passed**: [run
34261776233](https://github.com/flashinfer-ai/flashinfer/actions/runs/34261776233),
14/14 jobs at exact PR head; `13,988`s workflow turnaround, including
`8,166`s H100 JIT runtime |

### 8×B200 correctness and paired performance

Evidence run `1917124.8` measured the generated reference path and the
vendored
FlashInfer path in the same exclusive 8×B200 allocation and process
lifetime.
Timings use cold-L2 CUPTI activity spans and include exactly 11
correlated
kernel activities per rank per iteration. Setup, compilation, workspace
allocation, weight-layout preparation, and tensor-map construction are
outside
the measured region.

| Checkpoint | Generated reference median (ms) | FlashInfer median (ms)
| FlashInfer / reference | Reference / FlashInfer speedup |
|---:|---:|---:|---:|---:|
| 1 | `0.6629205` | `0.5953525` | `0.898075259` | `1.113492427`× |
| 2 | `0.661384` | `0.5916085` | `0.894500774` | `1.117942017`× |
| 3 | `0.662105` | `0.596794` | `0.901358546` | `1.109436422`× |
| **Summary** | — | — | **`0.901358546` maximum / `0.897973826`
geomean** | **`1.109436422`× minimum / `1.113618205`× geomean** |

- Correctness: **passed** on all 8 ranks at BF16 `atol=0.01`,
`rtol=0.01`,
with zero mismatches and zero maximum absolute/relative error for both
paths.
- No-regression gates: **passed**; every FlashInfer/reference ratio was
at
most `0.901358546` and the geomean was `0.897973826`, versus required
limits
  of 1.05 and 1.03.
- Hardware: exactly eight B200/CC10.0 devices in one exclusive step.
- Physical timing: `113.723015`s paired-measurement window,
  `128.835860729`s driver, `162`s exclusive 8-GPU step, and
  `170.932982922`s submission-to-completion turnaround.
- Evidence SHA-256: comparison
  `d04d61e59ef95d120dbb7ce89662aabb8571c7ad4df63456ee4eb5b32c9affcf`;
  receipt
  `d63a8464d9b3c49ff19b2186e20cb4ee97e2bb9f74c924f862eda170b8f28bea`;
  artifact index
  `80f410b47cbf6be78cf273abd42fa21d2286908885b674bb366df5791264e563`.

### Compute Sanitizer

Retained runs `1899002.19` (synccheck) and `1899002.15` (racecheck) used
the same generated-source, vendored-source, and manifest hashes listed
above.
These are source-identical sanitizer results, not new executions at the
latest repository head.

Both sanitizer tools were run separately against one complete 11-stage
DAG on
each of eight B200 ranks. The application correctness check used the
same BF16
`atol=0.01`, `rtol=0.01` gate and passed on every rank with zero
mismatches and
zero maximum error.

| Tool | Result |
|---|---|
| synccheck | **Passed cleanly**: tool exit 0; 8/8 logs report `ERROR
SUMMARY: 0 errors`; no sanitizer-internal or target-application error |
| racecheck | **Completed with a confirmed tool false positive**:
application correctness passed, but the tool returned 86 for the
allocator-expansion signature described below |

Racecheck reported the same two signatures on each rank, in the FC1 and
FC2
stages: an allocator-internal write at a negative program counter and a
reported
read within the `tcgen05.alloc.cta_group::2` expansion. There were 592
displayed
hazards per stage per rank (9,472 underlying instances total). A
standalone
minimal kernel containing only the allocation, required synchronization,
address consumption, and deallocation reproduces the same negative-PC
hazard
while running successfully without the sanitizer. Disassembly maps the
reported
read PC to `SYNCS.ARRIVE.TRANS64.RED` inside the assembler-generated
allocation
sequence, before the source-level address load. No target-application
error or
sanitizer-internal error was reported. This evidence is recorded as a
bounded
Compute Sanitizer limitation, not as a zero-error racecheck result.

- synccheck runtime: `782.255600452`s sanitizer span; `812`s 8-GPU step.
- racecheck runtime: `190.873103380`s sanitizer span; `220`s 8-GPU step.
- minimal reproducer runtime: `3.997018337`s driver; `26`s step.
- synccheck summary/index SHA-256:
  `a5f5c68435b639e960b28a6772280262a5738e7b7be8734cce1c027cbc35ccb8` /
  `8db3d451b69bbe425538ae81949054e052ee3f327addd6a4351938272d54ede9`.
- racecheck summary/index SHA-256:
  `be03156c17281cae07331b62116a7a4e4f7e3048973d4ddb017421d68cc8087d` /
  `a08b4b1dedb6b3d9645f2ceeca84f3ed49f5ab0a5a188aaad6e337a11c92edd6`.
- reproducer receipt/index SHA-256:
  `c708913da8a147a71da986fee2da860de6b99cc8a17d61c53b93ae3b583ce958` /
  `95e5ad5fe43afaaeb7c014585c61c18be675f5ae8b3dbe89824df61f8fe95064`.

### Real-model integration

Current comparison `1917124.10` used real DeepSeek-V3-0324-BF16 weights
at revision
`2e840f66bd45f87e2078d0972405e53dc26672c1`. The same-allocation paired
serving
run on eight B200s passed both correctness and performance gates. Two
deterministic 32-token probes (1000- and 1024-token inputs) produced
identical
output token IDs; maximum output-logprob deltas were `0.0039856611` and
`0.0001090435`.

| Workload | Baseline throughput | FlashInfer throughput | FlashInfer /
baseline |
|---|---:|---:|---:|
| Prefill (input tok/s) | `3639.680149` | `4650.939306` | `1.277842864`×
|
| Decode (output tok/s) | `66.766437` | `64.940911` | `0.972658025`× |
| Mixed (total tok/s) | `1772.745784` | `2253.482340` | `1.271181892`× |
| **Summary** | — | — | **`0.972658025`× minimum / `1.164702769`×
geomean** |

The required minimum per-workload ratio was `0.95` and required geomean
was
`1.0`. Decode throughput was 2.73% lower, within the 5% per-workload
limit.
Current-head comparison step `1917124.10` completed in a
`1537.123533726`s
physical payload window, `1567`s exclusive GPU step, `1577.348894119`s
managed runtime, and `1577.462846994`s submission-to-completion
turnaround.
Summary SHA-256:
`5ae0c17c7890e8decfcdf422538602b599019522fa279540989a9b5e0f1c911b`.

Current formal 8-shot GSM8K ran only through controller `1917640` with
literal Slurm dependency `afterok:1917639` on the successful comparison
validator. Its authorization binds qualifying comparison `1917124.10`.
Step `1917124.19` scored **`0.9496567506`** (1,245 correct out of all
1,311
evaluated examples), strictly above the required `0.935`, at the same PR
head
and model revision. Evaluation latency was `498.308874611`s; the GPU
payload
span was `1260.085841179`s, Slurm runtime `1296`s, managed runtime
`1304.746068716`s, and submission-to-completion turnaround
`1304.855983973`s.
The complete comparison-request-to-GSM8K-completion turnaround was
`3572.044692516`s.

- GSM8K summary SHA-256:
  `b06b71ca91a3cff7f4b11e027d2912c9ef4052e5195e311d3c203877414d9929`.
- Authorization receipt SHA-256:
  `8681237aac4c44d1edfb36d8276bb7b8e4c7bb16b5fdfeb4c9b8d56f02b2ac18`.
- Literal-afterok submission receipt SHA-256:
  `37dfe10d50fc272a9217e85f6b017f947658f0cb84de89185d892dbffd53d3e9`.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks.
- [x] I have run `pre-commit run --all-files` and fixed the reported
issues.

### Tests

- [x] Tests have been added or updated as needed.
- [x] Exclusive final-head paired correctness/performance.
- [x] Separate source-identical synccheck completed cleanly.
- [x] Separate source-identical racecheck completed and its
allocator-expansion false positive was reduced to a standalone
reproducer.
- [x] Full current-head PR Test workflow: 14/14 jobs passed in run
`34261776233`.
- [x] Real-model comparison `1917124.10` and dependency-bound formal
GSM8K `1917124.19` passed.

## Reviewer Notes

The backend intentionally fixes the maximum coordinate and workspace
capacity,
while accepting 1–128 active rows per rank at runtime. The main review
surfaces
are the manifest-pinned launch ABI, active-row grid selection and
rank-major
mapping, workspace ownership/lifetime, staging, and explicit rejection
of
unsupported capacities and coordinates.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for a Blackwell SM100 BF16 rank-major MegaMoE CUDA
backend.
* Added preprocessing and validation for rank-major BF16 model weights
and inputs.
* Added support for variable active token counts from 1 to 128 per rank.
* Added packaged kernel resources for on-demand compilation and
execution.
* Added session-based execution and workspace management for the fixed
eight-rank configuration.

* **Tests**
* Added coverage for backend registration, validation, kernel manifests,
session behavior, and workspace pooling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [7b40d3c](https://github.com/flashinfer-ai/flashinfer/commit/7b40d3cb914cef34544a831994bd8d8a1a9987d2)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-09-10T22:52:15Z
- **提交信息**: perf(topk_varlen): gvr_2 dispatch rungs for 4K-8K rows, SM-count-aware register band, hint-free gvr_2 in auto (#4986)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #4811 (these two commits were pushed to its branch after
the squash-merge, so they never landed). Both are host-side changes to
the `gvr_2` self-sampling top-k backend; no kernel code changes.

**1. `gvr_2` dispatch rungs for compressed widths 4K < n <= 8K
(`c7f9075f`).** An SGLang report ("gvr_v2 slower than
`topk_transform_512_v2` at 32K with c4") reproduced with their input
recipe held in exactly one band: compressed width 6144-8192, where
`gvr_2` was 3-7% slower at bs <= 128 and 13-21% slower at bs 256, while
already 8-45% faster at every other width from 4096 to 131072. The cause
is the dispatch, not the kernels: for `1024 < n4 <= 4096` the upstream
`route()` runs every `wide` row on the VPT=4 register kernel (two empty
float4 slots per thread up to n = 8192) and sends b > 148 to the
streaming slab. Two FlashInfer-local rungs (marked inline, reported to
the kernel owner as internal DKG issue #61): `n4 <= 2048` and `wide` ->
`_reg(1024, 2, 1, 2*NB)` (18-20% faster for K in {512, 1024, 2048}); `n4
<= 2048` and one wave of `MINB=2` CTAs -> `_reg(512, 4, 2, NB)` instead
of the slab (1.3-1.7x), with `NBSEL` following so `IMGOFF == NBH`.

**Hint-free `gvr_2` (same commit).** `pre_idx` is now optional for
`gvr_2`: `run_varlen(pre_idx=None, top_k=K)` runs on a cached
`arange(k)` table (`_hint_free_pre_idx`, per (device, k), grown eagerly,
refused under CUDA-graph capture, pre-sized by `warmup_varlen`). The
kernels use the hint only as a sampling anchor, so the result is exact;
hint-free is within ~10% of the hinted time on most cells and 1.5-5x
ahead of `radix` / `radix_filter` everywhere except K >= 2048, N <=
4096, B = 1 (radix_filter 1.3x faster). `auto` ranks `gvr_2` first for
fp32 with or without a hint, with that one cell carved out to
`radix_filter`; a malformed hint on `backend="gvr_2"` is discarded with
the existing RuntimeWarning and the call still runs on `gvr_2`; the
"requires pre_idx" refusal now applies to `gvr` only.

**2. SM-count-aware register band (`4cb98eab`).** `route()` hard-codes
148 (the B200 SM count). Tuning the same band on B300 (160 SMs) and
Rubin (208 SMs) showed the remaining losses sat exactly where that
constant mis-sizes a wave: rows in (148, sms] are one wave of
1024-thread CTAs there and the register kernels beat the slab by
1.4-1.8x (B300 12288 x 160: 7.2 -> 4.6 us; Rubin 12288 x 160-192: 5.6 ->
4.0 us). `route(b, n, npad, k, sms=148)` takes the device SM count
(`_sm_count()`, part of both launcher cache keys) for the register-band
tests only: `wide`, the `QC`/`CURE` flags, and the BLK=512 rung's wave
cutoffs (`b <= 2*sms`, plus a second wave `b <= 4*sms` from n = 6144
up). The streaming constants stay at 148 on every part: scaling them
made the 131072 x 192-256 slab cells 3-28% slower on B300 and Rubin.

**Measured** (same-node, one process per node, isolated computelab B200
/ B300 nodes and Rubin; sglang `topk_v2` vs `gvr_2` with the upstream
dispatch vs with this PR; K = 512, perfect hint, CUDA-graph replay
medians; 84 uniform cells = 7 widths 4096-131072 x 12 batch sizes 1-512,
48 ragged cells = 4 widths x 12 batch sizes, per-row lengths uniform in
[1, width]). `gvr_2` faster-or-equal than sglang:

| GPU | uniform, upstream dispatch | uniform, this PR | ragged, upstream
| ragged, this PR |
|---|---|---|---|---|
| B200 (148 SMs) | 65 / 84 | 83 / 84 | 35 / 48 | 45 / 48 |
| B300 (160 SMs) | 62 / 84 | 82 / 84 | 31 / 48 | 43 / 48 |
| Rubin (208 SMs) | 58 / 84 | 84 / 84 | 31 / 48 | 46 / 48 |

At the reported cell (width 8192, B200): sglang 4.27-4.48 us vs `gvr_2`
3.62-3.76 us for bs 1-128 (was 4.46-4.58); 6.77 vs 4.89 us at bs 256
(was 8.04). Every `gvr_2` cell in every run was value-multiset exact.
What sglang still wins: 1-4 randomly short rows at width 4096 (~1 us
calls; its short-row early exit is 0.3-0.5 us cheaper), the second CTA
wave at width 12288 (B200 bs 160 0.99; B300 bs 256-320 0.91-0.97), and a
few B300 ragged cells within 7%. Note sglang's kernel fuses the
page-table transform, so it does slightly more work per call.

Tried and rejected (measured, same-node): swapping the `regimg` flavour
for plain `reg` at n <= 4K (+5%..-12% by cell and hint quality);
clustered-register configs for 8K < n <= 16K at b > sms (2-4x slower);
`_reg(1024, 4, 1)` for the second wave of 8K-16K (mixed); scaling the
streaming constants (see above).

## 🔍 Related Issues

Follow-up to #4811. Dispatch findings reported to the TRT-LLM kernel
owner as internal DKG issue #61 (the DSL host in TensorRT-LLM has the
same rungs).

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

New tests: hint-free exactness on every kernel family incl.
short/MTP/cr=4 rows; hint-free CUDA-graph replay with table-growth
refusal; host `top_k` contract; the rungs (tuple, `NBH == IMGOFF`, wave
cutoffs, `route_split` parity); SM-count-aware dispatch (rungs at sms /
2*sms / 4*sms for sms in {160, 208}, streaming half identical for every
sms); `auto` order with and without a hint; per-backend malformed-hint
behaviour; family-parity key carries the SM count. `tests/topk_varlen`
on the final code: A100, L40S, H100, RTX 5080 (74-78 passed, `gvr_2`
skips), B100, DRIVE P2021, isolated computelab B200 and B300, Rubin
(323-324 passed, 2 known xfails).

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

Both commits are FlashInfer-local deviations from the vendored TRT-LLM
host dispatch (`route()` is otherwise a pure mirror); each deviation is
marked inline with its measurement. The `logs/`-style benchmark scripts
are not part of the PR.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* GVR2 varlen top-k execution supports workloads without a precomputed
index hint.
* Backend selection adapts to hint availability, top-k values, workload
size, and GPU resources.
* Workspace management supports separate allocations per device and CUDA
stream.

* **Bug Fixes**
* Improved validation and warnings for malformed hints and missing or
invalid top-k values.
* Improved CUDA Graph reliability through stream-specific warmup and
workspace requirements.
* Improved correctness for concurrent multi-stream and multi-device
execution.

* **Performance**
* Expanded SM-aware optimization coverage across GPU configurations and
larger top-k ranges.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [19a103e](https://github.com/flashinfer-ai/flashinfer/commit/19a103e6e688f4c2c370a7b5456720089f6999ca)

- **作者**: Ziang Li
- **时间**: 2026-09-10T20:57:26Z
- **提交信息**: bench: compare DeepSeek MoE against pure TRTLLM BF16 (#4985)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

Compare CuTe DSL W4A16/W4A4 MoE against pure TRTLLM BF16 using the same
DeepSeek-V3 source inputs. Extend `benchmarks/bench_moe_deepseek.py`
with BF16 and NVFP4 precision modes in the existing `bench_trtllm`
helper.

- **BF16 contract:** BF16 activations and expert weights; public
`TrtllmBf16Config.prepare_weights` applies gated row reorder and
BlockMajorK layout outside timing, with no quantization.
- **Integration:** `TRTLLM NVFP4` / `TRTLLM BF16` output and
`trtllm-nvfp4` / `trtllm-bf16` selectors for benchmarking/profiling;
shared routing, autotuning and measurement setup with explicit precision
branches. Both precisions reuse the same cached routed realization per
input row.
- **Finalize:** `--no-fused-finalize` applies to CuTe. TRTLLM retains
native finalize; FP4 activation flags do not affect pure BF16.
- **Scope:** benchmark script only; no kernel or distributed-script
changes. Three configurations below: inference per-tensor, inference
per-token, and the deterministic RL configuration from #4048.

### Source and environment

- **Measured source:** `1ac2233d43df747af455ed4a8406d7439d686d9f`
(FlashInfer 0.6.18), used for all nine sweeps. **Implementation head:**
`2079fa00c4a2a0fb2e95bb284978a703653a4830`. The nine sweeps precede the
shared-helper/name/CLI-validation updates. Separate diagnostic
measurements below identify their own source commits; they do not
replace the original sweeps. Paired refactor correctness validation is
linked in Tests.
- **Hardware:** retained C2 devbox, one B300 SXM6 AC
(`CUDA_VISIBLE_DEVICES=0`, SM103, 148 SMs, 267.7 GiB) on an eight-B300
host; driver 590.48.01 and image CUDA compatibility library 595.58.03.
- **Image:** `nvcr.io/nvidia/pytorch:26.05-py3`; digest
`nvcr.io/nvidia/pytorch@sha256:222d8b18e671be5c3ef91cb41727a2572a0b23f59ded6c39f373a96946f6f2ba`.
- **Software:** CUDA toolkit 13.2 (`nvcc V13.2.78`), PyTorch
`2.12.0a0+5aff3928d8.nv26.05`, Python 3.12.3, CuTe DSL `[cu13]==4.7.0`,
`cupti-python==13.2.0`, `nvidia-cuda-cupti==13.2.86`,
`apache-tvm-ffi==0.1.13.post3`; `nvidia-cuda-nvdisasm==13.3.73` is the
DSL disassembler dependency, while compiler/runtime remain CUDA 13.2.
- **Provenance:** editable metadata still reports initial commit
`e713467f`; the measured Git checkout is `1ac2233d`. Their difference
only shares routed benchmark inputs across TRTLLM precisions. Warm
compilation caches are retained.

### Reproduction and configuration

Run inside the image above. Setup the exact measured source; the
optional EP-transport build is disabled because no communication is
performed.

```sh
set -euo pipefail
mkdir -p /workspace/flashinfer-moe-bf16-benchmark/artifacts
cd /workspace/flashinfer-moe-bf16-benchmark
git clone --branch zianglih/bench-deepseek-moe-bf16 https://github.com/zianglih/flashinfer.git flashinfer
cd flashinfer
git checkout --detach 1ac2233d43df747af455ed4a8406d7439d686d9f
git submodule update --init --recursive
export BUILD_NVEP=0 FLASHINFER_BUILD_NO_PIP=1 MAX_JOBS=8
python3 -m pip install 'setuptools>=77' 'apache-tvm-ffi>=0.1.6,!=0.1.8,!=0.1.8.post0,<0.2'
python3 -m pip install 'nvidia-cutlass-dsl[cu13]==4.7.0' 'cupti-python==13.2.0' 'nvidia-cuda-cupti==13.2.86' 'nvidia-cuda-nvdisasm==13.3.73' ninja einops pytest pytest-timeout
python3 -m pip install --no-build-isolation --no-deps -e .
python3 -m flashinfer.collect_env > ../artifacts/environment.txt
python3 -m pip freeze > ../artifacts/pip-freeze.txt
nvcc --version >> ../artifacts/environment.txt
nvidia-smi --query-gpu=name,uuid,driver_version,memory.total --format=csv >> ../artifacts/environment.txt
```

Run each command below from that checkout. All commands use logits
routing, wrapper API, TP1, initial activation quantization included,
CUDA graphs, CUPTI and autotuning. The existing order was per-token 1,
RL 1, per-token 2, RL 2, per-token 3, RL 3. Only the added per-tensor
variant was subsequently run three times consecutively. Every repetition
starts a fresh Python process.

**Inference per-tensor — `Per-token activation: False`:** omit
`--use-per-token-activation`; use the existing global-scale path, 4over6
disabled, FP4 quantization fast math enabled, CuTe fused atomic
finalize. The default CLI includes CUTLASS NVFP4 in this configuration.

```sh
env \
  -u FLASHINFER_NVFP4_4OVER6 \
  -u FLASHINFER_NVFP4_4OVER6_E4M3_USE_256 \
  -u FLASHINFER_NVFP4_4OVER6_ERR_MODE \
  -u FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH \
  -u FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH \
  CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 MAX_JOBS=8 \
  python3 benchmarks/bench_moe_deepseek.py \
    --num-tokens 1,2,4,8,16,32,64,128,256,512,1024,2048,4096 \
    --ep 8 --warmup 10 --iters 100 --routing-input-mode logits \
    --include-activation-quant
```

**Inference per-token — `Per-token activation: True`:** per-token
activation scaling, 4over6 disabled, FP4 quantization fast math enabled,
CuTe fused atomic finalize. CUTLASS is omitted because it does not
consume per-token scales.

```sh
env \
  -u FLASHINFER_NVFP4_4OVER6 \
  -u FLASHINFER_NVFP4_4OVER6_E4M3_USE_256 \
  -u FLASHINFER_NVFP4_4OVER6_ERR_MODE \
  -u FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH \
  -u FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH \
  CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 MAX_JOBS=8 \
  python3 benchmarks/bench_moe_deepseek.py \
    --num-tokens 1,2,4,8,16,32,64,128,256,512,1024,2048,4096 \
    --ep 8 --warmup 10 --iters 100 --routing-input-mode logits \
    --include-activation-quant --use-per-token-activation
```

**Deterministic RL — `Per-token activation: True`:** per-token 4over6
MSE, E4M3 max 256, error fast math enabled, FP4 quantization fast math
disabled, CuTe two-stage finalize. This is the requested configuration
name, not a full-model determinism claim; CUTLASS is omitted.

```sh
env \
  -u FLASHINFER_NVFP4_4OVER6 \
  -u FLASHINFER_NVFP4_4OVER6_E4M3_USE_256 \
  -u FLASHINFER_NVFP4_4OVER6_ERR_MODE \
  -u FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH \
  -u FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH \
  CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 MAX_JOBS=8 \
  FLASHINFER_NVFP4_4OVER6=1 \
  FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1 \
  FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE \
  FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=1 \
  FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1 \
  python3 benchmarks/bench_moe_deepseek.py \
    --num-tokens 1,2,4,8,16,32,64,128,256,512,1024,2048,4096 \
    --ep 8 --warmup 10 --iters 100 --routing-input-mode logits \
    --include-activation-quant --use-per-token-activation --no-fused-finalize
```

- **Timing:** 10 warmups, 100 iterations/case, cold L2; each run reports
median iteration latency. Routing, expert computation, finalize and
initial FP4 activation quantization are timed. W4A16/BF16 consume BF16
directly. Weight preparation, compilation and autotuning are outside
measurement.
- **Workload:** H=7168, I=2048, E=256, 32 local experts (EP8
simulation), top-k=8, 8 groups/top-4 groups, routed scale=2.5, bias
scale=0.01, seed 42, tokens 1–4096 in powers of two. All arms share
source BF16 inputs and logits within each row. TFLOPS uses expected
uniform local work fraction 32/256; printed routing statistics show
actual local routes.
- **Capture:** an outer wrapper serializes returned `BenchResult`
records after measurement; original CLI/timing functions are unchanged.
All nine processes exited 0. All 507 captured latencies (6×13×4 +
3×13×5) were checked against the printed values before aggregation.

### Complete raw performance results

All nine complete result tables follow. Backend names and table spacing
are normalized for display; decorative divider lines are omitted.
Original logs and captures remain unchanged, as do every result value
and column. Identical printed configuration headers are shown once per
three-run group. Raw latency prints to 0.001 ms; raw speedups use
unrounded values. The existing six per-token/RL measurements remain
unchanged; only the three per-tensor runs were added.

**Inference per-tensor — printed configuration for all three runs:**

```text
DeepSeek-V3 MoE Performance Benchmark
GPU: NVIDIA B300 SXM6 AC
CuteDSL API: Wrapper
Per-token activation: False
Initial activation quantization: True
CuteDSL modes: W4A4 and W4A16; baselines: TRTLLM NVFP4 and TRTLLM BF16
Tensor parallelism simulation: TP=1
CUDA profiler capture: False
CuteDSL finalize: atomic fused
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
DeepSeek-V3 MoE Benchmark: CuteDSL W4A4/W4A16 vs CUTLASS vs TRTLLM NVFP4 / TRTLLM BF16 (EP=8, TP=1)
Model: hidden=7168, intermediate=2048, experts=256, top_k=8
EP Config: 32 local experts (simulating 8-way parallelism)
TP Config: intermediate size 2048 (simulating 1-way parallelism)
CUDA Graph: enabled, CUPTI: enabled
Routing bias scale: 0.01 (larger values tend to create expert imbalance)
Timed initial activation quantization for FP4-activation backends: included; W4A16 and TRTLLM BF16 consume BF16 directly
CuteDSL finalize: atomic fused
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
```

<details>
<summary>Inference per-tensor run 1 — 13 token counts, 5
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | CUTLASS       | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs CUTLASS | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16     | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.031     2.8 | 0.040     2.2 | 0.048     1.8 | 0.026     3.4 | 0.051     1.7 | 1.53x    1.21x     | 0.82x    0.65x          | 1.63x    1.29x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.040     4.4 | 0.046     3.9 | 0.058     3.1 | 0.036     4.9 | 0.079     2.2 | 1.43x    1.26x     | 0.89x    0.79x          | 1.95x    1.72x         | TRTLLM NVFP4 | 4       | 0/  1/   0.00
4      | 0.057     6.2 | 0.063     5.6 | 0.070     5.0 | 0.051     6.9 | 0.117     3.0 | 1.24x    1.12x     | 0.89x    0.81x          | 2.05x    1.85x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.073     9.7 | 0.079     8.9 | 0.086     8.2 | 0.064    11.0 | 0.157     4.5 | 1.18x    1.10x     | 0.88x    0.81x          | 2.15x    1.99x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.083    17.0 | 0.085    16.5 | 0.097    14.5 | 0.076    18.7 | 0.192     7.3 | 1.17x    1.14x     | 0.91x    0.89x          | 2.32x    2.25x         | TRTLLM NVFP4 | 13      | 0/  2/   0.00
32     | 0.113    24.8 | 0.119    23.8 | 0.127    22.1 | 0.106    26.5 | 0.285     9.9 | 1.12x    1.07x     | 0.94x    0.90x          | 2.52x    2.41x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.146    38.5 | 0.153    36.9 | 0.159    35.6 | 0.139    40.6 | 0.388    14.5 | 1.08x    1.04x     | 0.95x    0.91x          | 2.65x    2.54x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.150    75.3 | 0.158    71.5 | 0.164    68.8 | 0.144    78.3 | 0.399    28.3 | 1.10x    1.04x     | 0.96x    0.91x          | 2.66x    2.53x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.158   142.8 | 0.164   137.2 | 0.173   130.0 | 0.154   146.7 | 0.427    52.8 | 1.10x    1.06x     | 0.97x    0.94x          | 2.71x    2.60x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.160   282.2 | 0.169   267.2 | 0.179   251.4 | 0.164   275.3 | 0.435   103.7 | 1.12x    1.06x     | 1.03x    0.97x          | 2.72x    2.58x         | W4A4         | 32      | 7/ 23/  14.00
1024   | 0.165   545.5 | 0.189   476.0 | 0.197   458.2 | 0.295   305.4 | 0.444   203.3 | 1.19x    1.04x     | 1.79x    1.56x          | 2.68x    2.34x         | W4A4         | 32      | 17/ 42/  28.50
2048   | 0.177  1018.3 | 0.233   773.7 | 0.223   810.3 | 0.299   602.6 | 0.475   379.4 | 1.26x    0.95x     | 1.69x    1.28x          | 2.68x    2.04x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.219  1646.7 | 0.363   993.0 | 0.281  1282.8 | 0.309  1167.4 | 0.529   682.5 | 1.28x    0.77x     | 1.41x    0.85x          | 2.41x    1.45x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Inference per-tensor run 2 — 13 token counts, 5
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | CUTLASS       | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs CUTLASS | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16     | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.031     2.8 | 0.039     2.2 | 0.048     1.8 | 0.026     3.4 | 0.051     1.7 | 1.53x    1.21x     | 0.82x    0.65x          | 1.63x    1.29x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.040     4.4 | 0.046     3.8 | 0.058     3.1 | 0.036     4.9 | 0.079     2.2 | 1.43x    1.26x     | 0.89x    0.79x          | 1.95x    1.72x         | TRTLLM NVFP4 | 4       | 0/  1/   0.00
4      | 0.057     6.2 | 0.063     5.6 | 0.070     5.0 | 0.051     6.9 | 0.117     3.0 | 1.24x    1.12x     | 0.89x    0.81x          | 2.05x    1.85x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.073     9.7 | 0.079     9.0 | 0.086     8.2 | 0.064    11.0 | 0.157     4.5 | 1.18x    1.10x     | 0.88x    0.81x          | 2.15x    1.99x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.083    17.0 | 0.088    16.0 | 0.097    14.5 | 0.076    18.6 | 0.192     7.3 | 1.17x    1.10x     | 0.91x    0.86x          | 2.32x    2.17x         | TRTLLM NVFP4 | 13      | 0/  2/   0.00
32     | 0.114    24.8 | 0.118    23.8 | 0.127    22.1 | 0.106    26.6 | 0.285     9.9 | 1.12x    1.08x     | 0.93x    0.90x          | 2.51x    2.41x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.147    38.4 | 0.151    37.4 | 0.159    35.5 | 0.140    40.3 | 0.388    14.5 | 1.08x    1.05x     | 0.95x    0.93x          | 2.64x    2.57x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.150    75.3 | 0.158    71.3 | 0.164    68.8 | 0.144    78.2 | 0.399    28.2 | 1.09x    1.04x     | 0.96x    0.91x          | 2.67x    2.53x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.158   143.0 | 0.164   137.1 | 0.173   130.2 | 0.154   146.5 | 0.428    52.7 | 1.10x    1.05x     | 0.98x    0.94x          | 2.71x    2.60x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.160   281.9 | 0.169   267.3 | 0.179   251.3 | 0.164   275.4 | 0.435   103.8 | 1.12x    1.06x     | 1.02x    0.97x          | 2.72x    2.58x         | W4A4         | 32      | 7/ 23/  14.00
1024   | 0.165   546.4 | 0.190   475.7 | 0.197   458.4 | 0.295   305.4 | 0.443   203.6 | 1.19x    1.04x     | 1.79x    1.56x          | 2.68x    2.34x         | W4A4         | 32      | 17/ 42/  28.50
2048   | 0.177  1018.2 | 0.233   772.9 | 0.223   810.6 | 0.299   603.6 | 0.476   379.1 | 1.26x    0.95x     | 1.69x    1.28x          | 2.69x    2.04x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.217  1661.9 | 0.363   994.3 | 0.281  1283.9 | 0.309  1166.6 | 0.530   680.7 | 1.29x    0.77x     | 1.42x    0.85x          | 2.44x    1.46x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Inference per-tensor run 3 — 13 token counts, 5
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | CUTLASS       | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs CUTLASS | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16     | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.031     2.8 | 0.040     2.2 | 0.048     1.8 | 0.026     3.4 | 0.051     1.7 | 1.53x    1.21x     | 0.82x    0.65x          | 1.64x    1.29x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.043     4.1 | 0.046     3.9 | 0.058     3.1 | 0.036     4.9 | 0.078     2.2 | 1.34x    1.26x     | 0.83x    0.79x          | 1.82x    1.71x         | TRTLLM NVFP4 | 4       | 0/  1/   0.00
4      | 0.057     6.2 | 0.063     5.6 | 0.071     5.0 | 0.051     6.9 | 0.117     3.0 | 1.24x    1.12x     | 0.90x    0.81x          | 2.05x    1.85x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.073     9.7 | 0.079     9.0 | 0.086     8.2 | 0.064    11.0 | 0.156     4.5 | 1.18x    1.10x     | 0.88x    0.81x          | 2.15x    1.99x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.083    17.0 | 0.085    16.5 | 0.097    14.5 | 0.076    18.6 | 0.189     7.5 | 1.17x    1.14x     | 0.91x    0.89x          | 2.28x    2.22x         | TRTLLM NVFP4 | 13      | 0/  2/   0.00
32     | 0.114    24.8 | 0.118    23.8 | 0.127    22.1 | 0.106    26.6 | 0.286     9.9 | 1.12x    1.08x     | 0.93x    0.89x          | 2.52x    2.41x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.147    38.5 | 0.151    37.3 | 0.158    35.6 | 0.140    40.3 | 0.387    14.6 | 1.08x    1.05x     | 0.95x    0.93x          | 2.64x    2.56x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.150    75.4 | 0.156    72.1 | 0.164    68.9 | 0.144    78.2 | 0.399    28.3 | 1.09x    1.05x     | 0.96x    0.92x          | 2.67x    2.55x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.158   142.7 | 0.165   136.7 | 0.173   130.0 | 0.154   146.9 | 0.428    52.7 | 1.10x    1.05x     | 0.97x    0.93x          | 2.70x    2.59x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.160   282.0 | 0.169   267.2 | 0.179   251.4 | 0.164   275.1 | 0.435   103.7 | 1.12x    1.06x     | 1.03x    0.97x          | 2.72x    2.58x         | W4A4         | 32      | 7/ 23/  14.00
1024   | 0.165   546.2 | 0.190   475.9 | 0.195   463.0 | 0.296   304.9 | 0.443   203.5 | 1.18x    1.03x     | 1.79x    1.56x          | 2.68x    2.34x         | W4A4         | 32      | 17/ 42/  28.50
2048   | 0.177  1019.1 | 0.233   774.0 | 0.223   810.6 | 0.299   603.0 | 0.477   378.4 | 1.26x    0.95x     | 1.69x    1.28x          | 2.69x    2.05x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.217  1661.4 | 0.363   993.5 | 0.280  1288.5 | 0.309  1168.4 | 0.529   681.8 | 1.29x    0.77x     | 1.42x    0.85x          | 2.44x    1.46x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

**Inference per-token — printed configuration for all three runs:**

```text
DeepSeek-V3 MoE Performance Benchmark
GPU: NVIDIA B300 SXM6 AC
CuteDSL API: Wrapper
Per-token activation: True
Initial activation quantization: True
CuteDSL modes: W4A4 and W4A16; baselines: TRTLLM NVFP4 and TRTLLM BF16
Tensor parallelism simulation: TP=1
CUDA profiler capture: False
CuteDSL finalize: atomic fused
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
DeepSeek-V3 MoE Benchmark: CuteDSL W4A4/W4A16 vs TRTLLM NVFP4 / TRTLLM BF16 (EP=8, TP=1)
Model: hidden=7168, intermediate=2048, experts=256, top_k=8
EP Config: 32 local experts (simulating 8-way parallelism)
TP Config: intermediate size 2048 (simulating 1-way parallelism)
CUDA Graph: enabled, CUPTI: enabled
Routing bias scale: 0.01 (larger values tend to create expert imbalance)
Timed initial activation quantization for FP4-activation backends: included; W4A16 and TRTLLM BF16 consume BF16 directly
CuteDSL finalize: atomic fused
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
CUTLASS omitted: it does not consume the per-token activation scale.
```

<details>
<summary>Inference per-token run 1 — 13 token counts, 4
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.042     2.1 | 0.040     2.2 | 0.034     2.6 | 0.053     1.7 | 0.82x    0.87x          | 1.26x    1.34x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.053     3.3 | 0.046     3.9 | 0.046     3.8 | 0.079     2.2 | 0.87x    1.01x          | 1.49x    1.72x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.072     4.9 | 0.062     5.7 | 0.060     5.9 | 0.116     3.0 | 0.83x    0.97x          | 1.61x    1.87x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.088     8.0 | 0.078     9.0 | 0.074     9.5 | 0.157     4.5 | 0.84x    0.95x          | 1.79x    2.01x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.097    14.6 | 0.084    16.8 | 0.086    16.3 | 0.190     7.4 | 0.89x    1.03x          | 1.97x    2.27x         | W4A16        | 13      | 0/  2/   0.00
32     | 0.132    21.4 | 0.120    23.5 | 0.116    24.3 | 0.287     9.8 | 0.88x    0.97x          | 2.18x    2.39x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.165    34.2 | 0.153    36.8 | 0.148    38.0 | 0.386    14.6 | 0.90x    0.97x          | 2.34x    2.52x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.170    66.5 | 0.157    71.8 | 0.154    73.2 | 0.398    28.3 | 0.91x    0.98x          | 2.34x    2.53x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.178   126.8 | 0.164   137.3 | 0.164   137.9 | 0.427    52.8 | 0.92x    1.00x          | 2.40x    2.60x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.182   247.3 | 0.169   267.6 | 0.174   259.3 | 0.436   103.5 | 0.95x    1.03x          | 2.39x    2.58x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.192   470.5 | 0.190   475.4 | 0.316   285.6 | 0.443   203.8 | 1.65x    1.66x          | 2.31x    2.33x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.213   848.8 | 0.233   774.5 | 0.326   553.7 | 0.477   378.2 | 1.53x    1.40x          | 2.24x    2.05x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.268  1346.3 | 0.362   997.3 | 0.338  1066.3 | 0.529   681.8 | 1.26x    0.94x          | 1.97x    1.46x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Inference per-token run 2 — 13 token counts, 4
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.048     1.8 | 0.039     2.2 | 0.035     2.5 | 0.051     1.7 | 0.73x    0.88x          | 1.06x    1.28x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.053     3.3 | 0.046     3.9 | 0.046     3.8 | 0.079     2.2 | 0.87x    1.01x          | 1.49x    1.73x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.072     4.9 | 0.062     5.7 | 0.060     5.9 | 0.117     3.0 | 0.83x    0.97x          | 1.62x    1.90x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.088     8.0 | 0.078     9.0 | 0.074     9.5 | 0.156     4.5 | 0.84x    0.95x          | 1.78x    2.00x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.097    14.6 | 0.087    16.3 | 0.087    16.3 | 0.190     7.4 | 0.90x    1.00x          | 1.96x    2.19x         | W4A16        | 13      | 0/  2/   0.00
32     | 0.132    21.4 | 0.120    23.5 | 0.116    24.3 | 0.287     9.8 | 0.88x    0.97x          | 2.18x    2.39x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.165    34.2 | 0.153    36.8 | 0.149    37.9 | 0.387    14.6 | 0.90x    0.97x          | 2.34x    2.53x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.170    66.4 | 0.157    71.7 | 0.154    73.1 | 0.398    28.3 | 0.91x    0.98x          | 2.34x    2.53x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.178   126.7 | 0.164   137.2 | 0.164   137.8 | 0.427    52.8 | 0.92x    1.00x          | 2.40x    2.60x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.183   247.1 | 0.169   267.4 | 0.174   259.2 | 0.436   103.5 | 0.95x    1.03x          | 2.39x    2.58x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.191   471.0 | 0.190   475.1 | 0.317   284.7 | 0.442   203.9 | 1.65x    1.67x          | 2.31x    2.33x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.213   848.6 | 0.233   774.4 | 0.326   553.2 | 0.477   378.4 | 1.53x    1.40x          | 2.24x    2.05x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.268  1345.8 | 0.363   994.6 | 0.339  1065.5 | 0.528   683.5 | 1.26x    0.93x          | 1.97x    1.46x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Inference per-token run 3 — 13 token counts, 4
backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.048     1.8 | 0.040     2.2 | 0.034     2.6 | 0.051     1.7 | 0.72x    0.87x          | 1.06x    1.28x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.053     3.3 | 0.046     3.9 | 0.046     3.8 | 0.079     2.2 | 0.87x    1.01x          | 1.49x    1.73x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.072     4.9 | 0.064     5.5 | 0.060     5.9 | 0.116     3.0 | 0.83x    0.94x          | 1.61x    1.83x         | TRTLLM NVFP4 | 7       | 0/  1/   0.00
8      | 0.088     8.0 | 0.078     9.0 | 0.074     9.5 | 0.156     4.5 | 0.84x    0.95x          | 1.78x    2.00x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.097    14.6 | 0.087    16.3 | 0.086    16.4 | 0.190     7.4 | 0.89x    0.99x          | 1.97x    2.20x         | TRTLLM NVFP4 | 13      | 0/  2/   0.00
32     | 0.132    21.4 | 0.120    23.5 | 0.116    24.3 | 0.287     9.8 | 0.88x    0.97x          | 2.18x    2.39x         | TRTLLM NVFP4 | 21      | 0/  3/   1.00
64     | 0.165    34.1 | 0.153    36.8 | 0.149    37.8 | 0.387    14.6 | 0.90x    0.97x          | 2.34x    2.53x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.170    66.4 | 0.157    71.8 | 0.154    73.2 | 0.400    28.2 | 0.91x    0.98x          | 2.36x    2.55x         | TRTLLM NVFP4 | 30      | 0/  8/   3.00
256    | 0.178   126.9 | 0.164   137.2 | 0.163   138.0 | 0.427    52.8 | 0.92x    0.99x          | 2.40x    2.60x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.182   247.7 | 0.168   267.7 | 0.174   258.9 | 0.436   103.4 | 0.96x    1.03x          | 2.39x    2.59x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.192   470.6 | 0.190   475.5 | 0.316   285.5 | 0.443   203.8 | 1.65x    1.67x          | 2.31x    2.33x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.212   848.9 | 0.233   774.4 | 0.326   554.0 | 0.477   378.1 | 1.53x    1.40x          | 2.25x    2.05x         | W4A4         | 32      | 38/ 74/  57.50
4096   | 0.268  1346.0 | 0.362   997.1 | 0.338  1066.0 | 0.529   682.3 | 1.26x    0.94x          | 1.97x    1.46x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

**Deterministic RL — printed configuration for all three runs:**

```text
DeepSeek-V3 MoE Performance Benchmark
GPU: NVIDIA B300 SXM6 AC
CuteDSL API: Wrapper
Per-token activation: True
Initial activation quantization: True
CuteDSL modes: W4A4 and W4A16; baselines: TRTLLM NVFP4 and TRTLLM BF16
Tensor parallelism simulation: TP=1
CUDA profiler capture: False
CuteDSL finalize: deterministic two-stage
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
DeepSeek-V3 MoE Benchmark: CuteDSL W4A4/W4A16 vs TRTLLM NVFP4 / TRTLLM BF16 (EP=8, TP=1)
Model: hidden=7168, intermediate=2048, experts=256, top_k=8
EP Config: 32 local experts (simulating 8-way parallelism)
TP Config: intermediate size 2048 (simulating 1-way parallelism)
CUDA Graph: enabled, CUPTI: enabled
Routing bias scale: 0.01 (larger values tend to create expert imbalance)
Timed initial activation quantization for FP4-activation backends: included; W4A16 and TRTLLM BF16 consume BF16 directly
CuteDSL finalize: deterministic two-stage
TRTLLM NVFP4 / TRTLLM BF16 finalize: native (unaffected by --no-fused-finalize).
CUTLASS omitted: it does not consume the per-token activation scale.
```

<details>
<summary>Deterministic RL run 1 — 13 token counts, 4 backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.048     1.8 | 0.039     2.2 | 0.036     2.5 | 0.051     1.7 | 0.74x    0.91x          | 1.05x    1.29x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.059     3.0 | 0.046     3.8 | 0.047     3.7 | 0.078     2.3 | 0.80x    1.03x          | 1.32x    1.70x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.078     4.5 | 0.061     5.8 | 0.061     5.7 | 0.117     3.0 | 0.79x    1.01x          | 1.51x    1.93x         | W4A16        | 7       | 0/  1/   0.00
8      | 0.093     7.6 | 0.076     9.3 | 0.076     9.3 | 0.157     4.5 | 0.82x    1.00x          | 1.69x    2.07x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.104    13.6 | 0.084    16.9 | 0.087    16.3 | 0.191     7.4 | 0.83x    1.04x          | 1.83x    2.28x         | W4A16        | 13      | 0/  2/   0.00
32     | 0.138    20.4 | 0.117    24.1 | 0.117    24.0 | 0.286     9.9 | 0.85x    1.01x          | 2.07x    2.45x         | W4A16        | 21      | 0/  3/   1.00
64     | 0.175    32.3 | 0.150    37.5 | 0.150    37.5 | 0.386    14.6 | 0.86x    1.00x          | 2.21x    2.57x         | W4A16        | 29      | 0/  5/   2.00
128    | 0.180    62.8 | 0.155    72.9 | 0.156    72.1 | 0.398    28.3 | 0.87x    1.01x          | 2.21x    2.57x         | W4A16        | 30      | 0/  8/   3.00
256    | 0.188   119.6 | 0.167   134.7 | 0.166   136.0 | 0.427    52.8 | 0.88x    0.99x          | 2.26x    2.55x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.194   232.1 | 0.167   270.1 | 0.177   254.2 | 0.435   103.6 | 0.91x    1.06x          | 2.24x    2.61x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.208   433.7 | 0.185   487.7 | 0.319   282.7 | 0.443   203.7 | 1.53x    1.73x          | 2.13x    2.39x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.238   758.6 | 0.224   807.1 | 0.334   540.8 | 0.477   378.0 | 1.40x    1.49x          | 2.01x    2.14x         | W4A16        | 32      | 38/ 74/  57.50
4096   | 0.311  1160.4 | 0.328  1098.6 | 0.350  1030.2 | 0.529   681.9 | 1.13x    1.07x          | 1.70x    1.61x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Deterministic RL run 2 — 13 token counts, 4 backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.048     1.8 | 0.039     2.2 | 0.036     2.5 | 0.053     1.7 | 0.74x    0.91x          | 1.10x    1.35x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.059     3.0 | 0.046     3.8 | 0.047     3.7 | 0.079     2.2 | 0.80x    1.03x          | 1.34x    1.71x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.077     4.5 | 0.060     5.8 | 0.061     5.7 | 0.116     3.0 | 0.79x    1.02x          | 1.50x    1.92x         | W4A16        | 7       | 0/  1/   0.00
8      | 0.093     7.6 | 0.075     9.4 | 0.075     9.4 | 0.160     4.4 | 0.81x    1.00x          | 1.72x    2.13x         | TRTLLM NVFP4 | 10      | 0/  2/   0.00
16     | 0.104    13.5 | 0.083    16.9 | 0.087    16.3 | 0.190     7.4 | 0.83x    1.04x          | 1.83x    2.28x         | W4A16        | 13      | 0/  2/   0.00
32     | 0.138    20.4 | 0.115    24.5 | 0.117    24.1 | 0.287     9.8 | 0.85x    1.02x          | 2.08x    2.49x         | W4A16        | 21      | 0/  3/   1.00
64     | 0.175    32.3 | 0.150    37.5 | 0.150    37.6 | 0.386    14.6 | 0.86x    1.00x          | 2.21x    2.57x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.180    62.8 | 0.153    73.5 | 0.156    72.1 | 0.400    28.2 | 0.87x    1.02x          | 2.23x    2.61x         | W4A16        | 30      | 0/  8/   3.00
256    | 0.189   119.6 | 0.167   134.7 | 0.165   136.3 | 0.427    52.8 | 0.88x    0.99x          | 2.26x    2.55x         | TRTLLM NVFP4 | 32      | 1/ 11/   7.00
512    | 0.194   232.2 | 0.167   270.2 | 0.177   254.4 | 0.436   103.5 | 0.91x    1.06x          | 2.24x    2.61x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.208   433.7 | 0.185   487.9 | 0.320   282.2 | 0.443   203.5 | 1.54x    1.73x          | 2.13x    2.40x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.238   759.1 | 0.224   807.1 | 0.333   542.0 | 0.477   378.2 | 1.40x    1.49x          | 2.01x    2.13x         | W4A16        | 32      | 38/ 74/  57.50
4096   | 0.311  1160.6 | 0.328  1098.4 | 0.350  1029.4 | 0.528   682.8 | 1.13x    1.07x          | 1.70x    1.61x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

<details>
<summary>Deterministic RL run 3 — 13 token counts, 4 backends</summary>

```text
Tokens | CuteDSL W4A4  | CuteDSL W4A16 | TRTLLM NVFP4  | TRTLLM BF16   | Speedup vs TRTLLM NVFP4 | Speedup vs TRTLLM BF16 | Winner       | Active  | Stats
       | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | ms  TFLOPS    | W4A4     W4A16          | W4A4     W4A16         |              | experts | min/max/median
1      | 0.048     1.8 | 0.040     2.2 | 0.036     2.4 | 0.053     1.7 | 0.75x    0.90x          | 1.09x    1.31x         | TRTLLM NVFP4 | 2       | 0/  1/   0.00
2      | 0.059     3.0 | 0.046     3.8 | 0.047     3.7 | 0.079     2.2 | 0.81x    1.03x          | 1.34x    1.71x         | W4A16        | 4       | 0/  1/   0.00
4      | 0.077     4.6 | 0.060     5.8 | 0.061     5.7 | 0.117     3.0 | 0.79x    1.01x          | 1.51x    1.93x         | W4A16        | 7       | 0/  1/   0.00
8      | 0.093     7.6 | 0.075     9.4 | 0.075     9.4 | 0.157     4.5 | 0.81x    1.00x          | 1.68x    2.09x         | W4A16        | 10      | 0/  2/   0.00
16     | 0.104    13.6 | 0.083    16.9 | 0.087    16.3 | 0.190     7.4 | 0.84x    1.04x          | 1.83x    2.28x         | W4A16        | 13      | 0/  2/   0.00
32     | 0.139    20.3 | 0.117    24.1 | 0.117    24.1 | 0.287     9.8 | 0.84x    1.00x          | 2.07x    2.46x         | W4A16        | 21      | 0/  3/   1.00
64     | 0.175    32.3 | 0.152    37.0 | 0.150    37.5 | 0.386    14.6 | 0.86x    0.99x          | 2.21x    2.54x         | TRTLLM NVFP4 | 29      | 0/  5/   2.00
128    | 0.180    62.8 | 0.155    72.8 | 0.156    72.2 | 0.398    28.4 | 0.87x    1.01x          | 2.21x    2.57x         | W4A16        | 30      | 0/  8/   3.00
256    | 0.189   119.5 | 0.162   139.1 | 0.166   136.0 | 0.427    52.8 | 0.88x    1.02x          | 2.26x    2.63x         | W4A16        | 32      | 1/ 11/   7.00
512    | 0.194   232.3 | 0.167   270.1 | 0.177   254.3 | 0.436   103.3 | 0.91x    1.06x          | 2.25x    2.61x         | W4A16        | 32      | 7/ 23/  14.00
1024   | 0.208   433.5 | 0.185   487.5 | 0.322   280.3 | 0.443   203.4 | 1.55x    1.74x          | 2.13x    2.40x         | W4A16        | 32      | 17/ 42/  28.50
2048   | 0.238   759.5 | 0.223   807.2 | 0.333   542.3 | 0.477   378.1 | 1.40x    1.49x          | 2.01x    2.14x         | W4A16        | 32      | 38/ 74/  57.50
4096   | 0.311  1159.4 | 0.329  1097.9 | 0.351  1029.3 | 0.528   683.4 | 1.13x    1.07x          | 1.70x    1.61x         | W4A4         | 32      | 81/147/ 117.00
Speedup > 1.0 means that CuTe DSL mode is faster than the comparison backend
```

</details>

### Derived performance summary

Latencies are **medians of three fresh-process runs**, calculated from
unrounded captures and displayed in milliseconds to three decimal
places. Each **W4A16 speedup** is the named TRTLLM baseline's median
latency divided by the CuTe DSL W4A16 median latency at that token
count. These are ratios of medians; values above 1 mean W4A16 is faster;
values below 1 mean W4A16 is slower. Both NVFP4 and pure BF16
comparisons are explicit.

**Inference per-tensor — median of three runs**

| Tokens | CuTe W4A4 (ms) | CuTe W4A16 (ms) | CUTLASS NVFP4 (ms) |
TRTLLM NVFP4 (ms) | TRTLLM BF16 (ms) | W4A16 speedup over TRTLLM NVFP4 |
W4A16 speedup over TRTLLM BF16 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 0.031 | 0.040 | 0.048 | 0.026 | 0.051 | 0.65x | 1.29x |
| 2 | 0.040 | 0.046 | 0.058 | 0.036 | 0.079 | 0.79x | 1.72x |
| 4 | 0.057 | 0.063 | 0.070 | 0.051 | 0.117 | 0.81x | 1.85x |
| 8 | 0.073 | 0.079 | 0.086 | 0.064 | 0.157 | 0.81x | 1.99x |
| 16 | 0.083 | 0.085 | 0.097 | 0.076 | 0.192 | 0.89x | 2.25x |
| 32 | 0.114 | 0.118 | 0.127 | 0.106 | 0.285 | 0.89x | 2.41x |
| 64 | 0.147 | 0.151 | 0.159 | 0.140 | 0.388 | 0.92x | 2.56x |
| 128 | 0.150 | 0.158 | 0.164 | 0.144 | 0.399 | 0.91x | 2.53x |
| 256 | 0.158 | 0.164 | 0.173 | 0.154 | 0.428 | 0.93x | 2.60x |
| 512 | 0.160 | 0.169 | 0.179 | 0.164 | 0.435 | 0.97x | 2.58x |
| 1024 | 0.165 | 0.190 | 0.197 | 0.295 | 0.443 | 1.56x | 2.34x |
| 2048 | 0.177 | 0.233 | 0.223 | 0.299 | 0.476 | 1.28x | 2.04x |
| 4096 | 0.217 | 0.363 | 0.281 | 0.309 | 0.529 | 0.85x | 1.46x |

**Inference per-token — median of three runs**

| Tokens | CuTe W4A4 (ms) | CuTe W4A16 (ms) | TRTLLM NVFP4 (ms) | TRTLLM
BF16 (ms) | W4A16 speedup over TRTLLM NVFP4 | W4A16 speedup over TRTLLM
BF16 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 0.048 | 0.040 | 0.034 | 0.051 | 0.87x | 1.28x |
| 2 | 0.053 | 0.046 | 0.046 | 0.079 | 1.01x | 1.73x |
| 4 | 0.072 | 0.062 | 0.060 | 0.116 | 0.97x | 1.88x |
| 8 | 0.088 | 0.078 | 0.074 | 0.156 | 0.95x | 2.00x |
| 16 | 0.097 | 0.087 | 0.086 | 0.190 | 1.00x | 2.20x |
| 32 | 0.132 | 0.120 | 0.116 | 0.287 | 0.97x | 2.39x |
| 64 | 0.165 | 0.153 | 0.149 | 0.387 | 0.97x | 2.52x |
| 128 | 0.170 | 0.157 | 0.154 | 0.398 | 0.98x | 2.53x |
| 256 | 0.178 | 0.164 | 0.164 | 0.427 | 1.00x | 2.60x |
| 512 | 0.182 | 0.169 | 0.174 | 0.436 | 1.03x | 2.58x |
| 1024 | 0.192 | 0.190 | 0.316 | 0.443 | 1.66x | 2.33x |
| 2048 | 0.213 | 0.233 | 0.326 | 0.477 | 1.40x | 2.05x |
| 4096 | 0.268 | 0.362 | 0.338 | 0.529 | 0.94x | 1.46x |

**Deterministic RL — median of three runs**

| Tokens | CuTe W4A4 (ms) | CuTe W4A16 (ms) | TRTLLM NVFP4 (ms) | TRTLLM
BF16 (ms) | W4A16 speedup over TRTLLM NVFP4 | W4A16 speedup over TRTLLM
BF16 |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 0.048 | 0.039 | 0.036 | 0.053 | 0.91x | 1.34x |
| 2 | 0.059 | 0.046 | 0.047 | 0.079 | 1.03x | 1.71x |
| 4 | 0.077 | 0.060 | 0.061 | 0.117 | 1.01x | 1.93x |
| 8 | 0.093 | 0.075 | 0.075 | 0.157 | 1.00x | 2.09x |
| 16 | 0.104 | 0.083 | 0.087 | 0.190 | 1.04x | 2.28x |
| 32 | 0.138 | 0.117 | 0.117 | 0.287 | 1.00x | 2.46x |
| 64 | 0.175 | 0.150 | 0.150 | 0.386 | 1.00x | 2.57x |
| 128 | 0.180 | 0.155 | 0.156 | 0.398 | 1.01x | 2.57x |
| 256 | 0.189 | 0.167 | 0.166 | 0.427 | 0.99x | 2.55x |
| 512 | 0.194 | 0.167 | 0.177 | 0.436 | 1.06x | 2.61x |
| 1024 | 0.208 | 0.185 | 0.320 | 0.443 | 1.73x | 2.40x |
| 2048 | 0.238 | 0.224 | 0.333 | 0.477 | 1.49x | 2.13x |
| 4096 | 0.311 | 0.328 | 0.350 | 0.528 | 1.07x | 1.61x |

- **Inference per-tensor:** W4A16 speedup 0.65–1.56x over TRTLLM NVFP4
(2/13 faster); 1.29–2.60x over TRTLLM BF16 (13/13 faster).
- **Inference per-token:** W4A16 speedup 0.87–1.66x over TRTLLM NVFP4
(4/13 faster); 1.28–2.60x over TRTLLM BF16 (13/13 faster).
- **Deterministic RL:** W4A16 speedup 0.91–1.73x over TRTLLM NVFP4 (9/13
faster); 1.34–2.61x over TRTLLM BF16 (13/13 faster).

### BF16 performance investigation

**Finding:** the W4A16 advantage is present in GPU expert computation.
TRTLLM BF16 tuning is active; exhaustive native-tactic checks on the
actual inputs do not close the gap. Preparation, tuning, L2 flushing and
host dispatch are outside the reported CUPTI GPU span. Independent
single-call graph events reproduce the ordering. These diagnostics
supplement the unchanged nine sweeps.

**Provenance:** profiles, actual-input tactic sweep and event controls
use `2079fa00c4a2a0fb2e95bb284978a703653a4830` on the same retained
B300/CUDA 13.2 image above. Nsight Systems 2026.2.1, GPU 0; tactic
diagnostics GPU 1, serialized with GPU 0 work. Initial cache/default
audit uses `a3fce87d5beec29775e9bc3917df99ba6bc4db9c`. Naming commit
`d0caa842` and profiling-only commit `2079fa00` are separate; normal
benchmark functions/timing remain unchanged from the refactor validation
source.

**Autotuning:** 2,852 successful native candidate profiles across 21
token buckets, zero failures; all ten measured warmup/capture dispatches
used nonfallback cache hits with tuning disabled. The selected tactic
reaches the native launcher. At 32 tokens, all 352 actual-input
candidates give a best 284.5635 µs versus 287.3155 µs for the selected
baseline (about 1%, single sweep). At 4096, the selected `(128,0)` is
also the exhaustive eight-candidate winner at 529.3520 µs. Default `-1`
is ~15% slower there. The v1 tuner's synthetic routing activates 11/30
local experts at 32/4096, versus 21/32 on actual inputs; shorter
synthetic probe times therefore are not the final benchmark latency. The
exhaustive actual-input sweep checks this selection concern directly.

TRTLLM BF16 tuned/default controls (µs; each cell is a 100-iteration
median; 3 alternating pairs):

```csv
tokens,tuned_tactic,repeat,tuned_us,default_us
32,8:92,1,286.9315,287.1400
32,8:92,2,287.1560,287.0915
32,8:92,3,287.0440,287.0440
4096,128:0,1,528.9665,609.1280
4096,128:0,2,530.0870,610.4075
4096,128:0,3,531.5110,611.6720
```

All actual-input native candidates (median of 100 iterations, µs; one
sample each). Each CSV row lists latencies in ascending contiguous
config-ID order; `(tileN, config)` is the native tactic. This includes
every 352/8 enumerated candidate plus default.

```text
tokens=32; default(-1)=286.8350
tile=8; config=0..143
295.8595,286.0840,297.8440,285.7475,299.2360,285.5240,295.9080,297.4760,286.0515,299.2035,286.1795,285.4120,297.0920,287.0435,298.6920,286.5315,300.6760,286.2120,296.9640,298.5000,286.8360,300.1955,286.5155,286.3720,295.2840,285.3795,296.8685,285.3000,299.1075,284.6115,295.2520,296.9475,285.4115,299.1080,284.8520,284.5635,296.2920,286.4840,298.1160,286.3075,300.0350,285.9240,296.1640,298.5960,286.8840,300.0355,286.2435,285.6995,297.1560,286.8360,298.8200,286.7560,300.6760,286.3080,296.5795,298.5475,286.8035,300.8355,286.7235,286.1800,296.7555,286.9640,298.3240,287.0435,300.3080,286.3885,296.9475,297.9720,287.0115,300.1160,286.6915,286.4990,296.2600,285.9395,297.4600,285.8280,299.6360,285.6360,295.9720,297.3800,286.1155,299.5075,285.6360,285.3955,297.2680,287.2360,298.4360,286.8200,300.6600,286.3555,297.1070,298.7720,286.9630,301.0115,286.7235,286.4840,295.3160,285.2355,296.7560,285.2200,299.2040,284.9795,295.3315,296.9640,285.4600,299.2995,285.0440,284.5800,296.3880,286.6440,297.8755,286.3395,299.7320,285.7800,296.1955,297.9715,287.1240,300.1160,286.1960,285.9715,297.1395,287.0595,299.0280,286.9150,300.9635,286.3720,297.1560,298.4520,286.9155,300.9960,286.6755,286.5800,296.9000,287.0920,298.2125,287.1080,300.1795,286.5635,296.5800,298.5800,287.0280,300.3085,286.8520,286.2920
tile=16; config=0..143
292.6915,294.5480,285.8280,296.8680,285.6355,285.1880,292.8355,285.6040,294.7075,296.8840,285.6200,285.3160,293.3160,295.2365,286.3875,297.7965,286.3235,286.0680,293.0440,286.6600,295.0760,297.4760,286.4200,286.2920,291.9400,293.9885,285.0910,296.1645,285.0600,284.7080,292.0835,284.9640,293.8280,296.4360,285.1070,284.7230,292.6760,294.9800,285.9240,297.1880,286.2595,285.3320,292.7240,285.9880,294.7080,296.8680,286.0040,285.5075,293.7630,295.8605,287.0440,298.0835,287.0920,286.5960,293.5720,286.7880,295.6520,297.4760,287.0120,286.1800,293.2840,295.4600,286.8670,297.9560,286.6115,286.2115,293.0435,286.3720,295.3805,297.2840,286.9325,286.0675,292.2435,294.4520,285.6040,296.4360,285.8760,285.1560,292.7245,285.5240,294.7560,296.9000,285.7320,285.3005,293.2845,295.3000,286.3245,297.5245,286.4360,286.5000,293.1080,286.4680,295.2520,297.5875,286.7240,286.1480,291.8760,294.1960,285.1080,296.0360,284.9640,284.8200,291.6040,285.1235,294.0360,296.2920,285.3160,284.7555,292.6440,294.8200,285.8920,296.9640,286.0520,285.1880,292.7560,285.9550,294.5955,297.2520,286.0840,285.7315,293.7000,295.8920,286.8520,298.2760,286.9000,286.9320,293.7320,286.8520,295.3640,297.7485,287.1720,286.6755,293.3965,295.4440,286.3725,297.3800,286.9160,286.1795,293.5725,286.5480,295.1400,297.5710,286.5950,286.2915
tile=32; config=0..63
292.4360,286.0520,295.0600,285.7955,292.2285,295.1080,285.5555,286.2440,294.3400,287.7800,297.5880,287.7320,294.1960,297.2200,287.8120,287.8920,293.0760,286.9160,296.5960,286.7720,292.8675,296.4680,286.8035,286.7240,293.6680,287.7165,297.1715,287.5720,293.5565,296.9160,287.6040,287.4920,292.1795,286.2110,295.2680,285.7475,292.1635,295.4600,286.0200,286.0675,294.1480,288.0195,297.5405,287.7955,294.1480,297.2200,287.6845,288.0680,293.2840,286.9160,296.1320,286.7075,293.0920,296.3240,286.9320,286.9800,293.8600,287.7960,296.7075,287.4290,293.5720,296.9160,287.3000,287.6835
tokens=4096; default(-1)=609.7365
tile=64; config=0..3
611.4960,611.9765,610.2970,611.5760
tile=128; config=0..3
529.3520,529.5590,530.8710,530.3430
```

**Nsight Systems complete device breakdown (µs):** 20 cold-L2, one-call
graph replays per case after tuning and three uncaptured replays. Every
non-dash activity cell is the mean of 20 instances; both temporary-zero
kernels are shown separately. All target kernels/memsets are accounted
for inside synchronized `moe` NVTX ranges; each contains one
`cudaGraphLaunch`. The 20 separately labeled L2 flushes are excluded.
Kernel sums are diagnostic, not latency: [programmatic dependent
launch](https://docs.nvidia.com/cuda/cuda-programming-guide/04-special-topics/programmatic-dependent-launch.html)
allows dependent kernel intervals to overlap. GPU span measures the
first activity start through last activity end; uncovered gaps use the
union of intervals. Inference profiles cover both inference activation
variants because those flags do not change W4A16 or TRTLLM BF16; RL is
separately profiled.

**Inference:**

| Activity / metric | CuTe W4A16 / 32 | TRTLLM BF16 / 32 | CuTe W4A16 /
4096 | TRTLLM BF16 / 4096 |
| --- | ---: | ---: | ---: | ---: |
| Top-k routing | 3.150 | 3.346 | 9.635 | 9.214 |
| Temporary zero 1 | 0.587 | — | 0.672 | — |
| Temporary zero 2 | 0.628 | — | 0.702 | — |
| Route map | 3.709 | 3.171 | 6.832 | 6.339 |
| BF16 permute | 4.648 | — | 22.986 | — |
| GEMM1 + SwiGLU | 67.812 | 189.739 | 164.956 | 331.377 |
| Output zero | 0.906 | — | 9.722 | — |
| GEMM2 | 36.946 | 89.677 | 147.033 | 150.361 |
| Finalize | — | 5.779 | — | 38.018 |
| GPU activity sum | 118.386 | 291.712 | 362.538 | 535.309 |
| GPU span | 118.522 | 285.562 | 359.142 | 527.871 |
| Uncovered GPU gaps | 0.668 | 0.000 | 0.644 | 0.000 |
| Graph launch CPU API (excluded) | 9.867 | 8.062 | 7.405 | 8.048 |
| L2 flush (excluded) | 67.826 | 67.925 | 67.882 | 67.810 |

**Deterministic RL:**

| Activity / metric | CuTe W4A16 / 32 | TRTLLM BF16 / 32 | CuTe W4A16 /
4096 | TRTLLM BF16 / 4096 |
| --- | ---: | ---: | ---: | ---: |
| Top-k routing | 3.094 | 3.283 | 9.622 | 9.283 |
| Temporary zero 1 | 0.592 | — | 0.677 | — |
| Temporary zero 2 | 0.590 | — | 0.694 | — |
| Route map | 3.578 | 3.014 | 7.237 | 6.586 |
| BF16 permute | 4.526 | — | 23.088 | — |
| GEMM1 + SwiGLU | 68.505 | 188.811 | 165.900 | 331.810 |
| Output zero | — | — | — | — |
| GEMM2 | 43.343 | 89.194 | 110.439 | 150.190 |
| Finalize | 5.880 | 5.755 | 31.789 | 38.095 |
| GPU activity sum | 130.108 | 290.058 | 349.446 | 535.964 |
| GPU span | 114.262 | 284.682 | 326.137 | 528.484 |
| Uncovered GPU gaps | 0.365 | 0.000 | 0.329 | 0.000 |
| Graph launch CPU API (excluded) | 7.163 | 6.141 | 10.132 | 8.223 |
| L2 flush (excluded) | 67.928 | 67.817 | 67.880 | 67.842 |

Kernel mapping: top-k=`deepseek_v3_topk_kernel` / `routingMainKernel`;
route map=`routingIndicesClusterKernel` / `routingIndicesCoopKernel`;
temporary zeros=`vectorized_elementwise_kernel`;
permute/unpermute=`moePermuteKernel` / `moeUnpermuteKernel`; CuTe
GEMMs=`Sm100W4A16GroupedGemmKernel` in launch order; TRTLLM BF16
GEMMs=`bmm_Bfloat16_Bfloat16Bfloat16...` (FC1 has `swiGlu`); native
finalize=`finalizeKernel` / `finalizeKernelVecLoad`. CuTe inference
GEMM2 includes atomic finalize; RL uses the separate unpermute row. At
32 tokens both GEMMs explain the gap; at 4096 the largest difference is
GEMM1, with native finalize also contributing. TRTLLM BF16 has no
uncovered device gaps in these traces.

**Independent timer control:** same tuned callable, one call per graph,
100 samples after 10 warmups; zero a 2×L2 byte buffer and synchronize
before each start event, then `start.record(); graph.replay();
end.record(); end.synchronize()`. CUPTI separately measures the same
prepared callable. Every case passed with finite outputs. Table contains
every case's median in µs. Event intervals add roughly 4–6 µs but retain
the gap; host submission cannot explain the BF16 slowdown. Warm-cache
results are sequential diagnostics, not an isolated cache speedup claim.
Ordinary `--no-cupti` is not this control: it uses ten-call graphs and
rotates only input kwargs, leaving closure-held weights unrotated.

| Config | Tokens | Backend | Cold CUPTI | Cold events | Warm events |
| --- | ---: | --- | ---: | ---: | ---: |
| inference | 1 | CuTe W4A16 | 38.9440 | 42.9440 | 39.8240 |
| inference | 1 | TRTLLM BF16 | 50.7525 | 56.8640 | 46.5280 |
| inference | 32 | CuTe W4A16 | 118.9450 | 124.4480 | 113.4080 |
| inference | 32 | TRTLLM BF16 | 286.0665 | 292.3360 | 276.1920 |
| inference | 4096 | CuTe W4A16 | 361.9550 | 366.7200 | 378.1440 |
| inference | 4096 | TRTLLM BF16 | 528.9640 | 533.6480 | 543.2800 |
| rl | 1 | CuTe W4A16 | 40.1280 | 45.8080 | 42.1760 |
| rl | 1 | TRTLLM BF16 | 53.0885 | 58.8960 | 48.0480 |
| rl | 32 | CuTe W4A16 | 115.0410 | 120.3360 | 112.3520 |
| rl | 32 | TRTLLM BF16 | 286.5785 | 292.5920 | 276.2240 |
| rl | 4096 | CuTe W4A16 | 327.4590 | 333.0560 | 355.2640 |
| rl | 4096 | TRTLLM BF16 | 528.6275 | 533.4560 | 542.9120 |

### Nsight Compute: fixed normal-tuned tactics

- **Scope:** inference per-token, EP8/TP1, B300 GPU 0, NCU 2026.1.1,
source `2079fa00`. Tactics were recorded during normal tuning before NCU
injection, then fixed by a diagnostic helper; all captured calls had
tuning disabled. Each report contains exactly FC1 (with SwiGLU) and FC2,
nine replay passes each. Node replay flushes caches and isolates PDL
kernels: these durations are diagnostics, not additive end-to-end
latency.
- **Tactics:** TRTLLM BF16: `(8, 37)` at 32; `(128, 1)` at 4096. CuteDSL
W4A16 uses the same tactic for both GEMMs: `((128, 8, 256), (2, 1),
True)` at 32; `((256, 128, 256), (2, 1), True)` at 4096.

Raw counters below: R/W = DRAM bytes; D/T/S = DRAM throughput /
tensor-pipe activity / SM throughput (% of sustained elapsed peak);
LD/ST = local-memory sectors; warps = active warps per active SM cycle;
A/T = achieved/theoretical occupancy (%).

| Tokens | Backend | GEMM | R bytes | W bytes | ns | D/T/S % | LD/ST |
Warps | Occupancy A/T % | Registers/thread | Shared bytes/block |
| ---: | --- | --- | ---: | ---: | ---: | --- | --- | ---: | --- | ---:
| ---: |
| 32 | TRTLLM BF16 | FC1 | 1233656832 | 3507200 | 176896 |
91.17/2.42/25.37 | 0/0 | 11.33 | 17.70/18.75 | 168 | 181904 |
| 32 | TRTLLM BF16 | FC2 | 616784896 | 4100096 | 93760 |
86.35/2.27/23.87 | 0/0 | 7.95 | 12.42/12.50 | 255 | 216720 |
| 4096 | TRTLLM BF16 | FC1 | 2064285184 | 17972224 | 323040 |
84.03/40.83/45.78 | 0/0 | 10.84 | 16.94/18.75 | 168 | 187032 |
| 4096 | TRTLLM BF16 | FC2 | 960271104 | 50072064 | 152864 |
86.17/44.00/48.40 | 0/0 | 6.98 | 10.91/12.50 | 255 | 219800 |
| 32 | CuteDSL W4A16 | FC1 | 349258752 | 3499264 | 65632 |
70.11/6.61/53.35 | 0/0 | 15.86 | 24.77/25.00 | 128 | 215040 |
| 32 | CuteDSL W4A16 | FC2 | 174409728 | 3022592 | 37504 |
61.78/5.74/49.50 | 0/0 | 15.61 | 24.39/25.00 | 128 | 206880 |
| 4096 | CuteDSL W4A16 | FC1 | 637545728 | 13989120 | 165696 |
51.26/87.20/87.81 | 0/0 | 15.84 | 24.75/25.00 | 128 | 223232 |
| 4096 | CuteDSL W4A16 | FC2 | 322100992 | 7225344 | 148096 |
28.99/44.90/46.44 | 0/0 | 15.06 | 23.53/25.00 | 128 | 215168 |

Remaining launch counters (all eight kernels): occupancy limits = 32
blocks, 1 block by registers, 1 by shared memory; warp limit = 5/8
blocks for BF16 FC1/FC2 and 4 for W4A16. Cluster dimensions = `(2,1,1)`,
except BF16 at 32 uses `(1,1,1)`. `occupancy_cluster_pct` = 3.12%;
`occupancy_cluster_gpu_pct` = 0.59/0.39% for BF16 FC1/FC2 and 0.78% for
both W4A16 kernels (launch estimates, not measured GPU activity). Full
raw CSV/report metadata is retained.

**Interpretation:** at 4096, BF16 still reaches 84–86% DRAM throughput
with 41–44% tensor activity; W4A16 FC1 reaches 87% tensor activity. BF16
reads 3.025 GB versus W4A16's 0.960 GB. EP8 leaves 3715 local
assignments across 32 experts (116/expert); 4096 is not each expert's
GEMM M. No local load/store traffic was measured in any kernel.
Registers and shared memory both limit residency to one block/SM; low
occupancy alone does not establish an avoidable defect. These counters
support a bandwidth explanation and do not demonstrate a spilling or
launch-overhead bug.

Public CLI equivalent on `2079fa00`: TRTLLM BF16 at 32 passed normal
cache save then fresh-process `--no-autotune` load (both exit 0, target
cache hit, no retuning, unchanged cache hash). The measured counters
above used the helper-frozen tactics, not this smoke cache. Run in the
same inference environment with NVFP4 overrides unset. Require a
target-operation `Config cache hit`; missing/incompatible caches can
otherwise fall back.

```bash
export CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 MAX_JOBS=8 FLASHINFER_LOGGING_LEVEL=info
m=(dram__bytes_{read,write}.sum {dram__throughput,sm__throughput,sm__pipe_tensor_cycles_active}.avg.pct_of_peak_sustained_elapsed gpu__time_duration.sum l1tex__t_sectors_pipe_lsu_mem_local_op_{ld,st}.sum sm__warps_active.avg.{per_cycle_active,pct_of_peak_sustained_active} sm__maximum_warps_per_active_cycle_pct launch__{registers_per_thread,shared_mem_per_block,occupancy_limit_{blocks,registers,shared_mem,warps},cluster_dim_{x,y,z},occupancy_cluster_pct,occupancy_cluster_gpu_pct})
for n in 32 4096; do
  for b in cute-dsl-w4a16 trtllm-bf16; do
    a=(benchmarks/bench_moe_deepseek.py --num-tokens "$n" --ep 8 --tp 1 --routing-input-mode logits --use-per-token-activation --include-activation-quant --profile-cuda --profile-backend "$b" --profile-iters 1 --cache "$b-$n.json")
    python "${a[@]}"
    test -s "$b-$n.json" || exit 1
    ncu --profile-from-start off --replay-mode kernel --graph-profiling node --nvtx --nvtx-include moe/ --kernel-name-base demangled --rename-kernels off --kernel-name 'regex:.*(Sm100W4A16GroupedGemmKernel|bmm_Bfloat16_Bfloat16Bfloat16_).*' --launch-count 2 --cache-control all --clock-control none --metrics "$(IFS=,; echo "${m[*]}")" --csv --page raw --print-units base --export "$b-$n" python "${a[@]}" --no-autotune
  done
done
```

**Why 4096 remains bandwidth-sensitive:** the actual EP8 routing has
3715/32 = 116.09 rows per expert. Useful BF16 GEMM FLOPs divided by
unique weight bytes give 116.09 FLOP/byte; including minimum activation
traffic gives about 108–112. The advertised dense BF16 rate is 36
PFLOPS/node ÷ 2 ÷ 8 = 2.25 PFLOPS/GPU ([NVIDIA HGX
specifications](https://www.nvidia.com/en-us/data-center/hgx/)); with [8
TB/s
HBM](https://docs.nvidia.com/enterprise-reference-architectures/hgx-ai-factory/latest/components.html),
the ideal crossover is about 281 FLOP/byte. These are analytical peak
bounds, supported here by the measured DRAM counters. Tile128 pads to 40
tiles/5120 slots (72.56% useful rows). The 3.025 GB measured BF16 reads
are close to 2.819 GB unique weights and below 3.523 GB if every token
tile reread them. Compression moves W4A16 GEMM1 toward compute
saturation; equal tensor-core input precision does not give equal memory
traffic.

**Reproduce the eight Nsight traces** from the implementation checkout
and image above. Output files remain on the retained devbox; no
compilation caches are removed.

```bash
git checkout 2079fa00c4a2a0fb2e95bb284978a703653a4830
export CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 MAX_JOBS=8
for mode in inference rl; do
  unset FLASHINFER_NVFP4_4OVER6 FLASHINFER_NVFP4_4OVER6_E4M3_USE_256
  unset FLASHINFER_NVFP4_4OVER6_ERR_MODE FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH
  unset FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH
  extra=()
  if [[ $mode == rl ]]; then
    export FLASHINFER_NVFP4_4OVER6=1 FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1
    export FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=1
    export FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1
    extra=(--no-fused-finalize)
  fi
  for n in 32 4096; do
    for backend in cute-dsl-w4a16 trtllm-bf16; do
      nsys profile --sample=none --cpuctxsw=none --trace=cuda,nvtx \
        --cuda-graph-trace=node --capture-range=cudaProfilerApi \
        --capture-range-end=stop -o "$mode-$backend-t$n" \
        python3 benchmarks/bench_moe_deepseek.py --num-tokens "$n" --ep 8 \
        --warmup 10 --iters 100 --use-per-token-activation --include-activation-quant \
        --profile-cuda --profile-backend "$backend" --profile-iters 20 "${extra[@]}"
      nsys export --type=sqlite -o "$mode-$backend-t$n.sqlite" "$mode-$backend-t$n.nsys-rep"
    done
  done
done
```

Aggregate all GPU activities contained by each synchronized `moe` NVTX
range, including target memsets; verify 20 ranges and one graph launch
per range. Report per-kernel `sum(end-start)/20`, per-range GPU
`max(end)-min(start)`, and CPU graph-launch duration separately. Exclude
`l2_flush`; do not sum kernel durations as wall-clock latency. These are
single-GPU local-expert diagnostics, not distributed or full-model
speedups.

### Interpretation and limits

- Single-GPU EP8 shard shapes: no dispatch/combine, all-gather,
all-reduce, network or full-model runtime is timed.
- Both TRTLLM arms use native finalize in every configuration. Native
logits routing stores selected weights in BF16; CuTe route weights are
FP32. This is not a numerical-parity claim between BF16/quantized paths
or proof of RL-training determinism.
- New per-tensor runs also remeasure the unaffected W4A16/BF16 paths.
Differences across separate sweeps are not attributed solely to
activation scaling. Coverage is B300/SM103 and the stated shapes; other
architectures and distributed execution were not tested.

## 🔍 Related Issues

Related implementation and benchmark configurations: #4048.

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

- **Original measured source:** seven existing BF16 GPU tests passed
(310 deselected); eight independent reference cases passed with
unchanged `rtol=atol=0.03`, three exact eager repeats and three exact
CUDA-graph replays per case. BF16 CLI/profiler smoke passed. [Complete
original test output, helper and
commands](https://github.com/flashinfer-ai/flashinfer/pull/4985#issuecomment-5549485234).
- **Shared-helper refactor `a3fce87d`:** 43 paired GPU cases matched
measured source `1ac2233d` for public entry points, bound kernel
arguments, finalized output bytes and timing inputs; renamed selectors
and NVFP4 profiler smoke passed; an excluded profiling backend is
rejected with exit 2. Autotuning was disabled for these bounded
equivalence checks. [Complete refactor validation and
reproduction](https://github.com/flashinfer-ai/flashinfer/pull/4985#issuecomment-5549433238).
- **Later head `2079fa00`:** printed-name fixtures and external-profiler
NVTX ranges are validated separately; the five benchmark functions and
non-profile timing branch remain AST-identical to the 43-case refactor
source. Those 43 cases are attributed to the refactor commit above.
- **Static scope:** file-scoped pre-commit hooks, Ruff, formatting,
Python compilation and `git diff --check` passed. Mypy is skipped by the
configured hook because this benchmark is outside its `flashinfer/`
scope. No upstream test files were changed; all-files hooks and the full
repository test suite were not run. These correctness checks do not
replace the nine performance sweeps.

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

Please review the precision-specific TRTLLM weight/scale arguments,
shared routing and timing boundary, explicit backend/finalize labels,
and the three configuration definitions. All nine raw tables and both
W4A16 baseline speedup columns are above; complete validation output is
linked in Tests. Unchecked all-files/full-suite items reflect the stated
scope.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Unified TensorRT-LLM benchmarking for NVFP4 and BF16 precision modes.
  * Added support for logits and pre-routed execution scenarios.
* Added the `trtllm-bf16` backend to benchmark selection, validation,
tables, speedup reporting, and command-line help.
* Improved consistency for routed workload comparisons across
TensorRT-LLM precision modes.

* **Bug Fixes**
* Profile-backend selection now rejects values not included in the
selected backend list.
* Benchmark status and winner labels now clearly distinguish NVFP4 and
BF16 results.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e184c74](https://github.com/flashinfer-ai/flashinfer/commit/e184c741f48c084d2d7c5f7f4b83e077af3f805e)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-10T19:19:29Z
- **提交信息**: refactor(kda): stop 0.7 advertising unreleased KDA surface (mark prefill wrapper experimental, trim kda_kernels.__all__) (#5040)

## 📌 Description

Stops `0.7` from advertising KDA surface that has never shipped and that
the unification plan expects to change. No kernel logic, no behaviour
change on any released path.

- `RecurrentKDAPrefillWrapper.plan` / `.run` get
`@flashinfer_experimental_api`, and the planning implementation moves to
`flashinfer/experimental/kda_prefill_wrapper/`. The class keeps its
signatures and docstrings in `flashinfer/kda.py` as the thin entry
point, reaching the planner through a function-local import, so core
never imports `flashinfer.experimental` at module level. Removal is a
one-directory deletion plus the thin class. Same shape as
`sm110_gqa_decode`.
- The three `*_kda_prefill_sm120` names leave `kda_kernels.__all__`,
which is now byte-identical to `v0.6.18`'s. They are dispatch plumbing
for `flashinfer.kda_prefill`, and they are bound to `None` on any
install where the SM120a module fails its optional import, so they were
never fit to be public exports. Removing a name from `__all__` leaves
the attribute in place and every consumer already reaches them by
attribute or through `kda_kernels.sm120_prefill`, so no call site
changes.
- The wrapper's tests move to `tests/experimental/`, including its
CUDA-graph coverage. The stable lane no longer constructs the wrapper,
so deleting the experimental directory leaves it green.

None of this is in `v0.6.18` — that tag has no
`kda_kernels/sm120_prefill/` at all. Both changes are free today and
cost a deprecation cycle once `0.7` cuts.

## 🔍 Related Issues

- #5069 — graduation plan for the wrapper (owner, criteria, target).
- #4936 — KDA API unification audit; this is steps 3b-i and 3c.
- #4965 has landed, removing the training/backward family, which is why
only `RecurrentKDAPrefillWrapper` is marked here. With it merged and
this PR, no unreleased KDA symbol is advertised at the top level for
0.7.

## 🧪 Tests

All on a B200 (CC 10.0).

- `tests/experimental/test_kda_prefill_wrapper.py` — 10 passed. These
pin the experimental
marking itself, the top-level export, the plan metadata and buffer
handoff, the planner's
validation, the planned path against the eager packed path it wraps
(plain and checkpointed,
  bit-exact), and CUDA-graph capture/replay.
- `tests/kda/test_recurrent_kda_prefill.py` — 262 passed, 1 skipped, run
with
`flashinfer/experimental/kda_prefill_wrapper/` deleted. The stable lane
has no remaining
  reference to the wrapper, so removal touches no stable test.
- `tests/kda/test_recurrent_kda_prefill_sm120.py` — 50 passed, 88
skipped (the skips are CC 12.0 cells).
- `examples/experimental/kda_prefill_wrapper.py` runs.
- Verified `flashinfer.experimental` is not in `sys.modules` after
`import flashinfer`, that
`pytest tests/` does not collect the relocated file, and that all three
SM120a names remain
  reachable as attributes.

Three mutations were used to check the tests actually hold the change
down, each of which used to
pass unnoticed: deleting both `@flashinfer_experimental_api` decorators,
and dropping `scale` or
`use_qk_l2norm_in_kernel` from the handoff. All three now fail. The
handoff assertion is derived
from `run`'s signature, so it covers parameters that do not change
numerics.

The two cake-vs-CuTe comparisons that used to drive the wrapper now call
the eager packed path.
That is a different dispatch configuration inside the kernel wrapper,
not the same call, so the
reference test covers the planned path at both the plain and the
checkpointed/indexed
configurations those tests exercise. Shared input builders and reference
implementations moved to
`tests/test_helpers/` so both lanes can use them; that accounts for most
of the diff in the stable
file.

## 📝 Notes for reviewers

- The class is deliberately **not** listed in
`docs/api/kda_prefill.rst`, per
`flashinfer/experimental/README.md` ("Experimental APIs are not listed
in `docs/api/*.rst`
before graduation"). The prose note still states the experimental
status, the opt-in and the
  limitations, and the package README carries the detail.
- `RecurrentKDAPrefillWrapper.__init__` is not decorated, so
construction imports the experimental
package and allocates a workspace without warning. `plan` and `run` both
warn, once each per
  process, so any actual use is warned; construction alone is not.
- `_planned`, `_num_sequences`, `_total_tokens` and `_lock` moved to the
planner and are no longer
attributes of the wrapper. `device`, `plan` and `run` are the whole
public surface.

## 📋 Not included (deliberately)

Step 3c in #4936 also proposes giving SM120a an explicit `backend=`
literal and gating its automatic branch. Both change `"auto"` prefill
routing on CC 12.0, mostly by converting working calls into raises, so
they belong in their own PR validated on a CC 12.0 device.

## 🚀 Pull Request Checklist

- [x] I have read the [Contributing
Guidelines](https://github.com/flashinfer-ai/flashinfer/blob/main/CONTRIBUTING.md).
- [x] I have installed and run `pre-commit`.
- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5069
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware, including a correctness test against a reference.
`examples/experimental/kda_prefill_wrapper.py` is runnable, and
`docs/api/kda_prefill.rst` states the experimental status, the opt-in
and the limitations.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.) The stable kernels the
wrapper hands off to stay AOT-registered, since `run` calls the stable
`recurrent_kda` facade.
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_kda_prefill_wrapper.py
```

## Summary by CodeRabbit

- **New Features**
- Packed prefill planning now generates ordering and chunk metadata on
the device, reducing host-side preparation.
- CUDA Graph replays can use shape-based capacity while adapting to the
actual chunk count.

- **Documentation**
- Documented `RecurrentKDAPrefillWrapper` as experimental, including
opt-in behavior, supported compute capabilities, backend limitations,
and warmup requirements.
  - Updated guidance for accessing SM120 prefill functionality.

- **API**
  - Removed SM120 prefill utilities from package-level exports.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->






<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an experimental recurrent KDA packed prefill planner for
supported CUDA architectures using the CuTe DSL backend.
- Added a runnable example with configurable sequence lengths and
attention heads.

- **Documentation**
- Clarified opt-in behavior, supported hardware, warmup constraints,
kernel dispatch, and experimental status.

- **Breaking Changes**
- Removed SM120 KDA prefill functions from package-level exports; use
the dedicated prefill modules instead.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [ae736b1](https://github.com/flashinfer-ai/flashinfer/commit/ae736b1863082e3eb893753a4d3e54d276486abf)

- **作者**: NVJiangShao
- **时间**: 2026-09-10T18:03:50Z
- **提交信息**: perf(moe): improve SM90 mixed-input CUTLASS MoE backend performance (#5005)

## 📌 Description

This PR improves the SM90 CUTLASS mixed-input MoE backend in two areas.

First, it expands the MXFP4×FP8 Humming single-warpgroup tactic set with
the
`(128, 64, 128)` shape for both PrefillAll and RollingRefill. The N64
shape is
registered alongside the existing N8/N16/N32/N40 shapes, routed through
the
small-K dispatch, and configured for two CTAs per SM, matching its
shared-memory
occupancy limit. PrefillAll is eligible for `K <= 384`, while
RollingRefill
covers `K > 384`.

Second, it extends the existing work-map builder, which already
constructs the
A and B TMA descriptors, to also construct output-D descriptors before
the
persistent grouped GEMM is launched:

- Allocate one prebuilt output descriptor per local expert.
- Select the corresponding D descriptor for the initial expert and
whenever
the scheduler moves to another expert, instead of rebuilding its
address,
  dimensions, and strides in the GEMM kernel.
- Remove mutable output descriptors from the epilogue shared-memory and
  per-SM descriptor workspace when the prebuilt path is enabled.

At SM90 module-generation time, the prebuilt-D variant is selected
internally
only if JIT is enabled and the current CUDA device reports 78 SMs,
covering the
intended H20 and H20-3e configurations. Devices reporting other SM
counts,
including H100 and H200, generate the generic mutable-D variant. The
78-SM
variant uses a distinct JIT module name to avoid a cache collision with
the
generic SM90 module. Single-warpgroup small-K kernels are excluded from
prebuilt-D and retain their existing direct-store epilogue.

On 78-SM devices, this compile-time switch applies to regular,
non-single-warpgroup SM90 mixed-input grouped GEMMs instantiated by this
launcher. The H20 evaluation below combines protocol-matched NCU sweeps
of
the MXFP4×FP8 Humming, INT4×FP8, and MXFP4×BF16 path families. The N64
tactic expansion is Humming-specific, while the prebuilt-D optimization
is
shared by all three regular mixed-input paths on the selected H20 route.

## Performance

### H20 DSV4-Pro TPEP benchmark

The formal H20 NCU evaluation covers all three regular SM90 mixed-input
path
families reached by this launcher:

- MXFP4 weights with FP8 activations (Humming).
- INT4 weights with internally quantized FP8 activations (W4A8), using
BF16
  output in the performance sweep.
- MXFP4 weights with BF16 activations (W4A16).

Each path covers all 36 DeepSeek-V4-Pro TPEP cases (`TP1/EP8`,
`TP2/EP4`,
`TP4/EP2`, and `TP8/EP1`) at batch sizes 8 through 2048, for 108 logical
cases
in total.

- Metric: NCU `gpu__time_duration.sum`; CUDA Event and host timings are
  excluded.
- NCU 2026.1.1, application replay, cache-control `none`, clock-control
`none`. This preserves the cache state established by the builder for
the
  immediately following GEMM.
- Each revision/case contains 50 fused calls; the first two are
discarded,
  leaving 48 paired samples.
- `FC1 total = FC1 builder + FC1 GEMM`.
- `FC2 total = FC2 builder + FC2 GEMM`.
- `FC1+FC2 total` includes both builders and both GEMMs.
- Per-case speedup is baseline median divided by candidate median;
aggregate
  values are geometric means.

<img width="4096" height="2920"
alt="dsv4_sm90_all_mixed_paths_pr_de701865_vs_main_39b484f1_ncu_speedup_percent_h20"
src="https://github.com/user-attachments/assets/5e1ccd1c-e40a-456c-99ea-18a33829155c"
/>


| H20 path | Cases | FC1 total | FC2 total | FC1+FC2 total | Equivalent
latency reduction |
|---|---:|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 36 | 1.0064x | 1.0923x | **1.0470x** | **4.493%**
|
| INT4×FP8 | 36 | 1.0211x | 1.0857x | **1.0515x** | **4.895%** |
| MXFP4×BF16 | 36 | 1.0014x | 1.0277x | **1.0123x** | **1.212%** |
| All three paths | 108 | 1.0096x | 1.0681x | **1.0368x** | **3.547%** |

| H20 FC1+FC2 total | TP1/EP8 | TP2/EP4 | TP4/EP2 | TP8/EP1 |
|---|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 1.0050x | 1.0045x | 1.0366x | 1.1484x |
| INT4×FP8 | 1.0218x | 1.0205x | 1.0292x | 1.1390x |
| MXFP4×BF16 | 1.0008x | 1.0018x | 1.0012x | 1.0460x |

All 36 Humming cases improved. The best Humming case was TP8/EP1 BS512:
`1416.928 us -> 1214.624 us` (`1.1666x`, 14.278% lower latency). The
aggregate
builder slowdown from constructing D descriptors is included in every
result.

All 36 INT4×FP8 cases improved. Its best FC1+FC2 case was TP8/EP1
BS128: `1413.136 us -> 1214.352 us` (`1.1637x`, 14.067% lower latency).

For MXFP4×BF16, 29 of 36 cases improved. Its best FC1+FC2 case was
TP8/EP1
BS128: `1704.464 us -> 1612.848 us` (`1.0568x`, 5.375% lower latency).
The largest of the seven remaining regressions was TP2/EP4 BS2048:
`11563.584 us -> 11577.600 us` (`0.9988x`, 0.121% higher latency).

#### Observed TP-dominant FC2 trend

In the DSV4 matrix, FC2's reduction K is the local intermediate size:
3072,
1536, 768, and 384 for TP1 through TP8. With the fixed `64x16x128`
tactic,
that corresponds to 24, 12, 6, and 3 mainloop K tiles per output tile. A
likely
explanation for the observed trend is that a smaller K does not reduce
the
amount of output data, but makes each output tile reach the epilogue
after
fewer mainloop iterations. This leaves less mainloop work over which to
amortize the fixed-cost mutable-D descriptor update, its warp
synchronization,
and descriptor fence release at an expert (`L_idx`) transition.
TP-dominant
configurations also have more local experts, which may increase expert
transitions and partial-tile fragmentation for the same routed-token
count.

The FC2 builder-plus-GEMM geometric means show the same trend across all
three
paths:

| H20 FC2 total | TP1/EP8<br>K=3072 | TP2/EP4<br>K=1536 |
TP4/EP2<br>K=768 | TP8/EP1<br>K=384 |
|---|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 1.0019x | 1.0007x | 1.0874x | **1.3055x** |
| INT4×FP8 | 1.0225x | 1.0201x | 1.0435x | **1.2763x** |
| MXFP4×BF16 | 1.0005x | 1.0028x | 1.0012x | **1.1105x** |

The cross-path trend is consistent with prebuilding D being most
valuable when
short FC2 mainloops have less work over which to amortize online
descriptor
maintenance. Because TP changes both reduction K and the local expert
count,
this sweep does not isolate their individual contributions. The prebuilt
path
still performs the required descriptor acquire and TMA stores; it
removes the
mutable descriptor rewrite, that update's warp synchronization, and
fence
release from the GEMM critical path.

Prebuilding D adds work to the builder: the builder-only aggregate was
`0.9835x` for MXFP4×FP8 Humming, `0.9805x` for INT4×FP8, and `0.9793x`
for
MXFP4×BF16. That cost is included in every FC1, FC2, and combined result
above.

The Humming sweep selected the same default Pingpong `64x16x128`
structural
tactic in baseline and candidate; N64 was selected in `0/72` case/stage
pairs.
The other two paths were forced to that same structural tactic (absolute
FC1
and FC2 profile IDs `0` and `116`), and the strict parser verified
matching
kernel families and structural tactics for all 144
baseline-versus-candidate
FC1/FC2 stage comparisons. The N64 tactics are Humming-only and do not
change
the tactic space of the other paths. The performance gains above are
therefore
not attributed to the new N64 tactic.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used
  my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed
  any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
> [pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Existing tests cover the affected paths; this PR does not add a
test-only
  file.
- [x] Relevant SM90 mixed-input correctness tests are passing.

Validation included:

- Exact SM90a JIT builds and fresh-process loads for both routes: H20
used
`fused_moe_90_h20_prebuilt_d`, while H200 used the generic
`fused_moe_90`
  module without the prebuilt-D define.
- A single no-build H20 run explicitly recorded candidate source
matching
`de701865`, the `fused_moe_90_h20_prebuilt_d` module, the prebuilt-D
compile
define, and the loaded `.so` SHA256; all 26 selected tests passed. These
comprise seven
  Humming `use_autotune=False` cases, 13 W4A16
correctness/coverage/activation cases, and six W4A8 cases covering BF16
and
  FP16 correctness, autotuning, and the exact packed-workspace size.
- The Humming no-build A/B sweep over all 36 DeepSeek-V4-Pro TPEP cases
produced bit-identical BF16 outputs from bit-identical deterministic
inputs.
- The Humming and other-path performance sweeps produced 216 complete
NCU
reports. Every report passed the exact 200-launch ordered-slot check;
all
144 baseline-versus-candidate FC1/FC2 stage comparisons in the
other-path
  sweep used the same structural tactic.
- During N64 bring-up on H20, forcing N64 PrefillAll for both FC1 and
FC2 at K
values 128, 256, and 384 produced bit-identical complete MoE outputs to
N40
  PrefillAll (`max_abs = 0`).
- `pre-commit run -a` passed.

## Reviewer Notes

- This PR contains three commits so the N64 tactic expansion, prebuilt-D
optimization, and H20-only device gate remain independently reviewable.
- The H20 selection is internal to the SM90 JIT generator and does not
add a
  public API argument. H100 and H200 continue to use the generic module.
- Each path's 36-case DSV4 matrix holds the structural tactic constant
between
baseline and candidate. The reported gains therefore are not attributed
to
  the new N64 tactic.
- The prebuilt path stores one read-only D descriptor per expert and
shares it
  between consumer warpgroups.
- The H20 performance validation covers Humming plus both other regular
SM90
  mixed-input path families reached by this launcher.
- Non-prebuilt kernels retain their mutable descriptor initialization
and
update path. Single-warpgroup kernels retain their direct-store
epilogue.
- The builder overhead and main-kernel gains are both included in the
reported
  fused-call totals.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for additional SM90 mixed-precision MoE and grouped GEMM
configurations using 128×64 tiles.
* Expanded compatibility with larger tile widths in single-warpgroup
execution paths.
* Added optimized output descriptor handling for supported H20 and
H20-3e systems.

* **Performance Improvements**
* Improved scheduling and execution efficiency for supported H20 MoE
workloads.
* Added optimized kernel configurations for FP8 activation and FP4
weight operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>

### [72f6dfa](https://github.com/flashinfer-ai/flashinfer/commit/72f6dfade4367ba6e68f6aee1b1393c0c902b474)

- **作者**: NVJiangShao
- **时间**: 2026-09-10T18:03:23Z
- **提交信息**: perf(moe): improve SM90 mixed-input CUTLASS MoE backend performance (#5005)

## 📌 Description

This PR improves the SM90 CUTLASS mixed-input MoE backend in two areas.

First, it expands the MXFP4×FP8 Humming single-warpgroup tactic set with
the
`(128, 64, 128)` shape for both PrefillAll and RollingRefill. The N64
shape is
registered alongside the existing N8/N16/N32/N40 shapes, routed through
the
small-K dispatch, and configured for two CTAs per SM, matching its
shared-memory
occupancy limit. PrefillAll is eligible for `K <= 384`, while
RollingRefill
covers `K > 384`.

Second, it extends the existing work-map builder, which already
constructs the
A and B TMA descriptors, to also construct output-D descriptors before
the
persistent grouped GEMM is launched:

- Allocate one prebuilt output descriptor per local expert.
- Select the corresponding D descriptor for the initial expert and
whenever
the scheduler moves to another expert, instead of rebuilding its
address,
  dimensions, and strides in the GEMM kernel.
- Remove mutable output descriptors from the epilogue shared-memory and
  per-SM descriptor workspace when the prebuilt path is enabled.

At SM90 module-generation time, the prebuilt-D variant is selected
internally
only if JIT is enabled and the current CUDA device reports 78 SMs,
covering the
intended H20 and H20-3e configurations. Devices reporting other SM
counts,
including H100 and H200, generate the generic mutable-D variant. The
78-SM
variant uses a distinct JIT module name to avoid a cache collision with
the
generic SM90 module. Single-warpgroup small-K kernels are excluded from
prebuilt-D and retain their existing direct-store epilogue.

On 78-SM devices, this compile-time switch applies to regular,
non-single-warpgroup SM90 mixed-input grouped GEMMs instantiated by this
launcher. The H20 evaluation below combines protocol-matched NCU sweeps
of
the MXFP4×FP8 Humming, INT4×FP8, and MXFP4×BF16 path families. The N64
tactic expansion is Humming-specific, while the prebuilt-D optimization
is
shared by all three regular mixed-input paths on the selected H20 route.

## Performance

### H20 DSV4-Pro TPEP benchmark

The formal H20 NCU evaluation covers all three regular SM90 mixed-input
path
families reached by this launcher:

- MXFP4 weights with FP8 activations (Humming).
- INT4 weights with internally quantized FP8 activations (W4A8), using
BF16
  output in the performance sweep.
- MXFP4 weights with BF16 activations (W4A16).

Each path covers all 36 DeepSeek-V4-Pro TPEP cases (`TP1/EP8`,
`TP2/EP4`,
`TP4/EP2`, and `TP8/EP1`) at batch sizes 8 through 2048, for 108 logical
cases
in total.

- Metric: NCU `gpu__time_duration.sum`; CUDA Event and host timings are
  excluded.
- NCU 2026.1.1, application replay, cache-control `none`, clock-control
`none`. This preserves the cache state established by the builder for
the
  immediately following GEMM.
- Each revision/case contains 50 fused calls; the first two are
discarded,
  leaving 48 paired samples.
- `FC1 total = FC1 builder + FC1 GEMM`.
- `FC2 total = FC2 builder + FC2 GEMM`.
- `FC1+FC2 total` includes both builders and both GEMMs.
- Per-case speedup is baseline median divided by candidate median;
aggregate
  values are geometric means.

<img width="4096" height="2920"
alt="dsv4_sm90_all_mixed_paths_pr_de701865_vs_main_39b484f1_ncu_speedup_percent_h20"
src="https://github.com/user-attachments/assets/5e1ccd1c-e40a-456c-99ea-18a33829155c"
/>


| H20 path | Cases | FC1 total | FC2 total | FC1+FC2 total | Equivalent
latency reduction |
|---|---:|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 36 | 1.0064x | 1.0923x | **1.0470x** | **4.493%**
|
| INT4×FP8 | 36 | 1.0211x | 1.0857x | **1.0515x** | **4.895%** |
| MXFP4×BF16 | 36 | 1.0014x | 1.0277x | **1.0123x** | **1.212%** |
| All three paths | 108 | 1.0096x | 1.0681x | **1.0368x** | **3.547%** |

| H20 FC1+FC2 total | TP1/EP8 | TP2/EP4 | TP4/EP2 | TP8/EP1 |
|---|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 1.0050x | 1.0045x | 1.0366x | 1.1484x |
| INT4×FP8 | 1.0218x | 1.0205x | 1.0292x | 1.1390x |
| MXFP4×BF16 | 1.0008x | 1.0018x | 1.0012x | 1.0460x |

All 36 Humming cases improved. The best Humming case was TP8/EP1 BS512:
`1416.928 us -> 1214.624 us` (`1.1666x`, 14.278% lower latency). The
aggregate
builder slowdown from constructing D descriptors is included in every
result.

All 36 INT4×FP8 cases improved. Its best FC1+FC2 case was TP8/EP1
BS128: `1413.136 us -> 1214.352 us` (`1.1637x`, 14.067% lower latency).

For MXFP4×BF16, 29 of 36 cases improved. Its best FC1+FC2 case was
TP8/EP1
BS128: `1704.464 us -> 1612.848 us` (`1.0568x`, 5.375% lower latency).
The largest of the seven remaining regressions was TP2/EP4 BS2048:
`11563.584 us -> 11577.600 us` (`0.9988x`, 0.121% higher latency).

#### Observed TP-dominant FC2 trend

In the DSV4 matrix, FC2's reduction K is the local intermediate size:
3072,
1536, 768, and 384 for TP1 through TP8. With the fixed `64x16x128`
tactic,
that corresponds to 24, 12, 6, and 3 mainloop K tiles per output tile. A
likely
explanation for the observed trend is that a smaller K does not reduce
the
amount of output data, but makes each output tile reach the epilogue
after
fewer mainloop iterations. This leaves less mainloop work over which to
amortize the fixed-cost mutable-D descriptor update, its warp
synchronization,
and descriptor fence release at an expert (`L_idx`) transition.
TP-dominant
configurations also have more local experts, which may increase expert
transitions and partial-tile fragmentation for the same routed-token
count.

The FC2 builder-plus-GEMM geometric means show the same trend across all
three
paths:

| H20 FC2 total | TP1/EP8<br>K=3072 | TP2/EP4<br>K=1536 |
TP4/EP2<br>K=768 | TP8/EP1<br>K=384 |
|---|---:|---:|---:|---:|
| MXFP4×FP8 Humming | 1.0019x | 1.0007x | 1.0874x | **1.3055x** |
| INT4×FP8 | 1.0225x | 1.0201x | 1.0435x | **1.2763x** |
| MXFP4×BF16 | 1.0005x | 1.0028x | 1.0012x | **1.1105x** |

The cross-path trend is consistent with prebuilding D being most
valuable when
short FC2 mainloops have less work over which to amortize online
descriptor
maintenance. Because TP changes both reduction K and the local expert
count,
this sweep does not isolate their individual contributions. The prebuilt
path
still performs the required descriptor acquire and TMA stores; it
removes the
mutable descriptor rewrite, that update's warp synchronization, and
fence
release from the GEMM critical path.

Prebuilding D adds work to the builder: the builder-only aggregate was
`0.9835x` for MXFP4×FP8 Humming, `0.9805x` for INT4×FP8, and `0.9793x`
for
MXFP4×BF16. That cost is included in every FC1, FC2, and combined result
above.

The Humming sweep selected the same default Pingpong `64x16x128`
structural
tactic in baseline and candidate; N64 was selected in `0/72` case/stage
pairs.
The other two paths were forced to that same structural tactic (absolute
FC1
and FC2 profile IDs `0` and `116`), and the strict parser verified
matching
kernel families and structural tactics for all 144
baseline-versus-candidate
FC1/FC2 stage comparisons. The N64 tactics are Humming-only and do not
change
the tactic space of the other paths. The performance gains above are
therefore
not attributed to the new N64 tactic.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used
  my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed
  any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
> [pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Existing tests cover the affected paths; this PR does not add a
test-only
  file.
- [x] Relevant SM90 mixed-input correctness tests are passing.

Validation included:

- Exact SM90a JIT builds and fresh-process loads for both routes: H20
used
`fused_moe_90_h20_prebuilt_d`, while H200 used the generic
`fused_moe_90`
  module without the prebuilt-D define.
- A single no-build H20 run explicitly recorded candidate source
matching
`de701865`, the `fused_moe_90_h20_prebuilt_d` module, the prebuilt-D
compile
define, and the loaded `.so` SHA256; all 26 selected tests passed. These
comprise seven
  Humming `use_autotune=False` cases, 13 W4A16
correctness/coverage/activation cases, and six W4A8 cases covering BF16
and
  FP16 correctness, autotuning, and the exact packed-workspace size.
- The Humming no-build A/B sweep over all 36 DeepSeek-V4-Pro TPEP cases
produced bit-identical BF16 outputs from bit-identical deterministic
inputs.
- The Humming and other-path performance sweeps produced 216 complete
NCU
reports. Every report passed the exact 200-launch ordered-slot check;
all
144 baseline-versus-candidate FC1/FC2 stage comparisons in the
other-path
  sweep used the same structural tactic.
- During N64 bring-up on H20, forcing N64 PrefillAll for both FC1 and
FC2 at K
values 128, 256, and 384 produced bit-identical complete MoE outputs to
N40
  PrefillAll (`max_abs = 0`).
- `pre-commit run -a` passed.

## Reviewer Notes

- This PR contains three commits so the N64 tactic expansion, prebuilt-D
optimization, and H20-only device gate remain independently reviewable.
- The H20 selection is internal to the SM90 JIT generator and does not
add a
  public API argument. H100 and H200 continue to use the generic module.
- Each path's 36-case DSV4 matrix holds the structural tactic constant
between
baseline and candidate. The reported gains therefore are not attributed
to
  the new N64 tactic.
- The prebuilt path stores one read-only D descriptor per expert and
shares it
  between consumer warpgroups.
- The H20 performance validation covers Humming plus both other regular
SM90
  mixed-input path families reached by this launcher.
- Non-prebuilt kernels retain their mutable descriptor initialization
and
update path. Single-warpgroup kernels retain their direct-store
epilogue.
- The builder overhead and main-kernel gains are both included in the
reported
  fused-call totals.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for additional SM90 mixed-precision MoE and grouped GEMM
configurations using 128×64 tiles.
* Expanded compatibility with larger tile widths in single-warpgroup
execution paths.
* Added optimized output descriptor handling for supported H20 and
H20-3e systems.

* **Performance Improvements**
* Improved scheduling and execution efficiency for supported H20 MoE
workloads.
* Added optimized kernel configurations for FP8 activation and FP4
weight operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>

### [0158769](https://github.com/flashinfer-ai/flashinfer/commit/01587699b6a4b47305595f56da391caa54055707)

- **作者**: kangbintNV
- **时间**: 2026-09-10T17:44:45Z
- **提交信息**: docs: document MiniMax-H3 prepared run parameters (#5087)

## 📌 Description

Add a complete NumPy-style docstring for
`MiniMaxH3Mxfp8PreAttention.run`, including every runtime parameter,
return
objects, and the prepared-operation tensor identity constraint.

This resolves the Docstring Completeness failure reported for the API
since
2026-09-10 and also satisfies the argument-consistency check.

## 🔍 Related Issues

N/A — automated documentation-check finding.

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

Validation performed:

- `pre-commit run --all-files`
- `python3 -m py_compile flashinfer/cake_minimax_h3.py`
- `python3 -m pr_checks.check_docstrings`: 339 APIs scanned, 0
completeness failures, 0 argument-consistency failures
- `python3 scripts/check_pr_document.py --base origin/main --head HEAD
--strict`: 0 new findings

No behavioral tests were added because this change only expands an
existing
docstring. The focused pytest could not be started in the local
environment
because its Python interpreter does not have `pytest` installed.

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

The parameter shapes and dtypes in the docstring mirror the validation
contract
in `prepare_minimax_h3_mxfp8_pre_attention`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Expanded API documentation for the MiniMax H3 pre-attention operation,
including tensor shapes, data types, ownership requirements, return
values, and rebinding behavior.
  * No runtime behavior or public API changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b8d2b3f](https://github.com/flashinfer-ai/flashinfer/commit/b8d2b3f07827c8377fd905ff34389ceeddbe1de5)

- **作者**: Pratap
- **时间**: 2026-09-10T16:27:33Z
- **提交信息**: fix(activation): pick a vector width that divides hidden_size in act_and_mul (fixes d=3420) (#5013)

## 📌 Description

`act_and_mul_kernel` hardcodes `vec_size = 16 / sizeof(T)` (8 for
fp16/bf16) and reads the second half of each row at element offset `d`
and writes the output row at `token_idx * d`. When `d` is not a multiple
of 8 those addresses are not 16-byte aligned and the vectorized loads
fault. Qwen2.5-VL's vision MLP has `intermediate_size = 3420`: the y
half starts at byte 6840, which is only 8-byte aligned, and
`silu_and_mul` dies with `cudaErrorMisalignedAddress` in both fp16 and
bf16.

The Python guard did not catch it because it checks the full row:
`input.shape[-1] * itemsize % 16`, i.e. `4d % 16`, which passes for any
`d % 4 == 0`. So `d = 1234` was rejected cleanly while `d = 3420`
reached the kernel and crashed.

This PR:

- makes `vec_size` a template parameter of `act_and_mul_kernel`, and has
the launcher pick the largest power of two that divides `d` (8, 4, 2 or
1). With `vec_size | d` every access (x half, y half at `+d`, output row
at `token_idx * d`) is aligned to `vec_size * sizeof(T)`. Power-of-two
and multiple-of-8 dims keep the full width, so common models are
untouched.
- relaxes the guard in `silu_and_mul`, `gelu_and_mul` and
`gelu_tanh_and_mul` to "last dimension must be even".
- removes the kernel's tail loop. With `vec_size | d` the grid-stride
main loop already covers every element, so the tail can only re-process
elements. Since #4733 capped `blockDim` at 256, its bound `d % (blockDim
* vec_size)` no longer equals `d % vec_size`, so on main it re-computes
up to 2047 already-written elements per row with scalar accesses (768
for `d = 11008`). Output was correct, the work was wasted.

Same design as #2613 (approved by @yzh119 in February, never rebased and
now conflicting), redone on current main.

## 🔍 Related Issues

Fixes #2526. Supersedes #2613.

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

`tests/utils/test_activation.py` gains `855` (odd, `vec_size = 1`),
`1710` (`vec_size = 2`) and `3420` (`vec_size = 4`) in all three dim
lists.

On an RTX 3050 Laptop (sm_86, CUDA 13.3, torch 2.14.0+cu130):

```
pytest tests/utils/test_activation.py -k "855 or 1710 or 3420 or 11008"
540 passed, 540 skipped (enable_pdl=True needs sm_90), 1620 deselected
```

Before the patch, `silu_and_mul` on `(4, 2*3420)` raises `CUDA error:
misaligned address` in fp16 and bf16; after it matches the torch
reference.

Throughput (fp16, 4096 tokens, median of 5x200 iterations, kernel is
memory-bound at ~179 GB/s on this GPU):

| d | before (us) | after (us) |
| --- | ---: | ---: |
| 3416 | 482.2 | 468.8 |
| 4096 | 561.0 | 560.3 |
| 8192 | 1118.9 | 1119.8 |
| 11008 | 1517.1 | 1504.0 |
| 12288 | 1680.2 | 1679.4 |
| 16384 | 2240.4 | 2239.9 |

The small gains at 3416 and 11008 are the removed duplicate tail; the
rest is noise.

## Reviewer Notes

- Only fp16/bf16 go through `DISPATCH_DLPACK_DTYPE_TO_CTYPE_FP16`, so
the maximum `vec_size` is 8 and the dispatch has four cases.
- Base pointers are still assumed 16-byte aligned, as before. Offset
views (e.g. `x[:, 1:]`) are out of scope here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Activation-and-mul operations now support any input shape with an even
final dimension, including dimensions that were previously rejected.
- Improved handling of varying activation dimensions enables broader
compatibility across supported inputs.

- **Tests**
- Expanded coverage for fused SiLU, GELU-tanh, and GELU
activation-and-mul operations with additional nonstandard dimensions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d195309](https://github.com/flashinfer-ai/flashinfer/commit/d1953098bb04337348f351832c1be592740e3826)

- **作者**: Yang Xu
- **时间**: 2026-09-10T14:36:25Z
- **提交信息**: refactor(kda): remove the unreleased recurrent KDA training/backward family (#4965)

## Summary

KDA training (forward + backward) ships from cuDNN Frontend, where
`cudnn.linear_attention.ops.kimi_delta_attention` already provides KDA
fwd+bwd with autograd and where the CAKE training kernels are being
added as an engine. FlashInfer keeps the inference surface. This removes
the paired training API and the legacy backward that shares its JIT
module, before either reaches a release.

Context:
https://github.com/flashinfer-ai/flashinfer/issues/4936#issuecomment-5538954882
(step 3b of #4936 becomes removal instead of relocation to
`flashinfer/experimental/`).

### Removed

- Public symbols: `recurrent_kda_training_forward`,
`recurrent_kda_training_backward`, `RecurrentKDATrainingContext`,
`recurrent_kda_backward`, `RecurrentKDABackwardWorkspace` (re-exports in
`__init__.py` and `kda.py`).
- Modules: `kda_training.py`, `_kda_training_impl.py`,
`_kda_training_dispatch.py`, `kda_backward.py`,
`jit/flash_kda_training.py`, `jit/flash_kda_backward.py`; the
`flash_kda_backward_sm10{0,3}a` capability flags and specs in `aot.py`.
- Frozen CUDA sources: `csrc/kda/flashkda_training_*.cu`,
`flashkda_backward*.cu`, `training_fallback_pointer_sm_10{0,3}a.cu`,
`training_grouped_row_wg8_pointer_sm_10{0,3}a.cu`,
`cake_aligned_training_export/` (and their `.pre-commit-config.yaml`
exclude).
- Docs: `docs/api/kda_training.rst`, `docs/api/kda_backward.rst`, two
toctree lines.
- Tests / benchmarks:
`tests/kda/test_recurrent_kda_{training,backward}.py`,
`tests/jit/test_flash_kda_{training,backward}_jit.py`,
`benchmarks/bench_recurrent_kda_{training,backward}.py`.

### Kept (released inference surface)

- The `recurrent_kda` prefill path including the `m128_n16_checkpoint`
variant and the `state_checkpoints` / `checkpoint_cu_starts` /
`checkpoint_every_n_tokens` kwargs (SGLang prefix caching).
- The `flashkda_binding_common.cuh` changes from #4636 (SM103a target,
checkpoint granularity 16).

### Compatibility

None of the removed symbols is in `v0.6.18`; GitHub-wide code search for
`recurrent_kda_training` finds no caller outside this repository. No
deprecation shim is needed.

## Test plan

- [x] `grep` for every removed identifier across the tree: no remaining
references (CODEOWNERS globs aside)
- [x] `ruff check` / `ruff format --check` on `flashinfer/__init__.py`,
`flashinfer/kda.py`, `flashinfer/aot.py`
- [x] `pre-commit run --files <changed>`: all hooks pass
- [x] `python -m compileall flashinfer`
- [x] `import flashinfer; import flashinfer.kda, flashinfer.kda_prefill,
flashinfer.kda_decode, flashinfer.aot` from this tree; removed symbols
absent, prefill symbols present
- [x] `pytest tests/trace/test_template_registry.py`: 4 passed
- [ ] CI

Draft until the cuDNN Frontend engine PR is up for cross-reference.

<!-- note to self: claude::474ab347-d36d-4192-8851-7adc03759dc1 —
"Flashinfer KDA training kernel migration to cuDNN" · cwd
/home/scratch.yanxu_libs/cudnn_frontend · workspace
/home/scratch.yanxu_gpu/kda_bprop_move_2026-09-04 -->

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Breaking Changes**
* Removed the recurrent KDA backward and training APIs, including their
public exports and JIT/AOT support.
* Removed the associated GPU implementations and fallback execution
paths.
  * Removed documentation covering recurrent KDA backward and training.

* **Chores**
  * Removed related benchmarks and automated tests.
* Updated generated-code exclusions to cover additional build artifacts.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [98eea52](https://github.com/flashinfer-ai/flashinfer/commit/98eea5207b1febc2bd9b80fa55570f623f85a572)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-09-10T13:12:34Z
- **提交信息**: fix: guard BF16 warp Split-K availability and prune tactics (#5089)

<!-- .github/pull_request_template.md -->

## 📌 Description

Guard BF16 warp Split-K runner creation with the existing
`is_cute_dsl_experimental_available()` probe. CuTe DSL 4.6.2 lacks
`cutlass.experimental`; skip only this runner before importing its
kernel, keeping Direct, cluster Split-K, and the cuBLASLt fallback
available.

Also include the retained BF16 warp Split-K tactic-pruning heuristic:
- For multi-tile K, prune larger token tiles when a smaller supported
tile produces the same CTA grid. Keep single-K-tile alternatives, which
can still win, and preserve the default tactic.
- Exclude `k_tile=256, k_tile_count=2` from candidate generation and
explicit validation: this schedule can produce an invalid hinted
`LDGSTS`.
- Bump the BF16 CuTe DSL autotune cache version from 11 to 12 so earlier
selections are not reused.

The GPU mainloop, JIT/launch implementation, default-selection
heuristic, dependencies, and test files are unchanged. Document the warp
runner's CuTe DSL >= 4.7 requirement without raising the package
dependency floor.

## 🔍 Related Issues

Follow-up to #4908.

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

All hooks passed for both changed files: `pre-commit run --files
flashinfer/gemm/gemm_base.py
flashinfer/gemm/kernels/dense_bf16_gemm_warp_splitk.py`. Repository-wide
hooks were not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

No test files added or modified. Reused the existing accuracy tests on
NVIDIA B200 (SM100), CUDA 13.0, PyTorch 2.13.0+cu130:

```bash
python -m pytest -q tests/gemm/test_mm_bf16.py -k 'cute and not cutile'
```

- CuTe DSL 4.6.2: 10 passed; verified the warp kernel module was never
imported.
- CuTe DSL 4.7.0: 10 passed; verified the warp kernel remained
available.

Additionally verified the public K=512, N=256 path: autotune at M=64
with bias and PDL, then run M=8/25/33 and compare with an FP32
reference. No test files were added for these validation runs.

Validation is scoped to these existing BF16 CuTe DSL cases and the
stated runtime checks, not the full repository suite.

### Autotuning cost

Before = `31a6926b` (availability guard only); after = this heuristic
update.

| Metric | Before | After |
|---|---:|---:|
| Warp tactic evaluations across the full-table harness's 77 tuning
profiles | 9,714 | 5,834 |
| Existing B200 accuracy/autotune suite wall time, one run per version |
247.26 s | 124.38 s |

Candidate counts follow the 210-cell, 16-family workload from
vllm-project/vllm#54524: tune once at M=16 per family, or M=8 when the
family's largest M is 8. The 39.9% reduction measures the search space,
not kernel latency.

The wall-time rows use the exact pytest command and
B200/CUDA/PyTorch/CuTe DSL 4.7.0 environment above, including JIT
compilation, autotuning, setup, and correctness checks. They are
single-run observations, not a steady-state kernel benchmark or a
general speedup guarantee.

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

Missing experimental support silently excludes the warp runner from both
default selection and autotuning; it does not disable the whole
`cute-dsl` backend or suppress unrelated import failures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved compatibility with older CuTe DSL versions by omitting
unsupported experimental warp Split-K runners.
- Prevented unavailable runners from being included in BF16 matrix
multiplication execution paths.
- Prevented selection of an invalid BF16 GEMM schedule that could
produce incorrect GPU instructions.
- Improved autotuning by excluding redundant token-tile options when
they provide no additional grid coverage.
- **Documentation**
- Clarified CuTe DSL version requirements and available BF16 runner
behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a866ec0](https://github.com/flashinfer-ai/flashinfer/commit/a866ec03a99da34f559b1d43b05a276e34955d16)

- **作者**: Alex Yang
- **时间**: 2026-09-10T09:33:30Z
- **提交信息**: fix(moe): bound routing_replay_out dim0 from below in both validators (#5072)

## 📌 Description

The trtllm routing kernels write one replay row per token
unconditionally — `routingDeepSeek`
launches `numBlocks == num_tokens` and writes row `blockIdx.x`, and the
custom/llama4 kernels write
row `tokenIdx` — so the kernel touches rows `[0, num_tokens)` regardless
of the buffer's actual
`dim0`.

Neither validator checked that lower bound. The C++ one receives
`hidden_states` but only compared
`device_id`; the Python one never saw `num_tokens` at all. A caller that
passes a shorter buffer
(e.g. `num_tokens=1024` against a `[8, 2]` replay tensor) is accepted by
both, and the kernel then
writes past the end of the allocation. Under the caching allocator that
lands silently in a
neighbouring tensor; `compute-sanitizer` only sees it with
`PYTORCH_NO_CUDA_MEMORY_CACHING=1`.

This adds `dim0 >= num_tokens` to both validators. Oversized buffers
stay legal, which is what
CUDA-graph capture at a fixed maximum batch size actually needs — the
original "dim0 is
intentionally NOT checked" comment conflated the two directions.

## 🔍 Related Issues

Addresses part 2 of #5009.

Part 1 of that issue — the fused-shared-experts replay stride — is
deliberately **not** in this PR.
It removes host-side rejections in order to enable a currently
unreachable feature combination
(`routing_replay_out` together with `num_fused_shared_experts > 0`),
which is a larger change with a
different review surface. The OOB it describes is unreachable today
precisely because those
rejections exist.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on B300 (SM103), CUDA 13.0, against this branch:

```
tests/moe/test_trtllm_gen_fused_moe.py tests/moe/test_trtllm_gen_routed_fused_moe.py
  -k 'replay or shared_expert'          46 passed, 4459 deselected
tests/model_optimizations/test_dsv3_fused_routing.py -k replay
                                        84 passed, 60 skipped, 4681 deselected
```

Existing callers were checked against the new bound before it was added,
since a new rejection is
exactly the kind of change that breaks a test quietly:

- `test_dsv3_fused_routing.py` and `test_trtllm_gen_fused_moe.py`
allocate `(num_tokens, top_k)`,
  so the bound holds exactly.
- `test_trtllm_gen_routed_fused_moe.py` uses `replay_capacity =
num_tokens + 5`, deliberately
  oversized — which this change keeps legal.
- `test_trtllm_gen_fused_moe.py:2461` passes `torch.empty((1, 1))` and
asserts
`match="routing_replay_out is not supported"`. A `(1, 1)` buffer would
also fail the new bound,
  so the raised message could have changed; it does not, because the
`num_fused_shared_experts > 0` rejection sits first in
`_validate_routing_replay_out` and the new
  check is second-to-last.

**No new test is added.** #5009 suggests FP8/FP4 host-side rejection
tests for the new bound; happy
to add them here if a reviewer prefers that over a follow-up.

AI-assisted (Claude Opus 5).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Routing replay buffers are now validated to ensure they contain at
least one row per input token.
* Undersized buffers now produce a clear error showing the required
minimum and received size, preventing potential out-of-bounds writes.
  * Oversized buffers remain supported for CUDA graph pre-allocation.
* Validation is consistently applied across supported Mixture-of-Experts
operations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: feih <feih@nvidia.com>

### [556679b](https://github.com/flashinfer-ai/flashinfer/commit/556679b27fa4957c31f9b466d6ac5ed3b3476061)

- **作者**: eigen
- **时间**: 2026-09-10T08:15:19Z
- **提交信息**: feat(cake_nvfp4_svdquant): add NVFP4 SVDQuant GEMM SM100 and SM103 backend (#5076)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `backend="cake"` to `mm_nvfp4_svdquant` for NVFP4 SVDQuant GEMM on
SM100 and SM103. The backend combines the quantized GEMM with the
low-rank correction and optional bias, using generated CUDA sources and
the existing FlashInfer JIT package layout.

Use `backend="cake"` explicitly; `backend="auto"` does not select it.
Only exact `(M, N, K, rank, bias)` tuples in the detected architecture's
catalog are supported, with `bias` denoting whether a bias tensor is
present. `enable_pdl=None` preserves the selected route's setting; an
explicit conflicting value is rejected.

CUDA 13.0 or newer is required for `backend="cake"` on SM100 and SM103;
other backends retain their existing CUDA requirements. Commit
`5c62434686eaf3b15e6dcf2ef688e9d43b291284` adds the check before
generated-backend compilation. Generated CUDA and catalogs are
unchanged. Validation of this version check, the CUDA 12.9 skips and
rejection case, and normal CUDA 13.0 operation is still pending; the
completed package and performance receipts below retain their original
commit binding.

Both architecture catalogs ship in the wheel. API tests cover CUDA Graph
execution across all seven selected templates and scale buffers with
additional backing storage.

The generated CUDA and catalogs retain the source binding of both
complete 64 MiB matrices, with the explicitly accepted rank-96
performance exception described below. B300 and B200 checkout and
installed-wheel API validation passed for the same final combined
package, including explicit backend forwarding; pre-commit checks
passed; the original automated performance failures remain visible.

The previously validated integration change forwards literal
`backend="cake"` from the public API to the generated loader, whose
keyword-only backend contract rejects other values before route
selection. Generated CUDA, catalogs, selected routes and launches are
unchanged. The final package/API and pre-commit checks include this
two-file follow-up. B300 and B200 checkout and installed-package API
validation passed using the same final wheel.

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the pinned hooks on the changed files with `pre-commit
run --files ...`; all passed without modifying files.

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

Qualification uses all 46 declared shapes and seven selected templates
per architecture. Source/export must be at least 0.97x, directional
disagreement and endpoint drift at most 2%, and the recorded floor for
all four declared CUTLASS/export comparisons is 1.0x. Delivery has an
explicit acceptance exception only for the persistent
M129/N3072/K3072/rank96/bias tactic-25 comparison on each architecture.
Sampled steady-state SM clocks must meet the 1900 MHz floor. Correctness
uses FP4 tolerances atol=1.0 and rtol=0.1.

Both selected 64 MiB matrices completed all 46 shapes and passed
correctness on every row; each passed 45/46 complete automated gate
sets. An explicit user-accepted exception applies only to the persistent
M129/N3072/K3072/rank96/bias tactic-25 CUTLASS comparison on SM100 and
SM103. That measured gap no longer blocks delivery. The original failed
gate values remain unchanged; the recorded runtime-source binding is
retained, and combined checkout/wheel API validation passed on B300 and
B200 using the same wheel; pre-commit checks passed. The historical 8
MiB tables below retain their original measurement binding: SM103 passed
46/46 rows; SM100 passed 43/46.

## Final pre-commit and publication-base review

The final pinned hooks passed on all **34 delivery files** without
changes in **7 s**. This is included in the final package step below. An
earlier pre-commit run passed on **38 files**: the 34 delivery files
plus four license copies created by the wheel build. Hooks made no
changes. The four build-created license copies are excluded from the
public payload. Hook runtime was **137 s**, with **226.541274 s**
physical turnaround; existing filters preserve the byte-attested
generated CUDA.

The public diff is applied to FlashInfer revision
`dbb52c8a9775840fbfe229eb3b83543a59449b19`. The upstream generated-code
exclusion is retained alongside the new NVFP4 exclusion. Generated CUDA,
catalog and handwritten API/loader files match the final B300-tested
package. Recovered local commit
`34a30311cf6ed95a192e36058700ff2117ee7223` records the public diff.
Relevant upstream API, JIT core/environment, utility, test and build
files did not change between the measured package base and this
publication base. The previously synchronized producer passed the checks
below. The synchronized producer retains a strict regeneration identity
failure because generated names and catalog bytes changed. The completed
correspondence review below establishes unchanged computation and launch
behavior, allowing reuse of the source GPU gates while retaining the
exact original qualified export and wheel.

## Synchronized source correspondence and gate reuse

The review covers **46 routes and seven modules per architecture**. A
one-to-one module mapping shows that every route value is identical
except `stage/module/name`. Argument plans, compile flags, architecture,
role and FFI entry are identical. Device sources differ only in the
generated kernel symbol; binding sources differ only in that symbol and
their private host namespace. The original adapter's four shared
integration files per architecture are byte-identical. The separate
public API/loader forwarding change is covered by the final package
tests on both GPUs.

The recorded result remains `strict_archived_delivery_identity=false`,
and the diagnostic retains `acceptance_granted=false`. The review
supports reusing the source GPU gates for the unchanged computation and
launch program. This PR retains the **exact original qualified generated
files and final wheel**; it makes no new binary-identity or performance
claim for the newly named diagnostic artifacts.

The two existing dispatcher unit files passed **31 tests** in **1.60 s**
pytest time and **3.423902 s** process time. Diagnostic and unit
execution took **35.205978 s**, with **1474.050176 s** physical
turnaround including queue time. No GPU performance measurement was
repeated.

## Validation of the previously synchronized source

The previously validated producer resolves all **46 shapes and seven
templates per architecture** with unchanged protocol semantics. All **19
delivered files per architecture** generated by the original adapter
match their recorded bytes. Generation and comparison took **3.558351
s** for SM100 and **3.445491 s** for SM103. The check used the measured
source plus the exact six changed files in the relevant dependency path.
This binds the original generated delivery; the later two-file
API/loader forwarding change is covered by the final package checks
below. GPU timings were not repeated.

Host validation finished with **374 unique tests passed and four
skipped**. The initial run passed 372 tests and exposed two missing
harness inputs; after repairing those inputs, only the two failed tests
were rerun and both passed. Initial pytest/process runtime was
**17.84/19.646297 s**, and the retry **5.15/5.933023 s**. Physical
turnaround was **261.376262 s** for the initial step and **74.034837 s**
for the retry. The original failed attempt remains recorded separately.

## Final combined package validation

The final package includes explicit backend forwarding and is built on
FlashInfer revision `dbb52c8a9775840fbfe229eb3b83543a59449b19`. The
recovered public commit is `34a30311cf6ed95a192e36058700ff2117ee7223`,
tree `7cc2d62dfb0ceab7b3384996a8be381c90cf2953`. All 32 packaged runtime
files were verified against the final composition, including 28
generated CUDA files, both architecture catalogs, the common loader and
public API. The performance matrices retain their original measured base
`f32f740ad2f228afa432c348904aef748f673ce3`.

| Final B300 / SM103 check | Result | Pytest runtime s | Process runtime
s |
| --- | --- | ---: | ---: |
| Pinned pre-commit hooks | 34 files passed, no changes | — | 7 |
| Wheel build | pass | — | 718.461875 |
| Checkout API | 12 passed, 81 deselected | 400.00 | 442.737793 |
| Wheel installation | pass | — | 76.603915 |
| Installed source/include/catalog discovery | pass | — | 5.786246 |
| Installed-wheel API | 12 passed, 81 deselected | 402.54 | 409.347554 |

Final package validation took **1653.158446 s**, composition plus
validation **1808.875369 s**, and physical turnaround **1991.341457 s**.
These are package/test durations, separate from GPU performance timing.
The final wheel SHA256 is
`e121bf3642a8919cddc326a1cccb0ec0c29d1a5e68ebd873d8b2dc9a309c89ed`.
Checkout and installed-package API checks on B200 passed with this exact
B300-built wheel, without rebuilding it.

### Final B200 / SM100 validation of the same wheel

B200 reused the exact B300-built wheel with SHA256
`e121bf3642a8919cddc326a1cccb0ec0c29d1a5e68ebd873d8b2dc9a309c89ed`. All
**32 packaged runtime files** match the final composition. The original
performance flags remain `all_performance_gates_passed=false` and
`performance_exception_accepted=true`.

| Final B200 / SM100 check | Result | Pytest runtime s | Process runtime
s |
| --- | --- | ---: | ---: |
| Checkout API | 12 passed, 81 deselected | 646.13 | 653.416701 |
| Same-wheel installation | pass, wheel reused | — | 71.561795 |
| Installed source/include/catalog discovery | pass | — | 4.878556 |
| Installed-wheel API | 12 passed, 81 deselected | 667.88 | 673.969898 |

Package validation took **1403.986691 s**, composition plus validation
**1570.214396 s**, and physical turnaround **1642.690739 s**. These
nested package/test durations are separate from the GPU performance
transactions and are not additive. No wheel rebuild or performance
measurement was repeated. The same final package is qualified on both
B200 and B300. The source correspondence review above supports reuse of
the source GPU gates while preserving the strict byte-identity failure.

All **34 public files** in the final transfer archive match recovered
commit `34a30311cf6ed95a192e36058700ff2117ee7223` exactly. It has the
same tree `7cc2d62dfb0ceab7b3384996a8be381c90cf2953` previously recorded
for historical commit `ecb38800107bf6168395c287d6b1b9bd96e8b812`, with
the final wheel hash unchanged. The checkout recovery preserved existing
qualification without repeating tests; the subsequent B200 checks below
qualify that same file tree and wheel on the second GPU. Archive
preparation took **1.761103 s** in-process and **60.964021 s**
physically. Both-architecture package/API qualification and source
correspondence review are complete.

## Historical package validation before explicit backend forwarding

The tested combined package was built on FlashInfer revision
`fb9612816ade4cf93f5a48cd5605da1c7879ec0e`; the performance matrices
below retain their measured base
`f32f740ad2f228afa432c348904aef748f673ce3`. Wheel construction,
installation, installed source/include discovery, and both scoped API
runs passed on B300. The wheel and installed package contain all 28
generated CUDA files, both architecture catalogs, the common JIT loader
and public API, with their expected bytes verified.

| B300 / SM103 check | Result | Pytest runtime s | Process runtime s |
| --- | --- | ---: | ---: |
| Wheel build | pass | — | 662.906001 |
| Checkout API | 12 passed, 81 deselected | 402.24 | 448.342788 |
| Wheel installation | pass | — | 64.396129 |
| Installed source/include/catalog discovery | pass | — | 6.631899 |
| Installed-wheel API | 12 passed, 81 deselected | 398.84 | 405.083937 |

The scoped API selection is `cake or backend_arch_support or
sm100_pooled_alpha_uses_first_element` in
`tests/gemm/test_nvfp4_svdquant_gemm.py`, using
`--import-mode=importlib`. Package validation took **1587.568805 s**,
composition plus validation **1725.025357 s**, and physical turnaround
**1781.820629 s**. These are package/test runtimes, separate from the
GPU timing transactions below. This preceding package has wheel SHA256
`919b7cfb92b919f4dcdd81b8ffd1c86881e88d77fcd3a8daa565945f59c718ad`; it
predates the backend-forwarding follow-up. It is superseded by the final
package above. B200 checkout and installed-package API validation used
the new final wheel and passed.

SM100 runtime sources were deterministically recovered and matched the
recorded hashes for all seven modules, the catalog, loader and API. The
original SM100 binary and raw archive are unavailable, so this
establishes source identity without claiming reconstructed binary
identity or a new performance measurement. Recovery took **10.216705 s**
in-process and **78.336634 s** physically. The SM103 delivery retains
its original generated-file records. Both original failed performance
verdicts and the exact accepted exceptions remain unchanged.

## Current 64 MiB full-matrix results — first complete attempts

Both selected 64 MiB matrices completed all 46 shapes and passed
correctness on every row; each passed 45/46 complete automated gate
sets. An explicit user-accepted exception applies only to the persistent
M129/N3072/K3072/rank96/bias tactic-25 CUTLASS comparison on SM100 and
SM103. That measured gap no longer blocks delivery. The original failed
gate values remain unchanged; the recorded runtime-source binding is
retained, and combined checkout/wheel API validation passed on B300 and
B200 using the same wheel; pre-commit checks passed.

Cold-L2 CUPTI; symmetric external CUDA Graphs; same-arm priming; three
counterbalanced groups, seed 344; 100 ms warmup and 200 ms reportable
budget per arm/group; 1900 MHz SM clock floor. All recorded thresholds
and denominators remain unchanged. The delivery acceptance exception is
limited to the one named CUTLASS comparison per architecture; both
below-floor rows remain in the full-denominator aggregates.

| GPU | Correct / completed | All gates passed | Measurement
transactions s | Runner s | Physical turnaround s |
| --- | ---: | ---: | ---: | ---: | ---: |
| NVIDIA B200 / SM100 | 46 / 46 | 45 / 46 | 8300.545440 | 8778.739862 |
8868.191509 |
| NVIDIA B300 SXM6 AC / SM103 | 46 / 46 | 45 / 46 | 9199.939530 |
9402.083315 | 9504.121605 |

| GPU | All-46 source geomean ms | All-46 export geomean ms | Source /
export | All-four CUTLASS geomean ms | Paired export geomean ms |
CUTLASS / export |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| SM100 | 0.048014620970 | 0.047879776551 | 1.002816313x |
0.010353928254 | 0.009716228597 | 1.065632426x |
| SM103 | 0.045933782736 | 0.045808321908 | 1.002738822x |
0.009856127808 | 0.009391928412 | 1.049425355x |

The failed persistent row measured source/export/CUTLASS
**8.672/8.608/8.480 us on SM100** (CUTLASS/export **0.985130112x**) and
**8.448/8.352/8.256 us on SM103** (**0.988505747x**). Direction and
endpoint-drift gates passed on both; CUTLASS endpoint drift was zero.
The recorded baseline floor remains 1.0x; these two exact-shape results
are accepted exceptions, with their original failing verdicts retained.

Every completed shape follows. A dash means no external comparison is
declared for that shape.

### SM100 — 46 shapes / seven templates

GPU: NVIDIA B200; driver 580.82.07. Public target revision:
`f32f740ad2f228afa432c348904aef748f673ce3`.

| Shape | Route | Source ms | Export ms | Source / export | CUTLASS ms |
CUTLASS / export | Correctness | Verdict |
| --- | --- | ---: | ---: | ---: | ---: | ---: | --- | --- |
| fixed_m129_n3072_k3072_r32_bias0_sm_100a |
tactic14_m128n64k128_cluster1x2 | 0.006655 | 0.006624 | 1.004680x |
0.007936 | 1.198068x | pass | pass |
| fixed_m129_n3072_k3072_r32_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011456 | 0.011488 | 0.997214x | —
| — | pass | pass |
| fixed_m129_n3072_k3072_r128_bias0_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011808 | 0.011744 | 1.005450x | —
| — | pass | pass |
| fixed_m129_n3072_k3072_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.012800 | 0.012833 | 0.997429x | —
| — | pass | pass |
| fixed_m129_n3072_k12288_r32_bias0_sm_100a | tactic18_2sm_m256n128k256
| 0.015327 | 0.015264 | 1.004127x | 0.015424 | 1.010482x | pass | pass |
| fixed_m129_n3072_k12288_r32_bias1_sm_100a | parent_tactic25_k12288_r32
| 0.025855 | 0.025760 | 1.003688x | — | — | pass | pass |
| fixed_m129_n3072_k12288_r128_bias0_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.026559 | 0.026560 | 0.999962x | —
| — | pass | pass |
| fixed_m129_n3072_k12288_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.027520 | 0.027328 | 1.007026x | —
| — | pass | pass |
| fixed_m6912_n3072_k3072_r32_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.089695 | 0.089791 | 0.998931x | —
| — | pass | pass |
| fixed_m6912_n3072_k3072_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.096543 | 0.096447 | 1.000995x | —
| — | pass | pass |
| fixed_m6912_n3072_k12288_r32_bias1_sm_100a |
parent_tactic25_k12288_r32 | 0.201726 | 0.201374 | 1.001748x | — | — |
pass | pass |
| fixed_m6912_n3072_k12288_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.236574 | 0.236382 | 1.000814x | —
| — | pass | pass |
| chunk_m129_n3072_k3072_r64_t0_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010400 | 0.010240 | 1.015625x
| 0.011072 | 1.081250x | pass | pass |
| chunk_m129_n3072_k3072_r64_t1_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010464 | 0.010528 | 0.993921x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r64_t19_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010495 | 0.010464 | 1.002963x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r64_t25_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010463 | 0.010304 | 1.015431x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t0_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009760 | 0.009920 |
0.983871x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t1_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009888 | 0.009728 |
1.016447x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t19_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009856 | 0.009728 |
1.013158x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t25_sm_100a |
tactic25_rank96_uniform_k64_persistent_raster_producer_control_warp_uniform
| 0.008672 | 0.008608 | 1.007435x | 0.008480 | 0.985130x | pass |
cutlass.baseline_over_export |
| chunk_m6912_n3072_k3072_r64_t0_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.085055 | 0.085023 | 1.000376x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t1_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.084800 | 0.084768 | 1.000378x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t19_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.084799 | 0.084864 | 0.999234x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t25_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.084639 | 0.084511 | 1.001515x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t0_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.076255 | 0.075583 |
1.008891x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t1_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.075871 | 0.075807 |
1.000844x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t19_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.076063 | 0.075551 |
1.006777x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t25_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.076159 | 0.075519 |
1.008475x | — | — | pass | pass |
| autotuned_m129_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011232 | 0.011135 | 1.008711x | —
| — | pass | pass |
| autotuned_m129_n3072_k3072_r96_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009920 | 0.009792 |
1.013072x | — | — | pass | pass |
| autotuned_m6912_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.089407 | 0.089503 | 0.998927x | —
| — | pass | pass |
| autotuned_m6912_n3072_k3072_r96_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.076063 | 0.075807 |
1.003377x | — | — | pass | pass |
| cuda_graph_m129_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011264 | 0.011296 | 0.997167x | —
| — | pass | pass |
| cuda_graph_m129_n3072_k3072_r128_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.012608 | 0.012640 | 0.997468x | —
| — | pass | pass |
| bench_m4096_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.058848 | 0.058815 | 1.000561x | —
| — | pass | pass |
| bench_m6889_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.089759 | 0.089567 | 1.002144x | —
| — | pass | pass |
| bench_m9216_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.116830 | 0.116543 | 1.002463x | —
| — | pass | pass |
| bench_m16384_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.199263 | 0.198910 | 1.001775x | —
| — | pass | pass |
| bench_m4096_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.201599 | 0.201182 | 1.002073x | —
| — | pass | pass |
| bench_m6889_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.329373 | 0.329309 | 1.000194x | —
| — | pass | pass |
| bench_m9216_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.435452 | 0.435324 | 1.000294x | —
| — | pass | pass |
| bench_m16384_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.757465 | 0.755993 | 1.001946x | —
| — | pass | pass |
| bench_m4096_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.133663 | 0.133599 | 1.000479x | — | — | pass | pass |
| bench_m6889_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.200222 | 0.200062 | 1.000800x | — | — | pass | pass |
| bench_m9216_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.263486 | 0.263134 | 1.001338x | — | — | pass | pass |
| bench_m16384_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.457180 | 0.457117 | 1.000139x | — | — | pass | pass |

**Complete denominator: true (46/46). Automated all-gates result: false
(45/46). Delivery accepts the single rank-96 CUTLASS exception.**

### SM103 — 46 shapes / seven templates

GPU: NVIDIA B300 SXM6 AC; driver 580.126.09. Public target revision:
`f32f740ad2f228afa432c348904aef748f673ce3`.

| Shape | Route | Source ms | Export ms | Source / export | CUTLASS ms |
CUTLASS / export | Correctness | Verdict |
| --- | --- | ---: | ---: | ---: | ---: | ---: | --- | --- |
| fixed_m129_n3072_k3072_r32_bias0_sm_103a |
tactic14_m128n64k128_cluster1x2 | 0.006464 | 0.006400 | 1.010000x |
0.007135 | 1.114844x | pass | pass |
| fixed_m129_n3072_k3072_r32_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011392 | 0.011296 | 1.008499x | —
| — | pass | pass |
| fixed_m129_n3072_k3072_r128_bias0_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.010048 | 0.010048 | 1.000000x | —
| — | pass | pass |
| fixed_m129_n3072_k3072_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011392 | 0.011392 | 1.000000x | —
| — | pass | pass |
| fixed_m129_n3072_k12288_r32_bias0_sm_103a | tactic18_2sm_m256n128k256
| 0.014816 | 0.014817 | 0.999933x | 0.014944 | 1.008571x | pass | pass |
| fixed_m129_n3072_k12288_r32_bias1_sm_103a | parent_tactic25_k12288_r32
| 0.022912 | 0.022785 | 1.005574x | — | — | pass | pass |
| fixed_m129_n3072_k12288_r128_bias0_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.024768 | 0.024800 | 0.998710x | —
| — | pass | pass |
| fixed_m129_n3072_k12288_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.026240 | 0.026145 | 1.003634x | —
| — | pass | pass |
| fixed_m6912_n3072_k3072_r32_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086496 | 0.086465 | 1.000359x | —
| — | pass | pass |
| fixed_m6912_n3072_k3072_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.093217 | 0.093089 | 1.001375x | —
| — | pass | pass |
| fixed_m6912_n3072_k12288_r32_bias1_sm_103a |
parent_tactic25_k12288_r32 | 0.196466 | 0.196290 | 1.000894x | — | — |
pass | pass |
| fixed_m6912_n3072_k12288_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.226370 | 0.226146 | 1.000991x | —
| — | pass | pass |
| chunk_m129_n3072_k3072_r64_t0_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009856 | 0.009824 | 1.003257x
| 0.010720 | 1.091205x | pass | pass |
| chunk_m129_n3072_k3072_r64_t1_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009856 | 0.009920 | 0.993548x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r64_t19_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009856 | 0.009921 | 0.993448x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r64_t25_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009856 | 0.009824 | 1.003257x
| — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t0_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009247 | 0.009248 |
0.999892x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t1_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009247 | 0.009152 |
1.010380x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t19_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009217 | 0.009152 |
1.007102x | — | — | pass | pass |
| chunk_m129_n3072_k3072_r96_t25_sm_103a |
tactic25_rank96_uniform_k64_persistent_raster_producer_control_warp_uniform
| 0.008448 | 0.008352 | 1.011494x | 0.008256 | 0.988506x | pass |
cutlass.baseline_over_export |
| chunk_m6912_n3072_k3072_r64_t0_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081761 | 0.081729 | 1.000392x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t1_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081825 | 0.081601 | 1.002745x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t19_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081793 | 0.081729 | 1.000783x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r64_t25_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081664 | 0.081409 | 1.003132x
| — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t0_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.073505 | 0.072800 |
1.009684x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t1_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.072929 | 0.072929 |
1.000000x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t19_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.073472 | 0.072768 |
1.009675x | — | — | pass | pass |
| chunk_m6912_n3072_k3072_r96_t25_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.073344 | 0.072704 |
1.008803x | — | — | pass | pass |
| autotuned_m129_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011137 | 0.011072 | 1.005871x | —
| — | pass | pass |
| autotuned_m129_n3072_k3072_r96_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009248 | 0.009248 |
1.000000x | — | — | pass | pass |
| autotuned_m6912_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086465 | 0.086305 | 1.001854x | —
| — | pass | pass |
| autotuned_m6912_n3072_k3072_r96_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.073184 | 0.073089 |
1.001300x | — | — | pass | pass |
| cuda_graph_m129_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011200 | 0.011200 | 1.000000x | —
| — | pass | pass |
| cuda_graph_m129_n3072_k3072_r128_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.012160 | 0.012000 | 1.013333x | —
| — | pass | pass |
| bench_m4096_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.056673 | 0.056640 | 1.000583x | —
| — | pass | pass |
| bench_m6889_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086561 | 0.086145 | 1.004829x | —
| — | pass | pass |
| bench_m9216_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.112609 | 0.112545 | 1.000569x | —
| — | pass | pass |
| bench_m16384_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.192930 | 0.192162 | 1.003997x | —
| — | pass | pass |
| bench_m4096_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.194850 | 0.194562 | 1.001480x | —
| — | pass | pass |
| bench_m6889_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.318307 | 0.318947 | 0.997993x | —
| — | pass | pass |
| bench_m9216_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.422501 | 0.421893 | 1.001442x | —
| — | pass | pass |
| bench_m16384_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.734985 | 0.732296 | 1.003672x | —
| — | pass | pass |
| bench_m4096_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.129345 | 0.129249 | 1.000743x | — | — | pass | pass |
| bench_m6889_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.195650 | 0.195490 | 1.000818x | — | — | pass | pass |
| bench_m9216_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.257699 | 0.257570 | 1.000501x | — | — | pass | pass |
| bench_m16384_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.446821 | 0.446885 | 0.999857x | — | — | pass | pass |

**Complete denominator: true (46/46). Automated all-gates result: false
(45/46). Delivery accepts the single rank-96 CUTLASS exception.**

## Historical sm_103a export qualification — 8 MiB

GPU: NVIDIA B300 SXM6 AC; driver 580.126.09. Public target revision:
`f32f740ad2f228afa432c348904aef748f673ce3`.

Cold-L2 CUPTI, `symmetric_external_cuda_graph`, 3 counterbalanced
groups; 100.000 ms warmup and 200.000 ms reportable budget per
arm/group. Same-arm priming: True.

Final runner: 9616.477 s. Final managed attempt: 9813.360 s. Cumulative
physical execution of 1 explicitly included managed attempts: 9813.360
s.

Reportable GPU execution across all final rows: 72.394507 s across all
arms (excludes priming, warmup, cold-cache flushes and host overhead).

## Per-shape results

| Shape | Route | Source ms | Export ms | Source / Export | Correctness
| Verdict |
|---|---|---:|---:|---:|---|---|
| fixed_m129_n3072_k3072_r32_bias0_sm_103a |
tactic14_m128n64k128_cluster1x2 | 0.006496 | 0.006432 | 1.009950x | pass
| pass |
| fixed_m129_n3072_k3072_r32_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011264 | 0.011232 | 1.002849x |
pass | pass |
| fixed_m129_n3072_k3072_r128_bias0_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.010432 | 0.010400 | 1.003077x |
pass | pass |
| fixed_m129_n3072_k3072_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011617 | 0.011680 | 0.994606x |
pass | pass |
| fixed_m129_n3072_k12288_r32_bias0_sm_103a | tactic18_2sm_m256n128k256
| 0.014816 | 0.014816 | 1.000000x | pass | pass |
| fixed_m129_n3072_k12288_r32_bias1_sm_103a | parent_tactic25_k12288_r32
| 0.023168 | 0.023072 | 1.004161x | pass | pass |
| fixed_m129_n3072_k12288_r128_bias0_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.024800 | 0.024832 | 0.998711x |
pass | pass |
| fixed_m129_n3072_k12288_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.026080 | 0.026048 | 1.001229x |
pass | pass |
| fixed_m6912_n3072_k3072_r32_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086497 | 0.086466 | 1.000359x |
pass | pass |
| fixed_m6912_n3072_k3072_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.093313 | 0.093057 | 1.002751x |
pass | pass |
| fixed_m6912_n3072_k12288_r32_bias1_sm_103a |
parent_tactic25_k12288_r32 | 0.197154 | 0.196930 | 1.001137x | pass |
pass |
| fixed_m6912_n3072_k12288_r128_bias1_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.227042 | 0.226722 | 1.001411x |
pass | pass |
| chunk_m129_n3072_k3072_r64_t0_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009889 | 0.009824 | 1.006616x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t1_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009920 | 0.009952 | 0.996785x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t19_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009824 | 0.009887 | 0.993628x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t25_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.009856 | 0.009792 | 1.006536x
| pass | pass |
| chunk_m129_n3072_k3072_r96_t0_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009312 | 0.009280 |
1.003448x | pass | pass |
| chunk_m129_n3072_k3072_r96_t1_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009248 | 0.009216 |
1.003472x | pass | pass |
| chunk_m129_n3072_k3072_r96_t19_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009281 | 0.009184 |
1.010562x | pass | pass |
| chunk_m129_n3072_k3072_r96_t25_sm_103a |
tactic25_rank96_uniform_k64_persistent_raster_producer_control_warp_uniform
| 0.008352 | 0.008256 | 1.011628x | pass | pass |
| chunk_m6912_n3072_k3072_r64_t0_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081760 | 0.081729 | 1.000379x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t1_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081696 | 0.081505 | 1.002343x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t19_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081632 | 0.081664 | 0.999608x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t25_sm_103a |
tactic0_rank64_bias_smem_row_broadcast | 0.081409 | 0.081281 | 1.001575x
| pass | pass |
| chunk_m6912_n3072_k3072_r96_t0_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.074369 | 0.073857 |
1.006932x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t1_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.073953 | 0.074688 |
0.990159x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t19_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.074144 | 0.074433 |
0.996117x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t25_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.074337 | 0.073793 |
1.007372x | pass | pass |
| autotuned_m129_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011041 | 0.010880 | 1.014798x |
pass | pass |
| autotuned_m129_n3072_k3072_r96_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009247 | 0.009248 |
0.999892x | pass | pass |
| autotuned_m6912_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086240 | 0.086209 | 1.000360x |
pass | pass |
| autotuned_m6912_n3072_k3072_r96_sm_103a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.074080 | 0.073985 |
1.001284x | pass | pass |
| cuda_graph_m129_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.011072 | 0.011040 | 1.002899x |
pass | pass |
| cuda_graph_m129_n3072_k3072_r128_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.012095 | 0.011936 | 1.013321x |
pass | pass |
| bench_m4096_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.056929 | 0.056833 | 1.001689x |
pass | pass |
| bench_m6889_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.086497 | 0.086241 | 1.002968x |
pass | pass |
| bench_m9216_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.112865 | 0.112705 | 1.001420x |
pass | pass |
| bench_m16384_n3072_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.192546 | 0.192146 | 1.002082x |
pass | pass |
| bench_m4096_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.194273 | 0.194113 | 1.000824x |
pass | pass |
| bench_m6889_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.318179 | 0.318691 | 0.998393x |
pass | pass |
| bench_m9216_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.420900 | 0.421380 | 0.998861x |
pass | pass |
| bench_m16384_n12288_k3072_r32_sm_103a |
parent_tactic0_n128_exact_epilogue | 0.737159 | 0.733447 | 1.005061x |
pass | pass |
| bench_m4096_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.129601 | 0.129217 | 1.002972x | pass | pass |
| bench_m6889_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.196353 | 0.195970 | 1.001954x | pass | pass |
| bench_m9216_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.258370 | 0.258402 | 0.999876x | pass | pass |
| bench_m16384_n3072_k12288_r32_sm_103a | parent_tactic25_k12288_r32 |
0.445060 | 0.445828 | 0.998277x | pass | pass |

## Per-shape comparison: FlashInfer CUTLASS SVDQuant backend

| Shape | Baseline ms | Paired export ms | Baseline / Export |
|---|---:|---:|---:|
| fixed_m129_n3072_k3072_r32_bias0_sm_103a | 0.007009 | 0.006432 |
1.089708x |
| fixed_m129_n3072_k12288_r32_bias0_sm_103a | 0.014944 | 0.014816 |
1.008639x |
| chunk_m129_n3072_k3072_r64_t0_sm_103a | 0.010657 | 0.009824 |
1.084792x |
| chunk_m129_n3072_k3072_r96_t25_sm_103a | 0.008256 | 0.008256 |
1.000000x |

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

| Shape tag | Timed rows | Denominator | Source ms | Export ms | Source
/ Export |
|---|---:|---:|---:|---:|---:|
| all | 46 | 46 | 0.046037 | 0.045933 | 1.002257x |
| all_tactics | 12 | 12 | 0.030738 | 0.030686 | 1.001681x |
| autotuned_benchmark | 12 | 12 | 0.206481 | 0.206234 | 1.001196x |
| autotuned_replay | 4 | 4 | 0.028419 | 0.028304 | 1.004064x |
| complete_denominator | 46 | 46 | 0.046037 | 0.045933 | 1.002257x |
| cuda_graph | 2 | 2 | 0.011572 | 0.011479 | 1.008096x |
| fixed_tactic | 16 | 16 | 0.027114 | 0.027051 | 1.002306x |
| declared baseline comparisons | 4 | 4 | 0.009442 | 0.009376 |
1.007039x |
| required | 14 | 14 | 0.044362 | 0.044236 | 1.002848x |
| sm_103a | 46 | 46 | 0.046037 | 0.045933 | 1.002257x |

### Geomeans: FlashInfer CUTLASS SVDQuant backend

| Shape tag | Timed rows | Denominator | Baseline ms | Paired export ms
| Baseline / Export |
|---|---:|---:|---:|---:|---:|
| all | 4 | 4 | 0.009798 | 0.009376 | 1.044956x |
| all_tactics | 2 | 2 | 0.010234 | 0.009762 | 1.048390x |
| complete_denominator | 4 | 4 | 0.009798 | 0.009376 | 1.044956x |
| fixed_tactic | 2 | 2 | 0.009380 | 0.009006 | 1.041534x |
| declared baseline comparisons | 4 | 4 | 0.009798 | 0.009376 |
1.044956x |
| required | 4 | 4 | 0.009798 | 0.009376 | 1.044956x |
| sm_103a | 4 | 4 | 0.009798 | 0.009376 | 1.044956x |

Complete denominator: **true** (46/46).

All gates passed: **true** (46/46).

## Historical SM100 export qualification — 8 MiB, first complete attempt

NVIDIA B200, driver 610.57.04. All 46 shapes completed and passed
correctness; 43 passed all gates. The three failures remain in every
applicable aggregate below. The persistent rank-96 row misses the 1.0x
CUTLASS floor; two large rows exceed the 2% endpoint-drift limit.

Runner runtime: 8934.440764 s; measurement phases: 8890.945308 s;
physical turnaround: 9048.584472 s. This is a nonqualifying attempt;
subsequent diagnostics do not replace these rows.

| Shape | Route | Source ms | Export ms | Source / Export | Correctness
| Verdict |
|---|---|---:|---:|---:|---|---|
| fixed_m129_n3072_k3072_r32_bias0_sm_100a |
tactic14_m128n64k128_cluster1x2 | 0.006880 | 0.006816 | 1.009390x | pass
| pass |
| fixed_m129_n3072_k3072_r32_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011936 | 0.011872 | 1.005391x |
pass | pass |
| fixed_m129_n3072_k3072_r128_bias0_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.010496 | 0.010496 | 1.000000x |
pass | pass |
| fixed_m129_n3072_k3072_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.012063 | 0.012032 | 1.002576x |
pass | pass |
| fixed_m129_n3072_k12288_r32_bias0_sm_100a | tactic18_2sm_m256n128k256
| 0.015487 | 0.015520 | 0.997874x | pass | pass |
| fixed_m129_n3072_k12288_r32_bias1_sm_100a | parent_tactic25_k12288_r32
| 0.023712 | 0.023648 | 1.002706x | pass | pass |
| fixed_m129_n3072_k12288_r128_bias0_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.025600 | 0.025665 | 0.997467x |
pass | pass |
| fixed_m129_n3072_k12288_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.027168 | 0.027231 | 0.997686x |
pass | pass |
| fixed_m6912_n3072_k3072_r32_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.089983 | 0.090143 | 0.998225x |
pass | pass |
| fixed_m6912_n3072_k3072_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.096255 | 0.096671 | 0.995697x |
pass | pass |
| fixed_m6912_n3072_k12288_r32_bias1_sm_100a |
parent_tactic25_k12288_r32 | 0.199934 | 0.199775 | 1.000796x | pass |
pass |
| fixed_m6912_n3072_k12288_r128_bias1_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.235678 | 0.235134 | 1.002314x |
pass | pass |
| chunk_m129_n3072_k3072_r64_t0_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010272 | 0.010304 | 0.996894x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t1_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010304 | 0.010304 | 1.000000x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t19_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010272 | 0.010272 | 1.000000x
| pass | pass |
| chunk_m129_n3072_k3072_r64_t25_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.010272 | 0.010304 | 0.996894x
| pass | pass |
| chunk_m129_n3072_k3072_r96_t0_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009792 | 0.009728 |
1.006579x | pass | pass |
| chunk_m129_n3072_k3072_r96_t1_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009856 | 0.009728 |
1.013158x | pass | pass |
| chunk_m129_n3072_k3072_r96_t19_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009792 | 0.009760 |
1.003279x | pass | pass |
| chunk_m129_n3072_k3072_r96_t25_sm_100a |
tactic25_rank96_uniform_k64_persistent_raster_producer_control_warp_uniform
| 0.008992 | 0.008960 | 1.003571x | pass | cutlass.baseline_over_export
|
| chunk_m6912_n3072_k3072_r64_t0_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.085376 | 0.085503 | 0.998515x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t1_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.085375 | 0.085375 | 1.000000x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t19_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.085311 | 0.085280 | 1.000364x
| pass | pass |
| chunk_m6912_n3072_k3072_r64_t25_sm_100a |
tactic0_rank64_bias_smem_row_broadcast | 0.085215 | 0.085215 | 1.000000x
| pass | pass |
| chunk_m6912_n3072_k3072_r96_t0_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.077183 | 0.077471 |
0.996282x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t1_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.077119 | 0.076575 |
1.007104x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t19_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.077407 | 0.077247 |
1.002071x | pass | pass |
| chunk_m6912_n3072_k3072_r96_t25_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.077119 | 0.076927 |
1.002496x | pass | pass |
| autotuned_m129_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011519 | 0.011392 | 1.011148x |
pass | pass |
| autotuned_m129_n3072_k3072_r96_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.009760 | 0.009696 |
1.006601x | pass | pass |
| autotuned_m6912_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.089951 | 0.090016 | 0.999278x |
pass | pass |
| autotuned_m6912_n3072_k3072_r96_sm_100a |
tactic25_rank96_compact_tail_bias_smem_vec | 0.077087 | 0.077375 |
0.996278x | pass | pass |
| cuda_graph_m129_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011552 | 0.011424 | 1.011204x |
pass | pass |
| cuda_graph_m129_n3072_k3072_r128_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.011968 | 0.011936 | 1.002681x |
pass | pass |
| bench_m4096_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.058912 | 0.058847 | 1.001105x |
pass | pass |
| bench_m6889_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.090175 | 0.090047 | 1.001421x |
pass | pass |
| bench_m9216_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.117535 | 0.117439 | 1.000817x |
pass | endpoint_drift |
| bench_m16384_n3072_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.200351 | 0.200351 | 1.000000x |
pass | pass |
| bench_m4096_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.202719 | 0.202495 | 1.001106x |
pass | pass |
| bench_m6889_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.331038 | 0.330478 | 1.001695x |
pass | pass |
| bench_m9216_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.436541 | 0.436029 | 1.001174x |
pass | pass |
| bench_m16384_n12288_k3072_r32_sm_100a |
parent_tactic0_n128_exact_epilogue | 0.759675 | 0.758876 | 1.001052x |
pass | pass |
| bench_m4096_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.132575 | 0.132447 | 1.000966x | pass | endpoint_drift |
| bench_m6889_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.199039 | 0.199199 | 0.999197x | pass | pass |
| bench_m9216_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.261887 | 0.261759 | 1.000487x | pass | pass |
| bench_m16384_n3072_k12288_r32_sm_100a | parent_tactic25_k12288_r32 |
0.463837 | 0.463069 | 1.001659x | pass | pass |

| Declared CUTLASS comparison | Baseline ms | Paired export ms |
Baseline / Export |
|---|---:|---:|---:|
| fixed_m129_n3072_k3072_r32_bias0_sm_100a | 0.007328 | 0.006816 |
1.075117x |
| fixed_m129_n3072_k12288_r32_bias0_sm_100a | 0.015776 | 0.015520 |
1.016495x |
| chunk_m129_n3072_k3072_r64_t0_sm_100a | 0.011328 | 0.010304 |
1.099379x |
| chunk_m129_n3072_k3072_r96_t25_sm_100a | 0.008672 | 0.008960 |
0.967857x |

All 46 source/export geomeans: **0.047839331 / 0.047761623 ms,
1.001627x**. Four declared CUTLASS/export geomeans: **0.010323185 /
0.009941085 ms, 1.038436x**. These include the failing rows.

Endpoint drift: M9216/N3072/K3072/rank32 **2.316933%**;
M4096/N3072/K12288/rank32 **3.239870%**. Both endpoints slow together.
The three recorded group clocks are 1965 MHz; these snapshots do not
establish the cause of within-group drift.

The recorded runtime-source binding is retained. Combined checkout/wheel
API validation passed on B300 and B200 using the same final wheel;
pre-commit checks passed. The accepted rank-96 performance exception
requires no further tuning.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added explicit Cake backend support for NVFP4 SVDQuant GEMM on SM100
and SM103 GPUs.
* Added automatic kernel selection, workspace management, and launch
support for supported problem shapes.
  * Added optional bias handling and optimized fused computation paths.

* **Bug Fixes**
* Improved input validation for tensor layouts, devices, data types,
dimensions, and workspace requirements.
  * Ensured trailing padding in scale buffers does not affect results.

* **Tests**
* Added coverage for backend architecture support and CUDA Graph
capture/replay.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [dbc88cf](https://github.com/flashinfer-ai/flashinfer/commit/dbc88cf86571d2c01f8f67415789097839beaa52)

- **作者**: eigen
- **时间**: 2026-09-10T08:04:55Z
- **提交信息**: feat(cake_warp_decode): Add SM100 NVFP4 warp decode and standalone SiLU (#5036)

This adds exact SM100 support to NVFP4 warp decode while preserving the
SM103 production contract, and adds standalone SiLU alongside default
SwiGLU
through the public API, dispatch, generated programs, and GPU
validation.
`CakeWarpDecodeConfig(backend="cake")` selects the backend. The shuffled
MajorK
weight layout, R128c4 block scales, caller-owned output/workspace, and
CUDA
Graph lifecycle remain supported. SwiGLU GEMM1 weights use `[E, 2 * I,
H]`;
standalone SiLU uses `[E, I, H]`.

SM100 SwiGLU E60/H2048/I1536/top-k4 retains GPU expert packing for
T20–T32,
including packing in the complete timed pipeline. The repaired FC2
factory
is used by all 96 SM100 routes. The canonical
`export-generated-programs`
output contains 73 generated files,
27 modules and 17 sequences,
covering all 192 public routes.

The current matrix combines 96 new B200 measurements with 96 retained
B300
measurements. All 192 meet correctness, source/export fidelity, timing
and
clock requirements. Source/export geomean (range) is
**0.998549× (0.975995–1.017915×)**. Across the 128 applicable
SwiGLU comparisons, official/export is
**1.090404× (0.928586–1.321875×)**.
There are 6 official regressions;
all remain included. Standalone SiLU has no matching official baseline
and
reports N/A. The previous 96 SM100 measurements and 13 earlier
superseded
measurements remain below as history with their original cohorts.

The SM100 N8/K256 FC2 factory now rejoins the elected
cluster-launch-control
issuer with its warp before consuming the response. Its TMEM allocation
rendezvous includes all 16 warps, covering every reader of the shared
allocation address. The repair is limited to this factory. Direct
comparison
of source-factory CUDA found the four SM103 production FC2 variants
unchanged;
source launch options, symbols and block dimensions also remain
unchanged.
The exporter refreshed content identities and generated symbol names for
the
five FC2 factories and their sequence bindings. Binary equivalence was
not
assessed.

The repaired source passed 9 unit tests, 2 policy checks, 8 GPU
end-to-end
tests, and both registered E60/T20 and E60/T32 CUPTI benchmark
regressions.
Source validation took 99.286 s in the worker and 106.138 s physically.

The registered E60/T32 sanitizer launcher exercises route packing, FC1
device
workfeed, FC2 K256 and the packed finalizer. It uses a fresh physical
fixture
and independently computed FP4 reference, with fixture seed 4106. Cached
fixture/reference preparation preserves the instrumented launches and
output
comparison. Synccheck passed in 27.469 s with 0 reported errors;
racecheck
passed in 32.935 s with 0 reported errors. Each reported zero mismatches
and
maximum absolute error zero. Fresh
fixture preparation plus both tools took 83.681 s in the worker and
137.533 s
physically.

Earlier racecheck attempts on the unrepaired implementation timed out at
the
300 s and 900 s limits. The newer-tool retry also timed out. A
scheduler-only
diagnostic completed and exposed the shared TMEM allocation-address
race.
Those unsuccessful results remain historical evidence; the repaired
source
passed both complete registered sanitizer commands.

| Compute Sanitizer | Repaired-source result |
|---|---|
| synccheck | Passed, 0 reported sanitizer errors; 0 FP4 mismatches, max
absolute error 0; 27.469 s |
| racecheck | Passed, 0 reported sanitizer errors; 0 FP4 mismatches, max
absolute error 0; 32.935 s |

Public commit `3a82ec37d572aa59f7b5468c057f8b58ecb29048`:
[scoped](https://github.com/flashinfer-ai/flashinfer/actions/runs/34438123334)
cancelled;
[pre-commit](https://github.com/flashinfer-ai/flashinfer/actions/runs/34438067541)
success;
[documentation](https://github.com/flashinfer-ai/flashinfer/actions/runs/34438067571)
success.

Across 3 formal worker attempt(s), measurement phases totaled
6,784.659 s and workers totaled
7,070.909 s. Physical turnaround for these formal
campaign attempts was 7,330.945 s.
Separate diagnostic work took 56.127 s runtime and 218.756 s physical
turnaround; it contributes no primary benchmark latency. The retained
B300 measurement bracket was 6,374.569 s with 6,556 s physical
turnaround.
These host durations are separate from the CUPTI kernel latencies below.

The first formal campaign submission to the final formal confirmation
completed
in 8,774.059 s (146.234 min), including the diagnostic and orchestration
gaps.
The attempt totals above sum the actual individual executions.

The original T07 capture failure and SiLU T1 fidelity failure remain in
the
attempt table. T07 passed its single formal retry. One predeclared SiLU
T1
confirmation used the unchanged formal worker and protocol, including
the
original graph capture order, three 100 ms groups and clock checks. It
measured
21.344 / 21.472 µs source/export (0.994039), with all three group clocks
at
1965 MHz. The original 21.504 / 22.465 µs result (0.957222) remains
disclosed;
its earlier timing discrepancy was not reproduced and its cause was not
established.

CI acceptance remains incomplete: the scoped public workflow was
cancelled,
and the additional B200 CUDA 12.9/13.0 CI jobs have not reached tests
because
runner credential retrieval and then account admission failed. These are
pre-test infrastructure failures; no test-source change was made for
them.


## Performance evidence

Measured 192/192 public routes; 192 rows qualify for correctness,
source/export fidelity, and timing. 186 rows pass every frozen legacy
gate.

Qualification retains source/export ≥0.97, directional disagreement and
endpoint drift ≤2% for both comparisons, physical NVFP4 correctness
(atol=1.0, rtol=0.1), and SM clock ≥1900 MHz. The frozen legacy
official/export ≥1 gate is disclosed separately; ratios below 1 are
regressions. Every completed row is included without pass-based
selection. Standalone SiLU has no official baseline (N/A).

Method: CUPTI bench_gpu_time, cold L2, symmetric external CUDA Graphs,
seed 28301, three counterbalanced groups, 50 ms warmup per arm/group;
P500 rows use 500 ms and P100 rows use 100 ms measurement per arm/group,
prime_before_each=true.

| Scope | Group | Rows | Source/export geomean (range) | Worst source
row | Official/export geomean (range) | Worst official row |
|---|---|---:|---|---|---|---|
| overall | all | 192 | 0.998549× (0.975995–1.017915) |
sm100a_silu_e192_h6144_i1536_k4_t05 (0.975995×) | 1.090404×
(0.928586–1.321875) | sm100a_swiglu_e512_h2048_i512_k10_t32 (0.928586×)
|
| architecture | sm_100a | 96 | 0.998380× (0.975995–1.017915) |
sm100a_silu_e192_h6144_i1536_k4_t05 (0.975995×) | 1.082306×
(0.928586–1.293808) | sm100a_swiglu_e512_h2048_i512_k10_t32 (0.928586×)
|
| architecture | sm_103a | 96 | 0.998717× (0.984189–1.014085) |
sm103a_swiglu_e512_h2048_i512_k10_t01 (0.984189×) | 1.098563×
(1.012723–1.321875) | sm103a_swiglu_e512_h2048_i512_k10_t32 (1.012723×)
|
| geometry | swiglu_e512_h2048_i512_k10 | 64 | 0.997878×
(0.980469–1.017915) | sm100a_swiglu_e512_h2048_i512_k10_t01 (0.980469×)
| 1.042524× (0.928586–1.144951) | sm100a_swiglu_e512_h2048_i512_k10_t32
(0.928586×) |
| geometry_architecture | sm_100a:swiglu_e512_h2048_i512_k10 | 32 |
0.998430× (0.980469–1.017915) | sm100a_swiglu_e512_h2048_i512_k10_t01
(0.980469×) | 1.036503× (0.928586–1.144951) |
sm100a_swiglu_e512_h2048_i512_k10_t32 (0.928586×) |
| geometry_architecture | sm_103a:swiglu_e512_h2048_i512_k10 | 32 |
0.997327× (0.984189–1.011801) | sm103a_swiglu_e512_h2048_i512_k10_t01
(0.984189×) | 1.048580× (1.012723–1.121113) |
sm103a_swiglu_e512_h2048_i512_k10_t32 (1.012723×) |
| geometry | swiglu_e60_h2048_i1536_k4 | 64 | 0.999203×
(0.985772–1.014085) | sm100a_swiglu_e60_h2048_i1536_k4_t05 (0.985772×) |
1.140483× (1.023220–1.321875) | sm100a_swiglu_e60_h2048_i1536_k4_t19
(1.023220×) |
| geometry_architecture | sm_100a:swiglu_e60_h2048_i1536_k4 | 32 |
0.998216× (0.985772–1.008410) | sm100a_swiglu_e60_h2048_i1536_k4_t05
(0.985772×) | 1.130133× (1.023220–1.293808) |
sm100a_swiglu_e60_h2048_i1536_k4_t19 (1.023220×) |
| geometry_architecture | sm_103a:swiglu_e60_h2048_i1536_k4 | 32 |
1.000192× (0.988007–1.014085) | sm103a_swiglu_e60_h2048_i1536_k4_t16
(0.988007×) | 1.150928× (1.099370–1.321875) |
sm103a_swiglu_e60_h2048_i1536_k4_t16 (1.099370×) |
| geometry | silu_e192_h6144_i1536_k4 | 64 | 0.998565×
(0.975995–1.008046) | sm100a_silu_e192_h6144_i1536_k4_t05 (0.975995×) |
N/A | N/A |
| geometry_architecture | sm_100a:silu_e192_h6144_i1536_k4 | 32 |
0.998494× (0.975995–1.007729) | sm100a_silu_e192_h6144_i1536_k4_t05
(0.975995×) | N/A | N/A |
| geometry_architecture | sm_103a:silu_e192_h6144_i1536_k4 | 32 |
0.998635× (0.991116–1.008046) | sm103a_silu_e192_h6144_i1536_k4_t06
(0.991116×) | N/A | N/A |

| Shape | Cohort | Source µs | Export µs | Source/export | Official µs |
Paired export µs | Official/export | Qualified | Legacy all gates |
|---|---|---:|---:|---:|---:|---:|---:|---|---|
| sm100a_swiglu_e512_h2048_i512_k10_t01 | B200-P100-repair | 16.064 |
16.384 | 0.980469× | 17.792 | 16.384 | 1.085938× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t02 | B200-P100-repair | 20.000 |
19.648 | 1.017915× | 22.496 | 19.648 | 1.144951× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t03 | B200-P100-repair | 23.552 |
23.489 | 1.002682× | 25.729 | 23.489 | 1.095364× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t04 | B200-P100-repair | 27.392 |
27.808 | 0.985040× | 30.144 | 27.808 | 1.084005× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t05 | B200-P100-repair | 30.400 |
30.560 | 0.994764× | 33.568 | 30.560 | 1.098429× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t06 | B200-P100-repair | 34.176 |
34.432 | 0.992565× | 36.704 | 34.432 | 1.065985× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t07 | B200-P100-repair | 36.704 |
36.800 | 0.997391× | 38.752 | 36.800 | 1.053043× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t08 | B200-P100-repair | 39.520 |
38.913 | 1.015599× | 40.897 | 38.913 | 1.050986× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t09 | B200-P100-repair | 41.760 |
41.952 | 0.995423× | 44.288 | 41.952 | 1.055683× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t10 | B200-P100-repair | 44.609 |
44.896 | 0.993607× | 46.720 | 44.896 | 1.040627× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t11 | B200-P100-repair | 46.976 |
47.232 | 0.994580× | 48.736 | 47.232 | 1.031843× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t12 | B200-P100-repair | 49.312 |
49.312 | 1.000000× | 50.496 | 49.312 | 1.024010× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t13 | B200-P100-repair | 51.712 |
51.808 | 0.998147× | 53.216 | 51.808 | 1.027177× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t14 | B200-P100-repair | 54.241 |
54.560 | 0.994153× | 55.936 | 54.560 | 1.025220× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t15 | B200-P100-repair | 57.120 |
57.664 | 0.990566× | 59.168 | 57.664 | 1.026082× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t16 | B200-P100-repair | 60.032 |
59.872 | 1.002672× | 61.952 | 59.872 | 1.034741× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t17 | B200-P100-repair | 61.952 |
62.049 | 0.998437× | 66.560 | 62.049 | 1.072701× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t18 | B200-P100-repair | 64.480 |
64.672 | 0.997031× | 68.897 | 64.672 | 1.065330× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t19 | B200-P100-repair | 66.528 |
66.784 | 0.996167× | 71.296 | 66.784 | 1.067561× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t20 | B200-P100-repair | 68.608 |
68.735 | 0.998152× | 72.896 | 68.735 | 1.060537× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t21 | B200-P100-repair | 70.976 |
70.848 | 1.001807× | 74.624 | 70.848 | 1.053297× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t22 | B200-P100-repair | 73.088 |
72.896 | 1.002634× | 75.872 | 72.896 | 1.040825× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t23 | B200-P100-repair | 75.008 |
74.816 | 1.002566× | 77.632 | 74.816 | 1.037639× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t24 | B200-P100-repair | 76.960 |
76.768 | 1.002501× | 79.136 | 76.768 | 1.030846× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t25 | B200-P100-repair | 79.392 |
79.104 | 1.003641× | 80.896 | 79.104 | 1.022654× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t26 | B200-P100-repair | 81.953 |
81.728 | 1.002753× | 82.304 | 81.728 | 1.007048× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t27 | B200-P100-repair | 84.097 |
84.192 | 0.998872× | 83.648 | 84.192 | 0.993539× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t28 | B200-P100-repair | 86.273 |
86.208 | 1.000754× | 84.352 | 86.208 | 0.978471× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t29 | B200-P100-repair | 88.704 |
88.896 | 0.997840× | 86.784 | 88.896 | 0.976242× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t30 | B200-P100-repair | 90.560 |
90.816 | 0.997187× | 87.360 | 90.816 | 0.961950× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t31 | B200-P100-repair | 92.768 |
92.896 | 0.998622× | 88.960 | 92.896 | 0.957630× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t32 | B200-P100-repair | 95.072 |
95.457 | 0.995967× | 88.640 | 95.457 | 0.928586× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t01 | B200-P100-repair | 15.647 |
15.584 | 1.004043× | 16.320 | 15.584 | 1.047228× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t02 | B200-P100-repair | 18.880 |
19.040 | 0.991597× | 20.800 | 19.040 | 1.092437× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t03 | B200-P100-repair | 24.256 |
24.288 | 0.998682× | 31.424 | 24.288 | 1.293808× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t04 | B200-P100-repair | 27.520 |
27.488 | 1.001164× | 34.976 | 27.488 | 1.272410× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t05 | B200-P100-repair | 31.040 |
31.488 | 0.985772× | 38.112 | 31.488 | 1.210366× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t06 | B200-P100-repair | 33.184 |
33.248 | 0.998075× | 39.328 | 33.248 | 1.182868× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t07 | B200-P100-repair | 35.712 |
36.000 | 0.992000× | 42.528 | 36.000 | 1.181333× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t08 | B200-P100-repair | 38.368 |
38.048 | 1.008410× | 44.704 | 38.048 | 1.174937× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t09 | B200-P100-repair | 40.736 |
41.184 | 0.989122× | 47.168 | 41.184 | 1.145299× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t10 | B200-P100-repair | 42.720 |
42.720 | 1.000000× | 49.505 | 42.720 | 1.158813× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t11 | B200-P100-repair | 44.897 |
45.184 | 0.993648× | 52.160 | 45.184 | 1.154391× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t12 | B200-P100-repair | 48.576 |
48.576 | 1.000000× | 55.904 | 48.576 | 1.150856× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t13 | B200-P100-repair | 50.272 |
50.624 | 0.993047× | 56.160 | 50.624 | 1.109355× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t14 | B200-P100-repair | 52.896 |
52.992 | 0.998188× | 59.520 | 52.992 | 1.123188× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t15 | B200-P100-repair | 55.168 |
55.360 | 0.996532× | 61.120 | 55.360 | 1.104046× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t16 | B200-P100-repair | 57.120 |
57.216 | 0.998322× | 62.272 | 57.216 | 1.088367× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t17 | B200-P100-repair | 58.560 |
58.784 | 0.996189× | 63.232 | 58.784 | 1.075667× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t18 | B200-P100-repair | 60.129 |
60.448 | 0.994723× | 63.488 | 60.448 | 1.050291× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t19 | B200-P100-repair | 61.568 |
62.016 | 0.992776× | 63.456 | 62.016 | 1.023220× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t20 | B200-P100-repair | 57.953 |
57.888 | 1.001123× | 64.416 | 57.888 | 1.112769× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t21 | B200-P100-repair | 59.584 |
59.232 | 1.005943× | 66.401 | 59.232 | 1.121033× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t22 | B200-P100-repair | 59.424 |
59.776 | 0.994111× | 66.208 | 59.776 | 1.107602× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t23 | B200-P100-repair | 59.904 |
59.808 | 1.001605× | 66.080 | 59.808 | 1.104869× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t24 | B200-P100-repair | 60.480 |
60.416 | 1.001059× | 67.329 | 60.416 | 1.114423× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t25 | B200-P100-repair | 61.344 |
61.440 | 0.998437× | 68.416 | 61.440 | 1.113542× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t26 | B200-P100-repair | 63.008 |
62.912 | 1.001526× | 70.688 | 62.912 | 1.123601× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t27 | B200-P100-repair | 64.415 |
64.736 | 0.995041× | 72.800 | 64.736 | 1.124567× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t28 | B200-P100-repair | 65.600 |
65.345 | 1.003902× | 73.856 | 65.345 | 1.130247× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t29 | B200-P100-repair | 65.440 |
65.248 | 1.002943× | 73.824 | 65.248 | 1.131437× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t30 | B200-P100-repair | 66.176 |
66.112 | 1.000976× | 74.528 | 66.112 | 1.127308× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t31 | B200-P100-repair | 66.432 |
66.240 | 1.002899× | 74.720 | 66.240 | 1.128019× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t32 | B200-P100-repair | 66.272 |
66.176 | 1.001451× | 74.625 | 66.176 | 1.127675× | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t01 | B200-P100-repair | 21.344 |
21.472 | 0.994039× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t02 | B200-P100-repair | 29.248 |
29.248 | 1.000000× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t03 | B200-P100-repair | 35.072 |
35.360 | 0.991855× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t04 | B200-P100-repair | 43.328 |
43.648 | 0.992669× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t05 | B200-P100-repair | 49.440 |
50.656 | 0.975995× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t06 | B200-P100-repair | 56.896 |
56.864 | 1.000563× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t07 | B200-P100-repair | 64.352 |
64.480 | 0.998015× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t08 | B200-P100-repair | 70.400 |
70.752 | 0.995025× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t09 | B200-P100-repair | 76.480 |
76.704 | 0.997080× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t10 | B200-P100-repair | 82.368 |
82.177 | 1.002324× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t11 | B200-P100-repair | 88.416 |
88.416 | 1.000000× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t12 | B200-P100-repair | 94.656 |
94.592 | 1.000677× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t13 | B200-P100-repair | 100.224 |
99.457 | 1.007712× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t14 | B200-P100-repair | 105.152 |
105.505 | 0.996654× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t15 | B200-P100-repair | 112.352 |
112.320 | 1.000285× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t16 | B200-P100-repair | 116.416 |
116.513 | 0.999167× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t17 | B200-P100-repair | 121.121 |
120.192 | 1.007729× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t18 | B200-P100-repair | 126.080 |
127.232 | 0.990946× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t19 | B200-P100-repair | 132.193 |
132.417 | 0.998308× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t20 | B200-P100-repair | 138.017 |
137.569 | 1.003257× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t21 | B200-P100-repair | 142.432 |
142.560 | 0.999102× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t22 | B200-P100-repair | 148.640 |
149.057 | 0.997202× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t23 | B200-P100-repair | 152.512 |
152.384 | 1.000840× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t24 | B200-P100-repair | 157.329 |
157.408 | 0.999495× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t25 | B200-P100-repair | 162.496 |
162.689 | 0.998814× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t26 | B200-P100-repair | 168.865 |
169.216 | 0.997926× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t27 | B200-P100-repair | 175.136 |
175.008 | 1.000731× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t28 | B200-P100-repair | 180.256 |
180.513 | 0.998579× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t29 | B200-P100-repair | 186.400 |
186.177 | 1.001198× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t30 | B200-P100-repair | 190.241 |
190.241 | 1.000000× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t31 | B200-P100-repair | 194.321 |
193.697 | 1.003219× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t32 | B200-P100-repair | 199.489 |
198.913 | 1.002896× | N/A | N/A | N/A | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t01 | B300-P500 | 15.873 | 16.128 |
0.984189× | 17.376 | 16.128 | 1.077381× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t02 | B300-P500 | 19.264 | 19.296 |
0.998342× | 21.633 | 19.296 | 1.121113× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t03 | B300-P500 | 22.880 | 22.977 |
0.995778× | 25.184 | 22.977 | 1.096053× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t04 | B300-P500 | 27.521 | 27.200 |
1.011801× | 28.992 | 27.200 | 1.065882× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t05 | B300-P500 | 30.016 | 30.144 |
0.995754× | 32.544 | 30.144 | 1.079618× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t06 | B300-P500 | 33.663 | 34.080 |
0.987779× | 36.257 | 34.080 | 1.063879× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t07 | B300-P500 | 36.128 | 36.384 |
0.992964× | 38.816 | 36.384 | 1.066843× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t08 | B300-P500 | 39.009 | 39.393 |
0.990252× | 41.376 | 39.393 | 1.050339× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t09 | B300-P500 | 41.953 | 41.696 |
1.006164× | 44.320 | 41.696 | 1.062932× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t10 | B300-P500 | 44.736 | 44.864 |
0.997147× | 47.041 | 44.864 | 1.048524× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t11 | B300-P500 | 46.945 | 47.072 |
0.997302× | 49.025 | 47.072 | 1.041490× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t12 | B300-P500 | 49.313 | 49.216 |
1.001971× | 50.977 | 49.216 | 1.035781× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t13 | B300-P500 | 51.809 | 51.840 |
0.999402× | 53.440 | 51.840 | 1.030864× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t14 | B300-P500 | 54.497 | 54.400 |
1.001783× | 55.905 | 54.400 | 1.027665× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t15 | B300-P500 | 57.344 | 57.472 |
0.997773× | 59.072 | 57.472 | 1.027840× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t16 | B300-P500 | 60.161 | 60.193 |
0.999468× | 61.441 | 60.193 | 1.020733× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t17 | B300-P500 | 62.208 | 62.145 |
1.001014× | 66.560 | 62.145 | 1.071044× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t18 | B300-P500 | 64.608 | 64.577 |
1.000480× | 68.929 | 64.577 | 1.067392× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t19 | B300-P500 | 66.688 | 66.401 |
1.004322× | 71.170 | 66.401 | 1.071821× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t20 | B300-P500 | 68.897 | 68.768 |
1.001876× | 73.057 | 68.768 | 1.062369× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t21 | B300-P500 | 71.136 | 71.264 |
0.998204× | 74.176 | 71.264 | 1.040862× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t22 | B300-P500 | 72.961 | 73.377 |
0.994331× | 76.417 | 73.377 | 1.041430× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t23 | B300-P500 | 74.624 | 73.985 |
1.008637× | 76.705 | 73.985 | 1.036764× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t24 | B300-P500 | 76.545 | 76.545 |
1.000000× | 78.721 | 76.545 | 1.028428× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t25 | B300-P500 | 78.113 | 79.073 |
0.987859× | 81.313 | 79.073 | 1.028328× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t26 | B300-P500 | 79.392 | 79.521 |
0.998378× | 82.881 | 79.521 | 1.042253× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t27 | B300-P500 | 80.833 | 81.121 |
0.996450× | 84.032 | 81.121 | 1.035885× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t28 | B300-P500 | 81.345 | 82.113 |
0.990647× | 84.481 | 82.113 | 1.028838× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t29 | B300-P500 | 83.744 | 84.577 |
0.990151× | 86.048 | 84.577 | 1.017392× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t30 | B300-P500 | 84.449 | 84.833 |
0.995473× | 88.353 | 84.833 | 1.041493× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t31 | B300-P500 | 86.049 | 86.785 |
0.991519× | 88.480 | 86.785 | 1.019531× | True | True |
| sm103a_swiglu_e512_h2048_i512_k10_t32 | B300-P500 | 87.841 | 88.033 |
0.997819× | 89.153 | 88.033 | 1.012723× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t01 | B300-P500 | 13.824 | 13.632 |
1.014085× | 17.152 | 13.632 | 1.258216× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t02 | B300-P500 | 18.464 | 18.369 |
1.005172× | 21.184 | 18.369 | 1.153247× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t03 | B300-P500 | 23.201 | 23.360 |
0.993193× | 30.879 | 23.360 | 1.321875× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t04 | B300-P500 | 26.976 | 26.912 |
1.002378× | 35.105 | 26.912 | 1.304437× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t05 | B300-P500 | 30.528 | 30.496 |
1.001049× | 38.240 | 30.496 | 1.253935× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t06 | B300-P500 | 32.864 | 32.736 |
1.003910× | 39.712 | 32.736 | 1.213099× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t07 | B300-P500 | 35.328 | 35.168 |
1.004550× | 42.720 | 35.168 | 1.214741× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t08 | B300-P500 | 37.441 | 37.280 |
1.004319× | 44.865 | 37.280 | 1.203460× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t09 | B300-P500 | 39.840 | 40.000 |
0.996000× | 47.488 | 40.000 | 1.187200× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t10 | B300-P500 | 42.433 | 42.561 |
0.996993× | 49.537 | 42.561 | 1.163906× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t11 | B300-P500 | 44.960 | 44.929 |
1.000690× | 52.352 | 44.929 | 1.165216× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t12 | B300-P500 | 48.769 | 48.833 |
0.998689× | 55.232 | 48.833 | 1.131038× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t13 | B300-P500 | 49.200 | 49.408 |
0.995790× | 55.264 | 49.408 | 1.118523× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t14 | B300-P500 | 52.512 | 52.097 |
1.007966× | 58.880 | 52.097 | 1.130199× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t15 | B300-P500 | 54.785 | 54.913 |
0.997669× | 60.768 | 54.913 | 1.106623× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t16 | B300-P500 | 55.361 | 56.033 |
0.988007× | 61.601 | 56.033 | 1.099370× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t17 | B300-P500 | 55.968 | 56.513 |
0.990356× | 63.041 | 56.513 | 1.115513× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t18 | B300-P500 | 57.057 | 56.800 |
1.004525× | 62.913 | 56.800 | 1.107623× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t19 | B300-P500 | 56.000 | 56.129 |
0.997702× | 63.041 | 56.129 | 1.123145× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t20 | B300-P500 | 57.440 | 57.600 |
0.997222× | 63.616 | 57.600 | 1.104444× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t21 | B300-P500 | 58.689 | 58.400 |
1.004949× | 65.408 | 58.400 | 1.120000× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t22 | B300-P500 | 59.392 | 59.073 |
1.005400× | 65.697 | 59.073 | 1.112132× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t23 | B300-P500 | 59.105 | 58.912 |
1.003276× | 65.761 | 58.912 | 1.116258× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t24 | B300-P500 | 60.513 | 60.512 |
1.000017× | 66.721 | 60.512 | 1.102608× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t25 | B300-P500 | 60.672 | 61.408 |
0.988015× | 68.192 | 61.408 | 1.110474× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t26 | B300-P500 | 63.169 | 62.688 |
1.007673× | 69.921 | 62.688 | 1.115381× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t27 | B300-P500 | 63.968 | 64.033 |
0.998985× | 72.192 | 64.033 | 1.127419× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t28 | B300-P500 | 64.513 | 64.513 |
1.000000× | 72.737 | 64.513 | 1.127478× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t29 | B300-P500 | 64.576 | 64.705 |
0.998006× | 72.640 | 64.705 | 1.122633× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t30 | B300-P500 | 66.145 | 65.696 |
1.006835× | 73.857 | 65.696 | 1.124224× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t31 | B300-P500 | 66.049 | 66.273 |
0.996620× | 73.824 | 66.273 | 1.113938× | True | True |
| sm103a_swiglu_e60_h2048_i1536_k4_t32 | B300-P500 | 66.305 | 66.529 |
0.996633× | 73.761 | 66.529 | 1.108704× | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t01 | B300-P500 | 21.376 | 21.440 |
0.997015× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t02 | B300-P500 | 28.801 | 28.704 |
1.003379× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t03 | B300-P500 | 34.976 | 34.977 |
0.999971× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t04 | B300-P500 | 43.584 | 43.808 |
0.994887× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t05 | B300-P500 | 49.697 | 49.792 |
0.998092× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t06 | B300-P500 | 57.121 | 57.633 |
0.991116× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t07 | B300-P500 | 65.216 | 65.504 |
0.995603× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t08 | B300-P500 | 71.489 | 71.585 |
0.998659× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t09 | B300-P500 | 77.217 | 77.217 |
1.000000× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t10 | B300-P500 | 83.169 | 83.265 |
0.998847× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t11 | B300-P500 | 89.601 | 89.761 |
0.998217× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t12 | B300-P500 | 95.808 | 95.617 |
1.001998× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t13 | B300-P500 | 101.281 | 101.312 |
0.999694× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t14 | B300-P500 | 107.617 | 107.713 |
0.999109× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t15 | B300-P500 | 115.009 | 114.945 |
1.000557× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t16 | B300-P500 | 119.458 | 119.425 |
1.000276× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t17 | B300-P500 | 124.288 | 123.296 |
1.008046× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t18 | B300-P500 | 130.401 | 129.985 |
1.003200× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t19 | B300-P500 | 135.393 | 136.321 |
0.993193× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t20 | B300-P500 | 140.482 | 140.962 |
0.996595× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t21 | B300-P500 | 145.857 | 146.593 |
0.994979× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t22 | B300-P500 | 151.650 | 151.746 |
0.999367× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t23 | B300-P500 | 156.385 | 156.641 |
0.998366× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t24 | B300-P500 | 162.018 | 161.698 |
1.001979× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t25 | B300-P500 | 166.913 | 167.809 |
0.994661× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t26 | B300-P500 | 173.570 | 174.209 |
0.996332× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t27 | B300-P500 | 179.202 | 179.713 |
0.997157× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t28 | B300-P500 | 185.026 | 185.313 |
0.998451× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t29 | B300-P500 | 190.945 | 191.425 |
0.997492× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t30 | B300-P500 | 195.106 | 194.977 |
1.000662× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t31 | B300-P500 | 199.841 | 199.873 |
0.999840× | N/A | N/A | N/A | True | True |
| sm103a_silu_e192_h6144_i1536_k4_t32 | B300-P500 | 205.474 | 205.730 |
0.998756× | N/A | N/A | N/A | True | True |

The primary matrix combines 96 newly measured SM100 routes using the
repaired FC2 schedule and 96 retained SM103 routes checked against the
new generated source, module/sequence ABI, and actual host
selector/workspace/launch projections. Retained rows keep their original
build and hardware identities. Binary equivalence was not assessed.

| Cohort | Primary rows | Measurement ms/arm/group |
|---|---:|---:|
| B300-P500 | 96 | 500 |
| B200-P100-repair | 96 | 100 |

| Segment | Cohort | GPU | Driver | PyTorch | Torch CUDA | Rows |
|---|---|---|---|---|---|---:|
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| initial | B300-P500 | NVIDIA B300 SXM6 AC | 580.126.09 | 2.13.0+cu130
| 13.0 | 12 |
| sm100-repair | B200-P100-repair | NVIDIA B200 | 580.82.07 |
2.13.0a0+9186a08b2c.nv26.07 | 13.3 | 96 |

The current primary matrix contains 6 official/export ratios below 1.
Those comparisons remain included. Standalone SiLU retains official=N/A.

Historical evidence retains 18 invalid records, 1 validation-only
records, 17 original negative records and 6 negative records from the
immediately previous primary matrix. Superseded rows below contribute no
latency to the current primary aggregates.

The 96 repaired SM100 primary rows include 94 rows from the original
worker and 2 from the explicitly recorded formal retries. Original
worker failures and all retry attempts remain in the evidence; their
status fields are unchanged.

| Formal attempt | Attempted rows | Completed rows | Primary rows | Raw
worker status | Measurement phase s | Worker s |
|---|---:|---:|---:|---|---:|---:|
| Original | 96 | 96 | 94 | FAIL | 6569.150 | 6807.906 |
| Retry 1 | 1 | 1 | 1 | PASS | 104.457 | 128.551 |
| Retry 2 | 1 | 1 | 1 | PASS | 111.051 | 134.452 |

The following original results were replaced only after follow-up
validation. They contribute no latency to primary aggregates. Each retry
below reports its actual measurement qualification and whether its row
was selected.

| Evidence | Shape | Source µs | Export µs | Source/export |
Official/export | Result | Primary |
|---|---|---:|---:|---:|---:|---|---|
| Original | `sm100a_swiglu_e512_h2048_i512_k10_t07` | N/A | N/A | N/A |
N/A | Capture failure; no timing | no |
| Original | `sm100a_silu_e192_h6144_i1536_k4_t01` | 21.504 | 22.465 |
0.957222346 | N/A | Source/export fidelity FAIL | no |
| Retry 1 | `sm100a_swiglu_e512_h2048_i512_k10_t07` | 36.704 | 36.800 |
0.997391304 | 1.053043478 | Qualification PASS | yes |
| Retry 2 | `sm100a_silu_e192_h6144_i1536_k4_t01` | 21.344 | 21.472 |
0.994038748 | N/A | Qualification PASS | yes |

### Previously superseded measurements

| Shape | Cohort | Source µs | Export µs | Source/export | Official µs |
Paired export µs | Official/export | Qualified | Legacy all gates |
|---|---|---:|---:|---:|---:|---:|---:|---|---|
| sm100a_swiglu_e60_h2048_i1536_k4_t20 | B200-P100 | 63.776 | 63.840 |
0.998997× | 64.672 | 63.840 | 1.013033× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t21 | B200-P100 | 65.343 | 65.440 |
0.998518× | 67.008 | 65.440 | 1.023961× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t22 | B200-P100 | 67.199 | 67.711 |
0.992438× | 67.008 | 67.711 | 0.989618× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t23 | B200-P100 | 68.768 | 69.120 |
0.994907× | 66.528 | 69.120 | 0.962500× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t24 | B200-P100 | 70.336 | 70.624 |
0.995922× | 67.872 | 70.624 | 0.961033× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t25 | B200-P100 | 72.352 | 72.480 |
0.998234× | 68.704 | 72.480 | 0.947903× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t26 | B200-P100 | 73.631 | 74.048 |
0.994369× | 70.720 | 74.048 | 0.955056× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t27 | B200-P100 | 75.711 | 75.776 |
0.999142× | 72.832 | 75.776 | 0.961149× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t28 | B200-P100 | 78.239 | 78.463 |
0.997145× | 73.951 | 78.463 | 0.942495× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t29 | B200-P100 | 80.255 | 80.255 |
1.000000× | 73.792 | 80.255 | 0.919469× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t30 | B200-P100 | 82.015 | 82.239 |
0.997276× | 74.815 | 82.239 | 0.909727× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t31 | B200-P100 | 83.807 | 84.223 |
0.995061× | 74.688 | 84.223 | 0.886789× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t32 | B200-P100 | 85.632 | 85.984 |
0.995906× | 74.688 | 85.984 | 0.868627× | True | False |

### SM100 measurements superseded by the FC2 repair

| Shape | Cohort | Source µs | Export µs | Source/export | Official µs |
Paired export µs | Official/export | Qualified | Legacy all gates |
|---|---|---:|---:|---:|---:|---:|---:|---|---|
| sm100a_swiglu_e512_h2048_i512_k10_t01 | B200-P500 | 15.776 | 16.032 |
0.984032× | 17.409 | 16.032 | 1.085891× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t02 | B200-P500 | 19.713 | 19.552 |
1.008234× | 22.336 | 19.552 | 1.142390× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t03 | B200-P500 | 23.743 | 23.552 |
1.008110× | 25.695 | 23.552 | 1.090990× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t04 | B200-P500 | 27.712 | 27.775 |
0.997732× | 29.856 | 27.775 | 1.074923× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t05 | B200-P500 | 30.464 | 30.656 |
0.993737× | 33.344 | 30.656 | 1.087683× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t06 | B200-P500 | 34.240 | 34.464 |
0.993500× | 36.736 | 34.464 | 1.065924× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t07 | B200-P500 | 36.416 | 37.088 |
0.981881× | 38.528 | 37.088 | 1.038827× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t08 | B200-P500 | 39.007 | 39.392 |
0.990226× | 40.960 | 39.392 | 1.039805× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t09 | B200-P500 | 41.888 | 42.400 |
0.987925× | 44.256 | 42.400 | 1.043774× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t10 | B200-P500 | 44.832 | 45.120 |
0.993617× | 46.944 | 45.120 | 1.040426× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t11 | B200-P500 | 47.072 | 47.840 |
0.983946× | 48.896 | 47.840 | 1.022074× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t12 | B200-P500 | 49.119 | 49.087 |
1.000652× | 50.687 | 49.087 | 1.032595× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t13 | B200-P500 | 51.840 | 52.736 |
0.983010× | 53.439 | 52.736 | 1.013331× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t14 | B200-P500 | 54.912 | 54.848 |
1.001167× | 56.128 | 54.848 | 1.023337× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t15 | B200-P500 | 57.631 | 57.504 |
1.002209× | 58.912 | 57.504 | 1.024485× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t16 | B200-P500 | 60.351 | 60.192 |
1.002642× | 61.503 | 60.192 | 1.021780× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t17 | B200-P500 | 62.399 | 62.528 |
0.997937× | 65.951 | 62.528 | 1.054743× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t18 | B200-P500 | 64.736 | 64.672 |
1.000990× | 68.991 | 64.672 | 1.066783× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t19 | B200-P500 | 67.264 | 67.136 |
1.001907× | 71.392 | 67.136 | 1.063394× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t20 | B200-P500 | 69.215 | 68.895 |
1.004645× | 72.927 | 68.895 | 1.058524× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t21 | B200-P500 | 71.423 | 70.944 |
1.006752× | 74.719 | 70.944 | 1.053211× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t22 | B200-P500 | 73.631 | 72.991 |
1.008768× | 75.999 | 72.991 | 1.041211× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t23 | B200-P500 | 75.488 | 75.232 |
1.003403× | 77.984 | 75.232 | 1.036580× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t24 | B200-P500 | 77.504 | 76.928 |
1.007488× | 79.871 | 76.928 | 1.038257× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t25 | B200-P500 | 79.776 | 79.423 |
1.004445× | 81.599 | 79.423 | 1.027398× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t26 | B200-P500 | 82.303 | 82.239 |
1.000778× | 82.848 | 82.239 | 1.007405× | True | True |
| sm100a_swiglu_e512_h2048_i512_k10_t27 | B200-P500 | 84.703 | 84.511 |
1.002272× | 83.903 | 84.511 | 0.992806× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t28 | B200-P500 | 86.815 | 86.816 |
0.999988× | 84.735 | 86.816 | 0.976030× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t29 | B200-P500 | 88.959 | 89.312 |
0.996048× | 85.983 | 89.312 | 0.962726× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t30 | B200-P500 | 91.072 | 91.008 |
1.000703× | 86.911 | 91.008 | 0.954982× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t31 | B200-P500 | 92.992 | 93.343 |
0.996240× | 88.384 | 93.343 | 0.946873× | True | False |
| sm100a_swiglu_e512_h2048_i512_k10_t32 | B200-P500 | 95.295 | 95.200 |
1.000998× | 88.959 | 95.200 | 0.934443× | True | False |
| sm100a_swiglu_e60_h2048_i1536_k4_t01 | B200-P500 | 15.584 | 15.872 |
0.981855× | 16.353 | 15.872 | 1.030305× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t02 | B200-P500 | 18.624 | 18.816 |
0.989796× | 20.767 | 18.816 | 1.103688× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t03 | B200-P500 | 24.416 | 24.224 |
1.007926× | 31.424 | 24.224 | 1.297226× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t04 | B200-P500 | 27.456 | 27.583 |
0.995396× | 35.264 | 27.583 | 1.278469× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t05 | B200-P500 | 31.104 | 31.360 |
0.991837× | 37.760 | 31.360 | 1.204082× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t06 | B200-P500 | 33.312 | 33.377 |
0.998053× | 39.264 | 33.377 | 1.176379× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t07 | B200-P500 | 35.872 | 35.936 |
0.998219× | 42.528 | 35.936 | 1.183437× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t08 | B200-P500 | 38.271 | 38.144 |
1.003329× | 45.023 | 38.144 | 1.180343× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t09 | B200-P500 | 40.896 | 40.960 |
0.998437× | 47.360 | 40.960 | 1.156250× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t10 | B200-P500 | 43.040 | 43.104 |
0.998515× | 49.663 | 43.104 | 1.152167× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t11 | B200-P500 | 45.216 | 45.279 |
0.998609× | 52.416 | 45.279 | 1.157623× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t12 | B200-P500 | 48.640 | 48.896 |
0.994764× | 55.872 | 48.896 | 1.142670× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t13 | B200-P500 | 50.656 | 50.784 |
0.997480× | 55.903 | 50.784 | 1.100799× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t14 | B200-P500 | 53.184 | 53.248 |
0.998798× | 59.263 | 53.248 | 1.112962× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t15 | B200-P500 | 55.744 | 55.743 |
1.000018× | 61.472 | 55.743 | 1.102775× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t16 | B200-P500 | 57.567 | 57.728 |
0.997211× | 62.496 | 57.728 | 1.082594× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t17 | B200-P100 | 59.199 | 59.520 |
0.994607× | 63.424 | 59.520 | 1.065591× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t18 | B200-P100 | 60.832 | 60.863 |
0.999491× | 63.487 | 60.863 | 1.043113× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t19 | B200-P100 | 62.111 | 62.464 |
0.994349× | 63.936 | 62.464 | 1.023558× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t20 | B200-P100-optimized | 58.528 |
58.176 | 1.006051× | 64.863 | 58.176 | 1.114944× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t21 | B200-P100-optimized | 60.032 |
60.064 | 0.999467× | 66.336 | 60.064 | 1.104422× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t22 | B200-P100-optimized | 60.287 |
60.223 | 1.001063× | 66.527 | 60.223 | 1.104678× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t23 | B200-P100-optimized | 60.319 |
60.256 | 1.001046× | 66.432 | 60.256 | 1.102496× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t24 | B200-P100-optimized | 61.184 |
60.992 | 1.003148× | 67.680 | 60.992 | 1.109654× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t25 | B200-P100-optimized | 61.856 |
61.760 | 1.001554× | 68.768 | 61.760 | 1.113472× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t26 | B200-P100-optimized | 63.168 |
63.391 | 0.996482× | 70.751 | 63.391 | 1.116105× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t27 | B200-P100-optimized | 65.088 |
64.800 | 1.004444× | 72.896 | 64.800 | 1.124938× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t28 | B200-P100-optimized | 65.535 |
65.472 | 1.000962× | 73.983 | 65.472 | 1.129995× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t29 | B200-P100-optimized | 65.664 |
65.856 | 0.997085× | 73.759 | 65.856 | 1.120004× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t30 | B200-P100-optimized | 66.752 |
66.623 | 1.001936× | 74.720 | 66.623 | 1.121535× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t31 | B200-P100-optimized | 66.720 |
67.072 | 0.994759× | 74.720 | 67.072 | 1.114035× | True | True |
| sm100a_swiglu_e60_h2048_i1536_k4_t32 | B200-P100-optimized | 66.687 |
66.911 | 0.996652× | 74.879 | 66.911 | 1.119084× | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t01 | B200-P100 | 21.760 | 21.376 |
1.017964× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t02 | B200-P100 | 28.993 | 29.120 |
0.995639× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t03 | B200-P100 | 35.584 | 35.167 |
1.011858× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t04 | B200-P100 | 43.584 | 43.263 |
1.007420× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t05 | B200-P100 | 50.399 | 50.176 |
1.004444× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t06 | B200-P100 | 58.112 | 57.888 |
1.003870× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t07 | B200-P100 | 65.760 | 65.632 |
1.001950× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t08 | B200-P100 | 71.647 | 72.128 |
0.993331× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t09 | B200-P100 | 77.600 | 77.599 |
1.000013× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t10 | B200-P100 | 83.583 | 83.296 |
1.003446× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t11 | B200-P100 | 89.887 | 89.695 |
1.002141× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t12 | B200-P100 | 95.871 | 95.551 |
1.003349× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t13 | B200-P100 | 101.055 | 100.960 |
1.000941× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t14 | B200-P100 | 108.255 | 108.223 |
1.000296× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t15 | B200-P100 | 114.079 | 114.143 |
0.999439× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t16 | B200-P100 | 119.679 | 118.462 |
1.010273× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t17 | B200-P100 | 121.823 | 121.439 |
1.003162× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t18 | B200-P100 | 128.351 | 128.414 |
0.999506× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t19 | B200-P100 | 134.750 | 134.143 |
1.004525× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t20 | B200-P100 | 140.191 | 139.967 |
1.001600× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t21 | B200-P100 | 145.407 | 145.311 |
1.000661× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t22 | B200-P100 | 151.519 | 151.583 |
0.999578× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t23 | B200-P100 | 154.815 | 154.783 |
1.000207× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t24 | B200-P100 | 160.319 | 159.967 |
1.002200× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t25 | B200-P100 | 165.950 | 166.046 |
0.999422× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t26 | B200-P100 | 171.870 | 171.935 |
0.999622× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t27 | B200-P100 | 177.983 | 177.855 |
1.000720× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t28 | B200-P100 | 183.935 | 183.391 |
1.002966× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t29 | B200-P100 | 189.279 | 189.502 |
0.998823× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t30 | B200-P100 | 193.710 | 193.566 |
1.000747× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t31 | B200-P100 | 197.343 | 197.582 |
0.998788× | N/A | N/A | N/A | True | True |
| sm100a_silu_e192_h6144_i1536_k4_t32 | B200-P100 | 202.398 | 202.591 |
0.999047× | N/A | N/A | N/A | True | True |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
  - Added exact SM100 and SM103 support for Cake warp-decode.
- Added standalone SiLU support for the 6144×1536, 192-expert geometry.
  - Added activation-aware weight preparation and validation.
- Added target-specific module generation, loading, and runtime
selection.

- **Documentation**
- Updated API, validation, and design documentation with supported
architectures, activations, layouts, and benchmarking guidance.

- **Tests**
- Expanded coverage for SM100, SM103, SiLU configurations, target
selection, source resolution, and invalid activation/geometry
combinations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4369
- **最后更新**: 2026-09-10T20:25:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34490
- **最后更新**: 2026-09-10T22:12:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Lucain

## AI分析总结

## 提交分析总结

**1. 主要更新类型**
本次提交属于**重构/依赖管理优化**类型，核心是调整 `httpx` 库的导入来源，将其从直接依赖改为从 `huggingface_hub` 中导入。

**2. 关键变更点及与项目方向的关系**
- 变更点：不再自行声明和导入 `httpx`，而是复用 `huggingface_hub` 已封装的 `httpx`。
- 与项目方向的关系：diffusers 作为 HuggingFace 生态的核心库，正持续向**统一依赖、减少冗余**的方向演进。通过复用 `huggingface_hub` 的依赖，可避免版本冲突，保持与 Hub 生态的一致性。

**3. 对项目的影响和潜在意义**
- 减少 diffusers 自身的直接依赖项，降低安装体积与版本冲突风险。
- 确保 `httpx` 版本与 `huggingface_hub` 保持同步，提升与 Hub 交互（如下载模型、上传）的稳定性。
- 体现 HuggingFace 各库之间**依赖收敛**的工程实践，利于长期维护。

**4. 值得关注的技术点**
- 这种“从上游库导入依赖”的模式，要求 `huggingface_hub` 稳定导出 `httpx`，存在隐式耦合。
- 若未来 `huggingface_hub` 更换 HTTP 客户端，diffusers 可能被动受影响，需关注其兼容性策略。
- 属于典型的依赖治理重构，对功能行为无直接影响，但影响打包与运行环境。

**5. 基于项目背景的影响**
diffusers 定位为扩散模型的模块化工具箱，强调易用性与生态协同。此提交虽小，却契合其**依托 HuggingFace 生态、简化用户安装体验**的整体目标，有助于降低新用户的环境配置门槛，推动项目更顺畅地融入 Hub 工作流，对项目长期健康发展具有积极意义。

## 详细提交记录

### [a71e62e](https://github.com/huggingface/diffusers/commit/a71e62e0d226c284b86abf518791a5ffbba064bf)

- **作者**: Lucain
- **时间**: 2026-09-10T20:45:54Z
- **提交信息**: [httpx migration] Import httpx from huggingface_hub (#14753)

Import httpx from huggingface_hub

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
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


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13082
- **最后更新**: 2026-09-10T19:45:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35776
- **最后更新**: 2026-09-10T23:58:16Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 30
- **主要提交者**: Mick, Liangsheng Yin, Kangyan-Zhou

## AI分析总结

# SGLang 昨日提交批次分析（38 条提交）

## 1. 主要更新类型分布

- **功能新增与模型支持**：NemotronH_Omni_Reasoning_V3、DeepSeek-V4.1 系列、Ling-3.0-flash-VL INT4/FP4、flashinfer Mega MoE、采样掩码支持 overlap scheduling、Rust TreeCore 外部缓存链接器。
- **Bug 修复**：KV-canary 工作区核算、PureSWA 尾部释放、HiCache 回载配额、DeepSeek-V4 路由下溢与 renorm、NPU PP=2 挂起、FP8 缓存前缀反量化。
- **性能优化**：SM120 精确 query-head 宽度、NPU HiCache L2 IO（Memfabric acc_offload）、AMD Fast Triton Sparse MLA、AITER verify 运行时尺寸恢复。
- **重构与清理**：退役 CUDA 12 通道、删除 cutlass_mla / 非 Marlin GPTQ / AWQ AOT / Dual Chunk Flash Attention、DeepSeek V4 元数据命名澄清。
- **依赖与 CI**：smg-grpc-servicer 下限提升、XPU 去除 human-eval 依赖、GB300 测试恢复、多项 AMD/NPU CI 修复、CI 权限更新。
- **文档**：LMSYS 博客卡片同步、diffusion 快照与 minimax-h3 特性、Cookbook 增补 HiCache L2 旋钮。

## 2. 关键变更点与项目方向

- **硬件后端持续扩张**：AMD（MXFP4 在线量化、Triton Sparse MLA）、NPU（HiCache L2、DeepEP 测试）、SM120、B300/GB300 验证，体现项目对多厂商推理硬件的全面覆盖战略。
- **DeepSeek-V4/V4.1 深度打磨**：从路由数值稳定性、稀疏 MLA 解码宽度到元数据命名，说明该模型是当前重点优化目标。
- **投机解码（Spec）增强**：Inkling MTP 草稿元数据、大 MTP 批次短卷积元数据，延续 SGLang 在 Speculative Decoding 上的领先投入。
- **技术债清理**：退役 CUDA 12 通道、删除多个旧内核，反映项目向更精简、更现代的运行时收敛。

## 3. 对项目的影响与潜在意义

- 多硬件后端（AMD/NPU/SM120）的同步推进，强化了 SGLang 作为**跨平台高性能推理引擎**的定位。
- 内核清理与 JIT 化（expert-pack MXFP4 迁移至 load_jit）降低维护成本，提升编译与部署灵活性。
- HiCache 相关修复（配额、L2 IO、PureSWA）直接关系到长上下文与缓存复用场景的稳定性，对生产部署意义重大。
- 大量 CI 修复与依赖调整保障了夜间构建与端到端测试的可靠性，是持续交付的基础。

## 4. 值得关注的技术点

- **MXFP4 在线量化**：AMD 上将 bf16 MTP 草稿专家在线量化为 MXFP4，兼顾精度与显存。
- **Memfabric acc_offload**：NPU 上优化 HiCache L2 IO，是异构内存分层的关键实践。
- **采样掩码 + overlap scheduling**：在调度重叠下支持采样掩码，属调度与采样的深度协同。
- **Rust TreeCore 外部缓存链接器**：Rust 组件与缓存系统的集成，暗示项目在核心数据结构上引入 Rust 提升性能。
- **DeepSeek-V4 路由数值修复**：sqrtsoftplus 下溢与无下限 renorm，是 MoE 路由稳定性的典型工程问题。

## 5. 结合 README 的项目发展影响

README 显示 SGLang 定位为面向大模型与多模态的高性能服务框架，强调易用性与多硬件支持。本批提交与此高度一致：一方面通过 NemotronH、DeepSeek-V4.1、Ling-3.0-flash-VL 等新模型扩展覆盖面；另一方面通过 AMD/NPU/SM120 后端优化与内核清理提升性能与可维护性。整体看，项目正从“功能覆盖”转向“多后端稳定性 + 生产级缓存/调度”的成熟阶段，为大规模部署与长上下文推理奠定基础。

## 详细提交记录

### [52c191d](https://github.com/sgl-project/sglang/commit/52c191da52390fa5508de98eddd1e3eca2dbcfb2)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-10T23:58:09Z
- **提交信息**: [Deps] Retire the CUDA 12 lane (#38404)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [fae8cd8](https://github.com/sgl-project/sglang/commit/fae8cd84cbc5a847901e565439d2eaeb869a022c)

- **作者**: rystewart-nvidia
- **时间**: 2026-09-10T23:57:22Z
- **提交信息**: Support NemotronH_Omni_Reasoning_V3 in SGLang (#35599)

Signed-off-by: Ryan Stewart <rystewart@nvidia.com>
Signed-off-by: rystewart-nvidia <rystewart@nvidia.com>
Co-authored-by: elvischenv <219235043+elvischenv@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [203d7e8](https://github.com/sgl-project/sglang/commit/203d7e812c6c9cde8859499daf54686091714638)

- **作者**: cctry
- **时间**: 2026-09-10T23:10:12Z
- **提交信息**: Fix KV-canary workspace accounting after graph capture (#38596)

### [42bbaac](https://github.com/sgl-project/sglang/commit/42bbaac25914ef31eaf7ec0dbea7df52c608a0b9)

- **作者**: cctry
- **时间**: 2026-09-10T23:09:21Z
- **提交信息**: [metrics] Report logical prefill token counts (#38566)

### [dc5f59c](https://github.com/sgl-project/sglang/commit/dc5f59c3a2c4989a789fcf14ffd1c4c3fdc69dac)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-10T22:42:52Z
- **提交信息**: [Refactor] Clarify DeepSeek V4 metadata names for V4.1 (#38947)

### [d076eec](https://github.com/sgl-project/sglang/commit/d076eec42788b9c26354e8714ef0c43fe6dab6af)

- **作者**: Pengyun Lin
- **时间**: 2026-09-10T22:40:17Z
- **提交信息**: [SM120] Use exact query-head widths for DeepSeek-V4 sparse MLA decode (#36655)

### [bb15be6](https://github.com/sgl-project/sglang/commit/bb15be6d79d3b127295b0436b5164757335c2d1a)

- **作者**: paulzhang-tm
- **时间**: 2026-09-10T22:32:19Z
- **提交信息**: [Spec] Stage Inkling MTP draft metadata before verify (#38169)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [a63efd9](https://github.com/sgl-project/sglang/commit/a63efd9056b33a3d4a32dfba6262fac1d62b959a)

- **作者**: paulzhang-tm
- **时间**: 2026-09-10T22:13:17Z
- **提交信息**: [Spec] Support large MTP batches in short-convolution metadata (#38558)

### [fd7743e](https://github.com/sgl-project/sglang/commit/fd7743e0e1725f9f24844e6f3446fcf0f9ade815)

- **作者**: Byron Hsu
- **时间**: 2026-09-10T21:52:44Z
- **提交信息**: [Sampling] Support sampling masks with overlap scheduling (#36631)

Co-authored-by: ByronHsu <ByronHsu@users.noreply.github.com>
Co-authored-by: root <root@slurm-h200-208-179.slurm-compute.tenant-slurm.svc.cluster.local>
Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>

### [55b45cb](https://github.com/sgl-project/sglang/commit/55b45cb45a02b96a49837ca4311c3a1f01b8dcd2)

- **作者**: YAMY
- **时间**: 2026-09-10T21:07:39Z
- **提交信息**: fix(qsa): dequantize FP8 cached prefixes in the sparse prefill kernels (#38855)

### [06dfe05](https://github.com/sgl-project/sglang/commit/06dfe05d65f7dbc1a630048cf9c7d433fc02a157)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-10T20:55:36Z
- **提交信息**: [Deps] Raise smg-grpc-servicer floor to >=0.9.0 to unbreak SMG E2E CI (#38801)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [a26273d](https://github.com/sgl-project/sglang/commit/a26273d668c82400e9e2a97ed328d4148a04e123)

- **作者**: zijiec
- **时间**: 2026-09-10T20:00:41Z
- **提交信息**: [AMD] Quantize the bf16 MTP draft experts online to MXFP4 for Qwen3.5 (#38748)

Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>
Co-authored-by: jacky.cheng <yichiche@amd.com>

### [887c401](https://github.com/sgl-project/sglang/commit/887c401e151e2d1b082d74ef8769a23eef5c465c)

- **作者**: sglang-bot
- **时间**: 2026-09-10T18:37:14Z
- **提交信息**: docs: sync LMSYS SGLang blog cards (#36773)

Co-authored-by: sglang-bot <sglang-bot@users.noreply.github.com>

### [4b7331f](https://github.com/sgl-project/sglang/commit/4b7331fb7770e4d89f159846449da2396c32eb18)

- **作者**: zijiexia
- **时间**: 2026-09-10T18:04:53Z
- **提交信息**: Make the remaining DeepSeek-V4.1 NVIDIA cells start (#38861)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [209654c](https://github.com/sgl-project/sglang/commit/209654c42090a7a33896a2849b33ab3a50af32c5)

- **作者**: James
- **时间**: 2026-09-10T16:23:36Z
- **提交信息**: [NPU][Hicache] Optimize HiCache L2 IO with Memfabric acc_offload (#38826)

### [19b83b4](https://github.com/sgl-project/sglang/commit/19b83b4b9d47a485dbd1077fbe89c7da0141eabd)

- **作者**: Shuwen Wang
- **时间**: 2026-09-10T15:55:48Z
- **提交信息**: [Radix Cache] Fix PureSWA tail release without insertion (#38349)

### [cc7e43a](https://github.com/sgl-project/sglang/commit/cc7e43ad2229f264988125dcc6f6ec409c9013d6)

- **作者**: Shuwen Wang
- **时间**: 2026-09-10T15:54:08Z
- **提交信息**: [HiCache] Account for newly pinned ancestors in load-back quota (#38481)

### [92dffeb](https://github.com/sgl-project/sglang/commit/92dffebe16f5d29788ab0dbeac49d28f97e26cbf)

- **作者**: pllimax
- **时间**: 2026-09-10T15:32:54Z
- **提交信息**: [NPU] Set DEEPEP_HYBRID_DEPLOYMENT for new DeepEP tests; switch glm5_2 to w8a8; tune nightly timeouts (#38775)

### [1277178](https://github.com/sgl-project/sglang/commit/12771786f23190b1845db33366eba09cb5eacf41)

- **作者**: Chengze Fan
- **时间**: 2026-09-10T12:57:47Z
- **提交信息**: [AMD] Restore AITER verify runtime sizing reverted by #34647 (#38575)

### [6130022](https://github.com/sgl-project/sglang/commit/613002281e78fc57d888f68999253fe7de33b950)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-10T12:55:06Z
- **提交信息**: [CI] Drop the GPTQ dynamic-config test for the deleted non-Marlin kernel (#38881)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [908226f](https://github.com/sgl-project/sglang/commit/908226fea2df861769e2720161a75649ae4c6f92)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-10T11:22:24Z
- **提交信息**: [Rust TreeCore] Support external cache linker (#37306)

### [334e94d](https://github.com/sgl-project/sglang/commit/334e94d8ac8780575007e10ad38355949168a709)

- **作者**: liupeng374
- **时间**: 2026-09-10T11:21:37Z
- **提交信息**: [NPU] fix pp 2 hang on npu (#38249)

### [a37ded1](https://github.com/sgl-project/sglang/commit/a37ded1693f608c0aae50cff4a3c40146b0b643b)

- **作者**: Yuhao Yang
- **时间**: 2026-09-10T10:20:34Z
- **提交信息**: [Cookbook] DeepSeek-V4.1: add the HiCache L2 knob to the Playground (#38844)

Co-authored-by: Claude Code <noreply@anthropic.com>

### [dc2157d](https://github.com/sgl-project/sglang/commit/dc2157dcd62d5fb1bc5317fcf8765ebfcd8a8dad)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-10T09:50:51Z
- **提交信息**: [JIT] Port the expert-pack MXFP4 kernels to load_jit and fix their launch limits (#38830)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [8022505](https://github.com/sgl-project/sglang/commit/8022505705eb7dc6239ab0bbdb7c1a0ce8682d40)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-10T09:41:15Z
- **提交信息**: Revert "[CI] Temporarily disable GB300 tests" (#38842)

### [c9c26d5](https://github.com/sgl-project/sglang/commit/c9c26d56b2c68a98058312d9d0590dbd94ebdfb7)

- **作者**: Mick
- **时间**: 2026-09-10T09:23:43Z
- **提交信息**: [diffusion] docs: sync snapshot and minimax-h3 subblock features (#38784)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [8a6ab89](https://github.com/sgl-project/sglang/commit/8a6ab89bf0b90304b3b454a833fcdcaefb777c29)

- **作者**: Clint
- **时间**: 2026-09-10T08:58:00Z
- **提交信息**: [AMD] Enable Fast Triton Sparse MLA backend (#30575)

Co-authored-by: clintg6 <7388379+clintg6@users.noreply.github.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [5caafd2](https://github.com/sgl-project/sglang/commit/5caafd2118b7b198416c5d74b24e1f0aae0346ef)

- **作者**: zijiexia
- **时间**: 2026-09-10T08:49:44Z
- **提交信息**: Fix the DeepSeek-V4.1 reasoning example and mark the B300 cells verified (#38839)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [fa6e657](https://github.com/sgl-project/sglang/commit/fa6e657b93cbef4b2a62b8c4e82c519381b38d7f)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-10T08:38:58Z
- **提交信息**: [misc] Update CI permission (#38834)

### [b23db06](https://github.com/sgl-project/sglang/commit/b23db06769ec3cf2b5dd0920aaac1cccc95358bf)

- **作者**: ashwini rathi
- **时间**: 2026-09-10T08:24:43Z
- **提交信息**: pyproject(xpu): drop human-eval git dep to unblock image build (#38824)

### [55b4f4f](https://github.com/sgl-project/sglang/commit/55b4f4f19506c5571d7c4b04b1b47e85790b6db3)

- **作者**: Adarsh Shirawalmath
- **时间**: 2026-09-10T08:07:43Z
- **提交信息**: [Test] Add offline Transformers loader compatibility checks (#38336)

Signed-off-by: adarshxs <adarsh.shirawalmath@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [9a2f17f](https://github.com/sgl-project/sglang/commit/9a2f17f41d185614a17f740c006c4aca84c016bf)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-10T07:23:50Z
- **提交信息**: Add INT4 and FP4 lanes to the Ling-3.0-flash-VL cookbook (#38527)

### [1b77f49](https://github.com/sgl-project/sglang/commit/1b77f498a0f7c422782eaccd018fdd850b421cfd)

- **作者**: Shu Wang
- **时间**: 2026-09-10T07:22:47Z
- **提交信息**: [NVIDIA] Support flashinfer Mega Moe (#31470)

Co-authored-by: djns99 <40156487+djns99@users.noreply.github.com>
Co-authored-by: 云挚 <ningyunxiao.nyx@antgroup.com>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [c0b790c](https://github.com/sgl-project/sglang/commit/c0b790cf7fe6dc1516c3ec1f23de9b37baca654a)

- **作者**: Brayden Zhong
- **时间**: 2026-09-10T07:12:01Z
- **提交信息**: Delete cutlass_mla, non-Marlin GPTQ, AWQ AOT kernel, and Dual Chunk Flash Attention (#32114)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [7152c14](https://github.com/sgl-project/sglang/commit/7152c143841df01cb8f5d27dd059fd338f958576)

- **作者**: Brayden Zhong
- **时间**: 2026-09-10T07:10:50Z
- **提交信息**: Fix DeepSeek-V4 routing: sqrtsoftplus underflow and unfloored renorm (#34459)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [6b2e13b](https://github.com/sgl-project/sglang/commit/6b2e13bcb02721899dcc495279238fa3c8d42018)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-10T07:07:08Z
- **提交信息**: [AMD] Fix the diffusion perf fixture lookup  (#38686)

### [bd922bc](https://github.com/sgl-project/sglang/commit/bd922bc39b09748d5f0f1c355bb8dcf41c4cc5e1)

- **作者**: Bingxu Chen
- **时间**: 2026-09-10T07:02:00Z
- **提交信息**: [AMD][CI] Fix UMBP test buffer after MoRI upgrade (#38672)

### [13fb796](https://github.com/sgl-project/sglang/commit/13fb796c81bc01cf22cdb2c17975f4b31a0f138a)

- **作者**: Michael
- **时间**: 2026-09-10T07:00:28Z
- **提交信息**: [AMD][CI] Drop the dead miles ROCm 7.0 nightly image build (#38694)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Michael <michaelzhang-ai@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1275
- **最后更新**: 2026-09-10T02:30:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91441
- **最后更新**: 2026-09-10T23:58:35Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 36
- **主要提交者**: Alexander Crettenand, YoavMiron, Toby Mao

## AI分析总结

# vLLM 昨日提交批次分析（共39条）

## 一、主要更新类型分布

- **Bug修复**（约14条）：占比最高，覆盖前端、多模态、ROCm、MoE、CLI参数解析等。
- **性能优化**（约8条）：集中在ROCm、Kimi K3、GLM-5.3、DCP/KV Connector等。
- **功能新增**（约6条）：DeepSeek-V4.1-Flash模型定义、Bailing V3 VL、Fast Start支持fp4、MTP独立lm head等。
- **硬件后端适配**（约6条）：XPU、ROCm、CPU的专项修复与优化。
- **CI/构建/文档/类型**（约5条）：ruff规则、mypy类型、CI缓存、文档修正。

## 二、关键变更点与项目方向

1. **新模型持续接入**：DeepSeek-V4.1-Flash（含Rust/Python前端）、Bailing V3 VL、Nemotron MTP，体现vLLM"支持广泛模型"的核心定位。
2. **多硬件后端深化**：XPU（forward_xpu、FalconH1）、ROCm（多流专家、bpreshuffle FP8 GEMM、KV connector）、CPU（CI修复）并行推进，呼应"for everyone"的普惠目标。
3. **KV Connector与分布式推理增强**：对称DCP disagg支持混合mamba、NIXL PCP rank报告、ROCm AITER统一注意力，强化生产级部署能力。
4. **性能热点打磨**：Kimi K3 KDA gather/scatter优化（5.2%~7.7%吞吐提升）、GLM-5.3解码热路径清理、MRV2 fast-prefill与UVA写入，直指"fast"承诺。

## 三、对项目的影响与意义

- **稳定性**：大量Bugfix（流式stop_sequence、音频缓存UUID、EC元数据校验、DSML容错）直接提升生产可靠性。
- **性能竞争力**：ROCm与Kimi/GLM专项优化缩小与CUDA差距，增强AMD生态吸引力。
- **生态扩展**：新模型与前端支持（Rust/Python）降低用户迁移成本，巩固vLLM作为LLM服务事实标准的地位。

## 四、值得关注的技术点

- **MRV2 fast-prefill + UVA-backed apply_write**：内存管理与预填充加速的架构级改进。
- **MTP独立量化lm head**：投机解码与量化结合的灵活设计。
- **Fused A2A pack kernel融合LSE mask**：DCP场景下的通信-计算融合思路。
- **bpreshuffled blockscaled FP8 GEMM**：ROCm上FP8性能的关键突破。
- **ruff INP规则强制`__init__.py`**：代码规范治理的工程化实践。

## 五、结合README的项目发展影响

README强调"Easy, fast, and cheap LLM serving for everyone"。本批次提交从三个维度支撑该愿景：**Easy**——新模型开箱即用、CLI参数修复、文档澄清；**Fast**——Kimi/GLM/ROCm性能优化、fast-prefill、FP8 GEMM；**for everyone**——XPU/ROCm/CPU多后端并行适配。整体看，项目正从"支持主流GPU"向"全硬件、全模型、生产级分布式"演进，Bugfix密度高说明社区活跃且注重质量，性能优化集中于新兴模型与AMD平台，显示vLLM在保持CUDA领先的同时积极拓展异构算力版图。

## 详细提交记录

### [5b6cf93](https://github.com/vllm-project/vllm/commit/5b6cf93e8e229aa0901e8c152eba4511a6195d28)

- **作者**: Marceli Fylcek
- **时间**: 2026-09-10T23:58:28Z
- **提交信息**: [XPU] Add forward_xpu to Mixer2RMSNormGated and FusedRMSNormGated (#54968)

Signed-off-by: Marceli Fylcek <marceli.fylcek@intel.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [a89de95](https://github.com/vllm-project/vllm/commit/a89de950a43896cfd97a3b7f051a8f0984ea6be0)

- **作者**: Tyler Michael Smith
- **时间**: 2026-09-10T23:26:11Z
- **提交信息**: [CI/Build] Pin HyperCLOVAX V2 test model revision (#56335)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [360f33f](https://github.com/vllm-project/vllm/commit/360f33f61ce02bda04bcb7ea876f1d2e5af8d06d)

- **作者**: Colin McNamara
- **时间**: 2026-09-10T22:21:21Z
- **提交信息**: [Bugfix] Set stop_sequence explicitly in streaming message_delta event (#55325)

Signed-off-by: Colin McNamara <colin@2cups.com>

### [9163190](https://github.com/vllm-project/vllm/commit/9163190dda009a310d8c175d63860ac7c671ca90)

- **作者**: Matt
- **时间**: 2026-09-10T22:14:22Z
- **提交信息**: [ROCm][Bugfix][Perf] Tune multi-stream shared experts use; wvSplitKrc fixes (#56098)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [ae71862](https://github.com/vllm-project/vllm/commit/ae71862c51f2e069998e0dd5dc30a03a3b475ab9)

- **作者**: shaohuaxi
- **时间**: 2026-09-10T19:23:34Z
- **提交信息**: [Bugfix][Frontend] Check EC requirements for each metadata item (#56070)

Signed-off-by: 子华 <huaxi.shx@alibaba-inc.com>
Co-authored-by: Codex <noreply@openai.com>

### [a36dfc9](https://github.com/vllm-project/vllm/commit/a36dfc93cb1e4ca11425cfde48b5ed2264027aa2)

- **作者**: Jiatai Wang
- **时间**: 2026-09-10T19:20:03Z
- **提交信息**: [Bugfix][Multimodal] Restore cached audio inputs with UUIDs (#56310)

Signed-off-by: JiataiWang <wangjiatai@proton.me>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7de70fa](https://github.com/vllm-project/vllm/commit/7de70fa7ae9fdda688257eed13639b56cc677fde)

- **作者**: Micah Williamson
- **时间**: 2026-09-10T18:54:52Z
- **提交信息**: [Bugfix][ROCm] Create linear layer biases with `requires_grad=False` (#56161)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [48cb12c](https://github.com/vllm-project/vllm/commit/48cb12c184e9b753c5de1c8ecab7953ded127b87)

- **作者**: Matt
- **时间**: 2026-09-10T18:39:33Z
- **提交信息**: [ROCm][Bugfix] Fix profiler in TheRock image (#56190)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [7cdd930](https://github.com/vllm-project/vllm/commit/7cdd9304ae2e46572f220741bf86e0b3c2da569c)

- **作者**: Wei Zhao
- **时间**: 2026-09-10T18:12:15Z
- **提交信息**: [KV Connector] Support symmetric DCP disagg for hybrid mamba models (#55531)

Signed-off-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Wei Zhao <weizha@oci-aga-slurm-1-vscode-02.cm.cluster>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [983b7e2](https://github.com/vllm-project/vllm/commit/983b7e28c9f87c3a150081640e0fdeafec5d553a)

- **作者**: Julien Denize
- **时间**: 2026-09-10T17:57:44Z
- **提交信息**: [Bugfix] Avoid MistralCommonBackend for HF tokenizers (#54192)

Signed-off-by: Julien Denize <40604584+juliendenize@users.noreply.github.com>

### [8359e15](https://github.com/vllm-project/vllm/commit/8359e15aae32dee9dc1f259a9b2574fb72b5507e)

- **作者**: Simon Danielsson
- **时间**: 2026-09-10T17:48:42Z
- **提交信息**: [ROCm][Feature] Support KV connectors with ROCM_AITER_UNIFIED_ATTN (#53695)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Signed-off-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [e6cb563](https://github.com/vllm-project/vllm/commit/e6cb56337b49e606f55fde1870adbbb051e23f9f)

- **作者**: Nick Hill
- **时间**: 2026-09-10T17:36:04Z
- **提交信息**: [Core] MRV2 support for fast-prefill (#56145)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [7470082](https://github.com/vllm-project/vllm/commit/7470082f57a0245703be7482544f4b0fd410e1f2)

- **作者**: Simon Danielsson
- **时间**: 2026-09-10T16:18:37Z
- **提交信息**: [ROCm][Perf] Add bpreshuffled blockscaled fp8 GEMM (#51692)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [3078e7c](https://github.com/vllm-project/vllm/commit/3078e7cbe1efb7dfcdeabceea9a6f890bc724976)

- **作者**: Josiah Davis
- **时间**: 2026-09-10T16:13:09Z
- **提交信息**: [Docs]: quote variable-bearing wheel URLs (#56286)

Signed-off-by: Josiah Davis <Josiah.Davis@arm.com>

### [6ee5bb0](https://github.com/vllm-project/vllm/commit/6ee5bb0a0b3e32dd1a6d9fddb61b50905ccdd6e0)

- **作者**: Rita Brugarolas
- **时间**: 2026-09-10T15:43:00Z
- **提交信息**: [DCP][Kernel][Perf] Fuse the empty-shard LSE mask into the A2A pack kernel (#54889)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bdea277](https://github.com/vllm-project/vllm/commit/bdea2777eaeab65937dffdbdcb372b03e2cad441)

- **作者**: Itay Alroy
- **时间**: 2026-09-10T15:33:56Z
- **提交信息**: [Bugfix][MoE] Fix batched CUTLASS workspace overallocation (#55579)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [db723d2](https://github.com/vllm-project/vllm/commit/db723d245a2ed029c9fdb21e8c51a57fd4980f8a)

- **作者**: Cenab Batu Bora
- **时间**: 2026-09-10T15:07:42Z
- **提交信息**: [Bugfix] Honor explicit empty and zero CLI arguments (#55710)

Signed-off-by: Cenab Batu Bora <40250311+cenab@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [46bae7e](https://github.com/vllm-project/vllm/commit/46bae7e98c353bc64dd762f3ebac70165f1027d9)

- **作者**: Li, Jiang
- **时间**: 2026-09-10T14:27:26Z
- **提交信息**: [CI/Build][CPU] Fix flaky rust downloads, broken prune flag, and triton-cpu cache coupling (#56247)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [2e0ee66](https://github.com/vllm-project/vllm/commit/2e0ee66cab1e7a0fd2ccfb0992a0e4b5e940196d)

- **作者**: bjf-frz
- **时间**: 2026-09-10T14:27:16Z
- **提交信息**: [Perf] Use UVA-backed contents for MRV2 apply_write (#55819)

Signed-off-by: bjf-frz <frz123db@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [7d8d71e](https://github.com/vllm-project/vllm/commit/7d8d71e9897e44f0b148cec117291387ea26ed33)

- **作者**: Alexander Crettenand
- **时间**: 2026-09-10T13:49:35Z
- **提交信息**: [Bugfix] Qwen3-VL(-MoE): pass architectures to with_hf_config for pipeline parallelism (#43272)

Signed-off-by: Xonder <xonder@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [364679f](https://github.com/vllm-project/vllm/commit/364679feabbbd0243ca97095cab1fe3dcbf782f4)

- **作者**: Harry Mellor
- **时间**: 2026-09-10T13:49:17Z
- **提交信息**: [CI] Enable ruff `INP` to require `__init__.py` under `vllm/` (#56264)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [f9083cb](https://github.com/vllm-project/vllm/commit/f9083cb83af44debe290f3753ca2effc292ea1c1)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-10T13:43:08Z
- **提交信息**: [Mypy] Fix typing for R/S models (#54157)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [73fb191](https://github.com/vllm-project/vllm/commit/73fb19151f4ff461196d7fb5d82e9cb4d57234f6)

- **作者**: siyu
- **时间**: 2026-09-10T13:22:17Z
- **提交信息**: [Fast Start] Support fp4 (#55465)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [40e6042](https://github.com/vllm-project/vllm/commit/40e6042ec83eb8f2971f21043a5da40496bd188a)

- **作者**: YoavMiron
- **时间**: 2026-09-10T12:26:31Z
- **提交信息**: [Feature][Spec Decode] MTP with separate (possibly quantized) lm head for nemotron (#54574)

Signed-off-by: Yoav Miron <yomiron@nvidia.com>
Signed-off-by: YoavMiron <yomiron@nvidia.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>

### [9b959b8](https://github.com/vllm-project/vllm/commit/9b959b86577c082c0b2bf9e2c22263255a36ad83)

- **作者**: Roger Wang
- **时间**: 2026-09-10T12:16:26Z
- **提交信息**: [Model] DeepSeek-V4.1-Flash Model Definitions (#56228)

Signed-off-by: Roger Wang <hey@rogerw.io>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Codex <noreply@openai.com>

### [e83d57d](https://github.com/vllm-project/vllm/commit/e83d57d8ae14e240e2779c37db58b6dacd21bab2)

- **作者**: AlexHuang
- **时间**: 2026-09-10T11:42:31Z
- **提交信息**: [Doc] Sync KV event medium terminology after #48123 (#51646)

Signed-off-by: Alex <jihui.huang@daocloud.io>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [93911fc](https://github.com/vllm-project/vllm/commit/93911fcf68117f25a6a13942804f8c51dc31d465)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-10T10:58:05Z
- **提交信息**: [NIXL][PCP] Report replicated-PCP ranks > 0 as done sending instead of hiding them (#53903)

Signed-off-by: Lucas Wilkinson <lwilkinson@neuralmagic.com>
Signed-off-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [08426d5](https://github.com/vllm-project/vllm/commit/08426d51ef1dd2b86921b9810e9d8b966f97a63a)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-10T10:19:39Z
- **提交信息**: [Docs][Security] Clarify reporter credit and CVE publication timing (#55476)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [86aca66](https://github.com/vllm-project/vllm/commit/86aca6619161b308d675c753f228201e70b59ed7)

- **作者**: Wentao Ye
- **时间**: 2026-09-10T09:57:01Z
- **提交信息**: [Kimi K3 Perf] Avoid KDA mixed-batch gather/scatter, 5.2%~7.7% E2E Throughput Improvement (#56159)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [c9355e2](https://github.com/vllm-project/vllm/commit/c9355e25e8cfdc0548a5034f7bc148e1760e82d2)

- **作者**: Jakub Byczkowski
- **时间**: 2026-09-10T09:48:00Z
- **提交信息**: [XPU][Bugfix] Add forward_xpu to Ernie4_5_VLRotaryEmbedding (#55942)

Signed-off-by: Jakub Byczkowski <jakub.byczkowski@intel.com>
Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com>

### [6fd08c4](https://github.com/vllm-project/vllm/commit/6fd08c45e696999b403b64835ae44d322efaab35)

- **作者**: Jakub Byczkowski
- **时间**: 2026-09-10T09:47:29Z
- **提交信息**: [XPU][Bugfix] Fix FalconH1 pipeline-parallel execution (#55913)

Signed-off-by: Jakub Byczkowski <jakub.byczkowski@intel.com>
Co-authored-by: Copilot <175728472+Copilot@users.noreply.github.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [fe26c70](https://github.com/vllm-project/vllm/commit/fe26c705f7099da3b155b3cb6218f013bb308e63)

- **作者**: zexplorerhj
- **时间**: 2026-09-10T09:46:56Z
- **提交信息**: [Model] Add Bailing V3 VL support (#55921)

Signed-off-by: zexplorerhj <zhjoneson@163.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [6ff479e](https://github.com/vllm-project/vllm/commit/6ff479e1f798048829f884b4229f28c9b9b0c8d7)

- **作者**: Giuseppe Grossi
- **时间**: 2026-09-10T09:17:41Z
- **提交信息**: [ROCm] Add better kv dtype error discoverability (#55236)

Signed-off-by: Giuseppe Grossi <ggrossi@amd.com>

### [b28c3e1](https://github.com/vllm-project/vllm/commit/b28c3e1568bfae930f61d4b24940e47528c85d4a)

- **作者**: Toby Mao
- **时间**: 2026-09-10T08:39:24Z
- **提交信息**: [BugFix] Retain both replay boundaries so an EAGLE resend of a block-aligned prompt still hits (#54713)

Signed-off-by: tobymao <toby.mao@gmail.com>

### [1768273](https://github.com/vllm-project/vllm/commit/1768273c13d8e083aa07d48f0fb79c05cec39df5)

- **作者**: Jared Wen
- **时间**: 2026-09-10T08:28:33Z
- **提交信息**: [Perf][GLM-5.3-Flash] Decode hot-path cleanups: strided KDA recurrent inputs, NoPE MQA query without concat, no duplicate router GEMM (#55736)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b47b01c](https://github.com/vllm-project/vllm/commit/b47b01cf3383d50a5fae8569cadcbd0736076234)

- **作者**: Bugen Zhao
- **时间**: 2026-09-10T08:15:06Z
- **提交信息**: [Model][Frontend] Support DeepSeek-V4.1-Flash in Rust and Python frontends (#56208)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [9521c60](https://github.com/vllm-project/vllm/commit/9521c60bdc0ccd1264961c284c64f4873335aed1)

- **作者**: kliuae
- **时间**: 2026-09-10T07:37:54Z
- **提交信息**: [ROCm][Perf] Kimi-K3 Fused kernels for KDA prefill reland (#54038)

Signed-off-by: kliuae <kuanfu.liu@embeddedllm.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Signed-off-by: kliuae <17350011+kliuae@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [be1cb98](https://github.com/vllm-project/vllm/commit/be1cb9834b3d74114f4d426068d2bce57c9912a0)

- **作者**: Yongye Zhu
- **时间**: 2026-09-10T07:35:59Z
- **提交信息**: [Kernel] Optional Q-norm in fused DSv4 MLA epilogue; group_size=32 for packed FP8 quant (#56215)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [9e25706](https://github.com/vllm-project/vllm/commit/9e2570656013a90cb601b391723af4bf9b3207d4)

- **作者**: Flora Feng
- **时间**: 2026-09-10T07:04:29Z
- **提交信息**: [Bugfix] Tolerate misspelled DSML tool_calls wrapper (#56141)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-11
**监控日期**: 2026-09-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6759
- **最后更新**: 2026-09-11T00:04:13Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 11
- **主要提交者**: wangyu, tlysanhuo, Guangjian Dong

## AI分析总结

# vllm-omni 昨日提交批次分析（14 条）

## 1. 主要更新类型

本批次以 **Bug 修复与 CI/构建稳定性** 为主，兼有**功能增强、性能优化与重构**：

- **Bug 修复（约 6 条）**：扩散 LoRA 适配器未绑定层时的失败处理、视频预热缓存保留与取消重启延迟、扩散 worker 关闭升级、HWR 域初始化锁等待、Qwen3-Omni VAD E2E 稳定性等。
- **CI/Build（3 条）**：恢复 post-merge L3 的 diff-aware 源过滤、CUDA/NPU 管道的源文件依赖感知、layerwise offload 内存测量隔离。
- **功能/性能（3 条）**：Cosmos3 action policy 改进、Cosmos3 混合 W8A8/W8A16 与 W4A4/W4A16 去噪量化、视频媒体契约类型化。
- **重构/杂项（2 条）**：API server 辅助函数迁出 api_server、safetensors 保留诊断工具。

## 2. 关键变更点与项目方向

- **量化与模型支持深化**：Cosmos3 引入混合精度去噪（W8A8/W8A16、W4A4/W4A16），契合项目"易用、快速、低成本的全模态模型服务"定位，直接降低推理成本。
- **扩散（Diffusion）链路加固**：LoRA 绑定校验、worker 关闭升级、视频缓存与媒体契约类型化，显示项目正系统性提升扩散推理的健壮性与可观测性。
- **CI 精细化**：diff-aware 源过滤与依赖感知，说明项目在规模化后追求"只跑受影响测试"，提升合并效率。
- **架构解耦**：API server 辅助函数外迁，属于 P0.2 分阶段重构，为后续模块化铺路。

## 3. 对项目的影响与潜在意义

- 修复类提交直接提升**生产可用性**，尤其扩散 LoRA 与视频预热问题会影响真实服务稳定性。
- 量化支持扩展意味着**显存与吞吐优化**，对多模态大模型部署意义重大。
- CI 稳定性与 diff-aware 过滤降低维护成本，保障高频合并下的质量。
- 重构与诊断工具（safetensors retention）增强**可维护性与问题定位能力**。

## 4. 值得关注的技术点

- Cosmos3 混合量化方案（W8A8/W8A16、W4A4/W4A16）如何在去噪中平衡精度与速度。
- 类型化的 pre-D2H 视频媒体契约，可能成为后续视频管道的统一接口。
- 扩散 worker 关闭"升级并保留幸存者"策略，涉及分布式容错设计。
- HWR 域初始化锁等待限界，反映并发初始化中的死锁/阻塞治理。

## 5. 结合 README 的项目发展影响

README 强调"为所有人提供简单、快速、低成本的全模态模型服务"。本批次通过**量化降本、扩散链路加固、CI 提效、架构解耦**四条主线，正好对应"fast/cheap/easy"三大目标：量化与缓存优化支撑"fast & cheap"，稳定性修复与重构支撑"easy & reliable"。整体看，项目正从功能扩张期进入**稳定性、性能与工程化并重**的成熟阶段，为多模态（文本、图像、视频、音频）统一服务奠定更扎实的基础。

## 详细提交记录

### [ffcaaa9](https://github.com/vllm-project/vllm-omni/commit/ffcaaa9439823d9b927d201397bb9d4db7218f14)

- **作者**: Guangjian Dong
- **时间**: 2026-09-10T18:45:28Z
- **提交信息**: [Bugfix] Fail when a diffusion LoRA adapter binds no layer (#7349)

Signed-off-by: Guangjian <hiro20833@gmail.com>

### [627630d](https://github.com/vllm-project/vllm-omni/commit/627630d7e4725d94c84b64e9996f97bdec2044fe)

- **作者**: wangyu
- **时间**: 2026-09-10T16:11:27Z
- **提交信息**: [BugFix][CI] Restore diff-aware source filtering for post-merge L3 (#7371)

Signed-off-by: wangyu <410167048@qq.com>

### [05ab509](https://github.com/vllm-project/vllm-omni/commit/05ab5092695169ec711c2a0462e90e1b194968ad)

- **作者**: MaciejBalaNV
- **时间**: 2026-09-10T14:32:50Z
- **提交信息**: Cosmos3 action policy improvements (#6460)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: MaciejBalaNV <mbala@nvidia.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [c8bef00](https://github.com/vllm-project/vllm-omni/commit/c8bef008ebad9913cc7990eb420df5cbd322d20e)

- **作者**: psv666
- **时间**: 2026-09-10T14:16:57Z
- **提交信息**: [Bugfix] Fix video prewarm cache retention and cancel-restart delay (#7363)

Signed-off-by: psv666 <2693925048@qq.com>

### [e540dfb](https://github.com/vllm-project/vllm-omni/commit/e540dfb72f0439be08c26fe61912d8df572fdc7c)

- **作者**: tlysanhuo
- **时间**: 2026-09-10T13:44:28Z
- **提交信息**: [Test] Use public render_jinja_template in MiniCPM-o native template test (#7362)

Signed-off-by: tly <2200895168@qq.com>

### [43a476c](https://github.com/vllm-project/vllm-omni/commit/43a476c1e5817cedfdf706a6d62c867a43cd5065)

- **作者**: wkutak
- **时间**: 2026-09-10T11:51:09Z
- **提交信息**: [Model] Add Cosmos3 mixed W8A8/W8A16 and W4A4/W4A16 denoising (#6560)

Signed-off-by: Rahul Steiger <rsteiger@aws-cmh-slurm-1-vscode-04.cm.cluster>
Signed-off-by: Wojciech Kutak <wkutak@nvidia.com>
Co-authored-by: Rahul Steiger <rsteiger@nvidia.com>

### [d8d4062](https://github.com/vllm-project/vllm-omni/commit/d8d4062547899d71b9073649f404e61658136a68)

- **作者**: andyluo7
- **时间**: 2026-09-10T09:58:24Z
- **提交信息**: [CI] Isolate layerwise offload memory measurements (#6938)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [f11bf1a](https://github.com/vllm-project/vllm-omni/commit/f11bf1a05d8dff5d9b03d0012fb9d3dca3bc6b05)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-10T09:57:20Z
- **提交信息**: [Misc] Add standalone safetensors retention diagnostic (#7145)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [ce27ee6](https://github.com/vllm-project/vllm-omni/commit/ce27ee6038bb188ed874f024ebae431d809d8b12)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-10T09:56:44Z
- **提交信息**: [Bugfix] Escalate diffusion worker shutdown and retain survivors (#7126)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [7576c4c](https://github.com/vllm-project/vllm-omni/commit/7576c4ceb98c2219a3f54b295d27be8b5fed3e31)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-10T09:56:27Z
- **提交信息**: [Bugfix] Bound HWR domain initialization lock waits (#7128)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [a2486dd](https://github.com/vllm-project/vllm-omni/commit/a2486dd00bcc4f6206ebfe4c99f40e8a784e8d06)

- **作者**: NancyFyong
- **时间**: 2026-09-10T09:50:54Z
- **提交信息**: [Core][Diffusion] Add a typed pre-D2H video media contract (#6615)

Signed-off-by: NancyFyong <NancyFyong@users.noreply.github.com>
Signed-off-by: Samit <285365963@qq.com>
Co-authored-by: NancyFyong <NancyFyong@users.noreply.github.com>
Co-authored-by: Samit <285365963@qq.com>

### [5b927b7](https://github.com/vllm-project/vllm-omni/commit/5b927b7ceb92d9b1998e22d50cdc4ee400db08d0)

- **作者**: wangyu
- **时间**: 2026-09-10T08:40:01Z
- **提交信息**: [CI/Build] Diff-aware source_file_dependencies for CUDA/NPU pipelines (#6597)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [a7c295d](https://github.com/vllm-project/vllm-omni/commit/a7c295d5442820d7390a39968aea5b9f135bbb2e)

- **作者**: LHXuuu
- **时间**: 2026-09-10T07:40:49Z
- **提交信息**: [CI] Stabilize Qwen3-Omni Server VAD E2E (#7356)

Signed-off-by: LHXuuu <xulianhao.xlh@antgroup.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [bbac4df](https://github.com/vllm-project/vllm-omni/commit/bbac4df7d3392791ce64a574c4f78c18927e61fc)

- **作者**: herotai214
- **时间**: 2026-09-10T07:03:21Z
- **提交信息**: [Refactor] P0.2: Migrate API server helpers out of api_server (#5453)

Signed-off-by: herotai214 <herotai214@gmail.com>

---
