# GitHub Stars 合并报告 - 2026-08-04

**合并日期**: 2026-08-05
**监控日期**: 2026-08-04
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


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2125
- **最后更新**: 2026-08-04T21:49:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2568
- **最后更新**: 2026-08-04T20:47:50Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Musisoul

## AI分析总结

### 提交分析总结

#### 1. 主要更新类型
本次提交为 **Bug修复**，针对训练过程中的学习率调度问题。

#### 2. 关键变更点及与项目方向的关系
- **变更内容**：修复了 `fastwam`（快速预热）训练策略中 `lr_eta_min`（最小学习率）的设置问题。
- **与项目方向的关系**：LightX2V 定位为轻量级视频生成推理框架，训练效率与稳定性是核心目标之一。学习率调度直接影响模型收敛速度与最终质量，此修复直接服务于训练流程的可靠性，与项目“轻量高效”的定位一致。

#### 3. 对项目的影响和潜在意义
- **直接影响**：确保 `fastwam` 策略下学习率下限正确生效，避免因参数错误导致训练震荡或收敛不充分。
- **潜在意义**：提升训练过程的稳定性，减少因调度问题引发的重复实验成本，为后续视频生成模型的快速迭代提供更可靠的基础设施支持。

#### 4. 值得关注的技术点
- **`fastwam` 策略**：一种快速预热+衰减的学习率调度方法，常用于加速早期训练并稳定后期收敛。本次修复表明该策略已进入实际应用阶段，且团队在精细化调参。
- **`lr_eta_min` 的作用**：作为学习率下限，防止衰减过度导致模型更新停滞。修复其设置逻辑，体现了对训练细节的严谨把控。

#### 5. 对项目发展的影响
- **短期**：修复训练流程中的已知缺陷，提升开发者和用户的训练体验。
- **长期**：稳定的训练机制是框架吸引更多模型接入和社区使用的基础。此类细节修复虽小，但累积起来能增强框架的工程成熟度，为 LightX2V 从“推理框架”向“训练+推理一体化”演进铺路，符合视频生成领域对端到端工具链的需求趋势。

---

**总结**：本次提交是一次针对训练调度细节的精准修复，虽规模小，但体现了项目对工程稳定性的重视，有助于巩固 LightX2V 作为轻量级视频生成框架的可靠性口碑。

## 详细提交记录

### [78a036b](https://github.com/ModelTC/LightX2V/commit/78a036b12ac9d0211c7144bb1696813d8213bd69)

- **作者**: Musisoul
- **时间**: 2026-08-04T12:47:30Z
- **提交信息**: Fix: fastwam training lr_eta_min (#1330)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
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


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6100
- **最后更新**: 2026-08-04T21:27:53Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: eigen, feih-nv, Sebastian Huang

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本次提交涵盖**功能新增**（MxInt4 MoE支持、LoRA delta支持）、**性能优化**（NVFP4 TMA路径优化、SM100系列kernel共享）、**代码清理**（移除无用头文件）和**维护性更新**（CODEOWNERS调整、bug修复）。

## 2. 关键变更点

- **SM100系列kernel整合**：将recurrent-KDA decode kernel统一编译为`sm_100f`，在B200/GB200和B300/GB300间共享，同时保留两个物理目标例外（CUDA 12.8的B200和GB300的直接T1变体），性能影响极小（geomean约1.0011x）。
- **MxInt4 MoE支持**：通过`TrtllmMxInt4Config.prepare_weights()`实现BF16到MxInt4的权重量化，新增`TrtllmMxInt4RoutedRunner`，支持预计算路由、FromLogits、专家并行和CUDA graph捕获。
- **NVFP4 TMA优化**：移除临时padding输入分配和全张量拷贝，利用G2S TMA越界零填充处理非128对齐的M，非对齐32K形状性能提升72.1%-72.2%。
- **LoRA delta支持**：为FP4 block-scale MoE路径添加`BiasType::Mn`，支持LoRA微调增量。
- **代码清理**：移除三个launcher中未使用的`<nvrtc.h>`头文件，解决部分容器因缺少`cuda-nvrtc-dev`导致的编译失败。

## 3. 项目影响与意义

这些提交显著增强了FlashInfer作为**高性能GPU推理kernel库**的实用性和兼容性。MxInt4和LoRA支持扩展了MoE的量化方案和微调能力，SM100整合简化了多代Blackwell架构的维护，NVFP4优化直接提升了非对齐场景下的推理性能。

## 4. 值得关注的技术点

- 通过共享kernel减少二进制体积和编译时间的策略，同时保留性能关键路径的精确目标编译
- TMA越界零填充替代显式padding的创新方案，消除非对齐M的拷贝性能悬崖
- 对CUDA toolkit版本差异的精细处理（12.8 vs 12.9+）
- 量化感知的fuzzer测试策略，确保MxInt4路径的正确性

## 5. 对项目发展的影响

这些提交体现了FlashInfer在**多代GPU架构兼容性**和**量化推理支持**上的持续投入。通过kernel共享策略降低维护成本，同时扩展对TensorRT-LLM生态的兼容性（MxInt4、LoRA），巩固其作为LLM推理高性能后端的定位。性能优化和构建修复提升了实际部署体验，符合项目"为推理提供高性能GPU kernel"的核心目标。

## 详细提交记录

### [968fa04](https://github.com/flashinfer-ai/flashinfer/commit/968fa048e52269839e318cdeeff855c2a7b3fdef)

- **作者**: eigen
- **时间**: 2026-08-04T21:26:01Z
- **提交信息**: feat(cake_kda): share recurrent decode kernels across SM100 family (#4314)

> [!IMPORTANT]
> Follow-up to merged #4279. This PR is a single incremental
SM100-family
> target-consolidation commit based directly on upstream
`main@4433996e`.

## Description

Compile the frozen recurrent-KDA decode portfolio as `sm_100f` on CUDA
12.9+
and share it between CC 10.0 (B200/GB200) and CC 10.3 (B300/GB300). The
public
`backend="cake"` contract and all device split selectors remain
unchanged.

Two physical-target exceptions are deliberate:

- CUDA 12.8 B200 retains the exact `sm_100a` portfolio because `sm_100f`
is
  unavailable in that toolkit.
- GB300 retains exact `sm_103a` modules for the two direct-T1 variants.
A
repeated target-only A/B found a systematic approximately 2.1%
regression
  when those variants were compiled as `sm_100f`.

All 23 frozen generated CUDA bodies are byte-identical to #4279. CUDA
12.9+
B200 registers 23 family modules. CUDA 12.9+ GB300 registers the family
portfolio plus two exact direct-T1 modules; T2-T6 use the family
modules.

## Validation

Publication commit: `e2552d7b0671b6694564053d22f67a7f82ef023f` (tree
`d3312b2fbd8b52544f0a1ba6c9f1b8b318ca9aad`), based directly on upstream
`main@4433996e`. Its tree is byte-identical to ready commit `0c8212ad`
and to
the candidate validated on both GPUs.

| Gate | B200 | GB300 |
|---|---:|---:|
| Public decode GPU tests | 151/151 passed | 151/151 passed |
| Targeted CPU tests at publication commit | 194 passed, 20 skipped |
same commit |
| Pre-commit at publication commit | passed | same commit |

Strict CUPTI, cold-L2, balanced-process A/B below compares the final
family /
hybrid build with the exact-target implementation. Speedup is
`exact / family-or-hybrid`.

| GPU | T1 | T2 | T3 | T4 | T5 | T6 | 30-shape geomean |
|---|---:|---:|---:|---:|---:|---:|---:|
| B200 | 1.0043x | 1.0031x | 1.0029x | 0.9954x | 1.0003x | 1.0006x |
**1.0011x** |
| GB300 | 1.0015x | 0.9988x | 1.0138x | 1.0035x | 0.9998x | 0.9985x |
**1.0027x** |

GB300 T1 in this final table is exact `sm103a` on both sides; the row
verifies
that retaining the performance exception does not perturb public
dispatch.
The existing #4279/upstream and CAKE-internal baseline measurements
remain the
algorithm-level performance comparison; this A/B isolates
physical-target
consolidation.

Follow-up to merged #4279. Related to #4254.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added Flash-KDA decode support for SM103a and SM100-family targets,
including direct single-token variants.
- Added architecture-aware JIT and AOT module generation, loading,
caching, and dispatch.
- Added support for architecture-specific scheduling and value-split
policies.

- **Bug Fixes**
- Improved validation for GPU architecture and CUDA version
compatibility.
- Unsupported target and variant combinations are now rejected earlier.

- **Documentation**
- Updated recurrent KDA guidance with supported architectures,
compilation requirements, scheduling policies, and performance details.

- **Tests**
- Expanded coverage for target selection, routing, compatibility checks,
and numerical correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [68a85cd](https://github.com/flashinfer-ai/flashinfer/commit/68a85cd3b3b0c5042ab1e9b866450a97a0018795)

- **作者**: feih-nv
- **时间**: 2026-08-04T19:23:57Z
- **提交信息**: feat(moe): enable MxInt4 in unified API (#4320)

## 📌 Description

Enable TensorRT-LLM MxInt4 execution through FlashInfer’s unified MoE
API.

This change adds production BF16-to-MxInt4 weight preparation through
`TrtllmMxInt4Config.prepare_weights()`, including signed INT4 packing,
BF16 block scales, gated-activation row permutation, scale interleaving,
and BlockMajorK conversion.

It also adds and registers `TrtllmMxInt4RoutedRunner`, supporting:
- Packed precomputed routing
- MxInt4 `FromLogits` support with BF16 router logits
- Expert-parallel local expert offsets
- Unified MoELayer dispatch and autotuning
- CUDA graph capture and replay

The unified MoE fuzzer now includes an MxInt4 handler, a
quantization-aware reference, and curated packed and `FromLogits` seeds.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All relevant tests are passing.

### SM100

- Unified MxInt4 suite: 30 passed
- Curated unified MoE fuzzer seeds: 2 passed
- Existing flat routed regressions: 4 passed

### SM107

- Unified MxInt4 suite: 30 passed
- Curated unified MoE fuzzer seeds: 2 passed


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added TRTLLM MxInt4 support for unified Mixture-of-Experts layers.
* Added BF16 activation and packed INT4 weight preparation for supported
routed architectures.
* Added precomputed and in-kernel routing, autotuning, and CUDA graph
compatibility.
* Added validation for supported data types, shapes, devices, and weight
layouts.

* **Bug Fixes**
* Improved permutation cache accuracy by accounting for all relevant
configuration settings.

* **Tests**
* Expanded fuzz and integration coverage for MxInt4 quantization,
routing, validation, and execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c9d66fe](https://github.com/flashinfer-ai/flashinfer/commit/c9d66feb8f8acf8061046e445191bd0c772de550)

- **作者**: Alex Yang
- **时间**: 2026-08-04T15:55:11Z
- **提交信息**: Update CODEOWNERS for moe_ep and autotuner sections (#4332)

<!-- .github/pull_request_template.md -->

## 📌 Description

update code owner dir mapping for autotuner

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Updated code ownership assignments for MOE_EP, Mamba, and Autotuner
areas.
  * Expanded Mamba ownership coverage.
* Updated Autotuner ownership assignments and simplified coverage to
apply at the directory level.
  * Removed outdated ownership mappings for MOE_EP.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [4967994](https://github.com/flashinfer-ai/flashinfer/commit/496799463915347b3144faf93abdfec159742cd7)

- **作者**: Brayden Zhong
- **时间**: 2026-08-04T14:46:35Z
- **提交信息**: Fix the expert correction bias checking inconsistency in `trtllm_mxint4_block_scale_moe` (#3898)

This cast doesn't actually need to exist. it's already handled by the
routing method

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **Bug Fixes**
* Expanded routing-bias validation so supported MoE paths accept both
`bfloat16` and `float32` inputs.
* Improved compatibility checks for selected mixed-precision and
block-scale MoE variants while preserving existing dimensional and shape
validation.

* **Documentation**
* Clarified supported input dtypes, optional routing-bias handling,
block-scaling requirements, and `None` behavior across multiple MoE
APIs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [67f7637](https://github.com/flashinfer-ai/flashinfer/commit/67f76379a145f19793896394974e29e610cda912)

- **作者**: Barry Kang
- **时间**: 2026-08-04T07:17:59Z
- **提交信息**: perf: remove NVFP4 TMA input padding copy (#4210)

## 📌 Description

Remove the temporary padded input allocation and full-tensor copy from
the CuTe DSL NVFP4 TMA path. The TMA tensor map now describes the
physical `M` rows and relies on G2S TMA out-of-bounds zero fill for row
tiles that extend into the padded scale layout. The FP4 output remains
bounded by `M`, while padded scale rows are still explicitly zeroed.

This keeps the existing TMA pipeline and 128x4 scale layout while
eliminating the non-128-aligned `M` copy cliff.

### B200 performance

Configuration: NVIDIA B200, BF16 input, `K=4096`, 128x4 scale layout,
PDL enabled, eager/no CUDA Graph, cold L2, CUPTI timing. Each value is
the median of three runs with 20 warmups and 100 measured iterations per
run.

| M | Aligned to 128 | TMA + input copy (µs) | Vectorized (µs) | This PR
(µs) |
|---:|:---:|---:|---:|---:|
| 32283 | No | 212.446 | 62.399 | **59.248** |
| 32384 | Yes | 59.072 | 62.399 | **59.312** |
| 32386 | No | 213.054 | 62.367 | **59.151** |
| 32512 | Yes | 59.375 | 62.431 | **59.184** |
| 32621 | No | 213.581 | 62.031 | **59.423** |
| 32640 | Yes | 59.455 | 62.031 | **59.392** |
| 32733 | No | 213.902 | 62.080 | **59.407** |
| 32768 | Yes | 59.439 | 61.967 | **59.552** |

For non-aligned 32K shapes, this reduces API GPU time by 72.1%–72.2%
versus TMA with the padded input copy and is 4.2%–5.2% faster than the
vectorized path. For aligned shapes, it stays within ±0.41% of the
previous TMA path and is 3.9%–5.2% faster than vectorized. `M=6326/6400`
remains on the existing vectorized heuristic and is unaffected by this
TMA change.

Reproduction template:

```bash
FLASHINFER_NVFP4_QUANTIZE_USE_TMA=1 python3 benchmarks/flashinfer_benchmark.py   --routine nvfp4_quantize   --backends cute-dsl   --m 32283   --k 4096   --input_dtype bfloat16   --global_scale 1.0   --sf_layout 128x4   --sf_vec_size 16   --enable_pdl   --no_cuda_graph   --dry_run_iters 20   --num_iters 100   --refcheck   -vv
```

## 🔍 Related Issues

Related to #3905.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Relevant B200 validation is passing: FP16/BF16 partial- and
fully-OOB cross-path checks, nonzero-sentinel padding-scale checks, and
`compute-sanitizer --tool memcheck` (`ERROR SUMMARY: 0 errors`).

## Reviewer Notes

The TMA descriptor uses the physical `M`, but the kernel intentionally
continues through `padded_M` to initialize the scale layout. The focused
regression case uses `M=8193`, which produces one partial TMA tile
followed by seven fully-OOB tiles before the 128-row scale boundary.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved NVFP4 quantization for inputs whose row count requires
padding.
* Ensured out-of-bounds padded rows are automatically zero-filled during
TMA processing.
* Preserved correct quantization results and scale factors for valid
rows.

* **Tests**
* Added coverage for non-aligned row counts and verified zero values in
padded rows.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5116e2b](https://github.com/flashinfer-ai/flashinfer/commit/5116e2b359f55bbff5c0b5b420eed6dc0435601b)

- **作者**: Alex Yang
- **时间**: 2026-08-04T07:12:24Z
- **提交信息**: chore: drop unused <nvrtc.h> includes from three launchers (#4293)

## 📌 Description

Three launchers include `<nvrtc.h>` without referencing a single NVRTC
symbol. Each was
introduced by a single commit and appears to have been copied along with
code ported from
TRT-LLM / cuDNN rather than added for a symbol the file needs:

| File | Introduced by | Commit |
|---|---|---|
| `csrc/trtllm_fmha_kernel_launcher.cu` | #1051 — "[nvidia] Add
Blackwell FMHA decode kernel from TRT-LLM" | `9af6afe1` (2025-05-27) |
| `csrc/cudnn_sdpa_kernel_launcher.cu` | #1187 — "Feature/cudnn dynamic
cubin" | `ece99ccc` (2025-06-30) |
| `csrc/trtllm_fused_moe_kernel_launcher.cu` | #1212 — "feat: trtllm-gen
fp8 moe kernels" | `bd74e15c` (2025-07-10) |

In all three the include arrived as a pure `+#include <nvrtc.h>` with no
accompanying NVRTC
usage, and none has been used since.

The include is not harmless. `nvrtc.h` ships in `cuda-nvrtc-dev`, which
is missing from
some otherwise complete CUDA installs (several NGC / vLLM-derived
containers carry only the
NVRTC runtime). On those images the JIT build fails outright:

```
csrc/trtllm_fused_moe_kernel_launcher.cu:16:10: fatal error: nvrtc.h: No such file or directory
   16 | #include <nvrtc.h>
```

even though nothing in the translation unit needs NVRTC. I hit this
compiling the
trtllm-gen fused-MoE module on a B200 container and had to `sed` the
include out to get a
build.

`csrc/nv_internal/tensorrt_llm/deep_gemm/jit_utils.cuh` **keeps** its
include — it is the
one file that genuinely uses `nvrtcResult` / `NVRTC_SUCCESS` /
`nvrtcGetErrorString`.

Verification that the removals are safe:

```console
$ grep -cE "nvrtc[A-Za-z_]+|NVRTC_[A-Z_]+" csrc/cudnn_sdpa_kernel_launcher.cu \
      csrc/trtllm_fmha_kernel_launcher.cu csrc/trtllm_fused_moe_kernel_launcher.cu
0
0
0
$ grep -cE "nvrtc[A-Za-z_]+|NVRTC_[A-Z_]+" csrc/nv_internal/tensorrt_llm/deep_gemm/jit_utils.cuh
3
```

## 🔍 Related Issues

None filed, but this is the second time it has cost us. The same removal
was already made
locally as `c6c461ae` ("fix: remove unused nvrtc.h include from trtllm
launcher files") on a
`debug/4168-release-v0.6.16-test` branch while investigating #4168, and
never made it
upstream. That commit covered two of the three files;
`csrc/cudnn_sdpa_kernel_launcher.cu`
was missed. This PR upstreams the fix and completes it.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Include-only change with no functional effect; covered by the existing
build/CI.

## Reviewer Notes

Deletion-only. The single file that actually uses NVRTC is deliberately
untouched.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Chores**
  - Removed unused internal dependencies from GPU kernel components.
  - No user-facing functionality or public interfaces were changed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [6fb14ef](https://github.com/flashinfer-ai/flashinfer/commit/6fb14ef1d5115fb7398b0d46cc282779e23b8e88)

- **作者**: Sebastian Huang
- **时间**: 2026-08-04T07:02:23Z
- **提交信息**: feat(moe): enable BiasType::Mn (LoRA delta) for nvfp4/mxfp4 MoE (#3987)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds LoRA delta support to the FP4 block-scale MoE path (`NvFp4` /
`MxFp4xMxFp8` / `MxFp4xBf16`).

- **Launcher**: `trtllm_fp4_block_scale_routed_moe` takes
`gemm1_lora_delta`; picks `BiasType::Mn` when it's set. Static
`gemm1_bias` and the delta share one bias slot (mutually exclusive).
- **Wrapper**: for NvFp4, pre-divides the delta by `dequantScaleAb`
since the kernel folds that into `scaleC` and applies it to the bias.
- **Tests**: `test_moe_lora_delta` now covers the 3 FP4 modes

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

Extends `test_moe_lora_delta` to cover the three FP4 modes: `NvFp4`,
`MxFp4xMxFp8`, `MxFp4xBf16`.

Tested with:

```bash
pytest tests/moe/test_trtllm_gen_fused_moe.py::test_moe_lora_delta
```

## Reviewer Notes

None. 


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added LoRA-delta (GEMM1 bias-delta) support for FP4 routed MoE,
including optional GEMM1 activation outputs when applicable.
* Extended FP4 routed execution and valid-configuration handling to
accept GEMM1 bias/delta inputs.
* **Bug Fixes**
* Improved correctness for non-finalize execution by reliably returning
expert weights and aligning intermediate activation ordering/decoding
with reference behavior.
* **Tests**
* Expanded FP4 LoRA-delta coverage across additional FP4/MoE variants
and updated CUDA-graph and intermediate-output checks for routed
workflows.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3918
- **最后更新**: 2026-08-04T20:57:19Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Kaiqin Kong

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**功能新增**（`feat`），核心是引入对 MiniMax H3 模型的支持。

**2. 关键变更点与项目方向**  
- 新增 MiniMax H3 模型的集成，扩展了 FastVideo 支持的模型生态。  
- 与项目“快速、高效训练与推理”的目标一致，通过适配新架构提升工具链的通用性，覆盖更多用户场景。

**3. 对项目的影响与潜在意义**  
- 增强项目在视频生成领域的竞争力，吸引使用 MiniMax H3 的开发者。  
- 为后续优化（如针对该模型的显存/速度调优）奠定基础，可能推动社区贡献更多相关功能。

**4. 值得关注的技术点**  
- 模型适配涉及架构映射、权重加载及推理流程调整，需确保与现有框架兼容。  
- 可能包含针对 H3 的特定优化（如注意力机制或并行策略），值得后续查看代码细节。

**5. 对项目发展的影响**  
FastVideo 定位为高效视频生成工具，支持更多模型（如 MiniMax H3）可扩大用户基础，增强生态吸引力。此提交是持续扩展模型库的一步，有助于巩固其作为通用视频生成平台的地位，并可能催生更多基于 H3 的社区工作流。

**总结**：本次提交是功能扩展，通过支持 MiniMax H3 提升项目通用性，符合 FastVideo 构建开放、高效视频生成生态的长期方向。

## 详细提交记录

### [e8b0e4c](https://github.com/hao-ai-lab/FastVideo/commit/e8b0e4c61e58aeff33b0e331fc21a75ee99c49ce)

- **作者**: Kaiqin Kong
- **时间**: 2026-08-04T20:54:39Z
- **提交信息**: [feat] Add MiniMax H3 (#1674)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34230
- **最后更新**: 2026-08-04T16:10:40Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: jiqing-feng, sashakunitsyn, Sayak Paul

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **Bug修复**：Kandinsky 5 I2V（图像到视频）管线的条件注入逻辑修复
- **测试重构**：将`tests/others`目录迁移至`pytest`框架
- **测试适配**：为XPU硬件平台添加BNB 4-bit Flux Control LoRA测试的期望切片值

### 2. 关键变更点与项目方向的关系
- **Kandinsky 5修复**：修正了`Kandinsky5I2VPipeline.prepare_latents`中重复注入条件图像的问题。原实现将图像潜变量同时注入首帧和`visual_cond`通道，而参考实现仅注入首帧。这一修复使diffusers实现与官方参考对齐，提升了生成质量，符合项目“提供高质量、与官方实现一致的模型管线”的核心目标。
- **pytest迁移**：将测试基础设施从旧框架迁移至pytest，这是测试现代化的重要一步，有助于提升测试可维护性和可扩展性，与项目持续改进开发工具链的方向一致。
- **XPU测试适配**：为Intel XPU硬件添加特定期望值，体现了项目对多硬件平台（CPU/GPU/XPU）支持的承诺，扩大了用户覆盖面。

### 3. 对项目的影响和潜在意义
- **Kandinsky 5修复**直接影响使用I2V功能的用户，消除网格/视觉伪影，显著提升生成质量。该修复基于参考实现，降低了与官方行为偏差的风险，对模型可信度有积极影响。
- **pytest迁移**是长期技术债清理，虽然对用户无直接影响，但能降低后续测试编写和维护成本，加速开发迭代。
- **XPU适配**使Intel硬件用户获得更准确的测试验证，有助于在更多平台上提供一致体验。

### 4. 值得关注的技术点
- **条件注入机制**：修复揭示了多模态管线中条件信号注入的微妙性——同一条件被注入多个通道可能导致过度条件化（over-conditioning），这是生成质量下降的常见原因。
- **测试框架迁移策略**：提交中包含了“下载内核”功能的尝试与回退，展示了在迁移过程中对依赖管理的谨慎处理。
- **硬件特定测试值**：XPU切片值差异反映了不同硬件在数值精度上的细微差别，测试需要针对平台做适配。

### 5. 对项目发展的影响
结合README背景，diffusers作为HuggingFace核心的扩散模型库，致力于提供统一、可靠的模型实现。本次提交体现了三个发展方向：**一是追求实现与官方参考的一致性**（Kandinsky修复），确保模型行为可预期；**二是持续优化开发者体验**（pytest迁移），降低贡献门槛；**三是扩展硬件兼容性**（XPU支持），服务更广泛的用户群体。这些提交虽规模不大，但分别从产品质量、工程效率和平台覆盖三个维度巩固了项目的基础设施，属于稳健的渐进式改进，有助于维持diffusers在扩散模型生态中的领先地位。

## 详细提交记录

### [09514d4](https://github.com/huggingface/diffusers/commit/09514d4892ebc6d48ef24a868d9513963bc7e0ff)

- **作者**: sashakunitsyn
- **时间**: 2026-08-04T15:17:47Z
- **提交信息**: [Kandinsky 5] Fix I2V conditioning: don't inject the image latent into visual_cond channels (#14282)

Fix Kandinsky 5 I2V: don't duplicate image latent into visual_cond channels

Kandinsky5I2VPipeline.prepare_latents injected the conditioning image both as the
first latent frame and into the visual_cond channels; the reference implementation
(kandinskylab/kandinsky-5) only does the former. The duplicate over-conditions the
first frame and produces mesh/visual artifacts. Remove the redundant injection to
match the reference.

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [7aa57aa](https://github.com/huggingface/diffusers/commit/7aa57aafffb6e1be179a9d12521583650aad63ae)

- **作者**: Sayak Paul
- **时间**: 2026-08-04T15:03:21Z
- **提交信息**: [tests] Migrate `tests/others` to `pytest`. (#14299)

* download kernels when users request for it.

* migrate tests/others to pytest

* Revert "download kernels when users request for it."

This reverts commit 6fe34ade6b6412e694d83a8dd3aee1550a9ebbab.

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [c79e352](https://github.com/huggingface/diffusers/commit/c79e352363744c3e6a7bd1c1e832d4b5aea935d8)

- **作者**: jiqing-feng
- **时间**: 2026-08-04T13:36:15Z
- **提交信息**: Add XPU expected slice for `SlowBnb4BitFluxControlWithLoraTests::test_lora_loading` (#14202)

* fix xpu slice

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

* complete comment

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

---------

Signed-off-by: jiqing-feng <jiqing.feng@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
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


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12808
- **最后更新**: 2026-08-04T15:07:24Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Hong Zhang

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交包含**版本升级**、**代码重构**和**Bug修复**三类变更，无新增功能或文档更新。

### 2. 关键变更点及与项目方向的关系
- **版本升级至2.1.0**：标志着项目进入新阶段，通常伴随功能稳定和API兼容性承诺，与DiffSynth-Studio作为开源视频生成工具持续迭代的方向一致。
- **重构minimax prompt embedder**：优化了文本提示编码器的内部实现，属于核心推理链路的关键组件。重构而非重写，表明在保持接口兼容的前提下提升代码质量和可维护性，符合项目“易用性”定位。
- **修复minimax audio VAE磁盘卸载问题**：解决视频生成中音频编解码器在显存不足时无法正确卸载到磁盘的缺陷，直接提升长视频或高分辨率场景下的稳定性。

### 3. 对项目的影响和潜在意义
- 版本号提升至2.1.0暗示可能有新特性或行为变化，对下游用户和依赖该库的生态项目有兼容性影响。
- prompt embedder重构可能带来推理速度或内存占用的细微改善，但主要意义在于降低后续维护成本，为未来扩展新模型或提示词策略奠定基础。
- audio VAE修复直接改善用户体验，尤其是处理长视频或资源受限环境时，减少因显存溢出导致的生成失败，增强项目在专业创作场景的可靠性。

### 4. 值得关注的技术点
- **磁盘卸载（disk offloading）机制**：这是大模型推理中常见的显存优化手段，修复表明项目在资源管理上持续打磨，值得关注其实现细节。
- **prompt embedder的模块化设计**：重构后可能更易替换或扩展不同模型的文本编码器，为支持更多视频生成模型（如不同厂商的API）提供便利。
- 提交信息中“tmp commit”到“refactor”的演进，显示开发流程中先快速验证再整理代码的实践。

### 5. 对项目发展的影响
DiffSynth-Studio定位为集成多种视频生成技术的统一工具库（从README的logo和trendshift可见其社区热度）。本次提交：
- **巩固稳定性**：修复audio VAE问题，提升多模态（视频+音频）生成的整体可靠性，这是区别于纯视频生成工具的关键优势。
- **强化可扩展性**：重构prompt embedder为未来接入更多模型（如不同厂商的文本编码器）铺路，符合项目“多模型支持”的生态战略。
- **传递成熟信号**：版本号提升至2.1.0且伴随重构和修复，表明项目进入稳定迭代期，有助于吸引更多生产环境用户。

总体而言，本次提交是典型的“内部优化+稳定性修复”组合，虽无新功能，但对提升项目专业度和长期可维护性有积极意义，为后续功能开发打下更扎实的基础。

## 详细提交记录

### [0ad8509](https://github.com/modelscope/DiffSynth-Studio/commit/0ad850953156c028c6334ea8c17c50032a1ef169)

- **作者**: Hong Zhang
- **时间**: 2026-08-04T08:18:17Z
- **提交信息**: update version to 2.1.0 (#1562)

### [d48d64e](https://github.com/modelscope/DiffSynth-Studio/commit/d48d64e6ba94e16c41a865472008c28fca0e1fbf)

- **作者**: Hong Zhang
- **时间**: 2026-08-04T08:00:02Z
- **提交信息**: Refactor minimax prompt embedder

* tmp commit

* refactr prompt embedder

### [6f13b82](https://github.com/modelscope/DiffSynth-Studio/commit/6f13b8227e912880be7b140aaef7030fec770dee)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-04T07:31:08Z
- **提交信息**: fix minimax audio vae disk offloading issues (#1560)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31279
- **最后更新**: 2026-08-04T22:13:15Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 16
- **主要提交者**: Lu Fang, Sugar920, Kan Wu

## AI分析总结

# sglang 仓库提交分析报告

## 一、主要更新类型

本批29个提交涵盖**性能优化**（占比最高）、**新硬件支持**、**新模型适配**、**Bug修复**、**CI/CD改进**、**代码重构**和**可观测性增强**。其中AMD/NPU/XPU等异构硬件适配、扩散模型加速、KV缓存优化是核心主题。

## 二、关键变更点与项目方向

**1. 硬件生态扩展**：多个提交针对AMD（gfx950 FP8 FMHA、MiniMax-M3 MI35x测试）、NPU（迁移至a3-560T）、XPU（CI稳定性）进行适配，体现项目“多硬件后端”战略。Bump mori至最新版、启用aiter hd256 FP8 prefill等，持续强化AMD平台竞争力。

**2. 扩散模型加速**：两个提交分别融合DiT FFN tanh-GELU到GEMM（H200上12.36→12.05秒）和实现FLUX.2 VAE解码器快速路径（1024²从97.6→29.2ms），通过cublasLt epilogue和quality=high选项，显著提升图像生成性能，扩展sglang在扩散模型领域的覆盖。

**3. KV缓存与显存管理**：多个提交围绕HiCache分层缓存（L2缓存+写回策略、post-capture KV sizing、DP注意力支持）展开，优化KV缓存预留逻辑和日志清晰度，提升长序列场景下的显存效率。

**4. 新模型支持**：支持Kimi k3和Laguna模型（含per-layer LoRA hidden-dim分辨率），新增sglang-mm服务器视觉管线核心（Qwen VL），扩展模型生态。

**5. 架构重构**：将chat template验证移出ServerArgs dispatcher、内联_gc设置、自定义decode graph runners，简化架构、提升可维护性。

## 三、项目影响与意义

- **性能提升**：扩散模型加速和KV缓存优化直接降低推理延迟，增强产品竞争力
- **硬件覆盖**：AMD/NPU/XPU适配扩大部署场景，吸引更多企业用户
- **可观测性增强**：新增启动、内存、混合SWA诊断及tokenizer流式指标，便于生产环境监控
- **CI/CD健壮性**：精简B200测试、稳定XPU CI、修复rust-ext-build venv问题，提升开发效率

## 四、值得关注的技术点

- **cublasLt epilogue融合**：将激活函数融合进GEMM，减少kernel启动开销
- **L2分层缓存写回策略**：优化多级缓存一致性
- **DP注意力下的post-capture KV sizing**：解决分布式注意力与CUDA Graph的兼容问题
- **自定义decode graph runners**：提供更灵活的CUDA Graph扩展机制
- **FP8 prefill FMHA**：利用AMD gfx950硬件特性提升预填充速度

## 五、对项目发展的影响

sglang正从单一LLM推理引擎向**多模态、多硬件、多模型**的综合推理平台演进。扩散模型加速和视觉管线建设表明其向图像生成领域扩展；Kimi/Laguna等新模型支持紧跟业界前沿；AMD/NPU/XPU适配则瞄准企业级异构部署需求。KV缓存优化和可观测性增强巩固其在高性能推理领域的领先地位。整体来看，这些提交体现了sglang“性能优先、生态开放”的发展策略，有望吸引更广泛的用户和贡献者，推动项目向生产级推理基础设施迈进。

## 详细提交记录

### [b327d76](https://github.com/sgl-project/sglang/commit/b327d76682f34ab2c185f357e153970901259278)

- **作者**: Zhaoyi Li
- **时间**: 2026-08-04T22:12:40Z
- **提交信息**: [AMD] Bump mori to latest in sglang (#33462)

### [c8822fd](https://github.com/sgl-project/sglang/commit/c8822fd990c9fef449b0b09ba196f8d6f898bed3)

- **作者**: cctry
- **时间**: 2026-08-04T22:06:11Z
- **提交信息**: Clarify post-capture KV reservation logs (#33598)

### [19d3f86](https://github.com/sgl-project/sglang/commit/19d3f86895f43eb23b71a707726810cd700f947d)

- **作者**: Filip
- **时间**: 2026-08-04T21:48:05Z
- **提交信息**: [LoRA] Laguna: per-layer LoRA hidden-dim resolution for packed attention (#30298)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [a9c3b55](https://github.com/sgl-project/sglang/commit/a9c3b5543550c9c38dd503bfe47df99fe1295dd6)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-04T21:45:47Z
- **提交信息**: [Refactor] Keep chat template validation out of ServerArgs dispatcher (#33392)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [e510dc5](https://github.com/sgl-project/sglang/commit/e510dc58ba8fc1fa22d776fc0bde7a8b9a9ecbca)

- **作者**: Jimmy Shong
- **时间**: 2026-08-04T21:10:19Z
- **提交信息**: Add @Jiminator as codeowner for Laguna model and config (#33472)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [34af3ff](https://github.com/sgl-project/sglang/commit/34af3ff38655e93533813f2e63b938ed47e47ff5)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T20:23:08Z
- **提交信息**: Allow optimistic prefill with L2 hierarchical cache and write-back policy (#33545)

Co-authored-by: cctry <cctry@meta.com>

### [abddb1c](https://github.com/sgl-project/sglang/commit/abddb1c7e9d61ddddeaf016d885c2f20aab426e8)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-04T20:22:49Z
- **提交信息**: [Kimi] Support kimi-k3 (#32541)

Co-authored-by: DarkSharpness <76582120+DarkSharpness@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>
Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Ziyi Xu <ziyi.xu@radixark.ai>
Co-authored-by: Zijie Xia <37504505+zijiexia@users.noreply.github.com>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: zhangxiaohao <1024393531@qq.com>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>
Co-authored-by: Julien Lin <jullin@nvidia.com>
Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Thomas Wang <1am9trash@gmail.com>
Co-authored-by: RolaoDenthu <xinyisong0111@gmail.com>
Co-authored-by: pigeonsoup <32922982+pigeonsoup@users.noreply.github.com>
Co-authored-by: HaiShaw <hixiao@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Pranjal Shankhdhar <pranjal.ssh@gmail.com>
Co-authored-by: Lee Nau <lee.nau@gmail.com>
Co-authored-by: HMING <126185151+Hearum@users.noreply.github.com>
Co-authored-by: elvischenv <219235043+elvischenv@users.noreply.github.com>
Co-authored-by: Byron Hsu <byronhsu1230@gmail.com>
Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: Xinyi Song <86638975+RolaoDenthu@users.noreply.github.com>
Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>
Co-authored-by: BBuf <xiaoyu.zhang@radixark.ai>
Co-authored-by: Hanming Lu <hanminglu@meta.com>
Co-authored-by: Xinyi Song <xinyis10@illinois.edu>

### [0753663](https://github.com/sgl-project/sglang/commit/0753663b8ea7adf235c71074e7e10f3bbf2dedf9)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-04T20:22:00Z
- **提交信息**: [CI] Trim redundant B200 test registrations (#33586)

### [aa06433](https://github.com/sgl-project/sglang/commit/aa064337095c6091280e89f6981edde86cc952c6)

- **作者**: Xingyu Liu
- **时间**: 2026-08-04T19:54:04Z
- **提交信息**: Avoid TRTLLM prefill output copy (#33306)

### [38dc2d6](https://github.com/sgl-project/sglang/commit/38dc2d6cf8a69a4ff1742fe445516259ab60145f)

- **作者**: Lu Fang
- **时间**: 2026-08-04T19:53:52Z
- **提交信息**: [metrics] Split tokenizer request metrics by stream (#32734)

Co-authored-by: wpc <wpc@devvm23443.cco0.facebook.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [4794b40](https://github.com/sgl-project/sglang/commit/4794b401d51ff47049ec0d9f94e15995bc6d6571)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T19:50:09Z
- **提交信息**: [Observability] Add startup, memory, and hybrid SWA diagnostics (#33375)

### [5081c06](https://github.com/sgl-project/sglang/commit/5081c063c0105363ac01acf051fd94dd44ddd915)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T19:49:17Z
- **提交信息**: fix(metrics): clear forward occupancy on idle (#33562)

Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>

### [dea2be5](https://github.com/sgl-project/sglang/commit/dea2be5ae3eb44988f54f414ffc68a0ca8a10b10)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T19:48:56Z
- **提交信息**: [CUDA Graph] Allow custom decode graph runners (#33553)

Co-authored-by: Itai Gat <itaigat.mail@gmail.com>

### [e76d0ac](https://github.com/sgl-project/sglang/commit/e76d0acdc923d992bbda20d4b2bc51db9ac314a7)

- **作者**: Sugar920
- **时间**: 2026-08-04T17:17:58Z
- **提交信息**: migrate NPU PR/nightly test cases to a3-560T (#33346)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [95d0e57](https://github.com/sgl-project/sglang/commit/95d0e57e838b627d77031082c91095c200037fe5)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-04T15:49:43Z
- **提交信息**: [diffusion] Fuse DiT FFN tanh-GELU into up-proj GEMM (cublasLt epilogue) behind quality=high (Qwen-Image 1024^2 denoise 12.36 -> 12.05 s on H200) (#33536)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [0d0c7d8](https://github.com/sgl-project/sglang/commit/0d0c7d853fe5afadaa0bfbb16464117a2828ba6c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-04T15:48:19Z
- **提交信息**: [diffusion] FLUX.2 VAE decoder fast path behind quality=high (H200: 1024^2 97.6->29.2 ms, 2048^2 437.2->168.5 ms) (#33451)

### [7adf2f4](https://github.com/sgl-project/sglang/commit/7adf2f4a9a4389d1c021a2caf128cf7e2f4adb35)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T14:31:56Z
- **提交信息**: Inline _set_gc into _set_envs_and_config (#33538)

### [d257b58](https://github.com/sgl-project/sglang/commit/d257b58e67193780ff8a59ab54b48219b9dc28d2)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T12:55:35Z
- **提交信息**: [Router] Report accelerator count in /v1/loads (#33548)

Co-authored-by: Yinghai Lu <yinghai@meta.com>

### [8f2a3ad](https://github.com/sgl-project/sglang/commit/8f2a3ad6d7d68c58ae65b61a75bb2115449addca)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T11:21:36Z
- **提交信息**: [mem_cache] Label HiCache host pools and clarify post-capture KV sizing logs (#33445)

### [723c277](https://github.com/sgl-project/sglang/commit/723c2776401987cba3cfee25830db50f3964b83f)

- **作者**: jacky.cheng
- **时间**: 2026-08-04T09:40:33Z
- **提交信息**: [AMD] [Fix] Enable aiter hd256 FP8 prefill FMHA on gfx950 (#33399)

### [5e6c37f](https://github.com/sgl-project/sglang/commit/5e6c37f2b4c68d3d86024252d3849a119165c5d1)

- **作者**: Xingyu Liu
- **时间**: 2026-08-04T09:23:34Z
- **提交信息**: [cuda_graph] Gate breakable-CG capture_inputs retention to DP-gather paths (#32678)

Signed-off-by: xingyuliu <charlotteliu12x@gmail.com>

### [b57721c](https://github.com/sgl-project/sglang/commit/b57721ccf79b2b6fb8c159e1d94c2f505204c715)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T09:20:24Z
- **提交信息**: Enable post-capture KV sizing with DP attention (#33427)

Co-authored-by: cctry <cctry@meta.com>
Co-authored-by: cctry <cctry@fb.com>

### [16d3b11](https://github.com/sgl-project/sglang/commit/16d3b118a20e70f7bb93b57c9e6d532d6a6fece6)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-04T09:19:56Z
- **提交信息**: Reduce startup log noise and fix Dynamo / CUDA-graph edge cases (#33428)

### [b6d548a](https://github.com/sgl-project/sglang/commit/b6d548afd7c2db64cccbbb82feebcb5533099677)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-04T09:01:39Z
- **提交信息**: [Fix] Resolve VLM test image placeholders from the model's own chat template (#33509)

### [26a5427](https://github.com/sgl-project/sglang/commit/26a542722f83f4740b8b513fc47fd5c58501f051)

- **作者**: Kan Wu
- **时间**: 2026-08-04T08:56:16Z
- **提交信息**: [CI] Replace the rust-ext-build venv instead of failing when it exists (#33512)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [eaf5c29](https://github.com/sgl-project/sglang/commit/eaf5c29cc5a1874a34c4fe47afb7e5b15e89d6f9)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-04T08:55:06Z
- **提交信息**: [AMD] Enable block-fp8 + quick INT4 all-reduce in MiniMax-M3 MI35x nightly Test (#33402)

### [53804d6](https://github.com/sgl-project/sglang/commit/53804d609cb3d7e1a3dfaed0c3e9557b7749767d)

- **作者**: ashwini rathi
- **时间**: 2026-08-04T08:28:52Z
- **提交信息**: [CI][XPU] Stabilize XPU CI: pin UMD/IGC, retry infra flakes, right-size EAGLE3 (#32438)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [17d1908](https://github.com/sgl-project/sglang/commit/17d19081d9517e7479ae3f8cf58efe06d6d0f77e)

- **作者**: Kan Wu
- **时间**: 2026-08-04T07:47:00Z
- **提交信息**: [mm] sglang-mm: server vision pipeline core (fetch/driver/pipeline) + Qwen VL (#32364)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [154f0ac](https://github.com/sgl-project/sglang/commit/154f0ac662e7f7465a928a8da3c63d788742c0e4)

- **作者**: Vladislav Nosivskoy
- **时间**: 2026-08-04T07:35:57Z
- **提交信息**: Fix DSpark and DP/EP (#33098)

Signed-off-by: Vladislav Nosivskoy <vladnosiv@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
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


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88185
- **最后更新**: 2026-08-04T22:28:27Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 24
- **主要提交者**: Kevin H. Luu, Wentao Ye, Harry Mellor

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批提交涵盖**性能优化**（约40%）、**新功能支持**（约30%）、**Bug修复**（约20%）及**基础设施/文档改进**（约10%）。核心聚焦于Kimi K3/K2.5系列模型的推理优化、MoE架构增强及多模态能力扩展。

### 2. 关键变更点与项目方向

- **Kimi K3专项优化**：多项提交针对Kimi K3模型，包括SiTU激活函数支持、共享专家分片（节省16.98 GiB/GPU）、AttnRes状态融合及工具渲染对齐，体现对前沿模型生态的快速适配能力。
- **MoE架构深化**：共享专家部分加法融合进Lamport集合通信、EP加载时过滤打包专家权重，提升MoE推理效率与正确性。
- **内核级优化**：新增CuTeDSL融合查询内核（SM100）、Flashinfer Mamba SSU算法选择、无权重RMSNorm按声明宽度融合，持续强化底层计算能力。
- **模型运行器v2**：E/P/D分离支持（预填充/解码/分块）是架构级改进，为异构部署和资源调度奠定基础。
- **多模态与MLA**：ViT全CUDA图支持、Transformers后端MLA支持、多模态图像推理（Rust前端gRPC），扩展模型类型覆盖。

### 3. 项目影响与潜在意义

- **性能领先性**：通过内核融合、内存优化和通信优化，巩固vLLM在LLM推理性能上的优势地位。
- **模型生态扩展**：对Kimi、DeepSeek V4、GLM-5.2等新模型的快速支持，增强对最新模型架构的兼容性。
- **架构演进**：Model Runner v2的E/P/D分离和Rust前端gRPC多模态支持，为未来可扩展性和异构部署铺路。

### 4. 值得关注的技术点

- **CuTeDSL内核**：针对SM100的融合查询内核，代表对NVIDIA下一代硬件的提前适配。
- **共享专家分片**：非mega场景下通过分片节省大量显存，是MoE推理内存优化的实用方案。
- **E/P/D分离**：将预填充、解码、分块阶段解耦，可能改变vLLM的资源调度模型。
- **CPU线程管理**：显式管理torch CPU线程，提升多worker场景下的资源利用效率。

### 5. 对项目发展的影响

vLLM正从“快速LLM服务”向**全栈推理优化平台**演进：内核级优化保持性能领先，模型适配覆盖最新架构，架构重构（Model Runner v2、Rust前端）提升可扩展性，多模态支持拓展应用边界。这些提交体现了vLLM在**性能、兼容性、架构前瞻性**三方面的持续投入，巩固其作为LLM推理基础设施的核心地位。

## 详细提交记录

### [3756bf1](https://github.com/vllm-project/vllm/commit/3756bf1e2ba0909500fbe77e03fe02eafb7f7080)

- **作者**: xiaozhoupy
- **时间**: 2026-08-04T22:23:06Z
- **提交信息**: [Kernel][SM100] Add a CuTeDSL fused query kernel (#49792)

Signed-off-by: Peiyuan Zhou <peiyuanzhou1994@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c687c1a](https://github.com/vllm-project/vllm/commit/c687c1abb8dc04bd224c7d98d520e30953400b86)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-04T21:15:27Z
- **提交信息**: [ci] Update CI notify workflow with PR write permissions (#51079)

Signed-off-by: Kevin H. Luu <khluu000@gmail.com>

### [a5149b2](https://github.com/vllm-project/vllm/commit/a5149b2feeb74c15990dafb1d8bf16cdb98616e4)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-04T21:13:59Z
- **提交信息**: [CI] Stabilize GLM-5.2 PCP evaluation (#51015)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [05b7876](https://github.com/vllm-project/vllm/commit/05b7876f50391d5ee5062bf2605d1f33f200272d)

- **作者**: Julian Huang
- **时间**: 2026-08-04T19:39:18Z
- **提交信息**: [MoE][Humming] Support SiTU activation for Kimi-K3 (#50510)

Signed-off-by: 墨楼 <huangzhilin.hzl@antgroup.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [edbc496](https://github.com/vllm-project/vllm/commit/edbc4969a76b25c531f7b9bb16b79984e65ef023)

- **作者**: Canlin Guo
- **时间**: 2026-08-04T18:41:35Z
- **提交信息**: [Kernel][Inkling] Fuse shared-expert partial addition into the Lamport collective (#50697)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [8ae8337](https://github.com/vllm-project/vllm/commit/8ae8337ffa6eed0823b0b827618090937512d503)

- **作者**: NVShreyas
- **时间**: 2026-08-04T18:05:40Z
- **提交信息**: [Spec Decode] Enable fused non-causal TokenSpeed MLA for DSpark (#50911)

Signed-off-by: Shreyas Misra <shreyasm@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [d31de3c](https://github.com/vllm-project/vllm/commit/d31de3c421c0281a959ac1a3cbe1a7f354bae179)

- **作者**: Wentao Ye
- **时间**: 2026-08-04T18:00:44Z
- **提交信息**: [Kimi K3 Perf] option to shard the shared expert for non mega case, 16.98 GiB memory/GPU saved (#50912)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7cab436](https://github.com/vllm-project/vllm/commit/7cab4368f22271dd562e3cef1d59232ebf07e8fb)

- **作者**: Linkun
- **时间**: 2026-08-04T17:15:56Z
- **提交信息**: [MM][CG] Support ViT full CUDA graph for Kimi-K2.5 (#50929)

Signed-off-by: lkchen <anthropic@lkchen.net>
Co-authored-by: lkchen <anthropic@lkchen.net>

### [7635a90](https://github.com/vllm-project/vllm/commit/7635a9002baecca64909dbcf8b1d461d26fb879d)

- **作者**: Nick Hill
- **时间**: 2026-08-04T17:06:38Z
- **提交信息**: [Core] Explicitly manage torch CPU threads in workers (#49919)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [52c0e3c](https://github.com/vllm-project/vllm/commit/52c0e3cb08b8178829e1f2db4ac90e9bb98c8a5f)

- **作者**: amitz-nv
- **时间**: 2026-08-04T16:40:23Z
- **提交信息**: [Kernel] Add support for Flashinfer Mamba SSU algorithm selection (#50157)

Signed-off-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7ac2ec7](https://github.com/vllm-project/vllm/commit/7ac2ec758208a27bbe0c4155a136969463e8e6c8)

- **作者**: yinfengLiu
- **时间**: 2026-08-04T16:32:13Z
- **提交信息**: [Kimi-K3][AMD] Fuse AttnRes state updates and norms (#50593)

Signed-off-by: Liuyinfeng01 <199041580+LiuYinfeng01@users.noreply.github.com>
Co-authored-by: Liuyinfeng01 <199041580+LiuYinfeng01@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7153fd7](https://github.com/vllm-project/vllm/commit/7153fd70f6128c85b0f670f082634174c9b38e2e)

- **作者**: aoshen02
- **时间**: 2026-08-04T16:32:03Z
- **提交信息**: [Bugfix][MoE] Filter packed expert weights during EP loading (#49558)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>

### [166f4e2](https://github.com/vllm-project/vllm/commit/166f4e2dc3a6ed1dfc3641611c9a07d8f0e87f9c)

- **作者**: Anuj Bolewar
- **时间**: 2026-08-04T16:03:09Z
- **提交信息**: fix: fuse weightless RMSNorms at their declared width (#50867)

Signed-off-by: Anuj Bolewar <anujbolewar@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Anuj Bolewar <anujbolewar@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4f819f8](https://github.com/vllm-project/vllm/commit/4f819f801b7702e39d9588cc9f2ecd28560b31f5)

- **作者**: Wentao Ye
- **时间**: 2026-08-04T15:52:23Z
- **提交信息**: [Model Runner v2] E/P/D disaggregation support (#38390)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [7743486](https://github.com/vllm-project/vllm/commit/77434861904a9f01ea4818fe9f0c7b2a5c05686e)

- **作者**: Bugen Zhao
- **时间**: 2026-08-04T15:51:32Z
- **提交信息**: [Frontend] DeepSeek V4 0731 reasoning effort prompts & mappings (#50580)

### [f9c74b4](https://github.com/vllm-project/vllm/commit/f9c74b4b9c25c202cb84e0e9908b82a503a8c7c4)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-04T15:20:51Z
- **提交信息**: [Mamba] enable prefix cache by default (#50991)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7b50d2c](https://github.com/vllm-project/vllm/commit/7b50d2c0bcee44ad89ee7ec75377560ed37915e3)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-04T14:56:54Z
- **提交信息**: [Misc] Avoid importing `nixl_ep` on every `vllm serve` config (#50879)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [122b3d4](https://github.com/vllm-project/vllm/commit/122b3d46b674f8b005a7c9902e27cf3b37b109ec)

- **作者**: Harjoth Khara
- **时间**: 2026-08-04T14:56:33Z
- **提交信息**: [Bugfix][CPU] Fix macOS build: std::sqrt is not constexpr under libc++ (#50915)

Signed-off-by: harjoth <harjoth.khara@gmail.com>

### [199644d](https://github.com/vllm-project/vllm/commit/199644d410dbfd94255d6b0cde08479858032266)

- **作者**: yimdev
- **时间**: 2026-08-04T13:59:33Z
- **提交信息**: [Bugfix][Attention] Guard sparse MLA masked MHA workspace (#50906)

Signed-off-by: yimdev <5779256+yimdev@users.noreply.github.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [7c40d61](https://github.com/vllm-project/vllm/commit/7c40d61eaf6bdd80bb493cf94032efbbe0ed0ee4)

- **作者**: Michał Ganczarenko
- **时间**: 2026-08-04T13:34:58Z
- **提交信息**: [Bugfix] Flatten >2D multimodal embeddings, not just 3D (#50250)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>

### [5f2ee2f](https://github.com/vllm-project/vllm/commit/5f2ee2fa8c59d9f9cddd07c79806e6418b0d841a)

- **作者**: Tanmay Dixit
- **时间**: 2026-08-04T12:53:32Z
- **提交信息**: [Bugfix][Core] Log KV cache capacity after block-size resolution (#50462)

Signed-off-by: Tanmay Dixit <22117787+tandixit95@users.noreply.github.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Tanmay Dixit <22117787+tandixit95@users.noreply.github.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [5789897](https://github.com/vllm-project/vllm/commit/5789897aa40fbab6bdfcffaa9e83da64939286fb)

- **作者**: Andrii Skliar
- **时间**: 2026-08-04T12:52:53Z
- **提交信息**: [Spec Decode] Add top-k DSpark Markov projection (#49969)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

### [1eb3694](https://github.com/vllm-project/vllm/commit/1eb3694521a67446ae23ce1e6dd04093e944a08e)

- **作者**: Harry Mellor
- **时间**: 2026-08-04T12:29:04Z
- **提交信息**: [Docs] Fix two docs build warnings (#51014)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [59b2fdf](https://github.com/vllm-project/vllm/commit/59b2fdfc4e237794c2b26f0781054ced73f5b8df)

- **作者**: Harry Mellor
- **时间**: 2026-08-04T12:24:11Z
- **提交信息**: Support MLA properly in the Transformers modeling backend (#48250)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [24c939c](https://github.com/vllm-project/vllm/commit/24c939c47df59d0d3e9af2fe63046e21e65b5924)

- **作者**: Yan Ma
- **时间**: 2026-08-04T11:53:28Z
- **提交信息**: [XPU] fix collecting oneccl version info (#47104)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [6a9fdf0](https://github.com/vllm-project/vllm/commit/6a9fdf0dc75844de3fff993c32e6f2a35f6fbf0d)

- **作者**: Lazurite
- **时间**: 2026-08-04T11:39:39Z
- **提交信息**: [Bugfix] Resolve seq-cls `num_labels` from the top-level config for multimodal checkpoints (#50950)

Signed-off-by: Lazurite <43494437+Rapisurazurite@users.noreply.github.com>

### [a1657a0](https://github.com/vllm-project/vllm/commit/a1657a0235a77ce85f8d348c83ff4adb29918b71)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-04T10:06:04Z
- **提交信息**: [Bugfix][Build] Fix DeepGEMM CUDA 12.9 FP8 header visibility (#51003)

Signed-off-by: khluu <khluu000@gmail.com>

### [e98a877](https://github.com/vllm-project/vllm/commit/e98a8774cba6f518a8de4433801cc32323a46071)

- **作者**: Connor Carpenter
- **时间**: 2026-08-04T09:34:31Z
- **提交信息**: [Rust Frontend][gRPC] Add multimodal image inference (#50368)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [0b1c151](https://github.com/vllm-project/vllm/commit/0b1c151cbcacd12e207f2a91e4ca9f5b6961ec8a)

- **作者**: Bugen Zhao
- **时间**: 2026-08-04T08:03:46Z
- **提交信息**: [Rust Frontend] Align tool rendering for Kimi K3 (#50540)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-05
**监控日期**: 2026-08-04
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5847
- **最后更新**: 2026-08-04T22:22:17Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: ruirui(rein) yang, Mu GuanLin, NATURE

## AI分析总结

# vllm-omni 昨日提交分析

## 主要更新类型

本次提交涵盖**Bug修复**（3项）、**性能优化**（2项）、**重构**（2项）、**功能新增**（1项）和**前端集成**（1项），整体呈现多维度推进态势。

## 关键变更点

1. **多模态位置编码修复**：修复Bagel模型中CFG位置ID拼接问题，直接影响多模态RoPE的正确性，对视觉-语言模型的推理质量至关重要。
2. **视频加载器统一重构**：改用vLLM标准视频加载器处理视频参考解码，消除重复实现，提升代码复用性和维护性。
3. **Qwen3-TTS性能优化**：在代码预测器中融合QKV和gate_up投影，减少内核调用次数，提升推理效率。该提交曾被回滚后重新合入，说明团队在性能与稳定性间进行了权衡。
4. **KV传输优化**：为Hunyuan/Bagel模型避免对仅发送KV的节点使用payload连接器，减少不必要的数据传输开销。
5. **MiniMax H3 FP8支持**：新增在线FP8量化支持，降低显存占用并提升推理速度，同时配套ComfyUI前端集成，降低用户使用门槛。
6. **调度器架构重构**：移除重复的AR/generation调度器管道，建立显式共享生命周期契约，为后续调度器统一演进奠定基础。

## 对项目的影响与意义

- **性能与效率提升**：TTS投影融合和KV传输优化直接降低推理延迟和资源消耗，符合项目“fast and cheap”的核心定位。
- **多模态能力增强**：视频加载器统一和位置编码修复提升了多模态处理的正确性和一致性，巩固项目在omni-modality领域的竞争力。
- **生态扩展**：MiniMax H3的FP8支持和ComfyUI集成，使项目能服务更广泛的用户群体，降低专业使用门槛。
- **架构健康度改善**：调度器重构和视频加载器统一是长期技术债清理，为未来功能扩展提供更稳固的基础。

## 值得关注的技术点

- **FP8在线量化**：在保持精度的同时显著降低显存需求，是当前大模型部署的热门方向。
- **调度器生命周期契约**：显式化共享生命周期是复杂系统设计的重要实践，值得深入理解其设计思路。
- **QKV融合的权衡**：该优化被回滚后重新合入，提示性能优化需兼顾稳定性，团队在CI保障上可能加强了验证。

## 对项目发展的影响

这些提交体现了vllm-omni“**易用、快速、低成本**”的核心理念：通过性能优化和FP8支持降低成本，通过ComfyUI集成提升易用性，通过架构重构保障长期可维护性。项目正从“功能可用”向“性能卓越、生态完善”阶段迈进，多模态支持与推理效率的双轮驱动将吸引更多开发者和企业用户，巩固其在omni-modality serving领域的领先地位。

## 详细提交记录

### [c9f2e5a](https://github.com/vllm-project/vllm-omni/commit/c9f2e5ad94032b8f2493ca829560efb607e26b79)

- **作者**: Atharv Arun Chivate
- **时间**: 2026-08-04T17:53:59Z
- **提交信息**: fix(bagel): correct CFG position ID concatenation for multimodal RoPE (#5775)

Signed-off-by: atharv0o <missionblood2@gmail.com>

### [fbea788](https://github.com/vllm-project/vllm-omni/commit/fbea7886682e332c0450c5e4d0c75b330b661166)

- **作者**: Nick Cao
- **时间**: 2026-08-04T17:49:41Z
- **提交信息**: [Refactor] Use vLLM video loader for video reference decoding (#5085)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [78c144f](https://github.com/vllm-project/vllm-omni/commit/78c144f3a8f1e4fb3e9d9e0c38bc0a0e635c7c98)

- **作者**: Gao Han
- **时间**: 2026-08-04T15:21:38Z
- **提交信息**: [CI failed] Revert "[Perf][Qwen3-TTS] Fuse QKV and gate_up projections in code predictor" (#5777)

### [1c4aca7](https://github.com/vllm-project/vllm-omni/commit/1c4aca7f6e3bd24507872e193e091a6af55140f6)

- **作者**: NATURE
- **时间**: 2026-08-04T14:40:27Z
- **提交信息**: [Bugfix][Hunyuan/Bagel]Avoid payload connector for KV-only senders (#5744)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [6fdc4ca](https://github.com/vllm-project/vllm-omni/commit/6fdc4ca62dc6080bc683552c6ec9e310e9c80867)

- **作者**: 林鑫
- **时间**: 2026-08-04T11:59:32Z
- **提交信息**: [Perf][Qwen3-TTS] Fuse QKV and gate_up projections in code predictor (#4958)

Signed-off-by: sheenlin <sheenlin@tencent.com>
Co-authored-by: sheenlin <sheenlin@tencent.com>
Co-authored-by: yurain <yurain26@users.noreply.github.com>

### [b6728db](https://github.com/vllm-project/vllm-omni/commit/b6728db486a31d5e86fa167484f49e638357a430)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-08-04T11:51:12Z
- **提交信息**: [Frontend] Add ComfyUI support for r2v (MiniMax H3 as example) (#5756)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Signed-off-by: Zeyu Huang | 黃澤宇 <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

### [b9a5159](https://github.com/vllm-project/vllm-omni/commit/b9a51592f0ca845e23dad9018f25e9fda4b4928c)

- **作者**: Mu GuanLin
- **时间**: 2026-08-04T11:35:01Z
- **提交信息**: [Model][Feat] MiniMax H3 online FP8 support (#5737)

Signed-off-by: mglyn <1203789601@qq.com>

### [5215e03](https://github.com/vllm-project/vllm-omni/commit/5215e03a91adecbb5ffece29aa74360a7569d0c5)

- **作者**: ruirui(rein) yang
- **时间**: 2026-08-04T07:10:47Z
- **提交信息**: [Refactor][1/N Scheduler]Remove duplicated AR/generation scheduler plumbing and establish explicit shared lifecycle contracts. (#5461)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>

---
