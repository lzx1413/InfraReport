# GitHub Stars 合并报告 - 2026-07-31

**合并日期**: 2026-08-01
**监控日期**: 2026-07-31
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


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2117
- **最后更新**: 2026-07-31T08:22:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Zhang1Sheng

## AI分析总结

## 提交分析：9651e80

### 1. 主要更新类型

- **性能优化 + Bug修复**（以 `perf` 和 `fix` 双重标签标记），属于典型的硬件适配层调优改动。

### 2. 关键变更点

- **AscendC GDN 内核的变长元数据预计算**:将原本运行时重复计算的 `varlen metadata` 移至预处理阶段，减少内核执行期间的计算开销。
- **Qwen3.5 的 NPU 同步优化**:针对昇腾 NPU 上的同步机制进行精简，降低同步等待带来的性能损耗。

### 3. 对项目的影响与潜在意义

- **强化多硬件后端的工程完备性**:直接提升了昇腾（Ascend）平台上的算子执行效率，使 VeOmni 不仅是"配方"层面的抽象，更深入到硬件内核级别的可运行优化。
- **弥补训练框架与国产芯片之间的性能鸿沟**:通过内核级优化和同步机制调整，缩小平移运行时的性能差距，增强 NPU 作为训练后端的实用性。

### 4. 值得关注的技术点

- `varlen metadata` 的预计算:说明该 GDN 内核服务于**变长序列**场景（常见于多模态或长序列模型），预计算是一种典型的访存/计算权衡策略。
- `NPU sync` 优化:针对昇腾硬件的同步语义与 GPU 不同，单独优化说明该提交来自真实 NPU 环境下的实测调优，而非简单的 API 替换。

### 5. 项目发展方向的启示

- VeOmni 的"**模型中心配方**"愿景正在从策略/配置层面的抽象，走向**硬件感知的算子级实现**——即同一个模型配方在不同硬件上会获得对应的底层优化路径。
- 对 Qwen3.5 的专门优化暗示项目正在积极支持前沿开源模型在非 NVIDIA 硬件上的高效训练，这是扩大生态覆盖面的关键一步。
- 若后续持续出现类似内核级优化提交，表明项目正在从研究框架向**可在生产环境中落地的多后端训练系统**演进。

## 详细提交记录

### [9651e80](https://github.com/ByteDance-Seed/VeOmni/commit/9651e80750a7d204d69423d71063c2987b03bf08)

- **作者**: Zhang1Sheng
- **时间**: 2026-07-31T08:19:52Z
- **提交信息**: [perf, ops, model] fix: precompute varlen metadata for AscendC GDN kernels and optimize NPU sync for Qwen3.5 (#999)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2550
- **最后更新**: 2026-07-31T09:23:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
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


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6073
- **最后更新**: 2026-07-31T20:50:08Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: kangbintNV, akhilg-nv, Brian K. Ryu

## AI分析总结

根据提供的提交记录，以下是对仓库 `flashinfer-ai/flashinfer` 昨日提交的 1/1 批记录分析总结：

---

### 1. 主要更新类型

- **Bug 修复**（1 条）：修复 CI Docker 镜像构建中 pip 自动切换 PyTorch CUDA 版本导致 JIT 链接失败的问题。
- **文档更新**（1 条）：完善 Ulysses 通信器与 MoE EP（Expert Parallelism）相关 API 文档。
- **性能优化**（1 条）：优化 `trtllm_fmha_v2` FP8 因果注意力中的 q-tile 调度策略。

整体以性能优化为核心，辅以 CI 稳定性和文档完善，属于混合型提交。

---

### 2. 关键变更点及与项目方向的关系

- **Docker/CI 依赖锁定** (`e9bb80f`)：
  - 问题：在 CUDA 12.9 容器中，pip 因 `cuda-python` 依赖冲突回溯，将 `torch` 悄悄替换为 PyPI 上的 CUDA 13 wheel，导致 FlashInfer JIT 模块链接的 `libcublasLt.so.12` 与 torch 返回的 cuBLAS-13 句柄不兼容，触发 `CUBLAS_STATUS_NOT_INITIALIZED`。
  - 修复：在 `requirements.txt` 前预先固定 `cuda-python` 主版本，对已安装的 `+cuXXX` torch 使用 `PIP_CONSTRAINT` 强制约束，并在构建末尾断言 torch/cuda-python 与镜像 CUDA 大版本一致。
  - 与项目关系：FlashInfer

## 详细提交记录

### [e9bb80f](https://github.com/flashinfer-ai/flashinfer/commit/e9bb80f9fd4194a3a74bc9e1ea9f5d1c8bb77b11)

- **作者**: Brian K. Ryu
- **时间**: 2026-07-31T20:49:43Z
- **提交信息**: fix(docker): stop pip from swapping the +cuXXX torch in CI image (#4284)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The latest cu12 CI image `flashinfer-ci-cu129:20260728-e63fc61` shipped
with `torch 2.13.0+cu130` inside a CUDA 12.9 container.
  
On a clean build, `cuda-python>=12.0` (requirements.txt) resolves to
13.3.x, whose `cuda-bindings~=13.3.1` conflicts with the `+cu129`
torch's `cuda-toolkit==12.9.1`. pip backtracks on `torch` (also unpinned
in requirements.txt) and swaps in the PyPI CUDA-13 wheel. The later
`cuda-python==12.*` restores cuda-python but not torch.

FlashInfer's JIT modules link `libcublasLt.so.12`, but
`torch.cuda.current_blas_handle()` now returns a cuBLAS-**13** handle,
which cuBLASLt 12 rejects with `CUBLAS_STATUS_NOT_INITIALIZED`, which
was observed in the CI of #4201

**The Fix**
1. Pin `cuda-python` to the image's CUDA major **before**
`requirements.txt` (keeping the existing pin after it, since
`nvshmem4py-cu12` pins `cuda-python<=12.9`).
2. `PIP_CONSTRAINT` the installed `+cuXXX` torch for the rest of the
build, so a re-resolution fails loudly instead of silently switching
CUDA major.
3. Assert at end of build that torch and cuda-python match the image's
CUDA major.

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

* **Bug Fixes**
* Improved installation reliability for CUDA-enabled Python
environments.
* Ensured PyTorch and CUDA Python packages match the image’s CUDA major
version.
  * Added support for compatible CUDA 12 and CUDA 13 packages.
  * Added validation to detect incompatible CUDA package installations.
  * Preserved required CUDA-specific cuDNN and CUTLASS components.

* **Chores**
* Updated CUDA 13.2 images to use the stable package channel for more
predictable builds.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [668a1ba](https://github.com/flashinfer-ai/flashinfer/commit/668a1ba1ca86432c79f6adad37ecfce8d06ec083)

- **作者**: kangbintNV
- **时间**: 2026-07-31T10:01:40Z
- **提交信息**: docs: improve Ulysses communicator and MoE EP docs (#4240)

## 📌 Description

Fixes the NEW documentation issues reported by the comm doc check.

Changes:
- document MoE EP environment variables in `CLAUDE.md`
- keep Ulysses topology helper functions documented under the topology
API section without marking them as `@flashinfer_api`
- add missing parameter documentation for Ulysses communicator/raw A2A
APIs
- add missing parameter documentation for
`MixedCommHandler.checkpoint_restore`

## 🔍 Related Issues

N/A

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
- [ ] All tests are passing (`unittest`, etc.).

Validation:
- `git diff --check`
- `python3 -m compileall flashinfer/comm/ulysses.py
flashinfer/comm/ulysses_topology.py flashinfer/comm/mixed_comm.py`
- AST check for the reported decorator/docstring/env-var items

## Reviewer Notes

The Ulysses topology helper functions are intentionally documented but
remain internal and are not marked with `@flashinfer_api`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Documentation**
* Added quick-reference documentation for three MoE EP environment
variables.
* Expanded Ulysses communication API documentation with parameters,
tensor shapes, backend modes, device and dtype requirements, and return
semantics.
* Clarified topology probing, backend selection, and checkpoint
restoration behavior.
  * Improved API reference generation for Ulysses backend utilities.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [dca5546](https://github.com/flashinfer-ai/flashinfer/commit/dca55465f65ddd8513f79007b3482e9f348e62b3)

- **作者**: akhilg-nv
- **时间**: 2026-07-31T07:26:24Z
- **提交信息**: perf: optimize trtllm_fmha_v2 fp8 causal attention q-tile scheduling & decoding for uniform seqlen (#3575)

<!-- .github/pull_request_template.md -->

## 📌 Description

The default logical order q-tile scheduling computes the heaviest (most
work) tiles last in the case of causal attention (these tiles have the
longest KV to attend to). We currently enable reverse q-tile scheduling
within heads. However, if we know the input has uniform seq_len, we can
schedule q-tiles in reverse _globally_ across all heads. This has two
perf benefits:

1. For smaller seq-len problems, reducing the idle time of straggler
tiles at the end can have a more significant perf benefit.
2. Previously, we do an O(b) loop over `cu_q_seqlens` for every tile to
find which batch element it belongs to. For uniform seqlens, batch
membership can be computed directly in O(1) with integer division. This
matters at large batch sizes where the loop overhead is significant
relative to per-tile compute work.

## Performance Analysis

### Before & After Comparison
H200, qwen3-8b (32 Q heads / 8 KV heads, D=128), FP8 Q + paged FP8 KV,
causal prefill
Reuse r means q_len = (1-r) * seqlen new tokens attending to a
seqlen-long KV cache.
baseline represents per-head reversal (includes #3760)
                                                                  
| bs | seqlen | reuse | no-fix (us) | fix (us) | speedup | dominant
optimization |

|------|--------|-------|-------------|-----------|---------|------------------------|
| 1 | 1024 | 0% | 29.54 | 23.05 | 1.28x | global reverse-Q |
| 1 | 1024 | 75% | 18.27 | 18.40 | 0.99x | global reverse-Q |
| 1 | 2048 | 0% | 67.65 | 56.35 | 1.20x | global reverse-Q |
| 1 | 2048 | 75% | 27.81 | 27.98 | 0.99x | global reverse-Q |
| 1 | 4096 | 0% | 200.63 | 186.22 | 1.08x | global reverse-Q |
| 1 | 4096 | 75% | 85.69 | 80.61 | 1.06x | global reverse-Q |
| 1 | 8192 | 0% | 712.61 | 683.80 | 1.04x | global reverse-Q |
| 1 | 8192 | 75% | 309.27 | 297.05 | 1.04x | global reverse-Q |
| 1 | 16384 | 0% | 2613.81 | 2616.19 | 1.00x | baseline |
| 1 | 16384 | 75% | 1177.90 | 1175.85 | 1.00x | baseline |
| 1 | 32768 | 0% | 10220.14 | 10208.78 | 1.00x | baseline |
| 1 | 32768 | 75% | 4593.89 | 4596.09 | 1.00x | baseline |
| 1 | 65536 | 0% | 40979.19 | 41132.69 | 1.00x | baseline |
| 1 | 65536 | 75% | 18190.07 | 18130.69 | 1.00x | baseline |
| 8 | 1024 | 0% | 144.00 | 130.91 | 1.10x | global reverse-Q |
| 8 | 1024 | 75% | 53.70 | 52.07 | 1.03x | global reverse-Q |
| 8 | 2048 | 0% | 428.77 | 431.20 | 0.99x | baseline |
| 8 | 2048 | 75% | 179.45 | 179.50 | 1.00x | baseline |
| 8 | 4096 | 0% | 1531.95 | 1493.30 | 1.03x | baseline |
| 8 | 4096 | 75% | 648.73 | 646.80 | 1.00x | baseline |
| 8 | 8192 | 0% | 5492.92 | 5425.48 | 1.01x | baseline |
| 8 | 8192 | 75% | 2387.58 | 2345.91 | 1.02x | baseline |
| 8 | 16384 | 0% | 20922.64 | 20887.59 | 1.00x | baseline |
| 8 | 16384 | 75% | 9279.48 | 9314.80 | 1.00x | baseline |
| 8 | 32768 | 0% | 82992.32 | 82467.46 | 1.01x | baseline |
| 8 | 32768 | 75% | 36291.18 | 36217.11 | 1.00x | baseline |
| 8 | 65536 | 0% | 331989.68 | 331463.10 | 1.00x | baseline |
| 8 | 65536 | 75% | 144711.02 | 144451.89 | 1.00x | baseline |
| 128 | 1024 | 0% | 3075.17 | 2206.18 | 1.39x | O(1) decode |
| 128 | 1024 | 75% | 1035.22 | 788.26 | 1.31x | O(1) decode |
| 128 | 2048 | 0% | 8394.99 | 6978.02 | 1.20x | O(1) decode |
| 128 | 2048 | 75% | 3098.25 | 2701.66 | 1.15x | O(1) decode |
| 128 | 4096 | 0% | 26582.22 | 23500.72 | 1.13x | O(1) decode |
| 128 | 4096 | 75% | 10578.38 | 10037.62 | 1.05x | O(1) decode |
| 128 | 8192 | 0% | 95111.76 | 87358.46 | 1.09x | O(1) decode |
| 128 | 8192 | 75% | 40390.40 | 37379.09 | 1.08x | O(1) decode |
| 1024 | 1024 | 0% | 98662.79 | 17425.83 | 5.66x | O(1) decode |
| 1024 | 1024 | 75% | 26737.20 | 6208.66 | 4.31x | O(1) decode |
| 1024 | 2048 | 0% | 214207.16 | 55237.25 | 3.88x | O(1) decode |
| 1024 | 2048 | 75% | 61502.07 | 21421.72 | 2.87x | O(1) decode |
| 1024 | 4096 | 0% | 500318.30 | 187036.71 | 2.67x | O(1) decode |
| 1024 | 4096 | 75% | 153684.34 | 78563.73 | 1.96x | O(1) decode |

### Ablation: Measuring L2 gate heuristic with Q vs KV seqlen

We gate the global reverse-Q scheduling behind an estimate of whether
the entire KV working set fits in L2 cache. This scheduling pattern has
concurrently running CTAs compute tiles from different heads, each
streaming different KV - if the combined working set is too large to fit
in cache, this will force eviction and re-fetching from HBM, resulting
in a net performance loss.

With prefix-caching or chunked prefill, the query seqlen can be much
smaller than the KV cache it attends to. Estimating using the q-seqlen
can underestimate the KV cache size and enable the optimization in cases
where memory will thrash, hurting performance. Hence, we estimate the
optimization gate using the max KV seqlen, and number of KV heads
(accounting for GQA).

For the following problem sizes, the q-gate heuristic would allow global
reverse-q scheduling, while gating with the kv seqlen does not.

| bs | seqlen | reuse | KV size | fix, kv-gate (us) | fix, q-gate (us) |
q-gate vs kv-gate |

|----|--------|-------|---------------------|-------------|-------------------|------------------|
| 1 | 16384 | 75% | 33.5 MB (fits L2, but fails 2x headroom heuristic) |
1175.85 | 1177.45 | 1.00x |
| 1 | 32768 | 75% | 67 MB (exceeds L2) | 4596.09 | 4712.94 | 0.97x |
| 8 | 2048 | 75% | 33.5 MB (fits L2, but fails 2x headroom heuristic) |
179.50 | 181.49 | 0.99x |
| 8 | 4096 | 75% | 67 MB (exceeds L2) | 646.80 | 678.89 | 0.95x |

### Unit Benchmark vs Baseline and FA3

Uses an internal benchmarking harness

Repro: `python benchmark.py --backends fmha_v2,fmha_v2_native_paged,fa3
--model qwen3-8b --hw h200 --dtype fp8 --tp 1 --batch-sizes 1,8,128
--seq-lens 4096,8192,16384,32768,65536,128000 --mode prefill --graph
--reuse-ratios 0,0.75`
- Backends: fmha_v2, fmha_v2_native_paged, fa3
- Model: qwen3-8b
- Hardware: h200
- Dtypes: fp8
- TP sizes: [1]
- Modes: ['prefill']
- Reuse ratios: [0.0, 0.75]
- CUDA graphs: ON 
- backends: fmha_v2_native_paged is roughly equivalent to flashinfer
release 0.6.14. FA3 is tri-dao's implementation, not the fa3 path in
flashinfer.

#### Charts

<img width="1484" height="643" alt="image"
src="https://github.com/user-attachments/assets/e3f54af2-337a-46eb-97ef-bbee09dcfc1b"
/>

<img width="1484" height="643" alt="image"
src="https://github.com/user-attachments/assets/a204e9c1-3773-4825-b2c8-5264a57e4e94"
/>

<img width="1934" height="643" alt="image"
src="https://github.com/user-attachments/assets/a4bbe3c2-8e35-4216-bf22-7f001aec9649"
/>

#### Comprehensive Perf Table

| Batch | SeqLen | Reuse | fmha_v2 (µs) | fmha_v2 TFLOPS |
fmha_v2_native_paged (µs) | fmha_v2_native_paged TFLOPS | fa3 (µs) | fa3
TFLOPS |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 4096 | 0% | **176.61** | **1556.43** | 241.91 | 1136.29 | 211.06 |
1302.38 |
| 1 | 4096 | 75% | **81.51** | **843.12** | 106.83 | 643.24 | 92.14 |
745.79 |
| 1 | 8192 | 0% | **682.77** | **1610.37** | 827.22 | 1329.17 | 779.32 |
1410.86 |
| 1 | 8192 | 75% | **301.10** | **912.91** | 366.72 | 749.55 | 346.28 |
793.81 |
| 1 | 16384 | 0% | **2682.01** | **1639.83** | 3041.99 | 1445.78 |
2995.73 | 1468.10 |
| 1 | 16384 | 75% | **1186.19** | **926.93** | 1370.05 | 802.53 |
1325.75 | 829.35 |
| 1 | 32768 | 0% | **10425.80** | **1687.37** | 11859.58 | 1483.37 |
12104.85 | 1453.32 |
| 1 | 32768 | 75% | **4575.19** | **961.28** | 5556.91 | 791.46 |
5366.06 | 819.60 |
| 1 | 65536 | 0% | **40726.10** | **1727.85** | 46582.26 | 1510.63 |
47011.47 | 1496.84 |
| 1 | 65536 | 75% | **18060.43** | **974.07** | 20826.16 | 844.72 |
21291.12 | 826.27 |
| 1 | 128000 | 0% | **156669.65** | **1713.39** | 179025.46 | 1499.43 |
181194.70 | 1481.48 |
| 1 | 128000 | 75% | **70141.73** | **956.76** | 79600.64 | 843.07 |
80303.97 | 835.69 |
| 8 | 4096 | 0% | **1511.78** | **1454.59** | 1674.89 | 1312.94 |
1709.11 | 1286.65 |
| 8 | 4096 | 75% | **652.87** | **842.07** | 712.15 | 771.97 | 718.33 |
765.32 |
| 8 | 8192 | 0% | **5599.38** | **1570.91** | 6202.37 | 1418.18 |
6367.32 | 1381.44 |
| 8 | 8192 | 75% | **2422.92** | **907.59** | 2698.08 | 815.03 | 2795.07
| 786.75 |
| 8 | 16384 | 0% | **21221.78** | **1657.94** | 24217.44 | 1452.85 |
24156.83 | 1456.50 |
| 8 | 16384 | 75% | **9332.31** | **942.54** | 10354.94 | 849.46 |
10822.69 | 812.75 |
| 8 | 32768 | 0% | **83444.66** | **1686.60** | 94945.36 | 1482.30 |
96524.73 | 1458.05 |
| 8 | 32768 | 75% | **36722.86** | **958.11** | 41739.18 | 842.96 |
42043.73 | 836.85 |
| 8 | 65536 | 0% | **332198.46** | **1694.62** | 376604.80 | 1494.80 |
383431.81 | 1468.19 |
| 8 | 65536 | 75% | **143286.32** | **982.21** | 163839.17 | 859.00 |
167547.72 | 839.98 |
| 8 | 128000 | 0% | **1268215.88** | **1693.31** | 1436317.87 | 1495.13
| 1461567.38 | 1469.30 |
| 8 | 128000 | 75% | **560619.29** | **957.64** | 634596.41 | 846.00 |
641308.44 | 837.15 |
| 128 | 4096 | 0% | **23941.04** | **1469.63** | 26728.22 | 1316.38 |
27044.40 | 1300.99 |
| 128 | 4096 | 75% | **9983.85** | **881.03** | 11000.45 | 799.61 |
11309.89 | 777.73 |
| 128 | 8192 | 0% | **88602.50** | **1588.41** | 100113.19 | 1405.78 |
102108.03 | 1378.32 |
| 128 | 8192 | 75% | **38049.23** | **924.71** | 42138.00 | 834.98 |
43289.22 | 812.77 |
| 128 | 16384 | 0% | **343959.58** | **1636.67** | 388339.39 | 1449.63 |
395420.68 | 1423.67 |
| 128 | 16384 | 75% | **147553.99** | **953.80** | 167629.66 | 839.57 |
170874.88 | 823.63 |
| 128 | 32768 | 0% | **1344904.24** | **1674.32** | 1524630.37 | 1476.95
| 1553335.69 | 1449.65 |
| 128 | 32768 | 75% | **585379.85** | **961.68** | 663073.49 | 849.00 |
676537.63 | 832.10 |

## Summary: Best Backend per Regime

| Dtype | Mode | SeqLen Range | Concurrency | Reuse | Best (wins) |
Median % Peak | 2nd Best (wins) | Median % Peak |
|---|---|---|---|---|---|---|---|---|
| fp8 | prefill | Short (<=4K) | Low (bs<=8) | No Reuse | **fmha_v2
(2/2)** | 38.0% | fa3 (0/2) | 32.7% |
| fp8 | prefill | Short (<=4K) | Low (bs<=8) | Reuse 75% | **fmha_v2
(2/2)** | 21.3% | fa3 (0/2) | 19.1% |
| fp8 | prefill | Short (<=4K) | Med (bs<=128) | No Reuse | **fmha_v2
(1/1)** | 37.1% | fmha_v2_native_paged (0/1) | 33.3% |
| fp8 | prefill | Short (<=4K) | Med (bs<=128) | Reuse 75% | **fmha_v2
(1/1)** | 22.3% | fmha_v2_native_paged (0/1) | 20.2% |
|  |  |  |  |  |  |  |  |  |
| fp8 | prefill | Medium (<=32K) | Low (bs<=8) | No Reuse | **fmha_v2
(6/6)** | 41.7% | fa3 (0/6) | 36.8% |
| fp8 | prefill | Medium (<=32K) | Low (bs<=8) | Reuse 75% | **fmha_v2
(6/6)** | 23.6% | fa3 (0/6) | 20.6% |
| fp8 | prefill | Medium (<=32K) | Med (bs<=128) | No Reuse | **fmha_v2
(3/3)** | 41.4% | fmha_v2_native_paged (0/3) | 36.6% |
| fp8 | prefill | Medium (<=32K) | Med (bs<=128) | Reuse 75% | **fmha_v2
(3/3)** | 24.1% | fmha_v2_native_paged (0/3) | 21.2% |
|  |  |  |  |  |  |  |  |  |
| fp8 | prefill | Long (>32K) | Low (bs<=8) | No Reuse | **fmha_v2
(4/4)** | 43.1% | fmha_v2_native_paged (0/4) | 37.8% |
| fp8 | prefill | Long (>32K) | Low (bs<=8) | Reuse 75% | **fmha_v2
(4/4)** | 24.4% | fmha_v2_native_paged (0/4) | 21.4% |

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

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

## Summary by CodeRabbit

* **New Features**
* Added new configuration flags to enable a faster path when Q sequence
lengths are uniform, and to optionally switch to a head-first balanced
scheduling order.

* **Performance Improvements**
  * Introduced an O(1) tile-id decoding fast path for uniform Q.
* Improved dynamic/variable-length handling by using the exact decoding
path only when Q is not padded.
* Refined launch heuristics with corrected sizing and an L2-cache-based
decision for head-first scheduling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Jimmy Zhou <79552142+jimmyzho@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3901
- **最后更新**: 2026-07-31T15:51:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34206
- **最后更新**: 2026-07-31T21:25:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 428
- **最后更新**: 2026-07-31T09:46:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12789
- **最后更新**: 2026-07-31T18:44:35Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31017
- **最后更新**: 2026-07-31T22:07:15Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 17
- **主要提交者**: YC Yen-Ching Tseng, Peng Wu, Danila Shtan

## AI分析总结

分析生成失败

## 详细提交记录

### [55b6769](https://github.com/sgl-project/sglang/commit/55b6769b0ede7a07704e707701c181d63f3126b0)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T22:06:59Z
- **提交信息**: config: read resolved config via namespace accessors (#33013)

### [4862edc](https://github.com/sgl-project/sglang/commit/4862edc85f7b5e4b0140103dea383d05029c5ded)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T22:06:22Z
- **提交信息**: runtime_context: record the publishing process role (#33012)

### [ab25532](https://github.com/sgl-project/sglang/commit/ab2553284aec27a09a1d8a878869e5573859bc22)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T22:05:41Z
- **提交信息**: config: preserve resolved config across nested publishes + mutation ratchets (#33011)

### [1d640aa](https://github.com/sgl-project/sglang/commit/1d640aaea2e2047885ab76ad711246b3c280b649)

- **作者**: Rain Jiang
- **时间**: 2026-07-31T22:02:28Z
- **提交信息**: bump dynamo-tokenizers to 1.7.0 (#32981)

### [70cec31](https://github.com/sgl-project/sglang/commit/70cec31378e88711081320511af9159b1035ef6e)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-31T21:56:30Z
- **提交信息**: [AMD] Pin mem_fraction_static for the piecewise CUDA graph 1-GPU test on MI300 (#32862)

### [4480e2a](https://github.com/sgl-project/sglang/commit/4480e2a0514858e9b96adf39cbb17aa6695f5e4b)

- **作者**: Xinyuan Tong
- **时间**: 2026-07-31T21:48:30Z
- **提交信息**: [Fix] Repair verify mask test fixture (#33087)

### [7e996a5](https://github.com/sgl-project/sglang/commit/7e996a5d0d875444747d3c5887cf913333d6a006)

- **作者**: Ethan (Yusheng) Su
- **时间**: 2026-07-31T21:23:01Z
- **提交信息**: Split #32584 into 1/2: [LoRA] Guard DP-attention idle forwards against stale LoRA batch state (#32707)

### [301ea43](https://github.com/sgl-project/sglang/commit/301ea43f35b9dd569d957968218f7761fe995767)

- **作者**: Alison Shao
- **时间**: 2026-07-31T21:22:26Z
- **提交信息**: [CI] Re-enable GB300 CI jobs (#32719)

### [9dcaf6b](https://github.com/sgl-project/sglang/commit/9dcaf6bfdff89b4b29611725ef44161be4e429dd)

- **作者**: Rain Jiang
- **时间**: 2026-07-31T19:36:25Z
- **提交信息**: rust server build release artifacts (#33096)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [94743f9](https://github.com/sgl-project/sglang/commit/94743f934c987c4ee1efc41d7208463b859bf4be)

- **作者**: Xinyuan Tong
- **时间**: 2026-07-31T19:14:53Z
- **提交信息**: [Docs] Add DeepSeek-V4 Flash Official (0731) recipe (#33083)

Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [5df193b](https://github.com/sgl-project/sglang/commit/5df193b4ac0f036e6a16cfae4eba254c355004ef)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-07-31T18:58:49Z
- **提交信息**: [Speculative Decoding] Fix GPT-OSS EAGLE3 hidden states (#32334)

### [4af8ddb](https://github.com/sgl-project/sglang/commit/4af8ddb5767509fc0a59ab796889c43e184ae206)

- **作者**: Rain Jiang
- **时间**: 2026-07-31T18:56:31Z
- **提交信息**: support rust sglang server (#29799)

### [77c77a3](https://github.com/sgl-project/sglang/commit/77c77a3da87958b34c822646753049603264190e)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T18:52:12Z
- **提交信息**: feat(inkling): migrate short convs onto the ShortConv attention backend (#33023)

### [d3222bc](https://github.com/sgl-project/sglang/commit/d3222bcc3a793973c8c890a3f22fb593fb176883)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T18:46:46Z
- **提交信息**: [unified-memory] Support fa3, the default MLA backend on pre-Blackwell hosts (#33046)

### [26486a9](https://github.com/sgl-project/sglang/commit/26486a957d51bcd6ef179ed13cc40853b96908ff)

- **作者**: luchangli
- **时间**: 2026-07-31T18:37:57Z
- **提交信息**: Fix --hicache-size allocating ~2x host memory on hybrid Mamba (#32915)

### [89f4a80](https://github.com/sgl-project/sglang/commit/89f4a80c1f5e71c1c960df120f1e03b43dfd3c1d)

- **作者**: Nan Jiang
- **时间**: 2026-07-31T15:12:32Z
- **提交信息**: Support fastsafetensors no-GDS loading and page-cache release (#31859)

### [5f9b0db](https://github.com/sgl-project/sglang/commit/5f9b0db18c787cf56ed9bbaf255f083f26c6ebc2)

- **作者**: Danila Shtan
- **时间**: 2026-07-31T13:46:33Z
- **提交信息**: Fix async loading of RunAI-streamed tensors (#32896)

Co-authored-by: Danila Shtan <dan@nebius.com>

### [690de09](https://github.com/sgl-project/sglang/commit/690de097c429c35b9e38a20a2df18d8f27f75d8a)

- **作者**: luoroger37
- **时间**: 2026-07-31T12:43:25Z
- **提交信息**: [fix]reject media input for text-only models (#32914)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [e3d4f48](https://github.com/sgl-project/sglang/commit/e3d4f48e5547ab023c2f67effb2d93eaf2221642)

- **作者**: Peng Wu
- **时间**: 2026-07-31T11:43:09Z
- **提交信息**: [Fix] missing max_context_len on HybridAttnBackend (#32690)

### [754b692](https://github.com/sgl-project/sglang/commit/754b692afc2948137c4315989481e406acae0159)

- **作者**: Mick
- **时间**: 2026-07-31T11:35:48Z
- **提交信息**: [diffusion] optimization: support cuda-ipc zero-staging all-to-all for 2-rank Ulysses (#31854)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [fd28242](https://github.com/sgl-project/sglang/commit/fd28242b683f367dbee47736a361cc694906d067)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-31T09:28:37Z
- **提交信息**: [CI] Pin NCCL ports for GB300 PR tests (#33044)

### [2573190](https://github.com/sgl-project/sglang/commit/2573190b9377debd135417f25b0c4185b0a3c48a)

- **作者**: Khoa Pham
- **时间**: 2026-07-31T09:14:09Z
- **提交信息**: feat: support Kimi Linear PD disaggregation with DCP (#32837)

Co-authored-by: Yangmin Li <yangminl@nvidia.com>

### [33c27d8](https://github.com/sgl-project/sglang/commit/33c27d8e7f4f1c6bb479c702cde92567c67f8391)

- **作者**: Cheng Wan
- **时间**: 2026-07-31T08:32:08Z
- **提交信息**: [unified-memory] Let Kimi-Linear use the paged MLA attention backends (#32972)

### [937c77c](https://github.com/sgl-project/sglang/commit/937c77cf5003fb32ab5f871c2f582b9c96f70269)

- **作者**: Ziang Li
- **时间**: 2026-07-31T07:35:15Z
- **提交信息**: [Fix] Clear stale FlashInfer BF16 MoE index cache (#33016)

### [585a7d0](https://github.com/sgl-project/sglang/commit/585a7d05e384c79ee17bf3185c7469fe8ce75946)

- **作者**: Kangrui Du
- **时间**: 2026-07-31T07:29:07Z
- **提交信息**: [Diffusion] Return scheduler sigmas snapshot in rollout dit_trajectory (#32683)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1240
- **最后更新**: 2026-07-30T09:22:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 87810
- **最后更新**: 2026-07-31T22:16:27Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 31
- **主要提交者**: Nicolò Lucchesi, Martin Hickey, Kyle Sayers

## AI分析总结

分析生成失败

## 详细提交记录

### [e3be896](https://github.com/vllm-project/vllm/commit/e3be89673db6143c1f9c8689d853b9c7c7a5eb29)

- **作者**: Mike G
- **时间**: 2026-07-31T21:48:27Z
- **提交信息**: Enable ModelOpt FP8 emulation on SM80 (#50019)

Signed-off-by: Mike G <180722391+mikekg@users.noreply.github.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [454ea5b](https://github.com/vllm-project/vllm/commit/454ea5b52611c933e00581723e2db56f0144cea7)

- **作者**: bnellnm
- **时间**: 2026-07-31T21:13:03Z
- **提交信息**: [MoE Refactor] Combine CompressedTensorsWNA16MarlinMoEMethod with CompressedTensorsWNA16MoEMethod (#44570)

Signed-off-by: Bill Nell <bnell@redhat.com>
Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: Dobrzyniewicz, Agata <agata.dobrzyniewicz@intel.com>
Signed-off-by: Tushar Jain <tushar00jain@users.noreply.github.com>
Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Agata Dobrzyniewicz <160237065+adobrzyn@users.noreply.github.com>
Co-authored-by: Tushar Jain <8455015+tushar00jain@users.noreply.github.com>
Co-authored-by: Tushar Jain <tushar00jain@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [0c4dc7c](https://github.com/vllm-project/vllm/commit/0c4dc7c488754e6c895ff785b86b76b9c26923c4)

- **作者**: Ning Xie
- **时间**: 2026-07-31T20:51:33Z
- **提交信息**: [graceful shutdown] fix http server start firstly before app signal handler register (#49668)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [9032991](https://github.com/vllm-project/vllm/commit/90329913e945cb3ed515bd8e1712094cecb76a0c)

- **作者**: Michael Goin
- **时间**: 2026-07-31T20:04:34Z
- **提交信息**: [UX] Reduce startup log noise (#50590)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [e8b358b](https://github.com/vllm-project/vllm/commit/e8b358b4c0df5cf136072747c97a95526bd59df1)

- **作者**: yzong-rh
- **时间**: 2026-07-31T19:45:40Z
- **提交信息**: [Bugfix][Responses] Add tests for Chat Completions Responses API Render Parity (#50334)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [4fdd3e0](https://github.com/vllm-project/vllm/commit/4fdd3e0b74ab5bfcf86341a304cc894c09705d5b)

- **作者**: Adrian
- **时间**: 2026-07-31T19:30:09Z
- **提交信息**: [ROCm][ViT] Detect Triton-AMD kernels at their new aiter location (#40289)

Signed-off-by: Adrian Kurt <info@zzit.ch>
Signed-off-by: Adrian <info@zipfuzapfu.ch>
Co-authored-by: Claude <noreply@anthropic.com>

### [9a7ae4b](https://github.com/vllm-project/vllm/commit/9a7ae4b80866a322678ece31ca2854d9a174ab8d)

- **作者**: Ning Xie
- **时间**: 2026-07-31T18:55:09Z
- **提交信息**: [chore] log process manager shutdown with more details (#49437)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [726ef43](https://github.com/vllm-project/vllm/commit/726ef437a160798c4312586fdbf38d1d112c5c9a)

- **作者**: Ning Xie
- **时间**: 2026-07-31T18:54:08Z
- **提交信息**: [chore] delete useless code (#49424)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [963a658](https://github.com/vllm-project/vllm/commit/963a658674045d460ef370214d7d73575efffb98)

- **作者**: Shangdi Yu
- **时间**: 2026-07-31T18:06:49Z
- **提交信息**: Bump Helion to 1.4.0 (#50307)

Signed-off-by: Shangdi Yu <shangdiy@meta.com>

### [aef85ae](https://github.com/vllm-project/vllm/commit/aef85aed5d8970052fa14407b716cdac1a8164ac)

- **作者**: Soila Kavulya
- **时间**: 2026-07-31T17:42:32Z
- **提交信息**: [Bugfix][TurboQuant] Add KV quant mode for turboquant  (#50533)

Signed-off-by: Soila Kavulya <soila.p.kavulya@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e67a2e0](https://github.com/vllm-project/vllm/commit/e67a2e0a56b7ba535bae8bfd98c1c4e4fa742e63)

- **作者**: fxmarty-amd
- **时间**: 2026-07-31T17:07:15Z
- **提交信息**: [ROCm][Quark][7/N] Use MXFP4 linear kernel abstraction for `emulation` backend (#48949)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [d87d2ca](https://github.com/vllm-project/vllm/commit/d87d2ca74791fe23ca2a0ba68c997de1618b33b6)

- **作者**: Kyle Sayers
- **时间**: 2026-07-31T17:06:30Z
- **提交信息**: [Compressed-Tensors] Support Kimi-K3 quantized models (#50500)

Signed-off-by: Kyle Sayers <kylesayrs@gmail.com>

### [8d8a4e0](https://github.com/vllm-project/vllm/commit/8d8a4e0f2b118dc975bbba930aeb7c6cbd623c2a)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-31T16:32:43Z
- **提交信息**: [ROCm][CI] Restore Mistral tool-parser compatibility after unification (#50515)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [7c08664](https://github.com/vllm-project/vllm/commit/7c08664f5c628ade14d2bf28f764ee1cfbbcedb1)

- **作者**: Dennis Yeh
- **时间**: 2026-07-31T16:22:42Z
- **提交信息**: Upgrade tpu-inference to v0.26.0 (#50522)

### [10ad649](https://github.com/vllm-project/vllm/commit/10ad649d6c1c4e1f1be986e928169a5351b9f6a7)

- **作者**: ylangtsou
- **时间**: 2026-07-31T15:57:16Z
- **提交信息**: Update torch version to 2.13.0+cpu (#50412)

Signed-off-by: Ylang Tsou <ylangt@google.com>
Co-authored-by: Ylang Tsou <ylangt@google.com>

### [c036cb2](https://github.com/vllm-project/vllm/commit/c036cb257f39dd022c30fd5738c6a12c14784a28)

- **作者**: LG
- **时间**: 2026-07-31T15:56:01Z
- **提交信息**: [Doc] Add BgeM3EmbeddingModel to embedding supported models (#50571)

### [a0cd2b6](https://github.com/vllm-project/vllm/commit/a0cd2b69b3dac2b43be02fc16ff940b856d6791b)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-31T15:52:17Z
- **提交信息**: [Bugfix] Universally align block table width to 128 tokens (#50302)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>

### [94e9ef0](https://github.com/vllm-project/vllm/commit/94e9ef0768d0297299069502bf46813dc7479ce5)

- **作者**: Harry Mellor
- **时间**: 2026-07-31T15:46:52Z
- **提交信息**: [Bugfix] Don't transpose fused MoE quantization scales in `RoutedExperts.load_weights` (#50137)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [df71917](https://github.com/vllm-project/vllm/commit/df71917cf17c97d81f48122e6baa7c13d184ff90)

- **作者**: Wentao Ye
- **时间**: 2026-07-31T15:45:58Z
- **提交信息**: [DSv4 Perf] Optimize workspace reuse for eager break, 3.9% E2E TTFT improvement. (#49236)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5233368](https://github.com/vllm-project/vllm/commit/5233368daccd3d84293bab7b04bacae1433ea0e4)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-31T15:33:16Z
- **提交信息**: [ROCm][CI] Fall back to lossless Kimi K3 MXFP4 emulation on gfx942 (#50516)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [82ae416](https://github.com/vllm-project/vllm/commit/82ae4164ee016d4daecd2033c26f5c0827984a80)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-31T13:01:24Z
- **提交信息**: [2/N][Attention] Enable masked MHA for sparse MLA prefills (#48770)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [864a87f](https://github.com/vllm-project/vllm/commit/864a87febb5b4f3fe15b50520a6857b241d5bf63)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-31T12:53:16Z
- **提交信息**: [Kernel][CI] `--jit-monitor-mode error` e2e tests for kernel warmup infra (#50109)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [7fdc1ab](https://github.com/vllm-project/vllm/commit/7fdc1ab29e3d34b2a12b7b40256b53d5586d4aad)

- **作者**: Oğuzhan KIR
- **时间**: 2026-07-31T12:29:31Z
- **提交信息**: [CI] Remove default_torch_num_threads workaround from llava-onevision-transformers test (#50560)

Signed-off-by: oguz <oguzhankir17@gmail.com>

### [0b5b49d](https://github.com/vllm-project/vllm/commit/0b5b49dde81ca27b27b010fb257138686b056aba)

- **作者**: Recoordinate
- **时间**: 2026-07-31T11:54:43Z
- **提交信息**: [Bugfix][Frontend] Raise VLLMValidationError for user-facing errors in chat_utils.py (#50491)

Signed-off-by: latent-9 <296084221+latent-9@users.noreply.github.com>
Co-authored-by: latent-9 <296084221+latent-9@users.noreply.github.com>

### [f5ffc59](https://github.com/vllm-project/vllm/commit/f5ffc59b6abbf317708d4c319702bac2b2aa8e72)

- **作者**: wang.yuqi
- **时间**: 2026-07-31T11:46:53Z
- **提交信息**: [Renderer] Warm up the renderer properly. (#50408)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [2c4d348](https://github.com/vllm-project/vllm/commit/2c4d3488483a4ce90b44661aefdb0cd31c6fbffa)

- **作者**: Itay Etelis
- **时间**: 2026-07-31T11:42:54Z
- **提交信息**: [KV Connector] Add per-layer canonical KV page mappings for parallelism-agnostic offload (#48408)

Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Itay Etelis <Itay.etelis@gmail.com>

### [b2fb83e](https://github.com/vllm-project/vllm/commit/b2fb83e7ffbc30a1aa4667b1dad7ca3e2c342bcf)

- **作者**: Martin Hickey
- **时间**: 2026-07-31T11:20:18Z
- **提交信息**: [Attention]: Use KVCacheSpec for AttentionMetadataBuilder type hints (#50148)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [92643d6](https://github.com/vllm-project/vllm/commit/92643d68f551fe36c35a26b4a2e3bfd894d7d92a)

- **作者**: Jee Jee Li
- **时间**: 2026-07-31T11:12:03Z
- **提交信息**: K3 DSpark AR fusion (#50242)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [17beffd](https://github.com/vllm-project/vllm/commit/17beffd55f6fcc28f2e777d47d3e8aab6ea34c9a)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-31T10:46:53Z
- **提交信息**: [Misc] Clarify mono audio requirement (#50141)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [6e311c6](https://github.com/vllm-project/vllm/commit/6e311c6e2014a54868e2cbedf944a6873d06228b)

- **作者**: bnellnm
- **时间**: 2026-07-31T10:28:18Z
- **提交信息**: [MoE Refactor] Rename FusedMoE to FusedMoEFactory (#44941)

Signed-off-by: Bill Nell <bnell@redhat.com>
Signed-off-by: bnellnm <49004751+bnellnm@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [c911120](https://github.com/vllm-project/vllm/commit/c911120a6f499a50f46a484109bf9bb2971ead5f)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-31T10:16:52Z
- **提交信息**: [ROCm][CI] Update Transformers AR+RMS fusion expectation (#50517)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>

### [0e9b500](https://github.com/vllm-project/vllm/commit/0e9b50074e1cd3c498830b9124364037899a5c98)

- **作者**: Fadi Arafeh
- **时间**: 2026-07-31T10:15:38Z
- **提交信息**: [chore] clean-up weight prepack for INT8 MoE (#50116)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [88bc8fb](https://github.com/vllm-project/vllm/commit/88bc8fb56f69667bcb67b482ecf729385d7ae972)

- **作者**: Rehan Khan
- **时间**: 2026-07-31T09:49:31Z
- **提交信息**: [CPU][s390x] Optimize inference perf and add oneDNN INT8 GEMM for s390x (#50219)

Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [482cfc2](https://github.com/vllm-project/vllm/commit/482cfc20f05fd7d08401f646ce44ba1f7086dde3)

- **作者**: Chaojun Zhang
- **时间**: 2026-07-31T09:28:18Z
- **提交信息**: [XPU] Unify XPU RMSNorm kernels with vllm_c and drop redundant XPU-specific implementation (#46981)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [5d7647a](https://github.com/vllm-project/vllm/commit/5d7647a1092aba8eb4f41be91f89ef352854b318)

- **作者**: Qiming Zhang
- **时间**: 2026-07-31T08:32:49Z
- **提交信息**: [UT] add skipif for rocm aiter sampler UT (#50530)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>

### [34bb795](https://github.com/vllm-project/vllm/commit/34bb795ff3efee6cc08c9dd104deceefff2c4d55)

- **作者**: Thien Tran
- **时间**: 2026-07-31T08:01:48Z
- **提交信息**: [CI] Add M3 MSA tests to CI (#49143)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Codex <noreply@openai.com>

### [f727951](https://github.com/vllm-project/vllm/commit/f727951d3f0dbeb9acdb8a2f7ebfecaeb67090b3)

- **作者**: Taneem Ibrahim
- **时间**: 2026-07-31T07:46:18Z
- **提交信息**: [Bugfix] Re-land MiniMax M3 default video processor (#50305)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [10e6b40](https://github.com/vllm-project/vllm/commit/10e6b400150c8d2cbedad54260def4871d464667)

- **作者**: Fadi Arafeh
- **时间**: 2026-07-31T07:28:44Z
- **提交信息**: [CPU][BugFix] Remove redundant kv cache write (#50437)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>
Signed-off-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: jiang1.li <jiang1.li@intel.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [3ee2bd1](https://github.com/vllm-project/vllm/commit/3ee2bd13211e830b1b170d146d551c253801d3d1)

- **作者**: Mi Jiazhi
- **时间**: 2026-07-31T07:20:06Z
- **提交信息**: Fix duplicate HunyuanVL image boundary tokens (#49691)

Co-authored-by: Jiazhi Mi <jiazhimi@tencent.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-01
**监控日期**: 2026-07-31
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5768
- **最后更新**: 2026-07-31T21:45:11Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Nathan Price, wuli666, 林鑫

## AI分析总结

根据提交记录和项目背景（vllm-omni 旨在提供易用、快速、低成本的多模态模型服务），以下是分析总结：

### 1. 主要更新类型
- **Bug 修复**（5项）：涉及全双工通信、遗留输入源默认值、MiniCPM-o 部署连接器、Gradio 演示依赖、CI 性能测试。
- **性能优化**（1项）：缓存 RoPE cos/sin 表，提升 code predictor 效率。

### 2. 关键变更点与项目方向的关系
- **RoPE 表缓存（#5503)**：旋转位置编码计算在长序列/多模态推理中高频发生，缓存显著减少重复计算，符合“快速”服务目标。
- **运行时控制消息 JSON 序列化（#5613)**：修复全双工模式下控制指令的跨模块传输问题，增强实时交互稳定性，支撑“让每个人都能轻松使用”的愿景。
- **遗留阶段输入源默认值（#5498)**：避免配置缺失导致启动失败，提升系统健壮性，降低用户使用门槛。
- **MiniCPM-o 连接器解析（#5533)**：修正注册管线的隐式部署解析，完善对具体多模态模型的支持，助力生态扩展。
- **恢复 Gradio 依赖（#5632)**：确保演示功能可用，便于社区快速体验和验证。
- **CI 服务器复用（#5624)**：优化测试资源配置，提高开发迭代效率，间接保障项目质量。

### 3. 对项目的影响和潜在意义
- **稳定性增强**：多数修复消除了潜在崩溃或通信异常，使项目更接近生产可用状态。
- **性能提升**：RoPE 缓存直接降低推理延迟，对实时多模态交互尤其重要。
- **模型兼容性扩展**：MiniCPM-o 相关的修复表明项目正加速支持更多前沿模型，增强市场竞争力。
- **开发者体验优化**：CI 和演示依赖的修复有助于吸引贡献者，降低协作障碍。

### 4. 值得关注的技术点
- **RoPE 缓存策略**：如何平衡缓存占用与计算节省，可能预示后续对长上下文场景的优化。
- **全双工协议设计**：JSON 序列化修复暗示运行时控制通道的演进，可能涉及多进程/分布式通信机制。
- **部署连接器解析**：MiniCPM-o 的修复可能涉及了注册表或模型路由逻辑，值得注意扩展新模型时的通用模式。
- **CI 基础设施**：服务器复用方案对成本和服务测试覆盖率有直接影响，是工程效率的关键细节。

### 5. 从项目背景看发展影响
- vllm-omni 的目标是“简单、快速、便宜”地服务多模态模型，这批提交集中在**优化性能**和**修复关键路径漏洞**上，符合项目早期迭代阶段对稳定性的高要求。
- 同时针对具体模型（MiniCPM-o）和演示工具（Gradio）的修复

## 详细提交记录

### [d33c905](https://github.com/vllm-project/vllm-omni/commit/d33c905d803262d517a80564db20bc448998a929)

- **作者**: 林鑫
- **时间**: 2026-07-31T14:03:18Z
- **提交信息**: [Perf] Cache RoPE cos/sin tables in code predictor (#5503)

Signed-off-by: I-wave <2083236231@qq.com>

### [4715570](https://github.com/vllm-project/vllm-omni/commit/4715570acc45c83e680665ab53d534ea0a40f643)

- **作者**: Nathan Price
- **时间**: 2026-07-31T10:17:25Z
- **提交信息**: [Bugfix][Full Duplex] Make runtime_control payloads JSON serializable (#5613)

Signed-off-by: thecodewrangler <nathan@abridge.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [4956a41](https://github.com/vllm-project/vllm-omni/commit/4956a41f1291923845b69be4eba4f842932697eb)

- **作者**: wuli666
- **时间**: 2026-07-31T10:00:14Z
- **提交信息**: [Bugfix] Default missing legacy stage input sources (#5498)

Signed-off-by: wuli666 <421774554@qq.com>

### [2739f07](https://github.com/vllm-project/vllm-omni/commit/2739f0776b7563cd2eb77cbeaed2e44932341eff)

- **作者**: ruirui(rein) yang
- **时间**: 2026-07-31T09:38:26Z
- **提交信息**: [Bugfix][MiniCPM-o]Fix implicit deploy connector resolution for registered pipelines (#5533)

Signed-off-by: R2-Y <ruiruyang2@gmail.com>

### [2d8ef47](https://github.com/vllm-project/vllm-omni/commit/2d8ef4754c7d10ccef80e146549389f2d69f06c7)

- **作者**: maithilijoshi20
- **时间**: 2026-07-31T09:24:45Z
- **提交信息**: [Bugfix] Restore Gradio demo dependency (#5632)

Signed-off-by: maithilijoshi20 <maithilijoshi2003@gmail.com>
Co-authored-by: maithilijoshi20 <maithilijoshi2003@gmail.com>

### [f8a8fbf](https://github.com/vllm-project/vllm-omni/commit/f8a8fbf72e360634274d50eb1a5ef3797196ff42)

- **作者**: SYLAR
- **时间**: 2026-07-31T08:23:17Z
- **提交信息**: [Bugfix][CI] Reuse servers across paired perf cases (#5624)

Signed-off-by: lishunyang12 <lishunyang03@gmail.com>
Co-authored-by: lishunyang12 <lishunyang03@gmail.com>

---
