# GitHub Stars 合并报告 - 2026-03-26

**合并日期**: 2026-03-27
**监控日期**: 2026-03-26
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


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1769
- **最后更新**: 2026-03-26T11:54:43Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Juncheng Wan

## AI分析总结

根据您提供的仓库README摘要和提交记录，结合项目“VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo”的背景（专注于为多模态模型训练提供模型中心的分布式训练方案），以下是昨日更新的要点分析：

### 1. 主要更新类型
*   **功能新增**：提交 `06f4d87` 增加了对标签（labels）token数量的统计功能。
*   **代码维护/优化**：提交 `99a3f97` 优化了并行训练（特别是FSDP1）中的模块过滤逻辑。

### 2. 关键变更点及其与项目整体方向的关系
*   **增强训练监控与统计** (`06f4d87`)：新增对标签token的计数，这直接服务于项目“Scaling Any Modality Model Training”的核心目标。更精细的token统计有助于：
    *   **优化资源分配**：在多模态训练中，不同模态（文本、图像、视频）的输入和标签数据量差异巨大，精确统计是高效分配计算和内存资源的基础。
    *   **改进训练配方**：为项目宣称的“Distributed Recipe Zoo”提供更详细的数据支持，帮助用户理解和调优不同模态混合下的训练行为。
*   **优化并行训练逻辑** (`99a3f97`)：细化了全分片数据并行（FSDP1）中模块的过滤规则，确保只过滤掉与基础模块相同的额外并行模块。这直接关系到项目的“Model-Centric Distributed”特性：
    *   **提升训练稳定性与效率**：避免因模块过滤不当导致的冗余计算或通信开销，确保分布式训练配方的精确执行。
    *   **增强系统鲁棒性**：使并行策略在处理复杂模型结构时更加可靠，支持更广泛的模型类型。

### 3. 对项目的影响和潜在意义
*   **正向影响**：两项更新都是对核心训练流程的**精细化改进**，而非颠覆性变更。它们共同提升了VeOmni系统在**实际训练任务中的可观测性、可控性和效率**。
*   **潜在意义**：
    *   `06f4d87` 为未来更智能的**自动化资源调度**和**训练配方推荐**打下了数据基础。
    *   `99a3f97` 减少了因框架逻辑问题引入隐性Bug的风险，**降低了用户使用高级并行策略的门槛和调试成本**。

### 4. 值得关注的技术点
*   **FSDP（Fully Sharded Data Parallel）的定制化**：提交 `99a3f97` 显示项目团队正在对PyTorch的FSDP等底层分布式训练原语进行**深度定制和调优**，以适应多模态模型的特殊性，这是实现高效“Scaling”的关键技术环节。
*   **训练过程指标的扩展**：`06f4d87` 表明项目在**训练过程监控指标**上持续深化，不仅关注输入，也开始更细致地监控输出（标签）侧的数据特征，这对理解多模态训练动态至关重要。

### 5. 基于项目背景的提交影响分析
VeOmni旨在成为一个**模型中心、配方驱动的多模态分布式训练平台**。昨日的更新完美契合了这一发展方向：
*   **支撑“Recipe Zoo”**：更详细的token统计（`06f4d87`）为“训练配方”提供了更丰富的**元数据和评估维度**，使得配方的描述、比较和复用更加科学。
*   **强化“Model-Centric”和“Distributed”**：对FSDP逻辑的优化（`99a3f97`）体现了以**模型结构为中心**来适配和优化分布式策略的思想，确保分布式方案能紧密贴合不同模态模型的特性，实现高效扩展。
*   **体现成熟度**：此类对核心系统进行“精雕细琢”的更新，表明项目已度过早期的基础设施搭建阶段，进入**提升稳定性、易用性和智能化水平**的深入优化期，这对于吸引社区用户和应用于生产环境至关重要。

**总结**：昨日的更新是两项针对性强、质量高的优化提交，分别从**训练可观测性**和**分布式执行效率**两个维度，巩固和增强了VeOmni作为专业多模态分布式训练平台的核心能力。

## 详细提交记录

### [06f4d87](https://github.com/ByteDance-Seed/VeOmni/commit/06f4d87be83514d2e4f01fe20115cd693f691894)

- **作者**: Juncheng Wan
- **时间**: 2026-03-26T11:54:38Z
- **提交信息**: [misc] feat: count more token number of labels  (#610)

### [99a3f97](https://github.com/ByteDance-Seed/VeOmni/commit/99a3f97024f736336f2b8a7fa1ae116ff5ee3f0c)

- **作者**: Juncheng Wan
- **时间**: 2026-03-26T10:50:00Z
- **提交信息**: [parallel] chore: only filter out extra parallel modules same as the basic modules in fsdp1 (#607)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2105
- **最后更新**: 2026-03-26T14:12:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 1979
- **最后更新**: 2026-03-26T05:08:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5223
- **最后更新**: 2026-03-26T18:13:06Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Li Min, Brian K. Ryu

## AI分析总结

根据对FlashInfer仓库README（专注于高性能GPU推理内核）和昨日提交记录的分析，以下是总结要点：

### 1. 主要更新类型
- **功能新增**：新增了两个基于**NVIDIA CuTe DSL**的后端实现。
    1. **MLA解码内核**：支持Blackwell SM100架构的MLA（多头潜在注意力）解码，覆盖BF16/FP16和FP8数据类型。
    2. **NVFP4量化后端**：为4位浮点（FP4）量化添加了CuTe-DSL后端支持，包含两种优化内核变体。

### 2. 关键变更点及其与项目方向的关系
- **引入CuTe DSL**：两项提交均利用NVIDIA的**CuTe（C++模板引擎）DSL**编写高性能内核。这与FlashInfer“**提供高性能GPU推理内核**”的核心目标高度一致，旨在通过更现代的、声明式的编程模型提升性能与可维护性。
- **支持新硬件与数据类型**：
    - **MLA解码**明确针对新一代**Blackwell（SM100）** GPU和**FP8**数据类型进行优化，紧跟硬件发展前沿。
    - **NVFP4量化**支持**4位浮点**这种极低精度格式，直接服务于大模型推理中的**显存压缩和带宽优化**，是推理加速的关键技术。
- **性能与自动化**：
    - 均实现了**自动内核调度**（MLA根据序列长度选择持久/非持久内核；NVFP4根据问题规模在向量化加载和TMA内核间选择）。
    - 强调**零开销张量布局转换**（MLA）和**高带宽利用**（NVFP4达峰值84%），紧扣“高性能”主题。

### 3. 对项目的影响和潜在意义
- **性能提升**：在目标场景（Blackwell上的MLA解码、大矩阵的FP4量化）下实现了显著的**速度提升**（部分配置达1.3倍以上），巩固了FlashInfer作为高性能推理库的竞争力。
- **技术栈演进**：标志着项目内核开发从传统CUDA C++向**CuTe DSL**的积极迁移。CuTe DSL能更优雅地表达复杂张量运算和内存层次，可能降低未来开发复杂内核的难度。
- **扩大应用场景**：
    - **MLA解码**支持了如DeepSeek-V3等使用MLA架构的新模型。
    - **FP4量化后端**使FlashInfer在**模型权重量化**和**低精度推理**领域的能力更加完备。
- **生态兼容性**：通过提供与PyTorch兼容的API并消除Python端开销，提升了**易用性和集成度**。

### 4. 值得关注的技术点
- **CuTe DSL的实际应用**：提交展示了如何用CuTe DSL实现复杂的生产级内核（注意力解码、量化），并实现**AOT编译缓存**（`--enable-tvm-ffi`），这对社区有参考价值。
- **针对Blackwell的FP8优化**：FP8是Blackwell重点推广的数据类型，此次更新是FlashInfer抢占**新一代硬件生态**的先手。
- **智能内核调度策略**：NVFP4量化中基于 `log2(M) + log2(K) >= 25` 的启发式调度，体现了对**不同问题规模适配不同优化策略**的精细设计。
- **高测试覆盖率**：MLA解码通过了**396种配置**的测试，确保了功能的鲁棒性。

### 5. 基于项目背景的发展影响
FlashInfer的目标是成为**LLM推理场景中不可或缺的高性能算子库**。昨日的更新从两个维度强力推进了这一目标：
- **纵向深化（性能极限）**：通过采用CuTe DSL、支持FP8/FP4等新技术，在**最新硬件（Blackwell）** 上追求极致的算力和带宽利用，保持技术领先性。
- **横向拓展（场景覆盖）**：新增的**MLA解码**支持了新的模型架构，**FP4量化**强化了模型压缩和部署能力。这使得FlashInfer不仅能优化标准的Transformer推理，还能适配**更复杂、更前沿的模型和部署需求**。

**总结**：昨日提交是FlashInfer一次重要的**技术升级和功能扩张**。它不仅仅增加了两个新功能，更代表了项目向**更现代的内核编程范式（CuTe DSL）** 和**更广泛的低精度推理支持**的战略性迈进，旨在巩固其在高性能LLM推理基础设施领域的核心地位。

## 详细提交记录

### [31b63bc](https://github.com/flashinfer-ai/flashinfer/commit/31b63bc3d73597612419b4831218feabc57fd97d)

- **作者**: Li Min
- **时间**: 2026-03-26T18:12:59Z
- **提交信息**: Add cute dsl mla decode op (#2743)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Integrate NVIDIA's CuTe DSL MLA (Multi-Head Latent Attention) decode
kernels for Blackwell SM100 into FlashInfer, supporting both BF16/FP16
and FP8 dtypes.

- Add CuTe DSL MLA decode kernel files (mla_helpers.py,
mla_decode_fp16.py, mla_decode_fp8.py) and compilation wrapper
(mla_decode.py)
- Accept tensors from PyTorch and use zero-cost cute.make_tensor layout
reinterpretation inside kernel __call__, eliminating ~10 us of
Python-side .permute() overhead per call
- Compile with --enable-tvm-ffi for AOT caching via
compile_and_cache_cute_dsl_kernel

  ### Test plan

- python -m pytest tests/attention/test_cute_dsl_mla_decode.py — 18
tests passing (FP16 + FP8, various batch/head/seq_len configs)
- Standalone run functions in mla_decode_fp16.py and mla_decode_fp8.py
pass
  - pre-commit run --all-files passes

### Funtionality:

All 396 configs PASSED with 0 failures.

  Test matrix:
  - dtype: bfloat16, float8_e4m3fn
  - page_size: 32, 64
  - batch_size: 1, 2, 4, 16, 32, 64, 128, 256, 512, 768, 1024
  - seq_len: 1024, 4096, 8192
  - q_len_per_request: 1, 2, 4
  
  | Status | Count |
  |--------|-------|
  | PASSED | 396   |
  | FAILED | 0     |
  | TOTAL  | 396   |


### Performance:

- **GPU**: NVIDIA Blackwell (SM100a)
- **Model config**: DeepSeek-V3 MLA (128 heads, kv_lora_rank=512,
qk_nope_head_dim=128, qk_rope_head_dim=64)
- **KV seq_len**: 8192, **page_size**: 32
- **Timing**: CUPTI, CUDA graph enabled, cold L2 cache, 30 iterations
median
- **Date**: 2026-03-11

## 1. FP8 fixed-len (is_var_seq=False → persistent)

```
Config                                             trtllm-gen (ms)   cute-dsl (ms)    Speedup
---------------------------------------------------------------------------------------------
B=1, q=1, s=8192, ps=32, fp8                                0.0159          0.0166      0.96x
B=32, q=1, s=8192, ps=32, fp8                               0.0522          0.0513      1.02x
B=64, q=1, s=8192, ps=32, fp8                               0.0771          0.0704      1.10x
B=128, q=1, s=8192, ps=32, fp8                              0.1430          0.1336      1.07x
B=256, q=1, s=8192, ps=32, fp8                              0.2825          0.2681      1.05x
B=1, q=4, s=8192, ps=32, fp8                                0.0192          0.0185      1.04x
B=32, q=4, s=8192, ps=32, fp8                               0.1307          0.1214      1.08x
B=64, q=4, s=8192, ps=32, fp8                               0.2612          0.2441      1.07x
B=128, q=4, s=8192, ps=32, fp8                              0.4840          0.4533      1.07x
B=256, q=4, s=8192, ps=32, fp8                              0.9927          0.9359      1.06x
```

## 2. FP8 var-seqlen (is_var_seq=True → non-persistent)

```
Config                                             trtllm-gen (ms)   cute-dsl (ms)    Speedup
---------------------------------------------------------------------------------------------
B=1, q=1, s=8192, ps=32, fp8                                0.0159          0.0164      0.97x
B=32, q=1, s=8192, ps=32, fp8                               0.0463          0.0468      0.99x
B=64, q=1, s=8192, ps=32, fp8                               0.0704          0.0640      1.10x
B=128, q=1, s=8192, ps=32, fp8                              0.1264          0.1020      1.24x
B=256, q=1, s=8192, ps=32, fp8                              0.1873          0.1698      1.10x
B=1, q=4, s=8192, ps=32, fp8                                0.0192          0.0184      1.05x
B=32, q=4, s=8192, ps=32, fp8                               0.1181          0.1037      1.14x
B=64, q=4, s=8192, ps=32, fp8                               0.1851          0.1637      1.13x
B=128, q=4, s=8192, ps=32, fp8                              0.3040          0.2930      1.04x
B=256, q=4, s=8192, ps=32, fp8                              0.5964          0.6038      0.99x
```

## 3. BF16 fixed-len (is_var_seq=False → persistent)

```
Config                                             trtllm-gen (ms)   cute-dsl (ms)    Speedup
---------------------------------------------------------------------------------------------
B=1, q=1, s=8192, ps=32, bf16                               0.0241          0.0185      1.30x
B=32, q=1, s=8192, ps=32, bf16                              0.0824          0.0844      0.98x
B=64, q=1, s=8192, ps=32, bf16                              0.1351          0.1283      1.05x
B=128, q=1, s=8192, ps=32, bf16                             0.2566          0.2441      1.05x
B=256, q=1, s=8192, ps=32, bf16                             0.5106          0.4971      1.03x
B=1, q=4, s=8192, ps=32, bf16                               0.0227          0.0224      1.02x
B=32, q=4, s=8192, ps=32, bf16                              0.2136          0.2096      1.02x
B=64, q=4, s=8192, ps=32, bf16                              0.4284          0.4347      0.99x
B=128, q=4, s=8192, ps=32, bf16                             0.7891          0.8124      0.97x
B=256, q=4, s=8192, ps=32, bf16                             1.6007          1.7218      0.93x
```

## 4. BF16 var-seqlen (is_var_seq=True → non-persistent)

```
Config                                             trtllm-gen (ms)   cute-dsl (ms)    Speedup
---------------------------------------------------------------------------------------------
B=1, q=1, s=8192, ps=32, bf16                               0.0241          0.0184      1.31x
B=32, q=1, s=8192, ps=32, bf16                              0.0746          0.0764      0.98x
B=64, q=1, s=8192, ps=32, bf16                              0.1210          0.1126      1.07x
B=128, q=1, s=8192, ps=32, bf16                             0.2196          0.1805      1.22x
B=256, q=1, s=8192, ps=32, bf16                             0.3392          0.3090      1.10x
B=1, q=4, s=8192, ps=32, bf16                               0.0220          0.0214      1.03x
B=32, q=4, s=8192, ps=32, bf16                              0.1841          0.1743      1.06x
B=64, q=4, s=8192, ps=32, bf16                              0.2929          0.2961      0.99x
B=128, q=4, s=8192, ps=32, bf16                             0.5050          0.5384      0.94x
B=256, q=4, s=8192, ps=32, bf16                             1.0073          1.0903      0.92x
```



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
* Added "cute-dsl" backend for MLA decoding with FP16/BF16/FP8 support
and a PyTorch-compatible MLA decode API.
* Added MLA static-tile scheduling helpers and deterministic
kernel/workspace handling.

* **Public API**
* Exposed the new decode API and a torch→Cutlass dtype mapping in the
public interface.

* **Tests**
* End-to-end tests for FP16/BF16/FP8, variable sequence lengths, and API
path.

* **Benchmarking**
  * Benchmarks updated to select and exercise the new backend.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [d426b18](https://github.com/flashinfer-ai/flashinfer/commit/d426b1831e921c1226d059d19d09d433b4fece96)

- **作者**: Brian K. Ryu
- **时间**: 2026-03-26T07:14:28Z
- **提交信息**: feat: Add CuTe-DSL backend for NVFP4 quantization (#2838)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Adds backend="cute-dsl" support to nvfp4_quantize with two kernel
variants:
- Default kernel: vectorized global loads (ld.global.v4.u32), optimal
for small-to-medium problems
- TMA kernel: producer-consumer warp specialization (1 producer + 8
consumer warps), 3D TMA with SWIZZLE_128B, optimal for large problems
(M×K >= 2^25 elements)
- Auto-dispatches between variants based on log2(M) + log2(K) >= 25
threshold
- Supports all SF layouts (128x4, 8x4, linear), fp16/bf16 input dtypes,
and PDL


  Performance
- 1.16x geometric mean speedup over the CUDA backend across 99 (M, K)
configurations on B200
  - Faster in 85/99 cases, worst case 0.98x
  - Achieves up to 6.7 TB/s memory bandwidth (84% of B200 peak)
  
Performance Sweeps in M (rows) and K (cols) space comparing the two
backends:
B200:
```
================================================================================                                                                                                                                                                                                                                  
Summary: CuTe-DSL speedup over CUDA  (>1 = CuTe-DSL faster)                                                                                                                                                                                                                                                       
================================================================================                                                                                                                                                                                                                                  
M\K          512    1024    2048    4096    6144    8192   12288   16384   32768                                                                                                                                                                                                                                  
--------------------------------------------------------------------------------                                                                                                                                                                                                                                  
128         1.10    1.13    1.14    1.22    1.43    1.43    1.34    1.52    1.55                                                                                                                                                                                                                                  
256         1.12    1.14    1.19    1.24    1.41    1.38    1.31    1.43    1.43                                                                                                                                                                                                                                  
512         1.18    1.17    1.27    1.39    1.45    1.40    1.28    1.35    1.31                                                                                                                                                                                                                                  
1024        1.18    1.18    1.22    1.24    1.30    1.31    1.35    1.37    1.34                                                                                                                                                                                                                                  
2048        1.16    1.17    1.21    1.17    1.20    1.15    1.17    1.16    1.11                                                                                                                                                                                                                                  
4096        1.14    1.14    1.16    1.10    1.09    1.09    1.07    1.06    1.04                                                                                                                                                                                                                                  
8192        1.19    1.14    1.14    1.10    1.08    1.08    1.06    1.05    1.02                                                                                                                                                                                                                                  
16384       1.25    1.16    1.10    1.10    1.10    1.11    1.09    1.09    1.10                                                                                                                                                                                                                                  
32768       1.25    1.06    1.02    1.02    1.01    1.02    1.00    0.99    1.00                                                                                                                                                                                                                                  
65536       1.21    1.07    0.99    1.00    0.99    0.99    0.99    0.99    0.99                                                                                                                                                                                                                                  
131072      1.37    1.09    0.99    0.98    0.98    0.98    0.98    1.01    0.99                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                                  
Geometric mean: 1.15x                                                                                                                                                                                                                                                                                             
Min: 0.98x   Max: 1.55x                                                                                                                                                                                                                                                                                           
Cases where CuTe-DSL faster: 85/99 
```
RTX PRO 6000 Workstation:
```
================================================================================
Summary: CuTe-DSL speedup over CUDA  (>1 = CuTe-DSL faster)
================================================================================
M\K          512    1024    2048    4096    6144    8192   12288   16384   32768
--------------------------------------------------------------------------------
128         1.10    1.05    0.92    0.95    1.52    1.15    1.10    1.19    1.11
256         1.04    0.94    1.03    1.06    1.27    1.27    1.05    1.07    1.06
512         0.98    0.95    0.98    1.01    1.12    1.10    1.09    1.03    1.06
1024        1.32    1.34    1.35    1.28    1.34    1.22    1.13    1.03    0.99
2048        1.33    1.33    1.16    1.08    1.14    1.06    1.01    1.00    1.01
4096        1.51    1.35    1.15    1.04    1.04    1.01    1.00    1.00    1.00
8192        1.41    1.16    1.04    1.02    1.00    1.01    1.00    1.00    1.00
16384       1.16    1.05    1.01    1.01    1.00    1.00    1.00    1.00    1.00
32768       1.03    1.02    1.01    1.00    1.00    1.00    1.00    1.00    1.00
65536       1.03    1.01    1.00    1.00    1.00    1.00    1.00    1.00    1.00
131072      1.01    1.01    1.00    1.00    1.01    1.00    1.00    1.00    0.99

Geometric mean: 1.07x
Min: 0.92x   Max: 1.52x
Cases where CuTe-DSL faster: 86/99
```
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

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
* Added CuTe-DSL backend support for NVFP4/MXFP4 FP4 quantization with
experimental backend selection.
* Introduced configurable scale-factor layouts (128x4, 8x4, linear) and
new layout-aware quantization paths.
* Extended public quantization APIs with a backend parameter and
CuTe-DSL execution paths.

* **Tests**
* Added comprehensive backend-parametrized tests exercising CUDA vs
CuTe-DSL parity, NVFP4 layouts, FP8 inputs, and large-shape TMA
scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3316
- **最后更新**: 2026-03-26T18:42:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33174
- **最后更新**: 2026-03-26T18:49:26Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, kaixuanliu

## AI分析总结

### 1. 主要更新类型
- **Bug修复**：修复了Claude工作流中的权限配置问题。
- **代码优化**：移除了Flux-Control示例中的硬件设备硬编码，提升代码可移植性。

### 2. 关键变更点及其与项目整体方向的关系
- **Claude工作流修复**：确保自动化流程（如CI/CD）具有正确的写入权限，符合项目对稳定开发和协作效率的重视。
- **设备硬编码移除**：将示例代码从依赖特定硬件（如`device="cuda"`）改为动态适配，**支持更广泛的硬件生态**（如Intel设备），与项目推动**跨平台兼容性**和**可访问性**的目标一致。

### 3. 对项目的影响和潜在意义
- **提升开发流程可靠性**：修复工作流权限可避免后续自动化任务失败，减少协作中断。
- **增强示例代码的通用性**：使Flux-Control示例能在不同硬件环境（CPU/GPU）中直接运行，**降低用户使用门槛**，促进模型测试和部署的灵活性。

### 4. 值得关注的技术点
- **权限配置精细化**：`id-token`的写入权限调整反映了对云原生工具链安全性的关注。
- **硬件抽象化**：示例代码通过移除硬编码，**倡导设备无关的设计模式**，有利于项目适配多样化的部署场景（如边缘计算或混合云环境）。

### 5. 基于项目背景的提交影响分析
- **背景关联**：Diffusers作为扩散模型库，旨在提供易用、高效的模型实现。这些提交虽小，但直接支持其核心目标：
  - **稳定性保障**：工作流修复维护了项目持续集成和文档更新的流畅性，确保开源协作质量。
  - **生态扩展**：硬件适配优化**呼应了项目对多硬件支持的战略**（如Intel合作），有助于扩大用户基础，推动扩散模型在更广泛设备上的应用。

---
**总结**：昨日更新虽为局部调整，但通过修复自动化流程和提升代码可移植性，**强化了项目的工程稳健性和跨平台友好性**，间接支持了Diffusers作为主流扩散模型库的长期生态建设。

## 详细提交记录

### [b757035](https://github.com/huggingface/diffusers/commit/b757035df6fe080b56a672c4000e458bb442821a)

- **作者**: Sayak Paul
- **时间**: 2026-03-26T10:09:10Z
- **提交信息**: fix claude workflow to include id-token with write. (#13338)

### [41e1003](https://github.com/huggingface/diffusers/commit/41e1003316173218656998281b28f9e0f6fcbcff)

- **作者**: kaixuanliu
- **时间**: 2026-03-26T07:10:53Z
- **提交信息**: avoid hardcode device in flux-control example (#13336)

Signed-off-by: Liu, Kaixuan <kaixuan.liu@intel.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 387
- **最后更新**: 2026-03-24T05:55:47Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12106
- **最后更新**: 2026-03-26T15:48:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 25071
- **最后更新**: 2026-03-26T23:03:06Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 15
- **主要提交者**: SevenJ, McZyWu, Ho-Ren (Jack) Chuang

## AI分析总结

根据提供的 `sglang` 仓库提交记录和 README 摘要（项目定位为高性能大语言模型推理框架），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位，涉及模型支持、推理崩溃、缓存、依赖加载等多个方面。
- **性能优化**：针对特定硬件（AMD、NPU）和算子（LoRA、注意力机制）进行了优化。
- **CI/CD 与测试**：更新了持续集成流程、测试套件和文档。
- **功能扩展**：新增了对 Apple Silicon MLX 后端的原生支持。
- **依赖更新**：升级了 `xgrammar` 依赖版本。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **修复多模型/适配器问题** (如 Kimi、DBRX、Qwen3-Next、多适配器 LoRA) | 直接提升框架的**模型兼容性**和**稳定性**，这是作为通用推理框架的核心。 |
| **优化硬件特定性能** (AMD、NPU、Apple Silicon MLX) | 践行项目“高性能”目标，通过**硬件适配和算子优化**扩展框架的部署范围和效率。 |
| **修复推理核心组件Bug** (注意力机制、KV缓存、解码、卸载) | 确保**推理过程的核心正确性与可靠性**，是框架可用性的基石。 |
| **增强缓存与配置灵活性** (添加缓存超时、支持无rope参数模型) | 提升框架的**可配置性和鲁棒性**，满足更复杂的生产环境需求。 |
| **重构测试与CI流程** | 提升**代码质量与开发效率**，为项目的长期健康迭代提供保障。 |

### 3. 对项目的影响和潜在意义
- **用户体验**：修复大量模型相关Bug将直接改善终端用户和开发者的使用体验，减少部署障碍。
- **生态扩展**：对 AMD、NPU 和 Apple Silicon 的持续投入，显著拓宽了框架的**硬件生态**，吸引更广泛的用户群体。
- **性能基石**：对注意力机制、KV缓存、LoRA等关键路径的优化，巩固了框架的**性能优势**。
- **维护性**：CI/CD 和测试的改进有助于提升项目的**软件工程质量**，降低回归风险。

### 4. 值得关注的技术点
- **Apple Silicon 原生支持** (`[MLX] Add native MLX execution backend`)：为 Mac 用户提供了高性能的原生推理选项，是重要的生态扩展。
- **硬件特定优化**：如 AMD 的 `fused_topk` 集成、NPU 的 CI 缓存，显示了项目对异构计算生态的深度适配。
- **复杂场景修复**：如多适配器 LoRA、NSA预填与FP8 KV缓存结合等问题的修复，体现了对**前沿/复杂推理场景**的支持能力。
- **扩散模型支持**：多项与 Diffusion 相关的提交，表明项目正在将能力从纯文本 LLM 向**多模态生成领域**延伸。

### 5. 基于项目背景的提交影响分析
`sglang` 旨在成为**高性能、可扩展的LLM服务引擎**。昨日的提交集合清晰地反映了这一目标的执行路径：
1.  **巩固核心（可靠性）**：通过修复 Kimi、DBRX、Qwen 等模型支持和核心推理 Bug，**强化了框架作为通用服务底座的稳定性和可信度**。
2.  **拓宽边界（兼容性与生态）**：
    - **硬件生态**：积极适配 AMD、NPU、Apple Silicon，打破对单一硬件（如NVIDIA CUDA）的依赖，**提升项目在多样化基础设施中的生存力和竞争力**。
    - **模型/任务生态**：不仅修复文本模型，还持续投入扩散模型，**为支持多模态推理铺路**，符合大模型技术发展趋势。
3.  **追求极致（性能）**：不满足于功能可用，持续对 LoRA、注意力、topk 等算子进行底层优化，**体现了对“高性能”这一核心卖点的坚持**。
4.  **保障迭代（工程化）**：通过改进 CI、测试和文档，**为项目在快速迭代中保持高质量提供了系统性保障**，这对一个活跃的开源项目至关重要。

**总结**：昨日的更新是一次典型的“夯实基础、扩展生态、优化体验”的迭代。它没有引入颠覆性特性，而是通过大量细致的工作，从**稳定性、兼容性、性能、可维护性**多个维度，全面巩固和推进了 `sglang` 作为一款生产级 LLM 推理框架的目标。特别是对多种硬件的深度支持和多模态的探索，显示出项目正朝着构建一个**广泛适配、高性能的生成式AI服务基础设施**的方向稳步前进。

## 详细提交记录

### [2e65c27](https://github.com/sgl-project/sglang/commit/2e65c27b29152cc99fac5589a89a79edbc975a81)

- **作者**: SevenJ
- **时间**: 2026-03-26T21:44:37Z
- **提交信息**: Api add flush cache timeout (#21413)

Signed-off-by: root <wenjun7j@gmail.com>

### [8c3ccef](https://github.com/sgl-project/sglang/commit/8c3ccef2d94e185159badc74dcbe07885ad21ff3)

- **作者**: Qiaolin Yu
- **时间**: 2026-03-26T21:40:26Z
- **提交信息**: Fix Kimi K2.5 dp attention+ spec decoding launch crash (#21391)

### [be0cca5](https://github.com/sgl-project/sglang/commit/be0cca5596f97c2eff6f5e7b4ba49f187e7a2e11)

- **作者**: satyamk7054
- **时间**: 2026-03-26T21:35:20Z
- **提交信息**: Use torch.addmm instead of separate mm and add_ calls for LoRA torch.native (#20562)

Co-authored-by: Satyam Kumar <satyamk@linkedin.com>

### [e59ea4f](https://github.com/sgl-project/sglang/commit/e59ea4f6e9aacb50b54fb29b8396d22708b3df79)

- **作者**: satyamk7054
- **时间**: 2026-03-26T21:34:16Z
- **提交信息**: fix: torch-native LoRA for multi-adapter case (#20564)

Co-authored-by: Satyam Kumar <satyamk@linkedin.com>

### [fb90c9d](https://github.com/sgl-project/sglang/commit/fb90c9d298eeeb15fde5de1c7676cfc3d9a4b6ee)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-26T21:26:46Z
- **提交信息**: [Test] Consolidate eval accuracy test mixins into eval_accuracy_kit (#21047)

### [e5dd411](https://github.com/sgl-project/sglang/commit/e5dd411f64b5860e1fa5d36c1d781eb9bed0d647)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-26T20:50:13Z
- **提交信息**: [CI] Add ci-workflow-guide skill and consolidate CI docs (#21429)

### [e5b7650](https://github.com/sgl-project/sglang/commit/e5b7650353234754a92116b9fd5478dd3bfffa13)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-26T20:00:16Z
- **提交信息**: Fix UnboundLocalError when DetokenizerManager constructor fails (#21471)

### [17f43d1](https://github.com/sgl-project/sglang/commit/17f43d15187be710828a1ff6a4843fdddb0b1eb7)

- **作者**: Liangsheng Yin
- **时间**: 2026-03-26T19:54:51Z
- **提交信息**: [CI] Skip stage health check for release branch cut (#21488)

### [4b5f63e](https://github.com/sgl-project/sglang/commit/4b5f63e1b8ba37f26d71caf2a6004e473db53675)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-03-26T19:50:50Z
- **提交信息**: FIX: (NSA) Compute topk_indices_offset when NSA prefill flashmla_sparse is used with FP8 KV cache (#20606)

Signed-off-by: Ho-Ren (Jack) Chuang <horenchuang@bytedance.com>

### [3867c64](https://github.com/sgl-project/sglang/commit/3867c6431ae3388eda30d3f3f960d32abe380273)

- **作者**: jianzhao-xu
- **时间**: 2026-03-26T18:23:30Z
- **提交信息**: Fix bug in dbrx model (#21445)

Co-authored-by: Jianzhao Xu <xujianchao@huawei.com>

### [646573e](https://github.com/sgl-project/sglang/commit/646573e4e8d10c2684e0563bc40915b4bef874f4)

- **作者**: shuwenn
- **时间**: 2026-03-26T18:22:12Z
- **提交信息**: fix: use get_rope_config() to support models without rope_parameters (#21135)

### [0906e45](https://github.com/sgl-project/sglang/commit/0906e45cec97abf3aa8ee9cf8962f6a5d36ed4f1)

- **作者**: McZyWu
- **时间**: 2026-03-26T13:21:00Z
- **提交信息**: bugfix for weight loading for qwen3-next (#21313)

### [8febc36](https://github.com/sgl-project/sglang/commit/8febc3650d0490db2ed3fcc471b6925028dc027c)

- **作者**: monkeyLoveding
- **时间**: 2026-03-26T11:35:34Z
- **提交信息**: [NPU] multimodal-gen-test-8-npu-a3,Cache pytorch dependency (#21470)

Co-authored-by: Kelon <kelonlu@163.com>

### [013fa55](https://github.com/sgl-project/sglang/commit/013fa5563022f921e0e2f634a946cbcecbc082b2)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-03-26T10:16:33Z
- **提交信息**: [AMD] CI - fix amd 4-GPU PR test (#21444)

### [238a4b8](https://github.com/sgl-project/sglang/commit/238a4b8f8f5d5a550820de2dcd0da160136af16d)

- **作者**: Mick
- **时间**: 2026-03-26T08:33:22Z
- **提交信息**: [diffusion] CI: fix breaking import path in nightly (#21449)

### [35720d9](https://github.com/sgl-project/sglang/commit/35720d9969ef404566c0d5801c072bf0085255d1)

- **作者**: Mick
- **时间**: 2026-03-26T08:31:44Z
- **提交信息**: [diffusion] fix: fix qwen-image with nunchaku (#21415)

### [f289d17](https://github.com/sgl-project/sglang/commit/f289d173aa6031a01c4300c14584fa48ffa6e36e)

- **作者**: Anant Sharma
- **时间**: 2026-03-26T08:22:37Z
- **提交信息**: [Deps] Bump xgrammar to 0.1.32 (#21032)

### [fd53594](https://github.com/sgl-project/sglang/commit/fd535942acfe4fa63b46040bd26f411be04a2995)

- **作者**: Chen, Zhentao
- **时间**: 2026-03-26T07:57:56Z
- **提交信息**: [AMD]Integrate aiter's fused_topk for softmax scoring in topk function (#21421)

Co-authored-by: Chen, Todd <zhenchen@amd.com>

### [a305964](https://github.com/sgl-project/sglang/commit/a3059641593b985387a6abbb70c19c4ddc53cf1e)

- **作者**: R0CKSTAR
- **时间**: 2026-03-26T07:09:17Z
- **提交信息**: [MLX] Add native MLX execution backend for Apple Silicon Mac (#20342)

Signed-off-by: Xiaodong Ye <yeahdongcn@gmail.com>

### [7ca015f](https://github.com/sgl-project/sglang/commit/7ca015fe65e5369df8cc4936f48617dca269b1b2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-03-26T07:02:02Z
- **提交信息**: [Diffusion] Refactor diffusion JIT kernel test layout and narrow CI triggers (#21385)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with hybrid cache acceleration and massive parallelism for DiTs.
- **语言**: Python
- **星标数**: 1108
- **最后更新**: 2026-03-26T13:56:15Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据提供的README摘要和提交记录，以下是针对vipshop/cache-dit仓库昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：修复量化配置问题（#920）。
- **功能新增**：支持FP8（8位浮点数）每张量（per-tensor）回退机制（#919）。

### 2. 关键变更点及其与项目整体方向的关系
- **修复量化配置**：确保量化模块的配置正确性，提升推理引擎的稳定性和可靠性。
- **新增FP8每张量回退支持**：扩展量化功能，允许在特定情况下（如硬件不支持更细粒度量化时）使用每张量级别的FP8量化，增强兼容性和灵活性。
- **与项目方向关系**：cache-dit作为PyTorch原生推理引擎，专注于混合缓存加速和大规模并行化。这些更新强化了其量化能力，有助于优化模型推理时的内存使用和计算效率，符合项目提升DiT（Diffusion Transformers）推理性能的核心目标。

### 3. 对项目的影响和潜在意义
- **稳定性提升**：修复配置问题可减少因量化错误导致的运行时异常。
- **性能优化潜力**：FP8量化支持可能降低内存带宽需求，加速计算，特别是在支持FP8的硬件（如新一代GPU）上。
- **兼容性增强**：回退机制使引擎能在更广泛的硬件环境中有效运行，扩大适用场景。

### 4. 值得关注的技术点
- **FP8量化**：作为一种新兴的低精度格式，FP8在保持模型精度的同时显著提升效率，是边缘计算和高效推理的前沿技术。
- **每张量回退策略**：体现了量化实现的灵活性，确保在硬件限制下仍能提供可行的优化方案。
- **量化配置管理**：强调配置正确性对量化效果的关键作用，可能涉及量化参数（如缩放因子、零点）的校准或验证。

### 5. 基于项目背景的提交影响分析
- **项目背景**：cache-dit旨在通过混合缓存和并行化加速DiT推理，量化是减少模型大小、提升推理速度的重要手段。
- **发展影响**：
  - **功能完善**：这些提交丰富了量化选项，使引擎能更好地适应不同精度和硬件需求，提升整体竞争力。
  - **用户体验**：修复Bug提高可靠性，新增功能增加灵活性，有助于吸引更多用户采用。
  - **技术前沿性**：支持FP8量化保持项目与行业趋势同步，可能为后续集成更先进的优化技术奠定基础。

**总结**：昨日更新聚焦于量化模块的改进，通过修复和功能增强，进一步巩固了cache-dit作为高效DiT推理引擎的技术基础，有助于其在性能和兼容性方面持续优化。

## 详细提交记录

### [bf823ac](https://github.com/vipshop/cache-dit/commit/bf823aca86b7346549de9b69187db3be741c00ee)

- **作者**: DefTruth
- **时间**: 2026-03-26T10:22:32Z
- **提交信息**: quant: fix quantize config (#920)

### [4990aea](https://github.com/vipshop/cache-dit/commit/4990aeaab37823eb0cee840c686e8f8b2e420993)

- **作者**: DefTruth
- **时间**: 2026-03-26T10:05:07Z
- **提交信息**: quant: support fp8 per-tensor fallback (#919)

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

* quant: support fp8 per-tensor fallback

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 74433
- **最后更新**: 2026-03-26T23:07:06Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 21
- **主要提交者**: TJian, Divakar Verma, Zhewen Li

## AI分析总结

根据提供的提交记录和项目README摘要（vLLM：面向所有人的易用、快速、经济的LLM服务引擎），以下是昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占主导地位，涉及Transformers配置、ROCm平台、CUDA图、错误消息等多个方面。
- **CI/CD与测试**：大量针对ROCm平台的CI流程修复、测试用例添加和稳定性改进。
- **功能优化/调整**：包括模型运行器（Model Runner）的拒绝采样控制、XPU图形默认禁用、无用代码清理等。
- **文档更新**：修复文档中的过时引用和错误。
- **重构**：渲染器（Renderer）工厂方法整合、模型处理器辅助函数使用。
- **回退**：回退了Flashinfer的nvfp4 moe内核集成。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 与项目方向的关系 |
| :--- | :--- |
| **Transformers v5配置修复** (`f73bcb1`) | 确保vLLM与主流模型库（Transformers）新版本的兼容性，支持更广泛的模型，符合“为所有人服务”的目标。 |
| **多节点AllReduce融合修复** (`0904b65`) | 提升多节点分布式推理的性能和稳定性，对大规模、低成本服务至关重要。 |
| **ROCm平台的大量修复与测试增强** (多个提交) | 显著加强对AMD GPU平台（ROCm）的支持，扩大硬件生态覆盖，体现“便宜”和“面向所有人”的宗旨。 |
| **模型运行器V2支持强制接受率** (`c32e976`) | 增强推理生成的控制能力，提升输出质量，改善开发者体验。 |
| **CUDA图持久化缓冲区恢复（FP8 FlashMLA）** (`0aac204`) | 修复高性能推理路径（CUDA图+FP8量化）的关键Bug，直接服务于“快速”的核心目标。 |
| **DeepGemm E8M0精度修复（Qwen3.5 FP8 on Blackwell）** (`5206901`) | 针对最新硬件（NVIDIA Blackwell）和模型（Qwen3.5）的FP8量化精度进行优化，是追求极致性能和效率的前沿工作。 |

### 3. 对项目的影响和潜在意义
- **稳定性与可靠性提升**：大量Bug修复，尤其是跨平台（ROCm）和核心性能特性（CUDA图、AllReduce）的修复，直接提升生产环境稳定性。
- **硬件生态扩展**：对ROCm的持续投入（CI流水线、测试覆盖、版本发布）使vLLM在AMD GPU上更可靠，降低了用户部署成本。
- **性能与功能前沿探索**：对FP8量化、Blackwell架构、Mamba模型、拒绝采样等功能的改进，保持vLLM在高性能LLM推理领域的技术竞争力。
- **开发者体验改善**：文档修复、错误信息优化、无用代码清理，使项目更易于理解和使用。
- **维护健康度**：回退有问题的内核集成、重组测试用例，显示了对代码质量和长期可维护性的关注。

### 4. 值得关注的技术点
- **FP8量化与最新硬件**：提交`5206901`专门修复了在Blackwell GPU上运行Qwen3.5 FP8模型的精度问题，这是追求极致推理效率的关键技术。
- **多节点通信优化**：提交`0904b65`修复的多节点AllReduce融合问题，对分布式推理的扩展性和效率至关重要。
- **ROCm平台的成熟度**：昨日有近三分之一提交与ROCm相关，涉及内核、CI、测试、发布全链路，表明vLLM正在将AMD GPU支持推向生产就绪状态。
- **模型运行器V2的演进**：提交`c32e976`为拒绝采样增加了更细粒度的控制，表明推理引擎的生成策略正在变得更加灵活和可控。
- **Mamba等新架构支持**：提交`b9dbc5c`为Mamba模型添加测试，显示项目正持续集成新兴的高效模型架构。

### 5. 基于项目背景的提交影响分析
vLLM的目标是提供**易用、快速、经济**的LLM服务。昨日的提交集体体现了对这一目标的全面推动：
- **快速**：通过修复CUDA图、AllReduce融合、FP8精度等核心性能路径的Bug，并探索新的控制功能（如强制接受率），直接保障和提升了推理速度。
- **经济**：通过对**ROCm平台的大力投入**，显著降低了用户使用AMD GPU进行推理的门槛和成本，拓宽了“经济”的硬件选择范围。
- **易用**：通过修复Transformers配置、文档错误、错误消息，以及回退不稳定的内核，提升了框架的兼容性、可理解性和稳定性，让开发者更容易集成和使用。
- **生态发展**：支持多种硬件（NVIDIA, AMD, Intel XPU, Arm CPU）、修复多种模型（Transformers v5, Qwen3.5, GLM, Mamba）的问题，使vLLM的生态更加健壮和多元化，巩固其作为主流LLM服务引擎的地位。

**总结**：昨日的更新是一次以**稳定性修复和平台扩展**为主的常规推进，重点夯实了AMD ROCm平台的支持，并修复了多个影响核心性能与可靠性的关键问题。这些工作紧密围绕项目核心目标，通过提升跨平台能力、修复性能瓶颈、改善开发者体验，持续巩固vLLM作为高效、开放LLM推理引擎的领先地位。

## 详细提交记录

### [f73bcb1](https://github.com/vllm-project/vllm/commit/f73bcb1c51cfc764f534fcd109f8437e196be2ec)

- **作者**: Harry Mellor
- **时间**: 2026-03-26T23:06:59Z
- **提交信息**: Various Transformers v5 config fixes (#38247)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [28048bd](https://github.com/vllm-project/vllm/commit/28048bd6b09cb164a934a8c134b7d7a7f4733b4f)

- **作者**: yzong-rh
- **时间**: 2026-03-26T21:43:03Z
- **提交信息**: [Bugfix] Add missing f-string prefix in xgrammar choices error message (#38162)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [c32e976](https://github.com/vllm-project/vllm/commit/c32e97602d54f34fb60ff956dae09f9a557ec50a)

- **作者**: Giancarlo Delfin
- **时间**: 2026-03-26T20:38:12Z
- **提交信息**: [Model Runner V2] Enable forcing a specific acceptance rate during rejection sampling (#38045)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>

### [0904b65](https://github.com/vllm-project/vllm/commit/0904b6550d8e2d11295762fabf3f0d7972bd0300)

- **作者**: Wei Zhao
- **时间**: 2026-03-26T20:24:36Z
- **提交信息**: Fix multi-node allreduce fusion (#38136)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: root <root@theia0053.lyris.clusters.nvidia.com>

### [f26fcdf](https://github.com/vllm-project/vllm/commit/f26fcdfb9e50fef30381ed27fa956f7a43b0b1aa)

- **作者**: Stig-Arne Grönroos
- **时间**: 2026-03-26T19:01:05Z
- **提交信息**: [Bugfix][ROCm] Fix lru_cache on paged_mqa_logits_module (#37547)

Signed-off-by: Stig-Arne Grönroos <stig-arne.gronroos@amd.com>

### [bc9c6fb](https://github.com/vllm-project/vllm/commit/bc9c6fbbe655072a0ff924a44b1069bd11ba0772)

- **作者**: TJian
- **时间**: 2026-03-26T18:47:10Z
- **提交信息**: [ROCm] [Bugfix] [Release] Fix nightly rocm release pipeline (#38263)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [bff9a1c](https://github.com/vllm-project/vllm/commit/bff9a1c2666de363d5b34f629e9fa61455a338ca)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T18:33:45Z
- **提交信息**: [ROCm][CI] Override PYTORCH_ROCM_ARCH with detected GPU arch in test containers (#38165)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [db01535](https://github.com/vllm-project/vllm/commit/db01535e2bd5641e8cd7f88e5febf1d2a26bfbce)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T17:44:01Z
- **提交信息**: [ROCm][CI] Add uv pip compile workflow for rocm-test.txt lockfile (#37930)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [a4cf9b2](https://github.com/vllm-project/vllm/commit/a4cf9b22ba8f08df8d7977c2b0753fe20231cffc)

- **作者**: jennyyyyzhen
- **时间**: 2026-03-26T17:33:39Z
- **提交信息**: [ROCM][Bugfix] Use correct stride in cp_mha_gather_cache_kernel for hybrid model (#37228) (#37228)

Signed-off-by: jennyyyyzhen <yzhen@hmc.edu>
Co-authored-by: yZhen <yZhen@fb.com>

### [9c3ae04](https://github.com/vllm-project/vllm/commit/9c3ae04bfe6532d6d6d812ae6688366c9911555b)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T16:51:18Z
- **提交信息**: [ROCm][CI] Add LM Eval Qwen3.5 Models test for MI355 (#38155)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [a8e48a7](https://github.com/vllm-project/vllm/commit/a8e48a7b85f035df401cab03dfb11b16f98aa413)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T16:46:03Z
- **提交信息**: [CI] Fix conch kernel crash on 3D input by reshaping to 2D before GEMM (#38178)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [b9dbc5c](https://github.com/vllm-project/vllm/commit/b9dbc5c4ab2b01f626376ffaeb68e575e70ff58c)

- **作者**: Divakar Verma
- **时间**: 2026-03-26T16:40:35Z
- **提交信息**: [Mamba][APC] Add test case to compare apc outputs  (#34977)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>

### [60af7b9](https://github.com/vllm-project/vllm/commit/60af7b967bf52aa9623aa4f224a0d281757ba9b0)

- **作者**: TJian
- **时间**: 2026-03-26T16:32:25Z
- **提交信息**: [Releases] [ROCm] Enable Nightly Docker Image and Wheel Releases for ROCm (#37283)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>
Co-authored-by: Hongxia Yang <hongxiay.yang@amd.com>

### [bdc1719](https://github.com/vllm-project/vllm/commit/bdc1719eb9b27ef4a30c1f753b406bf05c8edd3a)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T16:26:46Z
- **提交信息**: [ROCm][CI] Fix AITER state leak in shared_fused_moe_routed_transform test (#38137)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [0aac204](https://github.com/vllm-project/vllm/commit/0aac2048bf3a7e60eaddf1ebcb4165ed777eb8ff)

- **作者**: haosdent
- **时间**: 2026-03-26T16:13:39Z
- **提交信息**: [Bugfix] Restore CUDA graph persistent buffers for FP8 FlashMLA decode (#35175)

Signed-off-by: haosdent <haosdent@gmail.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [cb22632](https://github.com/vllm-project/vllm/commit/cb2263218e6638cc1982d7f7a0be735e8cc46ab5)

- **作者**: Chuan (Richard) Li
- **时间**: 2026-03-26T15:59:24Z
- **提交信息**: [Bugfix][Minor] Fix potential NameError in mamba backend selector and misc typos (#35886)

Signed-off-by: Li <chuali@amd.com>

### [e054f15](https://github.com/vllm-project/vllm/commit/e054f152faa48ab27389f490d6e86c959d86d122)

- **作者**: Wentao Ye
- **时间**: 2026-03-26T15:54:54Z
- **提交信息**: [CI] Add batch invariant test for b200 (#38014)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [0f5b526](https://github.com/vllm-project/vllm/commit/0f5b5260401e3c59adec8ffc078ae0f799b08f80)

- **作者**: zhang-prog
- **时间**: 2026-03-26T15:34:49Z
- **提交信息**: [Fix] Remove unused packing_position_embedding from PaddleOCRVL for better checkpoint compatibility (#38232)

Signed-off-by: zhangyue66 <zhangyue66@baidu.com>

### [be1a85b](https://github.com/vllm-project/vllm/commit/be1a85b7a2929f25c93d469fdd733a3576609e70)

- **作者**: Zhewen Li
- **时间**: 2026-03-26T14:59:09Z
- **提交信息**: Revert "[MoE Kernel] Flashinfer nvfp4 cutedsl moe kernel integration" (#38050) (#38169)

Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

### [2e225f7](https://github.com/vllm-project/vllm/commit/2e225f7bd23f533e3ffd909fd5596a85f352c518)

- **作者**: Cyrus Leung
- **时间**: 2026-03-26T12:19:22Z
- **提交信息**: [Renderer] Consolidate factory methods (#38218)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [757eafc](https://github.com/vllm-project/vllm/commit/757eafcf37ba1db654bf9abb96e39054af0dc69d)

- **作者**: Jared Wen
- **时间**: 2026-03-26T12:11:21Z
- **提交信息**: [bug-fix] GLM OCR Patch Merger context_dim (#37962)

Signed-off-by: JaredforReal <w13431838023@gmail.com>

### [dcdc145](https://github.com/vllm-project/vllm/commit/dcdc1458931a1a57cbcadb92b2dfc10d225d675f)

- **作者**: wang.yuqi
- **时间**: 2026-03-26T12:07:01Z
- **提交信息**: [CI] Reorganize scoring tests (#38207)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [f2d1620](https://github.com/vllm-project/vllm/commit/f2d16207c794e40c323adec50245ceecc4e6b635)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T11:57:00Z
- **提交信息**: [ROCm][CI] Fix flaky GPTQ compile correctness test (#38161)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [37a8300](https://github.com/vllm-project/vllm/commit/37a83007fef9925609a8d9b7c7b86bb41dab4e5d)

- **作者**: Andreas Karatzas
- **时间**: 2026-03-26T11:54:59Z
- **提交信息**: [ROCm][CI] Fix wvSplitKrc mock argument order in test_rocm_unquantized_gemm (#38167)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [bf5eec6](https://github.com/vllm-project/vllm/commit/bf5eec638d7571f0b88ea48a3d13709322b19a0c)

- **作者**: Wentao Ye
- **时间**: 2026-03-26T09:08:19Z
- **提交信息**: [Refactor] Remove unused utils (#38153)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [b1cb1d3](https://github.com/vllm-project/vllm/commit/b1cb1d3d2c2332e2bd30d63ba18ff6a4a046c122)

- **作者**: Mateusz Sokół
- **时间**: 2026-03-26T08:55:42Z
- **提交信息**: DOC: Documentation pages fixes (#38125)

Signed-off-by: Mateusz Sokół <mat646@gmail.com>

### [6ae8bbd](https://github.com/vllm-project/vllm/commit/6ae8bbd0c2fa5b057f0c3066bc6519792f7048af)

- **作者**: Kunshang Ji
- **时间**: 2026-03-26T08:53:45Z
- **提交信息**: [XPU] Disable xpu graph by default (#38193)

Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>

### [a9213c0](https://github.com/vllm-project/vllm/commit/a9213c0ffea4c6485dd1d03de5e8b3ff96dda924)

- **作者**: Cyrus Leung
- **时间**: 2026-03-26T08:52:38Z
- **提交信息**: [Doc] Fix outdated reference to CUDAGraphManager (#38209)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [502c41a](https://github.com/vllm-project/vllm/commit/502c41a8f65e50f394882c6f957ef22b0bdef5a4)

- **作者**: Cyrus Leung
- **时间**: 2026-03-26T08:44:04Z
- **提交信息**: [Model] Use helper function to run MM processors with token inputs (where applicable) (#38018)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>

### [5206901](https://github.com/vllm-project/vllm/commit/52069012fe53714581682ded6746cd311108bf3a)

- **作者**: Vadim Gimpelson
- **时间**: 2026-03-26T08:21:47Z
- **提交信息**: [Bugfix] Fix DeepGemm E8M0 accuracy degradation for Qwen3.5 FP8 on Blackwell (#38083)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>

### [71161e8](https://github.com/vllm-project/vllm/commit/71161e8b63f9534d6ac5e098a4874621164d1f1e)

- **作者**: Fadi Arafeh
- **时间**: 2026-03-26T07:03:31Z
- **提交信息**: [cpu][ci] remove soft-fail for Arm CI and add quant model tests (#37691)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-03-27
**监控日期**: 2026-03-26
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 3919
- **最后更新**: 2026-03-26T23:03:05Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 13
- **主要提交者**: WeiQing Chen, Daniel Huang, Baoyuan Qi

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：占比最高（6项），涉及图像生成、TTS语音、运行时隔离、异步引擎等多个核心模块。
- **测试与验证**：新增3项针对扩散模型（Diffusion）和音频模型的完整功能测试。
- **CI/持续集成**：2项更新，修复测试超时和模型识别问题。
- **文档改进**：1项关于扩散生成参数的文档优化。
- **兼容性增强**：1项为音频分词器添加多注意力后端支持。
- **性能基准**：1项新增图像生成（t2i/i2i）的准确性基准测试集成。

### 2. 关键变更点及其与项目方向的关系
- **扩散模型稳定性**：多项修复（如TP模式下的图像损坏、预处理问题）和测试（L4、Wan2.2）表明项目正**强化多模态图像生成的工业级可靠性**，与“fast and cheap omni-modality serving”目标一致。
- **语音/音频模块完善**：针对Qwen3TTS和Voxtral的Bug修复（语音上传、嵌入加载）体现了对**语音合成服务可用性**的重视，支持“omni-modality”中的语音模态。
- **运行时与引擎优化**：修复异步引擎挂起问题和设备隔离问题，直接提升**服务稳定性和资源利用率**，符合高性能推理服务的定位。
- **测试与质量保障**：新增准确性基准测试和CI修复，显示项目在**规模化服务过程中注重质量监控与回归预防**。

### 3. 对项目的影响和潜在意义
- **用户体验提升**：减少图像生成错误、语音合成故障，增强终端用户服务的确定性。
- **开发者体验改善**：更清晰的生成参数文档和更稳定的异步API，降低集成难度。
- **生产就绪度提高**：通过针对性测试和基准测试，为大规模部署提供可靠性验证。
- **社区与生态贡献**：兼容性增强（如音频注意力后端）可能促进更多模型适配和社区集成。

### 4. 值得关注的技术点
- **TP（Tensor Parallelism）下的扩散模型修复**：涉及分布式推理中的随机种子与图像完整性，对高性能多卡服务至关重要。
- **多注意力后端支持**（MIMO-Audio Tokenizer）：可能为音频模型提供更灵活的硬件/内核优化选择。
- **异步引擎挂起问题修复**：涉及并发请求处理，直接影响高吞吐服务的稳定性。
- **准确性基准测试集成**：为多模态生成质量提供量化评估框架，是服务标准化的重要一步。

### 5. 基于项目背景的提交影响分析
vllm-omni旨在提供**统一、高效、低成本的多模态模型服务**。昨日的更新整体上：
- **强化了核心模态（图像、语音）的可靠性**：通过密集的Bug修复和测试，确保扩散模型和TTS在复杂配置（如TP、异步）下稳定工作，直接支撑“easy and fast”的服务承诺。
- **提升了服务的鲁棒性与可维护性**：CI修复、基准测试和文档改进有助于项目在快速迭代中保持质量，支持“for everyone”的开放服务愿景。
- **体现了向生产环境深度优化的趋势**：关注设备隔离、异步引擎、分布式错误等生产级问题，表明项目从“功能可用”向“企业级可靠”演进。

这些提交共同推动vllm-omni从一个多模态推理框架向一个**成熟、稳定的云原生服务基础设施**迈进，符合其作为下一代Omni-Modality Serving平台的长远目标。

## 详细提交记录

### [a678595](https://github.com/vllm-project/vllm-omni/commit/a67859574d72beb2f8d993bd38b9eda7258f6837)

- **作者**: Peiqi Yin
- **时间**: 2026-03-26T18:16:08Z
- **提交信息**: [Test] L4 complete diffusion feature test for Z-Image (#2132)

Signed-off-by: yinpe <11810305@mail.sustech.edu.cn>

### [590ab5b](https://github.com/vllm-project/vllm-omni/commit/590ab5b3e98c534f888ce8c545c7dde86e8a4579)

- **作者**: Cheung Ka Wai
- **时间**: 2026-03-26T16:56:46Z
- **提交信息**: [Bug Fix] Resolve broken image issue when TP is enabled and no seed is provided. (#2176)

Signed-off-by: Mike Cheung <zhtmike@gmail.com>

### [66d5478](https://github.com/vllm-project/vllm-omni/commit/66d5478dad437c5c39d5fe235311ce1ee4df195f)

- **作者**: Baoyuan Qi
- **时间**: 2026-03-26T16:47:53Z
- **提交信息**: [Compatibility] Add Multiple Attention Backends Support in MIMO-Audio Tokenizer (#2225)

Signed-off-by: 齐保元 <qibaoyuan@xiaomi.com>

### [e3d178c](https://github.com/vllm-project/vllm-omni/commit/e3d178cd663fe8f1b450f3b2ec4f1953e140b5d7)

- **作者**: Dnoob
- **时间**: 2026-03-26T16:26:59Z
- **提交信息**: [Bugfix] Fix diffusion benchmark issues #1873 (#1897)

Signed-off-by: Dnoob <dxpouo@gmail.com>

### [d96d63c](https://github.com/vllm-project/vllm-omni/commit/d96d63cb7fbdd839ff0f893434d63c56d2a41257)

- **作者**: Samit
- **时间**: 2026-03-26T15:12:16Z
- **提交信息**: [Doc] Improve diffusion generation parameter docs for online serving (#2051)

Signed-off-by: samithuang <285365963@qq.com>
Signed-off-by: Samit <285365963@qq.com>
Signed-off-by: gcanlin <canlinguosdu@gmail.com>
Co-authored-by: Zeyu Huang | 黃澤宇 <11222265+fhfuih@users.noreply.github.com>
Co-authored-by: gcanlin <canlinguosdu@gmail.com>

### [574ec99](https://github.com/vllm-project/vllm-omni/commit/574ec99ef490804b4ed007e2e4c34e58b561e9a7)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-03-26T14:26:52Z
- **提交信息**: [Qwen3TTS][ServingSpeech] Bugfix/voice upload and add optional ref_text (#2046)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [3a5483d](https://github.com/vllm-project/vllm-omni/commit/3a5483d339a7eb790bfa0b8d3deffad6e5636db2)

- **作者**: WeiQing Chen
- **时间**: 2026-03-26T14:03:03Z
- **提交信息**: [CI] fix Wan22 timeout and i2i accuracy threshold (#2235)

Signed-off-by: David Chen <530634352@qq.com>

### [9857ed2](https://github.com/vllm-project/vllm-omni/commit/9857ed2839cbcc56648b650f2186b93f75f00831)

- **作者**: Yueqian Lin
- **时间**: 2026-03-26T13:34:31Z
- **提交信息**: [Bugfix] Fix Voxtral TTS voice embeddings not loading (#2156)

Signed-off-by: linyueqian <linyueqian@outlook.com>

### [c9e2d2c](https://github.com/vllm-project/vllm-omni/commit/c9e2d2c39458ba9920d27862253cb66e448ac958)

- **作者**: Junhong Liu
- **时间**: 2026-03-26T11:54:18Z
- **提交信息**: [CI] qwen2.5-omni model cannot recognize the synthetic video (#2211)

Signed-off-by: Junhong Liu <98734602+LJH-LBJ@users.noreply.github.com>

### [15df8ec](https://github.com/vllm-project/vllm-omni/commit/15df8ec97f8667d76638e780480f2cca7e9d76e5)

- **作者**: Jared Wen
- **时间**: 2026-03-26T10:50:54Z
- **提交信息**: [Bug Fix] GLM-Image stage device isolation and t2i prompt preprocessing in Omni runtime (#2137)

### [2dde219](https://github.com/vllm-project/vllm-omni/commit/2dde219c00669e3b6cd11c191084f6e2b877d6c3)

- **作者**: bjf-frz
- **时间**: 2026-03-26T10:18:23Z
- **提交信息**: [Test] L4 complete diffusion feature test for Wan2.2 models (#2087)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [c392ce2](https://github.com/vllm-project/vllm-omni/commit/c392ce21e9cf9ea65c52b866447793db10e0261c)

- **作者**: WeiQing Chen
- **时间**: 2026-03-26T09:27:29Z
- **提交信息**: [Accuracy Benchmark] feat: add accuracy benchmark integrations for t2i and i2i (#1917)

Signed-off-by: David Chen <530634352@qq.com>
Signed-off-by: WeiQing Chen <40507679+david6666666@users.noreply.github.com>

### [ce916f4](https://github.com/vllm-project/vllm-omni/commit/ce916f4233a8cf8b0b6680ce447523925985e763)

- **作者**: Daniel Huang
- **时间**: 2026-03-26T08:52:01Z
- **提交信息**: [Enhancement] Patch AsyncOmniEngine try_get_output[_async] hanging issues (#2153)

Signed-off-by: Daniel Huang <daniel1.huang@intel.com>

### [029c853](https://github.com/vllm-project/vllm-omni/commit/029c85393a7e28137e806af1b59e0cc2acaf2667)

- **作者**: amy-why-3459
- **时间**: 2026-03-26T07:16:25Z
- **提交信息**: [BugFix]Fix keyError: num_processed_tokens_delta (#2213)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
