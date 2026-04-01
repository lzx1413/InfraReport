# GitHub Stars 合并报告 - 2026-04-01

**合并日期**: 2026-04-02
**监控日期**: 2026-04-01
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


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1786
- **最后更新**: 2026-04-01T18:43:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhiyu Wu

## AI分析总结

根据提供的提交记录和README摘要，以下是对VeOmni项目昨日更新的分析总结：

### 1. 主要更新类型
*   **功能新增/适配**：本次提交的核心是功能适配，将Qwen2模型更新至支持`transformers`库的v5版本。

### 2. 关键变更点及其与项目整体方向的关系
*   **关键变更**：更新了`Qwen2`模型相关的代码，使其与`transformers` v5版本兼容。
*   **与项目方向的关系**：VeOmni旨在构建一个“以模型为中心的分布式配方动物园”，支持多模态模型训练。保持对主流模型（如Qwen2）和核心框架（如`transformers`）最新版本的支持，是确保项目**前沿性、兼容性和易用性**的基础，完全符合其作为“配方动物园”和训练解决方案的定位。

### 3. 对项目的影响和潜在意义
*   **直接影响**：确保了使用VeOmni框架训练或微调Qwen2系列模型的用户，可以无缝使用`transformers`库的最新特性和优化。
*   **潜在意义**：
    *   **降低用户使用门槛**：避免了用户因版本不匹配导致的兼容性问题。
    *   **维持生态同步**：使VeOmni能够紧跟Hugging Face `transformers`生态的快速发展，间接获得其性能改进和新功能。
    *   **示范作用**：为如何将其他模型适配到新版本`transformers`提供了参考。

### 4. 值得关注的技术点
*   **`transformers` v5兼容性**：`transformers` v5版本可能引入了新的API、模型架构优化或训练特性。此次更新暗示VeOmni团队正在积极跟进这些底层依赖的重要升级。
*   **大语言模型（LLM）支持**：明确提及`Qwen2`，表明VeOmni不仅关注多模态，也持续投入对主流纯文本大语言模型的分布式训练支持。

### 5. 基于项目背景的提交影响分析
*   **巩固项目核心价值**：README强调VeOmni是一个“配方动物园”。本次更新相当于为“Qwen2”这个热门“食材”提供了适配最新“厨具”（`transformers` v5）的**配方**，直接增强了项目作为**一站式、最新、可用配方集合**的核心价值。
*   **支持“Scaling”目标**：项目目标包括“Scaling Any Modality Model Training”。保持与`transformers`这样的基础框架的版本同步，是确保分布式训练方案能在最新软件栈上稳定、高效运行的前提，从而支持更大规模的模型训练。
*   **体现持续维护与社区响应**：此类依赖库版本更新提交，显示了项目团队对代码库的**持续维护**和对开源生态演进的**快速响应**，这对于吸引开发者和用户参与至关重要。

**总结**：这是一次**关键的维护性功能更新**。它虽不是新增模态或算法，但通过确保与核心依赖生态的同步，**维护并提升了VeOmni作为前沿、可用、易用的分布式模型训练配方库的实用性和可靠性**，是项目健康发展和保持竞争力的必要日常活动。

## 详细提交记录

### [a4b5ddc](https://github.com/ByteDance-Seed/VeOmni/commit/a4b5ddc7cc0c9af50e054a457e8c918794685df3)

- **作者**: Zhiyu Wu
- **时间**: 2026-04-01T18:43:24Z
- **提交信息**: [model] feat: update Qwen2 to transformers v5 (#526)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2129
- **最后更新**: 2026-04-01T07:42:16Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: PengGao

## AI分析总结

根据提供的仓库README摘要和提交记录，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增/合并**：本次提交（`f766d71`）是一个合并提交（`#981`），将分支 `Gp/merged` 的内容合并到主分支。这通常意味着整合了多项开发工作，可能包含新功能、修复或优化。

### 2. 关键变更点及其与项目整体方向的关系
- **合并操作**：将 `Gp/merged` 分支合并到主分支，表明团队正在整合阶段性开发成果，以保持代码库的同步和稳定。
- **协作贡献**：提交由 `wangshankun` 共同创作（Co-authored-by），体现了团队协作和代码审查流程。
- **与项目方向的关系**：LightX2V 是一个轻量级视频生成推理框架，专注于高效推理。合并分支可能引入了新模型支持、性能改进或架构优化，以增强框架的轻量化和实用性，符合其“Light”和“Inference Framework”的核心目标。

### 3. 对项目的影响和潜在意义
- **代码整合**：确保主分支包含最新功能，提升项目完整性和可用性。
- **稳定性提升**：合并前通常经过测试，有助于减少潜在错误，提高框架可靠性。
- **协作效率**：展示团队高效协作模式，为后续开发奠定基础。
- **潜在意义**：可能为即将发布的版本或新特性铺平道路，吸引更多用户或贡献者。

### 4. 值得关注的技术点
- **分支管理**：`Gp/merged` 分支的命名可能指向特定功能或优化（如 GPU 相关改进），但需查看具体代码变更确认。
- **合并策略**：提交记录简洁，未显示详细变更内容，建议查看合并的 Pull Request #981 以了解具体技术细节（如是否涉及模型架构、推理速度或内存优化）。
- **协作流程**：使用 Co-authored-by 标签，符合开源项目最佳实践，促进透明贡献。

### 5. 基于项目背景的提交影响分析
- **项目背景**：LightX2V 旨在提供轻量、高效的视频生成推理框架，可能针对实时或资源受限场景。
- **发展影响**：
  - **功能增强**：如果合并引入了新模型或优化，将直接提升框架的竞争力和适用性。
  - **性能优化**：可能改进推理速度或降低资源消耗，强化“Light”特性。
  - **生态建设**：定期合并贡献有助于活跃社区，推动项目向成熟框架发展。
  - **用户体验**：稳定整合可减少用户使用障碍，促进 adoption。

**建议**：由于提交记录信息有限，如需深入分析，可查看关联的 Pull Request #981 的详细描述和代码变更，以获取更具体的技术洞察。

## 详细提交记录

### [f766d71](https://github.com/ModelTC/LightX2V/commit/f766d71b3f93dbca7e248f6f25bc1ceb3c5e5a1e)

- **作者**: PengGao
- **时间**: 2026-04-01T07:42:10Z
- **提交信息**: Gp/merged (#981)

Co-authored-by: wangshankun <wangshankun2011@hotmail.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1993
- **最后更新**: 2026-04-01T12:27:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5252
- **最后更新**: 2026-04-01T22:20:31Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: Yong Wu, Brian K. Ryu, Yinzuo Jiang

## AI分析总结

根据FlashInfer项目（专注于高性能GPU推理内核）的README背景和昨日提交记录，以下是分析总结：

### 1. 主要更新类型
- **功能新增**：实现了Top-K内核的确定性模式（#2661）；为CUTLASS MoE后端添加了Relu2激活函数支持（#2926）。
- **Bug修复**：修复了向量化函数导致的CPU争用（#2935）、KV块缩放因子步幅读取问题（#2844）、MoE自动调优崩溃（#2916）以及JIT编译中缺失的GDC标志导致的随机崩溃（#2913）。
- **性能优化**：优化了CuTe-DSL的FP4/FP8量化内核（#2904）；为cuDNN后端添加了动态形状支持以减少编译开销（#2910）。
- **文档更新**：在贡献指南中添加了CI触发说明（#2924）。
- **工具/配置更新**：升级了CI中的cuDNN版本（#2930）。

### 2. 关键变更点及其与项目方向的关系
- **确定性Top-K**：通过实现稳定的排序逻辑，提升了推理结果的可复现性，符合项目对**可靠、高性能推理**的核心目标。
- **量化内核优化**：采用双路径（线性+Swizzled）架构和整数位操作，提升了MXFP4/NVFP4/FP8量化的性能，直接服务于项目**优化低精度计算效率**的方向。
- **动态形状与GDC修复**：cuDNN动态形状重用预编译图，减少开销；GDC标志修复确保SM12x等新架构上内核同步正确，增强了**对新硬件和复杂工作负载的兼容性与稳定性**。
- **MoE相关修复与功能**：修复了路由和激活函数支持问题，巩固了项目在**混合专家模型推理**领域的竞争力。

### 3. 对项目的影响和潜在意义
- **提升可靠性**：确定性Top-K和多项崩溃修复减少了生产环境中的不确定性和错误风险。
- **性能增益**：量化优化和动态形状支持预计将提升吞吐量，降低延迟，尤其在批量可变场景中。
- **扩展适用性**：Relu2激活支持使项目能服务于更多先进模型（如Nemotron-H），增强了生态适配性。
- **开发者体验**：CI文档更新和工具链升级改善了贡献流程和测试一致性。

### 4. 值得关注的技术点
- **确定性实现机制**：在线程交错顺序（thread-strided order）和原子操作结合下保证稳定输出，兼顾性能与确定性。
- **向量化替代Python循环**：使用PyTorch张量操作消除CPU瓶颈，展示了**计算密集型预处理优化**的典型模式。
- **GDC（Grid Dependency Control）**：针对SM90/100+架构的内核同步标志，是**避免新一代GPU上数据竞争**的关键。
- **CuTe-DSL双路径量化**：根据问题规模自适应选择线程配置和内存布局，体现了**面向特定硬件特性的精细化优化**。

### 5. 基于项目背景的提交影响分析
FlashInfer旨在提供**极致性能的GPU推理内核**。昨日的提交集体推动了以下发展：
- **强化核心能力**：Top-K确定性和量化优化直接提升了关键算子的**性能与确定性**，这是推理引擎的核心竞争力。
- **扩大硬件与模型覆盖**：GDC修复和SM12x支持确保了在**最新GPU架构（如Blackwell）上的稳定运行**；Relu2激活支持扩展了**模型兼容性**。
- **改善工程健壮性**：多项修复减少了边缘情况下的崩溃风险，提升了**生产就绪性**。
- **优化开发与部署流程**：CI和自动调优改进有助于**加速迭代和降低部署开销**。

**总结**：昨日更新聚焦于**性能、稳定性和扩展性**，既深化了核心算子的优化，又解决了新硬件和复杂模型下的实践问题，整体推动FlashInfer向更高效、更可靠的GPU推理解决方案迈进。

## 详细提交记录

### [637209a](https://github.com/flashinfer-ai/flashinfer/commit/637209a4de7addeaff049136b0b7bec92b2665ed)

- **作者**: Yinzuo Jiang
- **时间**: 2026-04-01T22:20:24Z
- **提交信息**: feat: implement deterministic topk (#2661)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

> Part of the FilteredTopK implementation refers to or is adapted from
@Linda-Stadter's work in #2759

### Deterministic Mode for Top-K Kernels

#### FilteredTopK Kernel

FilteredTopKKernel implements deterministic mode as follows:

1. Build a coarse histogram.

- Build a coarse histogram on the top 8 bits to locate the coarse
threshold bin that contains the k-th largest element.
- Same as non-deterministic mode, elements with bin > threshold_bin are
appended to s_indices via **atomicAdd** (see
`collect_gt_and_nondet_eq_threshold`); their final order is determined
by the post-sort kernel.

2. Refine with 8-bit radix passes.

- Run multiple 8-bit refine passes to find the exact pivot.
- Deterministic == pivot selection is performed by
`collect_det_eq_pivot`, which writes the selected tie elements into
`s_indices` in deterministic **thread-strided order**.

> **Thread-strided order** means, for example, if `BLOCK_THREADS = 4`,
then the logical scan order is:
>
> - thread 0: `0, 4, 8, ...`
> - thread 1: `1, 5, 9, ...`
> - thread 2: `2, 6, 10, ...`
> - thread 3: `3, 7, 11, ...`
>
> If the `== pivot` positions are:
> - thread 0: `0, 8`
> - thread 1: `5`
> - thread 2: none
> - thread 3: `3, 7`
>
>  then the deterministic collection order is: [0, 8, 5, 3, 7].
> That is, we order elements first by thread ID, and then by each
thread's strided traversal order.

3. Post-sort kernels.

- After FilteredTopKKernel finishes, `SortTopKByIndexKernel` is applied
to produce index-ascending output and make the final ordering
deterministic (we use atomicAdd to collect > pivot at stage 1).
- If the Python API is called with sorted=True,
`StableSortTopKByValueKernel` is applied afterward to produce
value-descending output.

#### RadixTopK Kernel


1. RadixSelectFindPivot

- Finds `ordered_pivot`, which Stage 2 uses to determine whether an
element is >= `ordered_pivot`.
- Computes `cta_local_eq_count` and `cta_local_gt_count`, which Stage 2
uses to **determine** how many elements the current CTA may emit and
where each emitted element should be placed.

2. collect_indices (`RadixCollectIndicesDeterministic`)

RadixCollectIndicesDeterministic: after the pivot is known, assigns each
CTA a fixed output range, then writes all > pivot elements followed by
the required == pivot elements in a deterministic order.

Order definition:

- Emit > pivot elements first, then == pivot elements.
- For each category, earlier CTAs write to earlier output positions.
- Within each CTA, emit elements in thread-strided order.

### Benchmarks

machine: NVIDIA A100-PCIE-40GB

command: (fp32/fp16/bf16)
```bash
python -u benchmarks/bench_topk.py \
  --op all \
  --dtype fp32 \
  --deterministic \
  --compare-torch-deterministic \
  --input-pattern random
```

raw results:


[output.txt](https://github.com/user-attachments/files/26337712/output-group2-current-v1_5-20260330-101411.txt)
**Summary**


| dtype | geomean det slowdown vs non-det | geomean speedup vs torch.det
|
  | --- | ---: | ---: |
  | fp32 | 1.0992x | 1.7660x |
  | fp16 | 1.0777x | 1.3381x |
  | bf16 | 1.0745x | 1.3055x |


NOTE: FlashInfer deterministic **underperforms** PyTorch mainly on
short-sequence workloads. Importantly, this is not unique to the
deterministic path: FlashInfer non-deterministic top-k is also slower
than PyTorch in the same short-sequence regime. This suggests the gap is
primarily a short-sequence top-k issue rather than a
deterministic-specific regression. Optimizing short-sequence top-k, for
both non-deterministic and deterministic modes, is better treated as
future work.



## 🔍 Related Issues

close: #2584


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

```
unittest I ran:
test_topk.py
test_sampling.py
test_logits_processor.py
```
## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Deterministic mode for top‑k and fused transforms (stable, repeatable
tie ordering) with API flag to enable deterministic outputs and stable
sorting behavior.

* **Benchmarks**
* Expanded benchmarking to compare deterministic vs nondeterministic
runs, pre-generated input patterns, DSA workload cases, and richer CLI
output.

* **Tests**
* Large suite of determinism and correctness tests (ties, multi‑CTA,
streams, sorted behavior, cache transitions).

* **Bug Fixes**
  * Improved runtime-error labeling and benchmark cache handling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yinzuo Jiang <jiangyinzuo@foxmail.com>
Signed-off-by: Linda-Stadter <57756729+Linda-Stadter@users.noreply.github.com>
Co-authored-by: Linda-Stadter <57756729+Linda-Stadter@users.noreply.github.com>

### [5a906be](https://github.com/flashinfer-ai/flashinfer/commit/5a906be2fd9c9298887a8108336b67f0148bfcb5)

- **作者**: youkaichao
- **时间**: 2026-04-01T20:25:49Z
- **提交信息**: fix: vectorize get_shuffle_matrix_a_row_indices to eliminate CPU contention (#2935)

## Problem

Closes #2934.

`get_shuffle_matrix_a_row_indices` in `flashinfer/utils.py` used a
Python `for` loop iterating over all `M` rows of the weight matrix to
build the shuffle index permutation. For large models this loop is slow
(~0.5s per call on large weight matrices), and when multiple
tensor-parallel ranks finish loading their weight shards at the same
time, all ranks hit this CPU-bound loop simultaneously. This causes
severe CPU contention — ranks that happen to start earlier monopolize
the CPU cores and the stragglers are delayed by up to ~30 minutes, even
though the final permutation is identical across all ranks (same `M`,
same `shuffle_block_size`, same `row_map`).

The false dependency between ranks compounds the problem: all ranks are
computing the same result independently, yet they serialize on CPU.

## Fix

Replace the Python for-loop with vectorized PyTorch tensor operations:

```python
# Before: O(M) Python loop — slow and causes CPU contention
for old_row in range(M):
    block_idx = old_row // shuffle_block_size
    row_in_block = old_row % shuffle_block_size
    mapped_row_in_block = row_map[row_in_block]
    new_row = block_idx * shuffle_block_size + mapped_row_in_block
    row_indices[new_row] = old_row

# After: vectorized — equivalent logic, no Python loop
old_rows = torch.arange(M, dtype=torch.long)
row_map_tensor = torch.tensor(row_map, dtype=torch.long)
mapped_rows = row_map_tensor[old_rows % shuffle_block_size]
new_rows = (old_rows // shuffle_block_size) * shuffle_block_size + mapped_rows
row_indices[new_rows] = old_rows
```

The logic is identical — only the implementation changes from a scalar
Python loop to bulk tensor operations, which is orders of magnitude
faster for large `M`. After the fix, the function takes around 0.05s.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
* Optimized internal tensor operations to improve performance
efficiency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

### [d476c61](https://github.com/flashinfer-ai/flashinfer/commit/d476c61c3f8bcbbca30755b330a0c10b141dede3)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-01T19:08:51Z
- **提交信息**: perf: Optimize CuTe-DSL fp4 and fp8 quantization kernels (#2904)

<!-- .github/pull_request_template.md -->

## 📌 Description

**Summary**
- Adopt dual-path kernel architecture (linear flat + swizzled row-based)
for MXFP4 and NVFP4 CuTe-DSL quantization kernels.
- Architecture chanes to MXFP8 quantization for better perf.
- Expand benchmark scripts and test coverage across all three
quantization kernels. Compares exact output match between CUDA &
CuTe-DSL backends
- **All mxfp4, mxfp8, and nvfp4 quantization have exact bitwise match in
for CUDA vs. CuTe DSL backends in both the output and scaling factors.**

**Kernel changes**
`mxfp8_quantize.py`
- Adaptive 2T/SF dispatch: 2 threads per SF block for large problems
(total_sf >= 65536), 4 threads for small problems for better memory
bandwidth utilization.
- Integer UE8M0 conversion (float_to_ue8m0_fast,
ue8m0_to_inv_scale_fast): replaces SFU-based lg2.approx/ex2.approx with
integer bit manipulation, freeing the SFU pipeline
- reduce_max_2threads: 1-shuffle XOR reduction for the 2T path
- Remove unused self.dtype and self.K attributes              
`mxfp4_quantize.py`
- Add swizzled kernel. Previously only supported linear layout.
- Swizzled kernel: small-K multi-row path and large-K column-loop path,
compile-time selected via const_expr(needs_col_loop)
- Inline padding for swizzled layout (row and column) — eliminates the
expensive separate flat-iteration padding passes that caused 5x+
regression at small M
- Dynamic thread count via _compute_optimal_threads(K) for 100% thread
utilization
`nvfp4_quantize.py`
- Same dual-path split: NVFP4QuantizeLinearKernel +
NVFP4QuantizeSwizzledKernel
- Supports all three SF layouts (128x4, 8x4, linear) with compile-time
dispatch
- Remove unused self.row_tile_size and self.ROW_ITERATIONS from TMA
kernel
 `quantization_cute_dsl_utils.py`
- ue8m0_to_inv_scale_fast: integer bit construction replacing ex2.approx
- reduce_max_2threads: 1-shuffle reduction for 2T/SF MXFP8 path
- 2T/SF constants: ELTS_PER_THREAD, THREADS_PER_SF, SF_BLOCKS_PER_WARP +
legacy 4T variants
- MXFP8_2T_SF_THRESHOLD = 65536     

**Test changes**
- `test_fp4_quantize.py` and `test_fp8_quantize.py`: Add more problem
sizes.
- `test_fp4_quantize_padding.py`: Add both-backend parametrization and
CUDA-vs-CuTe-DSL parity test for linear layout padding.

**Perf comparison between backends on B200**

<details>
  <summary>Click to see mxfp8 performance comparison</summary>

Linear (gmean 1.42x)

<img width="1644" height="1477"
alt="mxfp8_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/21b630ff-d1a7-427b-9e59-5b6417c498c6"
/>

Swizzled (gmean 1.37x)

<img width="1644" height="1477"
alt="mxfp8_backend_comparison_swizzled_bfloat16"
src="https://github.com/user-attachments/assets/f9d19958-df34-4fc9-8351-6b9348aba8c6"
/>


</details>

<details>
  <summary>Click to see mxfp4 performance comparison</summary>

Linear (gmean 1.41x)

<img width="1644" height="1477"
alt="mxfp4_quantize_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/e050a38d-600e-43c1-92eb-f0b51e22accf"
/>


Swizzled (gmean 1.39x)

<img width="1644" height="1477"
alt="mxfp4_quantize_backend_comparison_swizzled_bfloat16"
src="https://github.com/user-attachments/assets/d4e4cd72-baad-4057-9523-63cd6665bf6e"
/>

</details>

<details>
  <summary>Click to see nvfp4 performance comparison</summary>

Linear (gmean 1.34x)

<img width="1644" height="1477"
alt="nvfp4_quantize_backend_comparison_linear_bfloat16"
src="https://github.com/user-attachments/assets/532ef7f2-0a41-406c-8eda-0f16436672c1"
/>


Swizzled (gmean 1.32x)

<img width="1644" height="1477"
alt="nvfp4_quantize_backend_comparison_swizzled_bfloat16"
src="https://github.com/user-attachments/assets/9694e1d3-e92e-45c9-81b5-527dca4e6cd1"
/>


</details>

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Benchmarks now run and report both linear and swizzled scale-factor
layouts separately, generating distinct heatmaps/tables and layout-aware
labels.
* Added a new NVFP4 quantization benchmark with bandwidth and comparison
modes.

* **Refactor**
* Quantize kernels split into layout-specific implementations and
introduced dual-mode threading optimizations for better performance
across sizes.

* **Tests**
* Expanded parameter sweeps, added backend parameterization, and
capability-aware skips.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7924dc0](https://github.com/flashinfer-ai/flashinfer/commit/7924dc02f9c0a7a927f6ca04f23e18e4cc72b26b)

- **作者**: sychen52
- **时间**: 2026-04-01T17:43:58Z
- **提交信息**: read real strides for kv and block scale (#2844)

Acked-by: Shiyang Chen <shiychen@nvidia.com>

<!-- .github/pull_request_template.md -->

## 📌 Description

I realize that current kv block scale factor's stride is derived from kv
cache instead of reading from the actual tensor. This put a lot of
unnecessary assumption/constraint on the scale factor.


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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Chores**
* Kernel launcher and runtime updated to accept explicit stride
parameters for key/value scale tensors and propagate them for kernel
execution, improving KV cache stride handling.
* **Documentation**
* Expanded backend-specific docs describing KV layout, contiguity and
stride constraints for KV data and per-block scale tensors; clarified
automatic transpose/contiguous copy behavior, expected shapes and
dtypes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a67a7ab](https://github.com/flashinfer-ai/flashinfer/commit/a67a7ab8d78f574f66263c91f99c924fd6d70e3d)

- **作者**: Yong Wu
- **时间**: 2026-04-01T17:02:20Z
- **提交信息**: doc: add CI triggering guide to CONTRIBUTING.md (#2924)

<!-- .github/pull_request_template.md -->

## 📌 Description

doc: add CI triggering guide to CONTRIBUTING.md

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

* **Documentation**
* Enhanced contribution guidelines with detailed Continuous Integration
info: public GitHub Actions and an internal CI, when CI runs and
draft-PR behavior, how to trigger/approve/rerun/stop workflows via bot
commands and labels, and a GPU/CUDA test matrix mapping unit, multi-GPU,
and multi-node test targets (with some manual-trigger-only jobs).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d55028b](https://github.com/flashinfer-ai/flashinfer/commit/d55028b778163650677849e94efec2b224acd011)

- **作者**: yanqinz2
- **时间**: 2026-04-01T16:24:35Z
- **提交信息**: Yanqinz/dynamic shape unified api (#2910)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add cudnn override shape support for bf16 and fp4 gemm.
Current bf16/nvfp4 gemm cudnn backend uses static shape approach, which
rebuild the execution plan every time a new shape is encountered, which
introduces tons of compilation overhead and repeated cached graphs.
This PR introduces override shape support and makes it as default option
for cudnn backend, which reuse the pre-built cudnn graph and execution
plans during the autotuning phase for the following problem sizes
encountered, avoid repeated graph/execution plan caching and compilation
overhead.

## 🔍 Related Issues

https://nvbugspro.nvidia.com/bug/5539146

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Refactor**
* Standardized cuDNN GEMM public API names, removing redundant exported
symbols.

* **New Features**
* Added an optional policy parameter to cuDNN graph builders (defaults
to heuristic choice).

* **Bug Fixes**
  * Improved workspace buffer reallocation for dynamic-shape operations.
* Corrected shape/stride handling for override-shape execution and added
safer fallback when override support is unavailable.

* **Tests**
* Updated tests to use renamed APIs and adjusted FP4 quantization calls.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yanqin Zhai <yanqinz@nvidia.com>

### [23b3279](https://github.com/flashinfer-ai/flashinfer/commit/23b3279868432f1e93d3ce0c6217eb10131d18de)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-01T13:40:22Z
- **提交信息**: fix: Fix autotuner crash on meta-device tensor in trtllm_fp4_block_scale_routed_moe  Description: (#2916)

<!-- .github/pull_request_template.md -->

## 📌 Description

#### Summary
- Fixes `RuntimeError: Cannot pack tensors on meta when
trtllm_fp4_block_scale_routed_moe` is called with autotuning enabled
- Ensures the autotuner profiles the correct kernel code path
(no-routing) when routing is pre-computed

#### Root Cause
Wh#en `trtllm_fp4_block_scale_routed_moe` is called, `routing_logits` is
`None` because routing has already been done (pre-computed `topk_ids`
are provided instead). To give the autotuner a tensor with the right
shape/dtype for profile generation, a placeholder was created with
`device="meta"`:

```
torch.empty(num_tokens, num_experts, dtype=routing_dtype, device="meta")
```
This worked without autotuning because `choose_one` returns early (only
inspects .size() for the cache key, never passes the tensor to a
kernel).

With autotuning enabled, `choose_one` enters the profiling loop, which
calls `_create_tensor_like` on the placeholder. That method copies
`origin_tensor.device`, so the derived profiling tensor is also on
`"meta"`. When the profiling path calls `MoERunner.forward`, this meta
tensor is passed to the C++ kernel via TVM FFI, which attempts DLPack
conversion and fails: the meta device has no real memory.

#### Fix
Three changes in `flashinfer/fused_moe/core.py:`

- Replace `device="meta"` with `device=hidden_states.device` — the
placeholder is now a real CUDA tensor so the autotuner can safely derive
profiling tensors from it.
- Pass `skip_routing=(routing_logits is None)` through `kwargs` to
`choose_one`, signaling that routing was pre-computed.
- In `MoERunner.forward`, set `routing_logits = None` when
`skip_routing=True` — this ensures the C++ kernel takes the same
no-routing code path during profiling as it does in production. Without
this, the autotuner would profile with routing computation enabled
(random `routing_logits` data), potentially selecting a suboptimal
tactic for the actual inference path where routing is skipped.

#### Unit test changes
Added test_fp4_routed_moe_autotune_no_crash regression test in
`tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py` The
test calls `trtllm_fp4_block_scale_routed_moe` inside `autotune(True)`
with `num_tokens=1` and `num_tokens=16`, verifying no crash occurs.

Main branch fails the newly added tests before the changes in
`flashinfer/fused_moe/core.py:`
```
$ pytest tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py
...
tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py ....FF...   
...
FAILED tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py::test_fp4_routed_moe_autotune_no_crash[4-16-1] - RuntimeError: Cannot pack tensors on meta
FAILED tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py::test_fp4_routed_moe_autotune_no_crash[4-16-16] - RuntimeError: Cannot pack tensors on meta
====================================================================================== 2 failed, 7 passed in 4.08s ======================================================================================
```

After fix:
```
$ pytest tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py
...
tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py .........                                                                                                                           [100%]

=========================================================================================== 9 passed in 6.47s ============================================================================================
```


<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

## 🔍 Related Issues

#2023

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
* Added skip routing support for Mixture of Experts operations, enabling
optimization when routing computation can be bypassed.

* **Tests**
* Added regression test for FP4 routed Mixture of Experts autotuning to
ensure stability across token configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b12d344](https://github.com/flashinfer-ai/flashinfer/commit/b12d3449de76650ddea58e3d91c07fcf6a780c4f)

- **作者**: Johnny
- **时间**: 2026-04-01T08:29:41Z
- **提交信息**: fix(jit): enable GDC for CUTLASS fused MoE PDL — prevent random crashes on SM12x (#2913)

### Summary

- Add missing `-DCUTLASS_ENABLE_GDC_FOR_SM100=1` compile flag to all
CUTLASS fused MoE JIT modules (SM100/SM103/SM120) and
`-DCUTLASS_ENABLE_GDC_FOR_SM90=1` to SM90 modules
- Sync nv_internal `grid_dependency_control.h` with upstream CUTLASS to
support SM100/SM103/SM110/SM120/SM121 GDC
- Add `-DCUTLASS_ENABLE_GDC_FOR_SM90=1` to FP8 blockscale GEMM SM90
module

### Problem

Random `cudaErrorIllegalInstruction` crashes on DGX Spark (SM121) and
RTX 50-series (SM120) when running NVFP4 MoE models (e.g., Nemotron,
Qwen3.5-122B) under load. The crashes are intermittent and worsen with
longer context lengths and higher concurrency.

**Root cause:** PR #2780 fixed the missing GDC compile flags for GEMM
modules (`flashinfer/jit/gemm/core.py`), but the **CUTLASS fused MoE
modules** in `flashinfer/jit/fused_moe.py` and the **FP8 blockscale GEMM
module** were not fixed. This is the exact same class of bug as #2708.

Without `-DCUTLASS_ENABLE_GDC_FOR_SM100=1`, CUTLASS's
`grid_dependency_control.h` compiles `wait_on_dependent_grids()` and
`launch_dependent_grids()` as **empty no-ops**:

```cpp
CUTLASS_DEVICE void wait_on_dependent_grids() {
#if (defined(CUTLASS_GDC_ENABLED))   // ← not defined without the flag
  asm volatile("griddepcontrol.wait;");
#endif
}
```

Meanwhile, the host-side code still sets
`programmaticStreamSerializationAllowed = true` (PDL enabled) via
`device_support_pdl()` which returns `True` for all `major >= 9`,
including SM12x. This means:

1. **Host enables PDL** → CUDA runtime overlaps consecutive kernels
2. **Device GDC barriers are no-ops** → No synchronization between
overlapping kernels
3. **Race condition** → Dependent kernel reads stale global memory →
corruption → `cudaErrorIllegalInstruction`

The crash is random because it depends on exact kernel scheduling
timing, which varies per request.

### Fix

**`flashinfer/jit/fused_moe.py`** — Added GDC flags to all CUTLASS fused
MoE modules:

| Module | Flag | Architectures Covered |
|---|---|---|
| `gen_cutlass_fused_moe_sm120_module()` |
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` | SM120, SM121 |
| `gen_cutlass_fused_moe_sm103_module()` |
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` | SM103, SM120, SM121 |
| `gen_cutlass_fused_moe_sm100_module()` |
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` | SM100, SM110, SM120, SM121 |
| `gen_cutlass_fused_moe_sm90_module()` |
`-DCUTLASS_ENABLE_GDC_FOR_SM90=1` | SM90 |
| `gen_trtllm_gen_fused_moe_sm100_module()` |
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` | SM100+, SM120, SM121 |

**`flashinfer/jit/gemm/fp8_blockscale.py`** — Added
`-DCUTLASS_ENABLE_GDC_FOR_SM90=1` to
`gen_fp8_blockscale_gemm_sm90_module()`.

**`csrc/nv_internal/.../grid_dependency_control.h`** — Synced with
upstream CUTLASS
(`3rdparty/cutlass/include/cutlass/arch/grid_dependency_control.h`) to
add SM100+ GDC support. Previously only handled SM90, so any nv_internal
TensorRT-LLM code compiled for SM12x would have GDC barriers silently
compiled as no-ops.

### Why `-DCUTLASS_ENABLE_GDC_FOR_SM100=1` covers SM12x

CUTLASS uses a single flag for the entire Blackwell family. From
`grid_dependency_control.h`:

```cpp
#if(CUDA_BARRIER_ENABLED && defined(CUTLASS_ENABLE_GDC_FOR_SM100) && defined(__CUDA_ARCH__) && \
    ((__CUDA_ARCH__ == 1000 && ...) ||   // SM100
     (__CUDA_ARCH__ == 1030 && ...) ||   // SM103
     (__CUDA_ARCH__ == 1100 && ...) ||   // SM110
     (__CUDA_ARCH__ == 1200 && ...) ||   // SM120 (RTX 50-series)
     (__CUDA_ARCH__ == 1210 && ...)))    // SM121 (DGX Spark)
#define CUTLASS_GDC_ENABLED
```

### Why SM90 GDC flag was NOT added to SM100+ modules

PR #2716 attempted to add both `-DCUTLASS_ENABLE_GDC_FOR_SM90=1` and
`-DCUTLASS_ENABLE_GDC_FOR_SM100=1` to all modules. It broke AOT builds
because `sm120_gemm_tma_warpspecialized_cooperative_asymmetric_dma.hpp`
checks `CUTLASS_ENABLE_GDC_FOR_SM90` and calls
`scheduler.is_last_tile()` — a method not present on the SM120
scheduler. PR #2780 corrected this by using only the SM100 flag for
SM100+ modules. This PR follows the same approach.

### Related

- #2708 — Original issue: missing GDC flags cause PDL race condition
- #2716 — First fix attempt (reverted — broke AOT)
- #2780 — Corrected fix for GEMM modules only
-
[vllm-project/vllm#38423](https://github.com/vllm-project/vllm/pull/38423)
— NVFP4 bugfix on DGX Spark
- [NVIDIA/cutlass#3121](https://github.com/NVIDIA/cutlass/pull/3121) —
K=64 block-scaled GEMM tiles (separate issue)

### Test plan

- [x] Clear JIT cache: `rm -rf ~/.cache/flashinfer/`
- [x] Run NVFP4 MoE model on SM121 (DGX Spark) with 128K context under
load — verify no `cudaErrorIllegalInstruction`
- [x] Run NVFP4 MoE model on SM120 (RTX 50-series) with concurrent
requests — verify no NaN/garbage output
- [x] Verify `CUDA_LAUNCH_BLOCKING=1` workaround is no longer needed
- [x] AOT build with `FLASHINFER_CUDA_ARCH_LIST="12.1a"` completes
without errors
- [x] SM90 (Hopper) fused MoE tests pass: `pytest tests/moe/`
- [x] SM100 GEMM tests still pass (no regression from existing GDC
flags)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded GPU kernel compilation support: enabled additional
optimizations for NVIDIA SM100 and SM90 GPUs, activating
dependency-control optimizations where available.
* Updated JIT/GEMM build configs to include these architecture-specific
compile options, improving performance and compatibility on supported
hardware.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2c675fb](https://github.com/flashinfer-ai/flashinfer/commit/2c675fb1df66679fe82126ac313a278d91045bbc)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-01T08:07:19Z
- **提交信息**: docker: upgrade cuDNN to latest version in CI install script (#2930)

Replace minimum version constraint with --upgrade flag to ensure CI
containers always get the latest cuDNN version, fixing inconsistency
between cu12 and cu13 containers.

Fixes #2929

Generated with [Claude Code](https://claude.ai/code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

## Chores
* Updated NVIDIA cuDNN packages in Docker installation to the latest
available versions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: claude[bot] <41898282+claude[bot]@users.noreply.github.com>
Co-authored-by: Brian K. Ryu <bkryu@users.noreply.github.com>

### [d47f327](https://github.com/flashinfer-ai/flashinfer/commit/d47f3275df5b2058151b802124c892598bb1232c)

- **作者**: Andrii Skliar
- **时间**: 2026-04-01T08:07:01Z
- **提交信息**: feat: add Relu2 (squared ReLU) activation support in CUTLASS MoE backend (#2926)

## Summary

Add **Relu2 (squared ReLU) activation** support for the CUTLASS MoE GEMM
path, enabling models that use Relu2 as their MoE gate activation (e.g.
Nemotron-H MTP draft model) to run through the FlashInfer CUTLASS
backend instead of throwing `InvalidType` at runtime.

## Problem

Two pieces were missing:

1. `epilogue_helpers.h` had no `EpilogueOpDefaultRelu2` tag struct or
`Epilogue` partial specialization, so there was no CUTLASS epilogue type
for Relu2.
2. `moeGemmBiasAct()` in `moe_gemm_template_dispatch.h` had no `case
ActivationType::Relu2`, causing it to fall through to `InvalidType` and
throw.

The `Relu2` functor itself (`relu(x)²`) already existed in
`fused_activations.h` — this PR just wires it into the epilogue
dispatch.

## Changes

- **`epilogue_helpers.h`**: Added `EpilogueOpDefaultRelu2` tag struct
and a corresponding `Epilogue<..., EpilogueOpDefaultRelu2>` partial
specialization that instantiates the existing `Relu2Op` functor via
`LinearCombinationGeneric`.
- **`moe_gemm_template_dispatch.h`**: Added `case ActivationType::Relu2`
to `moeGemmBiasAct()`, dispatching to the new epilogue type.

## Test plan

- [ ] Existing MoE tests pass: `pytest tests/moe/`
- [ ] Relu2-specific tests: `pytest
tests/moe/test_trtllm_gen_fused_moe.py -k Relu2`
- [ ] Manual: run a Relu2 MoE model (e.g. Nemotron-H MTP) through vLLM
with FlashInfer CUTLASS backend and verify no `InvalidType` errors

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added Relu2 activation function support for model computation kernels.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3336
- **最后更新**: 2026-04-01T22:34:16Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Jinzhe Pan, vishruthb

## AI分析总结

根据提供的README摘要和提交记录，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：新增了Gen3C（Cosmos-7B）模型及流水线支持。
- **持续集成/部署优化**：两项提交涉及CI流程的改进，包括分支同步策略调整和测试重试机制增强。

### 2. 关键变更点及其与项目整体方向的关系
- **新增Gen3C模型支持**：这表明项目正在积极扩展其支持的视频生成或处理模型生态，与README中提到的“FastVideo”作为高效视频AI工具包的定位一致，旨在提供更丰富的模型选择。
- **CI流程优化**：
  - 将分支同步策略从`rebase`改为`update`，可能旨在减少冲突风险或简化同步流程。
  - 引入测试重试机制并聚合状态刷新，提升了CI的稳定性和反馈效率，有助于维护代码质量。

### 3. 对项目的影响和潜在意义
- **功能增强**：Gen3C模型的加入直接丰富了项目的模型库，可能吸引更多用户或开发者关注，提升项目在视频AI领域的竞争力。
- **开发体验提升**：CI优化减少了开发过程中的摩擦，提高了团队协作效率和代码交付的可靠性，对长期项目维护有积极影响。

### 4. 值得关注的技术点
- **Gen3C（Cosmos-7B）模型**：这是一个较新的模型，可能针对视频生成、编辑或理解任务进行了优化，值得关注其性能特点及与现有模型的差异。
- **CI策略调整**：从`rebase`切换到`update`可能涉及Git工作流的调整，反映了团队对版本控制最佳实践的持续优化。

### 5. 基于项目背景的提交影响分析
- **项目背景**：从README推断，FastVideo是一个专注于高效视频AI处理的工具包，可能强调快速推理、易用性和模型多样性。
- **影响分析**：
  - 模型扩展（Gen3C）直接支持了项目的核心目标——提供先进的视频AI解决方案，增强了项目的实用性和前沿性。
  - CI优化虽不直接影响终端用户，但通过提升开发效率间接促进了项目迭代速度，有助于更快地响应用户需求和技术演进。

**总结**：昨日更新以功能扩展和开发流程优化为主，既强化了项目在视频AI模型方面的能力，又通过CI改进提升了团队生产力，整体上推动了项目向更稳定、更功能丰富的方向发展。

## 详细提交记录

### [5789955](https://github.com/hao-ai-lab/FastVideo/commit/5789955bbeb67356259ea3d8c7b6dcc3a3a7e4d1)

- **作者**: vishruthb
- **时间**: 2026-04-01T11:42:02Z
- **提交信息**: [feat] add gen3c (cosmos-7b) model and pipeline support (#1059)

### [2ad84a3](https://github.com/hao-ai-lab/FastVideo/commit/2ad84a3b7889f7545b20e47339281ad354618538)

- **作者**: Jinzhe Pan
- **时间**: 2026-04-01T11:16:59Z
- **提交信息**: [ci] Use update instead of rebase for auto branch sync (#1215)

### [12d699c](https://github.com/hao-ai-lab/FastVideo/commit/12d699cd7869a50b82100d80e936e32325e1c338)

- **作者**: Jinzhe Pan
- **时间**: 2026-04-01T09:21:28Z
- **提交信息**: [ci] Add direct test retry with check overwrite and aggregate status refresh (#1214)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33234
- **最后更新**: 2026-04-01T19:21:16Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Steven Liu, Andrew Ross

## AI分析总结

### 1. 主要更新类型
- **文档更新**：提交1（e365d74）涉及文档调整，标记部分pipeline为已弃用（deprecated）。
- **Bug修复**：提交2（b935381）修复了单文件路径验证逻辑的问题。

### 2. 关键变更点及其与项目整体方向的关系
- **弃用pipeline**：提交1中，项目开始弃用某些pipeline，并更新相关文档和链接。这与项目（Diffusers库）持续优化架构、推动模块化和灵活性的方向一致，可能旨在简化代码库或引导用户转向更高效的API。
- **路径验证修复**：提交2修正了单文件路径验证逻辑，确保文件处理更可靠。这符合项目对稳定性和兼容性的重视，尤其是在处理模型和配置文件时。

### 3. 对项目的影响和潜在意义
- **用户迁移**：弃用pipeline可能影响现有用户，需引导他们更新代码以适应新API，短期可能带来不便，但长期有助于提升代码可维护性。
- **稳定性提升**：路径验证修复减少了潜在的文件处理错误，增强了库的鲁棒性，对依赖文件加载的功能（如模型导入）尤为重要。

### 4. 值得关注的技术点
- **弃用策略**：项目通过文档更新和链接调整来管理弃用过程，体现了良好的向后兼容性实践。
- **路径验证逻辑**：修复涉及测试更新（`test_modular_pipelines_common.py`），强调了测试在维护代码质量中的作用。

### 5. 基于项目背景的提交影响分析
- **项目背景**：Diffusers库专注于扩散模型，提供预训练模型和pipeline以简化生成任务。README强调易用性、模块化和社区驱动。
- **影响发展**：
  - 弃用pipeline可能推动用户采用更模块化的组件，符合项目向灵活、可定制架构演进的趋势。
  - Bug修复直接提升了库的可靠性，支持项目在快速迭代中保持稳定性，有助于维持用户信任和社区贡献。

**总结**：昨日更新以文档调整和Bug修复为主，既反映了项目在架构优化上的持续努力，也通过细节改进增强了用户体验。这些变更平衡了创新与稳定性，支持Diffusers库作为领先扩散模型工具库的长期发展。

## 详细提交记录

### [e365d74](https://github.com/huggingface/diffusers/commit/e365d749a1a260e31a1373415255a1288909ef7e)

- **作者**: Steven Liu
- **时间**: 2026-04-01T17:16:23Z
- **提交信息**: [docs] deprecate pipelines (#13157)

* deprecate

* fix

* fix

* fix

* fix

* remove deprecated .md files

* update links

* fix

### [b935381](https://github.com/huggingface/diffusers/commit/b9353819a491727636cf4afeac165aaf709ec9ae)

- **作者**: Andrew Ross
- **时间**: 2026-04-01T15:08:42Z
- **提交信息**: corrects single file path validation logic (#13363)

* corrects single file path validation logic

* Update tests/modular_pipelines/test_modular_pipelines_common.py

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

---------

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-27T06:03:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12146
- **最后更新**: 2026-04-01T17:37:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25312
- **最后更新**: 2026-04-01T22:44:46Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 21
- **主要提交者**: Mick, DarkSharpness, yudian0504

## AI分析总结

根据提供的提交记录和README摘要（SGLang是一个专注于高效LLM推理和服务的项目），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及测试、内存分配、竞态条件、Tokenizer初始化、生成控制等多个方面。
- **性能优化与功能新增**：主要集中在**推理后端优化**（FlashInfer集成、TRT-LLM稀疏MLA、动态GPU缓冲区）和**硬件支持扩展**（MUSA/FA3、NPU）。
- **测试与CI/CD增强**：增加了扩散模型精度CI、NPU完整测试管道、网络超时处理、合并策略等。
- **代码重构与清理**：删除重复代码，移除不必要的包装器。
- **文档更新**：更新了NPU（昇腾）相关文档。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **GPU异构TP KV传输的动态环形分配器** (#19890) | 直接服务于**分布式推理性能**，是核心优化。 |
| **集成FlashInfer TRT-LLM MXFP8 GEMM** (#21576) | 提升**计算效率与吞吐量**，符合高性能推理目标。 |
| **支持MUSA上的FA3注意力后端** (#18648) | 扩展对**国产硬件（沐曦）** 的支持，体现生态扩展。 |
| **为NPU添加完整测试管道** (#20751) | 强化对**华为昇腾NPU**的官方支持与稳定性。 |
| **修复多GPU VLM服务中的共享内存竞态** (#21655) | 确保**视觉语言模型服务**的稳定性和正确性。 |
| **多项Bug修复**（如Mamba内存分配、生成暂停） | 提升**系统整体稳定性与可靠性**，是项目成熟度的体现。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性显著提升**：大量Bug修复和测试增强，使项目更健壮，适合生产环境。
- **性能与效率持续优化**：针对KV缓存、注意力计算、数据传输等核心路径的优化，直接提升推理速度和吞吐量。
- **硬件与生态壁垒进一步打破**：加强对国产硬件（MUSA、NPU）和多种后端（FlashInfer, TRT-LLM）的支持，增强了项目的适应性和竞争力。
- **复杂模型支持更完善**：针对扩散模型、VLM、MoE、Mamba等模型的修复和优化，表明项目正深入支持前沿和复杂的模型架构。

### 4. 值得关注的技术点
1.  **动态环形分配器**：用于GPU间异构张量并行（TP）的KV传输，可能是一种解决内存碎片和提升传输效率的创新内存管理方案。
2.  **TRT-LLM稀疏MLA内核**：针对Prefill批处理的稀疏混合专家（MoE）注意力优化，是处理大模型长上下文和稀疏激活的关键技术。
3.  **JIT RMSNorm更新**：即时编译优化层归一化操作，可能带来低延迟推理的收益。
4.  **硬件后端抽象**：FA3 on MUSA、NPU benchmark等提交，展示了项目良好的硬件抽象层设计，便于集成新硬件。

### 5. 基于项目背景的提交影响分析
SGLang的目标是成为**高效、灵活且支持广泛硬件的LLM推理与服务引擎**。昨日的提交集体体现了这一方向的快速推进：
- **向“生产就绪”迈进**：密集的Bug修复和CI强化，表明项目重心从功能实现转向**系统稳定性和交付质量**，这是开源项目获得大规模应用的关键一步。
- **深化性能护城河**：对推理核心路径（注意力、内存、传输）的持续优化，巩固了其在高性能推理领域的技术优势。
- **构建开放生态**：积极适配MUSA、NPU等不同硬件，并集成TRT-LLM、FlashInfer等优秀后端，展现了**不绑定单一技术栈**的开放策略，有利于吸引更广泛的社区和厂商合作。
- **覆盖前沿模型**：对扩散模型、VLM、MoE、Mamba等模型的支持与优化，确保项目能跟上LLM及应用快速演进的步伐，保持其技术前瞻性和实用性。

**总结**：昨日的更新是一次以**夯实基础、优化核心、扩展生态**为主的综合性推进。它不仅在修复问题和提升稳定性，更在关键的性能路径和硬件适配层面进行深度优化，充分体现了SGLang项目在追求极致推理性能的同时，积极构建一个稳定、开放、支持广泛硬件的下一代服务引擎的战略方向。

## 详细提交记录

### [1ac74e6](https://github.com/sgl-project/sglang/commit/1ac74e652e2429d425290206a57484c6e011669f)

- **作者**: Alison Shao
- **时间**: 2026-04-01T22:44:35Z
- **提交信息**: [Misc] Fix comparator e2e tests: add polars dep + fix dp-attention test (#21804)

Co-authored-by: Alison Shao <alison.shao@mac.lan>

### [70fc4ce](https://github.com/sgl-project/sglang/commit/70fc4ce3efcf54ca91d239cefd044fc71bda2a02)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-01T22:08:09Z
- **提交信息**: Add merge prohibition policy during CI maintenance mode (#21882)

### [821a8a9](https://github.com/sgl-project/sglang/commit/821a8a99fbeceb246a9ec2c2873f73ea6c283b58)

- **作者**: YAMY
- **时间**: 2026-04-01T21:09:18Z
- **提交信息**: [Disagg] GPU staging buffer with dynamic ring allocator for heterogeneous TP KV transfer (#19890)

### [5e12c4e](https://github.com/sgl-project/sglang/commit/5e12c4e08ec3bd74972a938513f763a0cb10769e)

- **作者**: Baizhou Zhang
- **时间**: 2026-04-01T20:55:05Z
- **提交信息**: [DSA] Support trtllm sparse mla kernel for prefill batches  (#21783)

### [8950d12](https://github.com/sgl-project/sglang/commit/8950d129bdee9b9824ebd006befa433038b0e3f8)

- **作者**: Trevor Morris
- **时间**: 2026-04-01T20:52:22Z
- **提交信息**: [refactor] Clean up duplicate flashinfer trtllm moe code (#21233)

### [0138708](https://github.com/sgl-project/sglang/commit/01387085762bf9e75bc6f3a0a06b033e99174da0)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-01T20:16:14Z
- **提交信息**: [Misc] Add network timeout to eval dataset downloads (#21873)

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [a19ef3a](https://github.com/sgl-project/sglang/commit/a19ef3a61539bbf8628e4717de5214c80f2393d2)

- **作者**: Ziang Li
- **时间**: 2026-04-01T19:55:06Z
- **提交信息**: [FlashInver v0.6.7] Integrate flashinfer_trtllm mxfp8 gemm (#21576)

### [a1c725b](https://github.com/sgl-project/sglang/commit/a1c725bdc50d7d9f82bbdd5ecc65c54328d274ac)

- **作者**: shuwenn
- **时间**: 2026-04-01T17:54:53Z
- **提交信息**: fix: pre-init tokenizer_manager to avoid AttributeError in shutdown (#21824)

### [ca3286d](https://github.com/sgl-project/sglang/commit/ca3286d2d59776446c5cbc3c4f504af074fbdd95)

- **作者**: R0CKSTAR
- **时间**: 2026-04-01T17:49:34Z
- **提交信息**: [diffusion] hardware: support FA3 attention backend on MUSA (attn backend, 14/N) (#18648)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [6098c51](https://github.com/sgl-project/sglang/commit/6098c51bc229c360857d36832f4e6bdaa8c65dde)

- **作者**: shuwenn
- **时间**: 2026-04-01T16:47:27Z
- **提交信息**: fix(MiMo-V2-Flash): add mimo reasoning parser (#21414)

### [c9f5d1d](https://github.com/sgl-project/sglang/commit/c9f5d1d5028c66cb61968d5830c91eefbfe3695d)

- **作者**: yuefeng Wu
- **时间**: 2026-04-01T15:53:10Z
- **提交信息**: [Diffusion][NPU] add ring sp performance benchmark page in npu (#21811)

### [20f4193](https://github.com/sgl-project/sglang/commit/20f41935897261cd38ff183518ace948dfb31984)

- **作者**: DarkSharpness
- **时间**: 2026-04-01T15:40:00Z
- **提交信息**: [Feature] JIT rmsnorm update (with claude) (#21834)

### [4f5b55e](https://github.com/sgl-project/sglang/commit/4f5b55e37947177e77b1ca754089edcd2b879150)

- **作者**: Ratish P
- **时间**: 2026-04-01T13:51:36Z
- **提交信息**: [diffusion][CI]: Add individual component accuracy CI for diffusion models (#18709)

Co-authored-by: Xiaoyu Zhang <35585791+BBuf@users.noreply.github.com>

### [e67b95d](https://github.com/sgl-project/sglang/commit/e67b95d66b092fa36f666fc2a575e76f45464441)

- **作者**: Cherry_ming
- **时间**: 2026-04-01T11:56:31Z
- **提交信息**: [NPU]Add a full test pipeline on NPU, resolve issues in the NPU test architecture (#20751)

### [ac039bd](https://github.com/sgl-project/sglang/commit/ac039bd04ed31f7dc09f69d89fb36c69276ad551)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-01T11:26:11Z
- **提交信息**: Use CustomTestCase for TestSessionControl to enable CI retry (#21830)

### [1aabe44](https://github.com/sgl-project/sglang/commit/1aabe44b64a4ab422b910fcd15fa1c2c21c90aa8)

- **作者**: Yuhao Yang
- **时间**: 2026-04-01T09:39:50Z
- **提交信息**: [VLM] remove AsyncMMDataProcessor wrapper (#21651)

### [80b1bc5](https://github.com/sgl-project/sglang/commit/80b1bc5f565afbebf7e1da4369a35d8a6b098f72)

- **作者**: amote-i
- **时间**: 2026-04-01T09:14:26Z
- **提交信息**: [NPU] update ascend docs (#21807)

### [7bba319](https://github.com/sgl-project/sglang/commit/7bba319f1e845ff0a156d21c623cf84a8f0533e0)

- **作者**: Mick
- **时间**: 2026-04-01T08:47:59Z
- **提交信息**: [diffusion] fix: respect --prompt-path (#21756)

### [95b8814](https://github.com/sgl-project/sglang/commit/95b881452e737a6eb465691612c9246266d74f6f)

- **作者**: wduan-hai
- **时间**: 2026-04-01T08:36:28Z
- **提交信息**: Fix in-place mode in pause generation (#21705)

### [eec7028](https://github.com/sgl-project/sglang/commit/eec70286ec56f2172605184f9b8ed373e97483f0)

- **作者**: yunkchen
- **时间**: 2026-04-01T08:17:14Z
- **提交信息**: [Bugfix] Fix effective_mamba_size over-allocation (#20858)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [7d2b856](https://github.com/sgl-project/sglang/commit/7d2b856ce73479aedd48f32d4f1e9b634215e952)

- **作者**: yudian0504
- **时间**: 2026-04-01T08:15:14Z
- **提交信息**: [Bug][VLM] Fix shared memory race condition in ShmPointerMMData broadcast for multi-GPU VLM serving (#21655)

### [9eb7521](https://github.com/sgl-project/sglang/commit/9eb75211b166553552a0347c8acc78093d86b77e)

- **作者**: Zhiqiang Xie
- **时间**: 2026-04-01T08:03:17Z
- **提交信息**: style refinement for hisparse (#21198)

### [57341b1](https://github.com/sgl-project/sglang/commit/57341b128fb2b9d8c4388dd8bbc3f932d104bd11)

- **作者**: Yuxuan Zhang
- **时间**: 2026-04-01T07:21:10Z
- **提交信息**: glm_interleave for GLM-V (#21671)

### [835e196](https://github.com/sgl-project/sglang/commit/835e19656fcfd886e49e9ce684525c86c562636b)

- **作者**: khalilzhk
- **时间**: 2026-04-01T07:01:53Z
- **提交信息**: Bug fix for llama eagle3 (#21397)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1118
- **最后更新**: 2026-04-01T12:21:00Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的仓库README摘要（PyTorch-native推理引擎，专注于DiTs的混合缓存加速和大规模并行）和提交记录，以下是昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：所有提交均为文档更新，涉及CUDA Graphs性能结果和参数修正。
- **代码维护**：包含一个参数拼写修复（chore类型）。

### 2. 关键变更点及其与项目整体方向的关系
- **CUDA Graphs文档增强**：多次提交添加了更多CUDA Graphs性能结果，说明项目正在重点优化和展示其**推理性能**。
- **参数拼写修复**：修正`fullgraph`参数拼写，确保API使用的**准确性和用户体验**。
- **关系**：这些更新直接支持项目的核心目标——**高性能推理加速**，通过文档完善帮助用户理解和使用CUDA Graphs优化功能。

### 3. 对项目的影响和潜在意义
- **提升用户理解**：丰富的性能结果文档有助于用户评估CUDA Graphs在DiTs推理中的加速效果。
- **减少使用错误**：参数拼写修复避免了潜在的用户配置错误。
- **强化项目专业性**：持续更新文档反映了项目的活跃维护和对用户体验的重视。

### 4. 值得关注的技术点
- **CUDA Graphs的应用**：项目可能正在深入集成CUDA Graphs以减少内核启动开销，这是PyTorch推理优化的**关键技术**。
- **性能数据展示**：通过文档展示具体性能结果，暗示项目在**实际部署场景**中已取得显著加速效果。

### 5. 基于项目背景的提交影响分析
- **背景回顾**：项目是专注于DiTs（可能指Diffusion Transformers）的PyTorch推理引擎，核心优势是**混合缓存和并行计算**。
- **发展影响**：
  - 文档更新**强化了性能导向的宣传**，吸引更多用户关注其推理加速能力。
  - 聚焦CUDA Graphs表明项目在**底层计算优化**上持续投入，与“PyTorch-native”定位一致。
  - 这些更新虽未直接新增功能，但通过**完善文档和修复细节**，提升了项目的成熟度和可信度，有助于推广和实际应用。

**总结**：昨日更新以文档完善为主，重点突出CUDA Graphs性能优化，直接服务于项目的高效推理目标，体现了项目在性能优化和用户体验上的持续投入。

## 详细提交记录

### [d6b1393](https://github.com/vipshop/cache-dit/commit/d6b1393dda19f3b023468800930819f0468e6cbb)

- **作者**: DefTruth
- **时间**: 2026-04-01T12:20:54Z
- **提交信息**: docs: update cuda graphs docs (#950)

### [6e41902](https://github.com/vipshop/cache-dit/commit/6e419020214eb4f24d21e0408069339d61eaeb82)

- **作者**: DefTruth
- **时间**: 2026-04-01T11:59:34Z
- **提交信息**: docs: add more cuda graph perf results (#949)

### [8253635](https://github.com/vipshop/cache-dit/commit/8253635259d88f1ccaa0b6c7dc6b3b65914eafc0)

- **作者**: DefTruth
- **时间**: 2026-04-01T11:53:45Z
- **提交信息**: docs: add more cuda graph perf results (#948)

* docs: add more cuda graph perf results

* docs: add more cuda graph perf results

* docs: add more cuda graph perf results

* docs: add more cuda graph perf results

* docs: add more cuda graph perf results

* docs: add more cuda graph perf results

### [d05530e](https://github.com/vipshop/cache-dit/commit/d05530e3c825f3e373fba74bc92c09bd329b24a4)

- **作者**: DefTruth
- **时间**: 2026-04-01T07:27:31Z
- **提交信息**: chore: fix fullgraph param typo (#947)

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 74937
- **最后更新**: 2026-04-01T23:03:46Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 21
- **主要提交者**: Stefano Castagnetta, Harry Mellor, Chauncey

## AI分析总结

根据vLLM项目README中“Easy, fast, and cheap LLM serving for everyone”的核心目标，结合昨日（基于提交记录）的更新，分析总结如下：

### 1. 主要更新类型
- **Bug修复**：占主导地位（约10项），涉及预提交流程、模型解析、内核、执行器、安全等多个方面。
- **功能新增/增强**：包括新的执行器（RayExecutorV2）、新的量化融合（SiLU Block Quant Fusion）、新的数据类型支持（MXFP8）、新的内核（Triton bilinear_pos_embed for ViT）以及新模型支持（IBM Granite Vision）。
- **性能优化**：涉及内核优化（如Triton bilinear_pos_embed）和重构以提升效率（如简化FutureWrapper、简化多模态掩码）。
- **重构**：对MoE（混合专家）组件和MXFP8线性操作进行重构，提高代码模块化和可维护性。
- **文档更新**：更新支持模型列表并修复文档中的拼写错误和示例。
- **工具/流程改进**：修复预提交流程，并添加标签以触发验证。

### 2. 关键变更点及其与项目整体方向的关系
| 关键变更点 | 与项目方向（易用、快速、廉价）的关系 |
| :--- | :--- |
| **引入RayExecutorV2** (`#36836`) | **廉价/扩展性**：为分布式计算提供更现代、可能更高效的执行后端，有助于在集群上实现低成本、高扩展的LLM服务。 |
| **多项内核与性能修复/优化** (如TRT-LLM SM100限制、Triton异构TP修复、ViT位置编码内核) | **快速**：直接提升推理速度和硬件利用率。修复特定硬件（如GB300）的挂起问题，保障服务稳定性与性能。 |
| **量化与数据类型支持** (SiLU量化融合、MXFP8支持) | **快速 & 廉价**：通过更高效的量化技术减少模型内存占用和计算开销，从而提升速度并降低部署成本。 |
| **安全增强** (VideoMediaIO帧数限制) | **易用/稳定**：增强系统安全性，防止潜在的资源耗尽攻击，使服务更健壮可靠。 |
| **模型与工具解析支持** (IBM Granite模型、Qwen3CoderToolParser修复) | **易用**：扩大vLLM的模型生态和工具调用兼容性，让用户能更容易地服务更多类型的模型。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量的Bug修复，特别是涉及核心执行流程（预提交、KV传输、执行器）和内核（TRT-LLM、Triton）的修复，显著增强了生产环境的稳定性。
- **性能与效率边界拓展**：新的执行器、量化技术和内核优化，持续推动vLLM在吞吐量和延迟方面的性能极限。
- **生态与兼容性扩展**：支持新的模型（IBM Granite Vision）和持续改进工具解析器，加强了vLLM作为通用LLM服务引擎的定位。
- **代码健康度与可维护性**：重构工作（如MoE、FutureWrapper）有助于降低长期维护成本，为未来功能开发打下更好基础。

### 4. 值得关注的技术点
1.  **RayExecutorV2**：可能标志着vLLm分布式执行层的一次重要演进，值得关注其与旧版的差异和带来的优势。
2.  **MXFP8数据类型的集成与重构**：低精度格式（MXFP8）的深入支持是追求极致推理效率的关键方向。
3.  **针对特定硬件的内核调优与修复**：如对NVIDIA GB300（SM103）和Triton异构TP的修复，显示了项目对前沿硬件适配的深度投入。
4.  **SiLU Block Quant Fusion**：将激活函数（SiLU）与量化块融合，是模型优化中减少内核启动开销的典型技术。
5.  **安全加固**：在多媒体输入处理中引入帧数限制，体现了项目对生产环境安全性的重视。

### 5. 基于项目背景的提交影响分析
这些提交共同推动vLLm向其“**为所有人提供简单、快速、廉价的LLM服务**”的目标迈进：
- **快速**：通过**内核优化**（ViT Triton内核）、**量化融合**（SiLU Block Quant）和**执行器升级**（RayExecutorV2）直接提升推理性能。
- **廉价**：通过**更好的量化支持**（MXFP8）和**更高效的分布式执行**（RayExecutorV2）来降低计算资源消耗和成本。
- **易用**：通过**扩大模型支持**（IBM Granite）、**修复工具解析**（Qwen3CoderToolParser）和**增强安全性**，降低用户的使用门槛和运维负担。
- **稳定可靠**：大量的**Bug修复**和**流程完善**（预提交）确保了核心服务的高可用性，这是“为所有人服务”的基础。

**总结**：昨日的更新是一次以**巩固稳定性**为基础，同时**在性能、功能覆盖和架构现代化方面积极进取**的发布。它既解决了近期集成和运行中的实际问题，也布局了未来提升效率与扩展性的关键技术，完全符合vLLM致力于成为领先的、生产就绪的LLM推理引擎的战略方向。

## 详细提交记录

### [6241521](https://github.com/vllm-project/vllm/commit/6241521dd2751b036d43d4bfc965f68319c32068)

- **作者**: Nick Hill
- **时间**: 2026-04-01T22:35:06Z
- **提交信息**: [BugFix] Fix precommit breakage due to conflicting in-flight merges (#38759)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [1785dc5](https://github.com/vllm-project/vllm/commit/1785dc55014cfd39c488158a0542cd987fed53c8)

- **作者**: Kevin H. Luu
- **时间**: 2026-04-01T22:34:28Z
- **提交信息**: Revert "[Bugfix] Fix Qwen3CoderToolParser anyOf/oneOf type resolution for nullable params (#37831)" (#38751)

### [5450054](https://github.com/vllm-project/vllm/commit/54500546ac2c34d650ae6d7757777a005dfbc4c0)

- **作者**: Chang Su
- **时间**: 2026-04-01T22:16:44Z
- **提交信息**: [Bugfix] Preserve original ImportError in gRPC server entrypoint (#38673)

Signed-off-by: Chang Su <chang.s.su@oracle.com>

### [de5e6c4](https://github.com/vllm-project/vllm/commit/de5e6c44c6fb8aebcc67ff57e85693f6951c8795)

- **作者**: Jeffrey Wang
- **时间**: 2026-04-01T21:34:29Z
- **提交信息**: [Feat][Executor] Introduce RayExecutorV2 (#36836)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>

### [cb268e4](https://github.com/vllm-project/vllm/commit/cb268e4e55bf6455d96eec750e6f11dc48ed9ff2)

- **作者**: yzong-rh
- **时间**: 2026-04-01T21:28:26Z
- **提交信息**: [Refactor] Simplify FutureWrapper in MultiprocExecutor (#38644)

Signed-off-by: Yifan <yzong@redhat.com>
Signed-off-by: Yifan Zong <yzong@redhat.com>

### [6183cae](https://github.com/vllm-project/vllm/commit/6183cae1bd8db73ee579f6424382975b17d02fb0)

- **作者**: Stefano Castagnetta
- **时间**: 2026-04-01T19:08:40Z
- **提交信息**: [Bugfix] Restrict TRTLLM attention to SM100, fixing GB300 (SM103) hang (#38730)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [c09ad76](https://github.com/vllm-project/vllm/commit/c09ad767cda74fc7fb587afaf3a92d714e04e1d5)

- **作者**: Monishver
- **时间**: 2026-04-01T18:50:43Z
- **提交信息**: Feature/silu block quant fusion v1 (#32996)

Signed-off-by: Monishver Chandrasekaran <monishverchandrasekaran@gmail.com>

### [c9a9db0](https://github.com/vllm-project/vllm/commit/c9a9db0e023a03f7e2c40e43be302fb07512946a)

- **作者**: Wentao Ye
- **时间**: 2026-04-01T18:28:57Z
- **提交信息**: [Compile] Fix nvfp4 compile warning (#38573)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [cbe7d18](https://github.com/vllm-project/vllm/commit/cbe7d1809649b1a8a954eb155b52d418a5554c4b)

- **作者**: Chauncey
- **时间**: 2026-04-01T16:56:45Z
- **提交信息**: [Misc] Rename think_start_str/think_end_str to reasoning_start_str/reasoning_end_str (#38242)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [db5d071](https://github.com/vllm-project/vllm/commit/db5d0719e1057b876ed673ae6387d940962691bb)

- **作者**: Michael Goin
- **时间**: 2026-04-01T16:41:42Z
- **提交信息**: [Kernel] Add MXFP8 to Marlin GEMM/MoE and refactor Mxfp8LinearOp (#34664)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [dc0428e](https://github.com/vllm-project/vllm/commit/dc0428ebb879af3224e5d9ef5ab93cb04d8d1b27)

- **作者**: yzong-rh
- **时间**: 2026-04-01T15:23:15Z
- **提交信息**: [NIXL][BUG] Fix Triton heterogeneous TP (#37940)

Signed-off-by: Yifan <yzong@redhat.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [148c207](https://github.com/vllm-project/vllm/commit/148c2072ecb21afe293b0c55dc7c3915506fa995)

- **作者**: Jesus Talavera
- **时间**: 2026-04-01T15:22:25Z
- **提交信息**: Add ibm-granite/granite-vision-3.3-2b to supported models documentation (#38714)

Signed-off-by: Jesus Talavera <jesus.talavera@ibm.com>

### [2f5c3c1](https://github.com/vllm-project/vllm/commit/2f5c3c1ec07ff0d26fb667eadd1566615325fdd9)

- **作者**: majianhan
- **时间**: 2026-04-01T14:39:46Z
- **提交信息**: [Misc] Fix docstring typo: buildin -> builtin (#38722)

Co-authored-by: majianhan <majianhan@kylinos.cn>

### [fa246d5](https://github.com/vllm-project/vllm/commit/fa246d52318dadb7b6ca429d0f674a7375abe9ca)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-04-01T14:29:33Z
- **提交信息**: Fix shape comment in extract_hidden_states example (#38723)

Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>

### [7cf56a5](https://github.com/vllm-project/vllm/commit/7cf56a59a267d2f32860c96a601e56bb29f6627a)

- **作者**: bnellnm
- **时间**: 2026-04-01T13:44:08Z
- **提交信息**: [MoE Refactor] Make SharedExperts class for use with DefaultMoERunner (#35153)

Signed-off-by: Bill Nell <bnell@redhat.com>

### [5e30e9b](https://github.com/vllm-project/vllm/commit/5e30e9b9a9b0dc91927f2ec4ffbd92c4af3825c0)

- **作者**: Elvir Crnčević
- **时间**: 2026-04-01T13:11:10Z
- **提交信息**: [Bugfix] Revert "Zero-init MLA attention output buffers to prevent NaN from CUDA graph padding" (#38359)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Tyler Michael Smith <tyler@neuralmagic.com>

### [582340f](https://github.com/vllm-project/vllm/commit/582340f273666d768630aca65314dd104be41b14)

- **作者**: 손세정
- **时间**: 2026-04-01T12:22:29Z
- **提交信息**: [Bugfix] Fix Qwen3CoderToolParser anyOf/oneOf type resolution for nullable params (#37831)

Signed-off-by: AAISSJ <maze0717@g.skku.edu>
Signed-off-by: <>
Co-authored-by: 세덩 <saison@sedeong-ui-MacBookAir.local>

### [9923685](https://github.com/vllm-project/vllm/commit/992368522f69aa2df15a3f9539d138498e52c5bf)

- **作者**: yjz
- **时间**: 2026-04-01T10:41:49Z
- **提交信息**: [KVTransfer] Fix TpKVTopology.is_kv_replicated equality case (#38179)

Signed-off-by: JianDan0212 <zhangyj0212@gmail.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [58ee614](https://github.com/vllm-project/vllm/commit/58ee61422169ce17e08248f8efa1e9df434fe395)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-04-01T10:23:45Z
- **提交信息**: (security) Enforce frame limit in VideoMediaIO (#38636)

Signed-off-by: jperezde <jperezde@redhat.com>

### [f9f6a90](https://github.com/vllm-project/vllm/commit/f9f6a9097a0a2714f6d0fab1c04c5d1f0100d014)

- **作者**: Harry Mellor
- **时间**: 2026-04-01T09:31:02Z
- **提交信息**: Add `verified` label to trigger `pre-commit` (#38708)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [c75a313](https://github.com/vllm-project/vllm/commit/c75a31382418111b2d4cde4b67dd6352eb980bc9)

- **作者**: Zhanda Zhu
- **时间**: 2026-04-01T08:52:02Z
- **提交信息**: [Perf] triton bilinear_pos_embed kernel for ViT (#37948)

Signed-off-by: Zhanda Zhu <zhandazhu@gmail.com>

### [4f6eed3](https://github.com/vllm-project/vllm/commit/4f6eed3bd4a92c6bd513460ee85b917d6df88a17)

- **作者**: Lukas Geiger
- **时间**: 2026-04-01T08:18:22Z
- **提交信息**: [Core] Simplify multimodal masking (#34246)

Signed-off-by: Lukas Geiger <lukas.geiger94@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-02
**监控日期**: 2026-04-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4076
- **最后更新**: 2026-04-01T22:54:58Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: R0CKSTAR, Wu JIAZHEN, Roger Wang

## AI分析总结

根据 `vllm-project/vllm-omni` 仓库的 README 摘要（“Easy, fast, and cheap omni-modality model serving for everyone”）和昨日的提交记录，以下是对更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：3项（#2422, #2397, #2367），主要针对图像生成流程和分布式通信的稳定性。
- **功能新增**：4项（#2029, #2337, #1769, #1751），涵盖多模态模型支持、新硬件平台、扩散模型控制等。
- **性能优化**：1项（#2398），针对推理延迟和一致性进行优化。
- **CI/基础设施**：1项（#2401），调整测试资源配置。
- **文档/治理**：1项（#2419），更新项目治理页面。

### 2. 关键变更点及其与项目整体方向的关系
- **多模态模型扩展**（#2029, #1751）：新增对 Qwen-image、Z-Image、GLM-Image、HunyuanImage3.0 等图像模型的支持，并增强配置参数（如 `cfgP`），**直接强化了项目的“omni-modality”（全模态）核心定位**，使服务能覆盖更广泛的视觉-语言任务。
- **硬件生态拓展**（#2337）：增加对 Moore Threads GPUs（MUSA 平台）的支持，**体现了“for everyone”的包容性**，降低用户使用特定国产硬件的门槛。
- **图像生成流程加固**（#2422, #2397, #2398）：修复 Bagel 模型在 AR/DIT 工作流中的解码错误和回退问题，并优化 KV 缓存转发与时间步一致性，**提升了复杂多阶段图像生成服务的可靠性和效率**，对齐“fast”和“easy”的目标。
- **扩散模型控制增强**（#1769）：支持在扩散过程中按步中止，**为用户提供了更精细的生成控制**，改善交互体验。
- **分布式通信修复**（#2367）：确保 `all_gather` 操作的输入张量连续性，**提升多 GPU 场景下的稳定性**，支撑大规模服务部署。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：Bug 修复和性能优化减少了图像生成中的错误和延迟，使服务更稳定、响应更快。
- **生态扩展**：新增模型和硬件支持吸引了更广泛的用户群体（如使用国产 GPU 或特定多模态模型的团队），增强了项目竞争力。
- **开发者协作**：治理页面更新（#2419）反映了社区成长，有助于项目长期维护。
- **测试效率**：CI 资源调整（#2401）可能加快开发迭代速度。

### 4. 值得关注的技术点
- **HSDP（Hierarchical State-Distributed Parallelism）支持**（#2029）：用于扩展大视觉模型训练/推理，是分布式计算的前沿实践。
- **MUSA 平台集成**（#2337）：展示了项目对新兴国产 AI 硬件的适配能力，具有战略意义。
- **Bagel 工作流优化**（#2398, #2422）：涉及 AR/DIT 多阶段生成、KV 缓存管理和时间步同步，体现了对复杂多模态推理引擎的深度优化。
- **Step-boundary abort**（#1769）：在扩散模型中实现精细中断控制，可能为交互式应用（如实时编辑）奠定基础。

### 5. 基于项目背景的提交影响分析
- **强化“Omni-Modality”定位**：多项功能新增（尤其是图像模型支持）直接扩展了项目对多模态任务的服务范围，使用户能通过统一框架处理文本、图像等多种输入输出。
- **推动“Easy, Fast, and Cheap”目标**：
  - **Easy**：硬件平台支持和模型集成降低了部署门槛；Bug 修复减少了用户遇到问题的概率。
  - **Fast**：性能优化（如 KV 缓存转发）提升了推理速度；CI 优化可能加速开发测试流程。
  - **Cheap**：对 Moore Threads GPUs 等硬件的支持为用户提供了更多低成本算力选择。
- **促进社区与生态发展**：治理更新和广泛的技术贡献显示项目正处于活跃发展阶段，有助于形成健康开源生态。

**总结**：昨日更新紧密围绕 vllm-omni 的“全模态、高性能、易用、低成本”愿景，通过修复关键 Bug、扩展模型/硬件支持、优化核心性能，进一步巩固了其作为多模态模型服务框架的实用性和竞争力。

## 详细提交记录

### [bbae904](https://github.com/vllm-project/vllm-omni/commit/bbae904f1d9347d8b9a47dc1628ed7c332bc2c29)

- **作者**: NATURE
- **时间**: 2026-04-01T15:01:39Z
- **提交信息**: [Bugfix] Fix delayed decoding bug for Bagel AR/DIT workflow (L3 test_bagel_img2img error) (#2422)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [70a6265](https://github.com/vllm-project/vllm-omni/commit/70a62651b9ea4780ebc655c67e9243c6d8a7e3d6)

- **作者**: Lancer
- **时间**: 2026-04-01T12:01:09Z
- **提交信息**: [Feat] support HSDP for Qwen-image series, Z-Image, GLM-Image (#2029)

Signed-off-by: Lancer <maruixiang6688@gmail.com>

### [4e4bbc4](https://github.com/vllm-project/vllm-omni/commit/4e4bbc42a6f4d511ec6c3542bbb439afbe563892)

- **作者**: TJian
- **时间**: 2026-04-01T11:37:34Z
- **提交信息**: [CI] Tune GPU resources for test (#2401)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [6ef0e90](https://github.com/vllm-project/vllm-omni/commit/6ef0e907af7c9468fa45783669eb10ee03ffe905)

- **作者**: Roger Wang
- **时间**: 2026-04-01T11:35:48Z
- **提交信息**: Add new committers to governance page (#2419)

### [3def008](https://github.com/vllm-project/vllm-omni/commit/3def008b324f636940953862daedec54b9021a87)

- **作者**: R0CKSTAR
- **时间**: 2026-04-01T09:55:00Z
- **提交信息**: [Feat] Add MUSA platform support for Moore Threads GPUs (#2337)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>

### [bf5bd0a](https://github.com/vllm-project/vllm-omni/commit/bf5bd0a4c00feed487f5f5e70810de84fe3d4604)

- **作者**: 汪志鹏
- **时间**: 2026-04-01T09:29:02Z
- **提交信息**: [BugFix]: Fix bagel single-stage img2img fallback to text2img bug (#2397)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [3fd4a4d](https://github.com/vllm-project/vllm-omni/commit/3fd4a4dc27db9709604ac923aa278fcb583c4956)

- **作者**: Wu JIAZHEN
- **时间**: 2026-04-01T09:25:02Z
- **提交信息**: [Feat] Support step-boundary abort in diffusion (#1769)

Signed-off-by: jader <yjader@foxmail.com>
Signed-off-by: asukaqaq-s <1311722138@qq.com>
Co-authored-by: jader <yjader@foxmail.com>

### [d40840b](https://github.com/vllm-project/vllm-omni/commit/d40840b1144bce12e5cc4d5ced8fb22820e8fd81)

- **作者**: NATURE
- **时间**: 2026-04-01T08:50:45Z
- **提交信息**: [Perf] Bagel KV-ready early forwarding and time step consistency for /v1/chat/completions (#2398)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [08cb436](https://github.com/vllm-project/vllm-omni/commit/08cb436d4e9271fe6272702fe10da768aad42df9)

- **作者**: zdoba
- **时间**: 2026-04-01T08:41:25Z
- **提交信息**: Fix: ensure input tensor is contiguous in GroupCoordinator.all_gather (#2367)

Signed-off-by: daixinning <daixinning@163.com>
Co-authored-by: daixinning <daixinning@163.com>

### [c3376a4](https://github.com/vllm-project/vllm-omni/commit/c3376a466b67db11d5ac4abd9bc19f3f53eef145)

- **作者**: Ding Zuhao
- **时间**: 2026-04-01T08:33:02Z
- **提交信息**: [Feature][HunyuanImage3.0] Add cfgP to HunyuanImage3.0 (#1751)

Signed-off-by: Ding Zuhao <e1583181@u.nus.edu>

---
