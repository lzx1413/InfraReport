# GitHub Stars 合并报告 - 2026-03-20

**合并日期**: 2026-03-21
**监控日期**: 2026-03-20
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


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1745
- **最后更新**: 2026-03-20T22:38:17Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: 鐘天楽, Ting

## AI分析总结

根据您提供的仓库README摘要和提交记录，结合VeOmni项目“为任意模态模型训练提供模型中心化分布式方案”的核心目标，以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **功能新增**：两项提交均为新增功能。
    *   `1c9e7fc`: 为分布式训练新增对特定计算后端（EP）的支持。
    *   `8839fb3`: 为数据处理新增对非整除帧对齐场景的支持。

### 2. 关键变更点及其与项目整体方向的关系
*   **扩展分布式训练能力 (`1c9e7fc`)**：
    *   **变更点**：为合并的`fc1`层和`quack` GEMM后端添加了EP（推测为“Execution Provider”，如特定硬件或计算后端）支持。
    *   **与项目方向关系**：直接服务于项目“**Scaling** ... Training with **Model-Centric Distributed Recipe**”的核心目标。通过支持更多、更高效的计算后端，增强了框架在复杂模型（尤其是涉及全连接层和特定矩阵运算的模型）上的分布式训练能力和硬件适配性，是“分布式方案”的具体实现和优化。

*   **增强数据预处理灵活性 (`8839fb3`)**：
    *   **变更点**：支持`frame_factor_remainder`，处理视频/序列数据帧数无法被设定因子（如采样率）整除时的对齐问题。
    *   **与项目方向关系**：紧扣“**Any Modality**”这一目标。视频是重要的模态之一，此更新使数据处理管道更能适应真实世界数据的不规则性，提升了框架处理多模态数据（尤其是时序视觉数据）的鲁棒性和实用性，是支持“任意模态”的基础设施完善。

### 3. 对项目的影响和潜在意义
*   **提升训练效率与兼容性**：EP支持的扩展可能意味着对新型硬件（如特定AI加速卡）或优化计算库更好的利用，有望直接提升大规模训练的效率和速度。
*   **提高数据处理的实用性与精度**：更灵活的视频帧处理能减少因强制对齐造成的信息丢失或扭曲，对于视频理解、生成等任务的质量有潜在积极影响。
*   **降低使用门槛**：自动处理非整除情况，减少了用户预处理数据的负担，使框架更易用。

### 4. 值得关注的技术点
*   **`quack GEMM`后端**：这可能是一个专有或高度优化的矩阵乘法计算后端，关注其性能特点及与特定硬件的关联。
*   **`frame_factor_remainder`的处理策略**：具体如何处置“余数”帧（如丢弃、填充、加权平均等），这直接影响数据保真度和下游任务性能。
*   **“合并的fc1层”**：可能暗示模型结构上的特定优化或定制，例如将多个全连接层融合以提升计算效率，反映了框架对模型性能的深度优化。

### 5. 基于项目背景的提交影响分析
VeOmni旨在成为**多模态、大规模模型训练的分布式基础设施**。昨日的更新虽看似具体，但精准地推动了这一宏观目标：
*   **纵向深化（Scaling）**：`1c9e7fc`提交通过扩展底层计算支持，**强化了分布式训练栈的深度和效率**，使框架能更好地驾驭更大、更复杂的模型，是“**Scaling**”目标的技术落实。
*   **横向拓展（Any Modality）**：`8839fb3`提交通过完善视频数据处理细节，**拓宽了框架所支持数据模态的覆盖面和适应能力**，确保了“**Any Modality**”不只停留在口号，而是能处理实际数据中的各种边界情况。
*   **整体协同**：两项更新分别从**计算**和**数据**两个关键维度同时推进，体现了项目在提升端到端训练流水线能力上的均衡发展，共同巩固了其作为**全面、鲁棒的多模态分布式训练解决方案**的定位。

**总结**：昨日的更新是两项针对性强、务实的功能新增，分别从**底层计算优化**和**上层数据适配**两个方面，扎实地推进了VeOmni项目在**大规模**和**多模态**两个核心方向上的能力建设。

## 详细提交记录

### [1c9e7fc](https://github.com/ByteDance-Seed/VeOmni/commit/1c9e7fce8fa3cac3796da1e8f138f9076ce00de7)

- **作者**: 鐘天楽
- **时间**: 2026-03-20T18:38:43Z
- **提交信息**: [ops, dist] feat: Add EP support for merged fc1 and quack GEMM backends (#588)

### [8839fb3](https://github.com/ByteDance-Seed/VeOmni/commit/8839fb362c018cf98996e67d5848edcc8699df74)

- **作者**: Ting
- **时间**: 2026-03-20T08:58:48Z
- **提交信息**: [data] feat: support frame_factor_remainder for non-divisible frame alignment (#587)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2081
- **最后更新**: 2026-03-20T16:29:47Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Musisoul, Shiqiao Gu (谷石桥)

## AI分析总结

根据您提供的仓库README摘要和提交记录，结合项目“LightX2V: Light Video Generation Inference Framework”的背景，以下是昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增**：提交 `6d45f47` 为 `seedvr2` 模块增加了对长视频输入的支持。
*   **代码优化/修复**：提交 `a75f590` 更新了 `converter.py` 文件，可能涉及功能优化、Bug修复或代码改进。

### 2. 关键变更点及其与项目整体方向的关系
*   **扩展输入能力**：`seedvr2` 支持长视频输入，直接**增强了框架的输入处理能力**，使其能应对更复杂、更长的视频生成任务。
*   **工具链完善**：更新 `converter.py` 这类核心工具文件，**提升了框架的健壮性或易用性**，是维护高质量基础设施的一部分。
*   **关系**：这两项变更都紧密围绕项目的核心目标——**构建一个轻量、高效的视频生成推理框架**。支持长视频输入扩展了应用场景，而工具优化则确保了框架的稳定和高效运行。

### 3. 对项目的影响和潜在意义
*   **提升实用性**：长视频支持能力使框架能处理更真实的视频生成需求，**拓宽了潜在的应用范围**（如短视频生成、长片段编辑）。
*   **改善用户体验**：优化核心转换工具可能意味着更快的处理速度、更少的错误或更友好的接口，**直接提升开发者体验**。
*   **技术债管理**：定期更新和优化核心模块，有助于**保持代码库健康，降低长期维护成本**。

### 4. 值得关注的技术点
*   **长视频处理技术**：`seedvr2` 如何实现对长视频的高效分割、特征提取或内存管理，是**视频生成领域的常见挑战**，其解决方案值得关注。
*   **转换器优化**：`converter.py` 的具体改动（虽未详述）可能涉及**模型格式转换、数据处理流水线或性能优化**，这些都是影响推理效率的关键环节。

### 5. 基于项目背景的提交影响分析
LightX2V 定位为 **“轻量级视频生成推理框架”**，强调高效与易用。昨日的更新：
*   **强化核心能力**：通过支持长视频输入，框架向处理 **“更复杂现实任务”** 迈进一步，增强了其作为**通用视频生成工具**的竞争力。
*   **巩固技术基础**：持续优化 `converter.py` 这类底层工具，体现了对**框架稳定性与性能**的重视，这与“轻量高效”的目标一致，确保推理流程顺畅可靠。
*   **发展态势**：这些提交表明项目处于**积极的功能扩展和代码优化阶段**，不仅关注新增特性，也注重夯实基础，是项目健康迭代、向更成熟阶段发展的标志。

## 详细提交记录

### [6d45f47](https://github.com/ModelTC/LightX2V/commit/6d45f476009d1f0078ac670099fb0abe20bf8253)

- **作者**: Musisoul
- **时间**: 2026-03-20T10:56:14Z
- **提交信息**: Support long video input in seedvr2 (#953)

### [a75f590](https://github.com/ModelTC/LightX2V/commit/a75f5906788b99b35c24bf9659611056f338bc44)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-03-20T09:28:04Z
- **提交信息**: Update converter.py (#956)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1975
- **最后更新**: 2026-03-20T13:47:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5189
- **最后更新**: 2026-03-20T22:03:32Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: DevashishLal-CB, Ka-Hyun Nam, akshaver

## AI分析总结

根据FlashInfer仓库的README摘要（专注于“高性能GPU推理内核”）和昨日提交记录，以下是分析总结：

### 1. 主要更新类型
昨日提交以 **Bug修复** 和 **性能优化** 为主，辅以少量功能完善和代码质量改进。
- **Bug修复** (4项): 涉及Python API导出、自动调优器、多节点NVLink检测和弃用警告。
- **性能优化** (1项): 针对稀疏MLA解码内核选择启发式算法的显著提升。
- **代码/构建修复** (1项): 为特定GPU架构启用CUTLASS GEMM的网格依赖控制(GDC)，确保并发正确性。

### 2. 关键变更点及其与项目方向的关系
| 提交 | 关键变更点 | 与项目方向的关系 |
| :--- | :--- | :--- |
| **af1e02d** | 在Python `__init__.py` 中补全 `rmsnorm_quant` 和 `fused_add_rmsnorm_quant` 的导出。 | **完善API**：确保用户能方便地访问所有量化归一化函数，提升库的易用性和完整性。 |
| **c72f62a** | 优化TRT-LLM FMHA中稀疏MLA解码内核的选择启发式算法，重构选择循环。 | **核心性能优化**：直接提升特定配置（如DeepSeek-V3, numHeadsQ=64）下的解码速度达1.35-2.74倍，强化了项目在**高效注意力机制**上的领先地位。 |
| **8e1642a** | 为SM100+架构的CUTLASS GEMM内核启用GDC，修复并发执行时的数据竞争问题。 | **确保正确性与并发性能**：解决底层计算内核在流并发时可能产生NaN/垃圾数据的问题，保障了**高性能矩阵计算**基础的可靠性。 |
| **e679e45** | 修复自动调优器对非2的幂次方`num_tokens`的处理，并为TRT-LLM融合MoE内核创建所有支持的tileN启动器。 | **提升鲁棒性与兼容性**：解决了自动调优和MoE内核在边缘情况下的崩溃问题，使系统对**多样化工作负载**更稳定。 |
| **7cb016d** | 为`gated_delta_rule_mtp`的`intermediate_states_buffer=True`参数添加弃用警告。 | **API演进管理**：提前通知用户未来默认行为的变更，有助于平滑过渡，维护良好的用户体验。 |
| **1313ec0** | 防护单节点NVSwitch环境下`clusterUuid`为空导致的`IndexError`。 | **增强部署稳定性**：修复了可能导致所有TP工作进程在启动时崩溃的严重问题，提升了在**复杂GPU集群环境**下的健壮性。 |

### 3. 对项目的影响和潜在意义
- **性能大幅提升**：稀疏MLA解码的优化对使用类似DeepSeek-V3架构的大模型推理有直接的加速效果，巩固了FlashInfer在性能竞赛中的优势。
- **稳定性增强**：多个Bug修复（尤其是自动调优器、MoE内核、NVLink检测）减少了生产环境中的崩溃风险，提升了库的成熟度和可信度。
- **开发者体验**：补全API导出和添加弃用警告，使得库更易于使用和维护。
- **底层正确性保障**：GDC的修复确保了高级别并发优化（如内核重叠）的基础正确性，避免了难以调试的数值错误。

### 4. 值得关注的技术点
- **启发式内核选择** (`c72f62a`)：根据`numHeadsQ`、`batchSize`和GPU流处理器(MP)利用率动态选择`KeepsMmaAb`/`SwapsMmaAb`策略和`tileSizeQ`，是典型的**性能可移植性**优化。
- **网格依赖控制(GDC)** (`8e1642a`)：深入到了CUDA内核与CUTLASS库的交互层面，展示了在利用第三方高性能库时，如何确保**并发同步**的正确性。
- **自动调优与MoE集成** (`e679e45`)：揭示了在**混合专家模型**等复杂算子中，自动调优缓存策略与内核启动配置之间微妙的交互问题及解决方案。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供**高性能GPU推理内核**。昨日的提交完美契合了这一方向：
1. **强化核心优势**：对注意力机制(`c72f62a`)和矩阵计算(`8e1642a`)的优化与修复，直接提升了**推理速度**和**计算可靠性**这两个最核心的指标。
2. **拓展适用场景**：修复MoE(`e679e45`)和NVLink检测(`1313ec0`)的问题，使得FlashInfer能够更稳定地支持**更大、更复杂的模型**（如MoE模型）和**更广泛的硬件部署环境**（从单卡到多节点集群）。
3. **完善产品化能力**：通过修复边缘Case、完善API、管理弃用，项目正在从纯粹的“高性能内核集合”向一个**稳定、易用、可维护的工业级推理库**演进，这对于其被更广泛地集成到（如vLLM等）推理框架中至关重要。

**总结**：昨日更新是一次高质量的迭代，在**不引入新功能**的前提下，专注于**打磨现有核心组件的性能、正确性和健壮性**。这标志着项目

## 详细提交记录

### [af1e02d](https://github.com/flashinfer-ai/flashinfer/commit/af1e02dbf513d1d4dd2d2a1a38de3a2c53c04c19)

- **作者**: DevashishLal-CB
- **时间**: 2026-03-20T22:02:36Z
- **提交信息**: fix: add missing re-exports for rmsnorm quant and fused_add_rmsnorm q… (#2783)

add missing re-exports for rmsnorm quant and fused_add_rmsnorm quant

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

added missing imports in the top level `flashinfer/__init__.py` file
- rmsnorm_quant
- fused_add_rmsnorm_quant

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
* Two additional normalization quantization functions are now publicly
available from the flashinfer package API.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Devashish Lal <devcode@fb.com>
Co-authored-by: Devashish Lal <devcode@fb.com>

### [c72f62a](https://github.com/flashinfer-ai/flashinfer/commit/c72f62aa9582c71c5342ae31f39125d2992b1c4a)

- **作者**: Perkz Zheng
- **时间**: 2026-03-20T21:29:35Z
- **提交信息**: [Fmha] Sparse MLA decode kernel selection heuristics (#2836)

<!-- .github/pull_request_template.md -->

## 📌 Description

## Summary

Improve kernel-selection heuristic in FlashInfer's trtllm-gen FMHA
runner (SM100/SM103 sparse MLA decode), and
cleans up the kernel selection loop in `run()`.

### Changes

**`selectSparseMlaGenerationKernel()` (new function)**

Separates sparse MLA selection from the generic generation path with
tuned per-config heuristics:

- **numHeadsQ=64 (KeepsMmaAb, tileSizeQ=64)** — previously selected
  SwapsMmaAb (tileSizeQ=16); this is the main perf win (see below).
- **numHeadsQ=128 (KeepsMmaAb)** — batch-aware 1CTA/2CTA selection:
  use 2CTA when `batchSize * numCtasPerToken * 8 > MP` (avoids
  under-utilizing SM at small batch).
- **numHeadsQ≤32 (SwapsMmaAb)** — batch-aware tileSizeQ halving at
  batch=1: use tileSizeQ/2 when `batchSize * maxNumCtasPerSeqKv ≤ MP/8`
  (doubles head-splitting parallelism when GPU is under-utilized).
- **CgaSmemReduction guard** scoped to MLA kernels only: suppress for
  tileSizeQ≥32 (headDimQk=576 exceeds smem budget); non-MLA paths
  unaffected.

**`run()` refactoring**

- Replaces the unbounded `while (mSelectNewKernel)` loop with a bounded
  `for` loop (`kMaxKernelSelectionPasses=4`), making convergence
  explicit and verifiable.
- Extracts `buildLaunchConfig()` and `setNonPortableClusterIfNeeded()`
  as private helpers to eliminate duplicated inline setup.
- Replaces `!mSelectNewKernel` guards on `mMultiCtasKvMode` assignments
in `selectSparseMlaGenerationKernel` with an `isGmemReduction()` check,
  preserving `Disabled`/`CgaSmemReduction` modes set by
  `computeCtaAndClusterConfig` on re-entry.

**Artifact**

Updates `TRTLLM_GEN_FMHA` cubin checksum for new KeepsMmaAb sparse
variants required by the numHeadsQ=64 path.

---

## Benchmark — Sparse MLA decode speedup (SM100, DeepSeek-V3 config)

GPU: B200, topK=128, seqlen=[1k–32k], dtype=[bf16, fp8]

| numHeadsQ | batch | Speedup range |
|-----------|-------|---------------|
| 64        | 32    | 1.35–1.72x    |
| 64        | 128   | 2.17–2.74x    |
| 64        | 512   | 2.23–2.50x    |
| 32        | 128   | 1.24–1.59x    |
| 32        | 512   | 1.28–1.50x    |
| 16/128    | all   | ~1.0x (neutral, path unchanged) |

The numHeadsQ=64 improvement (1.35–2.74x) comes entirely from switching
to KeepsMmaAb/tileSizeQ=64 (previously SwapsMmaAb/tileSizeQ=16).
---

## Tests

- `test_trtllm_gen_mla.py`: 4512/4512 passed (3168 skipped, SM100 only)
- `test_trtllm_gen_attention.py`: 20832/20832 passed (23544 skipped)

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/2797

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
* Fixed FMHA kernel selection logic to use bounded iteration instead of
unbounded loop, improving reliability and preventing potential
deadlocks.
* Updated internal artifact references and checksums for TRT-LLM FMHA
kernels.

* **New Features**
* Added kernel parameter configuration option for shared paged KV index
handling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8e1642a](https://github.com/flashinfer-ai/flashinfer/commit/8e1642a4ca29c6bbf8889638134690d862848b19)

- **作者**: Martin Vit
- **时间**: 2026-03-20T20:19:30Z
- **提交信息**: fix(jit): enable GDC for CUTLASS GEMM PDL — SM100 flag only (#2780)

## Summary

Re-applies #2716 (reverted in #2737) with the fix for the AOT build
failure.

**Only `-DCUTLASS_ENABLE_GDC_FOR_SM100=1`** is added. The
`-DCUTLASS_ENABLE_GDC_FOR_SM90=1` flag that broke AOT builds is
intentionally omitted.

## Why the original PR broke AOT

`sm90_gemm_tma_warpspecialized_cooperative.hpp:794` has a direct `#ifdef
CUTLASS_ENABLE_GDC_FOR_SM90` guard (not `CUTLASS_GDC_ENABLED`) that
calls `scheduler.is_last_tile()`. When compiling SM120 kernels with that
flag, the SM120 scheduler (`PersistentTileSchedulerSm100StreamK`)
doesn't have `is_last_tile()` → compilation error.

## Why SM100 flag alone is sufficient

CUTLASS 4.2.1 `grid_dependency_control.h` defines `CUTLASS_GDC_ENABLED`
for the entire SM100 family (SM100/101/103/120/121) when
`CUTLASS_ENABLE_GDC_FOR_SM100` is set. This enables
`griddepcontrol.wait` and `griddepcontrol.launch_dependents` device-side
barriers for all affected architectures.

## Why this is needed

All affected GEMM kernels hardcode `enablePDL=true`, which enables
host-side kernel overlap. Without the GDC compile flag, the device-side
synchronization barriers compile as no-ops → race condition →
NaN/garbage output tiles under concurrency.

## Affected modules

- `fp4_gemm_cutlass` (SM100)
- `fp4_gemm_cutlass_sm103` (SM103)
- `fp4_gemm_cutlass_sm120` (SM120)
- `fp8_gemm_cutlass` (SM100)
- `mxfp8_gemm_cutlass` (SM100)
- `gemm_sm120` (SM120 FP8 groupwise)

(`tgv_gemm` already had the SM100 flag.)

## Test plan

- [ ] AOT build with `FLASHINFER_CUDA_ARCH_LIST="12.1a"` (the exact
config that broke before)
- [ ] AOT build with full arch list `"7.5 8.0 8.9 9.0a 10.0a 12.0a"`
- [ ] FP4 GEMM correctness under concurrent streams on SM120

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated CUDA compilation configurations for matrix multiplication
kernels across multiple data format variants (FP4, FP8, MXFP8, BF16)
supporting additional GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [e679e45](https://github.com/flashinfer-ai/flashinfer/commit/e679e45383d2621681a06c39670448be59a817c9)

- **作者**: amitz-nv
- **时间**: 2026-03-20T19:38:48Z
- **提交信息**: fix: Autotuner _find_nearest_profile non-power-of-2 num_tokens, create launchers for all supported tileN in trtllm fused MoE (#2821)

## 📌 Description

It fixes two autotuner related bugs:
1. Revert back the autotuner fix that was reverted in
https://github.com/flashinfer-ai/flashinfer/pull/2697
2. Fix the issue that
https://github.com/flashinfer-ai/flashinfer/pull/2697 revealed, which is
trtllm fused MoE kernel launcher crash when it receives tileN that is
supported but filtered out by `computeSelectedTileN`, by creating kernel
launchers for all supported tileN values.

This PR continues the work in
https://github.com/flashinfer-ai/flashinfer/pull/2695 by @danisereb to
revert bugfix 1 and to fix bug 2.

More technical details:
### Bug 1:
When given num_tokens that isn't a power-of-2, the autotuner (python
side) fails to find its appropriate entry in the autotuner cache, so it
falls back to passing default, which means passing `[-1, -1]` as the
`(tileN, tactic)` to the CPP.
It was fixed in [this
PR](https://github.com/flashinfer-ai/flashinfer/pull/2617/changes#diff-1964ab957d8185d04b0d5f0cb02d0c7c0a3260ac0a6c573167af6875ab0b0e87L729-L734)
but soon after merge, it was reverted
[here](https://github.com/flashinfer-ai/flashinfer/pull/2697), as it
exposed the next bug.

### Bug 2 (exposed after fixing bug 1):
Crash in fused MoE kernel launcher on forward pass on some values of
num_tokens. The crash is at `launchers_map.at(tile_N)` in
`trtllm_fused_moe_kernel_launcher.cu`. It happens because:
The python side of the autotuner profiles num_tokens that are power of
2, and each such value represents the range until the next power of 2.
e.g.: The profile for the range `[2048, 4095]` is done on
num_tokens=2048.

`computeSelectedTileN` function in `trtllm_fused_moe_kernel_launcher.cu`
reduces the set of supported tileN values (to reduce the autotuner's
search space), by choosing specific values from the supported tileN
sorted list, the values are: `roundUpToPowerOfTwo(num_tokens * topK /
numExperts)`, its previous one, and its next 2 values (max value is
256). So values in the same range can get different sets of tileN
values.
For example, on Nemotron 3 Super NVFP4:
- `num_tokens=2048` -> `2048*22/512 = 88`, which rounds up to 128, so
the tileN set is `(64, 128, 256)`
- `num_tokens=3003` -> `3003*22/512 = 129.03`, which rounds up to 256,
so the tileN set is `(128, 256)`
In case `tileN=64` was found to be the fastest on `num_tokens=2048` for
range `[2048, 4095]`, when given `num_tokens=3003`, the python side
would pass `[64, someTactic]` to the CPP, but for `num_tokens=3003`,
there's no launcher for `tileN=64` as `computeSelectedTileN` filtered it
out.


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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Stricter MoE tile validation and ensured all supported tiles are
available at launch to avoid missing kernel configurations.
* Autotuner mapping for linked dynamic dimensions now yields consistent
cached bucket values.

* **Tests**
* Added SM100 MoE autotuner integration tests (including
invalid-cached-tactic checks).
* Re-enabled and expanded autotuner unit tests and added a test utility
to reset the autotuner.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Daniel Serebrenik <daserebrenik@nvidia.com>
Signed-off-by: amitz-nv <203509407+amitz-nv@users.noreply.github.com>
Co-authored-by: Daniel Serebrenik <daserebrenik@nvidia.com>

### [7cb016d](https://github.com/flashinfer-ai/flashinfer/commit/7cb016df2c35f9d229f8593b77523ef389073a76)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-03-20T17:26:22Z
- **提交信息**: fix: Deprecation for gated_delta_rule_mtp's intermediate_states_buffer=True (#2730)

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Deprecations**
* A deprecation notice has been introduced that alerts users when
relying on default behavior. The current default is scheduled to change
in a future release.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1313ec0](https://github.com/flashinfer-ai/flashinfer/commit/1313ec0df37acede39da7dea42be2ae6c04a1c1b)

- **作者**: akshaver
- **时间**: 2026-03-20T08:33:10Z
- **提交信息**: fix: Protect against null clusterUuid in mnnvl.py (#2626)

<!-- .github/pull_request_template.md -->

## 📌 Description

Guard against empty clusterUuid in is_mnnvl_fabric_supported().

On single-node cluster with NVSwitch, clusterUuid is all-zero bytes (no
multi-node NVLink cluster), per nvidia-smi
[documentation](https://docs.nvidia.com/deploy/nvidia-smi/index.html).
In code, ctypes truncates at the first null byte, producing an empty
string. The existing fabric_info.clusterUuid[0] != 0 check then raises
IndexError: string index out of range, crashing all TP workers at
startup.

The clusterUuid check itself is correct — cuMemCreate with
CU_MEM_HANDLE_TYPE_FABRIC requires an active multi-node NVLink domain
(non-zero ClusterUUID). The bug is only in failing to handle the
empty-string edge case from ctypes.

Fix: Add a len() guard so an empty clusterUuid safely returns False,
falling back to PosixFDHandleExchanger for single-node topologies.

## 🔍 Related Issues

Filed issue
[flashinfer-2633](https://github.com/flashinfer-ai/flashinfer/issues/2633).
This may have been why VLLM rolled back flashinfer from 0.6.4 to 0.6.3.

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
This is a trivial fix. I tested it in e2e tests, which passed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved detection of GPU fabric support to reduce incorrect status
reporting and improve stability in edge cases.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3250
- **最后更新**: 2026-03-20T21:22:50Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Kaiqin Kong

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复了训练与验证步骤不匹配的问题。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：解决了训练过程中“self-forcing”机制在训练和验证阶段行为不一致的问题（#1173）。
- **与项目方向的关系**：FastVideo 专注于高效视频生成与处理，训练稳定性直接影响模型性能与可靠性。此修复确保了训练流程的一致性，符合项目追求高精度、可复现模型训练的目标。

### 3. 对项目的影响和潜在意义
- **直接影响**：提升训练过程的稳定性，避免因步骤不匹配导致的模型性能下降或训练失败。
- **潜在意义**：增强代码健壮性，为后续功能扩展（如新模型训练或实验）减少隐性问题，有助于维护项目在视频生成领域的竞争力。

### 4. 值得关注的技术点
- **Self-forcing机制**：可能涉及训练中的自监督或自回归策略，修复此类问题通常需要深入理解模型训练动态。
- **步骤同步**：确保训练/验证逻辑对齐，可能涉及数据流、条件判断或回调函数的调整，对分布式训练或复杂实验尤为重要。

### 5. 基于README背景的提交影响分析
- **项目背景**：FastVideo 是一个高效视频生成框架，注重快速推理、易用性和模块化（参考README中的文档与快速启动链接）。
- **影响发展**：
  - **用户体验**：修复训练Bug能提升开发者体验，降低使用门槛，支持更稳定的模型迭代。
  - **项目成熟度**：此类修复体现项目进入精细化维护阶段，有助于吸引社区贡献并推动实际应用。
  - **生态建设**：与README中提到的“Weekly Dev Meeting”和Slack社区相呼应，通过持续优化核心功能，促进社区协作与项目长期发展。

## 详细提交记录

### [7d263c6](https://github.com/hao-ai-lab/FastVideo/commit/7d263c6a36da814579ac2f118d614ef75d3791ce)

- **作者**: Kaiqin Kong
- **时间**: 2026-03-20T07:52:45Z
- **提交信息**: [bugfix] self-forcing train/validation step mismatch (#1173)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33112
- **最后更新**: 2026-03-20T23:17:08Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复了 `audioldm2` 的测试问题，确保测试稳定性。
- **功能新增**：添加了对 `fa4`（可能指 Flash Attention 4）的支持，提升模型推理效率。
- **测试/CI优化**：调整了 CI 配置，尝试解决 `is_flaky` 测试的稳定性问题，减少随机失败。

---

### 2. 关键变更点及其与项目整体方向的关系
- **`audioldm2` 测试修复**：确保音频生成模型的测试可靠性，符合项目对多模态（图像、音频）扩散模型支持的目标。
- **`fa4` 支持**：引入最新的注意力优化技术，与项目追求高性能、低内存占用的扩散模型推理方向一致。
- **CI 稳定性改进**：通过减少测试随机失败，提升开发效率和代码质量，支持项目快速迭代。

---

### 3. 对项目的影响和潜在意义
- **提升稳定性**：修复测试和 CI 问题有助于减少开发中的干扰，加速新功能合并。
- **性能增强**：`fa4` 支持可能显著提升长序列生成任务的推理速度，降低内存使用，改善用户体验。
- **维护成本降低**：更稳定的测试套件可减少维护负担，让团队更专注于核心功能开发。

---

### 4. 值得关注的技术点
- **`fa4` 集成**：可能涉及注意力机制的低级优化，值得关注其对不同硬件（如 GPU）的兼容性和性能提升数据。
- **测试工具调整**：`is_flaky` 修复涉及测试框架的配置调整，可能为未来测试策略提供参考。
- **音频模型测试**：`audioldm2` 测试修复反映了对音频生成模型质量的重视，可能预示该领域的功能扩展。

---

### 5. 基于项目背景的提交影响分析
- **项目背景**：Diffusers 是一个专注于扩散模型（如图像、音频生成）的库，旨在提供易用、高效且可扩展的实现。
- **影响分析**：
  - **功能完善**：`fa4` 支持增强了库的竞争力，符合开源社区对高性能推理的需求。
  - **质量保障**：测试修复和 CI 优化提升了代码可靠性，有助于吸引更多用户和贡献者。
  - **生态扩展**：音频模型测试的维护加强了多模态支持，与项目向音频、视频等领域的扩展战略相符。

这些更新整体上强化了项目的稳定性、性能和多模态能力，支持其作为领先扩散模型库的持续发展。

## 详细提交记录

### [a9855c4](https://github.com/huggingface/diffusers/commit/a9855c4204047c3ff7183fce1502a253efb005c4)

- **作者**: Sayak Paul
- **时间**: 2026-03-20T15:23:21Z
- **提交信息**: [tests] fix audioldm2 tests. (#13293)

fix audioldm2 tests.

### [0b35834](https://github.com/huggingface/diffusers/commit/0b358343512e80b65510c18b8f29ace84fb773d4)

- **作者**: Sayak Paul
- **时间**: 2026-03-20T11:58:09Z
- **提交信息**: [core] fa4 support. (#13280)

* start fa4 support.

* up

* specify minimum version

### [522b523](https://github.com/huggingface/diffusers/commit/522b523e40abc0055b81026378b3b0907126b739)

- **作者**: Sayak Paul
- **时间**: 2026-03-20T10:32:16Z
- **提交信息**: [ci] hoping to fix is_flaky with wanvace. (#13294)

* hoping to fix is_flaky with wanvace.

* revert changes in src/diffusers/utils/testing_utils.py and propagate them to tests/testing_utils.py.

* up

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-20T07:34:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12041
- **最后更新**: 2026-03-20T19:57:32Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

根据提供的README摘要和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：支持WanToDance模型。
- **文档更新**：更新了相关文档。
- **Bug修复**：修复了相关bug。

### 2. 关键变更点及其与项目整体方向的关系
- **支持WanToDance**：新增了对WanToDance模型的支持，这符合项目作为“Diffusion-based Video Synthesis Studio”的定位，旨在集成多种先进的视频生成和编辑模型，扩展其视频合成能力。
- **文档更新与Bug修复**：伴随新功能上线，更新文档以确保用户能正确使用，并修复潜在问题，体现了项目对用户体验和稳定性的重视。

### 3. 对项目的影响和潜在意义
- **功能增强**：丰富了项目的模型库，为用户提供了更多视频生成（尤其是舞蹈视频生成）的选择，提升了工具的实用性和吸引力。
- **生态扩展**：通过集成更多模型，强化了项目作为综合性视频合成平台的地位，可能吸引更广泛的用户和开发者社区。
- **用户体验提升**：及时的文档更新和bug修复有助于降低用户使用门槛，提高满意度。

### 4. 值得关注的技术点
- **WanToDance集成**：可能涉及舞蹈动作生成或视频驱动技术，反映了项目在动态视频合成领域的持续探索。
- **多模型支持架构**：项目需要维护灵活的架构以集成不同模型，这体现了其模块化和可扩展的设计思路。

### 5. 基于项目背景的提交影响分析
- README表明项目目标是成为基于扩散模型的视频合成平台，支持多种任务（如生成、编辑、控制）。昨日更新通过新增WanToDance支持，直接强化了其在**视频生成**方面的能力，特别是可能针对舞蹈或人体动作合成这一垂直场景。这有助于项目在竞争激烈的AI视频生成领域中保持技术前沿性和功能多样性，推动其向更全面的“Studio”目标发展。同时，文档更新和bug修复维护了项目的专业性和可靠性，支持长期生态建设。

## 详细提交记录

### [078fc55](https://github.com/modelscope/DiffSynth-Studio/commit/078fc551d924a78a077f6befd24caf4e419d5317)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-20T09:16:47Z
- **提交信息**: update doc (#1362)

### [52ba5d4](https://github.com/modelscope/DiffSynth-Studio/commit/52ba5d414e4c4603e917265a9133d7f622c9e400)

- **作者**: Zhongjie Duan
- **时间**: 2026-03-20T08:40:35Z
- **提交信息**: Support WanToDance (#1361)

* support wantodance

* update docs

* bugfix

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 24822
- **最后更新**: 2026-03-20T21:55:15Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 14
- **主要提交者**: Muqi Li, DarkSharpness, Zijun Gao

## AI分析总结

根据提供的提交记录和README摘要（SGLang项目是一个专注于高效LLM推理的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：为AMD硬件添加MoE权重填充、支持Qwen3-VL模型的统一注意力机制、在dump comparator中新增多项功能（如维度等价性支持、轴推断与解析）。
- **Bug修复**：修复FP8内核计算、torch.compile与Qwen3 QK-norm的兼容性问题、DeepSeek V32 FP4测试问题等。
- **性能优化/硬件支持**：针对AMD、NPU（华为昇腾）的优化与CI基准更新，添加预-Blackwell架构的编译时向量保护。
- **重构与代码质量**：重构dump comparator工具、整合CI环境检测逻辑、替换未来token ID解析为JIT内核实现。
- **CI/CD与测试**：更新CI运行器标签、合并测试套件、修复基准测试CI、新增单元测试和端到端演示测试。

### 2. 关键变更点及其与项目方向的关系
- **AMD硬件支持深化**（提交1、2）：添加MoE权重填充和启用Qwen3-VL的统一注意力，**强化对AMD GPU的适配能力**，符合项目支持多硬件高效推理的方向。
- **dump comparator功能增强**（提交4-10）：新增维度等价性、轴推断与验证等功能，**提升模型权重与激活值对比调试的精度与自动化水平**，有助于保障多设备/后端推理结果的一致性。
- **JIT内核与性能优化**（提交15、21）：支持自定义All-Reduce操作并用JIT内核替换原有逻辑，**持续优化计算性能与内核灵活性**，是提升推理效率的核心。
- **多硬件与精度支持修复**（提交16、17、23）：修复FP8、FP4精度及编译兼容性问题，**确保低精度推理与新硬件的稳定性**，对支持前沿模型与部署至关重要。

### 3. 对项目的影响和潜在意义
- **提升硬件生态兼容性**：加强对AMD、NPU的支持与优化，降低用户在不同硬件上的部署门槛。
- **增强调试与验证能力**：dump comparator的升级有助于快速定位多设备/后端差异，提升开发与测试效率。
- **巩固性能基础**：JIT内核优化与精度修复直接提升推理速度与稳定性，支撑高负载生产场景。
- **CI/CD流程成熟化**：标签调整、套件合并等改动反映项目CI流程正在细化与优化，有助于提高开发迭代质量。

### 4. 值得关注的技术点
- **统一注意力机制扩展至视觉语言模型**（Qwen3-VL）：可能意味着项目正将优化技术从纯文本模型扩展到多模态领域。
- **依赖轴自动解析与联合推断**：在模型对比工具中引入更智能的维度匹配，减少手动配置成本。
- **预-Blackwell架构的256位向量保护**：针对未来NVIDIA架构的提前适配，体现项目的前瞻性。
- **平台派发的JIT内核替换**：用统一内核加平台派发替代原有逻辑，可能提升代码维护性与跨平台性能。

### 5. 基于项目背景的提交影响分析
SGLang旨在提供**高效、可扩展的LLM推理框架**。昨日更新整体上：
- **强化了“高效”支柱**：通过JIT内核优化、精度修复和多硬件支持，持续提升推理性能与资源利用率。
- **拓展了“可扩展”边界**：增强对AMD、NPU的适配及多模态模型（Qwen3-VL）的支持，拓宽了框架的硬件与模型覆盖范围。
- **夯实了工程基础**：dump comparator的增强与CI/CD的优化提升了框架的**可靠性与可维护性**，这对于需要稳定服务生产环境的推理框架至关重要。

这些提交表明项目正处于**快速迭代期**，重点在扩大硬件支持、深化性能优化、完善工具链，以巩固其作为高效LLM推理框架的竞争力。

## 详细提交记录

### [9419453](https://github.com/sgl-project/sglang/commit/9419453713146b1be0c21e6d328f435f1db95da6)

- **作者**: mqhc2020
- **时间**: 2026-03-20T21:55:09Z
- **提交信息**: [AMD] Add MoE weights and scales padding (#18684)

### [f97c09d](https://github.com/sgl-project/sglang/commit/f97c09dac16192d1578d05ecb340b4dca1923e0a)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-20T19:07:41Z
- **提交信息**: [AMD] Enable aiter unified attention for non-SWA models (Qwen3-VL) (#20897)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [576e397](https://github.com/sgl-project/sglang/commit/576e397b6ef41fd54c577da4d18547a63258a7a8)

- **作者**: Zijun Gao
- **时间**: 2026-03-20T15:38:48Z
- **提交信息**: [Test] Add unit tests for srt/sampling (#20891)

### [146700d](https://github.com/sgl-project/sglang/commit/146700db6891c2960a73f28dd4547c41e3ae814f)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:41:01Z
- **提交信息**: Add e2e demo test in dump comparator (#21031)

### [6703cc4](https://github.com/sgl-project/sglang/commit/6703cc448450e1165a5e62bcef765a98fd9cab6c)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:04:50Z
- **提交信息**: Enhance output formatting in dump comparator (#21029)

### [fdbcb81](https://github.com/sgl-project/sglang/commit/fdbcb8156edb6dabbeb680fa0ebb43ce54ebef97)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:04:20Z
- **提交信息**: Refactor dp_utils to use ParallelAxis enum in dump comparator (#21028)

### [154395a](https://github.com/sgl-project/sglang/commit/154395ab7dbf745b5a5f59930c27c33c5c1ff792)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:03:34Z
- **提交信息**: Support s≡t dimension name equivalence in dump comparator (#21027)

### [cc22601](https://github.com/sgl-project/sglang/commit/cc22601d28c2e8965443c63c29458af0e21f5a37)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:02:40Z
- **提交信息**: Validate replicated axes orthogonality in dump comparator (#21026)

### [2f01950](https://github.com/sgl-project/sglang/commit/2f01950a0e947e6d7e8c53a3ed783ef3f6949141)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T14:01:26Z
- **提交信息**: Support jointly-determined axes inference in dump comparator (#21025)

### [ecd7e40](https://github.com/sgl-project/sglang/commit/ecd7e40d207a6039cb426c82dd48ccaff19aa101)

- **作者**: fzyzcjy
- **时间**: 2026-03-20T13:56:39Z
- **提交信息**: Support dependent axis auto-resolution in dump comparator (#21024)

### [2d7a262](https://github.com/sgl-project/sglang/commit/2d7a262ca3820ce0b781f83b6e343c6cbe8d3af6)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T13:04:15Z
- **提交信息**: ci: rename 1/2-gpu-runner labels to 1/2-gpu-h100 (#21008)

### [104b10f](https://github.com/sgl-project/sglang/commit/104b10f70af602a10fbcdc5aef2f6fba13da0eed)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T12:55:36Z
- **提交信息**: refactor: consolidate is_in_ci (jit_kernel, sgl-kernel benchmarks, tests) (#21009)

### [9fbe680](https://github.com/sgl-project/sglang/commit/9fbe6800aa2196f416765ee3fed63429910b530b)

- **作者**: Артем Савкин
- **时间**: 2026-03-20T12:54:12Z
- **提交信息**: [NPU] [Diffusion] Update CI performance baseline for Wan2.2-T2V-A14B-Diffusers-w8a8 (#20997)

### [f418327](https://github.com/sgl-project/sglang/commit/f41832795ee73bdc6b1b6e00eff3cd676dc1223f)

- **作者**: xingsy97
- **时间**: 2026-03-20T10:25:12Z
- **提交信息**: Add compile-time 256-bit vector guard for pre-Blackwell (#19794)

### [2dd9196](https://github.com/sgl-project/sglang/commit/2dd9196079e3424bb44bea2ce7697eeed5578e6a)

- **作者**: DarkSharpness
- **时间**: 2026-03-20T10:24:07Z
- **提交信息**: [JIT Kernel][Feature] Support JIT custom all reduce (rewrite as v2) (#19880)

Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>

### [2099943](https://github.com/sgl-project/sglang/commit/2099943a4942a736b403b80cc883e9ba262a02bc)

- **作者**: Muqi Li
- **时间**: 2026-03-20T10:09:31Z
- **提交信息**: Fix scale_step_k computation in the fp8_kernel (#20819)

Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>

### [ec01ef9](https://github.com/sgl-project/sglang/commit/ec01ef9092fbb8467504aa36649ce33bef7a6689)

- **作者**: Jia Guo
- **时间**: 2026-03-20T10:05:09Z
- **提交信息**: Fix torch.compile/dynamo crash with Qwen3 QK-norm in piecewise CUDA g… (#19818)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [c1da420](https://github.com/sgl-project/sglang/commit/c1da4207990477e2b75e82710070af1933d998af)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T09:55:16Z
- **提交信息**: ci: run Stage A CUDA tests as stage-a-test-small-1-gpu on 5090 (#20988)

### [fa89d15](https://github.com/sgl-project/sglang/commit/fa89d152c030664855d51bc26dc31b6cab41f801)

- **作者**: Prozac614
- **时间**: 2026-03-20T09:51:55Z
- **提交信息**: [diffusion] CI: fix hunyuan3d JIT cache (#20773)

Co-authored-by: daiweitao <dwti614707404@163.com>

### [a0a4dae](https://github.com/sgl-project/sglang/commit/a0a4dae67f5fdcb209cbbd7b6885a99b06406ac3)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T09:19:28Z
- **提交信息**: Revert "Fix DeepSeek V32 FP4 test" (#21003)

### [112b628](https://github.com/sgl-project/sglang/commit/112b6282272e3730d306989cb9e00b4d70150b58)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T08:47:03Z
- **提交信息**: Replace _resolve_future_token_ids with JIT kernel + platform dispatch (#20976)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [cf60c5b](https://github.com/sgl-project/sglang/commit/cf60c5bd1599998b849f443a6cafcbee8dc4eddd)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-20T08:40:20Z
- **提交信息**: [CI] Fix jit_kernel benchmark ci (#20990)

### [c82d20d](https://github.com/sgl-project/sglang/commit/c82d20d48ecc643ab2a84a0961b8b71901eeffb1)

- **作者**: Baizhou Zhang
- **时间**: 2026-03-20T08:04:32Z
- **提交信息**: Fix DeepSeek V32 FP4 test (#20984)

### [26f709e](https://github.com/sgl-project/sglang/commit/26f709e97df255bd1f7729e2d5a94d7c6b69fed6)

- **作者**: Yilong Zhao
- **时间**: 2026-03-20T07:05:53Z
- **提交信息**: misc: make prefill-delayer compatible with multiple types of mem pool (#20979)

### [193bbf9](https://github.com/sgl-project/sglang/commit/193bbf9b66032f3e3b9e2d17231bd1db139558a3)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T07:05:22Z
- **提交信息**: chore(ci): remove deprecated CI Monitor workflow (#20993)

### [cea7953](https://github.com/sgl-project/sglang/commit/cea79530f818b82d7d90c4832f88751e6deb2087)

- **作者**: Lianmin Zheng
- **时间**: 2026-03-20T07:04:55Z
- **提交信息**: ci: merge CPU default and stage-a-cpu-only suites (#20992)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1102
- **最后更新**: 2026-03-20T17:42:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 73809
- **最后更新**: 2026-03-20T23:44:20Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 29
- **主要提交者**: Jee Jee Li, Andreas Karatzas, Giancarlo Delfin

## AI分析总结

根据提供的提交记录和项目README摘要（vLLM：面向所有人的易用、快速、经济的LLM服务），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及弹性端点、注意力后端、量化、内存管理、配置兼容性等多个核心模块。
- **性能优化**：包括消除冗余计算、避免重复编译、优化内存使用等。
- **功能新增/增强**：新增模型支持、扩展模型运行器V2功能、改进编译和量化支持。
- **CI/测试维护**：针对ROCm平台和测试套件进行多项调整和修复。
- **代码重构**：清理无用代码、重构目录结构以提高可维护性。
- **平台支持扩展**：加强对AMD ROCm、Intel XPU等异构计算平台的支持和优化。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向（易用、快速、经济）的关系 |
| :--- | :--- |
| **弹性端点修复** (`#37131`) | 提升服务**可靠性**和弹性伸缩能力，确保服务稳定（易用、经济）。 |
| **模型支持扩展** (Kimi-K25, Pixtral, LFM2-ColBERT等) | 扩大**模型生态**支持，吸引更多用户和用例（易用）。 |
| **Model Runner V2增强** (流式输入、修复CUDAGraph) | 提升**推理流水线**的功能和效率，优化用户体验和资源利用（快速、经济）。 |
| **性能优化** (消除冗余SparseMatrix、避免内核重编译) | 直接提升**推理速度**和**资源效率**（快速、经济）。 |
| **多平台支持** (ROCm多项修复、XPU内核升级) | 降低硬件依赖，让更多用户能以**低成本硬件**运行（经济、易用）。 |
| **量化相关修复** (Exllama/Conch线性核、Quark OCP) | 优化**低精度推理**，降低部署成本（经济）。 |
| **编译系统改进** (AOT编译、后端初始化) | 提升**部署性能**和**可移植性**（快速、易用）。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量Bug修复直接增强了生产环境的稳定性。
- **性能与效率持续优化**：从内核到调度层的优化，巩固了vLLM在**推理速度**和**吞吐量**方面的领先优势。
- **生态扩展**：支持更多新模型和硬件平台，扩大了项目的**适用场景**和**用户基础**。
- **开发者体验改善**：重构、日志优化和配置修复，使项目更易于维护和贡献。
- **面向生产就绪**：对弹性伸缩、内存管理和流式处理等企业级功能的打磨，表明项目正朝着**成熟、稳定的生产级服务框架**迈进。

### 4. 值得关注的技术点
- **注意力机制优化**：FlashInfer MLA后端检查、区分短扩展与解码，针对不同场景优化注意力计算。
- **混合专家模型支持**：对MoE（如TRTLLM MoE）和稀疏激活模型的持续优化。
- **高级量化支持**：对通道量化、混合精度（FP8）的深入支持，是降低部署门槛的关键。
- **编译部署链路**：AOT编译、VLLM后端初始化等，预示着对**预编译和静态部署**的重视。
- **异构计算**：对AMD ROCm（特别是RDNA4/gfx1x）和Intel XPU的深度优化，体现**硬件无关性**战略。

### 5. 基于项目背景的提交影响分析
vLLM的核心目标是降低LLM服务的技术门槛和成本。昨日的提交全面服务于这一目标：
- **“易用”方面**：通过支持更多模型（如Kimi、Pixtral）、修复Transformers v5配置兼容性、优化日志和错误提示，让用户能更轻松地部署各种模型。
- **“快速”方面**：通过内核级性能优化、内存管理修复（如CUDAGraph内存重复计算）、注意力后端优化，持续压榨硬件性能，保持推理速度优势。
- **“经济”方面**：通过量化修复、多平台支持（ROCm/XPU）、弹性端点修复和性能优化，帮助用户在不同硬件上以更低的成本和更高的资源利用率运行服务。

**总体而言**，这些提交表明vLLM项目正处于一个**巩固核心、扩大边界**的阶段：在确保核心推理引擎高效稳定的同时，积极扩展模型生态、硬件支持和企业级功能，以巩固其作为开源LLM服务首选框架的地位。

## 详细提交记录

### [c57d38d](https://github.com/vllm-project/vllm/commit/c57d38d603213a9acfd5e83f38d45f9d635124fb)

- **作者**: Itay Alroy
- **时间**: 2026-03-20T23:13:02Z
- **提交信息**: elastic_ep: Fix issues with repeated scale up/down cycles (#37131)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Ron Tourgeman <rtourgeman@nvidia.com>

### [e5ed6c6](https://github.com/vllm-project/vllm/commit/e5ed6c6c134ffac42fde5299943dbe3af1821be2)

- **作者**: Kaihang Jiang
- **时间**: 2026-03-20T22:14:55Z
- **提交信息**: [BugFix] Allow qk_nope_head_dim=192 in FlashInfer MLA backend checks (#37475)

Signed-off-by: Kaihang Jiang <kaihangj@nvidia.com>

### [b3d0b37](https://github.com/vllm-project/vllm/commit/b3d0b37908c349ddbb1591bdf2325af15cd21620)

- **作者**: Wentao Ye
- **时间**: 2026-03-20T22:12:51Z
- **提交信息**: [Refactor] Remove unused dead code (#36171)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [85f671b](https://github.com/vllm-project/vllm/commit/85f671b8e1cfa6655605efdf1263cf2f94e9b992)

- **作者**: Santino Ramos
- **时间**: 2026-03-20T20:42:25Z
- **提交信息**: [Model Runner V2] Support Streaming Inputs (#37028)

Signed-off-by: Santino Ramos <elsantinoramos@gmail.com>

### [8bc6b5c](https://github.com/vllm-project/vllm/commit/8bc6b5cdb080e8392075f83cdbc46dde90e49617)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T19:25:08Z
- **提交信息**: [ROCm][CI] Setting some mi325_4 tests back to optional (in parity with upstream) (#37711)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [4f16ebb](https://github.com/vllm-project/vllm/commit/4f16ebbbd35e21b7d98173c406f51853a72a7157)

- **作者**: Vadim Gimpelson
- **时间**: 2026-03-20T19:19:26Z
- **提交信息**: [Bugfix] Disable monolithic TRTLLM MoE for Renormalize routing (#37591) (#37605)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [12fd17e](https://github.com/vllm-project/vllm/commit/12fd17eb5198708523008dda6809143d0f7234ed)

- **作者**: Angela Yi
- **时间**: 2026-03-20T18:40:33Z
- **提交信息**: [compile] Initialize passes at VllmBackend init (#35216)

Signed-off-by: angelayi <yiangela7@gmail.com>

### [37aadf6](https://github.com/vllm-project/vllm/commit/37aadf623786a0fb22a29051b8084168f18db1c9)

- **作者**: Cyrus Leung
- **时间**: 2026-03-20T18:30:22Z
- **提交信息**: [Model] Update Kimi-K25 and Isaac processors to fit HF-style (#37693)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [d7d2b5e](https://github.com/vllm-project/vllm/commit/d7d2b5e405a24f716371cc7f9b488b14300b0991)

- **作者**: Le Yang
- **时间**: 2026-03-20T18:28:34Z
- **提交信息**: [Bugfix] Disable --calculate-kv-scales for hybrid GDN/Mamba+Attention… (#37565)

Signed-off-by: Young-Leo <562593859@qq.com>

### [6ec5e9f](https://github.com/vllm-project/vllm/commit/6ec5e9fd37efc3634f509bc16e34f0d9a3cce528)

- **作者**: SherryC41
- **时间**: 2026-03-20T17:54:08Z
- **提交信息**: refactor: abstract deepgemm support into platform (#37519)

Co-authored-by: sherryC41 <sherry.c.c41@gmail.com>

### [e1d85e5](https://github.com/vllm-project/vllm/commit/e1d85e5c2454bd8d349dbe676679380cbe0e920a)

- **作者**: Lucas Wilkinson
- **时间**: 2026-03-20T17:49:36Z
- **提交信息**: [Attention] Support distinguishing between short extends and decodes (#37303)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>

### [79eb936](https://github.com/vllm-project/vllm/commit/79eb9369c5baa83db934407b0a448a5005c3dd72)

- **作者**: Peter Pan
- **时间**: 2026-03-20T17:36:32Z
- **提交信息**: fix CUDAGraph memory being counted twice (#37426)

Signed-off-by: Peter Pan <Peter.Pan@daocloud.io>
Signed-off-by: Peter Pan <peter.pan@daocloud.io>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [e80cfe5](https://github.com/vllm-project/vllm/commit/e80cfe575d52232b558a053f9c6c12ebd5b6b081)

- **作者**: Woosuk Kwon
- **时间**: 2026-03-20T17:31:45Z
- **提交信息**: [MRV2] Avoid recompilation of _gather_block_tables_kernel (#37645)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [d0532bf](https://github.com/vllm-project/vllm/commit/d0532bf38da5c8f4758e34e53a3708be0955d2db)

- **作者**: Xin Yang
- **时间**: 2026-03-20T17:28:41Z
- **提交信息**: [Perf] Eliminate redundant SparseMatrix creation in gpt_oss_triton_kernels (#37683)

Signed-off-by: Xin Yang <xyangx@amazon.com>

### [fb4e8bf](https://github.com/vllm-project/vllm/commit/fb4e8bf442c53a211d297d31f0381f16c40b1240)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T17:16:59Z
- **提交信息**: [ROCm][CI] Fix accuracy for llama-nemotron-vl pooling tests (#37613)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [6ade4bc](https://github.com/vllm-project/vllm/commit/6ade4bc5a544f6319af968aff4d9b7e71f37434f)

- **作者**: Harry Mellor
- **时间**: 2026-03-20T16:30:12Z
- **提交信息**: Fix various config related issues for Transformers v5 (#37681)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2e089b9](https://github.com/vllm-project/vllm/commit/2e089b96a8a69d921b3d3a127c0c9f84caca6f5e)

- **作者**: Zhengxu Chen
- **时间**: 2026-03-20T16:22:46Z
- **提交信息**: [compile] Add compiled artifact counter for VLLM_USE_MEGA_AOT_ARTIFACT=1. (#37589)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [880be2b](https://github.com/vllm-project/vllm/commit/880be2b1b80fb2d18c32b0ee5a95174cf2e37c7d)

- **作者**: Martin Hickey
- **时间**: 2026-03-20T16:11:34Z
- **提交信息**: [Metrics] Some small refactoring for better maintainability (#33898)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [c0f5fae](https://github.com/vllm-project/vllm/commit/c0f5fae601cf2649dec3cb06ad80008ced7a46ea)

- **作者**: Zhengxu Chen
- **时间**: 2026-03-20T16:06:29Z
- **提交信息**: [compile] Fix aot test failures with torch 2.12. (#37604)

Signed-off-by: zhxchen17 <zhxchen17@fb.com>

### [aa84e43](https://github.com/vllm-project/vllm/commit/aa84e43ccb540dfbbd723f5b315ef7eefd732641)

- **作者**: Rémi Delacourt
- **时间**: 2026-03-20T15:50:15Z
- **提交信息**: [Pixtral] Enable Pixtral language model support Eagle3 (#37182)

Signed-off-by: remi <remi@mistral.ai>

### [5e806bc](https://github.com/vllm-project/vllm/commit/5e806bcf541c0a90619bbf4fab3ab721c98b12a1)

- **作者**: Matthias Gehre
- **时间**: 2026-03-20T15:32:21Z
- **提交信息**: [Bugfix] Fix ConchLinearKernel channelwise quantization (group_size=-1) (#37329)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [56a62c3](https://github.com/vllm-project/vllm/commit/56a62c310cc4840671949488c60c40df5e0e2f1f)

- **作者**: Matthias Gehre
- **时间**: 2026-03-20T15:31:57Z
- **提交信息**: [Bugfix] Reject channelwise quantization (group_size <= 0) in ExllamaLinearKernel (#37331)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [1779c09](https://github.com/vllm-project/vllm/commit/1779c09898e091167b5d29cb8931ce1f5dea9a47)

- **作者**: L.B.R.
- **时间**: 2026-03-20T15:11:23Z
- **提交信息**: [ROCm] Enable wvSplitK skinny GEMM kernel for RDNA4/gfx1x decode (#34709)

Signed-off-by: L.B.R. <lbr@mmonad.com>
Co-authored-by: L.B.R. <lbr@mmonad.com>

### [44eea10](https://github.com/vllm-project/vllm/commit/44eea10f68461852ff4467cd5b7924a46777c8c9)

- **作者**: xuebwang-amd
- **时间**: 2026-03-20T15:10:03Z
- **提交信息**: [ROCm][Quantization] make quark ocp mx dtype parser robust for weight-only quantization (#36232)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>

### [8b6c6b9](https://github.com/vllm-project/vllm/commit/8b6c6b950579778e222b24f501cd81a0c1d719d8)

- **作者**: Ilya Boytsov
- **时间**: 2026-03-20T14:57:57Z
- **提交信息**: [Model] Add LFM2-ColBERT-350M support  (#37528)

Signed-off-by: Ilya Boytsov <ilyaboytsov1805@gmail.com>

### [9f6d9dd](https://github.com/vllm-project/vllm/commit/9f6d9dd371c63154dddd2a8b85d7f337f3e10911)

- **作者**: Harry Mellor
- **时间**: 2026-03-20T14:49:40Z
- **提交信息**: Fix attribute error in `isaac_patch_hf_runner` (#37685)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [dd20ee4](https://github.com/vllm-project/vllm/commit/dd20ee4e3e873364bd79983dcbb30d2189c96507)

- **作者**: Jee Jee Li
- **时间**: 2026-03-20T11:17:26Z
- **提交信息**: [UX] Enable torch_profiler_with_stack (#37571)

Signed-off-by: Jee Jee Li <pandaleefree@gmail.com>

### [0523449](https://github.com/vllm-project/vllm/commit/0523449c9c78b958b548eefc3fdbdd026ae37aba)

- **作者**: Chauncey
- **时间**: 2026-03-20T10:40:36Z
- **提交信息**: [Misc] Use logger.info_once for auto tool choice log message (#37661)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [b4c1aef](https://github.com/vllm-project/vllm/commit/b4c1aef21c1a4cb252e7a440b3f9b0baebefbbef)

- **作者**: Flora Feng
- **时间**: 2026-03-20T09:50:34Z
- **提交信息**: [Refactor] Relocate tests from tests/v1/entrypoints/ to tests/entrypoints/ (#37500)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [6050b93](https://github.com/vllm-project/vllm/commit/6050b93bedb66a086281c160814b3cfca8da3111)

- **作者**: Flora Feng
- **时间**: 2026-03-20T09:10:47Z
- **提交信息**: [Refactor] Move serve entrypoint tests under tests/entrypoints/serve/ (#37595)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [5a4a179](https://github.com/vllm-project/vllm/commit/5a4a1795916a7cf3120ab47cc96f663904bca3f0)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T09:07:26Z
- **提交信息**: [ROCm][CI] Fix granite_speech test for gfx90a by selecting compatible attention backend (#37611)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [37cd9fc](https://github.com/vllm-project/vllm/commit/37cd9fc107211931d1d69d3d79c93a8c408778c0)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T09:07:07Z
- **提交信息**: [ROCm][CI] Remove deepep DBO tests on gfx90a (#37614)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [9cfd4eb](https://github.com/vllm-project/vllm/commit/9cfd4ebb5eaac58724652517e316302e8fd597e6)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T09:06:53Z
- **提交信息**: [ROCm][CI] Update GSM8K eval config to use fp8-and-mixed models list (#37619)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [ed359c4](https://github.com/vllm-project/vllm/commit/ed359c497a728f08b5b41456c07a688ccd510fbc)

- **作者**: wang.yuqi
- **时间**: 2026-03-20T08:07:56Z
- **提交信息**: [Model] Deprecate the score task (this will not affect users).  (#37537)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [dcee9be](https://github.com/vllm-project/vllm/commit/dcee9be95a0f7fce32ab82060733ab31f90b9154)

- **作者**: Giancarlo Delfin
- **时间**: 2026-03-20T07:43:47Z
- **提交信息**: [Model Runner V2] Fix draft logits not populated during cudagraph replay (#37639)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [bd8c4c0](https://github.com/vllm-project/vllm/commit/bd8c4c0752b7542c687ed06c2284cfb594a61e48)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-20T07:20:33Z
- **提交信息**: [CI] Removing deprecated rlhf examples reference (#37585)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [0140eaf](https://github.com/vllm-project/vllm/commit/0140eafb1546c24d8486761abdbaa538d948bf42)

- **作者**: Wei Zhao
- **时间**: 2026-03-20T07:09:21Z
- **提交信息**: [Bug] Fix FlashInfer allreduce fusion workspace uninitialized error (#37461)

Signed-off-by: root <root@prenyx0169.a51.clusters.nvidia.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Signed-off-by: <>
Co-authored-by: root <root@prenyx0169.a51.clusters.nvidia.com>
Co-authored-by: root <root@prenyx0042.a51.clusters.nvidia.com>

### [bdf6a0a](https://github.com/vllm-project/vllm/commit/bdf6a0a57bfed4f4fee29a10ed066d8c0d427883)

- **作者**: Kunshang Ji
- **时间**: 2026-03-20T07:04:38Z
- **提交信息**: [XPU] bump vllm-xpu-kernels to v0.1.4 (#37641)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-21
**监控日期**: 2026-03-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3351
- **最后更新**: 2026-03-20T23:41:53Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: Chen-Yo Sun, dengyunyang, Lancer

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：3项（#1634, #1851, #2031）
- **性能优化**：2项（#2012, #1368）
- **功能增强/测试改进**：2项（#1657, #2014）
- **代码清理/配置优化**：1项（#2056）

### 2. 关键变更点及其与项目方向的关系
- **多模态模型支持优化**：
  - 修复Z-Image CFG阈值逻辑（#1634）→ 提升图像生成质量稳定性
  - 优化Qwen3-omni代码预测器性能（#2012）→ 增强代码生成场景的推理效率
- **系统稳定性与性能**：
  - 重构pipeline阶段/步骤（#1368）→ 改善服务端处理流程
  - 移除冗余YAML配置（#2056）→ 简化Voxtral TTS部署配置
- **测试与验证能力增强**：
  - 扩散模型随机数据集支持（#1657）→ 提升基准测试的覆盖面和可靠性
  - 实现基准测试CLI的模拟HTTP请求处理（#2014）→ 完善测试基础设施

### 3. 对项目的影响和潜在意义
- **用户体验**：修复配置重复项（#1851）和错误阈值（#1634）直接提升部署和推理的稳定性
- **开发者体验**：测试框架的完善（#2014, #2031）降低了贡献门槛，保障代码质量
- **性能基准**：随机数据集支持（#1657）使性能评估更贴近真实场景，增强结果可信度

### 4. 值得关注的技术点
- **Qwen3-omni优化**（#2012）：通过**重预填充（re-prefill）+ SDPA（Scaled Dot-Product Attention）** 减少CPU往返，显著优化解码路径性能，对长序列或高并发场景尤为重要
- **Pipeline重构**（#1368）：可能涉及**异步处理或阶段并行化**，为后续支持更高吞吐量奠定基础
- **模拟HTTP请求测试**（#2014）：采用**Mock技术**隔离外部依赖，提升测试速度和可靠性

### 5. 基于项目背景的提交影响分析
vllm-omni旨在提供**“易用、快速、经济的全模态模型服务”**。昨日的更新紧密围绕这一目标：
- **“快速”与“经济”**：性能优化（#2012, #1368）和Bug修复（#1634, #1851）直接提升推理效率与资源利用率，降低服务成本
- **“易用”**：配置清理（#2056）和测试完善（#2014, #2031）简化部署流程，提升系统可靠性
- **“全模态”**：涉及**图像生成（Z-Image）、语音合成（Voxtral TTS）、代码生成（Qwen3-omni）和扩散模型**的改进，体现了对多模态场景的持续深耕

**整体来看**，本次更新以**性能优化和稳定性提升**为核心，通过修复关键Bug、优化核心路径、完善测试体系，进一步巩固了vllm-omni作为高效、可靠的全模态推理服务框架的基础。这符合项目在快速发展期兼顾功能扩展与系统健壮性的典型演进路径。

## 详细提交记录

### [95018c5](https://github.com/vllm-project/vllm-omni/commit/95018c536a812cee6a8f9d36f2c39912b5d02a72)

- **作者**: Chen-Yo Sun
- **时间**: 2026-03-20T21:02:35Z
- **提交信息**: [Voxtral TTS] Remove redundant yaml (#2056)

Signed-off-by: Chen-Yo Sun <chenyo.sun@mistral.ai>

### [b33d763](https://github.com/vllm-project/vllm-omni/commit/b33d7637deb8c185ab319fc24067ed1b0d3ddbaf)

- **作者**: Lancer
- **时间**: 2026-03-20T12:13:10Z
- **提交信息**: [Bugfix] Z-Image CFG threshold should be > 0 instead of > 1 (#1634)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [ff25479](https://github.com/vllm-project/vllm-omni/commit/ff254795facbca763be6ff2b1c28c3b9b51e6105)

- **作者**: dengyunyang
- **时间**: 2026-03-20T12:12:49Z
- **提交信息**: [Benchmark] [Diffusion] [Enhancement] Random dataset (#1657)

Signed-off-by: dengyunyang <584797741@qq.com>
Signed-off-by: Samit <285365963@qq.com>
Signed-off-by: bjf-frz <frz123db@gmail.com>
Co-authored-by: Samit <285365963@qq.com>
Co-authored-by: bjf-frz <frz123db@gmail.com>

### [6901ba4](https://github.com/vllm-project/vllm-omni/commit/6901ba426e28b1bdd90bde626ae064f7a55b2b28)

- **作者**: Junhong Liu
- **时间**: 2026-03-20T11:33:52Z
- **提交信息**: [Fixbug][Perf] Qwen3-omni: code predictor with re-prefill + SDPA and eliminate decode hot-path CPU round-trips (#2012)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>

### [da7a8f8](https://github.com/vllm-project/vllm-omni/commit/da7a8f801480d8fc8c00c1f67bcd481d5d8aa6e8)

- **作者**: Wu JIAZHEN
- **时间**: 2026-03-20T11:21:50Z
- **提交信息**: reafator pipeline stage/step pipeline (#1368)

Signed-off-by: asukaqaq-s <1311722138@qq.com>

### [199f783](https://github.com/vllm-project/vllm-omni/commit/199f7832e7d4293a07644f83a1fac9fdaf45caee)

- **作者**: Alicia
- **时间**: 2026-03-20T08:41:45Z
- **提交信息**: [CI] Fix test. (#2031)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [fafa248](https://github.com/vllm-project/vllm-omni/commit/fafa248665758b86449edc90c1cd5b0bbdd7224b)

- **作者**: wangyu
- **时间**: 2026-03-20T08:13:39Z
- **提交信息**: [Test] Implement mock HTTP request handling in benchmark CLI tests (#2014)

Signed-off-by: yenuo26 <410167048@qq.com>
Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [05d8de8](https://github.com/vllm-project/vllm-omni/commit/05d8de813ec6ac9a93c51b73de2fb56beddd71eb)

- **作者**: Zhou Taichang
- **时间**: 2026-03-20T08:13:24Z
- **提交信息**: [Bugfix] Remove duplicated config keyword max batch size (#1851)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: Zhou Taichang <tzhouam@connect.ust.hk>

---
