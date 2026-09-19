# GitHub Stars 合并报告 - 2026-09-18

**合并日期**: 2026-09-19
**监控日期**: 2026-09-18
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


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2216
- **最后更新**: 2026-09-18T23:46:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2830
- **最后更新**: 2026-09-18T21:15:32Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Chernobyllight, Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

# LightX2V 昨日提交分析总结

## 1. 主要更新类型

本批次共 4 个提交，类型分布为：**功能新增 2 项**（Qwen-Image-2.1 支持、CPU Block Offload）、**重构 2 项**（移除内置 Gradio UI、序列并行注意力 API 定稿）。整体以“能力扩展 + 架构收敛”为主，无 Bug 修复类提交。

## 2. 关键变更点与项目方向的关系

- **新增 Qwen-Image-2.1 支持**：持续扩充模型矩阵，延续 LightX2V 作为“多模型统一推理框架”的定位。
- **序列并行注意力 API 定稿**：将 Ulysses/Ring 注意力从旧 `apply` 接口迁移到显式 main/aux 契约，统一 FP8/FP4 量化配置，是推理性能基础设施的规范化收口。
- **CPU Block Offload 跨模型族集成**：覆盖 Hunyuan Image 3.0、MiniMax-H3、Qwen-Image-2512、Wan 2.1，支持 host/NUMA 权重共享，直击大模型显存瓶颈。
- **移除内置 Gradio UI 并隔离 SekoTalk resize 逻辑**：剥离非核心耦合，让框架更聚焦于推理引擎本身。

这些变更共同指向 README 强调的“轻量、高效视频生成推理框架”目标——既做宽（模型覆盖），又做深（并行与卸载优化），同时做减法（去 UI 耦合）。

## 3. 对项目的影响与潜在意义

- **显存门槛下降**：CPU offload 让大模型在有限 GPU 资源下可运行，扩大部署场景（消费级/边缘）。
- **并行能力标准化**：显式注意力契约降低了新模型接入成本，提升多后端一致性。
- **生态扩展**：Qwen-Image-2.1 的加入强化了与主流开源模型的同步节奏。
- **架构清晰化**：去 Gradio 后，项目边界更明确，利于库化集成与长期维护。

## 4. 值得关注的技术点

- **main/aux 显式契约**：区分 main-only、full-QKV、Q-only 辅助 KV 及动态布局，保留模型专属 RoPE、token 顺序与缓存重建，兼顾通用性与正确性。
- **seq_p_quant_scheme 统一**：将 FP8/FP4 通信配置归一，简化量化并行调参。
- **host/NUMA 权重共享**：跨模型族的共享 CPU block 卸载，配合 CLI 作用域选择与双语文档，工程完成度较高。
- **SekoTalk resize 隔离**：避免特定模型逻辑污染通用路径。

## 5. 基于项目背景的发展影响

LightX2V 定位为“轻量视频生成推理框架”，本批提交精准呼应三大支柱：**模型广度**（Qwen-Image-2.1）、**推理效率**（序列并行 API 定稿 + CPU offload）、**工程简洁性**（移除 UI）。序列并行与 offload 的组合，意味着项目正从“能跑”迈向“在受限硬件上高效跑”，这是推理框架商业与开源竞争力的关键。整体看，本批次是面向生产可用性的一次扎实推进，而非零散修补。

## 详细提交记录

### [5216198](https://github.com/ModelTC/LightX2V/commit/521619854887a80dee2e3e745185aa31a2a0abce)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-18T15:57:23Z
- **提交信息**: Support qwen-image-2.1 (#1533)

### [cde7c13](https://github.com/ModelTC/LightX2V/commit/cde7c13398cfe549ee1741ae246512ea016ca308)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-18T09:51:14Z
- **提交信息**: refactor: remove bundled Gradio UI and isolate SekoTalk resize handling (#1532)

### [a8afa64](https://github.com/ModelTC/LightX2V/commit/a8afa64af9b747f70ea3643e28dc0664cbb53d9d)

- **作者**: STwangyingrui
- **时间**: 2026-09-18T09:40:30Z
- **提交信息**: refactor(sp): finalize explicit sequence-parallel attention API (#1531)

## Summary

Finalize the public Ulysses/Ring attention API and migrate all reachable
consumers to the explicit main/aux contract.

## Changes

- Replace the legacy `apply` API with the finalized explicit contract.
- Cover main-only, full-QKV, Q-only auxiliary-KV, and dynamic layouts.
- Preserve model-specific RoPE, token ordering, cache, and output
reconstruction.
- Unify FP8/FP4 communication configuration under `seq_p_quant_scheme`.

### [a6cca57](https://github.com/ModelTC/LightX2V/commit/a6cca57f730642e2bcf3d44b8bc53a24123c553d)

- **作者**: Chernobyllight
- **时间**: 2026-09-18T09:34:28Z
- **提交信息**: feat(offload): add host/NUMA shared CPU block offload across model families (#1530)

Integrates shared CPU block offload for Hunyuan Image 3.0, MiniMax-H3,
Qwen-Image-2512, and Wan 2.1, with host/NUMA weight sharing, simplified
launchers, CLI scope selection, and bilingual usage guides.

---------

Co-authored-by: liuhongda <liuhongda@sensetime.com>
Co-authored-by: helloyongyang <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2252
- **最后更新**: 2026-09-18T08:40:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6446
- **最后更新**: 2026-09-19T00:00:43Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 8
- **主要提交者**: SeongJun Lee, Haobin Guo, feih-nv

## AI分析总结

# FlashInfer 昨日提交总结

## 主要更新类型

昨日共 9 个提交，涵盖功能新增、性能优化、Bug 修复与文档测试四类。功能新增包括：cuDNN decode 后端扩展、Cake GDN 上下文并行 prefill、因果+双向区间 batch prefill、SM90 CuTe-DSL MoE 后端新增激活类型，以及 CUTLASS FP8 per-tensor runner 兼容 TRT-LLM 静态缩放。性能优化聚焦 CuTe-DSL 窗口化解码跳过非活跃页与 RMSNorm 分块调优。此外修复了 SM107 上 KDA 测试 oracle 缺失问题，并明确了 gated MoE 权重行序契约。

## 关键变更点

- **cuDNN decode 扩展**：支持多 token 验证、滑动窗口与 attention sinks，对齐 Qwen3-Next/GLM-4.5 MTP、gpt-oss 等主流解码模型。
- **Cake GDN 上下文并行 prefill**：以 opt-in 方式引入，默认路由不变，体现渐进式落地策略。
- **因果+双向区间 prefill**：用紧凑 `int32 [total_q, 2]` 张量替代稠密 mask，16384 query 仅 128 KiB，缓解长上下文内存瓶颈。
- **窗口化解码跳页**：K=8192 时延迟降低约 86%，是长上下文推理的关键优化。
- **FP8 静态缩放统一**：`prepare_weights` 新增 global scale 参数，折叠 flat `quant_scales` 推导四个缩放因子，移除动态路径，统一为 TRT-LLM 风格契约。

## 项目影响与意义

本批提交从三个维度推进 FlashInfer 作为高性能推理内核库的定位：**模型覆盖**（MTP、sinks、sliding window）、**场景覆盖**（超长上下文、上下文并行）、**硬件覆盖**（SM100/103/107 调优）。FP8 契约统一使 vLLM/SGLang/TRT-LLM 可复用同一套 CUTLASS MoE 内核，降低集成摩擦；CUDA tensor scale 绕过主机校验，实现 sync-free 且可被 CUDA graph 捕获，对低延迟部署意义重大。整体呈现"扩展能力但保持默认路径稳定"的工程纪律。

## 技术关注点

- cuDNN 的 `diagonal_band_left_bound` 与 FlashInfer 窗口计数存在 off-by-one，需 `window_left + 1` 对齐。
- attention sink 约定为未缩放 fp32 logits，测试用 8e-3 精度钉死。
- 窗口跳页通过"页表原点前移 + 有效序列长度重基"保持因果/窗口掩码、余数、页数三项不变量。
- RMSNorm 调优仅改 tiling（每线程约 32 元素），不改 kernel 体，以显式架构列表门控。
- 双向区间变体设 `window_left = kv_len` 以阻止 FA2 滑窗剪枝误删有效键。
- 缩放折叠数学：`fc1_dequant_scale = fc1_dequant / a1`、`fc2_dequant_scale = fc2_dequant / a2`、`fc1_act_dequant_scale = 1 / a1`，静态乘子吸收进反量化 scale，避免运行时额外计算。

整体而言，FlashInfer 通过统一多后端量化契约、扩展新一代解码模型适配、优化长上下文性能，持续强化其作为多框架共享内核层的价值，契合"高性能 + 易集成"的核心目标。

## 详细提交记录

### [ee89af9](https://github.com/flashinfer-ai/flashinfer/commit/ee89af9b5286ebe94c12a0104c8d0d8ab33a4fc6)

- **作者**: Vedaanta Agarwalla
- **时间**: 2026-09-18T23:45:21Z
- **提交信息**: feat(cudnn): decode backend forwards q_len_per_req > 1, sliding window and attention sinks (#5327)

<!-- .github/pull_request_template.md -->

## 📌 Description

`BatchDecodeWithPagedKVCacheWrapper(backend="cudnn")` (#4625) served
one-token, full-window, sink-free decode only, so the wrapper rejected
exactly the variants the popular decode models need: multi-token
verification rows (Qwen3.5 / Qwen3-Next MTP, GLM-4.5 MTP), a left
sliding window and learned attention sinks (gpt-oss). cuDNN accepts all
three on the same paged SDPA graph; this PR forwards them.

`flashinfer.cudnn.decode.cudnn_batch_decode_with_kv_cache` gains three
keyword arguments:

- **`q_len_per_req`** (default 1): `q` has `batch * q_len_per_req`
consecutive rows per request. The graph sees a `(batch, heads, q_len,
d)` strided view (no copy) and applies the **bottom-right causal
diagonal** (row `i` of a request with `kv_len` keys sees keys `0 ..
kv_len - q_len + i`). `O` / `Stats` are bound token-major, so `out` is
`(rows, heads, d_vo)` and `lse` `(rows, heads)` — the wrapper's shapes.
- **`window_left`** (default -1): FlashInfer counts the keys *before*
the diagonal position (the position itself is always visible); cuDNN's
`diagonal_band_left_bound` counts the diagonal too, so the graph gets
`window_left + 1` under bottom-right alignment. (An off-by-one on either
side shows against fa2 at windows 64 / 128 — tested.)
- **`sinks`** (default None): `(num_heads_qo,)` fp32 logits bound as a
`(1, H, 1, 1)` `sink_token`: one extra softmax column with a zero value
row, **unscaled** — FlashInfer's contract. Probe on B200: cuDNN matches
the torch reference to 8e-3 with the unscaled sink; `sink * scale`,
`sink * log2e`, `sink / log2e` are off by 0.5–2, so the convention is
pinned by test. Whether a stack serves a sink at `q_len_per_req == 1` is
decided by cuDNN's SDPA engines: the backend engine raises a
not-supported error at graph build (test skips with the reason),
cudnn-frontend 1.30+ with the FROST engines enabled serves it (every
sink case passes on that stack, see Tests).

The graph-cache key (`_sdpa_decode_key_fn`) carries `q_len_per_req`,
`window_left` and the sink tensor's layout, so same-shape calls that
differ only in them do not share a graph.

`BatchDecodeWithPagedKVCacheWrapper(backend="cudnn")`: the
`q_len_per_req > 1`, `window_left` and `sinks` rejections are gone; the
generic multi-token checks know the cudnn path (it needs no tensor-core
module) and the cudnn path enforces `q_len_per_req` equal to the planned
value like the fa2 path. `benchmarks/routines/attention.py` no longer
drops the cudnn wrapper backend for `--s_qo > 1` with the causal draft
mask (the standalone `cudnn-native` stays one-row; `--spec_dec_mask`
other than `causal` still skips cudnn, whose graph applies the
bottom-right causal diagonal and takes no draft-block mask) and plans
the wrappers with `q_len_per_req=s_qo`. The `cudnn_batch_decode` trace
template gains the three optional inputs, a reference that honors them,
and a decode-specific `num_q_rows` axis for `q` / `output` (`batch_size
* q_len_per_req` rows) while `block_tables` keeps `batch_size`; the
shared paged axis map is untouched. `docs/api/cudnn.rst` and the wrapper
docstring updated.

**Not changed: `backend="auto"`.** On B200 cuDNN measures 3–4× ahead of
the CUDA-core fa2 kernel `auto` resolves to for a default wrapper (64/8
heads, d128, page 16, 4k KV: 28 vs 96 µs at b=8, 91 vs 369 µs at b=32,
316 vs 1419 µs at b=128) and at parity with fa2 tensor cores (91 vs 94
µs at b=32, 316 vs 438 µs at b=128). It still should not pick cudnn:
`auto` is resolved at `plan()` before `run()` sees `sinks`, and the
backend engine cannot take a sink at `q_len_per_req == 1`, so `auto →
cudnn` would turn gpt-oss-style callers on Blackwell into a hard error
at the first run. That needs a sink-aware plan (or the FROST stack
everywhere) first.

Observation for a follow-up (not fixed here): the plain fa2 tensor-core
decode wrapper accepts `sinks=` at `run()` and silently ignores them
unless the module was built with the `AttentionSink` JIT variant
(`jit_args`) or via `BatchAttentionWithAttentionSinkWrapper` — its
output equals the no-sink result to 8e-3 in the probe. That is why the
sink tests here compare against the torch reference, not fa2.

## 🔍 Related Issues

Follows #4625 (backend="cudnn" for the decode wrapper) and #4626.
cuDNN-side coverage for these decode variants: cudnn-frontend #1094
(d128 decode tile), #1095 (sink at S_q == 1), #1109 (d256 decode tile).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (`ruff@0.12.8 format` / `check` on every
touched Python file: clean.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

`tests/attention/test_cudnn_decode.py` (B200, cuDNN backend 9.26.0.51,
torch 2.14 nightly cu132):

- `test_cudnn_wrapper_mtp_matches_fa2[q_len 2 / 4 × fp16 / bf16 × HND /
NHD]` — output + base-2 LSE vs fa2 tensor-core decode, row for row.
- `test_cudnn_wrapper_sliding_window_matches_fa2[window 64 / 128 × q_len
1 / 2]` — vs fa2.
- `test_cudnn_wrapper_sinks_match_reference[(32/8 d128, 64/8 d64) ×
window -1 / 128 × q_len 1 / 2]` — vs the torch reference (`_decode_ref`
gained `q_len_per_req` / `window_left` / `sinks`, LSE includes the
sink); also asserts the sink changed the output. The 64/8 d64 + window
128 + sink cases are the gpt-oss decode graph.
- `test_cudnn_decode_standalone_q_len_per_req_matches_wrapper` — the
standalone entry point's `(rows, heads, d)` / `(rows, heads)` shapes
equal the wrapper's cudnn result bit-for-bit; a non-multiple row count
raises `ValueError`.
- `test_cudnn_wrapper_rejects_malformed_sinks`,
`test_sdpa_decode_key_fn_discriminates_baked_attributes` (three new
variants), `test_cudnn_wrapper_rejects_unsupported` (soft-cap / RoPE /
fp8 KV stay rejected).
-
`tests/trace/test_fi_trace_template_consistency.py::test_fi_trace_cudnn_batch_decode_multi_token_rows_have_their_own_axis`
— the B=4, `q_len_per_req` 2 schema through the real `fi_trace` entry:
extractors read 8 rows from `q` and 4 from the table, the emitted schema
names `num_q_rows` and `batch_size` separately.

```
pip cudnn-frontend 1.29 (cuDNN backend engine):
  pytest tests/attention/test_cudnn_decode.py -q      -> 67 passed, 4 skipped
     (skips: sink at q_len_per_req == 1, "decode only mode, i.e. s_q == 1, not supported with sink_token")
cudnn-frontend develop @ 43d176a36 + FROST engines enabled (CUDNN_FRONTEND_ENABLE_FROST_ENGINES=1):
  -k "sinks or standalone"                              -> 10 passed, 0 skipped (sink at q_len 1 served)
  -k "sinks or mtp or sliding_window or standalone"     -> 22 passed
pytest tests/trace/test_fi_trace_template_consistency.py -q -> 707 passed, 1 skipped
pytest tests/trace/test_cudnn_batch_decode_reference_correctness.py -q -> 2 passed
mypy@1.17.1 --config-file pyproject.toml (cudnn/decode.py, decode.py, trace/templates/attention.py) -> no issues
```

**Before / after** (`benchmarks/flashinfer_benchmark.py --routine
BatchDecodeWithPagedKVCacheWrapper`, B200, bf16, b=32, KV 4096, page 16,
CUDA graphs; µs, median). Before this PR the cudnn wrapper backend
rejected `--s_qo > 1` (and the benchmark skipped it), so "before" is the
only path that existed: trtllm-gen.

| shape (b=32, KV 4096, page 16, bf16) | `--s_qo` | trtllm-gen (before:
the only path) | fa2_tc | cudnn wrapper, pip stack (cuDNN 9.26 backend
engine) | cudnn wrapper, FROST stack (frontend develop, engines enabled)
|
|---|---|---|---|---|---|
| Qwen3-235B: 64/4 heads, d128 | 1 | 44 | 60 | 48 | 49 |
| | 2 | 45 | skipped by the routine | 993 | 50 |
| | 4 | 46 | skipped by the routine | 993 | 51 |
| Qwen3.5: 32/2 heads, d256 | 1 | 46 | 58 | 88 | 57 |
| | 2 | 47 | skipped by the routine | 1975 | 67 |
| | 4 | 53 | skipped by the routine | 1973 | 68 |

`--refcheck` passed on every row. The backend-engine rows for `s_qo > 1`
are the known cuDNN backend cliff (the paged multi-token graph lands on
a prefill engine, 20x off); the FROST rows are the same FlashInfer code
on cudnn-frontend develop with `CUDNN_FRONTEND_ENABLE_FROST_ENGINES=1`,
where the d128 / d256 decode tiles (cudnn-frontend #1094, #1109) serve
the graph. The benchmark routine's fa2_tc skip for `--s_qo > 1` predates
fa2's multi-token support and is left as is.

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

- The mask spelling is the one cuDNN's frontend documents:
`use_causal_mask_bottom_right=True` pins the right bound to the
diagonal, `diagonal_band_left_bound` masks columns at or before `row_idx
- left_bound`; FlashInfer's `window_left` is therefore `left_bound - 1`.
Plain one-token decode without a window keeps the graph byte-identical
to before (no mask kwargs), so existing cached graphs and CUDA-graph
captures are unaffected.
- `q_len_per_req > 1` on the cuDNN **backend** engine is correct but
slow (it lands on a prefill engine; see the table). The fast path is the
FROST decode tiles in cudnn-frontend develop (#1094 d128, #1109 d256),
which the same graph reaches once that frontend ships and the engines
are enabled — the FROST rows in the table are that stack.
- Diff: 7 files (the stat of the branch against main).

AI-assisted.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* cuDNN batch decoding now supports multi-token queries, including
speculative/MTP decoding.
* Added left sliding-window attention and per-head attention sinks for
supported cuDNN configurations.
* Standalone and wrapper decode paths now provide consistent handling
and validation for these options.

* **Documentation**
* Updated cuDNN capability documentation, including supported features
and compatibility limitations.

* **Tests**
* Added coverage for multi-token decoding, sliding windows, attention
sinks, validation, tracing, and wrapper consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d7bfcab](https://github.com/flashinfer-ai/flashinfer/commit/d7bfcab6091da2e1d98c1b26b46d8e613389c2e1)

- **作者**: eigen
- **时间**: 2026-09-18T22:11:01Z
- **提交信息**: feat(cake_gdn): add opt-in SM100/SM103 context-parallel prefill backend (#5320)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add source-distributed SM100/SM103 context-parallel GDN prefill kernels
with generated CUDA, target-owned launch bindings, and JIT loading
metadata.

Enable Cake CP with `chunk_gated_delta_rule(..., backend="cake_gdn",
use_cp=True)`. The default `backend="auto"` and explicit
`backend="flashinfer"` retain the existing routes. With
`backend="cake_gdn"`, `use_cp=False` or `"auto"` selects Cake non-CP.
Unsupported explicit Cake requests raise an error.

The backend supports FP16/BF16 inputs, FP32/FP16/BF16 state,
variable-length and empty sequences, indexed/in-place state pools,
checkpoints, and Q/K normalization. State-index tests explicitly forward
the selected backend. GPU tests use exact architecture gates and
supported CUDA-version references.

The runtime manifest contains only source inventory, hashes and loading
metadata. Planner tests directly parameterize 120 shapes across
SM100a/SM103a; the historical export snapshot is excluded from the
source tree.

## 🔍 Related Issues

Related implementation: #4539. This PR uses the identical head commit
`c7800f145ade47f809f0306d762fb1fffc962918` on a new branch.

Performance baseline: #4917, fixed revision
`453ce62939f385fe10b3b8f09625f545f9c85e23`.

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

Existing validation, retained at the revisions actually exercised:

- 181 affected GB300 tests passed for the cleanup/opt-in changes, with
affected source files matching
`6d7abd5c47a421d6866252b56e62540d134b34a3` (175 state-index cases and 6
public-dispatch/state-lifecycle cases).
- 242 CPU tests passed at `3a03487eb02ac6b14df1f4b5c64b7222d30b6fd9`:
240 planner cases covering 120 shapes and two architectures, plus source
inventory and manifest loading. Ruff lint/format and exporter projection
checks passed.
- Fresh CI will target `tests/gdn/test_cake_gdn_cp_backend.py`,
`tests/gdn/test_prefill_cp_delta_rule.py`,
`tests/gdn/test_prefill_delta_rule.py`, and
`tests/gdn/test_prefill_state_indices.py`. Results from earlier
revisions are not relabeled as results from this new PR.

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

Performance was measured on GB300 (152 SM), with FP16 inputs and FP32
state, at generated implementation
`8a0e7f847d8b6eca5544f2cbcd5be5e6167919ed`. All 120 shapes beat the
fixed #4917 baseline, including the 28 previously slower shapes.
Geometric-mean speedup is **1.133407×** and the minimum is
**1.004463×**. The new/previous export latency geometric ratio is
**0.943958** across separate runs.

| Shape | #4917 (ms) | Export (ms) | Speedup |
|---|---:|---:|---:|
| `perf_hq16_hv64_1x65536` | 2.066336 | 1.994048 | 1.036252× |
| `perf_hq16_hv64_6144_2048` | 0.323168 | 0.314560 | 1.027365× |
| `perf_hq2_hv8_1024_7168` | 0.097056 | 0.093920 | 1.033390× |
| `perf_hq16_hv48_1024_7168` (minimum) | 0.252064 | 0.250944 | 1.004463×
|

Timing uses cold-L2 CUPTI and symmetric external CUDA Graphs, 100 ms
warmup plus 1000 ms measurement ×3 per arm, with directional/endpoint
drift ≤2%. Outputs and final states pass `atol=rtol=1e-2`. These are
historical measurements at the stated executed SHA; creating this PR
does not constitute a new benchmark run.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added a Blackwell-optimized context-parallel GDN prefill backend for
FP16 and BF16 workloads.
- Added support for state gathering, scattering, fixup, normalization,
checkpointing, and precomputation across supported GPU architectures.
- Added the optional `max_seqlen` parameter to improve context-parallel
launch sizing.
- Added runtime validation, plan caching, CUDA Graph replay support, and
JIT loading for supported kernels.

- **Documentation**
- Added API documentation covering backend selection, supported
hardware, CUDA requirements, data types, and runtime behavior.

- **Benchmarks**
  - Updated benchmarking to pass the maximum segment length explicitly.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Avery Huang <averyh@nvl72d016-T17.cm.cluster>

### [d207165](https://github.com/flashinfer-ai/flashinfer/commit/d207165a34290f6464cd33a233e8fe067b0f4fee)

- **作者**: kzos
- **时间**: 2026-09-18T19:00:55Z
- **提交信息**: perf(cute-dsl): skip inactive pages in windowed decode (#4825)

<!-- .github/pull_request_template.md -->

## 📌 Description

Skip whole paged-KV pages that are entirely before a sliding-window
decode
request's earliest active key. The kernel advances the page-table origin
and
rebases the effective sequence length before constructing page and
sequence
tile counts; the existing mask still handles the retained leading
partial
page.

The rebase preserves three invariants:

1. key and query coordinates shift by the same whole-page token count,
so
   causal and sliding-window mask decisions are unchanged, including
   multi-token decode;
2. the sequence-length remainder modulo page size is unchanged, so
partial
   last-page handling is unchanged;
3. skipped pages plus retained pages equals the original page count, so
fixed
   and ragged page-table segments remain in bounds.

BLASST threshold normalization intentionally continues to use the
original
full sequence length. Dense and causal-without-left-window paths do not
enter
the new branch.

### Performance

Fresh same-GPU results compare parent `231f708` with exact candidate
`117518a` on one NVIDIA B300 SM103. The workload is BF16
B16/Q1/Hq32/Hkv16/D256 with `window_left=1023`. Compilation, allocation,
and
graph capture are outside timing. Each measurement uses 50 warmups and
300
CUDA Graph iterations; cells run A/B/A for three cycles. The parent
median is
over six samples and the candidate median over three.

| Page | K | Parent median (us) | Candidate median (us) | Latency
reduction |
|---:|---:|---:|---:|---:|
| 16 | 1024 | 42.185 | 42.237 | -0.12% |
| 16 | 4096 | 152.694 | 42.585 | 72.11% |
| 16 | 8192 | 304.258 | 42.872 | 85.91% |
| 32 | 1024 | 41.880 | 41.714 | 0.40% |
| 32 | 4096 | 152.613 | 41.899 | 72.55% |
| 32 | 8192 | 305.401 | 42.022 | 86.24% |
| 64 | 1024 | 41.927 | 41.814 | 0.27% |
| 64 | 4096 | 153.293 | 41.639 | 72.84% |
| 64 | 8192 | 306.466 | 41.854 | 86.34% |

K1024 is the no-skip control because the requested window already covers
the
entire sequence; it remains flat. At longer K the candidate remains near
the
cost of the retained window while the parent scans the full sequence.

CLI-equivalent command used by each arm (with `$P` and `$K` expanded per
row):

```bash
python flashinfer/cute_dsl/attention/gqa_decode_paged.py \
  --b 16 --p 1 --s "$K" --pg "$P" --h_q 32 --h_k 16 --d 256 \
  --kv_splits 0 --reduction auto --window_left 1023 --window_right 0 \
  --warmups 50 --iterations 300 --skip_ref_check --quiet
```

The CLI's derived throughput labels use the original full K and are not
reported here after page skipping; only measured latency is compared.

## 🔍 Related Issues

None yet.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Local source checks completed:

- `uvx pre-commit run --all-files`
- `uvx ruff check flashinfer/cute_dsl/attention/gqa_decode_paged.py
tests/attention/test_cute_dsl_decode.py`
- `uvx ruff format --check
flashinfer/cute_dsl/attention/gqa_decode_paged.py
tests/attention/test_cute_dsl_decode.py`
- `python3 -m py_compile
flashinfer/cute_dsl/attention/gqa_decode_paged.py
tests/attention/test_cute_dsl_decode.py`
- `git diff --check`

B300 checks completed for exact candidate `117518a`:

- 10 focused tests passed: Q1/Q4, page sizes 8/16/32/64, ragged split-K,
split early-exit, CUDA Graph replay with growing lengths, and the BLASST
  full-length-normalization discriminator;
- the direct fixed-length B2/Q4/K2051/page16/split-K3 CLI path passed
its
  numerical reference;
- the exact D256 benchmark geometry passed numerical reference checks at
page
  sizes 16, 32, and 64;
- Compute Sanitizer 2025.3.1 memcheck reported zero errors for a ragged
  page16/split-K3 early-exit cell;
- the reproducible parent/candidate latency matrix above completed.

Follow-up review fix `eebdefb` strengthens the BLASST test with a
third-tile
score delta that lies between the full-length and rebased-length
thresholds and
distinct nonzero values on that tile. On the same B300, the exact
follow-up head
passed the full focused matrix: `10 passed, 178 deselected`. The
source-side
change in that commit only makes the existing sliding-window subtype
narrowing
explicit for mypy; the page-rebase calculation is unchanged. The
performance
table remains the A/B/A measurement of `117518a` reported above.

## Reviewer Notes

Please focus on the page-table-origin/sequence-coordinate invariant and
the
choice to retain full-sequence BLASST normalization. The change was
independently reviewed by Kimi K3 Max; its initial test-strength finding
was
addressed before commit. AI assistance was used to review and prepare
this
change; the human submitter has reviewed the final diff and is
responsible for
the design and results.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved paged sliding-window decoding to preserve partially active
pages and ensure correct attention results at window boundaries.
* Fixed sequence-length handling when runtime lengths change, including
CUDA Graph replay scenarios.
* Corrected threshold normalization to consistently use the full
sequence length.
* Improved numerical correctness for split-K decoding and kernel-based
reduction paths across supported configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Zaheer Sheriff K <zaheersheriff.k@gmail.com>

### [012542c](https://github.com/flashinfer-ai/flashinfer/commit/012542c8523b7e0034fb24a65f0599c6f60b56ff)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-18T17:09:28Z
- **提交信息**: perf(norm): tune CuTe-DSL qk_rmsnorm and fused_add_rmsnorm_quant tiling for SM100/103/107 (#5305)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Two tiling adjustments to the CuTe-DSL norm kernels on Blackwell and
Rubin (SM100, SM103, SM107), gated on an explicit architecture list
(`_LATENCY_BOUND_SMS`) so all other architectures are unchanged. No
kernel body, layout, or math changes.
  
**`qk_rmsnorm`: fewer threads per row for small head_dim.** The kernel
reused the RMSNorm threads-per-row table, which for head_dim ≤ 256
leaves every thread with a single 16-byte vector. With at most 2048
resident threads per SM that is only 32 KB in flight per SM, and the
kernel is latency-bound at large M. On the listed architectures each
thread now owns ~32 elements (4/4/8 threads per row for head_dim
64/128/256 instead of 8/16/32). Adding threads per CTA instead was
measured to be monotonically worse. `QKRMSNormKernel` now takes
`sm_version`, which is part of the compile-cache key like the other norm
kernels.
  
**`fused_add_rmsnorm_quant`: no 256-thread bump for H > 8192.** The
two-rows-per-CTA rule doubles the two shared-memory tiles and halves
resident CTAs. On the listed architectures the kernel keeps 128 threads
and one row per CTA. Output is bit-identical.
### Performance (cold L2, bf16, CUDA-event timing, same-process A/B,
before → after)
Cold L2, bf16, same-process A/B, before → after. Primary numbers use the
library-default PDL setting (on); PDL-off is
 shown where measured.
  
**`qk_rmsnorm`, 32 heads, SM107, PDL on**
| head_dim | M=512 | M=8192 | M=32768 |
|---|---|---|---|
| 64 | 1.00× | 1.41× | 1.70× |
| 128 | 1.09× | 1.75× | 2.13× |
| 256 | 1.18× | 1.93× | 2.10× |
With PDL off on SM107: 1.35× / 1.70× / 1.65× at M=32768, neutral at M ≤
128.
**`qk_rmsnorm`, 32 heads, B200 (SM100), PDL off**
| head_dim | M=2048 | M=8192 | M=32768 | M ≤ 512 |
|---|---|---|---|---|
| 64 | 1.00× | 1.13× | 1.16× | 0.98–1.01× |
| 128 | 1.00× | 1.14× | 1.20× | 0.98–1.00× |
  | 256 | 1.13× | 1.32× | 1.36× | 1.00× |   

  Geomean 1.07× over all 18 cells, 1.15× for M ≥ 2048.

  **`fused_add_rmsnorm_quant`, M=32768**
  
  | GPU | PDL | H=12288 | H=14336 | H=16384 |
  |---|---|---|---|---|
  | SM107 | on | 1.07× | 1.10× | 0.98× |
  | SM107 | off | 1.08× | 1.11× | 0.99× |

  
H ≤ 8192 produces an identical kernel configuration and is unaffected.
Cells at or below the launch floor (M ≤ 128)
  are within timer resolution on both GPUs.
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

* **Performance Improvements**
* Improved RMS normalization and fused add-normalization quantization
performance on supported GPU architectures through adaptive thread
allocation.
  * Added architecture-aware workload sizing for latency-sensitive GPUs.
* Optimized processing for large feature dimensions to improve
throughput across GPU configurations.
* Preserved efficient execution on latency-bound hardware while applying
additional parallelism where beneficial.
* Improved consistency of normalization performance across supported
devices.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1eccf6f](https://github.com/flashinfer-ai/flashinfer/commit/1eccf6f0bc7d5e5626c6b294c533c6847aa25046)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-09-18T17:00:18Z
- **提交信息**: fix(tests): skip cuDNN KDA kernel-oracle arm where the oracle has no SM107 (#5298)

## 📌 Description

On the Rubin (VR200 / SM107) lane, all 12 parametrizations of

`tests/kda/test_recurrent_kda_cudnn_backend.py::test_cudnn_backend_matches_default`
fail:

```
E   ValueError: backend='cute-dsl' does not support this recurrent_kda prefill contract
E   ValueError: backend='cake'     does not support this recurrent_kda prefill contract
```

The cuDNN backend under test is fine there. The failure is in the test's
**oracle** — the same
shape as #5246, one exception type further out.

This test compares cuDNN against FlashInfer's own recurrent KDA prefill
backends, parametrized over
both of them, and both are gated to compute capability `{(10, 0), (10,
3)}`:

| | gate | value |
|---|---|---|
| cute-dsl prefill | `flashinfer/kda_prefill_cute.py:34` |
`_SUPPORTED_COMPUTE_CAPABILITIES = {(10, 0), (10, 3)}` |
| Cake prefill | `flashinfer/kda_prefill.py:59` |
`_FLASH_KDA_SUPPORTED_COMPUTE_CAPABILITIES = {(10, 0), (10, 3)}` |
| cuDNN engines (module gate) |
`tests/test_helpers/cudnn_linear_attention.py:39` | `{(10, 0), (10, 1),
(10, 2), (10, 3), (10, 7)}` |

cuDNN serves five capabilities, the oracles two. On the three in
between, the module runs and the
oracle cannot. Because the test names a backend explicitly rather than
using `"auto"`, the
dispatcher refuses instead of falling back (`flashinfer/kda.py:553` for
cute-dsl, `:662` for Cake),
so the reference call raises before cuDNN is reached. 12 = 2 oracles × 2
`use_initial_state` × 3
`seq_lens`, each failing in under a second, host-side.

### Why #5246's guard does not catch it

#5246 routed this very call through the shared
`reference_kernel_or_skip` helper, which catches
`ImportError` and `NotImplementedError` — the two ways a backend reports
*unavailable* (DSL too old,
backend missing, GDN prefill needing CUDA 13+). A backend that is merely
**architecture-ineligible**
reports it as a `ValueError`, which escapes the helper.

Widening the helper to catch `ValueError` would be wrong: the same
exception is how a real contract
regression would surface on B200, and swallowing it would turn a genuine
failure into a silent skip.
So this gates on the capability instead, reading the supported sets from
the product modules rather
than restating them, so the skip follows automatically if SM107 support
lands.

### The other cuDNN linear-attention tests

Four test files use the cuDNN linear-attention helper; only two ever use
an in-tree kernel as an
oracle, and they are exactly the two `reference_kernel_or_skip` call
sites:

| File | In-tree oracle | Exposure |
|---|---|---|
| `tests/kda/test_recurrent_kda_cudnn_backend.py` |
`recurrent_kda(backend="cute-dsl"/"cake")` | **this PR** |
| `tests/gdn/test_prefill_cudnn_backend.py` | `chunk_gated_delta_rule`
(default backend) | not arch-gated this way; passes the SM107 dispatch
check (`_arch_major in (9, 10, 12)`) and does not fail on the Rubin
nightly |
| `tests/gdn2/test_prefill_gdn2_cudnn_backend.py` | none | FlashInfer
has no GDN-2 kernel — `auto` and `cudnn` are one path, and the
cross-family GDN comparison passes `backend="cudnn"` |
| `tests/gdp/test_prefill_gdp_cudnn_backend.py` | none | same: no GDP
kernel, cross-family comparison is `backend="cudnn"` |

`tests/mamba/` has no cuDNN coverage at all — it never imports the
frontend — so there is nothing to
audit there.

The Rubin nightly agrees: pipeline #68147175 on VR200 / CUDA 13.4
reports
`tests/kda/test_recurrent_kda_cudnn_backend.py (12 failed nodes)` and no
GDN, GDN-2 or GDP cuDNN
file in the failed set.

## 🧪 Tests

This box is B200 / CUDA 13.0 with cudnn-frontend 1.27 < the required
1.29, so the module gate skips
the file wholesale here (59 skipped), exactly as in #5246. The new
branch was therefore driven
directly, with only the two host-side facts the module gate reads faked:

- Gate forced open, capability faked to `(10, 7)`: **12 failed → 12
skipped**, reporting
`reference backend cute-dsl does not support sm107` / `... cake does not
support sm107`.
- Gate forced open, real `(10, 0)`: the skip does **not** fire, so
supported hardware is unaffected.
- Unfaked: 59 skipped, unchanged from `main`.
- `pre-commit run --files tests/kda/test_recurrent_kda_cudnn_backend.py`
→ clean.

Please run CI to confirm the Rubin column: `/bot run tests/kda tests/gdn
tests/gdn2 tests/gdp`

## 🔍 Related Issues

Sibling of #5246. The Rubin failure was surfaced by the VR200 lane on
#5253.

## Note, out of scope

Whether the cute-dsl and Cake KDA prefill backends should support SM107
at all is a kernel-coverage
question, not a test fix, and is left alone here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated cuDNN backend comparisons to run only on GPUs supported by the
selected reference backend.
* Tests now skip unsupported compute capabilities instead of producing
invalid comparison results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0104536](https://github.com/flashinfer-ai/flashinfer/commit/01045366e15df38e19e76050592f82e49b4cff64)

- **作者**: Haobin Guo
- **时间**: 2026-09-18T13:45:25Z
- **提交信息**: feat(moe): add more activation types to the SM90 CuTe-DSL MoE backend (#5295)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds more activation types to the SM90 CuTe-DSL BF16/FP16 MoE backend:
- gated SwiGLU (default), including the parameterized form via
`swiglu_alpha` / `swiglu_beta` / `swiglu_limit` (gate clamped from
above, up clamped to `[-limit, limit]`, `gate * sigmoid(alpha * gate) *
(up + beta)`) and SiTU via `situ_beta` / `situ_linear_beta`
- gated GeGLU-tanh (`ActivationType.GegluTanh`)
- non-gated ReLU² (`ActivationType.Relu2`; `w1` is a plain `[E, I,
hidden]` projection, `I % 64 == 0`)

## 🔍 Related Issues

Follow-up to #4878.

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



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for SwiGLU, SiTU, GeGLU-tanh, and non-gated ReLU²
activations in BF16/FP16 fused MoE workflows.
* Added configurable activation parameters and gated or non-gated weight
layouts.
* Added activation validation and expanded Hopper benchmark coverage
across additional model shapes.

* **Documentation**
* Documented the BF16 wrapper, activation options, supported shapes,
tracing support, and benchmark coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Haobin Guo <haobing@nvidia.com>

### [2269b3a](https://github.com/flashinfer-ai/flashinfer/commit/2269b3add6f3be44dccf5590f62a2fed9be464b4)

- **作者**: feih-nv
- **时间**: 2026-09-18T10:59:51Z
- **提交信息**: docs(moe): state the canonical [up, gate] row order of the gated GEMM1 weight (w13) (#5291)

<!-- .github/pull_request_template.md -->

## 📌 Description

Every unified `prepare_weights` already takes gated `w1` as `[E, 2I, H]`
with rows `[up, gate]`, but the contract lived only in per-backend
docstrings, and random-weight conformance cannot tell a swapped kernel
from a reference that shares the same swap.

- State the order once on `MoEWeightPack` and in the design doc.
- `test_bf16_gate_up_row_order_is_up_then_gate`: one pack with
asymmetric `[up, gate]` halves. First checks the `[up, gate]` and
`[gate, up]` dense references disagree on the same inputs (so the
fixture can tell the two readings apart), then requires every available
BF16 runner (TRT-LLM and CUTLASS on SM100) to match the `[up, gate]`
reference.

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

On SM100 (B200): `tests/moe/test_unified_moe.py -k "gate_up_row_order or
_bf16"` — pass.

## Reviewer Notes

None.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Documented the canonical gated MoE weight layout and `[up, gate]` row
ordering expected across backends.
* Clarified that backends requiring `[gate, up]` ordering perform the
conversion during weight preparation.

* **Tests**
* Added BF16 coverage for TRT-LLM and CUTLASS to verify consistent
gated-weight interpretation.
* Strengthened asymmetric row-order checks to detect backend and
reference ordering mismatches.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [0e4c173](https://github.com/flashinfer-ai/flashinfer/commit/0e4c173821a0aca29e9eb00c50c3bde8696e6dc6)

- **作者**: SeongJun Lee
- **时间**: 2026-09-18T08:22:59Z
- **提交信息**: feat(attention): add causal + bidirectional-ranges batch prefill (#5189)

<!-- .github/pull_request_template.md -->

## 📌 Description

FA2 supports custom attention variants, but there is currently no
packaged batch-prefill path for sequences that are causal except for
spans that attend in both directions. Callers either have to materialize
a dense custom mask or use a different backend.

The dense mask is `O(qo_len * kv_len)`. For example, 16384 scheduled
query tokens against a 262144-token context require 4 GiB just for a
boolean mask.

This PR adds an FA2 paged-prefill wrapper that computes the mask
directly from a compact `int32 [total_q, 2]` range tensor:

```text
(causal AND causal_window) OR (in_range AND range_window)
```

Each query row contains an inclusive `[start, end]` span in
request-local KV positions. `(-1, -1)` means that the query has no
bidirectional span and remains purely causal. At 16384 query tokens,
this tensor is 128 KiB regardless of context length.

The implementation uses the existing `variant_owns_mask` path in
`BatchPrefillWithPagedKVCacheWrapper`; it does not change the default
prefill dispatch.

The public API added here is:

| Symbol | Exported from |
|---|---|
| `BatchPrefillWithCausalBidirectionalRangesWrapper` | `flashinfer`,
`flashinfer.attention` |
| `gen_batch_prefill_bidirectional_ranges_module` |
`flashinfer.jit.attention` |

The wrapper and generator share one internal spec for the URI and JIT
tensor and scalar arguments.

Two kernel details are worth calling out:

- The variant sets `window_left = kv_len` to keep FA2's normal
sliding-window tile pruning from discarding keys that may still belong
to a bidirectional range. The causal and range windows are applied
inside the variant instead.
- Padded `CTA_TILE_Q` lanes are clamped to the last real query row
before indexing the range tensor.

The wrapper is FA2-only because this path relies on a custom
`LogitsMask` being evaluated for every KV tile. Its JIT specialization
is fixed in the constructor; `plan()` and `workspace_size()` inherit
omitted dtype values from that specialization and reject explicit
mismatches. Options that conflict with the variant-owned mask are
rejected rather than silently ignored.

Packed NVFP4 KV caches use the existing `maybe_k_cache_sf` and
`maybe_v_cache_sf` JIT tensor conventions.

## 🔍 Related Issues

None.

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

```bash
pytest tests/attention/test_bidirectional_ranges_attention.py
# 39 passed, 2 warnings, on one SM80 device
```

The targeted tests cover:

- dense-reference correctness with multiple requests, GQA and shuffled
page IDs;
- independent causal-window and bidirectional-range behavior;
- partial query tiles and padded lanes;
- packed NVFP4 KV, separate output dtype and non-unit Q/K/V scales;
- CUDA graph replay while updating the same range buffer;
- constructor/plan specialization mismatches and unsupported mask
options.

Pre-commit hooks for the changed files also pass.

## Reviewer Notes

This is currently JIT-only. Unlike the existing attention-sink AOT
entry, it does not have a small fixed set of dtype and head-dimension
combinations to precompile.

Testing was limited to SM80. I did not run this on SM90 or SM100, and
the FP8 paths were not exercised.

This wrapper is separate from `prefix_len_ptr`, which selects
`MaskMode.MULTIITEMSCORING`; the two mask modes cannot be combined.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added bidirectional range attention for batch prefill, combining
causal masking with per-query key spans.
  - Exposed the new attention wrapper through the public API.
  - Added support for NVFP4 key-value caches and log-sum-exp results.
- Added validation for range inputs, attention settings, data types, and
configuration compatibility.
- Added tensor-valued query, key, and value scaling support for paged
prefill.

- **Documentation**
  - Documented causal and bidirectional ranges prefill functionality.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>

### [dd13d70](https://github.com/flashinfer-ai/flashinfer/commit/dd13d705d7a76138d30b525d3996c0d59c21e4d9)

- **作者**: feih-nv
- **时间**: 2026-09-18T07:43:18Z
- **提交信息**: feat(moe): CUTLASS FP8 per-tensor runner takes the TRT-LLM static-scale activation pack (#5294)

<!-- .github/pull_request_template.md -->

## 📌 Description

`(TrtllmFp8PerTensorConfig(), CutlassFp8PerTensorConfig())` could not
share one `MoEActivationPack`: TRT-LLM keeps a static calibration
multiplier in its weight view and carries no pack scale; the unified
CUTLASS runner expected a dynamic (per-call, amax-derived) 0-dim dequant
scale on the pack. vLLM / SGLang feed static scales to the flat CUTLASS
FP8 path, so CUTLASS now speaks the static contract.

- `CutlassFp8PerTensorConfig.prepare_weights(...,
hidden_states_scale_global=, intermediate_scale_global=)` takes the
TRT-LLM static multipliers (`q = x * scale`) and folds the flat
`quant_scales` at load time: `fc1_dequant_scale = fc1_dequant / a1`,
`fc2_act_quant_scale = a2`, `fc2_dequant_scale = fc2_dequant / a2`,
`fc1_act_dequant_scale = 1 / a1`. `fc1_dequant` / `fc2_dequant` and the
two globals stay in the view as metadata.
- `CutlassFp8PerTensorRunner` validates and passes the four through.
GEMM2 input is requantized with the calibrated intermediate scale (was
an implicit 1.0); `hidden_states_scale` must be `None`.
- `prepare_activations` is the TRT-LLM helper;
`prepare_cutlass_fp8_per_tensor_activations` (dynamic scale) is removed.
A CUDA-tensor scale skips host-side validation, so the per-step path is
sync-free and graph-capturable.

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

Coverage added / changed in `tests/moe/test_unified_moe_cutlass.py`
unless noted:

- Reference models the static intermediate requantization, on fp32
dequantized operands.
- Folded view scales are checked against the calibration metadata;
`cutlass_fp8_per_tensor` is back in `test_scale_orders_match_flat_abi`.
- TRT-LLM + CUTLASS mixed-candidate test on one pack, SwiGLU and ReLU2.
- `prepare_activations` under CUDA graph capture with a CUDA-tensor
scale.
- Fuzz handler (`test_unified_moe_fuzz.py`) moves onto the TRT-LLM
per-tensor pack; FP8 per-tensor helpers shared via `tests/moe/utils.py`.

On SM100 (B200): `tests/moe/test_unified_moe_cutlass.py -k
"fp8_per_tensor or scale_orders"`, `tests/moe/test_unified_moe_fuzz.py
-k fp8_per_tensor`, `tests/moe/test_unified_moe_fp8.py -k per_tensor` —
pass.

## Reviewer Notes

- User-visible: `prepare_weights` / `prepare_activations` gained
required scale kwargs; view keys: `fc1_dequant` / `fc2_dequant`
unchanged, four `*_scale` keys new; FP8 numerics change (intermediate
requantization).
- Dynamic per-tensor activation quantization is no longer a runner mode:
a per-step scale means `prepare_weights` per step (requantizes weights
too; a re-fold helper can follow if needed).
- `TrtllmFp8PerTensorConfig.prepare_activations` shares the helper: a
CUDA-tensor scale is no longer checked for finite / positive
(`prepare_weights` validated it); Python float / CPU scales are still
checked, with two host syncs.
- Design doc: FP8 details sit in the "First-class prep" bullet for now;
whichever of #5230 / #5294 merges second moves them into #5230's
canonical-pack section and shortens the bullet.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Enhancements**
* CUTLASS FP8 per-tensor MoE processing now follows the TRT-LLM static
calibration-scale contract.
* Weight preparation accepts calibration scales and folds them into the
required quantization scales.
* Activation preparation shares the TRT-LLM activation format without
per-call activation scales.
* GEMM2 inputs use the calibrated intermediate scale for consistent
requantization.
  * Calibration and scale layouts are validated during preparation.

* **Documentation**
* Updated API and design documentation for static scales and activation
packing.

* **Tests**
* Expanded coverage for validation, recalibration, backend
compatibility, graph capture, and numerical correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4471
- **最后更新**: 2026-09-18T13:43:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: primorLee

## AI分析总结

## FastVideo 昨日提交分析（第 1/1 批）

### 1. 主要更新类型
- **Bug 修复**：本次提交为单一 bugfix（#1737），标题为“Restore exact Qwen3-VL vision interpolation”，即恢复 Qwen3-VL 视觉插值的精确行为。
- 属于回归修复性质，而非新功能或性能优化。

### 2. 关键变更点及与项目方向的关系
- 核心是修正 Qwen3-VL 视觉编码器中图像/视频帧的插值（interpolation）逻辑，使其恢复到预期的精确实现。
- FastVideo 作为面向视频生成的高速推理框架，依赖多模态视觉语言模型（如 Qwen3-VL）进行条件编码。视觉插值的精确性直接影响条件特征的数值一致性。
- 该修复契合项目“高质量、可复现视频生成”的整体方向，确保模型输入预处理环节不引入偏差。

### 3. 对项目的影响和潜在意义
- 修复后，使用 Qwen3-VL 作为文本/视觉编码器的推理流程可避免因插值偏差导致的生成质量下降或结果不一致。
- 对依赖精确数值复现的用户（如对比实验、论文复现）尤为重要，减少“结果对不上”的排查成本。
- 属于稳定性维护，虽不扩展功能，但保障了既有 pipeline 的可靠性。

### 4. 值得关注的技术点
- **插值方式**：视觉插值（如 bilinear/bicubic/nearest 或 resize 对齐方式）在 VLM 预处理中常被忽视，但会显著影响 patch 特征。
- **精确性恢复**：说明此前某次改动无意改变了插值行为，本次回退/修正到“exact”实现，提示项目对数值一致性的重视。
- 由两位贡献者协作完成，反映社区对多模态编码器细节的关注。

### 5. 基于 README 背景的项目发展影响
- FastVideo 强调快速推理与易用性（Quick Start、Cookbook），此类 bugfix 保证新用户按文档运行时能获得预期效果，降低上手门槛。
- 项目设有每周开发会议与活跃讨论，说明处于快速迭代期；及时的回归修复有助于维持主干稳定性，支撑后续功能（如新模型支持、加速优化）的可靠叠加。
- 总体看，该提交是维护性的一小步，但对多模态视频生成链路的正确性有实际价值，符合项目追求高质量生成与可复现性的定位。

## 详细提交记录

### [430e521](https://github.com/hao-ai-lab/FastVideo/commit/430e52154e76b902c3cc17a16b3edc1fad790012)

- **作者**: primorLee
- **时间**: 2026-09-18T12:00:05Z
- **提交信息**: [bugfix]: Restore exact Qwen3-VL vision interpolation (#1737)

Co-authored-by: William Lin <8941107+SolitaryThinker@users.noreply.github.com>
Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34543
- **最后更新**: 2026-09-18T20:00:04Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: jiqing-feng, Wang, Yi

## AI分析总结

# diffusers 昨日提交分析（第 1/1 批，共 2 条）

## 1. 主要更新类型
- **Bug 修复（核心）**：修复磁盘 offload 路径下的内存同步缺陷，解决输出 NaN 问题。
- **测试增强**：扩展 CLI 命令测试与 DreamLite 流水线集成测试覆盖。
- 整体属于**稳定性修复 + 测试加固**，无新功能或文档变更。

## 2. 关键变更点及与项目方向的关系
- `_offload_to_disk` 在释放已加载张量前**同步计算流（compute stream）**，与 `_offload_to_memory` 行为对齐。这是对 group offloading 机制的一致性修补。
- 扩展 `test_group_offload_arg` 及 DreamLite 移动端/常规流水线集成测试，强化回归防护。
- 与 diffusers 持续优化**大模型显存受限场景**（CPU/磁盘 offload）的方向一致，保障低显存推理的正确性。

## 3. 对项目的影响和潜在意义
- 直接消除磁盘 offload 场景下因内存复用导致的**静默数据损坏（NaN）**，提升低显存用户推理可靠性。
- 测试覆盖扩展降低未来回归风险，尤其针对 Intel 等贡献方关注的 offload 与移动端流水线。
- 属于“小而关键”的修复，对依赖 offload 做长序列/视频生成的用户意义重大。

## 4. 值得关注的技术点
- **异步计算流与内存分配器的竞态**：释放张量时内核可能仍在读取，需显式同步。
- **两条 offload 路径（内存 vs 磁盘）行为不一致**是缺陷根源，提示需统一抽象。
- 复现用例指向 VidTok 自编码器的 group offloading 测试，说明该机制在视频模型中被实际使用。

## 5. 基于 README 背景的项目发展影响
diffusers 定位为面向扩散模型的模块化工具箱，强调易用与高效推理。本次修复保障了 offload 这一**降低显存门槛的关键能力**在磁盘路径上同样正确，契合项目让大模型在消费级硬件上可运行的目标；配套测试扩展则巩固了 CLI 与流水线集成的稳定性，为后续更多 offload 相关特性奠定可信基础。

## 详细提交记录

### [a3e0b8e](https://github.com/huggingface/diffusers/commit/a3e0b8ec235c27a6c17a21976daf7fd32d819d05)

- **作者**: jiqing-feng
- **时间**: 2026-09-18T12:06:16Z
- **提交信息**: Synchronize the compute stream before offloading to disk (#14657)

`_offload_to_disk` releases the onloaded tensors at the end, returning their device memory to the allocator while the compute stream may still be reading them. The memory is then reused by the next onload, so the in-flight kernel reads foreign data and the output becomes NaN. `_offload_to_memory` already synchronizes for this reason, do the same on the disk path.

Reproducer: tests/models/autoencoders/test_models_autoencoder_vidtok.py::TestAutoencoderVidTokMemory::test_group_offloading_with_disk[leaf_level-False]

### [7a4e1e3](https://github.com/huggingface/diffusers/commit/7a4e1e3c5fab95141911c955eb3516562c2d3473)

- **作者**: Wang, Yi
- **时间**: 2026-09-18T11:22:41Z
- **提交信息**: extend tests/others/test_cli_commands.py::TestRunCommand::test_group_… (#14697)

extend tests/others/test_cli_commands.py::TestRunCommand::test_group_offload_arg
tests/pipelines/dreamlite/test_pipeline_dreamlite_mobile.py::TestDreamLiteMobilePipelineIntegration
tests/pipelines/dreamlite/test_pipeline_dreamlite.py::TestDreamLitePipelineIntegration

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
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


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13136
- **最后更新**: 2026-09-18T21:18:13Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36152
- **最后更新**: 2026-09-19T00:09:37Z

## 提交统计

- **昨日提交总数**: 42
- **提交者数量**: 24
- **主要提交者**: Ke Bao, Kangyan-Zhou, Shuwen Wang

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

昨日 42 个提交覆盖面很广，以**性能优化**和**Bug 修复**为主，辅以**功能新增**、**文档更新**和**测试/CI 建设**：

- **性能优化**：SWA 页查找融合、Triton 投机验证、EP+MoE-TP 通信合并、NPU 内核融合、FlashInfer MXFP8 GEMM 等。
- **Bug 修复**：Mistral 分词器聊天提示损坏、Mistral3 视觉层冗余、MoE top-1 路由缩放、ROCm 导入遮蔽、HiCache 边界问题等。
- **功能新增**：外部模型配置注册、agentic rollout 模拟器、插件 prefill 共享读能力、SM100 NVFP4 KV 缓存等。
- **测试/CI**：新增 CI 审计技能目录、统一内存重跑测试组、CI 权限更新。
- **文档**：HiCache 传输参数、diffusion CFG 与 tracing 文档同步。

## 2. 关键变更点与项目方向

- **多模态（MM）持续深化**：占位符 ID 异步拷贝到 CUDA、纯文本请求跳过 VMM 错误收集，体现对多模态推理路径的精细化优化。
- **HiCache/PD 分离架构演进**：乐观 prefill、buffer-only L3 写透、prefetch 重试抑制等，说明项目在分层 KV 缓存与预填充-解码分离方向持续投入。
- **Router 重构（1/3、2/3、3/3 系列）**：统一请求日志、区分背压与熔断故障、按链根分片 KV 树，显示路由层正被系统性重构以提升可观测性与稳定性。
- **量化与硬件适配**：MXFP8、NVFP4、NPU arch35、ROCm、AMD MI355X 等多后端支持，契合 SGLang 作为高性能多硬件推理引擎的定位。
- **DSV4/DSV4.1 集成**：剩余模型与运行时集成、TileLang JIT 缓存修复，表明新模型支持正在收尾。

## 3. 对项目的影响与潜在意义

- 性能类提交直接提升吞吐与显存效率，对大规模部署意义重大。
- Router 系列重构与 HiCache 修复增强系统鲁棒性，减少线上故障。
- 多硬件后端扩展（NPU/ROCm/AMD）扩大项目适用面，降低厂商锁定。
- 测试与 CI 建设提升回归防护能力，支撑快速迭代。

## 4. 值得关注的技术点

- **异步占位符拷贝**与**图池内存借用**：体现对 CUDA 内存与图执行的深度优化。
- **FlashInfer 融合 finalize 默认关闭**：以数值精度优先，反映工程权衡。
- **外部模型配置注册机制**：为生态扩展提供接口。
- **Agentic rollout 模拟器**：面向智能体场景的基准工具，预示新应用方向。

## 5. 结合项目背景的发展影响

SGLang 定位为面向大模型与多模态的高性能服务框架。昨日提交延续其核心路线：**在保持多硬件、多模型兼容的同时，持续压榨推理性能并强化系统稳定性**。Router 与 HiCache 的系统性重构，加上多模态与量化后端的扩展，表明项目正从"能用"向"大规模生产可用"演进，为社区提供更可靠、更高效的推理基础设施。

## 详细提交记录

### [b876213](https://github.com/sgl-project/sglang/commit/b876213548f1c1cb3c47e07f64bfebf4d34f8470)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-18T23:35:49Z
- **提交信息**: [Test] Add a ci-test-audit skill cataloging CI and test audit patterns (#40257)

### [21e6c98](https://github.com/sgl-project/sglang/commit/21e6c98ccbb3d85e716e7639786e7f6135c6d86c)

- **作者**: Alison Shao
- **时间**: 2026-09-18T23:12:06Z
- **提交信息**: Fix corrupted chat prompts on mistral_common tokenizers (tool_choice auto never fires) (#39773)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [2394b23](https://github.com/sgl-project/sglang/commit/2394b231c226a91901bbf1912d5aefa6c61f9eec)

- **作者**: Alison Shao
- **时间**: 2026-09-18T23:11:54Z
- **提交信息**: Fix Mistral3 retaining every vision-tower layer to read one (#39185)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [fa521e2](https://github.com/sgl-project/sglang/commit/fa521e2758b5c9049e87d8ffe6f9246a882101b4)

- **作者**: metamergebot
- **时间**: 2026-09-18T23:10:37Z
- **提交信息**: [MM] Copy placeholder ids to CUDA asynchronously (#40010)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [ceb1d2e](https://github.com/sgl-project/sglang/commit/ceb1d2e580dd3dda5d6c9a481fe5b15afedd3f82)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-18T23:04:15Z
- **提交信息**: [PD] Enable optimistic prefill with buffer-only L3 write-through HiCache (#40043)

Co-authored-by: cctry <csycfl@gmail.com>

### [5e4b94b](https://github.com/sgl-project/sglang/commit/5e4b94b134e4dcc9a10fac465f94cdf576268646)

- **作者**: metamergebot
- **时间**: 2026-09-18T23:00:43Z
- **提交信息**: [MM] Skip VMM error gathers for text-only requests (#40005)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [803f0c9](https://github.com/sgl-project/sglang/commit/803f0c93d20104cf19ff6a95f7ef580b9fe449a2)

- **作者**: hunhokim
- **时间**: 2026-09-18T22:54:45Z
- **提交信息**: Fix DSA partial DP-TP mode log to use derived attn_tp_size (#39871)

Co-authored-by: Hun-ho Kim <hunho.kim@samsung.com>

### [f385148](https://github.com/sgl-project/sglang/commit/f3851486cbc5155df62551f0aba3ac702f0d137e)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-18T22:51:07Z
- **提交信息**: [Perf] Fuse SWA page lookup and mapping clear (#38948)

### [81a199f](https://github.com/sgl-project/sglang/commit/81a199f56ada4d5b26928aa807ad1aabd89c0d0f)

- **作者**: metamergebot
- **时间**: 2026-09-18T22:47:56Z
- **提交信息**: [HiCache] Read the in-flight buffer backup's node id from its snapshot in sanity_check (#40013)

Co-authored-by: Pranjal Shankhdhar <pranjalssh@meta.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>

### [0e5347d](https://github.com/sgl-project/sglang/commit/0e5347db8282deacbf10b4447c6c3f788d4f6289)

- **作者**: metamergebot
- **时间**: 2026-09-18T22:40:38Z
- **提交信息**: Support MXFP8 and deferred route weighting in DeepEP v2 (#40030)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Xingyu Liu <38244988+charlotte12l@users.noreply.github.com>
Co-authored-by: pranjalssh <14260275+pranjalssh@users.noreply.github.com>

### [6cc9090](https://github.com/sgl-project/sglang/commit/6cc9090d1f903b1aa54f4e116081a1cc77454d96)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-18T22:37:52Z
- **提交信息**: [mem_cache] Release up to `owned_kv_len` on radix cache insert (#40075)

### [a0534f8](https://github.com/sgl-project/sglang/commit/a0534f8cca44779f94be6da9e1bfd50915d2789d)

- **作者**: Zhiqiang Xie
- **时间**: 2026-09-18T22:33:58Z
- **提交信息**: [HiCache] Stop arming a prefetch retry for a too-short storage span (#40042)

### [d346b21](https://github.com/sgl-project/sglang/commit/d346b214fb642b8dbca8cb771f0312965458e7b0)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-09-18T21:50:46Z
- **提交信息**: feat(kv-cache): support SM100 NVFP4 GenMHA and speculative decoding (#36340)

### [f5a1434](https://github.com/sgl-project/sglang/commit/f5a14347000b9b6e298aa98f718def21a6ad2b1b)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-18T21:08:19Z
- **提交信息**: [HiCache] Document transfer arguments (#40239)

Clarify the legacy host_indices argument and label Mamba test arguments,
including the current staging_tokens parameter. Executable code is unchanged.

Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>

### [cd4dd81](https://github.com/sgl-project/sglang/commit/cd4dd81c224ef1a6c40863b9cf4338d5f1897ce6)

- **作者**: amd-danli103
- **时间**: 2026-09-18T20:28:38Z
- **提交信息**: [AMD][DSV4] fix: drop shadowing local get_exec import that breaks model startup on ROCm (#40186)

### [6a9c700](https://github.com/sgl-project/sglang/commit/6a9c7001d3364d899db963eabb1ee47dc8a116d5)

- **作者**: metamergebot
- **时间**: 2026-09-18T20:18:01Z
- **提交信息**: [Logprob] Borrow graph-pool memory for input logprob logits construction (#40007)

Co-authored-by: cctry <csycfl@gmail.com>

### [da2f434](https://github.com/sgl-project/sglang/commit/da2f434951e0e4ea72b227078ee09c46f19ec2c8)

- **作者**: Jialin Ouyang
- **时间**: 2026-09-18T20:11:01Z
- **提交信息**: [Spec] Add explicit prefill shared-read capability for plugins (#39502)

### [aed3fb1](https://github.com/sgl-project/sglang/commit/aed3fb1cdd0cde61192c5db1c442430d212f140d)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-18T19:11:00Z
- **提交信息**: [Router] Log every request at one site; derive its outcome from the final status (3/3) (#39465)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [248c202](https://github.com/sgl-project/sglang/commit/248c202b46d4a44ad46a3f09d48661b0d9ce6257)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-18T18:07:55Z
- **提交信息**: Use runtime token widths for Triton speculative verification (#39859)

Co-authored-by: raghotham <853234+raghotham@users.noreply.github.com>

### [6bd1a0a](https://github.com/sgl-project/sglang/commit/6bd1a0af1d9e5756d115dbec6d02e0289c1b6950)

- **作者**: Lianmin Zheng
- **时间**: 2026-09-18T17:06:24Z
- **提交信息**: Add registration for external model configurations (#39452)

### [50a7de4](https://github.com/sgl-project/sglang/commit/50a7de47d5972a6f9a1560afe1067fd67d548b81)

- **作者**: Byron Hsu
- **时间**: 2026-09-18T17:06:13Z
- **提交信息**: [Benchmark] Add agentic rollout simulator and offline explorer (#40034)

### [4e0b56c](https://github.com/sgl-project/sglang/commit/4e0b56c8119a2673d0bf3bd748b8d9a895af79cb)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-18T16:46:29Z
- **提交信息**: [Router] Treat an upstream 503/429 as backpressure, not a breaker fault (2/3) (#39464)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [191172f](https://github.com/sgl-project/sglang/commit/191172fa742f8837423ca4e4be4919ebb52f1b51)

- **作者**: Shuwen Wang
- **时间**: 2026-09-18T15:29:29Z
- **提交信息**: [Unified Tree] fix: exempt host-locked aux nodes from the sanity_check host-LRU check (#39980)

### [45938a2](https://github.com/sgl-project/sglang/commit/45938a24ae415d7d70b986d77e2f9a632a5a9b07)

- **作者**: ChangLiu0709
- **时间**: 2026-09-18T15:21:58Z
- **提交信息**: [AMD] GLM-5.2 MI355X MXFP4: bump image to 20260916, use HIP Top-K (#40148)

### [7714b18](https://github.com/sgl-project/sglang/commit/7714b182f223bdcd1b376c6ade369d9c48dfb7ac)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-18T14:53:13Z
- **提交信息**: [Bugfix] Fix top-1 MoE routing with non-unit scaling (#40187)

### [81363bf](https://github.com/sgl-project/sglang/commit/81363bf8cb545ff8e1a9838733448c2252dd6cc0)

- **作者**: DarkSharpness
- **时间**: 2026-09-18T14:40:54Z
- **提交信息**: [kernel] Share the warp vectorized copy and enforce its alignment (#36176)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [9784d5f](https://github.com/sgl-project/sglang/commit/9784d5f979c9eaa5a6d9b31e596a7a73cb76dab8)

- **作者**: Mick
- **时间**: 2026-09-18T10:03:40Z
- **提交信息**: [diffusion] doc: sync CFG and tracing documentation (#39883)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [a6cf058](https://github.com/sgl-project/sglang/commit/a6cf05817f11d22023fd951a76255ef50fb09f49)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-18T09:55:30Z
- **提交信息**: dsv4.1: remaining model and runtime integration (#38798)

Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Xiaoyu Zhang <xiaoyu.zhang@radixark.ai>
Co-authored-by: Yuwei An <ayw.sirius19@gmail.com>
Co-authored-by: Khoa Pham <khoa.pham@radixark.ai>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Zhichen Zeng <zczeng@uw.edu>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [1b200ff](https://github.com/sgl-project/sglang/commit/1b200ffaaadc8039f0af84eac5271447a151c138)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-18T09:51:12Z
- **提交信息**: [Quant] Serve 32-wide-K ue8m0 block-FP8 linears through the FlashInfer MXFP8 GEMMs (#40039)

### [6c7c5e7](https://github.com/sgl-project/sglang/commit/6c7c5e78de0aa12ca6fb87fac32c0ee6158579c5)

- **作者**: iridiumine
- **时间**: 2026-09-18T09:19:31Z
- **提交信息**: [NPU] Run arch35 block-FP8 dense linears on the native MXFP8 GEMM (#39823)

### [7e6d5cb](https://github.com/sgl-project/sglang/commit/7e6d5cbfac4e792cb05990115f69508adb27ed97)

- **作者**: iridiumine
- **时间**: 2026-09-18T09:07:07Z
- **提交信息**: [NPU] Gate DFlash replay metadata refresh behind spec_algorithm check (#39879)

### [bbfcda4](https://github.com/sgl-project/sglang/commit/bbfcda48cebfbde2ed4be4e8273eb593c764e638)

- **作者**: Cheng Wan
- **时间**: 2026-09-18T08:59:07Z
- **提交信息**: [CI] Add a unified-memory rerun test group (#40147)

### [d6090f9](https://github.com/sgl-project/sglang/commit/d6090f92bf60dd6d0a02d8c02ec535f6f66ab1a9)

- **作者**: iridiumine
- **时间**: 2026-09-18T08:50:49Z
- **提交信息**: [NPU] Fuse MXFP4 W4A8 MoE gmm1 + swiglu + requant into one kernel (#39881)

### [2dee23a](https://github.com/sgl-project/sglang/commit/2dee23a876a02d3221b252c7978453ed08bed147)

- **作者**: Gurpreet Singh Dhami
- **时间**: 2026-09-18T08:40:32Z
- **提交信息**: [ROCm][diffusion] Enable fused qk norm and rope on ROCm (#35573)

Co-authored-by: jacky.cheng <yichiche@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [1e8699f](https://github.com/sgl-project/sglang/commit/1e8699fda39fdf7b78fa39b8e14962f34b83bd90)

- **作者**: Shu Wang
- **时间**: 2026-09-18T08:35:10Z
- **提交信息**: [NVIDIA][comm] Merge EP+MoE-TP post-experts all-reduces into one _TP reduction (#32963)

### [8ac39c6](https://github.com/sgl-project/sglang/commit/8ac39c66d837f6c91a496ba99a9dba7af1efa894)

- **作者**: zhaozx-cn
- **时间**: 2026-09-18T08:33:54Z
- **提交信息**: [NPU] support kimi k3 on A5 and improve performance (#39589)

### [6de4666](https://github.com/sgl-project/sglang/commit/6de4666e430951e4e39729e05e46d54e9ca7c850)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-18T08:32:45Z
- **提交信息**: [Router] Derive error status from a failure class; preserve the worker's status (1/3) (#39463)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [1fdd6c8](https://github.com/sgl-project/sglang/commit/1fdd6c89214d5c2f8a3529867b29de996ceb3237)

- **作者**: Rumit Desai
- **时间**: 2026-09-18T07:42:46Z
- **提交信息**: [Runtime] Let out-of-tree platforms provide full graph backends (#37969)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [c46bf5e](https://github.com/sgl-project/sglang/commit/c46bf5e990bdd99e2c200214b04683022100e4df)

- **作者**: Ziang Li
- **时间**: 2026-09-18T07:15:57Z
- **提交信息**: [MoE] Disable FlashInfer fused finalize by default for numerical accuracy (#40105)

### [956d414](https://github.com/sgl-project/sglang/commit/956d414dadd3211ce86788fd22402b4311616d45)

- **作者**: Ke Bao
- **时间**: 2026-09-18T07:12:36Z
- **提交信息**: Update ci permission (#40121)

### [0be8a0a](https://github.com/sgl-project/sglang/commit/0be8a0af0ef2d1c740dc4d084f368e75ef55a2cf)

- **作者**: Shuwen Wang
- **时间**: 2026-09-18T07:06:35Z
- **提交信息**: [DSV4] fix: keep the TileLang JIT cache under SGLANG_CACHE_DIR (#39364)

### [3bf243d](https://github.com/sgl-project/sglang/commit/3bf243d6a98448ae8e229bf170bed532cf0be602)

- **作者**: Kangyan-Zhou
- **时间**: 2026-09-18T07:00:17Z
- **提交信息**: [Router] Shard the cache-aware KV tree by chain root (#39167)

Co-authored-by: Kangyan Zhou <kangyan.zhou@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1282
- **最后更新**: 2026-09-18T01:53:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92125
- **最后更新**: 2026-09-19T00:04:20Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 34
- **主要提交者**: Itay Alroy, Taneem Ibrahim, Kevin H. Luu

## AI分析总结

# vLLM 昨日提交分析总结（39 条）

## 1. 主要更新类型分布

- **Bug 修复**（约 12 条）：占比最高，覆盖 MRV2 LoRA 批处理、KVConnector 中止安全、MLA 稀疏预填充缓冲、NIXL 通知请求、ROCm 段错误、DeepSeek V4 MoE 专家分布、Mistral-Large-3 精度回归、TritonMLA 非法内存访问等。
- **功能新增**（约 8 条）：DeepSeek-V4.1-Flash 编码器侧 SWA 重放、MoonEP 均衡 EP 后端 BF16 集成、Quark W4A16 INT4 导出、CPU FP8 W8A8、kimi-k3 路由专家量化、Rust 前端 gRPC 采样掩码等。
- **性能优化**（约 3 条）：DSV4.1 MegaMoE 暂存与 NVFP4 缓存优化、KV Offloading 背压检测与修复。
- **CI/基础设施**（约 8 条）：ROCm MI300 分片、MI250 弃用 DinD、GSM8K 超时上调、flaky 重跑标记等。
- **重构/清理**（约 5 条）：移除 assistant_token_mask、清理 Mistral tokenizer 死代码、移除 Transformers 版本守卫、Gemma4 权重加载重构、mypy 类型修复。

## 2. 关键变更点与项目方向

- **多硬件后端持续扩展**：ROCm（MI300/MI250）、XPU（int8 MoE、sleep 模式）、CPU（FP8 W8A8）、AMD Quark 量化同步推进，契合 vLLM "for everyone" 的跨平台普惠定位。
- **新模型快速适配**：DeepSeek-V4.1-Flash、Gemma4、Mistral-Large-3、kimi-k3 等前沿模型密集支持，体现项目紧跟模型生态的策略。
- **分布式与量化深化**：MoonEP 均衡专家并行、KV Offloading 背压、KVConnector 健壮性，强化大规模服务能力。

## 3. 对项目的影响与潜在意义

- 大量 Bug 修复（尤其 MLA、MoE、KV 缓存相关）直接提升生产环境稳定性与数值正确性。
- 量化与硬件后端扩展降低部署成本，扩大适用场景。
- CI 稳定性改进（超时、重跑、分片）减少误报，提升开发效率与合并吞吐。
- 移除废弃接口（assistant_token_mask）推动 API 收敛，减少维护负担。

## 4. 值得关注的技术点

- **KV Offloading 背压检测**：为长上下文/高并发场景提供自适应保护机制。
- **MoonEP 均衡 EP 后端**：面向专家并行的负载均衡新方案。
- **DeepSeek-V4.1 编码器侧 SWA 重放**：滑动窗口注意力在编码器侧的有界重放，属前沿优化。
- **Rust 前端 gRPC 采样掩码**：前端架构向 Rust 迁移的持续信号。
- **NVFP4 缓存 gather 优化**：新一代低精度格式的性能落地。

## 5. 结合 README 的项目发展视角

README 强调 "Easy, fast, and cheap LLM serving for everyone"。本批提交从三个维度呼应这一目标：**fast**——MegaMoE/NVFP4 优化与背压机制提升吞吐；**cheap**——多硬件量化（CPU FP8、Quark INT4、XPU int8）降低部署门槛；**everyone**——ROCm/XPU/CPU 及新模型支持扩大覆盖面。整体呈现"稳中求进"：以密集 Bug 修复保障可靠性，同时稳步推进新模型、新硬件与新量化格式，巩固 vLLM 作为通用高性能 LLM 服务引擎的领先地位。

## 详细提交记录

### [a1bf8ac](https://github.com/vllm-project/vllm/commit/a1bf8ac12d9f1537ff2d233f5ab3d1346fd8bd44)

- **作者**: waizuichougou
- **时间**: 2026-09-18T22:13:23Z
- **提交信息**: [Bugfix][MRV2] Match fast-prefill padding to active LoRA batches (#56456)

Signed-off-by: waizuichougou <2082431897@qq.com>
Signed-off-by: waizuichougou <105572299+waizuichougou@users.noreply.github.com>

### [1dc2d85](https://github.com/vllm-project/vllm/commit/1dc2d854c12099f1f08233c886368a8c7baf430f)

- **作者**: Yifan Qiao
- **时间**: 2026-09-18T22:01:24Z
- **提交信息**: [Feat][Model] Support encoder-side SWA-bounded replay for DeepSeek-V4.1-Flash (#56227)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [6aab78f](https://github.com/vllm-project/vllm/commit/6aab78f4777c945b02123af330ff351f72785c0f)

- **作者**: ys2025-AI
- **时间**: 2026-09-18T21:53:02Z
- **提交信息**: [Bugfix][KVConnector] Make ExampleHiddenStatesConnector abort-safe (#56841)

Signed-off-by: ys2025-AI <yuanshuaien@163.com>

### [62af3df](https://github.com/vllm-project/vllm/commit/62af3df7347cf890b4b925a18ab6a2afd00c70b9)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-18T21:22:18Z
- **提交信息**: [Bugfix][MLA] Reserve sparse prefill buffers before KV cache sizing (#57575)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [0390299](https://github.com/vllm-project/vllm/commit/0390299309c5bc11b8aa78ea0f1d10993273dbb4)

- **作者**: Aarushi Jain
- **时间**: 2026-09-18T21:16:29Z
- **提交信息**: [ROCm][CI] Shard MI300 Entrypoints Integration (Pooling) (#57583)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>

### [2c3fb4c](https://github.com/vllm-project/vllm/commit/2c3fb4c545005db887788747b48d040d930604df)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-18T21:13:35Z
- **提交信息**: [CI][ROCm] Deprecate DinD for MI250 test groups (#56162)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [49e0427](https://github.com/vllm-project/vllm/commit/49e0427ca5183a56ccb112e5be1300feb2873ca9)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-18T20:33:02Z
- **提交信息**: [Bugfix][NIXL] Avoid receive reports for notification-only requests (#57570)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [63d9ad0](https://github.com/vllm-project/vllm/commit/63d9ad0a3a435cdf3a44495028b10f390a38f960)

- **作者**: Matt Mastracci
- **时间**: 2026-09-18T20:11:27Z
- **提交信息**: [Model] DiffusionGemma: honor logprob_token_ids on the converging step (#57417)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [50d812b](https://github.com/vllm-project/vllm/commit/50d812b66a697c464a9964b3a061b47583b83e34)

- **作者**: Woosuk Kwon
- **时间**: 2026-09-18T19:57:19Z
- **提交信息**: [Perf][DSV4.1] Optimize MegaMoE staging and NVFP4 cache gathers (#57604)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [23e26e0](https://github.com/vllm-project/vllm/commit/23e26e058839fb2a3e77c78fbf2184f563593227)

- **作者**: bnellnm
- **时间**: 2026-09-18T18:47:48Z
- **提交信息**: [KV Offloading] Back-pressure detection and remediation (#50045)

Signed-off-by: Bill Nell <bnell@redhat.com>
Signed-off-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>

### [71fc70d](https://github.com/vllm-project/vllm/commit/71fc70d3ae1df53300a23ec69f6d97b7207a109f)

- **作者**: frida-andersson
- **时间**: 2026-09-18T16:57:44Z
- **提交信息**: [ROCm][DSv4] Fix sparse-indexer logits collapse on gfx950/gfx942 (#50455)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Signed-off-by: frida-andersson <fanderss@amd.com>

### [8a5cf54](https://github.com/vllm-project/vllm/commit/8a5cf5438728180210aea43897d6a717de4b46ec)

- **作者**: Harry Mellor
- **时间**: 2026-09-18T16:29:11Z
- **提交信息**: [Multimodal] Type dummy options per modality (#57576)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [56cac80](https://github.com/vllm-project/vllm/commit/56cac80b145ed1e9814bba519735ad4c71c530f5)

- **作者**: Cyrus Leung
- **时间**: 2026-09-18T16:17:51Z
- **提交信息**: [Deprecation] Remove assistant_token_mask support (#57520)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [164dca8](https://github.com/vllm-project/vllm/commit/164dca8d1e65b8f10346321f01b25e23caa642a6)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-18T16:08:59Z
- **提交信息**: [Nixl] Separate transport-failure metrics from KV expiry (#55854)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [a715606](https://github.com/vllm-project/vllm/commit/a7156060c1fc17c5b31d46d3760829bed8ac1a58)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-18T16:08:44Z
- **提交信息**: [Core] Make parallel sampling (n>1) reqs admission atomic (#53936)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4991f97](https://github.com/vllm-project/vllm/commit/4991f976698d8ebf1a3b6d743c959b52bac689cc)

- **作者**: Yan Ma
- **时间**: 2026-09-18T15:49:17Z
- **提交信息**: [XPU] sleep mode: fix KV cache release test (#57485)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [017dced](https://github.com/vllm-project/vllm/commit/017dced6a6fd3cf430e4686a47b354da1cadfbf5)

- **作者**: Itay Alroy
- **时间**: 2026-09-18T15:17:07Z
- **提交信息**: [DeepSeek V4] Fix fused MoE expert distribution (#57465)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [dbf4b89](https://github.com/vllm-project/vllm/commit/dbf4b89cf229fa52869aa36744d2e0ec0c8997ed)

- **作者**: Cyrus Leung
- **时间**: 2026-09-18T15:01:35Z
- **提交信息**: [Misc] Remove unnecessary Transformers version guards (#57556)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [1cdf168](https://github.com/vllm-project/vllm/commit/1cdf1689e55c483a754c6c24baac3e47d39d4ece)

- **作者**: Artur Fierka
- **时间**: 2026-09-18T14:38:15Z
- **提交信息**: [Quantization][XPU] Enable int8_w8a8 MoE on the Triton backend for XPU (#53162)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [70164bd](https://github.com/vllm-project/vllm/commit/70164bdadc048ce2697ea92b2dbb2d39f881e65e)

- **作者**: Martin Hickey
- **时间**: 2026-09-18T14:36:27Z
- **提交信息**: [Frontend] Add stream reasoning and tool calls from the derender endpoint (#50550)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [9115482](https://github.com/vllm-project/vllm/commit/911548247a7b04e0c9cffca1cfba66b7120d6d3f)

- **作者**: Kevin Li
- **时间**: 2026-09-18T14:34:01Z
- **提交信息**: [Distributed][MoonEP] BF16 integration of MoonEP balanced EP backend (#52101)

Signed-off-by: kevinli <306243285+kaijunli-infr@users.noreply.github.com>
Co-authored-by: kevinli <306243285+kaijunli-infr@users.noreply.github.com>

### [2bdae2a](https://github.com/vllm-project/vllm/commit/2bdae2a5a83fe8e5640078a3d4bfe86cce323d0b)

- **作者**: Julien Debache
- **时间**: 2026-09-18T14:19:16Z
- **提交信息**: [fix] Mistral-Large-3 accuracy regression on `main` (#57563)

Signed-off-by: jdebache <jdebache@nvidia.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [76d517f](https://github.com/vllm-project/vllm/commit/76d517fd1279805fa2318c28343fcd57b030ead3)

- **作者**: Kyle Sayers
- **时间**: 2026-09-18T14:03:59Z
- **提交信息**: [Quantization] Support kimi-k3 routed expert quant (#57430)

Signed-off-by: Kyle Sayers <kylesayrs@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [44dd18f](https://github.com/vllm-project/vllm/commit/44dd18fe0bb0f13157f97a5aa029b6604468fca6)

- **作者**: Asaf Gardin
- **时间**: 2026-09-18T12:07:30Z
- **提交信息**: [Model][Gemma4] Load Weights with AutoWeightsLoader (#55911)

Signed-off-by: Josephasafg <ajgard7@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [2b8a549](https://github.com/vllm-project/vllm/commit/2b8a5495a88a9a44a9d92e8c4f4aae3b55b6b74b)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-18T11:50:01Z
- **提交信息**: [Mypy] Fix mypy typing for N/O models (#54142)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [e562003](https://github.com/vllm-project/vllm/commit/e562003adbb9c4eb177194d1318eb2e6862a8e15)

- **作者**: Aditya Ganesh Kumar
- **时间**: 2026-09-18T11:46:41Z
- **提交信息**: [Tokenizer] Drop dead Mistral tokenizer shims for transformers#41962 (#56325)

Signed-off-by: Aditya Ganesh Kumar <adty910@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [c58532c](https://github.com/vllm-project/vllm/commit/c58532c86b8ab821fc1d819636480b7588bce7b5)

- **作者**: Bugen Zhao
- **时间**: 2026-09-18T11:44:05Z
- **提交信息**: [Frontend] Upgrade XGrammar to 0.2.7 and Rust structural tags to 0.3.0 (#57272)

Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [cc09352](https://github.com/vllm-project/vllm/commit/cc09352e5c50ca6b7d2c6d79b29d6d3b18df3046)

- **作者**: adenzhou1350
- **时间**: 2026-09-18T10:44:39Z
- **提交信息**: [Bugfix][Multimodal] Preserve DeepSeek V4 image block spacing (#56882)

Signed-off-by: Xucheng Zhou <aden1350@outlook.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [04a3a00](https://github.com/vllm-project/vllm/commit/04a3a00eb79118dda521577caaaba2ba6b65bb33)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-18T10:40:54Z
- **提交信息**: [CI] Raise GSM8K startup max wait to 2400s for flaky 30B+ MoE eval configs (#57361)

Signed-off-by: khluu <khluu000@gmail.com>

### [f2b6152](https://github.com/vllm-project/vllm/commit/f2b6152ec2448b4ea877153d6a613c381e7fd8bb)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-18T10:40:32Z
- **提交信息**: [CI] Add flaky rerun markers / timeout skips to sibling tests lacking them (#57359)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [4c6c1a4](https://github.com/vllm-project/vllm/commit/4c6c1a40b3cb4f9018e2a6c79fdbe11621acbda1)

- **作者**: Matt
- **时间**: 2026-09-18T10:13:45Z
- **提交信息**: [ROCm][Bugfix] Fix intermittent ROCR host segfault (#57328)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>

### [5397f96](https://github.com/vllm-project/vllm/commit/5397f967b9ee282354f9803af3e758c9270588e9)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-18T10:11:07Z
- **提交信息**: [CI] Add residual timeout headroom after JIT rollback (#56649)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [5bb5962](https://github.com/vllm-project/vllm/commit/5bb596201a19ba73e08e05e062a7ad64e96ecda2)

- **作者**: vllm-agent
- **时间**: 2026-09-18T10:10:38Z
- **提交信息**: [CI] Raise Elastic EP Scaling step timeout 30m -> 40m (#57287)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>

### [b346479](https://github.com/vllm-project/vllm/commit/b34647906550f6e9dc65c55ecfb36b697d5e1f43)

- **作者**: Yuwen Zhou
- **时间**: 2026-09-18T09:59:42Z
- **提交信息**: [CPU] Add CPU FP8 W8A8 linear/MoE support (#49942)

Signed-off-by: yuwenzho <yuwen.zhou@intel.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [6df2b1a](https://github.com/vllm-project/vllm/commit/6df2b1a8c64a7956c51410cbfe1b786a69574263)

- **作者**: meng-amd
- **时间**: 2026-09-18T09:52:46Z
- **提交信息**: [Quantization] Support native Quark W4A16 INT4/UINT4 exports in vLLM (#48606)

Signed-off-by: HongWei Meng <HongWei.Meng@amd.com>

### [67a8a3f](https://github.com/vllm-project/vllm/commit/67a8a3f9269795d683868254d134a199c29aff4f)

- **作者**: shaohuaxi
- **时间**: 2026-09-18T09:05:13Z
- **提交信息**: [Bugfix][CPU] Fix macOS multimodal SHM cache initialization (#57142)

Signed-off-by: 子华 <huaxi.shx@alibaba-inc.com>
Co-authored-by: Codex <noreply@openai.com>

### [3263658](https://github.com/vllm-project/vllm/commit/32636580a6f1c3bc41deefc4bf7800f850c24034)

- **作者**: olka-amd
- **时间**: 2026-09-18T08:49:53Z
- **提交信息**: [Bugfix][MLA] TritonMLA: fix illegal memory access on causal multi-token decode (#51065)

Signed-off-by: Oleksandr Kachur <oleksandr.kachur@amd.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [8da75d6](https://github.com/vllm-project/vllm/commit/8da75d61904cd0b2c5c322746ea15251773ec51f)

- **作者**: Thien Tran
- **时间**: 2026-09-18T08:39:27Z
- **提交信息**: C3x SM100 FP8 blockwise - Pad activation scales to multiple of 4 (#57377)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Codex <noreply@openai.com>

### [95d7237](https://github.com/vllm-project/vllm/commit/95d723700b1df07b20263c696c0342b92c188bfe)

- **作者**: Biswa Panda
- **时间**: 2026-09-18T08:26:17Z
- **提交信息**: [Rust Frontend] Return sampling masks over gRPC (#56777)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: Biswa Panda <biswa.panda@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-19
**监控日期**: 2026-09-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6888
- **最后更新**: 2026-09-19T00:10:31Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 12
- **主要提交者**: ooooooye, chickeyton, Zeng Chuang

## AI分析总结

# vllm-omni 昨日提交分析（14 条）

## 1. 主要更新类型
- **Bug 修复为主**（约 6 条）：核心 CLI 并行参数、Realtime 截断、TTS 流式、MiniMax-H3 精度、Ascend 权重加载、XPU KV 预分配。
- **CI/Build 治理**（约 5 条）：XPU 镜像源清理、Qwen3-Omni 结构化配置校验、HiDream/MammothModa2 测试重定向、MiniCPM-o Nightly 修复。
- **模型迁移与性能**（约 3 条）：MammothModa2 DiT 迁移、LoRA delta 计算加速、HunyuanVideo E2E 跨硬件共享。

## 2. 关键变更点与项目方向
- **MammothModa2 DiT 迁移至共享 diffusion runtime**：体现项目"统一多模态推理运行时"的核心方向，减少模型专属代码，提升复用性。
- **LoRA delta 在 CPU 权重下启用 NPU/GPU matmul**：直接服务于"fast & cheap serving"目标，优化异构硬件下的性能。
- **CLI 并行参数与嵌套 deploy 配置的修复**：强化部署配置一致性，符合"easy serving"的易用性诉求。
- **XPU/Ascend/NPU 多硬件适配**：显示项目正积极扩展非 NVIDIA 硬件生态。

## 3. 对项目的影响与意义
- 修复类提交提升了**生产可用性**，尤其是 CLI 参数丢失、TTS 流式中断等直接影响用户体验的问题。
- CI 治理降低了**回归风险**，将跳过测试重新关联到真实 issue，避免"假绿"。
- 硬件适配与性能优化扩大了**部署覆盖面**，契合"for everyone"的定位。

## 4. 值得关注的技术点
- **设备无关的 KV 预分配**：为 AR-Diffusion 在多后端间统一行为奠定基础。
- **Hopper-safe 调制精度**：反映模型精度与硬件兼容性的精细权衡。
- **DLOFix/mxfp 在线卸载后的超宽权重直载主机内存**：涉及量化+卸载的复杂内存路径，是 Ascend 场景的关键修复。
- **结构化配置采样默认值对齐 vLLM 归一化**：说明项目在配置语义上向 vLLM 主仓靠拢。

## 5. 结合 README 的项目发展视角
README 强调"Easy, fast, and cheap omni-modality serving for everyone"。本批提交三条主线与之高度吻合：**易用性**（CLI/配置修复）、**性能**（LoRA matmul、KV 预分配）、**普惠性**（XPU/NPU/Ascend 多硬件支持）。MammothModa2 迁移到共享 runtime 则推动架构收敛，为后续更多 omni 模型低成本接入铺路。整体看，项目正从"功能覆盖"转向"稳定性 + 跨硬件一致性 + 性能精细化"的成熟阶段。

## 详细提交记录

### [4c7a98c](https://github.com/vllm-project/vllm-omni/commit/4c7a98c26f6167a219b008263773c959a65ac0f2)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-18T22:32:33Z
- **提交信息**: [XPU][CI] Drop the USTC PyPI mirror from the XPU image build (#7808)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [7b4fc7c](https://github.com/vllm-project/vllm-omni/commit/7b4fc7ce2e533b29193b3d10a7348b6ac5380fae)

- **作者**: Sun
- **时间**: 2026-09-18T20:29:18Z
- **提交信息**: [Model] Migrate MammothModa2 DiT to the shared diffusion runtime (#7134)

Signed-off-by: levius <2114377220@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [ca3ccfc](https://github.com/vllm-project/vllm-omni/commit/ca3ccfc9a3054e65e4267bb3e3cc95db48a98f09)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-18T19:41:41Z
- **提交信息**: [XPU][Bugfix] Make AR-Diffusion KV preallocation device-agnostic (#7777)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [fbb4e63](https://github.com/vllm-project/vllm-omni/commit/fbb4e63f0abc7076b0c3d92110d2b376adbb313c)

- **作者**: bcsdhjew
- **时间**: 2026-09-18T18:59:09Z
- **提交信息**: [Bugfix][Core] Apply Realtime item truncation once per command (#7800)

Signed-off-by: Nolen Liang <nliang@nvidia.com>

### [0570f7a](https://github.com/vllm-project/vllm-omni/commit/0570f7a06ebcac9d880f18d106e8ceb7c1e94567)

- **作者**: Yueqian Lin
- **时间**: 2026-09-18T18:25:01Z
- **提交信息**: [CI][Qwen3-Omni] Keep the deploy-YAML literal in the structured-config sampling check (#7803)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [d4ffde1](https://github.com/vllm-project/vllm-omni/commit/d4ffde1a6ef1559426616b9aed4d0c53530d81fa)

- **作者**: Yueqian Lin
- **时间**: 2026-09-18T14:55:58Z
- **提交信息**: [CI][Qwen3-Omni] Compare structured-config sampling defaults against vLLM normalization (#7742)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [0a5ece4](https://github.com/vllm-project/vllm-omni/commit/0a5ece4ae5559fc40e1b6fe38f695b7e0dbe4466)

- **作者**: wangyu
- **时间**: 2026-09-18T13:24:00Z
- **提交信息**: [CI/Build] Retarget skipped HiDream and MammothModa2 E2E tests to current issues (#7755)

Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [4b0c187](https://github.com/vllm-project/vllm-omni/commit/4b0c187a1e1658c14b93121cae2a6bfda7c563d2)

- **作者**: Yukim1
- **时间**: 2026-09-18T13:09:18Z
- **提交信息**: [Bugfix][Core] Fix CLI parallel flags losing to nested deploy parallel_config (#7786)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [3084b5d](https://github.com/vllm-project/vllm-omni/commit/3084b5d1073522b970002a2b8127ab0b2354c8a3)

- **作者**: akshatvishu
- **时间**: 2026-09-18T12:06:57Z
- **提交信息**: [BugFix][TTS] Restore MOSS v1 codec streaming (#6420)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [6df62d5](https://github.com/vllm-project/vllm-omni/commit/6df62d51573ca5be7826321ba2de1cd071d997f8)

- **作者**: chickeyton
- **时间**: 2026-09-18T08:58:33Z
- **提交信息**: [CI/Build][MiniCPM-o] Fix the Nightly tests (#7758)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [aa2fada](https://github.com/vllm-project/vllm-omni/commit/aa2fadac42a9370d33958351ed8bc8869d4c8354)

- **作者**: holykie
- **时间**: 2026-09-18T08:51:23Z
- **提交信息**: [Perf][Diffusion] Activate NPU/GPU matmul for LoRA delta computation when weights are on CPU (#7590)

Signed-off-by: holykie <116775684+holykie@users.noreply.github.com>

### [eb20759](https://github.com/vllm-project/vllm-omni/commit/eb2075981d3a2351978bf890bcc8c266c2917887)

- **作者**: Zeng Chuang
- **时间**: 2026-09-18T08:49:08Z
- **提交信息**: [Test][Ascend] Share HunyuanVideo-1.5 E2E across GPU and NPU (#7547)

Signed-off-by: zengchuang <zengchuang3@huawei.com>

### [823af92](https://github.com/vllm-project/vllm-omni/commit/823af92347952708b2496e4b07d2a4a26ed436ac)

- **作者**: ooooooye
- **时间**: 2026-09-18T07:36:48Z
- **提交信息**: [Bugfix][Ascend NPU][Diffusion] Load over-wide unquantized fallback weights straight into host memory under DLOFix/mxfp online offload after quant (#7009)

Signed-off-by: brandneway <gyuan4892@gmail.com>

### [5d3e6dc](https://github.com/vllm-project/vllm-omni/commit/5d3e6dc1b4c172202b080a8659f522deae76852b)

- **作者**: WeiQing Chen
- **时间**: 2026-09-18T07:16:45Z
- **提交信息**: [Bugfix][MiniMax-H3] Use Hopper-safe modulation precision (#7693)

Signed-off-by: david6666666 <530634352@qq.com>

---
