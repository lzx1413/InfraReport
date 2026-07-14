# GitHub Stars 合并报告 - 2026-07-14

**合并日期**: 2026-07-15
**监控日期**: 2026-07-14
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


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2085
- **最后更新**: 2026-07-14T15:40:18Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: 鐘天楽

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增（Feature）**：为 DeepSeek V4 模型添加了基于 TileLang 的内核实现。

#### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在 `model/ops` 模块中新增 `DeepSeek V4 TileLang kernels`（提交 #912）。  
- **与项目方向的关系**：  
  VeOmni 的核心理念是“规模任意模态模型训练”（Scaling Any Modality Model Training），而 DeepSeek 系列是当前业界主流的高性能大语言模型（LLM）。该提交直接扩展了对 DeepSeek V4 的支持，通过 TileLang（一种面向张量计算的 DSL/编译器）定制化优化关键算子，旨在提升训练效率与性能，与项目“模型中心的分布式配方库”（Model-Centric Distributed Recipe Zoo）目标一致——为不同模型提供最优的训练基础设施。

#### 3. 对项目的影响和潜在意义
- **影响**：  
  - 用户可以更高效地训练 DeepSeek V4 模型，尤其是需要大规模分布式训练的团队。  
  - 为后续集成其他基于 TileLang 的优化内核奠定了模块化基础。  
- **潜在意义**：  
  - 巩固 VeOmni 在多模态训练框架中的竞争力，特别是支持最新前沿 LLM 的能力。  
  - 通过 TileLang 的硬件/算子抽象，可能进一步降低不同 GPU 架构（如 NVIDIA、AMD）的适配成本，提升框架的通用性。

#### 4. 值得关注的技术点
- **TileLang 内核**：这是一种基于分块（tiling）的代码生成技术，可实现高性能计算与自动调优。该内核的引入表明 VeOmni 在底层算子优化上采用了更先进的编译方法。  
- **针对 DeepSeek V4 的算子定制**：DeepSeek V4 模型结构（如 MLA、MoE 等）需要特定的高性能实现，该提交可能覆盖了注意力、前馈网络等核心算子的优化。

#### 5. 基于项目背景，这些提交如何影响项目发展
- **短期**：直接增强了对 DeepSeek V4 的训练支持，吸引更多使用此模型的开发者采用 VeOmni。  
- **长期**：建立 “模型+算子+编译” 的协同优化范式，推动项目从“支持多种模型”向“为每种模型提供定制化高性能内核”进化，符合“模型中心”的设计哲学。同时，TileLang 的集成可能成为后续支撑更多模态（如图像、视频）异构计算的基座，加速“任意模态”规模化训练目标的实现。

## 详细提交记录

### [2f8dec2](https://github.com/ByteDance-Seed/VeOmni/commit/2f8dec2fa0e09868a3d5c4ed9746651e7f756a44)

- **作者**: 鐘天楽
- **时间**: 2026-07-14T14:28:44Z
- **提交信息**: [model,ops] feat: add DeepSeek V4 TileLang kernels (#912)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2492
- **最后更新**: 2026-07-14T18:24:49Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

好的，根据您提供的仓库上下文和提交记录，以下是对昨日更新的分析总结：

### 1. 主要更新类型
**功能新增** — 提交 `Support wan-dancer (#1247)` 明确为项目增加了一个新的模型/功能支持。

### 2. 关键变更点及其与项目整体方向的关系
- **变更内容**：新增对 `wan-dancer` 的支持（推测为一种面向舞蹈动作生成的视频模型）。
- **与项目方向的关系**：LightX2V 定位为“轻量视频生成推理框架”，其核心价值在于兼容多种主流视频生成模型并提供高效推理。本次更新扩展了支持模型列表，直接服务于“轻量 & 多模型兼容”的目标，使框架能够覆盖更多视频生成场景（如舞蹈动作生成），提升了框架的通用性和实用性。

### 3. 对项目的影响和潜在意义
- **生态扩展**：吸引需要舞蹈类视频生成的用户和开发者，可能进一步丰富社区贡献。
- **竞争力提升**：相比同类框架，更早支持热门视频生成模型（`wan-dancer` 可能指代某类新近流行模型），有助于巩固 LightX2V 在轻量级推理框架中的领先地位。
- **验证框架可扩展性**：通过添加新模型，间接测试了项目的架构设计（如模型注册、推理管线等）是否易于扩展，为未来集成更多模型积累了经验。

### 4. 值得关注的技术点
- **模型适配策略**：`wan-dancer` 可能涉及特定的模型结构、输入格式或后处理逻辑，其集成方式值得关注（例如是通过插件、配置文件还是直接修改代码）。
- **推理性能优化**：轻量级框架通常关注推理效率，该模型是否在内存占用、延迟等方面经过针对性优化，可作为后续评估重点。
- **接口一致性**：新增模型是否保持了与现有 API 的兼容性，是否遵循了框架统一的调用范式，这将影响用户的学习成本和迁移体验。

### 5. 基于 README 背景，这些提交如何影响项目发展
- 项目 README 强调了“Light Video Generation Inference Framework”（轻量视频生成推理框架），本次更新直接体现“支持更多模型”这一核心演进路径。
- 随着模型支持数量的增加，LightX2V 的**模型库逐渐丰富**，有助于从单一框架向一站式视频生成推理平台演进，吸引更多研究者、开发者和下游应用。
- 同时，提供对 `wan-dancer` 等特色模型的支持，可能推动框架在**特定垂直领域（如舞蹈生成、视频编辑）** 的应用落地，进一步扩大项目影响力和用户基础。

> 总结：一次直接的功能扩展，朴素但重要——它表明项目正稳步推进“多模型覆盖”的路线，为后续生态建设打下基础。

## 详细提交记录

### [863c9e8](https://github.com/ModelTC/LightX2V/commit/863c9e848f8e78309a8e362003f248b200769b04)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-14T18:23:43Z
- **提交信息**: Support wan-dancer (#1247)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2170
- **最后更新**: 2026-07-14T16:48:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5957
- **最后更新**: 2026-07-14T18:35:19Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Ziang Li, Yihan Wang, RuQing Xu

## AI分析总结

以下是对 `flashinfer-ai/flashinfer` 仓库昨日（基于提供提交时间）更新的要点总结，结合项目 README 背景（高性能 GPU 推理内核）进行分析。

### 1. 主要更新类型

- **功能新增**：3 个 PR（FP8 MoE GEMM、每 token NVFP4 MoE、CuTe DSL FMHA 及块缩放版本）
- **Bug 修复 / 稳定性改进**：2 个 PR（自动调优内存泄漏、MLA block table 对齐放宽）
- **测试 / 质量保障**：1 个 PR（统一 GEMM/BMM 模糊测试 + 约定审计）
- **重构 / 优化**：1 个 PR（FMHA 新 JIT 内核架构，内含性能优化）

### 2. 关键变更点及其与项目整体方向的关系

- **统一模糊测试框架**（#3539）：替换原有零散的测试文件，采用确定性稀疏输入、紧数值 Oracle、输出污染、跨架构一致性校验。**方向**：强化测试质量，确保持续集成中不会遗漏结构性和精度回归问题，为后续新内核开发提供坚实保障。
- **每 token NVFP4 量化 MoE**（#3645）：让 CuTe DSL 路径与 TRTLLM 路径对齐，支持每 token 激活量化。**方向**：统一并扩充 MoE 支持的量化精度，提升部署灵活性（DeepSeek 等模型受益）。
- **FP8 分组缩放 MoE GEMM（SM120）**（#3891）：为 Blackwell 架构（RTX

## 详细提交记录

### [0472b9b](https://github.com/flashinfer-ai/flashinfer/commit/0472b9b3f2fba11b463f8526f390297d52a8aad7)

- **作者**: Yang Xu
- **时间**: 2026-07-14T18:35:13Z
- **提交信息**: test: unified GEMM/BMM fuzzer + convention auditor (#3539)

# test: unified GEMM/BMM fuzzer + convention auditor

## What this is

**One** harness — `tests/gemm/test_unified_gemm_fuzz.py` — for
flashinfer's scaled GEMM/BMM family:
`{op-shape: mm, bmm} × {quant: bf16, fp8 (e4m3+e5m2), nvfp4, mxfp4} ×
{backend}`, driven through thin
per-API **adapters**. It replaces the earlier per-op fuzzers
(`test_mm_fp4_fuzz.py`,
`test_bmm_fp8_fuzz.py`) — their logic, plus the `#2440` quantize-root
test, is folded in here — so
there is one strong, encapsulated tester instead of N scattered files.

> Scope note: this PR is now **GEMM-only**. The MoE fuzzers that were
originally in this branch have
> moved: the production unified-MoE fuzzer landed on `main` with the
unified MoE API (#3093), and the
> older MoE/adapter crash-finders are parked on branch
`yanxu/moe-fuzzers-parked` for later (they
> cover in-kernel routing, which the pre-routed unified API can't yet
exercise).

## Input model (same as the unified MoE fuzzer)

**Sparse (~75% zero) + exactly-representable inputs**, snapped to each
quant mode's grid via a
per-mode round-trip (bf16 = identity, fp8 = `to_float8`, nvfp4 =
`nvfp4_quantize`+`e2m1` decode,
mxfp4 = `mxfp4_quantize`+`mxfp4_dequantize`). Because input quantization
is then **lossless**:
- structural bugs (wrong tile / dropped block / wrong scale role)
produce a **gross** error over the
  short sparse reductions instead of being averaged away;
- the numeric oracle is a **tight** `atol = C·‖ref‖∞` against the
authoritative snapped-input
reference (C = the accumulation/requant floor), not a loose `cosine >
0.97`. This catches both
structural bugs and the **sub-floor accuracy regressions** a cosine
oracle misses.

Magnitude regimes (tiny/large/…) are kept only in the standalone
quantize-root test, where extreme
magnitudes are the point (`#2440`: finite inputs must never yield
non-finite scale factors).

## Oracles (per config)

no-spurious-NaN/Inf · tight numeric vs authoritative reference ·
not-(almost)-all-zero (`#3398/#3068`)
· **output-buffer poison** (NaN-fill → catches a kernel that doesn't
fully write its output) ·
run-to-run **determinism** (`#2514`) · **device-state probe** (a
context-corrupting IMA → clean
failure) · **cross-arch by construction** (run the same seed on each
GPU, diff pass/fail).

## Convention auditor (existing APIs unchanged)

Each scaled-GEMM API ships its own scale convention (per-tensor alpha vs
block vs block+global alpha
vs none; A/B-scale roles; layout) — the surface where the fp4-vs-fp8
incompatibility was found. The
APIs **cannot be changed** (would break users), so this harness does
**not** force them to agree:
- each adapter **declares** its convention explicitly;
- the per-config oracle validates each backend against its **own**
recipe (a deviation is caught) —
never against a different convention (forcing cross-convention equality
is a false-positive trap);
- `test_convention_conformance` cross-checks backends that **share** a
declared convention (a real
cross-backend oracle), prints a convention matrix, and a
`_CONVENTION_DIVERGENCES` ledger documents
known cross-mode incompatibilities so they're tracked, not silently
passing.

This is the **enforcement hook** for the future: if a unified GEMM API
(or an incremental
convention-compat fix) makes two divergent APIs share a convention, move
them into one conformance
group + drop the ledger entry → the test then enforces they agree.

## Debuggability (every test)

- **Deterministic**: every config (shapes, modes, input data, buffer
poison, global RNG) is derived
  from its seed → bit-reproducible.
- **Self-explanatory failures**: prints the full config; on a numeric
mismatch dumps output-vs-oracle
stats (nan/inf/zero counts, `max|.|`) + the worst ≤30 elements — so a CI
log shows whether the
  output is all-zero / NaN / Inf / garbage **without rerunning**.
- **Perfect repro**: prints a `REPRO:` line;
`FLASHINFER_GEMM_FUZZ_ONLY_SEED=<seed>` reruns exactly
  that one config.

## Validation

Run on all four archs on the dev box — **A100/SM80, L40S/SM89,
H100/SM90, B200/SM100** — all clean
(fp4 adapters skip cleanly below SM100; fp8 below SM89). Tolerances
calibrated on SM100 and verified
to hold cross-arch (fp8 ≤ 0.011, bf16 ≤ 0.0035). Default
`FLASHINFER_GEMM_FUZZ_NUM_TESTS=1000`
(~10-min full sweep; tunable via env). The new dump immediately surfaced
— and we fixed — a harness
B-layout bug (a `.contiguous()` made fp8 `B` row-major, which cublas
*silently* computes garbage from
while cudnn/cutlass reject it).

## Follow-ups (tracked in-file TODOs)

autotune ON/OFF + cache-coherence oracle · non-contiguous-input axis
(B1) · `use_8x4_sf_layout=True`
/ `#2861` (C1, needs the matching SF layout + a trtllm backend) ·
grouped op-shape
(`group_*`/`*deepgemm*`, m_indptr) · more point APIs (`mm_fp8`
low-latency, `mm_mxfp8`, `bmm_mxfp8`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Added a unified GEMM/BMM fuzzing framework with deterministic sparse
and quantized inputs, NaN-poisoning, per-quant-mode FP32 reference
checks, determinism validation, convention-conformance grouping and
agreement checks, quantize-fuzz tests, and autotune-cache isolation with
dynamic-shape validation.
* **Bug Fixes**
* Disabled a known-bad cuDNN backend version and surface an upgrade
message.
* Enforced minimum dimensions for certain quantized batch-matrix cases
to reject unsafe small shapes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yang Xu <yanxu@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [59b1516](https://github.com/flashinfer-ai/flashinfer/commit/59b1516a2167ffe430ace53412df4838c24ffaa8)

- **作者**: Ziang Li
- **时间**: 2026-07-14T16:27:09Z
- **提交信息**: Add per-token NVFP4 quantization to CuTe DSL MoE (#3645)

## 📌 Description
@humansand

Adds per-token NVFP4 activation quantization support to the CuTe DSL
fused MoE path.

The CuTe DSL MoE path now mirrors the existing TRTLLM per-token
activation contract. When `per_token_scale` is provided, GEMM1/SwiGLU
applies the input row scale before the nonlinear activation. The path
then materializes the GEMM1/SwiGLU intermediate, reuses the standalone
CuTe DSL NVFP4 per-token quantizer for FC2 input, and lets the finalize
kernel apply the returned FC2 per-row scale together with the routing
scale.

This also updates the DeepSeek MoE benchmark script with
`--use-per-token-activation` support for CuTe DSL and TRTLLM, and
extends CuTe DSL MoE numerical coverage across the per-token activation
axis.

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

Local:

```bash
pre-commit run --all-files
```

Result: passed.

B200 validation setup after rebasing on upstream `main`:

```bash
python3 -m pip uninstall -y flashinfer-jit-cache flashinfer-python flashinfer-cubin
python3 -m pip install --no-deps flashinfer-cubin==0.6.14 --index-url https://flashinfer.ai/whl
python3 -m pip install --no-deps flashinfer-jit-cache==0.6.14 --index-url https://flashinfer.ai/whl/cu130
python3 -m pip install --no-build-isolation --no-deps -e .
python3 -m pip install -U cupti-python
FLASHINFER_DISABLE_VERSION_CHECK=1 flashinfer show-config
```

`flashinfer show-config` reported the rebased editable
`flashinfer-python==0.6.15` source with `flashinfer-cubin==0.6.14`,
`flashinfer-jit-cache==0.6.14+cu130`, Torch `2.11.0+cu130`, CUDA runtime
available, CUDA Graph enabled, and CUPTI enabled for benchmark timing.

Non-4over6 unit test, with no `FLASHINFER_NVFP4_4OVER6*` env vars and no
`CUDA_LAUNCH_BLOCKING`:

```bash
FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_CUDA_ARCH_LIST=10.0a \
CUDA_VISIBLE_DEVICES=0 \
python3 -m pytest -q tests/moe/test_cute_dsl_fused_moe.py
```

Result on the post-rebase implementation before the final diff-only
cleanup: `317 passed, 138 warnings in 276.99s (0:04:36)`.

4over6 unit test, without `CUDA_LAUNCH_BLOCKING`:

```bash
FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_CUDA_ARCH_LIST=10.0a \
CUDA_VISIBLE_DEVICES=0 \
FLASHINFER_NVFP4_4OVER6=1 \
FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1 \
FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE \
FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=0 \
FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1 \
python3 -m pytest -q tests/moe/test_cute_dsl_fused_moe.py
```

Result on the post-rebase implementation before the final diff-only
cleanup: `317 passed, 138 warnings in 281.47s (0:04:41)`.

After the final diff audit, representative legacy and strict-4over6
per-token numerical cases were rerun on head `791e304b`; both passed.

Non-4over6 per-token MoE benchmark, no `FLASHINFER_NVFP4_4OVER6*` env
vars:

```bash
FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_CUDA_ARCH_LIST=10.0a \
CUDA_VISIBLE_DEVICES=0 \
python3 benchmarks/bench_moe_deepseek.py --use-per-token-activation
```

B200, wrapper API, CUDA graph enabled, CUPTI timing. CUTLASS is omitted
because this comparison is for the explicit per-token activation scale
contract.

| Tokens | CuteDSL ms | TRTLLM ms | CuteDSL vs TRTLLM | Winner |
|---:|---:|---:|---:|---|
| 128 | 1.017 | 0.890 | 0.88x | TRTLLM |
| 256 | 1.058 | 0.938 | 0.89x | TRTLLM |
| 512 | 1.071 | 1.199 | 1.12x | CuteDSL |
| 1024 | 1.099 | 1.265 | 1.15x | CuteDSL |
| 2048 | 1.147 | 1.445 | 1.26x | CuteDSL |
| 4096 | 1.580 | 2.038 | 1.29x | CuteDSL |

Geomean speedup: `1.08x` vs TRTLLM.

4over6 per-token MoE benchmark:

```bash
FLASHINFER_DISABLE_VERSION_CHECK=1 \
FLASHINFER_CUDA_ARCH_LIST=10.0a \
CUDA_VISIBLE_DEVICES=0 \
FLASHINFER_NVFP4_4OVER6=1 \
FLASHINFER_NVFP4_4OVER6_E4M3_USE_256=1 \
FLASHINFER_NVFP4_4OVER6_ERR_MODE=MSE \
FLASHINFER_NVFP4_4OVER6_ERR_USE_FAST_MATH=0 \
FLASHINFER_DISABLE_FP4_QUANT_FAST_MATH=1 \
python3 benchmarks/bench_moe_deepseek.py --use-per-token-activation
```

B200, wrapper API, CUDA graph enabled, CUPTI timing. CUTLASS is omitted
because this comparison is for the explicit per-token activation scale
contract.

| Tokens | CuteDSL ms | TRTLLM ms | CuteDSL vs TRTLLM | Winner |
|---:|---:|---:|---:|---|
| 128 | 1.033 | 0.900 | 0.87x | TRTLLM |
| 256 | 1.076 | 0.958 | 0.89x | TRTLLM |
| 512 | 1.101 | 1.222 | 1.11x | CuteDSL |
| 1024 | 1.142 | 1.251 | 1.10x | CuteDSL |
| 2048 | 1.239 | 1.482 | 1.20x | CuteDSL |
| 4096 | 1.705 | 2.206 | 1.29x | CuteDSL |

Geomean speedup: `1.07x` vs TRTLLM.

## Reviewer Notes

The non-FP4 GEMM1/SwiGLU path must preserve `None` for the optional
output scale/global scale pointers. The CuTe kernel uses pointer
presence to select the scale-generation epilogue, so dummy pointers
would incorrectly enable FP4 scale generation for BF16 intermediate
output.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optional per-token activation mode for MoE benchmark runs and
fused MoE execution, with trace support.
* Introduced an additional optional per-token scale input
(`per_token_scale` / `a_per_token_scale`) to enable per-token scaling in
the fused MoE NVFP4 pipeline and related kernels.
* Added `--use-per-token-activation` to control benchmark behavior and
reporting.
* **Bug Fixes**
* Improved input validation and ensured consistent output
scaling/behavior across per-token vs global-scaling modes.
* **Tests**
* Expanded and parameterized MoE fused-kernel tests to cover per-token
activation paths and new scale input contracts.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1d4525e](https://github.com/flashinfer-ai/flashinfer/commit/1d4525eb3b7b02407e442d7ea85a444254161039)

- **作者**: Julien Debache
- **时间**: 2026-07-14T15:50:34Z
- **提交信息**: fix: autotuner memory leak follow up (#3912)

## 📌 Description

In #3687, we partially fixed the identity of objects used to identify
cache entries in the cache of `_find_nearest_profile`. However, as
correctly pointed out in #3810, we did not handle the initializer for
the MoE TopK IDs.

This PR fixes this gap and adds a test to preserve the correct
behaviour.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
* Improved Mixture-of-Experts autotuning efficiency by reusing the
expert-routing initialization used to build tuning configurations.

* **Reliability / Bug Fixes**
* Improved autotuner profile-cache stability by ensuring equivalent
tuning configurations deduplicate correctly.
* Updated integration-test cache injection to target the correct
operator entry.

* **Tests**
* Added regression coverage for profile-cache deduplication and
verifying cache growth when new initializers are recreated.
* Made VSA BlockSparseAttention tests conditional on the presence of
`quack`.

* **Chores**
  * Updated benchmark cache-update keying to match loader expectations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jdebache <jdebache@nvidia.com>

### [9d33a28](https://github.com/flashinfer-ai/flashinfer/commit/9d33a28e8321b2da099e7106fbc527ab3bca904c)

- **作者**: CarstyYou
- **时间**: 2026-07-14T12:05:14Z
- **提交信息**: Add FP8 groupwise MoE GEMM entry (cute SM120 backend) (#3891)

## 📌 Description

FP8 (E4M3 + float32 `(1, 128, 128)` groupwise scaling) **MoE GEMM**
entry for NVIDIA RTX PRO 6000 Blackwell (**SM120**), implemented via
**CuTe C++**. Follow-up to #3562, sharing the same in-tree kernel
package and JIT module (single `.so`).

**Entry**: `flashinfer.grouped_mm.moe_gemm_fp8_nt_groupwise(a, b,
a_scale, b_scale, m_indptr, scale_granularity_mnk=(1, 128, 128),
scale_major_mode="MN", out=None, out_dtype=None)`.

Zero-padding mode: token-packed A `(cum_m, k)` with **no token
padding**; only the float32 A-scale carries per-expert 4-row-aligned
padding (contiguous MN-major `[ceil(k/128), m_padded]`, `m_padded =
(cum_m + 3 * num_experts) // 4 * 4`). B-scale is a compact
`[num_experts, ceil(k/128), ceil(n/128)]` per-`(128, 128)`-block tensor.

This PR also restructures the in-tree kernel layout synced from the
kernel source-of-truth: shared components move to `sm120_common/`
(persistent scheduler, A/B TMA load, epilogue, math helpers), the FP8
float-scale family lands in `sm120_blockscaling/`, and the MXFP8 family
keeps `sm120_blockscaled/`. MXFP8 outputs are bit-identical pre/post
restructure (existing `test_cute_sm120_mxfp8.py`: 69 passed before and
after).

### Comparison vs existing FP8 grouped-MM entries

| Aspect | `group_gemm_fp8_nt_groupwise` (cutlass) |
`group_deepgemm_fp8_nt_groupwise` (DG) | `moe_gemm_fp8_nt_groupwise`
(this PR, cute SM120) |
|---|---|---|---|
| Token (A) layout + pad | `(cum_m, k)`, `m_indptr` elements
multiple-of-4 | `(m, k)` contiguous, per-expert M pad via `m_indices` |
token-packed `(cum_m, k)`, **no token pad** |
| Scale (A) layout | MN-major `(k // 128, cum_m)` fp32 | `(m, k // 128)`
fp32 per-token | zero-padding MN-major `[Kb, m_padded]` fp32, pad ≤ `3 ×
num_experts × Kb × 4 B` |
| SM120 support | guarded (`num_groups > 1` raises on SM120/121) | not
dispatched (arch table is `{100a, 103a}`) | **native SM120 target** |
| Tile / SwapAB | fixed cooperative `128x128`, no SwapAB | DG-fixed |
**multi-tile selector + SwapAB** (small-M optimized) + staged-R2G
epilogue |

## Benchmark on SM120 (RTX PRO 6000 Blackwell Server Edition, 188 SM)

| Backend | Library API | Notes |
|---|---|---|
| **cute** | `flashinfer.grouped_mm.moe_gemm_fp8_nt_groupwise` | this
PR, `(1, 128, 128)` groupwise float scale |
| **cutlass** | `flashinfer.gemm.group_gemm_fp8_nt_groupwise`
(`skip_check=True`) | same `(1, 128, 128)` groupwise recipe —
apples-to-apples; SM120 wrapper guard bypassed for a perf baseline only;
`m_indptr` multiple-of-4 contract, so no `m_pe = 1` cell |
| **cudnn** | `flashinfer.grouped_mm.grouped_mm_fp8` (`alpha=None`) |
**per-tensor recipe (no groupwise scaling — strictly less rescale work
than cute/cutlass); perf reference only** |

warmup 10 + 50-iter median, numbers in µs, `(+X%)` = that backend's
latency over cute, computed within each backend's own paired run against
the same cute entry. `(pad 4)`: cutlass's `m_indptr` multiple-of-4
contract requires the caller to pad each expert to 4 rows at `m_pe = 1`;
the padded latency is charged to cutlass.

### fc1 (N=4096, K=7168)

| m_pe | cute E=4 | cutlass E=4 | cudnn E=4 | cute E=8 | cutlass E=8 |
cudnn E=8 |
|---|---|---|---|---|---|---|
| 1 | 39.3 | 107.6 (pad 4, +178%) | 88.9 (+126%) | 166.7 | 207.7 (pad 4,
+25.2%) | 206.1 (+23.7%) |
| 4 | 38.9 | 124.7 (+220%) | 79.1 (+113%) | 166.8 | 206.6 (+23.9%) |
208.5 (+24.3%) |
| 8 | 37.4 | 101.5 (+171%) | 77.5 (+107%) | 168.1 | 201.9 (+20.1%) |
203.1 (+20.9%) |
| 16 | 44.7 | 104.2 (+133%) | 108.8 (+140%) | 172.4 | 207.9 (+20.6%) |
207.6 (+20.2%) |
| 192 | 143.5 | 171.1 (+19.3%) | 231.7 (+63.4%) | 221.3 | 239.4 (+8.2%)
| 343.9 (+54.2%) |
| 256 | 139.1 | 151.8 (+9.1%) | 169.6 (+19.6%) | 224.4 | 243.4 (+8.5%) |
330.4 (+48.0%) |
| 1024 | 384.6 | 388.2 (+0.9%) | 398.8 (+3.0%) | 694.4 | 697.2 (+0.4%) |
677.5 (**-2.1%**) |

### fc2 (N=7168, K=4096)

| m_pe | cute E=4 | cutlass E=4 | cudnn E=4 | cute E=8 | cutlass E=8 |
cudnn E=8 |
|---|---|---|---|---|---|---|
| 1 | 41.3 | 130.8 (pad 4, +194%) | 84.2 (+104%) | 162.9 | 204.4 (pad 4,
+25.6%) | 199.7 (+22.6%) |
| 4 | 37.6 | 108.7 (+189%) | 85.4 (+129%) | 164.0 | 195.1 (+19.0%) |
262.5 (+60.5%) |
| 8 | 37.1 | 106.8 (+188%) | 79.8 (+114%) | 164.3 | 194.4 (+18.4%) |
260.8 (+58.3%) |
| 16 | 43.5 | 107.3 (+147%) | 76.7 (+70.0%) | 166.1 | 202.0 (+21.5%) |
265.2 (+58.8%) |
| 192 | 119.0 | 144.2 (+21.2%) | 120.2 (+0.6%) | 210.6 | 225.1 (+6.9%) |
300.2 (+43.7%) |
| 256 | 117.0 | 136.1 (+16.4%) | 156.6 (+31.8%) | 214.8 | 226.1 (+5.3%)
| 300.6 (+39.3%) |
| 1024 | 354.4 | 373.5 (+5.4%) | 386.6 (+9.2%) | 690.1 | 713.2 (+3.3%) |
708.5 (+2.9%) |

All cutlass cells positive across 2 independent rounds (no cell drifts >
3pp between rounds); cudnn likewise measured over 2 rounds. The only
cell where cudnn leads (fc1, E=8, m_pe=1024, ~2%) is consistent with its
per-tensor recipe doing no groupwise rescale work.

## 🔍 Related Issues

Follow-up to #3562 (MXFP8 MoE GEMM entry, same kernel package).

## 🧪 Tests

`tests/grouped_mm/test_cute_sm120_fp8.py` — standalone (no dependency on
the MXFP8 test). Quantization helpers reuse the DG-imported
`flashinfer.testing.utils.{per_token_cast_to_fp8,
per_block_cast_to_fp8}`; the zero-padding scale re-pack reference
`per_token_cast_to_fp8_for_moe_gemm` mirrors the MXFP8 test convention.

Coverage: uniform cells (E ∈ {4, 8} × m_pe ∈ {1, 8, 192, 1024} ×
fc1/fc2), uneven and empty-expert routing, per-dimension bad-scale-shape
rejects (`a_kb / a_m / b_expert / b_kb / b_n`), and bad-input rejects
(granularity / scale_major_mode / backend / m_indptr).

Verified on RTX PRO 6000 Blackwell Server Edition: 27/27 passed
(`calc_diff < 1e-3` against per-expert bf16 reference), existing MXFP8
test 69/69 passed, cold JIT compile clean, pre-commit clean
(`clang-format`, `mypy`, `ruff check`, `ruff format`).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [a92fce7](https://github.com/flashinfer-ai/flashinfer/commit/a92fce7a109293783ce4af422734f278d6b089c6)

- **作者**: Yihan Wang
- **时间**: 2026-07-14T08:02:42Z
- **提交信息**: fix(mla): allow native-width block tables for TRTLLM-GEN (#3916)

## 📌 Description

Allow `trtllm_batch_decode_with_kv_cache_mla` to accept native, unpadded
block-table widths when the caller explicitly selects
`backend="trtllm-gen"`.

The TRTLLM-GEN launcher already consumes the actual final dimension of
the
block table. The public API's `block_num % (128 / page_size)` check
therefore
forced callers to add unnecessary padding and CUDA-graph fill/copy
operations.

This PR:

- makes block-table width alignment optional in the internal shape
validator
- disables only that alignment check for explicit TRTLLM-GEN dispatch
- covers both regular and flattened/cumulative-query TRTLLM-GEN paths
- preserves rank, shared/separate layout, dtype, device, and batch
validation
- leaves `auto`, XQA, and CuTe-DSL behavior unchanged
- documents native-width support for TRTLLM-GEN

On B300, removing caller-side padding improved output throughput by
1.85% and
reduced the stable CUDA-graph makespan by 2.25%. The measured graph lost
exactly 8,192 nodes: 4,096 page-table fills and 4,096 copies.

## 🔍 Related Issues

Closes #3915.

Internal context: NVBUG 6430674.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I ran the hooks on the modified files and fixed all reported
issues.

Validated hooks: standard file checks, mypy, Ruff check, and Ruff
format.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All focused tests pass.

GPU validation on B300:

```text
tests/attention/test_trtllm_gen_mla.py::test_trtllm_batch_decode_mla_native_block_table_width
tests/attention/test_trtllm_gen_mla.py::test_trtllm_batch_decode_mla_preallocated_out

8 passed
```

The new test uses `page_size=32`, `max_seq_len=1025`, and native width
33,
with an active partial final page. It covers both shared 2-D and
separate 3-D
block-table layouts and compares against the existing FA2 numerical
reference.

## Reviewer Notes

The validator option defaults to requiring alignment. Only call sites
that
unconditionally use TRTLLM-GEN disable it, keeping the behavior change
narrowly
scoped. The C++ launcher already forwards `block_tables.size(-1)`
without an
alignment restriction, so no launcher change is required.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved MLA decoding compatibility with block tables whose widths are
not aligned to the previously required boundary.
* Relaxed alignment requirements where supported while preserving
validation for applicable backends.
* Added coverage for native block-table widths across shared and
non-shared paged KV configurations.

* **Documentation**
* Clarified block-table padding requirements for the supported MLA
decoding backend.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Yihan Wang <yihwang@nvidia.com>

### [41155ec](https://github.com/flashinfer-ai/flashinfer/commit/41155ec20cbb51c0c1c7638467713c0aa08c881e)

- **作者**: RuQing Xu
- **时间**: 2026-07-14T07:20:55Z
- **提交信息**: [feat] New CuTe DSL JIT kernels for FMHA: Dense & MXFP8 & NVFP4 formats (#3857)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

### Added kernels

- `fmha.py`: high-throughput FMHA kernel in CuTe DSL
  - QK_dtype & V_dtype can independently select BF16, FP16, or FP8.
- Accepts the same input format as CUBINs wrapped by
`flashinfer/attention/cute_dsl/fmha.py`.
- Substantially faster than `flashinfer/cute_dsl/attention/prefill.py` .
- `fmha_blockscaled.py`: QK can select MXFP8 & NVFP4. V can select BF16,
FP16, or FP8.

Added kernel doesn't support decode-phase attention.

### API design

#### Dense FMHA

| Content | Location | API |
| ------- | -------- | --- |
| New JIT source code | `flashinfer/cute_dsl/attention/fmha/fmha.py` |
... |
| Compilation entry | `flashinfer/cute_dsl/attention/fmha/compile.py` |
`compile_cute_dsl_fmha_kernel` |
| Runner (cubin & JIT shares runner) |
`flashinfer/attention/cute_dsl/fmha.py` | `cute_dsl_fmha_ragged_prefill`
|
| **Frontend** | `flashinfer/prefill.py` | ... |

Here, The **Frontend** changes are independent to JIT compilation &
execution: it wires the existing `trtllm_ragged_attention_deepseek` to
the `BatchPrefillWithRaggedKVCacheWrapper` generic module to ease use.

#### Block-scaled FMHA

| Content | Location | API |
| ------- | -------- | --- |
| New JIT source code |
`flashinfer/cute_dsl/attention/fmha/fmha_blockscaled.py` | ... |
| Compilation entry | `flashinfer/cute_dsl/attention/fmha/compile.py` |
`compile_cute_dsl_fmha_blockscaled_kernel` |
| Runner | `flashinfer/attention/cute_dsl/fmha_blockscaled.py` |
`cute_dsl_fmha_blockscaled_prefill` |
| Quantizer | `flashinfer/cute_dsl/attention/fmha/quantize.py` |
`quantize_blockscaled_qk` |

## 🔍 Related Issues

<!-- Link any related issues here -->
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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a block-scaled CuTe DSL FMHA attention path, including
block-scaled Q/K quantization to drive it.
* Improved `cute-dsl` planning/runtime to support `return_lse` for the
FMHA route.
* Expanded end-to-end and JIT FMHA correctness coverage with
CUDA/SM100a+ gated tests.

* **Bug Fixes**
* Improved robustness when prebuilt FMHA kernels are unavailable by
falling back to JIT compilation and enforcing consistent input dtypes.

* **Chores**
* Updated type-checking and linting exclusions to skip
generated/unsupported FMHA sources.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Ruqing Xu <7891482+xrq-phys@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3837
- **最后更新**: 2026-07-14T15:00:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34061
- **最后更新**: 2026-07-14T22:30:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: yzhautouskay, Steven Liu

## AI分析总结

根据提供的两条提交记录，结合 HuggingFace Diffusers 库（主攻扩散模型与管线）的项目背景，以下是昨日更新的要点总结：

### 1. 主要更新类型
- **功能新增**：为 Cosmos3 模块化管线添加传输支持。
- **代码重构/改进**：引入 `torch.dtype` 别名，并更新相关测试与兼容性修复。

### 2. 关键变更点及与项目方向的关系
- **`torch.dtype` 别名**  
  - 新增 `dtype` 别名机制，统一数据类型引用方式。  
  - 针对 Cosmos 管线保持 `safety_checker` 在 `float32` 的差异，调整测试跳过逻辑（因 T5GemmaEncoder 与 transformers v5 不兼容）。  
  - **关系**：提升代码可维护性与跨管线数据类型处理的灵活性，符合 Diffusers 支持多模型、多精度的目标。

- **Cosmos3 模块化管线传输支持**  
  - 为 Cosmos3 实现独立的转移步骤模块（`Cosmos3TransferSetupStep`），并按照模块化约定重构代码结构。  
  - 临时禁用独立传输工作流，确保集成稳定性。  
  - **关系**：扩展了 Diffusers 对 NVIDIA Cosmos 系列模型（特别是 3 代）的支持，丰富模块化管线生态。

### 3. 对项目的影响与潜在意义
- **Cosmos3 支持**：使社区能够将 Cosmos3 模型无缝集成到 Diffusers 工作流中，增强管线多样性（可能是面向视频生成或高质量图像领域）。  
- **别名机制**：减少因数据类型不一致导致的兼容性问题，为未来多框架（如 `torch.float16` vs `torch.bfloat16`）提供统一入口。  
- **测试兼容性修复**：避免因底层库（transformers）升级导致的测试失败，提升 CI/CD 鲁棒性。

### 4. 值得关注的技术点
- **模块化设计**：Cosmos3 的传输步骤被放置在 `before_encoder.py` 中，与管线核心逻辑解耦，遵循 Diffusers 模块化架构模式。  
- **显式数据类型传递**：Cosmos 管线要求 `safety_checker` 保持 `float32` 并显式传入，提示用户需注意特定模型的数据类型约束。  
- **暂禁独立工作流**：表明传输功能尚需进一步测试，后续可能解锁完整流程。

### 5. 对项目发展的影响（结合项目背景）
- **多模型生态巩固**：Diffusers 作为最主流的扩散模型库，持续吸纳 Cosmos 等前沿生成模型，保持竞争力。  
- **代码质量提升**：别名与兼容性修复降低了维护成本，有助于吸引更多贡献者。  
- **模块化架构演进**：Cosmos3 的传输步骤设计为独立模块，验证了该架构的可扩展性，为后续新模型加入提供模板。

> 注：因提交数量较少，昨日更新偏向增量式功能与代码整理，未涉及重大性能优化或架构变动。

## 详细提交记录

### [23b0004](https://github.com/huggingface/diffusers/commit/23b000433065e2d402080603d73544321d3bc82e)

- **作者**: Steven Liu
- **时间**: 2026-07-14T17:08:01Z
- **提交信息**: torch.dtype alias (#14162)

* alias

* add tests

* feedback

* Fix failing test_dtype_alias pipeline tests

Cosmos pipelines keep the safety_checker in float32 and require it to be
passed explicitly on reload, mirroring their test_torch_dtype_dict
overrides. PRX skips dtype-dict/save-load tests because the custom
T5GemmaEncoder is not compatible with transformers v5; do the same for
test_dtype_alias.

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [e29a9ce](https://github.com/huggingface/diffusers/commit/e29a9ce631478e9250e88414a7302d5397ffc7e8)

- **作者**: yzhautouskay
- **时间**: 2026-07-14T17:07:43Z
- **提交信息**: Transfer support for Cosmos3 ModularPipeline (#14150)

* Add transfer support to the Cosmos3 modular pipeline

* Convention matches fixes

* Align Cosmos3 transfer blocks with modular conventions

* Move Cosmos3TransferSetupStep to before_encoder.py

* Decouple Cosmos3 transfer blocks from task-pipeline internals

* Temporarily disable standalone transfer workflow

* Auto docstring run fix

* Apply style fixes

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 424
- **最后更新**: 2026-07-10T06:55:40Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12693
- **最后更新**: 2026-07-14T18:41:37Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30308
- **最后更新**: 2026-07-14T22:04:49Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 15
- **主要提交者**: Kevin Flansburg, zijiexia, Mick

## AI分析总结

好的，以下是对 `sgl-project/sglang` 仓库昨日提交记录的分析总结，结合项目背景（大模型推理框架）进行解读。

---

### 1. 主要更新类型

| 类型 | 数量 | 示例 |
|------|------|------|
| **功能新增** | 6 | Mamba 卷积窗口可配置、支持 Ideogram V4、统一 RadixTree 默认、DP-attention 调度接收跳过等 |
| **Bug 修复** | 7 | 双倍 KV 释放、Flash MLA 测试路径、tilelang 污染、NPU 拓扑探测、CPU topk 等 |
| **性能优化** | 1 | 设备端 stride KV 索引后再拷贝至主机 |
| **重构/代码清理** | ~30 | ModelRunner 解耦为独立模块、引入 KVCacheConfigurator / WeightUpdater 等新组件 |
| **文档/CI** | 4 | TorchNPU 名称统一、CI 测试修复、cookbook 配图及默认值说明 |
| **其他** | 2 | 内部重构验证工具增强、拆分初始化辅助函数 |

---

### 2. 关键变更点与项目方向的关系

- **

## 详细提交记录

### [463a3f4](https://github.com/sgl-project/sglang/commit/463a3f42482c66eb3163d569d80a7e2f71d9bf2b)

- **作者**: paulzhang-tm
- **时间**: 2026-07-14T21:41:10Z
- **提交信息**: [Mamba] Support configurable conv-window layouts (#31059)

### [08c46e1](https://github.com/sgl-project/sglang/commit/08c46e1f1af0f389b32bc4cd58da9e528889de9d)

- **作者**: paulzhang-tm
- **时间**: 2026-07-14T21:30:31Z
- **提交信息**: Add dummy forward batch preparation hook (#31070)

### [0d89564](https://github.com/sgl-project/sglang/commit/0d89564d27f7b18f655eb90ab68ad2b00f7bdbc9)

- **作者**: karverma-amd
- **时间**: 2026-07-14T21:02:58Z
- **提交信息**: Support scheduler_recv_interval (recv skipper) under DP-attention (#30457)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [bdc9848](https://github.com/sgl-project/sglang/commit/bdc9848c25facc9766e38fa139d25feeb1028f7e)

- **作者**: axx-ty911
- **时间**: 2026-07-14T18:56:08Z
- **提交信息**: [Doc]Standardize the names of PyTorch NPU-related software throughout the documentation by replacing them all with `TorchNPU`. (#29886)

Signed-off-by: a60124901 <anyuxin4@h-partners.com>
Signed-off-by: axx-ty911 <anyuxin4@h-partners.com>
Co-authored-by: sglang-npu-bot <sglangnpu@163.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [cb47a68](https://github.com/sgl-project/sglang/commit/cb47a687170d29d250cc71df883593bcf3867755)

- **作者**: cctry
- **时间**: 2026-07-14T17:08:30Z
- **提交信息**: [PD] Stride KV token->page indices on device before D2H copy (#31173)

Co-authored-by: cctry <cctry@fb.com>

### [a5c3e02](https://github.com/sgl-project/sglang/commit/a5c3e0283f3284ebda56fb1d3a40c0466287ac2c)

- **作者**: hunhokim
- **时间**: 2026-07-14T17:08:24Z
- **提交信息**: [Bug fix] Account for KV replication fan-out in transfer-byte metrics (#30351)

Co-authored-by: Hun-ho Kim <hunho.kim@samsung.com>

### [271e5ef](https://github.com/sgl-project/sglang/commit/271e5ef5c3ac5733908ce270d556985c1dee0624)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-14T16:01:23Z
- **提交信息**: [CI] Fix Flash MLA SM120 test import path (#31199)

### [04af94d](https://github.com/sgl-project/sglang/commit/04af94d150e5921801a6fdafeb042a7b983c250f)

- **作者**: Mick
- **时间**: 2026-07-14T14:30:27Z
- **提交信息**: fix: avoid tilelang cuda runtime pollution (#30870)

### [f853293](https://github.com/sgl-project/sglang/commit/f853293440ade5f95df63483d7d46fe307a6e6e7)

- **作者**: Peng Xingchen
- **时间**: 2026-07-14T14:17:54Z
- **提交信息**: [NPU] Fix CPU device for node topology probe (#30619)

### [3154878](https://github.com/sgl-project/sglang/commit/31548781e04a6d6248f8512bf0c60326be895c2d)

- **作者**: Ma Mingfei
- **时间**: 2026-07-14T13:48:22Z
- **提交信息**: [CPU] bypass scoring_func argument in topk for cpu device (#31110)

### [bbb5702](https://github.com/sgl-project/sglang/commit/bbb5702a3c7faba97ab425b15808cbe5f3ab6f7c)

- **作者**: Kevin Flansburg
- **时间**: 2026-07-14T12:16:58Z
- **提交信息**: fix: avoid double KV release on disaggregated prefill grammar errors (#30937)

Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [43241b7](https://github.com/sgl-project/sglang/commit/43241b7f3fdb2ac0146171bda14b35399b377e5d)

- **作者**: Mick
- **时间**: 2026-07-14T11:51:35Z
- **提交信息**: [diffusion] model: support fal Ideogram V4 Fast and Instant (#31177)

### [ee000f6](https://github.com/sgl-project/sglang/commit/ee000f673458c4d78e5d802a2769990fdf5c303e)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-14T09:32:29Z
- **提交信息**: [CI] Fix SGLANG_JIT_KERNEL_RUN_FULL_TESTS never activating the nightly full jit-kernel sweep (#31042)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [1a35440](https://github.com/sgl-project/sglang/commit/1a35440c4af9e5e39e78feb7cf88f0512b49b295)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-14T08:53:46Z
- **提交信息**: [Kernel] Migrate generic attention kernels to sglang.kernels (RFC #29630, Phase 2.5, 4/7) (#30789)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [a5a71c6](https://github.com/sgl-project/sglang/commit/a5a71c6c26305b75e5203a461e93a38a3a640d2c)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:45:48Z
- **提交信息**: Enhance mechanical-refactor-verify skill with a whole-chain verifier, new relocation primitives, and generator inference (#30585)

### [0fe2dbd](https://github.com/sgl-project/sglang/commit/0fe2dbd42caeb627bd8aca162dab7763d292fda9)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:09:00Z
- **提交信息**: Split initialize() into orchestration helpers (#31169)

### [64a70c9](https://github.com/sgl-project/sglang/commit/64a70c909740ce61b40cedc2d89d5b57d58f968c)

- **作者**: Ankith Averineni
- **时间**: 2026-07-14T08:06:36Z
- **提交信息**: [AMD] jit_kernel: complete utils.cuh HIP-compat (cudaDevAttr / cudaDeviceGetAttribute) (#31143)

### [bf04cc9](https://github.com/sgl-project/sglang/commit/bf04cc9b143b9cc6cd7c69f73ad1ee17cfa1e9ba)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:04:45Z
- **提交信息**: Extract cuda-graph setup into a module (#31168)

### [ed2fcd3](https://github.com/sgl-project/sglang/commit/ed2fcd3201b68b5eb49cc2be48de7b2ea0b4fb84)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:03:48Z
- **提交信息**: Extract attention-backend setup into a module (#31167)

### [54f99a2](https://github.com/sgl-project/sglang/commit/54f99a21d52717ea748d44c86673fcf3c9a9739b)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:03:07Z
- **提交信息**: Narrow component dependencies to injected fields instead of ModelRunner (#31166)

### [6999007](https://github.com/sgl-project/sglang/commit/6999007a13b622ab0a80f904784c13449597019d)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:02:40Z
- **提交信息**: Drop ModelRunner's duplicated parallel-degree fields and read them via self.ps (#31165)

### [cfd1730](https://github.com/sgl-project/sglang/commit/cfd17301a8c4b1f871ca47c7b7aeb4279eafffed)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:02:09Z
- **提交信息**: Extract per-architecture KV-cache pool builders into KVCacheConfigurator (#31163)

### [d6cf290](https://github.com/sgl-project/sglang/commit/d6cf2908ce5bd4b24843c165194972257cc97dcc)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:01:45Z
- **提交信息**: Introduce KVCacheConfigurator and migrate KV-cache config logic (#31162)

### [7259209](https://github.com/sgl-project/sglang/commit/725920915f5b58e052fd8c5e9ffcc8ede238eecb)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:01:14Z
- **提交信息**: Introduce ModelRunner.ps ParallelState (#31161)

### [1dc48c2](https://github.com/sgl-project/sglang/commit/1dc48c2c3bd345e3caa72befac3d8ffeadc1c5ab)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:00:51Z
- **提交信息**: Absorb capturer setup and extract the shared-mooncake gate (#31160)

### [08798db](https://github.com/sgl-project/sglang/commit/08798dba0d8129d595e16b9132b42bc96ab69508)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:00:24Z
- **提交信息**: Extract MoE/EP setup into a moe_ep_setup module (#31159)

### [440aebd](https://github.com/sgl-project/sglang/commit/440aebdfe0f650bf61f9fb5c7a6570c37e2effea)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T08:00:01Z
- **提交信息**: Extract small single-function helpers into modules (#31158)

### [17c0460](https://github.com/sgl-project/sglang/commit/17c04602c645c71d22a81651818e2935ea4d3f5c)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:59:35Z
- **提交信息**: Extract spec aux-hidden-state resolution into a module (#31157)

### [39e508b](https://github.com/sgl-project/sglang/commit/39e508b7fc30bf1792360a8dc9de12431d57f278)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:59:07Z
- **提交信息**: Extract layer-index setup into a module (#31156)

### [5b540b1](https://github.com/sgl-project/sglang/commit/5b540b16de8eb33dd24ad46c056b2c35640efe18)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:58:40Z
- **提交信息**: Extract load_model helpers into a load_model_utils module (#31155)

### [d15f6a9](https://github.com/sgl-project/sglang/commit/d15f6a9ac33a2878a53390976fb1a62286899e76)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:58:08Z
- **提交信息**: Introduce NgramEmbeddingManager component (#31154)

### [0f20f52](https://github.com/sgl-project/sglang/commit/0f20f52e5e0f5067791af38aac6062596fa1fafc)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:57:43Z
- **提交信息**: Introduce RemoteInstanceWeightTransporter component (#31153)

### [caa85ea](https://github.com/sgl-project/sglang/commit/caa85ea022dc58c89ae5782f1f606d70ae55954d)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:56:57Z
- **提交信息**: Extract init_torch_distributed and refactor into functions (#31152)

### [205a2f2](https://github.com/sgl-project/sglang/commit/205a2f2de41eccc35929242586a9e8663a1ee734)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:56:18Z
- **提交信息**: Move LoRA cuda-graph buffers and logging into LoRAManager (#31151)

### [e20c346](https://github.com/sgl-project/sglang/commit/e20c346541b07bff116d365a62a2432aaeb4cee6)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:55:32Z
- **提交信息**: Extract hybrid-arch helpers into configs.hybrid_arch and ModelConfig (#31150)

### [c9b4081](https://github.com/sgl-project/sglang/commit/c9b4081016037ca493c8a99e3d1afcc60e6aaa5c)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:54:40Z
- **提交信息**: Extract expert location updating into EPLBManager (#31149)

### [6507d4a](https://github.com/sgl-project/sglang/commit/6507d4a090aab5339b6e16fca3b1a8b08ec5c1e0)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:53:33Z
- **提交信息**: Introduce WeightUpdater and WeightExporter components (#31148)

### [45dfa31](https://github.com/sgl-project/sglang/commit/45dfa318fb170c8f33559c7b4357cd042021430a)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:52:39Z
- **提交信息**: Extract kv cache dtype configuration into mem_cache (#31147)

### [cad8fe7](https://github.com/sgl-project/sglang/commit/cad8fe7a66100446e53bc5a773a88adf6e4c7859)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:52:03Z
- **提交信息**: Extract leaf helpers out of ModelRunner into utility modules (#31146)

### [b1a60ad](https://github.com/sgl-project/sglang/commit/b1a60ad00d4b5bd5a1f5bfcfc573edf2e735697d)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:50:53Z
- **提交信息**: Clean up ModelRunner by renaming effective-token property and remove dead code (#31145)

### [2cf753c](https://github.com/sgl-project/sglang/commit/2cf753c4feab0640959e0bcf85fce1196606e3ba)

- **作者**: fzyzcjy
- **时间**: 2026-07-14T07:49:05Z
- **提交信息**: Clarify ModelRunner.dp_size into attn_dp_size (#31142)

### [afa3c06](https://github.com/sgl-project/sglang/commit/afa3c06d1fc9396b13235cfe358ae5a96170feb6)

- **作者**: Zhangheng
- **时间**: 2026-07-14T07:17:08Z
- **提交信息**: Using UnifiedRadixTree by default for SWA, Mamba, and DSA models (#30468)

Co-authored-by: ispobock <ispobaoke@gmail.com>

### [7e0b29a](https://github.com/sgl-project/sglang/commit/7e0b29ac03168455bf925788af237d34a83ea8df)

- **作者**: zijiexia
- **时间**: 2026-07-14T07:08:49Z
- **提交信息**: docs: add VLA card image to cookbook overview (#31132)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [96c2ebc](https://github.com/sgl-project/sglang/commit/96c2ebc58ba15edd3f75d8ac7e2daab766f0c630)

- **作者**: zijiexia
- **时间**: 2026-07-14T07:04:47Z
- **提交信息**: [docs] Note the default dsa-topk-backend on all DSA-model cookbook pages (#31124)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1227
- **最后更新**: 2026-07-14T06:20:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86265
- **最后更新**: 2026-07-14T23:07:12Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 19
- **主要提交者**: Srinivas Krovvidi, Matthew Bonanni, Artur Fierka

## AI分析总结

好的，根据你提供的 vllm-project/vllm 仓库 README 背景（致力于为所有人提供**简单、快速、低成本**的 LLM 服务）以及昨日的 22 条提交记录，以下是更新要点总结：

---

### 1. 主要更新类型

| 类型 | 数量 | 说明 |
|------|------|------|
| **Bug 修复** | 约 8 项 | 涵盖 MLA/SWA 检查、Gemma4 流式输出、MoRIIO 健康端点、安全竞争条件、多模态输入错误状态码等 |
| **性能优化 / 调优** | 约 4 项 | TPOT 推理预算优化、FlashAttention MLA 维度支持、ROCm MI355 调优、KV offload 监控拆分 |
| **新模型 / 新功能支持** | 2 项 | 新增 Cosmos3 Edge Reasoner 模型、LlavaNextVideo LoRA 支持 |
| **CI/CD 与构建** | 4 项 | macOS arm64 原生构建、Intel GPU CI 滑动窗口测试、ROCm flashinfer 检查修复、MLS 精度问题修复 |
| **安全修复** | 2 项 | 并发稀疏不变性绕过 CVE、lm-format-enforcer 正则超时防护 |
| **重构 / 重命名** | 1 项 | TRITON 后端环境变量重命名（`VLLM_TRITON_ATTN_USE_TD` → `VLLM_TRITON_USE_TD`） |
| **文档 / 注释同步** | 1 项 | 同步 4 个函数文档字符串与签名 |
| **测试增强** | 1 项 | CPU offloading 测试中启用 HMA 模型的 KV cache 事件 |

---

### 2. 关键变更点与项目方向关系

- **新增 Cosmos3 Edge Reasoner 模型**（#48291）  
  → 扩展模型生态，进一步实现“支持更多模型”的目标。Edge 模型暗示对边缘设备推理的支持，符合“便宜”的愿景。

- **LlavaNextVideo LoRA 支持**（#48594）  
  → 完善多模态模型适配，使视觉语言模型更易微调部署，降低定制成本。

- **TPOT 优化 + 推测解码思维预算**（#46662）  
  → 在推理阶段通过思考预算动态优化 Token 生成时间，直接提升速度和效率，是“快速”的核心改进。

- **拆分 KV Offload 读写利用率监控**（#47666）  
  → 更精细的缓存管理指标，提升运维可见性，有助于成本控制和稳定性。

- **安全修复两处**（#48583, #47595）  
  → 防止并发竞争和正则注入，保护服务免受 CVE 攻击，增强系统健壮性，对“服务化”至关重要。

- **环境变量和 CI 标准化**（#45781, #48289 等）  
  → 清理内部命名（Triton 相关）、原生构建 macOS 轮子，提升开发者体验与跨平台可维护性。

---

### 3. 对项目的影响与潜在意义

| 领域 | 影响 |
|------|------|
| **性能** | TPOT 优化和 FlashAttention MLA 修复能直接提升推理吞吐和首 Token 延迟，尤其对长上下文和推理密集型场景（如思维链、多步推理）意义重大 |
| **稳定性** | 多个 Bug 修复（Gemma4 输出不一致、多模态错误码、页面传输宽度等）减少服务异常，提升用户体验 |
| **安全性** | 两个 CVE 相关修复降低了被利用风险，对生产环境部署至关重要 |
| **生态兼容性** | 新增模型（Cosmos3）、LoRA 支持、ROCm/XPU CI 扩展，使 vLLM 能在更多硬件和模型上运行，拓宽“人人可用”的范围 |
| **可观测性** | KV offload 监控细化帮助运营团队优化成本与性能平衡 |

---

### 4. 值得关注的技术点

- **MoRIIO 代理健康检查端点**（#45222）：说明社区正在将 vLLM 集成到更复杂的分布式推理架构（如 P/D 分离）中，可能需要关注。
- **MLA + SWA 精度修复**（#48520）：针对 Multi-head Latent Attention + Sliding Window Attention 的组合，是近年大模型压缩的关键技术，修复影响深远。
- **并发稀疏不变性绕过 CVE**（#48583）：暗示 vLLM 内部的稀疏计算存在竞态条件，安全团队有意识地在修复，未来可能加强并发相关安全审计。
- **DSv3.2 + MTP + Sequence Parallel 精度问题**（#48036）：多令牌预测与序列并行的组合优化，提示 vLLM 在探索下一代加速架构。
- **NIXL 双向读取过期块预防**（#47021）：跨节点通信模块（NIXL）的稳定性改进，对分布式推理至关重要。

---

### 5. 结合 README 背景，这些提交如何影响项目发展

- **“简单”**：函数文档同步、环境变量重

## 详细提交记录

### [520a20b](https://github.com/vllm-project/vllm/commit/520a20ba4e2d2a15e58f34751f668bd8d046bc45)

- **作者**: chaeminlim-mb
- **时间**: 2026-07-14T22:56:46Z
- **提交信息**: [Bugfix] MoRIIO toy P/D proxy: add /health (#45222)

Signed-off-by: Chaemin Lim <chaemin.lim@mangoboost.io>
Signed-off-by: Edwin Lim <edwinlim0919@gmail.com>
Co-authored-by: Edwin Lim <edwin.lim@mangoboost.io>
Co-authored-by: Jaeyoun Kim <jaeyoun.kim@mangoboost.io>
Co-authored-by: Edwin Lim <edwinlim0919@gmail.com>

### [9182e86](https://github.com/vllm-project/vllm/commit/9182e8697133e95f6e4ed236628a344b12e1c702)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-14T22:00:46Z
- **提交信息**: Log fully resolved pooling config at startup (#48030)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [313d01f](https://github.com/vllm-project/vllm/commit/313d01f507fc86306960aadf7939d2b7376b3a90)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-14T21:33:02Z
- **提交信息**: [CI][Bugfix] Fix FlashAttention reported MLA dimension support (#48631)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [05d4f8b](https://github.com/vllm-project/vllm/commit/05d4f8bba3aac85814c3fc42cfc60bef21bb2bb4)

- **作者**: Divakar Verma
- **时间**: 2026-07-14T20:54:19Z
- **提交信息**: [ROCm][CI] fix flashinfer import check (#48647)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [0b54201](https://github.com/vllm-project/vllm/commit/0b54201a044c419e07a4bd464adf91e576640977)

- **作者**: Michael Goin
- **时间**: 2026-07-14T19:40:26Z
- **提交信息**: [CI] Build macOS arm64 CPU wheel natively on the macmini queue (#48289)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [32e632d](https://github.com/vllm-project/vllm/commit/32e632dfeb0860d11332754e641035ddd755f89f)

- **作者**: rishitdholakia13
- **时间**: 2026-07-14T18:55:40Z
- **提交信息**: [Reasoning] Optimize TPOT for thinking budget when used with speculative decoding (#46662)

Signed-off-by: rishitdholakia13 <rishit+github@cohere.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [7ffb98e](https://github.com/vllm-project/vllm/commit/7ffb98e248c03fc65c38472aac8ed2ee577c09a9)

- **作者**: vanshbhatia-amd
- **时间**: 2026-07-14T18:26:35Z
- **提交信息**: [ROCm] Retune MI355 selective_state_update float32 config on the unified effective_batch grid (#48373)

Signed-off-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>
Co-authored-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>

### [cdaa40d](https://github.com/vllm-project/vllm/commit/cdaa40d2a8c9297349669fc6e7db6dcb282df0b8)

- **作者**: Srinivas Krovvidi
- **时间**: 2026-07-14T17:13:41Z
- **提交信息**: [KV Offload] Split cpu_cache_usage_perc into write/read usage gauges (#47666)

Signed-off-by: srinivas_oo7 <sklinkedin0120@gmail.com>
Co-authored-by: srinivas_oo7 <sklinkedin0120@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [ca3618b](https://github.com/vllm-project/vllm/commit/ca3618bc698ed029c971a359f9b2b5bc1d041bb8)

- **作者**: Daoyuan Li
- **时间**: 2026-07-14T17:10:13Z
- **提交信息**: [Doc] Sync four function docstrings with their signatures (#45437)

Signed-off-by: Daoyuan Li <94409450+DaoyuanLi2816@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b2f7d25](https://github.com/vllm-project/vllm/commit/b2f7d2560ae66122bb90b670d8c626216dc48f5f)

- **作者**: Michael Goin
- **时间**: 2026-07-14T16:53:34Z
- **提交信息**: [Bugfix] Make MLA+SWA check the layer's backend, not the model config (#48520)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [1ff9429](https://github.com/vllm-project/vllm/commit/1ff9429655f01c804a7b17412144323e804f1324)

- **作者**: Wentao Ye
- **时间**: 2026-07-14T14:00:24Z
- **提交信息**: [CI Bug] Fully solve accuracy issue for DSv3.2 + MTP + Sequence Parallel (#48036)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [af453e5](https://github.com/vllm-project/vllm/commit/af453e5647773b6edb89230148b9fabeea0ace21)

- **作者**: adhi29
- **时间**: 2026-07-14T13:30:16Z
- **提交信息**: [Bugfix] Gemma4 parser: classify channel-less output consistently in streaming and non-streaming (#48262)

Signed-off-by: Adhithya Balakrishnan <adhithya.b2004@gmail.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [32aef44](https://github.com/vllm-project/vllm/commit/32aef4438822f90310d2a709b71192f30da2fea8)

- **作者**: Itay Etelis
- **时间**: 2026-07-14T13:07:26Z
- **提交信息**: [Bugfix] Include inline per-token-head scales in offloaded page transfer width (#48411)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Signed-off-by: Itay Etelis <Itay.etelis@gmail.com>
Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <Itay.etelis@gmail.com>

### [7a74a96](https://github.com/vllm-project/vllm/commit/7a74a9662bff4e5ef91f210f41b7f930de3df0bc)

- **作者**: tomerg-nvidia
- **时间**: 2026-07-14T13:03:41Z
- **提交信息**: [NIXL] Avoid reading expired blocks in bidirectional turn-2 read (#47021)

Signed-off-by: Tomer Gilad <tgilad@nvidia.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [b6754f5](https://github.com/vllm-project/vllm/commit/b6754f536e9cb40a1e117705a44d74218873b437)

- **作者**: karthik
- **时间**: 2026-07-14T12:09:38Z
- **提交信息**: [Model] Enable LoRA support for tower and connector in LlavaNextVideo (#48594)

Signed-off-by: gangula-karthik <gkarthik923@gmail.com>

### [793cf79](https://github.com/vllm-project/vllm/commit/793cf79c89d4049124e756915468ac30318f2e50)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-07-14T11:08:24Z
- **提交信息**: [Bugfix][Security] Fix concurrent sparse invariant race bypassing CVE remediation (#48583)

Signed-off-by: jperezde <jperezde@redhat.com>

### [50ac1c7](https://github.com/vllm-project/vllm/commit/50ac1c7bab47f14d56d86967532574824d02260e)

- **作者**: Artur Fierka
- **时间**: 2026-07-14T10:32:57Z
- **提交信息**: [Misc] Rename VLLM_TRITON_ATTN_USE_TD to VLLM_TRITON_USE_TD (#45781)

Signed-off-by: Artur Fierka <artur.fierka@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f04d3f6](https://github.com/vllm-project/vllm/commit/f04d3f640e41ff217d4a793c315438aa2878f193)

- **作者**: Itay Etelis
- **时间**: 2026-07-14T09:22:27Z
- **提交信息**: [Test] Enable KV cache events for HMA models in CPU offloading test (#47754)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [0a9396a](https://github.com/vllm-project/vllm/commit/0a9396a25e3c2c399cde4f748ca6b2209b9dafe7)

- **作者**: xiangdong
- **时间**: 2026-07-14T08:50:16Z
- **提交信息**: [XPU][CI] Add tests/v1/e2e/general/test_correctness_sliding_window.py in Intel GPU CI (#47231)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>
Signed-off-by: xiangdong <40376367+zxd1997066@users.noreply.github.com>

### [038ec29](https://github.com/vllm-project/vllm/commit/038ec293b17d8d1018b5494a97187597b10c5182)

- **作者**: Hoang Nguyen
- **时间**: 2026-07-14T08:15:43Z
- **提交信息**: [Bugfix] Return 400 instead of 500 when multimodal data is sent to a text-only model (#48473)

Signed-off-by: Hoang Nguyen Tien <hoang.nguyentien.2601@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [894ebb2](https://github.com/vllm-project/vllm/commit/894ebb27f5c7d7f8758266163ffd503132e432d2)

- **作者**: adsridhar
- **时间**: 2026-07-14T08:14:50Z
- **提交信息**: Add Cosmos3 Edge Reasoner model (#48291)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>
Co-authored-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [c9a788e](https://github.com/vllm-project/vllm/commit/c9a788eedc412acceaa5112e0d44624b49841577)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-07-14T07:18:11Z
- **提交信息**: fix(security): guard lm-format-enforcer regex compile with timeout (#47595)

Signed-off-by: jperezde <jperezde@redhat.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-15
**监控日期**: 2026-07-14
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5561
- **最后更新**: 2026-07-14T15:59:15Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: bjf-frz, Weiming Liao, Alex Steiner

## AI分析总结

以下是昨日（基于提交记录）`vllm-project/vllm-omni` 仓库的更新要点总结：

---

### 1. 主要更新类型
- **Bug 修复**：3 个（#5103、#5088、#4941）
- **功能新增**：1 个（#5037，BitsAndBytes W4 量化）
- **重构**：1 个（#4922，扩散输出重构）
- **性能优化 / CI**：1 个（#5010，添加扩散性能测试配置）
- **配置 / 配方**：1 个（#4978，Cosmos3-nano NPU 配方）
- **基础设施**：1 个（#5095，NPU CI 镜像升级）

---

### 2. 关键变更点及其与项目方向的关系
| 提交 | 变更内容 | 与项目方向（Easy, Fast, Cheap, Omni-modal）的关系 |
|------|----------|-----------------------------------------------------|
| #5103 #5088 | 修复量化组件初始化状态、支持 HSDP 下的打包参数 | 提升量化稳定性与兼容性 → **Cheap（低成本）** |
| #5037 | 添加 BitsAndBytes W4 在线量化，针对扩散 Transformer | 新型模型压缩方法 → **Fast + Cheap**，降低显存与计算 |
| #4922 | 重构扩散模型输出为 payload metadata | 统一输出格式，便于多模态扩展 → **Omni-modal** 标准化 |
| #5010 | 添加 Cosmos3 扩散性能配置到 CI | 保障扩散模型性能基线 → **Fast**，提升 CI 覆盖 |
| #4941 | 修复 `kv_prefetch_jobs` 参数接受 |

## 详细提交记录

### [6603450](https://github.com/vllm-project/vllm-omni/commit/6603450d71619d0731ca26ba8a077a3ac491bd77)

- **作者**: wuli666
- **时间**: 2026-07-14T12:06:55Z
- **提交信息**: [Bugfix][Quantization] Initialize component quantization base state (#5103)

Signed-off-by: wuli666 <djjpro975@gmail.com>
Co-authored-by: wuli666 <djjpro975@gmail.com>

### [b14ff23](https://github.com/vllm-project/vllm-omni/commit/b14ff23041cc88b393260d4ee7100671e7871176)

- **作者**: bjf-frz
- **时间**: 2026-07-14T10:25:17Z
- **提交信息**: [PERF][CI]Add Cosmos3 diffusion perf config (#5010)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [1a4a042](https://github.com/vllm-project/vllm-omni/commit/1a4a042a8307033a5f2a8ebf34ec866737560994)

- **作者**: bjf-frz
- **时间**: 2026-07-14T09:24:03Z
- **提交信息**: [REFACT]Refactor diffusion outputs to payload metadata (#4922)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [4b9d09c](https://github.com/vllm-project/vllm-omni/commit/4b9d09cb8752631c9cb704e91028a800274f89d8)

- **作者**: Alex Steiner
- **时间**: 2026-07-14T08:24:26Z
- **提交信息**: [Bugfix][Quantization] Support packed parameters with HSDP (#5088)

Signed-off-by: Alex Steiner <asteiner@nvidia.com>

### [3589a67](https://github.com/vllm-project/vllm-omni/commit/3589a676e22bc1cee8ccc4d0f62ddc5834aa2eaa)

- **作者**: wjsuijlenh
- **时间**: 2026-07-14T08:22:40Z
- **提交信息**: [Bugfix] Accept kv_prefetch_jobs in ARDiffusionModelRunner.execute_model (#4941)

Signed-off-by: Wijnand Suijlen <wijnand.suijlen@huawei.com>

### [b180998](https://github.com/vllm-project/vllm-omni/commit/b1809985ef30a8b60a0c1d3d6b6e8b4aabe529c5)

- **作者**: Zhang Jian
- **时间**: 2026-07-14T08:19:44Z
- **提交信息**: [recipe] Add cosmos3-nano recipe for npu (1xA3) (#4978)

Signed-off-by: Zhang Jian <jianmusings@gmail.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>

### [e0570a0](https://github.com/vllm-project/vllm-omni/commit/e0570a08596fb9a85d392531bc07e509c38867dc)

- **作者**: Diya Peng
- **时间**: 2026-07-14T07:48:48Z
- **提交信息**: [Quantization] Add BitsAndBytes W4 online quantization for diffusion transformer (#5037)

Signed-off-by: diyapeng <50388704+diyapeng@users.noreply.github.com>
Co-authored-by: diyapeng <50388704+diyapeng@users.noreply.github.com>

### [b20ebc8](https://github.com/vllm-project/vllm-omni/commit/b20ebc8f9ba405f25cb941969804645b87d998be)

- **作者**: Weiming Liao
- **时间**: 2026-07-14T07:47:02Z
- **提交信息**: [NPU] Upgrade CI IMAGE to v0.25.0 (#5095)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

---
