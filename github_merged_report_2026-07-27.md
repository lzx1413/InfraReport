# GitHub Stars 合并报告 - 2026-07-27

**合并日期**: 2026-07-28
**监控日期**: 2026-07-27
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


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2109
- **最后更新**: 2026-07-27T15:36:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2536
- **最后更新**: 2026-07-27T09:57:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2180
- **最后更新**: 2026-07-25T19:55:38Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6046
- **最后更新**: 2026-07-27T19:50:03Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Ka-Hyun Nam, Observer007, Jimmy Zhou

## AI分析总结

当然，以下是对 FlashInfer 仓库昨日三条提交的分析与总结。

---

### 1. 主要更新类型
- **Bug 修复 / 重构**：修复 GDN decode 在 SM121 架构上的编译与运行问题，并迁移至统一 CuTe DSL（`d536efd`）
- **性能优化**：针对 Blackwell（SM100）的 GDN prefill 内核实现中位数 1.25× 加速（`f057e15`）
- **回退 / 兼容性调整**：回退 PR #4122，调整 GPU 架构支持列表和内核选择逻辑（`6258e52`）

---

### 2. 关键变更点及其与项目方向的关系
- **SM121 解码支持**：将 WY output-only GDN decode 内核从废弃的 `cute.experimental` 装饰器迁移到统一 CuTe DSL，并指定 `sm_120a` / `sm_121a` 编译目标。同时将计算能力加入编译缓存 key，防止缓存冲突。  
  → 直接支持 FlashInfer 在新一代消费级/服务器级 GPU（如 GB10）上的推理部署，延续项目“高性能 GPU 推理内核”定位。
- **SM100 Prefill 优化**：重构 chunk 处理、状态加载/存储、逆运算等逻辑，并在编译时启用更积极的优化等级（`--opt-level 3`），实现 120 种配置无回归的性能提升。  
  → 针对 Blackwell 架构（B300 等）的推理场景显著提升吞吐量，加强项目在最新硬件上的竞争力。
- **回退 PR #4122**：撤销此前对 SM107/10.7a 等架构的修改，恢复原有架构支持范围与内核选择。  
  → 表明项目对兼容性变更持谨慎态度，避免因激进引入新架构导致现有用户中断，保持项目稳定性。

---

### 3. 对项目的影响和潜在意义
- **硬件覆盖扩大**：成功支持 SM12x（GB10 等）和 SM100（Blackwell），使 FlashInfer 能覆盖 NVIDIA 从 Ada 到 Blackwell 的完整推理硬件链。
- **性能持续领先**：GDN prefill 在 Blackwell 上的显著加速，进一步巩固 FlashInfer 在高吞吐量推理场景的效率优势。
- **代码质量提升**：通过迁移至统一 DSL，减少实验性 API 依赖，降低后续维护成本；同时加入更精细的编译缓存策略，避免跨架构缓存错误。
- **稳定性保障**：及时回退有潜在兼容性风险的变更，体现项目对生产环境部署可靠性的重视。

---

### 4. 值得关注的技术点
- **CuTe DSL 统一化**：弃用 `cute.experimental`，改用统一 DSL 并搭配 TMA、mbarrier、cluster-launch 等标准原语，体现了向成熟 CuTe 生态的迁移趋势。
- **编译缓存 key 粒度增强**：将计算能力（`sm_120a` / `sm_121a`）纳入缓存 key，避免多架构混合编译时使用错误缓存的 bug。
- **性能优化手法**：kernel 处理阶段重排、状态加载存储针对 Blackwell 布局优化、逆运算数值稳定性改进——这些通用优化方法也适用于其他 attention 变体。
- **回退 PR 的广度**：回退不仅影响 GDN，还涉及 attention、GEMM、MoE、量化

## 详细提交记录

### [d536efd](https://github.com/flashinfer-ai/flashinfer/commit/d536efd5aeb3f7a2fc9e887592cd0fe9f1a94893)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-07-27T19:06:19Z
- **提交信息**: fix(gdn): support WY decode on SM121 (#4117)

## Summary
- migrate the WY output-only GDN decode kernel from deprecated
`cute.experimental` decorators to the unified CuTe DSL decorators
- compile SM12x kernels for the device-specific `sm_120a` / `sm_121a`
target
- include compute capability in the in-process compile cache key

The kernel uses no experimental-only APIs; the unified DSL supports its
TMA, mbarrier, cluster-launch, and occupancy controls. The experimental
path emitted a Core MLIR `sm_121` attribute that
`nvidia-cutlass-dsl==4.6.1` rejects before compilation.

Closes #3995.

## Test plan
- [x] H100 (SM90): `pytest
tests/gdn/test_decode_delta_rule.py::test_gdn_decode_bf16_wy_output_only_mtp_kernel
-q` — 15 passed
- [x] GB10 (SM121), `nvidia-cutlass-dsl==4.6.1`: same test — 15 passed
- [x] pre-commit hooks: mypy, ruff check, ruff format

Related: #3960 uses the same device-matched SM12x compile target for GDN
prefill.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Refactor**
  * Updated GPU kernel compilation to use stable compilation interfaces.
  * Improved compilation behavior for newer GPU architectures.
* Enhanced kernel caching to prevent reuse of incompatible compiled
binaries.
* **Bug Fixes**
* Improved reliability when compiling and running the kernel across
different GPU variants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f057e15](https://github.com/flashinfer-ai/flashinfer/commit/f057e15bdf8285509f86bac3004adf25a274f121)

- **作者**: Observer007
- **时间**: 2026-07-27T19:03:54Z
- **提交信息**: [GDN] improve sm100 GDN performance (#4133)

## What

Optimizes the Blackwell SM100 chunk-stream Gated Delta Net (GDN) prefill
kernel.
Coauthored by @guangyunh-nv @jhjpark 

## Test environment

- **GPU:** NVIDIA B300 SXM6 AC — Blackwell (SM100)
- **Compile:** `--enable-tvm-ffi --opt-level 3`
- **Dtype:** bf16 in/out, fp32 state + accumulation
- **Benchmark:** `benchmarks/bench_gdn_prefill.py`, 2 warmup + 8 timed
iters, CUDA graph
- **Baseline ("pre-PR"):** the initial functional port of this kernel
(`--opt-level 2`)

## Performance

120 configurations (8 head configs x 15 sequence configs). **Median
1.25x** speedup
(range 1.07x-1.32x). No regressions (every config is faster than the
baseline).

<details>
<summary>Full 120-configuration results (h_qk/h_v, seqlen, pre-PR ms,
this-PR ms, speedup)</summary>

| h_qk/h_v | seqlen | pre-PR (ms) | this PR (ms) | speedup |
|---|---|---|---|---|
| 2/8 | 1x65536 | 2.352 | 1.827 | 1.29x |
| 2/8 | 1x32768 | 1.184 | 0.923 | 1.28x |
| 2/8 | 1x16384 | 0.601 | 0.470 | 1.28x |
| 2/8 | 1x8192 | 0.311 | 0.242 | 1.28x |
| 2/8 | 1x4096 | 0.165 | 0.129 | 1.28x |
| 2/8 | 1x2048 | 0.091 | 0.069 | 1.31x |
| 2/8 | 6144+2048 | 0.237 | 0.187 | 1.27x |
| 2/8 | 4096+4096 | 0.165 | 0.131 | 1.26x |
| 2/8 | 2048+6144 | 0.237 | 0.187 | 1.27x |
| 2/8 | 1024+7168 | 0.274 | 0.215 | 1.27x |
| 2/8 | 2048x4 | 0.093 | 0.074 | 1.25x |
| 2/8 | 1024x8 | 0.057 | 0.047 | 1.22x |
| 2/8 | 8192x8 | 0.315 | 0.246 | 1.28x |
| 2/8 | 8192x16 | 0.317 | 0.248 | 1.28x |
| 2/8 | 8192x32 | 0.627 | 0.490 | 1.28x |
| 4/16 | 1x65536 | 2.349 | 1.830 | 1.28x |
| 4/16 | 1x32768 | 1.185 | 0.925 | 1.28x |
| 4/16 | 1x16384 | 0.602 | 0.471 | 1.28x |
| 4/16 | 1x8192 | 0.311 | 0.245 | 1.27x |
| 4/16 | 1x4096 | 0.165 | 0.131 | 1.26x |
| 4/16 | 1x2048 | 0.092 | 0.074 | 1.25x |
| 4/16 | 6144+2048 | 0.238 | 0.189 | 1.26x |
| 4/16 | 4096+4096 | 0.166 | 0.133 | 1.25x |
| 4/16 | 2048+6144 | 0.239 | 0.188 | 1.27x |
| 4/16 | 1024+7168 | 0.276 | 0.216 | 1.27x |
| 4/16 | 2048x4 | 0.094 | 0.077 | 1.23x |
| 4/16 | 1024x8 | 0.060 | 0.050 | 1.21x |
| 4/16 | 8192x8 | 0.317 | 0.249 | 1.27x |
| 4/16 | 8192x16 | 0.626 | 0.493 | 1.27x |
| 4/16 | 8192x32 | 1.235 | 1.031 | 1.20x |
| 8/32 | 1x65536 | 2.361 | 1.836 | 1.29x |
| 8/32 | 1x32768 | 1.190 | 0.928 | 1.28x |
| 8/32 | 1x16384 | 0.605 | 0.475 | 1.27x |
| 8/32 | 1x8192 | 0.312 | 0.247 | 1.26x |
| 8/32 | 1x4096 | 0.166 | 0.133 | 1.24x |
| 8/32 | 1x2048 | 0.092 | 0.075 | 1.24x |
| 8/32 | 6144+2048 | 0.240 | 0.191 | 1.26x |
| 8/32 | 4096+4096 | 0.167 | 0.134 | 1.24x |
| 8/32 | 2048+6144 | 0.241 | 0.190 | 1.27x |
| 8/32 | 1024+7168 | 0.278 | 0.218 | 1.28x |
| 8/32 | 2048x4 | 0.097 | 0.079 | 1.23x |
| 8/32 | 1024x8 | 0.113 | 0.094 | 1.20x |
| 8/32 | 8192x8 | 0.628 | 0.508 | 1.24x |
| 8/32 | 8192x16 | 1.242 | 1.033 | 1.20x |
| 8/32 | 8192x32 | 2.185 | 1.933 | 1.13x |
| 16/64 | 1x65536 | 2.383 | 1.835 | 1.30x |
| 16/64 | 1x32768 | 1.202 | 0.927 | 1.30x |
| 16/64 | 1x16384 | 0.611 | 0.473 | 1.29x |
| 16/64 | 1x8192 | 0.316 | 0.247 | 1.28x |
| 16/64 | 1x4096 | 0.168 | 0.133 | 1.26x |
| 16/64 | 1x2048 | 0.094 | 0.077 | 1.23x |
| 16/64 | 6144+2048 | 0.243 | 0.192 | 1.26x |
| 16/64 | 4096+4096 | 0.171 | 0.137 | 1.26x |
| 16/64 | 2048+6144 | 0.244 | 0.192 | 1.27x |
| 16/64 | 1024+7168 | 0.281 | 0.220 | 1.27x |
| 16/64 | 2048x4 | 0.186 | 0.152 | 1.23x |
| 16/64 | 1024x8 | 0.219 | 0.185 | 1.19x |
| 16/64 | 8192x8 | 1.246 | 1.034 | 1.21x |
| 16/64 | 8192x16 | 2.189 | 1.930 | 1.13x |
| 16/64 | 8192x32 | 4.404 | 4.001 | 1.10x |
| 16/32 | 1x65536 | 2.364 | 1.839 | 1.29x |
| 16/32 | 1x32768 | 1.192 | 0.930 | 1.28x |
| 16/32 | 1x16384 | 0.605 | 0.475 | 1.27x |
| 16/32 | 1x8192 | 0.312 | 0.247 | 1.26x |
| 16/32 | 1x4096 | 0.166 | 0.134 | 1.24x |
| 16/32 | 1x2048 | 0.092 | 0.075 | 1.23x |
| 16/32 | 6144+2048 | 0.240 | 0.191 | 1.25x |
| 16/32 | 4096+4096 | 0.167 | 0.134 | 1.25x |
| 16/32 | 2048+6144 | 0.241 | 0.191 | 1.27x |
| 16/32 | 1024+7168 | 0.278 | 0.219 | 1.27x |
| 16/32 | 2048x4 | 0.097 | 0.080 | 1.21x |
| 16/32 | 1024x8 | 0.112 | 0.095 | 1.18x |
| 16/32 | 8192x8 | 0.629 | 0.499 | 1.26x |
| 16/32 | 8192x16 | 1.244 | 1.065 | 1.17x |
| 16/32 | 8192x32 | 2.190 | 1.990 | 1.10x |
| 16/48 | 1x65536 | 2.335 | 1.832 | 1.27x |
| 16/48 | 1x32768 | 1.177 | 0.927 | 1.27x |
| 16/48 | 1x16384 | 0.599 | 0.473 | 1.27x |
| 16/48 | 1x8192 | 0.310 | 0.246 | 1.26x |
| 16/48 | 1x4096 | 0.165 | 0.133 | 1.25x |
| 16/48 | 1x2048 | 0.092 | 0.075 | 1.23x |
| 16/48 | 6144+2048 | 0.239 | 0.191 | 1.25x |
| 16/48 | 4096+4096 | 0.168 | 0.134 | 1.25x |
| 16/48 | 2048+6144 | 0.240 | 0.190 | 1.26x |
| 16/48 | 1024+7168 | 0.277 | 0.219 | 1.27x |
| 16/48 | 2048x4 | 0.184 | 0.150 | 1.23x |
| 16/48 | 1024x8 | 0.165 | 0.138 | 1.19x |
| 16/48 | 8192x8 | 0.930 | 0.780 | 1.19x |
| 16/48 | 8192x16 | 1.852 | 1.566 | 1.18x |
| 16/48 | 8192x32 | 3.393 | 3.059 | 1.11x |
| 16/16 | 1x65536 | 2.377 | 1.836 | 1.29x |
| 16/16 | 1x32768 | 1.198 | 0.928 | 1.29x |
| 16/16 | 1x16384 | 0.608 | 0.473 | 1.29x |
| 16/16 | 1x8192 | 0.314 | 0.246 | 1.28x |
| 16/16 | 1x4096 | 0.167 | 0.132 | 1.26x |
| 16/16 | 1x2048 | 0.092 | 0.074 | 1.25x |
| 16/16 | 6144+2048 | 0.240 | 0.189 | 1.27x |
| 16/16 | 4096+4096 | 0.168 | 0.132 | 1.27x |
| 16/16 | 2048+6144 | 0.242 | 0.189 | 1.28x |
| 16/16 | 1024+7168 | 0.279 | 0.217 | 1.28x |
| 16/16 | 2048x4 | 0.095 | 0.076 | 1.24x |
| 16/16 | 1024x8 | 0.060 | 0.050 | 1.20x |
| 16/16 | 8192x8 | 0.319 | 0.252 | 1.27x |
| 16/16 | 8192x16 | 0.632 | 0.507 | 1.25x |
| 16/16 | 8192x32 | 1.243 | 1.107 | 1.12x |
| 32/32 | 1x65536 | 2.398 | 1.844 | 1.30x |
| 32/32 | 1x32768 | 1.209 | 0.932 | 1.30x |
| 32/32 | 1x16384 | 0.614 | 0.476 | 1.29x |
| 32/32 | 1x8192 | 0.316 | 0.247 | 1.28x |
| 32/32 | 1x4096 | 0.168 | 0.133 | 1.26x |
| 32/32 | 1x2048 | 0.093 | 0.075 | 1.24x |
| 32/32 | 6144+2048 | 0.242 | 0.191 | 1.27x |
| 32/32 | 4096+4096 | 0.168 | 0.134 | 1.25x |
| 32/32 | 2048+6144 | 0.242 | 0.191 | 1.27x |
| 32/32 | 1024+7168 | 0.280 | 0.219 | 1.28x |
| 32/32 | 2048x4 | 0.098 | 0.080 | 1.22x |
| 32/32 | 1024x8 | 0.113 | 0.096 | 1.18x |
| 32/32 | 8192x8 | 0.634 | 0.537 | 1.18x |
| 32/32 | 8192x16 | 1.254 | 1.114 | 1.13x |
| 32/32 | 8192x32 | 2.238 | 2.097 | 1.07x |


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
* Improved Blackwell prefill reliability across padded and partial
chunks.
  * Corrected final-state handling for sequences with no tokens.
  * Improved state loading and storing for Blackwell layouts.
  * Enhanced numerical handling for inverse calculations and edge cases.

* **Performance**
* Reworked kernel processing and staging to improve execution
efficiency.
  * Optimized compilation settings for faster runtime performance.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [6258e52](https://github.com/flashinfer-ai/flashinfer/commit/6258e5220dbc0f91df4f9f224257cda0b71bcbb5)

- **作者**: Jimmy Zhou
- **时间**: 2026-07-27T16:40:58Z
- **提交信息**: Revert PR 4122 (#4171)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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

* **Compatibility**
* Updated GPU architecture support and kernel selection across
attention, GEMM, MoE, quantization, and sampling workloads.
* Removed dedicated support for select SM107/10.7a builds and refreshed
compatible architecture targets.
* NVFP4 KV-cache operations now validate scale factors without an
additional SM107 restriction.

* **Bug Fixes**
* Improved TensorRT-LLM kernel compatibility and shared-memory
configuration.
* Improved optional backend detection and reduced failures in
environments with limited runtime support.

* **Documentation**
* Updated installation examples to reflect the revised CUDA architecture
list.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3888
- **最后更新**: 2026-07-27T18:15:45Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: William Lin

## AI分析总结

根据提交记录和项目背景（FastVideo 是一个面向视频生成/处理的工具库，注重文档和易用性），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **文档更新**：完善支持矩阵，覆盖所有已注册模型。
- **功能新增**：添加 LTX-2 微调示例配置（recipes）。

### 2. 关键变更点与项目方向的关系
- **`[docs]: cover all registered models in the support matrix (#1641)`**  
  将文档中“支持矩阵”更新为完整列出所有已注册模型。这直接对应 FastVideo 的“文档优先”路线（如 README 强调快速开始和详细文档），确保用户能一目了然地看到项目适配的模型范围，降低使用困惑。
- **`[misc]: add LTX-2 fine-tuning example recipes (#1645)`**  
  新增了针对 LTX-2 模型进行微调的示例配置。与项目“扩展模型支持”和“提供现成实践”的目标一致，使用户能直接复用配方进行微调，推动更多模型被社区使用。

### 3. 对项目的影响和潜在意义
- **提升可用性**：模型支持矩阵的完整覆盖，减少用户“这个模型是否被支持”的疑问，增强项目可信度。
- **降低上手门槛**：LTX-2 微调示例提供了一个即用模板，鼓励开发者尝试新模型微调，有助于吸引更多贡献者和用户。
- **促进生态扩展**：通过提供具体模型的实践路径，为后续更多模型集成或定制化场景打下基础。

### 4. 值得关注的技术点
- **注册模型机制**：项目可能采用模型注册表（model registry）管理所有支持的模型，文档中的“support matrix”可能是代码自动生成的表格，确保文档与代码实际支持列表同步。
- **LTX-2 微调配方**：需留意复现步骤中使用的数据格式、超参数、训练脚本等是否与项目现有框架一致，可能隐含对特定硬件或训练策略的优化。

### 5. 基于项目背景，这些提交如何影响发展
- FastVideo 的 README 强调“快速开始”和“周开发会议”，说明项目处于快速发展期，注重社区协作。  
  - **文档完整化** 是项目成熟度的体现，有助于从早期用户扩展到更广泛的开发者群体，减少新手提问。  
  - **新增微调示例** 直接回应了“周开发会议”中可能提出的需求，通过具体案例促进社区讨论（如 LTX-2 的微调技巧、性能报告），形成“示例→反馈→改进”的良性循环。  
- 整体上，这两次更新巩固了项目的基础设施（文档）和实用价值（微调示例），是项目从“核心功能”走向“易用生态”的典型步骤。

## 详细提交记录

### [1801512](https://github.com/hao-ai-lab/FastVideo/commit/18015128183c17ac6cab2052d6d65c4d9e9ec370)

- **作者**: William Lin
- **时间**: 2026-07-27T18:13:53Z
- **提交信息**: [docs]: cover all registered models in the support matrix (#1641)

### [5ae05b0](https://github.com/hao-ai-lab/FastVideo/commit/5ae05b032e3b4f98b57439a7878ab744203d06e9)

- **作者**: William Lin
- **时间**: 2026-07-27T18:11:49Z
- **提交信息**: [misc]: add LTX-2 fine-tuning example recipes (#1645)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34166
- **最后更新**: 2026-07-27T22:11:29Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Linoy Tsaban, Sayak Paul

## AI分析总结

好的，我们来分析 `huggingface/diffusers` 仓库昨日的三条提交记录。

---

### **1. 主要更新类型**
- **功能新增**（提交 `2dabcc9`）：为 LoRA 训练添加了 **caption dropout** 和 **aspect ratio buckets** 支持（针对 `krea2` 和 `qwen-image` 模型）。
- **Bug 修复**（提交 `82610a5`）：修复了 CLI 测试中的问题，并跳过了变体（variant）未找到时的测试。
- **重构**（提交 `1c98c38`）：将训练相关的测试迁移到 **pytest** 框架。

---

### **2. 关键变更点及其与项目整体方向的关系**
- **LoRA 训练增强**：
  - 为 `krea2` 和 `qwen-image` 添加 caption dropout（文本条件随机丢弃）和 aspect ratio buckets（保持原始宽高比的图像分桶训练）。
  - **关系**：diffusers 项目致力于提供丰富的扩散模型微调工具（如 LoRA、DreamBooth）。此改动扩展了 LoRA 训练的能力，使其能处理更多样化的图像和文本条件，符合项目“易用且功能全面”的目标。
- **测试修复与迁移**：
  - 修复 CLI 命令测试，并迁移训练测试到 pytest。
  - **关系**：项目对测试基础设施的改进体现了对代码质量和可维护性的重视，为后续大规模功能开发提供更稳健的测试保障。

---

### **3. 对项目的影响和潜在意义**
- **对用户（开发者）**：
  - 使用 `krea2` 或 `qwen-image` 进行 LoRA 微调时，可直接利用 **caption dropout** 减少模型对文本的过拟合，生成结果更鲁棒；**aspect ratio buckets** 允许不同宽高比的图像无需裁剪即可训练，保留原始构图信息，提升生成质量。
- **对项目维护**：
  - 测试迁移到 pytest 使新的贡献者更容易编写测试（pytest 语法简洁），且 pytest 丰富的插件生态（如参数化、fixture）能提高测试效率和覆盖率。
  - 修复 CLI 测试避免了 CI 中断，保证发布流程稳定。
- **潜在意义**：这两项增强（尤其是 LoRA 新特性）可能推动社区在文生图模型上探索更灵活的微调策略，进一步提升 diffusers 作为微调工具链的竞争力。

---

### **4. 值得关注的技术点**
- **Caption Dropout**：一种正则化技术，训练时随机丢弃一定比例的文本 token 或整句，迫使模型从图像本身学习，增强文本‑图像对齐的鲁棒性。类似的原理在 DALLE‑2 或 CLIP 训练中也有应用。
- **Aspect Ratio Buckets**：将图像按宽高比（如 1:1, 4:3, 16:9）分桶，每个桶内图像保持原始尺寸（可能缩放后填充/裁剪），但训练时 batch 内图像分辨率一致。常见于 Stable Diffusion 社区的微调脚本（如 Kohya 的 LoRA 训练器），现被官方吸收，增加了兼容性和易用性。
- **pytest 迁移**：pytest 支持自动发现测试、简洁的断言、参数化测试，迁移后训练测试的编写和维护成本降低，同时通过 fixture 可以更干净地管理训练依赖（如模型加载、临时目录）。

---



## 详细提交记录

### [2dabcc9](https://github.com/huggingface/diffusers/commit/2dabcc9aa08aa5f6d82392dee5cbe93803cc5791)

- **作者**: Linoy Tsaban
- **时间**: 2026-07-27T18:59:21Z
- **提交信息**: [lora training] add caption dropout and aspect ratio buckets to krea2 and qwen-image (#14089)

### [82610a5](https://github.com/huggingface/diffusers/commit/82610a5463dc5fe29005fddac7d0aa5c7d5dd621)

- **作者**: Sayak Paul
- **时间**: 2026-07-27T12:31:34Z
- **提交信息**: [tests] fix some CLI command tests (#14302)

* fix cli tests.

* fix

* skip in case of variant not found

### [1c98c38](https://github.com/huggingface/diffusers/commit/1c98c38c313fc5cba8575efd4409bdc1354becdb)

- **作者**: Sayak Paul
- **时间**: 2026-07-27T11:35:42Z
- **提交信息**: [tests] migrate training tests to pytest. (#14267)

migrate training tests to pytest.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
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


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12766
- **最后更新**: 2026-07-27T12:43:09Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30804
- **最后更新**: 2026-07-27T22:20:53Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Liangsheng Yin, James Liu, Shangming Cai

## AI分析总结

分析生成失败

## 详细提交记录

### [3005af0](https://github.com/sgl-project/sglang/commit/3005af09412cedb988a5871a3441ae49424a13bb)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-27T21:56:42Z
- **提交信息**: Fix compressed-tensors NVFP4 MoE W13 layout (#32430)

### [8a311d1](https://github.com/sgl-project/sglang/commit/8a311d1c889244ab1f857d7df79de7e5f0a6891c)

- **作者**: Kangrui Du
- **时间**: 2026-07-27T19:05:13Z
- **提交信息**: [diffusion] fix: preserve tensor stride when offloading rollout weights to pinned host memory (#32420)

### [1da062f](https://github.com/sgl-project/sglang/commit/1da062f018ffc42bcc492a25f386923d7fe791e8)

- **作者**: James Liu
- **时间**: 2026-07-27T19:01:13Z
- **提交信息**: [Inkling] Add minimal DFLASH support (#31840)

### [7cae831](https://github.com/sgl-project/sglang/commit/7cae831e41c942f4514c2458c5840c6b5ac0dd81)

- **作者**: Yuhao Yang
- **时间**: 2026-07-27T17:52:41Z
- **提交信息**: Update mi35x ROCm image to k3-20260727 (#32559)

### [3ebb7c2](https://github.com/sgl-project/sglang/commit/3ebb7c2d0722d92515d19dff431ab9b9a44faa8d)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-27T16:23:43Z
- **提交信息**: docs: point Kimi-K3 references to public branch (#32547)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [7dafacc](https://github.com/sgl-project/sglang/commit/7dafacca494e2832a2f44309703db260828b979d)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-27T15:37:30Z
- **提交信息**: docs(cookbook): add the Kimi-K3 serving cookbook (#32542)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Mick <mickjagger19@icloud.com>
Co-authored-by: Baizhou Zhang <sobereddiezhang@gmail.com>
Co-authored-by: thomawan <thomawan@amd.com>
Co-authored-by: BBuf <1182563586@qq.com>

### [8d6549b](https://github.com/sgl-project/sglang/commit/8d6549bc4039d33635844495d86684677a4f0df8)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-27T13:31:04Z
- **提交信息**: [Attention Backend] Extend hpc_ops dynamic-scheduled decode to bf16 (#32304)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Halcyon <56064364+VAthree@users.noreply.github.com>

### [5656de2](https://github.com/sgl-project/sglang/commit/5656de2d9a95815bd2910eafc8ae0122ede1cd6e)

- **作者**: inkcherry
- **时间**: 2026-07-27T13:07:23Z
- **提交信息**: [PD] pool decode bootstrap HTTP sessions (#31543)

### [db9143e](https://github.com/sgl-project/sglang/commit/db9143ee08d1aee2f313ea44b6e35ec23454b5c3)

- **作者**: Peng Xingchen
- **时间**: 2026-07-27T11:19:38Z
- **提交信息**: [NPU] Fix MTP IndexShare warm-up for attention DP and prefill CP (#32210)

### [34454c0](https://github.com/sgl-project/sglang/commit/34454c06b891bffbd787afa4774151bfdf8b82ba)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-27T11:09:09Z
- **提交信息**: [Refactor] Tidy server_args.py section grouping and drop unused alias (#32496)

### [1d350aa](https://github.com/sgl-project/sglang/commit/1d350aaad3511920616a5cd16fbe413166b34a88)

- **作者**: Shangming Cai
- **时间**: 2026-07-27T10:15:47Z
- **提交信息**: fix(reasoning):  let --enable-strict-thinking works for DeepSeek-V4 (#32400)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [08af5ae](https://github.com/sgl-project/sglang/commit/08af5aea570a96f5edd9c1d9e0c28c690fdd842a)

- **作者**: Mick
- **时间**: 2026-07-27T09:34:29Z
- **提交信息**: optimize: optimize EmbeddingGemma prefill performance (#32383)

### [9a0bd24](https://github.com/sgl-project/sglang/commit/9a0bd24bed1828cb0c6728262580306f8fd8ec02)

- **作者**: Jackey Hua
- **时间**: 2026-07-27T07:49:58Z
- **提交信息**: model: serve bare Qwen3Model backbone natively as an embedding model (#32457)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [169fc1e](https://github.com/sgl-project/sglang/commit/169fc1e20cbf5c87c4f44e2bf1873249cb719d30)

- **作者**: McZyWu
- **时间**: 2026-07-27T07:40:49Z
- **提交信息**: [NPU] Acc fix for afmoe model introduced by topk refactor. (#31280)

### [c0f47a0](https://github.com/sgl-project/sglang/commit/c0f47a06fc8e8b7c9eec0e38018e6fb176fe1cb1)

- **作者**: McZyWu
- **时间**: 2026-07-27T07:12:38Z
- **提交信息**: [NPU] Determine the topk norm_type through scoring_func (#31393)

### [3d3ba4f](https://github.com/sgl-project/sglang/commit/3d3ba4f7468764a056b211c6fd6e2fdf4b9ba030)

- **作者**: Zheng Wengang
- **时间**: 2026-07-27T07:06:01Z
- **提交信息**: [BugFix][EPD] Fix Mooncake source-MR lifecycle for multi-TP /send (#32071)

### [082b2a1](https://github.com/sgl-project/sglang/commit/082b2a10b628700c8d5b76b5fa90b86c0981a89c)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-27T07:03:59Z
- **提交信息**: Add local ZIP uploader for whl releases (#32489)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
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


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87345
- **最后更新**: 2026-07-27T22:20:53Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 29
- **主要提交者**: Rui "Garry" Gao, Xiaochang Wu, Guan-Ming Chiu

## AI分析总结

分析生成失败

## 详细提交记录

### [53f6dd5](https://github.com/vllm-project/vllm/commit/53f6dd5c6f7725df4e5ac9441569860023100870)

- **作者**: fxmarty-amd
- **时间**: 2026-07-27T21:47:07Z
- **提交信息**: [CI][ROCm] Fix `test_ocp_mx_wikitext_correctness` reference value (#49690)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [99115fc](https://github.com/vllm-project/vllm/commit/99115fcdcde9736d4097ea15e7bbab368c405edf)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-27T21:29:08Z
- **提交信息**: [CI] Initialize DeepEP FP8 test weights (#49912)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [1053e24](https://github.com/vllm-project/vllm/commit/1053e248f02f453390fbaadbecd2b94beff2fbb4)

- **作者**: amd-sourjya
- **时间**: 2026-07-27T21:01:34Z
- **提交信息**: [ROCm][Quantization][5/N] Refactor quark_moe w8a8-int8 w/ oracle (#46765)

Signed-off-by: amd-sourjya <amd-sourjya@users.noreply.github.com>
Co-authored-by: amd-sourjya <amd-sourjya@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [b5bcb3c](https://github.com/vllm-project/vllm/commit/b5bcb3ce881e1d324ff7f6176ef27606558dbd74)

- **作者**: Wentao Ye
- **时间**: 2026-07-27T19:58:26Z
- **提交信息**: [Refactor] Remove dead code in multiple files (#49745)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [b2f9e4c](https://github.com/vllm-project/vllm/commit/b2f9e4caa49425d93667e01be5c9ad4c45bf81df)

- **作者**: Wentao Ye
- **时间**: 2026-07-27T19:56:52Z
- **提交信息**: [DSv4 Perf] Adaptive topk width, 1.0% E2E throughput improvement (#50004)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [831d384](https://github.com/vllm-project/vllm/commit/831d3848f16e21e652bf1c377d010c2b5fe76f37)

- **作者**: Andrea Tassi
- **时间**: 2026-07-27T19:48:35Z
- **提交信息**: [Core] Fail fast when /dev/shm is too small for the shm ring buffer (#48879)

Signed-off-by: Dr Andrea Tassi <andrea@verticular.uk>
Co-authored-by: Dr Andrea Tassi <andrea@verticular.uk>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [fd10e89](https://github.com/vllm-project/vllm/commit/fd10e8946d7b27d1f3070d4f58febd8eac1c3a4b)

- **作者**: Rishi Puri
- **时间**: 2026-07-27T19:03:58Z
- **提交信息**: [Test] Regression test for hybrid-Mamba eagle cache-peek in Mooncake connector (#43559) (#48361)

Signed-off-by: Rishi Puri <riship@nvidia.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [ed13deb](https://github.com/vllm-project/vllm/commit/ed13deb37622cf9f603596743642807561c7691d)

- **作者**: oops-oom
- **时间**: 2026-07-27T18:35:57Z
- **提交信息**: [Bugfix][CPU] Fall back to torch for unaligned swigluoai on NEON/vec MoE (#49985)

Signed-off-by: oops-oom <73481342@qq.com>
Co-authored-by: oops-oom <73481342@qq.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [99de48e](https://github.com/vllm-project/vllm/commit/99de48e98fe9570d52b733a545d27661929c170c)

- **作者**: Harry Mellor
- **时间**: 2026-07-27T18:32:32Z
- **提交信息**: Fix MLA padding and grouped topk routing in the Transformers modelling backend (#49982)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [bf2b45b](https://github.com/vllm-project/vllm/commit/bf2b45b5d6a991f47702d4d87c81bb0ef8619a65)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-27T18:25:50Z
- **提交信息**: [Attention] Integrate FlashAttention 4 SM100 headdim 256 support (#42669)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [8112b6c](https://github.com/vllm-project/vllm/commit/8112b6c9972067012e08ce4f0dbf1d1d9906dbe3)

- **作者**: Nick Hill
- **时间**: 2026-07-27T17:25:17Z
- **提交信息**: [MRV2] Always build attn metadata at capture time (#49364) (#49995)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [15d65f8](https://github.com/vllm-project/vllm/commit/15d65f86694ac647b139179f88c9d7aea0820108)

- **作者**: TobyJBell
- **时间**: 2026-07-27T17:06:46Z
- **提交信息**: [Bugfix] Changed speech to text chunk timestamp to cumulative approach (#41131)

Signed-off-by: Toby Bell <toby.bell1702@hotmail.co.uk>

### [e3c2fc3](https://github.com/vllm-project/vllm/commit/e3c2fc3b3ca3f41466126cd2aa0b228eb8465844)

- **作者**: Connor Carpenter
- **时间**: 2026-07-27T16:53:27Z
- **提交信息**: [Rust Frontend][gRPC] Add server and model discovery (#49491)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [2b465b2](https://github.com/vllm-project/vllm/commit/2b465b2c42e6f7d37fbbc67956dc9741e832dc29)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-27T16:51:37Z
- **提交信息**: [Misc][PD] Nixl cleanup `get_backend_aware_kv_block_len` and `virtually_split_kv_in_blocks` (#49988)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [3f47a83](https://github.com/vllm-project/vllm/commit/3f47a8384d90a6e29b05b18d84942f8d7c895def)

- **作者**: yzong-rh
- **时间**: 2026-07-27T16:12:14Z
- **提交信息**: [Bugfix] Fix VLLM_ENFORCE_STRICT_TOOL_CALLING mutation in tests (#49846)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [04502de](https://github.com/vllm-project/vllm/commit/04502deca2f66b874d0fceae446c668c987413c0)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-07-27T15:57:55Z
- **提交信息**: [Perf] Hash videos by source bytes (#49607)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>
Signed-off-by: Guan-Ming Chiu <105915352+guan404ming@users.noreply.github.com>
Co-authored-by: Isotr0py <2037008807@qq.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d2ca300](https://github.com/vllm-project/vllm/commit/d2ca3002d93314a08bbddf9c6eb6ee78b1343407)

- **作者**: Song Zhixin
- **时间**: 2026-07-27T15:31:36Z
- **提交信息**: [MRV2][Performance] Skip no-op FP32 logits materialization (#47711)

Signed-off-by: jesse <szxfml@gmail.com>
Signed-off-by: Song Zhixin <szxfml@gmail.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [27d7061](https://github.com/vllm-project/vllm/commit/27d7061ef62b3d853b4d335baf8ea9b3c56d9bf3)

- **作者**: Umut Polat
- **时间**: 2026-07-27T14:52:59Z
- **提交信息**: [Bugfix] Restore truncate_prompt_tokens for Jina rerank/score online (#49963)

Signed-off-by: Umut Polat <52835619+umut-polat@users.noreply.github.com>

### [ef9975d](https://github.com/vllm-project/vllm/commit/ef9975d021448b99a5408e8c78a4c4f6b63443c7)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-07-27T14:37:54Z
- **提交信息**: [Bugfix] Reject pipeline parallelism for DiffusionGemma (#45828)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [56c96b0](https://github.com/vllm-project/vllm/commit/56c96b0d91f05140b61a2005c222d83e9ec042db)

- **作者**: Roberto L. Castro
- **时间**: 2026-07-27T14:25:37Z
- **提交信息**: [Perf] Tune LL BF16 Router GEMM (#48774)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [59a6b04](https://github.com/vllm-project/vllm/commit/59a6b0411d1817c712728a17fa8c2e0cdb4cf1f9)

- **作者**: Nick Hill
- **时间**: 2026-07-27T14:00:46Z
- **提交信息**: [Core] Fix internal LB load-balancing (#49204)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [dbccc5a](https://github.com/vllm-project/vllm/commit/dbccc5ae328d7b9168bc33b278a9125cfd89cc69)

- **作者**: Rui "Garry" Gao
- **时间**: 2026-07-27T13:42:35Z
- **提交信息**: [Model] Enable EVS for Qwen3.5 (#48912)

Signed-off-by: Rui "Garry" Gao <garrygaogg@gmail.com>

### [a89015c](https://github.com/vllm-project/vllm/commit/a89015c6df8eeb37a843b717c97a5be1355de83d)

- **作者**: liminfei-amd
- **时间**: 2026-07-27T13:24:42Z
- **提交信息**: [Perf] Make merge attention context count a runtime argument (#48739)

Signed-off-by: liminfei-amd <91481003+liminfei-amd@users.noreply.github.com>

### [96fa3f4](https://github.com/vllm-project/vllm/commit/96fa3f42c95acc75f40a8fddbc3a621c2355a30d)

- **作者**: neweyes
- **时间**: 2026-07-27T12:16:42Z
- **提交信息**: [Perf] Skip ll_bf16 router GEMM warmup for non-MoE models (#49659)

Signed-off-by: neweyes <328719365@qq.com>

### [81962bb](https://github.com/vllm-project/vllm/commit/81962bb6995eaebd1e49998c2a91c9e01e24da27)

- **作者**: rongfu.leng
- **时间**: 2026-07-27T12:12:23Z
- **提交信息**: [Bugfix]Reject invalid FlashInfer MNNVL workspaces (#49043)

Signed-off-by: lengrongfu <lenronfu@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [92e8518](https://github.com/vllm-project/vllm/commit/92e8518d376c3c9a6979da4d56ee6263ef6af630)

- **作者**: Harry Mellor
- **时间**: 2026-07-27T11:51:16Z
- **提交信息**: Improve Transformers modelling backend `fx` tracer (#49957)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [77cba02](https://github.com/vllm-project/vllm/commit/77cba0259f21dfc6f4f6298f54f3e43c9cc824c3)

- **作者**: Ronen Schaffer
- **时间**: 2026-07-27T10:29:57Z
- **提交信息**: [KV Offloading] Per-request tier filtering with TierFilter/TierMatcher (#48123)

Signed-off-by: Ronen Schaffer <ronen.schaffer@ibm.com>

### [30fbd05](https://github.com/vllm-project/vllm/commit/30fbd055379ce4c5f26fcece6cfc90c5d8596f59)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-27T10:11:06Z
- **提交信息**: [ROCm] Use backend-default dot precision for ReplaySSM (#49909)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [0906123](https://github.com/vllm-project/vllm/commit/0906123953a5a253cc0cc4f26e548ca08ece102a)

- **作者**: TJian
- **时间**: 2026-07-27T10:05:46Z
- **提交信息**: [ROCm] [Model] Enable TML inkling (#48841)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [bc3629b](https://github.com/vllm-project/vllm/commit/bc3629b1c4760f7260d41a67e38ff460edbe22d7)

- **作者**: fxmarty
- **时间**: 2026-07-27T09:36:38Z
- **提交信息**: [ROCm][CI] Skip three torchao tests of gfx950 until `torchao==0.18` is released (#49732)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [312ea82](https://github.com/vllm-project/vllm/commit/312ea82e758a27a333e4254cc7669ae1a5d7c69e)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-27T09:23:12Z
- **提交信息**: [CI][ROCm] Make hf-xet reconstruction safe on shared NFS (#49837)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [394beb6](https://github.com/vllm-project/vllm/commit/394beb633b0b5b5d68aed3d2f2b5c1477e756d80)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-27T09:18:01Z
- **提交信息**: [Bugfix][ROCm] Use batch DMA for CPU KV cache loads (#49843)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [7f599d7](https://github.com/vllm-project/vllm/commit/7f599d78546819948c32f2b23d913507bbb38875)

- **作者**: haoyangli0109
- **时间**: 2026-07-27T08:38:45Z
- **提交信息**: [communication] [bugfix] fix quickreduce acc error in cudagraph mode (#46913)

Signed-off-by: Haoyang Li <lihaoyang0109@gmail.com>
Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [eb290ab](https://github.com/vllm-project/vllm/commit/eb290ab673c8f3ff87648cd8e4cd60f50fe7b301)

- **作者**: Li, Jiang
- **时间**: 2026-07-27T08:32:23Z
- **提交信息**: [Bugfix][CPU] Zero-pad MoE intermediate size for grouped-gemm TP alignment (#49591)

Signed-off-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [cbc3a87](https://github.com/vllm-project/vllm/commit/cbc3a872005d595493b546acf46f94a9c9f68cbb)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-27T07:49:11Z
- **提交信息**: [Tokenizer] Use HF config for HF tokenizers (#49907)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [afc9452](https://github.com/vllm-project/vllm/commit/afc94523c965a61bd6869287c798b2a45f2c205e)

- **作者**: liuzhenwei
- **时间**: 2026-07-27T07:28:02Z
- **提交信息**: [XPU][CI] Use platform device in InputBatch V2 test (#49939)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [8061dc2](https://github.com/vllm-project/vllm/commit/8061dc26bd0b37a2ad58068b99d072be5a0e5f47)

- **作者**: Xiaochang Wu
- **时间**: 2026-07-27T07:02:48Z
- **提交信息**: [Bugfix] Normalize sparse MLA warmup compression ratios (#49392)

Signed-off-by: Wu, Xiaochang <xiaochang.wu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-28
**监控日期**: 2026-07-27
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5710
- **最后更新**: 2026-07-27T20:00:20Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 11
- **主要提交者**: Yueqian Lin, xsmccc, LHXuuu

## AI分析总结

以下是基于 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型
- **新模型支持**：新增 `MammothModa2-Dev` 模型（#5411）。
- **性能优化**：MiniCPM-o 单 GPU 启动内存降低（#5447）、多模态编码器内存优化（#5188）；新增 `Skip-Softmax` 的 TRT-LLM 扩散注意力后端（#5283）。
- **Bug 修复**：实时服务中断会话循环问题（#5388）、连接器异步块发送处理器刷新（#5414）、MiniCPM-o 无异步块时的音频输出恢复（#5455）、部署配置中 `sequence_parallel_size` 缺失（#5449）。
- **重构与架构改进**：Ming-TTS 说话人提取与缓存移至 Stage-0（#5351）；MammothModa2-dev 示例路径重构（#5454）；添加模型运行器缺失测试（#5333）。
- **依赖升级**：Rebase 至 vLLM 0.26.0（#5443）。
- **适配与兼容性**：NPU 上 HunyuanImage3 扩散 FusedMoE 适配 vLLM ≥0.24.0（#5167）；从 `VllmOmniConfig` 读取 stage 元数据（#5343）。

### 2. 关键变更点与项目方向关系
- **增加多模态模型覆盖**：`MammothModa2-Dev` 是新的全模态模型，与项目“全模态服务”目标一致，扩展支持的模型种类。
- **降低部署门槛**：MiniCPM-o 的内存优化（单 GPU 启动 & 编码器）直接实现 “cheap” 目标，让更小硬件能运行多模态模型。
- **提升服务稳定性**：实时会话修复、连接器刷新等 Bug 修复提高了生产环境可靠性，符合 “easy” 和 “fast” 的期望。
- **集成最新基础设施**：Rebase 到 vLLM 0.26.0 确保与上游性能优化和安全更新同步，保持与 vLLM 生态的兼容性。
- **架构前瞻**：

## 详细提交记录

### [d4a5eaa](https://github.com/vllm-project/vllm-omni/commit/d4a5eaac9081cb8345aa535aba4eb4218d8730dc)

- **作者**: Yueqian Lin
- **时间**: 2026-07-27T17:04:17Z
- **提交信息**: [Bugfix][Realtime] Stop disconnected sessions from cycling through stages (#5388)

Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Co-authored-by: Sy03 <1370724210@qq.com>

### [8f11516](https://github.com/vllm-project/vllm-omni/commit/8f115164c236e140755b82f26edc7d8567de7757)

- **作者**: Yueqian Lin
- **时间**: 2026-07-27T16:04:08Z
- **提交信息**: [Bugfix][Connectors] Flush processor tail on terminal async-chunk sends (#5414)

Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [cbab1d4](https://github.com/vllm-project/vllm-omni/commit/cbab1d4d8f814e48ee691b69ac4cee9d0419f218)

- **作者**: Zhou Taichang
- **时间**: 2026-07-27T15:35:49Z
- **提交信息**: [Rebase] Rebase to vllm 0.26.0 (#5443)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Signed-off-by: tzhouam <tzhouam@gmail.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: tzhouam <tzhouam@gmail.com>

### [fb89ab4](https://github.com/vllm-project/vllm-omni/commit/fb89ab43ead813afa8a5580f8aa986f2b111771c)

- **作者**: LHXuuu
- **时间**: 2026-07-27T14:55:47Z
- **提交信息**: [Refactor][Ming-TTS] Move speaker extraction and caching to Stage-0 (#5351)

Signed-off-by: LHXuuu <xulianhao.xlh@antgroup.com>
Co-authored-by: Yuanheng Zhao <54058983+yuanheng-zhao@users.noreply.github.com>

### [7762d66](https://github.com/vllm-project/vllm-omni/commit/7762d664d8550bd21cd71f092c56b53e679d5a74)

- **作者**: SYLAR
- **时间**: 2026-07-27T14:48:11Z
- **提交信息**: [Attention] Add trtllm diffusion attention backend with Skip-Softmax (#5283)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

### [4dd1b47](https://github.com/vllm-project/vllm-omni/commit/4dd1b47f478a09f3b1ab3841e30a38bcc81fd480)

- **作者**: Wang  fuyin
- **时间**: 2026-07-27T14:44:06Z
- **提交信息**: [Config] Read stage metadata from VllmOmniConfig (#5343)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e108cbb](https://github.com/vllm-project/vllm-omni/commit/e108cbb51049046275deefa5eb7a9668d22133be)

- **作者**: jiangmengyu18
- **时间**: 2026-07-27T14:41:34Z
- **提交信息**: [NPU][HunyuanImage3] Adapt diffusion FusedMoE for vLLM >= 0.24.0 (#5167)

Signed-off-by: betta18 <jiangmengyu1@huawei.com>
Signed-off-by: jiangmengyu18 <56633611+jiangmengyu18@users.noreply.github.com>
Co-authored-by: betta18 <jiangmengyu1@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [82172b1](https://github.com/vllm-project/vllm-omni/commit/82172b112d727c32a8ad8504ba9d3e11b6b50c38)

- **作者**: ruirui(rein) yang
- **时间**: 2026-07-27T14:19:46Z
- **提交信息**: [BugFix][MiniCPM-o] Restore audio output without async chunk (#5455)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e9bc7fc](https://github.com/vllm-project/vllm-omni/commit/e9bc7fc06a39eb7abc57e2b984497ab493df0b4a)

- **作者**: 汪志鹏
- **时间**: 2026-07-27T14:11:49Z
- **提交信息**: [Refactor]: Mammothmoda2-dev use x_to_text.py in examples (#5454)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [8001bb1](https://github.com/vllm-project/vllm-omni/commit/8001bb155dae5798a1ae891ae2529a314c6ee99a)

- **作者**: zzh
- **时间**: 2026-07-27T09:15:08Z
- **提交信息**: Fix missing sequence_parallel_size in deploy config output (#5449)

Signed-off-by: zzh <943967662@qq.com>

### [88b7ca2](https://github.com/vllm-project/vllm-omni/commit/88b7ca2ffa6ad9192a9175b36b15948e1f78febd)

- **作者**: 汪志鹏
- **时间**: 2026-07-27T09:01:54Z
- **提交信息**: [Model] Support MammothModa2-Dev (#5411)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [5b23054](https://github.com/vllm-project/vllm-omni/commit/5b230541c90b4ba883d3739dd1ed708f9275b656)

- **作者**: rein yang
- **时间**: 2026-07-27T08:37:25Z
- **提交信息**: [Deploy] Reduce MiniCPM-o single-GPU startup memory (#5447)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>

### [776424f](https://github.com/vllm-project/vllm-omni/commit/776424f0de8a69fc2f5da0c4f3cf767f96855f90)

- **作者**: Zhou Taichang
- **时间**: 2026-07-27T08:24:47Z
- **提交信息**: [Refactor][WIP] Add missing test for modelrunner (G1/N) (#5333)

Signed-off-by: Taichang Zhou <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [d688aa8](https://github.com/vllm-project/vllm-omni/commit/d688aa82fcfd4c09ab1d708f90ba225a7bc04527)

- **作者**: xsmccc
- **时间**: 2026-07-27T07:24:51Z
- **提交信息**: [Model] Optimize MiniCPM-o multimodal encoder memory (#5188)

Signed-off-by: xsmccc <247721718+xsmccc@users.noreply.github.com>
Co-authored-by: xsmccc <247721718+xsmccc@users.noreply.github.com>

---
