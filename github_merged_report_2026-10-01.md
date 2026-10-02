# GitHub Stars 合并报告 - 2026-10-01

**合并日期**: 2026-10-02
**监控日期**: 2026-10-01
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


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2230
- **最后更新**: 2026-09-30T08:21:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2867
- **最后更新**: 2026-10-01T19:07:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2277
- **最后更新**: 2026-10-01T19:56:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6530
- **最后更新**: 2026-10-02T01:12:14Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 6
- **主要提交者**: Ka-Hyun Nam, LightSeek Foundation, Jan Bernlöhr

## AI分析总结

# FlashInfer 昨日 19 个提交综合分析

## 一、主要更新类型
- **性能优化**：NVFP4 半-M 对 tile 路由、Kimi-K3 AttnRes 后端、SM12x NVFP4 W4A4 GEMM、W4A16 预取策略、MoE 分组 GEMM 等，在多类算子上取得 1.2–2.13 倍加速。
- **大型重构**：退役孤立的 MoE all-reduce 融合源码包（约 −29 万行生成代码），合并为少量手写绑定与运行时调度启动器；撤销对上游 CuTe DSL 内核的侵入性改动；清理不可达内核、统一 JIT 构建路径。
- **Bug 修复**：CUDA graph scratch 张量保持、块缩放 GEMM 地址错位崩溃、cuTile 架构守卫、autotuner 策略元数据丢失、SM110 AOT 注册遗漏等。
- **功能新增**：Kimi-K3 AttnRes 后端（SM100/SM103）、cake 系列后端（`backend="cake"`/`"cake_cute"`）以隔离方式接入。

## 二、关键变更点与项目方向
1. **核心与实验分离的架构哲学**：撤销对上游 CuTe DSL 内核的侵入式修改，CAKE/Kimi-K3 等专用内核改为通过独立后端 API 接入，核心内核保持无改动的参考实现。
2. **MoE 维护成本清偿**：MoE all-reduce fusion 与 union 两批生成代码从数百个内核/绑定对折叠为数十个翻译单元加一个通用启动器；PDL、cooperative launch、架构差异均改为运行时标志（如 `__CUDA_ARCH__` 守卫、设备缓存 SM 数），消除组合爆炸，为后续隐藏尺寸扩展和模板化再生成奠定基础。
3. **下一代 GPU 覆盖**：围绕 Blackwell（SM100/SM103/SM107）与 DGX Spark（SM120/SM121）持续扩展量化推理（NVFP4、MXFP4、FP8 groupwise、W4A8）能力，并加速从 CUTLASS 向 CuTe DSL 生成内核的迁移。
4. **量化输出 ABI 统一**：量化张量改为按字节类型校验，与 TRT-LLM 后端行为对齐，提升框架兼容性。

## 三、对项目的影响
- **可靠性提升**：GEMM 崩溃修复消除 B200 CI 上千个失败用例；CUDA graph scratch 修复消除内存破坏隐患；错误处理改为抛异常前清除 CUDA 错误，避免"幽灵错误"污染调用方。
- **性能收益显著**：27B down projection 在 M=8192 时达 2.13 倍加速；动态 W4A4/W4A16 权重 buffer 共享设计为 serving 场景的精度自适应选择奠定基础。
- **工程质量**：零风险重构（设备端 SASS 字节级不变）保证推理性能无回归；kernel bundle 通过源码哈希与 manifest digest 保证字节级可追溯。

## 四、值得关注的技术点
- **CUDA graph 安全性**：scratch 张量地址被图捕获后遭缓存分配器重用会写入外域内存，修复采用退役列表加容量倍增控制内存上界。
- **SFB/TMEM 寻址约束**：`tcgen05.mma` 对奇数列偏移敏感，窄 N tile 的 SFB 寻址需兼顾正确性与配置覆盖。
- **PDL 运行时化**：从编译时克隆改为启动时经 `cudaLaunchAttributeProgrammaticStreamSerialization` 注入，是减少代码克隆的典范。
- **Benchmark 方法论**：冷 L2 刷新、CUPTI 按 rank 聚合、CUDA graph replay、多轮交错采样等严谨协议确保结果可信。
- **分阶段调度**：staged/persistent/ping-pong 等策略按 M 值形状自动选择，体现精细性能工程。

## 五、整体项目发展影响
FlashInfer 作为高性能 GPU 推理内核库，正在"稳定核心 + 可插拔实验后端"的路径上持续演进：通过大规模生成代码的参数化重构清偿技术债务，同时以隔离方式快速跟进 Kimi-K3 等采用前沿量化方案的大模型。这既服务 SGLang 等推理引擎的通用需求，又巩固了项目作为 AI 推理基础设施底层算力核心组件的地位，为 MoE 大模型的高性能 serving 提供了更稳固、更可扩展的支撑。

## 详细提交记录

### [1db3fe8](https://github.com/flashinfer-ai/flashinfer/commit/1db3fe8ec169056dcd3f0c8bf92845bd76cfbd4c)

- **作者**: eigen
- **时间**: 2026-10-01T23:21:17Z
- **提交信息**: revert(cake_fused_moe): remove the Kimi-K3 W4A8 MXFP4 SiTU changes to the CuTe DSL MoE path (#5430) (#5681)

> Developed by the **CAKE team**, the kernels in this PR **outperform**
the relevant **SOTA baselines at the time of merge** on the **vast
majority of performance benchmark shapes**, matching them otherwise.

This PR reverts the CuTe DSL MoE changes from the **CAKE team's**
Kimi-K3 SiTU work (optimized on existing kernels by CAKE), since we want
to keep CAKE kernel holistic and independent on others' kernel; it
introduces no new kernels or SOTA performance comparison.

## Summary

Reverts #5430 (merged as 05ebb2d7976) in full. The MXFP4 SiTU routed MoE
work in that PR modified the existing CuTe DSL grouped GEMM kernels and
the shared plan/routing path rather than living beside them:

-
`flashinfer/fused_moe/cute_dsl/blackwell/blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`,
`..._finalize_fusion.py`, `utils.py`
-
`flashinfer/fused_moe/cute_dsl/blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`,
`..._finalize_fusion.py`, `fused_moe.py`, `moe_utils.py`, `__init__.py`
- `csrc/moe_utils_binding.cu`,
`csrc/fused_moe/trtllm_backend/trtllm_fused_moe_routing_common.cu`
- `include/flashinfer/trtllm/fused_moe/RoutingKernel.cuh`,
`RoutingKernel.h`
- `flashinfer/fused_moe/prepare.py`, `docs/index.rst`

These files return to their pre-#5430 content, so the original CuTe DSL
kernels are again the unmodified reference for this path. The files
#5430 added (the MXFP4 SiTU runner, `mxfp4*.py`, the swap-AB grouped
GEMM and its dispatch binding, `benchmarks/bench_mxfp4_situ_moe.py`,
`benchmarks/mxfp4_situ_timing.py`, `docs/mxfp4_situ_moe.rst`,
`tests/moe/test_cute_dsl_mxfp4_situ*.py`) are removed with it.

The open follow-up on the same path, #5639, is being closed instead of
merged. The MXFP4 SiTU routed MoE will return as separate backends of
the fused MoE API (`backend="cake"` and `backend="cake_cute"`) that do
not modify the upstream CuTe DSL kernels.

One change from that lineage is worth keeping on its own: the
finalize-fusion kernel must issue its griddepcontrol wait before the
first read of the routing outputs under programmatic dependent launch.
That is submitted as a separate minimal fix PR, #5682.

## Verification

- `git revert -m 1 05ebb2d7976` applied with no conflicts on top of
90a709ca8 (current `main`).
- Every restored file is byte-identical to its content at `05ebb2d7976^`
(`git diff 05ebb2d7976^ -- <modified files>` is empty).
- No commit on `main` after 05ebb2d7976 touched any of the reverted
files (`git log 05ebb2d7976..origin/main -- <files>` is empty), so
nothing else is affected.
- Upstream pre-commit hooks pass on the modified files (mypy, ruff
check, ruff format, clang-format, whitespace).

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Expanded use of the single-cluster routing path on newer GPUs to
include token counts above the previous 1,024-token cutoff.

* **Other Changes**
* Removed experimental MXFP4 SiTU MoE support, including related
benchmarks, utilities, tests, and APIs.
* Simplified MoE routing and execution to use a single tile
configuration; several advanced scheduling and launch options are no
longer available.
* SiTU parameters now accept scalar values only and require the SwiGLU
activation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0c101ac](https://github.com/flashinfer-ai/flashinfer/commit/0c101ac509fa4a8b2ab8acdf1528c22432deb4fa)

- **作者**: eigen
- **时间**: 2026-10-01T23:06:20Z
- **提交信息**: fix(cake_comm): retain replaced MoE all-reduce scratch tensors recorded by captured graphs (#5894)

Follow-up of #5856 (the review thread on `scratch_allreduce_output`).

## Problem

`trtllm_moe_allreduce_fusion(backend="cake")` without
`moe_allreduce_out` writes the all-reduce output into a loader-owned
scratch tensor, cached per `(device, dtype)` and replaced when a larger
`token_num` arrives. A CUDA graph captured while the cached scratch was
large enough records that tensor's device address (the launcher passes
only `data_ptr()`). A later eager call with a larger `token_num`
replaced the cache entry and dropped the only reference, so the caching
allocator could hand the storage to another tensor and a graph replay
would write the all-reduce output into foreign memory. A capture that
needs a *larger* scratch was already safe: the fresh tensor comes from
the graph's private pool and is not cached.

## Fix

- Replaced scratch tensors are retired into a module-level list for the
process lifetime instead of being freed.
- The cache grows to at least twice its previous capacity, so the total
retired memory stays bounded by the live capacity (without this a slowly
increasing `token_num` sequence would retire O(T²) rows).
- Docstring states the retention requirement. No kernel, launcher or
route change; `csrc/cake_trtllm_moe_allreduce_union/` is untouched.

## Tests

-
`test_scratch_allreduce_output_is_cached_per_device_and_dtype_and_grows`
(CPU) now asserts the replaced tensor is retired and the doubling.
- New
`test_scratch_allreduce_output_retains_addresses_recorded_by_captured_graphs`
(GPU): captures a graph that fills the cached scratch, grows the cache
eagerly, allocates a canary of the old size, replays the graph and
asserts the canary is untouched and the recorded address is in the
retired list.
- `tests/comm/test_cake_moe_allreduce_api.py` +
`tests/comm/test_cake_moe_allreduce_union.py`: 70 passed on a B200 node
(pytorch:26.01 container, main 08776e742 + this change); ruff 0.12.8
check and format clean.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved scratch-buffer resizing so repeated requests can reuse a
larger allocation.
* Preserved allocations used by captured CUDA graphs, helping prevent
invalid memory access during graph replay.
  * Added coverage for buffer reuse and CUDA graph replay behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e429900](https://github.com/flashinfer-ai/flashinfer/commit/e429900768cfae8c07930e9fee1d1cfcdd3c8883)

- **作者**: Mingyang Wang
- **时间**: 2026-10-01T22:46:11Z
- **提交信息**: fix(tests): skip unsupported cuTile groupwise GEMM architectures (#5883)

<!-- .github/pull_request_template.md -->

## 📌 Description

The dedicated cuTile output-dtype and invalid-layout tests admit SM107
through a major-only architecture check, then fail because the
production backend rejects that capability. Replace both guards with the
production `is_backend_supported("cutile", cc)` query and skip before
allocation. Preserve the existing parameter matrix, dependency checks,
and assertions.

## 🔍 Related Issues

Follow-up to #5759, which fixed the main parametrized groupwise GEMM
test. This change covers the two dedicated cuTile tests in the same
file.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Targeted validation:
- All 17 dedicated cuTile cases passed on B100 (CUDA 13.4, cuTile
1.5.0): `python3 -m pytest tests/gemm/test_groupwise_scaled_gemm_fp8.py
-q -k 'test_gemm_fp8_nt_groupwise_cutile_out_dtypes or
test_gemm_fp8_nt_groupwise_cutile_rejects_mn_scale_major'`.
- 31 evidence-only guard checks passed against the actual test bodies:
mocked SM107/no-CUDA skips, missing-toolchain skips, and
supported-capability continuation. No permanent regression module added.
- Changed-file pre-commit hooks and diff hygiene passed; repository-wide
hooks/tests were not run.
- Validation was performed before rebasing onto
`9deb117bfb8aad2bd08ed781238483be3dec9810`; the final test file is
byte-identical and relevant GEMM implementation, support-query logic,
dependencies, and test harness are unchanged. No new GPU run after
rebase.
- Actual SM107 execution was not rerun. The validation image had
conflicting PyTorch/cuDNN dependency pins; the editable install used
`--no-deps` to preserve its preinstalled packages, followed by
dependency preflight and the passing targeted GPU run.

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

Test-only change; production capability support is unchanged. The
invalid-layout case still checks its original `ValueError` on supported
devices. An independent review found no issues.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated FP8 groupwise GEMM test coverage to check cuTile support for
the detected GPU compute capability.
* The tests now skip when CUDA is unavailable or the detected capability
is unsupported, while preserving existing test behavior otherwise.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [91dcc2a](https://github.com/flashinfer-ai/flashinfer/commit/91dcc2ab031a240a8bc0fa622656e3e9502e7802)

- **作者**: eigen
- **时间**: 2026-10-01T22:22:48Z
- **提交信息**: fix(gemm): keep narrow block-scaled N tiles inside the first 32-token SFB group (#5890)

## Summary

`tests/gemm/test_mm_mxfp8.py::test_mm_mxfp8[True-cute-dsl-...]` fails on
every B200 CI run that executes the file since the 2026-09-28 nightly:
the first `cute-dsl` autotune case dies with `CUDA error: misaligned
address` and the remaining 1080 cute-dsl cases fail on the sticky
context error. The regression comes from #5609, which relaxed
`Sm100BlockScaledPersistentDenseGemmKernel.can_implement` for narrow N
tiles (8/16/32) from `n <= tile_n` to any `n`, relying on the sub-tile
SFB addressing added there. That addressing shifts the MMA's SFB TMEM
address by one column per 32 tokens; `tcgen05.mma` faults when that
shift is odd (observed for offsets 1 and 3), while the 64-wide tile's
two-column shift is fine. The MXFP8 cute-dsl runner therefore enumerated
18 faulting tactics (`(128, 8/16/32)` x clusters `(1,1)/(2,1)/(4,1)` x
both operand orders) that the autotuner profiles before it ever checks
correctness.

This PR restores the safe boundary: narrow N tiles are valid only while
every sub-tile stays inside the first 32-token group, i.e. the kernel-N
extent (`n`, or `m` when A and B are swapped) is at most 32. That keeps
the low-M per-token configurations from #5609 (kernel-N = M <= 32, which
only shift the S2T copy's smem source) and removes the faulting ones.
NVFP4 is unaffected in practice: `_rank_mm_fp4_autotune_tactics` already
demotes narrow tiles that cannot cover `prob_n`, so they never reached
the top-32 list.

## Root cause evidence (B200, upstream main 122037aa,
`sglang:26.07-py3`, cutlass-dsl 4.7.0)

Each tactic of the cute-dsl MXFP8 runner was launched in its own process
with `CUDA_LAUNCH_BLOCKING=1` and checked against `torch.mm` (cosine
similarity > 0.97):

| shape (m, n, k) | tile N 8/16/32, swap_ab=False (kernel-N = n) | tile
N 8/16/32, swap_ab=True (kernel-N = m) |
|---|---|---|
| 128, 8, 128 | pass (6/6 incl. cluster (2,1)/(4,1) at n=128 below:
fail) | fail, error 716 |
| 128, 16, 128 | pass | fail |
| 128, 32, 128 | pass (smem shifts of 128/256/384 B exercised) | fail |
| 128, 64, 128 | fail (TMEM column offset 1) | fail |
| 128, 128, 128 | fail (offsets 1..3) | fail |

All 120 tactics with tile N >= 64 pass; before #5609 the runner offered
exactly those 120. `compute-sanitizer --tool memcheck` reports
`Misaligned shared or local address` in the MMA warp (threads 128..159)
of `Sm100BlockScaledPersistentDenseGemmKernel` for the narrow tactics.

## Changes

- `flashinfer/gemm/kernels/dense_blockscaled_gemm_sm100.py`:
`can_implement` rejects `mma_tiler_mn[1] < 64` when `n > 32` (or the SFB
tile would be multicast), with the reason documented next to the
sub-tile addressing in the mainloop.
- `tests/gemm/test_mm_mxfp8.py`:
`test_mm_mxfp8_cute_dsl_narrow_tiles_only_within_32_tokens` asserts the
runner's tactic set (no kernel compile): no narrow tile for kernel-N >
32, narrow tiles only without the swap at `(128, 32)` and only with the
swap at `(32, 128)`.

## Validation

B200 (`sglang:26.07-py3`, cutlass-dsl 4.7.0), on this branch:

- `tests/gemm/test_mm_mxfp8.py -k "cute-dsl or cutedsl or
narrow_tiles"`: 508 passed (every cute-dsl `test_mm_mxfp8` case incl.
autotune, `test_mm_mxfp8_large_dimensions`, `cutedsl_low_latency`
small-M cases, the new tactic-set test); `-k "cutlass and False"`: 224
passed.
- Per-tactic probe on the patched tree: `(128, 128, 128)` offers no tile
narrower than 64; `(128, 32, 128)` offers `(128, 8/16/32)` without the
swap only and `(32, 128, 128)` with the swap only, all 6 pass with
correct results.
- FP4 regression (same kernel class): `tests/gemm/test_cake_mm_fp4.py`
26 passed; `tests/gemm/test_mm_fp4.py` run in progress on the patched
tree, result to be posted as a comment.
- `pre-commit run --files` on the two changed files: all hooks passed,
no reformatting.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved MXFP8 matrix multiplication tactic selection for narrow
dimensions. Unsupported narrow-tile configurations are no longer
selected when the output dimension exceeds the supported limit, while
valid configurations at the boundary remain available.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [08776e7](https://github.com/flashinfer-ai/flashinfer/commit/08776e742cf9b07154b36695947a7b6e11c3c29a)

- **作者**: eigen
- **时间**: 2026-10-01T21:02:53Z
- **提交信息**: refactor(cake_comm): retire the isolated MoE all-reduce fusion bundle; serve calls without the all-reduce output from the union (#5856)

Part of #5768; closes #5770 (step 5, the follow-up left open by #5849).

## What changes

Every `trtllm_moe_allreduce_fusion(backend="cake")` call now runs the
Cake all-reduce union. A call without `moe_allreduce_out` gets a scratch
tensor the union loader owns (`scratch_allreduce_output`: cached per
device and dtype, grown to the largest `token_num` seen, never cached
when allocated under CUDA-graph capture), so the union kernels, launcher
and route table are untouched. With that, the isolated source bundle
`csrc/cake_trtllm_moe_allreduce_fusion/` (reachable only for
`moe_allreduce_out=None` since #5514/#5599), its loader
`flashinfer/jit/cake_trtllm_moe_allreduce.py`, the
`get_cake_moe_allreduce_module` entry, the `.pre-commit-config.yaml`
exclude entry and the bundle's structure test are deleted.
`route_applies` loses its `emit_moe_allreduce` parameter.

Net: 9 files, +158 / −6,458 lines.
`csrc/cake_trtllm_moe_allreduce_union/` is byte-identical to main.

## Why the extra store is acceptable

The union kernels always write the all-reduce output; the scratch costs
one `[tokens, 7168]` store per call. Measured before deleting the
bundle, same node and container, interleaved arms, FlashInfer
`bench_gpu_time` with CUPTI per rank, row time = median over iterations
of the maximum over ranks, on the 30 ratified rows per architecture (10
shapes × world sizes 2/4/8):

Method: FlashInfer `bench_gpu_time(enable_cupti=True)` per rank with a
per-rank aggregate, row time = median over iterations of the maximum
over ranks; 3 interleaved blocks per row (legacy→union, union→legacy,
legacy→union), 10 warm-up + 30 timed iterations per block, one process
group per row, separate workspaces per arm, both arms launched with the
row's PDL setting; the legacy arm is the bundle of the parent commit
built from its two source files outside this PR. The default
per-iteration L2 flush was disabled for the table below: it issues a 250
MB memset plus a host sync per rank with no cross-rank barrier, and the
resulting launch skew is absorbed by ranks spinning in the Lamport
exchange (with the flush on, the same run still passes 29 of 30 rows
with geometric mean 0.64; the one outlier row showed two ranks at 23 µs
and two at 55 µs with the legacy arm also jumping to 55 µs in one
block).

### B300 (SM103), 8×B300 node, CUDA 13.1

30/30 rows: geometric mean of union/legacy = **0.643**, maximum =
**1.022** (`perf_ws8_bf16_t1_e8`, 11.01 → 11.25 µs); every other row
faster, large-token rows 1.6–3.4× faster.

<details><summary>B300 per-row table</summary>

| row | ws | dtype | PDL | T | experts | legacy µs | union+scratch µs |
ratio |
|---|---|---|---|---|---|---|---|---|
| perf_ws2_bf16_t1_e8 | 2 | bfloat16 | no | 1 | 8 | 8.38 | 7.78 | 0.9274
|
| perf_ws2_bf16_t64_e8_pdl | 2 | bfloat16 | yes | 64 | 8 | 13.09 | 10.37
| 0.7922 |
| perf_ws2_fp16_t64_e12 | 2 | float16 | no | 64 | 12 | 14.37 | 13.12 |
0.9132 |
| perf_ws2_bf16_t128_e16 | 2 | bfloat16 | no | 128 | 16 | 23.81 | 14.30
| 0.6008 |
| perf_ws2_fp16_t128_e16_pdl | 2 | float16 | yes | 128 | 16 | 22.77 |
14.27 | 0.6268 |
| perf_ws2_bf16_t256_e8 | 2 | bfloat16 | no | 256 | 8 | 32.90 | 16.66 |
0.5063 |
| perf_ws2_bf16_t256_e12_pdl | 2 | bfloat16 | yes | 256 | 12 | 37.10 |
18.96 | 0.5110 |
| perf_ws2_fp16_t2048_e8 | 2 | float16 | no | 2048 | 8 | 337.20 | 104.59
| 0.3102 |
| perf_ws2_bf16_t2048_e12_pdl | 2 | bfloat16 | yes | 2048 | 12 | 396.32
| 124.08 | 0.3131 |
| perf_ws2_fp16_t2048_e16_pdl | 2 | float16 | yes | 2048 | 16 | 454.05 |
135.28 | 0.2979 |
| perf_bf16_t1_e8 | 4 | bfloat16 | no | 1 | 8 | 10.19 | 9.76 | 0.9576 |
| perf_bf16_t64_e8_pdl | 4 | bfloat16 | yes | 64 | 8 | 17.44 | 16.14 |
0.9257 |
| perf_fp16_t64_e12 | 4 | float16 | no | 64 | 12 | 18.54 | 17.31 |
0.9335 |
| perf_bf16_t128_e16 | 4 | bfloat16 | no | 128 | 16 | 27.81 | 19.94 |
0.7169 |
| perf_fp16_t128_e16_pdl | 4 | float16 | yes | 128 | 16 | 37.22 | 22.53
| 0.6054 |
| perf_bf16_t256_e8 | 4 | bfloat16 | no | 256 | 8 | 45.33 | 31.97 |
0.7053 |
| perf_bf16_t256_e12_pdl | 4 | bfloat16 | yes | 256 | 12 | 51.39 | 32.11
| 0.6248 |
| perf_fp16_t2048_e8 | 4 | float16 | no | 2048 | 8 | 390.98 | 181.52 |
0.4643 |
| perf_bf16_t2048_e12_pdl | 4 | bfloat16 | yes | 2048 | 12 | 449.00 |
195.78 | 0.4360 |
| perf_fp16_t2048_e16_pdl | 4 | float16 | yes | 2048 | 16 | 517.62 |
240.08 | 0.4638 |
| perf_ws8_bf16_t1_e8 | 8 | bfloat16 | no | 1 | 8 | 11.01 | 11.25 |
1.0218 |
| perf_ws8_bf16_t64_e8_pdl | 8 | bfloat16 | yes | 64 | 8 | 27.36 | 25.01
| 0.9140 |
| perf_ws8_fp16_t64_e12 | 8 | float16 | no | 64 | 12 | 25.17 | 22.69 |
0.9015 |
| perf_ws8_bf16_t128_e16 | 8 | bfloat16 | no | 128 | 16 | 44.75 | 34.98
| 0.7816 |
| perf_ws8_fp16_t128_e16_pdl | 8 | float16 | yes | 128 | 16 | 41.79 |
36.00 | 0.8614 |
| perf_ws8_bf16_t256_e8 | 8 | bfloat16 | no | 256 | 8 | 81.33 | 57.18 |
0.7031 |
| perf_ws8_bf16_t256_e12_pdl | 8 | bfloat16 | yes | 256 | 12 | 82.78 |
62.75 | 0.7580 |
| perf_ws8_fp16_t2048_e8 | 8 | float16 | no | 2048 | 8 | 601.25 | 362.10
| 0.6022 |
| perf_ws8_bf16_t2048_e12_pdl | 8 | bfloat16 | yes | 2048 | 12 | 644.01
| 366.34 | 0.5688 |
| perf_ws8_fp16_t2048_e16_pdl | 8 | float16 | yes | 2048 | 16 | 631.83 |
385.22 | 0.6097 |

</details>

### B200 (SM100), 8×B200 node, CUDA 13.1

30/30 rows: geometric mean of union/legacy = **0.638**, maximum =
**0.997** (`perf_ws8_bf16_t1_e8`, 10.83 → 10.80 µs); every row at or
below the legacy time, large-token rows 1.6–3.4× faster.

<details><summary>B200 per-row table</summary>

| row | ws | dtype | PDL | T | experts | legacy µs | union+scratch µs |
ratio |
|---|---|---|---|---|---|---|---|---|
| perf_ws2_bf16_t1_e8 | 2 | bfloat16 | no | 1 | 8 | 8.86 | 8.10 | 0.9134
|
| perf_ws2_bf16_t64_e8_pdl | 2 | bfloat16 | yes | 64 | 8 | 12.85 | 10.74
| 0.8356 |
| perf_ws2_fp16_t64_e12 | 2 | float16 | no | 64 | 12 | 14.26 | 12.62 |
0.8855 |
| perf_ws2_bf16_t128_e16 | 2 | bfloat16 | no | 128 | 16 | 23.86 | 13.47
| 0.5647 |
| perf_ws2_fp16_t128_e16_pdl | 2 | float16 | yes | 128 | 16 | 22.72 |
13.68 | 0.6021 |
| perf_ws2_bf16_t256_e8 | 2 | bfloat16 | no | 256 | 8 | 33.36 | 16.61 |
0.4978 |
| perf_ws2_bf16_t256_e12_pdl | 2 | bfloat16 | yes | 256 | 12 | 37.63 |
17.47 | 0.4643 |
| perf_ws2_fp16_t2048_e8 | 2 | float16 | no | 2048 | 8 | 342.88 | 103.50
| 0.3019 |
| perf_ws2_bf16_t2048_e12_pdl | 2 | bfloat16 | yes | 2048 | 12 | 403.56
| 119.58 | 0.2963 |
| perf_ws2_fp16_t2048_e16_pdl | 2 | float16 | yes | 2048 | 16 | 464.46 |
136.64 | 0.2942 |
| perf_bf16_t1_e8 | 4 | bfloat16 | no | 1 | 8 | 9.92 | 9.86 | 0.9936 |
| perf_bf16_t64_e8_pdl | 4 | bfloat16 | yes | 64 | 8 | 16.58 | 14.38 |
0.8678 |
| perf_fp16_t64_e12 | 4 | float16 | no | 64 | 12 | 16.78 | 14.99 |
0.8932 |
| perf_bf16_t128_e16 | 4 | bfloat16 | no | 128 | 16 | 27.58 | 20.13 |
0.7297 |
| perf_fp16_t128_e16_pdl | 4 | float16 | yes | 128 | 16 | 26.85 | 20.03
| 0.7461 |
| perf_bf16_t256_e8 | 4 | bfloat16 | no | 256 | 8 | 44.80 | 30.90 |
0.6896 |
| perf_bf16_t256_e12_pdl | 4 | bfloat16 | yes | 256 | 12 | 49.71 | 32.03
| 0.6443 |
| perf_fp16_t2048_e8 | 4 | float16 | no | 2048 | 8 | 395.88 | 181.13 |
0.4575 |
| perf_bf16_t2048_e12_pdl | 4 | bfloat16 | yes | 2048 | 12 | 453.88 |
199.41 | 0.4393 |
| perf_fp16_t2048_e16_pdl | 4 | float16 | yes | 2048 | 16 | 521.82 |
233.96 | 0.4484 |
| perf_ws8_bf16_t1_e8 | 8 | bfloat16 | no | 1 | 8 | 10.83 | 10.80 |
0.9970 |
| perf_ws8_bf16_t64_e8_pdl | 8 | bfloat16 | yes | 64 | 8 | 24.53 | 22.53
| 0.9185 |
| perf_ws8_fp16_t64_e12 | 8 | float16 | no | 64 | 12 | 23.63 | 21.89 |
0.9262 |
| perf_ws8_bf16_t128_e16 | 8 | bfloat16 | no | 128 | 16 | 44.66 | 33.73
| 0.7553 |
| perf_ws8_fp16_t128_e16_pdl | 8 | float16 | yes | 128 | 16 | 41.34 |
32.98 | 0.7976 |
| perf_ws8_bf16_t256_e8 | 8 | bfloat16 | no | 256 | 8 | 80.09 | 62.54 |
0.7809 |
| perf_ws8_bf16_t256_e12_pdl | 8 | bfloat16 | yes | 256 | 12 | 83.66 |
61.77 | 0.7384 |
| perf_ws8_fp16_t2048_e8 | 8 | float16 | no | 2048 | 8 | 613.39 | 377.39
| 0.6153 |
| perf_ws8_bf16_t2048_e12_pdl | 8 | bfloat16 | yes | 2048 | 12 | 656.12
| 364.60 | 0.5557 |
| perf_ws8_fp16_t2048_e16_pdl | 8 | float16 | yes | 2048 | 16 | 645.53 |
372.81 | 0.5775 |

</details>

## Tests

| GPU | `test_cake_moe_allreduce_api.py` +
`test_cake_moe_allreduce_union.py` (CPU) |
`test_cake_moe_allreduce_distributed.py` tp2/tp4/tp8 × fp16/bf16
(no-output rows at T=1, 64, 2048, eager + graph) | pre-commit |
|---|---|---|---|
| B300 (SM103) | 69 passed | 6 passed | ruff 0.12.8 check + format clean
|
| B200 (SM100) | 69 passed | 6 passed | ruff 0.12.8 check + format clean
|

New CPU tests: the no-output call reaches the union with
`moe_allreduce_out=None`; the scratch is cached per device/dtype, reused
for smaller token counts and grown once for larger ones.

## Environment note

Both nodes ran the distributed test with `TORCH_SYMMMEM=NVSHMEM` (the
default symmetric-memory provider fails in
`trtllm_create_ipc_workspace_for_all_reduce_fusion` on these containers,
unrelated to this change).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Cake MoE all-reduce now supports calls that omit the all-reduce output
tensor, using a scratch output instead.
* Scratch outputs can be reused for smaller requests and resized for
larger ones. Requests with different data types or devices use separate
scratch outputs.
* **Improvements**
* Cake MoE all-reduce routing now uses the union implementation across
its supported GPU architectures and world sizes, including
configurations previously handled by a separate implementation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6ea003e](https://github.com/flashinfer-ai/flashinfer/commit/6ea003e705cb6a9fd473432d3d8f4c6a9f76574c)

- **作者**: eigen
- **时间**: 2026-10-01T20:54:29Z
- **提交信息**: perf(cake_mm_fp4): half-M pair tile for the narrow-N 2-CTA rows of the per-token NVFP4 route (sm_100a, sm_103a) (#5869)

<!-- .github/pull_request_template.md -->

## 📌 Description

Tactic-rule and program update of the experimental `backend="cake"`
per-token NVFP4 route (#5744 → #5697): one measured lever on the host
tactic rules and the generated 2-CTA programs, no public API, default or
backend-semantics change, no approximation; every GEMM output is bitwise
identical to the merged route on every measured row and the quantizer
programs are unchanged.

**Half-M pair tile for the narrow-N 64-wide 2-CTA rows (`half_m`).** The
merged route runs 7168x2112 / 7168x1536 at M = 128..257 as one 2x64 pair
tile per weight tile; the pair's second CTA streams a zero-filled A
half, so each CTA moves 16 KB per K step for 12 KB of real data. The new
program is a `tcgen05.mma.cta_group::2` M = 128 pair (64 token rows per
CTA): 12 KB per CTA per step, Layout-B accumulator / epilogue, and the
2x2 block-scale TMEM layout. The scale words the two CTAs need sit 4 / 8
B inside the 16 B lane chunks of the 128x4 scale layout (no TMA box or
`tcgen05.cp` descriptor can address them), so a gather warp moves them
with register-path `cp.async` whose completion arrives on the stage
barrier itself (`cp.async.mbarrier.arrive.noinc`); the peer's otherwise
idle MMA warp publishes the stage with `fence.proxy.async` and a
CTA-scope arrival. The 64-row MMA keeps one accumulation chain per
output, so the rows stay bitwise. Under programmatic dependent launch
the gather warp waits on the grid dependency before its first copy of
the preceding quantizer's scale words (the loader's TMA already did),
and the peer CTA signals `launch_dependents` after its last publication.
Rule: the 64-wide 2-CTA tiles of the narrow-N rows (≤ 40 weight tiles,
no CLC / grouped raster) take the half-M pair while `ceil(M/64) × weight
tiles ≤ 1.5 × pairs`: 7168x2112 M = 128 / 130 (66 / 99 half tiles on 74
/ 76 pairs) and 7168x1536 M = 128 / 130 (48) do; 7168x1536 M = 257 (120
tiles, 1.6 waves: +2.5-3.4 % as a GEMM alone but 0.979-0.990 in the
quantize + GEMM chain on both GPUs) and 7168x2112 M = 257 (165 tiles,
2.2 waves, 0.75 alone) keep the 2x64 pair.

Regenerated programs: every 2-CTA program (the two flat scale tensors
are two more arguments of the 2-CTA kernels) and the new
`m64_2cta_hm_{bf16,f16}_bF_l2256b` programs on both arches; the 1-CTA,
n-orientation, split-K and quantizer programs are unchanged. Both
exports (B200 sm_100a and GB300 sm_103a) produced the byte-identical
registry.

## Baselines and their source PRs

- #5744 (merged): tactic rules and regenerated programs of the
`backend="cake"` per-token route — **progress baseline** (arm A of the
progress tables: its generated programs and host rules, launched by the
merged backend).
- #5697 (merged; `flashinfer/experimental/cake_nvfp4_per_token`): the
`backend="cake"` per-token route itself.
- #5609 `97b3bd80` (merged): CuTe-DSL per-token kernel optimisations;
`backend="cute-dsl"` with the untuned default tactic is the **threshold
baseline** of the threshold tables.
- #5504 `7d967939` (merged): per-token alpha `mm_fp4` + `out_scale` fold
in per-token `nvfp4_quantize` (the API both routes implement).

## Methodology

Container `sglang:26.07-py3`, single tenant, cold L2 (persisting lines
reset before each flush), CUPTI kernel spans, 100 iterations per timing,
≥ 6 paired rounds per row with the arm order alternated (rows in the
0.995-1.00 band re-measured to 12 rounds); per row min / median /
geomean; acceptance statistic = min-of-round-medians ratio (GEMM, fused)
and per-round medians (quantize); fused = quantize + GEMM GPU time with
PDL, CUDA Graph replay primary, eager secondary. Correctness per row:
quantizer outputs bitwise vs the merged route; GEMM outputs bitwise vs
the merged route (no accumulation-order change shipped) and within atol
= rtol = 1e-2 of the FP32 dequantized reference;
`test_mm_fp4_per_token_alpha` criteria per row. compute-sanitizer
memcheck + synccheck 0 errors on the new programs (both GPUs).

## Results


### Speedup summary

| table | GPU | vs #5744 (merged cake route) | vs cute-dsl per-token
(untuned default) |
|---|---|---|---|
| GEMM per-token | B200 | bf16 1.0020 (min 0.9970, n=80) / fp16 1.0016
(min 0.9951, n=80) | bf16 1.0576 (min 0.9893, n=80) / fp16 1.0574 (min
0.9964, n=80) |
| GEMM per-token | GB300 | bf16 1.0023 (min 0.9965, n=80) / fp16 1.0022
(min 0.9949, n=80) | bf16 1.0534 (min 0.9980, n=80) / fp16 1.0531 (min
0.9990, n=80) |
| Fused quantize + GEMM chain | B200 | bf16 1.0026 (min 0.9948, n=80) /
fp16 1.0020 (min 0.9897, n=80) | bf16 1.0889 (min 1.0099, n=80) |
| Fused quantize + GEMM chain | GB300 | bf16 1.0015 (min 0.9950, n=80) /
fp16 1.0017 (min 0.9915, n=80) | bf16 1.0907 (min 1.0071, n=80) |
| Quantize kernel | B200 | bf16 1.0005 (min 0.9961, n=100) / fp16 1.0014
(min 1.0000, n=8) | bf16 1.1256 (min 1.0110, n=100) / fp16 1.1156 (min
1.0632, n=8) |
| Quantize kernel | GB300 | bf16 1.0006 (min 0.9889, n=100) / fp16
1.0005 (min 1.0000, n=8) | bf16 1.1231 (min 1.0115, n=100) / fp16 1.1123
(min 1.0638, n=8) |

Statistic per cell: geometric mean of the per-row acceptance statistic
(min-of-round-medians ratio for GEMM and fused, median of round medians
for the quantizer) over the perf rows; rows below the band were
re-measured at 12 rounds and carry that reading. Per-row min / median /
geomean and the roofline share are in the tables below (B200 first, then
GB300). Rows at or below parity after the 12-round rechecks, all
unchanged programs with bitwise-equal outputs: vs #5744 — GB300 GEMM
fp16 7168x2112 M=17 0.9949 (one 32 ns CUPTI tick on a 6.2 us row), GB300
fused fp16 7168x2112 M=1 / M=17 0.9915 / 0.9918 and B200 fused bf16
8192x8192 M=1 0.9948 (two ticks; a null A/B with the #5744 programs in
both arms reads the same rows at 0.9957 / 0.9959 / 0.9897), GB300
quantizer K=7168 M=128 0.9889 (one tick on a 2.85 us row; null
identical), B200 fused fp16 16384x7168 M=8192 0.9897 (second-slot band
of the 350 us persistent rows; null 0.9944; GEMM alone 1.0000 / 0.9968);
vs cute-dsl — GB300 GEMM 7168x18432 M=8192 0.9980 / 0.9990 with both
arms at 90.7 % of the measured dense-FP4 peak, and B200 GEMM 7168x18432
M=128 0.9893 / 0.9964 where the same program reads 1.0074 / 1.0145 on
the NVRTC source arm and 1.0298 in the export protocol (measurement-path
spread larger than the gap; seven structural variants screened, none
better).

### Quantize table

**B200**

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5744: bf16 rows 100, geomean 1.0005, min 0.9961, rows <= 1.00: 83;
fp16 (8 registered rows) rows 8, geomean 1.0014, min 1.0000, rows <=
1.00: 7. vs cute-dsl: bf16 rows 100, geomean 1.1256, min 1.0110, rows <=
1.00: 0; fp16 rows 8, geomean 1.1156, min 1.0632, rows <= 1.00: 0

|K|M|fold|vs #5744 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/1.002)|1.202(1.202/1.202)|LB 1.8f|
|7168|1|1|1.000(1.000/1.000)|1.169(1.169/1.171)|LB 1.8f|
|7168|8|0|1.000(1.000/0.998)|1.175(1.175/1.175)|LB 1.8f|
|7168|8|1|1.000(1.000/1.001)|1.096(1.096/1.098)|LB 1.8f|
|7168|17|0|1.000(1.000/0.999)|1.096(1.096/1.098)|LB 1.8f|
|7168|17|1|1.000(1.000/1.000)|1.139(1.139/1.137)|LB 1.8f|
|7168|32|0|1.000(1.000/0.997)|1.082(1.082/1.090)|LB 1.8f|
|7168|32|1|1.000(1.000/0.999)|1.095(1.095/1.095)|LB 1.8f|
|7168|128|0|1.000(1.000/1.002)|1.088(1.088/1.094)|13%h 2.0f|
|7168|128|1|1.000(1.000/0.994)|1.087(1.087/1.090)|13%h 2.0f|
|7168|130|0|1.000(1.000/0.997)|1.086(1.086/1.085)|13%h 2.0f|
|7168|130|1|1.000(1.000/1.000)|1.096(1.096/1.090)|13%h 2.0f|
|7168|257|0|1.000(1.000/1.001)|1.063(1.063/1.065)|21%h 2.4f|
|7168|257|1|1.000(1.000/1.001)|1.063(1.063/1.069)|21%h 2.4f|
|7168|512|0|1.000(1.000/1.001)|1.062(1.062/1.061)|32%h 3.2f|
|7168|512|1|1.007(1.007/1.002)|1.076(1.076/1.078)|32%h 3.1f|
|7168|2048|0|0.996(0.996/0.997)|1.281(1.281/1.282)|64%h|
|7168|2048|1|1.003(1.003/1.003)|1.337(1.337/1.340)|64%h|
|7168|8192|0|0.996(0.996/0.997)|1.153(1.153/1.152)|95%h|
|7168|8192|1|1.000(1.000/0.999)|1.181(1.181/1.181)|94%h|
|8192|1|0|1.000(1.000/1.000)|1.186(1.186/1.184)|LB 1.9f|
|8192|1|1|1.000(1.000/1.000)|1.198(1.198/1.198)|LB 1.8f|
|8192|8|0|1.000(1.000/1.000)|1.094(1.094/1.094)|LB 1.9f|
|8192|8|1|1.000(1.000/1.001)|1.093(1.093/1.095)|LB 1.9f|
|8192|17|0|1.000(1.000/1.001)|1.070(1.070/1.071)|LB 1.9f|
|8192|17|1|1.000(1.000/0.999)|1.070(1.070/1.071)|LB 1.9f|
|8192|32|0|1.000(1.000/1.000)|1.081(1.081/1.072)|LB 1.9f|
|8192|32|1|1.000(1.000/1.001)|1.057(1.057/1.060)|LB 1.9f|
|8192|128|0|1.010(1.010/1.002)|1.074(1.074/1.074)|14%h 2.0f|
|8192|128|1|1.000(1.000/0.997)|1.073(1.073/1.077)|14%h 2.1f|
|8192|130|0|1.000(1.000/1.000)|1.104(1.104/1.102)|14%h 2.1f|
|8192|130|1|1.000(1.000/1.001)|1.072(1.072/1.077)|14%h 2.1f|
|8192|257|0|1.000(1.000/0.999)|1.051(1.051/1.052)|23%h 2.5f|
|8192|257|1|1.000(1.000/0.998)|1.042(1.042/1.044)|22%h 2.6f|
|8192|512|0|1.000(1.000/1.002)|1.058(1.058/1.058)|34%h 3.4f|
|8192|512|1|1.000(1.000/1.000)|1.045(1.045/1.045)|34%h 3.4f|
|8192|2048|0|1.000(1.000/0.999)|1.183(1.183/1.187)|65%h|
|8192|2048|1|1.003(1.003/1.001)|1.194(1.194/1.192)|64%h|
|8192|8192|0|1.001(1.001/1.000)|1.149(1.149/1.147)|97%h|
|8192|8192|1|1.000(1.000/1.000)|1.143(1.143/1.144)|98%h|
|16384|1|0|1.000(1.000/1.001)|1.165(1.165/1.160)|LB 2.1f|
|16384|1|1|1.000(1.000/1.002)|1.109(1.109/1.105)|LB 2.2f|
|16384|8|0|1.000(1.000/1.000)|1.113(1.113/1.112)|LB 2.2f|
|16384|8|1|1.000(1.000/0.999)|1.112(1.112/1.113)|LB 2.1f|
|16384|17|0|1.000(1.000/1.001)|1.081(1.081/1.080)|LB 2.2f|
|16384|17|1|1.000(1.000/0.998)|1.071(1.071/1.066)|LB 2.2f|
|16384|32|0|1.000(1.000/1.001)|1.038(1.038/1.043)|LB 2.2f|
|16384|32|1|1.009(1.009/1.002)|1.079(1.079/1.075)|LB 2.2f|
|16384|128|0|1.000(1.000/1.002)|1.048(1.048/1.046)|21%h 2.7f|
|16384|128|1|1.000(1.000/0.999)|1.041(1.041/1.039)|21%h 2.7f|
|16384|130|0|1.000(1.000/0.999)|1.062(1.062/1.061)|21%h 2.8f|
|16384|130|1|1.000(1.000/1.000)|1.048(1.048/1.048)|21%h 2.8f|
|16384|257|0|1.000(1.000/1.001)|1.042(1.042/1.041)|32%h 3.6f|
|16384|257|1|1.006(1.006/1.001)|1.025(1.025/1.022)|33%h 3.5f|
|16384|512|0|1.000(1.000/1.003)|1.170(1.170/1.172)|45%h 5.0f|
|16384|512|1|1.000(1.000/0.998)|1.178(1.178/1.180)|46%h 5.0f|
|16384|2048|0|0.998(0.998/0.998)|1.475(1.475/1.475)|81%h|
|16384|2048|1|1.000(1.000/0.998)|1.439(1.439/1.437)|79%h|
|16384|8192|0|1.001(1.001/1.000)|1.340(1.340/1.341)|101%h|
|16384|8192|1|1.000(1.000/1.000)|1.338(1.338/1.339)|100%h|
|18432|1|0|1.000(1.000/0.999)|1.158(1.158/1.152)|LB 2.2f|
|18432|1|1|1.000(1.000/1.000)|1.152(1.152/1.147)|LB 2.3f|
|18432|8|0|1.000(1.000/0.998)|1.160(1.160/1.159)|LB 2.2f|
|18432|8|1|1.000(1.000/1.000)|1.095(1.095/1.100)|LB 2.2f|
|18432|17|0|1.000(1.000/0.997)|1.108(1.108/1.104)|LB 2.2f|
|18432|17|1|1.000(1.000/1.000)|1.094(1.094/1.097)|LB 2.3f|
|18432|32|0|1.000(1.000/1.002)|1.056(1.056/1.062)|LB 2.3f|
|18432|32|1|1.000(1.000/0.996)|1.105(1.105/1.104)|LB 2.3f|
|18432|128|0|1.008(1.008/1.001)|1.047(1.047/1.049)|23%h 2.8f|
|18432|128|1|1.000(1.000/0.999)|1.046(1.046/1.047)|22%h 2.9f|
|18432|130|0|1.000(1.000/1.002)|1.043(1.043/1.046)|22%h 3.0f|
|18432|130|1|1.000(1.000/0.998)|1.045(1.045/1.049)|20%h 3.2f|
|18432|257|0|1.000(1.000/1.000)|1.029(1.029/1.030)|34%h 3.8f|
|18432|257|1|1.000(1.000/1.000)|1.011(1.011/1.013)|32%h 4.0f|
|18432|512|0|1.000(1.000/1.002)|1.182(1.182/1.183)|49%h 5.3f|
|18432|512|1|1.000(1.000/1.001)|1.237(1.237/1.235)|49%h 5.3f|
|18432|2048|0|1.000(1.000/1.000)|1.481(1.481/1.482)|84%h|
|18432|2048|1|0.998(0.998/0.999)|1.470(1.470/1.469)|82%h|
|18432|8192|0|1.001(1.001/1.000)|1.081(1.081/1.081)|100%h|
|18432|8192|1|1.000(1.000/1.000)|1.064(1.064/1.064)|100%h|
|28672|1|0|1.000(1.000/0.999)|1.173(1.173/1.174)|LB 2.5f|
|28672|1|1|1.000(1.000/1.001)|1.207(1.207/1.203)|LB 2.5f|
|28672|8|0|1.000(1.000/1.000)|1.175(1.175/1.173)|LB 2.5f|
|28672|8|1|1.009(1.009/1.004)|1.181(1.181/1.174)|LB 2.5f|
|28672|17|0|1.000(1.000/1.000)|1.119(1.119/1.121)|LB 2.6f|
|28672|17|1|1.000(1.000/1.002)|1.141(1.141/1.134)|LB 2.6f|
|28672|32|0|1.000(1.000/1.000)|1.098(1.098/1.099)|LB 2.7f|
|28672|32|1|1.000(1.000/0.997)|1.120(1.120/1.125)|LB 2.7f|
|28672|128|0|1.000(1.000/1.000)|1.050(1.050/1.050)|29%h 3.5f|
|28672|128|1|1.000(1.000/0.999)|1.069(1.069/1.069)|29%h 3.4f|
|28672|130|0|1.000(1.000/1.000)|1.047(1.047/1.045)|27%h 3.7f|
|28672|130|1|1.000(1.000/1.001)|1.068(1.068/1.066)|27%h 3.7f|
|28672|257|0|1.000(1.000/1.000)|1.018(1.018/1.017)|41%h 4.9f|
|28672|257|1|1.000(1.000/0.999)|1.058(1.058/1.059)|41%h 4.9f|
|28672|512|0|1.006(1.006/1.003)|1.134(1.134/1.133)|55%h|
|28672|512|1|1.000(1.000/1.001)|1.149(1.149/1.151)|54%h|
|28672|2048|0|1.001(1.001/1.001)|1.309(1.309/1.308)|89%h|
|28672|2048|1|1.001(1.001/1.001)|1.317(1.317/1.316)|88%h|
|28672|8192|0|1.000(1.000/1.000)|1.110(1.110/1.110)|100%h|
|28672|8192|1|1.000(1.000/1.000)|1.117(1.117/1.117)|100%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5744 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/1.002)|1.108(1.108/1.104)|
|7168|17|0|1.000(1.000/1.003)|1.098(1.098/1.096)|
|7168|32|0|1.000(1.000/1.001)|1.096(1.096/1.103)|
|7168|128|0|1.011(1.011/1.003)|1.100(1.100/1.100)|
|7168|130|0|1.000(1.000/1.001)|1.063(1.063/1.067)|
|7168|257|0|1.000(1.000/0.999)|1.073(1.073/1.074)|
|7168|512|0|1.000(1.000/0.999)|1.070(1.070/1.069)|
|7168|2048|0|1.000(1.000/1.001)|1.341(1.341/1.337)|



**GB300**

#### Quantize kernel (fold = out_scale folded into the per-token scale)
— vs #5744: bf16 rows 100, geomean 1.0006, min 0.9889, rows <= 1.00: 85;
fp16 (8 registered rows) rows 8, geomean 1.0005, min 1.0000, rows <=
1.00: 7. vs cute-dsl: bf16 rows 100, geomean 1.1231, min 1.0115, rows <=
1.00: 0; fp16 rows 8, geomean 1.1123, min 1.0638, rows <= 1.00: 0

|K|M|fold|vs #5744 bf16|vs cute-dsl bf16|roof|
|---|---|---|---|---|---|
|7168|1|0|1.000(1.000/1.001)|1.207(1.207/1.209)|LB 2.1f|
|7168|1|1|1.000(1.000/1.000)|1.188(1.188/1.183)|LB 2.1f|
|7168|8|0|1.000(1.000/1.000)|1.165(1.165/1.162)|LB 2.1f|
|7168|8|1|1.000(1.000/1.000)|1.122(1.122/1.117)|LB 2.1f|
|7168|17|0|1.000(1.000/1.002)|1.098(1.098/1.100)|LB 2.1f|
|7168|17|1|1.000(1.000/1.000)|1.141(1.141/1.143)|LB 2.1f|
|7168|32|0|1.000(1.000/1.003)|1.110(1.110/1.107)|LB 2.1f|
|7168|32|1|1.000(1.000/1.000)|1.098(1.098/1.100)|LB 2.1f|
|7168|128|0|0.989(0.989/0.996)|1.089(1.089/1.092)|12%h 2.3f|
|7168|128|1|1.000(1.000/0.998)|1.100(1.100/1.099)|12%h 2.3f|
|7168|130|0|1.000(1.000/1.000)|1.100(1.100/1.098)|12%h 2.3f|
|7168|130|1|1.000(1.000/1.002)|1.099(1.099/1.096)|12%h 2.4f|
|7168|257|0|1.000(1.000/1.002)|1.055(1.055/1.055)|20%h 2.8f|
|7168|257|1|1.000(1.000/1.001)|1.064(1.064/1.069)|20%h 2.8f|
|7168|512|0|1.000(1.000/1.000)|1.072(1.072/1.072)|31%h 3.6f|
|7168|512|1|1.000(1.000/0.999)|1.072(1.072/1.072)|30%h 3.7f|
|7168|2048|0|1.000(1.000/1.002)|1.319(1.319/1.316)|65%h|
|7168|2048|1|1.004(1.004/1.001)|1.288(1.288/1.287)|63%h|
|7168|8192|0|1.000(1.000/1.000)|1.157(1.157/1.157)|93%h|
|7168|8192|1|0.999(0.999/0.998)|1.170(1.170/1.171)|93%h|
|8192|1|0|1.000(1.000/1.000)|1.190(1.190/1.187)|LB 2.2f|
|8192|1|1|1.000(1.000/1.000)|1.193(1.193/1.196)|LB 2.1f|
|8192|8|0|1.000(1.000/1.000)|1.082(1.082/1.086)|LB 2.2f|
|8192|8|1|1.000(1.000/1.000)|1.094(1.094/1.089)|LB 2.2f|
|8192|17|0|1.000(1.000/1.000)|1.083(1.083/1.082)|LB 2.2f|
|8192|17|1|1.000(1.000/1.000)|1.083(1.083/1.073)|LB 2.1f|
|8192|32|0|1.000(1.000/1.000)|1.071(1.071/1.070)|LB 2.2f|
|8192|32|1|1.000(1.000/1.000)|1.082(1.082/1.080)|LB 2.2f|
|8192|128|0|1.000(1.000/1.004)|1.064(1.064/1.064)|13%h 2.4f|
|8192|128|1|1.000(1.000/1.003)|1.075(1.075/1.078)|13%h 2.4f|
|8192|130|0|1.000(1.000/0.998)|1.074(1.074/1.072)|13%h 2.4f|
|8192|130|1|1.011(1.011/1.002)|1.084(1.084/1.082)|13%h 2.4f|
|8192|257|0|1.000(1.000/1.001)|1.043(1.043/1.045)|22%h 3.0f|
|8192|257|1|1.000(1.000/1.000)|1.052(1.052/1.051)|22%h 3.0f|
|8192|512|0|1.000(1.000/1.000)|1.067(1.067/1.067)|33%h 3.9f|
|8192|512|1|1.000(1.000/0.999)|1.039(1.039/1.037)|33%h 3.9f|
|8192|2048|0|1.006(1.006/1.006)|1.184(1.184/1.184)|63%h|
|8192|2048|1|1.000(1.000/1.001)|1.168(1.168/1.170)|64%h|
|8192|8192|0|1.000(1.000/1.001)|1.162(1.162/1.164)|95%h|
|8192|8192|1|1.001(1.001/1.001)|1.168(1.168/1.168)|95%h|
|16384|1|0|1.000(1.000/0.998)|1.183(1.183/1.178)|LB 2.4f|
|16384|1|1|1.000(1.000/1.000)|1.110(1.110/1.108)|LB 2.5f|
|16384|8|0|1.010(1.010/1.002)|1.129(1.129/1.129)|LB 2.5f|
|16384|8|1|1.000(1.000/1.000)|1.137(1.137/1.137)|LB 2.5f|
|16384|17|0|1.000(1.000/1.003)|1.083(1.083/1.089)|LB 2.5f|
|16384|17|1|1.000(1.000/0.999)|1.082(1.082/1.085)|LB 2.5f|
|16384|32|0|1.000(1.000/1.000)|1.070(1.070/1.061)|LB 2.5f|
|16384|32|1|1.010(1.010/1.002)|1.081(1.081/1.089)|LB 2.5f|
|16384|128|0|1.000(1.000/1.001)|1.042(1.042/1.043)|21%h 3.0f|
|16384|128|1|1.000(1.000/0.999)|1.041(1.041/1.044)|21%h 3.1f|
|16384|130|0|1.000(1.000/1.001)|1.049(1.049/1.047)|20%h 3.2f|
|16384|130|1|1.000(1.000/1.001)|1.040(1.040/1.041)|21%h 3.1f|
|16384|257|0|1.000(1.000/1.001)|1.043(1.043/1.041)|31%h 4.1f|
|16384|257|1|1.000(1.000/1.000)|1.025(1.025/1.023)|32%h 4.1f|
|16384|512|0|1.000(1.000/1.001)|1.128(1.128/1.130)|44%h 5.8f|
|16384|512|1|1.000(1.000/1.000)|1.169(1.169/1.166)|45%h 5.7f|
|16384|2048|0|1.002(1.002/1.002)|1.416(1.416/1.418)|78%h|
|16384|2048|1|0.998(0.998/1.000)|1.372(1.372/1.374)|76%h|
|16384|8192|0|1.000(1.000/1.000)|1.318(1.318/1.317)|98%h|
|16384|8192|1|0.999(0.999/1.000)|1.324(1.324/1.324)|97%h|
|18432|1|0|1.000(1.000/0.999)|1.143(1.143/1.147)|LB 2.5f|
|18432|1|1|1.000(1.000/1.001)|1.149(1.149/1.151)|LB 2.7f|
|18432|8|0|1.000(1.000/0.998)|1.121(1.121/1.120)|LB 2.5f|
|18432|8|1|1.010(1.010/1.004)|1.120(1.120/1.123)|LB 2.6f|
|18432|17|0|1.000(1.000/1.001)|1.101(1.101/1.097)|LB 2.6f|
|18432|17|1|1.000(1.000/1.004)|1.097(1.097/1.094)|LB 2.6f|
|18432|32|0|1.000(1.000/0.998)|1.078(1.078/1.079)|LB 2.6f|
|18432|32|1|1.010(1.010/1.003)|1.087(1.087/1.087)|LB 2.7f|
|18432|128|0|1.000(1.000/1.000)|1.031(1.031/1.029)|22%h 3.2f|
|18432|128|1|1.000(1.000/1.000)|1.039(1.039/1.043)|22%h 3.3f|
|18432|130|0|1.000(1.000/1.001)|1.069(1.069/1.069)|22%h 3.3f|
|18432|130|1|1.000(1.000/0.999)|1.038(1.038/1.036)|22%h 3.3f|
|18432|257|0|1.000(1.000/1.000)|1.029(1.029/1.030)|32%h 4.5f|
|18432|257|1|1.000(1.000/1.000)|1.011(1.011/1.011)|31%h 4.6f|
|18432|512|0|1.000(1.000/1.000)|1.185(1.185/1.182)|47%h|
|18432|512|1|1.004(1.004/1.002)|1.208(1.208/1.207)|47%h|
|18432|2048|0|0.998(0.998/0.998)|1.423(1.423/1.425)|81%h|
|18432|2048|1|1.000(1.000/0.999)|1.402(1.402/1.402)|79%h|
|18432|8192|0|1.001(1.001/1.000)|1.078(1.078/1.078)|97%h|
|18432|8192|1|0.999(0.999/0.999)|1.067(1.067/1.066)|96%h|
|28672|1|0|1.000(1.000/1.000)|1.193(1.193/1.191)|LB 2.9f|
|28672|1|1|1.000(1.000/0.999)|1.193(1.193/1.194)|LB 2.9f|
|28672|8|0|1.000(1.000/1.000)|1.173(1.173/1.168)|LB 2.9f|
|28672|8|1|1.000(1.000/0.999)|1.175(1.175/1.179)|LB 2.9f|
|28672|17|0|1.000(1.000/1.000)|1.124(1.124/1.119)|LB 2.9f|
|28672|17|1|1.000(1.000/1.000)|1.155(1.155/1.153)|LB 3.0f|
|28672|32|0|1.000(1.000/1.001)|1.101(1.101/1.097)|LB 3.1f|
|28672|32|1|1.000(1.000/1.001)|1.125(1.125/1.122)|LB 3.1f|
|28672|128|0|1.007(1.007/1.003)|1.038(1.038/1.041)|29%h 3.9f|
|28672|128|1|1.000(1.000/0.999)|1.071(1.071/1.069)|28%h 3.9f|
|28672|130|0|1.000(1.000/0.998)|1.055(1.055/1.055)|26%h 4.3f|
|28672|130|1|1.006(1.006/1.000)|1.018(1.018/1.017)|27%h 4.3f|
|28672|257|0|1.000(1.000/1.000)|1.014(1.014/1.011)|40%h 5.6f|
|28672|257|1|1.000(1.000/1.000)|1.060(1.060/1.061)|40%h 5.5f|
|28672|512|0|1.000(1.000/0.999)|1.108(1.108/1.105)|53%h|
|28672|512|1|1.000(1.000/0.999)|1.129(1.129/1.131)|52%h|
|28672|2048|0|0.999(0.999/0.999)|1.268(1.268/1.268)|85%h|
|28672|2048|1|1.001(1.001/1.000)|1.324(1.324/1.324)|86%h|
|28672|8192|0|1.000(1.000/1.000)|1.114(1.114/1.114)|97%h|
|28672|8192|1|1.001(1.001/1.001)|1.109(1.109/1.109)|97%h|

fp16 activations (the registered fp16 quantizer rows):

|K|M|fold|vs #5744 fp16|vs cute-dsl fp16|
|---|---|---|---|---|
|7168|8|0|1.000(1.000/1.001)|1.123(1.123/1.123)|
|7168|17|0|1.000(1.000/1.000)|1.073(1.073/1.073)|
|7168|32|0|1.000(1.000/0.999)|1.099(1.099/1.097)|
|7168|128|0|1.000(1.000/1.001)|1.102(1.102/1.103)|
|7168|130|0|1.000(1.000/0.999)|1.100(1.100/1.094)|
|7168|257|0|1.000(1.000/0.999)|1.074(1.074/1.074)|
|7168|512|0|1.000(1.000/1.001)|1.064(1.064/1.061)|
|7168|2048|0|1.004(1.004/1.002)|1.277(1.277/1.277)|


### GEMM table

**B200**

#### GEMM per-token — vs #5744: bf16 rows 80, geomean 1.0020, min
0.9970, rows <= 1.00: 48; fp16 rows 80, geomean 1.0016, min 0.9951, rows
<= 1.00: 56. vs cute-dsl: bf16 rows 80, geomean 1.0576, min 0.9893, rows
<= 1.00: 1; fp16 rows 80, geomean 1.0574, min 0.9964, rows <= 1.00: 1

|K|N|M|tactic|vs #5744 bf16|vs #5744 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1*|n8sk4|1.000(1.000/1.000)|1.005(1.000/1.000)|1.027(1.027/1.025)|1.027(1.027/1.028)|22%h
4.1f|

|7168|2112|8*|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.021(1.021/1.019)|1.021(1.026/1.022)|22%h
4.1f|

|7168|2112|17*|n8sk2|1.005(0.995/0.999)|0.995(1.000/0.999)|1.025(1.029/1.027)|1.030(1.025/1.026)|21%h
4.4f|

|7168|2112|32*|n8sk2|1.000(1.000/0.998)|1.005(1.000/1.001)|1.029(1.034/1.032)|1.034(1.034/1.032)|21%h
4.4f|

|7168|2112|128*|2xm64|1.037(1.041/1.039)|1.037(1.041/1.038)|1.086(1.090/1.089)|1.086(1.086/1.087)|19%h
5.3f|

|7168|2112|130*|2xm64|1.028(1.028/1.030)|1.028(1.032/1.031)|1.081(1.077/1.079)|1.077(1.077/1.078)|19%h
5.4f|

|7168|2112|257*|2xm64|1.004(1.000/1.001)|1.000(1.000/0.999)|1.046(1.046/1.045)|1.050(1.046/1.047)|20%h
5.6f|

|7168|2112|512*|2xm64|1.004(1.000/1.001)|0.996(1.000/1.000)|1.049(1.045/1.046)|1.045(1.045/1.045)|25%c
5.8f|

|7168|2112|2048*|2xm256|1.000(1.002/1.001)|0.998(1.000/1.000)|1.039(1.039/1.039)|1.039(1.039/1.038)|57%c|

|7168|2112|8192*|2xm192g8|1.001(1.001/1.001)|1.000(1.000/1.000)|1.046(1.046/1.046)|1.045(1.046/1.045)|75%c|

|7168|1536|1*|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.017(1.017/1.015)|1.017(1.012/1.014)|17%h
3.9f|

|7168|1536|8*|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.012(1.011/1.013)|1.006(1.011/1.010)|17%h
3.9f|

|7168|1536|17*|n8sk3|1.006(1.000/1.001)|1.006(1.000/1.003)|1.097(1.102/1.100)|1.096(1.096/1.094)|17%h
3.9f|

|7168|1536|32*|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.002)|1.037(1.037/1.038)|1.038(1.037/1.039)|16%h
4.2f|

|7168|1536|128*|2xm64|1.038(1.037/1.038)|1.037(1.037/1.036)|1.075(1.075/1.075)|1.079(1.075/1.077)|15%h
5.2f|

|7168|1536|130*|2xm64|1.029(1.033/1.031)|1.029(1.033/1.030)|1.067(1.058/1.058)|1.058(1.058/1.057)|14%h
5.3f|

|7168|1536|257*|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.040(1.044/1.042)|1.040(1.044/1.042)|16%h
5.5f|

|7168|1536|512*|2xm64|1.000(1.000/1.001)|1.004(1.000/1.000)|1.040(1.044/1.041)|1.040(1.040/1.040)|19%h
5.6f|

|7168|1536|2048*|2xm192|1.000(1.000/1.000)|0.997(1.000/1.000)|1.040(1.040/1.039)|1.040(1.040/1.039)|51%c|

|7168|1536|8192*|2xm256g8|1.000(1.000/1.000)|0.999(0.999/1.000)|1.072(1.072/1.072)|1.071(1.071/1.072)|70%c|

|16384|7168|1*|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.001)|1.119(1.123/1.120)|1.121(1.121/1.121)|68%h|

|16384|7168|8*|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.000)|1.121(1.122/1.122)|1.123(1.124/1.124)|68%h|

|16384|7168|17*|n32sk2|1.000(1.000/1.000)|1.000(1.000/1.001)|1.149(1.148/1.149)|1.146(1.146/1.147)|66%h|

|16384|7168|32*|n32sk2|0.998(1.000/0.999)|1.000(1.000/1.000)|1.144(1.143/1.143)|1.148(1.146/1.146)|66%h|

|16384|7168|128|m64|1.000(0.998/1.000)|1.002(1.000/1.000)|1.018(1.018/1.018)|1.016(1.018/1.018)|61%h|

|16384|7168|130*|2xm128|1.000(0.998/0.999)|0.998(1.000/0.999)|1.046(1.048/1.046)|1.048(1.048/1.047)|58%h|

|16384|7168|257*|2xm256|1.001(1.000/1.000)|1.000(1.000/1.000)|1.040(1.040/1.039)|1.037(1.040/1.039)|43%h|

|16384|7168|512*|2xm256|1.000(1.001/1.001)|1.000(1.000/1.000)|1.040(1.040/1.040)|1.040(1.040/1.041)|61%c|

|16384|7168|2048*|2xm192|1.000(1.000/1.000)|1.000(1.000/1.000)|1.044(1.044/1.045)|1.044(1.044/1.045)|74%c|

|16384|7168|8192*|2xm256g16clc|0.998(1.020/1.029)|0.998(0.984/0.981)|1.136(1.141/1.131)|1.139(1.167/1.181)|88%c|

|7168|18432|1|n8s3|1.002(1.000/1.000)|1.000(0.998/0.999)|1.025(1.029/1.027)|1.025(1.027/1.026)|72%h|

|7168|18432|8|n8s3|0.998(1.000/1.000)|0.998(0.998/0.999)|1.031(1.029/1.029)|1.031(1.031/1.032)|72%h|

|7168|18432|17|n32s3|1.000(1.000/1.003)|1.000(1.000/1.002)|1.014(1.017/1.016)|1.013(1.015/1.016)|72%h|

|7168|18432|32|n32s3|1.000(0.998/1.000)|0.998(1.000/1.000)|1.008(1.010/1.009)|1.011(1.011/1.011)|72%h|

|7168|18432|128|m128l2n|1.002(0.998/0.999)|1.000(1.000/1.000)|0.989(0.989/0.988)|0.996(0.991/0.990)|71%h|

|7168|18432|130*|2xm256|1.002(1.000/1.000)|0.998(1.000/1.000)|1.034(1.035/1.035)|1.035(1.035/1.036)|67%h|

|7168|18432|257*|2xm256|0.999(1.000/1.000)|0.999(0.999/0.999)|1.039(1.038/1.038)|1.038(1.038/1.038)|51%h|

|7168|18432|512*|2xm256|1.001(1.000/1.000)|1.000(1.000/1.000)|1.037(1.037/1.036)|1.037(1.038/1.037)|68%c|

|7168|18432|2048*|2xm256|1.001(1.000/1.000)|1.000(1.000/1.000)|1.031(1.031/1.031)|1.031(1.031/1.031)|85%c|

|7168|18432|8192*|2xm256clc|0.998(1.000/0.989)|0.997(0.991/1.003)|1.018(1.019/1.019)|1.023(1.035/1.034)|87%c|

|18432|7168|1|n8|1.002(1.000/1.001)|0.998(1.000/1.000)|1.145(1.145/1.144)|1.143(1.145/1.144)|69%h|

|18432|7168|8|n8|1.000(1.000/1.001)|1.000(1.000/1.000)|1.145(1.147/1.145)|1.145(1.146/1.146)|69%h|

|18432|7168|17*|n32sk2|1.002(1.002/1.004)|0.998(1.000/1.001)|1.156(1.156/1.159)|1.158(1.156/1.157)|66%h|

|18432|7168|32*|n32sk2|1.002(1.002/1.001)|0.998(1.000/0.999)|1.152(1.151/1.151)|1.151(1.149/1.150)|66%h|

|18432|7168|128|m64|1.000(1.000/1.000)|0.997(1.000/1.000)|1.021(1.021/1.021)|1.021(1.021/1.021)|62%h|

|18432|7168|130*|2xm128|1.000(0.998/1.000)|1.000(1.000/1.001)|1.056(1.056/1.055)|1.054(1.056/1.055)|59%h|

|18432|7168|257*|2xm256|1.000(1.000/1.000)|1.001(1.000/1.000)|1.044(1.044/1.044)|1.044(1.045/1.044)|44%h|

|18432|7168|512*|2xm256|1.000(0.999/1.000)|1.001(1.000/1.000)|1.046(1.046/1.047)|1.045(1.045/1.046)|62%c|

|18432|7168|2048*|2xm192|1.001(1.000/1.000)|1.000(1.000/1.000)|1.046(1.045/1.045)|1.045(1.045/1.045)|74%c|

|18432|7168|8192*|2xm256g16clc|1.000(1.032/1.015)|1.008(0.976/0.993)|1.134(1.118/1.124)|1.124(1.129/1.131)|87%c|

|8192|8192|1|n8|1.000(1.000/1.001)|1.003(0.997/0.999)|1.009(1.009/1.009)|1.012(1.009/1.009)|57%h|

|8192|8192|8|n8|1.003(1.000/1.001)|1.000(1.000/0.999)|1.018(1.018/1.018)|1.024(1.021/1.021)|57%h|

|8192|8192|17|n32|0.997(1.000/1.006)|0.997(0.997/1.000)|1.018(1.018/1.020)|1.021(1.021/1.021)|56%h|

|8192|8192|32|n32|1.000(1.000/1.000)|0.997(1.000/0.999)|1.012(1.015/1.014)|1.009(1.009/1.010)|56%h|

|8192|8192|128|m64|1.000(1.000/1.000)|1.000(0.997/1.000)|1.011(1.011/1.009)|1.006(1.011/1.009)|55%h|

|8192|8192|130*|2xm128|1.000(1.000/1.000)|1.000(1.000/1.000)|1.047(1.047/1.047)|1.047(1.047/1.047)|52%h|

|8192|8192|257*|2xm256|1.000(1.000/1.000)|1.000(1.000/0.999)|1.041(1.043/1.043)|1.043(1.043/1.043)|41%h|

|8192|8192|512*|2xm256|1.000(0.998/1.000)|1.000(0.998/1.000)|1.042(1.042/1.041)|1.040(1.042/1.041)|56%c|

|8192|8192|2048*|2xm192|1.000(1.000/1.000)|1.000(0.999/1.000)|1.058(1.059/1.059)|1.059(1.058/1.058)|76%c|

|8192|8192|8192*|2xm256g16clc|1.000(1.007/1.022)|0.999(0.998/0.993)|1.036(1.041/1.039)|1.036(1.035/1.027)|90%c|

|8192|28672|1|n8|0.997(1.000/0.999)|1.000(1.001/1.001)|1.013(1.013/1.013)|1.013(1.013/1.013)|82%h|

|8192|28672|8|n8|1.000(1.000/0.999)|1.000(1.001/1.001)|1.015(1.015/1.015)|1.016(1.019/1.017)|82%h|

|8192|28672|17|n32|1.000(0.999/1.007)|1.000(1.000/1.001)|1.016(1.016/1.025)|1.015(1.015/1.015)|82%h|

|8192|28672|32|n32|0.999(1.000/0.999)|0.999(1.000/1.000)|1.017(1.016/1.017)|1.014(1.015/1.014)|82%h|

|8192|28672|128|m128|0.999(1.001/1.000)|0.999(1.001/1.000)|1.053(1.052/1.052)|1.055(1.053/1.053)|76%h|

|8192|28672|130*|2xm256|0.999(1.000/0.999)|0.998(1.001/1.000)|1.025(1.025/1.025)|1.024(1.024/1.024)|69%h|

|8192|28672|257*|2xm192|0.999(1.001/1.000)|1.000(0.999/1.000)|1.063(1.062/1.062)|1.061(1.062/1.062)|48%h|

|8192|28672|512*|2xm192|1.000(0.999/1.000)|0.998(1.000/1.000)|1.063(1.063/1.063)|1.063(1.064/1.064)|64%c|

|8192|28672|2048*|2xm256clc|1.000(1.000/1.000)|1.000(1.006/1.006)|1.034(1.034/1.036)|1.034(1.034/1.034)|86%c|

|8192|28672|8192*|2xm256clc|1.002(0.989/0.977)|1.004(1.027/1.016)|1.023(1.027/1.028)|1.008(1.000/1.011)|85%c|

|28672|8192|1|n8|1.001(1.001/1.001)|1.002(0.999/1.000)|1.209(1.210/1.210)|1.207(1.209/1.210)|81%h|

|28672|8192|8|n8|1.000(1.000/1.000)|1.000(1.000/1.001)|1.209(1.207/1.209)|1.206(1.209/1.209)|81%h|

|28672|8192|17*|n32sk2|0.999(0.999/1.000)|1.001(1.001/1.003)|1.184(1.187/1.189)|1.181(1.182/1.183)|78%h|

|28672|8192|32*|n32sk2|1.001(1.000/1.000)|0.998(1.000/1.000)|1.182(1.181/1.182)|1.182(1.183/1.183)|78%h|

|28672|8192|128|m64|1.000(1.001/1.001)|1.000(0.999/1.000)|1.020(1.019/1.019)|1.020(1.022/1.021)|73%h|

|28672|8192|130*|2xm128|1.000(1.001/1.001)|1.000(1.000/1.000)|1.044(1.044/1.044)|1.042(1.042/1.043)|70%h|

|28672|8192|257*|2xm256|0.999(1.001/1.000)|1.001(1.001/1.001)|1.046(1.047/1.047)|1.046(1.045/1.046)|52%h|

|28672|8192|512*|2xm256|1.001(1.001/1.001)|1.000(1.000/1.000)|1.054(1.055/1.055)|1.054(1.053/1.054)|75%c|

|28672|8192|2048*|2xm192|1.002(1.007/1.015)|1.000(0.999/0.995)|1.051(1.050/1.053)|1.050(1.044/1.046)|85%c|

|28672|8192|8192*|2xm256g8clc|1.005(0.997/0.991)|1.010(1.011/1.005)|1.114(1.110/1.102)|1.120(1.133/1.116)|85%c|


**GB300**

#### GEMM per-token — vs #5744: bf16 rows 80, geomean 1.0023, min
0.9965, rows <= 1.00: 54; fp16 rows 80, geomean 1.0022, min 0.9949, rows
<= 1.00: 52. vs cute-dsl: bf16 rows 80, geomean 1.0534, min 0.9980, rows
<= 1.00: 1; fp16 rows 80, geomean 1.0531, min 0.9990, rows <= 1.00: 1

|K|N|M|tactic|vs #5744 bf16|vs #5744 fp16|vs cute-dsl bf16|vs cute-dsl
fp16|roof (share of measured peak; Nf = N x launch floor)|
|---|---|---|---|---|---|---|---|---|

|7168|2112|1*|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.027(1.022/1.025)|1.022(1.022/1.023)|22%h
4.7f|

|7168|2112|8*|n8sk4|1.000(1.000/1.001)|1.000(1.000/1.000)|1.022(1.022/1.020)|1.022(1.022/1.019)|22%h
4.7f|

|7168|2112|17*|n8sk2|1.000(1.000/1.000)|0.995(1.000/1.000)|1.031(1.031/1.032)|1.031(1.036/1.032)|21%h
5.0f|

|7168|2112|32*|n8sk2|1.000(1.000/1.000)|1.000(1.005/1.002)|1.030(1.030/1.032)|1.030(1.030/1.033)|21%h
5.1f|

|7168|2112|128*|2xm64|1.056(1.060/1.057)|1.060(1.060/1.058)|1.112(1.111/1.112)|1.112(1.116/1.116)|19%h|

|7168|2112|130*|2xm64|1.055(1.051/1.053)|1.055(1.055/1.055)|1.098(1.097/1.098)|1.098(1.097/1.097)|19%h|

|7168|2112|257*|2xm64|1.000(1.000/1.000)|1.000(1.000/0.999)|1.044(1.043/1.045)|1.048(1.048/1.046)|20%h|

|7168|2112|512*|2xm64|1.000(0.996/0.999)|1.000(1.000/1.001)|1.043(1.043/1.045)|1.043(1.043/1.045)|23%h|

|7168|2112|2048*|2xm256|1.000(1.000/1.000)|1.000(1.000/1.000)|1.039(1.042/1.040)|1.039(1.042/1.041)|58%c|

|7168|2112|8192*|2xm192g8|1.002(1.002/1.000)|0.997(0.999/0.999)|1.023(1.022/1.022)|1.024(1.022/1.022)|74%c|

|7168|1536|1*|n8sk4|1.000(1.000/1.001)|1.000(1.000/1.000)|1.029(1.023/1.024)|1.023(1.023/1.023)|17%h
4.4f|

|7168|1536|8*|n8sk4|1.000(1.000/1.000)|1.000(1.000/1.000)|1.029(1.029/1.027)|1.023(1.017/1.019)|17%h
4.4f|

|7168|1536|17*|n8sk3|1.000(1.000/0.998)|1.000(1.000/1.000)|1.087(1.081/1.083)|1.081(1.081/1.082)|17%h
4.4f|

|7168|1536|32*|n8sk2|1.000(1.000/1.000)|1.000(1.000/1.001)|1.027(1.027/1.027)|1.022(1.027/1.025)|16%h
4.7f|

|7168|1536|128*|2xm64|1.039(1.044/1.042)|1.044(1.039/1.041)|1.096(1.100/1.099)|1.101(1.100/1.098)|14%h
5.9f|

|7168|1536|130*|2xm64|1.030(1.030/1.031)|1.026(1.030/1.028)|1.069(1.073/1.071)|1.074(1.073/1.072)|14%h
5.9f|

|7168|1536|257*|2xm64|1.000(1.000/1.001)|0.996(1.000/1.000)|1.042(1.046/1.042)|1.042(1.046/1.044)|15%h|

|7168|1536|512*|2xm64|1.000(1.000/1.000)|1.000(1.000/1.000)|1.045(1.045/1.046)|1.041(1.045/1.045)|19%h|

|7168|1536|2048*|2xm192|1.000(1.000/1.000)|1.000(1.000/1.000)|1.053(1.053/1.053)|1.053(1.053/1.054)|50%c|

|7168|1536|8192*|2xm256g8|0.998(0.999/0.999)|1.001(1.000/1.000)|1.056(1.057/1.056)|1.056(1.056/1.055)|68%c|

|16384|7168|1*|n8sk2|1.000(1.000/0.999)|1.000(1.000/1.001)|1.127(1.127/1.126)|1.123(1.127/1.125)|66%h|

|16384|7168|8*|n8sk2|1.000(0.998/1.000)|1.002(0.998/1.000)|1.132(1.134/1.133)|1.134(1.133/1.132)|66%h|

|16384|7168|17*|n32sk2|0.998(1.000/0.999)|1.000(1.000/0.999)|1.151(1.150/1.151)|1.153(1.150/1.152)|64%h|

|16384|7168|32*|n32sk2|1.000(1.002/1.001)|0.998(1.000/1.000)|1.148(1.145/1.145)|1.145(1.147/1.146)|64%h|

|16384|7168|128|m64|0.998(0.998/0.999)|0.998(0.998/0.999)|1.020(1.022/1.021)|1.020(1.016/1.019)|59%h|

|16384|7168|130*|2xm128|0.996(1.000/0.999)|0.998(0.998/1.000)|1.048(1.050/1.049)|1.050(1.050/1.050)|57%h|

|16384|7168|257*|2xm192|1.000(0.998/0.999)|1.002(1.002/1.001)|1.034(1.033/1.034)|1.032(1.033/1.033)|51%h|

|16384|7168|512*|2xm192|1.001(1.001/1.001)|1.000(0.999/1.000)|1.037(1.039/1.039)|1.040(1.040/1.041)|68%c|

|16384|7168|2048*|2xm256g8|0.999(0.999/1.000)|0.999(1.002/1.001)|1.020(1.019/1.019)|1.022(1.021/1.021)|89%c|

|16384|7168|8192*|2xm256g16clc|0.999(1.002/1.001)|1.001(1.001/1.001)|1.107(1.107/1.107)|1.107(1.108/1.107)|93%c|

|7168|18432|1|n8s3|1.000(0.998/0.999)|0.998(1.000/1.000)|1.045(1.047/1.047)|1.047(1.047/1.047)|70%h|

|7168|18432|8|n8s3|1.000(1.000/0.999)|1.000(1.000/0.999)|1.051(1.048/1.050)|1.051(1.053/1.053)|70%h|

|7168|18432|17|n32s3|1.000(1.000/1.000)|1.002(1.000/1.000)|1.028(1.028/1.028)|1.034(1.034/1.034)|70%h|

|7168|18432|32|n32s3|1.000(1.000/0.999)|1.000(1.000/1.001)|1.022(1.026/1.025)|1.026(1.024/1.025)|70%h|

|7168|18432|128|m128l2n|0.998(0.998/0.999)|1.000(0.998/0.999)|1.006(1.006/1.005)|1.002(1.004/1.003)|70%h|

|7168|18432|130*|2xm256|1.000(1.000/1.000)|1.000(1.000/1.001)|1.027(1.025/1.026)|1.027(1.027/1.026)|66%h|

|7168|18432|257*|2xm256|1.000(1.001/1.001)|0.999(0.999/0.999)|1.039(1.040/1.040)|1.037(1.039/1.038)|52%h|

|7168|18432|512*|2xm256|1.003(1.001/1.002)|1.000(1.000/0.999)|1.031(1.033/1.033)|1.033(1.032/1.032)|65%c|

|7168|18432|2048*|2xm256|0.998(1.000/1.000)|0.999(0.999/0.999)|1.015(1.011/1.012)|1.013(1.012/1.012)|82%c|

|7168|18432|8192*|2xm256clc|0.999(1.000/1.000)|1.001(1.001/1.000)|0.998(0.997/0.997)|0.999(0.997/0.998)|90%c|

|18432|7168|1|n8|1.002(1.000/1.000)|1.002(1.000/0.999)|1.124(1.122/1.123)|1.124(1.120/1.121)|67%h|

|18432|7168|8|n8|0.998(0.998/0.999)|1.000(1.000/1.000)|1.124(1.124/1.124)|1.122(1.124/1.123)|67%h|

|18432|7168|17*|n32sk2|1.000(1.000/1.000)|1.000(1.000/1.000)|1.156(1.155/1.156)|1.154(1.153/1.153)|65%h|

|18432|7168|32*|n32sk2|1.000(1.000/1.000)|1.000(0.998/1.000)|1.153(1.153/1.153)|1.155(1.151/1.152)|65%h|

|18432|7168|128|m64|1.000(0.998/0.999)|1.000(1.002/1.000)|1.025(1.025/1.025)|1.027(1.025/1.025)|61%h|

|18432|7168|130*|2xm128|1.000(1.000/1.000)|1.002(1.000/1.000)|1.052(1.052/1.051)|1.050(1.053/1.052)|58%h|

|18432|7168|257*|2xm192|1.001(1.001/1.001)|1.000(0.999/1.000)|1.037(1.039/1.039)|1.039(1.039/1.039)|52%h|

|18432|7168|512*|2xm192|1.001(1.000/1.000)|0.999(1.000/1.000)|1.042(1.041/1.042)|1.042(1.042/1.042)|69%c|

|18432|7168|2048*|2xm256g8|1.001(0.999/0.999)|1.000(1.001/1.001)|1.019(1.015/1.016)|1.015(1.015/1.015)|90%c|

|18432|7168|8192*|2xm256g16clc|0.999(1.000/0.999)|1.002(1.001/1.001)|1.110(1.109/1.110)|1.109(1.108/1.109)|93%c|

|8192|8192|1|n8|1.003(1.000/1.002)|1.000(0.997/0.998)|1.009(1.009/1.010)|1.006(1.012/1.010)|55%h|

|8192|8192|8|n8|1.000(1.000/1.000)|1.000(1.000/1.000)|1.018(1.018/1.018)|1.019(1.022/1.019)|55%h|

|8192|8192|17|n32|1.000(1.000/0.999)|1.000(1.000/0.999)|1.021(1.018/1.019)|1.018(1.018/1.018)|54%h|

|8192|8192|32|n32|1.003(1.000/1.001)|1.000(0.997/0.999)|1.018(1.021/1.018)|1.018(1.018/1.017)|54%h|

|8192|8192|128|m64|1.003(1.003/1.001)|1.003(1.000/1.000)|1.011(1.014/1.014)|1.014(1.014/1.014)|53%h|

|8192|8192|130*|2xm128|1.003(1.000/1.001)|1.000(0.997/0.999)|1.051(1.051/1.050)|1.051(1.051/1.052)|51%h|

|8192|8192|257*|2xm256|0.998(1.000/0.999)|1.000(1.002/1.000)|1.038(1.038/1.037)|1.036(1.038/1.037)|42%h|

|8192|8192|512*|2xm256|0.998(0.998/0.999)|0.998(1.000/1.000)|1.037(1.037/1.038)|1.037(1.037/1.037)|54%c|

|8192|8192|2048*|2xm192|1.001(1.001/1.000)|0.999(0.999/0.999)|1.053(1.050/1.050)|1.048(1.050/1.049)|74%c|

|8192|8192|8192*|2xm256g16clc|0.999(0.999/0.999)|0.999(1.001/1.001)|1.003(1.001/1.001)|1.002(1.001/1.001)|88%c|

|8192|28672|1|n8|1.000(1.000/1.000)|1.001(1.000/1.000)|1.016(1.016/1.015)|1.013(1.014/1.014)|80%h|

|8192|28672|8|n8|0.997(0.999/0.999)|1.000(1.000/1.000)|1.021(1.019/1.021)|1.018(1.019/1.020)|80%h|

|8192|28672|17|n32|1.001(1.001/1.001)|1.001(1.000/1.000)|1.018(1.021/1.019)|1.015(1.015/1.016)|80%h|

|8192|28672|32|n32|1.000(1.000/0.999)|1.001(1.000/1.000)|1.017(1.019/1.018)|1.010(1.013/1.012)|80%h|

|8192|28672|128|m192|1.000(0.999/0.999)|1.001(1.000/1.000)|1.012(1.011/1.011)|1.012(1.011/1.010)|77%h|

|8192|28672|130*|2xm192|1.001(1.000/1.000)|1.000(0.999/0.999)|1.019(1.019/1.019)|1.016(1.018/1.017)|77%h|

|8192|28672|257*|2xm256|0.999(1.000/1.000)|1.001(0.999/1.000)|1.033(1.033/1.033)|1.032(1.031/1.032)|59%h|

|8192|28672|512*|2xm256|1.002(1.000/1.001)|1.000(1.001/1.001)|1.034(1.034/1.034)|1.034(1.033/1.034)|74%c|

|8192|28672|2048*|2xm256clc|1.001(1.000/1.000)|1.000(1.000/1.000)|1.009(1.007/1.008)|1.008(1.008/1.008)|88%c|

|8192|28672|8192*|2xm256clc|1.002(1.000/1.000)|1.001(1.003/1.002)|1.002(1.001/1.000)|1.004(1.002/1.002)|92%c|

|28672|8192|1|n8|0.997(1.000/1.000)|1.001(1.000/1.000)|1.177(1.178/1.177)|1.181(1.180/1.179)|78%h|

|28672|8192|8|n8|1.000(1.000/1.000)|1.001(1.000/1.001)|1.179(1.179/1.179)|1.179(1.178/1.179)|78%h|

|28672|8192|17*|n32sk2|1.001(1.002/1.002)|1.000(1.001/1.001)|1.197(1.196/1.196)|1.197(1.195/1.195)|76%h|

|28672|8192|32*|n32sk2|1.000(1.000/1.000)|1.001(1.000/1.000)|1.190(1.191/1.191)|1.195(1.193/1.193)|76%h|

|28672|8192|128|m64|1.003(0.999/1.000)|0.999(1.000/1.000)|1.019(1.020/1.019)|1.018(1.020/1.020)|71%h|

|28672|8192|130*|2xm128|0.999(1.000/1.000)|0.999(0.999/0.999)|1.035(1.037/1.036)|1.037(1.037/1.037)|69%h|

|28672|8192|257*|2xm256|1.001(0.999/1.000)|1.001(1.000/1.000)|1.032(1.031/1.031)|1.033(1.032/1.032)|52%h|

|28672|8192|512*|2xm256|0.998(0.999/0.999)|0.998(1.000/1.000)|1.039(1.038/1.038)|1.041(1.039/1.039)|71%c|

|28672|8192|2048*|2xm192|1.001(1.001/1.000)|1.002(1.001/1.001)|1.027(1.026/1.026)|1.025(1.025/1.026)|82%c|

|28672|8192|8192*|2xm256g8clc|1.003(1.000/1.000)|1.001(0.999/1.000)|1.100(1.097/1.097)|1.101(1.097/1.099)|91%c|

### Fused table (CUDA Graph replay; eager secondary)

**B200**

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5744: bf16 rows 80, geomean 1.0026, min 0.9948, rows <= 1.00: 32;
fp16 rows 80, geomean 1.0020, min 0.9897, rows <= 1.00: 38. vs cute-dsl
(bf16): rows 80, geomean 1.0889, min 1.0099, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5744 bf16|vs #5744 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1*|n8sk4|1.017(1.021/1.018)|1.017(1.017/1.016)|1.112(1.158/1.148)|

|7168|2112|8*|n8sk4|1.000(1.017/1.009)|1.000(1.013/1.007)|1.142(1.172/1.166)|

|7168|2112|17*|n8sk2|1.012(1.008/1.008)|1.008(1.012/1.007)|1.153(1.169/1.163)|

|7168|2112|32*|n8sk2|1.004(1.004/1.005)|1.000(1.000/1.002)|1.124(1.123/1.130)|

|7168|2112|128*|2xm64|1.019(1.009/1.012)|1.016(1.009/1.013)|1.144(1.150/1.149)|

|7168|2112|130*|2xm64|1.010(1.022/1.015)|1.010(1.022/1.016)|1.129(1.160/1.148)|

|7168|2112|257*|2xm64|0.997(0.994/0.994)|1.000(0.997/0.996)|1.116(1.123/1.117)|

|7168|2112|512*|2xm64|1.005(1.005/1.005)|1.006(1.011/1.009)|1.112(1.144/1.137)|

|7168|2112|2048*|2xm256|1.003(0.997/0.997)|1.004(0.994/0.998)|1.220(1.216/1.216)|

|7168|2112|8192*|2xm192g8|1.001(1.000/1.000)|0.999(1.000/1.000)|1.052(1.056/1.054)|

|7168|1536|1*|n8sk4|1.000(0.991/0.997)|1.000(0.991/0.996)|1.121(1.099/1.113)|

|7168|1536|8*|n8sk4|1.005(0.991/0.997)|1.009(0.991/0.999)|1.112(1.109/1.109)|

|7168|1536|17*|n8sk3|1.005(1.009/1.006)|1.009(1.004/1.004)|1.163(1.146/1.161)|

|7168|1536|32*|n8sk2|1.004(0.996/1.001)|1.004(1.000/1.004)|1.103(1.093/1.098)|

|7168|1536|128*|2xm64|0.997(0.984/0.992)|1.000(0.990/0.991)|1.103(1.084/1.093)|

|7168|1536|130*|2xm64|1.013(1.026/1.024)|1.000(0.990/0.990)|1.092(1.080/1.080)|

|7168|1536|257*|2xm64|0.997(1.000/1.000)|1.000(0.985/0.994)|1.075(1.071/1.078)|

|7168|1536|512*|2xm64|1.017(1.023/1.018)|1.014(1.020/1.017)|1.119(1.119/1.118)|

|7168|1536|2048*|2xm192|0.998(1.000/1.000)|0.997(0.998/0.998)|1.194(1.208/1.202)|

|7168|1536|8192*|2xm256g8|1.001(1.007/1.005)|1.000(1.007/1.005)|1.083(1.084/1.084)|

|16384|7168|1*|n8sk2|1.004(1.007/1.006)|1.006(1.005/1.005)|1.115(1.116/1.113)|

|16384|7168|8*|n8sk2|1.007(1.013/1.009)|1.004(1.007/1.004)|1.128(1.133/1.128)|

|16384|7168|17*|n32sk2|1.004(0.998/1.000)|1.002(0.998/0.999)|1.150(1.148/1.146)|

|16384|7168|32*|n32sk2|0.998(1.007/1.005)|1.002(1.009/1.004)|1.146(1.151/1.149)|

|16384|7168|128|m64|1.008(1.005/1.004)|1.006(1.005/1.004)|1.043(1.046/1.043)|

|16384|7168|130*|2xm128|1.000(1.001/1.000)|1.002(1.003/1.001)|1.081(1.101/1.094)|

|16384|7168|257*|2xm256|0.999(0.993/0.996)|1.000(1.004/1.003)|1.028(1.026/1.027)|

|16384|7168|512*|2xm256|0.995(0.996/0.996)|0.996(0.992/0.993)|1.065(1.065/1.066)|

|16384|7168|2048*|2xm192|0.999(0.999/0.999)|0.999(0.998/0.999)|1.099(1.098/1.099)|

|16384|7168|8192*|2xm256g16clc|0.998(1.012/1.001)|0.990(0.989/0.994)|1.131(1.129/1.135)|

|7168|18432|1|n8s3|1.002(1.003/1.001)|0.998(1.002/1.001)|1.066(1.078/1.073)|

|7168|18432|8|n8s3|1.011(1.014/1.012)|1.007(1.011/1.010)|1.084(1.096/1.090)|

|7168|18432|17|n32s3|1.004(1.004/1.004)|1.004(1.005/1.003)|1.053(1.058/1.056)|

|7168|18432|32|n32s3|1.007(1.003/1.005)|1.003(1.003/1.004)|1.051(1.058/1.058)|

|7168|18432|128|m128l2n|1.002(1.000/1.000)|1.002(0.998/1.000)|1.025(1.024/1.023)|

|7168|18432|130*|2xm256|1.002(0.995/0.999)|0.998(0.995/0.999)|1.053(1.053/1.055)|

|7168|18432|257*|2xm256|0.998(0.994/0.996)|0.998(0.993/0.996)|1.059(1.055/1.057)|

|7168|18432|512*|2xm256|1.002(1.005/1.004)|1.002(1.005/1.004)|1.066(1.069/1.067)|

|7168|18432|2048*|2xm256|1.000(1.000/1.000)|1.001(0.998/0.999)|1.045(1.047/1.047)|

|7168|18432|8192*|2xm256clc|1.004(1.002/1.010)|1.009(0.996/0.997)|1.025(1.040/1.031)|

|18432|7168|1|n8|1.000(1.002/1.000)|1.003(1.002/1.003)|1.108(1.070/1.078)|

|18432|7168|8|n8|1.007(1.042/1.031)|1.007(1.042/1.031)|1.139(1.139/1.132)|

|18432|7168|17*|n32sk2|1.011(1.019/1.014)|1.010(1.021/1.014)|1.161(1.160/1.158)|

|18432|7168|32*|n32sk2|0.998(0.988/0.991)|0.997(0.988/0.991)|1.149(1.142/1.146)|

|18432|7168|128|m64|1.003(1.000/1.001)|0.996(0.993/0.993)|1.050(1.053/1.052)|

|18432|7168|130*|2xm128|0.999(0.999/1.000)|1.007(1.012/1.009)|1.077(1.076/1.077)|

|18432|7168|257*|2xm256|1.000(1.004/1.004)|0.995(0.995/0.996)|1.029(1.039/1.035)|

|18432|7168|512*|2xm256|1.000(1.007/1.005)|0.996(0.994/0.994)|1.100(1.097/1.096)|

|18432|7168|2048*|2xm192|0.999(0.999/1.000)|1.000(0.999/0.999)|1.102(1.103/1.103)|

|18432|7168|8192*|2xm256g16clc|0.998(0.996/0.992)|0.998(1.012/1.020)|1.104(1.069/1.083)|

|8192|8192|1|n8|0.995(0.982/0.986)|1.000(0.997/0.997)|1.059(1.061/1.057)|

|8192|8192|8|n8|1.008(1.010/1.011)|1.010(1.013/1.010)|1.062(1.067/1.060)|

|8192|8192|17|n32|1.000(0.995/0.998)|1.005(0.990/0.990)|1.050(1.042/1.042)|

|8192|8192|32|n32|1.010(1.003/1.000)|1.013(1.013/1.012)|1.060(1.052/1.053)|

|8192|8192|128|m64|1.002(1.000/1.000)|0.998(0.995/0.998)|1.047(1.051/1.048)|

|8192|8192|130*|2xm128|1.002(1.004/1.005)|1.000(1.000/1.004)|1.082(1.082/1.083)|

|8192|8192|257*|2xm256|1.000(0.988/0.993)|0.997(0.993/0.994)|1.067(1.059/1.063)|

|8192|8192|512*|2xm256|1.003(1.003/1.004)|1.006(1.005/1.005)|1.075(1.077/1.077)|

|8192|8192|2048*|2xm192|1.001(0.999/1.000)|1.002(1.003/1.002)|1.083(1.082/1.082)|

|8192|8192|8192*|2xm256g16clc|0.999(0.991/0.992)|0.998(0.985/0.983)|1.015(1.003/1.007)|

|8192|28672|1|n8|1.006(1.009/1.008)|0.995(0.994/0.993)|1.033(1.035/1.033)|

|8192|28672|8|n8|1.000(0.998/0.998)|1.000(0.995/0.997)|1.034(1.034/1.036)|

|8192|28672|17|n32|1.001(1.004/1.003)|1.002(0.999/1.000)|1.028(1.026/1.027)|

|8192|28672|32|n32|1.006(1.006/1.005)|1.000(1.007/1.004)|1.024(1.025/1.025)|

|8192|28672|128|m128|0.999(0.998/1.000)|0.997(0.997/0.997)|1.014(1.016/1.017)|

|8192|28672|130*|2xm256|1.002(1.005/1.003)|1.002(1.005/1.003)|1.046(1.050/1.048)|

|8192|28672|257*|2xm192|1.003(1.001/1.001)|1.003(1.002/1.001)|1.064(1.066/1.065)|

|8192|28672|512*|2xm192|1.000(0.999/0.999)|1.000(1.001/1.000)|1.075(1.072/1.072)|

|8192|28672|2048*|2xm256clc|1.000(0.996/0.995)|1.000(1.005/1.000)|1.033(1.028/1.027)|

|8192|28672|8192*|2xm256clc|1.004(1.052/1.043)|1.002(1.062/1.024)|1.010(1.064/1.048)|

|28672|8192|1|n8|1.000(1.001/1.001)|1.000(1.002/1.001)|1.182(1.183/1.183)|

|28672|8192|8|n8|1.001(0.999/1.001)|1.000(1.000/1.000)|1.193(1.192/1.193)|

|28672|8192|17*|n32sk2|0.998(1.005/1.003)|1.000(1.004/1.004)|1.190(1.187/1.189)|

|28672|8192|32*|n32sk2|1.001(1.001/1.003)|1.000(1.003/1.004)|1.194(1.191/1.193)|

|28672|8192|128|m64|0.996(0.996/0.997)|0.996(0.995/0.996)|1.053(1.052/1.053)|

|28672|8192|130*|2xm128|0.999(0.997/0.997)|0.995(0.994/0.995)|1.067(1.068/1.067)|

|28672|8192|257*|2xm256|1.001(1.002/1.001)|1.001(1.003/1.002)|1.063(1.067/1.066)|

|28672|8192|512*|2xm256|0.999(1.002/1.000)|0.999(1.001/1.001)|1.084(1.084/1.083)|

|28672|8192|2048*|2xm192|0.999(1.010/1.002)|1.000(0.987/0.992)|1.067(1.077/1.072)|

|28672|8192|8192*|2xm256g8clc|1.008(0.988/0.982)|1.012(0.921/0.960)|1.143(1.148/1.127)|


**GB300**

#### Fused quantize + GEMM chain (CUDA-graph replay, PDL edge included)
— vs #5744: bf16 rows 80, geomean 1.0015, min 0.9950, rows <= 1.00: 46;
fp16 rows 80, geomean 1.0017, min 0.9915, rows <= 1.00: 39. vs cute-dsl
(bf16): rows 80, geomean 1.0907, min 1.0071, rows <= 1.00: 0

|K|N|M|GEMM tactic|vs #5744 bf16|vs #5744 fp16|vs cute-dsl bf16|
|---|---|---|---|---|---|---|

|7168|2112|1*|n8sk4|0.996(0.971/0.982)|0.991(0.979/0.986)|1.089(1.091/1.092)|

|7168|2112|8*|n8sk4|1.009(0.992/1.000)|1.009(0.996/1.004)|1.139(1.122/1.136)|

|7168|2112|17*|n8sk2|0.996(0.996/1.002)|0.992(1.000/0.995)|1.132(1.137/1.148)|

|7168|2112|32*|n8sk2|1.012(1.004/1.007)|1.012(1.008/1.008)|1.133(1.145/1.142)|

|7168|2112|128*|2xm64|1.017(1.023/1.022)|1.020(1.023/1.023)|1.145(1.152/1.156)|

|7168|2112|130*|2xm64|1.013(1.010/1.014)|1.017(1.007/1.013)|1.141(1.132/1.142)|

|7168|2112|257*|2xm64|1.000(1.015/1.005)|1.000(1.009/1.004)|1.107(1.125/1.122)|

|7168|2112|512*|2xm64|1.000(0.994/0.999)|1.003(0.997/0.999)|1.136(1.126/1.131)|

|7168|2112|2048*|2xm256|1.003(1.005/1.003)|0.997(0.986/0.989)|1.216(1.211/1.212)|

|7168|2112|8192*|2xm192g8|1.004(1.005/1.006)|1.004(1.004/1.004)|1.051(1.056/1.057)|

|7168|1536|1*|n8sk4|1.000(0.987/0.988)|1.000(0.987/0.988)|1.077(1.089/1.099)|

|7168|1536|8*|n8sk4|1.014(1.027/1.018)|1.014(1.032/1.019)|1.133(1.146/1.137)|

|7168|1536|17*|n8sk3|1.000(1.000/1.001)|0.996(1.000/1.000)|1.130(1.150/1.149)|

|7168|1536|32*|n8sk2|1.004(1.004/1.006)|1.004(1.008/1.006)|1.094(1.097/1.100)|

|7168|1536|128*|2xm64|1.007(1.013/1.013)|1.010(1.014/1.014)|1.100(1.105/1.108)|

|7168|1536|130*|2xm64|1.031(1.034/1.030)|1.031(1.031/1.031)|1.110(1.116/1.111)|

|7168|1536|257*|2xm64|1.000(0.991/0.998)|1.003(0.997/1.002)|1.069(1.087/1.080)|

|7168|1536|512*|2xm64|1.000(1.000/0.998)|1.000(1.003/1.000)|1.110(1.100/1.100)|

|7168|1536|2048*|2xm192|0.998(0.954/0.970)|0.998(0.959/0.971)|1.230(1.223/1.227)|

|7168|1536|8192*|2xm256g8|1.005(1.009/1.006)|1.004(1.009/1.007)|1.098(1.098/1.098)|

|16384|7168|1*|n8sk2|0.998(1.002/0.999)|0.998(1.000/0.998)|1.127(1.136/1.132)|

|16384|7168|8*|n8sk2|0.998(0.993/0.997)|1.000(0.994/0.996)|1.129(1.130/1.131)|

|16384|7168|17*|n32sk2|1.007(1.009/1.009)|1.005(1.009/1.009)|1.159(1.165/1.161)|

|16384|7168|32*|n32sk2|0.998(1.000/0.998)|1.002(1.002/1.001)|1.161(1.156/1.157)|

|16384|7168|128|m64|0.995(0.992/0.991)|0.995(0.992/0.993)|1.065(1.068/1.066)|

|16384|7168|130*|2xm128|1.000(1.000/0.998)|1.000(1.005/1.002)|1.072(1.077/1.076)|

|16384|7168|257*|2xm192|1.003(1.008/1.004)|1.001(1.007/1.004)|1.065(1.068/1.068)|

|16384|7168|512*|2xm192|0.998(0.999/0.999)|0.998(0.998/0.999)|1.118(1.117/1.118)|

|16384|7168|2048*|2xm256g8|1.003(0.998/0.999)|1.002(0.999/0.999)|1.089(1.084/1.084)|

|16384|7168|8192*|2xm256g16clc|1.001(1.001/1.001)|1.001(1.001/1.000)|1.149(1.149/1.148)|

|7168|18432|1|n8s3|1.002(1.004/1.005)|1.004(1.004/1.004)|1.060(1.062/1.060)|

|7168|18432|8|n8s3|0.998(0.998/0.998)|1.000(1.000/0.999)|1.064(1.069/1.070)|

|7168|18432|17|n32s3|0.996(1.000/1.001)|1.000(0.998/1.002)|1.047(1.042/1.045)|

|7168|18432|32|n32s3|0.998(1.000/0.999)|0.998(0.995/0.998)|1.038(1.032/1.036)|

|7168|18432|128|m128l2n|1.002(0.998/1.001)|1.000(1.000/0.999)|1.029(1.027/1.030)|

|7168|18432|130*|2xm256|1.002(1.003/1.003)|1.002(1.003/1.003)|1.049(1.054/1.052)|

|7168|18432|257*|2xm256|1.005(1.005/1.004)|1.002(1.004/1.003)|1.071(1.070/1.070)|

|7168|18432|512*|2xm256|1.001(0.998/0.998)|1.001(0.999/0.999)|1.069(1.066/1.067)|

|7168|18432|2048*|2xm256|0.999(0.998/0.998)|0.998(0.997/0.998)|1.048(1.048/1.048)|

|7168|18432|8192*|2xm256clc|0.998(1.000/1.000)|1.000(1.000/1.000)|1.011(1.012/1.012)|

|18432|7168|1|n8|1.005(0.958/0.974)|1.003(0.958/0.973)|1.126(1.076/1.084)|

|18432|7168|8|n8|1.003(1.044/1.029)|1.000(1.042/1.029)|1.126(1.123/1.114)|

|18432|7168|17*|n32sk2|0.998(1.000/1.000)|0.997(1.002/1.002)|1.156(1.146/1.148)|

|18432|7168|32*|n32sk2|1.007(1.008/1.005)|1.005(1.008/1.006)|1.159(1.162/1.159)|

|18432|7168|128|m64|0.998(1.002/1.001)|1.002(1.002/1.002)|1.061(1.070/1.067)|

|18432|7168|130*|2xm128|1.001(1.000/1.001)|0.996(0.994/0.996)|1.055(1.064/1.062)|

|18432|7168|257*|2xm192|0.998(0.995/0.996)|0.998(0.995/0.998)|1.059(1.055/1.059)|

|18432|7168|512*|2xm192|1.001(1.006/1.004)|1.002(1.004/1.004)|1.120(1.122/1.121)|

|18432|7168|2048*|2xm256g8|0.999(0.998/0.999)|1.000(0.998/0.998)|1.093(1.087/1.088)|

|18432|7168|8192*|2xm256g16clc|1.001(1.001/1.001)|1.001(1.001/1.001)|1.100(1.100/1.100)|

|8192|8192|1|n8|1.000(0.992/0.995)|0.997(0.990/0.991)|1.065(1.056/1.060)|

|8192|8192|8|n8|1.000(0.997/1.001)|1.000(0.995/0.999)|1.051(1.053/1.054)|

|8192|8192|17|n32|1.016(1.013/1.012)|1.013(1.010/1.010)|1.092(1.097/1.094)|

|8192|8192|32|n32|0.997(0.992/0.993)|1.000(0.992/0.992)|1.073(1.064/1.066)|

|8192|8192|128|m64|0.998(0.990/0.996)|1.000(0.995/0.996)|1.051(1.051/1.055)|

|8192|8192|130*|2xm128|1.002(0.998/1.000)|0.998(0.995/0.998)|1.089(1.084/1.085)|

|8192|8192|257*|2xm256|0.998(1.004/1.002)|1.002(1.005/1.003)|1.080(1.086/1.083)|

|8192|8192|512*|2xm256|0.998(0.993/0.997)|0.998(0.993/0.996)|1.092(1.086/1.088)|

|8192|8192|2048*|2xm192|0.999(0.999/0.999)|1.003(1.002/1.002)|1.089(1.079/1.081)|

|8192|8192|8192*|2xm256g16clc|1.002(1.003/1.002)|1.001(1.001/1.001)|1.015(1.014/1.013)|

|8192|28672|1|n8|1.000(1.001/1.000)|0.999(1.001/1.000)|1.014(1.012/1.012)|

|8192|28672|8|n8|1.001(1.006/1.005)|1.004(1.005/1.005)|1.019(1.017/1.018)|

|8192|28672|17|n32|0.996(0.995/0.997)|1.002(1.005/1.004)|1.008(1.006/1.009)|

|8192|28672|32|n32|0.999(0.996/0.998)|0.996(0.995/0.997)|1.007(1.004/1.005)|

|8192|28672|128|m192|0.998(1.003/1.001)|1.001(1.001/1.001)|1.029(1.031/1.031)|

|8192|28672|130*|2xm192|1.000(0.999/0.999)|0.998(0.996/0.998)|1.047(1.043/1.046)|

|8192|28672|257*|2xm256|0.998(0.997/0.996)|1.000(0.995/0.996)|1.063(1.062/1.062)|

|8192|28672|512*|2xm256|0.999(0.999/1.000)|0.999(1.000/1.000)|1.063(1.064/1.064)|

|8192|28672|2048*|2xm256clc|0.998(0.997/0.998)|0.996(0.995/0.997)|1.026(1.028/1.028)|

|8192|28672|8192*|2xm256clc|0.999(1.000/0.999)|1.001(0.998/0.999)|1.009(1.008/1.008)|

|28672|8192|1|n8|0.999(0.994/0.995)|0.999(0.993/0.995)|1.175(1.175/1.175)|

|28672|8192|8|n8|0.999(1.006/1.004)|1.001(1.008/1.006)|1.193(1.196/1.197)|

|28672|8192|17*|n32sk2|1.010(1.010/1.009)|1.004(1.008/1.006)|1.204(1.204/1.203)|

|28672|8192|32*|n32sk2|1.000(1.002/1.003)|1.004(1.003/1.004)|1.197(1.198/1.197)|

|28672|8192|128|m64|1.000(1.000/1.000)|1.001(1.002/1.001)|1.063(1.063/1.062)|

|28672|8192|130*|2xm128|1.001(1.005/1.003)|1.006(1.007/1.006)|1.082(1.082/1.083)|

|28672|8192|257*|2xm256|0.996(0.998/0.998)|0.998(0.997/0.997)|1.075(1.073/1.074)|

|28672|8192|512*|2xm256|1.003(1.003/1.003)|1.005(1.006/1.006)|1.094(1.094/1.093)|

|28672|8192|2048*|2xm192|0.998(0.995/0.996)|0.999(0.999/0.998)|1.059(1.057/1.058)|

|28672|8192|8192*|2xm256g8clc|0.996(0.996/0.997)|1.000(0.999/0.999)|1.103(1.104/1.105)|


## 🔍 Related Issues

Tracker #4254 (cake per-token NVFP4 route). Supersedes nothing; follows
#5744.

## 🚀 Pull Request Checklist

- [x] Pre-commit hooks pass
- [x] Tests: `tests/gemm/test_cake_mm_fp4.py`,
`tests/quantization/test_cake_nvfp4_quantize.py`,
`tests/gemm/test_mm_fp4.py`, `tests/quantization/test_fp4_quantize.py`,
`tests/utils/test_cute_dsl_cache.py` (incl. graph replay) on B200 and
GB300: 26 / 30 / 136 (+12 skipped) / 10565 / 63 passed on each GPU,
pre-commit clean
- [x] No public API change; generated programs produced by the export
protocol (no hand edits)

## Reviewer Notes

The half-M program's gather path is documented inline (`cake_backend.py`
passes the flat scale tensors to every 2-CTA program; the kernel key
gains `hm`). Design ledger incl. every negative variant: internal design
doc, CAKE round-3 chapter.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Improved NVFP4 per-token GEMM tactic selection for eligible workloads,
with smaller token tiles in half-M mode.
* **Bug Fixes**
* Corrected row mapping during GEMM output processing across supported
GPU architectures.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [3ad8127](https://github.com/flashinfer-ai/flashinfer/commit/3ad8127678c24cdfb5e2ccfd9f484116ef90babc)

- **作者**: LightSeek Foundation
- **时间**: 2026-10-01T20:44:48Z
- **提交信息**: fix(autotuner): preserve profiling policy in saved configs (#5705)

@lightseekorg

<!-- .github/pull_request_template.md -->

## 📌 Description

Saved v1 autotuner configs lose the replay/L2 policy under which their
tactics were measured, so a subsequent cold-L2 tuning pass ignores them
and profiles again. Preserve that provenance so matching requests can
reuse saved results while changed policies still trigger tuning.

## 🔍 Related Issues

Related: #5495 addresses managed v2 caches; this fix covers v1
`save_configs` / `load_configs`.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

C++ formatting is skipped because this change touches only Python.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation: `python3 -m pytest -q
tests/autotuner/test_autotuner_configs.py`. The full repository suite
was not run. The regression covers matching-policy reuse, policy
mismatch, re-saving loaded results, and legacy replacement.

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

Legacy two-field records retain their existing tuning and serving
behavior. No kernel changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Autotuner cache entries retain their measurement settings, so
configurations are reused only when the requested replay and L2-cache
policies match.
* Older cache entries without saved settings use the default hot-L2
policy. Replacing a policy-aware entry with a legacy entry clears its
prior settings.
* The winning configuration’s measurement settings are updated when it
is ranked again under a different L2-cache policy.
* **Documentation**
* Clarified how saved measurement settings are handled, including the
default for older entries.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lightseek-bot <243258330+lightseek-bot@users.noreply.github.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2d69639](https://github.com/flashinfer-ai/flashinfer/commit/2d696397586ecb05ff8304fa4b10193f83115a19)

- **作者**: eigen
- **时间**: 2026-10-01T19:44:21Z
- **提交信息**: feat(cake_kimi_k3_attn_res): add Kimi-K3 AttnRes backend for SM100/SM103 (#5853)

## Generated-program export evidence

Baseline: **Cake production AttnRes launcher (launch_for_eval)** at Cake
revision `c3fb15f3fedf7a0f5b5d35580b69fd7636baa552`.

## Hardware stages

- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-79f60bde-265c-7161-f69c-e5d3a594e23f`;
75 shapes (named in the per-shape tables below).
- `sm_100a` / world size `1`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-cb4983fc-f8e6-aa1b-07f6-e43082875978`;
75 shapes (named in the per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-17b7eecb-67d8-59e7-26d1-268a16561993`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-7cd61e26-6d3f-1d38-7144-e75f4931ec0e`; 50 shapes (named in the
per-shape tables below).
- `sm_103a` / world size `1`: GPUs `NVIDIA B300 SXM6 AC`, capabilities
`10.3`, drivers `580.126.09`, UUIDs
`GPU-08d5c267-59b5-b3ec-4494-61102f2db64e`; 50 shapes (named in the
per-shape tables below).

Target revision: `071266a0ed3486357a34a48d4c2d4b95b32cd93d`.

Benchmark execution: `symmetric_external_cuda_graph` with 8
independently captured graph instances per arm, replayed round-robin; 3
counterbalanced groups, 100 warmup calls and 1000 reportable calls per
arm/group (fixed counts; no sizing pilot).
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the tables below retain every registered shape without
repeating those arguments.

## Per-shape results

|Shape|GPU|Route|Source ms|Export ms|Source /
Export|Correctness|Verdict|
|---|---|---|---:|---:|---:|---|---|

|primary_m1_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl0|0.003232|0.003200|1.010000x|pass|pass|

|primary_m1_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl0|0.003808|0.003808|1.000000x|pass|pass|

|primary_m1_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl0|0.004960|0.004960|1.000000x|pass|pass|

|primary_m1_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl0|0.006016|0.005984|1.005348x|pass|pass|

|primary_m2_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl0|0.003264|0.003264|1.000000x|pass|pass|

|primary_m2_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl0|0.003808|0.003840|0.991667x|pass|pass|

|primary_m2_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl0|0.005023|0.005024|0.999801x|pass|pass|

|primary_m2_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl0|0.006016|0.006048|0.994709x|pass|pass|

|primary_m4_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl0|0.003328|0.003328|1.000000x|pass|pass|

|primary_m4_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl0|0.003872|0.003872|1.000000x|pass|pass|

|primary_m4_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl0|0.005056|0.005056|1.000000x|pass|pass|

|primary_m4_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl0|0.006112|0.006144|0.994792x|pass|pass|

|primary_m8_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl0|0.003360|0.003360|1.000000x|pass|pass|

|primary_m8_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl0|0.003936|0.003936|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl0|0.005152|0.005153|0.999806x|pass|pass|

|primary_m8_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl0|0.006176|0.006176|1.000000x|pass|pass|

|primary_m16_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl0|0.003392|0.003360|1.009524x|pass|pass|

|primary_m16_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl0|0.003968|0.003968|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl0|0.005376|0.005408|0.994083x|pass|pass|

|primary_m16_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl0|0.006656|0.006624|1.004831x|pass|pass|

|primary_m32_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl0|0.003488|0.003488|1.000000x|pass|pass|

|primary_m32_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl0|0.004160|0.004160|1.000000x|pass|pass|

|primary_m32_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl0|0.005696|0.005728|0.994413x|pass|pass|

|primary_m32_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl0|0.006816|0.006816|1.000000x|pass|pass|

|primary_m64_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl0|0.003680|0.003680|1.000000x|pass|pass|

|primary_m64_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl0|0.004480|0.004480|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl0|0.006240|0.006240|1.000000x|pass|pass|

|primary_m64_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl0|0.007744|0.007744|1.000000x|pass|pass|

|primary_m128_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl0|0.004256|0.004255|1.000235x|pass|pass|

|primary_m128_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl0|0.005248|0.005248|1.000000x|pass|pass|

|primary_m128_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl0|0.007136|0.007136|1.000000x|pass|pass|

|primary_m128_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl0|0.008576|0.008608|0.996283x|pass|pass|

|primary_m256_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl0|0.005888|0.005888|1.000000x|pass|pass|

|primary_m256_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl0|0.007488|0.007520|0.995745x|pass|pass|

|primary_m256_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl0|0.009920|0.009920|1.000000x|pass|pass|

|primary_m256_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl0|0.013120|0.013056|1.004902x|pass|pass|

|primary_m512_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl0|0.008032|0.008064|0.996032x|pass|pass|

|primary_m512_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl0|0.010416|0.010400|1.001538x|pass|pass|

|primary_m512_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl0|0.015104|0.015105|0.999934x|pass|pass|

|primary_m512_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl0|0.021152|0.021120|1.001515x|pass|pass|

|primary_m1024_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl0|0.012576|0.012576|1.000000x|pass|pass|

|primary_m1024_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl0|0.015680|0.015649|1.001981x|pass|pass|

|primary_m1024_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl0|0.023616|0.023616|1.000000x|pass|pass|

|primary_m1024_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl0|0.033760|0.033760|1.000000x|pass|pass|

|primary_m2048_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl0|0.021632|0.021633|0.999954x|pass|pass|

|primary_m2048_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl0|0.026751|0.026751|1.000000x|pass|pass|

|primary_m2048_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl0|0.041696|0.041728|0.999233x|pass|pass|

|primary_m2048_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl0|0.060800|0.060816|0.999737x|pass|pass|

|primary_m4096_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl0|0.040000|0.040000|1.000000x|pass|pass|

|primary_m4096_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl0|0.048736|0.048736|1.000000x|pass|pass|

|primary_m4096_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl0|0.079584|0.079904|0.996001x|pass|pass|

|primary_m4096_k8__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl0|0.114847|0.114864|0.999852x|pass|pass|

|primary_m8192_k0__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl0|0.075584|0.075552|1.000424x|pass|pass|

|primary_m8192_k1__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl0|0.093376|0.093376|1.000000x|pass|pass|

|primary_m8192_k4__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl0|0.145119|0.145056|1.000434x|pass|pass|

|primary_m8192_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl0|0.212864|0.212833|1.000146x|pass|pass|

|primary_m16384_k0__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl0|0.146720|0.146720|1.000000x|pass|pass|

|primary_m16384_k1__sm_100a__pdl0|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl0|0.179264|0.179168|1.000536x|pass|pass|

|primary_m16384_k4__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl0|0.278112|0.277952|1.000576x|pass|pass|

|primary_m16384_k8__sm_100a__pdl0|G1|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl0|0.410336|0.410337|0.999998x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl0|0.004096|0.004096|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl0|0.004896|0.004896|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl0|0.005120|0.005120|1.000000x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl0|0.005600|0.005600|1.000000x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl0|0.005728|0.005760|0.994444x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl0|0.058463|0.058432|1.000531x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl0|0.069088|0.068992|1.001391x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl0|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl0|0.086080|0.086111|0.999634x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl0|0.094848|0.094816|1.000337x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl0|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl0|0.106240|0.106176|1.000603x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl0|0.005024|0.004992|1.006410x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl0|0.023712|0.023712|1.000000x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl0|0.026560|0.026528|1.001206x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl0|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl0|0.009600|0.009824|0.977199x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl0|G0|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl0|0.015936|0.015936|1.000000x|pass|pass|

|primary_m1_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k0_sm_100a_pdl1|0.003200|0.003200|1.000000x|pass|pass|

|primary_m1_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1_k1_sm_100a_pdl1|0.003776|0.003776|1.000000x|pass|pass|

|primary_m1_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1_k4_sm_100a_pdl1|0.004960|0.004960|1.000000x|pass|pass|

|primary_m1_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1_k8_sm_100a_pdl1|0.005984|0.005983|1.000167x|pass|pass|

|primary_m2_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k0_sm_100a_pdl1|0.003264|0.003264|1.000000x|pass|pass|

|primary_m2_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k1_sm_100a_pdl1|0.003840|0.003840|1.000000x|pass|pass|

|primary_m2_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2_k4_sm_100a_pdl1|0.005056|0.005056|1.000000x|pass|pass|

|primary_m2_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2_k8_sm_100a_pdl1|0.005984|0.006015|0.994846x|pass|pass|

|primary_m4_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4_k0_sm_100a_pdl1|0.003264|0.003264|1.000000x|pass|pass|

|primary_m4_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k1_sm_100a_pdl1|0.003872|0.003872|1.000000x|pass|pass|

|primary_m4_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4_k4_sm_100a_pdl1|0.005024|0.005056|0.993671x|pass|pass|

|primary_m4_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4_k8_sm_100a_pdl1|0.006048|0.006048|1.000000x|pass|pass|

|primary_m8_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k0_sm_100a_pdl1|0.003233|0.003232|1.000309x|pass|pass|

|primary_m8_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8_k1_sm_100a_pdl1|0.003936|0.003936|1.000000x|pass|pass|

|primary_m8_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8_k4_sm_100a_pdl1|0.005216|0.005216|1.000000x|pass|pass|

|primary_m8_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8_k8_sm_100a_pdl1|0.006144|0.006144|1.000000x|pass|pass|

|primary_m16_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k0_sm_100a_pdl1|0.003360|0.003360|1.000000x|pass|pass|

|primary_m16_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k1_sm_100a_pdl1|0.003968|0.003968|1.000000x|pass|pass|

|primary_m16_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16_k4_sm_100a_pdl1|0.005313|0.005376|0.988281x|pass|pass|

|primary_m16_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16_k8_sm_100a_pdl1|0.006431|0.006433|0.999689x|pass|pass|

|primary_m32_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m32_k0_sm_100a_pdl1|0.003488|0.003488|1.000000x|pass|pass|

|primary_m32_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k1_sm_100a_pdl1|0.004129|0.004160|0.992548x|pass|pass|

|primary_m32_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m32_k4_sm_100a_pdl1|0.005696|0.005728|0.994413x|pass|pass|

|primary_m32_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m32_k8_sm_100a_pdl1|0.006816|0.006816|1.000000x|pass|pass|

|primary_m64_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k0_sm_100a_pdl1|0.003711|0.003680|1.008424x|pass|pass|

|primary_m64_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m64_k1_sm_100a_pdl1|0.004544|0.004544|1.000000x|pass|pass|

|primary_m64_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m64_k4_sm_100a_pdl1|0.006336|0.006336|1.000000x|pass|pass|

|primary_m64_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m64_k8_sm_100a_pdl1|0.007808|0.007808|1.000000x|pass|pass|

|primary_m128_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k0_sm_100a_pdl1|0.004160|0.004160|1.000000x|pass|pass|

|primary_m128_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k1_sm_100a_pdl1|0.005216|0.005216|1.000000x|pass|pass|

|primary_m128_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m128_k4_sm_100a_pdl1|0.007167|0.007168|0.999860x|pass|pass|

|primary_m128_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m128_k8_sm_100a_pdl1|0.008640|0.008640|1.000000x|pass|pass|

|primary_m256_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m256_k0_sm_100a_pdl1|0.005792|0.005792|1.000000x|pass|pass|

|primary_m256_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k1_sm_100a_pdl1|0.007488|0.007488|1.000000x|pass|pass|

|primary_m256_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m256_k4_sm_100a_pdl1|0.009951|0.009920|1.003125x|pass|pass|

|primary_m256_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m256_k8_sm_100a_pdl1|0.013343|0.013280|1.004744x|pass|pass|

|primary_m512_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k0_sm_100a_pdl1|0.008320|0.008289|1.003740x|pass|pass|

|primary_m512_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m512_k1_sm_100a_pdl1|0.010400|0.010368|1.003086x|pass|pass|

|primary_m512_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m512_k4_sm_100a_pdl1|0.015104|0.015104|1.000000x|pass|pass|

|primary_m512_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m512_k8_sm_100a_pdl1|0.021184|0.021152|1.001513x|pass|pass|

|primary_m1024_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k0_sm_100a_pdl1|0.012512|0.012512|1.000000x|pass|pass|

|primary_m1024_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k1_sm_100a_pdl1|0.015808|0.015808|1.000000x|pass|pass|

|primary_m1024_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m1024_k4_sm_100a_pdl1|0.023744|0.023744|1.000000x|pass|pass|

|primary_m1024_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m1024_k8_sm_100a_pdl1|0.033632|0.033631|1.000030x|pass|pass|

|primary_m2048_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2048_k0_sm_100a_pdl1|0.021472|0.021473|0.999953x|pass|pass|

|primary_m2048_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k1_sm_100a_pdl1|0.026912|0.026913|0.999963x|pass|pass|

|primary_m2048_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m2048_k4_sm_100a_pdl1|0.041664|0.041696|0.999233x|pass|pass|

|primary_m2048_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m2048_k8_sm_100a_pdl1|0.060704|0.060736|0.999473x|pass|pass|

|primary_m4096_k0__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k0_sm_100a_pdl1|0.040064|0.040064|1.000000x|pass|pass|

|primary_m4096_k1__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4096_k1_sm_100a_pdl1|0.049344|0.049344|1.000000x|pass|pass|

|primary_m4096_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m4096_k4_sm_100a_pdl1|0.078368|0.078240|1.001636x|pass|pass|

|primary_m4096_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m4096_k8_sm_100a_pdl1|0.114047|0.114016|1.000272x|pass|pass|

|primary_m8192_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k0_sm_100a_pdl1|0.075616|0.075584|1.000423x|pass|pass|

|primary_m8192_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k1_sm_100a_pdl1|0.091807|0.091808|0.999989x|pass|pass|

|primary_m8192_k4__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m8192_k4_sm_100a_pdl1|0.146560|0.146528|1.000218x|pass|pass|

|primary_m8192_k8__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m8192_k8_sm_100a_pdl1|0.213152|0.213185|0.999845x|pass|pass|

|primary_m16384_k0__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16384_k0_sm_100a_pdl1|0.146817|0.146881|0.999564x|pass|pass|

|primary_m16384_k1__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k1_sm_100a_pdl1|0.178848|0.178816|1.000179x|pass|pass|

|primary_m16384_k4__sm_100a__pdl1|G1|kimi_k3_attn_res_primary_m16384_k4_sm_100a_pdl1|0.276672|0.276545|1.000459x|pass|pass|

|primary_m16384_k8__sm_100a__pdl1|G0|kimi_k3_attn_res_primary_m16384_k8_sm_100a_pdl1|0.410719|0.410656|1.000153x|pass|pass|

|k_sweep_m1_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k2_sm_100a_pdl1|0.004127|0.004128|0.999758x|pass|pass|

|k_sweep_m1_k3__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k3_sm_100a_pdl1|0.004896|0.004896|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k5_sm_100a_pdl1|0.005120|0.005120|1.000000x|pass|pass|

|k_sweep_m1_k6__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m1_k6_sm_100a_pdl1|0.005568|0.005568|1.000000x|pass|pass|

|k_sweep_m1_k7__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m1_k7_sm_100a_pdl1|0.005920|0.005920|1.000000x|pass|pass|

|k_sweep_m4096_k2__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k2_sm_100a_pdl1|0.058880|0.058880|1.000000x|pass|pass|

|k_sweep_m4096_k3__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k3_sm_100a_pdl1|0.068800|0.068831|0.999550x|pass|pass|

|k_sweep_m4096_k5__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m4096_k5_sm_100a_pdl1|0.086048|0.086080|0.999628x|pass|pass|

|k_sweep_m4096_k6__sm_100a__pdl1|G1|kimi_k3_attn_res_k_sweep_m4096_k6_sm_100a_pdl1|0.094592|0.094656|0.999324x|pass|pass|

|k_sweep_m4096_k7__sm_100a__pdl1|G0|kimi_k3_attn_res_k_sweep_m4096_k7_sm_100a_pdl1|0.105984|0.106047|0.999406x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_100a_pdl1|0.005024|0.005024|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_100a_pdl1|0.023616|0.023680|0.997297x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_100a__pdl1|G0|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_100a_pdl1|0.028288|0.028319|0.998905x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_100a_pdl1|0.009632|0.009889|0.974012x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_100a__pdl1|G1|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_100a_pdl1|0.016096|0.016096|1.000000x|pass|pass|

|primary_m1_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl0|0.002976|0.002976|1.000000x|pass|pass|

|primary_m1_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl0|0.003584|0.003584|1.000000x|pass|pass|

|primary_m1_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl0|0.004928|0.004800|1.026667x|pass|pass|

|primary_m1_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl0|0.005729|0.005760|0.994618x|pass|pass|

|primary_m2_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl0|0.003040|0.003040|1.000000x|pass|pass|

|primary_m2_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl0|0.003616|0.003584|1.008929x|pass|pass|

|primary_m2_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl0|0.004928|0.004768|1.033557x|pass|pass|

|primary_m2_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl0|0.005856|0.005889|0.994396x|pass|pass|

|primary_m4_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl0|0.003040|0.003072|0.989583x|pass|pass|

|primary_m4_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl0|0.003585|0.003584|1.000279x|pass|pass|

|primary_m4_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl0|0.004992|0.004832|1.033113x|pass|pass|

|primary_m4_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl0|0.005888|0.005920|0.994595x|pass|pass|

|primary_m8_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl0|0.003104|0.003104|1.000000x|pass|pass|

|primary_m8_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl0|0.003680|0.003649|1.008495x|pass|pass|

|primary_m8_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl0|0.005056|0.004896|1.032680x|pass|pass|

|primary_m8_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl0|0.005984|0.006048|0.989418x|pass|pass|

|primary_m16_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl0|0.003200|0.003231|0.990405x|pass|pass|

|primary_m16_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl0|0.003840|0.003808|1.008403x|pass|pass|

|primary_m16_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl0|0.005215|0.005056|1.031448x|pass|pass|

|primary_m16_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl0|0.006144|0.006176|0.994819x|pass|pass|

|primary_m32_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl0|0.003328|0.003360|0.990476x|pass|pass|

|primary_m32_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl0|0.004000|0.004000|1.000000x|pass|pass|

|primary_m32_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl0|0.005632|0.005472|1.029240x|pass|pass|

|primary_m32_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl0|0.006592|0.006656|0.990385x|pass|pass|

|primary_m64_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl0|0.003552|0.003553|0.999719x|pass|pass|

|primary_m64_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl0|0.004416|0.004384|1.007299x|pass|pass|

|primary_m64_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl0|0.006304|0.006145|1.025875x|pass|pass|

|primary_m64_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl0|0.007296|0.007360|0.991304x|pass|pass|

|primary_m128_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl0|0.004128|0.004096|1.007812x|pass|pass|

|primary_m128_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl0|0.005152|0.005152|1.000000x|pass|pass|

|primary_m128_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl0|0.007232|0.007072|1.022624x|pass|pass|

|primary_m128_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl0|0.008416|0.008448|0.996212x|pass|pass|

|primary_m256_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl0|0.005568|0.005600|0.994286x|pass|pass|

|primary_m256_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl0|0.007360|0.007297|1.008634x|pass|pass|

|primary_m256_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl0|0.009696|0.009440|1.027119x|pass|pass|

|primary_m256_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl0|0.012608|0.012608|1.000000x|pass|pass|

|primary_m512_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl0|0.008128|0.008129|0.999877x|pass|pass|

|primary_m512_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl0|0.010079|0.010016|1.006290x|pass|pass|

|primary_m512_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl0|0.015136|0.015040|1.006383x|pass|pass|

|primary_m512_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl0|0.021247|0.021185|1.002950x|pass|pass|

|primary_m1024_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl0|0.012575|0.012640|0.994858x|pass|pass|

|primary_m1024_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl0|0.015744|0.015744|1.000000x|pass|pass|

|primary_m1024_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl0|0.024577|0.023840|1.030914x|pass|pass|

|primary_m1024_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl0|0.034720|0.034817|0.997214x|pass|pass|

|primary_m2048_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl0|0.021984|0.022016|0.998547x|pass|pass|

|primary_m2048_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl0|0.027104|0.027104|1.000000x|pass|pass|

|primary_m2048_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl0|0.042016|0.042016|1.000000x|pass|pass|

|primary_m2048_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl0|0.062369|0.062465|0.998463x|pass|pass|

|primary_m4096_k0__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl0|0.040000|0.040096|0.997606x|pass|pass|

|primary_m4096_k1__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl0|0.049344|0.049313|1.000629x|pass|pass|

|primary_m4096_k4__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl0|0.077889|0.078177|0.996316x|pass|pass|

|primary_m4096_k8__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl0|0.116833|0.117025|0.998359x|pass|pass|

|primary_m8192_k0__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl0|0.076609|0.076737|0.998332x|pass|pass|

|primary_m8192_k1__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl0|0.093697|0.093729|0.999659x|pass|pass|

|primary_m8192_k4__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl0|0.145570|0.146178|0.995841x|pass|pass|

|primary_m8192_k8__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl0|0.217858|0.217987|0.999408x|pass|pass|

|primary_m16384_k0__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl0|0.147810|0.148034|0.998487x|pass|pass|

|primary_m16384_k1__sm_103a__pdl0|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl0|0.181026|0.181091|0.999641x|pass|pass|

|primary_m16384_k4__sm_103a__pdl0|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl0|0.279555|0.280260|0.997484x|pass|pass|

|primary_m16384_k8__sm_103a__pdl0|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl0|0.418982|0.419077|0.999773x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl0|0.003777|0.003776|1.000265x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl0|0.004576|0.004577|0.999782x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl0|0.004960|0.005024|0.987261x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl0|0.005440|0.005472|0.994152x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl0|0.005632|0.005632|1.000000x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl0|0.059808|0.059776|1.000535x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl0|0.067073|0.067073|1.000000x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl0|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl0|0.087105|0.088225|0.987305x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl0|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl0|0.097921|0.098146|0.997707x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl0|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl0|0.108386|0.108257|1.001192x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl0|0.004640|0.004672|0.993151x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl0|0.022337|0.022336|1.000045x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl0|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl0|0.025761|0.025888|0.995094x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl0|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl0|0.009152|0.009152|1.000000x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl0|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl0|0.015265|0.015265|1.000000x|pass|pass|

|primary_m1_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k0_sm_103a_pdl1|0.002944|0.002944|1.000000x|pass|pass|

|primary_m1_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1_k1_sm_103a_pdl1|0.003616|0.003584|1.008929x|pass|pass|

|primary_m1_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1_k4_sm_103a_pdl1|0.004865|0.004704|1.034226x|pass|pass|

|primary_m1_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1_k8_sm_103a_pdl1|0.005761|0.005728|1.005761x|pass|pass|

|primary_m2_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k0_sm_103a_pdl1|0.003040|0.003072|0.989583x|pass|pass|

|primary_m2_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2_k1_sm_103a_pdl1|0.003584|0.003552|1.009009x|pass|pass|

|primary_m2_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2_k4_sm_103a_pdl1|0.004928|0.004768|1.033557x|pass|pass|

|primary_m2_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2_k8_sm_103a_pdl1|0.005888|0.005824|1.010989x|pass|pass|

|primary_m4_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k0_sm_103a_pdl1|0.003072|0.003072|1.000000x|pass|pass|

|primary_m4_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4_k1_sm_103a_pdl1|0.003616|0.003616|1.000000x|pass|pass|

|primary_m4_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4_k4_sm_103a_pdl1|0.004960|0.004768|1.040268x|pass|pass|

|primary_m4_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4_k8_sm_103a_pdl1|0.005888|0.005824|1.010989x|pass|pass|

|primary_m8_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k0_sm_103a_pdl1|0.003072|0.003104|0.989691x|pass|pass|

|primary_m8_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8_k1_sm_103a_pdl1|0.003648|0.003648|1.000000x|pass|pass|

|primary_m8_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8_k4_sm_103a_pdl1|0.005088|0.004896|1.039216x|pass|pass|

|primary_m8_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8_k8_sm_103a_pdl1|0.005952|0.005888|1.010870x|pass|pass|

|primary_m16_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k0_sm_103a_pdl1|0.003264|0.003264|1.000000x|pass|pass|

|primary_m16_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16_k1_sm_103a_pdl1|0.003809|0.003808|1.000263x|pass|pass|

|primary_m16_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16_k4_sm_103a_pdl1|0.005216|0.005056|1.031646x|pass|pass|

|primary_m16_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16_k8_sm_103a_pdl1|0.006240|0.006208|1.005155x|pass|pass|

|primary_m32_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k0_sm_103a_pdl1|0.003328|0.003360|0.990476x|pass|pass|

|primary_m32_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m32_k1_sm_103a_pdl1|0.004032|0.004000|1.008000x|pass|pass|

|primary_m32_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m32_k4_sm_103a_pdl1|0.005600|0.005440|1.029412x|pass|pass|

|primary_m32_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m32_k8_sm_103a_pdl1|0.006655|0.006592|1.009557x|pass|pass|

|primary_m64_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k0_sm_103a_pdl1|0.003584|0.003584|1.000000x|pass|pass|

|primary_m64_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m64_k1_sm_103a_pdl1|0.004416|0.004384|1.007299x|pass|pass|

|primary_m64_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m64_k4_sm_103a_pdl1|0.006304|0.006144|1.026042x|pass|pass|

|primary_m64_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m64_k8_sm_103a_pdl1|0.007296|0.007232|1.008850x|pass|pass|

|primary_m128_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k0_sm_103a_pdl1|0.004096|0.004097|0.999756x|pass|pass|

|primary_m128_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m128_k1_sm_103a_pdl1|0.005184|0.005153|1.006016x|pass|pass|

|primary_m128_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m128_k4_sm_103a_pdl1|0.007168|0.007008|1.022831x|pass|pass|

|primary_m128_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m128_k8_sm_103a_pdl1|0.008384|0.008321|1.007571x|pass|pass|

|primary_m256_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k0_sm_103a_pdl1|0.005696|0.005728|0.994413x|pass|pass|

|primary_m256_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m256_k1_sm_103a_pdl1|0.007393|0.007360|1.004484x|pass|pass|

|primary_m256_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m256_k4_sm_103a_pdl1|0.009728|0.009504|1.023569x|pass|pass|

|primary_m256_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m256_k8_sm_103a_pdl1|0.012608|0.012640|0.997468x|pass|pass|

|primary_m512_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k0_sm_103a_pdl1|0.007968|0.008000|0.996000x|pass|pass|

|primary_m512_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m512_k1_sm_103a_pdl1|0.010017|0.009984|1.003305x|pass|pass|

|primary_m512_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m512_k4_sm_103a_pdl1|0.015104|0.015009|1.006330x|pass|pass|

|primary_m512_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m512_k8_sm_103a_pdl1|0.021473|0.021536|0.997075x|pass|pass|

|primary_m1024_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k0_sm_103a_pdl1|0.012576|0.012608|0.997462x|pass|pass|

|primary_m1024_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m1024_k1_sm_103a_pdl1|0.015569|0.015584|0.999005x|pass|pass|

|primary_m1024_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m1024_k4_sm_103a_pdl1|0.024769|0.024064|1.029297x|pass|pass|

|primary_m1024_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m1024_k8_sm_103a_pdl1|0.034304|0.034496|0.994434x|pass|pass|

|primary_m2048_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k0_sm_103a_pdl1|0.021952|0.022048|0.995646x|pass|pass|

|primary_m2048_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m2048_k1_sm_103a_pdl1|0.026753|0.026752|1.000037x|pass|pass|

|primary_m2048_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m2048_k4_sm_103a_pdl1|0.042017|0.042017|1.000000x|pass|pass|

|primary_m2048_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m2048_k8_sm_103a_pdl1|0.062369|0.062497|0.997952x|pass|pass|

|primary_m4096_k0__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k0_sm_103a_pdl1|0.039969|0.040064|0.997629x|pass|pass|

|primary_m4096_k1__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m4096_k1_sm_103a_pdl1|0.049345|0.049344|1.000020x|pass|pass|

|primary_m4096_k4__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m4096_k4_sm_103a_pdl1|0.078496|0.078528|0.999599x|pass|pass|

|primary_m4096_k8__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m4096_k8_sm_103a_pdl1|0.116994|0.117250|0.997817x|pass|pass|

|primary_m8192_k0__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k0_sm_103a_pdl1|0.076737|0.076928|0.997517x|pass|pass|

|primary_m8192_k1__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m8192_k1_sm_103a_pdl1|0.093825|0.093889|0.999318x|pass|pass|

|primary_m8192_k4__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m8192_k4_sm_103a_pdl1|0.144993|0.145569|0.996043x|pass|pass|

|primary_m8192_k8__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m8192_k8_sm_103a_pdl1|0.218531|0.218754|0.998981x|pass|pass|

|primary_m16384_k0__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k0_sm_103a_pdl1|0.147778|0.147969|0.998709x|pass|pass|

|primary_m16384_k1__sm_103a__pdl1|G2|kimi_k3_attn_res_primary_m16384_k1_sm_103a_pdl1|0.181635|0.181764|0.999290x|pass|pass|

|primary_m16384_k4__sm_103a__pdl1|G3|kimi_k3_attn_res_primary_m16384_k4_sm_103a_pdl1|0.279619|0.280484|0.996916x|pass|pass|

|primary_m16384_k8__sm_103a__pdl1|G4|kimi_k3_attn_res_primary_m16384_k8_sm_103a_pdl1|0.418726|0.418934|0.999505x|pass|pass|

|k_sweep_m1_k2__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k2_sm_103a_pdl1|0.003744|0.003744|1.000000x|pass|pass|

|k_sweep_m1_k3__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k3_sm_103a_pdl1|0.004576|0.004576|1.000000x|pass|pass|

|k_sweep_m1_k5__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m1_k5_sm_103a_pdl1|0.004992|0.005055|0.987537x|pass|pass|

|k_sweep_m1_k6__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m1_k6_sm_103a_pdl1|0.005345|0.005408|0.988351x|pass|pass|

|k_sweep_m1_k7__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m1_k7_sm_103a_pdl1|0.005633|0.005632|1.000178x|pass|pass|

|k_sweep_m4096_k2__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k2_sm_103a_pdl1|0.060033|0.060033|1.000000x|pass|pass|

|k_sweep_m4096_k3__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k3_sm_103a_pdl1|0.067681|0.067649|1.000473x|pass|pass|

|k_sweep_m4096_k5__sm_103a__pdl1|G3|kimi_k3_attn_res_k_sweep_m4096_k5_sm_103a_pdl1|0.086529|0.088193|0.981132x|pass|pass|

|k_sweep_m4096_k6__sm_103a__pdl1|G4|kimi_k3_attn_res_k_sweep_m4096_k6_sm_103a_pdl1|0.098050|0.098273|0.997731x|pass|pass|

|k_sweep_m4096_k7__sm_103a__pdl1|G2|kimi_k3_attn_res_k_sweep_m4096_k7_sm_103a_pdl1|0.108641|0.108481|1.001475x|pass|pass|

|semantic_layer0_m1_k0_write0__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_layer0_m1_k0_write0_sm_103a_pdl1|0.004480|0.004480|1.000000x|pass|pass|

|semantic_boundary_m17_k4_write4__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_boundary_m17_k4_write4_sm_103a_pdl1|0.023104|0.023104|1.000000x|pass|pass|

|semantic_boundary_tail_m3_k7_write7__sm_103a__pdl1|G2|kimi_k3_attn_res_semantic_boundary_tail_m3_k7_write7_sm_103a_pdl1|0.026720|0.026689|1.001162x|pass|pass|

|semantic_post_boundary_m17_k4_no_delta__sm_103a__pdl1|G3|kimi_k3_attn_res_semantic_post_boundary_m17_k4_no_delta_sm_103a_pdl1|0.009184|0.009184|1.000000x|pass|pass|

|semantic_final_m7_k8_no_output_norm__sm_103a__pdl1|G4|kimi_k3_attn_res_semantic_final_m7_k8_no_output_norm_sm_103a_pdl1|0.015392|0.015361|1.002018x|pass|pass|

## Per-shape comparison: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape|Baseline ms|Paired export ms|Baseline / Export|
|---|---:|---:|---:|
|primary_m1_k0__sm_100a__pdl0|0.004160|0.003200|1.300000x|
|primary_m1_k1__sm_100a__pdl0|0.004448|0.003808|1.168067x|
|primary_m1_k4__sm_100a__pdl0|0.005312|0.004960|1.070968x|
|primary_m1_k8__sm_100a__pdl0|0.006368|0.005984|1.064171x|
|primary_m2_k0__sm_100a__pdl0|0.004129|0.003264|1.265012x|
|primary_m2_k1__sm_100a__pdl0|0.004511|0.003840|1.174740x|
|primary_m2_k4__sm_100a__pdl0|0.005312|0.005024|1.057325x|
|primary_m2_k8__sm_100a__pdl0|0.006432|0.006048|1.063492x|
|primary_m4_k0__sm_100a__pdl0|0.004224|0.003328|1.269231x|
|primary_m4_k1__sm_100a__pdl0|0.004576|0.003872|1.181818x|
|primary_m4_k4__sm_100a__pdl0|0.005376|0.005056|1.063291x|
|primary_m4_k8__sm_100a__pdl0|0.006496|0.006144|1.057292x|
|primary_m8_k0__sm_100a__pdl0|0.004224|0.003360|1.257143x|
|primary_m8_k1__sm_100a__pdl0|0.004608|0.003936|1.170732x|
|primary_m8_k4__sm_100a__pdl0|0.005472|0.005153|1.061906x|
|primary_m8_k8__sm_100a__pdl0|0.006560|0.006176|1.062176x|
|primary_m16_k0__sm_100a__pdl0|0.004256|0.003360|1.266667x|
|primary_m16_k1__sm_100a__pdl0|0.004672|0.003968|1.177419x|
|primary_m16_k4__sm_100a__pdl0|0.005728|0.005408|1.059172x|
|primary_m16_k8__sm_100a__pdl0|0.006816|0.006624|1.028986x|
|primary_m32_k0__sm_100a__pdl0|0.004384|0.003488|1.256881x|
|primary_m32_k1__sm_100a__pdl0|0.004864|0.004160|1.169231x|
|primary_m32_k4__sm_100a__pdl0|0.006000|0.005728|1.047486x|
|primary_m32_k8__sm_100a__pdl0|0.007200|0.006816|1.056338x|
|primary_m64_k0__sm_100a__pdl0|0.004576|0.003680|1.243478x|
|primary_m64_k1__sm_100a__pdl0|0.005153|0.004480|1.150223x|
|primary_m64_k4__sm_100a__pdl0|0.006528|0.006240|1.046154x|
|primary_m64_k8__sm_100a__pdl0|0.007872|0.007744|1.016529x|
|primary_m128_k0__sm_100a__pdl0|0.005088|0.004255|1.195770x|
|primary_m128_k1__sm_100a__pdl0|0.005888|0.005248|1.121951x|
|primary_m128_k4__sm_100a__pdl0|0.007552|0.007136|1.058296x|
|primary_m128_k8__sm_100a__pdl0|0.008704|0.008608|1.011152x|
|primary_m256_k0__sm_100a__pdl0|0.006784|0.005888|1.152174x|
|primary_m256_k1__sm_100a__pdl0|0.008000|0.007520|1.063830x|
|primary_m256_k4__sm_100a__pdl0|0.010016|0.009920|1.009677x|
|primary_m256_k8__sm_100a__pdl0|0.012896|0.013056|0.987745x|
|primary_m512_k0__sm_100a__pdl0|0.008928|0.008064|1.107143x|
|primary_m512_k1__sm_100a__pdl0|0.010944|0.010400|1.052308x|
|primary_m512_k4__sm_100a__pdl0|0.015391|0.015105|1.018934x|
|primary_m512_k8__sm_100a__pdl0|0.021952|0.021120|1.039394x|
|primary_m1024_k0__sm_100a__pdl0|0.013312|0.012576|1.058524x|
|primary_m1024_k1__sm_100a__pdl0|0.016224|0.015649|1.036744x|
|primary_m1024_k4__sm_100a__pdl0|0.024257|0.023616|1.027121x|
|primary_m1024_k8__sm_100a__pdl0|0.036064|0.033760|1.068246x|
|primary_m2048_k0__sm_100a__pdl0|0.022367|0.021633|1.033930x|
|primary_m2048_k1__sm_100a__pdl0|0.027296|0.026751|1.020373x|
|primary_m2048_k4__sm_100a__pdl0|0.043169|0.041728|1.034533x|
|primary_m2048_k8__sm_100a__pdl0|0.064256|0.060816|1.056564x|
|primary_m4096_k0__sm_100a__pdl0|0.040577|0.040000|1.014425x|
|primary_m4096_k1__sm_100a__pdl0|0.049504|0.048736|1.015758x|
|primary_m4096_k4__sm_100a__pdl0|0.078784|0.079904|0.985989x|
|primary_m4096_k8__sm_100a__pdl0|0.118112|0.114864|1.028277x|
|primary_m8192_k0__sm_100a__pdl0|0.075745|0.075552|1.002555x|
|primary_m8192_k1__sm_100a__pdl0|0.094144|0.093376|1.008225x|
|primary_m8192_k4__sm_100a__pdl0|0.147744|0.145056|1.018531x|
|primary_m8192_k8__sm_100a__pdl0|0.223488|0.212833|1.050063x|
|primary_m16384_k0__sm_100a__pdl0|0.146144|0.146720|0.996074x|
|primary_m16384_k1__sm_100a__pdl0|0.181248|0.179168|1.011609x|
|primary_m16384_k4__sm_100a__pdl0|0.284672|0.277952|1.024177x|
|primary_m16384_k8__sm_100a__pdl0|0.433120|0.410337|1.055523x|
|k_sweep_m1_k2__sm_100a__pdl0|0.004736|0.004096|1.156250x|
|k_sweep_m1_k3__sm_100a__pdl0|0.005120|0.004896|1.045752x|
|k_sweep_m1_k5__sm_100a__pdl0|0.005535|0.005120|1.081055x|
|k_sweep_m1_k6__sm_100a__pdl0|0.005984|0.005600|1.068571x|
|k_sweep_m1_k7__sm_100a__pdl0|0.006112|0.005760|1.061111x|
|k_sweep_m4096_k2__sm_100a__pdl0|0.058784|0.058432|1.006024x|
|k_sweep_m4096_k3__sm_100a__pdl0|0.073024|0.068992|1.058442x|
|k_sweep_m4096_k5__sm_100a__pdl0|0.087009|0.086111|1.010423x|
|k_sweep_m4096_k6__sm_100a__pdl0|0.101536|0.094816|1.070874x|
|k_sweep_m4096_k7__sm_100a__pdl0|0.109216|0.106176|1.028632x|
|primary_m1_k0__sm_100a__pdl1|0.004096|0.003200|1.280000x|
|primary_m1_k1__sm_100a__pdl1|0.004480|0.003776|1.186441x|
|primary_m1_k4__sm_100a__pdl1|0.005312|0.004960|1.070968x|
|primary_m1_k8__sm_100a__pdl1|0.006336|0.005983|1.059001x|
|primary_m2_k0__sm_100a__pdl1|0.004128|0.003264|1.264706x|
|primary_m2_k1__sm_100a__pdl1|0.004544|0.003840|1.183333x|
|primary_m2_k4__sm_100a__pdl1|0.005407|0.005056|1.069422x|
|primary_m2_k8__sm_100a__pdl1|0.006337|0.006015|1.053533x|
|primary_m4_k0__sm_100a__pdl1|0.004129|0.003264|1.265012x|
|primary_m4_k1__sm_100a__pdl1|0.004576|0.003872|1.181818x|
|primary_m4_k4__sm_100a__pdl1|0.005344|0.005056|1.056962x|
|primary_m4_k8__sm_100a__pdl1|0.006400|0.006048|1.058201x|
|primary_m8_k0__sm_100a__pdl1|0.004191|0.003232|1.296720x|
|primary_m8_k1__sm_100a__pdl1|0.004576|0.003936|1.162602x|
|primary_m8_k4__sm_100a__pdl1|0.005504|0.005216|1.055215x|
|primary_m8_k8__sm_100a__pdl1|0.006528|0.006144|1.062500x|
|primary_m16_k0__sm_100a__pdl1|0.004257|0.003360|1.266964x|
|primary_m16_k1__sm_100a__pdl1|0.004640|0.003968|1.169355x|
|primary_m16_k4__sm_100a__pdl1|0.005664|0.005376|1.053571x|
|primary_m16_k8__sm_100a__pdl1|0.006784|0.006433|1.054562x|
|primary_m32_k0__sm_100a__pdl1|0.004384|0.003488|1.256881x|
|primary_m32_k1__sm_100a__pdl1|0.004833|0.004160|1.161779x|
|primary_m32_k4__sm_100a__pdl1|0.006016|0.005728|1.050279x|
|primary_m32_k8__sm_100a__pdl1|0.007200|0.006816|1.056338x|
|primary_m64_k0__sm_100a__pdl1|0.004576|0.003680|1.243478x|
|primary_m64_k1__sm_100a__pdl1|0.005184|0.004544|1.140845x|
|primary_m64_k4__sm_100a__pdl1|0.006656|0.006336|1.050505x|
|primary_m64_k8__sm_100a__pdl1|0.007936|0.007808|1.016393x|
|primary_m128_k0__sm_100a__pdl1|0.005024|0.004160|1.207692x|
|primary_m128_k1__sm_100a__pdl1|0.005824|0.005216|1.116564x|
|primary_m128_k4__sm_100a__pdl1|0.007520|0.007168|1.049107x|
|primary_m128_k8__sm_100a__pdl1|0.008641|0.008640|1.000116x|
|primary_m256_k0__sm_100a__pdl1|0.006688|0.005792|1.154696x|
|primary_m256_k1__sm_100a__pdl1|0.007968|0.007488|1.064103x|
|primary_m256_k4__sm_100a__pdl1|0.009984|0.009920|1.006452x|
|primary_m256_k8__sm_100a__pdl1|0.013184|0.013280|0.992771x|
|primary_m512_k0__sm_100a__pdl1|0.009120|0.008289|1.100253x|
|primary_m512_k1__sm_100a__pdl1|0.010944|0.010368|1.055556x|
|primary_m512_k4__sm_100a__pdl1|0.015456|0.015104|1.023305x|
|primary_m512_k8__sm_100a__pdl1|0.022016|0.021152|1.040847x|
|primary_m1024_k0__sm_100a__pdl1|0.013184|0.012512|1.053708x|
|primary_m1024_k1__sm_100a__pdl1|0.016576|0.015808|1.048583x|
|primary_m1024_k4__sm_100a__pdl1|0.024320|0.023744|1.024259x|
|primary_m1024_k8__sm_100a__pdl1|0.036032|0.033631|1.071392x|
|primary_m2048_k0__sm_100a__pdl1|0.022112|0.021473|1.029758x|
|primary_m2048_k1__sm_100a__pdl1|0.027488|0.026913|1.021365x|
|primary_m2048_k4__sm_100a__pdl1|0.043040|0.041696|1.032233x|
|primary_m2048_k8__sm_100a__pdl1|0.064224|0.060736|1.057429x|
|primary_m4096_k0__sm_100a__pdl1|0.040608|0.040064|1.013578x|
|primary_m4096_k1__sm_100a__pdl1|0.050016|0.049344|1.013619x|
|primary_m4096_k4__sm_100a__pdl1|0.078752|0.078240|1.006544x|
|primary_m4096_k8__sm_100a__pdl1|0.118016|0.114016|1.035083x|
|primary_m8192_k0__sm_100a__pdl1|0.075680|0.075584|1.001270x|
|primary_m8192_k1__sm_100a__pdl1|0.092576|0.091808|1.008365x|
|primary_m8192_k4__sm_100a__pdl1|0.147840|0.146528|1.008954x|
|primary_m8192_k8__sm_100a__pdl1|0.223680|0.213185|1.049230x|
|primary_m16384_k0__sm_100a__pdl1|0.146241|0.146881|0.995643x|
|primary_m16384_k1__sm_100a__pdl1|0.182032|0.178816|1.017982x|
|primary_m16384_k4__sm_100a__pdl1|0.284833|0.276545|1.029970x|
|primary_m16384_k8__sm_100a__pdl1|0.433440|0.410656|1.055482x|
|k_sweep_m1_k2__sm_100a__pdl1|0.004704|0.004128|1.139535x|
|k_sweep_m1_k3__sm_100a__pdl1|0.005153|0.004896|1.052492x|
|k_sweep_m1_k5__sm_100a__pdl1|0.005536|0.005120|1.081250x|
|k_sweep_m1_k6__sm_100a__pdl1|0.005952|0.005568|1.068966x|
|k_sweep_m1_k7__sm_100a__pdl1|0.006145|0.005920|1.038007x|
|k_sweep_m4096_k2__sm_100a__pdl1|0.059648|0.058880|1.013043x|
|k_sweep_m4096_k3__sm_100a__pdl1|0.072896|0.068831|1.059058x|
|k_sweep_m4096_k5__sm_100a__pdl1|0.086976|0.086080|1.010409x|
|k_sweep_m4096_k6__sm_100a__pdl1|0.101504|0.094656|1.072346x|
|k_sweep_m4096_k7__sm_100a__pdl1|0.109216|0.106047|1.029883x|
|primary_m1_k0__sm_103a__pdl0|0.003840|0.002976|1.290323x|
|primary_m1_k1__sm_103a__pdl0|0.004160|0.003584|1.160714x|
|primary_m1_k4__sm_103a__pdl0|0.004960|0.004800|1.033333x|
|primary_m1_k8__sm_103a__pdl0|0.005985|0.005760|1.039062x|
|primary_m2_k0__sm_103a__pdl0|0.003840|0.003040|1.263158x|
|primary_m2_k1__sm_103a__pdl0|0.004160|0.003584|1.160714x|
|primary_m2_k4__sm_103a__pdl0|0.004960|0.004768|1.040268x|
|primary_m2_k8__sm_103a__pdl0|0.006048|0.005889|1.026999x|
|primary_m4_k0__sm_103a__pdl0|0.003872|0.003072|1.260417x|
|primary_m4_k1__sm_103a__pdl0|0.004160|0.003584|1.160714x|
|primary_m4_k4__sm_103a__pdl0|0.005024|0.004832|1.039735x|
|primary_m4_k8__sm_103a__pdl0|0.006048|0.005920|1.021622x|
|primary_m8_k0__sm_103a__pdl0|0.003936|0.003104|1.268041x|
|primary_m8_k1__sm_103a__pdl0|0.004256|0.003649|1.166347x|
|primary_m8_k4__sm_103a__pdl0|0.005088|0.004896|1.039216x|
|primary_m8_k8__sm_103a__pdl0|0.006176|0.006048|1.021164x|
|primary_m16_k0__sm_103a__pdl0|0.003968|0.003231|1.228103x|
|primary_m16_k1__sm_103a__pdl0|0.004288|0.003808|1.126050x|
|primary_m16_k4__sm_103a__pdl0|0.005248|0.005056|1.037975x|
|primary_m16_k8__sm_103a__pdl0|0.006305|0.006176|1.020887x|
|primary_m32_k0__sm_103a__pdl0|0.004065|0.003360|1.209821x|
|primary_m32_k1__sm_103a__pdl0|0.004480|0.004000|1.120000x|
|primary_m32_k4__sm_103a__pdl0|0.005632|0.005472|1.029240x|
|primary_m32_k8__sm_103a__pdl0|0.006784|0.006656|1.019231x|
|primary_m64_k0__sm_103a__pdl0|0.004288|0.003553|1.206867x|
|primary_m64_k1__sm_103a__pdl0|0.004928|0.004384|1.124088x|
|primary_m64_k4__sm_103a__pdl0|0.006368|0.006145|1.036290x|
|primary_m64_k8__sm_103a__pdl0|0.007456|0.007360|1.013043x|
|primary_m128_k0__sm_103a__pdl0|0.004864|0.004096|1.187500x|
|primary_m128_k1__sm_103a__pdl0|0.005584|0.005152|1.083851x|
|primary_m128_k4__sm_103a__pdl0|0.007296|0.007072|1.031674x|
|primary_m128_k8__sm_103a__pdl0|0.008512|0.008448|1.007576x|
|primary_m256_k0__sm_103a__pdl0|0.006336|0.005600|1.131429x|
|primary_m256_k1__sm_103a__pdl0|0.007648|0.007297|1.048102x|
|primary_m256_k4__sm_103a__pdl0|0.009760|0.009440|1.033898x|
|primary_m256_k8__sm_103a__pdl0|0.012640|0.012608|1.002538x|
|primary_m512_k0__sm_103a__pdl0|0.008672|0.008129|1.066798x|
|primary_m512_k1__sm_103a__pdl0|0.010623|0.010016|1.060603x|
|primary_m512_k4__sm_103a__pdl0|0.015168|0.015040|1.008511x|
|primary_m512_k8__sm_103a__pdl0|0.021792|0.021185|1.028652x|
|primary_m1024_k0__sm_103a__pdl0|0.013216|0.012640|1.045570x|
|primary_m1024_k1__sm_103a__pdl0|0.015968|0.015744|1.014228x|
|primary_m1024_k4__sm_103a__pdl0|0.024449|0.023840|1.025545x|
|primary_m1024_k8__sm_103a__pdl0|0.036512|0.034817|1.048683x|
|primary_m2048_k0__sm_103a__pdl0|0.022688|0.022016|1.030523x|
|primary_m2048_k1__sm_103a__pdl0|0.027328|0.027104|1.008264x|
|primary_m2048_k4__sm_103a__pdl0|0.044001|0.042016|1.047244x|
|primary_m2048_k8__sm_103a__pdl0|0.064865|0.062465|1.038422x|
|primary_m4096_k0__sm_103a__pdl0|0.040704|0.040096|1.015164x|
|primary_m4096_k1__sm_103a__pdl0|0.049377|0.049313|1.001298x|
|primary_m4096_k4__sm_103a__pdl0|0.080193|0.078177|1.025788x|
|primary_m4096_k8__sm_103a__pdl0|0.119202|0.117025|1.018603x|
|primary_m8192_k0__sm_103a__pdl0|0.077505|0.076737|1.010008x|
|primary_m8192_k1__sm_103a__pdl0|0.093920|0.093729|1.002038x|
|primary_m8192_k4__sm_103a__pdl0|0.150882|0.146178|1.032180x|
|primary_m8192_k8__sm_103a__pdl0|0.226019|0.217987|1.036846x|
|primary_m16384_k0__sm_103a__pdl0|0.148321|0.148034|1.001939x|
|primary_m16384_k1__sm_103a__pdl0|0.181762|0.181091|1.003705x|
|primary_m16384_k4__sm_103a__pdl0|0.290980|0.280260|1.038250x|
|primary_m16384_k8__sm_103a__pdl0|0.436869|0.419077|1.042455x|
|k_sweep_m1_k2__sm_103a__pdl0|0.004383|0.003776|1.160752x|
|k_sweep_m1_k3__sm_103a__pdl0|0.004704|0.004577|1.027747x|
|k_sweep_m1_k5__sm_103a__pdl0|0.005088|0.005024|1.012739x|
|k_sweep_m1_k6__sm_103a__pdl0|0.005632|0.005472|1.029240x|
|k_sweep_m1_k7__sm_103a__pdl0|0.005824|0.005632|1.034091x|
|k_sweep_m4096_k2__sm_103a__pdl0|0.059809|0.059776|1.000552x|
|k_sweep_m4096_k3__sm_103a__pdl0|0.073553|0.067073|1.096619x|
|k_sweep_m4096_k5__sm_103a__pdl0|0.088321|0.088225|1.001088x|
|k_sweep_m4096_k6__sm_103a__pdl0|0.102625|0.098146|1.045636x|
|k_sweep_m4096_k7__sm_103a__pdl0|0.110114|0.108257|1.017154x|
|primary_m1_k0__sm_103a__pdl1|0.003808|0.002944|1.293478x|
|primary_m1_k1__sm_103a__pdl1|0.004192|0.003584|1.169643x|
|primary_m1_k4__sm_103a__pdl1|0.004928|0.004704|1.047619x|
|primary_m1_k8__sm_103a__pdl1|0.006016|0.005728|1.050279x|
|primary_m2_k0__sm_103a__pdl1|0.003872|0.003072|1.260417x|
|primary_m2_k1__sm_103a__pdl1|0.004129|0.003552|1.162444x|
|primary_m2_k4__sm_103a__pdl1|0.004960|0.004768|1.040268x|
|primary_m2_k8__sm_103a__pdl1|0.006080|0.005824|1.043956x|
|primary_m4_k0__sm_103a__pdl1|0.003936|0.003072|1.281250x|
|primary_m4_k1__sm_103a__pdl1|0.004160|0.003616|1.150442x|
|primary_m4_k4__sm_103a__pdl1|0.004992|0.004768|1.046980x|
|primary_m4_k8__sm_103a__pdl1|0.006049|0.005824|1.038633x|
|primary_m8_k0__sm_103a__pdl1|0.003936|0.003104|1.268041x|
|primary_m8_k1__sm_103a__pdl1|0.004192|0.003648|1.149123x|
|primary_m8_k4__sm_103a__pdl1|0.005120|0.004896|1.045752x|
|primary_m8_k8__sm_103a__pdl1|0.006176|0.005888|1.048913x|
|primary_m16_k0__sm_103a__pdl1|0.004000|0.003264|1.225490x|
|primary_m16_k1__sm_103a__pdl1|0.004289|0.003808|1.126313x|
|primary_m16_k4__sm_103a__pdl1|0.005248|0.005056|1.037975x|
|primary_m16_k8__sm_103a__pdl1|0.006400|0.006208|1.030928x|
|primary_m32_k0__sm_103a__pdl1|0.004096|0.003360|1.219048x|
|primary_m32_k1__sm_103a__pdl1|0.004512|0.004000|1.128000x|
|primary_m32_k4__sm_103a__pdl1|0.005663|0.005440|1.040993x|
|primary_m32_k8__sm_103a__pdl1|0.006816|0.006592|1.033981x|
|primary_m64_k0__sm_103a__pdl1|0.004352|0.003584|1.214286x|
|primary_m64_k1__sm_103a__pdl1|0.004896|0.004384|1.116788x|
|primary_m64_k4__sm_103a__pdl1|0.006337|0.006144|1.031413x|
|primary_m64_k8__sm_103a__pdl1|0.007455|0.007232|1.030835x|
|primary_m128_k0__sm_103a__pdl1|0.004800|0.004097|1.171589x|
|primary_m128_k1__sm_103a__pdl1|0.005632|0.005153|1.092956x|
|primary_m128_k4__sm_103a__pdl1|0.007232|0.007008|1.031963x|
|primary_m128_k8__sm_103a__pdl1|0.008480|0.008321|1.019108x|
|primary_m256_k0__sm_103a__pdl1|0.006465|0.005728|1.128666x|
|primary_m256_k1__sm_103a__pdl1|0.007617|0.007360|1.034918x|
|primary_m256_k4__sm_103a__pdl1|0.009761|0.009504|1.027041x|
|primary_m256_k8__sm_103a__pdl1|0.012672|0.012640|1.002532x|
|primary_m512_k0__sm_103a__pdl1|0.008577|0.008000|1.072125x|
|primary_m512_k1__sm_103a__pdl1|0.010528|0.009984|1.054487x|
|primary_m512_k4__sm_103a__pdl1|0.015200|0.015009|1.012726x|
|primary_m512_k8__sm_103a__pdl1|0.021857|0.021536|1.014905x|
|primary_m1024_k0__sm_103a__pdl1|0.013280|0.012608|1.053299x|
|primary_m1024_k1__sm_103a__pdl1|0.015904|0.015584|1.020534x|
|primary_m1024_k4__sm_103a__pdl1|0.024736|0.024064|1.027926x|
|primary_m1024_k8__sm_103a__pdl1|0.036480|0.034496|1.057514x|
|primary_m2048_k0__sm_103a__pdl1|0.022656|0.022048|1.027576x|
|primary_m2048_k1__sm_103a__pdl1|0.027073|0.026752|1.011999x|
|primary_m2048_k4__sm_103a__pdl1|0.044032|0.042017|1.047957x|
|primary_m2048_k8__sm_103a__pdl1|0.064993|0.062497|1.039938x|
|primary_m4096_k0__sm_103a__pdl1|0.040672|0.040064|1.015176x|
|primary_m4096_k1__sm_103a__pdl1|0.049537|0.049344|1.003911x|
|primary_m4096_k4__sm_103a__pdl1|0.080449|0.078528|1.024456x|
|primary_m4096_k8__sm_103a__pdl1|0.119393|0.117250|1.018277x|
|primary_m8192_k0__sm_103a__pdl1|0.077633|0.076928|1.009164x|
|primary_m8192_k1__sm_103a__pdl1|0.094209|0.093889|1.003408x|
|primary_m8192_k4__sm_103a__pdl1|0.150817|0.145569|1.036052x|
|primary_m8192_k8__sm_103a__pdl1|0.226211|0.218754|1.034089x|
|primary_m16384_k0__sm_103a__pdl1|0.148322|0.147969|1.002386x|
|primary_m16384_k1__sm_103a__pdl1|0.182340|0.181764|1.003169x|
|primary_m16384_k4__sm_103a__pdl1|0.290916|0.280484|1.037193x|
|primary_m16384_k8__sm_103a__pdl1|0.436966|0.418934|1.043044x|
|k_sweep_m1_k2__sm_103a__pdl1|0.004352|0.003744|1.162393x|
|k_sweep_m1_k3__sm_103a__pdl1|0.004736|0.004576|1.034965x|
|k_sweep_m1_k5__sm_103a__pdl1|0.005152|0.005055|1.019189x|
|k_sweep_m1_k6__sm_103a__pdl1|0.005569|0.005408|1.029771x|
|k_sweep_m1_k7__sm_103a__pdl1|0.005824|0.005632|1.034091x|
|k_sweep_m4096_k2__sm_103a__pdl1|0.060065|0.060033|1.000533x|
|k_sweep_m4096_k3__sm_103a__pdl1|0.073601|0.067649|1.087984x|
|k_sweep_m4096_k5__sm_103a__pdl1|0.088673|0.088193|1.005443x|
|k_sweep_m4096_k6__sm_103a__pdl1|0.102721|0.098273|1.045262x|
|k_sweep_m4096_k7__sm_103a__pdl1|0.110082|0.108481|1.014758x|

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

|Shape tag|Timed rows|Denominator|Source ms|Export ms|Source / Export|
|---|---:|---:|---:|---:|---:|
|all|300|300|0.013532|0.013512|1.001438x|
|correctness|20|20|0.013435|0.013472|0.997295x|
|full_k_sweep|72|72|0.018475|0.018478|0.999854x|
|pdl_off|150|150|0.013529|0.013514|1.001107x|
|pdl_on|150|150|0.013534|0.013510|1.001768x|
|perf|280|280|0.013539|0.013515|1.001734x|
|primary_geomean|240|240|0.012678|0.012648|1.002361x|

### Geomeans: pinned vLLM SM100f native CUDA AttnRes op
(csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu)

|Shape tag|Timed rows|Denominator|Baseline ms|Paired export ms|Baseline
/ Export|
|---|---:|---:|---:|---:|---:|
|all|280|280|0.014505|0.013515|1.073240x|
|full_k_sweep|72|72|0.019599|0.018478|1.060660x|
|pdl_off|140|140|0.014503|0.013523|1.072508x|
|pdl_on|140|140|0.014507|0.013507|1.073973x|
|perf|280|280|0.014505|0.013515|1.073240x|
|primary_geomean|240|240|0.013625|0.012648|1.077260x|

Complete denominator: **true** (300/300).

All gates passed: **true** (300/300).
## What changed in this revision

This revision regenerates the delivery from the exporter with the
duplication removed at its source; no emitted file was hand-edited.

- **Generated kernel files: 110 -> 50** (50 distinct bodies, no
identical-body or per-architecture-copy findings; the only remaining
constant-clone findings are the declared `NUM_BLOCKS`
persistent-schedule axis). SM100 and SM103 programs whose generated text
is identical are delivered once and shared.
- **PDL is a launch argument.** Each program takes an `enable_pdl` entry
argument and sets the programmatic-dependent-launch attribute
conditionally; the grid-dependency instructions are emitted
unconditionally. The former PDL-off program copies are gone. Cost: the
PDL-off launches of the small-M token-per-CTA kernels (about 3.6 us) now
run the former PDL-on body and measure 2 to 6 % slower than the previous
delivery on sm_100a; their `vLLM / export` ratios stay 1.12 or better
(table below).
- **Persistent variants that only PDL-off launches selected** are now
explicit per-cell route flags (route key
`persistent:k<K>_nc<NC>_d<D>_f<15 bits>`), so the host dispatcher and
the exporter agree on one key per cell.
- **Direct bootstrap route** keeps `K`, `has_delta`, `write_block` and
`apply_output_norm` as compile-time specializations (route key
`direct:k<K>_d<d>_w<w>_n<n>`); a runtime-parameter variant was measured
1.1-3.3x slower on the semantic rows and rejected.
- No shared-header bundle, no per-architecture duplicate modules, no
`.pre-commit-config.yaml` change; the generated directory opts out of
clang-format through its own `.clang-format`.
- Rebased onto `883825a2` so the branch fast-forwards onto `main`.

## Baselines and their source PRs

- **Cake production AttnRes launcher** (parity arm, `source / export`
ratios): the same generated programs launched through the Cake
production dispatcher at the producer revision recorded in the summary.
Source and export arms run on identical tensors inside one
CUPTI-interleaved window per group.
- **vLLM native CUDA AttnRes op** (external baseline, `baseline /
export` ratios): `csrc/libtorch_stable/kimi_k3/attn_res_kernel.cu` from
https://github.com/vllm-project/vllm at revision
`ee3c00bbf47e0ef7e975705cc980b06ee5576bb0`, built with the torch C++
extension at run time. Upstream PRs that define this kernel:
- vllm-project/vllm#50090 (`61ac3680`, 2026-07-28) — add AttnRes kernels
- vllm-project/vllm#50567 (`41ba11b8`, 2026-08-04) — enforce packed rows
and op availability in AttnRes dispatch
- vllm-project/vllm#50185 (`7b4ed496`, 2026-08-06) — attn_res kernel
latency improvements
- vllm-project/vllm#54261 (`d6d66585`, 2026-08-31) — make native CUDA
AttnRes the SM100 default
- **Correctness oracle**: FP32 PyTorch reference of the AttnRes op (BF16
outputs checked at atol 0.08 / rtol 0.03; in-place state bit-exact),
applied to source, export and vLLM arms before and after every timed
window.

## Acceptance

Every perf row must satisfy `vLLM / export >= 0.97` (owner decision
2026-10-01). Final measurement at Cake producer `c3fb15f3fed` against
this scaffold (`071266a0e`; sm_100a on 3x B200, sm_103a on 3x B300,
CUPTI timing under the frozen protocol): 300 of 300 shape rows pass; of
the 280 rows that carry the vLLM baseline, 276 are >= 1.0 and the
remaining rows are:

| row | vLLM / export |
| --- | --- |
| primary_m256_k8 (sm_100a, pdl0 / pdl1) | 0.9805 / 0.9805 |
| primary_m16384_k0 (sm_100a, pdl0 / pdl1) | 0.9961 / 0.9961 |

Geomean of `vLLM / export` over the perf rows: 1.080 (sm_100a), 1.067
(sm_103a). Compared with the previous delivery of this PR (110 files,
measured at scaffold `3c4823837`), the per-shape export timings are
unchanged within run-to-run noise (geomean before/after 0.998 on
sm_100a, 0.999 on sm_103a) except for the PDL-off small-M token-per-CTA
rows noted above (worst 0.941 on sm_100a primary_m1_k1, 0.963 on sm_103a
primary_m128_k1); sm_103a has no row below 1.0 against vLLM in this
revision. The sm_103a stage was measured on a separate cluster and
retained into this delivery through the runner's exact-input-closure
proof (byte-identical generated kernel and binding sources; see
`prior_execution` in the per-shape receipts).

## CI

```
/bot run tests/experimental/test_cake_kimi_k3_attn_res.py
@flashinfer-bot run tests/experimental/test_cake_kimi_k3_attn_res.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [122037a](https://github.com/flashinfer-ai/flashinfer/commit/122037aaa23f068578e8a741586de22f42abf27b)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-01T19:11:01Z
- **提交信息**: Add SM12x NVFP4 support to the CuTe DSL GEMM backend (#5100)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds native SM120/SM121 NVFP4 W4A4 kernels to `mm_fp4(...,
backend="cute-dsl")`. The kernels consume canonical packed weights and
physical 128x4 E4M3 scales directly, without repacking or a second
weight copy. Sharing these buffers with W4A16 in #5242 enables dynamic
W4A4/W4A16 selection.

Independent staged kernels handle small and ragged shapes; persistent
ping-pong kernels handle aligned larger shapes. Support includes
positive M, N/K divisible by 64, BF16 output, live GPU alpha and CUDA
graph replay.

**Performance on DGX Spark (SM121):** the 27B down projection (`N=5120,
K=17408`) is **1.69x faster at M=4096 and 2.13x at M=8192 than default
CUTLASS**, or **1.17x and 1.41x with both backends autotuned**. Geomeans
across the measured shapes:

| Shapes | Count | Default speedup | Autotuned speedup |
|---|---:|---:|---:|
| Official, M <= 16 | 78 | 1.208x | 1.071x |
| Official, M = 64 | 32 | 1.078x | 1.052x |
| Official, M >= 128 | 49 | 0.970x | 0.942x |
| All official shapes | 159 | 1.103x | 1.026x |
| 27B, M = 4096/8192 | 4 | 1.408x | 1.126x |

Speedup = CUTLASS latency / CuTe latency, matching default with default
and autotuned with autotuned. Commit `5d97fec`, CUDA 13, CuTe DSL 4.7.1,
BF16, cold-L2 CUPTI CUDA graphs; median of three shuffled passes with
100 repetitions each. The SM clock request was 1500 MHz; sustained-load
medians were 1404 MHz for the official grid and 1469 MHz for the four
supplemental cases.

<details>
<summary>Full performance table: 159 official shapes and four 27B
large-M cases</summary>

| M | N | K | CUTLASS default (us) | CUTLASS tuned (us) | CuTe default
(us) | CuTe tuned (us) | Default speedup | Tuned speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 1856 | 2688 | 34.896 | 34.848 | 32.353 | 32.352 | 1.079x | 1.077x
|
| 128 | 1856 | 2688 | 37.904 | 39.329 | 38.592 | 38.593 | 0.982x |
1.019x |
| 2000 | 1856 | 2688 | 147.553 | 130.161 | 147.217 | 147.681 | 1.002x |
0.881x |
| 1 | 2688 | 1856 | 40.800 | 39.232 | 36.513 | 36.480 | 1.117x | 1.075x
|
| 128 | 2688 | 1856 | 44.640 | 42.352 | 44.112 | 44.032 | 1.012x |
0.962x |
| 2000 | 2688 | 1856 | 161.569 | 137.856 | 147.601 | 149.729 | 1.095x |
0.921x |
| 1 | 3712 | 2688 | 60.080 | 63.169 | 57.280 | 57.409 | 1.049x | 1.100x
|
| 128 | 3712 | 2688 | 65.585 | 66.081 | 64.320 | 64.032 | 1.020x |
1.032x |
| 2000 | 3712 | 2688 | 257.410 | 219.553 | 233.922 | 233.969 | 1.100x |
0.938x |
| 1 | 2688 | 3712 | 59.152 | 59.264 | 56.240 | 56.273 | 1.052x | 1.053x
|
| 128 | 2688 | 3712 | 64.608 | 69.473 | 64.865 | 64.977 | 0.996x |
1.069x |
| 2000 | 2688 | 3712 | 235.425 | 215.889 | 246.065 | 245.985 | 0.957x |
0.878x |
| 1 | 1024 | 7168 | 50.784 | 38.513 | 37.248 | 37.216 | 1.363x | 1.035x
|
| 4 | 1024 | 7168 | 51.104 | 38.960 | 38.176 | 38.144 | 1.339x | 1.021x
|
| 16 | 1024 | 7168 | 50.688 | 39.153 | 38.704 | 38.720 | 1.310x | 1.011x
|
| 256 | 1024 | 7168 | 63.521 | 63.392 | 64.706 | 64.001 | 0.982x |
0.990x |
| 1024 | 1024 | 7168 | 129.296 | 118.305 | 128.225 | 128.128 | 1.008x |
0.923x |
| 1 | 7168 | 512 | 30.768 | 26.368 | 23.968 | 23.968 | 1.284x | 1.100x |
| 4 | 7168 | 512 | 27.728 | 25.376 | 22.528 | 22.592 | 1.231x | 1.123x |
| 16 | 7168 | 512 | 28.448 | 25.728 | 23.488 | 23.552 | 1.211x | 1.092x
|
| 64 | 7168 | 512 | 32.992 | 28.288 | 30.240 | 27.616 | 1.091x | 1.024x
|
| 256 | 7168 | 512 | 53.216 | 44.016 | 41.921 | 41.936 | 1.269x | 1.050x
|
| 1024 | 7168 | 512 | 113.857 | 99.537 | 103.505 | 103.393 | 1.100x |
0.963x |
| 1 | 7168 | 4608 | 168.128 | 149.137 | 140.561 | 140.433 | 1.196x |
1.062x |
| 4 | 7168 | 4608 | 170.226 | 151.376 | 141.072 | 140.961 | 1.207x |
1.074x |
| 16 | 7168 | 4608 | 169.441 | 150.113 | 142.145 | 142.097 | 1.192x |
1.056x |
| 64 | 7168 | 4608 | 166.753 | 150.753 | 143.905 | 151.857 | 1.159x |
0.993x |
| 256 | 7168 | 4608 | 171.009 | 159.153 | 181.233 | 175.665 | 0.944x |
0.906x |
| 1024 | 7168 | 4608 | 355.618 | 339.730 | 335.090 | 335.266 | 1.061x |
1.013x |
| 1 | 9216 | 7168 | 265.890 | 223.153 | 215.938 | 215.777 | 1.231x |
1.034x |
| 4 | 9216 | 7168 | 261.570 | 224.338 | 214.226 | 214.161 | 1.221x |
1.048x |
| 16 | 9216 | 7168 | 254.401 | 224.722 | 214.161 | 214.257 | 1.188x |
1.049x |
| 64 | 9216 | 7168 | 237.569 | 221.841 | 220.033 | 220.017 | 1.080x |
1.008x |
| 256 | 9216 | 7168 | 240.754 | 239.522 | 237.377 | 236.961 | 1.014x |
1.011x |
| 1024 | 9216 | 7168 | 615.732 | 587.876 | 668.083 | 667.797 | 0.922x |
0.880x |
| 1 | 512 | 7168 | 48.416 | 27.120 | 23.072 | 23.072 | 2.098x | 1.175x |
| 4 | 512 | 7168 | 47.969 | 42.033 | 23.072 | 22.960 | 2.079x | 1.831x |
| 16 | 512 | 7168 | 47.968 | 25.313 | 22.592 | 22.592 | 2.123x | 1.120x
|
| 64 | 512 | 7168 | 47.937 | 30.000 | 29.184 | 29.120 | 1.643x | 1.030x
|
| 256 | 512 | 7168 | 51.488 | 43.377 | 54.720 | 39.904 | 0.941x | 1.087x
|
| 1024 | 512 | 7168 | 72.769 | 74.272 | 114.576 | 84.864 | 0.635x |
0.875x |
| 1 | 7168 | 256 | 19.344 | 15.296 | 13.856 | 13.824 | 1.396x | 1.106x |
| 4 | 7168 | 256 | 18.080 | 14.496 | 13.264 | 13.216 | 1.363x | 1.097x |
| 16 | 7168 | 256 | 18.800 | 15.408 | 14.832 | 14.848 | 1.268x | 1.038x
|
| 64 | 7168 | 256 | 20.000 | 19.120 | 22.496 | 16.912 | 0.889x | 1.131x
|
| 256 | 7168 | 256 | 43.056 | 43.136 | 32.257 | 43.872 | 1.335x | 0.983x
|
| 1024 | 7168 | 256 | 112.273 | 96.161 | 95.249 | 95.425 | 1.179x |
1.008x |
| 4 | 7168 | 2304 | 92.289 | 85.953 | 85.025 | 84.960 | 1.085x | 1.012x
|
| 16 | 7168 | 2304 | 93.873 | 86.305 | 85.424 | 85.280 | 1.099x | 1.012x
|
| 64 | 7168 | 2304 | 93.856 | 88.448 | 90.528 | 86.849 | 1.037x | 1.018x
|
| 256 | 7168 | 2304 | 107.153 | 102.209 | 114.145 | 110.433 | 0.939x |
0.926x |
| 1 | 4608 | 7168 | 149.041 | 146.129 | 140.800 | 140.945 | 1.059x |
1.037x |
| 4 | 4608 | 7168 | 152.017 | 147.009 | 140.993 | 140.961 | 1.078x |
1.043x |
| 16 | 4608 | 7168 | 150.977 | 146.849 | 141.793 | 141.744 | 1.065x |
1.036x |
| 64 | 4608 | 7168 | 149.409 | 147.137 | 144.113 | 146.401 | 1.037x |
1.005x |
| 256 | 4608 | 7168 | 167.265 | 152.096 | 172.721 | 161.297 | 0.968x |
0.943x |
| 1024 | 4608 | 7168 | 323.746 | 294.002 | 365.762 | 365.794 | 0.885x |
0.804x |
| 1 | 896 | 1024 | 13.120 | 8.912 | 7.488 | 7.504 | 1.752x | 1.188x |
| 4 | 896 | 1024 | 13.408 | 9.312 | 8.192 | 8.192 | 1.637x | 1.137x |
| 16 | 896 | 1024 | 13.440 | 9.216 | 8.624 | 8.640 | 1.558x | 1.067x |
| 64 | 896 | 1024 | 13.536 | 13.696 | 10.464 | 9.600 | 1.294x | 1.427x |
| 256 | 896 | 1024 | 18.944 | 17.376 | 19.552 | 19.536 | 0.969x | 0.889x
|
| 1024 | 896 | 1024 | 39.936 | 38.129 | 37.344 | 37.120 | 1.069x |
1.027x |
| 1 | 10240 | 8192 | 322.194 | 265.874 | 253.521 | 253.474 | 1.271x |
1.049x |
| 8 | 10240 | 8192 | 304.466 | 269.394 | 254.369 | 254.274 | 1.197x |
1.059x |
| 64 | 10240 | 8192 | 270.913 | 265.874 | 262.577 | 262.562 | 1.032x |
1.013x |
| 512 | 10240 | 8192 | 427.123 | 420.514 | 494.563 | 459.890 | 0.864x |
0.914x |
| 1 | 8192 | 8192 | 286.898 | 226.625 | 217.026 | 217.137 | 1.322x |
1.044x |
| 8 | 8192 | 8192 | 274.818 | 226.065 | 216.562 | 216.657 | 1.269x |
1.043x |
| 64 | 8192 | 8192 | 261.522 | 229.089 | 222.417 | 222.578 | 1.176x |
1.029x |
| 512 | 8192 | 8192 | 376.114 | 355.410 | 384.899 | 385.298 | 0.977x |
0.922x |
| 1 | 8192 | 28672 | 873.302 | 616.419 | 586.388 | 586.340 | 1.489x |
1.051x |
| 8 | 8192 | 28672 | 858.485 | 623.443 | 590.580 | 590.516 | 1.454x |
1.056x |
| 64 | 8192 | 28672 | 700.293 | 633.076 | 623.492 | 623.156 | 1.123x |
1.016x |
| 512 | 8192 | 28672 | 1224.808 | 1129.863 | 1413.016 | 1291.927 |
0.867x | 0.875x |
| 1 | 7168 | 5120 | 181.873 | 160.193 | 149.889 | 149.889 | 1.213x |
1.069x |
| 8 | 7168 | 5120 | 183.249 | 161.825 | 150.433 | 150.545 | 1.218x |
1.075x |
| 64 | 7168 | 5120 | 177.249 | 161.281 | 156.929 | 160.689 | 1.129x |
1.004x |
| 512 | 7168 | 5120 | 220.001 | 208.481 | 224.306 | 224.338 | 0.981x |
0.929x |
| 1 | 5120 | 5120 | 132.225 | 128.449 | 122.497 | 122.337 | 1.079x |
1.050x |
| 8 | 5120 | 5120 | 142.065 | 140.224 | 126.256 | 126.192 | 1.125x |
1.111x |
| 64 | 5120 | 5120 | 126.497 | 125.792 | 122.385 | 123.953 | 1.034x |
1.015x |
| 512 | 5120 | 5120 | 179.569 | 172.498 | 211.169 | 186.033 | 0.850x |
0.927x |
| 1 | 5120 | 16384 | 320.337 | 272.721 | 259.714 | 259.346 | 1.233x |
1.052x |
| 8 | 5120 | 16384 | 322.002 | 280.817 | 261.265 | 261.265 | 1.232x |
1.075x |
| 64 | 5120 | 16384 | 340.882 | 287.906 | 333.411 | 281.777 | 1.022x |
1.022x |
| 512 | 5120 | 16384 | 522.867 | 467.123 | 646.068 | 568.244 | 0.809x |
0.822x |
| 1 | 5120 | 8192 | 177.617 | 169.906 | 161.985 | 162.209 | 1.097x |
1.047x |
| 8 | 5120 | 8192 | 175.969 | 169.953 | 163.313 | 163.377 | 1.077x |
1.040x |
| 64 | 5120 | 8192 | 173.153 | 171.137 | 165.425 | 169.728 | 1.047x |
1.008x |
| 512 | 5120 | 8192 | 265.762 | 244.737 | 284.945 | 284.786 | 0.933x |
0.859x |
| 1 | 8192 | 4096 | 167.249 | 149.441 | 143.393 | 143.537 | 1.166x |
1.041x |
| 8 | 8192 | 4096 | 171.809 | 155.713 | 145.473 | 145.537 | 1.181x |
1.070x |
| 64 | 8192 | 4096 | 157.873 | 146.753 | 141.666 | 144.433 | 1.114x |
1.016x |
| 512 | 8192 | 4096 | 210.034 | 209.617 | 206.161 | 206.128 | 1.019x |
1.017x |
| 1 | 8192 | 14336 | 462.595 | 347.298 | 329.922 | 329.922 | 1.402x |
1.053x |
| 8 | 8192 | 14336 | 456.707 | 358.562 | 329.809 | 330.290 | 1.385x |
1.086x |
| 64 | 8192 | 14336 | 396.226 | 349.331 | 340.994 | 340.658 | 1.162x |
1.025x |
| 512 | 8192 | 14336 | 619.860 | 557.219 | 661.940 | 661.620 | 0.936x |
0.842x |
| 1 | 3584 | 5120 | 93.616 | 109.120 | 92.737 | 92.704 | 1.009x | 1.177x
|
| 8 | 3584 | 5120 | 93.168 | 104.897 | 92.305 | 92.304 | 1.009x | 1.136x
|
| 64 | 3584 | 5120 | 95.472 | 105.712 | 97.856 | 95.376 | 0.976x |
1.108x |
| 512 | 3584 | 5120 | 147.521 | 139.297 | 156.017 | 156.161 | 0.946x |
0.892x |
| 1 | 5120 | 2560 | 69.233 | 68.672 | 67.216 | 67.216 | 1.030x | 1.022x
|
| 8 | 5120 | 2560 | 67.424 | 68.193 | 67.969 | 68.032 | 0.992x | 1.002x
|
| 64 | 5120 | 2560 | 71.137 | 69.873 | 70.401 | 68.609 | 1.010x | 1.018x
|
| 512 | 5120 | 2560 | 111.745 | 107.825 | 126.625 | 114.960 | 0.882x |
0.938x |
| 1 | 5120 | 4096 | 107.905 | 106.624 | 103.105 | 103.120 | 1.047x |
1.034x |
| 8 | 5120 | 4096 | 105.920 | 105.600 | 102.129 | 102.336 | 1.037x |
1.032x |
| 64 | 5120 | 4096 | 110.368 | 109.904 | 108.096 | 107.713 | 1.021x |
1.020x |
| 512 | 5120 | 4096 | 149.057 | 150.065 | 176.305 | 155.345 | 0.845x |
0.966x |
| 1 | 2560 | 8192 | 106.113 | 105.201 | 99.808 | 99.841 | 1.063x |
1.054x |
| 8 | 2560 | 8192 | 108.257 | 106.865 | 103.025 | 102.913 | 1.051x |
1.038x |
| 64 | 2560 | 8192 | 109.249 | 105.856 | 102.192 | 105.857 | 1.069x |
1.000x |
| 512 | 2560 | 8192 | 155.313 | 144.032 | 174.865 | 153.857 | 0.888x |
0.936x |
| 1 | 8192 | 2048 | 89.633 | 86.481 | 86.720 | 86.672 | 1.034x | 0.998x
|
| 8 | 8192 | 2048 | 87.488 | 85.872 | 83.488 | 83.472 | 1.048x | 1.029x
|
| 64 | 8192 | 2048 | 92.785 | 91.744 | 92.145 | 90.416 | 1.007x | 1.015x
|
| 512 | 8192 | 2048 | 130.272 | 123.905 | 119.505 | 119.681 | 1.090x |
1.035x |
| 1 | 8192 | 7168 | 252.561 | 207.058 | 199.089 | 199.009 | 1.269x |
1.040x |
| 8 | 8192 | 7168 | 251.345 | 206.561 | 198.465 | 198.577 | 1.266x |
1.040x |
| 64 | 8192 | 7168 | 238.353 | 204.257 | 202.401 | 202.368 | 1.178x |
1.009x |
| 512 | 8192 | 7168 | 334.723 | 311.650 | 337.858 | 338.019 | 0.991x |
0.922x |
| 1 | 1792 | 5120 | 50.064 | 47.072 | 47.936 | 47.904 | 1.044x | 0.983x
|
| 8 | 1792 | 5120 | 49.904 | 46.400 | 47.136 | 46.865 | 1.059x | 0.990x
|
| 64 | 1792 | 5120 | 51.696 | 63.392 | 50.944 | 48.960 | 1.015x | 1.295x
|
| 512 | 1792 | 5120 | 103.600 | 100.001 | 110.289 | 110.113 | 0.939x |
0.908x |
| 1 | 5120 | 1280 | 38.528 | 37.808 | 37.344 | 37.392 | 1.032x | 1.011x
|
| 8 | 5120 | 1280 | 38.817 | 37.456 | 37.344 | 37.344 | 1.039x | 1.003x
|
| 64 | 5120 | 1280 | 41.536 | 39.552 | 42.624 | 38.720 | 0.974x | 1.021x
|
| 512 | 5120 | 1280 | 77.776 | 71.936 | 78.960 | 74.321 | 0.985x |
0.968x |
| 1 | 5120 | 2048 | 60.496 | 59.713 | 55.520 | 55.520 | 1.090x | 1.076x
|
| 8 | 5120 | 2048 | 54.992 | 56.577 | 55.888 | 55.904 | 0.984x | 1.012x
|
| 64 | 5120 | 2048 | 59.600 | 58.577 | 60.049 | 57.425 | 0.993x | 1.020x
|
| 512 | 5120 | 2048 | 100.929 | 94.049 | 107.969 | 99.552 | 0.935x |
0.945x |
| 1 | 1280 | 8192 | 61.088 | 66.224 | 52.736 | 52.832 | 1.158x | 1.253x
|
| 8 | 1280 | 8192 | 60.832 | 72.928 | 53.120 | 53.120 | 1.145x | 1.373x
|
| 64 | 1280 | 8192 | 63.697 | 65.377 | 58.048 | 58.448 | 1.097x | 1.119x
|
| 512 | 1280 | 8192 | 88.624 | 94.977 | 148.081 | 113.472 | 0.598x |
0.837x |
| 1 | 8192 | 1024 | 48.288 | 45.601 | 44.928 | 44.897 | 1.075x | 1.016x
|
| 8 | 8192 | 1024 | 49.264 | 47.152 | 46.160 | 46.080 | 1.067x | 1.023x
|
| 64 | 8192 | 1024 | 53.617 | 49.201 | 52.096 | 47.808 | 1.029x | 1.029x
|
| 512 | 8192 | 1024 | 90.864 | 84.129 | 83.265 | 83.376 | 1.091x |
1.009x |
| 1 | 8192 | 3584 | 141.633 | 134.241 | 129.489 | 129.505 | 1.094x |
1.037x |
| 8 | 8192 | 3584 | 144.032 | 131.505 | 126.273 | 126.145 | 1.141x |
1.042x |
| 64 | 8192 | 3584 | 143.792 | 136.417 | 133.377 | 136.705 | 1.078x |
0.998x |
| 512 | 8192 | 3584 | 189.217 | 184.113 | 185.281 | 185.010 | 1.021x |
0.995x |
| 1 | 896 | 5120 | 37.345 | 26.593 | 24.640 | 24.704 | 1.516x | 1.076x |
| 8 | 896 | 5120 | 37.520 | 27.200 | 26.176 | 26.208 | 1.433x | 1.038x |
| 64 | 896 | 5120 | 37.904 | 34.112 | 30.304 | 30.176 | 1.251x | 1.130x
|
| 512 | 896 | 5120 | 54.528 | 56.672 | 56.097 | 55.968 | 0.972x | 1.013x
|
| 1 | 5120 | 640 | 27.072 | 25.137 | 22.272 | 22.208 | 1.216x | 1.132x |
| 8 | 5120 | 640 | 26.529 | 25.296 | 21.889 | 21.824 | 1.212x | 1.159x |
| 64 | 5120 | 640 | 30.032 | 26.928 | 30.112 | 25.696 | 0.997x | 1.048x
|
| 512 | 5120 | 640 | 64.688 | 50.609 | 59.264 | 59.153 | 1.092x | 0.856x
|
| 1 | 5120 | 1024 | 31.840 | 30.576 | 30.016 | 30.048 | 1.061x | 1.018x
|
| 8 | 5120 | 1024 | 34.368 | 33.104 | 31.745 | 31.664 | 1.083x | 1.045x
|
| 64 | 5120 | 1024 | 37.568 | 39.008 | 39.072 | 33.760 | 0.962x | 1.155x
|
| 512 | 5120 | 1024 | 73.120 | 66.561 | 70.912 | 69.008 | 1.031x |
0.965x |
| 4096 | 34816 | 5120 | 5953.060 | 5705.375 | 6055.075 | 5944.979 |
0.983x | 0.960x |
| 8192 | 34816 | 5120 | 12809.576 | 11732.035 | 11592.434 | 11586.514 |
1.105x | 1.013x |
| 4096 | 5120 | 17408 | 5116.573 | 3538.180 | 3020.001 | 3020.736 |
1.694x | 1.171x |
| 8192 | 5120 | 17408 | 12435.254 | 8242.750 | 5830.257 | 5829.616 |
2.133x | 1.414x |

</details>

## 🔍 Related Issues

Related: #3170, #4223, #4071. This PR integrates dense NVFP4 into the
existing public backend and autotuner. #5093 separately expands CUTLASS
tactics; #5242 adds canonical-layout W4A16.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Pre-commit is installed.
- [x] Hooks pass on changed files.

## 🧪 Tests

- [x] Tests have been added or updated.

SM121: **210 numerical/API tests and 45 JIT-cache tests passed**. All
**163 measured shapes** passed full-output bitwise checks across every
admitted tactic and the public default, including graph replay after
changing inputs and GPU alpha. Coverage also includes zero/sparse
inputs, padded scale tails and actual-shape cache validation. SM120
validation is queued on RTX 5090.

```bash
.venv/bin/python -m pytest tests/gemm/test_mm_fp4_sm12x_cute.py -v
.venv/bin/python -m pytest tests/jit/test_cute_dsl_cache.py -v
```

AI assistance was used for implementation, tests and analysis.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added NVFP4 GEMM support using the CuTe DSL backend on SM120 and SM121
GPUs.
* Support includes ragged logical M dimensions and stream-ordered
launches; output is limited to bfloat16, with NVFP4 inputs and specific
scale-layout requirements.
* Backend selection recognizes the supported architectures and selects
compatible execution tactics.
* Added tactic preparation for supported shapes, including reuse of
compiled kernels during CUDA graph capture.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [112b9cb](https://github.com/flashinfer-ai/flashinfer/commit/112b9cb016a6352a653a73078a010da1dd98954c)

- **作者**: Stefano Castagnetta
- **时间**: 2026-10-01T18:42:27Z
- **提交信息**: Add native W4A16 prefetch and grouped-tile tactics on SM121 (#5648)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add register-prefetch and grouped-tile tactics to `cute-dsl-native` on
SM121. They read the canonical NVFP4 weights and scales directly,
preserving weight sharing for dynamic W4A4/W4A16 serving. The autotuner
can select register prefetch at M=1..64 and grouped M tiles with packed
scale loads above that range for the 27B gate/up and down projections.
Existing defaults and fallbacks remain available.

On DGX Spark (SM121), this PR achieves **1.18x geomean speedup versus
the autotuned merged W4A16 backend** across 46 cases (M=1..8192),
including **1.31x at M<=16**. At M=4096/8192, gate/up improves
**1.31x/1.29x** and down improves **1.16x/1.18x**. Stage-local FP32
partial sums keep the long-K grouped kernel within the existing
correctness tolerance.

Both versions were autotuned per shape and measured on the same GPU with
CUDA graphs, cold-L2 CUPTI timing and three alternating passes of 100
samples. Times are medians of the three run medians, excluding
compilation and tuning. Speedup is merged time divided by this PR's
time.

<details>
<summary>Full performance table (46 cases)</summary>

| M | N | K | Merged W4A16 (us) | This PR (us) | Speedup |
|---:|---:|---:|---:|---:|---:|
| 1 | 5120 | 17408 | 305.137 | 252.913 | 1.206x |
| 2 | 5120 | 17408 | 346.112 | 251.185 | 1.378x |
| 4 | 5120 | 17408 | 345.216 | 251.761 | 1.371x |
| 8 | 5120 | 17408 | 350.305 | 252.753 | 1.386x |
| 12 | 5120 | 17408 | 351.505 | 253.744 | 1.385x |
| 16 | 5120 | 17408 | 352.753 | 256.368 | 1.376x |
| 17 | 5120 | 17408 | 354.737 | 257.249 | 1.379x |
| 32 | 5120 | 17408 | 356.465 | 261.953 | 1.361x |
| 64 | 5120 | 17408 | 366.880 | 306.080 | 1.199x |
| 65 | 5120 | 17408 | 371.249 | 370.961 | 1.001x |
| 127 | 5120 | 17408 | 393.857 | 393.649 | 1.001x |
| 128 | 5120 | 17408 | 397.393 | 396.993 | 1.001x |
| 129 | 5120 | 17408 | 653.282 | 711.378 | 0.918x |
| 256 | 5120 | 17408 | 685.377 | 685.330 | 1.000x |
| 352 | 5120 | 17408 | 905.506 | 811.601 | 1.116x |
| 512 | 5120 | 17408 | 1234.275 | 1179.523 | 1.046x |
| 1024 | 5120 | 17408 | 2487.797 | 2406.742 | 1.034x |
| 1568 | 5120 | 17408 | 4188.506 | 3540.728 | 1.183x |
| 2000 | 5120 | 17408 | 5455.996 | 4323.930 | 1.262x |
| 2048 | 5120 | 17408 | 5536.157 | 4606.506 | 1.202x |
| 3072 | 5120 | 17408 | 8207.395 | 7468.610 | 1.099x |
| 4096 | 5120 | 17408 | 11377.530 | 9779.702 | 1.163x |
| 8192 | 5120 | 17408 | 23684.855 | 20037.630 | 1.182x |
| 1 | 34816 | 5120 | 525.777 | 467.393 | 1.125x |
| 2 | 34816 | 5120 | 611.090 | 466.849 | 1.309x |
| 4 | 34816 | 5120 | 606.881 | 466.801 | 1.300x |
| 8 | 34816 | 5120 | 614.369 | 469.697 | 1.308x |
| 12 | 34816 | 5120 | 616.816 | 473.184 | 1.304x |
| 16 | 34816 | 5120 | 617.633 | 474.352 | 1.302x |
| 17 | 34816 | 5120 | 606.113 | 475.201 | 1.275x |
| 32 | 34816 | 5120 | 614.594 | 484.433 | 1.269x |
| 64 | 34816 | 5120 | 636.178 | 537.186 | 1.184x |
| 65 | 34816 | 5120 | 645.489 | 645.344 | 1.000x |
| 127 | 34816 | 5120 | 747.554 | 680.689 | 1.098x |
| 128 | 34816 | 5120 | 747.089 | 664.706 | 1.124x |
| 129 | 34816 | 5120 | 977.986 | 974.067 | 1.004x |
| 256 | 34816 | 5120 | 1281.379 | 1180.131 | 1.086x |
| 352 | 34816 | 5120 | 1813.955 | 1519.636 | 1.194x |
| 512 | 34816 | 5120 | 2570.709 | 2347.093 | 1.095x |
| 1024 | 34816 | 5120 | 5225.820 | 4483.257 | 1.166x |
| 1568 | 34816 | 5120 | 8230.067 | 7121.889 | 1.156x |
| 2000 | 34816 | 5120 | 11216.985 | 8949.077 | 1.253x |
| 2048 | 34816 | 5120 | 11288.827 | 9863.894 | 1.144x |
| 3072 | 34816 | 5120 | 18731.274 | 15042.354 | 1.245x |
| 4096 | 34816 | 5120 | 25482.282 | 19495.916 | 1.307x |
| 8192 | 34816 | 5120 | 51730.565 | 40155.916 | 1.288x |

</details>

## 🔍 Related Issues

Follow-up to #5242; used by vllm-project/vllm#54614. #5100 implements
W4A4 separately. Existing W4A16 MoE optimizations do not add this dense
GEMM tactic.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] Installed pre-commit in a uv environment.
- [x] Installed hooks with `pre-commit install`.
- [x] All applicable hooks passed on the changed files, including mypy
and Ruff.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Added reference, graph replay, live-alpha, stream and eligibility
tests across small, medium and large M, plus runtime-M compilation
reuse.
- [x] DGX Spark: all 112 tests passed at the original tolerances,
including forced optimized tactics, live-input CUDA graph replay,
non-default streams and runtime-M compilation reuse.

```bash
.venv/bin/python -m pytest tests/gemm/test_native_bf16_fp4.py -v
.venv/bin/python benchmarks/flashinfer_benchmark.py --routine mm_bf16_fp4 \
  --backends cute-dsl-native --m 16 --n 5120 --k 17408 \
  --input_dtype bfloat16 --out_dtype bfloat16 --autotune --refcheck
```

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
Do not delete the fence or change its `experimental-tests` tag , the
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

Kernel validation covers both projection families through M=8192,
including partial M tiles. AI assistance was used for implementation and
validation.

---------

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [f50badc](https://github.com/flashinfer-ai/flashinfer/commit/f50badcbc9a58287158f7a11341d0ac57b5871b6)

- **作者**: Jan Bernlöhr
- **时间**: 2026-10-01T18:29:13Z
- **提交信息**: fix(aot): include CUTLASS fused MoE in SM110 providers (#5695)

## 📌 Description

SM110-only JIT-cache provider builds omit `fused_moe_100` because AOT
registration is gated on SM100, although the generator supports both
SM10x and SM11x. On Thor, this forces a cold runtime compilation during
SGLang's FlashInfer autotune.

Register the module in the SM110 path when SM100 is absent. Builds
targeting both architectures still call the generator once. Add eight
regression cases covering SM110-only, SM100-only, combined targets, and
an unsupported target, with MoE registration enabled and disabled.

## 🔍 Related Issues

Fixes https://github.com/flashinfer-ai/flashinfer/issues/5649

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
- [ ] All tests are passing (`unittest`, etc.).

- All applicable pre-commit hooks passed on the changed files, including
mypy, Ruff lint, and Ruff formatting:
  ```bash
pre-commit run --files flashinfer/aot.py
tests/jit/test_cutlass_fused_moe_aot.py
  ```
Hooks were run manually; `pre-commit install` and a repository-wide
`--all-files` run were not performed.
- Registration regression check on macOS: **1 failed / 7 passed before
the fix; 8 passed after it**. The failing baseline case was SM110-only
with MoE enabled. A local harness executed the unchanged
`gen_all_modules` and helper function bodies with external imports
isolated; the test mocks kernel generators. This is not a full
FlashInfer import or CUDA test.
- `git diff --check` passed.
- Pending in a supported FlashInfer environment:
  ```bash
  pytest tests/jit/test_cutlass_fused_moe_aot.py
  ```
- Pending before marking ready: build the patched
`flashinfer-jit-cache-sm110a` provider wheel and verify it loads
`fused_moe_100` on Thor without runtime JIT.

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

The earlier experiment in #5649 used FlashInfer `0.7.0.dev20260922`,
NVIDIA Thor, and SGLang serving Nemotron-3-Nano FP8. The unmodified
control exceeded the 900-second readiness limit while compiling
`fused_moe_100`; providing a prebuilt SM110 module reduced autotune to
28 seconds and the benchmark completed. That treatment used FlashInfer's
in-package AOT path, not a rebuilt provider wheel, and was not run
against this latest-main commit.

The module increases the SM110 provider's build workload. The earlier
standalone SM110 compilation took approximately 98 minutes on a 16-CPU
aarch64 builder with three parallel compiler jobs. Keep the PR in draft
until provider-wheel validation is complete.

Prepared with assistance from Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected ahead-of-time registration of fused MoE modules when both
SM100 and SM110 are enabled, avoiding duplicate registration.
* **Tests**
* Added coverage for fused MoE registration across supported and
unsupported GPU capabilities, including configurations with and without
`add_moe`.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9deb117](https://github.com/flashinfer-ai/flashinfer/commit/9deb117bfb8aad2bd08ed781238483be3dec9810)

- **作者**: Mingyang Wang
- **时间**: 2026-10-01T18:13:29Z
- **提交信息**: fix(tests): skip unsupported groupwise GEMM architectures (#5759)

<!-- .github/pull_request_template.md -->

## 📌 Description

Skip unsupported FP8 groupwise GEMM test cases using the production
API's backend-specific compute-capability metadata. The existing
major-version checks could admit unsupported combinations, such as SM107
for the TRTLLM and cuTile backends, and fail instead of skipping.

Check backend support before allocating tensors, preserving the original
parametrization and existing shape/dependency guards. The final diff
changes only `tests/gemm/test_groupwise_scaled_gemm_fp8.py`.

## 🔍 Related Issues

Related Jira: [IKL-432](https://jirasw.nvidia.com/browse/IKL-432).

The related AlphaMoE SM100/SM103 gate is already fixed on main by #5444.
This PR covers the remaining groupwise GEMM test gate.

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

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Targeted validation on the pre-rebase source passed:

- B100: CUTLASS groupwise `cutlass-MN-256-128-128`.
- 38 temporary guard regression checks, including
unsupported-architecture skip behavior, plus the B100 CUTLASS case. The
temporary regression module is not included in this PR.
- Pre-commit hooks on the changed files.

The GEMM test file is byte-identical to the tested version. The
groupwise API, backend capability predicates, and support-query
decorators are unchanged across the rebase; upstream changes include
unrelated imports and packaging. GPU tests were not rerun after
rebasing. The full suite and actual SM107 execution were not run; this
does not establish that the nightly is fully passing.

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

Please review the capability checks against each API/backend support
contract. Production kernels and support metadata are unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* FP8 groupwise GEMM tests now skip when CUDA is unavailable and run
only when the selected backend supports the combined compute capability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [240de7a](https://github.com/flashinfer-ai/flashinfer/commit/240de7a90bd43d663e3eb93429bf47559b50fd5b)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-01T17:44:26Z
- **提交信息**: fix(tests): scale cake/cute SSDCombined parity atol by the output scale (#5756)

## 📌 Description


`tests/mamba/test_cake_ssd_combined.py::test_cake_ssd_combined_route_matrix`
fails every night on `unit_test_gb200` (both `cu129` and `cu130`) on the
two Nemotron-H rows, `nheads=128, ngroups=8` batched and varlen. Each
failure is **one element out of 2,097,152**, overshooting the tolerance
by 0.0009:

```
AssertionError: Tensor-likes are not close!
Mismatched elements: 1 / 2097152 (0.0%)
Greatest absolute difference: 0.013671875 at index (1, 122, 61, 20) (up to 0.01 allowed)
Greatest relative difference: 0.049560546875 at index (1, 122, 61, 20) (up to 0.01 allowed)
```

This is a tolerance bug in the test, not a `cake` kernel defect.
`_assert_cute_parity` compares the two GPU backends at a flat
`atol=1e-2`, but the route-matrix outputs reach `max|out|` of
46.25–97.50. Entries near the failing element's magnitude (`|expected| ≈
0.276`) are the residue of cancellation among summands of a much larger
scale, so their absolute error tracks that scale rather than their own
value. `rtol` only protects large entries, leaving `atol` as the binding
constraint exactly where cancellation is worst. The observed 0.0137 is
~7 bf16 ULPs at that magnitude (bf16 ULP in [0.25, 0.5) is 0.001953),
consistent with two fp32 reduction orders rounded to bf16 rather than a
wrong result.

Measured on a B200 (CC 10.0, same compute capability as GB200, different
board), all 12 route-matrix rows — the quiet ones included, since they
bound the blast radius:

| row | nheads | ngroups | varlen | max\|out\| | max abs diff | diff /
scale |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | 8 | 8 | False | 56.00 | 0.015625 | 2.8e-4 |
| 1 | 8 | 8 | False | 55.75 | 0.003906 | 7.0e-5 |
| 2 | 8 | 8 | True | 46.75 | 0.015625 | 3.3e-4 |
| 3 | 8 | 8 | True | 46.25 | 0.015625 | 3.4e-4 |
| 4 | 8 | 8 | False | 55.75 | 0.001953 | 3.5e-5 |
| 5 | 1 | 1 | False | 61.25 | 0.000002 | 3.1e-8 |
| 6 | 12 | 3 | False | 97.50 | 0.015625 | 1.6e-4 |
| 7 | 16 | 4 | False | 97.50 | 0.003906 | 4.0e-5 |
| 8 | 128 | 1 | False | 93.50 | 0.062500 | 6.7e-4 |
| 9 | 128 | 128 | False | 94.00 | 0.031250 | 3.3e-4 |
| 10 | 128 | 8 | False | 70.00 | 0.015625 | 2.2e-4 |
| 11 | 128 | 8 | True | 70.50 | 0.015625 | 2.2e-4 |

The ratio is **not** a fixed fraction of scale — it spans 3.1e-8 (row 5,
where the backends agree to 2e-6) to 6.7e-4 (row 8) — but where the
backends diverge, the divergence is bounded by a small fraction of the
tensor scale rather than of the entry.

So this PR replaces the flat floor with `atol = max(1e-2, 5e-4 *
max|reference|)`, per compared tensor. Small tensors keep the original
`1e-2`; `rtol=1e-2` is unchanged, and the `max(1e-2, ...)` floor means
no existing comparison is ever tightened. At `rtol=1e-2` the GB200 log
requires `atol ≥ 0.013671875 − 0.01 × 0.275862 = 0.010913`, a 1.09x
increase over today's `1e-2`; `5e-4 × 70.0 = 0.035` holds **3.21x** over
that.

I left that margin rather than fitting the coefficient to the single
GB200 number because the `cute` reference is not bit-stable across
processes. On identical inputs (verified by digest) routes 1 and 9 each
produce two distinct outputs over ~20 fresh processes, swinging route
9's required `atol` between ~0 and 5.3e-3 — over half the whole `1e-2`
budget — while `cake` is bit-identical in every run and route 10 is
stable. Within one process `cute` repeats exactly, so this looks like a
one-time kernel-selection decision. A nondeterministic reference is also
a latent flake source for every comparison in this file; that is out of
scope here and I will file it separately.

The unused `nheads`/`ngroups` parameters are dropped. They have been
accepted and never read since the helper was introduced in 624fce19
(#4576); the driver of the error floor is the tensor scale, which the
helper reads directly, so wiring the head counts in would have been
misleading.

## 🔍 Related Issues

Internal: IKL-447.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> `pre-commit`, `black` and `ruff` are not available in the environment
I worked in, so I could not run them. The change is 8 lines in one test
file and follows the surrounding formatting (88-column, black style);
please let the hooks confirm.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On a B200 (CC 10.0, torch 2.14.0+cu130): `pytest
tests/mamba/test_cake_ssd_combined.py -q` → `141 passed, 2 skipped`,
identical before and after. Two further failures in that run are
environmental in my worktree (`flashinfer/data/csrc/seq_chunk_cumsum.cu`
is absent, so ninja cannot build `mamba_seq_chunk_cumsum`); they
reproduce on the unmodified file and neither test goes through
`_assert_cute_parity`.

### Limits of what I verified

- **I could not reproduce the failure itself.** It passes on B200, where
the tolerance is merely near the edge (worst element needs 0.00375, i.e.
0.006 under the limit) rather than over it as on GB200 (needs 0.010913,
0.0009 over). The fix is derived from the numbers in the GB200 CI log,
not from a local red-to-green transition. A GB200 run is the real check.
- **There is exactly one GB200 data point**, and it is the maximum over
2,097,152 samples of a quantity whose tail I have not characterised. I
have no GB200 access, so I did not measure a B200↔GB200 spread.
- Why B200 and GB200 diverge numerically at all, both being CC 10.0, is
unproven. Plausible causes are SM-count dependent tiling changing fp32
reduction order, or cu129 vs cu130 codegen. I did not isolate it and
this PR does not address it.
- The scale used is the whole-tensor max, which is looser than the scale
that actually bounds the error: each head is an independent SSM, and for
the failing entry the head-local max is 44.75 and the max along its
reduction axis is 6.97, against a global max of 70. A per-head scale
would be the principled version and clears every local route; the tensor
max is one line and cannot tighten anything, but it is a bound, not a
mechanism.
- **The coefficient alone does not cover the final states.** Their
diff/scale ratio reaches 2.09e-3, *above* `5e-4`; they pass because the
`1e-2` floor dominates at their scale (6.94). If a future route pushed
final-state magnitudes past ~10, the coefficient would be undersized for
them.
- Widening the tolerance is not hiding a `cake` defect: against an fp64
reference the two backends are indistinguishable in aggregate (mean
error 1.79e-3, rms 4.13e-3 each), and among the elements where they
disagree `cake` is the closer one more often than `cute` (2639 of 4967).
- No perf implications; this is test-only.

### [1cad381](https://github.com/flashinfer-ai/flashinfer/commit/1cad38165e5fe9d3007a07f79b3d5a2d73d6fce4)

- **作者**: eigen
- **时间**: 2026-10-01T11:34:16Z
- **提交信息**: perf(cake_sampling): round 7 -- speculative-sample stage-1 twin, whole-CTA tail for cluster-8 streams, capability-keyed host policy (#5847)

## cake_sampling round 7: speculative-sample stage-1 twin, whole-CTA
tail for cluster-8 streams, capability-keyed host policy

Follow-up to #5439, #5482, #5585, #5607, #5636, #5684 and #5731 (round
6, bundle `b9772a65`). Exact top-k / top-p radix
sampling route
(`flashinfer.cake_sampling.top_k_top_p_sampling_from_probs`); every
kernel output stays bit-identical to
round 6 (the correctness contract is unchanged: exact top-k set with the
documented tie rule, exact top-p cut within
eps = 1e-6 of p, sample inside the exact support, deterministic replay).

### What changed

- **Bundle** (`csrc/cake_sampling/generated`, manifest source
`e68d4b4757ada128`, 73 kernels: 20 default stage-1 builds,
8 coarse-sample `_cs`, 8 speculative-sample `_sp`, 19 whole-CTA-tail
`_bt`, 18 stage-2/3; six source parts under 5 MiB).
Against round 6: 30 kernels identical, 16 stream kernels differ by one
redundant block barrier (FX2), 27 new.
- **`_sp` (launch_flags bit 6)**: the first register chunk doubles as
the sample (no separate sampled read); the host
takes it for every ept-16 stream and the 1 / 2-on-cluster-8 / >=
16-chunk ept-32 streams on B200 / GB300 (on B200 a
two-chunk row whose second chunk is at least half full keeps the coarse
build: the cluster-8 V = 262144 stream measured
the twin 2.1 % slower in two interleaved profiler passes,
`_SPEC_SAMPLE_WIDE_TWO_CHUNK_MAX_FILL_BY_CAPABILITY`), and on
Hopper / Rubin only for clusters <= 4 with >= 64 CTAs (k <= 64: rows of
>= 5 chunks; chain: >= 128 CTAs for rows of
>= 16 chunks), where the matrices measured it. Never on a cluster-8
stream that takes the two-kernel chain (k above
the fused-tail cap): that chain lost 3-17 % with it on H100, R200 and
GB300 V = 262144.
- **`_bt` (launch_flags bit 3)**: single-launch whole-CTA tail for
cluster-8 streams above k = 768 on a one-wave grid
(B200 any vocabulary, GB300 up to V = 196608); every other k > 64 cell
keeps the PDL-chained two-launch form.
- **Dispatcher**: `choose_stage1` resolves the device defaults and
memoises the ranking (`_choose_stage1_resolved`,
`lru_cache`): the served route asks twice per call and the round-7
per-candidate tail test had doubled the host cost
(B200 102 -> 162 us per call), which a two-launch chain pays inside its
launch gap. 148-SM cost row re-fitted on the
round-7 graph-replay sweeps (three terms: the `_sp` saving of the ept-32
stream, the ragged last-chunk penalty of the
ept-32 stream at k > 64, the stage-2/3 launch behind a resident grid);
worst regret 21.4 -> 4.1 %; the picks match the
  cake tree dispatcher on 1944 / 1944 cells.
- Binding: `spec_sample` manifest column / variant table entry, bit-6
validation (streams only, exclusive with bits 3 / 4);
JIT validator reads the new column. Tests cover the twins' bit-identity,
the policy tables and the route.

### Measured (CUPTI medians, same node / run, round-6 bundle vs this PR;
`benchmarks/bench_cake_sampling.py --cupti`)

| GPU | cells | vs round 6: faster by > 2 % / within 2 % / slower by > 2
% | worst | vs `top_k_first` min / median / max | k = 50 eager, B <= 16
(us, round 6 -> this PR) | k = 1000 graph, B = 64 (us) |
|---|---|---|---|---|---|---|
| H100 SXM | 192 | 59 / 122 / 11 | +8.2 % (k = 1000, eager, V = 262144,
B = 1) | 1.81x / 3.52x / 8.89x | 14.2 -> 14.2 | 34.1 -> 30.9 / 50.0 ->
47.9 / 56.7 -> 48.9 / 68.0 -> 65.5 |
| B200 | 192 | 68 / 118 / 6 | +6.3 % (k = 10, eager, V = 151936, B = 1)
| 1.81x / 4.07x / 8.71x | 12.9 -> 13.2 | 29.9 -> 28.7 / 41.7 -> 41.5 /
46.5 -> 41.1 / 48.0 -> 46.8 |
| GB300 | 192 | 62 / 125 / 5 | +4.7 % (k = 1000, graph, V = 262144, B =
1) | 1.53x / 4.22x / 15.93x | 13.2 -> 12.6 | 31.4 -> 30.8 / 44.3 -> 43.5
/ 41.4 -> 40.9 / 47.2 -> 48.1 |
| R200 | 192 | 23 / 167 / 2 | +4.6 % (k = 10, graph, V = 151936, B = 16)
| 1.59x / 3.56x / 7.79x | 12.1 -> 12.1 | 26.1 -> 26.1 / 35.8 -> 35.6 /
39.4 -> 32.8 / 38.9 -> 38.8 |

Per-cell tables (all 192 cells per GPU, eager + CUDA graph, k = 50 /
1000) are in `docs/api/cake_sampling.rst`. Rows slower than round 6 by
more than 2 %: B200 6 (k <= 64 eager column on small-batch single-kernel
cells, V151K B1/B2 and V256K B1; the reversed-order run reproduces the
medians, the interleaved per-cell harness on the same node measures
those cells equal or faster for this PR (V256K B1 12.73 vs 12.74 us on
identical kernels, V151K B1 k = 10 12.59 vs 12.77), and a same-process
experiment shows the eager span of these 12-13 us cells is bimodal (two
modes 0.6-0.8 us apart) within one tree -- the eager metric's floor,
classified in the design doc), GB300 5 (the V = 262144 B <= 8 k = 1000
chain in graph mode, +2..+4.7 %: identical kernels / flags / launch
path, difference vanishes with PDL disabled in both trees -- open PDL
scheduling residual), H100 11 (k = 1000 chains, eager only, graph clean:
interleaved per-cell A/B of both trees measures equal spans with
identical kernel durations), R200 2 (graph-noise rows not reproduced in
the reversed run).

Every one of the 192 cells per GPU stays faster than `top_k_first`
(joint is slower still). The eager metric is the CUPTI span from the
first kernel start to the last kernel end and contains the PDL-chained
launch gap; on the Grace-hosted GB300 node that gap is 6-9 us in both
trees and jitters by several us run to run, so eager deltas on
two-launch cells are judged under graph replay. Host cost per call
dropped from 103 / 114 / 141-166 us (B200 / H100 / GB300, round 6) to 43
/ 47 / 78-109 us with the memoised dispatcher.

### Validation

- `tests/utils/test_cake_sampling.py` +
`test_cake_sampling_upstream.py`: 253 passed / 18 skipped on B200 at
this host
(9d762aa6) and on H100, GB300 and R200 (sm_107a) at 1e0a3fa3 (the later
host commit only changes (10,0) dispatch); RTX PRO 6000 (sm_120a): 250
passed / 21 skipped (the route keeps `top_k_first` fallback semantics
  there).
- Cake tree gates (export digest pin, pipeline e2e with the adversarial
/ graph-replay / concurrent-stream / deterministic-replay
cases, weave kernel slice): pass on B200, GB300, H100, R200 at the
exporting head and again on B200 at the final cake head.
- compute-sanitizer synccheck + memcheck: 0 errors on the registered
cells and the per-variant repro (every frozen stage-1 variant
x default / `_cs` / `_sp` build x fused / two-launch, every `_bt` twin,
every stage-2/3 form; 448 launches) on B200 and R200.
- sglang GSM8K (Qwen3.5-35B-A3B, n = 1319): cake k50/p0.9 0.7074 /
0.6967 vs top_k_first 0.6702 / 0.6755 vs joint
0.6884 / 0.7051; k1000 0.6975 / 0.6937 / 0.6846; multi-seed histograms:
outside_support 0 on every arm.
- Dispatcher: picks identical to the cake tree dispatcher on 1944 / 1944
cells; the k <= 64 constants of the 148-SM row were
re-fitted on the served route (every candidate forced through the
dispatcher, eager + graph, B200 + GB300).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added automatic selection of speculative-sampling variants for
eligible launches, alongside existing sampling options.
* Enabled fused tail processing for eligible one-wave, cluster-8
workloads on B200 and GB300; other workloads retain the two-launch path.
* **Bug Fixes**
* Prevented speculative-sampling variants from being selected with
incompatible launch options.
* **Documentation**
* Updated sampling selection rules, correctness expectations, and
benchmark results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9af4a13](https://github.com/flashinfer-ai/flashinfer/commit/9af4a130b7524d4e930dc0269b6940e2f9fdaa03)

- **作者**: eigen
- **时间**: 2026-10-01T11:33:04Z
- **提交信息**: feat(cake_moe_grouped_gemm): ragged BF16 grouped GEMM for MoE experts (forward, dX, dW) on SM100/SM103/SM107 (#5678)

Adds the experimental `cake_moe_grouped_gemm` backend: ragged BF16 grouped GEMM
for MoE experts (forward, input gradient, weight gradient) generated from Weave
IR programs for SM100 / SM103 / SM107, with `grouped_mm_bf16(backend="cake")`,
an autograd wrapper, JIT module tables, docs and tests.

Measured under the paired, interleaved, cold-L2 export protocol on R200, GB300
and B200 against torch._grouped_mm, a per-expert cuBLAS loop and cuDNN grouped
GEMM; every row is validated against an fp64 reference. Remaining rows at or
below 1.00 are ties within measurement noise at the tensor-pipe ceiling and are
documented in the PR description.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

### [883825a](https://github.com/flashinfer-ai/flashinfer/commit/883825a20f9b9ff92f64101168ed4c324642121c)

- **作者**: eigen
- **时间**: 2026-10-01T09:38:47Z
- **提交信息**: perf(cake_fmha): round-4 balanced DCP E4M3 bodies and deterministic packed-MTP fold on SM100/SM103 (#5855)

## Summary

Round 4 of the on-device load-balanced varlen scheduler for the Cake DCP
speculative-decode and packed-MTP decode families on SM100 / SM103
(sibling rounds: #5634 round 1, #5688 round 2, #5750 round 3). The host
route, bands, JIT adapters and tests are unchanged; this PR ships the
round-4 **kernel bodies** of six families from the Cake export and
re-pins the manifest:

- `cake_fmha_dcp_spec_bf16_fp8_balanced` (E4M3 cache, page 64, head_dim
128): the first K/V page group is published before the Q split, the next
item is claimed 8 blocks ahead, one-body wide reduce fold, deterministic
two-chunk fold.
- `cake_fmha_dcp_spec_bf16_fp8_d256_balanced` (E4M3 cache, page 64,
head_dim 256): one-body wide reduce fold, deterministic two-chunk fold.
- `cake_fmha_dcp_spec_bf16_balanced` (BF16 cache, page 16, head_dim
128): **unchanged** -- the round-3 body is kept; the same levers
measured neutral or negative on its short rows (10-round paired A/B on
both GPUs).
- `cake_fmha_decode_balanced_{bf16,fp16}_mtp_n{32,64}` (packed MTP
decode): deterministic two-chunk fold (the round-3 bodies were 1-11 ulp
run-to-run on the `mtp7_uniform_b64_hkv1_s32768` row because the
in-place fold's rounding depended on which CTA arrived last).

Shipped static programs other than these are untouched (byte-identical
to `main`); the add-on manifest keeps its entries and only the six
families' records, `source_package_sha256` and the pinned manifest
digest change.

## Speedup summary

Ratios are time of the round-3 bodies (`main`) / time of this PR's
bodies, cold-L2 CUPTI medians of the eager launch, same node and same
run (paired, rotated arms, 5 rounds); > 1 = this PR faster.

| engine | rows | GB300 min / geomean / max | B200 min / geomean / max |
|---|---|---|---|
| `cake_fmha_dcp_spec_bf16_fp8_balanced` | 10 | 1.025 / 1.075 / 1.161 |
1.028 / 1.068 / 1.123 |
| `cake_fmha_dcp_spec_bf16_fp8_d256_balanced` | 5 | 0.995 / 1.066 /
1.181 | 0.999 / 1.062 / 1.161 |
| `cake_fmha_decode_balanced_*_mtp_n*` (Cake rows) | 5 | 0.999 / 1.000 /
1.001 | 0.999 / 1.001 / 1.005 |

<details><summary>per row</summary>

| engine | row | GB300 (sm_103a) | B200 (sm_100a) |
|---|---|---:|---:|
| `cake_fmha_dcp_spec_bf16_fp8_balanced` | `prod_b8_s4096_q4_cp4` |
1.040 | 1.044 |
|  | `prod_b8_s8192_q4_cp4_graph` | 1.032 | 1.044 |
|  | `prod_b8_s16384_q4_cp4` | 1.026 | 1.032 |
|  | `prod_b64_s4096_q4_cp4` | 1.161 | 1.123 |
|  | `prod_b64_s4096_q8_cp4` | 1.154 | 1.102 |
|  | `prod_b64_s16384_q8_cp4` | 1.057 | 1.045 |
|  | `prod_b1_s8192_q4_cp4_graph` | 1.104 | 1.114 |
|  | `prod_b256_s8192_q4_cp4_graph` | 1.124 | 1.120 |
|  | `dcp_fp8_agentx_b16_q4_cp4_r0` | 1.025 | 1.028 |
|  | `dcp_fp8_random_128_65k_b64_q4_cp4_r0` | 1.036 | 1.035 |
| `cake_fmha_dcp_spec_bf16_fp8_d256_balanced` |
`prod_d256_b1_ctx32768_q4_cp4_graph` | 1.181 | 1.161 |
|  | `prod_d256_b8_ctx32768_q4_cp4_graph` | 1.173 | 1.161 |
|  | `prod_d256_b64_ctx32768_q4_cp4_graph` | 0.998 | 1.004 |
|  | `prod_d256_b128_ctx32768_q4_cp4_graph` | 1.001 | 0.999 |
|  | `prod_d256_b128_ctx32768_q8_cp4_graph` | 0.995 | 0.999 |
| `cake_fmha_decode_balanced_*_mtp_n*` (Cake rows) |
`perf_decode_balanced_mtp7_uniform_b64_hkv1_s32768` | 0.999 | 1.000 |
| | `perf_decode_balanced_mtp4_uniform_b16_hkv8_s32768` | 0.999 | 1.000
|
|  | `perf_decode_balanced_mtp7_agentx_b128_hkv4` | 1.000 | 1.005 |
|  | `perf_decode_balanced_mtp4_agentx_b64_hkv1` | 1.000 | 1.000 |
|  | `correctness_decode_bf16_balanced_mtp` | 1.001 | 0.999 |


</details>

MTP `perf_decode_balanced_mtp7_agentx_b128_hkv4` on B200: 5-round 0.984
(pairs disagreed), 10-round recheck 1.005. Rows are the Cake benchmark
rows of each family (batch / sequence / q tokens / cp ranks);
`cake_fmha_dcp_spec_bf16_balanced` is not in the table because its body
is unchanged.

**vs the static incumbents through the same public entry point**
(`benchmarks/bench_cake_dcp_spec_decode.py --family all --graph`, cold
L2 with the incumbent's `evict_last` lines demoted):

**GB300** (NVIDIA GB300, 152 SMs, manifest 46a6d77fcc8e, 63 rows):
balanced/static (static = the shipped incumbent route through the same
public entry point; > 1 = balanced faster), balanced-routed rows only:

| family | rows (balanced-routed) | above 1.0 | min / geomean / max |
graph-replay min / geomean |
|---|---|---|---|---|
| bf16 / page 16 / D128 | 11 (10) | 10 / 10 | 1.124 / 2.682 / 6.773 |
1.121 / 2.677 |
| E4M3 / page 64 / D128 | 34 (32) | 32 / 32 | 1.064 / 2.376 / 6.973 |
1.056 / 2.372 |
| E4M3 / page 64 / D256 | 18 (13) | 13 / 13 | 1.165 / 2.179 / 3.748 |
1.162 / 2.174 |

round-3 bodies on the same GPU (unit-1 baseline run): bf16 / page 16 /
D128 min 1.116 / geomean 2.667; E4M3 / page 64 / D128 min 1.027 /
geomean 2.207; E4M3 / page 64 / D256 min 1.169 / geomean 2.155

<details><summary>GB300: all 63 rows</summary>

**GB300** — NVIDIA GB300, 152 SMs (sm_103a), manifest 46a6d77fcc8e, 63
rows; CUPTI, cold L2 (evict_last lines demoted), median (+ CUDA-graph
replay); times in ms.

| row | kind | batch | q | cp (rank) | band route (reason) | static |
balanced | balanced/static | graph ratio | max abs diff out |
|---|---|---|---|---|---|---|---|---|---|---|
| perf_b1_s4096_q4_w4_r0 | bf16_p16 | 1 | 4 | 4 (0) | static (one_wave)
| 0.0102 | 0.0123 | 0.831 | 0.841 | 0.0001 |
| perf_b1_s16384_q8_w4_r0 | bf16_p16 | 1 | 8 | 4 (0) | balanced
(long_tile) | 0.0188 | 0.0168 | 1.124 | 1.121 | 0.0001 |
| perf_b8_s4096_q4_w4_r0 | bf16_p16 | 8 | 4 | 4 (0) | balanced (waves) |
0.0199 | 0.0148 | 1.347 | 1.340 | 0.0001 |
| perf_b8_s16384_q8_w4_r0 | bf16_p16 | 8 | 8 | 4 (0) | balanced
(long_tile) | 0.0905 | 0.0375 | 2.414 | 2.398 | 0.0001 |
| perf_b64_s4096_q4_w4_r0 | bf16_p16 | 64 | 4 | 4 (0) | balanced (waves)
| 0.1061 | 0.0619 | 1.714 | 1.715 | 0.0001 |
| perf_b64_s16384_q8_w4_r0 | bf16_p16 | 64 | 8 | 4 (0) | balanced
(long_tile) | 0.5457 | 0.1797 | 3.036 | 3.032 | 0.0001 |
| perf_b8_s16383_q8_w4_r3_tail | bf16_p16 | 8 | 8 | 4 (3) | balanced
(long_tile) | 0.0908 | 0.0374 | 2.426 | 2.413 | 0.0001 |
| dcp_bf16_agentx_b16_q4_cp4_r0 | bf16_p16 | 16 | 4 | 4 (0) | balanced
(long_tile) | 1.3340 | 0.3447 | 3.870 | 3.873 | 0.0001 |
| dcp_bf16_agentx_b16_q8_cp4_r3 | bf16_p16 | 16 | 8 | 4 (3) | balanced
(long_tile) | 2.3602 | 0.3485 | 6.773 | 6.786 | 0.0001 |
| dcp_bf16_random_128_65k_b64_q4_cp4_r0 | bf16_p16 | 64 | 4 | 4 (0) |
balanced (long_tile) | 1.1820 | 0.3131 | 3.776 | 3.782 | 0.0002 |
| dcp_bf16_random_128_32k_b128_q4_cp4_r0 | bf16_p16 | 128 | 4 | 4 (0) |
balanced (long_tile) | 1.3548 | 0.3216 | 4.213 | 4.211 | 0.0002 |
| prod_b1_s8192_q4_cp4_graph | fp8_p64 | 1 | 4 | 4 (0) | static
(one_wave) | 0.0092 | 0.0154 | 0.600 | 0.608 | 0.0005 |
| prod_b8_s8192_q4_cp4_graph | fp8_p64 | 8 | 4 | 4 (0) | balanced
(two_waves) | 0.0244 | 0.0191 | 1.282 | 1.281 | 0.0007 |
| prod_b32_s8192_q4_cp4_graph | fp8_p64 | 32 | 4 | 4 (0) | balanced
(waves) | 0.0773 | 0.0405 | 1.909 | 1.905 | 0.0007 |
| prod_b64_s8192_q4_cp4_graph | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1388 | 0.0712 | 1.949 | 1.944 | 0.0008 |
| prod_b128_s8192_q4_cp4_graph | fp8_p64 | 128 | 4 | 4 (0) | balanced
(waves) | 0.2651 | 0.1180 | 2.246 | 2.241 | 0.0009 |
| prod_b192_s8192_q4_cp4_graph | fp8_p64 | 192 | 4 | 4 (0) | balanced
(waves) | 0.3908 | 0.1657 | 2.359 | 2.359 | 0.0008 |
| prod_b256_s8192_q4_cp4_graph | fp8_p64 | 256 | 4 | 4 (0) | balanced
(waves) | 0.5167 | 0.2143 | 2.412 | 2.410 | 0.0008 |
| prod_b8_s4096_q4_cp4 | fp8_p64 | 8 | 4 | 4 (0) | balanced (two_waves)
| 0.0155 | 0.0145 | 1.064 | 1.056 | 0.0010 |
| prod_b8_s4096_q8_cp4 | fp8_p64 | 8 | 8 | 4 (0) | balanced (waves) |
0.0238 | 0.0149 | 1.593 | 1.579 | 0.0010 |
| prod_b8_s16384_q4_cp4 | fp8_p64 | 8 | 4 | 4 (0) | balanced (long_tile)
| 0.0436 | 0.0295 | 1.478 | 1.481 | 0.0005 |
| prod_b8_s16384_q8_cp4 | fp8_p64 | 8 | 8 | 4 (0) | balanced (long_tile)
| 0.0678 | 0.0300 | 2.258 | 2.239 | 0.0005 |
| prod_b64_s4096_q4_cp4 | fp8_p64 | 64 | 4 | 4 (0) | balanced (waves) |
0.0847 | 0.0454 | 1.864 | 1.859 | 0.0011 |
| prod_b64_s4096_q8_cp4 | fp8_p64 | 64 | 8 | 4 (0) | balanced (waves) |
0.1387 | 0.0477 | 2.906 | 2.900 | 0.0012 |
| prod_b64_s16384_q4_cp4 | fp8_p64 | 64 | 4 | 4 (0) | balanced
(long_tile) | 0.2468 | 0.1149 | 2.148 | 2.148 | 0.0005 |
| prod_b64_s16384_q8_cp4 | fp8_p64 | 64 | 8 | 4 (0) | balanced
(long_tile) | 0.4166 | 0.1175 | 3.544 | 3.540 | 0.0006 |
| prod_b256_s4096_q4_cp4 | fp8_p64 | 256 | 4 | 4 (0) | balanced (waves)
| 0.3048 | 0.1366 | 2.231 | 2.230 | 0.0012 |
| prod_b256_s4096_q8_cp4 | fp8_p64 | 256 | 8 | 4 (0) | balanced (waves)
| 0.5249 | 0.1455 | 3.607 | 3.607 | 0.0013 |
| prod_b256_s16384_q4_cp4 | fp8_p64 | 256 | 4 | 4 (0) | balanced
(long_tile) | 0.9409 | 0.3714 | 2.533 | 2.532 | 0.0006 |
| prod_b256_s16384_q8_cp4 | fp8_p64 | 256 | 8 | 4 (0) | balanced
(long_tile) | 1.6133 | 0.3828 | 4.214 | 4.213 | 0.0006 |
| prod_b64_s8191_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1388 | 0.0709 | 1.956 | 1.952 | 0.0007 |
| prod_b64_s8192_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1388 | 0.0709 | 1.958 | 1.952 | 0.0008 |
| prod_b64_s8193_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1388 | 0.0709 | 1.958 | 1.952 | 0.0008 |
| prod_b64_s8194_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1388 | 0.0709 | 1.958 | 1.952 | 0.0008 |
| prod_b64_s8192_q4_cp2 | fp8_p64 | 64 | 4 | 2 (0) | balanced
(long_tile) | 0.2470 | 0.1144 | 2.160 | 2.160 | 0.0005 |
| prod_b64_s8192_q4_cp8 | fp8_p64 | 64 | 4 | 8 (0) | balanced (waves) |
0.0848 | 0.0451 | 1.881 | 1.881 | 0.0011 |
| cp1_peer_b1_s8192_q4 | fp8_p64 | 1 | 4 | 1 (0) | static (one_wave) |
0.0161 | 0.0172 | 0.935 | 0.945 | 0.0003 |
| cp1_peer_b8_s8192_q4 | fp8_p64 | 8 | 4 | 1 (0) | balanced (long_tile)
| 0.0784 | 0.0392 | 2.000 | 2.001 | 0.0003 |
| cp1_peer_b64_s8192_q4 | fp8_p64 | 64 | 4 | 1 (0) | balanced
(long_tile) | 0.4716 | 0.1988 | 2.372 | 2.374 | 0.0004 |
| cp1_peer_b256_s8192_q4 | fp8_p64 | 256 | 4 | 1 (0) | balanced
(long_tile) | 1.7958 | 0.6778 | 2.650 | 2.650 | 0.0004 |
| stretch_b384_s8192_q4_cp4 | fp8_p64 | 384 | 4 | 4 (0) | balanced
(waves) | 0.7684 | 0.3100 | 2.478 | 2.477 | 0.0009 |
| dcp_fp8_agentx_b16_q4_cp4_r0 | fp8_p64 | 16 | 4 | 4 (0) | balanced
(long_tile) | 0.8267 | 0.1954 | 4.230 | 4.223 | 0.0006 |
| dcp_fp8_agentx_b16_q8_cp4_r3 | fp8_p64 | 16 | 8 | 4 (3) | balanced
(long_tile) | 1.3908 | 0.1995 | 6.973 | 6.964 | 0.0007 |
| dcp_fp8_random_128_65k_b64_q4_cp4_r0 | fp8_p64 | 64 | 4 | 4 (0) |
balanced (long_tile) | 0.7489 | 0.1840 | 4.070 | 4.068 | 0.0014 |
| dcp_fp8_random_128_32k_b128_q4_cp4_r0 | fp8_p64 | 128 | 4 | 4 (0) |
balanced (long_tile) | 0.7458 | 0.1908 | 3.910 | 3.907 | 0.0020 |
| prod_d256_b1_ctx32768_q4_cp4_graph | fp8_p64_d256 | 1 | 4 | 4 (0) |
static (one_wave) | 0.0153 | 0.0245 | 0.624 | 0.621 | 0.0003 |
| prod_d256_b8_ctx32768_q4_cp4_graph | fp8_p64_d256 | 8 | 4 | 4 (0) |
static (one_wave) | 0.0212 | 0.0271 | 0.783 | 0.780 | 0.0003 |
| prod_d256_b16_ctx32768_q4_cp4_graph | fp8_p64_d256 | 16 | 4 | 4 (0) |
static (one_wave) | 0.0336 | 0.0337 | 0.997 | 1.001 | 0.0004 |
| prod_d256_b32_ctx32768_q4_cp4_graph | fp8_p64_d256 | 32 | 4 | 4 (0) |
static (one_wave) | 0.0570 | 0.0475 | 1.202 | 1.204 | 0.0004 |
| prod_d256_b64_ctx32768_q4_cp4_graph | fp8_p64_d256 | 64 | 4 | 4 (0) |
balanced (waves) | 0.1102 | 0.0697 | 1.582 | 1.572 | 0.0004 |
| prod_d256_b128_ctx32768_q4_cp4_graph | fp8_p64_d256 | 128 | 4 | 4 (0)
| balanced (waves) | 0.2174 | 0.1051 | 2.068 | 2.067 | 0.0004 |
| prod_d256_b192_ctx32768_q4_cp4_graph | fp8_p64_d256 | 192 | 4 | 4 (0)
| balanced (waves) | 0.3244 | 0.1722 | 1.885 | 1.874 | 0.0004 |
| prod_d256_b256_ctx32768_q4_cp4_graph | fp8_p64_d256 | 256 | 4 | 4 (0)
| balanced (waves) | 0.3792 | 0.1901 | 1.994 | 1.989 | 0.0004 |
| prod_d256_b128_ctx32768_q1_cp4_graph | fp8_p64_d256 | 128 | 1 | 4 (0)
| static (one_wave) | 0.0965 | 0.1021 | 0.945 | 0.946 | 0.0004 |
| prod_d256_b128_ctx32768_q2_cp4_graph | fp8_p64_d256 | 128 | 2 | 4 (0)
| balanced (waves) | 0.1209 | 0.1038 | 1.165 | 1.162 | 0.0004 |
| prod_d256_b128_ctx32768_q3_cp4_graph | fp8_p64_d256 | 128 | 3 | 4 (0)
| balanced (waves) | 0.1688 | 0.1038 | 1.626 | 1.624 | 0.0004 |
| prod_d256_b128_ctx32768_q5_cp4_graph | fp8_p64_d256 | 128 | 5 | 4 (0)
| balanced (waves) | 0.2718 | 0.1345 | 2.021 | 2.016 | 0.0004 |
| prod_d256_b128_ctx32768_q6_cp4_graph | fp8_p64_d256 | 128 | 6 | 4 (0)
| balanced (waves) | 0.3247 | 0.1347 | 2.410 | 2.403 | 0.0004 |
| prod_d256_b128_ctx32768_q7_cp4_graph | fp8_p64_d256 | 128 | 7 | 4 (0)
| balanced (waves) | 0.3265 | 0.1361 | 2.400 | 2.397 | 0.0004 |
| prod_d256_b128_ctx32768_q8_cp4_graph | fp8_p64_d256 | 128 | 8 | 4 (0)
| balanced (waves) | 0.3809 | 0.1372 | 2.777 | 2.767 | 0.0004 |
| dcp_d256_agentx_b16_q4_cp4_r0 | fp8_p64_d256 | 16 | 4 | 4 (0) |
balanced (long_tile) | 0.1950 | 0.0722 | 2.700 | 2.693 | 0.0006 |
| dcp_d256_agentx_b64_q4_cp4_r0 | fp8_p64_d256 | 64 | 4 | 4 (0) |
balanced (long_tile) | 0.7514 | 0.2005 | 3.748 | 3.750 | 0.0007 |
| dcp_d256_random_128_65k_b128_q4_cp4_r3 | fp8_p64_d256 | 128 | 4 | 4
(3) | balanced (long_tile) | 0.4221 | 0.1290 | 3.272 | 3.272 | 0.0018 |

Balanced-routed rows: 55, above 1.0: 55, minimum ratio 1.064;
static-routed rows run the shipped program unchanged (the balanced
column there is the forced arm, for reference only).

</details>

**B200** (NVIDIA B200, 148 SMs, manifest 46a6d77fcc8e, 63 rows):
balanced/static (static = the shipped incumbent route through the same
public entry point; > 1 = balanced faster), balanced-routed rows only:

| family | rows (balanced-routed) | above 1.0 | min / geomean / max |
graph-replay min / geomean |
|---|---|---|---|---|
| bf16 / page 16 / D128 | 11 (10) | 10 / 10 | 1.105 / 2.665 / 6.747 |
1.102 / 2.664 |
| E4M3 / page 64 / D128 | 34 (31) | 31 / 31 | 1.176 / 2.361 / 7.031 |
1.182 / 2.366 |
| E4M3 / page 64 / D256 | 18 (13) | 13 / 13 | 1.192 / 2.230 / 3.898 |
1.186 / 2.224 |

round-3 bodies on the same GPU (unit-1 baseline run): bf16 / page 16 /
D128 min 1.100 / geomean 2.663; E4M3 / page 64 / D128 min 1.139 /
geomean 2.197; E4M3 / page 64 / D256 min 1.180 / geomean 2.204

<details><summary>B200: all 63 rows</summary>

**B200** — NVIDIA B200, 148 SMs (sm_100a), manifest 46a6d77fcc8e, 63
rows; CUPTI, cold L2 (evict_last lines demoted), median (+ CUDA-graph
replay); times in ms.

| row | kind | batch | q | cp (rank) | band route (reason) | static |
balanced | balanced/static | graph ratio | max abs diff out |
|---|---|---|---|---|---|---|---|---|---|---|
| perf_b1_s4096_q4_w4_r0 | bf16_p16 | 1 | 4 | 4 (0) | static (one_wave)
| 0.0106 | 0.0128 | 0.828 | 0.835 | 0.0001 |
| perf_b1_s16384_q8_w4_r0 | bf16_p16 | 1 | 8 | 4 (0) | balanced
(long_tile) | 0.0196 | 0.0177 | 1.105 | 1.102 | 0.0001 |
| perf_b8_s4096_q4_w4_r0 | bf16_p16 | 8 | 4 | 4 (0) | balanced (waves) |
0.0204 | 0.0155 | 1.323 | 1.326 | 0.0001 |
| perf_b8_s16384_q8_w4_r0 | bf16_p16 | 8 | 8 | 4 (0) | balanced
(long_tile) | 0.0935 | 0.0382 | 2.447 | 2.449 | 0.0001 |
| perf_b64_s4096_q4_w4_r0 | bf16_p16 | 64 | 4 | 4 (0) | balanced (waves)
| 0.1104 | 0.0626 | 1.765 | 1.760 | 0.0001 |
| perf_b64_s16384_q8_w4_r0 | bf16_p16 | 64 | 8 | 4 (0) | balanced
(long_tile) | 0.5706 | 0.1800 | 3.170 | 3.169 | 0.0001 |
| perf_b8_s16383_q8_w4_r3_tail | bf16_p16 | 8 | 8 | 4 (3) | balanced
(long_tile) | 0.0936 | 0.0383 | 2.446 | 2.442 | 0.0001 |
| dcp_bf16_agentx_b16_q4_cp4_r0 | bf16_p16 | 16 | 4 | 4 (0) | balanced
(long_tile) | 1.3286 | 0.3463 | 3.836 | 3.854 | 0.0001 |
| dcp_bf16_agentx_b16_q8_cp4_r3 | bf16_p16 | 16 | 8 | 4 (3) | balanced
(long_tile) | 2.3601 | 0.3498 | 6.747 | 6.756 | 0.0001 |
| dcp_bf16_random_128_65k_b64_q4_cp4_r0 | bf16_p16 | 64 | 4 | 4 (0) |
balanced (long_tile) | 1.1915 | 0.3184 | 3.742 | 3.735 | 0.0002 |
| dcp_bf16_random_128_32k_b128_q4_cp4_r0 | bf16_p16 | 128 | 4 | 4 (0) |
balanced (long_tile) | 1.2423 | 0.3264 | 3.806 | 3.805 | 0.0002 |
| prod_b1_s8192_q4_cp4_graph | fp8_p64 | 1 | 4 | 4 (0) | static
(one_wave) | 0.0096 | 0.0164 | 0.588 | 0.598 | 0.0006 |
| prod_b8_s8192_q4_cp4_graph | fp8_p64 | 8 | 4 | 4 (0) | balanced
(two_waves) | 0.0251 | 0.0213 | 1.176 | 1.182 | 0.0008 |
| prod_b32_s8192_q4_cp4_graph | fp8_p64 | 32 | 4 | 4 (0) | balanced
(waves) | 0.0795 | 0.0429 | 1.852 | 1.851 | 0.0007 |
| prod_b64_s8192_q4_cp4_graph | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1448 | 0.0760 | 1.905 | 1.906 | 0.0008 |
| prod_b128_s8192_q4_cp4_graph | fp8_p64 | 128 | 4 | 4 (0) | balanced
(waves) | 0.2724 | 0.1256 | 2.169 | 2.170 | 0.0008 |
| prod_b192_s8192_q4_cp4_graph | fp8_p64 | 192 | 4 | 4 (0) | balanced
(waves) | 0.4009 | 0.1824 | 2.198 | 2.198 | 0.0008 |
| prod_b256_s8192_q4_cp4_graph | fp8_p64 | 256 | 4 | 4 (0) | balanced
(waves) | 0.5301 | 0.2319 | 2.286 | 2.287 | 0.0008 |
| prod_b8_s4096_q4_cp4 | fp8_p64 | 8 | 4 | 4 (0) | static
(two_wave_floor) | 0.0159 | 0.0161 | 0.984 | 0.990 | 0.0010 |
| prod_b8_s4096_q8_cp4 | fp8_p64 | 8 | 8 | 4 (0) | balanced (waves) |
0.0250 | 0.0168 | 1.486 | 1.488 | 0.0011 |
| prod_b8_s16384_q4_cp4 | fp8_p64 | 8 | 4 | 4 (0) | balanced (long_tile)
| 0.0447 | 0.0320 | 1.398 | 1.399 | 0.0005 |
| prod_b8_s16384_q8_cp4 | fp8_p64 | 8 | 8 | 4 (0) | balanced (long_tile)
| 0.0704 | 0.0327 | 2.156 | 2.158 | 0.0005 |
| prod_b64_s4096_q4_cp4 | fp8_p64 | 64 | 4 | 4 (0) | balanced (waves) |
0.0884 | 0.0498 | 1.777 | 1.779 | 0.0010 |
| prod_b64_s4096_q8_cp4 | fp8_p64 | 64 | 8 | 4 (0) | balanced (waves) |
0.1477 | 0.0522 | 2.830 | 2.829 | 0.0011 |
| prod_b64_s16384_q4_cp4 | fp8_p64 | 64 | 4 | 4 (0) | balanced
(long_tile) | 0.2574 | 0.1218 | 2.114 | 2.115 | 0.0006 |
| prod_b64_s16384_q8_cp4 | fp8_p64 | 64 | 8 | 4 (0) | balanced
(long_tile) | 0.4423 | 0.1235 | 3.582 | 3.584 | 0.0005 |
| prod_b256_s4096_q4_cp4 | fp8_p64 | 256 | 4 | 4 (0) | balanced (waves)
| 0.3131 | 0.1518 | 2.062 | 2.064 | 0.0012 |
| prod_b256_s4096_q8_cp4 | fp8_p64 | 256 | 8 | 4 (0) | balanced (waves)
| 0.5601 | 0.1614 | 3.470 | 3.471 | 0.0012 |
| prod_b256_s16384_q4_cp4 | fp8_p64 | 256 | 4 | 4 (0) | balanced
(long_tile) | 0.9646 | 0.3938 | 2.449 | 2.417 | 0.0006 |
| prod_b256_s16384_q8_cp4 | fp8_p64 | 256 | 8 | 4 (0) | balanced
(long_tile) | 1.7158 | 0.4106 | 4.179 | 4.199 | 0.0006 |
| prod_b64_s8191_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1446 | 0.0754 | 1.917 | 1.918 | 0.0008 |
| prod_b64_s8192_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1446 | 0.0753 | 1.921 | 1.923 | 0.0008 |
| prod_b64_s8193_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1445 | 0.0753 | 1.920 | 1.923 | 0.0008 |
| prod_b64_s8194_q4_cp4_residue | fp8_p64 | 64 | 4 | 4 (0) | balanced
(waves) | 0.1446 | 0.0754 | 1.918 | 1.921 | 0.0007 |
| prod_b64_s8192_q4_cp2 | fp8_p64 | 64 | 4 | 2 (0) | balanced
(long_tile) | 0.2577 | 0.1219 | 2.113 | 2.116 | 0.0006 |
| prod_b64_s8192_q4_cp8 | fp8_p64 | 64 | 4 | 8 (0) | balanced (waves) |
0.0884 | 0.0494 | 1.789 | 1.794 | 0.0010 |
| cp1_peer_b1_s8192_q4 | fp8_p64 | 1 | 4 | 1 (0) | static (one_wave) |
0.0166 | 0.0185 | 0.895 | 0.904 | 0.0003 |
| cp1_peer_b8_s8192_q4 | fp8_p64 | 8 | 4 | 1 (0) | balanced (long_tile)
| 0.0804 | 0.0413 | 1.946 | 1.945 | 0.0004 |
| cp1_peer_b64_s8192_q4 | fp8_p64 | 64 | 4 | 1 (0) | balanced
(long_tile) | 0.4901 | 0.2098 | 2.336 | 2.338 | 0.0004 |
| cp1_peer_b256_s8192_q4 | fp8_p64 | 256 | 4 | 1 (0) | balanced
(long_tile) | 1.8512 | 0.7532 | 2.458 | 2.563 | 0.0004 |
| stretch_b384_s8192_q4_cp4 | fp8_p64 | 384 | 4 | 4 (0) | balanced
(waves) | 0.7878 | 0.3355 | 2.349 | 2.352 | 0.0009 |
| dcp_fp8_agentx_b16_q4_cp4_r0 | fp8_p64 | 16 | 4 | 4 (0) | balanced
(long_tile) | 0.8592 | 0.2049 | 4.194 | 4.194 | 0.0007 |
| dcp_fp8_agentx_b16_q8_cp4_r3 | fp8_p64 | 16 | 8 | 4 (3) | balanced
(long_tile) | 1.4694 | 0.2090 | 7.031 | 7.015 | 0.0006 |
| dcp_fp8_random_128_65k_b64_q4_cp4_r0 | fp8_p64 | 64 | 4 | 4 (0) |
balanced (long_tile) | 0.7943 | 0.1931 | 4.115 | 4.140 | 0.0013 |
| dcp_fp8_random_128_32k_b128_q4_cp4_r0 | fp8_p64 | 128 | 4 | 4 (0) |
balanced (long_tile) | 0.8076 | 0.2015 | 4.008 | 4.011 | 0.0021 |
| prod_d256_b1_ctx32768_q4_cp4_graph | fp8_p64_d256 | 1 | 4 | 4 (0) |
static (one_wave) | 0.0162 | 0.0268 | 0.602 | 0.600 | 0.0002 |
| prod_d256_b8_ctx32768_q4_cp4_graph | fp8_p64_d256 | 8 | 4 | 4 (0) |
static (one_wave) | 0.0226 | 0.0299 | 0.757 | 0.755 | 0.0003 |
| prod_d256_b16_ctx32768_q4_cp4_graph | fp8_p64_d256 | 16 | 4 | 4 (0) |
static (one_wave) | 0.0358 | 0.0367 | 0.977 | 0.975 | 0.0003 |
| prod_d256_b32_ctx32768_q4_cp4_graph | fp8_p64_d256 | 32 | 4 | 4 (0) |
static (one_wave) | 0.0606 | 0.0507 | 1.195 | 1.190 | 0.0004 |
| prod_d256_b64_ctx32768_q4_cp4_graph | fp8_p64_d256 | 64 | 4 | 4 (0) |
balanced (waves) | 0.1187 | 0.0732 | 1.621 | 1.618 | 0.0004 |
| prod_d256_b128_ctx32768_q4_cp4_graph | fp8_p64_d256 | 128 | 4 | 4 (0)
| balanced (waves) | 0.2344 | 0.1088 | 2.155 | 2.127 | 0.0004 |
| prod_d256_b192_ctx32768_q4_cp4_graph | fp8_p64_d256 | 192 | 4 | 4 (0)
| balanced (waves) | 0.3496 | 0.1808 | 1.934 | 1.929 | 0.0005 |
| prod_d256_b256_ctx32768_q4_cp4_graph | fp8_p64_d256 | 256 | 4 | 4 (0)
| balanced (waves) | 0.4087 | 0.1970 | 2.074 | 2.065 | 0.0004 |
| prod_d256_b128_ctx32768_q1_cp4_graph | fp8_p64_d256 | 128 | 1 | 4 (0)
| static (one_wave) | 0.0979 | 0.1041 | 0.941 | 0.940 | 0.0004 |
| prod_d256_b128_ctx32768_q2_cp4_graph | fp8_p64_d256 | 128 | 2 | 4 (0)
| balanced (waves) | 0.1260 | 0.1057 | 1.192 | 1.186 | 0.0004 |
| prod_d256_b128_ctx32768_q3_cp4_graph | fp8_p64_d256 | 128 | 3 | 4 (0)
| balanced (waves) | 0.1790 | 0.1067 | 1.678 | 1.674 | 0.0004 |
| prod_d256_b128_ctx32768_q5_cp4_graph | fp8_p64_d256 | 128 | 5 | 4 (0)
| balanced (waves) | 0.2920 | 0.1461 | 1.998 | 1.999 | 0.0005 |
| prod_d256_b128_ctx32768_q6_cp4_graph | fp8_p64_d256 | 128 | 6 | 4 (0)
| balanced (waves) | 0.3493 | 0.1470 | 2.376 | 2.379 | 0.0004 |
| prod_d256_b128_ctx32768_q7_cp4_graph | fp8_p64_d256 | 128 | 7 | 4 (0)
| balanced (waves) | 0.4054 | 0.1490 | 2.721 | 2.709 | 0.0004 |
| prod_d256_b128_ctx32768_q8_cp4_graph | fp8_p64_d256 | 128 | 8 | 4 (0)
| balanced (waves) | 0.4074 | 0.1516 | 2.686 | 2.697 | 0.0004 |
| dcp_d256_agentx_b16_q4_cp4_r0 | fp8_p64_d256 | 16 | 4 | 4 (0) |
balanced (long_tile) | 0.2095 | 0.0766 | 2.734 | 2.722 | 0.0006 |
| dcp_d256_agentx_b64_q4_cp4_r0 | fp8_p64_d256 | 64 | 4 | 4 (0) |
balanced (long_tile) | 0.8097 | 0.2077 | 3.898 | 3.895 | 0.0007 |
| dcp_d256_random_128_65k_b128_q4_cp4_r3 | fp8_p64_d256 | 128 | 4 | 4
(3) | balanced (long_tile) | 0.4573 | 0.1408 | 3.247 | 3.253 | 0.0021 |

Balanced-routed rows: 54, above 1.0: 54, minimum ratio 1.105;
static-routed rows run the shipped program unchanged (the balanced
column there is the forced arm, for reference only).

</details>

## Correctness

- `tests/attention/test_dcp_spec_balanced.py`,
`tests/attention/test_dcp_spec_jit.py`,
`tests/attention/test_dcp_spec_fp8.py`,
`tests/attention/test_cake_fmha.py` on B200 (sm_100a) and GB300
(sm_103a): all green on both GPUs (GB300: 227 passed; 187 passed, 1
skipped; B200: 227 passed; 187 passed, 1 skipped).
- Tolerance suite vs an fp64 reference on every production row of the
DCP and packed-MTP families (max|E|, mean|E| within 1.05x of the round-3
bodies, beyond-1-ulp share within 0.1 pp, dtype caps): PASS on both
GPUs; every row bit-identical over three runs on both GPUs (the round-3
bodies were not on the two-chunk rows).
- compute-sanitizer synccheck + memcheck on B200: `ERROR SUMMARY: 0
errors` for the three DCP families (the two shipped bodies and the
unchanged bf16 body).

## Rounding path

The deterministic fold keeps the arithmetic of the round-3 fold (one
product, one fma -- no extra rounding) and fixes which chunk's term
takes the fma's exact slot to the chunk index instead of the arrival
order; a split row now has one bit pattern instead of two. Unsplit rows
are bit-identical to the round-3 bodies.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Performance**
* Updated speculative attention scheduling and grouped output reductions
across balanced BF16, FP8, and FP16 paths.
* Adjusted two-chunk accumulation order to support consistent output
calculations across supported decode configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [36ad74a](https://github.com/flashinfer-ai/flashinfer/commit/36ad74addfa1260f8f368d650ade47c856fa90e1)

- **作者**: eigen
- **时间**: 2026-10-01T08:36:31Z
- **提交信息**: refactor(cake_comm): drop the unreachable all-reduce-output kernels from the MoE all-reduce fusion bundle and build it through gen_jit_spec (#5849)

## Summary

Part of #5768, resolves the first four steps of #5770.

Since #5514 / #5599, every `trtllm_moe_allreduce_fusion(...,
backend="cake")` call that requests `moe_allreduce_out` is routed to
`cake_trtllm_moe_allreduce_union`. The isolated source bundle
`csrc/cake_trtllm_moe_allreduce_fusion` therefore serves only calls
without the all-reduce output, and its dispatch can no longer select
half of its kernels. This PR removes the dead half, builds the bundle
through the regular JIT path, and keeps the remaining kernels
byte-for-byte (source) and instruction-for-instruction (SASS) identical.

No behaviour or performance change: the kernels that run are the same
binaries, launched with the same grid rule, block size, dynamic shared
memory, cluster dimension and PDL attribute.

## Reachability

The loader selected a kernel as `kernel_index = dtype_index * 6 +
world_index * 2 + output_index` with `output_index =
moe_allreduce_out.has_value()`, then switched to the `_sm103_t1` group
(SM103, `token_num == 1`) or the `_sm100_ws8_mid` group (SM100,
`world_size == 8`, `token_num in {64, 128}`).

- `flashinfer/comm/trtllm_ar.py::_cake_moe_allreduce_union_applies`
sends every call with `moe_allreduce_out` on SM100/SM103 at world sizes
2/4/8 to the union export; `_validate_cake_moe_allreduce` rejects every
other architecture and world size before the bundle is reached. On the
bundle path `output_index == 0` always, so the 14 `*_o1110` kernels are
unreachable.
- Per architecture, the old cubin carried all 28 kernels but could reach
8 (SM100: 6 generic `o0110` + 2 `sm100_ws8_mid`) or 12 (SM103: 6 generic
+ 6 `sm103_t1`).
- The two `sm100_ws8_mid` kernels compile to exactly the same SASS as
the generic eight-rank kernels on `sm_100a` (per-function `cuobjdump
-sass` text identical: `e2a1b86d365aba13` for float16 / 968
instructions, `2db7c534fbac0a3c` for bfloat16 / 1304 instructions, in
the old cubin as well as in a module that still contained them), so
their 64/128-token special case selected an identical binary. They are
removed too; the SM100 module holds the six generic kernels.

Splitting the 14,142-line file into its 28 `extern "C"` blocks confirms
the issue's counts: each `o0110`/`o1110` pair differs by the symbol line
plus one 8-line store of the all-reduce output; the `sm103_t1` clones
differ from the generic kernels by 33/51/87 lines (ws2/4/8), the
`sm100_ws8_mid` clones by 80 lines.

## Changes

-
`csrc/cake_trtllm_moe_allreduce_fusion/cake_trtllm_moe_allreduce_fusion_kernels.cu`:
the 14 `*_o1110` blocks and the 2 `*_sm100_ws8_mid` blocks are deleted;
the 12 remaining blocks are untouched. The `_sm103_t1` group sits behind
`CAKE_MOE_AR_SM103_T1`, which the loader defines per architecture, so
each module contains only the kernels its launcher can select (14,142 →
5,978 lines).
- New `cake_trtllm_moe_allreduce_fusion_launcher.cu`: a regular
`tvm_ffi_utils.h` launcher (`cudaLaunchKernelExC`, cluster `(4,1,1)`,
optional programmatic stream serialization, `grid = min(sm_count, 4 *
tokens)` rounded down to a cluster multiple, 224 threads, 256 B dynamic
smem). The SM count is cached per device instead of queried on every
launch. The `run_reduction` FFI entry and its 18-argument ABI are
unchanged, so `trtllm_ar.py` and the API tests are untouched; a direct
call with `moe_allreduce_out` now raises instead of selecting a kernel
that no longer exists.
- `flashinfer/jit/cake_trtllm_moe_allreduce.py` (542 → 94 lines):
`gen_jit_spec` module per architecture; no `nvcc` subprocesses, no
`manifest.json`, no regex symbol inventory, no re-derived workspace
constants.
- Deleted `manifest.json` and
`tests/comm/test_cake_trtllm_moe_allreduce_source.py` (structure
assertions on the generated text).
- `tests/comm/test_cake_moe_allreduce_distributed.py`: the one-token row
now also runs without the all-reduce output, which exercises the SM103
single-token kernels of this bundle (previously only reachable in
production).
- `.pre-commit-config.yaml`: the clang-format exclusion is narrowed to
the generated kernels file so the launcher is formatted.

Net: 7 files, +1,532 / −10,185 lines.

## Equivalence proof (SASS)

For each architecture, the original 28-kernel file was compiled with the
old loader's exact recipe (`nvcc -cubin -arch=<arch> --std=c++17 -O3
--use_fast_math`) and the new module was built through `gen_jit_spec`.
`cuobjdump -sass` of both was split per function and compared textually.

**sm_100a**: 6/6 kernels identical; old cubin held 28 kernels, new
module holds 6; unexpected symbols: none; missing: none.

| kernel | SASS instructions | old SASS sha256[:16] | new SASS
sha256[:16] | identical |
|---|---|---|---|---|
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws2_o0110` | 1016 |
881b2493d8f886d5 | 881b2493d8f886d5 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws4_o0110` | 1104 |
21ed5bdbebbd6063 | 21ed5bdbebbd6063 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws8_o0110` | 1304 |
2db7c534fbac0a3c | 2db7c534fbac0a3c | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws2_o0110` | 816 |
23b80c81e37d9007 | 23b80c81e37d9007 | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws4_o0110` | 848 |
c725db9efcb02fe6 | c725db9efcb02fe6 | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws8_o0110` | 968 |
e2a1b86d365aba13 | e2a1b86d365aba13 | yes |

**sm_103a**: 12/12 kernels identical; old cubin held 28 kernels, new
module holds 12; unexpected symbols: none; missing: none.

| kernel | SASS instructions | old SASS sha256[:16] | new SASS
sha256[:16] | identical |
|---|---|---|---|---|
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws2_o0110` | 1016 |
6e5793298cc6a10c | 6e5793298cc6a10c | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws2_o0110_sm103_t1` | 1032
| af86422889e70687 | af86422889e70687 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws4_o0110` | 1104 |
70d11ac45c5aad90 | 70d11ac45c5aad90 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws4_o0110_sm103_t1` | 1112
| c2bb8f4e914b1876 | c2bb8f4e914b1876 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws8_o0110` | 1304 |
5f015b254e31ee92 | 5f015b254e31ee92 | yes |
| `kernel_cake_trtllm_moe_reduction_bfloat16_ws8_o0110_sm103_t1` | 1320
| 0efdb38ea9d66ecd | 0efdb38ea9d66ecd | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws2_o0110` | 816 |
e2cf8f563fa2f415 | e2cf8f563fa2f415 | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws2_o0110_sm103_t1` | 832 |
0d7ad3916a811b04 | 0d7ad3916a811b04 | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws4_o0110` | 848 |
a3752380ce77bb0d | a3752380ce77bb0d | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws4_o0110_sm103_t1` | 864 |
6c19def22f53be8a | 6c19def22f53be8a | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws8_o0110` | 968 |
d532a88a52eae5f9 | d532a88a52eae5f9 | yes |
| `kernel_cake_trtllm_moe_reduction_float16_ws8_o0110_sm103_t1` | 984 |
d6afde1a8ced7a93 | d6afde1a8ced7a93 | yes |

The same comparison on the B200 node gives 6/6 and 12/12 identical as
well (CUDA 13.1 and CUDA 13.3 toolchains).


`cuobjdump -symbols` of the new modules lists exactly the reachable
sets: 6 kernels on `sm_100a`, 12 on `sm_103a`.

## Tests

| node | suite | result |
|---|---|---|
| 8×B200 (SM100) | CPU: `test_cake_moe_allreduce_api.py` +
`test_cake_moe_allreduce_union.py` | 86 passed, 19 warnings in 2.96s |
| 8×B200 (SM100) | distributed tp2/4/8 × fp16/bf16 (default
symmetric-memory provider, see note) | 6 failed, 20 warnings in 88.19s
(0:01:28) |
| 8×B200 (SM100) | distributed tp2/4/8 × fp16/bf16
(`TORCH_SYMMMEM=NVSHMEM`) | 6 passed, 20 warnings in 558.55s (0:09:18) |
| 8×B300 (SM103) | CPU: `test_cake_moe_allreduce_api.py` +
`test_cake_moe_allreduce_union.py` | 86 passed, 20 warnings in 3.94s |
| 8×B300 (SM103) | distributed tp2/4/8 × fp16/bf16 (default
symmetric-memory provider, see note) | 6 failed, 20 warnings in 74.91s
(0:01:14) |
| 8×B300 (SM103) | distributed tp2/4/8 × fp16/bf16
(`TORCH_SYMMMEM=NVSHMEM`) | 6 passed, 20 warnings in 507.98s (0:08:27) |


Both nodes ran the tests inside `nvcr.io/nvidia/pytorch:26.01-py3` (CUDA
13.1, nvcc `cuda_13.1.r13.1`), FlashInfer source checkout at the PR tree
on top of upstream `192842b49`. The distributed test needs
`TORCH_SYMMMEM=NVSHMEM` in that container on both nodes; with the
default symmetric-memory provider the workers die inside
`trtllm_create_ipc_workspace_for_all_reduce_fusion` (symmetric-memory
rendezvous: `Failed to bind socket` on the B300 node, SIGSEGV on the
B200 node) before this bundle is even loaded; that code path is not
touched by this PR.

## Follow-up

Step 5 of #5770 (serve `moe_allreduce_out=None` from the union kernels,
route it there, delete this bundle) is tracked separately.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [6eb9eb4](https://github.com/flashinfer-ai/flashinfer/commit/6eb9eb41e4389a1204a283373a9619732f184929)

- **作者**: eigen
- **时间**: 2026-10-01T08:09:36Z
- **提交信息**: refactor(cake_moe_finalize_allreduce_fusion): drop the SM103 copy, fold the PDL/binding clones and replace the import manifest (#5852)

Part of #5771 (umbrella #5768). Mechanical steps 1-5 of that issue; the
templated regeneration (step 6) and hidden sizes other than 7168 remain
follow-ups.

## Summary

`backend="cake"` of `trtllm_moe_finalize_allreduce_fusion` (SM100/SM103,
fp16/bf16, TP 2/4/8, hidden size 7168) shipped 72 generated `.cu` files,
a 7,695-line import manifest and a 950-line loader. Almost all of it was
duplication:

- the 12 `sm_103a/*_device.cu` were byte-identical to `sm_100a/`; the 24
`sm_103a` bindings differed from the `sm_100a` ones only in a namespace
hash;
- `*_pdl0_binding.cu` and `*_pdl1_binding.cu` differed in one launch
attribute;
- every binding re-implemented a device guard and tensor checks that
`tvm_ffi_utils.h` already provides, plus two helpers that were never
called.

This PR keeps the 12 generated device kernels (one per dtype x world
size x quant epilogue, byte-for-byte unchanged) and replaces everything
around them.

## Changes

- **Delete `csrc/cake_moe_finalize_allreduce_fusion/sm_103a/`.** The
SM103 module is now built from the `sm_100a` device sources with the
`sm_103a` nvcc flags. The compiled SASS is identical (table below).
- **One hand-written binding**
(`cake_moe_finalize_allreduce_fusion_binding.cu`, 270 lines) replaces 48
generated ones. It uses `ffi::CUDADeviceGuard`, the `CHECK_*` helpers
and `get_stream`; PDL is a runtime flag that adds the
`cudaLaunchAttributeProgrammaticStreamSerialization` attribute; the
kernel is selected from a `[dtype][world size][quant]` table; the SM
count is cached per device.
- **Byte-typed `quant_out` / `scale_out`.** Both are checked by byte
size (`tokens * 7168 / 2` and the padded SWIZZLED_128x4 size) and accept
any element type, like the TRT-LLM backend. The previous code required
fp16/bf16 storage and sized `scale_out` in 2-byte elements.
- **Loader** `flashinfer/jit/cake_moe_finalize_comm.py`: 950 -> 167
lines. One JIT module per architecture (12 device TUs + binding),
architecture cached per device, no manifest, no SHA-256 of 3.9 MB of
source at first use, no arg-plan interpretation, validation once (in the
binding).
- **Delete the import manifest.** The directory stays on the pre-commit
clang-format exclude list exactly as on main (no change to
`.pre-commit-config.yaml`); the new binding is clang-formatted by hand.
- **Trim** the benchmark (639 -> 401 lines, same CUPTI method and leg
order) and the monkeypatch dispatch test; the GPU test allocates the FP4
outputs as bytes.

Net: **-30,011 lines** (67 files, +544 / -30,555).

## Equivalence

SASS of every kernel, compiled through FlashInfer's JIT before and after
this PR (`cuobjdump -sass`, kernel symbol and addresses normalised), 12
kernels x 2 architectures:

| kernel | SASS sha256 before | SASS sha256 after | instructions |
result |
|---|---|---|---|---|
| sm_100a bfloat16 ws2 o110 | e5327535ceef27ad | e5327535ceef27ad | 706
| equal |
| sm_100a bfloat16 ws2 o111 | e291df2046af2593 | e291df2046af2593 | 786
| equal |
| sm_100a bfloat16 ws4 o110 | 112aeebb4375285a | 112aeebb4375285a | 794
| equal |
| sm_100a bfloat16 ws4 o111 | d1261091b0ff4ba4 | d1261091b0ff4ba4 | 874
| equal |
| sm_100a bfloat16 ws8 o110 | 9af1e98f5b6f9ae6 | 9af1e98f5b6f9ae6 | 1002
| equal |
| sm_100a bfloat16 ws8 o111 | 3c97dfb010de8b15 | 3c97dfb010de8b15 | 1074
| equal |
| sm_100a float16 ws2 o110 | 8b4368e903536171 | 8b4368e903536171 | 706 |
equal |
| sm_100a float16 ws2 o111 | 2575837f376ad054 | 2575837f376ad054 | 786 |
equal |
| sm_100a float16 ws4 o110 | 90e883c6ce36c591 | 90e883c6ce36c591 | 794 |
equal |
| sm_100a float16 ws4 o111 | 033aa386a4da9d67 | 033aa386a4da9d67 | 874 |
equal |
| sm_100a float16 ws8 o110 | 398df28cfc8cbb13 | 398df28cfc8cbb13 | 1002
| equal |
| sm_100a float16 ws8 o111 | fbbab10651346659 | fbbab10651346659 | 1074
| equal |
| sm_103a bfloat16 ws2 o110 | 8f016e82526e2c2a | 8f016e82526e2c2a | 706
| equal |
| sm_103a bfloat16 ws2 o111 | bd88a02a3b26fe7f | bd88a02a3b26fe7f | 786
| equal |
| sm_103a bfloat16 ws4 o110 | b408addbe4524e48 | b408addbe4524e48 | 794
| equal |
| sm_103a bfloat16 ws4 o111 | 6bda4c77f2e60f7f | 6bda4c77f2e60f7f | 874
| equal |
| sm_103a bfloat16 ws8 o110 | 26d9884fe93a4336 | 26d9884fe93a4336 | 1002
| equal |
| sm_103a bfloat16 ws8 o111 | 00043a40bd611461 | 00043a40bd611461 | 1074
| equal |
| sm_103a float16 ws2 o110 | 4b11cd68e1430ffd | 4b11cd68e1430ffd | 706 |
equal |
| sm_103a float16 ws2 o111 | 96fab7ceeaeff450 | 96fab7ceeaeff450 | 786 |
equal |
| sm_103a float16 ws4 o110 | 3de717888fc2f013 | 3de717888fc2f013 | 794 |
equal |
| sm_103a float16 ws4 o111 | 3baecaf08bccab11 | 3baecaf08bccab11 | 874 |
equal |
| sm_103a float16 ws8 o110 | a172f3e251648abc | a172f3e251648abc | 1002
| equal |
| sm_103a float16 ws8 o111 | 0ceacee4245d7a1b | 0ceacee4245d7a1b | 1074
| equal |

The same 24 hashes were reproduced on the B300 node (sm_103a build with
nvcc 13.0; B200 node used nvcc 13.3): 24/24 equal on both.

## Tests

Run from source with the FlashInfer JIT on one 8xB200 node (NSC, sglang
26.07 container, CUDA 13.3) and one 8xB300 node (FlashInfer CI cu130
image, CUDA 13.0):

| test | B200 | B300 |
|---|---|---|
| `tests/comm/test_cake_moe_finalize_allreduce.py` (ws 2/4/8 x
fp16/bf16; PDL off/on; incl. the FP4 profile with byte-typed outputs;
TRT-LLM backend as the second arm) | 6 passed | 6 passed |
|
`tests/comm/test_allreduce_fusion_moe_unified_api.py::test_moe_finalize_allreduce_unified_api_cake`
+ `::test_cake_finalize_rejects_non_trtllm_workspace` | 2 passed | 2
passed |
| `tests/comm/test_cake_moe_finalize_dispatch.py` (CPU) | 5 passed | 5
passed |

`pre-commit run --files <changed files>`: all hooks pass (clang-format,
ruff check/format, mypy, whitespace hooks).

## Performance

Paired CUPTI benchmark
(`benchmarks/comm/bench_cake_moe_finalize_allreduce.py`, legs TRT-LLM /
Cake / TRT-LLM, cold L2, rank-max median), same GPUs back to back, main
vs this PR. The device code is unchanged, so only the host path can
move.

Default profiles (fp16/bf16 x tokens 1/16/128/2048 x top_k 4/8 x PDL
off/on x profile 110/111 x shared expert off/on = 128 rows), TP2, two
paired runs per node in opposite tree order so that same-session drift
cancels. `before/after` = Cake median on main / Cake median on this PR
(higher is better for the PR); the TRT-LLM legs of each run serve as the
drift control.

**B200 (NSC nsc-svg-slurm-1-gpu-169)** `NVIDIA B200` TP2, 128 rows x 2
runs (run 1 base->work, run 2 work->base)

| tokens | rows | median(before/after) min | geomean | max |
|---|---|---|---|---|
| 1 | 32 | 0.989 | 1.040 | 1.122 |
| 16 | 32 | 1.005 | 1.051 | 1.093 |
| 128 | 32 | 0.980 | 1.010 | 1.226 |
| 2048 | 32 | 0.987 | 1.001 | 1.014 |

all rows: median-of-runs min 0.980, geomean 1.025, max 1.226; rows with
median below 0.98: 0
per-run raw ratios: min 0.962, geomean 1.025; drift-normalised (TRT-LLM
control): min 0.897, geomean 1.011, max 1.442

**B300 (computelab umb-b300-089)** `NVIDIA B300 SXM6 AC` TP2, 128 rows x
4 paired runs (median of runs)

| tokens | rows | median(before/after) min | geomean | max |
|---|---|---|---|---|
| 1 | 32 | 1.011 | 1.954 | 3.278 |
| 16 | 32 | 1.345 | 1.839 | 2.548 |
| 128 | 32 | 0.816 | 1.318 | 1.830 |
| 2048 | 32 | 0.980 | 1.011 | 1.042 |

all rows: min 0.816, geomean 1.479, max 3.278; rows with median below
0.98: 4; drift-normalised (TRT-LLM control) per-run geomean 1.262

This air-cooled B300 node is noisy: in runs 1-2 (no warm-up) the TRT-LLM
control arm moved together with the Cake arm (e.g. the tree that ran
first measured both arms ~1.7x slower at tokens=1 while clocks ramped;
the fp16 tokens=128 rows had the TRT-LLM leg go 33 -> 42 us together
with the Cake leg). Runs 3-4 add a one-minute warm-up before each
measured tree:

**B300, runs 3-4 only (1-minute warm-up before each measured tree)**
`NVIDIA B300 SXM6 AC` TP2, 128 rows x 2 paired runs (median of runs)

| tokens | rows | median(before/after) min | geomean | max |
|---|---|---|---|---|
| 1 | 32 | 1.830 | 2.450 | 3.494 |
| 16 | 32 | 1.774 | 2.008 | 2.732 |
| 128 | 32 | 1.164 | 1.549 | 1.853 |
| 2048 | 32 | 1.008 | 1.030 | 1.084 |

all rows: min 1.008, geomean 1.674, max 3.494; rows with median below
0.98: 0; drift-normalised (TRT-LLM control) per-run geomean 1.355

The four rows whose 4-run median is below 0.98 are all fp16 top_k=8 rows
whose runs 1-2 show the TRT-LLM control moving by the same factor
(drift-normalised 0.96-0.99) and whose warmed runs are at or above 1.0:

| dtype | tokens | top_k | pdl | profile | shared | per-run before/after
| per-run drift-normalised |
|---|---|---|---|---|---|---|---|
| float16 | 128 | 8 | 0 | 110 | 0 | 0.807 / 0.805 / 0.826 / 1.662 |
0.976 / 0.982 / 0.994 / 1.381 |
| float16 | 128 | 8 | 0 | 110 | 1 | 0.842 / 0.800 / 1.004 / 1.357 |
0.984 / 0.961 / 1.089 / 1.129 |
| float16 | 128 | 8 | 0 | 111 | 0 | 0.823 / 0.811 / 1.008 / 1.685 |
0.983 / 0.977 / 1.002 / 1.395 |
| float16 | 2048 | 8 | 1 | 110 | 1 | 0.998 / 0.959 / 0.961 / 1.065 |
0.993 / 0.987 / 0.982 / 1.031 |

The large gains at small token counts come from the host path: the
Lamport all-reduce waits for the slowest rank's launch, so the per-call
manifest/route scan and the second device query of the old loader showed
up directly in GPU time on this node.

TP4 could not be completed: the main-tree benchmark at TP4 ran for more
than 50 minutes on both nodes and was cut by the step's inactivity
timeout; TP2 covers the same device code and the same host path.

## Follow-ups (tracked in #5771)

- Regenerate the 12 kernels as one templated kernel (dtype x world size
x quant epilogue).
- Hidden sizes other than 7168.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [26a48d3](https://github.com/flashinfer-ai/flashinfer/commit/26a48d38ad2a7c2fd9537096e4270939ddc1bb75)

- **作者**: eigen
- **时间**: 2026-10-01T07:26:14Z
- **提交信息**: refactor(cake_comm): fold the MoE all-reduce union to one kernel per route, one launcher and a small route table (#5848)

Part of #5768; mechanical steps 1–6 of #5769.

## What changes

`csrc/cake_trtllm_moe_allreduce_union` shipped one JIT module per *rank*
of every route: 322 `_kernel.cu` + `_binding.cu` pairs (644 files, 292K
lines) and a 19,150-line loader whose `MODULES` literal carried an arg
plan, a launch record and SHA-256 digests per module. This PR folds that
tree without touching device semantics:

- **One kernel per route.** `world_rank` is already a kernel argument
and 64 of the 66 routes carried byte-identical rank modules (the two
`t128_e16_owner_forward` routes keep one kernel per rank). 322 modules →
33 kernel translation units under `kernels/`, named
`ws{2,4,8}_{bf16,f16}_<specialization>[_rank<r>].cu`.
- **PDL and cooperative launch are runtime flags.**
`griddepcontrol.wait` / `launch_dependents` were unconditional in every
kernel text; PDL only ever changed the launch attribute. The launcher
sets `cudaLaunchAttributeProgrammaticStreamSerialization` /
`cudaLaunchAttributeCooperative` from per-call flags.
- **SM100 and SM103 share one source.** For every route present on both
architectures the kernels differed in one statement (the shared-memory
base address); it is now guarded by `__CUDA_ARCH__ >= 1030`. The common
prelude (typedefs, tensor-map ABI, `make_warp_uniform`, `smem_addr`,
`mapa_to_rank`) moved to `cake_trtllm_moe_allreduce_union_common.cuh`.
- **One launcher.** `cake_trtllm_moe_allreduce_union_launcher.cu`
replaces the 322 generated bindings; it is compiled per kernel with
`-DCAKE_UNION_KERNEL/_DTYPE/_WORLD_SIZE/_BLOCK/_CLUSTER` and uses the
standard `tvm_ffi_utils.h` checks (one `cudaGetDevice`, no device-guard
class, no mutex/map includes). A rejected launch (e.g. a cooperative
grid above the co-resident capacity) now clears the thread's CUDA error
before raising, so the caller's next CUDA call does not report it.
- **Small loader table.** `KERNELS` (33 entries) + `ROUTES` (66 entries:
kernel, residency, cooperative) + `_REVIEWED_SPECIALIZATIONS` (53)
replace the 18K-line `MODULES` literal. The raw-pointer registry (and
its hook in `trtllm_create_ipc_workspace_for_all_reduce_fusion`), the
per-call arg-plan dict and the SHA-256 check are gone; arch and SM count
are cached. No `.tolist()` sync; CUDA-graph capture needs no eager
warm-up call.
- **Tests.** `test_cake_moe_allreduce_union.py` is a routing test (every
route names a kernel of its dtype/world size, every kernel is reachable,
PDL twins share a kernel, selection rules, grid rule, dispatch to union
vs legacy bundle). `test_cake_moe_allreduce_distributed.py` now runs
every reviewed `(token_num, num_experts)` shape plus a `(512, 8)` probe
and asserts that all routes of the `(arch, world size, dtype)` are
reached (previously 40 of 66 routes).

The kernels still take the unused parameters (`workspace_control`,
`workspace_payload_*`, `quant_out`, `scale_out`, `scale_factor`,
`layout_code`); dropping them changes the parameter layout and is left
to the regeneration step (#5769, last checkbox). The legacy bundle
(`cake_trtllm_moe_allreduce_fusion`, #5770) is untouched.

## Equivalence evidence

- **SASS identity.** Every original kernel translation unit (322,
compiled for its architecture with the JIT's nvcc flags) and every
folded kernel (33, compiled for each architecture it serves) were
compiled to cubins and their `cuobjdump -sass` compared after
normalising the kernel symbol:

| arch | original per-rank modules | folded kernels | SASS identical |
different |
  |---|---|---|---|---|
  | sm_100a | 154 | 23 | 154 | 0 |
  | sm_103a | 168 | 25 | 168 | 0 |

(370 compiles, 0 failures; 15 of the 33 folded kernels serve both
architectures, 8 are SM100-only and 10 SM103-only.)
- **Launch configuration** per route (block, cluster, dynamic smem, PDL,
cooperative, persistent CTAs/SM, cluster cap) is carried over verbatim
from the original per-module records.
- **GPU tests** (8 GPUs per node, run from this branch at 973743a59; JIT
build of all 33 folded kernels per rank):

| GPU | `test_cake_moe_allreduce_union.py` + `_api.py` + `_source.py` |
`test_cake_moe_allreduce_distributed.py` tp2/tp4/tp8 (fp16, bf16; every
reviewed `(tokens, experts)` row, all routes reached) | pre-commit |
  |---|---|---|---|
  | B200 (SM100) | 74 passed | 6 passed | clean |
  | B300 (SM103) | 74 passed | 6 passed | clean |

## Size

| | before | after |
|---|---|---|
| `csrc/cake_trtllm_moe_allreduce_union` files | 644 | 35 |
| lines (csrc + loader + tests) | 312,685 | 19,034 |

Produced by a scripted transform (no hand-edited device text); the
transform and its manifest live with the Cake exporter.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4533
- **最后更新**: 2026-10-01T18:31:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34639
- **最后更新**: 2026-10-01T21:21:52Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Dhruv Nair, Sayak Paul

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型

这四个提交属于**功能新增**和**代码重构**为主：两个提交为新模型添加单文件加载支持（Krea 2、Minimax H3），一个提交为代码质量改进（添加 copied-from 注释），一个提交是关于 PyTorch 设备后端调度的**重构**。

## 2. 关键变更点及与项目整体方向的关系

- **单文件加载支持（Krea 2 & Minimax H3）**：为新发布或已有的模型（Krea 2、Minimax H3）增加"single file"权重加载能力，让用户可以直接从社区平台（如 Civitai、Hugging Face Hub）下载并加载这些模型的权重文件，无需完整 checkpoint 转换流程。这与 diffusers 项目"降低扩散模型使用门槛、推动社区模型互操作性"的核心目标高度一致，也是 Hugging Face 持续推进"社区权重 → diffusers 原生格式"这一路线的重要一环。

- **TorchDeviceBackend 调度重构（#14792）**：引入 `TorchDeviceBackend` 抽象层来统一调度 torch 设备相关的操作。当前社区对不同硬件加速后端（如 MPS、XPU、ROCM 等）的支持分散在各处代码中，这个重构将设备相关逻辑收敛到统一的接口下，便于后续扩展更多后端，减少维护负担。这是对项目**可维护性和可扩展性**的重要改进。

- **qwenimage 2.1 VAE copied-from 注释**：为 Qwen-Image 2.1 的 VAE 添加标准的"copied from"注释，这是 Hugging Face 项目中的惯例做法，确保代码可追溯性，表明该模块是从上游 VAE 代码派生的，符合项目对代码规范和透明度的要求。

## 3. 对项目的影响和潜在意义

- **用户体验提升**：新模型的单文件支持意味着用户可以更快速地体验 Krea 2 和 Minimax H3 等较新模型，减少上手成本，有利于社区采用。
- **架构层面的长期收益**：`TorchDeviceBackend` 的引入为后续支持更多硬件平台（如 Intel XPU、NVIDIA CUDA 的细粒度管理等）打下基础，是未来多后端策略的铺垫。
- **项目规范性增强**：copied-from 注释的补充反映了项目持续在做代码卫生维护，有助于降低代码审查和协作成本。

## 4. 值得关注的技术点

- **TorchDeviceBackend 抽象设计**：值得关注该抽象如何定义设备能力（capability）查询、调度策略等接口，以及是否引入了注册模式（registry pattern）来管理不同设备后端，这将影响后续硬件适配的扩展方式。
- **单文件加载的实现路径**：Krea 2 和 Minimax H3 的单文件支持需要处理模型权重的去重、安全检查（safetensors 格式）以及与 `from_pretrained` 流程的兼容性。
- **Sayak Paul 的参与**：他是 diffusers 社区中活跃的贡献者之一，这两个功能提交均与其合作完成，体现了项目良好的社区协作模式。

## 5. 基于项目背景的影响总结

huggingface/diffusers 作为 Hugging Face 生态中最重要的开源扩散模型库，其核心使命是让扩散模型的使用尽可能简单且跨平台兼容。本次提交的组合反映了项目当前的两个关键发展路径：

1. **快速跟进社区新模型**：通过单文件加载支持持续扩展支持的模型范围，确保用户总能以最低门槛体验最新研究成果，这与 Hugging Face "democratize machine learning" 的愿景直接呼应。

2. **技术架构的持续演进**：`TorchDeviceBackend` 的重构表明项目在快速迭代的同时也在重视长期的技术债务和架构健康度。随着 AI 硬件生态的多元化（NVIDIA、AMD、Apple Silicon、Intel 等），这种统一的设备抽象对于 diffusers 保持"一键式跨平台推理"体验至关重要。

总体来看，这些提交展示了项目在**功能广度**和**架构深度**两个维度上的同步推进，既满足了社区对新模型支持的即时需求，也为未来的可扩展性做了必要准备。

## 详细提交记录

### [578c9b2](https://github.com/huggingface/diffusers/commit/578c9b2c6636ab2424a0e56186268b83623656b2)

- **作者**: Dhruv Nair
- **时间**: 2026-10-01T11:07:20Z
- **提交信息**: Add single file support for Krea 2 (#14914)

update

### [7997e4e](https://github.com/huggingface/diffusers/commit/7997e4eabb1f880fa5697e2b24de09a892fffad5)

- **作者**: Sayak Paul
- **时间**: 2026-10-01T08:21:28Z
- **提交信息**: chore: add one additional copied from in qwenimage 2.1 vae (#14810)

* add one additional copied from in qwenimage 2.1 vae.

* formattinmg

### [acbabca](https://github.com/huggingface/diffusers/commit/acbabca385070cbcb7554a91d1a2722dc0265c70)

- **作者**: Dhruv Nair
- **时间**: 2026-10-01T08:11:30Z
- **提交信息**: Consolidate torch device backend dispatch (#14792)

* introduce TorchDeviceBackend

* update

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [4de185d](https://github.com/huggingface/diffusers/commit/4de185d6ec51a54ae12a07bba1fccef598e86147)

- **作者**: Dhruv Nair
- **时间**: 2026-10-01T07:44:41Z
- **提交信息**: Add single file support for Minimax H3 (#14839)

update

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
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


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13200
- **最后更新**: 2026-10-01T14:37:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36703
- **最后更新**: 2026-10-02T01:43:18Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 24
- **主要提交者**: Xinyi Song, elvischenv, Kan Wu

## AI分析总结

# sgl-project/sglang 昨日提交分析

## 1. 主要更新类型
本次 33 条提交以**硬件后端适配与量化路径优化**为核心，Bug 修复与性能优化并重，同时包含少量新功能（sgl-router、Rust gRPC）、CI 基线调整与文档补充，整体呈现"多硬件 + 多量化格式"的横向扩展与生产可用性打磨并行的特征。

## 2. 关键变更点及与项目方向的关系
- **AMD gfx950（V4.1）成为最大热点**：FP8/MXFP4 serving、MXFP8 GEMM 替换、OPUS sparse prefill 布局转换、dspark draft 元数据进 CUDA graph、top-k v2 路由、batched GEMM tile 选择等，围绕 ROCm 路径的完整量化推理链路进行补齐。
- **NVIDIA 侧量化与模型修复**：SM100 上的 MXFP4 MoE runner 选择、ModelOpt NVFP4 experts 的 W13 布局保留、DeepSeek V4 Pro TP24 词表 padding、Hopper 上的 FlashMLA KV 格式命名收敛。
- **sgl-router 持续演进**：`--api-key`/`--worker-api-key` 鉴权、`--dp-aware` 按 DP rank 路由、PD 版本组兼容性校验、prefill 失败时 fail-fast 并取消 decode、无 tokenizer 的 load-only 路由。
- **稳定性与隔离性**：Llama4 局部注意力在 CUDA graph 下读取 page table、Kimi-K3 按平台守卫优化路径、DFlash 阻止 NaN/Inf 跨请求泄漏、NCCL 图缓冲注册、Mooncake 传输前校验 state strides。
- **基础设施**：Mamba2 SSD kernel 的 Triton autotune、NIXL stride desc API、Rust gRPC 接入前端生命周期、PPU/NPU 后端注册与 CI 基线。

## 3. 对项目的影响和潜在意义
多硬件覆盖与多量化格式的补全将显著降低用户在不同加速卡上的选型与部署成本；sgl-router 的鉴权、DP 感知路由与 fail-fast 机制则表明该项目正从"性能工具"向"生产级推理网关"演进，配套的 peer bootstrap 文档也印证了这一方向。

## 4. 值得关注的技术点
aiter 版本升级与 MXFP8 GEMM 的引入、CUDA graph 与量化 kernel/元数据构建的协同、MoE 专家布局（W13）对 kernel 选择的影响、以及 state strides 与版本组这类在 PD 分离架构下容易被忽略的一致性校验，均是值得深入跟踪的技术点。

## 5. 基于 README 的项目背景分析
README 强调 SGLang 致力于为 LLM 与多模态模型提供高速推理能力，本次提交群正是这一目标的直接体现：既通过量化与 kernel 优化压低延迟，也通过硬件后端（AMD/NVIDIA/NPU/PPU）与路由器层的加固扩大可部署场景，推动项目在保持性能优势的同时提升工程成熟度。

## 详细提交记录

### [5423a4d](https://github.com/sgl-project/sglang/commit/5423a4d88526416b45395d69164bfcd23835e507)

- **作者**: shyeh25
- **时间**: 2026-10-01T23:12:34Z
- **提交信息**: [MegaMoE] Preserve W13 layout for ModelOpt NVFP4 experts (#39388)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>

### [f17f770](https://github.com/sgl-project/sglang/commit/f17f7705a5a67c137edf279edfdbd5460f2ceb6e)

- **作者**: sonle5
- **时间**: 2026-10-01T22:59:44Z
- **提交信息**: [AMD] [GLM-5.3-Flash] Enable FP8 and MXFP4 serving on gfx950 (#39273)

Co-authored-by: Byron Hsu <byron+per@periodiclabs.ai>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: long10024070 <long10024070@users.noreply.github.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: sunxxuns <126995791+sunxxuns@users.noreply.github.com>
Co-authored-by: Long Luong <long.luong2+personal@onemount.com>

### [80bb3fb](https://github.com/sgl-project/sglang/commit/80bb3fb6511ac421ed3b4309067681392203f3bd)

- **作者**: Jan Bernlöhr
- **时间**: 2026-10-01T22:33:30Z
- **提交信息**: [Fix] Select the MXFP4 MoE runner for MiMo-V2 packed experts on SM100 (#41668)

Co-authored-by: jbernloehr <janbernloehr@users.noreply.github.com>

### [a21dcbd](https://github.com/sgl-project/sglang/commit/a21dcbd3204f485ef43d24adea03543d0897ac9b)

- **作者**: Kan Wu
- **时间**: 2026-10-01T21:54:59Z
- **提交信息**: [sgl-router] Support engines started with --api-key (--worker-api-key) (#41996)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [d756521](https://github.com/sgl-project/sglang/commit/d7565215ec9631d55e737437b3ac9f19dc0f2ab2)

- **作者**: Kan Wu
- **时间**: 2026-10-01T21:50:59Z
- **提交信息**: [sgl-router] Route to a specific DP rank inside multi-rank workers (--dp-aware) (#41974)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>

### [52d5fae](https://github.com/sgl-project/sglang/commit/52d5faed5bfaa9aedb80a2a4c7c64e526cbe557a)

- **作者**: Martin Hua
- **时间**: 2026-10-01T21:42:22Z
- **提交信息**: [Bugfix] Llama4 local attention: read page ids from the graph tables in CUDA-graph capture/replay (page_size > 1) (#38187)

### [bf2d686](https://github.com/sgl-project/sglang/commit/bf2d686a82a1fdb4bd7f1fa9ff18ad2562dd8314)

- **作者**: elvischenv
- **时间**: 2026-10-01T21:25:37Z
- **提交信息**: Add triton autotune on the Mamba2 SSD kernels (#39130)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [dcf4e18](https://github.com/sgl-project/sglang/commit/dcf4e182839c2df77f6eaf2c3303b80bcf982bff)

- **作者**: Jiajun Li
- **时间**: 2026-10-01T19:34:23Z
- **提交信息**: fix(nccl): disable graph buffer registration for pausable graph pools (#40648)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a71c7d1](https://github.com/sgl-project/sglang/commit/a71c7d19e7154f5cf2a698418486706f7ce314f6)

- **作者**: Shangming Cai
- **时间**: 2026-10-01T18:20:36Z
- **提交信息**: [Router] Document peer bootstrap: flags, RBAC, downward API, probe implications (#42049)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [3f4bfda](https://github.com/sgl-project/sglang/commit/3f4bfda13ce9b30db766594800e066e0e229caf3)

- **作者**: Michael Gschwind
- **时间**: 2026-10-01T18:11:18Z
- **提交信息**: [Bugfix] Fix DeepSeek V4 Pro TP24 vocabulary-padding failure on Hopper (#31801)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a0fcebb](https://github.com/sgl-project/sglang/commit/a0fcebb3bb7043e62b6ca8885b9e723f2262e091)

- **作者**: Ilia Yastrebov
- **时间**: 2026-10-01T17:53:00Z
- **提交信息**: NIXL: Use stride desc API (#37827)

Signed-off-by: Ilia Yastrebov <iyastrebov@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>

### [fb92ba1](https://github.com/sgl-project/sglang/commit/fb92ba11279b02677da01ee6782afdb6cdb6a31c)

- **作者**: jain-ria
- **时间**: 2026-10-01T17:44:56Z
- **提交信息**: [Rust] Wire the gRPC server into the frontend lifecycle (#41964)

Signed-off-by: jain-ria <riajain@NVIDIA.com>

### [f03a183](https://github.com/sgl-project/sglang/commit/f03a183719c9e7fb2bd528ed5c7e3b627d9df92d)

- **作者**: Joe
- **时间**: 2026-10-01T15:53:31Z
- **提交信息**: Fix Kimi-K3 MLA output gate dispatch on non-CUDA devices (#36406)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [3031091](https://github.com/sgl-project/sglang/commit/3031091c36982478fcb694c3215cb03e9874c551)

- **作者**: Joe
- **时间**: 2026-10-01T15:53:05Z
- **提交信息**: [Kimi-K3] Guard optimized paths by platform (#40269)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [1bbce57](https://github.com/sgl-project/sglang/commit/1bbce57d9e2d7261eadce2f700e063a0647c3268)

- **作者**: Артем Савкин
- **时间**: 2026-10-01T15:02:37Z
- **提交信息**: [NPU] [Diffusion] Fix NPU multimodal-gen CI (#41528)

### [41cbe65](https://github.com/sgl-project/sglang/commit/41cbe65de05b209f3263942389267f79bd749d6a)

- **作者**: Kan Wu
- **时间**: 2026-10-01T12:24:20Z
- **提交信息**: [sgl-router] Enforce compatible PD version groups (#41613)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kan Wu <kan.wu@MacBook-Pro.local>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [3b2ad1c](https://github.com/sgl-project/sglang/commit/3b2ad1c6ae54ff752fba1ece3dffc7214df5c813)

- **作者**: Kan Wu
- **时间**: 2026-10-01T11:35:56Z
- **提交信息**: [sgl-router] Fail fast and cancel decode when prefill fails (#41612)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [1a0250c](https://github.com/sgl-project/sglang/commit/1a0250c5b6f25d2b59d39855e3636ce701d06248)

- **作者**: Aurick Qiao
- **时间**: 2026-10-01T10:47:41Z
- **提交信息**: [Disagg] Validate state strides before Mooncake transfers (#41607)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>

### [d669efb](https://github.com/sgl-project/sglang/commit/d669efba8464538acf8b2ee9417d4a897d00221a)

- **作者**: Thomas Wang
- **时间**: 2026-10-01T10:35:28Z
- **提交信息**: [AMD][V4.1][*/N] Greedy dspark draft/accept under SGLANG_SIMULATE_ACC_LEN (#41981)

Co-authored-by: wunhuang <wunhuang@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [4663796](https://github.com/sgl-project/sglang/commit/46637965ab378efc48938b980b1c80cf37e389f9)

- **作者**: Kan Wu
- **时间**: 2026-10-01T10:30:35Z
- **提交信息**: [sgl-router] Allow load-only routing without a tokenizer (#41611)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [3c4e218](https://github.com/sgl-project/sglang/commit/3c4e2187793dc7d85054964b9526bf707d9643b1)

- **作者**: Xinyi Song
- **时间**: 2026-10-01T10:21:25Z
- **提交信息**: [AMD][V4.1][*/N] OPUS sparse prefill on gfx950 through layout conversion (#42017)

Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: thomawan <thomawan@amd.com>

### [f45c004](https://github.com/sgl-project/sglang/commit/f45c004e18d22222356928eac0a5c26d7af3398f)

- **作者**: kk
- **时间**: 2026-10-01T09:17:13Z
- **提交信息**: [AMD][V4.1][*/N] Build DSpark draft metadata inside the CUDA graph on ROCm (#42014)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [7be0e85](https://github.com/sgl-project/sglang/commit/7be0e8565854c16ba8162f0d68da3f72f62e438d)

- **作者**: 黄孝君
- **时间**: 2026-10-01T09:13:28Z
- **提交信息**: [CI][NPU][Diffusion] Bump ascend consistency GT to the CANN 9.1.0 baseline (#41500)

### [73ba651](https://github.com/sgl-project/sglang/commit/73ba6513f46923736a88273adb193517f804cb82)

- **作者**: Xinyi Song
- **时间**: 2026-10-01T09:04:39Z
- **提交信息**: [AMD][V4.1][*/N] Switch the fp8 dense GEMMs on gfx950 to aiter's MXFP8 GEMM (#41970)

### [0224fcb](https://github.com/sgl-project/sglang/commit/0224fcbd1cc7c8f3f88a8bfba0d80dd6f69bb255)

- **作者**: Xinyi Song
- **时间**: 2026-10-01T08:56:31Z
- **提交信息**: [AMD][V4.1][*/N] Route low-ratio indexer and candidate-block top-k through top-k v2 (#41947)

### [5fab1f0](https://github.com/sgl-project/sglang/commit/5fab1f0f51df1f5536fe989e859b59e28a389834)

- **作者**: Cheng Wan
- **时间**: 2026-10-01T08:55:15Z
- **提交信息**: [Fix] Let the aiter DCP ASM decode test run without aiter (#42018)

### [69240ba](https://github.com/sgl-project/sglang/commit/69240ba7d640650c12d98c1615fc67142030966e)

- **作者**: Thomas Wang
- **时间**: 2026-10-01T08:52:39Z
- **提交信息**: [AMD][V4.1][*/N] Pick the gfx950 wo_a batched gemm tile by row count (#41971)

### [ffb1341](https://github.com/sgl-project/sglang/commit/ffb134188b005b0cdcfcbe92a5e966e8798be063)

- **作者**: Thomas Wang
- **时间**: 2026-10-01T08:49:45Z
- **提交信息**: [AMD] Update aiter version for v41 (#42023)

### [266d9d1](https://github.com/sgl-project/sglang/commit/266d9d1fa7653653b9fef4fb480b63cc601142bc)

- **作者**: Shunkangz
- **时间**: 2026-10-01T08:28:55Z
- **提交信息**: [Qwen3.8 CP 1/4] Context parallelism for QSA attention and the sparse indexer (#39721)

### [b51d4a0](https://github.com/sgl-project/sglang/commit/b51d4a04f08a6a8cd1aabd2f95d4a0a9ae14abf0)

- **作者**: rodamani
- **时间**: 2026-10-01T07:18:37Z
- **提交信息**: [DFlash] Keep grouped-conv taps inside each request's block so NaN/Inf cannot leak across requests (#41736)

Co-authored-by: Rahul Chalamala <22563365+rchalamala@users.noreply.github.com>
Co-authored-by: Devin AI <158243242+devin-ai-integration[bot]@users.noreply.github.com>

### [42f2e4f](https://github.com/sgl-project/sglang/commit/42f2e4fcb742318057e69be357f1aac9cf98df18)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-01T07:16:28Z
- **提交信息**: [DSA] Stop forcing the per-step CPU seq_lens sync for the k-pool indexer (#41987)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [3ed6367](https://github.com/sgl-project/sglang/commit/3ed6367d3f28f11674f72fd298c355f72aee540f)

- **作者**: DarkSharpness
- **时间**: 2026-10-01T07:02:18Z
- **提交信息**: [DSV4/DSA] Name the FlashMLA KV format and drop the V4.1 support probe (#41337)

### [d010e50](https://github.com/sgl-project/sglang/commit/d010e50ad662ffd03fa220a8a0d0bda2d98325a7)

- **作者**: yunzshi
- **时间**: 2026-10-01T07:01:17Z
- **提交信息**: [PPU][1/N] CI: Add backend registration and runner preflight (#39788)

Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
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


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93041
- **最后更新**: 2026-10-02T01:29:07Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 33
- **主要提交者**: Mark McLoughlin, fululi12, YueshenZ

## AI分析总结

# vLLM 昨日提交分析（38 条）

## 1. 主要更新类型

- **性能优化**（约 8 条）：HiSparse 前缀扫描优化、flash-maxsim 迟交互评分、GLM 5.3 qlnorm 跳过（E2E TTFT 提升 4.4%~7.7%）、AITER MLA 页索引并行化、Kimi-K3 Triton 内核迁移、NIXL KV 复制合并等。
- **Bug 修复**（约 14 条）：覆盖 Frontend（Rust 与 Python）、KVConnector、Engram、HiSparse、MRV2、ROCm 量化路径、Nemotron Parse 权重加载等多个子系统。
- **功能新增**：JSON 内置日志格式器、Rust `hf` 响应模板解析器、Step-3.5 流式解析器移植、MiniMax-M3 NVFP4 KV cache、DA8W4 int4 支持等。
- **CI/工程化**：ROCm 测试流水线瘦身、Mypy 修复、自动打标签规则、测试兼容性适配。
- **文档清理**：移除废弃环境变量引用。

## 2. 关键变更点与项目方向的关系

项目目标是"人人可用的快速、低成本 LLM 服务"，这批提交与之高度契合：

- **多硬件后端成熟化**：ROCm/AMD 相关提交多达 11 条（CI、量化、内核、AITER），加上 CPU/Zen（zentorch）和 NVIDIA 侧改动，体现项目持续强化"开放多平台支持"这一核心定位。
- **推理基础设施演进**：Model Runner V2（MRV2）是当前重点重构方向，多个提交（随机 dummy 输入、GDN 预填充元数据、多层 MTP LM head）表明 V2 引擎正在功能补全中。
- **KV 缓存与分布式扩展**：NIXL KVConnector 相关修复与合并（跨缓存组主机缓冲区复制、过期后通知计数）服务于多实例 KV 池化场景。
- **量化精度路径完善**：MXFP8 GEMM、NVFP4、W4A8、DA8W4 等提交直接服务于"低成本服务"目标。

## 3. 对项目的影响与潜在意义

- 性能类提交带来可量化的端到端收益（如 TTFT 提升），增强对生产部署场景的竞争力。
- ROCm CI 瘦身与 bug 修复降低了 AMD 平台的维护成本，可能加速其生产就绪度。
- Rust 前端与解析器统一化（Step-3.5、Responses API 标准化、hf 模板）体现向 OpenAI 兼容 API 收敛，提升生态互操作性。
- Mypy 清理、日志 JSON 格式化等工程质量提升，有利于长期可维护性。

## 4. 值得关注的技术点

- **AI 辅助开发普及**：约半数提交出现 Claude/Codex/Cursor 等 AI co-author，显示 AI 辅助编程已成为 vLLM 贡献的常态。
- **HiSparse 免费缓存与 livelock 修复**：稀疏注意力路径上的性能与正确性问题并存解决，说明该特性正从实验走向稳定。
- **GPU 依赖自动打标签**（auto-label rules）：为多后端仓库的 CI 资源优化提供了自动化范式。
- **竞态类修复**（AITER MLA FP8 调度元数据、Engram Triton 崩溃）提示异步调度与多内核交互仍是潜在风险点。

## 5. 对项目发展的影响总结

结合 README 的"快速、低成本 LLM 服务"愿景，这批次提交集中强化了三件事：一是通过持续的内核级性能优化与量化支持兑现"快速与低成本"；二是通过 ROCm/CPU/NIXL 等多硬件投入兑现"人人可用"的跨平台承诺；三是通过 Rust 前端、API 兼容性与 MRV2 引擎演进，为 vLLM 从"可运行"走向"架构统一、可长期演进"的服务框架奠定基础。整体方向健康，社区协作与 AI 辅助流程也明显走向成熟。

## 详细提交记录

### [e667426](https://github.com/vllm-project/vllm/commit/e6674262f19a0da389dad1c37b5bbd937db80778)

- **作者**: Divakar Verma
- **时间**: 2026-10-01T23:37:36Z
- **提交信息**: [Bugfix][CI] Widen DBO+DP+EP GSM8K accuracy margin on ROCm (#59700)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [e35082e](https://github.com/vllm-project/vllm/commit/e35082e7b627f403b36488cc68a21e291b8d6c8a)

- **作者**: hcl
- **时间**: 2026-10-01T23:35:58Z
- **提交信息**: [Bugfix][CLI] Include inherited field docstrings in get_attr_docs (#49821)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>
Signed-off-by: hclsys <chenglunhu@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [d2125ea](https://github.com/vllm-project/vllm/commit/d2125ea681784c17251c47939f5ed6d1c67384f8)

- **作者**: Aarushi Jain
- **时间**: 2026-10-01T22:30:13Z
- **提交信息**: [ROCm][CI] Raise the MI355 DeepSeek-R1 GSM8K startup wait to 1800s (#59666)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

### [a5105db](https://github.com/vllm-project/vllm/commit/a5105dba05616d74dde5d40267fc500a4422b3db)

- **作者**: Flora Feng
- **时间**: 2026-10-01T22:18:37Z
- **提交信息**: [Frontend] Port Step-3.5 parsers to the streaming parser engine (#59321)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [ca65eb6](https://github.com/vllm-project/vllm/commit/ca65eb67d995f5401c575ec90cba523757127ec7)

- **作者**: Matej Sirovatka
- **时间**: 2026-10-01T21:48:18Z
- **提交信息**: [Perf][HiSparse] Avoid repeated prefix scans and residency updates (#57930)

Signed-off-by: S1ro1 <matej.sirovatka@gmail.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [7566d83](https://github.com/vllm-project/vllm/commit/7566d83bd35cdfd7cd3f9e521a005d2fc1ed1c33)

- **作者**: Yongye Zhu
- **时间**: 2026-10-01T21:39:55Z
- **提交信息**: [Attention][MiniMax-M3] NVFP4 KV cache on the MSA sparse attention path (#59300)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ea84051](https://github.com/vllm-project/vllm/commit/ea84051819c2a52a535e4b6df1fd828def5880f7)

- **作者**: Zijing Liu
- **时间**: 2026-10-01T21:30:58Z
- **提交信息**: [KVConnector][NIXL] Count completion notifications that arrive after KV expiry (#58875)

Signed-off-by: Zijing Liu <liuzijing2014@gmail.com>

### [ccda909](https://github.com/vllm-project/vllm/commit/ccda9098cc5a91b6b6f73e0c0e697022382e01b4)

- **作者**: stefankoncarevic
- **时间**: 2026-10-01T19:54:26Z
- **提交信息**: [ROCm][CI] Drop two no-GPU AMD mirrors from the CPU test areas (#59593)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [840c7c2](https://github.com/vllm-project/vllm/commit/840c7c2f4bc72c7c55edb2dea6d23f9a9c9734e0)

- **作者**: djramic
- **时间**: 2026-10-01T19:38:55Z
- **提交信息**: [Bugfix][Engram] Fix intermittent Triton 3.8 crash in the lookup kernel (#59639)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7b44aad](https://github.com/vllm-project/vllm/commit/7b44aad5db820f8914810ae9f238ffb871e86d44)

- **作者**: Harry Mellor
- **时间**: 2026-10-01T19:32:27Z
- **提交信息**: [MyPy] Fix mypy errors in `vllm/model_executor/models/[kK]*` (#59402)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2a52715](https://github.com/vllm-project/vllm/commit/2a52715ef7ca533a0ce287e14dc1c0702bdc2e8d)

- **作者**: ai-jz
- **时间**: 2026-10-01T19:20:57Z
- **提交信息**: [Bugfix][Responses] Use standard reasoning content-part events (#59652)

Signed-off-by: ai-jz <ai-jz@users.noreply.github.com>
Co-authored-by: ai-jz <ai-jz@users.noreply.github.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [d848c4e](https://github.com/vllm-project/vllm/commit/d848c4ed3d0c576c3c24860547fa2b4ee980b37d)

- **作者**: Jaden Mathias
- **时间**: 2026-10-01T18:41:41Z
- **提交信息**: [ROCm][Triton] Migrate Kimi-K3 kernels from make_block_ptr to tensor … (#58769)

Signed-off-by: JadenMathias <jaden.mathias@amd.com>

### [47de9d4](https://github.com/vllm-project/vllm/commit/47de9d4d049831914858404c48827837c2d915db)

- **作者**: Chanbin Lim
- **时间**: 2026-10-01T18:10:54Z
- **提交信息**: [KV Connector][NIXL] Coalesce host-buffer KV copies across cache groups (#54483)

Signed-off-by: beenpow <57864041+beenpow@users.noreply.github.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [e9be532](https://github.com/vllm-project/vllm/commit/e9be5323f0f864c1dc5a22a138530f3e106ebbb6)

- **作者**: roipony
- **时间**: 2026-10-01T18:06:43Z
- **提交信息**: [Perf] Integrate flash-maxsim Triton kernels for late-interaction scoring (#40337)

Signed-off-by: roi.pony <roi.pony@ibm.com>
Co-authored-by: roi.pony <roi.pony@ibm.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [083060d](https://github.com/vllm-project/vllm/commit/083060d046a84c685fdb4b8932d95869de060543)

- **作者**: Misha Goin
- **时间**: 2026-10-01T17:28:27Z
- **提交信息**: [CI/Build] Add agents auto-label rule (#59641)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3a69636](https://github.com/vllm-project/vllm/commit/3a6963664537ed21172e2ec12e96e3a2dcd3718c)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-01T17:02:31Z
- **提交信息**: [Bugfix][HiSparse] Fix a chunked-prefill preemption livelock (#59494)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [26bfdfb](https://github.com/vllm-project/vllm/commit/26bfdfb6bc5ef85e2128b9ddcf27c369356edd3b)

- **作者**: fululi12
- **时间**: 2026-10-01T17:00:15Z
- **提交信息**: [ROCm][Perf] Parallelise AITER MLA page-index expansion over token chunks (#57978)

Signed-off-by: lifulu <fululi12@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [362cfb7](https://github.com/vllm-project/vllm/commit/362cfb72de36efca1a16c1c92c64e82729536e3d)

- **作者**: Misha Goin
- **时间**: 2026-10-01T16:54:54Z
- **提交信息**: [Agents] Expose PR checklist skill to Claude (#59638)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [08e03df](https://github.com/vllm-project/vllm/commit/08e03df94028d5e7cff96bf569459d8d2b926d9e)

- **作者**: Mehmet Cagri
- **时间**: 2026-10-01T16:32:25Z
- **提交信息**: [Bugfix][ROCm] Use a zero default for masked scales in the MXFP8 GEMM (#59454)

Signed-off-by: Mehmet Cagri Kaymak <mehmet.kaymak@amd.com>

### [9aaef42](https://github.com/vllm-project/vllm/commit/9aaef4296f4eb9df7392de6920b6b2ed79f354ba)

- **作者**: Shijie Lyu
- **时间**: 2026-10-01T16:26:55Z
- **提交信息**: [Bugfix][Frontend] Check reused prompt token ids against the vocab before streaming (#59555)

Signed-off-by: Shijie Lyu <lshjhf@gmail.com>

### [83cadd6](https://github.com/vllm-project/vllm/commit/83cadd65d9ec9e7c2839339a8f70f201246b540b)

- **作者**: aniskumar-nv
- **时间**: 2026-10-01T16:26:33Z
- **提交信息**: [Bugfix] Tie lm_head.weight for Nemotron Parse when checkpoint omits it (#53020)

Signed-off-by: Anish Kumar <aniskumar@nvidia.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [cfd54ca](https://github.com/vllm-project/vllm/commit/cfd54ca8819de923dcf555807298eaca34dd342d)

- **作者**: stefankoncarevic
- **时间**: 2026-10-01T15:10:49Z
- **提交信息**: [ROCm][CI] Drop four no-GPU CPU groups from the legacy AMD pipeline (#59595)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [b538d80](https://github.com/vllm-project/vllm/commit/b538d807ffe0976af7e5d107ccfe77e676b83b70)

- **作者**: ai-jz
- **时间**: 2026-10-01T14:59:15Z
- **提交信息**: [Bugfix][MRV2] Keep GDN prefill checkpoint metadata local to each cache group (#59536)

Signed-off-by: Jingqiao Zhang <ai-jz@users.noreply.github.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Jingqiao Zhang <ai-jz@users.noreply.github.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [5d9214d](https://github.com/vllm-project/vllm/commit/5d9214d6b2ebecb05a9b4cafc2763404acb79289)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-01T13:44:40Z
- **提交信息**: [Bugfix][Frontend] Strip `x-anthropic-billing-header` billing header from `/v1/chatcompletions` (#59419)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [f3b77ef](https://github.com/vllm-project/vllm/commit/f3b77eff640b5ed5cc9221a4f5f402ab65adc021)

- **作者**: Idder Ghanbaja
- **时间**: 2026-10-01T13:03:03Z
- **提交信息**: [Rust][Benchmark] Warn when temperature is left to the server default (#59247)

### [ab52667](https://github.com/vllm-project/vllm/commit/ab5266769e702434a0968d47319d0731d8ccac35)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-01T10:19:02Z
- **提交信息**: [CI/Build] Add mooncake auto-label rule and assign topic owners (#59192)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [cb6458c](https://github.com/vllm-project/vllm/commit/cb6458c5ce61632524c0447d49790725c1e1d9a2)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-01T09:59:37Z
- **提交信息**: [Core] Remove deprecated mamba_cache_mode "all" (#58997)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Thomas Parnell <tpa@zurich.ibm.com>

### [08d77ca](https://github.com/vllm-project/vllm/commit/08d77cad7be4c2ba1f72ebbd5d58571e7e91b2de)

- **作者**: YueshenZ
- **时间**: 2026-10-01T09:25:45Z
- **提交信息**: [Bugfix] Gate Kimi-K3 KDA warmup on sys.modules to skip Kimi import for non-Kimi models (#59257)

Signed-off-by: YueshenZ <YueshenZ@users.noreply.github.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: YueshenZ <YueshenZ@users.noreply.github.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>

### [bcee730](https://github.com/vllm-project/vllm/commit/bcee730b1a9d25f0fd283a0ef6c19133ebeebf4f)

- **作者**: Sundri Lai
- **时间**: 2026-10-01T08:26:14Z
- **提交信息**: [Docs] Remove references to removed env vars (#59530)

Signed-off-by: Sundri Lai <laiyanting.neu@gmail.com>

### [24fb5fc](https://github.com/vllm-project/vllm/commit/24fb5fc08c2bcae8575bd2e861f463d8cf919ffb)

- **作者**: Bugen Zhao
- **时间**: 2026-10-01T08:16:38Z
- **提交信息**: [Rust Frontend] Add `hf` parser for response templates (#59005)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [91fcec1](https://github.com/vllm-project/vllm/commit/91fcec12350aa01cd151d866fd76a307df17d120)

- **作者**: Mark McLoughlin
- **时间**: 2026-10-01T08:11:46Z
- **提交信息**: [Core][Logging] Add built-in JSON formatter (#58739)

Add `--logging-config.formatter=json` to enable the python-json-logger
formatter without having to use a complete Python logging dictConfig.

Signed-off-by: Mark McLoughlin <markmc@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [c4fc3c7](https://github.com/vllm-project/vllm/commit/c4fc3c7d322bbcd1b25307ccbd9770c8eebc5c09)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-01T08:09:14Z
- **提交信息**: [Bugfix][Spec Decode] Per-module LM heads for multi-layer MTP on Model Runner V2 (#58921)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: chanh <channguyen@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e5e38ba](https://github.com/vllm-project/vllm/commit/e5e38ba9b7d18f9746d989e389a51a94b0f96f6f)

- **作者**: Robert Shaw
- **时间**: 2026-10-01T07:52:26Z
- **提交信息**: [Model Runner V2] Support randomized dummy inputs (#58411)

Signed-off-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Robert Shaw <robshaw@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [5addde2](https://github.com/vllm-project/vllm/commit/5addde2a0afa1e27b6e0c478ba9b6995724f006d)

- **作者**: Ganesh R
- **时间**: 2026-10-01T07:51:53Z
- **提交信息**: [CPU][Zen] Pass f32 weight scales to the zentorch INT8 MoE (#59434)

Signed-off-by: Ganesh R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [e12b735](https://github.com/vllm-project/vllm/commit/e12b7351099e23414de79cededdd3854633e986f)

- **作者**: jiangyunfan1
- **时间**: 2026-10-01T07:38:29Z
- **提交信息**: [Test] Make Anthropic messages test compatible with SDK 1.x via extra_body (#57780)

Signed-off-by: jiangyunfan1 <jiangyunfan1@h-partners.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e12291d](https://github.com/vllm-project/vllm/commit/e12291d7332db897885fdc0e6ed61b28c969d743)

- **作者**: Ganesh R
- **时间**: 2026-10-01T07:18:25Z
- **提交信息**: [CPU][Zen] Add DA8W4 (W4A8) int4 support for dense and MoE layers (#54024)

Signed-off-by: R <Ganesh.R@amd.com>
Signed-off-by: Ganesh R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4d6874d](https://github.com/vllm-project/vllm/commit/4d6874d13756868453f78d5e717b2fbe9f8281d0)

- **作者**: Wentao Ye
- **时间**: 2026-10-01T07:13:57Z
- **提交信息**: [GLM 5.3 Perf] Skip qlnorm calculation for MHA, 4.4~7.7% E2E TTFT Improvement (#58845)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [aee8fe2](https://github.com/vllm-project/vllm/commit/aee8fe202a2fbd79a7a33cae70b310edc5960aa5)

- **作者**: Mehdi Ghanimifard
- **时间**: 2026-10-01T07:02:52Z
- **提交信息**: [Bugfix][ROCm] Fix race on AITER MLA FP8 prefill scheduling metadata under async scheduling (#58887)

Signed-off-by: Mehdi Ghanimifard <mehdi.ghanimifard@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-02
**监控日期**: 2026-10-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7022
- **最后更新**: 2026-10-01T23:36:54Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Doug Smith, Youyuan Li, andyluo7

## AI分析总结

## vllm-omni 仓库近期提交分析

### 1. 主要更新类型

以 **Bug 修复** 和 **功能新增** 为主，辅以 **CI/构建流程优化**。四项提交覆盖了跨平台兼容性修复、模型功能扩展和打包机制改进。

### 2. 关键变更点及其与项目方向的关系

- **ROCm/CPU 测试修复**：修复了 AMD ROCm 硬件的测试路由问题和 CPU 场景下的超时问题，以及 Breeze 自动调优配置。这表明项目正在积极扩展对 **AMD GPU 和 CPU 后端** 的支持，降低不同硬件环境下的部署门槛。
- **Ming ISTFT 频谱 float32 修复**：在音频处理管线中修复了 ISTFT 频谱构建的数据类型精度问题，这与项目作为 **omni-modality（全模态）** 服务框架的定位直接相关，音频质量的正确性对多模态推理至关重要。
- **显式打包运行时数据**：改进了构建流程中运行时数据文件的打包方式，使发布产物更规范、更可靠，体现了项目在 **生产就绪度** 上的持续投入。
- **新增 YuE2-3B 音乐生成模型**：新增了文本转音乐模型及对应的 `/v1/audio/speech` 适配器，这是项目向 **音频生成（音乐/语音）** 模态拓展的重要一步。

### 3. 对项目的影响和潜在意义

- **跨平台可用性提升**：ROCm 和 CPU 的修复直接增强了项目在 AMD 硬件和纯 CPU 环境下的可靠性，有助于扩大用户基础和云厂商合作范围。
- **模态覆盖拓展**：YuE2-3B 的加入使 vllm-omni 从语言/视觉/语音服务延伸到 **音乐生成** 领域，进一步印证其 "omni-modality" 的核心目标——为全模态模型提供统一的推理服务框架。
- **工程质量改善**：打包优化和精度修复降低了运维成本，使开发者能更轻松地集成和部署。

### 4. 值得关注的技术点

- **ISTFT 频谱精度问题**：音频合成中浮点精度累积误差可能导致音质劣化，该修复使用 float32 重建频谱，值得其他音频推理框架参考。
- **测试路由机制**：ROCm 测试路由的修复暗示项目 CI 中存在针对不同硬件后端的差异化测试策略，这是大规模多后端推理框架的典型挑战。
- **模型适配器模式**：YuE2-3B 通过 `/v1/audio/speech` 接口暴露，复用了 OpenAI 风格的 API 约定，降低了客户端集成成本。

### 5. 对项目发展的综合影响

从 README 看，vllm-omni 的目标是 **"为所有人提供简单、快速、廉价的全模态模型服务"**。本次提交恰好从三个维度推进了这一愿景：

- **"简单"** —— 打包优化让部署更顺畅；
- **"快速/廉价"** —— 跨平台（ROCm/CPU）修复扩大了硬件选择，降低了成本；
- **"全模态"** —— 新增音乐生成模型和音频精度修复直接丰富了模态覆盖。

整体而言，这些提交反映了项目正处于 **功能扩展与工程稳定性并重** 的成熟阶段，社区活跃且各模块推进均衡，是 vLLM 生态在多模态服务方向上的有力延伸。

## 详细提交记录

### [bbee488](https://github.com/vllm-project/vllm-omni/commit/bbee488da3baf65817f4f8826b1f6e89cc28fda7)

- **作者**: andyluo7
- **时间**: 2026-10-01T23:36:41Z
- **提交信息**: fix: repair ROCm test routing, CPU timeouts, and Breeze autotuning (#8342)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [2560f91](https://github.com/vllm-project/vllm-omni/commit/2560f918592a8ee5d24b7d3fb2ac0bb7da35db1c)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-01T22:45:09Z
- **提交信息**: fix(ming): build ISTFT spectrogram in float32 (#7538)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [7b15d22](https://github.com/vllm-project/vllm-omni/commit/7b15d22f48a4af2ba83f9a209944d0496348fc91)

- **作者**: Doug Smith
- **时间**: 2026-10-01T19:10:21Z
- **提交信息**: [CI/Build] Package runtime data explicitly (#7956)

Signed-off-by: Doug Smith <dosmith@redhat.com>

### [423f343](https://github.com/vllm-project/vllm-omni/commit/423f34326ed420e5acf0b1fb862a1b5ffb7e0fa7)

- **作者**: Youyuan Li
- **时间**: 2026-10-01T10:04:31Z
- **提交信息**: [Model] Add YuE2-3B text-to-music (model + /v1/audio/speech adapter) (#7886)

Signed-off-by: Youyuan Li <105433145+Darcy-Lee@users.noreply.github.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

---
