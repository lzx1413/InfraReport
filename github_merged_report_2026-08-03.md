# GitHub Stars 合并报告 - 2026-08-03

**合并日期**: 2026-08-04
**监控日期**: 2026-08-03
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


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2123
- **最后更新**: 2026-08-03T14:04:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2559
- **最后更新**: 2026-08-03T12:32:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Chernobyllight, Bilang ZHANG, STwangyingrui

## AI分析总结

### 主要更新类型
- **功能新增**：新增 Bagel、SenseNova-Vision 模型支持，并引入 NVFP4 FFN split-N 硬件适配方案。
- **重构优化**：对 wan、qwen-image 和 InfiniteTalk 进行公共代码复用，消除冗余。
- **临时性 workaround**：针对特定硬件（NVIDIA Jetson AGX Thor）的 NVFP4 GEMM 问题提供专项解决路径。

### 关键变更点及其与项目整体方向的关系
- **common reuse**（`6818c45`）：抽取多个模型共用的逻辑，提升代码可维护性，符合框架“轻量、通用”的长期方向。
- **NVFP4 split-N workaround**（`a30738b`）：在不改变现有 NVFP4 实现的前提下，为 Wan 的 `ffn_0` 和 `ffn_2` 提供可选优化路径，解决 Jetson 平台上的 GEMM 适配问题，体现了对边缘硬件场景的重视。
- **SenseNova-Vision & Bagel 支持**（`0f73304`）：引入统一视觉任务层级和常驻多任务服务器，使框架能对绝大多数公共视觉子任务进行离线处理，扩展了模型生态和 API 兼容性。

### 对项目的影响和潜在意义
- **扩展模型覆盖面**：新增 Bagel 和 SenseNova-Vision 使框架支持更多视频/视觉生成模型，吸引更广泛的用户群体。
- **增强硬件兼容性**：通过 split-N workaround 适应 Jetson 等受限设备，为边缘部署扫清障碍。
- **提升代码质量**：公共代码复用减少了重复实现，降低后续维护成本，为更多模型接入奠定基础。
- **建立统一服务范式**：视觉任务层次结构和服务端设计，为未来其他模型提供参考模板。

### 值得关注的技术点
- **NVFP4 分片推理**：将输出维度分为两个 N/2 分片，执行两次 `cutlass_scaled_nvfp4_mm` 再拼接，是面对硬件限制时的实用技巧。
- **可选开关设计**：通过 `nvfp4_ffn_split_n_workaround` 布尔选项控制，确保默认行为不变，风险隔离。
- **服务端 API 架构**：单一常驻多任务服务器 + 官方后处理 + 14 个视觉子任务的完整覆盖，体现了

## 详细提交记录

### [6818c45](https://github.com/ModelTC/LightX2V/commit/6818c45299a2cfddcd67425bb85314e93c312e88)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-03T12:31:48Z
- **提交信息**: common reuse: wan, qwen-image and InfiniteTalk (#1324)

### [a30738b](https://github.com/ModelTC/LightX2V/commit/a30738b1f6442f239886eda920528a5508d0bb59)

- **作者**: STwangyingrui
- **时间**: 2026-08-03T11:51:43Z
- **提交信息**: feat(nvfp4): add Wan FFN split-N workaround (#1306)

This MR adds an opt-in split-N workaround for Wan FFN NVFP4 GEMMs on
NVIDIA Jetson AGX Thor. A dedicated weight implementation quantizes
activations once, splits the output dimension into two aligned N/2
shards, runs two serial `cutlass_scaled_nvfp4_mm `calls, and
concatenates the outputs. The existing NVFP4 implementation remains
unchanged. The workaround is selected only for Wan `ffn_0 `and `ffn_2
`through the `nvfp4_ffn_split_n_workaround `boolean option, so other
linear layers and models keep their current behavior. This path is
temporary and can be removed once the backend supports architecture- and
shape-aware dispatch or internal split-N.

### [0f73304](https://github.com/ModelTC/LightX2V/commit/0f73304e6d2a67f4c462d902cbd6230c9c8b53dc)

- **作者**: Chernobyllight
- **时间**: 2026-08-03T10:19:42Z
- **提交信息**: Lightx2v supports Bagel and SenseNova-Vision with server API (#1323)

This version is a temporary validation build for the unified
SenseNova-Vision integration. It introduces the omni_vision_task/subtask
hierarchy, a single resident multi-task server, official-parity
post-processing, reorganized remote client tooling, and complete offline
coverage for all 14 public vision subtasks.

---------

Co-authored-by: liuhongda <liuhongda@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2183
- **最后更新**: 2026-08-03T14:17:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6091
- **最后更新**: 2026-08-03T21:54:55Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Adrian, yichengj, Jimmy Zhou

## AI分析总结

根据仓库README和提交记录，以下是对昨日7个提交的整体分析：

## 1. 主要更新类型

- **性能优化**（3项）：SM12x架构下的W4A16和NVFP4 fused-MoE内核全面同步上游b12x；针对B200的新decode/prefill后端
- **新功能**（2项）：CAKE生成的B200（SM100a）专用KDA decode和prefill后端
- **Bug修复**（2项）：SM100 GDN状态更新的block-end decay回归修复；一个测试期望值修正
- **测试/CI改进**（1项）：单元测试分片支持以加速CI流水线

## 2. 关键变更点与项目方向的关系

- **MoE内核大量同步b12x上游**：带来cooperative persistent launches、tensor-core decode路径、按2的幂容量做shape-stable route packing（避免decode批次变化触发重编译）、以及MXFP4 K/32新格式支持。这体现了FlashInfer紧跟开源社区最优实现、保持与`local-inference-lab/sparkinfer`同步演进的策略
- **添加CAKE后端**：并非简单"加一个kernel"，而是为B200提供一条完整的、契约精确匹配的替代代码路径——不匹配则抛错而非回退，保证确定性。同时保留原CuTe-DSL实现作为默认，体现渐进式迁移思路
- **GN D修复**：修复了#4133引入的线程坐标依赖bug，恢复块端衰减语义，补充了覆盖整块/部分/循环块的回归测试

## 3. 对项目的影响和潜在意义

- **架构覆盖更完整**：SM120/SM121（RTX 5080/5090等）和SM100a（B200）都有针对性的优化路径，且decode/prefill均覆盖
- **性能提升显著**：MoE decode batch 1-2最高提速2.3x，prefill普遍1.1x；B200新后端针对T=1..6的speculative decode做了专门优化
- **测试基础设施加强**：测试分片支持解决CI耗时问题（关联issue #3936），为后续大规模并行测试铺路

## 4. 值得关注的技术点

- **cooperative launch的引入**：MoE内核需要全grid同步，这对并发场景有死锁风险，需与CUDA graph正确地配合使用
- **shape-stable packing**：以2的幂容量替代精确token数，用空间换编译时间，是处理decode动态批次的好思路
- **MXFP4 K/32格式**：新增的`fp4_e8m0_k32`权重格式，处理TP分片非128对齐的scale-tail
- **GDN bug的根因**：从线程局部坐标推导块端标量，而该坐标因线程id变化——提醒推导共享内存索引时必须验证线程无关性
- **CAKE的契约设计**：不做fallback而是抛错，保证性能路径可预期

## 5. 对项目发展的整体影响

FlashInfer正从"通用高性能kernel库"向"多架构、多后端、精确优化的

## 详细提交记录

### [28ca04e](https://github.com/flashinfer-ai/flashinfer/commit/28ca04ebf35664c32bbdd11c52f338714cc4b9a5)

- **作者**: yichengj
- **时间**: 2026-08-03T21:54:48Z
- **提交信息**: feat(moe): sync SM12x W4A16 fused MoE family to b12x HEAD (#4255)

## 📌 Description

Updates the SM120/SM121 W4A16 (NVFP4 weights, bf16 activations)
fused-MoE family to current
[b12x](https://github.com/local-inference-lab/sparkinfer) upstream
(`cc9b476`).

Changes:

- Cooperative persistent launches for the fused FC1/FC2 kernel, with
occupancy-aware tile selection and launch bounds.
- A tensor-core decode path for small batches on the packed serving
weights, folding the top-k sum into the FC2 store epilogue and removing
a separate launch.
- Shape-stable route packing: the triton packing kernels specialize on a
power-of-two capacity instead of the exact token count, so decode
batch-size changes no longer recompile. The W4A16 workspaces are sized
to the same capacity.
- A new `fp4_e8m0_k32` (MXFP4 K/32) weight source format, including
scale-tail handling for TP shards that are not 128-aligned.

Public API and behavior changes:

- `b12x_fused_moe`'s `source_format` parameter accepts the new
`fp4_e8m0_k32` value.
- W4A16 workspaces are now sized to the power-of-two route capacity,
slightly larger than before. This is what lets decode batch-size changes
reuse one compiled route-packing kernel instead of recompiling.
- Kernel launches now dispatch through torch custom ops, registered at
module import. This brings the family in line with the library-wide
convention it predated.

Upstream features with no FlashInfer target checkpoint are not included:

- NF3 (3-bit normal-float) weights. Their kernel branches stay: they
compile out and keep future sync diffs clean.
- The NVFP4+NF3 hybrid entry points.
- The native-ModelOpt small-batch micro kernel.
- The SiTU and swiglu-oai activations.

## 📊 Performance

Speedup over the previous kernels at the MoE shape of a Nemotron
variant, with relu2 and silu activations, run under CUDA graphs, median
of three runs. Each cell reads RTX 5080 / RTX Pro 6000 Server Edition /
GB10:

| Activation | m=1 | m=4 | m=16 | m=64 | m=2048 |
|---|---|---|---|---|---|
| relu2 | 1.07x / 1.15x / 1.11x | 1.03x / 1.07x / 1.04x | 1.00x / 1.00x
/ 1.02x | 0.99x / 1.00x / 1.03x | 12.91x / 18.52x / 1.00x |
| silu | 0.98x / 1.23x / 1.10x | 0.99x / 1.05x / 1.02x | 0.95x / 0.98x /
1.01x | 0.95x / 0.98x / 1.00x | 11.70x / 16.88x / 1.02x |

The m=2048 cells fix a stall rather than measure a general kernel win:
the fused kernel uses grid-wide barriers but was not launched
cooperatively, so at large m CTAs could spin waiting for peers that were
never co-scheduled. GB10 kept the whole grid resident and never hit the
stall, so its m=2048 cells have no win to inherit.

## 🔍 Related Issues

#4223 (item 3).

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

- `tests/moe/test_b12x_fused_moe.py` (142 cases) passes on SM121, both
on the default dispatch and with the W4A16 path forced.
- Added `tests/moe/test_b12x_w4a16_route_pack.py` (64 cases): route
packing against a host reference, covering `expert_map`, invalid expert
ids, preallocated buffers, and the workspace capacity contract.
- Weight preparation is bit-identical to the previous implementation
across the supported source formats and activations.

## Reviewer Notes

- Most of the diff is upstream code taken as is. FlashInfer-local
changes are limited to the import remaps, the two support modules, the
API-boundary checks, the workspace sizing in `moe_dispatch`, and the
decode-path cap below.
- One tuning deviation from upstream: the tensor-core decode path is
selected up to m = 4 instead of upstream's m = 8. The crossover to the
route-packed GEMM varies by card, so the cap conservatively stops where
the decode path wins or ties on every card measured.
- The fused kernel compiles at DSL optimizer level 3 instead of
upstream's 2. Level 3 generates a faster mainloop on the DSL version
pinned here, at the cost of a longer compile for this kernel.
- The kernels import activation metadata and a kernel compile cache from
upstream's library. The two new modules, `moe_w4a16_activations.py` and
`moe_w4a16_compiler.py`, are small local implementations of those two
pieces.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded Blackwell W4A16 fused MoE support for NF3, NVFP4, ModelOpt,
CompressedTensors, and FP4 E8M0 formats.
* Added configurable activations, SwiGLU parameters, routing,
calibration, and launch options.
* Improved route packing for large workloads, dynamic capacities, expert
remapping, and invalid route IDs.
* Added optimized quantization, dequantization, conversion, and
matrix-operation support.
  * Added compile caching to reduce repeated kernel compilation.

* **Bug Fixes**
  * Improved workspace sizing and safe handling of zero-valued scales.

* **Tests**
* Added coverage for route grouping, padding, capacity fallbacks, large
shapes, and expert mapping.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [5a4b54b](https://github.com/flashinfer-ai/flashinfer/commit/5a4b54bed1dfe6f112cd4ec9bc196da517369f46)

- **作者**: yichengj
- **时间**: 2026-08-03T21:43:37Z
- **提交信息**: perf(moe): sync SM12x NVFP4 fused-MoE kernels to b12x HEAD (#4285)

## 📌 Description

Syncs the SM12x NVFP4 (W4A4) fused-MoE kernels behind `b12x_fused_moe`
and `B12xMoEWrapper` with upstream
[b12x](https://github.com/local-inference-lab/sparkinfer) at `f9be272`,
reaching backend parity.

The module now has four kernels. `MoEDirectMicroKernel` takes the
smallest decode batches, `MoEMicroKernel` and `MoEStaticKernel` cover
the rest of decode with tile assignments fixed at launch, and
`MoEDynamicKernel` covers prefill by distributing tiles through an
in-kernel work queue.

Changes:

- Adopt upstream's current `MoEDirectMicroKernel`, replacing a stale
copy in `moe_direct_micro_kernel.py` that was never routed to. It reads
the top-k ids directly, so the smallest batches skip the routing
pre-pass that dominates their runtime, and it now supports gelu_tanh.
- Let `MoEDynamicKernel` use tiles smaller than 128 rows, so sparse
routing stops padding every expert up to 128.
- Launch all kernels cooperatively. They synchronize the whole grid
between phases, which deadlocks if concurrent work keeps part of the
grid off the GPU.
- Simplify `MoEDynamicKernel`'s work queue and size its pipeline stages
from the real shared-memory footprint.
- Vectorize `MoEStaticKernel`'s scatter epilogue and refresh the decode
tile heuristics.
- Restrict the fast FP4 quantizer to gated activations, since relu2's
squared outputs need the exact one.

Public API and behavior changes: none.

## 📊 Performance

Versus main, measured over 38 target-model MoE shapes on three GPUs.
Geomean speedup per shape group:

| shape group | DGX Spark | RTX 5080 | RTX Pro 6000 SE |
|---|---|---|---|
| decode, batch 1-2 | 1.06x | 1.30x | 1.40x |
| decode, batch 4-40 | 1.00x | 1.00x | 1.00x |
| prefill, batch 512-2048 | 1.10x | 1.10x | 1.09x |
| prefill, batch 8192 | 1.00x | 1.00x | 1.00x |

- The batch 1-2 gains come from the new `MoEDirectMicroKernel`; the
shapes it serves win up to 2.3x.
- The prefill gains come from `MoEDynamicKernel` picking tiles smaller
than 128 rows; those shapes win up to 1.26x.

## 🔍 Related Issues

#4223 (item 2).

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

- On SM121 (DGX Spark GB10): `tests/moe/test_b12x_fused_moe.py` (157
cases) and `tests/moe/test_unified_moe_b12x.py` (58 cases) pass,
including tests that force each backend and a test that a smaller tile
is picked again after a large-batch call.

## Reviewer Notes

Deviations from the b12x source, beyond import plumbing:

- gelu_tanh added to `MoEDirectMicroKernel`, matching the activation
coverage of the module's other kernels.
- The module's API accepts reciprocal-form scales but upstream's kernel
only takes multipliers, so dispatch inverts them before launch.
- `MoEDirectMicroKernel`'s cutover is re-measured: upstream's only
alternative is its counterpart of `MoEDynamicKernel`, while here it
competes with `MoEMicroKernel` and `MoEStaticKernel`.
- Upstream sizes scratch and builds the kernel together inside one plan
object, so their tile sizes always match. FlashInfer has no plan object,
so the workspace cache is keyed by tile size to give the same guarantee.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [da42be0](https://github.com/flashinfer-ai/flashinfer/commit/da42be08026e1d396ce89349b05b25dec5bbc0c9)

- **作者**: Jimmy Zhou
- **时间**: 2026-08-03T20:53:53Z
- **提交信息**: test(msa_ops): fix stale split-K heuristic expectation on high-SM GPUs (#4303)

## 📌 Description

Fixes #4276 on `main`. Same one-line test fix as #4273, which targets
`release-v0.6.16` — `main` and `release-v0.6.16` are byte-identical for
both `tests/msa_ops/test_proxy_fp4.py` and
`flashinfer/msa_ops/proxy_score.py`, so the bug is present on `main` too
and #4273 alone does not cover it.

`test_proxy_split_k_heuristic` hard-coded the fp4 split factor as
`ceil(2*sm/8)`, but `_proxy_split_k_fp4` delegates to the
`_split_k_makespan_argmin` model, which caps at one CTA wave and breaks
ties to the smaller split. The closed form ignores wave quantization and
KV-tile rounding, so it diverges from the implementation on most SM
counts:

| SMs | model | `ceil(2*sm/8)` | |
|---|---|---|---|
| 82 | 20 | 21 | mismatch |
| 108 (H100) | 27 | 27 | ok |
| 132 (B200) | 32 | 33 | mismatch |
| 144 | 35 | 36 | mismatch |
| 170 (RTX 5090 / sm120) | 40 | 43 | mismatch |
| 192 | 47 | 48 | mismatch |

sm120 CI is just where it first surfaced. This is a test-only bug — the
kernel and the heuristic are correct.

Assert against `_split_k_makespan_argmin(8, 512, 2 * sm)` instead of a
closed form. `get_device_sm_count == multi_processor_count`, so this
mirrors exactly what `_proxy_split_k_fp4` computes and stays correct
regardless of the runtime SM count, while still exercising the real code
path (residency target + degenerate-case guards).

## 🔍 Related Issues

Fixes #4276. Release-branch counterpart: #4273.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Diff is byte-identical to #4273. Not runnable on my local L40S (sm89 —
`_skip_if_unsupported()` skips); relies on CI's sm120 runner, which is
where the original failure was caught.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated split-factor validation to use the makespan model for more
accurate small-grid heuristic coverage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [76c5836](https://github.com/flashinfer-ai/flashinfer/commit/76c583655cf789051fca5870fef2adb8e544b576)

- **作者**: Adrian
- **时间**: 2026-08-03T16:18:44Z
- **提交信息**: test: Add sharding support to scripts/task_run_unit_tests.sh (#4141)

<!-- .github/pull_request_template.md -->

## 📌 Description

Unit test can optionally run in shards for parallelization

## 🔍 Related Issues

A few, for example:
https://github.com/flashinfer-ai/flashinfer/issues/3936

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
## Summary by CodeRabbit

* **New Features**
* Added end-to-end deterministic test sharding with planning, execution
leasing, JSON progress/events, and resumable finalize/summarize
artifacts.
* Introduced a unit-test runner CLI (plan/run/finalize/summarize) and a
pytest sharding plugin, including `solo`-group collection.
* Added tools to scan sharded JUnit outputs and refresh timing estimates
(including reproducible estimate outputs).
* **Documentation**
* Expanded guidance on timing estimate artifacts and scan/refresh/prune
workflows.
* **Tests**
* Expanded coverage for sharding planner/scanner/runner CLI, JUnit
utilities, atomic writes, and estimate-refresh reproducibility.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4433996](https://github.com/flashinfer-ai/flashinfer/commit/4433996e45def64146c3aaf71341c4090a00c4fa)

- **作者**: eigen
- **时间**: 2026-08-03T12:39:45Z
- **提交信息**: feat(cake_kda): add optimized B200 recurrent decode backend (#4279)

## 📌 Description

This PR exports the CAKE internal recurrent-KDA decode family as 23
frozen CUDA
modules behind the existing public
`flashinfer.kda_decode.recurrent_kda` API. The export covers the exact
B200
(`sm_100a`) BF16 D128 contracts for `T=1..6` and keeps the existing
CuTe-DSL
implementation as the default.

`backend="cake"` is an explicit top-level choice. Once selected, a
supported
call launches exactly one Cake module. A contract mismatch raises
`ValueError`; it never falls back to CuTe-DSL. Calls that omit the
option keep
the existing `backend="cute-dsl"` behavior.

### Supported contracts

All Cake routes require exact compute capability 10.0, BF16
Q/K/V/G/beta/output/state, key and value dimensions both equal to 128,
in-kernel Q/K L2 normalization, a finite scale, `HV >= H`, and
`HV % H == 0`. Q/K/V/beta/output are contiguous; G may pad only its
token
stride, and state may pad only its outer slot stride while retaining
compact
`[HV, 128, 128]` blocks. Metadata is contiguous int32, and output/state
must
not alias one another or any read-only input.

- `T=1` uses the standard decode API (`[N, 1, ...]`) with precomputed
gates,
pre-sigmoided beta, and no `A_log`, `dt_bias`, `lower_bound`, or
source-state
pool. The wrapper presents the packed frozen ABI through zero-copy views
and
  cached identity metadata. Explicit T1 `cu_seqlens` is outside the Cake
  contract and raises rather than launching or falling back.
- `T=2/4/5/6` use packed speculative decode with
  `num_spec_tokens=T-1`, Q/K `[1, N*T, H, 128]`, V/G
`[1, N*T, HV, 128]`, beta `[1, N*T, HV]`, packed checkpoint indices, and
precomputed gates. All `T` checkpoint states are written; padded
sequences
  retain the public API semantics.
- `T=3` preserves the measured lower-bound contract:
  `num_spec_tokens=2`, `H=HV=16`, `N in {1,2,4,8,16}`, raw BF16 gates,
  float32 `A_log` and `dt_bias`, a finite negative `lower_bound`, and
  `use_gate_in_kernel=True`.

Optional modes outside these contracts, including source-state reads and
logit beta, are rejected by the explicit Cake backend.

### Frozen inventory and measured dispatch

| T | Frozen modules | Public dispatch |
|---:|---|---|
| 1 | four WY splits `{1,2,4,8}` plus direct one-warp splits `{16,8}` |
direct split 16 when `W <= 2S`, otherwise direct split 8 |
| 2 | splits `{1,2,4,8}` | split 4 |
| 3 | lower-bound split 4 | split 4 |
| 4 | splits `{1,2,4,8}` | split 2 |
| 5 | coefficient-Gram splits `{1,2,4,8}` | CTA-wave policy below |
| 6 | coefficient-Gram splits `{1,2,4,8}` | CTA-wave policy below |

Here `W=N*HV` and `S` is the device SM count. For `T=5/6`, the CTA-wave
policy selects split 8 for `W <= 3S/8`, split 2 for
`3S/8 < W <= S/2`, split 4 for `S/2 < W <= 3S/4`, split 2 for
`3S/4 < W <= 3S/2`, and split 1 above that range.

The 23 modules are registered through both exact-`sm_100a` JIT and AOT
paths.
Raw and normalized SHA-256 assertions protect every frozen generated
CUDA body
against source drift. Launches use the caller's current CUDA stream and
require
no extra workspace.

## 🧪 Validation

Final validation used candidate
`3f93eff31974d7073a74fa749b0fe9b1d3f50696` on
`NVIDIA B200` (`sm_100a`, compute capability 10.0), driver `580.82.07`,
CUDA
`12.9` (nvcc `12.9.41`), PyTorch `2.8.0a0+5228986c39.nv25.05`, and
CUTLASS
`4.6.1`.

| Gate | Result |
|---|---|
| Public `recurrent_kda` output and complete mutated-state correctness
against explicit `backend="cute-dsl"` across all 30 benchmark shapes,
plus targeted checkpoint, padding, layout, stream, and CUDA Graph
coverage | Passed: 30/30 benchmark shapes, 20/20 targeted GPU tests, and
123/123 CPU and trace tests |
| Cold JIT compile and cache reload for all 23 modules | Passed: 23/23
modules |
| Exact-`sm_100a` AOT registration for all 23 modules and JIT-disabled
execution with zero missing-JIT fallback | Passed: 23/23 registrations,
143/143 JIT-disabled tests, and zero missing-JIT records |
| `compute-sanitizer` memcheck and synccheck over the `T=1..6` public
Cake routes, both direct T1 schedules, and a non-identity-metadata
direct T1 safety case | Passed: 12/12 tests and 0 errors under each
sanitizer |
| Ruff checks and pre-commit hooks on all 37 files changed from the
pinned upstream baseline | Passed: Ruff check, Ruff format, and all
pre-commit hooks |

The full repository test suite was not run.

### Fresh B200 public-API CUPTI benchmark

All three clean checkouts are invoked through
`flashinfer.kda_decode.recurrent_kda`: the candidate uses
`backend="cake"` and the baselines use their source-default public API.
Every candidate row first compares the complete output and mutated BF16
state
against explicit `backend="cute-dsl"` at `atol=rtol=1e-2`.

The pinned baselines are:

- upstream main

[`39f2ce47663243e25b311a7e64681d742905f974`](https://github.com/flashinfer-ai/flashinfer/commit/39f2ce47663243e25b311a7e64681d742905f974);
- the FlashInfer baseline used to reproduce the CAKE internal comparison

[`cea7f46ffc190cabf82c95a39cd0d2aa6c888c17`](https://github.com/flashinfer-ai/flashinfer/commit/cea7f46ffc190cabf82c95a39cd0d2aa6c888c17).

The matrix has five shapes per token count (30 total): `T=1/2/4/5/6` use
`N={8,16,32,64,128}`, `H=16`, `HV=32`; `T=3` uses
`N={1,2,4,8,16}`, `H=HV=16`. Inputs are deterministic seed-42 BF16 D128
data with `scale=1/sqrt(128)`. Timing uses CUPTI with cold-L2 flushing
and
CUDA Graphs disabled. State/output restoration and warm-up use separate
allocations outside the measured call. Results use nine paired rounds in
a
three-source cyclic Latin-square process order. Speedup is
`baseline_time / candidate_time`; each table entry is a geometric mean
over
the five matching shapes. These are fresh public-API measurements, not
copied
from CAKE internal results.

| T | cases | ratio-of-medians vs upstream | median-paired vs upstream |
ratio-of-medians vs CAKE internal baseline | median-paired vs CAKE
internal baseline |
|---:|---:|---:|---:|---:|---:|
| 1 | 5 | 1.0923x | 1.0922x | 1.0905x | 1.0869x |
| 2 | 5 | 1.0689x | 1.0705x | 1.0710x | 1.0709x |
| 3 | 5 | 1.1470x | 1.1622x | 1.1433x | 1.1448x |
| 4 | 5 | 1.0872x | 1.0846x | 1.0866x | 1.0800x |
| 5 | 5 | 1.1904x | 1.1954x | 1.1894x | 1.1912x |
| 6 | 5 | 1.2418x | 1.2421x | 1.2426x | 1.2426x |

Overall across all 30 shapes:

- ratio-of-medians geomean vs upstream: `1.1363x`;
- median-paired geomean vs upstream: `1.1394x`;
- ratio-of-medians geomean vs CAKE internal baseline: `1.1356x`;
- median-paired geomean vs CAKE internal baseline: `1.1343x`.

<details>
<summary>Per-shape ratio-of-medians results (30 cases)</summary>

| T | N | Selected variant | Candidate median (us) | Upstream median
(us) | CAKE internal baseline median (us) | Speedup vs upstream |
Speedup vs CAKE internal baseline |
|---:|---:|:---|---:|---:|---:|---:|---:|
| 1 | 8 | `d128_t1_precomputed_direct_split16` | 6.336 | 7.008 | 7.040 |
1.1061x | 1.1111x |
| 1 | 16 | `d128_t1_precomputed_direct_split8` | 9.504 | 9.888 | 9.920 |
1.0404x | 1.0438x |
| 1 | 32 | `d128_t1_precomputed_direct_split8` | 16.096 | 17.152 |
17.088 | 1.0656x | 1.0616x |
| 1 | 64 | `d128_t1_precomputed_direct_split8` | 27.648 | 31.008 |
30.656 | 1.1215x | 1.1088x |
| 1 | 128 | `d128_t1_precomputed_direct_split8` | 50.944 | 57.600 |
57.536 | 1.1307x | 1.1294x |
| 2 | 8 | `d128_t2_precomputed_split4` | 8.736 | 10.464 | 10.592 |
1.1978x | 1.2125x |
| 2 | 16 | `d128_t2_precomputed_split4` | 15.968 | 16.448 | 16.448 |
1.0301x | 1.0301x |
| 2 | 32 | `d128_t2_precomputed_split4` | 27.871 | 28.224 | 28.031 |
1.0127x | 1.0057x |
| 2 | 64 | `d128_t2_precomputed_split4` | 48.512 | 50.464 | 50.623 |
1.0402x | 1.0435x |
| 2 | 128 | `d128_t2_precomputed_split4` | 90.976 | 97.662 | 97.824 |
1.0735x | 1.0753x |
| 3 | 1 | `d128_t3_lower_bound_split4` | 6.048 | 6.976 | 7.008 | 1.1534x
| 1.1587x |
| 3 | 2 | `d128_t3_lower_bound_split4` | 6.496 | 7.488 | 7.360 | 1.1527x
| 1.1330x |
| 3 | 4 | `d128_t3_lower_bound_split4` | 7.040 | 7.872 | 7.871 | 1.1182x
| 1.1180x |
| 3 | 8 | `d128_t3_lower_bound_split4` | 8.160 | 9.888 | 9.856 | 1.2118x
| 1.2078x |
| 3 | 16 | `d128_t3_lower_bound_split4` | 14.464 | 15.936 | 15.936 |
1.1018x | 1.1018x |
| 4 | 8 | `d128_t4_precomputed_split2` | 13.216 | 15.136 | 15.136 |
1.1453x | 1.1453x |
| 4 | 16 | `d128_t4_precomputed_split2` | 23.359 | 23.999 | 23.904 |
1.0274x | 1.0233x |
| 4 | 32 | `d128_t4_precomputed_split2` | 41.440 | 42.464 | 42.431 |
1.0247x | 1.0239x |
| 4 | 64 | `d128_t4_precomputed_split2` | 73.855 | 81.663 | 81.856 |
1.1057x | 1.1083x |
| 4 | 128 | `d128_t4_precomputed_split2` | 139.392 | 158.783 | 158.750 |
1.1391x | 1.1389x |
| 5 | 8 | `d128_t5_precomputed_gram_split1` | 13.792 | 17.120 | 17.119 |
1.2413x | 1.2412x |
| 5 | 16 | `d128_t5_precomputed_gram_split1` | 25.920 | 30.336 | 30.239
| 1.1704x | 1.1666x |
| 5 | 32 | `d128_t5_precomputed_gram_split1` | 48.704 | 53.599 | 53.407
| 1.1005x | 1.0966x |
| 5 | 64 | `d128_t5_precomputed_gram_split1` | 85.983 | 104.255 |
104.319 | 1.2125x | 1.2133x |
| 5 | 128 | `d128_t5_precomputed_gram_split1` | 166.846 | 205.725 |
206.142 | 1.2330x | 1.2355x |
| 6 | 8 | `d128_t6_precomputed_gram_split1` | 15.264 | 19.584 | 19.680 |
1.2830x | 1.2893x |
| 6 | 16 | `d128_t6_precomputed_gram_split1` | 28.831 | 35.168 | 35.135
| 1.2198x | 1.2187x |
| 6 | 32 | `d128_t6_precomputed_gram_split1` | 54.656 | 62.304 | 62.176
| 1.1399x | 1.1376x |
| 6 | 64 | `d128_t6_precomputed_gram_split1` | 95.904 | 121.759 |
121.951 | 1.2696x | 1.2716x |
| 6 | 128 | `d128_t6_precomputed_gram_split1` | 186.014 | 242.493 |
242.462 | 1.3036x | 1.3035x |

</details>

Evidence:

- source bundle SHA-256:
  `33f8362662ba1952d0b1134e85a594c5d7e9758521a63950e3dc2630b58403d1`;
- benchmark summary SHA-256:
  `99ac081e3c3b22007b6b7e00ee581dc7331bb4a6fae87aec639fe2a2fead12ef`;
- AOT registration receipt SHA-256:
  `1bb40d06442215747674521d76533d8b736d4b59a47d206fab0feb3053952275`;
- validation evidence manifest SHA-256:
  `b3c4f22fab77c18b0e7d8364844c7d3c6977e6de6432836de71c1e0ea2b9feda`.

## 🚀 Pull Request Checklist

- [x] Tests and API documentation were added or updated.
- [x] The Cake backend is opt-in and strict; unsupported Cake contracts
raise
  without entering CuTe-DSL.
- [x] Frozen-source integrity and exact-`sm_100a` JIT/AOT registration
are
  covered.
- [ ] The full repository test suite was not run.

## Reviewer notes

The main review surfaces are:

1. strict `backend="cake"` eligibility and no-fallback behavior;
2. packed checkpoint/state semantics and buffer-alias guards;
3. the measured `T=1..6` dispatch policy; and
4. frozen-source integrity plus exact-`sm_100a` JIT/AOT integration.

Related to #4254.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [1d2fc15](https://github.com/flashinfer-ai/flashinfer/commit/1d2fc15ca10a8d1b9979e41c1ab0141087a519af)

- **作者**: eigen
- **时间**: 2026-08-03T07:57:26Z
- **提交信息**: feat(cake_kda): add optimized B200 recurrent prefill backend (#4262)

<!-- Suggested PR title: feat(kda): add optimized B200 recurrent prefill
backend -->

## 📌 Description

This PR adds an CAKE-generated optimized SM100a BF16 recurrent-KDA
prefill backend and
dispatches to it through the existing `recurrent_kda` API.

The new backend coexists with the current CuTe-DSL implementation.
Decode
(`T=1`), speculative decode, GQA, state-pool/checkpoint features,
unsupported
layouts and dtypes, and non-B200 devices continue to use the existing
backend
unchanged.

### Dispatch contract

The optimized path is selected only when all of the following hold:

- the device is exactly compute capability 10.0 (B200 / SM100a);
- the call is ordinary multi-token prefill: fixed `T > 1`, or packed
input
  with more tokens than sequences;
- Q, K, V, and G are contiguous BF16 `[B, T, H, 128]` tensors with a
shared
  head count, and beta is contiguous BF16 `[B, T, H]`;
- `A_log` is contiguous FP32 `[H]`, while `dt_bias` is contiguous FP32
  `[H, 128]` or `[H * 128]`;
- `use_qk_l2norm_in_kernel=True`, `use_gate_in_kernel=True`,
  `beta_is_logit=True`, and `lower_bound` is finite and negative;
- speculative decode, GQA, state indices, committed-state sources, and
  accepted-token/checkpoint features are disabled.

Packed input uses `B=1` and contiguous CUDA int32/int64 `cu_seqlens`.
The
binding consumes int64 offsets; CUDA graph capture therefore requires
callers
to supply int64 offsets directly. An optional contiguous CUDA int32
`seq_order` can order packed sequences for better tail utilization.

Calls that do not exactly match this contract fall back to the existing
CuTe-DSL path.

### Physical schedules and true in-place state update

- M64 is used only for fixed-layout `B=1, H=64`.
- M128 handles every other eligible fixed-layout call and all eligible
packed
  calls.
- State layout remains BF16 `[N, H, V, K]` with `V=K=128`.
- A supplied `initial_state` is passed as both the initial- and
final-state
kernel pointer. The kernel updates that allocation directly; there is no
  state scratch allocation and no post-kernel `copy_`/memcpy.
- M128 assigns one CTA to each `(sequence, head)`. M64 assigns two CTAs
whose
64-row value partitions are disjoint. Each CTA loads all initial-state
rows
it owns before storing those same final-state rows, making exact pointer
  aliasing safe.
- The binding accepts either disjoint state buffers or an exact
full-range
  alias and rejects partial overlap.
- When `initial_state=None`, final-state storage is created only if
  `output_final_state=True`.

The generated source emits `__restrict__` for every pointer and has no
per-argument alias escape hatch, so the removal of `__restrict__` from
only the
two state parameters is an explicitly delimited FlashInfer ABI
integration
patch. The frozen-source test restores those two qualifiers, removes the
existing tensor-map acquire integration prologue, and verifies the
remaining
generated source against its normalized SHA256.

### CUDA graph and tensor-map safety

`RecurrentKDAPrefillWorkspace` owns optional final-state scratch for
calls
without an initial state, beta padding, and separate 768-byte M64/M128
tensor-map descriptor blocks. It binds to one stream, is warmed eagerly
against the exact tensor signature, and is used by one captured
`recurrent_kda` invocation. A workspace that has participated in capture
is
rejected by later Python calls; graph replay remains valid because it
does not
re-enter Python.

Tensor maps are prepared outside capture and published to stable global
storage on the caller stream. Every consumer CTA executes
`fence.proxy.tensormap::generic.acquire.gpu` for all six maps, followed
by a
CTA barrier, before any TMA instruction can consume them.

### Other integration

- Adds JIT and AOT registration for separate M64 and M128 translation
units.
- Updates tracing and API documentation for `seq_order` and
  `prefill_workspace`.
- Adds correctness, routing/fallback, ABI, stream, overlap, workspace,
and
  CUDA graph tests.
- Adds a CUPTI cold-L2 benchmark for the six fixed/packed contract
shapes,
  including a commit- and binary-verified MoonshotAI/FlashKDA peer.

## 🧪 Validation

Final validation was run on pushed head
`f6c3b0c486787e64f76b2be91ddb239ea3ba66ce`, on an NVIDIA B200
(compute capability 10.0), PyTorch `2.13.0.dev20260503+cu132`, CUDA
13.2,
and Python 3.13.13.

| Gate | Result |
| --- | --- |
| Frozen-source/JIT specification tests | 8 passed |
| Full targeted recurrent-KDA prefill suite, including fixed/packed
correctness, M64/M128, non-default streams, and CUDA graph
capture/replay | 28 passed |
| Focused M64/M128 `compute-sanitizer --tool memcheck` | 5 passed;
`ERROR SUMMARY: 0 errors` |
| Focused M64/M128 `compute-sanitizer --tool synccheck` | 5 passed;
`ERROR SUMMARY: 0 errors` |
| Pre-commit hooks on the change | Passed |

The full repository test suite was not run.

### Fresh B200 CUPTI benchmark

The candidate is invoked only through the public
`flashinfer.kda_decode.recurrent_kda` entry point and performs its state
update
in place inside the kernel. Its timed region contains no state memcpy.

The comparison uses six fixed/packed shapes with deterministic seeds,
matching
tensor distributions, BF16 state, and `scale=1/sqrt(128)`.
Preinitialized
rotating state buffers ensure each timed candidate invocation receives
the
same initial state. Allocation, metadata creation, sequence ordering,
state-pool reset, and JIT/cache warmup are outside the measured region.

The peer is `MoonshotAI/FlashKDA._fwd_raw`, from source commit

[`d2ff19a6`](https://github.com/MoonshotAI/FlashKDA/commit/d2ff19a6a0c82f39f796f637ebd1c36090b1268f)
and CUTLASS

[`5c149f52`](https://github.com/NVIDIA/cutlass/commit/5c149f52a436782210263fb2f19b354443a61c6a).
The loaded extension SHA256 is
`997c3a1d1338f8bf9dba3c1a01386b1b74448214c294d64409454cc11141c04c`.
The benchmark records the source revision and independently computed
extension
digest.

Timing uses CUPTI activity tracing, cold-L2 flushing, no CUDA graph, 20
ms
warmup, and 100 ms measurement per block. Each value is the median of
two
independent block medians; the reported scopes occupy symmetric
`PR/raw/.../raw/PR` positions. Speedup is `FlashKDA / this PR`.

| Case | Layout / sequence lengths | Variant | This PR public in-place
API (ms) | FlashKDA raw peer (ms) | Speedup |
| --- | --- | --- | ---: | ---: | ---: |
| H=96 fixed | `[8192]` | M128 | 0.506095 | 1.085277 | **2.1444x** |
| H=96 mixed | `[1300, 547, 2048, 963, 271, 3063]` | M128 | 0.391135 |
0.894702 | **2.2875x** |
| H=96 uniform | `[1024] × 8` | M128 | 0.434992 | 0.735535 | **1.6909x**
|
| H=64 fixed | `[8192]` | M64 | 0.469711 | 0.992638 | **2.1133x** |
| H=64 mixed | `[1300, 547, 2048, 963, 271, 3063]` | M128 | 0.269903 |
0.676574 | **2.5067x** |
| H=64 uniform | `[1024] × 8` | M128 | 0.292567 | 0.495871 | **1.6949x**
|
| **Geometric mean** | | | | | **2.0512x** |

All six output/state comparisons against FlashKDA passed at
`atol=rtol=1e-2`; the maximum observed absolute errors were
`0.0009765625`
for output and `0.015625` for state. The benchmark JSON SHA256 is
`c34b27f9e8fb4e4dfbc500e6976e63668fcd0bff2bb00086cd516de59491f259`.

### Upstream recurrent-KDA comparison

Pinned upstream main does not implement ordinary multi-token
recurrent-KDA
prefill through its public API: fixed `T != 1` is rejected, and packed
standard
decode processes one token per sequence. Speculative decode has
different
checkpoint/state semantics and is not an equivalent workload. The
upstream
prefill comparison is therefore **unsupported / N/A**, rather than
timing a
different operation.

## 🚀 Pull Request Checklist

- [x] Tests were added or updated.
- [x] Targeted tests and pre-commit hooks pass.
- [ ] Full repository test suite was not run.

## Reviewer Notes

The main review surfaces are:

1. strict eligibility and unchanged fallback behavior;
2. exact-alias state ABI and direct in-kernel update;
3. workspace lifetime, stream binding, and CUDA graph rules;
4. tensor-map publication/acquire ordering;
5. the two explicitly delimited frozen-CUDA integration patches and
their
   integrity normalization.


Related to #4254

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optimized recurrent Kimi Delta Attention prefill support for
eligible B200/SM100a configurations.
* Added M64 and M128 execution variants with eager execution and CUDA
graph compatibility.
* Added a phase-neutral `recurrent_kda` API supporting decode,
speculative decode, and prefill workflows.
  * Added reusable prefill workspace support and public package exports.

* **Documentation**
* Added API documentation covering prefill behavior, dispatch,
workspaces, and supported configurations.

* **Tests**
* Added comprehensive coverage for validation, routing, numerical
correctness, workspace reuse, and CUDA graphs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Zihao <zihaoy@nvidia.com>
Co-authored-by: Zihao Ye <expye@outlook.com>

### [ed6f615](https://github.com/flashinfer-ai/flashinfer/commit/ed6f6150058b1863e34795b16fabb3547a488259)

- **作者**: Guangyun Han
- **时间**: 2026-08-03T07:29:31Z
- **提交信息**: fix(gdn): use block-end decay for SM100 state updates (#4311)

## Summary

- restore the block-end cumulative decay when updating the recurrent
SM100 GDN state
- remove the thread-local coordinate materialization used to select that
scalar
- add a shared regression test covering full, partial, and recurrent
blocks on all supported GDN architectures

## Root cause

PR #4133 replaced the fixed block-end lookup with an index derived from
the last coordinate in each thread's partitioned accumulator fragment:

```python
max_coord = tTR_tCcShared[cute.size(tTR_tCcShared) - 1]
cumprod_total = sCumprod[max_coord[1], 0, gate_handle.index]
```


That max_coord coordinate is thread-dependent. Its second coordinate is:

```
tid % 4 == 0: coord[1] = 57
tid % 4 == 1: coord[1] = 59
tid % 4 == 2: coord[1] = 61
tid % 4 == 3: coord[1] = 63
```

Representative output:

```
tid=0   coord=(24, 57)
tid=1   coord=(24, 59)
tid=2   coord=(24, 61)
tid=3   coord=(24, 63)
...
tid=124 coord=(127, 57)
tid=125 coord=(127, 59)
tid=126 coord=(127, 61)
tid=127 coord=(127, 63)
```

The fix directly loads the block-end scalar:

```python
cumprod_total = sCumprod[self.b_t - 1, 0, gate_handle.index]
```

This remains correct for a partial block. The gate loader predicates
out-of-bounds elements after initializing them to the multiplicative
identity `1.0`. Their log2 contribution is therefore zero, so the
inclusive prefix product remains constant after the final valid token
and slot `BT - 1` contains the product over exactly the valid block.

## Reproduction

The regression test uses FP16, sequence lengths `[64, 111, 192]`, one
head, normalized K, and alpha/beta sampled from `[0.99, 1.0)`. These
lengths cover one full block, a non-multiple tail with recurrent carry,
and three aligned blocks.

| Revision | Output max error | Output mismatches | State max error |
State mismatches |
|---|---:|---:|---:|---:|
| Before #4133 (`6258e522`) | `5.80e-4` | `0 / 46976` | `2.28e-4` | `0 /
49152` |
| After #4133 (`f057e15b`) | `1.59e-2` | `1660 / 46976` | `1.01e-2` |
`6361 / 49152` |
| This fix | `5.80e-4` | `0 / 46976` | `2.28e-4` | `0 / 49152` |

## Validation

```bash
PYTHONPATH=. python -m pytest -q \
  tests/gdn/test_prefill_delta_rule.py::test_prefill_block_end_decay
```

Result: `1 passed` on SM100 with CUDA 13. The test now collects on SM90,
SM100, and SM12x so architecture CI covers the shared contract.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved gated delta network prefill behavior for partial chunks and
block-boundary sequence lengths.
* Ensured cumulative decay uses neutral padding values when processing
incomplete chunks.

* **Tests**
* Added GPU coverage comparing prefill results and final states against
the blockwise reference implementation, including decay factors near
one.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3912
- **最后更新**: 2026-08-03T22:25:20Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

根据提供的提交记录，总结如下：

### 1. 主要更新类型
- **Bug修复**：这是一个针对硬件特定评估路径的错误修复，属于维护性更新。

### 2. 关键变更点及与项目方向的关系
- **变更点**：为 GB200 硬件单独分配了一个 SSIM 参考文件夹，替代原先误用的 B200 文件夹。
- **与项目关系**：FastVideo 项目强调多硬件支持和性能优化，该变更确保在 GB200 环境下使用正确的参考数据，与项目适配新硬件、提升评估准确性的方向一致。

### 3. 对项目的影响和潜在意义
- 修复了在 GB200 上运行评估时可能产生的 SSIM 指标错误，避免因参考数据不匹配导致的质量评估失真。
- 体现了项目对硬件差异的精细化处理，有助于提升跨 GPU 型号评估结果的可信度和一致性。

### 4. 值得关注的技术点
- **SSIM 参考文件夹**：说明项目维护了按硬件区分的标准参考数据，这可能是为了消除不同 GPU 在解码、色彩空间转换等环节的细微信号差异，从而统一评估基线。
- **硬件适配策略**：为不同 GPU 型号单独配置评估资源，这种灵活性值得其他类似项目借鉴。

### 5. 对项目发展的影响
- 作为一次小规模但必要的修正，它强化了 FastVideo 在多种新硬件（如 GB200）上的可用性和可靠性，有利于后续用户在特定设备上获得准确的质量评估，从而增强项目的实用性和社区信任度。

## 详细提交记录

### [c3d07c8](https://github.com/hao-ai-lab/FastVideo/commit/c3d07c870bbd8bf8a8f8dc9bd31a49ddd8d503b2)

- **作者**: William Lin
- **时间**: 2026-08-03T22:14:25Z
- **提交信息**: [bugfix]: give GB200 its own SSIM reference folder instead of B200's (#1676)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34226
- **最后更新**: 2026-08-03T19:23:44Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: YiYi Xu, Sayak Paul, Akshan Krithick

## AI分析总结

分析生成失败

## 详细提交记录

### [6f2010e](https://github.com/huggingface/diffusers/commit/6f2010e8bbe61fd2a81a659b858e298edcba8fab)

- **作者**: YiYi Xu
- **时间**: 2026-08-03T16:40:38Z
- **提交信息**: Auto-reply to new model requests with remote code guidance (#14343)

* Auto-reply to new model requests with Modular Diffusers guidance

Points new model/pipeline/scheduler requests at building a Hub-hosted
modular pipeline instead of waiting on a core PR, and asks requesters to
tag @asomoza when they have something to share.

Gates on the `### Model/Pipeline/Scheduler description` heading the issue
form renders rather than on a label: the label the template declares does
not exist in this repo, so GitHub never applies it, and template labels
land after issue creation anyway.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Apply suggestion from @yiyixuxu

* Tighten the new model request reply

Lead with starting on the Hub and frame what follows as a support
decision (work with the authors, upstream a community version, or point
people at the Hub one) rather than a soft no to PRs. Trims the message
by collapsing the author section and the resource list.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Link the Modular Pipelines collection in the reply

Community-built model pipelines belong in the Modular Pipelines
collection rather than Custom Blocks, so point the "we'll add the ones we
like" line there and keep both collections in the resource list.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Recommend starting on the Hub for new models

Adds a callout to the contribution guide asking model authors to get in
touch on a feature request, and community contributors to coordinate
there and start with a Hub repo at the same time.

Points agents the same way: default to publishing a modular pipeline as
remote code rather than opening a PR against src/diffusers.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Apply suggestion from @yiyixuxu

* Apply suggestion from @yiyixuxu

* Update .github/workflows/new_model_request_reply.yml

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* Consolidate the Hub-first guidance into one place

stevhliu noted the new callout in "Adding pipelines, models, schedulers"
overlapped the last two paragraphs of the AI-assisted contributions
section. Drop the community-contributor paragraph there — it is general
contribution policy rather than agent-specific guidance — and point the
model-author paragraph at the callout instead. Carry the custom models
link over so the non-modular Hub path stays covered.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

### [f83ba3b](https://github.com/huggingface/diffusers/commit/f83ba3b7cd758112a36d1c0d63fe6864295ea05b)

- **作者**: Akshan Krithick
- **时间**: 2026-08-03T15:29:06Z
- **提交信息**: refactor flux2 klein kv pipeline tests to the new mixin structure (#14344)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [b16e3ce](https://github.com/huggingface/diffusers/commit/b16e3cec27b5f441ad2d0c119bf2246adee11808)

- **作者**: Akshan Krithick
- **时间**: 2026-08-03T15:28:37Z
- **提交信息**: refactor flux2 klein pipeline tests to the new mixin structure (#14336)

* refactor flux2 klein pipeline tests to the new mixin structure

* use assert_tensors_close instead of torch.allclose

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [3533886](https://github.com/huggingface/diffusers/commit/353388698732a9c1ed22dcdfffc3f5eae8246868)

- **作者**: Sayak Paul
- **时间**: 2026-08-03T15:28:24Z
- **提交信息**: [kernels] download kernels when users request for it. (#14298)

* download kernels when users request for it.

* address review feedback

### [a834536](https://github.com/huggingface/diffusers/commit/a8345366ed15cc1c447c89f2976784b7dc6031f1)

- **作者**: Akshan Krithick
- **时间**: 2026-08-03T08:32:01Z
- **提交信息**: refactor flux2 klein inpaint pipeline tests to the new mixin structure (#14337)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 429
- **最后更新**: 2026-08-03T02:53:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12799
- **最后更新**: 2026-08-03T20:11:06Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

根据仓库背景和提交记录分析，昨日提交集中围绕 **Minimax-H3 模型** 展开，主要涉及训练支持、量化优化、示例重构和文档完善。

### 1. 主要更新类型
- **功能新增**：正式支持 Minimax-H3 训练（含 LoRA 训练流程）。
- **性能优化**：支持量化和磁盘卸载，减少显存占用，提升超大模型在受限资源下的可用性。
- **Bug 修复**：修复 VAE 相关问题和若干训练/推理中的缺陷。
- **重构**：重构 Minimax 相关示例，优化代码结构和文档。
- **文档更新**：完善训练文档和快速上手指南。

### 2. 关键变更点
- **训练能力**：新增 Minimax-H3 的完整训练流程（包括 LoRA），扩大了项目支持的模型类型。
- **资源管理**：引入量化磁盘卸载技术，允许将模型权重临时卸载到磁盘，结合 text_encoder 量化，降低 GPU 压力。
- **示例重构**：统一并精简了 Minimax 示例，使新手更容易上手，同时更新了相关文档。
- **模型修复**：修正了 Minimax-H3 的 VAE 组件问题，提升了生成质量。

### 3. 对项目的影响与意义
- **增强模型生态**：Minimax-H3 的加入使 DiffSynth-Studio 得以覆盖更多视频/图像生成模型，吸引更广泛的用户。
- **降低使用门槛**：通过量化与磁盘卸载优化，普通显卡也能尝试训练/微调大型模型，提升了项目实用性。
- **提升代码质量**：重构和文档更新使项目更易维护、更易参与，有助于社区贡献。

### 4. 值得关注的技术点
- **量化 + 磁盘卸载**：这是解决大模型显存瓶颈的实用方案，值得在项目中推广到其他模型。
- **LoRA 训练**：支持高效微调，降低训练成本，是社区热门方向。
- **VAE 修复**：提示模型特定组件的兼容性调试是集成第三方模型时的常见难点。

### 5. 对项目发展的影响
DiffSynth-Studio 旨在提供多样化的扩散模型工具，包括训练、推理和创意应用。本次提交通过支持新模型、优化资源利用和改善文档，进一步夯实了项目作为“综合扩散模型工作台”的定位，尤其强化了视频生成模型方向的竞争力，有望吸引更多开发者和研究者使用与贡献。

## 详细提交记录

### [dee91e2](https://github.com/modelscope/DiffSynth-Studio/commit/dee91e2002ea24a6499408546121278c915f55e5)

- **作者**: Hong Zhang
- **时间**: 2026-08-03T12:13:08Z
- **提交信息**: Refactor Minimax examples (#1555)

* fix quant disk offload

* update text_encoder quant

* update dataset dir

* update full training

* update docs

* update quick start

### [f47e930](https://github.com/modelscope/DiffSynth-Studio/commit/f47e9304de0f219bd9b23af7b3b1408915a36eb6)

- **作者**: Hong Zhang
- **时间**: 2026-08-03T10:27:27Z
- **提交信息**: Support quantization with disk offloading (#1554)

* fix quant disk offload

* update text_encoder quant

### [ab12bf4](https://github.com/modelscope/DiffSynth-Studio/commit/ab12bf4119b7c9a23ff3359eefb41ba54a658ccb)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-03T08:34:57Z
- **提交信息**: bugfix (#1553)

### [e376839](https://github.com/modelscope/DiffSynth-Studio/commit/e3768399632da81cf8ab205f0133eb1c21b77d5b)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-03T08:30:19Z
- **提交信息**: refine minimax-h3 examples (#1552)

### [a4fb85d](https://github.com/modelscope/DiffSynth-Studio/commit/a4fb85d14b0186972086366cc74e421de61fc94f)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-03T07:19:13Z
- **提交信息**: Minimax h3 vae fix (#1551)

* renmae minimax model id

* fix MinimaxH

### [d1056cf](https://github.com/modelscope/DiffSynth-Studio/commit/d1056cfb4d057b686fdd71e9623523023cc29df7)

- **作者**: Hong Zhang
- **时间**: 2026-08-03T07:14:28Z
- **提交信息**: Support Minimax-H3 training (#1550)

* support h3 train

* lora train docs

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31190
- **最后更新**: 2026-08-03T22:08:29Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: cctry, huangtingwei, Xinyuan Tong

## AI分析总结

### 1. 主要更新类型

- **Bug 修复**：占比最高，涉及 PD 分离（健康 503 误报）、HiSparse 传输、启动循环导入、Mooncake API 导入、CI 加载超时等问题。
- **性能优化**：prefill delayer 的调度策略改进（限制分支延迟 + 动态衰减高水位）。
- **新硬件/模型集成**：AMD gfx950 对 Qwen3.5 的 FMHA FP8 支持（HD256）。
- **可观测性增强**：新增 PD 负载快照中的 `queues.prealloc_ready` 计数器。
- **文档更新**：补充 MiniMax-H3 在 H200 上的拓扑对比数据。
- **CI/测试改进**：为 diffusion 模型增加 2-GPU 一致性覆盖。

---

### 2. 关键变更点与项目整体方向的关系

-

## 详细提交记录

### [bc7e1a0](https://github.com/sgl-project/sglang/commit/bc7e1a07c3ae7733f639ab531fe42c084ed31d84)

- **作者**: Hanming Lu
- **时间**: 2026-08-03T21:43:02Z
- **提交信息**: Bound prefill delayer all-branch delay and decay the max_prefill_bs high-watermark (#32880)

### [7cd79fd](https://github.com/sgl-project/sglang/commit/7cd79fda564c037c567ebd00175d7bdefaa6bd59)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-03T21:21:25Z
- **提交信息**: [CI] Skip absent inline suites when loading timeouts (#33410)

### [4ef1660](https://github.com/sgl-project/sglang/commit/4ef1660cd8b071b9e9a3988a94910fefd0ca3a48)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-03T19:54:29Z
- **提交信息**: [Docs] MiniMax-H3: add measured H200 Ulysses4 vs TP2+Ulysses2 topology data (#33398)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [db0fe37](https://github.com/sgl-project/sglang/commit/db0fe370b72585d02ab775eaf19d5317ea819cd0)

- **作者**: cctry
- **时间**: 2026-08-03T16:44:25Z
- **提交信息**: [PD] Fix false health-503 during decode retraction re-admission (#33118)

### [6cf6611](https://github.com/sgl-project/sglang/commit/6cf661117d9def62eb0a3852c426ecffb12e7e01)

- **作者**: cctry
- **时间**: 2026-08-03T16:44:11Z
- **提交信息**: [PD] Add a queues.prealloc_ready counter to the load snapshot (#33133)

### [0ba46c8](https://github.com/sgl-project/sglang/commit/0ba46c88e5b16c739be0b698ec7405a147a05cb4)

- **作者**: Mick
- **时间**: 2026-08-03T14:40:08Z
- **提交信息**: [diffusion] CI: add minimax-h3 2-gpu consistency coverage (#33281)

### [3953788](https://github.com/sgl-project/sglang/commit/39537885961c535656b2c93159b6ab89401ab450)

- **作者**: huangtingwei
- **时间**: 2026-08-03T12:35:04Z
- **提交信息**: [HiSparse]Fix DeepSeek V4 HiSparse PD Transfers with Separate Host and Device KV Indices (#31901)

Co-authored-by: jackyYang6 <82102811+jackyYang6@users.noreply.github.com>

### [d48ab2d](https://github.com/sgl-project/sglang/commit/d48ab2d386e0287f471d5fafd1e39f35de148eed)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-03T08:53:16Z
- **提交信息**: Fix BCG circular import during server startup (#33371)

### [a2d1003](https://github.com/sgl-project/sglang/commit/a2d1003b185fd060d7375ada08a3894c9d07f6fa)

- **作者**: Xun Sun
- **时间**: 2026-08-03T08:16:41Z
- **提交信息**: [Mooncake] Fix ProcessGroup API imports (#32403)

### [92999d8](https://github.com/sgl-project/sglang/commit/92999d84f46a77b5e12ff0877a89d83d5da133cc)

- **作者**: amd-oshkarav
- **时间**: 2026-08-03T07:25:31Z
- **提交信息**: [AMD]Qwen3.5 integration gfx950 fmha fp8 hd256 (#32046)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1242
- **最后更新**: 2026-08-03T09:04:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88103
- **最后更新**: 2026-08-03T22:22:07Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 30
- **主要提交者**: Varun Vinayak Shenoy, zcxGGmu, Andreas Karatzas

## AI分析总结

根据提交记录，以下是分析总结：

## 一、主要更新类型

| 类型 | 数量/占比 | 代表提交 |
|------|----------|---------|
| Bug修复 | ~10 | #50327、#50417、#50746、#50777、#49056、#50823、#50869、#49230 |
| 功能新增/增强 | ~11 | #48048、#43615、#50721、#50656、#50524、#50383、#50424 |
| 重构/代码清理 | ~4 | #50285、#49389、#50678、#50801 |
| 性能优化 | 2 | #50716、#50776 |
| CI/测试改进 | 5 | #50726、#46844、#50266、#50839、#46870 |
| 文档更新 | 2 | #50624、#46870 |
| 安全修复 | 1 | #50755 |
| UX改进 | 1 | #50750 |

## 二、关键变更点与项目方向关系

1. **前端与会话机制** (#48048)：为请求增加session id传递，为多轮对话和会话管理场景打下基础，契合vLLM作为服务端框架对生产级会话支持的完善。

2. **ModelRunnerV2 系列修复与扩展** (#50327, #50417, #50721, #50678, #50383)：
   - 修复Mamba状态更新、多模态草稿检测恢复
   - 启用路由专家捕获（routed-experts capture）
   - 移动LatentMoERunner到独立文件，并支持大规模批次下分片共享专家
   - 表明MRV2正在快速成熟，从bug修复向性能优化过渡

3. **ROCm 支持增强** (#43615, #50728, #50582, #50726)：
   - 为GFX120x启用AITER和FP8推理
   - 修复AITER MXFP4测试契约、清理MOE环境变量
   - 导出基准脚本到测试产物
   - 显著扩大AMD GPU平台支持范围，包括最新架构

4. **多模态能力提升** (#50424, #50716, #50839, #50755)：
   - 支持量化的DSpark Markov heads（用于多模态推理时的视觉token预测）
   - 优化多模态占位符扫描性能
   - 增加多模态生成模型的PPL测试
   - 修复图像/视频URL的media type编码
   - 安全方面：DeepStream分类为GPU后端并强制像素限制

5. **新模型支持**：
   - K-EXAONE-2.0-750B-A37B (#50524)：大型MOE模型
   - Kimi-K3 系列多项优化（#50582, #50656, #50678, #50383）：专门针对K3架构的深度集成

6. **内核优化与兼容性** (#50776, #50801, #49960)：
   - 窗口化Triton prefill跳过全掩码key块
   - CPU内核调度精炼
   - 修复CPU-only主机上torch.compile崩溃问题

## 三、对项目的影响与潜在意义

- **跨平台能力增强**：ROCm支持从基础组件扩展到先进架构（GFX120x）和复杂特性（AITER、FP8、MXFP4），对AMD用户群体的扩展至关重要。
- **新模型架构适配**：针对Kimi-K3和K-EXAONE等最新MOE模型做专项优化（共享专家分片、LatentMoE重构），显示vLLM对前沿大模型架构的快速跟进能力。
- **运行稳定性提升**：修复多个bug（特别是MRV2和前端API问题），减少启动断言错误，移除废弃的KV scale计算，有助于降低生产环境事故风险。
- **多模态推理完善**：从模型支持、性能到安全限制的系统性改进，巩固vLLM在多模态推理服务领域的竞争力。
- **测试与CI基建强化**：增加Mooncake PD集成测试、KimiLinear PD夜测、多模态PPL测试，提高回归捕获能力，加速开发迭代。

## 四、值得关注的技术点

1. **MRV2 的Mamba状态更新修复**：int32映射处理细节，涉及状态张量标量更新的正确性，对Mamba类状态空间模型在runner中的执行保证重要。
2. **共享专家分片代替复制**：在K3大模型场景下，分片共享专家可显著减少显存占用，对大batch推理的资源利用效率意义重大。
3. **窗口化prefill跳过全掩码key块**：针对长序列窗口中无效块的计算裁剪，可能显著降低某些模式下prefill延迟。
4. **NIXL speculative config兼容性验证**：对集成NIXL的推测解码配置做后端兼容检查，避免错误配置导致的运行时失败。
5. **DeepStream像素限制安全修复**：属于安全本质，限制多模态模型输入图像大小，防止资源耗尽攻击，这属于LLM服务安全问题。
6. **CPU torch.compile修复**：使用`torch.accelerator.synchronize`导致CPU-only崩溃，修复展示了vLLM对CPU后端部署场景的基本保障覆盖。

## 五、对项目发展的综合影响

vLLM正处在**多平台、多架构、多模态并行推进**的阶段。这一日提交反映出的项目发展方向：

- **模型支持广度**：

## 详细提交记录

### [f57123a](https://github.com/vllm-project/vllm/commit/f57123aa2dbc1badb1865b18c724b308f90dceda)

- **作者**: Karen Chung
- **时间**: 2026-08-03T22:18:58Z
- **提交信息**: feat(frontend): session id plumbing into requests (#48048)

Signed-off-by: Karen Chung <karenc@nvidia.com>

### [e578de3](https://github.com/vllm-project/vllm/commit/e578de311c2416e66c6a8b9819586bb91de10f9d)

- **作者**: Varun Vinayak Shenoy
- **时间**: 2026-08-03T22:05:12Z
- **提交信息**: [ModelRunnerV2] Fix scalar Mamba state update with int32 mappings (#50327)

Signed-off-by: Varun Shenoy <varun.vinayak.shenoy@oracle.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [f43e1d2](https://github.com/vllm-project/vllm/commit/f43e1d26e3e6b40398be27b218cf2f2786432028)

- **作者**: skysnow2001
- **时间**: 2026-08-03T21:45:37Z
- **提交信息**: [ROCm] Enable AITER and FP8 inference on GFX120x (#43615)

Signed-off-by: skysnow2001 <skysnow9285@gmail.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [4a3447d](https://github.com/vllm-project/vllm/commit/4a3447d200e5aa428d68d1a00aa00f1a19a1a729)

- **作者**: Raphaël Rialland
- **时间**: 2026-08-03T21:18:14Z
- **提交信息**: [Bugfix][Model Runner V2] Restore multimodal draft capability detection (#50417)

Signed-off-by: Raphael Rialland <raphael.rialland@mistral.ai>

### [42ab184](https://github.com/vllm-project/vllm/commit/42ab184ea74ee6cf2966529c77bb51fd825a5d0c)

- **作者**: aoshen02
- **时间**: 2026-08-03T21:00:13Z
- **提交信息**: [MRV2] Enable routed-experts capture (#50721)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [e279f71](https://github.com/vllm-project/vllm/commit/e279f7158322d81f7b10ec9733fd7f9420d2fdc6)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-03T20:53:18Z
- **提交信息**: [ROCm][Test] Fix AITER MXFP4 oracle contract (#50728)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [c4e9f09](https://github.com/vllm-project/vllm/commit/c4e9f09de74aa1bf885af8cafd949c3c4dca67db)

- **作者**: zcxGGmu
- **时间**: 2026-08-03T20:50:15Z
- **提交信息**: [Bugfix][Frontend] Reject empty gRPC stop strings (#50746)

Signed-off-by: zq <zhouquan1511@163.com>
Co-authored-by: zq <zhouquan1511@163.com>

### [755513d](https://github.com/vllm-project/vllm/commit/755513d9a24fb639a8985172e645c7fe5a263154)

- **作者**: Francesco Fusco
- **时间**: 2026-08-03T20:24:22Z
- **提交信息**: [Hybrid] Stage the postprocess inputs with a single loop over the request list (#48120)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1c0d207](https://github.com/vllm-project/vllm/commit/1c0d20791556861f4c1804b43b03d9cc03ffa6b8)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-03T19:07:59Z
- **提交信息**: [Bugfix] Default Gemma3 Model intermediate_tensors to None (#50777)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [7f2e78b](https://github.com/vllm-project/vllm/commit/7f2e78ba4df2f7091c247155fc5aeecaa73a486d)

- **作者**: Vineeth Sai Varikuntla
- **时间**: 2026-08-03T19:02:23Z
- **提交信息**: [Bugfix] Emit a valid media type from encode_{audio,image,video}_url (#49056)

Signed-off-by: Vineeth Sai <vineethsai4444@gmail.com>

### [8f50685](https://github.com/vllm-project/vllm/commit/8f50685c48d6bc88d199d9560ab67615e1b2c2a4)

- **作者**: Hongxia Yang
- **时间**: 2026-08-03T18:54:04Z
- **提交信息**: [ROCm][Kimi-K3] aiter moe environment variable cleanup (#50582)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>

### [952694e](https://github.com/vllm-project/vllm/commit/952694e3843e478dd99cffd132c756d582fe8a94)

- **作者**: Tzu-Ling Kan
- **时间**: 2026-08-03T18:51:04Z
- **提交信息**: [Bugfix] Validate NIXL speculative config compatibility (#49230)

Signed-off-by: Tzu-Ling <tzulingk@nvidia.com>
Co-authored-by: GPT-5.6 Sol <noreply@openai.com>
Co-authored-by: Cursor Grok 4.5 <noreply@cursor.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [65cf127](https://github.com/vllm-project/vllm/commit/65cf1276a25b5e7dbbed7d3febdd54a815ced8c8)

- **作者**: Almog Tavor
- **时间**: 2026-08-03T18:48:47Z
- **提交信息**: [Kernel] Skip fully masked key blocks in windowed Triton prefill (#50776)

Signed-off-by: almogtavor <almogtavor@gmail.com>

### [76d995d](https://github.com/vllm-project/vllm/commit/76d995df2c80fd1f81901723fa05c992714693b2)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-03T18:09:44Z
- **提交信息**: [CI][ROCm] Export Helion benchmark script in test artifacts (#50726)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [f0de1a6](https://github.com/vllm-project/vllm/commit/f0de1a604cad003379e5bb4dfc3cc5d2a1f25fa8)

- **作者**: drakosha
- **时间**: 2026-08-03T17:34:29Z
- **提交信息**: [Bugfix] Shard UniformTypeKVCacheSpecs block table width under DCP (#50823)

Signed-off-by: Mikhail Kostryukov <mike@triptrack.net>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [5df9999](https://github.com/vllm-project/vllm/commit/5df9999fcfaa72d9eb61348a789058fff805f142)

- **作者**: Tyler Michael Smith
- **时间**: 2026-08-03T15:41:24Z
- **提交信息**: [Kimi-K3] Add option to shard the shared expert instead of replicating (#50656)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [dd11df0](https://github.com/vllm-project/vllm/commit/dd11df04f3b7046c40f13e586ac38a3725bc3c03)

- **作者**: wangxiyuan
- **时间**: 2026-08-03T15:15:13Z
- **提交信息**: [Misc] Remove deprecated calculate_kv_scales runtime KV scale calculation (#49389)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [0cf49a5](https://github.com/vllm-project/vllm/commit/0cf49a5d15d18275972d0cd35c6968731a5d18e1)

- **作者**: Wentao Ye
- **时间**: 2026-08-03T14:59:08Z
- **提交信息**: [Refactor] Remove multiple dead codes (#50285)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [68ca6fd](https://github.com/vllm-project/vllm/commit/68ca6fd02c6cd705c4fa6872317611c83b26b4c6)

- **作者**: Benjamin Chislett
- **时间**: 2026-08-03T14:21:50Z
- **提交信息**: [Bugfix] Remove bad startup assertion (#50869)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>

### [8ba87e0](https://github.com/vllm-project/vllm/commit/8ba87e01813271fec7841b6bec63595aa1698a91)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-03T13:55:51Z
- **提交信息**: [CI] Mooncake PD integration tests (#46844)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [005fa01](https://github.com/vllm-project/vllm/commit/005fa017566177e1a66d75eba7908d326c5acd60)

- **作者**: Fede Kamelhar
- **时间**: 2026-08-03T13:45:23Z
- **提交信息**: docs: document `reasoning_content` output removal as a breaking client change (#50624)

Signed-off-by: fede-kamel <fkamelhar@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9ae11a6](https://github.com/vllm-project/vllm/commit/9ae11a6b895dea5b2275e0b6ad96327af67d3b0c)

- **作者**: Kyungmin Lee
- **时间**: 2026-08-03T13:33:02Z
- **提交信息**: [Model] Add K-EXAONE-2.0-750B-A37B (#50524)

Signed-off-by: lkm2835 <lkm2835@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b977407](https://github.com/vllm-project/vllm/commit/b977407d8be3bc076c1e2d6f3df02b9bdbd1fab9)

- **作者**: Andrii Skliar
- **时间**: 2026-08-03T12:35:39Z
- **提交信息**: Support quantized DSpark Markov heads (#50424)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [ad0bf39](https://github.com/vllm-project/vllm/commit/ad0bf3963eef4c3cf267f78199324b1b340b6a12)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-03T12:20:41Z
- **提交信息**: [CI] KimiLinear PD in nightlies  (#50266)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Claude <noreply@anthropic.com>

### [ec40f6a](https://github.com/vllm-project/vllm/commit/ec40f6a8a62d588dbd216d0509374666caea2f4a)

- **作者**: Ganesh R
- **时间**: 2026-08-03T11:48:48Z
- **提交信息**: [CPU] Fix torch.compile crash from torch.accelerator.synchronize on CPU-only hosts (#49960)

Signed-off-by: R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [32c42c4](https://github.com/vllm-project/vllm/commit/32c42c4f2f894bfd18e9b2fff1fede7fea4885e8)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-03T11:25:49Z
- **提交信息**: [UX] remove torch compile warning when using breakable cudagraph (#50750)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [9acb7b3](https://github.com/vllm-project/vllm/commit/9acb7b3699b2c9e76db380983850c7e4c12941ab)

- **作者**: wang.yuqi
- **时间**: 2026-08-03T11:25:08Z
- **提交信息**: [CI] And PPL test for multimodal generation models  (#50839)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [c8602c7](https://github.com/vllm-project/vllm/commit/c8602c79062440074a018c1d5f875a5571eb6881)

- **作者**: Li, Jiang
- **时间**: 2026-08-03T09:42:53Z
- **提交信息**: [CPU] Refine CPU kernel dispatch (#50801)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [b9d1e24](https://github.com/vllm-project/vllm/commit/b9d1e2437e1ad6d98d301939949072b5c56dfef1)

- **作者**: Jee Jee Li
- **时间**: 2026-08-03T09:36:17Z
- **提交信息**: K3: Move LatentMoERunner (#50678)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [d9dac2b](https://github.com/vllm-project/vllm/commit/d9dac2b3d4cdd57ff2f7c5311bc8aaf3eef3feec)

- **作者**: Christopher Miyai
- **时间**: 2026-08-03T08:34:12Z
- **提交信息**: fix: remove stray duplicate from serving benchmark config (#46870)

Signed-off-by: cmiyai <cmiyai@bu.edu>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [89ac407](https://github.com/vllm-project/vllm/commit/89ac407e3d8bdb34901dc63af71e4b5732de5ca0)

- **作者**: Hareesh Gali
- **时间**: 2026-08-03T08:27:56Z
- **提交信息**: [Perf] Speed up multimodal placeholder and token-match scanning (#50716)

Signed-off-by: Hareesh <hgsata@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [d83eb0b](https://github.com/vllm-project/vllm/commit/d83eb0b36bfbe26fc856ffdb60f05c8bd460f2fd)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-03T08:23:09Z
- **提交信息**: fix(security): classify DeepStream as GPU backend and enforce pixel limits (#50755)

Signed-off-by: jperezde <jperezde@redhat.com>

### [4635cc3](https://github.com/vllm-project/vllm/commit/4635cc3e8f609755ad45f9fc2cdb54fa7552038e)

- **作者**: Jee Jee Li
- **时间**: 2026-08-03T07:49:39Z
- **提交信息**: Shard the K3 Latent-MoE up-projection on large batches (#50383)

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-04
**监控日期**: 2026-08-03
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5815
- **最后更新**: 2026-08-03T21:15:43Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Yukim1, ooooooye, WeiQing Chen

## AI分析总结

根据提交记录并结合项目背景（旨在提供易用、快速、便宜的全模态模型服务），本次提交的主要更新总结如下：

### 1. 主要更新类型
- **模型功能增强**：围绕 MiniMax H3 模型的精度测试与音频加载兼容性改进
- **代码重构**：清理 serve CLI 中的遗留参数
- **社区维护**：更新微信社群二维码

### 2. 关键变更点与项目方向的关系
- **为 MiniMax H3 增加 T2VA 准确度测试**：T2VA（文本到视频/音频）是多模态生成的重要场景，该测试确保模型服务的输出质量，契合 vllm-omni 提供的“全模态”服务目标。
- **为 MiniMax H3 增加 soundfile 回退机制**：音频加载时若默认后端不可用，将自动回退到 soundfile，提升了对不同音频格式和环境的兼容性，降低部署门槛。
- **移除 serve CLI 中的 `--stage-configs-path`**：这是对旧配置方式的清理，使 CLI 更简洁，与新架构保持一致，体现出服务化模块的成熟和收敛。
- **更新微信社区二维码**：属于社区运营层面的维护，不影响核心代码，但有助于用户获取支持。

### 3. 对项目的影响和潜在意义
- 强化了 MiniMax H3 模型的可用性，不仅覆盖生成质量验证，还解决了实际数据加载中的潜在异常，提升用户体验。
- 重构减少了用户误用旧参数的风险，也使开发者维护成本降低，为后续功能迭代腾出空间。
- 社区更新虽小，但反映出项目持续运营和用户生态建设的重视。

### 4. 值得关注的技术点
- **音频加载回退策略**：使用 soundfile 作为 fallback，意味着项目需要跨库处理不同格式（如通过 librosa 或 soundfile），这种兼容性设计在多模态服务中很实用。
- **准确度测试的引入**：说明项目对模型推理精度的关注，避免仅停留在“跑通”层面，而是追求可验证的服务质量。

### 5. 对项目发展的影响
- 本次提交呈现「扩展 + 收拢」的节奏：一方面继续增加对热门多模态模型（MiniMax H3）的支持和测试，另一方面逐步清理历史配置，优化 CLI 体验。
- 这体现了 vllm-omni 从“堆功能”向“稳定高效”过渡，有助于吸引更多生产环境用户，并为其“everyone”的目标奠定基础。

## 详细提交记录

### [900a7f0](https://github.com/vllm-project/vllm-omni/commit/900a7f0813d0482811b0e4dfd3cf7deabbe2429f)

- **作者**: WeiQing Chen
- **时间**: 2026-08-03T15:59:30Z
- **提交信息**: [Model] Add MiniMax H3 T2VA accuracy test (#5709)

Signed-off-by: david6666666 <530634352@qq.com>

### [7a2007c](https://github.com/vllm-project/vllm-omni/commit/7a2007cc17d63ce9070e1feefd29fcca8a93cf34)

- **作者**: Yukim1
- **时间**: 2026-08-03T15:41:52Z
- **提交信息**: [Refactor] Remove legacy --stage-configs-path from the serve CLI (#5647)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [76de642](https://github.com/vllm-project/vllm-omni/commit/76de642c5475732a3351b1c5beb9b86973733688)

- **作者**: WeiQing Chen
- **时间**: 2026-08-03T09:56:16Z
- **提交信息**: Update WeChat community QR code (#5701)

Signed-off-by: David Chen <530634352@qq.com>

### [a4ea67a](https://github.com/vllm-project/vllm-omni/commit/a4ea67a21b20054dacc6e83952f9bd407e8ee4e7)

- **作者**: ooooooye
- **时间**: 2026-08-03T08:24:50Z
- **提交信息**: [Model] Add soundfile fallback for MiniMax H3 audio loading (#5699)

Signed-off-by: brandneway <gyuan4892@gmail.com>

---
