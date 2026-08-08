# GitHub Stars 合并报告 - 2026-08-08

**合并日期**: 2026-08-09
**监控日期**: 2026-08-08
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


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2135
- **最后更新**: 2026-08-07T20:53:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2600
- **最后更新**: 2026-08-08T15:18:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2191
- **最后更新**: 2026-08-08T17:02:56Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6129
- **最后更新**: 2026-08-08T15:41:45Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Dhiraj Reddy (cuDNN/FlashInfer), Cindy Zhang, Han-Yin Chang

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本批提交包含**性能优化**（MoE内核磁盘缓存）、**Bug修复**（CI测试竞态问题）和**功能新增**（稀疏注意力top-k选择、DSV4 MLA支持）三类变更。

## 2. 关键变更点与项目方向的关系

- **MoE内核磁盘缓存**：将CuTe-DSL内核编译结果持久化到磁盘，使热启动编译时间从秒级降至毫秒级（约135倍加速），直接提升推理框架的启动效率。
- **CI测试修复**：解决`mpirun`与`torch.multiprocessing.spawn`双重启动导致的端口竞争问题，提升测试稳定性。
- **DSV4稀疏MLA支持**：为SM120/SM121架构补齐topk=192/256的decode和prefill调度，支持TP8场景，完善对DeepSeek-V4模型的支持。
- **top_k_varlen新API**：新增稀疏注意力KV选择功能，提供radix、GVR和CUTLASS三种后端，适配不同GPU架构和场景。

## 3. 项目影响与潜在意义

这些变更显著增强了FlashInfer作为**高性能GPU推理内核库**的实用性：磁盘缓存降低实际部署中的启动开销；DSV4支持扩展了前沿模型兼容性；top_k_varlen填补了稀疏注意力推理的关键空白。CI修复则保障了项目持续集成的可靠性。

## 4. 值得关注的技术点

- 缓存键使用**命名函数**作为单一事实来源，并对浮点值做摘要处理保证唯一性
- GVR后端利用注意力模式的时间局部性，以**上一步top-k索引**作为热启动
- radix后端采用**SM感知的多CTA分块**，同时修复大N时的共享内存溢出
- 对不支持的decode形状抛出**可操作的Python错误**而非进程中止

## 5. 对项目发展的影响

结合README中“高性能GPU推理内核”的定位，本批提交体现了项目在**推理全链路优化**上的持续推进：从内核编译效率（缓存）、模型覆盖（DSV4）、到上层API完备性（top_k_varlen）多维度完善。特别是top_k_varlen和DSV4支持，直接服务于当前主流稀疏注意力推理需求，有助于吸引更多生产环境用户。整体上，这些变更巩固了FlashInfer在推理内核领域的竞争力，并展现出对社区贡献的有效整合能力。

## 详细提交记录

### [29196cf](https://github.com/flashinfer-ai/flashinfer/commit/29196cf437778906c72630dc5d9850de547501de)

- **作者**: Han-Yin Chang
- **时间**: 2026-08-08T15:41:33Z
- **提交信息**: perf(moe): persist b12x MoE CuTe-DSL kernels to the disk cache (#4331)

## 📌 Description

Rolls the on-disk CuTe-DSL kernel cache out to the three sm12x NVFP4
fused-MoE kernels (micro,
static, dynamic), addressing #4317. The infrastructure landed in #3874 /
#4029; @bkryu noted in
#4317 that it still had to reach individual kernels and that the core
team lacked bandwidth, so this
applies it to b12x MoE.

Follows the rollout note in `docs/design_docs/cute_dsl_kernel_cache.md`:
each `cute.compile` becomes
a closure passed to `build_and_load_cute_dsl_kernel`. The three
cache-key tuples become named
functions so both cache levels derive from one source of truth, and the
artifact name appends a
digest of that tuple — the keys hold floats and `None` (`swiglu_*`), and
`1.5` / `-1.5` both sanitize
to `1_5`, so a formatted name would not be injective.

As in the existing adopters, the kernels now compile against
`make_fake_stream(use_tvm_ffi_env_stream=True)`, so TVM-FFI supplies the
caller's current stream and
the two launch sites no longer pass one (compiled signatures: 24 / 24 /
32 parameters).

**Not covered:** the direct-micro kernel
(`compile_direct_micro_kernel`), which this module started
dispatching to recently. It compiles without `--enable-tvm-ffi` and
launches through the DSL rather
than a TVM-FFI callable, so caching it is a separate change — #4317 is
only partly closed by this PR.

### Measured — GB10 (sm_121), DSL 4.6.0, five kernel shapes per process

| process | total compile + load |
|---|---:|
| before, two runs | 17.92 s / 17.95 s |
| after, cold first run | 18.91 s |
| after, two later runs | **0.130 s / 0.134 s** (~135×) |

Warm, per kernel: dynamic 7.7 s → 1 ms; static 3.2 s → 1 ms; micro
2.3–3.2 s → 1 ms (the first warm
kernel pays 0.13 s of one-off module setup). The cold run costs a few
percent for the export.
Artifacts are 161–262 KB each.

## 🔍 Related Issues

#4317 (partly — see the scope note above). Builds on the cache
infrastructure from #3874 and #4029.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] `pre-commit` installed.
- [x] Hooks installed.
- [x] `pre-commit run` on the two changed files: all hooks pass, no
files modified. (I ran it
file-scoped rather than `--all-files`, since the remaining hooks are
repo-wide.)

## 🧪 Tests

- [x] Tests added.
- [x] The new tests pass; see the caveat below for what does not run on
my hardware.

- New `tests/moe/test_b12x_moe_kernel_cache.py`: 61 naming-contract
tests — signature coverage,
per-argument perturbation, symbol safety, cross-family collision —
replicating
`tests/jit/test_cute_dsl_cache.py` as the design doc asks of new
adopters (happy to fold them into
  that file instead if you would rather keep all adopters together).
- Also checked on the same host: a corrupt artifact and a read-only
cache directory each fall back to
compiling with a warning, and editing a key source invalidates the
module and recompiles it once.

**Not verified — please check on sm120 hardware.**
`tests/moe/test_b12x_fused_moe.py`'s numerical
tests do not run on my GB10: the nvcc reference ops fail to build (`CUDA
compiler and CUDA toolkit
headers are incompatible`). The suite gives an identical `142 failed, 15
passed` — the same 142 test
ids — on unmodified `main` and on this branch, so I have no accuracy
signal either way. All timings
above are compile/load time; steady-state kernel performance should be
unchanged, since it is the
same binary.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added shared on-disk caching for static, micro, and dynamic MoE
kernels.
  * Improved cache invalidation when source dependencies change.
* Kernel launches now automatically use the caller’s active CUDA stream.

* **Tests**
* Added comprehensive coverage for cache-key completeness, naming
stability, symbol safety, and uniqueness across kernel types.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [29add4e](https://github.com/flashinfer-ai/flashinfer/commit/29add4ed1ca5be502e9ba1f7b01bfa6176a77a2a)

- **作者**: Cindy Zhang
- **时间**: 2026-08-08T12:47:57Z
- **提交信息**: Fix/quantized allreduce ci harness (#4330)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix the CI launch mode for `tests/comm/test_quantized_allreduce.py`.

This test already creates its distributed workers with
`torch.multiprocessing.spawn`, so running it under the outer `mpirun -np
4 pytest` launcher starts multiple pytest parent processes. Each parent
can then spawn its own distributed worker group and race on
TCPStore ports, causing intermittent `EADDRINUSE` failures during
`dist.init_process_group`.

This change keeps MPI-style comm tests under `mpirun`, but runs the
spawn-managed quantized allreduce test with plain `pytest`.


## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/4321 

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

- Dry-run confirmed:
- `tests/comm/test_allreduce_unified_api.py` still runs with `mpirun -np
4 pytest`
- `tests/comm/test_quantized_allreduce.py` now runs with plain `pytest`


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Updated multi-GPU communication test execution to separate MPI-managed
and spawn-managed tests.
* Moved the quantized allreduce test to a standalone test run with
matching dry-run support.
  * Simplified MPI test execution to use the unified API test.
* Improved distributed test setup with temporary file-based rendezvous,
providing more reliable coordination across correctness, edge-case,
scale, benchmark, and command-line test scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [24d7dfb](https://github.com/flashinfer-ai/flashinfer/commit/24d7dfb2639083c5a4d418881099421fc800b7bb)

- **作者**: Gabriel Wu
- **时间**: 2026-08-08T11:33:06Z
- **提交信息**: feat(sm120): consolidate DSV4 sparse MLA top-k 192/256 support (#4380)

## 📌 Description

This PR consolidates the community work needed to run
DeepSeek-V4-Flash-0731 with DSpark through the SM120/SM121 sparse MLA
backend.

A downstream DSpark configuration has 133 active sparse entries per
query: 128 sliding-window entries plus 5 draft entries. The index tensor
is padded to 192 because the kernel consumes 64-entry tiles. Other
integrations use the 256 bucket. Neither shape was fully represented in
the existing SM120 decode and prefill dispatch matrices, so decode-sized
requests could miss the standalone kernel and fall through to the
prefill-only orchestrator, which aborts on `num_tokens <= 64`.

This change:

- adds DSV4 decode instantiations for `topk=192` and `topk=256` with 8,
16, 32, 64, and 128 query heads;
- adds DSV4 single-cache prefill dispatch for `topk=192` and `topk=256`
using BF16 QK;
- supports TP8 prefill by padding H8 into the existing 16-head MG tile
while gating all global Q, sink, output, and LSE accesses;
- enables the padded H8 MG path for both single-cache and dual-cache
prefill, including both supported secondary-cache page sizes and runtime
top-k lengths;
- keeps the Python and CUDA dispatch matrices and user-facing
documentation synchronized;
- raises an actionable Python `ValueError` when an unsupported decode
shape would otherwise enter the prefill-only kernel and abort the
process;
- fixes the sparse MLA benchmark KV cache view to match its default HND
layout; and
- expands correctness and benchmark coverage for the new dispatch
shapes, active-length truncation, HND/NHD layouts, caller-owned
workspaces, and output-buffer reuse.

## 🔍 Related Issues and Community PRs

After coordination with the maintainers, this PR is intended as the
single consolidated replacement for the overlapping open
implementations:

- #4309 — DSV4 `topk=192` decode/prefill and active-length coverage.
- #4372 — broad DSV4 `topk=256` decode/prefill dispatch and public API
coverage.
- #3989 — combined DSpark `topk=256` fix and benchmark HND layout
correction.
- #3817 — DSV4 `topk=256` decode instantiations and decode-to-prefill
fail-fast behavior.
- #3834 — DSV4 `topk=256` BF16 prefill dispatch.

It also covers the implementation scope of the earlier closed
alternatives #3896 and #3923. Related reports include #3828, #3988, and
#4336.

The NVFP4 KV-cache extension in #3937 is a separate feature and is not
superseded by this PR.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I used the repository-compatible `prek` hook runner.
- [x] All hooks relevant to the changed files pass, including
clang-format, mypy, ruff check, and ruff format.
- [x] `git diff --check` passes.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] `pytest -q tests/attention/test_sparse_mla_sm120.py`: 309 passed
on SM120.
- [x] `compute-sanitizer --tool memcheck` on representative H8
single-cache, dual-cache PBS64, dual-cache PBS2, and runtime-length
cases: 4 passed, `ERROR SUMMARY: 0 errors`.
- [x] The complete `benchmarks/bench_sparse_mla_sm120.py` sweep runs
successfully, including the corrected HND path and H8/H16 single- and
dual-cache cases.

## Reviewer Notes

The main review focus is the padded H8 MG specialization. The kernel
still computes a 16-head tile, but only the first 8 rows may touch
caller-owned global tensors; the remaining rows are zero-filled in
shared memory and excluded from sink, output, and LSE accesses. Tests
cover sinks, active-length truncation, the public HND API, dual-cache
full-tile and runtime-length paths, and both secondary-cache page sizes.

AI tools were used to assist with implementation, testing, and PR
preparation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded sparse MLA support for additional head counts and top-k
values, including 192, 256, and 2048.
* Added support for eight-head configurations and more prefill,
token-count, page-size, and dual-cache scenarios.
  * Improved compatibility with HND and NHD layouts.

* **Bug Fixes**
  * Unsupported decode shapes are now rejected before processing.
  * Improved truncation handling for top-k and extra top-k lengths.

* **Tests**
* Expanded coverage for layouts, buffer reuse, workspace, sequence
lengths, decode, and prefill scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: David Orman <ormandj@corenode.com>
Co-authored-by: JimZhang-lab <60953754+JimZhang-lab@users.noreply.github.com>
Co-authored-by: Albert Catalan Tatjer <ac.tatjer@gmail.com>
Co-authored-by: carlosmolina0615 <carlosmolina0615@gmail.com>
Co-authored-by: Wei-Cheng (Wayne) Chiu <waynehacking8@gmail.com>
Co-authored-by: OsakaTX <OsakaTX@users.noreply.github.com>
Co-authored-by: Martin Vit <martin@voipmonitor.org>

### [6d4f309](https://github.com/flashinfer-ai/flashinfer/commit/6d4f3095ee429227fb115f4e6fae9e4e5c5c7696)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-08-08T11:06:09Z
- **提交信息**: feat(topk): Add top_k_varlen with GVR and radix backends for sparse-attention KV selection (#3901)

<!-- .github/pull_request_template.md -->

## 📌 Description

Sparse attention has to pick the top-K KV positions for each request on
every decode step, and requests in a batch have different sequence
lengths. This adds flashinfer.top_k_varlen to do that, with three
backends:

radix – CuTe DSL single-pass multi-CTA radix. Handles variable lengths
natively (no logit masking) and is Blackwell-only. This is the default
when no pre_idx hint is passed.
gvr – Guess-Verify-Refine. Uses the previous step's top-K indices
(pre_idx) as a warm start, since a layer's attention pattern barely
moves from one step to the next. Blackwell-only, with a load-balance
mode for ragged batches.
radix_cutlass – masked fallback on the existing CUTLASS radix kernel.
Runs on any GPU.
backend="auto" uses GVR when a pre_idx hint is available, otherwise the
CuTe DSL radix on Blackwell, otherwise the CUTLASS fallback.

The GVR and radix kernels are ported from TRT-LLM and tuned to match it.
Across the shapes we measured (batch × seq-len × K, bf16 and fp32 on
B200) latency is on par with the equivalent TRT-LLM path. Two changes
did most of that: SM-aware multi-CTA chunking on the radix path, which
also fixes a shared-memory overflow at large N, and feeding the per-CTA
scan width into the GVR launch heuristic.

Also in here:

tests/topk/test_topk_varlen.py – covers the three backends, the
multi-CTA path, CUDA-graph capture/replay, ragged and seq_len <= top_k
cases, and that the backends agree with torch.topk.
benchmarks/routines/topk_varlen.py – compares the backends on a given
shape and reference-checks the results.

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

Unit tests — covers all three backends, the multi-CTA path, CUDA-graph
capture/replay, ragged and seq_len <= top_k cases, and cross-backend
agreement with torch.topk:


pytest tests/topk/test_topk_varlen.py
Trace-template reference correctness:


pytest tests/trace/test_top_k_varlen_reference_correctness.py
Benchmark with a reference check across backends (radix / gvr /
radix_cutlass):


python benchmarks/flashinfer_benchmark.py --routine top_k_varlen \
    --batch_size 16 --max_seq_len 8192 --top_k 512 --refcheck
The GVR and CuTe-DSL radix paths need Blackwell (sm_100+); radix_cutlass
runs anywhere.

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a unified `top_k_decode` API with `radix`, `gvr`, or `auto`
backend selection, plus `load_balance` for Blackwell-optimized hybrid
GVR decoding.
* Added/expanded options: `return_values`, `next_n`, `compress_ratio`,
and support for preallocated output buffers.
* Expanded the public API surface with `top_k_decode` and new GVR tuning
configurations (including load-balanced settings).

* **Tests**
* Added GPU and radix correctness tests covering values, grouping
(`next_n`), compression, preallocation, determinism, fallback behavior,
and configuration validation.

* **Benchmarks**
* Added `top_k_decode` to sampling benchmarks with backend-aware runs
and result verification.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Dhiraj Reddy Nallapa <dnallapa@nvidia.com>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3934
- **最后更新**: 2026-08-08T20:31:12Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34265
- **最后更新**: 2026-08-08T18:05:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 430
- **最后更新**: 2026-08-05T05:40:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12885
- **最后更新**: 2026-08-08T22:22:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31543
- **最后更新**: 2026-08-08T22:22:19Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 16
- **主要提交者**: YAMY, Mick, Mohammad Miadh Angkad

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交涵盖**性能优化**（占比最高）、**Bug修复**、**硬件适配**、**代码重构**、**CI改进**和**文档更新**六大类。其中AMD/ROCm相关适配、DeepSeek模型优化、扩散模型（Diffusion）加速是核心主题。

### 2. 关键变更点与项目方向

- **AMD HIP平台适配**：支持DeepSeek V4 DSpark、分离ROCm专用MHA/MLA前向路径，体现项目对多硬件生态的持续投入，与README中跨平台推理引擎定位一致。
- **Kimi-K3模型优化**：修复路由GEMM精度问题、新增低延迟性能检查，显示对前沿模型的支持深度。
- **扩散模型加速**：清理内核、Sana模型实现bit-exact的LayerNorm+modulate融合（H200去噪延迟降低4.8%），表明项目正从纯LLM向多模态生成扩展。
- **JIT内核重构**：统一命名空间、修复缺失命名空间问题，提升代码可维护性。
- **调度器与内存管理**：统一WAR读完成门控、修复KV缓存别名问题，强化核心推理引擎稳定性。

### 3. 项目影响与潜在意义

- **硬件生态扩展**：AMD/NPU适配持续深化，降低对单一GPU厂商依赖，扩大用户覆盖面。
- **多模态能力增强**：扩散模型优化与K3 VLM特性文档化，标志项目向图像生成领域延伸。
- **性能竞争力提升**：MoE对齐单次启动（小批量多专家场景）、CUDA图捕获优化等，直接改善推理延迟和吞吐。
- **代码质量建设**：CI测试精简、NPU测试效率提升，降低维护成本。

### 4. 值得关注的技术点

- **DCP KV头映射修复**（GQA模型）：解决分布式并行中的关键正确性问题。
- **CUDA图默认捕获**：简化prefill路径，可能影响显存占用与首次延迟的权衡。
- **Triton替代Helion内核**：在Inkling后端用通用Triton替换专用内核，体现对可移植性的追求。
- **多节点VMM自动选择**：VLM推理在多节点场景的显存管理优化。

### 5. 对项目发展的影响

结合README背景，sglang定位为高性能、多硬件支持的推理框架。本次提交显示其正沿三条主线演进：**一是深化AMD/NPU等非NVIDIA平台支持**，构建真正的硬件中立生态；**二是从LLM向多模态（图像生成、VLM）扩展**，抢占生成式AI全栈市场；**三是通过内核级优化维持性能领先**，特别是在DeepSeek、Kimi等热门模型上的表现。这些改动共同强化了sglang作为生产级推理框架的竞争力，为吸引更广泛用户和社区贡献奠定基础。

## 详细提交记录

### [ba7abd4](https://github.com/sgl-project/sglang/commit/ba7abd4f92defcf2d3c3f82a051fa3995cb3d48b)

- **作者**: Wang, FangYuan
- **时间**: 2026-08-08T22:22:14Z
- **提交信息**: [AMD] Support DeepSeek V4 DSpark on AMD HIP platform (#30964)

### [a59bb93](https://github.com/sgl-project/sglang/commit/a59bb931c61bd1314d78e79a857147e0523f2304)

- **作者**: YAMY
- **时间**: 2026-08-08T21:25:09Z
- **提交信息**: Fix DCP KV head mapping for GQA models (#32858)

Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c2d90db](https://github.com/sgl-project/sglang/commit/c2d90db1e31165095b6f7fa770d4464cc1b52100)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-08T20:42:59Z
- **提交信息**: [CI] Add Kimi-K3 low-latency performance check (#34089)

### [c4f018b](https://github.com/sgl-project/sglang/commit/c4f018ba1dac843b7cd25d77c621919b29acd7ee)

- **作者**: Diya Peng
- **时间**: 2026-08-08T20:39:36Z
- **提交信息**: [Refactor] Separate ROCm-specific DeepSeek MHA and MLA forward paths (#31531)

### [3fbb533](https://github.com/sgl-project/sglang/commit/3fbb5330c7e5aecdbd4d6309abc608913c30b7e3)

- **作者**: Brayden Zhong
- **时间**: 2026-08-08T19:23:40Z
- **提交信息**: Fix the router GEMM inaccuracy when using _front_w in Kimi-K3 (#33764)

### [dc9624d](https://github.com/sgl-project/sglang/commit/dc9624deb2f03ebe5e52bd03337addf91386c041)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-08T16:37:00Z
- **提交信息**: [diffusion] Clean up kernels and shared fast paths (#34085)

### [ec5199b](https://github.com/sgl-project/sglang/commit/ec5199b906f14ff09980ccd7666f7a3369ad59db)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-08T14:15:05Z
- **提交信息**: [jit_kernel] Fix missing JIT kernel namespaces (#34106)

Co-authored-by: BBuf <1182563586@qq.com>

### [f3ed82b](https://github.com/sgl-project/sglang/commit/f3ed82b3a8bd7f855f4e1796d1d2e79cf04915a8)

- **作者**: Eric Zhang
- **时间**: 2026-08-08T13:59:32Z
- **提交信息**: [inkling] Let Anthropic thinking=disabled map to reasoning effort "none" (#33913)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [548ff54](https://github.com/sgl-project/sglang/commit/548ff545c53f5ae9f21ee5f0d195dcdaa57a1353)

- **作者**: Gregory Leleytner
- **时间**: 2026-08-08T13:32:40Z
- **提交信息**: [diffusion] fix: guard sage attention sm90 bindings (#34107)

Co-authored-by: RunFMe <RunFMe@users.noreply.github.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [db75dfe](https://github.com/sgl-project/sglang/commit/db75dfe10ff7ef1f735d79178d2f2090683e3eb0)

- **作者**: Mick
- **时间**: 2026-08-08T11:24:49Z
- **提交信息**: fix: always capture default prefill CUDA graph (#33352)

### [cf2d4fd](https://github.com/sgl-project/sglang/commit/cf2d4fd679623b4aa0cad17b8ae18e9229d3bcff)

- **作者**: Mick
- **时间**: 2026-08-08T11:23:00Z
- **提交信息**: docs: clarify K3 VLM feature transport (#34099)

### [cfb354b](https://github.com/sgl-project/sglang/commit/cfb354bcfc5f6757cc843fdeea3921de46076a13)

- **作者**: Leon Gao
- **时间**: 2026-08-08T10:34:44Z
- **提交信息**: [Bugfix] Fix batched KV free aliasing (#34067)

### [a1ca76b](https://github.com/sgl-project/sglang/commit/a1ca76b24bab65603c0107ec4e60a6810127f473)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-08T10:26:36Z
- **提交信息**: [Scheduler] Unify WAR read-done gating behind shared-read boundary declarations (#34052)

### [2c0188c](https://github.com/sgl-project/sglang/commit/2c0188cc782236d609f410f0ce4d95ebe54ce95e)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-08T09:04:16Z
- **提交信息**: [Fix] Give the piecewise CUDA graph test stub an `hf_config` (#34100)

### [f6a6f5b](https://github.com/sgl-project/sglang/commit/f6a6f5bf1e18155acbed3e72d37f46e0cd2010ca)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-08T08:42:46Z
- **提交信息**: [CI] Trim redundant nightly test registrations (#34070)

Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>

### [dd5d82b](https://github.com/sgl-project/sglang/commit/dd5d82bead2e111e23b43d4bc0c4f436a7b56afa)

- **作者**: Cherry_ming
- **时间**: 2026-08-08T08:42:44Z
- **提交信息**: [NPU] Improve the execution efficiency and maintainability of pr‑test‑npu (#33724)

Co-authored-by: Even Zhou <even.y.zhou@outlook.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [e732c0a](https://github.com/sgl-project/sglang/commit/e732c0a9dc071ca06026dba93887e8d77e631d04)

- **作者**: xdtbynd
- **时间**: 2026-08-08T08:15:12Z
- **提交信息**: [UT][NPU] add unit tests for ascend_torch_native_backend and mla_preprocess (#32505)

### [4ad5bb5](https://github.com/sgl-project/sglang/commit/4ad5bb5d9ae0afb270a99937de0cb492f9f2f262)

- **作者**: DarkSharpness
- **时间**: 2026-08-08T08:10:15Z
- **提交信息**: [jit_kernel] Move JIT kernels into namespace sglang (#33400)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5fdf6cd](https://github.com/sgl-project/sglang/commit/5fdf6cd18f978b84fb02b7ac82c740a4d2d7d5e3)

- **作者**: Yuan Luo
- **时间**: 2026-08-08T08:08:25Z
- **提交信息**: [MoE] Single-launch moe_align for tiny batches with many experts (#32395)

### [8914456](https://github.com/sgl-project/sglang/commit/891445676cdfd48841662957d6793ea67c55e783)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-08T08:05:25Z
- **提交信息**: [diffusion] Sana: bit-exact fused aten LayerNorm+modulate under BCG (H200 denoise -4.8%) (#34015)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [d747bd0](https://github.com/sgl-project/sglang/commit/d747bd052ef9bae97459b57b522762e524f62d68)

- **作者**: Mick
- **时间**: 2026-08-08T08:00:58Z
- **提交信息**: feat(vlm): auto-select cuda vmm on multi-node mnnvl (#33936)

### [db3898f](https://github.com/sgl-project/sglang/commit/db3898fec136884a36ef72afa34a0da5b01e300f)

- **作者**: Mick
- **时间**: 2026-08-08T08:00:10Z
- **提交信息**: fix: avoid piecewise prefill graph for trtllm_mla (#32785)

### [afb4f37](https://github.com/sgl-project/sglang/commit/afb4f37ca509544351c48af8470bf60696d74676)

- **作者**: Sam Shleifer
- **时间**: 2026-08-08T07:00:23Z
- **提交信息**: [Inkling] silu_and_mul: replace helion kernels with plain Triton (#33903)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1243
- **最后更新**: 2026-08-08T20:48:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88538
- **最后更新**: 2026-08-08T22:27:34Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: Jeff (Junze) Ma, Tianyu Guo, Vegetog

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次5个提交全部为 **Bug修复**，无功能新增、性能优化或文档更新。修复集中在三个领域：**解析器（Parser）**、**模型内核（Mamba/LFM2）** 和 **编译支持**。

### 2. 关键变更点与项目方向关系
- **Inkling内容块解析修复**（2个提交）：修复了推理结束判定和工具调用时块结束泄漏问题，直接提升LLM输出解析的准确性，与vLLM“易用、快速、廉价”的定位一致。
- **Mamba状态保持修复**：修复了FlashAttention与外部Mamba状态冲突时的结果保持问题，确保混合架构模型（Mamba+Attention）的推理正确性。
- **LFM2 ShortConv量化修复**：修复了量化忽略列表的破坏问题，保障了量化模型的精度和部署稳定性。
- **Qwen3-VL编码器torch.compile支持**：为视觉语言模型编码器添加编译支持，提升推理性能，契合“快速”目标。

### 3. 对项目的影响和潜在意义
- **解析器修复**直接提升多轮对话和工具调用场景的可靠性，对Agent应用至关重要。
- **Mamba和LFM2修复**扩大了vLLM对新兴架构（状态空间模型、混合模型）的支持范围，增强模型生态兼容性。
- **Qwen3-VL编译支持**是性能优化的重要一步，为视觉语言模型的高效部署铺路。

### 4. 值得关注的技术点
- **Inkling块边界处理**：涉及解析器状态机的边界条件，修复了“块结束泄漏”这类隐蔽问题，体现对边缘场景的严谨处理。
- **外部状态与FlashAttention的交互**：Mamba修复涉及注意力机制与外部状态的内存管理，是混合架构推理的核心难点。
- **量化忽略列表的维护**：LFM2修复提醒量化配置与模型结构变更需同步更新，避免静默错误。
- **torch.compile集成**：Qwen3-VL的编译支持需要处理动态形状和自定义算子，是vLLM编译优化能力的验证。

### 5. 对项目发展的影响
vLLM正从“通用LLM推理引擎”向“多架构、多模态、高可靠性”方向演进。本批次修复虽小，但体现了三个战略方向：**一是强化Agent场景的解析可靠性**，为工具调用和结构化输出提供坚实基础；**二是扩展对新兴模型架构的支持**，保持技术领先性；**三是深化编译优化能力**，为极致性能铺路。这些修复共同巩固了vLLM作为“人人可用的LLM服务”的承诺，在正确性、兼容性和性能三个维度持续打磨，为大规模生产部署提供更稳定的基石。

## 详细提交记录

### [1c1077c](https://github.com/vllm-project/vllm/commit/1c1077c6cc4308bdf4c2bf207d7420757a9bfd87)

- **作者**: Vegetog
- **时间**: 2026-08-08T22:07:39Z
- **提交信息**: [Bugfix][Parser] Confirm reasoning end when an Inkling content block opens (#49876)

Signed-off-by: Vegetog <110553275+Vegetog@users.noreply.github.com>

### [75231ef](https://github.com/vllm-project/vllm/commit/75231eff2f3873e2bce7cc9558bb5227ea70b808)

- **作者**: cherry77-cloud
- **时间**: 2026-08-08T16:34:32Z
- **提交信息**: [Bugfix][Parser] Prevent Inkling block-end leakage with tools (#51391)

Signed-off-by: cherry77-cloud <1615405@qq.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [58d3918](https://github.com/vllm-project/vllm/commit/58d3918e3ea0a544ffedadad2ba84559e9c51d8f)

- **作者**: Jeff (Junze) Ma
- **时间**: 2026-08-08T12:20:16Z
- **提交信息**: [BugFix] Preserve divergent FA hits with external Mamba state (#51468)

Signed-off-by: Roger Wang <hey@rogerw.io>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Signed-off-by: Jeff Ma <jeffjma@umich.edu>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [0fe9a91](https://github.com/vllm-project/vllm/commit/0fe9a916e88e884d6ee7fa20c4b15f5a9610218f)

- **作者**: ylsun
- **时间**: 2026-08-08T11:27:13Z
- **提交信息**: [Bugfix] Fix LFM2 ShortConv prefix breaking quant ignore list (#51495)

Signed-off-by: ylsun <1654366371@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [653ebb5](https://github.com/vllm-project/vllm/commit/653ebb52dffd8b4653b430302473c771117529f1)

- **作者**: Tianyu Guo
- **时间**: 2026-08-08T08:23:18Z
- **提交信息**: Add torch compile for qwen3_vl encoder (#40116)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Signed-off-by: Tianyu Guo <guoty@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-09
**监控日期**: 2026-08-08
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5968
- **最后更新**: 2026-08-08T21:57:47Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Hongsheng Liu, Caspian Chen

## AI分析总结

### 主要更新类型
- **功能新增**：为Qwen2.5-Omni模型添加了仅思考器（thinker-only）的ModelOpt NVFP4 W4A4量化检查点支持。
- **文档/流程更新**：新增了vLLM-Omni PR审查技能文档，属于项目协作流程的补充。

### 关键变更点及与项目方向的关系
1. **量化支持扩展**：提交593b404使vLLM-Omni能够加载和运行Qwen2.5-Omni的仅思考器NVFP4 W4A4量化模型。NVFP4是NVIDIA的4位浮点量化格式，W4A4表示权重和激活均为4位。这直接服务于项目“易用、快速、廉价”的omni模态服务目标——通过低比特量化降低显存占用和推理成本，同时保持模型质量，尤其适合仅思考器场景（如推理时不需要视觉/音频编码器）。
2. **PR审查技能文档**：提交f663d12添加了PR审查技能，这属于项目治理和开发效率的改进，有助于标准化代码审查流程，提升协作质量，间接加速功能迭代。

### 对项目的影响和潜在意义
- **量化支持**：显著扩展了vLLM-Omni对Qwen2.5-Omni的部署灵活性。NVFP4 W4A4是当前工业界前沿的低比特量化方案，支持该格式意味着用户可以在更廉价的硬件（如消费级GPU）上运行大型omni模型，降低准入门槛，符合“cheap”的定位。仅思考器模式也优化了推理路径，减少不必要的计算开销。
- **审查技能**：提升项目维护效率，减少低质量PR的合并风险，对长期稳定发展有正面作用。

### 值得关注的技术点
- **ModelOpt NVFP4**：这是NVIDIA Model Optimizer库中的量化方案，采用4位浮点（FP4）存储权重和激活，配合W4A4策略，理论上可减少约4倍内存占用。支持该格式需要vLLM-Omni的量化内核和推理管线适配，可能涉及反量化或混合精度计算。
- **仅思考器（thinker-only）**：Qwen2.5-Omni可能包含多个子模块（如视觉、音频、语言），仅思考器模式只加载语言模型部分，适合纯文本推理任务，减少资源消耗。该提交表明vLLM-Omni已能识别并处理这种部分加载的检查点结构。

### 对项目发展的影响
基于README中“为所有人提供简单、快速、廉价的omni模态服务”的目标，这两个提交分别从**技术能力**和**协作效率**两个维度推动项目：
- 量化支持直接强化了“廉价”和“快速”的承诺，使vLLM-Omni在低成本部署场景中更具竞争力，可能吸引更多中小型团队采用。
- PR审查技能则优化了项目自身的开发流程，确保未来功能迭代的质量和速度，为持续扩展更多omni模型（如其他多模态架构）奠定基础。

整体来看，这批提交体现了vLLM-Omni在**实用化部署**和**社区协作规范化**上的双线推进，既增强了模型服务的性价比，也提升了项目治理的成熟度。

## 详细提交记录

### [593b404](https://github.com/vllm-project/vllm-omni/commit/593b4045391b701fa51b90d38c6f176caaba7a74)

- **作者**: Caspian Chen
- **时间**: 2026-08-08T18:45:57Z
- **提交信息**: [Quantization][Qwen2.5-Omni] Support thinker-only ModelOpt NVFP4 W4A4 checkpoints (#5073)

Signed-off-by: Caspian443 <scrisis843@gmail.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [f663d12](https://github.com/vllm-project/vllm-omni/commit/f663d120c78e225976d6cd07b2f93a5c5e13012d)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-08T14:18:54Z
- **提交信息**: [Misc] Add vLLM-Omni PR review skill (#5871)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
