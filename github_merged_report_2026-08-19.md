# GitHub Stars 合并报告 - 2026-08-19

**合并日期**: 2026-08-20
**监控日期**: 2026-08-19
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


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2159
- **最后更新**: 2026-08-19T07:09:37Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2695
- **最后更新**: 2026-08-19T17:52:46Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Bilang ZHANG, Xin Qiu

## AI分析总结

### 1. 主要更新类型
- **功能新增**：两项提交均为新功能支持，分别引入视频超分能力和Intel XPU平台优化算子。

### 2. 关键变更点及其与项目整体方向的关系
- **swiftvr原生视频超分支持**：为LightX2V增加视频超分辨率能力，直接扩展了框架的推理功能边界，与项目“轻量视频生成推理”的核心定位一致，使用户在生成后可直接进行画质增强，形成更完整的视频处理链路。
- **MiniMax-H3 RoPE的XPU优化内核**：针对Intel XPU平台实现专用旋转位置编码（RoPE）内核，属于底层性能优化。这与项目追求“轻量高效”的目标高度契合，通过硬件适配提升特定模型（MiniMax-H3）在Intel设备上的推理效率。

### 3. 对项目的影响和潜在意义
- **功能层面**：超分支持使LightX2V从纯生成框架向“生成+后处理”一体化演进，可能吸引需要端到端视频处理方案的用户。
- **生态层面**：XPU内核的加入表明项目正积极拓展硬件兼容性，不仅限于NVIDIA GPU，有助于覆盖Intel数据中心和边缘设备用户，扩大潜在部署场景。
- **工程层面**：新增的SYCL内核打包流程和测试体系，为后续更多XPU算子移植提供了可复用的工程范式，降低未来适配成本。

### 4. 值得关注的技术点
- **SYCL内核与PyTorch回退机制**：设计上采用“原生内核优先，不支持输入自动回退”的策略，兼顾性能与兼容性，是异构计算中常见的稳健设计模式。
- **XPU_TARGET构建参数**：支持针对不同Intel微架构（如BMG、Panther Lake）定制编译，体现对硬件差异化的精细优化思路。
- **算子注册方式**：将`minimax_h3_xpu_rope`注册为平台级算子，并通过配置开关启用，保持了框架的模块化和可扩展性。

### 5. 基于README背景，这些提交如何影响项目发展
- **强化“轻量”定位**：XPU优化内核直接降低特定模型在Intel平台的计算开销，符合“Light”命名所强调的效率优先理念，有助于在非旗舰硬件上实现流畅推理。
- **拓宽应用场景**：视频超分功能的加入，使框架能覆盖从低分辨率生成到高清输出的完整工作流，可能吸引视频修复、增强等实际业务需求，提升项目在工业界的实用性。
- **增强平台竞争力**：通过主动适配Intel XPU，项目在硬件中立性上迈出一步，避免过度依赖单一GPU生态，为未来在更多国产或异构硬件上运行奠定基础，也符合开源项目追求广泛兼容性的长期趋势。

总体而言，这两项提交分别从功能丰富度和底层性能两个维度推进了LightX2V的发展，既满足了用户对视频质量提升的直接需求，又为框架在更广泛硬件环境中的高效运行铺平了道路，体现了项目在“轻量高效”与“生态扩展”之间的平衡发展策略。

## 详细提交记录

### [26dff2e](https://github.com/ModelTC/LightX2V/commit/26dff2ec1cea3484214fe7729063b491bea980ec)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-19T11:02:58Z
- **提交信息**: swiftvr: add native video super-resolution support (#1400)

### [6f31c17](https://github.com/ModelTC/LightX2V/commit/6f31c17e92004076013724324ced65dddc95166e)

- **作者**: Xin Qiu
- **时间**: 2026-08-19T07:23:39Z
- **提交信息**: feat(xpu): add optimized MiniMax-H3 RoPE kernel (#1395)

## Summary

Add an optimized Intel XPU implementation of MiniMax-H3 partial
split-half RoPE.

  ## Changes

  - Add a native SYCL MiniMax-H3 RoPE kernel
  - Add PyTorch fallback for unsupported inputs
  - Register `minimax_h3_xpu_rope` as an Intel XPU platform operator
  - Package the kernel in the `sycl_kernels` wheel
  - Add kernel correctness tests
  - Improve XPU wheel build reproducibility

  ## Usage

  Build and install the XPU kernels:

  ```bash
  cd lightx2v_kernel_xpu
  XPU_TARGET=bmg ./build.sh
  pip install dist/sycl_kernels-*.whl --force-reinstall --no-deps
  ```
  Use XPU_TARGET=ptl-h for Panther Lake.

  Enable the operator in the MiniMax-H3 config:
  ```
  {
    "rope_type": "minimax_h3_xpu_rope"
  }
  ```
The native kernel is used for compatible BF16 inputs; unsupported inputs
automatically fall back to PyTorch.

  ## Testing

  - Added native and cached-frequency correctness tests
  - Verified the PyTorch fallback against the reference implementation
  - Passed syntax and Ruff checks

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2199
- **最后更新**: 2026-08-19T15:24:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6194
- **最后更新**: 2026-08-19T22:19:27Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Alex Yang, Gabriel Wu, hsr1234563

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本批提交包含**功能新增**、**Bug修复**和**兼容性维护**三类变更，无文档更新或纯重构。

## 2. 关键变更点

- **Bug修复（核心）**：修复SM12x MoE内核因`_collapse_to_vmk`方法被错误绑定为实例方法而导致的编译失败。该问题源于#4479引入的代码改动，影响了NVFP4 MoE路径在Blackwell架构上的可用性。
- **功能新增**：为PrimTS注意力机制新增Q64×KV256物理执行配置，支持块稀疏MHA/GQA/MQA，覆盖连续和分页K/V存储模式，并提供可复用包装API和一次性调用入口。
- **兼容性维护**：为`bsa_attn_fwd`和`bsa_attn_blk64_fwd`添加向后兼容的弃用别名，修复因#4259重命名导致的导入失败问题。
- **流程维护**：添加代码审查负责人。

## 3. 与项目方向的关系

FlashInfer定位为**高性能GPU推理内核库**，本批提交紧密围绕这一核心：

- MoE修复直接保障了Blackwell平台（SM120）上融合MoE推理的可用性，对vLLM等下游框架的NVFP4 MoE后端至关重要。
- PrimTS扩展进一步强化了Blackwell架构上的稀疏注意力能力，与项目“为最新GPU架构提供极致推理性能”的目标一致。
- 兼容性别名维护了API稳定性，降低用户升级成本，有利于生态建设。

## 4. 对项目的影响

- **可用性提升**：修复使`main`分支重新支持SM12x融合MoE，恢复Qwen3.5-397B等大模型在RTX PRO 6000上的推理能力。
- **性能优化**：Q64×KV256配置在B200上相比KV128实现最高**2.11倍**加速，显著提升长序列稀疏注意力性能。
- **生态友好**：兼容性别名避免破坏性变更，保护现有用户代码。

## 5. 值得关注的技术点

- **借用模式脆弱性**：MoE内核以未绑定方式调用`DenseGemmKernel`的方法，暴露了类间耦合风险。修复方案将纯函数移至模块级，增强了代码健壮性。
- **AST扫描测试**：新增的回归测试通过源码扫描验证借用契约，无需导入内核模块即可运行，设计巧妙。
- **物理瓦片与语义块解耦**：PrimTS的Q64/KV256是物理执行尺寸，与BSR块大小和页大小独立，体现了灵活的分层设计。
- **性能数据详实**：提交包含完整的基准测试数据，便于验证优化效果。

## 6. 对项目发展的意义

本批提交体现了FlashInfer**“性能优先、架构适配、生态稳定”**的发展策略：通过持续优化Blackwell架构支持保持技术领先，通过API兼容性维护降低用户迁移成本，通过系统性测试保障代码质量。这些变更巩固了FlashInfer作为高性能推理内核库的地位，为AI推理框架提供了更强大的底层支撑。

## 详细提交记录

### [b2d0236](https://github.com/flashinfer-ai/flashinfer/commit/b2d02361301f97becfb40672abd87ba5a4a361ea)

- **作者**: Alex Yang
- **时间**: 2026-08-19T21:02:23Z
- **提交信息**: Add @Anerudhan to CODEOWNERS for core review (#4622)

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

### [3f0a5ee](https://github.com/flashinfer-ai/flashinfer/commit/3f0a5eef47a4f757c2704e68f7d5e80de72d1ef5)

- **作者**: Gabriel Wu
- **时间**: 2026-08-19T17:19:11Z
- **提交信息**: fix(moe): restore SM12x MoE kernels broken by self-resolved helper in borrowed dense methods (#4602)

# fix(moe): restore SM12x MoE kernels broken by self-resolved helper in
borrowed dense methods

## Summary

#4479 (MXFP4 dense GEMM on SM120) added the `_collapse_to_vmk`
staticmethod to
`DenseGemmKernel` and called it as `self._collapse_to_vmk(...)` inside
`_partition_fragment_SFA` / `_partition_fragment_SFB`. Those two methods
are
also invoked **unbound** by the SM12x MoE kernels
(`MoEStaticKernel`, `MoEMicroKernel`, `MoEDynamicKernel`,
`MoEGatedDynamicKernel`), which pass their own instance as `self`:

```python
tCrSFA = self._dense_cls._partition_fragment_SFA(self, ...)
```

Since none of the MoE kernel classes define `_collapse_to_vmk`, every
NVFP4
SM12x MoE path now fails at kernel compile time:

```
AttributeError: 'MoEGatedDynamicKernel' object has no attribute '_collapse_to_vmk'
```

This makes `main` unusable for SM12x fused MoE (e.g. vLLM's
`flashinfer_b12x` NVFP4 MoE backend serving Qwen3.5-397B-A17B-NVFP4 on
4x RTX PRO 6000 Blackwell).

## Fix

Move `_collapse_to_vmk` to a module-level function in
`dense_blockscaled_gemm_sm120_b12x.py` (next to the existing
module-level
helpers) and call it directly instead of via `self.`. The helper is pure
—
it never touches instance state — so nothing needs to live on the class,
and
borrowers become immune to this class of change for this helper.

Net diff: one method moved, two call sites updated. No behavior change.

## Regression test

Adds a CPU-only borrow-contract test section in
`tests/moe/test_b12x_fused_moe.py`
(pure source scanning via AST; imports no kernel module, so it collects
and
runs even where the CuTe DSL stack is unavailable) that enforces
the structural contract the borrowing pattern relies on:

- discovers borrower classes by scanning the `fused_moe` sources for
`self._dense_cls.<method>(self, ...)` call sites — new kernels are
covered
  without editing the test;
- computes the transitive set of `self.<attr>` reads inside each
borrowed
`DenseGemmKernel` method and asserts the borrowing class provides every
one;
- fails with an actionable message, e.g.
`MoEStaticKernel borrows DenseGemmKernel._partition_fragment_SFA() but
does
not provide ['_collapse_to_vmk']; make the helper a module-level
function or
  add it to MoEStaticKernel.`

Discovery is guarded by a non-empty assertion, so renaming `_dense_cls`
or
changing the borrow idiom fails loudly instead of silently skipping the
parametrized test. Verified in both directions: the test passes on this
PR
and fails on all four borrowers when the `self._collapse_to_vmk` call is
temporarily reintroduced.

## Testing

- New contract test: 4/4 pass (MoEStaticKernel, MoEMicroKernel,
MoEDynamicKernel, MoEGatedDynamicKernel); auto-discovery verified by
adding
a temporary borrowing class, which was collected and failed as expected.
- End-to-end: vLLM `flashinfer_b12x` serving Qwen3.5-397B-A17B-NVFP4 on
  4x RTX PRO 6000 (SM120, CUDA 13) now starts, captures CUDA graphs
(FULL_AND_PIECEWISE), and completes a full C1/C4/C16/C64 serving
benchmark
  (8K/1K, 850 requests total) with zero errors.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of partitioned scale-factor tensors for dense matrix
operations, including MXF4 formats.
* Updated scale-factor processing to provide more consistent fragment
partitioning.

* **Tests**
* Added validation to ensure fused mixture-of-experts components
correctly inherit required dense matrix operation behavior and
dependencies.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [05e5d92](https://github.com/flashinfer-ai/flashinfer/commit/05e5d927399d62a2479c430ad3e167738254d760)

- **作者**: hsr1234563
- **时间**: 2026-08-19T13:14:59Z
- **提交信息**: add backward-compatible aliases for bsa_attn_fwd and bsa_attn_blk64_fwd (#4590)

bsa_attn_fwd and bsa_attn_blk64_fwd were public APIs in v0.6.16/v0.6.17
that were renamed to bsa_attn_sm100_blk128_fwd and
bsa_attn_sm100_blk64_fwd in PR #4259 without backward-compatible
aliases, causing import failures.

Add deprecated shims to restore compatibility:
- bsa_attn_fwd -> bsa_attn_sm100_blk128_fwd (bsa_attn_sm100_blk128.py)
- bsa_attn_blk64_fwd -> bsa_attn_sm100_blk64_fwd
(bsa_attn_sm100_blk64.py)

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

* **Deprecations**
* Added deprecated compatibility aliases for the 128-block and 64-block
sparse attention forward operations.
* Calls through these aliases continue to work but now emit deprecation
warnings.
  * Aliases are available through the sparse attention package exports.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: root <root@umb-b200-250.ipp8c2.colossus.nvidia.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: root <root@umb-b200-041.ipp4a1.colossus.nvidia.com>

### [0daec0a](https://github.com/flashinfer-ai/flashinfer/commit/0daec0a52baa8353cf07560e6b10761115ec8948)

- **作者**: Yuhang He
- **时间**: 2026-08-19T11:51:38Z
- **提交信息**: feat(attention): add PrimTS Q64/KV256 and paged GQA block-sparse attention (#4474)

## Summary

This PR extends PrimTS attention on NVIDIA Blackwell with:

- a physical **Q64 x KV256** execution profile for dense paged-KV
decode;
- block-sparse **MHA, GQA, and MQA** with contiguous or paged K/V
storage;
- per-request K/V lengths and optional logical-token masks; and
- reusable wrapper APIs plus one-shot contiguous and paged entry points.

Paged and contiguous K/V share the same PrimTS block-sparse workflow.

`Q64` and `KV256` are physical execution tile sizes. They are
independent of
the semantic BSR block size and the physical page size.

## Public APIs

| K/V storage | Reusable API | One-shot API |
| --- | --- | --- |
| Contiguous BSHD | `BlockSparseTSWrapper` | `block_sparse_attention` |
| Paged HND | `BlockSparsePagedTSWrapper` |
`block_sparse_attention_with_paged_kv_cache` |

The paged path accepts combined or separate K/V caches, fixed or
per-request
K/V lengths, and live page IDs. Both storage modes support dense or
bottom-right causal masking and an optional per-request `uint32` token
bitset.

## Performance

Measurements below use an NVIDIA B200 and exclude planning and JIT.

### Dense Q64 x KV256

For BF16 paged-KV attention with B1/D128, the fixed physical Q64/KV256
profile was faster than Q64/KV128 on **12/12 workloads**. Across the 10
rows
with the same direct execution mode, the geometric-mean speedup was
**1.276x**.

| Heads | Sq / Skv | Q64/KV128 | Q64/KV256 direct | Direct speedup |
Selected KV256 mode |
| --- | ---: | ---: | ---: | ---: | ---: |
| MHA 32/32 | 64 / 8192 | 52.27 us | 38.24 us | **1.37x** | 28.38 us
(**1.84x**) |
| GQA 64/8 | 64 / 8192 | 50.97 us | 33.99 us | **1.50x** | 24.15 us
(**2.11x**) |

The direct comparison isolates the physical KV256 tile improvement; the
last
column also includes its selected execution mode. This compares the
physical
profiles directly and does not imply automatic selection for every
shape.

### Block-sparse vs FlashInfer FA2

For B1/H32/D128 BF16 self-attention at S=16K and 12.5% block density,
PrimTS
outperformed FlashInfer's public `BlockSparseAttentionWrapper` with the
FA2
backend in all four representative cases:

| Semantic block | Mask | PrimTS (us) | FlashInfer FA2 (us) | FI /
PrimTS |
| ---: | --- | ---: | ---: | ---: |
| 16 | none | 2,536.93 | 3,128.37 | **1.23x** |
| 16 | 75% token keep | 2,617.92 | 5,435.38 | **2.08x** |
| 64 | none | 590.37 | 1,761.71 | **2.98x** |
| 64 | 75% token keep | 696.94 | 2,974.22 | **4.27x** |

Both paths use the same Q/K/V tensors, logical BSR pattern, and
visible-token
set. PrimTS timing includes runtime route preparation; FlashInfer's
element-mask
construction occurs before planning and is not timed.

### VSA-style fine-adapter workloads

PrimTS also outperformed the pinned FlashInfer VSA fine-attention path
across
short, long, and Wan-style compact workloads:

| Workload | PrimTS | FlashInfer VSA | FI / PrimTS |
| --- | ---: | ---: | ---: |
| S=1K, H32, top-k=2 | 109.41 us | 151.98 us | **1.39x** |
| S=16K, H32, top-k=32 | 671.81 us | 2,030.02 us | **3.02x** |
| Wan compact, H10, valid=75,600, padded=92,160, top-k=144 | 5.244 ms |
6.833 ms | **1.30x** |

These are adapter-level measurements: each adapter path includes its own
route
or staging work, while planning and JIT are excluded.

### Paged block-sparse K/V

Paged addressing adds **12-17%** over the equivalent contiguous
block-sparse
path in the measured workloads. The timed region includes route
preparation
and FMHA; all rows passed eager and CUDA Graph checks against an FP32
reference.

| Workload | Page | Contiguous (us) | Paged (us) | Overhead |
| --- | ---: | ---: | ---: | ---: |
| MQA, Q32/KV128 | 64 | 12.32 | 14.37 | +16.6% |
| GQA, Q128/KV128 | 128 | 16.46 | 18.50 | +12.4% |
| GQA, Q64/KV256 | 64 | 12.36 | 14.41 | +16.6% |
| GQA, Q64/KV256, variable K + token bits (diagnostic) | 64 | 14.41 |
16.46 | +14.2% |

The variable-K row is diagnostic: paged storage uses compact per-request
capacity while contiguous storage retains the maximum-K capacity.

## Validation

- Host tests: **283 passed, 1 skipped**.
- Trace tests: **660 passed**.
- Final B200 block-sparse shard: **50 passed**.
- Full candidate accuracy gate: **407 passed**.
- A 542-row dense FMHA, MLA, and context comparison against clean `main`
  found no confirmed regression above 5%.

## Current constraints

- Performance qualification targets B200/SM100a.
- Block-sparse attention currently requires head dimension 128 and
matching
  FP16 or BF16 Q/K/V/O dtypes.
- `Hq / Hkv` must be a power of two no greater than 32.
- Semantic Q/KV block sizes may be 8, 16, 32, or a positive multiple of
64.
- Paged block-sparse supports page sizes 16, 32, 64, and 128, subject to
the
  documented page/block-size compatibility rules.
- The API returns O only; LSE and split-KV reduction are not exposed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added experimental block-sparse attention for contiguous and paged
key/value caches.
* Added reusable planning and execution wrappers, optional masking,
scaling, validity bits, and output buffers.
* Added tracing support for block-sparse attention, including tuple and
combined paged-cache formats.
* Added support for larger 256-token decode tiles in eligible
configurations.

* **Documentation**
* Documented block-sparse attention APIs, planning behavior, paging,
routing, and validation semantics.

* **Tests**
* Added comprehensive coverage for correctness, masking, metadata
validation, CUDA graphs, stream usage, tracing, and decode
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3951
- **最后更新**: 2026-08-19T20:47:34Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Hyunsung Lee, Aryan Kumar

## AI分析总结

### 主要更新类型
本次提交包含**文档更新**和**性能优化**两类变更，无Bug修复或重构。

### 关键变更点与项目方向
1. **FastMetal-QAD 公告文档**：新增关于 FastMetal-QAD 的文档，用于介绍该功能或模型。FastMetal 系列与 FastVideo 的高效视频生成目标一致，可能涉及金属（Metal）后端优化或特定量化/蒸馏技术（QAD），强化了项目在跨平台性能和模型压缩方面的布局。
2. **FA4 CuTe 反向支持**：为 VSA-256 架构添加 FA4（FlashAttention-4）的 CuTe 反向传播支持。CuTe 是 NVIDIA 的线性代数模板库，用于高性能算子开发。此改动直接提升 VSA-256 在训练/微调时的反向传播效率，属于底层算子优化。

### 对项目的影响与意义
- **性能优化**：FA4 反向支持可显著加速 VSA-256 的训练速度，降低显存占用，使大规模视频模型训练更可行，直接服务于 FastVideo 的高效训练目标。
- **生态扩展**：FastMetal-QAD 文档表明项目正拓展到非 CUDA 平台（如 Apple Metal），或引入新的量化/蒸馏方法，有助于吸引更广泛用户群，提升跨平台可用性。

### 值得关注的技术点
- **CuTe 模板库应用**：使用 CuTe 而非传统 CUDA 内核，表明项目在算子层面采用更现代、可维护的抽象，利于后续扩展新架构。
- **FA4 反向传播**：FlashAttention 的反向支持是训练优化的关键，此改动可能涉及内存布局和调度策略的精细调整，对长序列视频训练尤为重要。

### 对项目发展的影响
结合 README 中 FastVideo 强调的“快速训练/推理”和“高效视频生成”，这两项提交分别从**文档宣传**和**底层性能**两个维度推进项目：
- 文档更新扩大了项目影响力，吸引潜在贡献者和用户；
- 性能优化则直接提升核心训练效率，为更大规模、更复杂视频模型的研究铺路。

整体上，提交体现了项目在**性能极致优化**和**生态多元化**上的持续投入，符合 FastVideo 作为高效视频生成工具的发展愿景。

## 详细提交记录

### [86d639c](https://github.com/hao-ai-lab/FastVideo/commit/86d639c848e8e71a85d9e02b453fcff433875b1c)

- **作者**: Aryan Kumar
- **时间**: 2026-08-19T20:45:49Z
- **提交信息**: [docs] Announce FastMetal-QAD (#1721)

### [00338aa](https://github.com/hao-ai-lab/FastVideo/commit/00338aa9ca9161fc2e080d482bbac5836ebbfe0e)

- **作者**: Hyunsung Lee
- **时间**: 2026-08-19T18:46:49Z
- **提交信息**: [perf] Add FA4 CuTe backward support for VSA-256 (#1639)

Co-authored-by: Hyunsung Lee <hyunsungl@sizigistudios.com>
Co-authored-by: alexzms <3036648523@qq.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34343
- **最后更新**: 2026-08-19T20:14:27Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Dhruv Nair, Atharva Joshi, Jingya HUANG

## AI分析总结

# 提交分析总结

## 主要更新类型

本次提交包含**功能新增**（张量并行支持）、**Bug修复**（图像预处理、CI认证）、**文档修正**（docstring拼写错误）以及**模型兼容性扩展**（SkyReelsV2/ChronoEdit单文件加载）。

## 关键变更点与项目方向

1. **张量并行支持（核心变更）**：为CUDA和Neuron后端引入模型推理的张量并行能力，覆盖Flux2、Wan、PixArt等主流模型，并重写Flux的SwiGLU激活以避免Neuron IR中的gather操作。这与diffusers作为多后端推理框架的定位高度契合，显著提升大规模模型部署效率。

2. **Cosmos3图像预处理修复**：保留条件图像的宽高比，解决生成质量受图像拉伸影响的问题，属于对特定模型管线的精细化打磨。

3. **多GPU VAE修复**：修复Cosmos3在`device_map="balanced"`分片部署下的跨设备RuntimeError，将归一化缓冲区固定到编码输出设备，提升分布式推理稳定性。

4. **SkyReelsV2/ChronoEdit兼容**：复用WanTransformer3DModel的转换逻辑，支持从单文件加载，增强社区GGUF构建的可用性。

5. **CI认证修复**：解决fork PR的认证问题，优化开源协作流程。

## 项目影响与潜在意义

张量并行支持是本次提交的战略性升级，使diffusers能够应对超大规模模型的单机多卡推理需求，直接提升其在生产环境中的竞争力。多GPU VAE修复和图像预处理优化则体现了项目对分布式部署和生成质量的持续关注。

## 值得关注的技术点

- **Neuron后端适配**：针对AWS Neuron硬件重写激活函数，展示了对特定硬件架构的深度优化能力。
- **设备感知的缓冲区管理**：VAE归一化缓冲区的设备绑定策略，是分布式推理中常见的隐性bug来源，此修复具有通用参考价值。

## 对项目发展的影响

结合README背景，diffusers致力于成为统一、易用的扩散模型工具库。本次提交通过张量并行支持拓展了其在高性能计算场景的适用性，同时通过模型兼容性扩展和CI优化，强化了社区驱动、多硬件支持的项目理念。这些变更推动diffusers从研究工具向生产级推理平台演进，为后续支持更大规模模型和更复杂部署场景奠定基础。

## 详细提交记录

### [4e0466f](https://github.com/huggingface/diffusers/commit/4e0466f3e5260f0d78b5e2b68ffbf27d819cc6db)

- **作者**: Atharva Joshi
- **时间**: 2026-08-19T18:43:50Z
- **提交信息**: fix: image preprocessing for cosmos3 (#14519)

fix: preserve Cosmos3 conditioning image aspect ratio

### [ac56fa2](https://github.com/huggingface/diffusers/commit/ac56fa2f25c1c15b4cbaa1e0b3255e9bc38c06dc)

- **作者**: Dhruv Nair
- **时间**: 2026-08-19T12:11:04Z
- **提交信息**: [CI] Fix authentication on forked PRs (#14534)

fix auth for forked PRs

### [7d2e86a](https://github.com/huggingface/diffusers/commit/7d2e86a85a372df75ee2ccefe84e5a44cfc60429)

- **作者**: Jingya HUANG
- **时间**: 2026-08-19T10:50:59Z
- **提交信息**: [core] Support tensor parallelism for model inference (CUDA, Neuron) (#13718)

* draft:add neuron as a legit backend

* feat: neuron-specific changes in the pipeline

* tests: eager tests

* draft: start with tp for flux2

* fix: style

* fix:apr_02 beta

* feat:add wan

* fix:pixart

* fix: rewrite flux swiglu activation to avoid gather op in neuron IR

* test: pixart compile mode on neuron

* cleanup & fix style

* merge: another change

* review: cleanup+suggestions

* fix: CIs style

* tests: add test units for tp

* fix: in case of text-encoder(s) on CPU

* review:cleanup+add test

* fix: style

* doc: remove it for now

* Add from_single_file support for SkyReelsV2 and ChronoEdit transformers (#13946)

SkyReels-V2 and ChronoEdit are both built on Wan, and their transformers have
the same keys as WanTransformer3DModel, so they reuse
convert_wan_transformer_to_diffusers (like WanVACE / WanAnimate). This lets the
community GGUF builds load directly.

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

* multi-GPU VAE Fix for Cosmos 3 (#13924)

fix(cosmos3): pin VAE latent norm buffers to encode output device

Under sharded placement (device_map="balanced"), vae.encode() runs on the
VAE's own device while the mean/inv_std buffers were pinned to x.device,
causing a cross-device RuntimeError. Compute raw_mu first, then pin the
normalization buffers to its device so all tensors share one device.

Co-authored-by: Atharva Joshi <atjoshi@smc521ge-0036.ipp2a2.colossus.nvidia.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* docs: fix repeated word typo in set_timesteps docstring (#13876)

* docs: fix repeated word typo in set_timesteps docstring

Removed the duplicate word "schedule" from the docstring for the sigmas argument in EulerDiscreteScheduler.set_timesteps.

* Update scheduling_euler_discrete.py

* Apply style fixes

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

* clean some stuff to simplify code.

* clean more to remove permutation related shenanigans.

* revert: put torch.chunk back

* Update docs/source/en/training/distributed_inference.md

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* Address Sayak's TP review nits (docstrings + stale comments)

- _modeling_parallel: fix stale comment claiming attention processors read
  tp_degree at runtime (no longer true after the PackedColwise/Rowwise
  refactor; processors are TP-agnostic via head_dim).
- tensor_parallel: single backticks instead of double in docstrings, add
  input/output examples to _blocks_to_block_sizes and _resolve_tp_plan, and
  drop the stale "applies the Flux2 fused-weight permutations" line from
  apply_tensor_parallel (permuters were removed).

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Fix stale permuter reference in Flux2ParallelSelfAttnProcessor comment

The proportional QKV/MLP slice is now guaranteed by PackedColwiseParallel
block-by-block sharding, not the removed fused-weight permuter.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Derive TP backend inside apply_tensor_parallel from the mesh device type

Drops the `backend` parameter: apply_tensor_parallel already holds the TP
mesh, so it derives neuron-vs-default from `config._mesh.device_type` itself.
The caller no longer computes it. Documents why torch_device can't be used
(Neuron reports as "cpu" via torch's accelerator API). Removes the now-unused
is_torch_neuronx_available import from modeling_utils.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Simplify TP backend derivation to the mesh device type alone

Drop the redundant is_torch_neuronx_available() guard: a DeviceMesh("neuron", ...)
only exists when running on Neuron, so tp_mesh.device_type is the single source
of truth.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Remove incorrect "Neuron reports as cpu" rationale from TP backend docstring

Verified on the current native torch_neuronx drop that Neuron does surface as
the torch accelerator (torch._C._get_accelerator().type == "neuron",
get_device() == "neuron"); the old "reports as cpu" claim was stale. The
mesh-device-type derivation is unchanged — it's the device being sharded onto.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Drop stale "XLA" labels from Neuron device/runtime comments

Neuron is a native torch backend now (not XLA-routed): remove the "(XLA)"
parenthetical from the randn-on-CPU note in torch_utils and the "XLA runtime"
mention from the Neuron TP test docstring. Behavior unchanged.

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* make style: reflow tensor_parallel docstrings

Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

* Revert "revert: put torch.chunk back"

This reverts commit 7ea75f771aee1c16d5a5668343a92ea2717fb84a.

* fix: sharding for neuron + validate flux 1

* fix: change for check_repository_consistency

* feat: support qwen image as well

* Update docs/source/en/training/distributed_inference.md

Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

* review: keep bria and nucleusmoe out

* review: keep bria and nucleusmoe out

* review: keep bria and nucleusmoe out

* review: address agent review

* review: apply suggestions

* Update docs/source/en/training/distributed_inference.md

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

* review: change example tp size to 4

* review: add flux tp test

* review: address comments

* review: improve the doc

* review:apply qwen rotary_emb per device

* review:remove redundant device def after PR #14383

* review: doc title suggestion

* review: restore copy comment

* review: remove cp divisibility explanation from doc on parallelism guide

* fix style

---------

Co-authored-by: Hz_Zhang <47402297+HaozheZhang6@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Atharva Joshi <atjoshi@nvidia.com>
Co-authored-by: Atharva Joshi <atjoshi@smc521ge-0036.ipp2a2.colossus.nvidia.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: Ramkumar R <ramkumarashvanth09@gmail.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Steven Liu <59462357+stevhliu@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
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


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12970
- **最后更新**: 2026-08-19T15:21:09Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Jinyan Ye

## AI分析总结

### 主要更新类型
- **功能新增**：为日志系统新增 CSV 格式支持，并统一了日志选项配置。

### 关键变更点及与项目方向的关系
- 新增 CSV logger，允许将训练/推理过程中的日志数据以结构化表格形式导出，便于后续数据分析与可视化。
- 统一 logger 选项，简化了不同日志后端（如终端、文件、CSV）的配置方式，降低了用户使用门槛。
- 该变更与 DiffSynth-Studio 作为一站式图像/视频合成工具链的定位一致——项目强调易用性与可复现性，结构化日志有助于用户追踪实验过程、对比不同参数效果。

### 对项目的影响和潜在意义
- **提升可观测性**：CSV 日志为长时间训练任务提供了更友好的监控手段，用户可借助 Excel、pandas 等工具快速分析损失曲线、指标变化。
- **降低使用复杂度**：统一 logger 选项减少了配置碎片化，新用户更容易上手，老用户迁移成本低。
- **为后续功能铺路**：结构化日志是自动化调参、超参数搜索、实验管理等功能的基础，该提交为项目未来集成更高级的 MLOps 能力打下基础。

### 值得关注的技术点
- 使用 Python 标准库 `csv` 实现，无额外依赖，保持了项目轻量特性。
- 通过统一 logger 接口，实现了对不同输出格式的抽象，体现了良好的设计模式（策略模式），便于未来扩展 JSON、TensorBoard 等新格式。

### 对项目发展的影响
- 结合 README 中项目强调的“开箱即用”和“高效合成”目标，该提交进一步强化了工具的实用性——用户不仅能快速生成结果，还能清晰记录和复盘过程。
- 从社区角度看，CSV 日志降低了参与贡献的门槛，外部开发者更容易理解实验数据，从而促进协作与二次开发。
- 整体上，这是一次小而精的工程优化，虽不改变核心算法，但显著提升了用户体验和项目生态的健壮性，符合 DiffSynth-Studio 从“能用”向“好用”演进的趋势。

## 详细提交记录

### [e23b5bb](https://github.com/modelscope/DiffSynth-Studio/commit/e23b5bbde43dcb437e8c601fb83b7f81b2cfa93a)

- **作者**: Jinyan Ye
- **时间**: 2026-08-19T10:17:35Z
- **提交信息**: feat(logger): add CSV logger and unify logger options (#1618)

* feat(logger): add CSV logger and unify logger options

* fix: import csv

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32119
- **最后更新**: 2026-08-19T22:29:42Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 28
- **主要提交者**: karverma-amd, Zhiqiang Xie, jacky.cheng

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次共37个提交，涵盖功能新增、Bug修复、性能优化、文档更新和重构等多个方面。其中Bug修复占比最高（约40%），功能新增约30%，性能优化约20%，文档和CI调整约10%。

## 二、关键变更点与项目方向

**模型支持扩展**：新增Qwen3.8-27B、Intern-S2-Mobius FP8、Kimi-K3 ModelOpt混合NVFP4/FP8检查点支持，并修复Gemma4 MTP桥接投影量化问题，持续扩大模型生态覆盖。

**MoE通信架构演进**：DeepEPv2（ElasticBuffer）MoE A2A后端经历了提交和回退的反复，最终重新合并，表明项目在MoE通信优化上采取谨慎迭代策略。同时为AMD平台DeepSeek-V4优化了batched GEMM和FP8缩放重排，体现硬件适配深度。

**HiCache分层缓存系统**：多个提交围绕HiCache展开，包括缓冲模式风格调整、跨rank主机内存预算拆分、DCP与DSpark支持，显示项目正系统化构建分层KV缓存体系。

**预填充-解码分离（PD）架构**：新增NIXL后端延迟解码侧KV释放、预填充DP-rank启动查询重叠，以及可配置解码间隔，持续优化PD架构的调度效率和资源利用率。

**Diffusion模型支持**：修复量化VAE组件路由、多组分层卸载启动内存、Cosmos3-Nano分组KV问题，并新增fused-kernels文档页，表明Diffusion推理正在成为重要方向。

**安全与稳定性**：拒绝grammar规范中的NUL字节以防止xgrammar段错误，修复Nemotron-H Mamba在DP注意力下的非法内存访问，修复min-new-token的EOS处理逻辑。

## 三、对项目的影响与意义

这些提交显著增强了SGLang的多模型、多硬件、多场景适配能力。AMD平台优化（MI355X、DeepSeek-V4）和DCP支持表明项目正积极拓展非NVIDIA生态。HiCache和PD架构的持续演进将提升长上下文和分布式推理场景的性能表现。

## 四、值得关注的技术点

1. **DeepEPv2回退再合并**：反映项目对重大架构变更的审慎态度
2. **NIXL后端KV释放优化**：直接降低PD架构内存峰值
3. **可配置解码间隔**：为预填充后解码调度提供细粒度控制
4. **TP LMHead优化文档**：补充了张量并行下LM Head的优化指南
5. **UnifiedTree运行时attach/detach**：增强动态图结构灵活性

## 五、对项目发展的影响

结合README中SGLang作为高性能LLM推理框架的定位，这些提交体现了三个发展方向：**生态广度**（更多模型和硬件支持）、**架构深度**（PD、HiCache、MoE通信的持续优化）、**工程成熟度**（CI精简、文档完善、安全修复）。特别是AMD和Diffusion方向的投入，预示着SGLang正从纯NVIDIA LLM推理框架向多硬件、多模态推理平台演进，这将扩大其用户基础和应用场景。整体而言，项目处于快速迭代期，在保持性能领先的同时，正积极构建更完整的推理生态。

## 详细提交记录

### [c7e2c08](https://github.com/sgl-project/sglang/commit/c7e2c08d14da7b1e3df9af4b7b637f7d683d41b7)

- **作者**: Junhao Shen
- **时间**: 2026-08-19T22:31:14Z
- **提交信息**: fix(constrained): reject NUL bytes in grammar specs to stop an xgrammar segfault (#34679)

Signed-off-by: Junhao Shen <junshen@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [082aac8](https://github.com/sgl-project/sglang/commit/082aac8fce2757a1bbe1049c7a44168ac8fb2030)

- **作者**: milesial
- **时间**: 2026-08-19T22:29:22Z
- **提交信息**: [Bugfix] Fix min-new-token EOS handling (#31378)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>

### [01814e1](https://github.com/sgl-project/sglang/commit/01814e110de026efb9afa0c04feff27e3e3efbcd)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-19T22:23:21Z
- **提交信息**: [HiCache] Simple style change for buffer mode (#35574)

### [38b74d2](https://github.com/sgl-project/sglang/commit/38b74d294b21ec5d64c85d84e8e11a58f64f5784)

- **作者**: Siyuan Chen
- **时间**: 2026-08-19T21:59:35Z
- **提交信息**: Add docs for TP LMHead optimizaiton (#35283)

### [1270204](https://github.com/sgl-project/sglang/commit/1270204d2c6961cd28ff0216a407321824447da3)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-19T21:14:38Z
- **提交信息**: Revert "[Feature] Add DeepEPv2 (ElasticBuffer) MoE A2A backend" (#35568)

### [a6bc053](https://github.com/sgl-project/sglang/commit/a6bc0532c9367d4d23b863c8135c9bd3b8feb44e)

- **作者**: elvischenv
- **时间**: 2026-08-19T21:13:40Z
- **提交信息**: [Fix] Fix Nemotron-H Mamba illegal memory access under DP attention with CUDA graph (#34561)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [ed12d68](https://github.com/sgl-project/sglang/commit/ed12d6827d031ac95e725a0296f6e03282a4dac8)

- **作者**: milesial
- **时间**: 2026-08-19T20:54:37Z
- **提交信息**: fix(disagg): allow fake transfer with decode DCP (#35409)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>

### [defb2a3](https://github.com/sgl-project/sglang/commit/defb2a3100e875ebbc225a711d733f4122d368f8)

- **作者**: Jason Wiemels
- **时间**: 2026-08-19T20:37:50Z
- **提交信息**: feat(openai): Accept the input_audio content part in chat completions (#33606)

### [746418a](https://github.com/sgl-project/sglang/commit/746418a1ec78ff1231e452706ce560bcad787c39)

- **作者**: DarkSharpness
- **时间**: 2026-08-19T20:09:21Z
- **提交信息**: [DSA] Trim top-k v2 output modes and tighten its PDL waits (#35041)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1c82955](https://github.com/sgl-project/sglang/commit/1c82955861e06777638a99824980930ee001c004)

- **作者**: cctry
- **时间**: 2026-08-19T20:01:58Z
- **提交信息**: [HiCache] Split the host-memory budget across co-located ranks (#35540)

### [b170799](https://github.com/sgl-project/sglang/commit/b1707996e8c50b921a91c815d28fe44fe54d8dea)

- **作者**: Ayushman Singh
- **时间**: 2026-08-19T19:41:52Z
- **提交信息**: fix(gemma4): quantize MTP bridge projections (#32440)

### [6f69f92](https://github.com/sgl-project/sglang/commit/6f69f927da9e5692bb4709821faecff6be9b5a8a)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-08-19T19:01:36Z
- **提交信息**: [Scheduler] Add configurable decode interval after prefill (#35017)

### [4f8ecf6](https://github.com/sgl-project/sglang/commit/4f8ecf6ae9a8d609fbb5d19edf68a879c377bf30)

- **作者**: MengYu
- **时间**: 2026-08-19T18:52:45Z
- **提交信息**: [Feature] Add DeepEPv2 (ElasticBuffer) MoE A2A backend (#29525)

Co-authored-by: menyu <menyu@nvidia.com>

### [03cf2de](https://github.com/sgl-project/sglang/commit/03cf2de2e3601f9ccbdf64e02e51dc1f77fe396e)

- **作者**: YAMY
- **时间**: 2026-08-19T18:12:32Z
- **提交信息**: [Qwen3.5][MTP] Preserve online NVFP4 draft quantization for mixed checkpoints (#35545)

### [157d8ad](https://github.com/sgl-project/sglang/commit/157d8ad27acc65425837e8d57c7571b2e591e4a7)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-19T17:58:01Z
- **提交信息**: Support Intern-S2-Mobius FP8 (#34908)

### [5f12839](https://github.com/sgl-project/sglang/commit/5f128395910dafb98c34083dc26cb790c7674d34)

- **作者**: YAMY
- **时间**: 2026-08-19T15:13:45Z
- **提交信息**: [Fix] Support Kimi-K3 ModelOpt mixed NVFP4/FP8 checkpoint (#35077)

### [41c018a](https://github.com/sgl-project/sglang/commit/41c018a9ec9f896f73809eb6ecbb10a7644a7229)

- **作者**: Shuwen Wang
- **时间**: 2026-08-19T14:49:08Z
- **提交信息**: [UnifiedTree] feat: support runtime attach/detach (#35269)

Co-authored-by: hzh0425 <hzh0425@apache.org>

### [1ef7882](https://github.com/sgl-project/sglang/commit/1ef7882a5b76f3eca14b1abd37ffa1da3c353e1c)

- **作者**: Yoray Zack
- **时间**: 2026-08-19T14:31:05Z
- **提交信息**: [NIXL] Query EP top-k index dtype (#35294)

### [23f2320](https://github.com/sgl-project/sglang/commit/23f2320c95b01c05531132e73d1a899dd5081eec)

- **作者**: Mick
- **时间**: 2026-08-19T13:27:58Z
- **提交信息**: [Docs] PaddleOCR-VL: update which stage of the pipeline this serves and show real output (#35458)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [e3445ed](https://github.com/sgl-project/sglang/commit/e3445ed2bda12c878b234a1b77be68b87c619679)

- **作者**: Mick
- **时间**: 2026-08-19T13:02:46Z
- **提交信息**: [diffusion] fix: route quantized vae component repos safely (#35184)

### [29f5d1c](https://github.com/sgl-project/sglang/commit/29f5d1c7c33da409e7dc016073af20b2a5ad5f79)

- **作者**: Mick
- **时间**: 2026-08-19T12:32:31Z
- **提交信息**: [diffusion] fix: fix multi-group layerwise offload startup memory (#35509)

### [c57ada8](https://github.com/sgl-project/sglang/commit/c57ada81e1f01f365268f8b5aaffa9f5bf7d28eb)

- **作者**: Arseniy Mironov
- **时间**: 2026-08-19T12:26:28Z
- **提交信息**: [Diffusion]  Use current_platform instead of hardcoded "cuda" in cosmos3 guardrails  (#34612)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [5742746](https://github.com/sgl-project/sglang/commit/574274660f788174d925cacf99771b939ccba4de)

- **作者**: jacky.cheng
- **时间**: 2026-08-19T10:49:32Z
- **提交信息**: [AMD] cookbook: serve Qwen3.5 MXFP4 on MI355X with an fp8_e4m3 KV cache (#35445)

### [3e5ce26](https://github.com/sgl-project/sglang/commit/3e5ce26c2daba1cc571bfb01decc1d541ef513e5)

- **作者**: Rohit Kumar Singh
- **时间**: 2026-08-19T10:44:23Z
- **提交信息**: fix: fix transcription & audio-understanding for ASR/audio/speech models (#32611)

Co-authored-by: Singh <rohitsi2@iil-login.iind.intel.com>

### [f446e85](https://github.com/sgl-project/sglang/commit/f446e853e73f88c4ef915eeb45a877397fda408c)

- **作者**: karverma-amd
- **时间**: 2026-08-19T10:04:48Z
- **提交信息**: [AMD] DeepSeek-V4: route decode wo_a bf16 batched matmul to aiter batched_gemm_bf16 (#33313)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [ce1830c](https://github.com/sgl-project/sglang/commit/ce1830c59b753b44b91602d7ae98a89aa65b73b9)

- **作者**: karverma-amd
- **时间**: 2026-08-19T10:02:40Z
- **提交信息**: [AMD] DeepSeek-V4 MI355X: eliminate bpreshuffle fp8-scale relayout copy in dense w8a8 linear (#33165)

### [f22442d](https://github.com/sgl-project/sglang/commit/f22442d3a495ce8c2face86489a2d1e121ea039c)

- **作者**: HeYao
- **时间**: 2026-08-19T09:59:45Z
- **提交信息**: Add three new test cases (#35502)

Co-authored-by: HeYao <heyao@example.com>

### [adca19c](https://github.com/sgl-project/sglang/commit/adca19c4970933fa1990fecf3541b527d3153594)

- **作者**: Shangming Cai
- **时间**: 2026-08-19T09:29:45Z
- **提交信息**: [PD] Deferred decode-side KV release for the NIXL backend (#35360)

### [aa215e5](https://github.com/sgl-project/sglang/commit/aa215e55230bc9b0eb503b5a3886c015c2e5f526)

- **作者**: YAMY
- **时间**: 2026-08-19T09:25:52Z
- **提交信息**: [PD] Overlap prefill DP-rank bootstrap queries (#35071)

### [0e4a094](https://github.com/sgl-project/sglang/commit/0e4a09480ccf598cfc11f4ca0bfa7a0adfb8f9b1)

- **作者**: Khoa Pham
- **时间**: 2026-08-19T08:42:19Z
- **提交信息**: [HiCache] Support DCP with DSpark (#35221)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [9113fc6](https://github.com/sgl-project/sglang/commit/9113fc6d93f85aa6f6bcd25d11b1ebceeb0c4b04)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-19T08:32:42Z
- **提交信息**: [docs] Add a fused-kernels page for SGLang Diffusion (#35436)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [8a1e6e4](https://github.com/sgl-project/sglang/commit/8a1e6e4e461044246739b5a1ad579c8acc556a2d)

- **作者**: Yuhao Yang
- **时间**: 2026-08-19T08:31:43Z
- **提交信息**: Qwen3.8-27B Model Support (#34859)

Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>
Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>
Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>

### [ebec85f](https://github.com/sgl-project/sglang/commit/ebec85f6065ef5b3125944a75f4d2919cafd5a93)

- **作者**: kangwangamd
- **时间**: 2026-08-19T08:27:20Z
- **提交信息**: [AMD][DI][CI] Run MI355X disagg nightly at 7AM UTC (#35467)

Co-authored-by: bingxche <bingxche@users.noreply.github.com>

### [73e5fa4](https://github.com/sgl-project/sglang/commit/73e5fa4724d812e3df7681f781777853eb6a06e9)

- **作者**: Mick
- **时间**: 2026-08-19T08:18:36Z
- **提交信息**: [diffusion] refactor: gate native encoder quantized checkpoints (#35183)

Co-authored-by: Yiqi Yang <yangyiqi8787@gmail.com>

### [ccbe380](https://github.com/sgl-project/sglang/commit/ccbe38002873f76499749fc1e06d8c6a18cc0151)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-19T07:48:07Z
- **提交信息**: [CI] Trim the base-c 4-gpu-h100 stage from 5 shards to 4 (#35407)

### [e614121](https://github.com/sgl-project/sglang/commit/e6141218667a405f74247ba11273d3bdf1a69049)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-19T07:37:26Z
- **提交信息**: [Fix] Scale the req_to_token row headroom by attn_dcp_size (#35424)

### [f415871](https://github.com/sgl-project/sglang/commit/f4158719d176fa6caf7086f4e4e187e538a09906)

- **作者**: Michael
- **时间**: 2026-08-19T07:17:40Z
- **提交信息**: [AMD] Let the diffusion AITer backend take grouped-query K/V (fix Cosmos3-Nano startup) (#34485)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Michael <michaelzhang-ai@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1250
- **最后更新**: 2026-08-19T02:22:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89467
- **最后更新**: 2026-08-19T22:18:59Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 29
- **主要提交者**: Andreas Karatzas, akii96, Nick Hill

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本次35个提交涵盖Bug修复（约14个）、CI/构建改进（约6个）、ROCm/AMD平台支持（约5个）、量化与内核优化（约4个）、模型支持新增（约2个）、前端/API调整（约3个）、文档更新（约2个）及重构（约1个），整体以稳定性和平台扩展为主。

## 二、关键变更点与项目方向

1. **AMD ROCm平台持续强化**：多个提交扩展了ROCm下的MoE测试覆盖、Fused MoE/FP8测试支持、Triton内核优化及EngineCore清理机制，体现vLLM对AMD GPU生态的重视，与“为所有人提供LLM服务”的愿景一致。

2. **量化与内核优化**：修复CT block FP8与Marlin的兼容性、恢复int8分组WNA16 MoE支持、修复OCP MX MoE的mxfp6激活量化问题，以及SM120上FP8 GEMM路由修正，直接提升推理效率与模型兼容性。

3. **MoE架构支持扩展**：新增Kimi K3 MoE基准测试支持、Humming WNA16 MoE支持，并修复Triton fused shared expert对齐问题，强化了vLLM在MoE模型领域的领先地位。

4. **模型架构新增**：支持DeepSeek双向（encoder-only）注意力机制、新增NemotronH_Omni_Reasoning_V3架构支持，持续扩大模型覆盖范围。

5. **LoRA机制修复**：避免不支持模块类型的误匹配、修复部分LoRA场景下的None组员问题，提升LoRA功能的鲁棒性。

6. **前端与API改进**：修复n>1时生成结果返回不完整的问题、将api_server.py移出openai文件夹、语义化任务校验错误，改善用户体验与代码结构。

## 三、项目影响与潜在意义

- **稳定性显著提升**：大量Bugfix覆盖量化、LoRA、前端、日志安全（API密钥脱敏）等关键路径，降低生产环境风险。
- **多硬件平台战略加速**：ROCm相关提交占比高，配合CPU平台修复（causal_conv1d GDN路径、float32 SSM缓存），vLLM正从NVIDIA独占走向多平台覆盖。
- **性能优化持续深化**：内核级优化（FP8 GEMM路由、Triton对齐、scale packing）直接提升推理吞吐与延迟表现。
- **CI/CD体系加固**：自动标签修复、GPU清理检查强化、文档构建修复，保障项目长期可维护性。

## 四、值得关注的技术点

1. **SM120 FP8 GEMM路由修正**：避免将misaligned-M blockwise操作路由到small-M配置，属于硬件适配层面的精细优化。
2. **prefix-cache广播跳过优化**：跳过mm tensor数据向worker的广播，减少通信开销，对长序列场景收益明显。
3. **InstantTensor加入CUDA依赖**：可能引入新的张量计算加速能力。
4. **UE8M0 scale packing**：为Triton内核新增量化格式支持，扩展低比特推理能力。
5. **双向注意力支持**：为DeepSeek等编码器模型铺路，拓展vLLM从纯解码器到编码器-解码器架构的边界。

## 五、对项目发展的整体影响

vLLM正沿着“性能极致优化+多硬件适配+模型生态扩展”三条主线快速演进。昨日提交体现了项目在保持NVIDIA平台领先性能的同时，大力投入ROCm/CPU/XPU等替代平台建设，并通过持续修复量化、MoE、LoRA等核心功能的边界问题来巩固生产就绪度。CI体系的加固和文档修复则保障了社区协作效率。整体来看，vLLM正从“NVIDIA GPU上的高性能推理引擎”向“全平台、全模型类型的通用LLM服务基础设施”转型，这些提交正是这一战略的具体落地。

## 详细提交记录

### [c205726](https://github.com/vllm-project/vllm/commit/c205726108df54bb6fbf15b19e725a4a3add2b18)

- **作者**: jcotant-inferact
- **时间**: 2026-08-19T21:45:44Z
- **提交信息**: [CI] Fix and extend PR/issue auto-labeling (#51459)

Signed-off-by: Joe Cotant <joe@inferact.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d591d1d](https://github.com/vllm-project/vllm/commit/d591d1d511b5f2a70ae34adfd5adc5c1956ecae2)

- **作者**: vanshbhatia-amd
- **时间**: 2026-08-19T19:42:30Z
- **提交信息**: [Bugfix] Add Kimi K3 MoE support to benchmark_moe.py (#50082)

Signed-off-by: Vansh Bhatia <210711135+vanshbhatia-amd@users.noreply.github.com>
Co-authored-by: Vansh Bhatia <210711135+vanshbhatia-amd@users.noreply.github.com>

### [541c6d6](https://github.com/vllm-project/vllm/commit/541c6d64c19b64b970edc9122a56027d41b7a0be)

- **作者**: Misha Goin
- **时间**: 2026-08-19T19:41:26Z
- **提交信息**: [Bugfix][Quantization] Support CT block FP8 with Marlin (#52966)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [cb58bb9](https://github.com/vllm-project/vllm/commit/cb58bb9c1e38cd366910858873946c95be6328a9)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-19T19:17:17Z
- **提交信息**: [CI] Harden RemoteVLLMServer GPU cleanup checks (#52282)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [480d4f0](https://github.com/vllm-project/vllm/commit/480d4f0d154a00b719abf876dd9c1a98bc5acbf7)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-19T18:46:12Z
- **提交信息**: [ROCm][CI] Enable modular OAI Triton MoE tests (#46434)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [755492e](https://github.com/vllm-project/vllm/commit/755492e37d7d7201d93f0effa200acac56601f38)

- **作者**: Roger Wang
- **时间**: 2026-08-19T17:48:46Z
- **提交信息**: Revert "[Kernel] Gemma-4 FA4 FP8 Kernel" (#52987)

### [f76d71d](https://github.com/vllm-project/vllm/commit/f76d71d7ceac040d555323f36b2f6afeab0e8df2)

- **作者**: Misha Goin
- **时间**: 2026-08-19T17:32:37Z
- **提交信息**: [CI/Build] Fix CPU platform pre-commit formatting (#52981)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9b5f345](https://github.com/vllm-project/vllm/commit/9b5f3454f2be4c2c0f17c84a78af25a1d550d446)

- **作者**: linitra24
- **时间**: 2026-08-19T16:48:11Z
- **提交信息**: [LoRA] Avoid false target matches for unsupported module types (#52313)

Signed-off-by: linitra24 <Joy25810@foxmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [0c8c3f4](https://github.com/vllm-project/vllm/commit/0c8c3f41cff4a4d361d4a80804eddd8dfc2a56ce)

- **作者**: lxy
- **时间**: 2026-08-19T16:44:36Z
- **提交信息**: [Bugfix][V1] Sync mamba_block_size via EngineCoreReadyResponse (#50809)

Signed-off-by: “新颐” <lxy537258@antgroup.com>
Co-authored-by: “新颐” <lxy537258@antgroup.com>

### [3a386cf](https://github.com/vllm-project/vllm/commit/3a386cfaf51f872334c64edd08fbf71dd4bb0120)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-19T16:39:59Z
- **提交信息**: [ROCm] Give EngineCore cleanup grace after request abort (#52281)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e9e1630](https://github.com/vllm-project/vllm/commit/e9e1630e93b13b241c4cdb52c47e35fd38c6eb46)

- **作者**: Egor
- **时间**: 2026-08-19T16:36:27Z
- **提交信息**: [Model] Support bidirectional (encoder-only) attention for DeepSeek e… (#52948)

Signed-off-by: Egor <erop001@gmail.com>
Signed-off-by: Egor <47443236+Lossfull@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [54dd98b](https://github.com/vllm-project/vllm/commit/54dd98be2830bbd7b70fd60a0e917b7d0df5adab)

- **作者**: Yi Liu
- **时间**: 2026-08-19T16:31:32Z
- **提交信息**: [CT] Support Humming for WNA16 MoE (#48918)

Signed-off-by: yiliu30 <yi4.liu@intel.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c676232](https://github.com/vllm-project/vllm/commit/c676232313fce3d607da7c66e41fe8d4739c194d)

- **作者**: xuebwang-amd
- **时间**: 2026-08-19T16:29:29Z
- **提交信息**: [Bugfix][Quantization] Fix OCP MX MoE emulation silently skipping mxfp6 activation QDQ (#52704)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>

### [583a002](https://github.com/vllm-project/vllm/commit/583a00257d4c5d1a54063d956057df1df6822b06)

- **作者**: akii96
- **时间**: 2026-08-19T16:14:52Z
- **提交信息**: [ROCm] [Bugfix] Fix Triton fused shared expert alignment (#51632)

Signed-off-by: Aakif Nawaz <aakif.nawaz@amd.com>

### [525b7bb](https://github.com/vllm-project/vllm/commit/525b7bbb3a74d811cedcee108425d9bb5c215fdd)

- **作者**: Dinesh Chitlangia
- **时间**: 2026-08-19T15:50:59Z
- **提交信息**: [Bugfix][CPU] Enable C++ causal_conv1d GDN path and float32 SSM cache on non-AMX AVX-512BF16 CPUs (#49688)

Signed-off-by: Dinesh Chitlangia <dineshchitlangia@gmail.com>

### [17dbd42](https://github.com/vllm-project/vllm/commit/17dbd429306d2fe9cc6be04e57aab314bd697f5e)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-19T15:20:05Z
- **提交信息**: [ROCm] Add UE8M0 scale packing for Triton silu_mul_quant (#37835)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [160f7f0](https://github.com/vllm-project/vllm/commit/160f7f0840e1773b2418199800c7ac66f1b4f074)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-19T15:19:42Z
- **提交信息**: [ROCm][CI] Extended Fused MoE and FP8 MoE test support (#41100)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [be06873](https://github.com/vllm-project/vllm/commit/be06873198cd544f963b4e2f0f0877b23ab5861e)

- **作者**: Yohann Prigent
- **时间**: 2026-08-19T14:55:59Z
- **提交信息**: [Bugfix] compressed-tensors: restore int8 grouped WNA16 MoE support (#52002)

Signed-off-by: Yohann Prigent <prigent.yohann@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [2d7f42b](https://github.com/vllm-project/vllm/commit/2d7f42b4f3b2b69dd9b2610d287083d147c997f6)

- **作者**: Misha Goin
- **时间**: 2026-08-19T14:55:09Z
- **提交信息**: [Build] Add InstantTensor to CUDA dependencies (#52801)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [db92053](https://github.com/vllm-project/vllm/commit/db92053e97b5630a6a36118693b1dffe9b03be36)

- **作者**: Xiaoan (Sean) Liu
- **时间**: 2026-08-19T14:16:39Z
- **提交信息**: [Core] Skip broadcasting mm tensor data to workers for prefix-cache-covered items (#52041)

Signed-off-by: Xiaoan (Sean) Liu <shawnliu0327@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [2b7fcbf](https://github.com/vllm-project/vllm/commit/2b7fcbf52782f8729fd6ce6c9ab803617d72897b)

- **作者**: Gabriel Wu
- **时间**: 2026-08-19T13:25:29Z
- **提交信息**: [Kernel] SM120: stop routing misaligned-M blockwise FP8 GEMMs to the small-M swapAB config (#52775)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>

### [c2e7242](https://github.com/vllm-project/vllm/commit/c2e7242ab7287cc9e2bdbea5901c560fc2d17bff)

- **作者**: Eilam
- **时间**: 2026-08-19T13:24:26Z
- **提交信息**: [Bugfix][LoRA] Guard None group members in expand_packed_lora (partial LoRA on Qwen3.5/3.6 GatedDeltaNet) (#47640)

Signed-off-by: Eilam C <eilamc14@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [92bdee0](https://github.com/vllm-project/vllm/commit/92bdee05cb4ea5e94c4cce3eb0544f51d6eece8d)

- **作者**: Quentin Gallouédec
- **时间**: 2026-08-19T12:48:45Z
- **提交信息**: [Bugfix][Frontend] Return all choices from /inference/v1/generate when n > 1 (#52399)

Signed-off-by: Quentin Gallouédec <quentin.gallouedec@huggingface.co>

### [58de6cb](https://github.com/vllm-project/vllm/commit/58de6cbdc2fac255ca6fe6855f90c65f80a76d57)

- **作者**: Nave Assaf
- **时间**: 2026-08-19T12:34:50Z
- **提交信息**: Add NemotronH_Omni_Reasoning_V3 as a supported Nemotron architecture (#52929)

Signed-off-by: Nave Assaf <nassaf@nvidia.com>

### [2f54100](https://github.com/vllm-project/vllm/commit/2f54100a593e34dd473912c756346abee55a6246)

- **作者**: Harry Mellor
- **时间**: 2026-08-19T12:25:46Z
- **提交信息**: [CI] Fix docs build (#52937)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [58302b4](https://github.com/vllm-project/vllm/commit/58302b459198eec60fad49af3c506ec10d6af821)

- **作者**: QWERQWERQWE86
- **时间**: 2026-08-19T11:38:34Z
- **提交信息**: [Doc] Fix group numbering in Case 3 of hybrid_kv_cache_manager.md (#52160)

Signed-off-by: qwerqwerqwe8688-jpg <xuuuuu2021@163.com>

### [b160cab](https://github.com/vllm-project/vllm/commit/b160cab156106b212ee67beb16c9725d366b8857)

- **作者**: hy123
- **时间**: 2026-08-19T11:18:10Z
- **提交信息**: [Bugfix] Restore model info caching for package backends (#52690)

Signed-off-by: haoyang.qian <haoyangqian@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [cba0676](https://github.com/vllm-project/vllm/commit/cba06764d7a9da41e6f535d6355c13f725574f07)

- **作者**: wangxiyuan
- **时间**: 2026-08-19T10:31:19Z
- **提交信息**: [Platform] Fill in the missing backend parameter for torch.compile (#51781)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [eac636a](https://github.com/vllm-project/vllm/commit/eac636a7fa476983cdae34b45a984e9852aad375)

- **作者**: wang.yuqi
- **时间**: 2026-08-19T09:43:46Z
- **提交信息**: [Frontend] Move api_server.py out openai folder (#52131)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [340b7e4](https://github.com/vllm-project/vllm/commit/340b7e4909f14ff33943ab6ac7955191e1b8b4ff)

- **作者**: Yufeng He
- **时间**: 2026-08-19T09:29:32Z
- **提交信息**: fix: reject string schemas that mix pattern/format with length bounds (#49996)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>

### [93eea4f](https://github.com/vllm-project/vllm/commit/93eea4f665a0a6a188fd52b37f4a18bc37315f62)

- **作者**: Qiming Zhang
- **时间**: 2026-08-19T09:01:12Z
- **提交信息**: [XPU][CI] downgrade sentencepiece (#52904)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [9a9aa2b](https://github.com/vllm-project/vllm/commit/9a9aa2b017b468082ca538b6f7a725a60d7f8b47)

- **作者**: LuckyStep
- **时间**: 2026-08-19T07:52:53Z
- **提交信息**: [Bugfix] Redact api_key in non-default args log (#52523)

Signed-off-by: LuckyStep <67696304+Andy365-365@users.noreply.github.com>

### [842dd8f](https://github.com/vllm-project/vllm/commit/842dd8fd96650063e1ad32e6075742d457d39773)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-19T07:21:08Z
- **提交信息**: [Pooling] Use semantic task validation errors (#52867)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [b09bd69](https://github.com/vllm-project/vllm/commit/b09bd69b5bf14911abef9a0e8e493b83c8a38fa6)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-19T07:13:52Z
- **提交信息**: [Model][NVIDIA] Route DSA models to the CUDA non-compiled path (#52861)

### [ee11730](https://github.com/vllm-project/vllm/commit/ee117307512f7ab0fe5ce70f8a2963bb83dfc442)

- **作者**: Nick Hill
- **时间**: 2026-08-19T07:07:40Z
- **提交信息**: [BugFix] Revert incorrect MM keep_on_cpu=True changes (#52881)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-20
**监控日期**: 2026-08-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6178
- **最后更新**: 2026-08-19T21:32:22Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: WeiQing Chen, Zeyu Huang | 黃澤宇, Joshna-Medisetty

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以 **Bug修复** 为主（3项），辅以 **文档更新**（2项）和 **测试重构**（1项），无新增功能或性能优化。

### 2. 关键变更点与项目方向的关系
- **XPU设备异步D2H图像损坏修复**：针对Intel XPU平台，将`torch.Event`改为设备无关实现，解决异步设备到主机传输中的图像数据损坏问题，直接服务于项目“多模态模型服务”的跨硬件兼容目标。
- **FLUX.2-klein图像位置ID去重**：修复图像token位置编码重复问题，提升图像生成模型的输出质量，强化了项目对最新扩散模型的支持能力。
- **MiniCPM-o流式音频缓存恢复**：恢复流式音频缓存机制并解决首个双工响应卡顿问题，改善实时语音交互体验，与项目“全模态”定位高度契合。
- **文档清理与更新**：移除过时的`DiffusionParallelConfig`配置引用、更新微信二维码，保持文档与代码同步，降低用户上手门槛。
- **API服务端防护测试**：新增API server表面防护的P0级测试，提升服务稳定性和安全性。

### 3. 对项目的影响和潜在意义
- **硬件生态扩展**：XPU修复使项目在Intel加速卡上的可用性显著提升，扩大潜在用户群体。
- **多模态体验优化**：图像和音频相关的修复直接改善核心场景（文生图、语音对话）的用户体验，增强产品竞争力。
- **工程质量提升**：测试防护和文档清理表明项目正从功能开发转向成熟度打磨，为大规模部署做准备。

### 4. 值得关注的技术点
- **设备无关的`torch.Event`**：在XPU上使用设备无关事件记录时间戳，避免异步操作中的设备特定行为差异，是跨平台AI框架的关键实践。
- **图像位置ID去重逻辑**：涉及FLUX.2-klein的token序列构造，修复需确保位置编码唯一性而不破坏注意力机制，属于精细的模型层调试。
- **流式音频缓存恢复**：涉及双工通信中的状态管理，恢复缓存需兼顾内存占用与响应延迟的平衡。

### 5. 对项目发展的影响
vLLM-Omni定位为“人人可用的全模态模型服务”，本次提交在三个维度推动这一愿景：**广度上**，XPU支持扩展硬件覆盖；**深度上**，图像与音频修复提升核心模态质量；**厚度上**，测试与文档完善增强项目可靠性。这些改动虽小，但标志着项目正从“能跑”向“好用”过渡，为吸引更广泛开发者社区和实际生产部署奠定基础。

## 详细提交记录

### [efaf427](https://github.com/vllm-project/vllm-omni/commit/efaf4276f93d3e0833198e97ba091ffb530b3dab)

- **作者**: Thanaji Rao Thakkalapelli
- **时间**: 2026-08-19T21:30:38Z
- **提交信息**: [Bugfix] Record device-agnostic torch.Event on XPU to fix async D2H image corruption [XPU] (#5571)

Signed-off-by: Thanaji Rao Thakkalapelli <thanaji.rao.thakkalapelli@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [ea24dee](https://github.com/vllm-project/vllm-omni/commit/ea24deefcce4d44339105e0fe6d243743b858074)

- **作者**: Joshna-Medisetty
- **时间**: 2026-08-19T21:30:12Z
- **提交信息**: [Bugfix][FLUX.2-klein] Fix duplicated image position ids  (#6130)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Signed-off-by: Joshna-Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [c3f8050](https://github.com/vllm-project/vllm-omni/commit/c3f80502e00b564d7b74d43a5e21fbc6b9da2aed)

- **作者**: WeiQing Chen
- **时间**: 2026-08-19T10:52:24Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#6369)

Signed-off-by: David Chen <530634352@qq.com>

### [8dc3d50](https://github.com/vllm-project/vllm-omni/commit/8dc3d504d8bae73bd6a627b4b759a4dbe6cd35fb)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-08-19T07:27:58Z
- **提交信息**: [skip ci][Doc] Remove obsolete DiffusionParallelConfig in many example scripts (#6347)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [7099583](https://github.com/vllm-project/vllm-omni/commit/70995834040f488d63ed5c916fcee4e94268a902)

- **作者**: BruceLoveDecimal
- **时间**: 2026-08-19T07:26:03Z
- **提交信息**: [Bugfix][MiniCPM-o] Restore streaming audio cache and unstall the first duplex response (#6274)

Signed-off-by: BruceLoveDecimal <liuqihao970610@gmail.com>

### [ac00670](https://github.com/vllm-project/vllm-omni/commit/ac0067078bd01200776b74e15ee7119153ab1af8)

- **作者**: herotai214
- **时间**: 2026-08-19T07:20:18Z
- **提交信息**: [Tests][Refactor] P0.1: Add API server surface guardrails (#6202)

Signed-off-by: herotai214 <herotai214@gmail.com>

---
