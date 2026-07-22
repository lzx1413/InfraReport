# GitHub Stars 合并报告 - 2026-07-21

**合并日期**: 2026-07-22
**监控日期**: 2026-07-21
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


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2102
- **最后更新**: 2026-07-22T11:24:14Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: zangyu

## AI分析总结

根据您提供的仓库 README 和提交记录，以下是昨日更新（提交 `8e37b8a`）的分析与总结：

### 1. 主要更新类型
- **功能新增**：支持在 **Ascend NPU**（华为昇腾）上训练 **Qwen3-Omni-MoE** 模型，并采用 **融合 RoPE**（Rotary Position Embedding）优化。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：新增 `ops`（算子）、`model`（模型定义）和 `config`（配置）模块，使 VeOmni 能够适配 Qwen3-Omni-MoE 架构在昇腾 NPU 上的训练流程，同时针对 RoPE 进行了算子融合。
- **与项目方向的关系**：项目 VeOmni 的核心目标是“Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo”，即提供一个模型中心的分布式训练框架，支持任意模态模型和多种硬件平台。本次更新明确扩展了对 **国产硬件（Ascend NPU）** 和 **最新多模态大模型（Qwen3-Omni-MoE）** 的支持，直接强化了项目的硬件兼容性和模型覆盖面，符合“Any Modality”和“Distributed Recipe Zoo”的理念。

### 3. 对项目的影响和潜在意义
- **硬件生态拓展**：引入昇腾 NPU 支持，使 VeOmni 不再局限于 NVIDIA GPU，有助于降低对特定硬件的依赖，提升在国产化场景下的可用性。
- **模型生态丰富**：Qwen3-Omni-MoE 是当前业界先进的多模态 MoE（混合专家）模型，支持其训练意味着 VeOmni 可处理更复杂、更大规模的视觉-语言-音频联合模型。
- **性能优化潜力**：融合 RoPE 算子（fused RoPE）通常能减少显存占用和计算延迟，对昇腾 NPU 上的训练效率有直接提升，也为未来在其他硬件上的类似优化提供了参考。

### 4. 值得关注的技术点
- **fused RoPE**：将 RoPE 计算融合进注意力机制中，减少 kernel launch 次数和访存开销，是适配特殊硬件（如昇腾 NPU）常见的性能优化手段。
- **ops 模块新增**：意味着 VeOmni 的算子库开始面向昇腾进行定制，后续可能继续增加更多硬件加速算子。
- **config 支持**：训练 Qwen3-Omni-MoE 需要特定的模型配置、分布式策略和优化器设置，本次提交一并更新了配置模板，降低了用户上手门槛。

### 5. 基于项目背景，提交如何影响项目发展
- **加速“任意硬件”愿景**：从仅支持 NVIDIA GPU 扩展到除昇腾外的更多国产 AI 芯片（如寒武纪、海光），为项目成为真正的“硬件无关”训练框架奠定基础。
- **吸引更广泛用户群体**：国内研究者和企业常受困于 GPU 禁运，昇腾支持将显著提升项目在高校和工业界的吸引力，扩大社区贡献者基础。
- **推动多模态 MoE 训练落地**：Qwen3-Omni-MoE 是开源社区高度关注的模型，VeOmni 率先提供训练 Recipe，有助于建立“极致灵活”的生态印象，与其他训练框架（如 Megatron、DeepSpeed）形成差异化。

**一句话概括**：本次提交使 VeOmni 首次支持国产昇腾 NPU 上的先进多模态 MoE 模型训练，标志项目从“单一 GPU”向“多硬件、多模态”的全面拓展迈出关键一步。

## 详细提交记录

### [8e37b8a](https://github.com/ByteDance-Seed/VeOmni/commit/8e37b8acbba04b044137fb82af3de49f8d66a9be)

- **作者**: zangyu
- **时间**: 2026-07-21T09:03:20Z
- **提交信息**: [ops, model, config] feat: support Qwen3-Omni-MoE training on Ascend NPU with fused RoPE (#910)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2517
- **最后更新**: 2026-07-22T13:13:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

以下是基于提交记录`[05e6608] Add SENSITIVE_LAYER_DTYPE for hidream-o1 (#1275)`的分析总结：

### 1. 主要更新类型
- **功能新增**：为特定模型`hidream-o1`引入了`SENSITIVE_LAYER_DTYPE`配置选项。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：添加了一个允许用户为`hidream-o1`模型中的“敏感层”指定独立数据类型的机制（例如，部分层使用fp32，其余层使用fp16/bf16）。
- **与项目方向关系**：LightX2V致力于成为**轻量级、可配置的视频生成推理框架**。该提交通过提供更细粒度的精度控制，增强了框架对不同模型（尤其是对数值稳定性敏感的模型）的适配能力，符合项目“灵活性”和“可调优”的宗旨。

### 3. 对项目的影响和潜在意义
- **直接好处**：提升`hidream-o1`模型在推理时的**数值稳定性**和**精度可控性**，避免因全局低精度导致的关键层输出异常。
- **潜在影响**：可能作为模板，未来其他模型也可复用此机制，从而整体提高框架对混合精度场景的鲁棒性。
- **用户价值**：允许高级用户在精度与速度之间更精细地权衡，尤其适用于需要保持高保真度输出的视频生成任务。

### 4. 值得关注的技术点
- **“敏感层”的识别方式**：提交未说明如何标记敏感层（可能基于权重/激活的分布，或通过经验手动指定）。这涉及模型内部结构理解。
- **实现方式**：推测是在模型加载或推理过程中，通过覆盖层的`dtype`属性实现，可能涉及对`torch.dtype`的转换钩子。
- **性能开销**：仅对特定层使用高精度，理论上对整体吞吐量影响较小，但可能增加显存占用（如果fp32层较多）。

### 5. 结合README项目背景，本次更新如何影响项目发展
- **完善模型支持矩阵**：`hidream-o1`是框架支持的模型之一，新增可配置性使该模型更易落地到实际生产场景。
- **推动框架成熟度**：表明项目正在从“功能可用”向“精细化调优”阶段演进，注重解决特定模型（如视频生成模型）的数值不稳定痛点。
- **吸引开发者社区**：此类功能通常由用户需求驱动，意味着社区或开发者对`hidream-o1`的推理优化有实际需求，框架的响应速度有助于巩固用户信任。

**补充说明**：昨日仅此一个提交，无其他Bug修复或文档更新。整体专注于模型推理精度的精细化控制。

## 详细提交记录

### [05e6608](https://github.com/ModelTC/LightX2V/commit/05e6608f54d0814ed021e7cbe9fb84d3c1007546)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-21T12:38:28Z
- **提交信息**: Add SENSITIVE_LAYER_DTYPE for hidream-o1 (#1275)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2178
- **最后更新**: 2026-07-22T09:38:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6001
- **最后更新**: 2026-07-22T14:35:50Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Igor Shovkun, yanqinz2, kangbintNV

## AI分析总结

## 昨日更新要点总结（2025-04-09）

### 1. 主要更新类型
- **功能新增**（3项）：可选normed输出、融合SwiGLU+NVFP4量化、Mamba checkpointing双内核拆分
- **性能优化**（4项）：自动调优加速、KDA解码内核统一、编译代码裁剪、JIT架构过滤
- **Bug修复**（1项）：自动调优器多进程冲突
- **文档更新**（2项）：审查指南、MSA/GDN API文档补充

### 2. 关键变更点与项目方向关系
| 提交 | 核心变更 | 与项目目标关联 |
|------|----------|----------------|
| `37b80f2` | `add_rmsnorm_fp4quant` 新增可选`y_out`参数，**一次运算同时输出normed结果和FP4量化** | 减少MoE层中两个消费者（FP4专家+路由门）的重复计算，**直接提升推理吞吐** |
| `7a4c24b` | 融合SwiGLU与NVFP4量化，**去除中间激活** | 消除显存带宽瓶颈，**符合推理场景的显存/计算协同优化** |
| `afd4754` | Mamba-2 SSU内核**拆分为precompute+main**，引入**环形缓冲区缓存** | 适配vLLM ReplaySSM协议，**支持更大batch的高效MTP解码** |
| `3c9da47` | 递归KDA解码**统一为单warp +自动tile选择** | 对比Triton实现**平均快1.2-1.7x**，巩固FFA在Blackwell上的性能优势 |
| `54642d4` | `mm_fp4`自动调优**并行编译+磁盘缓存** | 首次调优**从93.5s降至45.8s**，后续**仅4.35s**，**大幅降低开发者迭代成本** |
| `b43a71b` | 删除`dispatch`永远不会加载的架构代码 | JIT缓存安装包**减少587MB**，**降低部署体积** |
| `41c07b7` | 修复自动调优器使用其他runner的缓存 | 避免**静默性能退化或崩溃**，**提高多进程调优的鲁棒性** |

### 3. 对项目的影响与潜在意义
- **推理性能提升**：融合算子（SwiGLU+量化、RMSNorm+量化）和内核统一优化，直接加速LLM推理的 **MoE层、注意力层、FFN层**，覆盖主流架构（Qwen、Mamba、Gemma等）。
- **Blackwell生态夯实**：多项优化针对SM100+（B200/B300），**锁定NVFP4量化路径**，降低推理

## 详细提交记录

### [7f786be](https://github.com/flashinfer-ai/flashinfer/commit/7f786be972de1f4ded1a1db4255a9c29404289bc)

- **作者**: Alex Yang
- **时间**: 2026-07-21T22:31:01Z
- **提交信息**: Code review guidance proposal (#3790)

<!-- .github/pull_request_template.md -->

## 📌 Description

Aligning review focus and quality standard

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Added new code review guidance for both agent and human reviewers,
establishing a clear **speed vs accuracy** review posture.
* Introduced structured focus areas and checklists covering crash-prone
issues, API/interface conventions (including “Torch-free” documentation
expectations), testing/refcheck expectations, and comment/doc quality.
* Added dedicated guidance for kernel review (including confidence
calibration) and effort calibration to match review depth.
* Added an explicit workflow for **experimental APIs** under a separate,
issue-declared quality bar.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [37b80f2](https://github.com/flashinfer-ai/flashinfer/commit/37b80f25824c99b5a780b0afae26eae9a8807b30)

- **作者**: Guoming Zhang
- **时间**: 2026-07-21T22:09:31Z
- **提交信息**: feat: add optional normed-output (y_out) to add_rmsnorm_fp4quant (#4072)

<!-- .github/pull_request_template.md -->

## 📌 Description

add_rmsnorm_fp4quant fuses add + RMSNorm + FP4 quantization into one
CuTe-DSL kernel. It computes y = RMSNorm(residual + input) * weight and
quantizes y to FP4, but the normed y never leaves registers — it's
consumed only by the quantizer.

This is a problem when a second consumer needs y in its original
precision. In a Qwen3-Next MoE layer, the post-attention norm feeds two
readers at once:

the FP4 experts (want the FP4-quantized y), and
the router gate (wants y in bf16).
Today that forces two kernels — a separate fused_add_rmsnorm for the
router plus a standalone fp4_quantize for the experts — reading the same
normed tensor twice.

This PR adds an optional y_out tensor. When provided, the kernel also
writes the normed bf16/fp16 y (one extra [M, H] store in the epilogue),
so a single launch feeds both consumers. On Qwen3.6-35B-A3B-NVFP4 decode
(B200) this collapses fused_add_rmsnorm + two FP4 quantizes into one
kernel — roughly 8.4µs → 3.1µs per MoE layer per decode step.

✅ Key properties
Zero cost when unused. y_out=None is a compile-time specialization
threaded through the JIT cache key, so the default path generates the
identical kernel as before.
Non-invasive. The return-tuple arity is unchanged; y_out is written in
place.
Numerically transparent. The FP4 payload, both scale-factor layouts, and
the in-place residual update are byte-identical with and without y_out.
y_out itself matches the fp32 reference within 1–2 ULPs, and is the
un-scaled RMSNorm result (global_scale only affects the FP4 block
scales, never y).
Small overhead when used. +0.19µs at M=4 (2.87µs → 3.06µs, CUDA-graph
replay, PDL on) — just the extra store.

🧪 Tests
New TestYNormOutput class: correctness vs the fp32 reference,
byte-identity of the FP4/scale/residual outputs with and without y_out,
composition with output_both_sf_layouts, 3D inputs, MXFP4
(block_size=32), the global_scale ≠ 1 semantics, shape/dtype/device
guards, and trace-dispatch refusal. 145 passed on B200.

📎 Notes
The trace template models only the core FP4-quantize signature, so a
dispatch guard makes fi_trace refuse to emit a definition when y_out (or
the pre-existing output_both_sf_layouts) is active, rather than silently
dumping an incomplete one.
A full-file test run shows 96 unrelated failures in
TestFusedVsSeparateFP4Quantize::test_mxfp4_fused_matches_separate; these
are pre-existing on main (reproduced by reverting this kernel file) and
untouched by this change — the edit is entirely guarded by y_out is not
None.

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

- **New Features**
- Added optional `y_out` to `add_rmsnorm_fp4quant` to write `RMSNorm(x +
residual) * weight` (unscaled) into a caller-provided FP16/BF16 tensor
for both 2D and 3D inputs, including MXFP4 mode (block size 32).
- `y_out` can be used alongside `output_both_sf_layouts` while
preserving the existing FP4 payload, scale-factor outputs, and residual
updates.

- **Documentation**
- Updated tracing notes: trace/replay is not supported for `y_out` and
`output_both_sf_layouts`.

- **Tests**
- Added a dedicated test suite validating correctness, invariance vs
baseline outputs, and argument validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: nv-guomingz <137257613+nv-guomingz@users.noreply.github.com>

### [54642d4](https://github.com/flashinfer-ai/flashinfer/commit/54642d4591712982b91fac1af122d0b8e74501ce)

- **作者**: Brian K. Ryu
- **时间**: 2026-07-21T21:51:43Z
- **提交信息**: perf(gemm): Improve mm_fp4 cute-dsl autotune time via disk-cache and parallel compilation (#4029)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Follow-up to #3948 (top-N tactic ranking) and built on #3874 (CuTe-DSL
disk cache). Autotuned `mm_fp4(backend='cute-dsl')` still:
* Recompiles every tactic in-process
* Compiles serially, taking 2-3 seconds per kernel

This PR:

1. Persists mm_fp4 kernels to the on-disk CuTe-DSL cache. Loading
`JITLink` cached artifacts from disk is measured to be done in ~10 ms
per kernel.
2. Parallelizes first-time compilation. The autotuner checks for
not-yet-cached tactics with a subprocess pool (default 4, RAM-capped)
that persists directly into the shared disk cache.
* default pool size of 4 was set to be conservative. Empirically
measured RAM (RSS) size per compilation was ~1GB per compilation.

### Autotune time improvements
Evaluated with
`python3 benchmarks/flashinfer_benchmark.py --routine mm_fp4 --m 256 --n
1024 --k 7168 --out_dtype bfloat16 --backends cute-dsl
--use_128x4_sf_layout --use_nvfp4 --refcheck --autotune`

End-to-end process wall time on B200, 3 runs each:

| Scenario | Runs | Median | Speedup |
|---|---|---:|---:|                             
| Current main branch main (in-process serial compilation) | 94.9 / 93.5
/ 93.2 s | **93.5 s** | 1.0× |
| this PR, first run; cold disk cache (parallel compile + persist) |
45.8 / 44.6 / 46.0 s | **45.8 s** | **~2×** |
| this PR, every subsequent process; hot disk cache (load from disk) |
4.38 / 4.35 / 4.35 s | **4.35 s** | **~20×** |

Autotuned results are unchanged: the same tactics are profiled with
bitwise identical kernel and output; just changes in the compilation
infra.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance**
  * Improved FP4 GEMM startup by precompiling eligible CuTe-DSL tactics.
* Added parallel CuTe-DSL kernel compilation with persistent on-disk
caching to reduce repeated build times.
  * Strengthened device-scoped caching to speed up subsequent launches.
* **Reliability**
* Disk persistence failures now fall back gracefully, allowing kernels
to compile on demand.
* Updated FP4/MXF dtype handling and improved deterministic,
collision-resistant kernel naming.
* **Tests**
* Added coverage ensuring FP4 CuTe-DSL kernel names change with all
codegen arguments and are filename-safe.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [3c9da47](https://github.com/flashinfer-ai/flashinfer/commit/3c9da4747db034d97e2d235b0fa008c9bddef1bc)

- **作者**: Duncan Moss
- **时间**: 2026-07-21T19:29:26Z
- **提交信息**: perf(kda): unify recurrent decode on a faster one-warp kernel (#4001)

### Summary

This PR optimizes and simplifies the CuTe DSL recurrent-KDA
implementation on Blackwell:

- Uses a single register-tiled, one-warp kernel for D=64 and D=128.
- Automatically selects measured 8-, 16-, or 32-row tiles and tree or
dual-accumulator reductions.
- Removes the legacy base/vtile kernels, dispatch branches, compilation
caches, and environment overrides.
- Supports loading speculative token 0 from a separate read-only
committed-state pool.
- Supports applying sigmoid to beta inside the kernel.
- Simplifies the schedule tests and recurrent-KDA benchmark.

### Performance

Benchmarks were run on B300/SM103 with PyTorch 2.11.0+cu130 using CUDA
graphs. Latencies are in microseconds.

#### FLA comparison

`FLA/CuTe > 1` means FlashInfer is faster.

| Config | Batch | CuTe T=1 | FLA T=1 | FLA/CuTe T=1 | CuTe T=4 | FLA
T=4 | FLA/CuTe T=4 |
|:---|---:|---:|---:|---:|---:|---:|---:|
| H8-D64 | 1 | 2.6 | 3.4 | 1.32x | 4.6 | 7.2 | 1.58x |
| H8-D64 | 2 | 2.5 | 3.4 | 1.39x | 4.7 | 7.2 | 1.55x |
| H8-D64 | 4 | 2.5 | 3.4 | 1.37x | 4.8 | 7.2 | 1.52x |
| H8-D64 | 8 | 2.6 | 3.5 | 1.33x | 4.9 | 7.4 | 1.51x |
| H8-D64 | 16 | 2.8 | 3.9 | 1.37x | 5.6 | 8.7 | 1.56x |
| H8-D64 | 32 | 3.3 | 4.9 | 1.49x | 6.4 | 11.2 | 1.75x |
| H8-D64 | 64 | 4.1 | 7.5 | 1.85x | 8.0 | 19.7 | 2.46x |
| H8-D64 | 128 | 5.1 | 11.5 | 2.26x | 13.8 | 33.1 | 2.40x |
| H16-D128 | 1 | 2.5 | 3.6 | 1.44x | 6.8 | 8.4 | 1.25x |
| H16-D128 | 2 | 2.6 | 3.8 | 1.47x | 6.6 | 8.2 | 1.24x |
| H16-D128 | 4 | 2.7 | 4.6 | 1.68x | 7.9 | 10.0 | 1.28x |
| H16-D128 | 8 | 3.3 | 5.7 | 1.72x | 9.1 | 13.2 | 1.45x |
| H16-D128 | 16 | 4.4 | 8.8 | 2.01x | 17.3 | 23.6 | 1.36x |
| H16-D128 | 32 | 7.5 | 13.2 | 1.77x | 23.8 | 44.2 | 1.86x |
| H16-D128 | 64 | 12.9 | 24.7 | 1.92x | 52.2 | 83.0 | 1.59x |
| H16-D128 | 128 | 23.7 | 54.8 | 2.31x | 97.5 | 156.2 | 1.60x |
| H32-D128 | 1 | 2.6 | 3.8 | 1.46x | 7.0 | 8.6 | 1.23x |
| H32-D128 | 2 | 2.8 | 4.2 | 1.53x | 7.5 | 9.7 | 1.29x |
| H32-D128 | 4 | 3.4 | 5.8 | 1.72x | 9.1 | 13.2 | 1.45x |
| H32-D128 | 8 | 4.4 | 8.7 | 1.99x | 17.2 | 23.2 | 1.35x |
| H32-D128 | 16 | 7.7 | 13.1 | 1.71x | 24.2 | 44.7 | 1.84x |
| H32-D128 | 32 | 12.9 | 23.7 | 1.84x | 51.0 | 82.0 | 1.61x |
| H32-D128 | 64 | 23.9 | 52.2 | 2.18x | 97.4 | 155.9 | 1.60x |
| H32-D128 | 128 | 53.9 | 99.4 | 1.85x | 185.9 | 299.4 | 1.61x |

Geometric-mean speedup over the 24 configurations:

- T=1: **1.68x**
- T=4: **1.55x**

#### SGLang Triton comparison

This comparison uses the unchanged Triton implementation from [SGLang PR
#30113](https://github.com/sgl-project/sglang/pull/30113) at commit
`f66df9cac0517755578a28620aecfe322d73d05d`.

KDA decode, T=1:

| B | Triton (us) | FlashInfer (us) | Speedup | Output max diff | State
max diff |
|---:|---:|---:|---:|---:|---:|
| 1 | 4.15 | 4.13 | 1.00x | 2.98e-08 | 2.44e-04 |
| 4 | 6.16 | 4.13 | 1.49x | 2.98e-08 | 2.44e-04 |
| 16 | 6.18 | 6.18 | 1.00x | 1.91e-06 | 4.88e-04 |
| 32 | 10.28 | 8.23 | 1.25x | 1.91e-06 | 4.88e-04 |
| 64 | 18.46 | 14.37 | 1.28x | 1.91e-06 | 4.88e-04 |
| 128 | 29.77 | 24.55 | 1.21x | 7.63e-06 | 9.77e-04 |

Geometric-mean T=1 speedup: **1.195x**.

KDA target verify, T=8:

| B | Triton (us) | FlashInfer (us) | Speedup | Output max diff | State
max diff |
|---:|---:|---:|---:|---:|---:|
| 1 | 16.42 | 12.32 | 1.33x | 1.53e-05 | 4.88e-04 |
| 4 | 16.42 | 14.37 | 1.14x | 1.53e-05 | 9.77e-04 |
| 16 | 24.60 | 24.62 | 1.00x | 3.05e-05 | 9.77e-04 |
| 32 | 53.52 | 52.49 | 1.02x | 3.05e-05 | 9.77e-04 |
| 64 | 99.40 | 97.76 | 1.02x | 6.10e-05 | 9.77e-04 |
| 128 | 175.54 | 173.34 | 1.01x | 3.05e-05 | 9.77e-04 |

Geometric-mean T=8 speedup: **1.081x**.

### Correctness and validation

The accuracy tests, tolerances, and benchmark comparison paths were not
changed to obtain these results.

- `74 passed` in `tests/kda/test_recurrent_kda.py`
- D=64 and D=128
- Standard and speculative decode
- Precomputed, softplus, and lower-bound gate modes
- Separate committed-state and in-place state sources
- Padded and variable-length sequences
- All active 8-, 16-, and 32-row schedules
- Tree and dual-accumulator reductions
- Ruff: all checks passed
- `git diff --check`: passed


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Recurrent KDA decoding now supports initializing from a separate
committed state source using corresponding state indices.
  * Added `beta_is_logit` to interpret beta inputs as logits.
* Added recurrent KDA tracing support, including a new trace
configuration example.
* **Performance**
* Updated recurrent KDA decoding to use an optimized tiled execution
path with improved specialization/schedule selection.
* **Bug Fixes**
* Improved recurrent/spec decode correctness, including BF16 comparison
behavior and padded output handling.
* Correct handling for `T=1` with empty sequence rows (no token reads or
state mutation).
* **Documentation**
  * Refined recurrent KDA benchmark documentation for `T=1` vs `T>1`.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [afd4754](https://github.com/flashinfer-ai/flashinfer/commit/afd47547f6fae12b0eb6353d7c282081f2ef427a)

- **作者**: Igor Shovkun
- **时间**: 2026-07-21T18:39:53Z
- **提交信息**:  mamba checkpointing SSU: two-kernel split + ring-buffer cache for checkpointing SSU (#3975)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds two things to the checkpointing-SSU (Mamba-2 MTP-replay) kernel.

**1. Two-kernel split.** An alternative to the single monolithic kernel
that wins
at larger batch. A **precompute** kernel produces the conv1d
coefficients (the
C·B contraction and the cumulative-A·dt decays); a **persistent,
grid-stride
main** kernel does the state replay + output projection, consuming the
precompute's outputs through caller-provided scratch
(`cb_scaled` / `cumAdt_vec` / `cb_old` / `cumAdt_old` — graph-safe,
allocated like
`out`). The public API auto-dispatches on `batch × nheads` (monolith
below
~1 work-unit/SM, split above); `algorithm="monolith"|"two-kernel"`
forces either
path for benchmarking. The split covers 2- and 4-byte state
(bf16/fp16/fp32);
**8-bit state (int8/fp8) always runs the monolith**
(`checkpointing_ssu_kernel_8bit`)
— its quantize + per-block-scale flow doesn't factor cleanly into
precompute→main.

**2. Ring-buffer cache contract (breaking).** The MTP-replay cache
tensors change
from the double-buffered `old_x` / `old_B` / `old_dt` / `old_cumAdt` +
`cache_buf_idx` to single-buffered, head-major **ring buffers**:

| tensor       | shape                                   | dtype |
|--------------|-----------------------------------------|-------|
| `x_cache`    | `(state_cache_size, nheads, L, dim)`    | input |
| `B_cache`    | `(state_cache_size, ngroups, L, dstate)`| input |
| `dt_cache`   | `(state_cache_size, nheads, L)`         | f32   |
| `ring_start` | `(state_cache_size,)`                   | i32   |

with `L = max_window + npredicted`. Live tokens are `(ring_start + j)
mod L` for
`j ∈ [0, pnat)`; appends land at `(ring_start + pnat + i) mod L`. The
**host owns
all ring bookkeeping** (advancing `ring_start` on flush) — the kernels
only read
`ring_start` / `prev_num_accepted` and append. No decay is cached:
`cumAdt` is a
prefix sum and is not invariant under the ring-start advance a flush
performs, so
it is recomputed from the `dt` ring; on the two-kernel path the
precompute stages
it into the `cumAdt_old` scratch for the main. Matches the ReplaySSM
contract.

## 🔍 Related Issues

Design follows the ReplaySSM cache contract from vLLM PR
vllm-project/vllm#48018.
<!-- link the FlashInfer tracking issue here if one exists -->

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit`.
- [x] I have installed the hooks with `pre-commit install`.
- [x] The hooks (ruff / clang-format / mypy) pass on the changed files.

## 🧪 Tests

- [x] Tests added/updated — `tests/mamba/test_checkpointing_ssu.py`
rewritten for
the ring contract: two-kernel-vs-monolith bit-exactness across
write/no-write,
`d_split`, pipeline-stages, meta-ring refill, and per-state-dtype
(f16/f32/mixed)
cases; ring wraparound; varlen; non-contiguous strides; determinism. All
validated against the Triton reference
(`replay_selective_state_update.py`).
- [x] All tests passing — the two-kernel-vs-monolith parity battery +
the broad
  correctness subset pass on B200.

## Reviewer Notes

- **Breaking change.** The cache API changes shape and semantics
(double-buffer →
ring). Callers must switch to `x_cache / B_cache / dt_cache /
ring_start` and
take over `ring_start` advancement on flush. The custom-op
`mutates_args` set
  and the wrapper validation are updated to match.
- **8-bit scope.** The two-kernel split is 2/4-byte-state only; 8-bit
stays on the
  monolith (see Description).
- **Perf** (B200/B300, mixed-PNAT sweep with conv1d + PDL — the
production shape):
the two-kernel split overtakes the monolith from ~256 work-units up. The
ring
migration is roughly perf-neutral: the monolith is at parity (slightly
faster
from the gather rewrite) and the two-kernel no-write path is at parity;
the
large-batch two-kernel path carries a small floor (~1.5%) from
recomputing the
decay the ring no longer caches, exposed to ~10% at one low-occupancy
batch
  (~32) — a precompute head-tiling tune can close that if needed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added ring-buffer-based SSU checkpointing with monolithic and
two-kernel execution modes.
* Added variable-length sequence support, optional causal convolution
integration, and improved cache handling.
* Added Triton replay reference implementations and expanded CUDA/Triton
compatibility options.

* **Benchmarks**
* Added mixed-checkpointing analysis, PNAT sampling, CSV export,
plotting, and benchmark collection tools.

* **Bug Fixes**
* Improved GPU feature detection and stochastic-rounding support across
supported hardware.

* **Tests**
* Expanded coverage for replay modes, ring caches, varlen inputs,
quantized states, determinism, and two-kernel execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [b43a71b](https://github.com/flashinfer-ai/flashinfer/commit/b43a71b28696369af640d6bcae9c8a621292d6df)

- **作者**: yichengj
- **时间**: 2026-07-21T18:16:51Z
- **提交信息**: perf(jit): prune arch gencode that dispatch can never load (#4073)

## 📌 Description

Follow-up to #3947, which removed compiled GPU code that SM12x devices
can never run. This PR extends the same audit to the whole tree: every
module's `supported_major_versions` list was checked against the
dispatch logic that decides which module a GPU actually loads. Four
lists still contained architectures whose GPUs can never load the
module:

| module | change | why the removed entries are dead |
|---|---|---|
| mamba SSU base | `[8, 9, 10, 11]` → `[8]` | SM90 and newer GPUs always
load the sm90 or sm100 variant instead |
| mamba SSU sm90 | `[9, 10, 11]` → `[9]` | SM100 and newer GPUs always
load the sm100 variant |
| fp8 GEMM (`gemm_sm100`) | `[10, 11]` → `[10]` | every caller accepts
SM100 only; SM110 gets an error before the module loads |
| xqa | `[9, 10, 11, 12]` → `[9, 10, 12]` | the xqa API rejects SM110
before the module can load |

`aot.py` gets a matching change: the two mamba modules are now prebuilt
only for the build targets that load them (base for SM8x, sm90 variant
for SM9x). This is required: after the prune, prebuilding the base
module in a wheel with no SM8x target has no architecture left to
compile for and fails the build.

### Result

This further removes about 587 MB of installed size from the cu130
aarch64 jit-cache wheel, on top of the ~1 GB removed by #3947:

| pruned GPU code | installed |
|---|---|
| mamba SSU base variants (48 modules) | 214 MB |
| mamba SSU sm90 variants (48 modules) | 267 MB |
| xqa (384 modules), SM110 code | 56 MB |
| fp8 GEMM (`gemm_sm100`), SM110 code | 50 MB |

The xqa and fp8 GEMM rows are SM110 code, which only exists in cu130
aarch64 wheels (the only build that targets SM110). The mamba rows apply
to every wheel.

## 🔍 Related Issues

#3170 (cross-cutting item 10, extended beyond SM12x).

## 🧪 Tests

- A GPU-free dispatch simulation (45 cases): for every compute
capability from 8.0 to 12.1, dispatch picks the expected module, and
that module still compiles for the architecture. All pass on this
branch. Removing a live entry on purpose makes exactly the matching case
fail, which confirms the check can catch a bad prune.
- Runtime verification on H100 (SM90) and B200 (SM100), JIT-compiling
this branch into a fresh cache. All affected suites pass: mamba SSU and
xqa on both machines, and the `gemm_sm100` fp8 GEMM suite on B200. The
cache afterwards holds only sm90 variants on H100 and only sm100
variants on B200, so dispatch never requested the pruned modules.
- `pre-commit run` on the changed files is clean.

## Reviewer Notes

- Two more dead entries (SM110 in the sm103 fp4 and cutlass bf16 GEMM
modules) stay in place: those modules are not prebuilt into wheels, so
keeping the entries costs nothing and future SM110 support there needs
no list edit.
- The dead verdicts reflect today's dispatch. If a later change routes
one of these architectures back (for example, Thor support in xqa), the
entry must be re-added here.
- The audit also found the opposite mismatch: some modules do run on
architectures that wheels never prebuild them for (several SM110-capable
modules, and the trtllm-gen fused MoE on SM12x). Left unchanged, since
adding prebuilds grows wheels and deserves its own decision.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved GPU architecture targeting for generated CUDA kernels.
* Corrected architecture-specific generation for selective state update,
GEMM, and XQA kernels.
* Reduced compilation attempts for unsupported GPU architectures,
improving build compatibility and reliability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [41c07b7](https://github.com/flashinfer-ai/flashinfer/commit/41c07b7783557a994a7d4afcca5ec29c6401e359)

- **作者**: yanqinz2
- **时间**: 2026-07-21T17:36:24Z
- **提交信息**: Yanqinz/fix autotuner using autotuning plan from other runners (#4004)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR removes the explicit runner position index used in autotuner to
prevent it using autotuning plan from other runners, which can cause
either silent perf loss, or even crash

## 🔍 Related Issues

https://github.com/flashinfer-ai/flashinfer/issues/3999

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved autotuning cache lookup reliability across runner
configurations.
* Preserved distinct tuning results for configurations with different
extra parameters.
* Added support for non-integer tactic values in tuning configurations.
* Ensured cached tactics are matched to the correct runner rather than
relying on runner order.
* Improved compatibility when loading and saving existing tuning
configuration files.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yanqin Zhai <yanqinz@nvidia.com>

### [06400d0](https://github.com/flashinfer-ai/flashinfer/commit/06400d062a2d51564bbe781f6f811d0b75ca593e)

- **作者**: kangbintNV
- **时间**: 2026-07-21T07:35:47Z
- **提交信息**: docs: fix MSA and GDN doc-check findings (#4058)

Fix documentation-check regressions reported in the v0.6.15 nightly doc
check.

This PR:
- adds `flashinfer.msa_ops` API entries to `docs/api/sparse.rst`
- adds `_radix_top_k` to `docs/api/sampling.rst`
- documents missing `msa_proxy_score`, `msa_proxy_score_fp4`, and
`msa_sparse_decode_attention` parameters
- documents GDN env vars in `CLAUDE.md`

Likely introduced by:
- #3655 (`feat(attn): Enable MiniMax Sparse Attention (MSA) for Consumer
Blackwell GPUs (SM120/121)`)
- #3720 (`feat(gdn): add output-only BF16-state WY MTP decode kernel`)
- #3908 (`Ameyn/gdn wy perf followup`)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Added API reference entries for Minimax Sparse Attention capabilities,
including scoring, selection, sparse attention, and decoding.
* Expanded parameter documentation for proxy-score and sparse decode
attention APIs.
* Added quick-reference commands for configuring native and strided
execution paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [7a4c24b](https://github.com/flashinfer-ai/flashinfer/commit/7a4c24b6a1e002835e3feb6ab4974e43a4ff117e)

- **作者**: Philipp Hack
- **时间**: 2026-07-21T07:22:52Z
- **提交信息**: feat: CuTe-DSL Fused SwiGLU NVFP4 Quantization (#4040)

## 📌 Description

Adds `silu_and_mul_nvfp4_quantize`, a fused SwiGLU and NVFP4
quantization path for FP16 and BF16 inputs. It computes `silu(gate) *
up` and quantizes the result without materializing the intermediate
activation.

The CuTe-DSL implementation extends the existing linear and swizzled
NVFP4 kernels and supports linear, 128x4, and 8x4 scale-factor layouts,
the fast/exact scale-math modes, and the experimental 4over6 recipe. The
public API validates Blackwell support and handles empty inputs and
misaligned storage views. It requires SM100+ and the CuTe-DSL backend.

Also adds public exports, FP4 quantization documentation, a benchmark,
an fi_trace definition with a self-contained reference, and correctness
tests.

<details>
<summary>On GB200, `bench_silu_and_mul_nvfp4_quantize.py` measured a
1.19x geomean speedup over the equivalent unfused CuTe-DSL path.
</summary>

<table>
<thead>
<tr>
<th align="right">M</th>
<th align="right">K</th>
<th align="right">Fused (us)</th>
<th align="right">Unfused (us)</th>
<th align="right">Speedup</th>
</tr>
</thead>
<tbody>
<tr><td align="right">1024</td><td align="right">2048</td><td
align="right">11.3</td><td align="right">15.6</td><td
align="right">1.38x</td></tr>
<tr><td align="right">1024</td><td align="right">4096</td><td
align="right">13.2</td><td align="right">14.7</td><td
align="right">1.11x</td></tr>
<tr><td align="right">1024</td><td align="right">8192</td><td
align="right">17.4</td><td align="right">19.5</td><td
align="right">1.12x</td></tr>
<tr><td align="right">1024</td><td align="right">16384</td><td
align="right">25.6</td><td align="right">29.7</td><td
align="right">1.16x</td></tr>
<tr><td align="right">1536</td><td align="right">2048</td><td
align="right">11.3</td><td align="right">13.3</td><td
align="right">1.17x</td></tr>
<tr><td align="right">1536</td><td align="right">4096</td><td
align="right">15.3</td><td align="right">16.4</td><td
align="right">1.07x</td></tr>
<tr><td align="right">1536</td><td align="right">8192</td><td
align="right">23.6</td><td align="right">25.5</td><td
align="right">1.08x</td></tr>
<tr><td align="right">1536</td><td align="right">16384</td><td
align="right">35.5</td><td align="right">39.9</td><td
align="right">1.12x</td></tr>
<tr><td align="right">2048</td><td align="right">2048</td><td
align="right">13.3</td><td align="right">14.3</td><td
align="right">1.07x</td></tr>
<tr><td align="right">2048</td><td align="right">4096</td><td
align="right">17.4</td><td align="right">19.4</td><td
align="right">1.12x</td></tr>
<tr><td align="right">2048</td><td align="right">8192</td><td
align="right">27.6</td><td align="right">31.3</td><td
align="right">1.13x</td></tr>
<tr><td align="right">2048</td><td align="right">16384</td><td
align="right">44.0</td><td align="right">52.2</td><td
align="right">1.19x</td></tr>
<tr><td align="right">4096</td><td align="right">2048</td><td
align="right">17.4</td><td align="right">19.4</td><td
align="right">1.12x</td></tr>
<tr><td align="right">4096</td><td align="right">4096</td><td
align="right">27.6</td><td align="right">29.7</td><td
align="right">1.07x</td></tr>
<tr><td align="right">4096</td><td align="right">8192</td><td
align="right">44.0</td><td align="right">54.3</td><td
align="right">1.23x</td></tr>
<tr><td align="right">4096</td><td align="right">16384</td><td
align="right">72.8</td><td align="right">95.1</td><td
align="right">1.31x</td></tr>
<tr><td align="right">4608</td><td align="right">2048</td><td
align="right">19.5</td><td align="right">19.4</td><td
align="right">1.00x</td></tr>
<tr><td align="right">4608</td><td align="right">4096</td><td
align="right">29.7</td><td align="right">31.7</td><td
align="right">1.07x</td></tr>
<tr><td align="right">4608</td><td align="right">8192</td><td
align="right">48.1</td><td align="right">59.4</td><td
align="right">1.23x</td></tr>
<tr><td align="right">4608</td><td align="right">16384</td><td
align="right">81.9</td><td align="right">104.4</td><td
align="right">1.28x</td></tr>
<tr><td align="right">8192</td><td align="right">2048</td><td
align="right">27.6</td><td align="right">27.6</td><td
align="right">1.00x</td></tr>
<tr><td align="right">8192</td><td align="right">4096</td><td
align="right">44.0</td><td align="right">51.2</td><td
align="right">1.16x</td></tr>
<tr><td align="right">8192</td><td align="right">8192</td><td
align="right">76.8</td><td align="right">97.3</td><td
align="right">1.27x</td></tr>
<tr><td align="right">8192</td><td align="right">16384</td><td
align="right">136.2</td><td align="right">174.1</td><td
align="right">1.28x</td></tr>
<tr><td align="right">16384</td><td align="right">2048</td><td
align="right">44.0</td><td align="right">48.2</td><td
align="right">1.09x</td></tr>
<tr><td align="right">16384</td><td align="right">4096</td><td
align="right">76.8</td><td align="right">93.2</td><td
align="right">1.21x</td></tr>
<tr><td align="right">16384</td><td align="right">8192</td><td
align="right">140.0</td><td align="right">181.2</td><td
align="right">1.29x</td></tr>
<tr><td align="right">16384</td><td align="right">16384</td><td
align="right">257.0</td><td align="right">332.8</td><td
align="right">1.29x</td></tr>
<tr><td align="right">32768</td><td align="right">2048</td><td
align="right">76.8</td><td align="right">93.2</td><td
align="right">1.21x</td></tr>
<tr><td align="right">32768</td><td align="right">4096</td><td
align="right">140.3</td><td align="right">173.1</td><td
align="right">1.23x</td></tr>
<tr><td align="right">32768</td><td align="right">8192</td><td
align="right">264.2</td><td align="right">350.0</td><td
align="right">1.32x</td></tr>
<tr><td align="right">32768</td><td align="right">16384</td><td
align="right">497.7</td><td align="right">654.3</td><td
align="right">1.31x</td></tr>
<tr><td align="right">65536</td><td align="right">2048</td><td
align="right">140.0</td><td align="right">170.8</td><td
align="right">1.22x</td></tr>
<tr><td align="right">65536</td><td align="right">4096</td><td
align="right">264.2</td><td align="right">331.4</td><td
align="right">1.25x</td></tr>
<tr><td align="right">65536</td><td align="right">8192</td><td
align="right">512.4</td><td align="right">689.2</td><td
align="right">1.34x</td></tr>
<tr><td align="right">65536</td><td align="right">16384</td><td
align="right">978.2</td><td align="right">1298.5</td><td
align="right">1.33x</td></tr>
</tbody>
</table>

</details>

## 🔍 Related Issues

N/A

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

Local (all passed): `python -m pre_commit run --all-files`; `pytest -v
tests/utils/test_fp4_quantize.py`; `pytest -v tests/trace/` (SM100 +
CuTe-DSL).

New coverage: fused-versus-unfused parity across FP16/BF16 inputs,
linear, 128x4, and 8x4 scale layouts, multiple K sizes, fast/exact scale
math, and the 4over6 recipe; dequantized round-trip trace-reference
correctness.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added fused SiLU-and-multiply + NVFP4 quantization for supported GPUs,
with both linear and swizzled scale layouts.
  * Exposed the operation in the public package APIs.
  * Added trace support for the fused operation.

* **Documentation**
  * Updated FP4 quantization API docs to include the new fused function.

* **Tests**
* Added correctness coverage for fused outputs, scale layouts, 4over6
configurations, and trace references.
  * Added a benchmark comparing fused vs. unfused performance.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3869
- **最后更新**: 2026-07-22T12:47:51Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34133
- **最后更新**: 2026-07-22T13:37:50Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Dhruv Nair, Álvaro Somoza, Linoy Tsaban

## AI分析总结

根据提供的提交记录和项目背景（`huggingface/diffusers` 专注于扩散模型，最初支持 PyTorch/JAX/Flax 等多框架），以下是昨日更新的关键要点：

---

### 1. 主要更新类型
- **代码重构/清理**：移除 JAX/Flax 支持（[80bfe77]）
- **Bug 修复**：Dreambooth LoRA 训练脚本中的长宽比分桶问题（[2919c50]）；Modular Diffusers 中组卸载设备不匹配（[ba66c64]）
- **测试改进**：将注意力处理器测试移植到 pytest（[58a0c4d]）

---

### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 变更内容 | 与项目方向的关系 |
|------|---------|------------------|
| [80bfe77] | **完全移除 JAX/Flax 支持**：删除所有 Flax 模型、调度器、流水线、加载工具、CI 配置、文档等。仅保留 PyTorch 核心。Flax 训练示例仍保留但标记为版本限制（≤0.39.x）。 | 项目明确聚焦 PyTorch 生态，简化维护负担，提升开发效率。与 HuggingFace 近期缩减多框架支持的策略一致（如 `transformers` 也曾弱化 Flax）。 |
| [2919c50] | 修复 Dreambooth 脚本中 **长宽比分桶**（aspect ratio bucketing）逻辑，同时引入 caption dropout 和即时桶（on-the-fly buckets）。 | 提升 LoRA 训练脚本的稳定性和灵活性，迎合社区对高质量微调的需求。 |
| [ba66c64] | 修复 **Modular Diffusers**（模块化架构）中组卸载时的设备不匹配错误。 | 模块化是 diffusers 未来演进方向（参考近期引入的 `module` API），此类修复确保新架构的可靠性。 |
| [58a0c4d] | 注意力处理器测试从 `unittest` 迁移到 `pytest`。 | 测试现代化，提高可读性和扩展性，为后续注意力机制优化（如 Flash Attention）铺路。 |

---

### 3. 对项目的影响和潜在意义
- **重大架构变化**：移除 Flax 意味着约 20%-30% 的代码量削减，CI 速度提升，但会丢失部分使用 JAX/TPU 的用户。潜在意义：团队可集中资源优化 PyTorch 性能（例如 FP8、编译加速）和新功能开发（如视频扩散、可控生成）。
- **训练脚本质量提升**：长宽比分桶修复直接改善 Dreambooth 在非正方形分辨率下的训练效果，这是社区高频诉求。
- **模块化稳定性修复**：为即将发布的 `diffusers 1.0` 的模块化 API 消除隐患。

---

### 4. 值得关注的技术点
- **Flax 兼容性保留**：虽然删除了 Flax 代码，但依然在下载时忽略 `*.msgpack` 文件，保持对旧 Hub 仓库的兼容。旧 `model_index.json` 中的 Flax 类名不再转换，需用户手动处理。
- **即时桶（on-the-fly buckets）**：训练时动态计算桶边界，避免预计算带来的分辨率限制，提升灵活性。
- **pytest 迁移**：测试框架升级，未来可轻松集成参数化测试（如多设备、多精度）。

---

### 5. 基于 README 背景，这些提交如何影响项目发展
- **聚焦核心能力**：README 中的多框架支持描述即将过时，项目正从“多框架扩散库”转变为“PyTorch 专用扩散库”，这与 HuggingFace 的 `diffusers` 实际使用情况（绝大多数用户使用 PyTorch）相符。
- **强化微调生态**：修复 Dreambooth 脚本是回应社区对 LoRA、DreamBooth 等微调方法的诉求，巩固项目在个性化生成领域的地位。
- **为未来架构奠基**：模块化修复和 pytest 测试改进，为引入更复杂的组件（如多模态、视频、3D 扩散）奠定更稳健的基础。

> **总结**：昨日更新核心是**砍掉 Flax 包袱**，同时修复微调和模块化中的关键 bug，项目正加速向 PyTorch 极致化、模块化、高质量微调方向演进。

## 详细提交记录

### [2919c50](https://github.com/huggingface/diffusers/commit/2919c50962c375e32b9fa40ae5fad50cd3251332)

- **作者**: Linoy Tsaban
- **时间**: 2026-07-21T21:12:31Z
- **提交信息**: [lora training] fix aspect ratio bucketing in dreambooth scripts (+ caption dropout, on-the-fly buckets) (#14158)

### [ba66c64](https://github.com/huggingface/diffusers/commit/ba66c64a2c85f38309846623b630b279bb9af133)

- **作者**: Álvaro Somoza
- **时间**: 2026-07-21T18:55:27Z
- **提交信息**: [Modular Diffusers] Fix group offload device mismatch (#14252)

fix

### [58a0c4d](https://github.com/huggingface/diffusers/commit/58a0c4d58d92b2e30ef08c506c267cbd4dfe9bca)

- **作者**: Sayak Paul
- **时间**: 2026-07-21T08:12:34Z
- **提交信息**: [tests] port attention processor tests to use pytest (#14161)

port attention processor tests to use pytest

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

### [80bfe77](https://github.com/huggingface/diffusers/commit/80bfe77b572113a970471931de1c23c3680b971f)

- **作者**: Dhruv Nair
- **时间**: 2026-07-21T07:42:27Z
- **提交信息**: Remove JAX/Flax  (#14169)

* Remove JAX/Flax support

Deletes all Flax models, schedulers, pipelines, and loading utilities,
the from_flax loading path, flax/jax packaging extras, Flax CI filters,
Flax training examples, and Flax content in translated docs.

Hub compatibility is preserved: Flax class names in old model_index.json
files are still stripped to their PyTorch equivalents, and *.msgpack
files in repos are still ignored during download.

* Drop Flax class-name remapping from model_index.json loading

Flax-saved checkpoint metadata is no longer recognized: class names like
FlaxStableDiffusionPipeline in model_index.json now fail to resolve
instead of being remapped to their PyTorch equivalents. *.msgpack files
in hub repos are still ignored during download.

* Restore Flax training examples

The example scripts are standalone and still work with diffusers<=0.39.x.
A warning note is added to each Flax README section pointing out the
version requirement now that the library itself no longer ships Flax.

* update

* Repoint scheduler default-config tests off the Flax fixture

* Repoint example training tests off the Flax fixture

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 426
- **最后更新**: 2026-07-21T12:34:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12735
- **最后更新**: 2026-07-22T12:51:16Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 3
- **主要提交者**: MaskYuan(SII), Hz_Zhang, Zhongjie Duan

## AI分析总结

以下是对 DiffSynth-Studio 仓库昨日（基于提交时间）更新的分析总结：

### 1. 主要更新类型
- **Bug 修复**：2 项（float8 缩放范围、WanModel 批量维度广播）
- **性能优化**：1 项（acestep 低显存补丁）
- **文档/用户体验改进**：1 项（下载提示）
- **重构/兼容性**：1 项（重新导出 xfuser 工具函数）
- **版本管理**：1 项（版本号升至 2.0.18）

### 2. 关键变更点及其与项目方向的关系
- **`float8_e4m3fnuz` 缩放范围修复**：修正低精度计算时的数值偏移，直接提升模型推理精度与稳定性，与项目追求高保真生成效果的目标一致。
- **WanModel 批量头部调制广播修复**：修复批量大小 >1 时注意力头调制失败的问题，使项目能更好地支持批量视频/图像合成场景，契合 README 中“视频等复杂内容生成”的定位。
- **acestep 低显存补丁**：优化显存占用，降低硬件门槛，符合项目模型“易用性”和“可部署性”的长期方向。
- **重新导出 xfuser 工具函数**：确保序列并行相关功能的接口兼容性，为后续分布式推理或长序列生成（如长视频）铺路。
- **下载提示增强**：改善用户首次使用时的引导体验，属文档类完善。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：两个 bug 修复直接解决了实测中可能遇到的生成失败或精度劣化问题，提升模型输出可靠性。
- **硬件友好性**：低显存补丁让更多配备 6–8GB 显存的用户可尝试 acestep 等高精度采样器，扩大受众。
- **体系化进度**：版本号更新表明代码处于活跃维护期，社区反馈能快速响应。

### 4. 值得关注的技术点
- **低精度计算**：`float8_e4m3fnuz` 修复表明项目在探索 8-bit 推理以加速/减少显存，同时需谨慎处理范围缩放。
- **序列并行接口**：重新导出 `get_sequence_parallel_rank` 等函数，暗示项目可能在为长上下文（如长视频、高分辨率）生成准备分布式推理方案。
- **WanModel 结构**：修复头部调制广播说明该架构的注意力机制存在 batch 维度特殊处理，这可能是 Wan 系列模型用于视频的关键设计。

### 5. 对项目发展的影响（结合 README）
- DiffSynth-Studio 的核心是提供开放、易用的扩散合成工具。昨日更新涵盖了从**底层精度**（float8）到**顶层批处理**（WanModel batch) 再到**资源开销**（低显存）的全链路优化，体现了“兼顾高质量与用户体验”的平衡策略。
- 特别是低显存补丁和下载提示，直接降低了新用户的上手门槛，有助于社区规模扩大。
- 重构性提交（重新导出）维护了代码整洁性与接口一致性，利于后续功能迭代。整体而言，此次更新是项目成熟化过程中的一次扎实巩固。

## 详细提交记录

### [c020226](https://github.com/modelscope/DiffSynth-Studio/commit/c02022681b09424e778b2d6275ee657a532834d3)

- **作者**: Zhongjie Duan
- **时间**: 2026-07-21T09:11:28Z
- **提交信息**: add downloading tips (#1535)

* add downloading tips

* Update diffsynth/core/loader/config.py

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

---------

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [65732bc](https://github.com/modelscope/DiffSynth-Studio/commit/65732bcbb461f8685e567e85ffdde8ebe55d3b8c)

- **作者**: MaskYuan(SII)
- **时间**: 2026-07-21T07:59:17Z
- **提交信息**: Fix float8_e4m3fnuz scaling range (#1528)

Thanks for your contribution.

### [c91fd87](https://github.com/modelscope/DiffSynth-Studio/commit/c91fd870136c08453685a5b63e50e388a60ee9a6)

- **作者**: Hz_Zhang
- **时间**: 2026-07-21T07:57:23Z
- **提交信息**: Re-export get_sequence_parallel_rank and get_sp_group from xfuser utils (#1521)

### [99098b5](https://github.com/modelscope/DiffSynth-Studio/commit/99098b50bae807e18523e9990c373d9436c4e03e)

- **作者**: Hz_Zhang
- **时间**: 2026-07-21T07:55:32Z
- **提交信息**: Fix Head modulation broadcast for batch size > 1 in WanModel (#1517)

Thanks for your contribution.

### [304b6b4](https://github.com/modelscope/DiffSynth-Studio/commit/304b6b43d0e50d2284a04609a9d9580728fd101c)

- **作者**: Zhongjie Duan
- **时间**: 2026-07-21T07:36:14Z
- **提交信息**: update version to 2.0.18 (#1534)

### [d666ec0](https://github.com/modelscope/DiffSynth-Studio/commit/d666ec040c152dd9199699b700c4011da54c572b)

- **作者**: Zhongjie Duan
- **时间**: 2026-07-21T07:34:55Z
- **提交信息**: acestep low-vram patch (#1533)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30632
- **最后更新**: 2026-07-22T15:27:53Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 22
- **主要提交者**: Yuan Luo, Zhangheng, Alison Shao

## AI分析总结

好的，以下是针对 sgl-project/sglang 仓库昨日提交记录的分析总结，结合项目背景（高性能 LLM 推理引擎，支持多硬件、多模态、FP8、Mamba、LoRA 等）进行解读。

---

### 1. 主要更新类型
- **性能优化**: 7 项（Page-Table 跳过、FP8 GEMM 后端切换、LongCat-Flash GEMM、HiCache 优化、Mamba 推测解码、CUDA 图预填充等）
- **Bug 修复**: 6 项（CUDA 导入兼容性、DP 注意力 Top-k 掩码、编码器 DP 嵌入设备放置、工具调用流式丢失、NPU MoE OOM、extra_buffer_lazy 守卫绕过）
- **CI / 测试增强**: 5 项（B200 多模态测试路由、Nightly 测试添加、NIXL 分解功能测试、KL Mamba HiCache 测试释放、CI 权限文件更新）
- **功能新增 / 重构**: 4 项（AutoWeightLoader 支持原生模型、MXFP4 量化 AMD 支持、删除旧 kernel 改用 flashinfer、参数清理）
- **文档 / 食谱**: 3 项（DeepSeek-V4 重新基准测试、新模型 Laguna-S-2.1 食谱、CODEOWNERS 目录更新）
- **其他**: 2 项（健康检查鲁棒性、debug 断言门控）

### 2. 关键变更点与项目方向关系
- **删除 sgl-kernel AOT `bmm_fp8`** → 改用 `flashinfer.bmm_fp8`，统一依赖并减少维护成本，符合项目“复用社区高性能 kernel”趋势。
- **FP8 per-tensor GEMM 后端 SM120 切到 cuBLAS** → 针对最新 NVIDIA 架构优化，提升 FP8 推理吞吐，契合项目对最新硬件的快速适配。
- **HiCache 两步优化**（L3 预取同步、参数清理）→ 增强混合 / DSA 场景下的缓存效率，支持更大上下文推理。
- **LongCat-Flash 路由器 GEMM 利用 HPC-Ops bf16xfp32 kernel** → 针对 MoE 路由场景极致调优，呼应项目“专业路由器优化”路线。
- **Mamba 推测解码 + extra_buffer_lazy** → 进一步挖掘 Mamba 模型加速潜力，扩大对状态空间模型的支持。
- **MXFP4 量化 AMD 支持** → 完善 AMD GPU 生态，符合项目“多硬件后端”目标（已支持 NVIDIA、AMD、NPU）。
- **AutoWeightLoader 支持原生模型** → 简化加载流程，降低用户上手门槛，利于社区贡献模型。
- **DP 注意力相关修复与默认开启 CUDA 图预填充** → 提升分布式推理稳定性和效率。

### 3. 对项目的影响和潜在意义
- **性能提升显著**：Page-Table 跳过、FP8 后端切换、LongCat-Flash GEMM 等

## 详细提交记录

### [2f4f236](https://github.com/sgl-project/sglang/commit/2f4f2362fbada9a372fbf5d78a4498c03bd6420b)

- **作者**: Brayden Zhong
- **时间**: 2026-07-21T23:44:47Z
- **提交信息**: Delete sgl-kernel AOT `bmm_fp8`, use `flashinfer.bmm_fp8` (#31202)

Co-authored-by: root <root@sgl-b300-inference.datacrunch.io>

### [1b4cb6b](https://github.com/sgl-project/sglang/commit/1b4cb6b8c14944fbe3d7e02d4f8de6e8b465d971)

- **作者**: Alison Shao
- **时间**: 2026-07-21T23:41:17Z
- **提交信息**: Route /rerun-test for b200 multimodal tests to the b200 pool (#31928)

### [08cb081](https://github.com/sgl-project/sglang/commit/08cb081ed0bbb75d61233d343b52fb306801db74)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-21T23:20:14Z
- **提交信息**: [Perf] Skip page-table columns past kv length in DSA draft-extend metadata kernel (#31981)

### [4a55fdb](https://github.com/sgl-project/sglang/commit/4a55fdba0b7e5ac8e8dee0233064d34468b16a06)

- **作者**: Douglas Yang
- **时间**: 2026-07-21T22:55:36Z
- **提交信息**: docs(cookbook): re-benchmark DeepSeek-V4 on sglang 0.5.15 (#31363)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [9057db9](https://github.com/sgl-project/sglang/commit/9057db94175e58ce59a234c60aea167c436ca5c2)

- **作者**: Raghavendra Vedula
- **时间**: 2026-07-21T22:28:23Z
- **提交信息**: Gate Mamba slot-donation debug asserts behind SGLANG_MAMBA_DEBUG_ASSERTS (#31982)

### [becf252](https://github.com/sgl-project/sglang/commit/becf252e6c92be8dd51c119ff4152b48e3be3b7a)

- **作者**: JD
- **时间**: 2026-07-21T21:32:13Z
- **提交信息**: AutoWeightLoader support Sglang native models 1: demo  (#28671)

### [0eae942](https://github.com/sgl-project/sglang/commit/0eae9423d86ddf0c820dd47c97b97fb779467b91)

- **作者**: Brayden Zhong
- **时间**: 2026-07-21T21:09:01Z
- **提交信息**: Change the FP8 per-tensor GEMM backend on SM120 to cuBLAS (#31961)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>

### [cb324cc](https://github.com/sgl-project/sglang/commit/cb324cc958a143eeb9dfe1783bfa5fbe0f16ef65)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-21T21:03:00Z
- **提交信息**: Add wangfakang to CI_PERMISSIONS.json (#31980)

### [d03c8ce](https://github.com/sgl-project/sglang/commit/d03c8cee8090bdfa63f6476c6f7e150ad4244f50)

- **作者**: Hanming Lu
- **时间**: 2026-07-21T19:07:30Z
- **提交信息**: Negotiate PrefillDelayer only after KV-budget admission checks (#31835)

### [927979e](https://github.com/sgl-project/sglang/commit/927979e127a6a332b125c3afaa8857acd1763a96)

- **作者**: Hanming Lu
- **时间**: 2026-07-21T18:49:17Z
- **提交信息**: Fix pad-row top-k masking with custom_routing_function under DP attention (#31838)

### [9a6c960](https://github.com/sgl-project/sglang/commit/9a6c96083ffa40a998174048f5353e3099db1243)

- **作者**: Jimmy Shong
- **时间**: 2026-07-21T17:01:50Z
- **提交信息**: [Cookbook] Add Laguna-S-2.1 (#31918)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [57e5846](https://github.com/sgl-project/sglang/commit/57e5846b90f5950bf1712b811e9c3887a5a8fd35)

- **作者**: Yanbin Jiang
- **时间**: 2026-07-21T16:47:17Z
- **提交信息**: [LoRA] Guard TMA down path for LoRA hooks (#31608)

### [604b150](https://github.com/sgl-project/sglang/commit/604b1507d249c0b89a8a0137d22b214c6d919e12)

- **作者**: Ke Bao
- **时间**: 2026-07-21T15:06:11Z
- **提交信息**: Add Inkling to nightly test (#31939)

### [6f55de0](https://github.com/sgl-project/sglang/commit/6f55de0468397c4235be441e232f8b539fa7e526)

- **作者**: Zheng Wengang
- **时间**: 2026-07-21T14:36:11Z
- **提交信息**: [EPD] Make encoder register/unregister health-check robust (#31576)

Co-authored-by: siyu <liusy58@linux.alibaba.com>

### [8260ade](https://github.com/sgl-project/sglang/commit/8260ade61b8e72b289835813b290949b692d3879)

- **作者**: Артем Савкин
- **时间**: 2026-07-21T13:47:46Z
- **提交信息**: [Bugfix] Fix CUDA import on non-CUDA platforms (#31919)

### [075bd97](https://github.com/sgl-project/sglang/commit/075bd9795207efea9a3600847b7c31332aef26d9)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-21T12:44:52Z
- **提交信息**: [Benchmark] Remove obsolete auto-benchmark remnants (#31941)

### [0a06cc5](https://github.com/sgl-project/sglang/commit/0a06cc53170b843e62c4fe80ca5b90d9fd778cac)

- **作者**: Ke Bao
- **时间**: 2026-07-21T12:41:35Z
- **提交信息**: Fix extra_buffer_lazy guard bypass (#31942)

### [e4eea7c](https://github.com/sgl-project/sglang/commit/e4eea7ce2ffab90d6eef2e79cbb39e4d14577f7c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-21T12:05:17Z
- **提交信息**: Optimize LongCat-Flash router GEMM with the HPC-Ops bf16xfp32 kernel (#30247)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Halcyon <56064364+VAthree@users.noreply.github.com>

### [303896a](https://github.com/sgl-project/sglang/commit/303896a475c47f3acf6c283ad79933316171ba04)

- **作者**: qyb233
- **时间**: 2026-07-21T11:54:36Z
- **提交信息**: [Bugfix] Place empty Qwen encoder-DP embeddings on the communication device (#31663)

### [7c92575](https://github.com/sgl-project/sglang/commit/7c9257529f0d4140bfdcc1f38a4b7b46c35562cd)

- **作者**: YAMY
- **时间**: 2026-07-21T11:38:03Z
- **提交信息**: [Mamba] Support speculative decoding with extra_buffer_lazy (#30437)

### [1a53f23](https://github.com/sgl-project/sglang/commit/1a53f231d62d373cbc35ecbeaad727ff75834fe8)

- **作者**: Zhangheng
- **时间**: 2026-07-21T10:59:51Z
- **提交信息**: [HiCache]: Optimize hybrid/DSA L3 prefetch result sync and usable-prefix clamping (#31443)


Co-authored-by: AlejandroParedesLT <alejandroparedeslatorre@gmail.com>
Co-authored-by: Kevin Flansburg <kevin.flansburg@gmail.com>
Co-authored-by: Chao Shi <chao.shi@alibaba-inc.com>

### [df39a7b](https://github.com/sgl-project/sglang/commit/df39a7b0b630d091eabf6a790053fa0976404360)

- **作者**: nbarzilie
- **时间**: 2026-07-21T10:17:06Z
- **提交信息**: [CI][PD] Add NIXL disaggregation functional tests (#27894)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [2cf2e73](https://github.com/sgl-project/sglang/commit/2cf2e7377ff4d52a554bb41120c3d5b7e14c1207)

- **作者**: Ke Bao
- **时间**: 2026-07-21T10:07:43Z
- **提交信息**: Fix dropped tool calls when a stream delta carries several (#31860)

### [f369a82](https://github.com/sgl-project/sglang/commit/f369a820d48370f7f9c56f25fc04aa0e8f2ba0e0)

- **作者**: Chao Shi
- **时间**: 2026-07-21T09:54:06Z
- **提交信息**: [HiCache] Remove redundant parameters of build_xxx_stack and others (#31308)

Co-authored-by: Zhangheng <hzh0425@apache.org>

### [dcd9014](https://github.com/sgl-project/sglang/commit/dcd9014f1503c1d3ec07d6a4de8592dde3e6cc5e)

- **作者**: fxmarty-amd
- **时间**: 2026-07-21T09:50:23Z
- **提交信息**: [AMD][MXFP4] Reland "Online MXFP4 quantization 2/N - FP8 to MXFP4 requantization on AMD GPUs" (#28291)

Co-authored-by: Bowen Bao <bowenbao@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [696e8f8](https://github.com/sgl-project/sglang/commit/696e8f80d1cec93b3a020e00b5ff2ae2aa969f21)

- **作者**: Alison Shao
- **时间**: 2026-07-21T09:09:26Z
- **提交信息**: [CI] Graceful teardown in kl_mamba hicache tests to release pinned host pool (#31871)

### [66ea79d](https://github.com/sgl-project/sglang/commit/66ea79dc2e11dd8dca3fd328b7ad251ae61dd5e6)

- **作者**: Yuan Luo
- **时间**: 2026-07-21T08:57:10Z
- **提交信息**: Update FLA directory in CODEOWNERS (#31916)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [c0ed009](https://github.com/sgl-project/sglang/commit/c0ed009f5b566be023661bd4e93065b8b4b8b31f)

- **作者**: wenxuewuhd
- **时间**: 2026-07-21T08:09:34Z
- **提交信息**: [NPU] Fix LLaDA2 MoE OOM after the FRACTAL_NZ cast, re-enabling the NZ speedup (#31772)

### [429f6b6](https://github.com/sgl-project/sglang/commit/429f6b6d157a9d8013903c4e4260b027e7bf5386)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-21T07:03:43Z
- **提交信息**: Turn on breakable prefill cuda graph for dp attention by default (#31682)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1234
- **最后更新**: 2026-07-20T09:15:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86881
- **最后更新**: 2026-07-22T15:35:50Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 26
- **主要提交者**: Nicolò Lucchesi, Seiji Eicher, Roberto L. Castro

## AI分析总结

好的，我来分析 vllm-project/vllm 仓库昨日的 32 个提交记录，结合项目背景（“Easy, fast, and cheap LLM serving for everyone”）进行总结。

## 1. 主要更新类型

| 类型 | 数量 | 示例 |
|------|------|------|
| **Bug 修复** | 12+ | DFlash size、cutlass版本、Qwen3-VL M-RoPE、Spec Decode、DSA崩溃、Prefix-cache指标、MLA fallback、Cosmos3、Ovis2_5等 |
| **CI/测试增强** | 13 | 超时调整、新模型集成测试（Gemma-4、DeepSeek MTP、inkling）、ROCm CI修复、OOM修复、新硬件（B200）测试、编码器/管理器cudagraph测试 |
| **性能与加速** | 3 | TopK skip cudagraph/DP padding；Rust benchmark改用async HTTP；SYCL kernel路径（XPU） |
| **重构/清理** | 3 | KV-Cache布局重构（Mamba统一）；移除旧参数`max_num_partial_prefills`等；代码所有权新增 |
| **硬件支持** | 3 | ROCm AITER版本升级、ROCm FP8 MLA修复、XPU fuse_index_q |
| **文档** | 1 | XPU文档驱动链接修复 |
| **回滚** | 1 | 回退fp32 logits 上采样修改 |

## 2. 关键变更点及其与项目方向的关系

- **模型支持扩展**（与“easy, fast, cheap”方向一致）
  - 新增 DeepSeek MTP 并行加载测试、Gemma-4-E4B-it 集成测试、Cosmos3 Edge 修复——表明 vLLM 持续支持最新/最热模型，降低用户接入成本。
  - Qwen3-VL M-RoPE 修复（Transformers 后端及编译）——巩固多模态能力，满足更广泛使用场景。

- **硬件平台适配深化**（“cheap”意味着多硬件支持，降低部署成本）
  - ROCm 修复（FP8 注意力、AITER 升级）——让 AMD GPU（MI355等）用户获得稳定推理体验。
  - XPU（Intel）新增 DeepSeek-V4 的 SYCL kernel——扩展对 Intel 硬件的支持。
  - B200 测试 wire in——紧跟 NVIDIA 最新硬件。

- **性能与内存优化**（“fast”核心）
  - TopK 跳过 cudagraph/DP padding——可能带来小批量场景的延迟或吞吐提升。
  - Rust 基准工具改用异步 HTTP——提升 benchmark 自身性能。
  - 回退 fp32 logits 上采样（采样器）——表明团队谨慎权衡精度与性能，回退以避免回归。

- **代码质量与可维护性**（支撑“cheap”，降低维护成本）
  - KV-Cache 布局重构：标准化 Mamba cache，丢弃旧接口——为未来统一管理模式铺路。
  - 移除废弃参数`max_num_partial_prefills`——清理技术债务。
  - 增加 VLLMValidationError 统一验证错误处理——提升 API 健壮性。

- **CI/测试体系加固**（保障“easy”，用户信赖）
  - 大量 CI 修复、超时调整、OOM 规避——直接提高发行版稳定性和自动化测试可靠性。
  - 多节点测试修复（fork 方法兼容 Python 3.14）——前瞻性维护。

## 3. 对项目的影响和潜在意义

- **直接影响**：多个 bug 修复（DSA崩溃、Prefix-cache指标双计、MLA fallback、Cutlass版本升级兼容性、Spec Decode限制）能立即减少用户在实际部署中遇到的崩溃和性能异常。
- **稳定性提升**：CI 修复（尤其是 ROCm 上的顺序依赖失败、OOT embedding OOM、“The Rock” fork 方法）使得开发和发布流程更可靠。
- **新硬件/模型解锁**：DeepSeek-V4 XPU、Qwen3-VL 修复、Cosmos3 修复等降低了用户在新模型/新硬件上的适配门槛。
- **架构演进**：KV-Cache 布局重构是底层基础设施改善，为未来更高效的内存管理和多引擎统一打下基础。
- **技术债务减少**：清理旧参数、统一错误处理、升级 AITER 版本，有助于未来扩展和维护。

## 4. 值得关注的技术点

- **Flash Attention 缓存传播到 Ray workers** (adfbbc1): 表明 vLLM 的分布式推理中 flash attention 配置的传递需要显式处理，对多节点部署有影响。
- **MLA 回退处理** (7bb49be): 在 FA4 JIT warmup 期间处理 MLA fallback，体现团队对复杂注意力机制（Multi-Head Latent

## 详细提交记录

### [05781e2](https://github.com/vllm-project/vllm/commit/05781e21dd4af5ed042d4cc19e833a3ee333e92f)

- **作者**: stefankoncarevic
- **时间**: 2026-07-21T23:54:33Z
- **提交信息**: [ROCm][CI] Fix order-dependent failure in test_flash_attn_accepts_handled_fp8_variants (MI355) (#49329)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [85f638a](https://github.com/vllm-project/vllm/commit/85f638a2b8f9838275b911c44fb0c2abdf604476)

- **作者**: gnovack
- **时间**: 2026-07-21T22:20:30Z
- **提交信息**: skip cudagraph/DP padding in topk (#48979)

Signed-off-by: gnovack <novackgm@gmail.com>

### [08e5067](https://github.com/vllm-project/vllm/commit/08e50675615fc0b3e4e458645d8dd16cefb371bd)

- **作者**: Nick Hill
- **时间**: 2026-07-21T21:54:03Z
- **提交信息**: [CI] Bump timeout of `entrypoints-integration-api-server-openai-part-2` (#49359)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [a7d00ec](https://github.com/vllm-project/vllm/commit/a7d00ec051624e551ea822ec55d1113d117e47b7)

- **作者**: Michael Goin
- **时间**: 2026-07-21T21:42:52Z
- **提交信息**: [Bugfix] DFlash fc sized wrong when num_target_layers != num_hidden_layers (#48524)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [b8fb56d](https://github.com/vllm-project/vllm/commit/b8fb56d970a4fa2a8d668d7e09ee5c7fbb7b680b)

- **作者**: Michael Goin
- **时间**: 2026-07-21T20:51:04Z
- **提交信息**: [CI] Add gemma-4-E4B-it-assistant to CI gsm8k for GemmaMTP (#49243)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [96a7392](https://github.com/vllm-project/vllm/commit/96a739289e07530cd7d8fc03665746edae8177e7)

- **作者**: rongfu.leng
- **时间**: 2026-07-21T20:42:14Z
- **提交信息**: [Bugfix] fix cutalss version upgrade bug, need update MSG new commit (#49016)

Signed-off-by: lengrongfu <lenronfu@gmail.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [60d443f](https://github.com/vllm-project/vllm/commit/60d443f738bfc13001973d36445f022cba499721)

- **作者**: rasmith
- **时间**: 2026-07-21T20:40:29Z
- **提交信息**: [CI/Build][The Rock][BugFix] Use fork method in test_multiproc_executor_multi_node for py 3.14 compat and fix test_multiproc_executor_shutdown_cleanup  (#48655)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1dca300](https://github.com/vllm-project/vllm/commit/1dca300653e63db8d6d00b2073d97bd6d59d3fd7)

- **作者**: Nick Hill
- **时间**: 2026-07-21T19:41:16Z
- **提交信息**: [CI] Fix and wire encoder/manager cudagraph unit tests (#49339)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [fca252d](https://github.com/vllm-project/vllm/commit/fca252d59efdb627549e5677263c69709590c982)

- **作者**: Flora Feng
- **时间**: 2026-07-21T19:00:06Z
- **提交信息**: [CI][Bugfix] Reduce max_model_len in OOT embedding test to fix KV-cache OOM on small GPUs (#49351)

Signed-off-by: sfeng33 <4florafeng@gmail.com>

### [33178f9](https://github.com/vllm-project/vllm/commit/33178f90063e5eec7d3e2a6288f3ca43d39ae8d3)

- **作者**: Aritra Roy Gosthipaty
- **时间**: 2026-07-21T18:28:39Z
- **提交信息**: Fix Qwen3-VL M-RoPE on the Transformers modeling backend (grids + compile) (#49292)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [b2b8f67](https://github.com/vllm-project/vllm/commit/b2b8f679d0589f0c956f3e734cc70dab07b27b8a)

- **作者**: Evan Takahashi
- **时间**: 2026-07-21T17:53:37Z
- **提交信息**: [Bugfix][Spec Decode] Restrict embedding-width share guard to EAGLE drafts (#47953)

Signed-off-by: Evan Takahashi <evan10takahashi@gmail.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [de6ec29](https://github.com/vllm-project/vllm/commit/de6ec294ef0772673ade8fa3abf3f61f501880ae)

- **作者**: Nick Hill
- **时间**: 2026-07-21T17:28:13Z
- **提交信息**: [Bugfix] Fix DSA crash under breakable piecewise cudagraphs (#49302)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [61e10f0](https://github.com/vllm-project/vllm/commit/61e10f0116ef45ea8c77271a9285185af87b0406)

- **作者**: stefankoncarevic
- **时间**: 2026-07-21T17:19:45Z
- **提交信息**: [ROCm][CI] Fix AITER MLA fp8 decode metadata regression test (#48845)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [6e96891](https://github.com/vllm-project/vllm/commit/6e96891ba00d3d61a1eaa9c95bdd8d2663b183bd)

- **作者**: Fangzhou Ai
- **时间**: 2026-07-21T15:39:11Z
- **提交信息**: [ROCm] Bump AITER to v0.1.16.post5 (#48683)

Signed-off-by: Fangzhou Ai <fangzhouai@gmail.com>
Signed-off-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [47f1b47](https://github.com/vllm-project/vllm/commit/47f1b47a7396c5ba627001b2f7a1599258a6c856)

- **作者**: Michael Goin
- **时间**: 2026-07-21T15:30:42Z
- **提交信息**: Ci/add laguna xs gsm8k (#49241)

Signed-off-by: Joe Rowell <joerowell4@gmail.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Joe Rowell <joerowell4@gmail.com>

### [5aab491](https://github.com/vllm-project/vllm/commit/5aab491bc98fbc5ae83274b5906f342c747a8ced)

- **作者**: Nick Hill
- **时间**: 2026-07-21T14:43:20Z
- **提交信息**: [CI] Wire tests/models/inkling into a B200 job (#49325)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [5812e1a](https://github.com/vllm-project/vllm/commit/5812e1a66bc5909508c5e08674c43896f5d3401b)

- **作者**: Stefano Castagnetta
- **时间**: 2026-07-21T14:38:20Z
- **提交信息**: [Test] Add DeepSeek MTP parallel-load tests (#41653)

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [8950394](https://github.com/vllm-project/vllm/commit/8950394e0a40a781c61a9ef1f099ef847af03891)

- **作者**: Seiji Eicher
- **时间**: 2026-07-21T14:02:03Z
- **提交信息**: [Bugfix] Prefix-cache metrics double-counted when a KV connector defers requests (#48860)

Signed-off-by: Seiji Eicher <58963096+eicherseiji@users.noreply.github.com>
Signed-off-by: Seiji Eicher <seiji@anyscale.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Lixi Zhang <muxixibbb@gmail.com>
Co-authored-by: harjothkhara <harjoth.khara@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [7bb49be](https://github.com/vllm-project/vllm/commit/7bb49be4d1160257f4a27d798d4ccadf5699d292)

- **作者**: Roberto L. Castro
- **时间**: 2026-07-21T13:58:05Z
- **提交信息**: [Bugfix] Handle MLA fallback during FA4 JIT warmup (#49306)

### [c67650f](https://github.com/vllm-project/vllm/commit/c67650f04bc9241073130a7f8f245ce470bb69ac)

- **作者**: Avery Miao
- **时间**: 2026-07-21T13:22:34Z
- **提交信息**: [XPU][DeepSeekV4]Add DeepSeek-V4 fuse_index_q SYCL kernel path (#45991)

Signed-off-by: Avery Miao <avery.miao@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [f890e1d](https://github.com/vllm-project/vllm/commit/f890e1dbe2fe5deddd5417250b4e1e2db71e9314)

- **作者**: Ilya Markov
- **时间**: 2026-07-21T12:59:26Z
- **提交信息**: [BugFix] Set graph_pool_id before FULL CUDA graph capture in ModelRunner V2 (#48843)

Signed-off-by: Markov Ilya <markovilya19@gmail.com>
Co-authored-by: Markov Ilya <markovilya19@gmail.com>

### [040cbf9](https://github.com/vllm-project/vllm/commit/040cbf95cc05b14af8874ea980f3f4deb71b4708)

- **作者**: Umut Polat
- **时间**: 2026-07-21T11:38:20Z
- **提交信息**: [Misc] Use VLLMValidationError in chat completion tool and batch validators (#49214)

Signed-off-by: Umut Polat <52835619+umut-polat@users.noreply.github.com>

### [5b3762a](https://github.com/vllm-project/vllm/commit/5b3762a7f04a1939e58ae2dc33cf956576a01be1)

- **作者**: Sya
- **时间**: 2026-07-21T09:58:52Z
- **提交信息**: [Bugfix][CPU] Fix Clang OpenMP build on macOS (#49021)

Signed-off-by: markyangcc <mmdou3@163.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [4d30c51](https://github.com/vllm-project/vllm/commit/4d30c510ce36e692f385f92fa69a05939ac44a52)

- **作者**: bastefaniak
- **时间**: 2026-07-21T09:18:36Z
- **提交信息**: [bugfix] Fix Cosmos3 Edge checkpoint weights filtering, video loading, prompt expansion (#49190)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [6700813](https://github.com/vllm-project/vllm/commit/6700813f86552a2e0787989dd9f468fddcb88bac)

- **作者**: Lucas Wilkinson
- **时间**: 2026-07-21T09:16:15Z
- **提交信息**: [3/N][KV-Cache Layout Refactor] Standardize Mamba cache; drop `get_transfer_cache_regions` (#44456)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [eb44b3a](https://github.com/vllm-project/vllm/commit/eb44b3aaa40b134ffb9030c19671964c8d0602e3)

- **作者**: Bugen Zhao
- **时间**: 2026-07-21T08:53:57Z
- **提交信息**: [Rust][Benchmark] Use async HTTP clients (#49295)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [7a98c7a](https://github.com/vllm-project/vllm/commit/7a98c7a392222d0073e8e15bbfa05cf03d7d8fb6)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-21T08:52:52Z
- **提交信息**: [Misc] Remove old now unsupported `max_num_partial_prefills` and `max_long_partial_prefills` (#49244)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [0d9e606](https://github.com/vllm-project/vllm/commit/0d9e60619b4e2efac467eaa809ec7984e986bed9)

- **作者**: Lena Onyshchenko
- **时间**: 2026-07-21T08:45:41Z
- **提交信息**: [Misc][Docs] Fix XPU compute-runtime driver link version mismatch (#49299)

Signed-off-by: oonyshch <xonyshch@gmail.com>

### [1134545](https://github.com/vllm-project/vllm/commit/1134545b6f0064e5fa1459455d18b05d8ffaae1f)

- **作者**: vllm-agent
- **时间**: 2026-07-21T08:36:45Z
- **提交信息**: Revert "[Sampler] Stop upcasting logits to fp32 in apply_sampling_params" (#48641) (#49033)

Co-authored-by: vllm-agent <vllm-agent@users.noreply.github.com>

### [3e0c887](https://github.com/vllm-project/vllm/commit/3e0c8875118e14be7822b7aafa8fd83c80c5e3e7)

- **作者**: Miłosz Grunwald
- **时间**: 2026-07-21T08:09:20Z
- **提交信息**: [Bugfix] Fix Ovis2_5 special tokens for transformers v5 (#47298)

Signed-off-by: mgrunwal <milosz.grunwald@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [adfbbc1](https://github.com/vllm-project/vllm/commit/adfbbc10051fff393b3f6a3b0e96f8d6243c8cb9)

- **作者**: Stefan Kaestle
- **时间**: 2026-07-21T07:47:53Z
- **提交信息**: Propagate Flash Attention cache configuration to Ray workers (#49177)

Signed-off-by: Stefan Kaestle <skaestle@nvidia.com>

### [adc98f0](https://github.com/vllm-project/vllm/commit/adc98f04d01ed432d470532b8f7ca40d71417baa)

- **作者**: Roy Wang
- **时间**: 2026-07-21T07:44:24Z
- **提交信息**: [Misc] Add @esmeetu to codeowners for rust/src/bench (#49298)

Signed-off-by: esmeetu <jasonailu87@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-22
**监控日期**: 2026-07-21
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5652
- **最后更新**: 2026-07-22T14:36:40Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: SYLAR, Hongshaorou, akshatvishu

## AI分析总结

### 1. 主要更新类型
- **功能新增**：2个模型支持（Boogu图像系列、LingBot视频系列）。
- **Bug修复**：6个，覆盖扩散模型、量化、配置命名、音频处理、CI测试等问题。
- **重构/示例迁移**：1个（Wan2.2示例迁移至`--deploy-config`）。
- **性能基准更新**：1个（基于最近7天平均值调整基线）。

### 2. 关键变更点及其与项目整体方向的关系
- **新增多模态模型**：支持**Boogu-Image**（基础版+编辑版）和**LingBot Video**（稠密+MoE架构），直接呼应项目“omni-modality”定位，扩展了图像/视频推理能力。
- **修复扩散模型数据保留**：修复图像payload与推理元数据冲突问题，确保多模态输出完整性。
- **量化稳定性**：跳过未初始化scale的FP8 GEMM，避免空指针/错误结果，提升低精度推理可靠性。
- **配置文件修复**：纠正Cosmos3 edge配置键名，保证生成模型参数正确加载。
- **音频占位符修正**：修复MiniCPM-o 4.5音频处理的pool步骤，增强音频流支持。
- **重构示例部署**：将Wan2.2示例迁移至统一部署配置接口，降低用户配置复杂度。

### 3. 对项目的影响和潜在意义
- **模型生态扩大**：新增两个视觉模型系列（图像+视频），吸引更多垂直场景用户。
- **稳定性提升**：6个Bug修复覆盖主流模型（扩散、量化、音频），减少用户遇到的生产问题。
- **部署易用性**：示例迁移到`--deploy-config`统一了配置方式，降低学习成本。
- **性能基线标准化**：更新基线使性能测试更贴合实际平均负载，利于后续回归检测。

### 4. 值得关注的技术点
- **MoE架构视频模型支持**（LingBot Video）：项目首次加入混合专家模型，可能涉及分布式推理调度优化。
- **FP8量化尺度占用检查**：体现了对低精度计算中异常状态的防御性处理。
- **音频placeholder池步骤修复**：指向多模态流水线中跨模态token管理的复杂逻辑。

### 5. 基于项目背景的综合影响
- **强化“全能模态”服务能力**：提交持续覆盖图像、视频、音频、扩散等多种模态，符合README中“easy, fast, cheap omni-modality model serving”的愿景。
- **从实验到生产稳定性**：大量Bug修复表明项目正从功能开发转向稳定维护阶段，准备迎接更广泛的生产部署。
- **降低用户门槛**：通过重构示例和修复CI问题，减少开发者和运维人员的引入障碍，促进社区贡献。

## 详细提交记录

### [ee33954](https://github.com/vllm-project/vllm-omni/commit/ee33954dff27da317be597449a6c1b5a5df4052b)

- **作者**: Jae
- **时间**: 2026-07-21T18:58:56Z
- **提交信息**: [Model] Support Boogu/Boogu-Image-0.1-Base and Boogu/Boogu-Image-0.1-Edit (#4995)

Signed-off-by: zzehli <jaeli_ottawa@outlook.com>
Signed-off-by: jl <jaeli_ottawa@outlook.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [d34b917](https://github.com/vllm-project/vllm-omni/commit/d34b91722f372bc6c2888821849540c22b572edc)

- **作者**: akshatvishu
- **时间**: 2026-07-21T16:49:18Z
- **提交信息**: [BugFix][Diffusion] Preserve image payloads with reasoning metadata (#5238)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [9ca9800](https://github.com/vllm-project/vllm-omni/commit/9ca98009b2cadd35affb7f6a7befdc5b535bfe31)

- **作者**: wangyu
- **时间**: 2026-07-21T15:29:06Z
- **提交信息**: [Bugfix][CI] Recognize local_model in check-test-ci-coverage hook (#5275)

Signed-off-by: wangyu <410167048@qq.com>

### [7b5b399](https://github.com/vllm-project/vllm-omni/commit/7b5b399210dec4297954c3396b0b86062f8f837f)

- **作者**: wangyu
- **时间**: 2026-07-21T13:47:55Z
- **提交信息**: [CI] skip test_audio_in_video_default_loader_sampling_regression (#5248) (#5280)

Signed-off-by: wangyu <410167048@qq.com>

### [7924bee](https://github.com/vllm-project/vllm-omni/commit/7924beef84ff2846833f01b123e3c52f7ddaa1c6)

- **作者**: SYLAR
- **时间**: 2026-07-21T12:28:31Z
- **提交信息**: [Refactor] Migrate replica-DP Wan2.2 example to --deploy-config (#5267)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [0034eaa](https://github.com/vllm-project/vllm-omni/commit/0034eaa9c3f39d49019f04a1582e1d664b239a2c)

- **作者**: Alicia
- **时间**: 2026-07-21T12:26:22Z
- **提交信息**: Update perf baseline base on 7/5-7/11 7 days avg. (#5231)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [779466b](https://github.com/vllm-project/vllm-omni/commit/779466becb8f2c84efcfb1898358089db8fc767c)

- **作者**: SYLAR
- **时间**: 2026-07-21T10:11:16Z
- **提交信息**: [Bugfix][Quant] Skip quack FP8 GEMM when scales are unpopulated (#5262)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [5a6a93d](https://github.com/vllm-project/vllm-omni/commit/5a6a93dc5f36ddaec0cf0cf2945a362b3a1bc580)

- **作者**: wtz2333
- **时间**: 2026-07-21T09:27:29Z
- **提交信息**: [diffusion][model] Add LingBot Video dense and MoE support (#5035)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>
Signed-off-by: wtz2333 <2955110911@qq.com>
Co-authored-by: hsliuustc0106 <liuhongsheng4@huawei.com>

### [2f33df4](https://github.com/vllm-project/vllm-omni/commit/2f33df4678b2b13c70abd9ddffffc314908fb23a)

- **作者**: bastefaniak
- **时间**: 2026-07-21T07:56:31Z
- **提交信息**: [bugfix] Cosmos3 edge fix config use_k_norm_und_for_gen name (#5239)

Signed-off-by: Bartosz Stefaniak <bstefaniak@nvidia.com>

### [0576264](https://github.com/vllm-project/vllm-omni/commit/0576264dd1a063ec0c8601b45e2926f039ef1752)

- **作者**: Hongshaorou
- **时间**: 2026-07-21T07:44:05Z
- **提交信息**: [Bugfix] Fix MiniCPM-o 4.5 audio placeholder pool step (#5116)

Signed-off-by: a-kaa <siruhe666@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
