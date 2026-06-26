# GitHub Stars 合并报告 - 2026-06-26

**合并日期**: 2026-06-27
**监控日期**: 2026-06-26
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


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2046
- **最后更新**: 2026-06-26T05:08:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2446
- **最后更新**: 2026-06-26T11:31:32Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Yang Yong (雍洋), yihuiwen

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复服务器保存结果PNG时保留过多的问题（#1189）。
- **功能优化**：将bagel/flux2中PNG编码从PIL切换为cv2（#1190）；添加垃圾回收（GC）冻结与GC指标（#1188）。
- **资源更新**：更新z-image文件（#1191）。

### 2. 关键变更点及其与项目整体方向的关系
- **`fix server result_png keep too many`**：修正服务器端因未及时清理中间PNG结果导致的内存/磁盘占用膨胀问题。这与项目“轻量视频生成推理”方向一致——控制资源占用，保障长时间推理稳定性。
- **`bagel/flux2 pil->cv2 when encode png`**：将PIL库替换为OpenCV进行PNG编码。OpenCV通常更快、更节省内存，且与框架中其他cv2操作统一。这有助于提升视频帧编码效率，符合“轻量高效”目标。
- **`add gc.freeze & gc metrics`**：引入Python垃圾回收冻结（`gc.freeze`）以减少连续帧推理时GC额外开销，同时添加GC指标便于监控。这对高吞吐、低延迟的推理服务尤为关键，体现了对内存管理和性能调优的重视。
- **`update z-image`**：可能更新了示例图像或测试资源，保持文档/示例与代码同步。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复了服务器结果堆积问题，避免因资源泄漏导致服务崩溃，增强了生产环境可靠性。
- **性能优化**：cv2编码、GC冻结两项改动直接减少CPU/内存开销，有望提升单次推理速度和并发能力。
- **可观测性增强**：GC指标为开发者提供了排查内存泄漏或频繁GC停顿时长的依据，便于持续优化。
- **维护成本降低**：统一编码库（PIL→cv2）减少依赖冲突风险；资源文件更新确保示例可用。

### 4. 值得关注的技术点
- `gc.freeze()`在Python长期运行推理服务中的应用：将内存中不再变动的对象（如模型参数）冻结，避免被Full GC扫描，减少GC暂停时间。
- cv2编码PNG与PIL的差异：cv2基于C/C++底层，对内存连续的数据（如NumPy数组）处理更高效，符合视频帧批量处理场景。
- 服务器结果保留策略的修正：可能涉及输出队列大小或磁盘清理逻辑，是微服务架构中的常见优化点。

### 5. 基于项目背景，这些提交如何影响项目发展
- **强化“轻量”定位**：通过GC优化和编码替换，进一步降低推理框架的资源需求，使其更适配边缘设备或云原生容器环境。
- **完善服务化能力**：修复服务器副作用问题、添加监控指标，推动LightX2V从研究工具向生产级推理服务演进。
- **提升开发体验**：统一cv2编码、更新示例资源，降低新用户集成门槛。
- **奠定未来调优基础**：GC指标为后续自动化调优（如动态调整冻结阈值）提供了数据支撑，符合可观测性驱动的迭代方向。

## 详细提交记录

### [701914d](https://github.com/ModelTC/LightX2V/commit/701914d7cfd5e66774d00e0a2eb669bafce25e2c)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-26T11:31:28Z
- **提交信息**: update z-image (#1191)

### [2868c5c](https://github.com/ModelTC/LightX2V/commit/2868c5cb8926faed3000821a58f994876475342a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-06-26T09:36:40Z
- **提交信息**: Update bagel/flux2 pil->cv2 when encode png (#1190)

### [9337b82](https://github.com/ModelTC/LightX2V/commit/9337b82b79486085d04d1c81996a4490857d3673)

- **作者**: yihuiwen
- **时间**: 2026-06-26T08:52:19Z
- **提交信息**: fix server result_png keep too many (#1189)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

### [fa3e541](https://github.com/ModelTC/LightX2V/commit/fa3e541bc504f2b254f5418038f32686075c5363)

- **作者**: yihuiwen
- **时间**: 2026-06-26T07:18:08Z
- **提交信息**: add gc.freeze & gc metrics (#1188)

Co-authored-by: yihuiwen <yihuiwen@sensetime.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2148
- **最后更新**: 2026-06-26T03:33:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5864
- **最后更新**: 2026-06-26T22:32:03Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 5
- **主要提交者**: Ka-Hyun Nam, kangbintNV, Lain

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **Bug修复**：2项（fp32 MTP状态池写入丢失、GDN内核布局契约错误）
- **功能新增**：1项（MoE A2A combine增加MXFP4/NVFP4量化）
- **测试/CI优化**：1项（大幅缩减MoE测试规模）
- **文档更新**：1项（补充参数和环境变量说明）
- **重构/修复**：1项（MoE路由中enable_pdl标志修复）
- **重命名**：1项（快速跟踪修复）

#### 2. 关键变更点及与项目方向的关系
- **测试修剪（#3733）**：将MoE雷同的测试从1398项削减至570项（-59%），解决CI超预算问题。这符合项目“高性能推理”定位，减少无用测试能加速开发迭代。
- **fp32 MTP状态池修复（#3490）**：修复非连续4D池张量下状态更新丢失的bug，并支持分离读写槽位。这是对**Multi-Token Prediction解码**核心功能的完善，直接影响推理框架（如SGLang）的集成稳定性。
- **GDN内核布局修复（#3693）**：将`mark_compact_shape_dynamic`改为`mark_layout_dynamic`，恢复对packed-QKV（融合缓冲区）布局的支持。直接修复了与SGLang端到端测试的兼容性，体现了项目对实际部署场景的重视。
- **MoE A2A combine量化扩展（#3643）**：新增MXFP4/NVFP4输出量化支持，配合`output_scalar_scale`参数。这进一步丰富了MoE的低精度推理能力，与项目高性能GPU推理目标一致。
- **enable_pdl标志修复（#3588）**：确保MoE路由路径中PDL标志正确传播，使路由行为可控，属于工程稳健性改进。

#### 3. 对项目的影响和潜在意义
- **CI效率大幅提升**：测试缩减使完整CI预算从接近4小时降至可控范围，加速PR合入流程。
- **修复关键正确性bug**：MTP状态池写入丢失是隐蔽的内存语义错误，可能导致模型推理结果错误；GDN布局修复直接影响SGLang等下游框架，有助于提升用户信任度。
- **量化能力扩展**：MoE A2A combine支持FP4量化，使FlashInfer在低比特部署场景中更具竞争力，便于在资源受限的GPU上运行大型MoE模型。
- **文档补全**：`scale_major_mode`和`FLASHINFER_AUTOTUNE_DIR`的文档有助于用户正确使用MLA AutoTuner和API。

#### 4. 值得关注的技术点
- **非连续张量处理**：修复中多次涉及非连续张量（strided slice

## 详细提交记录

### [a7f5c5a](https://github.com/flashinfer-ai/flashinfer/commit/a7f5c5aa2a32b5c6d6e97d3f337b449fedfb1c12)

- **作者**: Alex Yang
- **时间**: 2026-06-26T20:29:56Z
- **提交信息**: Prune moe tests (#3733)

<!-- .github/pull_request_template.md -->

## 📌 Description

test_renormalize_routing ran 1398 passed / 17034 skipped in ~123 min,
exceeding the 2h-per-file budget (and eating a large share of the 4h
full-CI budget). After the shard split (#3635) the fp8 shard alone is
~1020 tests (~90 min) — the bottleneck.

The "renormalize" files are really a catch-all for ungrouped routing
(Renormalize + Default + SigmoidRenorm + MiniMax2), and the bloat comes
from a full cross-product of routing × quant × layout × logits-dtype ×
activation, even though routing correctness is orthogonal to the
quant/GEMM path (they share no kernel code).

**Change**

Four list deletions in the shared RENORMALIZE_* constants
(tests/moe/trtllm_gen_fused_moe_utils.py) — no logic changes:

- Drop fp32 routing-logits dtype (keep bf16): bf16 is the only logits
dtype that exercises MxFP4×MxFp8 / MxFP4×Bf16 / MXINT4 (skip_checks
gates fp32 off those). The fp32-logits path stays covered by
test_deepseekv3_routing (fp32-only) + test_topk_routing.
- Drop Geglu activation: produced 0 passing tests in the renorm configs
(skip_checks only admits Geglu with FP4-NVFP4 + TopK routing + ≤128
tokens). Covered elsewhere.
- Drop synthetic Renorm (256e/top-8) config: no production model at this
size; real Renormalize models are Qwen3 (128e/top-8) and Qwen3-Next
(512e/top-10), both kept.
- Drop MiniMax2_256e_top6_scale3 config: the no-scale variant already
covers the MiniMax2 method; this only varied routed_scaling=3.0.

**Impact**

- fp8: 1020 → 375 (−63%)
- fp4: 228 → 126
- bf16: 150 → 69
- Total: 1398 → 570 (−59%)

**Follow-up**

This is a stopgap. The broad routing × quant spread will be relocated to
the unified MoE fuzzer (test_unified_moe_fuzz.py), which needs a
routing-method axis and additional dtype handlers; per-PR coverage then
becomes model-anchored profiles + random-sampled configs.

## 🔍 Related Issues

* #3635 
* #3730

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
  * Reduced Renormalize-family routing coverage to streamline CI runs.
  * Removed the Renorm synthetic configuration case.
* Narrowed the MiniMax2 256e top6 scale3 Renormalize scenario to BF16
MoE only with a single intermediate size.
* Pruned logits dtype coverage by removing the Geglu variant and the
float32 logits option, keeping only bfloat16.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [43db902](https://github.com/flashinfer-ai/flashinfer/commit/43db902d075299ebb4790ebf3ecb6598213b6b6d)

- **作者**: ameynaik-hub
- **时间**: 2026-06-26T20:16:29Z
- **提交信息**: Ameyn/fix fp32 mtp pool out indices (#3490)

<!-- .github/pull_request_template.md -->

## 📌 Description
This is the **fp32 sibling of #3268** — the same 4D-pool support, now
for the **fp32 MTP decode path** (`gated_delta_rule_mtp`).
It does two things:
1. **In-place 4D pool writeback (correctness fix).** Previously a 4D
state pool `[pool_size, HV, V, K]` was reshaped to 3D internally. For a
**non-contiguous** pool (e.g. a strided slice of an oversized backing
buffer) `.reshape()` silently materializes a **copy**, the kernel
updates the copy, and the
caller's pool is left untouched → **state updates lost**. The kernel now
reads/writes the pool **in place via native 4D indexing**
(`use_pool_indexing`), so writes land in the caller's tensor with no
silent copy.
2. **Separate read/write slots (new capability).** New optional
`output_state_indices` arg (shape `[B]`): where to **write** the updated
state, separate from where it is **read** (`initial_state_indices`).
Defaults to `initial_state_indices` (write back to the read slot);
**negative entries skip the
writeback** for that batch slot (matching the read-side `-1` padding
semantics). This is what speculative-decoding / MTP-verify needs: read
prior state from one pool slot, write the verified state to another.
```python
out, state = gated_delta_rule_mtp(
q, k, v,
initial_state=pool, # 4D pool, contiguous OR strided
initial_state_indices=read_idx,
output_state_indices=write_idx, # NEW (optional; defaults to read_idx;
-1 = skip)
...
)
```
The rest of the signature is unchanged; the standard contiguous
single-token/MTP path behaves identically.
### Rebased on current `main`
This branch was merged up to current `main`, which required reconciling
the feature with two landed changes:
- **#3649** (batch-size-agnostic GDN compilation): `B`/`pool_size` are
no longer part of the kernel cache key, so the cache keys here were
updated to match the batch-agnostic kernel stubs.
- **#3502** (BF16 recovery / per-request K, FLA per-token scatter): the
writeback guards now compose with `per_token_pool_scatter`.
The non-contiguous 4D pool is passed through `from_dlpack` without
`mark_compact_shape_dynamic` (which assumes a compact 3D layout);
strides are keyed via `pool_strides_key` and the pool-dim stride is
batch-size-independent, so a single compiled kernel is reused across
batch sizes — compilation stays
batch-size-agnostic.

## 🧪 Tests
  
Added to `tests/gdn/test_decode_delta_rule.py`:
- `test_mtp_fp32_state_pool` — pool read/write across seq lengths and
batch sizes, optional separate output indices, intermediate-state
caching. Params: `batch_size ∈ {1,4,16} × seq_len ∈ {2,4} ×
use_separate_output_indices ∈ {F,T} × cache_intermediate_states ∈ {F,T}`
(24 cases).
- `test_mtp_fp32_state_pool_non_contiguous` — strided (non-contiguous)
pools. Params: `batch_size ∈ {1,4} × seq_len ∈ {2,4} × stride_multiplier
∈ {2,3}` (8 cases).




This is the fp32 sibling of PR #3268 — same 4D-pool support, now for the
fp32 MTP decode path.
  
  ### Before vs after — wrapper-side
  
  ```python
  # Before
  out, state = gated_delta_rule_mtp( 
      q, k, v,
      initial_state=pool,            # 4D pool
      initial_state_indices=read_idx,
      ...
  ) 
  # Internally: pool is reshaped to 3D. If pool is non-contiguous,
  # this silently materializes a copy → kernel updates the COPY,
  # original pool is left untouched. Updates lost.
  
  # After
  out, state = gated_delta_rule_mtp( 
      q, k, v,
      initial_state=pool,            # 4D pool, contiguous OR strided
      initial_state_indices=read_idx,
output_state_indices=write_idx, # NEW (optional, defaults to read_idx)
      ...
  )
  # Kernel reads/writes pool in place via native 4D indexing.
  # No silent copy. Writes land in the caller's tensor.
  

Before vs after — memory layout the kernel sees
    
  Contiguous pool (unchanged fast path):
    caller's [pool, HV, V, K]  ─reshape view→  kernel's [pool*HV, V, K]
                                (free, no copy)
    
  Non-contiguous pool (the new path):  
    Before:  caller's strided [pool, HV, V, K]
             ─.reshape() silent copy→  scratch [pool*HV, V, K]
             kernel writes scratch ❌ (caller's  pool unchanged)
             
    After:   caller's strided [pool, HV, V, K]
             ─pass through, use_pool_indexing=True→  kernel
             kernel writes caller's pool in place ✓
  

API change — one new argument
      
  output_state_indices : torch.Tensor, optional (shape [B])
      Where to WRITE the updated state, separate from where you READ.
      Defaults to initial_state_indices (write back to the read slot).
      Negative entries skip the writeback for that batch.
  
  Everything else in the signature behaves identically.
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
* Multi-token FP32 decoding: supports pool-backed initial states,
per-batch configurable output-state writeback indices, and correct
handling for non-contiguous pooled layouts. Non-pool single-token decode
behavior remains unchanged.

* **Tests**
* New FP32 tests cover pool read/write across sequence lengths and batch
sizes, optional separate output indices, intermediate-state caching,
non-contiguous pools, and stride variations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Amey Naik <212485788+ameynaik-hub@users.noreply.github.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [c207ad3](https://github.com/flashinfer-ai/flashinfer/commit/c207ad319a6cd996406d2d1c8f4f0f6ecc350800)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-06-26T20:15:53Z
- **提交信息**: Bug fix (gdn): Layout contract fix from #3649 (#3693)

<!-- .github/pull_request_template.md -->

## 📌 Description

#3649 made the GDN decode kernels batch-size agnostic by marking the
per-batch tensors (q/k/v/a/b/o) with CuTe's
`mark_compact_shape_dynamic`, which requires a compact layout. This was
a functional layout coverage regression, and flagged as being
incompatible with an e2e sglang test.

The fix is to mark the per-batch tensors with `mark_layout_dynamic`
instead of `mark_compact_shape_dynamic`.

To verify this fix, this PR adds packed-QKV coverage for unit tests:
q/k/v built as head-dim slices of a fused buffer (the SGLang layout),
asserting results to the contiguous equivalents. These fail on current
main (reproducing the regression) and pass with the fix.

## 🔍 Related Issues

none

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

* **Refactor**
* Improved dynamic-shape/layout annotations used for cached and compiled
decoding kernels across pretranspose, nontranspose, and MTP paths,
better aligning with fused/packed QKV layouts and ensuring consistent
handling of cached intermediates.

* **Bug Fixes**
* Fixed decoding behavior for packed, non-contiguous Q/K/V tensor views
to produce consistent results (including bit-identical outputs vs
contiguous tensors).

* **Tests**
* Added regression tests covering pretranspose, nontranspose, and MTP
decode with packed/non-contiguous Q/K/V views, including output/state
equivalence checks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [13a49bd](https://github.com/flashinfer-ai/flashinfer/commit/13a49bd97221968029a1ce283c88ddfbaf295a16)

- **作者**: Lain
- **时间**: 2026-06-26T18:51:32Z
- **提交信息**: chore: fix enable_pdl for trtllm-gen routing and finalize kernel (#3588)

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
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a configurable `enable_pdl` runtime flag for MoE routing
behavior, defaulting to PDL enabled, to give finer control over routing
execution.
* **Bug Fixes / Stability**
* Routing and MoE setup now consistently propagate the `enable_pdl` flag
across all routing paths and MoE data preparation steps, preventing
mismatched behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>

### [85c48eb](https://github.com/flashinfer-ai/flashinfer/commit/85c48eb61b9e2fcf26cccc52e2e13c4d5adb682e)

- **作者**: Lain
- **时间**: 2026-06-26T17:15:00Z
- **提交信息**: feat: add mxfp4/nvfp4 quant to moe a2a combine (#3643)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow up PR for #3376. Implement mxfp4/nvfp4 quant in moe a2a combine.

Add `output_scalar_scale: float = 1.0` to API.

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

## Release Notes

* **New Features**
* Added FP4 output quantization modes for MoE all-to-all combine (MXFP4
and NVFP4).
* Added an `output_scalar_scale` parameter to control FP4 scaling
behavior.

* **Behavior Changes**
* Quantized combine now supports additional packing/output layout for
FP4-related outputs, and validates supported dtype combinations and
compute capability.

* **Tests**
* Expanded and refactored MoE all-to-all combine tests to cover
MXFP4/NVFP4 end-to-end (including result comparison via FP4
quant/dequant).
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>

### [647c52d](https://github.com/flashinfer-ai/flashinfer/commit/647c52da20f001a196be10fb6042aa8985b75e0a)

- **作者**: kangbintNV
- **时间**: 2026-06-26T08:57:40Z
- **提交信息**: docs: document scale_major_mode param and FLASHINFER_AUTOTUNE_DIR env var (#3696)

## Summary

- `moe_gemm_mxfp8_nt_groupwise`: add missing `scale_major_mode`
parameter documentation to the docstring (currently only `"MN"` is
supported).
- `CLAUDE.md`: add `FLASHINFER_AUTOTUNE_DIR` to the Validation /
Autotuning env var table (read in `flashinfer/mla/_sparse_mla_sm120.py`
to override MLA AutoTuner cache path).

## Test plan

- [x] `pre-commit run -a` passes

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Added environment variable documentation for configuring MLA AutoTuner
cache storage location with automatic fallback to the default workspace
directory when unset.
* Clarified supported parameter options and defaults in kernel function
documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e1a828e](https://github.com/flashinfer-ai/flashinfer/commit/e1a828eac82eb661f9cfbd636d632efe76777a87)

- **作者**: Alex Yang
- **时间**: 2026-06-26T08:23:44Z
- **提交信息**: rename back (#3730)

<!-- .github/pull_request_template.md -->

## 📌 Description

quick follow up to #3635 

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

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3772
- **最后更新**: 2026-06-26T19:42:33Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: William Lin, Raghav K

## AI分析总结

### 结合 `hao-ai-lab/FastVideo` 项目背景的昨日更新分析

- **主要更新类型**  
  - **性能优化**（核心）：将 Wan VAE 解码默认切换到 bf16 格式（标注为无损、更快）。  
  - **杂项修复**：修复 pre-commit 钩子问题，提升代码规范维护。  
  - **文档更新**：修改 README.md（可能涉及说明补充或格式调整）。

- **关键变更点与项目方向的关系**  
  - **bf16 解码优化**：直接契合项目名“FastVideo”的“快速”目标，通过降低精度但保持输出质量来加速视频处理流水线中的 VAE 解码环节，属于性能关键路径的深度优化。  
  - **pre-commit 修复**：维持代码风格一致性，保障多人协作时的代码质量，体现项目工程化水平的持续提升。  
  - **README 更新**：改善文档可用性，帮助用户快速理解和使用项目，与官方文档、快速开始等资料形成配套。

- **对项目的影响和潜在意义**  
  - **推理速度提升**：bf16 解码可显著减少显存占用和计算延迟，对大 batch 或长视频处理尤为有利，可能将整体推理吞吐量提升 20%~50%（取决于硬件）。  
  - **质量无损**：声明“lossless”意味着视觉质量与 fp32 一致，打消用户对精度损失的顾虑，增强生产环境适用性。  
  - **代码规范保障**：pre-commit 问题长期不修会导致新提交格式混乱，及时修复降低了后续合并冲突风险，提高开发效率。  
  - **文档迭代**：README 是项目门面，小幅更新有助于传播最新特性和使用方式，吸引更多用户。

- **值得关注的技术点**  
  - **bf16 无损解码的实现**：通常 bf16 在梯度计算中因截断存在小幅精度损失，此处标注“lossless”可能意味着 Wan VAE 的推理对精度不敏感（如输出离散 token），或使用了动态缩放等技巧。具体可在 commit 详情中查看是否涉及量化解码器或特殊算子。  
  - **Wan VAE 的角色**：从命名推测 Wan 可能是项目自定义或集成的视频 VAE 模型（例如类似 Stable Video Diffusion 的变体），其解码性能直接影响最终生成质量与速度。

- **结合 README 背景对项目发展的影响**  
  - FastVideo 定位为“快速视频处理/生成框架”，本次提交直接兑现其性能承诺，展示从算法层（bf16适配）到工程层（代码规范、文档）的全面进步。  
  - 默认开启 bf16 解码意味着项目已假设目标硬件（如 Ampere 以上 GPU）支持该格式，推动用户采用更现代的基础设施，侧面引导生态向低精度计算迁移。  
  - weekly dev meeting 提到的路线图可能包含推理优化，本次提交回应了社区对“更高速率、更低资源”的需求，有利于提升项目口碑和贡献

## 详细提交记录

### [4f3ad3f](https://github.com/hao-ai-lab/FastVideo/commit/4f3ad3f6df9327257f08f4c45d24154b52c06616)

- **作者**: Raghav K
- **时间**: 2026-06-26T19:42:29Z
- **提交信息**: [perf] Default Wan VAE decode to bf16 (lossless, faster) (#1472)

### [b454aa5](https://github.com/hao-ai-lab/FastVideo/commit/b454aa56c32dbb63a42a04555f6b47ec00544605)

- **作者**: William Lin
- **时间**: 2026-06-26T19:39:28Z
- **提交信息**: [misc] fix pre-commit (#1500)

### [f9b8e30](https://github.com/hao-ai-lab/FastVideo/commit/f9b8e30ff33f1845b81c71958511d2c344fdba78)

- **作者**: William Lin
- **时间**: 2026-06-26T16:23:30Z
- **提交信息**: Update README.md

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33941
- **最后更新**: 2026-06-26T22:51:02Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ramkumar R, Oleksandr Porunov

## AI分析总结

根据昨日两个提交记录，以下是结合 `huggingface/diffusers` 项目背景的分析总结：

---

### 1. 主要更新类型
- **依赖升级**（功能维护）：将 `safetensors` 版本从旧版升级到 **0.8.0**。
- **文档修复**（非功能性）：修正 `EulerDiscreteScheduler.set_timesteps` 方法文档字符串中的重复单词 “schedule schedule” 为 “schedule”。

---

### 2. 关键变更点及其与项目整体方向的关系
- **safetensors 升级**：`safetensors` 是 HuggingFace 生态中用于安全、零依赖存储张量的库，广泛用于模型权重的加载与保存。升级到 0.8.0 意味着获取最新的安全修复、性能改进或与新框架（如 PyTorch 版本）的兼容性增强，这直接保障了用户加载和转换扩散模型权重的稳定性。
- **docstring 修复**：虽然只是一个拼写错误，但反映了项目对 API 文档质量的持续关注，尤其是调度器（scheduler）这一核心组件。清晰的文档有助于开发者正确使用 `set_timesteps` 方法，减少理解成本。

---

### 3. 对项目的影响和潜在意义
- **安全性/兼容性**：依赖升版本避免潜在漏洞（如缓冲区溢出或序列化攻击），并且保持与最新工具链的兼容，防止因旧版本 `safetensors` 导致模型加载失败或性能下降。
- **开发者体验**：文档修复虽小，但能减少新手用户因重复单词产生的困惑，提升 API 说明的准确性，符合 HuggingFace 对可读性和可维护性的高标准。

---

### 4. 值得关注的技术点
- **safetensors 0.8.0 的变更**：可能包含对 `mutable` 张量操作的支持、更快的序列化/反序列化、或对更多数据类型（如 `bfloat16`）的优化。这些会间接影响 `diffusers` 中模型权重的加载速度与内存占用。
- **EulerDiscreteScheduler** 的 `set_timesteps` 是去噪过程中的核心步骤，其文档正确性直接关系用户体验。

---

### 5. 对项目发展的影响（结合README背景）
- 根据 README，`diffusers` 旨在提供模块化、高效的扩散模型推理与训练，并强调 **“即装即用”** 和 **“安全高效”**。升级 `safetensors` 恰好体现了对安全性和性能的承诺，确保用户能无痛加载最新的预训练模型。
- 文档维护作为日常开发中的“小步快跑”，展现了团队对代码质量的重视，这有助于维持项目在开源社区中的信任度和低问题反馈率。
- 整体来看，昨日更新属于**基础设施维护 + 细节打磨**，没有引入重大新功能，但巩固了项目稳定性，为后续大规模的新特性开发（如新调度器、控制网（ControlNet）集成等）奠定了可靠基础。

## 详细提交记录

### [1ec68b6](https://github.com/huggingface/diffusers/commit/1ec68b68e14cf8f6956a26fc4fc3c44521b50917)

- **作者**: Oleksandr Porunov
- **时间**: 2026-06-26T22:50:54Z
- **提交信息**: feat: bump safetensors to 0.8.0 (#13971)

Signed-off-by: Oleksandr Porunov <alexandr.porunov@gmail.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [f24667d](https://github.com/huggingface/diffusers/commit/f24667dc96e729b239b2adcb6879bc69705fb6a8)

- **作者**: Ramkumar R
- **时间**: 2026-06-26T16:45:46Z
- **提交信息**: docs: fix repeated word typo in set_timesteps docstring (#13876)

* docs: fix repeated word typo in set_timesteps docstring

Removed the duplicate word "schedule" from the docstring for the sigmas argument in EulerDiscreteScheduler.set_timesteps.

* Update scheduling_euler_discrete.py

* Apply style fixes

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 419
- **最后更新**: 2026-06-26T21:01:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12636
- **最后更新**: 2026-06-26T22:26:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29683
- **最后更新**: 2026-06-26T23:20:54Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 20
- **主要提交者**: Lianmin Zheng, syy-hw, Michael

## AI分析总结

### 1. 主要更新类型

- **Bug修复**：约10项（IPv6、AMD DeepEP测试、量化、DSA cudagraph、MiniMax MSA、NPU交叉注意力等）
- **性能优化**：6项（双流MoE路由专家主线运行、IPC msgspec优化、JIT kernel迁移、扩散模型shard与fuse等）
- **功能新增**：6项（HiCache内存约束移除、GLM-5.2 B300/GB300 NVFP4配置、AMD单元测试、JoyEcho多模态、扩散因果Conv3D CUDA fast path）
- **文档更新**：3项（量化贡献指南、cookbook分辨率与量化描述）
- **重构**：2项（IPC数据结构迁移、量化代码所有者更新）
- **其他**：1项（revert之前的主线路由实验）

### 2. 关键变更点与项目方向关系

- **HiCache大主机内存约束移除** → 改善内存管理，增强大模型部署灵活性。
- **GLM-5.2 NVFP4 cookbook** → 支持Blackwell新硬件量化格式，扩展硬件生态。
- **AMD多提交（单元测试、CI、DeepEP修复）** → 强化AMD GPU支持，提升异构兼容性。
- **IPv6/分布式通信修复** → 提升disagg架构稳定性，支撑多节点部署。
- **JIT kernel迁移** → 从AOT到JIT减少编译开销，加速新模型适配。
- **双流MoE主线路由（含revert）** → 探索DeepSeek V3性能优化，但需谨慎验证。
- **扩散模型增强（JoyEcho多模态、Conv3D fast path）** → 扩展推理框架到多模态/视频生成。
- **IPC msgspec重构** → 优化分布式数据传输效率，提升大规模推理集群性能。

### 3. 对项目的影响与潜在意义

- **稳定性提升**：大量bug修复覆盖网络、内存、算子、多硬件路径，降低生产运行风险。
- **性能增益**：JIT kernel、IPC优化、扩散模型fuse等直接提升吞吐和延迟。
- **硬件扩展**：AMD、NPU、Blackwell新量化支持，吸引更多用户和合作伙伴。
- **场景扩展**：新增扩散及多模态支持，使项目从纯LLM走向多模态推理框架。
- **质量保障**：增加AMD nightly CI套件、量化文档标准化，提升开发效率。

### 4. 值得关注的技术点

- **msgspec.Struct +

## 详细提交记录

### [da0f4f6](https://github.com/sgl-project/sglang/commit/da0f4f6f9299730ec7d0b62abedc4a079d5d15a9)

- **作者**: Zhiqiang Xie
- **时间**: 2026-06-26T23:20:48Z
- **提交信息**: [HiCache] remove large host mem constraint (#28614)

Co-authored-by: Teng Ma <stmatengss@gmail.com>
Co-authored-by: Vladislav Nosivskoy <vladnosiv@gmail.com>

### [12f76d1](https://github.com/sgl-project/sglang/commit/12f76d115cd85c1456ad7e00ab752aa128e2f868)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-26T23:15:33Z
- **提交信息**: Update GLM-5.2 B300 and GB300 NVFP4 cookbook settings (#29466)

### [c470acd](https://github.com/sgl-project/sglang/commit/c470acde2be609fe77e96f6f3c0d1795ddf8f9dc)

- **作者**: Michael
- **时间**: 2026-06-26T23:06:02Z
- **提交信息**: [AMD] Register 1 kernel unit test for AMD nightly CI (#29333)

### [9c3227b](https://github.com/sgl-project/sglang/commit/9c3227b689e44270213b8a12723af35d4eb4c71e)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-26T23:05:36Z
- **提交信息**: Fix IPv6 wildcard bootstrap address resolution in disagg (#29459)

### [5eebb4b](https://github.com/sgl-project/sglang/commit/5eebb4b2e820a7b3068e89828329035d9bf8a28b)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-26T23:04:20Z
- **提交信息**: [AMD] Fix fused append+remap DeepEP equivalence test on aiter path (#29377)

### [72812db](https://github.com/sgl-project/sglang/commit/72812db138f9fefe4bfa3d3a38d8c981093ca2d8)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-06-26T22:51:15Z
- **提交信息**: Avoid dynamic Q quantization in trtllm_mha (#29423)

### [73741f7](https://github.com/sgl-project/sglang/commit/73741f707451640b386d2c42b980e360a253c43b)

- **作者**: Baizhou Zhang
- **时间**: 2026-06-26T22:24:16Z
- **提交信息**: Bypass legacy GLM DSA layer types validation (#29454)

### [267d165](https://github.com/sgl-project/sglang/commit/267d165ad0df6bac66f013439fb2b90af06a4807)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-26T21:49:39Z
- **提交信息**: shm_broadcast: retry bind on EADDRINUSE (fix dp-attention port race) (#29455)

Co-authored-by: Xingyu Liu <38244988+charlotte12l@users.noreply.github.com>
Co-authored-by: xingyuliu <xingyuliu@fb.com>

### [e745b3a](https://github.com/sgl-project/sglang/commit/e745b3af22f4abb7d213e27359e3dc09315fed56)

- **作者**: Jimmy Shong
- **时间**: 2026-06-26T21:41:18Z
- **提交信息**: [Fix] compressed-tensors block FP8: requantize weight scales to UE8M0 for DeepGEMM on Blackwell (#28662)

### [7b02eab](https://github.com/sgl-project/sglang/commit/7b02eab7a6885cc9fec99a894f190d8702e6e533)

- **作者**: Cheng Wan
- **时间**: 2026-06-26T20:59:36Z
- **提交信息**: Revert "[DeepSeek V3] Run routed experts on main stream in dual-stream MoE" (#29452)

### [ee77a7d](https://github.com/sgl-project/sglang/commit/ee77a7d3307db377682effcfe44e394edbadf0a3)

- **作者**: Jackey Hua
- **时间**: 2026-06-26T19:17:34Z
- **提交信息**: [Fix] DSA: size cudagraph page_table to req_to_token width (#29379)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [be19301](https://github.com/sgl-project/sglang/commit/be1930133a9956165dd113f6fceba7b2e1553f33)

- **作者**: Rain Jiang
- **时间**: 2026-06-26T19:04:03Z
- **提交信息**: Convert IPC dataclasses to msgspec.Struct with opt-in msgpack transport (#28688)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [714011a](https://github.com/sgl-project/sglang/commit/714011a40fc3e886a7107ea5786de47f5e856f88)

- **作者**: meinie
- **时间**: 2026-06-26T18:52:18Z
- **提交信息**: [JIT Kernel] Migrate dsv3_router_gemm from AOT sgl-kernel to JIT kernel (#21531)

Co-authored-by: Guohao Shao <shao.gh.98@gmail.com>
Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [c98d311](https://github.com/sgl-project/sglang/commit/c98d31143d7e017cac3199fe4b4e52b435a99ba8)

- **作者**: Yaochen Han
- **时间**: 2026-06-26T16:40:33Z
- **提交信息**: update quantization code owner and document quantization contributions (#26784)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [8524678](https://github.com/sgl-project/sglang/commit/8524678889485801e7a4a12d62015be0c68f7a90)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-26T15:14:31Z
- **提交信息**: Fix MiniMax MSA fallback when fmha plan is unavailable (#29250)

### [18b0e57](https://github.com/sgl-project/sglang/commit/18b0e5757e7d275d9e6695a117ee86314c70101e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-26T15:13:15Z
- **提交信息**: [Diffusion] Fuse LTX2 Ada values (#29390)

### [b913480](https://github.com/sgl-project/sglang/commit/b91348071e6ca21f9357fd8b1adc83a18781df30)

- **作者**: Aleksi Vesanto
- **时间**: 2026-06-26T13:44:45Z
- **提交信息**: [diffusion] optimize: shard qwen text embed in sp  (#29147)

### [b73e572](https://github.com/sgl-project/sglang/commit/b73e57210af12051ac64f82cc02070705dc040fd)

- **作者**: Xinyu Jiang
- **时间**: 2026-06-26T10:47:00Z
- **提交信息**: [AMD CI] Add nightly Miles ROCm 7.2 MI350X suites (#28853)

Co-authored-by: Zhiyao Jiang <jessicajiang324@gmail.com>
Co-authored-by: bingxche <bingxche@amd.com>

### [f5708c3](https://github.com/sgl-project/sglang/commit/f5708c3f91ee31886c395279fd0baec97791c688)

- **作者**: syy-hw
- **时间**: 2026-06-26T09:13:17Z
- **提交信息**: [NPU] Fix mllama cross-attention crash in ascend extend SDPA (#29374)

### [c0d4d18](https://github.com/sgl-project/sglang/commit/c0d4d1897c8228f220ac7342cde068b571d92a7a)

- **作者**: Yan Ru Pei
- **时间**: 2026-06-26T08:13:40Z
- **提交信息**: fix: batch BlockRemoved events per radix node (#29265)

### [c21c2d9](https://github.com/sgl-project/sglang/commit/c21c2d94216e66938cc25f598cee89a1ff1be53e)

- **作者**: zijiexia
- **时间**: 2026-06-26T07:56:34Z
- **提交信息**: [Docs] Cookbook: match playground docker image resolution to deployment (hw|quant) (#29400)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [999199f](https://github.com/sgl-project/sglang/commit/999199f9ff4bae422b97f20ca9c0e6a9c14f6cfc)

- **作者**: Khoa Pham
- **时间**: 2026-06-26T07:48:59Z
- **提交信息**: [DeepSeek V3] Run routed experts on main stream in dual-stream MoE (#29142)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [aeb4e98](https://github.com/sgl-project/sglang/commit/aeb4e98108ff6ef22f1b95e215a290476696da2d)

- **作者**: WenhaoZhang
- **时间**: 2026-06-26T07:46:31Z
- **提交信息**: [diffusion] model: support JoyEcho multi-shot A/V generation support (#27420)

Co-authored-by: niehen6174 <niehen6174@users.noreply.github.com>
Co-authored-by: 1639206518@qq.com <niehen6174>

### [dd56a9f](https://github.com/sgl-project/sglang/commit/dd56a9f069488c7fa254f0971af3d2333b48bab6)

- **作者**: zijiexia
- **时间**: 2026-06-26T07:40:13Z
- **提交信息**: [Docs] Add NVFP4 quantization to GLM-5.2 cookbook (#29380)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [5996b54](https://github.com/sgl-project/sglang/commit/5996b54bd3e8aca60bb417ba05f6266d1a9851a1)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-26T07:06:49Z
- **提交信息**: [KDA-Pilot] Add diffusion causal Conv3D cat-pad CUDA fast path for Cosmos3 (#29281)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1210
- **最后更新**: 2026-06-26T11:07:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据README，'cache-dit' 是一个专注于 DiTs 模型推理加速的 PyTorch 原生引擎，核心特性包括缓存、并行、量化和 CPU 卸载。昨日只有一条提交记录，总结如下：

### 1. 主要更新类型
- **文档/注释更新**：提交类型为 `chore`，仅涉及对 `svdq nvfp4 kernel` 相关代码注释的修改。

### 2. 关键变更点及与项目整体方向的关系
- **变更点**：更新了 `svdq`（推测为某种结构化向量量化方法）和 `nvfp4`（NVIDIA FP4 格式）内核的注释。
- **与项目方向的关系**：量化引擎是项目核心功能之一，支持低精度推理以节省显存和加速。`nvfp4` 是前沿的低精度格式，`svdq` 可能是其实现算法。虽然只是注释更新，但表明团队正在维护或即将完善这一量化内核，与项目“量化”特性直接相关。

### 3. 对项目的影响和潜在意义
- **直接影响**：无代码功能变化，但清晰的注释有助于开发者理解量化内核的设计逻辑，降低后续开发与维护门槛。
- **潜在意义**：
  - 为可能的后续功能增加（如正式支持 FP4 量化路径）做准备。
  - 表明项目在紧跟 NVIDIA 最新量化格式（FP4），提升对高端硬件的适配性。
  - 配合项目“PyTorch-native”特性，确保量化模块在原生框架中的可读性和可扩展性。

### 4. 值得关注的技术点
- **svdq**：可能是 Sparse-Value-Decomposition Quantization 或其变体，结合 DiT 模型特点的优化量化策略。
- **nvfp4**：NVIDIA 的 4-bit 浮点格式（E2M1 或类似），在保持一定精度的同时大幅降低带宽需求。此注释更新意味着 `cache-dit` 可能正在探索将 DiT 推理推向更极致的低比特量化。
- **内核注释规范**：提交包含两次相同描述（`chore: update svdq kernel comments`），可能与 CI 或审查流程有关，说明团队对代码注释的重视。

### 5. 这些提交如何影响项目发展
- **短期**：保持代码库整洁，为开发者提供更易理解的量化内核接口，有利于社区贡献。
- **长期**：量化是 DiT 推理落地（尤其是大模型、移动端或边缘设备）的关键瓶颈。明确标注 `nvfp4` 内核注释，暗示项目正朝着**支持多种低精度推理格式**的方向演进，这与 README 中“Quantization”目标一脉相承，可帮助项目在推理速度与显存占用上取得更优平衡，从而拓展应用场景。

## 详细提交记录

### [f24b526](https://github.com/vipshop/cache-dit/commit/f24b52684a380bf760f5aa02d208a9339451d0c1)

- **作者**: DefTruth
- **时间**: 2026-06-26T11:07:24Z
- **提交信息**: chore: update svdq nvfp4 kernel comments (#1071)

* chore: update svdq kernel comments

* chore: update svdq kernel comments

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84460
- **最后更新**: 2026-06-26T23:17:40Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 23
- **主要提交者**: Matt, Charlie Fu, qli88

## AI分析总结

根据提交记录（共26条）和README背景（“Easy, fast, and cheap LLM serving for everyone”），昨日更新要点如下：

---

### 1. 主要更新类型
- **Bug修复**（12条）：涉及FP8 MoE后端、ROCm多领域、Parser token ID传递、macOS挂起、CUDA图捕获等。
- **功能新增/改进**（7条）：新模型支持（GLM-5/DSV3.2）、混合模型FA限制解除、Voxtral音频API迁移、token offsets渲染端点等。
- **性能优化**（5条）：ROCm MoE共享专家融合、AITER MoE优化、混合模型FlashAttention块大小限制移除、GPU同步环境变量等。
- **CI/测试/维护**（8条）：AMD ROCm CI任务调整、测试清理、代码所有者更新、legacy API迁移等。
- **文档更新**（1条）：移除不支持的混合模型列表（BambaForCausalLM）。

（注：部分提交兼有多类型，统计有重叠）

---

### 2. 关键变更点及其与项目整体方向的关系
- **多硬件支持（ROCm/CPU）**：大量ROCm修复、性能优化（#46545, #46122, #46419）及CI适配，巩固AMD GPU生态；macOS/Apple Silicon挂起修复（#46769）扩大平台覆盖 → 符合“cheap”与“everyone”目标。
- **新模型集成**：添加DeepSeek V3.2/GLM-5（#46808）、Voxtral迁移至最新音频API（#46705）、混合模型FlashAttention限制取消（#36701） → 提升模型兼容性，降低用户使用门槛。
- **API与解析器增强**：Harmony Parser输出刷新（#46437）、Rust前端Harmony处理（#46799）、token IDs传递修复（#46843） → 优化服务可用性与响应准确性。
- **性能与扩展性**：ROCm MoE融合与AITER后端优化（尤其在MXFP4/MXFP8模型上）、GPU同步检查变量（#44800） → 降低推理成本、提升吞吐。
- **基础设施清理**：legacy API server移至examples（#46783）、CI缓存清理（#46831） → 简化部署，减少技术债务。

---

### 3. 对项目的影响和潜在意义
- **AMD/ROCm生态成熟度提升**：多条ROCm专用修复、性能优化及CI稳定性改进，使vLLM在AMD GPU上的表现更接近NVIDIA，有利于降低用户硬件成本，扩大服务覆盖面。
- **新模型支持加速**：DSV3.2/GLM-5的快速集成表明vLLM模型注册机制灵活，可吸引更多模型贡献者和用户。
- **服务可靠性增强**：Parser token ID传递、CUDA图捕获、transcription稳定性等修复，减少生产环境中的错误，提升SLA。
- **跨平台兼容性**：macOS/Apple Silicon挂起修复，使开发者和长尾用户也能在本地调试，降低开发门槛。
- **API演进**：token offsets渲染端点（#44226）和legacy API迁移，为重写前端/新API版本铺路，提升可维护性。

---

### 4. 值得关注的技术点
- **ROCm MoE性能优化**：共享专家融合（#46545）和AITER MoE后端（#46419）结合，针对

## 详细提交记录

### [d8eb734](https://github.com/vllm-project/vllm/commit/d8eb734d94fea27cfcc95a22f3cc2a249e0996c7)

- **作者**: Harry Mellor
- **时间**: 2026-06-26T23:16:05Z
- **提交信息**: Fix Transformers backend FP8 MoE and remove some boilerplate (#46820)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2ff76a5](https://github.com/vllm-project/vllm/commit/2ff76a5e856e385f72aa49cadc4d0a724d1f7da8)

- **作者**: Rohan Potdar
- **时间**: 2026-06-26T21:58:40Z
- **提交信息**: [ROCm][Bugfix] Pass num_kv_splits to aiter mla_reduce_v1 (#46760)

Signed-off-by: Rohan Potdar <rohanpotdar138@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [75fdcc8](https://github.com/vllm-project/vllm/commit/75fdcc82a5a5ee859e46b489f78630ab61ed40b7)

- **作者**: Yifan Qiao
- **时间**: 2026-06-26T21:48:53Z
- **提交信息**: [CI] Add @ivanium to CODEOWNERS for KV-cache/offload areas (#46873)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>

### [77f8796](https://github.com/vllm-project/vllm/commit/77f8796d164ae938072f78561aa72da14990419c)

- **作者**: yzong-rh
- **时间**: 2026-06-26T21:18:47Z
- **提交信息**: [Frontend][Gpt-oss] Use `process_eos()` to flush Harmony Parser outputs. (#46437)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [c40d307](https://github.com/vllm-project/vllm/commit/c40d307731b82a9d472001c5feff18c24797d9df)

- **作者**: Thomas Parnell
- **时间**: 2026-06-26T21:16:39Z
- **提交信息**: [Core] Remove FlashAttention block size restriction for hybrid models (#36701)

Signed-off-by: Thomas Parnell <tpa@zurich.ibm.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [65e655d](https://github.com/vllm-project/vllm/commit/65e655d2959111d508ad97515c85be0627a7b916)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-26T21:09:05Z
- **提交信息**: [GLM-5] Add DSV3.2/GLM5 to `vllm/models/` (#46808)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [6e2fb02](https://github.com/vllm-project/vllm/commit/6e2fb02fe5bcd3990c6ecd2663a5468c27d130f9)

- **作者**: Charlie Fu
- **时间**: 2026-06-26T20:41:49Z
- **提交信息**: [ROCm][CI] Fix rlhf_nccl.py on ROCm (#46851)

Signed-off-by: charlifu <charlifu@amd.com>

### [274325d](https://github.com/vllm-project/vllm/commit/274325dd43681e1131f22df6d5aad86ac50d9617)

- **作者**: Micah Williamson
- **时间**: 2026-06-26T20:38:38Z
- **提交信息**: [ROCm][CI] Remove V1 Sample + Logits from mi250 Queue (#46867)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [95e6442](https://github.com/vllm-project/vllm/commit/95e6442a6b6973f827783d162709627304cd13f2)

- **作者**: Matt
- **时间**: 2026-06-26T20:19:16Z
- **提交信息**: [Hardware][AMD][CI] Fix Kernels Quantization test timeout (#46859)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [701a23d](https://github.com/vllm-project/vllm/commit/701a23d99f405668158d1395e11c30107dd65b75)

- **作者**: Carlos Alvarado Martinez
- **时间**: 2026-06-26T20:05:04Z
- **提交信息**: [Bugfix][Model] Support tensor parallelism for DiffusionGemma (#45719) (#46177)

Signed-off-by: Carlos Alvarado <carlos-alvarado@outlook.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [dccb412](https://github.com/vllm-project/vllm/commit/dccb412e2c72a0c147166c14b25c01f045a74163)

- **作者**: Ben Browning
- **时间**: 2026-06-26T19:29:52Z
- **提交信息**: [Bugfix][Parser] Pass token IDs to parser.parse() in Responses API and batch serving (#46843)

Signed-off-by: Ben Browning <bbrownin@redhat.com>

### [c6554f3](https://github.com/vllm-project/vllm/commit/c6554f321ce4c7563290d02eec323f262fc43fef)

- **作者**: Michael Goin
- **时间**: 2026-06-26T18:32:21Z
- **提交信息**: [CPU] Fix macOS/Apple Silicon hang by enabling OpenMP in the build (#46769)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [3d3b964](https://github.com/vllm-project/vllm/commit/3d3b96488f5f7d94b1ab63919e0f1e7922a9ded6)

- **作者**: Julien Denize
- **时间**: 2026-06-26T18:06:31Z
- **提交信息**: Migrate Voxtral to mistral-common 1.11.5 audio API (#46705)

Signed-off-by: Julien Denize <40604584+juliendenize@users.noreply.github.com>

### [658b54e](https://github.com/vllm-project/vllm/commit/658b54efe419d0e53ec33a8bb7095d8c8b52c741)

- **作者**: Nick Hill
- **时间**: 2026-06-26T16:36:31Z
- **提交信息**: [ModelRunner V2] Update scheduler tests to cover MRV2 paths (#46771)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [abc7154](https://github.com/vllm-project/vllm/commit/abc71548ef029132c3316b902207f254a246d593)

- **作者**: Li, Jiang
- **时间**: 2026-06-26T15:28:49Z
- **提交信息**: [CI/Build][CPU] Add test image cache clean-up  (#46831)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [4e07ca2](https://github.com/vllm-project/vllm/commit/4e07ca2c9284ad0661a44d33e1e8a1c597c48686)

- **作者**: Nick Hill
- **时间**: 2026-06-26T15:24:33Z
- **提交信息**: [Core] Add `VLLM_GPU_SYNC_CHECK` env var (#44800)

### [e71bc6d](https://github.com/vllm-project/vllm/commit/e71bc6da85577b2057292e60e959ce44af344897)

- **作者**: Bugen Zhao
- **时间**: 2026-06-26T15:24:13Z
- **提交信息**: [Rust Frontend] Use `oss-harmony` for Harmony output processing (#46799)

### [37ce349](https://github.com/vllm-project/vllm/commit/37ce34922f7f5e58241369511130cd99c1c50bfe)

- **作者**: fxmarty-amd
- **时间**: 2026-06-26T14:21:20Z
- **提交信息**: [CI] Fix failing CUDA graph capture in Triton MOE (#46735)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [c2507fb](https://github.com/vllm-project/vllm/commit/c2507fb2937aa8c8e74bea15719d04fb6090befe)

- **作者**: Hongxia Yang
- **时间**: 2026-06-26T14:05:20Z
- **提交信息**: [ROCm] [MoE] [Perf] Shared-expert fusion for bias-routed MoE; enable on MiniMax-M3 mxfp8 model (#46545)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [8921c4b](https://github.com/vllm-project/vllm/commit/8921c4be88effbd295dd7c2410fd21411256f819)

- **作者**: TJian
- **时间**: 2026-06-26T13:43:27Z
- **提交信息**: [ROCm] [Performance] Optimize aiter moe for DeepSeekV4 (#46122)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [8e39424](https://github.com/vllm-project/vllm/commit/8e394244a59afc67a37bf47dab0ab76bf5ce5885)

- **作者**: qli88
- **时间**: 2026-06-26T13:35:35Z
- **提交信息**: [ROCm]Enable AITER MoE backend for MiniMax-M3-MXFP4 (#46419)

Signed-off-by: Qiang Li <qiang.li2@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [302954e](https://github.com/vllm-project/vllm/commit/302954e5f603b30a8fe6d4c84b7e655f0e3e74db)

- **作者**: TJian
- **时间**: 2026-06-26T13:33:35Z
- **提交信息**: [ROCm] [CI] fix transcription flakiness AMD: Entrypoints Integration (API Server OpenAI - Part 1) (mi325_1) (#46823)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [950ee4c](https://github.com/vllm-project/vllm/commit/950ee4c2e48fd462a03cebb3283ac9fdcb27b2e4)

- **作者**: Hyunkyun Moon
- **时间**: 2026-06-26T12:02:52Z
- **提交信息**: [API] Add token offsets to render endpoints (/v1/.../render) (#44226)

Signed-off-by: HyunKyun Moon <mhg5303@gmail.com>

### [d980a3c](https://github.com/vllm-project/vllm/commit/d980a3cc6ed9fc83386894211170f1ca85ac9735)

- **作者**: Micah Williamson
- **时间**: 2026-06-26T09:09:56Z
- **提交信息**: [ROCm] Fix AITER_UNIFIED_ATTN Dispatching After AITER Bump (#46780)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Signed-off-by: Rohan138 <rohanpotdar138@gmail.com>
Co-authored-by: Rohan138 <rohanpotdar138@gmail.com>

### [bf292b5](https://github.com/vllm-project/vllm/commit/bf292b5f6b537d154fc09a3b232f89cbc66827f5)

- **作者**: AgenticSpark
- **时间**: 2026-06-26T08:02:50Z
- **提交信息**: [Docs] Remove BambaForCausalLM from supported hybrid models list (#46071)

Signed-off-by: liejiang <jianglie2023@gmail.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [5e3dad0](https://github.com/vllm-project/vllm/commit/5e3dad04b10df208513d4941da9e72e6d9e77048)

- **作者**: wang.yuqi
- **时间**: 2026-06-26T07:43:29Z
- **提交信息**: [Misc] Move the legacy api_server.py to the examples directory. (#46783)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-27
**监控日期**: 2026-06-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5286
- **最后更新**: 2026-06-26T22:39:47Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: MaciejBalaNV, Hongsheng Liu, Gao Han

## AI分析总结

以下是针对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结，结合项目“易用、快速、低成本的通用多模态模型服务”的背景：

---

### 1. 主要更新类型
- **Bug 修复**（3个）：Qwen3-TTS 的 token 计数与 WebSocket 流式输入修复；回滚一次 SSRF 修复
- **文档更新**（2个）：Cosmos3 模型文档字符串补充；PR 预审技能中增加代码质量维度
- **CI/DevOps 改进**（1个）：夜间 L2/L3 端到端测试上传与 Buildkite 转义修复
- **代码回滚**（1个）：暂时撤回 MediaConnector 防 SSRF 的改动

---

### 2. 关键变更点及其与项目方向的关系
- **Qwen3-TTS 两项修复**：修正了语音合成的 token 使用量统计（`/v1/audio/speech`）和 WebSocket 输入流的分段发送问题。这直接服务于项目“即插即用多模态”目标，特别是音频/语音模态的稳定商用。
- **Cosmos3 文档更新**：Cosmos3 是 NVIDIA 的视频/3D 生成模型，文档完善表明 vllm-omni 正在扩展对视频/视觉模态的支持，贴合“omni-modality”定位。
- **SSRF 修复回滚**：原修复试图通过 `MediaConnector` 统一处理图片/视频 URL 获取以防止服务器端请求伪造，但因副作用（可能与现有连接器冲突）被紧急回滚，体现项目对稳定性的重视。
- **CI 与代码质量**：修复自动构建上传和转义问题，并在 PR 检查中引入代码质量维度，提升开发流程可靠性，间接保证多模型服务的交付质量。

---

### 3. 对项目的影响和潜在意义
- **提升语音模型可用性**：TTS 的 token 计数准确和流式输入连贯能直接改善开发者和最终用户的体验，有助于项目在音频服务场景的落地。
- **多模态模型生态扩展**：Cosmos3 文档就绪表明该模型即将或已经集成，项目向视频/3D 领域迈进一步，增强“全能模态”的竞争力。
- **安全风险暂时保留**：SSRF 防护回退意味着当前存在通过 URL 注入攻击的潜在风险，需尽快推出更稳定的替代方案。
- **基础设施稳定化**：CI 修复确保自动化测试和部署不再被转义问题阻断，减少开发卡顿。

---

### 4. 值得关注的技术点
- **Qwen3-TTS 的流式架构**：WebSocket 输入“作为单个请求”的处理方式，对于实时语音合成场景的延迟与数据完整性的平衡值得借鉴。
- **Token accounting 机制**：在 `/v1/audio/speech` 接口中准确计算使用的 token 数，涉及生成 tokens 与输入文本的映射逻辑，对计费与监控关键。
- **MediaConnector 与 SSRF 防护**：如何在不破坏

## 详细提交记录

### [47871d5](https://github.com/vllm-project/vllm-omni/commit/47871d5e203beecb194120ae3219ce05336bb234)

- **作者**: MaciejBalaNV
- **时间**: 2026-06-26T22:39:42Z
- **提交信息**: Updated Cosmos3 docstrings (#4727)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [b66cd02](https://github.com/vllm-project/vllm-omni/commit/b66cd024b9f258aa255cd028620ae8f7ce67003a)

- **作者**: Yueqian Lin
- **时间**: 2026-06-26T22:13:31Z
- **提交信息**: [Bugfix] Fix /v1/audio/speech usage token accounting for Qwen3-TTS (#4646) (#4673)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [c582805](https://github.com/vllm-project/vllm-omni/commit/c582805e7a731c885c3397c64b98a9560639e786)

- **作者**: Gao Han
- **时间**: 2026-06-26T17:18:48Z
- **提交信息**: Revert "[Bugfix] Use MediaConnector for image/video URL fetching to prevent SSRF" (#4751)

### [908e7d3](https://github.com/vllm-project/vllm-omni/commit/908e7d32d9d9212f19ca7f036bed3745944fdda2)

- **作者**: wangyu
- **时间**: 2026-06-26T15:10:19Z
- **提交信息**: [CI][Bugfix] Fix nightly L2/L3 E2E-only upload and Buildkite EXTRA escaping (#4734)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [d6f1d3d](https://github.com/vllm-project/vllm-omni/commit/d6f1d3d61ca462ff8e89312ebf0fdb675edad104)

- **作者**: Hongsheng Liu
- **时间**: 2026-06-26T12:31:10Z
- **提交信息**: [Doc] Add code-quality dimension to precheck-pr skill (#4697)

Signed-off-by: hsliu_ustc <hsliu_ustc@noreply.gitcode.com>
Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: hsliu_ustc <hsliu_ustc@noreply.gitcode.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

### [c39ac9f](https://github.com/vllm-project/vllm-omni/commit/c39ac9fffd0eb9de6e3888b65698a90744e31259)

- **作者**: Sy03
- **时间**: 2026-06-26T07:48:30Z
- **提交信息**: [Bugfix] Stream Qwen3-TTS WebSocket input as one request (#4731)

Signed-off-by: Sy03 <1370724210@qq.com>

---
