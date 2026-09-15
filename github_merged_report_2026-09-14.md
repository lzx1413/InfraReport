# GitHub Stars 合并报告 - 2026-09-14

**合并日期**: 2026-09-15
**监控日期**: 2026-09-14
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


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2208
- **最后更新**: 2026-09-14T14:44:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2813
- **最后更新**: 2026-09-14T17:38:25Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Watebear

## AI分析总结

# LightX2V 昨日提交分析（第 1/1 批）

## 1. 主要更新类型
本次仅有一条提交，属于 **Bug 修复（fix）**，范围限定在 `minimax-h3` 相关模块，具体涉及 `ref2av`（reference-to-audio-video）流程中 base transformer 的可用性调整。

## 2. 关键变更点及与项目方向的关系
- 变更核心：允许在 `ref2av` 场景下使用 **base transformer**，此前该路径可能被限制或存在调用异常。
- 与项目方向的关系：LightX2V 定位为轻量级视频生成推理框架，强调多模型、多任务的高效推理支持。`minimax-h3` 是其支持的模型之一，`ref2av` 属于参考图/参考条件驱动的音视频生成任务。放开 base transformer 的使用，意味着框架在模型组件选择上更加灵活，符合项目“通用推理框架”的定位。

## 3. 对项目的影响和潜在意义
- **修复层面**：解决了 `ref2av` 流程中 base transformer 无法正常启用的问题，提升该路径的可用性。
- **兼容性层面**：可能改善与不同 transformer 配置（base 与其它变体）的兼容，降低用户在该任务上的使用门槛。
- **生态层面**：作为编号 #1515 的修复，说明社区或内部已在实际使用中暴露该问题，及时修复有助于维护框架在音视频生成任务上的稳定性与口碑。

## 4. 值得关注的技术点
- `ref2av` 任务中 transformer 的选择逻辑：base transformer 与其它 transformer 在结构或权重加载上的差异，可能是此前限制的原因。
- 该修复是否涉及配置解析、模型加载分支或推理管线的条件判断，值得后续查看 diff 确认。
- 与 `minimax-h3` 模型整体支持的关系：是否还有其他组件（如 VAE、调度器）存在类似限制。

## 5. 基于 README 的项目背景分析
README 显示 LightX2V 是“Light Video Generation Inference Framework”，强调轻量、高效的视频生成推理，并支持多种模型与任务。本次提交虽小，但体现了项目在 **多任务推理路径上的持续打磨**：通过修复特定模型（minimax-h3）在特定任务（ref2av）中的组件可用性问题，逐步完善框架的鲁棒性和覆盖面。对于依赖该框架进行音视频生成推理的用户而言，这类修复直接提升了实际可用性，是项目从“能跑”走向“好用”的必要积累。

**总结**：这是一次针对性的 Bug 修复，规模小但指向明确，服务于框架在多模型、多任务推理场景下的稳定性和灵活性，符合 LightX2V 作为轻量视频生成推理框架的持续演进方向。

## 详细提交记录

### [8335bb4](https://github.com/ModelTC/LightX2V/commit/8335bb488ff747d079ad643c833ea5b10d2c5fd6)

- **作者**: Watebear
- **时间**: 2026-09-14T11:50:38Z
- **提交信息**: fix(minimax-h3): allow base transformer for ref2av (#1515)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2247
- **最后更新**: 2026-09-14T02:59:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6406
- **最后更新**: 2026-09-15T00:31:26Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Brian K. Ryu, Yan Wang, Alex Yang

## AI分析总结

## 一、主要更新类型

本批 7 个提交以**功能新增**和**性能优化**为主，辅以测试修复与 API 正式化：涵盖注意力内核扩展（SM80/SM107）、GEMM 新后端、通信原语、MoE API 官方化，以及针对特定硬件路径的专项优化。

## 二、关键变更点与项目方向

- **硬件覆盖横向扩张**：FA2 大 head FP8 KV 从 SM100+ 下放到 SM80+（A100），paged-MQA logits 启用 Rubin SM107，并新增 SM10x 分组 FP8 GEMM 的 CuTe 后端。这与 FlashInfer 作为“跨代 GPU 高性能推理内核库”的定位高度一致。
- **性能路径精细化**：paged FA2 对 K/V 等步长做编译期特化，避免冗余地址计算；MoE、通信层引入可复用 workspace 与重叠流水线。
- **API 成熟度提升**：统一 MoE API 正式打上 `@flashinfer_api`，标志其从实验走向稳定。
- **测试稳健性**：KDA 预填充测试在旧版 CuTe DSL 上 xfail，避免环境差异导致的假失败。

## 三、对项目的影响与潜在意义

- **扩大可用场景**：A100 用户可启用 FP8 KV cache 与 Gemma 4 等大 head 模型，直接提升存量硬件的服务吞吐（README 数据显示 OTPS/GPU 显著优于 Triton）。
- **抢占新硬件先机**：Rubin SM107 与 SM103 支持使 FlashInfer 在 Blackwell 后续架构上保持首发优势。
- **降低集成门槛**：MoE API 官方化与通信原语标准化，便于 vLLM 等下游框架稳定对接。

## 四、值得关注的技术点

- **架构探测与 DSL 版本解耦**：SM107 启用中区分“是否提供内核”与“DSL 能否编译”，并用 `native_only=True` 拒绝不健全的 family 回退。
- **异构节点正确性**：arch 决策基于输入张量设备而非环境探测，避免 Blackwell+Rubin 混合部署下的错误特化与缓存污染。
- **TMEM 列数约束**：FP4 `next_n=4` 需 544 列，超 SM100 的 512 上限，靠 Rubin 576 列的非 2 次幂分配实现。
- **等步长特化**：主机侧一次性比较 stride，内核零分支，兼顾性能与通用性。

## 五、结合项目背景的发展影响

FlashInfer 的核心目标是提供跨 GPU 代际的高性能推理内核。本批提交同时推进三条主线：**向下兼容存量硬件**（A100/SM80）、**向上适配新架构**（Rubin/SM107）、**横向完善组件生态**（GEMM、MoE、通信）。这表明项目正从“单点内核优化”转向“全栈、全代际的推理基础设施”，既服务现有部署，又为下一代硬件与框架集成铺路，巩固其作为 vLLM 等推理引擎底层加速库的地位。

## 详细提交记录

### [51dfe7a](https://github.com/flashinfer-ai/flashinfer/commit/51dfe7ad5bd7ffad0e68567462b3ea8c4bdcd14b)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-09-14T23:35:57Z
- **提交信息**: feat: enable large-head attention on SM80, for VLLM to run FP8 kv (#5044)

<!-- .github/pull_request_template.md -->

## 📌 Description

Enable FlashAttention-2 large-head FP8 KV-cache kernels on SM80+ so
models with head dimension 512, including Gemma 4, can use FlashInfer
FP8 KV cache on A100.

Changes:

- Generate and JIT-compile FA2 large-head FP8 KV modules for SM80+
instead of restricting them to SM100+.
- Enable the existing large-head FP8 prefill and tensor-core decode
paths on Ampere while retaining the SM100+ restriction for NVFP4
large-head decode.
- Extend the existing FP8 prefill/decode test coverage to SM80.
- Add focused Gemma 4 head-dim-512 prefill and decode correctness tests
against an independent FP32 PyTorch reference, plus a JIT
architecture-flag regression test.

### A100 serving performance

NVIDIA A100-SXM4-80GB; fixed 128-request chat dataset; mean ISL 9,936;
max OSL 300; MTP3; prefix caching disabled; concurrency 1–64. BF16 uses
TP2 and quantized checkpoints use TP1. OTPS/GPU is aggregate
output-token throughput divided by TP.

| Checkpoint | TP | KV cache | Attention | c1 OTPS/user | Best observed
OTPS/GPU (c1–64) |
|---|---:|---|---|---:|---:|
| BF16-IT | 2 | BF16 | Triton | 158.12 | 241.08 (c64) |
| BF16-IT | 2 | BF16 | FlashInfer | 148.49 | **323.82 (c64)** |
| [FP8 dynamic][fp8-model] | 1 | BF16 | Triton | 154.52 | 267.01 (c16) |
| [FP8 dynamic][fp8-model] | 1 | BF16 | FlashInfer | **174.13** | 371.60
(c64) |
| [FP8 dynamic][fp8-model] | 1 | FP8 | FlashInfer | 170.90 | **389.46
(c64)** |
| NVFP4 | 1 | BF16 | Triton | 154.23 | 286.49 (c64) |
| NVFP4 | 1 | BF16 | FlashInfer | **175.11** | **415.74 (c64)** |
| NVFP4 | 1 | FP8 | FlashInfer | 173.01 | 412.56 (c64) |

<img width="3144" height="1922"
alt="gemma4_26b_a4b_a100_260910_4line_mtp3_no_c128_no_sla_pareto"
src="https://github.com/user-attachments/assets/1e559635-b636-4348-b2ef-01809c36f965"
/>

At the best observed points from concurrency 1–64, FlashInfer improves
OTPS/GPU over Triton by 34% for BF16, 39–46% for the FP8 checkpoint, and
44–45% for NVFP4.

## 🔍 Related Issues

N/A

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

Added/updated coverage:

- Gemma 4 FP8 KV head-dim-512 chunked prefill versus an FP32 PyTorch
reference.
- Gemma 4 FP8 KV head-dim-512 tensor-core decode versus an FP32 PyTorch
reference.
- SM80 JIT architecture flags and existing FP8 large-head prefill/decode
coverage.
- End-to-end A100 serving sweeps and GPQA Diamond validation.

### GPQA Diamond

FP8 golden/reference checkpoint:
[RedHatAI/gemma-4-31B-it-FP8-dynamic][fp8-model]. All runs use TP4,
MTP3, and thinking. Each score covers 198 questions with 16 sampled
solutions per question; pass@1 is the reported average of 16 runs.

| Checkpoint | Triton KV cache | Triton pass@1 (avg. of 16) | Triton
pass@16 | FlashInfer KV cache | FlashInfer pass@1 (avg. of 16) |
FlashInfer pass@16 |
|---|---|---:|---:|---|---:|---:|
| [FP8 dynamic][fp8-model] | BF16 | 79.36% ± 2.08% | **94.95%** | BF16 |
**80.62% ± 1.69%** | 93.94% |
| NVFP4 | BF16 | 79.23% ± 1.84% | 93.43% | FP8 | **80.40% ± 1.00%** |
**94.95%** |

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends".
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

Please focus on the SM80 architecture gating and the
independent-reference tolerances in
`tests/attention/test_gemma4_fa2_accuracy.py`.

[fp8-model]: https://huggingface.co/RedHatAI/gemma-4-31B-it-FP8-dynamic


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Expanded large-head attention support for compatible KV data types on
Ampere and newer GPUs.
* Large-head FP8 prefill and paged decode paths now support SM80+
hardware.
  * NVFP4 large-head decode remains limited to newer GPU architectures.

* **Tests**
  * Added Gemma 4 FP8 KV accuracy coverage for prefill and decode.
* Added validation for Ampere-compatible large-head kernel builds and
expanded large-head test coverage on SM80+ GPUs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>

### [82316cd](https://github.com/flashinfer-ai/flashinfer/commit/82316cda999de3e33ac1fd3d033a02920fb5ec06)

- **作者**: Sahil Modi
- **时间**: 2026-09-14T23:20:29Z
- **提交信息**: feat(gemm): add SM10x contiguous grouped FP8 CuTe backend (#4734)

## 📌 Description

Adds `flashinfer.gemm.group_gemm_fp8_nt_groupwise_contiguous`, a
standalone CuTe-DSL function for grouped FP8 GEMM on SM100 and SM103.

The existing `group_deepgemm_fp8_nt_groupwise` API is unchanged. The new
function does not take a `backend` argument.

### Behavior

- Accepts FP8 E4M3 inputs with per-row 128-element scales for A and
128×128 block scales for B.
- Returns bfloat16 output and supports a caller-provided `out` tensor.
- Requires positive N and K divisible by 128. M can have a partial final
tile or be zero.
- Requires sorted, in-range expert indices with 128-row-aligned internal
expert boundaries. `-1` padding is unsupported.
- Provides optional `validate_indices=True` checks. These synchronize
with the CPU and must run outside CUDA graph capture. With validation
disabled, callers must satisfy the documented index requirements.
- Uses the input tensor’s CUDA device and current PyTorch stream.
- Reuses compiled kernels across token counts, keeping at most two
variants per device and weight shape. Concurrent calls share one
compilation.

Includes API documentation, trace support, generated trace examples,
regression tests, and a benchmark script.

### B200 performance

The original comparison below uses a caller-preallocated output for both
implementations, so output allocation is excluded. Measurements are the
arithmetic mean of two complete runs with 10 warmups and 50 timed
iterations per workload. Device-active timing gives a 1.659x weighted
geomean, close to the 1.676x end-to-end kernel-call result.

Original benchmark environment: B200 at a stable 1500 MHz SM clock, CUDA
13.2, PyTorch 2.13.0+cu132, CUTLASS/CuTe DSL 4.6.1, and
`sgl-deep-gemm==0.1.5.post3`. Each expert has 256 consecutive rows.

| Workload | Shape `(M, N, K, experts)` | DeepGEMM | CuTe DSL | Speedup
|
|---|---:|---:|---:|---:|
| TP8 gate/up | `(131072, 256, 4096, 512)` | 268.184 us | 195.192 us |
1.374x |
| TP8 down | `(131072, 4096, 128, 512)` | 564.415 us | 229.384 us |
2.461x |
| EP8 gate/up | `(16384, 2048, 4096, 64)` | 194.672 us | 159.224 us |
1.223x |
| EP8 down | `(16384, 4096, 1024, 64)` | 125.016 us | 96.312 us | 1.298x
|
| WideEP32 gate/up | `(4096, 2048, 4096, 16)` | 74.440 us | 52.744 us |
1.411x |
| WideEP32 down | `(4096, 4096, 1024, 16)` | 52.632 us | 31.288 us |
1.682x |
| **Weighted geomean** | | **246.389 us** | **146.987 us** | **1.676x**
|

### Current validation

Additional validation used production B200 through CudaGym 2.4.32 with
CuTe DSL 4.7.0 and PyTorch 2.13.0+cu132.

The standalone API passed all six production workloads. Compared with
the previous CuTe API, geometric-mean GPU latency changed by
approximately +0.22%. The device kernel and compile-cache implementation
were unchanged by the API split.

The cache fix reduced calls with new token counts from 309–315 ms to
0.28–0.42 ms once the corresponding aligned/tail variant was compiled.
The first call for each variant still incurs compilation.

The original DeepGEMM comparison above has not been remeasured on this
newer software stack.

### Reproduction

    python benchmarks/bench_grouped_fp8.py --cache-probe
python benchmarks/bench_grouped_fp8.py --production-shapes --backends
cute_dsl

## 🔍 Related Issues

Closes #3712.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Pre-commit checks run through `uvx`.
- [ ] Pre-commit hooks installed locally.
- [x] All changed files pass pre-commit, including mypy and Ruff.

## 🧪 Tests

- [x] 79 focused tests passed on a two-B200 allocation.
- [x] All six production workloads passed correctness checks.
- [x] Tests cover invalid inputs, empty batches, supplied outputs,
streams, device selection, CUDA graphs, cache reuse, concurrent
compilation, and trace correctness.
- [x] Confirmed the existing DeepGEMM function and its checker match the
PR base.
- [ ] Full repository test suite.

Remote validation used the exact changed sources over the production
image’s FlashInfer 0.6.18 supporting dependencies. It was focused
source-overlay validation, not a full clean repository installation.

---------

Co-authored-by: nv-yunzheq <yunzheq@nvidia.com>

### [5ed46a9](https://github.com/flashinfer-ai/flashinfer/commit/5ed46a9ee125f167fd1070be9aa081d70e92b366)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-09-14T21:22:24Z
- **提交信息**: Paged-MQA logits: Rubin (SM107) enablement, FP4 next_n=4, and DKG epilogue/scheduler optimizations (#4737)

## 📌 Description

Three changes to the paged-MQA logits kernels
(`flashinfer.attn_scores`): enable them on Rubin (SM107), support FP4
`next_n=4` on both architectures — natively on Rubin, via an in-kernel
atom split on Blackwell — and port the epilogue/scheduler optimizations
from DKG MR !26202.

### 1. Enable paged-MQA logits on Rubin (SM107)

`fp8_paged_mqa_logits` / `fp4_paged_mqa_logits` refused SM107 outright:
their capability list was `[100, 103]`, so dispatch raised before any
kernel ran. No kernel changes were needed — both CuTe-DSL kernels use
the family-portable tcgen05 surface and compile for `sm_107a` as-is.

The change also separates two questions that were conflated: *does
FlashInfer ship a kernel for this tier* (the capability list) versus
*can the installed CuTe DSL emit code for this device*. A DSL release
predating Rubin fails on `sm_107a` deep inside `cute.compile`; the new
probe rejects that up front, using `native_only=True` because these
kernels need block-scaled `tcgen05` MMA, for which the
family-conditional (`sm_100f`) fallback is not sound.

Multi-GPU correctness note: the kernels' construction-time arch
decisions (the FP4 atom cap, the per-arch optimization gates, the TMEM
column count) are derived from the compile-target arch threaded from the
input tensor's device — not from the DSL's ambient device-0 probe — so
heterogeneous Blackwell+Rubin nodes get the right specialization in both
directions, and nothing arch-dependent is cached under a key that does
not carry it.

### 2. FP4 `next_n=4` (port of DKG MR !25506)

The kernel packs all `next_n` speculative positions into one MMA tile so
the KV cache is streamed once for all of them. The tile's accumulator
lives in TMEM, and `next_n=4` needs 544 columns: over SM100's 512-column
cap, within Rubin's 576 via an exclusive (non-power-of-two) allocation.
So the same shape that is physically impossible on Blackwell runs as a
single direct kernel on Rubin.

Two pieces, both from the upstream MR:

- **Arch-aware TMEM sizing** — below 512 columns the SM100 rule stands
(pow2, min 32); above it, 32-column-aligned exclusive allocation, capped
by `get_max_tmem_alloc_cols(arch)`.
- **In-kernel atom split** — `next_n` decomposes into atoms; the
MMA/TMEM tile is sized by the *atom*, so the atom is what the arch cap
gates. The kernel maps each atom task back onto the native
`block_tables`/`seq_lens` (per-atom context is staggered to reproduce
the unsplit causal masks), which is what lets Blackwell run `next_n=4`
as two atoms of 2 inside one launch, with no page-table duplication and
no context-length rebuild.

This is the follow-up that commit 29ca0629 anticipated when it removed
the old caller-side `next_n=4` split ("the kernel needs to be smarter to
avoid unnecessary tensor creation at runtime"). The in-kernel split
eliminates that removal's per-call tensor costs; the one hazard that
cannot be engineered away — a caller-supplied `schedule_meta` under a
split describes B rows while the kernel iterates B×atoms, which
**hangs** the persistent kernel — is handled by construction:
`compute_paged_mqa_logits_schedule` now takes the call's
`next_n`/`variant` and applies the same internal decomposition, so a
correctly-built caller schedule exists for every configuration (a
mismatched one is caught by the opt-in freshness check); that exact
combination (untested when 29ca0629 found it) now has a test.

The decomposition is a **fixed internal rule, not an API knob**: always
direct, splitting into the minimal legal atoms only where TMEM forces it
(`next_n=4` on SM100/SM103 → two atoms of 2). A forced-decomposition
sweep (batch 1–64, ctx {4K, 16K}, `next_n` {2, 4}, CUDA-graph-timed with
`benchmarks/bench_paged_mqa_logits.py`) on both B100 (SM100) and Rubin
measured direct winning or tying every cell: upstream's wave-count
heuristic would pick small-batch splits that run up to 1.26× slower than
direct here, and finer-than-minimal splits of the forced case lose up to
1.37× at large batch. The small-batch occupancy win that motivates a
shape heuristic upstream does not materialise on this repo's kernels, so
callers state the problem and the library picks the strategy — nothing
shape- or user-dependent survives in the decomposition.

### 3. Epilogue/scheduler optimizations (port of DKG MR !26202)

Five SASS-campaign findings expressed at source level, applied to both
kernels while keeping this repo's epilogue text: paired pipeline polls
(fp8; the two mbarrier round-trips overlap), a loop-invariant TMEM
tiled-copy (the per-task rebuild re-derived invariant copy descriptors
in the hot loop), a flat logits view with a carried row offset (the
store's row term only changes on q-change), a two-level task loop (the
rare q-change/rollover blocks move off the hot path; the task sequence
is replayed exactly), and per-role scheduler state (deriving the
loop-carried scheduler words before the warp-role branches spilled them
to local memory).

Also from that MR, one **correctness** fix: an SFB WAR-closure mbarrier
in the FP4 kernel. At a q transition, warp 0's s2t `tcgen05.cp`
overwrites the SFB TMEM region both UMMA warps' previous-q MMAs read,
and `mma`→`cp` is not a pipelined tcgen05 pair — MMA completion is only
observable via `tcgen05.commit`→mbarrier. Relying on issue-order
completion is unspecified on both architectures, so the closure is
unconditional.

Upstream measured several of these levers as **regressions on Rubin**,
so they carry per-arch auto gates (kernel-internal, deterministic; the
public API is unchanged). One deliberate divergence from upstream's
policy: with this repo's epilogue, both gated levers regress at a next_n
atom of 3 on B200 — the register-pressure maximum (fp32 w-cache cap 56)
— confirmed by ablation (both-on −5%, both-off = baseline), so atom=3 is
gated off too.

### 4. API alignment (breaking, pre-release)

The functions inherited DeepGEMM's vocabulary; they now use
flashinfer's: `seq_lens` / `block_tables` / `max_seq_len` / `q_sf` /
`padded_seq_len()`, with `block_tables` preceding `seq_lens`
positionally as in `trtllm_batch_decode_with_kv_cache`. Old positional
callers fail loudly on the rank checks; old keywords raise TypeError.
Trace templates and committed artifacts were regenerated against the new
signature. `num_epi_subtiles` was removed from both signatures for the
same reason `next_n_atom` never shipped: measured
never-better-than-default at every reachable geometry and
numerics-neutral; the compile layer keeps the parameter and its cache
tag so a future per-shape policy can route a winning value through.

A follow-up consistency pass (a 47-finding audit across every
user-facing surface) finished the job: kernel implementation constants
(`SPLIT_KV=256`, the 128-token compute tile) no longer appear in
user-facing text -- the contracts are expressed through two opaque
sizing helpers, `padded_seq_len()` (output columns) and the new
`min_block_table_width()` (block-table width; this also fixed the
docstring Examples, which under-allocated the table).
`compute_paged_mqa_logits_schedule(next_n=, variant=)` builds the right
schedule on every architecture, replacing the former fp4 `next_n=4`
rejection, so the caller-buffer CUDA-graph pattern works on every
configuration. Vocabulary is uniformly block/seq_lens (the benchmark
flag is now `--seq-len`), and both docstrings carry dtype-annotated
formulas, fused-KV byte-map diagrams with nibble/endianness zoom-ins,
and validated `out=` examples (run verbatim under
FLASHINFER_VALIDATE_INPUTS=1).

### 5. Review follow-ups (Lee Nau's review, 2026-09-11)

Ten threads, each fixed at the layer that owns the constraint, one
commit per root cause:

- **Natural-width block tables** (`ea926adf`): both kernels
tail-predicate the block-table load per column on the row's own
`ceil(seq_len / block_size)` instead of per 128-token compute tile, so
the conventional serving-stack table (SGLang/vLLM `ceil(seq /
page_size)`) is the contract and `min_block_table_width()` collapses to
that width. compute-sanitizer showed the previous kernels reading 4
bytes past a natural-width table's allocation (`seq_lens=[129, 257,
385]`, block 64); 0 errors after. Graph-replay perf on B200 and Rubin is
at parity (interleaved A/B on the noisiest cells). New SGLang-shaped
regression, eager under `FLASHINFER_VALIDATE_INPUTS=1` and under
CUDA-graph replay, plus an opt-in memcheck test.
- **Internal fp8 epilogue policy** (`b2111922`): at `num_heads=32` the
epilogue's weight register cache spilled (Nsight Compute: ~12k local
loads / ~8k local stores per launch at `next_n=6`); a 96-register budget
removes every spill and runs 8-35% faster at `next_n=6` and up to 37%
faster at `next_n=8` on B200/Rubin, bit-identical to the shipped kernel.
Encoded as an internal per-shape rule (`_fp8_epilogue_policy`: fp32
epilogue at `num_heads=32` -> 96-register budget; its fp16 epilogue at
`next_n=6` -> two subtiles; default elsewhere), keyed into the compile
cache and artifact tag; no public knob.
`benchmarks/bench_paged_mqa_logits.py --num-heads 32 --next-n 6`
reproduces the numbers.
- **Contracts enforced only where the kernels have them** (`e1883993`,
`35beee0e`, `37966de2`, `5a1ea510`): `block_tables[::next_n]` and
`seq_lens[::next_n]` views are accepted zero-copy (symbolic strides in
all three compiled kernels; only `block_tables.stride(1) == 1` is
checked); `out=` rows must be distinct storage (`stride(0) >=
padded_seq_len(max_seq_len)`; a pitched `as_strided` or `expand()`ed
view used to return silently wrong logits);
`compute_paged_mqa_logits_schedule` validates rank / dtype / device up
front on every internal path (`[1, B]` used to be accepted silently by
two of them); fp8 `num_heads` must be a multiple of 4, checked at the
API boundary instead of leaking the kernel constructor's
`num_epi_subtiles` message.
- **Split-schedule consistency** (`d57b50aa`, `c197056f`): the
stale-`schedule_meta` error's recipe is the exact call that repairs it
(a test parses and executes it); precompile warms the schedule buckets
the fp4 atom split actually requests (`sched_b64` for `B=32` on
SM100/SM103); a caller-supplied schedule no longer triggers an
unconditional length expansion under capture.
- **Benchmark inputs** (`fdbeb497`): `kv_fused` is built in the API's
fused `[all values][all scales]` layout (the old per-token slice left
66% of fp8 and 11% of fp4 logits non-finite) with a finiteness
self-check over the API-defined output region only (`293768a8`: the
causal tail is unspecified and the fp4 next_n=4 split leaves it
unwritten at seq_len=257; out= is NaN-prefilled so an unwritten defined
cell cannot hide, 257 joins the default grid, and a test pins the
contract) that aborts the sweep on drift.

## 🔍 Related Issues

- DKG MR !25506 (*"Support FP4 paged-MQA next_n=4 on Rubin"*) and MR
!26202 (*"fp8_paged_mqa_logits: port sass-gen (epilogue) optimization
back to cute dsl kernel"*) — the upstream sources.
- Commit 29ca0629 — the deliberate removal of the previous caller-side
split, whose recorded hazards this PR re-verifies one by one.

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

`tests/attn_scores`: **599 passed / 14 skipped on B200 (SM100)**, **598
passed / 15 skipped on Rubin (SM107)**, and **602 passed / 11 skipped on
a two-GPU SM100 pair** (which exercises the cross-device rejection
tests); SM80/89/90/120 skip cleanly (the host-side validation tests pass
everywhere). A fresh-eyes API-usability review round additionally
landed: runnable docstring examples (the fp8 one verified byte-identical
to the test helper's fused-KV layout), the output-validity contract in
the Returns sections, literal-valued Restrictions, a consolidated
CUDA-graph recipe per function, and curated errors for every reachable
failure path (wrong-rank/dtype/device/layout inputs, schedule-helper
input validation, precompile toolchain guards, and a block-table
pool-bounds check under FLASHINFER_VALIDATE_INPUTS). New coverage:
`next_n=4` numerics against the torch reference on both architectures
(direct on Rubin, the in-kernel two-atom split on Blackwell — the only
decompositions that ship); an adversarial zero-work-atom test (a
short-but-nonzero row's leading atoms are zero work under a split, which
must not desync the producer prefetch); the helper-built caller
`schedule_meta` under the split (accepted and equal to the internal
schedule; a default-args schedule is caught by the opt-in freshness
check); and a construction-time arch-gate regression test pinning kernel
specialization to the compile target rather than the ambient device. The
trace suite (template consistency, registry, paged-MQA
reference/checker) passes with the templates and committed artifacts
updated to the multi-arch (`sm100/sm103/sm107`) tags.

Performance — methodology and reproduction are checked in as
`benchmarks/bench_paged_mqa_logits.py` (CUDA-graph replay isolates
device work, which is the timing behind the numbers below; the script
also reports eager wall-clock per call, which on these microsecond
kernels is host-dispatch-bound and several times larger). CUDA-graph
timing vs `main`: the `next_n<=3` Blackwell paths are net faster — the
!26202 port measures **+4.7% geomean on B200 FP4 (up to +11.7%)**, FP8
neutral-to-positive in this harness. The marginal cost of the 4th
speculative position over the 3rd is ~1.20× on Rubin (direct) versus
~1.55× on Blackwell (split, KV read twice); Rubin runs these kernels
~1.7× faster than B200 at serving shapes (SM ratio 1.405×), rising to
2.3–2.4× for FP4 `next_n=4`. On Rubin the !26202 levers measure neutral
(back-to-back ablations; the gates keep upstream's measured regressions
off) — its unconditional benefit there is the SFB WAR fix.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
  - Added FP4 and FP8 paged attention support for Rubin (SM107).
- Enabled FP4 attention with `next_n=4` through automatic
device-specific execution.
- **Performance**
- Improved FP4 and FP8 attention with architecture-aware scheduling and
memory optimizations.
- **Bug Fixes**
- Improved handling of short, empty, and partially processed sequences.
  - Added validation for incompatible schedules during split execution.
- **Documentation**
- Updated attention documentation and architecture metadata to include
Rubin support.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [8c94f70](https://github.com/flashinfer-ai/flashinfer/commit/8c94f70f49fbe17adb5deae5b2b48ff467346863)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-14T19:24:03Z
- **提交信息**: test(kda): xfail CuTe DSL recurrent prefill tests on nvidia-cutlass-dsl<4.7 (#5219)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The CuTe DSL KDA prefill backend is built on `cutlass.experimental`,
which only exists in nvidia-cutlass-dsl>=4.7.0. Tests that import
`kda_chunked_bt16` directly or request `backend="cute-dsl"` explicitly
fail on older DSLs (the library raises ImportError by design; only
`backend="auto"` falls back to Cake). Mark them xfail via the library's
own availability probe (`_is_cute_dsl_kda_runtime_available`),
`raises=ImportError`, `strict=True`. Covers the two tests in #4911 plus
ten more found by sweeping the file on 4.6.3.

## 🔍 Related Issues

<!-- Link any related issues here -->

Fixes #4911.

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

- **Tests**
- Updated KDA prefill test coverage to clearly report expected failures
when the required experimental CuTe-DSL runtime is unavailable.
- Prevents environment-related test failures from obscuring results on
systems using older supported DSL versions.
- Tests continue to run normally when the experimental runtime is
available.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [15e83b7](https://github.com/flashinfer-ai/flashinfer/commit/15e83b7bb9f32d81d84017e2e715c265fb7253f5)

- **作者**: Yan Wang
- **时间**: 2026-09-14T17:51:30Z
- **提交信息**: feat(comm): add allocation-stable head-chunk Ulysses primitives (#5027)

## 📌 Description

This PR adds allocation-stable, head-chunked Ulysses communication
primitives and a benchmark-local compute/communication overlap reference
pipeline.

The change has three layers:

1. **Destination-passing and reusable workspaces**
- Adds `UlyssesWorkspace` and `UlyssesCommunicator.create_workspace()`.
- Extends `scatter_heads()` and `gather_heads()` with optional `out=`
and `workspace=` arguments.
- Preserves the existing allocation-based path when neither argument is
provided.

2. **Head-chunk layout and transport primitives**
   - Adds fused Q/K/V head-band packing and output head-band merging.
- Adds `scatter_qkv_head_chunk()` and `gather_output_head_chunk()`
communicator APIs.
- Supports uneven schedules, positive-stride non-contiguous Q/K/V views,
batch sizes 1 and 2, and caller-selected CUDA streams.
- Adds storage-range alias checks, divisibility checks, int32 payload
limits, and explicit workspace lifetime rules.

3. **Reference composition and benchmark**
- Adds a benchmark-local three-stream reference pipeline that overlaps
input A2A for chunk N+1, attention for chunk N, and output A2A/merge for
chunk N-1.
   - Uses separate input and output process groups/communicators.
- Benchmarks ordinary Ulysses, whole-QKV fusion, sequential head chunks,
and overlapped head chunks.

The framework remains responsible for process-group ownership, model
attention semantics, varlen metadata, schedule selection, and feature
admission. FlashInfer does not inspect or mutate TP/EP/CP configuration
and does not enable head chunking automatically.

### Performance and current-head validation

The original RTX PRO 6000 (SM120/PCIe) speedup table was measured before
`e782390a` changed request-varying Triton divisors and strides from
compile-time
to runtime arguments. I have removed it as a current performance claim.
Those
measurements remain historical motivation in the design document and
will be
promoted again only after the current head is rerun on SM120 hardware.

I reran current head `e782390a` on a 6× NVIDIA B200 node (SM100, NV18
full
mesh). MiniMax H3 has 56 heads, so U2/U4 are legal but U6 is not. Each
row uses
5 warmups and 20 timed iterations in each of three independent
processes; the
table reports median-of-run-medians and median paired speedup. These
rows use
the custom-NVLink communicator and BF16 PyTorch SDPA.

| Physical shape | Ulysses | Schedule | Ordinary | Whole QKV | Whole
speedup | Head-chunk overlap | Overlap speedup |
|---|---:|---|---:|---:|---:|---:|---:|
| `[1,37760,56,128]` | 2 | `[7,14,7]` | 17.732 ms | 19.120 ms | 0.927× |
18.293 ms | 0.974× |
| `[1,37760,56,128]` | 4 | `[2,10,2]` | 8.824 ms | 9.261 ms | 0.953× |
9.173 ms | 0.962× |
| `[1,37888,56,128]` | 2 | `[7,14,7]` | 17.735 ms | 18.889 ms | 0.934× |
18.294 ms | 0.969× |
| `[1,37888,56,128]` | 4 | `[2,10,2]` | 8.745 ms | 9.310 ms | 0.939× |
9.164 ms | 0.956× |

All compared outputs had `max_abs=0`. On this full-NVLink B200 topology,
the
ordinary path is the correct admission choice: communication is already
short,
and the extra pack/merge, events, and smaller attention launches are not
amortized. This is why the PR provides opt-in primitives and leaves
schedule
admission to the framework rather than enabling head chunks
automatically.

For context only, a separate local SM100 distributed-FA4 prototype—not
code in
this PR—uses symmetric K/V push, remote-Q tile loads inside FA4, and
owner-O
scatter in the FA4 epilogue. At the same physical
`[1,37888,56,128]` work domain it reduced U2 from 18.379 to 16.149 ms
(12.13%)
and U4 from 9.266 to 8.182 ms (11.70%). That result supports an
architecture-aware portfolio: share rank-consistent dispatch, workspace
lifetime, and fallback contracts, but contribute the SM100
attention-kernel
fusion as a separate follow-up rather than nesting head chunks around
it.

These are operator/reference-pipeline measurements, not model E2E
results. The
benchmark in this PR treats the physical sequence as dense; production
integrations remain responsible for varlen and padding semantics.

## 🔍 Related Issues

None.

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
- [x] All tests are passing (`unittest`, etc.).

Pre-review validation on RTX PRO 6000:

- Ruff 0.12.8 format and check on all changed Python files.
- Python compile and `git diff --check`.
- 21 single-GPU layout, validation, workspace, and lifecycle tests.
- 12 NCCL W2/W3/W4 correctness, destination-passing, head-chunk, stream,
and fallback tests.
- U8 T2V post-rebase performance/correctness regression: 31.115 ms
ordinary vs. 26.268 ms overlap (1.184×), with `max_abs=0`.

Additional review-fix validation on 4× NVIDIA H200 (SM90, NV18 full
mesh),
using CUDA 12.9, PyTorch 2.13, Triton 3.7.1, and NCCL 2.29.7:

- 9 single-GPU head-chunk layout and validation tests.
- 5 NCCL W2/W4 FP16/BF16 head-chunk and non-default-stream tests.
- 2 custom-NVLink head-chunk and non-default-stream tests, plus W2/W4
  T2V-shape benchmark correctness.
- Whole-fused, sequential-chunk, and overlapped-chunk outputs matched
ordinary
  Ulysses with `max_abs=2.44141e-4` at `[1,37760,56,128]`.

Current-head B200 validation:

- U2/U4 NCCL and custom-NVLink correctness, plus the current-head
performance
  table above; every compared output had `max_abs=0`.
- Latest `tests/comm` CI: 13/17 executed jobs passed; the four
unexecuted jobs
were reported as infrastructure failures on RTX PRO 6000 and B300, with
no
  new test failure classified.

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

- The production scheduler and auto-admission policy intentionally
remain outside the FlashInfer runtime API; `ReferenceHeadChunkPipeline`
is benchmark-only.
- One communicator permits at most one in-flight collective.
Bidirectional overlap uses independent input/output communicators.
- The submitted PRO6000 system has no NVLink. Its historical performance
is no longer presented as current-head evidence; an SM120 rerun remains
required. The custom-NVLink path is functionally validated on H200 and
measured on B200, where head chunks are not admitted for the tested
shapes.
- FP8 attention may be composed above these APIs with BF16
communication, but FP8 communication, TP+Ulysses, Ring Attention,
Attention2D, and CUDA Graph capture are not enabled by this PR.
- Remote-Q loading and owner-O scattering inside FA4 are not implemented
in this PR; that SM100-specific kernel path belongs in a separate
follow-up contribution.
- Review feedback on whether to keep the benchmark/reference composition
in this PR or split it after the reusable workspace and transport
primitives is welcome.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **New Features**
- Added head-chunked Ulysses communication for packing QKV data and
merging output head bands.
- Added reusable workspaces and optional preallocated output buffers to
reduce communication allocations.
- Added fused QKV transfers and efficient head-band scatter/gather
workflows.
- Exported workspace and head-chunk utilities through the communication
API.

- **Documentation**
- Added API and design guidance for workspaces, head-chunk operations,
constraints, and usage.

- **Benchmarks**
- Added comparisons of ordinary, fused, sequential, and overlapped
communication strategies.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Codex Automation <codex-automation@noreply.local>

### [db0cdc2](https://github.com/flashinfer-ai/flashinfer/commit/db0cdc26b0060e7d2419013f9e55bc73ee4b4425)

- **作者**: Mingyang Wang
- **时间**: 2026-09-14T17:31:18Z
- **提交信息**: perf(attention): specialize paged FA2 equal-stride KV (#4736)

## 📌 Description

Paged FA2 currently computes and stores independent V offsets even when
K and V have identical strides. That extra address-generation work
regresses common equal-stride paged decode and prefill workloads.

This change:

- checks the relevant K/V strides once during host dispatch and selects
a compile-time `SAME_KV_STRIDES` specialization;
- reuses the K offsets for V in the equal-stride specialization;
- preserves independent V offsets for unequal-stride layouts, including
asymmetric NVFP4; and
- adds focused coverage to the existing tensor-core decode, batch
prefill, and JIT generator suites.

The stride comparison is host-side dispatch work. It does not add a
per-element branch to the GPU kernel.

## 🔍 Related Issues

https://nvbugspro.nvidia.com/bug/6634590

https://nvbugspro.nvidia.com/bug/6634592

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
- [ ] All tests are passing (`unittest`, etc.). Full repository CI is
pending; the focused validation below passed.

Focused validation on B300/SM103:

- JIT specialization test: 1 passed.
- Equal-stride tensor-core decode and paged prefill correctness tests: 2
passed.
- Reference-checked acceptance matrix:

| Workload | Target backend | Median | Gate |
| --- | --- | ---: | ---: |
| Llama-4 Scout | `fa2_tc` | 0.334 ms | ≤ 0.3675 ms |
| Llama-3.1 70B | `fa2_tc` | 0.336 ms | ≤ 0.3675 ms |
| GPT-OSS | `fa2` | 1.355 ms | ≤ 1.446 ms |

All matrix cases returned zero with reference checking enabled and no
mismatch diagnostics. CUPTI was unavailable, so benchmark timing used
CUDA events. Unsupported control backends were skipped.

## Reviewer Notes

The extra compile-time specialization increases generated build
artifacts. Qualification measured approximately +26.9% aggregate object
bytes and +33.2% shared-library bytes, with unchanged generated
source/module counts. This is the main tradeoff for recovering the
equal-stride runtime performance.

POD and batch-POD callers retain the conservative independent-stride
default unless they explicitly select the new specialization.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added support for paged key/value caches with independent memory
layouts and strides.
- Added automatic routing between matching- and independent-stride
execution paths.
- Added lazy loading and optional prewarming of stride-specific variants
before CUDA graph capture.
- Extended support across batch prefill, decode, cascade, shared-prefix,
POD, and block-sparse workflows.

- **Bug Fixes**
- Improved correctness for bfloat16 paged prefill and tensor-core
decoding, including grouped query attention.

- **Tests**
- Added coverage for routing, reuse, CUDA graphs, compilation, and
reference-output correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5d0c89e](https://github.com/flashinfer-ai/flashinfer/commit/5d0c89eacae6ca08f2a1ce92eba557bbad7a1bfc)

- **作者**: Alex Yang
- **时间**: 2026-09-14T11:01:33Z
- **提交信息**: feat(moe): tag the unified MoE API as official with @flashinfer_api (#5200)

<!-- .github/pull_request_template.md -->

## 📌 Description

Promotes the unified MoE API to an official FlashInfer API by tagging it
with `@flashinfer_api`.

The unified MoE API was deliberately left untagged while it matured.
FlashInfer intends lower-level component APIs and higher-level unified
APIs to **co-exist** — this is a maturity milestone, not the correction
of an oversight, and neither layer supersedes the other.
`docs/design_docs/flashinfer_moe_api.md` recorded adding
`@flashinfer_api` as an explicit release-time gate; this closes it.

**Exactly two entry points are tagged:**

| entry point | signature |
|---|---|
| `MoELayer.__init__` | `(self, config: MoEConfig, device:
Optional[torch.device] = None)` |
| `MoELayer.__call__` | `(self, act_pack: MoEActivationPack,
weight_pack: MoEWeightPack) -> Union[torch.Tensor, List[torch.Tensor]]`
|

Everything else in the surface is deliberately **not** tagged: the
config dataclasses (`MoEConfig`, `QuantConfig`, `RoutingConfig`,
`ExpertConfig`, `ActivationConfig` and subclasses, `MoEFinalizeConfig`,
`ExecutionConfig`, the per-backend `*Config` types) are frozen data
rather than callables, and the `TunableRunner` methods are driven by the
autotuner in a tight per-tactic loop where per-call logging would be
actively harmful.

### Two supporting changes — required, not cosmetic

**`flashinfer/api_logging.py`** — `MoELayer` joins the class-name prefix
list. Its entry point is `__call__`, so without the prefix every
unified-MoE call logs as a bare `__call__`: unreadable, and useless as a
`FLASHINFER_DUMP_INCLUDE` / `FLASHINFER_DUMP_EXCLUDE` pattern since it
would also match any other decorated `__call__`.

**`flashinfer/fused_moe/api.py`** — metadata-only `__repr__` on
`MoEActivationPack` and `MoEWeightPack`. These are the arguments of the
newly decorated `__call__`, and they are **dataclasses holding CUDA
tensors**. The logging guards against `str()`/`repr()` on tensor-bearing
containers are keyed on the concrete `list`/`tuple`/`dict` types, so a
dataclass falls through to the generic `repr` fallback in both
`_format_value` (level 3+ logging) and `_serialize_value` (level-10 dump
metadata). Tensor `repr` reads device memory and **can invalidate CUDA
graph capture**. Fixing it at the source covers every consumer rather
than special-casing two pack types inside the shared logger. Non-tensor
values fall back to `repr` instead of assuming `.shape`, so an unrelated
debugger inspection cannot raise.

### Documentation

`MoELayer` appeared only in an `autosummary` stub, so `__call__` — a
dunder — never rendered. This adds an explicit `.. autoclass::` with
`automethod` for both entry points, matching the pattern already used
for the `CuteDsl*` wrappers in the same file, plus a short note that the
two API layers co-exist by design.

`scripts/pr_checks/check_api_docs` is unchanged at **MISSING 0**. (STALE
48 is pre-existing debt on `main`, predominantly `flashinfer.comm`;
untouched here.)

## 🔍 Related Issues

Closes the `@flashinfer_api` release gate recorded in
`docs/design_docs/flashinfer_moe_api.md`.

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

Verified: `py_compile`, `mypy`, `ruff check`, `ruff format`, and the
full pre-commit hook set, plus `scripts/pr_checks/check_api_docs`. No
behavioural change — `@flashinfer_api` is zero-overhead at the default
`FLASHINFER_LOGLEVEL=0`.

## Reviewer Notes

**Deliberately not included: the `trace=` argument** from CLAUDE.md's
Trace Template Checklist. Two reasons, both worth a reviewer's opinion:

1. `TraceTemplate` models **flat tensor argument lists** (`axes` /
`inputs` / `outputs` as `Tensor`/`Scalar`/`Var` specs, with `init`
building flat kwargs). `MoELayer.__call__` takes **pack dataclasses**.
Wiring `trace=` therefore means either extending the trace machinery to
model packs, or writing a flattening adapter — a design change rather
than wiring, and better reviewed on its own.
2. The checklist's mandatory steps — regenerating
`tests/trace/fi_trace_out/` via `python tests/trace/example.py` and
running `pytest tests/trace/` — need a torch environment that was not
available while preparing this change. Committing a `TraceTemplate`
whose generated JSON had not actually been regenerated would be worse
than deferring it.

Raising it explicitly so the deviation is deliberate and visible rather
than silent. Happy to land it as a follow-up, or to fold it in here if a
reviewer would rather not split them.

**Keyword-only guard (included — this section previously said
otherwise).** `RoutingConfig` and `ExpertConfig` each gain a trailing
`_: KW_ONLY` sentinel. It is placed **at the end**, with no fields after
it, so it is a **no-op today**: every existing field keeps its current
binding and `RoutingConfig(8, 2)` still binds positionally. Only fields
*appended below* the sentinel become keyword-only, which is the growth
this is meant to make safe — inserting or appending a field can
otherwise silently rebind an existing positional argument at a call site
that still type-checks. `QuantConfig` already carries the same guard
from #5061.

Corrections to an earlier revision of this description, both caught in
review: it claimed the keyword-only change was "not in this PR" (it is),
and it quoted field counts of 12 / 8 for `RoutingConfig` /
`ExpertConfig` — the real counts on this branch are **6** and **4**. The
inflated numbers came from a script that counted docstring `Parameters`
entries alongside real fields.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Documentation**
- Added API documentation for `MoELayer`, including initialization,
invocation, instrumentation, and lower-level interfaces.
- Updated design documentation covering logging, tracing, and
tensor-dump behavior.

- **Improvements**
  - Improved operation logging and diagnostics for `MoELayer`.
  - Added concise metadata displays for MoE activation and weight data.
- Updated configuration constructors so selected optional settings are
keyword-only.

- **Tests**
  - Added coverage verifying class-specific operation names in logging.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4391
- **最后更新**: 2026-09-15T00:01:46Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Yaegaki1Erika, William Lin, Lele

## AI分析总结

## 1. 主要更新类型

本批次共 4 条提交，以 **Bug 修复为主（3 条）**，辅以 **1 条文档更新**，无新功能或性能优化：

- MiniMax H3 帧数边界修复
- Parquet 数据加载器 dtype 修复
- Wan I2V 在序列并行下的 DMD 条件修复
- AGENTS.md 文档地图刷新

## 2. 关键变更点及与项目方向的关系

- **MiniMax H3 帧填充（15 秒上限）**：将 `MINIMAX_H3_MIN/MAX_ALIGNED_FRAMES` 常量提升到 `align_num_frames` 附近，并在 CUDA 阶段、MLX 运行时、LoRA 示例中统一复用，接受因果 VAE 对齐的 362 帧桶（15.083 秒）。这体现了 FastVideo 对**多后端一致性（CUDA/MLX）**和**入口统一**的追求。
- **Wan I2V DMD 条件修复**：此前仅沿时间轴预分片图像条件，而噪声仍为全长，导致 `sp_world_size > 1` 时拼接失败。改为传入全长 mask+latent 条件，由 transformer 在 patch embedding 后自行分片。这直接服务于项目的**序列并行（SP）能力**，是分布式推理正确性的关键。
- **Parquet dtype 修复**：尊重序列化张量的 dtype，属于数据管道健壮性改进。
- **AGENTS.md 刷新**：补充 Wan SP/I2V 与 CI 测试说明，改善协作与可维护性。

## 3. 对项目的影响和潜在意义

- 修复了**分布式场景下的静默错误**（Wan I2V SP），避免多卡推理结果错误，对生产可用性意义重大。
- MiniMax H3 边界放宽使 15 秒请求不再被误拒，提升**用户体验与 API 兼容性**。
- 常量集中化降低了多入口漂移风险，是**工程规范化**的积极信号。
- 文档更新有助于新贡献者快速理解测试与并行结构。

## 4. 值得关注的技术点

- **因果 VAE 帧对齐**：362 帧对应 15.083 秒，说明帧数需按 VAE 时间压缩比对齐，而非简单取整。
- **序列并行下的条件拼接顺序**：需在 transformer 的 `(bs, c, t, h, w)` 布局中拼接，且分片职责从 pipeline 转移到 transformer。
- **已知缺口**：362 帧桶无 GPU 通道覆盖（SSIM 仅跑 124 帧），且显式 `num_frames=360` 仍会触发旧的网格门限，提示测试覆盖与边界逻辑仍有遗留问题。

## 5. 结合 README 背景的影响

FastVideo 定位为**高效视频生成框架**，强调快速推理、多后端（CUDA/MLX）与分布式能力。本批次提交虽小，但精准修补了分布式并行（SP）与多后端一致性这两条核心链路，并放宽了 MiniMax H3 的时长边界，直接支撑 README 中“快速开始/推理”场景的可靠性。文档与常量统一则强化了项目的可维护性，为后续扩展更多模型与并行策略打下基础。整体看，这是一次**以稳定性与正确性为导向**的维护性更新，符合项目从“能跑”向“跑得对、跑得稳”演进的阶段特征。

## 详细提交记录

### [316f387](https://github.com/hao-ai-lab/FastVideo/commit/316f3876c2ec13ebd25d435d814a94b6354e938e)

- **作者**: Lele
- **时间**: 2026-09-14T23:54:41Z
- **提交信息**: [bugfix]: allow MiniMax H3 frame padding at the 15-second limit

Accept the causal-VAE-aligned 362-frame bucket (15.083 s) for 15-second H3 requests.

- Hoist MINIMAX_H3_MIN/MAX_ALIGNED_FRAMES next to align_num_frames and reuse them in the CUDA stage, the MLX runtime, and the LoRA example so the bound is consistent across entry points.
- State the accepted frame range in the error messages.
- Cover seconds="15" -> 362 at OpenAI admission and the MLX resolve_geometry bound.
- Update the Spark/openai cookbook frame caps from 345 to 362.

Known gaps: no GPU-lane coverage for the 362 bucket (SSIM runs 124 frames; the golden gate is a fixed-geometry fingerprint), and explicit num_frames=360 still hits the pre-existing grid gate.

### [614b595](https://github.com/hao-ai-lab/FastVideo/commit/614b59543c40f56990dde2e55930635f9125c31d)

- **作者**: Yaegaki1Erika
- **时间**: 2026-09-14T23:34:25Z
- **提交信息**: [bugfix]: respect serialized tensor dtype in parquet dataloader (#1843)

### [1c14afd](https://github.com/hao-ai-lab/FastVideo/commit/1c14afd5599a0033d2ffe5db75a4b0d1106b5c58)

- **作者**: William Lin
- **时间**: 2026-09-14T23:06:53Z
- **提交信息**: [docs]: refresh AGENTS.md maps and add Wan SP/I2V and CI test notes (#1845)

### [9a3c457](https://github.com/hao-ai-lab/FastVideo/commit/9a3c45779cd4f869e619913076037b4519a5332b)

- **作者**: Yaegaki1Erika
- **时间**: 2026-09-14T22:58:13Z
- **提交信息**: [bugfix]: fix Wan I2V DMD conditioning under sequence parallelism (#1844)

The pipeline pre-sharded only the image conditioning along the temporal axis while the noise input stayed full-length, so concatenation could not match for sp_world_size > 1. WanTransformer3DModel shards the flattened token sequence after patch embedding, so pass full-length mask+latent conditioning and let the transformer shard.

Also reads temporal_compression_ratio from the VAE config, simplifies the conditioning mask, concatenates in the transformer's (bs, c, t, h, w) layout, and adds unit coverage.

Co-authored-by: Yaegaki1Erika <70182590+Yaegaki1Erika@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34511
- **最后更新**: 2026-09-14T20:16:38Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yiming Zhao, iridescentWen

## AI分析总结

# 昨日提交分析（huggingface/diffusers，共 2 条）

## 1. 主要更新类型
- **功能新增**：Cosmos3 引入混合精度去噪（W8A8/W8A16）支持 ModelOpt FP8 检查点。
- **文档修复**：修正多处 docstring 中与实际参数名不符的引用（拼写错误、重命名遗留）。
- 整体属于“量化推理能力增强 + 文档质量维护”的组合。

## 2. 关键变更点与项目方向
- 为 Cosmos3 视频生成模型增加**可选**的混合精度调度：中间步用原生 ModelOpt GEMM（W8A8），首尾步切换为反量化线性 W8A16，使 CFG 的 cond/uncond 在同一调度步共享精度。
- 精度调度从检查点的 `transformer/config.json` 的 `diffusion_step_policy` 读取，而非硬编码窗口；蒸馏 FP8 模型保持原生 W8A8。
- 加载逻辑加固：当运行时 ModelOpt 配置缺失时回退读取磁盘配置，策略不完整时“失败关闭”，并允许 W8A16 路径使用 FP32 激活。
- 非 ModelOpt 后端（如 TorchAO）保持原生 forward，不受影响。
- 文档修复覆盖 LTX2、DiffEdit、优化器、VAE 等模块的参数名一致性。

这与 diffusers 持续强化**大模型量化推理、视频生成支持、多后端兼容**的方向一致。

## 3. 对项目的影响与潜在意义
- 提升 Cosmos3 FP8 检查点在多步视频去噪中的**稳定性**（减少闪烁），同时保留速度优势。
- 通过“策略驱动”而非硬编码，使不同 Hub 上的 FP8 检查点能各自声明精度调度，增强可扩展性与正确性。
- 文档修复降低用户误用 API 的风险，提升库的可靠性口碑。

## 4. 值得关注的技术点
- W8A8 与 W8A16 的**按步切换**策略，以及 CFG 精度一致性设计。
- “fail closed” 的配置加载策略，避免静默降级。
- 明确区分 ModelOpt 与其他量化后端的行为边界。
- 官方 Hub FP8 调度文档的补充。

## 5. 结合 README 背景的项目发展影响
diffusers 定位为扩散模型工具箱，强调多模型、多后端与易用性。本次提交在**推理性能与数值稳定性**上进一步细化，尤其针对视频生成这一高成本场景，符合其向生产级推理优化的演进路径；文档修复则维护了其作为公共库的 API 严谨性。整体对项目发展是正向的增量改进。

## 详细提交记录

### [759164b](https://github.com/huggingface/diffusers/commit/759164b7ad116e091e9d3e222211c9aa27d835f6)

- **作者**: Yiming Zhao
- **时间**: 2026-09-14T20:16:31Z
- **提交信息**: [Cosmos3] Mixed W8A8/W8A16 denoising for ModelOpt FP8 checkpoints (#14664)

* Add opt-in mixed W8A8/W8A16 denoising for Cosmos3 ModelOpt FP8 checkpoints.

Keep native ModelOpt GEMM on middle steps and dequant-linear W8A16 on the first/last steps so CFG cond/uncond share one precision per scheduler step.

* Read Cosmos3 mixed-precision schedule from the checkpoint policy.

Enable first/last W8A16 only when transformer/config.json declares diffusion_step_policy, so distilled FP8 stays native W8A8 instead of inheriting a hardcoded 3+3 window.

* Harden Cosmos3 mixed-precision loading and document official Hub fp8 schedules.

Read the checkpoint runtime policy from on-disk transformer/config.json when the live ModelOpt config omits it, fail closed on incomplete policies, and allow FP32 activations on the W8A16 path.

* Address review: simplify FP8 mixed docs, no-op non-ModelOpt backends, drop unit tests.

W8A8/W8A16 is explained without listing call-site overrides; TorchAO and other
quantizers keep their native forwards; focused tests are removed until Hub fp8
usage is clearer.

* Document FP8 mixed default vs none trade-offs without ModelOpt restore boilerplate.

Keep serialized restore in the ModelOpt guide and spell out that all-W8A8 is faster but can flicker on multi-step video.

* Apply style fixes

* Regenerate Cosmos modular auto docstrings for mixed-precision inputs.

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

### [1f7be81](https://github.com/huggingface/diffusers/commit/1f7be81f9bc84e7f2ab1ae91d37c7236c4c15691)

- **作者**: iridescentWen
- **时间**: 2026-09-14T17:06:21Z
- **提交信息**: docs: fix two docstrings that reference names the code does not have (#14733)

* docs: fix two docstrings that reference names the code does not have

- transformer_ltx2.py:1449 says `peturbation_mask`; the parameter is
  `perturbation_mask`, spelled correctly at :253, :273, :314, :316, :623.
- pipeline_stable_diffusion_diffedit.py:885,:888 point at `source_image`,
  but generate_mask's image argument is `image`.

Fixes #14732

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

* docs: fix three renamed parameters left stale in docstrings

Each documents a name the signature no longer has:

- optimization.py:161      num_periods        -> num_cycles
- autoencoder_kl_ltx2.py:43 dim               -> channel_dim
- z_image/before_denoise.py:100 vae_scale_factor -> vae_scale_factor_spatial

Co-Authored-By: Claude Opus 5 (1M context) <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
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


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13107
- **最后更新**: 2026-09-14T19:03:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 昨日提交分析（第 1/1 批）

## 1. 主要更新类型
- **Bug 修复**：本次提交为 `fix audio loading bugs (#1690)`，属于针对音频加载模块的缺陷修复，不涉及新功能或重构。

## 2. 关键变更点及与项目方向的关系
- 修复了音频加载环节的 bug，说明 DiffSynth-Studio 在扩散模型推理流程中已涉及音频模态的处理（如音频生成或音视频联合生成场景）。
- 项目整体方向是提供统一的扩散模型推理与训练框架，覆盖图像、视频乃至音频等多模态生成能力。音频加载的稳定性是保证多模态 pipeline 端到端可用的基础环节，此次修复与项目“多模态扩散引擎”的定位一致。

## 3. 对项目的影响和潜在意义
- 直接提升音频相关推理/训练流程的可靠性，避免因加载异常导致的崩溃或错误输出。
- 对使用音频功能的用户而言，降低了使用门槛和调试成本，有助于提升框架在音频生成场景下的口碑与采用率。
- 属于维护性修复，不改变公共 API，风险较低，但对多模态功能的完整性有实际价值。

## 4. 值得关注的技术点
- 音频加载 bug 的具体成因（如采样率、格式兼容、路径处理、张量维度等）值得从 PR #1690 的 diff 中进一步确认。
- 该修复是否伴随测试用例补充，可反映项目对音频模块的测试覆盖程度。
- 音频与扩散模型的结合方式（如 latent 表示、条件注入）是 DiffSynth-Studio 区别于纯图像框架的技术亮点。

## 5. 基于 README 背景的项目发展影响
- README 显示 DiffSynth-Studio 定位为面向扩散模型的全流程工具链，强调易用性与多模态支持。此类音频 bug 修复虽小，却是维持“开箱即用”体验的必要维护动作。
- 持续修复边缘模态问题，有助于项目从图像/视频主战场向音频等更广场景稳健扩展，巩固其在开源扩散生态中的综合竞争力。
- 整体来看，本次提交是常规质量维护，对项目长期演进起到“补短板”作用，而非方向性调整。

**小结**：这是一次低风险、高必要性的音频模块修复，体现了项目在多模态扩散推理上的持续打磨，对提升框架稳定性与用户信任具有积极意义。

## 详细提交记录

### [c458cb4](https://github.com/modelscope/DiffSynth-Studio/commit/c458cb42ab1ee838bff85c6546e14bb01c3571e9)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-14T11:03:07Z
- **提交信息**: fix audio loading bugs (#1690)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 35956
- **最后更新**: 2026-09-15T00:29:16Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 17
- **主要提交者**: Richard Wang, cctry, Qiaolin Yu

## AI分析总结

# sglang 昨日提交分析（共 19 条）

## 1. 主要更新类型

- **Bug 修复为主**：约 8 条，集中在 KV 缓存释放、PD 重引导、NPU 设备不匹配、HiCache 指针别名、DeepSeek V4 K 缓存读取时序等。
- **平台适配与 CI**：AMD（gfx950/gfx95、MI355X、GLM-5.2 MXFP4）与 NPU（CANN 9.1.0、Ascend a5、多节点 e2e）共 6 条。
- **功能/性能优化**：投机解码预填充共享读、QSA 压缩 gather 钳制、chunked-prefill 计算预算精确填充。
- **工程维护**：依赖版本升级（sgl-deep-gemm 0.2.0）、代码所有权与 CI 权限、日志降级、一次批量 revert。

## 2. 关键变更点与项目方向

- **KV 缓存正确性**：`f81fbc7` 合并相邻 KV-row 释放，避免 DCP 下页中分裂导致的双重释放；`2123aca` 在读取 DeepSeek V4 K 缓存位置前等待 PDL。这延续了 sglang 作为高性能推理引擎对内存安全与多并行策略（DCP/PD）一致性的高要求。
- **PD 分离与重引导**：`5c2de3f` 在 rebootstrap 时保留 prefill rank，直接服务于 PD 解耦架构的稳定性。
- **投机解码**：`9128d57` 允许投机 worker 暂存 prefill 共享读，是 Spec 推理路径的进一步优化。
- **AMD 生态深化**：`5aa9b8f` 在 gfx950 上启用 fp8 双池 unified_kv，`95140a7` 补齐 MI355X PD 三种策略文档，显示 AMD 正从"能跑"走向"生产级配方"。
- **NPU 持续投入**：CANN 9.1.0 与 Ascend a5 nightly 套件、SWA mask 修复，表明昇腾是重点支持后端。

## 3. 对项目的影响与潜在意义

- 多项修复针对**分布式/多卡边界条件**（DCP 双重释放、PD rank、PDL 时序），降低长稳运行下的崩溃与数据损坏风险，对生产部署意义重大。
- AMD/NPU 的 CI 与镜像升级提升了**跨硬件可复现性**，有助于扩大用户基础。
- 一次批量 revert（`66c7bc8`）与随后 reland（`d72e595`）说明团队对回归保持谨慎，采用"先回退再修复重提"的稳健流程。

## 4. 值得关注的技术点

- **PDL（Programmatic Dependent Launch）** 与 DeepSeek V4 K 缓存的时序耦合，是 GPU 异步执行正确性的典型案例。
- **DCP 下页中分裂释放**：KV 缓存分页管理与分布式并行的交互，是易被忽视的隐蔽 bug 源。
- **fp8 双池 unified_kv**：在 gfx950 上统一 KV 池的 fp8 支持，涉及精度与显存布局权衡。
- **chunked-prefill 预算精确填充**：直接影响吞吐与延迟平衡。

## 5. 结合项目背景的发展意义

sglang 定位为面向大模型与多模态的高性能服务框架，强调 RadixAttention、PD 解耦与多硬件后端。本批提交延续三条主线：**正确性加固**（KV/PD/时序）、**硬件广度**（AMD、NPU 双线推进）、**推理效率**（投机解码、chunked-prefill）。整体看，项目正从功能扩张转向**生产级稳定性与多平台成熟度**，这对吸引企业级部署和巩固其在 vLLM 之外的高性能推理生态位具有积极意义。

## 详细提交记录

### [6e755e4](https://github.com/sgl-project/sglang/commit/6e755e411440bb3e42df59a9d0bc4e250615cf09)

- **作者**: faceless void
- **时间**: 2026-09-14T23:18:56Z
- **提交信息**: [Logging] Downgrade missing TokenizerManager request state log to warning (#36625)

Signed-off-by: syd520zy <529477025@qq.com>

### [0163f8f](https://github.com/sgl-project/sglang/commit/0163f8ff74c3d8f32e364e2b812d24dc715af039)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-09-14T22:49:05Z
- **提交信息**: [AMD] Fix registered HiCache host pointer aliases (#35233)

### [2fca6d6](https://github.com/sgl-project/sglang/commit/2fca6d69aa9347a8230aff3443dfc69cb7639cf2)

- **作者**: Baizhou Zhang
- **时间**: 2026-09-14T22:30:31Z
- **提交信息**: bumping sgl-deep-gemm to 0.2.0 (#39371)

### [710a044](https://github.com/sgl-project/sglang/commit/710a044caf9f95a4f0bd8ff5485c6f6f6ea2ef1e)

- **作者**: Richard Wang
- **时间**: 2026-09-14T22:27:15Z
- **提交信息**: [dLLM] Add rwang5203 as code owner and grant CI permissions (#39483)

Co-authored-by: Richard Wang <11150595+rwang5203@users.noreply.github.com>

### [dad8c07](https://github.com/sgl-project/sglang/commit/dad8c074e76de83d8e39242aec49d7499181fa83)

- **作者**: cctry
- **时间**: 2026-09-14T22:03:03Z
- **提交信息**: Scope prefetch cache state to the request attempt (#39318)

### [d72e595](https://github.com/sgl-project/sglang/commit/d72e59508b7554045cb51827f9b8d0f08c7a3abc)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-14T21:05:41Z
- **提交信息**: Reland fix(qsa): clamp the compress gather to the rows (#38346) (#39446)

Co-authored-by: ehuaa <ehuamail1@gmail.com>

### [9128d57](https://github.com/sgl-project/sglang/commit/9128d5796614c1c29b5a1f757f2cd220d5f1af46)

- **作者**: paulzhang-tm
- **时间**: 2026-09-14T21:03:27Z
- **提交信息**: [Spec] Allow speculative workers to stage prefill shared reads (#38554)

### [5c2de3f](https://github.com/sgl-project/sglang/commit/5c2de3f35567ffceec6cea86ba18e075692e9101)

- **作者**: Byron Hsu
- **时间**: 2026-09-14T16:20:37Z
- **提交信息**: [PD] Preserve the prefill rank during rebootstrap (#39357)

Co-authored-by: Byron Hsu <byronhsu@users.noreply.github.com>

### [7465e42](https://github.com/sgl-project/sglang/commit/7465e42b7a1238761742f81a500046c1df6decc1)

- **作者**: pllimax
- **时间**: 2026-09-14T14:39:42Z
- **提交信息**: [NPU][CI] Add CANN 9.1.0 and Ascend a5 nightly suites (#38833)

### [433c999](https://github.com/sgl-project/sglang/commit/433c999dd061d6f72beab3d35005535c8c5435d7)

- **作者**: pllimax
- **时间**: 2026-09-14T14:23:47Z
- **提交信息**: [NPU][CI] Fix sglang.test.ascend import failure in multi-node e2e pods (#39403)

### [242d8a7](https://github.com/sgl-project/sglang/commit/242d8a70c05bce1aace1e361000bb2f8b4f85469)

- **作者**: ChangLiu0709
- **时间**: 2026-09-14T13:50:52Z
- **提交信息**: [AMD] GLM-5.2 MI355X MXFP4: bump image to 20260913, enable TOPK_V2 (#39406)

### [d5f1c59](https://github.com/sgl-project/sglang/commit/d5f1c593c160ad817ef1eeb8a0c701ef6ebb462b)

- **作者**: pllimax
- **时间**: 2026-09-14T13:48:50Z
- **提交信息**: [NPU] Remove temperature/top_p from Qwen3.5-397B-A17B perf test (#39047)

### [f81fbc7](https://github.com/sgl-project/sglang/commit/f81fbc749abc099242b1b46abb1b4c55c4b57c76)

- **作者**: Kurt Shuster
- **时间**: 2026-09-14T13:44:32Z
- **提交信息**: [Fix] Merge adjacent KV-row frees so a mid-page split under DCP cannot double-free (#38941)

### [2123aca](https://github.com/sgl-project/sglang/commit/2123aca87e0f486d7843e50c5dd6928409bd9bb1)

- **作者**: Aurick Qiao
- **时间**: 2026-09-14T13:04:28Z
- **提交信息**: [Fix] Wait for PDL before reading DeepSeek V4 K cache locations (#38409)

Co-authored-by: Aurick Qiao <6137920+aurickq@users.noreply.github.com>

### [87db743](https://github.com/sgl-project/sglang/commit/87db74302151956e354a05c01ecda47fd24cb882)

- **作者**: iridiumine
- **时间**: 2026-09-14T11:36:33Z
- **提交信息**: [NPU] Fix device mismatch in SWA mask for DSpark verify graph capture (#39353)

### [66c7bc8](https://github.com/sgl-project/sglang/commit/66c7bc838e7c9d799af706eb40042d3414fc1ce0)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-14T10:04:07Z
- **提交信息**: [misc] Revert #38346, #33426, #39061 and #39219 (#39405)

### [5aa9b8f](https://github.com/sgl-project/sglang/commit/5aa9b8fb3ec9081f9a7e21f7996d4bd9a503bbcb)

- **作者**: amd-danli103
- **时间**: 2026-09-14T09:49:11Z
- **提交信息**: [AMD][DSV4] feat: enable fp8 two-pool unified_kv on gfx950 (#37413)

### [95140a7](https://github.com/sgl-project/sglang/commit/95140a7b0c9fc2f87a2a6cf6f6f0df8640a73174)

- **作者**: Theresa Shan
- **时间**: 2026-09-14T09:11:51Z
- **提交信息**: [docs] DeepSeek-V4: MI355X PD disaggregation recipes for all three strategies (#39396)

### [5200508](https://github.com/sgl-project/sglang/commit/5200508b0fd25733752c2c5e3af5539508023c27)

- **作者**: Jacob0226
- **时间**: 2026-09-14T07:35:15Z
- **提交信息**: [AMD][gfx95] Fill the chunked-prefill compute budget exactly (#32888)

Co-authored-by: Thomas Wang <thomawan@amd.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1275
- **最后更新**: 2026-09-10T02:30:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 91754
- **最后更新**: 2026-09-15T00:34:28Z

## 提交统计

- **昨日提交总数**: 51
- **提交者数量**: 43
- **主要提交者**: Jiangyun Zhu, Giancarlo Delfin, Nicolò Lucchesi

## AI分析总结

# vLLM 昨日提交分析总结（共51条）

## 1. 主要更新类型分布

- **性能优化（约14条）**：占比最高，集中在 ROCm/DeepSeek-V4、GLM-5.3-Flash、量化内核（FP8/W4A16）、稀疏注意力等方向。
- **Bug修复（约18条）**：覆盖面广，涉及 Rust 前端、KV Offload、多模态、CPU 后端、模型加载等。
- **功能新增（约8条）**：新模型支持（Nanbeige4.2）、水印控制、Scale-out 端点、SWA 指标支持等。
- **CI/测试（约7条）**：CI 新鲜度检查、CPU 投机解码覆盖、cudagraph 单测初始化等。
- **文档/重构（约4条）**：PromQL 示例修正、LoRA 钩子统一、emeritus 提交者变更。

## 2. 关键变更点与项目方向

- **性能持续深挖**：GLM-5.3-Flash 的 FlashKDA 分块预填（提速1.7-3.8倍）、Dense/masked-MHA 稀疏预填、Gemma3n 稀疏 GELU Triton 内核、ReLU2 与 FP8 量化融合——体现 vLLM 对"Easy, fast, cheap"中 **fast** 的极致追求。
- **量化后端精细化**：按量化类型选择线性后端、W4A16 零点保持4-bit 打包，说明量化生态正从"能用"走向"按场景最优"。
- **Rust 前端持续成熟**：水印控制透传、logprob 模式保留、多模态占位符对齐、prost 依赖修复——Rust 前端正逐步补齐与 Python 前端的功能对等。
- **MRV2/Model Runner V2 演进**：池化后处理跨 PP rank、自适应验证的接受率估计、Proton CUDA graph 归因——新一代运行时架构在可观测性和分布式正确性上稳步推进。
- **安全加固**：benchmark 日志凭据脱敏、Qwen-VL 视频采样上限、水印 e2e 与 GSM8K 质量测试——安全与合规被提升到显式议程。

## 3. 对项目的影响与潜在意义

- 大量 ROCm/AMD 相关优化（CSA 多流重叠、MoRI-IO 连接器、W4A16）表明 vLLM 正**强化非 NVIDIA 硬件生态**，降低单一硬件依赖。
- KV Offload、Mooncake、NixlPush 等连接器修复，直接关系到**分布式推理与 KV 缓存复用**的稳定性，是规模化部署的关键。
- 水印功能从"有"到"可控制、可测试、可验证"，为**合规化商用**铺路。
- CI 新鲜度检查与多项单测修复，反映项目在高速迭代下对**回归防护**的重视。

## 4. 值得关注的技术点

- **FlashKDA 替代 Triton 分块路径**：1.7-3.8倍提速，可能成为长上下文预填的新默认。
- **mHC post 折叠进延迟预投影**：ROCm 与通用路径同步优化，体现跨后端协同。
- **按量化选择线性后端**：架构层面的可扩展设计，未来可支持更多量化方案。
- **自适应验证接受率估计**：投机解码的动态调优，对推理吞吐有直接收益。
- **Rust 前端多模态占位符对齐**：跨语言前端一致性的难点，值得跟踪其长期方案。

## 5. 结合 README 的项目发展影响

README 定位 vLLM 为"Easy, fast, and cheap LLM serving for everyone"。本批提交高度契合这一定位：**fast** 由密集的性能内核与量化优化支撑；**cheap** 体现在 KV 缓存复用、CPU 后端修复与投机解码覆盖，降低部署成本；**for everyone** 则由 ROCm/CPU 多硬件支持、Rust 前端与安全加固共同保障。整体看，项目正从"支持更多模型"转向"在更多硬件上更快、更稳、更安全地服务"，进入**深度优化与工程化成熟期**。

## 详细提交记录

### [bbbd0a0](https://github.com/vllm-project/vllm/commit/bbbd0a02c9d1bec965ee818af29a1319baefa69c)

- **作者**: zhaoguochun1995
- **时间**: 2026-09-14T23:52:20Z
- **提交信息**: [Bugfix] Carry over queued work when materializing the dedicated stream (#56382)

Signed-off-by: zhaoguochun1995 <zhaoguochun1995@163.com>

### [f0a61bd](https://github.com/vllm-project/vllm/commit/f0a61bd4386bf0d694cfe848e853f2450462e454)

- **作者**: JinYan Su
- **时间**: 2026-09-14T23:48:23Z
- **提交信息**: [Rust][Benchmark] Support HF ShareGPT datasets in multi-turn mode (#51104)

Signed-off-by: xiaguan <751080330@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ba2ae9f](https://github.com/vllm-project/vllm/commit/ba2ae9f23961ac67bc5c055da8c26fbd660989c6)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-14T23:11:11Z
- **提交信息**: [MRV2] Run pooling post processing on non-final PP ranks (#56666)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3bb0a03](https://github.com/vllm-project/vllm/commit/3bb0a03f35269185b6358753e64932bb946cc531)

- **作者**: Giancarlo Delfin
- **时间**: 2026-09-14T22:58:48Z
- **提交信息**: [Model Runner V2] Acceptance estimation for adaptive verification (#52228)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [8e08cef](https://github.com/vllm-project/vllm/commit/8e08cef46ebeef501a1b1593fd7da77909afe4ae)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-14T22:58:33Z
- **提交信息**: [Bugfix] Redact credentials from benchmark logs (#56662)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [00972df](https://github.com/vllm-project/vllm/commit/00972dfd72988942138a7a6089eaee08580210b8)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-14T21:44:56Z
- **提交信息**: [ROCm][DSV4.1][Perf] Fold the mHC post step into the delayed pre projection (#56513)

Signed-off-by: Fangzhou Ai <fangzhou@semianalysis.ai>
Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [bdad63c](https://github.com/vllm-project/vllm/commit/bdad63c90aec1c97682b20f282ba2a959f8229c9)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-14T21:40:35Z
- **提交信息**: [CI] Check target branch freshness before starting CI (#56169)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [d320a21](https://github.com/vllm-project/vllm/commit/d320a214316b52b08cb84a4745475370a1564e87)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-14T21:37:44Z
- **提交信息**: [Bugfix][Rust Frontend] Restore prost test dependency (#56866)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Sherlock <sherlock@raft.ai>

### [d392ac8](https://github.com/vllm-project/vllm/commit/d392ac836e17e87f5fec6594ef5ee5b56db72a91)

- **作者**: Michele Campi
- **时间**: 2026-09-14T21:15:28Z
- **提交信息**: [Doc][Metrics] Fix spec-decode PromQL examples to use the exposed names (#55016)

Signed-off-by: Michele Campi <michele.campi@outlook.com>

### [dabc436](https://github.com/vllm-project/vllm/commit/dabc4362b47ad2665b0802b0b42b13f660efe634)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-14T20:47:32Z
- **提交信息**: [ROCm][DSV4.1][Perf] Stride the DSA decode candidate mask over the live context (#56628)

Signed-off-by: Fangzhou Ai <fangzhou.ai@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [7702ee8](https://github.com/vllm-project/vllm/commit/7702ee87dba0d8eed7f201e77a0a6613aac738a8)

- **作者**: sychen52
- **时间**: 2026-09-14T20:25:33Z
- **提交信息**: [Bugfix][DSA] Write nvfp4_ds_mla from the fused norm+rope kernel (#55538)

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>

### [d4ee7fe](https://github.com/vllm-project/vllm/commit/d4ee7fe7a98b3012f64309e18dd425e565069a01)

- **作者**: Netanel Haber
- **时间**: 2026-09-14T20:24:18Z
- **提交信息**: [Quantization] Select linear backends per quantization (#51204)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>

### [995e858](https://github.com/vllm-project/vllm/commit/995e8581f462a13e32f30cfba946c63d48cf31d7)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-14T19:16:39Z
- **提交信息**: [Model] Voxtral Realtime: add support for `CUDAGraphMode.FULL_DECODE_ONLY` (#51167)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Jorge Gallego Feliciano <jorge.gallego@mistral.ai>

### [0a5747d](https://github.com/vllm-project/vllm/commit/0a5747d410da9b08145dba2b6f3e6614bab35753)

- **作者**: 鐘天楽
- **时间**: 2026-09-14T19:02:07Z
- **提交信息**: [Profiler] Add Proton CUDA graph attribution for MRV2 (#51084)

Signed-off-by: Luossu <zhluosuu@outlook.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [5372e72](https://github.com/vllm-project/vllm/commit/5372e72a9884c141874465f0eb8054a4a81da6bb)

- **作者**: Yongye Zhu
- **时间**: 2026-09-14T18:57:37Z
- **提交信息**: [Perf][DSv4.1] Fold the mHC post block into the delayed pre projection (#56633)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>

### [56ca990](https://github.com/vllm-project/vllm/commit/56ca9904ce76975fe3aad28d1af7af961a07f054)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-14T18:37:08Z
- **提交信息**: [CI] Initialize ubatch runner in cudagraph unit test (#56808)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [e85c882](https://github.com/vllm-project/vllm/commit/e85c8826ce2a810367e8a70eedb987e31b140800)

- **作者**: Zhiyao(Ian) Yu
- **时间**: 2026-09-14T18:00:20Z
- **提交信息**: [Bugfix] Make KV cache and MFU log lines backend-neutral (#55650)

Signed-off-by: Ianniu <985683179yzy@gmail.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [03dc26e](https://github.com/vllm-project/vllm/commit/03dc26e639e1927cda51d7b62639a11a354e1c0d)

- **作者**: Samuel Nordmann
- **时间**: 2026-09-14T17:26:15Z
- **提交信息**: [Perf][Kernel][Quantization] Fuse ReLU2 with static FP8 activation quantization (#53793)

Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: ElizaWszola <ewszola@redhat.com>
Signed-off-by: snordmann <snordmann@nvidia.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: ElizaWszola <ewszola@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [435c96f](https://github.com/vllm-project/vllm/commit/435c96f9dbdd29258cb8e0f433c5b54a00cf6b16)

- **作者**: Thillai Chithambaram
- **时间**: 2026-09-14T16:04:55Z
- **提交信息**: [V1][Metrics] Support Sliding Window Attention (SWA) and hybrid layers in MFU/MBU estimation (#55624)

Signed-off-by: Thillai Chithambaram <thillaichithambaram.a@gmail.com>
Co-authored-by: Mark McLoughlin <markmc@redhat.com>

### [b7e8dd8](https://github.com/vllm-project/vllm/commit/b7e8dd8f372c1324c376ba5dc03d92264eae8f24)

- **作者**: Tomas Ruiz
- **时间**: 2026-09-14T15:29:13Z
- **提交信息**: [watermarking hardening]  Add e2e test and basic GSM8K quality tests (#56309)

Signed-off-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1713a09](https://github.com/vllm-project/vllm/commit/1713a094915d643c4ffaa25f421353108ee2049f)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-14T15:17:02Z
- **提交信息**: [Rust Frontend] Forward per-request watermarking controls (#56338)

Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [b3124a8](https://github.com/vllm-project/vllm/commit/b3124a8237f21fcd3a4510002a5e2925b0dbedfe)

- **作者**: zql
- **时间**: 2026-09-14T15:06:01Z
- **提交信息**: [Model] Add support for Nanbeige4.2 (transformers backend) (#56071)

Signed-off-by: zqlcode <lizongqiang@kanzhun.com>
Signed-off-by: zql <37731799+zqlcode@users.noreply.github.com>
Co-authored-by: zqlcode <lizongqiang@kanzhun.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [4be3dcf](https://github.com/vllm-project/vllm/commit/4be3dcf0fc7a9086d978eaea3c5a4d78fb98e44a)

- **作者**: Lucas Wilkinson
- **时间**: 2026-09-14T14:20:46Z
- **提交信息**: [PCP][DCP] Declare FlashMLASparse MTP support at CP interleave > 1 (#56722)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [ff5f6d4](https://github.com/vllm-project/vllm/commit/ff5f6d41b1ccf1e305e425db41bc7f52dbce8621)

- **作者**: Orestis Zambounis
- **时间**: 2026-09-14T14:07:09Z
- **提交信息**: [Bugfix] Scale KV page size for hidden states extraction with TP (#50894)

Signed-off-by: Claude <noreply@anthropic.com>
Signed-off-by: Orestis Zambounis <orestis-z@users.noreply.github.com>
Signed-off-by: Orestis Zambounis <23146389+orestis-z@users.noreply.github.com>
Signed-off-by: Speculators Bot <bot@speculators.ai>
Signed-off-by: Speculators Bot <speculatorsbot@gmail.com>
Co-authored-by: Orestis Zambounis <orestis-z@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>
Co-authored-by: Speculators Bot <speculatorsbot@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c676e49](https://github.com/vllm-project/vllm/commit/c676e4930bb3c87b97790520e7979d43887ca5dd)

- **作者**: Orestis Zambounis
- **时间**: 2026-09-14T14:07:07Z
- **提交信息**: [Spec Decode] Fix Qwen3 DSpark d2t requirement for padded-vocab drafts (#55133)

Signed-off-by: Orestis Zambounis <23146389+orestis-z@users.noreply.github.com>
Signed-off-by: Orestis Zambounis <orestis.zambounis@gmail.com>
Co-authored-by: Benjamin Chislett <chislett.ben@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [767d1c4](https://github.com/vllm-project/vllm/commit/767d1c4d473a3e81429563aac995f22f7151c325)

- **作者**: Russell Bryant
- **时间**: 2026-09-14T13:44:50Z
- **提交信息**: [Docs] Move russellb to emeritus committer (#56467)

Signed-off-by: Russell Bryant <rbryant@redhat.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [9d4d9aa](https://github.com/vllm-project/vllm/commit/9d4d9aa5bced3fc84c9e7c89b1257f206fbff6e2)

- **作者**: linitra24
- **时间**: 2026-09-14T13:19:15Z
- **提交信息**: [LoRA][Refactor] Unify multimodal LoRA token count hooks (#55071)

Signed-off-by: linitra24 <renshuang.zhou@daocloud.io>

### [6623fe5](https://github.com/vllm-project/vllm/commit/6623fe5b4ec783e7264f140e0caea20bdc45a341)

- **作者**: arkohut
- **时间**: 2026-09-14T13:18:55Z
- **提交信息**: [Bugfix] MiniCPM-V 4.6: fix ViT self-attn qkv weight loading (#49417)

Signed-off-by: arkohut <39525455+arkohut@users.noreply.github.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [47fbd36](https://github.com/vllm-project/vllm/commit/47fbd36e6dc908277e386424beeb8647355c1c8b)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-14T13:06:26Z
- **提交信息**: [Bugfix] Trim stale consequence claims from unannotated-eagle warning (#56791)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [e0c04c7](https://github.com/vllm-project/vllm/commit/e0c04c7b4dddceb25eb9d23d87c3914bfc2ad3f9)

- **作者**: Ronald
- **时间**: 2026-09-14T13:05:47Z
- **提交信息**: [Bugfix][Models] Fix OpenPangu sleep mode with static sinks (#53696)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>

### [1d0d108](https://github.com/vllm-project/vllm/commit/1d0d1081c409176a0e7c24742f7c60b9943657aa)

- **作者**: Simon Danielsson
- **时间**: 2026-09-14T12:52:56Z
- **提交信息**: [ROCm][Connector] SWA+HMA-support in MoRI-IO connector (Gemma4) (#53721)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [3f55ad2](https://github.com/vllm-project/vllm/commit/3f55ad2f073a7d1f573db5a5a3fe3dc9c688ddee)

- **作者**: Canlin Guo
- **时间**: 2026-09-14T12:16:25Z
- **提交信息**: [Qwen3.8-Flash-Next] Fuse PLE residual and QSA output gate (#55309)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [c612e2b](https://github.com/vllm-project/vllm/commit/c612e2bff0d045a5b2304371793985c330fba436)

- **作者**: AlexHuang
- **时间**: 2026-09-14T12:02:45Z
- **提交信息**: [Bugfix][KV Offload] Reuse in-flight async lookup probes (#55823)

Signed-off-by: Alex <jihui.huang@daocloud.io>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [a5f6f61](https://github.com/vllm-project/vllm/commit/a5f6f61a8a8eb9d8e839cf7e322b23cc8ae406e5)

- **作者**: Ganesh R
- **时间**: 2026-09-14T11:51:38Z
- **提交信息**: [CI][CPU] Add speculative-decoding coverage to CPU CI (#54934)

Signed-off-by: R <Ganesh.R@amd.com>
Signed-off-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: jiang1.li <jiang1.li@intel.com>

### [a6c5d6d](https://github.com/vllm-project/vllm/commit/a6c5d6d0fcd7dd5b49e3146991c201b16caebef2)

- **作者**: Shanshan Shen
- **时间**: 2026-09-14T11:21:30Z
- **提交信息**: [ROCm][Perf] Enable CSA multi-stream overlap for DeepSeek-V4 (#51794)

Signed-off-by: shen-shanshan <467638484@qq.com>
Signed-off-by: Shanshan Shen <87969357+shen-shanshan@users.noreply.github.com>

### [e82794f](https://github.com/vllm-project/vllm/commit/e82794f48ff0812b01543f7c19c34eb0c5b3b1ee)

- **作者**: Xiaozhen Bi
- **时间**: 2026-09-14T10:48:53Z
- **提交信息**: [CI][Test] Mock CPU backend block sizes in kv_connector unit conftest (#56671)

Signed-off-by: Xiaozhen Bi <xiaozhen.bi@gmail.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [7b1ea3f](https://github.com/vllm-project/vllm/commit/7b1ea3f524445be0545ed962cb06ce21a93fcc33)

- **作者**: Reid
- **时间**: 2026-09-14T10:37:59Z
- **提交信息**: [Bugfix][Rust Frontend][Multimodal] Align DeepSeek V4.1 and Kimi K3 media with rendered placeholders (#56366)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Codex <noreply@openai.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [0ca7aef](https://github.com/vllm-project/vllm/commit/0ca7aef4e341cb4f4d7233291c304a168f4384aa)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-14T10:37:12Z
- **提交信息**: [Bugfix][NixlPush] Guard _remote_agents read in _do_send_reg_notif (X1) (#56317)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [ea723c8](https://github.com/vllm-project/vllm/commit/ea723c81c3ea26425cb69503a5d5e90822a04a45)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-09-14T10:22:18Z
- **提交信息**: [Security] Cap Qwen-VL video sampling knobs (#56729)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [1678b39](https://github.com/vllm-project/vllm/commit/1678b396270406c27fcab8f5b86b21fd305ac605)

- **作者**: jiangkuaixue123
- **时间**: 2026-09-14T10:05:13Z
- **提交信息**: [Bugfix][EPD] Preserve media processing options in encoder requests (#56786)

Signed-off-by: jiangkuaixue123 <jiangxiaozhou111@163.com>

### [934b1fc](https://github.com/vllm-project/vllm/commit/934b1fcbcbbac6e68da7a4246928ac797fe54690)

- **作者**: Martin Hickey
- **时间**: 2026-09-14T10:02:14Z
- **提交信息**: [Frontend] Replace `VLLM_ENABLE_SCALE_OUT_ENDPOINTS` with `--enable-scale-out` (#55176)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [2c7ee87](https://github.com/vllm-project/vllm/commit/2c7ee87223f0c94f614a0b8600f6f193e6e4388f)

- **作者**: BruceLoveDecimal
- **时间**: 2026-09-14T09:55:39Z
- **提交信息**: [Bugfix][Mooncake] Report failed remote KV loads to the scheduler (#50984)

Signed-off-by: liuqihao <liuqihao@myhexin.com>
Co-authored-by: liuqihao <liuqihao@myhexin.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5236bef](https://github.com/vllm-project/vllm/commit/5236bef721223a45d52b3649530e88b5e824e0d9)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-14T09:52:45Z
- **提交信息**: [CI] Keep OTel bytecode out of mounted checkouts (#56766)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [dc2e8f1](https://github.com/vllm-project/vllm/commit/dc2e8f1157173d0f0fc09712f6897e9f6eee52a0)

- **作者**: Matthias Gehre
- **时间**: 2026-09-14T09:40:25Z
- **提交信息**: [ROCm][Perf] W4A16: keep skinny GEMM zero-points packed 4-bit (#54965)

Signed-off-by: Matthias Gehre <matthias.gehre@amd.com>

### [238cb2b](https://github.com/vllm-project/vllm/commit/238cb2b191630e8b02965adc772e3236d26936fe)

- **作者**: Jared Wen
- **时间**: 2026-09-14T09:36:39Z
- **提交信息**: [Perf][GLM-5.3-Flash] Dense/masked-MHA sparse prefill for the NoPE (256, 0, 256) layout + skip the NoPE K concat (#55738)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [79f0be2](https://github.com/vllm-project/vllm/commit/79f0be21ff4044d53f0a6f911422b9f52064639c)

- **作者**: Li, Jiang
- **时间**: 2026-09-14T09:30:28Z
- **提交信息**: [Bugfix][CPU] Fix DeepSeek-R1 (FP8 MLA + MoE) correctness on CPU backend (#56773)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [dc89fdf](https://github.com/vllm-project/vllm/commit/dc89fdfb0ede2918a884faae771a49bbbe7b6cf9)

- **作者**: Chinmay-Kulkarni-AMD
- **时间**: 2026-09-14T09:16:48Z
- **提交信息**: [CPU][Profiler] Group torch profiler tables by input shape when record_shapes is on (#56016)

Signed-off-by: Chinmay Kulkarni <Chinmay.Kulkarni@amd.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [b443c1c](https://github.com/vllm-project/vllm/commit/b443c1cc4e12171be0b0bbb7cc107919bda4634f)

- **作者**: Jared Wen
- **时间**: 2026-09-14T08:36:19Z
- **提交信息**: [Perf][GLM-5.3-Flash] Use FlashKDA for KDA chunked prefill (1.7-3.8x faster than the Triton chunk path) (#55737)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [23cfaad](https://github.com/vllm-project/vllm/commit/23cfaad49701c497def53552b23317335431f72a)

- **作者**: wang.yuqi
- **时间**: 2026-09-14T07:59:51Z
- **提交信息**: [CI] Update entrypoints CI (#56763)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [78e8426](https://github.com/vllm-project/vllm/commit/78e84261ab2ffb691a8079d698d1f3f96ecb7635)

- **作者**: JooHo Lee
- **时间**: 2026-09-14T07:42:15Z
- **提交信息**: [Performance] Add Triton kernel for Gemma3n sparse GELU (#48498)

Signed-off-by: BWAAEEEK <jooho414@gmail.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [e6b4e47](https://github.com/vllm-project/vllm/commit/e6b4e47d2d894a1a0815fbf03669adb1b3405083)

- **作者**: Alec
- **时间**: 2026-09-14T07:05:33Z
- **提交信息**: [Bugfix][Rust Frontend] Preserve selected-token logprob mode (#56406)

Co-authored-by: OpenAI Codex <noreply@openai.com>
Signed-off-by: Alec Flowers <aflowers@nvidia.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-15
**监控日期**: 2026-09-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6794
- **最后更新**: 2026-09-15T00:19:26Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 22
- **主要提交者**: yulun, Ethan ZHU, kunkun

## AI分析总结

# vllm-omni 昨日提交批次分析（23 条）

## 1. 主要更新类型分布

- **Bug 修复（约 10 条）**：占比最高，覆盖 Engine 生命周期、Qwen3-TTS、MiniCPM-o、Fish Speech、Qwen3-Omni 并行、前端音频格式等。
- **模型支持（约 5 条）**：新增 VoxCPM2 LoRA、Breeze-TTS-2、MOSS-TTS-Nano（Ascend）、MiniMax-H3 多卡、MiniCPM-o 优化。
- **性能优化（约 4 条）**：Ming ISTFT 融合、MammothModa2 隐状态传输与 FP8 KV cache、Qwen2.5-Omni 冗余 embedding 消除。
- **测试/前端/杂项**：并行扩散测试跳过 GPU 清理、duplex 基准指标、模块导入修复、死代码清理。

## 2. 关键变更点与项目方向

- **多模态模型矩阵持续扩张**：TTS（VoxCPM2、Breeze-TTS-2、MOSS-TTS-Nano）、Omni（Qwen3-Omni、Qwen2.5-Omni、MiniCPM-o、MiniMax-H3）密集迭代，契合 README 中“omni-modality model serving for everyone”的定位。
- **硬件生态扩展**：Ascend A2 上 MOSS-TTS-Nano 与 Qwen3-TTS 修复，显示项目正从 GPU 向国产加速器延伸。
- **流式/双工能力强化**：duplex 性能指标、duplex 音频格式保留、Breeze-TTS-2 流式支持，指向实时交互场景。
- **性能与显存优化并重**：FP8 KV cache、kernel 融合、隐状态传输优化，呼应“fast and cheap”目标。

## 3. 对项目的影响与潜在意义

- 大量 Bugfix 集中在 TTS/Omni 推理链路的稳定性（如 Thinker 重复循环、同步流水线并行、dtype 与图重放），说明项目正从“能跑”迈向“稳定可用”。
- 新增模型与 LoRA 启动支持降低了用户接入新模型的门槛，增强生态吸引力。
- 前端与基准工具改进（duplex 指标、音频格式保留）提升了可观测性与用户体验，为生产部署铺路。

## 4. 值得关注的技术点

- **Ming ISTFT overlap-add 与归一化融合**：音频后处理 kernel 级优化，减少内存往返。
- **MammothModa2 AR→DiT 隐状态传输 + FP8 KV cache**：跨阶段数据搬运与量化协同优化，是 AR+DiT 架构的关键性能路径。
- **MiniCPM-o 帧组与视觉槽预算对齐 Stage0**：多模态输入调度的一致性设计。
- **Qwen3-TTS 异步分块 Code2Wav 门控**：流式与非流式模式的正确性隔离。
- **Engine 在 py_generator=True 时不关闭**：涉及服务生命周期与资源管理的核心语义。

## 5. 结合项目背景的发展判断

vllm-omni 定位为“易用、快速、廉价的 omni 模态服务”，本批提交呈现三条主线：**模型广度扩张**（TTS/Omni 多家族）、**推理稳定性收敛**（密集 Bugfix）、**性能与硬件适配深化**（kernel 融合、FP8、Ascend）。这表明项目已度过早期功能验证阶段，进入多模型、多硬件、流式双工场景下的工程化打磨期，为面向生产环境的 omni 模态服务奠定基础。

## 详细提交记录

### [01f4479](https://github.com/vllm-project/vllm-omni/commit/01f4479138c308a9ccf0ac84403b8b27fab0d3ae)

- **作者**: Alex Brooks
- **时间**: 2026-09-14T22:33:38Z
- **提交信息**: [Bugfix] Don't shutdown Engine on py_generator=True (#6334)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [f062124](https://github.com/vllm-project/vllm-omni/commit/f062124ba428586965ec04bce44c315f86561cb4)

- **作者**: ZacheryAU
- **时间**: 2026-09-14T22:25:59Z
- **提交信息**: [Frontend][Benchmark] Add duplex performance metrics for OmniInteract and Omni-DuplexEval benchmark (#7242)

### [27f0e8c](https://github.com/vllm-project/vllm-omni/commit/27f0e8c1ead8249c81c67bf0eb885f182508b05e)

- **作者**: Zhichao Zhang
- **时间**: 2026-09-14T22:25:51Z
- **提交信息**: [Bugfix][Qwen3-TTS] Gate async-chunk Code2Wav on non_streaming_mode (#4371) (#6898)

Signed-off-by: Zhichao Zhang <60429419+smartDream-chao@users.noreply.github.com>

### [a22a7dd](https://github.com/vllm-project/vllm-omni/commit/a22a7dd68fa508767c5ff6d55a1ae64e96677ff7)

- **作者**: Aman
- **时间**: 2026-09-14T22:25:42Z
- **提交信息**: [Model] Add VoxCPM2 startup LoRA adapter support (#7108)

Signed-off-by: bezdarnost <urumbekovaman@gmail.com>
Co-authored-by: bezdarnost <urumbekovaman@gmail.com>

### [1b7e854](https://github.com/vllm-project/vllm-omni/commit/1b7e854b054a0c1f34059d906fff6831d27890f5)

- **作者**: Tianyao Wu
- **时间**: 2026-09-14T22:25:34Z
- **提交信息**: [Bugfix][MiniCPM-o] Attach a unit's whole frame group and size the vision slot budget like Stage0 (#7271)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5f50fc3](https://github.com/vllm-project/vllm-omni/commit/5f50fc3daf4e65ce777c2ecacd974f11d29d6bf4)

- **作者**: Yash Jain
- **时间**: 2026-09-14T22:25:25Z
- **提交信息**: [Kernel] Fuse Ming streaming ISTFT overlap-add and normalization (#7338)

Signed-off-by: Yash Jain <yashjainjain1704@gmail.com>

### [8e088c7](https://github.com/vllm-project/vllm-omni/commit/8e088c7725462634f6b8cf0981d24b20a37bc900)

- **作者**: yulun
- **时间**: 2026-09-14T22:25:17Z
- **提交信息**: [Hardware][Ascend][Model] Support MOSS-TTS-Nano on Ascend A2 (#7192)

Signed-off-by: Big2Wheel <1404207590@qq.com>

### [c68eadb](https://github.com/vllm-project/vllm-omni/commit/c68eadbbe002c422be8be2297c5a68e645652531)

- **作者**: kunkun
- **时间**: 2026-09-14T22:25:08Z
- **提交信息**: [Performance] Optimize MammothModa2 AR → DiT hidden-state transfer (#7102)

Signed-off-by: kunkunblueberry <1833921874@qq.com>
Signed-off-by: kunkun <72174834+kunkunblueberry@users.noreply.github.com>

### [9f85b37](https://github.com/vllm-project/vllm-omni/commit/9f85b3722e91677615e2fff899ed81856e36cca5)

- **作者**: Ethan ZHU
- **时间**: 2026-09-14T22:25:00Z
- **提交信息**: [Model] Stop MiniCPM-o Thinker at TTS boundaries (#7463)

Signed-off-by: Zhu Shihao <zhushihao@bytedance.com>
Co-authored-by: Zhu Shihao <zhushihao@bytedance.com>

### [7ad51f0](https://github.com/vllm-project/vllm-omni/commit/7ad51f0007f027e182565bd99d61bfddf58d7e38)

- **作者**: LOGO127
- **时间**: 2026-09-14T22:24:49Z
- **提交信息**: [Misc][HiggsAudioV3] Diagnose skipped reference audio substitution (#7098)

Signed-off-by: luozijian <luozijian0924@gmail.com>

### [ed37766](https://github.com/vllm-project/vllm-omni/commit/ed3776645d4f310eb5c762864eb68d04f47333d3)

- **作者**: Nick Cao
- **时间**: 2026-09-14T20:50:07Z
- **提交信息**: [Tests] Skip global GPU cleanup for parallel online diffusion tests (#7534)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [fb23e88](https://github.com/vllm-project/vllm-omni/commit/fb23e8807a151d77c8135e36c85e58d4793c52cb)

- **作者**: Nick Cao
- **时间**: 2026-09-14T19:15:27Z
- **提交信息**: [BugFix] Fix importing renamed module vllm.entrypoints.openai.engine.… (#7531)

Signed-off-by: Nick Cao <ncao@redhat.com>

### [731e36f](https://github.com/vllm-project/vllm-omni/commit/731e36fb5786e61fd569ba1979c6e3fdfe0db6ea)

- **作者**: yadong
- **时间**: 2026-09-14T18:43:02Z
- **提交信息**: [Bugfix][Hardware][Ascend] Fix Qwen3-TTS code predictor dtype and nested graph replay (#6639)

Signed-off-by: tanyadong <2209931449@qq.com>
Signed-off-by: tanyadong <yadongtan666@gmail.com>
Co-authored-by: tanyadong <2209931449@qq.com>

### [5f25d98](https://github.com/vllm-project/vllm-omni/commit/5f25d9865281029db95c1778ead2c8ad666ac643)

- **作者**: Pujitha Paladugu
- **时间**: 2026-09-14T17:02:39Z
- **提交信息**: [Bugfix] Allow Fish Speech phoneme-control tokens through normalize_fish_speech_text (#7043)

Signed-off-by: Pujitha Paladugu <10557236+pujitha24@users.noreply.github.com>
Co-authored-by: Pujitha Paladugu <10557236+pujitha24@users.noreply.github.com>

### [40f8e94](https://github.com/vllm-project/vllm-omni/commit/40f8e94400fca12ddcefbb46b9043f6a6d6dba96)

- **作者**: heyuanliu-intel
- **时间**: 2026-09-14T17:02:30Z
- **提交信息**: [Model][MiniMax-H3] Multi-GPU serving fixes and layer-wise offload component selection (#7047)

Signed-off-by: heyuanliu-intel <heyuan.liu@intel.com>

### [2f1a18e](https://github.com/vllm-project/vllm-omni/commit/2f1a18e69fad43e36b3dbc58e698fa142dba207b)

- **作者**: Deep Shah
- **时间**: 2026-09-14T17:02:21Z
- **提交信息**: [Bugfix][Qwen3-Omni] Fix synchronous Thinker pipeline parallelism (#7345)

Signed-off-by: Deep Shah <deep@socratic.co>

### [909b121](https://github.com/vllm-project/vllm-omni/commit/909b121e0a5485ed86a604ce091a6b153d6c7257)

- **作者**: nodeeeeee
- **时间**: 2026-09-14T17:02:11Z
- **提交信息**: [Qwen2.5-Omni] Avoid redundant embedding computation (#7477)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>

### [ea1a416](https://github.com/vllm-project/vllm-omni/commit/ea1a416a17849addf135e9aa74ef5c2d2574c130)

- **作者**: noname
- **时间**: 2026-09-14T16:55:53Z
- **提交信息**: [Model] Add Breeze-TTS-2 two-stage AR TTS support (talker + codec, streaming) (#7084)

Signed-off-by: noname <liuzhiwei08@kuaishou.com>
Signed-off-by: noname <133508552+lzwnoname@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: noname <liuzhiwei08@kuaishou.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [e0c4f97](https://github.com/vllm-project/vllm-omni/commit/e0c4f97f326f895c7830bdbdcc8c6861b8fcb10a)

- **作者**: bcsdhjew
- **时间**: 2026-09-14T16:05:55Z
- **提交信息**: [Bugfix][Frontend] Preserve duplex chat audio format and duration (#7316)

Signed-off-by: Nolen Liang <nliang@nvidia.com>

### [1b6cd28](https://github.com/vllm-project/vllm-omni/commit/1b6cd282f019fa8b49a8a34b4ae1b87f0ab4f0c2)

- **作者**: Tai An
- **时间**: 2026-09-14T13:48:51Z
- **提交信息**: fix(qwen-image): drop the shadowed dead _get_qwen_prompt_embeds duplicate (#7461)

Signed-off-by: Anai-Guo <antai12232931@outlook.com>

### [3d79348](https://github.com/vllm-project/vllm-omni/commit/3d793481a04c9453b89508bbc67ecbc0b2d68357)

- **作者**: BeatSeat
- **时间**: 2026-09-14T13:11:15Z
- **提交信息**: [Bugfix][MiniCPMO45] Return bare tensor in Thinker forward to fix repetition loop (#7497) (#7517)

Signed-off-by: BeatSeat <wendavid552@gmail.com>

### [446c2b5](https://github.com/vllm-project/vllm-omni/commit/446c2b5474dabffccf9a0034836eeab77c62b4b8)

- **作者**: psv666
- **时间**: 2026-09-14T11:29:50Z
- **提交信息**: [Bugfix] Forward Qwen3-Omni streaming video sampling parameters (#7325)

Signed-off-by: psv666 <2693925048@qq.com>

### [2cbfd3e](https://github.com/vllm-project/vllm-omni/commit/2cbfd3e93b460462031a0339d9f1e8733e39e1e6)

- **作者**: jiahengxie
- **时间**: 2026-09-14T07:47:39Z
- **提交信息**: [Performance][MammothModa2] Enable and validate FP8 KV cache for AR stage (#7436)

Signed-off-by: JH <13716265422@139.com>

---
