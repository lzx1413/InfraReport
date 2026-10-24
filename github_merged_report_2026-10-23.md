# GitHub Stars 合并报告 - 2026-10-23

**合并日期**: 2026-10-24
**监控日期**: 2026-10-23
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


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2264
- **最后更新**: 2026-10-24T00:29:53Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

### 主要更新类型
- **功能新增**：两个提交均为功能新增，涉及模型导出、检查点管理和多模态扩展。
- **配置与工具优化**：包含运行时配置分层和共享助手，属于工程改进。
- **多模态扩展**：添加SeedOmni TextEncoder，增强文本模态支持。

### 关键变更点与项目整体方向的关系
- **统一FP8/FP4导出**：对齐DeepSeek-V4在VeRL和Hugging Face中的检查点保存，提升量化模型的互操作性，符合项目“模型中心化”目标。
- **添加SeedOmni TextEncoder**：引入新的文本编码器，扩展多模态能力，直接支持“任何模态模型训练”的愿景。
- **运行时配置分层**：通过层次化配置提升灵活性，使训练配方更易定制，强化“配方库”概念。
- **共享助手**：提供跨组件复用工具，促进代码一致性和开发效率。

### 对项目的影响和潜在意义
- **提升兼容性**：统一量化导出便于用户在不同框架间迁移模型，降低集成门槛。
- **增强多模态覆盖**：新增文本编码器使项目能处理文本、图像、视频等更多模态，吸引更广泛的应用场景。
- **改进开发体验**：配置分层和共享助手简化配置管理，减少重复代码，加速研究迭代。
- **推动生产就绪**：这些变更使框架更稳定、功能更全面，可能吸引更多生产环境采用。

### 值得关注的技术点
- **FP8/FP4量化**：低精度训练和推理是当前趋势，统一导出格式对性能优化和模型部署至关重要。
- **配置分层设计**：可能采用默认-环境-用户层次，支持复杂实验场景。
- **跨框架检查点兼容**：通过统一保存格式，支持VeRL和Hugging Face生态，体现项目对开源工具链的适配。
- **SeedOmni TextEncoder**：专为多模态设计的文本编码器，可能集成高效注意力机制或预训练权重。

### 基于项目背景的发展影响
VeOmni旨在提供模型中心化的分布式训练配方库，这些提交进一步巩固了该定位：
- **扩展模型支持**：添加DeepSeek-V4和SeedOmni TextEncoder，使项目能覆盖更多先进模型和模态。
- **完善工具链**：统一导出和配置管理使训练流程更顺畅，符合“Recipe Zoo”中标准化、可复用的理念。
- **强化多模态能力**：文本编码器的加入使项目从视觉扩展至文本，真正实现“任何模态”训练。
- **提升工程成熟度**：配置和共享助手的改进表明项目正从研究原型走向生产级框架。

总之，这些变更使VeOmni在多模态模型训练领域的功能更强大、工具更完善，加速了其成为分布式训练标准平台的进程。

## 详细提交记录

### [eba362d](https://github.com/ByteDance-Seed/VeOmni/commit/eba362dd4ca43b6cba53dc69c1d378cf3eda57b6)

- **作者**: Coach257
- **时间**: 2026-10-23T10:02:21Z
- **提交信息**: [model, ckpt] feat: unify DeepSeek-V4 FP8/FP4 export across VeRL and HF checkpoint save (#1344)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [aa7b2d1](https://github.com/ByteDance-Seed/VeOmni/commit/aa7b2d169fe857d9051a2fdc6cc388efb38fe45d)

- **作者**: Coach257
- **时间**: 2026-10-23T07:48:35Z
- **提交信息**: [omni, model, ckpt, config, docs, agent, ci] feat: add SeedOmni TextEncoder, runtime config layering and shared helpers (#1330)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2950
- **最后更新**: 2026-10-23T17:25:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2312
- **最后更新**: 2026-10-23T16:51:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6763
- **最后更新**: 2026-10-24T00:28:36Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 9
- **主要提交者**: eigen, Chunan Zeng, Daniel Stokes

## AI分析总结

# FlashInfer 昨日提交总结（共 37 个提交）

## 主要更新

昨日提交以性能优化为主体，兼有功能新增、Bug 修复与代码治理。性能方面涉及 mega_mhc、QSA 稀疏注意力、RMSNorm 训练、Gated DeltaProduct 解码、DSA 索引器、Frost MoE 主机提交、cuDNN prefill 计划复用、KDA 上下文并行、NVFP4 SVDQuant 等；功能新增包括 Rubin MoE 自动调优集成、PDL 排序契约测试、Cake 后端量化输出变体（FP8 group-128、NVFP4、MXFP8 融合）、MoE finalize RMSNorm、Sage-FP8 变长块稀疏注意力、causal conv1d 新变体、AutoTuner 委托协议，以及面向 SM12x 的 FP8 Prefill Attention；修复涵盖 autotuner BF16 GEMM 排名、TRT-LLM MoE workspace 查询、激活检查点下的内存泄漏与 split-K fence 正确性；另有若干"deslop"提交折叠重复、删除死代码，单条净删约 1.4 万行。

## 关键变更

FlashInfer 定位"高性能 GPU 推理内核"，本批体现三条主线。一是**按硬件代际×形状的细粒度程序库**：mega_mhc 新增尾部流水线权重暂存程序、QSA 新增 sm_80 宽网格解码、GDP 新增双头 T=1 程序，覆盖 sm_80 至 sm_107a 多代架构。二是**主机与端到端延迟削减**：cuDNN 计划复用提速 14%，Frost MoE 主机提交提速 2.85–9.77 倍。三是**自动调优基础设施生产化**：MoE 接入 autotune v2、修复冷 L2 链式测量失效、支持工作区级状态管理并与 CUDA Graph 兼容。Cake 实验后端围绕 Blackwell 全系（sm_100/103/107）及 SM110 快速迭代，走向生产可用。

模型覆盖上，针对 GLM-4.7-Flash（MLA，256/256 头维度）与 GLM-4.7（GQA，128/128）两条前缀注意力路径，复用 FMHA v2 模板完成代码生成与 C++ 分发，新增特化分支及 GQA 索引逻辑，同时保留 DeepSeek 192/128 旧路径以保兼容。调优上，Hopper 平台 MXFP4 权重×FP8 激活 MegaMoE 新增 5 个 K128 折叠候选，目标形状候选池由 3 增至 8。

## 影响与技术关注点

性能收益可量化：QSA 在 A100 提速至 1.085×，GDP 大 batch 提速 1.13–1.18×，Sage-FP8 几何平均提速 1.09–1.22×，KDA 相比 FLA 加速 1.46–2.79 倍。技术点包括：PDL 用于流间重叠与竞态防护；冷 L2 链式调优揭示约 6.3 µs 固定开销地板；弱引用管理 workspace 将激活检查点下显存滞留由 4482 MiB 降为 0；MXFP8 scale 归约与 MNNVL cluster 协同设计；前缀注意力 QK 由 192 NoPE + 64 RoPE 组成、压缩 latent KV 缓存不纳入 API 输入契约的解耦设计。FP8 Prefill 降低 GLM-4.7 系列在最新 GPU 上的推理门槛，旧路径保留使升级平滑。验证普遍附带单测、trace 一致性校验与全精度参考对比，其中一项标注"未运行完整仓库测试套件"，存在集成风险。MegaMOE 带来 hidden size 128 对齐的破坏性变更，升级需留意。

## 项目发展意义

综合来看，FlashInfer 正从单一内核集合演进为"推理+训练+自动调优"全栈平台：内核库按硬件与形状细分为数十变体并智能分发，多后端（CuTe DSL/Cake/cuDNN）覆盖量化推理与线性注意力训练，正确性契约由显式测试锁定。本次提交从**纵向**（新模型+新架构的注意力覆盖）与**横向**（既有算子调优空间深度挖掘）两个维度强化该目标，巩固其在大模型推理加速领域"即插即用、性能领先"Kernel 库的地位。

## 详细提交记录

### [b75cff3](https://github.com/flashinfer-ai/flashinfer/commit/b75cff30e9cebb455f5c1bf6fbd0453d5fac8185)

- **作者**: eigen
- **时间**: 2026-10-23T23:11:12Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): weight-staging tailpipe program for the hidden-4096 BF16 route at many task waves (#7123)

`flashinfer.mega_mhc` (`prepare_mega_mhc`, programs under
`flashinfer/experimental/deepgemm_mega_mhc`) contains programs for the
fused manifold-constrained hyper-connection (mHC) inference step. Before
this PR, it ships 18 programs:

- **Existing variants:** 14 hidden-5120 FP8-E4M3-output variants
(shifted / unshifted, shared-scale, `col` / `extra` scale layouts, split
counts 16 / 20 / 27 / 40) on `sm_100a` / `sm_103a`. On `sm_107a` it
ships four programs: the hidden-4096 BF16-output program
(`sf_layout="bf16"`); its tailpipe twin from the previous PR of this
series (#7121), which the loader runs when the token count gives at most
22 splits (T >= 385 on a 208-SM GPU); and the hidden-4096 FP8 group-128
(`sf_layout="fp8_group128"`) and NVFP4 (`sf_layout="nvfp4"`) output
variants.
- **This PR:** a third hidden-4096 BF16-output program on `sm_107a`. It
is the weight-staging build of the tailpipe program: each CTA stages the
RMSNorm weight once in shared memory, and the tail reads it from there.
The loader uses it when the token count gives at most 16 splits and the
tasks run in five or more waves of the launch grid. On a 208-SM GPU that
means T >= 3329 tokens. At every other token count the loader keeps the
program it dispatched before this PR: the BF16 program at 32 and 64
splits, and the tailpipe program at the other counts up to 22.

The dispatched program takes the same plan, arguments and outputs as the
shipped programs (`new_residual` BF16, `y_bf16` BF16, `new_post_mix`
FP32 and `new_comb_res_mix` FP32).

The baseline is the program the loader dispatched before this PR at each
token count, which is the previous Cake version of this route: the BF16
program at T <= 256 and the tailpipe program at T >= 512. Speedup is the
baseline's time divided by the time of the program the loader picks with
this PR. On this GPU the switch to the new program is at T = 3329, the
first token count with 16 splits over five waves, so the T = 2048 row is
below the switch and the T = 4096 row above it. At T <= 2048 (64, 32, 22
or 13 splits), both sides run the same program, so those rows measure
noise only; they stay between 0.998× and 1.004× (within ±0.4 %). At T =
4096 and 8192 (16 splits), the loader runs the weight-staged tailpipe
program, and the speedup is 1.019× at both.

**NVIDIA R200 (`sm_107a`, 208 SMs), driver 615.71.09, CUDA 13.4 toolkit
(nvcc 13.4.92); SM clock 2386–2415 MHz during the measurement. Both
sides were measured in one process on the same GPU as CUPTI kernel time,
with cold L2 and three interleaved ABBA groups of 64 iterations per arm;
the median is reported.**

**Hidden-4096 BF16 output, program dispatched with this PR vs the
previous dispatch:**

| T (tokens) | Program dispatched (this PR) | Splits | Previous
dispatch, µs (A) | This PR (dispatched program), µs (B) | Speedup (A /
B) |
|---:|:--|---:|---:|---:|---:|
| 1 | BF16 | 64 | 8.712 | 8.704 | 1.001× |
| 4 | BF16 | 64 | 8.896 | 8.880 | 1.002× |
| 8 | BF16 | 64 | 8.896 | 8.864 | 1.004× |
| 16 | BF16 | 64 | 9.216 | 9.184 | 1.003× |
| 32 | BF16 | 64 | 9.384 | 9.376 | 1.001× |
| 64 | BF16 | 64 | 9.648 | 9.664 | 0.998× |
| 128 | BF16 | 64 | 10.272 | 10.256 | 1.002× |
| 256 | BF16 | 32 | 11.760 | 11.776 | 0.999× |
| 512 | tailpipe | 22 | 13.840 | 13.864 | 0.998× |
| 1024 | tailpipe | 13 | 17.880 | 17.888 | 1.000× |
| 2048 | tailpipe | 13 | 28.160 | 28.160 | 1.000× |
| 4096 | tailpipe (weight staged) | 16 | 54.064 | 53.064 | 1.019× |
| 8192 | tailpipe (weight staged) | 16 | 110.680 | 108.648 | 1.019× |

Cake's other variants of this kernel are the 14 hidden-5120 FP8-output
programs on `sm_100a` / `sm_103a` and the hidden-4096 FP8 group-128 and
NVFP4 output programs on `sm_107a`; the new program ships on `sm_107a`
only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* BF16 workloads now select an execution path based on split count and
workload size, including a path optimized for larger task grids.
* The available BF16 paths produce bitwise-identical outputs, preserving
result consistency across workload sizes.

* **Compatibility**
* Quantized output layouts continue to use their existing execution path
and are unaffected by the BF16 path selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3a4e382](https://github.com/flashinfer-ai/flashinfer/commit/3a4e382bc46ee27f3457d6cbbc299de0b1c02644)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-23T22:57:16Z
- **提交信息**: feat(moe_ep): integrate Rubin automatic tuning with autotune v2 (#6535)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `knobs="auto"` to the Rubin MegaMoE backends and route online and
offline tuning through `autotune_v2()`. Keep the native candidate
enumeration, sampled correctness checks and default measurement
boundary. The offline CLI still searches afresh and now writes
FlashInfer results by default, alongside the MegaMoE cache file.

Automatic selection checks FlashInfer records first, then the MegaMoE
file, and writes the selected record back to the MegaMoE file on cache
hits as well. Cache decisions and preparation are coordinated across the
layer's EP group. Results use the managed entries provided by #6534;
MegaMoE retains its capacity and compatibility lookup. MegaMoE file
output uses the shared cache version and routing fields from #5666.
Explicit `tuning_buckets` or `round_up=True` overrides raise before
selection because this adapter uses prepared workspace capacities.

Tune before capture in the normal flow. If a later Python forward needs
selection, replace the captured default workspace and retain its old
storage for existing graphs. Explicit workspace handles allow the caller
to control when that storage is released. Selection state belongs to
each workspace, and switching cache stores or policies reselects the
corresponding winner. `get_tuned_knobs(workspace=handle)` reads that
handle's result without allocation. Reacquire borrowed output views
after selection before capture.

Automatic workspace creation accepts `live_tokens` with a warning:
selection uses the actual warmup or forward batch size. Fixed workspaces
retain offline-profile selection.

## 🔍 Related Issues

Uses the shared tuning protocol merged in #6534.

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

447 host tests passed across the Rubin protocol/CLI, cache,
configuration, workspace and getter suites; ten GPU-dependent tests were
skipped. Regressions cover both routing values, deprecated keyword
aliases, preservation of other backend records and MegaMoE file output
on a managed-cache hit. Changed-file and commit hooks passed, including
mypy and Ruff.

On the rebased head, native Rubin EP2 passed all 20 automatic-tuning
cases and nine routing-oracle cases per rank, with no failures or skips.
A separate CUPTI run required real tracing and passed without CUDA-event
fallback. Three offline CLI invocations searched six capacity buckets,
including a repeated search with existing records. Fresh-process replay
passed with MegaMoE file lookup disabled. All four managed records match
the MegaMoE file, which uses the shared version and canonical routing
fields.

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

### [179af3f](https://github.com/flashinfer-ai/flashinfer/commit/179af3f6e08caf741ba535049f996f4f9aba7f81)

- **作者**: eigen
- **时间**: 2026-10-23T22:56:49Z
- **提交信息**: perf(cake_qsa_nvfp4): sm_80 launches the previous release's decode program on wide, long-stream grids (#7133)

This PR changes the Cake backend of
`flashinfer.sparse.qsa_sparse_paged_attention` (`backend="cake"`). It is
a gated sparse paged GQA decode attention kernel over an NVFP4 (E2M1) KV
cache with E4M3 block scales, BF16 queries, 256-dim heads and one query
token per row. The package ships one data-type variant that serves both
the NHD and HND layouts, in two forms with three programs in all: a
split form (a decode program plus a merge program) and a fused
co-resident form (one decode program, used on sm_90a when the grid
fits). This PR adds a fourth program for sm_80 only, the previous
release's whole-tile decode schedule. The host launches it when the call
uses the split form, the decode grid exceeds two CTAs per SM, and each
CTA streams at least 16 tiles of 64 tokens (1024 selected tokens). On
both A100 units, it makes the 128-row calls 1.060x to 1.085x faster than
the package before this PR (#7103). Rows 1 to 64 run the same program on
both sides and stay within noise of 1.00x.

**NVIDIA A100 80GB PCIe (sm_80), PyTorch 2.14.1+cu130 runtime, kernels
JIT-built with nvcc 13.4. GPU time of the whole call (decode + merge),
memset L2 flush before every call, 3 groups x 64 iterations, 2 KV heads,
2051 selected tokens per row; speedup = previous / this PR.**

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 34.75 | 34.42 | 1.010x |
| NHD | 2 | 34.85 | 34.70 | 1.004x |
| NHD | 4 | 35.23 | 35.07 | 1.005x |
| NHD | 8 | 35.36 | 35.34 | 1.000x |
| NHD | 16 | 36.67 | 36.67 | 1.000x |
| NHD | 32 | 57.50 | 57.63 | 0.998x |
| NHD | 64 | 109.73 | 109.60 | 1.001x |
| NHD | 128 | 198.50 | 182.91 | 1.085x |
| HND | 1 | 35.62 | 35.47 | 1.004x |
| HND | 2 | 36.38 | 36.26 | 1.004x |
| HND | 4 | 36.51 | 36.38 | 1.004x |
| HND | 8 | 35.86 | 35.79 | 1.002x |
| HND | 16 | 37.84 | 37.92 | 0.998x |
| HND | 32 | 59.73 | 59.73 | 1.000x |
| HND | 64 | 111.57 | 112.21 | 0.994x |
| HND | 128 | 198.53 | 185.63 | 1.069x |

**NVIDIA A100-PCIE-40GB (sm_80), PyTorch 2.14.1+cu130 runtime, kernels
JIT-built with nvcc 13.4. GPU time of the whole call (decode + merge),
memset L2 flush before every call, 3 groups x 64 iterations, 2 KV heads,
2051 selected tokens per row; speedup = previous / this PR.**

| layout | rows | previous (us) | this PR (us) | speedup |
|---|---:|---:|---:|---:|
| NHD | 1 | 40.74 | 40.66 | 1.002x |
| NHD | 2 | 41.30 | 41.22 | 1.002x |
| NHD | 4 | 40.54 | 40.32 | 1.006x |
| NHD | 8 | 40.10 | 40.13 | 0.999x |
| NHD | 16 | 39.55 | 39.63 | 0.998x |
| NHD | 32 | 62.23 | 62.70 | 0.992x |
| NHD | 64 | 121.35 | 121.09 | 1.002x |
| NHD | 128 | 218.48 | 201.83 | 1.083x |
| HND | 1 | 40.69 | 40.74 | 0.999x |
| HND | 2 | 39.60 | 40.34 | 0.982x |
| HND | 4 | 39.06 | 39.06 | 1.000x |
| HND | 8 | 41.34 | 41.46 | 0.997x |
| HND | 16 | 47.62 | 47.95 | 0.993x |
| HND | 32 | 64.85 | 64.93 | 0.999x |
| HND | 64 | 123.81 | 123.55 | 1.002x |
| HND | 128 | 220.37 | 207.99 | 1.060x |

Every other call still uses the kernel's existing Cake programs (the
split-form decode and merge, and the fused co-resident decode); the
kernel covers sm_80 and sm_90a, and this PR leaves the sm_90a programs
unchanged (their compiled SASS is identical to the previous ones).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture- and workload-aware kernel selection, including
whole-tile decoding for qualifying split workloads on SM80.
* Expanded support for selecting builds across SM80 and SM90a
architectures.
* **Documentation**
* Updated hardware validation status to include H100 and A100 80 GB and
40 GB PCIe devices.
* **Tests**
* Added coverage for workload-based selection, architecture-specific
behavior, and invalid inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [28b2c6d](https://github.com/flashinfer-ai/flashinfer/commit/28b2c6d93f33ef2fad0756b3f65bdf77c8bb70cd)

- **作者**: eigen
- **时间**: 2026-10-23T22:53:50Z
- **提交信息**: fix(cake_rmsnorm): the backward no longer stalls behind kernels resident on other streams (SM100 / SM103 / SM107) (#7131)

`cake_rmsnorm_train` is Cake's RMSNorm training kernel: one data type
(BF16 activations and weight, FP32 `rstd` and deterministic FP32
`dweight`) in four variants, plain and residual-fused, each forward and
backward. This PR changes the backward of both the plain and the
residual-fused variant on sm_100a, sm_103a and sm_107a, at every
supported hidden size H (512, 1536, 2048, 4096 and 6144). The baseline
is the previous Cake version, the shipped build of PR #6997. The
backward is a pair of plain launches (a chunk-claiming main kernel and a
`dweight` reduce kernel under programmatic dependent launch) in place of
a whole-device cooperative launch, so it does not wait behind a kernel
resident on another stream (#7038): in the issue's repro, with a
one-thread kernel resident on a side stream, the previous backward ran
10-280x slower and the new one at most 1.13x slower (at T = 65536).
Running alone, the new backward is slower than the previous Cake version
on every row below (every ratio is under 1.000x). This PR trades that
standalone latency for not waiting behind a resident kernel. `dweight`
stays deterministic (bitwise identical across launch grids), but its
summation order differs from the previous version's.

Both versions run in the same process on the same GPU. Latencies are
CUPTI kernel-active times (T x H input, cold L2 before every launch),
each the median of 3 counterbalanced paired groups. In the Pass column,
`bwd` is the backward (in the new version, both kernels of the pair) and
`step` is forward + backward. Speedup is previous / new latency; below
1.000x the new version is slower. The forward programs are rebuilt from
the same source and their latency is unchanged (median ratios
0.996-1.007 against the previous build), so forward rows are not listed.
Both versions are compiled with CUDA 13.4 (previous Cake: the shipped
FlashInfer build of #6997, nvcc 13.4; new Cake: NVRTC 13.4).

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 4.80 | 6.46 | 0.743x |
| 512 | 256 | step | 6.91 | 8.54 | 0.809x |
| 512 | 1024 | bwd | 5.25 | 7.26 | 0.722x |
| 512 | 1024 | step | 7.46 | 9.50 | 0.785x |
| 512 | 4096 | bwd | 7.74 | 10.66 | 0.727x |
| 512 | 4096 | step | 10.75 | 13.22 | 0.814x |
| 512 | 14928 | bwd | 12.61 | 19.74 | 0.639x |
| 512 | 14928 | step | 19.33 | 26.21 | 0.737x |
| 512 | 15288 | bwd | 13.25 | 20.26 | 0.654x |
| 512 | 15288 | step | 19.81 | 26.98 | 0.734x |
| 512 | 15566 | bwd | 12.99 | 20.35 | 0.638x |
| 512 | 15566 | step | 19.90 | 26.69 | 0.746x |
| 512 | 15590 | bwd | 12.80 | 20.35 | 0.629x |
| 512 | 15590 | step | 19.81 | 27.10 | 0.731x |
| 512 | 16114 | bwd | 12.90 | 20.51 | 0.629x |
| 512 | 16114 | step | 20.10 | 27.36 | 0.735x |
| 512 | 16132 | bwd | 13.12 | 20.58 | 0.638x |
| 512 | 16132 | step | 20.35 | 27.58 | 0.738x |
| 512 | 16164 | bwd | 13.12 | 20.48 | 0.641x |
| 512 | 16164 | step | 20.26 | 27.52 | 0.736x |
| 512 | 16263 | bwd | 13.12 | 20.51 | 0.640x |
| 512 | 16263 | step | 20.38 | 27.49 | 0.742x |
| 512 | 32768 | bwd | 21.06 | 31.04 | 0.678x |
| 512 | 32768 | step | 33.22 | 43.46 | 0.764x |
| 512 | 65536 | bwd | 36.48 | 51.52 | 0.708x |
| 512 | 65536 | step | 58.18 | 73.76 | 0.789x |
| 1536 | 256 | bwd | 4.96 | 7.38 | 0.672x |
| 1536 | 256 | step | 7.20 | 9.46 | 0.761x |
| 1536 | 1024 | bwd | 6.66 | 9.15 | 0.727x |
| 1536 | 1024 | step | 9.15 | 11.68 | 0.784x |
| 1536 | 4096 | bwd | 10.98 | 16.61 | 0.661x |
| 1536 | 4096 | step | 16.74 | 22.05 | 0.759x |
| 1536 | 14928 | bwd | 26.59 | 31.17 | 0.853x |
| 1536 | 14928 | step | 41.92 | 45.86 | 0.914x |
| 1536 | 15288 | bwd | 27.42 | 32.93 | 0.833x |
| 1536 | 15288 | step | 42.62 | 47.81 | 0.892x |
| 1536 | 15566 | bwd | 28.06 | 32.67 | 0.859x |
| 1536 | 15566 | step | 43.58 | 48.06 | 0.907x |
| 1536 | 15590 | bwd | 27.65 | 32.42 | 0.853x |
| 1536 | 15590 | step | 43.49 | 48.32 | 0.900x |
| 1536 | 16114 | bwd | 28.22 | 33.54 | 0.842x |
| 1536 | 16114 | step | 44.38 | 49.44 | 0.898x |
| 1536 | 16132 | bwd | 28.10 | 33.02 | 0.851x |
| 1536 | 16132 | step | 44.77 | 49.28 | 0.908x |
| 1536 | 16164 | bwd | 28.19 | 33.31 | 0.846x |
| 1536 | 16164 | step | 44.83 | 49.79 | 0.900x |
| 1536 | 16263 | bwd | 28.32 | 33.34 | 0.849x |
| 1536 | 16263 | step | 45.12 | 49.76 | 0.907x |
| 1536 | 32768 | bwd | 52.13 | 55.78 | 0.935x |
| 1536 | 32768 | step | 82.98 | 86.50 | 0.959x |
| 1536 | 65536 | bwd | 96.51 | 101.41 | 0.952x |
| 1536 | 65536 | step | 154.88 | 161.70 | 0.958x |
| 2048 | 256 | bwd | 5.70 | 7.55 | 0.754x |
| 2048 | 256 | step | 7.90 | 9.73 | 0.812x |
| 2048 | 1024 | bwd | 7.78 | 9.98 | 0.779x |
| 2048 | 1024 | step | 10.40 | 12.58 | 0.827x |
| 2048 | 4096 | bwd | 13.02 | 18.91 | 0.689x |
| 2048 | 4096 | step | 20.16 | 26.40 | 0.764x |
| 2048 | 14928 | bwd | 34.05 | 38.05 | 0.895x |
| 2048 | 14928 | step | 53.28 | 58.66 | 0.908x |
| 2048 | 15288 | bwd | 34.98 | 39.84 | 0.878x |
| 2048 | 15288 | step | 54.78 | 61.31 | 0.894x |
| 2048 | 15566 | bwd | 35.46 | 39.65 | 0.894x |
| 2048 | 15566 | step | 55.23 | 60.99 | 0.906x |
| 2048 | 15590 | bwd | 35.46 | 39.68 | 0.894x |
| 2048 | 15590 | step | 55.33 | 60.80 | 0.910x |
| 2048 | 16114 | bwd | 36.16 | 41.12 | 0.879x |
| 2048 | 16114 | step | 56.38 | 63.23 | 0.892x |
| 2048 | 16132 | bwd | 36.22 | 41.06 | 0.882x |
| 2048 | 16132 | step | 56.61 | 62.75 | 0.902x |
| 2048 | 16164 | bwd | 36.00 | 41.09 | 0.876x |
| 2048 | 16164 | step | 56.45 | 62.88 | 0.898x |
| 2048 | 16263 | bwd | 35.87 | 41.28 | 0.869x |
| 2048 | 16263 | step | 56.35 | 63.01 | 0.894x |
| 2048 | 32768 | bwd | 66.11 | 71.30 | 0.927x |
| 2048 | 32768 | step | 106.24 | 112.29 | 0.946x |
| 2048 | 65536 | bwd | 124.19 | 129.28 | 0.961x |
| 2048 | 65536 | step | 201.44 | 215.90 | 0.933x |
| 4096 | 256 | bwd | 6.37 | 8.16 | 0.780x |
| 4096 | 256 | step | 8.74 | 10.62 | 0.822x |
| 4096 | 1024 | bwd | 9.47 | 14.21 | 0.667x |
| 4096 | 1024 | step | 13.50 | 17.63 | 0.766x |
| 4096 | 4096 | bwd | 20.80 | 29.15 | 0.714x |
| 4096 | 4096 | step | 32.64 | 41.02 | 0.796x |
| 4096 | 14928 | bwd | 62.40 | 71.52 | 0.872x |
| 4096 | 14928 | step | 98.40 | 109.06 | 0.902x |
| 4096 | 15288 | bwd | 63.81 | 72.67 | 0.878x |
| 4096 | 15288 | step | 100.06 | 110.91 | 0.902x |
| 4096 | 15566 | bwd | 65.57 | 74.62 | 0.879x |
| 4096 | 15566 | step | 102.43 | 113.44 | 0.903x |
| 4096 | 15590 | bwd | 66.14 | 74.75 | 0.885x |
| 4096 | 15590 | step | 102.85 | 113.60 | 0.905x |
| 4096 | 16114 | bwd | 66.66 | 76.26 | 0.874x |
| 4096 | 16114 | step | 105.06 | 116.98 | 0.898x |
| 4096 | 16132 | bwd | 65.95 | 76.64 | 0.861x |
| 4096 | 16132 | step | 104.48 | 116.67 | 0.896x |
| 4096 | 16164 | bwd | 66.18 | 77.34 | 0.856x |
| 4096 | 16164 | step | 104.58 | 117.34 | 0.891x |
| 4096 | 16263 | bwd | 66.53 | 76.90 | 0.865x |
| 4096 | 16263 | step | 105.15 | 117.53 | 0.895x |
| 4096 | 32768 | bwd | 125.34 | 139.23 | 0.900x |
| 4096 | 32768 | step | 201.54 | 216.93 | 0.929x |
| 4096 | 65536 | bwd | 240.13 | 264.42 | 0.908x |
| 4096 | 65536 | step | 390.64 | 436.88 | 0.894x |
| 6144 | 256 | bwd | 7.71 | 9.34 | 0.825x |
| 6144 | 256 | step | 10.75 | 12.54 | 0.857x |
| 6144 | 1024 | bwd | 11.90 | 16.67 | 0.714x |
| 6144 | 1024 | step | 17.82 | 22.30 | 0.799x |
| 6144 | 4096 | bwd | 29.86 | 33.92 | 0.880x |
| 6144 | 4096 | step | 44.10 | 50.27 | 0.877x |
| 6144 | 14928 | bwd | 88.54 | 94.78 | 0.934x |
| 6144 | 14928 | step | 142.05 | 148.93 | 0.954x |
| 6144 | 15288 | bwd | 90.24 | 95.20 | 0.948x |
| 6144 | 15288 | step | 145.06 | 150.46 | 0.964x |
| 6144 | 15566 | bwd | 92.58 | 97.95 | 0.945x |
| 6144 | 15566 | step | 148.16 | 154.40 | 0.960x |
| 6144 | 15590 | bwd | 92.22 | 97.54 | 0.946x |
| 6144 | 15590 | step | 148.34 | 154.11 | 0.963x |
| 6144 | 16114 | bwd | 95.01 | 100.10 | 0.949x |
| 6144 | 16114 | step | 152.67 | 158.34 | 0.964x |
| 6144 | 16132 | bwd | 95.78 | 99.71 | 0.961x |
| 6144 | 16132 | step | 153.12 | 157.76 | 0.971x |
| 6144 | 16164 | bwd | 95.26 | 100.13 | 0.951x |
| 6144 | 16164 | step | 152.93 | 158.62 | 0.964x |
| 6144 | 16263 | bwd | 95.49 | 99.97 | 0.955x |
| 6144 | 16263 | step | 153.60 | 158.72 | 0.968x |
| 6144 | 32768 | bwd | 189.92 | 200.74 | 0.946x |
| 6144 | 32768 | step | 303.36 | 314.72 | 0.964x |
| 6144 | 65536 | bwd | 370.66 | 382.34 | 0.969x |
| 6144 | 65536 | step | 595.10 | 606.85 | 0.981x |

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4 (previous Cake: the
shipped FlashInfer build, nvcc 13.4; new Cake: NVRTC 13.4; same process,
same GPU)

| H | T | Pass | Previous Cake (µs) | New Cake (µs) | Speedup |
|---:|---:|---|---:|---:|---:|
| 512 | 256 | bwd | 5.12 | 6.69 | 0.766x |
| 512 | 256 | step | 7.14 | 9.07 | 0.787x |
| 512 | 1024 | bwd | 5.18 | 6.94 | 0.747x |
| 512 | 1024 | step | 7.52 | 9.47 | 0.794x |
| 512 | 4096 | bwd | 7.97 | 11.78 | 0.677x |
| 512 | 4096 | step | 10.78 | 14.62 | 0.737x |
| 512 | 14928 | bwd | 13.38 | 18.75 | 0.713x |
| 512 | 14928 | step | 20.03 | 24.96 | 0.803x |
| 512 | 15288 | bwd | 13.44 | 18.85 | 0.713x |
| 512 | 15288 | step | 20.32 | 25.60 | 0.794x |
| 512 | 15566 | bwd | 13.60 | 19.30 | 0.705x |
| 512 | 15566 | step | 20.38 | 26.08 | 0.782x |
| 512 | 15590 | bwd | 13.47 | 19.20 | 0.702x |
| 512 | 15590 | step | 20.42 | 25.82 | 0.791x |
| 512 | 16114 | bwd | 13.70 | 20.19 | 0.678x |
| 512 | 16114 | step | 20.77 | 26.98 | 0.770x |
| 512 | 16132 | bwd | 13.92 | 20.13 | 0.692x |
| 512 | 16132 | step | 20.61 | 26.98 | 0.764x |
| 512 | 16164 | bwd | 13.76 | 20.26 | 0.679x |
| 512 | 16164 | step | 20.86 | 27.36 | 0.763x |
| 512 | 16263 | bwd | 13.76 | 20.45 | 0.673x |
| 512 | 16263 | step | 20.74 | 27.23 | 0.761x |
| 512 | 32768 | bwd | 22.43 | 28.83 | 0.778x |
| 512 | 32768 | step | 34.59 | 41.09 | 0.842x |
| 512 | 65536 | bwd | 38.53 | 54.59 | 0.706x |
| 512 | 65536 | step | 61.70 | 77.79 | 0.793x |
| 1536 | 256 | bwd | 5.38 | 7.42 | 0.724x |
| 1536 | 256 | step | 7.65 | 9.76 | 0.784x |
| 1536 | 1024 | bwd | 6.91 | 9.41 | 0.735x |
| 1536 | 1024 | step | 9.73 | 11.84 | 0.822x |
| 1536 | 4096 | bwd | 11.39 | 17.38 | 0.656x |
| 1536 | 4096 | step | 17.38 | 23.20 | 0.749x |
| 1536 | 14928 | bwd | 27.97 | 33.15 | 0.844x |
| 1536 | 14928 | step | 43.78 | 48.70 | 0.899x |
| 1536 | 15288 | bwd | 28.35 | 33.09 | 0.857x |
| 1536 | 15288 | step | 44.61 | 48.83 | 0.913x |
| 1536 | 15566 | bwd | 28.64 | 34.30 | 0.835x |
| 1536 | 15566 | step | 45.28 | 50.27 | 0.901x |
| 1536 | 15590 | bwd | 28.93 | 34.43 | 0.840x |
| 1536 | 15590 | step | 45.12 | 49.79 | 0.906x |
| 1536 | 16114 | bwd | 29.70 | 34.69 | 0.856x |
| 1536 | 16114 | step | 46.37 | 50.91 | 0.911x |
| 1536 | 16132 | bwd | 29.70 | 34.59 | 0.858x |
| 1536 | 16132 | step | 46.27 | 50.69 | 0.913x |
| 1536 | 16164 | bwd | 29.89 | 34.56 | 0.865x |
| 1536 | 16164 | step | 46.24 | 51.20 | 0.903x |
| 1536 | 16263 | bwd | 29.70 | 34.85 | 0.852x |
| 1536 | 16263 | step | 46.21 | 51.14 | 0.904x |
| 1536 | 32768 | bwd | 54.05 | 57.95 | 0.933x |
| 1536 | 32768 | step | 85.31 | 89.28 | 0.956x |
| 1536 | 65536 | bwd | 99.23 | 104.03 | 0.954x |
| 1536 | 65536 | step | 159.17 | 164.61 | 0.967x |
| 2048 | 256 | bwd | 6.14 | 8.19 | 0.750x |
| 2048 | 256 | step | 8.42 | 10.54 | 0.798x |
| 2048 | 1024 | bwd | 8.00 | 10.21 | 0.784x |
| 2048 | 1024 | step | 11.11 | 12.61 | 0.881x |
| 2048 | 4096 | bwd | 13.67 | 19.71 | 0.693x |
| 2048 | 4096 | step | 21.92 | 27.84 | 0.787x |
| 2048 | 14928 | bwd | 35.07 | 42.29 | 0.829x |
| 2048 | 14928 | step | 54.43 | 63.17 | 0.862x |
| 2048 | 15288 | bwd | 35.39 | 42.24 | 0.838x |
| 2048 | 15288 | step | 55.46 | 64.10 | 0.865x |
| 2048 | 15566 | bwd | 35.97 | 43.04 | 0.836x |
| 2048 | 15566 | step | 56.32 | 65.17 | 0.864x |
| 2048 | 15590 | bwd | 36.48 | 43.10 | 0.846x |
| 2048 | 15590 | step | 56.70 | 65.28 | 0.869x |
| 2048 | 16114 | bwd | 36.96 | 44.34 | 0.834x |
| 2048 | 16114 | step | 58.21 | 66.66 | 0.873x |
| 2048 | 16132 | bwd | 37.22 | 44.62 | 0.834x |
| 2048 | 16132 | step | 58.02 | 66.88 | 0.867x |
| 2048 | 16164 | bwd | 37.50 | 43.36 | 0.865x |
| 2048 | 16164 | step | 58.69 | 66.37 | 0.884x |
| 2048 | 16263 | bwd | 37.57 | 43.26 | 0.868x |
| 2048 | 16263 | step | 58.72 | 65.89 | 0.891x |
| 2048 | 32768 | bwd | 68.16 | 78.06 | 0.873x |
| 2048 | 32768 | step | 108.99 | 124.13 | 0.878x |
| 2048 | 65536 | bwd | 127.57 | 140.99 | 0.905x |
| 2048 | 65536 | step | 206.37 | 221.25 | 0.933x |
| 4096 | 256 | bwd | 6.66 | 8.70 | 0.765x |
| 4096 | 256 | step | 9.02 | 10.85 | 0.832x |
| 4096 | 1024 | bwd | 9.95 | 15.20 | 0.655x |
| 4096 | 1024 | step | 14.05 | 18.88 | 0.744x |
| 4096 | 4096 | bwd | 21.92 | 31.20 | 0.703x |
| 4096 | 4096 | step | 34.30 | 43.26 | 0.793x |
| 4096 | 14928 | bwd | 63.68 | 78.59 | 0.810x |
| 4096 | 14928 | step | 101.06 | 120.00 | 0.842x |
| 4096 | 15288 | bwd | 65.06 | 80.00 | 0.813x |
| 4096 | 15288 | step | 103.14 | 121.54 | 0.849x |
| 4096 | 15566 | bwd | 67.68 | 81.79 | 0.827x |
| 4096 | 15566 | step | 105.34 | 123.86 | 0.851x |
| 4096 | 15590 | bwd | 67.46 | 82.16 | 0.821x |
| 4096 | 15590 | step | 105.15 | 124.38 | 0.845x |
| 4096 | 16114 | bwd | 68.61 | 83.68 | 0.820x |
| 4096 | 16114 | step | 108.61 | 128.16 | 0.847x |
| 4096 | 16132 | bwd | 67.90 | 84.16 | 0.807x |
| 4096 | 16132 | step | 108.06 | 128.26 | 0.843x |
| 4096 | 16164 | bwd | 68.32 | 82.78 | 0.825x |
| 4096 | 16164 | step | 108.80 | 124.13 | 0.877x |
| 4096 | 16263 | bwd | 68.06 | 84.43 | 0.806x |
| 4096 | 16263 | step | 108.90 | 128.74 | 0.846x |
| 4096 | 32768 | bwd | 130.50 | 153.63 | 0.849x |
| 4096 | 32768 | step | 208.90 | 244.45 | 0.855x |
| 4096 | 65536 | bwd | 249.18 | 286.62 | 0.869x |
| 4096 | 65536 | step | 403.84 | 441.44 | 0.915x |
| 6144 | 256 | bwd | 7.97 | 9.73 | 0.819x |
| 6144 | 256 | step | 11.14 | 12.58 | 0.885x |
| 6144 | 1024 | bwd | 12.45 | 17.76 | 0.701x |
| 6144 | 1024 | step | 18.62 | 23.52 | 0.792x |
| 6144 | 4096 | bwd | 30.62 | 34.56 | 0.886x |
| 6144 | 4096 | step | 44.80 | 52.19 | 0.858x |
| 6144 | 14928 | bwd | 90.91 | 105.54 | 0.861x |
| 6144 | 14928 | step | 146.27 | 161.31 | 0.907x |
| 6144 | 15288 | bwd | 95.10 | 107.74 | 0.883x |
| 6144 | 15288 | step | 151.97 | 165.02 | 0.921x |
| 6144 | 15566 | bwd | 94.02 | 109.02 | 0.862x |
| 6144 | 15566 | step | 151.74 | 167.26 | 0.907x |
| 6144 | 15590 | bwd | 94.91 | 109.31 | 0.868x |
| 6144 | 15590 | step | 152.38 | 167.46 | 0.910x |
| 6144 | 16114 | bwd | 97.28 | 111.39 | 0.873x |
| 6144 | 16114 | step | 157.12 | 171.42 | 0.917x |
| 6144 | 16132 | bwd | 96.64 | 111.52 | 0.867x |
| 6144 | 16132 | step | 156.00 | 171.58 | 0.909x |
| 6144 | 16164 | bwd | 97.89 | 111.71 | 0.876x |
| 6144 | 16164 | step | 157.47 | 171.78 | 0.917x |
| 6144 | 16263 | bwd | 98.18 | 111.90 | 0.877x |
| 6144 | 16263 | step | 158.18 | 172.29 | 0.918x |
| 6144 | 32768 | bwd | 197.18 | 205.86 | 0.958x |
| 6144 | 32768 | step | 315.84 | 324.29 | 0.974x |
| 6144 | 65536 | bwd | 385.44 | 396.30 | 0.973x |
| 6144 | 65536 | step | 627.01 | 633.86 | 0.989x |

The same table for sm_107a, on an R200 board, will follow in a later
edit of this description once it is measured.

Cake ships this kernel in the four variants above (plain and
residual-fused, forward and backward, BF16 with FP32 `rstd` / `dweight`)
for sm_100a, sm_103a and sm_107a; there are no other data types or
layouts.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of RMSNorm training backward execution across
supported routes and row counts.
* Workspace sizing now accounts for requested rows, and invalid chunk
sizes are rejected.
* Added coverage for deterministic results, workspace layout, chunk
scheduling, and performance stability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d51e166](https://github.com/flashinfer-ai/flashinfer/commit/d51e1660b22c34202555cee36701f6d33edc893b)

- **作者**: 0z5a
- **时间**: 2026-10-23T22:01:18Z
- **提交信息**: test: cover the PDL ordering contract of RMSNorm and fused add RMSNorm (#6799)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds PDL ordering coverage for `flashinfer.norm.rmsnorm` and
`flashinfer.norm.fused_add_rmsnorm` to the existing
`tests/utils/test_norm.py`.

With `enable_pdl=True` these kernels may start while the previous kernel
is still running. They must not read what that kernel is still writing
(RAW), and must not write what it is still reading (WAR), before
`griddepcontrol.wait`. Both the CuTe kernels and the CUDA kernels in
`include/flashinfer/norm.cuh` wait at entry today. The tests pin that
ordering, so a later prologue change that moves a load or a store ahead
of the wait fails in CI rather than as an intermittent race downstream.

The tests:

- **Helper extension** (`load_inline`, built against
`c10/cuda/CUDAStream.h` only, so a toolkit with just nvcc and cudart is
enough). Its producer kernel calls `griddepcontrol.launch_dependents` on
entry, spins about 4M cycles, and only then copies. Its probe kernel
reads a flag before its own wait.
- `test_pdl_race_probe_sees_overlap`, in eager and CUDA-graph modes: a
calibration check. The race tests can only fail where a PDL dependent
actually starts while the producer spins. Where it never does
(`CUDA_LAUNCH_BLOCKING=1`, or anything else that serializes launches),
the probe and every RAW/WAR case skip with that reason instead of
passing vacuously.
- `test_norm_pdl_waits_before_reading` (RAW): the producer writes the
activations late (`x`, and `residual` for the fused op), and the
destinations hold NaN until then. Results must be bitwise equal to the
same call on synchronized inputs. Weights are deliberately not part of
the contract: they are static parameters, and prefetching them before
`griddepcontrol.wait` is a legitimate optimisation.
- `test_norm_pdl_waits_before_writing` (WAR): the producer snapshots
`out` late (or `input`/`residual` for the in-place fused op). The
snapshot must still hold the pre-norm bytes.
- `test_norm_pdl_matches_plain_launch`: PDL and plain launches give
bitwise-identical results.
- An `enable_pdl` axis on the existing `test_rmsnorm_output_contract`.

The race cases cover 8 shapes, FP16 and BF16, and eager and graph modes.
The shapes reach the clustered and single-CTA CuTe builds, the strided
(padded-row) build, the 3D QK kernel, and three fused hidden sizes.
Below SM90, `enable_pdl=True` silently becomes a plain launch, so every
new PDL case skips there. The original 80 output-contract cases are
unchanged.

This PR is test-only. No production kernel, dispatch path, dependency or
tolerance changes, and no existing defect is claimed.

## 🔍 Related Issues

Related to #3605. This is the second Norm slice after #4994, scoped in
[this
comment](https://github.com/flashinfer-ai/flashinfer/issues/3605#issuecomment-6277100073).
Quantized and gated norm variants, layernorm and RoPE remain outside it.

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

`pre-commit run --all-files` passed: mypy, Ruff, clang-format and the
experimental-scope self-test.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Selection: `-k "output_contract or pdl_race or pdl_waits or
pdl_matches"`. Every run executed on one GH200 (SM 9.0, 132 SMs) through
the dispatch path named in the table. The selected path
(`_use_cuda_norm`) was recorded before each run.

| Tree | Dispatch | Result |
|---|---|---|
| main + this PR | CuTe (default) | **242 passed** |
| main + this PR | CUDA (`FLASHINFER_USE_CUDA_NORM=1`) | **242 passed**
|
| Negative control: `griddepcontrol.wait` removed from the 2D RMSNorm
and FusedAddRMSNorm kernels | CuTe | 56 failed, 10 passed |
| Same negative control | CUDA | 56 failed, 10 passed |
| main + this PR, `CUDA_LAUNCH_BLOCKING=1`, race selection only | CuTe |
66 skipped ("CUDA_LAUNCH_BLOCKING serializes launches; PDL cannot
overlap") |

There are 242 cases per run: 160 output-contract cases (the original 80
with `enable_pdl` False and True) plus 82 race cases. The negative
controls and the launch-blocking run use the race selection `-k
"pdl_race or pdl_waits"` (66 cases).

In each negative control:

- Every RAW and WAR case for the 7 mutated 2D/fused shapes failed.
- The 10 passing cases are the 3D QK cases, whose kernel kept its wait
(they act as an in-run positive control), and the 2 probe cases.
- The first failure in each case was a complete miss. For example,
`rmsnorm-264x128 bf16 eager`: 33792 of 33792 output elements differ
bitwise, both for RAW and for "out overwritten early".

```sh
FLASHINFER_USE_CUDA_NORM=0 python -m pytest tests/utils/test_norm.py -k "output_contract or pdl_race or pdl_waits or pdl_matches" -q
FLASHINFER_USE_CUDA_NORM=1 python -m pytest tests/utils/test_norm.py -k "output_contract or pdl_race or pdl_waits or pdl_matches" -q
```

- **Base:** `3e5a82608543be804a753f95c785c06a7f8414d9` with this PR's
two commits applied. The tested `tests/utils/test_norm.py` differs from
head `f76baf0e` only in the wording of one comment line. FlashInfer was
imported from that source tree, with JIT sources linked from the same
tree.
- **Helper headers:** `nvcc -M` with torch's include paths shows that
the earlier `ATen/cuda/CUDAContext.h` version pulled in `cublas_v2.h`,
`cublasLt.h`, `cublas_api.h`, `cusparse.h`, `cusolverDn.h` and
`cusolver_common.h`; the `c10/cuda/CUDAStream.h` version includes none
of them.
- **Environment:** Torch 2.14.0+cu130, nvcc 13.2, CUTLASS DSL 4.8.0, TVM
FFI 0.1.11, driver 595.58.

@YangXu1990uiuc also ran the selection with the header fix on A100 (80
passed, 194 skipped), H100 NVL and B200 (274 passed each, before the
`writes_weight` axis was dropped); see the review.

**Not run by me:** SM100 or SM120, a pre-SM90 GPU, compute-sanitizer,
and the full library suite. That is why the all-tests box is unchecked.

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

## Reviewer Notes

Resolved in review:

1. **Weights** are excluded from the contract (the `writes_weight` axis
is gone); a comment above `_PDL_RACE_CASES` explains why.
2. **CI cost:** `load_inline` stays. On the GH200 the one-time helper
build took 76–84 s inside the first probe case; the other race cases
took about 11 s (CuTe, including CuTe compilation of the new shapes) and
about 2 s (CUDA). The repeat count can be raised locally with
`FLASHINFER_NORM_PDL_REPEATS`.
3. **No-overlap setups** skip instead of passing vacuously. A runner
that silently stopped overlapping would therefore show skipped race
tests rather than a failing probe.

The test implementation is AI-assisted. The results above are only what
was actually executed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Expanded RMSNorm coverage to check parallel execution ordering, eager
and CUDA-graph behavior, and bitwise agreement with synchronized
references across supported shapes and data types.
  * Skipped PDL test cases on devices that do not support them.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: 0z5a <0z5a@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6103f5e](https://github.com/flashinfer-ai/flashinfer/commit/6103f5ea7c8904c8bcd11fab9d00397801fe3c30)

- **作者**: eigen
- **时间**: 2026-10-23T21:57:37Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): tailpipe program for the hidden-4096 BF16 route at small split counts (#7121)

`flashinfer.mega_mhc` (`prepare_mega_mhc`, programs under
`flashinfer/experimental/deepgemm_mega_mhc`) contains programs for the
fused manifold-constrained hyper-connection (mHC) inference step. Before
this PR, it ships 17 programs:

- **Existing variants:** 14 hidden-5120 FP8-E4M3-output variants
(shifted / unshifted, shared-scale, `col` / `extra` scale layouts, split
counts 16 / 20 / 27 / 40) on `sm_100a` / `sm_103a`. On `sm_107a` it
ships the hidden-4096 BF16-output program (`sf_layout="bf16"`) and the
hidden-4096 FP8 group-128 (`sf_layout="fp8_group128"`) and NVFP4
(`sf_layout="nvfp4"`) output variants.
- **This PR:** a second hidden-4096 BF16-output program on `sm_107a`. It
is the "tailpipe" build of the same kernel, where the tail's round-1
loads overlap the fold. The loader uses it when the token count gives at
most 22 splits on the device, which is T >= 385 tokens on a 208-SM GPU.
For the 32- and 64-split launches at small T, the loader keeps the
shipped BF16 program.

The dispatched program takes the same plan, arguments and outputs as the
shipped program (`new_residual` BF16, `y_bf16` BF16, `new_post_mix` FP32
and `new_comb_res_mix` FP32).

The baseline is the shipped hidden-4096 BF16 program, which is the
previous Cake version of this route. Speedup is the baseline's time
divided by the time of the program the loader picks at each token count.
At T <= 256 (64 or 32 splits), both sides run the same BF16 program, so
those rows measure noise and stay within ±0.4 %. At T >= 512 (22, 13 or
16 splits), the loader runs the tailpipe program, and the gain comes
from that program. The speedup there ranges from 1.004× (T = 1024,
inside the same ±0.4 % band) to 1.024× (T = 4096).

**NVIDIA R200 (`sm_107a`, 208 SMs), driver 615.71.09, CUDA 13.4 toolkit
(nvcc 13.4.92); SM clock 2386–2414 MHz during the measurement. Both
sides were measured in one process on the same GPU as CUPTI kernel time,
with cold L2 and three interleaved ABBA groups of 64 iterations per arm;
the median is reported.**

**Hidden-4096 BF16 output, dispatched program vs the shipped BF16
program:**

| T (tokens) | Program dispatched | Splits | Shipped BF16 program, µs
(A) | This PR (dispatched program), µs (B) | Speedup (A / B) |
|---:|:--|---:|---:|---:|---:|
| 1 | BF16 | 64 | 8.816 | 8.824 | 0.999× |
| 4 | BF16 | 64 | 9.024 | 9.032 | 0.999× |
| 8 | BF16 | 64 | 9.024 | 9.040 | 0.998× |
| 16 | BF16 | 64 | 9.088 | 9.088 | 1.000× |
| 32 | BF16 | 64 | 9.441 | 9.464 | 0.998× |
| 64 | BF16 | 64 | 9.776 | 9.792 | 0.998× |
| 128 | BF16 | 64 | 10.336 | 10.296 | 1.004× |
| 256 | BF16 | 32 | 11.888 | 11.904 | 0.999× |
| 512 | tailpipe | 22 | 14.016 | 13.888 | 1.009× |
| 1024 | tailpipe | 13 | 18.176 | 18.104 | 1.004× |
| 2048 | tailpipe | 13 | 28.408 | 27.944 | 1.017× |
| 4096 | tailpipe | 16 | 55.512 | 54.208 | 1.024× |
| 8192 | tailpipe | 16 | 112.656 | 111.103 | 1.014× |

Cake's other variants of this kernel are the 14 hidden-5120 FP8-output
programs on `sm_100a` / `sm_103a` and the hidden-4096 FP8 group-128 and
NVFP4 output programs on `sm_107a`; the new program ships on `sm_107a`
only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Hidden-4096 BF16 workloads now automatically select a program based on
split count: tailpipe at 22 splits or fewer, and BF16 at higher split
counts. Both produce bitwise-identical output.
* **Documentation**
* Clarified how BF16 inputs are prepared and how updating `fn` refreshes
its split data.
* Added a warning that caller-owned epoch storage cannot be reused
across plans with different launch grids.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [aec44bd](https://github.com/flashinfer-ai/flashinfer/commit/aec44bda63e69b657b7fee4935a3d5b2ffe08462)

- **作者**: Chunan Zeng
- **时间**: 2026-10-23T21:29:58Z
- **提交信息**: fix(autotuner): rank BF16 GEMM tactics on a cold launch chain (#6360)

## 📌 Description

`mm_bf16(backend="cute-dsl")` autotuning ranked low-M tactics by
**isolated single-launch latency** rather than the cold-L2 chained cost
it was configured for, and picked measurably slower tactics than ones in
its own candidate set. `backend="auto"`, which has included the cute-dsl
runners since #6392, had the same problem and also ranked them against
cuDNN, TGV and TinyGEMM on isolated launches.

**Root cause.** #4908 added `TuningConfig.use_cold_l2_graph_replay` for
the BF16 cute-dsl config: rank tactics on a graph of launches, each with
its own input copy, timed after an L2 flush. #4361 then routed every
`use_cold_l2_cache=True` config to `cold_l2_profile`, which times one
graph launch per flushed sample, so the flag stopped having any effect.
A single isolated launch carries a ~6.3 µs floor on B300 (a trivial
`add_` measures 6.38 µs) plus a first-launch cost that differs by kernel
family (cluster split-K > warp split-K > direct). The real kernels take
2.8–6.4 µs, so candidates tied at ~10.24 µs and the pick came down to
noise. Neither the event timer (32 ns resolution) nor PDL (same with
`pdl=False`) causes it.

**Changes**
- `TuningConfig.cold_chain_launches` (with `uses_cold_chain`):
`cold_l2_profile` captures that many back-to-back launches in one graph,
each on its own profile-arena lane, and reports the median flushed
sample divided by the launch count. Every tactic of a cold-chain config
is measured this way. Cost is bounded by the sample count: the existing
untimed warm replay of the chain graph is timed, and chained samples are
capped at about 10 ms of chain time per tactic (at least 1, at most
`repeat`). Configs without a profile arena (e.g. the MXFP8 cute-dsl
config) are unchanged.
- `ValueProfileArena` accepts any non-overlapping layout: slots are
sized by the tensor's memory span and lanes keep its strides, so a
transposed (`W.T`) or padded weight is staged as-is. An operand whose
touched bytes exceed 2×L2 is chained over the caller's tensors without a
copy; a small gapped tensor whose storage span exceeds 2×L2 (copying it
into distinct lanes would be too large) is timed with single cold
launches.
- `_BF16_GEMM_SM100_TUNING_CONFIG` itself gets `cold_chain_launches=8`
and the weight in the profile arena, so every SM100 `mm_bf16` backend
(`auto`, cute-dsl, cuDNN, CUTLASS, TGV, TinyGEMM, cuBLASLt) ranks on the
cold chain with one policy per cache key.
- `TuningConfig.l2_cache_policy` (`hot` / `cold` / `cold-chain:<n>`) is
recorded by `_profiling_policy`, so persisted picks from isolated timing
or a different chain length are re-ranked.
- Cache replacement after re-tuning (an earlier runner's stale winner
must not shadow the new one once the policy changes) is handled by
#6894, now merged; this PR is rebased on it.
- `_apply_tuning_overrides` copies the config with
`dataclasses.replace`; it rebuilt `TuningConfig` field by field and
would drop new fields.
- cuBLASLt and CUTLASS BF16 requirements now reject a non-column-major B
(both kernels require contiguous `A` and `B.T`). Before,
`backend="auto"` offered them for a padded weight and autotuning crashed
in runner preparation (pre-existing; reproduced at `e2df159`).
- `pure_profile` keeps its untimed first graph replay for
`use_cold_l2_graph_replay`; the dead eviction buffer is removed.

## 📊 Performance

**Current revision (`96f9b994`): chain length and tuning cost.** B300
SXM6 AC (sm_103), CUDA 13.0, PyTorch 2.13.0, nvidia-cutlass-dsl 4.6.2,
`pdl=True`, `backend="auto"`. Harness: ≥2 GiB of distinct weights
rotated inside one CUDA graph, median per-GEMM µs over 15 replays; every
tactic the tuner profiles is timed on it, and "×best" is the tuned pick
/ fastest candidate. Each row re-tunes `auto` 3–8 times per chain length
L (L=1 = single-launch samples, as on `main`); values are the worst
trial.

| (M, N, K) | best µs | L=1 (`main`) | L=4 | L=5 | L=6 | L=7 | **L=8** |
L=16 | L=32 |
|---|---|---|---|---|---|---|---|---|---|
| (1, 512, 8192) | 2.76 | 1.040 | 1.040 | 1.038 | 1.061 | 1.036 |
**1.013** | 1.012 | 1.013 |
| (8, 512, 8192) | 3.60 | 1.311 | 1.006 | | | | **1.006** | 1.006 |
1.006 |
| (16, 512, 8192) | 3.64 | 1.015 | 1.015 | | | | **1.015** | 1.015 |
1.015 |
| (16, 256, 8192) | 3.59 | 1.225 | 1.095 | 1.005 | 1.002 | 1.005 |
**1.002** | 1.005 | 1.005 |
| (4, 3584, 2560) | 4.16 | 1.052 | 1.025 | 1.002 | 1.049 | 1.002 |
**1.003** | 1.003 | 1.000 |
| (2, 2560, 1536) | 2.62 | 1.124 | 1.110 | 1.033 | 1.014 | 1.014 |
**1.016** | 1.016 | 1.012 |
| (32, 3584, 2560) | 4.31 | 1.196 | 1.000 | | | | **1.000** | 1.000 |
1.000 |
| (256, 512, 8192) | 6.91 | 1.126 | 1.000 | | | | **1.000** | 1.000 |
1.000 |
| (512, 512, 8192) | 7.58 | 1.200 | | | | | **1.000** | | |
| (512, 256, 8192) | 6.68 | 1.132 | | | | | **1.001** | | |
| (1024, 256, 8192) | 7.69 | 1.115 | | | | | **1.000** | | |
| (1024, 1024, 2560) | 5.68 | 1.201 | | | | | **1.001** | | |
| (256, 3584, 2560) | 6.16 | 1.048 | | | | | **1.003** | | |
| (24, 19456, 2560) | 17.64 | 1.006 | | | | | **1.000** | | 1.000 |
| (512, 3584, 2560), (1024 / 2048, 512, 8192), (128–1024, 19456, 2560) |
8.2–62 | ≤ 1.004 | | | | | ≤ 1.004 | | |

L=8 is the shortest chain within 1.6% of the best candidate on every
cell; L ≤ 7 misses by up to 6%, and 8 ranks as well as 16 or 32.
Chaining matters for kernels below ~8 µs regardless of M (e.g. M=1024
with a small weight), so it is applied to every bucket rather than cut
off by M.

Warm `auto` tuning time (s), same shapes on both sides:

| | `main` (`a9dae250`) | L=32 | **L=8 (this PR)** |
|---|---|---|---|
| (4096, 19456, 2560), one bucket, 54 tactics | 1.36 | 6.33 | **2.09** |
| all 5 buckets, (19456, 2560), real M=16 | 0.80 | 5.20 | **1.92** |
| all 5 buckets, (512, 8192), real M=16 | 0.81 | 3.69 | **1.61** |

Cold (first-run) tuning is dominated by CuTe-DSL compilation: 44.7 →
49.1 s and 70.6 → 73.6 s for the two sweeps at L=32 on `main` vs this
PR, so the L=8 overhead there is a few percent.

Correction: the earlier (24, 19456, 2560) row tuned with
`tuning_buckets=[24]` but served without the override, so it measured
the cache-miss fallback on both revisions; the row above serves under
the same override.

The tables below were measured on the original revision against `main`.

B300 SXM (sm_103), CUDA 13.0, nvidia-cutlass-dsl 4.8.0, `pdl=True`.
Harness: rotate ≥2 GiB of distinct weight buffers inside one CUDA graph
(cold L2), time with CUDA events over replays, arms in ABAB order;
values are median µs per GEMM. Baseline is unpatched `main` (f63b2e7cb).

60 low-M cells (GB300 TP16 shapes at K=8192 plus K=2560/1536 shapes,
M=1–16), compared against hand-picked split-K/direct tactics:

| | main | this PR |
|---|---|---|
| tuned vs hand, geomean | 1.017× | **1.124×** |
| cells where tuned loses >5% to hand | 17 (worst 0.719×) | **0** (worst
0.983×) |
| tuned vs cuBLAS, geomean | 1.741× | 1.915× |
| tuned this PR vs tuned main, geomean | — | 1.108× |

Largest changes:

| (M, N, K) | cuBLAS | hand | main tuned | PR tuned |
|---|---|---|---|---|
| (1, 512, 8192) | 5.37 | 2.79 | 3.88 | **2.75** |
| (8, 512, 8192) | 5.84 | 3.68 | 5.02 | **3.68** |
| (16, 256, 8192) | 5.58 | 3.69 | 5.06 | **3.67** |
| (16, 512, 8192) | 6.05 | 3.75 | 5.16 | **3.75** |
| (4, 3584, 2560) | 7.72 | 4.58 | 4.93 | **3.72** |
| (2, 2560, 1536) | 5.33 | 2.77 | 3.11 | **2.43** |

Tuner-measured vs harness time per candidate, N=512 K=8192 M=16:

| tactic | harness | main tuner | PR tuner |
|---|---|---|---|
| SplitK (64,8,4,12) | 3.74 | 12.29 | 4.03 ← PR pick |
| WarpSplitK (16,8,256,13,2) | 4.43 | 10.38 | 4.48 |
| WarpSplitK (16,8,256,16,1) | 5.17 | 10.34 ← main pick | — |
| Direct (128,4,8) | 6.42 | 14.30 | 6.66 |

Tuning time per weight shape is unchanged (9–200 s, dominated by kernel
compilation).

**`backend="auto"`.** GB300 (sm_103), CUDA 13.0, nvidia-cutlass-dsl
4.8.0, same cold-L2 harness. Five shapes (N, K) ∈ {(256, 8192), (512,
8192), (3584, 2560), (2560, 1536), (19456, 2560)} × M ∈ {1, 4, 8, 16,
24, 32}, one tuning run per arm. Each cell is compared with the fastest
of five tuning arms (cute-dsl and auto, each under isolated, cold-chain
or CUPTI-span timing; geomean):

| | pdl=1 geomean | pdl=1 cells >5% slower | pdl=1 worst | pdl=0 geomean
|
|---|---|---|---|---|
| `auto`, isolated timing (before) | 1.171× | 21/30 | 1.71× | 1.110× |
| `auto`, cold chain (this PR) | **1.006×** | **1/30** | 1.06× | 1.047×
|
| `cute-dsl`, cold chain (this PR) | 1.013× | 3/30 | 1.10× | 1.012× |

Selected pdl=1 cells, µs:

| (M, N, K) | cuBLAS | `auto` before | `auto` this PR | `cute-dsl` this
PR |
|---|---|---|---|---|
| (16, 256, 8192) | 5.27 | 6.24 (warp split-K) | **3.65** (split-K) |
3.67 |
| (32, 256, 8192) | 5.41 | 5.92 (cuDNN) | **3.65** (split-K) | 3.68 |
| (8, 512, 8192) | 5.46 | 4.40 (TinyGEMM) | **3.67** (split-K) | 3.69 |
| (32, 3584, 2560) | 6.50 | 5.67 (warp split-K) | **4.58** (TGV) | 5.03
|
| (24, 19456, 2560) | **17.33** | 18.65 (warp split-K) | 17.43 (TGV) |
17.45 |

Under the cold chain, `auto` also picks other backends where they beat
cute-dsl: TGV at pdl=1, and cuBLASLt/cuDNN at pdl=0 for N=19456 K=2560 M
≥ 16 (16.8–17.0 µs vs 17.1–18.3 µs for cute-dsl). Ranking by CUPTI
kernel spans removes the launch floor but still prefers warp split-K
where split-K is 1.2–1.4× faster (pdl=1 geomean 1.072×), so it is not a
substitute for the chain.

## 🔍 Related Issues

- Regression from #4361 relative to the profiling behavior #4908
introduced.
- Found while routing sglang low-M BF16 linears through
`mm_bf16(backend="cute-dsl")` (sgl-project/sglang#43703).
- #6392 added the cute-dsl runners to `backend="auto"`; this PR makes
`auto` rank them on the cold chain.
- Supersedes #6361 (closed): instead of letting cuBLASLt compete inside
`backend="cute-dsl"` at M ≤ 32, `auto` ranks cute-dsl against the other
backends.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed files.)

## 🧪 Tests

- [x] On B300 SXM6 AC at `534622c5` (rebased on `main` after #6894 and
#6833) (PyTorch 2.13.0+cu130, cuDNN frontend 1.29.0, CuTe DSL 4.6.2):
`python -m pytest tests/gemm/test_mm_bf16.py
tests/autotuner/test_autotuner_core.py
tests/autotuner/test_autotuner_configs.py
tests/autotuner/test_autotune_cache_v2.py -q` — **332 passed, 1
skipped**.
- [x] CPU-only run of autotuner core / cache_v2 / configs (torch CPU) at
`534622c5`: the same 2 failures as `main` (GPU-only), plus 4 new passes.
- [x] New / updated tests:
- `test_cold_chain_times_arena_lanes_per_launch[dense|gapped]`:
transposed and padded arena inputs keep strides and contents; the graph
captures one launch per scheduled batch across distinct lanes; latency
is divided per launch.
- `test_cold_chain_caps_samples_by_chain_time`: 10 / 2 / 1 timed samples
for short / 4 ms / 50 ms chains.
- `test_value_profile_arena_layout_helpers`,
`test_cold_chain_reuses_inputs_for_payload_above_working_set`,
`test_cold_chain_profiling_policy_labels`,
`test_tuning_overrides_keep_cold_chain`.
`test_cold_chain_reuses_inputs_for_payload_above_working_set` also
checks that a gapped view whose span exceeds 2×L2 while its elements do
not is timed with single launches (verified end-to-end on B300 with the
review's `(512, 8192)` stride-`(1, 16384)` cuDNN case).
- `test_mm_bf16_autotune_weight_layouts[auto|cudnn × dense|padded]`:
autotuning stages dense and padded weights in the cold-chain arena and
matches PyTorch. The padded `auto` case crashed before the
cuBLASLt/CUTLASS requirement fix.
- [x] Original revision, GB300 (sm_103), PyTorch 2.14.1+cu130, CuTe DSL
4.8.0: `python -m pytest tests/gemm/test_mm_bf16.py
tests/autotuner/test_autotuner_core.py -q` — 173 passed, 4 skipped.
- [x] `pre-commit run` on all changed files passed, including mypy and
Ruff.

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

- The cold chain now applies to every SM100 `mm_bf16` backend, which
changes the persisted cache identity (`l2_cache_policy` becomes
`cold-chain:8`), so previously tuned BF16 entries are re-tuned.
- Tuning cost: one untimed 8-launch warm replay plus up to 10 timed
chained samples per tactic (timed samples capped at about 10 ms of chain
time). Warm `auto` tuning is about 1.5–2.4× `main` (table above); cold
tuning is compile-dominated. Arena memory is about 4×L2; weights above
2×L2 are chained in place without a copy.
- Not run on SM100/B200; current-revision numbers are B300 only.

AI-assisted (Claude Code and Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved cold-cache profiling for CUDA Graph workloads with
configurable multi-launch chains and per-launch latency reporting.
  * Added optimized profiling for dense BF16 GEMM weights.

* **Bug Fixes**
* Improved support for non-contiguous tensor inputs while preserving
their layouts.
* Improved BF16 GEMM support for padded weights, with autotuning enabled
or disabled.
* Fixed stale tuning results being retained after retuning selects a
different runner.
* Improved profiling behavior for oversized arena payloads and
differentiated hot, cold, and cold-chain measurements.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [58232f5](https://github.com/flashinfer-ai/flashinfer/commit/58232f576ad772c7c7f10315073c306f9cf0a292)

- **作者**: eigen
- **时间**: 2026-10-23T21:25:31Z
- **提交信息**: perf(cake_gdp): two-head T = 1 decode program for the many-wave rows and a reduce-scatter split-V row reduction on SM100 / SM103 (#7128)

The Cake Gated DeltaProduct decode kernel
(`flashinfer.cake_gdp.cake_gated_delta_product_mtp`) has one variant:
BF16 q / k / v / output with an FP32 recurrent state in a slot-indexed
state pool, float32 `A_log` and `dt_bias`, optional per-token state
scatter, 1 <= T <= 16 tokens per sequence, K = 128, V = 64 and 1 <= n <=
4 Householder sub-steps. This PR delivers that same variant with two T =
1 changes on sm_100a / sm_103a. The first is a new two-heads-per-CTA T =
1 program for the many-wave rows (B x HV at or above 32 x the SM count).
The second is a reduce-scatter / all-gather row reduction in the T = 1
split-V kernel. The baseline is the previous Cake version of this
kernel, the Cake GDP decode package of FlashInfer PR #7086. Both
packages ran in the same process on the same GPU, interleaved A B B A
over 3 groups x 32 samples per call, with cold L2 and kernel time
measured; speedup = previous / this PR, and across the 48 shapes (HV in
{80, 20, 10, 24} x B in {1, 16, 64, 256} x T in {1, 4, 8}, n = 3) it is
0.99-1.13 on GB300 and 0.98-1.18 on B200. The changed kernels run on the
two-heads-per-CTA rows (HV 80 / B 64, HV 80 / B 256, HV 20 / B 256 and
HV 24 / B 256 at T = 1) and the T = 1 split-V rows (every B = 1 row and
HV 10 / B 16, at T = 1 only); every other row runs unchanged kernels.

**NVIDIA GB300 (sm_103a), CUDA 13.4.92 -- 48 rows, speedup 0.99-1.13**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.3 | 4.1 | 1.04 |
| 80 | 1 | 4 | 6.0 | 6.0 | 1.00 |
| 80 | 1 | 8 | 8.1 | 8.1 | 1.01 |
| 80 | 16 | 1 | 20.1 | 20.3 | 0.99 |
| 80 | 16 | 4 | 24.8 | 24.7 | 1.00 |
| 80 | 16 | 8 | 40.2 | 40.1 | 1.00 |
| 80 | 64 | 1 | 62.0 | 57.2 | 1.08 |
| 80 | 64 | 4 | 76.2 | 76.2 | 1.00 |
| 80 | 64 | 8 | 131.6 | 131.6 | 1.00 |
| 80 | 256 | 1 | 228.0 | 201.7 | 1.13 |
| 80 | 256 | 4 | 282.2 | 282.3 | 1.00 |
| 80 | 256 | 8 | 500.3 | 500.5 | 1.00 |
| 20 | 1 | 1 | 3.4 | 3.3 | 1.04 |
| 20 | 1 | 4 | 5.5 | 5.5 | 0.99 |
| 20 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 1 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 4 | 10.9 | 11.0 | 0.99 |
| 20 | 16 | 8 | 16.6 | 16.6 | 1.00 |
| 20 | 64 | 1 | 20.3 | 19.8 | 1.03 |
| 20 | 64 | 4 | 24.6 | 24.5 | 1.01 |
| 20 | 64 | 8 | 40.1 | 40.1 | 1.00 |
| 20 | 256 | 1 | 60.1 | 57.2 | 1.05 |
| 20 | 256 | 4 | 76.2 | 76.3 | 1.00 |
| 20 | 256 | 8 | 131.7 | 131.6 | 1.00 |
| 10 | 1 | 1 | 3.3 | 3.2 | 1.03 |
| 10 | 1 | 4 | 5.4 | 5.4 | 1.00 |
| 10 | 1 | 8 | 7.5 | 7.5 | 1.00 |
| 10 | 16 | 1 | 5.5 | 5.2 | 1.07 |
| 10 | 16 | 4 | 8.3 | 8.2 | 1.01 |
| 10 | 16 | 8 | 12.0 | 12.0 | 1.00 |
| 10 | 64 | 1 | 11.1 | 11.1 | 1.00 |
| 10 | 64 | 4 | 16.0 | 16.0 | 1.00 |
| 10 | 64 | 8 | 25.0 | 25.2 | 0.99 |
| 10 | 256 | 1 | 34.1 | 34.0 | 1.00 |
| 10 | 256 | 4 | 41.6 | 41.7 | 1.00 |
| 10 | 256 | 8 | 69.8 | 69.8 | 1.00 |
| 24 | 1 | 1 | 3.4 | 3.4 | 1.02 |
| 24 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 24 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 1 | 8.0 | 8.1 | 1.00 |
| 24 | 16 | 4 | 11.4 | 11.4 | 1.01 |
| 24 | 16 | 8 | 17.2 | 17.2 | 1.00 |
| 24 | 64 | 1 | 22.9 | 22.4 | 1.02 |
| 24 | 64 | 4 | 28.2 | 28.4 | 0.99 |
| 24 | 64 | 8 | 47.1 | 47.1 | 1.00 |
| 24 | 256 | 1 | 71.1 | 66.6 | 1.07 |
| 24 | 256 | 4 | 90.2 | 90.3 | 1.00 |
| 24 | 256 | 8 | 156.7 | 156.6 | 1.00 |

**NVIDIA B200 (sm_100a), CUDA 13.4.92 -- 48 rows, speedup 0.98-1.18**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.4 | 4.3 | 1.04 |
| 80 | 1 | 4 | 6.3 | 6.3 | 1.00 |
| 80 | 1 | 8 | 8.5 | 8.6 | 0.99 |
| 80 | 16 | 1 | 21.4 | 21.1 | 1.02 |
| 80 | 16 | 4 | 26.5 | 26.6 | 1.00 |
| 80 | 16 | 8 | 43.6 | 43.6 | 1.00 |
| 80 | 64 | 1 | 65.0 | 59.6 | 1.09 |
| 80 | 64 | 4 | 83.2 | 83.3 | 1.00 |
| 80 | 64 | 8 | 145.0 | 145.1 | 1.00 |
| 80 | 256 | 1 | 243.4 | 206.1 | 1.18 |
| 80 | 256 | 4 | 306.8 | 306.6 | 1.00 |
| 80 | 256 | 8 | 545.1 | 545.2 | 1.00 |
| 20 | 1 | 1 | 3.5 | 3.4 | 1.02 |
| 20 | 1 | 4 | 5.8 | 5.8 | 1.00 |
| 20 | 1 | 8 | 8.0 | 8.0 | 1.00 |
| 20 | 16 | 1 | 8.0 | 8.1 | 0.99 |
| 20 | 16 | 4 | 11.6 | 11.6 | 1.00 |
| 20 | 16 | 8 | 17.8 | 17.8 | 1.00 |
| 20 | 64 | 1 | 21.1 | 21.3 | 0.99 |
| 20 | 64 | 4 | 26.6 | 26.8 | 0.99 |
| 20 | 64 | 8 | 43.6 | 43.6 | 1.00 |
| 20 | 256 | 1 | 63.9 | 59.3 | 1.08 |
| 20 | 256 | 4 | 83.3 | 83.4 | 1.00 |
| 20 | 256 | 8 | 145.2 | 145.2 | 1.00 |
| 10 | 1 | 1 | 3.4 | 3.3 | 1.03 |
| 10 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 10 | 1 | 8 | 8.0 | 7.9 | 1.00 |
| 10 | 16 | 1 | 5.8 | 5.3 | 1.09 |
| 10 | 16 | 4 | 8.6 | 8.5 | 1.01 |
| 10 | 16 | 8 | 12.8 | 12.7 | 1.01 |
| 10 | 64 | 1 | 11.7 | 11.7 | 1.00 |
| 10 | 64 | 4 | 16.9 | 17.1 | 0.99 |
| 10 | 64 | 8 | 27.4 | 27.3 | 1.01 |
| 10 | 256 | 1 | 35.6 | 36.1 | 0.98 |
| 10 | 256 | 4 | 45.9 | 45.9 | 1.00 |
| 10 | 256 | 8 | 78.5 | 78.5 | 1.00 |
| 24 | 1 | 1 | 3.6 | 3.5 | 1.04 |
| 24 | 1 | 4 | 5.8 | 5.8 | 1.01 |
| 24 | 1 | 8 | 8.0 | 8.1 | 1.00 |
| 24 | 16 | 1 | 8.4 | 8.4 | 1.00 |
| 24 | 16 | 4 | 12.1 | 12.2 | 0.99 |
| 24 | 16 | 8 | 18.4 | 18.4 | 1.00 |
| 24 | 64 | 1 | 24.1 | 23.7 | 1.02 |
| 24 | 64 | 4 | 30.6 | 30.7 | 1.00 |
| 24 | 64 | 8 | 51.3 | 51.3 | 1.00 |
| 24 | 256 | 1 | 74.0 | 68.4 | 1.08 |
| 24 | 256 | 4 | 98.4 | 98.8 | 1.00 |
| 24 | 256 | 8 | 172.1 | 172.0 | 1.00 |

This variant is the kernel family's only data-type form; Cake ships it
on sm_90a (H100 / H200), sm_100a (B200 / GB200) and sm_103a (B300 /
GB300), and this PR changes one sm_100a / sm_103a kernel (the T = 1
split-V program) and adds one (the two-heads-per-CTA T = 1 program).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an additional decode option for one-token, three-Householder
workloads on newer GPU architectures, including cases with odd numbers
of heads.
* Updated decode routing to select supported options based on workload
size and available GPU resources.

* **Bug Fixes**
* Improved correctness of paired-row calculations in the decode kernel.

* **Compatibility**
  * Added generated library support for newer GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b27f6ca](https://github.com/flashinfer-ai/flashinfer/commit/b27f6cae7da4b63a3c355a48fb3fb0de13673cc1)

- **作者**: Yang Xu
- **时间**: 2026-10-23T20:59:49Z
- **提交信息**: perf: reuse unchanged cuDNN prefill plan descriptors (#7130)

<!-- .github/pull_request_template.md -->

## 📌 Description

Repeated cuDNN prefill `plan()` calls currently rebuild the full
descriptor key even when the existing metadata buffers and layouts are
unchanged. Reuse the immutable descriptor key after checking the scalar
graph facts and owned tensor snapshots; reuse the existing plan when the
bindings also match. New pointers still get fresh bindings, and changed
layouts still rebuild the descriptor. Keep the snapshots private to the
plan so a caller can reuse or mutate its metadata object safely.

This is a standalone main-based version of the plan optimization in
#7126. It can be reviewed and merged independently of #6231, #7050, and
#7052. It preserves main's existing descriptor and bounded-MLA contract.

H100 NVL (132 SMs), BF16 D128, Hq/Hkv=32/8, ragged NHD, causal
attention, explicit cuDNN; cuDNN 9.27.0.42, Torch 2.14.0+cu130, FE
development build `409340195`. Baseline `85e886c875` versus this patch.
Separate-process ABBA, reporting the mean of two process medians per
arm. Warm host timings exclude synchronization; GPU replay is measured
separately.

| Workload | Host plan, before → after | Host plan+run, before → after |
GPU replay, before → after |
|---|---:|---:|---:|
| B1, Q128, KV8192 |79.12 →68.12 µs|137.36 →126.12 µs|1339.72 →1341.93
µs|
| B4, Q512, KV512 |77.38 →65.83 µs|135.27 →122.01 µs|1207.21 →1207.11
µs|

Host plan improves by 13.9–14.9%, and plan+run by 8.2–9.8% in these two
component cases. Both arms select `eng9_k24=1_k27=0_k38=0_k40=3_k41=2`.
Warm enqueue remains about 39–40 µs; there is no measured GPU
improvement. Sampled independent math checks and output-poisoned graph
replay pass in all eight arms, including replay after replan. These are
wrapper component measurements, not a serving throughput or cold-start
claim.

Reproduce on each checkout in separate processes:

```bash
python benchmarks/bench_cudnn_wrapper_host.py --kind ragged --layout NHD --batch 1 --q 128 --kv 8192 --replan --output prefix.json
python benchmarks/bench_cudnn_wrapper_host.py --kind ragged --layout NHD --batch 4 --q 512 --kv 512 --replan --output full.json
```

## 🔍 Related Issues

Standalone counterpart of #7126. That PR adapts the same optimization to
the descriptor extensions in the #6231/#7052 stack; preserve this
optimization when that stack is integrated. No auto-admission or
kernel-selection change is included here.

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

Scoped hooks passed for both changed files (`pre-commit run --files
...`); the repository-wide hook run was not performed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests in the focused validation below pass.

H100: **184 passed, 38 skipped** across:

```bash
pytest -q -o addopts= tests/attention/test_cudnn_prepared_contract.py tests/attention/test_cudnn_wrapper_regressions.py tests/attention/test_cudnn_prepared_graph.py tests/attention/test_cudnn_ragged_shape_override.py tests/attention/test_cudnn_native_log2.py
```

Adds a regression for changing a tensor layout through a retained
metadata object. Existing coverage checks storage rebinding, dynamic
lengths, O/LSE, calibration scales, fallback, and captured execution
lifetimes. A separate warmed-plan probe checks that pending GPU work
remains pending after planning, with correct metadata under both stable
and rotating table pointers.

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

Please focus on descriptor invalidation and snapshot ownership. The two
public wrapper callers construct this plan with scales unset; their
per-run scale handling is unchanged. No timing or heuristic winner is
asserted in tests. The graph eligibility and mixed-length auto-selection
performance work remain in separate PRs. The retained-metadata
regression guards this optimization: main and the complete patch pass;
descriptor reuse without the owned metadata copy fails.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention prefill plan reuse when tensor bindings change but
their layouts remain compatible.
* Plans now update correctly when a tensor’s stride changes, helping
ensure they match the current input layout.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c56cd4f](https://github.com/flashinfer-ai/flashinfer/commit/c56cd4fb72220a2c52e168e2c86525ec37b5ee1e)

- **作者**: eigen
- **时间**: 2026-10-23T20:49:00Z
- **提交信息**: feat(cake_dense_projection_gemm): fence the split-K collector's bulk read and refresh the generated programs (#7129)

The Cake `dense_projection_gemm` kernel takes BF16 inputs and writes
BF16 or FP32 output in the fwd, dgrad and wgrad layouts (nn / kn / kk).
It also has an FP32 BF16x3 router GEMM with a fused split. This PR
re-renders the kernel's generated programs. The six split-K slab
collectors (`_sks_sb2`) gain an async-proxy fence before their bulk read
of the partial sums. 13 BF16-output programs, 3 FP32-output programs and
the fused split program pick up the generator's current store lowering.
No program is added, and all 294 representative shapes keep the plan
they have in the previous version (the Cake version delivered in #7108),
so the expected speedup in the tables below is 0.99–1.01. The
dense_gate_up, dense_down and 5120→5120 BF16 wgrad rows are faster on
both GPUs (1.008–1.016 on GB300, 1.003–1.037 on GB200). The extremes on
either side (0.981 and 1.028 on GB300, 0.922 and 1.056 on GB200) are on
programs this PR leaves unchanged.

**NVIDIA GB200 (sm_100a), driver 580.126.20, CUDA 13.4 (nvcc 13.4.92);
node nvl72012-T11. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × [20] iterations, both sides in the same session. Latency in µs;
speedup = previous version / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
171.9 | 172.2 | 0.998 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
171.6 | 171.4 | 1.001 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 166.9
| 166.9 | 1.000 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 167.6
| 167.4 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
176.1 | 177.0 | 0.995 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
176.8 | 177.7 | 0.995 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 175.1
| 175.0 | 1.001 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 176.3
| 176.2 | 1.001 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
257.0 | 257.9 | 0.996 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
254.3 | 254.4 | 1.000 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
262.2 | 262.1 | 1.000 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
257.5 | 256.9 | 1.002 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
255.1 | 245.9 | 1.037 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
250.1 | 250.0 | 1.001 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
256.1 | 262.2 | 0.977 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
258.0 | 258.4 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
264.6 | 262.8 | 1.007 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
261.3 | 260.8 | 1.002 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 642.8 |
644.0 | 0.998 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 643.0 |
643.1 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 643.2 |
642.8 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 643.9 |
645.8 | 0.997 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 620.8 |
616.4 | 1.007 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 617.7 |
618.2 | 0.999 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 630.1 |
629.3 | 1.001 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 641.4 |
633.2 | 1.013 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 642.5 |
640.6 | 1.003 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 643.5 |
643.1 | 1.001 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 24.0 | 23.9 |
1.001 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 24.0 | 24.1 |
0.999 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 44.6 | 44.7 | 0.997
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 45.0 | 45.0 | 0.999
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 26.4 | 26.3 | 1.001
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 26.2 | 26.1 | 1.001
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.5 | 28.6 |
0.998 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.3 | 28.3 |
1.001 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.6 | 28.5 | 1.004
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.6 | 28.5 | 1.004
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 24.5 | 24.5 |
0.999 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 24.5 | 24.6 |
0.999 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 45.1 | 45.1 | 1.001
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 45.6 | 45.3 | 1.006
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.4 | 26.4 | 0.999
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 26.2 | 26.2 | 0.999
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.9 | 28.7 |
1.010 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.8 | 28.9 |
0.998 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.8 | 28.8 | 0.999
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 29.6 | 29.6 | 0.998
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 24.4 | 24.4 |
1.001 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 24.5 | 24.6 |
0.999 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 45.3 | 45.2 | 1.002
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 45.5 | 45.2 | 1.006
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 26.5 | 26.6 | 0.996
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 26.5 | 26.6 | 0.996
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.7 | 28.7 |
1.002 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.4 | 28.4 |
1.000 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.8 | 28.8 | 1.000
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.5 | 28.5 | 0.999
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 25.6 | 25.6 |
0.999 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 25.8 | 25.8 |
1.000 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 47.3 | 47.3 |
0.999 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 47.5 | 47.4 |
1.003 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 27.3 | 27.3 | 1.000
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 27.2 | 27.4 | 0.993
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.5 | 29.5 |
0.999 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.2 | 29.2 |
0.999 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.5 | 29.5 |
0.999 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.3 | 29.2 |
1.002 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 49.9 | 49.7 |
1.004 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 49.8 | 49.5 |
1.006 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 69.5 | 69.6 |
0.998 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 69.2 | 69.5 |
0.996 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 54.5 | 54.3 | 1.003
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 54.0 | 54.0 | 1.000
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 48.7 | 48.8 |
0.997 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 49.0 | 49.2 |
0.997 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 48.9 | 48.7 |
1.003 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 49.1 | 49.1 |
0.998 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 93.5 | 93.5 |
1.000 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 93.9 | 93.8 |
1.001 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 94.5 | 94.4 |
1.001 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 94.7 | 94.8 |
0.999 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 94.2 | 94.1 |
1.002 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 94.9 | 94.9 |
1.000 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 96.3 | 96.5 |
0.998 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 97.2 | 97.3 |
0.999 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 317.0 | 310.9 |
1.020 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 310.6 | 311.2 |
0.998 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 312.0 | 311.7 |
1.001 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 311.6 | 311.9 |
0.999 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 331.8 | 324.3 |
1.023 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 326.1 | 326.1 |
1.000 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 329.0 | 328.5 |
1.002 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 331.3 | 330.6 |
1.002 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 921.9 | 923.0 |
0.999 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 944.7 | 962.4 |
0.982 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 906.8 | 881.0 |
1.029 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 934.5 | 902.6 |
1.035 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 915.7 | 917.6 |
0.998 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 946.4 | 916.4 |
1.033 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 954.6 | 952.6 |
1.002 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 948.8 | 959.4 |
0.989 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 28.7 | 28.7 |
0.999 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 28.9 | 28.8 |
1.003 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 53.6 | 53.8 | 0.995
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 54.1 | 54.2 | 0.999
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 31.4 | 31.3 | 1.002
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 32.2 | 32.2 | 1.000
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 33.1 | 32.8 |
1.010 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 33.0 | 33.2 |
0.996 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 32.7 | 32.7 | 1.000
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 33.0 | 33.1 | 0.997
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 29.1 | 29.1 |
0.999 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 29.3 | 29.3 |
1.002 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 54.3 | 54.3 | 0.999
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 54.7 | 54.9 | 0.997
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 31.3 | 31.4 | 0.996
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 32.1 | 32.1 | 1.000
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 33.6 | 33.6 |
1.001 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 33.8 | 33.9 |
0.997 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 33.4 | 33.4 | 1.000
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 33.8 | 33.8 | 1.000
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 29.2 | 29.1 |
1.004 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 29.3 | 29.3 |
1.001 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 54.7 | 54.6 | 1.001
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 54.8 | 54.8 | 1.000
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 32.0 | 32.0 | 1.000
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 32.4 | 32.5 | 0.997
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 33.2 | 33.3 |
0.996 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 33.7 | 33.5 |
1.007 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 33.2 | 33.3 | 0.998
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 33.6 | 33.6 | 0.999
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 30.7 | 30.7 |
0.998 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 30.7 | 30.7 |
1.001 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 56.8 | 57.0 |
0.997 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 57.3 | 57.2 |
1.002 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 33.1 | 33.1 | 1.001
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 32.7 | 32.7 | 0.999
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 33.7 | 33.7 |
1.000 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 34.3 | 34.1 |
1.006 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 33.4 | 33.5 |
0.997 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 34.0 | 34.1 |
0.996 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 64.2 | 64.4 |
0.996 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 64.1 | 64.3 |
0.998 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 86.7 | 86.5 |
1.003 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 86.1 | 86.3 |
0.997 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 67.6 | 67.4 | 1.002
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 68.2 | 68.3 | 0.999
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 66.5 | 66.8 |
0.997 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 67.2 | 67.4 |
0.997 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 68.2 | 68.8 |
0.992 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 68.7 | 68.6 |
1.002 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 114.0 | 113.8 |
1.002 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 114.0 | 114.0 |
1.000 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 116.3 | 116.4 |
0.999 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 116.6 | 116.6 |
1.000 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 120.9 | 121.1 |
0.998 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 121.4 | 121.5 |
0.999 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 122.0 | 122.3 |
0.998 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 122.8 | 123.2 |
0.997 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 482.1 | 481.1 |
1.002 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 482.5 | 482.8 |
0.999 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 481.5 | 481.3 |
1.000 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 483.3 | 483.4 |
1.000 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 489.1 | 487.6 |
1.003 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 494.5 | 492.4 |
1.004 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 490.0 | 490.2 |
1.000 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 494.4 | 494.9 |
0.999 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1627.4 | 1639.4
| 0.993 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1600.4 | 1611.1
| 0.993 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1594.4 | 1583.7 |
1.007 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1594.4 | 1599.0 |
0.997 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1597.0 | 1591.3
| 1.004 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1677.1 | 1717.8
| 0.976 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1643.9 | 1612.6
| 1.019 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1643.9 | 1629.5
| 1.009 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 34.3
| 34.3 | 1.001 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 34.3
| 34.3 | 1.000 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 61.5 |
61.3 | 1.003 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 61.4 |
61.5 | 0.998 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 36.8 |
37.0 | 0.995 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 37.0 |
37.1 | 0.998 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 37.6
| 37.7 | 0.998 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 37.4
| 37.5 | 0.998 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 37.6 |
37.7 | 0.996 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 37.4 |
37.6 | 0.997 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 35.9
| 35.9 | 1.000 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 35.9
| 35.9 | 1.000 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 65.1 |
65.1 | 1.000 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 65.0 |
64.9 | 1.001 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 38.4 |
38.4 | 0.999 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 38.3 |
38.3 | 1.001 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 38.4
| 38.4 | 1.000 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 38.4
| 38.4 | 1.002 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 38.3 |
38.3 | 1.000 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 38.4 |
38.3 | 1.002 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 84.3 |
84.5 | 0.998 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 84.1 |
84.4 | 0.996 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 110.6 |
109.6 | 1.009 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 111.2 |
110.8 | 1.004 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 92.7 | 92.9
| 0.999 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 92.8 | 92.7
| 1.002 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 81.4 |
81.1 | 1.004 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 81.8 |
81.5 | 1.003 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 82.6 | 83.2
| 0.993 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 83.3 | 83.2
| 1.002 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 254.8 |
253.9 | 1.003 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 249.6 |
249.8 | 0.999 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 262.8 |
262.5 | 1.001 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 263.3 |
262.8 | 1.002 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 249.6 |
249.0 | 1.002 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 248.7 |
249.3 | 0.997 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 258.1 |
258.4 | 0.999 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 258.2 |
258.4 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 259.0 |
259.2 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 260.3 |
260.5 | 0.999 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
250.2 | 249.9 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
250.7 | 250.1 | 1.003 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
262.9 | 262.8 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
262.7 | 262.7 | 1.000 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
248.3 | 249.0 | 0.997 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
248.7 | 248.7 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
257.5 | 258.1 | 0.998 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
259.2 | 259.3 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
260.0 | 259.3 | 1.003 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
260.3 | 260.0 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1361.1 | 1341.7 | 1.014 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1383.2 | 1359.7 | 1.017 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1351.3 | 1363.7 | 0.991 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1380.6 | 1341.0 | 1.030 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 56.1 | 57.7 |
0.973 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 46.9 | 46.9 |
0.999 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 91.0 | 90.9 |
1.000 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 90.2 | 90.2 |
1.000 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 48.7 | 48.7 | 1.000
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 49.3 | 49.4 | 1.000
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 44.7 | 44.8 |
0.997 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 44.9 | 44.8 |
1.002 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 44.7 | 44.7 |
0.999 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 44.9 | 44.9 |
1.001 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 904.3 | 905.1 |
0.999 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 908.5 | 890.9 |
1.020 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 917.9 | 917.8 |
1.000 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 924.1 | 941.4 |
0.982 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 902.1 | 905.4 |
0.996 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 908.7 | 915.1 |
0.993 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 945.4 | 910.7 |
1.038 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 924.7 | 914.3 |
1.011 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1342.3 | 1329.4 | 1.010 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1380.9 | 1332.1 | 1.037 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1343.4 | 1345.4 | 0.999 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1352.9 | 1373.0 | 0.985 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1801.0
| 1797.1 | 1.002 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1845.2
| 1835.3 | 1.005 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1860.1
| 1853.3 | 1.004 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1850.7
| 1863.4 | 0.993 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1817.2 |
1809.6 | 1.004 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1807.7 |
1837.2 | 0.984 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1755.3
| 1747.5 | 1.005 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1792.8
| 1848.9 | 0.970 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1779.2
| 1769.5 | 1.005 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1827.8
| 1798.4 | 1.016 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1596.1 | 1589.5
| 1.004 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1606.8 | 1615.5
| 0.995 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1586.1 | 1603.8 |
0.989 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1608.9 | 1608.9 |
1.000 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1591.2 | 1726.0
| 0.922 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1721.6 | 1645.8
| 1.046 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1679.2 | 1590.9
| 1.056 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1628.5 | 1610.2
| 1.011 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16172 | previous
version | 241.7 | 241.5 | 1.001 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16231 | previous
version | 238.6 | 238.6 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16172 | previous
version | 266.7 | 266.9 | 0.999 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16231 | previous
version | 276.0 | 275.9 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16172 | previous
version | 217.0 | 216.7 | 1.001 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16231 | previous
version | 217.5 | 217.3 | 1.001 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16172 | previous
version | 291.3 | 291.2 | 1.000 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16231 | previous
version | 293.2 | 293.2 | 1.000 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16172 | previous version
| 263.9 | 263.9 | 1.000 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16231 | previous version
| 266.3 | 266.6 | 0.999 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16172 | previous
version | 235.9 | 236.2 | 0.999 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16231 | previous
version | 236.5 | 236.8 | 0.999 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 187.5 |
187.2 | 1.001 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 191.9 | 191.8
| 1.000 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 189.8 |
188.2 | 1.008 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 236.4 |
236.5 | 1.000 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 225.7 | 225.2
| 1.002 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 239.4 |
239.7 | 0.999 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 272.4 |
271.8 | 1.002 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 273.5 |
273.1 | 1.001 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 260.4 | 261.0
| 0.998 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 259.4 | 259.4
| 1.000 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 248.7 |
248.7 | 1.000 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 249.3 |
248.8 | 1.002 |

**NVIDIA GB300 (sm_103a), driver 580.159.03, CUDA 13.4 (nvcc 13.4.92);
node nvl72d102-T18. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × [20] iterations, both sides in the same session. Latency in µs;
speedup = previous version / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
140.1 | 139.8 | 1.002 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
139.5 | 140.1 | 0.996 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 137.9
| 137.7 | 1.001 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 138.8
| 138.2 | 1.005 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
146.1 | 146.3 | 0.999 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
146.9 | 146.7 | 1.002 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 144.9
| 144.8 | 1.001 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 145.4
| 145.6 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
213.5 | 212.8 | 1.003 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
213.9 | 213.7 | 1.001 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
216.6 | 216.4 | 1.001 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
216.4 | 216.7 | 0.998 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
208.7 | 208.6 | 1.001 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
208.3 | 207.6 | 1.003 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
216.4 | 216.8 | 0.998 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
216.3 | 216.4 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
218.0 | 217.4 | 1.003 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
217.8 | 217.9 | 0.999 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 571.6 |
570.4 | 1.002 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 569.8 |
569.7 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 573.4 |
572.1 | 1.002 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 572.1 |
572.9 | 0.999 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 541.5 |
541.3 | 1.000 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 542.7 |
543.7 | 0.998 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 560.1 |
557.7 | 1.004 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 560.9 |
560.1 | 1.002 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 565.2 |
565.4 | 1.000 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 570.6 |
568.2 | 1.004 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 23.1 | 23.2 |
0.997 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 23.5 | 23.5 |
0.998 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 42.8 | 42.9 | 0.999
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 43.3 | 43.1 | 1.004
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 27.0 | 27.0 | 0.998
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 26.6 | 26.6 | 1.001
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.3 | 28.4 |
0.996 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.4 | 28.4 |
1.000 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.4 | 28.5 | 0.996
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.5 | 28.5 | 1.000
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 23.7 | 23.7 |
1.000 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 23.7 | 23.5 |
1.006 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 43.4 | 43.3 | 1.003
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 43.7 | 43.7 | 1.000
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.9 | 26.9 | 1.001
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 26.6 | 26.6 | 0.999
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.6 | 28.4 |
1.006 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.5 | 28.6 |
0.998 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.5 | 28.5 | 0.998
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 28.7 | 28.7 | 1.001
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 23.5 | 23.4 |
1.003 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 23.7 | 23.7 |
1.002 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 43.4 | 43.4 | 1.000
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 43.6 | 43.7 | 0.998
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 27.2 | 27.3 | 0.997
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 27.1 | 27.0 | 1.002
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.8 | 28.8 |
1.001 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.7 | 28.5 |
1.004 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.7 | 28.7 | 0.999
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.6 | 28.7 | 0.996
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 24.3 | 24.3 |
1.002 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 24.4 | 24.4 |
0.999 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 44.8 | 44.8 |
0.999 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 45.0 | 45.0 |
0.999 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 28.0 | 28.1 | 0.996
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 27.5 | 27.6 | 0.999
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.5 | 29.4 |
1.004 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.4 | 29.4 |
0.999 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.5 | 29.4 |
1.003 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.5 | 29.5 |
0.999 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 43.0 | 42.9 |
1.003 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 43.0 | 42.9 |
1.003 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 60.2 | 60.2 |
1.001 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 60.1 | 59.9 |
1.003 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 48.3 | 48.3 | 1.000
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 48.3 | 48.3 | 1.000
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 43.2 | 43.1 |
1.001 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 43.5 | 43.6 |
0.997 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 42.9 | 43.0 |
0.996 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 43.3 | 43.4 |
0.997 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 73.4 | 73.6 |
0.998 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 73.9 | 73.9 |
1.000 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 74.1 | 74.0 |
1.002 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 74.1 | 74.2 |
0.999 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 73.2 | 73.1 |
1.000 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 73.8 | 73.7 |
1.000 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 75.2 | 74.6 |
1.007 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 75.7 | 75.8 |
0.999 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 269.2 | 269.4 |
0.999 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 269.4 | 268.0 |
1.005 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 269.0 | 268.3 |
1.003 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 268.8 | 268.2 |
1.002 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 280.8 | 278.8 |
1.007 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 280.7 | 280.8 |
1.000 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 282.9 | 283.2 |
0.999 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 285.6 | 285.4 |
1.001 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 825.2 | 821.7 |
1.004 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 822.3 | 823.6 |
0.998 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 798.5 | 801.1 |
0.997 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 802.0 | 804.0 |
0.998 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 827.1 | 824.1 |
1.004 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 833.9 | 832.0 |
1.002 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 838.3 | 834.5 |
1.005 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 836.6 | 835.4 |
1.001 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 27.7 | 27.5 |
1.006 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 27.6 | 27.8 |
0.995 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 51.7 | 51.6 | 1.002
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 51.9 | 52.0 | 0.998
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 31.6 | 31.6 | 0.997
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 32.7 | 32.8 | 0.997
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 34.1 | 34.2 |
1.000 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 34.3 | 34.2 |
1.001 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 34.0 | 34.1 | 0.999
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 34.3 | 34.3 | 1.000
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 27.8 | 27.9 |
0.998 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 28.0 | 27.9 |
1.002 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 52.0 | 52.0 | 1.001
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 52.7 | 52.4 | 1.006
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 31.7 | 31.7 | 1.000
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 32.6 | 32.7 | 0.998
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 34.4 | 34.4 |
1.003 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 34.7 | 34.6 |
1.002 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 34.4 | 34.4 | 1.000
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 34.6 | 34.6 | 1.001
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 27.9 | 27.9 |
1.000 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 28.2 | 28.1 |
1.002 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 52.3 | 52.3 | 1.001
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 52.7 | 52.7 | 1.000
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 32.3 | 32.3 | 1.000
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 33.0 | 33.2 | 0.995
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 34.4 | 34.6 |
0.995 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 34.8 | 34.8 |
0.998 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 34.5 | 34.4 | 1.002
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 34.6 | 34.8 | 0.994
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 29.1 | 29.1 |
1.002 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 29.2 | 29.3 |
0.999 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 54.3 | 54.2 |
1.001 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 54.4 | 54.5 |
0.998 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 33.5 | 33.6 | 0.996
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 33.3 | 33.3 | 1.002
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 35.7 | 35.9 |
0.996 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 36.3 | 36.1 |
1.005 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 35.6 | 35.6 |
0.999 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 36.1 | 36.0 |
1.004 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 54.3 | 54.4 |
0.997 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 54.6 | 54.6 |
1.000 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 73.7 | 73.5 |
1.003 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 74.0 | 73.9 |
1.002 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 58.0 | 58.2 | 0.998
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 58.2 | 58.2 | 1.001
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 53.2 | 52.8 |
1.006 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 53.3 | 53.4 |
1.000 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 54.7 | 54.7 |
1.000 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 54.5 | 54.5 |
1.001 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 92.2 | 92.8 |
0.993 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 92.0 | 92.0 |
1.001 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 92.3 | 92.1 |
1.002 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 92.4 | 92.5 |
0.999 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 97.0 | 97.0 |
1.000 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 97.6 | 97.8 |
0.999 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 98.6 | 98.4 |
1.002 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 98.8 | 99.3 |
0.995 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 420.5 | 419.0 |
1.004 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 419.6 | 420.5 |
0.998 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 419.7 | 419.4 |
1.001 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 420.5 | 420.6 |
1.000 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 428.4 | 425.2 |
1.008 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 432.5 | 429.2 |
1.008 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 427.5 | 427.8 |
0.999 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 432.6 | 432.1 |
1.001 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1442.9 | 1464.3
| 0.985 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1458.5 | 1466.3
| 0.995 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1426.5 | 1419.9 |
1.005 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1430.5 | 1428.5 |
1.001 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1435.7 | 1432.2
| 1.002 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1445.2 | 1443.6
| 1.001 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1461.3 | 1434.7
| 1.019 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1454.7 | 1462.0
| 0.995 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 32.5
| 32.8 | 0.994 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 33.0
| 32.8 | 1.004 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 58.2 |
58.1 | 1.001 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 58.7 |
58.6 | 1.003 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 37.5 |
37.5 | 1.000 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 37.4 |
37.4 | 1.000 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 39.3
| 39.3 | 0.998 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 39.2
| 39.1 | 1.003 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 39.3 |
39.4 | 0.999 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 39.3 |
39.2 | 1.004 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 34.0
| 34.1 | 0.997 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 34.1
| 34.1 | 1.000 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 62.0 |
62.1 | 0.999 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 61.9 |
61.8 | 1.002 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 38.9 |
38.8 | 1.004 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 38.8 |
38.7 | 1.001 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 40.6
| 40.6 | 0.998 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 41.0
| 41.1 | 0.999 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 40.6 |
40.6 | 1.001 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 41.0 |
40.9 | 1.004 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 66.0 |
66.5 | 0.992 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 66.6 |
66.6 | 1.000 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 91.4 | 91.6
| 0.998 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 92.2 | 92.0
| 1.002 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 71.9 | 71.9
| 1.000 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 72.1 | 72.2
| 0.998 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 64.8 |
65.0 | 0.997 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 65.6 |
65.2 | 1.006 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 66.1 | 66.0
| 1.001 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 66.3 | 66.4
| 0.999 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 208.4 |
208.4 | 1.000 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 207.9 |
206.9 | 1.005 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 218.5 |
218.8 | 0.999 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 219.2 |
219.3 | 1.000 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 209.2 |
208.8 | 1.002 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 207.5 |
207.4 | 1.001 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 215.1 |
215.2 | 0.999 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 216.0 |
216.3 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 216.1 |
216.5 | 0.998 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 216.9 |
217.1 | 0.999 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
206.9 | 206.9 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
207.4 | 207.6 | 0.999 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
219.0 | 219.2 | 0.999 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
219.4 | 219.2 | 1.001 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
208.0 | 207.8 | 1.001 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
208.1 | 208.2 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
215.2 | 215.6 | 0.998 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
216.1 | 216.5 | 0.999 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
216.7 | 216.5 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
217.5 | 217.3 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1215.6 | 1197.6 | 1.015 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1224.3 | 1204.7 | 1.016 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1211.9 | 1203.0 | 1.007 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1220.8 | 1210.3 | 1.009 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 43.9 | 44.7 |
0.981 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 43.8 | 43.8 |
1.001 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 85.4 | 85.3 |
1.001 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 84.7 | 84.8 |
0.998 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 48.6 | 48.6 | 1.000
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 49.2 | 49.1 | 1.002
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 45.6 | 45.8 |
0.995 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 46.1 | 46.0 |
1.003 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 45.7 | 45.5 |
1.005 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 45.8 | 45.8 |
1.000 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 805.1 | 805.2 |
1.000 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 803.6 | 809.2 |
0.993 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 819.9 | 817.2 |
1.003 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 816.4 | 819.1 |
0.997 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 812.9 | 812.0 |
1.001 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 820.6 | 821.0 |
1.000 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 827.2 | 827.2 |
1.000 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 830.7 | 827.4 |
1.004 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1204.4 | 1195.0 | 1.008 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1215.9 | 1201.8 | 1.012 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1203.7 | 1205.3 | 0.999 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1213.9 | 1206.8 | 1.006 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1621.3
| 1614.5 | 1.004 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1624.3
| 1626.0 | 0.999 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1651.1
| 1650.5 | 1.000 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1651.6
| 1650.8 | 1.000 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1639.5 |
1629.1 | 1.006 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1647.9 |
1639.6 | 1.005 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1613.2
| 1605.6 | 1.005 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1636.2
| 1626.4 | 1.006 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1616.3
| 1622.4 | 0.996 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1631.7
| 1626.9 | 1.003 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1428.2 | 1440.4
| 0.992 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1432.1 | 1435.1
| 0.998 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1443.6 | 1427.1 |
1.012 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1431.4 | 1433.3 |
0.999 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1425.3 | 1420.7
| 1.003 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1471.3 | 1431.6
| 1.028 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1439.4 | 1430.0
| 1.007 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1440.1 | 1439.5
| 1.000 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16172 | previous
version | 232.2 | 232.4 | 0.999 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16231 | previous
version | 230.7 | 230.7 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16172 | previous
version | 241.3 | 241.3 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16231 | previous
version | 245.9 | 245.9 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16172 | previous
version | 218.8 | 219.1 | 0.999 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16231 | previous
version | 219.9 | 219.6 | 1.001 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16172 | previous
version | 265.4 | 264.6 | 1.003 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16231 | previous
version | 264.1 | 264.1 | 1.000 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16172 | previous version
| 252.9 | 252.9 | 1.000 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16231 | previous version
| 256.8 | 256.8 | 1.000 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16172 | previous
version | 237.2 | 236.6 | 1.003 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16231 | previous
version | 237.6 | 237.4 | 1.001 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 171.7 |
171.2 | 1.003 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 164.0 | 163.9
| 1.000 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 160.8 |
161.1 | 0.998 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 223.2 |
223.0 | 1.001 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 193.7 | 193.4
| 1.002 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 206.6 |
207.5 | 0.996 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 257.9 |
257.7 | 1.001 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 260.0 |
260.2 | 0.999 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 225.1 | 225.3
| 0.999 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 223.4 | 223.4
| 1.000 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 212.8 |
212.9 | 0.999 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 213.7 |
213.0 | 1.003 |

Every variant listed above ships in this package, which has programs for
sm_100a (GB200), sm_103a (GB300) and sm_107a: 247 build entries (80 / 80
/ 87) and 120 registry records, the same counts as in the previous
version.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added dense projection GEMM kernel variants for additional GPU
architectures.

* **Improvements**
* Updated bfloat16 result handling and memory synchronization across
dense projection GEMM kernels.
* Refreshed support for available kernel configurations across GPU
architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [21ac136](https://github.com/flashinfer-ai/flashinfer/commit/21ac136220454a309e9e0ece509ff3d7bfb3a50f)

- **作者**: eigen
- **时间**: 2026-10-23T20:37:29Z
- **提交信息**: feat(cake_deepgemm_mega_mhc): FP8 group-128 and NVFP4 output variants of the hidden-4096 fused mHC step on SM107 (#7114)

`flashinfer.mega_mhc` (`prepare_mega_mhc`, programs under
`flashinfer/experimental/deepgemm_mega_mhc`) contains programs for the
fused manifold-constrained hyper-connection (mHC) inference step. Before
this PR, it ships 15 programs:

- **Existing variants:** 14 hidden-5120 FP8-E4M3-output variants
(shifted / unshifted, shared-scale, `col` / `extra` scale layouts, split
counts 16 / 20 / 27 / 40) on `sm_100a` / `sm_103a`, and one hidden-4096
BF16-output variant (`sf_layout="bf16"`) on `sm_107a`.
- **This PR:** two hidden-4096 quantized-output variants on `sm_107a`:
- `sf_layout="fp8_group128"` also stores `y_fp8` (FP8-E4M3, `[T, 4096]`)
and `y_fp8_sf` (FP32, `[T, 32]`, one scale per 128-column group per
token). These are bitwise equal to vLLM's
`per_token_group_quant_fp8(y_bf16, 128, use_ue8m0=fp8_sf_ue8m0)` applied
to the step's own BF16 output. `fp8_sf_ue8m0=True` is the default, which
gives power-of-two scales.
- `sf_layout="nvfp4"` also stores `y_fp4` (packed E2M1, uint8 `[T,
2048]`) and `y_fp4_sf` (FP8-E4M3, `[T, 256]`, linear layout, one scale
per 16 columns) under a caller-supplied `fp4_global_scale`. It follows
vLLM's `scaled_fp4_quant(y_bf16, global_scale,
is_sf_swizzled_layout=False)`.

Both new variants keep the four outputs of the BF16 program bitwise
identical to that program's outputs: `new_residual` BF16, `y_bf16` BF16,
`new_post_mix` FP32 and `new_comb_res_mix` FP32. The loader routes on
the three-state output layout. It refuses an unexported combination and
reports the support matrix.

Cake has no earlier quantized-output program at hidden 4096. The
baseline is therefore the shipped hidden-4096 BF16 program, followed by
vLLM's quantization kernel on its `y_bf16` (vLLM 0.30.1rc1.dev709). For
FP8 that kernel is `per_token_group_quant_fp8` with group size 128 and
`use_ue8m0=True`. For NVFP4 it is `scaled_fp4_quant` with the linear
scale layout. Speedup is the baseline time (the sum of its two kernels)
divided by the time of this PR's single kernel. Across the 13 token
counts, the FP8 speedup ranges from 1.056× (T = 1024) to 1.197× (T =
256). The NVFP4 speedup ranges from 1.054× (T = 4096) to 1.173× (T =
32).

**NVIDIA R200 (`sm_107a`, 208 SMs), driver 615.71.09, CUDA 13.4 toolkit
(nvcc 13.4.92), PyTorch 2.13.0+cu130; SM clock 2384–2413 MHz during the
measurement. Both sides were measured in one process on the same GPU as
CUPTI kernel-time sums, with cold L2 and six interleaved ABBA groups of
64 iterations; the median is reported.**

**FP8 group-128 output (`sf_layout="fp8_group128"`), hidden 4096:**

| T (tokens) | BF16 program + vLLM FP8 group-128 quantization, µs | This
PR (fused FP8 output), µs | Speedup |
|---:|---:|---:|---:|
| 1 | 10.99 | 9.69 | 1.135× |
| 4 | 10.98 | 9.86 | 1.114× |
| 8 | 11.44 | 9.91 | 1.154× |
| 16 | 11.53 | 9.80 | 1.176× |
| 32 | 11.89 | 10.02 | 1.187× |
| 64 | 12.17 | 10.38 | 1.172× |
| 128 | 12.64 | 10.82 | 1.169× |
| 256 | 14.59 | 12.19 | 1.197× |
| 512 | 17.16 | 14.46 | 1.186× |
| 1024 | 22.66 | 21.46 | 1.056× |
| 2048 | 35.62 | 31.90 | 1.117× |
| 4096 | 67.85 | 63.25 | 1.073× |
| 8192 | 137.83 | 124.98 | 1.103× |

**NVFP4 output (`sf_layout="nvfp4"`), hidden 4096:**

| T (tokens) | BF16 program + vLLM NVFP4 quantization, µs | This PR
(fused NVFP4 output), µs | Speedup |
|---:|---:|---:|---:|
| 1 | 10.32 | 9.02 | 1.144× |
| 4 | 10.43 | 9.09 | 1.148× |
| 8 | 10.77 | 9.31 | 1.156× |
| 16 | 10.82 | 9.39 | 1.152× |
| 32 | 11.20 | 9.54 | 1.173× |
| 64 | 11.55 | 9.95 | 1.161× |
| 128 | 11.90 | 10.53 | 1.130× |
| 256 | 13.82 | 12.16 | 1.137× |
| 512 | 16.00 | 14.37 | 1.114× |
| 1024 | 20.66 | 18.78 | 1.100× |
| 2048 | 31.98 | 29.28 | 1.092× |
| 4096 | 60.83 | 57.72 | 1.054× |
| 8192 | 125.17 | 115.87 | 1.080× |

Cake's other variants of this kernel are the 14 hidden-5120 FP8-output
programs on `sm_100a` / `sm_103a` and the hidden-4096 BF16 program on
`sm_107a`; the two new variants ship on `sm_107a` only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added experimental group-of-128 FP8 and NVFP4 output options for
hidden size 4096, alongside BF16 output.
  * Added controls for FP8 scale format and NVFP4 global scale.
* Added an example that displays output and plan details and compares
quantized results with vLLM when available.
* **Compatibility**
* Quantized layouts are available only on supported hardware. NVFP4
requires a global scale.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c0e51ae](https://github.com/flashinfer-ai/flashinfer/commit/c0e51ae29b19960037ae064b0ec0c45b636a312d)

- **作者**: Yang Xu
- **时间**: 2026-10-23T20:36:55Z
- **提交信息**: perf: reduce Frost low-latency MoE host submission overhead (#7127)

<!-- .github/pull_request_template.md -->

## 📌 Description

Warm Frost calls currently reconstruct DLPack wrappers and pointer
descriptors and cross the Python/CuTe boundary separately for each
launch. This change compiles one TVM-FFI host entry per tactic, passes
current tensors directly, and forms views/descriptors inside that entry.
Existing Frost callers benefit without an API change. Device kernels and
their launch sequence stay the same.

The cache holds executable code and immutable specialization metadata.
Each call binds its own tensors and current stream; it does not cache
pointers, workspace, or stream state.

B300 validation against main `3f398977d` after #7053 merged covers BF16,
MXFP4/MXFP8, MXFP8/MXFP8 and NVFP4, T=1/2/4, and SwiGLU/SiTU/SiLU. Warm
public-API CPU submission is **2.85–4.65× faster**, and the prepacked
runner is **5.35–9.77× faster**. GPU time and plain CUDA Graph replay
CPU are separately measured; no model-throughput improvement is claimed.

Representative T=1 SwiGLU cases (µs); same B300, H=2048/physical
I=1408/E=64/top-k=6, tensors and tactics. Values are medians of two
opposite-order process medians.

| Path | Public API before → after | Host speedup | Prepacked runner
before → after | GPU before → after |
|---|---:|---:|---:|---:|
| BF16 FMA | 106.04 → 35.81 | 2.96× | 83.25 → 14.64 | 26.63 → 26.65 |
| MXFP4 TC128 | 260.85 → 61.85 | 4.22× | 217.82 → 24.90 | 10.33 → 10.33
|
| MXFP4 FMA | 154.30 → 47.30 | 3.26× | 117.98 → 14.33 | 17.25 → 17.25 |
| MXFP8 TC128 | 256.21 → 60.98 | 4.20× | 213.17 → 25.74 | 10.50 → 10.50
|
| MXFP8 FMA | 152.79 → 47.38 | 3.23× | 116.25 → 15.13 | 24.52 → 24.52 |
| NVFP4 FMA | 162.43 → 48.37 | 3.36× | 125.88 → 16.02 | 13.23 → 13.23 |

Python 3.12.15, PyTorch 2.14.1+cu130, CuTe DSL 4.8.0, apache-tvm-ffi
0.1.11, Intel Xeon Platinum 8570. Host intervals stop at Python return,
with synchronization outside timing. Warm public calls include the
normal winner-cache lookup, validation, packing and workspace
allocation; weight preparation, input quantization, initial tactic
selection and compilation occur before timing. GPU intervals use a
separate 50-call event-instrumented CUDA Graph with identical workspace
addresses, no L2 flush, and µs per MoE call. Output snapshots are
checked against independent call buffers. Paired GPU deltas are within
-0.32%..+0.26%; A/A is within -0.28%..+0.27%. CPU replay uses an
uninstrumented graph and has a median of 2.94 µs per 50-call replay.

[Performance
explanation](https://github.com/flashinfer-ai/flashinfer/blob/perf/frost-host-overhead-20261022/docs/frost_low_latency_moe.md#warm-host-submission)
and [machine-readable B300
data](https://github.com/flashinfer-ai/flashinfer/blob/perf/frost-host-overhead-20261022/docs/frost_low_latency_host_b300.json)
accompany the implementation.

The new benchmark records source hashes, verifies matching shared
wrappers/device helpers, reverses A/B order, and supports A/A noise
controls. Numerical checks compare baseline/candidate and public/replay
after routing changes.


## 🔍 Related Issues

Follow-up to #7053; host submission only. Auto dispatch, legacy adapter
migration and autotuner changes are outside this PR.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted pre-commit hooks passed for all changed files; the full-tree
formatter was not run.

Local B300 against merged main: **166 passed, 2 skipped** across the
five Frost test files. The two skips require two visible GPUs for
noncurrent-device checks; this allocation exposes one. Two
native-fallback cases passed on retry after fixing the isolated
container's cache permissions and excluding an older optional AOT wheel;
the source and tests were unchanged. The same production-source hashes
previously passed **149 tests on SM107** before the main rebase. New
tests cover fresh pointers/weights/workspaces, two threads and CUDA
streams, changed-input graph replay, no warm compilation/DLPack
wrapping, and release of call storage.

```bash
pytest -q tests/moe/test_frost_low_latency_host.py \
  tests/moe/test_frost_low_latency_bf16.py \
  tests/moe/test_frost_low_latency_mx_activations.py \
  tests/moe/test_frost_low_latency_nvfp4.py \
  tests/moe/test_frost_low_latency.py
```

Targeted CI on final head `2d70d8a34`: B200 and GB300 CuTe DSL 4.8 jobs
each passed **166 tests with 2 skips**; the two SM107 shards together
passed **166 tests with 2 skips**. All 63 new host-entry tests passed on
each platform. The skips are the existing two-GPU/noncurrent-device
checks. The [public focused H100
job](https://github.com/flashinfer-ai/flashinfer/actions/runs/40009112971/job/120604824261)
passed 5 tests and skipped 163 unsupported cases; it does not provide
native Frost GPU coverage. Public AOT builds in [the same
run](https://github.com/flashinfer-ai/flashinfer/actions/runs/40009112971)
are still running.

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

Please focus on per-call binding and lifetime semantics, the
current-stream FFI binding, the MX scale prefix view, and raw/finalized
output parity. There is no change to numerical contracts, tactics, GPU
kernels or PDL dependencies. No GPU/model speedup is claimed.

### [1ff9f67](https://github.com/flashinfer-ai/flashinfer/commit/1ff9f6772521495a389be2ef9f144ccf4a895459)

- **作者**: eigen
- **时间**: 2026-10-23T19:47:50Z
- **提交信息**: perf(cake_dsa_indexer): far-sample first threshold on the descending programs (#7125)

This PR updates the Cake DSA indexer top-k scan behind
`flashinfer.dsa_indexer.dsa_indexer_topk`. The kernel has one data-type
variant (BF16 queries and keys, FP32 head weights and scores). It is
built from per-architecture scan programs (wide, narrow, split,
paired-CTA, l6) plus finalize and merge kernels. This PR delivers new
descending-tile-order scan programs for sm_100a and sm_107a. Their
sampled first threshold now ranks only the far sample keys, so
attention-sink plus local-band scores no longer force a whole-unit
re-stream. The baseline is the previous Cake version of this kernel in
FlashInfer main, with the same default plan. On GB200 this PR is
1.3x-1.8x faster on eight of the ten sink rows, and Z3 and Z3cp are near
parity. The other 19 rows stay within 3 % of the previous version and
are slightly slower on the paired-CTA packed rows. On GB300 the programs
are unchanged in generated code, and the sink rows measure 1.00x-1.02x.

Speedup on GB200:

GB200 (NVIDIA GB200, sm_100a, CUDA 13.4 (nvcc 13.4.92)); ms = median of
the two arm-order processes of the CUPTI kernel time; speedup = previous
/ this PR.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 22.588 | 12.692 | 1.78x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 23.654 |
13.721 | 1.72x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 22.138 |
12.561 | 1.76x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
43.909 | 34.133 | 1.29x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 3.317 | 2.252 | 1.47x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.707 | 24.274 | 1.02x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.703 | 1.665 | 1.02x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 5.479 | 3.450 | 1.59x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 19.751 | 14.671 | 1.35x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 366.792 | 211.554 | 1.73x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.516 | 3.613
| 0.97x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.551 | 3.635 | 0.98x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.532 | 3.604 | 0.98x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.818 | 3.909 |
0.98x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.436
| 0.430 | 1.01x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.250 | 1.229 | 1.02x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
4.010 | 4.106 | 0.98x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
14.515 | 14.729 | 0.99x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
55.094 | 54.834 | 1.00x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
214.112 | 214.177 | 1.00x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
876.665 | 873.889 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
14.371 | 14.560 | 0.99x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.756 | 1.721 |
1.02x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 3.331 | 3.241
| 1.03x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.460 |
3.533 | 0.98x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 8.112 | 8.180 |
0.99x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 13.489 | 13.555
| 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 15.546 |
15.592 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3870.189 | 3866.585 | 1.00x |

Speedup on GB300:

GB300 (NVIDIA GB300, sm_103a, CUDA 13.4 (nvcc 13.4.92)); ms = median of
the two arm-order processes of the CUPTI kernel time; speedup = previous
/ this PR.

| row | shape | T (queries) | Tkv (keys) | segments | top-k | previous
Cake kernel ms | this PR ms | speedup |
|---|---|---|---|---|---|---|---|---|
| Z1 | #7042 repro: 262k document, CP16 zigzag rank 0 | 16384 | 270336 |
2 | 2048 | 11.954 | 11.825 | 1.01x |
| Z1k4096 | Z1 with top-k 4096 | 16384 | 270336 | 2 | 4096 | 15.446 |
15.328 | 1.01x |
| Z1k256 | Z1 with top-k 256 | 16384 | 270336 | 2 | 256 | 11.364 |
11.232 | 1.01x |
| Z2 | 8 x 32k documents, full causal | 262144 | 262144 | 8 | 2048 |
31.847 | 31.501 | 1.01x |
| Z2cp | 8 x 32k documents, CP16 zigzag rank 0 | 16384 | 270336 | 16 |
2048 | 2.053 | 2.026 | 1.01x |
| Z3 | packed 4k-64k documents, full causal | 169984 | 169984 | 8 | 2048
| 24.842 | 24.508 | 1.01x |
| Z3cp | packed 4k-64k documents, CP16 zigzag rank 0 | 10624 | 175296 |
16 | 2048 | 1.797 | 1.788 | 1.01x |
| P1sink | recorded P1 geometry with sink statistics | 16231 | 268757 |
8 | 2048 | 3.744 | 3.708 | 1.01x |
| S4sink | one 64k causal document, sink statistics | 65536 | 65536 | 1
| 2048 | 14.987 | 14.809 | 1.01x |
| S6sink | one 262k causal document, sink statistics | 262144 | 262144 |
1 | 2048 | 195.336 | 193.048 | 1.01x |
| P1 | recorded packed call | 16231 | 268757 | 8 | 2048 | 3.443 | 3.404
| 1.01x |
| P1_peaked | P1 with dominating keys | 16231 | 268757 | 8 | 2048 |
3.448 | 3.405 | 1.01x |
| P2 | second recorded token count, boundaries derived | 16172 | 267520
| 8 | 2048 | 3.429 | 3.389 | 1.01x |
| P3 | P1 with top-k 4096 | 16231 | 268757 | 8 | 4096 | 3.737 | 3.675 |
1.02x |
| S1 | single causal document N = 8192 | 8192 | 8192 | 1 | 2048 | 0.429
| 0.415 | 1.04x |
| S2 | single causal document N = 16384 | 16384 | 16384 | 1 | 2048 |
1.229 | 1.212 | 1.01x |
| S3 | single causal document N = 32768 | 32768 | 32768 | 1 | 2048 |
3.847 | 3.788 | 1.02x |
| S4 | single causal document N = 65536 | 65536 | 65536 | 1 | 2048 |
13.448 | 13.375 | 1.01x |
| S5 | single causal document N = 131072 | 131072 | 131072 | 1 | 2048 |
49.312 | 49.036 | 1.01x |
| S6 | single causal document N = 262144 | 262144 | 262144 | 1 | 2048 |
186.089 | 185.136 | 1.01x |
| S7 | single causal document N = 524288 | 524288 | 524288 | 1 | 2048 |
762.909 | 761.861 | 1.00x |
| S8 | single causal document N = 1048576 | 1048576 | 1048576 | 1 | 2048
| 3252.408 | 3244.856 | 1.00x |
| S4_peaked | S4 with dominating keys | 65536 | 65536 | 1 | 2048 |
13.440 | 13.296 | 1.01x |
| C1 | CP tail 4096 x 65536 | 4096 | 65536 | 1 | 2048 | 1.579 | 1.561 |
1.01x |
| C2 | CP tail 4096 x 131072 | 4096 | 131072 | 1 | 2048 | 2.950 | 2.927
| 1.01x |
| C3 | packed 8 x (2048 x 32768) | 16384 | 262144 | 8 | 2048 | 3.261 |
3.206 | 1.02x |
| V1 | N = 65536, ratio 2 | 65536 | 32768 | 1 | 2048 | 7.617 | 7.508 |
1.01x |
| V2 | N = 65536, top-k 256 | 65536 | 65536 | 1 | 256 | 12.232 | 12.201
| 1.00x |
| V3 | N = 65536, top-k 4096 | 65536 | 65536 | 1 | 4096 | 14.601 |
14.424 | 1.01x |

Cake ships no other data-type variant of this kernel; its
ascending-tile-order scan programs (every sm_103a program, the sm_100a
l6 and sm_107a wide programs) are unchanged in generated code, and the
family ships on sm_100a (GB200), sm_103a (GB300) and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated the experimental indexer’s processing and memory usage for
supported workloads.
* **Benchmarking**
* Added attention-sink and context-parallel benchmark cases, with
options to compare implementations and inspect output consistency.
* **Testing**
* Added checks for attention-sink behavior, reference accuracy, and
consistency across sampling modes.
* **Documentation**
* Clarified how generated package artifacts are maintained and how their
integrity is checked.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [c01aa77](https://github.com/flashinfer-ai/flashinfer/commit/c01aa7779bbbb04c247d76a391cbabbcaddb3622)

- **作者**: eigen
- **时间**: 2026-10-23T19:45:31Z
- **提交信息**: deslop(cake_moe_grouped_gemm): fold the fp32 clones onto bf16, share the preamble and binding blocks, drop dead glue (#7124)

## 📌 Description

### Summary

This PR is the round-2 deslop of the experimental package
`flashinfer/experimental/cake_moe_grouped_gemm`. The package holds
Cake's grouped GEMM for MoE training. It covers the forward pass, the
data gradient, and the weight gradient with a split-K tail reduction. It
targets SM100 (B200, compute capability 10.0), SM103 (GB300, 10.3) and
SM107 (R200, 10.7).

The package has these parts:
- a registry, `cake_jit.py` (`PROGRAMS`, `ROUTES`,
`HOST_PLAN_CONSTANTS`);
- a host backend, `cake_backend.py`;
- a manifest, `build.json`, with 26 entries: 10 on `sm_100a`, 10 on
`sm_103a` and 6 on `sm_107a`. Each entry is one JIT library, built from
one kernel translation unit and one host binding;
- generated kernel and binding sources under
`csrc/cake_moe_grouped_gemm/`;
- a README.

Three test files collect 44 ids:
`tests/experimental/test_cake_moe_grouped_gemm.py` (38),
`tests/experimental/test_cake_moe_grouped_gemm_api.py` (2) and
`tests/experimental/test_cake_moe_grouped_gemm_standalone.py` (4).

The six commits are mechanical and preserve behaviour:
- commit 1 drops dead launcher glue and registry scaffolding;
- commit 2 drops six registry keys that no code reads;
- commit 3 folds the three fp32 weight-gradient programs onto their bf16
twins as a compile-line specialization;
- commit 4 moves the shared kernel preamble and device helpers into one
device header;
- commit 5 moves the shared binding TMA encoders and the shared-memory
opt-in into four fragment headers;
- commit 6 drops two unused macros and three unused locals from the
tail-reduce kernel.

Commits 3-6 fold or edit exporter-generated files by hand. A later
export regenerates them (see Reviewer Notes).

Each commit has an identity proof. For the compiled units, the proof
covers preprocessed text, SASS, symbol tables and host exports. For the
Python files, it covers reference searches and AST checks. Totals versus
`main` `8ec9464ce`: 26 files changed (5 new headers, 6 deleted sources,
15 edited files), +893 / -4,018. Part of #6681.

### Changes

Base: `main` `8ec9464ce`. Head:
`59a76e187a80784186c2e916e876c925b6907b37` (6 commits). Reviewer Notes
give the `main` sha at publish time.

Several commits edit the same files: `build.json`, the README,
`cake_jit.py`, and some kernel and binding units. So the per-commit
counts do not sum to the branch totals.

### Commit 1 (7ac7f9cfd) - cake_moe_grouped_gemm: drop dead launcher
glue, registry scaffolding

3 files, +2 / -52.

- **Dead host code.** These parts have zero readers in the repository:
- the `_Launch.stage` / `_Launch.module` fields, and the two keywords
that `_bind` passed for them;
  - `_Launch.__call__`;
- the `GroupedGemmLaunch.stage_launchers` / `stage_modules` properties;
  - the `cake_jit` helpers `registered_arches` / `specs_for_arch`.

Same-named symbols in other packages read their own definitions.
`GroupedGemmLaunch.launch` and its `__call__` alias are the only
launchers, and they stay.
- **"Registry not filled" scaffolding.** `HOST_PLAN_CONSTANTS` is a
non-empty literal. So the `NotImplementedError` branch of
`host_plan_constants()` is unreachable. So is the `or not
HOST_PLAN_CONSTANTS` operand of `generated_program_available()`.
- **str-key branch.** The `cycles_per_step` keys are the ints 256 and
512. So only an external caller that passes JSON-round-tripped constants
can reach the str-key branch of `_cycles_per_step`. This PR declares
that deletion as medium confidence. The `KeyError` text stays.
- **Test helper.** The backend test's `_constants()` helper skipped on
an empty constant. That skip never fires. The helper folds into
`HOST_PLAN_CONSTANTS`.
- **Delta.** 50 lines are removed and 2 lines are edited. No error text
of a reachable path changes. No import changes. The package's standalone
import contract and its 9 public names are unchanged.
- **Proof.** Pruning the deleted nodes from the three base files
reproduces the new files (10 / 2 / 2 AST nodes, docstrings masked). A
whole-repository reference search per deleted name finds no reader
outside the deleted lines. The CPU run (CUDA hidden) and the GPU runs of
the three test files collect the same 44 ids on both trees. Each id
reports the same result on both trees.

### Commit 2 (683a6dceb) - cake_moe_grouped_gemm: drop the unread
exporter-written registry keys

1 file, +1 / -88.

- **Removed keys.** Six registry keys in `cake_jit.py` have no reader.
They take 87 lines in total:
  - `ROUTES[*].host_plan` (60 lines: the six per-route formula dicts);
- `ROUTES[*].public_helper`, `ROUTES[*].out_dtype` and
`ROUTES[*].tile_k` (6 lines each);
  - `PROGRAMS[*].kernel` (8 lines);
  - `HOST_PLAN_CONSTANTS.block_m` (1 line).
- **No reader.** A whole-repository search covers each key in its
subscript, `.get` and string forms. It finds no reader. The package, its
three test files, the benchmark and the manifest checker read only
these: `op`, `arches`, `stages` (`name` / `program` /
`specializations`), `library`, `ffi_entry`, `arg_plan`, `launch.block`
and the other `HOST_PLAN_CONSTANTS` entries. The benchmark's
`row["out_dtype"]` reads address the benchmark's own rows. The backend
test's `plan["tile_k"]` reads address the planner's plan dict. Neither
reads these records. The module comment loses its "host plan" clause.
- **Delta.** 87 lines are removed, 1 comment line is edited, and nothing
is added. The three literals keep every other key, in order.
`record_name`, `program_registered`, `select_module`, `stage_binding`
and `library_name` see identical inputs. The planner constants lose
`block_m` only. No import changes. The standalone import contract and
the 9 public names are unchanged.
- **Proof.** A whole-repository reference search per key finds no hit
outside the deleted lines. The `PROGRAMS` / `ROUTES` /
`HOST_PLAN_CONSTANTS` literals equal the parent's minus the removed keys
(checked with stdlib `ast`). The manifest checker's registry-refs rule
holds with 26 refs for 26 entries. The planner and selection streams are
the same on both trees. The CPU and GPU test runs report the same result
per id.

### Commit 3 (96889f7bc) - cake_moe_grouped_gemm: fold the fp32 output
clones onto bf16 programs

15 files, +442 / -2,911.

- **The clones.** Three fp32 weight-gradient programs were clones of
their bf16 twins: tail-reduce, k256 main and k512 main. They differ only
in the output element type. The kernels differ in 37 / 72 / 72 lines, in
2 / 3 / 3 hunks. The hunks are the kernel signature and the epilogue
stores (bf16x2-pack versus float4). The bindings differ at three sites:
the kernel declaration, the `check_dtype` of C and the C pointer cast.
- **Specialization.** The output width is now a compile-line
specialization of the shared bf16 sources. The compile definition
`WGRAD_OUT` is 16 (default) or 32. It is carried like the existing
`WGRAD_TILE`. The kernel units switch the hunks through whole-line `#if
WGRAD_OUT == 32` arms behind a validated `#ifndef` default. The binding
units switch through the object-like macros `CAKE_OUT_T` and
`CAKE_OUT_DLDTYPE`.
- **Symbols.** The per-library compile definitions `CAKE_PROGRAM_KERNEL`
and `CAKE_PROGRAM_SHIM` have `#ifndef` defaults. They keep every
library's own kernel symbol and host-shim namespace. So the fp32 builds
export the same symbols as before. The six fp32 source files are deleted
(2,619 lines).
- **Registry.** `PROGRAMS` drops the three fp32 records (72 lines).
Apart from the library name, they were identical to the twins' records.
The two fp32 routes bind the twin programs with `{"WGRAD_OUT": 32}`,
plus `WGRAD_TILE` on the tail stage. Route names, arches and record
names are unchanged.
- **Manifest.** The ten fp32 entries become
`<twin>_wgrad_out32[_wgrad_tileN]_<arch>` on the twin sources. Their
`nvcc_flags` are the entry's flags plus three definitions:
`WGRAD_OUT=32`, the clone's kernel symbol and the clone's shim
namespace. They carry the twin entry's closure digest. The manifest
keeps 26 entries, sorted by name. Every edited source digest is
recomputed.
- **README.** The three passages on the fp32 programs now describe the
specialization. A new note says that the shared sources, registry rows
and manifest entries are a hand fold of exported files. A later export
regenerates them.
- **Proof.**
- Each shared kernel, rendered with `WGRAD_OUT` undefined, reproduces
the base bf16 unit byte for byte (3 / 3).
- Each shared kernel, rendered with `WGRAD_OUT=32` and the clone symbol,
reproduces the base fp32 unit byte for byte (3 / 3).
- Each shared binding, after macro expansion, is token-identical to the
base twin and to the base clone (3 / 3 each).
- The SASS, the symbol table and the host exports of all 26 libraries
are identical on `sm_100a`, `sm_103a` and `sm_107a`.
  - The manifest checker's refs rule holds with 26 refs for 26 entries.
- The GPU tests report the same result per id on both trees, the 6 fp32
ids included.
- **Declared delta.**
- The `TVM_FFI_CHECK` backtrace lines of the three kept bindings shift
by +18. The cause is 18 directive lines inserted after `#include
<cstdint>`.
  - The launch-failure string is assembled from adjacent literals.
  - The fp32 builds report the twin's file name in `__FILE__`.
- The ten fp32 JIT library names change. So a warm JIT workspace
rebuilds those ten once.

### Commit 4 (799017040) - cake_moe_grouped_gemm: share the kernel
preamble via one device header

8 files, +185 / -564.

- **Shared text.** Every kernel unit opened with the same 32-line ABI
block. The block holds:
  - the fixed-width typedefs;
  - the 64-aligned tensor-map struct;
  - the `CUtensorMap` typedef or the `<cuda.h>` include;
  - the `<cuda_bf16.h>` and `<cuda_fp8.h>` includes;
  - `make_warp_uniform`.

Every unit also carried the unused define `CAKE_INF CUDART_INF_F` and
`#include <math_constants.h>`. The four main kernels also carried
byte-identical copies of eight device helpers: `elect_sync`,
`mbarrier_init`, `mbarrier_wait`, `union MmaSmemDesc`,
`elect_commit_cg2_multicast`, `tma_3d_gmem2smem_cta2`, `tmem_ld_x16`,
and `tma_4d_gmem2smem_cta2` (forward kernel only).
- **New header.**
`csrc/cake_moe_grouped_gemm/cake_moe_grouped_gemm_device.cuh` (144
lines) now carries that text once. It holds the ABI block, the
`CAKE_INF` define, the math-constants include and the helpers. The
helpers sit behind need-guards. A main kernel defines
`CAKE_MOE_GROUPED_GEMM_NEED_TCGEN05_HELPERS` before the include. The
forward kernel also defines
`CAKE_MOE_GROUPED_GEMM_NEED_TMA_4D_GMEM2SMEM_CTA2`.
- **Units.** Each unit replaces its copies with its need define(s) and
the include. Its define block, the separators inside that block and the
kernel body are untouched. The units lose 538 lines and gain 10. The
five kernel digests in `build.json` are recomputed (26 entries). The
README gains one sentence.
- **Proof.** The preprocessed device and host text of every kernel unit
is identical on the three architectures, after dropping line markers and
blank lines. The SASS and the symbol table of all 26 libraries are
identical. The host bindings are untouched. The moved lines are
definitions and includes that read no unit macro.
- **One reordering.** The header's text now expands as a whole before
the unit's define block. At the previous commit, the include and the
helpers followed that define block. The header names none of the units'
defines. The preprocessed-text comparison also covers the system
header's text.
- **Declared.** The header ships with the package sources (`csrc/**`).
The build's dependency tracking verifies it; no manifest digest does. It
is a hand fold of exported text that a later export regenerates.

### Commit 5 (9c3b1f535) - cake_moe_grouped_gemm: share the binding TMA
encoders and smem opt-in

10 files, +287 / -422.

- **Shared blocks.** Four bindings carried byte-identical copies of
shared blocks: forward, data gradient, and the two weight-gradient main
kernels. The blocks are:
- the dynamic shared-memory opt-in `CakeSetMaxDynamicSmem` (22 lines,
four copies);
- `EncodeTma_A` with box {64, 128, 1} (53 lines; forward and data
gradient);
- `EncodeTma_A` and `EncodeTma_B` with box {64, 64, 1} (53 lines each;
the two weight-gradient bindings).
- **New headers.** Four fragment headers under
`csrc/cake_moe_grouped_gemm/` carry each block once:
  - `cake_moe_grouped_gemm_binding_smem.h`;
  - `cake_moe_grouped_gemm_binding_tma_a_box64x128.h`;
  - `cake_moe_grouped_gemm_binding_tma_a_box64x64.h`;
  - `cake_moe_grouped_gemm_binding_tma_b_box64x64.h`.

Each header holds the license, two comment lines and the block verbatim.
The headers have no include guard. Each unit includes a header once,
inside the host-shim namespace, at the first line of the block it
replaces.
- **Bindings.** Each binding replaces its copies with one `#include`
line per block. The blank separators, `Run()` and every other line are
untouched. So are the single-copy encoders: the forward 4D `EncodeTma_B`
and the data-gradient `EncodeTma_B` with its third dimension. The
bindings lose 406 lines and gain 10. The headers add 257 lines. The four
binding digests in `build.json` are recomputed (16 entries). The README
gains one sentence.
- **Proof.** The preprocessed host text of every edited binding is
identical on the three architectures, after dropping line markers and
blank lines. The only exceptions are the file and line arguments of the
check sites that moved into a header:
- 96 of the 170 `TVM_FFI_CHECK` / `TVM_FFI_CHECK_CUDA_ERROR` sites now
name the header and its line (17 forward, 17 data gradient, 31 per
weight-gradient binding);
- the 74 sites that stay in a binding move up by exactly 73 lines
(forward, data gradient) or 125 lines (weight gradient).

Every message text is unchanged. The host object of every library
exports the same symbols as before. The kernels are untouched. No test
asserts on a backtrace.
- **Declared.** The headers ship with the package sources. The build's
dependency tracking verifies them; no manifest digest does. They are a
hand fold of exported text that a later export regenerates.

### Commit 6 (59a76e187) - cake_moe_grouped_gemm: drop unused
tail-reduce kernel definitions

2 files, +10 / -15.

- **Unused definitions.** The tail-reduce kernel is the one
weight-gradient reduction source. It is built for both output widths,
both tile sizes and three architectures. It defined two macros that no
line expands: `NUM_MAIN_STAGES` and `BLOCK_M`. It also defined three
locals that no statement reads: `lane` (`tid % 32`), `num_bids`
(`gridDim.x`) and `cta_rank` (0).
- **Edit.** The five definition lines are deleted (-5 / +0 source
lines). The local `warp` stays. Its initialiser is an `asm volatile`
shuffle, and removing it would change the generated code. Blank
separators, every comment, the directive blocks and every other line are
untouched. The ten `build.json` entries that list this source carry its
recomputed digest.
- **Proof.** The name check strips comments and string literals first.
In the parent's source, each deleted name occurs exactly once, at its
definition. It occurs nowhere in the shared device header, and zero
times after the edit. On the three architectures, the preprocessed
device and host passes differ from the previous commit by exactly the
three deleted local-definition lines. The two macro deletions leave no
preprocessed trace. The SASS and the symbol table of every tail library
are identical on the three architectures, for both output widths and
both tile sizes.
- **Declared.** This is a hand edit of exported text that a later export
regenerates.

### Validation

The compile-only rows compare the base `8ec9464ce` with each commit and
with the head, on `sm_100a`, `sm_103a` and `sm_107a`. Each tree is
exported from git into its own staging directory. Before any comparison,
every staging root path is replaced by one placeholder. So line markers
and `__FILE__` strings agree between trees.

The compile-only rows come in two kinds:
- 16 identity rows: one per kept library on each architecture, compared
with the same library at the base;
- 10 fold rows: one per renamed fp32 library on each architecture,
compared with the base clone library it replaces.

The compile-only rows use CUDA 13.4 (`nvcc` 13.4.92). The flag line of
record is the manifest's own line for each architecture:

`-gencode=arch=compute_100a,code=sm_100a -std=c++17 -O3 -DNDEBUG
--compiler-options=-fPIC --expt-relaxed-constexpr -Xfatbin=-compress-all
--compress-mode=size -static-global-template-stub=false`

The other two architectures use `compute_103a` / `sm_103a` and
`compute_107a` / `sm_107a`. Each entry's own `nvcc_flags` follow. The
weight-gradient entries carry `WGRAD_TILE`. The ten renamed fp32 entries
add `WGRAD_OUT=32` and the clone's kernel-symbol and shim-namespace
definitions. The `-cubin` builds drop the two fatbin compression options
on both sides.

The container that ran the compile-only rows did not capture the JIT
build's generated compile line. Its Python environment has no `torch`.
So the manifest-derived line is the line of record. The SASS row's
result names which form was used.

**Compile-only rows**

- **Pre-checks.** Three checks run first. The binding units compile with
the tvm-ffi and dlpack include directories alone. Every `TVM_FFI_CHECK`
site maps to exactly one backtrace site in the preprocessed text. The
third check is the export-macro probe: INCLUDE_CLOSURE (373 files,
Python.h no), F_SHAPE OK (40 source sites == 40 -E sites), EXPORT_MACRO
on
cake_moe_grouped_gemm_bc774d802e4f0b3ac27c_wgrad_out32_wgrad_tile256_sm_100a:
clone shim named, twin shim occurrences 0
- **Kernel units, preprocessed text.** Both `nvcc -E` passes (device and
host) run on every kernel unit. The comparison drops `# <n> "<file>"`
line markers and whitespace-only lines. Nothing else is masked. Identity
rows compare with the base. Fold rows compare with the base clone unit,
after the clone-to-twin basename mask: 16/16 identity + 10/10 fold (both
-E passes identical after N0)
- **Binding units, preprocessed text.** The same comparison runs for
every binding unit, with two declared accountings. First, adjacent
string literals are joined (the commit 3 launch-failure message).
Second, every `TVMFFIBacktrace("<file>", <line>` pair is classified. It
is either a site moved to a header (commit 5, 96 sites expected), or a
binding's own site shifted by exactly +18 (commit 3) or -73 / -125
(commit 5): 16/16 identity + 10/10 fold (N0 + F: 412 moved backtrace
sites over the compiled binding rows, 96 per architecture)
- **Fold rows.** The ten renamed fp32 libraries are compared with the
base clone libraries in all six compile-only comparisons: kernel text,
binding text, SASS, symbol table, metadata and host object: 10/10 fold
rows (E-Kf / E-Bf / S-fold / SYM-fold / INFO-fold / H-fold) against the
base clone libraries
- **SASS.** `nvcc -cubin` builds each library on each tree and
architecture. `cuobjdump -sass` output is compared per function, after
masking instruction addresses and encodings. The function sets must be
identical and must name exactly the library's kernel: 16/16 identity +
10/10 fold (per Function block; CUDA 13.4; flag line of record derived
from build.json (Form D; the JIT line was not captured))
- **Symbol tables.** The full `cuobjdump -symbols` table of each cubin
is compared as a multiset. Only the compiler-generated module id inside
internal-linkage names is canonicalised. `nvcc` derives that id from the
unit text, so any edit changes it. Everything else in each name is
compared: 16/16 identity + 10/10 fold: full symbol tables identical
after the declared module-id mask (0/0 entries masked; raw delta -0+0
INFO)
- **Resource usage and kernel metadata.** `cuobjdump -res-usage` must be
identical per kernel: registers, stack, shared, local and constant
banks. The per-kernel metadata records of the cubin (`.nv.info`
sections, decoded from the ELF) must also be identical: cuobjdump
-res-usage identical per Function on every S row (26); .nv.info per
kernel decoded identical on every compiled row (26; raw-identical 26)
- **Host objects.** `nvcc -c` builds each binding. The export set
{`build_cuda_version`, `run`} and the `nm` symbol table must be
identical. One exclusion is declared: the compiler-numbered local labels
of the literal pool (`.LC<n>`). Commit 5 moves `__FILE__` strings, which
renumbers them, so they are left out and their counts are recorded. The
kernel symbol must be undefined on both sides. Fold rows also check that
the clone's shim namespace is absent: 16/16 identity + 10/10 fold
(exports {build_cuda_version, run} + symbol tables identical)

**Manifest rows** (CPU, both trees)

- **Digests.** The SHA-256 of every source listed in `build.json` is
recomputed from the tree. Both trees must show 0 mismatches. The head
manifest must equal the fold's planned manifest, apart from digest
values. Entries must be kept or renamed as declared: 0 mismatches on
both trees; entries kept 16 / renamed 10 -> 10; 10 kept-source digests
changed; head manifest == the fold document modulo digests
- **Manifest checker.** The upstream
`scripts/check_cake_build_manifests.py --in-tree --package
cake_moe_grouped_gemm` runs on both trees. A replica of its rule also
runs. The replica also records the new headers, which no manifest digest
covers, by design: M1 exit 0 both trees; M2 0 findings both trees,
registry refs 26 == entries 26, INFO +5 new headers (5 recorded with
sha256)

**Other rows**

- **Reference search.** `git grep` word, string and AST rows run at the
head for every removed name and key of commits 1 and 2 (17 rows). Each
name must have 0 hits at the head and a definition at the base: 17/17
reference rows: 0 hits at HEAD, defined at the base
- **AST prune.** Pruning the deleted nodes from the base
`cake_backend.py`, `cake_jit.py` and the backend test must reproduce the
commit-1 files (docstrings masked; 10 / 2 / 2 nodes): 3/3 AST-prune
identities (cake_backend.py, cake_jit.py, the test)
- **Planner.** The plan and selection stream is enumerated on both trees
at SM counts 148 / 160 / 212. The base stream, with the fp32 library
renames applied, must equal the head stream. The constants must lose
`block_m` only: 378 planner records identical on both trees (constants
13 -> 12: ['block_m'] removed)
- **Apply replay.** Each commit's apply script re-runs in chain order on
a fresh copy of the base. After each unit, the tree must equal that
commit's tree byte for byte: 6 unit scripts replayed on the base (U1 U2
U3 U4 U5 U6); tree identical to the commits
- **Tests on a B200** (SM100, compute capability 10.0). The three test
files run on the base tree, then on the head tree. Each arm runs in a
fresh JIT workspace. The module directories are asserted absent before
each arm, so each arm JIT-builds its 4 libraries from its own tree. All
44 ids run on this GPU (44 passed / 0 skipped expected). Every id must
have the same outcome on both trees, the 6 fp32-route ids included: 44
ids on B200 (SM100) (driver 580.82.07, cc 10.0): 44 passed / 0 skipped,
per-id identical on both trees; fresh JIT workspace per arm (4 modules
built per arm)
- **Tests on a GB300** (SM103, compute capability 10.3), same protocol:
44 ids on GB300 (SM103) (driver 580.167.08, cc 10.3): 44 passed / 0
skipped, per-id identical on both trees; fresh JIT workspace per arm (4
modules built per arm)
- **Tests on an R200** (SM107, compute capability 10.7), same protocol:
not run on R200 (SM107): no R200 GPU could be allocated in the
validation window; the sm_107a identity proof is the compile-only rows
of the gate step (preprocessed text, SASS, symbol tables, metadata and
host objects; 6 libraries)
- **Every library loads.** On the B200 and on the GB300, all 10
libraries of the architecture are JIT-built and loaded on both trees.
`build_cuda_version()` is called on each. The 4 renamed fp32 libraries
must load under their new names. The 6 kept libraries must be
byte-identical builds: sm_100a: 10/10 libraries built + loaded on both
trees (4 renamed fp32 entries; kept spec names identical); sm_103a:
10/10 libraries built + loaded on both trees (4 renamed fp32 entries;
kept spec names identical)
- **Benchmark outputs.** The package benchmark's 58 rows run on both
trees on the same GPU. The SHA-256 of every output tensor and the plan
of every row must be identical. Each row must be deterministic across
two runs. This row exercises the tail-reduce and k512 libraries, which
the tests never launch: sm_100a: 58/58 benchmark rows bitwise identical
(output + plan string), deterministic; sm_103a: 58/58 benchmark rows
bitwise identical (output + plan string), deterministic
- **Tests with CUDA hidden** on a CPU node, both trees. The 44 ids are
expected to split 19 passed / 25 skipped, because the 25 need a GPU.
Per-id outcomes must be identical. The standalone import probe checks
that the 9 public names resolve with `flashinfer` blocked: 44 ids: 19
passed / 25 skipped (CUDA hidden), per-id identical on both trees, every
base-passed id passes on the candidate; standalone import probe OK on
both trees
- **CPU checks.** 24 checks run on one node, on both trees:
  - chain shape and totals;
  - `git diff --check`;
  - scope of the touched paths;
  - the shared files that this PR must not touch are untouched;
  - `py_compile`;
  - ruff;
  - collect-only parity (44 ids);
  - the CUDA-hidden tests;
  - the standalone import probe;
- pre-commit on the changed files, and with `--all-files` on both
checkouts;
  - the repository's mypy hook, with no new finding;
  - the reference search;
  - the AST prune;
  - the planner;
  - the upstream and replica manifest checks;
  - the header record;
  - the digests;
  - the manifest entries versus the fold plan;
  - the apply replay;
  - source hygiene;
  - the public-text scan;
  - the commit-message form;
  - a clean worktree.

  Result: 24/24
- **Rows not run, by environment (count and reason):** 2 row(s): the JIT
build's generated compile line was not captured (the compile-only rows
used the manifest-derived flag line; see the SASS row); the R200 test
row (no R200 GPU could be allocated in the validation window; see its
row)
- **GitHub CI.** The three files run on H100 through the experimental
lane. 19 ids are expected to pass and 25 to skip, because the kernels
need SM100 / SM103 / SM107. CI has no Blackwell or Rubin runner. So the
B200 and GB300 rows are the device evidence.

**Not run, by design.**
- **Benchmark timing.** The SASS row requires identical code for every
library, and no kernel behaviour changes. The benchmark row compares
outputs only.
- **Cross-tree tensor comparison beyond the benchmark outputs.** The
identity criterion is identical per-test outcomes, plus identical SASS,
symbol tables, metadata and host exports. Where it applies, preprocessed
text must also be identical.

### Not in this PR

- **The k512 route A/B** (`k512_archs` on versus off), and the
conditional removal of the k512 libraries. This is a performance-gated
change to route selection.
- **The split-K tail A/B** (`wgrad_tail_split` 0 versus 1), and the
conditional removal of the tail-reduce libraries, the tail plan and the
partials workspace. This is performance-gated and changes behaviour.
- **New GPU test cases that force the tail-reduce and k512 paths.** In
this PR, three rows give the identity evidence for those libraries: the
per-library SASS row, the every-library-loads row and the
benchmark-output row.
- **A CI lint job that runs `scripts/check_cake_build_manifests.py
--in-tree`.** `.github/**` and `.pre-commit-config.yaml` are shared root
files. The manifest checker row in Validation runs the checker by hand
on both trees.
- **Hoisting per-call host work.** Every weight-gradient call
re-validates, re-plans and allocates the slot ring and the partials
workspace. All bindings run `check_contiguous` on the output. Moving
this work changes behaviour and performance.
- **The k256 / k512 weight-gradient fold (224 differing lines) and the
forward / data-gradient fold (72).** They need a generator parameter
(tile K, transposed-B flag), not a constant clone.
- **Deduplicating `cake_build.py` and `csrc/cake_ffi_checks.h` across
the Cake packages.** The loader-identity check and the exporter
templates own them.
- **`build.json` repeating the per-entry source and digest block.** The
manifest schema is the contract of the checker and the loader.
- **Regenerating `closure_sha256`.** Its derivation is not in the
repository. The values are unchanged, so the kept JIT module names are
unchanged too.
- **Templated TMA encoders and an i32 range-check macro in the
bindings.** They split string literals, so they belong on the exporter
side.
- **Deleting `GroupedGemmLaunch.stages`.** Its docstring makes it
public, and it has zero readers. It is left for the exporter.
- **Shrinking the README's "Build targets and layout" section to a
pointer.** That is a prose rewrite without an identity proof. Commits
3-5 edit that section to keep it true.
- **Shared root files that this PR never edits:**
  - `.pre-commit-config.yaml`, `pyproject.toml` and `pytest.ini`;
  - `scripts/**` and `tests/test_helpers/**`;
  - `flashinfer/grouped_mm/**` and `flashinfer/jit/**`;
- the package's `cake_build.py`, `_experimental.py`,
`csrc/cake_ffi_checks.h` and `csrc/.clang-format`;
  - `benchmarks/bench_cake_moe_grouped_gemm.py`.
- **Regeneration from the exporter.** Commits 3-6 are hand folds or hand
edits of generated text (see Reviewer Notes).

## 🔍 Related Issues

Tracking issue: #6681

Part of #6681

#6681 is the round-2 deslop family issue. The open items are listed
under "Not in this PR".

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on the changed files and with `--all-files` on both
checkouts (base and head). The repository's pre-commit config excludes
this package's `csrc/` tree. So no hook covers the edited units or the
new headers. The CPU checks row in Validation gives the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

One test file changes: commit 1 folds the test's own `_constants()`
helper into `HOST_PLAN_CONSTANTS`. No id is added or removed (44 ids).
The three files ran on B200, on GB300 and with CUDA hidden on a CPU node
(see Validation).

CI targets: the three files in the experimental-tests block below.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #6681
- [ ] The tracking issue names an owner, the reason for the experimental
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

```experimental-tests
tests/experimental/test_cake_moe_grouped_gemm.py
tests/experimental/test_cake_moe_grouped_gemm_api.py
tests/experimental/test_cake_moe_grouped_gemm_standalone.py
```

The package is experimental. It lives under `flashinfer/experimental/`,
and its tests live under `tests/experimental/`. This PR edits only files
in the package and one test file. It changes no core file.

## Reviewer Notes

- **Hand fold.** Commits 3-6 fold or edit exporter-generated files by
hand. This covers the shared weight-gradient sources, the device header,
the four binding fragment headers and the tail-reduce edit. A re-export
re-emits the per-variant files. It leaves the headers unreferenced until
the exporter reproduces the folds. The exporter follow-up has three
parts:
  - emit the fp32 output width as a compile-line specialization;
  - emit the kernel preamble and the binding blocks once per package;
  - stop writing the unread registry keys and the loader glue.
- **Declared deviations.** Commit 3 shifts the backtrace lines of the
three kept bindings by +18. The fp32 builds report the twin's file name.
Commit 5 moves 96 check sites into headers. Their backtrace names the
header, and the message texts are unchanged. The ten fp32 JIT library
names change, so a warm JIT workspace rebuilds those ten once.
- **Header digests.** No manifest digest covers the 5 new headers. The
manifest digests the sources handed to `nvcc`, and those sources
`#include` the headers. The build's dependency tracking covers the
headers.
- **Symbol-table masking.** Only the compiler-generated module id of
internal-linkage names is canonicalised. The host-object comparison
leaves out the compiler-numbered `.LC<n>` literal labels and nothing
else. Commit 5 moves `__FILE__` strings, which renumbers those labels.
- **Flag line.** The compile-only rows used the manifest-derived flag
line. The container that ran them did not capture the JIT build's
generated line. The GPU test rows built the libraries through the real
JIT path.
- **Coverage.** CI has no SM100 / SM103 / SM107 runner. The kernel paths
ran on B200 and GB300, as Validation describes. For R200, see its row.
The CUDA-hidden run and the H100 CI exercise the host paths: registry,
manifest, planner and standalone import.
- **Base.** This PR is published from `main` `8ec9464ce`. `main` at
publish time is `3f398977d`, which touched no file of this PR. The six
patches apply on it unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for float32 weight-gradient output in grouped GEMM,
alongside the existing bfloat16 output option.
* **Refactor**
* Consolidated shared CUDA support across grouped GEMM variants. Some
previously exposed launch-stage and module details are no longer
available.
* **Documentation**
* Updated grouped GEMM documentation to describe output-type
specialization and supported build configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6b38488](https://github.com/flashinfer-ai/flashinfer/commit/6b38488084e37a44e8e037d9be467739f64ac9b3)

- **作者**: eigen
- **时间**: 2026-10-23T19:21:05Z
- **提交信息**: deslop(cake_blackwell_softmax): drop 3 unreachable kernels, fold clones (#7122)

### [9143f50](https://github.com/flashinfer-ai/flashinfer/commit/9143f50102b0ed06cba7ed5b230dc7d73092d9dc)

- **作者**: eigen
- **时间**: 2026-10-23T19:17:03Z
- **提交信息**: deslop(sm110): fold the shared device, binding and KV-cache blocks into headers; drop dead loader glue (#7116)

## 📌 Description

### Summary

This PR is the round-2 deslop of the two SM110 (Jetson AGX Thor) decode
packages under `flashinfer/experimental/`. `sm110_xqa` holds the XQA
tree and decode routes in 43 kernel translation units and 43 bindings.
`sm110_gqa_decode` holds the GQA decode routes in 7 kernel units and 7
bindings. The Cake exporter generates both packages. Each program has
one kernel `.cu` and one tvm-ffi binding `.cu`. Each package has a
`build.json` manifest with the SHA-256 of every source, and a
`cake_jit.py` registry.

Every kernel and binding unit is a generated file. Commits 1-4 are hand
folds: they move text that the generated files shared into headers under
each package's `csrc/`. A re-export from the exporter may re-inline the
blocks and leave the headers unreferenced. The headers stand in until
the exporter emits these blocks itself. Each package README says so.

The six commits are mechanical:
- commit 1 folds the shared device ABI block into one header per
package;
- commit 2 folds the device helpers into one guarded header per package;
- commit 3 folds the binding helpers into one fragment header per
sequence;
- commit 4 folds the `KVCacheList` record into one header per KV-cache
layout;
- commit 5 drops unreferenced loader glue and two unused launch keys
from both `cake_jit.py`;
- commit 6 documents the new headers, corrects the manifest-checker
wording and drops one test guard.

The proof for each fold is preprocessed-text identity, plus SASS
identity for the kernels. Totals against `main` `562917330`: 115 files
changed (9 new headers, 106 edited files), +1,729 / -15,860. Part of
#6679.

### Changes

Base: `main` `562917330`. Head:
`4b9f819b94e42f928559230353a26357b7bd1e32` (6 commits). Reviewer Notes
give the `main` sha at publish time.

The per-commit counts overlap. Several commits edit the same files,
including the same `build.json` digest lines. So the per-commit counts
do not sum to the branch totals.

### Commit 1 (9243f585f) - fold the shared device ABI block into one
header per package (54 files, +210 / -1,700)

- **Shared block.** All 50 kernel units opened with the same 32-line
device ABI block. It holds these parts:
  - the fixed-width typedefs;
  - the `CakeTensorMap64` / `CUtensorMap` size and alignment asserts;
  - `<cuda.h>`, `<cuda_bf16.h>` and `<cuda_fp8.h>`;
  - `make_warp_uniform`.

A blank line and `#define CAKE_INF CUDART_INF_F` follow the block. The
block is byte-identical in all 50 units.
- **New headers.** The block moves into
`csrc/cake_sm110_xqa_device_abi.cuh` and
`csrc/cake_sm110_gqa_decode_device_abi.cuh`. Each header has 55 lines
and an include guard. Each unit includes its header at the block's
position. No other line of any unit changes.
- **Manifests.** Both `build.json` files carry the recomputed SHA-256 of
the 50 edited kernel sources. Every other manifest key is unchanged. The
headers are never manifest sources, and this holds for commits 1-4.
- **Why behaviour is preserved.** Nothing emitted precedes the block. No
block line reads a unit-specific macro. The define is a directive. The
proof has two parts. Each preprocessed unit must be identical once line
markers and blank lines are dropped. The SASS of every kernel must be
identical.

### Commit 2 (658f5ff69) - fold the device helpers into one guarded
header per package (54 files, +1,089 / -10,258)

- **Helper library.** After the ABI include, each kernel unit carried
its own selection of device helpers. These are mbarrier, tcgen05, TMA,
TMEM and f32x2 wrappers. The helpers come from a library of 32 distinct
helpers in xqa and 19 in gqa. A helper has the same text in every unit
that defines it. One global order fits every unit.
- **New headers.** The library moves, in that order, into
`csrc/cake_sm110_xqa_device_helpers.cuh` (366 lines) and
`csrc/cake_sm110_gqa_decode_device_helpers.cuh` (195 lines). A helper
that is not in every unit of its package sits behind `#if
defined(CAKE_<PKG>_NEED_<HELPER>)`. That covers 20 of 32 helpers in xqa
and 15 of 19 in gqa.
- **Units.** Each unit's helper region lies between `#include
<math_constants.h>` and `extern "C" {`. Each unit replaces that region
with two things:
- one `#define CAKE_<PKG>_NEED_<HELPER>` line for each helper it used
(5-11 per xqa unit, 0-14 per gqa unit, 428 selector lines in all);
  - one include of the header.
- **Why the guards.** A guard that is off emits nothing. So the header
contributes exactly the helpers that the unit defined before, in the
same order. The preprocessed text stays identical. A superset header
without guards would insert unused definitions into every unit. That
would change the preprocessed text. That option is listed under "Not in
this PR".
- **Why behaviour is preserved.** No helper line reads a unit macro. No
unit uses `__LINE__` or `__FILE__`. The proof is preprocessed-text
identity (line markers and blank lines dropped) and SASS identity of
every kernel.

### Commit 3 (44197f210) - fold the binding helpers into one fragment
header per sequence (54 files, +294 / -2,486)

- **Three sequences.** Every binding unit defines a block of host
helpers inside `namespace cake_binding_<kernel>`, right after
`KERNEL_NAME`. Three sequences of this block exist:
- the 40 xqa TMA tree bindings: 52 lines (CheckCuda, CheckCu, DataPtr,
CheckUnitInnerStride, NumelAbove, Extent, Stride, CakeRecord, PutField);
- the 3 xqa decode bindings: 49 lines (CheckCuda, CheckCu, DataPtr,
CheckUnitInnerStride, NumelAbove, NonZero, CMod, Extent, Stride);
- the 6 gqa TMA bindings: 35 lines (CheckCuda, CheckCu, DataPtr,
CheckUnitInnerStride, Extent, Stride).

Each helper reads `KERNEL_NAME` symbolically. So the block text is
identical across the bindings of one sequence.
- **New headers.** The three blocks move into
`csrc/cake_sm110_xqa_binding_helpers_tma_record.h` (72 lines),
`csrc/cake_sm110_xqa_binding_helpers_decode.h` (69) and
`csrc/cake_sm110_gqa_decode_binding_helpers_tma.h` (55). Each of the 49
bindings replaces its block with one `#include` at the block's first
line, inside the namespace. The headers have no include guard. Each one
is a fragment that is included once per unit, inside its namespace.
- **Kept.** The gqa `short` binding keeps its block (CheckCuda, DataPtr,
CheckRank, CheckUnitInnerStride). It is the only binding of its
sequence. Kernel units are untouched.
- **Declared deviation: backtrace file and line.** 248 `TVM_FFI_CHECK` /
`TVM_FFI_THROW` sites move into the headers. That is 5 per tree binding,
6 per decode binding and 5 per gqa TMA binding. When one of these checks
fails, the error's backtrace names the header's file and line, not the
binding's. The message texts are unchanged. No test asserts on a
backtrace. Every site after the include line moves up by exactly 51
lines (tree, both KV layouts), 48 (decode) or 34 (gqa TMA).
- **Why behaviour is preserved.** The preprocessed text of every edited
binding must equal its parent's, apart from those file and line
arguments. The gate accounts for every one of them. The host object's
exports (`run`, `build_cuda_version`) must be identical.

### Commit 4 (ac4f7f4c1) - fold the KVCacheList record into one header
per KV-cache layout (83 files, +242 / -1,360)

- **Shared block.** The 40 tree kernel units of `sm110_xqa` and their 40
bindings carry the same `KVCacheList` block. It holds three parts:
  - a `<stddef.h>` include, guarded for the non-RTC path;
  - the struct;
  - its size, alignment and offsetof static_asserts.

The three-field `contig` record takes 15 lines. The four-field `page128`
record takes 17. Each block is byte-identical between each kernel and
its binding in all 40 pairs, and across the 20 units of each layout.
- **New headers.** Each layout's block moves into its own header:
`csrc/cake_sm110_xqa_kv_cache_list_contig.h` (40 lines) or
`csrc/cake_sm110_xqa_kv_cache_list_page128.h` (42). The 80 units include
it at the block's position. The 3 decode units carry no such block and
are untouched. `sm110_gqa_decode` is untouched.
- **Why behaviour is preserved.** The block defines no macro, reads no
unit macro and holds no check site. `<stddef.h>` expands at the same
position on both sides. The proof is preprocessed-text identity for all
80 units and SASS identity for the 40 kernels. Each binding's own check
sites after the include move up by 14 (contig) or 16 (page128) lines.
Only the line number changes, not the file. The host exports must be
identical.

### Commit 5 (6be23aa44) - drop the unreferenced loader glue and two
unused launch keys (2 files, +0 / -177)

- **Removed names.** `sm110_xqa/cake_jit.py` loses 116 lines, and
`sm110_gqa_decode/cake_jit.py` loses 61. These go:
  - `sm_count`, `specs_for_arch` and `run_module` in both modules;
  - `_admits` and the `STAGES` constant in the gqa module;
  - their `__all__` entries (the private `_admits` has none);
  - `import tvm_ffi`, which only `run_module` used.

  The xqa `STAGES` stays, because its test pins it.
- **Removed launch keys.** Every `MODULES` record's `launch` dict also
carried `block` and `dynamic_smem_bytes`. That is 43 xqa records and 7
gqa records. Both keys are dropped from all 50 dicts. Nothing reads
them:
  - the tests read only `cluster`, `cooperative` and `use_pdl`;
  - the bindings hard-code the block and dynamic shared-memory sizes;
  - the manifest checker walks only `library` / `arches`.
- **Proof.** A whole-repository reference search covers every removed
name in word, string and getattr forms. It must find no reader outside
the removed definitions and `__all__`. Same-named symbols elsewhere
belong to other packages' own loaders. For each module, the parent's AST
is pruned of exactly the removed nodes and keys. The pruned AST must
equal the new module's AST. So every kept statement and the module
docstring are unchanged. So are the live loader path (`entry`,
`argument_list`, `load`, `library_name`, `select_record`) and every
record name and leaf.
- **Behaviour note.** An out-of-tree caller of `cake_jit.sm_count`,
`run_module`, `specs_for_arch`, `_admits` or the gqa `STAGES` would
break. No code in the repository uses them. Both `backend.py` modules
import `tvm_ffi` at module level, so import-time behaviour is unchanged.
The exporter writes these leaves, so a re-export re-emits them until the
exporter changes.

### Commit 6 (4b9f819b9) - document the folded headers and fix the
checker wording (3 files, +24 / -9)

- **README file tables.** Each package README's file table gains one row
per new header: 6 in xqa and 3 in gqa. Each row names the header's
content and the units that include it. Each README also gains one
paragraph. It says that the headers are a hand fold of blocks the
generated files shared. They stand in until the files are regenerated
from the exporter.
- **Checker command.** Both Validation sections named a manifest-checker
command that the checker rejects. The checker takes no positional
argument. `--in-tree` is a flag, and `--package <name>` selects a
package. The xqa README now reads `python
scripts/check_cake_build_manifests.py --in-tree --package sm110_xqa`.
The gqa README drops the command and says the package is not registered
with that checker yet. It also names the digest rule that `cake_build`
applies at JIT load: the SHA-256 of each listed source equals the
`build.json` value.
- **gqa "Edit the exporter" paragraph.** One clause said the checker
reads `cake_jit.py`. That was false for this package. The paragraph now
says that the package tests check `build.json` against the registry in
`cake_jit.py` and against the sources.
- **Test guard.** `tests/experimental/test_sm110_gqa_decode.py` loses a
three-line rglob guard at the end of
`test_registry_names_delivered_sources`. The guard asserted that no file
named `manifest.json`, `RESULTS.md`, `jit.py` or `prepared.py` exists
under the package. No such file exists. The test keeps its registry,
manifest and source-file assertions. The collected ids are unchanged: 38
in that file.

### Validation

All rows compare the base `562917330` with the branch head. Each arm
used the same absolute checkout path, and the tree was swapped between
arms. So line markers and `__FILE__` strings agree between arms.

The compiler rows use CUDA 13.4 (nvcc 13.4.92). They use the manifest's
own flag line for `sm_110a`, which is identical for all 50 libraries:
`-gencode=arch=compute_110a,code=sm_110a -std=c++17 -O3 -DNDEBUG
--compiler-options=-fPIC --expt-relaxed-constexpr -Xfatbin=-compress-all
--compress-mode=size -static-global-template-stub=false
--use_fast_math`.

- Kernel preprocessed text, 50 kernel units. Both passes of `nvcc -E`
ran: the device pass with `__CUDA_ARCH__` = 1100, and the host pass. The
comparison drops `# <n> "<file>"` line markers and whitespace-only
lines. Nothing else is masked: 50/50 (both -E passes identical after N0)
- Binding preprocessed text, 50 binding units, both passes, with the
same comparison. It adds the declared accounting of the check sites that
commit 3 moves. Every `TVMFFIBacktrace("<file>", <line>` pair is
classified into one of two kinds:
  - a site moved to a header, at a fixed offset;
- the binding's own site, shifted by exactly 51 / 48 / 34 lines under
commit 3 and by 14 / 16 more under commit 4.

The gate expects 248 moved sites. The gqa `short` binding is untouched,
and file hashes verify it without a compile: 50/50 (N0 + F: 248 moved
backtrace sites, expected 248)
- SASS, 50 kernels. `nvcc -cubin` builds each kernel unit. `cuobjdump
-sass` output is compared per function, after masking instruction
addresses and encodings. The `cuobjdump -symbols` function lists must be
identical, with exactly one kernel per unit: 50/50 (CUDA 13.4)
- Host objects, 50 objects. `nvcc -c` builds each binding unit. The
export set {`__tvm_ffi_run`, `__tvm_ffi_build_cuda_version`} must be
identical. `nm -u` must name `kernel_<library>`. The host object must
hold no device function: 50/50 (exports + symbol tables identical)
- Manifest digests. The SHA-256 of every source listed in both
`build.json` files (86 xqa, 14 gqa) is recomputed from the tree, at the
base and at the head. Each manifest diff may touch only the SHA-256
values of the edited sources. `closure_sha256`, `sources` and the flags
must be unchanged. The canonical JSON must round-trip: 0 mismatches on
both packages of both trees; 99 source digests changed, no header in
sources
- Manifest checker. The upstream `scripts/check_cake_build_manifests.py
--in-tree --package sm110_xqa` runs on both trees. A replica of its rule
runs over both packages on both trees, because `sm110_gqa_decode` is not
registered with the upstream checker: M1 exit 0 both trees; M2 findings
identical to the base (1), INFO +9 new headers
- New headers. The 9 headers are recorded by path, line count and
SHA-256. By design, no manifest digest covers them, because the manifest
digests the sources handed to nvcc. Record: 9 new headers recorded
(sha256 + line count)
- Reference search on the head. A whole-repository word / string /
getattr search covers every name that commit 5 removes, and the two
launch keys: 5/5 (STAGES, _admits, run_module, sm_count, specs_for_arch:
0 hits)
- Apply replay. Each commit's apply script re-runs in order on a fresh
copy of the base. Each resulting tree must equal that commit's tree byte
for byte. This shows that text matching alone reproduces the folds: 6
unit scripts replayed on the base (U1 U2 U3 U4 U5 U6); tree identical to
the commits
- Tests on a Jetson AGX Thor (SM110, CC 11.0) with CUDA 13.4, the five
test files. The base tree ran first, then the branch tree. Each arm ran
in a fresh JIT workspace, and the 50 module directories were asserted
absent before each arm. Every id must have the same outcome on both
arms, including skip reasons. The files collect 625 ids (305 + 143 + 38
+ 63 + 76). 435 of them run only on SM110. 35 ids skip by design on both
arms: the E4M3 KV cases that the tests route to the pair kernels: 625
ids on Jetson AGX Thor (SM110) (driver 595.78): 590 passed / 35 skipped
by design, per-id identical on both trees; fresh JIT workspace per arm
- Tests with CUDA hidden on a CPU node, the same five files, both trees.
Per-id outcomes must be identical. The expected split is 160 passed /
465 skipped: 625 ids: 160 passed / 465 skipped (CUDA hidden), per-id
identical on both trees
- GitHub CI on H100 runs the same five files. On a non-SM110 GPU, the
SM110-only ids skip by their fixture. So 190 ids are expected to pass
and 435 to skip.
- CPU checks on one node, both trees, 19 checks:
  - chain shape and totals;
  - `git diff --check`;
  - scope of the touched paths;
  - the shared files that this PR must not touch are untouched;
  - `py_compile`;
  - ruff on both `cake_jit.py`;
  - collect-only parity (625 ids);
  - the CUDA-hidden tests;
- pre-commit on the changed files, and with `--all-files` on both
checkouts;
  - the repository's mypy hook, with no new finding;
  - the reference search;
  - the upstream and replica manifest checks;
  - the header record;
  - the digest rows;
  - the apply replay;
  - the public-text scan;
  - the commit-message form;
  - a clean worktree.

  Result: 19/19
- Not run (environment): none (0 rows: every planned row ran)

**Not run.** These are left out by design:
- **Benchmark.** The PR changes no kernel code, and the SASS row
compares every kernel.
- **Cross-tree tensor comparison.** The identity criterion is identical
per-test outcomes, plus identical SASS, preprocessed text and host
exports.

### Not in this PR

- **Regeneration from the exporter.** This has two parts. The first is
templating the per-ratio and per-precision units (head-group size,
paging, E4M3, cluster parity). The second is emitting the ABI block, the
helper library, the KV-cache record and the binding helper fragments
once per package at export time. This PR's headers are the hand-fold
stand-in until then.
- **A superset device-helper header without the `NEED` guards** (about
500 lines fewer). It inserts unused definitions into every unit and
changes the preprocessed text. It needs a different proof form: SASS
identity alone.
- **Fragment headers for the 19 distinct TMA-descriptor encoder bodies
in the bindings** (about 2,100 lines). The exporter's parameterisation
solves this better than 19 small headers.
- **Dropping the whole `launch` leaf and `kernel_symbol` from the
registries.** 9 test lines pin them.
- **Hoisting per-call host work.** This covers TMA descriptor encodes at
prepare time and the per-call device guards. It is a behaviour and
performance change that needs measurements on SM110.
- **Strided inputs.** The bindings reject non-contiguous tensors today.
Accepting them is a behaviour change.
- **Shared root files that this PR never edits:**
  - `pyproject.toml` (the gqa wheel's package data lacks `build.json`);
- `scripts/check_cake_build_manifests.py` (`sm110_gqa_decode` is not
registered);
  - `.clang-format-ignore` (it lists a vanished path);
  - `.pre-commit-config.yaml`;
  - `tests/test_helpers/cake_package.py`;
  - `flashinfer/decode.py` and `flashinfer/__init__.py`;
  - `flashinfer/jit/**`;
- both `cake_build.py`, both `csrc/cake_ffi_checks.h` and both
`csrc/.clang-format`.

Three of them have real defects: the gqa package data, the checker
registration and the stale ignore path. They are for a separate small
PR.
- **Regenerating `closure_sha256`.** Its derivation is not in the
repository. The value is unchanged, so the JIT module names are
unchanged too.

## 🔍 Related Issues

Tracking issue: #6679

Part of #6679

#6679 is the round-2 deslop family issue. This PR covers its mechanical
part for `sm110_xqa` and `sm110_gqa_decode`. The open items are listed
under "Not in this PR".

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

The hooks ran on the changed files and with `--all-files` on both
checkouts (base and branch). The repository's mypy hook ran on both
trees. The CPU checks row in Validation gives the results.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

One test changes: commit 6 drops a three-line rglob guard from
`tests/experimental/test_sm110_gqa_decode.py`. No test is added or
removed, and the collected ids are unchanged. The five test files ran on
a Jetson AGX Thor, and with CUDA hidden on a CPU node (see Validation).

CI targets: the five files in the experimental-tests block below.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #6679
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/sm110_xqa/test_sm110_xqa.py
tests/experimental/test_cake_sm110_xqa.py
tests/experimental/test_sm110_gqa_decode.py
tests/experimental/test_sm110_gqa_decode_prepared.py
tests/experimental/test_cake_sm110_gqa_decode.py
```

Both packages are experimental and live under
`flashinfer/experimental/`. Their tests live under
`tests/experimental/`. These five files are the CI run targets. This PR
edits only files in the two packages and one test file. It changes no
core file and no public API. The runnable examples are the two
benchmarks, `benchmarks/bench_sm110_xqa.py` and
`benchmarks/bench_sm110_gqa_decode.py`, which this PR does not change.
Neither package is registered in `flashinfer/aot.py`, and neither is
reachable from `backend="auto"`: their entry points are the
`@flashinfer_experimental_api` functions in `flashinfer/decode.py` and
`flashinfer/sm110_xqa.py`, which this PR does not change.

## Reviewer Notes

- **Hand fold.** Commits 1-4 fold text from exporter-generated files
into headers by hand. A re-export may re-inline the blocks and leave the
headers orphaned. The exporter follow-up under "Not in this PR" is the
durable solution.
- **Declared deviation (commit 3).** For 248 moved check sites, the
backtrace names the header's file and line instead of the binding's. The
message texts are unchanged.
- **Header digests.** No digest verifies the 9 new headers. The manifest
digests the sources handed to nvcc, and those sources `#include` the
headers.
- **Coverage.** The CUDA-hidden run and the H100 CI exercise the host
paths: registry, manifest and prepared routes. The kernel paths run only
on SM110. They ran on a Jetson AGX Thor, as Validation describes.
- **Base.** This PR is published from `main` `562917330`. `main` at
publish time is `8ec9464ce`. Since the base it touched no file of this
PR and no file of the two packages. The six patches apply on it
unchanged (identical range-diff, clean merge).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Consolidated shared support for experimental SM110 GQA decode and XQA
kernels. Kernel behavior and entry points remain unchanged.
* Updated experimental launch metadata; some previously available launch
utilities are no longer provided.

* **Documentation**
* Updated package file listings and build-validation guidance for the
experimental SM110 packages.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0e832d0](https://github.com/flashinfer-ai/flashinfer/commit/0e832d0636256d346fff0110f38117290b7f1397)

- **作者**: eigen
- **时间**: 2026-10-23T19:15:06Z
- **提交信息**: feat(cake_tp_moe_finalize_rmsnorm): add optimized backend (#7120)

### [85e886c](https://github.com/flashinfer-ai/flashinfer/commit/85e886c875b123bb5f4eaa78b0515f1d0f98392e)

- **作者**: eigen
- **时间**: 2026-10-23T19:13:46Z
- **提交信息**: perf(cake_deepgemm_mega_mhc): evict-first residual stream and atomic tail flag for the hidden-4096 BF16 program on SM107 (#7113)

### [787132c](https://github.com/flashinfer-ai/flashinfer/commit/787132c8353928266a7261ab68aa9045ba2252e0)

- **作者**: eigen
- **时间**: 2026-10-23T19:12:02Z
- **提交信息**: feat(cake_muse_spark_norm): add cake_muse_spark_norm_backend for three gated RMSNorm ops (#7119)

This PR adds `cake_muse_spark_norm_backend`, a Cake backend for three
fused RMSNorm ops that FlashInfer already exposes:
`flashinfer.norm.gated_residual_rmsnorm`,
`flashinfer.norm.gated_residual_next_rmsnorm` and
`flashinfer.norm.rmsnorm_sigmoid_gate`. `gated_residual_rmsnorm` uses
hidden 8192, BF16 `branch`, FP32 `residual` / `alpha` / `beta` / `out`,
and runtime `eps` and `gain_center`. It has two modes over M rows: mode
0 has no weight, and mode 1 applies a weight before the norm.
`gated_residual_next_rmsnorm` uses hidden 8192, FP32 `residual_out` and
BF16 `ffn_input`. It is timed in two forms over M rows: V1 uses an alpha
tensor and `post_weight`, and V2 uses scalar alpha 1.0 without
`post_weight`. `rmsnorm_sigmoid_gate` normalizes per-(token, head) rows
of 64 BF16 values in place and reads the gate from a strided view of the
projection. It is timed at 16, 32 and 128 heads over T tokens. No
earlier Cake version of these kernels is shipped, so the baseline is
FlashInfer's existing CuTe DSL kernels (PR #6544). Speedup = baseline µs
/ Cake µs, and a value above 1 means Cake is faster.

**`gated_residual_rmsnorm`, NVIDIA GB300 (`sm_103a`), CUDA 13.0.** M ≤
128: CUDA graph of 32 launches with PDL on both sides, per-launch; M ≥
256: isolated launch, cold L2.

| mode | M | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 0 | 1 | 1.35 | 1.09 | 1.234 |
| 0 | 2 | 1.41 | 1.16 | 1.220 |
| 0 | 4 | 1.42 | 1.16 | 1.221 |
| 0 | 8 | 1.42 | 1.22 | 1.158 |
| 0 | 16 | 1.52 | 1.29 | 1.182 |
| 0 | 32 | 1.61 | 1.35 | 1.186 |
| 0 | 64 | 1.93 | 1.80 | 1.071 |
| 0 | 128 | 2.27 | 2.24 | 1.014 |
| 0 | 256 | 5.30 | 5.52 | 0.959 |
| 0 | 512 | 8.45 | 8.86 | 0.953 |
| 0 | 1024 | 14.88 | 15.52 | 0.959 |
| 0 | 2048 | 27.42 | 27.18 | 1.009 |
| 0 | 4096 | 52.82 | 51.30 | 1.030 |
| 0 | 8192 | 104.03 | 99.10 | 1.050 |
| 0 | 16384 | 205.92 | 193.70 | 1.063 |
| 1 | 1 | 1.42 | 1.35 | 1.049 |
| 1 | 2 | 1.54 | 1.48 | 1.044 |
| 1 | 4 | 1.54 | 1.42 | 1.089 |
| 1 | 8 | 1.54 | 1.48 | 1.044 |
| 1 | 16 | 1.65 | 1.59 | 1.039 |
| 1 | 32 | 1.73 | 1.67 | 1.039 |
| 1 | 64 | 2.18 | 2.12 | 1.031 |
| 1 | 128 | 2.44 | 2.24 | 1.086 |
| 1 | 256 | 6.02 | 5.63 | 1.068 |
| 1 | 512 | 9.86 | 8.99 | 1.096 |
| 1 | 1024 | 16.93 | 15.97 | 1.060 |
| 1 | 2048 | 30.06 | 27.97 | 1.075 |
| 1 | 4096 | 56.13 | 52.08 | 1.078 |
| 1 | 8192 | 110.53 | 101.02 | 1.094 |
| 1 | 16384 | 218.08 | 196.70 | 1.109 |

**`gated_residual_rmsnorm`, NVIDIA B200 (`sm_100a`), CUDA 13.0.** M ≤
128: CUDA graph of 32 launches with PDL on both sides, per-launch; M ≥
256: isolated launch, cold L2.

| mode | M | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 0 | 1 | 1.48 | 1.22 | 1.209 |
| 0 | 2 | 1.48 | 1.22 | 1.210 |
| 0 | 4 | 1.48 | 1.22 | 1.210 |
| 0 | 8 | 1.48 | 1.28 | 1.157 |
| 0 | 16 | 1.54 | 1.29 | 1.199 |
| 0 | 32 | 1.67 | 1.47 | 1.132 |
| 0 | 64 | 1.99 | 1.86 | 1.067 |
| 0 | 128 | 2.35 | 2.24 | 1.045 |
| 0 | 256 | 5.60 | 5.41 | 1.036 |
| 0 | 512 | 8.86 | 8.98 | 0.988 |
| 0 | 1024 | 15.49 | 15.95 | 0.971 |
| 0 | 2048 | 28.45 | 28.16 | 1.010 |
| 0 | 4096 | 54.53 | 52.75 | 1.034 |
| 0 | 8192 | 108.42 | 101.79 | 1.065 |
| 0 | 16384 | 215.23 | 198.99 | 1.082 |
| 1 | 1 | 1.56 | 1.48 | 1.053 |
| 1 | 2 | 1.55 | 1.48 | 1.053 |
| 1 | 4 | 1.60 | 1.54 | 1.043 |
| 1 | 8 | 1.60 | 1.54 | 1.042 |
| 1 | 16 | 1.67 | 1.60 | 1.040 |
| 1 | 32 | 1.73 | 1.68 | 1.030 |
| 1 | 64 | 2.25 | 2.18 | 1.033 |
| 1 | 128 | 2.51 | 2.37 | 1.060 |
| 1 | 256 | 6.37 | 5.63 | 1.131 |
| 1 | 512 | 10.30 | 9.38 | 1.099 |
| 1 | 1024 | 17.55 | 16.35 | 1.073 |
| 1 | 2048 | 31.38 | 28.80 | 1.089 |
| 1 | 4096 | 59.46 | 54.54 | 1.090 |
| 1 | 8192 | 116.89 | 104.22 | 1.122 |
| 1 | 16384 | 232.32 | 203.36 | 1.142 |

**`gated_residual_next_rmsnorm`, NVIDIA GB300 (`sm_103a`), CUDA 13.0.**
Isolated launch, cold L2.

| variant | M | baseline µs | Cake µs | speedup |
|---|---:|---:|---:|---:|
| V1 | 1 | 2.98 | 2.66 | 1.120 |
| V1 | 8 | 3.14 | 2.80 | 1.120 |
| V1 | 16 | 3.35 | 2.94 | 1.142 |
| V1 | 32 | 3.63 | 3.17 | 1.146 |
| V1 | 64 | 4.28 | 3.78 | 1.133 |
| V1 | 128 | 5.70 | 4.86 | 1.175 |
| V1 | 256 | 9.24 | 6.86 | 1.346 |
| V1 | 512 | 16.23 | 10.82 | 1.500 |
| V1 | 1024 | 29.05 | 17.96 | 1.617 |
| V1 | 2048 | 54.45 | 34.61 | 1.573 |
| V1 | 4096 | 104.75 | 63.54 | 1.649 |
| V1 | 8192 | 204.43 | 121.74 | 1.679 |
| V1 | 16384 | 403.39 | 237.02 | 1.702 |
| V2 | 1 | 2.89 | 2.59 | 1.114 |
| V2 | 8 | 3.12 | 2.77 | 1.127 |
| V2 | 16 | 3.30 | 2.91 | 1.132 |
| V2 | 32 | 3.52 | 3.09 | 1.140 |
| V2 | 64 | 4.22 | 3.70 | 1.140 |
| V2 | 128 | 5.50 | 4.82 | 1.139 |
| V2 | 256 | 9.09 | 6.34 | 1.433 |
| V2 | 512 | 15.89 | 10.13 | 1.569 |
| V2 | 1024 | 28.14 | 17.66 | 1.594 |
| V2 | 2048 | 53.50 | 32.70 | 1.636 |
| V2 | 4096 | 101.46 | 61.90 | 1.639 |
| V2 | 8192 | 197.80 | 120.43 | 1.642 |
| V2 | 16384 | 390.75 | 238.12 | 1.641 |

**`gated_residual_next_rmsnorm`, NVIDIA B200 (`sm_100a`), CUDA 13.0.**
Isolated launch, cold L2.

| variant | M | baseline µs | Cake µs | speedup |
|---|---:|---:|---:|---:|
| V1 | 1 | 3.26 | 2.87 | 1.136 |
| V1 | 8 | 3.30 | 2.98 | 1.108 |
| V1 | 16 | 3.51 | 3.12 | 1.126 |
| V1 | 32 | 3.76 | 3.38 | 1.111 |
| V1 | 64 | 4.45 | 3.97 | 1.121 |
| V1 | 128 | 5.82 | 5.01 | 1.161 |
| V1 | 256 | 9.66 | 7.33 | 1.319 |
| V1 | 512 | 17.17 | 11.43 | 1.502 |
| V1 | 1024 | 31.58 | 19.71 | 1.602 |
| V1 | 2048 | 58.89 | 34.80 | 1.692 |
| V1 | 4096 | 113.67 | 65.06 | 1.747 |
| V1 | 8192 | 222.17 | 124.18 | 1.789 |
| V1 | 16384 | 438.82 | 241.37 | 1.818 |
| V2 | 1 | 3.21 | 2.76 | 1.162 |
| V2 | 8 | 3.23 | 2.80 | 1.154 |
| V2 | 16 | 3.46 | 3.08 | 1.122 |
| V2 | 32 | 3.68 | 3.33 | 1.106 |
| V2 | 64 | 4.35 | 3.87 | 1.124 |
| V2 | 128 | 5.63 | 4.99 | 1.128 |
| V2 | 256 | 9.42 | 6.93 | 1.359 |
| V2 | 512 | 16.74 | 10.74 | 1.560 |
| V2 | 1024 | 30.72 | 18.98 | 1.618 |
| V2 | 2048 | 57.21 | 33.35 | 1.715 |
| V2 | 4096 | 109.94 | 63.47 | 1.732 |
| V2 | 8192 | 214.66 | 122.45 | 1.753 |
| V2 | 16384 | 424.75 | 241.91 | 1.756 |

**`rmsnorm_sigmoid_gate`, NVIDIA GB300 (`sm_103a`), CUDA 13.0.**
Isolated launch, cold L2.

| heads | T | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 128 | 1 | 1.66 | 1.67 | 0.991 |
| 128 | 2 | 2.18 | 1.75 | 1.246 |
| 128 | 3 | 1.85 | 1.73 | 1.069 |
| 128 | 8 | 1.91 | 1.93 | 0.990 |
| 128 | 64 | 2.43 | 2.46 | 0.988 |
| 128 | 256 | 4.04 | 4.13 | 0.977 |
| 128 | 1024 | 9.70 | 9.87 | 0.983 |
| 128 | 4096 | 32.17 | 30.98 | 1.038 |
| 128 | 16384 | 118.72 | 114.07 | 1.041 |
| 32 | 1 | 1.67 | 1.55 | 1.077 |
| 32 | 2 | 2.17 | 1.76 | 1.233 |
| 32 | 8 | 2.23 | 1.78 | 1.253 |
| 32 | 9 | 1.81 | 1.73 | 1.046 |
| 32 | 17 | 1.87 | 1.80 | 1.039 |
| 32 | 64 | 1.96 | 2.00 | 0.982 |
| 32 | 256 | 2.42 | 2.45 | 0.988 |
| 32 | 257 | 2.42 | 2.44 | 0.992 |
| 32 | 1024 | 4.02 | 4.10 | 0.980 |
| 32 | 4096 | 9.74 | 9.92 | 0.982 |
| 32 | 16384 | 32.19 | 31.05 | 1.037 |
| 16 | 1 | 1.67 | 1.48 | 1.129 |
| 16 | 8 | 2.19 | 1.74 | 1.259 |
| 16 | 16 | 2.21 | 1.75 | 1.259 |
| 16 | 17 | 2.42 | 1.76 | 1.375 |
| 16 | 64 | 2.50 | 1.92 | 1.301 |
| 16 | 256 | 2.73 | 2.18 | 1.250 |
| 16 | 1024 | 3.44 | 3.08 | 1.117 |
| 16 | 4096 | 6.92 | 6.06 | 1.142 |
| 16 | 16384 | 20.20 | 17.20 | 1.174 |

**`rmsnorm_sigmoid_gate`, NVIDIA B200 (`sm_100a`), CUDA 13.0.** Isolated
launch, cold L2.

| heads | T | baseline µs | Cake µs | speedup |
|---:|---:|---:|---:|---:|
| 128 | 1 | 1.70 | 1.72 | 0.988 |
| 128 | 2 | 2.24 | 1.93 | 1.161 |
| 128 | 3 | 1.93 | 1.92 | 1.008 |
| 128 | 8 | 1.97 | 1.99 | 0.990 |
| 128 | 64 | 2.55 | 2.59 | 0.985 |
| 128 | 256 | 4.18 | 4.26 | 0.981 |
| 128 | 1024 | 10.02 | 10.09 | 0.993 |
| 128 | 4096 | 33.12 | 31.66 | 1.046 |
| 128 | 16384 | 121.54 | 115.90 | 1.049 |
| 32 | 1 | 1.71 | 1.60 | 1.062 |
| 32 | 2 | 2.22 | 1.81 | 1.230 |
| 32 | 8 | 2.26 | 1.81 | 1.252 |
| 32 | 9 | 1.91 | 1.82 | 1.049 |
| 32 | 17 | 1.95 | 1.95 | 1.000 |
| 32 | 64 | 2.05 | 2.08 | 0.986 |
| 32 | 256 | 2.52 | 2.56 | 0.984 |
| 32 | 257 | 2.52 | 2.56 | 0.984 |
| 32 | 1024 | 4.16 | 4.23 | 0.983 |
| 32 | 4096 | 10.14 | 10.28 | 0.986 |
| 32 | 16384 | 33.30 | 31.91 | 1.044 |
| 16 | 1 | 1.73 | 1.52 | 1.138 |
| 16 | 8 | 2.24 | 1.79 | 1.255 |
| 16 | 16 | 2.29 | 1.83 | 1.249 |
| 16 | 17 | 2.47 | 1.89 | 1.307 |
| 16 | 64 | 2.60 | 2.00 | 1.303 |
| 16 | 256 | 2.84 | 2.27 | 1.251 |
| 16 | 1024 | 3.60 | 3.20 | 1.125 |
| 16 | 4096 | 7.26 | 6.36 | 1.142 |
| 16 | 16384 | 21.54 | 17.80 | 1.210 |

The package also ships both `gated_residual_rmsnorm` modes in non-PDL
and PDL builds (the PDL build serves `enable_pdl`), uses the same
programs for the V3 form of `gated_residual_next_rmsnorm` (scalar alpha
0.5 with `post_weight`) and for its V4 form (alpha tensor without
`post_weight`, run by the V1 program with a zero `post_weight`), and
covers `rmsnorm_sigmoid_gate` at 16, 32 and 128 heads with tail-free,
token-cluster, head-block-cluster and head-major programs; the family
ships on `sm_100a` and `sm_103a`, and the `sm_107a` entries in the
kernel sources are unmeasured and not shipped in this package.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added the Cake backend for gated residual next-RMSNorm, with automatic
backend selection and options to explicitly choose Cake or CuTe.
  * Added Cake normalization operations for gated RMSNorm.
* Added support and warm-up queries to help check whether a device and
operation variant are available.
* **Bug Fixes**
* Added input validation and clearer errors for unsupported devices,
unavailable routes, and invalid inputs.
  * Empty batches now return without launching a kernel.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ddc9524](https://github.com/flashinfer-ai/flashinfer/commit/ddc9524d9f4d222acb8361ab584c2dc9cf23ca42)

- **作者**: eigen
- **时间**: 2026-10-23T19:10:36Z
- **提交信息**: perf(cake_kda): reuse the forward's carry plane in the context-parallel saved-context backward (#7117)

The Cake packed KDA kernel family, a chunked training backend for
documents packed into one sequence, has two variants: a single-device
variant, and a context-parallel (KCP) variant that splits the sequence
over the ranks of a distributed process group, passes the recurrent
state across ranks through affine state summaries, supports contiguous,
zigzag and per-document zigzag + ragged partition layouts as well as
saved-context and checkpoint-replay backward, and comes with the halo
variant of the causal conv1d + SiLU training backend. This PR makes the
saved-context backward of the context-parallel variant cheaper: on ranks
with parallel degree P > 1, the forward now keeps its carry plane (the
per-segment FP32 carry states, 12-80 MiB per rank for the configurations
in the table) in the saved set, and the backward binds that plane
read-only instead of rebuilding it, which skips its per-segment state
re-walk kernel and carry merge launches. Kernels, the P = 1 path and the
checkpoint-replay path are unchanged and results are bitwise identical
to the previous version; the forward's steady peak memory rises by the
kept plane while the backward's does not. The speedup over the previous
Cake version of the same kernels as merged in PR #7097, measured with
the same protocol, ranges from 0.9294x to 1.0397x in session 1 and from
0.9950x to 1.0387x in session 2: 34 of 144 rows are faster by more than
2 % in both sessions, 101 of 144 stay within 0.98-1.02 in both, no row
is slower by more than 2 % in both, and the remaining rows sit in
different bands in the two sessions. The skipped work is all in the
backward, which only B3 includes: B3 ranges from 0.9950x to 1.0387x
across both sessions, while B1, the forward alone, ranges from 0.9294x
to 1.0397x, with both extremes coming from session 1.

Latency in ms, NVIDIA GB300 (sm_103a), CUDA 13.0, driver 580.159.03, H =
64 heads, median over steady iterations of the slowest rank, two
sessions s1 / s2 on different nodes; CP2 / CP4 on one node, CP8 on two
nodes, CP16 on four nodes of one NVL72 domain; B1 = module forward, B3 =
forward + checkpoint replay + backward; previous version = the same
kernels as merged in PR #7097, measured with the same protocol in the
same sessions as an interleaved arm.

| pack | CP | layout | boundary | previous version ms (s1 / s2) | this
PR ms (s1 / s2) | speedup vs previous version (s1 / s2) |
|---|---|---|---|---|---|---|
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B1 = forward | 15.968 /
15.945 | 15.925 / 15.923 | 1.0027 / 1.0014 |
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 66.871 / 66.863 | 65.338 / 65.288 | 1.0235 / 1.0241
|
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B1 = forward | 16.151 /
16.152 | 16.150 / 16.161 | 1.0001 / 0.9994 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 67.387 / 67.435 | 65.889 / 65.942 | 1.0227 / 1.0226
|
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.203 / 16.228 | 16.202 / 16.227 | 1.0001 / 1.0001 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 67.295 / 67.283 | 66.015 /
66.070 | 1.0194 / 1.0184 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B1 = forward | 14.456 /
14.444 | 14.463 / 14.445 | 0.9995 / 0.9999 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 60.204 / 60.213 | 58.919 / 58.948 | 1.0218 / 1.0215
|
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B1 = forward | 15.278 /
15.281 | 15.276 / 15.272 | 1.0001 / 1.0006 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.115 / 63.099 | 61.520 / 61.515 | 1.0259 / 1.0257
|
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 14.973 / 14.988 | 14.989 / 14.980 | 0.9989 / 1.0005 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 61.993 / 62.010 | 60.827 /
60.823 | 1.0192 / 1.0195 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B1 = forward | 16.574 /
16.571 | 16.533 / 16.528 | 1.0025 / 1.0026 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 69.563 / 69.523 | 67.942 / 67.912 | 1.0239 / 1.0237
|
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B1 = forward | 16.408 /
16.410 | 16.411 / 16.419 | 0.9998 / 0.9995 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 68.891 / 68.901 | 67.577 / 67.583 | 1.0194 / 1.0195
|
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 17.256 / 17.249 | 17.247 / 17.247 | 1.0005 / 1.0001 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 71.200 / 71.236 | 69.850 /
69.915 | 1.0193 / 1.0189 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B1 = forward | 15.080 /
15.066 | 15.087 / 15.069 | 0.9995 / 0.9998 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 63.491 / 63.470 | 62.212 / 62.263 | 1.0206 / 1.0194
|
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B1 = forward | 15.215 /
15.214 | 15.205 / 15.204 | 1.0007 / 1.0007 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.557 / 63.571 | 62.394 / 62.364 | 1.0186 / 1.0194
|
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.875 / 15.884 | 15.880 / 15.905 | 0.9997 / 0.9987 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 65.797 / 65.806 | 64.498 /
64.514 | 1.0201 / 1.0200 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B1 = forward | 16.157 /
16.167 | 16.113 / 16.117 | 1.0027 / 1.0031 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 67.496 / 67.492 | 66.096 / 66.142 | 1.0212 / 1.0204
|
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B1 = forward | 16.071 /
16.079 | 16.062 / 16.089 | 1.0006 / 0.9994 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 67.247 / 67.277 | 66.047 / 66.044 | 1.0182 / 1.0187
|
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.601 / 16.616 | 16.613 / 16.614 | 0.9993 / 1.0001 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 68.950 / 68.996 | 67.596 /
67.676 | 1.0200 / 1.0195 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B1 = forward | 16.167 /
16.145 | 16.144 / 16.161 | 1.0014 / 0.9990 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 67.029 / 67.091 | 65.592 / 65.691 | 1.0219 / 1.0213
|
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B1 = forward | 16.423 /
16.435 | 16.423 / 16.447 | 1.0000 / 0.9993 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 68.214 / 68.164 | 66.687 / 66.649 | 1.0229 / 1.0227
|
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.930 / 16.928 | 16.916 / 16.925 | 1.0008 / 1.0002 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 69.925 / 69.910 | 68.619 /
68.621 | 1.0190 / 1.0188 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B1 = forward | 8.282 /
8.265 | 8.240 / 8.242 | 1.0051 / 1.0028 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.272 / 34.210 | 33.375 / 33.349 | 1.0269 / 1.0258
|
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B1 = forward | 8.510 / 8.502
| 8.558 / 8.511 | 0.9944 / 0.9989 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.948 / 34.892 | 34.152 / 34.071 | 1.0233 / 1.0241
|
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.377 / 8.401 | 8.328 / 8.352 | 1.0059 / 1.0059 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.878 / 33.888 | 33.833 /
33.829 | 1.0013 / 1.0017 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B1 = forward | 7.658 /
7.621 | 7.656 / 7.627 | 1.0003 / 0.9992 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 31.182 / 31.160 | 30.452 / 30.446 | 1.0240 / 1.0235
|
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B1 = forward | 7.870 / 7.862
| 7.863 / 7.871 | 1.0009 / 0.9989 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 32.090 / 32.100 | 31.301 / 31.293 | 1.0252 / 1.0258
|
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 7.780 / 7.790 | 7.786 / 7.770 | 0.9992 / 1.0026 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 31.263 / 31.233 | 31.261 /
31.216 | 1.0001 / 1.0005 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B1 = forward | 8.686 /
8.678 | 8.637 / 8.632 | 1.0057 / 1.0053 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 35.822 / 35.844 | 34.976 / 34.967 | 1.0242 / 1.0251
|
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B1 = forward | 8.923 / 8.912
| 8.928 / 8.906 | 0.9994 / 1.0007 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 36.578 / 36.570 | 35.683 / 35.687 | 1.0251 / 1.0247
|
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.796 / 8.801 | 8.794 / 8.806 | 1.0002 / 0.9994 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.644 / 35.614 | 35.628 /
35.631 | 1.0004 / 0.9995 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B1 = forward | 8.132 /
8.127 | 8.131 / 8.131 | 1.0001 / 0.9995 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.343 / 33.276 | 32.554 / 32.466 | 1.0242 / 1.0249
|
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B1 = forward | 8.262 / 8.268
| 8.231 / 8.223 | 1.0038 / 1.0055 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 33.841 / 33.803 | 32.941 / 32.941 | 1.0273 / 1.0262
|
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.354 / 8.366 | 8.344 / 8.353 | 1.0012 / 1.0016 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.040 / 34.029 | 33.374 /
33.341 | 1.0200 / 1.0206 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B1 = forward | 8.475 /
8.457 | 8.426 / 8.420 | 1.0058 / 1.0044 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.945 / 34.922 | 34.095 / 34.073 | 1.0249 / 1.0249
|
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B1 = forward | 8.742 / 8.718
| 8.739 / 8.734 | 1.0003 / 0.9982 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 35.834 / 35.839 | 34.991 / 34.975 | 1.0241 / 1.0247
|
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.648 / 8.622 | 8.635 / 8.606 | 1.0015 / 1.0019 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.834 / 34.813 | 34.841 /
34.804 | 0.9998 / 1.0003 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B1 = forward | 8.316 /
8.319 | 8.319 / 8.321 | 0.9996 / 0.9998 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.344 / 34.317 | 33.534 / 33.479 | 1.0242 / 1.0250
|
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B1 = forward | 8.489 / 8.484
| 8.497 / 8.484 | 0.9991 / 1.0000 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.816 / 34.824 | 34.021 / 33.995 | 1.0234 / 1.0244
|
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.773 / 8.780 | 8.764 / 8.794 | 1.0010 / 0.9984 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.607 / 35.616 | 34.992 /
34.957 | 1.0176 / 1.0189 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B1 = forward | 4.623 /
4.627 | 4.569 / 4.561 | 1.0118 / 1.0145 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.453 / 18.458 | 17.865 / 17.847 | 1.0329 / 1.0342
|
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B1 = forward | 4.568 / 4.575
| 4.915 / 4.564 | 0.9294 / 1.0024 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.935 / 17.943 | 17.950 / 17.911 | 0.9992 / 1.0018
|
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.687 / 4.695 | 4.840 / 4.686 | 0.9684 / 1.0019 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.390 / 18.393 | 18.370 /
18.390 | 1.0011 / 1.0002 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.270 /
4.287 | 4.291 / 4.279 | 0.9951 / 1.0019 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 16.941 / 16.931 | 16.469 / 16.466 | 1.0287 / 1.0282
|
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.214 / 4.223
| 4.208 / 4.227 | 1.0014 / 0.9991 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 16.412 / 16.422 | 16.388 / 16.427 | 1.0015 / 0.9997
|
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.280 / 4.258 | 4.267 / 4.236 | 1.0030 / 1.0052 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 16.680 / 16.625 | 16.679 /
16.606 | 1.0001 / 1.0011 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B1 = forward | 4.798 /
4.800 | 4.801 / 4.785 | 0.9994 / 1.0031 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 19.199 / 19.219 | 18.710 / 18.700 | 1.0261 / 1.0278
|
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B1 = forward | 4.758 / 4.756
| 4.757 / 4.756 | 1.0002 / 1.0000 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.741 / 18.716 | 18.744 / 18.703 | 0.9998 / 1.0007
|
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.906 / 4.946 | 4.906 / 4.940 | 1.0000 / 1.0012 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.318 / 19.342 | 19.275 /
19.310 | 1.0022 / 1.0017 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B1 = forward | 4.482 /
4.480 | 4.437 / 4.419 | 1.0101 / 1.0138 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.851 / 17.860 | 17.278 / 17.251 | 1.0332 / 1.0353
|
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B1 = forward | 4.763 / 4.417
| 4.581 / 4.416 | 1.0397 / 1.0002 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.294 / 17.278 | 17.293 / 17.273 | 1.0001 / 1.0003
|
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.536 / 4.522 | 4.502 / 4.513 | 1.0076 / 1.0020 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 17.643 / 17.596 | 17.581 /
17.577 | 1.0035 / 1.0011 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B1 = forward | 4.691 /
4.691 | 4.708 / 4.690 | 0.9964 / 1.0002 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.761 / 18.754 | 18.275 / 18.239 | 1.0266 / 1.0282
|
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B1 = forward | 4.664 / 4.672
| 4.946 / 4.662 | 0.9430 / 1.0021 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.331 / 18.322 | 18.329 / 18.320 | 1.0001 / 1.0001
|
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.880 / 4.879 | 4.885 / 4.893 | 0.9990 / 0.9971 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.196 / 19.193 | 19.207 /
19.207 | 0.9994 / 0.9993 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.610 /
4.603 | 4.616 / 4.598 | 0.9987 / 1.0011 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.454 / 18.436 | 17.935 / 17.912 | 1.0289 / 1.0293
|
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.571 / 4.579
| 4.563 / 4.558 | 1.0018 / 1.0046 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.917 / 17.905 | 17.930 / 17.890 | 0.9993 / 1.0008
|
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.634 / 4.631 | 4.634 / 4.640 | 1.0000 / 0.9981 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.295 / 18.288 | 18.293 /
18.328 | 1.0001 / 0.9978 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B1 = forward | 2.710 /
2.703 | 2.818 / 2.637 | 0.9617 / 1.0250 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.116 / 10.097 | 9.762 / 9.767 | 1.0363
/ 1.0338 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B1 = forward | 2.646 / 2.644
| 2.637 / 2.638 | 1.0034 / 1.0023 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.728 / 9.731 | 9.723 / 9.723 | 1.0005 / 1.0008 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.867 / 2.851 | 2.846 / 2.845 | 1.0074 / 1.0021 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.413 / 10.404 | 10.404 /
10.420 | 1.0009 / 0.9985 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.524 /
2.514 | 2.531 / 2.520 | 0.9972 / 0.9976 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.324 / 9.301 | 9.092 / 9.064 | 1.0255 /
1.0261 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.553 / 2.561
| 2.466 / 2.471 | 1.0353 / 1.0364 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.002 / 8.989 | 8.965 / 8.974 | 1.0041 / 1.0017 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.598 / 2.571 | 2.593 / 2.566 | 1.0019 / 1.0019 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 9.568 / 9.524 | 9.535 / 9.498 |
1.0035 / 1.0027 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B1 = forward | 2.808 /
2.790 | 2.802 / 2.794 | 1.0021 / 0.9986 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.527 / 10.490 | 10.252 / 10.215 |
1.0268 / 1.0269 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B1 = forward | 2.749 / 2.741
| 2.744 / 2.739 | 1.0018 / 1.0007 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 10.144 / 10.122 | 10.143 / 10.114 | 1.0001 / 1.0008
|
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.048 / 3.044 | 3.036 / 3.039 | 1.0040 / 1.0016 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.182 / 11.187 | 11.171 /
11.172 | 1.0010 / 1.0013 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B1 = forward | 2.644 /
2.633 | 2.574 / 2.565 | 1.0272 / 1.0265 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.794 / 9.788 | 9.443 / 9.423 | 1.0372 /
1.0387 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B1 = forward | 2.596 / 2.592
| 2.586 / 2.582 | 1.0039 / 1.0039 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.515 / 9.492 | 9.479 / 9.468 | 1.0038 / 1.0025 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.771 / 2.772 | 2.768 / 2.762 | 1.0011 / 1.0036 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.123 / 10.117 | 10.089 /
10.095 | 1.0034 / 1.0022 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B1 = forward | 2.757 /
2.755 | 2.756 / 2.752 | 1.0004 / 1.0011 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.311 / 10.290 | 10.031 / 10.020 |
1.0279 / 1.0269 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B1 = forward | 2.695 / 2.688
| 2.795 / 2.678 | 0.9642 / 1.0037 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.935 / 9.934 | 9.929 / 9.913 | 1.0006 / 1.0021 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.970 / 2.965 | 2.966 / 2.953 | 1.0013 / 1.0041 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.870 / 10.848 | 10.879 /
10.859 | 0.9992 / 0.9990 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.689 /
2.683 | 2.689 / 2.677 | 1.0000 / 1.0022 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.057 / 10.021 | 9.783 / 9.773 | 1.0280
/ 1.0254 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.644 / 2.645
| 2.642 / 2.627 | 1.0008 / 1.0069 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.725 / 9.706 | 9.721 / 9.755 | 1.0004 / 0.9950 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.751 / 2.780 | 2.742 / 2.783 | 1.0033 / 0.9989 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.305 / 10.316 | 10.282 /
10.313 | 1.0022 / 1.0003 |

The family's other Cake variant is the single-device packed KDA training
forward with saved-context and checkpoint-replay backward, together with
the non-context-parallel causal conv1d + SiLU training backend; the
family ships on sm_100a, sm_103a and sm_107a, its generated kernels are
built for all three, and this PR changes none of them.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Saved-mode backward processing can reuse stored carry data for
multi-segment fragments, avoiding repeated offset walks and carry
merges.
* **Options**
* Choose whether to save carry data or recompute it during backward
processing. Saving carry data is enabled by default and increases the
reported saved-memory requirement when plans use multiple segments.
* **Bug Fixes**
* Trimmed training paths now follow the same legacy channel-tile
planning rule as untrimmed paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2706a07](https://github.com/flashinfer-ai/flashinfer/commit/2706a076ac2b21aff3efa6b928400098b3d3b09b)

- **作者**: eigen
- **时间**: 2026-10-23T19:09:20Z
- **提交信息**: feat(cake_dense_projection_gemm): sm_103a programs, small-N shape rules, FP32 router backward (#7108)

`flashinfer/experimental/dense_projection_gemm` is the Cake backend of
the dense projection GEMM family. The family covers BF16 forward (fwd),
input-gradient (dgrad) and weight-gradient (wgrad) layouts, BF16 and
FP32-output gradient forms, batched MLA q-absorb and v-proj forms, and
the FP32 router GEMM, which runs as a split-BF16x3 GEMM with a fused
operand split. This PR adds sm_103a programs, small-N shape rules and
the FP32 router backward. The package now has 247 compiled program
instances (80 sm_100a / 80 sm_103a / 87 sm_107a), up from 104 (47 / 57)
in the package at FlashInfer main after #7066, which had no sm_103a
programs. This PR is faster than the baseline named in the row in 242 of
294 rows on GB200 and 250 of 294 rows on GB300. "previous version" means
the package at FlashInfer main after #7066 and is the baseline wherever
it served the shape. "cuBLAS BF16" or "cuBLAS FP32 (BF16x9)" is the
baseline wherever it did not: the small-N shapes that previously raised
`NotImplementedError`, and every GB300 row, because the previous version
had no sm_103a programs.

**NVIDIA GB200 (sm_100a), driver 580.126.20, CUDA 13.4 (nvcc 13.4.92);
node nvl72005-T14. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × 20 iterations, both sides in the same session. Latency in µs;
speedup = baseline / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
174.3 | 172.6 | 1.010 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
174.6 | 171.9 | 1.016 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 173.7
| 167.5 | 1.037 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 174.4
| 167.5 | 1.041 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
176.5 | 176.4 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
177.1 | 176.6 | 1.003 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 174.8
| 174.9 | 0.999 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 175.6
| 175.8 | 0.998 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
258.6 | 258.6 | 1.000 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
259.3 | 259.6 | 0.999 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
262.8 | 262.9 | 1.000 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
262.1 | 257.1 | 1.019 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
255.6 | 251.8 | 1.015 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
251.3 | 251.2 | 1.000 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
262.9 | 262.1 | 1.003 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
258.0 | 258.3 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
264.7 | 260.4 | 1.017 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
261.8 | 260.6 | 1.004 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 646.7 |
646.9 | 1.000 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 650.0 |
647.2 | 1.004 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 645.3 |
644.6 | 1.001 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 645.9 |
645.0 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 622.6 |
619.3 | 1.005 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 622.6 |
622.6 | 1.000 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 633.7 |
632.5 | 1.002 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 635.3 |
634.7 | 1.001 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 642.3 |
642.9 | 0.999 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 645.6 |
644.7 | 1.001 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 26.2 | 23.9 |
1.097 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 26.2 | 24.0 |
1.093 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 46.6 | 44.8 | 1.041
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 47.1 | 45.0 | 1.046
|
| 4096→32 | fwd | bf16 | 16231 | cuBLAS BF16 | 28.2 | 26.2 | 1.077 |
| 4096→32 | fwd | bf16 | 16384 | cuBLAS BF16 | 28.6 | 26.1 | 1.096 |
| 4096→32 | wgrad | bf16 | 16231 | cuBLAS BF16 | 31.5 | 28.2 | 1.116 |
| 4096→32 | wgrad | bf16 | 16384 | cuBLAS BF16 | 31.5 | 28.0 | 1.125 |
| 4096→32 | wgrad | f32 | 16231 | cuBLAS BF16 | 35.5 | 28.2 | 1.258 |
| 4096→32 | wgrad | f32 | 16384 | cuBLAS BF16 | 35.4 | 28.1 | 1.260 |
| 4096→48 | dgrad | bf16 | 16231 | previous version | 26.5 | 24.4 |
1.086 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 26.6 | 24.5 |
1.084 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 46.9 | 45.0 | 1.043
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 47.5 | 45.5 | 1.045
|
| 4096→48 | fwd | bf16 | 16231 | cuBLAS BF16 | 29.2 | 26.4 | 1.108 |
| 4096→48 | fwd | bf16 | 16384 | cuBLAS BF16 | 29.5 | 26.1 | 1.129 |
| 4096→48 | wgrad | bf16 | 16231 | cuBLAS BF16 | 32.4 | 28.2 | 1.148 |
| 4096→48 | wgrad | bf16 | 16384 | cuBLAS BF16 | 33.3 | 28.2 | 1.180 |
| 4096→48 | wgrad | f32 | 16231 | cuBLAS BF16 | 36.3 | 28.2 | 1.287 |
| 4096→48 | wgrad | f32 | 16384 | cuBLAS BF16 | 37.3 | 28.3 | 1.320 |
| 4096→64 | dgrad | bf16 | 16231 | previous version | 26.1 | 24.4 |
1.068 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 26.2 | 24.5 |
1.067 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 47.1 | 45.1 | 1.044
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 47.4 | 45.2 | 1.047
|
| 4096→64 | fwd | bf16 | 16231 | cuBLAS BF16 | 29.7 | 26.6 | 1.115 |
| 4096→64 | fwd | bf16 | 16384 | cuBLAS BF16 | 29.6 | 26.5 | 1.117 |
| 4096→64 | wgrad | bf16 | 16231 | cuBLAS BF16 | 30.2 | 28.7 | 1.054 |
| 4096→64 | wgrad | bf16 | 16384 | cuBLAS BF16 | 30.8 | 28.3 | 1.091 |
| 4096→64 | wgrad | f32 | 16231 | cuBLAS BF16 | 34.0 | 28.6 | 1.186 |
| 4096→64 | wgrad | f32 | 16384 | cuBLAS BF16 | 34.6 | 28.5 | 1.214 |
| 4096→128 | dgrad | bf16 | 16231 | previous version | 28.8 | 25.6 |
1.126 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 28.9 | 25.7 |
1.123 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 49.6 | 47.2 |
1.052 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 50.0 | 47.5 |
1.054 |
| 4096→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 31.8 | 27.4 | 1.163 |
| 4096→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 29.9 | 27.0 | 1.107 |
| 4096→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 34.4 | 29.3 | 1.172 |
| 4096→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 34.8 | 29.2 | 1.194 |
| 4096→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 38.3 | 29.4 | 1.304 |
| 4096→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 38.9 | 29.1 | 1.337 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 52.1 | 49.8 |
1.047 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 52.6 | 49.6 |
1.062 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 69.5 | 69.4 |
1.001 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 69.7 | 69.8 |
0.999 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 54.2 | 54.1 | 1.002
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 54.5 | 54.0 | 1.010
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 89.3 | 48.4 |
1.847 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 89.8 | 48.8 |
1.842 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 91.0 | 48.5 |
1.878 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 91.5 | 48.7 |
1.877 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 96.3 | 93.5 |
1.030 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 96.4 | 93.8 |
1.028 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 105.4 | 94.2 |
1.119 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 106.0 | 94.2 |
1.125 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 113.0 | 93.3 |
1.212 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 114.6 | 94.1 |
1.218 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 115.2 | 96.4 |
1.195 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 116.2 | 97.7 |
1.189 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 330.8 | 318.5 |
1.039 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 328.2 | 311.5 |
1.054 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 328.8 | 312.1 |
1.053 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 329.5 | 314.6 |
1.047 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 337.8 | 330.2 |
1.023 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 340.3 | 326.4 |
1.043 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 339.9 | 328.3 |
1.035 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 342.4 | 330.4 |
1.036 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 964.7 | 927.1 |
1.041 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 977.4 | 925.9 |
1.056 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 928.6 | 919.0 |
1.010 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 936.4 | 910.3 |
1.029 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 1018.0 | 922.0
| 1.104 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 1065.9 | 925.7
| 1.151 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 1035.9 | 965.0 |
1.074 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 1036.2 | 960.1 |
1.079 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 36.9 | 28.9 |
1.279 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 31.1 | 28.9 |
1.075 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 56.0 | 53.8 | 1.041
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 56.4 | 54.0 | 1.044
|
| 5120→32 | fwd | bf16 | 16231 | cuBLAS BF16 | 34.7 | 31.3 | 1.109 |
| 5120→32 | fwd | bf16 | 16384 | cuBLAS BF16 | 35.4 | 32.3 | 1.095 |
| 5120→32 | wgrad | bf16 | 16231 | cuBLAS BF16 | 38.4 | 32.7 | 1.176 |
| 5120→32 | wgrad | bf16 | 16384 | cuBLAS BF16 | 39.0 | 33.1 | 1.179 |
| 5120→32 | wgrad | f32 | 16231 | cuBLAS BF16 | 42.2 | 32.5 | 1.298 |
| 5120→32 | wgrad | f32 | 16384 | cuBLAS BF16 | 42.7 | 32.9 | 1.295 |
| 5120→48 | dgrad | bf16 | 16231 | previous version | 31.6 | 29.1 |
1.086 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 31.6 | 29.4 |
1.076 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 56.6 | 54.2 | 1.044
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 57.1 | 54.6 | 1.047
|
| 5120→48 | fwd | bf16 | 16231 | cuBLAS BF16 | 36.0 | 31.5 | 1.144 |
| 5120→48 | fwd | bf16 | 16384 | cuBLAS BF16 | 36.2 | 32.1 | 1.129 |
| 5120→48 | wgrad | bf16 | 16231 | cuBLAS BF16 | 41.3 | 33.2 | 1.242 |
| 5120→48 | wgrad | bf16 | 16384 | cuBLAS BF16 | 37.9 | 33.8 | 1.122 |
| 5120→48 | wgrad | f32 | 16231 | cuBLAS BF16 | 45.2 | 33.1 | 1.363 |
| 5120→48 | wgrad | f32 | 16384 | cuBLAS BF16 | 41.7 | 33.6 | 1.242 |
| 5120→64 | dgrad | bf16 | 16231 | previous version | 31.2 | 29.0 |
1.073 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 31.3 | 29.4 |
1.065 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 56.6 | 54.5 | 1.039
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 56.8 | 54.7 | 1.039
|
| 5120→64 | fwd | bf16 | 16231 | cuBLAS BF16 | 36.1 | 31.9 | 1.133 |
| 5120→64 | fwd | bf16 | 16384 | cuBLAS BF16 | 36.5 | 32.5 | 1.123 |
| 5120→64 | wgrad | bf16 | 16231 | cuBLAS BF16 | 38.7 | 33.3 | 1.164 |
| 5120→64 | wgrad | bf16 | 16384 | cuBLAS BF16 | 38.9 | 33.5 | 1.162 |
| 5120→64 | wgrad | f32 | 16231 | cuBLAS BF16 | 42.6 | 33.2 | 1.283 |
| 5120→64 | wgrad | f32 | 16384 | cuBLAS BF16 | 42.8 | 33.4 | 1.281 |
| 5120→128 | dgrad | bf16 | 16231 | previous version | 34.6 | 30.7 |
1.127 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 34.6 | 30.6 |
1.133 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 59.5 | 56.8 |
1.047 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 60.1 | 57.3 |
1.049 |
| 5120→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 38.5 | 33.1 | 1.162 |
| 5120→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 36.9 | 32.8 | 1.125 |
| 5120→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 41.0 | 33.7 | 1.218 |
| 5120→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 41.6 | 34.1 | 1.219 |
| 5120→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 45.2 | 33.5 | 1.346 |
| 5120→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 45.9 | 34.1 | 1.346 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 68.0 | 64.5 |
1.053 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 67.8 | 64.6 |
1.049 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 86.9 | 86.8 |
1.001 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 86.5 | 86.1 |
1.004 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 67.7 | 67.9 | 0.997
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 67.9 | 68.4 | 0.994
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 95.3 | 65.6 |
1.452 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 96.2 | 66.0 |
1.457 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 96.4 | 67.0 |
1.439 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 97.4 | 67.2 |
1.449 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 117.3 | 113.3 |
1.035 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 117.2 | 113.5 |
1.033 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 128.8 | 115.6 |
1.115 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 129.4 | 116.1 |
1.114 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 148.8 | 120.4 |
1.236 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 149.9 | 120.8 |
1.241 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 149.6 | 122.2 |
1.223 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 150.7 | 122.3 |
1.232 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 491.8 | 483.8 |
1.017 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 492.4 | 484.3 |
1.017 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 493.8 | 482.9 |
1.023 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 495.2 | 483.7 |
1.024 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 512.8 | 490.4 |
1.046 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 516.0 | 494.8 |
1.043 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 516.1 | 491.8 |
1.049 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 520.2 | 495.3 |
1.050 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1665.0 | 1646.0
| 1.012 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1687.2 | 1617.1
| 1.043 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1658.7 | 1742.3 |
0.952 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1731.1 | 1633.2 |
1.060 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1583.5 | 1639.6
| 0.966 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1719.0 | 1709.3
| 1.006 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1626.4 | 1613.4
| 1.008 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1666.8 | 1602.2
| 1.040 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 34.2
| 34.2 | 1.002 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 34.1
| 34.1 | 1.000 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 61.3 |
61.3 | 0.999 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 61.7 |
61.4 | 1.004 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 37.7 |
37.0 | 1.020 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 36.9 |
37.0 | 0.997 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 37.8
| 37.6 | 1.006 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 37.5
| 37.7 | 0.996 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 37.7 |
37.5 | 1.004 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 37.6 |
37.6 | 1.002 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 35.9
| 35.8 | 1.002 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 35.9
| 36.0 | 0.998 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 65.3 |
65.4 | 0.999 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 65.3 |
65.3 | 1.000 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 38.4 |
38.5 | 0.998 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 38.4 |
38.3 | 1.001 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 38.5
| 38.5 | 0.999 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 38.7
| 38.7 | 1.000 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 38.4 |
38.4 | 1.002 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 38.5 |
38.5 | 1.001 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 84.3 |
84.5 | 0.997 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 84.5 |
84.3 | 1.003 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 110.8 |
110.7 | 1.001 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 110.6 |
111.0 | 0.996 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 92.9 | 92.7
| 1.002 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 93.1 | 92.8
| 1.003 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 81.3 |
81.4 | 1.000 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 81.5 |
81.4 | 1.000 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 82.4 | 82.7
| 0.996 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 83.1 | 83.0
| 1.001 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 255.9 |
254.4 | 1.006 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 250.5 |
252.3 | 0.993 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 262.4 |
262.0 | 1.001 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 262.8 |
263.1 | 0.999 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 255.0 |
250.1 | 1.020 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 248.9 |
249.4 | 0.998 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 258.1 |
258.3 | 0.999 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 258.9 |
258.8 | 1.000 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 258.9 |
259.1 | 0.999 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 259.3 |
260.6 | 0.995 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
250.2 | 251.3 | 0.996 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
251.1 | 251.3 | 0.999 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
262.5 | 262.9 | 0.998 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
262.7 | 262.8 | 1.000 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
248.8 | 249.2 | 0.998 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
249.2 | 248.9 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
257.6 | 258.2 | 0.998 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
258.7 | 259.7 | 0.996 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
259.5 | 259.7 | 0.999 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
260.4 | 260.4 | 1.000 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1392.1 | 1360.8 | 1.023 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1369.4 | 1361.9 | 1.005 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1363.3 | 1353.2 | 1.008 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1363.2 | 1364.7 | 0.999 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 64.8 | 47.8 |
1.356 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 53.1 | 46.8 |
1.136 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 94.7 | 90.9 |
1.042 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 94.0 | 90.1 |
1.043 |
| 8192→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 58.6 | 48.7 | 1.204 |
| 8192→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 56.6 | 49.3 | 1.148 |
| 8192→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 54.6 | 44.9 | 1.216 |
| 8192→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 55.2 | 45.1 | 1.224 |
| 8192→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 59.6 | 44.8 | 1.330 |
| 8192→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 60.1 | 44.9 | 1.340 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 923.6 | 908.4 |
1.017 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 925.9 | 923.4 |
1.003 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 970.7 | 921.7 |
1.053 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 974.7 | 922.9 |
1.056 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 1008.8 | 900.0
| 1.121 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 1013.6 | 914.7
| 1.108 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 1028.3 | 929.7 |
1.106 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 1029.0 | 934.2 |
1.102 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1352.0 | 1336.2 | 1.012 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1449.0 | 1366.6 | 1.060 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1395.7 | 1355.5 | 1.030 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1386.9 | 1351.1 | 1.026 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 2011.9
| 1819.6 | 1.106 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1900.4
| 1821.2 | 1.043 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1869.9
| 1843.3 | 1.014 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1898.2
| 1932.0 | 0.983 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1852.4 |
1839.6 | 1.007 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1880.0 |
1842.8 | 1.020 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1808.8
| 1793.8 | 1.008 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1801.4
| 1911.2 | 0.943 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1876.9
| 1826.9 | 1.027 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1950.9
| 1837.3 | 1.062 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1612.7 | 1610.7
| 1.001 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1651.1 | 1626.5
| 1.015 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1719.0 | 1597.0 |
1.076 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1684.2 | 1599.6 |
1.053 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1587.3 | 1592.5
| 0.997 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1699.7 | 1596.4
| 1.065 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1617.4 | 1588.4
| 1.018 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1607.6 | 1616.2
| 0.995 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16172 | previous
version | 234.7 | 241.2 | 0.973 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16231 | previous
version | 239.2 | 238.6 | 1.002 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16172 | previous
version | 261.3 | 266.5 | 0.981 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16231 | previous
version | 261.5 | 275.3 | 0.950 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16172 | previous
version | 216.3 | 216.3 | 1.000 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16231 | previous
version | 216.8 | 216.8 | 1.000 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16172 | previous
version | 277.0 | 290.4 | 0.954 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16231 | previous
version | 286.8 | 291.9 | 0.983 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16172 | previous version
| 265.5 | 263.7 | 1.007 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16231 | previous version
| 263.3 | 266.5 | 0.988 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16172 | previous
version | 235.6 | 235.4 | 1.001 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16231 | previous
version | 236.8 | 236.7 | 1.000 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 351.5 |
189.2 | 1.858 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 324.4 | 193.1
| 1.680 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 313.1 |
187.2 | 1.673 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 462.4 |
238.0 | 1.943 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 372.9 | 224.9
| 1.658 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 354.2 |
239.2 | 1.481 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 526.0 |
272.4 | 1.931 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 529.1 |
273.8 | 1.933 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 419.3 | 260.7
| 1.608 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 420.6 | 259.6
| 1.620 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 394.1 |
248.1 | 1.588 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 400.9 |
248.1 | 1.616 |

**NVIDIA GB300 (sm_103a), driver 580.159.03, CUDA 13.4 (nvcc 13.4.92);
node nvl72d333-T16. Cold-L2 CUPTI kernel time, median of 5 alternating
groups × 20 iterations, both sides in the same session. Latency in µs;
speedup = baseline / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | cuBLAS BF16 | 140.4 |
141.0 | 0.996 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | cuBLAS BF16 | 141.0 |
140.8 | 1.001 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | cuBLAS BF16 | 137.9 |
137.3 | 1.004 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | cuBLAS BF16 | 137.9 |
137.4 | 1.003 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | cuBLAS BF16 | 143.9 |
146.1 | 0.985 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | cuBLAS BF16 | 144.3 |
146.2 | 0.987 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | cuBLAS BF16 | 161.7 |
144.8 | 1.117 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | cuBLAS BF16 | 162.3 |
145.1 | 1.118 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | cuBLAS BF16 | 216.0 |
214.4 | 1.008 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | cuBLAS BF16 | 216.3 |
215.0 | 1.006 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | cuBLAS BF16 | 298.3 |
216.7 | 1.376 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | cuBLAS BF16 | 297.2 |
215.4 | 1.380 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | cuBLAS BF16 | 210.4 |
207.9 | 1.012 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | cuBLAS BF16 | 210.9 |
207.5 | 1.016 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | cuBLAS BF16 | 219.7 |
216.9 | 1.013 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | cuBLAS BF16 | 219.3 |
216.2 | 1.014 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | cuBLAS BF16 | 248.7 |
219.7 | 1.132 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | cuBLAS BF16 | 249.1 |
220.0 | 1.132 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | cuBLAS BF16 | 560.7 | 577.7
| 0.971 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | cuBLAS BF16 | 557.7 | 569.5
| 0.979 |
| q_b (2048→16384) | dgrad | f32 | 16172 | cuBLAS BF16 | 639.8 | 574.4 |
1.114 |
| q_b (2048→16384) | dgrad | f32 | 16231 | cuBLAS BF16 | 640.6 | 574.9 |
1.114 |
| q_b (2048→16384) | fwd | bf16 | 16172 | cuBLAS BF16 | 536.4 | 543.6 |
0.987 |
| q_b (2048→16384) | fwd | bf16 | 16231 | cuBLAS BF16 | 537.2 | 544.9 |
0.986 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | cuBLAS BF16 | 575.8 | 561.5
| 1.026 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | cuBLAS BF16 | 577.7 | 563.9
| 1.024 |
| q_b (2048→16384) | wgrad | f32 | 16172 | cuBLAS BF16 | 659.7 | 567.4 |
1.163 |
| q_b (2048→16384) | wgrad | f32 | 16231 | cuBLAS BF16 | 662.0 | 571.4 |
1.158 |
| 4096→32 | dgrad | bf16 | 16231 | cuBLAS BF16 | 26.4 | 23.1 | 1.139 |
| 4096→32 | dgrad | bf16 | 16384 | cuBLAS BF16 | 23.1 | 23.4 | 0.985 |
| 4096→32 | dgrad | f32 | 16231 | cuBLAS BF16 | 190.0 | 43.1 | 4.404 |
| 4096→32 | dgrad | f32 | 16384 | cuBLAS BF16 | 193.6 | 43.3 | 4.467 |
| 4096→32 | fwd | bf16 | 16231 | cuBLAS BF16 | 28.6 | 27.0 | 1.061 |
| 4096→32 | fwd | bf16 | 16384 | cuBLAS BF16 | 29.0 | 26.6 | 1.091 |
| 4096→32 | wgrad | bf16 | 16231 | cuBLAS BF16 | 31.8 | 28.4 | 1.119 |
| 4096→32 | wgrad | bf16 | 16384 | cuBLAS BF16 | 31.7 | 28.5 | 1.111 |
| 4096→32 | wgrad | f32 | 16231 | cuBLAS BF16 | 35.5 | 28.4 | 1.250 |
| 4096→32 | wgrad | f32 | 16384 | cuBLAS BF16 | 35.6 | 28.8 | 1.236 |
| 4096→48 | dgrad | bf16 | 16231 | cuBLAS BF16 | 25.2 | 23.6 | 1.068 |
| 4096→48 | dgrad | bf16 | 16384 | cuBLAS BF16 | 23.2 | 23.8 | 0.975 |
| 4096→48 | dgrad | f32 | 16231 | cuBLAS BF16 | 189.2 | 43.2 | 4.374 |
| 4096→48 | dgrad | f32 | 16384 | cuBLAS BF16 | 193.6 | 43.8 | 4.423 |
| 4096→48 | fwd | bf16 | 16231 | cuBLAS BF16 | 29.6 | 26.9 | 1.100 |
| 4096→48 | fwd | bf16 | 16384 | cuBLAS BF16 | 29.9 | 26.7 | 1.118 |
| 4096→48 | wgrad | bf16 | 16231 | cuBLAS BF16 | 33.3 | 28.8 | 1.158 |
| 4096→48 | wgrad | bf16 | 16384 | cuBLAS BF16 | 33.6 | 28.9 | 1.161 |
| 4096→48 | wgrad | f32 | 16231 | cuBLAS BF16 | 37.2 | 28.7 | 1.298 |
| 4096→48 | wgrad | f32 | 16384 | cuBLAS BF16 | 37.5 | 29.0 | 1.292 |
| 4096→64 | dgrad | bf16 | 16231 | cuBLAS BF16 | 24.0 | 23.4 | 1.027 |
| 4096→64 | dgrad | bf16 | 16384 | cuBLAS BF16 | 22.8 | 23.7 | 0.965 |
| 4096→64 | dgrad | f32 | 16231 | cuBLAS BF16 | 188.2 | 43.6 | 4.316 |
| 4096→64 | dgrad | f32 | 16384 | cuBLAS BF16 | 193.3 | 43.6 | 4.429 |
| 4096→64 | fwd | bf16 | 16231 | cuBLAS BF16 | 30.5 | 27.2 | 1.124 |
| 4096→64 | fwd | bf16 | 16384 | cuBLAS BF16 | 30.5 | 27.0 | 1.128 |
| 4096→64 | wgrad | bf16 | 16231 | cuBLAS BF16 | 30.5 | 28.8 | 1.059 |
| 4096→64 | wgrad | bf16 | 16384 | cuBLAS BF16 | 30.9 | 28.8 | 1.074 |
| 4096→64 | wgrad | f32 | 16231 | cuBLAS BF16 | 34.3 | 28.8 | 1.191 |
| 4096→64 | wgrad | f32 | 16384 | cuBLAS BF16 | 34.6 | 28.8 | 1.204 |
| 4096→128 | dgrad | bf16 | 16231 | cuBLAS BF16 | 28.7 | 24.4 | 1.179 |
| 4096→128 | dgrad | bf16 | 16384 | cuBLAS BF16 | 27.6 | 24.4 | 1.127 |
| 4096→128 | dgrad | f32 | 16231 | cuBLAS BF16 | 193.1 | 44.9 | 4.302 |
| 4096→128 | dgrad | f32 | 16384 | cuBLAS BF16 | 198.1 | 45.2 | 4.382 |
| 4096→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 32.6 | 28.0 | 1.164 |
| 4096→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 30.9 | 27.5 | 1.121 |
| 4096→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 35.2 | 29.6 | 1.188 |
| 4096→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 35.3 | 29.5 | 1.194 |
| 4096→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 39.1 | 29.7 | 1.315 |
| 4096→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 39.2 | 29.6 | 1.326 |
| 4096→512 | dgrad | bf16 | 16231 | cuBLAS BF16 | 41.6 | 43.1 | 0.965 |
| 4096→512 | dgrad | bf16 | 16384 | cuBLAS BF16 | 41.8 | 43.1 | 0.969 |
| 4096→512 | dgrad | f32 | 16231 | cuBLAS BF16 | 211.0 | 60.7 | 3.475 |
| 4096→512 | dgrad | f32 | 16384 | cuBLAS BF16 | 212.7 | 60.4 | 3.521 |
| 4096→512 | fwd | bf16 | 16231 | cuBLAS BF16 | 54.9 | 48.4 | 1.133 |
| 4096→512 | fwd | bf16 | 16384 | cuBLAS BF16 | 49.8 | 48.2 | 1.032 |
| 4096→512 | wgrad | bf16 | 16231 | cuBLAS BF16 | 49.9 | 43.3 | 1.151 |
| 4096→512 | wgrad | bf16 | 16384 | cuBLAS BF16 | 50.1 | 43.5 | 1.152 |
| 4096→512 | wgrad | f32 | 16231 | cuBLAS BF16 | 56.6 | 43.0 | 1.317 |
| 4096→512 | wgrad | f32 | 16384 | cuBLAS BF16 | 56.9 | 43.2 | 1.316 |
| 4096→1024 | dgrad | bf16 | 16231 | cuBLAS BF16 | 72.0 | 74.1 | 0.971 |
| 4096→1024 | dgrad | bf16 | 16384 | cuBLAS BF16 | 72.1 | 74.5 | 0.967 |
| 4096→1024 | fwd | bf16 | 16231 | cuBLAS BF16 | 76.2 | 74.8 | 1.019 |
| 4096→1024 | fwd | bf16 | 16384 | cuBLAS BF16 | 77.1 | 74.8 | 1.030 |
| 4096→1024 | wgrad | bf16 | 16231 | cuBLAS BF16 | 71.5 | 72.9 | 0.981 |
| 4096→1024 | wgrad | bf16 | 16384 | cuBLAS BF16 | 72.2 | 73.3 | 0.985 |
| 4096→1024 | wgrad | f32 | 16231 | cuBLAS BF16 | 83.5 | 75.1 | 1.112 |
| 4096→1024 | wgrad | f32 | 16384 | cuBLAS BF16 | 84.1 | 76.0 | 1.107 |
| 4096→4096 | dgrad | bf16 | 16231 | cuBLAS BF16 | 271.0 | 268.7 | 1.009
|
| 4096→4096 | dgrad | bf16 | 16384 | cuBLAS BF16 | 270.9 | 269.7 | 1.004
|
| 4096→4096 | fwd | bf16 | 16231 | cuBLAS BF16 | 270.3 | 268.6 | 1.006 |
| 4096→4096 | fwd | bf16 | 16384 | cuBLAS BF16 | 270.4 | 265.8 | 1.017 |
| 4096→4096 | wgrad | bf16 | 16231 | cuBLAS BF16 | 287.3 | 276.2 | 1.040
|
| 4096→4096 | wgrad | bf16 | 16384 | cuBLAS BF16 | 289.6 | 282.1 | 1.027
|
| 4096→4096 | wgrad | f32 | 16231 | cuBLAS BF16 | 326.6 | 281.6 | 1.160
|
| 4096→4096 | wgrad | f32 | 16384 | cuBLAS BF16 | 328.6 | 283.6 | 1.159
|
| 4096→12288 | dgrad | bf16 | 16231 | cuBLAS BF16 | 820.9 | 825.1 |
0.995 |
| 4096→12288 | dgrad | bf16 | 16384 | cuBLAS BF16 | 820.8 | 837.2 |
0.980 |
| 4096→12288 | fwd | bf16 | 16231 | cuBLAS BF16 | 824.4 | 801.5 | 1.028
|
| 4096→12288 | fwd | bf16 | 16384 | cuBLAS BF16 | 824.9 | 802.4 | 1.028
|
| 4096→12288 | wgrad | bf16 | 16231 | cuBLAS BF16 | 827.4 | 824.2 |
1.004 |
| 4096→12288 | wgrad | bf16 | 16384 | cuBLAS BF16 | 831.7 | 836.3 |
0.995 |
| 4096→12288 | wgrad | f32 | 16231 | cuBLAS BF16 | 954.8 | 839.1 | 1.138
|
| 4096→12288 | wgrad | f32 | 16384 | cuBLAS BF16 | 957.8 | 840.5 | 1.140
|
| 5120→32 | dgrad | bf16 | 16231 | cuBLAS BF16 | 28.7 | 27.5 | 1.044 |
| 5120→32 | dgrad | bf16 | 16384 | cuBLAS BF16 | 27.6 | 27.7 | 0.996 |
| 5120→32 | dgrad | f32 | 16231 | cuBLAS BF16 | 239.0 | 51.6 | 4.628 |
| 5120→32 | dgrad | f32 | 16384 | cuBLAS BF16 | 239.7 | 52.0 | 4.612 |
| 5120→32 | fwd | bf16 | 16231 | cuBLAS BF16 | 35.4 | 31.8 | 1.114 |
| 5120→32 | fwd | bf16 | 16384 | cuBLAS BF16 | 35.9 | 32.8 | 1.094 |
| 5120→32 | wgrad | bf16 | 16231 | cuBLAS BF16 | 38.7 | 34.4 | 1.127 |
| 5120→32 | wgrad | bf16 | 16384 | cuBLAS BF16 | 39.4 | 34.3 | 1.149 |
| 5120→32 | wgrad | f32 | 16231 | cuBLAS BF16 | 42.4 | 34.1 | 1.246 |
| 5120→32 | wgrad | f32 | 16384 | cuBLAS BF16 | 42.8 | 34.3 | 1.247 |
| 5120→48 | dgrad | bf16 | 16231 | cuBLAS BF16 | 28.6 | 27.8 | 1.031 |
| 5120→48 | dgrad | bf16 | 16384 | cuBLAS BF16 | 28.1 | 28.0 | 1.003 |
| 5120→48 | dgrad | f32 | 16231 | cuBLAS BF16 | 239.2 | 52.2 | 4.586 |
| 5120→48 | dgrad | f32 | 16384 | cuBLAS BF16 | 240.3 | 52.4 | 4.581 |
| 5120→48 | fwd | bf16 | 16231 | cuBLAS BF16 | 36.2 | 31.8 | 1.140 |
| 5120→48 | fwd | bf16 | 16384 | cuBLAS BF16 | 36.7 | 32.6 | 1.125 |
| 5120→48 | wgrad | bf16 | 16231 | cuBLAS BF16 | 41.6 | 34.5 | 1.204 |
| 5120→48 | wgrad | bf16 | 16384 | cuBLAS BF16 | 38.6 | 34.9 | 1.107 |
| 5120→48 | wgrad | f32 | 16231 | cuBLAS BF16 | 45.4 | 34.5 | 1.317 |
| 5120→48 | wgrad | f32 | 16384 | cuBLAS BF16 | 42.3 | 34.8 | 1.218 |
| 5120→64 | dgrad | bf16 | 16231 | cuBLAS BF16 | 28.1 | 28.0 | 1.003 |
| 5120→64 | dgrad | bf16 | 16384 | cuBLAS BF16 | 26.8 | 28.1 | 0.954 |
| 5120→64 | dgrad | f32 | 16231 | cuBLAS BF16 | 238.6 | 52.4 | 4.557 |
| 5120→64 | dgrad | f32 | 16384 | cuBLAS BF16 | 239.0 | 52.8 | 4.531 |
| 5120→64 | fwd | bf16 | 16231 | cuBLAS BF16 | 36.9 | 32.4 | 1.140 |
| 5120→64 | fwd | bf16 | 16384 | cuBLAS BF16 | 37.2 | 33.1 | 1.122 |
| 5120→64 | wgrad | bf16 | 16231 | cuBLAS BF16 | 39.5 | 34.7 | 1.139 |
| 5120→64 | wgrad | bf16 | 16384 | cuBLAS BF16 | 39.8 | 34.9 | 1.139 |
| 5120→64 | wgrad | f32 | 16231 | cuBLAS BF16 | 43.3 | 34.7 | 1.249 |
| 5120→64 | wgrad | f32 | 16384 | cuBLAS BF16 | 43.6 | 34.8 | 1.251 |
| 5120→128 | dgrad | bf16 | 16231 | cuBLAS BF16 | 33.4 | 29.1 | 1.148 |
| 5120→128 | dgrad | bf16 | 16384 | cuBLAS BF16 | 30.1 | 29.2 | 1.031 |
| 5120→128 | dgrad | f32 | 16231 | cuBLAS BF16 | 244.1 | 54.2 | 4.505 |
| 5120→128 | dgrad | f32 | 16384 | cuBLAS BF16 | 242.4 | 54.2 | 4.468 |
| 5120→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 39.0 | 33.4 | 1.166 |
| 5120→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 37.8 | 33.2 | 1.136 |
| 5120→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 41.9 | 36.0 | 1.164 |
| 5120→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 42.5 | 36.3 | 1.172 |
| 5120→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 45.8 | 35.7 | 1.282 |
| 5120→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 46.5 | 36.1 | 1.286 |
| 5120→512 | dgrad | bf16 | 16231 | cuBLAS BF16 | 50.1 | 54.6 | 0.918 |
| 5120→512 | dgrad | bf16 | 16384 | cuBLAS BF16 | 50.0 | 55.0 | 0.909 |
| 5120→512 | dgrad | f32 | 16231 | cuBLAS BF16 | 261.1 | 73.6 | 3.548 |
| 5120→512 | dgrad | f32 | 16384 | cuBLAS BF16 | 263.2 | 74.4 | 3.537 |
| 5120→512 | fwd | bf16 | 16231 | cuBLAS BF16 | 66.4 | 58.2 | 1.142 |
| 5120→512 | fwd | bf16 | 16384 | cuBLAS BF16 | 60.3 | 58.2 | 1.035 |
| 5120→512 | wgrad | bf16 | 16231 | cuBLAS BF16 | 64.0 | 53.3 | 1.199 |
| 5120→512 | wgrad | bf16 | 16384 | cuBLAS BF16 | 64.5 | 53.4 | 1.207 |
| 5120→512 | wgrad | f32 | 16231 | cuBLAS BF16 | 72.0 | 55.1 | 1.307 |
| 5120→512 | wgrad | f32 | 16384 | cuBLAS BF16 | 72.5 | 54.6 | 1.327 |
| 5120→1024 | dgrad | bf16 | 16231 | cuBLAS BF16 | 88.3 | 92.7 | 0.953 |
| 5120→1024 | dgrad | bf16 | 16384 | cuBLAS BF16 | 88.5 | 92.5 | 0.957 |
| 5120→1024 | fwd | bf16 | 16231 | cuBLAS BF16 | 93.5 | 92.9 | 1.006 |
| 5120→1024 | fwd | bf16 | 16384 | cuBLAS BF16 | 99.2 | 93.0 | 1.067 |
| 5120→1024 | wgrad | bf16 | 16231 | cuBLAS BF16 | 98.9 | 97.6 | 1.013 |
| 5120→1024 | wgrad | bf16 | 16384 | cuBLAS BF16 | 99.7 | 98.5 | 1.012 |
| 5120→1024 | wgrad | f32 | 16231 | cuBLAS BF16 | 111.7 | 99.0 | 1.129 |
| 5120→1024 | wgrad | f32 | 16384 | cuBLAS BF16 | 112.4 | 99.6 | 1.128 |
| 5120→5120 | dgrad | bf16 | 16231 | cuBLAS BF16 | 441.8 | 424.5 | 1.041
|
| 5120→5120 | dgrad | bf16 | 16384 | cuBLAS BF16 | 421.3 | 420.7 | 1.001
|
| 5120→5120 | fwd | bf16 | 16231 | cuBLAS BF16 | 436.1 | 420.9 | 1.036 |
| 5120→5120 | fwd | bf16 | 16384 | cuBLAS BF16 | 420.3 | 421.9 | 0.996 |
| 5120→5120 | wgrad | bf16 | 16231 | cuBLAS BF16 | 434.5 | 429.2 | 1.012
|
| 5120→5120 | wgrad | bf16 | 16384 | cuBLAS BF16 | 437.6 | 433.3 | 1.010
|
| 5120→5120 | wgrad | f32 | 16231 | cuBLAS BF16 | 496.2 | 428.7 | 1.157
|
| 5120→5120 | wgrad | f32 | 16384 | cuBLAS BF16 | 499.7 | 432.9 | 1.154
|
| 5120→17408 | dgrad | bf16 | 16231 | cuBLAS BF16 | 1432.9 | 1448.1 |
0.989 |
| 5120→17408 | dgrad | bf16 | 16384 | cuBLAS BF16 | 1446.2 | 1455.9 |
0.993 |
| 5120→17408 | fwd | bf16 | 16231 | cuBLAS BF16 | 1468.0 | 1423.2 |
1.032 |
| 5120→17408 | fwd | bf16 | 16384 | cuBLAS BF16 | 1482.0 | 1448.3 |
1.023 |
| 5120→17408 | wgrad | bf16 | 16231 | cuBLAS BF16 | 1412.1 | 1435.5 |
0.984 |
| 5120→17408 | wgrad | bf16 | 16384 | cuBLAS BF16 | 1425.2 | 1432.3 |
0.995 |
| 5120→17408 | wgrad | f32 | 16231 | cuBLAS BF16 | 1636.7 | 1429.1 |
1.145 |
| 5120→17408 | wgrad | f32 | 16384 | cuBLAS BF16 | 1655.0 | 1440.2 |
1.149 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | cuBLAS BF16 | 36.4 |
32.9 | 1.108 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | cuBLAS BF16 | 36.7 |
32.6 | 1.126 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | cuBLAS BF16 | 288.0 |
58.3 | 4.941 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | cuBLAS BF16 | 288.7 |
58.6 | 4.924 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | cuBLAS BF16 | 41.1 | 37.6
| 1.092 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | cuBLAS BF16 | 41.1 | 37.5
| 1.095 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | cuBLAS BF16 | 41.8 |
39.4 | 1.060 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | cuBLAS BF16 | 41.5 |
39.2 | 1.059 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | cuBLAS BF16 | 45.6 | 39.4
| 1.158 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | cuBLAS BF16 | 45.4 | 39.4
| 1.151 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | cuBLAS BF16 | 40.9 |
34.2 | 1.197 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | cuBLAS BF16 | 40.8 |
34.3 | 1.192 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | cuBLAS BF16 | 292.2 |
62.3 | 4.694 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | cuBLAS BF16 | 293.2 |
62.1 | 4.723 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | cuBLAS BF16 | 45.6 | 39.0
| 1.169 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | cuBLAS BF16 | 45.6 | 38.8
| 1.176 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | cuBLAS BF16 | 45.6 |
40.8 | 1.118 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | cuBLAS BF16 | 46.1 |
41.1 | 1.121 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | cuBLAS BF16 | 49.7 | 40.8
| 1.219 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | cuBLAS BF16 | 50.2 | 40.9
| 1.226 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | cuBLAS BF16 | 65.8 | 66.5 |
0.989 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | cuBLAS BF16 | 65.9 | 67.1 |
0.982 |
| kv_a (6144→576) | dgrad | f32 | 16172 | cuBLAS BF16 | 317.0 | 92.0 |
3.447 |
| kv_a (6144→576) | dgrad | f32 | 16231 | cuBLAS BF16 | 318.2 | 92.4 |
3.444 |
| kv_a (6144→576) | fwd | bf16 | 16172 | cuBLAS BF16 | 84.4 | 72.7 |
1.162 |
| kv_a (6144→576) | fwd | bf16 | 16231 | cuBLAS BF16 | 84.3 | 72.4 |
1.165 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | cuBLAS BF16 | 73.0 | 65.1 |
1.120 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | cuBLAS BF16 | 73.0 | 65.6 |
1.113 |
| kv_a (6144→576) | wgrad | f32 | 16172 | cuBLAS BF16 | 82.6 | 65.8 |
1.256 |
| kv_a (6144→576) | wgrad | f32 | 16231 | cuBLAS BF16 | 83.0 | 65.9 |
1.259 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | cuBLAS BF16 | 211.3 | 207.1 |
1.021 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | cuBLAS BF16 | 212.4 | 206.9 |
1.027 |
| q_a (6144→2048) | dgrad | f32 | 16172 | cuBLAS BF16 | 459.0 | 218.4 |
2.102 |
| q_a (6144→2048) | dgrad | f32 | 16231 | cuBLAS BF16 | 460.3 | 218.5 |
2.106 |
| q_a (6144→2048) | fwd | bf16 | 16172 | cuBLAS BF16 | 213.4 | 208.2 |
1.025 |
| q_a (6144→2048) | fwd | bf16 | 16231 | cuBLAS BF16 | 212.8 | 207.9 |
1.023 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | cuBLAS BF16 | 218.3 | 215.6 |
1.012 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | cuBLAS BF16 | 219.0 | 215.8 |
1.014 |
| q_a (6144→2048) | wgrad | f32 | 16172 | cuBLAS BF16 | 247.5 | 217.1 |
1.140 |
| q_a (6144→2048) | wgrad | f32 | 16231 | cuBLAS BF16 | 248.4 | 217.7 |
1.141 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | cuBLAS BF16 |
212.4 | 206.9 | 1.026 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | cuBLAS BF16 |
212.7 | 207.1 | 1.027 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | cuBLAS BF16 | 459.5
| 219.3 | 2.095 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | cuBLAS BF16 | 460.4
| 218.5 | 2.107 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | cuBLAS BF16 | 212.4
| 208.1 | 1.021 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | cuBLAS BF16 | 212.4
| 208.5 | 1.019 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | cuBLAS BF16 |
218.3 | 215.2 | 1.014 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | cuBLAS BF16 |
219.2 | 216.9 | 1.011 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | cuBLAS BF16 | 247.6
| 216.8 | 1.142 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | cuBLAS BF16 | 248.2
| 217.9 | 1.139 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | cuBLAS BF16 |
1179.2 | 1236.4 | 0.954 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | cuBLAS BF16 |
1198.5 | 1218.8 | 0.983 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | cuBLAS BF16 |
1369.1 | 1229.7 | 1.113 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | cuBLAS BF16 |
1366.5 | 1230.1 | 1.111 |
| 8192→128 | dgrad | bf16 | 16231 | cuBLAS BF16 | 55.7 | 43.8 | 1.271 |
| 8192→128 | dgrad | bf16 | 16384 | cuBLAS BF16 | 52.0 | 43.8 | 1.188 |
| 8192→128 | dgrad | f32 | 16231 | cuBLAS BF16 | 388.2 | 85.5 | 4.541 |
| 8192→128 | dgrad | f32 | 16384 | cuBLAS BF16 | 389.8 | 85.0 | 4.588 |
| 8192→128 | fwd | bf16 | 16231 | cuBLAS BF16 | 58.3 | 48.6 | 1.200 |
| 8192→128 | fwd | bf16 | 16384 | cuBLAS BF16 | 56.7 | 49.2 | 1.151 |
| 8192→128 | wgrad | bf16 | 16231 | cuBLAS BF16 | 56.5 | 45.6 | 1.238 |
| 8192→128 | wgrad | bf16 | 16384 | cuBLAS BF16 | 56.9 | 46.1 | 1.235 |
| 8192→128 | wgrad | f32 | 16231 | cuBLAS BF16 | 61.1 | 45.6 | 1.339 |
| 8192→128 | wgrad | f32 | 16384 | cuBLAS BF16 | 61.3 | 45.7 | 1.341 |
| 12288→4096 | dgrad | bf16 | 16231 | cuBLAS BF16 | 834.7 | 803.0 |
1.039 |
| 12288→4096 | dgrad | bf16 | 16384 | cuBLAS BF16 | 828.6 | 809.9 |
1.023 |
| 12288→4096 | fwd | bf16 | 16231 | cuBLAS BF16 | 814.9 | 825.1 | 0.988
|
| 12288→4096 | fwd | bf16 | 16384 | cuBLAS BF16 | 817.1 | 825.6 | 0.990
|
| 12288→4096 | wgrad | bf16 | 16231 | cuBLAS BF16 | 821.5 | 812.8 |
1.011 |
| 12288→4096 | wgrad | bf16 | 16384 | cuBLAS BF16 | 829.4 | 823.5 |
1.007 |
| 12288→4096 | wgrad | f32 | 16231 | cuBLAS BF16 | 943.1 | 829.1 | 1.138
|
| 12288→4096 | wgrad | f32 | 16384 | cuBLAS BF16 | 951.5 | 831.5 | 1.144
|
| dense_down (12288→6144) | wgrad | bf16 | 16172 | cuBLAS BF16 | 1182.1
| 1220.8 | 0.968 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | cuBLAS BF16 | 1188.9
| 1231.5 | 0.965 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | cuBLAS BF16 | 1371.5 |
1210.9 | 1.133 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | cuBLAS BF16 | 1384.6 |
1227.6 | 1.128 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | cuBLAS BF16 | 1695.0 |
1617.3 | 1.048 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | cuBLAS BF16 | 1722.2 |
1636.6 | 1.052 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | cuBLAS BF16 | 2339.3 |
1649.6 | 1.418 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | cuBLAS BF16 | 2347.2 |
1653.7 | 1.419 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | cuBLAS BF16 | 1663.6 |
1626.9 | 1.023 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | cuBLAS BF16 | 1657.6 |
1631.4 | 1.016 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | cuBLAS BF16 | 1617.3 |
1595.5 | 1.014 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | cuBLAS BF16 | 1632.9 |
1604.7 | 1.018 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | cuBLAS BF16 | 1873.0 |
1626.1 | 1.152 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | cuBLAS BF16 | 1871.6 |
1623.2 | 1.153 |
| 17408→5120 | dgrad | bf16 | 16231 | cuBLAS BF16 | 1492.8 | 1440.8 |
1.036 |
| 17408→5120 | dgrad | bf16 | 16384 | cuBLAS BF16 | 1466.3 | 1446.5 |
1.014 |
| 17408→5120 | fwd | bf16 | 16231 | cuBLAS BF16 | 1431.2 | 1450.6 |
0.987 |
| 17408→5120 | fwd | bf16 | 16384 | cuBLAS BF16 | 1429.5 | 1442.6 |
0.991 |
| 17408→5120 | wgrad | bf16 | 16231 | cuBLAS BF16 | 1409.6 | 1433.0 |
0.984 |
| 17408→5120 | wgrad | bf16 | 16384 | cuBLAS BF16 | 1443.6 | 1445.1 |
0.999 |
| 17408→5120 | wgrad | f32 | 16231 | cuBLAS BF16 | 1642.9 | 1440.0 |
1.141 |
| 17408→5120 | wgrad | f32 | 16384 | cuBLAS BF16 | 1640.1 | 1445.1 |
1.135 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16172 | cuBLAS BF16
| 683.8 | 232.4 | 2.942 |
| MLA q-absorb (64 heads, 192→512) | dgrad | bf16 | 16231 | cuBLAS BF16
| 682.7 | 230.8 | 2.958 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16172 | cuBLAS BF16 |
1398.6 | 241.4 | 5.793 |
| MLA q-absorb (64 heads, 192→512) | fwd | bf16 | 16231 | cuBLAS BF16 |
1407.3 | 246.2 | 5.717 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16172 | cuBLAS BF16
| 217.3 | 218.9 | 0.993 |
| MLA q-absorb (64 heads, 192→512) | wgrad | bf16 | 16231 | cuBLAS BF16
| 217.9 | 220.1 | 0.990 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16172 | cuBLAS BF16 |
1413.0 | 265.5 | 5.321 |
| MLA v-proj (64 heads, 512→256) | dgrad | bf16 | 16231 | cuBLAS BF16 |
1422.2 | 265.1 | 5.365 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16172 | cuBLAS BF16 |
835.6 | 253.0 | 3.303 |
| MLA v-proj (64 heads, 512→256) | fwd | bf16 | 16231 | cuBLAS BF16 |
841.4 | 257.0 | 3.274 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16172 | cuBLAS BF16 |
251.0 | 236.8 | 1.060 |
| MLA v-proj (64 heads, 512→256) | wgrad | bf16 | 16231 | cuBLAS BF16 |
252.0 | 237.8 | 1.060 |
| router 4096→256 | dgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 198.2 |
173.6 | 1.142 |
| router 4096→256 | fwd | f32 | 16231 | cuBLAS FP32 (BF16x9) | 341.1 |
166.2 | 2.052 |
| router 4096→256 | wgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 227.7 |
163.6 | 1.392 |
| router 5120→256 | dgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 242.2 |
225.0 | 1.076 |
| router 5120→256 | fwd | f32 | 16231 | cuBLAS FP32 (BF16x9) | 414.7 |
195.7 | 2.119 |
| router 5120→256 | wgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 272.7 |
208.4 | 1.308 |
| router 6144→256 | dgrad | f32 | 16172 | cuBLAS FP32 (BF16x9) | 285.5 |
260.6 | 1.096 |
| router 6144→256 | dgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 285.5 |
262.9 | 1.086 |
| router 6144→256 | fwd | f32 | 16172 | cuBLAS FP32 (BF16x9) | 488.2 |
226.7 | 2.153 |
| router 6144→256 | fwd | f32 | 16231 | cuBLAS FP32 (BF16x9) | 488.5 |
224.8 | 2.173 |
| router 6144→256 | wgrad | f32 | 16172 | cuBLAS FP32 (BF16x9) | 321.1 |
214.9 | 1.494 |
| router 6144→256 | wgrad | f32 | 16231 | cuBLAS FP32 (BF16x9) | 321.7 |
214.0 | 1.503 |

The other variants of the family ship in the same Cake package, whose
compiled programs cover sm_100a, sm_103a and sm_107a; the tables above
measure only sm_100a (GB200) and sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added dense projection GEMM support for SM103, with architecture-aware
kernel selection and tuning.
* Improved projection weight-gradient orientation and scheduling across
supported workloads.
* Added fused splitting for eligible router weight-gradient operations,
with a Torch-based fallback when unavailable.
* **Bug Fixes**
* Updated the default split count for transposed router weight
gradients.
* Clarified supported output layouts and validation; unsupported layouts
are rejected at launch.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [34d28b3](https://github.com/flashinfer-ai/flashinfer/commit/34d28b323239de8952c9361f9b0a3fd3e9a45290)

- **作者**: eigen
- **时间**: 2026-10-23T19:09:07Z
- **提交信息**: perf(cake_qsa_nvfp4): load K first, restore evict_first, 1-prmt dequant (#7103)

The Cake QSA kernel (`flashinfer.experimental.cake_qsa_nvfp4`, called as
`flashinfer.sparse.qsa_sparse_paged_attention(..., backend="cake")`)
does NVFP4 sparse paged GQA decode attention. It takes BF16 queries and
writes BF16 outputs, reads an NVFP4 (E2M1) paged KV cache with E4M3
block scales, and accumulates in FP32. The kernel has one data type, two
KV layouts (NHD, HND) and two forms, for four variants in total, and
this PR updates all four: the fused form is a single cooperative launch
whose split-KV merge is done by the splits' own CTAs, the split form
runs a decode kernel followed by a separate merge kernel, and the host
picks the form for each call. Against the previous Cake version of this
kernel (#7056), timed as paired runs of the previous and the new kernel
programs in one process, the speedup across 16 shapes is 0.995x-1.127x:
1.037x-1.127x at 16, 32 and 64 rows in both KV layouts and at 8 rows in
HND, and 0.995x-1.019x, within 2% of the previous version, at the other
nine shapes.

**NVIDIA H100 80GB HBM3 (SXM, 132 SMs), sm_90a, CUDA 13.4 (PyTorch
2.14.1+cu130).** 24 query heads, 2 KV heads, head dim 256, top-k 2051,
page size 16. L2 was flushed by memset before every call. Each value is
the median of 3 groups x 64 calls, each group after 8 warm-up calls, the
previous and the new kernel timed alternately in the same process.
Speedup = the pooled ratio of the paired samples (previous / this PR).

| KV layout | rows | previous (us) | this PR (us) | speedup |
|---|---|---|---|---|
| NHD | 1 | 9.98 | 9.90 | 1.008 |
| NHD | 2 | 11.26 | 11.17 | 1.009 |
| NHD | 4 | 12.82 | 12.74 | 1.006 |
| NHD | 8 | 16.66 | 16.51 | 1.009 |
| NHD | 16 | 23.65 | 22.02 | 1.074 |
| NHD | 32 | 36.42 | 32.32 | 1.127 |
| NHD | 64 | 58.59 | 56.30 | 1.041 |
| NHD | 128 | 99.81 | 100.33 | 0.995 |
| HND | 1 | 9.73 | 9.74 | 0.998 |
| HND | 2 | 11.07 | 10.86 | 1.019 |
| HND | 4 | 12.54 | 12.42 | 1.010 |
| HND | 8 | 17.39 | 16.19 | 1.074 |
| HND | 16 | 25.52 | 23.01 | 1.109 |
| HND | 32 | 38.83 | 34.45 | 1.127 |
| HND | 64 | 62.03 | 59.82 | 1.037 |
| HND | 128 | 103.15 | 103.50 | 0.997 |

Cake ships no other data type or layout of this kernel; the family ships
for `sm_80` and `sm_90a`, with the `sm_80` programs built from the
package's `build.json` and the numbers above measured on `sm_90a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Refreshed build metadata for the supported GPU kernel variants and
updated their associated verification values.
* Adjusted output-writing behavior in the affected computation paths. No
changes to public interfaces or documented end-user behavior are
indicated.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fd5e515](https://github.com/flashinfer-ai/flashinfer/commit/fd5e515c6f09d81b46bf1a323b92ddc7dac49970)

- **作者**: eigen
- **时间**: 2026-10-23T19:08:55Z
- **提交信息**: feat(cake_kda): document-group batching for the lower-memory arena option; with grad (#7102)

The lower-memory arena option of #7069 (lean backward layouts and the
split tail) made the backward arena about x1.5–1.6 smaller, but the
arena was still sized for the whole packed sequence. This PR adds the
option's second lever, document-group batching. `kda_train_arena` gains
`batch_tokens`, the token budget of a group of whole, contiguous
documents (groups are formed greedily and no document may exceed the
budget), and `max_docs_per_batch`, a cap on the documents per group that
needs `batch_tokens`. Both are `None` by default, so nothing changes
unless they are set. Under a batched option, `chunk_kda_fwd`,
`chunk_kda_bwd` and `chunk_kda` require `doc_lengths` (the documents'
token counts as host integers, in `cu_seqlens` order) because the host
never reads tensor contents; an asynchronous device assertion checks the
device-side `cu_seqlens` against them. `kda_train_workspace` and
`kda_train_workspace_bytes` also take `doc_lengths` and then size the
arena exactly for the largest group; without them they size it for a
bound of every group. The forward and the backward run their chunk-local
programs once per group on views of that one arena instead of once for
the whole pack. Every group keeps the whole problem's records, segment
count per document and non-proportional block table. It reads the whole
token tensors through absolute chunk offsets and gathers / scatters the
saved segment states by chain rank, so `out` and the five gradients are
bit-for-bit those of the option-off path. There is one documented
exception: an exactly-zero `u` / `w` entry in a chunk whose WY pair
partner changed may change sign. The package's tests compare bit
patterns, including on rows built for that case, and found no
difference. The time cost comes from the recurrence phases, which are
latency-bound along a document's chain and run once per group. As the
table shows, the cost is small when many (document, head) chains share
each launch (H 32 / H 64, or balanced documents) and large with few
chains (H 2 / H 4) or one group per document, so the option is meant for
memory-bound cases. Rows whose block table gives the documents
proportional segment counts (`num_docs * H <= 4` on the segmented route)
refuse the option with `ValueError`. A lean batched workspace still
serves no checkpoint replay (`saved=None`; `torch.utils.checkpoint` is
unaffected), while a batched workspace that is not lean replays group by
group. `cake_backend.memory_report` reports the batched bound and floor
and the realized partition, and `cake_backend.arena_for_budget` /
`KdaWorkspace.for_budget` try the group steps after the lean ones.

Backward arena and time per option on one NVIDIA GB300 (sm_103a, 152
SMs) with the CUDA 13.0 build of PyTorch 2.14.1. The rows are the S =
261393 family (four documents of 23496, 88510, 114974 and 34413 tokens;
H 4, 2, 8, 16, 32 and 64) and the balanced controls EQ4_H16 / EQ4_H64
(four documents of 65349, 65348, 65348 and 65348 tokens). The family's H
1 row refuses the option (`num_docs * H = 4`) and is therefore absent.
The option "lean, 4 tail passes (no groups)" is the one from #7069,
re-measured in this run as the reference for the group rows. The group
options add a `batch_tokens` chosen so that the greedy partition yields
2 groups, 3 groups or one group per document (`max_docs_per_batch=1` for
the last). "groups (tokens)" gives the realized groups (documents joined
by `+`, groups separated by `‖`). The columns "arena default" and "arena
option" give the size of the backward workspace's arena
(`kda_train_workspace_bytes`, with `doc_lengths` for the group options)
in MiB with the option off and on, and "reduction" is the reduction
factor. B2 is the backward alone from the saved set and B3 is
`torch.utils.checkpoint(use_reentrant=False)` forward + recompute +
backward; times are in ms, and "change" is option time / default time −
1. Times come from FlashInfer's `bench_gpu_time` in CUPTI mode (the sum
of the kernel times of one call, L2 flushed before every call). Each arm
and boundary ran three interleaved groups of 8 warm-up + 64 timed calls
in one process on the same inputs, with the arm order rotated per group.
The reported time is the median of the group medians, and the run's
noise band is 2 %. For every row and option, `out` and the five
gradients (`dq`, `dk`, `dv`, `dbeta`, `dg`) are bit-for-bit those of the
default arena, also through the checkpointed path ("outputs /
gradients").

| row | H | option | groups (tokens) | arena default | arena option |
reduction | B2 default (ms) | B2 option (ms) | B2 change | B3 default
(ms) | B3 option (ms) | B3 change | outputs / gradients |
|---|---:|---|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---|
| P8_h4_s261393 | 4 | lean, 4 tail passes (no groups) | - | 4,481 MiB |
2,930 MiB | x1.53 smaller | 3.258 | 3.385 | +3.9 % | 5.995 | 6.122 |
+2.1 % | bitwise equal |
| P8_h4_s261393 | 4 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 4,481 MiB | 1,667 MiB | x2.69 smaller |
3.258 | 4.347 | +33.4 % | 5.995 | 8.006 | +33.5 % | bitwise equal |
| P8_h4_s261393 | 4 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 4,481 MiB | 1,266 MiB | x3.54 smaller |
3.258 | 4.827 | +48.2 % | 5.995 | 9.512 | +58.7 % | bitwise equal |
| P8_h4_s261393 | 4 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 4,481 MiB | 1,266 MiB | x3.54 smaller |
3.258 | 6.312 | +93.7 % | 5.995 | 12.194 | +103.4 % | bitwise equal |
| P10_h2_s261393 | 2 | lean, 4 tail passes (no groups) | - | 2,241 MiB |
1,504 MiB | x1.49 smaller | 1.736 | 1.869 | +7.7 % | 3.235 | 3.367 |
+4.1 % | bitwise equal |
| P10_h2_s261393 | 2 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 2,241 MiB | 853 MiB | x2.63 smaller | 1.736
| 3.675 | +111.7 % | 3.235 | 7.041 | +117.7 % | bitwise equal |
| P10_h2_s261393 | 2 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 2,241 MiB | 652 MiB | x3.44 smaller |
1.736 | 4.963 | +185.9 % | 3.235 | 9.692 | +199.6 % | bitwise equal |
| P10_h2_s261393 | 2 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 2,241 MiB | 643 MiB | x3.49 smaller |
1.736 | 6.391 | +268.1 % | 3.235 | 12.453 | +285.0 % | bitwise equal |
| P11_h8_s261393 | 8 | lean, 4 tail passes (no groups) | - | 8,963 MiB |
5,746 MiB | x1.56 smaller | 6.358 | 6.504 | +2.3 % | 11.569 | 11.713 |
+1.2 % | bitwise equal |
| P11_h8_s261393 | 8 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 8,963 MiB | 3,276 MiB | x2.74 smaller |
6.358 | 7.439 | +17.0 % | 11.569 | 13.138 | +13.6 % | bitwise equal |
| P11_h8_s261393 | 8 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 8,963 MiB | 2,504 MiB | x3.58 smaller |
6.358 | 7.762 | +22.1 % | 11.569 | 13.455 | +16.3 % | bitwise equal |
| P11_h8_s261393 | 8 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 8,963 MiB | 2,504 MiB | x3.58 smaller |
6.358 | 8.720 | +37.2 % | 11.569 | 14.817 | +28.1 % | bitwise equal |
| P12_h16_s261393 | 16 | lean, 4 tail passes (no groups) | - | 17,926
MiB | 11,263 MiB | x1.59 smaller | 13.473 | 13.713 | +1.8 % | 23.722 |
23.886 | +0.7 % | bitwise equal |
| P12_h16_s261393 | 16 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 17,926 MiB | 6,439 MiB | x2.78 smaller |
13.473 | 15.656 | +16.2 % | 23.722 | 27.942 | +17.8 % | bitwise equal |
| P12_h16_s261393 | 16 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 17,926 MiB | 4,952 MiB | x3.62 smaller |
13.473 | 16.667 | +23.7 % | 23.722 | 29.880 | +26.0 % | bitwise equal |
| P12_h16_s261393 | 16 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 17,926 MiB | 4,952 MiB | x3.62 smaller
| 13.473 | 17.384 | +29.0 % | 23.722 | 31.252 | +31.7 % | bitwise equal
|
| P13_h32_s261393 | 32 | lean, 4 tail passes (no groups) | - | 35,851
MiB | 22,527 MiB | x1.59 smaller | 24.590 | 24.779 | +0.8 % | 40.190 |
40.301 | +0.3 % | bitwise equal |
| P13_h32_s261393 | 32 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 35,851 MiB | 12,877 MiB | x2.78 smaller |
24.590 | 26.970 | +9.7 % | 40.190 | 45.946 | +14.3 % | bitwise equal |
| P13_h32_s261393 | 32 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 35,851 MiB | 9,903 MiB | x3.62 smaller |
24.590 | 27.419 | +11.5 % | 40.190 | 47.819 | +19.0 % | bitwise equal |
| P13_h32_s261393 | 32 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 35,851 MiB | 9,903 MiB | x3.62 smaller
| 24.590 | 27.691 | +12.6 % | 40.190 | 49.085 | +22.1 % | bitwise equal
|
| P14_h64_s261393 | 64 | lean, 4 tail passes (no groups) | - | 71,703
MiB | 45,054 MiB | x1.59 smaller | 47.440 | 47.441 | +0.0 % | 79.817 |
79.746 | -0.1 % | bitwise equal |
| P14_h64_s261393 | 64 | lean, 4 tail passes, 2 document groups |
23496+88510 ‖ 114974+34413 | 71,703 MiB | 25,755 MiB | x2.78 smaller |
47.440 | 51.536 | +8.6 % | 79.817 | 84.809 | +6.3 % | bitwise equal |
| P14_h64_s261393 | 64 | lean, 4 tail passes, 3 document groups |
23496+88510 ‖ 114974 ‖ 34413 | 71,703 MiB | 19,806 MiB | x3.62 smaller |
47.440 | 53.090 | +11.9 % | 79.817 | 86.083 | +7.9 % | bitwise equal |
| P14_h64_s261393 | 64 | lean, 4 tail passes, one group per document |
23496 ‖ 88510 ‖ 114974 ‖ 34413 | 71,703 MiB | 19,806 MiB | x3.62 smaller
| 47.440 | 53.499 | +12.8 % | 79.817 | 86.417 | +8.3 % | bitwise equal |
| EQ4_H16 | 16 | lean, 4 tail passes (no groups) | - | 17,926 MiB |
11,263 MiB | x1.59 smaller | 12.643 | 12.829 | +1.5 % | 21.882 | 22.081
| +0.9 % | bitwise equal |
| EQ4_H16 | 16 | lean, 4 tail passes, 2 document groups | 65349+65348 ‖
65348+65348 | 17,926 MiB | 5,634 MiB | x3.18 smaller | 12.643 | 13.988 |
+10.6 % | 21.882 | 24.529 | +12.1 % | bitwise equal |
| EQ4_H16 | 16 | lean, 4 tail passes, 3 document groups | 65349 ‖
65348+65348 ‖ 65348 | 17,926 MiB | 5,634 MiB | x3.18 smaller | 12.643 |
15.709 | +24.3 % | 21.882 | 27.934 | +27.7 % | bitwise equal |
| EQ4_H16 | 16 | lean, 4 tail passes, one group per document | 65349 ‖
65348 ‖ 65348 ‖ 65348 | 17,926 MiB | 2,820 MiB | x6.36 smaller | 12.643
| 17.419 | +37.8 % | 21.882 | 31.326 | +43.2 % | bitwise equal |
| EQ4_H64 | 64 | lean, 4 tail passes (no groups) | - | 71,703 MiB |
45,054 MiB | x1.59 smaller | 47.967 | 47.906 | -0.1 % | 80.884 | 80.940
| +0.1 % | bitwise equal |
| EQ4_H64 | 64 | lean, 4 tail passes, 2 document groups | 65349+65348 ‖
65348+65348 | 71,703 MiB | 22,538 MiB | x3.18 smaller | 47.967 | 48.205
| +0.5 % | 80.884 | 81.286 | +0.5 % | bitwise equal |
| EQ4_H64 | 64 | lean, 4 tail passes, 3 document groups | 65349 ‖
65348+65348 ‖ 65348 | 71,703 MiB | 22,538 MiB | x3.18 smaller | 47.967 |
50.984 | +6.3 % | 80.884 | 84.023 | +3.9 % | bitwise equal |
| EQ4_H64 | 64 | lean, 4 tail passes, one group per document | 65349 ‖
65348 ‖ 65348 ‖ 65348 | 71,703 MiB | 11,280 MiB | x6.36 smaller | 47.967
| 53.679 | +11.9 % | 80.884 | 86.840 | +7.4 % | bitwise equal |

Refs #7039, #7040.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional document batching for KDA training, grouping contiguous
whole documents by a token limit and optional maximum document count.
* Batched execution accepts host-provided document lengths and checks
them against sequence offsets.
* Workspace sizing and memory reports can use exact document lengths;
budget-based selection can consider progressively smaller batch
configurations.
* **Limitations**
* Batching is unavailable for proportional segmented rows. Checkpoint
replay with lean workspaces remains unsupported; non-lean workspaces
support replay group by group.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2c89a4f](https://github.com/flashinfer-ai/flashinfer/commit/2c89a4fefbd961525900b83ccf5435c4dc348d93)

- **作者**: Edwin Mascarenhas
- **时间**: 2026-10-23T18:41:46Z
- **提交信息**: comm: MXFP8 output for the allreduce + residual + RMSNorm fusion (#7031)

# comm: MXFP8 output for the allreduce + residual + RMSNorm fusion

<!-- .github/pull_request_template.md -->

## 📌 Description

Add two allreduce fusion patterns that quantize the RMSNorm output to
MXFP8 so an MXFP8 GEMM consumer avoids the overhead of an additional
quant kernel.

| pattern | value | outputs |
|---|---|---|
| `kARResidualRMSNormMXFP8Quant` | 13 | `residual_out`, `quant_out`,
`scale_out` |
| `kARResidualRMSNormOutMXFP8Quant` | 14 | as above, plus `norm_out` |

Both are supported on the TRT-LLM backend and on the MNNVL backend
(`MNNVLQuantType.MXFP8`, one-shot and two-shot), with the same
arguments, layouts and numerics.

**Why.** The FP8 and NVFP4 patterns exist; MXFP8 had no equivalent.
Models whose dense layers are MXFP8 (for example MiniMax-M3, whose
attention, shared-expert and dense projections ship in MXFP8) ran the
fusion and then a standalone quantize kernel.

**Outputs.** `quant_out` is `[token_num, hidden_dim]` `float8_e4m3fn`.
`scale_out` is a contiguous `uint8` buffer with one UE8M0 scale per 32
elements, in the `SWIZZLED_128x4` (default) or `LINEAR` layout. It must
hold at least `round_up(token_num, 128) * round_up(hidden_dim / 32, 4)`
bytes for `SWIZZLED_128x4`, or `token_num * hidden_dim / 32` bytes for
`LINEAR`. The output bytes are identical to running
`mxfp8_quantize(backend="cute-dsl")` on the bf16/fp16 norm output:
`scale = ue8m0_ceil(amax / 448)`, `q = satfinite_rn(x * 2^-scale)`.

**Implementation.**
- The epilogue is one device helper,
`trtllm_allreduce_fusion::utils::mxfp8_quantize_store`. It is called on
the bf16/fp16 norm output by the TRT-LLM kernels, the MNNVL one-shot
kernel and the MNNVL two-shot RMSNorm kernel.
- It reduces each 32-element scale group's amax with warp shuffles, so a
group's threads must sit in one CTA. For MXFP8 the MNNVL dispatchers
keep the CTA size a multiple of the group's thread count:
  - they narrow the cluster (one-shot, and two-shot with a cluster);
- or they round the CTA up when the two-shot RMSNorm kernel strides the
row; the extra threads skip the out-of-range tail.

Common hidden sizes already satisfy this; hidden 1056 with few tokens
did not.
- Each scale-group leader also zeroes its row's padded scale columns.
The padded scale rows `[token_num, round_up(token_num, 128))` are left
unwritten:
  - they exist only to fill the GEMM's last 128-row M tile;
  - the GEMM never stores those output rows;
  - each output row uses only its own scales.

Zeroing them in a serial loop dominated the kernel at small token
counts.
- `allreduce_fusion()` validates MXFP8 arguments identically for both
backends.
- Like the dynamic FP8 patterns, these patterns do not materialize
`allreduce_out`, so `allreduce_fusion()` no longer allocates an unused
output for them. As with the other quant patterns, the MNNVL path
returns `quant_out`.

**Performance.** End-to-end decode in vLLM: MiniMax-M3 NVFP4, B300 TP4,
8k input / 1k output, concurrency 1, EAGLE3 with 3 speculative tokens.
The only change between arms is this fusion; it is applied to FlashInfer
0.7.0 with the same device code.

| allreduce backend | TPOT p50, unfused | TPOT p50, fused | Δ |
|---|---|---|---|
| TRT-LLM | 2.241 ms | 2.208 ms | **−1.5%** |
| MNNVL | 2.190 ms | 2.142 ms | **−2.2%** |

A repeat of the unfused TRT-LLM arm came within 0.2%. Per call, on B200
decode, the MXFP8 tail adds about 0.5 µs to the fused allreduce at 4
tokens. In exchange, a standalone `mxfp8_quantize` launch (1.6–1.8 µs
plus its launch gap) leaves the critical path.

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

New tests cover world sizes 2/4/8, bf16 and fp16, hidden 1056–7168,
1–300 tokens, both scale layouts, and with and without `norm_out`:
- `tests/comm/test_trtllm_allreduce_fusion_mxfp8.py`:
  - one-shot and two-shot;
- quant, scale, residual and norm compared against `kARResidualRMSNorm`
followed by `mxfp8_quantize(cute-dsl)`;
- the unified `allreduce_fusion()` path (return value, layouts) and
argument validation.

Quant and scale bytes are identical except for isolated one-code
differences. These occur where the separate reference launch reduces the
RMS sum in a different order, which moves a norm value by one ulp across
an E4M3 rounding boundary.
- `tests/comm/test_trtllm_mnnvl_allreduce_mxfp8.py`:
  - one-shot and two-shot;
- quant and scale bytes bit-exact against `mxfp8_quantize(cute-dsl)` of
the kernel's own norm output;
- the norm within one ulp of a separate MNNVL `kARResidualRMSNorm`
launch;
  - argument validation.

GPU results. JIT-compiled from source in a torch 2.13 / CUDA 13.0
container:

| test | B200 (SM100) ×8 | B300 (SM103) ×8 |
|---|---|---|
| `test_trtllm_allreduce_fusion_mxfp8.py` (new) | 8 passed | 8 passed |
| `test_trtllm_mnnvl_allreduce_mxfp8.py` (new) | 6 passed | 6 passed |
| `test_trtllm_mnnvl_allreduce.py`, torchrun, 4 ranks (existing) | 300
passed | 300 passed |
| `test_trtllm_mnnvl_allreduce.py -k quant`, torchrun, 8 ranks
(existing) | 16 passed | 16 passed |
| `test_trtllm_allreduce_fusion.py` (existing, all patterns) | 131
passed | — |
| `test_trtllm_allreduce_fusion_group_fp8_quant.py` (existing) | 4
passed | — |

`test_trtllm_allreduce_dynamic_fp8_quant.py` fails the same 9 cases with
and without this PR, on the same node and container.

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

- Pattern value 12 is already `kMoEFinalizeARResidualRMSNormFP8Quant`,
so the new patterns are 13 and 14.
- The main design point is the padded scale rows left unwritten (see
Implementation). If you'd rather have the buffer fully defined, zeroing
could move to a parallel pass, at some cost for small token counts.
- The MNNVL CTA/cluster adjustment applies only to MXFP8 and changes no
other pattern's launch configuration.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added MXFP8 quantization support for fused all-reduce, residual
addition, and RMSNorm, with optional norm output.
* Supports linear and swizzled scale layouts across TRT-LLM and MNNVL
execution paths.
* MXFP8 outputs and scale buffers are validated for required shapes,
sizes, and data types. MXFP8 does not require an output-scale input.
  * Requires the hidden dimension to be divisible by 32.
* **Tests**
* Added coverage for MXFP8 results, scale layouts, optional norm output,
execution modes, and invalid buffer configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Edwin Mascarenhas <emascarenhas@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [75d4c6e](https://github.com/flashinfer-ai/flashinfer/commit/75d4c6e61ddc388151416818ca2d0ae930676089)

- **作者**: Lain
- **时间**: 2026-10-23T18:32:09Z
- **提交信息**: fix(moe): fix trtllm moe workspace query; expose tile size (#7025)

<!-- .github/pull_request_template.md -->

## 📌 Description

A follow up pr for #6825.

- Fix the issue that fp8 unshuffled trtllm moe workspace query that
returns 0. Add more unit tests.
- Expose tile size and config index in the query helper.

Current limitation: `do_finalize=False` is not supported yet.

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
* Workspace-size queries can now target a specific supported tactic;
queries without one continue to report the maximum across supported
tiles.
* **Bug Fixes**
* Improved workspace-size reporting across quantization modes, routing
methods, and configuration choices.
* Unsupported tiles and invalid tactics now return zero or are rejected,
preventing misleading workspace-size results.
* Verified that buffers sized for selected tactics support execution and
that routing modes produce matching outputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: siyuanf <siyuanf@nvidia.com>

### [3f39897](https://github.com/flashinfer-ai/flashinfer/commit/3f398977d75b4017cbd4c00824a5108017aade06)

- **作者**: Daniel Stokes
- **时间**: 2026-10-23T16:28:55Z
- **提交信息**: perf(MegaMOE): Add support for persistent TopK kernel and explicitly skipping CuTe-DSL finalize kernel (#5666)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
This imports the latest CuTe-DSL MegaMOE, which includes an optimized
CuTe-DSL finalize kernel, as well as an official API to skip the
finalize and perform a custom one


BREAKING CHANGE: Upstream MegaMOE now requires 128-element aligned
hidden size. This means models such as GPT-OSS need padding to work.


<details><summary>Agent Summary of name changes</summary>

<h3 aria-level="6" style="unicode-bidi: plaintext; color: rgb(191, 191,
191); font-family: -apple-system, &quot;system-ui&quot;, &quot;Segoe
UI&quot;, Roboto, sans-serif; font-style: normal;
font-variant-ligatures: normal; font-variant-caps: normal;
letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px;
text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color:
initial;">1.<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size: 0.9em;">do_finalize:
bool</code><span> </span>replaced by<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">finalize_mode: FinalizeMode</code></h3><p style="white-space:
pre-wrap; margin-top: 0.1em; margin-bottom: 0.2em; unicode-bidi:
plaintext; color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-size: 13px; font-style: normal; font-variant-ligatures: normal;
font-variant-caps: normal; font-weight: 400; letter-spacing: normal;
orphans: 2; text-align: start; text-indent: 0px; text-transform: none;
widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
background-color: rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">The old
keyword now raises <code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size: 0.9em;">TypeError</code>. A bool
passed positionally is caught by <code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">validate_finalize_mode</code> and raises <code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">TypeError</code>.</p>
Config | Old | New
-- | -- | --
Sm100_Bf16_Bf16_Bf16_Cutedsl_MegaMoeConfig | do_finalize=True |
finalize_mode=AUTO; accepts AUTO, DEFAULT, NONE
Sm100_Bf16_Nvfp4_Bf16_Cutedsl_MegaMoeConfig | do_finalize=True |
finalize_mode=AUTO; accepts AUTO, DEFAULT, NONE
Sm100_Nvfp4_Nvfp4_Bf16_Cutedsl_MegaMoeConfig | do_finalize=True |
finalize_mode=AUTO; accepts all modes

<h3 aria-level="6" style="unicode-bidi: plaintext; color: rgb(191, 191,
191); font-family: -apple-system, &quot;system-ui&quot;, &quot;Segoe
UI&quot;, Roboto, sans-serif; font-style: normal;
font-variant-ligatures: normal; font-variant-caps: normal;
letter-spacing: normal; orphans: 2; text-align: start; text-indent: 0px;
text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">3.
Positional construction silently shifts (no error)</h3><p
style="white-space: pre-wrap; margin-top: 0.1em; margin-bottom: 0.2em;
unicode-bidi: plaintext; color: rgb(191, 191, 191); font-family:
-apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto,
sans-serif; font-size: 13px; font-style: normal; font-variant-ligatures:
normal; font-variant-caps: normal; font-weight: 400; letter-spacing:
normal; orphans: 2; text-align: start; text-indent: 0px; text-transform:
none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
background-color: rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">These
configs are plain <code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size: 0.9em;">@dataclass</code> (not <code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">kw_only</code>), and new fields were inserted mid-list.
Positional calls will bind values to the wrong fields without any
error.</p><ul style="padding-inline-start: 2em; color: rgb(191, 191,
191); font-family: -apple-system, &quot;system-ui&quot;, &quot;Segoe
UI&quot;, Roboto, sans-serif; font-size: 13px; font-style: normal;
font-variant-ligatures: normal; font-variant-caps: normal; font-weight:
400; letter-spacing: normal; orphans: 2; text-align: start; text-indent:
0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;"><li
style="unicode-bidi: plaintext;"><strong><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">Sm100_Nvfp4_Nvfp4_Bf16_Cutedsl_MegaMoeConfig</code>:</strong><span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">num_valid_tokens_tensor</code><span> </span>now sits
between<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">combine_dtype</code><span> </span>and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">input_norm_const</code>. Every positional argument
from<span> </span><code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size:
0.9em;">input_norm_const</code><span> </span>onward moves by one
slot:<span> </span><code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size:
0.9em;">fc1_alpha</code>,<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">fc2_alpha</code>,<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">fc1_norm_const</code>,<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">knobs</code>,<span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size: 0.9em;">swiglu_*</code>, and so
on.</li><li style="unicode-bidi: plaintext;"><strong><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">Sm100_Mxfp8_Mxfp8_Bf16_Cutedsl_MegaMoeConfig</code>:</strong><span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">finalize_mode</code><span> </span>and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">num_valid_tokens_tensor</code><span> </span>now sit
between<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">enable_in_kernel_fc2_reduce</code><span> </span>and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">knobs</code>.<span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">knobs</code>,<span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">kernel_variant</code>,<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">mma_tiler_mnk</code>,<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">cluster_shape_mn</code><span> </span>and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">schedule_policy</code><span> </span>move by two slots.</li><li
style="unicode-bidi: plaintext;"><strong>BF16 and BF16×MXFP8
configs:</strong><span> </span>the new fields were appended at the end,
so these are safe.</li></ul><h3 aria-level="6" style="unicode-bidi:
plaintext; color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-style: normal; font-variant-ligatures: normal; font-variant-caps:
normal; letter-spacing: normal; orphans: 2; text-align: start;
text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">4. Knob
cache format version 1 → 2, shared by all backends</h3><p
style="white-space: pre-wrap; margin-top: 0.1em; margin-bottom: 0.2em;
unicode-bidi: plaintext; color: rgb(191, 191, 191); font-family:
-apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto,
sans-serif; font-size: 13px; font-style: normal; font-variant-ligatures:
normal; font-variant-caps: normal; font-weight: 400; letter-spacing:
normal; orphans: 2; text-align: start; text-indent: 0px; text-transform:
none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
background-color: rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">The
version is now centralised as <code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size: 0.9em;">KNOB_CACHE_VERSION =
2</code> in <code style="font-family: monospace; color: rgb(140, 140,
140); background: none 0% 0% / auto repeat scroll padding-box border-box
rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px; word-break:
break-word; font-size: 0.9em;">core/tuning.py</code>. It applies to the
SM100 CuTe-DSL, SM100/SM107 "next", SM90 pull-style and SM120 Cake
caches, which all share <code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">FLASHINFER_MOE_EP_KNOB_CACHE</code> (default <code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">~/.cache/flashinfer/moe_ep_knob_cache.json</code>).</p><ul
style="padding-inline-start: 2em; color: rgb(191, 191, 191);
font-family: -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;,
Roboto, sans-serif; font-size: 13px; font-style: normal;
font-variant-ligatures: normal; font-variant-caps: normal; font-weight:
400; letter-spacing: normal; orphans: 2; text-align: start; text-indent:
0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;"><li
style="unicode-bidi: plaintext;"><strong>Existing tuned entries are
silently ignored.</strong><span> </span>With<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">knobs=None</code>, every backend falls back to heuristics, which
is a possible perf regression until you re-tune.</li><li
style="unicode-bidi: plaintext;"><strong>SM100 NVFP4/BF16 entry keys
renamed:</strong><span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">apply_topk_in_fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>, and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">defer_topk_reduce</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">use_custom_finalize</code>. Hand-written or pre-shipped cache
files need regenerating.</li><li style="unicode-bidi:
plaintext;"><strong>Mixed versions clobber each
other.</strong><span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">record_knobs</code><span> </span>drops entries whose file
version doesn't match, then rewrites the file. Two FlashInfer versions
pointed at one cache file will repeatedly wipe each other's
entries.</li></ul><h3 aria-level="6" style="unicode-bidi: plaintext;
color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-style: normal; font-variant-ligatures: normal; font-variant-caps:
normal; letter-spacing: normal; orphans: 2; text-align: start;
text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">5. CLI
and benchmark flags and output keys</h3><ul style="padding-inline-start:
2em; color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-size: 13px; font-style: normal; font-variant-ligatures: normal;
font-variant-caps: normal; font-weight: 400; letter-spacing: normal;
orphans: 2; text-align: start; text-indent: 0px; text-transform: none;
widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
white-space: normal; background-color: rgb(25, 26, 27);
text-decoration-thickness: initial; text-decoration-style: initial;
text-decoration-color: initial;"><li style="unicode-bidi:
plaintext;"><strong><code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size: 0.9em;">python -m
flashinfer.moe_ep.tune</code>:</strong><span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--apply-topk-in-fc1</code><span> </span>/<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--no-apply-topk-in-fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--apply-routing-weights-before-fc2</code><span> </span>/<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--no-…</code>.<span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">--do-finalize</code><span> </span>is unchanged.</li><li
style="unicode-bidi: plaintext;"><strong><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">benchmarks/bench_cute_dsl_moe_distributed.py</code>:</strong><span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--apply-topk-in-fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">--apply-routing-weights-before-fc2</code>.</li><li
style="unicode-bidi: plaintext;"><strong>Benchmark JSON
output:</strong><span> </span>the<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_topk_in_fc1</code><span> </span>key
became<span> </span><code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>, both in the
per-iteration result records and in<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">MEGAMOE_TACTIC_JSON</code>. Any downstream parsers will need
updating.</li></ul><h3 aria-level="6" style="unicode-bidi: plaintext;
color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-style: normal; font-variant-ligatures: normal; font-variant-caps:
normal; letter-spacing: normal; orphans: 2; text-align: start;
text-indent: 0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">6.
Internal surfaces (only if someone imports past the<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">moe_ep</code><span> </span>boundary)</h3><p style="white-space:
pre-wrap; margin-top: 0.1em; margin-bottom: 0.2em; unicode-bidi:
plaintext; color: rgb(191, 191, 191); font-family: -apple-system,
&quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto, sans-serif;
font-size: 13px; font-style: normal; font-variant-ligatures: normal;
font-variant-caps: normal; font-weight: 400; letter-spacing: normal;
orphans: 2; text-align: start; text-indent: 0px; text-transform: none;
widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
background-color: rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;"><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">moe_ep/__init__.py</code> documents <code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">kernel_src</code> and <code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size: 0.9em;">cute_dsl</code> as
internal, but these changes will break direct importers:</p><ul
style="padding-inline-start: 2em; color: rgb(191, 191, 191);
font-family: -apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;,
Roboto, sans-serif; font-size: 13px; font-style: normal;
font-variant-ligatures: normal; font-variant-caps: normal; font-weight:
400; letter-spacing: normal; orphans: 2; text-align: start; text-indent:
0px; text-transform: none; widows: 2; word-spacing: 0px;
-webkit-text-stroke-width: 0px; white-space: normal; background-color:
rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;"><li
style="unicode-bidi: plaintext;"><strong>SM100
CuTe-DSL<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">kernel_src</code>:</strong><ul style="padding-inline-start:
2em;"><li style="unicode-bidi: plaintext;"><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">get_symm_buffer_for_mega_moe(...)</code><span> </span>and the
bf16-nvfp4<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">cute_dsl</code><span> </span>frontend config:<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_topk_in_fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>, and<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">defer_topk_reduce</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">use_custom_finalize</code>.</li><li style="unicode-bidi:
plaintext;">Frontend method<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">deferred_topk_reduce_workspace()</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">custom_finalize_workspace()</code>.</li><li style="unicode-bidi:
plaintext;">Knob-cache helpers (<code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">lookup_knobs</code><span> </span>and friends) take the same
renamed keyword arguments.</li></ul></li><li style="unicode-bidi:
plaintext;"><strong>SM90 FP8 pull-style shim:</strong><span> </span>the
config field<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">apply_topk_in_fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>. The SM90 MXFP4/BF16
shims still use the old name.</li><li style="unicode-bidi:
plaintext;"><strong>SM107<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">make_workspace_config</code>:</strong><span> </span>the
keyword<span> </span><code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">apply_topk_at_fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>.</li><li
style="unicode-bidi: plaintext;"><strong>Compiled kernel name
suffix:</strong><span> </span><code style="font-family: monospace;
color: rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">_topk_fc1</code><span> </span>became<span> </span><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">_routing_weights_before_fc2</code>, so cached CuTe-DSL artifacts
recompile once.</li><li style="unicode-bidi: plaintext;"><strong><code
style="font-family: monospace; color: rgb(140, 140, 140); background:
none 0% 0% / auto repeat scroll padding-box border-box rgb(38, 38, 38);
padding: 2px 4px; border-radius: 3px; word-break: break-word; font-size:
0.9em;">kernel_helpers.compute_megamoe_reference_*</code>:</strong><span> </span>these
are now wrappers that take<span> </span><code style="font-family:
monospace; color: rgb(140, 140, 140); background: none 0% 0% / auto
repeat scroll padding-box border-box rgb(38, 38, 38); padding: 2px 4px;
border-radius: 3px; word-break: break-word; font-size:
0.9em;">apply_routing_weights_before_fc2</code>.</li></ul><p
style="white-space: pre-wrap; margin-top: 0.1em; margin-bottom: 0.2em;
unicode-bidi: plaintext; color: rgb(191, 191, 191); font-family:
-apple-system, &quot;system-ui&quot;, &quot;Segoe UI&quot;, Roboto,
sans-serif; font-size: 13px; font-style: normal; font-variant-ligatures:
normal; font-variant-caps: normal; font-weight: 400; letter-spacing:
normal; orphans: 2; text-align: start; text-indent: 0px; text-transform:
none; widows: 2; word-spacing: 0px; -webkit-text-stroke-width: 0px;
background-color: rgb(25, 26, 27); text-decoration-thickness: initial;
text-decoration-style: initial; text-decoration-color: initial;">The new
<code style="font-family: monospace; color: rgb(140, 140, 140);
background: none 0% 0% / auto repeat scroll padding-box border-box
rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px; word-break:
break-word; font-size: 0.9em;">finalize_mode</code> field comments in
the configs say "NONE makes <code style="font-family: monospace; color:
rgb(140, 140, 140); background: none 0% 0% / auto repeat scroll
padding-box border-box rgb(38, 38, 38); padding: 2px 4px; border-radius:
3px; word-break: break-word; font-size:
0.9em;">MoEEpMegaLayer.forward</code> return per-route outputs". In fact
<code style="font-family: monospace; color: rgb(140, 140, 140);
background: none 0% 0% / auto repeat scroll padding-box border-box
rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px; word-break:
break-word; font-size: 0.9em;">forward()</code> raises in that mode, and
you have to call <code style="font-family: monospace; color: rgb(140,
140, 140); background: none 0% 0% / auto repeat scroll padding-box
border-box rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px;
word-break: break-word; font-size: 0.9em;">forward_unfinalized()</code>.
The <code style="font-family: monospace; color: rgb(140, 140, 140);
background: none 0% 0% / auto repeat scroll padding-box border-box
rgb(38, 38, 38); padding: 2px 4px; border-radius: 3px; word-break:
break-word; font-size: 0.9em;">FinalizeMode</code> docstring has it
right.</p>

<p>



</p>
</details> 
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

* **New Features**
* Added persistent top-k reduction and configurable reduction handling
for supported MegaMoE configurations.
* Added MXFP8 column-wise requantization, SiTU activation support, and
optional tail-split scheduling.
* Expanded the P2P benchmark with configurable warp counts and support
for additional GPU architectures.

* **Updates**
* Renamed the routing-weight placement setting to clarify when weights
are applied relative to FC2; configuration and benchmark output use the
updated name.
* Updated MegaMoE output handling to use a single output activation
buffer.

* **Bug Fixes**
* Improved MXFP8 scale handling and mismatch detection, including
reporting non-finite values as mismatches.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Anerudhan Gopal <agopal@nvidia.com>

### [89009ad](https://github.com/flashinfer-ai/flashinfer/commit/89009ad44586710d5cb94f15113929c6a8728af9)

- **作者**: eigen
- **时间**: 2026-10-23T13:57:45Z
- **提交信息**: perf(cake_all_gather_matmul): SM103a CTA-pair twins for the 512-row K-major N=2560 calls at world size 4 (#7083)

`cake_all_gather_matmul` all-gathers each rank's row-sharded activation
and multiplies it by a `[K, N]` weight held either as a contiguous `[K,
N]` tensor (N-major) or as the transposed view of a contiguous `[N, K]`
parameter (K-major). Cake ships it in bf16 and fp16, K-major and N-major
weights, world sizes 2, 4 and 8, two main-tile widths and two transport
routes (copy engine, SM push). This PR delivers one SM103a (B300)
routing-table change: the K-major calls with exactly 512 padded rows and
N = 2560 at world size 4 now run the CTA-pair main program (the `_cg2`
twin) instead of the one-CTA main program, in bf16 and in fp16. The bf16
world-size-4 K-major `_cg2` twin already ships on both architectures, so
this PR only routes the new point to it. The fp16 world-size-4 K-major
class gets its first `_cg2` twin, on SM103a only, and that twin is the
one kernel program this PR adds. No shipped kernel program is modified
or removed, and SM100a routes and programs are unchanged. Against the
previous Cake version of this kernel, which is what FlashInfer ships for
SM103a today, the speedup is 1.0767 to 1.1143 across both data types and
both nodes.

| Shape per rank, M × N (K = 8192, K-major weights) | Dtype | Node |
Previous version (µs) | This PR (µs) | Speedup |
|---|---|---|---:|---:|---:|
| 512 × 2560, world size 4 (Llama-3.1-70B TP4 QKV) | bf16 | node 1 |
115.4 | 106.2 | 1.0855 |
| 512 × 2560, world size 4 (Llama-3.1-70B TP4 QKV) | bf16 | node 2 |
114.4 | 105.3 | 1.0902 |
| 512 × 2560, world size 4 | fp16 | node 1 | 114.8 | 104.0 | 1.1143 |
| 512 × 2560, world size 4 | fp16 | node 2 | 115.3 | 107.3 | 1.0767 |

NVIDIA B300 (SM103a), CUDA 13.3, two 8×B300 nodes, one rank per GPU;
latency = median over calls of the slowest rank's time. Speedup > 1
means this PR is faster. Each speedup is the median over interleaved
measurement groups of the per-group ratio previous / this PR, so it is
not the quotient of the two medians beside it. Every ratio is outside
its node's noise band (0.0144 / 0.0149, node 1 / node 2 in ln; each
node's band applies to both data types).

Cake also ships `_n128` (128-wide), CTA-pair `_cg2`, spill-split pair
`_cg2s2` (world sizes 4 and 8 on both architectures) and `_ks4`
per-K-slice readiness (`sm_103a` only) twins of its main programs, a
`_po` peer-outer tile-order form of the world-size-4 bf16 K-major main
for one 128-row shape (`sm_103a` only), and the push programs
`peer_push` and `peer_push_wide` (both architectures) with the
`peer_push_wide_ks4` twin (`sm_103a` only); the family ships on
`sm_100a` (B200) and `sm_103a` (B300).

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8ec9464](https://github.com/flashinfer-ai/flashinfer/commit/8ec9464ce81d81c9e3670aa09acd1a8780f83695)

- **作者**: eigen
- **时间**: 2026-10-23T10:05:33Z
- **提交信息**: feat(cake_vsa_sm90): add Sage-FP8 variant of the variable block-sparse attention forward (#7092)

Cake's variable block-sparse attention forward for Hopper (sm_90a) is
called through
`flashinfer.sparse.VariableBlockSparseAttentionWrapper(backend="cake")`.
It supports HND layout, head_dim 128, 64-token blocks, 1 to 64 KV blocks
per query block, ragged and uniform block masks, any finite softmax
scale and the same number of query and KV heads, and it is non-causal.
Planning is separate from running, and each run is one kernel launch
that can be captured in a CUDA graph. The kernel now has two data-type
variants. BF16 is the version already shipped, and this PR does not
change it. Sage-FP8 is the variant this PR adds. In each variant the
planner chooses among 19 programs: 4 persistent programs and 15 small
direct, DSM-cluster, split-KV and split-cluster programs. In the
Sage-FP8 variant, Q, K and V are `float8_e4m3fn` with Sage-style FP32
scales supplied by the caller: `q_scale` per token `(1, H, Sq)`,
`k_scale` per 16-token group `(1, H, ceil(Sk/16))` and `v_scale` per
channel `(H, 128)`. The softmax probabilities also enter the P·V product
as E4M3, and the output is BF16. With `backend="cake"` on sm_90a, the
wrapper accepts float8 q/k/v plus the three scale tensors. This scale
interface has the same form as the existing Sage-FP8 interface of the
`vsa_sm100_blk64` backend. The BF16 path and the public API names are
unchanged. The baseline is the previous Cake version of this kernel: the
BF16 variant run on the same unquantized BF16 inputs and measured in the
same process. Against that baseline, the geometric-mean speedups
(process a / process b) are 1.0868 / 1.0866 on b20, 1.1537 / 1.1549 on
ext33, 1.2238 / 1.2244 on real39, 1.1542 / 1.1439 on long45, and 1.1632
/ 1.1602 over all 137 rows. The 137 rows cover 124 distinct shapes,
because 13 shapes appear in two sets. A paired test finds this PR faster
on 136 of 137 rows in process a and on 137 of 137 rows in process b. The
one row that is not faster in process a is
`h1-m64-n64-k1-ragged0-scale0`, a 2.7 µs single-launch row: 2.752 µs
previous vs 2.720 µs this PR, but in one of the nine groups the paired
median difference was one 32 ns timer tick in the other direction, so
the paired test does not count the row as faster.

NVIDIA H100 80GB HBM3 (sm_90a), driver 535.216.03, CUDA 13.4 toolchain
(PyTorch 2.14.1+cu130), SM clock 1980 MHz (the long45 rows ran at 1830
MHz); each value is the median over 9 interleaved groups × 256 samples
with a cold L2 before every sample; "a / b" are two independent
processes; speedup = previous Cake median / this PR median; the timed
region is the attention launch only, and the Sage quantization of Q/K/V
is a separate kernel outside it.

**b20 (the 20 shapes of PR 5470)**

| shape | previous Cake, BF16 (µs) a / b | this PR, Sage-FP8 (µs) a / b
| speedup a / b |
|---|---|---|---|
| h1-m64-n64-k1-ragged0-scale0 | 2.752 / 2.768 | 2.720 / 2.688 | 1.0118
/ 1.0298 |
| h4-m256-n256-k1-ragged0-scale0 | 3.200 / 3.200 | 3.008 / 3.008 |
1.0638 / 1.0638 |
| h8-m256-n256-k3-ragged0-scale0 | 5.120 / 5.152 | 4.640 / 4.672 |
1.1034 / 1.1027 |
| h8-m1024-n1024-k4-ragged0-scale0 | 7.168 / 7.168 | 6.400 / 6.400 |
1.1200 / 1.1200 |
| h8-m1024-n1024-k12-ragged0-scale0 | 10.752 / 10.688 | 10.464 / 10.463
| 1.0275 / 1.0215 |
| h8-m2048-n2048-k8-ragged0-scale0 | 14.208 / 14.240 | 13.728 / 13.760 |
1.0350 / 1.0349 |
| h8-m2048-n2048-k16-ragged0-scale0 | 21.120 / 21.056 | 20.032 / 19.775
| 1.0543 / 1.0648 |
| h8-m4096-n4096-k16-ragged0-scale0 | 37.183 / 37.215 | 35.712 / 35.776
| 1.0412 / 1.0402 |
| h8-m4096-n4096-k32-ragged0-scale0 | 61.536 / 61.983 | 59.008 / 59.168
| 1.0428 / 1.0476 |
| h4-m512-n1024-k4-ragged0-scale0 | 5.856 / 5.888 | 5.248 / 5.280 |
1.1159 / 1.1152 |
| h4-m1024-n512-k4-ragged1-scale0 | 5.760 / 5.760 | 5.215 / 5.184 |
1.1045 / 1.1111 |
| h4-m1024-n1024-k8-ragged1-scale0 | 6.784 / 6.784 | 5.952 / 5.983 |
1.1398 / 1.1339 |
| h7-m4096-n4096-k16-ragged1-scale0 | 23.968 / 23.967 | 22.112 / 22.144
| 1.0839 / 1.0823 |
| h4-m512-n512-k4-ragged0-scale1 | 5.409 / 5.408 | 5.121 / 5.152 |
1.0562 / 1.0497 |
| h1-m1024-n1024-k16-ragged0-scale0 | 6.048 / 5.952 | 5.696 / 5.632 |
1.0618 / 1.0568 |
| h7-m16384-n16384-k32-ragged0-scale0 | 224.510 / 224.190 | 198.174 /
197.086 | 1.1329 / 1.1375 |
| h7-m32768-n32768-k64-ragged0-scale0 | 905.755 / 890.105 | 780.972 /
786.617 | 1.1598 / 1.1316 |
| h7-m65536-n65536-k64-ragged0-scale0 | 1867.713 / 1862.928 | 1648.147 /
1634.961 | 1.1332 / 1.1394 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3272.724 / 3254.952 | 2878.168
/ 2883.194 | 1.1371 / 1.1289 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1648.516 / 1645.332 | 1459.253
/ 1448.485 | 1.1297 / 1.1359 |

**ext33 (33 banded and extended shapes)**

| shape | previous Cake, BF16 (µs) a / b | this PR, Sage-FP8 (µs) a / b
| speedup a / b |
|---|---|---|---|
| h16-m1024-n8192-k1-ragged0-scale0 | 9.152 / 9.184 | 6.528 / 6.528 |
1.4020 / 1.4069 |
| h8-m512-n4096-k2-ragged0-scale0 | 5.792 / 5.792 | 5.024 / 5.025 |
1.1529 / 1.1526 |
| h4-m2048-n4096-k6-ragged0-scale0 | 9.248 / 9.280 | 7.712 / 7.711 |
1.1992 / 1.2035 |
| h2-m4096-n4096-k5-ragged0-scale0 | 8.064 / 8.096 | 7.008 / 7.008 |
1.1507 / 1.1553 |
| h1-m2048-n4096-k20-ragged0-scale0 | 10.431 / 10.304 | 9.535 / 9.312 |
1.0940 / 1.1065 |
| h1-m1024-n4096-k24-ragged0-scale0 | 9.216 / 9.217 | 8.321 / 8.352 |
1.1076 / 1.1036 |
| h1-m512-n8192-k48-ragged0-scale0 | 10.752 / 10.656 | 9.632 / 9.568 |
1.1163 / 1.1137 |
| h1-m512-n8192-k64-ragged0-scale0 | 14.433 / 14.847 | 12.192 / 12.320 |
1.1838 / 1.2051 |
| h1-m256-n8192-k64-ragged0-scale0 | 14.080 / 14.304 | 11.408 / 11.584 |
1.2342 / 1.2348 |
| h1-m1024-n2048-k7-ragged0-scale0 | 5.152 / 5.152 | 4.704 / 4.704 |
1.0952 / 1.0952 |
| h1-m2048-n2048-k7-ragged0-scale0 | 6.080 / 6.112 | 5.568 / 5.728 |
1.0920 / 1.0670 |
| h1-m1024-n2048-k8-ragged0-scale0 | 5.248 / 5.249 | 4.704 / 4.704 |
1.1156 / 1.1159 |
| h1-m4096-n4096-k8-ragged0-scale0 | 7.008 / 7.008 | 6.528 / 6.401 |
1.0735 / 1.0948 |
| h1-m4096-n4096-k7-ragged1-scale0 | 6.592 / 6.592 | 5.825 / 5.855 |
1.1317 / 1.1259 |
| h1-m1024-n4096-k9-ragged0-scale0 | 6.175 / 6.143 | 5.536 / 5.536 |
1.1154 / 1.1096 |
| h1-m1024-n4096-k12-ragged0-scale0 | 7.328 / 7.328 | 6.464 / 6.464 |
1.1337 / 1.1337 |
| h1-m512-n4096-k16-ragged0-scale0 | 6.464 / 6.432 | 5.920 / 5.888 |
1.0919 / 1.0924 |
| h1-m512-n4096-k18-ragged0-scale0 | 6.464 / 6.464 | 5.856 / 5.824 |
1.1038 / 1.1099 |
| h1-m1024-n4096-k16-ragged0-scale0 | 6.688 / 6.656 | 6.080 / 6.048 |
1.1000 / 1.1005 |
| h2-m1024-n4096-k8-ragged0-scale0 | 7.040 / 7.040 | 6.272 / 6.303 |
1.1224 / 1.1169 |
| h1-m1024-n4096-k12-ragged0-scale0-uneven | 6.976 / 6.944 | 6.368 /
6.336 | 1.0955 / 1.0960 |
| h1-m2048-n4096-k20-ragged0-scale0-uneven | 9.344 / 9.408 | 7.968 /
8.032 | 1.1727 / 1.1713 |
| h4-m2048-n4096-k6-ragged0-scale0-uneven | 8.768 / 8.864 | 7.392 /
7.392 | 1.1861 / 1.1991 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven | 24.736 / 24.640 | 22.784 /
22.719 | 1.0857 / 1.0846 |
| h32-m2048-n2048-k8-ragged0-scale0 | 41.952 / 42.015 | 40.128 / 40.175
| 1.0455 / 1.0458 |
| h16-m4096-n16384-k16-ragged0-scale0 | 85.695 / 85.567 | 70.047 /
69.535 | 1.2234 / 1.2306 |
| h8-m1024-n32768-k64-ragged0-scale0 | 55.616 / 55.775 | 34.560 / 34.687
| 1.6093 / 1.6080 |
| h8-m2048-n32768-k48-ragged1-scale0 | 56.384 / 56.128 | 41.375 / 41.215
| 1.3628 / 1.3618 |
| h32-m8192-n8192-k24-ragged0-scale0 | 380.607 / 381.245 | 343.519 /
346.430 | 1.1080 / 1.1005 |
| h16-m8192-n8192-k5-ragged0-scale0 | 61.568 / 61.375 | 54.815 / 54.399
| 1.1232 / 1.1282 |
| h8-m8192-n8192-k2-ragged0-scale0 | 27.952 / 27.951 | 22.016 / 22.112 |
1.2696 / 1.2641 |
| h8-m4096-n4096-k64-ragged0-scale1 | 107.455 / 107.296 | 101.120 /
100.671 | 1.0626 / 1.0658 |
| h8-m4096-n4096-k20-ragged1-scale0 | 28.992 / 29.088 | 27.136 / 27.168
| 1.0684 / 1.0707 |

**real39 (39 serving shapes)**

| shape | previous Cake, BF16 (µs) a / b | this PR, Sage-FP8 (µs) a / b
| speedup a / b |
|---|---|---|---|
| h8-m512-n512-k1-ragged0-scale0 | 4.192 / 4.192 | 3.584 / 3.584 |
1.1696 / 1.1696 |
| h8-m512-n1024-k2-ragged0-scale0 | 5.376 / 5.376 | 4.672 / 4.703 |
1.1507 / 1.1431 |
| h16-m256-n512-k2-ragged1-scale0 | 5.408 / 5.376 | 4.736 / 4.736 |
1.1419 / 1.1351 |
| h8-m1024-n2048-k4-ragged0-scale0 | 8.320 / 8.352 | 6.944 / 6.976 |
1.1982 / 1.1972 |
| h8-m1024-n4096-k6-ragged0-scale0 | 11.392 / 11.392 | 8.128 / 8.128 |
1.4016 / 1.4016 |
| h4-m2048-n2048-k5-ragged0-scale0 | 7.840 / 7.872 | 7.168 / 7.136 |
1.0938 / 1.1031 |
| h8-m256-n4096-k8-ragged0-scale0 | 8.064 / 8.064 | 6.816 / 6.848 |
1.1831 / 1.1776 |
| h8-m256-n2048-k8-ragged0-scale0 | 7.488 / 7.583 | 6.720 / 6.752 |
1.1143 / 1.1231 |
| h4-m256-n2048-k7-ragged0-scale0 | 5.856 / 5.856 | 5.120 / 5.120 |
1.1438 / 1.1438 |
| h8-m512-n4096-k8-ragged0-scale0 | 10.048 / 10.048 | 8.064 / 8.064 |
1.2460 / 1.2460 |
| h16-m256-n2048-k7-ragged1-scale0 | 8.448 / 8.448 | 7.136 / 7.104 |
1.1839 / 1.1892 |
| h8-m256-n4096-k9-ragged0-scale0 | 8.544 / 8.608 | 6.784 / 6.768 |
1.2594 / 1.2719 |
| h4-m512-n2048-k9-ragged0-scale0 | 6.912 / 6.944 | 6.336 / 6.368 |
1.0909 / 1.0905 |
| h8-m512-n4096-k12-ragged0-scale0 | 11.840 / 11.872 | 8.480 / 8.448 |
1.3962 / 1.4053 |
| h8-m256-n2048-k10-ragged0-scale0 | 8.128 / 8.128 | 7.072 / 7.104 |
1.1493 / 1.1441 |
| h8-m256-n4096-k16-ragged0-scale0 | 12.480 / 12.512 | 9.568 / 9.503 |
1.3043 / 1.3166 |
| h4-m256-n4096-k14-ragged0-scale0 | 7.424 / 7.424 | 6.752 / 6.752 |
1.0995 / 1.0995 |
| h4-m256-n8192-k18-ragged0-scale0 | 9.088 / 9.216 | 7.680 / 7.680 |
1.1833 / 1.2000 |
| h8-m128-n4096-k17-ragged0-scale0 | 8.704 / 8.576 | 7.328 / 7.264 |
1.1878 / 1.1806 |
| h4-m256-n8192-k24-ragged0-scale0 | 11.200 / 11.168 | 9.184 / 9.152 |
1.2195 / 1.2203 |
| h8-m256-n16384-k32-ragged0-scale0 | 20.160 / 20.096 | 18.144 / 18.112
| 1.1111 / 1.1095 |
| h4-m512-n16384-k20-ragged0-scale0 | 15.104 / 14.912 | 11.072 / 10.912
| 1.3642 / 1.3666 |
| h8-m128-n32768-k64-ragged0-scale0 | 28.768 / 28.832 | 21.168 / 21.120
| 1.3590 / 1.3652 |
| h4-m256-n8192-k48-ragged0-scale0 | 16.960 / 16.192 | 11.936 / 11.744 |
1.4209 / 1.3787 |
| h8-m256-n4096-k12-ragged0-scale0-uneven | 7.776 / 7.776 | 6.944 /
6.912 | 1.1198 / 1.1250 |
| h8-m512-n8192-k24-ragged0-scale0-uneven | 14.176 / 14.176 | 10.752 /
10.784 | 1.3185 / 1.3145 |
| h8-m256-n4096-k8-ragged0-scale1 | 7.936 / 7.904 | 6.943 / 6.976 |
1.1430 / 1.1330 |
| h32-m2048-n2048-k8-ragged0-scale0 | 41.952 / 42.015 | 40.128 / 40.175
| 1.0455 / 1.0458 |
| h16-m4096-n16384-k16-ragged0-scale0 | 85.695 / 85.567 | 70.047 /
69.535 | 1.2234 / 1.2306 |
| h8-m1024-n32768-k64-ragged0-scale0 | 55.616 / 55.775 | 34.560 / 34.687
| 1.6093 / 1.6080 |
| h8-m2048-n32768-k48-ragged1-scale0 | 56.384 / 56.128 | 41.375 / 41.215
| 1.3628 / 1.3618 |
| h32-m8192-n8192-k24-ragged0-scale0 | 380.607 / 381.245 | 343.519 /
346.430 | 1.1080 / 1.1005 |
| h16-m8192-n8192-k5-ragged0-scale0 | 61.568 / 61.375 | 54.815 / 54.399
| 1.1232 / 1.1282 |
| h8-m4096-n4096-k64-ragged0-scale1 | 107.455 / 107.296 | 101.120 /
100.671 | 1.0626 / 1.0658 |
| h8-m4096-n4096-k20-ragged1-scale0 | 28.992 / 29.088 | 27.136 / 27.168
| 1.0684 / 1.0707 |
| h8-m4096-n4096-k24-ragged0-scale0-uneven | 24.736 / 24.640 | 22.784 /
22.719 | 1.0857 / 1.0846 |
| h16-m1024-n8192-k12-ragged0-scale0 | 29.632 / 29.984 | 18.976 / 19.040
| 1.5616 / 1.5748 |
| h32-m512-n8192-k16-ragged0-scale0 | 43.360 / 43.392 | 25.967 / 26.048
| 1.6698 / 1.6658 |
| h16-m1024-n8192-k1-ragged0-scale0 | 9.152 / 9.184 | 6.528 / 6.528 |
1.4020 / 1.4069 |

**long45 (45 long shapes)**

| shape | previous Cake, BF16 (µs) a / b | this PR, Sage-FP8 (µs) a / b
| speedup a / b |
|---|---|---|---|
| h3-m32768-n32768-k32-ragged0-scale0 | 211.264 / 206.943 | 172.031 /
173.119 | 1.2281 / 1.1954 |
| h3-m32768-n32768-k64-ragged0-scale0 | 378.333 / 378.765 | 321.774 /
322.493 | 1.1758 / 1.1745 |
| h3-m32768-n32768-k64-ragged1-scale0 | 207.215 / 205.198 | 177.408 /
177.694 | 1.1680 / 1.1548 |
| h3-m75648-n75648-k32-ragged0-scale0 | 486.108 / 486.764 | 408.285 /
407.725 | 1.1906 / 1.1939 |
| h3-m75648-n75648-k64-ragged0-scale0 | 963.453 / 939.946 | 803.006 /
809.227 | 1.1998 / 1.1615 |
| h3-m75648-n75648-k64-ragged1-scale0 | 491.373 / 491.741 | 401.661 /
402.205 | 1.2234 / 1.2226 |
| h3-m109632-n109632-k32-ragged0-scale0 | 745.135 / 734.683 | 614.910 /
620.812 | 1.2118 / 1.1834 |
| h3-m109632-n109632-k64-ragged0-scale0 | 1387.366 / 1385.031 | 1199.111
/ 1195.912 | 1.1570 / 1.1581 |
| h3-m109632-n109632-k64-ragged1-scale0 | 719.262 / 710.748 | 601.231 /
605.212 | 1.1963 / 1.1744 |
| h7-m32768-n32768-k32-ragged0-scale0 | 469.965 / 470.653 | 398.765 /
399.565 | 1.1786 / 1.1779 |
| h7-m32768-n32768-k64-ragged0-scale0 | 905.755 / 890.105 | 780.972 /
786.617 | 1.1598 / 1.1316 |
| h7-m32768-n32768-k64-ragged1-scale0 | 470.159 / 462.670 | 405.343 /
403.822 | 1.1599 / 1.1457 |
| h7-m75648-n75648-k32-ragged0-scale0 | 1139.833 / 1139.241 | 988.666 /
987.594 | 1.1529 / 1.1536 |
| h7-m75648-n75648-k64-ragged0-scale0 | 2206.479 / 2183.188 | 1922.894 /
1908.676 | 1.1475 / 1.1438 |
| h7-m75648-n75648-k64-ragged1-scale0 | 1129.673 / 1129.418 | 993.593 /
991.898 | 1.1370 / 1.1386 |
| h7-m109632-n109632-k32-ragged0-scale0 | 1776.319 / 1701.414 | 1469.104
/ 1473.128 | 1.2091 / 1.1550 |
| h7-m109632-n109632-k64-ragged0-scale0 | 3272.724 / 3254.952 | 2878.168
/ 2883.194 | 1.1371 / 1.1289 |
| h7-m109632-n109632-k64-ragged1-scale0 | 1648.516 / 1645.332 | 1459.253
/ 1448.485 | 1.1297 / 1.1359 |
| h8-m32768-n32768-k32-ragged0-scale0 | 537.725 / 538.429 | 462.205 /
462.973 | 1.1634 / 1.1630 |
| h8-m32768-n32768-k64-ragged0-scale0 | 1041.392 / 1021.403 | 904.736 /
905.339 | 1.1510 / 1.1282 |
| h8-m32768-n32768-k64-ragged1-scale0 | 530.013 / 529.901 | 468.541 /
468.861 | 1.1312 / 1.1302 |
| h8-m75648-n75648-k32-ragged0-scale0 | 1320.239 / 1298.393 | 1124.672 /
1122.442 | 1.1739 / 1.1568 |
| h8-m75648-n75648-k64-ragged0-scale0 | 2497.793 / 2493.938 | 2190.595 /
2187.988 | 1.1402 / 1.1398 |
| h8-m75648-n75648-k64-ragged1-scale0 | 1309.728 / 1294.010 | 1137.695 /
1139.546 | 1.1512 / 1.1355 |
| h8-m109632-n109632-k32-ragged0-scale0 | 1953.477 / 1945.797 | 1697.525
/ 1681.734 | 1.1508 / 1.1570 |
| h8-m109632-n109632-k64-ragged0-scale0 | 3730.447 / 3728.812 | 3271.647
/ 3296.975 | 1.1402 / 1.1310 |
| h8-m109632-n109632-k64-ragged1-scale0 | 1881.638 / 1879.541 | 1676.614
/ 1663.895 | 1.1223 / 1.1296 |
| h10-m32768-n32768-k32-ragged0-scale0 | 681.167 / 677.293 | 573.920 /
582.685 | 1.1869 / 1.1624 |
| h10-m32768-n32768-k64-ragged0-scale0 | 1276.921 / 1275.369 | 1138.090
/ 1130.938 | 1.1220 / 1.1277 |
| h10-m32768-n32768-k64-ragged1-scale0 | 674.432 / 664.253 | 590.688 /
593.261 | 1.1418 / 1.1197 |
| h10-m75648-n75648-k32-ragged0-scale0 | 1626.199 / 1624.840 | 1413.288
/ 1415.096 | 1.1506 / 1.1482 |
| h10-m75648-n75648-k64-ragged0-scale0 | 3140.639 / 3123.425 | 2733.438
/ 2759.138 | 1.1490 / 1.1320 |
| h10-m75648-n75648-k64-ragged1-scale0 | 1578.743 / 1579.591 | 1395.736
/ 1397.432 | 1.1311 / 1.1304 |
| h10-m109632-n109632-k32-ragged0-scale0 | 2510.863 / 2424.483 |
2138.798 / 2141.765 | 1.1740 / 1.1320 |
| h10-m109632-n109632-k64-ragged0-scale0 | 4672.502 / 4668.262 |
4206.824 / 4206.041 | 1.1107 / 1.1099 |
| h10-m109632-n109632-k64-ragged1-scale0 | 2365.983 / 2342.277 |
2066.848 / 2088.822 | 1.1447 / 1.1213 |
| h12-m32768-n32768-k32-ragged0-scale0 | 809.372 / 808.812 | 711.789 /
709.453 | 1.1371 / 1.1401 |
| h12-m32768-n32768-k64-ragged0-scale0 | 1556.352 / 1533.449 | 1366.368
/ 1371.001 | 1.1390 / 1.1185 |
| h12-m32768-n32768-k64-ragged1-scale0 | 798.364 / 795.052 | 729.884 /
720.781 | 1.0938 / 1.1030 |
| h12-m75648-n75648-k32-ragged0-scale0 | 1973.824 / 1943.622 | 1707.440
/ 1717.272 | 1.1560 / 1.1318 |
| h12-m75648-n75648-k64-ragged0-scale0 | 3721.867 / 3716.940 | 3292.990
/ 3277.757 | 1.1302 / 1.1340 |
| h12-m75648-n75648-k64-ragged1-scale0 | 1943.264 / 1923.398 | 1709.824
/ 1725.431 | 1.1365 / 1.1147 |
| h12-m109632-n109632-k32-ragged0-scale0 | 2921.296 / 2919.153 |
2568.130 / 2593.745 | 1.1375 / 1.1255 |
| h12-m109632-n109632-k64-ragged0-scale0 | 5612.267 / 5587.635 |
4988.143 / 4994.007 | 1.1251 / 1.1189 |
| h12-m109632-n109632-k64-ragged1-scale0 | 2832.159 / 2820.177 |
2560.897 / 2519.794 | 1.1059 / 1.1192 |

Cake also ships the BF16 variant of this kernel on sm_90a, which this PR
leaves unchanged; the Sage-FP8 variable block-sparse family added here
ships on sm_90a only, and Cake's Sage-FP8 block-sparse attention for
Blackwell (`cake_sage_block_sparse_attention_backend`) is a separate
kernel that ships on sm_100a / sm_103a / sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Sage FP8 support for SM90 sparse attention, including
BF16-to-FP8 quantization, scale-aware planning, and BF16 outputs.
* Added FP8 support across attention routes and expanded public access
to FP8 quantization helpers and constants.
* **Bug Fixes**
  * Improved barrier parity handling in selected attention kernels.
* **Tests**
* Expanded coverage for FP8 accuracy, supported routes, validation,
graph replay, and quantization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [baddd51](https://github.com/flashinfer-ai/flashinfer/commit/baddd518c5ef277167684d3d0611f30c791203f0)

- **作者**: eigen
- **时间**: 2026-10-23T09:57:15Z
- **提交信息**: perf(cake_kda): faster context-parallel host path, wave-fill plan rule and capped graph replay, with grad- #7089 (#7097)

The Cake packed KDA kernel family, a chunked training backend for
documents packed into one sequence, has two variants: a single-device
variant, and a context-parallel (KCP) variant that splits the sequence
over the ranks of a distributed process group, passes the recurrent
state across ranks through affine state summaries, supports contiguous,
zigzag and per-document zigzag + ragged partition layouts as well as
saved-context and checkpoint-replay backward, and comes with the halo
variant of the causal conv1d + SiLU training backend. This PR makes the
already shipped context-parallel variant faster: the eager
context-parallel calls take a trimmed host path that reuses
call-independent host work across calls through bounded caches keyed on
object identity and host integers, with kernels, arguments and launch
order unchanged and results bitwise identical to those of the previous
host path. The per-rank parallel degree P is now set by a wave-fill plan
rule with a P = 1 tie: a rank with two or three fragments takes P = 1
when its longest-processing-time makespan at P = 1 is not above the
makespan at the occupancy P, and then needs no segment composition and
no backward re-walk. The variant also gains dedicated context-parallel
output and adjoint programs (the chunk output and output-backward
kernels that form each rank's output from the forward walk's state tapes
and the first value gradient of the adjoint walk, which the
single-device route no longer launches) and an opt-in CUDA-graph replay
(`graph="replay"`, default `"off"`) whose captured tape launches carry
the one-CTA-per-SM shared-memory carveout as a kernel-node attribute. On
NVIDIA GB300 (sm_103a), its speedup over the KDA context-parallel
training of flash-linear-attention (FLA KCP) ranges from 1.4640x to
2.7942x across all 144 configurations and both sessions.

Latency in ms, NVIDIA GB300 (sm_103a), CUDA 13.0, driver 580.159.03, H =
64 heads, median over steady iterations of the slowest rank, two
sessions s1 / s2 on different nodes; CP2 / CP4 on one node, CP8 on two
nodes, CP16 on four nodes of one NVL72 domain; B1 = module forward, B3 =
forward + checkpoint replay + backward; for the per-document layout the
FLA KCP baseline is the faster of FLA's two layouts (the arm is named in
each cell: fla_C = contiguous, fla_Z = zigzag).

| pack | CP | layout | boundary | Cake ms (s1 / s2) | FLA KCP ms (s1 /
s2, arm) | speedup vs FLA KCP (s1 / s2) |
|---|---|---|---|---|---|---|
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B1 = forward | 15.891 /
15.935 | 33.791 / 33.620 (fla_C) | 2.1264 / 2.1098 |
| Q1 (249,856 tok / 4 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 66.671 / 66.731 | 136.961 / 135.913 (fla_C) | 2.0543
/ 2.0367 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B1 = forward | 16.117 /
16.136 | 42.537 / 42.380 (fla_Z) | 2.6393 / 2.6264 |
| Q1 (249,856 tok / 4 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 67.415 / 67.404 | 164.317 / 163.090 (fla_Z) | 2.4374
/ 2.4196 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.159 / 16.203 | 33.910 / 33.647 (fla_C) | 2.0985 / 2.0767 |
| Q1 (249,856 tok / 4 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 67.202 / 67.226 | 137.010 /
136.063 (fla_C) | 2.0388 / 2.0240 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B1 = forward | 8.222 /
8.242 | 22.217 / 22.220 (fla_C) | 2.7019 / 2.6959 |
| Q1 (249,856 tok / 4 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.183 / 34.193 | 90.079 / 89.664 (fla_C) | 2.6352 /
2.6223 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B1 = forward | 8.502 / 8.528
| 22.156 / 22.079 (fla_Z) | 2.6060 / 2.5889 |
| Q1 (249,856 tok / 4 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.868 / 34.932 | 88.677 / 88.283 (fla_Z) | 2.5432 /
2.5273 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.316 / 8.340 | 22.057 / 21.975 (fla_Z) | 2.6522 / 2.6351 |
| Q1 (249,856 tok / 4 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 33.796 / 33.824 | 88.635 /
88.146 (fla_Z) | 2.6227 / 2.6060 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B1 = forward | 4.563 /
4.571 | 11.657 / 11.660 (fla_C) | 2.5545 / 2.5508 |
| Q1 (249,856 tok / 4 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.371 / 18.365 | 46.240 / 46.318 (fla_C) | 2.5170 /
2.5221 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B1 = forward | 4.563 / 4.564
| 11.852 / 11.866 (fla_Z) | 2.5975 / 2.5996 |
| Q1 (249,856 tok / 4 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.920 / 17.910 | 46.068 / 46.142 (fla_Z) | 2.5708 /
2.5764 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.683 / 4.680 | 11.723 / 11.745 (fla_C) | 2.5032 / 2.5095 |
| Q1 (249,856 tok / 4 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.382 / 18.392 | 46.090 /
46.165 (fla_Z) | 2.5073 / 2.5101 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B1 = forward | 2.648 /
2.649 | 6.320 / 6.335 (fla_C) | 2.3872 / 2.3913 |
| Q1 (249,856 tok / 4 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.016 / 10.022 | 24.250 / 24.311 (fla_C)
| 2.4211 / 2.4257 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B1 = forward | 2.639 / 2.645
| 7.072 / 7.093 (fla_Z) | 2.6801 / 2.6811 |
| Q1 (249,856 tok / 4 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.707 / 9.721 | 26.065 / 26.197 (fla_Z) | 2.6851 /
2.6950 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.856 / 2.850 | 6.377 / 6.385 (fla_C) | 2.2327 / 2.2404 |
| Q1 (249,856 tok / 4 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.428 / 10.419 | 24.417 /
24.441 (fla_C) | 2.3416 / 2.3458 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B1 = forward | 14.430 /
14.462 | 40.320 / 40.221 (fla_C) | 2.7942 / 2.7812 |
| Q2 (226,336 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 60.129 / 60.177 | 144.905 / 143.848 (fla_C) | 2.4099
/ 2.3904 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B1 = forward | 15.238 /
15.253 | 37.186 / 37.002 (fla_Z) | 2.4404 / 2.4258 |
| Q2 (226,336 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.012 / 63.011 | 146.929 / 145.969 (fla_Z) | 2.3318
/ 2.3166 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 14.964 / 14.991 | 37.134 / 37.056 (fla_Z) | 2.4816 / 2.4719 |
| Q2 (226,336 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 61.981 / 61.991 | 144.922 /
143.895 (fla_C) | 2.3382 / 2.3212 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B1 = forward | 7.618 /
7.625 | 20.603 / 20.429 (fla_C) | 2.7047 / 2.6792 |
| Q2 (226,336 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 31.129 / 31.133 | 82.516 / 82.118 (fla_C) | 2.6508 /
2.6377 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B1 = forward | 7.844 / 7.863
| 20.053 / 19.986 (fla_Z) | 2.5563 / 2.5418 |
| Q2 (226,336 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 32.063 / 32.087 | 80.757 / 80.341 (fla_Z) | 2.5187 /
2.5038 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 7.776 / 7.790 | 20.077 / 19.981 (fla_Z) | 2.5821 / 2.5650 |
| Q2 (226,336 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 31.233 / 31.279 | 80.682 /
80.345 (fla_Z) | 2.5833 / 2.5686 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.270 /
4.263 | 10.697 / 10.711 (fla_C) | 2.5051 / 2.5124 |
| Q2 (226,336 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 16.897 / 16.897 | 42.207 / 42.285 (fla_C) | 2.4979 /
2.5025 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.209 / 4.225
| 10.795 / 10.903 (fla_Z) | 2.5650 / 2.5804 |
| Q2 (226,336 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 16.400 / 16.400 | 42.116 / 42.136 (fla_Z) | 2.5680 /
2.5693 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.246 / 4.275 | 10.702 / 10.811 (fla_C) | 2.5203 / 2.5287 |
| Q2 (226,336 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 16.650 / 16.662 | 42.144 /
42.147 (fla_Z) | 2.5312 / 2.5295 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.520 /
2.521 | 5.916 / 5.939 (fla_C) | 2.3473 / 2.3560 |
| Q2 (226,336 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.302 / 9.311 | 22.393 / 22.462 (fla_C) |
2.4072 / 2.4124 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.468 / 2.463
| 6.711 / 6.704 (fla_Z) | 2.7193 / 2.7222 |
| Q2 (226,336 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 8.966 / 8.985 | 24.364 / 24.411 (fla_Z) | 2.7174 /
2.7168 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.569 / 2.679 | 5.890 / 6.253 (fla_C) | 2.2930 / 2.3339 |
| Q2 (226,336 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 9.510 / 9.517 | 22.395 / 22.433
(fla_C) | 2.3548 / 2.3571 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B1 = forward | 16.513 /
16.548 | 26.521 / 26.364 (fla_C) | 1.6060 / 1.5932 |
| Q3 (262,048 tok / 6 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 69.409 / 69.436 | 125.293 / 124.271 (fla_C) | 1.8051
/ 1.7897 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B1 = forward | 16.365 /
16.403 | 35.945 / 35.804 (fla_Z) | 2.1965 / 2.1827 |
| Q3 (262,048 tok / 6 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 68.814 / 68.870 | 152.624 / 151.772 (fla_Z) | 2.2179
/ 2.2037 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 17.214 / 17.244 | 26.580 / 26.407 (fla_C) | 1.5441 / 1.5314 |
| Q3 (262,048 tok / 6 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 71.165 / 71.188 | 125.296 /
124.313 (fla_C) | 1.7607 / 1.7463 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B1 = forward | 8.622 /
8.647 | 22.349 / 22.367 (fla_C) | 2.5921 / 2.5867 |
| Q3 (262,048 tok / 6 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 35.785 / 35.779 | 89.243 / 88.918 (fla_C) | 2.4938 /
2.4852 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B1 = forward | 8.890 / 8.914
| 23.468 / 23.520 (fla_Z) | 2.6396 / 2.6384 |
| Q3 (262,048 tok / 6 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 36.506 / 36.536 | 93.308 / 92.958 (fla_Z) | 2.5559 /
2.5443 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.813 / 8.839 | 22.296 / 22.430 (fla_C) | 2.5300 / 2.5374 |
| Q3 (262,048 tok / 6 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.624 / 35.676 | 89.439 /
89.048 (fla_C) | 2.5107 / 2.4960 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B1 = forward | 4.794 /
4.786 | 12.199 / 12.212 (fla_C) | 2.5446 / 2.5515 |
| Q3 (262,048 tok / 6 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 19.195 / 19.187 | 48.431 / 48.566 (fla_C) | 2.5231 /
2.5312 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B1 = forward | 4.764 / 4.769
| 12.356 / 12.381 (fla_Z) | 2.5937 / 2.5959 |
| Q3 (262,048 tok / 6 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.723 / 18.748 | 48.217 / 48.274 (fla_Z) | 2.5753 /
2.5749 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.931 / 4.916 | 12.227 / 12.208 (fla_C) | 2.4796 / 2.4835 |
| Q3 (262,048 tok / 6 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.290 / 19.297 | 48.250 /
48.284 (fla_Z) | 2.5012 / 2.5021 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B1 = forward | 2.801 /
2.812 | 6.679 / 6.685 (fla_C) | 2.3847 / 2.3772 |
| Q3 (262,048 tok / 6 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.503 / 10.512 | 25.479 / 25.567 (fla_C)
| 2.4259 / 2.4322 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B1 = forward | 2.740 / 2.750
| 7.390 / 7.414 (fla_Z) | 2.6972 / 2.6962 |
| Q3 (262,048 tok / 6 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 10.123 / 10.162 | 27.334 / 27.492 (fla_Z) | 2.7002 /
2.7053 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 3.028 / 3.032 | 6.666 / 6.703 (fla_C) | 2.2012 / 2.2108 |
| Q3 (262,048 tok / 6 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 11.157 / 11.203 | 25.497 /
25.629 (fla_C) | 2.2854 / 2.2878 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B1 = forward | 15.056 /
15.121 | 24.905 / 24.702 (fla_C) | 1.6541 / 1.6336 |
| Q4 (240,160 tok / 3 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 63.418 / 63.444 | 137.595 / 136.196 (fla_C) | 2.1696
/ 2.1467 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B1 = forward | 15.130 /
15.185 | 33.762 / 33.745 (fla_Z) | 2.2315 / 2.2222 |
| Q4 (240,160 tok / 3 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 63.431 / 63.492 | 143.191 / 142.340 (fla_Z) | 2.2574
/ 2.2418 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 15.841 / 15.876 | 24.921 / 24.711 (fla_C) | 1.5732 / 1.5565 |
| Q4 (240,160 tok / 3 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 65.662 / 65.712 | 137.432 /
136.265 (fla_C) | 2.0930 / 2.0737 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B1 = forward | 8.120 /
8.149 | 21.813 / 21.778 (fla_C) | 2.6862 / 2.6724 |
| Q4 (240,160 tok / 3 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 33.283 / 33.297 | 87.601 / 87.267 (fla_C) | 2.6320 /
2.6209 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B1 = forward | 8.202 / 8.211
| 21.449 / 21.359 (fla_Z) | 2.6152 / 2.6013 |
| Q4 (240,160 tok / 3 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 33.709 / 33.709 | 85.491 / 85.097 (fla_Z) | 2.5362 /
2.5245 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.341 / 8.372 | 21.576 / 21.480 (fla_Z) | 2.5866 / 2.5658 |
| Q4 (240,160 tok / 3 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.025 / 34.052 | 85.699 /
85.261 (fla_Z) | 2.5187 / 2.5039 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B1 = forward | 4.438 /
4.430 | 11.306 / 11.298 (fla_C) | 2.5475 / 2.5503 |
| Q4 (240,160 tok / 3 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 17.755 / 17.777 | 44.600 / 44.663 (fla_C) | 2.5120 /
2.5124 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B1 = forward | 4.427 / 4.429
| 11.436 / 11.414 (fla_Z) | 2.5831 / 2.5768 |
| Q4 (240,160 tok / 3 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.298 / 17.279 | 44.544 / 44.499 (fla_Z) | 2.5751 /
2.5753 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.507 / 4.504 | 11.365 / 11.363 (fla_C) | 2.5216 / 2.5229 |
| Q4 (240,160 tok / 3 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 17.572 / 17.563 | 44.507 /
44.535 (fla_Z) | 2.5328 / 2.5358 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B1 = forward | 2.578 /
2.582 | 6.154 / 6.168 (fla_C) | 2.3874 / 2.3886 |
| Q4 (240,160 tok / 3 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 9.680 / 9.689 | 23.495 / 23.555 (fla_C) |
2.4273 / 2.4311 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B1 = forward | 2.695 / 2.594
| 7.204 / 6.960 (fla_Z) | 2.6729 / 2.6830 |
| Q4 (240,160 tok / 3 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.473 / 9.492 | 25.530 / 25.651 (fla_Z) | 2.6951 /
2.7024 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.760 / 2.757 | 6.194 / 6.219 (fla_C) | 2.2442 / 2.2557 |
| Q4 (240,160 tok / 3 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.546 / 10.100 | 25.103 /
23.640 (fla_C) | 2.3804 / 2.3406 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B1 = forward | 16.110 /
16.135 | 30.806 / 30.604 (fla_C) | 1.9122 / 1.8968 |
| Q5 (255,008 tok / 5 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 67.418 / 67.449 | 134.464 / 133.515 (fla_C) | 1.9945
/ 1.9795 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B1 = forward | 16.005 /
16.049 | 38.414 / 38.213 (fla_Z) | 2.4002 / 2.3811 |
| Q5 (255,008 tok / 5 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 67.184 / 67.214 | 157.516 / 156.477 (fla_Z) | 2.3445
/ 2.3281 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.573 / 16.613 | 30.818 / 30.684 (fla_C) | 1.8595 / 1.8470 |
| Q5 (255,008 tok / 5 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 68.924 / 68.894 | 134.467 /
133.589 (fla_C) | 1.9510 / 1.9390 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B1 = forward | 8.409 /
8.419 | 20.182 / 20.091 (fla_C) | 2.4000 / 2.3863 |
| Q5 (255,008 tok / 5 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.832 / 34.849 | 87.028 / 86.538 (fla_C) | 2.4985 /
2.4833 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B1 = forward | 8.701 / 8.718
| 20.329 / 20.201 (fla_Z) | 2.3365 / 2.3172 |
| Q5 (255,008 tok / 5 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 35.786 / 35.837 | 85.144 / 84.657 (fla_Z) | 2.3793 /
2.3623 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.601 / 8.613 | 20.280 / 20.187 (fla_C) | 2.3579 / 2.3437 |
| Q5 (255,008 tok / 5 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 34.788 / 34.785 | 85.262 /
84.618 (fla_Z) | 2.4509 / 2.4326 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B1 = forward | 4.680 /
4.684 | 11.934 / 11.935 (fla_C) | 2.5500 / 2.5482 |
| Q5 (255,008 tok / 5 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.719 / 18.746 | 47.234 / 47.377 (fla_C) | 2.5233 /
2.5273 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B1 = forward | 4.668 / 4.664
| 12.278 / 12.313 (fla_Z) | 2.6301 / 2.6398 |
| Q5 (255,008 tok / 5 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 18.317 / 18.335 | 47.256 / 47.385 (fla_Z) | 2.5799 /
2.5844 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.896 / 4.895 | 11.917 / 11.966 (fla_C) | 2.4339 / 2.4446 |
| Q5 (255,008 tok / 5 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 19.221 / 19.236 | 47.302 /
47.370 (fla_C) | 2.4610 / 2.4626 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B1 = forward | 2.757 /
2.761 | 6.562 / 6.585 (fla_C) | 2.3800 / 2.3854 |
| Q5 (255,008 tok / 5 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.281 / 10.293 | 24.967 / 25.048 (fla_C)
| 2.4284 / 2.4335 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B1 = forward | 2.691 / 2.693
| 7.148 / 7.158 (fla_Z) | 2.6566 / 2.6576 |
| Q5 (255,008 tok / 5 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.913 / 9.925 | 26.928 / 27.007 (fla_Z) | 2.7165 /
2.7210 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.963 / 2.963 | 6.545 / 6.562 (fla_C) | 2.2092 / 2.2148 |
| Q5 (255,008 tok / 5 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.852 / 10.898 | 24.934 /
25.056 (fla_C) | 2.2975 / 2.2991 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B1 = forward | 16.127 /
16.173 | 24.944 / 24.752 (fla_C) | 1.5467 / 1.5305 |
| Q6 (249,856 tok / 2 docs) | 2 | contiguous | B3 = forward + checkpoint
replay + backward | 67.096 / 67.050 | 140.433 / 139.492 (fla_C) | 2.0930
/ 2.0804 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B1 = forward | 16.372 /
16.428 | 33.127 / 33.055 (fla_Z) | 2.0233 / 2.0121 |
| Q6 (249,856 tok / 2 docs) | 2 | zigzag | B3 = forward + checkpoint
replay + backward | 68.017 / 68.098 | 155.528 / 154.397 (fla_Z) | 2.2866
/ 2.2673 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B1 =
forward | 16.852 / 16.911 | 24.940 / 24.758 (fla_C) | 1.4800 / 1.4640 |
| Q6 (249,856 tok / 2 docs) | 2 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 69.745 / 69.841 | 140.783 /
139.531 (fla_C) | 2.0185 / 1.9978 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B1 = forward | 8.310 /
8.344 | 22.811 / 22.769 (fla_C) | 2.7450 / 2.7289 |
| Q6 (249,856 tok / 2 docs) | 4 | contiguous | B3 = forward + checkpoint
replay + backward | 34.276 / 34.325 | 91.390 / 90.822 (fla_C) | 2.6663 /
2.6459 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B1 = forward | 8.478 / 8.484
| 22.083 / 22.027 (fla_Z) | 2.6047 / 2.5963 |
| Q6 (249,856 tok / 2 docs) | 4 | zigzag | B3 = forward + checkpoint
replay + backward | 34.760 / 34.821 | 88.907 / 88.469 (fla_Z) | 2.5578 /
2.5407 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B1 =
forward | 8.756 / 8.784 | 22.086 / 22.053 (fla_Z) | 2.5222 / 2.5105 |
| Q6 (249,856 tok / 2 docs) | 4 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 35.591 / 35.649 | 88.905 /
88.391 (fla_Z) | 2.4980 / 2.4795 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B1 = forward | 4.602 /
4.591 | 11.772 / 11.789 (fla_C) | 2.5580 / 2.5679 |
| Q6 (249,856 tok / 2 docs) | 8 | contiguous | B3 = forward + checkpoint
replay + backward | 18.418 / 18.413 | 46.421 / 46.473 (fla_C) | 2.5204 /
2.5239 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B1 = forward | 4.557 / 4.577
| 11.808 / 11.809 (fla_Z) | 2.5912 / 2.5802 |
| Q6 (249,856 tok / 2 docs) | 8 | zigzag | B3 = forward + checkpoint
replay + backward | 17.891 / 17.916 | 46.155 / 46.174 (fla_Z) | 2.5798 /
2.5773 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B1 =
forward | 4.631 / 4.626 | 11.777 / 11.816 (fla_C) | 2.5428 / 2.5545 |
| Q6 (249,856 tok / 2 docs) | 8 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 18.301 / 18.278 | 46.130 /
46.154 (fla_Z) | 2.5206 / 2.5251 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B1 = forward | 2.691 /
2.691 | 6.393 / 6.418 (fla_C) | 2.3754 / 2.3851 |
| Q6 (249,856 tok / 2 docs) | 16 | contiguous | B3 = forward +
checkpoint replay + backward | 10.024 / 10.027 | 24.414 / 24.495 (fla_C)
| 2.4356 / 2.4429 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B1 = forward | 2.646 / 2.635
| 7.087 / 7.070 (fla_Z) | 2.6787 / 2.6827 |
| Q6 (249,856 tok / 2 docs) | 16 | zigzag | B3 = forward + checkpoint
replay + backward | 9.715 / 9.707 | 26.288 / 26.359 (fla_Z) | 2.7059 /
2.7154 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B1 =
forward | 2.736 / 2.747 | 6.397 / 6.409 (fla_C) | 2.3378 / 2.3331 |
| Q6 (249,856 tok / 2 docs) | 16 | per-document zigzag + ragged | B3 =
forward + checkpoint replay + backward | 10.261 / 10.274 | 24.430 /
24.573 (fla_C) | 2.3810 / 2.3918 |

The family's other Cake variant is the single-device packed KDA training
forward with saved-context and checkpoint-replay backward, together with
the non-context-parallel causal conv1d + SiLU training backend; the
family ships on sm_100a, sm_103a and sm_107a, and the context-parallel
kernels of this PR are built for all three.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added chunk-stage support to KDA training, including forward and
gradient computations.
* CUDA graph replay is now documented for the three KDA training entry
points, with optional shared-memory tuning during capture.
* KCP partitioning now supports explicit fragment layouts and cut points
for zigzag-per-document layouts.
* **Improvements**
* Updated the default KCP planning strategy to account for eligible
workloads and fragment sizes.
* Host-side metadata is reused across matching calls, with a
cache-clearing option.
* **Documentation**
* Clarified partitioning inputs, graph replay behavior, and saved-value
handling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [462a48a](https://github.com/flashinfer-ai/flashinfer/commit/462a48a4cde305cf29f98eb061fd7789ef698dbc)

- **作者**: eigen
- **时间**: 2026-10-23T09:25:12Z
- **提交信息**: perf(cake_dsa): hole-free index rows, in-place strided dout, one-launch varlen index preparation and programmatic dependent launch, with grad (#7098)

`flashinfer.dsa_sparse_attention.dsa_sparse_attention` and
`dsa_sparse_attention_varlen` run Cake's native 64-query-head DeepSeek
Sparse Attention training kernels (package
`flashinfer/experimental/cake_dsa_train`). The kernels implement top-k
sparse MLA with absorbed queries: 64 heads, 512 latent + 64 rope
query/key dims, 512 value dims and any positive top-k. Inputs and
outputs are BF16, and both forward and backward are covered. The package
has two variants (records) with 14 kernel programs in total, spread
across the forward, index-preparation and backward main / delta / reduce
/ cast stages:

- **Variants:** the RoPE record `cake_dsa_h64_train` (latent + rope
operands) and the NoPE record `cake_dsa_h64_nope_train` (latent only).
- **This PR:** changes both records and adds no new variant. The
index-preparation stage compacts index rows with `-1` holes anywhere on
device, so a hole costs no attention work. The rotary backward consumes
a strided `dout` view in place, without a copy.
`dsa_sparse_attention_varlen` turns per-document indices into global
rows in one device launch instead of a chain of torch launches. The
index-preparation stage and the forward kernels run under programmatic
dependent launch.

The baseline is the previous Cake version of the same package at
FlashInfer main 73f6cebda. Speedup = baseline / this PR, computed from
the two times shown. Times are CUPTI kernel time in ms per forward
(fwd), backward (bwd) and training step (step).

**NVIDIA GB200 (`sm_100a`), driver 580.126.20, CUDA 13.4 toolkit (nvcc
13.4.92), PyTorch 2.14.1+cu130**

| Shape | Metric | Baseline (73f6cebda), ms | This PR, ms | Speedup |
|---|---|---:|---:|---:|
| **NoPE (`cake_dsa_h64_nope_train`), index rows with `-1` holes** | | |
| |
| `nope_repro_16k_gap`: T 16384, S 16384, K 2176, gap holes in 100 % of
rows | fwd | 3.355 | 2.028 | 1.654× |
| | bwd | 13.797 | 8.392 | 1.644× |
| | step | 17.010 | 10.699 | 1.590× |
| `nope_docs264x992_rank0_fixedtail`: T 16368, S 270072, K 2176, holes
in 75.8 % of rows | fwd | 2.868 | 1.377 | 2.083× |
| | bwd | 11.160 | 5.022 | 2.222× |
| | step | 13.964 | 6.352 | 2.198× |
| `nope_pack4_262k_rank0_fixedtail`: T 16384, S 270336, K 2176, holes in
37.5 % of rows | fwd | 3.632 | 3.058 | 1.188× |
| | bwd | 15.706 | 14.072 | 1.116× |
| | step | 19.937 | 17.941 | 1.111× |
| `nope_glm53_a_fixedtail`: T 16263, S 269564, K 2176, holes in 36.6 %
of rows | fwd | 3.515 | 2.964 | 1.186× |
| | bwd | 15.633 | 14.069 | 1.111× |
| | step | 19.917 | 17.797 | 1.119× |
| **RoPE (`cake_dsa_h64_train`)** | | | | |
| `doc_16231` | fwd | 4.359 | 3.925 | 1.111× |
| | bwd | 16.984 | 16.974 | 1.001× |
| `doc_16231_hm` (head-major `dout`) | fwd | 4.441 | 3.812 | 1.165× |
| | bwd | 18.100 | 16.979 | 1.066× |
| `packed_glm_a` | fwd | 4.000 | 3.436 | 1.164× |
| | bwd | 16.461 | 16.473 | 0.999× |
| `packed_glm_a_hm` (head-major `dout`) | fwd | 4.012 | 3.627 | 1.106× |
| | bwd | 17.211 | 16.214 | 1.061× |
| `tail_2123x67923` | fwd | 1.138 | 0.735 | 1.548× |

Hole-free rows of the existing benchmark, for reference:

| Shape | Metric | Baseline (73f6cebda), ms | This PR, ms | Speedup |
|---|---|---:|---:|---:|
| `nope_glm53_b` | fwd | 2.594 | 2.660 | 0.975× |
| `nope_doc_16384`: T 16384, S 16384, K 2176 | fwd | 3.797 | 3.555 |
1.068× |
| `nope_chunk_3975x269564` | step | 4.277 | 4.333 | 0.987× |
| `nope_repro_16k_compact_stable` | step | 10.741 | 10.540 | 1.019× |
| `nope_short_1024_k128`: T 1024, S 1024, K 128 | fwd | 0.051 | 0.067 |
0.761× |
| | step | 0.332 | 0.359 | 0.925× |
| `nope_tail_1024x16384_k512`: T 1024, S 16384, K 512 | fwd | 0.096 |
0.112 | 0.857× |
| | step | 0.512 | 0.534 | 0.959× |

**NVIDIA GB300 (`sm_103a`), driver 580.159.03, CUDA 13.4 toolkit (nvcc
13.4.92), PyTorch 2.14.1+cu130**

| Shape | Metric | Baseline (73f6cebda), ms | This PR, ms | Speedup |
|---|---|---:|---:|---:|
| **NoPE (`cake_dsa_h64_nope_train`), index rows with `-1` holes** | | |
| |
| `nope_repro_16k_gap`: T 16384, S 16384, K 2176, gap holes in 100 % of
rows | fwd | 3.295 | 1.971 | 1.672× |
| | bwd | 13.986 | 8.200 | 1.706× |
| | step | 17.141 | 10.023 | 1.710× |
| `nope_docs264x992_rank0_fixedtail`: T 16368, S 270072, K 2176, holes
in 75.8 % of rows | fwd | 2.818 | 1.348 | 2.091× |
| | bwd | 11.363 | 5.003 | 2.271× |
| | step | 14.109 | 6.280 | 2.247× |
| `nope_pack4_262k_rank0_fixedtail`: T 16384, S 270336, K 2176, holes in
37.5 % of rows | fwd | 3.308 | 2.795 | 1.184× |
| | bwd | 14.963 | 12.778 | 1.171× |
| | step | 18.198 | 15.508 | 1.173× |
| `nope_glm53_a_fixedtail`: T 16263, S 269564, K 2176, holes in 36.6 %
of rows | fwd | 3.280 | 2.774 | 1.182× |
| | bwd | 14.901 | 12.762 | 1.168× |
| | step | 18.097 | 15.455 | 1.171× |
| **RoPE (`cake_dsa_h64_train`)** | | | | |
| `doc_16231` | fwd | 4.112 | 3.629 | 1.133× |
| | bwd | 16.783 | 16.774 | 1.001× |
| `doc_16231_hm` (head-major `dout`) | fwd | 4.100 | 3.636 | 1.128× |
| | bwd | 17.886 | 16.779 | 1.066× |
| `packed_glm_a` | fwd | 3.736 | 3.211 | 1.164× |
| | bwd | 15.446 | 15.446 | 1.000× |
| `packed_glm_a_hm` (head-major `dout`) | fwd | 3.695 | 3.197 | 1.156× |
| | bwd | 16.620 | 15.449 | 1.076× |
| `tail_2123x67923` | fwd | 1.052 | 0.703 | 1.496× |

Hole-free rows of the existing benchmark, for reference:

| Shape | Metric | Baseline (73f6cebda), ms | This PR, ms | Speedup |
|---|---|---:|---:|---:|
| `nope_doc_16384_k512` | fwd | 1.146 | 1.148 | 0.998× |
| `nope_doc_16384`: T 16384, S 16384, K 2176 | fwd | 3.311 | 3.286 |
1.008× |
| `nope_short_4096_k512` | step | 1.391 | 1.392 | 0.999× |
| `nope_doc_65536`: T 65536, S 65536, K 2176 | step | 75.852 | 75.779 |
1.001× |
| `nope_short_1024_k128`: T 1024, S 1024, K 128 | fwd | 0.049 | 0.064 |
0.766× |
| | step | 0.333 | 0.355 | 0.938× |
| `nope_tail_1024x16384_k512`: T 1024, S 16384, K 512 | fwd | 0.084 |
0.098 | 0.857× |
| | step | 0.505 | 0.529 | 0.955× |

This kernel has no Cake variants beyond these two records, and both ship
on `sm_100a` (B200 / GB200), `sm_103a` (B300 / GB300) and `sm_107a`
(R200) as 42 build entries; the measurements above cover `sm_100a` and
`sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Varlen sparse-attention inputs now compact valid indices while
preserving their order, with optional per-row length limits and
valid-count reporting.
  * Backward passes support additional strided gradient layouts.
* NoPE inputs without explicit lengths can now compact valid indices
automatically.
* **Performance**
* Updated kernel launch paths and added benchmark coverage for index
preparation and alternate input layouts.
* **Documentation**
  * Clarified how compaction and length limits affect varlen inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [69124ac](https://github.com/flashinfer-ai/flashinfer/commit/69124ac26b80b44d3cdeff2de07ba66a4a6704a0)

- **作者**: eigen
- **时间**: 2026-10-23T09:15:04Z
- **提交信息**: feat(cake_causal_conv1d): bf16 taps, bias and fp32 SiLU-gradient routes; channel tiles for C 1280/1536/2560; with grad (#7089)

`cake_causal_conv1d_train` is the Cake causal conv1d + SiLU training
kernel. It handles packed documents via `cu_seqlens` and runs a width-4
depthwise causal conv on BF16 activations. It has 8 variants: 3 forward
(`fwd`, `fwd_dt`, `fwd_bias`) and 5 backward (`bwd`, `bwd_dt`,
`bwd_bias`, `bwd_fp32g`, `bwd_bias_fp32g`). This PR adds the six
variants beyond `fwd` / `bwd`:
- BF16 taps: `fwd_dt`, and `bwd_dt` with BF16 dweight.
- Bias: `fwd_bias` with BF16 taps, and `bwd_bias` with dbias.
- FP32 preactivation gradient: `bwd_fp32g` with FP32 taps/dweight, and
`bwd_bias_fp32g` with bias.

It also adds a new channel-tile rule for C 1280 / 1536 / 2560 on the
existing `fwd` / `bwd` variants and a faster dweight reduction kernel
for every backward variant. Otherwise, `fwd` / `bwd` keep their
programs. Against `p0-package` (the previous Cake version on main,
#7072), `fwd` / `bwd` are 1.115x–1.490x faster at C 1280 / 1536 / 2560
and within 0.995x–1.022x on the other shapes. No Cake BF16-taps variant
existed before, so `fwd_dt` / `bwd_dt` are compared with `shipped+casts`
(#7072 plus host-side dtype casts of the taps/dweight); they are
1.031x–1.990x faster. Against `fla` (flash-linear-attention 0.5.2
`causal_conv1d`, with bias where the route has one), `fwd_bias` is
1.319x–2.291x faster and `bwd_bias` / `bwd_fp32g` / `bwd_bias_fp32g` are
2.959x–6.649x faster.

NVIDIA GB300 (sm_103a / CC 10.3, 152 SMs), driver 580.159.03, CUDA 13.0
runtime / NVRTC 13.4. Latency = median CUPTI kernel time of every kernel
of the call (µs), ABBA 3 groups x (8 warmup, 64 iters), pooled over both
orders; speedup = baseline / new.

| route | shape (S x C) | baseline | baseline µs | new µs | speedup |
|---|---|---|---:|---:|---:|
| fwd | 239718 x 512 | p0-package | 83.2 | 83.5 | 0.996x |
| fwd | 245028 x 512 | p0-package | 88.5 | 86.9 | 1.019x |
| fwd | 249866 x 512 | p0-package | 86.5 | 86.9 | 0.995x |
| fwd | 250340 x 512 | p0-package | 87.3 | 87.3 | 1.000x |
| fwd | 258574 x 512 | p0-package | 89.3 | 89.7 | 0.996x |
| fwd | 259042 x 512 | p0-package | 89.3 | 89.2 | 1.001x |
| fwd | 259584 x 512 | p0-package | 89.2 | 89.2 | 1.000x |
| fwd | 261393 x 512 | p0-package | 90.7 | 90.1 | 1.006x |
| fwd | 250340 x 128 | p0-package | 28.2 | 28.3 | 0.997x |
| fwd | 250340 x 256 | p0-package | 47.5 | 47.4 | 1.001x |
| fwd | 250340 x 1024 | p0-package | 170.7 | 167.6 | 1.019x |
| fwd | 250340 x 2048 | p0-package | 323.2 | 323.5 | 0.999x |
| fwd | 250340 x 4096 | p0-package | 632.4 | 634.0 | 0.998x |
| fwd | 250340 x 8192 | p0-package | 1261.1 | 1259.0 | 1.002x |
| fwd | 250340 x 1280 | p0-package | 305.0 | 207.5 | 1.469x |
| fwd | 250340 x 1536 | p0-package | 305.4 | 248.8 | 1.227x |
| fwd | 262144 x 1280 | p0-package | 319.0 | 217.5 | 1.467x |
| fwd | 262144 x 1536 | p0-package | 319.6 | 259.0 | 1.234x |
| fwd | 250340 x 2560 | p0-package | 456.6 | 409.3 | 1.115x |
| fwd | 250340 x 1344 | p0-package | 305.0 | 305.2 | 1.000x |
| fwd | 250340 x 1160 | p0-package | 304.7 | 304.8 | 1.000x |
| fwd | 262144 x 1160 | p0-package | 319.0 | 319.1 | 1.000x |
| bwd | 239718 x 512 | p0-package | 141.9 | 141.2 | 1.005x |
| bwd | 245028 x 512 | p0-package | 147.5 | 148.0 | 0.997x |
| bwd | 249866 x 512 | p0-package | 147.4 | 147.3 | 1.000x |
| bwd | 250340 x 512 | p0-package | 147.2 | 147.8 | 0.996x |
| bwd | 258574 x 512 | p0-package | 150.6 | 150.8 | 0.999x |
| bwd | 259042 x 512 | p0-package | 152.5 | 152.7 | 0.999x |
| bwd | 259584 x 512 | p0-package | 150.9 | 151.5 | 0.996x |
| bwd | 261393 x 512 | p0-package | 155.8 | 155.3 | 1.003x |
| bwd | 250340 x 128 | p0-package | 60.7 | 59.4 | 1.022x |
| bwd | 250340 x 256 | p0-package | 96.1 | 95.7 | 1.004x |
| bwd | 250340 x 1024 | p0-package | 276.7 | 276.6 | 1.001x |
| bwd | 250340 x 2048 | p0-package | 550.0 | 548.2 | 1.003x |
| bwd | 250340 x 4096 | p0-package | 1058.3 | 1055.6 | 1.003x |
| bwd | 250340 x 8192 | p0-package | 2075.4 | 2070.5 | 1.002x |
| bwd | 250340 x 1280 | p0-package | 541.8 | 366.2 | 1.480x |
| bwd | 250340 x 1536 | p0-package | 542.4 | 426.2 | 1.273x |
| bwd | 262144 x 1280 | p0-package | 565.9 | 379.9 | 1.490x |
| bwd | 262144 x 1536 | p0-package | 564.5 | 441.9 | 1.277x |
| bwd | 250340 x 2560 | p0-package | 801.8 | 688.8 | 1.164x |
| bwd | 250340 x 1344 | p0-package | 542.3 | 540.7 | 1.003x |
| bwd | 250340 x 1160 | p0-package | 542.6 | 541.4 | 1.002x |
| bwd | 262144 x 1160 | p0-package | 565.2 | 563.5 | 1.003x |
| fwd_dt | 239718 x 512 | shipped+casts | 115.7 | 84.0 | 1.377x |
| fwd_dt | 245028 x 512 | shipped+casts | 113.2 | 86.6 | 1.307x |
| fwd_dt | 249866 x 512 | shipped+casts | 113.3 | 87.0 | 1.302x |
| fwd_dt | 250340 x 512 | shipped+casts | 114.3 | 87.2 | 1.310x |
| fwd_dt | 258574 x 512 | shipped+casts | 116.9 | 89.6 | 1.305x |
| fwd_dt | 259042 x 512 | shipped+casts | 117.4 | 88.8 | 1.322x |
| fwd_dt | 259584 x 512 | shipped+casts | 117.5 | 89.0 | 1.321x |
| fwd_dt | 261393 x 512 | shipped+casts | 119.1 | 90.1 | 1.322x |
| fwd_dt | 250340 x 128 | shipped+casts | 56.2 | 28.3 | 1.990x |
| fwd_dt | 250340 x 256 | shipped+casts | 75.8 | 46.8 | 1.622x |
| fwd_dt | 250340 x 1024 | shipped+casts | 199.6 | 167.4 | 1.192x |
| fwd_dt | 250340 x 2048 | shipped+casts | 354.7 | 321.7 | 1.103x |
| fwd_dt | 250340 x 4096 | shipped+casts | 668.0 | 631.8 | 1.057x |
| fwd_dt | 250340 x 8192 | shipped+casts | 1292.9 | 1254.2 | 1.031x |
| fwd_dt | 250340 x 1280 | shipped+casts | 337.9 | 207.5 | 1.628x |
| fwd_dt | 250340 x 1536 | shipped+casts | 336.8 | 249.0 | 1.352x |
| fwd_dt | 262144 x 1280 | shipped+casts | 351.1 | 217.7 | 1.613x |
| fwd_dt | 262144 x 1536 | shipped+casts | 358.2 | 257.6 | 1.390x |
| fwd_dt | 250340 x 2560 | shipped+casts | 493.4 | 408.0 | 1.209x |
| fwd_dt | 250340 x 1344 | shipped+casts | 344.1 | 306.1 | 1.124x |
| fwd_dt | 250340 x 1160 | shipped+casts | 364.8 | 305.9 | 1.193x |
| fwd_dt | 262144 x 1160 | shipped+casts | 366.2 | 320.4 | 1.143x |
| bwd_dt | 239718 x 512 | shipped+casts | 182.3 | 144.4 | 1.262x |
| bwd_dt | 245028 x 512 | shipped+casts | 187.3 | 148.7 | 1.260x |
| bwd_dt | 249866 x 512 | shipped+casts | 187.6 | 149.6 | 1.254x |
| bwd_dt | 250340 x 512 | shipped+casts | 187.1 | 149.5 | 1.251x |
| bwd_dt | 258574 x 512 | shipped+casts | 191.7 | 153.0 | 1.253x |
| bwd_dt | 259042 x 512 | shipped+casts | 194.8 | 155.2 | 1.255x |
| bwd_dt | 259584 x 512 | shipped+casts | 193.8 | 153.4 | 1.263x |
| bwd_dt | 261393 x 512 | shipped+casts | 195.0 | 155.8 | 1.252x |
| bwd_dt | 250340 x 128 | shipped+casts | 107.9 | 59.9 | 1.802x |
| bwd_dt | 250340 x 256 | shipped+casts | 142.1 | 95.8 | 1.484x |
| bwd_dt | 250340 x 1024 | shipped+casts | 317.0 | 274.5 | 1.155x |
| bwd_dt | 250340 x 2048 | shipped+casts | 594.1 | 541.8 | 1.097x |
| bwd_dt | 250340 x 4096 | shipped+casts | 1104.1 | 1034.9 | 1.067x |
| bwd_dt | 250340 x 8192 | shipped+casts | 2115.9 | 2031.0 | 1.042x |
| bwd_dt | 250340 x 1280 | shipped+casts | 587.5 | 362.6 | 1.620x |
| bwd_dt | 250340 x 1536 | shipped+casts | 589.1 | 422.9 | 1.393x |
| bwd_dt | 262144 x 1280 | shipped+casts | 612.4 | 376.6 | 1.626x |
| bwd_dt | 262144 x 1536 | shipped+casts | 619.9 | 440.7 | 1.407x |
| bwd_dt | 250340 x 2560 | shipped+casts | 852.1 | 676.6 | 1.259x |
| bwd_dt | 250340 x 1344 | shipped+casts | 598.5 | 538.6 | 1.111x |
| bwd_dt | 250340 x 1160 | shipped+casts | 608.9 | 538.8 | 1.130x |
| bwd_dt | 262144 x 1160 | shipped+casts | 629.6 | 557.6 | 1.129x |
| bwd_fp32g | 239718 x 512 | fla | 857.0 | 180.8 | 4.740x |
| bwd_fp32g | 245028 x 512 | fla | 862.2 | 183.9 | 4.688x |
| bwd_fp32g | 249866 x 512 | fla | 892.0 | 190.5 | 4.682x |
| bwd_fp32g | 250340 x 512 | fla | 885.2 | 190.8 | 4.639x |
| bwd_fp32g | 258574 x 512 | fla | 909.7 | 192.0 | 4.739x |
| bwd_fp32g | 259042 x 512 | fla | 912.9 | 193.7 | 4.713x |
| bwd_fp32g | 259584 x 512 | fla | 913.4 | 193.2 | 4.728x |
| bwd_fp32g | 261393 x 512 | fla | 920.7 | 194.9 | 4.725x |
| bwd_fp32g | 250340 x 128 | fla | 334.4 | 79.8 | 4.189x |
| bwd_fp32g | 250340 x 256 | fla | 523.9 | 138.1 | 3.794x |
| bwd_fp32g | 250340 x 1024 | fla | 1730.9 | 351.0 | 4.932x |
| bwd_fp32g | 250340 x 2048 | fla | 3414.6 | 683.1 | 4.999x |
| bwd_fp32g | 250340 x 4096 | fla | 6775.7 | 1312.2 | 5.164x |
| bwd_fp32g | 250340 x 8192 | fla | 13857.3 | 2567.2 | 5.398x |
| bwd_fp32g | 250340 x 1280 | fla | 1892.5 | 440.1 | 4.300x |
| bwd_fp32g | 250340 x 1536 | fla | 2240.5 | 522.4 | 4.289x |
| bwd_fp32g | 262144 x 1280 | fla | 1978.8 | 462.4 | 4.280x |
| bwd_fp32g | 262144 x 1536 | fla | 2346.0 | 544.8 | 4.306x |
| bwd_fp32g | 250340 x 2560 | fla | 3727.0 | 837.8 | 4.448x |
| bwd_fp32g | 250340 x 1344 | fla | 1980.5 | 669.3 | 2.959x |
| bwd_fp32g | 250340 x 1160 | fla | 2595.7 | 665.9 | 3.898x |
| bwd_fp32g | 262144 x 1160 | fla | 2714.4 | 697.6 | 3.891x |
| fwd_bias | 239718 x 512 | fla | 151.0 | 84.1 | 1.795x |
| fwd_bias | 245028 x 512 | fla | 153.4 | 87.0 | 1.764x |
| fwd_bias | 249866 x 512 | fla | 157.0 | 86.8 | 1.809x |
| fwd_bias | 250340 x 512 | fla | 156.8 | 87.5 | 1.793x |
| fwd_bias | 258574 x 512 | fla | 161.9 | 89.6 | 1.806x |
| fwd_bias | 259042 x 512 | fla | 162.3 | 89.4 | 1.816x |
| fwd_bias | 259584 x 512 | fla | 162.8 | 89.6 | 1.818x |
| fwd_bias | 261393 x 512 | fla | 163.7 | 90.4 | 1.810x |
| fwd_bias | 250340 x 128 | fla | 43.4 | 29.3 | 1.483x |
| fwd_bias | 250340 x 256 | fla | 80.3 | 49.0 | 1.639x |
| fwd_bias | 250340 x 1024 | fla | 308.5 | 166.1 | 1.858x |
| fwd_bias | 250340 x 2048 | fla | 618.0 | 319.8 | 1.932x |
| fwd_bias | 250340 x 4096 | fla | 1243.3 | 630.0 | 1.973x |
| fwd_bias | 250340 x 8192 | fla | 2492.0 | 1250.1 | 1.993x |
| fwd_bias | 250340 x 1280 | fla | 397.2 | 213.5 | 1.860x |
| fwd_bias | 250340 x 1536 | fla | 474.4 | 246.9 | 1.921x |
| fwd_bias | 262144 x 1280 | fla | 415.3 | 223.2 | 1.861x |
| fwd_bias | 262144 x 1536 | fla | 496.5 | 256.5 | 1.936x |
| fwd_bias | 250340 x 2560 | fla | 796.9 | 406.5 | 1.960x |
| fwd_bias | 250340 x 1344 | fla | 415.5 | 315.1 | 1.319x |
| fwd_bias | 250340 x 1160 | fla | 721.6 | 315.0 | 2.291x |
| fwd_bias | 262144 x 1160 | fla | 754.3 | 329.3 | 2.291x |
| bwd_bias | 239718 x 512 | fla | 869.4 | 152.3 | 5.710x |
| bwd_bias | 245028 x 512 | fla | 886.7 | 159.1 | 5.572x |
| bwd_bias | 249866 x 512 | fla | 904.8 | 158.6 | 5.705x |
| bwd_bias | 250340 x 512 | fla | 906.3 | 157.5 | 5.755x |
| bwd_bias | 258574 x 512 | fla | 932.9 | 163.6 | 5.704x |
| bwd_bias | 259042 x 512 | fla | 935.3 | 165.0 | 5.670x |
| bwd_bias | 259584 x 512 | fla | 936.7 | 163.6 | 5.726x |
| bwd_bias | 261393 x 512 | fla | 945.2 | 167.8 | 5.634x |
| bwd_bias | 250340 x 128 | fla | 341.4 | 61.3 | 5.570x |
| bwd_bias | 250340 x 256 | fla | 528.7 | 96.6 | 5.475x |
| bwd_bias | 250340 x 1024 | fla | 1770.2 | 292.1 | 6.061x |
| bwd_bias | 250340 x 2048 | fla | 3478.5 | 578.0 | 6.018x |
| bwd_bias | 250340 x 4096 | fla | 6976.3 | 1112.6 | 6.270x |
| bwd_bias | 250340 x 8192 | fla | 14508.6 | 2182.1 | 6.649x |
| bwd_bias | 250340 x 1280 | fla | 2397.5 | 389.4 | 6.157x |
| bwd_bias | 250340 x 1536 | fla | 2852.5 | 453.7 | 6.287x |
| bwd_bias | 262144 x 1280 | fla | 2499.0 | 404.3 | 6.180x |
| bwd_bias | 262144 x 1536 | fla | 2993.0 | 466.7 | 6.413x |
| bwd_bias | 250340 x 2560 | fla | 4749.3 | 729.1 | 6.514x |
| bwd_bias | 250340 x 1344 | fla | 2528.1 | 580.9 | 4.352x |
| bwd_bias | 250340 x 1160 | fla | 2645.4 | 578.0 | 4.577x |
| bwd_bias | 262144 x 1160 | fla | 2765.9 | 603.2 | 4.585x |
| bwd_bias_fp32g | 239718 x 512 | fla | 868.5 | 158.0 | 5.499x |
| bwd_bias_fp32g | 245028 x 512 | fla | 885.3 | 161.2 | 5.492x |
| bwd_bias_fp32g | 249866 x 512 | fla | 908.8 | 164.2 | 5.535x |
| bwd_bias_fp32g | 250340 x 512 | fla | 905.3 | 164.2 | 5.514x |
| bwd_bias_fp32g | 258574 x 512 | fla | 931.1 | 168.5 | 5.526x |
| bwd_bias_fp32g | 259042 x 512 | fla | 937.2 | 169.2 | 5.538x |
| bwd_bias_fp32g | 259584 x 512 | fla | 935.9 | 168.4 | 5.559x |
| bwd_bias_fp32g | 261393 x 512 | fla | 943.2 | 170.6 | 5.529x |
| bwd_bias_fp32g | 250340 x 128 | fla | 340.8 | 63.9 | 5.332x |
| bwd_bias_fp32g | 250340 x 256 | fla | 527.5 | 101.7 | 5.186x |
| bwd_bias_fp32g | 250340 x 1024 | fla | 1764.6 | 301.6 | 5.851x |
| bwd_bias_fp32g | 250340 x 2048 | fla | 3464.8 | 607.0 | 5.708x |
| bwd_bias_fp32g | 250340 x 4096 | fla | 6948.5 | 1173.6 | 5.921x |
| bwd_bias_fp32g | 250340 x 8192 | fla | 14484.4 | 2303.8 | 6.287x |
| bwd_bias_fp32g | 250340 x 1280 | fla | 2398.6 | 393.3 | 6.099x |
| bwd_bias_fp32g | 250340 x 1536 | fla | 2854.9 | 464.8 | 6.142x |
| bwd_bias_fp32g | 262144 x 1280 | fla | 2509.0 | 410.3 | 6.115x |
| bwd_bias_fp32g | 262144 x 1536 | fla | 2987.2 | 481.1 | 6.209x |
| bwd_bias_fp32g | 250340 x 2560 | fla | 4752.6 | 749.2 | 6.344x |
| bwd_bias_fp32g | 250340 x 1344 | fla | 2525.0 | 590.6 | 4.275x |
| bwd_bias_fp32g | 250340 x 1160 | fla | 2643.0 | 583.2 | 4.532x |
| bwd_bias_fp32g | 262144 x 1160 | fla | 2766.4 | 610.9 | 4.529x |

These eight are the kernel's only Cake variants (the context-parallel
KCP forward is a separate package and not part of this PR), and the
family ships on sm_100a (B200), sm_103a (GB300) and sm_107a (R200).

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Causal convolution training now supports optional per-channel bias,
including bias gradients.
* Supports FP32 or BF16 taps and gradients, with configurable bias
dtype.
* Choose whether SiLU gradients use BF16-rounded or FP32 preactivation
values.
* Adds support for additional GPU architectures and channel
configurations.
* **Documentation**
  * Clarifies supported dtypes, bias behavior, and gradient options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [1de520d](https://github.com/flashinfer-ai/flashinfer/commit/1de520d5b54feb4ae6d97a89b06cbc33b1bbd775)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-10-23T08:32:34Z
- **提交信息**: feat(autotuner): support delegated tuning protocols (#6534)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `AutoTuner.choose_with_protocol()` for operations that own their
tuning loop. The protocol controls candidate preparation, measurement,
cache selection and result installation while using the tuner's
controls, locking, statistics and managed v2 cache. Existing runner
selection is unchanged; no operator or MegaMoE cache file is migrated
here.

Protocol results use the existing managed entries, atomic writer and
preload. A tagged key identifies the namespace and record, `runner`
identifies the protocol, and `tactic` contains its JSON result. A
namespace index supports custom lookup, including capacity fallback.
Reload and clear invalidate that index. The context exposes measurement
and bucket controls so adapters can implement or reject them.
`force_tune=True` requests a fresh search, but disk writes still require
ambient tuning to be enabled and the operation to be absent from
`skip_ops`.

MegaMoE motivates this interface. Its tuner creates and releases
symmetric workspaces per candidate, checks numerical correctness, and
scores the median of the slowest rank's time for each sample. Launch
failures stop the search. Its cache lookup agrees on a compatible winner
across ranks before installation.

A `TunableRunner` integration remains an option. The standard tuner
already coordinates cache hits before distributed profiling (#6185).
Preserving MegaMoE's behavior would also need hooks for sample
aggregation, candidate workspace preparation and cleanup, validation,
failure handling, and compatible cached-winner selection across ranks.
The protocol keeps those rules in the adapter while leaving that
follow-up possible.

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
- [ ] All tests are passing (`unittest`, etc.).

The protocol, managed-cache and configuration suites passed 149 host
checks, including forced searches during replay, bare serving and
skipped-operation contexts. The runner cache tests stub profiling; a
host harness also stubs the CUDA capture-state query. Changed-file and
commit hooks passed, including mypy and Ruff. The broader
GPU/core/distributed suites were not rerun for this update.

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

The Rubin adapter is a separate follow-up. This PR can merge
independently.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added custom tuning protocols for application-controlled candidate
selection, measurement, and result installation.
* Added tuning context and result APIs, including protocol record
lookup, publication, and optional persistence.
* **Documentation**
* Documented protocol behavior, cache compatibility, measurement
policies, replay, and distributed coordination requirements.
* **Bug Fixes**
  * Invalid protocol cache entries are now skipped during loading.
* Cache reload and clearing now properly reset protocol records and
cached lookups.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1eee894](https://github.com/flashinfer-ai/flashinfer/commit/1eee894ea0e142f18faaedb11f37114a2c4e1670)

- **作者**: eigen
- **时间**: 2026-10-23T08:15:55Z
- **提交信息**: perf(cake_nvfp4_svdquant): tail-split register-bias programs on sm_100a (#7091)

`flashinfer.mm_nvfp4_svdquant(..., backend="cake")` computes the NVFP4
SVDQuant GEMM `out = BF16(alpha * (deq(A) @ deq(B)^T + D @ L1^T) +
bias)`. In this kernel, A and B are NVFP4 (E2M1) with E4M3 block scales.
The low-rank D / L1, the bias and the output are BF16, and accumulation
is FP32. Its Cake backend has one data-type / layout variant, with two
fused forms (with and without the fused bias), across LoRA ranks 32 / 64
/ 96 / 128. That variant ships for sm_100a and sm_103a as the vendorable
package `flashinfer/cake_nvfp4_svdquant_gemm_backend`. This PR is a
further tuning round of the same variant. On sm_100a, two of the 28
shapes below now dispatch to a tail-split program of the same kernel,
built with the register bias path. These shapes are (M, N, K, rank,
bias) = (6912, 3072, 3072, 96, 1) and (16384, 3072, 3072, 32, 1). A
tail-split program splits the last partial wave of tiles in N, so that
wave runs on more SMs. The two shapes speed up by 1.035 and 1.012. Every
other sm_100a shape keeps the previous kernel, and so does every sm_103a
(GB300) shape. Their compiled binaries are identical to the previous
release, so this PR has no GB300 table. "Previous Cake" is the previous
Cake release of this kernel, measured in the same session as this PR's
package.

**NVIDIA GB200 (sm_100a), CUDA 13.4**

| M | N | K | rank | bias | previous Cake (µs) | this PR (µs) | speedup
vs previous Cake |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 129 | 3072 | 3072 | 32 | 1 | 5.82 | 5.82 | 1.000 ‡ |
| 129 | 3072 | 3072 | 32 | 0 | 5.73 | 5.73 | 1.000 ‡ |
| 129 | 3072 | 3072 | 64 | 1 | 5.89 | 5.89 | 1.000 ‡ |
| 129 | 3072 | 3072 | 96 | 1 | 5.98 | 5.98 | 1.000 ‡ |
| 129 | 3072 | 3072 | 128 | 1 | 6.03 | 6.05 | 0.997 ‡ |
| 129 | 3072 | 3072 | 128 | 0 | 5.98 | 6.02 | 0.993 ‡ |
| 129 | 3072 | 12288 | 32 | 0 | 12.61 | 12.61 | 1.000 ‡ |
| 129 | 3072 | 12288 | 32 | 1 | 12.64 | 12.64 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 0 | 12.80 | 12.80 | 1.000 ‡ |
| 129 | 3072 | 12288 | 128 | 1 | 12.83 | 12.83 | 1.000 ‡ |
| 6912 | 3072 | 3072 | 32 | 1 | 28.26 | 28.26 | 1.000 ‡ |
| 6912 | 3072 | 3072 | 64 | 1 | 28.72 | 28.75 | 0.999 ‡ |
| 6912 | 3072 | 3072 | 96 | 1 | 30.96 | 29.92 | 1.035 |
| 6912 | 3072 | 3072 | 128 | 1 | 30.72 | 30.80 | 0.997 ‡ |
| 6912 | 3072 | 12288 | 32 | 1 | 96.83 | 97.15 | 0.997 ‡ |
| 6912 | 3072 | 12288 | 128 | 1 | 98.83 | 99.71 | 0.991 ‡ |
| 4096 | 3072 | 3072 | 32 | 1 | 19.49 | 19.49 | 1.000 ‡ |
| 4096 | 3072 | 12288 | 32 | 1 | 62.26 | 62.11 | 1.002 ‡ |
| 4096 | 12288 | 3072 | 32 | 1 | 63.26 | 63.30 | 0.999 ‡ |
| 6889 | 3072 | 3072 | 32 | 1 | 28.19 | 28.16 | 1.001 ‡ |
| 6889 | 3072 | 12288 | 32 | 1 | 97.06 | 97.17 | 0.999 ‡ |
| 6889 | 12288 | 3072 | 32 | 1 | 105.38 | 105.42 | 1.000 ‡ |
| 9216 | 3072 | 3072 | 32 | 1 | 35.29 | 35.23 | 1.002 ‡ |
| 9216 | 3072 | 12288 | 32 | 1 | 122.82 | 123.22 | 0.997 ‡ |
| 9216 | 12288 | 3072 | 32 | 1 | 135.97 | 135.38 | 1.004 ‡ |
| 16384 | 3072 | 3072 | 32 | 1 | 64.69 | 63.90 | 1.012 |
| 16384 | 3072 | 12288 | 32 | 1 | 207.02 | 208.97 | 0.991 ‡ |
| 16384 | 12288 | 3072 | 32 | 1 | 232.74 | 233.15 | 0.998 ‡ |

‡ This shape ships the previous Cake kernel unchanged on this GPU; its
ratio is the same-kernel control reading of the session.

Cake ships no other data-type, layout or fused-form variant of this
kernel beyond the one above (with and without the fused bias), and the
family ships on sm_100a and sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized NVFP4 SVD-quantized GEMM routes for select large
workloads on supported GPU architectures, including tail-split
processing.

* **Bug Fixes**
* Updated kernel synchronization and memory handling across GEMM
variants for more reliable execution.
  * Adjusted output-store handling for specific tail-split workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5629173](https://github.com/flashinfer-ai/flashinfer/commit/562917330db68299ba5a393c3305210eb4e2d2a7)

- **作者**: eigen
- **时间**: 2026-10-23T08:08:06Z
- **提交信息**: perf(cake_gdp): interleave a warp's two state rows in the T = 1 split-V decode kernel on SM100 / SM103 (#7086)

The Cake Gated DeltaProduct decode kernel
(`flashinfer.cake_gdp.cake_gated_delta_product_mtp`) has one variant:
BF16 q / k / v / output with an FP32 recurrent state in a slot-indexed
state pool, 1 <= T <= 16 tokens per sequence, K = 128, V = 64 and 1 <= n
<= 4 Householder sub-steps, with programs for sm_90a, sm_100a and
sm_103a. This PR makes that variant's single-sequence (B = 1) T = 1
decode kernel faster on sm_100a / sm_103a: the split-V T = 1 program now
runs a warp's two recurrent-state rows as two interleaved dependency
chains. Only that one kernel changes; the other 39 compiled entries,
including all sm_90a kernels, are machine-code-identical to the previous
package, and the public API is unchanged. The baseline is the previous
Cake version of this kernel, the Cake GDP decode package of FlashInfer
PR #7080; both packages ran in the same process on the same GPU with the
same inputs (A_log f32, dt_bias f32, q/k/v/a/b bf16, n = 3), interleaved
A B B A over 3 groups x 32 samples per call, with cold L2 and kernel
time measured; speedup = previous / this PR. Across 48 shapes (HV in
{80, 20, 10, 24} x B in {1, 16, 64, 256} x T in {1, 4, 8}), the speedup
is 0.99-1.07 on GB300 and 0.98-1.08 on B200. The four B = 1, T = 1 rows
run the changed kernel and read 1.03-1.07 on GB300 and 1.03-1.08 on
B200; the other 44 rows run unchanged kernels and are expected to read
about 1.00.

**NVIDIA GB300 (sm_103a), CUDA 13.4.92 -- 48 rows, speedup 0.99-1.07**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.4 | 4.3 | 1.03 |
| 80 | 1 | 4 | 6.0 | 6.0 | 0.99 |
| 80 | 1 | 8 | 8.1 | 8.1 | 1.00 |
| 80 | 16 | 1 | 20.1 | 20.3 | 0.99 |
| 80 | 16 | 4 | 24.8 | 24.8 | 1.00 |
| 80 | 16 | 8 | 40.1 | 40.0 | 1.00 |
| 80 | 64 | 1 | 62.0 | 62.0 | 1.00 |
| 80 | 64 | 4 | 76.1 | 76.1 | 1.00 |
| 80 | 64 | 8 | 131.5 | 131.5 | 1.00 |
| 80 | 256 | 1 | 227.8 | 228.5 | 1.00 |
| 80 | 256 | 4 | 282.2 | 282.2 | 1.00 |
| 80 | 256 | 8 | 499.9 | 499.9 | 1.00 |
| 20 | 1 | 1 | 3.6 | 3.4 | 1.06 |
| 20 | 1 | 4 | 5.5 | 5.5 | 0.99 |
| 20 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 20 | 16 | 1 | 7.6 | 7.6 | 1.01 |
| 20 | 16 | 4 | 10.9 | 11.0 | 0.99 |
| 20 | 16 | 8 | 16.6 | 16.7 | 1.00 |
| 20 | 64 | 1 | 20.4 | 19.8 | 1.03 |
| 20 | 64 | 4 | 24.5 | 24.5 | 1.00 |
| 20 | 64 | 8 | 40.0 | 40.0 | 1.00 |
| 20 | 256 | 1 | 60.3 | 60.2 | 1.00 |
| 20 | 256 | 4 | 76.2 | 76.3 | 1.00 |
| 20 | 256 | 8 | 131.6 | 131.6 | 1.00 |
| 10 | 1 | 1 | 3.5 | 3.3 | 1.07 |
| 10 | 1 | 4 | 5.4 | 5.4 | 1.00 |
| 10 | 1 | 8 | 7.5 | 7.5 | 1.00 |
| 10 | 16 | 1 | 5.6 | 5.5 | 1.01 |
| 10 | 16 | 4 | 8.2 | 8.1 | 1.01 |
| 10 | 16 | 8 | 11.9 | 11.9 | 1.00 |
| 10 | 64 | 1 | 11.2 | 11.1 | 1.01 |
| 10 | 64 | 4 | 16.0 | 15.9 | 1.01 |
| 10 | 64 | 8 | 25.0 | 25.1 | 0.99 |
| 10 | 256 | 1 | 34.0 | 34.0 | 1.00 |
| 10 | 256 | 4 | 41.5 | 41.7 | 1.00 |
| 10 | 256 | 8 | 69.8 | 69.8 | 1.00 |
| 24 | 1 | 1 | 3.6 | 3.4 | 1.06 |
| 24 | 1 | 4 | 5.6 | 5.6 | 1.00 |
| 24 | 1 | 8 | 7.6 | 7.6 | 1.00 |
| 24 | 16 | 1 | 8.1 | 8.0 | 1.00 |
| 24 | 16 | 4 | 11.5 | 11.4 | 1.00 |
| 24 | 16 | 8 | 17.2 | 17.2 | 1.00 |
| 24 | 64 | 1 | 22.9 | 22.3 | 1.03 |
| 24 | 64 | 4 | 28.1 | 28.4 | 0.99 |
| 24 | 64 | 8 | 46.9 | 47.0 | 1.00 |
| 24 | 256 | 1 | 71.0 | 71.2 | 1.00 |
| 24 | 256 | 4 | 90.1 | 90.2 | 1.00 |
| 24 | 256 | 8 | 156.5 | 156.4 | 1.00 |

**NVIDIA B200 (sm_100a), CUDA 13.4.92 -- 48 rows, speedup 0.98-1.08**

| HV (heads) | B (batch) | T (tokens) | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|---:|---:|---:|
| 80 | 1 | 1 | 4.6 | 4.5 | 1.03 |
| 80 | 1 | 4 | 6.3 | 6.3 | 1.00 |
| 80 | 1 | 8 | 8.6 | 8.6 | 1.00 |
| 80 | 16 | 1 | 21.5 | 21.2 | 1.01 |
| 80 | 16 | 4 | 26.4 | 26.5 | 1.00 |
| 80 | 16 | 8 | 43.5 | 43.6 | 1.00 |
| 80 | 64 | 1 | 65.3 | 65.6 | 1.00 |
| 80 | 64 | 4 | 83.3 | 83.3 | 1.00 |
| 80 | 64 | 8 | 145.0 | 145.0 | 1.00 |
| 80 | 256 | 1 | 245.2 | 245.2 | 1.00 |
| 80 | 256 | 4 | 306.4 | 306.3 | 1.00 |
| 80 | 256 | 8 | 544.2 | 544.3 | 1.00 |
| 20 | 1 | 1 | 3.8 | 3.6 | 1.06 |
| 20 | 1 | 4 | 5.8 | 5.8 | 0.99 |
| 20 | 1 | 8 | 8.0 | 8.1 | 0.99 |
| 20 | 16 | 1 | 8.0 | 8.1 | 0.99 |
| 20 | 16 | 4 | 11.6 | 11.6 | 1.00 |
| 20 | 16 | 8 | 17.8 | 17.8 | 1.00 |
| 20 | 64 | 1 | 21.2 | 21.4 | 0.99 |
| 20 | 64 | 4 | 26.5 | 26.7 | 0.99 |
| 20 | 64 | 8 | 43.6 | 43.6 | 1.00 |
| 20 | 256 | 1 | 64.1 | 64.0 | 1.01 |
| 20 | 256 | 4 | 83.4 | 83.4 | 1.00 |
| 20 | 256 | 8 | 145.0 | 145.0 | 1.00 |
| 10 | 1 | 1 | 3.7 | 3.4 | 1.08 |
| 10 | 1 | 4 | 5.7 | 5.7 | 1.00 |
| 10 | 1 | 8 | 8.0 | 8.0 | 1.00 |
| 10 | 16 | 1 | 5.9 | 5.7 | 1.03 |
| 10 | 16 | 4 | 8.6 | 8.5 | 1.01 |
| 10 | 16 | 8 | 12.9 | 12.7 | 1.01 |
| 10 | 64 | 1 | 11.7 | 11.7 | 1.00 |
| 10 | 64 | 4 | 16.9 | 17.1 | 0.99 |
| 10 | 64 | 8 | 27.4 | 27.4 | 1.00 |
| 10 | 256 | 1 | 35.8 | 36.4 | 0.98 |
| 10 | 256 | 4 | 46.0 | 45.9 | 1.00 |
| 10 | 256 | 8 | 78.6 | 78.6 | 1.00 |
| 24 | 1 | 1 | 3.8 | 3.6 | 1.06 |
| 24 | 1 | 4 | 5.8 | 5.8 | 1.00 |
| 24 | 1 | 8 | 8.1 | 8.1 | 1.00 |
| 24 | 16 | 1 | 8.4 | 8.4 | 0.99 |
| 24 | 16 | 4 | 12.1 | 12.2 | 0.99 |
| 24 | 16 | 8 | 18.4 | 18.5 | 1.00 |
| 24 | 64 | 1 | 24.3 | 23.8 | 1.02 |
| 24 | 64 | 4 | 30.6 | 30.6 | 1.00 |
| 24 | 64 | 8 | 51.3 | 51.4 | 1.00 |
| 24 | 256 | 1 | 74.5 | 74.7 | 1.00 |
| 24 | 256 | 4 | 98.5 | 98.7 | 1.00 |
| 24 | 256 | 8 | 171.9 | 171.9 | 1.00 |

This variant is the kernel family's only data-type form; Cake ships it
on sm_90a (H100 / H200), sm_100a (B200 / GB200) and sm_103a (B300 /
GB300), and this PR changes only one sm_100a / sm_103a kernel (the T = 1
split-V program).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved processing of paired output rows and state updates, including
handling of valid state slots.
* **Performance**
  * Updated the GPU kernel’s row-processing behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4f88101](https://github.com/flashinfer-ai/flashinfer/commit/4f88101e601728e1c701939d78a46471c7bb976e)

- **作者**: eigen
- **时间**: 2026-10-23T08:02:04Z
- **提交信息**: fix(cake_kda): keep no workspace alive across activation checkpointing and skip the arena zero fill; with grad (#7069)

Under non-reentrant `torch.utils.checkpoint`, only tensors saved with
`save_for_backward` are freed after the forward, but `chunk_kda` stored
the caller's `workspace` on the autograd context, so each checkpointed
layer kept its per-call arena alive until its backward (the KDA part of
#7039). `ChunkKDAFunction` now holds the workspace through a weak
reference: a workspace the caller keeps is still reused by the backward,
while a per-call workspace dropped after the forward is freed at once
and the backward allocates its own. Separately, `KdaWorkspace`
zero-filled its arena by default, so calls with the implicit workspace
(no `workspace=`) paid a fill in every forward and backward, although
every element a launch reads is written earlier in the same call (part 1
of #7040; part 2, a lower-memory arena option, is not in this PR).
`zero_init` now defaults to `False` (`torch.empty`), `zero_init=True`
remains for diagnostics, and the README's workspace section documents
both behaviors; public signatures (parameter lists) are unchanged. New
tests check that a checkpointed forward retains 0 bytes beyond its
output for implicit, per-call and caller-owned workspaces (gradients
equal to the explicit path), that the autograd node holds the workspace
weakly, and that a NaN-filled arena reproduces the zero-filled results
bit for bit on every path.

Measured with the issues' repro scripts on one NVIDIA GB300 (sm_103a),
CUDA 13.0 build of PyTorch 2.14.1, S = 261393 tokens in 4 documents;
before = current main, after = this branch. Gradients of the implicit
and the unzeroed-workspace runs are bitwise equal before and after.

| H | measure | before | after |
|---|---|---|---|
| 4 | kept after a checkpointed forward, per-call workspace | 4482.1 MiB
| 0.0 MiB |
| 4 | kept after a checkpointed forward, implicit workspace | 0.0 MiB |
0.0 MiB |
| 16 | kept after a checkpointed forward, per-call workspace | 17926.0
MiB | 0.0 MiB |
| 16 | kept after a checkpointed forward, implicit workspace | 0.0 MiB |
0.0 MiB |
| 4 | forward + backward, implicit workspace (median of 7) | 6.48 ms |
4.66 ms |
| 4 | forward + backward, per-call unzeroed workspace (median of 7) |
4.65 ms | 4.65 ms |
| 16 | forward + backward, implicit workspace (median of 7) | 26.10 ms |
18.83 ms |
| 16 | forward + backward, per-call unzeroed workspace (median of 7) |
18.83 ms | 18.81 ms |

Refs #7039, #7040.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Workspaces now default to uninitialized memory, which can reduce
initialization overhead. Enable zero initialization when zero-filled
memory is needed for diagnostics.
* Backward computation uses a supplied workspace while it remains
available; otherwise, it allocates a workspace as needed. Checkpointed
forwards no longer keep a workspace or saved tensor alive through the
autograd node.
* **Documentation**
* Clarified workspace initialization, lifetime, and allocation behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8e8342f](https://github.com/flashinfer-ai/flashinfer/commit/8e8342f909d4422c67d3e83b94aa8a5e94a68824)

- **作者**: Yilin Zhang
- **时间**: 2026-10-23T07:08:22Z
- **提交信息**: feat(attention): add SM12x FP8 prefill attention support for GLM-4.7 and GLM-4.7-Flash (#6466)

## 📌 Description

Enable causal FP8 E4M3-to-BF16 prefill for GLM-4.7-Flash MLA context and
GLM-4.7 GQA through `fmha_v2_prefill_deepseek`.

| Model | QK / V head dimensions | Query / KV heads |
|---|---|---|
| GLM-4.7-Flash | 256 / 256 | 20 / 20 |
| GLM-4.7 | 128 / 128 | 96 / 8 |

GLM-4.7-Flash uses expanded per-head Q/K/V for dense context attention.
Its QK dimension is 192 NoPE + 64 RoPE; the compressed latent KV cache
is outside this API's input contract.

- Add a 256/256 specialization using the existing tiled FMHA v2
template, including code generation, JIT compilation and C++ dispatch.
- Route 128/128 inputs to the existing D128 specialization and 256/256
inputs to the new specialization.
- Enable GQA by indexing K/V with `query_head / heads_per_kv`, while
retaining the query-head index for Q.
- Extend shape/head-count validation, trace metadata, references,
examples and tests.

The existing DeepSeek 192/128 path is retained.

## 🧪 Validation

Validated on one 5K Pro GPU (SM120, 110 SMs), with CUDA 13.0 and PyTorch
2.13.0+cu130:

- 63 targeted attention tests passed, including 256/256 with 20 heads
and the TP4-shaped 5-head case, retained 128/128 GQA coverage, and
existing MHA/DeepSeek regressions.
- Coverage includes host/device scale overrides, LSE, CUDA Graph replay,
sequence tails, batch offsets, metadata validation, and standard
causal/noncausal attention.
- 6 CPU trace consistency tests passed; affected fixtures were checked
against the actual metadata exporter.
- Full FP32 references passed for all six benchmark geometries,
including 4K and 8K sequences. FP8 checks retain `rtol=0.04, atol=0.06`
and use dequantized FP8 inputs, excluding initial Q/K/V quantization
error.
- Changed-file pre-commit checks passed, including clang-format, mypy
and Ruff.

The full repository test suite has not been run.

### Performance

GLM-4.7-Flash geometry: batch size 1, causal attention, QK/V=256/256 and
BF16 output. Latencies are medians of 50 CUDA Graph samples per
backend/configuration, collected over five randomized rounds, with 10
calls per graph and repeated Q/K/V/output buffers.

| Heads | Sequence length | FP8 FMHA v2 (µs) | BF16 FMHA v2, matched
tile (µs) | BF16 FA2 (µs) | Speedup vs. matched BF16 | Speedup vs. BF16
FA2 |
|---:|---:|---:|---:|---:|---:|---:|
| 20 | 1024 | 68.88 | 105.33 | 103.54 | 1.53× | 1.50× |
| 20 | 4096 | 782.40 | 1241.56 | 1110.74 | 1.59× | 1.42× |
| 20 | 8192 | 2975.75 | 4690.40 | 4077.53 | 1.58× | 1.37× |
| 5 | 1024 | 30.35 | 47.07 | 43.59 | 1.55× | 1.44× |
| 5 | 4096 | 243.48 | 387.44 | 377.05 | 1.59× | 1.55× |
| 5 | 8192 | 803.80 | 1290.77 | 1133.70 | 1.61× | 1.41× |

The matched BF16 control uses the same FMHA v2 algorithm template, 64×64
logical tile, 128 threads, separate Q/K/V layout and FP32 accumulation.
Its BF16 256/256 specialization and launcher were added only in an
isolated benchmark source copy; they are not part of this PR.
Dtype-specific MMA instructions, intermediate representations and
staging follow the existing BF16/FP8 traits. Both variants passed
correctness checks. This control measures the benefit of the FP8
instantiation with the logical configuration held fixed; BF16 FA2
provides an additional reference and was faster than the matched BF16
control in all six measured shapes.

Additional rotating-buffer measurements show 1.30–1.58× speedup over the
matched BF16 control and 1.11–1.38× over BF16 FA2 across the same
shapes; this is a buffer-rotation policy, not a guarantee of zero L2
hits.

Timing covers attention execution only, with LSE disabled. Quantization,
dequantization, layout packing, planning, compilation and projections
are excluded. BF16 baselines consume the same FP8 values dequantized and
cast to BF16. Five heads represent a TP4 shard shape measured on one
GPU, not distributed TP4 inference.

The matched FMHA v2 control compares different dtype instantiations of
the same algorithm template; the FA2 comparison also changes the
backend. The previously unsupported FP8 256/256 path has no pre-change
latency baseline.

## Reviewer Notes

- Release compilation of the causal FP8 kernels reports 183
registers/thread for 128/128 and 233 registers/thread for 256/256, with
zero spill loads/stores and zero stack-frame usage.
- The isolated matched BF16 control uses 247 registers/thread, also with
zero spill loads/stores and zero stack-frame usage.
- Runtime profiling confirms 64 KiB dynamic shared memory for 256/256.
Its current shared-memory footprint limits residency to one block per
SM.
- Hardware validation covers the 5K Pro SM120 device. RTX 5090, SM121,
full-model serving and distributed tensor parallelism have not been
tested.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added FP8 E4M3 prefill support for grouped-query and multi-query
attention, including configurations with fewer key/value heads than
query heads.
* Expanded supported attention head dimensions to include 256 for
applicable SM120 and DeepSeek prefill paths.
* Added support for separate query/key and value head dimensions in
DeepSeek prefill.
  * Extended scale handling to support device-provided scale values.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b17eaa0](https://github.com/flashinfer-ai/flashinfer/commit/b17eaa011241866e45a3ea06797c5fecaf6c7bc7)

- **作者**: Yilin Zhang
- **时间**: 2026-10-23T07:06:27Z
- **提交信息**: perf(moe_ep): add folded K128/N64 tuning candidate for Hopper MXFP4 x FP8 MegaMoE (#6465)

## 📌 Description

Expand the bounded tuning candidates for Hopper MXFP4 × FP8 MegaMoE,
motivated by the latency observed on a **Qwen3.8-Flash-Next-style routed
MoE workload**.

For an intermediate size of 640, K256 configurations are filtered out by
alignment requirements, leaving three eligible configurations in the
existing candidate pool. The pool misses useful K128 configurations
across different token counts.

### Changes

Add five measured M256/K128 configurations:

- An N16, cluster `(1,1,1)`, group-330 configuration with two dispatch
warps and FC1 store offload.
- Folded N64, cluster `(1,1,1)` configurations with group hints 132,
264, and 330.
- A folded N64, cluster `(1,2,1)`, group-132 configuration with
tail-pair scheduling.

All five use one scheduler stage. The folded configurations use one
dispatch warp, early FC1 publication, and direct FC1 stores.

For the target shape, the eligible candidate pool grows from **3 to 8
configurations**. Existing heuristic defaults are preserved; autotuning
selects among the expanded candidates.

### Benchmark configuration

- **GPU:** 2× NVIDIA H200, connected through NVLink.
- **Input:** `[tokens_per_rank, 2560]` per rank; EP=2.
- **Experts:** 512 total, 256 per rank; top-k=10; uniform expert load.
- **Intermediate size:** 640 after SwiGLU; gate/up projection
width=1280.
- **Precision:** MXFP4 weights with K32 scaling, FP8 activations, BF16
input/output.

### Performance

Both columns report tuned performance: the best of the original **3
candidates** versus the best of the **8 candidates available with this
PR**.

Selection minimizes Compute latency; operator E2E is reported from the
same selected configuration. Each configuration uses 10 warmups and 50
CUDA-event samples. The reported latency is the maximum of the two
ranks’ median latencies. Before/after comparisons use measurements from
the same tuning process at each token count.

All latencies are in **µs**. Latency reduction is calculated as
`(original − PR) / original × 100%`.

| Tokens/rank | Original Compute | PR Compute | Reduction | Original E2E
| PR E2E | Reduction |
|---:|---:|---:|---:|---:|---:|---:|
| 128 | 339.216 | 316.272 | 6.76% | 501.264 | 475.856 | 5.07% |
| 256 | 348.656 | 337.296 | 3.26% | 501.024 | 503.712 | −0.54% |
| 512 | 371.056 | 371.056 | 0.00% | 560.656 | 560.656 | 0.00% |
| 1024 | 593.264 | 488.128 | 17.72% | 756.176 | 643.296 | 14.93% |
| 2048 | 865.456 | 834.848 | 3.54% | 1033.200 | 999.984 | 3.21% |
| 4096 | 1405.728 | 1315.200 | 6.44% | 1573.472 | 1475.216 | 6.24% |
| 8192 | 2670.336 | 2343.024 | 12.26% | 2891.616 | 2560.176 | 11.46% |
| 16384 | 5223.024 | 4442.880 | 14.94% | 5628.496 | 4873.776 | 13.41% |

**Compute** includes prestaged MegaMoE execution, EP communication, and
final top-k reduction. **Operator E2E** additionally includes input
quantization/staging and output copy; weight preparation and JIT
compilation are excluded. These are operator measurements, not model
TTFT.

At 256 tokens/rank, the configuration selected by Compute is 2.688 µs
slower in operator E2E. At 512 tokens/rank, the original configuration
remains selected.

### Validation

- All five added configurations passed numerical checks on both ranks at
all eight token counts.
- Each token count’s selected winner also passed an independent replay.
- The existing host test suite passed all 23 tests.
- Pre-commit checks passed for the changed files.
- No new test files were added.

Measurements were collected with the exact registered configurations
using `repro_driver.py` on pinned source `2394fa705`; the final branch
was not separately timed. The workload uses synthetic weights and
balanced routing rather than a full model execution.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Performance**
- Expanded MXFP4 tuning options to improve performance across additional
model shapes and configurations.
- Added support for more tile, warp, cluster, and tail-processing
combinations while preserving existing heuristic defaults.

- **Bug Fixes**
- Improved validation for folded and tail-processing MXFP4 execution
paths, including partial tile routing scenarios.

- **Tests**
- Added coverage for expert-parallel MXFP4 workloads with nonstandard
token counts and both complete and partial tiles.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4695
- **最后更新**: 2026-10-23T19:40:55Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Aryan Kumar, posiposi443-ops

## AI分析总结

# FastVideo 昨日提交分析总结

## 1. 主要更新类型
本次提交以**性能优化**为主，辅以**CI/CD 流程强化**。没有新增功能或修复 Bug，而是围绕 MLX（Apple Silicon）推理路径做了性能提升和持续集成的保障机制。

## 2. 关键变更点及与项目方向的关系

- **性能优化（`8db2d71`）**：对 MLX 后端的 H3 文本精炼（text refinement）结果进行了缓存，并对注意力（attention）计算做了加速。这直接呼应 FastVideo 作为"快速视频生成"框架的核心使命——降低推理延迟、提升吞吐量。在 Apple Silicon 设备上运行视频扩散模型时，文本编码和注意力往往是瓶颈，缓存与优化属于精准的热点治理。
- **CI 强化（`1a1e721`、`33bdd25`）**：引入两条规则——当草稿 PR 被标记为 ready 时触发 macOS MLX 冒烟测试；凡是触碰 MLX 相关代码的 PR 都必须通过该冒烟测试。这表明 MLX 支持已经从实验性功能上升为需要严格质量守护的一等公民。

## 3. 对项目的影响和潜在意义

- **性能层面**：MLX 路径的推理速度提升，使 Mac 用户（尤其是 M 系列芯片）获得更具竞争力的本地视频生成体验，扩大了目标用户群。
- **工程质量层面**：强制的冒烟测试门槛能有效防止 MLX 代码回归，减少"改了核心代码但没人验证"的风险，为后续 MLX 相关功能的持续迭代奠定了可靠的基线。
- **社区协作层面**：`ready` 触发机制允许贡献者在草稿阶段免于频繁跑 CI，降低协作摩擦，同时不牺牲合入质量。

## 4. 值得关注的技术点

- **H3 文本精炼缓存**：文本条件在视频生成中往往重复使用，缓存精炼结果可避免重复计算，是一种低成本高回报的优化手段。
- **注意力加速**：MLX 框架本身的算子融合能力被进一步利用，值得观察具体采用了何种 kernel 优化策略（如 MQA/GQA 或 fused attention）。
- **分层 CI 策略**：按代码影响范围（touch MLX）精准触发测试，体现了"最小必要验证"的现代 CI 设计理念。

## 5. 对项目整体发展的影响

结合 README 可知，FastVideo 是一个面向快速视频生成/推理的开源框架，配有完善的文档、Cookbook 和社区机制。本次提交虽规模不大，但传递了清晰信号：项目正**深度投入 Apple Silicon 生态的性能打磨**，并通过 CI 机制将其固化为长期承诺。这种"性能优化 + 质量守护"双轮驱动的节奏，有助于 FastVideo 在多硬件平台（NVIDIA/Apple）上保持一致的高性能表现，吸引更多本地部署场景的用户和贡献者，对项目的跨平台竞争力具有积极而持续的推动作用。

## 详细提交记录

### [8db2d71](https://github.com/hao-ai-lab/FastVideo/commit/8db2d71ef217e84bec7dbb6e4ab65c92b144df4f)

- **作者**: posiposi443-ops
- **时间**: 2026-10-23T19:40:47Z
- **提交信息**: [perf] Cache MLX H3 text refinement and speed up attention (#2002)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [1a1e721](https://github.com/hao-ai-lab/FastVideo/commit/1a1e7216d2bb04ca757b82e4e387078aa0204a35)

- **作者**: Aryan Kumar
- **时间**: 2026-10-23T18:34:07Z
- **提交信息**: [ci]: Run macOS MLX smoke when a draft PR is marked ready

### [33bdd25](https://github.com/hao-ai-lab/FastVideo/commit/33bdd2528b9123835fb210ffb5f577542654eec0)

- **作者**: Aryan Kumar
- **时间**: 2026-10-23T18:23:35Z
- **提交信息**: [ci]: Require macOS MLX smoke for PRs that touch MLX code

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34786
- **最后更新**: 2026-10-23T23:16:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
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


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13294
- **最后更新**: 2026-10-23T22:59:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37677
- **最后更新**: 2026-10-24T00:40:09Z

## 提交统计

- **昨日提交总数**: 60
- **提交者数量**: 31
- **主要提交者**: Byron Hsu, Shangming Cai, Xinyuan Tong

## AI分析总结

# SGLang 昨日提交分析（60条记录）

## 1. 主要更新类型

- **Bug修复（约25条）**：占比最高，涵盖MoE路由、扩散模型、AMD/NPU后端、LoRA、离线加载等多个子系统。
- **功能新增（约14条）**：集中在Rust服务端、平台扩展性、基准测试、新模型支持（GLM5.3、DeepSeek-V4、MTP KV分片）。
- **性能优化（约12条）**：扩散模型推理、logits计算、模型门控等热点路径优化。
- **CI/测试（约10条）**：NPU、AMD、XPU、分布式等多硬件平台的测试流程改进。
- **文档与重构（约5条）**：量化设计文档、缓存树代码结构化等。

## 2. 关键变更点与项目方向的关系

- **Rust服务端持续成熟**：多项提交围绕Rust前端的中止请求（abort）、多模态布局处理、预填充端口管理展开，表明项目正推动Python调度器与Rust HTTP层的深度整合，以提升推理服务的生产可用性。
- **扩散（Diffusion）模型全面发力**：约18条提交涉及扩散模型，包括LoRA动态权重、并行解码、OpenAI API兼容、LTX/Wan/Cosmos/FLUX等多个模型的修复与性能优化，显示SGLang正从LLM推理平台扩展为**多模态/生成式推理统一平台**。
- **多硬件生态（AMD、Intel NPU、Intel XPU、NVIDIA）**：CI和后端修复覆盖多个硬件厂商，呼应README中"快速推理"的跨平台目标。
- **MoE与量化健壮性**：多条提交"Preserve ... budgets/metadata"聚焦MoE（CUTLASS、Marlin、GGUF、LoRA）的元数据与资源预算保护，属于大规模MoE模型（如DeepSeek-V4）落地的关键稳定性工作。
- **分层缓存与分离式架构**：HiCache L3（文件/Mooncake）、PD分离下的预填充承诺、心跳恢复等，支撑超长上下文和高吞吐部署。

## 3. 对项目的影响和潜在意义

- **稳定性提升**：大量"Preserve/Keep"类修复减少了MoE、扩散、KV缓存路径上的隐性回归风险，降低生产环境踩坑概率。
- **服务端能力补全**：Rust端支持abort请求、Granian keep-alive超时等，使异步/流式服务行为更接近标准HTTP服务器预期。
- **生态扩展**：平台自定义算子绑定（out-of-tree platforms）、checkpooint驱动的响应模板适配器等，降低第三方模型/硬件接入门槛。
- **文档与基准完善**：--input-len-list基准参数、Cookbook更新，有利于用户复现与调优。

## 4. 值得关注的技术点

- **Triton kernel用于bf16→fp32 logits转换**（#46167）：端到端性能微优化的典型范式。
- **Triton+扩散：IPC all-to-all避开expandable segments**（#45948）：多GPU显存分配器的深层交互问题。
- **HiCache与MLA DCP结合**（#41187）：将DeepSeek MLA注意力与三级缓存打通，是长上下文推理的关键组合。
- **KVShard支持MTP的KV分片**（#40929）：为多token预测（Multi-Token Prediction）提供缓存扩展性。
- **Inkling BF16 LM-head/FP32输出分离**（#45335）与自定义渲染器（#45340）：新推理内核/算子子系统的早期信号。

## 5. 对项目发展的总体影响

结合README所述"SGLang：面向LLM与多模态模型的快速推理"目标，昨日提交呈现三条主线：**其一**，推理性能持续打磨（logits、MoE门控、扩散去噪开销）；**其二**，多模态与扩散模型成为第二增长曲线，功能与稳定投入显著；**其三**，基础设施（Rust服务端、分层缓存、多硬件CI）日趋完善，支撑从研究原型向生产系统的演进。这些改动共同推动SGLang向"统一、高性能、多硬件可用的生成式推理引擎"演进，短期内将提升部署可靠性，中长期则拓宽了可服务的模型与硬件生态。

## 详细提交记录

### [6a319e7](https://github.com/sgl-project/sglang/commit/6a319e7b3446f39edd19d3d76aec4c6a2851b28d)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-23T23:48:08Z
- **提交信息**: [Fix] muse: Support Responses namespace tools and defer_loading (#44685)

Co-authored-by: sid-rp <sidrp@meta.com>

### [0d592c4](https://github.com/sgl-project/sglang/commit/0d592c475bca778a06116f2c05ac282b9c6491fa)

- **作者**: metamergebot
- **时间**: 2026-10-23T23:47:14Z
- **提交信息**: [Fix] rust-server: Keep a transfer backend's own bootstrap port on prefill (#46066)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [855c092](https://github.com/sgl-project/sglang/commit/855c092deb93104f1ad2844974fd2e4da7bb90f7)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T22:51:44Z
- **提交信息**: [Fix] inkling: Keep BF16 LM-head operands with FP32 output (#45335)

### [197be22](https://github.com/sgl-project/sglang/commit/197be2203ae6906db3959a566799195d9e41f102)

- **作者**: Ziang Li
- **时间**: 2026-10-23T22:49:18Z
- **提交信息**: [Doc] quantization: Link W4A16 design from environment reference (#46170)

### [f05ad5e](https://github.com/sgl-project/sglang/commit/f05ad5ec0139d1a41e04115384f6f03b0ac4d19f)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-23T22:06:09Z
- **提交信息**: [Perf] logits: Cast bf16 logits into the fp32 buffer with a Triton kernel (#46167)

### [15dc838](https://github.com/sgl-project/sglang/commit/15dc838f9bf5cb709468791fb520d9157ec66715)

- **作者**: Rohan Varma
- **时间**: 2026-10-23T21:43:54Z
- **提交信息**: [Fix] http_server: Apply SGLANG_TIMEOUT_KEEP_ALIVE to Granian HTTP/1.1 connections (#45760)

Signed-off-by: Rohan Varma <rohanv@nvidia.com>
Co-authored-by: Jun Wan <8323392+junwan01@users.noreply.github.com>

### [ea226cf](https://github.com/sgl-project/sglang/commit/ea226cf78267816a412defd32fb7e1d0853bfec3)

- **作者**: Baizhou Zhang
- **时间**: 2026-10-23T21:21:31Z
- **提交信息**: [Feat] glm5.3flash: Support padded CP BCG and prefix replay with PD/DFlash2 (#43774)

### [5f7542d](https://github.com/sgl-project/sglang/commit/5f7542d7627f6178d5a7e9ab1e3d2ca5af4d252e)

- **作者**: Yuhao Yang
- **时间**: 2026-10-23T21:15:01Z
- **提交信息**: [Perf] dsv41: Build the MegaGate row masks once per forward (#46071)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [27ac614](https://github.com/sgl-project/sglang/commit/27ac614f051f18de577f6f0f980d1c5cd83d7963)

- **作者**: Yoni Gozlan
- **时间**: 2026-10-23T21:05:54Z
- **提交信息**: [Feat] parser: Add checkpoint-driven response-template adapters (#40479)

Signed-off-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Yoni Gozlan <yonigozlan@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [4542fc8](https://github.com/sgl-project/sglang/commit/4542fc8f598e55d90f655de482b1b5cdf7c6228f)

- **作者**: em-dreyer
- **时间**: 2026-10-23T21:05:32Z
- **提交信息**: [Fix] mistral3: Subclass LlavaForConditionalGeneration instead of wrapping it (#45656)

### [194abb8](https://github.com/sgl-project/sglang/commit/194abb8e54a8db2144c9ee7f61e391b9eea00738)

- **作者**: Michael
- **时间**: 2026-10-23T20:26:56Z
- **提交信息**: [CI] [AMD] diffusion: Drain the Cosmos Dreams decode stream after freeing its outputs (#45983)

### [1d605b7](https://github.com/sgl-project/sglang/commit/1d605b7ece8e37291807f1098f82c8d0d1ca0ed7)

- **作者**: em-dreyer
- **时间**: 2026-10-23T20:20:06Z
- **提交信息**: [CI] vlm: Harden fixture cleanup after setup and shutdown failures (#45461)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Alison Shao <a.shao@wustl.edu>

### [005333d](https://github.com/sgl-project/sglang/commit/005333d0296ecc8b8432730454a4715e13e7ee72)

- **作者**: metamergebot
- **时间**: 2026-10-23T19:49:30Z
- **提交信息**: [Refactor] radix-tree: Make each cache action a typed CacheAction implementation (#45444)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [d0022e1](https://github.com/sgl-project/sglang/commit/d0022e1df3fd71a439ad4cf58429e4ec0336b2f8)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T19:32:55Z
- **提交信息**: [Fix] lora: Preserve MoE projection identity and routing lifetimes (#45681)

### [ac3db73](https://github.com/sgl-project/sglang/commit/ac3db731b3f93e5af1896667ac0bf5734043af94)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T19:32:05Z
- **提交信息**: [Fix] moe: Preserve CUTLASS routing metadata and execution budgets (#45917)

### [8b9b992](https://github.com/sgl-project/sglang/commit/8b9b992e417a950ad57883ee6903ef04d6b3fa5c)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T19:31:17Z
- **提交信息**: [Perf] moe: Preserve Marlin workspace and route-count budgets (#45462)

### [0931dfe](https://github.com/sgl-project/sglang/commit/0931dfedc9614e1369834ec1e356ec011afa7b27)

- **作者**: Pawel Kowalski
- **时间**: 2026-10-23T19:30:42Z
- **提交信息**: [Fix] [AMD] dsa: Fix AITER prefill with an FP8 KV cache (#39083)

Co-authored-by: Pawel Kowalski <pawel.kowalski@silo.ai>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [e6451c1](https://github.com/sgl-project/sglang/commit/e6451c1a956d6140df13841943bdec68671e506c)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T19:29:51Z
- **提交信息**: [Fix] gguf: Preserve MoE routing, weighting and allocation budgets (#45916)

### [1340044](https://github.com/sgl-project/sglang/commit/1340044e9763b7de7c22aaf8be317afd0f8826d8)

- **作者**: Cheng Wan
- **时间**: 2026-10-23T19:28:43Z
- **提交信息**: [Fix] deepseek-v4: Preserve decoder-tail token-count ownership (#45915)

### [9d7ad30](https://github.com/sgl-project/sglang/commit/9d7ad308bdbb253ba736f201475c8e798ff4b8fe)

- **作者**: Clint
- **时间**: 2026-10-23T19:11:21Z
- **提交信息**: [Fix] [AMD] Quark: fix Quark block-FP8 loading in DeepSeek loader (#40776)

Co-authored-by: clintg6 <7388379+clintg6@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Bowen Bao <bowenbao@amd.com>
Co-authored-by: Hubert Lu <Hubert.Lu@amd.com>

### [baf80c6](https://github.com/sgl-project/sglang/commit/baf80c61b7ea41878bb1cf63b962cbe81dfee194)

- **作者**: Alex Nails
- **时间**: 2026-10-23T19:02:42Z
- **提交信息**: [Feat] platforms: Let out-of-tree platforms bind group devices and custom ops (#45897)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1e894eb](https://github.com/sgl-project/sglang/commit/1e894eb92d403062cf21e2910dba888cad7adb9e)

- **作者**: Shangming Cai
- **时间**: 2026-10-23T17:41:39Z
- **提交信息**: [CI] disaggregation: Run the SWA decode radix cache test on Mooncake (#46126)

### [16aa816](https://github.com/sgl-project/sglang/commit/16aa8160606d2c370aa7b178827cd3aa0ee54e8d)

- **作者**: Peng Wu
- **时间**: 2026-10-23T17:26:10Z
- **提交信息**: [Fix] disaggregation: Restart a lost prefill's heartbeat miss count (#45922)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [74c08f3](https://github.com/sgl-project/sglang/commit/74c08f3dc5d98dddf052ba03122fc084a31a0269)

- **作者**: metamergebot
- **时间**: 2026-10-23T16:26:52Z
- **提交信息**: [Feat] rust-server: Let a multimodal processor finalize item layout after caller hashes (#45914)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>

### [30dc2f9](https://github.com/sgl-project/sglang/commit/30dc2f94303e339431cbd51489b2d1719678b0c1)

- **作者**: metamergebot
- **时间**: 2026-10-23T16:04:59Z
- **提交信息**: [Feat] benchmark: Add --input-len-list to bench_one_batch_server for per-request input lengths (#45982)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: wpc <wpc@users.noreply.github.com>

### [5a86d6e](https://github.com/sgl-project/sglang/commit/5a86d6ee17e1f2fd34cfa6d703ea38c581ab23fa)

- **作者**: metamergebot
- **时间**: 2026-10-23T16:04:54Z
- **提交信息**: [Fix] rust-server: Deliver scheduler-side aborts to Rust frontend clients (#45899)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [eb8ef80](https://github.com/sgl-project/sglang/commit/eb8ef8084231078c24fa3d8dbfc8a74d0f8f90e4)

- **作者**: metamergebot
- **时间**: 2026-10-23T16:04:49Z
- **提交信息**: [Feat] rust-server: Serve /abort_request from the Rust frontend (#45888)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [efd2ce8](https://github.com/sgl-project/sglang/commit/efd2ce8a9df027d3607766fc5e7efcb3390cf738)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-23T15:09:30Z
- **提交信息**: [Feat] comfyui: video-to-video input and prompt enhancement for server-mode nodes (#43673)

### [c677171](https://github.com/sgl-project/sglang/commit/c677171c1d11ac500d27808d496ed1b77094cef1)

- **作者**: Byron Hsu
- **时间**: 2026-10-23T15:09:04Z
- **提交信息**: [Feat] hicache: Support MLA DCP with HiCache L3(file/mooncake) (#41187)

Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Venkat Raman <venkat.raman@verda.com>

### [02b9836](https://github.com/sgl-project/sglang/commit/02b983603d34c6af09e554ed2b8bf8d85290d9ae)

- **作者**: Mick
- **时间**: 2026-10-23T13:19:53Z
- **提交信息**: [Fix] diffusion: Keep dynamic LoRA deltas on fused linear-GELU sites (#45943)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0e34962](https://github.com/sgl-project/sglang/commit/0e34962884b07669e65f6bdccd12f7473e6d0563)

- **作者**: Mick
- **时间**: 2026-10-23T13:18:57Z
- **提交信息**: [Perf] diffusion: Cut LTX-2 denoising-step host overhead (#45966)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [82ff16d](https://github.com/sgl-project/sglang/commit/82ff16dad08809a8819fa02d975d1a44cf202041)

- **作者**: Mick
- **时间**: 2026-10-23T13:18:06Z
- **提交信息**: [Perf] diffusion: Skip the residency calibration probe in auto mode until a planner consumes it (#45979)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3e5f550](https://github.com/sgl-project/sglang/commit/3e5f5505edfbcaeb4ad38f81e35d7591a6ed9480)

- **作者**: Mick
- **时间**: 2026-10-23T13:16:44Z
- **提交信息**: [Perf] diffusion: Serve image responses from in-memory encoded bytes (#45987)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2fbd094](https://github.com/sgl-project/sglang/commit/2fbd094a8cb641deb099b5b2ac0d362b7eaa6aec)

- **作者**: Mick
- **时间**: 2026-10-23T13:14:37Z
- **提交信息**: [Fix] diffusion: Offset LTX-2.3 BCG video RoPE by the SP shard start (#45995)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b46f27](https://github.com/sgl-project/sglang/commit/9b46f27090f32de75d65deb76013a357b5d08645)

- **作者**: pllimax
- **时间**: 2026-10-23T13:06:21Z
- **提交信息**: [Fix] [NPU] tests: Restore evalscope GSM8K baseline via NPUGSM8KMixin backend (#45732)

### [2a46e32](https://github.com/sgl-project/sglang/commit/2a46e32fbcf584d613ec26da2a0c59726ab1dc13)

- **作者**: shun8686
- **时间**: 2026-10-23T13:01:42Z
- **提交信息**: [CI] [NPU] precise-test: skip recommend-tests-from-coverage when no NPU paths changed (#46055)

### [86933b1](https://github.com/sgl-project/sglang/commit/86933b1f338afb802aa0a73590e0a260fce5d2f0)

- **作者**: Trevor Morris
- **时间**: 2026-10-23T12:57:44Z
- **提交信息**: [Fix] deps: Pin python-dateutil<3 to keep botocore resolvable (#45857)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [0347b2b](https://github.com/sgl-project/sglang/commit/0347b2bb4ef78a890c3359191b71161c867c1754)

- **作者**: shun8686
- **时间**: 2026-10-23T12:41:22Z
- **提交信息**: [CI] [NPU] precise-test: gate precision on PR judgeability, not bucket count (#46042)

### [4b1941e](https://github.com/sgl-project/sglang/commit/4b1941e8891fdef3d99d77a71e537a836561a85b)

- **作者**: Jimmy Shong
- **时间**: 2026-10-23T11:54:03Z
- **提交信息**: [CI] diffusion: Run the FLUX.2 XPU norm-fusion test on the XPU suite only (#46040)

### [f967418](https://github.com/sgl-project/sglang/commit/f967418a35cf125cc9840df21066a66258023364)

- **作者**: chuyeh
- **时间**: 2026-10-23T11:12:05Z
- **提交信息**: [Doc] cookbook: Qwen3.5 MI355X FP8 agentic adds scheduler/tokenizer tuning from the InferenceX recipe (#46032)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [535aeae](https://github.com/sgl-project/sglang/commit/535aeae2a709077e3d17f5efc48350319ac13fc9)

- **作者**: shun8686
- **时间**: 2026-10-23T10:06:58Z
- **提交信息**: [CI] [NPU] precise-test: run only the recommended multimodal_gen cases (#46014)

### [69f8307](https://github.com/sgl-project/sglang/commit/69f830756e5945e7416f424cf9cd4c32cdf98d76)

- **作者**: chuyeh
- **时间**: 2026-10-23T09:47:52Z
- **提交信息**: [Doc] cookbook: Qwen3.5 MI355X FP8 agentic uses HiCache write_through on the v0.5.22 image (#46017)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [611a703](https://github.com/sgl-project/sglang/commit/611a70306197239593959cb47a9fa92a9913dd18)

- **作者**: Sage
- **时间**: 2026-10-23T09:10:23Z
- **提交信息**: [Chore] api: add fields to generate request (#45164)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [494eeec](https://github.com/sgl-project/sglang/commit/494eeecb6c5f8c350f34f108babd6c3f299cde18)

- **作者**: Mick
- **时间**: 2026-10-23T09:01:51Z
- **提交信息**: [Fix] diffusion: Keep the linear-GELU verdict cache out of torch.compile traces (#45944)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f912991](https://github.com/sgl-project/sglang/commit/f9129915a36a2d0bac708110c617ca1861b5a100)

- **作者**: Mick
- **时间**: 2026-10-23T09:00:40Z
- **提交信息**: [Fix] diffusion: Give every SP rank the same Wan TI2V timestep (#45994)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8b9f724](https://github.com/sgl-project/sglang/commit/8b9f72417fa85a04de6193b0a52f4cec63370d77)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-23T08:43:38Z
- **提交信息**: [Feat] Inkling: render and parse chat via tml-renderers (#45340)

### [bb72b47](https://github.com/sgl-project/sglang/commit/bb72b47daf2684fd534ae44e32feaf856ca0caff)

- **作者**: Michael
- **时间**: 2026-10-23T08:38:54Z
- **提交信息**: [Test] [AMD] deepseek-v4.1: Give the encoder-replay test's request window a zero_row (#45728)

### [77bc8ca](https://github.com/sgl-project/sglang/commit/77bc8cab18a1c6f65b4c3835af911858b27aad02)

- **作者**: Shuwen Wang
- **时间**: 2026-10-23T08:32:41Z
- **提交信息**: [Fix] hicache/pd: Promise prefill only the L3 span the decode prefetch takes (#43548)

### [7d1a16d](https://github.com/sgl-project/sglang/commit/7d1a16d3eb2d12d540db7f849b0815bf6f82fb7e)

- **作者**: Michael
- **时间**: 2026-10-23T08:28:12Z
- **提交信息**: [CI] [AMD] diffusion: Skip the LTX-2.5 diffusion decoder case on the 2-GPU lane (#45861)

### [2b8e4cd](https://github.com/sgl-project/sglang/commit/2b8e4cde9564c4737f6ca0639a43ef85ec98b3fc)

- **作者**: Ziru
- **时间**: 2026-10-23T08:22:50Z
- **提交信息**: [Doc] [CPU] Cookbook: Update to the cookbook for models supported by Intel Xeon CPUs (#40092)

Co-authored-by: Niu Ziru <niuziru@a4bf018d3341.jf.intel.com>
Co-authored-by: Niu Ziru <niuziru@gnr799217.jf.intel.com>

### [4b27353](https://github.com/sgl-project/sglang/commit/4b273537dec55427c01487d9583e505975a9c9a0)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-23T08:08:13Z
- **提交信息**: [Fix] diffusion: runtime utils bug fixes (#44887)

### [02d2445](https://github.com/sgl-project/sglang/commit/02d244513871bb426bfd8a8d9de399f660ed24b5)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-23T08:04:01Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches with seven open InferenceX PRs (#46005)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [472208f](https://github.com/sgl-project/sglang/commit/472208fec00d7023db7f2039c64056d746de96a8)

- **作者**: shun8686
- **时间**: 2026-10-23T07:57:31Z
- **提交信息**: [CI] [NPU] precise-test: recommend multimodal_gen cases at test-case granularity (#45955)

### [6d6c9cd](https://github.com/sgl-project/sglang/commit/6d6c9cd4ae4491e5293e9a2b06e8f71dfde6dd18)

- **作者**: Yao Matrix
- **时间**: 2026-10-23T07:50:24Z
- **提交信息**: [Fix] offloader: Preserve cached weights during CPU offload (#44139)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [6f466f6](https://github.com/sgl-project/sglang/commit/6f466f655ad7b2cf9025e4bff1fa82b55bb48d7a)

- **作者**: Yihao Wang
- **时间**: 2026-10-23T07:38:12Z
- **提交信息**: [Perf] [XPU] diffusion/flux2: Fuse bit-exact LayerNorm and gated residual norm (#41942)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [8708d2e](https://github.com/sgl-project/sglang/commit/8708d2ee9995ae95659a745ae3fd141457b02039)

- **作者**: Mick
- **时间**: 2026-10-23T07:32:03Z
- **提交信息**: [Fix] diffusion/ltx: Keep tiled VAE decode off the sharded convs under parallel decode (#45942)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4f47c48](https://github.com/sgl-project/sglang/commit/4f47c48b332fbf8154a594b7ff1af6c00485c806)

- **作者**: Mick
- **时间**: 2026-10-23T07:31:19Z
- **提交信息**: [Fix] diffusion: Keep the N-rank IPC all-to-all's flags and staging out of expandable segments (#45948)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1cd0ebb](https://github.com/sgl-project/sglang/commit/1cd0ebb3d32479e943af220bfb15b8ab99651815)

- **作者**: Mick
- **时间**: 2026-10-23T07:30:09Z
- **提交信息**: [Perf] diffusion: Remove per-step and per-request host syncs in Cosmos3 and Qwen-Image-2.1 (#45967)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4da6f58](https://github.com/sgl-project/sglang/commit/4da6f585f3acd3202ae2d9dd0ce4a037928b2715)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-23T07:22:00Z
- **提交信息**: [Fix] diffusion: OpenAI API hardening (#43585)

### [79ab8f6](https://github.com/sgl-project/sglang/commit/79ab8f6d7c8f3d487558dde690bf386b3b2ce628)

- **作者**: Shunkangz
- **时间**: 2026-10-23T07:20:19Z
- **提交信息**: [Feat] KVShard: Support kv cache sharding for MTP (#40929)

Co-authored-by: Zhangheng <hzh0425@apache.org>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1293
- **最后更新**: 2026-10-23T10:31:32Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 分析总结：vipshop/cache-dit 昨日提交（2笔）

### 1. 主要更新类型
- **功能新增（核心）**：新增两个模型支持——Anima（基于 Cosmos Predict2 骨干）和 PRXPixel，均实现全栈加速能力。
- **配套重构**：将共享的 Cosmos 适配逻辑抽取为独立的 `_cosmos_predict2_adapter` 模块，提升代码复用。
- **文档更新**：补充 CLI 示例、支持矩阵、pending-model RFC 及技能笔记（量化/编译作用域陷阱）。

### 2. 关键变更点与项目方向的关系
- cache-dit 的定位是 PyTorch 原生的 DiT 推理引擎，主打 **缓存、并行、量化、CPU Offload** 四大加速手段。本次两笔提交都将这四类能力一次性扩展到新模型：
  - **Anima**：新增 BlockAdapter 前缀匹配、CP（上下文并行）与 TP（张量并行）planner、fp8 区域量化声明（28 块堆栈，448 层全覆盖），以及 CLI 示例。
  - **PRXPixel**：同样覆盖 cache、CP、TP、TE-P、量化、编译，并为 diffusers 未标注的模型显式声明 `_repeated_blocks`，使区域量化和 `compile_repeated_blocks` 生效。
- 两笔提交都**严格注册模型类名**，不匹配时显式失败（fail loudly），符合引擎"精确适配、可验证"的工程取向。

### 3. 对项目的影响和潜在意义
- **扩大模型覆盖面**：从原本的骨干扩展到 Cosmos 系和 PRX 这类较新架构，使 cache-dit 成为更通用的 DiT 推理加速层，对多模态/视频生成模型的生态价值显著提升。
- **可验证的加速效果**：Anima 在 RTX PRO 5000 上验证了 1024×1024 推理从基线 8.21s 降至缓存 4.41s、fp8+compile 4.20s、nvfp4 4.13s，并附带 PSNR/SSIM 等质量指标，为用户选型提供量化参考。
- **知识沉淀**：明确记录了"未声明 `_repeated_blocks` 时量化与编译会静默退化为整模块级，精度掉约 3dB 且编译反而更慢"这一陷阱，降低了其他贡献者接入新模型时的踩坑成本。

### 4. 值得关注的技术点
- **CP 设计细节**：Anima 的 CP 采用 `transformer_blocks.0` 单点切分，配合逐块重切 encoder_hidden_states、rope 输出切分和 `proj_out` gather；PRX 则在 `txt_in` 后切文本、`pe_embedder` 前切 image id，并按 Ulysses all-to-all 顺序重建联合 key mask——两者均拒绝不兼容的 Ring 模式，体现了对不同架构 loop-invariant 局部变量的精准适配。
- **TP 策略差异**：Anima 对 q/k/v 用 Colwise、输出 Rowwise 分片；PRX 的融合 QKV 因无 `shard_div_attr` 而采用 Replicate 策略，展示了 planner 需按模型结构定制的现实复杂度。
- **量化选型指引**：fp8_per_row 需配合 `--compile` 才有收益，svdq nvfp4 在像素空间模型上需 few_shot smoothing——这些结论对实际部署很有指导意义。
- **测试覆盖全面**：包含 CPU 适配接线、CP 布局、processor fork 一致性、精确类名注册，以及 2-GPU 小规模数值对齐（rel < 2e-2），保证并行正确性。

### 5. 对项目发展的意义
结合 README，cache-dit 的目标是为 DiT 模型提供一站式推理加速引擎。这两笔提交表明项目正处于**快速扩展模型支持矩阵的阶段**，且坚持"每个新模型都全栈打通（cache/CP/TP/量化/offload）+ 实测数据 + 对齐测试"的高质量接入标准。这强化了项目作为通用 DiT 推理加速层的定位，尤其在视频/多模态生成模型日益增多的背景下，持续吸引新架构接入将直接提升其在开源生态中的采用率和影响力。

## 详细提交记录

### [ab5be29](https://github.com/vipshop/cache-dit/commit/ab5be29b4a9b2d5e463026428000aec40bb9c8e9)

- **作者**: DefTruth
- **时间**: 2026-10-23T10:31:27Z
- **提交信息**: Support Anima (Cosmos Predict2 backbone): Anima adapter, CP/TP planners, CLI example (#1136)

- Add the 'Anima' BlockAdapter prefix (AnimaModularPipeline never matched the
  'Cosmos' prefix); has_separate_cfg derives from the modular guider instead
  of a fixed True, and the shared CosmosTransformer3DModel Pattern_2 branch
  is factored into _cosmos_predict2_adapter.
- Add Cosmos CP/TP planners (distributed/transformers/cosmos.py, exact
  class-name registration so Cosmos3OmniTransformer keeps failing loudly):
  CP is a single-point split at transformer_blocks.0 with per-block
  encoder_hidden_states re-split (the forward passes the full text from a
  loop-invariant local), a rope (cos, sin) output-split, and a proj_out
  gather; the CosmosAttnProcessor2_0 fork only swaps the attention dispatch.
  TP shards attn1/attn2 (q/k/v Colwise, out Rowwise, shard_div_attr heads)
  and the GELU FeedForward (ff.net.0.proj / ff.net.2).
- Register the anima CLI example (ANIMA_DIR env, 30 steps, CFG 4.0 held by
  the guider) and mark Anima as a verified modular pipeline.
- Declare _repeated_blocks for CosmosTransformer3DModel so regional
  quantization and compile_repeated_blocks find the 28-block stack (fp8:
  448 layers, 0 skipped).
- Tests: CPU adapter wiring + guider-derived separate-CFG, CP plan layout,
  processor fork parity, exact-name planner registration, and 2-GPU tiny
  CP/TP parity (rel < 2e-2).

Verified on RTX PRO 5000 (1024x1024, 30 steps, seed 42): baseline 8.21s;
cache rdt0.12 4.41s (15/30 cached, PSNR 33.4 / SSIM 0.927, rerun bit-exact);
CP2 6.84s bit-exact after the per-block text split; TP2 7.44s (40.8 dB /
0.983); fp8+compile 4.20s (30.8 dB / 0.815); svdq nvfp4+compile 4.13s
(30.0 dB / 0.651, texture softening only); layerwise offload bit-exact with
async transfer; TE-P (Qwen3) and VAE-P (QwenImage VAE) reused as-is.

### [74b6339](https://github.com/vipshop/cache-dit/commit/74b6339b49232bff2cca23b1fa9b82a3da4fe6b5)

- **作者**: DefTruth
- **时间**: 2026-10-23T08:10:52Z
- **提交信息**: feat: support PRXPixel (cache, CP, TP, TE-P, quant, compile) (#1134)

* skills: update skills

* feat: support PRXPixel (cache, CP, TP, TE-P, quant, compile)

- CP: split text after txt_in and image ids before pe_embedder (both are
  loop-invariant locals in PRX), split the 3D tokens at blocks.0, gather at
  final_layer; rebuild the joint text+image key mask in the Ulysses all-to-all
  order; reject Ring and --ulysses-anything
- TP: Replicate strategy for the fused QKV projections (no shard_div_attr)
- TE-P: register Qwen3VLTextModel
- declare _repeated_blocks for models diffusers never annotated, so regional
  quantization and compile_repeated_blocks() can find PRXBlock
- prx_pixel CLI example, CPU plan/mask tests, 2-rank CP/TP parity test
- README, supported matrix and pending-model RFC

* docs(skill): record the quantization/compile scope pitfall

quantization and compile_repeated_blocks() silently fall back to whole-module
work when a diffusers transformer declares no _repeated_blocks: accuracy drops
~3 dB and a full-module compile can lose to eager (PRX: 22.66s vs 16.42s).
Also note that fp8_per_row only pays off with --compile and svdq nvfp4 needs
few_shot smoothing on pixel-space models.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95253
- **最后更新**: 2026-10-24T00:28:37Z

## 提交统计

- **昨日提交总数**: 61
- **提交者数量**: 39
- **主要提交者**: Nick Hill, Stephan Toivonen, khryu

## AI分析总结

# vLLM 昨日提交总结（共61条）

## 1. 主要更新类型

- **Bug修复**占比最高（约40%），涉及MoE、LoRA、CPU、Mamba、Kernel等多个模块
- **Rust前端**是最突出亮点（约15条提交），集中于与Python实现的行为对齐
- **ROCm/AMD平台支持**持续投入（约15条），包括CI加固、内核修复和Kimi-K3模型适配
- **文档/Recipe更新**，重点是MiniMax-M3在NVIDIA B200/B300/H200/GB200上的推理Profile
- **CI基础设施优化与代码重构**，包括移除死代码、废弃vLLM IR优先级机制

## 2. 关键变更点及与项目方向的关系

**Rust前端全面对齐Python**（Bugen Zhao主导）：涵盖LoRA wire格式、logit_bias校验、bad_words去重、工具调用序列化、流式响应字段等十余项一致性修复。已有大量Python服务器测试接入Rust前端，表明Rust前端正从实验走向生产就绪，契合vLLM"高性能多语言服务"的战略方向。

**MoE/稀疏注意力与量化正确性**：修复topk_ids重映射、MXFP4激活覆盖、Humming量化等问题。其中特别值得注意的是对DeepSeek V4.1稀疏注意力预填充阶段的定向修复——在稀疏索引工作区中正确初始化-1哨兵值，消除垃圾索引被误当作有效索引的风险，避免隐蔽的精度劣化或推理崩溃。

**投机解码（Spec Decode）修复**：包括LoRA与投机解码兼容、drafters的rotary cache边界、CPU上GDN卷积状态布局等，表明投机解码正被纳入更多生产场景。

**新模型支持**：Domyn Edge、DeepSeek-V4.1-Flash的SWA bounded replay特性、Muse Spark RoPE缓存优化、Kimi-K3的ROCm深度适配等。

## 3. 对项目的影响和潜在意义

- **稳定性提升**：大量NaN处理、内存访问越界、KV cache边界及哨兵值初始化类修复，系统性降低了生产环境崩溃和静默计算错误的风险。
- **多硬件生态扩展**：AMD MI355X/MI300、Intel XPU、Rust前端均获得实质性推进，降低对单一硬件的依赖。
- **可观测性增强**：OpenAI兼容API流式响应新增KV参数、Mooncake传输指标导出，便于用户监控调优。
- **DeepSeek V4.1支持进入成熟化阶段**：从"能跑"走向"边用边修"的可靠性打磨。

## 4. 值得关注的技术点

- **cooperative_topk内核**：同日修复NaN导致的非法内存访问并优化单pass尺寸计算策略，体现"先正确后性能"的演进路径。
- **AI辅助开发常态化**：约70%提交有Claude/Codex等AI模型作为共同作者，vLLM已形成人类+Agent协作的开发流程。
- **vLLM IR退役进程**：清理实验性编译中间层和过时文档，聚焦核心推理路径。
- **多级KV cache**：保留被分层缓存引用的专家输出，完善分层存储架构。
- **哨兵值初始化的工程启示**：高性能推理为避免清零操作常跳过工作区初始化，但索引类数据若不播种-1哨兵会引入未定义行为——这是"性能优化"与"内存安全"的经典权衡点。

## 5. 基于项目定位的总结

README定位vLLM为"人人可用的易用、快速、廉价LLM服务"。本批提交对此目标的支撑体现在：

- **"易用"**：Rust前端与Python行为对齐减少迁移成本；稀疏索引修复让用户无需排查隐蔽bug，开箱即得正确结果。
- **"快速"**：ROCm性能优化（W4A16 prefill dequant、RoPE共享缓存）、稀疏注意力与spec decode修复保障长上下文推理吞吐。
- **"廉价"**：多硬件平台扩展提供更多性价比选择；MXFP4/NVFP4量化路径成熟直接降低显存占用和部署成本；正确的稀疏索引避免无效计算与显存浪费。

总体而言，这61条提交反映vLLM已进入**成熟期运营节奏**：核心功能稳健迭代、多平台并行推进、Rust前端加速产品化、前沿MoE/稀疏模型支持持续加固、开发流程高度AI协作化。

## 详细提交记录

### [e4db46c](https://github.com/vllm-project/vllm/commit/e4db46c79bca354fef07197465faea14ca563c09)

- **作者**: jlqibm
- **时间**: 2026-10-23T22:51:58Z
- **提交信息**: [Bugfix][MoE] Remap invalid topk_ids in moe_permute without expert_map (#59717)

Signed-off-by: Jerry Quinn <jlquinn@us.ibm.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2c58be2](https://github.com/vllm-project/vllm/commit/2c58be22b68dcb715455958e406e40f709bf59e8)

- **作者**: xaguilar-amd
- **时间**: 2026-10-23T22:50:22Z
- **提交信息**: [Bugfix][ROCm][Kimi-K3] Validate gfx942's int4 expert requant as int4 (#63131)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>

### [58301f6](https://github.com/vllm-project/vllm/commit/58301f6cb9b15dad4681e34af0f325c60a5d9323)

- **作者**: YAASHU DAVE
- **时间**: 2026-10-23T22:44:32Z
- **提交信息**: [Bugfix][LoRA] Don't reject LoRA for speculative decoding drafters (#63186)

Signed-off-by: Yaashu Dave <daveyaashu2411@gmail.com>
Co-authored-by: linitra24 <renshuang.zhou@daocloud.io>

### [96bbaa3](https://github.com/vllm-project/vllm/commit/96bbaa300fe4ea605f37f42b1a6406ec57bc4fb6)

- **作者**: Stephan Toivonen
- **时间**: 2026-10-23T22:43:52Z
- **提交信息**: [ROCm][RDNA][Perf] W4A16: packed fp16 prefill dequant and tiles for gfx1151 (#60644)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>
Signed-off-by: Stephan Toivonen <Stephan.Toivonen@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [109669c](https://github.com/vllm-project/vllm/commit/109669cfb314d807f7e5fa474dcd03abfca8cbd4)

- **作者**: Roberto L. Castro
- **时间**: 2026-10-23T22:28:25Z
- **提交信息**: [Bugfix][Kernel] Fix cooperative_topk illegal memory access on NaN scores (#63118)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aea0513](https://github.com/vllm-project/vllm/commit/aea0513a322e4159432fc93e50c1805505fa0cd9)

- **作者**: aoshen02
- **时间**: 2026-10-23T22:24:59Z
- **提交信息**: [Bugfix][AuxOutput] Retain routed experts while a KV cache tier holds their blocks (#62591)

Signed-off-by: Ao Shen <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [fbe133f](https://github.com/vllm-project/vllm/commit/fbe133ff30d357cdc90e3b15838b9fd2e7c5ca18)

- **作者**: Nishant Revur
- **时间**: 2026-10-23T22:17:43Z
- **提交信息**: [Bugfix][MRV2] Don't count adaptive verification profiling cache as CUDA graph memory (#61509)

Signed-off-by: Nishant Revur <kumrfni@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c7476c7](https://github.com/vllm-project/vllm/commit/c7476c7a6fc8e3f0cce572d8595bc56785cf9110)

- **作者**: Yicong Wang
- **时间**: 2026-10-23T22:10:14Z
- **提交信息**: [Feature][PCP] Support decoder-side SWA bounded replay with APC for DeepSeek-V4.1-Flash (#62384)

Signed-off-by: wangyicong <wangyicong@bytedance.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [1a15404](https://github.com/vllm-project/vllm/commit/1a1540480dd202a14067cac3eb5c2449f6fd38ef)

- **作者**: Wentao Ye
- **时间**: 2026-10-23T21:56:46Z
- **提交信息**: [Refactor] Remove dead code models (#63400)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [6fd0e70](https://github.com/vllm-project/vllm/commit/6fd0e701fd019a95829a9e08026f73065d05b0b9)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-23T21:37:15Z
- **提交信息**: [CI] Remove redundant Ubuntu 24.04 release variant (#63413)

Signed-off-by: khluu <khluu000@gmail.com>

### [29cf023](https://github.com/vllm-project/vllm/commit/29cf023770a0c4ae9f2423b922330f391524428e)

- **作者**: aditi-amd
- **时间**: 2026-10-23T21:27:17Z
- **提交信息**: [Refactor] [AMD] flydsl: Move UltraQuant/TurboQuant decode to public APIs (#61649)

Signed-off-by: Aditi Rana <aditi.rana@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [18df4cd](https://github.com/vllm-project/vllm/commit/18df4cd9a98b0280bf0fc0aa16c870dc5a921104)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T21:26:19Z
- **提交信息**: [ROCm][Bugfix] Fix Triton paged decode leaving output heads unwritten on gfx942 (#63268)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1815ffd](https://github.com/vllm-project/vllm/commit/1815ffd948fb8db11bf22a42f1bec66e41269302)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-23T21:18:44Z
- **提交信息**: [Doc] MiniMax-M3: update the B300 NVFP4 InferenceX AgentX profile (#63407)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [be03d19](https://github.com/vllm-project/vllm/commit/be03d19750cc0dab80e7c8c8696c4e4badfda520)

- **作者**: Divakar Verma
- **时间**: 2026-10-23T20:57:57Z
- **提交信息**: [CI][ROCm][MoE] Add MXFP4 SWIGLUOAI_UNINTERLEAVE/SITU test coverage on MI355 (#62907)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d143a9d](https://github.com/vllm-project/vllm/commit/d143a9de39157ff68486410608a73422d2705738)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T20:56:53Z
- **提交信息**: [Core] Let VLLM_WORKER_SHUTDOWN_TIMEOUT_SECONDS set the EngineCore cleanup grace after an immediate abort (#63260)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>

### [bc3afc4](https://github.com/vllm-project/vllm/commit/bc3afc4096239c12448d5ccf8b4736a2d758ea1a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T20:55:44Z
- **提交信息**: [CI][ROCm] Fail the AITER nightly overlay on wheels ci_base cannot load (#63242)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f869d64](https://github.com/vllm-project/vllm/commit/f869d6478838107fd417874cbf824eb9d1238b4a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T20:55:22Z
- **提交信息**: [CI][ROCm] Run the online FP8 MoE batch-invariance test on ROCm (#63283)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [a50259b](https://github.com/vllm-project/vllm/commit/a50259bb325366e7dd7c24461e1eb48e9b9ed7cf)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-23T20:29:45Z
- **提交信息**: [vLLM IR] Deprecate ir_op_priority ahead of vLLM IR removal (#63371)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a0544b1](https://github.com/vllm-project/vllm/commit/a0544b13f2ee6424d3aa6d03a00e1c745218dee9)

- **作者**: Shyamal Shah
- **时间**: 2026-10-23T19:46:49Z
- **提交信息**: [Docs][Mistral] Note that required and named tool choice may not produce a call (#63178)

Signed-off-by: Shyamal Shah <shyamals@nvidia.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [b1c66e5](https://github.com/vllm-project/vllm/commit/b1c66e55450d4869a7c79bd23df2092306f04adf)

- **作者**: Oxana Korzh
- **时间**: 2026-10-23T19:39:46Z
- **提交信息**: [ROCm][Model] Muse Spark: share one RoPE cache sized by max_model_len (#62757)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d561af5](https://github.com/vllm-project/vllm/commit/d561af5dfcd136fc1bea95a0343d3a09b6fa0988)

- **作者**: khryu
- **时间**: 2026-10-23T19:30:01Z
- **提交信息**: [Bugfix][Mamba] Avoid re-marking committed prompt-tail boundaries as cached this step (#62841)

Signed-off-by: Kyeonghyeon Ryu <khyun1109@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [7105440](https://github.com/vllm-project/vllm/commit/7105440c4009e1011e9c0dad87c879ad75a5afca)

- **作者**: Ankur Singh
- **时间**: 2026-10-23T19:20:37Z
- **提交信息**: [Doc] MiniMax-M3: use the autotune flag the pinned GB200 nightly accepts, fix golden-AL links (#63394)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>

### [c7c1118](https://github.com/vllm-project/vllm/commit/c7c11188a0a86d26292dcd1c105c23b2c1cea6fc)

- **作者**: Ankur Singh
- **时间**: 2026-10-23T19:20:17Z
- **提交信息**: [Doc] MiniMax-M3: document the B300 NVFP4 InferenceX AgentX aggregated profile (#63395)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>

### [8b21328](https://github.com/vllm-project/vllm/commit/8b21328cb8449649fb57003311a626946416ce46)

- **作者**: Ankur Singh
- **时间**: 2026-10-23T19:20:13Z
- **提交信息**: [Doc] MiniMax-M3: document the H200 MXFP8 InferenceX AgentX aggregated profile (#63391)

Signed-off-by: Ankur Singh <ankusingh@nvidia.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [224b2f5](https://github.com/vllm-project/vllm/commit/224b2f54f19d44bfb96edfe16c6343c7495853d3)

- **作者**: djramic
- **时间**: 2026-10-23T18:45:27Z
- **提交信息**: [ROCm][CI] Move NFS-affected MI300 test groups to MI355 (#62934)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [e2b6723](https://github.com/vllm-project/vllm/commit/e2b672312328d3f95980f5b82869f7937194fd62)

- **作者**: snadampal
- **时间**: 2026-10-23T18:34:48Z
- **提交信息**: [entrypoints/openai] add kv params to streaming api response (#40186)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7651825](https://github.com/vllm-project/vllm/commit/7651825993d001759107c66cdf6983535900c874)

- **作者**: jcotant-inferact
- **时间**: 2026-10-23T17:41:03Z
- **提交信息**: [CI] Automatically label Reflection Beam model changes (#62540)

### [08aa305](https://github.com/vllm-project/vllm/commit/08aa305fb5c56d66566f98f55d51a39b43af936f)

- **作者**: albertoveneri
- **时间**: 2026-10-23T17:31:57Z
- **提交信息**: [Model] Add Domyn Edge support (#62544)

Signed-off-by: albertoveneri <214657570+albertoveneri@users.noreply.github.com>
Signed-off-by: Alberto <214657570+albertoveneri@users.noreply.github.com>

### [4430253](https://github.com/vllm-project/vllm/commit/44302539f83046401a30d454f44f82599de7dfc1)

- **作者**: Ylean
- **时间**: 2026-10-23T17:29:00Z
- **提交信息**: [Bugfix][Tool Parser] Preserve large integer tool arguments (#55743)

Signed-off-by: Ylean <61880605+Woolgathererer@users.noreply.github.com>
Signed-off-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [37cf712](https://github.com/vllm-project/vllm/commit/37cf712552592d7d0f684e393aba6196a483fa3e)

- **作者**: Nick Hill
- **时间**: 2026-10-23T17:06:48Z
- **提交信息**: [Spec Decode] Keep drafters within their rotary cache on the V2 model runner (#63251)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [74ba638](https://github.com/vllm-project/vllm/commit/74ba6384c2f0f1f3c6fa04b4c2d382317be15133)

- **作者**: Chun Fang
- **时间**: 2026-10-23T17:04:52Z
- **提交信息**: [Doc][ROCm] Document DeepSeek-V4.1-Flash MI355X AgentX TP2 profiles (#63344)

Signed-off-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: Codex <noreply@openai.com>

### [89faadf](https://github.com/vllm-project/vllm/commit/89faadf7a6d4866903d0649e8ccae6aeb5bb35aa)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-23T16:52:17Z
- **提交信息**: [MRV2] Remove stale experimental README (#63370)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f3871c3](https://github.com/vllm-project/vllm/commit/f3871c3cbf8a608f7ee833ec4c2c5277f77bee41)

- **作者**: Jared Wen
- **时间**: 2026-10-23T16:00:17Z
- **提交信息**: [Bugfix][CPU] Match GPU conv-state layout in GDN spec decode (#63339)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [404c2b5](https://github.com/vllm-project/vllm/commit/404c2b510e1d73df151d78e5576e1ee7ca0bcaa3)

- **作者**: haosdent
- **时间**: 2026-10-23T15:47:29Z
- **提交信息**: [Perf][Kernel] Size cooperative_topk's single pass by row length, not stride (#62171)

Signed-off-by: haosdent <haosdent@gmail.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [c0a4172](https://github.com/vllm-project/vllm/commit/c0a41721c72db80768cf5220047c3e7192d4352e)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T15:34:38Z
- **提交信息**: [CI][ROCm] Raise the MI355 MiniMax M3 MonoKernel timeout to 45 minutes (#63269)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ecd1e12](https://github.com/vllm-project/vllm/commit/ecd1e12553e66b9a318e7e5259cbe3b5b07f2a77)

- **作者**: hshrivastava-droid
- **时间**: 2026-10-23T15:33:03Z
- **提交信息**: [Recipe] MiniMax-M3: add B200 NVFP4 AgentX aggregated profile (#63163)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [b2e178e](https://github.com/vllm-project/vllm/commit/b2e178eaa94bcdd5f0f5e88dec7eb65df1587cc0)

- **作者**: Nan Qin
- **时间**: 2026-10-23T15:21:32Z
- **提交信息**: [Bugfix] Skip prompt_embeds passthrough items in set_active_mm_loras (#63190)

Signed-off-by: Nan2018 <nan@protopia.ai>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Andrew Sansom <andrew@protopia.ai>

### [97b6a67](https://github.com/vllm-project/vllm/commit/97b6a67d94f7078221dcc9839141a0e2b5ff9a20)

- **作者**: Misha Goin
- **时间**: 2026-10-23T15:09:40Z
- **提交信息**: [Quantization] Honor MoE activation override for Humming MXFP4 (#62751)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [be08fa5](https://github.com/vllm-project/vllm/commit/be08fa5355a049b838803540211fed5647490b39)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-23T14:44:36Z
- **提交信息**: [ROCm] Bump UCX to v1.23.0-rc1 so NIXL uses rocm_ipc (#62827)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [aaa67b7](https://github.com/vllm-project/vllm/commit/aaa67b754ebe26247d0b97c8f412397eac066184)

- **作者**: Isotr0py
- **时间**: 2026-10-23T14:30:59Z
- **提交信息**: [Rust Frontend] Refactor rust frontend for latest `llm-multimodal` v1.14 crate (#59854)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Isotr0py <mozf@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c569393](https://github.com/vllm-project/vllm/commit/c569393ed21172c6d265b4f03951cd6622779f51)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T14:14:07Z
- **提交信息**: [CI][Rust Frontend] Run more Python server tests against the Rust frontend (#63320)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4bceda5](https://github.com/vllm-project/vllm/commit/4bceda5dbf265e5d20f171c9c339ffe6997b2fd0)

- **作者**: Fanli Lin
- **时间**: 2026-10-23T13:41:49Z
- **提交信息**: [XPU][CI] Run prefix-caching tests for GDN, Mamba and pooling models on XPU (#62683)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1839702](https://github.com/vllm-project/vllm/commit/1839702eecea52f1646b98fd399f2b1fb830b275)

- **作者**: Ziyang Ma
- **时间**: 2026-10-23T13:08:38Z
- **提交信息**: [XPU][UT] Use W8A8 FP8 linear kernel instead of W8A16 on XPU in modernbert_fp8 unit test (#63281)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7b1d074](https://github.com/vllm-project/vllm/commit/7b1d07440dde8426a8b3d85e5f5815c06913eb82)

- **作者**: aoshen02
- **时间**: 2026-10-23T11:55:06Z
- **提交信息**: [Bugfix][Rust Frontend] LoraRequest: drop tensorizer_config_dict to match the Python wire layout (#63295)

Signed-off-by: Ao Shen <aoshen@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ccd4e40](https://github.com/vllm-project/vllm/commit/ccd4e4030f4b86f959a3cb3435437c0f592c88b1)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:55:45Z
- **提交信息**: [Rust Frontend] Support --return-tokens-as-token-ids (#63318)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [933f796](https://github.com/vllm-project/vllm/commit/933f7962aeb81aa581eadb24dedd746fab20b2dd)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:55:26Z
- **提交信息**: [Rust Frontend] Export Mooncake connector transfer metrics like Python (#63317)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4a5ee8f](https://github.com/vllm-project/vllm/commit/4a5ee8fc77519a5fc1c68700809ac972277d8f6a)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:55:07Z
- **提交信息**: [Rust Frontend] Keep load_inplace off cached LoRA requests like Python (#63316)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [34b2954](https://github.com/vllm-project/vllm/commit/34b29544826f9192c157562d0393fc3810bd1419)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:54:31Z
- **提交信息**: [Rust Frontend] Validate, deduplicate and cap bad words like Python (#63315)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1b99dc5](https://github.com/vllm-project/vllm/commit/1b99dc5e8fce546a80dd88673f606df2fcd2ca85)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:54:12Z
- **提交信息**: [Rust Frontend] Render empty tool call arguments as an empty object like Python (#63314)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5c465dd](https://github.com/vllm-project/vllm/commit/5c465dda9da3dc88e557874bbb25607ca450b918)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:53:52Z
- **提交信息**: [Rust Frontend] Report every invalid logit_bias key like Python (#63313)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [faccd2f](https://github.com/vllm-project/vllm/commit/faccd2f9dd8f2847b7f20012fffa562be339e803)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:53:32Z
- **提交信息**: [Rust Frontend] End prefilled Kimi K3 reasoning at the response opener like Python (#63062)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [574084b](https://github.com/vllm-project/vllm/commit/574084bfe01a0eb3f53513b5709ae6ed2887f0f4)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:53:06Z
- **提交信息**: [Rust Frontend] Serialize unset chat response fields as null like Python (#63061)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [654bd12](https://github.com/vllm-project/vllm/commit/654bd123b37836bd8b79020d12114f0aff1a679a)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:52:46Z
- **提交信息**: [Rust Frontend] Reject an empty chat tools array like Python (#63060)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [afd07e4](https://github.com/vllm-project/vllm/commit/afd07e4ddb107c9092e60b68f4fbcf0427d75d9a)

- **作者**: Bugen Zhao
- **时间**: 2026-10-23T10:52:27Z
- **提交信息**: [Rust Frontend] Accept Gemma 4 tool calls without the call prefix like Python (#63059)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [098eb89](https://github.com/vllm-project/vllm/commit/098eb89ea45c63af78900c41222bf91b15caff5f)

- **作者**: YukioZzz
- **时间**: 2026-10-23T10:35:14Z
- **提交信息**: [ROCm][Kimi-K3] Support MoRIIO consumers with specialized decode (#63031)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [dc05b14](https://github.com/vllm-project/vllm/commit/dc05b1455636a5b8ec8565cb214b6a96a05bd22c)

- **作者**: YukioZzz
- **时间**: 2026-10-23T10:34:52Z
- **提交信息**: [ROCm][Kimi-K3] Support BF16 KDA recurrent state (#58743)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c3117c7](https://github.com/vllm-project/vllm/commit/c3117c7441dd75095e8fac8f068ad38a76b9a598)

- **作者**: Akash kaothalkar
- **时间**: 2026-10-23T09:57:24Z
- **提交信息**: [CPU][Bugfix] Skip KV cache memory reservation for pooling models (#59405)

Signed-off-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: Antigravity <antigravity@google.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e0e5e6e](https://github.com/vllm-project/vllm/commit/e0e5e6ee0a437654bceabecb9d6f014f1b594093)

- **作者**: xaguilar-amd
- **时间**: 2026-10-23T09:42:35Z
- **提交信息**: [Bugfix][CPU][CI] Accept assigned nodes in the no-Triton worker test (#63299)

Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f4edf9f](https://github.com/vllm-project/vllm/commit/f4edf9f0f078ae67392510aafd1871288948a3c3)

- **作者**: Paweł Mańczak
- **时间**: 2026-10-23T08:23:12Z
- **提交信息**: [XPU] Enable kernel/sampler unit tests on Intel XPU (#62419)

Signed-off-by: pmanczak <pawel.manczak@intel.com>

### [8fae0ff](https://github.com/vllm-project/vllm/commit/8fae0ff58bae8bde68b52bf3e547432250763e5c)

- **作者**: Vigilans
- **时间**: 2026-10-23T07:30:02Z
- **提交信息**: [Frontend] Accept images on /v1/systemone for multimodal next-token models (#62181)

Signed-off-by: Vigilans <vigilans@foxmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [9bd5c2a](https://github.com/vllm-project/vllm/commit/9bd5c2a0582d747c2550425286a585111e74b65b)

- **作者**: Qing
- **时间**: 2026-10-23T07:11:30Z
- **提交信息**: [Bugfix][DSv4.1] Seed the -1 sentinel in the prefill sparse index workspace (#60613)

Signed-off-by: Qing <xqoasis@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-24
**监控日期**: 2026-10-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7327
- **最后更新**: 2026-10-23T23:07:51Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 22
- **主要提交者**: MrDongsls, amy-why-3459, Weiming Liao

## AI分析总结

## vllm-omni 昨日提交分析

### 1. 主要更新类型
- **Bug修复**：占比最高（约60%），涵盖多平台、多模型的运行时问题
- **硬件平台支持**：XPU（Intel）、NPU（华为）、ROCm（AMD）、CUDA 各平台均有涉及
- **新功能**：稀疏注意力后端、Pipeline并行、语义VAD接入、实时API测试
- **CI/测试**：精度基准测试扩展、GPU资源隔离、安全加固

### 2. 关键变更点与项目方向的关系
- **多模态全栈优化**：针对 Qwen3-Omni、MiniCPM-o、Qwen2.5-Omni、MAGI-2、Cosmos3、Wan 等多模态模型修复前缀缓存、音频输出、Pipeline并行等问题，直接服务于"易用、快速、低成本的全模态模型服务"的核心定位。
- **多硬件生态扩展**：新增 XPU 上的 SPARGE INT8 稀疏注意力后端（Intel），NPU 上的分块因果注意力支持和性能优化（去除 host sync stalls），ROCm 上新增 MiniCPM-o 4.5 精度测试——体现项目跨硬件适配的战略方向。
- **实时语音/双工会话能力增强**：语义VAD接入 legacy Realtime 接口、WebSocket 一致性测试、双工会话冷启动超时、静音续传修复、共享内存锁等，提升实时多模态交互的稳定性和标准兼容性。
- **安全性修复**：限制不可信图像解码格式（#9114），提升服务端安全边界。

### 3. 对项目的影响和潜在意义
- 短期内提升各硬件平台和主流全模态模型的稳定性与正确性，减少生产环境故障。
- 稀疏注意力（SPARGE INT8）和 NPU 性能优化为推理吞吐和延迟改善提供基础，契合"fast and cheap"目标。
- 实时 API 一致性测试增强了对外接口的标准化程度，有利于生态集成。

### 4. 值得关注的技术点
- **前缀缓存平台条件化**（Qwen3-Omni 仅在 CUDA 启用）与默认启用策略的配合，体现缓存功能逐步推广的谨慎节奏。
- **Wan SDPA 重对齐与 math kernel 对比**：对视频扩散模型注意力数值正确性的精细验证。
- **SPARGE INT8 稀疏注意力**：面向低精度稀疏推理的新后端，值得关注其后续精度与性能数据。
- **AI辅助开发痕迹明显**：多个提交 Co-authored-by 包含 Claude、Grok、Cursor、Codex、Copilot 等，反映 AI 编程在该仓库的深度应用。

### 5. 对项目发展的影响
结合 README 定位，本批提交集中体现了 vllm-omni 从"多模态模型支持"向"多硬件稳定生产化"演进的趋势：一方面持续打磨实时双工会话和语音输出的细节体验（对应"easy"），另一方面通过稀疏注意力、NPU性能修复和跨平台精度测试夯实性能基础（对应"fast and cheap"）。同时，安全加固和标准一致性测试为项目走向更广泛的生产部署提供了必要保障，多硬件厂商（Intel、AMD、华为）的持续贡献也表明该开源生态正快速壮大。

## 详细提交记录

### [6ce5714](https://github.com/vllm-project/vllm-omni/commit/6ce57141bb132880f44e91bea44fe728408571ff)

- **作者**: hac17
- **时间**: 2026-10-23T22:24:04Z
- **提交信息**: [Bugfix] Expect Qwen3-Omni Thinker prefix cache only on CUDA (#9312)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [dc68e90](https://github.com/vllm-project/vllm-omni/commit/dc68e90b913752ab52e6073c4038cd430ddf51d9)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-23T20:39:05Z
- **提交信息**: [Bugfix] Place the MAGI-2 preview pipeline on the current accelerator (#8655)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [702989c](https://github.com/vllm-project/vllm-omni/commit/702989c7035f1e4c95227890c154f5c238850580)

- **作者**: haic0
- **时间**: 2026-10-23T20:34:12Z
- **提交信息**: [CI/Build][ROCm] Add MiniCPM-o 4.5 accuracy to MI300 nightly (#9267)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [bcd8eb6](https://github.com/vllm-project/vllm-omni/commit/bcd8eb62eef2fd529fdbe203de9fa3aaec9de192)

- **作者**: Yi Liu
- **时间**: 2026-10-23T19:07:51Z
- **提交信息**: [Feature][XPU] Add SPARGE INT8 sparse attention backend (#9254)

Signed-off-by: yiliu30 <yi4.liu@intel.com>

### [e12f297](https://github.com/vllm-project/vllm-omni/commit/e12f297536d0a5ae6b6c503c26236f0b2fb66719)

- **作者**: haic0
- **时间**: 2026-10-23T18:10:59Z
- **提交信息**: [Bugfix] Read Cosmos3 Edge PP ownership from the live modules (#9304)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [c704a28](https://github.com/vllm-project/vllm-omni/commit/c704a283f9813e791351a25be7de619a6f6f0fc6)

- **作者**: Akshat Anand
- **时间**: 2026-10-23T17:47:36Z
- **提交信息**: [Bugfix][CI/Build] Place stage-CLI test replicas on separate GPUs (#9041)

Signed-off-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>

### [7861026](https://github.com/vllm-project/vllm-omni/commit/78610269b446340edc6a9b061cbee4b6cd47d261)

- **作者**: haic0
- **时间**: 2026-10-23T17:07:11Z
- **提交信息**: [Bugfix][ROCm] Compare Wan SDPA realignment with the math kernel (#9303)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [8e2a7c1](https://github.com/vllm-project/vllm-omni/commit/8e2a7c15919187ca64f443b49d38164f27675331)

- **作者**: Iryna Boiko
- **时间**: 2026-10-23T16:22:22Z
- **提交信息**: [Bugfix][XPU] Fix HunyuanImage3 FLASH_ATTN regression from #9248 (#9302)

Signed-off-by: Iryna Boiko <iboiko@habana.ai>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [0131ae1](https://github.com/vllm-project/vllm-omni/commit/0131ae1e7330ff63aa373f8638cf56e249c54992)

- **作者**: Khairul Kabir
- **时间**: 2026-10-23T14:31:27Z
- **提交信息**: Add /v1/realtime WebSocket conformance tests (RHAISTRAT-2749) (#8258)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>

### [cbe4cc4](https://github.com/vllm-project/vllm-omni/commit/cbe4cc4b7c1126a903553f8e79e44ddfab782cf3)

- **作者**: Khairul Kabir
- **时间**: 2026-10-23T13:27:24Z
- **提交信息**: fix: guard omni-specific CLI args behind use_omni check (#8698)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>

### [58e3432](https://github.com/vllm-project/vllm-omni/commit/58e3432dd01645cf28e8dac9cb9403788743c139)

- **作者**: Zheng Wengang
- **时间**: 2026-10-23T11:55:24Z
- **提交信息**: [3/N][Config] Enable Thinker prefix caching by default for Qwen3-Omni and MiniCPM-o (#9203)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [45d7c00](https://github.com/vllm-project/vllm-omni/commit/45d7c0051ec6ac4987102195a68fd4b6468c206e)

- **作者**: MrDongsls
- **时间**: 2026-10-23T11:43:44Z
- **提交信息**: [Feat] Add Cosmos3-Nano Pipeline Parallel support (#4637)

Signed-off-by: Mr.Dong <1042542469@qq.com>
Signed-off-by: Zhipeng Wang <zhipeng.wang@inferact.ai>
Co-authored-by: Mr.Dong <1042542469@qq.com>
Co-authored-by: Zhipeng Wang <zhipeng.wang@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [859103e](https://github.com/vllm-project/vllm-omni/commit/859103ebfda6e44f3e96ed83f0baf29068270c70)

- **作者**: Armaan Amatya
- **时间**: 2026-10-23T11:43:38Z
- **提交信息**: [Bugfix] Re-aim a dropped silence continuation at the answer that opened (#7880)

Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>

### [e1b99a8](https://github.com/vllm-project/vllm-omni/commit/e1b99a8b609549dc93dca7429a71a769daed316e)

- **作者**: kunkun
- **时间**: 2026-10-23T11:43:32Z
- **提交信息**: [Bugfix][Duplex] Give the first session open a cold-start timeout budget (#9107)

Signed-off-by: kunkunblueberry <1833921874@qq.com>

### [81acd75](https://github.com/vllm-project/vllm-omni/commit/81acd7561f10ed25bd7f30ae7d0f0ef1f70a9d70)

- **作者**: Ranran
- **时间**: 2026-10-23T11:43:26Z
- **提交信息**: [Bugfix] Lock shared memory before opening segments (#9285)

Signed-off-by: Ranran Haoran Zhang <ranranhaoranzhang@gmail.com>

### [71e1846](https://github.com/vllm-project/vllm-omni/commit/71e1846cff66e57df6f6fe9a3081dc37e511494a)

- **作者**: Cao Xuanning
- **时间**: 2026-10-23T11:43:19Z
- **提交信息**: [Bugfix] Honor the per-request speaker for Qwen2.5-Omni audio output (#9266)

Signed-off-by: Cao Xuanning <2107254305@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c3109e1](https://github.com/vllm-project/vllm-omni/commit/c3109e19af07a96a5c607a6b32fce69b2eb65554)

- **作者**: Nick Cao
- **时间**: 2026-10-23T11:43:12Z
- **提交信息**: [Frontend] Wire semantic VAD into legacy Realtime (#9170)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [3ce3f97](https://github.com/vllm-project/vllm-omni/commit/3ce3f97342480ee9c55f3a66c11f60f958c4a88f)

- **作者**: amy-why-3459
- **时间**: 2026-10-23T11:43:06Z
- **提交信息**: [Bugfix] Align Wan VAE attention queries for 1x1 tiles (#9171)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <amy-why-3459@users.noreply.github.com>

### [ea719bc](https://github.com/vllm-project/vllm-omni/commit/ea719bc6b99b02e79c8ee40ce6c575761da297a7)

- **作者**: Nick Cao
- **时间**: 2026-10-23T11:43:00Z
- **提交信息**: [BugFix] security: restrict untrusted image decoding formats (#9114)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [0be1493](https://github.com/vllm-project/vllm-omni/commit/0be14932ba0f823709c16d7f23ded32c32bdb138)

- **作者**: Wang Boyuan
- **时间**: 2026-10-23T11:41:41Z
- **提交信息**: [Bugfix][NPU] Support piecewise block-causal attention for full_attn_spans (#9244)

Signed-off-by: YawningPants <54137998+YawningPants@users.noreply.github.com>
Co-authored-by: changetheway <guotaoyuan1@h-partners.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [bd73c65](https://github.com/vllm-project/vllm-omni/commit/bd73c651d50cb6dd7587671ca150481879cc30d3)

- **作者**: wangyu
- **时间**: 2026-10-23T11:39:34Z
- **提交信息**: [Bugfix] Register native KV specs in fast allocation tests (#9289)

Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [c829af4](https://github.com/vllm-project/vllm-omni/commit/c829af44682909490df334be3e8be77ccdb5faaa)

- **作者**: psv666
- **时间**: 2026-10-23T10:29:52Z
- **提交信息**: [CI/Build] Enable qwen3-omni accuracy benches on NPU A3 (#9091)

Signed-off-by: psv666 <150513104+psv666@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [b90ded4](https://github.com/vllm-project/vllm-omni/commit/b90ded47f0177eb72e311d9c4912327df0c21b00)

- **作者**: y-null
- **时间**: 2026-10-23T10:28:12Z
- **提交信息**: [perf][npu] Remove host sync stalls in the prompt feature setup (#9186)

Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4f193ab](https://github.com/vllm-project/vllm-omni/commit/4f193ab2e871aa24c426352873abf007fbe7ee56)

- **作者**: Weiming Liao
- **时间**: 2026-10-23T09:00:58Z
- **提交信息**: [Bugfix] Recognize mixed-attention warmup requests in MRv2 (#9264)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [a147aaf](https://github.com/vllm-project/vllm-omni/commit/a147aaf27e10ea4e68b2cc257e3820ac5e7358d7)

- **作者**: Sylvan Liu
- **时间**: 2026-10-23T08:46:48Z
- **提交信息**: [Bugfix] MiniMax-H3: keep native layout for local snapshots with modular_model_index.json (#8801)

Signed-off-by: Sylvan Liu <Sylvan.Liu@amd.com>

### [6537719](https://github.com/vllm-project/vllm-omni/commit/65377195a34c925865662e2882fccde262966faa)

- **作者**: amy-why-3459
- **时间**: 2026-10-23T08:42:15Z
- **提交信息**: [Bugfix][Core] Ignore completed duplex append tasks in response gating (#9282)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [1015af9](https://github.com/vllm-project/vllm-omni/commit/1015af987f31c5c1d84f6892ad7308afa51974b8)

- **作者**: wangqiankun13
- **时间**: 2026-10-23T07:59:12Z
- **提交信息**: [Bugfix][Diffusion][Qwen-Image-2.1] Fall back to SDPA for dense 4D masks (#9248)

Signed-off-by: wangqiankun13 <wangqiankun13@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [17bd19f](https://github.com/vllm-project/vllm-omni/commit/17bd19f3d775e552191fd2ab5ec21aab89b989c1)

- **作者**: amy-why-3459
- **时间**: 2026-10-23T07:30:23Z
- **提交信息**: [Bugfix] Make Qwen3-Omni Seed-TTS prompts read questions verbatim (#9284)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
