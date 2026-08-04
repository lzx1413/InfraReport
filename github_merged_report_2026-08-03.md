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
- **星标数**: 2124
- **最后更新**: 2026-08-04T06:21:30Z

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
- **星标数**: 2566
- **最后更新**: 2026-08-04T12:49:01Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Chernobyllight, STwangyingrui, Bilang ZHANG

## AI分析总结

### 1. 主要更新类型
- **功能新增**：新增对Bagel和SenseNova-Vision模型的支持，并引入统一的多任务服务器架构。
- **性能优化**：为Wan FFN NVFP4 GEMMs添加split-N workaround，优化特定硬件上的推理性能。
- **重构**：重构远程客户端工具，并引入omni_vision_task/subtask层级结构。

### 2. 关键变更点及其与项目整体方向的关系
- **Wan FFN split-N workaround**：针对NVIDIA Jetson AGX Thor的NVFP4 GEMMs，通过将输出维度拆分并串行执行两次`cutlass_scaled_nvfp4_mm`调用，提升推理效率。该变更仅影响Wan模型的`ffn_0`和`ffn_2`层，且为临时方案，待后端支持架构感知调度后移除。这与项目“轻量视频生成推理框架”的目标一致，旨在提升特定硬件上的性能。
- **Bagel和SenseNova-Vision集成**：引入统一的SenseNova-Vision集成，支持14个公共视觉子任务，并实现官方一致的后处理。该变更通过omni_vision_task/subtask层级和单驻留多任务服务器，简化了多任务处理流程，扩展了框架的模型兼容性，符合项目“支持多种视频生成模型”的方向。

### 3. 对项目的影响和潜在意义
- **性能提升**：split-N workaround针对特定硬件优化，可能显著提升Wan模型在Jetson AGX Thor上的推理速度，增强框架在边缘设备上的实用性。
- **生态扩展**：支持Bagel和SenseNova-Vision，扩大了框架的模型覆盖范围，吸引更多用户和开发者，提升项目在视频生成领域的竞争力。
- **架构优化**：统一的多任务服务器和层级结构，简化了多任务处理逻辑，为未来扩展更多视觉任务奠定基础。

### 4. 值得关注的技术点
- **NVFP4量化与split-N策略**：通过拆分输出维度并串行执行GEMMs，规避硬件限制，展示了在特定架构上优化量化推理的巧妙方法。
- **omni_vision_task/subtask层级**：该设计将复杂视觉任务分解为可管理的子任务，提高了代码的可维护性和可扩展性。
- **临时性方案的设计**：split-N workaround明确标注为临时，体现了项目对技术债务的谨慎管理，确保后续可平滑迁移至更优方案。

### 5. 对项目发展的影响
- **短期**：这些提交增强了框架的硬件适配性和模型兼容性，可能吸引更多用户尝试在边缘设备上部署视频生成模型。
- **长期**：统一的任务层级和服务器架构，为框架向多模态、多任务方向发展奠定基础，符合视频生成领域对多功能、高灵活性框架的需求。同时，对NVFP4优化的探索，可能推动框架在更多硬件平台上的性能优化，提升整体竞争力。

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
- **星标数**: 2184
- **最后更新**: 2026-08-04T14:38:09Z

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
- **星标数**: 6096
- **最后更新**: 2026-08-04T12:10:48Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 6
- **主要提交者**: Guangyun Han, Lee Yongjun, yichengj

## AI分析总结

# FlashInfer 提交分析报告

## 一、主要更新类型

本次提交涵盖**功能新增**（CAKE优化的B200解码/预填充后端、测试分片工具）、**Bug修复**（FP8 E5M2输出支持、GDN状态更新、测试期望修正）、**性能优化**（SM12x W4A16/W4A4 MoE内核同步）以及**测试基础设施改进**。

## 二、关键变更点与项目方向

1. **MoE内核大规模同步**：将SM120/SM121的W4A16和NVFP4 W4A4 fused-MoE内核同步至b12x上游最新版本，引入协作式持久化启动、张量核心解码路径、形状稳定的路由打包，以及新的`fp4_e8m0_k32`权重源格式。这直接服务于项目"高性能推理GPU内核"的核心目标，显著提升MoE场景性能。

2. **CAKE优化后端**：为B200（SM100a）添加了优化的recurrent-KDA解码和预填充后端，通过精确的契约匹配和显式`backend="cake"`选择，在不破坏现有CuTe-DSL路径的前提下提供硬件特化加速。

3. **FP8 E5M2支持修复**：修复了`rmsnorm_quant`和`fused_add_rmsnorm_quant`对E5M2输出类型的静默失败问题，统一了硬件和软件转换路径，使量化内核支持完整的FP8类型族。

4. **GDN状态更新修复**：修复了SM100 GDN状态更新中因线程局部坐标导致的错误，恢复块端累积衰减的正确计算。

5. **测试基础设施**：为单元测试脚本添加分片支持，实现确定性分片、执行租约和可恢复的汇总流程，并修复了高SM GPU上的split-K启发式测试期望。

## 三、项目影响与意义

这些变更体现了FlashInfer**面向特定硬件架构深度优化**的战略方向。MoE内核同步和CAKE后端都针对最新GPU（SM120/SM121/SM100a）进行特化，同时保持API兼容性和回退路径。性能数据显示解码批次的加速最高达2.3倍，预填充也有约1.1倍提升，直接增强了项目在MoE推理场景的竞争力。

## 四、值得关注的技术点

- **协作式持久化启动**：通过网格同步避免死锁，同时提高内核占用率
- **形状稳定路由打包**：以2的幂容量替代精确token数，避免解码批次变化时的重编译
- **契约精确匹配**：CAKE后端通过严格条件检查确保正确性，不匹配时明确报错而非静默回退
- **测试分片确定性**：通过规划、执行租约和可恢复汇总，支持大规模并行测试

## 五、对项目发展的影响

这些提交强化了FlashInfer作为**高性能推理内核库**的定位：一方面通过持续同步上游最佳实践保持MoE内核的领先性能，另一方面通过硬件特化后端（CAKE）探索极致优化空间。测试基础设施的改进和FP8类型支持的完善，则提升了项目的工程成熟度和可用性，为更广泛的部署场景奠定基础。

## 详细提交记录

### [5192059](https://github.com/flashinfer-ai/flashinfer/commit/519205914508547ed5e6ac146bfc3f87abdbb04b)

- **作者**: Lee Yongjun
- **时间**: 2026-08-03T23:00:41Z
- **提交信息**: fix: support fp8 e5m2 output in rmsnorm_quant and fused_add_rmsnorm_quant (#4202)

<!-- .github/pull_request_template.md -->

## 📌 Description

E5M2 output is rarely used in inference, but the current code fails
silently instead of rejecting it. This PR is a small fix to close that
gap.

`rmsnorm_quant` and `fused_add_rmsnorm_quant` quantize to the dtype of
the `out` tensor and the CUDA dispatch accepts e5m2, but:

- CuTe-DSL backend (default): the norm dtype map has no `float8_e5m2`
entry, so an e5m2 out tensor raises `KeyError`; the store epilogue and
the clamp were e4m3 only anyway.
- CUDA fallback (`FLASHINFER_USE_CUDA_NORM=1`): the kernels clamp to
`[-448, 448]` for any output dtype, silently collapsing the e5m2 range
(max 57344).

Changes:

- `norm/utils.py`: `FLOAT8_E5M2_MAX`, e5m2 conversion intrinsics (hw
via`cvt.rn.satfinite.e5m2x2.f32`, sw via bit manipulation), thin fp8
wrappers that select the variant from a constexpr dtype, and a
  `float8_e5m2` dtype map entry.
- `norm/kernels/{rmsnorm,fused_add_rmsnorm}.py`: quant epilogues
dispatch on the output element type; the clamp bound follows the output
dtype. Kernel signatures and compile cache keys are unchanged.
- `include/flashinfer/norm.cuh`: both quant kernels clamp with
`QuantTypeStaticVals<O>::MAX_VAL`, as `layernorm_quant` already does.
The trait moves above the kernels and drops its `ENABLE_FP8` guard:
the fp8 types are always visible (`vec_dtypes.cuh` includes `cuda_fp8.h`
unconditionally), and these kernels are instantiated for fp8 through
`DISPATCH_DLPACK_DTYPE_TO_CTYPE_FP8` even in builds without
`ENABLE_FP8`, so keeping the guard would break the no-fp8 build once
they reference the trait (exercised by
`test_norm_compilation_without_fp8`).
- Tests: `test_norm_quant` and `test_fused_add_rmsnorm_quant`
parametrized over `quant_dtype` (e4m3fn, e5m2), same style as
`test_layernorm_quant`.

Verified on RTX 5090: the full quant grids pass on both backends (3072
CuTe-DSL, 3085 CUDA cases). Both hw and sw conversion paths were checked
bit-exact against torch fp8 casts over all finite fp16 values plus
random and boundary floats, for both formats; since sm_120 always
dispatches the hw path, the sw path was force-compiled with
`use_hw_fp8=False` for this.

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

## Summary by CodeRabbit

* **New Features**
* Added FP8 E5M2 support for RMSNorm quantization and fused add +
RMSNorm quantization.
  * Quantized outputs now support both FP8 E4M3 and E5M2 formats.
* Clamping automatically uses the selected output format’s valid numeric
range.

* **Documentation**
  * Clarified supported FP8 output formats and quantization behavior.

* **Tests**
* Expanded coverage across both FP8 formats, including stride and
large-tensor cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

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
- **星标数**: 3918
- **最后更新**: 2026-08-04T09:46:59Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为 **Bug修复**，针对硬件适配问题进行了定向修正。

**2. 关键变更点**  
- 为 **GB200** 硬件创建了独立的 SSIM（结构相似性）参考文件夹，不再复用 B200 的参考数据。  
- 该变更直接关联到视频生成质量评估环节，确保不同硬件平台在评估指标上的一致性。

**3. 对项目的影响与潜在意义**  
- **提升评估准确性**：GB200 与 B200 在架构或计算特性上存在差异，共用参考数据可能导致 SSIM 指标失真。独立文件夹保证了评估基准的硬件适配性。  
- **增强可维护性**：明确区分硬件专属资源，避免后续版本迭代时因混用引发隐性错误，降低调试成本。  
- **支持多硬件生态**：FastVideo 作为高性能视频生成框架，需适配多种 GPU（如 B200、GB200），此修复完善了其硬件兼容矩阵。

**4. 值得关注的技术点**  
- **SSIM 参考数据的硬件敏感性**：表明视频质量评估不仅依赖算法，还受底层硬件数值精度影响，需按平台隔离基准。  
- **提交粒度**：修复仅针对文件夹分配，未改动评估逻辑，体现了“最小变更”原则，降低回归风险。

**5. 对项目发展的影响**  
FastVideo 定位于高效视频生成与评测，其核心优势之一是对最新硬件的快速适配。本次修复虽小，但直接关系到 **GB200 用户** 的评测可信度，有助于吸引高端硬件用户群体。同时，这种“硬件感知”的细节处理，反映了项目对工程严谨性的重视，为后续支持更多 GPU 型号（如未来架构）奠定了可扩展的评估框架基础。长期看，此类修复能减少用户因指标异常产生的困惑，提升社区信任度，间接促进项目在 AI 视频生成领域的采用率。

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
- **星标数**: 34227
- **最后更新**: 2026-08-04T13:39:19Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: YiYi Xu, Sayak Paul, Akshan Krithick

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以**自动化流程优化**和**测试重构**为主，辅以**功能改进**。具体包括：新增模型请求自动回复工作流、Flux2 Klein系列管线测试重构、以及内核下载机制优化。

### 2. 关键变更点与项目方向
- **自动化回复工作流**（#14343）：新增GitHub Action，自动回复新模型请求，引导用户优先构建Hub托管的模块化管线（Modular Pipelines），而非等待核心PR。这直接呼应了diffusers向**模块化、去中心化**方向发展的战略，鼓励社区贡献者通过远程代码发布模型，减轻核心维护负担。
- **测试重构**（#14336/#14337/#14344）：将Flux2 Klein系列的pipeline、inpaint和KV pipeline测试统一迁移到新的mixin结构，并改用`assert_tensors_close`替代`torch.allclose`。这是对测试基础设施的标准化整理，提升代码可维护性和一致性。
- **内核按需下载**（#14298）：改为用户请求时才下载kernels，优化资源使用和安装体验，属于性能与用户体验改进。

### 3. 项目影响与潜在意义
- 自动化回复将**改变社区贡献路径**，引导用户先发布Hub远程代码，再考虑核心集成，可能显著减少核心PR积压，加速生态扩展。
- 测试重构为后续大规模测试扩展奠定基础，mixin结构让测试更易复用和扩展，符合项目快速增长的节奏。
- 内核按需下载降低安装门槛，对资源受限用户更友好。

### 4. 值得关注的技术点
- 工作流通过**issue表单标题**（而非标签）触发，规避了仓库中标签不存在的问题，体现了对GitHub机制细节的精准把握。
- 回复内容经过多轮打磨，从“软拒绝”转向“支持决策”框架，引导用户与作者协作、上游社区版本或指向Hub版本，沟通策略成熟。
- 贡献指南新增**callout**，明确建议模型作者先开feature request沟通，社区贡献者同步在Hub建仓，形成清晰的协作路径。

### 5. 对项目发展的影响
结合README背景，diffusers作为HuggingFace核心的扩散模型库，正从“中心化核心库”向“Hub生态+核心库”双轨制演进。本次提交通过自动化引导、测试标准化和安装优化，**强化了Hub作为模型分发主渠道的地位**，同时保持核心库的整洁和高质量。这有助于项目在模型数量爆发式增长下维持可维护性，并鼓励社区创新，符合“让AI模型民主化”的使命。

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
- **星标数**: 12805
- **最后更新**: 2026-08-04T14:42:42Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **功能新增**：支持 Minimax-H3 模型的完整训练流程（LoRA 训练）
- **Bug修复**：修复 VAE 相关问题、量化磁盘卸载问题
- **重构优化**：重构 Minimax 示例代码，优化量化逻辑
- **文档更新**：更新训练文档和快速入门指南

### 2. 关键变更点与项目方向的关系
- **Minimax-H3 训练支持**：新增 H3 模型训练能力，包括全量训练和 LoRA 训练，扩展了项目支持的模型范围
- **量化磁盘卸载优化**：改进 text_encoder 量化逻辑，支持磁盘卸载，降低显存占用
- **示例重构**：统一并优化 Minimax 系列示例，提升代码可维护性
- **VAE 修复**：修正 Minimax-H3 的 VAE 实现，提升生成质量

这些变更与项目“提供多样化视频生成解决方案”的核心目标一致，通过扩展模型支持和优化资源使用，降低用户使用门槛。

### 3. 对项目的影响和潜在意义
- **降低硬件门槛**：量化磁盘卸载功能使显存有限的用户也能运行大型模型
- **扩展应用场景**：H3 训练支持使研究者能基于该模型进行定制化训练
- **提升稳定性**：多项 bugfix 增强了代码可靠性，改善用户体验
- **增强项目吸引力**：支持更多模型和训练方式，吸引更广泛的用户群体

### 4. 值得关注的技术点
- **量化与磁盘卸载结合**：在 text_encoder 上实现量化+磁盘卸载，平衡性能与资源
- **LoRA 训练支持**：提供轻量级微调方案，降低训练资源需求
- **VAE 修复细节**：对模型组件的精确修正，体现对生成质量的重视

### 5. 对项目发展的影响
DiffSynth-Studio 作为一站式视频生成工具，这些提交显著增强了其作为研究平台和实用工具的双重价值。通过支持 Minimax-H3 训练和优化资源使用，项目正朝着“更易用、更强大、更灵活”的方向发展，有望吸引更多开发者和研究者参与生态建设，巩固其在视频生成领域的领先地位。

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
- **星标数**: 31261
- **最后更新**: 2026-08-04T14:33:13Z

## 提交统计

- **昨日提交总数**: 15
- **提交者数量**: 12
- **主要提交者**: Hanming Lu, amd-oshkarav, Mohammad Miadh Angkad

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

- **Bug修复**（4项）：CUDA graph批处理捕获、PD健康检查误报、BCG循环导入、Mooncake API导入
- **CI/构建优化**（4项）：缓存持久化、工具链固定、测试超时处理、site-packages清理
- **文档更新**（2项）：目录重命名、MiniMax-H3性能数据补充
- **性能优化**（2项）：prefill延迟器改进、HiSparse KV索引分离
- **功能增强**（2项）：队列计数器新增、AMD Qwen3.5集成

### 2. 关键变更点与项目方向

- **PD（Prefill-Decode）分离架构持续完善**：修复decode重入时的健康检查误报，新增prealloc_ready计数器，反映项目对PD架构稳定性和可观测性的重视
- **Rust扩展构建体系规范化**：固定工具链版本、持久化cargo缓存，确保跨CI任务构建一致性
- **CUDA graph批处理修复**：确保多请求prefill场景下正确捕获graph批次，直接影响推理吞吐
- **HiSparse稀疏注意力优化**：分离host/device KV索引，支撑DeepSeek V4大规模稀疏模型部署

### 3. 项目影响与潜在意义

- **稳定性提升**：修复PD健康检查误报和BCG循环导入，减少服务启动和运行期故障
- **CI效率改善**：缓存持久化和工具链固定可显著缩短构建时间，加速迭代
- **可观测性增强**：新增队列计数器为负载快照提供更细粒度数据，便于容量规划
- **多硬件支持扩展**：AMD gfx950 FMHA FP8集成和Mooncake修复，拓宽GPU兼容性

### 4. 值得关注的技术点

- **prefill delayer的all-branch delay与max_prefill_bs高水位衰减**：这是对动态批处理策略的精细调优，平衡延迟与吞吐
- **HiSparse PD传输中KV索引分离设计**：解决大规模稀疏模型下host/device内存管理的关键问题
- **CI中site-packages影子目录清理**：避免本地安装包遮蔽git checkout版本，保障测试真实性

### 5. 对项目发展的影响

SGLang作为高性能LLM推理框架，本次提交体现了三个发展方向：**一是工程稳定性优先**，大量CI和Bug修复确保生产环境可靠性；**二是PD分离架构深化**，这是支撑高并发、低延迟服务的关键路径；**三是多硬件生态扩展**，AMD和Mooncake支持表明项目正从NVIDIA独占走向多平台适配。文档整理和性能数据补充则反映项目进入成熟期，开始注重知识沉淀和社区协作。整体来看，这些提交是项目从功能快速迭代转向工程化、规模化部署的典型特征。

## 详细提交记录

### [7eb2737](https://github.com/sgl-project/sglang/commit/7eb27372b34679cdc42d22875b328b103b1ef11d)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-08-03T23:56:59Z
- **提交信息**: fix(server): capture legal multi-request prefill CUDA graph batches (#30206)

### [b819d2f](https://github.com/sgl-project/sglang/commit/b819d2fb5bbdff3dfb969b4abd678cf54799e405)

- **作者**: zijiexia
- **时间**: 2026-08-03T23:51:00Z
- **提交信息**: [Docs] Rename docs_new/ to docs/ (#32123)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [c949e91](https://github.com/sgl-project/sglang/commit/c949e91f18d4167c920c66ceab276f649b9e7f88)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-03T23:31:25Z
- **提交信息**: [CI] Remove the orphaned site-packages sglang skeleton that shadows the checkout (#33441)

### [22c2e2b](https://github.com/sgl-project/sglang/commit/22c2e2bcad68368bdc333ef280b151babe92b89c)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-03T23:23:09Z
- **提交信息**: [CI] Persist the cargo build cache across CUDA CI jobs (#33361)

### [b8f6181](https://github.com/sgl-project/sglang/commit/b8f6181bff4ae5b9126e25d51e3e25962d828e28)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-03T23:16:34Z
- **提交信息**: [CI] Build the Rust extensions with the pinned toolchain instead of the image default (#33437)

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
- **星标数**: 88169
- **最后更新**: 2026-08-04T14:42:29Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 33
- **主要提交者**: Christopher Miyai, Karen Chung, Tzu-Ling Kan

## AI分析总结

# vLLM 仓库提交分析总结

## 一、主要更新类型

本次提交涵盖**Bug修复**（约12项）、**新功能与模型支持**（约8项）、**性能优化**（约5项）、**重构与代码清理**（约4项）、**CI/测试改进**（约4项）、**文档更新**（1项）及**安全修复**（1项），整体呈现多维度推进态势。

## 二、关键变更点与项目方向

1. **新模型支持**：新增K-EXAONE-2.0-750B-A37B和GLM-5.2支持，延续vLLM“为所有人提供易用、快速、便宜的LLM服务”的使命，持续扩展模型生态覆盖。
2. **Kimi-K3专项优化**：多项提交围绕K3架构（LatentMoE、共享专家分片、AITER环境变量清理），体现对前沿MoE架构的深度适配。
3. **ModelRunnerV2（MRV2）演进**：修复多模态草稿检测、启用路由专家捕获、修复标量Mamba状态更新，标志新一代模型运行器正加速成熟。
4. **ROCm/AITER支持增强**：启用GFX120x FP8推理、修复MXFP4测试，强化AMD平台竞争力。
5. **混合推理（Hybrid）改进**：修复MRv2前缀缓存竞态、优化后处理输入循环，提升混合推理稳定性与效率。

## 三、项目影响与潜在意义

- **稳定性提升**：修复Qwen3-Omni视频无音轨崩溃、Gemma3中间张量默认值、gRPC空停止字符串拒绝等问题，直接改善用户侧体验。
- **性能优化**：加速多模态占位符扫描、跳过窗口化Triton预填充中全掩码键块、CuTe DSL瘦GEMM扩展，均指向推理吞吐与延迟的进一步优化。
- **架构现代化**：移除废弃的KV scale运行时计算和大量死代码，简化代码库，降低维护成本。
- **安全加固**：DeepStream后端GPU分类与像素限制，填补潜在安全漏洞。

## 四、值得关注的技术点

1. **CuTe DSL扩展**：将CuTe领域特定语言应用于GLM-5.2瘦GEMM，体现vLLM在kernel层面的持续创新。
2. **共享专家分片选项**：K3模型可选择分片而非复制共享专家，为大规模MoE推理提供更灵活的内存/性能权衡。
3. **会话ID管道**：前端会话ID注入请求，为后续会话管理、多轮对话优化奠定基础。
4. **NIXL投机配置验证**：强化投机解码场景下的配置兼容性检查。
5. **量化DSpark Markov头支持**：扩展量化模型类型覆盖。

## 五、对项目发展的整体影响

这些提交表明vLLM正沿着**多硬件平台（NVIDIA/AMD/CPU）、多模型架构（MoE/多模态/混合推理）、多部署场景（PD分离/月蛋糕集成）** 三条主线快速演进。大量AI辅助编码工具（Codex、Claude、Cursor等）参与贡献，反映开源项目协作模式的新趋势。持续强化MRV2和ROCm支持，显示vLLM在保持CUDA领先地位的同时，正积极构建更均衡的硬件生态。整体而言，项目在稳定性、性能、生态广度三方面同步推进，巩固其作为生产级LLM服务框架的领先地位。

## 详细提交记录

### [c810937](https://github.com/vllm-project/vllm/commit/c8109375733e6b788e73c7cc1ed2004234834392)

- **作者**: xiaozhoupy
- **时间**: 2026-08-03T23:49:41Z
- **提交信息**: [Kernel] Extend CuTe DSL skinny GEMM to GLM-5.2 (#49791)

Signed-off-by: Peiyuan Zhou <peiyuanzhou1994@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [6a9109d](https://github.com/vllm-project/vllm/commit/6a9109d865d8abbfe70777ea52520425f1be6d3f)

- **作者**: Ryan Hamby
- **时间**: 2026-08-03T23:22:00Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni crash on video with no audio track when use_audio_in_video=True (#48420)

Signed-off-by: RyanJHamby <ryanhamby22@gmail.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [c2881ce](https://github.com/vllm-project/vllm/commit/c2881ce60302b5455867d2c29cdfae5fbeddecac)

- **作者**: Francesco Fusco
- **时间**: 2026-08-03T22:54:24Z
- **提交信息**: [Bugfix][Hybrid] Fix cross-block race on num_accepted in MRv2 align prefix cache (#50432)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>

### [0b37d83](https://github.com/vllm-project/vllm/commit/0b37d8389f4b8378adab0d3dfa1beffbb152e303)

- **作者**: Chris Fontes
- **时间**: 2026-08-03T22:47:37Z
- **提交信息**: fix: NVFP4 quantization out_dtype should match model dtype, not torch default (#48861)

Signed-off-by: Chris Fontes <2224082+fattchris@users.noreply.github.com>
Co-authored-by: Chris Fontes <chris@fontes.io>
Co-authored-by: Chris Fontes <chris@fontes.dev>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

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
- **星标数**: 5841
- **最后更新**: 2026-08-04T14:42:49Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: WeiQing Chen, Yukim1, ooooooye

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交包含**模型功能增强**（2项）、**代码重构**（1项）和**社区文档更新**（1项），未涉及Bug修复或性能优化。

### 2. 关键变更点及与项目方向的关系
- **MiniMax H3模型支持深化**：新增T2VA（文本到视频）准确性测试和音频加载的soundfile回退机制，表明项目正积极扩展MiniMax H3这一多模态模型的能力边界，与“omni-modality”（全模态）服务定位高度契合。
- **CLI接口清理**：移除遗留的`--stage-configs-path`参数，简化服务启动流程，属于技术债务清理，有助于降低用户使用门槛。
- **社区渠道更新**：更新微信社区二维码，属于运营维护，对项目技术发展无直接影响。

### 3. 对项目的影响和潜在意义
- **模型生态完善**：MiniMax H3的测试覆盖和音频加载鲁棒性提升，增强了项目对多模态模型的实际支持能力，有助于吸引更多模型接入。
- **用户体验优化**：CLI参数清理使服务部署更直观，符合“Easy, fast, and cheap”的项目承诺，降低新用户上手成本。
- **社区连接强化**：更新社区入口有助于扩大用户群，间接促进项目迭代反馈循环。

### 4. 值得关注的技术点
- **soundfile回退机制**：为音频加载提供备选方案，增强了对不同环境依赖的兼容性，这种防御性编程模式值得在模型加载模块中推广。
- **T2VA测试用例**：将视频生成任务的准确性验证纳入测试体系，为后续视频模态支持奠定质量保障基础。

### 5. 对项目发展的影响
结合README中“为所有人提供简单、快速、廉价的全模态模型服务”的定位，本次提交体现了项目在**多模态覆盖广度**和**工程成熟度**上的双线推进：一方面通过MiniMax H3的深度集成扩展模态支持范围，另一方面通过CLI清理提升工程可用性。这种“模型扩展+工程简化”的组合策略，有助于项目在竞争激烈的多模态服务赛道中巩固差异化优势，吸引更多开发者和企业用户。整体来看，提交节奏稳健，聚焦于核心能力的夯实而非激进扩张。

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
