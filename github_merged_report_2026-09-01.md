# GitHub Stars 合并报告 - 2026-09-01

**合并日期**: 2026-09-02
**监控日期**: 2026-09-01
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


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2183
- **最后更新**: 2026-09-01T06:54:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2765
- **最后更新**: 2026-09-01T19:31:05Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: helloyongyang, Bilang ZHANG

## AI分析总结

### 主要更新类型
- **基础设施维护**：更新 Dockerfile
- **Bug 修复**：修复 MiniMax-H3 注意力机制中的首次步骤重编译问题

### 关键变更点与项目方向的关系
1. **Dockerfile 更新**：属于部署与开发环境优化，确保容器化环境与最新依赖、运行要求保持一致，降低用户上手门槛，符合项目“轻量级推理框架”的定位。
2. **MiniMax-H3 注意力修复**：针对特定模型架构（H3 注意力）在推理首步触发不必要的重编译，直接影响推理延迟与资源占用。这与项目核心目标——高效视频生成推理——高度一致。

### 对项目的影响与潜在意义
- **Dockerfile 更新**：提升可复现性与易用性，减少环境配置问题，间接加速社区采用与贡献。
- **重编译修复**：直接降低首次推理的启动延迟，尤其对交互式或低延迟场景（如实时视频生成）意义重大；同时减少编译开销，提升整体吞吐量。

### 值得关注的技术点
- **首次步骤重编译**：在动态形状或图模式推理中，首步常触发算子编译。修复表明项目在精细化控制编译时机，避免不必要的 JIT 开销，属于性能调优中的典型优化点。
- **H3 注意力**：MiniMax-H3 是较新的注意力变体，修复其特定路径问题，说明项目对新兴架构的适配与优化能力在增强。

### 对项目发展的影响
- 这两项提交虽小，但分别从**部署体验**和**推理性能**两个维度巩固了 LightX2V 作为轻量级、高效视频生成框架的竞争力。
- 持续修复特定模型（如 MiniMax-H3）的细节问题，有助于吸引更多模型生态用户，扩大框架适用范围。
- 整体上，提交体现了项目在“易用性”与“性能”双轨并进的维护节奏，为后续功能扩展和社区增长奠定基础。

## 详细提交记录

### [437b70c](https://github.com/ModelTC/LightX2V/commit/437b70c410d8dab5cf00ba5094b1a1bbff1e6287)

- **作者**: helloyongyang
- **时间**: 2026-09-01T16:01:21Z
- **提交信息**: update dockerfiles

### [26cfa87](https://github.com/ModelTC/LightX2V/commit/26cfa87782e109ffdccb20d5f437561cefa9a530)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-01T08:50:03Z
- **提交信息**: fix: prevent first-step recompilation in MiniMax-H3 attention (#1469)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2227
- **最后更新**: 2026-09-01T06:50:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6312
- **最后更新**: 2026-09-01T23:50:14Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: Ka-Hyun Nam, lunarz-dev, Jiahan Chang (Cyrus)

## AI分析总结

# FlashInfer 昨日提交分析总结

## 主要更新类型

本次提交涵盖**Bug修复**（4项）、**功能新增**（2项）、**文档更新**（1项）和**工程优化**（1项），整体以修复和兼容性完善为主。

## 关键变更点

1. **SM107 (Rubin) 架构适配修复**：修复TRTLLM生成器对SM107架构的过滤逻辑，并针对CuTe DSL 4.8以下版本增加NVFP4后端的降级保护，确保旧DSL在Blackwell上仍可用。
2. **Sparse-MLA SM120死锁修复**：通过交替使用CTA barrier 1和5解决因数学线程提前到达导致的IO线程饥饿问题，修复了GB10上的挂起缺陷。
3. **PrimTS无填充MLA查询行支持**：将无填充分组查询行工作移植到PrimTS注意力与MLA解码，支持非2的幂次查询头数，并重构了调度策略。
4. **MLA基准测试元数据对齐**：修复随机采样序列长度下MLA基准无法执行的问题。
5. **TRTLLM MOE NVFP4 TileN 192精度修复**：修复量化精度并更新cubins。
6. **JIT冷构建日志与文档完善**：新增NVCC JIT模块冷构建的INFO日志，补充0.6.19版本API文档覆盖。

## 对项目的影响

这些提交直接服务于FlashInfer作为**高性能GPU推理内核库**的核心目标。SM107修复和Sparse-MLA死锁修复提升了新硬件（Rubin、GB10）上的稳定性和可用性；PrimTS无填充支持扩展了注意力内核的适用场景；基准测试修复保障了性能评估的可靠性。

## 值得关注的技术点

- **CTA barrier交替策略**：利用tile奇偶性交替使用两个barrier ID，优雅规避PTX ISA对同一barrier重复到达的限制，是GPU并发编程的精细实践。
- **架构条件化降级**：仅对SM107内核要求新DSL，保持旧DSL在Blackwell上的完整功能，体现了良好的向后兼容设计。
- **调度策略简化**：移除经验性crossover表和评分机制，转向基于几何和容量约束的确定性调度，降低维护成本。

## 对项目发展的意义

这些提交体现了FlashInfer在**多架构支持**（Blackwell、Rubin、GB10）和**内核覆盖广度**（MLA、MoE、线性注意力）上的持续投入。通过修复新硬件上的关键缺陷、扩展内核功能边界并完善工程基础设施，项目正稳步向"覆盖最新GPU架构的高性能推理内核库"目标迈进，同时通过自动化标签和文档检查提升社区协作效率。

## 详细提交记录

### [11be76d](https://github.com/flashinfer-ai/flashinfer/commit/11be76db6dbdbcdc8695968d97756cb09d3a0a42)

- **作者**: Vincent
- **时间**: 2026-09-01T23:47:07Z
- **提交信息**: Rubin open issue fixes (#4787)

## 📌 Description

Four independent SM107 (Rubin) fixes found during bring-up. They are
unrelated to each other and can be reviewed separately.

### `fix(trtllm-gen)` — accept SM107 for the `Sm100f` family-conditional
target

`isArchCompatible` mapped `CudaArch::Sm100f` to `smVersion` 100 or 103,
omitting 107. `Sm100f` is the family-conditional target and is valid
across the whole SM100 line, so on sm107 the filter discarded every
family cubin. When the pinned pack also lacks native `Sm107a` entries
for the requested option sets, nothing matches at all.

### `fix(moe)` ×2 — decline the CuTe DSL NVFP4 backend when the DSL
predates 4.8

The SM107 gather/activation-fusion and finalize-fusion kernels are built
on `cutlass.utils.rubin_helpers`, which only exists from CuTe DSL 4.8.
Two entry points needed guarding, and they are genuinely distinct:

* `cute_dsl/tuner.py` covers the **autotuning** path — without it the
tactic import raises `ModuleNotFoundError` instead of simply being
declined, aborting autotuning rather than falling back.
* `fused_moe/runners.py` covers **backend selection**.
`_check_support()` previously checked only the activation type and the
W4A16 per-token scale, so on an older DSL the runner passed the support
check, survived `build()`, and entered `MoELayer.runners`; the failure
then surfaced from inside `forward()`. A direct `forward(tactic=-1)`
call bypasses tactic filtering entirely, so the tuner guard alone does
not cover it.

The `runners.py` probe is **arch-conditional on purpose**: only the
SM107 kernels need `rubin_helpers`, so an older DSL remains fully usable
on SM100/SM103 and gating unconditionally would drop a working backend
on Blackwell.

### `test(moe)` — skip SM107 parameterizations the CuTe DSL kernels do
not implement

`fused_moe/cute_dsl/rubin/` holds a narrower specialisation of the
Blackwell kernels rather than a port of them: the gather kernel
hardcodes SwiGLU and exposes no `activation_type`, its wrapper has no
`a_per_token_scale_ptr`, and the finalize kernel has no unfused path.
The resulting `NotImplementedError`s for `use_a_per_token_scale`,
`use_fused_finalize=False` and `GegluTanh` are accurate statements about
kernel code that does not exist — product gaps, not defects — but they
report as failures on every SM107 run.

No dispatch-level fix is possible, and that was measured rather than
assumed: the affected tests call `cute_dsl_fused_moe_nvfp4()` directly
and contain zero `MoELayer` references, so there is no backend selection
to influence.

The skip is decided **from the parameterization, before the test body
runs**, so it cannot absorb a genuine regression — anything failing for
a different reason still fails. The three parameters are parametrized
only in this file, so no other MoE test is affected.

## 🔍 Related Issues

None filed upstream.

**Split out of this PR:** a JIT cache fix (atomic publish of the linked
`.so` plus discard-and-rebuild recovery) was originally included here.
It is **not** SM107-specific — nothing in it is arch-conditional, and it
can strand any GPU whose node has an interrupted link left behind. It is
being carried separately so it is not reviewed as a Rubin change.

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

Validated on SM107 hardware:

| Change | Evidence |
|---|---|
| `fix(trtllm-gen)` | Controlled A/B, identical tree, only these lines
differing: unpatched 158 × "no kernels runnable on sm107", 79 failed / 2
passed → patched 0 × that error, 26 failed / **56 passed**. |
| `test(moe)` | Affected subset on SM107 hardware — before: **3 failed /
11 passed / 0 skipped**; after: **0 failed / 11 passed / 3 skipped**.
All three outcome counts checked against baseline, so the skips are
exactly the three known gaps and no passing test was lost. |

Additionally, the `fix(moe)` lazy-import paths were **executed** on
SM107 hardware (`_assert_rubin_cute_dsl_available()` runs, the probe
resolves and returns `True`, the guarded `.rubin` import succeeds). Its
*declining* branch remains unexercised — that needs a public CuTe DSL <
4.8 stack.

## Reviewer Notes

* **`fix(moe)`'s decline branch is still unexercised.** Its import paths
were executed on SM107 hardware, but the container ships CuTe DSL 4.8,
so the probe returns `True` and the decline never fires. Only a public
CuTe DSL 4.7.0 stack exercises it. An earlier revision of this commit
imported `is_rubin_cute_dsl_available` from `cute_dsl.availability`,
which exists on `release-v0.6.18` but **not** on `main`; because the
import is function-local, `py_compile` and `ruff` both passed and only a
runtime call would have caught it. It now imports from `cute_dsl.utils`,
which provides the symbol on both branches, verified by execution.

Four things I would rather flag than have a reviewer discover:

1. **`Sm100f` is not universally family-valid.** Twelve lines below the
changed filter there is already a carve-out — *"Sm100f cubins miss the
f2fp patch, so sm103 must fall back to Sm103a for it."* The sm107 case
is empirically fine, but a similar per-feature gap would need the same
treatment.

2. **One of two patched runs of the trtllm-gen A/B segfaulted** with
zero arch errors. The repeat completed normally and it did not reproduce
— plausibly a known IMA class for that cubin pin rather than this change
— but it is 1-in-2 and worth watching in CI rather than dismissing.

3. * One case is matched by function identity, not by parameter.**
`test_geglu_tanh_accuracy` sets its activation in the test body rather
than via a parameter, so it is matched with
`request.node.function.__name__ == "test_geglu_tanh_accuracy"`. An
earlier revision used a substring match on `"geglu_tanh"`, which also
caught `test_geglu_tanh_activation_is_supported` — a pure-Python
assertion about `normalize_cute_dsl_moe_activation_type` that touches no
kernel and passes on SM107. That silently cost one passing test; the
exact match restores it, confirmed by the pass count above.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved fused MoE autotuning on Rubin (SM107) hardware by gracefully
falling back when required kernel support is unavailable.
* Added compatibility checks to prevent unsupported Rubin configurations
from causing failures.
* **Tests**
* Updated coverage for Rubin-specific capabilities and unsupported
feature combinations.
  * Enabled Rubin paths in relevant fused MoE autotuning tests.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5214b1f](https://github.com/flashinfer-ai/flashinfer/commit/5214b1ff518a680170b4381a3545d3b006b6eac3)

- **作者**: kangbintNV
- **时间**: 2026-09-01T19:30:41Z
- **提交信息**: docs: fix 0.6.19 document check failures (#4871)

## Summary

Fix the blocking findings in the FlashInfer 0.6.19 documentation check
report:

- add RST coverage for Cake VSA, FP8 per-channel MoE, and SSDCombined
APIs
- document recurrent KDA training forward/backward parameters and the
GDN CP chunk override
- document the two Blackwell MSA schedule environment variables
- correct the stale custom-routing source path in `CLAUDE.md`

The 41 `STALE` warnings are intentionally left unchanged. This PR does
not add `@flashinfer_api` decorators or otherwise change those API
classifications.

Report:
http://dlswqa-nas:8080/cudnn/flashinfer/flashinfer_document_check_report/flashinfer_0.6.18_0b79dc1b_doc_check_result.html

## Validation

- full API/RST checker: `MISSING 0`, `STALE 41` (unchanged warnings)
- docstring checker: `0` completeness failures, `0` args-consistency
failures
- cross-source target checks: `0` env-var failures and `0` quick-ref
path failures
- PR documentation checker against `origin/main`: `findings: []`
- `pre-commit run --files ...`: passed (mypy, ruff, formatting, and
repository hygiene hooks)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Documentation**
- Expanded API reference coverage for fused mixture-of-experts, Mamba,
and Cake VSA functionality.
- Added detailed parameter and return-value documentation for recurrent
KDA training operations.
- Documented new environment-variable controls for MSA scheduling and
routing behavior.

- **New Features**
- Added an optional context-parallel chunk-length override for gated
delta-rule prefill, supporting tuning and testing with validated chunk
sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f768e63](https://github.com/flashinfer-ai/flashinfer/commit/f768e63281c2044f9549512d8c9232c6ea594417)

- **作者**: Misha Goin
- **时间**: 2026-09-01T19:25:53Z
- **提交信息**: feat(jit): log cold nvcc module builds (#4844)

## Summary

Log one INFO message before a cold NVCC JIT module build. Prebuilt and
local JIT cache hits remain quiet.

## Tests

- Focused JIT tests
- Pre-commit on changed files

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an informational message when a JIT module is built for the
first time, including an indication that the process may take several
minutes.
  * Existing compiled artifacts and cache hits remain silent.

* **Documentation**
* Documented how to control JIT build progress messages through the
logging level setting.
* Clarified that this setting is independent of API logging
configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: mgoin <mgoin64@gmail.com>

### [d209081](https://github.com/flashinfer-ai/flashinfer/commit/d2090811b8b11a9934f4d2ccc823b583e732bffc)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-01T18:25:30Z
- **提交信息**: [bug fix] Issue 3700 sparse mla sm121 hang (#4732)

<!-- .github/pull_request_template.md -->

## 📌 Description

Sparse-MLA SM120 prefill uses CTA barrier 1 as an asymmetric handshake
(count 384): 256 math threads `barrier.cta.arrive` (non-blocking), 128
IO threads `barrier.cta.sync`. Math can arrive for tile `ti`, run
`ti+1`, and arrive **again** before IO syncs `ti`. The PTX ISA warns
against exactly that (`arrive` then another `barrier.cta` on the same id
before reset). The surplus arrival completes the phase without IO; a
later phase starves. Captured on GB10: IO warps parked on `BAR.SYNC 1,
384` after math had exited.

Fix: alternate the handshake between ids **1 and 5** by tile parity
(`bar_arrive_alt` / `bar_sync_alt`) at all five call sites. A run-ahead
tile lands on the other id. Two ids suffice because math cannot start
tile `ti` until IO has returned from the sync for `ti-2`, so at most one
arrival is outstanding per id.

Ungated: this is an invalid arrival pattern, not an sm_121 quirk. The
hang is only demonstrated on GB10; the kernel is SM12x-only.

## 🔍 Related Issues

Closes #3700

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

GB10 / sm_121: `pytest tests/attention/test_sparse_mla_sm120.py` → **309
passed**. Single-process soak on `heads=128, topk=1024, tokens=256`:
baseline **5/5 hung** (usually tens of iterations, sometimes a few
hundred); fix **5/5 × 30k, 0 hangs**. Two concurrent pytest (`-k
"prefill_glm_nsa_arbitrary_fp32 or prefill_dsv4"`): baseline wedged in
round 3; fix **12/12 clean**. All four instantiated prefill variants
soaked 30k each (with `assert_close`); 30k bitwise-identical iterations
vs a golden result (fix does not turn the hang into silent corruption).
No new unit test — the race is a soak, not a unit.

Header-only change: ninja may serve a stale `.so` (no `.d` depfiles).
Delete `csrc_sparse_mla_sm120_prefill.cuda.o` and `sparse_mla_sm120.so`
and confirm the `.so` mtime advances before A/B. Wedged processes ignore
`SIGTERM`; use `timeout -s KILL`.

### [f1e2a5c](https://github.com/flashinfer-ai/flashinfer/commit/f1e2a5ce7af2bac5558299b13a1a4ddebc486b55)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-01T18:03:53Z
- **提交信息**: Add PR labeler rules for op: linear attention and op: misc (#4852)

## Summary
- Auto-apply `op: linear attention` when a PR touches GDN, Mamba, or KDA
sources, tests, docs, or benches.
- Auto-apply `op: misc` for the remaining small ops: norm, activation,
sampling (including top-k, topk-varlen, logits processor, and sampling
softmax), RoPE, and quantization.
- Both labels already exist on the repo; this only extends
`.github/labeler.yml`. Path globs avoid MoE, GEMM, comm, and
attention-internal files so those `op:` labels stay primary.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Chores**
- Added automatic labeling for linear-attention-related changes,
including GDN, Mamba, and KDA.
- Added automatic labeling for miscellaneous model operations, including
normalization, activation, sampling, top-k processing, logits
processing, RoPE, and quantization.
- Labels now apply across implementation, tests, documentation, and
benchmark changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [eddd39c](https://github.com/flashinfer-ai/flashinfer/commit/eddd39c7e1343c3e3019be51678fca5967aee584)

- **作者**: lunarz-dev
- **时间**: 2026-09-01T17:30:40Z
- **提交信息**: fix(benchmark): align MLA metadata with backend contracts (#4835)

## 📌 Description

Flatten sampled KV lengths before planning MLA backends and pass page
tables only to CUTLASS.

This allows the benchmark harness to use the metadata representation
required by each planned MLA backend.

Objective: Restore execution of MLA benchmark cases with randomly
sampled sequence lengths.

Scope: Updates only the MLA benchmark routine and its regression test;
production MLA backend implementations are unchanged.

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/4833

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have run `pre-commit run --all-files` and fixed any reported
issues.

## 🧪 Tests

- [x] B300 MLA benchmark cases completed with non-empty results for
batch sizes 1 and 16.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved MLA paged-attention benchmark compatibility by passing
key/value sequence lengths in the expected format.
* Updated backend-specific argument handling for more reliable
FlashAttention and CUTLASS benchmark execution.

* **Tests**
* Added regression coverage for MLA benchmarks with a single query
token.
* Verified that each backend receives correctly shaped attention
metadata.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9d0e6f8](https://github.com/flashinfer-ai/flashinfer/commit/9d0e6f82ffa23d4271c08e0e0d4fc638b6b707ea)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-09-01T09:53:53Z
- **提交信息**: Fix TRTLLM MOE per-token NVFP4 TileN 192 and update cubins (#4741)

<!-- .github/pull_request_template.md -->

## 📌 Description

1. Fix TRTLLM MOE per-token NVFP4 TileN 192 accuracy
2. Update cubins to fix MXFP8 Quant

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
* Improved NVFP4 mixture-of-experts support by enabling additional tile
configurations, including tile size 192.
* Improved scale-factor layout handling for quantized matrix
multiplication and mixture-of-experts execution.

* **Bug Fixes**
* Corrected scale-factor layout selection to reflect the active kernel
configuration.
* Improved weight preparation cache separation for gated and non-gated
activation paths.

* **Chores**
* Updated the bundled TRTLLM generated matrix multiplication artifact
and its integrity verification.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0b79dc1](https://github.com/flashinfer-ai/flashinfer/commit/0b79dc1b09f24632179e0d4d231c3a981d5556d5)

- **作者**: Perkz Zheng
- **时间**: 2026-09-01T07:01:54Z
- **提交信息**: feat(prims_ts): support no-padding MLA query rows (#4830)

## Summary

Port the no-padding grouped query-row work to PrimTS attention and MLA
decode, covering both throughput-latency 1CTA and throughput 2CTA
kernels.

## Features

- Flatten `(query token, query head)` into physical query rows without
padding.
- Support fixed and packed Q layouts, including empty packed requests.
- Support non-power-of-two query-head counts such as H6, H12, H24, H48,
and H96.
- Make context, FMHA decode, and MLA compiled callables batch-dynamic
while keeping workspace sizing plan-specific.
- Reuse compiled topologies across batch sizes when their static
scheduler/reducer topology is unchanged.

## Dispatch policy

- Select the 1CTA query tile from flat query geometry only.
- Derive split-KV from K-step work, resident capacity, and the shared
128-split implementation limit.
- Use 2CTA above the native M64 1CTA row boundary.
- Within M64, select 2CTA only when 1CTA requires split reduction and
2CTA can produce direct output.
- Remove dtype-, shape-, and measurement-specific crossover tables,
power-of-two split rounding, and candidate scoring.

A few structural performance outliers are intentionally retained rather
than adding case-specific dispatch exceptions.

## Correctness fixes

- Predicate partial flat-query tails and empty runtime tiles.
- Apply causal masking using logical query rows.
- Preserve scheduler progress for multiwave and empty-tile launches.
- Correct split-workspace addressing and runtime-K pruning.
- Keep producer and standalone-reducer topology/capacity consistent.
- Use the fixed qualified reference-reducer launch geometry.

## Validation

| Validation | Result |
|---|---|
| Repository-wide pre-commit | Passed |
| Affected host suites | 178 passed, 286 skipped |
| CUDA 13.4 / B200 PrimTS MLA suite | 144 passed |
| Issue #4390 backend matrix | 72/72 refchecks |
| PrimTS wins in issue #4390 matrix | 24/24 |
| CuTe DSL / PrimTS geometric mean | 1.4288 |
| CuTe DSL / PrimTS minimum | 1.0832 |
| Representative 28-cell policy A/B geometric mean | 1.0851 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for empty and partially empty packed-query requests,
including safe no-op handling for all-empty batches.
* Expanded MLA decode support for additional query-head counts and
non-power-of-two configurations.
* Improved compiled-kernel reuse across batch sizes and runtime metadata
sizes.
  * Added automatic scheduler and split-KV topology selection.

* **Bug Fixes**
* Improved causal masking, variable-length query handling, split-KV
reduction, and padded-row processing.
  * Prevented unnecessary work for empty attention tiles.

* **Documentation**
* Clarified workspace reinitialization requirements, including after
batch-size changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4267
- **最后更新**: 2026-09-01T23:31:41Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Ishan, William Lin, Aryan Kumar

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以**功能新增**和**文档更新**为主，包含少量界面优化，未涉及Bug修复或性能优化。

### 2. 关键变更点及与项目方向的关系
- **FastH3本地支持与多机部署**（#1809、#1803）：新增FastH3在本地环境及跨两台DGX Spark服务器（通过Ray序列并行）的运行能力。FastH3是视频生成领域的高效架构，该功能直接强化了FastVideo作为**高性能视频生成框架**的核心定位，扩展了其在大规模多节点环境下的可用性。
- **Cookbook文档重构**（#1805）：将配方页面改为手风琴折叠布局，提升文档浏览效率；同时在README中新增Cookbook链接（#1810），降低新用户上手门槛。

### 3. 对项目的影响与潜在意义
- **技术影响力**：多机Ray并行支持使FastVideo具备处理超长视频或高分辨率生成任务的能力，吸引需要大规模算力的研究团队。
- **社区友好度**：文档布局优化和入口增强，配合README中已有的Cookbook、快速开始等资源，形成更清晰的学习路径，有助于扩大用户基础。
- **生态完善**：本地FastH3支持意味着用户无需依赖特定云环境即可复现实验，提升项目可移植性和可信度。

### 4. 值得关注的技术点
- **Ray序列并行**：跨节点并行策略是视频生成训练/推理的关键优化方向，该实现可能涉及序列切分、通信开销平衡等复杂设计。
- **FastH3架构适配**：本地与多机支持需处理硬件差异（如DGX Spark的特定GPU配置），体现了对异构环境的兼容性考量。
- **AI辅助协作**：提交中出现的Claude Sonnet/Opus共同作者，反映项目正采用AI辅助编码流程，可能加速功能迭代。

### 5. 对项目发展的影响
结合README中强调的“快速视频生成”与“多平台支持”目标，本次提交通过**扩展硬件适配范围**和**优化文档体验**双管齐下：前者巩固了FastVideo在专业视频生成工具中的技术优势，后者则通过降低使用门槛吸引更多开发者参与。多机并行能力尤其为未来支持更大规模视频生成模型（如长视频、高帧率）奠定了基础，与项目持续演进的方向高度一致。整体来看，这些变更属于**基础设施完善与生态建设**阶段的关键步骤，为后续高级功能开发铺平道路。

## 详细提交记录

### [40b9378](https://github.com/hao-ai-lab/FastVideo/commit/40b93784d25cf21174e7db54bb11826e514bab4d)

- **作者**: William Lin
- **时间**: 2026-09-01T19:42:19Z
- **提交信息**: [docs]: add cookbook link to README (#1810)

### [33d3478](https://github.com/hao-ai-lab/FastVideo/commit/33d3478bad67844dbb1696f841badc3f0b0eb266)

- **作者**: Aryan Kumar
- **时间**: 2026-09-01T19:28:04Z
- **提交信息**: [docs] Announce local FastH3 support (#1809)

### [3d8ac9d](https://github.com/hao-ai-lab/FastVideo/commit/3d8ac9d14bd697a89ede8f170cbfbca012a9edcc)

- **作者**: Ishan
- **时间**: 2026-09-01T08:51:51Z
- **提交信息**: [feat]: collapse cookbook recipe pages into an accordion layout, add … (#1805)

Co-authored-by: Vaish, Ishan <isvaish@UCSD.EDU>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [aaef49b](https://github.com/hao-ai-lab/FastVideo/commit/aaef49bfc610a96c009df870fc7963d9e9f4a205)

- **作者**: Aryan Kumar
- **时间**: 2026-09-01T08:37:23Z
- **提交信息**: [feat]: run FastH3 across two DGX Sparks with Ray sequence parallel (#1803)

Co-authored-by: Kyle <shh075@ucsd.edu>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Satyam Srivastava <srivastavasatyam53@gmail.com>
Co-authored-by: Aryan Kumar <aryan5v@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34419
- **最后更新**: 2026-09-01T16:37:56Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: iridescentWen, Sayak Paul

## AI分析总结

### 主要更新类型
- **文档更新**：修正Chroma pipeline文档字符串中的默认值描述。
- **重构/弃用**：正式弃用ONNX相关支持。

### 关键变更点及与项目方向的关系
1. **Chroma文档修正**：修复了三个Chroma pipeline的`__call__`文档中七处错误的默认值声明，使文档与实际签名一致。这属于质量改进，确保用户按文档操作时行为可预测，符合diffusers作为易用库的定位。
2. **ONNX弃用**：标记ONNX为弃用状态，表明项目正逐步淘汰该集成路径。这与diffusers聚焦于PyTorch原生生态、简化维护范围的战略一致，可能为未来架构精简铺路。

### 对项目的影响和潜在意义
- **文档修正**：减少用户因文档误导而产生的配置错误，提升开发者体验，降低支持成本。
- **ONNX弃用**：短期可能影响依赖ONNX导出的用户，但长期可减少维护负担，集中资源于核心功能（如新模型架构、训练/推理优化）。弃用通知也为用户提供迁移窗口，避免突然破坏。

### 值得关注的技术点
- 文档修正体现了对API契约严谨性的重视，尤其对默认值这类易被忽略但影响行为的细节。
- ONNX弃用可能伴随后续移除代码，需关注是否有替代方案（如通过`optimum`等外部库支持），以及是否影响跨框架部署场景。

### 对项目发展的影响
基于README，diffusers旨在提供易用的扩散模型工具。本次提交中，文档修正直接服务于“易用性”目标；ONNX弃用则反映项目在成熟期对技术栈的取舍——优先保障核心PyTorch体验，减少多后端兼容的复杂度。这有助于项目保持代码库整洁，加速新特性迭代，但需谨慎管理弃用流程，避免社区碎片化。整体上，这些变更属于渐进式优化，巩固了项目作为主流扩散模型库的地位。

## 详细提交记录

### [bda3386](https://github.com/huggingface/diffusers/commit/bda3386ddcaa31bc2853567a95e815629c8022b7)

- **作者**: iridescentWen
- **时间**: 2026-09-01T16:12:34Z
- **提交信息**: docs: correct stated defaults in Chroma pipeline docstrings (#14578)

Seven `defaults to X` entries in the three Chroma pipelines' __call__
docstrings name a value the signature does not use, so copying the
documented number reproduces different behavior than leaving the argument
out. Values taken from each __call__ signature.

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7c79e70](https://github.com/huggingface/diffusers/commit/7c79e7060750eb35c19bd8fcc7aaca57e692ae48)

- **作者**: Sayak Paul
- **时间**: 2026-09-01T12:54:03Z
- **提交信息**: [core] deprecate onnx (#14658)

* deprecate onnx

* up

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13033
- **最后更新**: 2026-09-01T21:13:13Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 提交分析（4dbf980）

## 主要更新类型
本次提交为**版本发布更新**，将项目版本从先前版本升级至 **2.1.6**，属于常规的版本迭代与功能整合发布。

## 关键变更点
提交信息仅包含版本号更新（`update to version 2.1.6`），未在提交信息中详细列出具体变更内容。结合项目背景，此类版本更新通常涵盖：
- 新功能的集成与完善
- 已有功能的优化与调整
- Bug修复与稳定性提升
- 依赖库的更新与兼容性调整

## 对项目的影响与潜在意义
版本号从 2.x 系列推进至 2.1.6，表明项目处于**持续活跃迭代**状态。对于 DiffSynth-Studio 这类面向视频合成与编辑的开源工具，版本更新意味着：
- 用户可获得更稳定的使用体验
- 新特性能够及时触达社区用户
- 项目保持对生态依赖（如 PyPI 发布）的同步更新

## 值得关注的技术点
由于提交信息未披露具体技术细节，值得关注的方向包括：
- 版本 2.1.6 是否包含对底层扩散模型推理性能的优化
- 是否新增了视频风格化或编辑相关的算法能力
- 是否修复了已知的兼容性问题（如特定 GPU 环境或依赖版本冲突）

## 对项目发展的影响
DiffSynth-Studio 定位为**创意视频合成工具**，强调趣味性与易用性（README 中展示 logo 动图及 Trendshift 榜单）。此次版本更新延续了项目**高频迭代、快速响应社区需求**的发展节奏。持续的小版本更新有助于：
- 巩固其在开源视频生成工具领域的竞争力
- 吸引更多开发者参与贡献
- 保持与 ModelScope 生态的紧密协同

总体而言，这是一次常规但重要的版本推进，体现了项目维护的活跃度和对用户反馈的积极响应。

## 详细提交记录

### [4dbf980](https://github.com/modelscope/DiffSynth-Studio/commit/4dbf980d4d0eb34eda136300dd0d72014cff8965)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-01T10:52:30Z
- **提交信息**: update to version 2.1.6 (#1662)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 33058
- **最后更新**: 2026-09-02T00:11:48Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 31
- **主要提交者**: DarkSharpness, datdo-msft, weireweire

## AI分析总结

# sglang 仓库提交分析报告

## 一、主要更新类型

本次提交涵盖**Bug修复**（约12项）、**性能优化**（约8项）、**功能新增**（约6项）、**文档/Cookbook更新**（约6项）、**CI改进**（约4项）及**代码重构**（约3项），整体呈现多维度并行推进态势。

## 二、关键变更点与项目方向

1. **Kernel层优化**：替换dsv3_router_gemm为统一tiny GEMM、融合softmax路由避免零偏置分配、新增LFM2.5 Triton MoE配置，体现对核心计算路径的持续精调。
2. **AMD/ROCm生态强化**：修复AITER topk kernel、启用topk v2 GLM、增加ROCm 10和7.2测试覆盖，表明对AMD平台支持力度显著加大。
3. **FlashInfer集成深化**：支持DSA top-k后端、避免滑动窗口长度的D2H同步、接受int64 top-k ID，推动推理后端多样化。
4. **内存管理改进**：基于预热测量确定CUDA graph池大小、新增`free_kv_row`按行范围释放、移除SWA页面扩展中的`torch.unique`同步，提升内存效率。
5. **NPU支持完善**：修复MLA HiCache备份、为视觉编码器填充序列去填充，扩展硬件适配范围。

## 三、项目影响与潜在意义

- **多硬件平台战略加速**：AMD、NPU、ROCm相关提交占比超25%，配合CI测试覆盖扩展，sglang正从NVIDIA单平台向多架构兼容演进。
- **推理性能持续突破**：Kernel融合、内存分配优化、异步化改造（避免同步点）共同指向更低延迟和更高吞吐。
- **生态兼容性增强**：FlashInfer、AITER、MLX等多后端适配，配合Cookbook新增DeepSeek-V4、GLM-5.3等热门模型配方，降低用户使用门槛。

## 四、值得关注的技术点

1. **统一tiny GEMM替换专用kernel**：简化代码维护同时可能带来性能一致性提升。
2. **CUDA graph池自适应大小**：从预热测量而非静态配置，更贴合实际负载。
3. **解码上下文并行支持Kimi-Linear**：针对长上下文模型的关键优化。
4. **DSA top-k后端扩展**：FlashInfer融合top-k与现有DSA路径，体现模块化设计思想。
5. **Rust组件重命名**（mem-cache→sglang-radix-tree）：反映架构演进中的命名规范化。

## 五、对项目发展的综合影响

结合README中sglang作为**高性能、多硬件推理框架**的定位，这些提交清晰展示了三条发展主线：**一是持续巩固NVIDIA平台性能优势**（Kernel优化、FlashInfer集成）；**二是积极拓展AMD/ROCm和NPU生态**，抢占多元化硬件市场；**三是通过Cookbook和文档建设降低采用门槛**，吸引更广泛用户群体。内存管理和CI稳定性改进则为大规模部署提供了坚实基础。整体来看，项目正处于**性能精调与生态扩张并重**的成熟阶段，技术深度和广度同步提升，有望在LLM推理框架竞争中保持领先地位。

## 详细提交记录

### [221a627](https://github.com/sgl-project/sglang/commit/221a6273ce3212c79483df233b4511fdf8fbe6d0)

- **作者**: YAMY
- **时间**: 2026-09-01T23:29:57Z
- **提交信息**: [Kernel] Avoid zero-bias allocation in fused softmax routing (#36811)

### [ed82bea](https://github.com/sgl-project/sglang/commit/ed82bea1464d8ef66ed2b3ff6d9fc06c2e18ee60)

- **作者**: Jimmy Shong
- **时间**: 2026-09-01T22:42:39Z
- **提交信息**: [Cookbook] DeepSeek-V4: add DGX Spark (2x GB10) Flash Official FP4 recipe (#37479)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9978aae](https://github.com/sgl-project/sglang/commit/9978aaec8bd7efdd46a9080e9700b0af15b2573f)

- **作者**: Yikai Zhang
- **时间**: 2026-09-01T22:40:12Z
- **提交信息**: [ROCm][Bugfix] Cap the DSA MQA-logits budget at AITER's buffer_store limit (#36960)

Co-authored-by: amdpilot-upstream-sync <amdpilot-upstream-sync@users.noreply.github.com>

### [f861871](https://github.com/sgl-project/sglang/commit/f8618714c5f3ebf53db16790dc7288c032827587)

- **作者**: Akash Palla
- **时间**: 2026-09-01T22:26:47Z
- **提交信息**: add reindex_device_id to device OOT plugin (#36220)

Co-authored-by: Akash Palla <apalla@fb.com>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [fb8d7ee](https://github.com/sgl-project/sglang/commit/fb8d7eedda98617b743ecd6c5e03bd391e8ee994)

- **作者**: weireweire
- **时间**: 2026-09-01T21:19:14Z
- **提交信息**: Fix dummy initialization of inverse weight scales (#35491)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [e57e934](https://github.com/sgl-project/sglang/commit/e57e934bcc5c1db616b01a08c9ff83735674ac2d)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-09-01T21:17:46Z
- **提交信息**: [Bugfix] Accept int64 top-k IDs in FlashInfer routed MoE packer (#32882)

### [83a9b5d](https://github.com/sgl-project/sglang/commit/83a9b5dd8886fa972324304ce0cc8acfebc0d022)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-01T21:16:47Z
- **提交信息**: [mem_cache] Drop the `torch.unique` sync from the SWA page expansion (#37463)

### [b24c8f1](https://github.com/sgl-project/sglang/commit/b24c8f10e71b936dbb2a7fbfd1c76cb4afe53c10)

- **作者**: lynn.lin
- **时间**: 2026-09-01T21:08:22Z
- **提交信息**: [FlashInfer] Avoid D2H sync for sliding-window lengths (#32218)

Co-authored-by: llilian73 <204300658+llilian73@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [0f18d38](https://github.com/sgl-project/sglang/commit/0f18d389b46bdb8d8860481019f55b402ec65a06)

- **作者**: zijiexia
- **时间**: 2026-09-01T20:09:14Z
- **提交信息**: [Cookbook] Verify DeepSeek-V4 Flash Vision balanced and high-throughput on B200 (#37468)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [442c7c1](https://github.com/sgl-project/sglang/commit/442c7c1e299790b1452977432a4762fc30dcd8ef)

- **作者**: Xinyuan Tong
- **时间**: 2026-09-01T19:56:22Z
- **提交信息**: [Docs] GLM-5.3-Flash cookbook: add NVFP4 FP8+TRT-LLM benchmark rows (follow-up to #37109) (#37412)

### [0b1ce3d](https://github.com/sgl-project/sglang/commit/0b1ce3d140c4faab4cab1eae3d9051fb49772e9a)

- **作者**: Cheng Wan
- **时间**: 2026-09-01T19:44:26Z
- **提交信息**: [Feature] Unified memory: support decode context parallelism for Kimi-Linear (#36890)

### [3315356](https://github.com/sgl-project/sglang/commit/3315356cc043d621c83df5ff5f989adc9ce7b623)

- **作者**: Ankur Singh
- **时间**: 2026-09-01T18:48:41Z
- **提交信息**: docs(cookbook): enable FlashInfer GDN for Qwen3.5 B200 (#37360)

### [a2b8681](https://github.com/sgl-project/sglang/commit/a2b8681d1d9092eccf569da0c932d3a1f3ba9c87)

- **作者**: Shuwen Wang
- **时间**: 2026-09-01T18:16:45Z
- **提交信息**: [CI][MLX] Restore the mamba_branching_seqlen attribute the MLX runner reads off a request (#37453)

### [9a05b47](https://github.com/sgl-project/sglang/commit/9a05b470fa849b349e384ef3c1381f9a85c6c550)

- **作者**: cctry
- **时间**: 2026-09-01T16:32:38Z
- **提交信息**: [Memory] Size the CUDA graph pool from warmup measurements and fix graph-pool borrowing (#36911)

Co-authored-by: cctry <cctry@fb.com>

### [c34f378](https://github.com/sgl-project/sglang/commit/c34f378342500970c514c8613e8498d61faa58f6)

- **作者**: hekhong-png
- **时间**: 2026-09-01T16:11:59Z
- **提交信息**: fix(nixl): make FILE path-mode devId globally unique (#34362)

Co-authored-by: hekh <hekh@local>
Co-authored-by: Claude <noreply@anthropic.com>

### [bb3e3cb](https://github.com/sgl-project/sglang/commit/bb3e3cbceb510b05109d3dfdcbbd07a1a2905314)

- **作者**: Thomas Wang
- **时间**: 2026-09-01T15:37:30Z
- **提交信息**: [AMD] Fix v4 topk issue (#37439)

### [44a92e5](https://github.com/sgl-project/sglang/commit/44a92e54b9efdd56be68a915ed717f4964f2e6ab)

- **作者**: billishyahao
- **时间**: 2026-09-01T15:35:31Z
- **提交信息**: [AMD] fix aiter cannot get heuristic kernel regression (#37438)

### [cb6dd58](https://github.com/sgl-project/sglang/commit/cb6dd58fbeca2df1fce2c6ca90c4553aec099f60)

- **作者**: DarkSharpness
- **时间**: 2026-09-01T15:00:21Z
- **提交信息**: [Kernel] Replace dsv3_router_gemm with the unified tiny GEMM (#34693)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [ee462b5](https://github.com/sgl-project/sglang/commit/ee462b5899c02db4e9d250f43c4c54d81253c4c6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-01T14:55:38Z
- **提交信息**: [Kernel] Add tuned LFM2.5 Triton MoE configs on B300 (#37158)

Co-authored-by: Song Bian <biansonghz@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [5993f91](https://github.com/sgl-project/sglang/commit/5993f91f843c3429b0e3bdf21bf05a9f1236f731)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-01T14:51:10Z
- **提交信息**: [Kernel] Register merged diffusion agent kernels with KDA backend (#37385)

### [4c7ff0d](https://github.com/sgl-project/sglang/commit/4c7ff0d90675fcc8058d98706af53c68e4559036)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-01T14:37:37Z
- **提交信息**: [CI] Double JIT kernel unit test timeout (#37435)

### [b6c06e1](https://github.com/sgl-project/sglang/commit/b6c06e1efb601f4c5c82b34b232546596ea5fdd8)

- **作者**: DarkSharpness
- **时间**: 2026-09-01T14:37:03Z
- **提交信息**: [DSA] Drop the redundant 512 from the top-k transform entry-point names (#36831)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [00689c0](https://github.com/sgl-project/sglang/commit/00689c0c947e5e5312993df58e89bd04245d6742)

- **作者**: Even Zhou
- **时间**: 2026-09-01T14:08:00Z
- **提交信息**: [CI] Add entrypoint to hc_combine test for standalone execution (#37406)

### [3ae54c6](https://github.com/sgl-project/sglang/commit/3ae54c6ca2655b4e72deb0b4001b862d43a57c3b)

- **作者**: Sugar920
- **时间**: 2026-09-01T14:00:04Z
- **提交信息**: test(npu): add DSV4-Flash / GLM-5.2 / Kimi-K3 gpqa accuracy cases (#37431)

Co-authored-by: Sugar920 <Sugar920@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4c2c169](https://github.com/sgl-project/sglang/commit/4c2c169e6ba15aee5408b250ce25ff7e73388d9b)

- **作者**: Estrella-xx
- **时间**: 2026-09-01T11:28:19Z
- **提交信息**: [NPU]Strip padding before FIA kernel for vision encoder padded sequences (#36329)

### [3103bc7](https://github.com/sgl-project/sglang/commit/3103bc746269a80f7fa0fd0707c780db9b9f852f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-01T11:23:19Z
- **提交信息**: [AMD][CI] Add daily ROCm 10 and ROCm 7.2 test coverage (#37409)

Co-authored-by: Chen <bingxche@amd.com>

### [ce7e79b](https://github.com/sgl-project/sglang/commit/ce7e79b32c5dc3e2c7536dbe7f3b4e041195c1a6)

- **作者**: Michael
- **时间**: 2026-09-01T11:06:32Z
- **提交信息**: [AMD] Fix nightly ROCm 7.0 image build: patch missing <optional> include in AITER topk kernel (#36216)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: quitenode <quitenode@users.noreply.github.com>
Co-authored-by: Chen <bingxche@amd.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [ed122ea](https://github.com/sgl-project/sglang/commit/ed122ea984c4fe9bdd974a1043947977816a35d8)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-09-01T10:48:50Z
- **提交信息**: [AMD] Enable topk v2 GLM ROCm (#36851)

Co-authored-by: KingRei <hiroki1139@gmail.com>

### [b425897](https://github.com/sgl-project/sglang/commit/b425897366767d9f4a55e4bf67de7e6cb8d8b7c6)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-09-01T10:46:15Z
- **提交信息**: [AMD] Gate the aiter memory-reserve exemption behind an env var (#37242)

### [49db275](https://github.com/sgl-project/sglang/commit/49db27528a966d001df467c7017c8ca28c40fead)

- **作者**: datdo-msft
- **时间**: 2026-09-01T10:14:55Z
- **提交信息**: fix(test): deflake zmq load-snapshot round-trip tests (#35787)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [a77283f](https://github.com/sgl-project/sglang/commit/a77283fb02843669e1f534a24e59baa39e38de22)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-01T10:03:44Z
- **提交信息**: [Rust] Rename mem-cache to sglang-radix-tree (#37290)

### [c16a8fc](https://github.com/sgl-project/sglang/commit/c16a8fc89995a93f683c71f4aa7eb49b1000d104)

- **作者**: chx96642264
- **时间**: 2026-09-01T09:31:11Z
- **提交信息**: [NPU] [bugfix] Fix NPU MLA HiCache backup accessing missing data_ptrs. (#36813)

### [dc1ae02](https://github.com/sgl-project/sglang/commit/dc1ae02684d496c83d032fca3d77b232dfdcc6f0)

- **作者**: zijiexia
- **时间**: 2026-09-01T09:08:28Z
- **提交信息**: [Cookbook] Add the DFlash2 speculative option to GLM-5.3 (#37392)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [b68702b](https://github.com/sgl-project/sglang/commit/b68702be99969e28fd103b60d83d3edd9415ba32)

- **作者**: eeecho
- **时间**: 2026-09-01T09:04:05Z
- **提交信息**: [DSV4] hc-prenorm: fuse the combine step into a Triton kernel (#35118)

### [6c72b49](https://github.com/sgl-project/sglang/commit/6c72b49a579605c123d9e667669aee1c8919f076)

- **作者**: zijiexia
- **时间**: 2026-09-01T08:25:13Z
- **提交信息**: Revert "[AMD] Add GLM-5.3-Flash recipes for MI300X, MI325X, and MI355X (#36608)" (#37380)

### [5edcd0a](https://github.com/sgl-project/sglang/commit/5edcd0a445bdfb8f1980000eaf0474fcfb8e33aa)

- **作者**: Ziang Li
- **时间**: 2026-09-01T08:18:10Z
- **提交信息**: [FlashInfer V0.6.18] feat(dsv4): support --dsa-topk-backend flashinfer with fused top-k (#33237)

### [3484f7f](https://github.com/sgl-project/sglang/commit/3484f7f8361f8bc32177ce3f1073cfc3a2988d66)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-01T08:14:43Z
- **提交信息**: [mem_cache] Add `free_kv_row` to release a request's kv row by row range (#36721)

### [1c3ad92](https://github.com/sgl-project/sglang/commit/1c3ad92438ac6c1064f0ef1b8fdb675ecb514993)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-01T08:14:29Z
- **提交信息**: [Diffusion] Fuse FLUX.2 ModelOpt FP8 producers and QKV packing (#37162)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [379e33d](https://github.com/sgl-project/sglang/commit/379e33d87ef8b4a2f2e2f6179747b70ca40c933a)

- **作者**: zijiexia
- **时间**: 2026-09-01T08:03:39Z
- **提交信息**: [Cookbook] Add NVFP4 options for DeepSeek-V4 Flash Official (0731) and Pro Official (0813) (#37351)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [03b33cb](https://github.com/sgl-project/sglang/commit/03b33cbe5d632ef43e21b3bcf241c1ae765b089a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-01T07:55:05Z
- **提交信息**: [CI] Fix hybrid wrapper test fake missing kv_index_translator (#37374)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1265
- **最后更新**: 2026-09-01T16:44:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90703
- **最后更新**: 2026-09-01T23:43:10Z

## 提交统计

- **昨日提交总数**: 59
- **提交者数量**: 46
- **主要提交者**: Ilya Markov, Priyansh Jain, Alberto Massidda

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本批次共59个提交，按类型分布如下：
- **Bug修复**（约20个）：占比最高，覆盖前端、KV连接器、量化、模型加载等多个模块
- **CI/构建优化**（约12个）：包括测试分片、运行器优化、CI流程改进
- **性能优化**（约6个）：涉及内核优化、权重预取、量化核改进
- **功能新增**（约5个）：如FlashInfer ReplaySSM后端、B12X因果分页注意力后端
- **重构**（约4个）：如QuantKey驱动的LinearMethod重构、MoE掩码激活泛化
- **文档更新**（1个）：FP8 GEMM内核选择与Blackwell支持文档

## 二、关键变更点与项目方向

1. **量化体系重构**：多个提交围绕`QuantKey`机制重构量化方法分发（#49381、#52958），统一Quark等量化框架的配置与调度逻辑，体现vLLM对多硬件量化支持的系统化整合。

2. **Rust前端持续演进**：多个提交涉及Rust前端的token属性、多模态支持、参数解析器边界（#52910、#54813、#54303），显示vLLM正加速推进Rust前端的生产就绪度。

3. **KV连接器与异构共享**：Mooncake Store Connector支持异构TP共享（#53129）、修复物理块传输长度（#54272），强化了跨节点KV缓存共享能力，支撑大规模分布式推理。

4. **CI基础设施大幅优化**：大量提交聚焦测试分片、运行器精简、量化测试加速（#54754、#54752、#53291），反映项目在规模化开发下的工程效率治理。

5. **多硬件适配深化**：ROCm相关提交密集（gfx950块缩放、softplus测试、权重加载覆盖），Intel GPU/XPU测试加入，CPU Zen路径通过zentorch路由Int8 MoE，体现多平台战略。

## 三、对项目的影响与意义

- **稳定性提升**：大量Bug修复覆盖推理路径的关键环节（token流、KV传输、量化权重加载），直接改善生产环境的可靠性。
- **性能潜力释放**：Kimi-K3的ll_bf16权重预取、Hopper LL-GEMM调优表、NVFP4 padding初始化等优化，针对特定模型和硬件组合挖掘性能空间。
- **架构演进加速**：QuantKey重构和Rust前端推进是长期架构投资，为后续扩展奠定基础。
- **测试效率改善**：CI分片和加速措施缩短验证周期，提升迭代速度。

## 四、值得关注的技术点

1. **FlashInfer ReplaySSM后端**（#52506）：为Mamba类模型引入新推理后端，扩展vLLM对SSM架构的支持。
2. **B12X因果分页注意力**（#52017）：新增注意力后端，可能针对特定硬件优化。
3. **自适应验证机制**（#52724）：FLASHINFER_MLA_SPARSE_DSV4启用自适应验证，提升MLA推理的可靠性。
4. **前缀缓存块丢弃控制**（#53388）：提供禁用trailing前缀缓存块丢弃的选项，增强缓存策略灵活性。
5. **安全修复**：嵌入稠密化边界控制（#54632）和MCP SDK 2.x兼容（#53870），关注安全与生态兼容。

## 五、对项目发展的影响

vLLM正从“高性能推理引擎”向“全栈LLM服务平台”演进。本批次提交体现了三个核心战略方向：**一是硬件生态广度**（AMD ROCm、Intel XPU、NVIDIA Blackwell全面覆盖）；**二是架构现代化**（Rust前端、QuantKey重构、KV连接器增强）；**三是工程效率规模化**（CI优化、测试分片、自动化工具链）。这些变化使vLLM在保持性能领先的同时，提升了可维护性和可扩展性，为应对LLM推理场景的多样化需求奠定了更坚实的基础。

## 详细提交记录

### [80389cf](https://github.com/vllm-project/vllm/commit/80389cfedd5040e382d64a64b1782f66de1a38bf)

- **作者**: Bugen Zhao
- **时间**: 2026-09-01T23:12:00Z
- **提交信息**: [CI/Build] Gate PR title check on ready PRs & use slim runners (#54827)

Co-authored-by: Codex <codex@openai.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [e01d4ac](https://github.com/vllm-project/vllm/commit/e01d4acbb1ea559379825072afd7595fd0160d1f)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-01T23:04:14Z
- **提交信息**: [ROCm][CI] Handle tied experts in softplus sqrt top-k test (#52679)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [3b6c0bd](https://github.com/vllm-project/vllm/commit/3b6c0bdae9ef0a923dfbd545e3633b95db36a13d)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-01T22:58:27Z
- **提交信息**: [CI] Shard long kernel test groups (#54754)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [96031b8](https://github.com/vllm-project/vllm/commit/96031b8623f36522f5e6e70f778d9654341a8d86)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-01T22:32:11Z
- **提交信息**: [CI] Shard distributed model jobs above the 24h P90 threshold (#54752)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [e90b608](https://github.com/vllm-project/vllm/commit/e90b608c42f60b03c20f57fabe22ec0d3cacd76c)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-01T22:29:33Z
- **提交信息**: [CI] Split nightly MTP acceptance tests (#52353)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [b911fe8](https://github.com/vllm-project/vllm/commit/b911fe85c42ae984f27d183a0b1de309adab9bf2)

- **作者**: Bugen Zhao
- **时间**: 2026-09-01T22:25:31Z
- **提交信息**: [Rust Frontend] Attribute decoded text to tokens (#52910)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [259a209](https://github.com/vllm-project/vllm/commit/259a209bfa8a561e87b72e9678fd3d3a35519ce6)

- **作者**: mingg26
- **时间**: 2026-09-01T21:40:19Z
- **提交信息**: [Kimi-K3][Perf] Prefetch ll_bf16 router weights for M=1 (#53524)

Signed-off-by: ming <ming@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [a56e74a](https://github.com/vllm-project/vllm/commit/a56e74afd6238914e263a61bcb33f89fd179b842)

- **作者**: Nick Hill
- **时间**: 2026-09-01T21:15:12Z
- **提交信息**: [CI] Remove MRV2-specific tests (#54823)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [fc72fc3](https://github.com/vllm-project/vllm/commit/fc72fc39ace2d5f42346880d3f8d27463a5c7079)

- **作者**: Wentao Ye
- **时间**: 2026-09-01T21:08:50Z
- **提交信息**: [Kimi Bug] Fix `cannot access local variable 'active_non_spec_mask_cpu'` (#54781)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [ce6a283](https://github.com/vllm-project/vllm/commit/ce6a283c097cd573f6f371bbb376c4e5c4d07ef7)

- **作者**: Micah Williamson
- **时间**: 2026-09-01T21:08:11Z
- **提交信息**: [Bugfix] Restore `weight_dtype` in `QuarkW8A8Fp8MoEMethod` to fix GPT-OSS FP8 MoE weight loading (#54824)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [18c5372](https://github.com/vllm-project/vllm/commit/18c53727cebb588771c5e2f62a207137b0d6dffd)

- **作者**: Jeff (Junze) Ma
- **时间**: 2026-09-01T20:31:30Z
- **提交信息**: [Bugfix][KV Connector] Fix DecodeBench DCP block selection (#54679)

Signed-off-by: Jeff Ma <jeffjma@umich.edu>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [16f1687](https://github.com/vllm-project/vllm/commit/16f16876fda8527189464613509188d873bf5e7f)

- **作者**: Andrey Talman
- **时间**: 2026-09-01T20:29:23Z
- **提交信息**: [CI] Read the CRCR report token from a Buildkite secret (#54605)

Signed-off-by: Andrey Talman <atalman@fb.com>

### [7a977c0](https://github.com/vllm-project/vllm/commit/7a977c0699b9891e97f6b30b4e28b6864c4761fc)

- **作者**: Juhi Mittal
- **时间**: 2026-09-01T20:28:56Z
- **提交信息**: [ModelOpt] Redesign the LinearMethod classes using the generic QuantKey-driven method (#49381)

Signed-off-by: Juhi Mittal <juhim@nvidia.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [4bf06be](https://github.com/vllm-project/vllm/commit/4bf06be985c64edbb0c8b0f994ceff787ce84b09)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-01T20:24:46Z
- **提交信息**: [CI] Disable CUDA graphs for GLM PCP evals (#54745)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [dc5cf43](https://github.com/vllm-project/vllm/commit/dc5cf437cfbe15affa46020e21463e343b8cfbd5)

- **作者**: Isotr0py
- **时间**: 2026-09-01T20:23:55Z
- **提交信息**: [Rust Frontend] Enable Qwen4-exp multimodal support (#54813)

### [5cc32fb](https://github.com/vllm-project/vllm/commit/5cc32fbdfac44987bc2ece1d9ded7cb43acc2820)

- **作者**: Zhewen Li
- **时间**: 2026-09-01T20:23:46Z
- **提交信息**: [Bugfix][KV Connector] Fix Mooncake physical-block transfer length (#54272)

Signed-off-by: zhewenl <zhewenl@users.noreply.github.com>
Co-authored-by: zhewenl <zhewenl@users.noreply.github.com>

### [7cb9a88](https://github.com/vllm-project/vllm/commit/7cb9a88f50088453bbcf86704c376103dcd6b699)

- **作者**: Dao007forever
- **时间**: 2026-09-01T20:23:35Z
- **提交信息**: [Bugfix][Mooncake] Offload producer partial tails on request finish (#52832)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Roger Wang <hey@rogerw.io>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [55178f2](https://github.com/vllm-project/vllm/commit/55178f2d09309c42bad093484c4c1d5df340ab14)

- **作者**: Alberto Massidda
- **时间**: 2026-09-01T20:05:04Z
- **提交信息**: [Bugfix][Profiler] Fix API server crash on double /stop_profile (#51678)

Signed-off-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Alberto Massidda <amassidda@nvidia.com>

### [73723b7](https://github.com/vllm-project/vllm/commit/73723b707fe4b5ba99271ef3cbd3d3ad20d36000)

- **作者**: stefankoncarevic
- **时间**: 2026-09-01T19:48:45Z
- **提交信息**: [ROCm][MoE] Fix gfx950 block scale swizzle for AITER Triton MXFP4 W4A16 (#54773)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [3439bad](https://github.com/vllm-project/vllm/commit/3439bad37e68ba9755a46f4f6b44a4aeaf1f60a9)

- **作者**: Bugen Zhao
- **时间**: 2026-09-01T19:45:50Z
- **提交信息**: [Rust Frontend] Bound recursive argument parsers (#54303)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [ab54f5b](https://github.com/vllm-project/vllm/commit/ab54f5bd832d27fbe3bccbfa45af5775473301c3)

- **作者**: Julien Debache
- **时间**: 2026-09-01T19:30:11Z
- **提交信息**: [Chore] Remove redundant `_pack_topk_ids_weights_kernel` in TrtLLM NvFP4 MoE (#46872)

Signed-off-by: jdebache <jdebache@nvidia.com>

### [aa71f9b](https://github.com/vllm-project/vllm/commit/aa71f9bcc420241bbbd37c133a0e2b8930878755)

- **作者**: Luyi Xiao
- **时间**: 2026-09-01T19:11:52Z
- **提交信息**: [Bugfix] Log platform plugin detection failures (#52285)

Signed-off-by: Luyi Xiao <xiao.luy@northeastern.edu>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [c0adee9](https://github.com/vllm-project/vllm/commit/c0adee92317d436b88b621751122a72c7361229e)

- **作者**: Divakar Verma
- **时间**: 2026-09-01T19:03:37Z
- **提交信息**: [ROCm][CI] Add ROCm misc ops and env tests (#53279)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [6c58595](https://github.com/vllm-project/vllm/commit/6c58595c2d0d37c338cd757d55d48f446a68a7da)

- **作者**: Wentao Ye
- **时间**: 2026-09-01T19:03:30Z
- **提交信息**: [Feature] Avoid flashinfer autotune each time when vllm source change (#54794)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d98bb2a](https://github.com/vllm-project/vllm/commit/d98bb2a87996f46791aac7b0682998371d4ff48b)

- **作者**: waizuichougou
- **时间**: 2026-09-01T19:00:28Z
- **提交信息**: [Bugfix][Frontend] Honor skip_decoder_start_token in async encoder-decoder rendering (#54799)

Signed-off-by: waizuichougou <2082431897@qq.com>

### [0ad5652](https://github.com/vllm-project/vllm/commit/0ad5652a523d7bfe191a08b97ca45ead585b1897)

- **作者**: Pratham Shirbhate
- **时间**: 2026-09-01T18:17:54Z
- **提交信息**: [Bugfix][Frontend] Restore the chat template content format mismatch warning (#54622)

Signed-off-by: Pratham Shirbhate <prathamshirbhate1909@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [d1c15e5](https://github.com/vllm-project/vllm/commit/d1c15e589d4c92136eea18773570a927d8795718)

- **作者**: fxmarty-amd
- **时间**: 2026-09-01T18:15:24Z
- **提交信息**: [CI] Speed up quantization test group (#53291)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [e7cf473](https://github.com/vllm-project/vllm/commit/e7cf4730d6c441723faec060b99cf597b701f285)

- **作者**: Suvrakamal Das
- **时间**: 2026-09-01T18:11:36Z
- **提交信息**: [Bugfix] Drop incomplete tool-call markup in non-streaming to match streaming (#47562)

Signed-off-by: Suvrakamal Das <jyb2084.usa@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [2f01039](https://github.com/vllm-project/vllm/commit/2f01039666b7d9bb6c93125c98318632c7de9272)

- **作者**: Misha Goin
- **时间**: 2026-09-01T17:22:09Z
- **提交信息**: [Misc] Share Buildkite CI failure skill across agents (#54806)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [c866ba9](https://github.com/vllm-project/vllm/commit/c866ba9d11984fd621af5837f91cd763312f4dd3)

- **作者**: 周峥
- **时间**: 2026-09-01T17:18:06Z
- **提交信息**: [KV Connector] Support heterogeneous TP sharing in Mooncake Store Connector (#53129)

Signed-off-by: Guanyi Chen <939416532@qq.com>
Signed-off-by: z-zanez <zhouzh93@mail2.sysu.edu.cn>
Signed-off-by: Zheng Zhou <zhouzh93@mail2.sysu.edu.cn>
Signed-off-by: zane <zhouzh93@mail2.sysu.edu.cn>
Co-authored-by: Guanyi Chen <939416532@qq.com>

### [2fe5cef](https://github.com/vllm-project/vllm/commit/2fe5cef35eddcaf1c74104002f9abbfe32f9ef4d)

- **作者**: fxmarty-amd
- **时间**: 2026-09-01T17:12:20Z
- **提交信息**: [Fix] Fix FSE compatibility detection for Quark-produced models (#54573)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>
Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: xuebwang-amd <xuebwang@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [514c731](https://github.com/vllm-project/vllm/commit/514c7314a06be9e43d00d3f126a5aaa54211274f)

- **作者**: Roberto L. Castro
- **时间**: 2026-09-01T16:49:07Z
- **提交信息**: [Perf][Kernel] Initialize NVFP4 padding in quant kernel (#53568)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [cdefd9d](https://github.com/vllm-project/vllm/commit/cdefd9d4997f00da72dc6245cc60678b50761b7e)

- **作者**: Eli Nabro Yeongmin Oh
- **时间**: 2026-09-01T15:53:38Z
- **提交信息**: [Bugfix] Support Sentence Transformers 5.4+ serialized configs (#54533)

Signed-off-by: maireneu <maireneu@gmail.com>
Co-authored-by: Codex <codex@openai.com>

### [f1e5fdd](https://github.com/vllm-project/vllm/commit/f1e5fdd7f2f4381cd3bd4e4b821fad4604bd72ab)

- **作者**: Harry Mellor
- **时间**: 2026-09-01T15:35:24Z
- **提交信息**: [Transformers backend] Replace vocab embeddings in `recursive_replace` (#54760)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [82b7d49](https://github.com/vllm-project/vllm/commit/82b7d49a6e30cf6d1d53838667ee20f09ac1f08b)

- **作者**: Misha Goin
- **时间**: 2026-09-01T15:34:13Z
- **提交信息**: [MoE] Generalize masked activation for padded layouts (#51217)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [a232e29](https://github.com/vllm-project/vllm/commit/a232e29e9d717562cf9cf7a8d086d52a57056615)

- **作者**: Bojiang Li
- **时间**: 2026-09-01T15:29:15Z
- **提交信息**: [Bugfix] Gate sm_100-only kernel tests on the capability family, not >= (#54306)

Signed-off-by: bojiang3 <bli314159@gmail.com>

### [76f3249](https://github.com/vllm-project/vllm/commit/76f3249fbdff761aa897218913050de0526ccca2)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-01T15:26:00Z
- **提交信息**: [Mypy] Fix typing for M models (#54262)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [d9eb4e3](https://github.com/vllm-project/vllm/commit/d9eb4e344f91838ef718c0f2123c836a58e49f08)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-01T15:24:19Z
- **提交信息**: [Bugfix] Reject tokenless chat and audio streams (#54708)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [339e16c](https://github.com/vllm-project/vllm/commit/339e16cbb687680a401afc4aca5b19cac54a5fe3)

- **作者**: Chauncey
- **时间**: 2026-09-01T15:02:39Z
- **提交信息**: [Bugfix] Support MCP SDK 2.x tool input schemas (#53870)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [0d4ad47](https://github.com/vllm-project/vllm/commit/0d4ad47981b6133c8f835d78f7a19ca4eda113d5)

- **作者**: Luke Alonso
- **时间**: 2026-09-01T14:42:02Z
- **提交信息**: [Kernel] Add B12X causal paged attention backend (#52017)

Signed-off-by: Luke Alonso <lalonso@gmail.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [adebc41](https://github.com/vllm-project/vllm/commit/adebc41b7e9f1085d3f73434e23beb76883b9eb4)

- **作者**: Andrii Skliar
- **时间**: 2026-09-01T14:26:43Z
- **提交信息**: [Mamba] Add FlashInfer ReplaySSM backend (#52506)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Signed-off-by: Andrii Skliar <andreyws96@gmail.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>

### [25efcfa](https://github.com/vllm-project/vllm/commit/25efcfa7887c4a9541b6328af69dbd5fee4e8173)

- **作者**: Ilya Markov
- **时间**: 2026-09-01T13:43:28Z
- **提交信息**: [Attention] Enable adaptive verification for FLASHINFER_MLA_SPARSE_DSV4 (#52724)

Signed-off-by: Markov Ilya <markovilya197@gmail.com>

### [1f1f628](https://github.com/vllm-project/vllm/commit/1f1f628859dd0dc2a3b7f43810254884799619e6)

- **作者**: Jan Kwieciński
- **时间**: 2026-09-01T13:17:01Z
- **提交信息**: [Feat][MM Hashing]  include media_io_kwargs in multi-modal hashes (#54241)

Signed-off-by: Jan Kwiecinski <jkwiecinski@nvidia.com>

### [55aa766](https://github.com/vllm-project/vllm/commit/55aa766dc8c1a7d739ef90c5580ca4b91050b35f)

- **作者**: Priyansh Jain
- **时间**: 2026-09-01T12:38:53Z
- **提交信息**: [Bugfix][Model] Fix GraniteMoeHybrid per-expert quantized weight loading (#54052)

### [4082428](https://github.com/vllm-project/vllm/commit/40824284bcb2f50047a48307ed39ce441bb15b0b)

- **作者**: Harjoth Khara
- **时间**: 2026-09-01T12:22:40Z
- **提交信息**: [Doc] Document FP8 GEMM kernel selection and Blackwell support (#49936)

Signed-off-by: harjoth <harjoth.khara@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [191cecd](https://github.com/vllm-project/vllm/commit/191cecd51e250de77618dda924359214b4d88119)

- **作者**: Zheng Cai
- **时间**: 2026-09-01T11:21:41Z
- **提交信息**: [Kernel][Qwen] Add Hopper LL-GEMM tuning table for Qwen4Exp (#54560)

Signed-off-by: Zheng Cai <8370601+zigzagcai@users.noreply.github.com>

### [481839a](https://github.com/vllm-project/vllm/commit/481839ad9e5ebf87aecb54fa5c9d986bd5ea4b81)

- **作者**: Ziming Huang
- **时间**: 2026-09-01T11:12:36Z
- **提交信息**: [Feature][Spec] Support disabling trailing prefix-cache block dropping (#53388)

Signed-off-by: Ziming Huang <zelda.huanghuang@gmail.com>
Signed-off-by: Ziming Huang <48115868+ZeldaHuang@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9e905f7](https://github.com/vllm-project/vllm/commit/9e905f7450fb556c4f43e49d4ece0f728cbfda2b)

- **作者**: maithilijoshi20
- **时间**: 2026-09-01T10:40:51Z
- **提交信息**: [Bugfix] Account for client queue time in serve benchmarks (#54136)

Signed-off-by: maithilijoshi20 <maithilijoshi2003@gmail.com>
Signed-off-by: maithilijoshi20 <97733343+maithilijoshi20@users.noreply.github.com>
Signed-off-by: maithilijoshi20 <maithilij2003@gmail.com>
Co-authored-by: maithilijoshi20 <maithilijoshi2003@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [92ccd2c](https://github.com/vllm-project/vllm/commit/92ccd2c30679d53418399be71f8ff7c0afef9790)

- **作者**: Liang Lv
- **时间**: 2026-09-01T10:40:47Z
- **提交信息**: [Bugifx][INC] Fix INC quantization method selection for non-quantized layers (#47237)

Signed-off-by: lvliang-intel <liang1.lv@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [754d5e1](https://github.com/vllm-project/vllm/commit/754d5e1f6597f0742f8fb8f7325533e5db37ae23)

- **作者**: Cyrus Leung
- **时间**: 2026-09-01T10:33:02Z
- **提交信息**: [CI/Build] Fix entrypoints coverage (#54750)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [504bb8b](https://github.com/vllm-project/vllm/commit/504bb8b0c39dbde713a7344772bdb7005adbb214)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-01T09:36:46Z
- **提交信息**: [CI] Add repository-local OTel tracing helpers (#52851)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [8f03625](https://github.com/vllm-project/vllm/commit/8f03625b3d14969e59b2adb06097b2f20be5ce8c)

- **作者**: Ganesh R
- **时间**: 2026-09-01T09:31:31Z
- **提交信息**: [CPU][Zen] Route Int8 MoE inference through zentorch on AMD (#44834)

Signed-off-by: R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c35551f](https://github.com/vllm-project/vllm/commit/c35551f892f1aa3ace67c0d8cde74eafd00b6e69)

- **作者**: AlexHuang
- **时间**: 2026-09-01T09:24:54Z
- **提交信息**: [Bugfix][KV Offload] Isolate tiering shutdown failures (#52290)

Signed-off-by: Alex <jihui.huang@daocloud.io>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [4707679](https://github.com/vllm-project/vllm/commit/4707679cd26459caef158b084f17c41489b4d0fa)

- **作者**: Subhash Polisetti
- **时间**: 2026-09-01T09:16:07Z
- **提交信息**: [Bugfix][MiniCPM-V] Route video_embeds to the shared vision parser (#54633)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>

### [5414b4e](https://github.com/vllm-project/vllm/commit/5414b4e694c4670a143229e9995268963c8f7af1)

- **作者**: xiangdong
- **时间**: 2026-09-01T08:57:55Z
- **提交信息**: [XPU][TEST] Add entrypoints test in Intel GPU CI (#53980)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ce73917](https://github.com/vllm-project/vllm/commit/ce7391712b59f55a8d1254468605c5a3592d2d50)

- **作者**: lzhan011
- **时间**: 2026-09-01T08:45:14Z
- **提交信息**: [Bugfix][Security] Bound embedding densification before to_dense() (#54632)

Signed-off-by: lzhan011 <35493221+lzhan011@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [8905633](https://github.com/vllm-project/vllm/commit/890563368750fad14864181715d9e1b96478868b)

- **作者**: waizuichougou
- **时间**: 2026-09-01T08:02:56Z
- **提交信息**: [Bugfix][Frontend] Preserve token offset origins after left text pre-trimming (#54692)

Signed-off-by: waizuichougou <2082431897@qq.com>

### [b65af5e](https://github.com/vllm-project/vllm/commit/b65af5e3396e161a64db6352241acf3afbdcd958)

- **作者**: stefankoncarevic
- **时间**: 2026-09-01T07:57:22Z
- **提交信息**: [CI][ROCm] Expand weight loading test coverage on AMD and cap its KV cache (#54037)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [63988f3](https://github.com/vllm-project/vllm/commit/63988f3c2d79db505ca2ac24dc1ed51f4b63249a)

- **作者**: fxmarty-amd
- **时间**: 2026-09-01T07:55:54Z
- **提交信息**: [Quantization][Refactor][1/N] Adopt `QuantKey` in `QuarkConfig` and methods, relying on `weight_quant_key`, `act_quant_key` for quant method dispatch (#52958)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-02
**监控日期**: 2026-09-01
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6548
- **最后更新**: 2026-09-02T00:09:55Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 9
- **主要提交者**: AuFlow, andyluo7, lea

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交涵盖**Bug修复**（4项）、**新模型支持**（1项）、**测试扩展**（1项）、**文档更新**（2项）、**前端功能增强**（1项）及**CI优化**（1项），整体以稳定性和兼容性提升为主。

### 2. 关键变更点与项目方向
- **Ascend NPU RoPE修复**：将复杂数域RoPE替换为实数运算，解决华为昇腾平台上的数值精度问题，强化了项目“多硬件适配”的定位。
- **SenseNova-U1.5-8B-MoT支持**：新增多模态思维链模型及其蒸馏LoRA，直接扩展了“omni-modality”模型生态，符合项目核心目标。
- **Speech API采样率可配置**：为语音接口增加输出采样率参数，完善了多模态服务的前端灵活性。
- **Cosmos3日志降噪**：将提示词日志从INFO降级，避免敏感信息泄露，提升生产环境安全性。
- **ROCm CI确定性修复**：解决AMD平台的L3测试阻塞，保障跨平台CI稳定性。

### 3. 项目影响与潜在意义
- **硬件生态扩展**：NPU和ROCm的修复使项目在非NVIDIA硬件上的可用性显著增强，扩大潜在用户群。
- **模型覆盖深化**：SenseNova系列支持填补了思维链多模态模型的空白，吸引研究型用户。
- **工程成熟度提升**：日志安全、参数防突变等修复表明项目正从“功能优先”转向“生产级质量”。

### 4. 值得关注的技术点
- **实数RoPE替代方案**：为NPU等非CUDA平台提供了一种可复用的数值稳定性优化模式。
- **LoRA蒸馏集成**：展示了项目对“高效微调+推理”组合场景的支持能力。
- **engine_args防突变**：通过避免配置对象被意外修改，提升了多阶段构建的可靠性。

### 5. 对项目发展的影响
结合README中“Easy, fast, and cheap omni-modality serving”的愿景，本次提交体现了三个推进方向：**一是通过硬件适配降低使用门槛**（NPU/ROCm），**二是通过模型扩展丰富模态覆盖**（SenseNova、MiniMax-H3），**三是通过工程化修复提升服务稳定性**（日志、CI、配置安全）。这些变更共同推动vllm-omni从“多模态推理框架”向“跨平台生产级服务系统”演进，为后续吸引更广泛的开发者与部署场景奠定基础。

## 详细提交记录

### [5f49848](https://github.com/vllm-project/vllm-omni/commit/5f49848536fb7a0de5d29963097d2411f54f2d86)

- **作者**: lea
- **时间**: 2026-09-01T23:11:01Z
- **提交信息**: [Bugfix][Ascend NPU][Boogu] Replace complex RoPE with real-valued operations (#6571)

Signed-off-by: lea_lei <JiaWen_Lei_7@163.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [3cddda9](https://github.com/vllm-project/vllm-omni/commit/3cddda978153f3a19ecd691d343854dd074e587d)

- **作者**: Arifuzzaman Joy
- **时间**: 2026-09-01T16:45:28Z
- **提交信息**: [Bugfix] Prevent build_engine_args_dict from mutating stage_config.engine_args (#6783)

Signed-off-by: Arifuzzamanjoy <s1710374103@ru.ac.bd>

### [0288c3f](https://github.com/vllm-project/vllm-omni/commit/0288c3f56eb4a4ff410194e586498e3bc8ff8362)

- **作者**: DanaerLee
- **时间**: 2026-09-01T14:53:53Z
- **提交信息**: [Model] Support SenseNova-U1.5-8B-MoT and its distilled 8-step LoRA (#6516)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [477083a](https://github.com/vllm-project/vllm-omni/commit/477083a103bef1e2c5fab174a61c268c43e9238d)

- **作者**: andyluo7
- **时间**: 2026-09-01T14:53:00Z
- **提交信息**: [CI][ROCm] Fix deterministic AMD L3 blockers (#6884)

Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e1b2f58](https://github.com/vllm-project/vllm-omni/commit/e1b2f589c12c015ba668bc2a1b31d33ab68d0bf9)

- **作者**: Rahul Steiger
- **时间**: 2026-09-01T14:52:15Z
- **提交信息**: [Bugfix][Cosmos3] Avoid logging prompts at INFO level (#6913)

Signed-off-by: Rahul Steiger <rsteiger@nvl72d233-T16.cm.cluster>
Co-authored-by: Rahul Steiger <rsteiger@nvl72d233-T16.cm.cluster>

### [44c8d1c](https://github.com/vllm-project/vllm-omni/commit/44c8d1c4491bb0640d5e6073f00b86b7ba1809ed)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-01T12:34:09Z
- **提交信息**: docs: add concise API server endpoint guide (#6114)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: hsliu_ustc <hsliu_ustc@noreply.gitcode.com>

### [2298359](https://github.com/vllm-project/vllm-omni/commit/2298359f677efdacc67c2924ed71df645529eab4)

- **作者**: Andy Zhou
- **时间**: 2026-09-01T12:18:44Z
- **提交信息**: [Bugfix][Diffusion] Preserve stage attention backend (#6645)

Signed-off-by: AndyZhou952 <jzhoubc@connect.ust.hk>

### [d1c8bee](https://github.com/vllm-project/vllm-omni/commit/d1c8beeb180b4617437c460ba5c8f61a4a561a7e)

- **作者**: Hongsheng Liu
- **时间**: 2026-09-01T11:50:26Z
- **提交信息**: [Doc] Update README and docs for v0.28.0 (#6858)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [e2b83db](https://github.com/vllm-project/vllm-omni/commit/e2b83db683673a0d54bb58db5f12d27a7f9f20e0)

- **作者**: WeiQing Chen
- **时间**: 2026-09-01T10:48:52Z
- **提交信息**: [Test] Add MiniMax-H3 DLO DP2 variants and Turbo LoRA L3 test (#6556)

Signed-off-by: david6666666 <530634352@qq.com>

### [49c6fc1](https://github.com/vllm-project/vllm-omni/commit/49c6fc15408ef92ee08619da6bf7ed4f8f7f96dd)

- **作者**: AuFlow
- **时间**: 2026-09-01T09:25:09Z
- **提交信息**: [Frontend] Add configurable output sample rate to Speech API (#6553)

Signed-off-by: 郑倩倩 <2458983186@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
