# GitHub Stars 合并报告 - 2026-11-22

**合并日期**: 2026-11-23
**监控日期**: 2026-11-22
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


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2301
- **最后更新**: 2026-11-22T08:24:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3018
- **最后更新**: 2026-11-22T23:46:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2339
- **最后更新**: 2026-11-22T22:18:32Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6989
- **最后更新**: 2026-11-22T13:54:40Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Henry Tsang, eigen

## AI分析总结

# FlashInfer 昨日提交分析

## 1. 主要更新类型
两笔提交均为**性能优化**为主，辅以 **Bug 修复**：
- **[3adb5ac]** 属于缺陷修复（内存管理导致的性能退化）
- **[1b4d210]** 属于纯性能优化（Kernel 加速）

## 2. 关键变更点与项目方向的关系

**提交一（autotuner CUDA Graph 池共享）：**
- 修复了 autotuner 每次 profiling 捕获都创建独立 PyTorch 私有内存池的问题，改为每个设备共享一个池
- 内存池条目从数千条降到 1 条，`memory_stats()` 调用从数百毫秒降至亚毫秒级
- 与 FlashInfer "高性能 GPU 推理 Kernel" 的目标直接相关：autotune 是 Kernel 选择的关键环节，其开销直接影响推理服务的调度延迟

**提交二（MLA Cake BF16 split-KV 加速）：**
- 为 DeepSeek MLA decode（Blackwell 平台）的 Cake 后端新增 64-split reducer，单行长 KV 查询的 split 数从 32 提升至 64
- 设备程序总数达 23 个（22 个既有 + 1 个新 reducer），仅影响 B200/GB300 的单行长 KV 场景
- `backend="auto"` 现已覆盖长 KV split-KV 桶位，扩大了 Cake 的适用范围

## 3. 对项目的影响和潜在意义

- **生产稳定性提升**：提交一解决了服务进程轮询 `memory_stats()` 时 GIL 阻塞调度线程的问题，冷启动 autotune 多个 MoE shape 时可积累约 27,000 条内存池条目，修复后消除这一隐患，对多 shape MoE 推理服务尤其重要
- **推理吞吐提升**：提交二在 B200 上相对旧 Cake 版本 geomean 加速 1.314x，GB300 达 1.328x；相对最强非 Cake 后端也有小幅优势（B200 geomean 1.033x）
- **不影响 API 兼容性**：两者均无公开 API 变更，对下游用户透明

## 4. 值得关注的技术点

- **CUDA Graph 内存池复用**：私有池条目泄漏导致 `memory_stats()` 字典构建成本线性增长，这是 PyTorch 内存统计机制的隐蔽性能陷阱，值得同类项目借鉴
- **split-KV 上限的硬件特化**：64-split 仅在 batch×q_len=1 的长 KV 场景启用（B200 从 max_seq_len 65536 起、GB300 从 131072 起），体现了对不同 Blackwell SKU 的精细调优
- **严谨的基准方法**：提交二坦承 tactic 选择本身存在噪声（36 个缓存条目中仅 8-13 个一致），并区分了"相对旧 Cake"与"相对最强非 Cake"两组指标，避免过度宣称收益

## 5. 对项目发展的整体影响

结合 README 中"High-Performance GPU Kernels for Inference"的定位，这两笔提交分别从**基础设施可靠性**和**核心算子性能**两个维度推进项目：前者保证 autotuner 在大规模生产部署中不成为调度瓶颈，后者持续压榨 Blackwell 上 DeepSeek MLA decode 的极限性能。两者共同强化了 FlashInfer 作为高性能推理引擎在 MoE 和 MLA 两大主流架构上的竞争力，也反映出项目正深入 Blackwell（sm_100a/sm_103a）新硬件的优化深水区。

## 详细提交记录

### [3adb5ac](https://github.com/flashinfer-ai/flashinfer/commit/3adb5ac7ca7423a3883eff4609933fb9cf3f6cd3)

- **作者**: Henry Tsang
- **时间**: 2026-11-22T20:59:58Z
- **提交信息**: fix(autotuner): share one CUDA graph pool across profiling captures (#9554)

<!-- .github/pull_request_template.md -->

## 📌 Description

Each autotuner profiling capture calls `torch.cuda.graph(graph)` without
`pool=`, so every capture creates a new PyTorch private memory pool.
When the profiled op allocates during capture (for example
`trtllm_fp4_block_scale_moe`), PyTorch keeps a
`reserved_bytes_by_private_pools` entry for that pool in
`torch.cuda.memory_stats()`, even after the graph and pool are released.
`memory_stats()` builds a Python dict per entry, and `memory_reserved()`
/ `memory_allocated()` call it, so their cost grows with every profiled
tactic. Serving processes that poll these for monitoring then stall the
scheduler thread while holding the GIL.

This PR captures all profiling graphs into one pool per device
(`profile_graph_pool()` in `_graph_timing.py`), at the four capture
sites in `flashinfer/autotuner/`, and adds
`tests/autotuner/test_profile_graph_pool.py`. No API change.

One FP4 MoE autotune call (E=16, H=I=3072, T=4096, top_k=4), B300, torch
2.15, flashinfer 0.7.2 with the equivalent change:

| | before | after |
|---|---:|---:|
| new `reserved_bytes_by_private_pools` entries | 2,800 | 1 |
| `torch.cuda.memory_stats()` after tuning | 21.9 ms | 0.06 ms |
| peak reserved memory / `cudaMalloc` calls / alloc retries / tuning
time | 1.23 GiB / 7,181 / 0 / 20.7 s | same |

Two tuning calls in one process (second shape E=32, H=2048, I=1536,
T=2048): 2,800 → 5,104 entries before, 1 → 1 after, stable over 3
alternating fresh-process rounds per arm; the tuned op then runs
normally outside tuning. Chosen tactics vary run to run even without
this change (8–12 of 36 cache entries agree between two unpatched runs;
5–13 of 36 between unpatched and patched), so tactic selection showed no
difference beyond that noise.

A cold-cache serving startup that tunes many MoE shapes accumulated
about 27,000 entries per rank, making each `memory_stats()` call take
350–460 ms.

**Concurrency safety (please check):** graphs that share a pool must not
be captured or replayed concurrently, and the pool is keyed only by
device. Each profiling graph here is captured, replayed and dropped
inside one profiling call. All profiling paths in `autotuner.py`
(`choose_one`, including `_settle_near_ties` → `_retime_candidate`;
`rank_tactics`; `profile_tactic`) run inside `with self._lock` on the
singleton `AutoTuner`, and `profile_individual_graph_calls` is only
called from `_profile_single_kernel`. So captures into this pool are
serialized across threads today. Reviewers should keep that invariant in
mind: any future path that profiles outside `self._lock`, or a second
`AutoTuner` instance, would need a per-thread/per-stream pool instead.
Separate processes get separate pools, so multi-process setups are
unaffected.

**Validation on `main` (B300, torch 2.15):**

- New test (hot, cold-L2 and individual-timing paths, 8 tactics that
each allocate during capture): fails on `main` (+8 entries per tuning
call), passes with this PR. It skips when PyTorch does not report
`reserved_bytes_by_private_pools`, and requires a real tactic with no
profiling failures, so a fully failing capture cannot pass it (both
guards checked).
- `pytest tests/autotuner`: 46 failed / 447 passed with this PR vs 49 /
444 on `main`; the only difference is the 3 new tests. The shared
failures are environment-related in my setup (missing local kernel
artifacts, `benchmarks/` not present, older compiled modules) and fail
identically on both.
- Retained memory (runner allocating 256 / 64 / 128 MiB with 3 failing
tactics / 1024 MiB, tuned in sequence): reserved memory after each
tuning call and peak during it are identical with and without this PR
(e.g. 1026 MiB current, 2050 MiB peak for the 1 GiB case), and
`torch.cuda.empty_cache()` returns to 2 MiB in both. Entries: 8 → 16 →
21 → 29 on `main`, 1 throughout with this PR. Failing tactics during
capture do not break later captures.

Not changed: `moe_ep/cute_dsl/megamoe/bf16_nvfp4/autotune.py` has its
own capture and could use the same helper.

AI-assisted: the change and this description were drafted with an AI
coding agent.

## 🔍 Related Issues

PyTorch keeps released-pool entries by design (pytorch/pytorch#178240).
Related: #6554, #6456 (re-tuning increases the number of captures).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran `pre-commit run --files` on the
changed files; all hooks passed.)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.). (No new failures in
`tests/autotuner`; see validation above.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/autotuner/`

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

This pull request and its description were written by Isaac.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Reduced extra CUDA memory pool creation during autotuner profiling,
helping limit profiling memory overhead across timing modes.
* **Tests**
* Added a regression check for CUDA profiling pool usage and successful
tactic selection.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Isaac <no-reply@databricks.com>

### [1b4d210](https://github.com/flashinfer-ai/flashinfer/commit/1b4d210d62d00f4cac7b57c99e41ca2a98ec2217)

- **作者**: eigen
- **时间**: 2026-11-22T17:33:51Z
- **提交信息**: perf(mla): Cake BF16 split-KV decode uses up to 64 KV splits for one long-KV query row (#9857)

The Cake backend of `trtllm_batch_decode_with_kv_cache_mla` runs
DeepSeek MLA decode on Blackwell. The family now has 23 device programs:
the 22 shipped before, which this PR does not change, plus one new
64-split reducer. This PR delivers the BF16 split-KV route for one query
row with long KV. That route may now use up to 64 KV splits instead of
32, and the new reducer merges them. B200 uses 64 splits from
max_seq_len 65536 and GB300 from max_seq_len 131072, in both cases only
with exactly one query row (batch × q_len = 1). Other devices and other
row counts keep the 32-split cap. The PR changes 36 shapes on B200 and
21 on GB300. On these shapes, the geomean speedup against the previous
Cake version (FlashInfer main 253986e2) is 1.314x on B200 (min 1.007x,
max 1.516x) and 1.328x on GB300 (min 1.052x, max 1.491x). Against the
fastest non-Cake backend, the geomean is 1.033x on B200 (min 0.957x, max
1.399x) and 0.999x on GB300 (min 0.953x, max 1.266x). `backend="auto"`
now offers Cake for the long-KV split-KV buckets.

The kernel's other Cake programs serve the remaining BF16 page-32/64
decode shapes, FP8 page 64, and a generic tail for other shapes, and the
family ships on sm_100a (B200) and sm_103a (GB300).

**Table: explicit `backend="cake"` on every shape this PR changes.**
GPUs: NVIDIA B200 (sm_100a, 148 SMs) and NVIDIA GB300 (sm_103a, 152
SMs). Software: CUDA 13.5 JIT (nvcc 13.5) and torch 2.14.1+cu130. Every
row uses a BF16 KV cache with batch 1 and q_len 1. "KV length" is the
maximum KV length (max_seq_len). The lengths are uniform; varied; short,
meaning short varied lengths under the long maximum; and uniform +
sinks, meaning uniform lengths with attention sinks. "Splits" is the
number of planned KV splits, previous Cake -> this PR. "Previous Cake"
is FlashInfer main 253986e2. "Fastest non-Cake" is the faster of tuned
trtllm-gen and cute-dsl, measured on the same GPU in the same rounds,
with the faster backend in parentheses. Timing is the CUPTI kernel span
over CUDA-graph replay, with L2 flushed before every iteration. Each
value is the median of the per-round medians over 6 rounds. Speedup =
baseline / this PR; >1 means this PR is faster.

| GPU | page size | batch | q_len | KV length | lengths | splits |
previous Cake (us) | fastest non-Cake (us) | this PR (us) | speedup vs
previous Cake | speedup vs fastest non-Cake |
|---|---|---|---|---|---|---|---|---|---|---|---|
| B200 | 32 | 1 | 1 | 65536 | short | 32 -> 64 | 16.448 | 17.296
(cute-dsl) | 15.912 | 1.034x | 1.087x |
| B200 | 32 | 1 | 1 | 65536 | uniform | 32 -> 64 | 35.168 | 27.984
(cute-dsl) | 27.312 | 1.288x | 1.025x |
| B200 | 32 | 1 | 1 | 65536 | uniform + sinks | 32 -> 64 | 35.151 |
38.352 (cute-dsl) | 27.408 | 1.283x | 1.399x |
| B200 | 32 | 1 | 1 | 65536 | varied | 32 -> 64 | 31.632 | 25.919
(cute-dsl) | 25.392 | 1.246x | 1.021x |
| B200 | 32 | 1 | 1 | 65568 | uniform | 31 -> 57 | 36.175 | 28.721
(cute-dsl) | 28.080 | 1.288x | 1.023x |
| B200 | 32 | 1 | 1 | 65568 | varied | 31 -> 57 | 27.360 | 23.729
(cute-dsl) | 23.024 | 1.188x | 1.031x |
| B200 | 32 | 1 | 1 | 98304 | uniform | 32 -> 64 | 47.200 | 35.024
(cute-dsl) | 34.064 | 1.386x | 1.028x |
| B200 | 32 | 1 | 1 | 98304 | varied | 32 -> 64 | 41.105 | 31.537
(cute-dsl) | 30.816 | 1.334x | 1.023x |
| B200 | 32 | 1 | 1 | 131072 | short | 32 -> 64 | 19.488 | 19.440
(cute-dsl) | 18.175 | 1.072x | 1.070x |
| B200 | 32 | 1 | 1 | 131072 | uniform | 32 -> 64 | 59.297 | 41.456
(cute-dsl) | 41.167 | 1.440x | 1.007x |
| B200 | 32 | 1 | 1 | 131072 | uniform + sinks | 32 -> 64 | 59.488 |
52.864 (trtllm-gen) | 41.504 | 1.433x | 1.274x |
| B200 | 32 | 1 | 1 | 131072 | varied | 32 -> 64 | 51.840 | 37.168
(cute-dsl) | 37.616 | 1.378x | 0.988x |
| B200 | 32 | 1 | 1 | 131104 | uniform | 32 -> 61 | 60.912 | 41.376
(cute-dsl) | 42.272 | 1.441x | 0.979x |
| B200 | 32 | 1 | 1 | 131104 | varied | 32 -> 61 | 59.184 | 41.200
(cute-dsl) | 41.952 | 1.411x | 0.982x |
| B200 | 32 | 1 | 1 | 196608 | uniform | 32 -> 64 | 82.912 | 54.208
(cute-dsl) | 54.752 | 1.514x | 0.990x |
| B200 | 32 | 1 | 1 | 196608 | varied | 32 -> 64 | 49.008 | 36.160
(cute-dsl) | 36.112 | 1.357x | 1.001x |
| B200 | 32 | 1 | 1 | 262144 | short | 32 -> 64 | 28.720 | 25.216
(cute-dsl) | 23.633 | 1.215x | 1.067x |
| B200 | 32 | 1 | 1 | 262144 | uniform | 32 -> 64 | 106.368 | 67.632
(cute-dsl) | 70.176 | 1.516x | 0.964x |
| B200 | 32 | 1 | 1 | 262144 | varied | 32 -> 64 | 99.136 | 63.728
(cute-dsl) | 66.560 | 1.489x | 0.957x |
| B200 | 64 | 1 | 1 | 65536 | short | 32 -> 64 | 16.480 | 17.792
(cute-dsl) | 16.096 | 1.024x | 1.105x |
| B200 | 64 | 1 | 1 | 65536 | uniform | 32 -> 64 | 34.783 | 28.176
(cute-dsl) | 27.312 | 1.274x | 1.032x |
| B200 | 64 | 1 | 1 | 65536 | varied | 32 -> 64 | 31.377 | 25.904
(cute-dsl) | 25.328 | 1.239x | 1.023x |
| B200 | 64 | 1 | 1 | 65600 | uniform | 31 -> 57 | 35.936 | 28.528
(cute-dsl) | 28.128 | 1.278x | 1.014x |
| B200 | 64 | 1 | 1 | 65600 | varied | 31 -> 57 | 23.888 | 22.032
(cute-dsl) | 21.104 | 1.132x | 1.044x |
| B200 | 64 | 1 | 1 | 98304 | uniform | 32 -> 64 | 46.496 | 35.024
(cute-dsl) | 33.888 | 1.372x | 1.034x |
| B200 | 64 | 1 | 1 | 98304 | varied | 32 -> 64 | 37.344 | 29.584
(cute-dsl) | 29.104 | 1.283x | 1.017x |
| B200 | 64 | 1 | 1 | 131072 | short | 32 -> 64 | 18.080 | 18.752
(cute-dsl) | 17.952 | 1.007x | 1.045x |
| B200 | 64 | 1 | 1 | 131072 | uniform | 32 -> 64 | 57.824 | 41.152
(cute-dsl) | 40.976 | 1.411x | 1.004x |
| B200 | 64 | 1 | 1 | 131072 | varied | 32 -> 64 | 43.599 | 33.488
(cute-dsl) | 32.312 | 1.349x | 1.036x |
| B200 | 64 | 1 | 1 | 131136 | uniform | 32 -> 61 | 59.552 | 41.632
(cute-dsl) | 41.872 | 1.422x | 0.994x |
| B200 | 64 | 1 | 1 | 131136 | varied | 32 -> 61 | 48.064 | 35.745
(cute-dsl) | 35.168 | 1.367x | 1.016x |
| B200 | 64 | 1 | 1 | 196608 | uniform | 32 -> 64 | 81.232 | 53.552
(cute-dsl) | 54.272 | 1.497x | 0.987x |
| B200 | 64 | 1 | 1 | 196608 | varied | 32 -> 64 | 60.193 | 42.577
(cute-dsl) | 42.480 | 1.417x | 1.002x |
| B200 | 64 | 1 | 1 | 262144 | short | 32 -> 64 | 33.104 | 27.728
(cute-dsl) | 26.352 | 1.256x | 1.052x |
| B200 | 64 | 1 | 1 | 262144 | uniform | 32 -> 64 | 103.584 | 67.824
(cute-dsl) | 68.800 | 1.506x | 0.986x |
| B200 | 64 | 1 | 1 | 262144 | varied | 32 -> 64 | 60.880 | 42.160
(cute-dsl) | 42.720 | 1.425x | 0.987x |
| GB300 | 32 | 1 | 1 | 131072 | short | 32 -> 64 | 18.512 | 18.144
(cute-dsl) | 17.568 | 1.054x | 1.033x |
| GB300 | 32 | 1 | 1 | 131072 | uniform | 32 -> 64 | 55.200 | 39.752
(cute-dsl) | 39.552 | 1.396x | 1.005x |
| GB300 | 32 | 1 | 1 | 131072 | uniform + sinks | 32 -> 64 | 55.472 |
50.752 (trtllm-gen) | 40.080 | 1.384x | 1.266x |
| GB300 | 32 | 1 | 1 | 131072 | varied | 32 -> 64 | 36.816 | 28.752
(cute-dsl) | 28.960 | 1.271x | 0.993x |
| GB300 | 32 | 1 | 1 | 131104 | uniform | 32 -> 61 | 56.752 | 39.600
(cute-dsl) | 40.816 | 1.390x | 0.970x |
| GB300 | 32 | 1 | 1 | 131104 | varied | 32 -> 61 | 39.872 | 30.656
(cute-dsl) | 30.848 | 1.293x | 0.994x |
| GB300 | 32 | 1 | 1 | 196608 | uniform | 32 -> 64 | 77.584 | 52.368
(cute-dsl) | 53.312 | 1.455x | 0.982x |
| GB300 | 32 | 1 | 1 | 196608 | varied | 32 -> 64 | 65.088 | 44.256
(cute-dsl) | 46.416 | 1.402x | 0.953x |
| GB300 | 32 | 1 | 1 | 262144 | short | 32 -> 64 | 25.456 | 22.624
(cute-dsl) | 22.048 | 1.155x | 1.026x |
| GB300 | 32 | 1 | 1 | 262144 | uniform | 32 -> 64 | 99.696 | 63.912
(cute-dsl) | 66.880 | 1.491x | 0.956x |
| GB300 | 32 | 1 | 1 | 262144 | varied | 32 -> 64 | 70.848 | 48.400
(cute-dsl) | 49.760 | 1.424x | 0.973x |
| GB300 | 64 | 1 | 1 | 131072 | short | 32 -> 64 | 19.456 | 19.024
(cute-dsl) | 18.496 | 1.052x | 1.029x |
| GB300 | 64 | 1 | 1 | 131072 | uniform | 32 -> 64 | 53.728 | 39.376
(cute-dsl) | 39.648 | 1.355x | 0.993x |
| GB300 | 64 | 1 | 1 | 131072 | varied | 32 -> 64 | 44.176 | 33.424
(cute-dsl) | 34.080 | 1.296x | 0.981x |
| GB300 | 64 | 1 | 1 | 131136 | uniform | 32 -> 61 | 55.072 | 39.328
(cute-dsl) | 40.048 | 1.375x | 0.982x |
| GB300 | 64 | 1 | 1 | 131136 | varied | 32 -> 61 | 44.048 | 33.104
(cute-dsl) | 33.488 | 1.315x | 0.989x |
| GB300 | 64 | 1 | 1 | 196608 | uniform | 32 -> 64 | 75.040 | 51.280
(cute-dsl) | 52.272 | 1.436x | 0.981x |
| GB300 | 64 | 1 | 1 | 196608 | varied | 32 -> 64 | 64.576 | 44.176
(cute-dsl) | 45.824 | 1.409x | 0.964x |
| GB300 | 64 | 1 | 1 | 262144 | short | 32 -> 64 | 25.232 | 22.672
(cute-dsl) | 22.240 | 1.135x | 1.019x |
| GB300 | 64 | 1 | 1 | 262144 | uniform | 32 -> 64 | 96.256 | 62.208
(cute-dsl) | 64.912 | 1.483x | 0.958x |
| GB300 | 64 | 1 | 1 | 262144 | varied | 32 -> 64 | 93.680 | 62.544
(cute-dsl) | 63.872 | 1.467x | 0.979x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Improved BF16 split-KV attention support for long sequences on
supported Blackwell GPUs. Eligible workloads can now use up to 64
splits, compared with the existing limit of 32 for other workloads.
* Added additional optimized configurations for selected batch sizes,
query lengths, and sequence lengths.
* **Bug Fixes**
* Improved handling of split-KV results, including optional sink values
and padded rows.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4843
- **最后更新**: 2026-11-23T01:34:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34967
- **最后更新**: 2026-11-23T01:18:28Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

## huggingface/diffusers 昨日提交分析（第 1/1 批）

### 1. 主要更新类型
本次提交属于**文档更新（docs）**，具体为修复自动文档字符串（autodocstring）的布局问题，不涉及核心功能或代码逻辑变更。

### 2. 关键变更点及其与项目整体方向的关系

- **核心变更**：修复了 modular diffusers 中组件（components）的自动文档字符串排版问题，并将该修复同步传播到相关配置文件（configs）中。
- **与项目方向的关联**：diffusers 作为 HuggingFace 生态中扩散模型的核心库，其 modular 架构是近年来推动组件化、模块化设计的重要方向。自动文档字符串直接影响开发者对 API 的理解效率，此次修复体现了团队对**开发者体验（DX）**的持续重视，与项目"降低使用门槛、提高文档质量"的整体方向一致。

### 3. 对项目的影响和潜在意义

- **直接影响有限**：作为纯文档修复，不改变任何运行时行为或 API 接口，对现有用户的代码无兼容性影响。
- **间接影响积极**：良好的文档排版有助于开发者更快速理解 modular 架构中各组件的参数、返回值和使用方式，降低上手难度，提升社区贡献和采用率。
- **传播到 configs 的细节值得注意**：说明修复不仅停留在单一页面，而是系统性地检查了所有相关文档生成路径，体现了团队在文档质量上的严谨态度。

### 4. 值得关注的技术点

- **自动文档字符串生成（autodocstring）**：项目采用了自动生成文档的机制，这类机制在组件数量庞大时容易出现排版问题（如参数列表对齐、类型标注显示等），需要定期维护。
- **modular diffusers 架构**：modular 设计意味着组件被拆分为独立模块，每个模块都有各自的文档字符串，布局一致性维护的复杂度更高，此次修复暗示该机制在大规模组件场景下仍存在边界情况需要持续迭代。
- **PR 编号 #15359**：从编号可以看出该仓库提交频率非常高，文档维护是日常开发中的常规工作之一。

### 5. 基于README的项目背景与影响分析

从README摘要可见，项目采用 Apache 2.0 开源协议，由 HuggingFace 团队主导，定位为开放的扩散模型工具库。基于此背景：

- 此次提交虽然体量小，但反映了 HuggingFace 团队对**开源项目成熟度**的关注——当项目达到一定规模后，文档质量往往比新功能更能决定社区留存率。
- 在扩散模型领域竞争激烈的当下，diffusers 通过持续打磨 modular 架构的文档体验，有助于巩固其作为**事实标准工具库**的地位，吸引更多开发者从 PyTorch 原生实现迁移到 diffusers 框架。
- 这类"小而频繁"的文档修复提交，也体现了团队采用的**持续集成和持续改进**的开发流程，对项目长期健康发展具有积极意义。

## 详细提交记录

### [750b3be](https://github.com/huggingface/diffusers/commit/750b3be2c0198e194c87e931a6904066de167a5f)

- **作者**: Sayak Paul
- **时间**: 2026-11-22T10:31:43Z
- **提交信息**: docs: fix autodocstring layout for components in modular diffusers. (#15359)

* docs: fix autodocstring layout for components in modular diffusers.

* propagate to configs.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-11-12T08:10:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13429
- **最后更新**: 2026-11-23T02:30:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38949
- **最后更新**: 2026-11-23T02:44:11Z

## 提交统计

- **昨日提交总数**: 54
- **提交者数量**: 28
- **主要提交者**: Liangsheng Yin, Ruilin Gao, Banruo Liu

## AI分析总结

## 1. 主要更新类型

- **性能优化（Perf）**：约 20 条，占比最高，集中在 diffusion（视频/图像生成）和 speculative decoding（投机采样）。
- **重构（Refactor）**：约 12 条，以 sampling 管线和 speculative verify 为主。
- **Bug 修复（Fix）**：约 14 条，覆盖 kernels、LoRA、hicache、AMD 平台、constrained decoding 等。
- **功能新增（Feat）**：少量，如 MiniMax-H3 双变体服务、GLM5 序列并行、PD 分离 Transport 抽象、外部模型 MLA 缓存、请求看门狗。
- **CI/测试**：若干，用于平台配置校验与单测稳定性。

## 2. 关键变更点及与项目方向的关系

- **Diffusion 子系统是本次提交的绝对重心**（约 25 条）：围绕 MiniMax-H3 视频/音频模型的性能打磨（VAE 解码加速、cuDNN attention 预热、Triton kernel replay、音频与视频并行解码），以及 LoRA 加载/合并的正确性修复。这表明 SGLang 正将多模态视频生成推理作为核心扩展方向。
- **Sampling 管线大重构**：将种子构建、watermark、grammar mask、采样参数等逐步改为"每步构建 + 有序流水线阶段"，替代旧的 SamplingBatchInfo filter/merge。同时修复了 filler 种子的安全 RNG 问题。这是为投机采样等更复杂场景做架构铺垫。
- **Speculative decoding 统一化**：EAGLE、NGRAM、DSpark、DFlash 共享同一套 verify logits 调整阶段、ring buffer 和 accept/commit 接口，降低重复实现，提升可维护性。
- **hicache 与 PD 分离**：write_back 驱逐改为 forward 流 fence 而非阻塞调度器；MooncakeTransport 抽象到统一 Transport 接口，服务 prefill-decode 分离架构。
- **AMD/ROCm 支持持续投入**：MiniMax-H3 在 gfx950 上的 VAE 解码加速、AITER topk 修复、mxfp8-moe 简化等，体现跨平台兼容性是长期目标。

## 3. 对项目的影响和潜在意义

- 视频生成推理的吞吐和稳定性显著提升，配合请求看门狗与 /health 503 机制，生产可用性增强。
- Sampling 与 speculative 的重构减少了技术债，未来引入新算法的成本更低。
- Transport 抽象和 MLA 缓存开放给外部模型，提升了框架的可扩展性。
- 大量 Fix 提交（零 token kernel guard、int64 偏移、EOS 语法终止等）修复了边界条件隐患，降低线上崩溃风险。

## 4. 值得关注的技术点

- **Triton kernel "replay launches"**：请求路径不再重编译，是 GPU 推理低延迟的关键手法。
- **Ulysses pipeline pool 带余量增长**：首个采样后保留并扩容，避免重复分配开销。
- **安全 RNG 每请求独立种子**：采样可复现性与安全性兼顾。
- **Concurrent DiT shard header 读取**：远程模型加载并行化，缩短冷启动。
- **Custom-all-reduce 每 peer 仅映射一次 graph-input 分配**：降低通信注册开销。

## 5. 基于 README 的项目发展影响

README 明确 SGLang 定位为"LLM 与多模态模型的快速推理框架"。本次提交表明项目正**双线推进**：一是以 diffusion 视频生成（MiniMax-H3、Wan、LTX、Qwen-Image 等）补齐多模态推理版图，并持续做极致性能优化；二是夯实核心 LLM 推理栈（sampling 管线、投机解码、hicache、PD 分离）的架构质量。二者共同强化了 SGLang"快"这一核心卖点——既提升模型覆盖广度，又通过重构和内核级优化降低延迟、提高吞吐，巩固其作为高性能推理基础设施的地位。

## 详细提交记录

### [1918da6](https://github.com/sgl-project/sglang/commit/1918da6349f9be1c62315503e1a7458a3957bc5f)

- **作者**: swh
- **时间**: 2026-11-22T18:40:32Z
- **提交信息**: [CI] diffusion: Fake the platform in the MiniMax-H3 video config (#51734)

Co-authored-by: Claude <noreply@anthropic.com>

### [3deaf8e](https://github.com/sgl-project/sglang/commit/3deaf8ea6d63a1ba7572572d7f81f3b0680c40e4)

- **作者**: Mick
- **时间**: 2026-11-22T18:39:41Z
- **提交信息**: [Feat] diffusion: Serve MiniMax-H3 fl2va and ref2va from one server (--model-variant fl2va+ref2va) (#52023)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [14ae584](https://github.com/sgl-project/sglang/commit/14ae5841d6f37f8976861c38813f347d1745f09c)

- **作者**: Mick
- **时间**: 2026-11-22T18:38:52Z
- **提交信息**: [CI] [AMD] diffusion: Check the CUDA partition plan against its own registry (#52216)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [4423b6b](https://github.com/sgl-project/sglang/commit/4423b6b3b3a9fc68fb3ab7becf21233b9d7891f4)

- **作者**: Mick
- **时间**: 2026-11-22T18:38:31Z
- **提交信息**: [Perf] diffusion: No request-path recompiles of the VSA-H3 kernels and the exact scaled residual add (#52224)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2e11d75](https://github.com/sgl-project/sglang/commit/2e11d753d552d99ab48daa6f600b5abf444695ce)

- **作者**: Mick
- **时间**: 2026-11-22T18:37:58Z
- **提交信息**: [Perf] diffusion: Build MiniMax-H3's vision-tower cuDNN attention kernels in the warm-up (#52225)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [de41ccf](https://github.com/sgl-project/sglang/commit/de41ccfae097c629a3928150b1f7139e33dfd183)

- **作者**: weireweire
- **时间**: 2026-11-22T16:46:53Z
- **提交信息**: [Perf] hicache: Fence write_back eviction copies on the forward stream instead of blocking the scheduler (#50469)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [cb33792](https://github.com/sgl-project/sglang/commit/cb337923d576f48a4accba439af9cfbc9b720a2c)

- **作者**: Chen Cheng
- **时间**: 2026-11-22T14:28:55Z
- **提交信息**: [Feat] glm5_next: Support LayerNorm sequence parallelism (#50906)

### [65123c0](https://github.com/sgl-project/sglang/commit/65123c04311c9e83f8c36e775a46c0bede6ec6ac)

- **作者**: Ruilin Gao
- **时间**: 2026-11-22T14:28:30Z
- **提交信息**: [Perf] diffusion/ltx-2.3: Reuse the cond pass's prefix blocks for the STG pass (#51999)

### [4c4d3b9](https://github.com/sgl-project/sglang/commit/4c4d3b9ce39668bfb82ba7a3b2e9d2b2a51928dc)

- **作者**: 黄云龙
- **时间**: 2026-11-22T14:28:05Z
- **提交信息**: [Perf] diffusion: replay launches for six more hot Triton wrappers (#52220)

### [77376b2](https://github.com/sgl-project/sglang/commit/77376b2553c72b9e208b7bc3fdecff0f8ce4c39e)

- **作者**: Marina Ma
- **时间**: 2026-11-22T14:27:41Z
- **提交信息**: [Fix] diffusion/lora: Snapshot the offloaded weight when committing a merged LoRA as the base (#52226)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d342b19](https://github.com/sgl-project/sglang/commit/d342b19980fca25380570017650317ca5901b29f)

- **作者**: leon
- **时间**: 2026-11-22T14:27:34Z
- **提交信息**: [Fix] kernels: Guard zero-token launch in grouped_gemma_rmsnorm (#52074)

### [b2ce7f8](https://github.com/sgl-project/sglang/commit/b2ce7f8811bc40fd0d67000030c22edbbe0f2a37)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-11-22T13:11:19Z
- **提交信息**: [Perf] speculative: Fill the DSA MTP draft's prefill KV cache without attention for all but the last token (#46784)

### [b34a52f](https://github.com/sgl-project/sglang/commit/b34a52fcb87a0d1c1190d16e0b5b3c4f867f591f)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T11:53:50Z
- **提交信息**: [Fix] sampling: Draw filler seeds per request with a secure RNG (#52277)

### [779d4a7](https://github.com/sgl-project/sglang/commit/779d4a7bb24ecb8fb194ba00ffa4ff55ab14de28)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T11:43:54Z
- **提交信息**: [Refactor] sampling: Build seeds and sampling-mask rows per step; drop SamplingBatchInfo filter/merge (#52270)

### [5529971](https://github.com/sgl-project/sglang/commit/55299713c24672673f0f0efd35fe974da0e57da6)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T11:35:15Z
- **提交信息**: [Refactor] sampling: Apply the grammar mask as a pipeline stage (#52192)

### [9135507](https://github.com/sgl-project/sglang/commit/9135507c1ce66386d86db3061a7aae2f042a555f)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T11:10:35Z
- **提交信息**: [Refactor] speculative: Share one verify logits-adjust stage across EAGLE, NGRAM, DSpark and DFlash (#52184)

### [2417313](https://github.com/sgl-project/sglang/commit/2417313dfa84ed3e8014804809e34ed5cfdfeb31)

- **作者**: Nan Jiang
- **时间**: 2026-11-22T11:09:10Z
- **提交信息**: [Fix] openai: Decide byte-level BPE from a fast tokenizer's declared decoder (#49982)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [a3a326a](https://github.com/sgl-project/sglang/commit/a3a326ad77a96e0d19228ce68f64dddff8d961b6)

- **作者**: Karthik Venugopal
- **时间**: 2026-11-22T11:07:55Z
- **提交信息**: [Feat] model_config: Allow external models to opt into MLA caching (#48746)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ea27df6](https://github.com/sgl-project/sglang/commit/ea27df605a8192ab504bc66258c3205aca9c45b6)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T10:22:24Z
- **提交信息**: [Test] disaggregation: Give the non-last PP stage boundary test a Mooncake transport (#52283)

### [1bad592](https://github.com/sgl-project/sglang/commit/1bad592d4c02bbe8fac1d223081ba367e5bd8ca8)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T10:09:53Z
- **提交信息**: [Refactor] sampling: Run sampling-stage adjustments through one ordered pipeline (#52185)

### [3117f58](https://github.com/sgl-project/sglang/commit/3117f5801752bfd8ea9aee8d3ba3dff8562378fd)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T09:53:38Z
- **提交信息**: [Refactor] sampling: Build sampler params per step (#52170)

### [d52a90a](https://github.com/sgl-project/sglang/commit/d52a90a497ab6b08887ffcf891e86156d135ff5a)

- **作者**: Banruo Liu
- **时间**: 2026-11-22T09:43:05Z
- **提交信息**: [Feat] pd: Extract MooncakeTransport behind a common Transport interface (#46460)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: GPT-6 Astra <noreply@openai.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [a7ac526](https://github.com/sgl-project/sglang/commit/a7ac5261eb803cf75d8e73f8b2c0c6ae0ed1886a)

- **作者**: Ruilin Gao
- **时间**: 2026-11-22T09:40:30Z
- **提交信息**: [Fix] diffusion: Map Wan2.1 I2V image-branch LoRA keys (k_img/v_img) (#51425)

### [dd6cb65](https://github.com/sgl-project/sglang/commit/dd6cb65b8fe95a1f5b377df5de2542700c582238)

- **作者**: Yuedong Wu
- **时间**: 2026-11-22T09:40:11Z
- **提交信息**: [Refactor] [AMD] mxfp8-moe: Remove redundant output zero-fill (#51170)

Signed-off-by: Yuedong Wu <dwcn22@outlook.com>

### [4cbe4cb](https://github.com/sgl-project/sglang/commit/4cbe4cbf43ebcaa87984066db04c44e2f6a4e2d5)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-22T08:16:10Z
- **提交信息**: [Fix] diffusion: Rebuild the Qwen2.5-VL vision RoPE table on the GPU so Qwen-Image-Edit gives the same image with the encoder offloaded (#51187)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [d40fb11](https://github.com/sgl-project/sglang/commit/d40fb11e71396e11440d695b2b72355099edb67f)

- **作者**: xiaoke12345678
- **时间**: 2026-11-22T08:15:46Z
- **提交信息**: [Fix] kernels/lora: Use int64 token row offsets in the csgmv shrink and expand kernels (#51199)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [1081898](https://github.com/sgl-project/sglang/commit/1081898d3e43cafd0ea2273fdb478edf95864d93)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-22T08:15:21Z
- **提交信息**: [Fix] diffusion/nomas: Run each requested video of a /v1/videos job as its own sample (#51753)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [c0bdbb3](https://github.com/sgl-project/sglang/commit/c0bdbb306b2c60557e2516b0d419eb293544a494)

- **作者**: Aaravos
- **时间**: 2026-11-22T08:14:39Z
- **提交信息**: [Fix] mamba: Use the intermediate state buffer stride during Triton verify (#51164)

### [a8f850a](https://github.com/sgl-project/sglang/commit/a8f850a9657e8c5437fd4b1c50d837762cf18bf7)

- **作者**: ankitgala007
- **时间**: 2026-11-22T08:14:14Z
- **提交信息**: [Fix] moe/tuning: Tune NemotronH's non-gated relu2 MoE with its real shape (#51632)

Co-authored-by: Ankit Gala <204639277+ankitgala007@users.noreply.github.com>

### [3433d31](https://github.com/sgl-project/sglang/commit/3433d3197bd78b15af09685e0062526024e176d6)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-22T08:13:32Z
- **提交信息**: [Fix] [AMD] aiter: Read the KV layout of the pool wrapped by HybridLinearKVPool (#51221)

### [1ed22fd](https://github.com/sgl-project/sglang/commit/1ed22fdb695bbaf40338ca8b571a2cce31f8d1bf)

- **作者**: almaslof
- **时间**: 2026-11-22T08:13:07Z
- **提交信息**: [Fix] [AMD] moe/topk: stop AITER rejecting apply_routed_scaling_factor_on_output (#50779)

Co-authored-by: Claude <noreply@anthropic.com>

### [e580411](https://github.com/sgl-project/sglang/commit/e5804110daed5bc1861bbddb6a4d1b1afc9a1d70)

- **作者**: labAxiaoming
- **时间**: 2026-11-22T08:13:00Z
- **提交信息**: [Perf] diffusion: Avoid boolean indexing in placeholder validation (#50979)

### [73ee961](https://github.com/sgl-project/sglang/commit/73ee961c9e41cad6d49609ebe561edb86ce200da)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T08:11:53Z
- **提交信息**: [Refactor] speculative: One target-verify ring for EAGLE, NGRAM and DSpark (#52174)

### [83b892e](https://github.com/sgl-project/sglang/commit/83b892e4146cf9c5cc39ca68441cd490e7450900)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T07:59:59Z
- **提交信息**: [Refactor] speculative: Describe verify accepts with VerifyAccept and commit them in one call (#52164)

### [9066ceb](https://github.com/sgl-project/sglang/commit/9066ceb87912295d4a1210e43b25e3a42461f737)

- **作者**: Kevin Mi
- **时间**: 2026-11-22T07:54:17Z
- **提交信息**: [Fix] diffusion: Preserve mapped component weights during low-memory offload (#36727)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [2052fb1](https://github.com/sgl-project/sglang/commit/2052fb1d3273fc056dae39af4509d15f352f8c28)

- **作者**: OnePunchMonk
- **时间**: 2026-11-22T07:46:52Z
- **提交信息**: [Perf] diffusion/lingbot-video-moe: compute timestep modulation once per sample (#46872)

### [6654688](https://github.com/sgl-project/sglang/commit/66546883095bc4bb3a84f90fa94de6c7884658ab)

- **作者**: Mick
- **时间**: 2026-11-22T07:46:10Z
- **提交信息**: [Feat] diffusion: Request watchdog and /health 503 when a request runs past its limit (#52012)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [35cb644](https://github.com/sgl-project/sglang/commit/35cb64443002f7f5479616adc74faf56ec859fc3)

- **作者**: Mick
- **时间**: 2026-11-22T07:45:35Z
- **提交信息**: [Perf] diffusion/registry: Skip native discovery for metadata-only lookups (#52218)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [9de5f37](https://github.com/sgl-project/sglang/commit/9de5f373b1d00e96b85ed344ead890b9167fed4c)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T07:41:14Z
- **提交信息**: [Refactor] speculative: One definition of logit adjustments and truncated sampling for verify gates (#52159)

### [7df7c09](https://github.com/sgl-project/sglang/commit/7df7c0972f91bef535692da7acb1cf05e828ed0e)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-22T07:26:44Z
- **提交信息**: [Refactor] sampling: Build watermark rows per step (#52158)

### [448764d](https://github.com/sgl-project/sglang/commit/448764da636a8500015f461afbb91e3d2d23c94f)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-11-22T04:59:59Z
- **提交信息**: [Fix] glm5_next: Gather DFlash aux hidden states for every scattered MoE all-to-all backend (#47047)

### [46377d7](https://github.com/sgl-project/sglang/commit/46377d7e415d2775a1344e14398172c1d7c30b4b)

- **作者**: Adarsh Shirawalmath
- **时间**: 2026-11-22T04:55:05Z
- **提交信息**: [Test] transformers: Fix three unit tests that fail on transformers main (#52118)

### [c923890](https://github.com/sgl-project/sglang/commit/c923890becc5477e5e24bbd639d9c83daad7ad04)

- **作者**: Mick
- **时间**: 2026-11-22T04:52:58Z
- **提交信息**: [Perf] diffusion/loader: Read remote DiT shard headers concurrently (#52183)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6902829](https://github.com/sgl-project/sglang/commit/690282901a400d90da4b8b46fd7edfdc2bbbbbe3)

- **作者**: Shuwen Wang
- **时间**: 2026-11-22T04:39:22Z
- **提交信息**: [Fix] cuda-graph: Initialize Breakable backend flag in prefill test fixture (#52214)

### [2f1d12f](https://github.com/sgl-project/sglang/commit/2f1d12f842677256be372460e92c591edbf8aceb)

- **作者**: Vladimir Serov
- **时间**: 2026-11-22T04:28:39Z
- **提交信息**: [Refactor] diffusion/LoRA: Rework linear and LoRA linear common part (#37460)

### [7a477eb](https://github.com/sgl-project/sglang/commit/7a477ebe3aab03921c84d8c6a9cc1dd5d7bcefcb)

- **作者**: metamergebot
- **时间**: 2026-11-22T04:24:27Z
- **提交信息**: [Perf] custom-all-reduce: Map each peer graph-input allocation once at registration (#52173)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: houseroad <houseroad@users.noreply.github.com>

### [450fb9d](https://github.com/sgl-project/sglang/commit/450fb9da3319a980e4f2a89531dda6cb973390c4)

- **作者**: metamergebot
- **时间**: 2026-11-22T02:28:43Z
- **提交信息**: [Fix] constrained: Let llguidance accept an EOS id the grammar itself ends on (#52180)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: luccafong <luccafong@users.noreply.github.com>

### [aa773f3](https://github.com/sgl-project/sglang/commit/aa773f3f56aca6ae5f3b5490c8e8e94d666aeece)

- **作者**: metamergebot
- **时间**: 2026-11-22T02:28:24Z
- **提交信息**: [Perf] rust-server: Let a full request-log buffer drop lines instead of stalling workers (#52171)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [7e62e83](https://github.com/sgl-project/sglang/commit/7e62e8361211a3e04deb7fa6bbb31d9a58778701)

- **作者**: Tri Dao
- **时间**: 2026-11-22T01:53:11Z
- **提交信息**: [Fix] hicache: Sample the explicit-size host budget once before any local rank pins (#52120)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4916e5a](https://github.com/sgl-project/sglang/commit/4916e5a56ab0e2c90d9065cd6116091a79f28f55)

- **作者**: Ruilin Gao
- **时间**: 2026-11-22T00:48:35Z
- **提交信息**: [Fix] diffusion: Load diffusers-format LoRAs saved with a transformer. prefix (#51451)

### [4e7a4ff](https://github.com/sgl-project/sglang/commit/4e7a4ff3c85609e84a65cc846133baab05382622)

- **作者**: Mick
- **时间**: 2026-11-22T00:47:03Z
- **提交信息**: [Perf] [AMD] diffusion: Speed up the MiniMax-H3 video VAE decode on ROCm (gfx950) (#52027)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [fcb2c1f](https://github.com/sgl-project/sglang/commit/fcb2c1f47566fccb95d1a91dec649e41a3103756)

- **作者**: Mick
- **时间**: 2026-11-22T00:41:39Z
- **提交信息**: [Perf] diffusion: Keep the Ulysses pipeline pool through first-sight checks and grow it with headroom (#52001)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [f0f33bf](https://github.com/sgl-project/sglang/commit/f0f33bf3d4d570ca2a51b2634e8f9b6184627664)

- **作者**: Mick
- **时间**: 2026-11-22T00:40:24Z
- **提交信息**: [CI] diffusion: Isolate platform overrides in unit tests (#52039)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [15a4624](https://github.com/sgl-project/sglang/commit/15a4624b42404d9208a1d1925bf1622a2cc6697b)

- **作者**: Mick
- **时间**: 2026-11-22T00:39:55Z
- **提交信息**: [Perf] diffusion: Decode the MiniMax-H3 audio beside the video tiles (#52051)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-22T02:02:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97369
- **最后更新**: 2026-11-23T02:44:47Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 15
- **主要提交者**: Bugen Zhao, 李绍飞, Tony Lin

## AI分析总结

## vLLM 昨日提交分析（第1/1批，共18条）

### 1. 主要更新类型
- **Bug修复**（约7条）：多模态、KV Offload等
- **功能新增**（约6条）：新模型、新配方、Rust前端、解码策略
- **性能优化**（2条）：KV Offload与GEMM优化
- **文档/CI重构**（2条）

### 2. 关键变更点及与项目方向的关系
- **新模型支持**：Nemotron（文本/MTP/视觉语言三形态），延续vLLM"广泛模型覆盖"的定位。
- **Kimi-K3.1-Pro推理配方**：多条提交针对MI355X、B300、GB300等AMD/NVIDIA硬件的PD分离预设与DSpark草稿对齐，体现对生产级多硬件部署生态的持续投入。
- **投机解码（Spec Decode）**：DFlash/DFlash2新增anchor-first采样策略，呼应"fast serving"目标。
- **KV Offload**是本日热点：新增access_mode读写权限、修复ARC前缀保留、CPU层级超限存储、避免唤醒空闲worker——围绕长上下文/高并发场景的分层存储逐步成熟。
- **多模态健壮性**：视频帧上限、张量/NumPy输入兼容、OpenCUA kwargs透传，提升API易用性。
- **Rust前端**支持allowed_tools工具调用，面向Agent推理工作负载。

### 3. 对项目的影响与潜在意义
- KV Offload系列修复+新特性表明该模块正从实验走向生产可靠，可显著降低长序列推理的显存压力。
- 硬件相关配方的高频更新显示vLLM与芯片厂商（AMD/NVIDIA）的深度协同，强化其作为跨平台推理标准层的地位。
- 离线API错误分类、多模态输入宽容化降低集成门槛，利好下游应用。

### 4. 值得关注的技术点
- `sample_from_anchor`投机解码新范式对接受限采样的质量/延迟权衡。
- KV Offload的`access_mode`权限模型与ARC（前缀复用）交互，涉及缓存一致性的微妙设计。
- sm120（RTX 5090）小M GEMM优化，显示对消费级GPU推理的重视。
- 提交中大量Claude/Devin等AI辅助协作署名，反映AI驱动开发实践的常态化。

### 5. 对项目发展的总体影响
这些提交共同推进README所承诺的"Easy, fast, cheap"目标：新模型与硬件配方扩展"Easy"的覆盖面，投机解码与GEMM优化提升"fast"，KV Offload分层存储压低"cheap"的显存成本。多模态与Rust前端的打磨则增强生态兼容性，整体上vLLM正从单一推理引擎演化为覆盖多硬件、多模态、Agent场景的全栈LLM服务基础设施，日志中稳定的质量修复节奏也显示项目成熟度在持续提高。

## 详细提交记录

### [ef687f6](https://github.com/vllm-project/vllm/commit/ef687f6179b752c028767e610addbda67ed36d03)

- **作者**: seungrokj
- **时间**: 2026-11-22T21:11:50Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: MI355X kimi-k31-712d9eb image and released DSpark draft, align with InferenceX#5119 (#69163)

Signed-off-by: seungrokj <seungrok.jung@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0fa6668](https://github.com/vllm-project/vllm/commit/0fa666893b2989efc61dd25f7e915ef21d23cdd0)

- **作者**: danielafrimi
- **时间**: 2026-11-22T21:04:07Z
- **提交信息**: [Model] Add Nemotron Shortcut (text, MTP, vision-language) (#68198)

Signed-off-by: Daniel Afrimi <dafrimi@nvidia.com>
Co-authored-by: Netanel Haber <nhaber@nvidia.com>
Co-authored-by: Amit Zuker <azuker@nvidia.com>
Co-authored-by: Omer Ullman Argov <118735753+omera-nv@users.noreply.github.com>
Co-authored-by: Tomer Bar Natan <tbarnatan@nvidia.com>
Co-authored-by: Daniel Serebrenik <daserebrenik@nvidia.com>
Co-authored-by: Matthieu Le <matthieul@nvidia.com>
Co-authored-by: Roi Garnett <rgarnett@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0e3c8db](https://github.com/vllm-project/vllm/commit/0e3c8dbdae9d55149b0fba4e6c1014b4b08c9c73)

- **作者**: mispa-ms
- **时间**: 2026-11-22T16:25:31Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: B300 PD preset on kimi-k31-mc-f4c9618, align with InferenceX#5175 (#69264)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e2052f5](https://github.com/vllm-project/vllm/commit/e2052f5c7ad64564f00dd4592e77c27785c9333f)

- **作者**: Deepanker Kumeria
- **时间**: 2026-11-22T16:07:22Z
- **提交信息**: [Spec Decode] Support anchor-first (sample_from_anchor) DFlash/DFlash2 drafts (#68827)

Signed-off-by: Deepanker Kumeria <deepanker.kumeria@decagon.ai>
Co-authored-by: Yiliu Dong <91178480+qianlihuang@users.noreply.github.com>
Co-authored-by: Devin AI <158243242+devin-ai-integration[bot]@users.noreply.github.com>
Co-authored-by: Devin (Cognition AI) <devin-ai-integration[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [186882d](https://github.com/vllm-project/vllm/commit/186882d9e865ccfabc9f75146a708c4a68524c8e)

- **作者**: mispa-ms
- **时间**: 2026-11-22T15:54:49Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: move the GB300 AgentX presets to the released DSpark draft, align with InferenceX#5109 (#69182)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [118d12f](https://github.com/vllm-project/vllm/commit/118d12f728c4f0bff4f088eb197a1404a7302038)

- **作者**: aoshen02
- **时间**: 2026-11-22T14:47:32Z
- **提交信息**: [Doc] Reorganize docs/training/ into weight_updates and rollout_artifacts (#69248)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>

### [b976fff](https://github.com/vllm-project/vllm/commit/b976fff86af82c559b19aa676f52ea193eb0c188)

- **作者**: Paul Pak
- **时间**: 2026-11-22T13:23:08Z
- **提交信息**: [Bugfix] Apply the video processor frame caps when loading videos (#68802)

Signed-off-by: paulpak58 <52512091+paulpak58@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [17323e0](https://github.com/vllm-project/vllm/commit/17323e0b1ca54296cc3016b72d481ecffc17e69b)

- **作者**: waizuichougou
- **时间**: 2026-11-22T12:12:23Z
- **提交信息**: [Perf][KV Offload] Avoid waking idle FS workers on job completion (#68451)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e29c741](https://github.com/vllm-project/vllm/commit/e29c741da8d11e2ae7ba381bb78b6f703812cae1)

- **作者**: waizuichougou
- **时间**: 2026-11-22T10:17:11Z
- **提交信息**: [Bugfix][KV Offload] Preserve reused ARC prefixes during running-request eviction (#69110)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [443b51e](https://github.com/vllm-project/vllm/commit/443b51e52fad36bbbd7960fd272c8baf23f14dbb)

- **作者**: Bugen Zhao
- **时间**: 2026-11-22T09:03:28Z
- **提交信息**: [Rust Frontend] Support allowed_tools tool_choice (#68408)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9ae9c15](https://github.com/vllm-project/vllm/commit/9ae9c15c569176e52783dd2ef8f4fedf8aadc70a)

- **作者**: Effi Ofer
- **时间**: 2026-11-22T08:43:30Z
- **提交信息**: [KV Offload] Add access_mode (read|write|readwrite) (#67961)

Signed-off-by: Effi Ofer <effi.ofer@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cb19fed](https://github.com/vllm-project/vllm/commit/cb19fedd85f55e4c09ce76ab95b3a70fe4b5872a)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-22T08:33:57Z
- **提交信息**: [Bugfix][Multimodal] Pass image kwargs through the OpenCUA processor (#68317)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>

### [d4cc8ec](https://github.com/vllm-project/vllm/commit/d4cc8ec42efa7e1b41dfc5462d189004d5c5cb19)

- **作者**: 李绍飞
- **时间**: 2026-11-22T08:21:23Z
- **提交信息**: [Frontend] Classify errors in offline LLM APIs (#68667)

Signed-off-by: 李绍飞 <73046195+Remarkable911@users.noreply.github.com>

### [e72fc9a](https://github.com/vllm-project/vllm/commit/e72fc9ae50c221180c4b8f4a94c5009714a4b199)

- **作者**: wkngdrm
- **时间**: 2026-11-22T06:20:24Z
- **提交信息**: [Bugfix][KV Offload] Store the chunks that fit when a request exceeds the CPU tier (#66719)

Signed-off-by: Zerui Wu <zeruiwu@uw.edu>
Co-authored-by: Zerui Wu <zeruiwu@uw.edu>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [647a768](https://github.com/vllm-project/vllm/commit/647a76866b4559a74e27d1c6b55fbffe85c07ce4)

- **作者**: Yarikama
- **时间**: 2026-11-22T05:34:47Z
- **提交信息**: [Bugfix][Multimodal] Accept torch.Tensor videos in vLLM's own HF processors (#69052)

Signed-off-by: yarikama <amaki30226@gmail.com>

### [cb85c4e](https://github.com/vllm-project/vllm/commit/cb85c4e9efc27be9644bb90d8eed5fb521a77f44)

- **作者**: Yarikama
- **时间**: 2026-11-22T05:21:39Z
- **提交信息**: [Bugfix][Multimodal] Accept NumPy images and PIL frame videos in Muse Spark Open (#69099)

Signed-off-by: yarikama <amaki30226@gmail.com>

### [2e73822](https://github.com/vllm-project/vllm/commit/2e738227cb06edfc3a0325ff295dfda8a7d0d27b)

- **作者**: Tony Lin
- **时间**: 2026-11-22T04:35:29Z
- **提交信息**: [CI] Decouple LoRA layer tests from GLM model imports (#68867)

Signed-off-by: Tony Lin <tony.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [8c17e46](https://github.com/vllm-project/vllm/commit/8c17e4692a7cf393e3d1dacf6404fa4d48d993a1)

- **作者**: Thien Tran
- **时间**: 2026-11-22T00:09:51Z
- **提交信息**: [Perf][Inkling2-Mini] Improve small M GEMM on 5090 (sm120) (#69168)

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-23
**监控日期**: 2026-11-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7909
- **最后更新**: 2026-11-23T02:36:31Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 18
- **主要提交者**: lm10-arg, haic0, searlion

## AI分析总结

## vllm-omni 昨日提交分析（1/1批，27条）

### 1. 主要更新类型
- **Bug修复**：约 9 条，占比最高，集中在 TTS 模型与多模态调度
- **CI/Build 稳定性**：约 7 条，几乎全部针对 **ROCm（AMD GPU）** 平台
- **文档更新**：约 5 条（集成指南、部署配方、链接修复）
- **性能优化**：2 条（Cosmos3 批处理、Ulysses QKV 打包）
- **模型/重构**：2 条（MiniCPM-o 简化与 FP16 融合）
- **测试与基准**：2 条

### 2. 关键变更点及与项目方向的关系
项目定位为"人人可用的**易、快、便宜的全模态模型服务**"，提交与此高度一致：

- **多模型生态巩固**：涉及 Qwen3-Omni、MiniCPM-o 4.5、Breeze-TTS-2、Ming-TTS、GLM-TTS、MiMo-Audio、Cosmos3、Wan2.2、MiniMax-H3 等十余个模型，体现"omni-modality serving"的多模型承诺。
- **异步与全双工（full-duplex）语音链路修复**：异步分块延迟指标持久化、残差采样请求级隔离、语音克隆参考填充、启动阶段副本失败容错、优先级透传，均指向**长时流式/交互式语音服务的可靠性**。
- **硬件覆盖扩展**：ROCm 相关 CI 大量投入（AMD TTS 夜间认证、Wan2.2 设备后处理等价性、Qwen-Image 周覆盖、阻塞副本可靠性），配合 Nvidia ModelOpt FP8 支持，直接服务"cheap/fast"——多硬件降低成本。

### 3. 对项目的影响和潜在意义
- **稳定性优先**：大量 ROCm 定性/等价性测试表明项目正从 NVIDIA 单一生态向**异构硬件生产级**迈进，降低供应商锁定。
- **语音服务质量拐点**：TTFT/TTFP 锚点门控、张量指标修复使延迟诊断可追踪，利于 SLO 达标。
- **兼容性韧性**：允许 stage 副本提前退出、短参考填充，减少真实部署中的边缘失败。

### 4. 值得关注的技术点
- **Qwen3-Omni 残差采样的 request-local 化**：修复并发请求间状态污染，是多租户推理的典型隐患。
- **MiniCPM-o FP16 fused CFM 在 ROCm 的恢复与补全**：异构硬件上自定义融合算子的可移植性工作。
- **Ulysses packed QKV（opt-in）**：长序列上下文并行的显存/带宽优化。
- **Cosmos3 单去噪循环内批处理多图输出 + FP8 路由专家混合精度**：T2I 吞吐与成本的双优化。
- **Ming-TTS 说话人 embedding 复用**：内联参考场景下省去重复编码开销。

### 5. 对项目发展的影响
基于 README 的"易、快、便宜"目标：**Bug修复与 ROCm CI** 支撑"易"（跨平台开箱即用），**性能提交**（批处理、FP8、packed QKV）支撑"快/便宜"，**文档与集成 skill**（全双工集成指南、硬件配方）降低接入门槛。整体显示项目处于**多模态语音/图像模型的硬化与平台化阶段**——在拓宽模型广度的同时，通过指标可观测性、异构硬件验证和流式链路修复，向生产级全双工、多硬件服务能力收敛，为后续稳定发布与社区采用奠定基础。

## 详细提交记录

### [4dfc203](https://github.com/vllm-project/vllm-omni/commit/4dfc20301c7e4fc7baddcb1b1381646f55805029)

- **作者**: lm10-arg
- **时间**: 2026-11-22T23:23:52Z
- **提交信息**: [Bugfix][Metrics] Persist Qwen3-Omni async-chunk latency diagnostics (#10969)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [344667c](https://github.com/vllm-project/vllm-omni/commit/344667cb5f2b2df89a21455a8b44a68d19d54fa6)

- **作者**: lm10-arg
- **时间**: 2026-11-22T23:22:05Z
- **提交信息**: [CI/Build][ROCm] Stabilize AMD TTS nightly qualification (#10968)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [3c885f4](https://github.com/vllm-project/vllm-omni/commit/3c885f4348a3534728631a01bc6f30f016ea14b1)

- **作者**: He Yingxu
- **时间**: 2026-11-22T22:34:42Z
- **提交信息**: [Bugfix][Breeze-TTS-2] Pad short voice-clone references to the warmup length (#10965)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a4f1f6f](https://github.com/vllm-project/vllm-omni/commit/a4f1f6f80d34a7f03c46957debb7402a74b57246)

- **作者**: lm10-arg
- **时间**: 2026-11-22T21:28:15Z
- **提交信息**: [Bugfix] Make Qwen3-Omni residual sampling request-local (#10966)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [9f394a4](https://github.com/vllm-project/vllm-omni/commit/9f394a4661089f5ef4ccb04df850c1547a10de65)

- **作者**: lm10-arg
- **时间**: 2026-11-22T20:35:27Z
- **提交信息**: [Bugfix] Restore MiniCPM-o FP16 fused CFM on ROCm (#10963)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [23cf44d](https://github.com/vllm-project/vllm-omni/commit/23cf44de0e7e8e5a53f4d891904fe6c0eebf7149)

- **作者**: wuli666
- **时间**: 2026-11-22T20:03:10Z
- **提交信息**: [Doc] Add full-duplex model integration skill (#10940)

Signed-off-by: wuli666 <421774554@qq.com>

### [0737776](https://github.com/vllm-project/vllm-omni/commit/0737776e4d43de80d892d0e3b14283407db7aebc)

- **作者**: lm10-arg
- **时间**: 2026-11-22T19:32:03Z
- **提交信息**: [CI/Build][ROCm] Stabilize Wan2.2 device-postprocess equivalence (#10961)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [171edfa](https://github.com/vllm-project/vllm-omni/commit/171edfab956893b68cbe4ce660593e1d7a07e371)

- **作者**: lm10-arg
- **时间**: 2026-11-22T19:03:44Z
- **提交信息**: [CI/Build] Harden GLM-TTS weekly speech diagnostics (#10962)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [acda6ed](https://github.com/vllm-project/vllm-omni/commit/acda6ed6161b76b133c67f042d29d20c4ef924e0)

- **作者**: jeremylyn0001-sudo
- **时间**: 2026-11-22T18:35:19Z
- **提交信息**: [Bugfix] Allow startup to continue when a stage replica exits before READY (#10881)

Signed-off-by: jeremylyn0001-sudo <jeremylyn0001@gmail.com>

### [f602d02](https://github.com/vllm-project/vllm-omni/commit/f602d0295852c430434f8cd2cd87da287db1a96e)

- **作者**: Xuchen Wei
- **时间**: 2026-11-22T17:19:18Z
- **提交信息**: [Bugfix] Reuse Ming-TTS speaker embeddings for inline references (#9408)

Signed-off-by: Xuchen Wei <adrian.xc.wei@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [bed8b53](https://github.com/vllm-project/vllm-omni/commit/bed8b53c013e46896e1862f8e6825eccbe6dfd23)

- **作者**: searlion
- **时间**: 2026-11-22T15:33:05Z
- **提交信息**: [Perf][Cosmos3] Batch T2I num_outputs_per_prompt > 1 in one denoising loop (#10768)

Signed-off-by: Lewis Won <lewis.won@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [fced3d0](https://github.com/vllm-project/vllm-omni/commit/fced3d009d7a71c51b8229b81607e63c4fcc1dba)

- **作者**: amy-why-3459
- **时间**: 2026-11-22T15:29:25Z
- **提交信息**: [Model] Simplify MiniCPM-o 4.5 internals (#10461)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [711a720](https://github.com/vllm-project/vllm-omni/commit/711a720c9a347f4ba73f7b350c8122b99090aa4f)

- **作者**: haic0
- **时间**: 2026-11-22T13:15:49Z
- **提交信息**: [Core] Add opt-in packed QKV exchange for Ulysses (#10134)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>

### [3b28981](https://github.com/vllm-project/vllm-omni/commit/3b2898143c5616c4ee2a2b220a3f19dd4e5bbe13)

- **作者**: Dominik Farhan
- **时间**: 2026-11-22T13:08:38Z
- **提交信息**: [Model] Cosmos3: support ModelOpt FP8 routed experts in mixed-precision (MAPS) (#9813)

Signed-off-by: Dominik Farhan <dfarhan@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0a88347](https://github.com/vllm-project/vllm-omni/commit/0a883471e28351eade7a6fc4e4cc37a27eb81129)

- **作者**: Diao Shengjia
- **时间**: 2026-11-22T11:19:01Z
- **提交信息**: [Frontend] Add MiniMax-H3 control to ComfyUI (#7492)

Signed-off-by: GoDiao <diaoshengjia@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [5b764ae](https://github.com/vllm-project/vllm-omni/commit/5b764aea027be18e7b1723c84e1a2b7aa1bb8029)

- **作者**: HariD
- **时间**: 2026-11-22T07:07:14Z
- **提交信息**: [Doc] Add Wan2.2-TI2V-5B recipe for RTX PRO 4500 Blackwell 32GB (#10504)

Signed-off-by: Harikishan Desineni <hk.desineni@gmail.com>

### [c5505fe](https://github.com/vllm-project/vllm-omni/commit/c5505fe4cfaa6135709a7397ea1c7fb23809f633)

- **作者**: lm10-arg
- **时间**: 2026-11-22T06:41:00Z
- **提交信息**: [CI/Build][ROCm] Add Qwen-Image weekly functional coverage (#10922)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [3e11384](https://github.com/vllm-project/vllm-omni/commit/3e11384ffa4b9aab6a95ac0178e9a50ffb4d52a3)

- **作者**: chickeyton
- **时间**: 2026-11-22T06:34:54Z
- **提交信息**: [Test][MiniCPM-o] Gate the duplex server-side TTFT/TTFP anchor in e2e; restore plugin policy tests (#7872)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [eb31a80](https://github.com/vllm-project/vllm-omni/commit/eb31a805fc4d08008b03ce7b050655c00a935c6b)

- **作者**: NATURE
- **时间**: 2026-11-22T06:34:47Z
- **提交信息**: [Model] Complete MiniCPM-o 4.5 FP16 fused CFM dispatch (#9231)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [a02a736](https://github.com/vllm-project/vllm-omni/commit/a02a736fd49b2995258f1e7d29fbc8e39f389f4c)

- **作者**: fbqqz
- **时间**: 2026-11-22T06:34:38Z
- **提交信息**: [Bugfix] Forward priority from AsyncOmni.generate to stage 0 (#9919)

Signed-off-by: fbqqz <36816313+ProvenceLavanda@users.noreply.github.com>

### [bbfa63d](https://github.com/vllm-project/vllm-omni/commit/bbfa63d9e52226c5d65eeaf72ee9e882e01f8bbf)

- **作者**: Neal Shinoda
- **时间**: 2026-11-22T06:34:31Z
- **提交信息**: [Doc] Compare streaming TTS input and output semantics (#9611)

Signed-off-by: Neal Shinoda <35791603+JLU-Neal@users.noreply.github.com>

### [569f54e](https://github.com/vllm-project/vllm-omni/commit/569f54e121a98c0ed573660b26c35c9c26634bbb)

- **作者**: Genghong Hu
- **时间**: 2026-11-22T06:34:23Z
- **提交信息**: [Doc] Fix duplicate section numbering in profiling guide (#9506)

Signed-off-by: Genghong Hu <111997394+GodHu777777@users.noreply.github.com>

### [7e85380](https://github.com/vllm-project/vllm-omni/commit/7e85380055c7add72018f5be187fb78e75789726)

- **作者**: lm10-arg
- **时间**: 2026-11-22T04:18:29Z
- **提交信息**: [CI/Build][ROCm] Add blocking replica reliability weekly coverage (#10521)

Signed-off-by: lm10-arg <lm10-arg@users.noreply.github.com>
Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [882ef04](https://github.com/vllm-project/vllm-omni/commit/882ef044fcef38967bbb00e6fff7acac15fd5d4c)

- **作者**: Alexis Román
- **时间**: 2026-11-22T04:00:57Z
- **提交信息**: docs: align run_server.sh override defaults with the scripts (#9086)

Signed-off-by: Jose Alexis Roman Martinez <alexis_romtz@hotmail.com>

### [d586bef](https://github.com/vllm-project/vllm-omni/commit/d586bef6d8aaeeaf791fbab2f59a6108e20a37d9)

- **作者**: Alexis Román
- **时间**: 2026-11-22T04:00:50Z
- **提交信息**: docs: fix broken relative links to the serving API guides (#9096)

Signed-off-by: Jose Alexis Roman Martinez <alexis_romtz@hotmail.com>

### [0496a8c](https://github.com/vllm-project/vllm-omni/commit/0496a8cba18d3abfe0eb08ed7bc74e5ec4dd4684)

- **作者**: lm10-arg
- **时间**: 2026-11-22T03:28:23Z
- **提交信息**: [Bugfix][Model] Fix MiMo-Audio text-only prompt task (#10916)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [a36de50](https://github.com/vllm-project/vllm-omni/commit/a36de509e5813a9171dbb45425d9d48afc512926)

- **作者**: longtai
- **时间**: 2026-11-22T00:17:05Z
- **提交信息**: [Benchmark] Wire --print-stage to duplex benchmarks (#7025)

Signed-off-by: tigerwash <liaolongtai@gmail.com>

---
