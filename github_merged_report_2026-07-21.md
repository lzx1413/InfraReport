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
- **星标数**: 2101
- **最后更新**: 2026-07-21T09:04:45Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: zangyu

## AI分析总结

### 1. 主要更新类型  
**功能新增**：支持 Qwen3-Omni-MoE 模型在 Ascend NPU 上的训练，并集成了融合 RoPE 优化。

### 2. 关键变更点及与项目方向的关系  
- **新增模型支持**：Qwen3-Omni-MoE 是一种多模态 MoE（Mixture of Experts）模型，符合 VeOmni “任意模态模型训练” 的定位，扩展了模型动物园（Recipe Zoo）。  
- **硬件适配**：针对华为 Ascend NPU 进行了适配，使框架不再局限于 GPU，体现了 “模型中心分布式训练” 对多样化硬件的兼容性。  
- **性能优化**：使用 fused RoPE（融合旋转位置编码），可减少计算开销，提升训练效率。

### 3. 对项目的影响和潜在意义  
- **扩大兼容性**：吸引使用 Ascend NPU 的用户群体，降低多模态模型训练对英伟达 GPU 的依赖。  
- **丰富生态**：整合 Qwen3-Omni-MoE 这类前沿模型，有助于 VeOmni 成为更全面的多模态训练工具。  
- **技术示范**：展示如何针对特定硬件（NPU）进行算子融合优化，为后续其他模型或硬件的适配提供参考。

### 4. 值得关注的技术点  
- **fused RoPE**：将 RoPE 计算融合到其他算子中，减少内存访问和核函数启动开销，是面向 Ascend NPU 的高效实现。  
- **MoE 训练支持**：Qwen3-Omni-MoE 的 MoE 架构对分布式通信和负载均衡有更高要求，该提交可能隐含了相关适配。

### 5. 对项目发展的影响（结合 README）  
- 符合 VeOmni “Scaling Any Modality Model Training” 的目标：新增模型和硬件都扩展了 “任意” 的边界。  
- 强化 “Model-Centric Distributed Recipe Zoo” 概念：为特定模型（Qwen3-Omni）提供了经过调优的配方（含 fused RoPE），使用户可直接复用。  
- 提升社区影响力：支持国产 NPU 和热门模型（Qwen 系列），有助于吸引更多开发者贡献和采用。

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
- **星标数**: 2516
- **最后更新**: 2026-07-21T12:40:40Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

根据提交记录和项目背景（LightX2V 轻量级视频生成推理框架），昨日更新要点总结如下：

### 1. 主要更新类型
- **功能新增**：为模型 `hidream-o1` 添加了 `SENSITIVE_LAYER_DTYPE` 配置支持。

### 2. 关键变更点与项目方向的关系
- **变更点**：新增 `SENSITIVE_LAYER_DTYPE` 参数，允许对 `hidream-o1` 模型中的敏感层（可能影响生成质量的关键层）指定独立的数据类型（如 float32 而非默认的 float16）。
- **与项目方向的关系**：LightX2V 作为轻量级推理框架，强调性能与质量的平衡。该提交通过细粒度的精度控制，在不显著增加显存/计算开销的前提下，提升了特定模型在关键层的推理精度，符合框架“灵活优化视频生成模型”的定位。

### 3. 对项目的影响和潜在意义
- **影响**：修复或缓解了 `hidream-o1` 在低精度推理下可能出现的质量退化问题，为该模型的部署提供了更稳健的默认配置。
- **潜在意义**：为后续更多模型引入“混合精度关键层”机制提供模板，增强框架对不同模型特性的适配能力，降低用户手动调试精度的门槛。

### 4. 值得关注的技术点
- **SENSITIVE_LAYER_DTYPE**：一种按层混合精度策略，仅对模型中对量化/低精度敏感的层（如注意力、时间模块）保持高精度，其余层仍使用低精度以节省资源。这比全局统一精度更精细，比逐层手动设置更易用。

### 5. 对项目发展的影响
- **丰富模型支持**：针对 `hidream-o1` 这一具体模型做了性能与质量的优化，体现了框架对主流/新兴视频生成模型的跟进。
- **提升框架成熟度**：引入敏感层精度配置，表明项目从“通用推理”向“模型自适应优化”演进，为后续支持更多文生视频、图生视频模型打下基础。

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
- **最后更新**: 2026-07-21T12:10:41Z

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
- **星标数**: 5994
- **最后更新**: 2026-07-21T22:31:07Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 9
- **主要提交者**: Igor Shovkun, Guoming Zhang, yichengj

## AI分析总结

根据你提供的9个提交记录，以下是针对`flashinfer-ai/flashinfer`仓库昨日更新的分析总结，结合项目“高性能GPU推理内核”的定位，梳理变更的要点和意义。

---

### 1. 主要更新类型

| 类型 | 数量 | 涉及的提交 |
|------|------|------------|
| **功能新增** | 3 | #4072（可选y_out）、#3975（Mamba checkpointing双内核+环形缓存）、#4040（SwiGLU+NVFP4融合量化） |
| **性能优化** | 3 | #4029（mm_fp4 autotune磁盘缓存+并行编译）、#4001（KDA解码统一单warp内核）、#4073（清理无用arch编译产物） |
| **Bug修复** | 1 | #4004（autotuner跨runner误用调优计划） |
| **文档/流程改进** | 2 | #3790（代码审查指南）、#4058（修复MSA/GDN文档缺失） |

所有更新均服务于**提升推理吞吐、降低延迟、减少显存占用**的核心项目目标。

---

### 2. 关键变更点及其与项目方向的关系

- **#4072（add_rmsnorm_fp4quant增补y_out）**  
  允许一次内核调用同时输出归一化结果和FP4量化结果，消除MoE层中路由器与专家分支的重复计算。直接提升Qwen3等模型在B200上的解码性能（单MoE层延迟从8.4µs降至3.1µs）。属于**融合算子优化**方向，减少内核启动次数和显存访问。

- **#4040（SwiGLU+NVFP4

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
- **星标数**: 3865
- **最后更新**: 2026-07-21T15:43:36Z

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
- **星标数**: 34125
- **最后更新**: 2026-07-21T21:12:55Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Sayak Paul, Álvaro Somoza, Linoy Tsaban

## AI分析总结

好的，以下是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结，结合项目背景（一个多模态扩散模型工具库，原本支持 PyTorch、Flax、JAX 等后端）进行解读。

---

### 1. 主要更新类型

- **Bug 修复**：2 个  
  - 修复 DreamBooth LoRA 训练中的纵横比分桶问题（含字幕丢弃、即时分桶）  
  - 修复模块化 Diffusers 中 group offload 的设备不匹配错误  
- **重构与清理**：2 个  
  - 将注意力处理器测试从原有框架迁移至 pytest（测试现代化）  
  - **彻底移除 JAX/Flax 支持**（删除模型、调度器、Pipeline、加载工具、文档及 CI 配置）

### 2. 关键变更点及其与项目整体方向的关系

| 变更 | 与项目方向的关系 |
|------|------------------|
| **移除 JAX/Flax**（提交 `80bfe77`） | 项目此前已开启“模块化 Diffusers”重构，核心是统一 PyTorch 为唯一后端。删除 Flax 代码极大减少维护负担，让团队聚焦 PyTorch 生态，符合官方此前预告的简化策略。 |
| **修复 group offload 设备不匹配**（`ba66c64`） | 模块化重构中引入的 offload 机制对模型在有限显存下运行至关重要，此修复增强了稳定性。 |
| **修复 DreamBooth LoRA 纵横比分桶**（`2919c50`） | 提升训练脚本在非正方形图像上的保真度与性能，对高级用户（如自定义微调）尤为重要。 |
| **测试迁移到 pytest**（`58a0c4d`） | 测试基础架构现代化，便于并行执行、参数化测试，提高质量保证效率。 |

### 3. 对项目的影响和潜在意义

- **显著降低代码复杂度**：Flax 相关代码曾占很大比例，删除后仓库更轻量，新贡献者上手门槛降低。
- **提升模块化稳定性**：group offload 修复是模块化架构从“原型”走向“生产可用”的关键步骤。
- **训练脚本健壮性增强**：LoRA 分桶修复影响面广（DreamBooth、SDXL 等），可减少用户因宽高比异常导致的训练失败。
- **测试基础设施升级**：pytest 迁移为未来 GPT-4 等自动化测试生成、并行测试打下基础。

### 4. 值得关注的技术点

- **Flax 兼容性保留策略**：虽然完全删除 Flax 代码，但依然保留了 `*.msgpack` 文件忽略下载的机制，以及从旧 `model_index.json` 中自动剥离 Flax 类名的兼容层（后一步在最终提交中实际移除），体现了谨慎的向前兼容思路。
- **“即时分桶”（on-the-fly buckets）**：修复中提到的功能，允许在训练过程中动态计算最佳纵横比分桶，而非预先固定，可提升数据利用率。
- **Group offload 设备不匹配**：模块化设计中不同子模型可能被分配到不同设备（CPU/GPU），此修复确保了 offload 时的设备一致性。

### 5. 基于项目背景，这些提交如何影响项目发展

- **战略方向明确**：移除 JAX/Flax 是 HuggingFace 对 diffusers 路线图的最终确认——聚焦 PyTorch，强化模块化架构，让库更轻量、更易维护。
- **社区影响**：旧用户可能需要调整基于 Flax 的 Pipeline，但受益于更快的迭代速度和更少的跨后端 Bug。
- **后续开发重点**：预计将全面转向模块化 Pipeline 设计，并可能引入更多 PyTorch 原生优化（如 `torch.compile` 适配）。测试迁移和训练修复表明质量保障和用户体验仍在同步提升。

> 总结：昨日提交可视为 **“彻底告别多后端时代，全面拥抱 PyTorch 模块化架构”** 的里程碑。

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
- **星标数**: 12728
- **最后更新**: 2026-07-21T19:23:12Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 3
- **主要提交者**: Hz_Zhang, MaskYuan(SII), Zhongjie Duan

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **Bug修复**（3个）：修复float8量化缩放范围、Wan模型批处理广播错误、序列并行工具导出遗漏
- **文档优化**（1个）：添加下载提示，提升用户体验
- **性能优化**（1个）：acestep低显存补丁，减少显存占用
- **版本发布**（1个）：更新至v2.0.18

#### 2. 关键变更点与项目方向关联
- **修复float8 E4M3FNZ缩放范围**：直接提升对低精度推理的稳定性，符合项目”降低显存、提升速度“的核心理念。
- **修复Wan模型批处理广播**：解决batch size >1时Head modulation的兼容性问题，增强了高吞吐场景的可靠性，与项目支持多模型、大规模生成的目标一致。
- **重导出序列并行工具**：完善与xfuser的集成，利于分布式推理的调用，强化了并行计算能力。
- **acestep低显存补丁**：专门优化的采样器低显存模式，进一步降低门槛，让更多用户能在有限资源下运行。

#### 3. 对项目的影响与潜在意义
- **稳定性提升**：quantization和模型层的bug修复降低了推理崩溃风险，尤其对生产级使用至关重要。
- **兼容性增强**：Wan模型批处理修复意味着可支持多张同时生成，提升效率。序列并行导出则让高级用户更方便部署大规模集群。
- **用户友好度**：下载提示和版本号更新降低了新手上手成本，维持了清晰的发布节奏。
- **资源优化**：acestep低显存补丁直接扩大硬件适用范围（如消费级显卡），增强项目竞争力。

#### 4. 值得关注的技术点
- **Float8 E4M3FNZ**：一种8-bit浮点格式，缩放范围修复体现了对混合精度训练的精细化支持。
- **Head modulation广播机制**：Wan模型中的特定注意力调制，跨批次广播的修复涉及张量运算维度对齐，属于深度学习工程典型陷阱。
- **Sequence Parallelism**：与xfuser库的集成，表明项目正在向长序列/视频生成场景的分布式推理迈进。
- **acestep低显存**：可能涉及梯度检查点、激活重计算等技术，虽未开源细节，但暗示项目持续优化内存管理。

#### 5. 结合项目背景的分析（如何影响发展）
- **强化低资源友好定位**：README强调“低显存”（如Flash Attention、DreamBooth低显存优化），本次acestep补丁和量化修复直接巩固了这一卖点。
- **推进多模型生态**：Wan模型修复表明项目已整合更多先进架构（如WanV2、WanV2.1），bug修复保障了这些新模型的可信度，吸引开发者采用。
- **提升工业级部署能力**：分布式工具导出和版本迭代表明项目正从研究工具向可落地的推理引擎演进，符合modelscope生态的工程化目标。
- **保持活跃维护**：单日6次提交且涵盖多维度，体现社区活跃度与响应速度，利于用户信心建立。

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
- **星标数**: 30590
- **最后更新**: 2026-07-21T23:27:18Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 22
- **主要提交者**: Liangsheng Yin, Raghavendra Vedula, Hanming Lu

## AI分析总结

好的，以下是基于 `sgl-project/sglang` 仓库昨日提交记录的分析总结，结合项目背景（高性能 LLM 推理与服务引擎）进行解读。

### 1. 主要更新类型

- **性能优化**：约 30% 的提交，涉及 DSA、FP8、HPC-Ops 内核、HiCache 等多处加速。
- **Bug 修复**：约 25%，包括 CUDA 导入、工具调用丢失、Encoder-DP 通信设备、内存泄漏等问题。
- **功能新增**：约 20%，如 AutoWeightLoader 支持原生模型、Mamba 支持 speculative decoding、Breakable Prefill CUDA Graph 默认开启、新模型 cookbook 等。
- **CI/测试**：约 15%，包括 NIXL 分解测试、Nightly 测试扩展、测试清理及优雅退出。
- **文档/配置**：约 10%，如 cookbook 重新评测 DeepSeek-V4、CODEOWNERS 更新、CI 权限更新。

### 2. 关键变更点与项目方向关系

| 变更点 | 与项目方向的关系 |
|--------|----------------|
| **FP8 per-tensor GEMM 在 SM120 上切换为 cuBLAS** | 提升 NVIDIA 新架构（SM120）计算效率，契合“多代GPU优化”目标 |
| **DSA draft-extend 元数据 kernel 跳过超过 kv 长度的 page-table 列** | 优化推测解码（draft-extend）场景的内存访问，提升吞吐 |
| **LongCat-Flash router GEMM 使用 HPC-Ops bf16xfp32 kernel** | 对大模型路由计算加速，适用于 Mixture-of-Experts (MoE) 场景 |
| **AutoWeightLoader 支持 Sglang 原生模型** | 简化模型加载流程，增强易用性，推动模型生态发展 |
| **Mamba 支持 speculative decoding + extra_buffer_lazy** | 扩展 Mamba 模型推理策略，提升解码效率 |
| **Breakable Prefill CUDA Graph 对 DP

## 详细提交记录

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
- **星标数**: 86819
- **最后更新**: 2026-07-21T23:21:29Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 26
- **主要提交者**: gnovack, Bugen Zhao, Fangzhou Ai

## AI分析总结

以下是基于 vllm-project/vllm 仓库的提交记录（昨日更新）的分析总结，结合项目背景（易用、快速、低成本的 LLM 服务）进行梳理。

---

### 1. 主要更新类型
- **Bug 修复**（约占一半）：涵盖 GPU 计算、模型兼容、缓存逻辑、多节点执行等多个方面。
- **CI/测试改进**：新增或修正测试用例、调整超时、适配新硬件（如 ROCm、XPU、Gemma 新模型）。
- **性能优化**：跳过不必要的 CUDA graph 填充、传播 Flash Attention 缓存配置给 Ray workers、Rust benchmark 改用异步 HTTP 客户端。
- **重构与清理**：KV-Cache 布局标准化（第 3 阶段）、废弃旧参数、删除冗余代码。
- **文档与杂项**：修复 XPU 驱动链接文档、更新 codeowners 等。

### 2. 关键变更点与项目方向的关系
- **纠正深层 Bug**（如 `DFlash fc sized wrong`、`Prefix-cache metrics double-counted`、`DSA crash under breakable piecewise cudagraphs`）→ 提升稳定性和指标准确性，符合“可靠服务”目标。
- **优化 CUDA Graph 与推理效率**（如 `skip cudagraph/DP padding in topk`、`Propagate Flash Attention cache to Ray workers`）→ 减少延迟、增加吞吐，实现“fast”承诺。
- **扩展模型支持**（如 Qwen3-VL、Cosmos3 Edge、Ovis2_5、DeepSeek-V4）→ 覆盖更多开源模型，降低用户迁移成本，体现“easy”。
- **加强多硬件适配**（ROCm AITER 升级、XPU SYCL 内核、CPU macOS 构建修复）→ 降低基础设施成本（cheap），扩大用户群。
- **CI 测试加固**（Gemma-4、Laguna xs、B200 job、DeepSeek MTP 并行加载测试）→ 防止退化，保证模型在新硬件上正常工作。

### 3. 对项目的影响与潜在意义
- **修复关键指标 double-count 问题**：`Prefix-cache metrics` 的 Bug 修复可避免错误报告，有助于运维和成本核算。
- **Ray 分布式推理改进**：`Flash Attention cache 配置传播` 能让多 GPU 或跨节点推理更高效，提升集群扩展性。
- **消除 KVCache 布局旧逻辑**：重构（`drop get_transfer_cache_regions`）为后续更灵活的缓存管理

## 详细提交记录

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
- **星标数**: 5644
- **最后更新**: 2026-07-21T19:09:00Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 8
- **主要提交者**: Alicia, Hongshaorou, SYLAR

## AI分析总结

## 昨日更新要点总结

### 1. 主要更新类型
- **功能新增**（2个）：增加对新图像模型（Boogu系列）和视频模型（LingBot Video）的支持  
- **Bug修复**（5个）：涉及扩散模型、量化、配置、音频占位符等问题的修复  
- **重构**（1个）：迁移示例到新的部署配置机制  
- **CI/测试**（2个）：修复CI hook、跳过有回归的测试、更新性能基线

### 2. 关键变更点与项目方向的关系
- **扩展多模态模型生态**：新增`Boogu-Image-0.1-Base/Edit`和`LingBot Video dense/MoE`支持，直接契合项目“omni-modality model serving”的定位，丰富了可服务的图像和视频模型种类。  
- **提升稳定性与正确性**：修复扩散模型中保留图像负载与推理元数据的问题、MiniCPM-o音频处理逻辑、Cosmos3配置名等，确保多模态推理的正确性和鲁棒性。  
- **优化部署与运维**：将Wan2.2示例迁移到`--deploy-config`，简化部署配置；更新性能基线、跳过已知回归测试，提升CI准确性和开发效率。  
- **量化与性能**：修复Quack FP8 GEMM跳过未填充scale的bug，避免量化推理异常，保障低精度计算的可靠性。

### 3. 对项目的影响和潜在意义
- **模型覆盖面更全**：Boogu和LingBot的加入使项目在图像生成/编辑和视频生成场景中更具竞争力，吸引更广泛的用户。  
- **生产环境可用性提升**：多个Bug修复（尤其扩散、量化、部署配置）减少了线上故障风险，为生产级部署奠定基础。  
- **开发效率改进**：CI跳过回归测试、修复覆盖率hook，减少无用告警，加速开发者迭代。  
- **性能基准透明化**：定期更新性能基线有助于团队追踪性能变化，方便用户评估模型服务效果。

### 4. 值得关注的技术点
- **扩散模型推理元数据保留**：`#5238`修复确保图像负载同时携带副作用信息，可能影响后续多轮生成或条件控制。  
- **FP8 GEMM条件跳过**：`#5262`避免在未填充scale时执行GEMM，是量化推理中常见的防御性设计。  
- **配置迁移模式**：`--deploy-config`的引入可能成为未来所有示例的统一部署方式，降低用户学习成本。  
- **视频模型MoE支持**：LingBot Video同时支持密集和MoE架构，展示了项目在视频生成领域对稀疏模型的支持。

### 5. 结合项目背景（omni-modality服务）的发展影响
- **强化“全模态”能力**：已有图像、视频、音频模型支持，本次更新进一步补全视频（LingBot）和图像（Boogu

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
