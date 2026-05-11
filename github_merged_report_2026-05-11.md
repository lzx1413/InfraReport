# GitHub Stars 合并报告 - 2026-05-11

**合并日期**: 2026-05-12
**监控日期**: 2026-05-11
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


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1908
- **最后更新**: 2026-05-11T17:36:03Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: phdddd, Juncheng Wan

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型
- **性能优化**：提交 `895abff` 明确包含性能优化（`optimize`）。
- **Bug修复**：提交 `895abff` 包含Bug修复（`fix`）。
- **功能新增**：提交 `a72086a` 是功能新增（`feat`），为特定硬件环境添加了Docker支持。

### 2. 关键变更点及其与项目整体方向的关系
- **`[parallel, perf] fix: sp gather && optimize: input embeds fusing`**：
  - **变更点**：修复了序列并行（Sequence Parallelism, SP）中的 `gather` 操作问题，并优化了输入嵌入（input embeds）的融合（fusing）。
  - **项目关系**：VeOmni的核心是“以模型为中心的分布式训练配方库”，旨在高效扩展任意模态模型的训练。序列并行是训练超长序列（如视频、长文档）的关键技术。修复其`gather`操作保证了数据在多设备间正确聚合；优化输入嵌入融合则能减少内存占用和通信开销，直接提升训练效率。这直接服务于项目“高效扩展”的核心目标。

- **`[docker] feat: add dockerfile and image for 9.0.0 cann base image`**：
  - **变更点**：为昇腾（Ascend）硬件的CANN 9.0.0基础镜像添加了Dockerfile和镜像支持。
  - **项目关系**：VeOmni旨在支持多种硬件平台。此提交扩展了对国产昇腾生态的支持，降低了用户在特定硬件环境下的部署门槛，体现了项目“模型中心”和“分布式”的包容性，有助于吸引更广泛的用户和开发者社区。

### 3. 对项目的影响和潜在意义
- **提升训练稳定性与效率**：修复SP gather bug能避免因数据聚合错误导致的训练失败或模型精度下降。优化输入嵌入融合能显著降低显存占用和跨设备通信量，从而支持更大模型或更长序列的训练，或提升训练吞吐量。
- **降低部署门槛，扩大生态**：提供昇腾CANN 9.0.0的Docker镜像，使得用户无需手动配置复杂的依赖环境，可以快速在昇腾硬件上启动VeOmni。这有助于项目在国产AI芯片生态中落地，吸引更多用户和贡献者，增强项目的生命力。

### 4. 值得关注的技术点
- **序列并行（SP）的`gather`操作**：这是分布式训练中一个容易出错但至关重要的环节。修复它表明项目团队在深入打磨分布式训练的核心通信原语，追求高可靠性。
- **输入嵌入融合（input embeds fusing）**：这是一种常见的模型优化技巧，通过将多个小操作（如embedding lookup、位置编码等）合并为一个内核执行，减少内核启动开销和内存带宽消耗。在VeOmni这种支持多模态的框架中，输入嵌入的处理可能因模态不同而复杂，此优化具有通用价值。
- **CANN 9.0.0 Docker支持**：这表明项目正在积极适配最新的昇腾软件栈，紧跟硬件生态发展，确保在国产硬件上的最佳性能。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化核心竞争力**：VeOmni的核心价值在于提供高效、可扩展的分布式训练方案。修复SP bug和优化嵌入融合，直接强化了其在处理长序列、大模型场景下的性能和稳定性优势，这是其区别于其他框架的关键。
- **拓展应用边界**：通过支持昇腾CANN 9.0.0，VeOmni不再局限于英伟达GPU生态，而是向更广泛的国产硬件平台延伸。这符合国家科技自立自强的趋势，能吸引来自不同硬件背景的研究者和工程师，为项目带来新的应用场景和贡献者，推动其从“论文中的框架”向“工业级通用平台”发展。

## 详细提交记录

### [895abff](https://github.com/ByteDance-Seed/VeOmni/commit/895abff1b08356a910c11f7f5bd84028eabcee55)

- **作者**: Juncheng Wan
- **时间**: 2026-05-11T12:22:11Z
- **提交信息**: [parallel, perf] fix: sp gather && optimize: input embeds fusing (#681)

### [a72086a](https://github.com/ByteDance-Seed/VeOmni/commit/a72086a087725da794de46e568c732542d4fe07f)

- **作者**: phdddd
- **时间**: 2026-05-11T09:50:39Z
- **提交信息**: [docker] feat: add dockerfile and image for 9.0.0 cann base image (#742)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2254
- **最后更新**: 2026-05-11T18:44:20Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Shiqiao Gu (谷石桥), Yang Yong (雍洋)

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 昨日更新要点总结

#### 1. 主要更新类型
本次更新主要集中在 **功能新增** 和 **Bug修复** 上，并包含一次 **重构**。

- **功能新增**：支持 `neopp` 模型的8步推理。
- **Bug修复**：修复了 `neopp` 模型在配置蒸馏（cfg distill）时的问题。
- **重构**：对 `matrix game v2` 相关代码进行了重构。

#### 2. 关键变更点及其与项目整体方向的关系
- **`neopp` 模型支持8步推理**：这是对 `neopp` 模型推理效率的显著提升。在视频生成领域，推理步数直接决定了生成速度。从默认的更多步数减少到8步，意味着在保持生成质量的前提下，大幅降低了计算开销和延迟，这与项目“轻量级视频生成推理框架”的定位高度一致。
- **修复 `neopp` 配置蒸馏Bug**：配置蒸馏（Classifier-Free Guidance Distillation）是一种用于加速推理的技术。修复此Bug确保了该加速路径的稳定性和正确性，是完善 `neopp` 模型加速能力的关键一步。
- **重构 `matrix game v2`**：重构通常旨在改善代码结构、可维护性或性能，为未来的功能迭代打下更坚实的基础。这体现了项目在快速迭代的同时，也在关注代码质量。

#### 3. 对项目的影响和潜在意义
- **提升 `neopp` 模型的实用性和竞争力**：8步推理和蒸馏Bug的修复，使得 `neopp` 模型在推理速度上更具优势，能更好地满足实时或近实时的视频生成应用场景，增强了框架在特定模型上的吸引力。
- **完善核心加速管线**：这些提交共同完善了针对 `neopp` 模型的加速管线（从推理步数优化到蒸馏技术修复），表明项目正在系统性地为不同模型提供定制化的高效推理方案。
- **为未来扩展铺路**：对 `matrix game v2` 的重构，可能为后续集成更多模型或优化算法提供了更清晰的架构基础。

#### 4. 值得关注的技术点
- **`neopp` 模型的8步推理**：这是一个具体的性能优化点。值得关注其实现方式（例如是否使用了特定的采样器或噪声调度策略），以及8步推理后生成视频的质量与原始模型的对比。
- **配置蒸馏（cfg distill）**：这是一种模型压缩和加速技术。修复其Bug表明项目团队正在深入应用此类前沿技术来优化推理效率。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **强化“轻量”与“高效”的核心价值**：项目README强调“Light Video Generation Inference Framework”。昨日更新直接通过减少推理步数和修复加速技术Bug，将“轻量”和“高效”落到了具体模型上，证明了框架在实现这一目标上的实际进展。
- **构建模型生态的差异化优势**：通过为 `neopp` 模型提供专门的优化（8步推理），框架可以吸引更多使用该模型的开发者，形成特定模型生态的优化优势，而不仅仅是提供一个通用的推理接口。
- **从“能用”向“好用”演进**：修复Bug和重构代码，表明项目正从实现基本功能（能用）转向提升稳定性、性能和可维护性（好用），这对于一个开源框架的长期发展至关重要。

## 详细提交记录

### [3b18c45](https://github.com/ModelTC/LightX2V/commit/3b18c4566b2d848c4638a5f4ea291de035f202dd)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-05-11T10:29:35Z
- **提交信息**: refactor matrix game v2 (#1062)

Co-authored-by: gushiqiao <975033167>

### [90069f0](https://github.com/ModelTC/LightX2V/commit/90069f04cfe787aa08985d6b4d02964e9ad1174c)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-11T10:26:44Z
- **提交信息**: fix neopp cfg distill (#1061)

### [8e54f55](https://github.com/ModelTC/LightX2V/commit/8e54f553454dbdb21cec25108134c8032db10ff5)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-11T08:40:26Z
- **提交信息**: support neopp model 8 steps infer (#1060)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2069
- **最后更新**: 2026-05-11T09:30:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5591
- **最后更新**: 2026-05-11T22:43:15Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Lee Nau, Mingyang Wang, Perkz Zheng

## AI分析总结

好的，这是对 `flashinfer-ai/flashinfer` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**
- **Bug 修复 (Bug Fix)**
- **性能优化 (Performance Optimization)**

### 2. 关键变更点及其与项目整体方向的关系

FlashInfer 项目的核心目标是提供用于大模型推理的高性能 GPU 内核。这些提交都紧密围绕这一目标，专注于扩展硬件支持、提升计算效率和修复性能问题。

- **扩展硬件支持与功能覆盖:**
    - **[4dba29f] feat: add SM120 fmha_v2 kernels to AOT pip wheel builds**: 将为 SM120/SM121 (Blackwell) 架构优化的 `fmha_v2` (Flash Attention) 内核纳入到预编译的 pip wheel 中。这直接扩展了项目对最新 NVIDIA GPU 架构的“开箱即用”支持，确保用户无需通过 JIT 编译即可获得最佳性能。
    - **[1bb79d4] feat: FP8 output support for CUTLASS MLA paged attention**: 为 MLA (Multi-head Latent Attention) 分页注意力内核增加了原生 FP8 输出支持。这允许模型在注意力计算后直接输出 FP8 格式，省去了额外的 `bf16 -> fp8` 量化内核启动，从而减少延迟和显存带宽消耗，是提升推理吞吐量的关键优化。
    - **[2d0e0ef] Support Kimi K2.5 H64 CuTe DSL MLA decode**: 通过填充技术，使 CuTe DSL (领域特定语言) 实现的 MLA 解码内核支持 Kimi K2.5 模型使用的 64 个查询头配置。这体现了项目对特定前沿模型架构的快速适配能力，增强了其在实际应用中的实用性。
    - **[4f072c4] Add dynamic tokens-per-page TRTLLM-GEN GQA kernels**: 引入了支持动态 tokens-per-page 的 GQA (Grouped Query Attention) 内核。这允许在推理时根据页面大小动态选择最优内核，提高了内存利用率和计算效率，特别是在处理变长序列时。

- **修复关键 Bug 与性能回归:**
    - **[6885e76] fix(jit): propagate -DNDEBUG to host-side cflags**: 修复了一个 JIT 编译中的 Bug，该 Bug 导致在 Release 构建中，主机端 (host-side) 代码未定义 `NDEBUG` 宏。这导致 TensorRT-LLM 的日志记录器默认使用 `DEBUG` 级别，在每次 MoE 前向传播时输出大量调试信息，造成巨大的日志文件（2.9GB）和潜在的性能开销。此修复确保了 Release 构建的纯净性。
    - **[e744910] fix(cute_dsl/moe): unbias autotuner profiling for tile_size enumeration**: 修复了 CuTe DSL MoE 内核自动调优器中的一个偏差问题。由于预分配缓冲区大小固定，导致自动调优器在评估不同 `tile_size` 时，会因内存分配开销不对称而产生偏好，从而选择次优的 `tile_size`。此修复通过调整缓冲区分配策略，确保了自动调优的公平性和准确性，直接提升了 MoE 内核的性能。

### 3. 对项目的影响和潜在意义

- **提升旗舰硬件支持**: 对 SM120 (Blackwell) 架构的全面支持（包括 AOT 编译），巩固了 FlashInfer 作为最新 NVIDIA GPU 上高性能推理库的地位。
- **优化关键模型性能**: FP8 输出和动态 tokens-per-page 等特性，直接针对当前主流的大模型（如使用 MLA 的 DeepSeek 系列）和推理场景（如变长序列批处理）进行优化，能显著降低推理成本和延迟。
- **提升稳定性和可靠性**: 修复 JIT 编译和自动调优器中的 Bug，不仅解决了日志爆炸等实际问题，也提升了整个库在 Release 模式下的性能和稳定性，增强了用户信心。
- **增强生态兼容性**: 对 Kimi K2.5 等特定模型架构的支持，以及与 TRTLLM-GEN 内核的集成，表明项目正积极与更广泛的 LLM 生态系统（如 Moonshot AI, NVIDIA TensorRT-LLM）进行适配和协同优化。

### 4. 值得关注的技术点

- **AOT vs JIT 编译**: 提交 `4dba29f` 强调了 AOT (Ahead-of-Time) 编译与 JIT (Just-in-Time) 编译路径的差异。确保新特性在两种路径下都可用，对于提供一致的用户体验至关重要。
- **`NDEBUG` 宏的传播**: 提交 `6885e76` 揭示了一个在混合 CUDA/C++ 项目中常见的陷阱：编译器标志（如 `-DNDEBUG`）需要在设备端 (`nvcc`) 和主机端 (`g++`) 编译时都正确传递，否则会导致 Release 和 Debug 行为不一致。
- **自动调优器的公平性**: 提交 `e744910` 指出，自动调优器在评估不同配置时，必须确保评估环境（如内存分配状态）是公平的，否则会引入系统性偏差，导致次优选择。这是一个在性能调优中容易被忽视但至关重要的细节。
- **CuTe DSL 的灵活性**: 提交 `2d0e0ef` 展示了 CuTe DSL 在实现复杂、非标准注意力模式（如 H=64 的 MLA）时的强大能力，以及通过“填充”等

## 详细提交记录

### [4dba29f](https://github.com/flashinfer-ai/flashinfer/commit/4dba29fbd626fc0ac28eea22101db8f8588d78b7)

- **作者**: Blake Ledden
- **时间**: 2026-05-11T22:43:10Z
- **提交信息**: feat: add SM120 fmha_v2 kernels to AOT pip wheel builds (#2885)

## Summary

`gen_trtllm_fmha_v2_sm120_module()` exists in `jit/attention/modules.py`
and the JIT runtime path (`generate_kernels.py`) already dispatches to
it correctly. However, `aot.py`'s `gen_all_modules()` — which drives the
pip wheel AOT build — was missing it from the `has_sm120 or has_sm121`
section.

This means SM120/SM121 devices using a pip wheel would never get the
fmha_v2 SM120 kernels compiled into the wheel, and would have to fall
back to slower paths.

**Fix:** Add `gen_trtllm_fmha_v2_sm120_module()` to the `has_sm120 or
has_sm121` block in `aot.py`, alongside the other SM120 modules (fused
MOE, GEMM, FP4 quantization).

No behavior change for JIT users; only affects AOT pip wheel builds.

Addresses the AOT gap noted in #2555.

Contributed by Second Nature Computing (https://joinsecondnature.com)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Expanded optimized inference module support for SM120 and SM121 GPUs
to include attention kernels in addition to existing fused MoE and GEMM
optimizations.
* Increased runtime coverage and readiness for attention-heavy workloads
on those architectures, improving performance consistency for models
using attention.

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/2885)
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [6885e76](https://github.com/flashinfer-ai/flashinfer/commit/6885e76a5e12a59220b9dc199d86a64fbe5f6d78)

- **作者**: Artem Perevedentsev
- **时间**: 2026-05-11T17:49:33Z
- **提交信息**: fix(jit): propagate -DNDEBUG to host-side cflags (#3278)

## 📌 Description

`gen_jit_spec` adds `-DNDEBUG` only to `extra_cuda_cflags` (consumed by
`nvcc` for `.cu` files), not to `extra_cflags` (consumed by `g++` for
host-side `.cpp`). Several host-only translation units are part of
MoE/GEMM JIT specs — most notably
`csrc/nv_internal/cpp/common/logger.cpp` — and they end up compiled
without `NDEBUG` while the rest of the module is a release build.

For the TensorRT-LLM logger this matters because of:

```cpp
// csrc/nv_internal/include/tensorrt_llm/common/logger.h
#ifndef NDEBUG
  Level const DEFAULT_LOG_LEVEL = DEBUG;
#else
  Level const DEFAULT_LOG_LEVEL = INFO;
#endif
```

With `NDEBUG` missing on the host side, every prebuilt
`flashinfer-jit-cache` wheel ships with `Logger::level_ = DEBUG (10)`.
On Hopper this turns each MoE forward pass into a stream of
`[TensorRT-LLM][DEBUG] ... sm90_generic_mixed_moe_gemm_kernelLauncher
...` lines from the OSS CUTLASS kernel dispatcher. Verified by reading
the data-section initializer of `Logger::Logger()` in the released
`flashinfer-jit-cache==0.6.10+cu130`
`fused_moe_{90,100,103,120,trtllm_sm100}.so` — all five start `Logger`
with `DEFAULT_LOG_LEVEL=10` and `level_=10`, even though the same wheels
carry no `.debug_*` sections (i.e. they are otherwise release-built).

The fix is one line: also append `-DNDEBUG` to the host `cflags` when
not in debug mode. The `flashinfer-jit-cache` wheel build picks this up
automatically and the prebuilt logger flips back to `INFO`.

## 🔍 Related Issues

Initially this bug was observed during integration of FI v0.6.10 into
vLLM: [[CI/Build] Bump flashinfer to v0.6.10
#41711](https://github.com/vllm-project/vllm/pull/41711).
There is a CI job log failure due to this issue:
[buildkite/ci/pr/distributed-tests-2-gpus-h100](https://buildkite.com/vllm/ci/builds/64532#019df966-e67d-4c27-af0e-76b00bc496e5).

Surfaced while debugging a downstream CI step that produced a 2.9 GB log
dominated by TRT-LLM debug prints from `fused_moe_90.so`. No FlashInfer
issue tracking this yet — happy to file one alongside this PR if useful.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`.
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`pytest tests/test_jit_cpp_ext.py`).

Two regression tests added in `tests/test_jit_cpp_ext.py`, mirroring the
existing `test_debug_jit_uses_sccache_compatible_nvcc_device_debug_flag`
style:

```
pytest tests/test_jit_cpp_ext.py -v
```

```
test_release_jit_propagates_ndebug_to_host_cflags PASSED
test_debug_jit_does_not_propagate_ndebug          PASSED
```

The first asserts that a release build
(`FLASHINFER_JIT_DEBUG`/`FLASHINFER_JIT_VERBOSE` unset) puts `-DNDEBUG`
in **both** `spec.extra_cflags` and `spec.extra_cuda_cflags`. The second
locks in symmetry: with `FLASHINFER_JIT_DEBUG=1` neither list contains
`-DNDEBUG`. Without the fix, the first test fails on `assert "-DNDEBUG"
in spec.extra_cflags`.

## Reviewer Notes

Single-line behavior change in `flashinfer/jit/core.py`. No effect on
debug builds. Prebuilt wheels rebuilt from this commit will pick up the
change automatically — no schema/version bump needed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* JIT-compiled code now includes optimized compilation flags in release
mode for improved performance.

* **Tests**
* Added test coverage for proper compilation flag handling between debug
and release build modes.

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3278)

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [1bb79d4](https://github.com/flashinfer-ai/flashinfer/commit/1bb79d4a2039f9c83caad3855fce2f6db65f6200)

- **作者**: Carl Y
- **时间**: 2026-05-11T17:03:17Z
- **提交信息**: feat: FP8 output support for CUTLASS MLA paged attention (#2779)

Closes #2778

## Summary

Wires `output_scale` and separate `ElementOut` type through the CUTLASS
MLA paged attention kernel stack to enable native FP8 output,
eliminating a separate bf16→FP8 quant kernel launch.

- Template `MlaSm100` on `ElementOut` separately from `Element` (input
type)
- Pass `output_scale` through `args_from_options`, `runMla`, FFI
binding, and Python API
- Dispatch on input/output dtype in FFI layer (bf16→bf16 or bf16→fp8)
- Pass `output_scale` to reduction kernel for correct split-KV handling
- Add `o_scale` parameter to `BatchMLAPagedAttentionWrapper.run()`
matching the existing ragged prefill API convention

### Motivation

The CUTLASS MLA kernel epilogue already supports arbitrary `ElementOut`
and `output_scale` at the template level, but the wrapper/FFI/Python
layers hardcoded `ElementOut = Element` and didn't expose
`output_scale`. This PR plumbs it through.

### Changes

| File | Change |
|------|--------|
| `cutlass_mla.cuh` | Template `MlaSm100<T, TOut>`, add `output_scale`
to `args_from_options` and `runMla` |
| `cutlass_mla.cu` | Accept `output_scale`, dispatch `bf16→bf16` vs
`bf16→fp8` |
| `flashinfer_mla_binding.cu` | Updated FFI signature |
| `sm100_mla.hpp` | Pass `output_scale` to reduction kernel args |
| `sm100_fmha_mla_reduction.hpp` | Add `output_scale` field, apply
before cast to `ElementOut` |
| `mla.py` | Add `o_scale` parameter to `run()` |

## Test plan

```
============================= test session starts ==============================
platform linux -- Python 3.12.3, pytest-9.0.3, pluggy-1.6.0 -- /root/flashinfer/.venv/bin/python3
cachedir: .pytest_cache
rootdir: /root/flashinfer
configfile: pytest.ini
collecting ... collected 16 items

tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-1-128-1] PASSED [  6%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-1-128-4] PASSED [ 12%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-1-1024-1] PASSED [ 18%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-1-1024-4] PASSED [ 25%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-16-128-1] PASSED [ 31%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-16-128-4] PASSED [ 37%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-16-1024-1] PASSED [ 43%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output[fp8_dtype0-16-1024-4] PASSED [ 50%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_no_out PASSED [ 56%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_wrong_dtype PASSED [ 62%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_invalid_scale[0.0] PASSED [ 68%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_invalid_scale[-1.0] PASSED [ 75%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_invalid_scale[nan] PASSED [ 81%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_output_validation_invalid_scale[inf] PASSED [ 87%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_bf16_output_unchanged PASSED [ 93%]
tests/attention/test_cutlass_mla_fp8_output.py::test_cutlass_mla_fp8_non_cutlass_backend_rejected PASSED [100%]

=============================== warnings summary ===============================
flashinfer/gemm/kernels/grouped_gemm_masked_blackwell.py:2060
  /root/flashinfer/flashinfer/gemm/kernels/grouped_gemm_masked_blackwell.py:2060: DeprecationWarning: tcgen05.OperandMajorMode is deprecated, use cute.nvgpu.OperandMajorMode instead
    a_major_mode: tcgen05.OperandMajorMode,

flashinfer/gemm/kernels/grouped_gemm_masked_blackwell.py:2062
  /root/flashinfer/flashinfer/gemm/kernels/grouped_gemm_masked_blackwell.py:2062: DeprecationWarning: tcgen05.OperandMajorMode is deprecated, use cute.nvgpu.OperandMajorMode instead
    b_major_mode: tcgen05.OperandMajorMode,

flashinfer/gdn_kernels/blackwell/gated_delta_net_chunked.py:99
flashinfer/gdn_kernels/blackwell/gated_delta_net_chunked.py:99
  /root/flashinfer/flashinfer/gdn_kernels/blackwell/gated_delta_net_chunked.py:99: DeprecationWarning: tcgen05.OperandMajorMode is deprecated, use cute.nvgpu.OperandMajorMode instead
    from cutlass.cute.nvgpu.tcgen05 import OperandMajorMode

-- Docs: https://docs.pytest.org/en/stable/how-to/capture-warnings.html
======================= 16 passed, 4 warnings in 34.24s ========================
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* FP8 fused-output support for MLA paged attention: callers may provide
an output scale to produce FP8 outputs on the CUTLASS backend.

* **Bug Fixes / Validation**
* Added validation for output-scale (finite, positive, representable)
and enforced that using a scale requires an FP8 output tensor;
non-CUTLASS backends reject output-scale.

* **Tests**
* Added tests for FP8 quantization correctness, validation error cases,
and backend compatibility.

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/2779)
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [2d0e0ef](https://github.com/flashinfer-ai/flashinfer/commit/2d0e0efacb011b4a365c7e4999ffe118f4d610e1)

- **作者**: Mingyang Wang
- **时间**: 2026-05-11T17:00:24Z
- **提交信息**: Support Kimi K2.5 H64 CuTe DSL MLA decode (#3235)

https://github.com/flashinfer-ai/flashinfer/issues/3161

## Summary

- Enable CuTe DSL MLA decode for Kimi K2.5-style 64 query heads.
- Allow H=64 split-KV by padding split-KV workspace storage to the
physical 128-head MMA lane width.
- Fold 64-head coverage into the existing CuTe DSL MLA decode test
sweep.

## Notes

An experimental 64-wide MMA-M path was investigated separately, but it
was reverted and is not part of this PR. The branch intentionally keeps
the GPU-validated padded implementation.

## Validation

- `pre-commit run --files
flashinfer/cute_dsl/attention/collective_builder.py
flashinfer/cute_dsl/attention/mla_config.py
flashinfer/cute_dsl/attention/mla_decode.py
flashinfer/cute_dsl/attention/mla_decode_fp8.py
flashinfer/cute_dsl/attention/scheduler/mla_persistent.py
flashinfer/cute_dsl/attention/wrappers/batch_mla.py
tests/attention/test_cute_dsl_mla_decode.py`
- SM100 smoke: H=64 CuTe DSL MLA public API with computed `split_kv=32`,
output shape `(1, 1, 64, 512)`, dtype `torch.float16`, no NaNs.
- SM100 padded benchmark: B=1/S=128 `0.027255 ms`, B=1/S=512 `0.027000
ms`, B=4/S=128 `0.026925 ms`, B=4/S=512 `0.026979 ms`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Relaxed head-count constraints so MLA decode accepts smaller head
dimensions and more configurations.

* **Bug Fixes**
* Workspace sizing now pads head dimension to 128 for accumulator/layout
computations and when computing workspace for split-KV, preventing
layout/address issues.
  * Removed runtime rejection for small head counts.

* **Tests**
* Expanded MLA decode tests to cover multiple head counts and added
NaN/Inf (finiteness) assertions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e744910](https://github.com/flashinfer-ai/flashinfer/commit/e744910fc3bda965542862e5fcff98f2d3edda2b)

- **作者**: Lee Nau
- **时间**: 2026-05-11T16:32:57Z
- **提交信息**: fix(cute_dsl/moe): unbias autotuner profiling for tile_size enumeration (#3252)

<!-- .github/pull_request_template.md -->

## 📌 Description

`CuteDslMoEWrapper.__init__` pre-allocates `_gemm1_output`,
`_gemm1_output_scale`, and `_moe_sort_buffers` sized for
`self.tile_size` only. The `use_prealloc` gate in `_forward_with_tactic`
(`fused_moe.py`) is `tile_size == self.tile_size and self.use_cuda_graph
and num_tokens <= self.max_num_tokens`, so during autotune profiling the
mismatched-`tile_size` tactics fall through to dynamic `torch.empty()`
allocation while matching ones run on the prealloc. The autotuner sees
**asymmetric allocation overhead** between tactic groups and
consistently picks the matching `tile_size` even when intrinsic kernel
performance favors the other — at EP=8/16 N=16384, fi locks to
`tile_size=128` in 14/14 cache entries while TRT-LLM picks
`tile_size=256` more often.

The fix includes three coordinated changes: (1) `tuner.py` lifts the
hardcoded `[128, 256]` to a module-level `VALID_TILE_SIZES` tuple —
single source of truth for tactic enumeration AND prealloc sizing; (2)
`fused_moe.py:_allocate_buffers` sizes buffers to fit any `tile_size in
VALID_TILE_SIZES` (`max_num_permuted_tokens` increases with `tile_size`
→ use `max(VALID_TILE_SIZES)`; `max_num_tiles` decreases → use
`min(VALID_TILE_SIZES)`); (3) the prealloc gate becomes `tile_size in
VALID_TILE_SIZES`. Both tactic groups now reuse the prealloc; profiling
is unbiased.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/pull/3216
https://github.com/flashinfer-ai/flashinfer/pull/3171

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

* **Bug Fixes**
* Improved CUDA preallocation gating so preallocated buffers are reused
safely when CUDA graphs are enabled, avoiding allocation mismatches
across supported tile sizes and improving memory efficiency.

* **New Features**
* Autotuner now scopes per-tactic timing so preallocation is skipped
during measurement windows but used outside them; buffer sizing now
supports all valid tile sizes.

* **Tests**
* Added CPU/GPU tests validating preallocation capacity and correct
gating behavior during tuning and inference.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [4f072c4](https://github.com/flashinfer-ai/flashinfer/commit/4f072c4fdfd6d4e29e7d493c3b191023b7825ba8)

- **作者**: Perkz Zheng
- **时间**: 2026-05-11T07:05:53Z
- **提交信息**: Add dynamic tokens-per-page TRTLLM-GEN GQA kernels (#3259)

## Summary
- update TRTLLM-GEN FMHA artifact path and checksum to the newly
published cubins
- select dynamic tokens-per-page kernels for paged GQA decode and
prefill when page size is at least 128
- keep MLA decode kernel selection on dense-mask keys and add
Blackwell-only dynamic page-size coverage
- relax fp16 Blackwell attention-sink context tolerance to match
observed precision noise

## Tests
- pre-commit run on changed files
- python3 -m pytest -q -n 8 --tb=short --maxfail=5 -k
trtllm-gen-mla-filter tests/attention/test_trtllm_gen_mla.py: 7686
passed
- python3 -m pytest -q -n 8 --tb=short
tests/attention/test_attention_sink_blackwell.py: 144 passed


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
  * Updated an artifact path and its checksum manifest.

* **New Features**
* Dynamic page-size selection for generation attention kernels on
supported GPUs.
* Per-token variable sparse-MLA top‑K lengths for finer-grained sparse
attention.
* Expanded MLA-generation kernel support for additional head/dimension
combos.

* **Tests**
  * Added GPU-only tests for dynamic page-size prefill/decode scenarios.
  * Relaxed float16 numerical tolerance in an attention test.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Perkz Zheng <PerkzZheng@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3464
- **最后更新**: 2026-05-11T14:32:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33595
- **最后更新**: 2026-05-11T21:45:41Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: sayakpaul, Sayak Paul

## AI分析总结

好的，这是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

*   **文档更新**：主要更新类型，涉及 API 文档的补充。
*   **构建/配置优化**：改进了项目依赖管理工具（UV）的配置。
*   **代码风格维护**：进行了代码格式化的修复。

### 2. 关键变更点及其与项目整体方向的关系

*   **提交 `e5cf820`**：在缓存 API 文档列表中添加了 `magcache`。
    *   **关系**：`diffusers` 项目致力于提供高效、易用的扩散模型推理工具。`magcache` 是一种用于加速推理的缓存技术，将其纳入官方文档，表明项目正在积极整合和推广社区或内部开发的性能优化方案，以提升用户体验。
*   **提交 `6382a3d`**：优化了 `UV_PRERELEASE=allow` 的使用方式。
    *   **关系**：`UV` 是一个快速的 Python 包安装器。此修改旨在更精确地控制预发布版本的安装，确保开发者和用户在安装依赖时能获得更稳定或更前沿的版本，这有助于项目的持续集成和开发流程的顺畅。
*   **提交 `0acc903`**：修复了代码风格问题。
    *   **关系**：保持代码风格统一是大型开源项目维护代码可读性和可维护性的基础工作，体现了项目对代码质量的重视。

### 3. 对项目的影响和潜在意义

*   **提升可发现性**：将 `magcache` 加入文档，能让更多用户了解并使用这项加速技术，从而在实际应用中提升模型推理速度，降低使用成本。
*   **改善开发体验**：优化 UV 配置可以减少因依赖版本问题导致的构建失败，提升开发者和贡献者的工作效率。
*   **维护代码健康度**：定期的代码风格修复有助于保持代码库的整洁，减少技术债务，为未来的功能迭代打下良好基础。

### 4. 值得关注的技术点

*   **`magcache`**：这是一个值得关注的技术点。它可能是一种针对扩散模型去噪过程（尤其是 Cross-Attention 层）的缓存机制，通过复用中间计算结果来显著加速推理。用户应关注其具体实现原理、适用场景（如是否支持所有模型）以及性能提升幅度。
*   **`UV_PRERELEASE`**：这个环境变量用于控制 UV 是否安装包的预发布版本。`better usage` 可能意味着项目现在更智能地处理了依赖关系，例如只在特定分支或场景下允许安装预发布版，以避免对稳定用户造成影响。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化“易用性”与“高性能”定位**：根据 README，`diffusers` 的目标是让扩散模型“人人可用”。将 `magcache` 这样的性能优化方案文档化，直接降低了用户使用高级特性的门槛，让“高性能”不再是少数专家的专利，这与项目核心目标高度一致。
*   **优化基础设施，支撑快速发展**：改进 UV 配置和修复代码风格，看似是“小事”，实则是为项目这艘大船进行日常维护和引擎调优。一个稳定、高效的开发基础设施，是 `diffusers` 能够持续快速迭代、集成最新模型（如 Stable Diffusion 3, Flux 等）和技术的基石。
*   **总结**：昨日的更新虽然规模不大，但体现了 `diffusers` 项目在“**功能推广**”和“**基础设施优化**”两个维度的持续投入。这有助于项目在保持技术领先的同时，也维持一个健康、高效的开发社区。

## 详细提交记录

### [e5cf820](https://github.com/huggingface/diffusers/commit/e5cf820fc3bf4f84296fa32b3ca918afdcb99974)

- **作者**: Sayak Paul
- **时间**: 2026-05-11T21:45:26Z
- **提交信息**: [docs] add magcache to caching api listing (#13714)

add magcache to caching api listing

### [6382a3d](https://github.com/huggingface/diffusers/commit/6382a3db4dd1e129ce8be68649db6fcbae015e8c)

- **作者**: Sayak Paul
- **时间**: 2026-05-11T08:13:00Z
- **提交信息**: better usage of UV_PRERELEASE=allow (#13716)

### [0acc903](https://github.com/huggingface/diffusers/commit/0acc903edf096da2ae764d52556b91434f11e058)

- **作者**: sayakpaul
- **时间**: 2026-05-11T07:49:01Z
- **提交信息**: styling fix.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 403
- **最后更新**: 2026-05-11T08:48:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12395
- **最后更新**: 2026-05-11T17:56:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 27662
- **最后更新**: 2026-05-11T22:59:57Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 17
- **主要提交者**: Jia Guo, Mick, Yihao Wang

## AI分析总结

好的，这是对仓库 `sgl-project/sglang` 昨日提交记录的分析总结：

### 1. 主要更新类型

-   **功能新增 (Feature)**
-   **性能优化 (Performance)**
-   **Bug 修复 (Bug Fix)**
-   **文档更新 (Documentation)**
-   **基础设施/CI (Infrastructure/CI)**
-   **代码重构 (Refactoring)**

### 2. 关键变更点及其与项目整体方向的关系

-   **推测解码 (Speculative Decoding) 优化与清理**：
    -   `[6c3541a]`, `[ce1736f]`, `[42bcbc0]`, `[c7e53e6]`: 对推测解码模块进行了多项优化，包括重构 `EagleDraft`/`EagleExtendInput` 类方法以更高效地路由空闲 `hidden_size`，移除死内核参数，修复 ngram 指标计算中的 off-by-1 错误，并放宽了命名规则。
    -   **关系**：推测解码是 SGLang 提升 LLM 推理吞吐量的核心技术之一。这些提交旨在使其更稳定、高效，并简化开发流程，直接服务于项目“高性能推理”的核心目标。

-   **新连接器 (Connector) 支持**：
    -   `[d3edfb5]`: 新增了对 Azure Blob Storage 连接器的支持，允许通过 `az://` 或 `*.blob.core.windows.net` 格式的 URL 加载模型或数据。
    -   **关系**：扩展了 SGLang 的生态系统集成能力，使其能更方便地部署在 Azure 云环境中，增强了项目的灵活性和云原生特性。

-   **性能优化与内存管理**：
    -   `[da0eeb8]`: 新增 `--prefill-only-disable-kv-cache` 参数，允许在仅执行预填充 (prefill) 的场景下跳过 KV 缓存池分配，从而节省显存。
    -   `[1df9edc]`: 对 DeepSeek V3.2 的 Indexer GEMM 操作使用 PyTorch 的 `torch.mm`，可能带来性能提升。
    -   `[23]`: 引入 Cute-DSL 实现的 NVFP4 量化内核，用于更高效的模型量化推理。
    -   **关系**：这些优化直接回应了 LLM 推理中的关键瓶颈——显存和计算效率。通过精细控制 KV 缓存和引入更高效的量化内核，项目在降低部署成本和提升吞吐量方面持续进步。

-   **硬件平台支持扩展**：
    -   `[2e69266]`, `[aeb8fef]`, `[6b6963f]`: 针对 AMD ROCm 平台，修复了依赖安装问题，并固定了 `cache-dit` 版本以确保环境稳定性。
    -   `[f7ba136]`, `[df441b8]`: 针对 NPU (神经网络处理器) 平台，升级了 `sgl-kernel-npu` 版本，并支持了共享专家的双流优化。
    -   **关系**：SGLang 致力于成为多硬件平台的推理框架。这些提交表明项目正在积极维护和优化对 AMD 和 NPU 等非 NVIDIA 硬件的支持，以扩大其用户基础和应用场景。

-   **可观测性与调试能力增强**：
    -   `[4b6f776]`: 新增了 SWA (Sliding Window Attention) 的 radix cache 事件发布功能。
    -   `[95985f9]`: 支持通过 `SGLANG_TRACE_LEVEL` 环境变量在启动时设置追踪级别。
    -   **关系**：增强了项目的可观测性，有助于开发者和运维人员更好地理解系统内部行为（如缓存命中、请求调度），从而进行性能分析和问题排查。

-   **文档与 CI 改进**：
    -   `[7407a62]`, `[62edbc3]`, `[9c03171]`: 更新了 MiniCPM-V-4.6 的文档、MiMo V2.5 的 cookbook 镜像以及部署指南。
    -   `[893dfb7]`, `[36ba60a]`, `[c027ae6]`, `[ea217a2]`: 更新了 CI 权限配置、注册了新的单元测试、对齐了 CUDA wheel 检查，并移除了一个不再需要的工作流。
    -   **关系**：持续改进文档和 CI 是项目健康发展的基础。这些提交确保了新功能的正确性、文档的时效性以及开发流程的顺畅。

### 3. 对项目的影响和潜在意义

-   **性能与效率**：KV 缓存优化和新的量化内核将直接降低推理延迟和显存占用，对部署高并发、长序列模型的服务至关重要。
-   **生态扩展**：Azure Blob Storage 连接器使 SGLang 能更好地融入 Azure 生态，吸引更多云用户。对 AMD 和 NPU 的持续支持则拓宽了其硬件选择范围。
-   **稳定性与可维护性**：推测解码的 Bug 修复和代码清理提高了核心功能的稳定性。增强的可观测性工具降低了运维和调试的复杂度。
-   **技术领先性**：引入 Cute-DSL 和 NVFP4 等前沿技术，表明项目团队在紧跟硬件和算法发展趋势，致力于提供最先进的推理能力。

### 4. 

## 详细提交记录

### [6c3541a](https://github.com/sgl-project/sglang/commit/6c3541a9145a9f0c28a977726eef3834b9be988a)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-11T22:59:51Z
- **提交信息**: spec: route idle hidden_size via EagleDraft{,Extend}Input classmethods (#25013)

### [ce1736f](https://github.com/sgl-project/sglang/commit/ce1736fcc6cc9a599752199c441a99123f8a3bcf)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-11T21:50:46Z
- **提交信息**: [Spec] Remove dead kernel params; fix stale comment in `trtllm_mla` (#25010)

### [893dfb7](https://github.com/sgl-project/sglang/commit/893dfb7b74bf2baffadbb5da940771c9b42cf55d)

- **作者**: Lianmin Zheng
- **时间**: 2026-05-11T21:44:07Z
- **提交信息**: Add libertyeagle to CI_PERMISSIONS.json (#25011)

### [42bcbc0](https://github.com/sgl-project/sglang/commit/42bcbc00d4282b81aa66d71cdb1fd368cd4a1452)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-11T21:35:34Z
- **提交信息**: [Spec] Drop Rule 5 (`_len` / `_lens` ban) from speculative naming rule (#25012)

### [d3edfb5](https://github.com/sgl-project/sglang/commit/d3edfb579be4a8847b63f431704b43adf383bba0)

- **作者**: Bruce Changlong Xu
- **时间**: 2026-05-11T21:20:22Z
- **提交信息**: [connector] Add Azure Blob Storage connector (az:// and *.blob.core.windows.net URLs) (#23995)

### [da0eeb8](https://github.com/sgl-project/sglang/commit/da0eeb82f2322a868648d5b526a7e3526a880038)

- **作者**: Jia Guo
- **时间**: 2026-05-11T20:10:24Z
- **提交信息**: perf: add --prefill-only-disable-kv-cache to skip KV pool allocation (#23675)

### [c7e53e6](https://github.com/sgl-project/sglang/commit/c7e53e68a270f989f8eb8af562014439d7db0339)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-11T19:25:18Z
- **提交信息**: [Spec] Fix ngram metric off-by-1 in `num_accepted_drafts_per_req_cpu` (#24965)

### [7407a62](https://github.com/sgl-project/sglang/commit/7407a62c1c02b2c1300586f728e65b01141bb98f)

- **作者**: Yihao Wang
- **时间**: 2026-05-11T18:10:19Z
- **提交信息**: [Docs] Update MiniCPM-V-4.6 documentation and deployment configuration (#24991)

### [4b6f776](https://github.com/sgl-project/sglang/commit/4b6f7768894b5707d0ab19d6b727950096f15f75)

- **作者**: Yan Ru Pei
- **时间**: 2026-05-11T17:31:45Z
- **提交信息**: feat(kv-events): publish SWA radix cache events (#24718)

Signed-off-by: PeaBrane <yanrpei@gmail.com>

### [95985f9](https://github.com/sgl-project/sglang/commit/95985f983d27df175f3e80351a6748e2fd77a15a)

- **作者**: Tianhe
- **时间**: 2026-05-11T17:31:03Z
- **提交信息**: feat(trace): support SGLANG_TRACE_LEVEL env var for startup trace level (#24716)

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [2e69266](https://github.com/sgl-project/sglang/commit/2e69266f845fd15cd35e692a07d11c8e0c17067b)

- **作者**: Bingxu Chen
- **时间**: 2026-05-11T15:05:16Z
- **提交信息**: [AMD] avoid aiter re-installing triton in amd_install_dependency (#24981)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [aeb8fef](https://github.com/sgl-project/sglang/commit/aeb8fefc25ae9b75ac07d74bc399c6e26ab4ff67)

- **作者**: Bingxu Chen
- **时间**: 2026-05-11T14:32:13Z
- **提交信息**: [AMD] Pin cache-dit==1.3.0 in rocm.Dockerfile + AMD CI install script (#24924)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [d9cb380](https://github.com/sgl-project/sglang/commit/d9cb38012ee7272afad75b37f5031d7b9f858952)

- **作者**: Ke Bao
- **时间**: 2026-05-11T14:04:31Z
- **提交信息**: Update MiMo V2.5 cookbook image to nightly (#24983)

### [62edbc3](https://github.com/sgl-project/sglang/commit/62edbc37c4b05dec8c102bff2606dac7781c788d)

- **作者**: Ke Bao
- **时间**: 2026-05-11T13:30:01Z
- **提交信息**: [Doc] Add rerun-test slash command usage (#24979)

### [9c03171](https://github.com/sgl-project/sglang/commit/9c03171f6c3ded56281622aefd6564e9ef538444)

- **作者**: Ke Bao
- **时间**: 2026-05-11T13:06:02Z
- **提交信息**: Fix gb envs in deployment guide (#24977)

### [36ba60a](https://github.com/sgl-project/sglang/commit/36ba60ad49bcd00a0b38924c30b35551c5c27923)

- **作者**: Ke Bao
- **时间**: 2026-05-11T12:21:05Z
- **提交信息**: Register SWA unit tests under unit/mem_cache (#24974)

### [6b6963f](https://github.com/sgl-project/sglang/commit/6b6963f42646e1e8e19cd5b3f2c6e8c0636f1b87)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-05-11T10:47:09Z
- **提交信息**: [AMD] Update scripts/ci/amd/ensure_vram_clear.sh (#24586)

### [6d30b57](https://github.com/sgl-project/sglang/commit/6d30b571b2a6998003cd13d0f538321a471ab7d7)

- **作者**: Mick
- **时间**: 2026-05-11T10:09:24Z
- **提交信息**: [diffusion] fix: fix single-step flow-match timesteps (#24708)

### [c027ae6](https://github.com/sgl-project/sglang/commit/c027ae677c3f5b8f8ce1fc26104f8eb89373095d)

- **作者**: Hank Han
- **时间**: 2026-05-11T08:22:20Z
- **提交信息**: ci: align torch CUDA wheel checks (#24940)

### [f7ba136](https://github.com/sgl-project/sglang/commit/f7ba1362797dc4d5869409dd27ffdf65de895fef)

- **作者**: monkeyLoveding
- **时间**: 2026-05-11T08:13:39Z
- **提交信息**: [NPU] bump sgl-kernel-npu version to 2026.05.01 (#24951)

### [df441b8](https://github.com/sgl-project/sglang/commit/df441b8feae3fced0175fda3c7decb02e0ee32de)

- **作者**: iridiumine
- **时间**: 2026-05-11T07:50:15Z
- **提交信息**: [NPU] Support shared expert dual stream optimization (#23827)

Co-authored-by: iridiumine <iridiumine@users.noreply.github.com>

### [1df9edc](https://github.com/sgl-project/sglang/commit/1df9edcd015dba4ce30864a3202c74a7ffe6a356)

- **作者**: Brayden Zhong
- **时间**: 2026-05-11T07:41:05Z
- **提交信息**: Use Torch `torch.mm` for Deepseek V3.2 Indexer GEMM (#23856)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [1d80a1a](https://github.com/sgl-project/sglang/commit/1d80a1a9fe6d6611cf55abb3a72767603d3db666)

- **作者**: Brayden Zhong
- **时间**: 2026-05-11T07:40:02Z
- **提交信息**: Use Cute-DSL NVFP4 quantization kernels (#23745)

Co-authored-by: b8zhong <b8zhong@users.noreply.github.com>

### [ea217a2](https://github.com/sgl-project/sglang/commit/ea217a2bf03345408b03e1f3a54ed083dd14a34b)

- **作者**: Baizhou Zhang
- **时间**: 2026-05-11T07:26:32Z
- **提交信息**: ci: remove Execute Notebooks workflow (#24460)

### [044bb88](https://github.com/sgl-project/sglang/commit/044bb88a97469f7977a2f710b89f4ee066c3c9ca)

- **作者**: Cheng Wan
- **时间**: 2026-05-11T07:07:46Z
- **提交信息**: fix: SGLANG_RADIX_FORCE_MISS chunk-cache passthrough (#24950)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1167
- **最后更新**: 2026-05-11T16:48:55Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能增强/基础设施改进**：本次提交属于对项目分布式执行能力的增强，而非直接的Bug修复或性能优化。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在Ray（一个分布式计算框架）中，将运行时环境（runtime env）传递给工作节点（workers）。
- **与项目方向的关系**：`cache-dit` 是一个面向Diffusion Transformers的PyTorch原生推理引擎，其核心卖点包括**并行性（Parallelism）**。Ray是实现分布式并行计算的关键基础设施。此提交通过确保工作节点能正确接收运行时环境配置（如Python依赖、环境变量等），使得Ray集群的部署和扩展更加可靠和灵活，直接支撑了项目的“并行性”目标。

### 3. 对项目的影响和潜在意义
- **影响**：修复了在复杂或异构的Ray集群环境中，工作节点可能因缺少正确的运行时环境而启动失败或行为异常的问题。
- **潜在意义**：
    - **提升部署可靠性**：使得用户在多机多卡、不同操作系统或依赖环境的集群上部署`cache-dit`进行大规模推理时，体验更稳定。
    - **简化用户操作**：用户无需手动在每个节点上配置环境，Ray可以自动分发环境，降低了分布式推理的使用门槛。
    - **为更大规模并行铺路**：稳定的Ray集成是未来支持更大规模模型并行、数据并行或流水线并行的基础。

### 4. 值得关注的技术点
- **Ray Runtime Environment**：这是Ray提供的一个强大功能，允许用户为每个任务或Actor指定独立的Python环境、文件、环境变量等。`cache-dit` 利用此功能，意味着其分布式推理任务可能依赖于特定的Python包（如特定版本的`torch`、`diffusers`等），通过`runtime env`可以确保所有工作节点使用一致的依赖，避免“环境不一致”导致的错误。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化核心优势**：`cache-dit` 的定位是“带缓存、并行、量化的Diffusion Transformers推理引擎”。本次提交直接强化了“并行”这一核心优势的底层基础设施，使其在分布式场景下更健壮。
- **提升企业级可用性**：VIPShop（唯品会）作为电商公司，其内部推理服务通常需要高可用、可扩展的分布式部署。此提交使`cache-dit`更符合企业级生产环境的要求，能更好地服务于大规模、高并发的图像生成任务。
- **吸引社区用户**：对于希望利用多GPU或集群加速Diffusion Transformers推理的研究者和开发者来说，一个稳定、易用的Ray集成是重要的吸引力。此更新降低了分布式部署的痛点，有助于项目获得更广泛的社区采用。

## 详细提交记录

### [97d1e4b](https://github.com/vipshop/cache-dit/commit/97d1e4b903048fae4ca2f39c79930a0b9f7030fe)

- **作者**: DefTruth
- **时间**: 2026-05-11T11:05:46Z
- **提交信息**: ray: pass runtime env to workers (#1007)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 79691
- **最后更新**: 2026-05-11T23:05:12Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 24
- **主要提交者**: Jeffrey Wang, wang.yuqi, Thien Tran

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复 (Bugfix):** 占比最高，共10项。涉及数据类型溢出、模型加载、量化算法、NCCL进程管理、KVCache布局等多个方面。
- **性能优化 (Perf):** 共5项。包括消除GPU-CPU同步、Cutlass FP8支持、算子融合（RMSNorm+Quant, RoPE+KVCache）等。
- **文档更新 (Docs):** 共2项。新增了Apple Silicon (Metal) 支持和FIPS合规性文档。
- **重构 (Refactor):** 共2项。清理了Batch Invariance相关的死代码，并重构了KV Offloading的管理器逻辑。
- **功能新增/增强 (Feature/Enhancement):** 共3项。包括DSv4的Flash Sparse MLA实现、Frontend API支持`chat_template_kwargs`、以及NIXL的Lease Renewal机制。
- **CI/测试改进 (CI/Test):** 共3项。整合了语音转文本测试，并将parser测试纳入CI覆盖范围。

### 2. 关键变更点及其与项目整体方向的关系

- **性能与效率 (Performance & Efficiency):** 这是本次更新的核心主题。
    - **[Perf] 消除GPU-CPU同步 (bbee532):** 直接减少延迟，提升吞吐量，符合vLLM“快速、廉价”的核心目标。
    - **[Perf] Cutlass FP8支持 (0d453e2):** 宣称有28.9%的端到端延迟改进，这是对FP8推理能力的重大增强，直接提升了vLLM在高端硬件上的竞争力。
    - **[Perf] 算子融合 (a721315, a51376b):** 通过融合RMSNorm+Quant、RoPE+KVCache等操作，减少了显存访问和内核启动开销，是典型的性能优化手段。
    - **[Bugfix] DeepGEMM FP8 Triton内核溢出 (6fdb493):** 修复了FP8计算中的关键bug，确保了新性能特性的正确性。
- **模型支持与兼容性 (Model Support & Compatibility):**
    - **[Bugfix] DSv4 Marlin后端 (5318138):** 修复了DeepSeek V4模型在特定量化后端上的问题，扩展了对前沿模型的支持。
    - **[Bugfix] EXAONE-4.5对齐 (27ae676):** 保持与上游Transformers库的同步，确保模型加载的兼容性。
    - **[Bugfix] Kimi dtype问题 (3f9c0c2):** 修复了特定模型（Kimi）的`mm_projector_forward`问题，体现了对多模态模型的支持。
    - **[Bugfix] Nemotron Nano VL权重损坏 (ac06214):** 修复了与特定加载器（如Runai）的兼容性问题，增强了在复杂部署环境下的稳定性。
- **稳定性与可靠性 (Stability & Reliability):**
    - **[BugFix] NCCL孤儿进程 (56e5810):** 修复了可能导致资源泄漏或进程残留的关键问题，提升了分布式推理的健壮性。
    - **[Bugfix] NIXL握手失败策略 (5672d10):** 确保在PD分离部署中，当KV传输失败时能优雅降级（重计算），而非直接崩溃，增强了系统的容错能力。
    - **[Bugfix] Model Runner V2日志类型 (d7af6b3):** 修复了logprob的数据类型问题，确保了日志和调试信息的准确性。
- **硬件平台扩展 (Hardware Platform Expansion):**
    - **[ROCm] 多项优化与修复 (a721315, 7863fff, 5f1b313):** 持续为AMD ROCm平台提供性能优化（如gfx950）和新功能（如DSv4 Flash Sparse MLA），表明vLLM正积极扩大对非NVIDIA硬件的支持。
    - **[Docs] Apple Silicon支持 (cf0d279):** 为Mac用户提供官方文档，降低了本地开发和测试的门槛，扩大了用户基础。
- **架构演进 (Architecture Evolution):**
    - **[Refactor] 清理Batch Invariance死代码 (4b64fc2):** 结合性能优化提交，表明vLLM正在重构其核心调度和执行逻辑，向更高效的“Batch Invariance”模式演进。
    - **[kv_offload] 重构与优化 (4955990, 8415bf2):** 持续优化KV Cache卸载功能，这对于支持超长上下文和超大模型至关重要。

### 3. 对项目的影响和潜在意义

- **性能提升是主旋律:** 多项性能优化（特别是Cutlass FP8和消除同步）将直接转化为用户可感知的更低延迟和更高吞吐量，巩固vLLM作为高性能推理引擎的地位。
- **稳定性和鲁棒性增强:** 大量Bug修复，尤其是在分布式和PD分离场景下的修复，将显著提升vLLM在生产环境中的可靠性，降低运维成本。
- **生态兼容性扩展:** 对AMD ROCm、Apple Silicon、以及各种新兴模型（DSv4, EXAONE, Kimi）的支持，使vLLM的生态系统更加多元化，吸引更广泛的用户和开发者。
- **架构持续演进:** 对Batch Invariance和KV Offloading的重构，表明vLLM正在为未来更大规模、更长上下文的模型推理场景做准备。

### 4. 值得关注的技术点

-

## 详细提交记录

### [d7af6b3](https://github.com/vllm-project/vllm/commit/d7af6b34d83fc691ad69347ee4d066231e5678ab)

- **作者**: Wentao Ye
- **时间**: 2026-05-11T21:55:43Z
- **提交信息**: [Model Runner V2] Bug fix: logprob dtype int64/int32 issue (#41761)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bbee532](https://github.com/vllm-project/vllm/commit/bbee5329880bfe45a8b0cf7753d17501760e62c9)

- **作者**: Nick Hill
- **时间**: 2026-05-11T20:36:03Z
- **提交信息**: [Perf][1/n] Eliminate various GPU<->CPU syncs (#41429)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5318138](https://github.com/vllm-project/vllm/commit/53181384e036cc660ff6754c8a94a8e6d0b60562)

- **作者**: Jee Jee Li
- **时间**: 2026-05-11T20:03:56Z
- **提交信息**: [Bugfix] Fix DSV4 swiglu_limit on marlin backend (#42287)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [a0dc7a0](https://github.com/vllm-project/vllm/commit/a0dc7a0f368a3f212d37e39ba4dd7b682e378fe2)

- **作者**: wang.yuqi
- **时间**: 2026-05-11T19:50:17Z
- **提交信息**: [CI] Consolidate Speech to Text tests (#42274)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [56e5810](https://github.com/vllm-project/vllm/commit/56e5810ff168bb13695d35fba2c7401256afdda4)

- **作者**: Jeffrey Wang
- **时间**: 2026-05-11T19:25:26Z
- **提交信息**: [BugFix] Prevent orphaned process on NCCL destroy (#39846)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>
Co-authored-by: Tyler Michael Smith <tyler@neuralmagic.com>

### [639cbfd](https://github.com/vllm-project/vllm/commit/639cbfd27428632f2851b46a9d70779e73bccbb3)

- **作者**: Flora Feng
- **时间**: 2026-05-11T19:08:54Z
- **提交信息**: [CI] Add tests/parser to CI coverage (#41877)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [a721315](https://github.com/vllm-project/vllm/commit/a721315488429e728e25adabb6d94c35a4770b94)

- **作者**: frida-andersson
- **时间**: 2026-05-11T19:00:51Z
- **提交信息**: [ROCm][Perf] Fix RMSNorm+Quant fusion for gfx950 (non-fnuz) (#41825)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Signed-off-by: Chuan Li <chuali@amd.com>
Co-authored-by: Markus Hartikainen <markus.hartikainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Chuan Li <chuali@amd.com>
Co-authored-by: Luka Govedič <ProExpertProg@users.noreply.github.com>
Co-authored-by: Frida Andersson <frida-andersson@users.noreply.github.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [6fdb493](https://github.com/vllm-project/vllm/commit/6fdb49392e5183c310c4703b883e7edbf25f6a96)

- **作者**: Vensen
- **时间**: 2026-05-11T18:52:31Z
- **提交信息**: [Bugfix] Fix int32 overflow in DeepGEMM SiLU/mul FP8 Triton kernel (#42201)

Signed-off-by: vensen <vensenmu@gmail.com>
Signed-off-by: Vensen <vensenmu@gmail.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [cf0d279](https://github.com/vllm-project/vllm/commit/cf0d2791420eefab4a3416551bb3f4a1288f0aea)

- **作者**: Alexa Griffith
- **时间**: 2026-05-11T18:34:25Z
- **提交信息**: [Docs] Add Apple Silicon documentation for vLLM-Metal GPU support (#41987)

Signed-off-by: alexagriffith <agriffith96@gmail.com>
Co-authored-by: Claude Sonnet 4.5 <noreply@anthropic.com>

### [5497ffb](https://github.com/vllm-project/vllm/commit/5497ffbf7c078550c18566cc76ab9bae86ad0496)

- **作者**: Vinay R Damodaran
- **时间**: 2026-05-11T18:17:02Z
- **提交信息**: Add documentation about vLLM FIPS compliance (#42190)

Signed-off-by: Vinay Damodaran <vrdn@hey.com>
Signed-off-by: Vinay R Damodaran <vrdn@hey.com>
Co-authored-by: Russell Bryant <russell.bryant@gmail.com>

### [9af6a5e](https://github.com/vllm-project/vllm/commit/9af6a5ed75bbb095c3e7e78b807ca0fe29ef90bb)

- **作者**: Nick Hill
- **时间**: 2026-05-11T17:37:50Z
- **提交信息**: [Model Runner V2] Fix `seq_lens_cpu_upper_bound` (#42202)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [7863fff](https://github.com/vllm-project/vllm/commit/7863fff6e591161a03a7df68b0879b9fa61cfc0b)

- **作者**: Hexiang Wang
- **时间**: 2026-05-11T16:27:11Z
- **提交信息**: [ROCm][DSv4] implement flash sparse mla with triton kernels (#41812)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>

### [0d453e2](https://github.com/vllm-project/vllm/commit/0d453e23364701f6fe2f20deafbb372b28714a86)

- **作者**: Wentao Ye
- **时间**: 2026-05-11T16:20:58Z
- **提交信息**: [Perf] Batch invariance with Cutlass fp8 support, 28.9% E2E latency improvement (#40408)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [3f9c0c2](https://github.com/vllm-project/vllm/commit/3f9c0c25b3312c6b9e9fa70c4b9849eb53a335ba)

- **作者**: Wentao Ye
- **时间**: 2026-05-11T15:45:24Z
- **提交信息**: [Bug] Fix kimi dtype issue with `mm_projector_forward` (#42081)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [a2e776d](https://github.com/vllm-project/vllm/commit/a2e776d7168e1a75fe32438aea4254542602c012)

- **作者**: Vadim Gimpelson
- **时间**: 2026-05-11T15:10:57Z
- **提交信息**: [Bugfix] Accept canonicalized `modelopt_*` quant_method in `_extract_modelopt_quant_algo` (#42181)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [4955990](https://github.com/vllm-project/vllm/commit/4955990f1bd91e5d6070a56ad3ed9684a23e5146)

- **作者**: Martin Hickey
- **时间**: 2026-05-11T15:09:29Z
- **提交信息**: [kv_offload] Move `FilterReusedOffloadingManager` logic to `CPUOffloadingManager` (#41727)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [4b64fc2](https://github.com/vllm-project/vllm/commit/4b64fc2cbf2a10c0027f7c80681af0ede0c3799a)

- **作者**: Wentao Ye
- **时间**: 2026-05-11T14:48:39Z
- **提交信息**: [Refactor] Cleanup batch invariant dead code (#41993)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [5f1b313](https://github.com/vllm-project/vllm/commit/5f1b313900fd5375857bdb7f709e1c5aad54443c)

- **作者**: pschlan-amd
- **时间**: 2026-05-11T14:45:18Z
- **提交信息**: [ROCm] Clean up a bit the AITER FA backend (#41942)

Signed-off-by: Patrick Schlangen <pschlan@amd.com>

### [724ed2f](https://github.com/vllm-project/vllm/commit/724ed2fc352bb388aea7269ca5c6690637c30ce7)

- **作者**: Thien Tran
- **时间**: 2026-05-11T14:41:12Z
- **提交信息**: [DSv4] Improved dequant gather K cache kernel (#42236)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [a51376b](https://github.com/vllm-project/vllm/commit/a51376b3f05a2f74eac6ceeed7e52598b871a0fb)

- **作者**: Rohan Potdar
- **时间**: 2026-05-11T14:10:50Z
- **提交信息**: [Performance][DSR1]: Fused RoPE+KVCache+q_concat for MLA (#40392)

Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Signed-off-by: Rohan Potdar <66227218+Rohan138@users.noreply.github.com>
Co-authored-by: ElizaWszola <ewszola@redhat.com>

### [8415bf2](https://github.com/vllm-project/vllm/commit/8415bf2cdbdd00c1786abb766df568d5ae19e2c0)

- **作者**: Martin Hickey
- **时间**: 2026-05-11T12:05:41Z
- **提交信息**: [kv_offload] Set offloading connector to prefer HND layout (#41928)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [ac06214](https://github.com/vllm-project/vllm/commit/ac062147fae75e482e1fd0b2930746678253d7bb)

- **作者**: Noa Neria
- **时间**: 2026-05-11T12:03:14Z
- **提交信息**: Avoid silent weights corruption when loading Nemotron Nano VL with reusable-buffer loaders like runai distributed streaming (#42244)

Signed-off-by: Noa Neria <nneria@nvidia.com>

### [617239b](https://github.com/vllm-project/vllm/commit/617239b70c46d3d53fc16619718da1c347c43fb6)

- **作者**: Chauncey
- **时间**: 2026-05-11T11:59:39Z
- **提交信息**: [Frontend]Responses API supports chat_template_kwargs (#42272)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [27ae676](https://github.com/vllm-project/vllm/commit/27ae6763647920119dcd50d147ca365fdc138945)

- **作者**: Kyungmin Lee
- **时间**: 2026-05-11T10:25:31Z
- **提交信息**: Fix EXAONE-4.5 to align with Transformers update (#42246)

Signed-off-by: lkm2835 <lkm2835@gmail.com>

### [17ed5e6](https://github.com/vllm-project/vllm/commit/17ed5e61f51ffa3bd14a5eb202439fb87892e421)

- **作者**: haosdent
- **时间**: 2026-05-11T09:47:16Z
- **提交信息**: [CI] Make Python-only Installation optional (#42293)

Signed-off-by: haosdent <haosdent@gmail.com>

### [5672d10](https://github.com/vllm-project/vllm/commit/5672d100ed66490b84ea54b030b0785a6d20d111)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-11T09:37:21Z
- **提交信息**: [KV Connector][NIXL][Bugfix] Fix NIXL handshake failures not honoring kv_load_failure_policy (#40364)

When NIXL handshake fails (e.g., due to compatibility hash mismatch
between prefill and decode instances), requests fail with "engine dead"
error instead of gracefully falling back to local recomputation as configured
by kv_load_failure_policy='recompute'.

Signed-off-by: NickLucche <nlucches@redhat.com>

### [770e9bd](https://github.com/vllm-project/vllm/commit/770e9bd6b3519e8a6fa5738877974af274ec946e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-05-11T09:27:30Z
- **提交信息**: [Nixl][PD] Lease renewal TTL KV blocks on P (#41383)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [9efdddc](https://github.com/vllm-project/vllm/commit/9efdddca283cc0eb7c37fa49c4a9d1c9bf59ec4e)

- **作者**: Cyrus Leung
- **时间**: 2026-05-11T09:04:06Z
- **提交信息**: [Model] Fix missing `maybe_prefix` (#42280)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [b1b5972](https://github.com/vllm-project/vllm/commit/b1b59720b252b422368deb99aadc888fb397db40)

- **作者**: Qiu
- **时间**: 2026-05-11T08:11:49Z
- **提交信息**: bugfix(flashinfer,dcp): remove kv_cache_layout for BatchDCPPrefillWrapper._new_tokens. (#38895)

Signed-off-by: QiuChunshuo <qiuchunshuo@huawei.com>

### [f9f770c](https://github.com/vllm-project/vllm/commit/f9f770ca0b02f8b83ae92997a68efa797611ce36)

- **作者**: shaharmor98
- **时间**: 2026-05-11T07:40:37Z
- **提交信息**: fix nixl side-channel host selection (#41806)

Signed-off-by: Shahar Mor <smor@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-12
**监控日期**: 2026-05-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4688
- **最后更新**: 2026-05-11T19:29:52Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: ChenWenjing, wuhang, wangyu

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **Bug修复**：3项（#3417, #3460, #3500）
- **性能优化**：1项（#3296）
- **新模型支持**：1项（#3319）
- **配置更新**：1项（#3172）
- **CI/测试**：2项（#3507, #3417）
- **杂项/清理**：1项（#3414）

### 2. 关键变更点及其与项目整体方向的关系

- **新模型支持 (Sensenova U1)**：新增了对 `sensenova u1` 模型的支持。这直接契合了项目“为所有人提供**简单、快速、廉价的全模态模型服务**”的核心目标，通过持续扩展支持的模型生态，增强平台的通用性和吸引力。
- **性能优化 (Qwen3-Omni)**：在Qwen3-Omni模型的“说话者”阶段移除了未使用的 `audio_tower` 和 `visual` 组件。这是对现有模型服务的**精细化性能调优**，通过消除冗余计算来提升推理速度和降低资源消耗，符合“快速、廉价”的承诺。
- **Bug修复**：
    - **Whisper转录去重**：修复了实时音频测试中Whisper转录可能出现的重复问题，提升了**实时音频处理**的稳定性和准确性，这对于支持语音交互的全模态服务至关重要。
    - **RMSNorm Inductor KeyError**：修复了在HSDP（分层数据并行）+ `torch.compile` 场景下的RMSNorm错误。这解决了在**大规模分布式部署**和**编译优化**下的兼容性问题，对提升项目在高性能计算环境下的稳定性有重要意义。
    - **HunyuanImage 3.0 编码行为**：修复了HunyuanImage 3.0模型在线和离线模式下不同宽高比（AR）编码行为不一致的问题。这确保了**图像生成任务**在不同服务模式下行为的一致性，提升了用户体验和模型的可预测性。
- **配置更新 (HunyuanImage3)**：为HunyuanImage3模型添加了部署配置。这是支持新模型（#3172）的配套工作，使得该模型能够被顺利部署和服务。
- **CI/测试**：跳过了部分失败的扩散模型和精度测试用例。这是一种**务实的项目管理**策略，旨在保持CI管道的绿色和高效，避免被已知的、非关键性的失败阻塞开发流程，同时为后续修复争取时间。
- **杂项/清理 (图像生成日志)**：清理了图像生成任务的日志。这属于**代码质量和可维护性**的提升，通过减少不必要的日志输出来降低I/O开销和提升调试体验。

### 3. 对项目的影响和潜在意义

- **提升稳定性和可靠性**：多个Bug修复（特别是Whisper去重、HunyuanImage行为一致性）直接提升了关键功能的稳定性和可靠性，这对于一个面向生产环境的服务框架至关重要。
- **增强性能和可扩展性**：Qwen3-Omni的性能优化和RMSNorm的修复，分别从单模型推理和分布式训练/推理两个层面提升了性能，有助于项目在更大规模、更复杂的场景下保持高效。
- **丰富模型生态**：新增Sensenova U1模型支持，持续扩大项目支持的模型范围，增强了项目作为“全模态模型服务”平台的竞争力。
- **优化开发流程**：CI的调整和日志清理，体现了项目在维护和开发效率上的持续投入，有助于保持开发节奏的健康。

### 4. 值得关注的技术点

- **HSDP + torch.compile**：修复RMSNorm在HSDP和 `torch.compile` 下的错误，表明项目正在积极拥抱并解决前沿分布式训练和编译优化技术带来的挑战。
- **实时音频测试**：对Whisper转录去重的修复，暗示项目在实时音频流处理方面有较高的质量要求，这是全模态服务中一个复杂且关键的技术领域。
- **模型特定优化**：针对Qwen3-Omni的“说话者”阶段进行优化，体现了项目对不同模型架构的深入理解，并能进行模型级别的精细调优，而非仅仅提供通用框架。

### 5. 结合项目背景，这些提交如何影响项目发展

基于README中“**为所有人提供简单、快速、廉价的全模态模型服务**”的愿景，昨日的更新从多个维度推动了项目发展：

- **“快速、廉价”**：通过移除Qwen3-Omni的冗余组件进行性能优化，直接降低了推理成本和时间。
- **“全模态”**：通过修复Whisper（音频）和HunyuanImage（图像）的Bug，以及新增Sensenova U1（推测为多模态）模型，巩固和扩展了项目在**音频、图像、文本**等多模态领域的服务能力。
- **“为所有人”**：通过修复分布式部署（HSDP）下的兼容性问题，降低了大规模部署的门槛；通过清理日志和优化CI，提升了开发者和维护者的体验。
- **“简单”**：通过修复在线/离线行为不一致的Bug，使得用户在不同使用场景下获得一致的体验，降低了使用复杂度。

总而言之，昨日的更新是一次**务实且全面**的迭代，在**扩展能力**（新模型）的同时，重点**夯实了基础**（修复Bug、优化性能、提升稳定性），这正是一个成熟的开源项目在快速发展期应有的节奏。

## 详细提交记录

### [4bca522](https://github.com/vllm-project/vllm-omni/commit/4bca522f01ca49f04bb9a6cfa14c7c8839013b0c)

- **作者**: ChenWenjing
- **时间**: 2026-05-11T17:09:10Z
- **提交信息**: [bugfix][ci] avoid Whisper transcript deduplication in realtime audio test (#3417)

Signed-off-by: CHEN <116010019@link.cuhk.edu.cn>

### [bd4ede3](https://github.com/vllm-project/vllm-omni/commit/bd4ede391b58295335061102fb534007e3e149af)

- **作者**: Nick Cao
- **时间**: 2026-05-11T16:04:56Z
- **提交信息**: [Perf] Remove dead audio_tower and visual from Qwen3-Omni talker stage (#3296)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6be59f7](https://github.com/vllm-project/vllm-omni/commit/6be59f7d19e11427605a727ff5142c980c9ae19c)

- **作者**: Junhong Liu
- **时间**: 2026-05-11T14:56:54Z
- **提交信息**: [Fix] Fix RMSNorm inductor KeyError under HSDP + torch.compile (#3460)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>

### [a33e2eb](https://github.com/vllm-project/vllm-omni/commit/a33e2eb5885472e4a87f9c431a7792967046fcb1)

- **作者**: Y. Fisher
- **时间**: 2026-05-11T14:49:19Z
- **提交信息**: [Config] Add HunyuanImage3 deploy configs (#3172)

Signed-off-by: KexiongYu <yukexiong1@huawei.com>
Signed-off-by: Y. Fisher <yukexiong1@huawei.com>

### [c9a8556](https://github.com/vllm-project/vllm-omni/commit/c9a8556c24ade154b09b55a39acd36a1697a1f1f)

- **作者**: 汪志鹏
- **时间**: 2026-05-11T14:19:00Z
- **提交信息**: [New Model]: Add sensenova u1 support (#3319)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [2cdffce](https://github.com/vllm-project/vllm-omni/commit/2cdffcea6b0117216f29ba329bebda814d090645)

- **作者**: wangyu
- **时间**: 2026-05-11T13:56:08Z
- **提交信息**: [CI] skip failing diffusion and accuracy cases (#3432, #3256, #3257, #3488) (#3507)

Signed-off-by: wangyu <410167048@qq.com>

### [3f27ffb](https://github.com/vllm-project/vllm-omni/commit/3f27ffbd4de71df4bede265bcf4f8212e6bfa07a)

- **作者**: wuhang
- **时间**: 2026-05-11T12:16:05Z
- **提交信息**: [Misc] Clean logs for image gen task (#3414)

Signed-off-by: wuhang <wuhang6@huawei.com>

### [3bf4f28](https://github.com/vllm-project/vllm-omni/commit/3bf4f2850c254c45152e53224b1462a1c450581e)

- **作者**: dengyunyang
- **时间**: 2026-05-11T11:34:58Z
- **提交信息**: [Bug][Hunyuanimage 3.0] fix different AR encode behavior  between online and offline (#3500)

Signed-off-by: dengyunyang <584797741@qq.com>

---
