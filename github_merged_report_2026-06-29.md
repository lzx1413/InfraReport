# GitHub Stars 合并报告 - 2026-06-29

**合并日期**: 2026-06-30
**监控日期**: 2026-06-29
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


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2049
- **最后更新**: 2026-06-29T14:19:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2448
- **最后更新**: 2026-06-29T21:14:28Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: qinxinyi, Chengtao Lv

## AI分析总结

### 昨日更新总结（基于 `ModelTC/LightX2V` 仓库）

---

#### 1. 主要更新类型
- **功能新增**： `Sparse` (#1195) —— 引入稀疏化机制（可能指稀疏注意力、稀疏激活或模型剪枝等）
- **Bug修复 + 功能增强**： `Fix/s2v sekotalk only` (#1194) —— 修复 `sekotalk` 相关功能并支持 1080p 高清分辨率

---

#### 2. 关键变更点及其与项目方向的关系
- **`Sparse` 提交**：  
  - 在轻量视频生成推理框架中加入稀疏计算，直接对应项目目标“轻量化”与“高效推理”。稀疏化可减少计算量、降低显存占用，是提升视频生成速度的关键技术之一。
- **`Fix/s2v sekotalk only` 提交**：  
  - 专门修复并增强 `sekotalk`（推测为一种视频生成管线或模型）的稳定性，并扩展其输出分辨率至 1080p。这提升了框架对高清视频生成的支持，扩大应用场景。

---

#### 3. 对项目的影响和潜在意义
- **性能提升**：稀疏化有望在不影响生成质量的前提下显著加速推理，使框架更适合实时或端侧部署。
- **能力上限提高**：1080p 视频生成的支持填补了此前可能欠缺的高清能力，增强了与主流视频生成模型的兼容性。
- **稳定性增强**：修复 `sekotalk` 的专属问题，减少特定场景下崩溃或错误，使用户体验更可靠。

---

#### 4. 值得关注的技术点
- **稀疏化实现**：需关注其具体形式（如稀疏注意力、结构剪枝、激活稀疏化）以及是否兼容现有模型结构。稀疏化通常需要适配算子和量化策略。
- **1080p 分辨率适配**：修复可能涉及内存管理、张量维度调整、算子优化等，对长视频/高分辨率生成有参考价值。

---

#### 5. 基于 README 背景的项目发展影响
- 项目定位为**轻量视频生成推理框架**，核心矛盾是**高质量生成 vs 低资源消耗**。`Sparse` 提交直接优化后者，`Fix/s2v sekotalk only` 则提升前者（质量与分辨率）。
- 两个提交共同推动框架从“可用”向“高效、高清”演进，增强了在边缘设备或成本敏感场景中的竞争力。
- 未来可能继续围绕稀疏化、量化、蒸馏等技术进行迭代，以支持更大规模视频生成模型。

## 详细提交记录

### [bf75223](https://github.com/ModelTC/LightX2V/commit/bf75223a8ed65fa1b0c791c7680cbd6fc27b8348)

- **作者**: Chengtao Lv
- **时间**: 2026-06-29T12:54:32Z
- **提交信息**: Sparse (#1195)

### [09f6471](https://github.com/ModelTC/LightX2V/commit/09f6471d147fadb8988ae61bd0a09ad60ae6333d)

- **作者**: qinxinyi
- **时间**: 2026-06-29T11:47:55Z
- **提交信息**: Fix/s2v sekotalk only (#1194)

support 1080p sekotalk

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2150
- **最后更新**: 2026-06-29T08:01:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5874
- **最后更新**: 2026-06-29T15:56:43Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: lunarz-dev, Jiahan Chang (Cyrus)

## AI分析总结

## 昨日更新要点总结

### 1. 主要更新类型
- **Bug修复**：修复 benchmark 代码中两个独立错误（`fused_dit_layernorm` 返回值缺失、列名不匹配，以及 FP8 量化参考实现的 scale 方向错误）。
- **性能优化**：显著优化 TRTLLM-Gen 的 MoE 路由内核（降低寄存器压力、减少寄存器溢出）。
- **功能增强**：为 MoE 路由添加多尺寸模板化内核（256/512/1024 线程块），并扩展了对非 2 的幂次专家数的支持。

### 2. 关键变更点
- **Benchmark 修复**：
  - 使 `fused_dit_layernorm` 基准测试正确返回结果（`return res`）并使用规范列名（`median_time`/`std_time`/`tflops`/`tb_per_sec`）。
  - 修正 `rmsnorm_quant`/`fused_add_rmsnorm_quant` 的参考实现：scale 应作为反量化因子（`value / scale`）而非乘法，并在 fp32 中执行 residual 相加以匹配 CuTe 内核。
- **MoE 路由优化**：
  - 新增集群路由内核（支持 256/512/1024 线程块），保留默认内核路径以保持兼容。
  - 改进路由块大小启发式算法，同时应用于集群和直方图得分路由路径。
  - 扩展路由层级覆盖，支持非 2 的幂专家数。

### 3. 对项目的影响
- **Benchmark 可靠性提升**：修复使基准测试可正常输出指标，避免因错误配置导致的性能误判，保障后续优化工作的数据可信度。
- **MoE 推理加速**：在专家数 E=1024/2048、token 数较少时获得 **1.5x~12x** 加速比，高专家路由场景下性能提升尤为突出（如 `softmax_sum` 在 E=1024、K=32、tokens=512 时加速 12.4x）。这将直接增强 FlashInfer 在 MoE 模型（如 Mixtral）推理中的竞争力。
- **兼容性扩展**：

## 详细提交记录

### [eb79c53](https://github.com/flashinfer-ai/flashinfer/commit/eb79c537b22bc42786ea369827736cff2f615b74)

- **作者**: lunarz-dev
- **时间**: 2026-06-29T15:56:13Z
- **提交信息**: fix(bench): make fused_dit_layernorm and FP8 quant refcheck work correctly (#3758)

## Problem

Two independent bugs in norm benchmark routines.

## Fix 1 — fused_dit_layernorm: missing `return res` + wrong column
names

- `testFusedDitLayernorm` returned `None` instead of `res`, crashing the
harness with `TypeError: 'NoneType' object is not iterable` whenever
`--output_path` is set.
- Result dict used `median_ms`/`std_ms` — not in `full_output_columns`,
so they were silently dropped and perf columns came out empty.

Fix: add `return res`; write canonical columns
`median_time`/`std_time`/`tflops`/`tb_per_sec` (`tflops=0.0`, matching
existing print call).

## Fix 2 — rmsnorm_quant / fused_add_rmsnorm_quant: FP8 refcheck
mismatch

Reference used `rmsnorm_output * scale` but the CuTe kernel treats
`scale` as a dequant factor → correct form is `value / scale`.

Also: residual add in `fused_add_rmsnorm_quant` now done in fp32 to
match the CuTe kernel and unit-test reference.

## Testing

Verified on B200 with `--refcheck` for
`rmsnorm_quant`,`fused_add_rmsnorm_quant`, and `fused_dit_layernorm`..

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
* Corrected quantized normalization reference calculations so results
are now computed consistently.
* Fixed the fused normalization reference path to use a single, more
accurate residual combination before quantization.
* Updated benchmark result fields to use clearer time-based labels and
ensure results are returned properly.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [2594b95](https://github.com/flashinfer-ai/flashinfer/commit/2594b958fa0f2e24bc1a4dc15921571f0761744d)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-06-29T09:28:29Z
- **提交信息**: [feat] Optimize TRTLLMGEN MoE routing (#3751)

<!-- .github/pull_request_template.md -->

## 📌 Description

Optimize TRTLLM-Gen MoE routing to reduce register pressure and avoid
heavy spilling in high-expert routing cases.

- Add templated cluster routing kernels for 256/512/1024 thread block
sizes while preserving the original default kernel path.
- Apply the updated routing block-size heuristic to cluster and
histogram-score routing paths.
- Extend the routing tier coverage for non-power-of-two expert counts.

## Perf Benchmark
### noop_softmax


| E | K | tokens | baseline ms | opt ms | speedup |
|---:|---:|---:|---:|---:|---:|
| 256 | 8 | 8 | 0.009216 | 0.009184 | 1.00x |
| 256 | 8 | 16 | 0.009280 | 0.009440 | 0.98x |
| 256 | 8 | 32 | 0.011264 | 0.009248 | 1.22x |
| 256 | 8 | 64 | 0.012832 | 0.009248 | 1.39x |
| 256 | 8 | 128 | 0.012800 | 0.010784 | 1.19x |
| 256 | 8 | 256 | 0.012832 | 0.013312 | 0.96x |
| 256 | 8 | 512 | 0.014208 | 0.014368 | 0.99x |
| 256 | 8 | 1024 | 0.014400 | 0.014336 | 1.00x |
| 256 | 8 | 2048 | 0.015744 | 0.016288 | 0.97x |
| 256 | 8 | 4096 | 0.018336 | 0.018336 | 1.00x |
| 256 | 8 | 8192 | 0.020512 | 0.020448 | 1.00x |
| 512 | 8 | 8 | 0.009312 | 0.009184 | 1.01x |
| 512 | 8 | 16 | 0.011168 | 0.009248 | 1.21x |
| 512 | 8 | 32 | 0.014720 | 0.009408 | 1.56x |
| 512 | 8 | 64 | 0.015392 | 0.011296 | 1.36x |
| 512 | 8 | 128 | 0.015424 | 0.011296 | 1.37x |
| 512 | 8 | 256 | 0.017376 | 0.015744 | 1.10x |
| 512 | 8 | 512 | 0.018432 | 0.016576 | 1.11x |
| 512 | 8 | 1024 | 0.018496 | 0.017920 | 1.03x |
| 512 | 8 | 2048 | 0.021696 | 0.018464 | 1.18x |
| 512 | 8 | 4096 | 0.024544 | 0.020640 | 1.19x |
| 512 | 8 | 8192 | 0.026624 | 0.024544 | 1.08x |
| 512 | 10 | 8 | 0.009376 | 0.009280 | 1.01x |
| 512 | 10 | 16 | 0.011328 | 0.009312 | 1.22x |
| 512 | 10 | 32 | 0.015392 | 0.011232 | 1.37x |
| 512 | 10 | 64 | 0.015392 | 0.011200 | 1.37x |
| 512 | 10 | 128 | 0.017440 | 0.013088 | 1.33x |
| 512 | 10 | 256 | 0.017408 | 0.017376 | 1.00x |
| 512 | 10 | 512 | 0.018432 | 0.016544 | 1.11x |
| 512 | 10 | 1024 | 0.018496 | 0.018080 | 1.02x |
| 512 | 10 | 2048 | 0.022528 | 0.018496 | 1.22x |
| 512 | 10 | 4096 | 0.024704 | 0.022368 | 1.10x |
| 512 | 10 | 8192 | 0.028480 | 0.024768 | 1.15x |
| 1024 | 32 | 8 | 0.029408 | 0.015328 | 1.92x |
| 1024 | 32 | 16 | 0.043872 | 0.015424 | 2.84x |
| 1024 | 32 | 32 | 0.078688 | 0.017408 | 4.52x |
| 1024 | 32 | 64 | 0.080608 | 0.017472 | 4.61x |
| 1024 | 32 | 128 | 0.080960 | 0.021472 | 3.77x |
| 1024 | 32 | 256 | 0.082624 | 0.031552 | 2.62x |
| 1024 | 32 | 512 | 0.097952 | 0.020608 | 4.75x |
| 1024 | 32 | 1024 | 0.100224 | 0.022464 | 4.46x |
| 1024 | 32 | 2048 | 0.100928 | 0.026688 | 3.78x |
| 1024 | 32 | 4096 | 0.112736 | 0.037312 | 3.02x |
| 1024 | 32 | 8192 | 0.183776 | 0.053760 | 3.42x |
| 2048 | 32 | 8 | 0.031264 | 0.029728 | 1.05x |
| 2048 | 32 | 16 | 0.046112 | 0.031456 | 1.47x |
| 2048 | 32 | 32 | 0.080608 | 0.033312 | 2.42x |
| 2048 | 32 | 64 | 0.082784 | 0.035584 | 2.33x |
| 2048 | 32 | 128 | 0.084448 | 0.037344 | 2.26x |
| 2048 | 32 | 256 | 0.084704 | 0.076544 | 1.11x |
| 2048 | 32 | 512 | 0.109440 | 0.037664 | 2.91x |
| 2048 | 32 | 1024 | 0.111456 | 0.037664 | 2.96x |
| 2048 | 32 | 2048 | 0.111776 | 0.047872 | 2.33x |
| 2048 | 32 | 4096 | 0.123488 | 0.068512 | 1.80x |
| 2048 | 32 | 8192 | 0.193216 | 0.101152 | 1.91x |

### softmax_sum

| E | K | tokens | baseline ms | opt ms | speedup |
|---:|---:|---:|---:|---:|---:|
| 256 | 8 | 8 | 0.009248 | 0.009216 | 1.00x |
| 256 | 8 | 16 | 0.011264 | 0.011232 | 1.00x |
| 256 | 8 | 32 | 0.013408 | 0.009344 | 1.43x |
| 256 | 8 | 64 | 0.015360 | 0.010752 | 1.43x |
| 256 | 8 | 128 | 0.015392 | 0.011456 | 1.34x |
| 256 | 8 | 256 | 0.015424 | 0.015424 | 1.00x |
| 256 | 8 | 512 | 0.015648 | 0.015456 | 1.01x |
| 256 | 8 | 1024 | 0.015904 | 0.016320 | 0.97x |
| 256 | 8 | 2048 | 0.018368 | 0.017568 | 1.05x |
| 256 | 8 | 4096 | 0.020544 | 0.020480 | 1.00x |
| 256 | 8 | 8192 | 0.024704 | 0.024384 | 1.01x |
| 512 | 8 | 8 | 0.013280 | 0.011328 | 1.17x |
| 512 | 8 | 16 | 0.015360 | 0.011456 | 1.34x |
| 512 | 8 | 32 | 0.021440 | 0.013280 | 1.61x |
| 512 | 8 | 64 | 0.021600 | 0.012896 | 1.67x |
| 512 | 8 | 128 | 0.023616 | 0.015424 | 1.53x |
| 512 | 8 | 256 | 0.023520 | 0.023552 | 1.00x |
| 512 | 8 | 512 | 0.022528 | 0.019584 | 1.15x |
| 512 | 8 | 1024 | 0.022528 | 0.019904 | 1.13x |
| 512 | 8 | 2048 | 0.028512 | 0.022528 | 1.27x |
| 512 | 8 | 4096 | 0.028576 | 0.028544 | 1.00x |
| 512 | 8 | 8192 | 0.040896 | 0.037088 | 1.10x |
| 512 | 10 | 8 | 0.013312 | 0.011392 | 1.17x |
| 512 | 10 | 16 | 0.016608 | 0.013152 | 1.26x |
| 512 | 10 | 32 | 0.023456 | 0.013344 | 1.76x |
| 512 | 10 | 64 | 0.023584 | 0.013344 | 1.77x |
| 512 | 10 | 128 | 0.024416 | 0.015648 | 1.56x |
| 512 | 10 | 256 | 0.025536 | 0.025568 | 1.00x |
| 512 | 10 | 512 | 0.022528 | 0.019840 | 1.14x |
| 512 | 10 | 1024 | 0.022560 | 0.020320 | 1.11x |
| 512 | 10 | 2048 | 0.028800 | 0.022656 | 1.27x |
| 512 | 10 | 4096 | 0.029888 | 0.029920 | 1.00x |
| 512 | 10 | 8192 | 0.042816 | 0.038848 | 1.10x |
| 1024 | 32 | 8 | 0.136224 | 0.048032 | 2.84x |
| 1024 | 32 | 16 | 0.281088 | 0.050048 | 5.62x |
| 1024 | 32 | 32 | 0.573312 | 0.051776 | 11.07x |
| 1024 | 32 | 64 | 0.575520 | 0.052128 | 11.04x |
| 1024 | 32 | 128 | 0.576832 | 0.072480 | 7.96x |
| 1024 | 32 | 256 | 0.578560 | 0.578208 | 1.00x |
| 1024 | 32 | 512 | 0.655584 | 0.052864 | 12.40x |
| 1024 | 32 | 1024 | 0.670816 | 0.053056 | 12.64x |
| 1024 | 32 | 2048 | 0.665152 | 0.084800 | 7.84x |
| 1024 | 32 | 4096 | 0.796704 | 0.149408 | 5.33x |
| 1024 | 32 | 8192 | 1.321440 | 0.249472 | 5.30x |
| 2048 | 32 | 8 | 0.134176 | 0.050048 | 2.68x |
| 2048 | 32 | 16 | 0.278016 | 0.050176 | 5.54x |
| 2048 | 32 | 32 | 0.570304 | 0.053984 | 10.56x |
| 2048 | 32 | 64 | 0.572480 | 0.055968 | 10.23x |
| 2048 | 32 | 128 | 0.574144 | 0.072352 | 7.94x |
| 2048 | 32 | 256 | 0.576256 | 0.575744 | 1.00x |
| 2048 | 32 | 512 | 0.662112 | 0.058208 | 11.37x |
| 2048 | 32 | 1024 | 0.667264 | 0.058336 | 11.44x |
| 2048 | 32 | 2048 | 0.670048 | 0.086912 | 7.71x |
| 2048 | 32 | 4096 | 0.776832 | 0.144128 | 5.39x |
| 2048 | 32 | 8192 | 1.321120 | 0.230336 | 5.74x |

### sigmoid_bias_scaled

| E | K | tokens | baseline ms | opt ms | speedup |
|---:|---:|---:|---:|---:|---:|
| 256 | 8 | 8 | 0.011136 | 0.011232 | 0.99x |
| 256 | 8 | 16 | 0.012768 | 0.013216 | 0.97x |
| 256 | 8 | 32 | 0.015296 | 0.011296 | 1.35x |
| 256 | 8 | 64 | 0.015456 | 0.011328 | 1.36x |
| 256 | 8 | 128 | 0.017376 | 0.013312 | 1.31x |
| 256 | 8 | 256 | 0.017440 | 0.017312 | 1.01x |
| 256 | 8 | 512 | 0.016768 | 0.016448 | 1.02x |
| 256 | 8 | 1024 | 0.018400 | 0.017696 | 1.04x |
| 256 | 8 | 2048 | 0.018496 | 0.018496 | 1.00x |
| 256 | 8 | 4096 | 0.021728 | 0.021568 | 1.01x |
| 256 | 8 | 8192 | 0.026048 | 0.025760 | 1.01x |
| 512 | 8 | 8 | 0.015360 | 0.014624 | 1.05x |
| 512 | 8 | 16 | 0.017376 | 0.015360 | 1.13x |
| 512 | 8 | 32 | 0.023520 | 0.015360 | 1.53x |
| 512 | 8 | 64 | 0.023712 | 0.015456 | 1.53x |
| 512 | 8 | 128 | 0.025568 | 0.017536 | 1.46x |
| 512 | 8 | 256 | 0.025632 | 0.025504 | 1.00x |
| 512 | 8 | 512 | 0.025984 | 0.022048 | 1.18x |
| 512 | 8 | 1024 | 0.026560 | 0.022688 | 1.17x |
| 512 | 8 | 2048 | 0.030688 | 0.024736 | 1.24x |
| 512 | 8 | 4096 | 0.030720 | 0.032256 | 0.95x |
| 512 | 8 | 8192 | 0.044800 | 0.040800 | 1.10x |
| 1024 | 32 | 8 | 0.033696 | 0.029440 | 1.14x |
| 1024 | 32 | 16 | 0.049792 | 0.029600 | 1.68x |
| 1024 | 32 | 32 | 0.082784 | 0.029664 | 2.79x |
| 1024 | 32 | 64 | 0.083040 | 0.031744 | 2.62x |
| 1024 | 32 | 128 | 0.084512 | 0.039776 | 2.12x |
| 1024 | 32 | 256 | 0.084704 | 0.084768 | 1.00x |
| 1024 | 32 | 512 | 0.130912 | 0.034912 | 3.75x |
| 1024 | 32 | 1024 | 0.134880 | 0.036576 | 3.69x |
| 1024 | 32 | 2048 | 0.137920 | 0.046816 | 2.95x |
| 1024 | 32 | 4096 | 0.150528 | 0.071552 | 2.10x |
| 1024 | 32 | 8192 | 0.249312 | 0.110560 | 2.25x |
 
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

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Expanded support for additional routing sizes and top-k combinations,
improving compatibility across more model configurations.
* Added smarter launch selection to better match workload size,
including smaller execution paths when appropriate.

* **Bug Fixes**
* Improved routing behavior for specialized preprocessing/postprocessing
cases.
* Added safer fallback handling when no matching routing tier is
available.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3782
- **最后更新**: 2026-06-29T21:05:43Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

根据昨日提交记录，结合 FastVideo 项目（一个面向视频生成/处理的高性能框架）的背景，总结更新要点如下：

---

### 1. 主要更新类型
- **Bug 修复**（2 个）：修复 aarch64 架构下 ThunderKittens 编译问题；修复 FP4（attn_qat_infer）内核在 sm_120a 架构上的编译问题。
- **CI/基础设施**（1 个）：新增对 aarch64 (Grace Hopper) 架构内核 wheel 包的构建与发布流程，与 x86_64 并行。

### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 变更点 | 与项目方向的关系 |
|------|--------|-----------------|
| #1515 | 添加 `-fsigned-char` 编译标志，使 ThunderKittens 能在 aarch64 (Grace Hopper) 上正常编译 | 支撑项目在 **ARM + GPU 异构架构**（如 NVIDIA Grace Hopper）上的部署，拓展硬件适配范围 |
| #1514 | CI 增加 aarch64 内核 wheel 的构建与发布 | 完善 **多架构分发能力**，让用户能通过 pip 直接安装 aarch64 预编译包，降低使用门槛 |
| #1508 | 将 FP4 内核按架构拆分，仅针对 sm_120a（Hopper GPU）编译 | 修复 **低精度量化内核（FP4/注意力 QAT推理）** 的编译错误，提升模型推理的兼容性与稳定性 |

### 3. 对项目的影响和潜在意义
- **扩展硬件生态**：Grace Hopper 是 NVIDIA 面向 AI/HPC 的下一代 ARM 架构，支持该平台可吸引云服务、高性能计算场景的用户。
- **提升分发效率**：CI 自动构建多架构 wheel，避免用户自行编译，减少“环境地狱”问题，加速社区采纳。
- **巩固低精度推理能力**：FP4 内核修复意味着项目在视频模型量化、高效推理方面的工程化成熟度提升，对边缘/高吞吐场景至关重要。

### 4. 值得关注的技术点
- **`-fsigned-char` 标志**：在 ARM 上 char 默认是 unsigned，而 ThunderKittens 假设 signed char，该修复体现了跨架构代码的 subtle 兼容性问题。
- **`per-arch split`**：将内核按 GPU 架构拆分编译，是避免冗余编译、防止无效二进制碰撞的典型做法，表明项目已开始精细化管理 CUDA 架构宏解。

### 5. 这些提交如何影响项目发展
- **加速多架构支持**：快速跟进 Grace Hopper 市场趋势，使 FastVideo 在 AI 视频领域的平台竞争力增强。
- **强化“开箱即用”体验**：结合 README 强调的“快速开始”，自动化构建 wheel 让用户无需关注底层编译细节，符合项目易用性目标。
- **提升代码健壮性**：修复低精度内核与特定 GPU sm 的绑定问题，为后续更激进的量化算法（如 FP4 训练）铺平道路，推动视频模型轻量化。

## 详细提交记录

### [3d36160](https://github.com/hao-ai-lab/FastVideo/commit/3d36160fc48f5da0d0e1dd80e1856899cb93bbb5)

- **作者**: William Lin
- **时间**: 2026-06-29T21:05:38Z
- **提交信息**: [bugfix] -fsigned-char so ThunderKittens compiles on aarch64 (Grace Hopper) (#1515)

### [a11ec43](https://github.com/hao-ai-lab/FastVideo/commit/a11ec43de2e513ffcb34c5f02335303aa1825957)

- **作者**: William Lin
- **时间**: 2026-06-29T19:28:34Z
- **提交信息**: [ci] build + publish aarch64 (Grace Hopper) kernel wheels alongside x86_64 (#1514)

### [2656d65](https://github.com/hao-ai-lab/FastVideo/commit/2656d6530cf2d432c4b55f4ebca62b5275db88c3)

- **作者**: William Lin
- **时间**: 2026-06-29T18:07:27Z
- **提交信息**: [bugfix] compile FP4 (attn_qat_infer) kernels for sm_120a only via per-arch split (#1508)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33954
- **最后更新**: 2026-06-29T20:18:03Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Linoy Tsaban, Kashif Rasul, GiGi Koneti

## AI分析总结

根据提供的三条提交记录，结合 `huggingface/diffusers` 项目（一个面向扩散模型的工具库，提供模型、调度器、Pipeline 及训练/推理支持）的背景，昨日更新的要点总结如下：

### 1. 主要更新类型
- **文档完善**：为 DiffusionGemma 调度器新增文档页面（#14092）。
- **功能新增**：为非 Diffusers 格式的 Krea 2 LoRA 权重加载提供支持（#14074）。
- **测试增强**：在无 `float8_e4m3fn` 支持的设备上跳过分层转换测试，并标记 MPS 上的预期失败（#14073）。

### 2. 关键变更点及其与项目整体方向的关系
- **文档扩展**：`DiffusionGemma` 是项目近期引入的新模型系列（基于 Gemma 架构的扩散模型）。新增调度器文档有助于用户理解如何使用该模型，推动新模型生态的完善。
- **LoRA 加载兼容性**：支持加载 Krea 2（一个图像生成工具）社区训练的 LoRA 权重（来自 ComfyUI / AI-Toolkit）。这直接扩大了 Diffusers 的 LoRA 生态兼容性，符合项目「开放、易于集成」的定位——允许用户直接使用其他框架训练的权重，无需手动转换。
- **测试健壮性**：修复因硬件不支持 `float8` 类型导致测试失败的问题。这体现了项目对多硬件平台（如 CPU、MPS）的细致适配，提升 CI 稳定性和开发者体验。

### 3. 对项目的影响和潜在意义
- **降低使用门槛**：Krea 2 LoRA 支持使得非 Diffusers 训练的用户（尤其是 ComfyUI 用户）可以无缝加载主流社区模型，吸引更多创作者采用 Diffusers 进行推理和微调。
- **模型覆盖度提升**：DiffusionGemma 文档的补全标志着该系列功能已趋于稳定，可能吸引更多基于 Gemma 的研究和二次开发。
- **硬件兼容性进步**：`float8` 相关测试的跳过机制避免了非功能性失败，同时为后续更细粒度的精度支持（如 AMP）奠定基础。

### 4. 值得关注的技术点
- **非 Diffusers LoRA 的 converter 设计**：提交中通过映射 `diffusion_model.` 和 `base_model.model.` 前缀到 Diffusers 内部命名，实现了“零修改”加载。这一模式可复用于其他第三方训练框架（如 Kohya、DreamBooth 等），体现了模块化设计思路。
- **DiffusionGemma 调度器类型**：涉及“discrete DDIM”和“entropy bound”调度器，说明该模型可能是离散时间扩散模型，且引入了新的噪声/采样理论，值得关注其学术背景。
- **测试跳过策略**：使用 `xfail` 而非直接跳过 MPS，保留了在修复后能自动通过的可能性，是一种精细的测试管理。

### 5. 基于项目背景，这些提交如何影响项目发展
- **从“框架”向“生态枢纽”演进**：LoRA 加载兼容性将 Diffusers 定位从单纯的训练/推理库，扩展为连接不同社区工具（ComfyUI、AI-Toolkit 等）的权重分发中心，与 HuggingFace Hub 的模型托管愿景高度一致。
- **提升对前沿模型（Gemma）的文档质量**：说明项目正在认真推动 Google 系模型的落地，强化与兄弟项目（如 `transformers`）的协同。
- **工程稳健性优先**：测试修复虽小，但反映了项目对 CI 可靠性的重视，有助于维持大型开源社区的高频贡献节奏。

## 详细提交记录

### [1f9c201](https://github.com/huggingface/diffusers/commit/1f9c2010835ca46dc995674143cfc40a3f331118)

- **作者**: Kashif Rasul
- **时间**: 2026-06-29T20:10:42Z
- **提交信息**: Add doc pages for the DiffusionGemma schedulers (#14092)

* add doc pages for the discrete ddim and entropy bound schedulers

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

* fix the cited paper titles to match the linked papers

Co-Authored-By: Claude Opus 4.8 <noreply@anthropic.com>

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [c112837](https://github.com/huggingface/diffusers/commit/c112837d160efc3c3c1e894de0c44cfc5323d314)

- **作者**: Linoy Tsaban
- **时间**: 2026-06-29T13:44:53Z
- **提交信息**: [lora] add non-diffusers LoRA loading support for Krea 2 LoRAs (#14074)

Support loading non-diffusers Krea 2 LoRAs (ComfyUI / AI-Toolkit)

Krea 2 LoRAs in the wild are trained against the original krea-ai/krea-2
module names and ship under either the `diffusion_model.` prefix (Krea 2
reference trainer / ComfyUI exports) or the `base_model.model.` prefix
(Ostris AI-Toolkit exports). Add a converter that maps these onto the
diffusers Krea2Transformer2DModel names so they load directly via
`Krea2Pipeline.load_lora_weights`.

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [f09adee](https://github.com/huggingface/diffusers/commit/f09adee565ad1e411ef4101bc44b4cb2c3c7531c)

- **作者**: GiGi Koneti
- **时间**: 2026-06-29T13:38:00Z
- **提交信息**: [Tests] Skip layerwise casting tests on devices without float8_e4m3fn support (#14073)

* Skip layerwise casting tests on devices without float8_e4m3fn support

* Xfail float8 layerwise casting tests on MPS

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 419
- **最后更新**: 2026-06-26T21:01:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12646
- **最后更新**: 2026-06-29T22:44:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29796
- **最后更新**: 2026-06-29T22:05:31Z

## 提交统计

- **昨日提交总数**: 22
- **提交者数量**: 19
- **主要提交者**: Jonathan Mamou, Feng Yao, Cheng Wan

## AI分析总结

好的，以下是对 **sgl-project/sglang** 昨日提交记录的分析总结，结合项目背景（高性能 LLM 推理框架，支持多模型、多硬件、优化策略）进行解读。

---

### 1. 主要更新类型

| 类型 | 数量 | 代表性提交 |
|------|------|------------

## 详细提交记录

### [6bdecb8](https://github.com/sgl-project/sglang/commit/6bdecb8206b8d066e9cfb4ed6032e5a1e9b14340)

- **作者**: Khoa Pham
- **时间**: 2026-06-29T22:05:01Z
- **提交信息**: [DeepSeek V3] Reland: run routed experts on main stream in dual-stream MoE (#29463)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [45314a9](https://github.com/sgl-project/sglang/commit/45314a9fcb1b70a764f7d1f6c4238560fc524a25)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-29T21:52:23Z
- **提交信息**: [spec] Fix index_share_for_mtp_iteration being a no-op in EAGLE MTP draft (#29654)

### [fc96edd](https://github.com/sgl-project/sglang/commit/fc96edd297c0127824546532db34116525a80844)

- **作者**: Cheng Wan
- **时间**: 2026-06-29T21:49:54Z
- **提交信息**: feat(mem_cache): page-major (layer-major within a page) KV/state layout (#29533)

Co-authored-by: lch1475369 <lch1475369@gmail.com>

### [6c018eb](https://github.com/sgl-project/sglang/commit/6c018eb4d157eb1dff1807d87d8c05a3605ad85e)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-29T21:49:16Z
- **提交信息**: Fix bounded checkpoint prefetching and buffered drop-cache handling (#29156)

### [5556631](https://github.com/sgl-project/sglang/commit/5556631789c8880159f69efaf783a62bf78b7be3)

- **作者**: Jonathan Mamou
- **时间**: 2026-06-29T21:45:12Z
- **提交信息**: [Speculative Decoding] Validate vocabulary compatibility in STANDALONE mode (#23838)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [5106b42](https://github.com/sgl-project/sglang/commit/5106b42cbd98a14813f76f3c5c1f23f0012bd2fd)

- **作者**: zijiexia
- **时间**: 2026-06-29T21:42:19Z
- **提交信息**: [cookbook] GLM-5.2 NVFP4 B300: TP8 recipe + 3 strategies (#29557)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [98d0e70](https://github.com/sgl-project/sglang/commit/98d0e702c3e4c0428d8a1b8e0e0756d7897d9341)

- **作者**: Brayden Zhong
- **时间**: 2026-06-29T21:19:24Z
- **提交信息**: [GLM-5] Tune the threshold of router GEMM (#29470)

### [11b7ed7](https://github.com/sgl-project/sglang/commit/11b7ed7c9e1386102bf56a98925b8ab3f88c4a8b)

- **作者**: zijiexia
- **时间**: 2026-06-29T21:13:34Z
- **提交信息**: [Docs] Add --prerelease=allow so uv installs the latest sglang (#29676)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [74a197a](https://github.com/sgl-project/sglang/commit/74a197af9d275298336aba514f06609d780a9f21)

- **作者**: zijiexia
- **时间**: 2026-06-29T21:06:30Z
- **提交信息**: docs: add B200 NVFP4 recipes + benchmarks to GLM-5.2 cookbook (#29674)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [a5c45a1](https://github.com/sgl-project/sglang/commit/a5c45a12bb378678ba03d2405ae1630799029135)

- **作者**: cctry
- **时间**: 2026-06-29T20:56:33Z
- **提交信息**: CUDA graph executable dedup via cudaGraphExecUpdate (#29625)

Co-authored-by: cctry <cctry@fb.com>

### [f480c5f](https://github.com/sgl-project/sglang/commit/f480c5f1f93ea586d0e684bc8b561427f4e52a0c)

- **作者**: Khoa Pham
- **时间**: 2026-06-29T18:57:10Z
- **提交信息**: [Spec] Frozen-KV MTP: delay target KV binding to pool init + reset stale draft out_cache_loc (#29616)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: bef0rewind <490285+ronhuafeng@users.noreply.github.com>
Co-authored-by: AlejandroParedesLT <99832715+AlejandroParedesLT@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [b0be644](https://github.com/sgl-project/sglang/commit/b0be6441339ab6bd7e84c945786737da1ee04a32)

- **作者**: Mick
- **时间**: 2026-06-29T17:25:37Z
- **提交信息**: [diffusion] feat: keep image-model auxiliary components resident under auto memory policy (#29649)

### [e6c15f7](https://github.com/sgl-project/sglang/commit/e6c15f76f343332793d767eb9807752beaf781e4)

- **作者**: Feng Yao
- **时间**: 2026-06-29T16:19:15Z
- **提交信息**: [optimize] fix swa eviction boundary for unfinished inserts (#29350)

### [473a278](https://github.com/sgl-project/sglang/commit/473a278dd14ddbc1f8296ccce6e740ac36db37a0)

- **作者**: Jyothirmai Kottu
- **时间**: 2026-06-29T16:16:42Z
- **提交信息**: model: support nvidia/LocateAnything-3B (#28958)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [5169df7](https://github.com/sgl-project/sglang/commit/5169df70f6f5434026a89e33946a9f2af2044a79)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-29T14:11:37Z
- **提交信息**: [AMD] Sgl-data mount opt-in (#29661)

Co-authored-by: bingxche <bingxche@amd.com>

### [bb7d344](https://github.com/sgl-project/sglang/commit/bb7d3440b56b3a054bfa34aedd100a40d4451cd9)

- **作者**: McZyWu
- **时间**: 2026-06-29T11:30:14Z
- **提交信息**: bugfix revise interface get cpu copy for npu mem pool to align with gpu (#29146)

### [489017b](https://github.com/sgl-project/sglang/commit/489017b3d6c0ba547923eb0a693715e60984e016)

- **作者**: amote-i
- **时间**: 2026-06-29T11:17:06Z
- **提交信息**: [NPU] [DOC] Update deterministic inference feature support status to A2, A3 (#29632)

### [93926b9](https://github.com/sgl-project/sglang/commit/93926b9a95d1ea672dbc5f6da48b839bcee484b4)

- **作者**: Shangming Cai
- **时间**: 2026-06-29T10:52:03Z
- **提交信息**: Add Qwen3 MoE tests for PP compatibility with CP and DP (#29640)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [a2b5ce2](https://github.com/sgl-project/sglang/commit/a2b5ce2ed124dd4f0d4728c021ebac468311e00f)

- **作者**: danielafrimi
- **时间**: 2026-06-29T08:47:09Z
- **提交信息**: Add stochastic rounding for FP16 Mamba SSM cache (#26929)

Signed-off-by: Daniel Afrimi <dafrimi@login-lyris01.lyris.clusters.nvidia.com>
Co-authored-by: Daniel Afrimi <dafrimi@login-lyris01.lyris.clusters.nvidia.com>

### [d5133e9](https://github.com/sgl-project/sglang/commit/d5133e925bbdd558bf9063f0a2f29a990cbe12ae)

- **作者**: iridiumine
- **时间**: 2026-06-29T08:34:54Z
- **提交信息**: [NPU][Bugfix] Add scoring_func for mimo_v2 (#29493)

Co-authored-by: iridiumine <iridiumine@users.noreply.github.com>

### [3b1b512](https://github.com/sgl-project/sglang/commit/3b1b512a9adb056b7d815022609ab6620459b2f6)

- **作者**: bef0rewind
- **时间**: 2026-06-29T08:22:29Z
- **提交信息**: Fix disaggregation receiver ZMQ cleanup (#29570)

### [91cf159](https://github.com/sgl-project/sglang/commit/91cf15969662296b2663e372d28adcd19b001b57)

- **作者**: SSSunzt
- **时间**: 2026-06-29T08:01:41Z
- **提交信息**: [PP] bugfix: include CP size in PP rank offset (#29571)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1211
- **最后更新**: 2026-06-29T07:39:04Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 84832
- **最后更新**: 2026-06-29T22:52:21Z

## 提交统计

- **昨日提交总数**: 36
- **提交者数量**: 27
- **主要提交者**: Blas Rodriguez Irizar, Xiaohong (Sean) Chen, wang.yuqi

## AI分析总结

## 昨日 vllm 更新要点总结

### 1. 主要更新类型
- **Bug 修复**（约 12 项）：稀疏注意力、FlashAttention、量化回归、依赖冲突、模型结构错误等。
- **性能优化**（4 项）：Triton kernel warmup 扩展（DSv4/Qwen）、MLA logits workspace、Helion kernel、FS Offloading 批量查找 C 实现。
- **新功能/模型支持**（4 项）：ModelRunner V2 支持 Mamba 混合模型前缀缓存对齐、FlashInfer MLA DCP 支持、MiniMax-M3 modelopt NV

## 详细提交记录

### [75698e6](https://github.com/vllm-project/vllm/commit/75698e60b3b0db7f443f8bf19d5d3a20ddc4ce0a)

- **作者**: Wentao Ye
- **时间**: 2026-06-29T22:45:53Z
- **提交信息**: [Bug] Fix sparse attention issue for GLM5.2 non-torch compile path (#47083)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [8632c88](https://github.com/vllm-project/vllm/commit/8632c884dc440e231c8b7aef65a8795b80fe6676)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-29T21:34:05Z
- **提交信息**: [ROCm][CI] Use spawn around the threaded OTLP test (#47003)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [c3734e8](https://github.com/vllm-project/vllm/commit/c3734e8334ba124b722676e745084b8f4f86420b)

- **作者**: peizhang56
- **时间**: 2026-06-29T21:29:47Z
- **提交信息**: [CI][Bugfix] Add cohere_melody to ROCm test requirements (#47072)

Signed-off-by: pei.zhang <pei.zhang@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [53f7553](https://github.com/vllm-project/vllm/commit/53f7553f099c2cbb88d2161959fc49dd71c8205b)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-29T21:28:02Z
- **提交信息**: [ROCm][DeepEP] Stabilize high-throughput DBO for DP+EP (#46990)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [4eb2279](https://github.com/vllm-project/vllm/commit/4eb227992aa2231ad538b8c90bc8191397ba3697)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-29T21:26:41Z
- **提交信息**: [ROCm][CI] Make memory sampling less racy in tests and sleep mode (#45490)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: Codex <codex@example.invalid>
Co-authored-by: Codex <codex@example.invalid>

### [ebcf511](https://github.com/vllm-project/vllm/commit/ebcf511ec3c291eae63c38f5f431c07229e2406d)

- **作者**: Micah Williamson
- **时间**: 2026-06-29T21:24:08Z
- **提交信息**: [ROCm][CI] Soft Fail `Spec Decode Ngram + Suffix` and `Entrypoints Integration (LLM)` AMD Mirrors (#47067)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>

### [8fc1b2d](https://github.com/vllm-project/vllm/commit/8fc1b2d046f4a991b5c24bb5470bf45efcfe9d01)

- **作者**: Matthew Bonanni
- **时间**: 2026-06-29T21:23:34Z
- **提交信息**: Fix FA4 dynamic_causal for full attention layers (#46659)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [5316638](https://github.com/vllm-project/vllm/commit/5316638a5eb98d764a5618c20a1558ffc24d3bc9)

- **作者**: Harry Mellor
- **时间**: 2026-06-29T21:20:33Z
- **提交信息**: Fix transient dependency issues caused by `requirements/common.txt` (#47015)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [61ab70e](https://github.com/vllm-project/vllm/commit/61ab70ec3bd13dd422b86f3b80207d322994a5e7)

- **作者**: zhrrr
- **时间**: 2026-06-29T21:09:16Z
- **提交信息**: [Model Runner V2] support mamba hybrid models align prefix cache (#42406)

Signed-off-by: zhuhaoran <zhuhaoran.zhr@alibaba-inc.com>

### [a309d4f](https://github.com/vllm-project/vllm/commit/a309d4fe60bef7657b88805a1fcc9b014c414314)

- **作者**: Woosuk Kwon
- **时间**: 2026-06-29T20:24:29Z
- **提交信息**: Support DCP with FlashInfer MLA (#43729)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [72f6399](https://github.com/vllm-project/vllm/commit/72f639927f6caf3495d69dec63b9d4a87ed782ef)

- **作者**: zofia
- **时间**: 2026-06-29T19:03:06Z
- **提交信息**: [XPU] [RMSNorm] revert weightless change on xpu (#46987)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [8ad4a01](https://github.com/vllm-project/vllm/commit/8ad4a01825ef941e785b2bc305ac7a6b5ca9c530)

- **作者**: Nick Hill
- **时间**: 2026-06-29T16:56:17Z
- **提交信息**: [ModelRunner V2] Simplify recent UnlimitedOCR-related changes (#46975)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [7be5826](https://github.com/vllm-project/vllm/commit/7be582697b27277e2756a3878f563fa9dfea30aa)

- **作者**: Jee Jee Li
- **时间**: 2026-06-29T16:44:05Z
- **提交信息**: [Bugfix] Fix DeepseekV2Model hidden_size (#46986)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [030c952](https://github.com/vllm-project/vllm/commit/030c9523bdb6a6292545768c863fd747c195b06b)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-29T16:40:34Z
- **提交信息**: [Perf][1/N] Expand Triton kernel warmup coverage, DSv4 (#46634)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [4708292](https://github.com/vllm-project/vllm/commit/4708292d48f3f15978a6ad3befe5f0052bc86491)

- **作者**: Wei Zhao
- **时间**: 2026-06-29T16:30:57Z
- **提交信息**: Bump flashinfer version to 0.6.13 (#46683)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [debec64](https://github.com/vllm-project/vllm/commit/debec6440b89fe6ab14acb00e6eb2b04257f57a2)

- **作者**: Jason Li
- **时间**: 2026-06-29T16:29:39Z
- **提交信息**: Add MiniMax-M3 modelopt nvfp4 support (#46756)

Signed-off-by: Xin Li <xinli@nvidia.com>
Signed-off-by: jasonlizhengjian <jasonlizhengjian@gmail.com>
Co-authored-by: Xin Li <xinli@nvidia.com>

### [c8fb296](https://github.com/vllm-project/vllm/commit/c8fb2963bd1baebbdd28062097096b59b2ba3189)

- **作者**: Varun Sundar Rabindranath
- **时间**: 2026-06-29T16:28:32Z
- **提交信息**: [FS-Offloading] Batch Lookup in C  (#46713)

Signed-off-by: <>
Co-authored-by: Varun Sundar Rabindranath <varun-sundar-rabindranath@h100-01.nemg-001.lab.rdu2.dc.redhat.com>

### [379acd4](https://github.com/vllm-project/vllm/commit/379acd4e4fc33c3939556cf3a888f0963ec5c8ce)

- **作者**: HDCharles
- **时间**: 2026-06-29T15:55:42Z
- **提交信息**: [Bugfix][Quantization] Fix W8A8 int-quantized scheme selection regression (#46860)

Signed-off-by: HDCharles <charlesdavidhernandez@gmail.com>

### [07d33e5](https://github.com/vllm-project/vllm/commit/07d33e575b472db52ae73ad44af18d909f34f177)

- **作者**: Martin Hickey
- **时间**: 2026-06-29T15:42:35Z
- **提交信息**: [MyPy] Fix mypy incompatible assignment errors in LRUCacheLoRAModelManager (#44657)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [36bbecd](https://github.com/vllm-project/vllm/commit/36bbecd6436d0dd4c7a27fbb09a787e00534d647)

- **作者**: Varun Sundar Rabindranath
- **时间**: 2026-06-29T14:54:34Z
- **提交信息**: [BugFix] Revert "[KV Offload] Use background thread for mmap / cpu_tensors pinning" (#46958)

Signed-off-by: <>
Co-authored-by: Varun Sundar Rabindranath <varun-sundar-rabindranath@h100-01.nemg-001.lab.rdu2.dc.redhat.com>

### [6149187](https://github.com/vllm-project/vllm/commit/6149187a4cca41e4e16c6461de39a6c33005c361)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-06-29T14:54:29Z
- **提交信息**: [Kernel] Triton MLA logits workspace (#46819)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [49e28e8](https://github.com/vllm-project/vllm/commit/49e28e8e91ad9ed102e88e50c190686408be5552)

- **作者**: Xiaohong (Sean) Chen
- **时间**: 2026-06-29T14:54:15Z
- **提交信息**: [Kernel][Helion][1/N] Add Helion kernel for fused_qk_norm_rope (#44010)

Signed-off-by: Sean Chen <seachen@redhat.com>

### [0ca39c4](https://github.com/vllm-project/vllm/commit/0ca39c4f1fc450339f57ceca6bddc2af1abe84a5)

- **作者**: Michael Goin
- **时间**: 2026-06-29T14:00:31Z
- **提交信息**: [Bugfix] Capture final-layer aux hidden state in deepseek_v2 backbone (#46973)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [6185d73](https://github.com/vllm-project/vllm/commit/6185d73882c0cdfd9ee13cea16a9b50d2b5267be)

- **作者**: Blas Rodriguez Irizar
- **时间**: 2026-06-29T13:46:33Z
- **提交信息**: [Rust Frontend] Keep literal "null" string for string-typed tool params (#46827)

Signed-off-by: Blas Rodriguez Irizar <rodrigblas@gmail.com>

### [bc8481a](https://github.com/vllm-project/vllm/commit/bc8481af09cd4c7f7272ba7bc1913f1051649813)

- **作者**: bnellnm
- **时间**: 2026-06-29T13:19:29Z
- **提交信息**: [MoE Refactor] Standardize Humming MoE experts + utilities (#43373)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [59575da](https://github.com/vllm-project/vllm/commit/59575da46df964e6161fb0e1a77fa76ea9ce3106)

- **作者**: Yan Ma
- **时间**: 2026-06-29T12:30:28Z
- **提交信息**: [XPU] exclude unsupported models for test_tensor_sechma.py (#47008)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [3483240](https://github.com/vllm-project/vllm/commit/3483240b7ea3d4372b6c79369ea36617f8b1fbb2)

- **作者**: wang.yuqi
- **时间**: 2026-06-29T10:18:53Z
- **提交信息**: [Frontend] Consolidate scale out entrypoints (#44512)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [eddfd4c](https://github.com/vllm-project/vllm/commit/eddfd4cf219359296758272ca736d38cb2c327b1)

- **作者**: Roberto L. Castro
- **时间**: 2026-06-29T10:10:07Z
- **提交信息**: [Perf][2/N] Expand Triton kernel warmup coverage, Qwen (#46750)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>

### [a4e3cb4](https://github.com/vllm-project/vllm/commit/a4e3cb40d07a1b43f6283cb77d560330b46369a9)

- **作者**: Martin Hickey
- **时间**: 2026-06-29T09:29:09Z
- **提交信息**: [mypy] Enable mypy for tests directory (#47018)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [ab132ee](https://github.com/vllm-project/vllm/commit/ab132ee98ba14c5d99977b1f83c2d5517c0a1e79)

- **作者**: soaringk
- **时间**: 2026-06-29T09:17:54Z
- **提交信息**: Fix model info cache for package models (#46567)

Signed-off-by: soaringk <k3vin.zhang@gmail.com>

### [e186107](https://github.com/vllm-project/vllm/commit/e1861078704b0b091206e83cdd64eaf10b1967ef)

- **作者**: Alden Lobo
- **时间**: 2026-06-29T09:12:20Z
- **提交信息**: [Bugfix] Use native SiLU activation in CPU fused MoE (#45961)

Signed-off-by: Alden Lobo <alden.lobo@arm.com>
Co-authored-by: Alden Lobo <alden.lobo@arm.com>

### [0e207da](https://github.com/vllm-project/vllm/commit/0e207dac784e6b217b8dc1f44ae3985b1f216b50)

- **作者**: John
- **时间**: 2026-06-29T08:59:15Z
- **提交信息**: [Bugfix] Transformers backend: apply learned lm_head.bias for tied-embedding models (#46835)

Signed-off-by: John Langford <jl@hunch.net>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [9e86352](https://github.com/vllm-project/vllm/commit/9e86352c606c61095029f156ae3e4ac2097cf7e5)

- **作者**: wang.yuqi
- **时间**: 2026-06-29T08:57:26Z
- **提交信息**: [CI Failure] Add transformers version check for openai/privacy-filter (#47011)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [5051698](https://github.com/vllm-project/vllm/commit/5051698e41b7dc3da421f1c50bfe178a92dc7881)

- **作者**: Harry Mellor
- **时间**: 2026-06-29T08:52:23Z
- **提交信息**: Remove unnecessary `load_weights` methods (#44589)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [db28ae2](https://github.com/vllm-project/vllm/commit/db28ae2d078da82d01f8e7fad05fb27a52ce37ef)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-29T07:59:24Z
- **提交信息**: [ROCm][CI] Explicitly tear down multimodal offline LLMs (#46999)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [f6bb868](https://github.com/vllm-project/vllm/commit/f6bb8682ee5b6a35cb0c74a4c1f01165ee6ca24d)

- **作者**: Harry Mellor
- **时间**: 2026-06-29T07:50:57Z
- **提交信息**: Fix docs on main (#47009)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-30
**监控日期**: 2026-06-29
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5346
- **最后更新**: 2026-06-29T21:14:43Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: Ayaka Mikazuki, Peiqi Yin, JiangJie Zhang

## AI分析总结

### 昨日更新要点总结

---

#### 1. 主要更新类型

- **功能新增**：为扩散管道（diffusion pipelines）添加请求级批处理支持
- **性能优化**：修复编排器（orchestrator）瓶颈，分离阶段间输出与客户端输出
- **Bug修复**：
  - 恢复 NPU 图行为（限制 `cudagraph_mode` 为 `PIECEWISE`）
  - 修复 Qwen2.5-Omni 的 AutoRound 加载问题

---

#### 2. 关键变更点与项目方向的关系

| 提交 | 关键变更 | 与项目方向关联 |
|------|----------|----------------|
| c45ac74 | 支持扩散管道的 **请求级批处理** | 直接服务于 **omni-modality** 目标：扩散模型常用于图像/视频生成，批处理提升吞吐量，降低多模态服务成本 |
| 504698d | 编排器性能优化：分离 **inter-stage** 与 **client outputs** | 编排器是 **多模态模型串联/并联的核心**，优化其瓶颈可减少多组件协同推理的延迟，提升整体服务效率 |
| 724f5d1 | 恢复 NPU 图行为（限制 `PIECEWISE`） | 华为 NPU 是国产推理硬件，修复兼容性确保 **vllm-omni 能在更多硬件上运行**，符合“cheap”理念 |
| deb9bd4 | 修复 Qwen2.5-Omni 的 AutoRound 加载 | Qwen2.5-Omni 是近期重要的 **全模态大模型**，修复量化模型加载是支持该模型的必要步骤，增强模型生态 |

---

#### 3. 对项目的影响和潜在意义

- **扩散管道批处理**：提升图像/视频生成类任务的服务并发能力，使 vllm-omni 不仅能处理文本/音频，还能高效服务生成式多模态模型。
- **编排器性能优化**：降低多模型组合（如视觉+语言模型）的端到端延迟，推动“cheap”目标——用更少资源跑更多模态。
- **NPU 图修复**：扩大硬件支持范围，尤其利好国产昇腾生态，吸引更多开发者使用。
- **Qwen2.5-Omni 修复**：紧跟最新开源多模态大模型，保持项目前沿性，便于用户快速部署此模型。

---

#### 4. 值得关注的技术点

- **Diffusion 请求级批处理**：不同扩散步骤（如去噪步数）的请求如何在 batch 中对齐？实现中可能涉及动态序列长度或 padding 策略，值得后续查看 PR#4079 细节。
- **编排器架构调整**：分离 inter-stage 与 client outputs 意味着修改了数据流，可能影响 API 接口或分布式调度逻辑，需关注是否引入新的配置项。
- **NPU cudagraph_mode = PIECEWISE**：之前 #9572 可能放宽了限制导致 bug，恢复后对性能的影响需要观察（PIECEWISE 是保守策略）。
- **AutoRound 加载修复**：量化模型加载常因权重格式或配置不匹配出错，修复可能涉及 `trust_remote_code` 或 `quantization_config` 处理。

---

#### 5. 结合项目背景，这些提交如何影响项目发展

vllm-omni 的定位是 **“Easy, fast, and cheap omni-modality model serving”**。昨日更新从三个维度推动该目标：

- **Fast**：编排器性能优化 + 扩散管道批处理直接加速多模态推理。
- **Cheap**：NPU 支持扩展低成本硬件选择；批处理提高资源利用率。
- **Omni-modality**：修复 Qwen2.5-Omni 加载、支持扩散管道批处理，扩展了支持的模态（文本+视觉+生成）。

整体来看，项目正在从 **“能跑模型”** 向 **“高效跑多模态模型”** 演进，尤其注重降低推理成本和硬件门槛，符合开源社区对普惠多模态服务的期待。

## 详细提交记录

### [c45ac74](https://github.com/vllm-project/vllm-omni/commit/c45ac74d4303662a14a3985353a59188f336c532)

- **作者**: JiangJie Zhang
- **时间**: 2026-06-29T16:09:19Z
- **提交信息**: [Core][Frontend] Support request-level batching for diffusion pipelines (#4079)

Signed-off-by: jader <yjader@foxmail.com>
Co-authored-by: Samit <285365963@qq.com>

### [504698d](https://github.com/vllm-project/vllm-omni/commit/504698dec824b99ea42765a7c21823cb97eb1713)

- **作者**: Peiqi Yin
- **时间**: 2026-06-29T15:43:36Z
- **提交信息**: [Core] Performance fix for orchestrator bottleneck: separates inter-stage from client outputs (#4527)

Signed-off-by: yinpeiqi <yinpeiqi809@gmail.com>
Co-authored-by: Chenguang ZHENG <645327136@qq.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [724f5d1](https://github.com/vllm-project/vllm-omni/commit/724f5d132deb55dfd73591c83494eca15c95d179)

- **作者**: Weiming Liao
- **时间**: 2026-06-29T07:54:26Z
- **提交信息**: [BugFix] Restore pre-#9572 NPU graph behavior (cap cudagraph_mode to PIECEWISE) (#4674)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [deb9bd4](https://github.com/vllm-project/vllm-omni/commit/deb9bd4efc385d20a54e3d2a63168c1381822969)

- **作者**: Ayaka Mikazuki
- **时间**: 2026-06-29T07:34:27Z
- **提交信息**: Fix Qwen2.5-Omni AutoRound loading (#4781)

Signed-off-by: Ayaka <ayaka@mail.shn.hk>

---
