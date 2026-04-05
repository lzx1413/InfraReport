# GitHub Stars 合并报告 - 2026-04-05

**合并日期**: 2026-04-06
**监控日期**: 2026-04-05
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


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1795
- **最后更新**: 2026-04-05T08:56:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2137
- **最后更新**: 2026-04-05T04:57:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1998
- **最后更新**: 2026-04-05T07:54:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5306
- **最后更新**: 2026-04-05T21:51:29Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sam (Kesen Li), ChristinaZ

## AI分析总结

根据对FlashInfer仓库README（高性能GPU推理内核）和昨日提交记录的分析，总结如下：

### 1. 主要更新类型
- **Bug修复**：修复了SM120系列GPU（如RTX PRO 6000、RTX 5090）上MXFP4 MoE CUTLASS内核因权重缩放向量大小检查失败而无法使用的问题。
- **重构**：对`trtllm-gen`的路由部分进行了大规模重构，引入了模块化、可扩展的策略设计。

### 2. 关键变更点及其与项目整体方向的关系
- **修复FP4量化缩放布局对齐问题**：针对`block_scale_interleave`填充导致的`weight_scale_vec_size`计算偏差，将硬性相等检查改为“对齐到最近有效值（16或32）+往返验证”。这**直接服务于项目“支持多种量化格式和硬件”的目标**，确保了新型GPU的兼容性。
- **重构路由系统**：
    - 引入**策略化设计**：将专家选择逻辑抽象为编译时模板参数（`ExpertSelectPolicy`），实现零运行时开销和高可扩展性。
    - 建立**分层调度系统**（`TierList`）：根据专家数量（`MaxNumExperts`）和TopK值（`MaxNumTopExperts`）预编译优化内核，避免组合爆炸。
    - 统一**执行流水线**：无论路由方法如何，后续的TopK、直方图、偏移计算等步骤都通过`runPostTopKPipeline`统一处理，减少代码重复。
    - 这**强化了项目“高性能、可扩展内核”的核心**，使路由系统能更高效、灵活地适配不同模型（如支持Nemotron Super V3的512专家、TopK 22）。

### 3. 对项目的影响和潜在意义
- **扩大硬件支持**：修复使FlashInfer能正式支持新一代SM120架构GPU，**拓宽了用户硬件基础**。
- **提升系统健壮性与可维护性**：路由重构将分散的逻辑模块化、标准化，**降低了未来添加新路由算法（如Lookup表）的复杂度**，并减少了错误风险。
- **性能优化潜力**：新的路由调度机制（如协作启动、集群感知分块）为**进一步榨取现代GPU性能**奠定了基础。
- **增强验证**：更严格的输入验证和更清晰的错误信息，**提升了开发者体验和调试效率**。

### 4. 值得关注的技术点
- **“对齐填充”引发的边界问题**：修复案例展示了底层内核优化中，**张量维度对齐、内存布局与算法假设不一致**导致的隐蔽Bug，这对高性能计算开发具有普遍警示意义。
- **编译时策略与零成本抽象**：利用C++模板在编译时注入策略，**避免运行时分支和多余字段存储**，是高性能库设计的典范。
- **分层编译（TierList）**：通过预定义`(E, K)`组合来控制内核编译数量，在**支持灵活性和编译时间/二进制大小之间取得平衡**。
- **统一后处理流水线**：将不同路由方法的公共下游步骤抽象为统一管道，是**优秀的软件工程实践**，避免了代码重复。

### 5. 基于项目背景的提交影响分析
FlashInfer的目标是提供**高性能、通用且易用的GPU推理内核**。昨日的提交紧密围绕这一目标：
- **修复Bug**：直接维护了库的**通用性和可靠性**，确保其在最新硬件上“开箱即用”，这是获得用户信任的基础。
- **路由重构**：是一次深刻的**架构升级**。它没有增加新功能，而是通过重构使系统**更高效、更灵活、更易于扩展**。这允许研究者和工程师未来能更轻松地集成新的路由算法（如为MoE模型设计的创新方法），而无需重写底层管道，**加速了创新落地**。同时，性能优化确保了内核能持续发挥GPU的极限算力。

**总结**：昨日更新是一次“夯实基础、面向未来”的迭代。Bug修复维护了现有能力的边界，而路由重构则为项目应对未来更复杂、更多样的稀疏化专家混合模型（MoE）推理需求，构建了更强大的核心基础设施。

## 详细提交记录

### [c4cb6e0](https://github.com/flashinfer-ai/flashinfer/commit/c4cb6e0117a4201f130dd6c48bb57289aaae0046)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-04-05T12:14:59Z
- **提交信息**: fix: snap weight_scale_vec_size to handle block_scale_interleave padding for SM120 (#2898)

Fixes #2847

SM120 GPUs (RTX PRO 6000, RTX 5090) cannot use MXFP4 MoE CUTLASS kernels
because the `weight_scale_vec_size` check in
  `trtllm_fp4_block_scale_moe` rejects valid inputs.

**Root cause**: `block_scale_interleave` pads scale columns via
`round_up(cols, 4)`, inflating
`gemm1_weights_scale.numel()`. When `hidden_size / sf_block_size` is not
a multiple of 4 (e.g. gpt-oss-120b:
hidden_size=2880, sf_block_size=32 → 90 scale cols padded to 92), the
reverse-computed `weight_scale_vec_size` becomes 31
   instead of 32, failing the strict equality check.

**Fix**: Replace the hard-coded equality check with
snap-to-nearest-valid (16 or 32) plus a round-trip validation
ensuring the actual scale tensor numel is at least as large as the
unpadded expectation.

  ## Changes

- `csrc/trtllm_fused_moe_kernel_launcher.cu`: Replace
`weight_scale_vec_size` check logic in `trtllm_fp4_block_scale_moe`
- `tests/moe/test_trtllm_cutlass_fused_moe.py`: Add
`test_moe_nvfp4_unaligned_hidden_size` and
`test_moe_mxfp8_mxfp4_unaligned_hidden_size` with hidden_size=2880 to
cover the padding scenario

  ## Test plan

- [x] Existing MoE tests pass without regression: `pytest
tests/moe/test_trtllm_cutlass_fused_moe.py -x`
- [x] New unaligned hidden_size tests pass (requires SM100/SM110/SM120
GPU)
  - [x] pre-commit lint passes


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* More tolerant fused MoE weight/scale sizing with vec-size snapped to
16/32 and clearer validation errors for unaligned hidden sizes.
* FP4 quantization scale layout now accounts for padded/interleaved
columns (aligned to blocks of 4) so scale buffers are interpreted
correctly.

* **Tests**
* Added CUDA regression test for fused MoE with an unaligned hidden size
under NVFP4 quantization.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [c26953f](https://github.com/flashinfer-ai/flashinfer/commit/c26953fb7ca68f3f3a2bfe2b3b22af268bcb0901)

- **作者**: ChristinaZ
- **时间**: 2026-04-05T08:24:48Z
- **提交信息**: Refactor the routing part (#2803)

<!-- .github/pull_request_template.md -->

## 📌 Description
Refactor the routing part of the trtllm-gen.

### Execution Flow

Each routing method follows the same high-level pattern:

1. **TopK selection** — Compute top-K experts per token from routing
scores.
2. **Histogram** — Count how many tokens are assigned to each expert.
3. **Offsets + Permutation** — Prefix-scan expert counts to get offsets;
build permutation indices mapping expanded token slots → padded
expert-sorted positions.
4. **GEMM config** — Write `ctaIdxXyToBatchIdx`, `ctaIdxXyToMnLimit`,
`numNonExitingCtas` so the downstream batched GEMM knows how to
partition work.

Depending on token count, different code paths are selected:

| Token Count | Code Path |

|--------------------|----------------------------------------------------------------|
| ≤ 4 | Single-block kernel (fuses all steps incl. topK) |
| ≤ cluster capacity | Single-cluster kernel (uses distributed smem,
incl. topK) |
| ≤ coop capacity | Scores→topK kernel + cooperative kernel (fuses
histogram+offsets) |
| Large | Scores→topK kernel + histogram kernel + offsets kernel |

When topK is pre-computed (mPtrTopKIds or mPtrTopKPacked), the first two
paths skip topK,
and the coop/large paths skip the scores→topK kernel.

`runPostTopKPipeline<DataType>()` handles the permutation pipeline when
topK is already computed
(e.g., by DeepSeek's grouped main kernel). It converts any routing
method's `Data` to
`routingCustom::Data` and dispatches through the appropriate token-count
path (single-block,
single-cluster, coop, or multi-kernel). This avoids duplicating
permutation code across methods.

### Routing Methods and TierList Configuration

#### RoutingMethodType → Policy Mapping

Each `RoutingMethodType` (defined in `runner.h`) maps to a specific
kernel path and policy
combination. The `routingCustom` method uses a **policy-based design**
where expert selection logic is injected as a compile-time
`ExpertSelectPolicy` template parameter, providing zero runtime overhead
and high extensibility.

The default `TopKExpertSelect<PreprocessPolicy, PostprocessPolicy>`
wraps the traditional preprocess → topK → postprocess pattern, while
users can write completely custom policies that bypass this pattern
(e.g., lookup-table-based expert selection).

Each policy owns its runtime data through a nested `Params<OutputT>`
struct. When a policy doesn't need extra data, its `Params` is empty and
costs **zero registers**. This avoids paying for unused fields (e.g., a
routing bias pointer) in policy combinations that don't need them.

#### TierList and PolicyTraits

Each routing kernel is templated on `MaxNumExperts` and
`MaxNumTopExperts`. These determine
shared memory sizes, loop bounds, and the `__launch_bounds__` thread
count. To avoid compiling
every combination, each policy declares which `(MaxNumExperts, MaxTopK)`
pairs it supports via
a `PolicyTraits` specialization:

```cpp
template <>
struct PolicyTraits<SigmoidBiasPreprocess, ScaledSumNormalizePostprocess>
{
    using Pairs = TierList<
        Tier<128, 8>,   // ≤128 experts, topK ≤ 8
        Tier<256, 8>,   // ≤256 experts, topK ≤ 8
        Tier<384, 8>,   // ≤384 experts, topK ≤ 8
        Tier<512, 8>,   // ≤512 experts, topK ≤ 8
        Tier<512, 22>   // ≤512 experts, topK ≤ 22  (Nemotron Super V3)
    >;
};
```

**Dispatch:** `dispatchTierPairs` iterates the `TierList` from first to
last, picking the
**first** `Tier<E, K>` where `numExperts ≤ E` AND `topK ≤ K`. This means
tighter tiers
must come first (sorted by E ascending, then K ascending within equal
E).

**Adding support for a new model:** If a new model has a `(numExperts,
topK)` combination
not covered by any existing tier, add a `Tier<E, K>` to the appropriate
`PolicyTraits`
specialization. No other changes are needed — the dispatch macros are
generic.

#### Available Policies

| Policy | Type | `Params` Fields | Description |
|--------|------|-----------------|-------------|
| `NoOpPreprocess` | Pre | *(empty)* | Pass-through; `BaseType = InputT`
|
| `SoftmaxPreprocess` | Pre | *(empty)* | Softmax over all expert
scores; `BaseType = float` |
| `SigmoidPreprocess` | Pre | *(empty)* | `sigmoid(score)` (no bias);
`BaseType = float` |
| `SigmoidBiasPreprocess` | Pre | `ptrRoutingBias`, `dtypeBias` |
`sigmoid(score) + bias[expertIdx]`; `BaseType = float` |
| `NoOpPostprocess` | Post | *(empty)* | No transformation |
| `SoftmaxPostprocess` | Post | *(empty)* | Softmax over selected top-K
scores |
| `SumNormalizePostprocess` | Post | `normTopkProb` | Divide top-K
scores by their sum |
| `ScaledSumNormalizePostprocess` | Post | `ptrRoutingBias`,
`dtypeBias`, `routeScale`, `sumEpsilon` | Recover sigmoid, normalize by
sum, apply scale |



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
* Runtime flag to toggle Top-K probability renormalization (enabled by
default).
  * Added two routing modes: SigmoidRenorm and MiniMax2.

* **Performance Improvements**
* Consolidated/custom routing path with improved cooperative launches
for modern GPUs.
  * Cluster-aware tiling and broader dtype-aware routing dispatch.

* **Bug Fixes**
* Stricter validation of routing inputs, dtypes and cluster/power-of-two
constraints; safer CUDA queries.

* **Tests**
  * Expanded routing tests with reference implementations for new modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Christina Zhang <83400082+ChristinaZ@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3344
- **最后更新**: 2026-04-05T14:03:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33270
- **最后更新**: 2026-04-05T23:25:21Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 389
- **最后更新**: 2026-04-04T18:57:49Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12173
- **最后更新**: 2026-04-05T21:23:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25450
- **最后更新**: 2026-04-05T23:15:53Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 10
- **主要提交者**: Zhangheng, R0CKSTAR, Yuhao Yang

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效执行大型语言模型的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位，涉及推理、注意力机制、缓存、测试等多个核心模块。
- **测试与CI/CD优化**：包括测试流程调整、失败重跑策略和问题调试。
- **功能新增/支持扩展**：新增对特定模型（如Voxtral）和硬件平台（如float64）的支持。
- **代码重构与统一**：统一配置来源，隔离不同版本的代码路径。
- **文档更新**：更新了特定模型的部署指南。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复TRT-LLM MHA CUDA非法地址错误** (`5dd2c24`) | 核心方向：**提升推理性能与稳定性**。修复了在使用EAGLE v2和DP注意力时的底层CUDA错误，确保在TensorRT-LLM后端上的高效稳定运行。 |
| **修复Hi-MambaRadixTree备份不变性违规** (`51b276d`) | 核心方向：**优化内存与缓存管理**。修复了RadixTree（用于前缀缓存）的关键Bug，维护了缓存系统的正确性，对生成效率至关重要。 |
| **统一`think_end_id`至`model_config`** (`df9c831`) | 核心方向：**提升框架一致性与可维护性**。将推理中的关键配置集中管理，避免分散和潜在的不一致，是重要的代码健康度改进。 |
| **支持Voxtral（语音转文本）模型** (`71544f0`) | 核心方向：**扩展模型生态支持**。将支持范围从纯文本LLM扩展到多模态（音频），增强了框架的适用场景。 |
| **为DeepSeek V3.2启用IndexCache** (`5a35316`) | 核心方向：**优化长上下文与特定模型性能**。IndexCache能显著提升长序列处理的效率，此举紧跟主流模型发展，优化用户体验。 |
| **隔离Speculative Decoding V1路径** (`cd2d45e`) | 核心方向：**推进推理优化技术**。为推测解码（一种加速技术）的新版本（V2）铺路，确保代码清晰且便于未来迭代。 |

### 3. 对项目的影响和潜在意义
- **稳定性提升**：大量针对核心组件（RadixTree、注意力、GEMM内核）的修复直接提升了系统在生产环境中的鲁棒性。
- **性能与效率优化**：修复CUDA错误、启用IndexCache、优化推测解码路径，这些都有助于巩固SGLang在**高效推理**方面的竞争力。
- **可维护性增强**：配置统一和代码路径隔离使项目更易于管理和未来开发。
- **生态扩展**：支持Voxtral和更新GLM-5指南，表明项目正积极拥抱更广泛的模型类型，吸引更多用户群体。
- **开发体验改进**：CI/CD流程的调整（如失败重跑、问题调试）有助于提升开发团队的效率。

### 4. 值得关注的技术点
- **推测解码（Speculative Decoding）的演进**：提交中多次提及SpecV2，并隔离V1路径，表明该项目正在积极迭代这一前沿推理加速技术。
- **多模态模型支持**：集成**Voxtral（语音转文本）** 是一个重要信号，显示SGLang不局限于文本LLM，开始向多模态推理栈延伸。
- **硬件与底层优化**：针对特定GPU架构（`sm103`）的GEMM内核修复、CUDA地址错误修复，体现了对**深度硬件适配**的重视。
- **复杂的缓存系统**：对`Hi-MambaRadixTree`和`IndexCache`的修改，凸显了项目在**内存管理与缓存优化**方面的技术深度，这是实现低延迟、高吞吐的关键。

### 5. 基于项目背景的提交影响分析
SGLang的目标是成为“LLM推理的操作系统”，强调**性能、灵活性和广泛的模型支持**。昨日的提交完美契合了这一战略：
1.  **巩固性能基石**：通过修复底层CUDA/内核Bug和优化缓存，确保了推理引擎的**高效与稳定**，这是框架生存的根本。
2.  **拓展能力边界**：支持Voxtral模型，是从“文本推理框架”向“**通用AI推理服务框架**”迈出的试探性一步，增加了应用潜力。
3.  **优化开发与部署体验**：通过统一配置、更新文档、优化测试流程，降低了框架的**使用和维护门槛**，有利于社区发展和企业 adoption。
4.  **紧跟技术前沿**：持续改进推测解码、适配DeepSeek V3.2等最新模型，表明项目保持**技术敏锐度**，确保其解决方案不落伍。

**总结**：昨日的更新是一次以**修复和夯实基础**为主，同时**稳步扩展功能边界**的迭代。它强化了SGLang作为高性能LLM推理框架的核心竞争力，并为支持更复杂的模型和场景做好了技术铺垫。

## 详细提交记录

### [30ba1f7](https://github.com/sgl-project/sglang/commit/30ba1f78b0982f1fcd1d87d3b58713c11a422ee5)

- **作者**: Zhiqiang Xie
- **时间**: 2026-04-05T23:15:47Z
- **提交信息**: Hisparse Minor Fix (#22131)

Co-authored-by: huangtingwei9988 <141888744+huangtingwei9988@users.noreply.github.com>
Co-authored-by: hzh0425 <58988019+hzh0425@users.noreply.github.com>

### [20ee59b](https://github.com/sgl-project/sglang/commit/20ee59bcfc2956cb2aef2c1a4ae1e8bbda4ba52d)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-05T23:01:02Z
- **提交信息**: [Misc] Remove unused cu13 docker release workflow (#22167)

### [596c34e](https://github.com/sgl-project/sglang/commit/596c34ee04b4bf983a4f0a46f79fb6f85cf82acc)

- **作者**: Kangyan-Zhou
- **时间**: 2026-04-05T17:39:19Z
- **提交信息**: Update ci_auto_bisect.py to have streak 1 so that all failures will b… (#22161)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [75ab75d](https://github.com/sgl-project/sglang/commit/75ab75d0276eea94287cf8707246f8d41674a6d4)

- **作者**: Shangming Cai
- **时间**: 2026-04-05T16:54:35Z
- **提交信息**: Fix create_grammar_backend test calls with think_end_id (#22158)

### [5dd2c24](https://github.com/sgl-project/sglang/commit/5dd2c243eb52dfd04f27b998e2595fe0c66437b1)

- **作者**: Kangyan-Zhou
- **时间**: 2026-04-05T16:41:14Z
- **提交信息**: fix: TRT-LLM MHA CUDA illegal address with EAGLE v2 + DP attention (#21649)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [c5fa364](https://github.com/sgl-project/sglang/commit/c5fa364b80b365fc916279d13c6d9384a65b9b3c)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-05T16:33:14Z
- **提交信息**: [Hotfix] Fix router gemm on sm103 (#22134)

### [f6c9072](https://github.com/sgl-project/sglang/commit/f6c9072e425a7f56a5dc0bc2cad2d03c4a0542a3)

- **作者**: Zhangheng
- **时间**: 2026-04-05T15:26:40Z
- **提交信息**: [SpecV2]: Reopen kl accuracy test for qwen3 + SpecV2 (#22104)

### [51b276d](https://github.com/sgl-project/sglang/commit/51b276de7493cc0503a9325176c7f670e1431e3d)

- **作者**: Zhangheng
- **时间**: 2026-04-05T15:19:50Z
- **提交信息**: [BugFix][RadixTree]: Fix backup invariant violation in Hi-MambaRadixTree (#22062)


Co-authored-by: 晟海 <huangtingwei.htw@antgroup.com>
Co-authored-by: linjianyu77@foxmail.com

### [dccb118](https://github.com/sgl-project/sglang/commit/dccb11881fae72886353bb7f278c020a0e3d08f0)

- **作者**: Shangming Cai
- **时间**: 2026-04-05T15:13:06Z
- **提交信息**: [PD] Fix staging warmup for GQA prefill decode different tp (#22153)

### [3a4f4cb](https://github.com/sgl-project/sglang/commit/3a4f4cbc525b9106bb57a69b96420c545a90f7ae)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T14:46:36Z
- **提交信息**: DEBUG: reproduce flaky test_load_weights_from_remote_instance (#22150)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [df9c831](https://github.com/sgl-project/sglang/commit/df9c831ab80c78495142b4dbcb1dfa537c9e1c73)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T10:35:38Z
- **提交信息**: Unify think_end_id to model_config as single source of truth (#22148)

### [aeff9fb](https://github.com/sgl-project/sglang/commit/aeff9fb7c1cf5204e47d48707ca4a024d8cf015b)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T10:23:52Z
- **提交信息**: Add dump_metric to MMMU, lm-eval, and NeMo Skills eval paths (#22147)

### [cd2d45e](https://github.com/sgl-project/sglang/commit/cd2d45e22085045a5e9cd14666be7b0e96af601d)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T10:16:56Z
- **提交信息**: Isolate spec V1 path in decode post-processing (#22146)

### [106baed](https://github.com/sgl-project/sglang/commit/106baedbfb9fb18e96e95963b12473a6d21c0ece)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-05T10:13:07Z
- **提交信息**: [Doc] Update GLM-5 instructions in sglang documentation (#21716)

### [10b18b8](https://github.com/sgl-project/sglang/commit/10b18b8b2915c96f79aac6c60802b20f4417dcfa)

- **作者**: R0CKSTAR
- **时间**: 2026-04-05T10:12:28Z
- **提交信息**: [diffusion] Add is_float64_supported to Platform (#22112)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [5a35316](https://github.com/sgl-project/sglang/commit/5a3531641735b456996ad3b1ef2f9988726f71a7)

- **作者**: iLeGend
- **时间**: 2026-04-05T09:45:58Z
- **提交信息**: Enable IndexCache for DeepSeek V3.2 (#21405)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [0882034](https://github.com/sgl-project/sglang/commit/088203454b14c13ca5c280c022961085593d57f8)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-05T09:26:42Z
- **提交信息**: [Fix] Fix nightly tests (#22140)

### [bd6a585](https://github.com/sgl-project/sglang/commit/bd6a585605c5d02805ce07eeaf505dabd891f018)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T08:09:11Z
- **提交信息**: Consolidate reasoning tests into test/registered/reasoning/ (#22139)

### [2b119ba](https://github.com/sgl-project/sglang/commit/2b119ba388dd615084b55b31c04fdff6ecb0510f)

- **作者**: Yuhao Yang
- **时间**: 2026-04-05T08:03:17Z
- **提交信息**: [diffusion] fix: fix accuracy for flux series (#22059)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [71544f0](https://github.com/sgl-project/sglang/commit/71544f0341dc610f7157c21cae6f573eeb1941bd)

- **作者**: Xiancheng Meng
- **时间**: 2026-04-05T07:46:30Z
- **提交信息**: [model] support voxtral (speech-to-text) (#21635)

Co-authored-by: mengxiancheng03 <mengxiancheng03@kuaishou.com>

### [904bb47](https://github.com/sgl-project/sglang/commit/904bb476d86b62aed1bf840db3be3ae2b1cf128b)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T07:30:57Z
- **提交信息**: Migrate reasoning_tokens tests to existing server fixtures (#22102)

### [bb9e058](https://github.com/sgl-project/sglang/commit/bb9e058f5b9d4754ac2965bb36864fee1cd978e8)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-05T07:24:50Z
- **提交信息**: Add failfast flag to rerun-test workflow (#22141)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1123
- **最后更新**: 2026-04-05T12:56:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 75366
- **最后更新**: 2026-04-05T22:53:21Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: Aaron Batilo, Wei Zhao, Netanel Haber

## AI分析总结

根据提供的提交记录和README摘要（vLLM项目专注于“易用、快速、经济的LLM服务”），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导（5/7），涉及模型兼容性、JSON解析、模块导入和推测解码。
- **性能优化**：2项提交，针对MoE（混合专家）模型和Trtllm FP8推理。
- **CI/基础设施更新**：1项，调整CI作业硬件配置。

### 2. 关键变更点及其与项目方向的关系
| 提交 | 关键变更点 | 与项目方向的关系 |
|------|-----------|----------------|
| **d56e952** | 修复Nano Nemotron VL模型在视频性能分析时的张量设备不匹配异常 | 增强**视觉语言模型（VLM）支持**，提升多模态服务稳定性 |
| **f53fa26** | 修复Gemma 4流式工具调用中的无效JSON问题（去除部分分隔符） | 确保**流式输出可靠性**，关键于生产级服务 |
| **228023b** | 修复MoE解码性能回归（优化多流共享专家重叠） | 直接提升**解码速度**，符合“快速”核心目标 |
| **1af6f78** | 优化Trtllm FP8 MoE的权重布局（使用Shuffled Weights和BlockMajorK） | 提升**低精度推理效率**，降低计算成本 |
| **9a52826** | 修复VLM模型在推测解码中提取隐藏状态的问题 | 完善**推测解码对VLM的支持**，提升吞吐量 |
| **4dd49b0** | 修复`encoder_cudagraph`模块的导入路径 | 维护**模块化架构**的健壮性 |
| **56de443** | CI作业切换到H200 MIG切片 | 利用**新一代硬件**进行测试，保持基础设施先进性 |

### 3. 对项目的影响和潜在意义
- **用户体验**：修复Gemma 4 JSON解析和VLM相关Bug，提升**服务可靠性**，减少中断风险。
- **性能与成本**：MoE解码优化和FP8布局改进直接强化**高吞吐量、低成本**的核心优势，尤其利好大规模部署。
- **模型生态扩展**：对Nemotron VL和VLM推测解码的修复，支持**更广泛的模型类型**，吸引多模态应用开发者。
- **开发维护**：导入路径修复和CI更新有助于**长期代码健康**和测试效率。

### 4. 值得关注的技术点
- **MoE性能调优**：通过“多流共享专家重叠”缓解解码回归，反映对**稀疏模型高效服务**的持续投入。
- **低精度推理优化**：Trtllm FP8的权重布局调整，显示在**硬件适配与量化**上的深入探索。
- **流式输出处理**：Gemma 4的JSON修复涉及**部分结果处理**，对实时交互场景至关重要。
- **视觉语言模型集成**：多个提交涉及VLM，表明项目正积极**扩展多模态能力**。

### 5. 基于项目背景的提交影响分析
vLLM旨在提供“**易用、快速、经济**的LLM服务”。昨日的更新整体**强化了这一使命**：
- **快速与经济**：MoE解码优化和FP8布局改进直接提升**推理速度并降低资源消耗**，支撑高性能低成本服务。
- **易用与可靠**：修复模型兼容性和JSON解析问题，减少用户端错误，提升**开箱即用体验**。
- **生态扩展**：加强对VLM和Nemotron等模型的支持，**扩大适用场景**，吸引更广泛的用户群体。
- **基础设施现代化**：CI向H200迁移，确保测试环境与**行业硬件发展同步**，为未来优化奠定基础。

**总结**：昨日更新以**Bug修复和性能优化**为主，紧密围绕提升服务**稳定性、速度和模型兼容性**，直接推动vLLM在“高效LLM服务”领域的竞争力。

## 详细提交记录

### [d56e952](https://github.com/vllm-project/vllm/commit/d56e95223917ba21af2dd87a335dcb5c0b347bfe)

- **作者**: Netanel Haber
- **时间**: 2026-04-05T22:23:45Z
- **提交信息**: nano_nemotron_vl: fix tensor device mismatch exception when video profiling (#39029)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [56de443](https://github.com/vllm-project/vllm/commit/56de443db1d50dce2624a21765c11a79dffa8740)

- **作者**: Kevin H. Luu
- **时间**: 2026-04-05T20:26:11Z
- **提交信息**: [ci] Switch some CI jobs to H200 MIG slices (#38956)

### [4dd49b0](https://github.com/vllm-project/vllm/commit/4dd49b06f81af2238ac5a86cfb0b7220083eb125)

- **作者**: Greg Pereira
- **时间**: 2026-04-05T19:11:58Z
- **提交信息**: [Bug] Fix Import paths for `encoder_cudagraph` modules (#38997)

Signed-off-by: greg pereira <grpereir@redhat.com>
Signed-off-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [f53fa26](https://github.com/vllm-project/vllm/commit/f53fa26e05c476a43f6db048a9e3b43bcb2b72fb)

- **作者**: Greg Pereira
- **时间**: 2026-04-05T17:11:18Z
- **提交信息**: [Bugfix] Fix invalid JSON in Gemma 4 streaming tool calls by stripping partial delimiters (#38992)

Signed-off-by: greg pereira <grpereir@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [1af6f78](https://github.com/vllm-project/vllm/commit/1af6f78ae5a1bd3d70f32d47fe4901bda5c97fdd)

- **作者**: Wei Zhao
- **时间**: 2026-04-05T14:54:31Z
- **提交信息**: [Perf] Change Trtllm fp8 MoE to use Shuffled Weights and BlockMajorK Layout (#38993)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [228023b](https://github.com/vllm-project/vllm/commit/228023b3a58f78ed028cb4e5fb4e078bb1574262)

- **作者**: Martin Vit
- **时间**: 2026-04-05T14:28:31Z
- **提交信息**: [Bugfix][MoE] Fix 6-8% decode regression: prefer multi-stream shared expert overlap (#38990)

Signed-off-by: Martin Vit <martin@voipmonitor.org>
Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [9a52826](https://github.com/vllm-project/vllm/commit/9a528260ef648500262709550807c292098a70c0)

- **作者**: Aaron Batilo
- **时间**: 2026-04-05T09:41:54Z
- **提交信息**: [Bugfix][Spec Decode] Fix extract_hidden_states for VLM models (#38987)

Signed-off-by: Aaron Batilo <abatilo@coreweave.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-06
**监控日期**: 2026-04-05
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4128
- **最后更新**: 2026-04-05T20:54:24Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 7
- **主要提交者**: Yuanheng Zhao, Yueqian Lin, Hyoseop Song

## AI分析总结

根据 `vllm-project/vllm-omni` 的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）和提供的昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **Bug修复**：修复了 Qwen3-TTS 流式生成边界伪影、代码预测器数据类型对齐、请求输出中原始提示符赋值等问题。
- **性能优化**：针对 Fish Speech 和 Qwen3-TTS 模型，释放未使用的解码器或编解码器组件以节省 VRAM。
- **功能新增**：为 FluxKontextPipeline 等扩散模型管道添加了性能剖析器和进度条支持。
- **CI/构建改进**：新增了面向 NVIDIA GPU 用户的 Dockerfile，并移除了 CosyVoice3 的合并后测试。
- **项目维护**：更新了 `.gitignore` 文件以忽略 `uv.lock`。

### 2. 关键变更点及其与项目整体方向的关系
- **多模态服务优化**：针对 **TTS（文本转语音）** 模型（Qwen3-TTS, Fish Speech）的修复和性能优化，直接强化了项目的“omni-modality”（全模态）核心能力，使其在语音生成方面更稳定、高效。
- **资源效率提升**：通过释放未使用的 VRAM 组件，体现了项目对“cheap”（低成本）和“fast”（快速）的追求，有助于降低部署和运行成本。
- **开发者体验与部署便利性**：新增 Dockerfile 和修复 CI 流程，降低了用户（尤其是 NVIDIA GPU 用户）的入门和部署门槛，与“for everyone”的目标一致。
- **工具链完善**：为扩散模型管道添加剖析器和进度条，提升了复杂模型服务的可观测性和调试体验。

### 3. 对项目的影响和潜在意义
- **稳定性增强**：修复流式生成伪影和数据类型对齐问题，提升了 TTS 服务的输出质量和可靠性，减少生产环境故障。
- **资源利用率提高**：VRAM 优化可能允许在相同硬件上运行更大模型或更多并发请求，直接支持“cheap”和可扩展的服务。
- **生态扩展准备**：完善 Docker 支持和 CI 流程，为项目吸引更广泛的用户和贡献者铺平道路，促进社区增长。
- **维护性提升**：`.gitignore` 更新等细节改进有助于保持代码库整洁，减少不必要的提交冲突。

### 4. 值得关注的技术点
- **Qwen3-TTS 流式生成修复**：涉及实时音频流处理的边界伪影问题，对低延迟流式服务至关重要。
- **VRAM 动态释放策略**：在 Fish Speech 和 Qwen3-TTS 中主动释放未使用的模型组件，展示了针对大模型内存管理的精细优化技巧。
- **扩散管道性能剖析**：为 FluxKontextPipeline 等添加剖析器，可能涉及对采样步骤、内存使用等的深度监控，有助于性能调优。
- **Docker 化支持**：提供官方 CUDA Dockerfile，简化了 GPU 环境下的依赖管理和部署。

### 5. 基于项目背景的提交影响分析
vllm-omni 旨在成为**全模态、高性能、低成本的模型服务平台**。昨日的提交集中体现了这一愿景的落地：
- **强化全模态能力**：TTS 相关修复和优化直接提升了语音模态的服务质量，使项目在文本、图像（通过扩散模型）、语音等多模态支持上更加均衡和成熟。
- **践行“fast & cheap”**：VRAM 优化和性能剖析工具的加入，从资源利用率和可观测性两个维度推动服务效率提升，有助于实现低成本、高性能的承诺。
- **降低使用门槛**：通过 Docker 支持和 CI 简化，项目正朝着“for everyone”的目标迈进，使更多开发者和团队能够轻松部署和贡献。
- **聚焦生产就绪**：修复边界伪影、数据类型对齐等细节问题，表明项目正在从功能实现向生产稳定性和鲁棒性深化，这对于企业级应用至关重要。

**总结**：昨日的更新以 **Bug 修复和性能优化** 为主，紧密围绕项目的核心——**提升全模态（尤其是 TTS）服务的稳定性、效率和可访问性**。这些提交不仅解决了即时问题，还通过资源优化和工具增强为项目的长期发展（社区增长、生产部署）奠定了更坚实的基础。

## 详细提交记录

### [e23b263](https://github.com/vllm-project/vllm-omni/commit/e23b2634d17a339a3c83002ec1aa39b1f5fcb72e)

- **作者**: Will.hou
- **时间**: 2026-04-05T20:54:15Z
- **提交信息**: fix(qwen3_tts): align code predictor buffer dtype with model parameters (#2470)

Signed-off-by: willamhou <willamhou@ceresman.com>
Co-authored-by: willamhou <willamhou@ceresman.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Happy <yesreply@happy.engineering>

### [8b57c62](https://github.com/vllm-project/vllm-omni/commit/8b57c6205e8db6703e83402ace641ce9673d2ebf)

- **作者**: Sy03
- **时间**: 2026-04-05T20:49:18Z
- **提交信息**: [Perf][Fish Speech] Free unused DAC codec components to save VRAM (#2430)

Signed-off-by: Sy03 <1370724210@qq.com>

### [f6cfacd](https://github.com/vllm-project/vllm-omni/commit/f6cfacdd160b73537019221d0b32e4d5831ac592)

- **作者**: Sy03
- **时间**: 2026-04-05T19:04:37Z
- **提交信息**: [Perf][Qwen3-TTS] Free unused decoder in Talker SpeechTokenizer to VRAM (#2429)

Signed-off-by: Sy03 <1370724210@qq.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [025408f](https://github.com/vllm-project/vllm-omni/commit/025408f693fb3ef0f82456481f48ceda653c8909)

- **作者**: Sy03
- **时间**: 2026-04-05T18:40:38Z
- **提交信息**: [Fix] [Qwen3-TTS] Qwen3-TTS streaming chunk-boundary artifacts (#2480)

Signed-off-by: Sy03 <1370724210@qq.com>

### [b2b2ab0](https://github.com/vllm-project/vllm-omni/commit/b2b2ab0c3c0e6999fa00c908a501f59bc33ec308)

- **作者**: Hyoseop Song
- **时间**: 2026-04-05T16:48:31Z
- **提交信息**: [CI/Build] Add Dockerfile.cuda for NVIDIA GPU users [Skip-CI] (#1439)

Signed-off-by: Hyoseop Song <crad_on25@naver.com>
Signed-off-by: Hyoseop Song  <crad_on25@naver.com>

### [88f7ed9](https://github.com/vllm-project/vllm-omni/commit/88f7ed9fb6a33c8ffd0211e891f8396543c615e9)

- **作者**: Yuanheng Zhao
- **时间**: 2026-04-05T10:46:11Z
- **提交信息**: [Bugfix] Assign original prompt back to RequestOutput (#2498)

Signed-off-by: Yuanheng Zhao <jonathan.zhaoyh@gmail.com>

### [dd9ca6f](https://github.com/vllm-project/vllm-omni/commit/dd9ca6feef7fe7176644ef950b744e93fe34aaf0)

- **作者**: Zhengyuan Su (苏政渊)
- **时间**: 2026-04-05T07:43:00Z
- **提交信息**: [Bugfix] Include uv.lock in .gitignore (#2493)

Signed-off-by: Zhengyuan Su (苏政渊) <su.zhengyuan@u.nus.edu>

### [832952b](https://github.com/vllm-project/vllm-omni/commit/832952b2beb1dcba3b328b3ea43e21f4569fc9cd)

- **作者**: Lancer
- **时间**: 2026-04-05T07:16:11Z
- **提交信息**: [Feat] add diffusion pipeline profiler and progress bar support to FluxKontextPipeline et.al (#2489)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [0824ede](https://github.com/vllm-project/vllm-omni/commit/0824edefd5e60fdc9eaf66c16ad692f161b3c322)

- **作者**: Yueqian Lin
- **时间**: 2026-04-05T07:05:52Z
- **提交信息**: ci: remove CosyVoice3 post-merge test (#2492)

---
