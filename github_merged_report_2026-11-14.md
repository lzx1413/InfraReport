# GitHub Stars 合并报告 - 2026-11-14

**合并日期**: 2026-11-15
**监控日期**: 2026-11-14
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


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2293
- **最后更新**: 2026-11-13T17:01:36Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3005
- **最后更新**: 2026-11-14T16:19:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2335
- **最后更新**: 2026-11-13T06:03:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6926
- **最后更新**: 2026-11-14T21:00:28Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Yanqin Zhai, Mingyang Wang, Brian K. Ryu

## AI分析总结

# FlashInfer 昨日提交分析（第1/1批，共4条）

## 1. 主要更新类型
- **功能新增与扩展**：扩展注意力内核和MoE模型的硬件/数值支持。
- **性能优化**：优化内核调度路径，提升H100上的推理性能。
- **测试与CI修复**：解决测试基础设施和环境兼容问题。
- **Bug修复**：修复基准测试中的不兼容比较问题。
- **文档与基准测试更新**：增强基准测试的灵活性和准确性。

## 2. 关键变更点及其与项目整体方向的关系
- **H100非causal paged prefill支持cuDNN**：将H100上非causal paged attention从FA3扩展到cuDNN域，扩展了内核调度灵活性，直接提升FlashInfer作为高性能GPU推理内核的硬件适配能力。
- **MegaMoE batch-invariant支持多格式**：将MegaMoE从BF16扩展到NVFP4、MXFP4、MXFP8等更多数值格式，支持Blackwell和Rubin架构，增强了FlashInfer对现代硬件和量化技术的覆盖。
- **采样draw测试环境继承修复**：解决CI中编译环境不一致导致的测试失败，提高了测试可靠性和开发效率。
- **推测解码benchmark掩码兼容修复**：确保基准测试比较的是兼容的注意力掩码，提高了性能评估的准确性。
- **基准测试增强**：添加`--no-causal`选项和独立参考实现，使基准测试更全面。

这些变更与FlashInfer作为**高性能GPU推理内核**的核心方向高度一致，重点扩展硬件支持、数值格式和调度灵活性，以满足现代LLM推理对多样硬件和优化技术的需求。

## 3. 对项目的影响和潜在意义
- **硬件覆盖扩展**：新增H100和Blackwell/Rubin支持，扩大了FlashInfer在主流和下一代GPU上的适用范围。
- **性能提升潜力**：cuDNN调度和更多数值格式支持可能带来显著的推理速度和效率提升。
- **生产可用性增强**：修复CI问题和benchmark准确性问题，提高了项目稳定性和可信度。
- **开发者体验改善**：测试基础设施修复和基准测试灵活性增强，降低了开发和验证成本。

## 4. 值得关注的技术点
- **内核调度策略**：如何根据硬件能力和计算特征在FA2/FA3/cuDNN之间智能调度。
- **Batch-invariant技术**：确保相同输入在不同批处理大小下产生相同结果的技术，对推理一致性至关重要。
- **数值格式支持**：对MXFP4/MXFP8等新量化格式的支持，反映了对低精度推理趋势的跟进。
- **编译环境继承机制**：测试基础设施中环境继承的设计，避免了CI环境不一致问题。
- **注意力掩码兼容性**：确保不同注意力变体（causal/non-causal）在基准测试中的正确比较。

## 5. 基于README的项目背景对项目发展的影响
根据README，FlashInfer定位为**"高性能GPU推理内核"**，专注于提供最优的注意力内核和推理优化。昨日的提交显示：
- **持续硬件适配**：通过H100/Blackwell支持扩展，保持对前沿硬件的领先地位。
- **技术创新深化**：batch-invariant技术和多数值格式支持，展示了对推理优化核心技术的深入探索。
- **质量保障提升**：测试和CI修复表明项目在扩展功能的同时注重工程质量和可维护性。
- **基准测试严谨性**：增强的基准测试确保性能优化有可靠的评估基础。

这些提交整体推动FlashInfer在**硬件覆盖、数值支持、调度灵活性和工程质量**四个维度上持续发展，巩固其在高性能推理内核领域的竞争力，并为未来支持更多硬件架构和优化技术奠定基础。项目正朝着**更广泛硬件支持、更智能调度、更严谨评估**的方向稳步前进。

## 详细提交记录

### [9c50996](https://github.com/flashinfer-ai/flashinfer/commit/9c50996794564e1e3b2a4b0683e9aa2bcc528df8)

- **作者**: Yang Xu
- **时间**: 2026-11-14T02:15:39Z
- **提交信息**: feat(attention): admit H100 noncausal paged prefill to cuDNN (#9473)

<!-- .github/pull_request_template.md -->

## 📌 Description

Noncausal H100 D256 paged attention currently stays on FA3 even when it
falls inside the qualified cuDNN domain. Extend the existing BF16/FP16
admission to `causal=False`, scoring actual CPU Q/KV lengths as `Hq *
sum(q_i * kv_i)`. Causal attention keeps its triangular formula; both
use the existing `2**24` work floor.

Keep the existing H100 80GB HBM3 / 132-SM, HND/page16, geometry and
runtime guards. Short-query FA2 and low-work requests retain their
native providers, as do existing native CUDA-Graph captures. The change
uses the shared FE graph API, adds no device readback or engine forcing,
and leaves Blackwell admission causal-only.

Cover both masks, mask changes after capture, page-map changes, and
device-scale replay. Add `--no-causal` with a matching independent
reference to `benchmarks/bench_cudnn_wrapper_host.py`; the benchmark
remains causal by default. No public API signature changes.

Author measurements: NVIDIA H100 80GB HBM3 (132 SMs), official FE
1.32.3, **actually loaded cuDNN 9.24.0.43**, Torch 2.14.1+cu130; FROST
opt-in unset and native kernels precompiled. O-only warm whole-call
timing; compilation, plan, and first call are recorded separately and
excluded. Graph time uses CUDA-event replay; eager waits for completion;
host enqueue excludes synchronization. These metrics are not additive
and do not establish serving TTFT.

All 32 public CLI processes passed: two dtypes × four workload families
× two masks × two provider orders. The table includes every noncausal
family/dtype, including native controls, and takes the geometric mean of
both process orders. Hq/Hkv=32/8, D=256, HND, page16 throughout; times
are µs. Native is FA2 for Q64 and FA3 otherwise.

| Dtype | B/Q/KV | Auto provider | Graph native → auto | Completed eager
native → auto | Host native → auto |
|---|---|---|---:|---:|---:|
| bfloat16 | 1/128/8192 | cudnn | 271.38 → 206.94 | 274.21 → 209.62 |
21.21 → 36.79 |
| bfloat16 | 4/64/8192 | fa2 | 272.40 → 272.47 | 271.77 → 271.62 | 22.70
→ 24.42 |
| bfloat16 | 1/1024/1024 | cudnn | 83.80 → 68.76 | 85.50 → 70.97 | 20.21
→ 35.16 |
| bfloat16 | 1/128/1024 | fa3 | 38.89 → 38.90 | 40.65 → 40.73 | 16.84 →
19.14 |
| float16 | 1/128/8192 | cudnn | 271.57 → 210.07 | 274.24 → 212.92 |
21.86 → 37.58 |
| float16 | 4/64/8192 | fa2 | 276.96 → 277.37 | 278.66 → 278.67 | 22.53
→ 24.35 |
| float16 | 1/1024/1024 | cudnn | 83.18 → 69.20 | 84.72 → 71.36 | 20.06
→ 35.07 |
| float16 | 1/128/1024 | fa3 | 38.73 → 38.73 | 40.78 → 40.88 | 16.98 →
19.30 |

Reproduce the first row from a checkout of this PR with the versions
above (the command asserts the loaded backend version and selected
provider):

```bash
env -u CUDNN_FRONTEND_ENABLE_FROST_ENGINES python benchmarks/bench_cudnn_wrapper_host.py \
  --kind paged --batch 1 --q 128 --kv 8192 --qo-heads 32 --kv-heads 8 \
  --head-dim 256 --page-size 16 --layout HND --dtype bfloat16 --no-causal \
  --expected-backend-version 92400 --expect-auto-backend cudnn \
  --backends fa3 auto cudnn --output h100-noncausal.json
```

Use the other B/Q/KV and dtype values for the remaining rows; Q64 uses
`fa2` as its native backend and expects `auto=fa2`, and the low-work row
expects `auto=fa3`. Reverse `--backends` to `cudnn auto fa3` (or `fa2`)
for the second process order; use `--causal` for the paired controls.
Each process interleaves provider sampling across rounds.

In the separately frozen 640-case independent study, the predeclared 260
newly admitted cases improve geometric-mean graph time **1210.50 →
933.64 µs (1.297×)** and completed eager **1208.76 → 935.57 µs
(1.292×)**, with no >5% regression in both orders. The 240
existing-cuDNN and 140 native controls meet their original 99% ±1%
equivalence intervals. Host submission worsens **12.80 → 26.73 µs**. All
inputs and adverse outcomes were retained; this is validation-catalog
coverage, not production traffic coverage. See the provenance limitation
below.

## 🔍 Related Issues

Extends #9451 and #9453; preserves the cache fix in #9469.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_cudnn_paged_hopper_auto.py
tests/cpu/attention/test_paged_hopper_auto.py
tests/cpu/attention/test_wrapper_host_benchmark_order.py`
Author validation:

- 841 CPU attention tests pass on the exact publication head
`cdc694e5b433e4cf39722b4ccc84ed62d7cf25b6`; import path and backend
version checked, CUDA uninitialized.
- 120/120 H100 lifecycle tests pass, no skips, on attention source
`238936`. O and O+LSE, both masks, retained replay across replanning,
mutated page maps/data, work boundaries, and live GPU scales are
covered.
- The 640 independent numerical/lifecycle case records pass. A separate
untimed 160-case source audit passes; the failed original postcheck
remains disclosed below.
- All 32 public CLI processes pass sampled mathematical references,
whole-output provider checks, and poisoned graph replay within one ULP
before/after timing. All author GPU allocations are released.
- Benchmark companion: five parser checks, twelve independent reference
checks, nine CPU benchmark tests, and changed-file pre-commit hooks
pass.
- GPU attention source `238936`, benchmark-only `4f647`, and publication
head `cdc694` have identical relevant attention paths. The final merge
brings unrelated upstream GEMM changes; this source audit does not claim
whole-final-head GPU coverage. Exact published-head actual CI is
requested separately.

Pre-commit was run on the five changed files, as prescribed by
`AGENTS.md`; `--all-files` and hook installation are not claimed.


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

- Please inspect mask-specific paired-length scoring, native capture
retention, and feature/runtime rejection paths. This is FI plan-time
admission; FE graph-declaration ranking and kernel implementations are
unchanged.
- The final independent process completed all 160 measurements, then
failed because its postcheck incorrectly required unused FA2 libraries
in a FA3-only shard. The original failed receipt is retained, and its
process maps were not saved. Original hashed source/AOT artifacts and
JIT-disabled local-first loading support its provenance; a separate
**untimed** run of the same 160 cases passed all checks and saved the
actual used FA3/cuDNN library paths and hashes. No performance samples
were rerun, dropped, or re-gated. Do not read this as four clean
original process exits.
- All 32 public processes exited successfully but emitted nanobind
shutdown leak diagnostics. They are retained; this is not a leak-free or
sanitizer qualification.
- Higher host submission cost remains visible. This PR makes no
serving/TTFT claim and does not clear the separate held Blackwell FP16
or storage-domain extensions.
- Implementation, validation and this description were prepared with
OpenAI Codex assistance.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Supported H100 workloads can now use automatic cuDNN admission for
noncausal paged attention when they meet the workload threshold. Causal
attention remains supported, and noncausal calls continue to use native
backends on Blackwell.
* The cuDNN wrapper benchmark now supports selecting causal or noncausal
attention; decode benchmarks reject the noncausal setting.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5ced14a](https://github.com/flashinfer-ai/flashinfer/commit/5ced14a7a13264aa3694acb1ed7ba211c92abeae)

- **作者**: Yanqin Zhai
- **时间**: 2026-11-14T01:35:37Z
- **提交信息**: Yanqinz/megamoe bi variants autotune (#9454)

<!-- .github/pull_request_template.md -->

## 📌 Description

Extend MegaMoE batch-invariant support beyond BF16 to supported NVFP4,
MXFP4, MXFP4×MXFP8, MXFP8, W4A16 and W8A16 paths on Blackwell and Rubin.

- Add arithmetic fingerprints and Lean models for the supported
numerical recipes.
- Support numerical variants, compatible K-stage tiles and
same-fingerprint outer AutoConfig selection.
- Harden distributed preparation and cached-plan validation.
- Add focused e2e coverage for numerical correctness, batch/plan/graph
invariance, autotune replay and multi-GPU EP.

Validated correctness and performance on SM100, SM103 and SM107,
including single-GPU and EP2/EP4 correctness. Focused host/Lean checks
and pre-commit passed; GPU tests were not rerun after test
simplification and CI conflict resolution.

BI guarantees remain scoped to a fixed architecture and numerical
recipe; cross-architecture bitwise equality is not guaranteed.

Developed with AI assistance.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added opt-in batch-invariant MegaMoE support for BF16, NVFP4, MXFP4,
MXFP8, and A16 configurations, with configurable activation variants.
* Added quantized combine options, deferred outputs, and ordered
handling of invalid expert routes.
* Expanded automatic configuration and tuning support, including
additional supported K-stage choices and complete-forward selection.
* Added a manually triggered qualification workflow for supported
hardware.
* **Documentation**
* Expanded guidance on supported configurations, numerical behavior,
tuning, and qualification.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d852a25](https://github.com/flashinfer-ai/flashinfer/commit/d852a253f47d9b87689afca51741f2512d51608a)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-14T00:46:18Z
- **提交信息**: test(batch_invariant): the sampling draw suite's precompile workers inherit the compiler environment (#9430)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

A test-only fix for `tests/utils/test_batch_invariant_sampling_draw.py`
(#9365). Its session fixture precompiles the device tests' kernels on
worker processes; those workers hid the device and set `CUTE_DSL_ARCH` /
`FLASHINFER_CUDA_ARCH_LIST` explicitly, so a CI that validates the
compiler environment of every process against the one recorded at test
start refuses them (`compiler environment changed after tests started:
switches.CUTE_DSL_ARCH`), and every device test errors at setup through
the fixture.

The workers now inherit the test process's environment unchanged -- the
same visible device, the same `CUTE_DSL_ARCH` and
`FLASHINFER_CUDA_ARCH_LIST` -- so they compile exactly what the process
would, into its module directory. The pool is smaller by default (8
workers, each with its own CUDA context) and
`BI_DRAW_PRECOMPILE_WORKERS=0` disables it (the tests then compile
in-process; a persistent compile cache makes that cheap). The
device-free form remains as an explicit opt-in
(`BI_DRAW_PRECOMPILE_DEVICE_FREE=1`) for development hosts with many
cores. The IR pin's compile subprocess likewise inherits the environment
when a device is visible and targets it; without a device it is
device-free with the target from `BI_TEST_ARCH` as before. No kernel,
model or expectation changes.


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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Compilation checks now request intermediate-representation and PTX
output during compilation, while preserving the existing environment and
adjusting device and architecture settings when needed.
* Precompilation uses up to eight workers by default. Set the worker
count to zero to skip precompilation; workers otherwise inherit the
current environment, with an option to compile without a visible CUDA
device.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9895105](https://github.com/flashinfer-ai/flashinfer/commit/9895105523d39d6c71f3b746dc1af0d54d1a3f3d)

- **作者**: Mingyang Wang
- **时间**: 2026-11-14T00:33:57Z
- **提交信息**: fix: respect speculative masks in decode benchmark (#9296)

<!-- .github/pull_request_template.md -->

## 📌 Description

Full-mask speculative decode previously kept causal TRTLLM backends
eligible, allowing the benchmark to compare incompatible attention
masks. Exclude the trtllm-gen wrapper and SM10x native auto route before
setup, execution and reference selection; retain Prims-TS and supported
native XQA routes.

Remove every occurrence of an incompatible backend, including duplicates
produced by the deprecated native alias.

## 🔍 Related Issues

Fixes https://github.com/flashinfer-ai/flashinfer/issues/6852 (benchmark
scope). Public API mask rejection is deferred.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_decode.py
tests/attention/test_xqa_batch_decode.py`

Targeted validation (patch on base
`c730038a2ee43a0f3c068862cbc8455515b75962`):

- Scoped pre-commit checks passed for the benchmark source, which is
unchanged since that run. The all-files hook command and full repository
suite were not run.
- B100 SM100: 16 BF16/FP8 full/causal combinations at query lengths
1/2/4/8 and two deterministic fixtures passed independent FP32
references at unchanged tolerances. All 16 graph checks exactly matched
eager output.
- BF16 and FP8 CLI runs at the issue shape, including repeated causal
backends and the deprecated native alias, passed and retained Prims-TS.

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

The suggested CI targets cover retained Prims-TS and XQA mask behavior;
they do not exercise benchmark backend selection. Selection was
validated through the benchmark CLI and task-local checks. No CI trigger
has been posted. The branch has not been rebased onto the newer main, so
the recorded GPU results do not claim validation of that merge.

Public APIs, kernels and comparison tolerances are unchanged. Validation
used B100 SM100, not the issue's B300; non-SM10x eligibility was checked
during development; no new automated test file is included in this PR.
This is a correctness change with no performance claim. When exclusion
leaves only Prims-TS, the benchmark still performs its graph/eager
check; independent dense-reference correctness was verified separately
during validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Benchmark runs using full speculative-decode masks now exclude
backends that do not support the required masking behavior. On certain
GPU architectures, the automatically selected implementation is also
excluded when it uses causal masking.
* If no compatible backends remain, the benchmark reports the existing
empty-backend error.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4818
- **最后更新**: 2026-11-14T20:51:33Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 3
- **主要提交者**: Aryan Kumar, Yixing Wang, Junda Chen

## AI分析总结

## 一、主要更新类型

- **性能优化（主）**：#2015 系列四连发（1/4~4/4）+ Spark 后续优化，是当日提交的核心。
- **功能新增**：对外提供并宣传 FastH3、Omni、Pika H3 Flex 的 480p/768p、5–15 秒任务。
- **Bug 修复**：FP4 测试硬件门控、机器人评审整改、LoRA 权重回退修复。
- **内核开发**：融合 SwiGLU/NVFP4 GEMM 及 GB10 内核修复。

## 二、关键变更点与项目方向的关系

- **FastH3 成为新的产品主线**：README 展示的是 FastVideo 推理/训练框架，而本批提交几乎全部围绕 FastH3（H3 系列）展开，说明项目正在从通用视频生成框架向**自有模型家族 + 专用推理栈**延伸。
- **DGX Spark / GB10 部署目标明确**：提交 5–8 构成完整的 #2015 优化序列——从解码加载、内核、DiT 融合到双 Spark 序列并行重叠，形成端到端的**边缘/小型 GPU 部署链路**，与项目"快速、高效推理"的定位高度契合。
- **NVFP4/FP4 量化贯穿始终**：说明团队把**低精度量化**作为核心竞争力，正在打通训练侧（QAT）与推理侧（FP4 权重）的闭环。
- **对外服务与广告（#2085）**：任务规格（480p/768p、5–15s）的公开，意味着 FastH3 已进入可对外演示/商用阶段。

## 三、对项目的影响与潜在意义

- **性能与硬件适配双线推进**：在保持框架通用性的同时，针对 GB10/Spark 这类新兴硬件做深度定制，可显著降低高端硬件门槛，扩大用户群。
- **量化链路趋于稳定**：测试门控、LoRA 权重修复表明 FP4 路径正从"能跑"走向"可靠"，是量产化前的关键加固。
- **代码质量受社区约束**：出现"Address bot reviews"提交，说明项目已引入自动化评审流程，协作规范度提升。

## 四、值得关注的技术点

1. **序列并行 + 重叠通信**（#2105）：双 Spark 场景下的并行策略，是大模型推理的高阶优化手段。
2. **融合 SwiGLU/NVFP4 GEMM**（#2103）：算子级融合直接决定量化推理的吞吐上限。
3. **AdaLN 缓存与稠密 NVFP4 前缀**（#2107）：通过缓存与混合精度前缀实现"opt-in"式灵活优化，兼顾默认路径稳定性。
4. **sm_12x 门控**：体现了对 GPU 架构代际差异的精细化管理，避免 CI 虚假失败。
5. **AI 协作痕迹**：多条 perf 提交标注 Co-authored-by Claude Opus 5.5，反映该项目已深度采用 AI 辅助开发。

## 五、基于 README 背景对项目发展的影响

README 显示 FastVideo 是一个面向社区、提供文档/Cookbook/快速上手与周会的**开源视频生成框架**。本批提交表明：

- 项目正在**从"框架"向"框架 + 自研模型 + 硬件深度优化"三位一体**演进，FastH3/Omni/Pika H3 Flex 构成新的模型矩阵。
- 面向 DGX Spark 的优化路径，契合社区对**低成本、可本地运行**视频生成的需求，有望提升项目的落地性与传播度。
- 完整的 PR 编号链（#2015→#2105）、分阶段交付与自动化评审，显示团队**工程化与协作成熟度**明显提高，为后续持续迭代和对外服务（#2085）打下基础。

综上，这批提交标志着 FastVideo 在 FastH3 模型栈、NVFP4 量化与新型硬件部署三方面同步提速，是项目迈向产品化与生态扩展的关键节点。

## 详细提交记录

### [5ccbe87](https://github.com/hao-ai-lab/FastVideo/commit/5ccbe87cf8c5f517445f8372c768257fc8bd09e4)

- **作者**: Aryan Kumar
- **时间**: 2026-11-14T23:55:02Z
- **提交信息**: [feat]: Serve and advertise H3 tasks, 480p/768p and 5-15 s for FastH3, Omni and Pika H3 Flex (#2085)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [48eadb7](https://github.com/hao-ai-lab/FastVideo/commit/48eadb715ee32eda31479ddab3e9551b57e0eb9e)

- **作者**: Aryan Kumar
- **时间**: 2026-11-14T23:43:56Z
- **提交信息**: [bugfix] Gate H3 native FP4 tests to sm_12x, where attn_qat_infer is built (#2112)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [b4faeae](https://github.com/hao-ai-lab/FastVideo/commit/b4faeae9c60ada35d58208b66828a0de3629f476)

- **作者**: Junda Chen
- **时间**: 2026-11-14T05:13:48Z
- **提交信息**: [bugfix]: Address bot reviews on the FastH3 Spark stack (#2108)

### [37fc5de](https://github.com/hao-ai-lab/FastVideo/commit/37fc5de5158eb8778177d2598f91a50fff43c634)

- **作者**: Aryan Kumar
- **时间**: 2026-11-14T02:58:47Z
- **提交信息**: [perf]: FastH3 Spark follow-ups: AdaLN cache in recipes, opt-in dense NVFP4 Omni prefix (#2107)

Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

### [e57464a](https://github.com/hao-ai-lab/FastVideo/commit/e57464a063de617027a846df9f686225b1b6cdb5)

- **作者**: Junda Chen
- **时间**: 2026-11-14T02:21:13Z
- **提交信息**: [perf]: FastH3 two-Spark sequence-parallel overlap (4/4 of #2015) (#2105)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [48ca5a1](https://github.com/hao-ai-lab/FastVideo/commit/48ca5a19e5c5884c58ce81fae2fd96c0c9d7abb3)

- **作者**: Junda Chen
- **时间**: 2026-11-14T02:20:09Z
- **提交信息**: [perf]: FastH3 single-Spark DiT fusions (3/4 of #2015) (#2104)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [20ddcec](https://github.com/hao-ai-lab/FastVideo/commit/20ddcec978f2728c664a28cceeaef4fbad26457d)

- **作者**: Junda Chen
- **时间**: 2026-11-14T02:19:15Z
- **提交信息**: [kernel]: FastH3 fused SwiGLU/NVFP4 GEMM and GB10 kernel fixes (2/4 of #2015) (#2103)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9d75351](https://github.com/hao-ai-lab/FastVideo/commit/9d7535138ab958b10022e6b43c43f5663a65354a)

- **作者**: Junda Chen
- **时间**: 2026-11-14T02:18:08Z
- **提交信息**: [perf]: FastH3 decode and loading for DGX Spark (1/4 of #2015) (#2102)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8570302](https://github.com/hao-ai-lab/FastVideo/commit/857030285022025421274f6a3ad537c56097470d)

- **作者**: Yixing Wang
- **时间**: 2026-11-14T00:14:04Z
- **提交信息**: [bugfix] Restore CPU-backed NVFP4 weights for LoRA lifecycle updates (#2076)

Co-authored-by: Yixing Wang <269992774+leo2ultimate@users.noreply.github.com>
Co-authored-by: leo <yixingwang@YIXINGs-MacBook-Pro.local>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34919
- **最后更新**: 2026-11-14T22:40:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
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


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13367
- **最后更新**: 2026-11-14T07:30:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38878
- **最后更新**: 2026-11-15T00:28:55Z

## 提交统计

- **昨日提交总数**: 60
- **提交者数量**: 32
- **主要提交者**: Shubham Garg, Pinjie Xu, Michael

## AI分析总结

# SGLang 昨日提交分析（60 条）

## 1. 主要更新类型分布
- **性能优化**：约 14 条，占比最高
- **Bug 修复**：约 16 条
- **功能新增**：约 10 条
- **CI/测试**：约 12 条
- **重构、文档、依赖维护**：其余若干

## 2. 关键变更点与项目方向的关系
- **内存缓存与分层缓存（hicache/kvcache/radix-tree）** 是最活跃领域：Rust 树核心上的 Full/SWA 联合驱逐、MXFP8 KV 缓存、逻辑 KV dtype 键、HiCache 外部后端分片等，直接服务于 SGLang 高吞吐推理的核心目标。
- **Rust 服务器持续演进**：新增 HTTP/2 支持、请求 ID 扩容、多模态帧限制传递、优雅关机测试，表明项目在将服务端基础设施 Rust 化。
- **多模态重构系列（MM refactor 3-5/9）**：分步拆分处理器架构，为视频/图像能力扩展铺路。
- **扩散模型（diffusion）性能与 CI 双线推进**：INT8 权重量化融合、IPC 泄漏修复、B200 测试维护，反映项目正扩展到图像/视频生成推理。
- **安全加固**：管理端点强制 `--admin-api-key`、路由鉴权级别固定、拒绝昂贵 Python 正则，提升生产可用性。

## 3. 对项目的影响与潜在意义
- 缓存与调度优化将直接降低长上下文推理的显存占用和延迟；scheduler 健康探测、prefill 优先级老化等修复提升服务稳定性。
- AMD/NPU 侧 cookbook 与 dsa token 分片等提交显示多硬件生态（AMD MI355X、NPU）投入持续加大。
- 依赖升级（sglang-kernel 0.4.11、sgl-fa3）保持内核层竞争力。

## 4. 值得关注的技术点
- **Rust 树核心的缓存驱逐与墓碑恢复**：性能关键路径向 Rust 迁移的典型案例。
- **spec decode 优化**：避免 H2D 阻塞 MRoPE、Mamba 状态测试，投机解码走向成熟。
- **sampling 正则拒绝与 top-k 标志重推导**：兼顾安全性与运行时正确性。
- 大量 metamergebot/多 AI 代理（Claude、Codex、Cursor）共同署名，体现 AI 辅助开发深度融入工作流。

## 5. 对项目发展的整体影响
这些提交共同强化了 SGLang 作为"快速 LLM 与多模态推理引擎"的定位：通过缓存、内核与调度层的持续性能挖掘巩固推理速度优势，通过安全与稳定性修复推进生产就绪，通过多模态重构和 diffusion 支持拓展应用场景，并通过多硬件适配扩大部署覆盖面。总体上，项目正从单纯的速度追求转向"高性能 + 高可靠 + 多形态"的综合推理平台建设，本次提交批次清晰地体现了这一演进方向。

## 详细提交记录

### [7b5fb39](https://github.com/sgl-project/sglang/commit/7b5fb39bb952da5f6da3bb7fe73c671cf449b6fa)

- **作者**: Shuwen Wang
- **时间**: 2026-11-14T23:32:04Z
- **提交信息**: [Feat] entrypoints: Require --admin-api-key for sensitive admin endpoints (#49896)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [7476772](https://github.com/sgl-project/sglang/commit/7476772241838a1419f5dfe43e2ec167cd75f73e)

- **作者**: metamergebot
- **时间**: 2026-11-14T21:42:37Z
- **提交信息**: [Feat] dp-controller: Forward a scheduler's router_l3_layout entry in the startup handshake (#50544)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: cctry <cctry@users.noreply.github.com>

### [d35aa8b](https://github.com/sgl-project/sglang/commit/d35aa8b8d88c57f299b6eb5095bb083ae20ac4ab)

- **作者**: em-dreyer
- **时间**: 2026-11-14T21:00:48Z
- **提交信息**: [CI] diffusion: Detect custom all-reduce v2 by its symmetric workspace log in the BCG TP2 test (#50426)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [60e6681](https://github.com/sgl-project/sglang/commit/60e6681c8bcada8da62858aa2355db93412bcdd7)

- **作者**: Rain Jiang
- **时间**: 2026-11-14T20:58:30Z
- **提交信息**: [CI] mem_cache: Scope the rendezvous mock in the unmapped-rank gather tests to the pool construction (#50528)

### [ecb69fe](https://github.com/sgl-project/sglang/commit/ecb69fe25df5a0b3d33671286f796395b2873317)

- **作者**: kk
- **时间**: 2026-11-14T20:13:13Z
- **提交信息**: [Doc] [AMD] dsv41: Align MI355X agentic cookbook with InferenceX #5029 (#50398)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [263011c](https://github.com/sgl-project/sglang/commit/263011ca42cb2d80ee409af50733892b4ceb01c5)

- **作者**: Zhang, Jiejing
- **时间**: 2026-11-14T20:08:36Z
- **提交信息**: [Doc] [AMD] cookbook: Refresh GLM-5.2 MI355X AgentX recipe (#50456)

Co-authored-by: Jiejing Zhang <jiejizha@smc300x-ccs-aus-a16-19.prov.aus.ccs.cpe.ice.amd.com>

### [3a93d61](https://github.com/sgl-project/sglang/commit/3a93d61649ca96723a86ee787c85ef2219979aaf)

- **作者**: Tamir Baydasov
- **时间**: 2026-11-14T19:27:28Z
- **提交信息**: [Feat] [NPU] dsa: Token shard, every head for this rank's slice of the tokens (2/2) (#42978)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: KevinZ <popkartzy@gmail.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [6de483b](https://github.com/sgl-project/sglang/commit/6de483b326c7dd4145fde06afcac9866bf491024)

- **作者**: WenhaoZhang
- **时间**: 2026-11-14T16:29:19Z
- **提交信息**: [Fix] comfyui: Stop pinning the H3 source SHA for the ComfyUI alignment patch (#50223)

### [999a6fa](https://github.com/sgl-project/sglang/commit/999a6fa3dc7cb4f9e10d7be8fab9ce5853ae2d4d)

- **作者**: trebladev
- **时间**: 2026-11-14T14:48:41Z
- **提交信息**: [Perf] diffusion: Hy-Nomas fuse groupwise INT8 weight dequantization (#49270)

Co-authored-by: WenhaoZhang <42087078+niehen6174@users.noreply.github.com>

### [0f0d687](https://github.com/sgl-project/sglang/commit/0f0d687b288edaf05d60fbb5b8e79b61bbf3efea)

- **作者**: WenhaoZhang
- **时间**: 2026-11-14T14:47:46Z
- **提交信息**: [Fix] diffusion: Stop the multi-rank IPC all-to-all leak with one IPC handle per peer (#50321)

### [9191794](https://github.com/sgl-project/sglang/commit/91917942f0addfc272cfd31f4f21b4ef6828dfdd)

- **作者**: WenhaoZhang
- **时间**: 2026-11-14T12:52:19Z
- **提交信息**: [CI] diffusion: Skip the server suites for ComfyUI-plugin-only changes (#49248)

### [71b29bb](https://github.com/sgl-project/sglang/commit/71b29bbbfa7a5cdfc3f2e8d3853bad53bd786dfc)

- **作者**: Shubham Garg
- **时间**: 2026-11-14T12:47:15Z
- **提交信息**: [Fix] sampling: Reject expensive Python stop regexes (#49915)

### [6932682](https://github.com/sgl-project/sglang/commit/6932682eb2ea859a468f5e50377e9d8ed774eef9)

- **作者**: Tanish Malekar
- **时间**: 2026-11-14T12:43:29Z
- **提交信息**: [Fix] qwen-vl: Bound GPU memory of image preprocessing (fixes #49796) (#50007)

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [0676b98](https://github.com/sgl-project/sglang/commit/0676b98ca44b8abc2200bcde53a6f82ed9e57a53)

- **作者**: Jensen
- **时间**: 2026-11-14T12:43:05Z
- **提交信息**: [Fix] [NPU] pp: Avoid output AllGather during graph replay (#50345)

### [340ac3a](https://github.com/sgl-project/sglang/commit/340ac3af0b03a860994acaff26a87f1a49dfc6fb)

- **作者**: Shuwen Wang
- **时间**: 2026-11-14T12:42:42Z
- **提交信息**: [Doc] hybrid: Document hybrid cache checkpoint levels (#50034)

### [304a601](https://github.com/sgl-project/sglang/commit/304a6016b3e2fcc157c5466a8c6a182fad20fb8d)

- **作者**: Shri Rajamanikandan Vasudevan
- **时间**: 2026-11-14T12:42:16Z
- **提交信息**: [Perf] gdn: Fuse MIS mapped gates into QKV preparation (#49905)

Co-authored-by: Copilot App <223556219+Copilot@users.noreply.github.com>

### [faa0477](https://github.com/sgl-project/sglang/commit/faa047708dcb60d1872a52b300fc30db59e9d765)

- **作者**: Vincent Liu
- **时间**: 2026-11-14T12:41:54Z
- **提交信息**: [Fix] distributed: Keep deprecated parallel_state getters traceable under torch.compile (#47346)

Signed-off-by: Vincent Liu <vvinniev34@gmail.com>

### [710813d](https://github.com/sgl-project/sglang/commit/710813dee32265a154bbd3194e39214c3d8c3d39)

- **作者**: lynn.lin
- **时间**: 2026-11-14T12:41:34Z
- **提交信息**: [Perf] spec: Avoid blocking H2D for MRoPE delta in spec decode (#46781)

Co-authored-by: scdotbox <128663994+scdotbox@users.noreply.github.com>

### [d87913b](https://github.com/sgl-project/sglang/commit/d87913b4e58b657a5bf54f5c08126a04bb286fdd)

- **作者**: Zhuofeng-Li
- **时间**: 2026-11-14T12:03:53Z
- **提交信息**: [Perf] glm: Bound Triton variants on decode replay (#49121)

Co-authored-by: Simon Yu <simon011130@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5f9e4bb](https://github.com/sgl-project/sglang/commit/5f9e4bb61e00313c179356491281747beda84b1d)

- **作者**: Jan Schalkamp
- **时间**: 2026-11-14T12:03:35Z
- **提交信息**: [Perf] qwen4-exp: gather prefill PLE rows on the host for the file-backed table (#50318)

### [c83b929](https://github.com/sgl-project/sglang/commit/c83b9297b605cf36ededcfa9c36e4136ea5e7c70)

- **作者**: Chen Cheng
- **时间**: 2026-11-14T12:03:19Z
- **提交信息**: [Test] mem_cache: Check request-end Mamba states under spec decode at both checkpoint levels (#50371)

### [85a36a3](https://github.com/sgl-project/sglang/commit/85a36a3c2d4c2095a8a7f8092b9f2062a35c82ef)

- **作者**: Rayan Hatout
- **时间**: 2026-11-14T12:03:04Z
- **提交信息**: [Fix] runtime_context: Read platform facts under torch.compile fullgraph (#50175)

### [5c2d9e4](https://github.com/sgl-project/sglang/commit/5c2d9e4056e131eb0f36daad5b5c21e5d19080df)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-11-14T12:02:48Z
- **提交信息**: [Fix] kvcache: Skip the reserved padding slot in the zero-RoPE MLA KV writer (#47013)

### [72d55dc](https://github.com/sgl-project/sglang/commit/72d55dc90082d0f5e5e9a8abdd3ca70213f5b8f5)

- **作者**: Shubham Garg
- **时间**: 2026-11-14T12:02:33Z
- **提交信息**: [Fix] models: Forward router top_k to fused MoE experts (#49805)

### [fdd71fe](https://github.com/sgl-project/sglang/commit/fdd71fe520dac1506f3877d99bb157e11c4db040)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-14T11:55:58Z
- **提交信息**: [CI] disaggregation: Drop sglang-router from CUDA CI and the NPU PD tests (#50510)

### [5ec2b14](https://github.com/sgl-project/sglang/commit/5ec2b14be5a8927f738c556b276bdf7105a8d30f)

- **作者**: Kangrui Du
- **时间**: 2026-11-14T11:48:05Z
- **提交信息**: [Refactor] multimodal: [MM refactor 5/9] Add a token-space multimodal processor (#46411)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [fc33c59](https://github.com/sgl-project/sglang/commit/fc33c59f3ea45be6dc074408400dfe297ee2e0d0)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-14T11:42:55Z
- **提交信息**: [CI] sgl-router: Build the router once for the e2e and k8s tests (#50502)

### [b77d7b8](https://github.com/sgl-project/sglang/commit/b77d7b8573747aee535612413b5deb2fa178f86e)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-14T10:39:01Z
- **提交信息**: [CI] disaggregation: Launch sgl-router instead of sgl-model-gateway in the PD tests (#50176)

### [19af0c7](https://github.com/sgl-project/sglang/commit/19af0c78a2e864006867b88f3ecb9f8773612fbf)

- **作者**: feixiangpeng
- **时间**: 2026-11-14T10:21:34Z
- **提交信息**: [Perf] hicache: Let the PP-sync channel run the pipeline's depth ahead, not one round (#45351) (#46363)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [8a1bd8a](https://github.com/sgl-project/sglang/commit/8a1bd8a557f2925dbc53203e3fb36d9576943e66)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-14T09:55:17Z
- **提交信息**: [Fix] constrained: Print grammar objects without a memory address (#50496)

### [50106ca](https://github.com/sgl-project/sglang/commit/50106ca2d7680e0ab4397488f13e191ce511d4cd)

- **作者**: Shuwen Wang
- **时间**: 2026-11-14T09:44:43Z
- **提交信息**: [Feat] unified_cache: Support MXFP8 KV caches in the direct external linker (#50324)

### [9ddaa93](https://github.com/sgl-project/sglang/commit/9ddaa93234684b7e863fe1d30743f8f7432e447e)

- **作者**: 黄孝君
- **时间**: 2026-11-14T09:25:28Z
- **提交信息**: [Refactor] [NPU] dsv4: consume registered sgl-kernel-npu Transformer APIs (#50203)

Co-authored-by: vstone-w <374330057@qq.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: lilDss <115407039+lilDss@users.noreply.github.com>
Co-authored-by: chx96642264 <chx96642264@163.com>
Co-authored-by: Codex <codex@openai.com>

### [89386ea](https://github.com/sgl-project/sglang/commit/89386eae7991624d402afcb488d86d5653c332e9)

- **作者**: Michael
- **时间**: 2026-11-14T09:14:14Z
- **提交信息**: [CI] [AMD] kimi-k3: Expect FutureWarning from the renamed KDA env aliases (#50036)

### [ce14d6d](https://github.com/sgl-project/sglang/commit/ce14d6d3ca4a861d6fffa6723c88fae87db66f6f)

- **作者**: Mick
- **时间**: 2026-11-14T09:06:10Z
- **提交信息**: [CI] diffusion: Refresh the B200 MiniMax-H3-Image GT after #50101 (#50476)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [233d6ba](https://github.com/sgl-project/sglang/commit/233d6bae87f218e4f667e4618fe4a674770d7422)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-14T08:52:31Z
- **提交信息**: [Chore] deps: Bump sglang-kernel to 0.4.11 and sgl-fa3 to 0.1.0 (#50397)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2456e0b](https://github.com/sgl-project/sglang/commit/2456e0beab40a2c130f56df4858976db91e2f735)

- **作者**: Shangming Cai
- **时间**: 2026-11-14T07:00:33Z
- **提交信息**: [Test] ep: Temporarily disable test_mooncake_ep_small on the Mooncake EP JIT nvcc spawn flake (#50466)

### [04eece1](https://github.com/sgl-project/sglang/commit/04eece19ada1bf2fee46ab52f19e570f581f2118)

- **作者**: Kangrui Du
- **时间**: 2026-11-14T06:44:04Z
- **提交信息**: [Refactor] multimodal: [MM refactor 4/9] Split feature transport and preprocessing placement out of the base processor (#46410)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [7c68396](https://github.com/sgl-project/sglang/commit/7c683961cce7b97ba29d8d9919a94415878cff0f)

- **作者**: Pinjie Xu
- **时间**: 2026-11-14T06:29:05Z
- **提交信息**: [Perf] diffusion/cosmos: optimize bf16 fa (#49234)

Signed-off-by: pinjie <pinjiex@nvidia.com>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [6a64408](https://github.com/sgl-project/sglang/commit/6a64408419ccc4a091e3982c5b9fc10c5bda0f0e)

- **作者**: Mick
- **时间**: 2026-11-14T06:20:47Z
- **提交信息**: [Perf] diffusion: Look up the rounded SiLU of the gated activation in a table on sm_10x (#50390)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cb55118](https://github.com/sgl-project/sglang/commit/cb551180329b719f892580fe21d3534b45fbcbe6)

- **作者**: Shuwen Wang
- **时间**: 2026-11-14T06:03:38Z
- **提交信息**: [Fix] entrypoints: Resolve auth levels of included routers and pin a level for every route (#49895)

### [ac939df](https://github.com/sgl-project/sglang/commit/ac939dfaa8dc72448b4cd8cdd8408c39c50b365b)

- **作者**: viete chen
- **时间**: 2026-11-14T05:30:51Z
- **提交信息**: [Fix] [NPU] modelslime: Fix NEXTN startup and mamba scatter UB overflow (#34353)

Co-authored-by: w1ida <noreply@github.com>

### [a05c729](https://github.com/sgl-project/sglang/commit/a05c729c4eb233c73b22f7a9289bcd11868d8cee)

- **作者**: Teng Ma
- **时间**: 2026-11-14T05:22:17Z
- **提交信息**: [Fix] hicache: Include logical KV dtype in storage keys (#38362)

Signed-off-by: Teng Ma <stmatengss@users.noreply.github.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: Teng Ma <stmatengss@users.noreply.github.com>

### [4a909c3](https://github.com/sgl-project/sglang/commit/4a909c3ba6ac32ea59347f9f5d7680794557cb97)

- **作者**: metamergebot
- **时间**: 2026-11-14T05:21:40Z
- **提交信息**: [Perf] sampling: Re-derive the top-k flags when a running batch drops rows (#50400)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: YavorGIvanov <YavorGIvanov@users.noreply.github.com>

### [bd47834](https://github.com/sgl-project/sglang/commit/bd4783409967b186ecb95956a6ab11256ce6d296)

- **作者**: lming2001
- **时间**: 2026-11-14T03:26:49Z
- **提交信息**: [Feat] rust-server: Accept client request IDs up to 256 bytes (#49970)

Co-authored-by: Minh Doan <doanmh@users.noreply.github.com>

### [c5d7c59](https://github.com/sgl-project/sglang/commit/c5d7c598049655046ccbdb8ae8d95b8e3aa3d2b3)

- **作者**: metamergebot
- **时间**: 2026-11-14T02:56:33Z
- **提交信息**: [Feat] rust-server: Pass the video item frame and token caps to multimodal processors (#50407)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: 22quinn <33176974+22quinn@users.noreply.github.com>

### [19668f7](https://github.com/sgl-project/sglang/commit/19668f7b9bee449057879a74de2ced640953e8d6)

- **作者**: metamergebot
- **时间**: 2026-11-14T02:56:25Z
- **提交信息**: [Feat] rust-server: Serve HTTP/2 (h2c) beside HTTP/1.1 with --enable-http2 (#50401)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [56fa7ca](https://github.com/sgl-project/sglang/commit/56fa7ca6e7e4004aeb935b6bb38d0acf81340510)

- **作者**: metamergebot
- **时间**: 2026-11-14T02:09:23Z
- **提交信息**: [Feat] kv-shard: Let an out-of-tree HiCache storage backend join logical-page KV sharding (#50370)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [6317e8e](https://github.com/sgl-project/sglang/commit/6317e8ed4b69996d39a59cddeb68177a7fcc7489)

- **作者**: Kangrui Du
- **时间**: 2026-11-14T02:01:40Z
- **提交信息**: [Refactor] multimodal: [MM refactor 3/9] Extract a shared multimodal processor mixin (#46409)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [1dd0dcc](https://github.com/sgl-project/sglang/commit/1dd0dcce38ee01c6828c16700e7a4790bf438a9d)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:53:13Z
- **提交信息**: [Feat] mem_cache: Joint Full/SWA eviction walk on the Rust tree core (#49992)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [fe10e2b](https://github.com/sgl-project/sglang/commit/fe10e2be647b7cdf693ccef972b8a9ba19244000)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:52:46Z
- **提交信息**: [Fix] scheduler: Answer health probes that are waiting behind other requests (#49721)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [e1113c1](https://github.com/sgl-project/sglang/commit/e1113c1fc373204398fff1f5ae262b670202a67c)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:52:20Z
- **提交信息**: [Refactor] mem_cache: Tag full-only KV frees that release a tree node's value, and commit load-backs through one method (#49695)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [5f11045](https://github.com/sgl-project/sglang/commit/5f11045a0829ff47c21c49cd9d287e6509bea416)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:51:49Z
- **提交信息**: [Perf] hicache: Keep the buffer load-back ownership check from waiting on the GPU at admission (#49666)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [e5caad9](https://github.com/sgl-project/sglang/commit/e5caad9a07573616e16614a9f374089959a7c48f)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:50:59Z
- **提交信息**: [Feat] scheduler: Add opt-in aging to the shortest-prefill-first policy (#49658)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [25363de](https://github.com/sgl-project/sglang/commit/25363debb81e827c292225f6fc22c1ee648a98ec)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:50:19Z
- **提交信息**: [Fix] scheduler: Observe finished storage prefetches before shortest-prefill-first ranks, and count staged prefixes as cached (#49649)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [cbf4c36](https://github.com/sgl-project/sglang/commit/cbf4c366879814053b48c216f272bcde9518da30)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:49:26Z
- **提交信息**: [Perf] hicache: End each buffer-only backup chain where the insert walk's previous one ended (#49644)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [800f596](https://github.com/sgl-project/sglang/commit/800f596bfc8fbcbb521ec58058c6f63d06e4ee31)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:48:19Z
- **提交信息**: [Fix] radix-tree: Clamp SWA tombstone recovery to the protected prefix in the Rust tree core (#49641)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin <Jialin@users.noreply.github.com>

### [1be399b](https://github.com/sgl-project/sglang/commit/1be399bd114af076921943e3e7d4f9eac7708b63)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:23:37Z
- **提交信息**: [Fix] rust-server: Log the drain's scheduler kill at info and bound the reap (#49630)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [b074ad4](https://github.com/sgl-project/sglang/commit/b074ad473a05614f830c4a2122fdcea05a0c1871)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:23:13Z
- **提交信息**: [Test] rust-server: Give each shutdown test its own parallel topology (#50396)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shub-garg <shub-garg@users.noreply.github.com>

### [6e4f22f](https://github.com/sgl-project/sglang/commit/6e4f22fcd1ec87de0c9ce2d24587c4a5f1e9cd2e)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:22:47Z
- **提交信息**: [Chore] rust-server: Refresh the frontend config catalogue and drop its Rust lexer (#49634)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [fc8d97d](https://github.com/sgl-project/sglang/commit/fc8d97d142b42dc9d9fcbf494290086a02fd6ed4)

- **作者**: metamergebot
- **时间**: 2026-11-14T01:21:46Z
- **提交信息**: [CI] tests: Give each NIXL storage test its own temp directory (#44613)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1307
- **最后更新**: 2026-11-14T20:07:58Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Butterfingrz

## AI分析总结

## 提交分析：`e085ea6` — Profiler 窗口化采集与 NVTX 标注

### 1. 主要更新类型
- **功能新增**：新增带时间窗口的 Torch Profiler / Nsight 采集能力、NVTX 阶段标注
- **重构**：将 profiler 相关代码从生成 CLI 中拆分到独立 `profile` 子包，采集器实现归位

### 2. 关键变更点与项目方向的关系
- **窗口化采集**：支持只在指定时间窗口内做 Torch Profiler 与 Nsight 采集，避免全程录制带来的开销，直接服务于推理引擎的性能调优场景。
- **CLI 集成**：在命令行中暴露 profile 请求能力，并为 MiniMax-H3 模型的推理步骤接入了 profiler，说明项目开始关注端到端模型链路的可观测性。
- **NVTX 阶段标注与模块钩子**：为推理各阶段（如编码、采样、去噪步）打上 NVTX scope，并通过模块钩子注入，便于在 Nsight Systems 中直观看到各阶段耗时。
- **NVTX + 窗口协同**：让 Nsight 窗口与 NVTX 标注协同工作，精准截取关键推理阶段的 GPU 时间线。
- **代码组织重构**：将 profiler 逻辑从生成 CLI 中剥离到 `profile` 子包，保持 CLI 精简，也便于后续扩展更多分析器。

### 3. 对项目的影响和潜在意义
- 填补了 cache-dit 作为推理引擎在**性能剖析**这一维度的空白，与 README 宣称的 Cache、并行、量化、CPU offload 等优化方向形成闭环——优化前先能量化。
- 让用户可以低成本地定位推理瓶颈（哪个阶段、哪层算子慢），降低使用门槛。
- 模块化的 profile 子包为未来接入更多 profiling 后端（如 PyTorch Kineto、自定义计时器）预留了扩展空间。

### 4. 值得关注的技术点
- **窗口化 vs 全程采集**的权衡：窗口内采集既保留细节又降低开销，对长序列/长步数 DiT 推理尤其重要。
- **NVTX 注入方式**：采用模块钩子而非侵入式改写模型代码，侵入性低、可开关。
- **NVTX 与 Nsight 协同**：需要进程内窗口与外部 Nsight 工具的时钟对齐，实现上有一定技巧性。
- 重构后 profiler 从 CLI 中解耦，架构更清晰，符合库化使用（PyPI 分发）的长期目标。

### 5. 对项目发展的整体影响
结合 README，cache-dit 是一个面向 DiT 的 PyTorch 原生推理引擎，核心卖点是各种推理优化。本次提交让项目从"只做优化"扩展到"优化 + 可观测"，为性能调优提供了**量化依据**，也便于社区贡献者排查问题。这是一次对工程成熟度有明显提升的基础性投入，后续的 Cache、量化等优化工作都能因此受益——先测量，再优化。

## 详细提交记录

### [e085ea6](https://github.com/vipshop/cache-dit/commit/e085ea6ac723bc6876f2a32d5334f3211b5b43c6)

- **作者**: Butterfingrz
- **时间**: 2026-11-14T09:04:28Z
- **提交信息**: feat(profiler): add windowed Torch/Nsight collection and NVTX annotations (#1326)

* feat(profiler): add windowed Torch collection

Signed-off-by: Butterfingrz <13524387014@163.com>

* feat(cli): profile requests and wire MiniMax-H3 steps

Signed-off-by: Butterfingrz <13524387014@163.com>

* feat(nvtx): add stage scopes and module hooks

Signed-off-by: Butterfingrz <13524387014@163.com>

* feat(minimax-h3): annotate inference stages

Signed-off-by: Butterfingrz <13524387014@163.com>

* feat(profiler): add coordinated Nsight windows

Signed-off-by: Butterfingrz <13524387014@163.com>

* refactor(profiler): move collectors into profile subpackage

Signed-off-by: Butterfingrz <13524387014@163.com>

* refactor(profiler): move instrumentation out of generate CLI

Signed-off-by: Butterfingrz <13524387014@163.com>

---------

Signed-off-by: Butterfingrz <13524387014@163.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96939
- **最后更新**: 2026-11-15T00:28:45Z

## 提交统计

- **昨日提交总数**: 49
- **提交者数量**: 37
- **主要提交者**: cjackal, aoshen02, siyu

## AI分析总结

## vLLM 昨日提交批次（49条）分析总结

### 1. 主要更新类型
- **性能优化**：约10条，涵盖MoE路由、GEMM、数据类槽位优化、垃圾回收等
- **Bug修复**：约15条，涉及多模态、Rust前端、投机解码、XPU后端等
- **硬件后端适配**：约12条，ROCm与XPU（Intel）占主导
- **CI/测试**：约12条，集中在ROCm与XPU测试稳定性
- **功能新增**：Transformers后端支持Qwen2、EPD支持Kimi-K3、NIXL KV连接器等

### 2. 关键变更点与项目方向的关系
- **硬件生态多元化**：大量ROCm（AMD MI300/MI355）与XPU（Intel）提交，体现vLLM"为所有人提供廉价快速LLM服务"的目标——扩大硬件覆盖以降低成本。
- **投机解码与DBO深化**：MRV2（DeepSeek-V4）、Dual Batch Overlap纯张量并行、EAGLE-3修复，推动推理吞吐上限。
- **模型支持扩展**：Qwen2走Transformers后端、Kimi-K3相关配方与EPD支持、NVFP4量化保持CSF压缩，紧跟前沿模型。
- **Rust前端生产化**：SIGTERM优雅停机、错误码修正，提升服务可靠性。

### 3. 对项目的影响和潜在意义
- ROCm测试队列重定向与torchao烘焙将提升AMD平台CI稳定性，加速GPU后端质量保障。
- DBO、MoE DP padding掩码、NVFP4专家scale驻留GPU等直接降低延迟、提升吞吐。
- 移除OpenPangu-VL、修复Mistral3示例体现对模型库的持续清理与维护。

### 4. 值得关注的技术点
- **B12X上NVFP4专家scale保持CSF压缩**：减少量化元数据的设备间搬运。
- **组top-k路由默认屏蔽DP padding行**：避免无效token影响路由质量。
- **NIXL从流水线并行prefill阶段拉取KV**：配合混合KV缓存管理器，支撑分离式架构。
- **内部数据类统一使用`slots=True`**：减少内存开销的小而通用的优化。

### 5. 结合README背景的影响
vLLM定位"简单、快速、廉价的LLM服务"。本批次通过：(a) AMD/Intel后端与CI加固降低硬件门槛；(b) 投机解码、DBO、量化等性能工作提升"快速"；(c) Rust前端与CI修复保障生产稳定性。整体显示项目在**广度（多硬件、多模型）与深度（性能极限）**上并行推进，且AI辅助开发（Claude/Codex/Copilot署名）已成为常规协作模式。

## 详细提交记录

### [a16bfee](https://github.com/vllm-project/vllm/commit/a16bfee11b92f1809628a8bd1f4bd70cdcb9b576)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-14T22:22:18Z
- **提交信息**: [Model Loader] Fill dummy FP8 weights with random codes across the range (#67693)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5e51c0c](https://github.com/vllm-project/vllm/commit/5e51c0ca1041168de7aa9e096982aebaeebabd38)

- **作者**: Taoyu Zhu
- **时间**: 2026-11-14T19:22:28Z
- **提交信息**: [Core][DBO] Dual batch overlap under pure tensor parallelism (split PR of M3.1) (#63483)

Signed-off-by: Taoyu Zhu <zhutaoyu97@gmail.com>
Signed-off-by: benzhuzhu <zhutaoyu97@gmail.com>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cb71f58](https://github.com/vllm-project/vllm/commit/cb71f581322c7fd4c136cb7a80f00d6b85625b0f)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-14T19:05:36Z
- **提交信息**: [CI][Test] Stub pipeline_relay in the engram DP-shard model forward test (#67636)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [640c349](https://github.com/vllm-project/vllm/commit/640c349c94d7538031325a6d29ff5a0b51234e7a)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-14T18:43:16Z
- **提交信息**: [Bugfix][Core] Keep dummy-run requests within max_model_len (#67545)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bb23c0a](https://github.com/vllm-project/vllm/commit/bb23c0a81779ba733923a7dab9b840b4e533f6a5)

- **作者**: ZhouXiaoya25
- **时间**: 2026-11-14T16:36:13Z
- **提交信息**: [XPU][MLA] Register XPUFlashAttnMLABackend for FLASH_ATTN_MLA in XPU (#64255)

Signed-off-by: Zhouxiaoya25 <xiaoya.zhou@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d2f9285](https://github.com/vllm-project/vllm/commit/d2f92859b4c62434a2c111036ebe62cb0e9de243)

- **作者**: lazymio
- **时间**: 2026-11-14T16:02:26Z
- **提交信息**: [Bugfix][MRV2] Allow non 8-bytes aligned `--max-num-batched-tokens` for DeepSeek-v4 (#66401)

Signed-off-by: lazymio <mio@lazym.io>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0431c0f](https://github.com/vllm-project/vllm/commit/0431c0f7353d54fbffd1f7881b26009f67c9618a)

- **作者**: Harry Mellor
- **时间**: 2026-11-14T15:38:52Z
- **提交信息**: [Transformers backend] Serve Qwen2 with the Transformers modeling backend (#66821)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0edc2ea](https://github.com/vllm-project/vllm/commit/0edc2ea1ee18b90b85786a47ef6144a2fa93f738)

- **作者**: Harry Mellor
- **时间**: 2026-11-14T15:38:46Z
- **提交信息**: [CI] Bump Transformers version to 5.23.0 (#67502)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [76a4fed](https://github.com/vllm-project/vllm/commit/76a4fedf4cc9f24764916cc8158f150e68c063b6)

- **作者**: Xinsheng Ooi
- **时间**: 2026-11-14T15:29:19Z
- **提交信息**: [MM] Support mm_device_do_normalize for LLaVA-OneVision (#67505)

Signed-off-by: Xinsheng Ooi <ooixinsheng@gmail.com>

### [5780268](https://github.com/vllm-project/vllm/commit/57802683a577c57ae78615460dfeaf2f3a20627e)

- **作者**: Wentao Ye
- **时间**: 2026-11-14T14:51:34Z
- **提交信息**: [Chore] Update agent skill for vLLM (#67273)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [0e73a58](https://github.com/vllm-project/vllm/commit/0e73a584534ec3872e78c380002568bf6ddfac3c)

- **作者**: mikume
- **时间**: 2026-11-14T14:42:46Z
- **提交信息**: [MM] Support mm_device_do_normalize for Qwen3-Omni (#67426)

Signed-off-by: gordan12 <gordan941222@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [865cf8c](https://github.com/vllm-project/vllm/commit/865cf8c1f2e5a0567fe6789663a5210ef904b57c)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-14T13:56:09Z
- **提交信息**: [CI][Test] Run test_mm_prefix_lm_pipeline_parallel with spawned workers (#67637)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [78233b8](https://github.com/vllm-project/vllm/commit/78233b8f2e256d2cb9dc5fbf547a17cfdd2cca18)

- **作者**: Tony Lin
- **时间**: 2026-11-14T13:54:11Z
- **提交信息**: [CI][XPU] Bound DeepStack test profiling to avoid OOM (#67601)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [f9d4b51](https://github.com/vllm-project/vllm/commit/f9d4b51b1dc3144780f5f9b3675f0e7247d43b47)

- **作者**: aoshen02
- **时间**: 2026-11-14T13:49:23Z
- **提交信息**: [Perf] Allow EPLB with modular TRT-LLM FP8 block-scale MoE (#67591)

Signed-off-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ec8b71e](https://github.com/vllm-project/vllm/commit/ec8b71e4a22c066791174fc48b7e9c3db092fb71)

- **作者**: aoshen02
- **时间**: 2026-11-14T13:46:24Z
- **提交信息**: [Bugfix][AuxOutput] Size the routed-experts row cache from one source (#67599)

Signed-off-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Ao Shen <aoshen524@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6f1ec6a](https://github.com/vllm-project/vllm/commit/6f1ec6a4c62d6a7a756edd53fd00a57782542cbd)

- **作者**: Harry Mellor
- **时间**: 2026-11-14T12:52:28Z
- **提交信息**: [Model] Remove OpenPangu-VL (#67632)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [01548ee](https://github.com/vllm-project/vllm/commit/01548eecdef5d99e286e27593b4eaea220327a6f)

- **作者**: Shuolei Wang
- **时间**: 2026-11-14T12:46:50Z
- **提交信息**: [Perf][Bugfix][RL] Fix sparse NCCL update OOM and improve performance (#66375)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [e72e9cb](https://github.com/vllm-project/vllm/commit/e72e9cb18b4253e2c36dedb48d644c0627baffeb)

- **作者**: Stefano Castagnetta
- **时间**: 2026-11-14T12:38:18Z
- **提交信息**: [Quantization][MoE] Keep NVFP4 expert scales CSF-compressed on the GPU with B12X (#64753)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Signed-off-by: lesj0610 <lesj0610@gmail.com>
Signed-off-by: Kam Basra <kameldipbasra@gmail.com>
Co-authored-by: lesj0610 <lesj0610@gmail.com>
Co-authored-by: Kam Basra <kameldipbasra@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2ab8e2f](https://github.com/vllm-project/vllm/commit/2ab8e2f746696ad7aab6cc6178ee37afa072ec8e)

- **作者**: Harry Mellor
- **时间**: 2026-11-14T11:25:01Z
- **提交信息**: [Bugfix] Fix EAGLE-3 on Transformers backend VLMs (#67519)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [02004e1](https://github.com/vllm-project/vllm/commit/02004e1a0b5335d74361beb8ec04ef42bde06baa)

- **作者**: Artur Fierka
- **时间**: 2026-11-14T11:12:56Z
- **提交信息**: [Bugfix][XPU] Use int64 token index in the DeepSeek-V4 qnorm/RoPE kernel (#64515)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5fad73d](https://github.com/vllm-project/vllm/commit/5fad73d1221d61446fb178bb0bf9151482ac43d0)

- **作者**: Thang Nguyen
- **时间**: 2026-11-14T10:54:08Z
- **提交信息**: [CI][ROCm] Bake torchao into the ROCm test image off the default path and re-enable MI300/MI355 Quantization (#66672)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ce72586](https://github.com/vllm-project/vllm/commit/ce72586f8aded8dafa7d4c745a5cef3198070e3e)

- **作者**: Nick Hill
- **时间**: 2026-11-14T09:18:41Z
- **提交信息**: [Perf] Use `slots=True` on all internal dataclasses (#67297)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [13079c3](https://github.com/vllm-project/vllm/commit/13079c37c29ed500083f49dc02bf077112ae7600)

- **作者**: Vinayak Gokhale
- **时间**: 2026-11-14T09:17:21Z
- **提交信息**: [ROCm] M3.1 GEMM improvements (#66933)

Signed-off-by: Vinayak Gokhale <vinayak.gokhale@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [2aa7eb3](https://github.com/vllm-project/vllm/commit/2aa7eb3ea5cea8c99f484ca726be2f4d9c0ba418)

- **作者**: Vinayak Gokhale
- **时间**: 2026-11-14T09:16:29Z
- **提交信息**: [ROCm] Minimax M3.1 attn indexer XCD balancing (#66934)

Signed-off-by: Vinayak Gokhale <vinayak.gokhale@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [5ec9995](https://github.com/vllm-project/vllm/commit/5ec99956ad4253e70a56c8c0179c5af14fef377d)

- **作者**: seungrokj
- **时间**: 2026-11-14T07:18:36Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: MI355X AgentX preset covering all six InferenceX#5043 concurrencies (#67600)

### [24d4c49](https://github.com/vllm-project/vllm/commit/24d4c4949db5d6d8c3149eb3c8f2ddb1f2c0224d)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-14T07:15:27Z
- **提交信息**: [Bugfix][Multimodal] Size the MOSS-Audio profiling dummy to its audio budget (#67474)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2fb6d0b](https://github.com/vllm-project/vllm/commit/2fb6d0b75d3e803a2d27c640b5c45be47af0029c)

- **作者**: Vito Lin
- **时间**: 2026-11-14T06:59:29Z
- **提交信息**: [Bugfix][Rust Frontend] Return 400 instead of 500 when tool parsing is disabled (#63580)

Signed-off-by: vito-lin-dev <ac1246897@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c1429e7](https://github.com/vllm-project/vllm/commit/c1429e77419d92f84db1c8c536fea7d4b4130e52)

- **作者**: Ekagra Ranjan
- **时间**: 2026-11-14T06:58:11Z
- **提交信息**: [Bugfix][Audio] Fall back to soundfile when torchcodec fails to decode (#67105)

Signed-off-by: Ekagra Ranjan <3116519+ekagra-ranjan@users.noreply.github.com>

### [ec94b6a](https://github.com/vllm-project/vllm/commit/ec94b6a7fc3b7141528113fbc89802829a914c25)

- **作者**: liangjuf
- **时间**: 2026-11-14T06:50:47Z
- **提交信息**: [Bugfix][Rust Frontend] SIGTERM only the managed engine's launcher so in-flight requests drain (#67282)

Signed-off-by: Liangjun Feng <lfeng@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Liangjun Feng <lfeng@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [165156b](https://github.com/vllm-project/vllm/commit/165156b59ba013a6353b70237e11366900cb99d3)

- **作者**: qizixi
- **时间**: 2026-11-14T06:16:51Z
- **提交信息**: [Spec Decode][MRV2] Build no draft attention metadata on a context-K/V-only prefill (#67291)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [06c5e7c](https://github.com/vllm-project/vllm/commit/06c5e7c3ba2c05beb3b7b69274cfc6c71cc9fb82)

- **作者**: Lin Sun
- **时间**: 2026-11-14T06:08:48Z
- **提交信息**: [ROCm] Keep the extensible KV cache for fd-exporting KV connectors (#67577)

Signed-off-by: Lin Sun <lin.sun@amd.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [615c9d6](https://github.com/vllm-project/vllm/commit/615c9d6474a7793a024786e67fbb99791e809d98)

- **作者**: FED4
- **时间**: 2026-11-14T05:52:57Z
- **提交信息**: [BugFix] Fix Mistral3 multimodal offline example (#43638)

Signed-off-by: FED4 <feiyyfrank@outlook.com>

### [b15bfb5](https://github.com/vllm-project/vllm/commit/b15bfb530f2e133d2ca2d8c6cd8b02899aa368df)

- **作者**: Sheral Kumar
- **时间**: 2026-11-14T05:45:30Z
- **提交信息**: [ROCm][CI] Retarget 36 MI300 1 GPU jobs to the mi300_dpx queue (#67308)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a1628b6](https://github.com/vllm-project/vllm/commit/a1628b6ac3be2b745dfc11f7d31825302992e4e2)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-14T05:37:41Z
- **提交信息**: [CI][ROCm][Kimi-K3] Compile each TP8 mono build and line the ranks up before launching it (#67439)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d06d4b7](https://github.com/vllm-project/vllm/commit/d06d4b7aa99809173611d6e1b7f4e99bf7b57413)

- **作者**: Aarushi Jain
- **时间**: 2026-11-14T05:37:22Z
- **提交信息**: [ROCm][CI] Stub dcp_world_size in the merged-cache sparse MLA test (#67555)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [449576c](https://github.com/vllm-project/vllm/commit/449576cd736544461357e835ca74b44a993668ea)

- **作者**: Alex Brooks
- **时间**: 2026-11-14T05:00:46Z
- **提交信息**: [Perf] Optimize Garbage Collection at Init Time (#64542)

Signed-off-by: Alex Brooks <albrooks@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [37ea94f](https://github.com/vllm-project/vllm/commit/37ea94f715acc34f84bc3728ec3e365e40eb53ac)

- **作者**: Avinash Paul
- **时间**: 2026-11-14T04:36:22Z
- **提交信息**: [ROCm][Disagg][CI] Give Wide-EP headless nodes the KV config (#65098)

Signed-off-by: avpaul <avpaul@amd.com>
Signed-off-by: avininjamay8 <avpaul@amd.com>
Co-authored-by: avpaul <avpaul@amd.com>
Co-authored-by: Chaitanya Sri Krishna Lolla <lollachaitanya@gmail.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [19e84b3](https://github.com/vllm-project/vllm/commit/19e84b344704764a0232084e6e7d3a102bba892a)

- **作者**: PerryZhang01
- **时间**: 2026-11-14T04:20:25Z
- **提交信息**: [CI][Multimodal] Use `uuid:`-tagged cache key for features in /generate test and docs (#67564)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [24fe0a9](https://github.com/vllm-project/vllm/commit/24fe0a99f1062f7351852804f2cd38668f7423bd)

- **作者**: Tianyu Guo
- **时间**: 2026-11-14T04:13:13Z
- **提交信息**: [Feature][EPD] Support Kimi-K3 image metadata-only inputs (#66925)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1a594a3](https://github.com/vllm-project/vllm/commit/1a594a3ec1872b40ac00131a31d1f83d81cbdd80)

- **作者**: cjackal
- **时间**: 2026-11-14T04:01:10Z
- **提交信息**: [Bugfix][Multimodal] Repeat-last default padding for `cu_seqlens` in multimodal CG (#65453)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [55aa0ca](https://github.com/vllm-project/vllm/commit/55aa0cab78dedbb018ad4f4ea649f2d3d5e1c2a8)

- **作者**: PerryZhang01
- **时间**: 2026-11-14T03:25:42Z
- **提交信息**: [CI][Bugfix] Fix fake backend in drafter kernel block size test (#67579)

Signed-off-by: PerryZhang01 <Perry.Zhang@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dcd6e77](https://github.com/vllm-project/vllm/commit/dcd6e77b58bfefc62f0fe9cabeac596341cf7a59)

- **作者**: seungrokj
- **时间**: 2026-11-14T03:25:06Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: MI355X kimi-k31-6d74a15 image, concurrency-48 with 3 draft tokens, align with InferenceX#5043 (#67487)

### [fee9686](https://github.com/vllm-project/vllm/commit/fee9686811b7c060c404dba0c6a5a6007de4659b)

- **作者**: Bo Pang
- **时间**: 2026-11-14T02:18:27Z
- **提交信息**: [Perf][MoE] Mask DP padding rows in grouped top-k routing by default (#66799)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [ea0e808](https://github.com/vllm-project/vllm/commit/ea0e80845dedfbcec72053a7b17caade285a4b1e)

- **作者**: siyu
- **时间**: 2026-11-14T02:17:28Z
- **提交信息**: [KV Connector][NIXL] Pull KV from pipeline-parallel prefill stages, with the hybrid KV cache manager (#65336)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Signed-off-by: Yuhan Zhou <zhouyuhan_@outlook.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yuhan Zhou <zhouyuhan_@outlook.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b11ae05](https://github.com/vllm-project/vllm/commit/b11ae058d62270964b21a469233ad7d3ab1a6560)

- **作者**: Hangrui Cao
- **时间**: 2026-11-14T02:01:47Z
- **提交信息**: [DeepSeek-V4] Warm the DeepGEMM kernels DeepSeek-V4/V4.1 JIT-compile at runtime (#64827)

Signed-off-by: hangrui cao <hangrui.cao@zoom.us>
Signed-off-by: HangruiCao2000 <caohangrui2000@gmail.com>
Co-authored-by: hangrui cao <hangrui.cao@zoom.us>
Co-authored-by: wangyicong <wangyicong@bytedance.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4b88a43](https://github.com/vllm-project/vllm/commit/4b88a438fb3efd4e11186ab06571d43d8eb514de)

- **作者**: Harry Mellor
- **时间**: 2026-11-14T01:12:25Z
- **提交信息**: [Transformers backend] Default decoder pooling to LAST and honour `is_causal=False` (#67455)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [555ae7d](https://github.com/vllm-project/vllm/commit/555ae7d1d1989dbf21abb6cee96d8f2cf810ff74)

- **作者**: Aarushi Jain
- **时间**: 2026-11-14T00:30:06Z
- **提交信息**: [ROCm][CI] Cover test_areas gaps on AMD mirrors (#67317)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [5cb0fd2](https://github.com/vllm-project/vllm/commit/5cb0fd265d65a8ab9a39517ddb33a9996fe45398)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-14T00:19:13Z
- **提交信息**: [ROCm][CI] Run the nightly Python 3.14 smoke test on AMD (#66314)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3f1c89b](https://github.com/vllm-project/vllm/commit/3f1c89b5785a0ddd10e3bb90922935c810fb23d2)

- **作者**: Aarushi Jain
- **时间**: 2026-11-14T00:19:01Z
- **提交信息**: [Bugfix][Test] Avoid capfd in test_pp_rejects_split_kv_sharing (#67321)

Signed-off-by: aarushjain29 <aarushi.jain2@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-15
**监控日期**: 2026-11-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7761
- **最后更新**: 2026-11-15T01:45:40Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 16
- **主要提交者**: Thanaji Rao Thakkalapelli, Pan Li, SFA_Sukhoi

## AI分析总结

# vllm-omni 昨日提交分析（1/1 批，共 22 条）

## 1. 主要更新类型
- **Bug 修复**：占比最高（约 8 条），涵盖 TTS/ROCm 周测路径、UNI diffusion 输出同步、FA Blackwell 测试、GLM-Image 离线路由等。
- **功能新增**：约 7 条，包括 Praxis-1 视频/动作策略（DROID）、Kandinsky6 Distil、weight_stack 包基础、LingBot-Video CPU/layerwise offload 等。
- **性能优化**：约 5 条，如 FlashInfer autotune、Wan2.2 S2V 音频注入编译、Qwen-Image ring SP、CUDA MRv2 K-step。
- **CI/Build 维护**：约 6 条，集中于 ROCm/CUDA 周测覆盖扩展与超时调优。

## 2. 关键变更点与项目方向的关系
- **多模态广度扩展**：新增视频（DROID、LingBot）、图像（Kandinsky6、Ming-Image）、TTS 多个模型的原生支持，直接呼应 README "omni-modality model serving" 的定位。
- **硬件生态双轨并行**：ROCm 周测大量补齐（BAGEL、Ming GLM IndexTTS、Breeze、TTS），与 CUDA 覆盖同步，体现跨平台 serving 承诺。
- **扩散模型深度优化**：attention profile 选择、LoRA delta 分片（TP）、layerwise offload、FlashInfer autotune，说明 diffusion 已成为核心负载之一。

## 3. 影响与潜在意义
- CI 稳定性显著提升（"zero retries, zero soft failures"），降低多硬件回归成本。
- offload 与 kernel autotune 使低显存/新架构（SM100+、Blackwell）可用性增强，扩大用户覆盖。
- 多个模型（Praxis-1 为 1/4 系列）分阶段合入，显示 roadmap 有序推进。

## 4. 值得关注的技术点
- **weight_stack 包**（RFC 9536 01-1）：diffusion 权重管理的架构级奠基，后续可能重构权重加载路径。
- **fused diffusion LoRA delta 分片**：把 LoRA 正确融入 TP，对多卡 serving 关键。
- **Wan VAE "one installer"**：统一 Wan 系列 VAE 安装路径，降低维护面。
- **FlashInfer autotune 默认开启（SM100+）**：意味着新 GPU 默认走自动调优，可能改变性能基线。

## 5. 对项目发展的影响
结合 README "Easy, fast, cheap" 的目标：本周提交同时压低成本（offload、缓存优化）、提升速度（kernel/attention 调优）与易用性（更多模型开箱即用、CI 可靠）。ROCm 覆盖的密集补齐表明项目正从 CUDA 单一生态走向真正的跨厂商 omni serving 平台，而 diffusion 系列优化则巩固了其在生成式多模态负载上的竞争力。整体看，项目处于"模型覆盖面扩张 + 底层性能与稳定性双打磨"的健康迭代节奏，为后续大规模生产部署铺路。

## 详细提交记录

### [eb20778](https://github.com/vllm-project/vllm-omni/commit/eb2077899989a07d0e7acb9cda3217734fdc8909)

- **作者**: lm10-arg
- **时间**: 2026-11-14T22:13:06Z
- **提交信息**: [CI/Build][ROCm] Add BAGEL weekly coverage and fix routed LoRA (#10382)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [1946a95](https://github.com/vllm-project/vllm-omni/commit/1946a95f3a49a2ca8e9d462ac11d774a2fb0c80e)

- **作者**: lm10-arg
- **时间**: 2026-11-14T17:46:10Z
- **提交信息**: [CI/Build][ROCm][Bugfix] Match remaining TTS weekly paths (#10367)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [12a02d4](https://github.com/vllm-project/vllm-omni/commit/12a02d46ddd8946c974fb0410ba81cfb91a5d99e)

- **作者**: Pan Li
- **时间**: 2026-11-14T17:00:04Z
- **提交信息**: [diffusion][model] Enable CPU/layerwise offload for LingBot-Video (#5359)

Signed-off-by: Pan Li <pandalee@ustc.edu>

### [0eac18a](https://github.com/vllm-project/vllm-omni/commit/0eac18a8f0a1f3f87209937b6586b0f89640def1)

- **作者**: Lucas Kabela
- **时间**: 2026-11-14T16:52:18Z
- **提交信息**: [1/4][Model] Add native Praxis-1 video/action policy (DROID) (#10197)

Signed-off-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Lucas Kabela <20960393+Lucaskabela@users.noreply.github.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [34dfbbd](https://github.com/vllm-project/vllm-omni/commit/34dfbbdb6c3bff8946864a6cc9bc70b85500f0eb)

- **作者**: SFA_Sukhoi
- **时间**: 2026-11-14T16:33:55Z
- **提交信息**: [Bugfix] Synchronize UNI diffusion output handoff (#9804)

Signed-off-by: beiningwu <sukhoi258@163.com>
Co-authored-by: beiningwu <sukhoi258@163.com>

### [07fb787](https://github.com/vllm-project/vllm-omni/commit/07fb787f3f0c1177ec116ed47f34ea5fd1a5ba89)

- **作者**: Linze Shi
- **时间**: 2026-11-14T16:25:11Z
- **提交信息**: [Bugfix] Shard fused diffusion LoRA deltas for tensor parallelism (#9708)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [513bcdf](https://github.com/vllm-project/vllm-omni/commit/513bcdfc2c1b474d327ff59d5a187ebc445bb63f)

- **作者**: Wang  fuyin
- **时间**: 2026-11-14T16:13:03Z
- **提交信息**: [Bugfix] Preserve requested layer count for Ming-Image Design-Layer (#10318)

Signed-off-by: liuchenbing <chenliumail@163.com>
Signed-off-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: liuchenbing <chenliumail@163.com>
Co-authored-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>

### [a0ca658](https://github.com/vllm-project/vllm-omni/commit/a0ca65891eeb2847a2310ba94cb795c377aa0008)

- **作者**: Nikita Osterov
- **时间**: 2026-11-14T13:45:24Z
- **提交信息**: [Model] Add Kandinsky6 Distil and integrated HD/FHD generation (#9027)

Signed-off-by: Nikita Osterov <osipovmekete@gmail.com>
Signed-off-by: Nikita Osterov <90456300+osipovmekete@users.noreply.github.com>
Co-authored-by: SYLAR <125541396+lishunyang12@users.noreply.github.com>

### [b8f1281](https://github.com/vllm-project/vllm-omni/commit/b8f128171463eee11dfaa3b0513707d344851fe4)

- **作者**: Weiming Liao
- **时间**: 2026-11-14T09:40:46Z
- **提交信息**: [Model][Frontend] Add MiniMax-H3 character replacement ComfyUI workflow (H3-04) (#9194)

Signed-off-by: Isotr0py <2037008807@qq.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [fb0e212](https://github.com/vllm-project/vllm-omni/commit/fb0e2123ccddb0a95d11bb585deaf56d46c45e47)

- **作者**: lm10-arg
- **时间**: 2026-11-14T09:37:55Z
- **提交信息**: [CI/Build][Bugfix][ROCm] Complete shared TTS weekly coverage (#10350)

Complete shared CUDA/ROCm weekly TTS coverage, repair vLLM 0.33 compatibility gaps, and stabilize weak Higgs transcript validation. Exact-head CUDA #19685 and AMD #16166 passed with zero retries and zero soft failures.

### [e25c968](https://github.com/vllm-project/vllm-omni/commit/e25c9682a7315d9ecccb9c17266f21f2a0b31f81)

- **作者**: xiangrong zhong
- **时间**: 2026-11-14T07:26:51Z
- **提交信息**: [Core][Diffusion] Select attention profiles from scheduler noise (#8746)

Signed-off-by: zhongc1211 <huixindaddy@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e3649ff](https://github.com/vllm-project/vllm-omni/commit/e3649ffc2c7160844efd55b28128ad0837d3bd07)

- **作者**: y-null
- **时间**: 2026-11-14T07:19:21Z
- **提交信息**: [Model] Enable CUDA MRv2 K-step for MiniCPM-o 4.5 (#10288)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [05708d6](https://github.com/vllm-project/vllm-omni/commit/05708d6bbeaa4e340b33a267ea39ed6d664125af)

- **作者**: wangyu
- **时间**: 2026-11-14T06:47:20Z
- **提交信息**: [CI/Build] Tune CUDA merge timeouts and reorganize Qwen3-Omni tests (#10286)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your_email@example.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [79d0ce7](https://github.com/vllm-project/vllm-omni/commit/79d0ce74320f278f57e0dccd3eaf2ce7c13324fd)

- **作者**: lm10-arg
- **时间**: 2026-11-14T04:05:28Z
- **提交信息**: [CI/Build][ROCm] Add Ming GLM IndexTTS and Breeze weekly coverage (#10329)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [020ec34](https://github.com/vllm-project/vllm-omni/commit/020ec3415419b9902b029e11d393e713d19dd952)

- **作者**: MaciejBalaNV
- **时间**: 2026-11-14T03:53:36Z
- **提交信息**: [bugfix] Fix FA test_vllm_dense_adapter_cuda_matches_sdpa_and_lse test for Blackwell (#9217)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [9954edf](https://github.com/vllm-project/vllm-omni/commit/9954edf9aa16f70bbc07b603403db47375e6a583)

- **作者**: kunkun
- **时间**: 2026-11-14T03:15:50Z
- **提交信息**: [Core][Diffusion] Add the weight_stack package foundation (RFC #9536 01-1) (#9725)

Signed-off-by: kunkunblueberry <1833921874@qq.com>

### [a35dce9](https://github.com/vllm-project/vllm-omni/commit/a35dce9650e534ae9305b9debababf98b82ed104)

- **作者**: lm10-arg
- **时间**: 2026-11-14T02:37:07Z
- **提交信息**: [CI/Test] Repair FlashInfer CUDA contracts (#10346)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [b58f76c](https://github.com/vllm-project/vllm-omni/commit/b58f76c84688b4a18eafb69d797ea1a9a61502ba)

- **作者**: Yi Liu
- **时间**: 2026-11-14T01:05:12Z
- **提交信息**: [Model][Qwen-Image-2.1] ring SP: attend the replicated prefix locally (#10283)

Signed-off-by: Yi Liu <yi4.liu@intel.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>

### [e5d0978](https://github.com/vllm-project/vllm-omni/commit/e5d0978fb7520505ed94ca16142dfdca57794538)

- **作者**: Thanaji Rao Thakkalapelli
- **时间**: 2026-11-14T00:46:36Z
- **提交信息**: [Bugfix][GLM-Image] Route offline prompts through the AR multimodal processor (#7958)

Signed-off-by: Thanaji Rao Thakkalapelli <thanaji.rao.thakkalapelli@intel.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>

### [4284c22](https://github.com/vllm-project/vllm-omni/commit/4284c226cbae60fa339877db4c36cef1bad3fb34)

- **作者**: Chendi.Xue
- **时间**: 2026-11-14T00:12:22Z
- **提交信息**: [Kernel][Diffusion] Wan VAE fast path: one installer for every Wan-family VAE (#9553)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [bbf033d](https://github.com/vllm-project/vllm-omni/commit/bbf033d7f16fe04265b4488c61de61c48814ff6b)

- **作者**: Chendi.Xue
- **时间**: 2026-11-14T00:12:17Z
- **提交信息**: [Core] FlashInfer autotune for diffusion stages (on by default on SM100+) (#9998)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [d05e222](https://github.com/vllm-project/vllm-omni/commit/d05e222888ac51d84c3f7a2d9262d743b8be1272)

- **作者**: Chendi.Xue
- **时间**: 2026-11-14T00:12:13Z
- **提交信息**: [Perf] Wan2.2 S2V: compile the audio injection with the DiT blocks (#10077)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

---
