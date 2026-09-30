# GitHub Stars 合并报告 - 2026-09-29

**合并日期**: 2026-09-30
**监控日期**: 2026-09-29
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


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2227
- **最后更新**: 2026-09-29T19:17:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2868
- **最后更新**: 2026-09-29T21:42:40Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: STwangyingrui

## AI分析总结

### 1. 主要更新类型
本次提交为**功能新增**，具体是添加了一套先进的、形状驱动的算子基准测试工具集。

### 2. 关键变更点及其与项目整体方向的关系
- **核心变更**：引入了针对 GEMM、MoE、稠密/稀疏注意力、以及 Ulysses/Ring 序列并行注意力等关键算子的系统化基准测试。
- **方向契合**：LightX2V 旨在提供“轻量级”的视频生成推理，其“轻”不仅体现在模型量化，也体现在对推理硬件的高效利用上。这套基准测试直接服务于**性能调优和硬件适配**这一核心方向，帮助用户量化并优化在特定硬件（如不同 GPU）上的推理效率。

### 3. 对项目的影响和潜在意义
- **提供深度诊断工具**：使得项目从“提供推理代码”延伸到“提供性能分析与优化指南”，极大地增强了框架的实用性和专业性。
- **促进硬件生态兼容**：通过支持生产后端自动发现、硬件峰值效率报告，能更清晰地指导用户在不同硬件上获得最佳性能，降低了部署门槛。
- **验证并行策略**：对序列并行（Ulysses, Ring）的基准测试，有助于评估和选择大规模分布式视频生成场景下的最优并行策略。

### 4. 值得关注的技术点
- **形状驱动方法论**：测试基于真实或合成的输入形状（而非固定形状），更贴近视频生成中多变的帧尺寸和分辨率场景。
- **后端自动发现与比较**：能自动评估不同计算后端（如 CUDA, Triton 等）的性能，为用户提供客观的配置建议。
- **通信与带宽诊断**：集成了对 L2/L3 通信的诊断，这对于优化多 GPU 并行推理至关重要。

### 5. 对项目发展的影响
此提交标志着 LightX2V 从一个推理执行框架，向一个**包含性能评估与优化生态的完整工具链**演进。它不仅让框架自身能更快定位性能瓶颈，也为社区用户提供了进行定制化性能调优的科学依据。这对于推动轻量级视频生成模型在实际生产环境中的高效、稳定部署具有关键意义，增强了项目的技术深度和用户吸引力。

## 详细提交记录

### [8a97c75](https://github.com/ModelTC/LightX2V/commit/8a97c7591d7252ef491392e83e1eb18617ac9368)

- **作者**: STwangyingrui
- **时间**: 2026-09-29T17:58:09Z
- **提交信息**: feat(benchmarks): add shape-driven operator benchmarks (including SP attention) (#1566)

## Summary

Add shape-driven benchmarks for:

- GEMM, MoE, dense attention, and sparse attention
- Production backend discovery and comparison
- Real QKV replay for sparse attention
- Ulysses and Ring sequence-parallel attention
- Ulysses head-group configuration sweep
- L2/L3 communication diagnostics and bandwidth reporting
- Hardware-specific compute and interconnect efficiency

The benchmark supports both model-derived shapes and synthetic shape
sweeps. Results include backend rankings, recommended configurations,
latency, throughput, and efficiency against user-provided hardware peak
profiles.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2269
- **最后更新**: 2026-09-29T18:40:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

**1. 主要更新类型：** 本次提交属于架构重构（Refactoring），旨在优化系统底层设计。

**2. 关键变更点及其与项目整体方向的关系：** 核心变更为“升级GPU内存模式架构”。这直接针对AIGC视频生成应用中GPU资源消耗大、显存管理复杂的痛点。项目旨在提供高效易用的视频生成工具（如CogVideoX-Fun, Wan-Fun），而此次架构升级旨在通过优化显存管理，提升模型运行的稳定性和资源利用效率，是支撑项目向更高性能、更广适用性方向发展的关键技术改进。

**3. 对项目的影响和潜在意义：**
*   **正面影响：** 预计能提升视频生成任务（尤其是长序列或高分辨率）的稳定性与速度，可能降低对硬件显存的最低要求，使项目对更广泛的用户和硬件环境更友好。
*   **潜在意义：** 为后续支持更复杂模型、更大批量处理或新功能（如交互式编辑）奠定了更坚实的底层架构基础，增强了项目的可持续演进能力。

**4. 值得关注的技术点：** 此次升级的“GPU内存模式架构”是关注重点。它可能涉及动态显存分配、计算与显存优化（如梯度检查点、混合精度）策略的系统性整合，或对现有显存管理流程的重新设计，以实现更精细化的资源控制。

**5. 对项目发展的影响（基于README背景）：** README显示项目聚焦于提供Fun（趣味/便捷）且强大的视频生成模型。此次架构重构虽为底层变更，但直接影响了产品的核心体验——运行的流畅性与可靠性。它确保了项目在追求更先进生成效果的同时，不牺牲易用性和部署灵活性，这符合“Fun”的定位，并有助于吸引更多开发者与用户参与，推动项目生态的健康发展。

## 详细提交记录

### [4b7b640](https://github.com/aigc-apps/VideoX-Fun/commit/4b7b6402a1e0f0406bd6801fb66c0a00bd922621)

- **作者**: Bubbliiiing
- **时间**: 2026-09-29T11:18:17Z
- **提交信息**: Upgrade GPU Memory Mode architecture (#521)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6522
- **最后更新**: 2026-09-30T00:31:44Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 16
- **主要提交者**: Jiading Gai, Copilot, yichengj

## AI分析总结

针对 `flashinfer-ai/flashinfer` 仓库昨日的27次提交，现将其分析整合总结如下：

### 主要更新类型
本次提交主要集中在 **性能优化**、**功能增强** 和 **基础设施与工程化改进** 三大方面。
*   **性能优化**是核心，涉及对MoE（混合专家）模型关键操作（如`expand`/`shrink`内核）、注意力计算（如持久化BatchAttention、DeepSeek-V4 MLA解码）以及针对新硬件架构（如Blackwell SM100/SM103、SM110）的内核进行深度调优与融合。
*   **功能增强**包括：为`SM12x W4A16`融合MoE引入专家并行能力；引入面向Blackwell架构的实验性`DeepGEMM`内核系列；新增针对`Kimi-K3`模型的`NVFP4 SiTU`融合MoE后端；将Prims-TS后端适配到统一的`MoEConfig`/`MoELayer`接口；公开NVFP4量化配置API；新增混合精度（FP8/NVFP4）的FMHA解码支持等。
*   **基础设施与工程化**改进涵盖：为CI流水线添加健壮的重试机制；更新CODEOWNERS以优化代码审查流程；重构测试框架以提升效率；修复文档构建问题；并将版本号提升至`0.7.1`。

### 关键变更点与项目方向
所有变更紧密围绕项目核心使命：**为大规模AI推理（特别是MoE架构模型）提供极致性能的GPU内核库**。
1.  **深化MoE支持**：从优化通用MoE操作（`bgmv`），到支持特定模型（Kimi-K3）的融合后端，再到为`SM12x`架构实现专家并行，全面提升了对万亿参数MoE模型的支持能力。
2.  **拥抱下一代硬件**：前瞻性布局NVIDIA Blackwell架构（SM100/SM103）和SM110 GPU，通过新增内核和针对性微架构调优（如TMEM路由、L2缓存管理），确保项目在新硬件上的性能领先。
3.  **向生产就绪演进**：将NVFP4量化配置从环境变量显式化为公开API，标志着项目从实验性功能向更稳定、易用的生产接口演进。统一的MoE API扩展也体现了模块化和异构集成的设计思路。

### 对项目的影响
*   **性能与竞争力**：对MoE、Attention等关键内核的优化以及新硬件后端的引入，显著提升了FlashInfer在单卡与多卡推理场景下的性能上限，巩固了其在SOTA性能基准中的领先地位。
*   **硬件覆盖与生态**：全面覆盖从SM90到Blackwell（SM100/SM103/SM103a）乃至SM110的多种架构，增强了项目在多样化部署环境中的适用性。对前沿模型（如DeepSeek）的持续集成，强化了其作为关键推理基础设施的生态位。
*   **开发与维护体验**：CI稳定性、文档准确性、测试效率和构建速度（如JIT优化）的改进，提升了项目的可靠性和开发者体验，为其长期健康发展和社区吸引奠定了坚实基础。

### 值得关注的技术点
*   **内存与指令级优化**：在`moe_bgmv_expand`等内核中，运用128-bit协同加载和多通道指令级并行（ILP）来榨取带宽极限，是性能优化的经典手法。
*   **架构感知的内核设计**：为不同硬件和工作负载（如专家并行、特定GQA比率）设计定制化调度方案（如“每计算分片，无令牌交换”的专家并行、基于TMEM的`pair`路由），体现了对GPU硬件特性的深刻理解与利用。
*   **智能测试策略**：测试框架重构采用“配对覆盖”与“完整矩阵”相结合的参数化策略，在保障测试全面性的同时提升了日常构建效率，是工程化实践的典范。
*   **硬件协同调优**：CAKE团队的工作展示了为新架构设计流水线发布、动态PTX调度、PDL早期调度等深度微架构协同技术，是将新硬件性能推向极致的必要手段。

### 总结
这些提交共同推动FlashInfer项目在 **性能深度**、**功能广度** 和 **工程成熟度** 上实现全面跃进。项目正通过持续的性能深潜、对新架构的快速适配以及API与工程体系的不断完善，巩固其在高性能GPU推理内核领域的领先性，为服务下一代大规模模型部署做好准备。

## 详细提交记录

### [47a13de](https://github.com/flashinfer-ai/flashinfer/commit/47a13dea1014b620a72c32a73cf72c4b7568261f)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-29T23:43:50Z
- **提交信息**: bump version to 0.7.1 (#5711)

<!-- .github/pull_request_template.md -->

## 📌 Description

Bump version to 0.7.1 for release.

Prepared from `main` at `60f0bc0f960f9c0cc461a80bac10cf4da23ff8d1`
(includes #4302). The audit baseline is the latest stable release,
`v0.7.0.post1`. This draft changes only `version.txt` and tracks release
preparation through the version-bump PR stage.

## 🔍 Related Issues


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.7.1

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

Validation: `pre-commit run --files version.txt` and `git diff --check`
passed. Hooks were run manually from a task-local installation; hooks
were not installed into the shared checkout, and the all-files checklist
remains unchecked.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Both canonical API listings completed successfully. This version-only PR
has no new tests. GPU, integration, and full-release validation have not
been run as part of this preparation.

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

**API changes review**

API changes since v0.7.0.post1, using `scripts/list_apis.sh` at the
candidate commit above.

The full raw diff is 2,633 lines and exceeds one GitHub body. Part 1 is
below; part 2 is in the linked continuation comment. The split is at a
hunk boundary; no diff lines are omitted. The two file labels identify
the compared revisions.

[API diff continuation — part 2 of
2](https://github.com/flashinfer-ai/flashinfer/pull/5711#issuecomment-5901074495)

```diff
diff -u \
  <(scripts/list_apis.sh -d -p --ref v0.7.0.post1) \
  <(scripts/list_apis.sh -d -p)
--- v0.7.0.post1
+++ main-60f0bc0f9
@@ -22,6 +22,8 @@
     a,
     mask,
     a_global_sf,
+    # Appended last so existing positional construction keeps working.
+    nvfp4_4over6: Optional[NVFP44Over6Config] = _UNSET,
 ):
 class BatchAttention:
     @flashinfer_api
@@ -51,6 +53,9 @@
         use_profiler: bool = False,
     ) -> None:
 
+    @flashinfer_api
+    def prewarm_paged_kv_stride_variant(self, variant: str = "independent") -> None:
+
     @flashinfer_api(trace=batch_attention_run_trace)
     def run(
         self,
@@ -66,511 +71,59 @@
             Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]
         ] = None,
     ) -> Tuple[torch.Tensor, torch.Tensor]:
-class BlockSparseTSWrapper(_BlockSparseWrapperBase):
-    @flashinfer_api(trace=prims_ts_block_sparse_wrapper_trace_dispatch)
-    def run(
-        self,
-        q: torch.Tensor,
-        k: torch.Tensor,
-        v: torch.Tensor,
-        block_indptr: torch.Tensor | None = None,
-        block_indices: torch.Tensor | None = None,
-        *,
-        exact_block_bits: torch.Tensor | None = None,
-        k_summary: torch.Tensor | None = None,
-        v_summary: torch.Tensor | None = None,
-        kv_valid_bits: torch.Tensor | None = None,
-        sm_scale: float | None = None,
-        out: torch.Tensor | None = None,
-    ) -> torch.Tensor:
-
-
-[Global Functions]
-@flashinfer_api(trace=prims_ts_block_sparse_trace_dispatch)
-def block_sparse_attention(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    block_indptr: torch.Tensor | None,
-    block_indices: torch.Tensor | None,
-    q_block_size: int,
-    kv_block_size: int,
-    *,
-    exact_block_bits: torch.Tensor | None = None,
-    k_summary: torch.Tensor | None = None,
-    v_summary: torch.Tensor | None = None,
-    kv_valid_bits: torch.Tensor | None = None,
-    sparse_format: Literal["bsr", "bitmask"] = "bsr",
-    use_proxy_routes: bool = False,
-    mask_type: Literal["dense", "causal"] = "dense",
-    sm_scale: float | None = None,
-    out: torch.Tensor | None = None,
-) -> torch.Tensor:
-class BlockSparsePagedTSWrapper(_BlockSparseWrapperBase):
-    @flashinfer_api(trace=prims_ts_paged_block_sparse_wrapper_trace_dispatch)
-    def run(
-        self,
-        q: torch.Tensor,
-        paged_kv_cache: PagedKVCache,
-        paged_kv_indptr: torch.Tensor,
-        paged_kv_indices: torch.Tensor,
-        seq_lens_kv: torch.Tensor,
-        block_indptr: torch.Tensor,
-        block_indices: torch.Tensor,
-        *,
-        kv_valid_bits: torch.Tensor | None = None,
-        sm_scale: float | None = None,
-        out: torch.Tensor | None = None,
-    ) -> torch.Tensor:
-
-
-@flashinfer_api(trace=prims_ts_paged_block_sparse_trace_dispatch)
-def block_sparse_attention_with_paged_kv_cache(
-    q: torch.Tensor,
-    paged_kv_cache: PagedKVCache,
-    paged_kv_indptr: torch.Tensor,
-    paged_kv_indices: torch.Tensor,
-    block_indptr: torch.Tensor,
-    block_indices: torch.Tensor,
-    q_block_size: int,
-    kv_block_size: int,
-    *,
-    max_seq_len_kv: int,
-    seq_lens_kv: torch.Tensor,
-    kv_valid_bits: torch.Tensor | None = None,
-    mask_type: Literal["dense", "causal"] = "dense",
-    sm_scale: float | None = None,
-    out: torch.Tensor | None = None,
-) -> torch.Tensor:
-class BatchPrefillTSWrapper:
-    @flashinfer_api
-    def __init__(self) -> None:
-
-    @flashinfer_api
-    def plan(
-        self,
-        *,
-        device: int | str | torch.device,
-        batch_size: int,
-        max_seq_len_q: int,
-        max_kv_len: int,
-        num_qo_heads: int,
-        num_kv_heads: int,
-        head_dim: int,
-        q_dtype: torch.dtype,
-        kv_dtype: torch.dtype,
-        out_dtype: Optional[torch.dtype] = None,
-        packed: bool = False,
-        mask_type: Literal["dense", "causal", "variable_window"] = "dense",
-        window_left: int = -1,
-        sm_scale: Optional[float] = None,
-        output_scale: float = 1.0,
-    ) -> None:
-
-    @flashinfer_api
-    def run(
-        self,
-        q: torch.Tensor,
-        k: torch.Tensor,
-        v: torch.Tensor,
-        qo_indptr: Optional[torch.Tensor] = None,
-        kv_indptr: Optional[torch.Tensor] = None,
-        *,
-        variable_window_token_starts: Optional[torch.Tensor] = None,
-        variable_window_token_ends: Optional[torch.Tensor] = None,
-        variable_window_cta_starts: Optional[torch.Tensor] = None,
-        out: Optional[torch.Tensor] = None,
-        scale_softmax_log2: Optional[torch.Tensor] = None,
-        output_scale: Optional[torch.Tensor] = None,
-        validate: bool = True,
-    ) -> torch.Tensor:
-class BatchPrefillPagedTSWrapper:
-    @flashinfer_api
-    def __init__(self, kv_layout: Literal["HND"] = "HND") -> None:
-
-    @flashinfer_api
-    def plan(
-        self,
-        *,
-        device: int | str | torch.device,
-        batch_size: int,
-        max_seq_len_q: int,
-        max_kv_len: int,
-        num_qo_heads: int,
-        num_kv_heads: int,
-        head_dim: int,
-        q_dtype: torch.dtype,
-        kv_dtype: torch.dtype,
-        out_dtype: Optional[torch.dtype] = None,
-        page_size: int = _DEFAULT_PAGED_KV_PAGE_SIZE,
-        mask_type: Literal["dense", "causal"] = "dense",
-        window_left: int = -1,
-        sm_scale: Optional[float] = None,
-        output_scale: float = 1.0,
-        uniform_packed_lengths: bool = False,
-        has_q_offset: bool = True,
-        paged_v_tail_is_zero: bool = False,
-    ) -> None:
-
-    @flashinfer_api
-    def run(
-        self,
-        q: torch.Tensor,
-        k_cache: torch.Tensor,
-        v_cache: torch.Tensor,
-        qo_indptr: torch.Tensor,
-        block_tables: torch.Tensor,
-        seq_lens_kv: torch.Tensor,
-        *,
-        out: Optional[torch.Tensor] = None,
-        scale_softmax_log2: Optional[torch.Tensor] = None,
-        output_scale: Optional[torch.Tensor] = None,
-        validate: bool = True,
-    ) -> torch.Tensor:
-
-
-[Global Functions]
-@flashinfer_api
-def batch_prefill(
-    q: torch.Tensor,
-    k: torch.Tensor,
-    v: torch.Tensor,
-    *,
-    qo_indptr: Optional[torch.Tensor] = None,
-    kv_indptr: Optional[torch.Tensor] = None,
-    mask_type: Literal["dense", "causal", "variable_window"] = "dense",
-    window_left: int = -1,
-    variable_window_token_starts: Optional[torch.Tensor] = None,
-    variable_window_token_ends: Optional[torch.Tensor] = None,
-    sm_scale: Optional[float] = None,
-    output_scale: float = 1.0,
-    out_dtype: Optional[torch.dtype] = None,
-    out: Optional[torch.Tensor] = None,
-) -> torch.Tensor:
-
-
-@flashinfer_api
-def batch_prefill_with_paged_kv_cache(
-    q: torch.Tensor,
-    k_cache: torch.Tensor,
-    v_cache: torch.Tensor,
-    qo_indptr: torch.Tensor,
-    block_tables: torch.Tensor,
-    seq_lens_kv: torch.Tensor,
-    *,
-    page_size: int = _DEFAULT_PAGED_KV_PAGE_SIZE,
-    kv_layout: Literal["HND"] = "HND",
-    mask_type: Literal["dense", "causal"] = "dense",
-    window_left: int = -1,
-    sm_scale: Optional[float] = None,
-    output_scale: float = 1.0,
-    out_dtype: Optional[torch.dtype] = None,
-    out: Optional[torch.Tensor] = None,
-) -> torch.Tensor:
-[Global Functions]
-@flashinfer_api(trace=prims_ts_decode_trace_dispatch)
-def prims_ts_batch_decode_with_kv_cache(
-    query: torch.Tensor,
-    kv_cache: PagedKVCache,
-    workspace_buffer: torch.Tensor,
-    block_tables: torch.Tensor,
-    seq_lens: torch.Tensor,
-    max_seq_len: int,
-    *,
-    seq_len_q: int = 1,
-    qo_indptr: Optional[torch.Tensor] = None,
-    max_seq_len_q: Optional[int] = None,
-    bmm1_scale: Optional[float] = None,
-    bmm2_scale: float = 1.0,
-    out: Optional[torch.Tensor] = None,
-    out_dtype: Optional[torch.dtype] = None,
-    mask_type: Literal["dense", "causal"] = "dense",
-    window_left: int = -1,
-    kv_layout: Literal["HND"] = "HND",
-) -> torch.Tensor:
-class BatchDecodePagedTSWrapper:
-    @flashinfer_api
-    def __init__(self, kv_layout: Literal["HND"] = "HND") -> None:
-
-    @flashinfer_api
-    def plan(
-        self,
-        device: Union[int, str, torch.device],
-        batch_size: int,
-        num_qo_heads: int,
-        num_kv_heads: int,
-        head_dim: int,
-        page_size: int,
-        max_kv_len: int,
-        *,
-        max_seq_len_q: int = 1,
-        packed_query: bool = False,
-        q_data_type: torch.dtype = torch.float16,
-        kv_data_type: Optional[torch.dtype] = None,
-        o_data_type: Optional[torch.dtype] = None,
-        mask_type: Literal["dense", "causal"] = "dense",
-        window_left: int = -1,
-        seq_lens: Optional[Union[Sequence[int], torch.Tensor]] = None,
-        workspace_buffer: Optional[torch.Tensor] = None,
-    ) -> None:
-
-    @flashinfer_api(trace=prims_ts_decode_wrapper_trace_dispatch)
-    def run(
-        self,
-        q: torch.Tensor,
-        paged_kv_cache: PagedKVCache,
-        seq_lens: Optional[torch.Tensor],
-        block_tables: torch.Tensor,
-        *,
-        qo_indptr: Optional[torch.Tensor] = None,
-        bmm1_scale: Optional[float] = None,
-        bmm2_scale: float = 1.0,
-        out: Optional[torch.Tensor] = None,
-        validate: bool = True,
-    ) -> torch.Tensor:
-
-
-@flashinfer_api(trace=attention_ts_decode_trace_dispatch)
-def batch_decode_with_paged_kv_cache(
-    q: torch.Tensor,
-    paged_kv_cache: PagedKVCache,
-    block_tables: torch.Tensor,
-    seq_lens_kv: torch.Tensor,
-    *,
-    seq_len_q: int = 1,
-    qo_indptr: Optional[torch.Tensor] = None,
-    max_seq_len_q: Optional[int] = None,
-    mask_type: Literal["dense", "causal"] = "dense",
-    window_left: int = -1,
-    kv_layout: Literal["HND"] = "HND",
-    bmm1_scale: Optional[float] = None,
-    bmm2_scale: float = 1.0,
-    out: Optional[torch.Tensor] = None,
-    out_dtype: Optional[torch.dtype] = None,
-) -> torch.Tensor:
-[Global Functions]
-@flashinfer_api(trace=prims_ts_decode_mla_trace_dispatch)
-def prims_ts_batch_mla_decode_with_kv_cache(
-    query: torch.Tensor,
-    kv_cache: torch.Tensor,
-    workspace_buffer: torch.Tensor,
-    kv_lora_rank: int,
-    qk_rope_head_dim: int,
-    block_tables: torch.Tensor,
-    seq_lens: torch.Tensor,
-    max_seq_len: int,
-    *,
-    qo_indptr: Optional[torch.Tensor] = None,
-    max_seq_len_q: Optional[int] = None,
-    out: Optional[torch.Tensor] = None,
-    bmm1_scale: float = 1.0,
-    bmm2_scale: float = 1.0,
-    mask_type: Literal["dense", "causal"] = "causal",
-    out_dtype: torch.dtype = torch.bfloat16,
-) -> torch.Tensor:
-class BatchMLADecodePagedTSWrapper:
-    @flashinfer_api
-    def __init__(self) -> None:
-
-    @flashinfer_api
-    def plan(
-        self,
-        device: int | str | torch.device,
-        batch_size: int,
-        num_heads: int,
-        kv_lora_rank: int,
-        qk_rope_head_dim: int,
-        page_size: int,
-        max_kv_len: int,
-        *,
-        max_seq_len_q: int,
-        packed_query: bool,
-        q_data_type: torch.dtype,
-        kv_data_type: torch.dtype,
-        o_data_type: torch.dtype,
-        mask_type: Literal["dense", "causal"] = "causal",
-        workspace_buffer: Optional[torch.Tensor] = None,
-    ) -> None:
-
-    @flashinfer_api(trace=prims_ts_decode_mla_wrapper_trace_dispatch)
-    def run(
-        self,
-        query: torch.Tensor,
-        kv_cache: torch.Tensor,
-        block_tables: torch.Tensor,
-        seq_lens: torch.Tensor,
-        *,
-        qo_indptr: Optional[torch.Tensor] = None,
-        bmm1_scale: float = 1.0,
-        bmm2_scale: float = 1.0,
-        out: Optional[torch.Tensor] = None,
-        validate: bool = True,
-    ) -> torch.Tensor:
-
-
-@flashinfer_api(trace=prims_ts_decode_mla_one_shot_trace_dispatch)
-def batch_mla_decode_with_paged_kv_cache(
-    query: torch.Tensor,
-    kv_cache: torch.Tensor,
-    block_tables: torch.Tensor,
-    seq_lens: torch.Tensor,
-    *,
-    qo_indptr: Optional[torch.Tensor] = None,
-    max_seq_len_q: Optional[int] = None,
-    kv_lora_rank: int = _MLA_LATENT_DIM,
-    qk_rope_head_dim: int = _MLA_ROPE_DIM,
-    mask_type: Literal["dense", "causal"] = "causal",
-    max_kv_len: Optional[int] = None,
-    bmm1_scale: float = 1.0,
-    bmm2_scale: float = 1.0,
-    out: Optional[torch.Tensor] = None,
-    out_dtype: torch.dtype = torch.bfloat16,
-) -> torch.Tensor:
 [Global Functions]
 @flashinfer_api(trace=fp8_paged_mqa_logits_trace)
 def fp8_paged_mqa_logits(
     q: torch.Tensor,
     kv_fused: torch.Tensor,
     weights: torch.Tensor,
-    context_lens: torch.Tensor,
-    block_table: torch.Tensor,
-    max_context_len: int,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    max_seq_len: int,
     *,
     output_dtype: torch.dtype = torch.float32,
     epi_dtype: torch.dtype = torch.float32,
     acc_dtype: torch.dtype = torch.float32,
-    num_epi_subtiles: int = 1,
-    schedule_meta: torch.Tensor = None,
-    out: torch.Tensor = None,
+    schedule_meta: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
 ) -> torch.Tensor:
     q: torch.Tensor,
-    sf_q: torch.Tensor,
+    q_sf: torch.Tensor,
     kv_fused: torch.Tensor,
     weights: torch.Tensor,
-    context_lens: torch.Tensor,
-    block_table: torch.Tensor,
-    max_context_len: int,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    max_seq_len: int,
     sf_vec_size: int = _FP4_SF_VEC_SIZE,
     output_dtype: torch.dtype = torch.bfloat16,
     epi_dtype: torch.dtype = torch.float32,
-    num_epi_subtiles: int = 1,
     is_kv_sf_interleaved: bool = False,
-    schedule_meta: torch.Tensor = None,
-    out: torch.Tensor = None,
+    schedule_meta: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
 ) -> bool:
 @flashinfer_api(trace=fp4_paged_mqa_logits_trace)
 def fp4_paged_mqa_logits(
     q: torch.Tensor,
-    sf_q: torch.Tensor,
+    q_sf: torch.Tensor,
     kv_fused: torch.Tensor,
     weights: torch.Tensor,
-    context_lens: torch.Tensor,
-    block_table: torch.Tensor,
-    max_context_len: int,
+    block_tables: torch.Tensor,
+    seq_lens: torch.Tensor,
+    max_seq_len: int,
     *,
     sf_vec_size: int = _FP4_SF_VEC_SIZE,
     output_dtype: torch.dtype = torch.bfloat16,
     epi_dtype: torch.dtype = torch.float32,
-    num_epi_subtiles: int = 1,
     is_kv_sf_interleaved: bool = False,
-    schedule_meta: torch.Tensor = None,
-    out: torch.Tensor = None,
+    schedule_meta: Optional[torch.Tensor] = None,
+    out: Optional[torch.Tensor] = None,
 ) -> torch.Tensor:
 
 
-    device: torch.device = None,
+    device: Optional[torch.device] = None,
     variants: Tuple[str, ...] = ("fp8", "fp4"),
-    output_dtypes: Tuple[torch.dtype, ...] = None,
-    batch_sizes: Sequence[int] = None,
-) -> None:
-[Global Functions]
-@flashinfer_api
-def get_dcp_spec_workspace_size_bytes(
-    batch_size: int,
-    q_len_per_req: int,
-    num_qo_heads: int,
-    num_split: int = _MAX_NUM_SPLIT,
-    *,
-    head_dim: int = _D128_HEAD_DIM,
-) -> int:
-
-
-@flashinfer_api
-def get_dcp_spec_counter_bytes(
-    batch_size: int,
-    q_len_per_req: int,
-    num_kv_heads: int,
-) -> int:
-
-
-    *,
-    workspace_buffer: torch.Tensor,
-    completion_buffer: Optional[torch.Tensor],
-    device: torch.device,
-    batch_size: int,
-    q_len_per_req: int,
-    num_qo_heads: int,
-    num_kv_heads: int,
-    head_dim: int,
-    num_split: int,
-) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
-
-
-    *,
-    logical_tiles: int,
-    sm_count: int,
-    local_blocks: int,
-) -> int:
-
-
-    *,
-    logical_tiles: int,
-    sm_count: int,
-    local_blocks: int,
-    cp_world: int,
-    head_dim: int = _D128_HEAD_DIM,
-) -> int:
-
-
-
-
-
-
-
-
-    query: torch.Tensor,
-    k_cache: torch.Tensor,
-    v_cache: torch.Tensor,
-    block_tables: torch.Tensor,
-    seq_lens: torch.Tensor,
-    causal_seqlens_kv_global: torch.Tensor,
-    out: torch.Tensor,
-    lse: torch.Tensor,
-    *,
-    batch_size: int,
-    q_len_per_req: int,
-    cp_world: int,
-    cp_rank: int,
-) -> tuple[int, int, str, int]:
-
-
-    query: torch.Tensor,
-    k_cache: torch.Tensor,
-    v_cache: torch.Tensor,
-    workspace_buffer: torch.Tensor,
-    block_tables: torch.Tensor,
-    seq_lens: torch.Tensor,
-    causal_seqlens_kv_global: torch.Tensor,
-    max_local_seq_len: int,
-    bmm1_scale: float,
-    bmm2_scale: float,
-    cp_world: int,
-    cp_rank: int,
-    q_len_per_req: int,
-    out: torch.Tensor,
-    lse: torch.Tensor,
-    completion_buffer: Optional[torch.Tensor],
-    backend: str = "cake",
+    output_dtypes: Optional[Tuple[torch.dtype, ...]] = None,
+    batch_sizes: Optional[Sequence[int]] = None,
 ) -> None:
 class MiniMaxH3Mxfp8PreAttention:
     @flashinfer_api(trace=minimax_h3_mxfp8_pre_attention_trace)
@@ -592,6 +145,70 @@
         debug_q_bf16: Optional[torch.Tensor] = None,
         debug_k_bf16: Optional[torch.Tensor] = None,
     ) -> tuple[torch.Tensor, torch.Tensor]:
+class MiniMaxH3Nvfp4PreAttention:
+    @flashinfer_api(trace=minimax_h3_nvfp4_pre_attention_trace)
+    def run(
+        self,
+        *,
+        x: torch.Tensor,
+        x_norm_weight: torch.Tensor,
+        adaln_scale: torch.Tensor,
+        adaln_shift: torch.Tensor,
+        adaln_index: torch.Tensor,
+        x_global_scale: torch.Tensor,
+        qkv_weight_q: torch.Tensor,
+        qkv_weight_sf: torch.Tensor,
+        w_global_scale: torch.Tensor,
+        q_norm_weight: torch.Tensor,
+        k_norm_weight: torch.Tensor,
+        rope_cos_sin: torch.Tensor,
+        out_global_scale: torch.Tensor,
+        out_q: torch.Tensor,
+        out_sf: torch.Tensor,
+        debug_q_bf16: Optional[torch.Tensor] = None,
+        debug_k_bf16: Optional[torch.Tensor] = None,
+        debug_adaln_bf16: Optional[torch.Tensor] = None,
+    ) -> tuple[torch.Tensor, torch.Tensor]:
+class MiniMaxH3QkvQuantizePack:
+    @flashinfer_api(trace=minimax_h3_qkv_quantize_pack_trace)
+    def run(
+        self,
+        *,
+        q: torch.Tensor,
+        k: torch.Tensor,
+        v: torch.Tensor,
+        out_q: torch.Tensor,
+        out_sf: torch.Tensor,
+        out_global_scale: Optional[torch.Tensor] = None,
+    ) -> tuple[torch.Tensor, torch.Tensor]:
+[Global Functions]
+@flashinfer_api
+def top_k_top_p_sampling_from_probs(
+    probs: torch.Tensor,
+    top_k: Union[int, torch.Tensor],
+    top_p: Union[float, torch.Tensor],
+    *,
+    top_k_max: Optional[int] = None,
+    generator: Optional[torch.Generator] = None,
+    philox_seed: Optional[int] = None,
+    philox_offset: Optional[int] = None,
+    out: Optional[torch.Tensor] = None,
+    renorm_out: Optional[torch.Tensor] = None,
+    workspace: Optional[tuple[torch.Tensor, torch.Tensor, torch.Tensor]] = None,
+    enable_pdl: bool = True,
+) -> torch.Tensor:
+
+
+@flashinfer_api
+def top_k_probs_to_slab(
+    probs: torch.Tensor,
+    top_k: Union[int, torch.Tensor],
+    *,
+    top_k_max: Optional[int] = None,
+    out_vals: Optional[torch.Tensor] = None,
+    out_idx: Optional[torch.Tensor] = None,
+    out_count: Optional[torch.Tensor] = None,
+) -> tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api(trace=cake_vsa_plan_trace)
 def plan_cake_vsa(
@@ -876,6 +493,8 @@
     block_quant_group_size: Optional[int] = None,
     # ===== RMSNorm variant =====
     weight_bias: float = 0.0,
+    *,
+    moe_finalize_backend: Literal["trtllm", "cake"] = "trtllm",
 ) -> torch.Tensor:
 [Global Functions]
 @flashinfer_api
@@ -906,7 +525,29 @@
     cp_rank: int,
     cp_size: int,
     enable_pdl: Optional[bool] = None,
+    out: Optional[tuple[torch.Tensor, torch.Tensor]] = None,
 ) -> tuple[torch.Tensor, torch.Tensor]:
+[Global Functions]
+@flashinfer_api
+def decode_cp_a2a_lse_reduce_create_workspace(
+    max_tokens: int,
+    local_heads: int,
+    cp_size: int,
+    head_dim: int,
+    dtype: torch.dtype,
+    group: Any,
+) -> torch.Tensor:
+
+
+@flashinfer_api(trace=decode_cp_a2a_lse_reduce_trace)
+def decode_cp_a2a_lse_reduce(
+    partial_o: torch.Tensor,
+    partial_lse: torch.Tensor,
+    workspace: torch.Tensor,
+    cp_rank: int,
+    cp_size: int,
+    lse_mode: Literal["base2", "basee"] = "base2",
+) -> torch.Tensor:
 class MixedCommHandler:
     @flashinfer_api
     def checkpoint_prepare(self):
@@ -934,6 +575,44 @@
         enable_pdl: bool = False,
     ) -> torch.Tensor:
 
+class PcieIpcAllGatherWorkspace(_PcieIpcWorkspace):
+    @flashinfer_api(trace=pcie_ipc_all_gather_trace_dispatch)
+    def all_gather(
+        self,
+        inp: torch.Tensor,
+        *,
+        out: Optional[torch.Tensor] = None,
+        config: Optional[PcieIpcAllGatherLaunchConfig] = None,
+    ) -> torch.Tensor:
+
+[Global Functions]
+@flashinfer_api
+def get_pcie_ipc_all_gather_launch_config(
+    world_size: int,
+    shard_numel: int,
+    max_blocks: int = AG_RS_MAX_BLOCKS,
+    element_size: int = 2,
+    ordered_4plus4: bool = False,
+) -> Optional[PcieIpcAllGatherLaunchConfig]:
+class PcieIpcReduceScatterWorkspace(_PcieIpcWorkspace):
+    @flashinfer_api(trace=pcie_ipc_reduce_scatter_trace_dispatch)
+    def reduce_scatter(
+        self,
+        inp: torch.Tensor,
+        *,
+        out: Optional[torch.Tensor] = None,
+        config: Optional[PcieIpcReduceScatterLaunchConfig] = None,
+    ) -> torch.Tensor:
+
+[Global Functions]
+@flashinfer_api
+def get_pcie_ipc_reduce_scatter_launch_config(
+    world_size: int,
+    shard_numel: int,
+    max_blocks: int = AG_RS_MAX_BLOCKS,
+    element_size: int = 2,
+    ordered_4plus4: bool = False,
+) -> Optional[PcieIpcReduceScatterLaunchConfig]:
 [Global Functions]
 @flashinfer_api
 def quantized_all_reduce(
@@ -962,6 +641,8 @@
     ep_size: int,
     max_num_tokens: int,
     eplb_stats_num_experts: int = 0,
+    *,
+    backend: MoeAlltoAllBackend = "trtllm",
 ):
 
 
@@ -990,6 +671,8 @@
     eplb_local_stats: Optional[torch.Tensor] = None,
     enable_rank_mask: bool = False,
     active_rank_mask: Optional[torch.Tensor] = None,
+    *,
+    backend: MoeAlltoAllBackend = "trtllm",
     recv_view_cache: Optional[dict] = None,
 ):
 
@@ -1016,6 +699,7 @@
     enable_pdl: Optional[bool] = None,
     enable_rank_mask: bool = False,
     active_rank_mask: Optional[torch.Tensor] = None,
+    backend: MoeAlltoAllBackend = "trtllm",
 ) -> torch.Tensor:
 
 
@@ -1027,6 +711,8 @@
     ep_rank: int,
     invalid_expert_id: int,
     enable_pdl: Optional[bool] = None,
+    *,
+    backend: MoeAlltoAllBackend = "trtllm",
 ):
 
 
@@ -1037,6 +723,8 @@
     total_dispatch_payload_size_per_token: int,
     combine_payload_size_per_token: int,
     eplb_stats_num_experts: int = 0,
+    *,
+    backend: MoeAlltoAllBackend = "trtllm",
 ):
 
 class MoeAlltoAll:
@@ -1048,6 +736,8 @@
         hidden_size: int,
         extra_payload_bytes_per_token: int = 0,
         eplb_stats_num_experts: int = 0,
+        *,
+        backend: MoeAlltoAllBackend = "trtllm",
     ) -> int:
     @flashinfer_api
     def checkpoint_prepare(self) -> None:
@@ -1093,6 +783,15 @@
         hidden_size: int,
         dtype: torch.dtype,
     ) -> torch.Tensor:
+class UlyssesWorkspace:
+    @flashinfer_api
+    def __init__(
+        self,
+        *,
+        max_elems: int,
+        dtype: torch.dtype,
+        device: Optional[Union[torch.device, str, int]] = None,
+    ):
 class UlyssesCommunicator:
     @flashinfer_api
     def __init__(
@@ -1106,10 +805,49 @@
     ):
 
     @flashinfer_api
-    def scatter_heads(self, x: torch.Tensor) -> torch.Tensor:
+    def create_workspace(self, *, max_elems: Optional[int] = None) -> UlyssesWorkspace:
 
     @flashinfer_api
-    def gather_heads(self, x: torch.Tensor) -> torch.Tensor:
+    def scatter_heads(
+        self,
+        x: torch.Tensor,
+        *,
+        out: Optional[torch.Tensor] = None,
+        workspace: Optional[UlyssesWorkspace] = None,
+    ) -> torch.Tensor:
+
+    @flashinfer_api
+    def scatter_qkv_head_chunk(
+        self,
+        query: torch.Tensor,
+        key: torch.Tensor,
+        value: torch.Tensor,
+        *,
+        head_offset: int,
+        head_count: int,
+        out: Optional[torch.Tensor] = None,
+        workspace: Optional[UlyssesWorkspace] = None,
+    ) -> torch.Tensor:
+
+    @flashinfer_api
+    def gather_heads(
+        self,
+        x: torch.Tensor,
+        *,
+        out: Optional[torch.Tensor] = None,
+        workspace: Optional[UlyssesWorkspace] = None,
+    ) -> torch.Tensor:
+
+    @flashinfer_api
+    def gather_output_head_chunk(
+        self,
+        x: torch.Tensor,
+        *,
+        local_heads: int,
+        head_offset: int,
+        out: torch.Tensor,
+        workspace: Optional[UlyssesWorkspace] = None,
+    ) -> torch.Tensor:
 
 [Global Functions]
 @flashinfer_api
@@ -1138,6 +876,54 @@
     mode: int,
 ) -> None:
 [Global Functions]
+@flashinfer_api
+def pack_ulysses_qkv_head_chunk(
+    query: torch.Tensor,
+    key: torch.Tensor,
+    value: torch.Tensor,
+    *,
+    world_size: int,
+    head_offset: int,
+    head_count: int,
+    out: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+
+
+    received,
+    out,
+    *,
+    world_size,
+    local_heads,
+    head_offset,
+):
+
+
+    received_rank_major,
+    out,
+    *,
+    world_size,
+    local_heads,
+    head_offset,
+) -> None:
+
+
+@flashinfer_api
+def merge_ulysses_output_head_chunk(
+    received: torch.Tensor,
+    *,
+    world_size: int,
+    local_heads: int,
+    head_offset: int,
+    out: torch.Tensor,
+) -> torch.Tensor:
+
+
+    out_rank_major,
+    source,
+    *,
+    world_size,
+) -> None:
+[Global Functions]
 @flashinfer_api(trace=concat_mla_k_trace)
 def concat_mla_k(
     k: torch.Tensor,
@@ -1164,7 +950,90 @@
     batch_offsets_k: Optional[torch.Tensor] = None,
     batch_offsets_v: Optional[torch.Tensor] = None,
     out: Optional[torch.Tensor] = None,
-) -> torch.Tensor:
+    return_lse: bool = False,
+    lse: Optional[torch.Tensor] = None,
+    q_len_per_req: int = 1,
+    window_left: int = -1,
+    sinks: Optional[torch.Tensor] = None,
+) -> Union[torch.Tensor, tuple[torch.Tensor, torch.Tensor]]:
+[Global Functions]
+@flashinfer_api
+def cudnn_chunk_gated_delta_rule(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    g: Optional[torch.Tensor] = None,
+    beta: Optional[torch.Tensor] = None,
+    scale: Optional[float] = None,
+    initial_state: Optional[torch.Tensor] = None,
+    output_final_state: bool = False,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    use_qk_l2norm_in_kernel: bool = False,
+    output: Optional[torch.Tensor] = None,
+    output_state: Optional[torch.Tensor] = None,
+    batch_invariant: bool = False,
+) -> Union[torch.Tensor, tuple[torch.Tensor, torch.Tensor]]:
+
+
+@flashinfer_api
+def cudnn_chunk_gated_delta_product(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    g: Optional[torch.Tensor] = None,
+    beta: Optional[torch.Tensor] = None,
+    num_householder: int = 1,
+    scale: Optional[float] = None,
+    initial_state: Optional[torch.Tensor] = None,
+    output_final_state: bool = False,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    use_qk_l2norm_in_kernel: bool = False,
+    output: Optional[torch.Tensor] = None,
+    output_state: Optional[torch.Tensor] = None,
+    batch_invariant: bool = False,
+) -> Union[torch.Tensor, tuple[torch.Tensor, torch.Tensor]]:
+
+
+@flashinfer_api
+def cudnn_chunk_gated_delta_rule2(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    g: Optional[torch.Tensor] = None,
+    beta: Optional[torch.Tensor] = None,
+    w: Optional[torch.Tensor] = None,
+    scale: Optional[float] = None,
+    initial_state: Optional[torch.Tensor] = None,
+    output_final_state: bool = False,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    use_qk_l2norm_in_kernel: bool = False,
+    output: Optional[torch.Tensor] = None,
+    output_state: Optional[torch.Tensor] = None,
+    batch_invariant: bool = False,
+) -> Union[torch.Tensor, tuple[torch.Tensor, torch.Tensor]]:
+
+
+@flashinfer_api
+def cudnn_recurrent_kda(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    g: torch.Tensor,
+    beta: torch.Tensor,
+    A_log: Optional[torch.Tensor] = None,
+    dt_bias: Optional[torch.Tensor] = None,
+    scale: Optional[float] = None,
+    initial_state: Optional[torch.Tensor] = None,
+    output_final_state: bool = False,
+    use_qk_l2norm_in_kernel: bool = True,
+    use_gate_in_kernel: bool = False,
+    lower_bound: Optional[float] = None,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    beta_is_logit: bool = False,
+    output: Optional[torch.Tensor] = None,
+    output_state: Optional[torch.Tensor] = None,
+    batch_invariant: bool = False,
+) -> tuple[torch.Tensor, Optional[torch.Tensor]]:
 [Global Functions]
 @flashinfer_api(trace=cudnn_batch_prefill_trace)
 def cudnn_batch_prefill_with_kv_cache(
@@ -1195,8 +1064,8 @@
     is_cuda_graph_compatible: bool = False,
     backend: Optional[str] = None,
     o_data_type: Optional[torch.dtype] = None,
+    lse_base: str = "log2",
 ) -> tuple[torch.Tensor, Optional[torch.Tensor]]:
-
 [Global Functions]
 @flashinfer_api(trace=add_rmsnorm_fp4quant_trace_dispatch)
 def add_rmsnorm_fp4quant(
@@ -1433,6 +1302,7 @@
     q_scale: Optional[torch.Tensor] = None,
     k_scale: Optional[torch.Tensor] = None,
     v_scale: Optional[torch.Tensor] = None,
+    backend: str = "cute",
 ) -> Tuple[torch.Tensor, Optional[torch.Tensor]]:
 
 
@@ -1487,12 +1357,13 @@
     q2k_block_nums: Optional[torch.Tensor] = None,
     softmax_scale: Optional[float] = None,
     *,
-    out: torch.Tensor,
-    tma_descriptor_workspace: torch.Tensor,
+    out: Optional[torch.Tensor] = None,
+    tma_descriptor_workspace: Optional[torch.Tensor] = None,
     uniform_block_count: bool = False,
     contiguous_block_indices: bool = False,
     backend: str = "cake",
 ) -> torch.Tensor:
+
 [Global Functions]
 @flashinfer_api
 def single_decode_with_kv_cache_with_jit_module(
@@ -1673,6 +1544,8 @@
     cp_rank: int = 0,
     causal_seqlens_kv_global: Optional[torch.Tensor] = None,
     bf16q_fp8kv_transform_mode: Optional[Literal["k_only", "separate_kv"]] = None,
+    request_order: Optional[torch.Tensor] = None,
+    request_order_plan: Optional[Any] = None,
 ) -> Union[
     torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor], torch.Tensor]
 ]:
@@ -1725,6 +1598,587 @@
     global_override_indptr_cpu: Optional[torch.Tensor] = None,
 ) -> None:
 [Global Functions]
+@flashinfer_api
+def minimax_h3_sm120_varlen_attention_nvfp4(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    cu_seqlens: torch.Tensor,
+    out: Optional[torch.Tensor] = None,
+    *,
+    cu_seqlens_host: Optional[Sequence[int]] = None,
+    softmax_scale: Optional[float] = None,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
+def prepare_minimax_h3_fc1_weight_fp8(
+    fc1_weight: torch.Tensor, chunk_rows: int = 2048
+) -> Tuple[torch.Tensor, torch.Tensor]:
+
+
+    fc1_weight: torch.Tensor, w_global_scale: Scalar
+) -> Tuple[torch.Tensor, torch.Tensor]:
+
+
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    fc1_weight_q: torch.Tensor,
+    fc1_weight_scale: torch.Tensor,
+    workspace_q: torch.Tensor,
+    workspace_scale: torch.Tensor,
+    out: torch.Tensor,
+    eps: float,
+) -> None:
+    x,
+    x_norm_weight,
+    adaln_scale,
+    adaln_shift,
+    adaln_index,
+    fc1_weight_q,
+    fc1_weight_scale,
+    workspace_q,
+    workspace_scale,
+    out,
+    eps,
+) -> None:
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    act_global_scale: torch.Tensor,
+    fc1_weight_q: torch.Tensor,
+    fc1_scale_tiles: torch.Tensor,
+    workspace_q: torch.Tensor,
+    workspace_sf: torch.Tensor,
+    out: torch.Tensor,
+    eps: float,
+    alpha: float,
+) -> None:
+    x,
+    x_norm_weight,
+    adaln_scale,
+    adaln_shift,
+    adaln_index,
+    act_global_scale,
+    fc1_weight_q,
+    fc1_scale_tiles,
+    workspace_q,
+    workspace_sf,
+    out,
+    eps,
+    alpha,
+) -> None:
+@flashinfer_api
+def minimax_h3_fc1_swiglu_fp8(
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    fc1_weight_q: torch.Tensor,
+    fc1_weight_scale: torch.Tensor,
+    *,
+    out: Optional[torch.Tensor] = None,
+    workspace_q: Optional[torch.Tensor] = None,
+    workspace_scale: Optional[torch.Tensor] = None,
+    eps: float = MINIMAX_H3_EPS,
+) -> torch.Tensor:
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    a_global_scale: torch.Tensor,
+    fc1_weight_q: torch.Tensor,
+    fc1_scale_tiles: torch.Tensor,
+    alpha: Scalar,
+    *,
+    out: Optional[torch.Tensor] = None,
+    workspace_q: Optional[torch.Tensor] = None,
+    workspace_sf: Optional[torch.Tensor] = None,
+    eps: float = MINIMAX_H3_EPS,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
+def quantize_minimax_h3_o_weight_fp8(
+    o_weight: torch.Tensor, chunk_rows: int = 1792
+) -> Tuple[torch.Tensor, torch.Tensor]:
+
+
+@flashinfer_api
+def quantize_minimax_h3_o_weight_nvfp4(
+    o_weight: torch.Tensor,
+) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
+@flashinfer_api
+def minimax_h3_fp8_out_proj(
+    attn_out: torch.Tensor,
+    o_weight_q: torch.Tensor,
+    o_weight_scale: torch.Tensor,
+    gate: torch.Tensor,
+    gate_index: torch.Tensor,
+    residual: torch.Tensor,
+    *,
+    out: Optional[torch.Tensor] = None,
+    act_q: Optional[torch.Tensor] = None,
+    act_scale: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+@flashinfer_api
+def minimax_h3_nvfp4_out_proj(
+    attn_out: torch.Tensor,
+    o_weight_q: torch.Tensor,
+    o_weight_sf: torch.Tensor,
+    o_weight_global_scale: Scalar,
+    act_global_scale: torch.Tensor,
+    gate: torch.Tensor,
+    gate_index: torch.Tensor,
+    residual: torch.Tensor,
+    *,
+    out: Optional[torch.Tensor] = None,
+    act_q: Optional[torch.Tensor] = None,
+    act_sf: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api
+def minimax_h3_fp8_pre_attention(
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    qkv_weight_q: torch.Tensor,
+    qkv_weight_scale: torch.Tensor,
+    q_norm_weight: torch.Tensor,
+    k_norm_weight: torch.Tensor,
+    rope_cos_sin: torch.Tensor,
+    *,
+    eps: float = MINIMAX_H3_DEFAULT_EPS,
+    out_mode: str = "bf16",
+    q: Optional[torch.Tensor] = None,
+    k: Optional[torch.Tensor] = None,
+    v: Optional[torch.Tensor] = None,
+    q_sf: Optional[torch.Tensor] = None,
+    k_sf: Optional[torch.Tensor] = None,
+    v_sf: Optional[torch.Tensor] = None,
+    q_descale: Optional[Scalar] = None,
+    k_descale: Optional[Scalar] = None,
+    v_descale: Optional[Scalar] = None,
+    q_global_scale: Optional[Scalar] = None,
+    k_global_scale: Optional[Scalar] = None,
+    v_global_scale: Optional[Scalar] = None,
+    act_q: Optional[torch.Tensor] = None,
+    act_scale: Optional[torch.Tensor] = None,
+) -> MiniMaxH3PreAttentionOutput:
+@flashinfer_api
+def minimax_h3_nvfp4_pre_attention(
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    qkv_weight_q: torch.Tensor,
+    qkv_weight_sf: torch.Tensor,
+    qkv_weight_global_scale: Scalar,
+    act_global_scale: torch.Tensor,
+    q_norm_weight: torch.Tensor,
+    k_norm_weight: torch.Tensor,
+    rope_cos_sin: torch.Tensor,
+    *,
+    eps: float = MINIMAX_H3_DEFAULT_EPS,
+    out_mode: str = "bf16",
+    alpha: Optional[float] = None,
+    q: Optional[torch.Tensor] = None,
+    k: Optional[torch.Tensor] = None,
+    v: Optional[torch.Tensor] = None,
+    q_sf: Optional[torch.Tensor] = None,
+    k_sf: Optional[torch.Tensor] = None,
+    v_sf: Optional[torch.Tensor] = None,
+    q_descale: Optional[Scalar] = None,
+    k_descale: Optional[Scalar] = None,
+    v_descale: Optional[Scalar] = None,
+    q_global_scale: Optional[Scalar] = None,
+    k_global_scale: Optional[Scalar] = None,
+    v_global_scale: Optional[Scalar] = None,
+    act_q: Optional[torch.Tensor] = None,
+    act_sf: Optional[torch.Tensor] = None,
+) -> MiniMaxH3PreAttentionOutput:
+[Global Functions]
+@flashinfer_api
+def minimax_h3_sm120_varlen_attention_fp8(
+    q: torch.Tensor,
+    k: torch.Tensor,
+    v: torch.Tensor,
+    cu_seqlens: torch.Tensor,
+    out: Optional[torch.Tensor] = None,
+    *,
+    cu_seqlens_host: Optional[Sequence[int]] = None,
+    softmax_scale: Optional[float] = None,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api(trace=minimax_h3_bf16_pre_attention_trace)
+def minimax_h3_bf16_pre_attention(
+    x: torch.Tensor,
+    x_norm_weight: torch.Tensor,
+    adaln_scale: torch.Tensor,
+    adaln_shift: torch.Tensor,
+    adaln_index: torch.Tensor,
+    qkv_weight: torch.Tensor,
+    q_norm_weight: torch.Tensor,
+    k_norm_weight: torch.Tensor,
+    rope_cos_sin: torch.Tensor,
+    *,
+    ulysses_degree: int,
+    out: torch.Tensor,
+    eps: float = _EPS,
+) -> torch.Tensor:
+[Global Functions]
+@flashinfer_api(trace=alphamoe_fused_router_trace)
+def alphamoe_fused_router(
+    logits: torch.Tensor,
+    *,
+    top_k: int,
+    block_m: int = 8,
+    has_shared_expert: bool = False,
+    plan: Optional[AlphaMoERoutePlan] = None,
+) -> AlphaMoERoutePlan:
+[Global Functions]
+@flashinfer_api(trace=alphamoe_nvfp4_aligned_moe_trace)
+def alphamoe_nvfp4_aligned_moe(
+    hidden_states: torch.Tensor,
+    hidden_states_scale: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    output1_scale_gate_scalar: torch.Tensor,
+    output1_scale_scalar: torch.Tensor,
+    output2_scale_scalar: torch.Tensor,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    topk_weights: torch.Tensor,
+    out: torch.Tensor,
+    top_k: int,
+    block_m: int = 8,
+    routed_scaling_factor: float = 1.0,
+    w1_scale_prepared: Optional[torch.Tensor] = None,
+    w2_scale_prepared: Optional[torch.Tensor] = None,
+) -> None:
+    topk_ids: torch.Tensor,
+    num_experts: int,
+    block_size: int,
+    initial_out: torch.Tensor,
+    pad_sorted_token_ids: bool = True,
+) -> bool:
+    topk_ids: torch.Tensor,
+    num_experts: int,
+    block_size: int,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    initial_out: torch.Tensor,
+    seeded_accumulator: torch.Tensor,
+    pad_sorted_token_ids: bool,
+) -> None:
+    topk_ids: torch.Tensor,
+    num_experts: int,
+    block_size: int,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    initial_out: torch.Tensor,
+    seeded_accumulator: torch.Tensor,
+    pad_sorted_token_ids: bool,
+) -> None:
+
+
+    topk_ids: torch.Tensor,
+    num_experts: int,
+    block_size: int,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    initial_out: torch.Tensor,
+    seeded_accumulator: torch.Tensor,
+    pad_sorted_token_ids: bool = True,
+) -> None:
+    hidden_states: torch.Tensor,
+    hidden_states_scale: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    output1_scale_gate_scalar: torch.Tensor,
+    output1_scale_scalar: torch.Tensor,
+    output2_scale_scalar: torch.Tensor,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    topk_weights: torch.Tensor,
+    out: torch.Tensor,
+    topk_ids: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    top_k: int,
+    block_m: int,
+    routed_scaling_factor: float,
+    w1_scale_prepared: Optional[torch.Tensor] = None,
+    w2_scale_prepared: Optional[torch.Tensor] = None,
+    w1_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_scale_prepared: Optional[torch.Tensor] = None,
+    w1_scale_prepared_interleaved: Optional[torch.Tensor] = None,
+    w2_data_prepared: Optional[torch.Tensor] = None,
+    w2_data_prepared_k256: Optional[torch.Tensor] = None,
+    w2_scale_prepared_k256: Optional[torch.Tensor] = None,
+    accumulate: bool = True,
+) -> None:
+    hidden_states: torch.Tensor,
+    hidden_states_scale: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    output1_scale_gate_scalar: torch.Tensor,
+    output1_scale_scalar: torch.Tensor,
+    output2_scale_scalar: torch.Tensor,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    topk_weights: torch.Tensor,
+    out: torch.Tensor,
+    topk_ids: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    top_k: int,
+    block_m: int,
+    routed_scaling_factor: float,
+    w1_scale_prepared: Optional[torch.Tensor] = None,
+    w2_scale_prepared: Optional[torch.Tensor] = None,
+    w1_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_scale_prepared: Optional[torch.Tensor] = None,
+    w1_scale_prepared_interleaved: Optional[torch.Tensor] = None,
+    w2_data_prepared: Optional[torch.Tensor] = None,
+    w2_data_prepared_k256: Optional[torch.Tensor] = None,
+    w2_scale_prepared_k256: Optional[torch.Tensor] = None,
+    accumulate: bool = True,
+) -> None:
+
+
+@flashinfer_api(trace=alphamoe_nvfp4_routed_moe_trace)
+def alphamoe_nvfp4_routed_moe(
+    hidden_states: torch.Tensor,
+    hidden_states_scale: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    output1_scale_gate_scalar: torch.Tensor,
+    output1_scale_scalar: torch.Tensor,
+    output2_scale_scalar: torch.Tensor,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    topk_weights: torch.Tensor,
+    out: torch.Tensor,
+    topk_ids: torch.Tensor,
+    cumsum_buffer: torch.Tensor,
+    top_k: int,
+    block_m: int = 8,
+    routed_scaling_factor: float = 1.0,
+    w1_scale_prepared: Optional[torch.Tensor] = None,
+    w2_scale_prepared: Optional[torch.Tensor] = None,
+    w1_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_data_prepared: Optional[torch.Tensor] = None,
+    w1_gate_up_scale_prepared: Optional[torch.Tensor] = None,
+    w1_scale_prepared_interleaved: Optional[torch.Tensor] = None,
+    w2_data_prepared: Optional[torch.Tensor] = None,
+    w2_data_prepared_k256: Optional[torch.Tensor] = None,
+    w2_scale_prepared_k256: Optional[torch.Tensor] = None,
+    accumulate: bool = True,
+) -> torch.Tensor:
+
+
+    topk_ids: torch.Tensor,
+    num_experts: int,
+    block_size: int,
+    initial_out: torch.Tensor,
+    pad_sorted_token_ids: bool = True,
+) -> bool:
+
+
+    hidden_states, gemm1_weights, top_k, block_m
+):
+
+
+    hidden_states,
+    gemm1_weights,
+    topk_ids,
+    out,
+    top_k,
+    block_m,
+):
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+
+    hidden_states,
+    hidden_states_scale,
+    gemm1_weights,
+    gemm1_weights_scale,
+    gemm2_weights,
+    gemm2_weights_scale,
+    output1_scale_gate_scalar,
+    output1_scale_scalar,
+    output2_scale_scalar,
+    topk_weights,
+    out,
+    topk_ids,
+    top_k,
+    routed_scaling_factor,
+    w1_scale_prepared,
+    w1_data_prepared,
+    w2_data_prepared_k256,
+    w2_scale_prepared_k256,
+    accumulate,
+):
+
+
+    hidden_states,
+    hidden_states_scale,
+    gemm1_weights,
+    gemm1_weights_scale,
+    gemm2_weights_scale,
+    topk_ids,
+    out,
+    top_k,
+    block_m,
+    w1_scale_prepared,
+    w2_scale_prepared,
+):
+
+
+    hidden_states,
+    hidden_states_scale,
+    gemm1_weights,
+    gemm1_weights_scale,
+    gemm2_weights_scale,
+    topk_ids,
+    out,
+    top_k,
+    block_m,
+    w1_scale_prepared,
+    w1_data_prepared=None,
+    w1_gate_up_data_prepared=None,
+    w1_gate_up_scale_prepared=None,
+    w1_scale_prepared_interleaved=None,
+    w2_scale_prepared=None,
+    w2_data_prepared=None,
+    w2_data_prepared_k256=None,
+    w2_scale_prepared_k256=None,
+):
+
+
+    hidden_states,
+    hidden_states_scale,
+    gemm1_weights,
+    gemm1_weights_scale,
+    gemm2_weights,
+    gemm2_weights_scale,
+    output1_scale_gate_scalar,
+    output1_scale_scalar,
+    output2_scale_scalar,
+    sorted_token_ids,
+    expert_ids,
+    num_tokens_post_padded,
+    topk_weights,
+    out,
+    topk_ids,
+    cumsum_buffer,
+    top_k,
+    block_m,
+    routed_scaling_factor,
+    w1_scale_prepared,
+    w1_data_prepared=None,
+    w1_gate_up_data_prepared=None,
+    w1_gate_up_scale_prepared=None,
+    w2_scale_prepared=None,
+    w1_scale_prepared_interleaved=None,
+    w2_data_prepared=None,
+    w2_data_prepared_k256=None,
+    w2_scale_prepared_k256=None,
+    accumulate=True,
+):
+
+
+
+
+
+
+
+
+
+
+[Global Functions]
+@flashinfer_api(trace=alphamoe_interleave_gated_weights_trace)
+def alphamoe_interleave_gated_weights(
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+) -> Tuple[torch.Tensor, torch.Tensor]:
+@flashinfer_api(trace=alphamoe_fp8_block_scale_aligned_moe_trace)
+def alphamoe_fp8_block_scale_aligned_moe(
+    hidden_states: torch.Tensor,
+    hidden_states_scale: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    sorted_token_ids: torch.Tensor,
+    expert_ids: torch.Tensor,
+    num_tokens_post_padded: torch.Tensor,
+    topk_weights: torch.Tensor,
+    *,
+    top_k: int,
+    block_m: int = 8,
+    routed_scaling_factor: float = 1.0,
+    out: Optional[torch.Tensor] = None,
+) -> torch.Tensor:
+[Global Functions]
 @flashinfer_api(trace=trtllm_bf16_moe_trace)
 def prims_ts_bf16_moe(
     routing_logits: torch.Tensor,
```



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated the release version from 0.7.0 to 0.7.1. This update contains
no reported changes to product features or behavior. Users should not
expect any new capabilities or visible changes from this version update.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [13122fc](https://github.com/flashinfer-ai/flashinfer/commit/13122fcfc19b259cc031109fd0a614578e85fd2d)

- **作者**: Copilot
- **时间**: 2026-09-29T23:40:09Z
- **提交信息**: ci: add a retry window with capped backoff to cubin downloads (#5256)

<!-- .github/pull_request_template.md -->

## 📌 Description

Nightly release builds were failing when the cubin downloader exhausted
its retry budget during transient NVIDIA Artifactory congestion. This
adds a wall-clock **retry window** to `download_artifacts()`: while the
window is open, a failed artifact keeps re-attempting instead of failing
the whole build the first time `download_file()` runs out of per-call
retries.

**One knob.** `FLASHINFER_CUBIN_RETRY_WINDOW_SECONDS` (default `0` =
today's behavior) is the only new environment variable. A deadline
subsumes an attempt count — the caller says how long to keep trying, and
`download_file()` keeps its own per-call retry budget unchanged — so
there is no separate max-retries knob.

**Backoff, not polling.** The outer loop paces re-entry with the same
capped equal-jitter backoff `download_file()` already uses internally
(`uniform[cap, 2*cap]`, 5 s base, doubling, cap 150 s). The cap is the
point: without it, a long window degrades into a sustained poll of the
endpoint the window exists *because* it is congested.

| retry # | 1 | 2 | 3 | 4 | 5 | 6+ |
|---|---|---|---|---|---|---|
| delay (s) | 5–10 | 10–20 | 20–40 | 40–80 | 80–160 | 150–300 |

A 24-hour window costs roughly **350 requests per artifact**, not ~86
000.

### Changes

- **`flashinfer/artifacts.py`** — read
`FLASHINFER_CUBIN_RETRY_WINDOW_SECONDS`; retry failed artifacts against
a single deadline shared by the whole download, with capped exponential
backoff and jitter. Report *which* artifacts failed (first five, plus a
count) rather than a bare `Failed to download cubins`. Give each pool
thread its own `requests.Session` — `Session` is not thread-safe and the
previous code shared one across threads.
- **`.github/workflows/nightly-release.yml`** — set
`FLASHINFER_CUBIN_RETRY_WINDOW_SECONDS: 86400` on
`build-flashinfer-cubin`.
- **`CLAUDE.md`** — document the variable in the cubin-loader env table.
- **`tests/test_artifacts.py`** — cover the window, the backoff
schedule, the default (no-window) path, env validation, and per-artifact
failure reporting.

## 🔍 Related Issues

Nightly release instability due to cubin download failures under
transient CDN/Artifactory congestion.

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

`pytest tests/test_artifacts.py` — 17 passed. The suite is pure-Python
and needs no GPU.

`test_download_artifacts_backs_off_exponentially_between_retries`
asserts the delay schedule itself (`[5, 10, 20, 40, 80, 150, 150]` with
jitter pinned to zero), not merely that a retry occurs. Verified it
fails against the flat-1 s cadence it replaces.

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

Two things worth a decision rather than a rubber stamp:

1. **`86400` is deliberate, but `ubuntu-latest` caps it at 6 h.**
GitHub-hosted jobs are hard-capped at 6 hours of execution time, so on
the current runner the effective window is 6 h and the build ends in an
opaque runner timeout rather than this code's `Failed to download
cubins: <names>`. We are keeping the 24-hour value anyway: it is the
spec'd budget and it becomes real the moment this job moves to a
self-hosted runner. Noting it here so nobody reads `86400` as a promise
the runner can currently keep.

2. **Non-retryable failures now spin for the whole window.**
`download_file()` returns a bare `False` for every failure mode, so a
genuine 404 (a bad pin, a pruned artifact) is indistinguishable from
congestion and will retry until the window closes. The backoff cap
bounds the cost to ~70 requests over 6 h and the build still fails, but
it turns a one-minute failure into a long one. Teaching
`download_file()` to report *why* it failed would fix this properly;
that is a wider change than this PR, so it is flagged rather than fixed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>
Co-authored-by: aleozlx <4958082+aleozlx@users.noreply.github.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [c3f7334](https://github.com/flashinfer-ai/flashinfer/commit/c3f7334d43072684c25456659551446f8a75120b)

- **作者**: Jiading Gai
- **时间**: 2026-09-29T23:34:14Z
- **提交信息**: perf(moe_bgmv): coalesced 128-bit loads for expand kernel (1.8–3× at batch≥256) (#3542)

## 📌 Description

Adds a faster, memory-coalesced kernel for the MoE BGMV expand op
(`moe_bgmv_expand_sliced`),
gated so it only runs where it's measured to win.

The op is memory-bound (each `(token, expert)` pair reads a `feat_out ×
feat_in` LoRA-B slice).
The new `moe_bgmv_expand_opt_kernel`:
- Loads W in **128-bit `uint4` (8×bf16) chunks** → fully coalesced;
`PASSES` independent loads give ILP.
- No shared-memory W staging / no `__syncthreads` → high occupancy hides
load latency.
- Per-column dot reduced across `feat_in/8` lanes (`__shfl_xor`), one
`atomicAdd` per output column
per pair — same accumulation count and **fp32 accumulate as before (no
downcast)**.

**Optimization Analysis:** the dominant lever is **W-load coalescing**.
Profiling the
baseline showed ~7.6 sectors/request on the W read (vs ~4 for a
fully-coalesced 128-bit load — about
half of each transaction's bytes wasted). The new kernel maps threads so
a warp reads contiguous
16 B (`uint4` = 8×bf16) chunks → ~100% sector efficiency: same bytes
moved, far fewer/wider HBM
transactions. SASS confirms it (rank=32, feat_out=3072): the new
kernel's W reads compile to **4×
`LD.E.128`** (the ILP passes), vs the baseline's single `LD.E.128` mixed
with narrower `LDG.E.64`
for the same data. The ILP, no-smem-staging occupancy, and `__shfl`
reduction are latency-hiding
support — they keep the pipes full once the kernel is bandwidth-bound.
The scaling confirms a
bandwidth win: speedup grows with token count (≈1.0× at tiny batch →
4.09× at large batch), largest
where W-read volume dominates. Both kernels write via `REDG.E.ADD.F32`
(identical fp32 reduction);
output matches within fp32 reduction-order tolerance.

**Gating:** use the new kernel when `feat_in % 8 == 0 && (feat_in <= 32
|| num_pairs >= 256)`; else
keep the existing tiled kernel. The only place the existing kernel is
faster is `feat_in == 64` at
small batch (`num_pairs < 256`), where the shuffle-reduction overhead
isn't amortized — that corner
falls back, so it is a real fallback, not dead code.

**Benchmarks** (real `bgmv_moe_expand` API vs unpatched `main`, H200,
cudaEvent; baseline dispatches
to its own tuned branch per shape). Swept the **full instantiation space
× both dtypes**: rank
{8,16,32,64} × all 24 compiled hidden sizes × tokens {16,512,4096} ×
{bf16, fp16} = **576 points**.
**0 regressions** with the gate (bf16 shown; fp16 within noise of it):

| tokens | min | median | max |
|-------:|----:|-------:|----:|
| 16   | 0.98× (parity, dispatch floor) | 1.03× | 2.05× |
| 512  | 1.07× | 1.98× | 3.71× |
| 4096 | 1.32× | 2.63× | 4.09× |

(Without the gate, 2/576 points regressed to 0.92–0.96× — rank-64,
tokens ≤ 16, bf16; the gate
routes that corner to the original kernel.)

The CUDA optimization was discovered by IFCO, an autonomous CUDA
optimization agent built by AWS,
then adapted to the production sliced `w_ptr` interface.


## 🔍 Related Issues

Builds on the MoE BGMV multi-LoRA kernels added in #3249.

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

`tests/moe/test_bgmv_moe.py` (JIT recompile): `TestBgmvMoeExpand` 48/48,
full suite 123/123. Plus a
96-shape correctness check vs a torch reference (all instantiations,
rel. diff < 2e-2).

## Reviewer Notes

- Like-for-like: new kernel vs the existing
`moe_bgmv_expand_sliced_kernel` (#3249), same API/shapes/GPU.
- `feat_in % 8 == 0` holds for all compiled ranks (8/16/32/64); the gate
threshold is calibrated from
  the 576-point sweep, not guessed.
- Files: `csrc/bgmv_moe/moe_bgmv_impl.cuh` (+83 insertions; original
kernel + ladder kept as fallback).

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved processing speed for MoE BGMV expansion on supported input
shapes.
* Input shapes outside the optimized range continue to use the existing
processing path.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Codex <codex@openai.com>

### [7d4d764](https://github.com/flashinfer-ai/flashinfer/commit/7d4d764fe2df64588d5fdbb74484c404bce63196)

- **作者**: Jiading Gai
- **时间**: 2026-09-29T23:33:52Z
- **提交信息**: feat(moe_bgmv): direct decode fast-path for shrink (1.3-3.8x vs sliced kernel) (#3535)

## 📌 Description

Adds a fused decode fast-path to `moe_bgmv_shrink_sliced`. In the decode
path
(`num_pairs <= decode_threshold`, i.e. small batch), the existing
cp.async-pipelined
sliced kernel is launch-starved: its grid is only
`ceil(num_pairs/PPB) × ceil(feat_out/RANK_TILE) × num_slices` blocks, so
just a handful
of SMs are active, and the shared-memory staging / async-pipeline
overhead is pure cost
because there is no inter-pair reuse to amortize it at small batch.

The new `moe_bgmv_shrink_fused_kernel` maps **one CTA per (pair, rank,
slice)** output
element. Each block strides the full `feat_in` contraction with 128-bit
vectorized loads
(`vec_t`), reduces with a warp shuffle + small block reduction, and
fuses the
`scale + cast` into the single accumulating write. This raises resident
blocks ~`feat_out`-fold
and removes the staging overhead.

## 🔍 Related Issues

N/A

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

Validated via FlashInfer's own `tests/moe/test_bgmv_moe.py` (JIT
recompile of the edited source):

```
tests/moe/test_bgmv_moe.py ............ 147 passed
```

- `TestBgmvMoeShrink` 48/48, `TestBgmvMoeEndToEnd` + edge cases 27/27,
full suite 147/147.
- Batch sizes give `num_pairs ∈ {2, 8, 64}`, exercising both the fused
path (≤32) and the
  pipelined path (64).
- **Added `test_shrink_correctness_multislice`** (`num_slices=2`,
gate_up packing, bf16+fp16)
to cover the kernel's `blockIdx.z` slice path, which the existing
`num_slices=1` tests do
  not exercise — 24/24 pass, `max_diff = 0`.
- `compute-sanitizer` clean on the fused kernel: **memcheck 0 errors,
racecheck 0 hazards,
synccheck 0 errors** (decode / multi-slice / `lora_id=-1` skip /
out-of-bounds-token branches).


## Reviewer Notes

**What the speedup compares.** All numbers are **this PR's
`moe_bgmv_shrink_fused_kernel`
vs. the existing `moe_bgmv_shrink_sliced_kernel` decode instantiation**
(the current
upstream baseline: `RANK_TILE=8, PAIRS_PER_BLOCK=4, NUM_STAGES=3` — the
cp.async-pipelined
kernel selected today when `num_pairs <= decode_threshold`). Both
kernels were compiled from
the same tree and run through the same `bgmv_moe_shrink` API on the same
H200 (SM90), at the
same shape (`feat_in=3072, feat_out=32, bf16, num_pairs=8`), timed
back-to-back. So this is a
like-for-like replacement of one decode kernel by another.

**SASS comparison insights** (control codes decoded with the SM90 layout
— `hi64[44:41]`
stall, `[48:46]` write-barrier, `[57:52]` wait mask; same disassembled
`.cuda.o`):

| | baseline `..._sliced_kernel` (decode) | this PR `..._fused_kernel` |
|---|---|---|
| static instructions | 4008 | **184** (21.8× fewer) |
| total static stall cycles | 11 798 | 410 |
| `LDGSTS` async-copy ops | 12 | **0** |
| smem staging (`STS.128`/`LDS.128`) | present (pipeline round-trip) |
**none** |


### Benchmarking results on H200

Kernel-level evidence at `feat_in=3072, feat_out=32, bf16`, decode
(`num_pairs=8`), on the
production build path (`bgmv_moe_bf16_bf16_bf16`), H200 SM90 — i.e. NOT
the Python/API
dispatch floor:

| metric | baseline (pipelined) | this PR (direct) |  |
|---|---|---|---|
| **kernel duration** (ncu `gpu__time_duration`) | **34.5 µs** | **5.95
µs** | **≈5.8× faster kernel** |
| blocks launched | 8 | 256 | 32× parallelism |
| occupancy limit (smem) | **1 block/SM** | 28 blocks/SM | staging cap
removed |
| SM throughput | 0.87 % | 5.12 % | |
| `LDGSTS` async-copy ops (SASS) | 12 | **0** | |
| static instructions (SASS) | 4008 | **184** | 21.8× fewer |

The mechanism is structural (launch starvation + cp.async-staging
removal) and reproducible
under ncu, not a fragile micro-optimization. The prefill kernel's SASS
is byte-for-byte
identical before/after this change.

### Performance ( `bgmv_moe_shrink` API, H200 SM90)

CUDA-event timed, 30 warmup + 200 iters × 5 reps, median; baseline vs
this PR, same GPU:

| hidden | rank | tokens | baseline µs | this PR µs | speedup |
|-------:|-----:|-------:|------------:|-----------:|--------:|
|   768  |  16  |   4    |    21.4     |    16.0    | **1.34×** |
|  2048  |  16  |  16    |    30.5     |    15.9    | **1.92×** |
|  3072  |  32  |   4    |    38.4     |    16.0    | **2.40×** |
|  4096  |  32  |  16    |    46.3     |    16.9    | **2.73×** |
|  5888  |  32  |   4    |    61.6     |    16.0    | **3.84×** |

Win grows with hidden size. Prefill control (tokens=256, gated →
pipelined kernel): within
noise, no regression. (The ~16 µs API floor is Python dispatch; the
kernel speedup is larger,
as the ncu numbers above show.)

> The core CUDA optimization techniques in this patch were discovered by
IFCO, an autonomous
> CUDA optimization agent built by AWS; the kernel was then re-derived
against the production `w_ptr` table
> interface.


| hot-path global load | mixed | single rolled **`LDG.E.128`** (0x800-B
grid stride) |
| scalar `LDG.E.U16` fallback | — | **0** (`if constexpr`-compiled away)
|

- The baseline spends most of its instruction stream staging `X`/`W`
tiles into shared
memory via `LDGSTS` and reading them back (`LDS.128`) to feed the
pipeline. At decode there
is no inter-pair reuse to amortize that round-trip, so it is pure
latency. The fused kernel
reads global memory straight into registers with 128-bit `LDG.E.128` and
reduces with
`SHFL` — eliminating all `LDGSTS`/`STS`/`LDS` and 21.8× of the static
instructions.
- The disassembly confirms the contraction is **fully 128-bit
vectorized** (one `LDG.E.128`
loop, no scalar `LDG.E.U16` path), and ncu reports 9.78 sectors/request
— consistent with
  128-bit loads, not a scalar bf16 contraction.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a faster MoE BGMV shrink execution path for supported hardware
and input sizes. Other configurations continue to use the existing path.
* **Tests**
* Added coverage for multi-slice shrink computations across token
counts, hidden sizes, ranks, and data types.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Codex <codex@openai.com>

### [60f0bc0](https://github.com/flashinfer-ai/flashinfer/commit/60f0bc0f960f9c0cc461a80bac10cf4da23ff8d1)

- **作者**: yichengj
- **时间**: 2026-09-29T23:24:11Z
- **提交信息**: feat(moe): expert parallelism for the SM12x W4A16 fused MoE (#4302)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds expert parallelism to the SM120/SM121 b12x W4A16 fused MoE. The
design keeps all communication in the caller: every rank receives the
full batch, computes only the experts it holds, and the caller sums the
per-rank partial outputs. No tokens are exchanged between ranks.

Changes:

- Threads `expert_map`, which describes the experts a rank holds, from
the Python APIs down to the kernels, which already supported it.
- The trace reference applies `expert_map`, so traced EP calls replay
against a correct baseline.

Public API and behavior changes:

- `b12x_fused_moe` and `B12xMoEWrapper` accept an optional `expert_map`.
- The unified `B12xW4A16Runner` no longer rejects expert parallelism.

## 🔍 Related Issues

#4223 (item 5). Builds on #4255 (merged).

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

- Added `tests/moe/test_b12x_w4a16_ep.py` (23 cases): simulated
multi-rank runs checked against the full-model output, plus expert-map
validation.
- Extended the unified-API and trace tests with the same EP coverage.
- Verified on two GPUs (2x RTX Pro 6000): results match a single-GPU run
over all experts.
- The existing W4A16 MoE suite (142 cases) passes unchanged on SM121.

## Reviewer Notes

- The design and the expert-map semantics follow upstream b12x. Only the
API surface is FlashInfer-specific, since upstream's EP entry points
build on weight-preparation classes that #4255 did not port.
- Expert placement travels per call rather than per workspace. The
internal workspace cache keys on expert counts only, which stays correct
because buffer geometry depends only on the counts.
- NVFP4 continues to reject expert parallelism, since its backend
indexes per-expert buffers by global top-k ids.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added expert-parallel execution for B12x W4A16 MoE with configurable
global-to-local expert mapping.
* Added contiguous expert sharding, partial-output aggregation, and
support for unrouted experts.
  * Extended tracing and reference execution to support expert maps.

* **Bug Fixes**
* Added validation for invalid maps, shard ranges, device placement, and
routing-map changes during execution.

* **Tests**
* Added coverage for routing, sharding, validation, CUDA graphs,
tracing, and output conformance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [0ee987a](https://github.com/flashinfer-ai/flashinfer/commit/0ee987a6bb67883ca64cdee52f2f908eb882fecc)

- **作者**: eigen
- **时间**: 2026-09-29T23:12:23Z
- **提交信息**: feat(cake_deepgemm): add generated DeepGEMM-family kernels for SM100a/SM103a (sparse MQA indexer, routing gate, mHC, MoE, FP8/FP4 GEMM) (#5523)

## Summary

This PR adds an experimental package of Blackwell kernels and Python
entry points generated from a typed kernel-schedule IR, for **SM100a
(B200, 148 SMs) and SM103a (GB300, 152 SMs)**. It ports the DeepGEMM
Blackwell family end to end rather than wrapping the DeepGEMM JIT:

| Family | Package | Generated source files (sm_100a / sm_103a) |
|---|---|---:|
| Sparse MXFP4/MXFP8 MQA logits indexer (contiguous + paged) |
`flashinfer.experimental.deepgemm_sparse_mqa` | 24 / 24 |
| Dense FP4/FP8 MQA lightning-indexer logits (scheduled, fused cleanup)
| `flashinfer.experimental.deepgemm_dense_mqa` | 19 / 19 |
| Fused routing gate | `flashinfer.experimental.deepgemm_mega_gate` | 26
/ 26 |
| Fused mHC (manifold hyper-connection) |
`flashinfer.experimental.deepgemm_mega_mhc` | 24 / 24 |
| Mixture-of-experts, source schedule (dispatch + two projections +
SwiGLU + shared experts + combine, prepared and mutable execution) |
`flashinfer.experimental.source_mega_moe` | 20 / 20 |
| Mixture-of-experts, v3 composed schedule (2-CTA, grouped L1/L2 with
fused scale-factor fence) | `flashinfer.experimental.mega_moe_v3` | 22 /
22 |
| FP8 1D1D GEMM (forward + wgrad, PTX source export) |
`flashinfer.experimental.deepgemm_fp8_gemm` | 4 / 4 |
| Mixed FP8 x FP4 GEMM | `flashinfer.experimental.deepgemm_mixed_gemm` |
24 / 24 |
| Native FP4 GEMM | `flashinfer.experimental.deepgemm_fp4_gemm` | 20 /
20 |
| FP4 K-grouped GEMM (accumulate + non-accumulate) |
`flashinfer.experimental.deepgemm_kgroup_gemm` | 24 / 24 |
| FP8 batched per-head projection GEMM |
`flashinfer.experimental.deepgemm_batched_gemm` | 12 / 12 |

Each family ships the generated CUDA sources per architecture
(`csrc/experimental/<family>/generated/sm_100a/` and `.../sm_103a/`),
TVM-FFI launch bindings, one JSON catalog of physical routes with an
`arches` section per architecture (`{"schema": "<family>.v2", "arches":
{"sm_100a": {...}, "sm_103a": {...}}}`), a small runtime module, a
top-level convenience module (`flashinfer/<family>.py`), an example
under `examples/experimental/`, and correctness tests under
`tests/experimental/`. The runtime selects the catalog section from the
device's compute capability (10.0 -> `sm_100a`, 10.3 -> `sm_103a`) and
compiles programs through `gen_jit_spec` with the exact `sm100a` /
`sm103a` flags (`use_fast_math=False`); every route carries the SM count
it was generated for (148 or 152) and entry points raise on any other
device. Nothing outside the new paths is modified except one line in
`.pre-commit-config.yaml` that excludes the generated CUDA directories
from `clang-format`, the same treatment as the other generated kernel
directories.

Every one of the 118 model rows of the source schedules is faster than
native DeepGEMM `39d8c4ca` on both architectures (native/source above
1.0x on all 118 rows on B200, minimum 1.0019x, and on all 118 rows on
GB300, minimum 1.0035x; geometric means 1.2427x and 1.2513x; the per-row
list is under Validation, "Both").

#4564 (the earlier stand-alone FP8 batch backend) is closed in favour of
this package, which regenerates that family from the current schedules
together with the ten other families.

## What changed in this revision

- `mega_moe_v3` (composed two-CTA MoE: dispatch + grouped L1 / SwiGLU /
L2 + combine, this revision), the fp4 T = 1 program at HIDDEN 5120 (one
of the ten rows; the two self-cleaning fp4 T = 1 programs are the only
ones that change, the other eighteen MoE v3 programs are
byte-identical): with a single token the six routing pairs make the
expert histogram and the pool prefix scan trivially recomputable by
every CTA, so the start-up chain grid-wide histogram -> grid sync ->
CTA-0 serial prefix scan -> second grid sync (about 7 us before the
first scheduled task on the per-phase traces of both architectures) is
folded into every CTA: each CTA histograms every pair into shared
memory, runs the prefix scan itself and orders its own token pulls,
scheduler, loaders and epilogues behind one CTA-wide named barrier; CTA
0 alone publishes the host-visible expert counts and tile lists, and the
per-expert row / scale-block offsets are written identically by every
CTA. Pool rows, claims, metadata and the block-readiness protocol are
unchanged and the two grid-sync words are left untouched by this
program; every program with more than one token and the other ten
families are unchanged (generated-CUDA identity check at 148 and 152
SMs: 18/20 MoE programs byte-identical, only the two self-cleaning fp4 T
= 1 programs differ). The output is bitwise identical on every row.
Paired tree A/B on the cohort launcher (previous revision vs this one,
same GPU, three ABBA rounds per architecture, CUPTI cold-L2 medians):
the fp4 T = 1 MoE row 45.72 -> 42.82 us on B200 (+6.78 %, faster in 3/3
rounds) and 41.50 -> 38.92 us on GB300 (+6.62 %, 3/3), output bitwise
identical to native DeepGEMM in every round; per-phase lm.timestamp
traces of both revisions put the first scheduled task at 9.3 / 9.6 us
(B200 / GB300) before the change and at 6.2 / 6.1 us after it (the two
dispatch grid syncs and the CTA-0 serial scan wait leave the critical
path; the folded per-CTA histogram + scan costs 2.5 us). Native/source
on the final tree (criterion-2 cohort spreads, six readings per row on
one (B200) and two (GB300) GPUs per architecture): fp4 T = 1 MoE B200
1.4577x (previous revision 1.3895x) / GB300 1.4744x (previous revision
1.3555x). Exported program vs. source route (3 % budget): B200 10/10
rows within budget (min 0.9964x), GB300 10/10 (min 0.9854x).
- `mega_moe_v3` (composed two-CTA MoE: dispatch + grouped L1 / SwiGLU /
L2 + combine, previous revision `eb0fd172`), the fp4 T = 1 program at
HIDDEN 5120 (one of the ten rows; the four other model-row programs per
architecture are re-rendered with identical device code and differ only
in their program identifier, and the six smoke, registry and canonical
programs are untouched): a dispatch warp that pulls one token's
activation row through registers issues all ten 512-byte vector loads of
its lane slice before the ten stores, and loads both scale-factor words
before storing them, so the loads overlap in flight and the row is
published to the block-readiness protocol one load latency after it
starts instead of ten; previously each 512-byte step loaded and stored
before the next load issued. The bulk-copy dispatch path (`num_tokens *
top_k > 256`) and the other ten families are unchanged (generated-CUDA
identity check at 148 and 152 SMs: 16/20 MoE programs byte-identical,
only the four fp4 T = 1 programs differ). The output is bitwise
identical on every row. Paired tree A/B on the cohort launcher (previous
revision vs this one, same GPU, three ABBA rounds per architecture,
CUPTI cold-L2 medians): the fp4 T = 1 MoE row 50.09 -> 45.70 us on B200
(+9.61 %, faster in 3/3 rounds) and 46.18 -> 42.29 us on GB300 (+9.21 %,
3/3), output bitwise identical to native DeepGEMM in every round; the
knob-level A/B of the same change on the isolated kernel (five ABBA
repeats, every arm bitwise on first launch and on graph replay) reads
-5.89 us on B200 and -5.82 us on GB300. Native/source on the final tree
(criterion-2 cohort spreads, six readings per row on one (B200) and two
(GB300) GPUs per architecture): fp4 T = 1 MoE B200 1.3895x (previous
revision 1.2555x) / GB300 1.3555x (previous revision 1.2264x). Exported
program vs. source route (3 % budget): B200 10/10 rows within budget
(min 0.9999x), GB300 10/10 (min 0.9862x).
- `deepgemm_dense_mqa` (dense FP4/FP8 MQA lightning-indexer, previous
revision `9fcc3668`), the FP4 program and the FP8 two-launch and
fused-Q128 programs (seventeen of the twenty rows; the three FP8
single-query rows use the fused-Q1 program, which is PTX-identical to
the previous revision): the math warps issue the TMEM accumulator loads
of Q rows 0-1 together, wait once, issue rows 2-3 behind them so their
TMEM reads overlap the first pair's weighted sums, and release the TMEM
stage as soon as the second pair has landed, ahead of that pair's sums
and logits stores; previously each of the four rows was loaded with its
own per-chunk waits and the stage was released only after the fourth
row's read. The other ten families are unchanged (generated-CUDA
identity check at 148 and 152 SMs: 46/46 non-indexer programs
byte-identical, the fused-Q1 programs PTX-identical). The output is
bitwise identical on every row. Cold-L2 CUPTI spreads of the twenty
indexer rows, previous revision vs this one: on B200 (6 readings on 2
GPUs) 4 of the twenty rows read faster outside both ranges
(fp4-q128-k131072 +1.0 %, fp8-q128-k4096 +1.0 %, fp8-q128-k32768 +2.2 %,
fp8-q128-k131072 +4.0 %), none slower outside both ranges,
fp4-q1-k131072 -1.6 %, fp4-q16-k1048576 -1.6 % overlapping; every
native/source reading stays above 1.0; on GB300 (8 readings on 4 GPUs) 5
of the twenty rows read faster outside both ranges (fp4-q1-k4096 +2.3 %,
fp4-q128-k131072 +0.4 %, fp8-q1-k4096 +1.5 %, fp8-q128-k4096 +1.6 %,
fp8-q128-k131072 +3.9 %), none slower outside both ranges,
fp4-q128-k32768 -1.5 % overlapping; every native/source reading stays
above 1.0. The paired old/new tree A/B (3 legs, 2 completed ABBA rounds
each, launcher medians that include the host gap between the two
launches of the fp8 rows) agreed in direction on the long fp8 q128 rows.
Native/source on the final tree (criterion-2 cohort spreads, six (B200)
/ eight (GB300) readings per row on two (B200) and four (GB300) GPUs per
architecture): dense indexer B200 1.1867x-16.4658x / GB300
1.1848x-16.3857x (twenty rows). Exported program vs. source route (3 %
budget): B200 20/20 rows within budget (min 0.9914x), GB300 20/20 (min
0.9853x).
- `deepgemm_mega_gate` (routing gate, previous revision `6e89f6a7`), the
single-CTA routes (M = 3, 16, 128, 512 and the two M = 16 variants) and
the two-CTA `cta_group::2` routes (M = 1024, 2048, 4096, 8192): the TMA
producer warp starts the first fill ahead of the TMEM-allocation
rendezvous. The prologue publishes the mbarrier initialisation before
`tcgen05.alloc` and replaces the final full-CTA rendezvous by a named
barrier of the eleven TMEM-consuming warps; the producer never reads
TMEM, so it only needs the initialised barriers (its own and the peer
CTA's on the two-CTA routes, where the ordered cluster publication also
makes the schedule's own setup `cluster_sync` redundant). The M = 1
cluster-8 split-K reduction route keeps the canonical prologue
(byte-identical CUDA); the other ten families are unchanged
(generated-CUDA identity check at 148 and 152 SMs, 60/60 programs
identical). The output is bitwise identical on every row. Paired old/new
tree A/B (three ABBA rounds per leg, separate process per tree per
round): on B200 the changed routes read m3 +0.0/+0.4 %, m1024 +3.2/+3.0
%, m2048 +2.7/+2.5 %, m8192 +1.2/+1.3 % kernel time vs the previous
revision and no gate row lost more than 0.19 %; on GB300 the changed
routes read m3 +0.4/+0.4 %, m1024 +3.4/+3.4 %, m2048 +2.7/+2.9 %, m8192
+1.4/+1.4 % kernel time vs the previous revision and no gate row lost
more than 0.35 %. Native/source on the final tree (criterion-2 cohort
spreads, 8 readings per row on two (B200) and four (GB300) GPUs per
architecture): routing gate B200 1.0226x-1.1473x / GB300 1.0198x-1.1110x
(eleven rows). Exported program vs. source route (3 % budget): B200
11/11 rows within budget (min 0.9815x), GB300 11/11 (min 0.9849x).
- `deepgemm_sparse_mqa` (sparse MQA indexer, previous revision
`a8f45c78`), the ten paged MXFP4/MXFP8 rows (Q = 512, K in {4096, 8192,
32768, 131072, 1048576}): the logits kernel runs its non-math warp roles
(copy, metadata, scheduler) at 40 registers so the math warps keep the
register budget; the metadata kernel probes each request's start with a
whole warp in parallel instead of one thread, builds the paged schedule
in two sub-batches so the second half's block-table loads overlap the
first half's records, and resolves the block-table records per chunk of
two pairs with both pairs' loads in flight before their stores (eight
pairs at once spilled at the 64-register cap; chunks of four lost on
small block tables). The contiguous programs are unchanged: the
contiguous logits programs are byte-identical CUDA and the contiguous
metadata programs compile to identical PTX (a trace-time constant that
the compiler folds). The logits output is bitwise identical; the
metadata bytes keep their documented claim-order nondeterminism. Paired
tree A/B legs against the previous revision on the ten paged rows (three
ABBA rounds per leg, launcher medians of the metadata + logits launch
pair; the r40 register split, the m2m3 metadata levers and the m1c2
pair-loop chunking summed): B200 -0.4..+2.4 % kernel time with 9/10 rows
faster (MXFP4 K = 8192 -0.4 %, where the register split costs 1.2 % and
the metadata levers recover 0.8 %), GB300 -0.2..+2.4 % with 9/10 rows
faster (MXFP8 K = 8192 -0.2 %); the two slower rows stay well above
native (native/source tables below). Native/source on the final tree
(criterion-2 cohort spreads, 8 readings per row on 3 (B200) / 4 (GB300)
GPUs per architecture): paged MXFP4 B200 1.0366x-1.1093x / GB300
1.0396x-1.1295x, paged MXFP8 B200 1.0724x-1.1433x / GB300
1.0549x-1.1140x. Exported program vs. source route (3 % budget): B200
20/20 rows within budget (min 0.9926x), GB300 20/20 (min 0.9840x).
- `deepgemm_mega_mhc` (fused mHC, previous revision `a8f45c78`), the
16-split shifted program that also writes the scale-factor output (the T
= 1025 and T = 4096 extra-layout rows): the Post worker publishes its
TMEM atoms to the mix warp-group in pairs (one barrier arrive per two
atoms) instead of one at a time; the other eleven programs per
architecture are byte-identical to the previous revision (generated-CUDA
identity check at 148 and 152 SMs). The output is unchanged. The paired
tree A/B of the batched TMEM publish against the previous revision
(three ABBA rounds, launcher medians) reads +1.18 % / +0.67 % kernel
time on the T = 1025 / T = 4096 extra-shifted rows on B200 and +0.97 % /
+0.54 % on GB300, a GAIN verdict in every round (all rounds agree in
direction and clear their half-spreads). Native/source on the final
tree: B200 1.0442x-1.0730x / GB300 1.0606x-1.0787x (T = 1025 / T = 4096
extra-shifted). Exported program vs. source route (3 % budget): B200
24/24 rows within budget (min 0.9719x), GB300 24/24 (min 0.9761x).
- `deepgemm_dense_mqa` (dense FP4/FP8 MQA lightning-indexer, previous
revision `66370251`, new family in that revision): the DeepSeek-V3.2
dense indexer (`logits[q, k] = sum_h relu(Q[q,h] . KV[k]) * w[q,h]`
inside each query's `[start, end)` window, `-inf` elsewhere) for packed
E2M1 inputs with UE8M0 scales and for E4M3 inputs with one FP32 scale
per KV token, 32 heads and D = 128, at the twenty scheduled model rows
(Q in {1, 16, 128} x K in {4096, 32768, 131072} and Q = 16 x K =
1048576, both precisions). Every route generates the DeepGEMM-compatible
schedule metadata (per-SM work headers, per-query-block spans) and
consumes it in the same submission: 16 routes per architecture are a
metadata program followed by the fused logits/cleanup program, and 4 FP8
routes (the single-query rows and Q = 128 x K = 4096) produce the
metadata inside the logits launch; 11 generated programs per
architecture. The exported schedules are the current source tree's: the
FP8 kernel is launched with programmatic dependent launch behind its
metadata producer, both kernels fill the uncovered logits columns with
`cp.async.bulk` stores of a `-inf` shared-memory tile instead of
per-thread stores, and the FP8 cleaner drains only the shared-memory
reads of its bulk groups before reusing the tile. Exported program vs.
source route (3 % budget; eight independently captured CUDA graph
instances per arm replayed round-robin, see the protocol note): B200
20/20 rows within budget (min 0.9872x), GB300 20/20 (min 0.9786x);
exported outputs are bitwise equal to the source route and the metadata
is bitwise equal to native DeepGEMM's on every row (three poisoned
replays per arm). Source route vs. native DeepGEMM on these twenty rows
(three-round cohort spreads, four GPUs per architecture, eight readings
per row): B200 1.1826x-16.4023x (min reading 1.1316x), GB300
1.2028x-16.3429x (min reading 1.1643x).
- Export-gate protocol note. The first dense legs captured one CUDA
graph per arm. Under the one-instance protocol the FP8 Q1/K32768
(fused-metadata single launch) row on B200 first read 0.9600x (2.304 vs
2.400 us) and 1.0000x on one disclosed re-measure; under the
eight-instance protocol described below the final B200 leg reads it at
1.0412x (2.400 vs 2.305 us). Under the one-instance protocol the FP4
Q1/K4096 (metadata + logits) row on GB300 read 0.9676x (5.728 vs 5.920
us) in two full legs with identical medians; under the eight-instance
protocol described below the final GB300 leg reads it at 0.9786x (5.856
vs 5.984 us). Per-stage paired eager timings of the two arms were
identical on every probed row and stage (1.0000x), their SASS and
resource usage identical, and the driver-API graph node parameters
(grid, block, dynamic shared memory), function attributes, launch
attributes and programmatic edges identical. A probe that captured the
same callable twice into two graphs measured route spans up to 14 x 32
ns ticks apart (5.888 vs 6.272 us on GB300, 5.920 vs 6.208 us on B200),
each instance stable to one tick across replays and deterministic per
process, so a one-instance-per-arm comparison reads an arm-independent
draw as an arm difference. The gate therefore captures eight independent
graph instances per arm and replays them round-robin, one instance per
reportable launch (PERFORMANCE graph_instances_per_arm = 8; the 3 %
budget, the fixed 4000 + 2000 launches per arm and group, three groups
and every other setting are unchanged); both final legs ran under that
protocol and the one-instance receipts are retained beside the final
receipts.
- `deepgemm_mega_gate` (routing gate, previous revision `8b750291`), the
M = 4096 row: the route that serves 4096 tokens (CTA pairs, split-K 2,
two token tiles per worker) now moves two 64-wide k-steps per pipeline
stage (BK 128: 5 stages of 38 KB instead of 11 stages of 19 KB, 218112
-> 198656 bytes of shared memory), which halves the ring handshakes and
TMA issues of its 40-k-step stream; the K16 MMA order is unchanged and
the scores are bitwise identical. The other ten routing-gate programs
are byte-identical to the previous revision at 148 and 152 SMs
(generated-CUDA identity check). Paired old/new kernel time (three ABBA
rounds, CUPTI medians, cold L2): B200 25.344 -> 25.088 us (old/new
1.0102, 3/3 rounds new faster); GB300 23.489 -> 23.328 us (old/new
1.0069, 3/3 rounds new faster). Native/source on the final tree
(three-round cohort spreads, native arm in the same graph replay): B200
1.0127x (9 readings on 1 GPU, min 1.0115x, source 25.12 us vs native
25.44 us); GB300 1.0164x (9 readings on 2 GPUs, min 1.0151x, source
23.39 us vs native 23.81 us). The other large-M routing-gate rows keep
BK 64: the merge read 0.5-2.2 % slower on the one-tile split-2 (M =
2048) and two-tile split-1 (M = 8192) routes on both architectures.
- `deepgemm_sparse_mqa` (sparse MQA indexer, previous revision
`603af178`), the MXFP8 rows (both layouts) and the paged MXFP4 rows: the
per-split metadata records (16-byte headers and 8-byte block infos)
leave the KV ring for their own ring that runs ahead of it (15 stages
for MXFP8 whose KV ring has 3, 7 for paged MXFP4 whose KV ring has 5, at
the shared-memory cap), released by the math warps through a new
`metaempty` barrier right after they read a split's metadata; the copy
warps wait for the KV slot themselves. The 3-stage MXFP8 ring could not
hide the metadata landing latency (480-704 ns per split measured with
globaltimer probes, against a 510-704 ns ring hop). Contiguous MXFP4
keeps the previous program byte for byte (its 5-stage ring already hides
the latency and the separate ring cost 3.5-7 % there). The logits output
is bitwise identical. Paired old/new kernel time (three ABBA rounds,
CUPTI medians, cold L2): B200 mxfp8-contiguous-k1048576 1.032x
(native/source 1.013x -> 1.043x), mxfp8-contiguous-k131072 1.135x
(native/source 1.014x -> 1.155x), mxfp8-contiguous-k32768 1.075x
(native/source 1.025x -> 1.108x), mxfp8-contiguous-k4096 1.060x
(native/source 1.067x -> 1.139x), mxfp8-contiguous-k8192 1.082x
(native/source 1.032x -> 1.116x), mxfp8-paged-k1048576 1.039x
(native/source 1.088x -> 1.131x), mxfp8-paged-k131072 1.044x
(native/source 1.059x -> 1.106x), mxfp8-paged-k32768 1.056x
(native/source 1.041x -> 1.099x), mxfp8-paged-k4096 1.034x
(native/source 1.035x -> 1.069x), mxfp8-paged-k8192 1.060x
(native/source 1.022x -> 1.083x), mxfp4-paged-k1048576 1.000x
(native/source 1.089x -> 1.089x), mxfp4-paged-k131072 1.002x
(native/source 1.026x -> 1.027x), mxfp4-paged-k32768 1.009x
(native/source 1.039x -> 1.048x), mxfp4-paged-k4096 0.997x
(native/source 1.077x -> 1.074x), mxfp4-paged-k8192 1.017x
(native/source 1.043x -> 1.060x); GB300 mxfp8-contiguous-k1048576 1.016x
(native/source 1.006x -> 1.022x), mxfp8-contiguous-k131072 1.192x
(native/source 1.023x -> 1.221x), mxfp8-contiguous-k32768 1.108x
(native/source 1.025x -> 1.133x), mxfp8-contiguous-k4096 1.091x
(native/source 1.081x -> 1.180x), mxfp8-contiguous-k8192 1.125x
(native/source 1.053x -> 1.185x), mxfp8-paged-k1048576 1.030x
(native/source 1.064x -> 1.096x), mxfp8-paged-k131072 1.030x
(native/source 1.020x -> 1.050x), mxfp8-paged-k32768 1.054x
(native/source 1.054x -> 1.111x), mxfp8-paged-k4096 1.032x
(native/source 1.037x -> 1.070x), mxfp8-paged-k8192 1.053x
(native/source 1.020x -> 1.074x), mxfp4-paged-k1048576 1.007x
(native/source 1.094x -> 1.102x), mxfp4-paged-k131072 1.007x
(native/source 1.026x -> 1.033x), mxfp4-paged-k32768 1.012x
(native/source 1.046x -> 1.058x), mxfp4-paged-k4096 0.996x
(native/source 1.078x -> 1.074x), mxfp4-paged-k8192 1.008x
(native/source 1.042x -> 1.051x).
- `source_mega_moe` (fused single-kernel MoE, previous revision
`603af178`), the fp4 T = 1 row: the first-wave weight L2 prefetch that
the weight-loader warp issues during the dispatch phase (previous
revision `928195bfe`) is not compiled for a single token, where it
competed with the dispatch pull on the critical path; T >= 16 keeps it
and those programs are byte-identical to the previous revision. The
output is unchanged. Paired old/new kernel time: B200 t1 1.087x
(native/source 1.366x -> 1.477x); GB300 t1 1.073x (native/source 1.297x
-> 1.394x).
- `deepgemm_mega_mhc` (fused mHC, previous revision `603af178`), the
Normal (non-shifted) layouts: the mix warp-group, which ran the Mix only
in the Shifted programs while the Normal worker ran it serially, now
runs it in both modes and the Normal worker computes only the mixing
coefficients (`mix_coeff`); the Shifted programs are byte-identical to
the previous revision. The output is unchanged. Paired old/new kernel
time on the twelve Normal rows: B200 t1-col 1.183x (native/source 1.121x
-> 1.325x), t1-extra 1.207x (native/source 1.097x -> 1.325x), t64-col
1.165x (native/source 1.050x -> 1.219x), t64-extra 1.182x (native/source
1.060x -> 1.250x), t200-col 1.083x (native/source 1.070x -> 1.157x),
t200-extra 1.077x (native/source 1.091x -> 1.177x), t65-col 1.167x
(native/source 1.078x -> 1.259x), t65-extra 1.182x (native/source 1.056x
-> 1.247x), t1025-col 1.008x (native/source 1.043x -> 1.054x),
t1025-extra 1.001x (native/source 1.055x -> 1.052x), t4096-col 1.024x
(native/source 1.026x -> 1.051x), t4096-extra 1.028x (native/source
1.044x -> 1.074x); GB300 t1-col 1.165x (native/source 1.135x -> 1.327x),
t1-extra 1.196x (native/source 1.117x -> 1.337x), t64-col 1.144x
(native/source 1.094x -> 1.235x), t64-extra 1.163x (native/source 1.092x
-> 1.267x), t200-col 1.081x (native/source 1.087x -> 1.175x), t200-extra
1.091x (native/source 1.109x -> 1.212x), t65-col 1.150x (native/source
1.063x -> 1.223x), t65-extra 1.156x (native/source 1.047x -> 1.211x),
t1025-col 1.011x (native/source 1.033x -> 1.047x), t1025-extra 1.003x
(native/source 1.045x -> 1.045x), t4096-col 1.023x (native/source 1.034x
-> 1.058x), t4096-extra 1.025x (native/source 1.046x -> 1.072x).
- `deepgemm_mega_gate` (routing gate, previous revision `962ba5cb`), the
rows with M <= 64 tokens (M = 1, 3, 16 and the two M = 16 variants in
the cohort): while the GEMM pipeline runs, the otherwise idle
TMEM-allocator warp reads one 4-byte word per 32-byte sector of the
physical expert map (weak loads, 16 in flight per lane, summed into a
128-byte shared-memory scratch appended to the kernel's data pool that
nothing reads), so the winner-dependent physical-map lookup on the
serialized tail is an L2 hit instead of a cold DRAM access. Kernels for
M > 64 are byte-identical to the previous revision (generated-CUDA check
for M = 128 and 4096); the routing output is unchanged. Paired A/B
against the previous revision on one B200 (ABBA, three rounds): M = 1
8.576 -> 8.256 us (old/new 1.0388), M = 16 1.0074, deterministic M = 16
1.0089, each faster in 3/3 rounds and bitwise-correct; at the shipped
revision the M = 1 pairing replicated on another B200, 8.352 -> 8.032 us
(1.0398, 3/3); the routing-gate lever study on three more B200s read M =
1 -1.9..-4.2 % and M = 16 -1.1..-2.6 % kernel time. Same-GPU pairings on
three GB300s: M = 1 8.29 -> 7.97 us (-4.0 %), M = 16 -1.2..-2.8 %; M =
128 identical.
- `deepgemm_mega_mhc` (fused mHC, previous revision `962ba5cb`), the
shifted-layout rows with fewer than 64 tokens: the norm warp-group
touches the RMSNorm weight and the mix bases and scales into L2 during
its idle prologue. The touch is compiled only into the program that
serves single-m-block token counts (the 40-split program at HIDDEN 5120,
tokens 1 to 65), behind a warp-uniform runtime guard on the token count;
the 27- and 16-split programs (200 and more tokens) are byte-identical
to the previous revision. The output is unchanged. Paired A/B at the
shipped revision on one B200 (ABBA, three rounds): T = 1 col shifted
11.456 -> 11.136 us (old/new 1.0287) and T = 64 col shifted 12.768 ->
12.640 us (1.0101), each faster in 3/3 rounds; T = 200 and T = 1025
shifted identical to the previous revision (1.0000). The lever study on
four more B200s read T = 1 col shifted -2.0..-3.8 % and T = 1 extra
shifted -1.4..-5.2 % kernel time; same-GPU pairings on three GB300s:
-6.0..-6.3 % and -4.9..-5.3 %. An interim build that compiled the
guarded touch into every shifted program cost 32-128 ns on the T = 200
col-shifted row on GB300 (same-GPU pairing), which is why the touch is
confined to the single-m-block program at this revision.
- `fp8_batched_gemm` (FP8 batched per-head projection GEMM, previous
revision `6037418d`), the swap-AB route (T = 1, 16 and 128 with the FP8
epilogue in the cohort): the five TMA descriptors of the swap-AB kernel
request 256-byte L2 promotion, and the elected thread of warp 0
prefetches the first four k-steps of the A and B tiles of the CTA's
first work item into L2 (`cp.async.bulk.prefetch.tensor`) before the
pipeline starts; the kernel launches exactly the working CTAs of the
swap-AB tile grid (rounded to an even count for the CTA pair) instead of
one CTA per SM. The schedule is otherwise unchanged and the output is
bitwise identical; the n256, general and BF16 T4/T128 routes are
unchanged. Paired old/new kernel time on the FP8 batched projection
swap-AB rows (three ABBA rounds per GPU, CUPTI medians, cold L2,
previous revision -> this revision): B200 T1 1.0209-1.0210x, T16
1.0209-1.0355x, T128 1.0203-1.0278x on three GPUs, new faster in 9/9
rounds per row (native/source T1 1.015-1.018x -> 1.039-1.042x, T16
0.997-1.029x -> 1.030-1.048x, T128 1.027-1.035x -> 1.056x); GB300
same-GPU three-round spreads T1 10.66-10.69 -> 10.34 us (native/source
1.012x -> 1.049x), T16 10.69 -> 10.40 us (1.018x -> 1.046x), T128
13.73-13.76 -> 13.44 us (1.030x -> 1.052x); the T512/T4096 and BF16 rows
are time-identical on both architectures.
- `deepgemm_mega_mhc` (fused mHC, previous revision `6037418d`), the T =
1 rows with the extra layout on 148 SMs: the launch is trimmed to the 40
working CTAs, as it already was on 152 SMs and for the rows that write
the scale-factor output; the other rows are unchanged and the output is
unchanged. Paired old/new kernel time for the mHC T=1 extra-layout rows
on B200 (same protocol): t1 extra-shifted 1.0226-1.0276x on three GPUs,
new faster in 9/9 rounds (native/source 1.005-1.041x -> 1.033-1.065x);
the other mHC rows keep identical medians. On GB300 (152 SMs) the launch
was already trimmed, so the mHC rows there are regenerated from the same
schedule with unchanged native comparison (t1 extra-shifted 1.023x).
- `source_mega_moe` (fused single-kernel MoE, previous revision
`6aa36ebf`), rows with `num_tokens * top_k > 256` (fp4 T128, T512,
T1024, T4096 in the cohort): the dispatch warps pull each token's
activation row through registers (one 16-byte vector load per lane per
512 bytes, `evict_first`) and store it into the ring with 16-byte global
stores, instead of the bulk-copy round trip through a per-warp
shared-memory send buffer; the freed shared memory becomes one more
pipeline stage (7 -> 8 at the 128-token block). The combine's
store-buffer reuse waits for the shared-memory read of the previous bulk
store (`cp.async.bulk.wait_group.read`) instead of its completion. Rows
with `num_tokens * top_k <= 256` keep the previous form. The output is
bitwise identical. Paired old/new kernel time on the fused MoE source
rows (three ABBA rounds, CUPTI medians, cold L2, B200, `214ef484` ->
`6aa36ebf`): fp4 T128 1.0025x, T512 1.0025x (native/source 0.999x ->
1.001x), T1024 1.0039x, T4096 1.012x (native/source 1.005x -> 1.017x);
final-tree repeats against native: T4096 1.011-1.019x on three B200s,
1.028x on six GB300s.
- `deepgemm_mega_gate` (routing gate, previous revision `6aa36ebf`), M =
1 only: the eight split-K CTAs of one expert group form a thread-block
cluster; the seven non-leader CTAs write their partial scores into the
leader's shared memory with `st.async` (distributed shared memory, one
transaction-counted mbarrier), the leader reduces the eight partials in
a fixed order and writes the reduced scores, so the global score barrier
only spans the three group leaders (24 -> 3 CTAs, one round trip instead
of two) and the partial-score scratch round trip through global memory
is gone. The other M rows keep the previous form. The output is bitwise
identical (fixed-order FP32 sums). Paired old/new kernel time for the
routing gate M=1 row (three ABBA rounds per GPU, B200): 8.864 -> 8.352
us and 8.895 -> 8.416 us on two GPUs (1.061x / 1.057x, new faster in 3/3
rounds each), 8.672 -> 8.704 us on a third GPU (0.996x, 3/3 slower; on
that GPU the previous route already ran below native at ~0.985x, so the
row was not made slower than native by this change); the other ten gate
rows keep byte-identical programs and identical medians. Final-tree
repeats against native at M=1: B200 1.10-1.12x on four GPUs and 0.98x on
the third GPU above; GB300 1.004-1.099x on six GPUs.
- `deepgemm_sparse_mqa` (sparse MQA indexer, previous revision
`6aa36ebf`), paged rows: the metadata kernel assigns each wave's
schedule entries to SMs in a snake order (rank for even waves, reversed
rank for odd waves) instead of a rotated order, skips the terminating
claim atomic when every query row already has a CTA (`num_ctas >=
num_q_tokens`), and the final CTA issues its request-boundary loads
before the exclusive-sum barrier pair. The logits kernel and the
split-record layout are unchanged; the logits output is bitwise
identical. Paired old/new kernel time on the ten paged sparse MQA rows
(same protocol, B200): fp4 q512/k8192 1.030x (native/source 1.007x ->
1.038x), fp4 k4096 1.055x, fp8 k32768 1.027x, new faster in 3/3 rounds
on every row; final-tree repeats against native for fp4 k8192: B200
1.034-1.045x, GB300 1.037-1.045x.
- `deepgemm_fp4_gemm` (native FP4 1D1D GEMM, previous revision
`214ef484`), the M=4096 x N=4608 x K=5120 row (the M = 4096 row that
uses the 256-wide N tile, on both architectures): the exported program
is the static-shape form of the schedule with a rasterization of 8 M
blocks per N sweep, so the CTAs in flight share their B tiles in L2
instead of walking N first; the M=4096 x N=5120 x K=2304 row keeps its
224-wide N-tile composition on both architectures and is unchanged. The
output is bitwise identical. Paired old/new kernel time on the
native-DeepGEMM cohort rows (three ABBA rounds, CUPTI medians, cold L2,
B200): M=4096 x 4608 x 5120 1.012x (native/source 0.998x -> 1.010x);
final-tree repeats on three GPUs per architecture: B200 1.010-1.022x,
GB300 1.027-1.036x against native for this row.
- `deepgemm_kgroup_gemm` (FP4 K-grouped GEMM, previous revision
`214ef484`), SM100a only, M=5120 x N=2304 with FP32 output and no
accumulation: the route now uses the swapped BM240/BN128 schedule (A
multicast across the CTA pair), which fills the 148 SMs with one
persistent wave; the FP32-accumulate and BF16 rows keep the N=256 form
(measured faster or equal with it), and the SM103a routes are unchanged.
The output is bitwise identical. Paired old/new kernel time (same
protocol, B200): 1.032x (native/source 0.999x -> 1.032x), final-tree
repeats on three GPUs 1.027-1.037x against native.
- `source_mega_moe` (previous revision `da43cdffe`), rows with
`num_tokens * top_k <= 256` (fp4 T1, fp4 T16, FP8 T16 in the cohort): on
a single device the routing tensor is complete in global memory when the
kernel starts, so every CTA's dispatch warps now histogram all top-k
entries themselves, the scheduler warp reads the per-expert counts from
that shared-memory histogram after a 160-thread named-barrier
rendezvous, and the pull warps locate their token with warp scans over
the counts (expert, ordinal, pool offset) and find the source top-k slot
by ballot/popc over the top-k words. The count exchange (send-count
atomics, two grid syncs, system-scope receive-sum atomics, self
barrier), the per-expert slot table and the pull loop's linear expert
walk are gone; the ring protocol, token metadata and clean-up are
unchanged, and rows with more entries keep the previous form. A
kernel-internal timeline (per-CTA `%globaltimer` sites in a separately
traced diagnostic build) put the first activation TMA at 14-17 us after
kernel start before this change and at about 6 us after it on both
architectures. The output is bitwise identical. Paired old/new kernel
time on the native-DeepGEMM cohort rows (three ABBA rounds, CUPTI
medians, cold L2): fp4 T1 B200 1.2907x / GB300 1.1733x, fp4 T16 1.0052x
/ 1.0072x, FP8 T16 1.0053x / 1.0034x (3/3 rounds each); the fp4 T128 and
T4096 rows are byte-identical CUDA. Nine independent repeats of that
revision on the native comparison (three GPUs x three rounds): fp4 T1
9/9 > 1 (median B200 1.3560x, GB300 1.2779x), fp4 T16 9/9 (1.0063x /
1.0084x), FP8 T16 9/9 (1.0045x / 1.0043x).
- `source_mega_moe` (previous revision `928195bfe`): three schedule
changes to the fused single-kernel MoE. (1) For small token counts
(`num_tokens * top_k <= 256`) the weight-loader warp rebuilds the
per-expert token histogram from the top-k indices before its first task,
derives its cluster's first routed L1 tile and prefetches the first 16
k-steps of that weight tile into L2 (`cp.async.bulk.prefetch.tensor`)
while the dispatch phase runs, so the first weight stream no longer
starts cold after the dispatch. (2) The dispatch token pulls and the
combine chunk loads carry the L2 `evict_first` policy, the form native
DeepGEMM's `tma_load_1d` uses for these single-use streams
(`cp.async.bulk...L2::cache_hint`). The output is bitwise identical.
Paired old/new kernel time on the native-DeepGEMM cohort rows (each
lever three ABBA rounds, CUPTI medians, cold L2): first-wave L2 weight
prefetch B200 fp4 T16 1.0104x / FP8 T16 1.0067x, GB300 fp4 T16 1.0066x /
FP8 T16 1.0062x; evict-first pulls + combine loads fp4 T4096 B200
1.0042x, GB300 1.0055x. Nine independent repeats of the final revision
on the native comparison: B200 fp4 T16 9/9 > 1 (median 1.0011x), FP8 T16
9/9 (1.0026x), fp4 T4096 8/9 (1.0032x); GB300 fp4 T16 6/9 (1.0045x), FP8
T16 6/9 (1.0018x), fp4 T4096 at parity (1.0002x).
- `fp8_batched_gemm` (previous revision `928195bfe`), T128 BF16 feature
program only: the prologue L2-prefetches this CTA's first-tile A half
and B tile for the first four k-steps before barrier/TMEM
initialisation, so the single-wave kernel's DRAM stream starts during
the prologue instead of after it. The output is bitwise identical; the
other nine batched programs are regenerated with the same CUDA (they
differ from the previous revision only in the program identifier
embedded in the kernel and launcher names, which carries the producer
revision). Paired old/new kernel time on the projection T128 BF16 row:
prologue prefetch 10 k-steps B200 1.0148x / GB300 1.0130x, then 10 -> 4
k-steps B200 1.0100x / GB300 1.0185x (2 and 1 k-steps lose on both).
Nine independent repeats of the final revision: 9/9 > 1 on both (B200
median 1.0200x, GB300 1.0714x).
- `mega_moe_v3` (previous revision `fdb3bcdc4`): the dispatch stage of
the composed MoE kernel now claims each token/top-k pair's slot during
the expert histogram (one returning `atomicAdd` per pair) and records
the pair in a per-expert slot list, the form native DeepGEMM's
`read_topk_idx` uses; the pull loop walks expert-contiguous pool
ordinals and reads the pair from the list, so the per-token claim
atomics, the T512 mapping pass and its grid sync are gone. The per-token
`__threadfence()` before the elected block-readiness `red.release` is
dropped (native issues `__syncwarp` + `red.release`), and CTA 0
prefetches all expert counts before its serial prefix scan. The output
is bitwise identical (the pool row order is unchanged). Paired old/new
kernel time on the native-DeepGEMM cohort rows (product of the three
lever steps, each three ABBA rounds, CUPTI medians, cold L2): B200 T1
1.111x, T16 1.011x, FP8 T16 1.006x, T128 1.007x, T512 1.024x; GB300 T1
1.095x, T16 1.008x, FP8 T16 1.006x, T128 1.004x, T512 1.011x. Every v3
model row is faster than native DeepGEMM on every independent repeat on
both architectures (12 repeats on three B200 GPUs, 9 on three GB300
GPUs).
- `mega_moe_v3`: the combine stage of the composed MoE kernel now issues
all top-k expert-output row loads of a token chunk into per-warp slots
(six 2560-byte buffers plus one store buffer per warp, four chunks per
token) before its first wait and reduces them in slot order with the
same FP32x2 accumulation. The output is bitwise identical; the combine
critical path shortens. Paired old/new kernel time on the
native-DeepGEMM cohort rows: B200 T1 1.077x, T16 1.006x, T128 1.005x,
T512 1.010x, FP8 T16 1.010x; GB300 T1 1.061x, T16 1.005x, T128 1.004x,
FP8 T16 1.010x (T512 unchanged).
- `source_mega_moe`: the fused schedule's combine gets the same slot
prefetch (one slot per routed expert plus the shared experts), and when
the kernel runs on a single device its dispatch warps no longer execute
a final grid gate and system-scope self barrier after the workspace
clean-up (the kernel boundary already orders the cleaned counters before
the next launch, and the self barrier has no peer). Either change alone
is neutral because the combine tail was hidden behind the dispatch
clean-up; together they move the kernel end. Paired old/new kernel time:
B200 T1 1.035x, T16 1.009x, T128 1.002x, T4096 1.002x, FP8 T16 1.005x;
GB300 T1 1.034x, T16 1.009x, T128 1.002x, T4096 1.001x, FP8 T16 1.005x.
The pipeline-depth dial now counts the extra mbarrier control words, so
every exported shape stays within the 227 KB shared-memory budget.
- `mega_moe_v3` was regenerated on both architectures from the current
schedule tree (this revision, and at `eb0fd172` before it);
`deepgemm_dense_mqa` (previous revision `9fcc3668`),
`deepgemm_mega_gate` (`6e89f6a7`), `deepgemm_sparse_mqa` and
`deepgemm_mega_mhc` (`a8f45c78`), `source_mega_moe` (`603af178`),
`fp8_batched_gemm` (`6037418d`), `deepgemm_fp4_gemm` and
`deepgemm_kgroup_gemm` (`214ef484`) and the other three families are
unchanged.
- FP8 1D1D GEMM, SM100a programs regenerated (previous revision
`ca22d5133`): the two exported `sm_100a` PTX programs now spell the
block-scale qualifier explicitly
(`tcgen05.mma.cta_group::2.kind::mxf8f6f4.block_scale.scale_vec::1X`,
PTX ISA 8.6 form). The previous files omitted the token and ptxas 12.9 /
13.0 rejected them under the `.version 8.6` header (`Feature '.block32'
requires PTX ISA .version 8.8 or later`; the failing CI cells were B200
with CUDA 12.9 and 13.0, while ptxas 13.3+ accept the omission). The
explicit spelling assembles to the byte-identical cubin under ptxas
12.9; the `sm_103a` programs (`.version 8.8`) are unchanged.

## Validation

Producer revisions per family: MoE v3 from `f708ece8` (this revision),
dense MQA indexer from `e0a1fcba`, routing gate from `37f9b69c`, sparse
MQA indexer and mHC from `2c87654a`, MoE source from `c765aae8`, FP8
batched from `ef2a0873`, native FP4 GEMM and FP4 K-grouped GEMM from
`01e93b3b`, FP8 1D1D SM100a from `6bc24e04`; the remaining families from
`ee18d128` (SM100a) / `03a7d348` (SM103a), with the mixed FP8 x FP4
SM100a section from `f123c6e9` (see the note at the end). All revisions
are successive commits of one schedule tree; every generated family
passed the same export gate on both architectures.

### GB300 (SM103a, 152 SMs)

| Check | Result |
|---|---:|
| Combined checkout import probes (11 families) | **11/11** |
| `tests/experimental` for the 10 test files | **134 passed, 0 failed, 0
skipped (run at 24fb6c80 on GB300, 152 SMs; 11/11 import probes)** |
| Exported program vs. source schedule latency, 3 % budget (CUPTI
medians, cold L2, paired ABBA with arm preconditioning) | **145/145 rows
within budget**; per family: MoE v3 10/10 (min 0.9854x, regenerated at
this revision), sparse MQA indexer 20/20 (min 0.9840x), mHC 24/24 (min
0.9761x), dense MQA indexer 20/20 (min 0.9853x), routing gate 11/11 (min
0.9849x), MoE source 10/10 (min 0.9840x), FP8 1D1D 2/2 (min 0.999x),
mixed FP8xFP4 15/15 (min 0.971x), native FP4 11/11 (min 0.9714x), FP4
K-grouped 12/12 (min 0.9803x), FP8 batched 10/10 (min 0.9894x); worst
row 0.9710x (mixed FP8xFP4) |

### B200 (SM100a, 148 SMs)

| Check | Result |
|---|---:|
| Combined checkout import probes (11 families) | **11/11** |
| `tests/experimental` for the 10 test files | **134 passed, 0 failed, 0
skipped (run at 24fb6c80 on B200, 148 SMs; 11/11 import probes)** |
| Exported program vs. source schedule latency, 3 % budget (CUPTI
medians, cold L2, paired ABBA with arm preconditioning) | **145/145 rows
within budget**; per family: MoE v3 10/10 (min 0.9964x, regenerated at
this revision), sparse MQA indexer 20/20 (min 0.9926x), mHC 24/24 (min
0.9719x), dense MQA indexer 20/20 (min 0.9914x), routing gate 11/11 (min
0.9815x), MoE source 10/10 (min 0.9957x), FP8 1D1D 2/2 (min 0.9998x),
mixed FP8xFP4 15/15 (min 0.972x), native FP4 11/11 (min 0.9881x), FP4
K-grouped 12/12 (min 0.9972x), FP8 batched 10/10 (min 0.9931x); worst
row 0.9719x (mHC) |

### Both

| Check | Result |
|---|---:|
| compute-sanitizer | exported programs regenerated at this revision, on
GB300 (`tests/experimental/test_generated_mega_moe.py` restricted with
`-k` to the v3 fp4 pipeline reference/replay tests and the v3
model-route (T = 1) workspace-lifecycle test): 3 passed, `ERROR SUMMARY:
0 errors` (synccheck, 270 s); the other families are unchanged from the
previous revision |
| Source schedules vs. native DeepGEMM (`39d8c4ca`), 118 model rows |
118/118 correct; geometric mean 1.2427x on the B200 cohort (118 rows
faster than native: 109 outright and 9 by the repeat rule) and 1.2513x
on the GB300 cohort (118 rows faster than native: 106 outright and 12 by
the repeat rule); under the repeat rule (three independent paired runs
on three GPUs agreeing in direction) 118/118 rows are faster on both
architectures. Cohort geomean native/source 1.2427 on B200 (previous
revision: 1.2422; minimum 1.0019, the fused fp4 MoE at T = 512, a sealed
row measured under the repeat rule in an earlier revision) and 1.2513 on
GB300 (previous revision: 1.2504; minimum 1.0035, the fused fp4 MoE at T
= 1024). The fp4 T = 1 MoE row re-measured in this revision reads
1.4577x on B200 (previous revision 1.3895x) and 1.4744x on GB300
(previous revision 1.3555x) (medians of six readings), with every
individual reading above 1.445. The other 117 rows keep their previous
measurement (their generated programs are identical, checked at 148 and
152 SMs). Correction to the earlier revisions of this row: the ten mixed
FP8 x FP4 GEMM rows had been listed at 1.25x-1.64x, which is the
specialized schedule's speedup over this package's generic fallback
schedule (the harness's paired baseline arm), not over native DeepGEMM;
against native `fp8_fp4_gemm_nt` they read 1.0044x-1.0372x on B200 and
1.0080x-1.0353x on GB300, every reading above native on five GPUs (M =
4096, N = 4608 by the repeat rule on B200), which lowers the geometric
means from the previously stated 1.2452x / 1.2597x; no other row
changes. The routing-gate rows with M <= 64 and the mHC shifted rows
were re-measured at the shipped programs on both architectures (B200:
three-round spreads on two GPUs plus the paired A/B; GB300: three-round
spreads on three GPUs); every other row's kernel is byte-identical to
the previous revision (generated-CUDA identity checks) and keeps its
earlier cohort readings. |
| Upstream pre-commit | passes on all 510 files of this PR with the
unchanged upstream `.pre-commit-config.yaml` (ruff check/format, mypy,
clang-format, whitespace/EOF/tabs hooks); the eleven package directories
carry a `.clang-format` with `DisableFormat: true` so the receipt-bound
generated sources are never reformatted |
| FP8 1D1D PTX assembly (`ptxas -v --register-usage-level=10
--gpu-name=sm_100a`) | the regenerated sm_100a programs assemble with
ptxas 12.9.86 and 13.3.73 (`rc=0`, checked on B200 before publication);
the previous sm_100a programs failed under ptxas 12.9 with `Feature
'.block32' requires PTX ISA .version 8.8 or later` at every block-scaled
MMA and assembled only with ptxas 13.3+; the sm_103a programs (`.version
8.8`) assemble on both and are unchanged |
| Head composition | `24fb6c8007159bf4babe6d4f6ed77d55842ecb6f` =
`eb0fd172` (the validated programs of the previous revisions) + the
regenerated MoE v3 model-row programs and catalog sections for both
architectures (5 files: the two self-cleaning fp4 T = 1 kernels and
their bindings carry the folded metadata chain; the eighteen other MoE
v3 programs are byte-identical to the previous revision and are not
rewritten); no generated program, Python module or test of the other ten
families changes |

<details>
<summary>Per-row native/source speedup of the 118 model rows (both
architectures; every row above 1.0x; minimum 1.0019x on B200, 1.0035x on
GB300)</summary>

native/source = native DeepGEMM `39d8c4ca` kernel time / source-schedule
kernel time on the same GPU (cohort harness: CUPTI medians, cold L2,
paired arms). "repeat rule" marks rows within 1 % of native that were
confirmed by three independent paired runs agreeing in direction; every
other row is above 1.0x outright. The fp4 T = 1 MoE v3 row was
re-measured at this revision; the other 117 rows keep their previous
measurement (their generated programs are byte-identical).

**Sparse MXFP4/MXFP8 MQA logits indexer** (20 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `sparse-mxfp4-contiguous-q8192-k1048576` | 1.0346x | 1.0266x |
| `sparse-mxfp4-contiguous-q8192-k131072` | 1.0445x | 1.0605x |
| `sparse-mxfp4-contiguous-q8192-k32768` | 1.0437x | 1.0621x |
| `sparse-mxfp4-contiguous-q8192-k4096` | 1.1174x | 1.1288x |
| `sparse-mxfp4-contiguous-q8192-k8192` | 1.0687x | 1.1050x |
| `sparse-mxfp4-paged-q512-k1048576` | 1.1093x | 1.1295x |
| `sparse-mxfp4-paged-q512-k131072` | 1.0366x | 1.0396x |
| `sparse-mxfp4-paged-q512-k32768` | 1.0560x | 1.0486x |
| `sparse-mxfp4-paged-q512-k4096` | 1.0843x | 1.0604x |
| `sparse-mxfp4-paged-q512-k8192` | 1.0546x | 1.0495x |
| `sparse-mxfp8-contiguous-q8192-k1048576` | 1.0466x | 1.0227x |
| `sparse-mxfp8-contiguous-q8192-k131072` | 1.1549x | 1.2213x |
| `sparse-mxfp8-contiguous-q8192-k32768` | 1.1083x | 1.1336x |
| `sparse-mxfp8-contiguous-q8192-k4096` | 1.1448x | 1.1796x |
| `sparse-mxfp8-contiguous-q8192-k8192` | 1.1149x | 1.1847x |
| `sparse-mxfp8-paged-q512-k1048576` | 1.1433x | 1.1140x |
| `sparse-mxfp8-paged-q512-k131072` | 1.1053x | 1.0549x |
| `sparse-mxfp8-paged-q512-k32768` | 1.0999x | 1.1139x |
| `sparse-mxfp8-paged-q512-k4096` | 1.0724x | 1.0733x |
| `sparse-mxfp8-paged-q512-k8192` | 1.0852x | 1.0724x |

**Dense FP4 MQA lightning indexer** (10 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `indexer_fp4-q1-k131072-scheduled` | 1.2595x | 1.3141x |
| `indexer_fp4-q1-k32768-scheduled` | 1.1875x | 1.2233x |
| `indexer_fp4-q1-k4096-scheduled` | 1.2565x | 1.2557x |
| `indexer_fp4-q128-k131072-scheduled` | 1.8138x | 1.8417x |
| `indexer_fp4-q128-k32768-scheduled` | 1.5655x | 1.5244x |
| `indexer_fp4-q128-k4096-scheduled` | 1.1867x | 1.1848x |
| `indexer_fp4-q16-k1048576-scheduled` | 6.7367x | 7.3756x |
| `indexer_fp4-q16-k131072-scheduled` | 3.6908x | 3.7334x |
| `indexer_fp4-q16-k32768-scheduled` | 2.0940x | 2.1415x |
| `indexer_fp4-q16-k4096-scheduled` | 1.3280x | 1.3727x |

**Dense FP8 MQA lightning indexer** (10 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `indexer_fp8-q1-k131072-scheduled` | 16.4658x | 16.3857x |
| `indexer_fp8-q1-k32768-scheduled` | 5.7418x | 5.8129x |
| `indexer_fp8-q1-k4096-scheduled` | 2.8286x | 2.9470x |
| `indexer_fp8-q128-k131072-scheduled` | 1.8296x | 1.8944x |
| `indexer_fp8-q128-k32768-scheduled` | 1.4303x | 1.4302x |
| `indexer_fp8-q128-k4096-scheduled` | 1.3400x | 1.3751x |
| `indexer_fp8-q16-k1048576-scheduled` | 6.3769x | 6.2472x |
| `indexer_fp8-q16-k131072-scheduled` | 3.7422x | 3.9745x |
| `indexer_fp8-q16-k32768-scheduled` | 2.0685x | 2.1605x |
| `indexer_fp8-q16-k4096-scheduled` | 1.2493x | 1.3273x |

**Fused routing gate** (11 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `gate-m1` | 1.1473x | 1.1110x |
| `gate-m1024` | 1.0470x | 1.0461x |
| `gate-m128` | 1.0330x | 1.0454x |
| `gate-m16` | 1.0658x | 1.0520x |
| `gate-m16-deterministic` | 1.0481x | 1.0543x |
| `gate-m16-logical` | 1.0375x | 1.0313x |
| `gate-m2048` | 1.0305x | 1.0473x |
| `gate-m3` | 1.0582x | 1.0407x |
| `gate-m4096` | 1.0391x | 1.0341x |
| `gate-m512` | 1.0391x | 1.0356x |
| `gate-m8192` | 1.0226x | 1.0198x |

**Fused mHC** (24 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `mhc-t1-col-plain` | 1.3254x | 1.3267x |
| `mhc-t1-col-shifted` | 1.0747x | 1.0536x |
| `mhc-t1-extra-plain` | 1.3247x | 1.3366x |
| `mhc-t1-extra-shifted` | 1.0627x | 1.0679x |
| `mhc-t1025-col-plain` | 1.0539x | 1.0464x |
| `mhc-t1025-col-shifted` | 1.0164x | 1.0222x |
| `mhc-t1025-extra-plain` | 1.0517x | 1.0449x |
| `mhc-t1025-extra-shifted` | 1.0442x | 1.0606x |
| `mhc-t200-col-plain` | 1.1579x | 1.1754x |
| `mhc-t200-col-shifted` | 1.0184x | 1.0087x (repeat rule) |
| `mhc-t200-extra-plain` | 1.1781x | 1.2119x |
| `mhc-t200-extra-shifted` | 1.0193x | 1.0129x |
| `mhc-t4096-col-plain` | 1.0507x | 1.0585x |
| `mhc-t4096-col-shifted` | 1.0427x | 1.0453x |
| `mhc-t4096-extra-plain` | 1.0733x | 1.0715x |
| `mhc-t4096-extra-shifted` | 1.0730x | 1.0787x |
| `mhc-t64-col-plain` | 1.2202x | 1.2348x |
| `mhc-t64-col-shifted` | 1.0556x | 1.0377x |
| `mhc-t64-extra-plain` | 1.2500x | 1.2672x |
| `mhc-t64-extra-shifted` | 1.0685x | 1.0571x |
| `mhc-t65-col-plain` | 1.2604x | 1.2225x |
| `mhc-t65-col-shifted` | 1.0666x | 1.0716x |
| `mhc-t65-extra-plain` | 1.2475x | 1.2109x |
| `mhc-t65-extra-shifted` | 1.0714x | 1.0858x |

**MoE, source schedule (fused single kernel)** (7 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `source-moe-fp4-t1` | 1.4740x | 1.3938x |
| `source-moe-fp4-t1024` | 1.0042x (repeat rule) | 1.0035x (repeat rule)
|
| `source-moe-fp4-t128` | 1.0057x (repeat rule) | 1.0052x (repeat rule)
|
| `source-moe-fp4-t16` | 1.0063x (repeat rule) | 1.0069x (repeat rule) |
| `source-moe-fp4-t4096` | 1.0158x | 1.0283x |
| `source-moe-fp4-t512` | 1.0019x (repeat rule) | 1.0047x (repeat rule)
|
| `source-moe-fp8-feature-t16` | 1.0061x (repeat rule) | 1.0052x (repeat
rule) |

**MoE, v3 composed schedule** (5 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `moe-fp4-t1` | 1.4577x | 1.4744x |
| `moe-fp4-t128` | 1.0028x (repeat rule) | 1.0061x (repeat rule) |
| `moe-fp4-t16` | 1.0193x | 1.0151x |
| `moe-fp4-t512` | 1.0045x (repeat rule) | 1.0050x (repeat rule) |
| `moe-fp8-feature-t16` | 1.0136x | 1.0050x (repeat rule) |

**Mixed FP8 x FP4 GEMM** (10 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `gemm-l1-m1` | 1.0313x | 1.0327x |
| `gemm-l1-m128` | 1.0362x | 1.0353x |
| `gemm-l1-m16` | 1.0330x | 1.0330x |
| `gemm-l1-m4096` | 1.0044x (repeat rule) | 1.0080x (repeat rule) |
| `gemm-l1-m512` | 1.0230x | 1.0249x |
| `gemm-l2-m1` | 1.0201x | 1.0207x |
| `gemm-l2-m128` | 1.0372x | 1.0343x |
| `gemm-l2-m16` | 1.0247x | 1.0208x |
| `gemm-l2-m4096` | 1.0127x | 1.0156x |
| `gemm-l2-m512` | 1.0177x | 1.0227x |

**Native FP4 GEMM** (8 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `fp4gemm-l1-m128` | 1.0312x | 1.0293x |
| `fp4gemm-l1-m16` | 1.0258x | 1.0233x |
| `fp4gemm-l1-m4096` | 1.0170x | 1.0363x |
| `fp4gemm-l1-m512` | 1.0207x | 1.0314x |
| `fp4gemm-l2-m128` | 1.0377x | 1.0275x |
| `fp4gemm-l2-m16` | 1.0265x | 1.0229x |
| `fp4gemm-l2-m4096` | 1.0079x (repeat rule) | 1.1464x |
| `fp4gemm-l2-m512` | 1.0251x | 1.0229x |

**FP4 K-grouped GEMM** (6 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `kgroup-training-feature-l1-bf16-acc0` | 1.0240x | 1.0283x |
| `kgroup-training-feature-l1-fp32-acc0` | 1.0182x | 1.0169x |
| `kgroup-training-feature-l1-fp32-acc1` | 1.1829x | 1.2082x |
| `kgroup-training-feature-l2-bf16-acc0` | 1.0131x | 1.0158x |
| `kgroup-training-feature-l2-fp32-acc0` | 1.0319x | 1.0081x (repeat
rule) |
| `kgroup-training-feature-l2-fp32-acc1` | 1.0824x | 1.0087x (repeat
rule) |

**FP8 batched per-head projection GEMM** (7 rows)

| row | B200 (148 SMs) | GB300 (152 SMs) |
|---|---:|---:|
| `batched-projection-t1-fp8` | 1.0419x | 1.0495x |
| `batched-projection-t128-alpha-feature` | 7.6815x | 8.9785x |
| `batched-projection-t128-bf16-feature` | 1.0198x | 1.0837x |
| `batched-projection-t128-fp8` | 1.0557x | 1.0524x |
| `batched-projection-t16-fp8` | 1.0449x | 1.0462x |
| `batched-projection-t4096-fp8` | 1.0185x | 1.0208x |
| `batched-projection-t512-fp8` | 1.0150x | 1.0115x |

</details>

## Baselines and their source PRs

Every "native" arm in the tables above is upstream DeepGEMM at the
pinned revision below; the exported programs are
compared against it by the same CUPTI protocol (cold L2, paired arms) on
the same GPU in the same process.

- **Native DeepGEMM `39d8c4cacc2c`** (2026-09-10, "Update News"; the
head of deepseek-ai/DeepGEMM PR #432 "Public Release 26/09",
merged 2026-09-10 as `66081d4c9c7d`). Kernels compared:
`deep_gemm/include/deep_gemm/impls/sm100_fp8_fp4_mega_moe.cuh`
(mega MoE: dispatch + grouped L1/SwiGLU/L2 + combine; the
`source_mega_moe` and `mega_moe_v3` families), the SM100
sparse MQA indexer, routing gate, mHC, FP8 1D1D / mixed FP8xFP4 / native
FP4 / FP4 K-grouped / FP8 batched GEMM
implementations under the same directory, and the host APIs under
`csrc/apis/` (e.g. `csrc/apis/mega_moe.hpp`).
Test oracle: the DeepGEMM reference paths from the same revision
(`deep_gemm.testing` numerics, `calc_diff`), plus the
PyTorch references in this PR's tests. No later change check: the newest
DeepGEMM commit touching those files is the PR #432
merge `66081d4c9c7d` (2026-09-10); DeepGEMM `main` (`78b69000794d`,
2026-09-14) contains no further change to them.
- **This branch's FlashInfer merge-base**: `a21dcfd96a48`
(flashinfer-ai/flashinfer main, 2026-09-24, "test(cake_sampling): pin
the
  nvcc sm_107 probe in the build-target test (#5511)").

## Not included / follow-ups

- The dense FP4/FP8 lightning-indexer family (`deepgemm_dense_mqa`) is
generated from the same schedule tree as the source-vs-native cohort
numbers above; its prepared plans own no allocation, regenerate the
schedule metadata on every submission and accept in-place operand and
window updates (including CUDA Graph replay).
- Mixed FP8 x FP4 uses the same route plan on both architectures
(swap-AB for M <= 16 and M = 128, normal for M = 512, elected-loader
normal for M = 4096, generic bk128/bk256 otherwise): 12 programs for 15
routes per architecture. On B200 the ten DeepSeek-shaped rows move from
0.66x-0.84x of native DeepGEMM with the generic fallback to
1.006x-1.036x with the specialized schedules (bitwise-equal outputs);
the SM100a section was regenerated from `f123c6e9` (the producer tree
plus the harness commit that admits these schedules on SM100), all other
sections from `ee18d128`.
- Every latency row pairs the two arms in counterbalanced ABBA blocks
with one unmeasured launch of the upcoming arm before each measured
launch; the K-grouped rows on SM100a use fixed per-group sample counts
(6000 warmup / 2000 measured per arm) instead of millisecond budgets,
because the ~1 s warmup that stabilizes B200 clocks on the 50-170 us
rows would cost ~370k launches per arm on the 3-7 us rows.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: yyihuang <yyihuang@users.noreply.github.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bd0cbcc](https://github.com/flashinfer-ai/flashinfer/commit/bd0cbcc8bc5c439949a0337250eee79bcf2b5710)

- **作者**: Enwei Zhu
- **时间**: 2026-09-29T23:09:10Z
- **提交信息**: fix(comm): support Kimi K3 shapes in MNNVL HT allreduce_fusion (#5632)

<!-- .github/pull_request_template.md -->

## 📌 Description

HT currently requires each reduction shard's BF16×8 pack count to divide
evenly across the reduction threads. For Kimi K3's hidden size of 3584,
TP4/TP8/TP16 produce 112/56/28 packs per shard, so all three
configurations are rejected.

This change:

- Uses ceiling division and predicates the final reduction iteration,
including the multicast load, residual load, and multicast store.
- Consolidates the load/store primitives around an optional predicate.
Omitting it preserves unconditional access; inactive loads return zero
and inactive stores perform no write. Aligned shards use a compile-time
constant predicate.
- Adds BF16 H3584/top-k16 profiles to `HT_ONLY_CONFIG` for TP4, TP8, and
TP16, sharing the same tuning presets.
- Extends the existing numerical contract test with one K3 shape case,
usable at all three TP sizes.

The public `allreduce_fusion` API and automatic LL/BT/HT dispatch
profiles remain unchanged.

## 🔍 Related Issues

None.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validation on NVIDIA GB300:

- Configuration tests: 18 passed.
- Existing numerical contract test: TP4 K3 case passed; all five TP8
cases passed. The four H8192 cases correctly skip at TP4.
- Additional local validation at TP4 and TP8: 16 cases per TP size
covering M = 1, 7, 8, 9, 33, 1025, 8192, and 8193, with shared/residual
inputs enabled and disabled. Both operation patterns passed eager
execution and two CUDA graph replays with changed inputs, missing
routes, and output guard checks. This harness is outside the PR.
- Existing no-RMSNorm tests: 11 passed at TP4; 10 passed and one
expected unsupported-profile skip at TP8.
- TP16: both operation patterns compiled for ranks 0 and 15, with
optional inputs enabled and disabled (eight variants). **Full TP16
runtime validation is pending access to 16 GPUs.**
- `pre-commit run --all-files` passed.

Distributed test modules were run in separate worker launches; a
combined invocation encountered an NCCL initialization error when
recreating the process group between modules.

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

### Predication regression checks

For aligned H8192/TP8 HT kernels, the constant predicate compiled away:
executable machine code and register usage matched the upstream
implementation. Consolidating the primitive APIs also preserved
executable code in all 16 compared TP8 LL/BT/HT variants, including K3
HT.

Cold-L2 regression measurements used eight GB300 GPUs, BF16 H8192,
top-k10, and TP8, with shared/residual inputs disabled. Each CUDA graph
iteration evicted 512 MiB from L2 and aligned ranks with a small NCCL
operation before the measured HT operation. Nsight GPU spans excluded
those controls. Baseline/candidate order alternated; results are medians
of 60 samples, each taking the maximum latency across ranks. Baseline:
`f4d45edf`.

Selected measurements (microseconds):

| Operation | Tokens | Before | After |
|---|---:|---:|---:|
| All-reduce + RMSNorm | 128 | 24.256 | 24.560 |
| All-reduce + RMSNorm | 1024 | 56.752 | 56.880 |
| All-reduce + RMSNorm | 8192 | 312.496 | 315.264 |
| Finalize + all-reduce + RMSNorm | 128 | 27.680 | 28.016 |
| Finalize + all-reduce + RMSNorm | 1024 | 69.600 | 69.344 |
| Finalize + all-reduce + RMSNorm | 8192 | 321.728 | 320.192 |

Across the full measured sweep, latency changes ranged from -0.48% to
+1.25%, with identical executable code for the compared aligned kernels.
These results are specific to the tested GB300 configurations.

TP4 and TP16 reuse the TP8 tuning values; this PR does not claim
separately optimized tuning for those TP sizes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added GB300 support for BF16 all-reduce and finalize operations with
hidden size 3584 and top-k 16 across tensor-parallel sizes 4, 8, and 16.
* Reduction operations now support shard sizes that are not evenly
divisible across threads.
  * Memory load and store operations can now be conditionally performed.
* **Bug Fixes**
* Improved handling of out-of-range vectors when processing uneven shard
sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Enwei Zhu <21126786+syuoni@users.noreply.github.com>

### [88c241d](https://github.com/flashinfer-ai/flashinfer/commit/88c241d45dc0ce29d71ebe517cec8fb0da0444cf)

- **作者**: eigen
- **时间**: 2026-09-29T22:56:21Z
- **提交信息**: feat(cake_fused_moe): add Kimi-K3 NVFP4 SiTU experts for SM100/SM103 (#5183)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baseline** on **all 52 reported performance
benchmark shapes across B200 and B300**.

Adds a Cake backend for TP8-local Kimi-K3 NVFP4 SiTU routed experts on
SM100 and SM103. The API uses caller-provided output and a prepared
workspace. It supports BF16 input/output, group-16 NVFP4 weights,
H=3584, I=384, E=896, top-k=16, and 1–16384 tokens.

The complete call performs input quantization, routing, FC1, SiTU
activation, intermediate requantization, FC2, and weighted BF16
finalization. Output is local to the tensor-parallel rank; the caller
owns collectives. Weights use the TRTLLM shuffled NVFP4 layout prepared
with `TrtllmFp4Config.prepare_weights(..., activation=SiTU())`, with the
corresponding six-entry `quant_scales` list. The default SiTU gate and
linear smoothing values are 4 and 25; caller-owned per-expert smoothing
tensors are also supported.

Use the public API in three steps:

1. Query `cutlass_fused_moe_workspace_size(...,
activation_type=ActivationType.Situ, tp_size=8, backend="cake")` and
allocate output and workspace storage.
2. Call `cutlass_fused_moe_prepare_workspace(workspace, num_tokens,
backend="cake")` for each token count before capture or first
submission. Preparation loads the generated route and initializes
workspace views and constants without allocating tensor storage.
3. Submit `cutlass_fused_moe(..., activation_type=ActivationType.Situ,
tp_size=8, backend="cake", workspace_buffer=workspace, output=output)`.
Submission makes no CUDA allocation and owns no graph; callers may
capture and replay the complete call. Concurrent calls require separate
workspace/output storage and normal stream ordering.

The implementation includes generated CUDA sources, launch bindings,
route selection, public workspace/graph tests, and
`docs/tutorials/cake_kimi_k3_situ.rst` with the full layout and API
example.

The backend is JIT-only by design for this first narrow-shape backend:
the generated sources are loaded per architecture/route selector through
`flashinfer/jit/cake_kimi_k3_situ.py`, and no ahead-of-time module
generator is registered in `flashinfer/aot.py`. Review follow-up (commit
`1bdc6882`): `cutlass_fused_moe_workspace_size` now covers every smaller
prepared shape for any `max_num_tokens` (the per-shape layout is not
monotonic in the token count at 32 and 64 tokens; the returned size
changes only for `max_num_tokens` in 33..63), with a CPU-only test over
all 16384 token counts and a GPU test that prepares 32 (64) tokens in a
buffer sized for 40 (100). Kernels, route table and the measured token
counts are unchanged.

Correctness checks compare every BF16 element with `atol=1.0, rtol=0.1`,
including intermediate results, and retain exact-array and routing
checks. They run before and after measurement with shared fixtures and
restored mutable state. Source/export activity parity and allocation
tracing verify that the submitted operation retains its execution
boundary.

The implementation now ships the unified generated-program export: 150
generated CUDA translation units (75 for sm_100a, 75 for sm_103a; 64
kernel modules and 22 prepared launch sequences, every source referenced
by the registration table) selected through 19 architecture/route
selectors, with the regenerated registration, prepared-workspace
runtime, public API dispatch, tutorial and tests. Routes added since the
first revision of this PR: tile-N16 claim-8 routes for M32-M256,
tile-N32 claim-8 routes for M512/M1024, a work-fed FC2 route for
M2048/M4096 and a dedicated single-token route; the public API and its
three-step usage above are unchanged.

Performance qualification covers 52 physical rows: B200 and B300, each
at M={1,8,16,32,64,128,256,512,1024,2048,4096,8192,16384}, with uniform
and skewed routing. The FlashInfer comparison uses
`trtllm_fp4_block_scale_routed_moe` at revision
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, including input quantization
and finalization for the same complete-call boundary. Every row is
re-measured with the final export in one isolated step per row with four
arms: the current source implementation, this export, the FlashInfer
baseline, and the previously published revision of this export
(`c3429c97a1de10be9e0a91de38930bb3ce1d6e2b`, the "original export").

All arms use symmetric external CUDA graphs and CUPTI activity timing
with cold L2. The frozen protocol uses three counterbalanced groups, 100
ms warmup and 1000 ms reportable budget per arm/group, a 100000-sample
cap, and a minimum 1900 MHz SM clock. Each sample follows an unmeasured
same-arm launch, state restoration, and a fresh cold-L2 flush.
Qualification requires source/export >= 0.97, directional disagreement
<= 2%, sustained endpoint drift <= 2% (maximum across arms of each arm's
median drift over the three groups), activity parity, allocation-free
submission, and no regression against the original export (original
export / export >= 1). Correctness (every BF16 element at `atol=1.0,
rtol=0.1`, exact intermediate arrays, exact routing) runs before and
after each measurement with shared fixtures and restored mutable state;
each row additionally passes compute-sanitizer synccheck (0 errors) and
racecheck (0 hazards) on the realized export before it is timed.

`Source / Export` measures retention of the current source
implementation's performance. `FlashInfer / Export` compares the
FlashInfer baseline with this backend; values above 1 favor the export.
`Original export / Export` compares the previously published export
revision with this one; values above 1 mean this revision is faster.
Geomeans include every timed row in the stated denominator.

| Rows | Count | Export faster than FlashInfer | Source / Export geomean
| FlashInfer / Export geomean | Original export / Export geomean |
Export us geomean | Source us geomean | FlashInfer us geomean |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| B200 (sm_100a) | 26 | 26/26 | 0.999627x | 1.095970x | 1.257645x |
258.095 | 257.999 | 282.864 |
| B300 (sm_103a) | 26 | 26/26 | 0.999036x | 1.096573x | 1.238362x |
255.408 | 255.162 | 280.073 |
| uniform routing | 26 | 26/26 | 0.999019x | 1.082566x | 1.203095x |
282.909 | 282.631 | 306.267 |
| skewed routing | 26 | 26/26 | 0.999644x | 1.110151x | 1.294511x |
233.006 | 232.923 | 258.672 |
| all rows | 52 | 52/52 | 0.999332x | 1.096271x | 1.247966x | 256.748 |
256.576 | 281.465 |


## Round 3: convergence toward the hardware ceiling

This update adds a per-row **ceiling-model gap** column to the 52-row
qualification table and reports the round-3 increments:

- B300 (sm_103a), M in {32, 64, 128, 256}, uniform and skewed routing:
the FC2 stage now runs a new program variant with the direct-store +
warp-arrive epilogue (the epilogue already shipped for the SM100 mid
rows in the previous update). Two generated SM103 program records (three
translation units) are added and one JIT route-table entry changes;
every other file is byte-identical to the previous head. Outputs are
bitwise identical to the previous export on all eight rows. These eight
rows supersede the sm_103a mid-row values of the previous update; the
other 44 rows keep their published measurements (no historical
substitution is used for any changed row).
- B200 (sm_100a) and B300 (sm_103a), M in {8192, 16384}, uniform and
skewed routing: the FC2 stage now runs the mid-shape FC2 program (the
production schedule of the M2048/M4096 rows) instead of the large-shape
variant. No generated source or program record is added; only the two
large-shape entries of the JIT route table change (two lines in
`flashinfer/jit/cake_kimi_k3_situ.py`), and every other file is
byte-identical to the previous head; the shipped set stays at 144
translation units behind the unchanged 19 route selectors. Outputs are
bitwise identical to the previous export on all eight rows. These eight
rows supersede the M8192/M16384 values of the previous update; the other
44 rows keep their published measurements (no historical substitution is
used for any changed row). Per row (`Previous export / Export` compares
the previous head's realization of the same row with this one):
- B200 (sm_100a) and B300 (sm_103a), M in {8192, 16384}, uniform and
skewed routing (this update): the FC1 stage now runs a new generated FC1
program whose shared-memory operand load path is wider; the FC2 stage
keeps the mid-shape program these rows received in the previous update.
Six generated sources are added (kernel and binding for the new FC1
module plus the new sequence binding, per architecture), the program
table gains four records, and the two large-shape entries of the JIT
route table move to the new sequences; the runtime module and every
other file are byte-identical to the previous head, so the shipped set
is 150 translation units behind the unchanged 19 route selectors.
compute-sanitizer synccheck, racecheck and memcheck (the shared-memory
store pattern changed) are clean on the source and the export arm of
every row. Outputs are bitwise identical to the previous export on all
eight rows and in every measurement round. These eight rows supersede
the M8192/M16384 values of the previous update; the other 44 rows keep
their published measurements (no historical substitution is used for any
changed row).

Values of the previous update for the eight large rows (superseded by
the table below):

| Row | Export us | FlashInfer / Export | Previous export / Export |
Source / Export |
|---|---:|---:|---:|---:|
| B200 M8192 uniform | 966.655 | 1.3596x | 1.0274x | 0.9992x |
| B200 M8192 skewed | 942.910 | 1.7737x | 1.0298x | 1.0004x |
| B200 M16384 uniform | 1614.053 | 1.4388x | 1.0228x | 1.0012x |
| B200 M16384 skewed | 1572.405 | 1.3765x | 1.0266x | 0.9999x |
| B300 M8192 uniform | 871.921 | 1.3756x | 1.0277x | 0.9993x |
| B300 M8192 skewed | 907.690 | 1.7694x | 1.0228x | 1.0000x |
| B300 M16384 uniform | 1459.857 | 1.4578x | 1.0230x | 1.0005x |
| B300 M16384 skewed | 1470.385 | 1.3617x | 1.0204x | 0.9993x |

This update:

| Row | Export us | FlashInfer / Export | Previous export / Export |
Export before the previous update / Export | Source / Export |
|---|---:|---:|---:|---:|---:|
| B200 M8192 uniform | 934.476 | 1.4336x | 1.0482x | 1.0771x | 1.0007x |
| B200 M8192 skewed | 917.241 | 1.8420x | 1.0362x | 1.0651x | 0.9999x |
| B200 M16384 uniform | 1525.078 | 1.5379x | 1.0763x | 1.0960x | 1.0023x
|
| B200 M16384 skewed | 1515.210 | 1.4513x | 1.0516x | 1.0786x | 1.0001x
|
| B300 M8192 uniform | 851.946 | 1.4327x | 1.0320x | 1.0613x | 1.0001x |
| B300 M8192 skewed | 880.616 | 1.8244x | 1.0321x | 1.0556x | 1.0001x |
| B300 M16384 uniform | 1399.250 | 1.5552x | 1.0658x | 1.0889x | 1.0004x
|
| B300 M16384 skewed | 1428.884 | 1.4137x | 1.0387x | 1.0576x | 0.9991x
|

**Ceiling model.** Each row's floor is the sum over the seven stages
(input quantization, routing, FC1, activation/requantization, FC2,
finalization) of max(HBM bytes / 7.4 TB/s, tensor FLOPs / 6.75 PFLOP/s),
with occupied-expert weight bytes per row. All 52 rows have a per-stage
attribution run (M = 1, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096,
8192, 16384; uniform and skewed; both GPUs), so every floor is the
attributed per-stage model and no floor is interpolated. The gap is the
whole-call export latency over the floor; convergence is declared per
row only when the gap is within 5 % of a reliable floor or when every
candidate lever measured on that row closed within run noise (+-0.5 %).
Skewed rows whose occupied-expert count is not resolved are reported as
`open (floor unresolved)`, never as converged.

Protocol, tolerances and the FlashInfer baseline (revision
`ac7bce13ea0ff76392fd17aa696b096e191d0825`, fresh autotune) are
unchanged from the previous update: symmetric external CUDA graphs,
CUPTI activity timing with cold L2, three counterbalanced groups, 1000
ms per arm/group, all-element BF16 atol 1.0 / rtol 0.1 with exact
intermediates, independent CPU-side audit of every raw receipt,
compute-sanitizer synccheck / racecheck (memcheck where stores change).

| Rows | Count | Export faster than FlashInfer | Source / Export geomean
| FlashInfer / Export geomean | Original export / Export geomean |
Ceiling-model gap geomean (reliable floors) | Convergence (a) / (b) /
open |
|---|---:|---:|---:|---:|---:|---:|---|
| B200 (sm_100a) | 26 | 26/26 | 0.999719x | 1.104873x | 1.265175x |
1.559x | 0 / 0 / 26 |
| B300 (sm_103a) | 26 | 26/26 | 0.999057x | 1.103906x | 1.244305x |
1.545x | 0 / 0 / 26 |
| uniform routing | 26 | 26/26 | 0.999145x | 1.091969x | 1.210341x |
1.454x | 0 / 0 / 26 |
| skewed routing | 26 | 26/26 | 0.999631x | 1.116952x | 1.300678x |
1.656x | 0 / 0 / 26 |
| all rows | 52 | 52/52 | 0.999388x | 1.104390x | 1.254697x | 1.552x | 0
/ 0 / 52 |

### B200 (sm_100a)

| Shape | Hardware | Export us | Source us | FlashInfer us | FlashInfer
/ Export | Source / Export | Original export / Export | Physical s |
Sampled GPU s (source / export / FlashInfer) | Floor us | Ceiling-model
gap | Convergence |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|---|
| sm_100a_m00001_uniform | B200 | 23.104 | 22.913 | 24.224 | 1.048476x |
0.991733x | 1.391923x | 2177.8 | 3.706 / 3.743 / 3.903 | 5.1 | 4.565x |
open (1 lever) |
| sm_100a_m00001_skew | B200 | 23.072 | 23.009 | 24.288 | 1.052705x |
0.997269x | 1.424411x | 2093.4 | 3.719 / 3.732 / 3.916 | 5.1 | 4.559x |
open (1 lever) |
| sm_100a_m00008_uniform | B200 | 73.151 | 73.247 | 77.760 | 1.063007x |
1.001312x | 1.238411x | 930.3 | 3.754 / 3.750 / 3.982 | 40.5 | 1.807x |
open (2 levers) |
| sm_100a_m00008_skew | B200 | 48.608 | 48.704 | 52.640 | 1.082949x |
1.001975x | 1.350210x | 1238.2 | 3.750 / 3.746 / 4.051 | 20.4 | 2.383x |
open (2 levers) |
| sm_100a_m00016_uniform | B200 | 121.504 | 121.568 | 125.567 |
1.033439x | 1.000527x | 1.113774x | 707.6 | 3.754 / 3.750 / 3.874 | 81.0
| 1.501x | open (2 levers) |
| sm_100a_m00016_skew | B200 | 62.496 | 62.528 | 66.656 | 1.066564x |
1.000512x | 1.374312x | 1058.4 | 3.744 / 3.743 / 3.993 | 30.7 | 2.033x |
open (2 levers) |
| sm_100a_m00032_uniform | B200 | 206.689 | 206.689 | 210.304 |
1.017490x | 1.000000x | 1.121530x | 652.4 | 3.752 / 3.752 / 3.817 |
161.9 | 1.276x | open (1 lever) |
| sm_100a_m00032_skew | B200 | 90.368 | 90.528 | 95.839 | 1.060541x |
1.001771x | 1.517705x | 978.6 | 3.737 / 3.732 / 3.957 | 51.5 | 1.756x |
open (1 lever) |
| sm_100a_m00064_uniform | B200 | 332.992 | 333.024 | 340.479 |
1.022484x | 1.000096x | 1.119742x | 551.0 | 3.752 / 3.752 / 3.835 |
283.7 | 1.174x | open (1 lever) |
| sm_100a_m00064_skew | B200 | 145.439 | 145.440 | 154.367 | 1.061387x |
1.000007x | 1.479438x | 797.2 | 3.742 / 3.742 / 3.971 | 102.9 | 1.413x |
open (1 lever) |
| sm_100a_m00128_uniform | B200 | 336.800 | 336.607 | 346.207 |
1.027931x | 0.999427x | 1.145748x | 559.1 | 3.760 / 3.762 / 3.866 |
286.1 | 1.177x | open (1 lever) |
| sm_100a_m00128_skew | B200 | 231.264 | 231.295 | 239.871 | 1.037217x |
1.000134x | 1.371939x | 628.2 | 3.747 / 3.748 / 3.885 | 195.8 | 1.181x |
open (1 lever) |
| sm_100a_m00256_uniform | B200 | 340.929 | 340.928 | 349.760 |
1.025903x | 0.999997x | 1.190444x | 426.1 | 3.753 / 3.753 / 3.849 |
291.1 | 1.171x | open (1 lever) |
| sm_100a_m00256_skew | B200 | 363.457 | 363.297 | 373.216 | 1.026850x |
0.999560x | 1.214999x | 405.3 | 3.750 / 3.752 / 3.849 | 291.1 | 1.249x |
open (1 lever) |
| sm_100a_m00512_uniform | B200 | 348.479 | 348.352 | 361.727 |
1.038017x | 0.999636x | 1.265568x | 412.5 | 3.753 / 3.754 / 3.898 |
301.0 | 1.158x | open (2 levers) |
| sm_100a_m00512_skew | B200 | 375.296 | 375.264 | 385.568 | 1.027370x |
0.999915x | 1.285726x | 408.3 | 3.753 / 3.754 / 3.855 | 301.0 | 1.247x |
open (2 levers) |
| sm_100a_m01024_uniform | B200 | 381.408 | 381.152 | 387.168 |
1.015102x | 0.999329x | 1.275778x | 396.2 | 3.752 / 3.755 / 3.812 |
320.7 | 1.189x | open (3 levers) |
| sm_100a_m01024_skew | B200 | 441.153 | 440.864 | 449.089 | 1.017989x |
0.999345x | 1.303858x | 385.7 | 3.757 / 3.759 / 3.826 | 320.7 | 1.376x |
open (3 levers) |
| sm_100a_m02048_uniform | B200 | 443.423 | 443.168 | 454.367 |
1.024681x | 0.999425x | 1.262253x | 532.3 | 3.793 / 3.796 / 3.890 |
360.2 | 1.231x | open (2 levers) |
| sm_100a_m02048_skew | B200 | 509.664 | 509.247 | 529.281 | 1.038489x |
0.999182x | 1.229298x | 498.6 | 3.857 / 3.860 / 4.009 | 360.2 | 1.415x |
open (2 levers) |
| sm_100a_m04096_uniform | B200 | 540.480 | 539.953 | 558.784 |
1.033866x | 0.999026x | 1.229842x | 492.4 | 3.879 / 3.883 / 4.015 |
439.2 | 1.231x | open (3 levers) |
| sm_100a_m04096_skew | B200 | 650.799 | 650.527 | 660.991 | 1.015660x |
0.999582x | 1.235748x | 512.0 | 3.848 / 3.850 / 3.913 | 439.2 | 1.482x |
open (3 levers) |
| sm_100a_m08192_uniform | B200 | 934.476 | 935.083 | 1339.673 |
1.433610x | 1.000651x | 1.246681x | 542.4 | 3.970 / 3.968 / 5.680 |
597.0 | 1.565x | open (4 levers) |
| sm_100a_m08192_skew | B200 | 917.241 | 917.177 | 1689.587 | 1.842032x
| 0.999930x | 1.201657x | 529.1 | 3.834 / 3.835 / 7.062 | 597.0 | 1.536x
| open (5 levers) |
| sm_100a_m16384_uniform | B200 | 1525.078 | 1528.646 | 2345.392 |
1.537883x | 1.002339x | 1.238526x | 517.8 | 4.008 / 4.004 / 6.148 |
912.8 | 1.671x | open (5 levers) |
| sm_100a_m16384_skew | B200 | 1515.210 | 1515.305 | 2199.095 |
1.451347x | 1.000063x | 1.175253x | 666.6 | 3.964 / 3.964 / 5.755 |
912.8 | 1.660x | open (5 levers) |

### B300 (sm_103a)

| Shape | Hardware | Export us | Source us | FlashInfer us | FlashInfer
/ Export | Source / Export | Original export / Export | Physical s |
Sampled GPU s (source / export / FlashInfer) | Floor us | Ceiling-model
gap | Convergence |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|---:|---:|---|
| sm_103a_m00001_uniform | B300 | 22.336 | 22.113 | 23.136 | 1.035817x |
0.990016x | 1.435530x | 2503.7 | 3.674 / 3.716 / 3.831 | 5.1 | 4.413x |
open (1 lever) |
| sm_103a_m00001_skew | B300 | 22.464 | 22.528 | 23.425 | 1.042780x |
1.002849x | 1.340500x | 2374.3 | 3.731 / 3.721 / 3.883 | 5.1 | 4.439x |
open (1 lever) |
| sm_103a_m00008_uniform | B300 | 73.665 | 73.664 | 79.232 | 1.075572x |
0.999986x | 1.197217x | 943.9 | 3.772 / 3.773 / 4.057 | 40.5 | 1.820x |
open (2 levers) |
| sm_103a_m00008_skew | B300 | 48.992 | 48.865 | 51.488 | 1.050947x |
0.997408x | 1.269126x | 1216.4 | 3.740 / 3.747 / 3.946 | 20.4 | 2.402x |
open (2 levers) |
| sm_103a_m00016_uniform | B300 | 123.937 | 123.777 | 127.457 |
1.028402x | 0.998709x | 1.104061x | 710.6 | 3.758 / 3.763 / 3.869 | 81.0
| 1.531x | open (2 levers) |
| sm_103a_m00016_skew | B300 | 63.426 | 63.201 | 67.425 | 1.063050x |
0.996453x | 1.334989x | 1099.5 | 3.744 / 3.757 / 3.993 | 30.7 | 2.063x |
open (2 levers) |
| sm_103a_m00032_uniform | B300 | 208.642 | 208.450 | 214.275 |
1.026998x | 0.999080x | 1.118102x | 606.1 | 3.753 / 3.756 / 3.858 |
161.9 | 1.288x | open (1 lever) |
| sm_103a_m00032_skew | B300 | 90.784 | 90.689 | 95.201 | 1.048654x |
0.998954x | 1.470931x | 1035.3 | 3.746 / 3.751 / 3.932 | 51.5 | 1.764x |
open (1 lever) |
| sm_103a_m00064_uniform | B300 | 337.060 | 337.220 | 347.876 |
1.032089x | 1.000475x | 1.106049x | 507.6 | 3.752 / 3.748 / 3.869 |
283.7 | 1.188x | open (1 lever) |
| sm_103a_m00064_skew | B300 | 145.538 | 145.665 | 155.970 | 1.071679x |
1.000873x | 1.463714x | 753.2 | 3.755 / 3.753 / 4.021 | 102.9 | 1.414x |
open (1 lever) |
| sm_103a_m00128_uniform | B300 | 340.643 | 340.675 | 350.819 |
1.029873x | 1.000094x | 1.130392x | 471.8 | 3.751 / 3.751 / 3.863 |
286.1 | 1.190x | open (1 lever) |
| sm_103a_m00128_skew | B300 | 233.250 | 233.250 | 256.131 | 1.098096x |
1.000000x | 1.344772x | 522.6 | 3.752 / 3.752 / 4.120 | 195.8 | 1.192x |
open (1 lever) |
| sm_103a_m00256_uniform | B300 | 346.947 | 347.043 | 358.084 |
1.032100x | 1.000277x | 1.174050x | 477.7 | 3.754 / 3.753 / 3.873 |
291.1 | 1.192x | open (1 lever) |
| sm_103a_m00256_skew | B300 | 369.316 | 369.092 | 378.628 | 1.025214x |
0.999393x | 1.189066x | 512.9 | 3.752 / 3.754 / 3.849 | 291.1 | 1.269x |
open (1 lever) |
| sm_103a_m00512_uniform | B300 | 354.596 | 354.532 | 369.316 |
1.041512x | 0.999820x | 1.242036x | 439.5 | 3.751 / 3.752 / 3.907 |
301.0 | 1.178x | open (2 levers) |
| sm_103a_m00512_skew | B300 | 380.675 | 380.452 | 393.475 | 1.033624x |
0.999414x | 1.261774x | 406.3 | 3.754 / 3.756 / 3.883 | 301.0 | 1.265x |
open (2 levers) |
| sm_103a_m01024_uniform | B300 | 387.204 | 386.980 | 396.132 |
1.023058x | 0.999421x | 1.234876x | 429.0 | 3.750 / 3.752 / 3.839 |
320.7 | 1.207x | open (3 levers) |
| sm_103a_m01024_skew | B300 | 443.364 | 443.205 | 456.549 | 1.029739x |
0.999641x | 1.282502x | 406.5 | 3.749 / 3.751 / 3.864 | 320.7 | 1.383x |
open (3 levers) |
| sm_103a_m02048_uniform | B300 | 441.638 | 440.774 | 449.990 |
1.018911x | 0.998044x | 1.226649x | 450.5 | 3.758 / 3.765 / 3.837 |
360.2 | 1.226x | open (2 levers) |
| sm_103a_m02048_skew | B300 | 496.645 | 495.909 | 503.141 | 1.013080x |
0.998518x | 1.213921x | 439.9 | 3.752 / 3.757 / 3.807 | 360.2 | 1.379x |
open (2 levers) |
| sm_103a_m04096_uniform | B300 | 524.199 | 523.143 | 531.752 |
1.014409x | 0.997985x | 1.188633x | 451.9 | 3.775 / 3.783 / 3.839 |
439.2 | 1.194x | open (3 levers) |
| sm_103a_m04096_skew | B300 | 635.494 | 634.533 | 639.653 | 1.006545x |
0.998488x | 1.195382x | 433.3 | 3.760 / 3.766 / 3.791 | 439.2 | 1.447x |
open (3 levers) |
| sm_103a_m08192_uniform | B300 | 851.946 | 852.010 | 1220.557 |
1.432669x | 1.000075x | 1.284381x | 458.1 | 3.798 / 3.797 / 5.422 |
597.0 | 1.427x | open (4 levers) |
| sm_103a_m08192_skew | B300 | 880.616 | 880.712 | 1606.573 | 1.824374x
| 1.000109x | 1.209243x | 507.4 | 3.758 / 3.758 / 6.855 | 597.0 | 1.475x
| open (5 levers) |
| sm_103a_m16384_uniform | B300 | 1399.250 | 1399.794 | 2176.062 |
1.555163x | 1.000389x | 1.256942x | 436.8 | 3.871 / 3.871 / 6.017 |
912.8 | 1.533x | open (5 levers) |
| sm_103a_m16384_skew | B300 | 1428.883 | 1427.571 | 2020.059 |
1.413732x | 0.999081x | 1.177104x | 433.9 | 3.801 / 3.805 / 5.385 |
912.8 | 1.565x | open (5 levers) |

Latencies are whole-call medians in microseconds; physical seconds are
the wall time of the row's isolated measurement step; sampled GPU
seconds are the CUPTI per-arm span sums of the reportable samples.

Evidence: every row in the tables above is the median of its own sealed
measurement step (prepare, correctness rounds, conditioning, five timed
arms) followed by an independent CPU-side audit of the raw receipt; the
per-row receipts and sanitizer logs are retained in the measurement
archive.

No increment has landed since the previous update: every row shows the
measurement of the export as shipped at this head, and no kernel, route
or host file changed. This revision refreshes only the floor and gap
columns: the 24 rows whose floor was previously interpolated from
neighbouring rows now have their own per-stage attribution run, and the
eight rows whose realization changed in the last two updates were
re-attributed on the shipped realization; the whole-table gap geomean
moves from 1.601x to 1.552x because measured floors on the M2048/M8192
rows sit above their analytic lower bounds. Convergence is unchanged at
0/52: no row is within 5 % of its floor (rule (a)) and every row still
has at least one open lever (rule (b)). Structural levers are under
evaluation; no accepted increment yet. Rows marked `open` list the count
of candidate levers not yet measured on that row; each will be replaced
only after its full ladder (prepare, synccheck, racecheck, memcheck
where stores change, sealed five-arm timer, independent CPU audit).

## Baselines and their source PRs

- FlashInfer baseline arm:
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe` (trtllm-gen
NVFP4 block-scale routed MoE, TP8-local shapes, fresh autotune) at
revision `ac7bce13ea0ff76392fd17aa696b096e191d0825` (2026-09-11, #4784
is the commit at that revision). Implementation files at that revision:
`flashinfer/fused_moe/core.py`,
`csrc/trtllm_fused_moe_kernel_launcher.cu`,
`csrc/trtllm_fused_moe_runner.cu`,
`csrc/trtllm_fused_moe_routing_binding.cu`,
`csrc/fused_moe/trtllm_backend/*`,
`flashinfer/tuning_configs/v0_1_trtllm_fused_moe_NVIDIA_B200.py`.
- Origin PRs of that baseline path: #1212 (bd74e15c, 2025-07-10,
trtllm-gen FP8 MoE kernels), #1214 (96801b2c, 2025-07-16, SM100
low-latency NVFP4 kernels), #1272 (39d81f77, 2025-07-18, shuffle-matrix
flag), #1475 (f1fd5c6b, 2025-08-19, trtllm-gen FP4 MoE autotuner), #1573
(8ce1b089, 2025-08-27, FP4 autotuner and routing update), #1548
(375a26b6, 2025-09-05, split-K and autotuner fix), #1882 (30314c3a,
2025-10-10, FP4 throughput batched GEMMs), #3861 (3a75b4e3, 2026-09-04,
autotuner v2 used by the fresh-autotune arm), #4797 (b41735dc,
2026-09-02, per-call launch state).
- Test oracle of the baseline: `tests/moe/test_trtllm_gen_fused_moe.py`
(reorganised in #1778, fb4293f7, 2025-09-29). This backend's own tests:
`tests/moe/test_cake_kimi_k3_situ.py`.
- Branch merge-base with `main`:
`653d211e8e706d94db854a80d375d0affd95e611`. Upstream commits between the
measured baseline revision and that merge-base that touch the baseline
path: #5281 (476f7bbd, PDL for intermediate quantization), #5207
(7281e687, restore missing trtllm MoE tactics), #4894 (7554a6ed), #4943
(10f7e147), #5096 (cd5e09ca), #4361 (c05407ce). The tables compare
against the fixed revision `ac7bce13` only; the baseline arm was not
re-measured at the merge-base, so any effect of those commits on the
FlashInfer numbers is not reflected here.

## Per-shape results

Latencies are whole-call medians in microseconds. Physical seconds are
the wall time of the row's isolated measurement step (prepare,
correctness rounds, conditioning and the four timed arms); sampled GPU
seconds are the CUPTI per-arm span sums of the reportable samples (mean
duration x sample count), excluding warmup, restoration and
preconditioning.

### B200 (sm_100a)

| Shape | Hardware | Export us | Source us | FlashInfer us | FlashInfer
/ Export | Source / Export | Original export / Export | Physical s |
Sampled GPU s (source / export / FlashInfer) |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|
| sm_100a_m00001_uniform | B200 | 23.104 | 22.913 | 24.224 | 1.048476x |
0.991733x | 1.391923x | 2177.8 | 3.706 / 3.743 / 3.903 |
| sm_100a_m00001_skew | B200 | 23.072 | 23.009 | 24.288 | 1.052705x |
0.997269x | 1.424411x | 2093.4 | 3.719 / 3.732 / 3.916 |
| sm_100a_m00008_uniform | B200 | 73.151 | 73.247 | 77.760 | 1.063007x |
1.001312x | 1.238411x | 930.3 | 3.754 / 3.750 / 3.982 |
| sm_100a_m00008_skew | B200 | 48.608 | 48.704 | 52.640 | 1.082949x |
1.001975x | 1.350210x | 1238.2 | 3.750 / 3.746 / 4.051 |
| sm_100a_m00016_uniform | B200 | 121.504 | 121.568 | 125.567 |
1.033439x | 1.000527x | 1.113774x | 707.6 | 3.754 / 3.750 / 3.874 |
| sm_100a_m00016_skew | B200 | 62.496 | 62.528 | 66.656 | 1.066564x |
1.000512x | 1.374312x | 1058.4 | 3.744 / 3.743 / 3.993 |
| sm_100a_m00032_uniform | B200 | 206.689 | 206.689 | 210.304 |
1.017490x | 1.000000x | 1.121530x | 652.4 | 3.752 / 3.752 / 3.817 |
| sm_100a_m00032_skew | B200 | 90.368 | 90.528 | 95.839 | 1.060541x |
1.001771x | 1.517705x | 978.6 | 3.737 / 3.732 / 3.957 |
| sm_100a_m00064_uniform | B200 | 332.992 | 333.024 | 340.479 |
1.022484x | 1.000096x | 1.119742x | 551.0 | 3.752 / 3.752 / 3.835 |
| sm_100a_m00064_skew | B200 | 145.439 | 145.440 | 154.367 | 1.061387x |
1.000007x | 1.479438x | 797.2 | 3.742 / 3.742 / 3.971 |
| sm_100a_m00128_uniform | B200 | 336.800 | 336.607 | 346.207 |
1.027931x | 0.999427x | 1.145748x | 559.1 | 3.760 / 3.762 / 3.866 |
| sm_100a_m00128_skew | B200 | 231.264 | 231.295 | 239.871 | 1.037217x |
1.000134x | 1.371939x | 628.2 | 3.747 / 3.748 / 3.885 |
| sm_100a_m00256_uniform | B200 | 340.929 | 340.928 | 349.760 |
1.025903x | 0.999997x | 1.190444x | 426.1 | 3.753 / 3.753 / 3.849 |
| sm_100a_m00256_skew | B200 | 363.457 | 363.297 | 373.216 | 1.026850x |
0.999560x | 1.214999x | 405.3 | 3.750 / 3.752 / 3.849 |
| sm_100a_m00512_uniform | B200 | 348.479 | 348.352 | 361.727 |
1.038017x | 0.999636x | 1.265568x | 412.5 | 3.753 / 3.754 / 3.898 |
| sm_100a_m00512_skew | B200 | 375.296 | 375.264 | 385.568 | 1.027370x |
0.999915x | 1.285726x | 408.3 | 3.753 / 3.754 / 3.855 |
| sm_100a_m01024_uniform | B200 | 381.408 | 381.152 | 387.168 |
1.015102x | 0.999329x | 1.275778x | 396.2 | 3.752 / 3.755 / 3.812 |
| sm_100a_m01024_skew | B200 | 441.153 | 440.864 | 449.089 | 1.017989x |
0.999345x | 1.303858x | 385.7 | 3.757 / 3.759 / 3.826 |
| sm_100a_m02048_uniform | B200 | 443.423 | 443.168 | 454.367 |
1.024681x | 0.999425x | 1.262253x | 532.3 | 3.793 / 3.796 / 3.890 |
| sm_100a_m02048_skew | B200 | 509.664 | 509.247 | 529.281 | 1.038489x |
0.999182x | 1.229298x | 498.6 | 3.857 / 3.860 / 4.009 |
| sm_100a_m04096_uniform | B200 | 540.480 | 539.953 | 558.784 |
1.033866x | 0.999026x | 1.229842x | 492.4 | 3.879 / 3.883 / 4.015 |
| sm_100a_m04096_skew | B200 | 650.799 | 650.527 | 660.991 | 1.015660x |
0.999582x | 1.235748x | 512.0 | 3.848 / 3.850 / 3.913 |
| sm_100a_m08192_uniform | B200 | 934.476 | 935.083 | 1339.673 |
1.433610x | 1.000651x | 1.246681x | 542.4 | 3.970 / 3.968 / 5.680 |
| sm_100a_m08192_skew | B200 | 917.241 | 917.177 | 1689.587 | 1.842032x
| 0.999930x | 1.201657x | 529.1 | 3.834 / 3.835 / 7.062 |
| sm_100a_m16384_uniform | B200 | 1525.078 | 1528.646 | 2345.392 |
1.537883x | 1.002339x | 1.238526x | 517.8 | 4.008 / 4.004 / 6.148 |
| sm_100a_m16384_skew | B200 | 1515.210 | 1515.305 | 2199.095 |
1.451347x | 1.000063x | 1.175253x | 666.6 | 3.964 / 3.964 / 5.755 |

### B300 (sm_103a)

| Shape | Hardware | Export us | Source us | FlashInfer us | FlashInfer
/ Export | Source / Export | Original export / Export | Physical s |
Sampled GPU s (source / export / FlashInfer) |
|---|---|---:|---:|---:|---:|---:|---:|---:|---|
| sm_103a_m00001_uniform | B300 | 22.336 | 22.113 | 23.136 | 1.035817x |
0.990016x | 1.435530x | 2503.7 | 3.674 / 3.716 / 3.831 |
| sm_103a_m00001_skew | B300 | 22.464 | 22.528 | 23.425 | 1.042780x |
1.002849x | 1.340500x | 2374.3 | 3.731 / 3.721 / 3.883 |
| sm_103a_m00008_uniform | B300 | 73.665 | 73.664 | 79.232 | 1.075572x |
0.999986x | 1.197217x | 943.9 | 3.772 / 3.773 / 4.057 |
| sm_103a_m00008_skew | B300 | 48.992 | 48.865 | 51.488 | 1.050947x |
0.997408x | 1.269126x | 1216.4 | 3.740 / 3.747 / 3.946 |
| sm_103a_m00016_uniform | B300 | 123.937 | 123.777 | 127.457 |
1.028402x | 0.998709x | 1.104061x | 710.6 | 3.758 / 3.763 / 3.869 |
| sm_103a_m00016_skew | B300 | 63.426 | 63.201 | 67.425 | 1.063050x |
0.996453x | 1.334989x | 1099.5 | 3.744 / 3.757 / 3.993 |
| sm_103a_m00032_uniform | B300 | 208.642 | 208.450 | 214.275 |
1.026998x | 0.999080x | 1.118102x | 606.1 | 3.753 / 3.756 / 3.858 |
| sm_103a_m00032_skew | B300 | 90.784 | 90.689 | 95.201 | 1.048654x |
0.998954x | 1.470931x | 1035.3 | 3.746 / 3.751 / 3.932 |
| sm_103a_m00064_uniform | B300 | 337.060 | 337.220 | 347.876 |
1.032089x | 1.000475x | 1.106049x | 507.6 | 3.752 / 3.748 / 3.869 |
| sm_103a_m00064_skew | B300 | 145.538 | 145.665 | 155.970 | 1.071679x |
1.000873x | 1.463714x | 753.2 | 3.755 / 3.753 / 4.021 |
| sm_103a_m00128_uniform | B300 | 340.643 | 340.675 | 350.819 |
1.029873x | 1.000094x | 1.130392x | 471.8 | 3.751 / 3.751 / 3.863 |
| sm_103a_m00128_skew | B300 | 233.250 | 233.250 | 256.131 | 1.098096x |
1.000000x | 1.344772x | 522.6 | 3.752 / 3.752 / 4.120 |
| sm_103a_m00256_uniform | B300 | 346.947 | 347.043 | 358.084 |
1.032100x | 1.000277x | 1.174050x | 477.7 | 3.754 / 3.753 / 3.873 |
| sm_103a_m00256_skew | B300 | 369.316 | 369.092 | 378.628 | 1.025214x |
0.999393x | 1.189066x | 512.9 | 3.752 / 3.754 / 3.849 |
| sm_103a_m00512_uniform | B300 | 354.596 | 354.532 | 369.316 |
1.041512x | 0.999820x | 1.242036x | 439.5 | 3.751 / 3.752 / 3.907 |
| sm_103a_m00512_skew | B300 | 380.675 | 380.452 | 393.475 | 1.033624x |
0.999414x | 1.261774x | 406.3 | 3.754 / 3.756 / 3.883 |
| sm_103a_m01024_uniform | B300 | 387.204 | 386.980 | 396.132 |
1.023058x | 0.999421x | 1.234876x | 429.0 | 3.750 / 3.752 / 3.839 |
| sm_103a_m01024_skew | B300 | 443.364 | 443.205 | 456.549 | 1.029739x |
0.999641x | 1.282502x | 406.5 | 3.749 / 3.751 / 3.864 |
| sm_103a_m02048_uniform | B300 | 441.638 | 440.774 | 449.990 |
1.018911x | 0.998044x | 1.226649x | 450.5 | 3.758 / 3.765 / 3.837 |
| sm_103a_m02048_skew | B300 | 496.645 | 495.909 | 503.141 | 1.013080x |
0.998518x | 1.213921x | 439.9 | 3.752 / 3.757 / 3.807 |
| sm_103a_m04096_uniform | B300 | 524.199 | 523.143 | 531.752 |
1.014409x | 0.997985x | 1.188633x | 451.9 | 3.775 / 3.783 / 3.839 |
| sm_103a_m04096_skew | B300 | 635.494 | 634.533 | 639.653 | 1.006545x |
0.998488x | 1.195382x | 433.3 | 3.760 / 3.766 / 3.791 |
| sm_103a_m08192_uniform | B300 | 851.946 | 852.010 | 1220.557 |
1.432669x | 1.000075x | 1.284381x | 458.1 | 3.798 / 3.797 / 5.422 |
| sm_103a_m08192_skew | B300 | 880.616 | 880.712 | 1606.573 | 1.824374x
| 1.000109x | 1.209243x | 507.4 | 3.758 / 3.758 / 6.855 |
| sm_103a_m16384_uniform | B300 | 1399.250 | 1399.794 | 2176.062 |
1.555163x | 1.000389x | 1.256942x | 436.8 | 3.871 / 3.871 / 6.017 |
| sm_103a_m16384_skew | B300 | 1428.883 | 1427.571 | 2020.059 |
1.413732x | 0.999081x | 1.177104x | 433.9 | 3.801 / 3.805 / 5.385 |

## Durations

| Rows | Count | Physical s (sum of row measurement steps) | Sampled GPU
s: source | export | FlashInfer | original export |
|---|---:|---:|---:|---:|---:|---:|
| B200 (sm_100a) | 26 | 19097.538 | 98.590 | 98.638 | 110.612 | 121.847
|
| B300 (sm_103a) | 26 | 19028.678 | 97.712 | 97.809 | 109.408 | 117.008
|
| all rows | 52 | 38126.216 | 196.302 | 196.447 | 220.021 | 238.855 |

Per measurement unit (each unit is one isolated GPU step per row on
session-owned devices; nested physical/benchmark/sampled scopes overlap
and are not additive):

| Measurement unit | Hardware | Rows | Physical s | Benchmark s |
Sampled GPU s: source | export | FlashInfer | original export |
|---|---|---:|---:|---:|---:|---:|---:|---:|
| B200 M1/M8/M16 (uniform+skew) | B200 | 6 | 8205.666 | 5989.038 |
22.427 | 22.465 | 23.719 | 28.764 |
| B200 M32/M64/M128 (uniform+skew) | B200 | 6 | 4166.509 | 1875.230 |
22.490 | 22.488 | 23.332 | 28.754 |
| B200 M256 (uniform+skew) | B200 | 2 | 831.423 | 284.298 | 7.503 |
7.505 | 7.698 | 9.046 |
| B200 M2048/M4096 (uniform+skew) | B200 | 4 | 2035.407 | 414.276 |
15.377 | 15.388 | 15.827 | 19.460 |
| B200 M8192/M16384 (uniform+skew) | B200 | 4 | 2255.874 | 378.085 |
15.777 | 15.771 | 24.646 | 16.603 |
| B300 M1/M8/M16 (uniform+skew) | B300 | 6 | 8848.386 | 6985.787 |
22.420 | 22.478 | 23.579 | 28.936 |
| B300 M32/M64/M128/M256 (uniform+skew) | B300 | 8 | 4887.238 | 2365.794
| 30.014 | 30.018 | 31.385 | 37.610 |
| B300 M2048/M4096 (uniform+skew) | B300 | 4 | 1775.523 | 432.136 |
15.045 | 15.072 | 15.274 | 15.657 |
| B300 M8192/M16384 (uniform+skew) | B300 | 4 | 1836.159 | 371.790 |
15.228 | 15.230 | 23.677 | 15.870 |
| B200 + B300 M512/M1024 (mixed) | B300+B200 | 8 | 3284.031 | 1102.361 |
30.020 | 30.032 | 30.884 | 38.156 |

## Correctness totals over the final measurement units

| Hardware | tensor checks | BF16 elements | exact elements | FI
canonical checks | routing checks | workfeed counter checks | allocation
probes |
|---|---:|---:|---:|---:|---:|---:|---:|
| B200 | 2,870 | 7,419,238,400 | 9,960,681,600 | 88 | 3,420 | 150 | 76 |
| B200 + B300 (M512/M1024 unit) | 880 | 572,522,496 | 739,639,296 | 32 |
1,080 | 80 | 24 |
| B300 | 2,960 | 7,435,753,472 | 9,985,896,576 | 88 | 3,510 | 160 | 78 |
| Combined | 6,710 | 15,427,514,368 | 20,686,217,472 | 208 | 8,010 | 390
| 178 |

Zero mismatches in every unit. Every row's prepare, synccheck, racecheck
and timer step is followed by an independent CPU-side audit of the raw
receipts.

## Hardware

- `NVIDIA B200`: 12 device UUID(s):
`1a7f9ffc-bf1e-ff95-60d8-c49720b8707a`,
`29653327-a4f7-908e-5dea-c561db58021f`,
`35476463-8c91-8819-0bd6-330985d7a543`,
`47212bdc-0600-61cd-e362-267db412ef15`,
`477dd790-fa89-2f0c-cace-b7329b309237`,
`69e90ca0-0d47-6ea5-ccbd-0c2ad865c0e4`,
`6be3be98-1386-fc1a-2d2f-97b841cd74fc`,
`72185052-b15f-1cd5-e0e9-f561d04bb990`,
`7724dc25-bbe5-1707-265a-4725655dda83`,
`a273c7b7-081d-9217-e3f4-8328bed281de`,
`c915a50d-1eb3-a004-ae41-d839b2c622e3`,
`eeb0b415-07db-62d1-b0c8-2e6b62be22f7`
- `NVIDIA B300 SXM6 AC`: 13 device UUID(s):
`0d72d081-b1df-3dd7-3976-cc48729d38ff`,
`1f676c6c-d48a-b37e-27b0-132aab03cf03`,
`330ea697-3b25-df40-5bbc-9bcf3dc2e0ea`,
`56510b39-a3ef-d03a-89ce-c6c7fe229100`,
`75e5e6e6-0a83-22b1-7fd4-5a8164a4a8a7`,
`88fd91da-b105-72e8-a448-24b5280d4385`,
`8dba321e-daba-73c3-0cf2-55c64a8c5707`,
`9cde7a68-49e4-4e65-e473-bace41ea98b0`,
`b1e1ab54-48f7-708f-43bd-c549f2f78ab9`,
`c83925bb-ed5f-611a-f17e-3ce5e1685f23`,
`da741ac6-e0f7-6347-3e9c-2d86e37ab091`,
`e29dabc5-633e-bb2c-f58c-bbf4505c81f4`,
`ed6b9822-9d64-faa2-bac2-93fd1eecae6e`

Target revision: `ac7bce13ea0ff76392fd17aa696b096e191d0825`. Benchmark
execution: `symmetric_external_cuda_graph`; 3 counterbalanced groups,
100.000 ms warmup and 1000.000 ms reportable budget per arm/group.

Related:
[4254](https://github.com/flashinfer-ai/flashinfer/issues/4254),
[4568](https://github.com/flashinfer-ai/flashinfer/issues/4568).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [823e46c](https://github.com/flashinfer-ai/flashinfer/commit/823e46c15cb9943027c5e6e2c5819a8fadd28d18)

- **作者**: eigen
- **时间**: 2026-09-29T22:54:58Z
- **提交信息**: perf(cake_comm): converge the SM100/SM103 MoE all-reduce fusion union programs (world sizes 2/4/8) (#5694)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on **every one of
the 60 benchmark rows** (SM100 and SM103, world sizes 2/4/8) against
upstream `backend="trtllm"`, the isolated Cake bundle and the currently
shipped union programs; rows whose program is unchanged measure at
parity.

<!-- .github/pull_request_template.md -->

## 📌 Description

Convergence round for the Cake TRT-LLM MoE all-reduce fusion union
programs (`trtllm_moe_allreduce_fusion(backend="cake")`, SM100 and
SM103, world sizes 2/4/8; #5650 on top of #5599). Every adopted change
keeps the Lamport clear/publish/poll protocol, the flag and
workspace layout, the FlashInfer API contract and the arithmetic (fp32
accumulation, same reduction order) unchanged: **every adopted
program produces bitwise-identical outputs to the shipped program it
replaces**. The public API is unchanged; calls without the
all-reduce output and every other architecture keep the isolated bundle
from #4730.

1. **Pipelined publish / poll** (`pipe1_u4_b5`, `pipe2_u4_b5`,
`pipe2_u4`): inside the persistent loop each cluster publishes token
`j + D` before it polls token `j` (`D` = 1 or 2), on the wide body with
the four-wide expert unroll. Each token is still published
before it is polled, the previous epoch is still cleared first, and
every cluster of the grid is co-resident (the generator checks
`cuOccupancyMaxActiveClusters` on the export node). `_b5` pins the entry
register count to 56 through `__launch_bounds__(224, 5)`
so five CTAs per SM are admissible where the uncapped pipelined body
would hold two or three. Selected for the nine T=2048 rows of
each architecture (`pipe1_u4_b5` / `pipe2_u4_b5`) and, as `pipe2_u4`,
for the SM100 two-rank bfloat16 PDL T=256 E=12 row
(1.02x-1.16x in the paired probe; the other T=256 rows lost or tied and
keep their program).
2. **Co-resident cluster cap** (`launch.max_persistent_clusters`): the
persistent grid of a module is `min(sm_count x k, cap x 4, T x 4)`
CTAs, where `cap` is the driver's `cuOccupancyMaxActiveClusters` answer
for that module recorded by the generator (175 clusters for the
56-register pipelined bodies on both architectures; `None` for every
other module). The 18 T=2048 rows hold five CTAs per SM on 175
co-resident clusters (700 CTAs) instead of four per SM on 148 (592
CTAs): 1.03x-1.07x over the four-per-SM grid of the same program,
bitwise identical. Every cluster of the grid stays co-resident (each
cluster publishes all of its tokens before it polls); the
generator re-checks the recorded cap against the driver on the export
node, and the loader never raises either recorded value.
3. **Push-style RMS partial exchange on the generic body** (`push_g`):
one cluster barrier instead of two plus a block barrier and
serialized peer reads, same fp32 partial order. SM103 eight-rank T in
{64, 128} and the bfloat16 PDL T=256 E=12 row (1.01x-1.02x);
the SM103 eight-rank bfloat16 no-PDL T=256 E=8 row runs the pipelined
body at three CTAs per SM (1.03x).
4. **Clear-first wide body** (`clrfirst`) for the SM100 four-rank
bfloat16 no-PDL T=128 E=16 row (1.05x).
5. **Launch rules**: the SM100 eight-rank `sm100_ws8_mid` rows (T in
{64, 128}) run four CTAs per SM, i.e. one cluster per token instead
of a 37-cluster persistent loop (1.18x at T=128, 1.05x at T=64); the
SM100 four-rank bfloat16 `wide_mlp` T=64 row runs three (1.01x).
6. **Exporter**: every (architecture, world size, dtype, PDL) class
keeps exporting its class program (`generic`, or `wide_mlp` for a
promoted class) for unreviewed token counts through a
class-representative shape (T=512, eight experts) when none of the
ratified
rows selects it any more; the loader's reviewed-row table names the new
rows, the class table is unchanged.

Generated programs:
`csrc/cake_trtllm_moe_allreduce_union/{sm_100a,sm_103a}/`, loader
`flashinfer/jit/cake_trtllm_moe_allreduce_union.py`,
tests `tests/comm/test_cake_moe_allreduce_union.py`.

### Program identity vs the shipped union programs (#5650)

The generated CUDA of every one of the 60 production selections (30
benchmark rows × SM100/SM103) was rendered host-side from the generator
tree that produced the shipped programs and from this round's final
tree, then compared byte for byte together with the compile options and
the kernel symbol:

- **29 selections (SM100 14, SM103 15) are the same program**: identical
CUDA, compile options, symbol, residency and launch rule. Their speedup
ratios against the shipped programs only measure session noise (all
within 0.99–1.01); they are listed for completeness, not as changes.
- **26 selections carry a different program** (adopted schedule
variants: pipelined publish/poll bodies for the T=2048 rows on both
architectures, the SM103 eight-rank `push_g` / `pipe1` small-token rows,
the SM100 two-rank `pipe2_u4` T=256 row and the SM100 four-rank
clear-first T=128 row).
- **5 selections keep the same CUDA but change only the launch rule**
(SM100 eight-rank T=64/128 rows at four persistent CTAs per SM instead
of one; SM100 four-rank bf16 PDL T=64 at three instead of one).

Every changed selection (31 in total: SM100 16, SM103 15) is ≥ 1.0
against the shipped programs, upstream and the standalone program in the
paired sessions below; every row below 1.0 against the shipped programs
is one of the 29 identical programs.

### Speedup vs baselines (CUPTI paired timing, same session, three
counterbalanced groups, maximum per-rank median)

Columns: `new` = this PR's program, `shipped` = the union program of
#5650 as built from upstream main
`27c8875c115b3edc5b137005001243b0e48b8b98`,
`upstream` = `trtllm_moe_allreduce_fusion(backend="trtllm")`,
`standalone` = the isolated Cake bundle of #4730. Speedups are baseline
time / new time.

#### sm_103a world size 2 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws2_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 16.64 | 17.12 | 1.0289 |
18.14 | 1.0904 | 17.86 | 1.0731 |
| perf_ws2_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 16.58 | 16.61 |
1.0020 | 22.85 | 1.3784 | 19.59 | 1.1815 |
| perf_ws2_fp16_t64_e12 | 64 | 12 | float16 | n | 18.14 | 18.11 | 0.9982
| 27.04 | 1.4903 | 22.43 | 1.2363 |
| perf_ws2_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 20.58 | 20.61 |
1.0016 | 50.53 | 2.4557 | 38.72 | 1.8818 |
| perf_ws2_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 20.64 | 20.77 |
1.0062 | 50.69 | 2.4558 | 38.75 | 1.8775 |
| perf_ws2_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 23.23 | 23.14 |
0.9959 | 58.88 | 2.5345 | 47.55 | 2.0468 |
| perf_ws2_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 28.64 | 28.54 |
0.9966 | 70.31 | 2.4547 | 56.90 | 1.9865 |
| perf_ws2_fp16_t2048_e8 | 2048 | 8 | float16 | n | 107.87 | 118.59 |
1.0994 | 422.79 | 3.9193 | 341.92 | 3.1697 |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 124.06 |
138.79 | 1.1187 | 512.29 | 4.1292 | 400.68 | 3.2296 |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 141.95 |
158.62 | 1.1174 | 612.74 | 4.3165 | 460.36 | 3.2430 |
geomean vs upstream 2.382 (min 1.0904), vs standalone 1.938 (min
1.0731), vs shipped union 1.035 (min 0.9959)

#### sm_103a world size 4 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 14.40 | 14.37 | 0.9978 |
15.87 | 1.1022 | 16.16 | 1.1222 |
| perf_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 18.53 | 18.53 | 1.0000
| 22.53 | 1.2159 | 20.51 | 1.1071 |
| perf_fp16_t64_e12 | 64 | 12 | float16 | n | 20.83 | 20.64 | 0.9908 |
30.08 | 1.4439 | 23.26 | 1.1167 |
| perf_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 25.63 | 25.63 | 1.0000
| 44.19 | 1.7241 | 40.90 | 1.5955 |
| perf_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 26.27 | 26.11 |
0.9939 | 57.54 | 2.1900 | 41.18 | 1.5676 |
| perf_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 34.53 | 34.53 | 1.0000 |
57.12 | 1.6543 | 52.51 | 1.5209 |
| perf_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 36.35 | 36.58 |
1.0061 | 66.59 | 1.8318 | 61.34 | 1.6875 |
| perf_fp16_t2048_e8 | 2048 | 8 | float16 | n | 182.18 | 212.93 | 1.1688
| 528.49 | 2.9009 | 397.41 | 2.1814 |
| perf_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 197.63 | 223.55 |
1.1311 | 489.93 | 2.4789 | 455.69 | 2.3057 |
| perf_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 210.13 | 225.22 |
1.0718 | 740.68 | 3.5249 | 518.05 | 2.4654 |
geomean vs upstream 1.883 (min 1.1022), vs standalone 1.601 (min
1.1071), vs shipped union 1.034 (min 0.9908)

#### sm_103a world size 8 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws8_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 19.97 | 20.13 | 1.0080 |
20.99 | 1.0513 | 20.70 | 1.0369 |
| perf_ws8_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 28.70 | 29.22 |
1.0178 | 34.11 | 1.1884 | 31.33 | 1.0914 |
| perf_ws8_fp16_t64_e12 | 64 | 12 | float16 | n | 29.34 | 29.70 | 1.0120
| 34.27 | 1.1679 | 32.19 | 1.0971 |
| perf_ws8_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 41.86 | 42.72 |
1.0206 | 55.90 | 1.3356 | 51.55 | 1.2317 |
| perf_ws8_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 41.60 | 42.18 |
1.0138 | 55.46 | 1.3330 | 51.10 | 1.2284 |
| perf_ws8_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 63.78 | 65.54 |
1.0276 | 91.52 | 1.4350 | 83.46 | 1.3086 |
| perf_ws8_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 66.78 | 67.52 |
1.0110 | 93.25 | 1.3963 | 85.92 | 1.2865 |
| perf_ws8_fp16_t2048_e8 | 2048 | 8 | float16 | n | 362.53 | 419.59 |
1.1574 | 682.41 | 1.8823 | 600.77 | 1.6572 |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 369.57 |
429.80 | 1.1630 | 712.10 | 1.9268 | 649.89 | 1.7585 |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 372.84 |
433.00 | 1.1614 | 715.47 | 1.9190 | 632.58 | 1.6967 |
geomean vs upstream 1.432 (min 1.0513), vs standalone 1.316 (min
1.0369), vs shipped union 1.057 (min 1.0080)

#### sm_100a world size 2 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws2_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 10.24 | 10.10 | 0.9859 |
12.90 | 1.2594 | 12.38 | 1.2093 |
| perf_ws2_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 13.50 | 13.66 |
1.0118 | 21.73 | 1.6091 | 19.81 | 1.4668 |
| perf_ws2_fp16_t64_e12 | 64 | 12 | float16 | n | 15.81 | 15.62 | 0.9879
| 25.57 | 1.6174 | 20.61 | 1.3036 |
| perf_ws2_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 18.30 | 18.24 |
0.9965 | 49.86 | 2.7238 | 44.03 | 2.4056 |
| perf_ws2_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 18.37 | 18.43 |
1.0035 | 50.18 | 2.7317 | 37.98 | 2.0679 |
| perf_ws2_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 21.38 | 21.50 |
1.0060 | 58.69 | 2.7455 | 52.93 | 2.4760 |
| perf_ws2_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 24.90 | 26.94 |
1.0823 | 70.56 | 2.8342 | 63.39 | 2.5463 |
| perf_ws2_fp16_t2048_e8 | 2048 | 8 | float16 | n | 104.77 | 117.02 |
1.1170 | 427.93 | 4.0846 | 346.85 | 3.3106 |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 122.72 |
146.62 | 1.1948 | 515.87 | 4.2037 | 463.33 | 3.7755 |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 140.22 |
155.17 | 1.1066 | 614.37 | 4.3813 | 466.69 | 3.3282 |
geomean vs upstream 2.603 (min 1.2594), vs standalone 2.228 (min
1.2093), vs shipped union 1.047 (min 0.9859)

#### sm_100a world size 4 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 15.52 | 15.55 | 1.0021 |
17.44 | 1.1238 | 17.12 | 1.1032 |
| perf_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 19.58 | 20.35 | 1.0392
| 24.10 | 1.2304 | 22.14 | 1.1307 |
| perf_fp16_t64_e12 | 64 | 12 | float16 | n | 21.70 | 21.60 | 0.9956 |
25.98 | 1.1976 | 22.53 | 1.0383 |
| perf_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 27.81 | 29.41 | 1.0575
| 45.22 | 1.6260 | 40.90 | 1.4707 |
| perf_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 27.58 | 27.42 |
0.9942 | 44.83 | 1.6253 | 36.86 | 1.3364 |
| perf_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 38.98 | 38.98 | 1.0000 |
56.93 | 1.4606 | 50.56 | 1.2972 |
| perf_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 40.10 | 40.00 |
0.9976 | 68.26 | 1.7023 | 60.80 | 1.5164 |
| perf_fp16_t2048_e8 | 2048 | 8 | float16 | n | 182.75 | 213.86 | 1.1702
| 419.71 | 2.2966 | 357.09 | 1.9539 |
| perf_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 198.78 | 234.50 |
1.1796 | 492.55 | 2.4778 | 422.05 | 2.1231 |
| perf_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 212.64 | 225.79 |
1.0619 | 543.10 | 2.5541 | 410.75 | 1.9317 |
geomean vs upstream 1.659 (min 1.1238), vs standalone 1.447 (min
1.0383), vs shipped union 1.048 (min 0.9942)

#### sm_100a world size 8 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | E | dtype | PDL | new us | shipped us | vs shipped |
upstream us | vs upstream | standalone us | vs standalone |
|---|---:|---:|---|---|---:|---:|---:|---:|---:|---:|---:|
| perf_ws8_bf16_t1_e8 | 1 | 8 | bfloat16 | n | 16.99 | 17.06 | 1.0038 |
18.43 | 1.0847 | 17.21 | 1.0131 |
| perf_ws8_bf16_t64_e8_pdl | 64 | 8 | bfloat16 | y | 28.03 | 29.98 |
1.0696 | 33.47 | 1.1940 | 30.30 | 1.0811 |
| perf_ws8_fp16_t64_e12 | 64 | 12 | float16 | n | 29.02 | 31.01 | 1.0684
| 33.57 | 1.1566 | 31.20 | 1.0750 |
| perf_ws8_bf16_t128_e16 | 128 | 16 | bfloat16 | n | 42.14 | 51.26 |
1.2164 | 56.45 | 1.3394 | 51.90 | 1.2316 |
| perf_ws8_fp16_t128_e16_pdl | 128 | 16 | float16 | y | 41.86 | 50.56 |
1.2079 | 56.54 | 1.3509 | 51.39 | 1.2278 |
| perf_ws8_bf16_t256_e8 | 256 | 8 | bfloat16 | n | 65.02 | 65.47 |
1.0069 | 94.40 | 1.4518 | 85.63 | 1.3169 |
| perf_ws8_bf16_t256_e12_pdl | 256 | 12 | bfloat16 | y | 66.40 | 67.14 |
1.0111 | 97.28 | 1.4651 | 87.78 | 1.3219 |
| perf_ws8_fp16_t2048_e8 | 2048 | 8 | float16 | n | 362.30 | 425.89 |
1.1755 | 708.99 | 1.9569 | 638.43 | 1.7621 |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 12 | bfloat16 | y | 369.92 |
436.86 | 1.1810 | 749.06 | 2.0249 | 667.74 | 1.8051 |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 16 | float16 | y | 374.85 |
440.74 | 1.1758 | 687.01 | 1.8328 | 669.63 | 1.7864 |
geomean vs upstream 1.453 (min 1.0847), vs standalone 1.332 (min
1.0131), vs shipped union 1.108 (min 1.0038)


### Numerics parity vs the shipped union programs (constraint 1)

Every arm of the paired sessions is compared bitwise against the new
production output on all three result tensors
(`moe_allreduce_out`, `norm_out`, `residual_out`), rank-locally, before
timing. **60/60 rows (SM100 30, SM103 30) are bitwise
identical to the shipped union programs of #5650**, including every
re-tuned row (the pipelined T=2048 forms under the cluster cap,
the push-style RMS partial exchange and pipelined small-token rows on
eight ranks, the clear-first and residency-only rows), so no
row relies on a reduction-order argument and the max abs error vs the
contract reference is identical for the new and the shipped
program on every row (per-row tables in the remote manifest:
`parity_sm103_p5.md`, `parity_sm100_p5.md`).

### Roofline bound, achieved fraction and named residual

Bound = byte model per rank (HBM: (E+2)·T·H·2 + (W−1)·T·H·2 + 4·T·H·2
bytes; NVLink: (W−1)·T·H·2 bytes per direction) at the node's
HBM / per-direction NVLink rates; the byte model was checked against
`dram__bytes_read.sum` on the B300 node (within 0.1 %). `residual`
names the measured component that binds the row (Nsight Compute
single-pass sets and an in-kernel timestamp profile on the B300 node;
the B200 rows use the same attribution with the B200 driver occupancy).

#### sm_103a world size 2 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws2_bf16_t1_e8 | 1 | 16.64 | 0.0 | 0.002 | one cluster (4 CTAs,
sm103_t1): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.0 us (hbm) |
| perf_ws2_bf16_t64_e8_pdl | 64 | 16.58 | 1.7 | 0.104 | all 64 token
clusters resident (256 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 1.7 us
(hbm) |
| perf_ws2_fp16_t64_e12 | 64 | 18.14 | 2.2 | 0.120 | all 64 token
clusters resident (256 CTAs, generic at k=5): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 2.2 us
(hbm) |
| perf_ws2_bf16_t128_e16 | 128 | 20.58 | 5.3 | 0.256 | all 128 token
clusters resident (512 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 5.3 us
(hbm) |
| perf_ws2_fp16_t128_e16_pdl | 128 | 20.64 | 5.3 | 0.256 | all 128 token
clusters resident (512 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 5.3 us
(hbm) |
| perf_ws2_bf16_t256_e8 | 256 | 23.23 | 6.9 | 0.296 | 256 tokens on 148
clusters (wide_mlp at k=4, 54 regs, driver 5 CTAs/SM / 175 clusters):
two tokens per cluster, protocol latency with partial publish/poll
overlap; bound 6.9 us (hbm) |
| perf_ws2_bf16_t256_e12_pdl | 256 | 28.64 | 8.7 | 0.304 | 256 tokens on
185 clusters (generic at k=5, 40 regs, driver 6 CTAs/SM / 213 clusters):
two tokens per cluster, protocol latency with partial publish/poll
overlap; bound 8.7 us (hbm) |
| perf_ws2_fp16_t2048_e8 | 2048 | 107.87 | 55.1 | 0.510 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 55.1 us (hbm) |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 124.06 | 69.7 | 0.562 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 69.7 us (hbm) |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 141.95 | 84.4 | 0.595 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 84.4 us (hbm) |

#### sm_103a world size 4 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_bf16_t1_e8 | 1 | 14.40 | 0.0 | 0.003 | one cluster (4 CTAs,
sm103_t1): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.0 us (nvlink) |
| perf_bf16_t64_e8_pdl | 64 | 18.53 | 3.1 | 0.165 | all 64 token
clusters resident (256 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 3.1 us
(nvlink) |
| perf_fp16_t64_e12 | 64 | 20.83 | 3.1 | 0.147 | cooperative resident
grid (one cluster per token, 256 CTAs, wide_mlp): protocol round trips
per tile; bound 3.1 us (nvlink) |
| perf_bf16_t128_e16 | 128 | 25.63 | 6.1 | 0.239 | all 128 token
clusters resident (512 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 6.1 us
(nvlink) |
| perf_fp16_t128_e16_pdl | 128 | 26.27 | 6.1 | 0.233 | cooperative
resident grid (one cluster per token, 512 CTAs, wide_mlp): protocol
round trips per tile; bound 6.1 us (nvlink) |
| perf_bf16_t256_e8 | 256 | 34.53 | 12.2 | 0.354 | 256 tokens on 148
clusters (wide_mlp at k=4, 56 regs, driver 5 CTAs/SM / 175 clusters):
two tokens per cluster, protocol latency with partial publish/poll
overlap; bound 12.2 us (nvlink) |
| perf_bf16_t256_e12_pdl | 256 | 36.35 | 12.2 | 0.337 | 256 tokens on
148 clusters (wide_mlp at k=4, 56 regs, driver 5 CTAs/SM / 175
clusters): two tokens per cluster, protocol latency with partial
publish/poll overlap; bound 12.2 us (nvlink) |
| perf_fp16_t2048_e8 | 2048 | 182.18 | 97.9 | 0.537 | bytes in flight at
the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM on 175
clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |
| perf_bf16_t2048_e12_pdl | 2048 | 197.63 | 97.9 | 0.495 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |
| perf_fp16_t2048_e16_pdl | 2048 | 210.13 | 97.9 | 0.466 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |

#### sm_103a world size 8 (NVIDIA B300 SXM6 AC, 148 SMs; 3
counterbalanced groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws8_bf16_t1_e8 | 1 | 19.97 | 0.1 | 0.006 | one cluster (4 CTAs,
sm103_t1): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.1 us (nvlink) |
| perf_ws8_bf16_t64_e8_pdl | 64 | 28.70 | 7.1 | 0.249 | all 64 token
clusters resident (256 CTAs, push_g at k=4): protocol round trips (clear
-> publish -> poll -> RMS) dominate, not bytes; bound 7.1 us (nvlink) |
| perf_ws8_fp16_t64_e12 | 64 | 29.34 | 7.1 | 0.243 | all 64 token
clusters resident (256 CTAs, push_g at k=4): protocol round trips (clear
-> publish -> poll -> RMS) dominate, not bytes; bound 7.1 us (nvlink) |
| perf_ws8_bf16_t128_e16 | 128 | 41.86 | 14.3 | 0.341 | all 128 token
clusters resident (512 CTAs, push_g at k=4): protocol round trips (clear
-> publish -> poll -> RMS) dominate, not bytes; bound 14.3 us (nvlink) |
| perf_ws8_fp16_t128_e16_pdl | 128 | 41.60 | 14.3 | 0.343 | all 128
token clusters resident (512 CTAs, push_g at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 14.3 us
(nvlink) |
| perf_ws8_bf16_t256_e8 | 256 | 63.78 | 28.5 | 0.448 | 256 tokens on 111
clusters (pipe1 at k=3, 72 regs, driver 4 CTAs/SM / 142 clusters): two
tokens per cluster, protocol latency with partial publish/poll overlap;
bound 28.5 us (nvlink) |
| perf_ws8_bf16_t256_e12_pdl | 256 | 66.78 | 28.5 | 0.427 | 256 tokens
on 148 clusters (push_g at k=4, 56 regs, driver 5 CTAs/SM / 175
clusters): two tokens per cluster, protocol latency with partial
publish/poll overlap; bound 28.5 us (nvlink) |
| perf_ws8_fp16_t2048_e8 | 2048 | 362.53 | 228.4 | 0.630 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 369.57 | 228.4 | 0.618 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 372.84 | 228.4 | 0.612 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |

#### sm_100a world size 2 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws2_bf16_t1_e8 | 1 | 10.24 | 0.0 | 0.003 | one cluster (1 CTAs,
wide_mlp): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.0 us (hbm) |
| perf_ws2_bf16_t64_e8_pdl | 64 | 13.50 | 1.7 | 0.127 | all 64 token
clusters resident (256 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 1.7 us
(hbm) |
| perf_ws2_fp16_t64_e12 | 64 | 15.81 | 2.2 | 0.138 | all 64 token
clusters resident (256 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 2.2 us
(hbm) |
| perf_ws2_bf16_t128_e16 | 128 | 18.30 | 5.3 | 0.288 | all 128 token
clusters resident (512 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 5.3 us
(hbm) |
| perf_ws2_fp16_t128_e16_pdl | 128 | 18.37 | 5.3 | 0.287 | all 128 token
clusters resident (512 CTAs, wide_mlp at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 5.3 us
(hbm) |
| perf_ws2_bf16_t256_e8 | 256 | 21.38 | 6.9 | 0.322 | 256 tokens on 148
clusters (wide_mlp at k=4, 56 regs, driver 5 CTAs/SM / 175 clusters):
two tokens per cluster, protocol latency with partial publish/poll
overlap; bound 6.9 us (hbm) |
| perf_ws2_bf16_t256_e12_pdl | 256 | 24.90 | 8.7 | 0.350 | 256 tokens on
148 clusters (pipe2_u4 at k=4, 56 regs, driver 5 CTAs/SM / 175
clusters): two tokens per cluster, protocol latency with partial
publish/poll overlap; bound 8.7 us (hbm) |
| perf_ws2_fp16_t2048_e8 | 2048 | 104.77 | 55.1 | 0.525 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 55.1 us (hbm) |
| perf_ws2_bf16_t2048_e12_pdl | 2048 | 122.72 | 69.7 | 0.568 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 69.7 us (hbm) |
| perf_ws2_fp16_t2048_e16_pdl | 2048 | 140.22 | 84.4 | 0.602 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
bound 84.4 us (hbm) |

#### sm_100a world size 4 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_bf16_t1_e8 | 1 | 15.52 | 0.0 | 0.003 | one cluster (1 CTAs,
wide_mlp): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.0 us (nvlink) |
| perf_bf16_t64_e8_pdl | 64 | 19.58 | 3.1 | 0.156 | all 64 token
clusters resident (256 CTAs, wide_mlp at k=3): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 3.1 us
(nvlink) |
| perf_fp16_t64_e12 | 64 | 21.70 | 3.1 | 0.141 | cooperative resident
grid (one cluster per token, 256 CTAs, wide_mlp): protocol round trips
per tile; bound 3.1 us (nvlink) |
| perf_bf16_t128_e16 | 128 | 27.81 | 6.1 | 0.220 | all 128 token
clusters resident (512 CTAs, clrfirst at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 6.1 us
(nvlink) |
| perf_fp16_t128_e16_pdl | 128 | 27.58 | 6.1 | 0.222 | cooperative
resident grid (one cluster per token, 512 CTAs, wide_mlp): protocol
round trips per tile; bound 6.1 us (nvlink) |
| perf_bf16_t256_e8 | 256 | 38.98 | 12.2 | 0.314 | 256 tokens on 148
clusters (generic at k=4, 54 regs, driver 5 CTAs/SM / 175 clusters): two
tokens per cluster, protocol latency with partial publish/poll overlap;
bound 12.2 us (nvlink) |
| perf_bf16_t256_e12_pdl | 256 | 40.10 | 12.2 | 0.305 | 256 tokens on
148 clusters (generic at k=4, 54 regs, driver 5 CTAs/SM / 175 clusters):
two tokens per cluster, protocol latency with partial publish/poll
overlap; bound 12.2 us (nvlink) |
| perf_fp16_t2048_e8 | 2048 | 182.75 | 97.9 | 0.536 | bytes in flight at
the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM on 175
clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |
| perf_bf16_t2048_e12_pdl | 2048 | 198.78 | 97.9 | 0.492 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 55 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |
| perf_fp16_t2048_e16_pdl | 2048 | 212.64 | 97.9 | 0.460 | bytes in
flight at the co-resident cluster capacity: pipe2_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 97.9 us (nvlink) |

#### sm_100a world size 8 (NVIDIA B200, 148 SMs; 3 counterbalanced
groups, rank-max median)

| row | T | new us | bound us | achieved | residual |
|---|---:|---:|---:|---:|---|
| perf_ws8_bf16_t1_e8 | 1 | 16.99 | 0.1 | 0.007 | one cluster (4 CTAs,
generic): cross-rank closed-loop latency - the B300 burst timestamp
profile puts 98.9 % of the in-kernel time in the first cross-rank wait
(launch skew + publish -> remote visibility -> poll), then RMS epilogue;
bound 0.1 us (nvlink) |
| perf_ws8_bf16_t64_e8_pdl | 64 | 28.03 | 7.1 | 0.255 | all 64 token
clusters resident (256 CTAs, sm100_ws8_mid at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 7.1 us
(nvlink) |
| perf_ws8_fp16_t64_e12 | 64 | 29.02 | 7.1 | 0.246 | all 64 token
clusters resident (256 CTAs, sm100_ws8_mid at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 7.1 us
(nvlink) |
| perf_ws8_bf16_t128_e16 | 128 | 42.14 | 14.3 | 0.339 | all 128 token
clusters resident (512 CTAs, sm100_ws8_mid at k=4): protocol round trips
(clear -> publish -> poll -> RMS) dominate, not bytes; bound 14.3 us
(nvlink) |
| perf_ws8_fp16_t128_e16_pdl | 128 | 41.86 | 14.3 | 0.341 | all 128
token clusters resident (512 CTAs, sm100_ws8_mid at k=4): protocol round
trips (clear -> publish -> poll -> RMS) dominate, not bytes; bound 14.3
us (nvlink) |
| perf_ws8_bf16_t256_e8 | 256 | 65.02 | 28.5 | 0.439 | 256 tokens on 148
clusters (generic at k=4, 56 regs, driver 5 CTAs/SM / 175 clusters): two
tokens per cluster, protocol latency with partial publish/poll overlap;
bound 28.5 us (nvlink) |
| perf_ws8_bf16_t256_e12_pdl | 256 | 66.40 | 28.5 | 0.430 | 256 tokens
on 148 clusters (generic at k=4, 56 regs, driver 5 CTAs/SM / 175
clusters): two tokens per cluster, protocol latency with partial
publish/poll overlap; bound 28.5 us (nvlink) |
| perf_ws8_fp16_t2048_e8 | 2048 | 362.30 | 228.4 | 0.630 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |
| perf_ws8_bf16_t2048_e12_pdl | 2048 | 369.92 | 228.4 | 0.617 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |
| perf_ws8_fp16_t2048_e16_pdl | 2048 | 374.85 | 228.4 | 0.609 | bytes in
flight at the co-resident cluster capacity: pipe1_u4_b5 at k=5 CTAs/SM
on 175 clusters (700 CTAs; driver 5 CTAs/SM at 56 regs, 175 co-resident
clusters; k+1 = 6 CTAs/SM needs the 48-register cap, which spills);
publish phase NVLink egress 82-83 % of the per-direction rate (timestamp
profile); bound 228.4 us (nvlink) |


### Convergence: directions measured and their paired result

Every direction below was measured as a paired arm against the
production program in the same CUPTI session (three counterbalanced
groups, maximum per-rank median, all arms bitwise-compared against the
production output); "3g" = all three groups agree. Adopted rows are
listed above; the rest are the measured negatives and the
analysis-closed directions.

| direction | candidate | SM103 (B300) | SM100 (B200) | outcome |
|---|---|---|---|---|
| overlap the NVLink-bound publish of token j+D with the poll of token j
| `pipe1`/`pipe2` (wide body, clear first) | T=2048: 1.07x-1.13x where
the body kept its residency, 0.92x-0.97x where it dropped a CTA per SM;
T=256 0.94x-0.97x | ws2/ws4 T=2048 `pipe2_u4` 1.02x-1.16x; ws8 uncapped
1.05x-1.08x (two CTAs per SM); T=256 0.95x-1.01x | adopted for the
T=2048 rows (see 1.) with the four-wide unroll and the 56-register cap |
| register cap to keep the pipelined body co-resident |
`__launch_bounds__(224, 5)` (56 regs) / `(224, 6)` (48 regs) | `_b5`:
ws2 1.03x-1.07x, ws4 1.01x-1.13x, ws8 1.12x-1.14x (3g); `_b6` spills and
loses to `_b5` by 1-3 % | `_b5`: ws8 T=2048 1.11x-1.13x (3g); `_b6`
1.07x-1.10x; ws2/ws4 `pipe2_u4_b5` ties `pipe2_u4` at four CTAs per SM
(0.999x-1.006x) and carries the cluster cap below | `_b5` adopted (B200
ws2/ws4 through the cluster cap), `_b6` rejected |
| launch the driver's co-resident cluster capacity instead of `sm_count
x k` (a fifth CTA per SM on 148 SMs needs 185 clusters; the driver
admits 175) | per-module cluster cap in the launch record
(`max_persistent_clusters` = the frozen `cuOccupancyMaxActiveClusters`
answer, re-checked against the driver before the first launch and on the
export node); grid = min(sm_count x 5, 175 x 4, T x 4) = 700 CTAs
instead of 592 | T=2048: ws2 1.052x / 1.050x / 1.063x, ws4 1.032x /
1.050x / 1.035x, ws8 1.028x / 1.037x / 1.025x (3g, bitwise identical);
T=256 rows 0.977x-1.013x | T=2048: ws2 1.069x / 1.061x / 1.073x, ws4
1.034x / 1.048x / 1.029x, ws8 1.026x / 1.028x / 1.027x (3g, bitwise
identical); T=256 rows 0.992x-1.016x; the ws2 bf16 PDL T=256 e12 row
(0.992x) shared the ws2 `pipe2_u4` module, so the T=2048 rows moved to
`pipe2_u4_b5` (fill 1.060x / 1.054x / 1.071x, 1.028x / 1.051x / 1.027x)
and that row keeps `pipe2_u4` at four | adopted for the 18 T=2048 rows
(five CTAs per SM under the 175-cluster cap); T=256 rows keep their
grids |
| deeper poll prefetch (probe the next token before the epilogue) |
`pp`, `pipe1_pp_u4(_b6)` | ws2 +0.5-1.7 % over the pipelined body only
at 56 regs; ws4/ws8 forms cost registers: 0.71x-0.96x | 0.79x-0.89x
(ws8), 1.01x-1.03x capped; under the cluster-cap grid `pipe1_pp_u4_b5`
0.90x-0.96x (B300) and 0.97x-1.03x (B200 ws2) vs the capped pipelined
body | rejected (register cost outweighs the hidden latency; no
remaining positive paired evidence once the grid fills the cluster
capacity) |
| clear the previous epoch before publishing | `clrfirst` (wide) /
`clrfirst_g` (generic) | small rows 0.87x-1.01x | ws4 bf16 no-PDL T=128
1.050x (3g); every other small row 0.97x-1.01x | adopted for that one
row |
| more expert loads in flight | expert unroll 8/12/16 (+ rotated peers)
| 0.91x-1.01x on every row | - | rejected: the publish limiter is not
the expert-load count |
| rank-rotated peer store order | `rot`, `rot_w`, `pipe1_rot` |
0.93x-0.95x alone; -2..+0.3 % on top of the pipelined body | - |
rejected: destination hot-spotting is not the NVLink limiter |
| fewer cluster barriers in the small-token epilogue | push-style RMS
partial exchange on the generic body (`push_g`), pack-once variants |
ws8 T in {64,128} 1.015x-1.020x (3g), T=256 1.013x-1.016x; ws2/ws4 rows
(already push-style in `wide_mlp`) 0.93x-0.98x | 1.003x-1.009x on the
ws8 mid rows (inside the 1 % band); 0.92x-1.02x elsewhere | adopted on
SM103 eight ranks only |
| one cluster per token instead of the one-CTA-per-SM loop (T <= 128) |
residency 2/3/4 for `sm100_ws8_mid` and the four-rank bf16 `wide_mlp`
module | n/a (already four CTAs per SM) | ws8 T=128 1.18x, T=64 1.05x
(3g); ws4 bf16 T=64 1.014x; ws2 and ws4 T=128 rows lose 6-18 % at
two/three CTAs per SM | adopted where positive |
| poll-loop backoff (`nanosleep`) | analysis | the poll is an unbounded
128-bit volatile sweep with no backoff to remove; DRAM is 16 % of peak
at T <= 128 | same | rejected: a backoff only lengthens the reaction
latency of latency-bound rows |
| PDL `griddepcontrol` placement / prologue overlap | analysis | the
wait is the first instruction of the compute role; only address
arithmetic (< 0.1 us) could precede it; moving workspace-table loads
above it changes the PDL contract | same | rejected by contract |
| T=1 launch / skew attribution | in-kernel timestamp profile aligned
with the CUPTI timeline | 98.9 % of the in-kernel time is the first
cross-rank wait (14.5 of 14.6 us per launch): the row is the cross-rank
closed-loop period chained across launches | - | closed: the single-CTA
geometry of the previous round already exhausted the launch-geometry
lever |
| bulk (TMA) publish from shared memory | not implemented | the ws4/ws8
publish phase already runs at 82-83 % of the per-direction NVLink rate |
- | deferred (<= 17 % headroom, protocol-neutral but a new data path) |
| dynamic token assignment across clusters | not implemented | per-CTA
total spread 293/383/421 us at ws8 T=2048 | - | needs a rank-local
counter in the workspace (API change) - out of scope for this round |

Residual per row: T=2048 rows are bytes in flight at the driver's
co-resident cluster capacity (five CTAs per SM on 175 clusters = 700
CTAs; a sixth CTA per SM needs the 48-register cap, which spills and
loses, and the ws4/ws8 publish phase already runs at 82-83 % of the
per-direction NVLink rate); T in {64, 128, 256} rows are bound by the
protocol round trips (clear -> publish -> remote visibility -> poll ->
RMS) at 15-16 % issue-active / DRAM; T=1 rows by the cross-rank
closed-loop latency.

### Baselines and their source PRs

- shipped union programs: #5650 (the previous performance round on top
of #5599), built and timed from upstream main
`27c8875c115b3edc5b137005001243b0e48b8b98` in the same process as the
new programs.
- standalone: the isolated SM100/SM103 Cake bundle of #4730
(`csrc/cake_trtllm_moe_allreduce_fusion`), unchanged by this PR.
- upstream: `trtllm_moe_allreduce_fusion(backend="trtllm")` of this tree
(base `27c8875c115b3edc5b137005001243b0e48b8b98`).

### Evidence manifest (SHA-256 of the remote receipts and tables)

| file | bytes | sha256 |
|---|---:|---|
| `delivery.patch` | 4888068 |
`82d8721b926e24e214af60dd5deb1cdbfc095fa8e77482958b367a4a8d44da9a` |
| `delivery.status` | 26860 |
`ce0dc0fb4953caea917dd72f4cd5ddb4e3ff09be669aaa715cc7b24d3ce5489c` |
| `receipts.index` | 49464 |
`6349cf78927970dc09e85a99cb1ba6a0680be43b6019d9e149f9d0d082c06b6f` |
| `summary.md` | 22530 |
`15d262bbfef1f1b1c9597251922135f962c973099cfee344041c9bdcc7e27fb9` |
| `gates-sm100-cake_unit_e2e_union_trtmoe_regression.json` | 788 |
`69d318e708d5345f3a9f3f55a0dc80510d8d3134da4e90ef00ab67af24bf4480` |
|
`gates-sm100-fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 770 |
`056a0e340778f23a85bad6739b458dad8bc7244f59bafecea0e8f22b43f646d8` |
| `roofline_sm100_ws2_p5.json` | 64649 |
`4d31e1106618e59125f3ec91e04d5892cb9f171c67b175fa2f9871065c3603f0` |
| `roofline_sm100_ws4_p5.json` | 64888 |
`c935c9d81de37f0b0e41f2e6c1ef9974b2503c8ebd46b524fd902fb64a8a9d75` |
| `roofline_sm100_ws8_p5.json` | 65020 |
`ab2e5627015f519179389613dcf967571363ed59993366ae826a5200875e0d1d` |
| `delivery.patch` | 5071940 |
`87be8b1a9b7e648ea41aef63d1725024a0160c2d39f862772b2170d755836ee9` |
| `delivery.status` | 18386 |
`25625db6565eabe360d29d3e1da8ccc4c2a60c5d12534e7638757a25598f97ce` |
| `receipts.index` | 50043 |
`6f0f9e01d0782eee6e217c15df8fb875f97100133c6b7f8903bcc9bb4652d74c` |
| `summary.md` | 24704 |
`f88e0a0d335ecad9074c0cd3a332e38b346ea7f2e3752e1b6b8aa1c80d41f606` |
|
`gates-sm103-cake_unit_e2e_union_sanitize_union_trtmoe_regression.json`
| 1154 |
`604221f9ad8532bef979f69bc7f46d883703b23a1ba6463a747c42a290f0e13e` |
|
`gates-sm103-fi_union_cpu_tests_fi_distributed_tp248_fi_precommit.json`
| 770 |
`fde453087aa79cdc8c264d1ab233be0c742e3c0e161a76292794e731f7325632` |
| `compare.json` | 39780 |
`bb53ad790423949a2619bf9033c67759d39246165e61cb6908236220789f813e` |
| `new.json` | 21539 |
`816fb6629ff4d25365bd5b6940bd305773d7b732facfba963224c220510012f1` |
| `old.json` | 21277 |
`0cb2c683579abfb1932864853e5a4d78637874b3a5c2339f825d151a8fb9b594` |
| `roofline_sm103_ws2_p5.json` | 64449 |
`677dff53ff1641ffc5dda4e55e971b1f9eeb5a74c72d4dc4a67534f9c8335f24` |
| `roofline_sm103_ws4_p5.json` | 64600 |
`6932f3d250a5db65b8fbb36efe9874dec20addc4f7813d5e5c537f7cd65985be` |
| `roofline_sm103_ws8_p5.json` | 64679 |
`c6799a20877447394e41fefecd03c6a44ae59c9157b2e3e8f6fbf917d777d916` |
| `san_sm103_ws2_san2_synccheck.json` | 7753 |
`ad92fe8fd9a356546bb08e43e5e5829d73de9ae61dc224c953ffc63e7fbb2c3a` |
| `san_sm103_ws2_san2_synccheck.log` | 7884 |
`8f3b2877c6e7f534fa0e33ab85a16ba336a89f41c364c968ef70d89f49b3f15c` |
| `san_sm103_ws2_san3_memcheck.json` | 7753 |
`ad92fe8fd9a356546bb08e43e5e5829d73de9ae61dc224c953ffc63e7fbb2c3a` |
| `san_sm103_ws2_san3_memcheck.log` | 7883 |
`bc4532964d855cfb8a5d38d35b804008ec90d6cf0cf455cc30d91ab3369ebdca` |
| `san_sm103_ws4_san2_synccheck.json` | 7782 |
`acf41efa8c57435f00c6c156e156c425d69526c2d35abf674e2d87af35c37b91` |
| `san_sm103_ws4_san2_synccheck.log` | 14420 |
`32cd3fc59e5cb931869b979306f3db07c82475ee143d53917a0803aeb6085980` |
| `san_sm103_ws4_san3_memcheck.json` | 7782 |
`acf41efa8c57435f00c6c156e156c425d69526c2d35abf674e2d87af35c37b91` |
| `san_sm103_ws4_san3_memcheck.log` | 14419 |
`eee451392fecef57ecd9e013e21ad34dc8bd0214d065fec9901a7953fe08a864` |
| `san_sm103_ws8_san2_synccheck.json` | 22496 |
`36f2c60945823f6d642c5457783b8ad1560606248477df5cd3092a466a4c293c` |
| `san_sm103_ws8_san2_synccheck.log` | 34707 |
`de18a6bc28a68007ebf0249e044ffe560c8dc5e8be3315609297b36f57d6fcb0` |
| `san_sm103_ws8_san3_memcheck.json` | 22496 |
`36f2c60945823f6d642c5457783b8ad1560606248477df5cd3092a466a4c293c` |
| `san_sm103_ws8_san3_memcheck.log` | 34706 |
`baab777164bc7ecfcfe6ef775f60586f7923d7b66a733f9c76b00a9d730c3d0c` |

## 🔍 Related Issues

- #5650 (union programs this PR re-tunes), #5599 (union export at world
sizes 2/4/8), #4730 (isolated bundle)
- Tracker: #4254

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass on the changed hand-written files (the
generated directory is excluded as a byte-faithful export).
- [x] Tests: `tests/comm/test_cake_moe_allreduce_union.py`,
`tests/comm/test_cake_moe_allreduce_api.py`,
      `tests/comm/test_cake_trtllm_moe_allreduce_source.py` (CPU) and
`tests/comm/test_cake_moe_allreduce_distributed.py -k "tp2 or tp4 or
tp8"` (eight B200 GPUs and eight B300 GPUs).
- [x] Every exported program passed the rank-set correctness check
against `backend="trtllm"` on all ranks (atol = rtol = 1e-2) with
bitwise source/export parity, and every adopted program is bitwise
identical to the shipped program it replaces.
- [x] compute-sanitizer synccheck + memcheck of the all-reduce-fusion
launchers on both architectures (the poll loop changed).

## 🧪 Tests

| gate | B200 exit | B300 exit | result |
|---|---:|---:|---|
| FlashInfer CPU tests (`tests/comm/test_cake_moe_allreduce_union.py`,
`test_cake_moe_allreduce_api.py`,
`test_cake_trtllm_moe_allreduce_source.py`) | 0 | 0 | PASS on both nodes
for this PR's head (92 passed: union loader/route/specialization rules,
API surface, source-bundle tests). |
| FlashInfer distributed tests
(`tests/comm/test_cake_moe_allreduce_distributed.py -k "tp2 or tp4 or
tp8"`, eight GPUs) | 0 | 0 | PASS 6/6 (tp2/tp4/tp8 x fp16/bf16) on eight
B200 and on eight B300 for this PR's head (the B300 run under
NVSHMEM-free symmetric memory, the B200 run with TORCH_SYMMMEM=NVSHMEM).
|
| pre-commit on the changed hand-written files (all hooks incl. mypy,
ruff check, ruff format) | 0 | 0 | PASS on both nodes for this PR's head
over every file this PR changes vs upstream main 27c8875c (all hooks
incl. mypy, ruff check, ruff format, clang-format on the generated .cu
files). An earlier head failed only ruff-format on two wrapped set
literals of the exported test; fixed in the head above. |
| Generator four-rank paired regression of the union programs vs the
pinned live FlashInfer (10 correctness + 10 CUPTI paired rows) | 0 | 0 |
PASS 20/20 on both nodes (10 correctness rows + 10 CUPTI paired
performance rows vs the pinned live FlashInfer): B300 paired geomean
1.408x, minimum 1.051x; B200 paired geomean 1.358x, minimum 1.068x
(required minimum > 1.0). Each node needed one same-node checkpoint
resume after the first attempt died in the torch symmetric-memory
rendezvous (a stale-handle class of the test harness, not the kernels);
the resumed run completed every row. |
| Generator end-to-end all-reduce-fusion slice (four ranks; union test +
dynamic-FP8 MNNVL test) | 0 | 1 | B200: 2/2 PASS (union test +
dynamic-FP8 MNNVL test). B300: the union test PASSED; the dynamic-FP8
MNNVL test fails at rank setup in the container (no multicast pointer),
identical to the previous round. |
| compute-sanitizer synccheck + memcheck over the registered
all-reduce-fusion sanitizer targets (26 four-rank rows incl. the six
TRT-MoE rows) | n/a | 1 | B300: exit 1 = environment, not the branch:
every registered target fails at rank setup inside the container
(symmetric-memory rendezvous handle has no multicast pointer,
`cuMemGetHandleForAddressRange` -> not supported), before any kernel
launch; identical to the previous round. B200: skipped (no
compute-sanitizer on the route). The changed programs are covered by the
per-row sanitizer probe above. |
| compute-sanitizer synccheck + memcheck on every rank of the paired
probe for every row whose program changed in this round (the 15 changed
B300 rows: pipelined T=2048 forms, push-style RMS partials, three-CTA
pipelined body; the 11 changed B200 rows have no sanitizer on that
route, see the note) | n/a | n/a | B300: PASS. synccheck and then
memcheck (`--report-api-errors no`, the CUDA Python driver's optional
entry-point probes are otherwise counted as API errors) on every rank of
the paired probe for the 15 changed SM103 rows (ws2/ws4 T=2048 x3 each,
ws8 x9; arms new program + upstream): `ERROR SUMMARY: 0 errors` on all
2/4/8 ranks, outputs bitwise identical to production. B200: not
obtainable, the bare-metal B200 route has no compute-sanitizer binary
(disclosed). |
| Generator unit tests of the touched modules (compared item by item
against the generator's main branch) | 1 | 1 | Exit 1 on both nodes =
pre-existing failures that fail identically on the generator's main
branch, compared item by item in the same environment: B300 (container,
0-GPU step) 26 failed on main and 26 on this tree with identical test
ids (18 in the export-discovery test module, one half-arithmetic
boundary test of the contract module under the container's torch 2.10, 7
GPU-only FFI tests in a 0-GPU step); B200 (bare-metal venv) the same 18
export-discovery ids on main and on this tree (the GPU gate run
deselects the GPU-only FFI tests). This tree adds 13 (B300) / 15 (B200)
passing tests, including the new cluster-cap receipt test. |
| Generator all-reduce-fusion family regression gate (six contracts,
four ranks) | n/a | n/a | Not run in full (disclosed). The changed
runtime surface is the TRT-LLM MoE all-reduce union export (program
schedules, launch geometry, the per-architecture cluster-cap table) plus
the exporter's source-build receipt, which affects unit names only; the
targeted regression for that surface is the paired TRT-MoE gate above
(20/20 PASS on both architectures, every paired row > 1.0x vs the pinned
live FlashInfer). No other kernel's generated CUDA or launch parameters
change. |

## Reviewer Notes

The export receipts (correctness against the upstream reference on every
rank, bitwise source/export parity, co-residency probe,
no-fallback route check, paired per-rank timing with the maximum across
ranks per sample) were produced by the Cake generated-program
exporter on one B300 node (SM103) and one B200 node (SM100), one
architecture per run, both against upstream main (#5650): the
first commit carries the SM103 delivery, the second the SM100 delivery,
and the loader tables of the second commit are the union of the
SM103 tables of the first commit and the SM100 tables of its own export
(every unit shared by both renders has identical text; every listed
source SHA-256 matches the committed file). Units whose program did not
change are byte-identical to the tracked files of #5650: all 172
SM103 files and 140 of the 212 SM100 files. The 72 SM100 files (36
modules) of the two routes whose launch record changed (eight-rank
T <= 128 rows: four CTAs per SM; four-rank bfloat16 PDL wide body:
three) are regenerated under new names with unchanged device source. The
tables above list every row of the frozen thirty-row denominator per
architecture; the additional class-representative shapes (T=512) are
listed separately in the receipts.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cc0ac3a](https://github.com/flashinfer-ai/flashinfer/commit/cc0ac3a75c431f2e3ee0a36bb79e4b685bf0a92f)

- **作者**: Ao Tang
- **时间**: 2026-09-29T22:43:45Z
- **提交信息**: fix(moe): forward enable_pdl to CuTeDSL MoE routing (#5497)

<!-- .github/pull_request_template.md -->

## 📌 Description

Forward `enable_pdl` from `_moe_core_impl` to `moe_sort` in the CuTeDSL
fused-MoE path.

Previously, `_moe_core_impl` forwarded the setting to the GEMMs but
omitted it from the routing call. Consequently, `moe_sort` used its
default `enable_pdl=False`, even when PDL was enabled by the caller.

The production change is one line:

```diff
         tile_tokens_dim=tile_size,
+        enable_pdl=enable_pdl,
         **moe_sort_kwargs,
```

This activates the existing routing PDL path when requested, allowing
routing to overlap with a preceding PDL-capable producer such as
`moeA2ASanitizeExpertIdsKernel`. Explicit `enable_pdl=False` remains
supported.


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

* **Bug Fixes**
* Mixture-of-experts token sorting now receives the configured PDL
setting, keeping routing behavior aligned with the selected execution
mode. Both enabled and disabled PDL configurations are passed through
unchanged, so routing uses the setting selected for execution. This
corrects handling for both configurations without changing the available
options or the expected behavior of other execution settings.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3a3fb9a](https://github.com/flashinfer-ai/flashinfer/commit/3a3fb9aa590d506bd6117bfbf3111f42fad314b8)

- **作者**: eigen
- **时间**: 2026-09-29T22:43:30Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): round 8 -- single-wave aligned K halves for the front prefill trailing wave, evict_first front instance for T <= 512, coalesced stream-K partial slots (SM100a/SM103a) (#5671)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

## Summary

Round 8 of the Kimi-K3 Stable LatentMoE front / tail projections in
`flashinfer/experimental/kimi_k3_latent_moe` (#5647, #5584, #5575,
tracker #4254): a paired lever ledger on B200 and B300 (A/B in
interleaved CUDA-graph groups, cold-L2 CUPTI timing, an A/A control per
row, a second independent process on every row under 15 us) adopts three
exact rules: two in the front prefill GEMM and one shared partial-slot
layout for the stream-K / split-K paths of both GEMMs; the decode
programs and the tail norm are regenerated unchanged. Public API, tensor
shapes / dtypes / strides and the weight layout (`[N, K]` bf16, no
load-time packing) are unchanged; every program still binds its tensor
maps by value. Numerics are exact: bf16 inputs with fp32 accumulation,
the same RMSNorm and eps, the shared expert always computed; the only
new arithmetic path is an fp32 partial sum combined in a fixed order.

- **Single-wave aligned K halves for the trailing wave of the front
prefill GEMM.** The persistent 2-CTA GEMM tiles the K-concatenated
`[gate; down; shared_gate; shared_up]` rows into 256 x 256 pair tiles
over 74 resident clusters; when the tile count leaves a partial last
wave, the tiles of that wave now run as two K halves (56 of the 112 K
iterations each) whose fp32 partials meet in a package-internal
workspace and are combined in a fixed order by the second contributor.
The rule takes the halves only when they fit one wave (`2 x rem <= 74`)
and the modelled saving is at least 4 % of the whole-tile cost, so it
fires on `front_tp8_m256` (24 tiles -> 48 halves), `front_tp8_m1024` (74
+ 22 x 2), `front_tp8_m4096` (370 + 14 x 2) and `front_tp1_m2048` (518 +
10 x 2); every other row keeps whole tiles. Halves aligned to tile
boundaries keep the two rows that share a weight column in lockstep
(general stream-K ranges that cross tiles were measured 5-29 % slower
because the pair rows fetch the column twice). Paired against whole
tiles on the same tree: `front_tp8_m256` **+25.5 / +24.4 %**,
`front_tp8_m1024` **+14.9 / +13.2 %**, `front_tp8_m4096` +3.7 / +3.6 %,
`front_tp1_m2048` +3.0 / +3.5 % (B200 / B300).
- **Coalesced `[chunk][row][16]` layout for the fp32 stream-K / split-K
partial slots** (both GEMMs; exact, same fixed reduction order): each
warp now stores and re-reads its partial tile as 512-byte contiguous
segments instead of 32 bytes per lane strided by the row, which removes
most of the partial-store + serial-fix-up epilogue of every stream-K
tile. Tail TP1 stream-K rows `tail_tp1_m256` / `m1024` **+6 / +6 %**,
`m2048` +2 %, `m4096` +1 % (both GPUs); it is also the layout under
which the front K halves above win (the same halves in the previous
row-major slots were 5-14 % slower). The six tail GEMM programs change
only in these ten generated lines.
- **`evict_first` weight stream for the short prefill rows**
(`front:i<I>e1`, T <= 512 = at most two pair rows per weight column):
the weights are streamed with an evict-first L2 policy on the rows where
no second row can reuse them; a second front instance per TP, selected
by the planner. +16-17 % on `front_tp1_m256` and +2-4 % on
`front_tp1_m512`, `front_tp8_m256` and `front_tp8_m512` (batches 8d /
8e, both GPUs); neutral from T = 1024 up, so the rule stops there.

Host planner (`cake_backend.py`): `front_split_plan(cluster_tiles,
sm_count)` (the rule above), `prefill_front_plan(M, i_local)` (items,
halves, workspace sizes, grid), `front_evict_first(m_tiles)` and the
`e1` kernel-key component; `_front_workspace` (fp32 partial slots +
self-resetting arrival counters, package-internal like the tail
workspace). Route keys for the front prefill are now `front:i<I>` and
`front:i<I>e1`.

## Evidence (Cake export protocol, producer `b92e5ec6cb3`, target
`e59b5008178`)

Every row runs the source (Cake production launcher) and the exported
programs in counterbalanced CUDA-graph groups; correctness = both arms
against the FP32/BF16 torch reference, bitwise source == export.

| arch | GPU | rows sealed | clock-unqualified (disclosed) | correct
(bitwise source == export) | source/export | steps |
|---|---|---|---|---|---|---|
| sm_100a | B200 | 50 / 60 | 9 clock-unqualified + `front_tp1_m1024`
(first: endpoint-drift gate, ratio 0.9992, correct, bitwise; retry:
endpoint-drift gate, ratio 1.0005, correct, bitwise) | 52 / 52 | 0.9654
- 1.0852 | `db7bcdcfec5a17b67f5d7cad` (protocol) +
`6fe93d4b3c7c535e7f8abf8b` (export) + `2551c6699719d635b9594c2b` (retry
+ FI tests) |
| sm_103a | B300 | 51 / 60 | 8 clock-unqualified + `tail_tp1_m4096`
(first: endpoint-drift gate, ratio 0.9994, correct, bitwise; retry:
clock-unqualified 1440/2032 MHz) | 52 / 52 | 0.9816 - 1.0647 |
`34ef53eff5f1b0754c491af5` (export) + `733d97bad2efd7819041a7b1` (retry
+ FI tests) |

Clock-unqualified rows: the sustained dense tcgen05 GEMM rows run at the
power cap and the interleaved timing session sampled the loaded SM clock
below 0.85 x max on both bounded attempts (sampled / max MHz): sm_100a:
`front_tp1_m2048` (1665/1965 MHz first, 1650/1965 MHz retry),
`front_tp1_m4096` (1305/1965 MHz first, 1507/1965 MHz retry),
`front_tp1_m8192` (1440/1965 MHz first, 1447/1965 MHz retry),
`front_tp1_m16384` (1365/1965 MHz first, 1387/1965 MHz retry),
`front_tp8_m8192` (1567/1965 MHz first, 1530/1965 MHz retry),
`front_tp8_m16384` (1425/1965 MHz first, 1425/1965 MHz retry),
`tail_tp1_m4096` (1552/1965 MHz first, 1597/1965 MHz retry),
`tail_tp1_m8192` (1470/1965 MHz first, 1477/1965 MHz retry),
`tail_tp1_m16384` (1395/1965 MHz first, 1425/1965 MHz retry); sm_103a:
`front_tp1_m2048` (1575/2032 MHz first, 1627/2032 MHz retry),
`front_tp1_m4096` (1327/2032 MHz first, 1725/2032 MHz retry),
`front_tp1_m8192` (1275/2032 MHz first, 1275/2032 MHz retry),
`front_tp1_m16384` (1230/2032 MHz first, 1237/2032 MHz retry),
`front_tp8_m8192` (1425/2032 MHz first, 1425/2032 MHz retry),
`front_tp8_m16384` (1282/2032 MHz first, 1455/2032 MHz retry),
`tail_tp1_m8192` (1290/2032 MHz first, 1297/2032 MHz retry),
`tail_tp1_m16384` (1230/2032 MHz first, 1252/2032 MHz retry). They are
disclosed per the protocol (no ratio gate loosened); their paired
speedups vs the stock chain are in the contract table below.

<details><summary>sm_100a per-row receipts</summary>

| row (B200, sm_100a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---:|---:|---|---|---|
| front_tp1_m1 | decode | 49.70 us | 50.11 us | 0.9917 | pass | yes |
sealed |
| front_tp1_m2 | decode | 50.08 us | 49.76 us | 1.0064 | pass | yes |
sealed |
| front_tp1_m4 | decode | 49.85 us | 50.11 us | 0.9949 | pass | yes |
sealed |
| front_tp1_m8 | decode | 49.73 us | 50.05 us | 0.9936 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.30 us | 50.05 us | 1.0051 | pass | yes |
sealed |
| front_tp1_m32 | decode | 50.21 us | 50.21 us | 1.0000 | pass | yes |
sealed |
| front_tp1_m64 | decode | 52.86 us | 52.96 us | 0.9982 | pass | yes |
sealed |
| front_tp1_m128 | decode | 58.72 us | 58.78 us | 0.9989 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 51.68 us | 51.78 us | 0.9981 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 84.48 us | 83.42 us | 1.0127 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | — | — | — | — | — | disclosed: first:
endpoint-drift gate, ratio 0.9992, correct, bitwise; retry:
endpoint-drift gate, ratio 1.0005, correct, bitwise |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1665/1965 MHz first, 1650/1965 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1305/1965 MHz first, 1507/1965 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1440/1965 MHz first, 1447/1965 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1365/1965 MHz first, 1387/1965 MHz retry) |
| front_tp8_m1 | decode | 21.57 us | 21.50 us | 1.0030 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.54 us | 21.54 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.73 us | 21.73 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.54 us | 21.57 us | 0.9986 | pass | yes |
sealed |
| front_tp8_m16 | decode | 21.92 us | 21.89 us | 1.0015 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.17 us | 23.17 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.50 us | 25.50 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.13 us | 31.17 us | 0.9990 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 34.56 us | 34.78 us | 0.9936 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 45.73 us | 45.89 us | 0.9965 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 72.13 us | 71.30 us | 1.0117 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 115.97 us | 116.16 us | 0.9983 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 230.11 us | 230.81 us | 0.9969 | pass |
yes | sealed (retry) |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1567/1965 MHz first, 1530/1965 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1425/1965 MHz first, 1425/1965 MHz retry) |
| tail_tp1_m1 | decode | 31.14 us | 31.23 us | 0.9969 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.23 us | 31.26 us | 0.9989 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 31.33 us | 31.39 us | 0.9980 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 31.52 us | 31.62 us | 0.9970 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.50 us | 33.57 us | 0.9981 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.08 us | 34.10 us | 0.9995 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.09 us | 36.13 us | 0.9991 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 42.78 us | 39.42 us | 1.0852 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 43.62 us | 43.65 us | 0.9993 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 56.90 us | 57.02 us | 0.9978 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 101.73 us | 102.24 us | 0.9950 | pass | yes
| sealed |
| tail_tp1_m2048 | prefill | 193.82 us | 193.37 us | 1.0023 | pass | yes
| sealed |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1552/1965 MHz first, 1597/1965 MHz retry) |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1470/1965 MHz first, 1477/1965 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1395/1965 MHz first, 1425/1965 MHz retry) |
| tail_tp8_m1 | decode | 8.00 us | 8.00 us | 1.0000 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.06 us | 8.06 us | 1.0000 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.16 us | 8.13 us | 1.0039 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.22 us | 8.19 us | 1.0039 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 9.85 us | 10.21 us | 0.9654 | pass | yes |
sealed |
| tail_tp8_m32 | decode | 11.10 us | 10.97 us | 1.0118 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 12.10 us | 12.19 us | 0.9921 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 14.66 us | 14.78 us | 0.9914 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 15.90 us | 15.68 us | 1.0143 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 18.69 us | 18.75 us | 0.9966 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 26.75 us | 26.66 us | 1.0036 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 40.22 us | 40.51 us | 0.9929 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 66.40 us | 66.34 us | 1.0010 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 116.35 us | 116.19 us | 1.0014 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 222.70 us | 222.88 us | 0.9992 | pass |
yes | sealed |

</details>

<details><summary>sm_103a per-row receipts</summary>

| row (B300, sm_103a) | route | source | export | source / export |
correctness (both arms) | bitwise src == exp | verdict |
|---|---|---|---:|---:|---|---|---|
| front_tp1_m1 | decode | 50.30 us | 50.21 us | 1.0019 | pass | yes |
sealed |
| front_tp1_m2 | decode | 50.27 us | 50.66 us | 0.9924 | pass | yes |
sealed |
| front_tp1_m4 | decode | 50.66 us | 51.01 us | 0.9931 | pass | yes |
sealed |
| front_tp1_m8 | decode | 50.72 us | 50.75 us | 0.9994 | pass | yes |
sealed |
| front_tp1_m16 | decode | 50.91 us | 51.74 us | 0.9839 | pass | yes |
sealed |
| front_tp1_m32 | decode | 51.07 us | 51.09 us | 0.9997 | pass | yes |
sealed |
| front_tp1_m64 | decode | 54.18 us | 54.24 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m128 | decode | 59.94 us | 59.94 us | 1.0000 | pass | yes |
sealed |
| front_tp1_m256 | prefill | 52.86 us | 52.93 us | 0.9988 | pass | yes |
sealed |
| front_tp1_m512 | prefill | 82.27 us | 82.40 us | 0.9984 | pass | yes |
sealed |
| front_tp1_m1024 | prefill | 154.39 us | 154.63 us | 0.9984 | pass |
yes | sealed |
| front_tp1_m2048 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1575/2032 MHz first, 1627/2032 MHz retry) |
| front_tp1_m4096 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1327/2032 MHz first, 1725/2032 MHz retry) |
| front_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1275/2032 MHz first, 1275/2032 MHz retry) |
| front_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1230/2032 MHz first, 1237/2032 MHz retry) |
| front_tp8_m1 | decode | 21.66 us | 21.63 us | 1.0014 | pass | yes |
sealed |
| front_tp8_m2 | decode | 21.73 us | 21.76 us | 0.9985 | pass | yes |
sealed |
| front_tp8_m4 | decode | 21.98 us | 21.98 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m8 | decode | 21.76 us | 21.79 us | 0.9985 | pass | yes |
sealed |
| front_tp8_m16 | decode | 22.05 us | 22.14 us | 0.9957 | pass | yes |
sealed |
| front_tp8_m32 | decode | 23.23 us | 23.30 us | 0.9972 | pass | yes |
sealed |
| front_tp8_m64 | decode | 25.70 us | 25.76 us | 0.9975 | pass | yes |
sealed |
| front_tp8_m128 | decode | 31.84 us | 31.84 us | 1.0000 | pass | yes |
sealed |
| front_tp8_m256 | prefill | 33.73 us | 33.79 us | 0.9981 | pass | yes |
sealed |
| front_tp8_m512 | prefill | 43.10 us | 43.01 us | 1.0023 | pass | yes |
sealed |
| front_tp8_m1024 | prefill | 69.78 us | 69.28 us | 1.0072 | pass | yes
| sealed |
| front_tp8_m2048 | prefill | 113.03 us | 113.28 us | 0.9977 | pass |
yes | sealed |
| front_tp8_m4096 | prefill | 227.20 us | 227.59 us | 0.9983 | pass |
yes | sealed |
| front_tp8_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1425/2032 MHz first, 1425/2032 MHz retry) |
| front_tp8_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1282/2032 MHz first, 1455/2032 MHz retry) |
| tail_tp1_m1 | decode | 31.78 us | 31.81 us | 0.9990 | pass | yes |
sealed |
| tail_tp1_m2 | decode | 31.84 us | 31.84 us | 1.0000 | pass | yes |
sealed |
| tail_tp1_m4 | decode | 32.07 us | 31.94 us | 1.0040 | pass | yes |
sealed |
| tail_tp1_m8 | decode | 32.06 us | 32.13 us | 0.9980 | pass | yes |
sealed |
| tail_tp1_m16 | decode | 33.79 us | 33.82 us | 0.9991 | pass | yes |
sealed |
| tail_tp1_m32 | decode | 34.50 us | 34.59 us | 0.9972 | pass | yes |
sealed |
| tail_tp1_m64 | decode | 36.61 us | 36.64 us | 0.9991 | pass | yes |
sealed |
| tail_tp1_m128 | decode | 42.66 us | 40.06 us | 1.0647 | pass | yes |
sealed |
| tail_tp1_m256 | prefill | 43.49 us | 43.20 us | 1.0067 | pass | yes |
sealed |
| tail_tp1_m512 | prefill | 54.50 us | 54.59 us | 0.9983 | pass | yes |
sealed |
| tail_tp1_m1024 | prefill | 99.07 us | 99.68 us | 0.9939 | pass | yes |
sealed |
| tail_tp1_m2048 | prefill | 187.23 us | 188.00 us | 0.9959 | pass | yes
| sealed |
| tail_tp1_m4096 | prefill | — | — | — | — | — | disclosed: first:
endpoint-drift gate, ratio 0.9994, correct, bitwise; retry:
clock-unqualified 1440/2032 MHz |
| tail_tp1_m8192 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1290/2032 MHz first, 1297/2032 MHz retry) |
| tail_tp1_m16384 | prefill | — | — | — | — | — | disclosed:
clock-unqualified (1230/2032 MHz first, 1252/2032 MHz retry) |
| tail_tp8_m1 | decode | 7.97 us | 8.00 us | 0.9961 | pass | yes |
sealed |
| tail_tp8_m2 | decode | 8.03 us | 8.00 us | 1.0040 | pass | yes |
sealed |
| tail_tp8_m4 | decode | 8.00 us | 8.06 us | 0.9921 | pass | yes |
sealed |
| tail_tp8_m8 | decode | 8.06 us | 8.13 us | 0.9921 | pass | yes |
sealed |
| tail_tp8_m16 | decode | 9.47 us | 9.38 us | 1.0102 | pass | yes |
sealed |
| tail_tp8_m32 | decode | 11.07 us | 11.20 us | 0.9886 | pass | yes |
sealed |
| tail_tp8_m64 | decode | 11.97 us | 12.19 us | 0.9816 | pass | yes |
sealed |
| tail_tp8_m128 | decode | 14.43 us | 14.56 us | 0.9912 | pass | yes |
sealed |
| tail_tp8_m256 | prefill | 15.20 us | 15.14 us | 1.0042 | pass | yes |
sealed |
| tail_tp8_m512 | prefill | 17.66 us | 17.79 us | 0.9928 | pass | yes |
sealed |
| tail_tp8_m1024 | prefill | 24.96 us | 25.09 us | 0.9949 | pass | yes |
sealed |
| tail_tp8_m2048 | prefill | 38.14 us | 38.69 us | 0.9859 | pass | yes |
sealed |
| tail_tp8_m4096 | prefill | 63.42 us | 63.55 us | 0.9980 | pass | yes |
sealed |
| tail_tp8_m8192 | prefill | 112.80 us | 112.83 us | 0.9997 | pass | yes
| sealed |
| tail_tp8_m16384 | prefill | 212.13 us | 212.39 us | 0.9988 | pass |
yes | sealed |

</details>

### Measured speedups (Cake contract, paired cold-L2 CUPTI graph timing
vs the fastest stock chain of each row)

Kernel arm = the exported programs of this PR (CUDA-graph form, three
alternating groups, cold-L2 CUPTI timing, correctness of both arms
against the torch reference, graph == eager); denominator = the fastest
stock chain of the row (see Baselines). **B200: 60 / 60 rows > 1.00, min
1.024 (`tail_tp1_m4096`), geomean 1.603. B300: 60 / 60 rows > 1.00, min
1.036 (`tail_tp1_m16384`), geomean 1.612.**

| row | B200: exported program / fastest stock chain us = speedup |
B300: same |
|---|---|---|
| `front_tp1_m1` | 50.91 / 88.41 = 1.737 | 50.78 / 85.70 = 1.687 |
| `front_tp1_m2` | 51.78 / 88.06 = 1.701 | 51.17 / 86.14 = 1.684 |
| `front_tp1_m4` | 51.01 / 89.28 = 1.750 | 51.39 / 87.11 = 1.695 |
| `front_tp1_m8` | 51.04 / 87.10 = 1.707 | 50.78 / 86.50 = 1.703 |
| `front_tp1_m16` | 50.43 / 88.67 = 1.758 | 50.82 / 88.64 = 1.744 |
| `front_tp1_m32` | 51.20 / 90.56 = 1.769 | 51.55 / 90.05 = 1.747 |
| `front_tp1_m64` | 54.37 / 90.94 = 1.673 | 54.59 / 90.47 = 1.657 |
| `front_tp1_m128` | 58.85 / 94.94 = 1.613 | 58.91 / 94.50 = 1.604 |
| `front_tp1_m256` | 52.42 / 115.78 = 2.209 | 52.26 / 114.30 = 2.187 |
| `front_tp1_m512` | 84.51 / 165.50 = 1.958 | 80.03 / 159.23 = 1.990 |
| `front_tp1_m1024` | 166.70 / 289.79 = 1.738 | 150.59 / 265.51 = 1.763
|
| `front_tp1_m2048` | 314.59 / 586.59 = 1.865 | 294.75 / 557.09 = 1.890
|
| `front_tp1_m4096` | 646.81 / 1174.97 = 1.817 | 603.60 / 1149.69 =
1.905 |
| `front_tp1_m8192` | 1303.43 / 2346.15 = 1.800 | 1222.76 / 2293.73 =
1.876 |
| `front_tp1_m16384` | 2570.99 / 4653.25 = 1.810 | 2422.89 / 4549.66 =
1.878 |
| `front_tp8_m1` | 21.82 / 59.71 = 2.736 | 21.76 / 56.74 = 2.607 |
| `front_tp8_m2` | 21.92 / 58.69 = 2.678 | 21.95 / 56.70 = 2.583 |
| `front_tp8_m4` | 21.89 / 57.60 = 2.631 | 21.73 / 55.81 = 2.568 |
| `front_tp8_m8` | 22.02 / 57.54 = 2.613 | 21.82 / 55.68 = 2.551 |
| `front_tp8_m16` | 22.21 / 56.86 = 2.561 | 22.15 / 56.32 = 2.543 |
| `front_tp8_m32` | 23.46 / 61.60 = 2.626 | 23.49 / 60.71 = 2.584 |
| `front_tp8_m64` | 25.76 / 60.22 = 2.338 | 25.63 / 59.74 = 2.331 |
| `front_tp8_m128` | 31.77 / 63.17 = 1.988 | 31.81 / 62.50 = 1.965 |
| `front_tp8_m256` | 34.78 / 72.89 = 2.096 | 33.79 / 71.33 = 2.111 |
| `front_tp8_m512` | 46.46 / 79.45 = 1.710 | 42.69 / 77.02 = 1.804 |
| `front_tp8_m1024` | 71.68 / 107.10 = 1.494 | 68.10 / 102.66 = 1.508 |
| `front_tp8_m2048` | 117.09 / 172.45 = 1.473 | 111.36 / 162.66 = 1.461
|
| `front_tp8_m4096` | 236.54 / 313.39 = 1.325 | 223.78 / 300.00 = 1.341
|
| `front_tp8_m8192` | 476.12 / 636.12 = 1.336 | 455.78 / 629.51 = 1.381
|
| `front_tp8_m16384` | 969.91 / 1297.91 = 1.338 | 867.64 / 1245.58 =
1.436 |
| `tail_tp1_m1` | 31.39 / 40.26 = 1.282 | 31.65 / 39.59 = 1.251 |
| `tail_tp1_m2` | 31.46 / 39.55 = 1.257 | 31.68 / 39.94 = 1.261 |
| `tail_tp1_m4` | 31.61 / 40.26 = 1.273 | 31.87 / 40.51 = 1.271 |
| `tail_tp1_m8` | 31.81 / 39.71 = 1.248 | 31.94 / 40.16 = 1.258 |
| `tail_tp1_m16` | 34.02 / 39.17 = 1.151 | 33.83 / 39.52 = 1.168 |
| `tail_tp1_m32` | 34.50 / 39.49 = 1.145 | 34.59 / 39.81 = 1.151 |
| `tail_tp1_m64` | 36.54 / 40.35 = 1.104 | 36.64 / 41.06 = 1.121 |
| `tail_tp1_m128` | 40.09 / 44.86 = 1.119 | 40.06 / 44.99 = 1.123 |
| `tail_tp1_m256` | 43.68 / 49.31 = 1.129 | 43.36 / 49.28 = 1.137 |
| `tail_tp1_m512` | 57.47 / 71.68 = 1.247 | 53.86 / 68.48 = 1.272 |
| `tail_tp1_m1024` | 103.30 / 122.66 = 1.187 | 97.82 / 115.49 = 1.181 |
| `tail_tp1_m2048` | 200.89 / 212.51 = 1.058 | 192.58 / 201.28 = 1.045 |
| `tail_tp1_m4096` | 408.09 / 417.69 = 1.024 | 388.71 / 408.77 = 1.052 |
| `tail_tp1_m8192` | 820.83 / 856.97 = 1.044 | 802.47 / 860.12 = 1.072 |
| `tail_tp1_m16384` | 1667.75 / 1716.10 = 1.029 | 1671.70 / 1731.39 =
1.036 |
| `tail_tp8_m1` | 7.97 / 15.87 = 1.992 (1.996, 1.992, 1.996) | 7.97 /
15.78 = 1.980 (1.996, 1.980, 1.996) |
| `tail_tp8_m2` | 7.90 / 16.64 = 2.105 (2.123, 2.105, 2.119) | 7.90 /
16.54 = 2.093 (2.138, 2.093, 2.138) |
| `tail_tp8_m4` | 7.97 / 16.93 = 2.124 (2.126, 2.124, 2.126) | 7.94 /
16.93 = 2.133 (2.182, 2.133, 2.182) |
| `tail_tp8_m8` | 8.10 / 16.61 = 2.051 (2.031, 2.051, 2.035) | 8.10 /
16.45 = 2.032 (2.051, 2.032, 2.051) |
| `tail_tp8_m16` | 9.41 / 18.21 = 1.935 (1.718, 1.935, 1.718) | 9.09 /
17.89 = 1.968 (1.838, 1.972, 1.838) |
| `tail_tp8_m32` | 10.53 / 17.70 = 1.681 (1.631, 1.681, 1.631) | 10.69 /
17.50 = 1.638 (1.612, 1.633, 1.609) |
| `tail_tp8_m64` | 12.13 / 19.36 = 1.596 (1.584) | 12.10 / 19.20 = 1.587
(1.573) |
| `tail_tp8_m128` | 14.56 / 20.19 = 1.387 | 14.37 / 19.87 = 1.383 |
| `tail_tp8_m256` | 15.94 / 22.34 = 1.402 | 15.23 / 21.79 = 1.431 |
| `tail_tp8_m512` | 18.98 / 27.68 = 1.459 | 17.92 / 26.85 = 1.498 |
| `tail_tp8_m1024` | 26.69 / 36.58 = 1.371 | 24.90 / 35.39 = 1.422 |
| `tail_tp8_m2048` | 39.90 / 51.23 = 1.284 | 37.89 / 49.44 = 1.305 |
| `tail_tp8_m4096` | 66.02 / 96.13 = 1.456 | 62.69 / 91.87 = 1.466 |
| `tail_tp8_m8192` | 117.47 / 181.95 = 1.549 | 111.36 / 175.01 = 1.571 |
| `tail_tp8_m16384` | 237.34 / 350.73 = 1.478 | 219.94 / 335.92 = 1.527
|

Values in parentheses: the same row in the additional independent
process(es) of the short-row re-measurement (tail TP8 T <= 32 at 300 ms
per arm, T = 64 at 250 ms per arm; the default window of these rows
exceeds the protocol's sample cap, so they are timed only in these
dedicated processes).

### Baselines and their source PRs

- **Stock chain (Cake contract denominator, per row the fastest of):**
torch / cuBLAS `torch.mm` / `torch.addmm` (FP32-upcast or
`out_dtype=float32` router GEMM, BF16 latent / shared GEMMs, `addmm` for
the tail sum) and every FlashInfer `mm_bf16` backend that computes the
product (`auto`, `cudnn`, `cublaslt`, `tgv`, `tinygemm`, `cutlass`,
`cute-dsl`), `flashinfer.rmsnorm` for the tail norm, torch `silu` /
`mul` / `topk` for the elementwise steps; same chain and same shapes as
#5575 / #5584 / #5647.
- **Previous rounds of this operator (the programs this PR replaces):**
#5647 (443347d3e, 2026-09-28), #5584 (1eb503cd3, 2026-09-27), #5575
(initial package); the exported-program contract of #5647 is the per-row
comparison baseline (no row may regress by more than 2 % against it).
- **Operator semantics reference:** `nvidia/Kimi-K3-NVFP4`
`modeling_kimi_linear.py` (`KimiSparseMoeBlock`, `KimiMLP`,
`KimiRMSNorm`, `SituAndMul`, `KimiMoEGate`); serving layout from vLLM
`models/kimi_k3/nvidia/{model.py, latent_moe_runner.py,
low_latency_gemm.py}` and SGLang `srt/models/kimi_k3.py`.
- **Test oracle:** the torch reference in
`tests/experimental/test_cake_kimi_k3_latent_moe.py` (transcribed from
the Cake reference module).
- **Merge-base:** upstream `main` 443347d3e (#5647, 2026-09-28); no
upstream change to the package or the baselines between the merge-base
and this branch.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_latent_moe.py
```

`pytest tests/experimental/test_cake_kimi_k3_latent_moe.py`: **40
passed, 24 warnings in 13.91s (B200) / 40 passed, 24 warnings in 8.14s
(B300)** on B200 (sm_100a) and on B300 (sm_103a), run on the delivered
tree in the export clone of each GPU (plan / route tests incl. the new
`front_split_plan` rules + GPU correctness for both stages x TP {1, 8} x
the row set, bit-identical re-launch and CUDA-graph replay, `y`
byte-exact). Producer-side gates on the same kernel tree: e2e GPU slice,
unit tests, bench-regression, compute-sanitizer synccheck / memcheck (0
errors, both GPUs), four launch-sequence stress passes of the 62-row
contract per GPU (canonical, reverse, shuffle 717 / 718; 62 / 62 correct
each) and a poisoned-workspace check of the new split fix-up path (NaN /
+-3e38 in the fp32 partial slots before every launch of the split rows;
15 / 15 per GPU, counters zero).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved Kimi K3 latent MoE prefill routing with adaptive work
splitting and weight-streaming variants, including trailing-wave
execution.
  * Updated partial-result accumulation for segmented work.
* **Documentation**
  * Clarified when prefill routing uses these execution strategies.
* **Tests**
* Added coverage for prefill planning, split behavior, and
kernel-variant selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <yyihuang@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [dfd17d6](https://github.com/flashinfer-ai/flashinfer/commit/dfd17d64d8c0b48161cdcacea0bd81ce7f124bb2)

- **作者**: eigen
- **时间**: 2026-09-29T21:09:04Z
- **提交信息**: perf(cake_vision_backend): round 5 — PDL prologue overlap (PDL_EARLY) census windows, m_e8 / m_e8_cs tiles, fc1 stream-K twins (sm_100a/sm_103a) (#5691)

## Summary

Round 5 of the generated-program export of the Cake Kimi-K3 vision tower
(MoonViT-3D encoder, 27 layers, + PatchMergerV2) for `sm_100a` (B200)
and `sm_103a` (B300/GB300) into
`flashinfer/experimental/kimi_k3_vision_tower` (#4568, tracker #4254;
round 1 = #5554, round 2 = #5570, round 3 = #5623, round 4 = #5643). The
branch is cut from upstream `main` `90a709ca8` (which contains the
round-4 delivery); the round-5 commits are the scaffold mirror and the
regenerated delivery.

- `3c16ac92a` -- the round-5 Cake host policy mirrored in the scaffold
(`cake_backend.py`, `cake_jit.py`, tests). All changes are GEMM routing
with identical numerics and unchanged kernel parameters: (1) two PDL
binaries per GEMM tile -- the production one and the `PDL_EARLY` one
(the grid-dependency wait moved from the common prologue into the load /
epilogue roles so the first weight stages stream before it,
`launch_dependents` at entry); the host picks the early binary per
launch from the form's census window (`PDL_EARLY_WINDOW` /
`PDL_EARLY_DEFAULT_WINDOW`, `pdl_early_on`) and never on the stream-K /
tail / multicast / `pos` tiles (`pdl_early_selected`); the registry
names it `gemm:<variant>:<tile>:pdle`; (2) the tiles `m_e8` / `m_e8_cs`
(eight-warp 256 x 128 pair tile of the K = 1024 norm GEMMs for 1656 < M
<= 4096, `norm_qkv_rope` above 2304) and `m_sk` (stream-K twin of the
256 x 128 pair tile) for `residual_fc1` at its census points (`m_sk` at
4609..4864 rows, `l_sk` for 15873 <= M <= 105984), and the widened
projector stream-K window (a removed partial round worth >= 9 % of the
rounds wins up to a 60 % tail); (3) the plan carries `gemm_kernel_keys`
(variant -> tile + PDL form) next to `gemm_configs`, `_gemm_launch`
binds the module by that key, `route_metadata` reports
`gemm_kernel_keys` / `gemm_pdl_early`, and `required_kernel_keys` is
derived from an exhaustive census (every 128-row tile up to the largest
routing window, every rule boundary, every PDL window edge): 47 / 48
keys per arch (43 GEMM keys, 25 of them `:pdle`). Tests: tile boundaries
over M = 1..20000 (incl. `m_e8` / `m_e8_cs` / `m_sk` / `l_sk` and the
widened `l` / `l_sk` alternation), the fc1 census, the PDL window edges
and exclusions, launch geometry of the fc1 twins, the required-key set,
a CPU plan with the fc1 stream-K workspace, and the per-variant GEMM key
of every contract row against the Cake export protocol (the mirror fails
loudly if it disagrees with the protocol).
- `4e603e857` -- the generated delivery only: `cake_jit.py` `MODULES` /
`KERNELS` registries (95 exact-architecture programs: 47 on `sm_100a` +
48 on `sm_103a`) and
`csrc/cake_kimi_k3_vision_tower/{sm_100a,sm_103a}/*_{kernel,binding}.cu`
(190 generated sources; excluded from the formatting hooks via
`csrc/.clang-format`; identities are receipt-bound). Both literals are
generated; do not edit by hand. Relative to round 4: 25 `PDL_EARLY`
programs per architecture are new, `gemm:norm_gelu:m_e8:pdle`,
`gemm:norm_qkv_rope:m_e8_cs:pdle`, `gemm:residual_fc1[_sqxw]:m_sk` and
`gemm:residual_fc1[_sqxw]:l_sk` are new tiles; the plain PDL programs of
the tiles that are always inside their window are no longer reachable
and are removed; attention, merge and rmsnorm-apply programs are
unchanged. The delivery patch regenerated on B200 and on B300 is
byte-identical (SHA-256
`e97791afdadab3f9a06327d71e297f60deee6beeeec7b12ff3b940ffc1b7c1f0`).
This head replaces the earlier `619248b49` (producer `d8e653fb949`,
patch `f095df67…`): the Cake producer was re-merged with its main before
delivery, and main had added the traced-schedule identity to the
exported module closure, which re-keys every module id / kernel symbol;
every generated kernel and binding source is byte-identical modulo that
id (verified by applying both patches to the `3c16ac92a` scaffold), so
the kernels themselves are unchanged and the round was re-run end to end
on the merged producer.

Kernel changes behind the regenerated programs (source project round 5,
CAKE-749): PDL prologue overlap (`PDL_EARLY`) inside per-form census
windows, the fc1 stream-K twins and the `m_e8` tiles at the
census-shaped contract shapes, the widened projector stream-K window.
Every accepted form is bitwise identical to production or (the stream-K
re-routings) reorders the f32 partial sums with pooled per-seed error
statistics not worse than baseline on both architectures (numbers in the
source project's round-5 design record).

## Evidence (Cake export protocol `k3-export-r5m`, producer
`42fa0ae56f7` = round-5 tree `d8e653fb949` merged with Cake main
`9a4dca296a8`, target `3c16ac92a`)

Every contract row is measured on the source (Cake production launcher)
and the exported programs in counterbalanced groups; `source_ms /
export_ms >= 0.97`, directional disagreement `<= 0.02`, endpoint drift
`<= 0.02`, correctness = bitwise `source == export` on every row before
and after timing. One uninterrupted single-cache round per architecture
on the final producer: part A (fresh state, 1 GPU) then part B (the
remaining 17 rows, 4 GPUs) against the same clone, state and JIT cache.
Protocol frozen on the final producer: 44 routes, 47 + 48 kernel keys,
484 stages, 0 PDL violations.

| arch | GPU | rows measured | passed | source/export (min .. max) |
directional disagreement | endpoint drift |
|---|---|---|---|---|---|---|
| sm_100a | B200 (NSC gpu-32; part A 1 GPU, part B 4 GPUs, one build
session) | 22 | 22 | 0.9845 (smoke_ragged) .. 1.0674 (smoke_2x2); perf
rows 0.9903 .. 1.0034, geomean 1.0014 | max 0.0033 (batch4_1024x768) |
max 0.0097 (batch4_1024x768) |
| sm_103a | B300 (PDX pool0-0364; part A 1 GPU, part B 4 GPUs, one build
session) | 22 | 22 | 0.9934 (img_640x480) .. 1.0605 (smoke_2x2); perf
rows 0.9934 .. 1.0042, geomean 1.0026 | max 0.0013 (img_2560x1440) | max
0.0075 (batch4_1024x768) |

Attention-heavy rows (pointer-ABI attention, bar `source/export >=
0.99`): img_1920x1080 1.0002 / 1.0002, doc_1240x1754 1.0003 / 1.0003,
img_2560x1440 1.0002 / 1.0004, img_3840x2160 1.0002 / 0.9999,
img_max_4096sq 0.9998 / 1.0006, video_1080p_4f 1.0009 / 1.0003,
video_720p_32f 1.0002 / 1.0001, video_480p_64f 0.9998 / 1.0001 (sm_100a
/ sm_103a); every timed row >= 0.9845 on both arches (bar 0.97; every
perf row >= 0.9903). Bitwise `source == export` 22/22 before and after
timing on both arches; 47 / 48 modules referenced with no conflicting
`binary_sha256` across receipts (single-cache identity).

Pooled smoke rows (8 seeds, candidate/reference-chain mean-error ratio /
violation ratio): smoke_2x2 0.9993 / 1.0070, smoke_ragged 0.9995 /
0.9974, smoke_t3 1.0020 / 1.0040 (sm_100a); 0.9993 / 1.0070, 1.0001 /
1.0021, 0.9993 / 0.9991 (sm_103a); all passed.

Receipts, raw timings and state copies stay on the cluster (host / path
/ size / SHA-256 recorded in the source project's design record and
`exports/kimi_k3_vision_tower/README.md`).

## Baselines and their source PRs

The export's correctness gate compares both arms against the FP32 tower
oracle relative to the HF BF16 chain whose attention is the fastest
FlashInfer ragged BF16 route of this checkout
(`BatchPrefillWithRaggedKVCacheWrapper(kv_layout="NHD", backend=...)`,
chosen by timing per row). Branch upstream merge-base: `90a709ca8`
(2026-09-28); the previous merge-base was `7ea849ffb` (2026-09-28, the
squash merge of #5623), the round-4 delivery merged as `5b0f975b4`
(#5643).

- `fa2` route: `flashinfer/prefill.py` (last upstream change #5350
`7685a893e`, 2026-09-24), `csrc/batch_prefill.cu` (#5176 `e0a18900c`,
2026-09-21), `include/flashinfer/attention/prefill.cuh` (#5239
`b8107c7fd`, 2026-09-17).
- `cudnn` route: `flashinfer/cudnn/prefill.py` (#5350 `7685a893e`,
2026-09-24).
- `cutlass` route: `csrc/fmha_cutlass_sm100.cu` (#3064 `1aa32d03e`,
2026-05-08), `csrc/fmha_cutlass_sm100_binding.cu` (#2047 `db2aacbd3`,
2025-12-17).
- `cute-dsl` route: `flashinfer/cute_dsl/attention/fmha/` (#4859
`f17b77260`, 2026-09-18; cubin refresh #4997 `75038cdf6`, 2026-09-10).
- Chain RMSNorm: `flashinfer/norm/` (#5305 `012542c85`, 2026-09-18).
- Previous programs (replaced by this PR): round-4 delivery from #5643
(merged `5b0f975b4`, 2026-09-28), round-3 from #5623 (`7ea849ffb`),
round-2 from #5570 (`b6e4ebfdd`), round-1 from #5554 (`6dd3104a7`); the
package tests / FP32-oracle stage tests
(`tests/experimental/test_cake_kimi_k3_vision_tower.py`) are the test
oracle, extended in `3c16ac92a` for the round-5 routing (PDL_EARLY keys,
fc1 stream-K twins, m_e8 tiles, contract-row key table).

No upstream commit between `5b0f975b4` and the current upstream `main`
(`90a709ca8`, 2026-09-28) touched any of the route files above.

## Test

```
pytest tests/experimental/test_cake_kimi_k3_vision_tower.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8500f4f](https://github.com/flashinfer-ai/flashinfer/commit/8500f4fb8f9d3cf02e697efe5045c0009327ec3a)

- **作者**: Taylor Yeonbok Lee
- **时间**: 2026-09-29T20:49:26Z
- **提交信息**: perf(jit): disable pre-RA instruction scheduling for the trtllm-gen MoE manifest (#5435)

## 📌 Description

JIT-compiling `fused_moe_trtllm_sm107` takes ~565 s on aarch64, and a
single translation unit accounts for essentially all of it:
`trtllm_batched_gemm_runner.cu` compiles in 565 s on its own.
This narrows that to ~91 s by disabling GCC's pre-register-allocation
instruction scheduling for this module on aarch64 , which is the default
x86 already uses.
### Why that one file is so expensive

`flashinferMetaInfo.h` declares `tllmGenBatchedGemmList` as `static
const`, and it cannot be `constexpr`: `BatchedGemmConfig` embeds
`BatchedGemmOptions`, which is polymorphic (virtual destructor) and
holds `std::vector`/`std::string` members, so the type is not a literal
type.
The manifest therefore cannot live in `.rodata`.
The host compiler emits it as load-time initialization code instead, for
the 3378-entry Rubin package that is 3.4 MB of `.text.startup` against
232 bytes of `.rodata`, driven by `GLOBAL__sub_I` /
`static_initialization_and_destruction_0()`.

The whole manifest lands in one enormous straight-line basic block, and
GCC's instruction scheduling is superlinear in block size:

| stage | time |
|---|---:|
| `gcc (compiling)` | 569.17 s |
| `cicc` | 2.69 s |
| `cudafe++` | 1.38 s |
| `ptxas` | 0.17 s |
| `fatbinary` | 0.16 s |

(`nvcc --time`, 575 s total.) Within that host compile, GCC's
`-ftime-report` attributes **465 s (85%) to the `scheduling` pass**;
nothing else exceeds 25 s.

### Why the pre-RA pass specifically

GCC schedules once before and once after register allocation. x86
disables the pre-allocation pass by default, because lengthening live
ranges ahead of allocation costs more than it gains on a register-poor
target; aarch64 leaves it on. An initializer that only stores constants
gives that pass nothing worth reordering.

Per-module measurements on VR, cold JIT cache, 352-core aarch64 host:

| configuration | module | `batched_gemm_runner` TU |
|---|---:|---:|
| baseline | 565 s | 565 s |
| `-fno-schedule-insns` | **197 s** | **91 s** |

### Scope and safety

- Applied only when the host compiler is GCC **and** the target is
aarch64. On x86 the pass is already off, so this is a no-op there.
- Post-allocation scheduling still runs on every target.
- `-Xcompiler` reaches only the host compiler; `cicc` and `ptxas` still
see `-O3` and the emitted cubins are unchanged.
- What is given up is instruction ordering in code that runs once per
process during initialization.


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

- **Bug Fixes**
- Improved fused mixture-of-experts module compilation on ARM64 systems
using GCC.
- Added compiler-specific handling to prevent problematic instruction
scheduling during CUDA extension builds.
- Preserved existing compilation behavior on other platforms and with
other host compilers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [6a8cd69](https://github.com/flashinfer-ai/flashinfer/commit/6a8cd698a730be4eecdb4b6204e73dcbb376493c)

- **作者**: eigen
- **时间**: 2026-09-29T20:10:20Z
- **提交信息**: perf(cake_gemm): evict_first weight stream and descriptor prefetch for the fused grouped FP8 gate_up + SwiGLU + quant program (#5692)

Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5645 (fused MoE gate_up projection for Blackwell SM100a:
pair + tail kernels, mixed-schedule route,
routing-aware route rule).  The prepared API

`flashinfer.gemm.prepare_group_gemm_fp8_nt_groupwise_contiguous_silu_quant(a,
b, a_scale, b_scale, m_indices).launch()`
and its contract are unchanged. Two changes, both bit-identical to the
three-kernel chain on every routing tested (data
movement order, accumulation order and rounding points are untouched;
only a TMA descriptor prefetch and an L2 eviction
priority operand are added):

- **`evict_first` on the per-expert weight stream (pair, tail and
mixed-schedule kernels).** Each expert's B tile is read
exactly once per output tile, while the activation rows of a tile are
re-read by the eight N-tile clusters and the scale
tensors by every tile. On the wide-EP32 gate_up shape `[M=4096, 2H=2048,
K=4096, G=16]` the 8 MiB-per-expert stream
displaces those reused lines from L2 well before its nominal turnover
(both operands' 128-row TMA boxes sit at a 4 KB row
stride). Marking the B loads `evict_first` (`.L2::cache_hint` on the
`cp.async.bulk.tensor` loads; no `evict_last`
anywhere) keeps them resident. Paired on B200 (same node, same process,
one CUDA graph per arm re-captured per group,
eight counterbalanced groups, CUPTI cold-L2 active-union medians,
NVRTC-built source programs of both arms): pair route
**1.1091x** (uniform routing, 44.11 → 39.74 µs), **1.0735x** (two
odd-block experts; the tail kernel's hint
  adds ≈ 2 % on this row), **1.0151x** at `M = 8192`;
mixed-schedule route **1.0231x** (random 128-aligned routing),
**1.0142x** (mixed-tail routing), 1.0419x (all-odd routing,
mixed route forced). SASS instruction count, registers, spills and MUFU
population are unchanged for all three kernels.
The residency bound that motivated it: the same 128 pair tiles run in
36.5 µs when B is L2-resident (one expert × 4096
  rows) versus 44.1 µs with per-expert B (16 × 256 rows).
- **TMA descriptor prefetch in the fused producers (pair and
mixed-schedule kernels).** The A and B TMA producer warps
issue `prefetch.tensormap` for their descriptors as the first thing they
do (pair kernel: right after the programmatic
dependent-launch signal; mixed kernel: A, the 64-row A descriptor and B
at role start), so the descriptor fetch overlaps
the expert-index load and the routing scan instead of serialising in
front of the first TMA load. +8 SASS instructions,
opcode set unchanged. Paired as above against #5645's program: pair +
tail route 1.0072x (uniform), 1.0048x (two odd
experts), 1.0046x at `M = 8192`; mixed-schedule route 1.0057x (random
128-aligned), 1.0060x (mixed tail).

**Not adopted, measured on the same B200 under the same bit-identical
constraint.** Removing the routing scan altogether
(a by-value routing table replacing the expert-index loads and the
64-step scan in every role — an upper bound, since
routing must stay device-read — starts the first MMA ≈ 1 µs earlier but
slows every steady-state tile by 1.2–1.8 µs and
reads 0.982–0.986x; a loop-free ballot/ffs scan 0.79–0.85x; the round-10
warp-parallel scans 0.91–0.96x), a 74-cluster
grid at equal wave counts (0.84–0.98x), wider clusters (≤ 3 % more SMs
at the pair geometry), a stream-K K split of the
128 / 148 wave quantization (the generalised segment loop costs 16–23 %
per tile; the split itself is 1.4–4.7 % slower on
the exact-wave rows), alternative load paths of the activation kernels
(0.87–1.01x), issuing adjacent K blocks back to
back for HBM page locality (0.99 / 1.03 / 0.99 on uniform / two-odd / `M
= 8192`), and L2 tensor prefetch 4–8 blocks
ahead (0.75–0.87x: the extra L2 traffic thrashes). The remaining exit
skew (3.5–4 µs on the wide rows) is accumulated
per-tile memory-arrival jitter — uncorrelated with launch order or CTA
position — which no static or dynamic tile
assignment shortens at exact wave counts.

**Toolchain note.** The exported programs are built by nvcc (this
repository's JIT), the source programs by NVRTC; the
paired table below compares nvcc-built modules of both registries in one
process.

The exported program bundle
(`csrc/cake_grouped_fp8_fused_silu_quant/sm_100a/`) keeps the five
kernels (pair, tail,
mixed, activation, wide activation) under the same four route templates;
`MODULES` / `ROUTE_GEOMETRY` are regenerated
by the same export protocol as #5567 / #5592 / #5645. Both activation
kernels' generated sources are identical to
#5645's up to the module-hash symbol; the pair, tail and mixed kernels
differ only by the prefetch instructions and the
cache-hint operand of the B loads.

## 🔍 Related Issues

- #4254 (CAKE kernel tracker)

## Baselines and their source PRs

| Baseline | Source PR | Revision | Implementation |
| --- | --- | --- | --- |
| CuTe-DSL contiguous grouped FP8 GEMM (chain GEMM, and the GEMM of the
GEMM + activation route) | #4734 | `main 795a96b22` |
`flashinfer/gemm/gemm_base.py::group_gemm_fp8_nt_groupwise_contiguous` |
| Cake prepared contiguous grouped FP8 GEMM (chain GEMM variant; the
small-M route's GEMM for partial-tail problems from `K = 1024`) | #5500
| `main 795a96b22` |
`flashinfer/gemm/cake_group_gemm_fp8_nt_groupwise_contiguous.py::prepare_group_gemm_fp8_nt_groupwise_contiguous`
|
| `silu_and_mul` + `per_token_group_quant_8bit` (chain activation +
quantization) | upstream | `main 795a96b22` |
`flashinfer/activation.py`, `flashinfer/quantization.py` |
| Fused gate_up + SwiGLU + quant program, previous form | #5567, #5592,
#5645 | `main 795a96b22` (merge-base of this branch) |
`flashinfer/gemm/cake_grouped_fp8_fused_silu_quant.py`,
`csrc/cake_grouped_fp8_fused_silu_quant/sm_100a/` |

The test oracle is the FlashInfer chain (#4734 GEMM + `silu_and_mul` +
`per_token_group_quant_8bit`) at the same
revision; no upstream change to these entry points landed between
`795a96b22` and this branch's merge-base.

## Benchmarks (B200, 148 SMs, CUPTI kernel time, cold L2, one CUDA graph
per arm, eight counterbalanced groups)

Sealed export run, 14 rows, B200 (148 SMs): reference = NVRTC build of
the same generated program, export = the nvcc-built
modules of this PR; both chains at `main 795a96b22` (CuTe chain = #4734
GEMM + `silu_and_mul` + `per_token_group_quant_8bit`,
prepared-GEMM chain = #5500 GEMM + the same two kernels). Bitwise =
export output identical to the CuTe chain.

| row | route | fused graph µs | chain graph µs | chain / fused | scales
exact | fp8 equal (fraction) |
|---|---|---:|---:|---:|---|---:|
| wide_ep32_gate_up_uniform | fused pair + tail | 38.18 | 71.33 | 1.868x
| True | 1.0000 |
| wide_ep32_gate_up_random_aligned | fused mixed-schedule | 45.28 |
69.79 | 1.541x | True | 1.0000 |
| wide_ep32_gate_up_all_odd | GEMM + wide activation | 54.21 | 72.90 |
1.345x | True | 1.0000 |
| wide_ep32_gate_up_all_one_block | GEMM + wide activation | 39.55 |
50.08 | 1.266x | True | 1.0000 |
| wide_ep32_gate_up_mixed_tail | fused mixed-schedule | 47.01 | 70.43 |
1.498x | True | 1.0000 |
| one_pair | GEMM + activation | 8.16 | 10.46 | 1.282x | True | 1.0000 |
| odd_blocks_with_empty | GEMM + activation | 7.94 | 11.71 | 1.476x |
True | 1.0000 |
| leading_internal_empty_partial_tail | GEMM (prepared) + activation |
9.41 | 11.71 | 1.245x | True | 0.99999994 |

The one non-1.0000 fraction is the small `GEMM (prepared) + activation`
row: its GEMM is #5500's prepared kernel, whose fp32 accumulation order
differs from the CuTe GEMM of the chain, so one FP8 element of this row
rounds differently; that route is byte-identical to #5645's (activation
kernel SASS unchanged, GEMM upstream) and the same fraction is read on
the unchanged program.

Geomeans: source / export (identity, NVRTC source vs nvcc export) all
1.0307x, perf rows 1.0441x, correctness rows 1.0207x; CuTe-DSL chain /
export all **1.3715x**, perf rows **1.4914x**, correctness rows 1.2879x;
prepared-GEMM chain (#5500) / export all **1.5338x**, perf rows
**1.8067x**, correctness rows 1.3566x.

FlashInfer benchmark
(`benchmarks/bench_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`,
delivered checkout):

(`benchmarks/bench_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`,
its eight default rows, CUDA-graph replay of the prepared launcher vs
the CuTe chain graph, delivered checkout, B200 at 1965 MHz)

| row | route | fused graph µs | chain graph µs | chain / fused | scales
exact | fp8 equal |
|---|---|---:|---:|---:|---|---:|
| wide_ep32_gate_up_all_odd | GEMM + wide activation | 54.21 | 72.90 |
1.345x | True | 1. |
| wide_ep32_gate_up_all_one_block | GEMM + wide activation | 39.55 |
50.08 | 1.266x | True | 1. |
| wide_ep32_gate_up_mixed_tail | fused mixed-schedule | 47.01 | 70.43 |
1.498x | True | 1.0000 |
| one_pair | GEMM + activation | 8.16 | 10.46 | 1.282x | True | 1.0000 |
| odd_blocks_with_empty | GEMM + activation | 7.94 | 11.71 | 1.476x |
True | 1.0000 |
| leading_internal_empty_partial_tail | GEMM (prepared) + activation |
9.41 | 11.71 | 1.245x | True | 1.00 |

## ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Every row of the delivered plan runs the same route as #5645; the pair,
tail and mixed kernels' generated sources change
only by the descriptor-prefetch instructions and the `evict_first`
cache-hint operand of the B loads, the activation
kernels are unchanged up to the module-hash symbol. Tests: the
existing plan / prepare parity cases, the bit-identity checks against
the chain and the route-rule assertions in

`tests/gemm/test_cake_group_gemm_fp8_nt_groupwise_contiguous_silu_quant.py`
(40 passed on B200).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Updated grouped FP8 fused SiLU quantization execution paths on
supported GPU targets, including revised handling of tensor transfers
and cache hints.
* Expanded and refreshed registered execution routes for regular and
wide SwiGLU quantization, as well as fused and staged processing.
  * Existing operation behavior, inputs, and outputs remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4301247](https://github.com/flashinfer-ai/flashinfer/commit/4301247a6938b8f010ee44569c64b80a2cd967b6)

- **作者**: eigen
- **时间**: 2026-09-29T20:09:03Z
- **提交信息**: perf(cake_vsa_sm90): queue-scheduled persistent stage for long uniform plans (#5687)

## Summary

Second persistent stage `attention_queue` for `backend="cake"` and
`backend="cake_cute"` (`VariableBlockSparseAttentionWrapper`, SM90):
every CTA runs its planned tile list except its last two tiles, which a
global tile queue hands out at run time, so the tail of long uniform
plans balances on measured rather than modelled tile times. The planner
selects it only for uniform plans with at least 12 tiles per CTA
(`plan["queue"]`); every other plan keeps the existing `attention` stage
and plan layout byte for byte, and the `attention` stage's generated
sources are unchanged from #5638.

Which CTA runs a tile does not change the arithmetic: the queue stage's
output is bit-identical to the static stage's on the same plan (new
test, both builds, with CUDA-graph replay and the queue words back to
zero after every launch), and identical to #5638's output on all 127
measured rows and both builds.

## Measurements (H100 SXM, cold L2, same-GPU ABAB b1 f1 b2 f2, 4 AB/BA
pairs, CUPTI)

Baseline A0/C0 = #5638 (`e9ef74ab`), B = `vsa_sm90_blk64` (#5470 @
`9f35c6acfda7`).

| set | rows | CUDA build vs A0 (geomean) | CuTe build vs C0 (geomean) |
rows below 0.99 in every ordering | vs B |
|---|---|---|---|---|---|
| long video rows (m ≥ 32k) | 45 | 1.0045 | 1.0038 | 0 | all > 1 (min
1.021 / 1.038) |
| #5470's 20 rows | 20 | 1.0007 | 1.0003 | 0 | all > 1 (min 1.039) |
| envelope | 39 | 1.0003 | 1.0003 | 0 | all > 1 except
h16-m1024-n8192-k1 CuTe 0.992 (pre-existing) |
| serving envelope | 39 | 1.0001 | 1.0002 | 0 | all > 1 |

Queue rows (all 28 uniform long rows): +0.3 to +1.7 % on m75648 /
m109632 K = 32 / 64, up to +3 % on h10/h12 m32768 K32, both builds. Rows
that keep the static stage are unchanged.

## Gates

- `tests/experimental/test_cake_vsa_sm90.py`: 104 passed on H100
(planner layout tests for both layouts, queue-vs-static bit-exact test
on both builds).
- 78 + 39 rows bit-exact between builds and deterministic; NaN-sentinel
0/19, workspace-poison 0/40 per row.
- compute-sanitizer on the queue stage, both builds: synccheck 0 errors,
memcheck 0 errors; racecheck reports only the mbarrier-ordered plan-slot
hand-off the tool cannot follow (same class as #5638's stage, documented
there).
- `sha256(csrc) == manifest` verified before push;
`csrc/cake_vsa_sm90/.clang-format` kept.

Baseline source PRs: #5470, #5638.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added queue-based scheduling for eligible uniform, persistent SM90 VSA
attention plans. Short or ragged plans continue to use static
scheduling.
  * Added support for the attention queue stage.
* **Tests**
* Added coverage for queue layouts, fallback scheduling, output
consistency, queue-state resets, and graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7bcf918](https://github.com/flashinfer-ai/flashinfer/commit/7bcf91831e4640cf7b8983e8b7954e94a03746b3)

- **作者**: Alex Yang
- **时间**: 2026-09-29T19:18:08Z
- **提交信息**: feat(quantization): expose NVFP4 4over6 recipe through the public API (#5152)

<!-- .github/pull_request_template.md -->

## 📌 Description

Partially addresses #5141 (fused-MoE kernels: see Related Issues).

NVFP4 "4over6" (#3264) was reachable only through four process-wide
environment variables (`FLASHINFER_NVFP4_4OVER6*`). That makes the
recipe implicit and process-global:

- a framework cannot express "this model uses 4over6 / MSE" in its own
config.
- two models in one process cannot use different recipes.
- tests must mutate `os.environ`.

This PR makes the recipe an explicit argument on every NVFP4
quantization entry point and on the unified MoE `QuantConfig`, with the
environment kept as a byte-for-byte compatible, **deprecated** fallback.

```python
from flashinfer import NVFP44Over6Config, make_nvfp4_global_scale, nvfp4_quantize

recipe = NVFP44Over6Config(e4m3_max=256, err_mode="MSE")
gs = make_nvfp4_global_scale(x, per_token_activation=True, nvfp4_4over6_config=recipe)
xq, sf, per_tok = nvfp4_quantize(x, gs, per_token_activation=True, nvfp4_4over6=recipe)

nvfp4_quantize(y, gs2, nvfp4_4over6=None)   # 4over6 off, env ignored
nvfp4_quantize(y, gs2)                      # omitted: legacy env read (+ FutureWarning when it enables 4over6)
```

`NVFP44Over6Config` fields, one per legacy variable:

- `e4m3_max` (448 or 256, `..._E4M3_USE_256`): top of the E4M3
block-scale range the global scale is built for. 256 leaves headroom so
the 1.5x tighter `amax / 4` candidate stays representable.
- `err_mode` (`NVFP44Over6ErrMode.MAE` / `.MSE` or the strings `"MAE"` /
`"MSE"`, `..._ERR_MODE`): metric that picks between the `amax / 6` and
`amax / 4` candidates after quantize-dequantize. MSE penalizes the few
clipped outliers harder, so it picks the tighter candidate less often.
- `err_use_fast_math` (`..._ERR_USE_FAST_MATH`): evaluate that error in
fp16 instead of fp32. Cheaper, and a distinct recipe because near-ties
can flip.

### One public type, three cases

`nvfp4_4over6` is `Optional[NVFP44Over6Config]`, the same two-state type
the kernel drivers have always used internally (`None` = off). "Defer to
the environment" is spelled by the *default value* (a private `_UNSET`
sentinel), not by a third public type:

| `nvfp4_4over6=` | Meaning | Environment |
| --- | --- | --- |
| omitted (default) | legacy behaviour | read per call. `FutureWarning`
when it turns 4over6 on |
| `None` | 4over6 off | ignored |
| `NVFP44Over6Config(...)` | on with exactly this recipe, no per-field
merge | ignored |

When the environment shim is retired, the default flips to `None` and no
signature changes. `make_nvfp4_global_scale` / `nvfp4_e4m3_max` take the
resolved recipe as `nvfp4_4over6_config=` and never read the environment
(their pre-existing contract).

### Data flow

- Python to kernel, in order:
1. `resolve_nvfp4_4over6(setting)` → `Optional[NVFP44Over6Config]`
(`None` = off). The only place that reads the environment.
2. `nvfp4_4over6_code(config)` → one `int64` across the custom-op /
TVM-FFI boundary: `-1` argument omitted (C++ reads the env), `0` off,
bit 0 set = explicit recipe with bits 1..4 = `e4m3_max` / `err_mode` /
`err_use_fast_math`.
3. `resolveNVFP4Recipe(code)` → `NVFP4RecipeSpec`, the only thing the
kernels read. Same recipe as `NVFP44Over6Config`. It carries a
`use4Over6` flag so "off" is an ordinary struct instead of an optional.
Encoder, decoder and bit layout:
`csrc/nv_internal/tensorrt_llm/kernels/nvfp4Recipe.h`.
- Unified MoE: `QuantConfig.nvfp4_4over6` takes the same value. Runners
opt in via `MoERunner.supports_nvfp4_4over6` and reject an explicit
setting otherwise. `CuteDslRunner` honors it on the per-token path.
`CuteDslConfig.prepare_weights(..., nvfp4_4over6=...)` pins the matching
`fc2_input_scale`.

### Bugs fixed along the way

1. Autotuner replayed tactics across recipes:
`MoERunner._cache_key_extras` now keys the **resolved** recipe.
2. `globalScaleInv` / `e4m3Max` desync in `trtllm_fused_moe_runner.cu`:
one `NVFP4RecipeSpec` per launch.
3. Caller/callee recipe mismatch on the per-token global scale is now
validated for explicit recipes.
4. The recipe-blind TMA CuTe-DSL kernel is no longer selected when a
recipe is active.
5. `enable_pdl` landed in the wrong positional slot of `fp4_quantize`
from `_fp4_quantize_custom_op`.
6. The four env vars are now documented in `CLAUDE.md` and enforced by
`scripts/pr_checks/check_cross_sources.py`.

### Out of scope (still read the environment)

- CUTLASS fused MoE and TRT-LLM gen MoE (`trtllm_fp4_block_scale_moe`):
see Related Issues.
- `flashinfer/prims_ts/moe/runner.py` and the `moe_ep` bridge.
- `FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH`: a separate debug knob, not
part of the recipe.
- Trace templates.

Backends that have not opted in raise `NotImplementedError` on an
explicit setting rather than ignoring it.

## 🔍 Related Issues

- Partially addresses #5141.
- Done: `fp4_quantize`, `nvfp4_quantize`, `silu_and_mul_nvfp4_quantize`
(CUDA and CuTe-DSL) and the CuTe-DSL MoE accept `nvfp4_4over6=`.
- Not done: the CUTLASS fused MoE and the TRT-LLM gen fused MoE still
read `FLASHINFER_NVFP4_4OVER6*` in their kernels (`TODO(aleozlx,
#5141)`).
- Follow-up PR: carry an `int64` recipe code in `MoERunnerArgs` (TRT-LLM
gen) and `QuantParams::fp4` (CUTLASS), pass it as a trailing FFI
argument, decode it with `resolveNVFP4Recipe()` at the two env-reading
sites, then set `supports_nvfp4_4over6` on both runners with CuTe-DSL's
per-token guard.
- Original 4over6 implementation: #3264. CuTe-DSL 4over6 and
`NVFP44Over6Config`: #3448.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On B200 (SM100a), JIT built from this branch:

| Suite | Result |
| --- | --- |
| `tests/utils/test_nvfp4_4over6_config.py` (CPU-only) | pass |
| `tests/utils/test_fp4_quantize.py -k 4over6` | pass |
| `tests/moe/test_unified_moe.py -k "cute_dsl or 4over6 or cache_key or
QuantConfig"` + `tests/jit/test_cute_dsl_cache.py` | pass |
| `python -m scripts.pr_checks.check_cross_sources` — Env Vars
Consistency | 0 fail |

Load-bearing tests:

- two recipes in one process with `os.environ` untouched.
- `nvfp4_4over6=NVFP44Over6Config()` with the environment unset is
bit-identical to the legacy `FLASHINFER_NVFP4_4OVER6=1` path on both
backends.
- the precedence matrix (omitted / `None` / config × environment unset /
set).
- `_nvfp4_kernel_name(..., nvfp4_4over6_config=None)` pinned to its
pre-PR string, so no on-disk CuTe-DSL artifact is invalidated.
- empty inputs still resolve and validate the recipe.

## Reviewer Notes

- `csrc/nv_internal/cpp/common/envUtils.{h,cpp}` is deliberately
untouched, since changing it would force a full JIT rebuild for
everyone. The new decoder lives in `nvfp4Recipe.h`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added configurable NVFP4 4-over-6 recipes through `nvfp4_4over6`.
* Added public recipe types, error modes, scale helpers, encoding
utilities, and resolution.
* Added per-call recipe selection, environment compatibility, and an
option to disable 4-over-6.
* Added recipe-aware fused MoE support, backend capability checks,
validation, and cache separation.
* **Documentation**
* Expanded API documentation with recipe options, scale requirements,
precedence rules, and examples.
  * Updated environment-variable references and compatibility warnings.
* **Bug Fixes**
* Improved backend failure messages and validation for incompatible
formats, scales, and recipes.
* Preserved compatibility with existing environment-based
configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: feih <feih@nvidia.com>

### [e3bf83a](https://github.com/flashinfer-ai/flashinfer/commit/e3bf83a9fd53a7acaafdacb212d91f92041846bc)

- **作者**: feih-nv
- **时间**: 2026-09-29T19:11:32Z
- **提交信息**: feat(moe): add opt-in Prims-TS backend to the unified MoE API (#5289)

## 📌 Description

Add an explicit unified-MoE backend for Prims-TS so callers can run
NVFP4 and BF16 MoE through `MoEConfig` / `MoELayer` instead of the flat
`prims_ts_*` APIs.

The existing flat path already does TRT-LLM routing → Prims-TS GEMM →
TRT-LLM finalize. This PR only adds the unified adapter (`PrimsTsConfig`
/ `PrimsTsRunner`, key `"prims_ts"`). It is **opt-in**: not in
`_DEFAULT_BACKEND`, so `backend="auto"` never selects it.

### Scope (MVP)

- SM100 / SM103 only
- Quant pairs: NVFP4×NVFP4 and BF16×BF16
- Activations: NVFP4 supports SwiGLU / GeGLU / SiTU / ReLU2; BF16
supports SwiGLU / ReLU2
- `intermediate_size` must be a multiple of 128

Out of scope: FP8, MXFP4, MXINT4, fused shared experts, LoRA, and making
Prims-TS compete with TRT-LLM in default autotune.

The remaining flat inner runners, for follow-up PRs (each reuses the
matching TRT-LLM weight view the same way NVFP4 / BF16 do here):

| Inner runner | Unified pair | TRT-LLM view |
| --- | --- | --- |
| `PrimsTsMxfp4Mxfp8MoERunner` | MXFP4×MXFP8 | `trtllm_fp4_routed` |
| `PrimsTsMxfp4Bf16MoERunner` | MXFP4×BF16 (W4A16) | `trtllm_fp4_routed`
|
| `PrimsTsFp8PerTensorMoERunner` | FP8PerTensor×FP8PerTensor |
`trtllm_fp8_per_tensor` |
| `PrimsTsFp8BlockScaleMoERunner` | DeepSeekFp8 / MXFP8 |
`trtllm_fp8_block` |

### How it is wired

A Prims-TS forward is still three stages. Only the middle GEMM is new at
the unified layer:

1. TRT-LLM routing (`trtllm_moe_run_routing*`)
2. Prims-TS FC1 / FC2 GEMM (CuTe-DSL batched GEMM, JIT)
3. TRT-LLM finalize (`trtllm_moe_run_finalize`)

Weight and activation layouts are reused from the matching TRT-LLM
prepare helpers, so one physical view can be registered under both keys:

- NVFP4: `TrtllmFp4Config` / `"trtllm_fp4_routed"` (MajorK, shuffled)
- BF16: `TrtllmBf16Config` / `"trtllm_bf16_routed"` (BlockMajorK)

`import flashinfer` does not load CUTLASS task scheduling.
`PrimsTsConfig` / `PrimsTsRunner` are eager exports; the inner
`PrimsTs*MoERunner` is constructed lazily.

The staged C++ launcher (`trtllm_moe_run_routing*`) has no
`routing_input_mode` argument and infers packed vs unpacked vs logits
from tensor rank. The inner Prims-TS runner therefore normalizes the ids
/ weights buffers from the pack's `routing_input_mode`
(`_staged_routing_io`) and selects finalize weights by the same mode, so
the adapter allocates the same 2-D routing buffers as
`TrtllmBf16RoutedRunner` and autotune's synthesized placeholders are
never read as caller weights.

## 🔍 Related Issues

Follows the flat Prims-TS MoE APIs from #4361.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New: `tests/moe/test_unified_moe_prims_ts.py`
- CPU: config/registry, opt-in (not in `_DEFAULT_BACKEND`), arch / `I %
128` / activation gates, staged-routing placeholders
- SM100 GPU: NVFP4 and BF16 vs the unified references, direct
`pack_inputs` + `forward`, CUDA-graph replay vs eager
 
Extended: `tests/test_prims_ts_import_isolation.py` (importing
`PrimsTsConfig` / `PrimsTsRunner` still must not load CUTLASS TS)
- Local SM100: `pytest tests/moe/test_unified_moe_prims_ts.py` → **17
passed**

## Reviewer Notes

- One Config/Runner pair. Inner `flashinfer/prims_ts/moe/runner.py`
(`PrimsTsNvfp4MoERunner` / `PrimsTsBf16MoERunner`) is **not** a unified
runner; `MoELayer` only talks to `PrimsTsRunner`.
- Do not pass TRT-LLM-only kwargs such as `hidden_states_scale_layout`
into Prims-TS `TuningConfig`.
- BF16 prepared weights are BlockMajorK; the unified runner must pass
that layout. The flat BF16 API defaults to MajorK and is a different
contract.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added an opt-in Prims-TS backend for unified Mixture-of-Experts
workloads on supported SM100/SM103 GPUs.
- Supports BF16×BF16 and NVFP4×NVFP4 execution, multiple routing modes,
and compatible activation functions.
- Added public configuration and runner APIs, with weight preparation
compatible with TRT-LLM layouts.

- **Documentation**
- Added API documentation, usage examples, and updated MoE capability
tables.

- **Tests**
- Added coverage for validation, routing behavior, GPU execution, and
CUDA Graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4a270cd](https://github.com/flashinfer-ai/flashinfer/commit/4a270cd77fc5119d62d95c125a98beeaf30cd689)

- **作者**: eigen
- **时间**: 2026-09-29T18:55:38Z
- **提交信息**: ci: add @yyihuang to every CODEOWNERS rule (#5654)

## 📌 Description

Adds `@yyihuang` to every path-specific `CODEOWNERS` rule (53 rules:
attention, gemm, grouped_mm, fused_moe, moe_ep, comm, norm, gdn,
mamba/ssu, kda, autotuner). `@yyihuang` already appears on the global
`*` rule; because the last matching rule wins, that entry did not count
as a code-owner review for any file covered by a more specific rule (for
example #5612 and #5613 stayed `REVIEW_REQUIRED` after an approval).
After this change a review from `@yyihuang` satisfies the code-owner
requirement on every path, consistent with the existing global entry.

Each rule keeps its existing owners and ordering; `@yyihuang` is
appended at the end of the line. Commit 1 covers the KDA rules, commit 2
the remaining ones.

## 🔍 Related Issues

#5612, #5613 (KDA PRs currently blocked on code-owner review).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Not run: the change touches only `.github/CODEOWNERS`; the file was
checked for trailing whitespace and a final newline.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

CODEOWNERS-only change; no code or tests affected (`.github/CODEOWNERS`
is in the CI skip pattern).

## Reviewer Notes

Append-only edit of `@yyihuang` on each rule line; no owner is removed
or reordered.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Expanded maintainer coverage across Attention, GEMM, Grouped GEMM,
MOE, MOE_EP, Communication, Norm, GDN, MAMBA, KDA, and Autotuner areas.
Additional coverage was added for selected Attention files, while
existing ownership patterns were retained.
  * No end-user-facing changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [88a6508](https://github.com/flashinfer-ai/flashinfer/commit/88a650823844baecf78964835cf120e94e036440)

- **作者**: kangbintNV
- **时间**: 2026-09-29T18:52:12Z
- **提交信息**: docs: resolve blocking documentation checks (#5483)

<!-- .github/pull_request_template.md -->

## 📌 Description

Resolve the blocking FlashInfer documentation checks on current `main`:

- document the MiniMax-H3 FP8/NVFP4 pre-attention, FC1 preparation, and
AlphaMoE routed-MoE parameters
- document the CAKE GDN, KDA, and NVFP4 runtime environment variables
- update the add-CUDA-kernel skill's norm-module path after the package
layout change

STALE API/RST warnings are intentionally left unchanged.

## 🔍 Related Issues

Nightly FlashInfer Doc Check failure for `v0.7.0` versus `main`.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review this pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Relevant tests are passing.

Validation performed:

- targeted `pre-commit run --files ...`: passed
- existing checker regression tests: 12 passed
- PR base/head static documentation comparison: 0 new findings
- docstring checker: completeness `0`, argument consistency `0`
- cross-source checker: all five categories `0`

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

The `sampling_softmax` report is a pre-existing checker false positive
present on the PR base. Runtime code, `scripts/`, and checker tests are
unchanged from `main` in this PR. The generic checker fix is tracked
separately in nightly checker MR !16.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Added reference entries for configuration options covering CAKE GDN
slot validation, NVFP4 quantization threads, KDA execution policies, and
KDA plan-cache size.
* Expanded API documentation for diffusion and fused MoE operations,
clarifying input shapes and formats, scaling requirements, alignment,
outputs, and optional workspaces.
* Updated a kernel-development guide with a corrected example file path.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: cindyz <cindyz@nvidia.com>

### [4cbd4b3](https://github.com/flashinfer-ai/flashinfer/commit/4cbd4b3c27c76ae6e43e7d85d4d304e8c7b1ba01)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-29T18:46:36Z
- **提交信息**: fix(aot): ship SM100-family modules in the SM103 JIT-cache provider (#5544)

<!-- .github/pull_request_template.md -->

## 📌 Description

The sm103a jit-cache provider is built for `10.3a` only, so `has_sm100`
is false and every module gated on it alone is skipped. SM103 still
loads those SM100-named modules at runtime, so GB300/B300 users
JIT-compile them on first use.

| `gen_all_modules` | Before | After |
|---|---|---|
| `10.3a` | 422 | 951 (none removed) |
| every other provider arch | — | identical |

| Module | Before | After |
|---|---|---|
| `fmha_gen`, `fmha_cutlass_sm100a`, `mla`, `xqa_*`, `gemm_sm100`,
CUTLASS fp8/mxfp8/svdquant GEMM, `mxfp8_quantization_sm100`,
`fused_moe_trtllm_sm100`, `trtllm_gen_routing`, `trtllm_gemm`,
`trtllm_low_latency_gemm`, `trtllm_mnnvl_comm`, `dcp_alltoall`,
`rmsnorm_silu_*`, `trtllm_utils` | `has_sm100` | `has_sm100 or
has_sm103` |
| `tgv_gemm_*` (sm_100f), `moe_utils` | `has_sm100f` | `has_sm100f or
has_sm103` |
| `tgv_gemm_*` (sm_100a) | `has_sm100` | `has_sm100 and not has_sm103` |
| `fp4_gemm_cutlass_sm103` | never AOT-built | `has_sm103` |
| `trtllm_gemm`, `trtllm_low_latency_gemm` flags | hardcoded `sm_100a` |
targeted SM10x arch |

- Every added module builds `sm_103a`, except the TGV GEMMs, which build
`sm_100f` (runs on SM103).
- SM100 FP4 quantization, CUTLASS fused MoE and CUTLASS FP4 GEMM stay
SM100-only, because SM103 has its own variants.
- `has_sm103` is now a required argument of `gen_attention` and
`gen_xqa`.

## 🔍 Related Issues

- #4514 split the jit-cache into per-arch provider wheels. The sm103a
provider is now built for `10.3a` alone, so `has_sm100` is false and the
SM100-named modules listed above dropped out of it.

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
- [x] All tests are passing (`unittest`, etc.).

`tests/jit/test_aot_sm103_modules.py` covers module registration for
SM103-only, SM100-only and combined builds, plus the arch flags of the
trtllm-gen GEMM runners.

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

- `trtllm_gemm` / `trtllm_low_latency_gemm` now raise `RuntimeError`
when the target arch list has no SM10x entry, the same as the other
SM100 generators.
- Both TGV variants share a module name and the first registered wins,
so a combined `10.0a 10.3a` build used to keep the `sm_100a` one, which
can't run on SM103. This predates the PR; release wheels are
single-arch.
- XQA is kept on SM103 for parity with sm100a, even though
`backend="auto"` doesn't pick it on SM10x.
- Expected sm103a wheel size is ~250–265 MiB, up from ~180–190 MiB; this
is estimated from the sm100a wheel and not yet measured.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded ahead-of-time support for SM103 GPUs across attention,
mixture-of-experts, GEMM, quantization, normalization, and communication
workloads.
* Added SM103 eligibility for XQA and support for shared modules used by
SM100 and SM103 architectures.

* **Bug Fixes**
* TensorRT-LLM GEMM builds now select compiler targets matching the
targeted SM10x architecture.
* When both SM100 and SM103 are targeted, TGV GEMM generation selects
SM100f variants instead of SM100a variants.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [d7c6d0d](https://github.com/flashinfer-ai/flashinfer/commit/d7c6d0df49a27075bffcb71fd5cd79abfdce3769)

- **作者**: Lain
- **时间**: 2026-09-29T17:40:52Z
- **提交信息**: [prims-ts] Mixed precision Fmha decode (#4414)

<!-- .github/pull_request_template.md -->

## 📌 Description

PR dependency: #4413.

  - Add mixed-precision Q/K/V support to PrimTS FMHA decode
  - Add SMEM- and TMEM-based transformed-KV paths
  - Support FP8 and NVFP4 KV caches with BF16 or FP8 queries
  - Update decode APIs, configuration, tracing, benchmarks, and tests

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
* Added support for packed NVFP4 key/value caches with scale factors in
attention decoding.
* Added mixed-precision query and key/value decoding, including FP8 and
BF16 workflows.
* Extended paged-cache and one-shot decode APIs to accept key/value
scale factors.
* Added automatic handling for NVFP4 storage dimensions and transformed
data staging.

* **Bug Fixes**
* Improved dtype, cache shape, device, stride, and alignment validation.
* Corrected FP8 attention-sink scaling and mixed-precision output
handling.

* **Tests**
* Added comprehensive coverage for NVFP4 caches, mixed precision,
validation errors, and eager/CUDA-graph execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>
Signed-off-by: siyuanf <siyuanf@nvidia.com>

### [99c158c](https://github.com/flashinfer-ai/flashinfer/commit/99c158c60469df0396cd9f982a093dfbb9fdcec2)

- **作者**: Mingyang Wang
- **时间**: 2026-09-29T17:13:19Z
- **提交信息**: perf: specialize persistent BatchAttention for equal KV strides (#5329)

<!-- .github/pull_request_template.md -->

## 📌 Description

Persistent BatchAttention computes separate K/V offsets even when their
strides match. Add an equal-stride specialization that shares offset
calculation and prefetch while preserving separate K/V pointers and
independent NVFP4 scale addressing.

The wrapper and default AOT build only the equal-stride primary; unequal
inputs lazily load a separate specialization. Selection checks all three
original data strides on every run. Public/custom generators retain
their signatures, URIs, and runtime compatibility. Reuse the existing
prefill lazy loader and expose the same prewarm API for graph capture.

**Performance:** baseline 35a3e9730f2f94bf2e890e2888d5c82cecd12d9f, CUDA
13.0.88, PyTorch 2.13.0+cu130, release SM100a/SM90a. Across 30 B200
primary cases, geometric-mean speedup is **1.0456x**, with conservative
noise-expanded 95% interval **[1.0207x, 1.0707x]**. This remains
inconclusive against a preselected 3% improvement threshold.

Representative direct-run medians in microseconds, BF16 NHD, equal
strides, page size 16, 32 query / 8 KV heads, head dimension 128,
causal:

| Request groups (count, KV length, query length) | B200 before → after
| H100 before → after |
| --- | --- | --- |
| (1, 8192, 1) | 23.936 → 23.872 | 30.544 → 31.248 |
| (64, 8192, 1) | 330.672 → 322.400 | 726.176 → 725.904 |
| (2, 4099, 129) | 98.720 → 96.320 | 112.896 → 113.312 |
| (64, 8192, 1) + (1, 8192, 1024) | 730.048 → 693.200 | 1069.744 →
1058.528 |
| (100, 1024, 1) + (8, 8192, 17) | 215.792 → 204.704 | 273.856 → 270.096
|

Five alternating baseline/candidate rounds, 100 synchronized CUDA-event
samples per case after warmup; medians above summarize five round
medians. Direct timing includes launch gaps. Separate B200 graph replay:
batched decode 326.528 → 317.744 us; mixed 726.112 → 687.648 us. The
primary matrix crosses these five groups with page sizes 1/16 and head
configurations (32,8,128), (64,8,128), (64,4,64).

Default 36-module shared-library bytes decrease: B200 22,135,104 →
21,764,128 (-1.68%); H100 19,816,768 → 19,535,904 (-1.42%). Median cold
compile/link time across three builds is 280.616 → 282.883 s and 376.210
→ 368.075 s. Using both stride modes still retains both libraries;
representative cold independent compilation costs 6.998 s on B200 /
9.331 s on H100.

<details>
<summary>Timing reproduction recipe</summary>

Run this extracted probe in separate source-installed baseline and PR
environments on the same GPU, with FLASHINFER_CUDA_ARCH_LIST=10.0a
(B200) or 9.0a (H100). Use separate JIT caches, warm them first, and
alternate five baseline/candidate runs. Set groups to each row above and
vary page/hq/hk/dim for the primary matrix. This recipe is not an
additional measurement.

```python
import itertools
import statistics
import torch
from flashinfer.attention import BatchAttention

torch.manual_seed(1715)
groups = [(64, 8192, 1)]
page, hq, hk, dim = 16, 32, 8, 128
lengths = [nk for count, nk, nq in groups for _ in range(count)]
queries = [nq for count, nk, nq in groups for _ in range(count)]
pages = [(n + page - 1) // page for n in lengths]
def pointer(sizes):
    return torch.tensor([0] + list(itertools.accumulate(sizes)), dtype=torch.int32)
q = torch.randn(sum(queries), hq, dim, dtype=torch.bfloat16, device="cuda")
shape = (sum(pages), page, hk, dim)
k = torch.randn(shape, dtype=q.dtype, device="cuda")
v = torch.randn_like(k)
out = torch.empty_like(q)
lse = torch.empty(q.shape[:2], dtype=torch.float32, device="cuda")
indices = torch.arange(sum(pages), dtype=torch.int32, device="cuda")
wrapper = BatchAttention(kv_layout="NHD", device="cuda:0")
for _ in range(6):
    wrapper.plan(pointer(queries), pointer(pages), indices,
                 torch.tensor(lengths, dtype=torch.int32), hq, hk, dim, dim, page,
                 causal=True, q_data_type=q.dtype, kv_data_type=q.dtype)
    torch.cuda.synchronize()
def run():
    wrapper.run(q, (k, v), out=out, lse=lse)
for _ in range(40):
    run()
torch.cuda.synchronize()
starts = [torch.cuda.Event(enable_timing=True) for _ in range(100)]
ends = [torch.cuda.Event(enable_timing=True) for _ in range(100)]
samples = []
for start, end in zip(starts, ends):
    start.record()
    run()
    end.record()
    end.synchronize()
    samples.append(start.elapsed_time(end) * 1000)
print(statistics.median(samples), "us")
```

</details>

## 🔍 Related Issues

Follow-up to #4736, applying its lazy specialization approach to
persistent BatchAttention.

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

Changed-file hooks passed, including clang-format, mypy, and Ruff; the
all-files command above was not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation in source-installed GPU environments:

- Final stride/trace contracts: B200 23 passed; H100 19 passed with four
NVFP4 cases deselected. Generator checks: 8 passed on each.
- Unchanged shared/wrapper lazy-loader tests: 25 passed. Direct
public/custom generators: 4 pytest cases / 12 plan-run evaluations
passed on both GPUs. Prefill regression probes passed.
- Coverage includes NHD/HND, each unequal data-stride axis, FP16/BF16,
all four NVFP4 data/scale stride combinations, wrapper reuse, graph
capture/prewarm/replay with changed inputs, and real no-JIT
provider/missing-artifact behavior.
- AOT qualification preserves exact baseline parity: 96 passes and 48
pre-existing mixed16 failures per variant/GPU. All 72 candidate
libraries load; missing-independent-cache checks pass. Known failures
are not counted as passes.
- Existing evidence is reused where source hashes are unchanged. The
full repository suite and installed-wheel/provider metadata were not
qualified; CI has not been requested.

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

Unequal layouts should call
prewarm_paged_kv_stride_variant("independent") after planning and before
CUDA graph capture. With JIT disabled, the independent variant requires
a recognized provider artifact or an already-loaded holder. Default AOT
intentionally includes only the primary.

H100 shows little runtime benefit. NVFP4 diagnostic point estimates were
1.4–2.6% slower, with no repeatable slowdown above 3% under the same
rule; this PR makes no NVFP4 speedup claim. B200 profiled spill
instructions decreased from 14,360 to 0, while registers/thread and
occupancy were essentially unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Batch attention supports paged K/V caches with equal or independent
memory strides.
* Runtime dispatch selects the appropriate implementation for the cache
layout.
* Independent-stride execution can be prewarmed before CUDA graph
capture.
  * Device-specific module loading supports AOT builds.

* **Bug Fixes**
* Improved correctness across page-, token-, and head-strided cache
layouts.
  * Prewarming runs on the wrapper’s configured device.

* **Tests**
* Expanded coverage for stride handling, lazy loading, CUDA graphs, AOT
builds, tracing, and custom attention modules.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6ed2d99](https://github.com/flashinfer-ai/flashinfer/commit/6ed2d991bcc2e9f67b3bd9596142198604734195)

- **作者**: Harrison Zhang
- **时间**: 2026-09-29T16:53:40Z
- **提交信息**: perf(prims_ts): mask partial last K/V tile outside softmax loop to prevent register spills in dense context fmha (#5280)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

For dense query-paired context FMHA with S % 128 != 0, the softmax
loop ran a masked row-max variant on every iteration. The tail size was
a compile-time constant, so each tail value produced a different cubin and
some tail sizes spilled heavily in the softmax warps. The build at 
S=147600 (with a tail size of S % 128 = 16) spilled 4.7x more than the 
tile-aligned build, evicted K/V from L2 and took 21% more cycles than 
ideal self attention scaling of S^2. The problem is exacerbated at large
S.

With these changes, the softmax loop now runs N_tiles-1 unmasked
iterations and a tail block masks the last tile once. Specifically, the softmax
task now loops over only the floor(S / 128) full K/V tiles with the plain
unmasked row max. Then, a separate block after the loop handles the one partial tile and
mask the zero-filled keys to -inf. The mask code is no longer in the loop
body, so now the loop's register allocation is the same for every S.

**Measured on B200 ncu elapsed cycles (B=2 H=40 D=128 bf16; lower is
better):**
  S=147600: 1283M -> 1037M (-19.2%), spill stores 764 GB -> 55 GB
  S=75600:   289M ->  274M (-5.3%)
  S=111600:  613M ->  593M (-3.3%)
  S=147456 (aligned, path untouched): unchanged
  PV-fp8 S=147600: 740 ms -> 650 ms
Correctness vs SDPA passes at S=4112, 4176, 4096, 1040.

**Test on Wan2.2-T2V-A14B E2E workloads shows improvement on both 
QKV-BF16 and QK-BF16/PV-FP8 modes:**
Across three prompts P1, P2, P3 over different number of output tokens, 
which is controlled by number of frames and resolution. 
| prompt | S | S mod 128 |
|---|---|---|
| P1 | 75600 | 80 |
| P2 | 111600 | 112 |
| P3 | 147600 | 16 |

<img width="2240" height="992" alt="image"
src="https://github.com/user-attachments/assets/961d6886-853e-46e4-898c-61af5944ef03"
/>

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

Added new test `test_attention_ts_context_fixed_dense_k_tail_accuracy`
which tests unpacked BSHD dense attention at K lengths 272, 336, 1040,
4112, 4176 as well as the aligned control 4096. For both PV-BF16 and
PV-FP8.

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

1. Work toward achieving parity with trtllm-gen.
2. E2E performance improvement for PrimsTS QK-BF16/PV-FP8 over the
QKV-BF16 variant on Wan2.2 T2V will be addressed in another PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved accuracy for dense attention when K/V sequences end with a
partial tile, while preserving full-sequence processing for single-QKV
staged launches.
- Corrected softmax handling of partial K/V tiles so tail values are
masked and processed in the appropriate stage. Variable-window attention
no longer uses the fixed dense K-tail mask.

- **Tests**
- Added accuracy coverage for partial and tile-aligned K/V sequence
lengths, including BF16 and FP8 value formats.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Harrison Zhang <harrisonz@nvidia.com>

### [10c80d7](https://github.com/flashinfer-ai/flashinfer/commit/10c80d75ba63a5b574e619d5167683e2a1d1a625)

- **作者**: eigen
- **时间**: 2026-09-29T11:03:37Z
- **提交信息**: perf(cake_sparse_mla): round-5 DSv4 sparse-MLA Cake programs for SM100/SM103 (exact numerics; stacked on #5644) (#5686)

## Summary

Round-5 performance of the `backend="cake"` DeepSeek-V4 sparse-MLA
decode path of `trtllm_batch_decode_sparse_mla_dsv4`
(SM100a / SM103a), regenerated from the same producer pipeline as #5644,
plus one host-side binding line. Every regenerated program computes
bit-identical output to its #5644 predecessor: this round only re-times
data movement and epilogues, with no change to the arithmetic.

- **BF16 H8/H16 decode programs (16 rows):** eight warps issue the K
gathers (both arches); the FP8 H8/H16 programs do the same on SM100a.
- **BF16/H128 persistent prefill programs (SM103a):** the O epilogue
loads the next tile's TMEM accumulator ahead of the store (−1.5..−4.3
%).
- **BF16/H64 split-K decode programs (9 rows):** owner-CTA form with
hoisted partial select, zero-fill and 256-bit stores: −1.7..−2.9 us per
  row (GB300 class geomean 1.25x -> **1.51x**, B200 1.18x -> **1.45x**).
- **FP8/H128 persistent prefill programs:** TMA-store O epilogue
(−0.5..−0.6 us on the 9-tile rows, −7.3 % on prefill-style-000093).
- **BF16/H32 retained-KV decode programs (4 rows):** the softmax
publishes P before the row-sum exchange (separate stats barrier),
−0.3..−1.2 %.
- Every other program is a byte-identical regeneration (renamed for the
new producer revision).
- **Host (`flashinfer/mla/cake_dsv4.py`, first commit of this branch):**
the FP8 persistent bodies now store O through a TMA descriptor
(`tmap_o`); `_TMA_SOURCE_ALIASES` binds it to the same `[tokens, heads,
512]` output rows the plain `O` argument sees. Without it every
FP8 launch on those routes raised "argument 'tmap_o' (tma_buffer) has no
host value" (28 failures in the hardening tests on the
regenerated programs alone). `test_registered_arg_plans_use_known_names`
now also requires every TMA descriptor to alias a tensor the
host actually places in its value table, so a vocabulary-only match
cannot pass again.

## Validation

Exports of the regenerated programs as published here (B200: export r15
against #5644's `6d479bea1`; GB300: export r16 against this branch's
host-fix commit `fd2131236`), same-session paired CUPTI (active-union
median, cold L2) against the default trtllm-gen path at the same
revision:

| | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---|
| 94 canonical + 40 hardening shapes correct (BF16 atol=rtol=1e-2, FP8
0.1; padded / separate-table / offset axes) | 134/134 correct; 133/134
export gates (row 085: baseline-arm order sensitivity, see doc §
Round-over-round) | 134/134 |
| **94 canonical rows faster than the default path** | 94/94 > 1,
geomean **1.370x**, min 1.129x (#5644: 1.343x, min 1.130x) | 94/94,
geomean **1.356x**, min 1.103x (#5644: 1.319x, min 1.048x) |
| 40 hardening rows faster than the default path | 40/40 > 1, geomean
**1.385x**, min 1.096x (#5644: 1.353x, min 1.085x) | 40/40 > 1, geomean
**1.333x**, min 1.045x (#5644: 1.310x, min 1.069x) |
| output bit-identical to the #5644 programs on every changed row | yes
| yes |
| compute-sanitizer synccheck + memcheck on the changed kernels | 0
errors | 0 errors |
| `tests/mla/test_cake_dsv4*.py` (GPU, fresh clone of this commit) | 296
passed, 0 failed | 296 passed, 0 failed |

## Baselines and their source PRs

- **trtllm-gen default path** =
`trtllm_batch_decode_sparse_mla_dsv4(...)` without `backend="cake"` (the
TRTLLM-GEN DSv4 sparse-MLA
kernels plus the framework launches it needs for equal semantics:
padded-Q masking, separate-table merge, workspace/counter handling).
Origin PRs: #3269 (9c76c994b, 2026-05-21); SM120 kernels #3395
(f95469478, 2026-06-15); DSv4.1 unification #5197 (eb5f05be1,
2026-09-18).
- **Cake backend under test** = `backend="cake"` from #4573 (13db2cfd5,
2026-09-16), hardened by #5591 (8589d49b0), round 2 #5610
(4b8167eab), round 3 #5630 (ebe0efbb1), round 4 #5644 (6d479bea1),
regenerated again by this PR.
- **Test oracle** = the PyTorch reference of
`tests/mla/test_cake_dsv4.py` / `test_cake_dsv4_hardening.py`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added output tensor-map support for selected CAKE DSV4 attention
paths, enabling outputs to be staged and transferred through optimized
tensor operations.
* Updated selected kernels to process larger output groups and adjust
work distribution for supported GPU architectures.
* Refreshed kernel-family registration and dispatch across supported
architectures.
* **Bug Fixes**
* Improved handling of invalid key/value indices and synchronization of
output statistics and transfers.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4321873](https://github.com/flashinfer-ai/flashinfer/commit/43218730b7c957966ecca091cd800ba373171dc1)

- **作者**: eigen
- **时间**: 2026-09-29T09:55:14Z
- **提交信息**: perf(cake_xqa): per-GQA-ratio tmem kernels and the cta_group::2 pair routes for experimental SM110 XQA (#5674)

## Summary

Round 9 of the SM110 XQA D512 tree kernels: per-GQA-ratio traces for the
`tmem` routes (lifting the ratio-8 freeze of #5658) and a new `pair`
kernel family, the same tcgen05/TMEM schedule run as two `cta_group::2`
CTA pairs in a `(4, 1, 1)` cluster per two 128-row Q tiles of a KV head.
The pair form is exported for the two E4M3 cache modes (contiguous and
page128) at GQA ratios 2/4/8/16 and `kernel="auto"` now selects it
whenever every KV head has an even number of Q tiles, because under the
strict cold-L2 protocol it beats the previous kernel of record (`tmem`,
#5658) on both E4M3 modes on every validated Thor node (per process
1.034-1.071, pooled 1.037-1.049; warm 1.16-1.18). FP16 KV and odd Q-tile
counts keep the `tmem` route, now at every GQA ratio.

-
`csrc/sm110_xqa/sm_110a/sm110_xqa_tree_<mode>_tmem_r{2,4,16}_{kernel,q_kernel}.cu`
(24 files): the tmem kernel traced per GQA ratio (the 128-row Q tile is
`ratio` heads x `128 / ratio` tokens, so the Q box and the row mapping
are compiled in), both cluster forms. The ratio-8 files of #5658 are
byte-identical. The four `*_tmem_binding.cu` select the kernel from
`(ratio, Q-tile parity)`, encode Q with the ratio's box and reject other
ratios.
-
`csrc/sm110_xqa/sm_110a/sm110_xqa_tree_fp8_<layout>_pair_r{2,4,8,16}_kernel.cu`
+ `*_pair_binding.cu` (10 files): the pair schedule. The pair leader
issues one M256 MMA stream for both Q tiles (QK M256 N64 K128 SS, PV
M256 N128 K16 TS from each CTA's tensor memory); each CTA holds one
token half of every K chunk and one column half of every V chunk (K/V
inflow, FP8 widen and MMA operand traffic per SM halve); raw E4M3 V rows
are multicast to the pair through a third tensor map (`KVV`); a
twelve-stage 8 KiB ring keeps two tiles in flight with the loader
bounded to six issued-but-not-landed stages. Grid `(4, heads *
ceil(q_len * ratio / 128) / 2, batch)`, 230400 B dynamic shared memory,
cluster dimensions compiled in; the binding requires an even Q-tile
count.
- `manifest.json`: the tmem routes carry `gqa_ratios`,
`kernel_symbols[ratio].{even,odd}` and `source_cubin_sha256s` (replacing
`gqa_ratio` / `kernel_symbol` / `fallback_kernel_symbol`); two
`tree_fp8_*_pair` routes (`kernel="pair"`, `cluster=[4,1,1]`,
`cta_group=2`, `q_tiles_per_cluster=2`, `kernel_symbols[ratio]`);
eighteen ledger rows, refreshed ledger digest.
- `jit.py`: fifth tree kernel family (`_pair` route suffix),
`TREE_GQA_RATIOS`, per-ratio symbol contract for both families.
- `backend.py`: `kernel="pair"` (E4M3 KV, even Q-tile counts;
`ValueError` otherwise), `kernel="tmem"` at every ratio, `kernel="auto"`
= `pair` for E4M3 KV with an even Q-tile count per head else `tmem`; the
pair grid from `q_tiles_per_cluster`.
- `benchmarks/sm110_xqa_shapes.json`: ledger rows
`tree_fp8_{contiguous,paged}_pair`.
- Tests: tmem cache cases at ratios 2/4/8/16 with even and odd Q-tile
counts (both cluster forms), pair cases on both E4M3 modes at every
ratio (uniform and packed Q), `auto` routing to pair / tmem, pair
rejections (FP16 KV, odd Q-tile counts), JIT fixture and geometry checks
for the per-ratio schema. README, RESULTS.md and validation.json record
the routes and the Thor validation.

The `tcgen05`, `register_mma` and `register_mma_split` routes and the
ratio-8 tmem kernel sources are untouched.

## Speedup vs baselines (shipped `auto` route for E4M3 KV = `pair`,
strict cold-L2 CUPTI medians)

Strict cold = a 64 MiB L2 flush before every launch; A = the previous
kernel of record (`tmem`, #5658); B = the upstream TensorRT Edge XQA
source. Each cell is the median over three independent processes per
node (four alternating pairs each, candidate and A each paired against B
in one process); ledger shape (batch 1, 20 query tokens, 32 query heads,
4 KV heads, D512, capacity 256, causal tree mask).

| mode | vs A node 1 (sr250v3-0666) | vs A node 2 (sr250v3-0669) |
per-process range | vs B (minimum over nodes) |
|---|---|---|---|---|
| FP8 page128 | 1.049 | 1.037 | 1.034-1.071 | 1.33 |
| FP8 contiguous | 1.048 | 1.041 | 1.039-1.049 | 1.36 |
| FP16 page128 | `tmem` (unchanged, 1.0005 / 1.0011 same-cubin noise) |
| | 1.64 |
| FP16 contiguous | `tmem` (unchanged, 1.0005 / 0.999) | | | 1.39 |

Warm-L2 (attribution only): FP8 page128 1.175 / 1.183, FP8 contiguous
1.176 / 1.163. The FP16 pair form measured slower cold (its K boxes are
2-4 KiB by the cta_group::2 operand geometry and the strict-cold DRAM
stream rate drops with box size), so FP16 keeps the tmem route.

## Kernel-side gates (two Thor nodes, CUDA 13.4, sm_110a)

- Seven qualification rows at the package tolerances (FP16
`atol=rtol=1e-2`, FP8 `atol=rtol=0.1`), max abs error 1.2e-4 (= the tmem
route's); the e2e slice (156 tests) passes on the shipped tree.
- Bit-deterministic: two direct launches, two CUDA-graph replays and a
side-stream eager launch produce identical bytes on every cache form and
input set.
- compute-sanitizer synccheck: 0 errors on all four cache modes on both
nodes; racecheck reaches the 20 s deadline in the schedule harness
(skipped by protocol; the exported routes below complete it).
- Static census: 128 registers, no local memory, 5.96-6.01k SASS
instructions (pair) vs 5.79-5.87k (tmem).

## FlashInfer-side validation (Thor, one container session; recorded in
`RESULTS.md` / `validation.json`)

Validation on NVIDIA Thor `sr250v3-0667` (20 SMs, CUDA 13.4, PyTorch
2.15.0a0+875d815502.nvinternal.main):

- Artifact parity (frozen schedule launcher vs the TVM-FFI export,
identical tensors, six alternating pairs, 256 CUPTI cold-L2 samples per
round, gate 3%): all six rows pass (export/schedule medians
0.9910-1.0063; largest deviation 0.899% on tree_fp8_paged_tmem, pair
rows 0.634% and 0.107%); full table in
`flashinfer/experimental/sm110_xqa/RESULTS.md` § Round 9 and
`validation.json` `round9`
- Public ledger benchmark (`benchmarks/bench_sm110_xqa.py`, 18 rows in
one process): tmem 30.208 / 30.944 / 23.840 / 23.904 us (fp16_c / fp16_p
/ fp8_c / fp8_p), pair 22.305 / 22.912 us (1.069x / 1.043x faster than
the tmem rows that `auto` previously selected), tcgen05 reference rows
58.9-61.5 us; every row correct.
- compute-sanitizer on the exported routes, 20 s limit: synccheck 0
errors and racecheck 0 hazards (0 errors, 0 warnings) on all six
tmem/pair routes, 7-9 s each.
- Tests in the container: JIT suite 44 passed; GPU suite 306 passed, 35
skipped (FP16 and odd-tile pair cases skip by design); pre-commit clean.

## Baselines and their source PRs

- `tmem` routes (A): PR #5658 (merged 98221238, 2026-09-29), ratio-8
kernel sources unchanged here.
- `register_mma` routes: PR #5293 (merged d7e03f5e, 2026-09-27);
`register_mma_split` route + `register_mma_auto`: PR #5597 (merged
2469eeb4, 2026-09-28); `tcgen05` routes: PR #5293. All untouched.
- Upstream TensorRT Edge XQA source (B): pinned revision e8b29522 of the
TensorRT Edge-LLM XQA kernel, built and timed in the same process by the
Cake benchmark harness; not part of this repository.
- Branch merge-base: upstream `main` at 90a709ca; no upstream commit
after the merge-base touches `flashinfer/experimental/sm110_xqa`,
`tests/experimental/sm110_xqa` or `benchmarks/sm110_xqa_shapes.json`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* SM110 tree attention now supports GQA ratios 2, 4, 8, and 16 across
TMEM routes.
* Added paired-kernel routing for FP8 KV cache layouts. Automatic
selection uses the paired route when the query-tile count is even, and
TMEM otherwise.
* The paired route requires FP8 KV and an even query-tile count;
unsupported inputs are rejected.
* Added benchmark coverage for contiguous and paged paired-kernel cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4a63813](https://github.com/flashinfer-ai/flashinfer/commit/4a6381331a58ca4e900b0455cd55088fb6ed2ecb)

- **作者**: Adrian
- **时间**: 2026-09-29T09:18:37Z
- **提交信息**: test: prune XQA batch-decode parameter matrix (#5421)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_xqa_batch_decode.py` to `parametrize_product`.
Regular pytest runs use deterministic pairwise coverage, while `pytest
--full` retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Updated batch-decode test combinations to cover causal and full-mask
modes across supported input shapes, while excluding single-token
full-mask cases.
* Switched to pairwise combinations to reduce redundant test cases.
These changes affect test coverage only; application behavior is
unchanged.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f80941d](https://github.com/flashinfer-ai/flashinfer/commit/f80941d6e44b872163b9a934cbe0147b6a923340)

- **作者**: Adrian
- **时间**: 2026-09-29T09:15:58Z
- **提交信息**: test: prune TensorRT-LLM XQA parameter matrix (#5419)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_trtllm_gen_attention_decode_xqa.py` to
`parametrize_product`. Regular pytest runs use deterministic pairwise
coverage, while `pytest --full` retains the exhaustive matrices for
nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated XQA decode test coverage to use pairwise combinations from the
supported-configuration matrix. Coverage no longer includes FP8 query
cases, NVFP4 combinations, non-contiguous queries, or configurations
without shared paged KV indices. The test documentation now describes
the supported matrix and how decode and prefill test shards run in
parallel.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4522
- **最后更新**: 2026-09-30T00:58:47Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: Junda Su, Aryan Kumar, lpc0220

## AI分析总结

根据FastVideo仓库昨日的提交记录及README背景，总结如下：

### 1. 主要更新类型
本次提交涵盖**性能优化、代码重构、Bug修复和文档更新**，体现了项目在功能、工程质量和用户体验上的多维度并进。

### 2. 关键变更点及其与项目方向的关系
*   **核心工程重构**：提交#1896、#1897和#1895共同推进了**环境变量管理的系统化**。这包括引入带类型的注册中心、集中读取逻辑并修复相关Bug。这直接服务于项目**提升代码健壮性、可维护性和开发者体验**的方向，为大型项目的规范协作奠定基础。
*   **硬件性能深化**：提交#1866为`sm_100a`（NVIDIA Blackwell架构）添加了VSA块稀疏注意力的CUDA反向传播内核。这紧扣项目名称“FastVideo”所强调的**追求极致推理/训练速度**的核心目标，并积极拥抱最新硬件以保持技术领先性。
*   **生态与易用性**：提交#1884更新了FastH3 V2的Cookbook和MLX安装指南，旨在**降低用户使用门槛，促进模型在多平台（如Apple MLX）的部署与应用**，扩展项目影响力。

### 3. 对项目的影响和潜在意义
*   **工程稳定性提升**：统一的环境变量管理能减少配置错误和硬编码，使得项目配置更清晰、测试更可靠，为持续集成和新功能开发扫清障碍。
*   **性能天花板拓展**：针对最新GPU架构的优化内核，意味着FastVideo能更充分地利用硬件算力，为用户提供更快的视频生成速度，巩固其“Fast”的定位。
*   **社区贡献友好**：文档的完善（如MLX安装指南）和代码结构的规范化，使得外部开发者更容易理解、使用和贡献代码，有利于社区生态成长。

### 4. 值得关注的技术点
*   **环境变量注册中心**：这是一个重要的设计模式（如#1896），它将分散的变量读取变为集中、类型安全且可测试的管理单元，是大型Python项目配置管理的良好实践。
*   **CUDA Kernel针对特定架构的优化**：提交#1866中的`sm_100a`支持和128-token块大小，显示了对**稀疏注意力机制**和**新硬件特性**的深度定制，这是实现高性能AI内核的关键。
*   **FastH3 V2的MLX部署**：#1884反映了项目对**跨平台推理**（特别是苹果生态）的支持，这在端侧AI和低功耗设备部署场景下具有重要意义。

### 5. 对项目发展的影响
这些提交共同推动FastVideo项目朝着**更专业、更快速、更易用**的方向发展：
1.  **性能与硬件**：持续优化最前沿硬件上的核心算子，确保项目在性能竞争中的优势。
2.  **工程架构**：通过重构基础配置模块，为构建更复杂、可靠的功能打下坚实基础，是项目从“能用”到“好用、可靠”的关键演进。
3.  **用户与社区**：更新文档和提供多平台支持，旨在扩大用户基础，构建更活跃的开发者和用户社区。整体上，这些提交在追求技术卓越的同时，也兼顾了项目的可持续发展。

## 详细提交记录

### [e1f3904](https://github.com/hao-ai-lab/FastVideo/commit/e1f390479919e156b30b8611d856ea340c0577dd)

- **作者**: lpc0220
- **时间**: 2026-09-29T23:57:22Z
- **提交信息**: [kernel] sm_100a CUDA backward for VSA block-sparse attention, 128-token blocks (#1866)

Co-authored-by: Pengcheng Li <pengchengl@ptyche0203.ptyche.clusters.nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [02f1ce1](https://github.com/hao-ai-lab/FastVideo/commit/02f1ce11aee39fbbfefebc191f1476b843ffd6aa)

- **作者**: Junda Su
- **时间**: 2026-09-29T21:36:16Z
- **提交信息**: [misc] Move environment var reads into env registry and rename unprefixed variables (#1897)

### [7f03e03](https://github.com/hao-ai-lab/FastVideo/commit/7f03e03dc6561f12815794294384b730bda4dbbb)

- **作者**: Aryan Kumar
- **时间**: 2026-09-29T20:03:18Z
- **提交信息**: [docs]: FastH3 V2 cookbook serving and MLX install guide (#1884)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [e3b88bb](https://github.com/hao-ai-lab/FastVideo/commit/e3b88bb12a4f696dbbeade16db16042af7327d9b)

- **作者**: Junda Su
- **时间**: 2026-09-29T19:50:45Z
- **提交信息**: [feat] Add a typed environment-variable registry, policy doc, and contract test (#1896)

### [cb66acd](https://github.com/hao-ai-lab/FastVideo/commit/cb66acd40065731f8fa1a6d750dc04679ba97756)

- **作者**: Junda Su
- **时间**: 2026-09-29T18:48:31Z
- **提交信息**: [bugfix] Fix environment-variable bugs in LTX-2 debug logging, HF token lookup, and attention backend reads (#1895)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34633
- **最后更新**: 2026-09-29T18:25:03Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

### 1. 主要更新类型
*   **性能优化**：提交 `[fef717f]` 针对 `sage attention` 进行了更新，旨在优化注意力机制的效率。
*   **基础设施与安全加固**：提交 `[4ac08e9]` 主要涉及为 `diffusers-cli` 添加 Dockerfile，并对 CI/CD 工作流进行了安全强化，属于项目基础设施的改进。

### 2. 关键变更点及其与项目整体方向的关系
*   **性能优化 (`sage attention`)**：此次更新可能涉及底层计算优化或对特定硬件（如提到的“Blackwell”架构）的支持。这与 `diffusers` 项目致力于提供高效、灵活且可扩展的扩散模型库这一核心方向一致，旨在持续降低推理和训练成本。
*   **工具链与安全增强**：为 `diffusers-cli` 提供 Dockerfile，方便了在 HuggingFace 生态内（如 HF Jobs）的部署和使用。同时，加固 GitHub Actions 工作流并修复安全标记问题，体现了项目对稳定性和安全性的重视，是支撑长期、可靠发展的关键基础。

### 3. 对项目的影响和潜在意义
*   **直接影响**：用户可能在使用某些模型或在新硬件上获得更快的推理速度。开发者和运维人员能更安全、便捷地构建和运行 `diffusers-cli` 相关任务。
*   **潜在意义**：性能优化有助于降低大规模应用的计算门槛；基础设施的完善则提升了项目的可维护性和社区贡献的流畅度，为接纳更多功能和用户打下了坚实基础。

### 4. 值得关注的技术点
*   **`sage attention` 的具体实现**：需要关注其更新的具体内容（如算法改进、算子融合等）以及对不同模型架构的兼容性。
*   **CI/CD 安全加固措施**：提交中提到了“harden workflow files”，值得了解具体采用了哪些实践（如权限最小化、依赖审计等）来提升安全性。

### 5. 对项目发展的影响
这些提交从**核心计算效率**和**工程基础设施**两个维度推动了项目。`sage attention` 的优化直接提升了库的性能竞争力，符合扩散模型领域对速度的不懈追求。而 `diffusers-cli` 工具链的完善与 CI 的加固，则使项目更易于维护、部署和贡献，增强了生态的健壮性。两者结合，既深化了技术优势，又夯实了可持续发展的根基，共同服务于将 `diffusers` 打造为高效、可靠、易用的扩散模型工具库这一目标。

## 详细提交记录

### [fef717f](https://github.com/huggingface/diffusers/commit/fef717ffb01f407d2637584ed936c16db908587a)

- **作者**: Sayak Paul
- **时间**: 2026-09-29T13:17:23Z
- **提交信息**: [core] propagate sage attention updates. (#14584)

* propagate sage attention updates.

* add sage blackwell.

* up

* style.

* address feedback

* style.

### [4ac08e9](https://github.com/huggingface/diffusers/commit/4ac08e940880fa906c36b944a42f420db4e24b26)

- **作者**: Sayak Paul
- **时间**: 2026-09-29T11:20:36Z
- **提交信息**: [diffusers-cli] add a dockerfile for diffusers cli hf jobs (#14550)

* add a dockerfile for diffusers cli hf jobs

* up

* up

* use diffusers from pypi

* fix(ci): harden GitHub Actions workflows (#14550) (#14851)

fix(ci): harden workflow files flagged on #14550

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* Apply batched suggestions from code review

Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* lower bound for tokenizers.

---------

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>
Co-authored-by: Dhruv Nair <dhruv.nair@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 433
- **最后更新**: 2026-09-26T17:57:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13196
- **最后更新**: 2026-09-29T14:08:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36607
- **最后更新**: 2026-09-30T01:17:05Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 25
- **主要提交者**: Jiacong Fang, Colin Z, Mohammad Miadh Angkad

## AI分析总结

根据提供的提交记录和项目背景，对昨日sgl-project/sglang的提交分析如下：

**1. 主要更新类型**
*   **Bug修复**：占据了较大比重，涉及核心推理组件（MoE、KV缓存）、指标计算、模型加载（LocateAnything）及多硬件后端（AMD， MUSA）的稳定性问题。
*   **性能优化与特性新增**：包含特定GPU（SM90）的内核调优、新硬件（GB300）支持、路由器架构演进及推理前缀缓存等新功能。
*   **基础设施与维护**：CI权限配置、依赖项清理、文档更新等项目维护工作。

**2. 关键变更点及其与项目整体方向的关系**
*   **鲁棒性增强**：大量对MoE（混合专家模型）、分布式推理和GPU特定代码的修复，直接强化了项目核心——**高性能LLM服务与推理引擎**的稳定性和可靠性。
*   **架构演进**：一系列关于路由器（Router）的提交（4/13至7/13）引入了快照（Snapshot）和引导（Bootstrap）机制，这是实现**弹性、可扩展的分布式路由与负载均衡**架构的关键步骤，符合其服务大规模模型的目标。
*   **硬件生态扩展**：对AMD、MUSA（摩尔线程）等平台的持续适配与修复，以及对NVIDIA GB300等新硬件的支持，体现了项目**广泛部署于异构计算环境**的雄心。
*   **可观测性完善**：修复和新增多个指标（Metrics），如TPOT直方图和TTFT计算，有助于更精细地监控和优化推理性能。

**3. 对项目的影响和潜在意义**
*   **短期影响**：提升了框架在特定模型（MoE）、硬件平台和分布式场景下的运行稳定性和性能，修复了影响用户体验的Bug。
*   **长期意义**：路由器架构的演进为未来支持更大规模、更复杂的动态负载均衡和故障恢复奠定了基础。多硬件平台的持续投入将扩大其用户和应用范围。对开发效率（如CI、测试策略）的优化有利于项目长期维护。

**4. 值得关注的技术点**
*   **内存管理**：将SWA KV池分配在特定内存区域（commit #4），体现了对GPU显存精细管理的追求。
*   **分布式协调**：路由器系列提交展示了如何通过元数据（Bootstrap）、快照校验和EndpointSlices监控来构建一个协调的路由层。
*   **测试策略**：将RDMA可用性检查从错误降级为警告（commit #8），反映了在复杂硬件环境中平衡测试严格性与实用性的策略。
*   **AI辅助开发**：多个提交由Claude等AI模型协作完成，表明了先进AI工具在辅助复杂代码库开发和维护中的应用。

**5. 基于项目背景的提交影响**
README强调sglang是一个**高性能LLM服务和推理引擎**。本次提交完全围绕这一核心目标展开：通过修复底层Bug保障服务可靠性；通过性能优化和新硬件支持追求更高吞吐量与更低延迟；通过重构路由架构和指标增强其作为生产级服务的可管理性与可扩展性。这些工作共同推动项目向更稳定、高效、易用的方向发展。

## 详细提交记录

### [ba3e04c](https://github.com/sgl-project/sglang/commit/ba3e04c063fad25675a9ddf40dc0ce51a2e3c5cf)

- **作者**: Jason Mancuso
- **时间**: 2026-09-29T23:42:01Z
- **提交信息**: [CI] Grant CI permissions to four contributors (#41775)

### [8d2d874](https://github.com/sgl-project/sglang/commit/8d2d87475832c31f4d92df9e5c5616f36393cbd3)

- **作者**: Cheng Wan
- **时间**: 2026-09-29T23:38:05Z
- **提交信息**: [Fix] Release consumed residual contributions (#41749)

### [3d49538](https://github.com/sgl-project/sglang/commit/3d4953839c39d0b5413bed701405632fc6a903f8)

- **作者**: Jiajun Li
- **时间**: 2026-09-29T23:29:27Z
- **提交信息**: [Fix] MoE: require TopK layer_id to ensure routed expert captures (#40980)

Co-authored-by: Shi Dong <hello@dongshi.me>

### [f0e4001](https://github.com/sgl-project/sglang/commit/f0e4001930f86cf4b418411ba7dd20e917ce6f90)

- **作者**: Jiajun Li
- **时间**: 2026-09-29T23:29:02Z
- **提交信息**: [Fix] Allocate SWA KV pools inside the memory-saver region (#40979)

### [d3f8a8f](https://github.com/sgl-project/sglang/commit/d3f8a8f4f57f0b058aa0e4eb0cff6b7da7c0b1ce)

- **作者**: Yuwei An
- **时间**: 2026-09-29T23:08:01Z
- **提交信息**: [Spec/Prefill Coordination] Dspark support (#41623)

### [211b1d9](https://github.com/sgl-project/sglang/commit/211b1d9784d15845566081cc25c8103ce43cc4f2)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-29T22:11:18Z
- **提交信息**: [Refactor] Share PD routing fields across request models (#41756)

### [37a4773](https://github.com/sgl-project/sglang/commit/37a47737c805782028e2c7cdbcc99f8770c0774c)

- **作者**: anthonyhe-bot
- **时间**: 2026-09-29T22:03:33Z
- **提交信息**: [Perf] Tune SM90 GDN recurrent verify launch for small batches (#41486)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [4885b56](https://github.com/sgl-project/sglang/commit/4885b563c33e10cc8655538f73db88451ca3cbb3)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-29T21:52:31Z
- **提交信息**: [Test] Demote PD test RDMA openability check to a warning (#41681)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [84523d6](https://github.com/sgl-project/sglang/commit/84523d67851171fa20f7c68d3d6dc6cbf20c4423)

- **作者**: James Liu
- **时间**: 2026-09-29T21:24:51Z
- **提交信息**: [Spec] Reuse K3 auxiliary outputs across decode CUDA graph sizes (#40159)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [46beacf](https://github.com/sgl-project/sglang/commit/46beacf13dbcd9d3aea456301f2d39ea3888540e)

- **作者**: jain-ria
- **时间**: 2026-09-29T20:40:04Z
- **提交信息**: [grpc rust] Define semantic frontend contract (#41709)

Signed-off-by: jain-ria <riajain@NVIDIA.com>

### [77a8199](https://github.com/sgl-project/sglang/commit/77a81996ce8295d9a3f683282693168ee4c229ed)

- **作者**: James Liu
- **时间**: 2026-09-29T20:32:54Z
- **提交信息**: [PD] Preserve bootstrap metadata in native Messages requests (#39711)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3c4653b](https://github.com/sgl-project/sglang/commit/3c4653b6a30cba798448f7fc34ad9a92a7f8e68b)

- **作者**: James Liu
- **时间**: 2026-09-29T20:12:09Z
- **提交信息**: [Metrics] Fix PD latency histogram accounting (#39706)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [f884231](https://github.com/sgl-project/sglang/commit/f884231f5a3108d9139b0141406ddea60f6a97ff)

- **作者**: zijiexia
- **时间**: 2026-09-29T19:47:21Z
- **提交信息**: [Docs] Add IQuestLab card logo to cookbook landing page (#41746)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [51ace48](https://github.com/sgl-project/sglang/commit/51ace48387ad8b86e6c81988de4bbbe6a014a544)

- **作者**: James Liu
- **时间**: 2026-09-29T19:20:22Z
- **提交信息**: [Metrics] Add request-level TPOT histogram (sglang:request_time_per_output_token_seconds) (#40275)

Co-authored-by: Gilford Ting <gilford@modal.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9a16e47](https://github.com/sgl-project/sglang/commit/9a16e4743769e391091760e31c8d9e56d98a4fc8)

- **作者**: ishandhanani
- **时间**: 2026-09-29T18:56:51Z
- **提交信息**: chore: grant jain-ria CI permissions (#41728)

### [bf80732](https://github.com/sgl-project/sglang/commit/bf80732b926eabadbd6f54f702ffa74916a9121b)

- **作者**: ashwini rathi
- **时间**: 2026-09-29T18:35:11Z
- **提交信息**: Fix pip install: exclude multimodal_gen/.claude symlink from package data (#41703)

### [8f2a963](https://github.com/sgl-project/sglang/commit/8f2a9638f7a5a2b3ac903aca45508b12206b0fda)

- **作者**: James Liu
- **时间**: 2026-09-29T18:24:52Z
- **提交信息**: [metrics] Fix non-streaming TTFT by flushing the first output through detokenization (#38600)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [875dd41](https://github.com/sgl-project/sglang/commit/875dd41e6f5cca73070078fdc198eee21b7c20e1)

- **作者**: Colin Z
- **时间**: 2026-09-29T18:20:10Z
- **提交信息**: [AMD] Fix Load and Inference of MLA models with Quark PTPC FP8 attention on ROCm (#28734)

### [affc602](https://github.com/sgl-project/sglang/commit/affc602f51d0dc85cabb1886d36d1208772a3b80)

- **作者**: Chunan Zeng
- **时间**: 2026-09-29T17:57:20Z
- **提交信息**: [CI] Extend DeepGEMM GB300 validation timeout to three hours (#41720)

### [ced5e9f](https://github.com/sgl-project/sglang/commit/ced5e9fe49386de27aa253497ecacea13c8c39d9)

- **作者**: Ajit Mistry
- **时间**: 2026-09-29T17:18:11Z
- **提交信息**: [Kimi] Enable GB300 TP4 and GB200/GB300 TP16 SP collectives (#35330)

Co-authored-by: Ajit Mistry <ajmistry@amistry.nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [fa090f7](https://github.com/sgl-project/sglang/commit/fa090f77551844087456f648ff7e10c1b7ae7ad7)

- **作者**: CYJiang
- **时间**: 2026-09-29T16:51:08Z
- **提交信息**: [MUSA] Fix fused MoE GEMV registration and torchada pin (#41444)

### [98fce73](https://github.com/sgl-project/sglang/commit/98fce73d5bd0a25afe7d68443d314190b1c47e64)

- **作者**: ashwini rathi
- **时间**: 2026-09-29T12:09:53Z
- **提交信息**: [XPU] publish nightly docker image with sgl-kernel-xpu built from main (#41650)

### [4a4e1ce](https://github.com/sgl-project/sglang/commit/4a4e1ce0140cacc52e2903bc8403ad762f6c68c7)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-29T12:07:37Z
- **提交信息**: [Router] Hold a booting rank's batches and graft a snapshot on the pump (7/13) (#40693)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8d1643b](https://github.com/sgl-project/sglang/commit/8d1643b21ea43ab86d9575302075fd1b951ab313)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-29T11:58:11Z
- **提交信息**: [Router] Vet a peer's snapshot before it may touch the tree (6/13) (#40692)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8b3a4ca](https://github.com/sgl-project/sglang/commit/8b3a4cad8be68a23f480b4c4ee07189150931d86)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-29T11:06:13Z
- **提交信息**: [Router] Track a booting rank's bootstrap and fetch a peer's snapshot (5/13) (#40691)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7bcfcf5](https://github.com/sgl-project/sglang/commit/7bcfcf5aa0e511058fb1fe021c9b17ad99d993c4)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-29T10:56:32Z
- **提交信息**: [Router] Watch EndpointSlices for sibling router replicas (4/13) (#40690)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c5a38d3](https://github.com/sgl-project/sglang/commit/c5a38d3998b33c07ca99afea0b6838969fff2d1e)

- **作者**: Kan Wu
- **时间**: 2026-09-29T10:55:58Z
- **提交信息**: [sgl-router] Add --tokenizer-backend fast and --tokenizer-l1-cache-mb (#41268)

Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5828cd4](https://github.com/sgl-project/sglang/commit/5828cd49276a419402b316aec0236e5c2161e46d)

- **作者**: Michael
- **时间**: 2026-09-29T09:49:01Z
- **提交信息**: [AMD] Add GLM-5.3 MI30x and MI35x nightly accuracy tests (#41602)

Co-authored-by: Claude <noreply@anthropic.com>

### [f731e82](https://github.com/sgl-project/sglang/commit/f731e82f09be137cfc5001c732f044dd44740c1d)

- **作者**: Rumit Desai
- **时间**: 2026-09-29T09:26:27Z
- **提交信息**: Fix MUSA detection under torch.compile fullgraph (#41065)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [0e586fd](https://github.com/sgl-project/sglang/commit/0e586fd12d63f06306ec20beb637bfeb331f1088)

- **作者**: Carrie Chen
- **时间**: 2026-09-29T09:25:10Z
- **提交信息**: fuse shared experts with routed experts in MegaMoE's DeepGEMM (#39313)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [c9cb32e](https://github.com/sgl-project/sglang/commit/c9cb32e3106118ba42edd885e775916fafbf4aff)

- **作者**: kangwangamd
- **时间**: 2026-09-29T09:20:42Z
- **提交信息**: [AMD] fix kda decode flydsl import (#40546)

Co-authored-by: Bingxu Chen <bingxche@amd.com>
Co-authored-by: Michael <13900043+michaelzhang-ai@users.noreply.github.com>

### [34a1234](https://github.com/sgl-project/sglang/commit/34a1234d212fefe86acbc943114187a2a89cfa2e)

- **作者**: Liang Gong
- **时间**: 2026-09-29T09:12:28Z
- **提交信息**: chore: expose agent skills via `.agents` directories (#40515)

### [05817a4](https://github.com/sgl-project/sglang/commit/05817a40c98a09021945f894b8200911df8e1ec6)

- **作者**: Michael
- **时间**: 2026-09-29T08:46:52Z
- **提交信息**: [AMD] Fix GLM-5.3 quark MoE MI35x test runner config (#41464)

### [bd78095](https://github.com/sgl-project/sglang/commit/bd780950300a0c236509352bab44d8a8a98f36c2)

- **作者**: Jiacong Fang
- **时间**: 2026-09-29T07:38:58Z
- **提交信息**: [Fix] Add name mapping in load_weights of nvidia/LocateAnything-3B (#41059)

### [dc1bd46](https://github.com/sgl-project/sglang/commit/dc1bd468020f8f543139d3f0e55d4d694e2d928c)

- **作者**: Mick
- **时间**: 2026-09-29T07:27:22Z
- **提交信息**: [diffusion] feat: support bounded exact conditioning cache across native models (#40470)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1287
- **最后更新**: 2026-09-29T13:34:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92959
- **最后更新**: 2026-09-30T01:16:57Z

## 提交统计

- **昨日提交总数**: 60
- **提交者数量**: 48
- **主要提交者**: Misha Goin, Jakub Zakrzewski, Lio Einaudi

## AI分析总结

根据vllm仓库昨日（约60条）的提交记录分析，总结如下：

### 1. 主要更新类型
*   **Bug修复（占比最高）**：大量修复集中在前端API（如Responses API的工具调用ID保留、`parallel_tool_calls`参数）、核心功能（如数据并行路由、请求中止后状态重置）及特定模型（如Mamba、GLM-5.3-Flash）的推理正确性上。
*   **性能优化**：包括内核优化（TP=2/4/8的矩阵乘法表）、KV缓存传输效率提升、减少Triton采样器预热编译开销、以及优化运行时内核重编译问题。
*   **功能增强与新模型支持**：新增了对DeepSeek-V4.1、MiMo-V2.6等模型特性的支持；扩展了“Fast Start”功能以支持流水线并行（PP）；改进了多模态、工具调用及量化推理。
*   **基础设施与维护**：包括CI/CD优化（尤其是AMD ROCm平台超时、镜像和测试路径修复）、依赖安全更新（aiohttp等）、代码质量提升（修复mypy类型错误）及文档构建加速。

### 2. 关键变更点与项目方向
*   **核心推理正确性与稳定性**：对工具调用、前缀缓存、数据并行等关键路径的bug修复，直接提升了API的稳定性和开发者体验，是项目走向生产就绪的关键。
*   **性能与效率深化**：从内核、采样器到KV缓存传输的多层面优化，旨在降低服务延迟和成本，紧扣项目“快速、低成本”的核心目标。
*   **硬件生态拓展**：对AMD ROCm（MI300/MI355）平台的持续修复、测试镜像和CI支持，以及对NVIDIA新架构内核的优化，体现了项目对广泛硬件兼容性的追求。
*   **“快速启动”体验完善**：相关提交解决了显存计算、权重加载和并行支持问题，旨在显著降低模型首次推理的延迟（冷启动时间），提升易用性。

### 3. 对项目的影响与潜在意义
*   **提升生产环境可靠性**：大量针对前端和核心引擎的修复，将增强用户部署服务的信心，尤其在复杂工具调用和多轮对话场景下。
*   **降低总拥有成本（TCO）**：性能优化直接转化为更高的吞吐量和更低的资源消耗，使vLLM在成本敏感场景中更具吸引力。
*   **扩大用户群体**：对新模型、新硬件及量化方案的支持，降低了先进模型（如DeepSeek-V4.1）和多样化硬件环境下的使用门槛。
*   **增强社区贡献活力**：提交来自多个个人及公司（AMD、NVIDIA、Red Hat等），表明项目生态健康，能持续吸收外部力量进行维护和发展。

### 4. 值得关注的技术点
*   **动态内核编译优化**：通过减少Triton采样器预热特化和避免运行时内核重编译，来加速模型加载与首次推理。
*   **内存与计算协同**：将守护进程持有的模型权重纳入`gpu_memory_utilization`计算，确保资源分配更精准。
*   **高效数据传输**：在分布式KV缓存场景下，通过“合并传输区域”等技术优化网络数据包，提升跨节点效率。
*   **精细化资源管理**：在模型量化（如compressed-tensors）和稀疏注意力等场景中，修复了休眠模式下元数据被意外清零等边界问题。

### 5. 对项目发展的影响
这些提交共同推动vLLM向一个更**健壮、高效和易用**的LLM推理服务平台演进。持续的bug修复和性能调优夯实了基础；对新硬件和模型的快速支持保持了技术前沿性；“快速启动”等功能优化则降低了使用门槛。项目通过广泛的社区协作，正朝着其“为每个人提供简单、快速、低成本LLM服务”的使命稳步前进，有望在开源LLM服务领域建立更稳固的地位。

## 详细提交记录

### [4e0a414](https://github.com/vllm-project/vllm/commit/4e0a414c440e489d472a797ff1028cfc41565693)

- **作者**: Lio Einaudi
- **时间**: 2026-09-29T23:51:50Z
- **提交信息**: [Kernel][Perf] Add TP=2/4/8 per-rank shapes to the sm_120 batch-invariant matmul table (#58495)

Signed-off-by: LioEinaudi <zhao3024667639@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [be25507](https://github.com/vllm-project/vllm/commit/be255076d0498c163441d4aa3fc9d2da142f30fd)

- **作者**: Harshil
- **时间**: 2026-09-29T23:12:15Z
- **提交信息**: [Bugfix] Reject a prefix_match_unit that a single KV cache group cannot honor (#58021)

Signed-off-by: QHarshil <harshil_c@hotmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [eec2a86](https://github.com/vllm-project/vllm/commit/eec2a86b1ed7d76b89f7afe25594acd9b0dd88a1)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-29T23:00:36Z
- **提交信息**: [Security] Bump nltk, aiohttp, pillow, and datamodel-code-generator (#59249)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0755e69](https://github.com/vllm-project/vllm/commit/0755e69e75838babf3eca3fcdb74799b92aa3ea2)

- **作者**: RongJie G
- **时间**: 2026-09-29T22:45:14Z
- **提交信息**: [Bugfix][Responses API] Preserve built-in tool output call IDs (#55596)

Signed-off-by: CorgiBoyG <111257566+CorgiBoyG@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [c37f86e](https://github.com/vllm-project/vllm/commit/c37f86e5721f089a27c8e4358c30e435805fcaab)

- **作者**: drakosha
- **时间**: 2026-09-29T22:36:39Z
- **提交信息**: [Bugfix] GLM-5.3-Flash: fp8 plan dtype on SM90 sparse MLA, and right-size the indexer prefill workspace (#55222)

Signed-off-by: Mikhail Kostryukov <mike@triptrack.net>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Mikhail Kostryukov <drakosha81@proton.me>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [50239df](https://github.com/vllm-project/vllm/commit/50239dfc4d10f007887f2cbc042809e3f4c2ceeb)

- **作者**: Tyler Michael Smith
- **时间**: 2026-09-29T22:36:30Z
- **提交信息**: [WideEP] Change DeepEPv2 to auto select hybrid mode by default (#57991)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [7975057](https://github.com/vllm-project/vllm/commit/797505747f7847e4415fb1db604421810de1865e)

- **作者**: Flora Feng
- **时间**: 2026-09-29T22:36:11Z
- **提交信息**: [Bugfix][Frontend] Honor parallel_tool_calls=false in the Responses API (#59298)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [a7a9ac2](https://github.com/vllm-project/vllm/commit/a7a9ac2745f47e55fa21ffe6bb5c94d2e086efa1)

- **作者**: aoshen02
- **时间**: 2026-09-29T22:20:51Z
- **提交信息**: [Core] Combine per-engine utility results like the Rust client (#59240)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5e887a0](https://github.com/vllm-project/vllm/commit/5e887a078b764e69b6579926619e25eb4f0066dc)

- **作者**: cherry77-cloud
- **时间**: 2026-09-29T21:58:46Z
- **提交信息**: [Bugfix] Route Step3p5 forced tool choices through XML parser (#51810)

Signed-off-by: taking-lying-flat <1615405@qq.com>
Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [4e7af3b](https://github.com/vllm-project/vllm/commit/4e7af3b0de4cae4f70056da590f2f3d676223978)

- **作者**: Ostring24
- **时间**: 2026-09-29T21:33:28Z
- **提交信息**: [Bugfix][Frontend] Enforce parallel_tool_calls=false in the required-tool grammar (#50502)

Signed-off-by: ostring <ostring@qq.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [1ee7f78](https://github.com/vllm-project/vllm/commit/1ee7f78e806b5e9b7476c74edf453b58fe108157)

- **作者**: Misha Goin
- **时间**: 2026-09-29T21:23:27Z
- **提交信息**: [Perf] Reduce redundant Triton sampler warmup specializations (#58605)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d882bdd](https://github.com/vllm-project/vllm/commit/d882bddbeab6b4a0d5861dfcb171bf61ce2109d6)

- **作者**: Jared Wen
- **时间**: 2026-09-29T21:00:16Z
- **提交信息**: [Bugfix][Mamba] Keep the prompt-end prefill checkpoint under sparse retention (#59146)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [1d331f8](https://github.com/vllm-project/vllm/commit/1d331f8341f09636c0182a4b48112f8e4f7d027c)

- **作者**: yzong-rh
- **时间**: 2026-09-29T20:40:15Z
- **提交信息**: [Bugfix] Suppress HarmonyError Unexpected token while expecting start token 200006 (#59254)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [faacc13](https://github.com/vllm-project/vllm/commit/faacc13565312d29e9596d182fc808b452a4508e)

- **作者**: Stary
- **时间**: 2026-09-29T20:29:04Z
- **提交信息**: [Perf][KV Connector][Mooncake] Pack hybrid/MLA KV into coalesced transfer regions (#57952)

Signed-off-by: staryxchen <staryxchen@tencent.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [5dd6931](https://github.com/vllm-project/vllm/commit/5dd693122c51198345847f384648fc5ed6314157)

- **作者**: Martin Hickey
- **时间**: 2026-09-29T20:27:45Z
- **提交信息**: [MyPy][2/N] Fix mypy errors in small tests/ dirs (#51043)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a96ee59](https://github.com/vllm-project/vllm/commit/a96ee5935d769ab72ca5c4dea5ee9b9964c9a45e)

- **作者**: sashko-zakharchuk
- **时间**: 2026-09-29T19:46:00Z
- **提交信息**: [MRV2] Add DRY as a custom logits processor example (#50584)

Signed-off-by: Oleksandr Zakharchuk <oleksandr.zakharchuk@gmail.com>

### [19a4d66](https://github.com/vllm-project/vllm/commit/19a4d66a0bdd01405ea14ab9a5ea12fb0ff87cf2)

- **作者**: hubunt
- **时间**: 2026-09-29T19:37:12Z
- **提交信息**: [Bugfix] Avoid JSON constraints for native tool parsers (#47512)

Signed-off-by: Flora Feng <4florafeng@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [7aa8372](https://github.com/vllm-project/vllm/commit/7aa8372ef76b333d179029b1ed6270cc76f3c7c5)

- **作者**: Aarushi Jain
- **时间**: 2026-09-29T19:25:01Z
- **提交信息**: [ROCm][CI] Run Basic Correctness Sleep Mode on MI300 for now (#59262)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

### [30ae824](https://github.com/vllm-project/vllm/commit/30ae8248b663ea56398d44d30c0d8276a598c4a0)

- **作者**: YukioZzz
- **时间**: 2026-09-29T19:14:24Z
- **提交信息**: [KVConnector][MoRIIO] Support K3 DSpark hybrid READ (#57700)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [35cd03e](https://github.com/vllm-project/vllm/commit/35cd03ebff344cc933ef7f42e45cfb19c76d0db7)

- **作者**: Andrey Talman
- **时间**: 2026-09-29T18:50:12Z
- **提交信息**: [CI] Mint the CRCR report's OIDC token after the wait, not before (#59259)

### [4dc57d4](https://github.com/vllm-project/vllm/commit/4dc57d44c4a790a210ad17cde2e1af98146f8bca)

- **作者**: Shimi Bandiel
- **时间**: 2026-09-29T18:43:44Z
- **提交信息**: [Frontend] Attach resolved logprobs to streaming derender chunks (#55029)

Signed-off-by: Shimi Bandiel <shimib@google.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [df4dbe4](https://github.com/vllm-project/vllm/commit/df4dbe46e7521e073a63c68247245323d86de9d5)

- **作者**: djramic
- **时间**: 2026-09-29T18:25:49Z
- **提交信息**: [CI][ROCm] Increase timeouts for AMD MI300 jobs near their limits (#59227)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [91de237](https://github.com/vllm-project/vllm/commit/91de237333e5f72b12e4de9f535e5774f9bfb1de)

- **作者**: Chanbin Lim
- **时间**: 2026-09-29T18:15:13Z
- **提交信息**: [Bugfix][DP] add_dp_placement_groups does not require ray[default] (#57648)

Signed-off-by: beenpow <57864041+beenpow@users.noreply.github.com>

### [9a190f1](https://github.com/vllm-project/vllm/commit/9a190f142c8acccffd0b19d2393e1eb76f775aea)

- **作者**: Ashraf Bhuiyan
- **时间**: 2026-09-29T18:13:52Z
- **提交信息**: [Mypy] Fix mypy typing for Zamba2 models (#58255)

Signed-off-by: Ashraf Bhuiyan <mbhuiyan@redhat.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [467d81d](https://github.com/vllm-project/vllm/commit/467d81d9a098c5f6695c67832a372a7ad8cd835a)

- **作者**: Chaitanya Sri Krishna Lolla
- **时间**: 2026-09-29T18:07:31Z
- **提交信息**: [ROCm] Upgrade MoRI version on rocm dockers required for WideEP DP16 DI CI enablement and fixes for combine API (#56073)

Signed-off-by: Shiksha Patel <shiksha.patel@amd.com>
Signed-off-by: lcskrishna <lollachaitanya@gmail.com>
Co-authored-by: shikamd123 <shikpate@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [afac509](https://github.com/vllm-project/vllm/commit/afac509a333db6d4ffa1f35b13c27c9e0c1f33aa)

- **作者**: Bugen Zhao
- **时间**: 2026-09-29T18:01:54Z
- **提交信息**: [Bugfix][Rust Frontend] Skip engine-derived metrics under `--disable-log-stats` (#59205)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f5ed3d9](https://github.com/vllm-project/vllm/commit/f5ed3d9c03ec634fbfe670baaf234569bbdecf96)

- **作者**: siyu
- **时间**: 2026-09-29T17:58:35Z
- **提交信息**: [Fast Start] Charge daemon-held weights against `gpu_memory_utilization` (#57298)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Xun Sun <UNIDY2002@outlook.com>

### [cb4f016](https://github.com/vllm-project/vllm/commit/cb4f016c5d02c9d483e6e3f1702d51da239b1a9b)

- **作者**: Jung Jiyu
- **时间**: 2026-09-29T16:53:20Z
- **提交信息**: [Bugfix] Fix standalone torch.compile cache loading after relocation (#52142)

Signed-off-by: jungjiyu <libraryofjiyu@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [cd94b21](https://github.com/vllm-project/vllm/commit/cd94b21264a76c484a567566658995fd3a84db65)

- **作者**: aoshen02
- **时间**: 2026-09-29T16:46:56Z
- **提交信息**: [Bugfix][Frontend] Return 400 for malformed RL dev route bodies (#59236)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [31876d8](https://github.com/vllm-project/vllm/commit/31876d8ea166e9fbeb6782466954151fd7e06a91)

- **作者**: Isotr0py
- **时间**: 2026-09-29T16:34:48Z
- **提交信息**: [Bugfix] Fix TorchCodec audio IO correctness (#58364)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [c3a4a36](https://github.com/vllm-project/vllm/commit/c3a4a36c201f8da384e43d14600ffaa2802930c6)

- **作者**: stefankoncarevic
- **时间**: 2026-09-29T16:32:04Z
- **提交信息**: [CI][ROCm] Fix stale basic_correctness path in Model Runner V2 Distributed (#59201)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [2454b5a](https://github.com/vllm-project/vllm/commit/2454b5a4f0c4c65109fff40e9c60e94bc0245bd2)

- **作者**: Ashraf Bhuiyan
- **时间**: 2026-09-29T16:10:28Z
- **提交信息**: [Mypy] Fix mypy typing for Whisper models (#58254)

Signed-off-by: Ashraf Bhuiyan <mbhuiyan@redhat.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [f4917da](https://github.com/vllm-project/vllm/commit/f4917dadc8b44b75e880d870588f9ddbd874f412)

- **作者**: AlanFokCo
- **时间**: 2026-09-29T15:34:15Z
- **提交信息**: [Bugfix][Quantization] Stop sleep(level=2) from zeroing compressed-tensors KV scales (#57163)

Signed-off-by: AlanFokCo <alanfok2868@gmail.com>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [8aaeef3](https://github.com/vllm-project/vllm/commit/8aaeef343a103bea13aadbbd55978df2c272744e)

- **作者**: Giulio De Pasquale
- **时间**: 2026-09-29T15:33:01Z
- **提交信息**: [Bugfix][MiMo] Declare embedding_fields so an EPD pair can serve images (#58938)

Signed-off-by: Giulio De Pasquale <git@depasquale.giugl.io>

### [ac7f3e1](https://github.com/vllm-project/vllm/commit/ac7f3e11ea88fff26e322f529c2e563dac2f663a)

- **作者**: ahmed xijiaat
- **时间**: 2026-09-29T15:21:27Z
- **提交信息**: [Bugfix] Profile maximum DeepSeek V4.1 vision features (#57898)

Signed-off-by: ahmed xijiaat <52128022+xijiaat@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [741edee](https://github.com/vllm-project/vllm/commit/741edeebeec3cedbe938d831b6d87641ed6191ef)

- **作者**: stefankoncarevic
- **时间**: 2026-09-29T13:27:34Z
- **提交信息**: [Bugfix][CI] Assert the logger call the Anthropic merge warning makes (#59202)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [cd947f5](https://github.com/vllm-project/vllm/commit/cd947f5c629f16fb1ac8ac243481ce82bfa6f5a2)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-09-29T13:27:03Z
- **提交信息**: [MM] Fix compiled ViT attention output layouts (#58182)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [d95d1dc](https://github.com/vllm-project/vllm/commit/d95d1dcfb975240d125b327f1eaef1cbd56ef56c)

- **作者**: Shijin Zhang
- **时间**: 2026-09-29T13:26:34Z
- **提交信息**: [Bugfix][Frontend] Force reasoning mode for GLM-5.3 chat templates in the GLM MoE parser (#56994)

Signed-off-by: Shijin Zhang <75300765+Dovis01@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [dfc8e0f](https://github.com/vllm-project/vllm/commit/dfc8e0f3e2ad7791ba32e2e88053cda064052208)

- **作者**: Yixin Dong
- **时间**: 2026-09-29T12:47:47Z
- **提交信息**: [Frontend] Support strict MiMo-V2.6 tool calling (#58019)

Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: yuchuan <yuchuan.7streams@gmail.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: Ubospica <ubospica@gmail.com>
Signed-off-by: yuchuan <yuchuan.7streams@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [79a0307](https://github.com/vllm-project/vllm/commit/79a0307d7463b11938c30e924c606509601b22aa)

- **作者**: jack
- **时间**: 2026-09-29T12:42:02Z
- **提交信息**: [Config] Remove Engram CUDA-alike device restrictions (#59171)

Signed-off-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>

### [998490c](https://github.com/vllm-project/vllm/commit/998490cd9f297381288eb631bc98a4dfe1304f57)

- **作者**: Harry Mellor
- **时间**: 2026-09-29T11:16:33Z
- **提交信息**: [Docs] Speed up docs build ~5x (#58705)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [05d8963](https://github.com/vllm-project/vllm/commit/05d89636fca80d806732ced636ef505f42e6fe35)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T10:28:15Z
- **提交信息**: [ROCm][CI] Mirror generic GEMM-RS/AR on MI355 (#58433)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3f3fbe2](https://github.com/vllm-project/vllm/commit/3f3fbe286f25ead10f793dea0c549a99c196ad11)

- **作者**: Reid
- **时间**: 2026-09-29T10:24:28Z
- **提交信息**: [Bugfix][Rust Frontend] Account for new requests in DP routing (#58956)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [208bb38](https://github.com/vllm-project/vllm/commit/208bb38c80984e29c03282d295d50325f5895338)

- **作者**: Louie Tsai
- **时间**: 2026-09-29T10:11:53Z
- **提交信息**: [Bugfix][Rust Frontend] Fix startup with config-only model (#58643)

Signed-off-by: louie-tsai <louie.tsai@intel.com>

### [af5b485](https://github.com/vllm-project/vllm/commit/af5b4857e1353c01fd6bf41bc3cb9f84dc82dd89)

- **作者**: siyu
- **时间**: 2026-09-29T09:37:43Z
- **提交信息**: [Fast Start] Support PP (#55477)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Xun Sun <UNIDY2002@outlook.com>

### [77e5264](https://github.com/vllm-project/vllm/commit/77e52645e9baba15d6b9cd7e09a12e70628b8237)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-09-29T09:37:20Z
- **提交信息**: [Bugfix][Model] MiMo: keep fused fp8 qkv_proj pairing state across weight-loading calls (#58142)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [4861833](https://github.com/vllm-project/vllm/commit/4861833ae280cf56e7802e6f2adb797031b51449)

- **作者**: aoshen02
- **时间**: 2026-09-29T09:23:32Z
- **提交信息**: [Bugfix][Core] Allow AuxOutput reset after abort without running requests (#59060)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [3e2a7e7](https://github.com/vllm-project/vllm/commit/3e2a7e74a556623ddee3a327299d7bf04055501e)

- **作者**: Chauncey
- **时间**: 2026-09-29T09:14:30Z
- **提交信息**: [Feat][Model] Enable KDA prefill checkpoints for GLM-5.3-Flash (#56960)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [3acddf0](https://github.com/vllm-project/vllm/commit/3acddf01e709b13693d3a90d25fdb74d8124049c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T09:14:26Z
- **提交信息**: [Bugfix][ROCm] Keep Mooncake bootstrap ports bound during startup (#58967)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6ebb5bd](https://github.com/vllm-project/vllm/commit/6ebb5bd64f5ef75dbe1471ee88c009003b3d03ec)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T08:40:07Z
- **提交信息**: [ROCm][CI] Expand MI355 mirrors and route MIG-sized jobs to DPX (#59137)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>

### [70dc122](https://github.com/vllm-project/vllm/commit/70dc122f81346032ebb658b3d00346f31ff1714d)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-09-29T08:33:52Z
- **提交信息**: [MM] Enable device normalization for Llama Nemotron VL Embed/Rerank (#57928)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [61349e3](https://github.com/vllm-project/vllm/commit/61349e342d5a79489e9642042ae03be17610427f)

- **作者**: Chauncey
- **时间**: 2026-09-29T08:31:22Z
- **提交信息**: [Misc] Avoid repeated warnings for merged Anthropic system messages (#59172)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [4b2e1cf](https://github.com/vllm-project/vllm/commit/4b2e1cfa7b8094f1a9547aee41c39e05d2ce5c97)

- **作者**: Yifan Qiao
- **时间**: 2026-09-29T08:25:46Z
- **提交信息**: [Model] Decoder-side SWA bounded replay for DeepSeek-V4.1 (#58132)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9af952c](https://github.com/vllm-project/vllm/commit/9af952c55568f596c1b76c68ced8c5aeb5593a39)

- **作者**: Yashasvi Asthana
- **时间**: 2026-09-29T08:01:52Z
- **提交信息**: [Bugfix][Rust Frontend] Support raise_exception in chat templates (#59020)

Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Yashasvi Asthana <yashasvi.asthana@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [77d9cda](https://github.com/vllm-project/vllm/commit/77d9cda688a21087539a495562134a6f2f205efe)

- **作者**: Jin Tao
- **时间**: 2026-09-29T07:57:23Z
- **提交信息**: [ROCm][Model][Bugfix] Fix GLM-5.2 shared-expert fusion and MTP on the ROCm DSA path (#58904)

Signed-off-by: Jin Tao <jin.tao@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [30f5c01](https://github.com/vllm-project/vllm/commit/30f5c01d4ebb5c493ed86195db24d0ec5b3ce3d7)

- **作者**: Juntian Liu
- **时间**: 2026-09-29T07:31:30Z
- **提交信息**: [DSv4.1] Avoid runtime recompiles of _ring_slot_mapping_kernel (#59119)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [6cbbea8](https://github.com/vllm-project/vllm/commit/6cbbea872141851421dcad5fca009aa6cec93dc6)

- **作者**: Václav Čadek
- **时间**: 2026-09-29T07:11:56Z
- **提交信息**: [Bugfix] Hoist $defs/definitions in Cohere parser tool schema composition (#49602)

Signed-off-by: Václav Čadek <vaclavcadek@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [78fc1e6](https://github.com/vllm-project/vllm/commit/78fc1e6274d326c869432e4dfde8dc5b4c6e85a8)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T07:10:26Z
- **提交信息**: [ROCm][CI] Add MI355 TP2 AR-RMS and B200 fusion mirrors (#58284)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [69d5c81](https://github.com/vllm-project/vllm/commit/69d5c81fcd52f29a3b498dd4c403b088c91e4ee1)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T07:08:31Z
- **提交信息**: [ROCm][CI] Mirror split kernel groups on MI355 and fix exposed tests (#58654)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Signed-off-by: Codex <codex@openai.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [0ae480f](https://github.com/vllm-project/vllm/commit/0ae480ff1a1b07a6959c3b19113739ffd2b60820)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-29T07:06:44Z
- **提交信息**: [CI][ROCm] Mirror large-model GSM8K evaluations on MI355 (#58683)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-30
**监控日期**: 2026-09-29
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7137
- **最后更新**: 2026-09-30T00:18:44Z

## 提交统计

- **昨日提交总数**: 11
- **提交者数量**: 9
- **主要提交者**: jingchengtian, guangli_Liu, vraiti

## AI分析总结

**1. 主要更新类型**
*   **功能新增与模型扩展**：添加了 MiniCPM-o 4.5 和 CosyVoice3 模型支持，引入了 turn-mode MRv2、批处理音频推理和 bounded 长视频修复等新功能。
*   **性能优化**：针对 VAE 推理引入 CUDA Graph 与 tiling 技术，为 MOSS-TTS 和 CosyVoice3 添加了批量推理支持以提升吞吐量。
*   **Bug修复与稳定性提升**：修复了 Qwen3-Omni 的实时路由问题、OpenAI 导入循环错误，并为不支持的管道禁用了异步块功能。
*   **测试与框架改进**：修复了 Qwen3-Omni 的 E2E 测试，扩展了共享的多阶段执行框架以支持混合 V1/MRv2 管道，并新增了 BF16 一致性测试预算。

**2. 关键变更点及与项目方向的关系**
*   **关键变更**：核心框架（[Core]）的扩展旨在更好地支持不同模型版本的混合流水线，这是实现灵活、统一跨模态服务的关键基础设施。性能优化（[Perf]）和新增模型（[Model]）直接增强了系统处理多模态任务的“速度”与“能力范围”。
*   **与项目方向关系**：所有变更都紧密围绕“易、快、省”的项目核心目标。新模型支持扩大了“全模态”覆盖；性能优化致力于“快速”响应；框架统一与错误修复则提升了系统的易用性和稳定性，降低了服务门槛。

**3. 对项目的影响和潜在意义**
*   **功能与生态扩展**：显著丰富了支持的模型库，特别是音频（MiniCPM-o, CosyVoice3, MOSS-TTS）和视频（SeedVR2）生成/理解能力，使项目成为更全面的跨模态服务平台。
*   **性能与效率提升**：CUDA Graph、批量推理等优化有望降低推理延迟、提升吞吐量，使服务更具成本效益。
*   **系统健壮性增强**：多项错误修复和测试改进提升了系统的可靠性和可维护性，为生产环境部署打下更坚实的基础。
*   **架构前瞻性**：对混合流水线框架的扩展，为未来集成更多不同架构或版本的模型预留了灵活空间。

**4. 值得关注的技术点**
*   **批量推理机制**：为 MOSS-TTS 和 CosyVoice3 添加的 per-row generator 和 opt-in packed Flow 技术，是提升多请求并发处理效率的关键。
*   **混合流水线框架**：扩展共享多阶段执行框架以支持混合 V1/MRv2 管道，体现了架构设计的灵活性和前瞻性。
*   **硬件适配与验证**：引入针对 AMD 平台的 BF16 一致性测试预算，显示了项目对硬件生态和计算精度的重视。

**5. 对项目发展的综合影响**
本次提交集中体现了 vllm-omni 项目在**功能丰富度**、**运行效率**和**系统稳定性**三个维度的同步推进。新增的模型直接拓宽了项目的应用场景和用户群体；性能优化与框架改进则从内部提升了服务的核心竞争力；一系列修复和测试加固保障了快速发展的同时不牺牲质量。这些变更共同强化了项目作为“一站式”高效跨模态模型服务解决方案的定位，使其在易用性、性能和可靠性上更趋近“为所有人服务”的愿景。

## 详细提交记录

### [3a28882](https://github.com/vllm-project/vllm-omni/commit/3a28882946fa79318e9e398f660619ab8fec2773)

- **作者**: BruceLoveDecimal
- **时间**: 2026-09-29T23:27:01Z
- **提交信息**: [Perf][Auk] VAE cuda graph and tiling (#7881)

Signed-off-by: liuqihao <liuqihao970610@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [8ad6e80](https://github.com/vllm-project/vllm-omni/commit/8ad6e801f5f4f5bad43c539d8cc80f8062ce9b35)

- **作者**: vraiti
- **时间**: 2026-09-29T20:23:28Z
- **提交信息**: [Tests] Fix Qwen3-Omni E2E LiveKit Test (#8294)

Signed-off-by: vraiti <vraiti@redhat.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [5af3a16](https://github.com/vllm-project/vllm-omni/commit/5af3a16526d3c11a7016763a77d383222bc3027e)

- **作者**: Sy03
- **时间**: 2026-09-29T18:41:39Z
- **提交信息**: [Model] Add MiniCPM-o 4.5 turn-mode MRv2 and batched audio inference (#8222)

Signed-off-by: Sy03 <1370724210@qq.com>

### [43ef1e6](https://github.com/vllm-project/vllm-omni/commit/43ef1e61fbb880a84cfa3416afd56e2be06a413e)

- **作者**: jingchengtian
- **时间**: 2026-09-29T17:13:50Z
- **提交信息**: [Perf][TTS] Add per-row generator support to MOSS-TTS talker to eliminate serial fallback for seeded batched requests (#7922)

Signed-off-by: jingchengtian <jingchengtian@users.noreply.github.com>
Signed-off-by: jingchengtian <tjc1995@126.com>
Co-authored-by: jingchengtian <jingchengtian@users.noreply.github.com>

### [764a109](https://github.com/vllm-project/vllm-omni/commit/764a109f66cd0f600a1dd907af6fd6630eb6e488)

- **作者**: Alex Brooks
- **时间**: 2026-09-29T15:52:09Z
- **提交信息**: [Config] Disable Async Chunk for Unsupported Pipelines (#5099)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [1ea0ee3](https://github.com/vllm-project/vllm-omni/commit/1ea0ee3b38945d43fb9e662f0d32f0be97717189)

- **作者**: Sy03
- **时间**: 2026-09-29T15:48:36Z
- **提交信息**: [Model] Add opt-in packed Flow and batched HiFT inference for CosyVoice3 (#8224)

Signed-off-by: Sy03 <1370724210@qq.com>
Signed-off-by: zack <huixindaddy@yahoo.com>
Co-authored-by: zack <huixindaddy@yahoo.com>

### [c85f1a4](https://github.com/vllm-project/vllm-omni/commit/c85f1a44fb1345af8c903ecb75260ca10a5e3094)

- **作者**: Nick Cao
- **时间**: 2026-09-29T15:07:03Z
- **提交信息**: [Bugfix] Break duplex OpenAI import cycle (#8287)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [f145f66](https://github.com/vllm-project/vllm-omni/commit/f145f66c827c6387440330735c95dcf74e98a6c2)

- **作者**: andyluo7
- **时间**: 2026-09-29T14:43:14Z
- **提交信息**: test: define Wan fused BF16 parity budget (#8188)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [001f8a8](https://github.com/vllm-project/vllm-omni/commit/001f8a80b9d92e5378912f25a4d3ae619d510ce0)

- **作者**: Sy03
- **时间**: 2026-09-29T14:40:57Z
- **提交信息**: [Core] Extend the shared multi-stage execution framework for mixed V1/MRv2 pipelines (#8184)

Signed-off-by: Sy03 <1370724210@qq.com>

### [6b4173f](https://github.com/vllm-project/vllm-omni/commit/6b4173f50b01b16af8938794934ab9668656427c)

- **作者**: guangli_Liu
- **时间**: 2026-09-29T14:23:11Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni realtime routing with typed stage configs (#8279)

Signed-off-by: liuguangli <liuguangli35@gmail.com>
Co-authored-by: liuguangli <liuguangli35@gmail.com>

### [7d6904a](https://github.com/vllm-project/vllm-omni/commit/7d6904aa944b2f11b3e16a4fe0a0a821b245714f)

- **作者**: 0z5a
- **时间**: 2026-09-29T11:33:50Z
- **提交信息**: SeedVR2: bounded long-video restoration (#8102)

Signed-off-by: 0z5a <Dezhen.lu@student.uni-tuebingen.de>
Signed-off-by: 0z5a <dezhen.lu@uni-tuebingen.de>
Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: 0z5a <dezhen.lu@uni-tuebingen.de>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

---
