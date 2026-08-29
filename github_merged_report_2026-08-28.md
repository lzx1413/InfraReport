# GitHub Stars 合并报告 - 2026-08-28

**合并日期**: 2026-08-29
**监控日期**: 2026-08-28
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


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2179
- **最后更新**: 2026-08-28T14:31:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2744
- **最后更新**: 2026-08-28T23:22:51Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Xin Qiu, Shiqiao Gu (谷石桥)

## AI分析总结

### 1. 主要更新类型
- **性能优化**（核心）：针对Intel XPU平台的CUTE注意力内核优化。
- **Bug修复**：修复H3模型ref2v的resize模式问题。
- **脚本更新**：更新项目脚本（可能涉及构建、测试或部署流程）。

### 2. 关键变更点与项目方向的关系
- **XPU优化**：LightX2V作为轻量视频生成推理框架，需支持多种硬件后端。本次针对Intel XPU的CUTE FMHA路径优化，直接提升MiniMax-H3长序列注意力性能，符合项目“轻量高效”定位。
- **Bug修复**：ref2v resize模式修复确保H3模型在特定场景下的正确性，维护模型兼容性。
- **脚本更新**：改善开发或使用流程，提升项目可维护性。

### 3. 对项目的影响和潜在意义
- **性能提升**：针对长序列（L>=18870）和特定形状（B=1, D=128, H∈{56,28,14,7}）的BF16输入，通过重叠V预取与QK GEMM、缓存首个Q tile、跳过不必要的softmax重缩放，显著降低计算和内存开销。
- **硬件适配**：增强Intel XPU上的推理能力，扩大项目硬件覆盖范围，吸引更多用户。
- **稳定性**：Bug修复减少H3模型使用中的错误，提升用户体验。

### 4. 值得关注的技术点
- **CUTE内核优化策略**：通过指令级流水线（V预取与QK GEMM重叠）和缓存复用（首个Q tile）减少内存访问延迟。
- **条件性softmax重缩放跳过**：利用行最大值不变性避免冗余计算，是注意力机制中常见的优化技巧，但需谨慎验证数值稳定性。
- **回退机制**：保留通用CUTE内核作为fallback，确保非优化场景下的正确性，体现工程稳健性。

### 5. 对项目发展的影响
- **强化竞争力**：在Intel XPU上提供更优性能，使LightX2V在视频生成推理领域更具吸引力，尤其针对长序列模型（如MiniMax-H3）。
- **生态扩展**：持续优化多硬件后端，符合开源项目吸引社区贡献和用户的方向，可能吸引更多XPU开发者参与。
- **技术积累**：CUTE内核优化经验可复用于其他模型或硬件，为未来架构演进（如支持更多注意力变体）奠定基础。

**总结**：本次提交以性能优化为核心，兼顾Bug修复和脚本维护，直接提升LightX2V在Intel XPU上的长序列推理效率，强化其“轻量高效”定位，并增强硬件兼容性和项目稳定性，对项目生态扩展和技术积累均有积极意义。

## 详细提交记录

### [7b8a96c](https://github.com/ModelTC/LightX2V/commit/7b8a96cc0a3a561824a5e6a8807ba7fae0984ea6)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-28T16:20:19Z
- **提交信息**: Update scripts (#1452)

### [5169278](https://github.com/ModelTC/LightX2V/commit/5169278f6bfb343f339b59ce8ebdb261a57a27e2)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-08-28T11:33:45Z
- **提交信息**: fix h3 ref2v resize mode (#1451)

### [cfcf923](https://github.com/ModelTC/LightX2V/commit/cfcf92321508343d6bfc523f178f3cc3e8073b23)

- **作者**: Xin Qiu
- **时间**: 2026-08-28T08:35:04Z
- **提交信息**: feat(xpu): Optimize CUTE attention for MiniMax H3 (#1450)

Optimize the Intel XPU CUTE FMHA path for MiniMax-H3 long-sequence
attention.

- Add an optimized FMHA variant for BF16 inputs with B=1, D=128,
L>=18870, and H∈{56,28,14,7}.
  - Overlap V prefetch with QK GEMM.
  - Cache the first Q tile.
- Skip unnecessary softmax rescaling when the row maximum is unchanged.
  - Keep the generic CUTE kernel as a fallback.

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2222
- **最后更新**: 2026-08-29T00:35:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6276
- **最后更新**: 2026-08-29T02:00:13Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: lunarz-dev, Jimmy Zhou, summer

## AI分析总结

# FlashInfer 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**Bug修复**（3项）、**功能新增**（2项）、**性能优化**（1项）、**重构**（1项）和**构建优化**（1项），类型分布均衡。

## 二、关键变更点与项目方向的关系

**Bug修复类**：
- 修复CUDA图捕获期间`trtllm_ragged_attention_deepseek`因`.item()` D2H同步导致的非法操作，将过宽的守卫改为跳过空行压缩路径，恢复全活跃批次在捕获场景下的正常行为
- 将RMSNorm FP4启动配置启发式限制在SM100/SM103，避免跨架构性能回退
- 修复共享cuDNN GEMM工作区在CUDA图捕获期间被移动的问题，通过`_gemm_workspace_at_least()`替代所有`resize_()`调用

**功能新增**：
- 为paged decode新增`prims-ts`后端及`is_causal`参数，打通非因果多token解码路径
- 新增recurrent KDA训练模板调度，支持前向/反向完整训练流程

**性能优化**：
- Blackwell块稀疏WS内核性能提升2.3-3.9倍

**重构与构建**：
- 隔离MLA的FA2/FA3/CUTLASS后端为独立实现
- 多架构cubins合并为单一构件，减少下载和验证开销

## 三、对项目的影响与潜在意义

这些提交显著增强了FlashInfer在**CUDA图兼容性**、**训练能力**和**多架构支持**方面的成熟度。CUDA图修复对生产环境推理至关重要，训练API的加入标志着项目从纯推理向训练/推理一体化演进，多架构构件合并则简化了部署流程。

## 四、值得关注的技术点

1. **CUDA图捕获安全**：多处修复围绕捕获期间禁止D2H同步和动态内存操作展开，体现对推理框架深度集成场景的重视
2. **后端抽象化**：MLA和decode的后端隔离为后续自动选择机制奠定基础
3. **架构感知优化**：启动配置按SM版本差异化，避免一刀切
4. **构建系统优化**：通过架构过滤kernel manifest，解决编译时间超线性增长问题

## 五、对项目发展的影响

结合README中"高性能GPU推理内核"的定位，这些提交强化了FlashInfer作为**生产级推理引擎**的可靠性（CUDA图支持），同时向**训练领域扩展**（KDA训练API），并保持对最新Blackwell架构的极致性能追求。整体方向是：在巩固推理优势的同时，拓展训练能力边界，完善多架构适配。

## 详细提交记录

### [e425c7b](https://github.com/flashinfer-ai/flashinfer/commit/e425c7b029ca90d5d01ff207913b070863d35a5b)

- **作者**: summer
- **时间**: 2026-08-28T23:51:28Z
- **提交信息**: [Bugfix] Skip .item() readback for trtllm_ragged_attention_deepseek during CUDA graph capture (#4609) (#4703)

## Summary

Fixes #4609.

`trtllm_ragged_attention_deepseek`'s empty-row compaction path (added in
`d898ed0`, #3779) reads `q_lens`/`kv_lens` off device tensors and calls
`.item()` to decide whether any row is empty. Since `.item()` is a D2H
sync and illegal inside `torch.cuda.graph()` capture, the same commit
added a Python-side guard that raises `ValueError` whenever
`is_current_stream_capturing()` is True and neither `q_seq_lens_cpu` nor
`kv_seq_lens_cpu` was supplied.

The guard is over-broad: it rejects **every** capturing caller,
including common all-active callers such as
`BatchPrefillWithRaggedKVCacheWrapper`, which never had empty rows to
compact in the first place. This is a regression against pre-`d898ed0`
behavior for the all-active case (the reporter bisected: fine at
`d69ab74`, broken at `d898ed0`, still broken at `4fa40ae`).

## Change

`flashinfer/prefill.py`: inside capture, if the caller did not pass CPU
seq-len mirrors, set `has_inactive_rows = False` / `has_active_rows =
True` and skip the compaction path, instead of raising. This restores
the pre-empty-row-compaction behavior — correct for all-active batches
and undefined for batches that actually contain empty rows. The
docstring for `q_seq_lens_cpu` is updated to state that captured batches
with possibly-empty rows must supply both CPU mirrors.

The `.item()` reads that trigger the D2H sync are now guarded behind
`else:` and only run outside capture.

The fix only removes a Python-side guard and moves two `.item()` calls
into the non-capture branch. **No numerical arithmetic changes.**

## Test Plan

- Regression test in `tests/attention/test_trtllm_ragged_kv_stride.py`:
replaced `test_trtllm_ragged_requires_cpu_lens_for_cuda_graph_capture`
(whose premise — that graph capture without CPU lens must raise — no
longer matches the new contract) with
`test_trtllm_ragged_all_active_cuda_graph_capture_without_cpu_lens`.
Uses `monkeypatch.setattr(torch.cuda, "is_current_stream_capturing",
lambda: True, raising=False)` and feeds an all-active batch
(`q_lens=[4,5,3,2,1]`, `kv_lens=[4,7,3,2,1]`, no zeros); asserts the
call returns a valid output tensor instead of raising.

## Test Result

Run on NVIDIA L20X (cc=(9,0)), CUDA 13.0, torch 2.9.1+cu130, in an
isolated venv with the buggy nightly
`flashinfer-python==0.6.18.dev20260819` (post-#3779) installed,
`FLASHINFER_DISABLE_VERSION_CHECK=1` to bypass cubin version pinning.

**Phase 1 — RED (unpatched nightly, `torch.cuda.graph()` capture,
all-active batch, no CPU seq lens)**

```
[env] flashinfer=0.6.18.dev20260819  torch=2.9.1+cu130  cuda=True  device=NVIDIA L20X
== Phase 1: capture with unpatched nightly (expect ValueError) ==
  kind=ValueError
  message: q_seq_lens_cpu and kv_seq_lens_cpu must be provided during CUDA graph capture
  PHASE 1 OK: reproduces #4609 raise before fix.
```

Reproduces the reporter's failure.

**Phase 2 — GREEN (same call, patched `prefill.py`)**

The Python-side `ValueError` from `prefill.py` no longer fires; capture
proceeds into the kernel dispatch path. Side-by-side control (same
input, same env, monkeypatched `is_current_stream_capturing()=True`,
only `prefill.py` differs between runs):

```
--- with ORIGINAL prefill.py ---
BUG PRESENT: ValueError -> q_seq_lens_cpu and kv_seq_lens_cpu must be provided during CUDA graph capture

--- with PATCHED prefill.py ---
OK — Python-side guard passed. Downstream failure (RuntimeError):
  Error in function 'TllmGenFmhaRunner' at .../fmhaRunner.cuh:37: Unsupported architecture
```

**Honest limitation: no numerical parity on this device.**

Neither backend of `trtllm_ragged_attention_deepseek` can execute on the
L20X available to me:

- `trtllm-gen` fmha runner reports `Unsupported architecture` at
`fmhaRunner.cuh:37` (requires the sm_90a Hopper variant; the L20X
reports cc=(9,0) but the runner rejects it).
- `cute-dsl` fmha requires one of `[sm_100a, sm_100f, sm_110a, sm_110f,
sm_103a, sm_103f]` (Blackwell-only).

Both arch limits exist **outside capture** as well — a plain non-capture
call fails identically. That means there is no working non-capture
reference on this device to diff a captured replay against, so I cannot
present capture-vs-non-capture parity numbers here. **Numerical parity
on B300/GB300 (the reporter's target hardware) still needs to be run.**

Since the change only removes a Python-side guard and does not touch any
arithmetic, capture-replay and non-capture calls invoke the same kernel
on the same inputs, so on hardware where the kernel does run, they
should produce identical outputs.

## Reference

- Root-cause commit: `d898ed0` (#3779, "Fix TRTLLM ragged prefill edge
cases", merged 2026-08-13).
- Reporter's bisect: fine at `d69ab74`, broken at `d898ed0`, still
broken at `4fa40ae`.
- Reporter's failing command uses `BatchPrefillWithRaggedKVCacheWrapper`
with `--backends fa2 fa3 cutlass cudnn trtllm-native` on a DeepSeek-R1
shape; the wrapper's `trtllm-gen` path routes to
`trtllm_ragged_attention_deepseek` and hits the guard when the caller
graph-captures without CPU seq-len mirrors.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- CUDA graph capture now requires CPU query and key-value
sequence-length mirrors, including for all-active batches.
- Outside CUDA graph capture, rows with zero query or key-value length
continue to be detected and compacted safely.
- Ragged attention capture now avoids device synchronization when using
mirrored sequence lengths.

- **Tests**
- Added coverage for missing-mirror errors and successful replay with
required mirrors and explicit maximum lengths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: summer <128961079+zhang-keliang@users.noreply.github.com>

### [2845d47](https://github.com/flashinfer-ai/flashinfer/commit/2845d474c89e2c4becae8902f8da875c93a7fdbd)

- **作者**: Lee Yong Jun
- **时间**: 2026-08-28T22:56:29Z
- **提交信息**: feat(decode): add prims-ts backend and is_causal to paged decode (#4739)

## 📌 Description

`BatchDecodeWithPagedKVCacheWrapper` derives the attention mask from
`q_len_per_req`, so a multi-token request is always causal:

```python
is_causal = q_len_per_req > 1
```

Non-causal multi-token decode is therefore not reachable from the public
API, even though the task-scheduled decode kernel in
`flashinfer.attention.prims_ts` takes `mask_type` as a plan argument and
supports `"dense"` for GQA, FP8 KV, and fixed `SQ > 1`. This PR connects
the two.

Two changes:

1. `backend="prims-ts"` on the paged decode wrapper, following the
`cute-dsl` backend structure: a delegate wrapper built in `__init__`, a
`plan()` branch, and a `run()` branch that returns before the
tensor-core argument assembly.
2. `is_causal: Optional[bool] = None` on `plan()`. `None` keeps the
existing derivation, so the other backends behave exactly as before. An
explicit value is honored only by `prims-ts`; the other backends raise,
because their mask mode is baked into the planned `qo_indptr` and JIT
key.

The `kv_len >= q_len_per_req` plan check now applies only under causal
masking. Dense attention places no such constraint, and the kernel
accepts `kv_len < q_len_per_req` in that mode.

The `prims-ts` kernel exposes a narrow surface, so unsupported wrapper
options are rejected rather than silently ignored:

| Option | Reason |
| --- | --- |
| `kv_layout="NHD"` | The kernel takes HND pages with compact inner
strides. |
| `use_cuda_graph=True` | The delegate re-allocates `seq_lens` and
scratch and re-specializes the kernel on every `plan()`, so a captured
`run()` does not follow a re-plan. Graph support needs a graph mode on
the prims-ts side and is left to a follow-up. |
| `jit_args` | No JIT customization hook. |
| `logits_soft_cap`, `pos_encoding_mode` | Not in the kernel contract. |
| `fixed_split_size`, `disable_split_kv` | Split-kv topology is chosen
internally. |
| `q_data_type != kv_data_type` | The kernel requires them equal. |
| `kv_cache_sf` | No block-scale path for NVFP4 KV. |
| `sinks` | Not in the kernel contract. |
| `return_lse` | LSE and split-kv partials are internal scratch. |
| `skip_softmax_threshold_scale_factor` | Not in the kernel contract. |

A sliding window under a dense mask is rejected by the kernel itself,
since `window_left >= 0` requires `mask_type="causal"`.

Automatic backend selection is untouched. `prims-ts` stays opt-in until
it is benchmarked against `trtllm-gen` on the causal path.

The `gqa_paged_decode` trace template is unaffected: it is scoped to one
query per sequence, where dense and causal masking coincide.

## 🔍 Related Issues

#3570, #3335

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

New file `tests/attention/test_prims_ts_decode_backend.py`. The
rejection tests run on any CUDA device because they fire before the
kernel is planned. The numerical tests are gated on SM100a, where the
kernel is qualified.

Numerical coverage: dense and causal against a paged reference at
`q_len_per_req` 1 and 4, dense output differing from causal on the same
inputs, dense with `kv_len < q_len_per_req`, and graph capture of a
fixed plan. The graph test only covers capture and replay of one plan;
the wrapper-level `use_cuda_graph=True` flow (re-plan then replay) is
rejected for this backend, see above.

Run on B200 (SM100a) with `nvidia-cutlass-dsl` 4.7.0:

```
tests/attention/test_prims_ts_decode_backend.py    24 passed
tests/attention/test_batch_decode_kernels.py       16 passed   (-k uniform_multi_token)
tests/attention/test_workspace_size.py              6 passed
```

## Reviewer Notes

`is_causal` is the spelling at the wrapper boundary because it replaces
the variable of that name; the branch translates it to the kernel's
`mask_type`.

NVFP4 KV under a dense mask is deliberately out of scope. It needs a
block-scale data path inside the kernel rather than wrapper plumbing, so
it belongs in a separate PR.

cc:@PerkzZheng

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added tracing support for paged key-value cache decode planning,
capturing configuration and request metadata for improved analysis.
* Expanded paged decode coverage across causal, dense, sliding-window,
and split-KV scenarios.

* **Bug Fixes**
* Added clearer validation for unsupported backend and runtime-option
combinations.
* Prevented incompatible CUDA Graph planning configurations from being
accepted.
* Improved validation for sequence metadata, grouped-query attention
dimensions, tensor contiguity, and sliding-window settings.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [adc49a8](https://github.com/flashinfer-ai/flashinfer/commit/adc49a85302ef16259aad0cf7c323049a5072851)

- **作者**: eigen
- **时间**: 2026-08-28T22:24:30Z
- **提交信息**: perf(cake_vsa): refresh Blackwell block-sparse WS kernel (#4804)

| Sequence | Density | Route | #4804 synchronized E2E ms | [Fixed #4612
CuTe
DSL](https://github.com/flashinfer-ai/flashinfer/blob/91acdfe40fbc57d0ab71b5a9a723339f28e8389c/flashinfer/cute_dsl/sparse/bsa_attn_sm100_blk64.py)
synchronized E2E ms | #4612 / #4804 |
|---:|---:|---|---:|---:|---:|
| 1024 | 0.25 | M64N128 | 0.064496 | 0.2526 | 3.9165x |
| 1024 | 0.50 | M64N128 | 0.064176 | 0.2490 | 3.8800x |
| 1024 | 0.75 | M64N128 | 0.065008 | 0.2543 | 3.9118x |
| 2048 | 0.25 | M64N128 | 0.066817 | 0.2519 | 3.7700x |
| 2048 | 0.50 | M64N128 | 0.071920 | 0.2455 | 3.4135x |
| 2048 | 0.75 | M64N128 | 0.077008 | 0.2568 | 3.3347x |
| 4096 | 0.25 | M64N128 | 0.084288 | 0.2498 | 2.9636x |
| 4096 | 0.50 | M64N256 WS | 0.100944 | 0.2519 | 2.4954x |
| 4096 | 0.75 | M64N256 WS | 0.112848 | 0.2574 | 2.2809x |
| Geometric mean | — | — | — | — | 3.2724x |

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [2af72b0](https://github.com/flashinfer-ai/flashinfer/commit/2af72b0b8a5c1d159554e111da7dae51b3dc35c7)

- **作者**: Qidong Su
- **时间**: 2026-08-28T19:33:45Z
- **提交信息**: fix(norm): limit add RMSNorm FP4 launch config heuristics to SM100 and SM103 (#4494)

<!-- .github/pull_request_template.md -->

## Summary

This PR limits the launch-config changes introduced in #4416 to SM100
and SM103.

- SM100/SM103 use the new M-aware launch configuration.
- Other architectures retain the pre-#4416 dispatch heuristic.
- The compiled-kernel cache is keyed by the selected launch config
instead of M, avoiding a separate compilation for every batch size.

## Motivation

The launch configuration introduced in #4416 performs well on GB200 and
GB300, but is not consistently beneficial across architectures.
Restricting it to SM100/SM103 preserves the measured gains while
retaining the previous behavior elsewhere.
## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

## Performance

GB300, BF16 input, two independent runs per case, 5 warmups and 30
iterations. Times are in milliseconds.

| dtype | batch_size | hidden_size | speedup | median_time_pre |
median_time_cur |
| --- | ---: | ---: | ---: | ---: | ---: |
| mxfp4 | 16384 | 4096 | 1.037 | 0.0824 | 0.0795 |
| nvfp4 | 16384 | 4096 | 1.060 | 0.0764 | 0.0721 |
| mxfp4 | 2048 | 4096 | 1.099 | 0.0157 | 0.0143 |
| nvfp4 | 2048 | 4096 | 1.102 | 0.0144 | 0.0131 |
| mxfp4 | 16384 | 8192 | 1.062 | 0.1625 | 0.1530 |
| nvfp4 | 16384 | 8192 | 1.068 | 0.1503 | 0.1407 |
| mxfp4 | 2048 | 8192 | 1.101 | 0.0261 | 0.0238 |
| nvfp4 | 2048 | 8192 | 1.112 | 0.0241 | 0.0217 |

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

* **Performance**
* Improved RMS normalization and FP4 quantization performance across
supported GPU architectures.
* Added workload-aware tuning based on tensor dimensions, batch size,
data type, GPU architecture, and available memory.
  * Improved execution consistency by reusing optimized launch settings.
  * Added architecture-specific tuning for supported GPU variants.
  * Reduced overhead from repeated launch configuration calculations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [e54b6f1](https://github.com/flashinfer-ai/flashinfer/commit/e54b6f1c8f8347f5b1e6dd52a8dd864ca7188003)

- **作者**: eigen
- **时间**: 2026-08-28T18:23:41Z
- **提交信息**: feat(cake_kda): add recurrent training template dispatch (#4726)

## Summary

- add complete paired recurrent KDA training APIs with
  `recurrent_kda_training_forward` and `recurrent_kda_training_backward`
- save the forward checkpoints and tape in one explicit route context so
  backward consumes forward state without recomputing the recurrence
- dispatch equal-head and grouped-QK production shapes through one C16
  forward/context/backward path, with analytical fallback routes for the
  remaining shapes
- keep packed planning on a trusted CPU offsets mirror, without reading
or
  iterating over CUDA offsets on the host
- support arbitrary positive sequence lengths by masking partial C16
chunks
  and guarding the final partial output store
- include frozen `sm_100a` and `sm_103a` CUDA sources for the
production,
  fallback, and grouped-row paths

## API contract

The kernel family requires BF16 token inputs, FP32 parameters and
recurrent
states, `K=V=128`, positive sequence lengths, and `Hv % Hqk == 0`. Fixed
layout
supports `B >= 1`. Packed layout uses physical batch one with semantic
sequences
described by CUDA `cu_seqlens` plus a trusted CPU int64 mirror supplied
as
`cu_seqlens_cpu` for launch planning.

Both equal-head and grouped-QK C16 problems retain exactly one selected
forward
context. Backward consumes that saved context and launches no forward
work.

## Validation

- [x] static/API selector and no-host-sync checks
- [x] `sm_100a` and `sm_103a` JIT compile/load and standalone CUDA
builds
- [x] B200/B300 memcheck and synccheck for ordinary and split partial
tails,
  with zero reported errors
- [x] four-platform 35-shape benchmark audit, including strict result
manifests,
  route contracts, timing-method locks, and direct correctness records

The benchmark corpus contains 21 primary shapes plus 14 supplemental
dispatcher-coverage rows. Speedup is Frost paired-DAG latency divided by
FlashInfer paired-DAG latency, so values above 1x mean FlashInfer is
faster.

The Frost reference is available in
[cuDNN
Frontend](https://github.com/NVIDIA/cudnn-frontend/tree/develop/python/cudnn/linear_attention/frost).

| GPU | Primary FI / Frost geomean (ms) | Primary speedup | Supplemental
speedup | All-35 speedup | Queue / allocation / harness runtime (s) |
|---|---:|---:|---:|---:|---:|
| B200 | 1.968157 / 2.206141 | 1.1209x | 1.3575x | 1.2102x | 15 / 1663 /
1452.7 |
| GB200 | 1.901246 / 2.030794 | 1.0681x | 1.1624x | 1.1049x | 3 / 1941 /
1607.4 |
| B300 | 1.837120 / 2.188012 | 1.1910x | 1.2990x | 1.2331x | 1 / 1601 /
1381.1 |
| GB300 | 1.914404 / 2.137932 | 1.1168x | 1.2148x | 1.1550x | 151 / 1935
/ 1662.5 |
| **All GPUs** | — | **1.1234x (84 rows)** | **1.2562x (56 rows)** |
**1.1747x (140 rows)** | — |

Strict `atol=rtol=1e-2` correctness is recorded before timing. The
sealed four-platform reports are not necessarily all-pass numerical
results; no tolerance was changed:

- B200 has 5 failing row(s): `04` (FlashInfer `output` 1 mismatch(s));
`fixed_b8_t2048_h96` (FlashInfer `final_state` 1 mismatch(s));
`fixed_b8_t8192_h96` (FlashInfer `output` 2 mismatch(s));
`fixed_b8_t16384_h96` (FlashInfer `output` 3 mismatch(s));
`fixed_b4_t2048_h96` (FlashInfer `dq` 1 mismatch(s)).
- GB200 has 5 failing row(s): `01` (FlashInfer `output` 1 mismatch(s));
`14` (FlashInfer `output` 1 mismatch(s)); `fixed_b8_t4096_h96`
(FlashInfer `output` 1 mismatch(s); FlashInfer `final_state` 1
mismatch(s)); `fixed_b8_t8192_h96` (FlashInfer `output` 4 mismatch(s));
`fixed_b8_t16384_h96` (FlashInfer `output` 3 mismatch(s)).
- B300 has 5 failing row(s): `04` (FlashInfer `output` 1 mismatch(s));
`fixed_b8_t2048_h96` (FlashInfer `final_state` 1 mismatch(s));
`fixed_b8_t8192_h96` (FlashInfer `output` 2 mismatch(s));
`fixed_b8_t16384_h96` (FlashInfer `output` 3 mismatch(s));
`fixed_b4_t2048_h96` (FlashInfer `dq` 1 mismatch(s)).
- GB300 has 5 failing row(s): `01` (FlashInfer `output` 1 mismatch(s));
`14` (FlashInfer `output` 1 mismatch(s)); `fixed_b8_t4096_h96`
(FlashInfer `output` 1 mismatch(s); FlashInfer `final_state` 1
mismatch(s)); `fixed_b8_t8192_h96` (FlashInfer `output` 4 mismatch(s));
`fixed_b8_t16384_h96` (FlashInfer `output` 3 mismatch(s)).

All other directly gated output, final-state, and token/state-gradient
values pass. Non-C16 routes require strict checks for both parameter
gradients; production C16 rows require their combined `dA_log` plus
`ddt_bias` mismatch count to be no worse than Frost on the same shape.
Direct parameter-gradient diagnostics remain recorded.

## Benchmark method and caveats

- CUPTI activity timing with cold L2, no CUDA Graph, and no CUDA-event
  fallback; 25 ms warmup and 100 ms sampling per row
- directly measured forward+backward public-API GPU DAG, not a sum of
component
  medians
- FlashInfer reuses preallocated public output, final-state, context,
and
  gradient buffers; Frost uses its native public autograd allocations
- fixed FlashInfer inputs remain physical `[B,T,H,D]`; packed inputs use
physical batch one and explicit offsets; Frost receives an
outside-timing
  THD view and equivalent int32 offsets
- Frost requires FP32 raw gate logits, so identical BF16 FlashInfer
values are
  cast outside timing
- Frost uses its native `B_T=16` checkpoint cadence; backward consumes
the
  forward checkpoints and does not recompute

The strict result-manifest SHA-256 values are:

- B200:
`0542a70d889a520672386f1f78991937dc7bd6c740fc0e32715f58bbb3a4e9db`
- GB200:
`6b1ab42f3e57b9248fbb4e44aa3e735de1ffb621ae1e8764e4d56b56ce1b9629`
- B300:
`cb811db8377ff08f16f59ecbb486bdd7e41564f50564c9ce7008f8f7b21b6307`
- GB300:
`805ca88f11b09795d8afa0854315248f66a653cfcd8dc51770e90b00b8c0e3c2`

The measured public snapshot is
`5b48970ed1f3d844c8aa0c41b0b058d6d56ef4e1` (tree
`c71cf055d58fc45ddc868fcafcc8ac648bd68872`). Frost is pinned to public
commit
`ae8705effeea3804585b6aca554beaca1a76a3da` (tree
`bc5925cd9605a01a69dc639675a710cbc5e91873`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added automatic cost-based selection among optimized recurrent KDA
training paths.
  * Added grouped row-split support for compatible Blackwell workloads.
  * Added fixed-length and packed benchmark layouts.
* Added paired forward/backward performance measurement and CPU
packed-sequence metadata support.

* **Bug Fixes**
  * Improved partial-tail, final-state, boundary, and gradient handling.

* **Documentation**
* Clarified context reuse, output buffers, packed metadata, precision
limits, route selection, and benchmarking.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Zihao Ye <zihaoy@nvidia.com>

### [ec45ed3](https://github.com/flashinfer-ai/flashinfer/commit/ec45ed3072bc3340e84d87c04580d2d228aeb24a)

- **作者**: Yanqin Zhai
- **时间**: 2026-08-28T18:14:30Z
- **提交信息**: fix(gemm): never move the shared cuDNN GEMM workspace (#4666)

<!-- .github/pull_request_template.md -->

## 📌 Description

- `DEFAULT_WORKSPACE_SIZE`: 32 MiB → 40 MiB, above cuDNN's
shape-independent
  request (33,554,692 B worst case) so no growth is needed.
- New `_gemm_workspace_at_least()` replaces all 10 `resize_()` sites. If
the
shared buffer is ever too small it returns a call-local buffer and
leaves the
shared one alone — the same thing the CUTLASS runners in `csrc/` already
do —
  and raises during CUDA graph capture, where neither option is safe.
- `_get_cache_buf()` retires a displaced buffer instead of dropping it,
so a
  stale captured pointer can no longer alias a live tensor.
- Refuse to build a cuDNN execution plan during graph capture
(`CudnnPlanBuildInCaptureError`). Plan build is where cuDNN loads kernel
modules, may invoke NVRTC, and makes the process's first
`cublasLtCreate()` —
which cuDNN documents as unsafe under capture, and which our
`lru_cache`'d,
shape-keyed graph builders made reachable. Warm the shape up outside the
  capture instead.

There are no `resize_()` calls left on shared workspaces.

## 🔍 Related Issues

[<!-- Link any related issues here
-->](https://github.com/flashinfer-ai/flashinfer/issues/4549)

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

* **Bug Fixes**
  * Improved CUDA graph capture reliability for cuDNN GEMM operations.
* Prevented workspace resizing from invalidating buffers still
referenced by captured graphs.
* Added safer workspace handling for standard, grouped, FP8, BF16,
MXFP8, and FP4 GEMM workloads.
* Increased the default GEMM workspace allocation from 32 MiB to 40 MiB.
* Added clearer safeguards when cuDNN plans must be built during graph
capture.
* **Documentation**
* Documented the option to allow cuDNN plan creation during CUDA graph
capture with a warning.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e54feea](https://github.com/flashinfer-ai/flashinfer/commit/e54feea05ba1d42948654cff92e21d0dd18c5b85)

- **作者**: lunarz-dev
- **时间**: 2026-08-28T17:05:43Z
- **提交信息**: Enable CuTe DSL MLA benchmarks for low head counts (#4656)

## 📌 Description

Remove the benchmark-side restriction that excludes the `cute-dsl`
backend when `num_qo_heads` is less than 128.

This enables `BatchMLAPagedAttentionWrapper` to benchmark `cute-dsl` for
tensor-parallel MLA decode configurations with low per-rank query-head
counts, including long-context `s_qo=8` workloads.

Objective: Enable CuTe DSL benchmark coverage for low query-head counts.

This PR is limited to the benchmark harness. It does not modify
production backend implementations or add `fold_sq` to the `trtllm-gen`
kernel.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Pre-commit result: **PASS** (`pre-commit run --all-files`).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All applicable tests are passing.

Test results:
- `pre-commit run --all-files`: PASS
- `BatchMLAPagedAttentionWrapper` with `cute-dsl`, low per-rank
query-head count, and `s_qo=8`: PASS

## Reviewer Notes

Co-authored-by: RCCA Agent <rcca-agent@localhost>

### [8b118e7](https://github.com/flashinfer-ai/flashinfer/commit/8b118e7539668b773f2e0c266892d22dc0d02087)

- **作者**: Mingyang Wang
- **时间**: 2026-08-28T16:55:25Z
- **提交信息**: refactor(mla): isolate planned FA2, FA3, and CUTLASS backends (#4697)

## 📌 Description

This is the first standalone section extracted from [the original Batch
MLA redesign PR](https://github.com/flashinfer-ai/flashinfer/pull/4031).
That PR covered several independent backend and API changes; this series
breaks the work into smaller PRs that can be reviewed, validated, and
landed individually.

### Current scope

This PR establishes the planned Batch MLA foundation for the existing
FA2, FA3, and CUTLASS backends:

- moves concrete planning and execution state into backend-owned
implementations;
- introduces canonical plan metadata and explicit packed/split query and
KV-cache layout contracts;
- keeps the planned `run()` path backend-native, with no runtime backend
discovery or replanning, and reuses plan-owned workspaces and empty-LSE
storage;
- makes CUDA Graph replanning transactional while preserving the wrapper
attributes used by SGLang's fast replay path;
- preserves legacy public imports, positional/flat-CSR planning, split
tensor calls, dynamic LSE behavior, and caller-owned output/LSE
identity;
- retains deprecated planless CUTLASS execution as a validated per-call
path without publishing or mutating planned state;
- preserves historical trace identities while allowing trace replay to
recognize the reorganized implementation; and
- documents the backend ownership and lifecycle conventions introduced
by this slice.

The structural input resolver also preserves the existing zero-width PE
compatibility case: a packed plan can still accept `(left, empty_right)`
without requiring a copy.

### Incoming follow-up sections

Subsequent PRs are expected to cover, independently:

1. a public sync-free CUDA Graph plan-update API and removal of the
temporary private SGLang bridge;
2. TRTLLM-GEN, XQA, and CuTe DSL backend verticals;
3. deterministic automatic selection with typed unsupported-backend
fallback;
4. the unified tensor-first functional API; and
5. optional autotuning and benchmark follow-ups.

## 🔍 Related Issues

- Original umbrella PR:
https://github.com/flashinfer-ai/flashinfer/pull/4031
- Related issue: https://github.com/flashinfer-ai/flashinfer/issues/4037

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

The complete repository-wide pre-commit suite passes.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validation completed:

- planned-wrapper compatibility suite: 71 passed;
- focused planned CUTLASS/FP8 suite: 10 passed;
- trace and trace-apply suite: 26 passed;
- repository-wide pre-commit suite and `git diff --check` passed;
- targeted SM90 and SM100 real-GPU checks passed for FA2/FA3/CUTLASS
numerical execution, CUDA Graph replay and replanning, legacy
flat-CSR/separate-tensor/dynamic-LSE calls, FP8 CUTLASS execution, and
zero-width PE packed-plan compatibility; and
- targeted SGLang SM100 integration passed fast decode/prefill planning,
wrapper mirror identity, canonical/legacy numerical parity, focused MLA
tests, and unified dense block-table tests.

Full repository tests, wheel/build validation, and the repository-wide
GPU CI matrix have not been run locally.

## Reviewer Notes

The first two commits intentionally preserve the review boundary between
the planned-contract foundation and the subsequent
compatibility/hot-path corrections. The final one-file commit only gives
the cached FA planning helper its concrete JIT-generator signature so
repository-wide mypy can validate it; cache keys and runtime behavior
are unchanged.

Suggested review focus:

- backend ownership and the plan/publication transaction boundary;
- planned `run()` hot-path work and workspace/LSE reuse;
- packed/split structural input compatibility, including zero-width PE;
- CUDA Graph replan behavior and SGLang mirror attributes;
- deprecated planless CUTLASS isolation; and
- legacy imports, call forms, output identity, and trace compatibility.

This branch is intentionally based on the validated extraction point
from #4031 rather than rebased after validation; current-main CI should
be treated as the integration check for intervening changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a planned Batch MLA paged-attention API supporting CSR, dense,
and combined metadata.
* Added packed and split query/KV inputs, FP8 output scaling, CUDA Graph
support, and automatic FA2, FA3, or CUTLASS backend selection.
  * Added planless CUTLASS execution for supported configurations.

* **Compatibility**
  * Preserved legacy calling patterns with deprecation warnings.

* **Documentation**
* Added comprehensive Batch MLA architecture, API, and backend
documentation.

* **Bug Fixes**
* Improved MLA tracing and validation for metadata, layouts, data types,
scaling, and backend capabilities.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [93f4f26](https://github.com/flashinfer-ai/flashinfer/commit/93f4f2642e1b3680a52ebb51cf68e0fdad237796)

- **作者**: Jimmy Zhou
- **时间**: 2026-08-28T09:53:19Z
- **提交信息**: misc: multi-arch cubins (sm100, 103, 107) in a single artifact (#4648)

<!-- .github/pull_request_template.md -->

## 📌 Description

This change collapses TRTLLM_GEN_BMM_RUBIN, TRTLLM_GEN_GEMM_RUBIN, and
DEEPGEMM_RUBIN back into their base constants and bumps all pins to the
consolidated packs, along with KERNEL_MAP_HASH_RUBIN and the
is_rubin_arch() artifact-path branch in deep_gemm.py. The enable_rubin
plumbing survives untouched — it still selects the module name, the
-DTLLM_RUBIN_FEATURES compile flag, and a per-module export-header root;
only the artifact path and checksum it used to select are now identical
for both variants. Halving the pinned pack count also halves what
download_artifacts() fetches and verifies, since the Blackwell and Rubin
packs no longer duplicate their shared sm100f kernels.


### Follow-up: arch-filtered kernel manifest (fixes the MoE compile-time
regression)

Consolidating the packs doubled the BMM `flashinferMetaInfo.h` from 3476
to 6862 entries. That header declares one `BatchedGemmConfig`
initializer per cubin, and `BatchedGemmConfig` embeds
`BatchedGemmOptions`, which has non-trivial members (`std::string`,
`std::vector<int>`) — so the array cannot be constant-folded into
`.rodata` and the host compiler emits a dynamic initializer for every
entry, at superlinear cost. Exactly one TU includes it
(`csrc/trtllm_batched_gemm_runner.cu`), and it became 99.96% of the
critical path of the fused-MoE JIT build.

The runtime never dispatches across architecture families
(`isArchCompatible()` accepts `Sm100a/Sm100f/Sm103a` only on
sm100/sm103, `Sm107a` only on sm107), so the other family's entries are
dead weight in any given module. This adds
`flashinfer/jit/trtllm_gen_metainfo.py`, which strips entries by their
`}, gemm::SmVersion::SmXXX},` terminator and rewrites the declared
`...ListLen` (raising rather than silently truncating if the manifest
shape changes). `gen_trtllm_gen_fused_moe_sm100_module` writes the
filtered copy into its per-module `gen_root` and drops the raw artifact
`include/` dir from the include path, so exactly one manifest is
reachable. The filter keys on the **module variant** (`enable_rubin`),
not the GPU present at build time — AOT builds both variants on one
machine. Blackwell now compiles 3476 entries, exactly the
pre-consolidation count; Rubin compiles 3386. Nothing changes on the
publishing side and no cubin is dropped: the variants partition the
manifest exactly (3476 + 3386 = 6862, disjoint arch sets).

Measured on B200 (CUDA 13.0), cold JIT build of
`fused_moe_trtllm_sm100`:

| | before | after | speedup |
|---|---|---|---|
| manifest entries | 6862 (29.2 MB) | 3476 (14.8 MB) | 1.97x smaller |
| `trtllm_batched_gemm_runner.cu` | 1175.2 s | 205.1 s | **5.7x** |
| whole module build | 1175.7 s | 226.4 s | **5.2x** |

## 🔍 Related Issues

Fixes the trtllm-gen MoE compile-time regression reported for the
consolidated packs. Also addresses #4569.

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
- [x] All tests are passing.

Validated on B200 (`umb-b200-261`, CUDA 13.0), against the pin this PR
ships (`8ec29a98 / 31ee4e5`) unless noted — **689 passed, 0 failed**:

| suite | result |
|---|---|
| `tests/jit/test_trtllm_gen_metainfo.py` | 11 passed (new; pure
text-transform, no GPU/network) |
| `tests/moe/test_trtllm_gen_moe_autotune_tactics.py` | 82 passed
(20:23) |
| `tests/moe/test_trtllm_gen_per_token_moe.py` +
`test_trtllm_gen_routed_fused_moe.py` | 380 passed (5:19) |
|
`tests/moe/test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp8,fp4}.py`
| 134 passed, 1018 skipped (41:51) |

The autotune-tactics suite is the meaningful gate for the `configIndex`
concern: its `*_all_tactics_are_correct` / `*_all_tactics_correctness`
cases enumerate every valid config index and check numerics per tactic.
It also passed 82/82 on the previous pin. The 1018 skips in the
renormalize suites are that file's own combinatorial gates in
`tests/moe/utils.py:skip_checks` (invalid activation x quant x routing x
shape combinations), decided in Python before kernel selection and
unaffected by the filter — a filter that dropped a needed kernel would
surface as a failure ("No kernel found"), not a skip.

Not covered: `tests/moe/test_trtllm_gen_fused_moe.py` (4141 cases) did
not fit the node lease; leaving it to CI.

## Reviewer Notes

- `main` is affected independently of this PR: its `TRTLLM_GEN_BMM` pin
is already multi-arch (6846 entries), and its `TRTLLM_GEN_BMM_RUBIN`
pack is multi-arch too (2552/90/2552) — so splitting the pins back would
not fix it. The filter is library-side and works regardless of what the
packs contain.
- Filtering renumbers `configIndex` into the manifest. In-process this
is consistent (`getValidConfigIndices` -> autotuner ->
`checkPassingConfigIndex`), and `prioritizePredefinedConfigs` matches by
kernel name, not index. A *persisted* tactic recorded against an
unfiltered build (a `FLASHINFER_TACTICS_BLOCKLIST` JSON, or a saved
autotune result) would be stale — the same hazard as any pin bump. No
blocklist JSONs are checked in.
- trtllm-gen FMHA uses a different compat rule (`isSMCompatible()` in
`fmhaKernels.cuh` *does* accept `kSM_100f` on sm107) and its manifest is
flat POD that constant-folds — measured at 0.98 s for all 35396 entries.
It does not need this treatment. The GEMM manifest is 186 entries, also
negligible.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Improvements

- Consolidated architecture-specific acceleration packages into unified
multi-architecture packages.
- Updated optimized GEMM, MoE, and DeepGEMM components to use the latest
verified artifacts and checksums.
- Simplified artifact selection across supported GPU architectures while
preserving architecture-specific compilation behavior.
- Added architecture-aware kernel manifest handling for more reliable
builds.
- Strengthened package integrity validation for similarly named files in
different locations.

## Documentation

- Clarified compatibility notes for specialized FP4 and fused MoE
kernels.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Lee Nau <lnau@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4114
- **最后更新**: 2026-08-29T02:29:21Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Aryan Kumar, William Lin

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批次提交以**功能新增**为主，辅以**版本发布**和**依赖管理**调整。具体包括：新增MiniMax H3模型的MLX推理支持、多模态OpenAI服务API对齐、v0.2.1版本发布以及fastvideo-kernel依赖版本固定。

### 2. 关键变更点及与项目方向的关系
- **MiniMax H3 MLX T2VA推理支持**：为FastVideo引入新的视频生成模型支持，扩展了模型生态。MLX是Apple的机器学习框架，表明项目正在向Apple Silicon平台延伸，与README中强调的"快速视频生成"目标一致，同时扩大了硬件兼容性。
- **多模态OpenAI服务API对齐**：将推理服务接口与OpenAI的多模态API标准对齐，这是提升互操作性的关键步骤。FastVideo作为视频生成工具，对齐行业标准API有助于降低用户接入门槛，促进生态集成。
- **v0.2.1版本发布**：标志着项目进入稳定迭代周期，为社区提供明确的版本基准。
- **fastvideo-kernel版本固定**：将核心内核依赖精确锁定到0.3.5，确保构建可复现性，减少因依赖漂移导致的兼容性问题。

### 3. 对项目的影响和潜在意义
- **生态扩展**：MiniMax H3支持使FastVideo能够服务更广泛的用户群体，特别是使用Apple硬件的开发者，潜在扩大社区影响力。
- **标准化提升**：API对齐增强了项目作为视频生成基础设施的可用性，便于与现有AI工具链集成，符合README中"快速上手"的定位。
- **工程稳定性**：版本发布和依赖固定提升了项目的可维护性和可靠性，为后续开发奠定坚实基础。

### 4. 值得关注的技术点
- **MLX框架集成**：表明FastVideo正在探索Apple Silicon上的高性能推理路径，这可能涉及针对Metal GPU的优化，值得关注其性能表现。
- **多模态API设计**：对齐OpenAI标准意味着FastVideo可能支持图像+文本+视频的混合输入，这是视频生成领域的前沿方向。
- **版本管理策略**：精确固定内核版本显示项目对依赖管理的严谨态度，有助于长期维护。

### 5. 对项目发展的影响
结合README中FastVideo定位为"快速视频生成"工具，本批次提交体现了三个发展方向：**模型多样性**（新增MiniMax H3）、**接口标准化**（对齐OpenAI API）和**工程成熟度**（版本发布与依赖锁定）。这些变化共同推动项目从研究原型向生产级工具演进，增强其在视频生成领域的竞争力。特别是API标准化，可能吸引更多开发者基于FastVideo构建应用，形成生态正循环。版本发布则为用户提供稳定选择，增强社区信心。整体来看，这批提交是项目迈向更广泛采用的重要一步。

## 详细提交记录

### [ac48bb3](https://github.com/hao-ai-lab/FastVideo/commit/ac48bb3cd12c7a8feb23170f5d539d7c40b4ba8c)

- **作者**: Aryan Kumar
- **时间**: 2026-08-28T19:54:33Z
- **提交信息**: [feat] Add MiniMax H3 MLX T2VA inference (#1770)

Co-authored-by: Aryan Kumar <aryank@Aryans-Mac-Studio.local>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>
Co-authored-by: CodeRabbit <noreply@coderabbit.ai>

### [3987b9d](https://github.com/hao-ai-lab/FastVideo/commit/3987b9ddcd102ecfebb73900a3f306701487b46b)

- **作者**: William Lin
- **时间**: 2026-08-28T17:09:58Z
- **提交信息**: [feat] Align multimodal OpenAI serving APIs (#1781)

### [c7da2f5](https://github.com/hao-ai-lab/FastVideo/commit/c7da2f5d6018d5f8b9f4e69da434382f344fe145)

- **作者**: William Lin
- **时间**: 2026-08-28T09:03:18Z
- **提交信息**: [chore]: release v0.2.1 (#1778)

### [39ae1de](https://github.com/hao-ai-lab/FastVideo/commit/39ae1decc0dd9aeeaa9fee00f6df9d571e80a09f)

- **作者**: William Lin
- **时间**: 2026-08-28T09:02:27Z
- **提交信息**: [misc] pin fastvideo-kernel to exact 0.3.5 (#1777)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34403
- **最后更新**: 2026-08-29T02:14:35Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 2
- **主要提交者**: Lucain, Sayak Paul

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本批提交包含**功能优化**（1项）和**测试重构**（3项），无Bug修复或文档更新。

### 2. 关键变更点
- **模型加载优化**（c1bf18c）：在`from_pretrained`入口处一次性解析revision，确保后续所有文件获取固定在同一commit，避免重复解析。
- **测试代码重构**（3项）：按字母顺序（E/G、H/I、J系列）系统性地重构pipeline测试，统一测试结构。

### 3. 对项目的影响
- **加载流程**：显著提升多文件模型加载的稳定性和缓存命中率，减少因revision漂移导致的版本不一致问题。
- **测试维护**：重构使测试更模块化、可读性更强，降低后续维护成本，为新增pipeline测试提供清晰范式。

### 4. 值得关注的技术点
- 依赖`huggingface_hub 1.26.0`新增的`resolve_revision`API，体现对上游工具的积极跟进。
- 测试重构采用“显式集合定义”方式，提高测试配置的透明度和可追溯性。

### 5. 对项目发展的影响
diffusers作为多模态生成模型库，模型加载的可靠性直接影响用户体验。该优化确保大型多文件模型（如SDXL、Flux）加载时版本一致性，是基础设施层面的重要改进。测试重构则反映项目在规模扩大后对代码质量的重视，为持续集成和快速迭代奠定基础。整体上，本批提交体现了“**夯实基础、优化体验**”的稳健发展策略。

## 详细提交记录

### [c1bf18c](https://github.com/huggingface/diffusers/commit/c1bf18c92c6285334adcaac7e75ef8946a227f49)

- **作者**: Lucain
- **时间**: 2026-08-28T16:40:26Z
- **提交信息**: [Download] Resolve the revision once at the beginning of from_pretrained (#14340)

* Resolve the revision once at the beginning of from_pretrained

Use `huggingface_hub.resolve_revision` (new in huggingface_hub 1.26.0) at the
top of the loading entrypoints so that every file fetched afterwards is pinned
to the same commit and can be served from the cache without re-resolving the
revision on each call.

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* less comments

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [9f7aee4](https://github.com/huggingface/diffusers/commit/9f7aee48215c5d01b1d84b52058669710596c7ee)

- **作者**: Sayak Paul
- **时间**: 2026-08-28T07:38:49Z
- **提交信息**: [tests] refactor j series pipeline tests (#14632)

* refactor j series pipeline tests

* explicit set definitions

### [8e7f4c9](https://github.com/huggingface/diffusers/commit/8e7f4c9068231df5845c4a50f1f831ed9b97add5)

- **作者**: Sayak Paul
- **时间**: 2026-08-28T07:16:48Z
- **提交信息**: [tests] refactor h and i series pipelines (#14633)

refactor h and i series pipelines

### [552db5f](https://github.com/huggingface/diffusers/commit/552db5faf2412cb56256c4b86a4fc67385e36a7a)

- **作者**: Sayak Paul
- **时间**: 2026-08-28T07:16:31Z
- **提交信息**: [tests] refactor e and g series pipeline tests (#14631)

refactor e and g series pipeline tests

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
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


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13017
- **最后更新**: 2026-08-29T01:46:52Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 提交分析（第1/1批）

## 主要更新类型
本次提交为**版本发布**（version 2.1.5），属于常规的版本迭代更新，非单一功能新增或Bug修复，而是包含多项改进的综合性发布。

## 关键变更点
提交信息仅显示版本号更新（#1652），未附带详细变更日志。结合项目背景，版本号从2.1.x递增至2.1.5，通常意味着：
- 修复了上一版本中发现的若干问题
- 可能包含对现有功能（如视频合成、图像编辑、模型推理等）的微调优化
- 可能更新了依赖库版本或兼容性适配

## 对项目的影响
作为活跃的开源项目（Trendshift榜单在列），频繁的版本迭代有助于：
- 维持用户信任，表明项目处于积极维护状态
- 及时修复社区反馈的问题，提升稳定性
- 为后续大版本功能更新奠定基础

## 值得关注的技术点
由于提交信息过于简略，无法直接判断具体技术改动。但DiffSynth-Studio作为视频/图像合成工具，版本更新可能涉及：
- 扩散模型推理效率优化
- 多模态特征融合的精度调整
- 对最新PyTorch或CUDA版本的适配

## 对项目发展的影响
DiffSynth-Studio定位于创意内容生成工具，其核心价值在于易用性和生成质量。本次版本更新虽小，但持续的小步快跑策略有助于：
- 保持与上游模型库（如ModelScope）的兼容性
- 积累用户反馈，为重大功能（如新模型支持、交互式编辑）铺路
- 在竞争激烈的生成式AI工具市场中维持竞争力

**总结**：这是一次常规的维护性版本发布，虽无显著功能亮点，但体现了项目团队的持续投入，对维持项目健康度和用户生态有积极意义。建议关注后续详细的Release Notes以获取具体变更内容。

## 详细提交记录

### [102fe99](https://github.com/modelscope/DiffSynth-Studio/commit/102fe9980b9375ecb6436d360297a00327472535)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-28T07:11:00Z
- **提交信息**: update to version 2.1.5 (#1652)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32640
- **最后更新**: 2026-08-29T03:17:18Z

## 提交统计

- **昨日提交总数**: 45
- **提交者数量**: 30
- **主要提交者**: Gregory Leleytner, karverma-amd, Артем Савкин

## AI分析总结

# SGLang 昨日提交分析（45条提交）

## 一、主要更新类型

- **Bug修复**（约15条）：覆盖MoE延迟、KV缓存、NPU算子、CPU兼容性等
- **性能优化**（约10条）：FP8 GEMM路由、AMD split-K启发式调优、HiCache预取优化
- **架构重构**（约8条）：JIT kernel目录重组、配置解析管线重构、diffusion API参数作用域
- **CI/基础设施改进**（约6条）：JIT测试拆分、ROCm镜像发布、subprocess死锁修复
- **新功能/硬件支持**（约6条）：ROCm 10镜像、NPU分布式推理、GLM-5.3 cookbook
- **文档更新**（约3条）：Tencent cookbook重命名、GLM-5.3 cookbook新增

## 二、关键变更点与项目方向

1. **JIT kernel与expert-pack目录重构**（db6f0a9）：配合CI测试拆分（96a4dcd、6ff2fe6），体现项目在kernel管理规范化上的投入，为多硬件后端扩展奠定基础。
2. **HiCache系列优化**（8e04f66、1061e34、3f1031d、3785b2d、f611e0c、c9bba09）：围绕L3存储预取、加载回退、并发控制展开，表明项目正强化长序列场景下的缓存层次管理能力。
3. **MoE路由与kernel优化**（4d78d59、3254f9b、b644771）：支持DP>1的模拟专家路由、Blackwell SM预留、Kimi K3 EP-A2A快速路径，显示项目在MoE推理效率上的持续深耕。
4. **配置系统重构**（ef20fab、7bc3204、43c63a2、c2928e8）：由Claude辅助的系列重构，将配置解析从record中解耦，提升代码可维护性。
5. **多硬件平台适配**（9579bff、c7879af、d3b972c、0c7d017）：AMD ROCm 10镜像、NPU算子修复、XPU延迟导入，体现全硬件覆盖战略。

## 三、项目影响与潜在意义

- **稳定性提升**：修复KV cache池过小（23cb11a）、batch请求状态竞争（70088aa）等关键问题，降低生产环境故障率。
- **性能增益**：SM90 FP8 GEMM路由至Torch（e1b3bba）、AMD MI355X split-K调优（2a96ebf）等，直接提升推理吞吐。
- **架构演进**：配置系统重构和JIT kernel目录重组，为后续功能扩展提供更清晰的代码结构。
- **生态扩展**：GLM-5.3 cookbook、Hy4-Preview文档更新，增强对最新模型的支持吸引力。

## 四、值得关注的技术点

1. **DeepGEMM MegaMoE的SM预留机制**（3254f9b）：针对Blackwell架构的细粒度资源调度。
2. **HiCache的混合预取丢弃自愈**（3f1031d）：缓存一致性维护的创新方案。
3. **MoE LoRA对齐JIT kernel的ROCm支持**（d3b972c）：跨平台kernel编译适配。
4. **diffusion kernel的transposed residual-gate add**（45424d8）：算子层面的模型结构适配。
5. **配置解析管线从record中移出**（c2928e8）：AI辅助重构的架构现代化尝试。

## 五、对项目发展的整体影响

SGLang正从单一推理引擎向**多硬件、多模型、生产级**的推理平台演进。昨日提交显示三条主线：**kernel层跨平台优化**（JIT重构、ROCm/NPU适配）、**缓存与内存管理深化**（HiCache系列、KV cache修复）、**MoE推理链路强化**（路由、调度、LoRA）。这些工作共同支撑项目在长上下文、大模型、多后端场景下的竞争力，同时通过CI和文档改进降低贡献门槛，吸引更广泛社区参与。配置系统的AI辅助重构也预示项目正探索更高效的开发协作模式。整体而言，项目处于快速迭代期，基础设施完善与前沿特性并进。

## 详细提交记录

### [db6f0a9](https://github.com/sgl-project/sglang/commit/db6f0a9d5318d890810fd1114024949e8ef0e7cc)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-28T23:41:25Z
- **提交信息**: Refactor JIT kernel and expert-pack directory layout (#36704)

### [50bc1a3](https://github.com/sgl-project/sglang/commit/50bc1a3767e955a06317082c1e6574fec0d55783)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-28T23:40:46Z
- **提交信息**: [diffusion] Keep Cosmos3 Nano resident on 96 GB GPUs (#36641)

### [e1b3bba](https://github.com/sgl-project/sglang/commit/e1b3bba3ccf5120e02aa0a87a45b12dc55741193)

- **作者**: Gregory Leleytner
- **时间**: 2026-08-28T23:35:37Z
- **提交信息**: [Kernel] Route large SM90 row/column-scaled FP8 GEMMs to Torch (#34318)

### [96a4dcd](https://github.com/sgl-project/sglang/commit/96a4dcdde826c1fa395ad2df5d6db236a03dd7cb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-28T23:26:49Z
- **提交信息**: [CI] Slim JIT kernel unit tests (#36887)

### [d12b313](https://github.com/sgl-project/sglang/commit/d12b313b93e1547d9b02c3a84426aa88519fc494)

- **作者**: Cheng Wan
- **时间**: 2026-08-28T22:05:08Z
- **提交信息**: fix: KT's last MoE layer stops deferring experts again (#36921)

### [ca179b7](https://github.com/sgl-project/sglang/commit/ca179b761b7e446a1412d3dc1d6dbbbfec1c0818)

- **作者**: Trevor Morris
- **时间**: 2026-08-28T21:56:23Z
- **提交信息**: Use kernel build node for cu134 image (#36912)

### [60f6d77](https://github.com/sgl-project/sglang/commit/60f6d77a9836561d289d56cd3306e0fb00c949b6)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-28T21:29:27Z
- **提交信息**: [mem_cache] Carry `swa_evicted_seqlen` into `SWARadixCache.cache_unfinished_req` (#36909)

### [4d78d59](https://github.com/sgl-project/sglang/commit/4d78d59e516f96b1a86e1dd1a458fda2664427d6)

- **作者**: Jonny Kong
- **时间**: 2026-08-28T21:22:45Z
- **提交信息**: [MoE] Make simulated expert routing support DP>1, and fuse into one triton kernel (#29718)

Co-authored-by: jonnykong <jonnykong@fb.com>

### [f65b2b2](https://github.com/sgl-project/sglang/commit/f65b2b2b157930e34c99dc659dd12aa8759455b2)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-28T21:16:53Z
- **提交信息**: [Fix] Lazy-import aiter in DSv4 paged_decode to unbreak CPU CI (#36914)

### [2a96ebf](https://github.com/sgl-project/sglang/commit/2a96ebf6486de5016f40c3f8c6b43536c01f5cc5)

- **作者**: karverma-amd
- **时间**: 2026-08-28T20:48:41Z
- **提交信息**: [AMD][DSV4] perf: retune decode split-K heuristic for MI355X (#36094)

### [ade4f4b](https://github.com/sgl-project/sglang/commit/ade4f4ba8b3113688ab7095de2b3cad0139e7e57)

- **作者**: Shuwen Wang
- **时间**: 2026-08-28T20:45:59Z
- **提交信息**: fix: report the real backend for non-CUDA CI registrations in /rerun-test (#36778)

### [3254f9b](https://github.com/sgl-project/sglang/commit/3254f9b47c9f6d36908a3bf6248e4085d5b16db0)

- **作者**: weireweire
- **时间**: 2026-08-28T20:37:36Z
- **提交信息**: [Blackwell] Reserve SMs for DeepGEMM MegaMoE grid barriers (#36657)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

### [70088aa](https://github.com/sgl-project/sglang/commit/70088aa5dbb77a7e70a16a4fb1a106fc7e8b2764)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-08-28T19:57:07Z
- **提交信息**: Fix KeyError on batch requests whose state is freed before it is read (#36638)

### [c7879af](https://github.com/sgl-project/sglang/commit/c7879af887c0293be9c32f3e67b4ae05bd6b568b)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-08-28T19:00:25Z
- **提交信息**: [AMD] release rocm10 image for gfx1250 from amd_helios (#36892)

### [f611e0c](https://github.com/sgl-project/sglang/commit/f611e0c07348a84019ce747763a9bf9ba50a2255)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-28T18:12:51Z
- **提交信息**: [HiCache] Fence load-back behind the forward stream (#36738)

### [c9bba09](https://github.com/sgl-project/sglang/commit/c9bba091f800d491ea0b8d2177ce77b699f995b5)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-28T18:12:10Z
- **提交信息**: [HiCache] Key storage prefetch by the request namespace (#36382)

### [ef20fab](https://github.com/sgl-project/sglang/commit/ef20fab38a03490e2cdf1b7377145ca3a3f2bfc5)

- **作者**: Cheng Wan
- **时间**: 2026-08-28T17:26:29Z
- **提交信息**: config: the forwarding slots go; the dispatcher calls the family directly (#36792)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7bc3204](https://github.com/sgl-project/sglang/commit/7bc32041170c6585c1a05be102dc0eeb72ab9d4c)

- **作者**: Cheng Wan
- **时间**: 2026-08-28T17:21:32Z
- **提交信息**: config: three cache and pool readers take the bags (#36791)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [43c63a2](https://github.com/sgl-project/sglang/commit/43c63a22ffe7f7956afbe603e4e1c7e4919d4d19)

- **作者**: Cheng Wan
- **时间**: 2026-08-28T17:18:46Z
- **提交信息**: config: the derived parallel widths are computed from the leaves (#36790)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [c2928e8](https://github.com/sgl-project/sglang/commit/c2928e86d78ee99a295c313409b7e8918d0c1b03)

- **作者**: Cheng Wan
- **时间**: 2026-08-28T17:17:24Z
- **提交信息**: config: the resolution pipeline moves out of the record (#36789)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [726665e](https://github.com/sgl-project/sglang/commit/726665e08e7f2880ad9126efea26c78adfa54b32)

- **作者**: pllimax
- **时间**: 2026-08-28T17:11:02Z
- **提交信息**: [CI] Read subprocess stdout on a background thread to avoid EOF deadlock (#36673)

### [8e04f66](https://github.com/sgl-project/sglang/commit/8e04f66a7046fa083cda3f5b8e8325632a5af8fd)

- **作者**: Chao Shi
- **时间**: 2026-08-28T16:52:53Z
- **提交信息**: HiCache: avoid unnecessary all-reduce in check_prefetch_progress (#36425)

### [23cb11a](https://github.com/sgl-project/sglang/commit/23cb11ae0114dd0946db6a7e5c3b88ab0cc56cde)

- **作者**: Alison Shao
- **时间**: 2026-08-28T16:47:23Z
- **提交信息**: Fix KV cache pool sized far too small when weight-loading memory is still referenced (#36583)

### [fcb4ff1](https://github.com/sgl-project/sglang/commit/fcb4ff1ee3af7a336be8a06ed85855eb44fb3439)

- **作者**: 黄孝君
- **时间**: 2026-08-28T16:42:28Z
- **提交信息**: [NPU] Update sgl-kernel-npu version (#36433)

### [6ff2fe6](https://github.com/sgl-project/sglang/commit/6ff2fe6a6ad8e2af96739e381518786fb782b4ff)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-08-28T16:32:58Z
- **提交信息**: CI: split JIT kernel unit tests into two partitions (#36775)

### [9579bff](https://github.com/sgl-project/sglang/commit/9579bff86085f886cf6d1ec69349017d0caeced4)

- **作者**: Bingxu Chen
- **时间**: 2026-08-28T15:03:39Z
- **提交信息**: [AMD] Add ROCm 10 (gfx942 / gfx950) release images (#36434)

### [395c225](https://github.com/sgl-project/sglang/commit/395c2258c3749f6de2ae677585f8c838f5063986)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-28T14:56:06Z
- **提交信息**: [Docs] Add GLM-5.3 cookbook (#36827)

Co-authored-by: JustinTong0323 <xinyuantong.cs@gmail.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Mohammad Angkad <176301910+mmangkad@users.noreply.github.com>

### [b644771](https://github.com/sgl-project/sglang/commit/b644771e07e39c8a5997a230f4e87175364c020b)

- **作者**: 匡胤鑫
- **时间**: 2026-08-28T13:46:35Z
- **提交信息**: [Fix] Route the Mooncake MoE A2A backend through Kimi K3's EP-A2A / SP-MoE fast path (#36862)

### [ecbadf0](https://github.com/sgl-project/sglang/commit/ecbadf0b4bd57c67b4c7eecfcf4b9ae6b6dde56b)

- **作者**: Артем Савкин
- **时间**: 2026-08-28T12:39:05Z
- **提交信息**: [NPU] [Diffusion] support distributed inference pipeline for GLM-Image  (#31320)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [803b4fb](https://github.com/sgl-project/sglang/commit/803b4fb31c30229ebde1ea3b95aa087e10b0cfd0)

- **作者**: Mick
- **时间**: 2026-08-28T11:08:30Z
- **提交信息**: [diffusion] refactor: scope model-specific API parameters (#35613)

### [d567064](https://github.com/sgl-project/sglang/commit/d56706459c8e52ec3ab1c41dae778e4fe03e0da3)

- **作者**: ming_wang
- **时间**: 2026-08-28T09:41:49Z
- **提交信息**: bugfix for index_fill_ on NPU (#36759)

### [74df026](https://github.com/sgl-project/sglang/commit/74df026877a490720739749c825b8de3a8423dd5)

- **作者**: Xinguo Zhu
- **时间**: 2026-08-28T09:31:26Z
- **提交信息**: fix(cpu): skip GPU JIT MoE top-k on CPU (#35677)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [9cee0a3](https://github.com/sgl-project/sglang/commit/9cee0a31d1a7f39526ba02b8ffb9e3b2854fbef2)

- **作者**: K Chiranjeevi
- **时间**: 2026-08-28T09:18:03Z
- **提交信息**: [XPU] Lazily import tvm_ffi-dependent all_reduce kernel in minimax_m2 (#35290)

Signed-off-by: Chiranjeevi Koppula <ckoppula@habana.ai>

### [69a49fe](https://github.com/sgl-project/sglang/commit/69a49fede863062ef0cabe87debeaa6eee87c271)

- **作者**: McZyWu
- **时间**: 2026-08-28T09:15:52Z
- **提交信息**: fix(kimi-k3): preserve dense ModelSlim MLA weights (#36603)

### [1e6d041](https://github.com/sgl-project/sglang/commit/1e6d041f78cd4a4d94ed43fa0634ccaa231fe048)

- **作者**: Zheng Wengang
- **时间**: 2026-08-28T09:02:16Z
- **提交信息**: [BugFix][VLM] keep Qwen3-VL MoE inference deepstack order (#34690)

### [3785b2d](https://github.com/sgl-project/sglang/commit/3785b2d20f0f92c1b0e20fc39e92f6f588c0851c)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-28T08:59:06Z
- **提交信息**: [HiCache] Reject load-back specs that claim nodes pinned by an in-flight load-back (#35931)

### [eebb99c](https://github.com/sgl-project/sglang/commit/eebb99c049aa557d939ba0f9fe392a9bd318e51a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-28T08:58:19Z
- **提交信息**: [diffusion][kernel] avoid 4D scale-shift autotuning (#36521)

### [45424d8](https://github.com/sgl-project/sglang/commit/45424d8434f99ddaf960edc464c38bcfad8f12d5)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-28T08:54:37Z
- **提交信息**: [diffusion][kernel] support transposed residual-gate add (#36504)

### [1061e34](https://github.com/sgl-project/sglang/commit/1061e34785ae0264c09d98b50690903dbf3be7aa)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-28T08:35:21Z
- **提交信息**: [HiCache] Retry L3 storage prefetch after a missed attempt (#36227)

### [3f1031d](https://github.com/sgl-project/sglang/commit/3f1031d697210d5725ebe193d68a3712566d176a)

- **作者**: Zhiqiang Xie
- **时间**: 2026-08-28T08:33:40Z
- **提交信息**: [HiCache] Heal the storage existence cache on a hybrid prefetch discard (#36386)

### [989e51b](https://github.com/sgl-project/sglang/commit/989e51ba9c4c6bf0a360b49c611527c8291db75f)

- **作者**: Haoguang Cai
- **时间**: 2026-08-28T08:31:52Z
- **提交信息**: [Docs] Rename Tencent cookbook page titles to "Hy4 preview" / "Hy3 preview" (#36823)

### [d3b972c](https://github.com/sgl-project/sglang/commit/d3b972cbf0e349c1934afb4c64c2e058a9a2dcbd)

- **作者**: Yikai Zhang
- **时间**: 2026-08-28T08:18:42Z
- **提交信息**: fix(lora): build the MoE LoRA align JIT kernel on ROCm (#36379)

Co-authored-by: amdpilot-upstream-sync <amdpilot-upstream-sync@users.noreply.github.com>

### [0c7d017](https://github.com/sgl-project/sglang/commit/0c7d017dbbaa7bafd62e78f4920f845637985165)

- **作者**: Bingxu Chen
- **时间**: 2026-08-28T08:11:53Z
- **提交信息**: [AMD][Fix] Qwen3.5: make empty-batch guard tuple-aware on fused AR+quant path (#35341)

### [2a7fb51](https://github.com/sgl-project/sglang/commit/2a7fb511c94840aac7766d37788c72b963a90d0c)

- **作者**: Bingxu Chen
- **时间**: 2026-08-28T08:05:59Z
- **提交信息**: [AMD][CI] Limit HiCache MGSM eval concurrency on ROCm (#36308)

### [2960d69](https://github.com/sgl-project/sglang/commit/2960d696228efc8ef930565f9f5dac9dffb6e571)

- **作者**: zijiexia
- **时间**: 2026-08-28T07:19:07Z
- **提交信息**: [Cookbook] Hy4-Preview follow-ups: runtime-accurate recipes + released-model info (#36808)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1261
- **最后更新**: 2026-08-28T22:22:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交属于**性能优化与代码清理**，核心是移除一个已无存在必要的回退路径（fallback），并强化了布局契约的强制校验。

### 2. 关键变更点
- **移除NHD逐张量物化回退**：此前当输入张量不满足NHD（非连续、非特定维度顺序）布局时，系统会通过`_keep_or_pack`将数据复制为连续内存再送入CUDA内核。现在所有CUDA内核族（persist-D / split-D / M4N2，覆盖fp8/fp4/fp16）均已原生支持NHD全局内存读取，包括打包NHD视图和跨步融合QKV分块视图，因此该回退路径不再被触发。
- **删除`is_nhd_zero_copy_input`探测函数**：该函数仅服务于旧构建的物化路径，现已一并移除。
- **强化布局违规检测**：不符合NHD布局契约的张量现在会在C++布局门控处直接报错，而非静默复制。

### 3. 对项目的影响与潜在意义
- **消除隐式性能陷阱**：此前不合规布局会触发静默拷贝，用户难以察觉性能损耗。现在要么原生支持，要么直接报错，行为更透明。
- **减少代码分支与维护成本**：移除回退路径和探测函数，简化了数据流逻辑，降低后续维护复杂度。
- **提升推理确定性**：布局违规不再被“容忍”，有助于在分布式或量化场景下提前暴露问题，避免运行时意外。

### 4. 值得关注的技术点
- **NHD布局的全面原生支持**：所有内核族已统一读写NHD全局内存，说明项目在内存布局上已收敛到单一契约，这是工程成熟度的体现。
- **“契约违规即报错”的设计哲学**：用显式失败替代隐式降级，符合高性能推理引擎对可预测性的追求。
- **跨精度（fp8/fp4/fp16）与跨内核族的一致性**：表明量化与并行策略已与布局设计深度耦合，而非临时补丁。

### 5. 对项目发展的影响
cache-dit定位为“PyTorch原生、带缓存/并行/量化/CPU卸载的DiT推理引擎”，其核心卖点是**高性能与低开销**。本次提交通过消除不必要的内存拷贝和分支判断，进一步压低了推理路径的常数开销，强化了“零拷贝”承诺。同时，布局契约的严格化有助于在后续引入更多量化格式或并行策略时，保持代码库的可维护性和性能可预测性。从项目演进看，这标志着其内核层已进入**收敛与硬化阶段**——不再需要兼容旧路径，而是聚焦于核心路径的极致优化，为未来支持更大模型、更长序列的推理场景奠定更干净的基础。

## 详细提交记录

### [26c72d7](https://github.com/vipshop/cache-dit/commit/26c72d7654f0989f3da5de6f41a3b0c68696e8a0)

- **作者**: DefTruth
- **时间**: 2026-08-28T10:30:51Z
- **提交信息**: ffpa: drop the NHD per-tensor materialization fallback (#1107)

Every CUDA kernel family (persist-D / split-D / M4N2 across fp8 / fp4 /
fp16) now reads NHD gmem natively -- packed-NHD and strided fused-QKV
chunk views alike -- so the _keep_or_pack materialization fallback has
no legitimate trigger left: tensors outside the NHD layout contract are
contract violators and now fail loudly in the C++ layout gates instead
of silently paying a copy. Also drops the is_nhd_zero_copy_input probe
that only served the old-build materialization path.

Co-authored-by: copilot-swe-agent[bot] <198982749+Copilot@users.noreply.github.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 90352
- **最后更新**: 2026-08-29T03:28:21Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 23
- **主要提交者**: ukannika, stefankoncarevic, Jung Jiyu

## AI分析总结

# vLLM 昨日提交分析总结

## 一、主要更新类型

本次提交涵盖多种类型：**Bug修复**（约8项）、**性能优化**（约7项）、**ROCm/AMD平台适配**（约6项）、**CI/构建改进**（约4项）、**功能新增**（2项）、**文档更新**（1项）、**类型检查修复**（1项）。

## 二、关键变更点与项目方向

**1. 多模态模型支持增强**：恢复Moondream3 MoE在fused-path中的all-reduce处理，支持Idefics3和SmolVLM的ViT全CUDA图，修复吞吐量后端多模态支持。这直接呼应vLLM“为所有人提供易用、快速、廉价的LLM服务”的使命，扩展了模型覆盖范围。

**2. 推测解码扩展**：为PLaMo3模型新增推测解码支持，持续完善vLLM的推理加速能力。

**3. 性能优化深入**：包括Rust前端SSE流式热路径优化、辅助帧解析减少拷贝、xdrope_positions H2D拷贝拆分、Kimi-K3低M融合MoE尾部优化等，体现对推理延迟和吞吐的持续追求。

**4. ROCm/AMD平台持续投入**：启用AITER PA gluon解码、移除FP4环境变量、启用block-quantized FP8融合共享专家、修复多个ROCm CI问题。这表明vLLM正积极拓展AMD GPU生态支持。

**5. 基础设施稳定性**：修复RayExecutorV2 TCPStore端口绑定、KV缓存内存释放、int32 token偏移溢出、breakable graph环境变量设置等问题，强化分布式推理的可靠性。

## 三、项目影响与潜在意义

- **稳定性提升**：多个Bugfix涉及分布式执行器、KV缓存生命周期、内存管理等核心路径，直接提升生产环境可靠性。
- **性能增益**：Rust前端优化和kernel级优化（如SplitKrc工作区预分配）将改善端到端推理延迟。
- **生态扩展**：ROCm相关提交占比高，表明vLLM正从NVIDIA独占走向多硬件平台支持，扩大用户基础。
- **开发流程规范化**：新增PR标题格式检查、预编译CUDA变体失败关闭机制，提升协作效率。

## 四、值得关注的技术点

1. **异步KV加载**：在无同步加载时，KV加载在forward启动后异步执行，优化调度流水线。
2. **Rust前端SSE优化**：vLLM正用Rust重写关键路径，本次优化流式传输热路径，减少拷贝。
3. **CUDA图覆盖扩展**：ViT全CUDA图支持减少多模态模型图捕获开销。
4. **Quark文档更新**：增加在线量化支持，完善量化工具链。

## 五、对项目发展的影响

从README可知，vLLM定位为“易用、快速、廉价的LLM服务”。本批提交从三个维度推动这一目标：**性能**（kernel优化、Rust前端、CUDA图）、**可用性**（多模态支持、推测解码、文档完善）、**可扩展性**（ROCm适配、分布式稳定性）。特别是ROCm相关提交占比超20%，显示vLLM正积极打破GPU供应商锁定，向“为每个人”的愿景迈进。整体来看，项目在保持性能领先的同时，正系统性地提升多硬件、多模型、多场景的覆盖能力。

## 详细提交记录

### [9662ab0](https://github.com/vllm-project/vllm/commit/9662ab0835e9eac28ac7d95d4b25ecb7140b7bf3)

- **作者**: Ace Eldeib
- **时间**: 2026-08-28T23:11:50Z
- **提交信息**: [Bugfix] Set breakable graph env before Ray actor import (#53293)

Signed-off-by: Ace Eldeib <aeldeib@coreweave.com>
Co-authored-by: Codex <codex@openai.com>

### [ae5b8e4](https://github.com/vllm-project/vllm/commit/ae5b8e4a8d77a5de404a0cf9a91a56e8c7f2a94e)

- **作者**: ukannika
- **时间**: 2026-08-28T22:54:39Z
- **提交信息**: [ROCm][PERF] Enable AITER PA gluon decode for MiniMax-M3 MTP and dense layers (#52849)

Signed-off-by: ukannika <uma.kannikanti@amd.com>
Signed-off-by: ykamiset <yaminipreethi.kamisetty@amd.com>
Co-authored-by: ykamiset <yaminipreethi.kamisetty@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b131311](https://github.com/vllm-project/vllm/commit/b131311fb4ef7adc2752333ed7ae87182f5e2665)

- **作者**: Bugen Zhao
- **时间**: 2026-08-28T22:50:47Z
- **提交信息**: [CI/Build] Add advisory PR title format check (#54263)

### [df14152](https://github.com/vllm-project/vllm/commit/df14152ac6b09f76345dae05b99541c3e87f8d35)

- **作者**: Shinichi Hemmi
- **时间**: 2026-08-28T22:31:07Z
- **提交信息**: [Model] Support speculative decoding method for PLaMo3 (#54239)

Signed-off-by: Shinichi Hemmi <shemmi@preferred.jp>

### [fd98d32](https://github.com/vllm-project/vllm/commit/fd98d32f732674b63705494ba3965f21aa449aba)

- **作者**: Charlie Fu
- **时间**: 2026-08-28T22:11:42Z
- **提交信息**: [ROCm][CI] Fix test_ray_v2_executor (#54249)

Signed-off-by: charlifu <charlifu@amd.com>

### [c274d36](https://github.com/vllm-project/vllm/commit/c274d361031e5bf920af13071794056aa704e690)

- **作者**: Oxana Korzh
- **时间**: 2026-08-28T22:06:42Z
- **提交信息**: [Bugfix] Keep the Moondream3 MoE all-reduce out of the fused-path try (#54152)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [2aac565](https://github.com/vllm-project/vllm/commit/2aac565cae880087d752e90f1a08dcd9b369f9a0)

- **作者**: Summer Yang
- **时间**: 2026-08-28T21:58:00Z
- **提交信息**: [Core][KV Connector] Start async KV loads after the forward launch when no sync loads are scheduled (#53333)

Signed-off-by: Summer Yang <girasoleyang@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [96242aa](https://github.com/vllm-project/vllm/commit/96242aa50d196993735854f03bd717496e88b7c3)

- **作者**: Nick Hill
- **时间**: 2026-08-28T21:27:09Z
- **提交信息**: [Bugfix][MRV2] Release layer-bound KV cache memory in shutdown() (#54246)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>

### [7073294](https://github.com/vllm-project/vllm/commit/70732942c6e0bcbe83a74cafc9214a0f49fd8929)

- **作者**: Nick Hill
- **时间**: 2026-08-28T21:22:53Z
- **提交信息**: [Bugfix][ROCm] Pre-allocate `wvSplitKrc` static workspaces before KV init (#54247)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.ai>

### [21fa2c5](https://github.com/vllm-project/vllm/commit/21fa2c5a2a471b9c978a5a3b7208a4c7fe88cefa)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-28T20:49:19Z
- **提交信息**: [Mypy] Fix mypy typing for model interfaces and H/I models (#54079)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [74850f9](https://github.com/vllm-project/vllm/commit/74850f9f669085c07353a5673b1fb2f352480cda)

- **作者**: Reid
- **时间**: 2026-08-28T20:35:38Z
- **提交信息**: [Rust Frontend] Optimize SSE streaming hot path (#51321)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [06cccf8](https://github.com/vllm-project/vllm/commit/06cccf8730a199817be58e2de576918fe7a46e1e)

- **作者**: canlahlah
- **时间**: 2026-08-28T20:23:36Z
- **提交信息**: [Bugfix] Fix int32 token offset overflow in fused SiLU block quant (#53409)

Signed-off-by: Anni <dranox2222@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [67e86d1](https://github.com/vllm-project/vllm/commit/67e86d1e6fbcab31a404a620521a5179a4c5fe67)

- **作者**: aoshen02
- **时间**: 2026-08-28T19:27:22Z
- **提交信息**: [BugFix] Bind RayExecutorV2 TCPStore before publishing its port (#50969)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [2f1cba7](https://github.com/vllm-project/vllm/commit/2f1cba799e02209e9782a747f7620e55d8251e67)

- **作者**: afriedri
- **时间**: 2026-08-28T18:59:53Z
- **提交信息**: [ROCm] remove VLLM_ROCM_USE_AITER_FP4_ASM_GEMM environment variable; make w4a4 use the preshuffle triton+asm by default (#53141)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Signed-off-by: afriedri <afriedri@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [31c5795](https://github.com/vllm-project/vllm/commit/31c579503dab4f5c1967adea2fde61fdc8319d2f)

- **作者**: hangy-amd
- **时间**: 2026-08-28T18:23:06Z
- **提交信息**: update quark docs to include online quantization (#52736)

Signed-off-by: Hang Yang <hangy@amd.com>

### [d9dabfa](https://github.com/vllm-project/vllm/commit/d9dabfa351acdb4ceaad18c9677bc7a08b6c04ea)

- **作者**: Yongye Zhu
- **时间**: 2026-08-28T17:45:36Z
- **提交信息**: [Kimi-K3][Kernel] Optimize the low-M fused latent MoE tail (#54168)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6f91e3d](https://github.com/vllm-project/vllm/commit/6f91e3d9537ea45128534ba9a234b81d6c843281)

- **作者**: Keyi Li
- **时间**: 2026-08-28T17:28:43Z
- **提交信息**: [Perf] Split xdrope_positions H2D copy into per-row transfers (#53412)

Signed-off-by: Keyi Li <likey6688@gmail.com>
Co-authored-by: Keyi Li <likey6688@gmail.com>

### [ffe690e](https://github.com/vllm-project/vllm/commit/ffe690eca95636e57de9e683445c6c0e3f6e3fa9)

- **作者**: Chipmunk
- **时间**: 2026-08-28T17:16:31Z
- **提交信息**: [MM][CG] Support ViT full CUDA graph for Idefics3 and SmolVLM (#47625)

Signed-off-by: Ryouichi Kurihara <ryouichi.kurihara.628@gmail.com>

### [06569a8](https://github.com/vllm-project/vllm/commit/06569a8696076eeae9558928b00f035ded8f8b60)

- **作者**: xuebwang-amd
- **时间**: 2026-08-28T16:23:07Z
- **提交信息**: [ROCm][Quantization][MOE] Enable fused shared experts for block-quantized FP8 (#53097)

Signed-off-by: xuebwang-amd <xuebwang@amd.com>

### [11012d2](https://github.com/vllm-project/vllm/commit/11012d2a35090a3c624d0aeeec0f407026fc4b12)

- **作者**: Bugen Zhao
- **时间**: 2026-08-28T16:01:17Z
- **提交信息**: [Rust Frontend] Reduce copy in auxiliary frame resolution (#54148)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [94a54f5](https://github.com/vllm-project/vllm/commit/94a54f581e1685a5706fe2809bd4ecb1a4c8e70b)

- **作者**: Xinyu Chen
- **时间**: 2026-08-28T14:12:17Z
- **提交信息**: [XPU]bump up vllm_xpu_kernels to 0.1.14.1 (#54203)

Signed-off-by: Xinyu Chen <xinyu1.chen@intel.com>

### [d1922cb](https://github.com/vllm-project/vllm/commit/d1922cb5a718259976fcb9044c18c9711c9ca694)

- **作者**: Michał Ganczarenko
- **时间**: 2026-08-28T10:28:25Z
- **提交信息**: [Bugfix] Restore multimodal support on the plain "vllm" throughput backend (#52168)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>

### [5f213ed](https://github.com/vllm-project/vllm/commit/5f213ed1592903b7bc38f173d320dac1b2769303)

- **作者**: stefankoncarevic
- **时间**: 2026-08-28T09:07:04Z
- **提交信息**: [ROCm][CI] Warm up the RLHF dev server before the pause/resume timing checks (#53594)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [3bb19cd](https://github.com/vllm-project/vllm/commit/3bb19cd8a32f9cd25f04883028ab3dc719f3edab)

- **作者**: Jung Jiyu
- **时间**: 2026-08-28T09:00:48Z
- **提交信息**: [Bugfix][CI/Build] Fail closed when selected precompiled CUDA variant is unavailable (#52545)

Signed-off-by: Jung Jiyu <jiyu.jung@navercorp.com>

### [f956e1c](https://github.com/vllm-project/vllm/commit/f956e1c343dc63720b50c01209bd5ada6d8589a2)

- **作者**: Thien Tran
- **时间**: 2026-08-28T08:32:20Z
- **提交信息**: [Kimi-K3][Bugfix] Fix low-latency GEMM fallback initialization (#54167)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [9236159](https://github.com/vllm-project/vllm/commit/9236159bb60e0a34dbf442a90f0f813780f2eb87)

- **作者**: stefankoncarevic
- **时间**: 2026-08-28T07:02:40Z
- **提交信息**: [ROCm][CI] Keep startup profiling from aborting when free memory grows (#53591)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-29
**监控日期**: 2026-08-28
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6439
- **最后更新**: 2026-08-29T03:36:04Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: ZacheryAU, prettygirlisnotme, Mu GuanLin

## AI分析总结

# vllm-omni 昨日提交分析

## 一、主要更新类型

本次提交涵盖**Bug修复**（4项）、**功能新增**（2项）、**性能优化**（1项）、**核心架构调整**（2项，含1项回滚），整体以稳定性和能力扩展为主。

## 二、关键变更点与项目方向的关系

**MiniCPM-o 多模态模型修复**（3项提交）是本次重点，涉及离线推理测试修复、视频帧与语音单元绑定、双工通话中打断与失败隔离。这些修复直接服务于项目“**易用、快速、廉价的omni模态服务**”核心目标，确保多模态交互的时序正确性和稳定性。

**Diffusion 管线增强**：Flux2Pipeline 的 `text_encoder_out_layers` 变为可配置，提升文本编码器输出层的灵活性，扩展了图像生成场景的适配能力。

**NPU 适配优化**：MossAudioTokenizer 解码中扩展 bf16 自动混合精度到 NPU，体现项目对**多硬件平台支持**的承诺。

**TTS 自适应缓冲控制器**：引入“自适应块斜坡”机制（Phase 2 缓冲反馈控制器），是流式语音合成延迟优化的关键进展，直接提升实时交互体验。

**MiniMax-H3 VAE 解码算子优化**：针对特定模型的性能调优，延续项目“**快速**”的定位。

**架构调整与回滚**：diffusion worker 标题拓扑感知的提交被回滚，说明团队在架构演进上保持审慎，避免引入不稳定因素。

## 三、项目影响与潜在意义

这些提交表明 vllm-omni 正从“可用”向“**好用**”迈进：MiniCPM-o 的系列修复完善了双工语音交互的可靠性，TTS 自适应缓冲控制为低延迟实时对话奠定基础，NPU 支持则拓宽了部署场景。回滚操作体现工程严谨性，防止架构变更影响稳定性。

## 四、值得关注的技术点

1. **双工通话的失败隔离与打断处理**：这是实时语音交互的核心难点，涉及事件时序和状态管理
2. **自适应块斜坡缓冲控制器**：动态调整缓冲策略以平衡延迟与稳定性，是流式推理的进阶优化
3. **NPU 上的 bf16 autocast**：跨硬件平台的精度策略一致性
4. **VAE 解码算子定制优化**：针对特定模型结构的底层性能挖掘

## 五、对项目发展的影响

结合 README 中“**为所有人提供易用、快速、廉价的 omni 模态服务**”的定位，这些提交从三个维度推动项目前进：**稳定性**（MiniCPM-o 系列修复）、**性能**（TTS 缓冲控制、VAE 算子优化）、**可扩展性**（Flux2 配置化、NPU 支持）。特别是 TTS 自适应缓冲和双工通话修复，直接关系到实时多模态交互的产品化落地，是项目从“支持多模态”走向“**优质多模态体验**”的关键一步。整体来看，项目正处于功能完善与架构收敛并行的阶段，工程化成熟度在持续提升。

## 详细提交记录

### [6d84409](https://github.com/vllm-project/vllm-omni/commit/6d84409a683aeef476ad2d47a839998ef2344b4b)

- **作者**: ZacheryAU
- **时间**: 2026-08-28T19:20:09Z
- **提交信息**: [bugfix][MiniCPM-o] Fix offline_inference/test_minicpmo_4_5.py and online_serving/ one (#5464)

Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ebb3b20](https://github.com/vllm-project/vllm-omni/commit/ebb3b20576736ec3ad264788b8721ec61b28aa8d)

- **作者**: Khairul Kabir
- **时间**: 2026-08-28T15:05:41Z
- **提交信息**: [Diffusion] Make Flux2Pipeline text_encoder_out_layers configurable (#6390)

Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [be335a8](https://github.com/vllm-project/vllm-omni/commit/be335a86f9af5bde108e11fb3e01d729553a3532)

- **作者**: Wallbreazzz
- **时间**: 2026-08-28T11:01:49Z
- **提交信息**: fix(npu): extend bf16 autocast to NPU in MossAudioTokenizer decode (#6664)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>
Signed-off-by: Canlin Guo <961750412@qq.com>
Co-authored-by: Canlin Guo <961750412@qq.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [d5aced9](https://github.com/vllm-project/vllm-omni/commit/d5aced92966e6f12134fe9a30679fdeab07e4bb9)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-28T09:30:03Z
- **提交信息**: Revert "[Core] Make diffusion worker titles topology-aware" (#6717)

### [4ad455e](https://github.com/vllm-project/vllm-omni/commit/4ad455e61e2857450594189895fe860596f402dc)

- **作者**: Wallbreazzz
- **时间**: 2026-08-28T09:11:05Z
- **提交信息**: [Feature][TTS] adaptive chunk ramp (Phase 2 buffer-feedback controller) (#6001)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>

### [da94c3e](https://github.com/vllm-project/vllm-omni/commit/da94c3ebe15c78f5c580936f6b18a6d97d03539b)

- **作者**: amy-why-3459
- **时间**: 2026-08-28T08:58:20Z
- **提交信息**: [Bugfix][MiniCPM-o] Bind omni-duplex video frames to the unit they close (#6404)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [13173d6](https://github.com/vllm-project/vllm-omni/commit/13173d6bbbd0f0ddd4f6caa2debabcf2375d911d)

- **作者**: prettygirlisnotme
- **时间**: 2026-08-28T08:00:30Z
- **提交信息**: [Core] Make diffusion worker titles topology-aware (#6307)

Signed-off-by: Dragonborn <1078757180@qq.com>

### [009b992](https://github.com/vllm-project/vllm-omni/commit/009b992c5b5d36acc55759dba7ed5acfee90d324)

- **作者**: Sy03
- **时间**: 2026-08-28T07:46:41Z
- **提交信息**: [Bugfix][MiniCPM-o] Isolate duplex handoff failures and barge-in (#6170)

Signed-off-by: Sy03 <1370724210@qq.com>

### [04b97a5](https://github.com/vllm-project/vllm-omni/commit/04b97a5922493f78293623d6169e62ccecde9116)

- **作者**: Mu GuanLin
- **时间**: 2026-08-28T07:14:33Z
- **提交信息**: [Perf] MiniMax-H3 VAE Decoder Ops (#6607)

Signed-off-by: mglyn <1203789601@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

---
