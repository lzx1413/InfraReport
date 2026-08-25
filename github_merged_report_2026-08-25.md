# GitHub Stars 合并报告 - 2026-08-25

**合并日期**: 2026-08-26
**监控日期**: 2026-08-25
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


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2171
- **最后更新**: 2026-08-25T12:24:19Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bin Jia, Kaiyu Shi

## AI分析总结

### 主要更新类型
本次提交以**性能优化**和**代码重构**为主，无新增功能或Bug修复。

### 关键变更点及与项目方向的关系
1. **DeepSeek-V4稀疏索引构建与RoPE融合重构**（9f3934d）：移除构建稀疏索引时的密集掩码，并将旋转位置编码（RoPE）融合进该过程。这直接服务于VeOmni“模型中心化分布式训练配方”的核心目标——通过减少中间张量生成和算子调度开销，提升多模态模型训练效率。
2. **编码器数据均衡调度器改用堆结构**（894f744）：将原有调度逻辑从线性/数组结构改为堆（heap）实现，优化数据分配均衡性。这与项目强调的“分布式配方”紧密相关，旨在提升多节点训练时的数据吞吐和负载均衡。

### 对项目的影响和潜在意义
- **训练效率提升**：稀疏索引构建是DeepSeek-V4这类MoE（混合专家）模型的关键路径，去掉密集掩码可显著降低显存占用和计算量；RoPE融合减少内核启动次数，直接加速训练迭代。
- **可扩展性增强**：堆结构调度器在处理大规模编码器数据流时，时间复杂度从O(n)降至O(log n)，有助于VeOmni在更大规模集群上保持稳定性能。
- **代码质量改善**：两项重构均属于内部实现优化，不改变对外接口，降低了后续维护和扩展的复杂度。

### 值得关注的技术点
- **稀疏索引的无掩码构建**：这是对传统MoE路由的优化，可能涉及自定义CUDA内核或更高效的内存访问模式，值得关注其实现细节。
- **RoPE与稀疏索引的融合**：将位置编码嵌入稀疏索引构建阶段，避免了额外的张量变换，是典型的算子融合优化策略。
- **堆调度器设计**：需关注其如何平衡不同编码器任务的数据量差异，以及是否支持动态优先级调整。

### 对项目发展的影响
VeOmni定位为“任意模态模型训练的分布式配方库”，其竞争力在于训练效率和可扩展性。这两项重构直接强化了这两点：一方面，DeepSeek-V4作为前沿模型，其训练优化会吸引更多用户采用VeOmni；另一方面，调度器的改进为未来支持更大规模多模态数据集打下基础。整体上，这些提交体现了项目“持续打磨底层性能”的长期方向，而非短期功能堆叠，有助于巩固其在分布式训练工具链中的技术领先地位。

## 详细提交记录

### [9f3934d](https://github.com/ByteDance-Seed/VeOmni/commit/9f3934da425b50765a42366c40ed8c8fd7e0f20c)

- **作者**: Bin Jia
- **时间**: 2026-08-25T11:58:09Z
- **提交信息**: [model, ops, perf] refactor: build DeepSeek-V4 sparse indices without a dense mask, and fuse its RoPE (#1107)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [894f744](https://github.com/ByteDance-Seed/VeOmni/commit/894f74442206a94cf802c8f69b2c01ef5e8b28ef)

- **作者**: Kaiyu Shi
- **时间**: 2026-08-25T11:48:49Z
- **提交信息**: [parallel, perf] refactor: use heap for encoder data-balance scheduler (#1118)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2726
- **最后更新**: 2026-08-25T20:57:08Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Xin Qiu, qinxinyi, Shankun Wang

## AI分析总结

# LightX2V 昨日提交分析

## 主要更新类型

本次提交以**功能新增**为主，辅以**Bug修复**和**性能优化**。核心集中在MiniMax-H3模型的XPU（Intel）推理支持扩展，同时包含SwiftVR和Wan-Animate2的修复与加速。

## 关键变更点与项目方向

1. **MiniMax-H3 XPU生态完善**：新增FP8推理支持（含oneDNN原语缓存、大矩阵分块移植、FP8线性层bias修复）、DMD LoRA 4步推理支持、Qwen文本编码器host权重固定控制，以及5090 H3部署配置。这与项目“轻量视频生成推理框架”定位高度一致，持续扩展多硬件适配能力。

2. **Wan-Animate2运行时修复**：修复命名问题并优化尾窗处理，预计加速30%+，直接提升用户推理体验。

3. **SwiftVR数值正确性修复**：将BF16图像在NumPy导出前转换，避免精度损失，保障输出质量。

## 项目影响与潜在意义

- **硬件生态扩展**：FP8和DMD LoRA支持显著降低Intel XPU上的显存占用和推理延迟，使高端消费级GPU（如5090）和XPU成为可行的推理后端，扩大项目用户基础。
- **内存灵活性提升**：Qwen编码器权重固定策略允许在“常驻/模型卸载/块卸载”三种模式下切换pinned/pageable内存，为显存受限场景提供降级方案，增强部署灵活性。
- **性能与正确性双轨推进**：既通过尾窗加速和FP8优化提升速度，又通过BF16转换和bias修复保障数值正确性，体现工程成熟度。

## 值得关注的技术点

- **FP8推理的工程化细节**：包括大矩阵分块策略、oneDNN原语缓存、平台特定算子隔离（MMWeightFp8IntelXpu），这些是高性能FP8落地的关键实践。
- **DMD/Turbo LoRA 4步蒸馏推理**：大幅减少采样步数，是视频生成实时化的前沿方向。
- **内存管理精细化**：host pinned/pageable权重切换机制，为异构内存场景提供可配置方案。

## 对项目发展的影响

结合README中“轻量级视频生成推理框架”的定位，这些提交表明项目正从单一GPU支持向**多硬件、多精度、多优化策略**的成熟推理框架演进。MiniMax-H3的深度优化（FP8、LoRA、内存控制）显示项目正重点打造该模型的标杆体验，同时Wan-Animate2和SwiftVR的修复维护了模型覆盖广度。整体上，项目在**性能、硬件适配、内存效率**三个维度同步推进，有望吸引更多在非NVIDIA硬件上部署视频生成模型的用户，巩固其作为轻量级推理框架的竞争力。

## 详细提交记录

### [5dc5d63](https://github.com/ModelTC/LightX2V/commit/5dc5d6372654406761474719647763ac7b4bd018)

- **作者**: qinxinyi
- **时间**: 2026-08-25T10:14:56Z
- **提交信息**: fix(swiftvr): convert BF16 images before NumPy export (#1429)

### [11cb5c4](https://github.com/ModelTC/LightX2V/commit/11cb5c48e8240ee6f34f0a16f7393b9abe89344c)

- **作者**: Shankun Wang
- **时间**: 2026-08-25T10:09:19Z
- **提交信息**: 5090 h3 deploy config (#1434)

### [bfdba99](https://github.com/ModelTC/LightX2V/commit/bfdba998d41d6946863e624a252a2a47a532f4e8)

- **作者**: STwangyingrui
- **时间**: 2026-08-25T09:50:54Z
- **提交信息**: Configure MiniMax-H3 Qwen host weight pinning (#1424)

Add text_encoder_host_pinned to control pinned or pageable Qwen host
weights across resident, model-offload, and block-offload modes. Pinned
memory remains the default for faster H2D transfers, while
memory-constrained XPU configs use pageable weights to reduce host
pressure. Native and quantized text encoders are supported.

### [7fe2803](https://github.com/ModelTC/LightX2V/commit/7fe2803c986c04a37dbaa567c918f86e00f35b86)

- **作者**: qinxinyi
- **时间**: 2026-08-25T08:54:56Z
- **提交信息**: Fix/wan animate2 runtime correctness (#1430)

wan-animate2名字修改
尾窗处理加速，预计加速30%+

### [9262999](https://github.com/ModelTC/LightX2V/commit/926299962ed32a142411e45468a289623432b4e4)

- **作者**: Xin Qiu
- **时间**: 2026-08-25T08:21:34Z
- **提交信息**: feat(xpu): add MiniMax-H3 DMD LoRA 4-step inference (#1432)

## Summary

Add Intel XPU inference support for MiniMax-H3 T2AV using the DMD/Turbo
LoRA 4-step checkpoint.

### [15ebb53](https://github.com/ModelTC/LightX2V/commit/15ebb53c347afe003c140654ea2fe4e53a576b44)

- **作者**: helloyongyang
- **时间**: 2026-08-25T08:03:34Z
- **提交信息**: Add animate2 script

### [d54ee0b](https://github.com/ModelTC/LightX2V/commit/d54ee0b167035397b2b504ecefec2f9e234b56ae)

- **作者**: Xin Qiu
- **时间**: 2026-08-25T07:16:10Z
- **提交信息**: feat(xpu): support MiniMax-H3 FP8 inference (#1431)

## Summary

  - Add MiniMax-H3 FP8 inference support for Intel XPU.
  - Add FP8 configuration and launch script.
  - Port large-matrix chunking from the day0 implementation.
  - Add oneDNN primitive caching.
  - Fix missing bias in FP8 linear operations.
  - Move MMWeightFp8IntelXpu into platform-specific ops.
  - Add related tests and documentation.

  ## Validation

  - XPU extension builds successfully.
  - Python syntax checks pass.
  - git diff --check passes.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2204
- **最后更新**: 2026-08-25T06:54:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6243
- **最后更新**: 2026-08-25T18:31:48Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: nv-yunzheq, Gabriel Wu, RuQing Xu

## AI分析总结

# 提交分析总结

## 主要更新类型

本批提交包含**功能新增**、**Bug修复**和**性能优化**三类变更，无纯文档或重构类提交。

## 关键变更点

1. **SageAttention量化修复**（857bc3a）：修复序列长度不能被块大小整除时的质量损坏问题，新增K平滑支持，提升量化精度。

2. **Qwen3.6-35B-A3B融合GDN解码支持**（75e834d）：为sm120架构新增多几何配置支持，引入几何感知的JIT编译和缓存机制，扩展测试覆盖。

3. **MoE工作空间共享**（083012d）：允许B12xMoEWrapper共享预分配缓冲区，将60层MoE模型的内存占用从约68 GiB降至约1.2 GiB。

## 与项目方向的关系

这些提交紧密围绕FlashInfer作为**高性能GPU推理内核库**的核心定位：SageAttention修复提升注意力计算质量；Qwen模型支持扩展了主流架构覆盖；MoE优化直接解决大规模稀疏模型的实际部署瓶颈。

## 项目影响与潜在意义

- **SageAttention修复**保障了长序列场景下的输出质量，对生产环境可靠性至关重要
- **Qwen支持**使项目紧跟最新模型架构趋势，增强市场竞争力
- **MoE内存优化**是突破性改进，使超大MoE模型（如397B参数）能在单节点部署，大幅降低硬件门槛

## 值得关注的技术点

- 几何感知的JIT编译缓存机制，避免重复编译
- CUDA Graph兼容性下的缓冲区共享安全策略
- 编译期静态几何检查防止无效tiling

## 对项目发展的影响

这些提交体现了FlashInfer在**模型覆盖广度**（新增Qwen架构）、**内存效率**（MoE优化）和**数值质量**（SageAttention修复）三个维度的持续投入，巩固其作为推理加速库的领先地位，尤其强化了对大规模稀疏模型和最新架构的支持能力。

## 详细提交记录

### [857bc3a](https://github.com/flashinfer-ai/flashinfer/commit/857bc3a11494aaa0b7142a65c4a956ad68066f69)

- **作者**: RuQing Xu
- **时间**: 2026-08-25T18:30:38Z
- **提交信息**: fix: SageAttention support block size doesn't divide sequence; support K-smoothing  (#4654)

<!-- .github/pull_request_template.md -->

## 📌 Description

The latest TRTLLM_GEN_FMHA artifact contains not only updated LLM
support, but also a fix for SageAttention to address quality corruption
when seqLen%SfsK!=0. This fix demands a fix for `sageQuant` provided by
this PR.

## 🔍 Related Issues

N/A
(corruption not spotted by issues yet)

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

- **New Features**
- Added optional K smoothing for SageAttention quantization with V
staging.
  - K-mean outputs are now available when smoothing is enabled.
- Added support for batched, variable-length query and key/value
sequences, including ragged inputs and partial token blocks.

- **Bug Fixes**
- Improved validation and handling of sequence offsets, batch
dimensions, and per-batch scale buffers.
- Improved quantization accuracy across supported head dimensions and
smoothing modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Ruqing Xu <7891482+xrq-phys@users.noreply.github.com>

### [75e834d](https://github.com/flashinfer-ai/flashinfer/commit/75e834d633bc87267accc6e3f9749d18e459566a)

- **作者**: nv-yunzheq
- **时间**: 2026-08-25T16:23:27Z
- **提交信息**: (perf) add fused_GDN_step support for Qwen 3.6 35B A3B on sm120 (#4708)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow up with #4481 
- Adds Qwen3.6-35B-A3B support at batches 1/2/4 for both CUDA and
CuTe-DSL implementations.
- Generates one geometry-specific CUDA JIT module using FI_GDN_* compile
definitions.
  - Passes geometry as cutlass.Constexpr to CuTe-DSL kernels.
- Includes geometry in compiled-kernel, workspace, and CUDA Graph
readiness cache keys.
  - Adds compile-time/static geometry checks to prevent invalid tiling.
- Adds registry_geometries() for introspection and potential AOT
iteration.
- Expands tests across both geometries, both implementations, registry
shape, invalid geometry rejection, JIT module uniqueness, and numerical
equivalence.
- Updates documentation for the multi-geometry registry and JIT/AOT
behavior.
- Removes the hypothetical FLASHINFER_QWEN_GDN_FUSED_DECODE_DISABLE test
reference.

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

* **New Features**
* Added fused GDN decode support for an additional model configuration,
including its supported decode batch sizes.
* Kernel compilation, dispatch, caching, and CUDA graph capture now
account for each layer geometry, batch size, scale, and layout.
* Added validation for supported dimensions and tiling relationships,
with fallback behavior for unsupported geometries.
  * Expanded supported workloads across both shipped geometries.

* **Documentation**
* Updated support, registry, CUDA graph, build, and model-integration
guidance with expanded geometry requirements and configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [083012d](https://github.com/flashinfer-ai/flashinfer/commit/083012d6819cf97128e559616b12acb666f2fffe)

- **作者**: Gabriel Wu
- **时间**: 2026-08-25T07:36:11Z
- **提交信息**: feat(moe): allow B12xMoEWrapper to share pre-allocated workspaces (#4603)

## Summary

`B12xMoEWrapper` pre-allocates its static workspace, dynamic workspace,
and
output buffer per instance for CUDA graph compatibility. Frameworks that
hold
one wrapper per MoE layer — e.g. vLLM's `flashinfer_b12x` NVFP4 MoE
backend —
pay this cost once **per layer**.

For Qwen3.5-397B-A17B-NVFP4 (60 MoE layers, 512 experts, top-10 routing)
with
`max_num_tokens=16384`, the per-layer buffers total ~68 GiB:

- static workspace: `(num_experts, max_rows, k/2)` packed input ≈ 640
MiB/layer
- dynamic workspace: ≈ 506 MiB/layer (routed_rows = 16384 × 10)
- output buffer: 128 MiB/layer

With weights taking ~52.5 GiB per GPU (TP4 on 96 GB RTX PRO 6000), the
model
cannot start: workspace allocation OOMs during vLLM's memory profiling.

## Change

MoE layers execute strictly sequentially, so identically-shaped wrappers
can
safely share a single set of buffers. Add optional constructor
parameters:

- `shared_static_workspace`
- `shared_dynamic_workspace`
- `shared_output`

When provided, `_allocate_buffers()` reuses them instead of allocating.
Default behavior (no sharing) is unchanged.

With sharing, the same model's total wrapper memory drops from ~68 GiB
to
~1.2 GiB and the server starts within the default
`gpu_memory_utilization=0.80` budget.

## Safety

- CUDA graphs record fixed buffer addresses; sharing keeps every layer's
  captured pointers valid, and graph capture preserves the sequential
  layer-to-layer stream order, so there are no cross-layer hazards.
- Workspace barrier state is epoch-based and restored after each launch,
the
same sequential-reuse pattern a single wrapper already relies on across
  forward passes.
- vLLM copies the returned output slice out immediately, so sharing the
  output buffer is safe for this caller pattern.

## Testing

- New CPU tests in `tests/moe/test_b12x_fused_moe.py`:
- `test_wrapper_defaults_allocate_own_buffers` — default behavior
unchanged
- `test_wrapper_shared_buffers_are_reused` — injected buffers reused, no
new
    allocations
- End-to-end on 4x RTX PRO 6000 (SM120, CUDA 13): vLLM `flashinfer_b12x`
  serving Qwen3.5-397B-A17B-NVFP4 with layer-shared workspaces starts,
  captures FULL_AND_PIECEWISE CUDA graphs, and completes a full
C1/C4/C16/C64 serving benchmark (8K/1K, 850 measured requests) with zero
errors and zero preemptions. Runtime validation was done on top of
#4602,
  which fixes a separate SM12x MoE compile-time regression.

## Consumer

A corresponding vLLM change makes `FlashInferB12xExperts` share one
buffer
set across layers (keyed by shape/device); it depends on this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for reusing shared workspace and output buffers with the
B12x MoE wrapper when CUDA graph mode is enabled.
* Automatically allocates only missing buffers across supported
quantization modes.

* **Bug Fixes**
* Improved default allocation so separate wrapper instances receive
independent resources.
* Added validation for compatible output shape, data type, and exact
CUDA device.
* Reports clearer errors when shared buffers are used outside graph mode
or on the wrong device.

* **Tests**
  * Added coverage for shared-buffer requirements and device validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4055
- **最后更新**: 2026-08-25T21:51:51Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为 **Bug修复**，同时包含对现有功能的适配性调整，属于技术维护类更新。

**2. 关键变更点及与项目方向的关系**  
- **修复FastMetal-QAD在MLX（Apple Silicon机器学习框架）上的兼容性问题**：明确拒绝CUDA QAD树（避免错误加载），改用打包的`mlx_dit`配置，并实现流式加载（stream loads）。  
- **与项目方向的关系**：FastVideo致力于高效视频生成，支持多硬件后端（如CUDA、MLX）。此修复直接强化了Apple Silicon设备的支持，符合项目“跨平台、高性能”的定位，填补了MLX后端在QAD（Quantized Attention Distillation）场景下的功能缺口。

**3. 对项目的影响和潜在意义**  
- **提升MLX后端的稳定性**：修复了此前可能因错误加载CUDA配置而导致的崩溃或性能退化，使MLX用户能正常使用QAD功能。  
- **扩大用户覆盖**：Apple Silicon设备用户（如MacBook、M系列芯片）可更可靠地运行FastVideo，降低使用门槛，增强项目在创意工具领域的吸引力。  
- **为后续优化铺路**：流式加载机制为处理大规模模型或长视频生成提供了更高效的内存管理基础。

**4. 值得关注的技术点**  
- **硬件后端隔离**：明确区分CUDA与MLX的配置加载逻辑，避免跨平台配置污染，是跨后端框架设计的关键实践。  
- **流式加载（stream loads）**：可能通过分块或按需加载模型权重，减少峰值内存占用，对长视频生成或低内存设备尤为重要。  
- **打包配置（packed mlx_dit config）**：将MLX相关配置整合为独立包，简化依赖管理，提升可维护性。

**5. 对项目发展的影响**  
基于README中“快速开始”和“文档”强调的易用性目标，此修复直接提升了MLX用户的体验，使FastVideo在Apple生态中更具竞争力。同时，它体现了项目对多硬件适配的持续投入，有助于吸引更多开发者贡献MLX相关优化，推动项目向“全平台高效视频生成工具”方向发展。长期看，此类兼容性修复将巩固FastVideo作为开源视频生成框架的可靠性声誉，促进社区增长。

## 详细提交记录

### [6388db8](https://github.com/hao-ai-lab/FastVideo/commit/6388db815b2f3d6b5fb05ff143c674a23a489878)

- **作者**: Aryan Kumar
- **时间**: 2026-08-25T21:51:40Z
- **提交信息**: [bugfix] FastMetal-QAD MLX support: refuse CUDA QAD trees, use packed mlx_dit config, stream loads (#1736) (#1758)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34379
- **最后更新**: 2026-08-25T21:58:26Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: kaixuanliu, Sayak Paul, dg845

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **代码重构**：LTX2Guidance 模块位置迁移
- **文档更新**：设备无关性改进、LTX2 文档完善
- **测试改进**：新增回归测试、pytest 迁移、测试覆盖扩展
- **核心功能优化**：kernels 调用传递库名称

### 2. 关键变更点与项目方向
- **LTX2Guidance 迁移**（c969cf2）：将 guider 从 modular_pipelines 移至独立 guiders/ 目录，解决 checkpoint 加载时组件解析问题。这与 diffusers 的模块化设计理念一致，确保 `from_pretrained` 能正确识别和加载 guider 组件，强化了模型组件的可组合性和可复用性。
- **文档设备无关化**（b9bc22b）：将硬编码的 CUDA 设备替换为通用写法，符合项目跨平台（CPU/GPU/XPU）支持的定位，降低多硬件环境使用门槛。
- **测试体系升级**（34d989f、be81dd0）：扩展 hunyuan/ltx/ltx2 测试覆盖，并将 test_pipelines.py 迁移至 pytest 框架，提升测试可维护性和可扩展性，与项目快速迭代节奏匹配。
- **kernels 库名称传递**（95c0d46）：优化底层调用链，使 kernels 调用能感知 diffusers 库身份，为后续版本兼容和调试提供基础。

### 3. 对项目的影响和潜在意义
- 修复了 LTX-2 guider 从 checkpoint 加载失败的实际问题，提升模型恢复和共享的可靠性。
- 测试迁移至 pytest 后，新测试编写成本降低，有助于提高整体测试覆盖率。
- 文档设备无关化扩大了潜在用户群，特别是非 NVIDIA 硬件用户。
- 这些改动共同增强了 diffusers 作为通用扩散模型工具库的健壮性和易用性。

### 4. 值得关注的技术点
- **模块路径迁移的兼容性处理**：移动类位置时同步更新文档和测试，确保 `modular_model_index.json` 中的引用可解析，体现了对序列化/反序列化链路的细致考量。
- **pytest fixture 的使用**：替代传统 unittest 风格，使测试更简洁、更易参数化。
- **kernels 调用链的库身份传递**：为未来多后端（如 Intel XPU）优化埋下伏笔。

### 5. 对项目发展的影响
结合 README 中 diffusers 作为模块化扩散模型工具库的定位，这批提交体现了三个发展方向：**组件可组合性**（guider 独立化）、**跨平台兼容性**（设备无关文档）、**测试现代化**（pytest 迁移）。这些改进有助于吸引更广泛的开发者贡献，同时保持库的稳定性和可扩展性，为后续新增模型和功能奠定更干净的基础架构。整体上，提交质量高，兼顾了功能修复、代码整洁和长期可维护性。

## 详细提交记录

### [c969cf2](https://github.com/huggingface/diffusers/commit/c969cf2f7ec56f0292c35bece674d170c8f9daa5)

- **作者**: dg845
- **时间**: 2026-08-25T17:27:18Z
- **提交信息**: Move `LTX2Guidance` Guider to `guiders/` Folder (#14558)

* Move LTX2Guidance from /modular_pipelines/ltx2/ to guiders/ to allow LTX-2 guiders to be correctly loaded from checkpoint

* Add regression test for LTX-2 guiders declared as from_pretrained components

Covers the round trip this move fixes: a checkpoint that declares `guider` and
`audio_guider` in `modular_model_index.json` must record a resolvable
(library, class_name) pair and reload its non-default guidance scales. The
existing `test_modular_index_consistency` skips components without a
`pretrained_model_name_or_path`, so `from_config` guiders were uncovered.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* Migrate LTX2Guidance docs to guider docs after move

* Improve LTX2Guidance docs and add arg docstrings

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [b9bc22b](https://github.com/huggingface/diffusers/commit/b9bc22bd579f591f8909a2d104ddca72688e6488)

- **作者**: kaixuanliu
- **时间**: 2026-08-25T15:12:22Z
- **提交信息**: make examples in docs device agnostic (#14414)

* docs: annotate hardcoded cuda device with alternatives in English docs

* docs: annotate hardcoded device_map="cuda" with alternatives

* update

Signed-off-by: kaixuanliu <kaixuan.liu@intel.com>

---------

Signed-off-by: kaixuanliu <kaixuan.liu@intel.com>

### [34d989f](https://github.com/huggingface/diffusers/commit/34d989f7efbc1562bfb214d9a6f1631f96d4864e)

- **作者**: Sayak Paul
- **时间**: 2026-08-25T15:09:05Z
- **提交信息**: [tests] hunyuan, ltx, ltx2 (#14587)

hunyuan, ltx, ltx2

### [95c0d46](https://github.com/huggingface/diffusers/commit/95c0d467cc2a4770b71fa25a117320377e6eb08f)

- **作者**: Sayak Paul
- **时间**: 2026-08-25T12:15:11Z
- **提交信息**: [core] pass diffusers library name to kernels calls (#14441)

up

### [be81dd0](https://github.com/huggingface/diffusers/commit/be81dd0f4ef57ef044c788c6cee2304591715a3d)

- **作者**: Sayak Paul
- **时间**: 2026-08-25T11:51:09Z
- **提交信息**: [tests] migrate `test_pipelines.py` to use pytest. (#14222)

* migrate test_pipelines.py to use pytest.

* use pytest fixtures.

* up

* fix

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12993
- **最后更新**: 2026-08-25T19:40:59Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Hong Zhang

## AI分析总结

# DiffSynth-Studio 提交分析

## 主要更新类型

本次提交记录包含两类更新：**文档更新**（update readme）和**功能新增**（为MiniMax-H3脚本添加训练适配器）。其中功能新增是核心变更，文档更新为辅助性维护。

## 关键变更点

1. **版本升级至2.1.0**：伴随功能更新进行版本号提升，表明项目进入新迭代周期。
2. **MiniMax-H3训练适配器**：为MiniMax-H3模型脚本新增训练支持，扩展了项目从推理到训练的能力边界。
3. **音频加载错误类型暴露**：改进错误处理机制，使音频加载失败时能提供更明确的错误信息，提升调试体验。
4. **量化选项文档补充**：完善量化相关使用文档，降低用户使用门槛。
5. **移除ref2va适配器**：清理不再需要的适配器代码，保持项目结构精简。

## 与项目整体方向的关系

DiffSynth-Studio定位为扩散模型综合工具库，覆盖图像、视频、音频等多模态生成。本次更新中，**训练适配器的加入**是重要战略步骤——项目正从单纯的推理工具向“训练+推理”全流程平台演进。MiniMax-H3作为新兴视频生成模型，其训练支持意味着项目紧跟前沿模型生态，增强了对最新技术的兼容能力。版本升级至2.1.0也印证了项目处于快速迭代期。

## 对项目的影响和潜在意义

- **能力边界扩展**：训练适配器使研究者可直接在DiffSynth-Studio框架内微调MiniMax-H3，无需切换工具链，提升工作流连贯性。
- **用户友好度提升**：错误类型暴露和量化文档补充，分别从技术调试和使用指引两方面改善用户体验，有利于吸引更广泛的用户群体。
- **代码库健康维护**：移除冗余适配器，降低维护成本，保持代码库整洁，为后续功能开发腾出空间。

## 值得关注的技术点

- **训练适配器架构**：值得关注其如何抽象训练流程，是否与现有推理接口统一，以及是否支持分布式训练等高级特性。
- **错误类型设计**：暴露音频加载错误类型，暗示项目在构建更完善的异常处理体系，可能为后续插件化或模块化设计铺路。
- **版本管理策略**：2.1.0版本号跳跃，结合多个功能点同步更新，反映项目采用功能集成的发布节奏。

## 对项目发展的影响

结合README中项目展示的多模态生成能力和活跃的社区生态（Trendshift徽章、PyPI发布），这些提交表明DiffSynth-Studio正从“演示型工具”向“生产级平台”转型。训练能力的加入将吸引更多研究者参与模型微调和定制，形成“社区贡献模型→平台集成→更多用户”的正向循环。同时，文档和错误处理的完善，是项目走向成熟化、企业级应用的重要标志。整体来看，这次提交是项目在功能深度和用户体验两个维度上的双重推进，为后续吸引更专业的用户群体和更复杂的应用场景奠定了基础。

## 详细提交记录

### [3f3df52](https://github.com/modelscope/DiffSynth-Studio/commit/3f3df523ed6273ee4c9dae245de2c7abd8fd4b5f)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-25T08:27:35Z
- **提交信息**: update readme (#1638)

### [bc83191](https://github.com/modelscope/DiffSynth-Studio/commit/bc83191f481e3115f1ba8a245bf4463e86449ed8)

- **作者**: Hong Zhang
- **时间**: 2026-08-25T08:01:59Z
- **提交信息**: Add Training adapter to MiniMax-H3 scripts (#1637)

* update version to 2.1.0

* Expose the error type for audio load.

* add training adapter for scripts

* add quant options for docs

* remove ref2va adapter

---------

Co-authored-by: yjy415 <2471352175@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32440
- **最后更新**: 2026-08-25T22:01:33Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 21
- **主要提交者**: Shangming Cai, Junpan Wu, Lianmin Zheng

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次提交涵盖**Bug修复**（约8项）、**性能优化**（约4项）、**文档更新**（约4项）、**CI/测试改进**（约3项）、**新功能支持**（约3项）及**架构适配**（约2项），整体以稳定性和多硬件适配为核心。

### 2. 关键变更点与项目方向

- **MoE（混合专家）路径深度优化**：多项提交聚焦MoE内核，包括MXFP8权重尺寸修复、CUTLASS预重排偏移溢出修复、共享专家融合、MXFP8缩放行步长处理等，直接支撑SGLang在高稀疏度大模型上的推理效率。
- **解耦服务（disagg）稳定性加固**：修复快照竞争条件和prefill引导元数据过期问题，提升预填充与解码分离架构的可靠性。
- **AMD/NPU多硬件适配加速**：新增MI35x性能基准、调整MI300阈值、启用HIP DSA后端CUDA图、NPU任务并行拆分，体现跨平台战略。
- **DeepSeek-V4专项支持**：为DeepSeek-V4适配NPU算子（压缩器、稀疏注意力），并启用共享专家融合，紧跟前沿模型需求。
- **文档与生态扩展**：新增IBM Granite 4.2、Kimi-K2.7-Code-MXFP4、MiniMax-M3等模型cookbook，降低用户上手门槛。

### 3. 对项目的影响与潜在意义

- **稳定性提升**：修复MoE权重尺寸、偏移溢出等底层问题，可减少大模型推理时的崩溃和错误结果，提升生产环境可靠性。
- **性能增益**：FlashInfer EXTEND调优、FP8缩放转置融合、CUDA图启用等优化，有望显著降低DP预填充延迟和显存开销。
- **生态扩展**：多模型cookbook和Diffusion模型支持（GLM-Image裁剪、Comfy NVFP4-AWQ文本编码器）吸引更广泛用户群。
- **硬件覆盖**：AMD和NPU的持续适配，使项目从NVIDIA独占走向多平台，扩大部署场景。

### 4. 值得关注的技术点

- **MXFP8 MoE权重尺寸修复**：非门控模型的权重布局修正，影响MoE层正确性。
- **CUTLASS MoE预重排int32溢出**：大模型下偏移量可能超过int32范围，修复避免内存越界。
- **HiCache L3的PP不一致修复**：多级缓存一致性保障，对长上下文场景至关重要。
- **MegaMoE预分发步长处理**：尊重填充后的缩放行步长，确保跨设备数据布局正确。
- **模型配置缓存键路径化**：避免不同路径下同名配置冲突，提升缓存命中率。

### 5. 对项目发展的影响

SGLang正从“高性能推理框架”向“多硬件、多模型、全场景”平台演进。本批次提交体现了三个战略方向：**一是深耕MoE和稀疏注意力等前沿模型结构**，通过内核级优化保持性能领先；**二是强化AMD/NPU等非NVIDIA生态**，降低对单一硬件依赖；**三是完善解耦架构和缓存机制**，为超长上下文和规模化部署铺路。文档和CI的持续投入，则确保社区能快速跟进新特性并保障质量。整体来看，项目正稳步迈向更成熟、更通用的LLM服务基础设施。

## 详细提交记录

### [f7a5649](https://github.com/sgl-project/sglang/commit/f7a56494b1e9c96cbe7ff1a4eeb8fdfcf12a606b)

- **作者**: Leon Gao
- **时间**: 2026-08-25T21:57:30Z
- **提交信息**: Fix SWA ownership across grouped frees (#36381)

### [4b4bf3d](https://github.com/sgl-project/sglang/commit/4b4bf3d2a57f4b72856a7429cb319c04abf94313)

- **作者**: Junpan Wu
- **时间**: 2026-08-25T21:55:25Z
- **提交信息**: [Deepseek-V4] Enable shared-experts fusion on the flashinfer_mxfp4 (trtllm-gen) MoE path (#35505)

Signed-off-by: Shiki Wu <shikiw@nvidia.com>

### [6569125](https://github.com/sgl-project/sglang/commit/6569125e3ad944ada667f5ff937fa9688cc98d03)

- **作者**: Michael
- **时间**: 2026-08-25T21:05:01Z
- **提交信息**: [AMD][CI] Add MiniMax-M3-MXFP8 MI35x nightly perf benchmark (#36142)

### [edff717](https://github.com/sgl-project/sglang/commit/edff717ef0106b4413b371bf7a05a5193ffeee85)

- **作者**: Shangming Cai
- **时间**: 2026-08-25T19:31:10Z
- **提交信息**: fix(disagg): snapshot affected rooms before iterating outside the lock (#36351)

### [7ddf92d](https://github.com/sgl-project/sglang/commit/7ddf92d5f481e79abd6db4f6c28dd27641fd2a7e)

- **作者**: Kevin Flansburg
- **时间**: 2026-08-25T19:29:20Z
- **提交信息**: fix(disagg): refresh stale prefill bootstrap metadata (#36029)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [99c02d7](https://github.com/sgl-project/sglang/commit/99c02d71b170673f97676f097fc928de38d847e0)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-25T17:38:46Z
- **提交信息**: docs(cookbook): use auto parser resolution for Granite 4.2 (#36342)

### [96a73c4](https://github.com/sgl-project/sglang/commit/96a73c4e15a2b98672b83b91af47d1e3bada707c)

- **作者**: Bingxu Chen
- **时间**: 2026-08-25T16:41:36Z
- **提交信息**: [AMD][CI] Adjust MI300 score API performance thresholds (#36290)

### [e9c9df6](https://github.com/sgl-project/sglang/commit/e9c9df6a52925af7a5908eea51f91c5dd5f01a00)

- **作者**: YAMY
- **时间**: 2026-08-25T15:29:57Z
- **提交信息**: [Performance] Tune FlashInfer EXTEND for DP prefill (#36219)

### [b760f7f](https://github.com/sgl-project/sglang/commit/b760f7fb1949604af2137c8284f1f121d2f0f8ff)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-25T14:54:55Z
- **提交信息**: docs(cookbook): add IBM Granite 4.2 cookbook (#36286)

### [46d9427](https://github.com/sgl-project/sglang/commit/46d9427b913b20ce0d72b95a9209717448b37368)

- **作者**: elvischenv
- **时间**: 2026-08-25T14:09:09Z
- **提交信息**: Fix MXFP8 MoE weight sizing for non-gated models (#36097)

### [a1f9508](https://github.com/sgl-project/sglang/commit/a1f9508dd41006672710eda29528cccb34d4a52e)

- **作者**: Benjamin Truong
- **时间**: 2026-08-25T12:56:42Z
- **提交信息**: [Bugfix] Fix int32 destination offset overflow in CUTLASS MoE pre-reorder (#35188)

### [829138a](https://github.com/sgl-project/sglang/commit/829138a31e4f464563defc35b10e3468542e9aa9)

- **作者**: Chao Shi
- **时间**: 2026-08-25T12:49:57Z
- **提交信息**: [HiCache] Fix PP inconsistency with HiCache L3 (#22607) (#27010)


Co-authored-by: ybyang <ybyang7@iflytek.com>
Co-authored-by: hzh0425 <hzh0425@apache.org>
Co-authored-by: shangmingc <csmthu@gmail.com>
Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>

### [c3947ee](https://github.com/sgl-project/sglang/commit/c3947eeadadb51ffe2fbaa1e85cba118eda81aad)

- **作者**: Mick
- **时间**: 2026-08-25T12:25:17Z
- **提交信息**: [diffusion] docs: desktop-safe 24 GB recipe and the DGX Spark tier (#36169)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [0c7ff19](https://github.com/sgl-project/sglang/commit/0c7ff19e3b739b2aabe9bfa070047bfa1aa6a7fd)

- **作者**: hhhh1252023
- **时间**: 2026-08-25T11:23:20Z
- **提交信息**: [NPU] [CI] Split the base-c-test-acc-2-npu-a3 task into two parts running in parallel (#36257)

### [443527a](https://github.com/sgl-project/sglang/commit/443527af0c11e0c0806d2545e926db1f99e38906)

- **作者**: Cheng Wan
- **时间**: 2026-08-25T10:18:28Z
- **提交信息**: config: the model-config cache keys on the path the record carried (#36300)

### [6a81038](https://github.com/sgl-project/sglang/commit/6a810383176a4e2a5b88f4a28ccf42cce2c1c538)

- **作者**: jacky.cheng
- **时间**: 2026-08-25T09:49:57Z
- **提交信息**: [AMD] Drop redundant FP8 bpreshuffle scale transpose via fused AR kernel (#33021)

### [a618d4c](https://github.com/sgl-project/sglang/commit/a618d4c064175d9d60bac0c4d1c43056337d1534)

- **作者**: Hsiu-Chun, Hung
- **时间**: 2026-08-25T09:37:32Z
- **提交信息**: [AMD] Add Kimi-K2.7-Code-MXFP4 to cookbook (#36246)

Co-authored-by: Hung <Emmanuel0612@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3bc1c58](https://github.com/sgl-project/sglang/commit/3bc1c580c6c845832531517c21288de41aa72932)

- **作者**: jiaryang
- **时间**: 2026-08-25T09:18:08Z
- **提交信息**: [AMD] Enable draft_extend CUDA graph for HIP DSA backend (#35672)

### [8f096b8](https://github.com/sgl-project/sglang/commit/8f096b853ad91b32c4f7eef2abf50db7d3ac06de)

- **作者**: AuFlow
- **时间**: 2026-08-25T08:50:47Z
- **提交信息**: [diffusion] fix: crop GLM-Image output to requested size (#33859)

Co-authored-by: AuFlow <AuFlow@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [2e3934f](https://github.com/sgl-project/sglang/commit/2e3934f4cba60c4012751d76eecbc11235185fbe)

- **作者**: Xinyi Song
- **时间**: 2026-08-25T08:48:09Z
- **提交信息**: [AMD] Enable Mori-EP on kimi-k3 (#35630)

### [d067622](https://github.com/sgl-project/sglang/commit/d067622820d459707cc94f217cf9555d3ed922bb)

- **作者**: Bingxu Chen
- **时间**: 2026-08-25T08:24:52Z
- **提交信息**: [AMD][bugfix] Add moe_ep_size/moe_tp_size to the allreduce-fusion gate test stub (#35340)

### [191244b](https://github.com/sgl-project/sglang/commit/191244b3f68cecf28ae0146747ff15f7dc2b8390)

- **作者**: Mick
- **时间**: 2026-08-25T07:43:30Z
- **提交信息**: [diffusion] feat: support loading Comfy NVFP4-AWQ text encoders (#36046)

### [bf1e03f](https://github.com/sgl-project/sglang/commit/bf1e03f7123edb75b0ce5e8295f2ef9bcfb7f6a3)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-25T07:27:33Z
- **提交信息**: [MegaMoE] Respect padded MXFP8 scale row strides in pre-dispatch (#36237)

Co-authored-by: yangliu991 <yangliu991@fb.com>

### [e2b5093](https://github.com/sgl-project/sglang/commit/e2b50930b9316719825c7ebcfbe40f16403d34a0)

- **作者**: unclezhou
- **时间**: 2026-08-25T07:13:12Z
- **提交信息**: [NPU] DeepSeek-V4 adapt sgl-kernel-npu ops (compressor/sparse-attn/sparse-attn-metadata) (#35676)

Co-authored-by: vstone-w <374330057@qq.com>
Co-authored-by: unclezhou486 <154310456@qq.com>
Co-authored-by: 摆渡人 <2044145178@qq.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1257
- **最后更新**: 2026-08-25T03:59:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90027
- **最后更新**: 2026-08-25T21:58:52Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 18
- **主要提交者**: Nick Hill, Wentao Ye, Yan Ma

## AI分析总结

# vLLM 仓库提交分析报告

## 一、主要更新类型

本批次共27个提交，涵盖以下类型：
- **Bug修复**（约10个）：涉及多模态、前端、Tokenizer、Profiler等多个模块
- **性能优化**（约4个）：包括Blackwell平台Triton内核、K3 Mamba元数据等
- **功能新增**（约3个）：DSpark自适应验证、MXFP4量化支持、Agent微基准测试技能
- **CI/测试改进**（约4个）：Docker缓存、GSM8K准确率测试、ROCm测试跳过
- **代码重构**（约3个）：sleep功能重构、前端文件移动、Mypy类型修复
- **配置改进**（约2个）：编码器配置规范化、任务错误提示优化

## 二、关键变更点与项目方向

1. **确定性执行保障**：`fuse_allreduce_rms`在`VLLM_BATCH_INVARIANT`下禁用，解决TP下的非确定性，体现vLLM对可复现推理的重视。
2. **Blackwell性能优化**：Triton内核自动调优实现33.6%端到端延迟降低，直接强化vLLM“快速”服务定位。
3. **DeepSeek V4系列支持**：多个提交围绕DeepSeek V4的Tokenizer、提示渲染、AMD平台测试，显示对最新模型的快速适配能力。
4. **DSpark稀疏MLA**：SM100上的自适应DSpark及Logprobs自适应验证，推进稀疏注意力技术前沿。
5. **量化方案扩展**：MXFP4权重+块FP8激活的MoE支持，丰富低成本部署选项。

## 三、项目影响与潜在意义

- **稳定性提升**：多个Bug修复（音频400错误、Gemma4工具调用、JinaVL缓存顺序）直接改善用户体验。
- **安全加固**：Rust前端日志中移除凭据，防止敏感信息泄露。
- **开发效率**：Rust Docker缓存保留、Mypy类型修复、代码重构均降低维护成本。
- **多平台覆盖**：XPU模型更新、ROCm测试适配、AMD DeepSeek测试，扩展硬件生态。

## 四、值得关注的技术点

1. **Cudagraph内存分析**：在一次性图池中运行，避免内存碎片问题。
2. **批不变性（Batch Invariance）**：作为核心设计原则，在性能与确定性间寻求平衡。
3. **K3 Mamba优化**：元数据准备优化带来6.6-7.6倍内核性能提升。
4. **编码器配置规范化**：生产者专用编码器配置处理，提升多模态模型灵活性。

## 五、对项目发展的影响

vLLM持续巩固其作为“易用、快速、廉价”LLM服务框架的定位。本批次提交体现了三个战略方向：**性能极致优化**（Blackwell、K3）、**生态广度扩展**（DeepSeek V4、XPU、ROCm、MXFP4）和**工程成熟度提升**（确定性、安全性、CI效率）。特别是对DeepSeek V4和AMD平台的密集支持，表明vLLM正积极拥抱新兴模型和硬件生态，保持行业领先地位。

## 详细提交记录

### [80771bb](https://github.com/vllm-project/vllm/commit/80771bbbddf9e5153eea3aca8055049ee5aaaed1)

- **作者**: Donald Tolley
- **时间**: 2026-08-25T19:16:09Z
- **提交信息**: [Core] Disable fuse_allreduce_rms under VLLM_BATCH_INVARIANT (non-deterministic under TP) (#51292)

Signed-off-by: Don Tolley <tolleybot@gmail.com>
Signed-off-by: tolleybot <tolleybot@gmail.com>
Co-authored-by: yewentao256 <yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0e30bd6](https://github.com/vllm-project/vllm/commit/0e30bd62fedfad509e045b01e4aed1ef82ff6dbf)

- **作者**: Wentao Ye
- **时间**: 2026-08-25T19:06:14Z
- **提交信息**: [CI Bug] Fix kimi test `AssertionError: Aligned Mamba state indices must be precomputed` (#53766)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [384d079](https://github.com/vllm-project/vllm/commit/384d07969771a988eef0e2030ef6ac92b0e8b75e)

- **作者**: Wentao Ye
- **时间**: 2026-08-25T19:06:01Z
- **提交信息**: [Perf] Autotune batch invariance triton kernel in blackwell, 33.6% E2E latency reduction (#53649)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [e6cc089](https://github.com/vllm-project/vllm/commit/e6cc0899b6e29ad613efae572eb98e0d776afe4d)

- **作者**: Nick Hill
- **时间**: 2026-08-25T18:52:15Z
- **提交信息**: [Bugfix][MRV2] Run cudagraph memory profiling in a throwaway graph pool (#53682)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [c9331d8](https://github.com/vllm-project/vllm/commit/c9331d8064808e3402ec79ae8631f48cebdc827a)

- **作者**: Misha Goin
- **时间**: 2026-08-25T18:13:36Z
- **提交信息**: [CI] Preserve Rust Docker cache across commits (#53290)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [299ebd0](https://github.com/vllm-project/vllm/commit/299ebd094a9cea1a16077dc2a4419192b85a777c)

- **作者**: Moe Huzaifa
- **时间**: 2026-08-25T17:31:42Z
- **提交信息**: [Bugfix][Multimodal] Reject malformed base64 audio with 400 instead of 500 (#53744)

Signed-off-by: mhuzaifa3 <mhuzaifa3@outlook.com>

### [7de9605](https://github.com/vllm-project/vllm/commit/7de96050c530009eb8e81065aea76570fc6ed15b)

- **作者**: Misha Goin
- **时间**: 2026-08-25T17:31:15Z
- **提交信息**: [Spec Decode] Enable adaptive DSpark on SM100 sparse MLA (#52783)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [70021a0](https://github.com/vllm-project/vllm/commit/70021a0081cc10d8862f7458c36353b72ea9b5f4)

- **作者**: Wentao Ye
- **时间**: 2026-08-25T16:47:16Z
- **提交信息**: [Mypy Fix] Mypy fix for "vllm/model_executor/models/[gG]" (#53616)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [217a0b5](https://github.com/vllm-project/vllm/commit/217a0b5cefec3f0f4a011cb498afcbf211f8bc25)

- **作者**: Moe Huzaifa
- **时间**: 2026-08-25T16:41:08Z
- **提交信息**: [Bugfix][Frontend] Apply the stop string limit to Cohere requests (#53750)

Signed-off-by: mhuzaifa3 <mhuzaifa3@outlook.com>

### [3e83393](https://github.com/vllm-project/vllm/commit/3e833933dcaa8456ce8eb0541b8df06ffa8d06a3)

- **作者**: Moe Huzaifa
- **时间**: 2026-08-25T16:32:12Z
- **提交信息**: [Bugfix][Frontend] Keep credentials out of the Rust frontend launch log (#53738)

Signed-off-by: mhuzaifa3 <mhuzaifa3@outlook.com>

### [19406fa](https://github.com/vllm-project/vllm/commit/19406fae287380991908d2f27fe3975ba047147d)

- **作者**: Moe Huzaifa
- **时间**: 2026-08-25T16:30:23Z
- **提交信息**: [Bugfix][Tokenizer] Replace bare asserts in the DeepSeek V4 encoder (#53747)

Signed-off-by: mhuzaifa3 <mhuzaifa3@outlook.com>

### [3454335](https://github.com/vllm-project/vllm/commit/3454335f7b64e31fd385e36eb590d76d08c84a92)

- **作者**: Luke Alonso
- **时间**: 2026-08-25T16:20:15Z
- **提交信息**: [Bugfix] Resolve B12X modules before Dynamo tracing (#53326)

Signed-off-by: Luke Alonso <lalonso@gmail.com>

### [bc11eca](https://github.com/vllm-project/vllm/commit/bc11ecaf4e6aeaa0d6a18567d59d75a90207444e)

- **作者**: Colin Z
- **时间**: 2026-08-25T16:06:58Z
- **提交信息**: [CI] Add GSM8K accuracy test for amd/DeepSeek-V4-Flash-MXFP4 (#50632)

Signed-off-by: Colin Zeng <Colin.Zeng@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [10ade93](https://github.com/vllm-project/vllm/commit/10ade939796611915ee481da076a897c0c54fcf3)

- **作者**: Yan Ma
- **时间**: 2026-08-25T15:10:48Z
- **提交信息**: [XPU] update key supported models (#53494)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [41729fc](https://github.com/vllm-project/vllm/commit/41729fc53b02cb09beda2a1ced690d021443be43)

- **作者**: Wentao Ye
- **时间**: 2026-08-25T15:00:28Z
- **提交信息**: [K3 Perf] Optimize k3 mamba metadata preparation, 6.6~7.6x kernel performance improvement (#52388)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d5cadce](https://github.com/vllm-project/vllm/commit/d5cadcee8641a9fcec15facb5a9157d157daa207)

- **作者**: Naveenraj Kamalakannan
- **时间**: 2026-08-25T14:22:33Z
- **提交信息**: [Feature][DSpark]: Logprobs adaptive verification (#52242)

Signed-off-by: Naveenraj Kamalakannan <therealnaveenkamal@gmail.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [ca29cd4](https://github.com/vllm-project/vllm/commit/ca29cd48ba05ac9ae1c9fa29271e9f899bc4ce56)

- **作者**: Elvir Crnčević
- **时间**: 2026-08-25T14:21:00Z
- **提交信息**: [Quantization][Humming] Support MXFP4 weight + block-FP8 activation for MoE (#51332)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Elvir Crnčević <elvircrn@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [9c8e90e](https://github.com/vllm-project/vllm/commit/9c8e90eb2637a863ca14e47fd436b10ed7ba6536)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-25T12:21:42Z
- **提交信息**: [Bugfix] Handle parenthesized Gemma4 tool calls (#53657)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [2014e47](https://github.com/vllm-project/vllm/commit/2014e4748502d5526fd515d2289a87d046e717a1)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-25T12:20:10Z
- **提交信息**: [Pooling UX] Improve serve --task error guidance (#53467)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [afc91fa](https://github.com/vllm-project/vllm/commit/afc91fa0d2eb8bc050d80e9bcd74c8b1d72b4191)

- **作者**: Elvir Crnčević
- **时间**: 2026-08-25T12:13:29Z
- **提交信息**: [Profiler] Fix start_profile permanently no-op after max_iterations auto-stop (#51839)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>

### [d9fbe52](https://github.com/vllm-project/vllm/commit/d9fbe526c0787eb5e6dd1e3e4d9b88848d21bc6b)

- **作者**: djramic
- **时间**: 2026-08-25T08:07:09Z
- **提交信息**: [ROCm][CI] Skip ModernBERT FP8 MTEB test when no FP8 ScaledMM kernel exists (#53589)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [12c84b9](https://github.com/vllm-project/vllm/commit/12c84b98ddeb71186da8b77382b0fad71ad03c8c)

- **作者**: Tianyu Guo
- **时间**: 2026-08-25T07:53:04Z
- **提交信息**: [Config][EC] Normalize producer-only encoder config (#53656)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [59d7fc9](https://github.com/vllm-project/vllm/commit/59d7fc92ea038544959aae020a8b28fc34159545)

- **作者**: Jiahao Liang
- **时间**: 2026-08-25T07:49:44Z
- **提交信息**: [Bugfix][DeepSeek V4] Handle trailing system messages in prompt rendering (#51262)

Signed-off-by: jiahaoliang <gzliangjiahao@gmail.com>
Signed-off-by: Jiahao Liang <gzliangjiahao@gmail.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [23310bc](https://github.com/vllm-project/vllm/commit/23310bc3de530fd90ea060fcc1ef7f58501ee859)

- **作者**: Ning Xie
- **时间**: 2026-08-25T07:45:20Z
- **提交信息**: [sleep functionality] code refactor about sleep/wake_up (#50431)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [5e379a3](https://github.com/vllm-project/vllm/commit/5e379a361e3ea8bb82b7efd768c36f39a0cf32fd)

- **作者**: Thien Tran
- **时间**: 2026-08-25T07:25:27Z
- **提交信息**: [Agents] Add kernel microbenchmark skill (#53688)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Codex <codex@openai.com>

### [06ecec7](https://github.com/vllm-project/vllm/commit/06ecec7a8424106dc80c5c40bb0cc22bcc6da667)

- **作者**: Jiatai Wang
- **时间**: 2026-08-25T07:03:05Z
- **提交信息**: [Bugfix][MM] Fix JinaVL processing cache order (#53553)

Signed-off-by: JiataiWang <wangjiatai@proton.me>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [735daf8](https://github.com/vllm-project/vllm/commit/735daf8ef64b7e4b2db9b7186c8160d335cb528f)

- **作者**: wang.yuqi
- **时间**: 2026-08-25T07:02:32Z
- **提交信息**: [Frontend] Move cli_args.py and dp_supervisor.py out openai folder (#53659)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-26
**监控日期**: 2026-08-25
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6326
- **最后更新**: 2026-08-25T22:31:39Z

## 提交统计

- **昨日提交总数**: 16
- **提交者数量**: 12
- **主要提交者**: wy17003, Bo Li, NumberWan

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交涵盖**Bug修复**（4项）、**CI/测试优化**（4项）、**性能优化**（3项）、**功能新增**（2项）、**文档更新**（1项）、**重构**（1项）及**示例整理**（1项），整体呈现多维度协同推进态势。

### 2. 关键变更点与项目方向的关系
- **环境变量配置文档化**（#6217、#6631）：系统梳理并校准环境变量清单，提升项目可配置性和可维护性，与“easy”理念直接呼应。
- **MiniMax-H3 DLO生命周期优化**（#6526）与**Qwen-Image性能修复**（#6525）：针对多模态模型推理路径进行深度优化，直接服务于“fast”目标。
- **MXFP4量化模型离线支持**（#5544）：扩展低比特量化生态，降低部署成本，契合“cheap”定位。
- **调度器重构**（#6149）：将硬编码阶段替换为可解析的传输能力，为后续架构演进奠定基础。

### 3. 对项目的影响和潜在意义
- **性能回归修复**（Qwen-Image）表明项目对线上质量的高度敏感，避免因调度参数映射错误导致用户体验下降。
- **DoS溢出处理**（#6598）增强服务安全性，对生产环境部署至关重要。
- **OmniInteract实时基准测试**（#6522）为多模态交互场景提供量化评估手段，有助于持续性能追踪。
- **CI精简与测试标记**（#6613、#6570、#6343）降低维护成本，提升开发效率，支撑项目快速迭代。

### 4. 值得关注的技术点
- **DLO（Direct Layer Offload）H2D mmap注册**（#6591）：针对扩散模型的高效内存映射优化，体现对硬件特性的深度挖掘。
- **TRTLLM无掩码打包路径**（#6542）：探索TensorRT-LLM后端性能边界，为高吞吐推理提供新选项。
- **调度器传输能力解析**（#6149）：架构层面的抽象升级，预示更灵活的流水线编排能力。

### 5. 对项目发展的影响
vllm-omni致力于打造**易用、快速、低成本的全模态模型服务**。本批提交从**文档完善、性能调优、安全加固、架构重构、生态扩展**五个维度同步推进：文档建设降低上手门槛，性能优化强化核心竞争力，安全修复保障生产可靠性，架构重构预留扩展空间，量化支持与基准测试则拓宽应用场景。整体上，这些变更体现了项目在**从“可用”向“好用”** 迈进过程中的系统性投入，尤其对多模态推理路径的持续打磨，将巩固其在全模态服务领域的差异化优势。

## 详细提交记录

### [a708ae5](https://github.com/vllm-project/vllm-omni/commit/a708ae5b7aac7ccd86f63cdc7cb853d68ede3284)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-25T22:13:28Z
- **提交信息**: [Bugfix] Reconcile env-var inventory with post-#6217 main drift (#6631)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [780e8d4](https://github.com/vllm-project/vllm-omni/commit/780e8d40aa01cddb686472e3e60e5c7e6f117a09)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-25T20:58:54Z
- **提交信息**: [Doc] Add environment variables configuration reference (#6217)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [6639c82](https://github.com/vllm-project/vllm-omni/commit/6639c82a171c4801895dae658a7feb8a6295f522)

- **作者**: Satellite
- **时间**: 2026-08-25T16:16:46Z
- **提交信息**: [CI/Build] Pin GGUF plugin for diffusion nightly tests (#6303)

Signed-off-by: Xin Wei <14196318+wxwxwwxxx@users.noreply.github.com>

### [0eb47b7](https://github.com/vllm-project/vllm-omni/commit/0eb47b76d06d563c5d7d59a24865cc92c0dcf08e)

- **作者**: Alex Brooks
- **时间**: 2026-08-25T16:09:03Z
- **提交信息**: [Bugfix] Handle DoS Overflow Cases (#6598)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [497c537](https://github.com/vllm-project/vllm-omni/commit/497c537c6f70e44f376b491bf7b50395cf2cba5d)

- **作者**: NATURE
- **时间**: 2026-08-25T15:32:58Z
- **提交信息**: [Benchmark] Add local OmniInteract realtime benchmark (#6522)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [c608910](https://github.com/vllm-project/vllm-omni/commit/c608910d20bdd9d56a7570d47cbd52c4a7777395)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-25T15:30:11Z
- **提交信息**: [Diffusion] Register HWR mmap for direct DLO H2D (#6591)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Signed-off-by: hsliuustc0106 <hsliuustc0106@users.noreply.github.com>
Co-authored-by: hsliuustc0106 <hsliuustc0106@users.noreply.github.com>

### [5a8b81e](https://github.com/vllm-project/vllm-omni/commit/5a8b81ebebd28b5bc23a8a0721d39998496e7015)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-25T15:13:41Z
- **提交信息**: [Model] Optimize MiniMax-H3 DLO component lifecycle (#6526)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [dd527b4](https://github.com/vllm-project/vllm-omni/commit/dd527b42456ad29d5df4fdbfa56040b3c196a75f)

- **作者**: NumberWan
- **时间**: 2026-08-25T14:55:15Z
- **提交信息**: [CI] Reduce Qwen-Image Function and share step-execution perf server (#6613)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [0d5d111](https://github.com/vllm-project/vllm-omni/commit/0d5d1115d6f0b8be86b7b9f003705b6698540887)

- **作者**: jl9876
- **时间**: 2026-08-25T14:44:38Z
- **提交信息**: [AutoRound] Add offline quantized MXFP4 model support (#5544)

Signed-off-by: jl9876 <jia.li@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [683f3c9](https://github.com/vllm-project/vllm-omni/commit/683f3c92a4750101d132dc61fe4b959fbdb11704)

- **作者**: psv666
- **时间**: 2026-08-25T14:14:43Z
- **提交信息**: [CI/Build] Clean up Qwen3-Omni nightly tests (#6570)

Signed-off-by: psv666 <2693925048@qq.com>

### [72beeae](https://github.com/vllm-project/vllm-omni/commit/72beeaee869f19bede9f10077414e1d950845599)

- **作者**: Jae
- **时间**: 2026-08-25T14:02:26Z
- **提交信息**: [Misc] move text-to-audio online examples to a unified folder (#4807)

Signed-off-by: zzehli <jaeli_ottawa@outlook.com>

### [d6b66fa](https://github.com/vllm-project/vllm-omni/commit/d6b66faba7c22d1fc99c67d87dcb68ec6e714cb8)

- **作者**: Bhavyansh Sharma
- **时间**: 2026-08-25T11:47:09Z
- **提交信息**: [CI] Fix response_format json_schema error expectation (#6290)

Signed-off-by: Bhavyansh Sharma <66562679+clumsylad21@users.noreply.github.com>

### [bc8ea48](https://github.com/vllm-project/vllm-omni/commit/bc8ea489effb5fc7aa3934ceb9f915a27765a40d)

- **作者**: NumberWan
- **时间**: 2026-08-25T10:36:11Z
- **提交信息**: [BugFix] Qwen-image performance regressed - Avoid mapping diffusion_batch_size onto scheduler max_num_seqs (#6525)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [29e3165](https://github.com/vllm-project/vllm-omni/commit/29e3165bb938088d007cad9094cf66154c8d88c1)

- **作者**: zhumingjue138
- **时间**: 2026-08-25T09:08:58Z
- **提交信息**: [Test] add marker for stability and add Wan2.2 npu test case (#6343)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [51b7565](https://github.com/vllm-project/vllm-omni/commit/51b7565f33017d74e2da7045327a65e8f048eaae)

- **作者**: Bo Li
- **时间**: 2026-08-25T07:45:21Z
- **提交信息**: [perf] Add mask-free TRTLLM packed-padding path (#6542)

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [b454e34](https://github.com/vllm-project/vllm-omni/commit/b454e34966f3d14d1605f29aca19c962d3a16152)

- **作者**: wy17003
- **时间**: 2026-08-25T07:24:59Z
- **提交信息**: [Refactor][2/N Scheduler]Replace _FULL_PAYLOAD_INPUT_STAGES with a resolved stage transport capability. (#6149)

Signed-off-by: wy17003 <yaow17003@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
