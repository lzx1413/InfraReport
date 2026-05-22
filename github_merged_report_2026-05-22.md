# GitHub Stars 合并报告 - 2026-05-22

**合并日期**: 2026-05-23
**监控日期**: 2026-05-22
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


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1942
- **最后更新**: 2026-05-22T22:08:46Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Ting, Bin Jia, yanghw116

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是昨日更新的要点分析：

### 1. 主要更新类型

*   **功能新增 (Feat):** 提交 `d13637a` 和 `52400a3` 引入了新的功能特性。
*   **重构 (Refactor):** 提交 `ab406b0` 是对现有代码结构的优化和调整。

### 2. 关键变更点及其与项目整体方向的关系

*   **提交 `d13637a` (Qwen2-ViT 多模态元数据预计算):**
    *   **变更点:** 将 Qwen2 系列的视觉Transformer (ViT) 模型接入到多模态元数据预计算钩子 (hook) 中。
    *   **与项目方向的关系:** 项目目标是“Scaling Any Modality Model Training”（扩展任意模态模型训练）。此提交直接扩展了项目支持的视觉模型家族（Qwen2-ViT），并优化了多模态数据预处理流程，是提升多模态训练效率的关键一步。

*   **提交 `52400a3` (Qwen-Image LoRA 配置):**
    *   **变更点:** 为 Qwen-Image 模型添加了 LoRA (Low-Rank Adaptation) 微调配置。
    *   **与项目方向的关系:** LoRA 是一种高效的模型微调技术，尤其适用于大模型。此提交丰富了项目的“Recipe Zoo”（配方库），为用户提供了更灵活、更经济的视觉模型微调方案，符合项目提供多样化训练策略的目标。

*   **提交 `ab406b0` (Qwen3/MoE NPU 支持与 OpSlot 守卫):**
    *   **变更点:** 为 Qwen3、Qwen3-VL、Qwen3-MoE 以及 Qwen3.5-MoE 模型添加了 NPU (神经网络处理器) 支持，并引入了 OpSlot 守卫机制。
    *   **与项目方向的关系:** 支持 NPU 意味着项目可以适配更广泛的硬件生态，降低对特定GPU的依赖，是实现“Scaling”的重要基础。OpSlot 守卫是一种代码健壮性措施，确保在特定算子（Op）不可用时系统能优雅降级，这对于一个支持多种模型和硬件的分布式训练框架至关重要。

### 3. 对项目的影响和潜在意义

*   **提升多模态能力:** 通过支持 Qwen2-ViT 和 Qwen-Image，项目在多模态（特别是视觉-语言）模型训练方面的能力得到显著增强。
*   **降低微调门槛:** LoRA 配置的加入使得用户无需完整训练整个模型即可进行高效微调，降低了计算成本和实验门槛，有助于吸引更多用户。
*   **增强硬件兼容性:** NPU 支持是项目走向更广泛硬件平台的关键一步，对于在国产芯片或特定AI加速器上部署和训练模型具有重要战略意义。
*   **提高系统稳定性:** OpSlot 守卫机制提升了框架的鲁棒性，使其在面对不同硬件或模型配置时能更稳定地运行。

### 4. 值得关注的技术点

*   **多模态元数据预计算钩子 (Multimodal Metadata Precompute Hook):** 这是一个设计模式，用于在训练前或训练中高效地处理和缓存多模态数据（如图像特征），避免重复计算，是提升训练吞吐量的关键技术。
*   **LoRA 配置:** 关注其具体实现方式（如目标模块、秩的大小等），这反映了项目对高效微调技术的支持深度。
*   **NPU 支持与 OpSlot 守卫:** 这是一个典型的“适配器”模式，通过抽象算子接口，使得同一套训练代码可以运行在不同的硬件后端上。OpSlot 守卫则是该模式下的容错机制。

### 5. 基于项目背景，这些提交如何影响项目发展

*   **强化“Recipe Zoo”核心价值:** 项目定位为“Model-Centric Distributed Recipe Zoo”。昨日提交新增了 Qwen2-ViT 和 Qwen-Image 的“配方”，并提供了 LoRA 这种更经济的“烹饪方式”，直接丰富了核心资产，使项目对用户更具吸引力。
*   **践行“Any Modality”承诺:** 通过持续集成不同视觉模型（Qwen2-ViT, Qwen-Image），项目在“Any Modality”（任意模态）的道路上稳步前进，从单一语言模型向多模态模型训练平台演进。
*   **夯实“Scaling”基础:** NPU 支持是“Scaling”在硬件维度上的体现，意味着项目可以扩展到更多样化的计算资源上。OpSlot 守卫则保证了这种扩展的稳定性，为大规模、多硬件的训练集群提供了可靠保障。
*   **提升项目成熟度:** 从单纯的功能新增（Feat）到代码重构和健壮性提升（Refactor），表明项目正在从快速迭代期进入成熟稳定期，开始关注代码质量和系统可靠性。

## 详细提交记录

### [d13637a](https://github.com/ByteDance-Seed/VeOmni/commit/d13637a1c8266c4a6b6a14a07923392e91ccbf9a)

- **作者**: Ting
- **时间**: 2026-05-22T22:08:41Z
- **提交信息**: [model, ci, agent] feat: wire qwen2-family ViT to the multimodal metadata precompute hook (#779)

### [52400a3](https://github.com/ByteDance-Seed/VeOmni/commit/52400a3ef376421279580f48ca250f8b6b72b9cf)

- **作者**: Bin Jia
- **时间**: 2026-05-22T15:59:23Z
- **提交信息**: [model, omni] feat: add Qwen-Image lora config (#784)

### [ab406b0](https://github.com/ByteDance-Seed/VeOmni/commit/ab406b066d3b9f1b46cd187eb60864891f2a3e31)

- **作者**: yanghw116
- **时间**: 2026-05-22T10:57:53Z
- **提交信息**: [model, ops] refactor: add NPU support and OpSlot guard for Qwen3/VL/MoE, Qwen3.5/MoE (#710)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2287
- **最后更新**: 2026-05-22T23:12:49Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

好的，根据您提供的仓库README摘要和提交记录，以下是针对昨日更新的要点分析：

### 1. 主要更新类型
- **环境配置/基础设施更新**

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：更新了Dockerfile以支持CUDA 13.0 (`cuda130`)。
- **与项目方向的关系**：LightX2V是一个**轻量级视频生成推理框架**。支持最新的CUDA版本（如13.0）是确保框架能够利用最新NVIDIA GPU硬件（如未来发布的Blackwell架构）进行高效推理的关键。这直接服务于项目“轻量”和“高效”的核心目标，确保用户能在最先进的硬件上获得最佳性能。

### 3. 对项目的影响和潜在意义
- **影响**：允许用户在配备CUDA 13.0环境的系统上构建和运行LightX2V，扩大了框架的硬件兼容性。
- **潜在意义**：
    - **性能提升**：CUDA 13.0通常包含针对新架构的底层优化，可能带来推理速度的提升。
    - **前瞻性**：提前适配未来主流的GPU环境，避免用户因环境不兼容而无法使用，有助于吸引和留住使用最新硬件的开发者与研究人员。
    - **维护成本**：需要确保框架代码与新版CUDA工具链完全兼容，可能涉及对底层算子或编译选项的微调。

### 4. 值得关注的技术点
- **Dockerfile的维护**：Dockerfile是项目可复现性和易用性的关键。更新它表明项目团队重视用户部署体验，并积极跟进底层技术栈的演进。
- **CUDA版本兼容性策略**：此次更新可能意味着项目开始或继续支持多个CUDA版本（例如，同时保留对CUDA 12.x的支持）。这是一个值得关注的技术决策，关系到项目的兼容性范围。

### 5. 基于项目背景，这些提交如何影响项目发展
- **巩固“轻量”与“高效”定位**：通过支持最新的CUDA，LightX2V能够利用最新硬件特性实现更快的视频生成推理，这直接强化了其作为“轻量”且“高效”推理框架的定位。
- **降低用户使用门槛**：对于拥有最新GPU的用户，无需手动配置复杂的环境即可直接使用，提升了项目的易用性和吸引力。
- **为未来功能铺路**：新CUDA版本可能引入新的库或API（如更高效的注意力机制实现），这为未来集成更先进的视频生成模型或优化技术提供了基础。此次更新是项目保持技术先进性的必要步骤。

## 详细提交记录

### [181846b](https://github.com/ModelTC/LightX2V/commit/181846bae646d7bda1203ab7aefcbfcd0a8f63fa)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-05-22T07:03:30Z
- **提交信息**: update dockerfile for cuda130 (#1087)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2092
- **最后更新**: 2026-05-22T13:52:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5661
- **最后更新**: 2026-05-22T22:25:06Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: Albert Cheng, Alex Yang, Richard Cai

## AI分析总结

好的，作为专业的代码分析助手，以下是对仓库 `flashinfer-ai/flashinfer` 昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**:
    - 为 Blackwell GPU 集成了基于 `cute-dsl` 的高性能 GQA Decode 内核。
    - 新增了 `trtllm_mxint4_block_scale_routed_moe` 和 `checkpointing_ssu` 等 API。
    - 为 `fp4_quantize` 添加了 `torch.compile` 兼容的自定义算子。
    - 替换了 SM120 上的 W4A16 MoE 内核，采用了新的 packed-route 设计。
- **Bug 修复 (Bug Fix)**:
    - 修复了自动调优器 (autotuner) 中文件缓存键冲突的问题，该问题会导致加载错误的配置。
    - 修复了 `trtllm-gen` 中 `plan()` 函数的一个 bug，该 bug 会意外修改共享缓冲区。
- **性能优化 (Performance)**:
    - 新的 `cute-dsl` decode 内核在 Blackwell GPU 上相比 `trtllm-gen` 和 `fa2` 有显著的性能提升。
- **测试与稳定性 (Testing & Stability)**:
    - 重构了测试流程，将高内存消耗的测试串行执行，并添加了超时机制和健康报告，以解决 OOM 问题。
- **版本发布 (Release)**:
    - 版本号升级至 `0.6.12`，为发布做准备。

### 2. 关键变更点及其与项目整体方向的关系

- **集成 `cute-dsl` Blackwell GQA Decode 内核**: 这是本次更新的核心。项目 README 明确其目标是提供“用于推理的高性能 GPU 内核”。此提交直接服务于这一目标，通过利用 NVIDIA 最新的 `cute-dsl` 框架，为 Blackwell (SM100a) 架构提供了最先进的 GQA (Grouped-Query Attention) 解码性能。这确保了 FlashInfer 在最新的硬件上保持竞争力。
- **修复自动调优器缓存键冲突**: 自动调优是 FlashInfer 实现高性能的关键技术之一。此修复确保了在不同配置（如 `use_8x4_sf_layout`）下，调优结果能被正确缓存和加载，避免了因加载错误配置导致的运行时崩溃。这直接关系到项目的**稳定性和可靠性**。
- **重构测试流程以解决 OOM**: 随着项目功能增多，测试套件变得庞大，导致 OOM 问题。此提交通过优化测试执行顺序和添加监控，提升了 CI/CD 管道的**健壮性**，确保新功能的引入不会破坏现有功能。
- **版本升级至 0.6.12**: 这是项目进入发布周期的标志。提交中详细列出了自上一版本以来的所有 API 变更，包括新增函数、参数修改等，为下游用户（如 vLLM）提供了清晰的升级指南。

### 3. 对项目的影响和潜在意义

- **巩固 Blackwell 平台优势**: 新的 `cute-dsl` 内核将使 FlashInfer 成为 Blackwell GPU 上 LLM 推理的首选库之一。性能数据显示，在多种配置下，其吞吐量都超越了 `fa2` 和 `trtllm-gen`，这将对依赖高性能推理的框架（如 vLLM, SGLang）产生直接且积极的影响。
- **提升项目成熟度和可靠性**: 自动调优器 bug 的修复和测试流程的改进，表明项目正在从快速迭代阶段向更加成熟、稳定的阶段过渡。这对于吸引生产环境用户至关重要。
- **扩展模型支持**: 新增的 `trtllm_mxint4_block_scale_routed_moe` 和 `checkpointing_ssu` 等 API 表明 FlashInfer 正在持续扩展其对不同模型架构（如 MoE, Mamba-2）和量化格式（如 MXINT4）的支持，使其成为一个更通用的推理加速库。

### 4. 值得关注的技术点

- **`cute-dsl` 的应用**: `cute-dsl` 是 NVIDIA 推出的新一代 CUDA 模板库，旨在编写更高效、更可移植的 GPU 内核。FlashInfer 率先在 Blackwell 上将其用于 GQA Decode，这是一个重要的技术方向。
- **三种 Reduction 模式**: 新的 decode 内核支持 `kernel` (确定性 split-K + reduction kernel), `atomic` (集群归约 + L2 atomic adds), 和 `none` (无 flash-decoding) 三种模式。这为在不同场景下平衡性能和确定性提供了灵活性。
- **`torch.compile` 兼容性**: 为 `fp4_quantize` 添加 `torch.compile` 支持，意味着该操作可以无缝集成到 PyTorch 2.0 的图编译流程中，从而获得额外的性能提升，这对于追求极致性能的用户非常重要。
- **Packed-Route MoE 设计**: SM120 W4A16 MoE 内核的重构采用了 packed-route 设计，将路由后的 token 按专家分组，再进行 GEMM 计算。这种设计可以更好地利用 GPU 的计算能力，减少因专家负载不均带来的性能损失。

### 5. 基于项目背景，这些提交如何影响项目发展

- **强化“高性能”核心价值**: 集成 `cute-dsl` 内核是项目“High-Performance GPU Kernels for Inference”这一核心使命的直接体现。通过持续引入最前沿的 GPU

## 详细提交记录

### [bff85f3](https://github.com/flashinfer-ai/flashinfer/commit/bff85f3459707d5d2f1426d1ded4a320ab142078)

- **作者**: Richard Cai
- **时间**: 2026-05-22T21:36:34Z
- **提交信息**: feat: integrate cute-dsl Blackwell GQA decode into BatchDecodeWithPagedKVCacheWrapper (#3360)

<!-- .github/pull_request_template.md -->

## 📌 Description
- Adds a new `cute-dsl` backend to `BatchDecodeWithPagedKVCacheWrapper`
powered by the cute-dsl Blackwell (SM100a) GQA decode kernel, supporting
    - NHD + HND paged + non-paged KV layout
    - fp8/bf16 QKVO
    - headdim multiple of 64 (large headdims supported)
    - speculative-decode (q_len_per_req > 1 + causal mask)
    - runtime PDL
    - skip softmax with threshold scale factor matching trtllm behavior
- per-tensor scale factors (folded into softmax scale and output scale)
    - LSE return
- three reduction modes:`kernel` (deterministic split-K + reduction
kernel), `atomic` (cluster reduction + L2 atomic adds), and `none`
(kv_splits == 1, no flash-decoding).
- Wraps the kernel in two PyTorch-facing classes
(`BatchDecodeCuteDSLWrapper`, `BatchDecodePagedCuteDSLWrapper`) modeled
on the prefill cute-dsl pattern. Compile is memoized via
`@functools.cache`; symbolic dims (`cute.sym_int`) cover runtime
variation in batch_size, seq_len, and prediction.
- Bug fix in trtllm-gen `plan()`: `block_id = indptr[0]` was a 0-dim
view, and `block_id += ...` did an in-place add that mutated
`indptr[0]`. Switched to a Python int read from the host-side indptr to
avoid corrupting shared buffers.
- Replace references to deprecated `cute.nvgpu.tcgen05.OperandMajorMode`
with `cute.nvgpu.OperandMajorMode` introduced in cute-dsl 4.5.0
- `BatchDecodeWithPagedKVCacheWrapper` API change: `q_len_per_req` is
now accepted in `plan` instead of `run`, to provide a tile size hint to
the `cute-dsl` compilation. Passing to `run` emits deprecation notice
and is used to validate the expected shape of `q`. Otherwise
`q_len_per_req` is inferred from the shape of `q` at runtime.

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
- [x] `pytest tests/attention/test_cute_dsl_decode.py` on Blackwell —
covers
both reduction modes, paged + ragged wrappers, LSE, speculative decode,
      v_scale, HND vs NHD layout, and runtime-q_len mismatch.
- [x] `python benchmarks/bench_cute_dsl_decode.py` — sanity-check
throughput
      against fa2 / trtllm-gen.

## Perf results B200
```
b= 1 mtp=0 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:   12.243 us      0.3 TB/s
   trtllm-gen:    6.301 us      0.7 TB/s
     cute-dsl:    4.862 us      0.9 TB/s
b= 1 mtp=0 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:   18.184 us      0.9 TB/s
   trtllm-gen:    8.128 us      2.1 TB/s
     cute-dsl:   11.002 us      1.5 TB/s
b= 1 mtp=0 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:   44.368 us      1.5 TB/s
   trtllm-gen:   17.782 us      3.8 TB/s
     cute-dsl:   18.137 us      3.7 TB/s
b= 8 mtp=0 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:   28.691 us      1.2 TB/s
   trtllm-gen:   10.577 us      3.2 TB/s
     cute-dsl:    8.952 us      3.8 TB/s
b= 8 mtp=0 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:   85.133 us      1.6 TB/s
   trtllm-gen:   24.139 us      5.6 TB/s
     cute-dsl:   22.920 us      5.9 TB/s
b= 8 mtp=0 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:  300.016 us      1.8 TB/s
   trtllm-gen:   78.230 us      6.9 TB/s
     cute-dsl:   77.682 us      6.9 TB/s
b=64 mtp=0 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:  159.955 us      1.7 TB/s
   trtllm-gen:   43.420 us      6.2 TB/s
     cute-dsl:   45.634 us      5.9 TB/s
b=64 mtp=0 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2:  589.830 us      1.8 TB/s
   trtllm-gen:  156.094 us      6.9 TB/s
     cute-dsl:  152.400 us      7.1 TB/s
b=64 mtp=0 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
          fa2: 2314.402 us      1.9 TB/s
   trtllm-gen:  606.548 us      7.1 TB/s
     cute-dsl:  598.255 us      7.2 TB/s
b= 1 mtp=3 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:    6.703 us      0.6 TB/s
     cute-dsl:    6.693 us      0.6 TB/s
b= 1 mtp=3 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   10.593 us      1.6 TB/s
     cute-dsl:   11.871 us      1.4 TB/s
b= 1 mtp=3 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   19.029 us      3.5 TB/s
     cute-dsl:   21.917 us      3.1 TB/s
b= 8 mtp=3 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   11.857 us      2.9 TB/s
     cute-dsl:   11.616 us      3.0 TB/s
b= 8 mtp=3 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   25.721 us      5.3 TB/s
     cute-dsl:   29.520 us      4.6 TB/s
b= 8 mtp=3 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   80.154 us      6.7 TB/s
     cute-dsl:   90.475 us      5.9 TB/s
b=64 mtp=3 s= 1024 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:   49.531 us      5.6 TB/s
     cute-dsl:   63.087 us      4.4 TB/s
b=64 mtp=3 s= 4096 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:  162.000 us      6.7 TB/s
     cute-dsl:  180.057 us      6.0 TB/s
b=64 mtp=3 s=16384 pg=16 h_q=64 h_kv=8 d=128 dtype=torch.bfloat16
   trtllm-gen:  621.074 us      6.9 TB/s
     cute-dsl:  690.734 us      6.2 TB/s
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a "cute-dsl" decode backend for Blackwell GPUs with
high-performance grouped-query attention decoding, plus two user-facing
wrappers for ragged and paged KV-cache decoding; supports LSE output,
kernel/atomic/none reductions, speculative multi-token decode,
softmax-skip tuning, workspace reuse, and optional user-provided
outputs.

* **Benchmarks**
* Added a CUDA-gated paged-batch GQA decode benchmark exercising
multiple backends, dtypes, batch/seq sizes and reporting
latency/bandwidth.

* **Tests**
* Added comprehensive integration and correctness tests covering decode
paths, LSE, reduction modes, softmax-skip behavior, and workspace
handling.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3360?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Mingyang Wang <35635157+saltyminty@users.noreply.github.com>

### [2f372e2](https://github.com/flashinfer-ai/flashinfer/commit/2f372e2e5f7c1c894c6aed11e4f02fc6dd69ee56)

- **作者**: Albert Cheng
- **时间**: 2026-05-22T20:22:46Z
- **提交信息**: fix(autotuner): differentiate file cache entries by runner specific kernel parameters (#3367)

## 📌 Description

The persistent autotune file cache key was constructed as a 3-tuple
`(custom_op, runner_class, profile)`, intentionally dropping
`hash(runner)` for cross-process stability, but **unintentionally also
dropping `extras`**, which carries runnerspecific parameters like
`use_8x4_sf_layout`, which caused `TrtllmGemmRunner` instances with
`use_8x4_sf_layout=True` and `use_8x4_sf_layout=False` to collide in the
file cache. When vLLM or other frameworks persists and reloads autotune
results, the wrong tactic gets applied, producing:
```
RuntimeError: Check failed: (config.mOptions.mSfLayoutB == mOptions.sfLayoutB)
             is false: Invalid sf layout in run
```

**Updates:**

1. **`flashinfer/autotuner.py`**, extend file key from 3-tuple to
4-tuple in `search_cache`, `save_configs`, `load_from_file`.
2. **`flashinfer/gemm/gemm_base.py`**, implement
`get_cache_key_extras()` to return `(self._use_8x4_sf_layout,)`.
3. **`tests/autotuner/test_autotuner_configs.py`**, add
`TestFileCacheKeyCollision` with two tests reproducing and update
existing tests for the new 4-tuple key format.

## 🔍 Related Issues

- Fixes flashinfer-ai/flashinfer#3363
- Related to vllm-project/vllm#42537

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
  - `test_autotuner_configs.py` — **37 passed**
  - `test_autotuner_core.py` — **78 passed**

## Reviewer Notes

The bug is latent until autotune results are persisted to disk and
reloaded. It was exposed by vllm-project/vllm#42537 which added
persistent caching for FlashInfer autotuning in vLLM.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Fixed cache key mismatch between memory and disk so runner-specific
parameters (extras/layout) are preserved when saving/loading autotuner
results.
* Resolved collisions where configurations that differed only by
layout-related parameters were treated as the same.

* **Tests**
* Added and updated tests to verify distinct file-cache entries and
loading for entries differing by extras/layout.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3367?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Albert Cheng (Engrg-Hardware 1) <albecheng@login-lyris01.lyris.clusters.nvidia.com>

### [dac8358](https://github.com/flashinfer-ai/flashinfer/commit/dac83584c47dd0281fe70466ac87c2073d8e1e17)

- **作者**: Jonathan Dierksen
- **时间**: 2026-05-22T17:06:06Z
- **提交信息**: Run high-likelihood OOM culprits separately, record memory usage and test duration for analysis (#2961)

<!-- .github/pull_request_template.md -->

## 📌 Description

A lot of tests have been reported previously as passing and more
recently as "no-report" due to getting killed by OOM before completing.
This rearranges things so that high-memory-use tests are run serially
after the rest of the tests have completed in parallel.

While this did stop the OOMs from happening, it did reveal that a couple
of other tests were taking 2+ hours, so I had to enforce a 2 hour
timeout to ensure that the tests could complete within a 4-hour timeout.

There is also now a health report at the end of each test run log that
displays the top 10 longest-running, highest-peak-memory, and
highest-peak-VRAM among all the tests run.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Tests that terminate before writing results are now detected, counted,
and recorded as failures.
* Kill reasons (including signal names like SIGKILL and SIGTERM) are
shown in failure messages for clearer diagnostics.
* Final exit status now reflects terminated test failures so CI/results
accurately indicate overall test health.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [42e2200](https://github.com/flashinfer-ai/flashinfer/commit/42e2200a55412007017f2cd7773f20ff81ea7d72)

- **作者**: Alex Yang
- **时间**: 2026-05-22T16:55:00Z
- **提交信息**: bump version to 0.6.12 (#3388)

## Description

Bump version to 0.6.12 for release.

## Related Issues (Gated-by PRs)


https://github.com/flashinfer-ai/flashinfer/issues?q=is%3Aopen+label%3Av0.6.12

## Reviewer Notes

**API changes review**

API changes since v0.6.11.post3, using new tool
* #3341

```diff
diff -u \
  <(scripts/list_apis.sh -d -p --ref v0.6.11.post3) \
  <(scripts/list_apis.sh -d -p)

--- /tmp/api_baseline.txt	2026-05-21 16:07:23.252004287 -0700
+++ /tmp/api_head.txt	2026-05-21 16:07:23.316004287 -0700
@@ -251,6 +251,8 @@
     shared_expert_output: Optional[torch.Tensor] = None,
     # ===== Group quant parameters =====
     block_quant_group_size: Optional[int] = None,
+    # ===== RMSNorm variant =====
+    weight_bias: float = 0.0,
 ) -> torch.Tensor:
 [Global Functions]
 @flashinfer_api
@@ -513,6 +515,7 @@
     out_dtype: Optional[torch.dtype] = None,
     is_var_seq: bool = True,
     enable_pdl: Optional[bool] = None,
+    sinks: Optional[torch.Tensor] = None,
 ) -> torch.Tensor:
 class BatchPrefillCuteDSLWrapper:
     @flashinfer_api
@@ -759,7 +762,11 @@
     skip_softmax_threshold_scale_factor: Optional[float] = None,
     kv_cache_sf: Optional[Tuple[torch.Tensor, torch.Tensor]] = None,
     uses_shared_paged_kv_idx: bool = True,
-) -> Union[torch.Tensor, FP4Tensor]:
+    lse: Optional[torch.Tensor] = None,
+    return_lse: bool = False,
+) -> Union[
+    torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor], torch.Tensor]
+]:
 @flashinfer_api(trace=xqa_batch_decode_trace)
 def xqa_batch_decode_with_kv_cache(
     query: torch.Tensor,
@@ -898,6 +905,7 @@
     weight_layout: int = WeightLayout.BlockMajorK,
     do_finalize: bool = True,
     enable_pdl: bool = True,
+    gemm1_lora_delta: Optional[torch.Tensor] = None,
     tune_max_num_tokens: int = 8192,
     activation_type: int = ActivationType.Swiglu.value,
     routing_replay_out: Optional[torch.Tensor] = None,
@@ -987,6 +995,7 @@
     weight_layout: int = 0,
     do_finalize: bool = True,
     enable_pdl: Optional[bool] = None,
+    gemm1_lora_delta: Optional[torch.Tensor] = None,
     output: Optional[torch.Tensor] = None,
     tune_max_num_tokens: int = 8192,
     fp8_quantization_type: Fp8QuantizationType = Fp8QuantizationType.DeepSeekFp8,
@@ -1034,7 +1043,7 @@
 
 @flashinfer_api(trace=trtllm_fp4_block_scale_routed_moe_trace)
 def trtllm_fp4_block_scale_routed_moe(
-    topk_ids: torch.Tensor,
+    topk_ids: Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]],
     routing_bias: Optional[torch.Tensor],
     hidden_states: torch.Tensor,
     hidden_states_scale: Optional[torch.Tensor],
@@ -1096,6 +1105,34 @@
     norm_topk_prob: bool = True,
     routing_replay_out: Optional[torch.Tensor] = None,
 ) -> List[torch.Tensor]:
+
+
+@flashinfer_api
+def trtllm_mxint4_block_scale_routed_moe(
+    topk_ids: torch.Tensor,
+    hidden_states: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm1_alpha: Optional[torch.Tensor],
+    gemm1_beta: Optional[torch.Tensor],
+    gemm1_clamp_limit: Optional[torch.Tensor],
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    num_experts: int,
+    top_k: int,
+    n_group: Optional[int],
+    topk_group: Optional[int],
+    intermediate_size: int,
+    local_expert_offset: int,
+    local_num_experts: int,
+    routed_scaling_factor: Optional[float],
+    routing_method_type: int = 0,
+    do_finalize: bool = True,
+    enable_pdl: Optional[bool] = None,
+    gemm1_lora_delta: Optional[torch.Tensor] = None,
+    output: Optional[torch.Tensor] = None,
+    tune_max_num_tokens: int = 8192,
+) -> List[torch.Tensor]:
 [Global Functions]
 @flashinfer_api(trace=b12x_fused_moe_trace)
 def b12x_fused_moe(
@@ -1117,8 +1154,6 @@
     output_dtype: torch.dtype = torch.bfloat16,
     activation: str = "silu",
     activation_precision: str = "fp4",
-    quant_mode: Optional[str] = None,
-    source_format: str = "modelopt",
 ) -> torch.Tensor:
 class B12xMoEWrapper:
     @flashinfer_api
@@ -1136,8 +1171,6 @@
         device: str = "cuda",
         activation: str = "silu",
         activation_precision: str = "fp4",
-        quant_mode: Optional[str] = None,
-        source_format: str = "modelopt",
     ):
 
     @flashinfer_api(trace=b12x_moe_wrapper_run_trace)
@@ -1477,8 +1510,6 @@
     out: Optional[torch.Tensor] = None,
     backend: Literal["cudnn", "cublas", "cutlass", "auto"] = "cublas",
 ):
-
-
 @flashinfer_api(trace=bmm_fp8_trace)
 def bmm_fp8(
     A: torch.Tensor,
@@ -1524,7 +1555,7 @@
     out_dtype: Optional[torch.dtype] = None,
     backend: Literal["cutlass", "trtllm"] = "cutlass",
 ):
-@flashinfer_api
+@flashinfer_api(trace=gemm_fp8_nt_groupwise_trace)
 def gemm_fp8_nt_groupwise(
     a: torch.Tensor,
     b: torch.Tensor,
@@ -1712,8 +1743,17 @@
     sf_dtype: str,
     c_dtype: str,
     sf_vec_size: int,
+    topk_weights: Optional[torch.Tensor] = None,
+    idx_src_info: Optional[torch.Tensor] = None,
+    rank_src_info: Optional[torch.Tensor] = None,
+    out_ptrs: Optional[torch.Tensor] = None,
+    num_ranks: int = 0,
     dst_signals: Optional[torch.Tensor] = None,
     sm_count: Optional[int] = None,
+    barrier_flag_local: Optional[torch.Tensor] = None,
+    barrier_flag_multicast: Optional[torch.Tensor] = None,
+    is_combine_fusion: bool = False,
+    is_swap_ab: bool = False,
     **kwargs,
 ):
 [Global Functions]
@@ -1722,14 +1762,21 @@
     mat_a: torch.Tensor,
     mat_b: torch.Tensor,
     out: torch.Tensor,
-    launch_with_pdl: bool = False,
+    launch_with_pdl: bool = True,
 ) -> None:
 @flashinfer_api(trace=mm_M1_16_K7168_N256_trace)
 def mm_M1_16_K7168_N256(
     mat_a: torch.Tensor,
     mat_b: torch.Tensor,
     out: torch.Tensor,
-    launch_with_pdl: bool = False,
+    launch_with_pdl: bool = True,
+) -> None:
+@flashinfer_api(trace=mm_M1_16_K6144_N256_trace)
+def mm_M1_16_K6144_N256(
+    mat_a: torch.Tensor,
+    mat_b: torch.Tensor,
+    out: torch.Tensor,
+    launch_with_pdl: bool = True,
 ) -> None:
 @flashinfer_api(trace=tinygemm_bf16_trace)
 def tinygemm_bf16(
@@ -1826,6 +1873,36 @@
     tactic: int = -1,
 ) -> torch.Tensor:
 [Global Functions]
+@flashinfer_api
+def checkpointing_ssu(
+    state: torch.Tensor,
+    old_x: torch.Tensor,
+    old_B: torch.Tensor,
+    old_dt: torch.Tensor,
+    old_cumAdt: torch.Tensor,
+    cache_buf_idx: torch.Tensor,
+    prev_num_accepted_tokens: torch.Tensor,
+    x: torch.Tensor,
+    dt: torch.Tensor,
+    A: torch.Tensor,
+    B: torch.Tensor,
+    C: torch.Tensor,
+    out: torch.Tensor,
+    D: Optional[torch.Tensor] = None,
+    z: Optional[torch.Tensor] = None,
+    dt_bias: Optional[torch.Tensor] = None,
+    dt_softplus: bool = False,
+    state_batch_indices: Optional[torch.Tensor] = None,
+    pad_slot_id: int = -1,
+    state_scale: Optional[torch.Tensor] = None,
+    rand_seed: Optional[torch.Tensor] = None,
+    philox_rounds: int = 10,
+    d_split: Optional[int] = None,
+    cu_seqlens: Optional[torch.Tensor] = None,
+    max_seqlen: Optional[int] = None,
+    enable_pdl: bool = False,
+) -> torch.Tensor:
+[Global Functions]
 @flashinfer_api(trace=selective_state_update_trace)
 def selective_state_update(
     state: torch.Tensor,
@@ -1966,6 +2043,7 @@
         kv_len: Optional[torch.Tensor] = None,
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
 
 
@@ -1991,7 +2069,10 @@
     backend: str = "auto",
     is_var_seq: bool = True,
     uses_shared_paged_kv_idx: bool = True,
-) -> torch.Tensor:
+    lse: Optional[torch.Tensor] = None,
+    return_lse: bool = False,
+    cute_dsl_impl: str = "auto",
+) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
 
 
 @flashinfer_api(trace=xqa_batch_decode_mla_trace)
@@ -2252,6 +2333,44 @@
     norm_out: Optional[torch.Tensor] = None,
     sf_out: Optional[torch.Tensor] = None,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
+    qkv,
+    q_weight,
+    k_weight,
+    **kwargs,
+):
+
+
+@flashinfer_api
+def fused_qk_rmsnorm_rope(
+    qkv: torch.Tensor,
+    q_weight: torch.Tensor,
+    k_weight: torch.Tensor,
+    *,
+    ppf: int,
+    pph: int,
+    ppw: int,
+    num_frame_channels: int,
+    num_height_channels: int,
+    num_width_channels: int,
+    num_heads_q: int,
+    num_heads_k: int,
+    num_heads_v: int,
+    head_dim: int,
+    eps: float = 1e-6,
+    base: float = 10000.0,
+    interleave: bool = True,
+    factor: float = 1.0,
+    low: float = 0.0,
+    high: float = 0.0,
+    attention_factor: float = 1.0,
+    is_qk_norm: bool = True,
+    output_fp8: bool = False,
+    output_quant_scale: float = 1.0,
+    v_quant_scale: float = 1.0,
+    q_out: Optional[torch.Tensor] = None,
+    k_out: Optional[torch.Tensor] = None,
+    v_out: Optional[torch.Tensor] = None,
+) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
 [Global Functions]
 @flashinfer_api
 def get_batch_indices_positions(
@@ -2730,7 +2849,11 @@
     skip_softmax_threshold_scale_factor: Optional[float] = None,
     uses_shared_paged_kv_idx: bool = True,
     causal: bool = True,
-) -> Union[torch.Tensor, FP4Tensor]:
+    lse: Optional[torch.Tensor] = None,
+    return_lse: bool = False,
+) -> Union[
+    torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor], torch.Tensor]
+]:
 
 
 @flashinfer_api(trace=fmha_v2_prefill_deepseek_trace)
@@ -2942,6 +3065,7 @@
     is_sf_swizzled_layout: bool = True,
     alignment: int = 32,
     enable_pdl: bool | None = None,
+    is_sf_8x4_layout: bool = False,
 ) -> Tuple[torch.Tensor, torch.Tensor]:
```

API changes since v0.6.11.post3 (old approach)

```diff
$ git diff v0.6.11.post3..main -- "*.py" | grep -B5 -A20 "@flashinfer_api"
-def _reconstruct_value(value: Any) -> Any:
+def flush_graph_dumps(synchronize: bool = True) -> int:
+    """Write CUDA-graph-deferred level-10 dumps to disk.
+
+    When ``FLASHINFER_LOGLEVEL=10`` is active inside ``torch.cuda.graph(...)``,
+    each ``@flashinfer_api`` call records input/output tensor references instead
+    of writing immediately or inserting D2H copies into the captured graph.
+    After ``g.replay()`` completes, calling this function materializes current
+    tensor values to CPU and serializes them to two places:
+
+    1. ``inputs.pt``/``outputs.pt`` (or the safetensors equivalents) in the
+       original dump directory, for backwards compatibility. These files
+       always reflect the most recent flush.
+    2. ``graph_flushes/flush_XXXX/`` under the original dump directory. These
+       immutable snapshots preserve every explicit flush, so callers can keep
+       every replay by calling ``flush_graph_dumps()`` after every replay.
+
+    Parameters
+    ----------
+    synchronize : bool, default True
+        Synchronize the current stream first to ensure the most recent
+        ``g.replay()`` has completed before materializing tensors. Set to
+        ``False`` only if you've already synchronized externally.
+
+    Returns
+    -------
--
         routing_logits,
         None,
         None,
@@ -3199,7 +3362,7 @@ def trtllm_fp4_block_scale_moe(
 
 @flashinfer_api(trace=trtllm_fp4_block_scale_routed_moe_trace)
 def trtllm_fp4_block_scale_routed_moe(
-    topk_ids: torch.Tensor,
+    topk_ids: Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]],
     routing_bias: Optional[torch.Tensor],
     hidden_states: torch.Tensor,
     hidden_states_scale: Optional[torch.Tensor],
@@ -3231,13 +3394,20 @@ def trtllm_fp4_block_scale_routed_moe(
     output: Optional[torch.Tensor] = None,
     tune_max_num_tokens: int = 8192,
 ) -> List[torch.Tensor]:
-    """FP4 block scale MoE operation.
+    """FP4 block scale MoE operation with pre-computed routing.
+
+    This function supports two pre-computed routing formats:
+    1. Packed format: topk_ids is a single tensor with packed (score << 16 | expert_id)
+    2. Unpacked format: topk_ids is a tuple of (topk_ids, topk_weights) tensors
 
     Args:
-        topk_ids (torch.Tensor): shape [seq_len, top_k]
-            Tensor of top-k indices and expert weights. Dtype must be int32.
--
         norm_topk_prob,
         routing_replay_out,
     )
+
+
+@flashinfer_api
+def trtllm_mxint4_block_scale_routed_moe(
+    topk_ids: torch.Tensor,
+    hidden_states: torch.Tensor,
+    gemm1_weights: torch.Tensor,
+    gemm1_weights_scale: torch.Tensor,
+    gemm1_alpha: Optional[torch.Tensor],
+    gemm1_beta: Optional[torch.Tensor],
+    gemm1_clamp_limit: Optional[torch.Tensor],
+    gemm2_weights: torch.Tensor,
+    gemm2_weights_scale: torch.Tensor,
+    num_experts: int,
+    top_k: int,
+    n_group: Optional[int],
+    topk_group: Optional[int],
+    intermediate_size: int,
+    local_expert_offset: int,
+    local_num_experts: int,
+    routed_scaling_factor: Optional[float],
+    routing_method_type: int = 0,
+    do_finalize: bool = True,
--
-    except Exception:
-        return False
-
-
 @supported_compute_capability([120, 121])
 @flashinfer_api(trace=b12x_fused_moe_trace)
 def b12x_fused_moe(
@@ -74,13 +67,11 @@ def b12x_fused_moe(
     output_dtype: torch.dtype = torch.bfloat16,
     activation: str = "silu",
     activation_precision: str = "fp4",
-    quant_mode: Optional[str] = None,
-    source_format: str = "modelopt",
 ) -> torch.Tensor:
     """Run fused MoE on SM120/SM121 using b12x CuTe DSL kernels.
 
-    The kernel takes bf16 input and runs routing, FC1, activation, FC2,
-    and scatter through the selected backend.
+    The kernel takes bf16 input and fuses quantization + routing +
+    FC1 + activation + FC2 + scatter in a single launch.
     Automatically selects micro (decode), static, or dynamic backend
     based on routed row count.
 
@@ -99,19 +90,16 @@ def b12x_fused_moe(
         w1_alpha: Per-expert global scale for FC1.
         w2_alpha: Per-expert global scale for FC2.
--
 
@@ -6387,7 +6276,7 @@ def _check_gemm_fp8_nt_groupwise_problem_size(
     },
     common_check=_check_gemm_fp8_nt_groupwise_problem_size,
 )
-@flashinfer_api
+@flashinfer_api(trace=gemm_fp8_nt_groupwise_trace)
 def gemm_fp8_nt_groupwise(
     a: torch.Tensor,
     b: torch.Tensor,
@@ -8031,7 +7920,7 @@ def _calculate_block_scale_dims(
 
 
 @functools.lru_cache(maxsize=1024)
-def create_cudnn_execution_plans_mxfp8_gemm(
+def build_cudnn_gemm_mxfp8_graph(
     a_shape,
     a_stride,
     a_type,  # cudnn.data_type, FP8_E4M3 or FP8_E5M2
@@ -8041,7 +7930,11 @@ def create_cudnn_execution_plans_mxfp8_gemm(
     block_size,
     o_type,  # cudnn.data_type, BF16 or FP16
     device,
+    policy=None,
 ):
+    if policy is None:
+        policy = cudnn.build_plan_policy.HEURISTICS_CHOICE
--
@@ -229,6 +264,54 @@ def mm_M1_16_K7168_N256(
     )
 
 
+@backend_requirement({}, common_check=_mm_M1_16_K6144_N256_shape_checks)
+@flashinfer_api(trace=mm_M1_16_K6144_N256_trace)
+def mm_M1_16_K6144_N256(
+    mat_a: torch.Tensor,
+    mat_b: torch.Tensor,
+    out: torch.Tensor,
+    launch_with_pdl: bool = True,
+) -> None:
+    """Optimized GEMM for the router operation in GLM-MoE-DSA.
+
+    This function performs a highly optimized matrix multiplication specifically tailored
+    for the expert routing GEMM in GLM-MoE-DSA's Mixture of Experts (MoE) architecture.
+    It computes out = mat_a @ mat_b where mat_a contains token embeddings and mat_b
+    contains expert routing weights.
+
+    The implementation is optimized for the specific problem dimensions used in GLM-MoE-DSA:
+    - Hidden dimension (K): 6144
+    - Number of experts (N): 256
+    - Number of tokens (M): 1-16
+
+    Args:
+        mat_a (torch.Tensor): Input token embeddings of shape (M, K) where M is the number
--
+) -> None:
+    """Fake implementation for torch.compile() meta tensor propagation."""
+    pass
+
+
+@flashinfer_api
+def checkpointing_ssu(
+    state: torch.Tensor,
+    old_x: torch.Tensor,
+    old_B: torch.Tensor,
+    old_dt: torch.Tensor,
+    old_cumAdt: torch.Tensor,
+    cache_buf_idx: torch.Tensor,
+    prev_num_accepted_tokens: torch.Tensor,
+    x: torch.Tensor,
+    dt: torch.Tensor,
+    A: torch.Tensor,
+    B: torch.Tensor,
+    C: torch.Tensor,
+    out: torch.Tensor,
+    D: Optional[torch.Tensor] = None,
+    z: Optional[torch.Tensor] = None,
+    dt_bias: Optional[torch.Tensor] = None,
+    dt_softplus: bool = False,
+    state_batch_indices: Optional[torch.Tensor] = None,
+    pad_slot_id: int = -1,
--
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> Tuple[torch.Tensor, torch.Tensor]: ...
 
     @flashinfer_api(trace=mla_paged_decode_trace)
@@ -489,6 +915,7 @@ class BatchMLAPagedAttentionWrapper:
         kv_len: Optional[torch.Tensor] = None,
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
         r"""Run the MLA attention computation.
 
@@ -506,6 +933,7 @@ class BatchMLAPagedAttentionWrapper:
             ``head_dim_kpe`` is 64 in DeepSeek v2/v3 models.
         out : Optional[torch.Tensor]
             The output tensor, if not provided, will be allocated internally.
+            When ``o_scale`` is provided, this should be an FP8 tensor.
         lse : Optional[torch.Tensor]
             The log-sum-exp of attention logits, if not provided, will be allocated internally.
         return_lse : bool, optional
@@ -516,6 +944,10 @@ class BatchMLAPagedAttentionWrapper:
             The query length of each request, shape: ``[batch_size]``. Required when ``backend`` is ``cutlass``.
         page_table : Optional[torch.Tensor]
             The page table of the paged kv-cache, shape: ``[batch_size, num_pages]``. Required when ``backend`` is ``cutlass``.
--
+            )
+
+    return True
+
+
+@flashinfer_api
+@backend_requirement(backend_checks={}, common_check=_check_fused_qk_rmsnorm_rope)
+def fused_qk_rmsnorm_rope(
+    qkv: torch.Tensor,
+    q_weight: torch.Tensor,
+    k_weight: torch.Tensor,
+    *,
+    ppf: int,
+    pph: int,
+    ppw: int,
+    num_frame_channels: int,
+    num_height_channels: int,
+    num_width_channels: int,
+    num_heads_q: int,
+    num_heads_k: int,
+    num_heads_v: int,
+    head_dim: int,
+    eps: float = 1e-6,
+    base: float = 10000.0,
+    interleave: bool = True,
+    factor: float = 1.0,```

**Supplemental: class-wrapper overload stub changes (BatchMLAPagedAttentionWrapper.run gained `o_scale`)**

```diff
$ git diff v0.6.11.post3..main -- "flashinfer/mla/_core.py" | grep -B5
-A10 "o_scale"
     mod = gen_trtllm_gen_fmha_module()
@@ -457,6 +881,7 @@ class BatchMLAPagedAttentionWrapper:
         kv_len: Optional[torch.Tensor] = None,
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> torch.Tensor: ...
 
     @overload
@@ -473,6 +898,7 @@ class BatchMLAPagedAttentionWrapper:
         kv_len: Optional[torch.Tensor] = None,
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> Tuple[torch.Tensor, torch.Tensor]: ...
 
     @flashinfer_api(trace=mla_paged_decode_trace)
@@ -489,6 +915,7 @@ class BatchMLAPagedAttentionWrapper:
         kv_len: Optional[torch.Tensor] = None,
         page_table: Optional[torch.Tensor] = None,
         return_lse_base_on_e: bool = False,
+        o_scale: Optional[float] = None,
     ) -> Union[torch.Tensor, Tuple[torch.Tensor, torch.Tensor]]:
         r"""Run the MLA attention computation.
 
@@ -506,6 +933,7 @@ class BatchMLAPagedAttentionWrapper:
             ``head_dim_kpe`` is 64 in DeepSeek v2/v3 models.
         out : Optional[torch.Tensor]
The output tensor, if not provided, will be allocated internally.
+            When ``o_scale`` is provided, this should be an FP8 tensor.
         lse : Optional[torch.Tensor]
The log-sum-exp of attention logits, if not provided, will be allocated
internally.
         return_lse : bool, optional
@@ -516,6 +944,10 @@ class BatchMLAPagedAttentionWrapper:
The query length of each request, shape: ``[batch_size]``. Required when
``backend`` is ``cutlass``.
         page_table : Optional[torch.Tensor]
The page table of the paged kv-cache, shape: ``[batch_size,
num_pages]``. Required when ``backend`` is ``cutlass``.
+        o_scale : Optional[float]
+ FP8 output dequantization scale (``real = quantized * o_scale``).
+ When provided, ``out`` must be an FP8 tensor. Only supported with
+            the ``cutlass`` backend.
         """
         if self._backend == "cutlass":
             if return_lse:
@@ -525,7 +957,26 @@ class BatchMLAPagedAttentionWrapper:
"profiler_buffer does not support cutlass backend for now."
                 )
             self._cached_module = get_mla_module()
-            if out is None:
+            output_scale = 1.0
+            if o_scale is not None:
+                output_scale = float(o_scale)
+ if not math.isfinite(output_scale) or output_scale <= 0.0:
+                    raise ValueError(
+ f"o_scale must be a finite positive value, got {o_scale}"
+                    )
+                if out is None:
+                    raise ValueError(
+ "out tensor must be provided when o_scale is used for FP8 output."
+                    )
+                if out.dtype not in (
+                    torch.float8_e4m3fn,
+                    torch.float8_e5m2,
+                ):
+                    raise ValueError(
+ f"out must be an FP8 tensor when o_scale is provided, got {out.dtype}"
+                    )
+ check_shape_dtype_device(out, q_nope.shape, None, q_nope.device,
"out")
+            elif out is None:
                 out = torch.empty_like(q_nope)
             else:
                 check_shape_dtype_device(
@@ -543,9 +994,14 @@ class BatchMLAPagedAttentionWrapper:
                 ckv_kpe_cache,
                 kv_len,
                 page_table,
+                output_scale,
             )
             return out
 
+        if o_scale is not None:
+            raise ValueError(
+ "o_scale is only supported with the cutlass backend for now."
+            )
         if profiler_buffer is None:
             if self._use_profiler:
                 raise ValueError(
@@ -615,7 +1071,10 @@ def trtllm_batch_decode_with_kv_cache_mla(
     backend: str = "auto",
     is_var_seq: bool = True,
     uses_shared_paged_kv_idx: bool = True,
-) -> torch.Tensor:
+    lse: Optional[torch.Tensor] = None,
```

**Supplemental: `trtllm_batch_decode_with_kv_cache` / `trtllm_batch_context_with_kv_cache` gained `lse` and `return_lse` parameters (signature widening — BC)**

```diff
$ git diff v0.6.11.post3..main -- "flashinfer/decode.py"
"flashinfer/prefill.py" | grep -B3 -A6 "return_lse: bool = False"
     uses_shared_paged_kv_idx: bool = True,
-) -> Union[torch.Tensor, FP4Tensor]:
+    lse: Optional[torch.Tensor] = None,
+    return_lse: bool = False,
+) -> Union[
+ torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor],
torch.Tensor]
+]:
     """
     Parameters
     ----------
--
     causal: bool = True,
-) -> Union[torch.Tensor, FP4Tensor]:
+    lse: Optional[torch.Tensor] = None,
+    return_lse: bool = False,
+) -> Union[
+ torch.Tensor, FP4Tensor, Tuple[Union[torch.Tensor, FP4Tensor],
torch.Tensor]
+]:
     """
     Parameters
     ----------
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Chores**
  * Version bumped to 0.6.12.

<!-- review_stack_entry_start -->

[![Review Change Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3388?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [16a8e27](https://github.com/flashinfer-ai/flashinfer/commit/16a8e274c4b7b2c4501894e765c2e4a1d82c2fa5)

- **作者**: Luke Alonso
- **时间**: 2026-05-22T16:23:55Z
- **提交信息**: Replace SM120 W4A16 MoE kernels (#3336)

## 📌 Description

Replace the previous SM120 W4A16 MoE kernel split with a packed-route
design.
The new W4A16 path groups routed token rows by expert before GEMM work,
then drives the
fused FC1/FC2 kernel from packed route indices, block expert IDs, and a
route count.

This removes the old static, dynamic, and micro W4A16 kernel files and
adds W4A16-specific
prepared-weight, route-packing, FP4 helper, host utility, and
fused-kernel modules under the
moe_w4a16_ prefix. The FlashInfer b12x MoE dispatch, workspace
allocation, tracing, and tests
are updated to use the new W4A16 backend while preserving the existing
caller-facing interfaces.

  ## 🔍 Related Issues

  None.

  ## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

  ### ✅ Pre-commit Checks

- [X] I have installed pre-commit by running pip install pre-commit (or
used your preferred method).
  - [X I have installed the hooks with pre-commit install.
- [X] I have run the hooks manually with pre-commit run --all-files and
fixed any reported issues.

  ## 🧪 Tests

  - [x] Tests have been added or updated as needed.
  - [x] All tests are passing (unittest, etc.).
  
 ## Reviewer Notes
 
Please focus review on the W4A16 kernel replacement itself:

- the packed-route layout and route-block metadata consumed by the fused
kernel
  - the FC1/activation/FC2 dataflow over that packed routed layout
  - workspace sizing and reuse for graph-captured execution
- preservation of the existing FlashInfer b12x MoE API surface for W4A16
callers

The intended behavior for the full-expert path is that topk_ids are
valid dense expert IDs. Skipped/nonlocal routing goes through the mapped
route path.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added explicit quantization mode (quant_mode) and source_format
inputs, W4A16 route-packing execution path, and W4A16
weight-preparation/packing utilities.

* **Improvements**
* Unified quant_mode-aware workspace allocation and dispatch for
SM120/SM121 MoE kernels; wrapper and trace templates surface new inputs
and validation.

* **Bug Fixes / Stability**
* CUDA-graph capture now requires preallocated outputs and rejects
incompatible quant_mode/source_format combinations.

* **Tests**
* Expanded tests to cover quant_mode, W4A16 routing, workspace
contracts, and CUDA-graph guards.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3336)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [77477e2](https://github.com/flashinfer-ai/flashinfer/commit/77477e275c74a860c63931aca83fa5ad36d5d719)

- **作者**: Serge Panev
- **时间**: 2026-05-22T16:22:07Z
- **提交信息**: Add torch.compile-compatible custom op for fp4_quantize (#3081)

## Summary

- Registers `fp4_quantize` as a `torch.library.custom_op`
(`flashinfer::fp4_quantize`) so `torch.compile` / dynamo treats it as
opaque and never traces into the JIT/subprocess internals
- Adds a `register_fake` meta kernel with correct shape inference for
all scale-factor layout combinations (swizzled 128x4, swizzled 8x4, and
linear)
- Callers inside `torch.compile` regions use
`torch.ops.flashinfer.fp4_quantize(...)` instead of `fp4_quantize()`
directly

Closes #2999

## Test plan

- [ ] Verify `torch.ops.flashinfer.fp4_quantize(x, scale)` produces
identical outputs to `fp4_quantize(x, scale)` in eager mode
- [ ] Verify `torch.compile(fullgraph=True)` succeeds when calling
`torch.ops.flashinfer.fp4_quantize`
- [x] Test with `sf_vec_size ∈ {16, 32}`, `is_sf_swizzled_layout ∈
{True, False}`, `is_sf_8x4_layout ∈ {True, False}`
- [x] Tested on DGX Spark (SM121) with SGLang 0.5.10
`torch.compile(fullgraph=True)` — shapes and values match eager
execution

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Introduced FP4 quantization support as a new operator exposed to
PyTorch.
* Added a meta/fake implementation for shape inference and allocation so
packed FP4 outputs and their scale-factor tensors are created with
correct shapes and layout handling (row-/column-major and swizzled
layouts) for downstream workflows.

<!-- review_stack_entry_start -->

[![Review Change
Stack](https://storage.googleapis.com/coderabbit_public_assets/review-stack-in-coderabbit-ui.svg)](https://app.coderabbit.ai/change-stack/flashinfer-ai/flashinfer/pull/3081?utm_source=github_walkthrough&utm_medium=github&utm_campaign=change_stack)

<!-- review_stack_entry_end -->
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3507
- **最后更新**: 2026-05-22T23:19:05Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Junda Su, William Lin, Raghav K

## AI分析总结

好的，这是对 `hao-ai-lab/FastVideo` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **功能新增 (Feature)**: 新增了 Dreamverse 的 Modal UI 镜像构建，以及 Attn-QAT（注意力量化感知训练）的推理与训练后端。
- **依赖管理 (Dependency)**: 修复了 Dreamverse npm 依赖的安全漏洞。
- **文档更新 (Documentation)**: 新增了 `enable_torch_compile` 的使用文档及 A/B 示例。

### 2. 关键变更点及其与项目整体方向的关系

- **Dreamverse 集成 (提交 1 & 2)**: 项目正在积极构建其“Dreamverse”子项目或功能模块。通过添加 UI 镜像构建和修复依赖安全问题，表明该项目正从核心训练/推理框架向更完整的、用户友好的产品化方向演进。
- **Attn-QAT 功能 (提交 3)**: 这是“Attn-QAT”系列的第4/12个提交，表明项目正在进行一项重大的、分阶段的功能开发。该功能旨在实现注意力机制的量化感知训练，直接关系到模型的**推理效率**和**部署成本**，与项目“FastVideo”追求速度的核心目标高度一致。
- **文档完善 (提交 4)**: 为 `torch.compile` 功能提供文档和示例，降低了用户使用该优化功能的上手门槛，有助于提升项目整体的易用性和性能表现。

### 3. 对项目的影响和潜在意义

- **提升产品成熟度**: Dreamverse 相关的提交（UI、依赖修复）标志着项目从一个纯技术库向一个更完整的、可部署的解决方案迈进，这对于吸引非核心开发者用户至关重要。
- **增强核心竞争力**: Attn-QAT 功能的持续开发，是项目在视频生成领域保持技术领先地位的关键。量化技术能显著降低显存占用和推理延迟，这对于长视频、高分辨率视频生成尤为重要，直接回应了项目的“Fast”承诺。
- **降低用户使用门槛**: `torch.compile` 的文档化，让用户能更轻松地利用 PyTorch 的 JIT 编译优化来加速模型，这是一种“开箱即用”的性能提升，对用户体验是正向的。

### 4. 值得关注的技术点

- **Attn-QAT 架构**: 该提交是系列中的第4个，值得关注其具体实现方式（例如，是仅量化权重，还是同时量化激活值？使用了哪种量化方案？）。这代表了视频生成模型在注意力机制上进行高效推理的前沿探索。
- **`torch.compile` 的 A/B 示例**: 文档中提供了 A/B 示例，这暗示了 `torch.compile` 可能并非对所有模型或场景都有正向效果。用户需要根据具体模型进行测试，项目方提供对比示例有助于用户做出正确决策。

### 5. 基于项目背景，这些提交如何影响项目发展

- **从“能用”到“好用”**: 结合 README 中强调的“快速上手”和“文档”，Dreamverse 的 UI 构建和 `torch.compile` 的文档化，都是将项目从“一个强大的技术库”推向“一个易用的产品”的关键步骤。
- **巩固“Fast”品牌**: Attn-QAT 和 `torch.compile` 的优化，直接服务于项目名称中的“Fast”。这些提交表明项目团队不仅在增加功能，更在持续优化核心性能，以维持其在视频生成速度方面的竞争优势。
- **构建完整生态**: Dreamverse 的引入暗示项目可能正在构建一个包含训练、推理、部署（甚至 UI）的完整生态。这有助于吸引更广泛的用户群体，从研究人员到应用开发者，从而推动社区和项目的长期发展。

## 详细提交记录

### [266fa04](https://github.com/hao-ai-lab/FastVideo/commit/266fa044b37cdf4a01a1bf1f9b7b8073b141eb96)

- **作者**: Junda Su
- **时间**: 2026-05-22T18:36:53Z
- **提交信息**: [infra] Add Dreamverse Modal UI image build (#1381)

### [f3398db](https://github.com/hao-ai-lab/FastVideo/commit/f3398db86877b50cb4cf8456ef7cae7cd3a99a68)

- **作者**: William Lin
- **时间**: 2026-05-22T18:29:33Z
- **提交信息**: chore: pin dreamverse npm deps to address Dependabot alerts (#1359)

### [fda0203](https://github.com/hao-ai-lab/FastVideo/commit/fda02036bc69a7163e1b2764636cb099ab562454)

- **作者**: William Lin
- **时间**: 2026-05-22T09:59:25Z
- **提交信息**: [feat]: Attn-QAT inference + training backends (deadcode) (Attn-QAT 4/12) (#1358)

Co-authored-by: jzhang38 <42993249+jzhang38@users.noreply.github.com>
Co-authored-by: RandNMR73 <99706358+RandNMR73@users.noreply.github.com>

### [68179cd](https://github.com/hao-ai-lab/FastVideo/commit/68179cd752ece48c117146cce9b645440e084e25)

- **作者**: Raghav K
- **时间**: 2026-05-22T07:25:42Z
- **提交信息**: [docs] Document enable_torch_compile (+ A/B example) (#1366)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33683
- **最后更新**: 2026-05-22T16:18:10Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Guian Fang, Sayak Paul

## AI分析总结

好的，作为专业的代码分析助手，以下是对 `huggingface/diffusers` 仓库昨日提交记录的分析总结。

### 项目背景回顾

`huggingface/diffusers` 是一个用于生成图像、音频、视频等内容的扩散模型库。其核心目标是提供一个模块化、可扩展且易于使用的框架，让研究人员和开发者能够轻松地训练、推理和分享扩散模型。项目强调与 Hugging Face 生态系统的集成，支持 `AutoPipeline` 等便捷接口。

### 提交记录分析总结

#### 1. 主要更新类型

-   **功能新增（核心）**：集成了全新的 **AnyFlow** 视频扩散模型系列，包括双向（Bidirectional）和 FAR（因果自回归）两种变体。
-   **重构（大量）**：对 AnyFlow 的代码进行了多轮大规模重构，以符合 `diffusers` 库的代码规范、设计模式和最佳实践。
-   **Bug修复**：修复了在集成过程中发现的多个问题，包括类型不匹配、测试失败、状态机逻辑错误等。
-   **文档更新**：为 AnyFlow 添加了完整的英文和中文文档、教程、API 参考和转换脚本说明。
-   **测试更新**：添加并重构了与 AnyFlow 相关的单元测试和集成测试框架。

#### 2. 关键变更点及其与项目整体方向的关系

-   **集成 AnyFlow 视频扩散模型**：这是本次更新的核心。AnyFlow 是一个支持“任意步长”采样的视频生成模型，代表了视频生成领域的前沿技术。这与 `diffusers` 项目“集成最新、最先进的扩散模型”的宗旨高度一致。
-   **代码重构以符合 `diffusers` 规范**：开发者花费了大量精力将 AnyFlow 的代码从研究原型重构为符合 `diffusers` 库标准的代码。这包括：
    -   **移除 `einops` 依赖**：使用原生 PyTorch 操作替代，减少外部依赖。
    -   **使用 `dispatch_attention_fn`**：统一注意力机制的调用方式，支持不同的后端（如 Flash Attention）。
    -   **拆分 Transformer 类**：将双向和 FAR 变体拆分为独立的 `AnyFlowTransformer3DModel` 和 `AnyFlowFARTransformer3DModel`，提高模块化和可维护性。
    -   **遵循 `PipelineTesterMixin`**：确保新 Pipeline 能通过库的标准测试套件，保证其稳定性和兼容性。
    -   **添加 `# Copied from` 注释**：复用现有代码（如 Wan 模型），并通过 `make fix-copies` 工具保持同步，这是 `diffusers` 库的典型做法。
-   **完善文档和教程**：提供了详细的使用指南，包括文本到视频、图像到视频、视频到视频等多种任务场景，并提供了中英文版本。这极大地降低了用户的使用门槛，符合项目“易用性”的目标。
-   **注册到 AutoPipeline**：将 AnyFlow 的双向 Pipeline 注册到 `AUTO_TEXT2VIDEO_PIPELINES_MAPPING`，使其可以通过 `AutoPipelineForText2Video` 自动加载，增强了与 Hugging Face 生态的集成。

#### 3. 对项目的影响和潜在意义

-   **显著增强视频生成能力**：AnyFlow 的加入使 `diffusers` 库在视频生成领域的能力得到质的飞跃，为用户提供了更强大、更灵活的选择（支持任意步长采样）。
-   **树立高质量集成的标杆**：这次集成的过程（从 PR 到多轮重构）展示了如何将一个研究模型高质量地集成到 `diffusers` 中。这对于未来其他模型的集成具有重要的参考价值。
-   **提升库的健壮性和一致性**：通过强制新代码遵循库的规范和测试标准，整个项目的代码质量和内部一致性得到了提升。
-   **吸引更多研究和应用**：AnyFlow 的先进特性（如 FAR 因果注意力）和易用性（通过 AutoPipeline）将吸引更多研究者和开发者基于 `diffusers` 进行视频生成的研究和应用开发。

#### 4. 值得关注的技术点

-   **AnyFlow 的核心技术**：
    -   **Flow-Map 采样**：允许模型在任意时间步之间进行单步采样，从而实现“任意步长”的视频生成，这是其核心创新点。
    -   **FAR (Frame-Aware Autoregressive) 因果注意力**：一种块稀疏的因果注意力机制，用于高效的帧级自回归生成，特别适合长视频生成。
-   **代码重构的细节**：
    -   **`FlowMapEulerDiscreteScheduler`**：一个支持任意步长采样的新调度器，其 `step()` 方法可以接受一个目标时间步 `r_timestep`。
    -   **`AnyFlowFARTransformer3DModel`**：在 Wan 模型基础上扩展，增加了 FAR 因果模块和双时间步嵌入，结构清晰。
    -   **`flex_attention` 的使用**：FAR 变体使用了 PyTorch 的 `flex_attention` 来实现高效的块稀疏因果注意力，并处理了 CPU 回退和头维度不足等兼容性问题。
-   **测试策略**：为 FAR 变体跳过了部分在 CPU 上无法运行的训练测试（如梯度检查点），并跳过了与 FAR 分块输出语义冲突的回调测试，体现了务实的测试策略。

#### 5. 基于项目背景，这些提交如何影响项目发展

-   **巩固了 `

## 详细提交记录

### [e39aecf](https://github.com/huggingface/diffusers/commit/e39aecff57ed14d1018529c3de6ec3c34fadb559)

- **作者**: Guian Fang
- **时间**: 2026-05-22T10:15:00Z
- **提交信息**: Add AnyFlow Any-Step Video Diffusion Pipelines (Bidirectional + FAR Causal) (#13745)

* [Pipelines] AnyFlow: scaffold pipelines/anyflow + register all top-level imports

This is the lazy-loader scaffolding only. Body files (pipeline_anyflow.py,
pipeline_anyflow_causal.py, transformer_anyflow.py,
scheduling_flow_map_euler_discrete.py) come in subsequent commits.

* [Schedulers] AnyFlow: add FlowMapEulerDiscreteScheduler

The flow-map scheduler advances samples from timestep t to caller-provided
target r in a single Euler step, supporting any-step sampling on flow-map-
distilled checkpoints. It is a general-purpose scheduler — not specific to the
AnyFlow checkpoints.

Tests: 12 standalone tests covering instantiation, set_timesteps endpoints,
shift identity/monotonicity, step shape preservation, zero-interval identity,
one-shot sampling, train weight schemes, scale_noise endpoints.

Docs: api/schedulers/flow_map_euler_discrete.md

* [Models] AnyFlow: add AnyFlowTransformer3DModel

A 3D DiT extending the v0.35.1 Wan2.1 backbone with two config-toggled modules:
* FAR causal blocks (init_far_model=True): block-sparse causal attention via
  flex_attention + compressed-frame patch embedding for frame-level
  autoregressive generation (Gu et al., 2025, arXiv:2503.19325).
* Dual-timestep flow-map embedding (init_flowmap_model=True): adds a delta
  timestep embedder enabling flow-map sampling z_t -> z_r over arbitrary
  intervals (AnyFlow).

With both flags off, the model reduces to stock Wan2.1.

The class is intentionally self-contained rather than annotated with
'# Copied from diffusers.models.transformers.transformer_wan' because upstream
Wan has been refactored extensively since v0.35.1 (new WanAttention class,
different processor architecture).

Tests: 9 unit tests covering construction in 3 modes, bidi forward shape and
determinism, return_dict variants, save/load round-trip with and without
init_far_model, gradient checkpointing toggle.

Docs: api/models/anyflow_transformer3d.md

* [Pipelines] AnyFlow: add AnyFlowPipeline and AnyFlowCausalPipeline

* AnyFlowPipeline (pipeline_anyflow.py, ~590 LOC): bidirectional T2V using
  flow-map sampling. Loads checkpoints from nvidia/AnyFlow-Wan2.1-T2V-{1.3B,14B}.
* AnyFlowCausalPipeline (pipeline_anyflow_causal.py, ~700 LOC): FAR-based
  causal pipeline supporting T2V/I2V/TV2V via task_type kwarg. Loads checkpoints
  from nvidia/AnyFlow-FAR-Wan2.1-{1.3B,14B}-Diffusers.

Both pipelines reuse stock WanLoraLoaderMixin, AutoencoderKLWan, UMT5EncoderModel,
and AutoTokenizer from upstream. The transformer is the AnyFlowTransformer3DModel
introduced in the previous commit. The scheduler is FlowMapEulerDiscreteScheduler.

Tests:
* tests/pipelines/anyflow/test_anyflow.py: PipelineTesterMixin fast tests +
  slow integration test against nvidia/AnyFlow-Wan2.1-T2V-1.3B-Diffusers.
* tests/pipelines/anyflow/test_anyflow_causal.py: same structure for FAR variant.

Reference slices for slow integration tests are deferred to Phase 7
(Final quality pass) where the user runs them on a real GPU.

* [Docs] AnyFlow: add main pipeline documentation page

Modeled on the Helios pipeline doc (PR #13208). Sections: paper link + abstract,
supported checkpoints table, memory/speed optimization tabs, T2V/I2V/TV2V
examples for both bidirectional and causal variants, autodoc trailers.

* [Auto/Scripts] AnyFlow: register AutoPipelineForText2Video + add conversion script

* Register AnyFlowPipeline in AUTO_TEXT2VIDEO_PIPELINES_MAPPING.
* AnyFlowCausalPipeline is intentionally NOT registered for AutoPipeline because
  its task switch (t2v / i2v / tv2v) is too rich for a single auto-resolve key.
* scripts/convert_anyflow_to_diffusers.py: convert .pt training checkpoints
  (with 'ema' state dict) into a diffusers save_pretrained layout. Supports all
  4 released NVIDIA AnyFlow variants. Replaces the omegaconf-based config in the
  upstream repo with argparse to match other diffusers conversion scripts.

* [Quality] AnyFlow: ruff-format + regenerated dummy stubs

* ruff format pass on all 5 source files (long lines + trailing comma fixes)
* check_dummies.py --fix_and_overwrite regenerated:
  - dummy_pt_objects.py: AnyFlowTransformer3DModel + FlowMapEulerDiscreteScheduler
  - dummy_torch_and_transformers_objects.py: AnyFlowPipeline + AnyFlowCausalPipeline

Local fast tests: 21/21 passed
  - 12 scheduler tests (FlowMapEulerDiscreteScheduler)
  - 9 transformer tests (AnyFlowTransformer3DModel construction + bidi forward + save/load)

The pipeline fast tests in tests/pipelines/anyflow/ require a local dev install
that matches the diffusers main branch's transformers >= compatibility floor.
The reference slices for slow integration tests (real GPU + 1.3B/14B
checkpoints) are intentionally left as TODO stubs to be captured by the user
on a real GPU machine before opening the PR.

* [AnyFlow] address review feedback: bug fixes + DMD wording + EN/ZH tutorials

Critical bug fixes (verified against precision-validation review):
* pipeline_anyflow.py / pipeline_anyflow_causal.py: replace hardcoded
  transformer_dtype = torch.bfloat16 with self.transformer.dtype, so
  pipe.to("cpu") and PipelineTesterMixin save/load tests do not crash on a
  dtype mismatch in the patch_embedding conv3d.
* transformer_anyflow.py: drop the duplicate `base = base = ...` assignment in
  _build_causal_mask (was a copy-paste typo carried over from FAR-Dev).
* transformer_anyflow.py: drop unused `q_is_context` / `k_is_context` locals
  and the `# noqa: F841` markers that were silencing the dead-store warning.
* transformer_anyflow.py: remove `CacheMixin` from the inheritance list — the
  pipeline manages KV cache directly, the mixin's interface is unused.
* transformer_anyflow.py: guard the module-level `torch.compile(flex_attention)`
  with try/except so the file imports cleanly on CPU CI / no-Triton machines.
* convert_anyflow_to_diffusers.py: replace ad-hoc print warnings with the
  stdlib logger (warning_once-style) and a module-level basicConfig.

Documentation accuracy:
* AnyFlowCausalPipeline class docstring + main pipeline doc + EN/ZH tutorial:
  drop the fictitious `task_type` / `image` / `video` arguments and document
  the real API: pass `context_sequence={"raw": tensor}` (or `{"latent": ...}`)
  to switch between T2V (None) / I2V (1-frame) / TV2V (4n+1-frame) modes.
* Pipeline class docstrings + main doc: explicitly describe AnyFlow's
  two-stage LoRA distillation including DMD reverse-divergence supervision
  with Flow-Map backward simulation in stage 2 (was previously implicit).
* training_rollout: add detailed docstring explaining its role as the
  3-segment Flow-Map backward simulation entry point used during DMD training.
* Long-form tutorial doc `using-diffusers/anyflow.md` (EN, 239 LOC) and
  Chinese mirror `docs/source/zh/using-diffusers/anyflow.md` (224 LOC) added
  and registered in both `_toctree.yml` files.

Tests:
* Skip `test_attention_slicing_forward_pass` in both pipeline test classes
  with a clear rationale (custom attention processor does not support slicing).
* All 21 standalone tests still pass (12 scheduler + 9 transformer).

Quality gates:
* `ruff check` clean across all AnyFlow files.
* `ruff format --check` reports 6 files already formatted.
* `python utils/check_copies.py` reports no diff.

Out of scope for this commit (deferred until reviewer feedback):
* Splitting AnyFlowTransformer3DModel into bidi + causal subclasses
* Unifying _forward_inference / _forward_cache return types
* Migrating model tests from plain unittest to BaseModelTesterConfig + mixins
* HF model card / config.json metadata updates on the nvidia/* repos
  (push to Hub manually before opening the PR)

* [AnyFlow] rename Causal->FAR + explicit forward signature + dataclass output

Round 2 of review feedback. Three groups of changes; transformer state-dict
keys, module hierarchy, and tensor flow are unchanged so the H200 bit-exact
validation remains valid.

A. Pipeline rename (mechanical, no behavior change):
   * Class: AnyFlowCausalPipeline -> AnyFlowFARPipeline (Causal in diffusers
     usually means an attention mask; AnyFlow's variant is FAR autoregressive,
     so the FAR name is more specific and matches the paper).
   * File: pipeline_anyflow_causal.py -> pipeline_anyflow_far.py (git mv).
   * Test file: test_anyflow_causal.py -> test_anyflow_far.py (git mv).
   * All references updated in src/, tests/, docs/, scripts/, plus stale
     anyflowcausalpipeline anchor links in tutorial markdown.

B. Pipeline test bug fixes (closes 19 fast-test failures reported by
   precision-validation reviewer):
   * pipeline_anyflow.py / pipeline_anyflow_far.py: __call__ now sets
     self._num_timesteps = num_inference_steps before the rollout, so the
     PipelineTesterMixin callback tests can read pipe.num_timesteps.
   * tests/pipelines/anyflow/test_anyflow_far.py: drop the fictitious
     task_type="t2v" kwarg that crashed every causal fast test (the FAR
     pipeline selects mode via context_sequence, not a task_type arg).

C. Transformer architecture cleanups (review-driven, no tensor changes):
   * Replace forward(*args, **kwargs) dispatcher with an explicit signature
     listing every supported kwarg (hidden_states, timestep, r_timestep,
     encoder_hidden_states, encoder_hidden_states_image, chunk_partition,
     clean_hidden_states, clean_timestep, kv_cache, kv_cache_flag, is_causal,
     attention_kwargs, return_dict). Helps IDE / type-checker / torch.compile
     tracing.
   * Drop SimpleNamespace returns. Add AnyFlowFARTransformerOutput
     (BaseOutput dataclass with sample + kv_cache fields) for the two causal
     paths that need to also propagate kv_cache (_forward_inference and the
     newly return_dict-aware _forward_cache). _forward_train and
     _forward_bidirection now consistently return Transformer2DModelOutput.
     Pipeline call sites already use return_dict=False with positional
     unpacking, so the fix is transparent there.

Out of scope (deferred until canonical-org HF metadata sync):
   * Splitting AnyFlowTransformer3DModel into a bidi class plus an
     AnyFlowFARTransformer3DModel subclass — touches register_to_config keys
     and would require updating model_index.json on every released checkpoint.
   * Promoting chunk_partition from register_to_config to a forward-time
     argument (same reason).
   * Renaming training_rollout to _denoise — would break callers in the
     FAR-Dev on-policy trainer that produced the released checkpoints.

Local fast tests: 21/21 still pass (12 scheduler + 9 transformer).
ruff check, ruff format, and check_copies.py are all clean.

* [AnyFlow] wire callback_on_step_end through inference_range + add chunk_partition to FAR fast-test fixture

Two root causes for the 19 remaining PipelineTesterMixin failures, identified
by the H200 reviewer:

1. callback_on_step_end was accepted by __call__ but never invoked. Both
   pipelines pass it through to training_rollout (and FAR additionally through
   inference()), and inference_range now fires it after scheduler.step in
   the standard inference branch:

       if callback_on_step_end is not None:
           callback_kwargs = {k: locals()[k] for k in callback_on_step_end_tensor_inputs}
           callback_outputs = callback_on_step_end(self, i, t, callback_kwargs)
           latents = callback_outputs.pop("latents", latents)
           prompt_embeds = ...
           negative_prompt_embeds = ...

   `nonlocal prompt_embeds, negative_prompt_embeds` lets the callback rewrite
   the closure-captured embeddings, matching upstream WanPipeline semantics.
   The 3-segment grad_timestep training rollout does not invoke the callback;
   it is intentionally training-only.

2. tests/pipelines/anyflow/test_anyflow_far.py::get_dummy_components built
   the dummy transformer without a `chunk_partition`, leaving it None on the
   model config and crashing the pipeline at `sum(self.transformer.config.chunk_partition)`.
   Set `chunk_partition=[1, 1, 1]` in the fixture (3 chunks of 1 latent frame
   each, matching the test's num_frames=9 -> 3 latent frames).

Local fast tests: 21/21 still pass.
ruff check, ruff format, and check_copies.py are all clean.

* [AnyFlow] Phase 2: split transformer + drop chunk_partition from config + rename helpers

Major architectural refactor that aligns the integration with diffusers conventions
ahead of the canonical-org Hub upload. State-dict keys, module hierarchy, and
tensor flow are unchanged so the H200 bit-exact validation remains valid; only
the on-disk transformer/config.json fields move.

Changes:

1. **Sibling transformer classes** replace the flag-driven single class:
   * AnyFlowTransformer3DModel — bidirectional only. Drops compressed_patch_size /
     full_chunk_limit / init_far_model / init_flowmap_model / chunk_partition
     kwargs (always-on for AnyFlow distilled checkpoints).
   * AnyFlowFARTransformer3DModel — adds far_patch_embedding + the 3 FAR forward
     paths (train / cache-prefill / autoregressive inference).
   * AnyFlowTimeTextImageEmbedding (the legacy single-time embedder used only by
     the old setup_flowmap_model bootstrap) is removed; both classes now build
     AnyFlowDualTimestepTextImageEmbedding directly in __init__.
   * setup_flowmap_model / setup_far_model methods are removed; weight warm-start
     for far_patch_embedding (trilinear interpolation from patch_embedding) moves
     into AnyFlowFARTransformer3DModel.__init__.

2. **chunk_partition** is no longer a model config field. The FAR pipeline owns
   the schedule:
   * AnyFlowFARPipeline.default_chunk_partition = [1, 3, 3, 3, 3, 3, 3, 2]
     matches the released 81-frame NVIDIA checkpoints.
   * AnyFlowFARPipeline.__call__ / _denoise_rollout accept a chunk_partition
     argument that overrides the default for non-default num_frames.

3. **training_rollout -> _denoise_rollout** rename across both pipelines and all
   English / Chinese docs that referenced it. Signals the method is internal to
   the pipeline driver, not a public training API.

4. **Conversion script + tests + docs + registries**:
   * scripts/convert_anyflow_to_diffusers.py: VARIANTS dict picks the right
     transformer class per variant; init_far_model / init_flowmap_model /
     chunk_partition kwargs are removed from the from_pretrained call.
   * Transformer test file split into AnyFlowTransformer3DModelTest and
     AnyFlowFARTransformer3DModelTest classes.
   * Pipeline test fixtures use the right class and pass chunk_partition via
     get_dummy_inputs (3-frame schedule [1, 1, 1] for the 9-frame test).
   * New docs page docs/source/en/api/models/anyflow_far_transformer3d.md;
     anyflow_transformer3d.md rewritten for the bidi-only class.
   * AnyFlowFARTransformer3DModel registered in src/diffusers/__init__.py,
     src/diffusers/models/__init__.py, models/transformers/__init__.py and the
     dummy_pt_objects.py stubs.
   * docs/source/en/_toctree.yml: new entry for the FAR transformer page.

5. **Cleanups**:
   * Pipeline __call__ no longer passes is_causal=False to the bidi forward (the
     bidi class doesn't accept it).
   * Pipeline class docstrings drop stale references to init_*_model flags.

Local tests: 22/22 pass (12 scheduler + 10 transformer covering both classes).
ruff check / format / check_copies clean.

Hub artifacts (model_index.json, transformer/config.json, scheduler config) need
to be regenerated for the released checkpoints; the HF update guide will be
delivered separately.

* [AnyFlow] Phase 3: convention compliance against .ai/AGENTS.md + .ai/models.md

Hard violations (per official diffusers guidelines):

* drop einops dependency — replace 25+ rearrange() calls with native
  permute/reshape/unflatten in transformer + both pipelines
* device-gate torch.float64 — apply_rotary_emb and AnyFlowRotaryPosEmbed now
  fall back to float32 / complex64 on MPS / NPU; freqs are lazily rebuilt
  per-device via _build_freqs (matches transformer_wan / transformer_flux
  pattern)
* migrate attention to dispatch_attention_fn — replace direct
  F.scaled_dot_product_attention calls with dispatch_attention_fn (works
  with sage / flash / native backends); introduce AnyFlowAttention(
  AttentionModuleMixin) with _default_processor_cls / _available_processors;
  rename processors to AnyFlowAttnProcessor / AnyFlowCrossAttnProcessor and
  declare _attention_backend / _parallel_config class attrs
* drop dead config fields — qk_norm and added_kv_proj_dim are pruned from
  both transformer __init__ signatures and AnyFlowTransformerBlock;
  AnyFlowAttention is hardcoded to rms-norm-across-heads (the only scheme
  the released checkpoints use) and has no add_k_proj path (T2V only)
* add _repeated_blocks = ["AnyFlowTransformerBlock"] to both transformer
  classes for compile_repeated_blocks() support (matches Wan)
* annotate prepare_latents with `# Copied from diffusers.pipelines.wan.
  pipeline_wan.WanPipeline.prepare_latents`; the pipeline-side rearrange
  to (B, T, C, H, W) layout is moved to the call site

State-dict keys are preserved (legacy Attention had identical to_q / to_k /
to_v / to_out / norm_q / norm_k naming), so existing AnyFlow checkpoints load
bit-exactly into the new AnyFlowAttention class.

The HF Hub config-update guide is updated correspondingly: transformer/
config.json now drops qk_norm and added_kv_proj_dim alongside the previous
init_far_model / init_flowmap_model / chunk_partition removals.

22 fast CPU tests still pass; ruff format / ruff check / check_copies all
clean.

* [AnyFlow] FAR fast-test compat: rope 0-dim guard + flex_attention CPU/head-dim fallbacks + KV-cache dtype + num_timesteps

Phase 3 migrated bidi + cross-attention to dispatch_attention_fn but the FAR
causal path still calls flex_attention directly, which has hard requirements
(CPU compile, head_dim >= 16) that fail on PipelineTesterMixin's tiny dummy
components. Real ckpts (head_dim=128, CUDA) never hit these branches; bit-exact
numerical equivalence with FAR-Dev preserved on all 4 released ckpts (forward
0.00e+00, backward kernel-nondet only, ratio 1.000).

Code fixes:

1. AnyFlowRotaryPosEmbed._forward_compressed_frame / _forward_full_frame now
   short-circuit to an empty tensor when num_frames / height / width is 0.
   PipelineTesterMixin's dummy VAE has scale_factor_spatial=8, so a 16x16 raw
   spatial input becomes a 2x2 latent which then floors to 0 against
   compressed_patch_size=(1, 4, 4); the original
   `freqs[:0].view(0, k, 1, -1)` reshape was ambiguous in that regime.

2. flex_attention dispatch: split the module-load
   `torch.compile(flex_attention, dynamic=True)` into `_flex_attention_eager`
   (always available) plus `_flex_attention_compiled`, with a tiny wrapper
   that picks compiled for CUDA tensors and eager for CPU. Avoids
   torch._inductor C++ codegen failures that broke fast tests after
   `pipe.to("cpu")`. CUDA performance unchanged (L10 benchmark: 0.0% delta on
   bidi 1.3B fwd, 0.0% delta on FAR causal 1.3B fwd).

3. AnyFlowAttnProcessor (FAR causal branch): when head_dim < 16
   (flex_attention's hard minimum) zero-pad q/k/v's last dim to 16 and pass
   `scale=1/sqrt(original_head_dim)` to flex_attention. Padded value rows
   contribute 0, so trimming the output back is mathematically equivalent.
   Released ckpts use head_dim=128 so the branch is never taken in production.

4. pipeline_anyflow_far.encode_kv_cache: replace the hardcoded
   `latents.to(torch.bfloat16)` with `self.transformer.dtype`. The hardcoded
   bf16 crashed conv3d on dummy fp32 components ("Input type (BFloat16) and
   bias type (float) should be the same"); real bf16 ckpts are unaffected.

5. pipeline_anyflow_far._denoise_rollout sets
   `self._num_timesteps = (len(chunk_partition) - num_context_chunks) * num_inference_steps`
   before the chunk loop, so PipelineTesterMixin.test_callback_cfg's
   `pipe.num_timesteps`-based assertion matches the actual number of callback
   fires (chunks * NFE) instead of the previous hardcoded num_inference_steps.

Tests:

* test_callback_inputs cannot pass without changing FAR's chunk-wise output
  semantics — it zeroes latents on the final step and asserts the *entire*
  output buffer is zero, but only the active chunk's slice is overwritten in
  a chunk-wise rollout. Marked `@unittest.skip` with a detailed rationale;
  callback functionality itself is still covered by test_callback_cfg.
* Full pytest run on tests/pipelines/anyflow/ +
  tests/models/transformers/test_models_transformer_anyflow.py +
  tests/schedulers/test_scheduler_flow_map_euler_discrete.py: 81 passed,
  0 failed, 11 skipped.

Quality gates:

* `ruff check` and `ruff format --check` clean across all AnyFlow files.
* `python utils/check_copies.py` clean.
* `python utils/check_dummies.py` clean.

* [AnyFlow] docs/code: paper-release tidy-up

User-facing alignment with the official HF Hub model card and the day-of-announcement
materials at https://huggingface.co/collections/nvidia/anyflow.

* Fill in the arXiv identifier 2605.13724 (5 paper links + 2 BibTeX entries).
* Rename TV2V → V2V across docs + pipeline_anyflow{,_far}.py so the diffusers
  copy uses the same Video-to-Video terminology as the official model card.
* Add the [nvidia/anyflow](https://huggingface.co/collections/nvidia/anyflow)
  HF collection link to the three tutorial intros.
* Drop the temporary "guyuchao/* staging" tip from the EN tutorial / API page
  / ZH tutorial — the nvidia/AnyFlow-*-Diffusers repos are now live.
* Wire up NVlabs/AnyFlow (training code) and nvlabs.github.io/AnyFlow (project
  page) in place of the prior <github-org> / <project-page-url> placeholders.
* Cite the authors (Yuchao Gu, Guian Fang et al.) and NUS ShowLab × NVIDIA
  affiliation in the main tutorial, API pipeline page, and both transformer
  model pages; BibTeX uses the standard `and others` to elide the full list
  until the next pass.

Working tree, CI gates, and tests after the change:

  ruff format --check                                  ✓
  ruff check                                           ✓
  python utils/check_copies.py                         ✓
  python utils/check_dummies.py                        ✓
  pytest tests/models + tests/schedulers (22 fast)     ✓

No production code logic changes — only docstring wording inside pipeline
files (TV2V → V2V).

* [AnyFlow] docs: drop in official BibTeX (full author list)

Replace the placeholder ``@article{gu2026anyflow, author = {Gu, Yuchao and
Fang, Guian and others}, ...}`` block in both the English and Chinese
tutorials with the canonical ``@misc{gu2026anyflowanystepvideodiffusion,
...}`` form from arxiv.org/abs/2605.13724, which lists all seven authors:
Yuchao Gu, Guian Fang, Yuxin Jiang, Weijia Mao, Song Han, Han Cai,
Mike Zheng Shou.

Docs-only.

* [AnyFlow] align with diffusers conventions + drop training-only code

Scheduler
- FlowMapEulerDiscreteScheduler.step now returns a
  FlowMapEulerDiscreteSchedulerOutput dataclass (or tuple with return_dict=False)
  and uses the conventional positional order (model_output, timestep, sample,
  r_timestep).
- Drop training-only helpers: adaptive_weighting, set_train_weight,
  get_train_weight, linear_timesteps_weights, and the weight_type config field.
- Add scale_model_input no-op for API parity; raise ValueError on missing
  r_timestep.

Transformer
- Remove gate_track debug write inside
  AnyFlowDualTimestepTextImageEmbedding.forward_timestep.
- Compile flex_attention lazily on first CUDA call instead of at import time.
- Replace assert with ValueError in build_block_mask.
- Resolve <arxiv-id> placeholders to 2605.13724.

Pipelines (AnyFlowPipeline + AnyFlowFARPipeline)
- Add EXAMPLE_DOC_STRING + @replace_example_docstring and full __call__
  docstrings covering every argument.
- Move use_mean_velocity from __init__ to __call__ so save/load round-trips.
- Drop _denoise_rollout's grad_timestep branch (DMD on-policy training rollout),
  the inner inference_range closure, and the redundant negative-prompt concat.
- Replace asserts with ValueError; wire show_progress to tqdm; rename inference
  -> _inference; remove dead current_timestep property.
- Update scheduler.step call sites to the new signature.
- Trim class docstrings to inference-only language.

Pipeline output
- Add Apache 2.0 license header; switch to relative import.

Auto pipeline / conversion script
- Register AnyFlowFARPipeline in AUTO_IMAGE2VIDEO_PIPELINES_MAPPING and
  AUTO_VIDEO2VIDEO_PIPELINES_MAPPING.
- Document the weights_only=False requirement in the conversion script.

Tests
- Scheduler tests use the new step signature and verify the Output dataclass
  contract.
- Drop the four obsolete training-weight tests; drop weight_type kwarg from
  pipeline test fixtures; remove internal milestone names from TODO comments.

Docs
- Resolve <arxiv-id> in the scheduler docs page.
- Trim DMD / on-policy distillation language in EN/ZH tutorials and the
  pipelines page; the paper abstract quote is preserved verbatim.

* [AnyFlow] split FAR causal transformer into transformer_anyflow_far.py

Per @dg845's review on #13745: extract FAR causal modules into a dedicated
sibling file so each transformer variant reads in isolation. Shared submodules
are duplicated via `# Copied from` so `make fix-copies` keeps both in sync.

- `transformer_anyflow.py`: bidi-only. `AnyFlowAttnProcessor` no longer carries
  the flex/KV-cache branch (was: dispatch in one branch, bare flex_attention in
  the other); `AnyFlowRotaryPosEmbed` drops the compressed-frame helpers and
  the `is_causal` arg; `AnyFlowDualTimestepTextImageEmbedding` drops its causal
  branch. `AnyFlowTransformerBlock` keeps a single class with a new
  `is_causal: bool = False` ctor flag that selects the self-attn processor —
  the forward path is identical in both modes, only the processor differs.

- `transformer_anyflow_far.py`: new. Contains `AnyFlowFARTransformerOutput`,
  `AnyFlowCausalAttnProcessor` (routed through `dispatch_attention_fn(backend=
  "flex")` with a clear ValueError when a non-flex backend is configured; the
  BlockMask is consumed only by the flex backend in `_native_flex_attention`),
  `AnyFlowDualTimestepTextImageEmbeddingCausal`, `AnyFlowCausalRotaryPosEmbed`,
  `AnyFlowFARTransformer3DModel`, and `# Copied from` clones of the shared
  shared `AnyFlowAttention`/`AnyFlowCrossAttnProcessor`/`AnyFlowImageEmbedding`/
  `AnyFlowTransformerBlock`/`AnyFlowAttnProcessor` modules.

Verified bit-exact against the pre-refactor branch on H200 (float32):
- bidi:  L2 = 0.000e+00, max|Δ| = 0.000e+00
- FAR :  L2 = 4.772e-06, max|Δ| = 3.576e-07
The FAR delta is fp32 accumulation noise from the dispatch path permuting
(B,L,H,D) ↔ (B,H,L,D) around the same `flex_attention` kernel.

Addresses review comments at transformer_anyflow.py:215, :261, :450, :622,
:671, :958.

* [AnyFlow] pipeline cleanup: video_processor, encode_video, inline rollout, kwarg rename

Per @dg845's review on #13745, applied to both bidi `AnyFlowPipeline` and
causal `AnyFlowFARPipeline`:

- Use `self.video_processor.preprocess_video(...)` instead of the manual
  `* 2 - 1` normalize.
- Merge `vae_encode` + `encode_latents` + `_normalize_latents` into a single
  `encode_video` method, mirroring `WanImageToVideoPipeline.encode_image`'s
  flat structure.
- Inline `_denoise_rollout` into `AnyFlowPipeline.__call__`. For the FAR
  pipeline, inline both `_denoise_rollout` and `_inference` as a nested loop
  (outer over chunks, inner over denoising steps), mirroring
  `WanAnimatePipeline.__call__`. `encode_kv_cache` is intentionally kept as a
  method — it is one transformer call with a different `kv_cache_flag` mode
  (cache-write), and inlining it would interleave two distinct forward
  semantics in the same loop body and lose readability.
- Rename `context_sequence` → `video` (pixel-space) + `video_latents`
  (pre-encoded), matching `WanVideoToVideoPipeline`. For the FAR pipeline,
  the old `{"raw"/"latent"}` dict form is replaced by the two kwargs.
  Mutually-exclusive validation raises `ValueError`.

Addresses review comments at pipeline_anyflow.py:358, :372, :393, :473 and
pipeline_anyflow_far.py:395, :489, :675.

* [AnyFlow] scheduler: N-length timesteps + step defaults r_timestep

Per @dg845's review on #13745:

- `set_timesteps(N)` now produces `N` timesteps backed by an internal
  `sigmas[N+1]` linspace, matching `FlowMatchEulerDiscreteScheduler.set_
  timesteps`. The final sigma (== 0) is the implicit r-endpoint of the last
  step; the pipeline rollouts iterate `for i, t in enumerate(timesteps)`
  without the old `[:-1]` slicing.
- `step(r_timestep=None)` now defaults to the next timestep on the schedule
  (resolved via fp-tolerant `argmin` over `sigmas[:-1]`), instead of raising.
  Any-step sampling is preserved when `r_timestep` is explicit. The raise
  stays only for the case where the caller passes a `timestep` value that
  isn't on the schedule and provides no `r_timestep` — there's no sensible
  default in that case.
- Build sigmas in float64 on CPU then move to the target device, with a
  float32 downcast for MPS / NPU (float64 isn't supported on those backends).

Pipeline rollout loops updated to compute `r = sigmas[i + 1] * num_train_
timesteps` for the model's `r_timestep` input and pass `r_timestep=None` to
`scheduler.step` (which resolves it from the schedule internally).

Addresses review comments at scheduling_flow_map_euler_discrete.py:107 and
:148.

* [AnyFlow] tests: regenerate via generate_model_tests.py; split bidi/FAR files

Per @dg845's review on #13745: replaced the hand-rolled transformer tests
with the standard mixin-based suite produced by `utils/generate_model_tests
.py`, and split the FAR causal model tests into their own file to mirror the
transformer file split.

- `tests/models/transformers/test_models_transformer_anyflow.py`: regenerated
  bidi suite. Pulls in `ModelTesterMixin`, `MemoryTesterMixin`,
  `TrainingTesterMixin`, `AttentionTesterMixin`, `TorchCompileTesterMixin` via
  `BaseModelTesterConfig`, with `get_init_dict()` / `get_dummy_inputs()`
  filled in for the small bidi config used in CI.

- `tests/models/transformers/test_models_transformer_anyflow_far.py`: new.
  Same mixin set (TorchCompile is intentionally skipped — FAR's
  `_build_causal_mask` uses `flex_attention.create_block_mask(_compile=False)`
  which conflicts with the standard compile tester's assumptions; the bidi
  file covers compile, FAR is bit-exact-validated end-to-end on H200 via the
  pipeline replay). Also carries an `AnyFlowCausalAttnProcessor` smoke test
  that exercises the backend gate (non-flex backends must raise) and asserts
  the `AnyFlowFARTransformerOutput` dataclass exposes the expected fields.

Addresses review comments at test_models_transformer_anyflow.py:71 and :128.

* [AnyFlow] docs: update for video / video_latents kwarg rename

Following the pipeline kwarg refactor in e9d50b2, sweep the user-facing docs
to reflect the new API:

- `docs/source/en/api/pipelines/anyflow.md`: T2V / I2V / V2V code examples now
  use `video=` instead of `context_sequence={"raw": ...}`. The "Generation
  with AnyFlow (FAR Causal)" intro describes the new mutually-exclusive
  `video` / `video_latents` selector.

- `docs/source/en/using-diffusers/anyflow.md`: the scenario selector table,
  the "Image-to-video and video-to-video" walkthrough, and the closing note
  about pre-encoded latents are all updated. `vae_encode` references are
  replaced with `encode_video`.

* [AnyFlow] tests: skip FAR training tests on CPU (flex backward); align scheduler tests with N-length timesteps

- TestAnyFlowFARTransformer3DTraining: skip test_training / test_training_with_ema /
  test_gradient_checkpointing_equivalence on CPU. FAR causal self-attn uses
  torch.nn.attention.flex_attention whose backward kernel is GPU-only.
- test_scheduler_flow_map_euler_discrete: assert timesteps is N-length (not N+1) and
  the sigma=0 r-endpoint lives in self.sigmas[-1]; test_step_one_shot_sampling now
  exercises r_timestep=None (resolved from sigmas) since N=1 has no timesteps[1].

* [AnyFlow] docs: complete forward() Args: sections for check_forward_call_docstrings

main #13758 added utils/check_forward_call_docstrings.py which requires every signature
arg to appear as its own `name (...):` entry under Args:. Expand the bidi and FAR
transformer forward docstrings to list each parameter individually.

* [AnyFlow] apply 5/21 review suggestions (A: 1-click)

FAR transformer:
- AnyFlowCausalAttnProcessor: default _attention_backend = 'flex' (was None);
  remove None from _SUPPORTED_BACKENDS. None previously fell through to SDPA
  which silently ignored the BlockMask; failing loudly is the right default.
- dispatch_attention_fn call: read self._attention_backend instead of hardcoded
  'flex', so '_native_flex' selection works.
- _build_freqs / _forward_full_frame: add '# Copied from' to bidi RoPE.

Pipelines:
- bidi + FAR docstrings: video shape (B, C, T, H, W) -> (B, T, C, H, W) to
  match VideoProcessor.preprocess_video.
- FAR EXAMPLE_DOC_STRING: single-frame I2V tensor wrap uses unsqueeze(1) for the
  T axis instead of unsqueeze(2).
- FAR encode_video: drop duplicated @torch.no_grad() decorator.

Tests:
- test_anyflow / test_anyflow_far: lift the test_save_load_optional_components
  skip (the test actually passes).
- FAR processor smoke test: assert default backend is 'flex' (was 'None').

* [AnyFlow] apply 5/21 review suggestions (B: refactors)

Pipelines:
- check_inputs accepts video / video_latents and raises early on:
    (a) mutual exclusion (was checked late in __call__);
    (b) FAR's (num_frames - 1) % 4 == 0 constraint.
  __call__ no longer carries duplicate validation.
- FAR pipeline: drop the show_progress kwarg and replace the single tqdm with
  nested progress bars in the LLaDA-2 pattern — outer 'Chunks' (position=0)
  and per-chunk inner 'Inference Steps' (position=1, leave=False) — both
  picking up DiffusionPipeline._progress_bar_config (so set_progress_bar_config
  controls them, including disable=None).

Scheduler:
- step() resolves source and target sigmas by indexing self.sigmas via the new
  index_for_timestep(), instead of dividing the input timesteps by
  num_train_timesteps. This keeps the math correct for any future schedule
  whose timestep/sigma relationship is non-linear. For an off-schedule
  r_timestep the code falls back to r / num_train_timesteps, so explicit
  any-step sampling outside the schedule still works (and t off-schedule with
  r=None still raises a clear ValueError, as before).

Numerical equivalence: for the shipped linspace+shift schedule the two
formulations are bit-identical (verified: max abs diff = 0.0 over an N=8,
shift=5 schedule).

* [AnyFlow] apply Claude bot review (5/21): 8 findings beyond dg845's list

Finding #1 — attention_kwargs plumbing:
  Both transformers now decorate forward() with @apply_lora_scale('attention_kwargs')
  (matches Wan); pipelines forward attention_kwargs to the transformer + encode_kv_cache,
  and the unused parameter is dropped from the inner _forward_train / _forward_cache /
  _forward_inference signatures. Pipeline docstrings updated to the standard wording.

Finding #2 — naming:
  Rename far_cfg -> layout_cfg in the bidi transformer (the bidi path is not FAR; the
  FAR transformer keeps far_cfg, which is accurate there).

Finding #3 — scheduler state machine:
  Add _step_index, _begin_index, step_index property, begin_index property,
  set_begin_index(), _init_step_index(). step() lazily initializes and advances the
  counter so downstream callbacks / composable schedulers can observe rollout progress.
  Sigma resolution remains a pure function of (timestep, r_timestep) — calling step()
  twice with identical args still returns identical prev_sample (idempotent).

Finding #4 — redundant @torch.no_grad():
  Drop the redundant decorators on bidi pipeline's encode_video and FAR pipeline's
  encode_kv_cache (callers are already in __call__'s no-grad scope).

Finding #5 — dead code:
  Remove the unreachable temb.ndim == 2 else branch from the bidi transformer's
  output-norm path (condition_embedder.forward always returns a 3D temb).

Finding #6 — private rename:
  forward_far_patchify[_inference] -> _forward_far_patchify[_inference] (only called
  internally by _forward_train / _forward_cache / _forward_inference).

Finding #7 — pipeline comment numbering:
  Bidi + FAR pipelines renumber steps so the # 4. slot is no longer skipped.

Finding #8 — mask-mod comment numbering:
  _build_causal_mask numbered comments now run 1) 2) 3) ... (was 1) 3) 4) ...).

Tests:
  - New test_step_index_advances + test_set_begin_index_anchors_step_index in the
    scheduler test file exercise the new state machine.
  - All existing pipeline / transformer / scheduler tests still pass (85 passed,
    85 skipped on CPU).

Bit-exact: 8-step rollout vs the previous formulation, max abs diff = 0.0 (the new
sigma-lookup is byte-identical to t/num_train_timesteps on this schedule).

* [AnyFlow] scheduler: honour off-schedule any-step in _init_step_index; drop dead _resolve_next_timestep

Audit caught two issues in the previous scheduler commit:

1. The new state machine raised in _init_step_index whenever the first timestep
   wasn't on the active schedule, contradicting the documented contract that
   step() falls back to t/num_train_timesteps for off-schedule any-step
   sampling. The fall-back numerics were intact but they were unreachable —
   the init check fired first.

   Fix: _init_step_index now initializes _step_index to 0 when the timestep is
   off-schedule (still a valid observable counter for callbacks). step()'s
   sigma resolution is untouched, so on-schedule rollouts stay bit-exact and
   off-schedule any-step sampling actually runs again. Regression test:
   test_step_off_schedule_anystep_supported.

2. _resolve_next_timestep had no remaining callers after the step() rewrite
   inlined the same lookup. Removed (private helper, no external API).

* [AnyFlow] docs: align user guides with video shape + kwarg fixes

- en api/pipelines/anyflow.md: video shape (B, C, T, H, W) -> (B, T, C, H, W);
  example tensor wrap uses unsqueeze(0).unsqueeze(1) and permute(0, 3, 1, 2)
  to match VideoProcessor.preprocess_video's 5D contract.
- zh using-diffusers/anyflow.md: same shape fixes; also flip the I2V / V2V
  examples from the obsolete context_sequence={...} dict to the current
  video= / video_latents= kwargs; helper to_video_tensor returns (1, T, C, H, W);
  add a note about mutual exclusion.

* [AnyFlow] tests: drop @slow integration test scaffolds for initial PR

.ai/skills/model-integration/SKILL.md is explicit: 'No integration / slow
tests in the initial PR — don't add anything gated on @slow / RUN_SLOW=1
yet.' Our two integration test classes were shape-only assertions with TODOs
for a future numeric reference, so dropping them loses no actual coverage —
the relevant rollouts are covered by H200 bit-exact replay outside the
pytest suite. Can land a follow-up PR after merge with proper numeric
reference slices once the maintainer is comfortable enabling slow tests.

* Apply style fixes

* [AnyFlow] apply 5/22 dg845 review: comment cleanups + custom sigmas/timesteps schedule

dg845 third pass — 7 of 9 comments applied; the 8th (custom sigmas/timesteps support)
matches FlowMatchEulerDiscreteScheduler conventions; the 9th (_build_causal_mask
refactor) is explicitly marked non-blocking and deferred to a follow-up that also
re-enables TorchCompileTesterMixin.

Comment cleanups:
- transformer_anyflow.py:704 temb output-norm comment: drop redundant 'no ndim==2 branch'.
- pipeline_anyflow.py:550 denoise loop comment: '# 6. Denoising loop'.
- pipeline_anyflow_far.py:684 denoise loop comment: '# 8. Denoising loop (outer over
  chunks, inner over timesteps).'.
- pipeline_anyflow_far.py:702 drop trailing inline comment on `timesteps = scheduler.timesteps`.
- scheduling_flow_map_euler_discrete.py: clearer wording on the off-schedule `r_timestep`
  error.

Custom schedule support:
- FlowMapEulerDiscreteScheduler.set_timesteps gains `sigmas` and `timesteps` kwargs
  mirroring FlowMatchEulerDiscreteScheduler. Default behaviour is unchanged
  (linspace + shift); the validation + length-N → length-N+1 terminal-0 append are
  shared with the default path so on-schedule rollouts stay bit-exact.
- AnyFlowPipeline.__call__ and AnyFlowFARPipeline.__call__ accept `sigmas` and
  `timesteps` kwargs, override num_inference_steps from their length, and forward
  to set_timesteps (matches LTX2Pipeline pattern).
- New scheduler tests: test_set_timesteps_custom_sigmas and
  test_set_timesteps_custom_timesteps cover both override paths.

Dtype skip on save/load:
- TestAnyFlowTransformer3D and TestAnyFlowFARTransformer3D now skip
  test_from_save_pretrained_dtype_inference (parametrized over fp16/bf16), mirroring
  WanTransformer3DModel's skip — the test's tolerance requirements are too high for
  meaningful signal under AnyFlow's flow-map mixed-precision sampling.

* [AnyFlow] docs: apply hf-doc-builder line wrap (max_len 119)

CI doc-builder style check flagged 3 files with docstring lines >119 chars.
Ran 'doc-builder style src/diffusers docs/source --max_len 119' to autoformat;
content unchanged, line wrapping only.

* [AnyFlow] apply 5/22 follow-up review: new_zeros terminal sigma + cleanup

dg845 blocking suggestion (r3287274209):
- scheduling_flow_map_euler_discrete.py:185 — use `working_sigmas.new_zeros(1)`
  instead of `torch.zeros(1, dtype=...)` so the appended terminal sigma inherits
  both device and dtype from working_sigmas. The current working_sigmas always
  starts on CPU so the device mismatch is latent, but new_zeros is the correct
  defensive pattern and matches how the published FAR test fixtures run on CUDA.

Claude bot final-review follow-ups:
- transformer_anyflow_far.py: drop three stale `# step 3: generate attention mask`
  comments left over from the original numbered-step structure (bot #6).
- pipeline_anyflow_far.py: annotate `encode_video` with
  `# Copied from diffusers.pipelines.anyflow.pipeline_anyflow.AnyFlowPipeline.encode_video`
  and align docstring + inline comment so `make fix-copies` keeps them in sync (bot #3).

Skipped (not real / judgment-call):
- bot #2 (private rename of `_forward_far_patchify*`) — already done in 84605d5;
  bot was looking at a stale snapshot.
- bot #4 (check_inputs `# Copied from`) — FAR's check_inputs has an extra
  `(num_frames - 1) % 4 == 0` constraint that doesn't map onto the bidi version,
  so a clean `# Copied from` link would require restructuring. Bot called it a
  consistency nit; leaving as-is.
- bot #5 (`encode_kv_cache` → `_encode_kv_cache`) — bot itself flagged this as
  judgment-call territory; the helper is a coherent operation that advanced
  inference callers may want to invoke directly.

---------

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

### [6b0f61c](https://github.com/huggingface/diffusers/commit/6b0f61cc3981879b6e948a838f8fe2cb8523e835)

- **作者**: Sayak Paul
- **时间**: 2026-05-22T08:48:25Z
- **提交信息**: [docs] fix ace step checkpoint id. (#13787)

* fix ace step checkpoint id.

* style

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 404
- **最后更新**: 2026-05-21T08:16:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12460
- **最后更新**: 2026-05-22T08:41:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 28127
- **最后更新**: 2026-05-22T21:39:58Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 20
- **主要提交者**: HuangJi, zhangtao2-1, Yueming Yuan

## AI分析总结

好的，这是对 `sgl-project/sglang` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **性能优化 (Performance):** 约 4 项
- **Bug 修复 (Bug Fix):** 约 7 项
- **功能新增 (Feature):** 约 4 项
- **CI/DevOps 改进:** 约 6 项
- **文档更新 (Documentation):** 1 项
- **代码重构 (Refactor):** 约 2 项
- **硬件/平台适配 (Platform Support):** 约 3 项

### 2. 关键变更点及其与项目整体方向的关系

- **DeepSeek 模型系列深度优化 (DeepSeekV3/V4):**
    - **变更点:** 支持 DeepSeekV3 的 CUDA Graph (NSA)、移除冗余 FP32 类型转换、修复 DeepSeekV4 的 RoPE 导入问题、更新 DeepSeekV4 量化文档。
    - **项目方向:** SGLang 明确将 DeepSeek 模型作为核心优化目标之一。这些提交直接提升了其推理速度和效率，巩固了 SGLang 作为 DeepSeek 系列模型首选推理框架的地位。

- **扩散模型 (Diffusion Models) 支持增强:**
    - **变更点:** 修复 Wan 视频模型的 VAE 解码损坏、修复 MOVA DAC 在 ROCm 上的 BF16 问题、支持基于角色的组件加载和阶段亲和性、改进 CI 以防止损坏输出。
    - **项目方向:** 表明 SGLang 正在积极扩展其能力边界，从纯 LLM 推理向多模态和扩散模型领域延伸，这与 README 中“高效、灵活、快速”的定位相符。

- **核心架构与性能优化:**
    - **变更点:** 将请求 Token ID 存储迁移到 `array.array('q')`、移除 `FutureIndices` 包装类、优化 `seq_lens` 在 GPU 上的维护方式、支持分段式 CUDA Graph。
    - **项目方向:** 这些是底层基础设施的优化，旨在减少内存占用、降低延迟、提升吞吐量。这直接服务于 SGLang 作为“高性能”推理引擎的核心目标。

- **工具链与生态兼容性:**
    - **变更点:** 添加 MiniCPM5 的 XML 风格函数调用解析器、修复 Jinja2 模板渲染错误、支持 RadixLinearAttention (Qwen3.5)。
    - **项目方向:** 这表明 SGLang 致力于兼容更广泛的模型架构和工具生态，降低用户集成成本，提升框架的通用性。

### 3. 对项目的影响和潜在意义

- **性能提升:** DeepSeekV3 的优化和核心架构重构将直接转化为更低的推理延迟和更高的吞吐量，对生产环境部署至关重要。
- **功能扩展:** 对扩散模型和 MiniCPM5 的支持，使 SGLang 从一个 LLM 推理引擎向一个通用 AI 推理平台演进，能吸引更多不同领域的用户。
- **稳定性增强:** 修复了多个 Bug（如 SWA 双重释放、VAE 解码损坏），提升了框架在各种复杂场景下的可靠性。
- **开发者体验改善:** CI 流程的优化（如批量 cherry-pick、更精细的测试触发）和文档更新，降低了开发和维护成本，提升了社区贡献效率。

### 4. 值得关注的技术点

- **`array.array('q')` 存储 Token ID:** 这是一个非常精巧的性能优化。将 Python 列表替换为 C 级别的 `array`，可以显著减少内存占用和访问开销，尤其在高并发场景下效果明显。
- **分段式 CUDA Graph (Piecewise CUDA Graph):** 这是对传统 CUDA Graph 技术的改进，可能允许在动态形状或复杂控制流下更灵活地使用 Graph 加速，是提升模型执行效率的前沿技术。
- **`FutureMap` 调试断言:** 在 `FutureMap` 中增加调试断言，体现了项目对异步执行正确性的严谨态度，有助于在开发阶段及早发现潜在的竞态条件或数据依赖问题。
- **扩散模型的角色加载与阶段亲和性:** 这是一种高级的调度策略，允许根据模型的不同部分（如文本编码器、UNet、VAE）分配不同的计算资源，对于优化多阶段、异构的扩散模型推理流程非常有价值。

### 5. 基于项目背景的综合分析

结合 README 中“高效、灵活、快速”的定位，昨日的更新清晰地展示了 SGLang 的发展路径：

1.  **巩固核心优势 (高效):** 通过针对 DeepSeekV3 的深度优化和底层架构重构，SGLang 在 LLM 推理性能上的领先地位得到进一步强化。这些优化直接回应用户对“快”的核心需求。
2.  **拓展能力边界 (灵活):** 对扩散模型、MiniCPM5 等新模型的支持，以及更完善的工具链（如函数调用解析器），表明 SGLang 正在从单一的 LLM 服务框架，向支持多种 AI 工作负载的通用平台演进，提升了框架的“灵活”性。
3.  **夯实工程基础 (快速):** 大量的 CI 改进、Bug 修复和平台适配（Intel GPU, XPU, MUSA），确保了框架在多种硬件和复杂场景下的稳定性和可维护性，为“快速”迭代和部署提供了坚实基础。

**总结:** 昨日的更新是 SGLang 项目一次高质量的

## 详细提交记录

### [cadfa2d](https://github.com/sgl-project/sglang/commit/cadfa2d025d3e251352a115291621c8214c733e5)

- **作者**: nvjullin
- **时间**: 2026-05-22T21:39:50Z
- **提交信息**: Support piecewise CUDA graph with NSA (#23351)

### [2df9e8b](https://github.com/sgl-project/sglang/commit/2df9e8b4b33112eed19d707b4e51e5a90ac39ce8)

- **作者**: maocheng23
- **时间**: 2026-05-22T21:23:57Z
- **提交信息**: [perf] DeepSeekV3: drop redundant FP32 upcasts in trtllm MoE paths (#25189)

### [b73278e](https://github.com/sgl-project/sglang/commit/b73278e4e007f0cda168048d27dc288efa17a0d4)

- **作者**: Minglei Zhu
- **时间**: 2026-05-22T20:30:35Z
- **提交信息**: [Fix]: BCG support for RadixLinearAttention (Qwen3.5 / linear-attn hybrid models) (#25110)

### [763174f](https://github.com/sgl-project/sglang/commit/763174fa6c1a98261eb5f1c022dc0138330b51b3)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-22T20:10:57Z
- **提交信息**: FutureMap: debug-assert that gather sees a stashed value (#26108)

### [0857772](https://github.com/sgl-project/sglang/commit/085777210c2f65aeb1d55dda75a50b1fbd6ed32a)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-22T17:59:45Z
- **提交信息**: feat(kv-events): expose structured KV-event publisher block on /server_info (#25844)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [06c23d5](https://github.com/sgl-project/sglang/commit/06c23d55b58e520a92944f7b6f788cdd01543d03)

- **作者**: Jialin Ouyang
- **时间**: 2026-05-22T17:51:07Z
- **提交信息**: perf: migrate Req token-id storage to array.array('q') in Scheduler (#25098)

Co-authored-by: jialino <jialino@fb.com>

### [5e9bd21](https://github.com/sgl-project/sglang/commit/5e9bd21979d1a9f844452c2d3d332144064fff59)

- **作者**: fanghao
- **时间**: 2026-05-22T16:43:26Z
- **提交信息**: fix(serving_chat): catch TypeError from tojson on Jinja2 Undefined variables (#20700)

### [b801a27](https://github.com/sgl-project/sglang/commit/b801a27ce6e760f788c06daaa0cec18360d9722f)

- **作者**: Mick
- **时间**: 2026-05-22T15:36:47Z
- **提交信息**: [diffusion] CI: disable torch compile in nightly comparison (#26120)

### [9bbd519](https://github.com/sgl-project/sglang/commit/9bbd519f34d6665c61466834909de796e5ab758d)

- **作者**: HuangJi
- **时间**: 2026-05-22T15:34:41Z
- **提交信息**: [diffusion] fix: fix Wan channels_last_3d VAE decode corruption (#25985)

### [6baa859](https://github.com/sgl-project/sglang/commit/6baa859a869cbed25c6e66975558ca276ac9713b)

- **作者**: zhangtao2-1
- **时间**: 2026-05-22T15:09:40Z
- **提交信息**: Add MiniCPM5 tool call parser for XML-style function calls (#25600)

Co-authored-by: zhangtao <zhangtao2@modelbest.cn>

### [f5ed268](https://github.com/sgl-project/sglang/commit/f5ed2687ec6a748dd9922e14b88c97bac8567612)

- **作者**: Mick
- **时间**: 2026-05-22T11:07:20Z
- **提交信息**: [diffusion] CI: guard gt publishing from corrupt output (#26044)

### [8c916a7](https://github.com/sgl-project/sglang/commit/8c916a715cf6933abf63156dfef206b823abf29d)

- **作者**: Heyang Huang
- **时间**: 2026-05-22T10:50:23Z
- **提交信息**: [diffusion] feat: support role-based component loading and stage affinity (#25168)

### [e1dcbca](https://github.com/sgl-project/sglang/commit/e1dcbca220ee7077889f24155f00d1703635d722)

- **作者**: kousakawang
- **时间**: 2026-05-22T10:39:47Z
- **提交信息**: [FIX][1/2] fix step3-vl/deepseek-ocr image processor error (#24701)

Co-authored-by: wanghanpei <wanghanpei@bytedance.com>

### [80680dc](https://github.com/sgl-project/sglang/commit/80680dc3fe7de3bbf5a1ef06abdb32c1d0ab0982)

- **作者**: Polisetty V R K Jyothendra Varma
- **时间**: 2026-05-22T10:23:18Z
- **提交信息**: [Intel GPU] 1/N Fix tilelang import in deepseek v4 rope as optional (#25128)

### [d4082ea](https://github.com/sgl-project/sglang/commit/d4082eab4d1c78b645c16c50ad4d8038a0040593)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-22T10:03:39Z
- **提交信息**: [CI] pr-test-extra: add run_all_tests to workflow_dispatch inputs (#26110)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [10751a4](https://github.com/sgl-project/sglang/commit/10751a4f0cb1cc9ae88556a546840adec5d27b0b)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-22T09:44:42Z
- **提交信息**: drop `FutureIndices` wrapper class (#26085)

### [bd6c7e7](https://github.com/sgl-project/sglang/commit/bd6c7e713cd076cdb381ee1ed69686a89a312351)

- **作者**: Yueming Yuan
- **时间**: 2026-05-22T09:01:40Z
- **提交信息**: [fix] Fallback DeepGEMM activation for unsupported shapes (#26025)

### [4486a33](https://github.com/sgl-project/sglang/commit/4486a339a3696522e40160c36b26d7a8373ec87d)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-22T08:27:46Z
- **提交信息**: [CI] bot-cherry-pick: remove concurrency group to enable batch dispatch (#26074)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [cf5f496](https://github.com/sgl-project/sglang/commit/cf5f49618340e5908701c8f2bb356b4acbabe230)

- **作者**: johnnycxm
- **时间**: 2026-05-22T08:24:25Z
- **提交信息**: [MUSA][22/N] ci(musa): repack wheels with +musa metadata, refine path filters, sync multimodal tests, and add nightly workflow (#25074)

Co-authored-by: xinyue.fan <xinyue.fan@mthreads.com>

### [16d049f](https://github.com/sgl-project/sglang/commit/16d049f898ec181405d2a17a1fe9312eb48f3b96)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-22T08:20:06Z
- **提交信息**: Add sglang-cherrypick skill for batching bot-cherry-pick dispatches (#26068)

Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>

### [63ecf2f](https://github.com/sgl-project/sglang/commit/63ecf2f62b18d95d1512e355bd6ed5cce1f85dab)

- **作者**: Kangyan-Zhou
- **时间**: 2026-05-22T08:16:07Z
- **提交信息**: [CI] Drop unused 'environment: prod' from bot-cherry-pick job (#26067)

### [06836aa](https://github.com/sgl-project/sglang/commit/06836aa38a41e5506c8fd4d8780a24caaa9862a2)

- **作者**: siyu
- **时间**: 2026-05-22T08:13:28Z
- **提交信息**: update code owner (#26060)

### [6339295](https://github.com/sgl-project/sglang/commit/633929555614953024451927e2a29b78625e6afa)

- **作者**: jiayisunx
- **时间**: 2026-05-22T08:09:08Z
- **提交信息**: [XPU] add apache-tvm-ffi dependency (#26053)

### [88a37d7](https://github.com/sgl-project/sglang/commit/88a37d740511fa7519eeeac4bef5e707b4c67327)

- **作者**: zijiexia
- **时间**: 2026-05-22T07:52:10Z
- **提交信息**: [docs] DeepSeek-V4 cookbook: split Quantization axis, add H100 SGLang FP8 (#26057)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [c9153da](https://github.com/sgl-project/sglang/commit/c9153da5dca5fb1ee1a0bd765432dd56e1fc0e5b)

- **作者**: Yuhao Yang
- **时间**: 2026-05-22T07:28:54Z
- **提交信息**: Fix SWA double-free in disagg decode with MTP speculation (#25805)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [a7555fc](https://github.com/sgl-project/sglang/commit/a7555fc997f36ef3f0ed53a7632cece1e93e6314)

- **作者**: Chi McIsaac
- **时间**: 2026-05-22T07:18:49Z
- **提交信息**: [diffusion] fix: fix MOVA DAC bf16 on ROCm (#25674)

### [c4b6b5e](https://github.com/sgl-project/sglang/commit/c4b6b5ea1e0e7f9cd94638cd985082023d279fe5)

- **作者**: Liangsheng Yin
- **时间**: 2026-05-22T07:12:51Z
- **提交信息**: [core] step 2: drop seq_lens sentinel; SB maintains GPU as `seq_lens_cpu` mirror (#26020)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization for Diffusion Transformers.
- **语言**: Python
- **星标数**: 1178
- **最后更新**: 2026-05-22T08:28:02Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

好的，这是对 `vipshop/cache-dit` 仓库昨日提交记录的分析总结：

### 1. 主要更新类型
*   **Bug修复**：主要修复了在特定分布式场景下的序列化问题。
*   **功能增强**：使“逐层卸载”（layerwise offload）功能与 `torch.compile` 兼容。

### 2. 关键变更点及其与项目整体方向的关系
*   **`feat: make layerwise offload compatible w/ compile`**：
    *   **变更点**：使“逐层卸载”功能能够与 PyTorch 的 `torch.compile` 技术协同工作。
    *   **与项目关系**：`cache-dit` 是一个专注于 Diffusion Transformers 推理加速的引擎，其核心优势在于“缓存”（Cache）和“并行化”（Parallelism）。`torch.compile` 是 PyTorch 2.x 中关键的图编译优化技术，能大幅提升模型执行效率。此提交将“逐层卸载”（一种显存优化策略）与 `torch.compile` 结合，意味着用户可以在享受显存优化的同时，获得图编译带来的性能提升，这是对项目核心“性能优化”目标的直接增强。

*   **`ray: fix custom components serialize`**：
    *   **变更点**：修复了在 Ray 分布式框架下，自定义组件无法正确序列化的问题。
    *   **与项目关系**：`cache-dit` 支持通过 Ray 进行分布式推理，以实现“并行化”。序列化是分布式计算的基础，自定义组件（如特定的缓存策略、量化算子等）无法序列化将导致分布式任务失败。此修复确保了项目的分布式能力稳定可靠，是支撑其“并行化”特性的关键基础设施修复。

### 3. 对项目的影响和潜在意义
*   **提升可用性与兼容性**：修复 Ray 序列化问题，直接提升了项目在分布式环境下的稳定性和易用性，降低了用户在使用 Ray 部署时遇到错误的概率。
*   **解锁性能潜力**：使“逐层卸载”与 `torch.compile` 兼容，为用户提供了“显存优化 + 计算加速”的组合能力。这允许用户在有限的显存资源下，运行更大的模型或批次，同时获得更快的推理速度，这对于 Diffusion Transformers 这类显存和计算密集型模型意义重大。
*   **巩固技术栈**：这两个提交分别强化了项目在“并行化”（Ray）和“性能优化”（`torch.compile`）两个核心方向上的技术实现，使 `cache-dit` 的推理引擎更加成熟和强大。

### 4. 值得关注的技术点
*   **`torch.compile` 兼容性**：这是一个值得关注的技术点。`torch.compile` 对模型代码有特定要求，并非所有自定义操作都能直接兼容。成功使“逐层卸载”兼容 `torch.compile`，说明项目团队对 PyTorch 的底层编译机制有深入理解，并可能对代码进行了必要的重构或适配。
*   **Ray 序列化机制**：修复自定义组件的序列化问题，通常涉及到对 Ray 的 `__getstate__`/`__setstate__` 或 cloudpickle 等序列化协议的深入理解和正确实现。这体现了项目在处理复杂分布式系统细节上的严谨性。

### 5. 基于项目背景，这些提交如何影响项目发展
*   **强化核心卖点**：`cache-dit` 的定位是“PyTorch-native”且集成了“Cache, Parallelism, Quantization”的推理引擎。本次更新直接强化了“Parallelism”（通过修复 Ray 序列化）和“Performance”（通过 `torch.compile` 与 offload 的结合），使其核心卖点更加扎实。
*   **降低用户门槛**：修复分布式部署的 bug，并解锁更优的性能组合，降低了用户在生产环境中使用 `cache-dit` 的门槛和顾虑，有助于吸引更多用户，特别是那些需要大规模部署 Diffusion Transformers 的用户。
*   **技术领先性**：积极拥抱 `torch.compile` 这样的前沿技术，并解决其与高级显存管理策略的兼容性问题，展示了项目团队的技术实力和追求极致性能的决心，有助于在同类开源项目中保持技术领先地位。

## 详细提交记录

### [929041e](https://github.com/vipshop/cache-dit/commit/929041eeaddb2eba434e19baf0bd3d03600bed78)

- **作者**: DefTruth
- **时间**: 2026-05-22T08:27:55Z
- **提交信息**: ray: fix custom components serialize (#1015)

* feat: make layerwise offload compatible w/ compile

* ray: fix custom components serialize

* ray: fix custom components serialize

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 80748
- **最后更新**: 2026-05-22T23:12:30Z

## 提交统计

- **昨日提交总数**: 31
- **提交者数量**: 26
- **主要提交者**: Juhi Mittal, Ilya Markov, wangxiyuan

## AI分析总结

好的，这是对 vllm-project/vllm 仓库昨日（根据提交记录推断）更新的分析总结。

### 1. 主要更新类型

- **功能新增 (Features):** 约 8 项
- **Bug 修复 (Bugfixes):** 约 7 项
- **性能优化 (Performance):** 约 3 项
- **重构 (Refactoring):** 约 5 项
- **文档更新 (Documentation):** 1 项
- **CI/构建修复 (CI/Build):** 约 3 项
- **硬件平台适配 (Platform Support):** 约 3 项

### 2. 关键变更点及其与项目整体方向的关系

- **核心方向：MoE (Mixture-of-Experts) 模型支持与优化**
    - **`[6d30655]`**: 为 MoE 模型在弹性专家并行（Elastic EP）场景下，提交了量化方法的重新配置逻辑。这直接服务于 vLLM 对大规模、动态 MoE 模型（如 DeepSeek-V4）的高效服务。
    - **`[e203006]` & `[fb21d8b]`**: 为 DeepSeek-V4 模型添加了 NVFP4 (W4A16) 量化支持，并实现了混合精度调度。这显著降低了 MoE 模型的内存占用和推理延迟，是 vLLM 追求“便宜且快速”服务的关键举措。
    - **`[8437157]`**: 将 DeepSeek V4 的稀疏 MLA (Multi-head Latent Attention) 实现提取到模型文件夹中，这是对特定模型架构的代码组织优化，便于后续维护和扩展。

- **核心方向：推理性能与效率**
    - **`[4e2eba2]`**: 优化了隐藏状态（hidden state）的提取逻辑，这是一个通用性能优化，能提升所有模型的推理吞吐量。
    - **`[47d4407]`**: 在 Model Runner V2 中支持共享 KV Cache 层。这是对内存管理的重大改进，通过减少 KV Cache 的冗余存储，可以支持更大的批处理大小或更长的上下文，直接提升服务效率。
    - **`[08cb467]`**: 移除了 `mhc_post` 中的 `sts` 指令并添加了向量化拷贝，这是一个底层算子优化，旨在提升特定硬件上的计算速度。

- **核心方向：硬件平台扩展**
    - **`[8de5cab]` & `[d3d1cf6]`**: 为 Intel XPU 平台添加了 DeepSeek-V4 相关算子的支持，以及 MoE TopK 路由和 MXFP4 后端的 XPU 回退方案。这体现了 vLLM 致力于支持多种硬件（如 Intel GPU）的承诺。
    - **`[65b7a81]`**: 在 CPU 平台上实验性地启用了 Triton 和 Model Runner V2。这表明 vLLM 正在探索将高性能推理扩展到 CPU 的可能性，以覆盖更广泛的部署场景。

- **核心方向：稳定性与可靠性**
    - **`[4e597b7]`**: 修复了在不支持的 GPU 上使用 FP8 torchao 量化时，错误信息不清晰的问题。这改善了用户体验，帮助用户快速定位问题。
    - **`[23f7b11]`**: 修复了 FlashInfer 中检测错误 `libcute_dsl_runtime.so` 变体的问题，增强了库依赖的健壮性。
    - **`[4658bf7]`**: 修复了在多模态（MM）场景下，由于缓存未清除导致的 `mm_hash` 不同步问题，保证了多模态推理的正确性。

### 3. 对项目的影响和潜在意义

- **对 DeepSeek-V4 的深度优化**：本次更新中，有多个提交直接针对 DeepSeek-V4 模型，包括量化、算子优化和代码重构。这表明 vLLM 正与 NVIDIA 等合作伙伴紧密合作，将 DeepSeek-V4 这类前沿模型作为标杆，推动其推理性能达到极致。
- **内存效率的重大提升**：`[47d4407]` 的 KV Cache 共享和 `[e203006]` 的 NVFP4 量化，将显著降低服务大型模型（尤其是 MoE 模型）的内存开销。这直接转化为更低的推理成本和更高的吞吐量，完美契合 vLLM “便宜且快速” 的核心理念。
- **硬件生态的持续扩展**：对 Intel XPU 和 CPU 平台的持续投入，表明 vLLM 不满足于仅支持 NVIDIA GPU。这有助于打破硬件垄断，为用户提供更多选择，扩大其用户基础。
- **代码库健康度提升**：大量的 Bug 修复、重构和 CI 修复，表明项目在快速迭代新功能的同时，也非常注重代码质量和稳定性。这为 vLLM 在生产环境中可靠运行奠定了基础。

### 4. 值得关注的技术点

- **弹性专家并行 (Elastic EP) + 量化**：`[6d30655]` 将 MoE 量化与弹性 EP 结合，这是一个高级特性，允许在动态调整专家数量的同时保持量化状态，对大规模分布式推理至关重要。
- **Model Runner V2 的 KV Cache 共享**：`[47d4407]` 是 Model Runner V2 架构演进的重要一步。共享 KV Cache 是实现 Prefix Caching 等高级特性的基础，

## 详细提交记录

### [6d30655](https://github.com/vllm-project/vllm/commit/6d30655b136bec37e7e7c7d045f1bcedc8cf3e2b)

- **作者**: Itay Alroy
- **时间**: 2026-05-22T22:57:26Z
- **提交信息**: elastic_ep: stage/commit MoE quant method on reconfigure (#40881)

Signed-off-by: Itay Alroy <ialroy@nvidia.com>

### [8de5cab](https://github.com/vllm-project/vllm/commit/8de5cabeb70df7a9ba835c423b66c2ec51dbeefc)

- **作者**: Ma Jian
- **时间**: 2026-05-22T22:29:45Z
- **提交信息**: [XPU]fix: add XPU platform guards to DeepSeek-V4 ops (#42950)

Signed-off-by: Ma Jian <jian1.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [4e2eba2](https://github.com/vllm-project/vllm/commit/4e2eba28beec9972445c338e8ad2080b3cab3246)

- **作者**: Benjamin Chislett
- **时间**: 2026-05-22T22:23:08Z
- **提交信息**: [Perf] Optimize hidden state extraction logic (#37374)

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Signed-off-by: Benjamin Chislett <chislett.ben@gmail.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [f743254](https://github.com/vllm-project/vllm/commit/f743254143f25e7f3519b2cd5f3f766692b6e397)

- **作者**: gnovack
- **时间**: 2026-05-22T22:21:33Z
- **提交信息**: DSv4 fused Q-norm kernel grid refactor (#42353)

### [47d4407](https://github.com/vllm-project/vllm/commit/47d4407d7cbb2a70fd02d73f34407caeee6ae565)

- **作者**: Nick Hill
- **时间**: 2026-05-22T22:18:23Z
- **提交信息**: [Model Runner V2] Support sharing kv cache layers (#35045)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [e203006](https://github.com/vllm-project/vllm/commit/e203006a8b05b6380f7deb261c28f384711674c1)

- **作者**: Juhi Mittal
- **时间**: 2026-05-22T20:51:49Z
- **提交信息**: [Quantization][ModelOpt] W4A16 NVFP4 fused MoE + mixed-precision dispatch (#42566)

Signed-off-by: Juhi Mittal <juhim@nvidia.com>

### [08cb467](https://github.com/vllm-project/vllm/commit/08cb46789d31e07f515243d646ca7f5df2d8d3e7)

- **作者**: gnovack
- **时间**: 2026-05-22T20:44:29Z
- **提交信息**: mhc_post - remove sts & add vectorized copies (#43437)

Signed-off-by: george <george@inferact.ai>
Co-authored-by: george <george@inferact.ai>

### [4e597b7](https://github.com/vllm-project/vllm/commit/4e597b749144d4b3f0716994b95486ab734b185f)

- **作者**: haosdent
- **时间**: 2026-05-22T20:09:17Z
- **提交信息**: [Bugfix] Clear error message for FP8 torchao quantization on unsupported GPUs (#36854)

Signed-off-by: haosdent <haosdent@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [23f7b11](https://github.com/vllm-project/vllm/commit/23f7b11bf4b715ee6084ea368c929789184a8555)

- **作者**: Artem Perevedentsev
- **时间**: 2026-05-22T19:33:33Z
- **提交信息**: [Bugfix] Detect wrong libcute_dsl_runtime.so variant in FlashInfer GDN (#43427)

Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [977703a](https://github.com/vllm-project/vllm/commit/977703aa94fa946e19a70de4c105625600255b66)

- **作者**: SandishKumarHN
- **时间**: 2026-05-22T19:19:24Z
- **提交信息**: [RFC][EPLB][#32028] Remove dead torch.accelerator.synchronize() from sync path (#40733)

Signed-off-by: SandishKumarHN <3078999+SandishKumarHN@users.noreply.github.com>
Co-authored-by: SandishKumarHN <3078999+SandishKumarHN@users.noreply.github.com>

### [2b94d1c](https://github.com/vllm-project/vllm/commit/2b94d1c0caf69d4108d720986f4e792960b02cf7)

- **作者**: Russell Bryant
- **时间**: 2026-05-22T18:59:14Z
- **提交信息**: [Frontend] Simplify AuthenticationMiddleware path extraction (#43426)

Signed-off-by: Russell Bryant <rbryant@redhat.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>

### [8437157](https://github.com/vllm-project/vllm/commit/843715739b7b555c61dd6190cafb5ab7a44c41f1)

- **作者**: Yongye Zhu
- **时间**: 2026-05-22T17:06:31Z
- **提交信息**: [Refactor] Extract DeepSeek V4 sparse MLA impl into model folder (#43149)

### [b21f3d5](https://github.com/vllm-project/vllm/commit/b21f3d56d4a2ab5504b56504e87e0475c6d84eb2)

- **作者**: Dao007forever
- **时间**: 2026-05-22T16:14:11Z
- **提交信息**: [KV Connector] MooncakeStore: don't co-queue save with load to avoid double delayed-free (#43371)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [c7624be](https://github.com/vllm-project/vllm/commit/c7624bea5ebba1c688eb4c216bd4ede7a94f2a82)

- **作者**: Zhanda Zhu
- **时间**: 2026-05-22T16:10:03Z
- **提交信息**: [Bugfix] Source num_qo_heads from Attention layers in Flashinfer/Triton metadata builders (#42650)

Signed-off-by: zhanda <zhandazhu@gmail.com>
Co-authored-by: Shang Wang <shangw@nvidia.com>

### [91f5b92](https://github.com/vllm-project/vllm/commit/91f5b92438a568c89e8b9d6c2c55de5a552291f6)

- **作者**: Bugen Zhao
- **时间**: 2026-05-22T15:22:11Z
- **提交信息**: [Rust Frontend] [Refactor] Extract a newtype for utility call ID (#43405)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [f0feb15](https://github.com/vllm-project/vllm/commit/f0feb15e7fc521544d23c2d23de0e327a509876b)

- **作者**: Isotr0py
- **时间**: 2026-05-22T14:31:00Z
- **提交信息**: [Multimodal] Simplify ViT CUDA graph interfaces (#41234)

Signed-off-by: Isotr0py <mozf@mail2.sysu.edu.cn>

### [fb21d8b](https://github.com/vllm-project/vllm/commit/fb21d8b4f9027f4642637c7bb0acc08c29dce387)

- **作者**: sychen52
- **时间**: 2026-05-22T14:21:51Z
- **提交信息**: Add NVFP4 MOE support for Deepseek V4. (#42209)

Signed-off-by: Shiyang Chen <shiychen@nvidia.com>

### [a377631](https://github.com/vllm-project/vllm/commit/a377631d21cc97db678727455d33c4257435f417)

- **作者**: haosdent
- **时间**: 2026-05-22T14:06:24Z
- **提交信息**: [CI] Fix AMD docker build tests (#43329)

Signed-off-by: haosdent <haosdent@gmail.com>

### [d3a5635](https://github.com/vllm-project/vllm/commit/d3a563501bcc6134a348f8458b1a797c94336f1f)

- **作者**: Ilya Markov
- **时间**: 2026-05-22T13:43:27Z
- **提交信息**: [EPLB] Change default EPLB communicator (#43110)

Signed-off-by: Markov Ilya <markovilya19@gmail.com>
Co-authored-by: Markov Ilya <markovilya19@gmail.com>

### [15f7cd3](https://github.com/vllm-project/vllm/commit/15f7cd33dc8bd4d2270b70ba49d511827d2413ff)

- **作者**: Jee Jee Li
- **时间**: 2026-05-22T13:41:56Z
- **提交信息**: [LoRA] Reduce memory of 2D weights when EP is set (#42737)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [79ff0ff](https://github.com/vllm-project/vllm/commit/79ff0ffa98dc8dd14a8651bce36ce6265ff4d35d)

- **作者**: Keyi Li
- **时间**: 2026-05-22T12:26:41Z
- **提交信息**: [BugFix] wire make_empty_intermediate_tensors on AyaVision and Voxtral (#43118)

Signed-off-by: Keyi Li <likey6688@gmail.com>
Co-authored-by: Keyi Li <likey6688@gmail.com>

### [4658bf8](https://github.com/vllm-project/vllm/commit/4658bf882b881287fc85797a23037aa91740b7a7)

- **作者**: Tobias Wasner
- **时间**: 2026-05-22T10:54:29Z
- **提交信息**: [Bugfix] Clear P0 mm sender cache on sleep/pause to fix mm_hash desync (#43001)

Signed-off-by: Tobias Wasner <wasnertobias@gmail.com>

### [b3c7ffc](https://github.com/vllm-project/vllm/commit/b3c7ffcab82c2439726f8cb213800f6f38c023d3)

- **作者**: Taneem Ibrahim
- **时间**: 2026-05-22T10:43:33Z
- **提交信息**: [Misc] Replace assert with proper exceptions for security and validation in pooling (#43286)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [d3d1cf6](https://github.com/vllm-project/vllm/commit/d3d1cf6972607c53327b5ce1748e56a95fc41c37)

- **作者**: Ma Jian
- **时间**: 2026-05-22T10:22:45Z
- **提交信息**: [XPU]feat: add XPU fallback for MoE topk routing and MXFP4 backend (#42951)

Signed-off-by: Ma Jian <jian1.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [7e1b45a](https://github.com/vllm-project/vllm/commit/7e1b45a09252a5b513cd83116aa7a2f310220c34)

- **作者**: wangxiyuan
- **时间**: 2026-05-22T09:13:12Z
- **提交信息**: [Attention] Mamba attention module refactor (#41126)

Signed-off-by: wangxiyuan <wangxiyuan1007@gmail.com>

### [65b7a81](https://github.com/vllm-project/vllm/commit/65b7a812a2dabd212d78c7b5b8a320b4efb9750d)

- **作者**: Li, Jiang
- **时间**: 2026-05-22T08:48:17Z
- **提交信息**: [CPU] Experimentally enable Triton and MRV2 (#43225)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [2380bfc](https://github.com/vllm-project/vllm/commit/2380bfc2104267914eea36015e2a347b9318c6c0)

- **作者**: wang.yuqi
- **时间**: 2026-05-22T08:43:14Z
- **提交信息**: [Docs] Note image preprocessing difference between qwen_vl_utils and vllm. (#43393)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>
Signed-off-by: wang.yuqi <noooop@126.com>
Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>

### [a761697](https://github.com/vllm-project/vllm/commit/a7616977176e12ddb14c0daab00cd2a2161ba37c)

- **作者**: mrjunwan-lang
- **时间**: 2026-05-22T08:36:17Z
- **提交信息**: Fix the docker build failure in tpu-inference (#43360)

Signed-off-by: mrjunwan-lang <mrjunwan@google.com>

### [694d9a8](https://github.com/vllm-project/vllm/commit/694d9a81bbb07977e7a72a597acb44f6a848f774)

- **作者**: Nick Hill
- **时间**: 2026-05-22T07:25:10Z
- **提交信息**: [BugFix] Fix setuptools-rust dep in requirements files (#43377)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [6bb8753](https://github.com/vllm-project/vllm/commit/6bb8753db1076f498c240fffdd88b1ab983b7f40)

- **作者**: Weida Hong
- **时间**: 2026-05-22T07:21:35Z
- **提交信息**: Correcting the mock classes for MM GC tests (#43321)

Signed-off-by: Weida Hong <wdhongtw@google.com>

### [025d4f5](https://github.com/vllm-project/vllm/commit/025d4f5cd2617bb767663f9e7d62354039887757)

- **作者**: haosdent
- **时间**: 2026-05-22T07:13:59Z
- **提交信息**: [CI] Fix "test_awq_load[gemma4-moe-*]" failure (#43296)

Signed-off-by: haosdent <haosdent@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-05-23
**监控日期**: 2026-05-22
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4857
- **最后更新**: 2026-05-22T19:05:39Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: Yueqian Lin, Alex Brooks, univa-HARRY

## AI分析总结

好的，这是对 `vllm-project/vllm-omni` 仓库昨日提交记录的分析总结。

### 1. 主要更新类型

- **性能优化 (Perf):** 1项
- **功能新增 (Feature):** 1项
- **Bug修复 (Bugfix):** 3项
- **配置/部署 (Recipe/Config):** 1项
- **CI/基础设施 (CI):** 1项

### 2. 关键变更点及其与项目整体方向的关系

- **性能优化：Triton Kernel融合 + CUDA Graph加速 (`OmniVoice`)**
    - **变更点:** 对 `OmniVoice` 模块进行了底层性能优化，通过融合Triton内核和利用CUDA Graph技术来加速推理。
    - **项目关系:** 直接响应了项目“**Easy, fast, and cheap**”的核心目标。`OmniVoice` 是项目支持的多模态能力之一，优化其性能是提升全模态服务体验的关键。

- **功能新增：支持 `Hidream-I1-Full` 模型**
    - **变更点:** 新增了对 `Hidream-I1-Full` 模型的支持。
    - **项目关系:** 扩展了项目支持的模型生态，体现了“**omni-modality**”的愿景，即不断集成新的、多样化的模型，为用户提供更多选择。

- **Bug修复：修复并发批处理下的文本截断问题 (`MiMo-Audio`)**
    - **变更点:** 回滚了 `MiMo-Audio` 模块的 `local_sampler` 策略，恢复为贪婪采样，以解决在并发批处理场景下出现的文本截断问题。
    - **项目关系:** 保证了多模态服务在并发场景下的**稳定性和正确性**，这对于生产环境的部署至关重要。

- **Bug修复：对齐离线与在线推理**
    - **变更点:** 修复了离线推理和在线推理结果不一致的Bug。
    - **项目关系:** 确保了不同使用模式下（如脚本调用 vs API服务）的**结果一致性**，提升了项目的可靠性和用户体验。

- **其他：**
    - **配置/部署:** 为 `Fish Speech S2 Pro` 模型添加了2-GPU部署配置，降低了特定模型的高效部署门槛。
    - **Bug修复:** 修复了 `Helios` 中 `CacheDiT` 的CFG标志问题，属于特定模块的稳定性修复。
    - **CI:** 修复了邮件发送的Bug并跳过了邮件分发，属于内部基础设施维护。

### 3. 对项目的影响和潜在意义

- **性能提升:** `OmniVoice` 的优化将直接降低语音相关任务的推理延迟和成本，使“**cheap**”和“**fast**”的目标更进一步。
- **模型生态扩展:** 支持 `Hidream-I1-Full` 模型，吸引了图像生成领域的用户，扩大了项目的潜在用户群。
- **稳定性增强:** 修复并发批处理下的文本截断和离线/在线推理不一致问题，显著提升了项目在**高负载和复杂使用场景下的鲁棒性**，这对于一个服务型项目至关重要。
- **易用性提升:** 为 `Fish Speech S2 Pro` 提供现成的部署配置，降低了用户的使用门槛，符合“**Easy**”的定位。

### 4. 值得关注的技术点

- **Triton Kernel Fusion + CUDA Graph:** 这是当前大模型推理优化的前沿技术。Triton允许编写高性能的自定义内核，而CUDA Graph可以减少内核启动的开销。将两者结合用于 `OmniVoice`，表明项目团队在底层优化方面有深入的技术投入。
- **`MiMo-Audio` 的采样策略回滚:** 这个修复揭示了在多模态并发推理中，采样策略的选择对结果正确性有显著影响。从非贪婪策略回滚到贪婪策略，说明在保证稳定性和正确性方面，有时需要牺牲一定的多样性。
- **离线与在线推理对齐:** 这是一个基础但重要的问题。通常在线服务会引入额外的优化（如动态批处理、KV Cache管理等），可能导致与离线推理结果有微小差异。修复此问题表明项目对**结果可复现性**有高要求。

### 5. 基于项目背景，这些提交如何影响项目发展

- **巩固“Fast”和“Cheap”的定位:** 对 `OmniVoice` 的性能优化是直接强化项目核心竞争力的举措。在竞争激烈的模型服务市场中，更快的速度和更低的成本是吸引用户的关键。
- **践行“Omni-modality”的承诺:** 新增 `Hidream-I1-Full` 模型支持，表明项目并非只停留在文本或语音，而是持续向**全模态**（文本、语音、图像、视频等）的目标迈进。这有助于构建一个统一的、一站式的多模态模型服务平台。
- **提升生产环境的成熟度:** 多个Bug修复，特别是针对并发和结果一致性的修复，表明项目正在从“能用”向“**好用**”和“**可靠**”的阶段过渡。这对于吸引企业级用户至关重要。
- **降低用户门槛:** 提供现成的部署配置（Recipe）和修复易用性问题，使得非核心开发者也能更容易地部署和使用复杂的多模态模型，这有助于扩大社区和用户基础。

**总结:** 昨日的更新是一次典型的“**性能优化 + 功能扩展 + 稳定性加固**”的组合拳。项目在追求极致性能的同时，也在积极扩展模型生态并解决实际部署中的痛点，整体上朝着一个更强大、更易用、更可靠

## 详细提交记录

### [e7644da](https://github.com/vllm-project/vllm-omni/commit/e7644daa7f45610665f33d85682ba24014186698)

- **作者**: univa-HARRY
- **时间**: 2026-05-22T13:12:47Z
- **提交信息**: [Perf] [OmniVoice]  Triton kernel fusion + CUDA Graph acceleration (#3336)

Signed-off-by: univa-HARRY <harry@univa.co.kr>
Signed-off-by: Harry <harry@univa.co.kr>
Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [d714b4c](https://github.com/vllm-project/vllm-omni/commit/d714b4ce0496928ac2cbd51ca0b4ecb6df8dbee2)

- **作者**: Yueqian Lin
- **时间**: 2026-05-22T12:14:03Z
- **提交信息**: [Recipe] Add Fish Speech S2 Pro 2-GPU deploy profile (#3323)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [23e2433](https://github.com/vllm-project/vllm-omni/commit/23e243378f907ebf0ce0e52a694202d36219b9a1)

- **作者**: Alex Brooks
- **时间**: 2026-05-22T11:56:41Z
- **提交信息**: [Bugfix] Set separate CFG flag in Helios for CacheDiT (#3756)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [5799d85](https://github.com/vllm-project/vllm-omni/commit/5799d85a51679cca2bacf2f28ea47121d01b2f41)

- **作者**: Jialong Liu
- **时间**: 2026-05-22T11:25:37Z
- **提交信息**: [Bugfix] Revert MiMo-Audio local_sampler to greedy to fix text truncation under concurrent batching (followup to #3686) (#3817)

Signed-off-by: Jialong Liu <88185941+Galleons2029@users.noreply.github.com>
Signed-off-by: Galleons2029 <Galleons777@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [89e389c](https://github.com/vllm-project/vllm-omni/commit/89e389cf37aa72c656386bb972fbcd585edb058e)

- **作者**: Alicia
- **时间**: 2026-05-22T09:29:45Z
- **提交信息**: [CI] Fix email bug & skip email distribution. (#3814)

Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>

### [90ed618](https://github.com/vllm-project/vllm-omni/commit/90ed618b5abb4fd68937402967c42bfa91d8e15d)

- **作者**: skf
- **时间**: 2026-05-22T08:08:04Z
- **提交信息**: [Bugfix] Align Offline and Online Inference (#3506)

### [28467dc](https://github.com/vllm-project/vllm-omni/commit/28467dc19a8c453105ce30c8e97537d2d265dd00)

- **作者**: ANHDY
- **时间**: 2026-05-22T07:23:03Z
- **提交信息**: [feature]: support Hidream-I1-Full model (#2572)

Signed-off-by: wangmengdi <160612767@qq.com>
Co-authored-by: wangmengdi <wangmengdi@cmss.chinamobile.com>

---
