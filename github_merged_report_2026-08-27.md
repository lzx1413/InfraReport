# GitHub Stars 合并报告 - 2026-08-27

**合并日期**: 2026-08-28
**监控日期**: 2026-08-27
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


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2177
- **最后更新**: 2026-08-28T02:53:09Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

### 主要更新类型
本次提交以**功能新增**为主，涉及训练器（trainer）、持续集成（CI）和算子（ops）三个模块，无Bug修复或文档更新。

### 关键变更点及与项目方向的关系
1. **训练器指标上报优化**（`77c4470`）：新增`aux_metrics`独立上报机制，不再将其折叠进主损失（loss）中。这直接服务于VeOmni“多模态模型训练”的核心目标——在多模态场景下，辅助指标（如模态对齐度、分任务损失）对训练监控至关重要，独立上报能更精细地追踪各模态学习状态。
2. **TileLang算子新增**（`0c5e57b`）：为DeepSeek-V4索引器添加了基于TileLang的教师分布（teacher-distribution）内核。这体现了项目“模型中心化分布式训练配方”的定位，通过为特定模型架构（DeepSeek-V4）定制高性能算子，扩展了配方库的覆盖范围。

### 对项目的影响和潜在意义
- **训练可观测性提升**：aux_metrics独立上报使研究人员能清晰区分主损失与辅助指标，便于诊断多模态训练中的模态失衡问题，直接提升训练配方的可调试性。
- **架构适配能力增强**：新增DeepSeek-V4专用内核，表明VeOmni正积极跟进前沿模型架构，强化其作为“配方动物园”（Recipe Zoo）的生态吸引力，吸引更多模型训练场景接入。
- **CI集成**：指标上报改动伴随CI更新，确保新功能在持续集成流程中稳定验证，维护项目工程质量。

### 值得关注的技术点
- **TileLang内核设计**：教师分布内核通常用于知识蒸馏或分布匹配，其实现可能涉及高效张量重排与分布计算，值得关注其性能优化策略。
- **指标上报架构**：`aux_metrics`独立于loss的通道设计，可能涉及训练循环中的指标聚合与日志记录重构，对后续扩展其他监控指标具有参考价值。

### 对项目发展的影响
基于README背景，VeOmni旨在成为“任意模态模型训练的分布式配方中心”。这两项提交分别从**训练监控精细化**和**模型架构覆盖广度**两个维度推进该目标：前者提升配方质量（更易调试），后者扩大配方适用性（支持新模型）。整体上，项目正通过持续的功能迭代，巩固其作为多模态训练基础设施的地位，并保持对前沿模型（如DeepSeek系列）的快速适配能力，符合其“模型中心化”的技术愿景。

## 详细提交记录

### [77c4470](https://github.com/ByteDance-Seed/VeOmni/commit/77c447072ab75f3865aee62901f15f0ab89f5470)

- **作者**: Bin Jia
- **时间**: 2026-08-27T10:16:58Z
- **提交信息**: [trainer, ci] feat: report model aux_metrics without folding them into the loss (#1110)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [0c5e57b](https://github.com/ByteDance-Seed/VeOmni/commit/0c5e57b85fffdf95e182316f355db450ab67e0a0)

- **作者**: Bin Jia
- **时间**: 2026-08-27T08:41:10Z
- **提交信息**: [ops] feat: add the TileLang teacher-distribution kernel for the DeepSeek-V4 indexer (#1109)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2737
- **最后更新**: 2026-08-28T02:49:38Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交以**代码清理与配置规范化**为主，属于项目维护和重构范畴，不涉及新功能开发或Bug修复。

### 2. 关键变更点及与项目方向的关系
- **移除已退役模型残留**（#1449）：删除不再维护的模型相关代码，符合项目聚焦核心视频生成推理能力的定位。
- **配置路径规范化与字段清理**（#1448）：统一配置文件的路径格式，移除冗余字段，提升配置系统的可维护性。
- **移除提示词增强器支持**（#1447）：删除prompt enhancer功能模块，简化推理流程，减少不必要的依赖。

### 3. 对项目的影响和潜在意义
- **降低维护成本**：清理退役代码和冗余配置，减少后续开发时的认知负担和潜在冲突。
- **提升代码质量**：配置规范化有助于减少因路径不一致导致的运行错误，增强框架的稳定性。
- **聚焦核心能力**：移除辅助功能（如prompt enhancer）表明项目正收敛到视频生成推理这一核心场景，避免功能膨胀。

### 4. 值得关注的技术点
- **配置路径规范化**：暗示项目可能正在统一不同模型/场景下的资源路径管理方式，为后续扩展打基础。
- **模块移除的彻底性**：三个提交均涉及删除操作，说明项目对技术债清理较为积极，且能快速决策功能去留。

### 5. 对项目发展的影响
LightX2V定位为轻量级视频生成推理框架，强调高效与简洁。本批提交通过**精简代码库、规范配置体系**，进一步强化了“轻量”这一核心卖点。移除prompt enhancer等外围功能，有助于将开发资源集中在推理性能优化和主流模型支持上，符合README中“Light”的定位。整体来看，这些清理工作为后续功能迭代提供了更干净的代码基础，属于健康的技术演进。

## 详细提交记录

### [680d9be](https://github.com/ModelTC/LightX2V/commit/680d9be199a69ebe4a02f86bdd653f23298ac02d)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-27T11:53:09Z
- **提交信息**: cleanup: remove retired model remnants (#1449)

### [7984268](https://github.com/ModelTC/LightX2V/commit/79842681ae93ff2bff3b72e7fa7316b381050a09)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-27T11:00:02Z
- **提交信息**: config: normalize paths and clean up fields (#1448)

### [7421f90](https://github.com/ModelTC/LightX2V/commit/7421f90e7f199d07abb344f88a59a8d43bfea427)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-27T08:39:36Z
- **提交信息**: remove prompt enhancer support (#1447)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2217
- **最后更新**: 2026-08-27T19:48:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6268
- **最后更新**: 2026-08-28T03:41:49Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Xuanteng Huang, eigen, Nader Al Awar

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **Bug修复**：修复CuTe DSL在SM107（Rubin）架构上的兼容性问题
- **功能新增**：三项新功能——Blackwell DCP投机解码、CUB Top-K后端、NVFP4 ReLU2 MoE支持

### 2. 关键变更点与项目方向
- **CuTe DSL架构门控修复**：解决旧版CuTe DSL（<4.8）在SM107上因缺少`sm_107a`枚举导致`KeyError`的问题，将硬件能力检查与DSL可用性检查分离，确保自动后端选择能正确回退到cutlass/cudnn
- **Cake FMHA DCP投机解码**：为`trtllm_batch_decode_with_kv_cache`增加上下文并行投机解码的原生路径，支持BF16和FP8格式，覆盖多种配置组合
- **CUB Top-K后端**：新增基于`cub::DeviceBatchedTopK`的API，支持变长序列和CUDA图捕获，在多数场景下性能提升1.6-2.0倍
- **NVFP4 ReLU2 MoE**：为Nemotron 3增加per-token NVFP4 MoE内核，扩展量化格式支持范围

### 3. 项目影响与意义
- **硬件前瞻性**：提前适配Rubin架构（SM107），确保在新硬件发布时即可使用
- **性能竞争力**：CUB Top-K在CUDA图场景下显著提升，直接惠及SGLang等推理框架
- **功能完整性**：DCP投机解码和NVFP4支持填补了关键场景空白，增强对最新模型架构的适配能力

### 4. 值得关注的技术点
- **错误处理设计**：将`NotImplementedError`适配为`ValueError`以保持自动后端搜索的连续性，体现了对异常语义的精细把控
- **CUDA图兼容性**：CUB变长路径在设备端读取lengths，实现固定形状下不同长度的图重放
- **性能权衡**：CUB在大批量长序列场景表现较弱，通过形状门控自动路由到更优后端

### 5. 对项目发展的影响
FlashInfer作为高性能GPU推理内核库，这些提交体现了其**多维度发展战略**：硬件前瞻适配（Rubin）、算法多样性（CUB/Cake）、量化格式扩展（NVFP4）。通过持续优化自动后端选择机制和扩展新硬件支持，项目正巩固其在推理性能领域的领先地位，同时为下一代GPU架构和最新模型架构做好技术储备。

## 详细提交记录

### [63f1b5b](https://github.com/flashinfer-ai/flashinfer/commit/63f1b5b30d11bcdd9543d1f538c99436805ebca6)

- **作者**: Vincent
- **时间**: 2026-08-27T23:55:58Z
- **提交信息**: fix(cute_dsl): consult the arch gate in the GEMM and GDN dispatchers (#4649)

## Problem

On SM107 (Rubin) with a CuTe DSL older than 4.8, FlashInfer fails with a
bare `KeyError: 'sm_107a'` raised from `enum.py` inside `cute.compile` —
no FlashInfer frame in the traceback, and no warning.

The root cause is that `supported_compute_capability` gates on
**hardware capability alone**. #4122 widened the cute-dsl lists to
`[100, 103, 107]`, which tells the dispatcher Rubin is supported
regardless of which DSL is installed. Public CuTe DSL tops out at 4.7.0
on PyPI, and that release has no `sm_107a` in its `Arch` enum.

This is reachable without asking for cute-dsl explicitly — two `auto`
heuristics route SM107 *toward* it:

- `_heuristic_func_mm_fp4`: `elif is_sm107: candidate_backends =
("cudnn", "cutlass", "cute-dsl")`
- `_heuristic_func_bmm_fp8`: appends `"cute-dsl_sm107"` when
`is_sm107_supported`

## Changes

**1. Decline the cute-dsl backend when the installed DSL cannot emit for
the device** (`fix(gemm)`)

The three cute-dsl requirement functions now call
`_check_cute_dsl_arch(...)`, which sits beside the existing
`_check_cute_dsl_availability()` and delegates to
`require_cute_dsl_arch()` — the helper added in #4122, which owns both
the predicate and the message (it derives the family arch and names the
exact `CUTE_DSL_ARCH=sm_100f` to export).

Only the exception type is adapted, and that part is load bearing:
`require_cute_dsl_arch` raises `NotImplementedError`, while
`suitable_auto_backends` catches `ValueError` to mean "backend not
suitable" and keeps searching. Left unadapted, an unsupported DSL would
propagate out of the auto path and fail the call instead of falling back
to cutlass/cudnn. Returning `False` instead of raising was also
rejected: on the explicit-backend path that surfaces as `ValueError:
Problem size is not supported`, which is misleading.

**No capability lists change.** This is deliberately an *availability*
check, not a capability one. The kernels do exist for sm_107, so
`@supported_compute_capability([100, 103, 107])` stays as-is and
`is_backend_supported("cute-dsl", 107)` keeps answering `True` — it is a
public method on the wrapper, called with no tensors by e.g.
`flashinfer/trace/templates/gemm.py:707`, and making it vary with an
installed pip package would also have made the skip reason in
`tests/grouped_mm/conftest.py` environment-dependent. This mirrors how
the codebase already separates the two axes:
`_cudnn_mm_mxfp8_requirement` lists its capabilities statically while
`CUDNN_AVAILABLE` handles presence, and
`_is_cudnn_override_shape_available` handles a dependency that is
present but too old.

**2. GDN CP delta rule resolves the arch instead of formatting it**
(`fix(gdn)`)

`_blackwell_compile_options` guards on the major only, then builds
`f"sm_{major}{minor}a"`. Rubin is 10.7, so it passes a check written
when "compute 10.x" meant Blackwell 10.0/10.3. This is the only place
FlashInfer names the arch for a compute-10 device; everywhere else the
DSL derives it internally.

`cute_dsl_compile_arch()` returns the device's own arch when the DSL has
it, the family arch when the DSL is targeting `sm_100f`, and otherwise
raises `NotImplementedError` naming `CUTE_DSL_ARCH`. Same rule as the
capability gate, so the two cannot disagree.

## Testing

Rubin CI, `TEST_PATH="tests/gemm tests/gdn"`, against `release-v0.6.18`,
with `CUTE_DSL_ARCH=sm_100f` exported and public CuTe DSL 4.7.0:

| | before | after |
|---|---|---|
| passed | 8,141 | **12,341** |
| failed | 4,230 | **1** |
| `KeyError: 'sm_107a'` | 4,482 | **0** |

Identical results on **both** VR200 (`hecate`, 4 workers, 2,078s) and
GR100 (8 workers, 3,424s); `suite_complete=true` on both, well inside
the 13,500s deadline.

Per-file, verified independently on both boards:

| File | before | after |
|---|---|---|
| `tests/gdn/test_prefill_delta_rule.py` | 2,678 | **0** |
| `tests/gemm/test_mm_mxfp8.py` | 501 | **0** |
| `tests/gdn/test_decode_delta_rule.py` | 417 | **0** |
| `tests/gdn/test_prefill_cp_delta_rule.py` | 232 | **0** |

The remaining failures are `tests/gdn/test_decode_ucache.py` and
`tests/gemm/test_bmm_fp8.py` — see below.

`BackendSupportedError` count is **0**, so the cute-dsl backends are
being selected and compiling successfully against `sm_100f` — not
silently skipped.

The node accounting reconciles exactly: the plan drops 44,275 → 44,229
nodes and 37 → 36 units, i.e. the 46 tests in the ucache module leave
collection entirely (a module-level skip is taken during collection, so
those nodes are not counted as `skipped`). `passed` moves +287 = +288
Triton tests now compiling, −1 ucache test that previously passed;
`failed` moves −333 = −288 Triton −45 ucache.

Also unit-tested away from hardware: the new decorator resolves
conditional 107 as False on DSL 4.7, True on 4.8+/`CUTE_DSL_ARCH`, False
when the predicate raises, and yields a plain `set` when no conditional
is given. `cute_dsl_compile_arch` was verified against a stubbed `Arch`
enum for native / family / unsupported / Blackwell-unchanged, and the
skip predicate for all four DSL-vs-arch combinations.

### Caveats

- **The numbers above do not reflect this branch.** They were measured
at `93143db2`, which carried a skip guard for
`tests/gdn/test_decode_ucache.py` that has since been reverted, so 45 of
those tests now fail again rather than skipping.
- **The gemm mechanism changed after that measurement.** The two commits
after it moved the check out of the decorator and into the requirement
functions; that mechanism is unit-tested (adapter pass-through,
`NotImplementedError` → `ValueError`, silent when the probe cannot be
imported) but has not been re-run on hardware.
- The measurement runs also carry `CUTE_DSL_ARCH=sm_100f` from the CI
side. With it set the DSL *can* target sm_107, so `_check_cute_dsl_arch`
passes and the gemm change is a no-op; only a run without that variable
exercises the deselect-and-fall-back path.
- `cute_dsl_compile_arch` changes `gdn_cp_prefill.py` for **all**
compute-10 devices, not just Rubin. Blackwell resolution (`sm_100a` /
`sm_103a`) is verified against a stubbed `Arch` enum, not on B200/GB200
hardware.

## Not addressed

- **45 `KeyError: 'sm_107a'`** in `tests/gdn/test_decode_ucache.py`. Not
fixable from FlashInfer: those kernels compile through
`@cute.experimental.jit` / `@cute.experimental.kernel`, passing no arch
and no compile options, so the DSL resolves the device arch itself and
looks up `sm_107a` in its own enum. There is no FlashInfer-side site to
guard, the traceback bottoms out at `enum.py:813` with no FlashInfer
frame, and `CUTE_DSL_ARCH=sm_100f` does not help because that path never
consults it — which points at a genuine **CuTe DSL 4.8** requirement.
Left visible rather than skipped; the kernel author (#4081) is better
placed to say whether it is inherent.
- **1 `No valid cute-dsl SM107 bmm_fp8 config`** in
`tests/gemm/test_bmm_fp8.py` — pre-existing, and present on the internal
DSL 4.8 stack too (18 vs 20 occurrences across stacks), so it is
independent of the DSL version question.

The 288 Triton `PTXASError` failures previously seen in
`tests/gemm/test_group_gemm.py` were a CI-side issue, not a FlashInfer
one: Triton resolves ptxas through its own knobs (`TRITON_PTXAS_PATH`,
and `TRITON_PTXAS_BLACKWELL_PATH` for arch >= 100, which is the one
Rubin selects) and otherwise falls back to `$CUDA_HOME/bin/ptxas`. Fixed
in flashinfer-ci!354; this run confirms 0 remaining.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added architecture detection for CuTe DSL compilation, including
native and family-compatible GPU architectures.
* Added clear guidance when the installed DSL cannot compile for a
target GPU.

* **Bug Fixes**
* Improved Blackwell architecture handling, including support for
devices with nonstandard architecture identifiers.
* Prevented unsuitable CuTe DSL backends from being selected
automatically when architecture support is unavailable.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [e04a5a5](https://github.com/flashinfer-ai/flashinfer/commit/e04a5a5d7fac9f2e9531b5e30e76ed999fb83055)

- **作者**: eigen
- **时间**: 2026-08-27T23:41:31Z
- **提交信息**: feat(cake_fmha): add native Blackwell DCP speculative decode (#4518)

## Summary

This adds an optional native Cake FMHA route to
`flashinfer.trtllm_batch_decode_with_kv_cache` for context-parallel
speculative
decode. The route is selected only when `causal_seqlens_kv_global` is
provided;
calls that omit it retain the existing decode dispatcher and ABI.

The route implements exact round-robin KV ownership, row-dependent
causal
bounds, exact empty-row values (`O=0`, `LSE=-inf`), and stable all-rank
merge
semantics.

## API and ABI

The public API adds optional `cp_world=1`, `cp_rank=0`, and
`causal_seqlens_kv_global=None` arguments. Callers continue to use the
existing
public `backend="auto"` or `backend="trtllm-gen"` entry point; after DCP
metadata
selects the route, the dispatcher uses the internal explicit
`backend="cake"`
call-down.

Q is rank 3 (`[B*q_len,Hq,D]`) and split K/V are rank 4
(`[num_pages,Hkv,page_size,D]`). Generated bindings reject additional
leading
dimensions. Graph-stable use supplies caller-owned BF16 O, FP32 base-2
LSE,
reusable Split-KV workspace, and zero-initialized reusable completion
tickets.
Fixed tensor/layout bindings must be prewarmed before CUDA Graph
capture.

After JIT/prewarm, one Cake invocation launches exactly one GPU kernel.
Empty
local ranks preserve the same one-launch ABI.

## Supported profiles

- BF16 D128/page16/HND: `q_len={1,2,4,5,6,8}`, integer `Hq/Hkv` in
`[1,8]`,
  and `cp_world={1,2,4,8}`.
- FP8 E4M3 D128/page64/HND: the continuous `q_len={1,2,3,4,5,6,7,8}`
range,
  integer `Hq/Hkv` in
  `[1,8]`, `cp_world={1,2,4,8}`, split1--4, and retain0/retain1 bodies.
- FP8 E4M3 D256/page64/HND: the continuous `q_len={1,2,3,4,5,6,7,8}`
range,
`Hq/Hkv=16/1`, and `cp_world={1,4}`. The CP4 serving profile uses global
  context 32768 and maximum rank-local length 8192.
- The D256 generated family contains retain0
split1/split2/split3/split4/
  split8/split16 bodies. The existing q4 CP4 routing policy selects
split8/split4/split2/split1 for `B=1/8/16/>=32`; every B128
q1-through-q8
  reviewer row selects split1. CP1 may select through split16.
- Generated targets cover SM100 and SM103 independently.

## CUDA Graph and activity contract

The reviewer matrix covers B128, CP4, all four ranks, and every D256
query
length from 1 through 8 with caller-owned capture and three replays: 32
exact
prepared routes. It verifies rank-local outputs, empty-rank neutral
values,
merged output/LSE, completion-ticket reset, pointer stability, and
replay
stability. The public exact-head Graph denominator is 8/8.

The public promotion hook requires at least two visible GPUs and
intentionally
uses devices 0 and 1. It runs unchanged on hosts exposing additional
GPUs;
regression coverage includes visible-device counts 1, 2, and 4.

Reportable timing uses alternating cold-L2 CUPTI correlation over the
complete
callable, with 20 ms warmup, 300 ms measurement, and three same-session
pairs.
Cake contributes exactly one correlated GPU activity per invocation. The
comparison peer is the public TRTLLM-Gen callable through the
exact-semantics
row-expanded-q1 adapter; every GPU activity inside that peer callable is
retained. This is not a Triton DCP comparison or a comparison against an
unavailable native DCP implementation.

## Generated source inventory and parity

The checked-in family contains exactly 37 files: 31 route bodies plus
four
bindings and two manifests. The q7 profile adds no kernel specialization
or
schedule. Regeneration after the source rebase adds compiler-visible
memory
clobbers to mbarrier initialization and publication fences in the 31
existing
device bodies. B200 and GB300 both prove 37/37 private/public generated
parity;
both architectures also pass exact-head split1/split2/split4/split8
synccheck
and memcheck without reusing older source-bound sanitizer receipts.

## Performance and promotion status

The fixed q1-through-q8 denominator contains 112 rows: 57 ordinary
Cake-versus-public-peer rows, 40 DCP-overhead rows, and 15
correctness-only
rows. A separate unchanged 25-shape cold-L2 CUPTI regression covers
production
dispatcher thresholds.

Exact-head status:

- GB300 passes 112/112 rows with a `1.095704` minimum normalized gate,
`2.154022x` ordinary geometric-mean speedup, `1.120523x` minimum
ordinary
speedup, `1.003921x` worst same-local DCP ratio, and `0.581745x` worst
raw
  same-global DCP ratio. Dispatcher-25 measures `0.2661 ms` against the
  `0.7031 ms` floor (`+62.2%`).
- B200 passes 112/112 rows with a `1.093768` minimum normalized gate,
`2.198186x` ordinary geometric-mean speedup, `1.146389x` minimum
ordinary
speedup, `1.005698x` worst same-local DCP ratio, and `0.586406x` worst
raw
  same-global DCP ratio.
Dispatcher-25 measures `0.280227 ms` against its unchanged floor
(`61.2%`
  margin).
- GB300 passes reviewer correctness 8/8, 32/32 prepared routes, direct
and
  registered dual-112, dispatcher 25/25, and 38/38 spill-free SM103 SASS
variants. Public validation passes JIT 35/35, Graph 8/8, the real
two-GPU API
  hook, and generated-source parity 37/37.
- B200 passes reviewer correctness 8/8, 32/32 prepared routes, direct
and
registered dual-112, dispatcher 25/25, 76/76 SM100+SM103 SASS variants,
  public JIT 35/35, Graph 8/8, and generated-source parity 37/37.
- Exact-head promoted-route synccheck/memcheck requalification passes
all 8/8
  combinations with zero errors on both GB300 and B200.
- Exact-head public CI passes on candidate
  `fde25da21966b3956e910d05660eb6eae4c05b95`: PR Test run `33081623448`
and Build FlashInfer Docs run `33081538233` both complete successfully.

Fresh per-query B200 and GB300 CUPTI results are posted in the q-length
review
reply on this PR.

Implements #4323.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [286eee4](https://github.com/flashinfer-ai/flashinfer/commit/286eee4e2999a825716eab68e597cb1ee0881e1b)

- **作者**: Nader Al Awar
- **时间**: 2026-08-27T16:39:19Z
- **提交信息**: feat: CUB `DeviceBatchedTopK` top-k backend with variable-length support (#4442)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds a new API, `top_k_cub`, that uses `cub::DeviceBatchedTopK`
internally. It supports fp32/fp16/bf16 inputs, tie-break modes, per-row
variable lengths, and CUDA graph capture — including the
variable-lengths path, where lengths is read on the device, so a
captured graph can be replayed with different per-row lengths at a fixed
shape.

This improves performance for plain top_k across the board: CUB wins
about 85% of benchmarked shapes in eager mode (geomean ~1.6x over the
radix default) and 94-97% under CUDA graphs (geomean 1.7-2.0x), with the
only weak spot being large batches (128+) at sequence lengths around
16k-64k. The biggest win is tie-break: it costs CUB only ~3-9% over its
own baseline while the native tie-break path is much slower, leaving CUB
~1.5-2x faster, and CUB supports tie-break at k=4096, which the native
path rejects. The fused transforms favor the native kernels in eager
mode, but under CUDA graphs (how SGLang calls them) CUB wins from mid
sequence lengths up and nearly everywhere with tie-break. Shape-based
gates in the dispatcher route each call to the faster backend
automatically. Full performance results here:
https://gist.github.com/NaderAlAwar/4038e4c44365b93737a55add0e6ec1b5

As a follow up, we plan on making the following improvements in future
PRs:
- Allow specifying exact dtypes in `gen_topk_module` to improve
compilation times (currently we compile all dtypes)
- Allow specifying certain runtime parameters that we know won't change
as compile time parameters by passing them to `gen_topk_module` to
improve performance. For example, this applies to the max row length in
the variable lengths path
- Support `sorted=True`
- Support `deterministic=True`
- Further optimize `cub::DeviceBatchedTopK` to improve performance


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

This PR depends on https://github.com/NVIDIA/cccl/pull/9224, and should
therefore remain in draft until that PR is merged. We should also update
the CCCL submodule to use a more recent commit that includes the changes
added in that PR.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optimized CUB backend for standard, ragged, and page-table
top-k operations.
* Top-k automatically selects the most suitable backend based on input
characteristics and execution mode.
* Added workspace queries, custom workspaces, tie-breaking, raw-index
outputs, and CUDA Graph-compatible execution.
  * Short transformed rows now use `-1` padding where applicable.

* **Performance**
* Expanded benchmark coverage and backend comparisons, including CUDA
Graph-aware measurements.

* **Documentation**
* Updated top-k API and configuration documentation with backend
selection details.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Ziang Li <ziangli@umich.edu>

### [737c7dd](https://github.com/flashinfer-ai/flashinfer/commit/737c7ddf1ab380065e4f3546a9e428f1ceadd902)

- **作者**: Xuanteng Huang
- **时间**: 2026-08-27T14:58:04Z
- **提交信息**: Support per-token NVFP4 ReLU2 MoE (#4618)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds the per-token NVFP4 MoE kernel with ReLU2 as the activation
(used by Nemotron 3).

## 🔍 Related Issues

Fixes #3584 

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
* Added CUTLASS support for NVFP4, FP8, MXFP8/MXFP4, W4A8, and Humming
MoE quantization formats.
* Added support for Relu2 activation alongside SwiGLU in TensorRT-LLM
FP4 routed MoE workflows.
* Added per-tensor and block scaling options for supported FP8
workflows.
* Added backend-specific weight preparation and validation for supported
GPU architectures.

* **Bug Fixes**
* Improved CUDA compatibility messages and corrected FP4/FP8 shape and
scaling documentation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Xuanteng Huang <xuantengh@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4088
- **最后更新**: 2026-08-28T04:50:12Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

### 主要更新类型
- **功能新增**：为 MiniMax H3 模型添加了 LoRA（低秩适配）推理和预览启动器。

### 关键变更点及其与项目整体方向的关系
- 新增了针对 MiniMax H3 的 LoRA 推理启动器和预览启动器，使 FastVideo 能够支持该模型的微调后推理。
- 这与项目“快速视频生成与推理”的核心目标一致，扩展了模型兼容性，特别是对 MiniMax 系列的支持，增强了项目的通用性和实用性。

### 对项目的影响和潜在意义
- 使 FastVideo 用户能够直接使用 MiniMax H3 的 LoRA 微调模型进行推理和预览，降低了使用门槛。
- 丰富了项目支持的模型生态，可能吸引更多使用 MiniMax 模型的开发者，提升项目在视频生成领域的竞争力。

### 值得关注的技术点
- LoRA 推理支持意味着项目已具备处理低秩适配权重的能力，这通常涉及权重合并或动态加载，对推理性能优化有潜在价值。
- 预览启动器的加入可能意味着提供了更便捷的交互式体验，方便用户快速验证模型输出。

### 基于README的项目背景，这些提交如何影响项目发展
- FastVideo 旨在提供高效、易用的视频生成工具链，此次提交通过扩展模型支持范围，进一步巩固了其作为通用视频生成框架的定位。
- 结合项目文档和社区活跃度（如每周开发会议），该功能可能吸引更多社区贡献，推动项目在模型适配和推理优化方面的持续迭代。

## 详细提交记录

### [a534ba2](https://github.com/hao-ai-lab/FastVideo/commit/a534ba20a02268689afb0513ec8d3e7d45586194)

- **作者**: William Lin
- **时间**: 2026-08-27T21:43:39Z
- **提交信息**: [feat] Add MiniMax H3 LoRA inference and preview launchers (#1771)

Co-authored-by: shaoxiongduan <shaoxiongduan@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34395
- **最后更新**: 2026-08-28T04:45:03Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 2
- **主要提交者**: Akshan Krithick, Sayak Paul

## AI分析总结

# 提交分析报告

## 1. 主要更新类型

本批次提交以**测试重构与迁移**为核心，辅以**CI修复**和**依赖清理**。具体包括：测试基础设施迁移（lora、flux、sdxl、zimage、krea2等）、废弃依赖移除（quanto）、新增测试覆盖（ideogram4）、CI编译测试修复。

## 2. 关键变更点

- **测试体系现代化**：将lora、flux、sdxl等大量测试从旧结构迁移至新的pipeline-level mixins，统一测试模式，提升可维护性。
- **依赖清理**：移除quanto相关测试并标记弃用，简化依赖树，聚焦核心功能。
- **新增覆盖**：为ideogram4管线添加完整测试，填补新模型测试空白。
- **CI修复**：修正编译测试的调用方式，保障CI稳定性。

## 3. 项目影响与意义

这些变更显著提升测试代码质量与一致性，降低维护成本。通过统一测试基座，新管线开发可复用成熟测试模式，加速迭代。移除quanto测试减少CI负担，同时明确技术方向——不再维护该集成。

## 4. 值得关注的技术点

- **pipeline-level mixins模式**：将通用测试逻辑抽象为mixin，实现跨管线复用，是测试架构的重要演进。
- **远程解码测试修复**：针对特定场景的测试可靠性优化。
- **容差放宽与跳过策略**：在ideogram4测试中灵活调整断言阈值和跳过条件，平衡测试严格性与实用性。

## 5. 对项目发展的影响

diffusers作为多模型统一推理库，测试体系的可扩展性至关重要。本批次提交通过重构测试架构，为持续接入新模型（如ideogram4）铺平道路，同时清理技术债务（quanto），使项目更聚焦于核心扩散模型生态。测试迁移工作虽不直接面向用户，但为后续功能开发提供了更稳固的质量保障基础，符合项目作为基础设施库的长期定位。

## 详细提交记录

### [119c339](https://github.com/huggingface/diffusers/commit/119c339551f68ea523b9f204120b929e56342421)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T12:04:54Z
- **提交信息**: ci: fix invocation for compile tests. (#14552)

ci: fix invokation for compile tests.

### [df07532](https://github.com/huggingface/diffusers/commit/df07532b397bd9b143d1cff97596df6017a38820)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T09:38:42Z
- **提交信息**: tests: migrate tests from tests/lora (#14559)

* tests: migrate tests from tests/lora

* up

### [daad99a](https://github.com/huggingface/diffusers/commit/daad99a04afc085b9604c4acd7dd4c8830773682)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T08:29:40Z
- **提交信息**: [tests] remove quanto tests. (#14254)

* remove quanto tests.

* deprecate quanto and remove tests

### [2371082](https://github.com/huggingface/diffusers/commit/2371082217eec63ab3a82756d8ff92b072ad66f7)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T08:00:12Z
- **提交信息**: [tests] refactor sdxl tests. (#14619)

refactor sdxl tests.

### [3d8d2e7](https://github.com/huggingface/diffusers/commit/3d8d2e7218d7b63dd5cfe3d0868084def2e40a5f)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T07:59:56Z
- **提交信息**: [tests] refactor zimage and krea2 pipeline tests (#14563)

* refactor zimage and krea2 pipeline tests

* remove group offloading skip and propaget the refactors to the rest of zimage

* add negative prompt

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [fc1b287](https://github.com/huggingface/diffusers/commit/fc1b2870cc7c5822c83012bf401d304385f0feb3)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T07:32:34Z
- **提交信息**: [tests] migrate remaining flux pipeline tests to use new mixins (#14560)

* migrate remaining flux pipeline tests to use new mixins

* up

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [0351a3a](https://github.com/huggingface/diffusers/commit/0351a3ab30827a0a9903bf95c77b8584b95595b8)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T07:30:26Z
- **提交信息**: [tests] fix remote decoding tests and disable encode tests. (#14601)

fix remote decoding tests and disable encode tests.

### [02654ab](https://github.com/huggingface/diffusers/commit/02654ab749ce7f60b41ed4102be23fb90257e3d2)

- **作者**: Sayak Paul
- **时间**: 2026-08-27T07:03:44Z
- **提交信息**: tests: add ideogram4 tests for pipelines. (#14599)

* tests: add ideogram4 tests for pipelines.

* skip callback tests

* Update tests/pipelines/ideogram4/test_pipeline_ideogram4.py

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

* up

* up

* allow pipeline level group offloading test

* loosen tolerance.

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [913ab22](https://github.com/huggingface/diffusers/commit/913ab2281aee282d9ca3d60e44721a25b6fd09c1)

- **作者**: Akshan Krithick
- **时间**: 2026-08-27T07:01:17Z
- **提交信息**: migrate wan lora tests to the pipeline-level mixins (#14613)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
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


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13013
- **最后更新**: 2026-08-28T00:10:28Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Li

## AI分析总结

# DiffSynth-Studio 提交分析报告

## 1. 主要更新类型

本次提交包含**功能新增**（CFG感知微调损失、文件重定向支持）和**Bug修复**（分片训练问题）两类更新，无文档或重构类变更。

## 2. 关键变更点与项目方向

- **CFG感知微调损失**：为MiniMax-H3模型引入训练时CFG（Classifier-Free Guidance）缩放参数，使损失计算能感知正负样本条件，显著提升视频-音频联合微调的灵活性。
- **文件重定向支持**：增强MiniMax模型的数据输入能力，允许通过文件重定向方式加载训练数据，简化大规模数据集的配置流程。
- **分片训练Bug修复**：解决分布式训练中分片逻辑的缺陷，保障多卡训练稳定性。

这些变更紧密围绕DiffSynth-Studio作为**视频生成与编辑工具**的核心定位，特别是对MiniMax-H3这一关键视频生成模型的支持深化，符合项目持续优化生成质量与训练效率的方向。

## 3. 项目影响与潜在意义

- **训练质量提升**：CFG感知损失使模型能更好区分条件与无条件生成，预期提升视频生成的一致性和可控性，对高质量视频合成有直接推动作用。
- **易用性增强**：文件重定向支持降低了用户准备训练数据的门槛，配合脚本注释改进，使MiniMax-H3的微调流程更友好，有助于吸引更多社区用户参与。
- **稳定性保障**：分片训练修复避免了多卡场景下的潜在错误，确保大规模训练任务可靠运行，为项目在复杂生产环境中的部署奠定基础。

## 4. 值得关注的技术点

- **CFG缩放参数设计**：将`training_cfg_scale`和`inputs_nega`参数引入损失函数，体现了对扩散模型训练中引导机制的精细化控制，是提升生成质量的关键创新。
- **训练脚本可配置性**：通过Shell脚本注释明确可选配置项，体现了项目对可复现性和用户自定义需求的重视。

## 5. 对项目发展的影响

结合README中DiffSynth-Studio作为**开源视频生成与编辑平台**的定位，这些提交强化了其对先进模型（MiniMax-H3）的适配能力，同时通过训练优化和易用性改进，巩固了项目在视频生成领域的竞争力。CFG感知损失和文件重定向支持为社区用户提供了更强大的微调工具，有望吸引更多开发者基于此构建定制化视频生成应用，推动项目生态的持续扩展。分片训练修复则保障了项目在规模化应用中的可靠性，为未来支持更大模型和更复杂任务奠定基础。整体而言，本次提交体现了项目在**技术深度**与**用户体验**上的双重推进，符合其作为趋势性开源项目的成长轨迹。

## 详细提交记录

### [71f6ebf](https://github.com/modelscope/DiffSynth-Studio/commit/71f6ebf84ffc4b5eb0aa720020b6e54ac03e6073)

- **作者**: Li
- **时间**: 2026-08-27T12:59:06Z
- **提交信息**: feat: add CFG-aware fine-tuning loss for MiniMax-H3 (#1650)

* feat: add CFG-aware fine-tuning loss for MiniMax-H3

Refactor FlowMatchSFTMiniMaxH3AudioVideoLoss to include training_cfg_scale and inputs_nega parameters for enhanced functionality.

* feat: expose MiniMax-H3 training CFG scale

Added training_cfg_scale parameter to control CFG scaling during training and updated related logic in the training process.

* Enhance MiniMax-H3-FL2VA.sh with training config notes

Added comments for optional training configuration.

* minor clean

---------

Co-authored-by: yjy415 <2471352175@qq.com>

### [f1ab0fb](https://github.com/modelscope/DiffSynth-Studio/commit/f1ab0fbf37a8c317758906d7f9ad44c25c6a92a9)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-27T10:27:23Z
- **提交信息**: support file redirection of MiniMax (#1649)

* support file redirection of MiniMax

### [746c6b2](https://github.com/modelscope/DiffSynth-Studio/commit/746c6b24bc4f15c2e9bb1a1c9ff53ec0c9e8ddfb)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-27T09:24:58Z
- **提交信息**: bugfix: split-training (#1648)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32593
- **最后更新**: 2026-08-28T04:58:01Z

## 提交统计

- **昨日提交总数**: 43
- **提交者数量**: 26
- **主要提交者**: Cheng Wan, GoldPancake, Khoa Pham

## AI分析总结

# SGLang 昨日提交分析总结

## 一、主要更新类型

本次43条提交涵盖**Bug修复**（约15条）、**性能优化**（约10条）、**代码重构**（约8条）、**文档更新**（约6条）及**新功能开发**（约4条），整体呈现“修复与优化并重、重构与文档同步推进”的态势。

## 二、关键变更点与项目方向

1. **多硬件平台适配深化**：XPU/ROCm/NPU相关修复（延迟导入、OOB gather修复、MLA HiCache备份修复）持续强化SGLang作为**跨平台推理引擎**的定位，与README中强调的多硬件支持目标一致。
2. **Diffusion模型支持扩展**：多条提交聚焦LingBot-Video、Cosmos3 Nano、LongCat、Wan等模型的注意力融合、GELU融合和文本编码修复，表明项目正从纯LLM推理向**多模态生成**方向拓展。
3. **配置系统重构**：系列提交（config相关5条、server_args重构2条）重构配置解析与传递机制，提升代码可维护性，为后续功能扩展奠定基础。
4. **AMD/CI优化**：合并MI35x nightly任务、添加Mori测试标签，体现对AMD生态的持续投入和CI效率的重视。

## 三、项目影响与潜在意义

- **稳定性提升**：多项针对特定硬件（NPU、XPU）的bugfix和speculative解码崩溃修复，直接提升生产环境可靠性。
- **性能优化**：H200 MoE配置、TMA调优、GELU融合等优化，在保持通用性的同时追求极致性能。
- **架构演进**：Mixed Chunk Prefill Base（#36288）作为新功能基础，可能改变prefill策略；per-scheduler负载发布为负载感知路由铺路。

## 四、值得关注的技术点

1. **Mixed Chunk Prefill**（#36288）：混合chunk预填充机制，可能显著提升长序列处理效率。
2. **统一控制平面**（#36160）：prefill传输控制平面对齐，为异构设备协同打基础。
3. **多模态嵌入缓存重编码**（#36595）：解决缓存不匹配问题，对多模态推理正确性至关重要。
4. **CUDA图内存优化**（#35275）：speculative adaptive的显存优化，降低推理资源门槛。
5. **Mori后端支持**（#35611）：DeepSeek-V4 prefill上下文并行，紧跟前沿模型需求。

## 五、对项目发展的影响

结合README中SGLang“快速、高效、灵活的AI推理框架”定位，这些提交呈现三个发展方向：**一是平台覆盖扩大**，从NVIDIA向AMD、NPU、XPU全面延伸；**二是能力边界拓展**，从文本生成向视频、图像等多模态领域渗透；**三是工程化成熟度提升**，通过配置重构、CI优化和文档完善，降低使用门槛。整体来看，项目正从“LLM推理引擎”向“通用多模态推理平台”演进，同时保持对性能极致追求和硬件生态兼容性的双重承诺。

## 详细提交记录

### [7cbe564](https://github.com/sgl-project/sglang/commit/7cbe5648295e363b151d9c0221c4b1adb14511e8)

- **作者**: ashwini rathi
- **时间**: 2026-08-27T23:17:24Z
- **提交信息**: [Fix][XPU/ROCm/NPU] Defer sgl_kernel.quantization import in expert_pack (#36529)

### [76217f6](https://github.com/sgl-project/sglang/commit/76217f660365c373d65a47ba0f6e34c8cba1187b)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-27T23:16:30Z
- **提交信息**: Revert "[NPU] [bugfix] Fix import of ggml_moe_a8_vec and Fix NPU MLA HiCache backup accessing missing data_ptrs" (#36747)

### [5640e53](https://github.com/sgl-project/sglang/commit/5640e53cab65e52c65629cbc0069370573e81d8a)

- **作者**: chx96642264
- **时间**: 2026-08-27T23:14:48Z
- **提交信息**: [NPU] [bugfix] Fix import of ggml_moe_a8_vec and Fix NPU MLA HiCache backup accessing missing data_ptrs (#36640)

Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [5d52f02](https://github.com/sgl-project/sglang/commit/5d52f02f229119115878f84a09e2a7e2bc74fc47)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-27T23:12:47Z
- **提交信息**: [misc] Fold the allocator free-group flag into `free_group` (#36739)

### [6ccfeb5](https://github.com/sgl-project/sglang/commit/6ccfeb59bcbc3e6ecf1b714b2241e2b05a19079e)

- **作者**: zijiexia
- **时间**: 2026-08-27T23:03:59Z
- **提交信息**: cookbook: add a Speculative card to the GLM-5.3-Flash playground (#36740)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [dc10483](https://github.com/sgl-project/sglang/commit/dc1048359243f1d7a451e5e5047d6b176aaf5e51)

- **作者**: Vedant V Jhaveri
- **时间**: 2026-08-27T23:01:22Z
- **提交信息**: [Kernel] Add H200 MoE configs for Qwen3.5 and Qwen3.6 (#35374)

Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [e283c9f](https://github.com/sgl-project/sglang/commit/e283c9f8ea3bf5873a58e5c986a8ae0f62706428)

- **作者**: Michael
- **时间**: 2026-08-27T22:40:27Z
- **提交信息**: [AMD][CI] Merge the four MI35x DeepSeek-V3.2 nightly jobs into two to save runtime (#36736)

Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: quitenode <quitenode@users.noreply.github.com>

### [0132848](https://github.com/sgl-project/sglang/commit/0132848349585cfe6aae51c4941cbae872505f8a)

- **作者**: sky
- **时间**: 2026-08-27T21:19:27Z
- **提交信息**: Revert "[Fix] Disable --enable-symm-mem under CUDA graphs on Kimi hybrid models" (#34842)

Signed-off-by: wangfakang <fakangwang@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ff5578e](https://github.com/sgl-project/sglang/commit/ff5578eb4e1d68d842303e3ab9ce4c86038c1c26)

- **作者**: Yuwei An
- **时间**: 2026-08-27T19:59:56Z
- **提交信息**: [1/N][Mix] Mixed Chunk Prefill Base (#36288)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [6ff2a20](https://github.com/sgl-project/sglang/commit/6ff2a20ccf64b64a6bb6d9a54c7b0e605f673da2)

- **作者**: Cheng Wan
- **时间**: 2026-08-27T19:57:10Z
- **提交信息**: config: the record is not an object that gets passed around (#36622)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [fd40a33](https://github.com/sgl-project/sglang/commit/fd40a331bf7d72a124375823b382b5df5bca77f5)

- **作者**: Cheng Wan
- **时间**: 2026-08-27T19:56:42Z
- **提交信息**: config: a parallel size has one spelling; a patched scope declares its own (#36621)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [ca1d7ed](https://github.com/sgl-project/sglang/commit/ca1d7ed8e64c3f8bc43065307dd40d5175870732)

- **作者**: Cheng Wan
- **时间**: 2026-08-27T19:56:11Z
- **提交信息**: config: a parallel leaf with no live counterpart is read bare (#36620)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7c3b5a6](https://github.com/sgl-project/sglang/commit/7c3b5a6732fbacc4d63beb0185141e7a2ec62496)

- **作者**: Cheng Wan
- **时间**: 2026-08-27T19:55:34Z
- **提交信息**: config: every handler declares its cuda-graph decisions (#36725)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [bd4bb17](https://github.com/sgl-project/sglang/commit/bd4bb1781a95e8298546feab69122897e0aaec1d)

- **作者**: Cheng Wan
- **时间**: 2026-08-27T19:53:17Z
- **提交信息**: config: resolution declares, and nothing writes a field (#36618)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [d1f1443](https://github.com/sgl-project/sglang/commit/d1f14431fdf036b386bec347461df004c99ed88c)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-27T19:18:25Z
- **提交信息**: GLM-5.3-Flash cookbook: HiCache for LL, fusion-flag drop, EAGLE, default-cell numbers, DCP4 overlay (#36544)

### [46a544e](https://github.com/sgl-project/sglang/commit/46a544e0a067a7c88a2470e55dbee19a6c110873)

- **作者**: zijiexia
- **时间**: 2026-08-27T19:16:35Z
- **提交信息**: [Docs] GLM-5.3-Flash: point at compute-mamba-ratio for the KDA/KV pool split (#36719)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [a0a2295](https://github.com/sgl-project/sglang/commit/a0a22952717a023d7c11210d963d24bb258a9275)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-27T19:16:16Z
- **提交信息**: Refactor server_args constants and layout (#36676)

### [11de5e2](https://github.com/sgl-project/sglang/commit/11de5e22818700f98239736d6834e193b445d0e4)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-27T19:15:17Z
- **提交信息**: docs(cookbook): add GB10 (DGX Spark) MXFP4 cells for Ling-3.0-flash (#36364)

### [20a491d](https://github.com/sgl-project/sglang/commit/20a491d1d311553bbab3f22e19bbafb86ef3c0cc)

- **作者**: Mick
- **时间**: 2026-08-27T15:24:30Z
- **提交信息**: [Fix] Re-encode multimodal embeddings after cache mismatch (#36595)

Co-authored-by: john.xh <dengxuhuijohn@gmail.com>

### [024a7a1](https://github.com/sgl-project/sglang/commit/024a7a1031fd7d789076f90e203e3a51b9656cb3)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T14:58:22Z
- **提交信息**: [diffusion] Fix native LingBot-Video text encoding (#36542)

### [8ad7641](https://github.com/sgl-project/sglang/commit/8ad76415e2db30cdc35d1863304434ab042591fd)

- **作者**: inkcherry
- **时间**: 2026-08-27T13:43:13Z
- **提交信息**: [PD][mori] Align prefill transfer control plane for unified control plane (#36160)

### [a7e3f59](https://github.com/sgl-project/sglang/commit/a7e3f590cabb676a02181fb3328026587822f934)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T13:07:04Z
- **提交信息**: [Diffusion] Fuse LongCat residual gate updates (#36577)

### [e061dd1](https://github.com/sgl-project/sglang/commit/e061dd1b470ac7726a0808f31e22518eb903484f)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T13:06:28Z
- **提交信息**: [Diffusion][Kernel] Fuse Wan FFN GELU epilogue (#36592)

### [1af95ff](https://github.com/sgl-project/sglang/commit/1af95ffded20fdf78162b66d40d669a0c57c5a83)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T12:59:15Z
- **提交信息**: [diffusion] Fuse Cosmos3 Nano T2I attention on Hopper (#36571)

### [db4125b](https://github.com/sgl-project/sglang/commit/db4125bb5689a230b21e015f05c125c40a64e12f)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T12:53:25Z
- **提交信息**: [diffusion] Accept mesh benchmark artifacts (#36553)

### [d42fa5e](https://github.com/sgl-project/sglang/commit/d42fa5e10a74b6faa26ba5a318e28cecb9df5131)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T12:52:00Z
- **提交信息**: [diffusion] align video BCG warmup frame count (#36485)

### [b647ae8](https://github.com/sgl-project/sglang/commit/b647ae82f524ed5e607ac39286ed50ee0b90d023)

- **作者**: xdtbynd
- **时间**: 2026-08-27T11:44:45Z
- **提交信息**: [NPU][Bugfix] Fix OOB gather in decode KV allocation when free pool is tight (#35727)

### [97ba990](https://github.com/sgl-project/sglang/commit/97ba99067dc1915771edc96972a8dbd08dc21148)

- **作者**: Shangming Cai
- **时间**: 2026-08-27T11:33:18Z
- **提交信息**: Publish per-scheduler load on a dedicated socket for load-aware routers (#34608)

Co-authored-by: Kangyan Zhou <zky314343421@gmail.com>
Co-authored-by: Zhangheng <hzh0425@apache.org>

### [94183a8](https://github.com/sgl-project/sglang/commit/94183a8d2b357a3200c97a1d7fccd2b866b8eda3)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-27T10:34:50Z
- **提交信息**: Move server args config parser under utils (#36681)

### [536f570](https://github.com/sgl-project/sglang/commit/536f570e6692eec0656ef9689db7591ca1d0e0a7)

- **作者**: Julian Huang
- **时间**: 2026-08-27T09:49:03Z
- **提交信息**: docs(cookbook): fix Qwen3.8 Flash Next H200 MTP verify with BF16 SSM state (#36611)

### [ad911a5](https://github.com/sgl-project/sglang/commit/ad911a5ec07b958f01f8d90b5101d01cefbd3eb5)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-27T09:47:32Z
- **提交信息**: [kernel] Tune LingBot-Video MoE TMA configs for H100 (#36543)

### [08315c5](https://github.com/sgl-project/sglang/commit/08315c56df3886d8d584f2766712018402c4f585)

- **作者**: Schwinn Saereesitthipitak
- **时间**: 2026-08-27T09:43:04Z
- **提交信息**: [Fix] Account resident weight memory in KV sizing (#34053)

Signed-off-by: Schwinn Saereesitthipitak <schwinns@nvidia.com>

### [56fdfc3](https://github.com/sgl-project/sglang/commit/56fdfc3b26010ee9889a6498ae963260c4dad711)

- **作者**: Xia Weiwen
- **时间**: 2026-08-27T09:38:02Z
- **提交信息**: XPU: remove SGLANG_USE_SGL_XPU flag (#34492)

### [78d36f5](https://github.com/sgl-project/sglang/commit/78d36f5f62d514f2fe4712bb21c547db66063955)

- **作者**: Khoa Pham
- **时间**: 2026-08-27T09:34:05Z
- **提交信息**: fix: kill_process_tree waits for the reap by default (#36589)

### [2ded8a6](https://github.com/sgl-project/sglang/commit/2ded8a6aeaebe235e7f72a4580b5d6effed09bd1)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-08-27T09:31:41Z
- **提交信息**: [AMD] Enable moe_a2a_backend=mori for DeepSeek-V4 prefill context parallelism (#35611)

### [636a6f7](https://github.com/sgl-project/sglang/commit/636a6f7dbad251f22a1c31d46b0b97ba8154a9a0)

- **作者**: zijiexia
- **时间**: 2026-08-27T09:19:47Z
- **提交信息**: cookbook: fix GLM-5.3-Flash speculative flag, size Hopper memory, record GSM8K (#36660)

### [3402265](https://github.com/sgl-project/sglang/commit/3402265989c6214ed53b48aa359693aa4d277476)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-27T08:56:03Z
- **提交信息**: [Core] Refactor server argument choices (#36586)

### [a126a5f](https://github.com/sgl-project/sglang/commit/a126a5fa319d564a464d817d5863fe13e1c1d402)

- **作者**: Alison Shao
- **时间**: 2026-08-27T08:36:04Z
- **提交信息**: [CI] Graceful teardown for the radix_cache server fixtures (#36605)

### [c2c3320](https://github.com/sgl-project/sglang/commit/c2c3320cf0a4f40e24ae1275e2a7af77e826b54e)

- **作者**: Mick
- **时间**: 2026-08-27T08:32:58Z
- **提交信息**: [VLM] feat: size the multimodal preprocessing pool by where preprocessing runs (#35349)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [c608f9b](https://github.com/sgl-project/sglang/commit/c608f9bf7581ea87dd2efccfc34093e22b3e8810)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-08-27T08:00:22Z
- **提交信息**: [CI] Fix Q8KV8 sparse prefill test fixture (#36639)

### [b8a6ada](https://github.com/sgl-project/sglang/commit/b8a6adadfe8c292fbb673291dbd2a5d23232f500)

- **作者**: GoldPancake
- **时间**: 2026-08-27T07:46:13Z
- **提交信息**: [Bug][Spec] fix startup crash and reduce CUDA graph memory usage for speculative adaptive (#35275)

Co-authored-by: alphabetc1 <2508695655@qq.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1a91c23](https://github.com/sgl-project/sglang/commit/1a91c232ea65630f2cee33bd93844f1f715fe738)

- **作者**: inkcherry
- **时间**: 2026-08-27T07:24:02Z
- **提交信息**: [AMD][CI] Add targeted Mori test labels (#36636)

Signed-off-by: inkcherry <mingzhi.liu@amd.com>

### [c967cd1](https://github.com/sgl-project/sglang/commit/c967cd19b56be8efed19e801357d437b5c1fe34c)

- **作者**: jacky.cheng
- **时间**: 2026-08-27T07:13:49Z
- **提交信息**: [AMD] Optimize Qwen3.5 MTP unified attention on gfx950 (#36330)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1260
- **最后更新**: 2026-08-27T11:36:32Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# 提交分析报告

## 1. 主要更新类型
本次提交属于**性能优化**和**代码重构**，核心目标是消除注意力机制中的非必要内存拷贝，提升推理效率。

## 2. 关键变更点
- **NHD直通路径**：将diffusers原生NHD格式的Q/K/V张量直接传递给ffpa-attn的persist-D内核，跳过原有的permute视图转换和BHND存储格式。
- **零拷贝输入判断**：新增`is_nhd_zero_copy_input`接口，按张量粒度判断是否可直通，不满足条件时回退到`.contiguous()`。
- **后端能力下沉**：将NHD支持规则（fp16 D≤128、fp4 D≤256、hybrid/hadamard拒绝）移入`CUDABackend.is_nhd_supported`，统一由后端工厂决策。
- **因果注意力支持**：明确允许causal attention走NHD路径，避免hybrid回退。

## 3. 对项目的影响
- **性能提升显著**：FLUX 1024×1024端到端测试中，ffpa_fp8从与sage持平（16.54s）变为稳定领先（16.47/16.51s vs 16.54/16.54s），单次注意力节省0.233ms（N=16896）。
- **消除下游拷贝**：非连续的NHD输出视图此前迫使diffusers的FluxAttnProcessor执行`flatten(2,3)`时发生strided copy，现在内核直接输出连续NHD，彻底移除该开销。
- **架构更清晰**：NHD支持规则从调用方逻辑收敛到后端实现，职责边界更明确，便于后续扩展新后端。

## 4. 值得关注的技术点
- **零拷贝判断的粒度**：按张量而非整体配置决定是否直通，兼顾灵活性与正确性。
- **优雅降级策略**：不满足NHD条件（如grad-on、fp4混合精度、CP重组）时自动回退legacy permute路径，保证功能完整性。
- **测试策略转变**：非连续V的测试从断言“物化”改为断言“零拷贝直通”（验证data_ptr/strides不变），确保优化不被回归。

## 5. 对项目发展的意义
cache-dit定位为PyTorch原生的DiT推理引擎，核心卖点是缓存、并行、量化与CPU offload。本次提交直接强化了**“原生”**这一关键属性——通过消除与diffusers生态之间的格式转换开销，使ffpa-attn真正融入PyTorch张量流。性能从“与sage持平”到“稳定领先”的转变，意味着在竞争激烈的DiT推理赛道中，cache-dit获得了可量化的差异化优势。同时，将NHD支持规则下沉到后端，为未来接入更多硬件后端（如AMD、NPU）奠定了更干净的抽象层，符合项目长期扩展的架构方向。

## 详细提交记录

### [6a9bfd3](https://github.com/vipshop/cache-dit/commit/6a9bfd3daac8cfde4405f438ab6e6961dc1ca060)

- **作者**: DefTruth
- **时间**: 2026-08-27T11:33:41Z
- **提交信息**: ffpa: pass strided-NHD inputs through for all families (#1106)

ffpa-attn fp8/fp4/fp16 persist-D kernels now consume strided-NHD
views natively, so the NHD fast path no longer materializes
non-contiguous Q/K/V. Use ffpa_attn.is_nhd_zero_copy_input (when
available) to decide per tensor: pass through when the relaxed
gate accepts it, else fall back to .contiguous().

Flip the noncontiguous-V test to assert zero-copy pass-through
(same data_ptr/strides) instead of materialization.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

### [d094874](https://github.com/vipshop/cache-dit/commit/d0948740899c37925b8ba9aa4b879de884d3f475)

- **作者**: DefTruth
- **时间**: 2026-08-27T08:36:23Z
- **提交信息**: ffpa: materialize only non-contiguous inputs on the NHD path (#1105)

* ffpa: pass NHD inputs through to the fp8 persist-D tensor_layout fast path

_ffpa_attn_core now hands the native diffusers NHD [B, N, H, D] tensors
straight to ffpa_attn_func(tensor_layout="NHD") when the ffpa-attn fast
path applies (forward-only fp8 persist-D, no hybrid/hadamard/fp4/CP):
the kernel reads NHD and writes a contiguous NHD output, eliminating the
input permute views and the BHND-storage output whose non-contiguous
NHD view forced a strided copy in downstream consumers (diffusers
FluxAttnProcessor flatten(2,3), +0.233ms/attn at N=16896). Any
non-qualifying config (grad-on, causal hybrid, fp16/fp4 backends, CP
reassembly) keeps the legacy permute path.

FLUX e2e 1024x1024 (repeat 3, warmup 2): ffpa_fp8 16.47/16.51s vs sage
16.54/16.54s — flips from par to consistently ahead.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* ffpa: NHD direct output for the fp16/fp4 persist-D families

The ffpa_attn tensor_layout switch moved into the CUDABackend
constructor (tensor_layout="NHD"), and the persist-D CUDA kernels
now natively store an NHD (diffusers [B, N, H, D]) output for the
fp16 and fp4 families in addition to fp8. _ffpa_attn_core routes
the direct NHD pass through _is_nhd_supported with explicit
per-family branches (fp8 persist-D / fp4 persist-D 64<=D<=256 /
fp16 persist-D D<=128) so unsupported dims keep the graceful
permute fallback. Causal attention is allowed: the backend factory
always resolves *_hybrid to an explicit bool, so the ffpa auto
causal-hybrid never triggers; hybrid and hadamard configs still
fall back.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* ffpa: delegate the NHD gate to CUDABackend.is_nhd_supported

The per-family NHD rules now live in the ffpa-attn backend itself
(CUDABackend.is_nhd_supported: fp16 D<=128, fp4 D<=256, hybrid/hadamard
declines), so _is_nhd_supported reduces to grad/layout context plus that
single call instead of duplicating the family branches. causal stays
allowed: _build_ffpa_cuda_backend always resolves *_hybrid explicitly.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* ffpa: let the CP forward op keep the native NHD output

The context-parallel reassembly primitives (send_o and friends) reshape
and copy stride-agnostically, and the CP input shards arrive NHD packed
(send_q/k/v materialize them), so the forward op no longer forces
nhd_out=False. The NHD direct pass now matches the sage backend contract
under Ulysses/Ring/USP (verified bit-exact against the single-rank
reference for fp16 / fp8 / fp4 on 2 ranks), and the call passes
nhd_native/nhd_out as keywords so a later added parameter cannot
silently bind positionally.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* ffpa: forward is_causal through the NHD gate

_is_nhd_supported hardcoded is_causal=False into
CUDABackend.is_nhd_supported, relying on the backend factory always
resolving *_hybrid to an explicit bool. If a hybrid stays None (auto)
with causal attention, the cache-dit gate would pass the direct NHD
pass while the ffpa fast-path gate declines it, surfacing as a
TypeError instead of the graceful BHND permute fallback. Forward the
runtime flag so both gates resolve auto-hybrid identically.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* attn: update ffpa attn backend config

* ffpa: drop is_causal/seqlen_q from the NHD gate

Hybrid no longer blocks NHD (the persist-D hybrid stage-1 writeback is
a stride-generic slice copy), so CUDABackend.is_nhd_supported shrank to
(headdim) and the cache-dit gate forwards nothing extra.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

* attn: use ffpa-fp8 qk int8 by default

* chore: pre-commit format

* ffpa: materialize only non-contiguous inputs on the NHD path

Single-stream blocks (e.g. FLUX.2) slice a fused QKV projection, so V
arrives as an interleaved chunk view (stride(1) = 3 * inner_dim). The old
all-or-nothing contiguity gate then materialized Q, K and V into packed
BHND and returned a strided HND view that downstream flatten re-copied,
adding ~4 full-tensor copies per single-stream call (~0.65ms each at
N=12800, ~80ms over a 4-step FLUX.2-klein edit run).

Gate on NHD support first and materialize per tensor instead, so already
contiguous Q/K stay zero-copy and the output is packed NHD (flatten is a
view). Behavior is unchanged for all-contiguous and NHD-unsupported
inputs; only the non-contiguous + NHD-supported case moves from the full
BHND fallback to the NHD fast path.

Verified bit-exact against the previous BHND path and the contiguous
reference at the FLUX.2 single-stream shape (B1 N12800 H32 D128), and
with a new non-contiguous-V dispatch unit test. End-to-end on
flux2_klein_9b_edit 1024x1024 (paired median of 3): ffpa_fp8 6.51s ->
6.46s vs sage 6.44s, recovering ~70ms of the 90ms gap.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

---------

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90265
- **最后更新**: 2026-08-28T04:46:07Z

## 提交统计

- **昨日提交总数**: 34
- **提交者数量**: 29
- **主要提交者**: Elvir Crnčević, Khushali Desai, Bugen Zhao

## AI分析总结

# vLLM 仓库提交分析总结

## 一、主要更新类型

本批次共34个提交，涵盖**Bug修复**（约12个）、**性能优化**（约8个）、**功能新增**（约6个）、**架构重构**（约4个）、**基础设施/CI**（约3个）及**文档更新**（1个）。Bug修复和性能优化占据主导，体现了项目在稳定性和效率上的持续投入。

## 二、关键变更点与项目方向

1. **Model Runner V2 全面默认启用**（#53183）：将MRV2设为所有模型的默认执行路径，标志着新一代模型运行架构的成熟落地，是项目架构演进的重要里程碑。

2. **FlashInfer 深度集成**：包括BF16 CuTeDSL低延迟GEMM内核（#50572）、MLA解码原生上下文并行（#54012）及MNNVL allreduce缓冲区修复（#50932），持续强化FlashInfer作为核心注意力后端的地位。

3. **DeepSeek-V4/GLM-5 专项优化**：多个提交针对DSv4的SwiGLU clamp内核（+1.40%吞吐）、GLM-5掩码MHA支持及稀疏MLA Q拼接融合，体现对前沿模型架构的快速适配能力。

4. **Rust前端功能对齐**（#53218、#53756）：OpenAI请求/响应边界情况对齐及LoRA路径跨传输验证，巩固Rust前端作为统一API层的方向。

5. **KV缓存管理增强**：睡眠模式KV隔离（#53508）、KV卸载填充处理（#54021）及KV组外部传输识别（#53779），为大规模多租户场景奠定基础。

## 三、项目影响与潜在意义

- **稳定性提升**：修复了fork死锁、TCPStore端口冲突、流式logprob偏移等关键问题，直接提升生产环境的可靠性。
- **性能增益显著**：Kimi低延迟GEMM调优带来4%~97%提升，DSv4 MoE优化增加1.40%吞吐，对高负载推理场景价值重大。
- **架构现代化**：MRV2默认化与Rust前端成熟化，表明vLLM正从快速迭代期转向架构稳定期，为长期可维护性铺路。

## 四、值得关注的技术点

- **弹性专家并行**（#53378）保留AOT缓存复用，解决动态扩展时的性能回退问题。
- **稀疏NCCL权重更新**（#53751）用于RL场景，减少通信开销。
- **推理端reasoning-end检测**（#54089）通过turn-boundary token限定范围，提升多轮对话解析准确性。
- **Rubin Docker构建**（#53443）提前布局下一代NVIDIA硬件支持。

## 五、对项目发展的影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批次提交从三个维度推动项目前进：**性能**上通过内核级优化和FlashInfer集成持续压低推理延迟与成本；**易用性**上通过Rust前端对齐、错误信息清晰化（如多模态占位符超限提示）降低使用门槛；**可扩展性**上通过KV缓存管理、弹性EP和MRV2架构为大规模部署铺路。整体呈现“性能驱动、架构收敛、生态扩展”的发展态势，vLLM正从功能追赶转向精细化运营阶段。

## 详细提交记录

### [d04d3e0](https://github.com/vllm-project/vllm/commit/d04d3e0a076b7411b6e8ff4b36b4ffb23665179b)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-27T23:36:33Z
- **提交信息**: [Bugfix] Revert renderer warmup overlap to avoid fork deadlock (#54023)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>

### [3cc015a](https://github.com/vllm-project/vllm/commit/3cc015acd265d0e4e4c9d0a73bf7e5d5a5e66eef)

- **作者**: Connor Carpenter
- **时间**: 2026-08-27T23:00:12Z
- **提交信息**: [Rust Frontend][gRPC] Enforce LoRA path validation across transports (#53756)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [e5377e6](https://github.com/vllm-project/vllm/commit/e5377e6727454f50d15d8b6225f84b76a8dee5f6)

- **作者**: qizixi
- **时间**: 2026-08-27T22:58:28Z
- **提交信息**: [Bugfix][Model] Fix K3 DSpark config for 96-head drafts (#54005)

Signed-off-by: zixi-qi <zixi@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [7c87706](https://github.com/vllm-project/vllm/commit/7c877062acab618beb377ed6aae959faccc727c0)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-08-27T22:29:12Z
- **提交信息**: [kernel] Integrate FlashInfer BF16 CuTeDSL Low Latency GEMM (#50572)

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [f79a2f5](https://github.com/vllm-project/vllm/commit/f79a2f5582cb578d333eef73cf146929332f6414)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-08-27T22:12:01Z
- **提交信息**: Add support for loading dflash2 model in speculators format (#53797)

Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>

### [479eeb3](https://github.com/vllm-project/vllm/commit/479eeb32d2b432dbb4e442fbd3f94ca2eca35d67)

- **作者**: Ronald
- **时间**: 2026-08-27T22:08:28Z
- **提交信息**: [Bugfix][MRV2] Isolate sleep-mode KV allocations (#53508)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [d262964](https://github.com/vllm-project/vllm/commit/d262964e8c8316c3ec2304a4698b8277b39ea4b9)

- **作者**: Dennis Yeh
- **时间**: 2026-08-27T21:25:00Z
- **提交信息**: Upgrade tpu-inference to v0.28.0 (#54020)

Signed-off-by: dennis yeh <dennis.yeh@cienet.com>

### [de9250a](https://github.com/vllm-project/vllm/commit/de9250ac9e9b249133fff14e15d9248a1ebbcdb8)

- **作者**: Matthew Bonanni
- **时间**: 2026-08-27T21:17:12Z
- **提交信息**: [Attention] Enable masked MHA for GLM-5 head dimensions (#53785)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [3a9bfc2](https://github.com/vllm-project/vllm/commit/3a9bfc209f9443203d795149da40a7e5b94f27dc)

- **作者**: Mikhail Podvitskii
- **时间**: 2026-08-27T20:57:32Z
- **提交信息**: [Bugfix][Parser] Scope reasoning-end detection to the current turn via turn-boundary tokens (#54089)

Signed-off-by: Mikhail Podvitskii <podvitskiymichael@gmail.com>

### [7d5769b](https://github.com/vllm-project/vllm/commit/7d5769b2d9cf1e999e3f2fc2c1da265cf0d5d794)

- **作者**: Chauncey
- **时间**: 2026-08-27T20:52:45Z
- **提交信息**: [Perf][DSv4] Use native CUDA SwiGLU clamp kernel for Humming MoE (throughput +1.40%) (#53685)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [9818bb3](https://github.com/vllm-project/vllm/commit/9818bb3db8fd6fdb7742dfa7f8b5007f67a736fd)

- **作者**: Wentao Ye
- **时间**: 2026-08-27T20:48:53Z
- **提交信息**: [Kimi Perf] Tune hopper low latency gemm kernel, 4%~97% performance improvement (#54088)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [79378fe](https://github.com/vllm-project/vllm/commit/79378fe6e87687c63ceab9815c68bf027d491868)

- **作者**: Jeffrey Wang
- **时间**: 2026-08-27T19:58:14Z
- **提交信息**: [Bugfix] Avoid TCPStore port collision for co-located non-DP Ray engines (#53666)

Signed-off-by: Jeffrey Wang <jeffreywang@anyscale.com>

### [9db222c](https://github.com/vllm-project/vllm/commit/9db222c6bea2623e18ce09a8f270ac9cb7d86981)

- **作者**: Bugen Zhao
- **时间**: 2026-08-27T19:23:38Z
- **提交信息**: [Rust Frontend] Align OpenAI request and response edge cases (#53218)

Co-authored-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [4aab2b0](https://github.com/vllm-project/vllm/commit/4aab2b0ebed20343efe543c633f71b3c1336d5b8)

- **作者**: Nick Hill
- **时间**: 2026-08-27T18:59:34Z
- **提交信息**: [Model Runner V2] Use MRV2 for all models by default (#53183)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a18dbe4](https://github.com/vllm-project/vllm/commit/a18dbe49add8adcbf1d9f7b7429e2f249cfc625d)

- **作者**: Paarth Sharma
- **时间**: 2026-08-27T18:38:03Z
- **提交信息**: [Doc] Add EXAONE-4.0-1.2B to batch invariance tested models (#53839)

Signed-off-by: Cogniera <paarths376@gmail.com>
Signed-off-by: Paarth Sharma <paarths376@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [674c284](https://github.com/vllm-project/vllm/commit/674c284dbd2012f4b3e0da362aa11b75044c5d0c)

- **作者**: Elvir Crnčević
- **时间**: 2026-08-27T18:28:38Z
- **提交信息**: Fix Humming MoE activation_output aliasing (#54056)

### [d7b6a35](https://github.com/vllm-project/vllm/commit/d7b6a35967ba72ebece3dc8466b77d315cebdfec)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-27T18:18:16Z
- **提交信息**: [Bugfix] Handle malformed namespace tools (#53763)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [07242fa](https://github.com/vllm-project/vllm/commit/07242faa4667adcec25e40cb5f580cec60f2faac)

- **作者**: Summer Yang
- **时间**: 2026-08-27T17:32:45Z
- **提交信息**: [Attention][DCP] Use FlashInfer native CP for MLA decode (#54012)

Signed-off-by: Summer Yang <girasoleyang@gmail.com>

### [32ad140](https://github.com/vllm-project/vllm/commit/32ad1400d7fa08872430de3f1d0f981dc8db5cb6)

- **作者**: Shanshan Shen
- **时间**: 2026-08-27T16:37:54Z
- **提交信息**: [ROCm][Perf] Fuse SWA q/kv RMSNorm and q FP8 group quant for DeepSeek-V4 (#53540)

Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [9650dc7](https://github.com/vllm-project/vllm/commit/9650dc73e249688d9f4dac1f24a3f6f09e8c04a1)

- **作者**: Shang Wang
- **时间**: 2026-08-27T16:06:44Z
- **提交信息**: [CI/Build][Hardware][NVIDIA] Add opt-in Rubin Docker builds (#53443)

Signed-off-by: Shang Wang <samshang.wang@mail.utoronto.ca>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d21c5b5](https://github.com/vllm-project/vllm/commit/d21c5b50a1d3db5950ab905fcf78b713c81e15e1)

- **作者**: Chauncey
- **时间**: 2026-08-27T15:54:32Z
- **提交信息**: [Perf][GLM5.2] Fuse sparse MLA Q concatenation with head padding (#53878)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [76c0c65](https://github.com/vllm-project/vllm/commit/76c0c6530e832c758f5502ca4ef37ae88a7ffa13)

- **作者**: Nick Hill
- **时间**: 2026-08-27T15:30:22Z
- **提交信息**: [Bugfix][Scheduler] Don't pad spec decode up to `max_model_len` (#53962)

### [f18e298](https://github.com/vllm-project/vllm/commit/f18e29834b2114428aa5e261bfde09cb87965b4b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-27T15:26:10Z
- **提交信息**: [Bugfix] Preserve parallel HY-V3 calls delivered in one streaming delta (#53965)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [d85708f](https://github.com/vllm-project/vllm/commit/d85708f7a4362334eb58cff1fdf5265b49cac310)

- **作者**: Matthew Bonanni
- **时间**: 2026-08-27T15:21:24Z
- **提交信息**: [1/N][KV Connector] Identify externally transferable KV cache groups (#53779)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [c7b0467](https://github.com/vllm-project/vllm/commit/c7b0467c2524f85d619a8143bc7cb0d94f968396)

- **作者**: Khushali Desai
- **时间**: 2026-08-27T15:01:08Z
- **提交信息**: buffer size insuffient Dspark sd for FlashInfer MNNVL allreduce (#50932)

### [6d11122](https://github.com/vllm-project/vllm/commit/6d1112260739e26c18a9176376fe1dd4ad03f90d)

- **作者**: Itay Alroy
- **时间**: 2026-08-27T14:55:44Z
- **提交信息**: [Elastic EP] Preserve AOT cache reuse during scaling (#53378)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [75dea9b](https://github.com/vllm-project/vllm/commit/75dea9b4ae9e4e671ea1295f53ee9132c26ff19b)

- **作者**: Matthew Bonanni
- **时间**: 2026-08-27T13:37:29Z
- **提交信息**: [Bugfix] Update FlashMLA for sparse decode workspace fix (#53755)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [4a6a327](https://github.com/vllm-project/vllm/commit/4a6a3272e8d75518efe0a6f9393eb504f3ed2ee0)

- **作者**: Hert4
- **时间**: 2026-08-27T11:06:20Z
- **提交信息**: [Bugfix][Frontend] Let pooling requests set padding (#51157)

Signed-off-by: Hert4 <ductransa01@gmail.com>

### [42e7942](https://github.com/vllm-project/vllm/commit/42e7942ac94309ad749c0091b1275bb7d7b22aea)

- **作者**: hcl
- **时间**: 2026-08-27T10:56:07Z
- **提交信息**: fix(config): guard LlamaBidirectionalConfig against missing hf_config.pooling (#50536)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>

### [478ec3e](https://github.com/vllm-project/vllm/commit/478ec3ea41358d410a0997d8852ef5a344c9a677)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-27T10:52:59Z
- **提交信息**: [Bugfix][KV Offload] Handle padded GPU cache storage (#54021)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [6c4aa8b](https://github.com/vllm-project/vllm/commit/6c4aa8bec3029ec03d32194dc7aa0d1252253eaf)

- **作者**: Shuolei Wang
- **时间**: 2026-08-27T10:19:51Z
- **提交信息**: [RL] Support checkpoint-coordinate sparse NCCL weight updates (#53751)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [50708f9](https://github.com/vllm-project/vllm/commit/50708f95aec011d81aeae3258d6532972d2b5ad3)

- **作者**: Ting SUN
- **时间**: 2026-08-27T10:19:07Z
- **提交信息**: [Bugfix][OpenAI] Fix streamed completion logprob offsets with echo (#47815)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [acd0af9](https://github.com/vllm-project/vllm/commit/acd0af90e854cd8a04060f3bf37bc9331a771f42)

- **作者**: Hung Hoang (黄兴）
- **时间**: 2026-08-27T09:49:40Z
- **提交信息**: [Bugfix] Raise clear error on interleaved multimodal placeholder overcount (#53999)

Signed-off-by: hungh <hungh@nvidia.com>

### [fd57c4b](https://github.com/vllm-project/vllm/commit/fd57c4b7afebc0b43d25ed7f5848fc35786463d0)

- **作者**: Charlie Fu
- **时间**: 2026-08-27T08:06:48Z
- **提交信息**: [Rocm][CI] add dockerfile.xpu to rocm ci artifact (#53949)

Signed-off-by: charlifu <charlifu@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-28
**监控日期**: 2026-08-27
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6410
- **最后更新**: 2026-08-28T04:43:25Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: NATURE, Zhanshenzhui, Deep Shah

## AI分析总结

# vllm-omni 昨日提交分析

## 一、主要更新类型

本次提交共6条，涵盖**功能新增**（LTX-2.5 VAE解码器、Omni-DuplexEval基准、Qwen3-Omni thinker-only管线）、**Bug修复**（MiniCPM-o自动回复边界、异步块恢复）、**配置优化**（duplex准入探测限制）及**CI/构建改进**，整体以功能扩展和稳定性修复并重。

## 二、关键变更点与项目方向

1. **LTX-2.5 Diffusion VAE解码器支持**：扩展了项目在扩散模型（Diffusion）领域的模态覆盖能力，与vllm-omni“全模态模型服务”的定位高度契合，填补了视频生成类模型解码环节的空白。

2. **MiniCPM-o系列三项改动**（Bugfix、配置优化、基准支持）：MiniCPM-o作为多模态对话模型，其自动回复边界修正和duplex准入限制的配置化，直接提升了双工（duplex）交互场景的稳定性和可部署性；新增Omni-DuplexEval基准则强化了项目对全双工交互能力的评测体系。

3. **Qwen3-Omni thinker-only管线注册**：为Instruct服务模式单独注册推理管线，体现了对不同模型推理策略的精细化支持，使项目能适配更广泛的模型架构和推理范式。

## 三、对项目的影响与意义

- **生态扩展**：LTX-2.5和Qwen3-Omni的加入，使vllm-omni在视频生成和下一代Omni模型上保持前沿支持，增强了对主流开源模型的覆盖度。
- **稳定性提升**：两处Bugfix（自动回复边界、异步块恢复）直接改善了多模态对话和长会话场景下的可靠性，对生产环境部署至关重要。
- **可配置性增强**：duplex准入限制从硬编码改为部署配置驱动，降低了运维复杂度，提升了系统在不同硬件/负载下的适应性。

## 四、值得关注的技术点

- **异步块恢复的会话模式门控**：修复了非会话模式下异步块恢复可能引发的状态错乱问题，体现了对底层调度机制的细致打磨。
- **thinker-only管线**：Qwen3-Omni的“思考者”专用管线设计，暗示项目开始支持模型内部推理路径的分离，为未来更复杂的推理优化（如思维链加速）奠定基础。
- **基准测试体系完善**：Omni-DuplexEval的引入，表明项目不仅关注服务性能，也开始重视端到端交互质量的量化评估。

## 五、对项目发展的整体影响

结合README中“Easy, fast, and cheap omni-modality model serving”的愿景，这些提交从三个维度推动项目前进：**广度**上新增视频生成和最新Omni模型支持；**深度**上通过Bugfix和配置优化提升双工交互的工程成熟度；**前瞻性**上通过thinker-only管线和评测基准为下一代交互范式做准备。整体呈现“快速跟进前沿模型+夯实核心稳定性”的双轮驱动发展态势，有助于vllm-omni在竞争激烈的多模态服务框架中保持技术领先和生态吸引力。

## 详细提交记录

### [5e4daaf](https://github.com/vllm-project/vllm-omni/commit/5e4daaf1970ef230c50d6fb2c7ef8ed4895545f8)

- **作者**: Mu GuanLin
- **时间**: 2026-08-27T15:54:40Z
- **提交信息**: [Diffusion] Add LTX-2.5 Diffusion VAE decoder support (#6189)

Signed-off-by: mglyn <1203789601@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [262ff14](https://github.com/vllm-project/vllm-omni/commit/262ff146935553d444702b583874da461b50c079)

- **作者**: NATURE
- **时间**: 2026-08-27T11:51:47Z
- **提交信息**: [Bugfix][MiniCPM-o] Bound native auto-response continuation (#6630)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [069e6c5](https://github.com/vllm-project/vllm-omni/commit/069e6c5fbc829d56490529df3c169c300a46043d)

- **作者**: Deep Shah
- **时间**: 2026-08-27T11:20:01Z
- **提交信息**: [CI/Build][MiniCPM-o] Derive duplex admission-probe limit from the deploy config (#6678)

Signed-off-by: Deep Shah <deep@socratic.co>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [54c1fc6](https://github.com/vllm-project/vllm-omni/commit/54c1fc64b78ad6fe80c565ba9a8b8374d509224c)

- **作者**: NATURE
- **时间**: 2026-08-27T10:52:09Z
- **提交信息**: [Bugfix] Gate async-chunk segment resume by session mode (#6680)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [c6df39e](https://github.com/vllm-project/vllm-omni/commit/c6df39e9f7ad8a12fd61bc2c5007103c6a62076a)

- **作者**: Zhanshenzhui
- **时间**: 2026-08-27T08:31:50Z
- **提交信息**: [Benchmark][MiniCPM-o] Add Omni-DuplexEval support (#6634)

Signed-off-by: Zhanshenzhui <99891002+zyforsure@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [94b1546](https://github.com/vllm-project/vllm-omni/commit/94b1546ce3a04a0b0f7c0a685e1db2af05d5be7a)

- **作者**: Zheng Wengang
- **时间**: 2026-08-27T08:21:03Z
- **提交信息**: [Model] Qwen3-Omni: register thinker-only pipeline for Instruct serve (#6284)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Signed-off-by: Zheng Wengang <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
