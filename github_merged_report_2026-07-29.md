# GitHub Stars 合并报告 - 2026-07-29

**合并日期**: 2026-07-30
**监控日期**: 2026-07-29
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


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2114
- **最后更新**: 2026-07-29T19:58:23Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Coach257

## AI分析总结

根据提供的提交记录，以下是昨日（基于该提交日期推断）更新的要点分析：

### 1. 主要更新类型
- **功能新增 & 文档更新**（feat + docs）：新增了关于 Cursor Cloud（仅 CPU）开发环境的说明文档。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在 `agent` 和 `docs` 模块中，增加了有关如何在 Cursor Cloud（一种云端 IDE，仅提供 CPU 资源）上搭建 VeOmni 开发环境的说明（笔记/指南）。
- **与项目方向关系**：VeOmni 定位为“以模型为中心的分布式配方动物园”，旨在支持任意模态（文本、图像、视频等）的大规模模型训练。通常此类训练依赖 GPU 集群，但开发、测试、代码调试等环节并不总是需要 GPU。该提交通过提供 **CPU-only 开发环境** 的配置指引，降低了开发者的环境准备门槛，使更多贡献者（尤其是缺乏 GPU 资源的开发者）能够参与代码修改、调试和实验，从而促进社区的协作和发展。

### 3. 对项目的影响和潜在意义
- **降低贡献门槛**：新用户可以借助免费/低成本的 CPU 云端环境快速启动开发，无需本地拥有高性能 GPU，有利于吸引更多开源贡献者。
- **提升开发效率**：Cursor Cloud 等云端 IDE 提供统一的开发环境，避免因本地环境差异导致的兼容性问题，方便团队协作。
- **完善基础设施文档**：作为项目文档的一部分，该提交补充了环境配置的缺失环节，使整体文档体系更完整。

### 4. 值得关注的技术点
- **CPU-only 开发限制**：虽然 VeOmni 主要面向 GPU 训练，但此提交意味着开发者可以在 CPU 模式下验证代码逻辑（例如数据预处理、模型结构、分布式调度逻辑等），仅推理/训练步骤无法完整执行。这是一种常见的开源项目实践（如 PyTorch 的 CPU-only 安装）。
- **Cursor Cloud 集成**：选择了 Cursor（基于 VS Code 的 AI 辅助 IDE）的云版本，说明项目团队关注现代开发工具与 AI 辅助的整合。

### 5. 基于项目背景的提交影响分析
- **推动社区化进程**：项目 README 强调“Scaling Any Modality Model Training”，需要大量社区贡献来完善不同模态的配方（recipe）。添加 CPU-only 开发指南有助于吸引非硬核 GPU 拥有者参与代码维护、文档完善和轻量级测试。
- **强化“Developer Experience”**：作为分布式训练框架，开发体验（DX）是项目成功的关键。该提交体现了对贡献者使用体验的重视，符合顶级开源项目“文档优先”的惯例。
- **为后续自动化测试打基础**：CPU 环境适合运行单元测试和代码风格检查，未来可能推动 CI 流程的 CPU-only 测试套件建设。

**总结**：这是一个小而精准的贡献，通过完善开发环境文档来降低社区参与壁垒，符合 VeOmni 作为开放性多模态训练框架的增长逻辑。

## 详细提交记录

### [df866c5](https://github.com/ByteDance-Seed/VeOmni/commit/df866c5e832145515be612e3a64372e2e0ca8181)

- **作者**: Coach257
- **时间**: 2026-07-29T08:27:53Z
- **提交信息**: [agent, docs] feat: add Cursor Cloud (CPU-only) dev environment notes (#997)

Co-authored-by: Coach257 <Coach257@users.noreply.github.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2542
- **最后更新**: 2026-07-29T18:00:26Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

### 主要更新类型
- **性能优化**：所有三条提交均围绕推理性能的**warmup（预热）与compile（编译）** 展开，属于运行时优化。
- **功能新增**：为多个模型/任务新增了预热与编译的支持。

### 关键变更点与项目方向关系
1. **warmup & compile 核心能力扩展**：
   - `[#1309]` 对 `skill` 模型启用 warmup 和 compile。
   - `[#1308]` 对 `LingBot-Video` 模型新增支持 text-to-image (t2i)、text-to-video (t2v) 和 image-to-video (i2v) 的预热与编译。
   - `[#1307]` 对 `ltx2 / ltx2.3` 模型以及 `i2av / t2av unsample` 流程加入编译支持，并涉及 `default` 和 `cpu_offload` 策略。
   
   这些变更直接指向**加速推理**，符合项目“轻量视频生成推理框架”的定位——在保持模型能力的同时，降低推理延迟与资源开销。

### 对项目的影响和潜在意义
- **性能提升显著**：预热可减少首次推理的冷启动延迟；图编译（如 `torch.compile`）能通过算子融合与内核优化提升吞吐量。
- **兼容性扩展**：覆盖了多个主流模型（LingBot-Video, LTX系列）和多模态任务（t2i/t2v/i2v/i2av），使框架的通用性更强。
- **降低部署门槛**：`cpu_offload` 支持显存不足的场景，有利于在消费级硬件上运行视频生成模型。

### 值得关注的技术点
- **编译与默认策略**：`#1307` 中提到的 `default` 和 `cpu_offload` 可能区分了不同显存预算下的编译行为，值得查看具体配置。
- **warmup 实现**：如何预热（如执行若干次虚拟推理）以及是否可自定义预热步数。
- **compile 与模型动态性兼容**：视频生成常涉及可变长度或循环结构，编译是否能有效处理动态计算图需关注。

### 对项目发展的影响
- **向前沿推理能力靠拢**：预热与编译是当前高效推理框架（如 vLLM、TensorRT-LLM）的标准能力，LightX2V 的此轮更新使其向“生产就绪”迈进。
- **吸引更多用户与模型贡献**：性能优化后，更易被下游开发者集成，也可能促进社区贡献更多模型适配。
- **为未来功能铺路**：编译基础设施成熟后，可进一步支持量化、稀疏化等高级优化，持续强化“轻量”标签。

## 详细提交记录

### [ea403a1](https://github.com/ModelTC/LightX2V/commit/ea403a17450a537ee517a5b42bb581d5f2440f70)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-29T12:16:33Z
- **提交信息**: skill: warmup and compile (#1309)

### [bf1d1a5](https://github.com/ModelTC/LightX2V/commit/bf1d1a5a6f514dd8a131186bd685e097b308ccae)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-29T11:56:13Z
- **提交信息**: LingBot-Video: t2i t2v and i2v support warmup and compile (#1308)

### [12fed15](https://github.com/ModelTC/LightX2V/commit/12fed156bab364dc354239a73875d04f71682411)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-29T08:47:25Z
- **提交信息**: compile: ltx2 and ltx2.3, i2av t2av unsample, default and cpu_offload… (#1307)

…(model, block)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2181
- **最后更新**: 2026-07-29T08:35:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6062
- **最后更新**: 2026-07-29T21:50:17Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Jonathan Dierksen, CarstyYou, Brayden Zhong

## AI分析总结

分析生成失败

## 详细提交记录

### [57b7719](https://github.com/flashinfer-ai/flashinfer/commit/57b771995132d077012f4400ca52a89f607296e2)

- **作者**: Brayden Zhong
- **时间**: 2026-07-29T21:50:05Z
- **提交信息**: Fix the routing inconsistency for num_groups > 1 (#3946)

(For example, this epsilon is in official DSV3.2 inference demo
https://github.com/deepseek-ai/DeepSeek-V3.2-Exp, and it's currently
applied when num_groups = 1 (GLM 5.x), but not this path. Add it for
potential fix for instability when using f32 expert correction bias.

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [d193c3f](https://github.com/flashinfer-ai/flashinfer/commit/d193c3f0e371564f9f831be913af958018c8ed8f)

- **作者**: Md Saidul Hoque Anik
- **时间**: 2026-07-29T21:08:37Z
- **提交信息**: perf(moe_ep): CuTe-DSL 4.5.2 mainloop WAR — drop the 4.6.1 runtime floor (#4101)

## Summary

`nvidia-cutlass-dsl==4.5.2` codegen has a regression that makes the
cutedsl MegaMoE nvfp4 swap-AB fc12 kernel 34–54% slower than 4.6.1 at
every token count (documented in `kernel_src/cutedsl_megamoe/TUNING.md`,
"CuTe-DSL runtime sensitivity"). This mattered because vLLM 0.25.1 pins
exactly 4.5.2, forcing integrations to carry a 4.6.1 force-upgrade plus
its compat chain (quack, tvm-ffi, tilelang, vendored-kernel patches).

This PR ports cutedsl_megamoe MR!27 (single file:
`src/moe_nvfp4_swapab/kernel_fc12.py`): when the installed DSL is
exactly 4.5.2, the MMA-consumer k-tile mainloop is peeled by one
iteration (unconditional `try_wait` inside the loop, last tile issued
after it). The gate is `cutlass.const_expr`-folded at trace time, so on
any other version the generated kernel is byte-identical to before.

## Version support matrix (all measured, 4x GB200, default geometry)

| DSL version | nvfp4 µs @1024/2048/8192 | status |
|---|---|---|
| 4.5.0 | — | fails at `cute.compile` (unsupported) |
| 4.5.1 | — | unmeasured; shim warns (<4.5.2) |
| 4.5.2 without WAR | 583.7 / 878.6 / 2579.5 | the regression |
| **4.5.2 + this WAR** | **428.6 / 621.5 / 1896.4** | full parity |
| 4.5.3 | 424.4 / 613.3 / 1933.3 | natively fast (upstream fix) |
| 4.6.0 | 427.0 / 614.1 / 1922.0 | natively fast |
| 4.6.1 | 428.5 / 625.6 / 1923.5 | reference |

Support statement: **>= 4.5.2 at full performance; < 4.5.2
unsupported.** The regression existed only in 4.5.2 and was fixed
upstream in 4.5.3, so the exact `== 4.5.2` gate never affects any other
version.

## Validation (all on pinned 4.5.2, 2026-07-22)

- **Correctness:** full `tests/moe_ep/run_tests.sh all` — all 8 sections
PASS (unit, torch-oracle, split multirank, bf16/nvfp4/ht correctness,
mega multirank, smoke).
- **Microbenchmark:** full 5-variant × 7-token-point reference sweep
reproduces the 4.6.1 reference within run noise at every cell; adopted
as the new TUNING.md reference table. mxfp8 needs no WAR (never
regressed — measured).
- **vLLM 0.25.1 e2e (DeepSeek-V4-Flash, 4x GB200):** headline pair
reproduces on vLLM's own 4.5.2 pin with no force-upgrade: prefill-8k
**1.176x** native (53,623 vs 45,582 tok/s), decode-1k **1.068x** (34,263
vs 32,086 total tok/s) — within 0.7% of the 4.6.1-stack references.

## Changes

- `kernel_src/cutedsl_megamoe/src/moe_nvfp4_swapab/kernel_fc12.py`: the
MR!27 loop peel, `const_expr`-gated on `== 4.5.2`.
- `kernel_src/cutedsl_megamoe/shim/__init__.py`: perf-floor warning now
fires only below 4.5.2, with the measured support matrix in the
docstring.
- `kernel_src/cutedsl_megamoe/TUNING.md`: 2026-07-15 sensitivity section
marked OBSOLETE (kept as record); reference tables re-measured on 4.5.2
and adopted; version-gap measurements and support statement added.

AI-assisted (Claude Code): MR port, benchmark reruns, and docs.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

- **Performance**
- Improved NVFP4 MoE behavior for supported CuTeDSL versions, including
corrected 4.5.2 handling.
- Refreshed microbenchmark and vLLM end-to-end results, with clarified
throughput metrics and updated guidance on valid “performance floor”
claims.

- **Compatibility**
- Added an import-time warning for outdated CuTeDSL versions, with an
environment variable to suppress it.

- **Bug Fixes**
- Fixed zero-token routing/staging to correctly reset masked outputs in
both fused and non-fused paths.

- **Documentation / Tests**
- Expanded the benchmarking runbook and tuning instructions; added a GPU
regression test for zero-token masking.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>

### [8b6af1a](https://github.com/flashinfer-ai/flashinfer/commit/8b6af1aaa5bb9b146eeb4b456cbc821f49cb71fa)

- **作者**: Enwei Zhu
- **时间**: 2026-07-29T10:16:13Z
- **提交信息**: fix(moe): pad trtllm-gen route map by one element to avoid OOB read (#4237)

## 📌 Description

The routed dynamic-batch batched-GEMM kernels (`Bmm_*_dynB` with
`-routeAct`)
read one `int32` past the end of `ptrRouteMap`, from the last batch-dim
CTA, on
every launch. The read is speculative — its value is never consumed, so
outputs
are always bitwise correct — but it faults with
`CUDA_ERROR_ILLEGAL_ADDRESS`
whenever the allocation happens to end at a mapped-region boundary. That
allocator-placement dependence is what makes it surface as *flaky* MoE
autotune
and inference crashes.

Root cause is kernel-side: an off-by-one clamp in the hoisted load-task
initializer (`WarpGrpThreadIdx` is clamped to the load-group size
instead of
size − 1), so off-group threads compute row `tileN` of a `tileN`-row
tile, i.e.
index `(ctaIdxY + 1) * tileN`. For the last CTA that is exactly one
element past
the shape documented in `KernelParamsDecl.h`
(`[sum(divUpMul(N[bi], tileN) for bi in B)]`) — which is what we
allocate. It has
been reported to the kernel owners and is being fixed there.

This PR is the integration-side workaround: allocate the route map with
one
extra element, so the already-shipped prebuilt cubins stay in bounds.
The
overrun is provably always exactly one `int32` from one CTA, so `+1` is
sufficient by construction, not a heuristic. The pad slot's contents are
irrelevant since the value is never used.

Two allocation sites, both `permuted_idx_to_token_idx` (→ `routeMap`).
Marked
`WAR` + `TODO` so the `+1` can be dropped once regenerated cubins land.

## 🔍 Related Issues

Likely explains #3530 and #3168 (and possibly #4012, #2776) — all report
intermittent NVFP4 MoE autotune crashes, and #3168 additionally reports
silent
garbage output, which is the expected signature of an OOB read that
usually
lands on mapped memory.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

No test added — the failure is allocator-placement dependent and does
not
reproduce deterministically through the public API. Validation was done
on
`v0.6.15.post1` (B200, SM100, Kimi-K2.5 NVFP4 TP4):

| Check | stock | route map +1 |
|---|---|---|
| `compute-sanitizer` memcheck, M=2 bucket × 4 ranks | 40 × `Invalid
__global__ read of size 4` | **0 violations** (816 profiles/rank) |
| Guard-page probe (route map placed at the tail of a VMM mapping) |
faults on every launch | **clean** |
| Full-model TP4 autotune crash loop | crashed by attempt 2 in 3/3 loops
| **6/6 clean** |

The guard-page probe is the load-bearing one: it removes all dependence
on
allocator placement, so it is deterministic in both directions.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved stability for fused mixture-of-experts routing operations by
preventing out-of-bounds memory access in supported execution paths.
* Applied the safeguard to both standard and FP4 block-scale routing
workflows.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Enwei Zhu <21126786+syuoni@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [92274ba](https://github.com/flashinfer-ai/flashinfer/commit/92274ba15efbc5241305989e1f6d2dbaf47faa7a)

- **作者**: CarstyYou
- **时间**: 2026-07-29T08:39:20Z
- **提交信息**: feat(sm120): fused MoE (SwiGLU) via moe_gemm is_gated for cute SM120 groupwise GEMM (#4130)

## 📌 Description

Adds **fused MoE FC1** (GEMM1 + SwiGLU in a single kernel) and a
**warp-cooperative MoE scheduler** to the SM120 CuTe groupwise MoE GEMM
entry. Fusion is exposed via an `is_gated` flag on the existing
`moe_gemm_{fp8,mxfp8}_nt_groupwise` API. Follow-up to #3562 (MXFP8) and
#3891 (FP8), sharing the same in-tree kernel package and JIT module.

With `is_gated=True` the kernel reads the `2I` gate+up weight (up in the
first `I` columns of N, gate in the second), applies `up * SiLU(gate)`
in the epilogue, and writes the `I`-wide activated output — fusing away
the `2I` intermediate global write+read and the separate activation
launch.

**Entry**: `flashinfer.grouped_mm.moe_gemm_{fp8,mxfp8}_nt_groupwise(a,
b, a_scale, b_scale, m_indptr, scale_granularity_mnk, out=None,
is_gated=False)`. `is_gated=True` requires even `b.size(1)` and halves
output N to `I`.

## Benchmark 1: fused vs unfused

- **fused** = `moe_gemm_*_nt_groupwise(..., is_gated=True)` — GEMM1 +
SwiGLU in one kernel.
- **unfused** = `moe_gemm_*_nt_groupwise(..., is_gated=False)` producing
the `2I` gate+up, then a standalone Triton SwiGLU.
- CUPTI kernel-level, warmup 20 + 50-iter median, exclusive serial.
Quant / scale-transform / routing / output allocation are outside the
timed window; the unfused window covers GEMM + SwiGLU back-to-back.
- **Δ = fusion speedup = `(unfused_us / fused_us − 1) × 100%`**
(positive = fused faster). FP8 and MXFP8 reported separately.

FC1 shapes: **Qwen3.5-35B** (E=256, K=2048, 2I=1024) · **Qwen3-235B**
(E=128, K=4096, 2I=3072) · **DeepSeek-V3** (E=256, K=7168, 2I=4096).
DeepSeek-V3 tops out at MPE=512, the other two at 1024.

### RTX PRO 6000 Blackwell Server Edition (SM120a, 188 SM)

#### Qwen3.5-35B

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 415.7 | 417.2 | +0.4% | 425.9 | 428.9 | +0.7% |
| 4 | 418.9 | 420.7 | +0.4% | 427.9 | 432.8 | +1.1% |
| 8 | 422.2 | 424.6 | +0.6% | 430.2 | 437.0 | +1.6% |
| 16 | 431.2 | 433.4 | +0.5% | 436.1 | 445.2 | +2.1% |
| 32 | 444.1 | 447.8 | +0.8% | 443.8 | 459.3 | +3.5% |
| 64 | 457.0 | 480.7 | +5.2% | 461.4 | 490.4 | +6.3% |
| 128 | 486.1 | 544.5 | +12.0% | 494.4 | 555.2 | +12.3% |
| 256 | 552.9 | 694.9 | +25.7% | 567.0 | 708.0 | +24.9% |
| 1024 | 1568.5 | 2087.1 | +33.1% | 1555.9 | 2089.5 | +34.3% |

#### Qwen3-235B

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 1127.5 | 1117.2 | -0.9% | 1159.9 | 1155.0 | -0.4% |
| 4 | 1133.3 | 1125.4 | -0.7% | 1164.7 | 1164.0 | -0.1% |
| 8 | 1137.5 | 1133.3 | -0.4% | 1166.9 | 1173.7 | +0.6% |
| 16 | 1148.1 | 1153.2 | +0.4% | 1180.5 | 1192.6 | +1.0% |
| 32 | 1164.1 | 1177.4 | +1.2% | 1189.9 | 1213.6 | +2.0% |
| 64 | 1194.3 | 1231.9 | +3.1% | 1220.9 | 1259.1 | +3.1% |
| 128 | 1235.5 | 1338.1 | +8.3% | 1261.7 | 1365.8 | +8.3% |
| 256 | 1329.5 | 1557.9 | +17.2% | 1369.7 | 1590.5 | +16.1% |
| 1024 | 4859.1 | 5462.0 | +12.4% | 5021.2 | 5705.6 | +13.6% |

#### DeepSeek-V3

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 4984.5 | 4969.1 | -0.3% | 5176.4 | 5179.1 | +0.1% |
| 4 | 5001.5 | 4999.3 | -0.0% | 5195.6 | 5219.7 | +0.5% |
| 8 | 5019.1 | 5031.8 | +0.3% | 5210.7 | 5254.8 | +0.8% |
| 16 | 5079.4 | 5119.5 | +0.8% | 5252.0 | 5328.3 | +1.5% |
| 32 | 5128.5 | 5211.5 | +1.6% | 5294.0 | 5413.6 | +2.3% |
| 64 | 5337.5 | 5437.7 | +1.9% | 5386.0 | 5621.7 | +4.4% |
| 128 | 5467.0 | 5788.3 | +5.9% | 5665.0 | 5974.9 | +5.5% |
| 256 | 6817.4 | 7261.4 | +6.5% | 6493.9 | 7089.9 | +9.2% |
| 512 | 13300.1 | 13823.2 | +3.9% | 12227.7 | 13102.6 | +7.2% |

### RTX PRO 5000 Blackwell (SM120a, 110 SM)

#### Qwen3.5-35B

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 455.3 | 465.1 | +2.2% | 471.4 | 477.5 | +1.3% |
| 4 | 468.1 | 475.4 | +1.6% | 483.1 | 492.2 | +1.9% |
| 8 | 475.6 | 481.2 | +1.2% | 496.0 | 499.4 | +0.7% |
| 16 | 486.6 | 488.7 | +0.4% | 503.7 | 507.4 | +0.7% |
| 32 | 497.3 | 503.9 | +1.3% | 512.8 | 521.7 | +1.7% |
| 64 | 525.7 | 549.7 | +4.6% | 540.0 | 577.2 | +6.9% |
| 128 | 573.1 | 633.3 | +10.5% | 600.7 | 652.4 | +8.6% |
| 256 | 706.4 | 862.8 | +22.1% | 714.5 | 873.1 | +22.2% |
| 1024 | 2790.3 | 3457.5 | +23.9% | 2817.7 | 3368.1 | +19.5% |

#### Qwen3-235B

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 1354.6 | 1366.7 | +0.9% | 1420.4 | 1406.5 | -1.0% |
| 4 | 1373.0 | 1377.1 | +0.3% | 1438.3 | 1426.4 | -0.8% |
| 8 | 1380.4 | 1381.6 | +0.1% | 1444.6 | 1436.1 | -0.6% |
| 16 | 1399.2 | 1397.4 | -0.1% | 1454.8 | 1449.8 | -0.3% |
| 32 | 1411.9 | 1410.7 | -0.1% | 1466.3 | 1468.7 | +0.2% |
| 64 | 1462.5 | 1469.2 | +0.5% | 1492.5 | 1544.5 | +3.5% |
| 128 | 1492.8 | 1639.3 | +9.8% | 1548.5 | 1694.6 | +9.4% |
| 256 | 2017.4 | 2323.8 | +15.2% | 2116.8 | 2342.8 | +10.7% |
| 1024 | 8278.5 | 9218.5 | +11.4% | 8306.9 | 9258.2 | +11.5% |

#### DeepSeek-V3

| MPE | fp8 fused (µs) | fp8 unfused (µs) | fp8 Δ | mxfp8 fused (µs) |
mxfp8 unfused (µs) | mxfp8 Δ |
|---|---|---|---|---|---|---|
| 1 | 6241.2 | 6235.1 | -0.1% | 6487.4 | 6451.4 | -0.6% |
| 4 | 6254.4 | 6254.3 | -0.0% | 6499.1 | 6481.9 | -0.3% |
| 8 | 6269.1 | 6290.3 | +0.3% | 6512.7 | 6510.1 | -0.0% |
| 16 | 6337.1 | 6366.4 | +0.5% | 6555.2 | 6596.9 | +0.6% |
| 32 | 6380.8 | 6442.6 | +1.0% | 6597.4 | 6682.0 | +1.3% |
| 64 | 6885.3 | 6726.1 | -2.3% | 6701.6 | 6894.7 | +2.9% |
| 128 | 7021.1 | 7308.6 | +4.1% | 7061.2 | 7408.3 | +4.9% |
| 256 | 10298.8 | 10741.8 | +4.3% | 10245.9 | 10829.9 | +5.7% |
| 512 | 20201.4 | 20958.2 | +3.7% | 19835.6 | 21038.7 | +6.1% |

Fusion is neutral (occasionally slightly negative) at decode — small
MPE, where FC1 grouped GEMM is weight-bandwidth /
per-expert-tile-schedule bound and the `2I` intermediate round-trip is
negligible against the GEMM floor — and grows with token count at
prefill. Peak gain scales inversely with K: **Qwen3.5-35B (K=2048) >
Qwen3-235B (K=4096) > DeepSeek-V3 (K=7168)** (up to +34% / +17% / +9% on
the 6000; +24% / +15% / +6% on the 5000). FP8 and MXFP8 track closely.

## Benchmark 2: cooperative MoE scheduler (new
`sm120_common/moe_scheduler.cuh`)

The ZeroPadding token→tile map was previously resolved by a per-lane
linear scan (base of #3891). This PR replaces it with a warp-cooperative
scan (coalesced 32-group load + `shfl` prefix-sum + `ballot`, isomorphic
to the CUTLASS SM90 group scheduler), selected per `GemmType` —
non-ZeroPadding paths are SASS-unchanged.

Decode-shaped microbenchmark on RTX PRO 6000 Blackwell Server Edition
(M=1 token × topk=8, E=256, GranK=32; `contig` = padding-free upper
bound), 4-arm NCU on one binary:

| scheduler | GEMM1 (N=1024, K=2048) | GEMM2 (N=2048, K=512) |
|---|---|---|
| linear scan (prev, #3891) | 30.70 µs (+109% vs ideal) | 26.44 µs
(+193%) |
| **cooperative (this PR)** | **17.45 µs (+18.9%)** | **10.77 µs
(+19.5%)** |
| **speedup vs linear scan** | **+76%** | **+146%** |

Scheduler global-load traffic drops **7.1×** (963,840 → 136,256 LSU
sectors) and instructions 5×↓ (7.9M → 1.6M), bringing decode scheduler
overhead from ~2–3× the padding-free ideal to within ~20%. At E≤64 both
schedulers are within ~2–3% of ideal; large-M (prefill) and
non-ZeroPadding shapes are unchanged (paired benchmark ≤0.42%, no
regression).

## 🔍 Related Issues

Follow-up to #3562 (MXFP8 MoE GEMM entry) and #3891 (FP8 MoE GEMM entry)
— same in-tree kernel package.

## 🧪 Tests

`tests/grouped_mm/test_cute_sm120_{fp8,mxfp8}.py` — adds gated (SwiGLU)
correctness cells for both dtypes, against a per-expert bf16 GEMM +
reference-SwiGLU baseline (FP8 `calc_diff < 2e-3`, MXFP8 `cos_sim >
0.99`). The `cute::Tensor` qualification in the blockscaling headers
keeps existing non-gated coverage bit-identical.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added optional gated MoE GEMM support for FP8 and MXFP8 workloads via
`is_gated`.
* Enables fused SwiGLU gate+up computation with reduced output width and
stricter shape validation for packed gate/up inputs.
  * Improved SM120 MoE execution/tiling for gated workloads.

* **Bug Fixes**
* Tightened gated-mode dimension and alignment checks (including updated
multiple-of-16 validation).

* **Tests**
* Added gated correctness coverage for FP8 and MXFP8 MoE GEMM, including
relaxed numerical tolerance where needed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [a34a735](https://github.com/flashinfer-ai/flashinfer/commit/a34a735b59642d382a313ea35973e42d3b39a715)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-07-29T07:35:15Z
- **提交信息**: [feat] Add SITU trtllmgen MOE (#4180)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add SiTU activation support for TRTLLM-Gen MoE for MXFP4 × MXFP8 and
NVFP4 × NVFP4




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
* Added SiTU gated activation support for FP4 MoE in routed and
non-routed execution, with configurable per-expert `gemm1_alpha`,
`gemm1_beta`, and `gemm1_clamp_limit`.
* Extended FP4 MoE trace templates with an `activation_type` input to
select SiTU.
* **Bug Fixes**
* Improved activation-type mapping/validation so SiTU uses the correct
gated behavior.
* Made MoE kernel/tile selection dtype-aware (activation + weight) and
corrected per-token scaling eligibility during config generation.
* **Tests**
* Expanded MoE coverage for SiTU and optional per-expert parameters,
including additional routed-logit and autotune regression checks.
* **Chores**
  * Updated the remote BMM artifact reference and checksum.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Siyuan Fu <siyuanf@nvidia.com>
Co-authored-by: Siyuan Fu <siyuanf@nvidia.com>

### [f6c2f1e](https://github.com/flashinfer-ai/flashinfer/commit/f6c2f1e7b0f38d31953a131fed93ccf1d0817e2b)

- **作者**: Jonathan Dierksen
- **时间**: 2026-07-29T07:29:53Z
- **提交信息**: [cli] add CLI helper for flashinfer-jit-cache and flashinfer-cubin wheel installs (#3142)

## Summary
Add CLI commands to install the matching flashinfer-jit-cache and/or
flashinfer-cubin wheels from the FlashInfer wheel index.

Also update documentation to reflect using `--index-url` for
`flashinfer-cubin` instead of installing my pypi.

## What changed
- detect the FlashInfer and CUDA versions and build the matching pip
install command
- document the new command in the CLI docs
- add CLI tests for version/index selection and dry-run behavior
- update docs to use `--index-url` for cubin wheel

## Why
Packages is too large for PyPI, so users need a helper that can resolve
the correct custom index-url and matching package version automatically.

## Validation
- Click dry-run smoke test in verified the generated command resolves to
with
- was not available in the current environment, so the added CLI tests
were not executed here

Closes #3033

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added new CLI commands to install pre-built cubin and JIT-cache
wheels.
- Added `download-kernels` to install both kernel artifact sets
together.
- Improved CUDA-version handling with auto-detection, compatibility
mapping, nightly installs, and `--dry-run`.
  - Added a hidden `download-jit-cache` alias for convenience.

- **Documentation**
- Updated README quickstart and artifact management CLI docs to use the
new `flashinfer` subcommands.
- Clarified what cubin downloads include and documented new
install/download command behavior.

- **Tests**
- Added/expanded mocked CLI tests covering exact install invocations,
dry-run behavior, CUDA fallback/validation, aliases, and failure
handling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: dierksen <dierksen@dierksen-spark.localdomain>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3894
- **最后更新**: 2026-07-29T09:26:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34186
- **最后更新**: 2026-07-29T20:43:21Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: David El Malih, Steven Liu, Akshan Krithick

## AI分析总结

以下是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结：

---

### 1. 主要更新类型
- **文档更新**（3 个提交）：贡献指南、方法文档字符串、基准测试移除。
- **Bug 修复**（1 个提交）：修复 LoRA 热切换时的编译重编译错误。
- **重构**（1 个提交）：调整 QwenImage img2img pipeline 测试结构。

---

### 2. 关键变更点及其与项目整体方向的关系
- **`[docs] update agentic contribution guidelines`**  
  更新贡献指南，强调“自主贡献”（agentic）规范。这与 HuggingFace 鼓励社区协作、降低贡献门槛的目标一致，尤其对大型开源项目而言，清晰的指南能提升 PR 质量。

- **`[docs] improve docstring scheduling_ddpm_wuerstchen.py`**  
  改进特定调度器（Wuerstchen 扩散模型的 DDPM）的文档字符串。项目作为扩散模型工具库，准确的方法文档是用户正确使用 API 的基础，有助于减少使用疑惑。

- **`[docs] remove image generation benchmarks`**  
  移除图像生成基准测试。可能是因为基准测试维护成本高、结果已过时，或项目转向更先进的评估方式。此举使文档更精简，聚焦于核心功能。

- **`[refactor] refactor qwenimage img2img pipeline tests to the new mixin structure`**  
  将 QwenImage 模型的图像到图像 pipeline 测试重构为统一的 mixin 结构。这是持续推动测试基础设施标准化的一步，便于后续模型统一测试，提升维护效率。

- **`[fix] Fix LoRA hot-swapping recompilation with different_shapes_for_compilation`**  
  修复了在启用 `different_shapes_for_compilation` 时，LoRA 热切换导致的 `RecompileError`。原因是鸭子形状（duck shape）假设导致张量维度被错误特化，通过将 `use_duck_shape = False` 移至通用 `_check_model_hotswap` 方法解决，并去除了之前掩盖问题的 `xfail` 标记。

---

### 3. 对项目的影响和潜在意义
- **文档更新**提高了项目可访问性和贡献效率，尤其 agentic 指南可能包括自动化工作流或协作模板。
- **测试重构**增强了测试代码的可复用性和可维护性，降低未来添加新模型时的测试编写成本。
- **LoRA 热切换修复**直接影响了**模型部署与推理优化**场景：LoRA 热切换允许在不重启模型时动态切换适配器，是生产环境中的重要特性。修复后，用户可以在不同输入形状下正常工作，避免因编译错误导致服务中断。

---

### 4. 值得关注的技术点
- **鸭子形状（duck shape）与即时编译（JIT）**：提交中提到的 `use_duck_shape` 是 PyTorch/torchdynamo 编译策略中的一个选项，用于处理动态形状。该 bug 揭示了在 LoRA 模块中，输入张量的序列长度（`height * width`）与通道数意外相同（均为 16），导致编译器错误将二者绑定为同一符号。
- **测试结构 mixin 化**：HuggingFace diffusers 正逐步将测试从重复的独立代码迁移至基于 mixin 的共享结构，这是一种常见的测试重构模式，可显著减少代码量并提升覆盖率一致性。
- **LoRA 热切换与编译模型的兼容性**：该修复确保了热切换 API 与 `different_shapes_for_compilation` 选项的协同，这在使用多样输入尺寸（如不同分辨率图像）的生产场景中至关重要。

---

### 5. 基于项目背景（扩散模型工具库）对项目发展的影响
- **稳定性提升**：修复 LoRA 热切换编译 bug 直接增强了库在生产环境中的可靠性，特别是对于需要动态切换适配器（如多风格生成、个性化模型）的应用。
- **文档与测试现代化**：清理过时文档（移除基准测试）并强化测试基础设施（mixin 化），表明项目正从快速迭代期进入**成熟维护与标准化阶段**，这有助于吸引更多企业用户。
- **社区协作优化**：贡献指南的更新可能引入更自动化的流程（如 AI 辅助代码审查），进一步降低贡献门槛，符合 HuggingFace 构建开放模型生态系统的一贯策略。

## 详细提交记录

### [9e969b6](https://github.com/huggingface/diffusers/commit/9e969b6cf0588fd75fbacee9a39d16a3f5c56fc4)

- **作者**: Steven Liu
- **时间**: 2026-07-29T20:43:07Z
- **提交信息**: [docs] update agentic contribution guidelines (#14312)

* docs

* feedback

### [904183c](https://github.com/huggingface/diffusers/commit/904183cd8b6116f79b92268507695f910444daf0)

- **作者**: David El Malih
- **时间**: 2026-07-29T15:33:59Z
- **提交信息**: docs: improve docstring scheduling_ddpm_wuerstchen.py (#14319)

Improve docstring scheduling ddpm wuerstchen

### [05dde2f](https://github.com/huggingface/diffusers/commit/05dde2f2006fbae413f0e38c69146428a832d7ec)

- **作者**: Steven Liu
- **时间**: 2026-07-29T15:00:24Z
- **提交信息**: [docs] remove image generation benchmarks (#14310)

* remove

* remove

### [1456cca](https://github.com/huggingface/diffusers/commit/1456cca53416df8b0fdc158edf071978ee773178)

- **作者**: Akshan Krithick
- **时间**: 2026-07-29T12:48:31Z
- **提交信息**: refactor qwenimage img2img pipeline tests to the new mixin structure (#14320)

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [52110fb](https://github.com/huggingface/diffusers/commit/52110fbbf68a6f18ce4f342cb91947b68df960df)

- **作者**: jiqing-feng
- **时间**: 2026-07-29T09:46:41Z
- **提交信息**: Fix LoRA hot-swapping recompilation with `different_shapes_for_compilation` (#14297)

[tests] fix hot-swapping recompilation with different_shapes_for_compilation

`test_hotswapping_compiled_model_linear` and
`test_hotswapping_compiled_model_both_linear_and_other` failed for every model
setting `different_shapes_for_compilation`, e.g.:

    RecompileError: tensor 'hidden_states' size mismatch at index 1.
    expected 16, actual 32

The dummy inputs are `(batch, height * width, channels)` with `channels = 16`
and the first traced shape is `(4, 4)`, so the image sequence length equals the
channel count. Duck shaping assigns both dims the same symbol, which `img_in`
(an `nn.Linear` with constant `in_features`) then specializes to 16, forcing a
recompile on the next shape.

`use_duck_shape = False` was already set in `test_compile_on_different_shapes`
and `test_hotswapping_compile_on_different_shapes` (#11327) but the other two
multi-shape hot-swapping tests were missed. Move it into
`_check_model_hotswap` so all of them are covered, and drop the now-redundant
duplicate.

Also drop the two `xfail(strict=True)` markers on
`TestQwenImageTransformerLoRAHotSwap` that were masking this bug.

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 427
- **最后更新**: 2026-07-28T14:17:53Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12777
- **最后更新**: 2026-07-29T15:38:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30930
- **最后更新**: 2026-07-29T22:04:16Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 33
- **主要提交者**: Nicolas Castet, Liangsheng Yin, pllimax

## AI分析总结

分析生成失败

## 详细提交记录

### [3c1717d](https://github.com/sgl-project/sglang/commit/3c1717d9b6355e48855be7cc079db3ef9958f36d)

- **作者**: cctry
- **时间**: 2026-07-29T22:03:59Z
- **提交信息**: Follow up on #30157 post-merge review (#32672)

### [8fc54d4](https://github.com/sgl-project/sglang/commit/8fc54d46eff5fe7a44274cf3c40ad00bcd2719e9)

- **作者**: Sam (Kesen Li)
- **时间**: 2026-07-29T21:58:55Z
- **提交信息**: Fix MoE reduce-scatterv eligibility check (#32663)

### [d24de56](https://github.com/sgl-project/sglang/commit/d24de56995733c6b19ef2448d8b5be10f6d58b1f)

- **作者**: Rain Jiang
- **时间**: 2026-07-29T21:55:06Z
- **提交信息**: sglang rust server sampling message (#32343)

### [ffd4705](https://github.com/sgl-project/sglang/commit/ffd4705baa39117cad64c6b7304249e10d773c17)

- **作者**: Willow Lopez
- **时间**: 2026-07-29T21:02:19Z
- **提交信息**: fix(reasoning): honor Poolside template thinking defaults (#32540)

Co-authored-by: Jiminator <69131491+Jiminator@users.noreply.github.com>

### [d0e69d3](https://github.com/sgl-project/sglang/commit/d0e69d3881453a8c4eb7ac1847232f41e69d3509)

- **作者**: Sam Shleifer
- **时间**: 2026-07-29T19:15:56Z
- **提交信息**: [feat] Optional base64 encoding for the flat prompt top logprob arrays (#31960)

### [e4f7f7b](https://github.com/sgl-project/sglang/commit/e4f7f7b3807b9e8bfb188954b9301fc46bdfc6a1)

- **作者**: ICENacl
- **时间**: 2026-07-29T19:01:09Z
- **提交信息**: fix(qwen3.5): restrict MoE weights to local PP layers (#32022)

Co-authored-by: chunjiang.hc <chunjiang.hc@alibaba-inc.com>
Co-authored-by: Yihao Wang <42559837+AgainstEntropy@users.noreply.github.com>

### [f73d6f2](https://github.com/sgl-project/sglang/commit/f73d6f278909e5f126888ca618667ba583efc8a2)

- **作者**: Ke Bao
- **时间**: 2026-07-29T18:23:23Z
- **提交信息**: Update Inkling cookbook install command (#32799)

### [2ca2ca7](https://github.com/sgl-project/sglang/commit/2ca2ca753a1bc7bd79707108f84b0479501b2e5e)

- **作者**: Rain Jiang
- **时间**: 2026-07-29T17:54:56Z
- **提交信息**: sglang rust server request message (#32242)

### [eefb434](https://github.com/sgl-project/sglang/commit/eefb434d17bc62ef984a4cd96c4235d47455e9c3)

- **作者**: ziang663
- **时间**: 2026-07-29T17:19:17Z
- **提交信息**: [PD+PP] Honor PP consensus for bootstrap and prealloc (#31869)

Co-authored-by: Chao Shi <chao.shi@alibaba-inc.com>

### [62d0f81](https://github.com/sgl-project/sglang/commit/62d0f81f16090fdc551adcc102340af5774ddc40)

- **作者**: Yoray Zack
- **时间**: 2026-07-29T17:06:56Z
- **提交信息**: [2/N] elastic-ep: Enable EPLB after scale-up (#30553)

### [d19999b](https://github.com/sgl-project/sglang/commit/d19999b75566885f72b29ab252bf064321809dc3)

- **作者**: Piotr Mazurek
- **时间**: 2026-07-29T17:02:14Z
- **提交信息**: [LFM2] Wire Lfm2MoeForCausalLM into the LFM2 serving override tables (#30780)

### [f69af7b](https://github.com/sgl-project/sglang/commit/f69af7b7ad62f055867732196c13f0dd742097d2)

- **作者**: Hert4
- **时间**: 2026-07-29T16:55:33Z
- **提交信息**: [Bugfix] compressed-tensors: mixed-precision checkpoints silently load unquantized (#32736)

Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [fddfc1f](https://github.com/sgl-project/sglang/commit/fddfc1fb5ef58fdb746616103aea01ea482370a6)

- **作者**: YAMY
- **时间**: 2026-07-29T16:47:35Z
- **提交信息**: [GDN] Support FlashInfer GDN prefill with extra-buffer radix cache (#29735)

### [50029f0](https://github.com/sgl-project/sglang/commit/50029f05a3b30ff59c01637d70746245c457744a)

- **作者**: huangtingwei
- **时间**: 2026-07-29T15:48:48Z
- **提交信息**: [HiCache] Merge HiCache event checks to reduce decode overhead (#30511)

Co-authored-by: alphabetc1 <47200617+alphabetc1@users.noreply.github.com>

### [bfc4502](https://github.com/sgl-project/sglang/commit/bfc450248efe06af2853464d390021d6d8bbf4ce)

- **作者**: Bingxu Chen
- **时间**: 2026-07-29T15:18:07Z
- **提交信息**: [AMD] Replace MI325 with MI300 CI Runners (#31409)

### [e1f2f9d](https://github.com/sgl-project/sglang/commit/e1f2f9d1fa84cd1b8d9020377fdd707b3a485687)

- **作者**: Nicolas Castet
- **时间**: 2026-07-29T14:39:36Z
- **提交信息**: Disable extra NCCL CUDA event synchronization with symm mem (#27089)

### [3763d3f](https://github.com/sgl-project/sglang/commit/3763d3fa8c359a6f95e6597c45d1a53141c2237d)

- **作者**: Ke Bao
- **时间**: 2026-07-29T14:38:34Z
- **提交信息**: Add decode-lock skip to compute-mamba-ratio (#32789)

### [1c6a0e9](https://github.com/sgl-project/sglang/commit/1c6a0e91e1257619dc5d5c0693e7f937b4be3227)

- **作者**: Wu Jiangming
- **时间**: 2026-07-29T14:36:48Z
- **提交信息**: fix mqa preshuffle layout issue for deepseek v4 (#31563)

### [22151ed](https://github.com/sgl-project/sglang/commit/22151edca162da06d913478c96bd8e3db84f4380)

- **作者**: Mick
- **时间**: 2026-07-29T14:04:20Z
- **提交信息**: [diffusion] optimization: accelerate CUDA video output finalization (#32784)

### [0ebbe43](https://github.com/sgl-project/sglang/commit/0ebbe43dbb9b6e916dd1e46ac03499fdae900094)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-29T13:58:41Z
- **提交信息**: fix(diffusion): size VSA top-k from padded blocks (#32695)

### [4f5b50c](https://github.com/sgl-project/sglang/commit/4f5b50c576e8118614174d5762c6818709227f58)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-29T13:57:50Z
- **提交信息**: perf(diffusion): decode Wan VAE in BF16 (#32697)

### [917e900](https://github.com/sgl-project/sglang/commit/917e900d4d53da6b35f67e0dd0c494ac8107c65a)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-29T13:57:05Z
- **提交信息**: feat(diffusion): add regional torch compile (#32696)

### [50b0292](https://github.com/sgl-project/sglang/commit/50b029257fb819b4673efb441cfdd048392571aa)

- **作者**: Ke Bao
- **时间**: 2026-07-29T13:53:28Z
- **提交信息**: Skip mamba lock during decoding (#32228)

### [d004a15](https://github.com/sgl-project/sglang/commit/d004a15a3edf6f772b9552007d584d0c031495af)

- **作者**: pllimax
- **时间**: 2026-07-29T13:44:17Z
- **提交信息**: Fix GLM4-7B-Flash accuracy test configuration, tune Qwen3.6-27B/35B performance test parameters, and harden Ascend NPU multi-node E2E test utilities against pod name format errors. (#32371)

### [977f04a](https://github.com/sgl-project/sglang/commit/977f04aafecac1e474751d009ceed61826ef2266)

- **作者**: Ilia Yastrebov
- **时间**: 2026-07-29T13:02:13Z
- **提交信息**: [PD] NIXL connector: shard by destination (#32025)

### [67c2258](https://github.com/sgl-project/sglang/commit/67c2258906d1898391cdcdfe871c94a79e4a6580)

- **作者**: Mick
- **时间**: 2026-07-29T12:44:13Z
- **提交信息**: [diffusion] fix: fix dual-DiT models crash with (1,)-placeholder weights after compile-time offload (#32743)

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [ca6e0ff](https://github.com/sgl-project/sglang/commit/ca6e0ff2c8fbff7060a2f63009539aa8067922bc)

- **作者**: JiaruiChang5268
- **时间**: 2026-07-29T12:13:31Z
- **提交信息**: [NPU] fix dsv4 mtp condition on NPU graph (#32711)

### [d254ec9](https://github.com/sgl-project/sglang/commit/d254ec9ff816d16918b13b3fbe2f967d54ec29b5)

- **作者**: Yi (Vincent) Zhong
- **时间**: 2026-07-29T11:58:47Z
- **提交信息**: Add LFM2.5 embedding model support (#28691)

### [4c82bb3](https://github.com/sgl-project/sglang/commit/4c82bb3252c65288f12f09ce5d0dce68ea910e54)

- **作者**: LZW
- **时间**: 2026-07-29T10:17:41Z
- **提交信息**: Add Mooncake tenant id support (#30256)

### [8742a1a](https://github.com/sgl-project/sglang/commit/8742a1a0f8e867cb84cf3b8d8c6afbc92c8a52f4)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-29T10:17:08Z
- **提交信息**: Add a benchmark script for the HPC-Ops bf16xfp32 router GEMM (#32642)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [c151080](https://github.com/sgl-project/sglang/commit/c151080d287436ad016f934545ddfccaeb677b5d)

- **作者**: Ke Bao
- **时间**: 2026-07-29T10:15:48Z
- **提交信息**: Add compute-mamba-ratio skill (#32763)

### [d12ea3e](https://github.com/sgl-project/sglang/commit/d12ea3e9ba9f8d76cd5fc1e9ce9b71681e2f3a2e)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-29T10:02:28Z
- **提交信息**: docker: add Kimi K3 images (#32760)

### [983e4aa](https://github.com/sgl-project/sglang/commit/983e4aa18d7e8746d3ef357ad9f8c8d757a3de5b)

- **作者**: hunhokim
- **时间**: 2026-07-29T09:58:48Z
- **提交信息**: Eliminate redundant DSA state transfers (Mooncake) (#32620)

Co-authored-by: Hun-ho Kim <hunho.kim@samsung.com>

### [f5bcd00](https://github.com/sgl-project/sglang/commit/f5bcd00e16384cab7f91039333cf79bc2dfcdbdc)

- **作者**: Xinyu Jiang
- **时间**: 2026-07-29T09:41:08Z
- **提交信息**: [AMD] DSv4: bring HIP compress-state pool into the memory_saver KV_CACHE region (#31747)

Co-authored-by: Zhiyao Jiang <jessicajiang324@gmail.com>

### [c32c4ef](https://github.com/sgl-project/sglang/commit/c32c4ef79cf5218c24f467aad7f3ff392a62bed7)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-29T09:25:00Z
- **提交信息**: [Kernel] Move sgl-kernel under sglang.kernels.aot (#32648)

### [1b9dfa1](https://github.com/sgl-project/sglang/commit/1b9dfa14e66b617ed53270164549d59290b1f7c8)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-29T09:12:18Z
- **提交信息**: Fix FlashInfer MNNVL workspace size check (#32318)

### [9ab8838](https://github.com/sgl-project/sglang/commit/9ab88380c170079cb94f65c855520cfcc83f555e)

- **作者**: Junlin Wu
- **时间**: 2026-07-29T09:10:01Z
- **提交信息**: :busts_in_silhouette: chore(codeowners): Update codeowners for NPU quantization (#31917)

### [227dadd](https://github.com/sgl-project/sglang/commit/227dadd79a17dc16c2a5e0c33ad7ea68f1e7093f)

- **作者**: Yihao Wang
- **时间**: 2026-07-29T08:52:55Z
- **提交信息**: [diffusion] feat: support resident layers for DiT (#31538)

### [0caf0fc](https://github.com/sgl-project/sglang/commit/0caf0fc01dc9fdc0e96732815f7cc644cbc1e2de)

- **作者**: Andrew Kuksa
- **时间**: 2026-07-29T08:50:15Z
- **提交信息**: [Diffusion][Docs] Ascend A2, A3 add basic usage and benchmark results in diffusion cookbook (#30614)

Co-authored-by: ANDREW_K <andrewsha3@DESKTOP-KNDINTT.localdomain>

### [7dcebca](https://github.com/sgl-project/sglang/commit/7dcebca255991e0e357116003e249da6dbfc888b)

- **作者**: Brayden Zhong
- **时间**: 2026-07-29T08:39:55Z
- **提交信息**: Fix nightly CI: NVFP4 cuda-graph crash, NVILA batching, CuTe paged-KV zero-size, Kimi-VL OOM (#32118)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [cce5873](https://github.com/sgl-project/sglang/commit/cce5873513fe4a9059cd0f0bab416e1c64db4c31)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-29T07:45:01Z
- **提交信息**: [CI] Fail lint when a registered file's TestCase classes never run (#32735)

### [f05c92f](https://github.com/sgl-project/sglang/commit/f05c92fb6d6599c108b1dd40571e2b1dc5b65f0a)

- **作者**: Junlin Wu
- **时间**: 2026-07-29T07:39:36Z
- **提交信息**: :sparkles: [llm][npu][quant] Add W8A8 MXFP8 quantization for Qwen3 MoE on Ascend NPU (#30768)

Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [da5528d](https://github.com/sgl-project/sglang/commit/da5528db3079170d1b3306e48373309536740930)

- **作者**: Mick
- **时间**: 2026-07-29T07:25:04Z
- **提交信息**: fix(vlm): materialize Qwen3-VL features on the vision device (#31596)

### [bd47ec9](https://github.com/sgl-project/sglang/commit/bd47ec97ff7a2881f9bb0316a4a657000a50c020)

- **作者**: weireweire
- **时间**: 2026-07-29T07:07:42Z
- **提交信息**: [EAGLE] Handle NaNs in fused top-k=1 (#32396)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1239
- **最后更新**: 2026-07-25T07:09:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87597
- **最后更新**: 2026-07-29T22:04:14Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 28
- **主要提交者**: Chanh Nguyen, Tianmu Li, Brandon Pelfrey

## AI分析总结

分析生成失败

## 详细提交记录

### [fa2a258](https://github.com/vllm-project/vllm/commit/fa2a2589bd2a1fce0851df7fd42ffb54b6195f04)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-29T22:02:12Z
- **提交信息**: [CI][ROCm] Fix AMD nightly distributed regressions (#50304)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [435c4da](https://github.com/vllm-project/vllm/commit/435c4dad97f90d7f1f72523be9d03dab2663bcd0)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-29T21:30:29Z
- **提交信息**: [ROCm][CI] Avoid Ray worker startup env race (#50311)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [5fa0154](https://github.com/vllm-project/vllm/commit/5fa01544480b60275edf913e1a620d229e40553d)

- **作者**: zaristei
- **时间**: 2026-07-29T20:53:25Z
- **提交信息**: [Rubin] Enable NVLink all-reduce paths on SM107 (#49647)

Signed-off-by: Zachary Aristei <zaristei@nvidia.com>
Co-authored-by: Sahithi Chigurupati <chigurupati.sahithi@gmail.com>
Co-authored-by: hlu1 <14827759+hlu1@users.noreply.github.com>

### [48fc2e2](https://github.com/vllm-project/vllm/commit/48fc2e2797ec3f35605c3ff399bbaab7938b0459)

- **作者**: Connor Carpenter
- **时间**: 2026-07-29T20:46:40Z
- **提交信息**: feat(grpc): add KV event source discovery (#50033)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [2ecd864](https://github.com/vllm-project/vllm/commit/2ecd8645d87e7c0716e5bc4347620e91e137619d)

- **作者**: Nick Hill
- **时间**: 2026-07-29T20:46:07Z
- **提交信息**: Revert "[Misc][Minimax-M3]add default video_processor (#50092)" (#50313)

### [82642d7](https://github.com/vllm-project/vllm/commit/82642d7d6c332fefdec06b260a246bd1a4ebf5ff)

- **作者**: Wentao Ye
- **时间**: 2026-07-29T20:45:38Z
- **提交信息**: [Perf] RMSNorm uncontiguous support, 1.2~3.1x kernel performance improvement (#49750)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Signed-off-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [9347745](https://github.com/vllm-project/vllm/commit/93477454f9155d4f74352e3d725c83f91c6894bf)

- **作者**: roikoren755
- **时间**: 2026-07-29T18:27:31Z
- **提交信息**: [torch.compile] Compile `CustomOp.forward_native` for ReLU^2 to avoid raw torch ops inside opaque custom ops (#50244)

Signed-off-by: Roi Koren <roik@nvidia.com>

### [5c7a7f9](https://github.com/vllm-project/vllm/commit/5c7a7f9462c97ff8b2f63e6458488b820f2bbd86)

- **作者**: Brandon Pelfrey
- **时间**: 2026-07-29T17:23:04Z
- **提交信息**: [docs] Add documentation for pynvvideocodec video decoding backend (#49066)

Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [f98061c](https://github.com/vllm-project/vllm/commit/f98061ce6cb0326978363fb6c0489fe75a9aac5d)

- **作者**: Chanh Nguyen
- **时间**: 2026-07-29T16:58:29Z
- **提交信息**: fix(step3p5-mtp): honor exclude_modules for the MTP head via prefix (#48883)

Signed-off-by: Chan Nguyen <channguyen@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [8255369](https://github.com/vllm-project/vllm/commit/82553692b899059d2ec967ece7677a76bf2daab2)

- **作者**: Nick Hill
- **时间**: 2026-07-29T16:45:53Z
- **提交信息**: [KV Connector] Fix NIXL mamba state pairing for multi-slot block tables (#50153)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [381b691](https://github.com/vllm-project/vllm/commit/381b6916202035f997467324a6b1495ab84d98a6)

- **作者**: stefankoncarevic
- **时间**: 2026-07-29T15:47:50Z
- **提交信息**: [ROCm][CI] Fix Kimi K3 KDA on ROCm (#50262)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [d6247d7](https://github.com/vllm-project/vllm/commit/d6247d71731249c65c829b4cbfb782b647849e4e)

- **作者**: Michael Goin
- **时间**: 2026-07-29T15:43:51Z
- **提交信息**: [Spec Decode][Perf] Replicate DSpark Markov head across TP ranks (#49731)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [a0c092e](https://github.com/vllm-project/vllm/commit/a0c092ee72c0dcefbb3b3e74f97ac62d842e5f4b)

- **作者**: Nick Hill
- **时间**: 2026-07-29T13:41:54Z
- **提交信息**: [BugFix] Fix `num_output_placeholders` preemption underflow (#48245)

Signed-off-by: Chris Eastwood <chris.eastwood@pwn4g3.dev>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Chris Eastwood <chris.eastwood@pwn4g3.dev>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>

### [43eaefb](https://github.com/vllm-project/vllm/commit/43eaefba5a5dbccb71d2404e4bf28e21bb74fce6)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-29T13:30:45Z
- **提交信息**: [ModelRunner V2] Enable sequence pooling for embedding and classification models (#48791)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [e0cfa52](https://github.com/vllm-project/vllm/commit/e0cfa52d22a00f755a53bbed925b0c92d4290f39)

- **作者**: christian
- **时间**: 2026-07-29T13:16:13Z
- **提交信息**: [Bugfix][Frontend] Return transcription and translation verbose as float (#49073)

Signed-off-by: Lucas Christian <lucaschgf7@gmail.com>

### [242c591](https://github.com/vllm-project/vllm/commit/242c591d5a38be6c80ff5197e83e4fa34c5f74b5)

- **作者**: Reid
- **时间**: 2026-07-29T12:21:09Z
- **提交信息**: [Rust Frontend] Send multimodal tensors in auxiliary frames (#49341)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [625871b](https://github.com/vllm-project/vllm/commit/625871b52c487077658582f72a0abbda559383e8)

- **作者**: stefankoncarevic
- **时间**: 2026-07-29T12:15:56Z
- **提交信息**: [CI][Test] Fix pooling truncation test after VLLMError hierarchy change (#50241)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>

### [72297d8](https://github.com/vllm-project/vllm/commit/72297d859ba34e019da4d7e5de58abbbd59961d4)

- **作者**: Yintong Lu
- **时间**: 2026-07-29T10:59:58Z
- **提交信息**: [XPU] Route weightless RMSNorm to _C dispatch (#47121)

Signed-off-by: Yintong Lu <yintong.lu@intel.com>
Co-authored-by: Yongqi Wang <yongqi.wang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [f51193b](https://github.com/vllm-project/vllm/commit/f51193b9aefe665904d793ca782002320224d27a)

- **作者**: sungsoo ha
- **时间**: 2026-07-29T10:54:52Z
- **提交信息**: [Kernel][Mamba] Fused-kernel support for align-mode DS-conv state migration with num_accepted_tokens > 1 (#49291)

Signed-off-by: Sungsoo Ha <sungsooh@nvidia.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [aeaa50a](https://github.com/vllm-project/vllm/commit/aeaa50a71c4f53a8b38ae043ab5914fed2504d4a)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-07-29T10:48:40Z
- **提交信息**: [Bugfix][Multimodal] Include media IO config in MM cache hash (#49975)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [542a8fa](https://github.com/vllm-project/vllm/commit/542a8fad6da059a0fd4a8b0a03b4476e9ec9b66a)

- **作者**: Chang Guo
- **时间**: 2026-07-29T10:05:50Z
- **提交信息**: [KV Offload] Move CPUOffloadingSpec onto SharedOffloadRegion (#50094)

Signed-off-by: Change72 <changg@nvidia.com>
Co-authored-by: Cursor Agent <cursor-agent@cursor.com>

### [9a4e5f9](https://github.com/vllm-project/vllm/commit/9a4e5f95390fc759ada001444637fe2e96a29ad9)

- **作者**: Minh Vu
- **时间**: 2026-07-29T09:52:42Z
- **提交信息**: [CI/Perf] Fix malformed serving benchmark config (#43538)

Signed-off-by: Minh Vu <vuhoangminh97@gmail.com>

### [c44e191](https://github.com/vllm-project/vllm/commit/c44e191b014db0619bd51921e94c86b901ab952e)

- **作者**: Maria Guevara
- **时间**: 2026-07-29T09:21:41Z
- **提交信息**: [Rust Frontend] Add --limit-mm-per-prompt support (#49604)

Signed-off-by: Maria Guevara <kawaiiplush14@gmail.com>

### [5b14019](https://github.com/vllm-project/vllm/commit/5b14019576475224d86044b262e28a04a85d4086)

- **作者**: fxmarty-amd
- **时间**: 2026-07-29T09:17:11Z
- **提交信息**: [CI] Fix MXFP8 MOE backend selection tests on gfx942 (#50222)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [dad7a63](https://github.com/vllm-project/vllm/commit/dad7a6383b7d86709cea420d9594f48b9b42cf69)

- **作者**: omerpaz95
- **时间**: 2026-07-29T09:04:22Z
- **提交信息**: [EC Connector] Add has_pending_push_work  (#49582)

Signed-off-by: omerpaz95 <omerpaz95@gmail.com>

### [5b29c95](https://github.com/vllm-project/vllm/commit/5b29c958c713d367c7caf9313529d4fb2dd6b762)

- **作者**: Yan Ma
- **时间**: 2026-07-29T08:24:56Z
- **提交信息**: [XPU] upgrade to torch 2.13 (#48677)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [df2735e](https://github.com/vllm-project/vllm/commit/df2735ea2e14b377ce71571ed27a63b9ceae2ba3)

- **作者**: rongfu.leng
- **时间**: 2026-07-29T08:24:51Z
- **提交信息**: [Misc][Minimax-M3]add default video_processor (#50092)

Signed-off-by: rongfu.leng <lenronfu@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [32e657e](https://github.com/vllm-project/vllm/commit/32e657e6894a8709d60f8edeffb5a2b1b1cb59a3)

- **作者**: Jared Wen
- **时间**: 2026-07-29T08:24:47Z
- **提交信息**: [BugFix] eagle draft max position embeddings (#49343)

Signed-off-by: JaredforReal <w13431838023@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [ad5d29d](https://github.com/vllm-project/vllm/commit/ad5d29db702ce5bce78d9d3b2da1a76eab72e9c2)

- **作者**: Perkz Zheng
- **时间**: 2026-07-29T08:21:57Z
- **提交信息**: [Model] Support Qwen3.5 text-only dense and MoE models (#50210)

Signed-off-by: Perkz Zheng <PerkzZheng@users.noreply.github.com>
Co-authored-by: Perkz Zheng <PerkzZheng@users.noreply.github.com>

### [f5a7cce](https://github.com/vllm-project/vllm/commit/f5a7cce9b6a61f4d995629a7418c7ea822e34a64)

- **作者**: Bugen Zhao
- **时间**: 2026-07-29T08:06:01Z
- **提交信息**: [Model] Add Kimi K3 support: Python frontend [2/2] (#50093)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [6370e53](https://github.com/vllm-project/vllm/commit/6370e53f246c97649615ccd7fca5366ee73f54aa)

- **作者**: Seiji Eicher
- **时间**: 2026-07-29T08:02:57Z
- **提交信息**: [Frontend] Reuse prefill token ids on the decode chat path for disaggregated serving (#48145)

Signed-off-by: Seiji Eicher <seiji@anyscale.com>

### [65a1a16](https://github.com/vllm-project/vllm/commit/65a1a16594995bdc8b8feae2bf2ecf208d585be8)

- **作者**: Tianmu Li
- **时间**: 2026-07-29T07:34:37Z
- **提交信息**: [CPU] Fix FP8 attention scratchpad sizing (#50194)

Signed-off-by: Li, Tianmu <tianmu.li@intel.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-30
**监控日期**: 2026-07-29
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5736
- **最后更新**: 2026-07-29T21:23:47Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: Mu GuanLin, zzh, Weiming Liao

## AI分析总结

### 1. 主要更新类型
- **功能新增（Feat）**：3项（LTX CFG并行化扩展、扩散模型异步输出、HunyuanImage VAE参数支持）
- **Bug修复（Bugfix）**：1项（HunyuanVideo I2V输入重复获取）
- **文档更新（Doc）**：1项（NPU版本引用修正）
- **重构（Refactor）+ CI改进**：1项（测试树重组、e2e移动到周级）
- **兼容性更新**：1项（Python 3.10兼容）

### 2. 关键变更点与项目方向的关系
- **LTX CFG并行化扩展** → 提升引导计划（guidance plan）的并行效率，直接服务于“fast”目标。
- **扩散图像模型异步输出** → 减少推理等待时间，优化吞吐量，符合“fast and cheap”理念。
- **HunyuanVideo I2V避免重新获取输入** → 降低冗余计算，提升视频模型服务效率。
- **VAE分块并行与tiling参数** → 增加HunyuanImage大模型的高效处理能力，响应“omni-modality”中对图像模型的支持。
- **Python 3.10兼容** → 降低运行门槛，扩大用户群体，体现“easy”易用性。
- **测试重构** → 改善CI可靠性与开发迭代速度，间接支持项目长期稳定发展。
-

## 详细提交记录

### [1b718f7](https://github.com/vllm-project/vllm-omni/commit/1b718f7b1529bf7b59450de2dba0f820ef676dc8)

- **作者**: Mu GuanLin
- **时间**: 2026-07-29T17:40:40Z
- **提交信息**: [Feat] [CI] [bugfix] Generalize LTX CFG parallelism to the complete guidance plan (#5547)

Signed-off-by: mglyn <1203789601@qq.com>

### [dba05c3](https://github.com/vllm-project/vllm-omni/commit/dba05c3517e77b1d3ec85a484ef5286834f8a600)

- **作者**: zzh
- **时间**: 2026-07-29T17:21:55Z
- **提交信息**: Enable Diffusion Image models asynchronous output  (#4981)

Signed-off-by: zzh <943967662@qq.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [f2d9eb1](https://github.com/vllm-project/vllm-omni/commit/f2d9eb163023ab55a7f4cf6e49b024b4f764edf1)

- **作者**: whisper
- **时间**: 2026-07-29T16:49:07Z
- **提交信息**: [Bugfix][CI/Build] Avoid refetching HunyuanVideo I2V input during sim… (#5552)

Signed-off-by: whisper-la <131673492+whisper-la@users.noreply.github.com>

### [fa0658e](https://github.com/vllm-project/vllm-omni/commit/fa0658eabb06baea5e278ef5407e84605c3e03f4)

- **作者**: Weiming Liao
- **时间**: 2026-07-29T15:53:20Z
- **提交信息**: [Doc][NPU] Fix a missed version reference: 0.25.0 → v0.26.0 (#5538)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [7c17111](https://github.com/vllm-project/vllm-omni/commit/7c17111ff54f93d054cbcb95edd66a7d54e89807)

- **作者**: wangyu
- **时间**: 2026-07-29T15:53:03Z
- **提交信息**: [Refactor][CI] Reorganize test tree, and move slow e2e to weekly (#4951)

Signed-off-by: wangyu <410167048@qq.com>

### [9253473](https://github.com/vllm-project/vllm-omni/commit/925347332f8190d172dfa8ac0c307a5cfa2320cb)

- **作者**: zzh
- **时间**: 2026-07-29T09:43:45Z
- **提交信息**: Add vae-patch-parallel-size and vae-use-tiling for HunyuanImage Benchmark (#5502)

Signed-off-by: zzh <943967662@qq.com>

### [7be7e0d](https://github.com/vllm-project/vllm-omni/commit/7be7e0d249134cc121da7ed3945abd3d2473f14d)

- **作者**: R0CKSTAR
- **时间**: 2026-07-29T09:11:04Z
- **提交信息**: Support Python 3.10 runtime compatibility (#5366)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

---
