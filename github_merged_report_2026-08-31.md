# GitHub Stars 合并报告 - 2026-08-31

**合并日期**: 2026-09-01
**监控日期**: 2026-08-31
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


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2181
- **最后更新**: 2026-08-31T22:16:15Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

# 提交分析：5767a56

## 主要更新类型
本次提交属于**重构与文档更新**，同时带有**破坏性变更（BREAKING）**标记，涉及优化器（optim）、配置（config）和文档（docs）三个模块。

## 关键变更点
核心变更为：将head-split Muon优化器模块的命名方式从“DSA索引器标志（DSA indexer flag）”改为**限定名称（qualified names）**。这意味着模块标识不再依赖一个单独的索引标志位，而是通过更明确、结构化的命名来区分不同的head-split配置。

## 与项目方向的关系
VeOmni的核心目标是构建“以模型为中心的分布式训练配方库”，支持任意模态模型的规模化训练。Muon优化器是近年在大模型训练中备受关注的自适应优化器变体，而head-split（头部分裂）是一种针对多模态或多头架构的并行策略。此次重构直接服务于**训练配方的可扩展性和可维护性**——通过更清晰的命名体系，使不同head-split配置的Muon模块能够被更灵活地组合和引用，这与项目“配方库”的核心理念高度一致。

## 对项目的影响与潜在意义
1. **API稳定性影响**：作为破坏性变更，现有依赖DSA索引器标志的配置和代码需要迁移，可能影响下游用户和内部集成。
2. **可扩展性提升**：限定名称机制使得新增head-split变体时无需维护额外的索引映射，降低了配方扩展的复杂度。
3. **可读性与可调试性**：模块名称更具语义化，便于日志输出、配置解析和问题定位。
4. **文档同步更新**：表明项目重视用户引导，破坏性变更伴随文档更新，降低了迁移成本。

## 值得关注的技术点
- **命名即接口**：用限定名称替代索引标志，本质上是将隐式约定（索引→含义）转为显式声明（名称即含义），这是分布式训练框架中提升配置可组合性的常见演进方向。
- **破坏性变更的管理方式**：提交中明确标注BREAKING，并同步更新文档，体现了规范的版本管理意识。
- **AI辅助开发**：提交由Cursor agent协作完成，反映了AI工具在大型开源项目中的实际应用。

## 对项目发展的影响
从VeOmni的定位来看，此次提交是**基础设施层面的打磨**。它不引入新功能，但通过改善模块命名体系，为后续更多优化器变体和并行策略的“配方”入库铺平了道路。随着多模态模型训练对灵活并行策略的需求增长，这种结构化的模块管理能力将成为项目竞争力的重要组成部分。整体而言，这是一次“内功修炼”型提交，短期带来迁移成本，长期提升项目可扩展性和生态友好度。

## 详细提交记录

### [5767a56](https://github.com/ByteDance-Seed/VeOmni/commit/5767a56a7daafe7d640663f3639254ad06fd02fb)

- **作者**: Bin Jia
- **时间**: 2026-08-31T07:25:11Z
- **提交信息**: [BREAKING][optim, config, docs] feat: qualify head-split Muon module names instead of a DSA indexer flag (#1108)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2757
- **最后更新**: 2026-09-01T00:42:52Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 4
- **主要提交者**: PengGao, Bilang ZHANG, STwangyingrui

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交涵盖**Bug修复**（SeedVR分布式导出恢复）、**CI流程优化**（避免重复和变异lint运行）、**性能优化**（Ulysses FP8预量化行分块）、以及**大规模重构**（ERNIE、Flux2、Hunyuan、Wan等多个模型的runner统一）。

### 2. 关键变更点与项目方向的关系
- **SeedVR修复**：恢复四个分布式操作导出，解决BF16和FP8推理在加载权重前的ImportError，直接保障了高分辨率（1920x1080）视频生成任务的可用性。
- **CI优化**：调整lint触发策略，避免重复运行，提升开发效率。
- **FP8性能优化**：通过block_m=8多行处理减少Triton程序启动开销，提升QKV和注意力输出的HBM效率，且不改变量化语义。
- **Runner统一重构**：将多个模型的蒸馏runner合并到基础runner中，简化代码架构，减少维护成本。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：SeedVR修复直接解决推理阻断问题，确保BF16和FP8两种精度模式均可正常运行。
- **性能增益**：FP8预量化优化降低通信开销，对长序列、高分辨率视频生成场景有显著加速效果。
- **架构简化**：多个runner统一重构减少代码冗余，降低新模型接入门槛，提升项目可维护性。
- **开发效率**：CI流程优化减少无效计算资源消耗，加快迭代速度。

### 4. 值得关注的技术点
- **序列并行实现**：SeedVR分布式操作导出路由到序列并行实现，同时保留单GPU无操作行为，体现框架对多卡和单卡场景的兼容设计。
- **FP8预量化行分块**：在保持per-row scale粒度的前提下，通过block_m=8多行处理平衡计算效率和量化精度，是Triton内核优化的典型实践。
- **Intel XPU支持**：启用torch.compile并新增SP×TP块CPU卸载配置，扩展了硬件适配范围。

### 5. 对项目发展的影响
LightX2V作为轻量视频生成推理框架，本批次提交体现了**成熟度提升**和**生态扩展**两个方向。一方面，通过修复关键bug和优化性能，增强了框架在高分辨率、长序列场景下的实用性；另一方面，通过runner统一和硬件适配（Intel XPU），降低了使用门槛并扩大了潜在用户群。这些变更共同推动项目向**更稳定、更高效、更易用**的方向发展，为后续支持更多视频生成模型和推理场景奠定基础。

## 详细提交记录

### [2ea24fe](https://github.com/ModelTC/LightX2V/commit/2ea24fe794f3bc488d9cd9473cc97d6094bbf00f)

- **作者**: PengGao
- **时间**: 2026-08-31T11:57:20Z
- **提交信息**: fix(seedvr): restore distributed ops exports (#1462)

## Summary
- restore the four SeedVR distributed-op exports removed by #1345
- route existing SeedVR inference imports to the sequence-parallel
implementations
- preserve single-GPU no-op behavior

## Validation
- SeedVR source imports pass in the CUDA runtime
- single-GPU semantics verified for all four exports
- full SeedVR2 3B BF16 inference passed (305-frame input, 1920x1080
output)
- full SeedVR2 3B FP8 inference passed (305-frame input, 1920x1080
output)

Without this change, both BF16 and FP8 fail before loading weights with
ImportError for gather_heads_scatter_seq.

### [7d6df66](https://github.com/ModelTC/LightX2V/commit/7d6df6659a332ce09d43860eef5321e7dc7e36ed)

- **作者**: PengGao
- **时间**: 2026-08-31T11:23:59Z
- **提交信息**: ci: avoid duplicate and mutating lint runs (#1463)

## Summary
- run the push-triggered lint workflow only for main
- keep pull_request linting for feature branches
- remove Ruff --fix from pre-commit so CI reports violations without
rewriting files

## Trigger behavior
- feature branch with PR: one pull_request lint run
- direct push to main: one push lint run
- merged PR: a pull_request run before merge and a main push run after
merge

## Validation
- both YAML files parse successfully
- git diff --check passes
- GitNexus change scan: 2 config files, 0 code symbols, LOW risk

### [6f3c491](https://github.com/ModelTC/LightX2V/commit/6f3c491bbf73ddf113f3da95da7e96f5a0649dd0)

- **作者**: STwangyingrui
- **时间**: 2026-08-31T10:57:55Z
- **提交信息**: Optimize Ulysses FP8 pre-quant row tiling (#1304)

Optimize Ulysses FP8 communication pre-quant kernels by processing
multiple rows per Triton program with block_m=8 while preserving per-row
scale granularity.

This reduces launch work and improves HBM efficiency for both QKV and
attention-output pre-quant paths without changing quantization
semantics.

### [d6cf4f1](https://github.com/ModelTC/LightX2V/commit/d6cf4f13d152e636ae6daac604d46531077e8670)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-31T08:35:21Z
- **提交信息**: refactor(ernie): remove redundant Turbo runner alias (#1459)

### [a90b940](https://github.com/ModelTC/LightX2V/commit/a90b940fdab8bfc9dd94b593bc760a835b4c58e5)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-31T08:23:26Z
- **提交信息**: refactor(flux2): unify runners and fix CFG encoding (#1458)

### [6a3d442](https://github.com/ModelTC/LightX2V/commit/6a3d44211f61e2931a810573a885ce116be2d9d8)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-31T07:39:38Z
- **提交信息**: refactor(hunyuan): merge distilled runner into HunyuanVideo 1.5 (#1457)

### [0a84b22](https://github.com/ModelTC/LightX2V/commit/0a84b22bde8b5cd165bd482b9695c732f2ed0652)

- **作者**: Xin Qiu
- **时间**: 2026-08-31T07:31:47Z
- **提交信息**: [Intel XPU] Enable torch.compile for MiniMax-H3 inference (#1456)

## Summary
- Enable `torch.compile` for 30-step MiniMax-H3 Intel XPU
configurations.
  - Add SP×TP block CPU-offload configuration and launch script.

### [23fc3d4](https://github.com/ModelTC/LightX2V/commit/23fc3d455df1c8d45ea04c572b8a6bf84e42e92e)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-31T07:20:43Z
- **提交信息**: refactor(wan): unify distilled runners with base Wan runners (#1455)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2225
- **最后更新**: 2026-08-31T14:29:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6301
- **最后更新**: 2026-09-01T01:09:36Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Raayan Dhar, Peterson Guo, Brian K. Ryu

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批提交包含**功能新增**（FP8 per-channel量化）、**架构重构**（MoE CuTe DSL统一调度）、**Bug修复**（CI测试跳过逻辑）和**API改进**（PrimTS实时元数据传递）四类变更。

### 2. 关键变更点

- **MoE CuTe DSL统一调度**：将W4A4、W4A8、W4A16三种量化模式整合到同一套dtype-agnostic API中，移除约1800行重复代码，同时保留NVFP4、MXFP8/MXFP4的兼容别名并发出弃用警告。
- **FP8 per-channel量化支持**：为MoE推理新增per-output-row权重和gate缩放能力，扩展FP8量化类型至per-tensor和per-channel模式。
- **PrimTS实时元数据**：将paged block-sparse attention的请求元数据从`plan()`移至`run()`，使静态容量计划可跨decode步骤和CUDA Graph重放复用。
- **CI修复**：在子进程启动前预检jit-cache，避免`MissingJITCacheError`绕过skip机制导致nightly构建失败。

### 3. 对项目的影响

这些变更显著**简化了MoE内核的维护成本**，统一了量化调度路径，同时**增强了FP8生态兼容性**（对齐TRTLLM能力）。PrimTS的API迁移虽破坏nightly兼容性，但为TensorRT-LLM集成铺平了道路。CI修复保障了nightly wheel发布流程的稳定性。

### 4. 值得关注的技术点

- **dtype-agnostic设计**：通过消除dtype后缀的底层入口，降低API表面积，提升可维护性。
- **兼容性策略**：对弃用API提供可操作的DeprecationWarning，而非直接移除，体现渐进式迁移思路。
- **CUDA Graph友好性**：PrimTS的静态计划+实时数据模式是CUDA Graph重放的最佳实践。
- **SM107/Rubin支持**：明确W4A4/W4A16支持而拒绝W4A8，体现对硬件特性的精细管理。

### 5. 对项目发展的影响

FlashInfer作为高性能GPU推理内核库，本批提交体现了**从功能堆叠向架构收敛的转变**：统一MoE调度路径降低长期维护负担，FP8 per-channel支持扩展了量化灵活性，PrimTS实时元数据则强化了与主流推理框架（TensorRT-LLM）的集成能力。整体上，项目正朝着**更简洁的API、更广泛的硬件适配和更稳定的发布流程**方向演进，为后续支持更多量化格式和注意力变体奠定基础。

## 详细提交记录

### [f7d4b16](https://github.com/flashinfer-ai/flashinfer/commit/f7d4b167f76c8db9404461ddbaa87cc184696226)

- **作者**: Peterson Guo
- **时间**: 2026-08-31T23:56:45Z
- **提交信息**: Unify MoE CuTe DSL dispatch to be dtype agnostic (#4793)

<!-- .github/pull_request_template.md -->

## 📌 Description

Consolidates the CuTe-DSL fused MoE implementation behind dtype-agnostic
APIs

- Routes W4A4 and W4A8 through the same blockscaled GEMM dispatch path
in fused_moe.py.
- Consolidates the public API into cute_dsl_fused_moe and
CuteDslMoEWrapper, selected with quant_mode="w4a4", "w4a8", or "w4a16".
- Replaces dtype-suffixed low-level entry points with unsuffixed
blockscaled APIs.
- Preserves deprecated NVFP4 and MXFP8/MXFP4 APIs through compatibility
aliases/adapters that emit actionable DeprecationWarnings.
- Preserves SM107/Rubin support for W4A4 and W4A16 while explicitly
rejecting W4A8.
- Removes the duplicate MXFP8/MXFP4 fused-MoE implementation, tuner,
split backend, and redundant tests.
- Retains activation, bias, routing, wrapper, functional API, and
dtype-specific coverage in the consolidated tests.

  Overall diff versus main: approximately 1,800 net lines removed.

  ## 🔍 Related Issues

  N/A

  ## 🚀 Pull Request Checklist

  ### ✅ Pre-commit Checks

  - [x] Pre-commit hooks were run against every changed file.
- [x] Mypy, Ruff checks, Ruff formatting, and repository hygiene hooks
pass.
  - [x] Full pre-commit run --all-files was run

  ## 🧪 Tests

  - [x] Tests have been added or updated as needed.
  - [x] Compatibility aliases and deprecation warnings are tested.
  - [x] W4A4 and W4A8 shared dispatch is tested.
  - [x] The real B200 W4A8 functional/wrapper kernel test passes.
  - [x] Focused compatibility, validation, and dispatch tests pass.
  - [x] The complete repository test suite was run.

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Unified CuTe DSL fused MoE support across W4A4, W4A8, and W4A16
quantization modes.
* Added optional MXFP8 pre-dispatch packing for supported distributed
MoE workflows.
  * Added W4A8 tactic selection, validation, and tuning support.

* **API Updates**
  * Introduced unified `cute_dsl_fused_moe` and `CuteDslRunner` APIs.
* Previous API names remain available as deprecated compatibility
aliases with warnings.

* **Documentation**
* Updated API and architecture documentation for unified block-scaled
MoE support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [85c3643](https://github.com/flashinfer-ai/flashinfer/commit/85c364393b8d4d492fc6e00104cca02dfc291219)

- **作者**: Brian K. Ryu
- **时间**: 2026-08-31T22:49:02Z
- **提交信息**: fix(ci): skip subprocess torch.compile tests when kernels are absent from jit-cache (#4783)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
#4760 removed the single prefill/decode modules from the jit-cache
wheels. The two regression tests
(`test_single_decode_torch_compile_cuda_graph`,
`test_single_prefill_torch_compile_cuda_graph`) run their workload in a
subprocess, so under `FLASHINFER_DISABLE_JIT=1` the
`MissingJITCacheError` surfaces as a nonzero subprocess exit code
instead of an exception — bypassing the conftest hook that converts it
into a skip. This fails the `test-nightly-build` job, which gates
nightly wheel publication.

Fix: preflight the API in the parent process before spawning the
subprocess. When the module is missing from the jit-cache, the error now
raises in-process and the existing conftest handler skips the test and
records it in the jit-cache coverage report. As a bonus, JIT compilation
in normal runs now happens outside the subprocess's 300s timeout.

Note: batch prefill/decode tests that use the single-request APIs as
references now also skip in the nightly (gracefully, via the same
handler). Nightly coverage of those paths can be restored later by
moving references to torch-native SDPA.

## 🔍 Related Issues
#4760

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

* **Tests**
* Improved CUDA graph test setup by validating required attention
kernels before launching subprocesses.
* Missing JIT-cache modules are now skipped cleanly instead of causing
subprocess failures.
* JIT compilation is performed outside subprocess timeout windows,
improving test reliability.

* **Chores**
* Nightly releases and wheel index updates now run only for changes on
the main branch.
* Builds and tests can still run as dry runs from other branches without
publishing artifacts.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [faf7c6a](https://github.com/flashinfer-ai/flashinfer/commit/faf7c6aecebcfa9b6dd7bff13c358b434a7d7ce9)

- **作者**: Raayan Dhar
- **时间**: 2026-08-31T15:37:47Z
- **提交信息**: feat(MoE): FP8 MoE per-channel quant support  (#2809)

<!-- .github/pull_request_template.md -->

## 📌 Description

See issue. Seems like the TRTLLM kernel already exposes some support for
this but was set to `nullptr`. Mostly plumbing work to try and get this
to work.

Need to test, unsure if this is functional + if we need cubin.

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/2419

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
* FP8 per-channel quantization for Mixture-of-Experts inference with
per-output-row weight and gate scaling; new public API to run FP8
per-channel MoE kernels.

* **Improvements**
* Kernel selection and error diagnostics now consider
per-token/per-channel scale options for clearer configuration matching.
* FP8 quantization types extended to include per-tensor and per-channel
modes and integrated into runtime dispatch and exports.

* **Tests**
* Added unit tests and utilities covering FP8 per-channel quantization,
dequantization, and routing behaviors.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: raayandhar <raayan.dhar@gmail.com>
Signed-off-by: raayandhar <raayan@magic.dev>
Signed-off-by: bai <v@gor.io>
Signed-off-by: Raayan Dhar <raayan@magic.dev>
Signed-off-by: Haobin Guo <haobing@nvidia.com>
Co-authored-by: bai <v@gor.io>
Co-authored-by: Haobin Guo <haobing@nvidia.com>

### [d981061](https://github.com/flashinfer-ai/flashinfer/commit/d981061a38ef9272781e898a7e393d58ef59fb0d)

- **作者**: Yuhang He
- **时间**: 2026-08-31T13:32:09Z
- **提交信息**: fix(attention): make PrimTS paged block-sparse metadata live (#4664)

## 📌 Description

A follow-up to #4474 that makes paged PrimTS block-sparse attention
consume live request metadata.

- Keep only static geometry and capacity in
`BlockSparsePagedTSWrapper.plan()`.
- Pass live page indptr, page IDs, KV sequence lengths, BSR routes, and
validity bits to `run()`.
- Reusable wrappers validate tensor structure on the host but trust
device-side metadata values. Invalid values are unsupported and may
access out of bounds; setting `CUTE_DSL_ENABLE_ASSERTIONS=1` before
kernel compilation enables diagnostic device assertions.
- One-shot APIs synchronously inspect live paged-KV and BSR values
before planning and execution.
- Add reusable wrapper trace schemas for contiguous, paged tuple-cache,
and paged combined-cache forms, with CUDA Graph coverage.

This lets one static capacity plan be reused across decode steps and
CUDA Graph replays.

### Intentional API migration

This intentionally changes the experimental paged block-sparse API
introduced by #4474. The old API appeared in nightly builds but has not
shipped in a stable or RC release.

- `plan()` now takes `batch_size`, `max_seq_len_kv`, and `device`; it no
longer snapshots `paged_kv_indptr` or `seq_lens_kv`.
- `run()` now takes live `paged_kv_indptr`, `paged_kv_indices`, and
`seq_lens_kv`.
- `block_sparse_attention_with_paged_kv_cache()` now uses
`max_seq_len_kv` and requires `seq_lens_kv`.

Nightly users must move request metadata from `plan()` to each `run()`
call and keep tensor addresses stable across CUDA Graph replay.

## 🔍 Related Issues

Dependency for the TensorRT-LLM PrimTS block-sparse / VisualGen VSA
integration.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`.
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on all changed files and fixed all reported
issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All relevant focused tests are passing.

Validation:
- Focused block-sparse/trace checks after rebase: `21 passed`.
- Full trace template consistency: `750 passed`.
- Batch-aware trace cleanup: `7 passed, 743 deselected`.
- Pre-commit on changed files: passed.

## Reviewer Notes

The paged kernel ABI already accepted page metadata and KV lengths as
runtime tensors. This change removes wrapper-side snapshots and always
selects the dynamic-length specialization for paged storage; it does not
change the FMHA math kernel.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Paged block-sparse attention now accepts live per-request sequence
lengths and page mappings at execution time.
* Planning uses static capacity limits, while reusable wrappers consume
current runtime metadata.
* Added reusable wrapper tracing for contiguous and paged cache formats.
* One-shot APIs validate live metadata before execution; reusable APIs
support optional assertion diagnostics.

* **Documentation**
* Updated APIs, trace schemas, examples, and guidance to distinguish
static capacities from live runtime metadata.
* Documented requirements and limitations for CUDA Graph capture and
invalid runtime values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: yuhangh <58161490+heyuhhh@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4242
- **最后更新**: 2026-08-31T22:27:14Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交以**功能新增**和**性能优化**为主，共3项变更，均围绕MiniMax H3模型的推理体验改进，无Bug修复或文档更新。

### 2. 关键变更点与项目方向
- **新增MLX TAEH3预览解码器**：为MiniMax H3引入可选的MLX（Apple Silicon机器学习框架）解码器，拓展了FastVideo在Apple硬件上的推理能力。
- **GPU-direct DiT加载优化**：在MiniMax H3的Sequential推理流程中，实现DiT（Diffusion Transformer）权重直接加载至GPU，减少CPU-GPU间数据拷贝延迟。
- **MLX推理速度提升**：针对MiniMax H3的MLX推理路径进行专项加速，优化算子执行效率。

三项变更均指向**推理性能与硬件适配**，与FastVideo“快速视频生成”的核心定位高度一致。

### 3. 对项目的影响与潜在意义
- **扩大硬件覆盖范围**：MLX支持使Mac用户无需依赖CUDA即可高效运行MiniMax H3，降低使用门槛，吸引更广泛的开发者社区。
- **提升推理吞吐量**：GPU-direct加载和MLX加速直接减少推理延迟，对实时或近实时视频生成场景意义重大，增强项目在同类工具中的竞争力。
- **为后续优化奠定基础**：这些性能改进可复用于其他模型，形成可迁移的优化模式。

### 4. 值得关注的技术点
- **MLX框架集成**：表明项目正积极拥抱Apple生态，MLX的算子级优化策略值得参考。
- **GPU-direct加载机制**：绕过传统数据管线，直接利用GPU显存，是高性能推理的关键技术路径。
- **Sequential推理流程优化**：针对MiniMax H3的特定架构（可能含时序依赖）进行定制优化，体现对模型特性的深入理解。

### 5. 对项目发展的影响
结合README中FastVideo强调的“快速”与“易用”目标，本批次提交通过**性能优化**和**硬件适配**双管齐下，直接强化了项目的核心卖点。MLX支持有望吸引Apple生态开发者，扩大社区贡献基础；而推理速度的提升则使FastVideo在视频生成工具中更具实用性，可能推动更多实时交互式应用场景的落地。长期来看，这些优化积累的技术经验（如GPU-direct加载）可反哺其他模型支持，加速项目向多模型、多硬件平台演进。整体上，本批次提交是FastVideo在“性能”与“生态”两个维度上的稳健推进，符合其作为高效视频生成框架的定位。

## 详细提交记录

### [a28f2ba](https://github.com/hao-ai-lab/FastVideo/commit/a28f2bab4b41c2e714119ca704db1098a483e4fb)

- **作者**: Aryan Kumar
- **时间**: 2026-08-31T12:08:06Z
- **提交信息**: [feat] Add an optional MLX TAEH3 preview decoder (#1794)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [f82d8be](https://github.com/hao-ai-lab/FastVideo/commit/f82d8be4bf90254243ea0d1e2a6dca8e8bac4ebb)

- **作者**: Aryan Kumar
- **时间**: 2026-08-31T11:20:21Z
- **提交信息**: [perf] Sequential MiniMax H3 start with GPU-direct DiT load (#1793)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [8e17751](https://github.com/hao-ai-lab/FastVideo/commit/8e1775183e1ae899c1a540c55430e337517a2198)

- **作者**: Aryan Kumar
- **时间**: 2026-08-31T11:14:55Z
- **提交信息**: [perf] Speed up exact MiniMax H3 MLX inference (#1792)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34416
- **最后更新**: 2026-08-31T22:15:09Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

### 主要更新类型
本次提交全部为**测试代码重构**，无功能新增、Bug修复或性能优化。

### 关键变更点
- 对L、M、N、V、K、S系列pipeline的测试进行了系统性重构。
- 将测试逻辑统一抽取到`common.py`中，并显式定义测试集合（sets）。
- 移除了已弃用pipeline的测试，并修复了stable audio和skyreels相关测试。

### 对项目的影响和潜在意义
- **提升可维护性**：通过集中公共测试逻辑，减少重复代码，降低后续维护成本。
- **明确测试边界**：显式定义测试集合，使测试覆盖范围更清晰，便于追踪和扩展。
- **清理技术债务**：移除弃用pipeline的测试，避免无效测试干扰，使测试套件更聚焦于当前支持的模型。

### 值得关注的技术点
- 测试重构采用“按系列分组”策略，与diffusers中pipeline的命名规范（如L、M、V系列）保持一致，便于开发者快速定位相关测试。
- 将公共逻辑下沉到`common.py`，体现了良好的测试架构设计，为未来新增pipeline测试提供了可复用模板。

### 对项目发展的影响
根据README，diffusers是一个多模态扩散模型工具库，支持图像、音频、视频等多种生成任务。本次重构虽不直接改变功能，但通过优化测试基础设施，为后续快速迭代新pipeline（如新增系列）扫清了测试层面的障碍。同时，清理弃用测试也符合项目“保持代码库整洁、聚焦活跃功能”的发展方向，有助于维持项目在快速演进中的稳定性和可靠性。整体而言，这是一次基础质量建设，为项目长期健康发展奠定基础。

## 详细提交记录

### [45b32f4](https://github.com/huggingface/diffusers/commit/45b32f4321e306d1dfd4e63db5599b3575b17465)

- **作者**: Sayak Paul
- **时间**: 2026-08-31T17:04:40Z
- **提交信息**: [tests] refactor l-series pipeline tests (#14637)

* refactor l-series pipeline tests

* define sets explicitly.

### [45ff6a6](https://github.com/huggingface/diffusers/commit/45ff6a6c187eb25a3759e2c1402105d83399055c)

- **作者**: Sayak Paul
- **时间**: 2026-08-31T16:43:03Z
- **提交信息**: [tests] refactor m and n series pipeline tests (#14638)

* refactor m and n series pipeline tests

* up

### [f9495c7](https://github.com/huggingface/diffusers/commit/f9495c7da144f45f452014a928482f140a57e910)

- **作者**: Sayak Paul
- **时间**: 2026-08-31T16:20:51Z
- **提交信息**: [tests] refactor v-series pipeline tests (#14653)

refactor v-series pipeline tests

### [e86072f](https://github.com/huggingface/diffusers/commit/e86072febab30920153a7027b9c0e12303a6eeb5)

- **作者**: Sayak Paul
- **时间**: 2026-08-31T16:20:41Z
- **提交信息**: [tests] refactor k-series pipeline tests (#14636)

* refactor k-series pipeline tests

* let's go.

* move to common.py

### [f9d1989](https://github.com/huggingface/diffusers/commit/f9d19895e653a46d504b33f1bf641031946eda33)

- **作者**: Sayak Paul
- **时间**: 2026-08-31T15:39:32Z
- **提交信息**: [tests] refactor remaining s series pipelines (#14654)

* refactor remaining s series pipelines

* remove tests for pipelines that are deprecated

* fix stable audio tests

* fix skyreels stuff.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
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


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13029
- **最后更新**: 2026-08-31T23:20:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32999
- **最后更新**: 2026-09-01T00:54:38Z

## 提交统计

- **昨日提交总数**: 28
- **提交者数量**: 16
- **主要提交者**: zijiexia, ishandhanani, Shuwen Wang

## AI分析总结

## 一、主要更新类型

本次提交涵盖功能新增、Bug修复、性能优化、文档更新、重构和基础设施改进六大类。其中，统一内存管理（unified-memory）系列提交（#35177、#35158、#35154、#37170）和Rust后端重构系列（#37226、#37222、#37221、#37220）构成主要工作，另有Diffusion模型算子融合、AMD GPU支持、Cookbook文档更新等分散改进。

## 二、关键变更点与项目方向

1. **统一内存管理深化**：为Mamba+混合SWA模型引入三子池架构，新增字节预算分配、可行性下限和守恒验证器，并修复混合模型路径的四个启动/正确性问题。这直接服务于SGLang对混合架构模型（如Mamba、SWA）的高效推理支持，是内存管理从通用走向模型特化的关键一步。

2. **Rust后端系统化重构**：简化请求默认值并文档化批头ABI、保持采样与调度器线格式同步、派生服务器地址并接受签名环境值、拆分重命名嵌入式服务器组件。这表明项目正将核心运行时向Rust迁移，以提升安全性和性能，同时保持与Python前端的协议一致性。

3. **Radix Cache Rust后端**：新增Rust TreeCore后端及共享奇偶校验测试，是缓存系统从Python向Rust迁移的重要里程碑，有望显著提升缓存查找和管理的性能。

4. **Diffusion模型优化**：融合FLUX.2 token拼接与NVFP4量化、Qwen-Image最终自适应LayerNorm及FP8归一化/激活量化，针对扩散模型推理做算子级融合，减少内核启动开销。

5. **硬件适配扩展**：AMD gfx1250支持ROCM 10并构建发布镜像，GB300 Triton MoE配置适配GLM-4.5 FP8，NPU修复evalscope精度解析，体现多硬件平台覆盖战略。

## 三、对项目的影响与潜在意义

- **性能提升**：内存子池和字节预算机制可减少混合模型的内存碎片和浪费；Diffusion算子融合和Radix Cache Rust化将直接降低推理延迟。
- **稳定性增强**：内存守恒验证器、KV记录一致性检查（#37167）、wfaas版本升级（#37170）等修复提升了系统在边界条件下的可靠性。
- **架构演进**：Rust组件拆分和TreeCore后端标志着SGLang正从Python主导走向混合架构，为未来高性能、低延迟部署奠定基础。

## 四、值得关注的技术点

- **三子池内存设计**：针对Mamba和SWA模型的不同访问模式分配独立内存池，避免相互干扰，是混合架构推理的关键优化。
- **字节预算与守恒验证**：通过可行性下限防止内存分配失败，守恒验证器确保内存使用不越界，属于防御性编程的典范。
- **Rust线格式同步**：保持采样和调度器wire schema同步，避免跨语言通信中的协议漂移问题。
- **GPU UUID键控权重缓存**：按GPU UUID区分权重缓存路径，解决多GPU环境下缓存冲突问题。

## 五、对项目发展的整体影响

SGLang作为高性能LLM推理框架，本次提交体现了三个战略方向：**一是向混合架构模型（Mamba、SWA、Diffusion）扩展**，通过内存和算子优化保持性能优势；**二是核心组件Rust化**，提升底层安全性和执行效率；**三是多硬件平台覆盖**（AMD、NPU、GB300），扩大生态适配范围。这些工作共同强化了SGLang在低延迟、高吞吐场景下的竞争力，同时为即将到来的DeepSeek-V4等新模型提供了就绪的推理路径。Cookbook文档更新（DSpark、DeepSeek-V4-Flash-Vision）则确保用户能快速上手新特性，形成"开发-优化-文档"的完整闭环。

## 详细提交记录

### [455232d](https://github.com/sgl-project/sglang/commit/455232de6e739db4f11b515af2dd6f5ba0274b56)

- **作者**: zijiexia
- **时间**: 2026-08-31T23:43:54Z
- **提交信息**: [Cookbook] Enable DSpark on the DeepSeek-V4 Flash Vision low-latency recipes (#37301)

### [ef9e58f](https://github.com/sgl-project/sglang/commit/ef9e58fd6d0140f9d2bade6a31dbab779013d038)

- **作者**: caihuali95
- **时间**: 2026-08-31T22:10:12Z
- **提交信息**: feat(unified-memory): three sub-pools for mamba + hybrid-SWA models (#35177)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [98cb353](https://github.com/sgl-project/sglang/commit/98cb3535b75224a5844cff075d1efb92a27f0619)

- **作者**: caihuali95
- **时间**: 2026-08-31T22:09:28Z
- **提交信息**: feat(unified-memory): byte-budget sizing, feasibility floor, and a conservation verifier (#35158)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [961beee](https://github.com/sgl-project/sglang/commit/961beee9e521decec22c511de7300e5cef474cb1)

- **作者**: caihuali95
- **时间**: 2026-08-31T22:08:43Z
- **提交信息**: fix(unified-memory): four boot/correctness fixes on the hybrid model paths (#35154)

Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [88cf5c9](https://github.com/sgl-project/sglang/commit/88cf5c954193ba61a287aed5c8e0700979822107)

- **作者**: zijiexia
- **时间**: 2026-08-31T21:52:28Z
- **提交信息**: [Cookbook] Add DeepSeek-V4-Flash-Vision-Exp to the DeepSeek-V4 page (#37293)

### [2530204](https://github.com/sgl-project/sglang/commit/253020450290328e9deb307eece1e402fa17f35e)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-31T19:46:15Z
- **提交信息**: [mem_cache] Make release, row-reuse asserts, and presence checks read the KV record (#37167)

### [95f0f41](https://github.com/sgl-project/sglang/commit/95f0f41021f17b65953861a37e41a78d25675ce2)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-31T19:39:59Z
- **提交信息**: [CI] Move tests onto the right CI stages (#34074)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [579270d](https://github.com/sgl-project/sglang/commit/579270d4590b1691156a984ecad6eeaefb2384ae)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-31T19:31:35Z
- **提交信息**: [Rust] Simplify request defaults and document batch header ABI (#37226)

### [2138494](https://github.com/sgl-project/sglang/commit/2138494272054bca670216e4b9c41f706b5579ff)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-31T19:31:07Z
- **提交信息**: [Rust] Keep sampling and scheduler wire schemas in sync (#37222)

### [48098b5](https://github.com/sgl-project/sglang/commit/48098b5f23b1a0f7f5aaccda8e57b403fd5f20f5)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-31T19:30:40Z
- **提交信息**: [Rust] Derive server address and accept signed env values (#37221)

### [1da86b9](https://github.com/sgl-project/sglang/commit/1da86b9801d5a5d2eedc2131a9960ce3ed069ece)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-31T19:28:43Z
- **提交信息**: [Rust] Split and rename embedded server components (#37220)

### [cf51650](https://github.com/sgl-project/sglang/commit/cf51650335b9f31b96a51b5b7235591d1812a5df)

- **作者**: ishandhanani
- **时间**: 2026-08-31T19:24:29Z
- **提交信息**: fix(config): retain pre-engine resolution declarations (#37195)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>

### [9e9d26a](https://github.com/sgl-project/sglang/commit/9e9d26a4af7b365090ad904f69b063c257314e17)

- **作者**: Shuwen Wang
- **时间**: 2026-08-31T18:43:59Z
- **提交信息**: Fix Mooncake serving benchmark trace rows (#37201)

### [549166b](https://github.com/sgl-project/sglang/commit/549166b819ea577db59197c7185a5d62d624e9ff)

- **作者**: Juhyun-Kim-Memphis
- **时间**: 2026-08-31T18:30:34Z
- **提交信息**: fix(gateway): bump wfaas to 1.0.2 so ContinueNextStep unblocks dependents (#37249)

### [07d84eb](https://github.com/sgl-project/sglang/commit/07d84ebd6dd2d8a4ced757f1cabfa9e2f96e1889)

- **作者**: Yuwei An
- **时间**: 2026-08-31T17:48:07Z
- **提交信息**: [2/N][Mixed] Mixed chunk prefill with spec enabled (#36933)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [9cf157c](https://github.com/sgl-project/sglang/commit/9cf157c2521bf9a1f866fd2a8c4a9ff83696085a)

- **作者**: Jialin Ouyang
- **时间**: 2026-08-31T16:26:20Z
- **提交信息**: [Radix Cache] Add Rust TreeCore backend with shared parity tests (#32710)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>

### [52e1c24](https://github.com/sgl-project/sglang/commit/52e1c24744bf4efe75fe976e26596ae1c9f279e2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-31T13:33:02Z
- **提交信息**: [Diffusion] Fuse FLUX.2 token concatenation and NVFP4 quantization (#37141)

### [d60d658](https://github.com/sgl-project/sglang/commit/d60d658f5f0f79c8853976aa83049be7174c4192)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-31T13:31:04Z
- **提交信息**: [Kernel] Add GB300 Triton MoE configs for GLM-4.5 FP8 (#37159)

Co-authored-by: Song Bian <biansonghz@gmail.com>

### [771e613](https://github.com/sgl-project/sglang/commit/771e613d96de0ee89631bc308a2525aaeae9f13e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-31T10:22:20Z
- **提交信息**: [Diffusion] Fuse Qwen-Image final adaptive LayerNorm (#37144)

### [1ed9bfa](https://github.com/sgl-project/sglang/commit/1ed9bfac2cd2d0de99271164e8f2a9b3b3a70fea)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-31T10:19:42Z
- **提交信息**: [Diffusion] Fuse Qwen-Image FP8 norm and activation quantization (#37156)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [a874b83](https://github.com/sgl-project/sglang/commit/a874b83c2cfddb3b440ad4e0c28f45fc10e99121)

- **作者**: pllimax
- **时间**: 2026-08-31T09:20:46Z
- **提交信息**: test: re-enable DSV4-Flash W8A8 8p nightly perf cases (#37214)

### [63b2adb](https://github.com/sgl-project/sglang/commit/63b2adbeac38cc82fd13735c96469c4ac56925ad)

- **作者**: pllimax
- **时间**: 2026-08-31T09:19:03Z
- **提交信息**: [NPU] Fix evalscope accuracy parsing and add glm5_1 aime26 request timeout (#36459)

### [a53718e](https://github.com/sgl-project/sglang/commit/a53718e88c2b06ef9821c79eca82a1bc54c8a16a)

- **作者**: YAMY
- **时间**: 2026-08-31T09:15:17Z
- **提交信息**: fix(ci): update attention backend test fixtures (#37219)

### [0674be7](https://github.com/sgl-project/sglang/commit/0674be736ceb138a2f4982c6d612754d2b319807)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-31T09:04:04Z
- **提交信息**: [AMD] build gfx1250 release image from main (#37225)

### [6580d5c](https://github.com/sgl-project/sglang/commit/6580d5cd9a835f7fc66f88057e5bf6ef6506ea4a)

- **作者**: Tarang Khanna
- **时间**: 2026-08-31T08:44:45Z
- **提交信息**: weight cache: key daemon paths by GPU UUID (#36101)

Co-authored-by: siyu <liusy58@linux.alibaba.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [3865efc](https://github.com/sgl-project/sglang/commit/3865efc9f7e88b3b0e59211b67dbdc072c972128)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-31T08:19:11Z
- **提交信息**: [AMD] support gfx1250 on ROCM 10 (#36871)

Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Kao <akao@amd.com>
Co-authored-by: wunhuang <wunhuang@amd.com>
Co-authored-by: Thomas Wang <1am9trash@gmail.com>
Co-authored-by: Xinyi Song <86638975+RolaoDenthu@users.noreply.github.com>
Co-authored-by: Lin, Soga <soga.lin@amd.com>
Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Bingxu Chen <bingxche@amd.com>
Co-authored-by: sogalin_codegen <39478626+sogalin@users.noreply.github.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [712a720](https://github.com/sgl-project/sglang/commit/712a720c8ae4ddaf760c53c1abd0457a6c8cb589)

- **作者**: Yuan Luo
- **时间**: 2026-08-31T08:11:49Z
- **提交信息**: [KDA] Fused-accept state advance for FlashInfer KDA MTP verify (#33722)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [f61bb7b](https://github.com/sgl-project/sglang/commit/f61bb7b40a4e647a19f35ae5589e68ec11a4c52e)

- **作者**: Cheng Wan
- **时间**: 2026-08-31T07:54:13Z
- **提交信息**: [unified-memory] Drop the vacated 'dense' qualifier and the restating comments (#37170)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1262
- **最后更新**: 2026-08-31T08:27:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90630
- **最后更新**: 2026-09-01T01:07:55Z

## 提交统计

- **昨日提交总数**: 46
- **提交者数量**: 36
- **主要提交者**: Roberto L. Castro, rasmith, zofia

## AI分析总结

# vLLM 昨日提交分析（46个提交）

## 一、主要更新类型

- **Bug修复**（约15个）：覆盖流水线并行、投机解码、KV卸载、多模态、前端等多个模块
- **性能优化**（约8个）：包括kernel调优、异步处理、注意力实现优化等
- **CI/测试改进**（约7个）：CI标签、测试稳定性、EKS迁移适配
- **新功能/硬件支持**（约8个）：AutoRound FP8量化、CPU AMX支持、SM100默认配置等
- **代码重构**（约3个）：前端协议文件移动、DSv3 kernel退役等

## 二、关键变更点与项目方向

1. **Kimi-K3模型深度支持**（4个提交）：修复RecoverSSM启动失败、注意力元数据构建错误，并在ROCm平台实现前缀缓存命中，表明vLLM正积极适配最新前沿模型架构（GDN注意力、MLA等）。

2. **KV Offload体系完善**（6个提交）：涉及事件元数据保留、P2P层级声明、CPU→GPU加载排序、共享内存区域管理等，显示KV缓存卸载作为长上下文推理的关键技术正被系统性加固。

3. **硬件平台扩展**：Intel XPU（AutoRound MXFP8、Qwen2-VL测试）、AMD ROCm（AITER注意力、DCP多token验证）、CPU（FP16/BF16 GDN状态）均有提交，体现vLLM多硬件平台战略持续推进。

4. **投机解码与注意力优化**：修复DFlash draft的RoPE布局、NemotronHMTP量化映射、SM120 DSv4 topk索引等，持续提升推理效率。

## 三、项目影响与潜在意义

- **稳定性提升**：大量Bugfix（尤其KV Offload和PP相关）直接增强生产环境可靠性
- **新模型支持加速**：Kimi-K3、Gemma4、Laguna-XS等新模型的适配，保持vLLM对前沿模型的快速跟进
- **多硬件生态成熟**：XPU/ROCm/CPU的持续投入，巩固vLLM作为跨平台推理框架的地位
- **队列管理新特性**：`max_num_queued_reqs/tokens`为服务端负载控制提供更细粒度手段

## 四、值得关注的技术点

1. **SM100默认使用原生CUDA AttnRes**：针对Blackwell架构的注意力优化成为默认配置
2. **Fused embedding kernel**：新kernel减少内存访问开销
3. **异步媒体并发解析**：多模态输入处理性能提升
4. **AutoRound块级FP8量化**：扩展量化格式支持范围
5. **DSv3 router GEMM kernel退役**：技术迭代更新

## 五、对项目发展的影响

vLLM正从“快速推理框架”向“生产级多硬件、多模型服务平台”演进。昨日提交体现了三个核心方向：**深度适配前沿模型架构**（Kimi-K3、DeepSeek-V3.2）、**完善分布式与KV管理基础设施**（KV Offload、DCP、PP）、**扩展硬件与量化生态**（XPU、ROCm、CPU、FP8）。CI系统的持续改进（EKS迁移、测试稳定性）则为规模化开发质量保驾护航。整体上，项目在保持快速迭代的同时，正系统性解决生产环境中的稳定性与性能瓶颈问题。

## 详细提交记录

### [89df6fc](https://github.com/vllm-project/vllm/commit/89df6fcb808febd88de0d08fb7437e9bddcaf81e)

- **作者**: Flora Feng
- **时间**: 2026-08-31T23:51:55Z
- **提交信息**: [CI] Broaden structured-output issue auto-labeling (#54645)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [6bafc04](https://github.com/vllm-project/vllm/commit/6bafc049aae6c26e210162630914ee9177a4b586)

- **作者**: Ausar
- **时间**: 2026-08-31T23:49:54Z
- **提交信息**: [Bugfix][PP] Never drop a decoding request from the sampled-token broadcast (#54436)

Signed-off-by: ArcheyChen <45146080+ArcheyChen@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b05acd2](https://github.com/vllm-project/vllm/commit/b05acd2ae04480186f218c3cd3dc186395c82e1d)

- **作者**: xiangdong
- **时间**: 2026-08-31T23:34:57Z
- **提交信息**: [XPU] [CI] Add retry for v1/sample in Intel GPU CI (#53669)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [91752b7](https://github.com/vllm-project/vllm/commit/91752b7a3e0cd20ba2a41a65069ece1b29825ee5)

- **作者**: Wentao Ye
- **时间**: 2026-08-31T23:22:49Z
- **提交信息**: [K3 Bug] Fix Kimi-K3 RecoverSSM startup failure `'MambaAttentionBackendEnum.GDN_ATTN declares 4 states, but provides 2 state copy funcs'` (#54634)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [3a2ed6c](https://github.com/vllm-project/vllm/commit/3a2ed6cbae167ea2fe7923112f206bfe0fc4ee39)

- **作者**: Wentao Ye
- **时间**: 2026-08-31T23:21:01Z
- **提交信息**: [Kimi Bug] Fix gdn build_attn_metadata `'KimiK3KDAMetadataBuilder' object has no attribute 'layer_names'` (#54636)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d6d6658](https://github.com/vllm-project/vllm/commit/d6d665854314f0aa90ad6ef32a3382136c71314c)

- **作者**: Yongye Zhu
- **时间**: 2026-08-31T23:18:12Z
- **提交信息**: [Kimi-K3][Perf] Make native CUDA AttnRes the SM100 default (#54261)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [07ea935](https://github.com/vllm-project/vllm/commit/07ea9350baf84e33fd696d36fec9b9f24735a733)

- **作者**: mobicham
- **时间**: 2026-08-31T22:21:22Z
- **提交信息**: [Kernel][Gemma4] Prune Triton sliding-window tiles for multimodal prefixes (#53147)

Signed-off-by: mobicham <hichamb@dropbox.com>

### [d61b6e1](https://github.com/vllm-project/vllm/commit/d61b6e1878a60d5a2dafab05565790d0c45ff469)

- **作者**: Zihan Zhang
- **时间**: 2026-08-31T22:13:20Z
- **提交信息**: [Bugfix][Spec Decode] Take the DFlash draft's RoPE layout from its own config (#54373)

Signed-off-by: SubSir <tiancaizhangdaxian@sjtu.edu.cn>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [24d42f3](https://github.com/vllm-project/vllm/commit/24d42f3553a35aa53006a3ee8d04cc9191cb7be9)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-31T21:56:27Z
- **提交信息**: [CI] Mark 1-GPU L4 test steps with device: l4 for EKS migration (#54549)

Signed-off-by: khluu <khluu000@gmail.com>

### [f5c3cc2](https://github.com/vllm-project/vllm/commit/f5c3cc240bc1fc0519694fe689edb87dee8dfd92)

- **作者**: Roberto L. Castro
- **时间**: 2026-08-31T20:44:38Z
- **提交信息**: [Perf][Kernel] Tune cooperative topk for medium batch-sizes (#53382)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [85c1365](https://github.com/vllm-project/vllm/commit/85c1365bd9711bde5484a3de7d7b2eaa44a03868)

- **作者**: Juhi Mittal
- **时间**: 2026-08-31T19:10:24Z
- **提交信息**: [Bugfix] NemotronHMTP: add hf_to_vllm_mapper so quant exclusions reach the MTP draft (#53790)

Signed-off-by: Juhi Mittal <juhim@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [a9dc631](https://github.com/vllm-project/vllm/commit/a9dc631429bec8709afa993595d91e27b00cabe6)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-31T19:07:17Z
- **提交信息**: [Bugfix] Reject empty bad-word tokenizations (#53433)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [f9c7c6e](https://github.com/vllm-project/vllm/commit/f9c7c6e0909eadc23f1aa2510a233f91692ed437)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-31T19:02:55Z
- **提交信息**: [Rust Frontend][CI] Remove TCP port races from mock-engine tests (#54481)

Co-authored-by: OpenAI Codex <codex@openai.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [f5e441d](https://github.com/vllm-project/vllm/commit/f5e441de10bd55149c4211473dc9fcffc84ad2ce)

- **作者**: Qiming Zhang
- **时间**: 2026-08-31T18:49:43Z
- **提交信息**: [Bugfix][Test] Fix off-by-one error in sampled token rank causing flaky logprobs test (#53976)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [65ce85f](https://github.com/vllm-project/vllm/commit/65ce85fcdcd79770eeb8cd5eeb4e4ba06120bf6d)

- **作者**: Joe Rowell
- **时间**: 2026-08-31T18:22:00Z
- **提交信息**: Add Laguna-XS-2.1-INT4 to nightly CI (#52961)

Signed-off-by: Joe Rowell <joe@poolside.ai>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [2ba984a](https://github.com/vllm-project/vllm/commit/2ba984a5d06db414f3b2474fe9338faf6cd80a1c)

- **作者**: YukioZzz
- **时间**: 2026-08-31T18:18:10Z
- **提交信息**: [ROCm][DSpark][DCP] Serve prefix cache hits under DCP for Kimi-K3 (#53598)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [dbb7fff](https://github.com/vllm-project/vllm/commit/dbb7fffddbca2815d5d2339c52ca04a6715f2139)

- **作者**: YukioZzz
- **时间**: 2026-08-31T17:42:28Z
- **提交信息**: [ROCm][MLA][DCP] Support causal multi-token verification (#51705)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Signed-off-by: billishyahao <bill.he@amd.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: billishyahao <bill.he@amd.com>

### [39e276e](https://github.com/vllm-project/vllm/commit/39e276eaeb9daed06a180f6a8d187bbb8790e97b)

- **作者**: Artem Perevedentsev
- **时间**: 2026-08-31T16:39:27Z
- **提交信息**: [Structured Output] Let terminal grammars stop under min_tokens (II) (#54218)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [e9dd6d4](https://github.com/vllm-project/vllm/commit/e9dd6d483484dec29d50b3f23c25cb8b711894ce)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-31T16:17:12Z
- **提交信息**: [CI] Exclude kv_transfer changes from broad spec-decode/kernels/multimodal triggers (#54365)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [3593c96](https://github.com/vllm-project/vllm/commit/3593c964de198646a2a284c24fc53cccd21afd7e)

- **作者**: rasmith
- **时间**: 2026-08-31T16:09:46Z
- **提交信息**: [ROCm] Add TheRock preview docker updates, Keep Python 3.12 and Ubuntu 22.04 (#49925)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [82936c4](https://github.com/vllm-project/vllm/commit/82936c409d17321d5a791796296790508605aaed)

- **作者**: Fanli Lin
- **时间**: 2026-08-31T14:59:57Z
- **提交信息**: [Tests][XPU] Limit Qwen2-VL generation length to avoid flaky numerical divergence (#54172)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [bd575a0](https://github.com/vllm-project/vllm/commit/bd575a0d0bdf482557648e5278bbba98b6a939b9)

- **作者**: Zhenzhong Xu
- **时间**: 2026-08-31T14:56:20Z
- **提交信息**: [AutoRound] Support AutoRound Format Block-Wise FP8 in vLLM (#47434)

Signed-off-by: Zhenzhong1 <zhenzhong.xu@intel.com>
Signed-off-by: Zhenzhong Xu <zhenzhong.xu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [dafbef1](https://github.com/vllm-project/vllm/commit/dafbef15a1c879c64ebb99427917e4ca8d5bca1e)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-31T14:26:49Z
- **提交信息**: [Core] Add `max_num_queued_reqs` and `max_num_queued_tokens` for queue size management (#49445)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [76ff0cd](https://github.com/vllm-project/vllm/commit/76ff0cdff2defded8d912d550299c902ff33cdca)

- **作者**: andyluo7
- **时间**: 2026-08-31T13:53:12Z
- **提交信息**: [Bugfix][ROCm] Preserve AITER unified-attention metadata during graph replay (#53821)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [c5d840f](https://github.com/vllm-project/vllm/commit/c5d840ff6a50f544fca8524e8caffda9f63b7728)

- **作者**: Itay Etelis
- **时间**: 2026-08-31T12:53:19Z
- **提交信息**: [KV Connector][Offloading] Certify attention-only hybrids in the canonical portability gate (#51689)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [4c58a0c](https://github.com/vllm-project/vllm/commit/4c58a0c398b056b135b98bd93c644945be7e3109)

- **作者**: Itay Etelis
- **时间**: 2026-08-31T12:53:00Z
- **提交信息**: [Bugfix][KV Offload] Unlink /dev/shm region after all workers map it (barrier variant of #51317) (#52596)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [e0d2704](https://github.com/vllm-project/vllm/commit/e0d27040ddcc5ac31cf01c5b04a7d764ccba656d)

- **作者**: Uttam Kumar
- **时间**: 2026-08-31T11:34:48Z
- **提交信息**: [Bugfix][KV Offload][P2P] Preserve aborted loads until abort completion (#52571)

Signed-off-by: Uttam Kumar <uttam.kumar912@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [e2c8eea](https://github.com/vllm-project/vllm/commit/e2c8eeac40d01051d6d60b8f42ebbe5842a1c672)

- **作者**: Jee Jee Li
- **时间**: 2026-08-31T11:34:14Z
- **提交信息**: [kernel] Fused embedding kernel  (#53677)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [bed3280](https://github.com/vllm-project/vllm/commit/bed3280f50dce36ff9472eee937d1aada7e31d75)

- **作者**: Itay Etelis
- **时间**: 2026-08-31T11:31:18Z
- **提交信息**: [KV offload] Order CPU->GPU loads against the compute stream (#50696)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [810bc32](https://github.com/vllm-project/vllm/commit/810bc3250c945829c64a745b4f695ddfd8f9a598)

- **作者**: waizuichougou
- **时间**: 2026-08-31T10:50:17Z
- **提交信息**: [Frontend][Performance] Resolve async media across modalities concurrently (#54537)

Signed-off-by: waizuichougou <2082431897@qq.com>

### [9debcd5](https://github.com/vllm-project/vllm/commit/9debcd5990bf275db5ac8ed7bea653a1fa8a23a0)

- **作者**: maithilijoshi20
- **时间**: 2026-08-31T10:46:50Z
- **提交信息**: [Test][Qwen3-VL] Cover compiled DeepStack input contract (#53529)

Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>

### [9acbc53](https://github.com/vllm-project/vllm/commit/9acbc5360aa50d148fcfcbd597703514aa9a3e22)

- **作者**: Moein Khazraee
- **时间**: 2026-08-31T10:28:30Z
- **提交信息**: [KV Offload] Preserve KV event metadata until final residency removal (#52068)

Signed-off-by: Moein Khazraee <moein@nvidia.com>

### [eeb549a](https://github.com/vllm-project/vllm/commit/eeb549a74dbf9cd41ff6b4c99ea2f4c6a82a7538)

- **作者**: wang.yuqi
- **时间**: 2026-08-31T10:13:50Z
- **提交信息**: [Frontend] Move engine/protocol.py out openai folder (#54492)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: Cyrus Leung <cyrus.tl.leung@gmail.com>

### [d8de4ae](https://github.com/vllm-project/vllm/commit/d8de4ae322b54e518b2de771fe28673c6e9664d9)

- **作者**: liranschour
- **时间**: 2026-08-31T10:07:20Z
- **提交信息**: [Bugfix][KVOffload] P2P tier declares REQUEST_LEVEL on the producer leg (#52912)

Signed-off-by: Liran Schour <lirans@il.ibm.com>

### [699e180](https://github.com/vllm-project/vllm/commit/699e180df48d78b5275d528124641c67b4b1664c)

- **作者**: Gabriel Wu
- **时间**: 2026-08-31T09:44:42Z
- **提交信息**: [Bugfix][SM120] DSv4: pass contiguous C128A decode topk indices on SM120 (#53574)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [28bf75c](https://github.com/vllm-project/vllm/commit/28bf75c9a951b9871d2646df1c7828ee5a66e953)

- **作者**: Hotragn Pettugani
- **时间**: 2026-08-31T09:29:01Z
- **提交信息**: [Bugfix][Frontend] Truncate prompt_is_token_ids with the prompt (#54509)

Signed-off-by: hotragn <hotragn.pettugani_2024@woxsen.edu.in>

### [399247c](https://github.com/vllm-project/vllm/commit/399247cc8877f60f02f3aa859c61c3330a59bfbb)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-31T09:07:52Z
- **提交信息**: [Bugfix][MM] Fix MiniCPM-o image processor reuse on Transformers v5 (#54501)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [5bfd763](https://github.com/vllm-project/vllm/commit/5bfd76372d66507d014895376458fd507e124e66)

- **作者**: wang.yuqi
- **时间**: 2026-08-31T08:40:37Z
- **提交信息**: [Renderer] Shutdown the renderer properly.  (#52124)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [1b9539d](https://github.com/vllm-project/vllm/commit/1b9539d37c90f179886a462d2149189e3fe38045)

- **作者**: jl9876
- **时间**: 2026-08-31T08:37:01Z
- **提交信息**: [Quantization][Autoround][XPU] Support AutoRound MXFP8 MoE models (#51248)

Signed-off-by: jl9876 <jia.li@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [c6c33f2](https://github.com/vllm-project/vllm/commit/c6c33f2b1facdcf6ace0d2f241f20507c6cc8157)

- **作者**: Tianmu Li
- **时间**: 2026-08-31T08:32:20Z
- **提交信息**: [CPU] Support FP16/BF16 persisted GDN state on AMX (#52191)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [2a61f06](https://github.com/vllm-project/vllm/commit/2a61f060d342afb680f5a8937ed614b774bf9305)

- **作者**: zofia
- **时间**: 2026-08-31T08:01:24Z
- **提交信息**: [XPU] Ensure unquantized linear weight is N-contiguous (#53536)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Co-authored-by: opencode <noreply@opencode.ai>

### [fdbf2dd](https://github.com/vllm-project/vllm/commit/fdbf2ddbd22a82f8f59b97ba30e5436f0509d2c8)

- **作者**: Li, Jiang
- **时间**: 2026-08-31T07:33:06Z
- **提交信息**: [Bugfix][CPU] Fix several bugs (#54042)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [2cf82bc](https://github.com/vllm-project/vllm/commit/2cf82bcdd17f658486c280b0acd23274f60bdf00)

- **作者**: Yunxiao Ning
- **时间**: 2026-08-31T07:30:45Z
- **提交信息**: [Bugfix][DCP] Fix NVIDIA DeepSeek-V3.2 / GLM-5.2 fused attention (#50005)

Signed-off-by: 云挚 <ningyunxiao.nyx@antgroup.com>
Signed-off-by: Mikhail Kostryukov <mike@triptrack.net>
Co-authored-by: Mikhail Kostryukov <mike@triptrack.net>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [f9d666f](https://github.com/vllm-project/vllm/commit/f9d666f917941852b7d48ec20069f37480fafc28)

- **作者**: Moein Khazraee
- **时间**: 2026-08-31T07:28:41Z
- **提交信息**: [KV Offload] Forward ownership in KV cache events (#52067)

Signed-off-by: Moein Khazraee <moein@nvidia.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [8e92248](https://github.com/vllm-project/vllm/commit/8e92248f79814bc12a195f5d2529cc245768017c)

- **作者**: Jee Jee Li
- **时间**: 2026-08-31T07:15:31Z
- **提交信息**: [Kernel] Retire the DSv3 router GEMM CUDA kernel  (#54040)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [da0b2d8](https://github.com/vllm-project/vllm/commit/da0b2d8b17c9203bdd5eeb7a9af575f75a050c09)

- **作者**: 范裕达
- **时间**: 2026-08-31T07:05:18Z
- **提交信息**: [Performance] Optimize Dots3 NOTE runtime (#53517)

Signed-off-by: KurodaKanbei <mistergalahad@gmail.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-01
**监控日期**: 2026-08-31
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6513
- **最后更新**: 2026-09-01T01:03:18Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: Alex Brooks, Inesh Reddy Chappidi, Bo Li

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交以 **Bug修复** 为主（5项），辅以 **CI改进**（2项）和 **功能增强**（1项）。无文档更新或大规模重构。

### 2. 关键变更点与项目方向的关系
- **核心调度修复**（eb11446）：修复segment watermark在未维护请求计数器时被错误推进的问题，直接影响vLLM-Omni的多模态请求调度正确性，是服务稳定性的基础保障。
- **MiniCPM-o模型修复**（705e781、b81aeb7）：修复检查点回放时序问题，并让音频一致性检查变为确定性测试，提升该多模态模型的可靠性和可测试性。
- **HunyuanImage3 DiT支持**（fe4a2a7）：为图像扩散模型添加paged KV cache支持，覆盖NPU和GPU，扩展了项目的模态覆盖范围，与“omni-modality”目标高度契合。
- **Kernel优化**（6f16f95）：通过copy engine分阶段处理strided Ulysses QKV，优化了长序列场景下的通信效率。
- **MiMo-Audio兼容性**（b864374）：恢复vLLM 0.28版本的中间张量创建逻辑，确保音频模型在版本升级后保持兼容。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：调度器和检查点修复直接减少多模态推理中的潜在崩溃和状态错乱风险。
- **模态扩展**：HunyuanImage3的KV cache支持标志着项目向图像生成领域纵深发展，强化“全模态”定位。
- **工程成熟度**：CI确定性测试和语音验证消息优化，表明项目正从功能开发转向质量保障阶段。

### 4. 值得关注的技术点
- **paged KV cache在DiT上的适配**：将LLM的显存优化技术迁移至扩散模型，是跨模态技术复用的典型案例。
- **Ulysses QKV的copy engine分阶段处理**：针对长序列通信瓶颈的精细化优化，对大规模部署有实际价值。
- **检查点回放时序**：在最终输入提交前进行回放，避免状态不一致，是多模态流水线中的关键细节。

### 5. 对项目发展的影响
结合README中“Easy, fast, and cheap omni-modality model serving”的定位，本批提交体现了三个发展信号：一是通过核心调度和内核优化夯实“fast”基础；二是通过MiniCPM-o、HunyuanImage3、MiMo-Audio等模型支持扩展“omni”边界；三是通过CI确定性测试和验证信息改进，向“easy”使用体验靠拢。整体上，项目正从多模型接入阶段迈向稳定性和性能优化阶段，为更广泛的模态覆盖和规模化部署做准备。

## 详细提交记录

### [eb11446](https://github.com/vllm-project/vllm-omni/commit/eb11446b7f2e30ca582f8aff3afe12e9a2e66f6c)

- **作者**: Inesh Reddy Chappidi
- **时间**: 2026-08-31T15:27:13Z
- **提交信息**: [Bugfix][Core] Do not advance the segment watermark past an unmaintained request counter (#6834)

Signed-off-by: Inesh Reddy Chappidi <ineshreddy249@gmail.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [705e781](https://github.com/vllm-project/vllm-omni/commit/705e781b0efc52bea75930ecd584690eafcc204a)

- **作者**: Gao Han
- **时间**: 2026-08-31T15:18:29Z
- **提交信息**: [Bugfix][MiniCPM-o] Checkpoint playback before final input commit (#6821)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [b81aeb7](https://github.com/vllm-project/vllm-omni/commit/b81aeb7b86837f6fe8956f3aef83798ad26c5a26)

- **作者**: Gao Han
- **时间**: 2026-08-31T13:08:49Z
- **提交信息**: [CI][MiniCPM-o] Make audio consistency checks deterministic (#6828)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [3d1ad0c](https://github.com/vllm-project/vllm-omni/commit/3d1ad0c0f44425ad799b5d606a42d9b8a52c359c)

- **作者**: wangyu
- **时间**: 2026-08-31T12:13:26Z
- **提交信息**: [CI][Bugfix]Drop dummy-weight Qwen3-TTS Base from Ready CI (#6861)

Signed-off-by: wangyu <410167048@qq.com>

### [fe4a2a7](https://github.com/vllm-project/vllm-omni/commit/fe4a2a7477da686d12dc20c1ab70fc266e90eb35)

- **作者**: Wang  fuyin
- **时间**: 2026-08-31T10:15:46Z
- **提交信息**: [Diffusion] Add paged KV cache support for HunyuanImage3 DiT on NPU and GPU (#6563)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Signed-off-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Signed-off-by: zwhzzz0821 <2831474076@qq.com>
Co-authored-by: zwhzzz0821 <zwhzzz0821@users.noreply.github.com>
Co-authored-by: zwhzzz0821 <2831474076@qq.com>

### [6f16f95](https://github.com/vllm-project/vllm-omni/commit/6f16f9546d18fa5094115d13502b885c761c93b8)

- **作者**: Bo Li
- **时间**: 2026-08-31T09:28:49Z
- **提交信息**: [Bugfix][Kernel] Stage strided Ulysses QKV with copy engine (#6814)

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [58cb8de](https://github.com/vllm-project/vllm-omni/commit/58cb8de68bfef2993440b568907db60f448956b6)

- **作者**: Alex Brooks
- **时间**: 2026-08-31T08:13:59Z
- **提交信息**: [CI] Fix Speech CI Validation Messages (#6827)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [b864374](https://github.com/vllm-project/vllm-omni/commit/b864374089749ad3b4e6d01cb5d4f627beeb6174)

- **作者**: Rakesh Kariya
- **时间**: 2026-08-31T07:26:35Z
- **提交信息**: [Bugfix][MiMo-Audio] Restore make_empty_intermediate_tensors on the talker for vLLM 0.28 (#6803)

Signed-off-by: rk9595 <rakesh.kariya@somaiya.edu>

---
