# GitHub Stars 合并报告 - 2026-06-22

**合并日期**: 2026-06-23
**监控日期**: 2026-06-22
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


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2035
- **最后更新**: 2026-06-22T12:41:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2432
- **最后更新**: 2026-06-22T15:56:00Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2142
- **最后更新**: 2026-06-22T21:51:52Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5838
- **最后更新**: 2026-06-22T19:24:55Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Ka-Hyun Nam, Brian K. Ryu

## AI分析总结

## 昨日更新分析总结

### 1. 主要更新类型
- **性能优化**（提交 a671c02）：GDN（Grouped Decode Normalization?）内核编译优化，支持动态 batch 尺寸。
- **功能新增**（提交 5bbf294）：新增 BF16_FP4 混合精度 GEMM，支持 W4A16 推理负载，提供 cuDNN 和 CuTe-DSL 两种后端。

### 2. 关键变更点及与项目方向的关系
| 提交 | 变更内容 | 与项目方向的关系 |
|------|----------|------------------|
| a671c02 | 使 GDN 内核编译不再依赖静态 batch 尺寸，运行时动态获取 batch 大小，提升编译缓存复用性 | 契合 FlashInfer "高性能 GPU 推理内核" 定位，降低分布式推理框架（如 vLLM）集成的开销 |
| 5bbf294 | 实现 `mm_bf16_fp4` 操作；提供 `prepare_bf16_fp4_weights` 和 `mm_bf16_fp4` 两阶段 API；针对 SM100/103/110/120/121 优化 | 扩展推理支持的数据类型（FP4 权重量化），直接服务 W4A16 场景，属于模型量化推理关键路径 |

### 3. 对项目的影响和潜在意义
- **GDN 动态 batch 支持**：消除 `vLLM` 等动态 batching 推理引擎重新编译内核的负担，提升部署灵活性与性能。
- **W4A16 支持**：增加 FlashInfer 在权重量化推理领域的竞争力，基准测试显示 CuTe-DSL 后端比 Marlin 有约 1.1 倍几何平均加速，尤其小 batch 场景表现突出。
- 两个提交共同降低了推理框架集成门槛并扩展了低精度计算能力，推动项目向更广泛的应用场景发展。

### 4. 值得关注的技术点
- **CuTe-DSL 自动生成内核**：基于 NVIDIA CUTLASS 的 CuTe DSL 自动生成 Blackwell 优化密集 GEMM 内核，无需手工编写 CUDA。
- **两阶段 API 设计**：权重复备与执行分离，利于模型加载时准备权重，推理时只执行 GEMM，优化延迟。
- **编译缓存优化**：GDN 内核通过运行时参数提取 batch 尺寸，避免因 batch 变化导致编译缓存失效，属工程技巧。
- **后端差异化处理**：cuDNN 支持输出 dtype 与输入不同，CuTe-DSL 不支持，但性能相当，提供选择灵活性。

### 5. 与项目发展方向的关联
根据 README，FlashInfer 致力于提供高性能 GPU 推理内核。**昨日更新直接加强了这一使命**：
- 动态 batch 支持使内核更易被主流推理引擎（如 vLLM、TGI）采用，推动项目在现实生产环境中落地。
- W4A16 是当前 LLM 推理中对显存和带宽极度敏感的场景，此功能填补了 FlashInfer 在低比特量化 GEMM 上的空白，且性能优于已有方案，有助于项目成为推理内核的首选库。
- 两提交体现了项目从「手写 CUDA 内核」向「自动生成+后端可插拔」架构演进，为未来支持更多硬件与精度打下基础。

## 详细提交记录

### [a671c02](https://github.com/flashinfer-ai/flashinfer/commit/a671c02ee2fbcdde7cc991f5a01c7cf5eb4a8972)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-06-22T16:23:30Z
- **提交信息**: perf(gdn): make GDN kernels compilation batch-size agnostic (support dynamic batch shapes for vLLM integration) (#3649)

## 📌 Description

Addresses part 2 of
https://github.com/flashinfer-ai/flashinfer/issues/3602 , also brings
over overlapping effort from @bkryu 's work in #3601

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

* **Performance Improvements**
* Improved GPU kernel compilation and caching to better reuse compiled
cubins across varying batch sizes.
* Updated GDN decode/verify (including MTP) kernel launch behavior to
derive batch sizing at runtime.
* **Robustness Improvements**
* Enhanced support for dynamic batch-dependent tensors during
compilation and execution.
* Improved handling of per-batch auxiliary metadata and correct
index/state aliasing for split-pool scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5bbf294](https://github.com/flashinfer-ai/flashinfer/commit/5bbf2945545e33b5cec9d36a04080f253b76a1fa)

- **作者**: Brian K. Ryu
- **时间**: 2026-06-22T15:49:40Z
- **提交信息**: feat: Add BF16_FP4 GEMM with cuDNN and CuTe-DSL backends for SM120/121 for W4A16 workloads (#3597)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

### Summary
This PR adds `mm_bf16_fp4` -- A bf16xfp4 mixed-precision GEMM for W4A16
inference workloads. Supports two backends: cuDNN and CuTe-DSL kernel.
Supported on SM100/103/110/120/121. cuDNN requires backend version
9.23.1 or later.
  
The computation is `out = (a @ dequant(b, b_sf).T) * alpha`, where 
* `a` is a `bfloat16` tensor,
* `b` is an `nvfp4` tensor,
* `b_sf` is the per-16-element FP8-E4M3 block scales, and
*  `alpha` is an optional fp32 global scale. 

Kernel is optimized for SM121 (DGX Spark). SM120 requires further
optimization.

**CuTe-DSL kernel adopted from [the CUTLASS bf16 dense GEMM
example](https://github.com/NVIDIA/cutlass/blob/main/examples/python/CuTeDSL/cute/blackwell_geforce/kernel/dense_gemm/dense_gemm.py).
Traces were auto-generated with AI**

### API
Weight-only quantized GEMMs need a backend-specific weight layout, so
the API is a two-step flow:
* `prepare_bf16_fp4_weights` --> For preprocessing nvfp4 weights (B
operand)
* The preparation step is a performance optimization to accelerate the
dequantization at GEMM runtime.
* `mm_bf16_fp4` → execute the bf16xfp4 GEMM.

```python
import torch
import flashinfer

## Prepare inputs and quantize the B operand (weights)
M, N, K = 128, 4096, 4096
a = torch.randn(M, K, device="cuda", dtype=torch.bfloat16)  # activations
w = torch.randn(N, K, device="cuda", dtype=torch.bfloat16)  # weight, row-major (N, K)
g_w = (448 * 6) / w.float().abs().max()
b_fp4, b_sf = flashinfer.nvfp4_quantize( 
    w, g_w, sfLayout=flashinfer.SfLayout.layout_128x4, do_shuffle=False, backend="cute-dsl"
)
alpha = torch.tensor([1.0 / g_w.item()], device="cuda", dtype=torch.float32)

backend = "cute-dsl"
## Prepare weights at model load: repack canonical nvfp4 weights for a backend.
b_p, sf_p, alpha_p = flashinfer.prepare_bf16_fp4_weights(b_fp4, b_sf, alpha, backend=backend)

## At inference time, run with a different A operand for each batch of tokens.
out = flashinfer.mm_bf16_fp4(a, b_p, sf_p, alpha_p, backend=backend)

## Refcheck against the unquantized weight (error dominated by FP4 weight quantization):
ref = (a.float() @ w.float().T).to(torch.bfloat16)
rel_l2 = (out.float() - ref.float()).norm() / ref.float().norm()
cos = torch.nn.functional.cosine_similarity(
    out.float().flatten(), ref.float().flatten(), dim=0
)
assert rel_l2 < 0.15 and cos > 0.99
```

### Testing
Adds a `test_mm_bf16_fp4.py ` unit test script. Example command and
output collected on DGX Spark

```
$ pytest tests/gemm/test_mm_bf16_fp4.py
================================================================= test session starts =================================================================  
platform linux -- Python 3.12.3, pytest-9.0.3, pluggy-1.6.0
rootdir: ...
configfile: pytest.ini
plugins: anyio-4.13.0
collected 234 items

tests/gemm/test_mm_bf16_fp4.py ............................................................................................................... [ 47%]
..................................................................................................................s........                     [100%]

===================================================== 233 passed, 1 skipped in 132.32s (0:02:12) ======================================================
```
The skipped test is:
```
tests/gemm/test_mm_bf16_fp4.py::test_backend_out_dtype_override[cudnn] PASSED                                                                  [ 96%]
tests/gemm/test_mm_bf16_fp4.py::test_backend_out_dtype_override[cute-dsl] SKIPPED (cute-dsl requires out_dtype == a.dtype)                     [ 96%]
where cuDNN allows different a and out dtypes (bf16 and fp16) while cute-dsl does not.
```

### Benchmarks
Adds a `mm_bf16_fp4` microbenchmark routine . Example command:
```
python benchmarks/flashinfer_benchmark.py --routine mm_bf16_fp4 --backends cute-dsl cudnn --m 1 --k 2688 --n 10304 --refcheck --no_cuda_graph --autotune
```

Benchmark results comparing `backend='cute-dsl'` with Marlin kernels
called via vLLM on DGX Spark (SM121).

Benchmarks runnable [via side branch with Marlin enabled in
microbenchmarks](https://github.com/bkryu/flashinfer/tree/mm_fp4_w4a16_cudnn_and_dsl_with_marlin).
<details>
<summary>Click to show reproducer microbenchmark commands</summary>

Note: The following commands used in the
mm_fp4_w4a16_cudnn_and_dsl_with_marlin branch has a different routine
name as it comes from a previous iteration.

```
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 512 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 512 --n 2048 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 1024 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 1024 --n 2048 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 2048 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 4096 --n 512 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 512 --n 4096 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 4096 --n 1024 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 1024 --n 4096 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 4096 --n 2048 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 4096 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 4096 --n 4096 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 131072 --refcheck --no_cuda_graph
python benchmarks/flashinfer_benchmark.py --routine mm_w4a16_fp4 --backends cute-dsl marlin --m 1 --k 2048 --n 248320 --refcheck --no_cuda_graph
```

</details>

| M | N | K | cute-dsl (ms) | cute-dsl TB/s | Marlin (ms) | Marlin TB/s
| Speedup |
|--:|--:|--:|--:|--:|--:|--:|--:|
| 1 | 2048 | 512 | 0.008 | 0.072 | 0.010 | 0.058 | 1.25× |
| 1 | 4096 | 512 | 0.014 | 0.085 | 0.016 | 0.073 | 1.14× |
| 1 | 2048 | 1024 | 0.013 | 0.088 | 0.017 | 0.072 | 1.31× |
| 1 | 4096 | 1024 | 0.024 | 0.097 | 0.025 | 0.093 | 1.04× |
| 1 | 512 | 2048 | 0.010 | 0.061 | 0.010 | 0.059 | 1.00× |
| 1 | 1024 | 2048 | 0.013 | 0.090 | 0.016 | 0.076 | 1.23× |
| 1 | 2048 | 2048 | 0.023 | 0.104 | 0.027 | 0.088 | 1.17× |
| 1 | 4096 | 2048 | 0.045 | 0.105 | 0.048 | 0.099 | 1.07× |
| 1 | 131072 | 2048 | 0.717 | 0.211 | 0.710 | 0.213 | 0.99× |
| 1 | 248320 | 2048 | 1.199 | 0.239 | 1.227 | 0.234 | 1.02× |
| 1 | 512 | 4096 | 0.017 | 0.070 | 0.016 | 0.075 | 0.94× |
| 1 | 1024 | 4096 | 0.023 | 0.104 | 0.025 | 0.094 | 1.09× |
| 1 | 2048 | 4096 | 0.041 | 0.115 | 0.046 | 0.102 | 1.12× |
| 1 | 4096 | 4096 | 0.080 | 0.118 | 0.085 | 0.111 | 1.06× |

cute-dsl matches or beats Marlin on 12 of 14 shapes (geomean **~1.10×**,
range 0.94×–1.31×); the two large-N cases and 512×4096 are within noise.



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
* Added W4A16 (FP4-weight, 16-bit activation) support to the `mm_fp4`
GEMM API with backend dispatch and public weight-prep/export.
* **Performance / Kernels**
* Introduced a new Blackwell-optimized dense GEMM kernel and enhanced
Cute-DSL backend preparation/launch with caching and autotuning.
* **Benchmarks**
* Added an `mm_fp4_w4a16` benchmark routine; benchmark CSV output now
fills all expected result columns with CLI-backed defaults.
* **Trace / Templates**
* Added W4A16 FP4 trace templates and generated trace fixtures for both
backends.
* **Tests**
* Added cross-backend API/trace reference correctness coverage and
reference-validation tests.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yanqin Zhai <yanqinz@nvidia.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3741
- **最后更新**: 2026-06-22T20:05:41Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Satyam Srivastava

## AI分析总结

根据提交记录 `[3d8cc4f] [bugfix] Fix performance component timing extraction (#1473)`，结合项目背景 `FastVideo`（一个视频处理/生成相关的开源项目），以下为昨日更新要点总结：

---

### 1. 主要更新类型
- **Bug修复**（唯一提交）

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：修复了“性能组件”中时间提取（timing extraction）的逻辑错误。
- **与项目方向的关系**：`FastVideo` 是一个专注于视频处理效率与性能的开源工具（从项目名和文档可以看出）。性能组件（performance component）很可能是用于监控、记录或分析视频处理各阶段耗时（如编码、解码、推理、传输等）的核心模块。时间提取的准确度直接影响性能数据的可靠性，进而影响用户对系统瓶颈的诊断、优化策略的制定以及基准测试的可信度。

### 3. 对项目的影响和潜在意义
- **影响**：修复后，性能组件能够正确提取和记录各类操作的耗时，避免因计时错误导致性能报告失真或优化方向误判。
- **潜在意义**：
  - 提升项目作为视频处理框架的可信度，尤其对于依赖精确性能数据的科研或生产用户。
  - 为后续性能优化（如并行调度、内存管理、算子选择）提供可靠的数据基础。
  - 间接支持项目追求“Fast”的核心目标——只有准确测量才能有效加速。

### 4. 值得关注的技术点
- **“timing extraction”的边界条件**：视频处理中常见异步操作（如GPU任务、多线程流水线），时间提取需要正确处理同步/异步边界，避免重复计时或遗漏计时。
- **可能涉及的数据结构**：如 `perf_counter`、`high_resolution_clock` 的使用，以及时间戳序列化管理。
- **回归风险**：修复可能引入新的并发问题（如竞态条件），需关注后续是否出现相关补偿提交。

### 5. 基于README背景分析对项目发展的影响
- `FastVideo` 的README强调提供**文档、快速开始、周会**，表明项目注重社区协作和易用性。本周提交虽小，但体现了对基础可靠性的持续打磨：
  - **“快速开始”** 用户依赖性能工具来评估自己的视频工作流能否达到“快速”，该修复保证了首次体验不因计时错误而误导。
  - **“每周开发会议”** 中常讨论性能问题，准确的性能指标能让讨论更具数据驱动性。
  - 整体上，该修复是项目从“功能可用”向“指标可信”迈进的一小步，有助于吸引更多对性能敏感的视频应用开发者。

---

**总结**：昨日是一个专注于**内部质量**的Bug修复，看似微小但直接关联项目“快速”承诺的可测量性，为后续性能优化和用户信任打下基础。

## 详细提交记录

### [3d8cc4f](https://github.com/hao-ai-lab/FastVideo/commit/3d8cc4f0a0d25a55ab034777e1415b35dd4f9c7d)

- **作者**: Satyam Srivastava
- **时间**: 2026-06-22T20:05:35Z
- **提交信息**: [bugfix] Fix performance component timing extraction (#1473)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33901
- **最后更新**: 2026-06-22T21:00:30Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

根据您提供的提交记录 `huggingface/diffusers` 昨日更新分析如下：

---

### 1. 主要更新类型
- **功能新增**：添加了全新的 `Krea2Transformer2DModel` 和 `Krea2Pipeline`，即 Krea 公司的 K2 文本到图像流水线及配套 Transformer 模型。

### 2. 关键变更点及其与项目整体方向的关系
- **变更内容**：引入基于 **流匹配（flow-matching）** 的多模态扩散 Transformer（MMDiT），采用 **分组查询注意力（grouped-query attention）**、**Qwen3-VL 文本编码器** 以及 **Qwen-Image VAE**。
- **与项目方向的关系**：diffusers 致力于提供广泛、灵活的生成式模型支持。本次新增使项目直接支持 Krea 的商业级模型，同时**拓宽了对非传统扩散范式（流匹配）** 和 **多模态 Transformer 架构** 的覆盖，符合项目“支持最新生成技术”的核心使命。

### 3. 对项目的影响和潜在意义
- **影响**：
  - 用户现可直接使用 diffusers 加载并运行 Krea K2 模型，无需额外适配。
  - 为社区提供了参考实现，促进流匹配和 MMDiT 在 diffusers 生态中的标准化。
- **潜在意义**：
  - 加强与 Krea 等工业界团队的合作，吸引更多商业模型集成。
  - 推动 diffusers 从传统扩散模型向流匹配等**新兴生成范式**演进，保持技术前沿性。

### 4. 值得关注的技术点
- **流匹配（Flow Matching）**：替代传统去噪扩散概率模型，训练更稳定、生成更直接。
- **MMDiT（多模态扩散 Transformer）**：将文本与图像嵌入在 Transformer 中交叉处理，提升跨模态对齐。
- **分组查询注意力（GQA）**：减少注意力计算量，提升推理效率。
- **Qwen3-VL 文本条件**：利用阿里 Qwen 系列视觉语言模型作为文本编码器，支持更丰富的语义理解。
- **Qwen-Image VAE**：与 Qwen 生态深度绑定的变分自编码器，保证潜在空间一致性。

### 5. 基于项目背景，该提交如何影响项目发展
- diffusers 一直强调对多种扩散模型和流水线的支持，本次新增**首次引入流匹配 MMDiT**，打破了仅限传统扩散框架的局限，为后续集成同类模型（如 Stable Diffusion 3、Flux 等）奠定架构基础。
- 同时集成 Qwen 生态组件，表明 diffusers 正积极与主流多模态基础模型（如 Qwen、LLaVA 等）打通，**增强跨项目协同能力**。
- 使 diffusers 成为 Krea K2 模型的官方推理工具，**提升项目在工业界的引用率和影响力**。

---

> 总结：这是一次重要的功能扩展，通过在 diffusers 中支持商业级流匹配 MMDiT 模型，推动项目向更广泛、更新颖的生成范式迈进，并加强与 Qwen 生态的互操作性。

## 详细提交记录

### [7104cb4](https://github.com/huggingface/diffusers/commit/7104cb43c3efa70949cf19811fd3441826a128e1)

- **作者**: YiYi Xu
- **时间**: 2026-06-22T20:59:24Z
- **提交信息**: Add Krea 2 (K2) text-to-image pipeline and transformer (#14045)

Adds Krea2Transformer2DModel and Krea2Pipeline: a flow-matching
text-to-image MMDiT with grouped-query attention, Qwen3-VL text
conditioning, and the Qwen-Image VAE.

Co-authored-by: Elea Zhong <elea@krea.ai>
Co-authored-by: Naga Sai Abhinay Devarinti <devarintinagasaiabhinay@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 417
- **最后更新**: 2026-06-22T04:30:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12614
- **最后更新**: 2026-06-22T16:02:57Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 29536
- **最后更新**: 2026-06-22T22:35:17Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 21
- **主要提交者**: Shangming Cai, YC Yen-Ching Tseng, Prajjwal Chittori

## AI分析总结

根据 `sgl-project/sglang` 昨日（根据提交时间推断）的 35 条提交记录，结合 README 中“高效推理引擎，支持多种模型与硬件”的项目背景，总结要点如下：

---

### 1. 主要更新类型
- **功能新增**：约 10 项（如 EAGLE 同步自由前填充、MiniMax-M3 稀疏注意力、Cohere2Vision CUDA graph、Qwen3-VL MoE FlashInfer allreduce、NPU 部署教程等）
- **Bug 修复**：约 8 项（Kimi-VL 非 RGB 图像崩溃、停止字符串修剪、CP 页面过滤、EAGLE 预填充管线恢复等）
- **性能优化**：约 5 项（FA4 page_size 自动强制、MoE 反向传播 barrier 优化、triton 内核去重等）
- **重构/清理**：约 4 项（ServerArgs 全量迁移至 Annotated style、测试风格重构、CUDA graph 日志清理）
- **CI/文档**：约 8 项（异步断言禁用、nixl 安装优化、扩散模型 CI 修复、AMD/NPU 文档更新等）

---

### 2. 关键变更点及与整体方向的关系
- **ServerArgs 大重构 (#28919, #28674)**：将全部字段迁移至 `Annotated` 风格，减少约 2400 行 CLI 参数代码。**提升可维护性**，为后续多后端扩展奠定基础。
- **EAGLE 投机推理增强 (#28854, #28870)**：新增同步自由的 `fast_prefill_plan` 配合 CUDA graph，修复预填充管线被 #23906 意外删除的问题。**提升解码吞吐量，贴合项目对投机解码的持续优化**。
- **硬件兼容性扩展**：
  - B300 (#28786)：FlashInfer allreduce 支持 Qwen3-VL MoE，**适配最新 GPU 架构**。
  - AMD (#28941, #28920, #28869)：修复 OOM、清理环境变量、固定 httpx 版本，**提升 ROCm 稳定性**。
  - NPU (#28621, #27893)：更新最佳实践文档与主流模型部署教程，**降低昇腾适配门槛**。
- **新模型/架构支持**：
  - MiniMax-M3 (#28712)：引入稀疏注意力 ops + JIT 内核，分步集成。
  - Cohere2Vision (#28686)：文本路径启用分段预填充 CUDA graph。
  - Nemotron3-Ultra (#28675)：增加 Mamba 后端和 SSM dtype 标志。
- **性能修复与优化**：
  - FA4 模式 (#28825)：修复 page_size 自动强制与 attention-backend 冲突问题。
  - Overlap WAR barrier (#28363)：通过门控前向读取恢复解码吞吐量。
  - kpool_topk_transform JIT 内核 (#28694)**：新增自定义 topk 变换内核**，提升 MoE 路由效率。

---

### 3. 对项目的影响与潜在意义
- **稳定性和可用性提升**：大量 Bug 修复（Kimi-VL、停止字符串、CP 过滤等）降低了生产环境崩溃风险。
- **推理效率提升**：CUDA graph 覆盖更多模型（EAGLE、Cohere2Vision）、MoE 优化、JIT 内核，**整体延迟和吞吐量受益**。
- **开发者体验改进**：ServerArgs 重构减少代码重复和参数混乱，CI 优化（nixl、flaky test）提高开发迭代速度。
- **硬件生态扩展**：AMD、NPU 的持续适配和文档完善，使项目不再局限于 NVIDIA，**符合开源多平台愿景**。
- **

## 详细提交记录

### [6c212a5](https://github.com/sgl-project/sglang/commit/6c212a5d6bbfc76bd7fe02b415c91e4aefe3e34c)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-22T22:35:10Z
- **提交信息**: [server_args] fix FA4 page_size auto-force for combined --attention-backend fa4 (#28825)

Co-authored-by: Brayden Zhong <b8zhong@uwaterloo.ca>
Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [a32f711](https://github.com/sgl-project/sglang/commit/a32f7111e4850784c54206df3720850d10a20b76)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-22T22:29:45Z
- **提交信息**: [CI] Disable async-assert for base-a tests in rerun-test (#28965)

### [770d6b2](https://github.com/sgl-project/sglang/commit/770d6b2825abfbade994805d6b153a756415203a)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-22T22:15:15Z
- **提交信息**: [Spec] Add sync-free `fast_prefill_plan` for EAGLE draft-extend CUDA graph (#28854)

### [c0198fc](https://github.com/sgl-project/sglang/commit/c0198fc277ad97305961f8ff270f85c2fc7dc06b)

- **作者**: Yuan Luo
- **时间**: 2026-06-22T21:59:06Z
- **提交信息**: [CI] Refactor int checkpoint tests style (#28813)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>

### [4f60378](https://github.com/sgl-project/sglang/commit/4f60378ff539b8fae8e4db229f82b0ddfa9c2a3f)

- **作者**: Kevin Flansburg
- **时间**: 2026-06-22T21:23:33Z
- **提交信息**: Fix Kimi-VL GPU image preprocessing crash on non-RGB images (#28647)

Signed-off-by: Kevin Flansburg <kflansburg@cloudflare.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>

### [bbc853d](https://github.com/sgl-project/sglang/commit/bbc853df462ba9eb5a6b1426c59bd3e08151b4ba)

- **作者**: Maxwill Lin
- **时间**: 2026-06-22T20:14:00Z
- **提交信息**: fix(schedule_batch): trim stop string when EOS matches in the same step (#28802)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [7c23d22](https://github.com/sgl-project/sglang/commit/7c23d2255a1f3d3f850701d635003aad195bb70a)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-22T20:10:43Z
- **提交信息**: [minimax-m3] Split 1/4: sparse attention ops + JIT kernels + config foundation (#28712)

### [b5e4e28](https://github.com/sgl-project/sglang/commit/b5e4e289b1fa49f59fbbf7d58a5145d070d02d88)

- **作者**: Alex Nails
- **时间**: 2026-06-22T20:08:33Z
- **提交信息**: [gRPC] Native server: Python bridge entrypoint (2/4) (#23507)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [8dc27f6](https://github.com/sgl-project/sglang/commit/8dc27f6326252d18383706df066b35d9e3a64e3d)

- **作者**: Wenyao Gao
- **时间**: 2026-06-22T20:01:21Z
- **提交信息**: [MoE] dedup triton_kernels backend quant-arg asserts and fill weight dtype guard (#28689)

### [669be54](https://github.com/sgl-project/sglang/commit/669be5448bbbbcbd724a6a6c45787dbcccde843a)

- **作者**: zijiexia
- **时间**: 2026-06-22T19:20:14Z
- **提交信息**: [cuda graph] Enable prefill piecewise CUDA graph for Cohere2Vision (text path) (#28686)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [adc203d](https://github.com/sgl-project/sglang/commit/adc203dfee4b343391a4a844250ed0c8532021dd)

- **作者**: Prajjwal Chittori
- **时间**: 2026-06-22T18:55:48Z
- **提交信息**: fix(router): use full conversation for PD chat cache-aware routing (#26263) (#27430)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [43b1fb9](https://github.com/sgl-project/sglang/commit/43b1fb95f6d9077c6750419546d73be8c710a754)

- **作者**: Shangming Cai
- **时间**: 2026-06-22T17:58:22Z
- **提交信息**: [CI] Optimize nixl dependency installation script (#28950)

Signed-off-by: Shangming Cai <csmthu@gmail.com>

### [99c18cc](https://github.com/sgl-project/sglang/commit/99c18cceecece3d0705fce113774e0bfc5d12ba8)

- **作者**: Brayden Zhong
- **时间**: 2026-06-22T17:23:46Z
- **提交信息**: Sync server arguments and environment variables + update various documentation (#28674)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [34e5e38](https://github.com/sgl-project/sglang/commit/34e5e38604bb32d1db524630b8ca6d340d062587)

- **作者**: Brayden Zhong
- **时间**: 2026-06-22T16:50:22Z
- **提交信息**: [Cookbook] Nemotron3-Ultra: Add mamba-backend and SSM dtype flags (#28675)

Co-authored-by: Brayden Zhong <brayden.zhong@radixark.ai>

### [ab21dc9](https://github.com/sgl-project/sglang/commit/ab21dc984a31145be3c8be9abb9d6de4335d46e4)

- **作者**: Shangming Cai
- **时间**: 2026-06-22T16:35:13Z
- **提交信息**: [CI] Fix flaky optimistic test by adding contention handling (#28947)

### [70883cb](https://github.com/sgl-project/sglang/commit/70883cb1b04f80965414c86932b3cc8f267b605e)

- **作者**: Zhangheng
- **时间**: 2026-06-22T15:48:48Z
- **提交信息**: [UnifiedTree]: Rollback mamba hicache test to direct io backend (#28904)

### [bbe8b7d](https://github.com/sgl-project/sglang/commit/bbe8b7dd8a495919215d29f28d00badbd4ea4942)

- **作者**: Mick
- **时间**: 2026-06-22T15:36:18Z
- **提交信息**: [diffusion] CI: restore Hunyuan3D-2 image-to-3D (#28781)

### [b28e990](https://github.com/sgl-project/sglang/commit/b28e990161a389fad5aaadd16cebd5b0b80c5f26)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-22T15:34:37Z
- **提交信息**: Migrate all ServerArgs fields to Annotated style, reduce add_cli_args by ~2400 lines (#28919)

### [6b2c730](https://github.com/sgl-project/sglang/commit/6b2c730bf793984c39f7f07b3c074ca05b059b00)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-22T14:39:21Z
- **提交信息**: [codex] Fix DSA indexer in prefill piecewise CUDA graph (#28644)

### [b43bd68](https://github.com/sgl-project/sglang/commit/b43bd6824f8b92260d86e24115b6a56624c0e974)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-22T14:38:45Z
- **提交信息**: [B300] Enable FlashInfer allreduce for Qwen3-VL MoE (#28786)

### [cee1caa](https://github.com/sgl-project/sglang/commit/cee1caaf476f989329232f3217a620a53cae315e)

- **作者**: Thomas Wang
- **时间**: 2026-06-22T14:35:45Z
- **提交信息**: [AMD] Fix nightly-8-gpu-mi35x-deepseek-v4-flash-rocm720 OOM issue (#28941)

### [04d952e](https://github.com/sgl-project/sglang/commit/04d952ea102d0bd922073f6d7a0b97b71e21ca0a)

- **作者**: Thomas Wang
- **时间**: 2026-06-22T14:32:43Z
- **提交信息**: [AMD] deepseek-v4 clean env vars (#28920)

### [dd39ef6](https://github.com/sgl-project/sglang/commit/dd39ef6cecd5f5950cc1c91e1ae251bdba6fa3d0)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-06-22T14:25:22Z
- **提交信息**: [AMD] Pin httpx>=0.25.0 to fix anthropic SDK socket_options error (#28869)

### [4923bb9](https://github.com/sgl-project/sglang/commit/4923bb93ae176583651d840b3fc5c229dd7e65e7)

- **作者**: Mick
- **时间**: 2026-06-22T13:21:16Z
- **提交信息**: [diffusion] CI: fix turbo_wan/flux invisible CI cases (#28913)

### [ad9723a](https://github.com/sgl-project/sglang/commit/ad9723af03601f805adfc912233a149cefa4ba4e)

- **作者**: Lianmin Zheng
- **时间**: 2026-06-22T13:15:26Z
- **提交信息**: Clean up CUDA graph capture logs (#28937)

### [ead39d3](https://github.com/sgl-project/sglang/commit/ead39d38fc31fc7cd95667b025ff45bae7fe8f0a)

- **作者**: Mick
- **时间**: 2026-06-22T13:00:38Z
- **提交信息**: [diffusion] refactor: refactor causal KV local head cache updates (#28888)

### [1adb53f](https://github.com/sgl-project/sglang/commit/1adb53f1478cc8b76df505bdd3e22aa6fd7b4d78)

- **作者**: shihaozhou
- **时间**: 2026-06-22T12:47:29Z
- **提交信息**: Fix CP page filtering by request-local position (#28718)

### [06e0013](https://github.com/sgl-project/sglang/commit/06e001347a79c5ffe6b5d846ddc1c45c5c3da954)

- **作者**: Shangming Cai
- **时间**: 2026-06-22T12:35:14Z
- **提交信息**: [CI] Update nixl installation to include nixl-cu13 for h20 runner (#28930)

### [b8e64fb](https://github.com/sgl-project/sglang/commit/b8e64fb56d25c75496140b9c3cd2f6ba7a028f83)

- **作者**: Shangming Cai
- **时间**: 2026-06-22T11:26:26Z
- **提交信息**: [CI] Modify nixl installation to force reinstall (#28927)

### [0c9e775](https://github.com/sgl-project/sglang/commit/0c9e775f2c8594249c08430a8f99df30faf9fafb)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-06-22T10:43:24Z
- **提交信息**: [Diffusion] Fix FastWan2.1 default 480p resolution (#28733)

### [4e1d251](https://github.com/sgl-project/sglang/commit/4e1d25117bf3134a3a43d55f461ea8708853f0b3)

- **作者**: jianzhao-xu
- **时间**: 2026-06-22T08:58:48Z
- **提交信息**: [NPU] update best practice docs from testcase (#28621)

### [2ce3236](https://github.com/sgl-project/sglang/commit/2ce32366a073135b462778359b01228c0a043aac)

- **作者**: Yuwei An
- **时间**: 2026-06-22T08:54:54Z
- **提交信息**: [Fix][BCG][Spec] Restore EAGLE prefill plumbing dropped by #23906 (#28870)

### [93553a6](https://github.com/sgl-project/sglang/commit/93553a67a3bc4f1ee8b516fded49d09860ea6d35)

- **作者**: amote-i
- **时间**: 2026-06-22T08:21:13Z
- **提交信息**: [NPU] [DOC] Create deployment tutorials for mainstream models on Ascend NPU (#27893)

### [db12bfc](https://github.com/sgl-project/sglang/commit/db12bfcdc8a686efc8ee0a2899bdb43be9cedcf8)

- **作者**: Xinyuan Tong
- **时间**: 2026-06-22T08:04:21Z
- **提交信息**: [JIT] Add kpool_topk_transform JIT kernel (#28670)

### [106d293](https://github.com/sgl-project/sglang/commit/106d2930a6c57fb2ad8960c149a4f256f822f3f9)

- **作者**: Liangsheng Yin
- **时间**: 2026-06-22T07:40:56Z
- **提交信息**: [core] Gate the overlap WAR barrier on forward reads to recover decode throughput (#28363)

Co-authored-by: thanhhao98 <31717833+thanhhao98@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1206
- **最后更新**: 2026-06-22T07:40:38Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，根据提供的提交记录和项目背景，以下是对昨日更新的分析总结：

---

### 1. 主要更新类型

- **功能新增**（feat）：支持foca校准器（`foca calibrator`）
- **文档修复**（chore）：修复文档渲染问题（#1067）

---

### 2. 关键变更点及其与项目整体方向的关系

| 提交 | 变更点 | 与项目方向的关系 |
|------|--------|------------------|
| `649c8a2` | 修复文档渲染错误 | 提升文档可读性和项目可维护性，利于用户理解和使用推理引擎 |
| `6f56ea3` | 新增 `foca calibrator` | 直接关联项目核心能力之一——**量化（Quantization）**。foca校准器可能是一种新的量化校准算法（如基于Fully Online Calibration），用于提升量化后模型的精度或推理效率，符合项目“量化”和“CPU卸载”等高效推理目标。 |

---

### 3. 对项目的影响和潜在意义

- **功能层面**：`foca calibrator` 为DiT模型提供了一种新的校准途径，可能优化量化激活/权重的缩放因子计算，从而在保持生成质量的同时降低模型精度损失。这有助于项目在**低精度推理（如INT8/INT4）场景**下获得更优的生成效果。
- **文档层面**：修复文档渲染能减少用户上手障碍，提升项目在PyPI上的专业形象，间接促进下载量增长（README中已有pip下载量显示）。
- **生态意义**：foca校准器的加入丰富了项目的量化工具链，可能与已有的量化模块组合，形成更完整的**精度-性能权衡方案**，对研究者和工业部署者均有吸引力。

---

### 4. 值得关注的技术点

- **foca校准器**：推测为“Fully Online Calibration Algorithm”或类似方法的实现。与传统的离线/后训练校准不同，foca可能结合推理过程进行动态校准，更适合DiT这种生成式模型在长序列推理中对精度敏感的特性。
- **量化适配性**：该校准器是否与项目中的缓存（Cache）和CPU卸载（CPU Offload）功能兼容？是否支持流水线并行？这些细节虽未在提交日志中体现，但很可能是后续关注点。
- **多提交模式**：feat提交包含5个重复的commit message，实际变更可能在一个commit内完成，但可通过文件diff查看具体改动（如新增的calibrator模块接口、与现有量化器的交互逻辑等）。

---

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化项目核心定位**：`cache-dit`旨在为Diffusion Transformers提供“高效推理”的一站式方案。foca校准器直接补全了量化环节的定制化能力，使项目从“支持量化”进化为“可配置的先进校准策略”，有助于在同类工具（如Hugging Face Optimum、TensorRT等）中建立差异化优势。
- **吸引更多用户**：文档修复提升了项目可用性，而新功能可能吸引需要高精度量化的用户（如移动端或边缘设备部署）。README中展示的下载量增长趋势也会被进一步巩固。
- **为未来扩展奠基**：foca校准器的设计可能作为后续更多校准算法（如min/max、percentile、KL散度等）的模板，促进项目逐渐形成量化校准器插件库，丰富项目生态。

---

**一句话总结**：昨日更新在**量化能力**上迈出了关键一步（foca校准器），同时通过文档修复提升了项目质量，两者均服务于`cache-dit`成为DiT高效推理首选引擎的目标。

## 详细提交记录

### [649c8a2](https://github.com/vipshop/cache-dit/commit/649c8a20ffd7a1cd766c866b26a4a29b28dcb643)

- **作者**: DefTruth
- **时间**: 2026-06-22T07:40:34Z
- **提交信息**: chore: fix docs rendering broken (#1067)

### [6f56ea3](https://github.com/vipshop/cache-dit/commit/6f56ea3bcac1346755836e529eb6b01cf762df45)

- **作者**: DefTruth
- **时间**: 2026-06-22T07:29:29Z
- **提交信息**: feat: support foca calibrator (#1066)

* feat: support foca calibrator

* feat: support foca calibrator

* feat: support foca calibrator

* feat: support foca calibrator

* feat: support foca calibrator

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 83574
- **最后更新**: 2026-06-22T22:42:56Z

## 提交统计

- **昨日提交总数**: 35
- **提交者数量**: 32
- **主要提交者**: Chao-Ju Chen, Tiezhen WANG, Simon Mo

## AI分析总结

好的，以下是对 `vllm-project/vllm` 仓库昨日（根据提交时间推断）35 条提交的更新要点分析。

---

### 1. 主要更新类型

| 类型 | 数量（约） | 说明 |
|------|------------|------|
| **CI 基础设施改进** | 8+ | ROCm 清理、超时修复、新测试、GPU 资源管理 |
| **Bug 修复** | 10+ | FusedMoE、KV 连接器竞态、EAGLE 缓存、CPU 模型、异步解码 |
| **硬件/平台适配** | 6+ | ROCm、XPU、CPU RISC-V、SM120（NVIDIA）、Intel GPU |
| **新功能/优化** | 5+ | FlashInfer NVFP4 GEMM、KV 事件自我描述、Rust 前端 thinking 预算 |
| **模型支持** | 4+ | DeepSeek V4、GLM-5.1、Llama4、ColQwen3.5 |
| **文档/流程** | 3+ | PR 限制说明、安全文档链接、MiniMax-M3 文档更新 |
| **重构/清理** | 3+ | 删除旧模型（MiniMaxText01 等）、Lora 类型检查、WhisperModelState 泛化 |
| **性能优化** | 2+ | FlashInfer NVFP4、MLA 跨层缓存重启用 |
| **测试增强** | 2+ | KV Offloading 单元测试、Humming 量化 LM Eval 测试 |

---

### 2. 关键变更点及与项目整体方向的关系

- **FlashInfer NVFP4 GEMM 后端**（d1a38c2）  
  方向：**极致性能**。通过集成 FlashInfer 的 FP4 矩阵乘，对低精度推理进行硬件加速，契合 vLLM “快速、便宜”的核心价值。

- **DeepSeek V4 / GLM-5.1 在 SM120 上支持**（44d9506）  
  方向：**模型生态扩展**。vLLM 持续跟踪最新大模型，确保能够在 NVIDIA 最新架构（SM120）上运行，保持竞争力。

- **Bugfix: FusedMoE 形状处理**（c0b2d8f）  
  方向：**稳定性**。修复 MoE 专家中尺度计算时的边界情况，提高推理可靠性。

- **Bugfix: 异步 speculate decode 竞态**（cec2ec1）  
  方向：**正确性**。异步推测解码是 vLLM 1.x 核心特性，修复这里保证了高吞吐下的结果一致性。

- **Rust 前端支持 thinking_token_budget**（80abe0d）  
  方向：**多语言前端**。vLLM 正在引入 Rust 作为高性能前端，支持“思考”Token 预算表明与大模型思维链特性的整合。

- **KV Offloading：自描述事件**（a9f7b2d）  
  方向：**大规模部署**。KV offloading 是 vLLM 应对长上下文 / 低内存场景的关键特性，自描述事件让 offloading 行为更可观测和可调试。

- **ML 架构：重新启用 MLA 跨层 KV 缓存布局**（aa4990a）  
  方向：**性能 + 兼容性**。MLA（Multi-head Latent Attention）是 DeepSeek 等模型的核心技术，此补丁通过 stride-aware 内核优化其缓存布局，提高显存效率。

- **ROCm 相关改进**（70ef4d3, fbf9ff7, 2b4a749, 89accad）  
  方向：**硬件多元化**。AMD ROCm 是 vLLM 第二大 GPU 平台，持续清理 CI、限制不兼容后端、优化内存查询，降低了维护成本并提升了 AMD 用户满意度。

- **CPU / XPU / RISC-V 适配**（1c7bc18, ccd49f6, 09cdcf3, d2c671c, 3da4a1b）  
  方向：**全平台覆盖**。vLLM 正大力拓展非 GPU 场景（CPU、Intel XPU、RISC-V），尤其是 R

## 详细提交记录

### [70ef4d3](https://github.com/vllm-project/vllm/commit/70ef4d30096bd41e025cdf79c7c89de6ce4e9c79)

- **作者**: Andreas Karatzas
- **时间**: 2026-06-22T22:42:47Z
- **提交信息**: [ROCm][CI] Purging away redundant test group definitions (#46418)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [e2fe837](https://github.com/vllm-project/vllm/commit/e2fe8375722605cd7b3106b0365fa8eadef98b10)

- **作者**: Tyler Michael Smith
- **时间**: 2026-06-22T22:08:00Z
- **提交信息**: [CI] Fix CPU-Multi-Modal Model Tests timeout by adding a 4th shard (#46388)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fbf9ff7](https://github.com/vllm-project/vllm/commit/fbf9ff7cf4a466387126097f15c3f00da316e6cb)

- **作者**: Aarushi Jain
- **时间**: 2026-06-22T22:05:26Z
- **提交信息**: [CI][ROCm] Restrict MLA cross-layer KV cache test to supported backends on ROCm (#46401)

Signed-off-by: aarushjain29 <Aarushi.Jain2@amd.com>

### [6cc2c9b](https://github.com/vllm-project/vllm/commit/6cc2c9ba3a2c78714b897474e087745058570902)

- **作者**: Michael Goin
- **时间**: 2026-06-22T21:52:38Z
- **提交信息**: [CI] Add DGX Spark GPQA smoke test (#39541)

Signed-off-by: mgoin <mgoin64@gmail.com>
Signed-off-by: Michael Goin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [c0b2d8f](https://github.com/vllm-project/vllm/commit/c0b2d8f471699a0619ab9cc2e99719937eba503f)

- **作者**: Varshith
- **时间**: 2026-06-22T20:26:53Z
- **提交信息**: [Bugfix] FusedMoE: coerce shape-(1,) per-tensor scales to 0-D scalar … (#43362)

Signed-off-by: Varshith <kvarshithgowda@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [d1a38c2](https://github.com/vllm-project/vllm/commit/d1a38c276202b23b5dc8a7bfc7f0b3b83a1ac913)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-06-22T20:17:18Z
- **提交信息**: [Kernel][Performance] Add FlashInfer cutedsl NVFP4 GEMM backend (#42235)

Signed-off-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [2b4a749](https://github.com/vllm-project/vllm/commit/2b4a7491ecffc362f1f080c3ac41dfe10018c39b)

- **作者**: stefankoncarevic
- **时间**: 2026-06-22T20:12:24Z
- **提交信息**: [ROCm][CI] Query total device memory via amdsmi to avoid HIP init (#46141)

Signed-off-by: stefankoncarevic <stefan.koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [82ede09](https://github.com/vllm-project/vllm/commit/82ede09a5a26c3b529a1e13adb68e5ecc0558790)

- **作者**: Saddss
- **时间**: 2026-06-22T20:08:47Z
- **提交信息**: [Bugfix][KVConnector] Fix SimpleCPUOffloadConnector GPU->CPU store race (#46278)

### [fbf520c](https://github.com/vllm-project/vllm/commit/fbf520cf3aab26f97337c6d6e299c66b96d0fcb9)

- **作者**: Nick Hill
- **时间**: 2026-06-22T19:40:02Z
- **提交信息**: [MRV2] Generalize use of `WhisperModelState` (#46096)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [44d9506](https://github.com/vllm-project/vllm/commit/44d95069e9d6f764bea72f8a9ae6fa7f21187182)

- **作者**: Gabriel Wu
- **时间**: 2026-06-22T18:54:14Z
- **提交信息**: Enable DeepSeek V4 and GLM-5.1 on SM120 (#43477)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [3ce15fd](https://github.com/vllm-project/vllm/commit/3ce15fd574960faaf19fb202851bc140d0eb9d02)

- **作者**: Dao007forever
- **时间**: 2026-06-22T18:54:00Z
- **提交信息**: [v1][kvconnector] DecodeBenchConnector: fill list/tuple (Mamba/KDA) KV caches (#45080)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [e4b3da3](https://github.com/vllm-project/vllm/commit/e4b3da3feb20c1854a4b23e431cfb787ee268f72)

- **作者**: Jinzhen Lin
- **时间**: 2026-06-22T18:23:55Z
- **提交信息**: [Quantization][CI] add humming lm-eval test (#43752)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3e6529c](https://github.com/vllm-project/vllm/commit/3e6529cc0e0f039bcc8c82d1403efa8355fd053d)

- **作者**: Nick Hill
- **时间**: 2026-06-22T18:14:02Z
- **提交信息**: [Bugfix][Spec Decode] Fix EAGLE drafter multimodal encoder cache misses (#46315)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [ac61458](https://github.com/vllm-project/vllm/commit/ac614587f514e9032bff75eb04c86ddeb3c9dbef)

- **作者**: Ilya Markov
- **时间**: 2026-06-22T17:54:08Z
- **提交信息**: [EPLB] Enable nixl eplb communicator for elastic ep (#45013)

Signed-off-by: Markov Ilya <markovilya197@gmail.com>
Signed-off-by: Markov Ilya <markovilya19@gmail.com>
Co-authored-by: Markov Ilya <markovilya19@gmail.com>

### [f2069b0](https://github.com/vllm-project/vllm/commit/f2069b005b815e8a1b44381712dc951157c42ad4)

- **作者**: Taneem Ibrahim
- **时间**: 2026-06-22T15:40:47Z
- **提交信息**: [Pooling] Validate non-negative rerank top_n (#46119)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [ccd49f6](https://github.com/vllm-project/vllm/commit/ccd49f6821ee110cc5a2b1aba620a8a1d66c7cbb)

- **作者**: Martin Hickey
- **时间**: 2026-06-22T14:57:09Z
- **提交信息**: [MyPy] Fix mypy for `vllm/lora` (#41722)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>

### [1c7bc18](https://github.com/vllm-project/vllm/commit/1c7bc1831808bf5e6d9b3283855d18951a1eb955)

- **作者**: Li, Jiang
- **时间**: 2026-06-22T14:52:05Z
- **提交信息**: [Bugfix][CPU] Fix CPU model runner v2 (#46365)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [9a938df](https://github.com/vllm-project/vllm/commit/9a938df64e5e296e42524fc0a67956923806197d)

- **作者**: AlexHuang
- **时间**: 2026-06-22T14:45:04Z
- **提交信息**: [Test][KV Offloading] Add unit tests for OffloadingSpecFactory and SecondaryTierFactory (#46355)

Signed-off-by: Alex <alex.tech.lab@outlook.com>

### [3da4a1b](https://github.com/vllm-project/vllm/commit/3da4a1b124a8839b1014e5d571784fc8d0953de7)

- **作者**: Liangliang Ma
- **时间**: 2026-06-22T14:29:13Z
- **提交信息**: [XPU] add awq format for INCXPULinear (#43404)

Signed-off-by: Ma, Liangliang <liangliang.ma@intel.com>

### [6871738](https://github.com/vllm-project/vllm/commit/687173877781670afde318491564bab92ac353aa)

- **作者**: Simon Mo
- **时间**: 2026-06-22T14:04:56Z
- **提交信息**: [Doc] Document pull request limit (#46376)

Signed-off-by: simon-mo <simon.mo@hey.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [aa4990a](https://github.com/vllm-project/vllm/commit/aa4990a9a2024b3f93f1f26f828931f7301daa15)

- **作者**: Yifan Qiao
- **时间**: 2026-06-22T13:57:02Z
- **提交信息**: [Attention] Re-enable cross-layer KV cache layout for MLA via stride-aware kernels (#45111)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>

### [a4610da](https://github.com/vllm-project/vllm/commit/a4610da0c642d63b988ec8e3dde858a7c13a4d99)

- **作者**: Simon Mo
- **时间**: 2026-06-22T13:28:25Z
- **提交信息**: [docs] link security docs from AGENTS (#46373)

Add a security-review routing sentence to AGENTS.md that points agents to SECURITY.md, docs/usage/security.md, and docs/contributing/vulnerability_management.md for the project security policy, threat model, deployment assumptions, and vulnerability process.

Co-authored-by: OpenAI Codex <codex@openai.com>

### [09cdcf3](https://github.com/vllm-project/vllm/commit/09cdcf34aac46a37320bc394cc714ac5f53b937d)

- **作者**: liuzhenwei
- **时间**: 2026-06-22T12:55:06Z
- **提交信息**: [XPU] update nixl to v1.2.0 (#46327)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [d2c671c](https://github.com/vllm-project/vllm/commit/d2c671c29be7ffe3c4dc081c90a7ba12fd1a904e)

- **作者**: wcy
- **时间**: 2026-06-22T12:53:54Z
- **提交信息**: [CPU][RISC-V] Add RVV micro GEMM for WNA16 (#44324)

Signed-off-by: wcy <233313160abc@gmail.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [b5a2ade](https://github.com/vllm-project/vllm/commit/b5a2adec4bae0032c00e974b391e04ce59b98242)

- **作者**: xiangdong
- **时间**: 2026-06-22T11:30:41Z
- **提交信息**: [XPU][CI]Skip v1/spec_decode/test_speculators_correctness.py in intel GPU nightly (#46356)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [78739e3](https://github.com/vllm-project/vllm/commit/78739e3bda0466ecbd63de1bda07d5ac09d88dca)

- **作者**: Maxwill Lin
- **时间**: 2026-06-22T10:16:35Z
- **提交信息**: [Bugfix] Reject matryoshka embedding dimensions above hidden size (#46313)

Signed-off-by: EazyReal <8047065+EazyReal@users.noreply.github.com>
Co-authored-by: EazyReal <8047065+EazyReal@users.noreply.github.com>

### [89accad](https://github.com/vllm-project/vllm/commit/89accad2cc9685bbd813ec0efab316b36cf123ca)

- **作者**: Tuukka Sarvi
- **时间**: 2026-06-22T09:26:54Z
- **提交信息**: [ROCm][DSV4] Disable TileLang MHC dispatch on gfx942 (#45931)

Signed-off-by: Tuukka Sarvi <tuukka.sarvi@amd.com>

### [3c8e495](https://github.com/vllm-project/vllm/commit/3c8e49596c3fd34ae82c8c5d881e91a38663639b)

- **作者**: Athrael Soju
- **时间**: 2026-06-22T09:25:54Z
- **提交信息**: [Model] ColQwen3.5: fix retrieval correctness (bias + bidirectional) (#46108)

Signed-off-by: Athrael Soju <athrael.soju@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [cec2ec1](https://github.com/vllm-project/vllm/commit/cec2ec11760f9f3beabd4c90451936078bf91533)

- **作者**: Weiwei Sun
- **时间**: 2026-06-22T08:53:16Z
- **提交信息**: [Bugfix] Avoid racy accepted counts in async spec decode (#45100)

Signed-off-by: Weiwei Sun <68775773+sunnweiwei@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>

### [435f82d](https://github.com/vllm-project/vllm/commit/435f82d61a1eddb84854ca59a008a8e4d97ab439)

- **作者**: liuzhenwei
- **时间**: 2026-06-22T08:40:43Z
- **提交信息**: [Bugfix] Fix Llama4ForCausalLM initialization test failure (#46341)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [1c4b51b](https://github.com/vllm-project/vllm/commit/1c4b51b9904a718d17faa5efe93b7414222d8efb)

- **作者**: Roger Wang
- **时间**: 2026-06-22T08:35:31Z
- **提交信息**: Temporarily skip M3 on CI (#46352)

Signed-off-by: Roger Wang <hey@rogerw.io>

### [2e2c479](https://github.com/vllm-project/vllm/commit/2e2c47928b916466d987f2ae53e84881e0fbec99)

- **作者**: Jee Jee Li
- **时间**: 2026-06-22T08:23:27Z
- **提交信息**: [Doc] Update MiniMax-M3  (#45940)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Roger Wang <hey@rogerw.io>
Co-authored-by: Jiangyun Zhu <riverclouds.zhu@qq.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [80abe0d](https://github.com/vllm-project/vllm/commit/80abe0de7d20523e465597d823a40ab4a29df20a)

- **作者**: Chao-Ju Chen
- **时间**: 2026-06-22T08:00:02Z
- **提交信息**: [Rust Frontend] Support thinking_token_budget for chat and completions (#46137)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: RickyChen / 陳昭儒 <ricky.chen@infinirc.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [a9f7b2d](https://github.com/vllm-project/vllm/commit/a9f7b2d41c5e92f0d60ebdd3dbe04e627019c179)

- **作者**: Change72
- **时间**: 2026-06-22T07:27:46Z
- **提交信息**: [feature][kv_offload] Self-describing KV events for OffloadingConnector (#43468)

Signed-off-by: Change72 <changg@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d14e551](https://github.com/vllm-project/vllm/commit/d14e551a5326c75f3213aa35ae4dbbed7a04ea02)

- **作者**: Tiezhen WANG
- **时间**: 2026-06-22T07:20:46Z
- **提交信息**: [Model] Remove MiniMaxText01, MiniMaxVL01, MiniMaxForCausalLM (#45993)

Signed-off-by: Xianbao QIAN <xianbao.qian@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-06-23
**监控日期**: 2026-06-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5240
- **最后更新**: 2026-06-22T21:44:03Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Zhou Taichang, Chenguang Zheng, 汪志鹏

## AI分析总结

好的，根据您提供的 vllm-project/vllm-omni 仓库的 7 条提交记录，结合 README 的项目定位（Easy, fast, and cheap omni-modality model serving），以下是昨日更新的总结分析：

---

### 1. 主要更新类型

| 类型 | 数量 | 具体提交 |
|------|------|----------|
| 功能新增 | 3 | IndexTTS2 文本转语音、Async Omni 异步物化输出、迁移 Magi human 示例 |
| Bug 修复 | 1 | HunyuanImage3 AR RGB 转换对齐 |
| 性能优化 | 1 | Cosmos3 I2V 跳过未使用的 conditioning latents |
| CI / 基础设施 | 2 | 修复流水线上传依赖、更新 NPU 镜像 |

无文档更新、重构或纯粹补丁。

---

### 2. 关键变更点与项目方向的关系

- **IndexTTS2 文本转语音支持** 🔈  
  vllm-omni 主打“全模态服务”，此前主要聚焦视觉（图像/视频）和语言模型。加入 TTS 支持补齐了“语音输出”模态，朝着真正 omni（全模态）方向迈出关键一步。

- **Async Omni output materialization** 🔄  
  异步输出物化允许模型推理与输出物化解耦，避免同步阻塞。对多模态服务（尤其是流式生成视频、音频等长时序输出）至关重要，直接提升“fast”和用户交互体验。

- **HunyuanImage3 AR RGB 转换修复** 🎨  
  确保图像生成结果与官方语义一致，避免因颜色空间转换导致的视觉偏差，提升模型输出正确性和可控性（尤其是遵循 prompt 的 RGB 语义）。

- **Cosmos3 I2V 性能优化（跳过未使用条件潜变量）** ⚡  
  视频/图像生成类模型常有多余的 conditioning 计算。跳过无用的潜变量可节省 GPU 算力与显存，提升推理速度，吻合“cheap”和“fast”目标。

- **Magi human 示例迁移** 👤  
  迁移示例代码，帮助用户快速上手特定人体交互场景，降低使用门槛，符合“easy”理念。

- **CI 修复与 NPU 镜像更新** 🛠  
  提升 CI 稳定性和对昇腾 NPU 平台的支持，扩大硬件兼容范围，促进“for everyone”。

---

### 3. 项目影响与潜在意义

- **模态扩展**：TTS 支持使 vllm-omni 从视觉→语言→语音全覆盖，成为真正的全模态服务框架雏形。
- **可用性提升**：异步输出物化改善了流式场景的并发处理能力，有助于多轮对话、实时生成等场景的 latency 降低。
- **生态兼容**：修复 RGB 转换、提供示例、更新 NPU 镜像，都降低了社区二次开发和部署的摩擦。

---

### 4. 值得关注的技术点

- **IndexTTS2 整合方式**：需要看后续是否支持流式 TTS、多语言、情感控制等，这会影响 vllm-omni 在语音应用中的竞争力。
- **Async materialization 架构**：此改动可能涉及 core engine 的调度逻辑，后续可能会扩展到其他模态（如视频、图像流式分块）。
- **Cosmos3 条件剪枝**：属于模型感知的优化，未来可推广到其他 I2V 或 V2V 模型中，提升通用性能。

---

### 5. 结合 README 背景的整体影响

vllm-omni 致力于“让所有人轻松、快速、廉价地使用全模态模型”。本次更新：

- **补充模态缺口**：从视觉+语言扩展到语音，朝着“omni”迈出实质一步。
- **优化性能与成本**：跳过无用计算、异步化输出直接降低成本（cheap）和延迟（fast）。
- **降低门槛**：示例迁移和 Bug 修复让开发者更容易集成、更少踩坑。
- **拓展硬件支持**：NPU CI 更新提示团队在支持国产化硬件方面持续投入，促进“for everyone”。

综上，这些提交是 vllm-omni 在**全模态覆盖**、**工程效率**和**生态易用性**上的重要推进，符合项目愿景。下一阶段可期待更多语音/音频模型接入以及异步化策略的广泛应用。

## 详细提交记录

### [044240d](https://github.com/vllm-project/vllm-omni/commit/044240d8ebeae9c19a7be01db9d37a1cd1a57c8a)

- **作者**: BeatSeat
- **时间**: 2026-06-22T19:24:01Z
- **提交信息**: [Model] Add IndexTTS2 text-to-speech support (#3838)

Signed-off-by: BeatSeat <wendavid552@gmail.com>
Signed-off-by: David <david@podcast.ai>
Signed-off-by: wendavid552 <wendavid552@gmail.com>
Signed-off-by: WenDavid <davidzhangcf@foxmail.com>

### [f4d922d](https://github.com/vllm-project/vllm-omni/commit/f4d922d8f60bf2a80e2a041ae9111714ef9d277c)

- **作者**: TaffyOfficial
- **时间**: 2026-06-22T16:09:03Z
- **提交信息**: [Bugfix][HunyuanImage3] Align AR RGB conversion with official semantics (#4502)

Signed-off-by: TaffyOfficial <2324465096@qq.com>
Co-authored-by: TaffyOfficial <2324465096@qq.com>

### [eaa16e1](https://github.com/vllm-project/vllm-omni/commit/eaa16e19417ec3f604058975b0605ce467637099)

- **作者**: Chenguang Zheng
- **时间**: 2026-06-22T16:07:07Z
- **提交信息**: [Feature] Support Async Omni output materialization (#4476)

Signed-off-by: Chenguang ZHENG <645327136@qq.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [8a67867](https://github.com/vllm-project/vllm-omni/commit/8a6786731e2c9115a4321b58af7d5d737461f471)

- **作者**: Zhou Taichang
- **时间**: 2026-06-22T15:22:11Z
- **提交信息**: [CI][Rebase] Fix Ready/Merge pipeline upload by stripping source_file_dependencies (#4532)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [fb0f178](https://github.com/vllm-project/vllm-omni/commit/fb0f17858fc18341f3d34af21d76ada84f9711c0)

- **作者**: Weiming Liao
- **时间**: 2026-06-22T14:33:06Z
- **提交信息**: [CI][NPU] Update VLLM ASCEND IMAGE (#4602)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [2447740](https://github.com/vllm-project/vllm-omni/commit/2447740308d58e3071e08c4a0e5022ef6839338b)

- **作者**: bjf-frz
- **时间**: 2026-06-22T09:51:47Z
- **提交信息**: [Perf]perf: skip unused Cosmos3 I2V conditioning latents (#4614)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [a10eac0](https://github.com/vllm-project/vllm-omni/commit/a10eac0f8c8fa8fbe3be8f2585f6e55aeaea7c76)

- **作者**: 汪志鹏
- **时间**: 2026-06-22T07:17:00Z
- **提交信息**: [Feature]: Migrate magi human example (#4572)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

---
