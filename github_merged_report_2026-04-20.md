# GitHub Stars 合并报告 - 2026-04-20

**合并日期**: 2026-04-21
**监控日期**: 2026-04-20
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


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 1841
- **最后更新**: 2026-04-20T23:33:57Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Ting

## AI分析总结

根据提供的提交记录和README摘要，以下是针对昨日更新的分析总结：

### 1. 主要更新类型
- **功能新增**：为未迁移的模型添加了针对Transformers v5的防护机制。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：在模型模块中引入了`guard`功能，确保尚未适配Transformers v5的模型在升级后仍能正常运行或给出明确提示。
- **与项目方向的关系**：VeOmni旨在构建一个模型中心的分布式训练方案库（"Model-Centric Distributed Recipe Zoo"），支持多模态模型训练。此次更新强化了**库的兼容性与健壮性**，确保用户在不同版本的底层框架（如Transformers）下都能稳定使用，这符合项目作为基础设施对**可靠性和易用性**的核心要求。

### 3. 对项目的影响和潜在意义
- **直接影响**：降低了用户因升级Transformers到v5版本而导致现有模型代码崩溃的风险，提升了用户体验。
- **潜在意义**：
    - 体现了项目对**依赖管理**和**向后兼容性**的重视。
    - 为未来集成更多模型或推动用户向新版本迁移提供了平滑过渡的路径。

### 4. 值得关注的技术点
- **“防护”（Guard）机制的具体实现**：如何检测未迁移的模型？是抛出警告、自动降级处理，还是提供明确的错误信息？这反映了项目在框架兼容性层面的设计思路。
- **与Transformers v5的交互**：此次更新可能涉及对Transformers v5新特性或破坏性变更的适配，关注这些变化有助于理解大模型训练库的前沿发展。

### 5. 基于项目背景的提交影响分析
VeOmni的目标是**规模化（Scaling）多模态（Any Modality）模型训练**。此次提交虽看似是一个具体的兼容性修补，但至关重要：
- **保障训练流程的稳定性**：对于分布式训练配方库，训练过程的稳定性和可重复性是基础。此更新防止了因底层框架意外升级而中断训练，直接支持了项目“**可靠缩放**”的核心目标。
- **维护生态兼容性**：作为旨在广泛使用的“方案库”（Recipe Zoo），必须与主流框架（如Transformers）的演进保持同步。此举显示了项目积极维护生态健康，有助于吸引和维护更广泛的用户与贡献者社区。
- **聚焦模型中心化**：变更位于`[model]`模块，强调了对模型本身的关注和保护，这与项目“**模型中心**”（Model-Centric）的理念一致，确保训练配方围绕模型特性构建，不受底层变动过度干扰。

**总结**：本次更新是一次针对关键依赖升级的**预防性兼容性增强**，虽改动范围可能不大，但直击分布式训练库的稳定性痛点，体现了项目在追求前沿缩放技术的同时，对工程基础与用户体验的扎实关注。

## 详细提交记录

### [dca9336](https://github.com/ByteDance-Seed/VeOmni/commit/dca9336433451aa6f2e25f852a5d74e146ce3331)

- **作者**: Ting
- **时间**: 2026-04-20T18:20:41Z
- **提交信息**: [model] feat: guard unmigrated models against transformers v5 (#675)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Light Image Video Generation Inference Framework
- **语言**: Python
- **星标数**: 2200
- **最后更新**: 2026-04-20T22:18:59Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Yang Yong (雍洋)

## AI分析总结

根据提供的提交记录和README摘要，以下是对昨日更新的分析总结：

### 1. 主要更新类型
- **功能优化/更新**：两个提交均涉及对“neo++”相关配置和推理代码的更新，属于框架内部组件的功能迭代。

### 2. 关键变更点及其与项目整体方向的关系
- **更新neo++配置（#1027）**：调整了neo++模型的配置文件，可能涉及模型参数、推理设置或兼容性调整。
- **更新neo++推理代码（#1026）**：优化或修复了neo++模型的推理流程，可能提升推理效率或稳定性。
- **与项目方向的关系**：LightX2V定位为“轻量级视频生成推理框架”，这些更新直接服务于核心目标——**优化视频生成模型的推理性能与易用性**，体现了对关键模型组件（如neo++）的持续维护和性能打磨。

### 3. 对项目的影响和潜在意义
- **提升推理可靠性**：配置和推理代码的更新可能修复潜在问题，确保neo++模型在框架中稳定运行。
- **优化性能或兼容性**：可能进一步压缩推理延迟、提升吞吐量，或适配新的硬件/软件环境。
- **维护框架竞争力**：持续迭代核心组件有助于保持框架在轻量级视频生成领域的**技术前沿性**和实用性。

### 4. 值得关注的技术点
- **neo++模型集成**：neo++可能是框架支持的一种高效视频生成模型，其配置和推理优化反映了框架对**先进模型适配能力**的重视。
- **配置驱动的优化**：通过配置文件调整模型行为，体现了框架设计上对**灵活性和可配置性**的追求。
- **推理流程改进**：可能涉及计算图优化、内存管理或并行策略调整，直接影响**端到端推理效率**。

### 5. 基于项目背景的提交影响分析
- **强化核心定位**：README强调LightX2V是“轻量级”且专注于“推理”的框架。本次更新通过优化neo++组件的配置与推理，直接**巩固了框架在高效推理方面的核心优势**。
- **支持模型生态演进**：neo++作为集成模型之一，其更新说明项目紧跟模型技术发展，确保框架能够**兼容和发挥最新模型的最佳性能**。
- **提升开发者体验**：配置和推理代码的改进可能简化部署流程或提供更优的默认设置，**降低用户使用门槛**，促进框架的采用。

**总结**：昨日的更新是LightX2V框架针对其核心模型组件neo++的一次针对性优化，旨在提升推理性能和稳定性。这完全契合其作为轻量级视频生成推理框架的定位，通过持续优化底层组件来确保框架高效、可靠且易于使用，从而在快速发展的视频生成领域中保持竞争力。

## 详细提交记录

### [1b52cc1](https://github.com/ModelTC/LightX2V/commit/1b52cc19fd611e6cab9faf30bfe2d7abe05fb798)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-20T13:46:53Z
- **提交信息**: update neo++ cfg (#1027)

### [cc9087e](https://github.com/ModelTC/LightX2V/commit/cc9087edb71b3b53ed7104f47deaacafee9100d4)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-04-20T09:21:11Z
- **提交信息**: update neo++ infer (#1026)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2026
- **最后更新**: 2026-04-20T07:55:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5455
- **最后更新**: 2026-04-20T23:08:47Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 4
- **主要提交者**: xueweilnvidia, Brian K. Ryu, Allan Lin

## AI分析总结

根据对FlashInfer仓库昨日提交记录的分析，结合其作为**高性能GPU推理内核库**的项目定位（专注于为LLM推理提供优化的GPU内核），以下是总结：

### 1. 主要更新类型
- **功能新增**：新增针对SM120/SM121架构的MoE（混合专家）API、ReLU2激活支持、并行注意力框架、更快的TopK算法。
- **Bug修复**：扩展了b12x FP4 GEMM内核对SM121架构（如GB10/DGX Spark）的支持。
- **性能优化**：引入了针对小批量解码的MoE微内核、利用SM90+ CTA集群特性的非确定性TopK算法。
- **架构/框架扩展**：新增了支持分布式计算的并行注意力模块。

### 2. 关键变更点及其与项目方向的关系
| 变更点 | 与项目方向的关系 |
| :--- | :--- |
| **SM12x MoE API与微内核** | 紧跟最新硬件（Ada/Hopper架构），为**解码阶段**（特别是单token/小批量）提供极致优化，直接提升推理效率。 |
| **ReLU2激活支持** | 支持**Nemotron-Super**等非门控MoE模型，扩大库的模型兼容性，服务于更广泛的MoE模型部署。 |
| **并行注意力框架** | 引入**Ulysses**（头并行）和**Ring**（KV交换）策略，项目从单GPU优化迈向**多GPU分布式推理**，解决长序列/大模型的内存与计算瓶颈。 |
| **更快TopK算法** | 优化了自回归解码中的**关键操作**（采样前TopK），利用新硬件特性提升整体吞吐量。 |
| **SM121 FP4支持修复** | 确保最新消费级/工作站GPU能使用最优的FP4量化内核，扩大硬件覆盖范围。 |

### 3. 对项目的影响和潜在意义
- **性能边界拓展**：微内核和集群TopK针对**边缘情况**（极小批量、大词汇表）优化，补齐性能短板。
- **硬件生态扩展**：明确支持SM120/SM121，巩固了对**NVIDIA最新消费级与数据中心GPU**的领先支持。
- **架构现代化**：并行注意力框架为未来支持**万亿参数模型**和**超长上下文**的分布式推理奠定了基础。
- **模型生态扩展**：通过ReLU2支持，紧跟**Nemotron**等前沿MoE模型，提升库的行业实用性。

### 4. 值得关注的技术点
- **MoE微内核的优化策略**：使用Triton进行路由ID压缩预处理、`all_rows_unique`快速路径、基于硬件的MAC调优阶梯，体现了**针对特定负载的精细化内核设计**。
- **非确定性TopK算法**：利用SM90+的CTA集群特性，以**非确定性**和可能的全局内存溢出为代价换取速度，是硬件特性驱动的算法创新。
- **并行注意力的装饰器架构**：`@ulysses_wrapper`和`@ring_wrapper`的**可组合装饰器设计**，使并行策略与底层注意力内核解耦，扩展性极强。
- **编译时分支**：在MoE内核中通过`cutlass.const_expr`实现`is_gated`的编译时分支，为不同激活函数生成最优内核，减少运行时开销。

### 5. 基于项目背景的提交影响分析
FlashInfer的核心目标是**为LLM推理提供性能最高的GPU内核**。昨日的更新集体指向三个战略方向：

1.  **纵向深化（单GPU性能）**：
    - MoE微内核和更快TopK直接优化了**解码延迟**的关键路径。
    - 支持新硬件（SM12x）和新模型（Nemotron-Super），确保在**最新软硬件栈**上保持性能领先。

2.  **横向扩展（分布式推理）**：
    - 并行注意力模块是**里程碑式**的更新，标志着项目从单GPU内核库向**分布式推理框架**演进，以应对模型规模不断增长的根本挑战。

3.  **生态巩固（兼容性与可用性）**：
    - 修复SM121支持，完善硬件覆盖。
    - 清晰的API分离（SM100 vs SM120）和CUDA Graph兼容的Wrapper，提升了**开发者体验和集成便利性**。

**总结**：昨日的提交不仅包含了持续的**单GPU性能挖潜**，更重要的是开启了**支持大规模分布式推理**的新篇章。这表明FlashInfer正积极地从“一个优秀的GPU内核集合”向“一个完整的**高性能推理运行时**”演进，以应对下一代LLM部署的挑战。

## 详细提交记录

### [8a9970b](https://github.com/flashinfer-ai/flashinfer/commit/8a9970b45a1e5bddace1f9d26b1b7a07a77ba504)

- **作者**: Brian K. Ryu
- **时间**: 2026-04-20T21:41:44Z
- **提交信息**: feat: Add b12x_fused_moe / B12xMoEWrapper SM120 APIs with micro kernel and ReLU2 (#3080)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

### Summary

 New SM120/SM121 MoE APIs (`b12x_fused_moe`, `B12xMoEWrapper`) with: 
- **Micro kernel** for tiny decode batches (≤20-40 routed rows) on
SM120/SM121, with Triton routing compaction pre-pass and MAC tuning
ladder
- **ReLU2 activation** (`max(0,x)²`) for non-gated MoE (Nemotron-Super)
across all three SM120 kernel backends (micro, static, dynamic)
- **Benchmark ReLU2 support** for both `cutlass_fused_moe` and
`cute_dsl_fp4_block_scale_moe` routines, with corrected TFLOPS/bandwidth
calculations for non-gated activations
- Clean API separation: SM120 uses `b12x_fused_moe`, SM100 keeps
`cute_dsl_fused_moe_nvfp4`

### API separation
| GPU | Functional API | Wrapper API |
|-----|---------------|-------------|  
| SM100/SM103 | `cute_dsl_fused_moe_nvfp4` (FP4 input) |
`CuteDslMoEWrapper` |
| SM120/SM121 | `b12x_fused_moe` (bf16 input) | `B12xMoEWrapper` |
The SM100 APIs (`cute_dsl_fused_moe_nvfp4`, `CuteDslMoEWrapper`) are
restored to SM100-only scope — no SM120 dispatch, no `activation_type`
parameter.

### Micro kernel

Ported from b12x. Selected automatically when `routed_rows ≤ 20`
(top_k=1) or `≤ 40` (top_k>1). Key optimizations vs the static kernel:
- **Triton compact pre-pass**: remaps global expert IDs to dense local
indices, eliminating CAS-based expert discovery inside the kernel
- **`all_rows_unique` fast path**: when `num_tokens=1` and every expert
is unique, skips atomic row counting and uses O(1) work-tile assignment
- **MAC tuning ladder**: per-routed-row optimal cluster counts from b12x
decode profiling, capped against hardware SM count to prevent deadlocks

### ReLU2 activation
Added `activation` parameter (`"silu"` default, `"relu2"`) to all SM120
kernel classes via `self.is_gated` compile-time branching
(`cutlass.const_expr`):
- **Storage**: `StorageGated` (3 pipelines, gate+up buffers) vs
`StorageRelu2` (2 pipelines, single FC1 buffer)
- **FC1**: dual GEMM (gate+up) for SiLU vs single GEMM for ReLU2
- **Activation**: `silu(gate) * up` vs `relu(x)²`
- **DMA**: up-projection TMA loads eliminated for ReLU2
Exposed through `activation_type` parameter on `CuteDslMoEWrapper` and
`cute_dsl_fused_moe_nvfp4` APIs.

### API usage

#### Functional
```python                                                                               
from flashinfer import b12x_fused_moe  

output = b12x_fused_moe(
    x=hidden_states_bf16,       # bf16 input (kernel fuses quantization)                                                                          
    w1_weight=w1_fp4, w1_weight_sf=w1_sf, w1_alpha=w1_alpha,                                                                                      
    fc2_input_scale=fc2_scale,                                                                                                                    
    w2_weight=w2_fp4, w2_weight_sf=w2_sf, w2_alpha=w2_alpha,                                                                                      
    token_selected_experts=topk_ids,                                                                                                              
    token_final_scales=topk_weights,                                                                                                              
    num_experts=512, top_k=22,                                                                                                                    
    activation="relu2",  # or "silu" (default)                                                                                                    
)                                                                                                                                                 
```

### Wrapper (CUDA graph compatible)
```python                              
from flashinfer import B12xMoEWrapper

moe = B12xMoEWrapper(                                                                                                                             
    num_experts=512, top_k=22,
    hidden_size=1024, intermediate_size=2688,                                                                                                     
    use_cuda_graph=True, activation="relu2",                                            
)                                                                                                                                                 
output = moe.run(x=hidden_states_bf16, ...)
```                               

#### Example micro benchmarks

```
# b12x cute dsl MoE for 1-token Nemotron 3 Super Size
python benchmarks/flashinfer_benchmark.py --routine cute_dsl_fp4_block_scale_moe --activation-type Relu2 --num_tokens 1 --hidden_size 1024 --intermediate_size 2688 --num_experts 512 --top_k 22 --use_cuda_events --num_iters 50
# Equivalent cutlass_fused_moe benchmark
python benchmarks/flashinfer_benchmark.py --routine cutlass_fused_moe --cutlass_variant nvfp4 --activation-type Relu2 --num_tokens 1 --hidden_size 1024 --intermediate_size 2688 --num_experts 512 --top_k 22 --quantized_input --use_cuda_events --num_iters 50
```

## 🔍 Related Issues

<!-- Link any related issues here -->

#3013

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

* **New Features**
* Non‑gated ReLU2 activation and dual gated/non‑gated FC1 layouts for
MoE; activation selectable at runtime.
* New micro‑kernel backend plus routing‑ID compaction for improved
single‑token/small‑batch performance.
* SM12x (b12x) fused‑MoE functional API and CUDA‑graph‑friendly wrapper
exported for SM12x workflows; runtime maps activations to kernel
implementations.
  * CuTe‑DSL helpers added to support ReLU2 + FP4 quantization.

* **Tests**
* End‑to‑end tests for ReLU2, gated vs non‑gated flows, micro‑kernel
paths, CUDA graph replay, and FP4 numerical agreement.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [44a2672](https://github.com/flashinfer-ai/flashinfer/commit/44a2672a4f937f5db1fa50f7344b1839d2b48038)

- **作者**: Allan Lin
- **时间**: 2026-04-20T21:07:52Z
- **提交信息**: [feat] Faster topk algorithm (#3009)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR implements a faster topk algorithm that uses sm90+ CTA clusters
feature. This is a non-deterministic algorithm, but does not drop
indices and instead overflows to global memory. Benchmark results show
that it's faster than both the multi-cta topk algorithm and the
filtering algorithm overall. The cases it's slower is when the overflow
happens too much.
Note: Speedup is speedup of flashinfer vs torch, while Speedup Clusters
vs. Default is speed up of this kernel over flashinfer.
```
====================================================================================================
top_k: Basic radix-based top-k selection (dtype=FP32, deterministic=False, pattern=random)
NOTE: default top-k sweep includes two extra large-batch/long-vocab stress cases beyond the original grid
====================================================================================================
 batch    seq_len      k |   FlashInfer   torch.topk    Speedup     Clusters  Speedup Clusters vs. Default
-------------------------------------------------------------------------------------------------------------------
     1        256    256 |         4.42us      20.64us      4.67x       1.50us                         2.94x
     1        512    256 |         5.79us      22.11us      3.82x       6.18us                         0.94x
     1        512    512 |         5.38us      21.28us      3.96x       1.54us                         3.50x
     1       1024    256 |        10.05us      27.68us      2.75x       6.40us                         1.57x
     1       1024    512 |         6.56us      24.51us      3.74x       6.40us                         1.02x
     1       1024   1024 |         5.12us      25.38us      4.96x       1.60us                         3.20x
     1       2048    256 |        10.08us      31.17us      3.09x       7.10us                         1.42x
     1       2048    512 |        11.01us      31.94us      2.90x       7.20us                         1.53x
     1       2048   1024 |         9.34us      32.03us      3.43x       7.07us                         1.32x
     1       2048   2048 |         5.79us      27.26us      4.71x       1.76us                         3.29x
     1       4096    256 |         9.12us      36.06us      3.95x       7.30us                         1.25x
     1       4096    512 |        11.42us      41.70us      3.65x       7.39us                         1.55x
     1       4096   1024 |        11.52us      41.15us      3.57x       7.58us                         1.52x
     1       4096   2048 |        10.22us      32.45us      3.17x       7.30us                         1.40x
     1       4096   4096 |         7.17us      35.78us      4.99x       2.02us                         3.56x
     1      16384    256 |        12.83us      78.53us      6.12x      11.49us                         1.12x
     1      16384    512 |        14.98us      89.09us      5.95x      12.24us                         1.22x
     1      16384   1024 |        15.95us      80.99us      5.08x      12.26us                         1.30x
     1      16384   2048 |        17.50us      93.33us      5.33x      12.51us                         1.40x
     1      16384   4096 |        21.28us      84.70us      3.98x      12.80us                         1.66x
     1      65536    256 |        33.44us      94.88us      2.84x      12.48us                         2.68x
     1      65536    512 |        34.24us      92.26us      2.69x      12.35us                         2.77x
     1      65536   1024 |        34.75us      91.52us      2.63x      12.42us                         2.80x
     1      65536   2048 |        36.58us      91.87us      2.51x      13.73us                         2.66x
     1      65536   4096 |        37.98us      92.03us      2.42x      13.92us                         2.73x
     1     131072    256 |        39.10us      99.81us      2.55x      14.69us                         2.66x
     1     131072    512 |        40.26us      98.13us      2.44x      14.72us                         2.73x
     1     131072   1024 |        39.81us      99.92us      2.51x      14.88us                         2.68x
     1     131072   2048 |        41.94us     101.50us      2.42x      14.98us                         2.80x
     1     131072   4096 |        43.62us     103.04us      2.36x      18.40us                         2.37x
     1     262144    256 |        43.46us     116.40us      2.68x      19.26us                         2.26x
     1     262144    512 |        44.46us     115.49us      2.60x      19.36us                         2.30x
     1     262144   1024 |        44.35us     114.14us      2.57x      19.34us                         2.29x
     1     262144   2048 |        45.89us     115.36us      2.51x      19.52us                         2.35x
     1     262144   4096 |        46.78us     116.83us      2.50x      19.71us                         2.37x
     1     524288    256 |        45.60us     152.27us      3.34x      28.00us                         1.63x
     1     524288    512 |        46.91us     146.75us      3.13x      28.19us                         1.66x
     1     524288   1024 |        46.34us     151.39us      3.27x      28.35us                         1.63x
     1     524288   2048 |        47.14us     149.55us      3.17x      28.58us                         1.65x
     1     524288   4096 |        47.76us     151.58us      3.17x      28.54us                         1.67x
    16        256    256 |         5.95us      20.99us      3.53x       1.50us                         3.96x
    16        512    256 |         9.98us      23.07us      2.31x       6.43us                         1.55x
    16        512    512 |         5.60us      22.82us      4.07x       1.50us                         3.72x
    16       1024    256 |        11.30us      28.86us      2.56x       6.59us                         1.71x
    16       1024    512 |         9.12us      26.37us      2.89x       6.62us                         1.38x
    16       1024   1024 |         6.21us      27.30us      4.40x       1.60us                         3.88x
    16       2048    256 |        11.65us      31.87us      2.74x       7.23us                         1.61x
    16       2048    512 |        10.62us      32.64us      3.07x       7.36us                         1.44x
    16       2048   1024 |        10.08us      30.27us      3.00x       7.30us                         1.38x
    16       2048   2048 |         6.75us      30.46us      4.51x       1.76us                         3.84x
    16       4096    256 |        11.55us      43.04us      3.73x       7.39us                         1.56x
    16       4096    512 |        12.26us      44.70us      3.65x       7.49us                         1.64x
    16       4096   1024 |        12.06us      42.21us      3.50x       7.63us                         1.58x
    16       4096   2048 |        12.10us      38.69us      3.20x       7.65us                         1.58x
    16       4096   4096 |         7.84us      41.50us      5.29x       2.02us                         3.89x
    16      16384    256 |        14.98us      92.72us      6.19x      14.18us                         1.06x
    16      16384    512 |        15.17us      96.22us      6.34x      15.38us                         0.99x
    16      16384   1024 |        17.73us      98.88us      5.58x      15.33us                         1.16x
    16      16384   2048 |        18.18us      98.50us      5.42x      15.81us                         1.15x
    16      16384   4096 |        21.63us     107.09us      4.95x      16.29us                         1.33x
    16      65536    256 |        27.73us     104.93us      3.78x      16.13us                         1.72x
    16      65536    512 |        32.16us     103.86us      3.23x      16.35us                         1.97x
    16      65536   1024 |        32.58us     103.84us      3.19x      16.16us                         2.02x
    16      65536   2048 |        35.90us     107.92us      3.01x      19.20us                         1.87x
    16      65536   4096 |        42.08us     110.78us      2.63x      19.62us                         2.15x
    16     131072    256 |        43.92us     115.10us      2.62x      20.96us                         2.10x
    16     131072    512 |        43.46us     112.86us      2.60x      21.23us                         2.05x
    16     131072   1024 |        53.47us     115.94us      2.17x      21.25us                         2.52x
    16     131072   2048 |        54.43us     116.69us      2.14x      21.25us                         2.56x
    16     131072   4096 |        48.22us     122.78us      2.55x      26.88us                         1.79x
    16     262144    256 |        49.12us     136.64us      2.78x      27.54us                         1.78x
    16     262144    512 |        49.33us     136.82us      2.77x      28.03us                         1.76x
    16     262144   1024 |        49.46us     138.70us      2.80x      28.03us                         1.76x
    16     262144   2048 |        50.59us     139.33us      2.75x      28.29us                         1.79x
    16     262144   4096 |        51.55us     142.85us      2.77x      28.77us                         1.79x
    16     524288    256 |        89.95us     181.86us      2.02x      42.38us                         2.12x
    16     524288    512 |        90.51us     178.05us      1.97x      43.17us                         2.10x
    16     524288   1024 |        90.75us     179.14us      1.97x      42.72us                         2.12x
    16     524288   2048 |        91.73us     182.66us      1.99x      43.39us                         2.11x
    16     524288   4096 |        93.60us     185.39us      1.98x      43.15us                         2.17x
    64        256    256 |         6.37us      22.05us      3.46x       1.50us                         4.24x
    64        512    256 |        10.53us      23.68us      2.25x       6.53us                         1.61x
    64        512    512 |         5.50us      23.55us      4.28x       1.54us                         3.58x
    64       1024    256 |        12.03us      31.09us      2.58x       6.70us                         1.79x
    64       1024    512 |        10.62us      27.30us      2.57x       6.77us                         1.57x
    64       1024   1024 |         6.66us      26.91us      4.04x       1.63us                         4.08x
    64       2048    256 |        11.34us      35.07us      3.09x       7.39us                         1.53x
    64       2048    512 |        10.88us      34.18us      3.14x       7.42us                         1.47x
    64       2048   1024 |        11.20us      32.42us      2.89x       7.52us                         1.49x
    64       2048   2048 |         7.39us      32.06us      4.34x       1.79us                         4.12x
    64       4096    256 |        12.67us      43.23us      3.41x       7.68us                         1.65x
    64       4096    512 |        11.71us      43.14us      3.68x       7.71us                         1.52x
    64       4096   1024 |        12.13us      46.66us      3.85x       7.87us                         1.54x
    64       4096   2048 |        11.97us      40.22us      3.36x       7.78us                         1.54x
    64       4096   4096 |         8.64us      40.93us      4.74x       2.08us                         4.15x
    64      16384    256 |        15.42us      98.59us      6.39x      14.11us                         1.09x
    64      16384    512 |        15.39us     101.60us      6.60x      15.42us                         1.00x
    64      16384   1024 |        17.98us      99.87us      5.55x      15.65us                         1.15x
    64      16384   2048 |        19.14us     102.14us      5.34x      15.97us                         1.20x
    64      16384   4096 |        22.37us     104.22us      4.66x      16.46us                         1.36x
    64      65536    256 |        27.97us     135.71us      4.85x      20.93us                         1.34x
    64      65536    512 |        32.85us     136.61us      4.16x      21.12us                         1.56x
    64      65536   1024 |        34.08us     135.14us      3.97x      21.22us                         1.61x
    64      65536   2048 |        36.93us     139.07us      3.77x      27.04us                         1.37x
    64      65536   4096 |        43.30us     141.86us      3.28x      28.35us                         1.53x
    64     131072    256 |        44.80us     178.22us      3.98x      29.41us                         1.52x
    64     131072    512 |        44.53us     174.94us      3.93x      29.57us                         1.51x
    64     131072   1024 |        54.59us     174.56us      3.20x      29.70us                         1.84x
    64     131072   2048 |        55.46us     177.73us      3.20x      30.24us                         1.83x
    64     131072   4096 |        90.98us     181.47us      1.99x      44.93us                         2.02x
    64     262144    256 |        75.17us     240.90us      3.20x      47.73us                         1.57x
    64     262144    512 |        80.53us     239.86us      2.98x      47.92us                         1.68x
    64     262144   1024 |        81.97us     241.82us      2.95x      48.13us                         1.70x
    64     262144   2048 |        98.64us     241.71us      2.45x      48.58us                         2.03x
    64     262144   4096 |       143.36us     244.83us      1.71x      49.95us                         2.87x
    64     524288    256 |       162.29us     488.82us      3.01x      84.50us                         1.92x
    64     524288    512 |       161.41us     488.70us      3.03x      84.70us                         1.91x
    64     524288   1024 |       175.39us     491.07us      2.80x      85.01us                         2.06x
    64     524288   2048 |       175.98us     494.22us      2.81x      85.89us                         2.05x
    64     524288   4096 |       227.90us     494.98us      2.17x      88.62us                         2.57x
   256        256    256 |         7.04us      23.15us      3.29x       1.82us                         3.86x
   256        512    256 |        15.12us      27.04us      1.79x       7.87us                         1.92x
   256        512    512 |         7.15us      26.37us      3.69x       1.89us                         3.79x
   256       1024    256 |        17.66us      40.45us      2.29x       8.26us                         2.14x
   256       1024    512 |        15.65us      37.55us      2.40x       8.32us                         1.88x
   256       1024   1024 |         7.58us      38.83us      5.12x       2.14us                         3.54x
   256       2048    256 |        18.66us      49.60us      2.66x       9.34us                         2.00x
   256       2048    512 |        18.66us      51.17us      2.74x       9.47us                         1.97x
   256       2048   1024 |        17.09us      46.14us      2.70x       9.66us                         1.77x
   256       2048   2048 |         8.99us      47.52us      5.28x       2.37us                         3.80x
   256       4096    256 |        19.23us      99.17us      5.16x      10.72us                         1.79x
   256       4096    512 |        19.97us      99.41us      4.98x      10.91us                         1.83x
   256       4096   1024 |        20.58us     102.10us      4.96x      11.28us                         1.82x
   256       4096   2048 |        18.34us     103.58us      5.65x      11.07us                         1.66x
   256       4096   4096 |        12.54us     114.22us      9.11x       2.82us                         4.45x
   256      16384    256 |        28.42us     131.98us      4.64x      16.19us                         1.75x
   256      16384    512 |        29.50us     135.30us      4.59x      22.11us                         1.33x
   256      16384   1024 |        31.34us     136.93us      4.37x      23.23us                         1.35x
   256      16384   2048 |        34.24us     138.99us      4.06x      24.26us                         1.41x
   256      16384   4096 |        40.64us     149.52us      3.68x      25.12us                         1.62x
   256      65536    256 |        53.92us     240.27us      4.46x      42.66us                         1.26x
   256      65536    512 |        64.16us     243.09us      3.79x      43.22us                         1.48x
   256      65536   1024 |        64.93us     243.83us      3.76x      43.97us                         1.48x
   256      65536   2048 |        71.01us     250.61us      3.53x      76.10us                         0.93x
   256      65536   4096 |       150.53us     260.10us      1.73x      83.87us                         1.79x
   256     131072    256 |        92.15us     487.68us      5.29x      81.01us                         1.14x
   256     131072    512 |        92.16us     488.58us      5.30x      81.44us                         1.13x
   256     131072   1024 |       111.23us     493.68us      4.44x      82.45us                         1.35x
   256     131072   2048 |       112.56us     495.41us      4.40x      84.58us                         1.33x
   256     131072   4096 |       259.01us     509.48us      1.97x     161.81us                         1.60x
   256     262144    256 |       178.59us     881.03us      4.93x     155.81us                         1.15x
   256     262144    512 |       192.08us     879.04us      4.58x     156.94us                         1.22x
   256     262144   1024 |       192.74us     879.60us      4.56x     158.18us                         1.22x
   256     262144   2048 |       230.40us     885.49us      3.84x     160.82us                         1.43x
   256     262144   4096 |       411.46us     898.68us      2.18x     170.59us                         2.41x
   256     524288    256 |       327.39us    1542.01us      4.71x     299.43us                         1.09x
   256     524288    512 |       327.95us    1542.65us      4.70x     300.77us                         1.09x
   256     524288   1024 |       355.35us    1544.52us      4.35x     303.06us                         1.17x
   256     524288   2048 |       357.19us    1549.56us      4.34x     305.75us                         1.17x
   256     524288   4096 |       824.29us    1568.89us      1.90x     316.91us                         2.60x
  2048     131072   1024 |       703.20us    3012.43us      4.28x     470.11us                         1.50x
  4096     200000   1024 |      1994.76us    8891.66us      4.46x    1383.16us                         1.44x

====================================================================================================
dsa_topk: DeepSeek DSA-like indexer top-k workload (dtype=FP32, deterministic=False, dsa_pattern=dsa_relu, k=2048)
====================================================================================================
                    case     rows    seq_len      k |   FlashInfer   torch.topk    Speedup     Clusters  Speedup Clusters vs. Default
---------------------------------------------------------------------------------------------------------------------------------
      decode_b1_q1_l128k        1     131072   2048 |      42.59us      98.62us      2.32x      14.98us                         2.84x
       decode_b8_q1_l64k        8      65536   2048 |      37.01us      97.70us      2.64x      14.59us                         2.54x
     decode_b32_q1_l128k       32     131072   2048 |      56.13us     135.20us      2.41x      23.01us                         2.44x
   prefill_b1_q128_l128k      128     131072   2048 |      62.02us     241.52us      3.89x      49.18us                         1.26x

====================================================================================================
top_k_page_table_transform: Fused top-k + page table gather (dtype=FP32, deterministic=False, pattern=random)
====================================================================================================
 batch    seq_len      k |   FlashInfer     Clusters  Speedup Clusters vs. Default
-------------------------------------------------------------------------------------------------------------
     1        256    256 |       2.85us       2.43us                         1.17x
     1        512    256 |       4.72us       7.04us                         0.67x
     1        512    512 |       2.94us       2.56us                         1.15x
     1       1024    256 |       7.04us       7.01us                         1.00x
     1       1024    512 |       4.45us       6.77us                         0.66x
     1       1024   1024 |       2.56us       2.24us                         1.14x
     1       2048    256 |       8.64us       7.92us                         1.09x
     1       2048    512 |       7.38us       7.87us                         0.94x
     1       2048   1024 |       7.12us       7.71us                         0.92x
     1       2048   2048 |       3.26us       2.91us                         1.12x
     1       4096    256 |       8.93us       8.26us                         1.08x
     1       4096    512 |       9.06us       8.35us                         1.08x
     1       4096   1024 |       7.95us       8.32us                         0.96x
     1       4096   2048 |       7.65us       8.00us                         0.96x
     1       4096   4096 |       4.16us       2.62us                         1.59x
     1      16384    256 |      12.26us      12.70us                         0.96x
     1      16384    512 |      13.10us      13.26us                         0.99x
     1      16384   1024 |      14.46us      13.50us                         1.07x
     1      16384   2048 |      15.46us      13.54us                         1.14x
     1      16384   4096 |      20.35us      13.73us                         1.48x
     1      65536    256 |      30.30us      13.07us                         2.32x
     1      65536    512 |      31.14us      13.12us                         2.37x
     1      65536   1024 |      31.58us      13.18us                         2.40x
     1      65536   2048 |      33.50us      14.62us                         2.29x
     1      65536   4096 |      35.33us      14.82us                         2.38x
     1     131072    256 |      35.42us      15.07us                         2.35x
     1     131072    512 |      35.87us      15.17us                         2.36x
     1     131072   1024 |      36.45us      15.33us                         2.38x
     1     131072   2048 |      38.05us      15.30us                         2.49x
     1     131072   4096 |      41.22us      19.17us                         2.15x
     1     262144    256 |      40.08us      19.78us                         2.03x
     1     262144    512 |      40.58us      20.32us                         2.00x
     1     262144   1024 |      41.15us      19.81us                         2.08x
     1     262144   2048 |      42.82us      20.02us                         2.14x
     1     262144   4096 |      45.06us      20.22us                         2.23x
     1     524288    256 |      42.75us      28.21us                         1.52x
     1     524288    512 |      42.82us      28.29us                         1.51x
     1     524288   1024 |      43.10us      28.26us                         1.53x
     1     524288   2048 |      43.71us      28.38us                         1.54x
     1     524288   4096 |      45.12us      29.31us                         1.54x
    16        256    256 |       2.75us       2.37us                         1.16x
    16        512    256 |       7.71us       7.17us                         1.08x
    16        512    512 |       2.85us       2.46us                         1.16x
    16       1024    256 |       8.19us       7.30us                         1.12x
    16       1024    512 |       6.94us       7.39us                         0.94x
    16       1024   1024 |       2.82us       2.56us                         1.10x
    16       2048    256 |       8.70us       8.08us                         1.08x
    16       2048    512 |       8.67us       8.19us                         1.06x
    16       2048   1024 |       8.19us       8.06us                         1.02x
    16       2048   2048 |       3.52us       3.20us                         1.10x
    16       4096    256 |       9.05us       8.45us                         1.07x
    16       4096    512 |      10.14us       8.50us                         1.19x
    16       4096   1024 |       9.31us       8.61us                         1.08x
    16       4096   2048 |       8.74us       8.35us                         1.05x
    16       4096   4096 |       4.50us       2.82us                         1.60x
    16      16384    256 |      12.74us      15.04us                         0.85x
    16      16384    512 |      13.38us      16.83us                         0.79x
    16      16384   1024 |      14.30us      16.80us                         0.85x
    16      16384   2048 |      16.26us      17.17us                         0.95x
    16      16384   4096 |      20.51us      17.52us                         1.17x
    16      65536    256 |      24.69us      16.86us                         1.46x
    16      65536    512 |      29.82us      16.80us                         1.78x
    16      65536   1024 |      30.69us      17.18us                         1.79x
    16      65536   2048 |      34.14us      20.29us                         1.68x
    16      65536   4096 |      39.68us      20.83us                         1.90x
    16     131072    256 |      40.78us      21.63us                         1.89x
    16     131072    512 |      41.25us      21.63us                         1.91x
    16     131072   1024 |      51.58us      21.66us                         2.38x
    16     131072   2048 |      52.78us      22.02us                         2.40x
    16     131072   4096 |      45.87us      27.94us                         1.64x
    16     262144    256 |      45.34us      28.64us                         1.58x
    16     262144    512 |      45.92us      28.70us                         1.60x
    16     262144   1024 |      46.34us      29.04us                         1.60x
    16     262144   2048 |      47.84us      29.60us                         1.62x
    16     262144   4096 |      49.70us      30.30us                         1.64x
    16     524288    256 |      86.62us      43.87us                         1.97x
    16     524288    512 |      87.30us      44.13us                         1.98x
    16     524288   1024 |      87.68us      44.35us                         1.98x
    16     524288   2048 |      89.30us      44.74us                         2.00x
    16     524288   4096 |      92.38us      45.36us                         2.04x
    64        256    256 |       2.85us       2.43us                         1.17x
    64        512    256 |       7.78us       7.39us                         1.05x
    64        512    512 |       2.91us       2.56us                         1.14x
    64       1024    256 |       8.58us       7.58us                         1.13x
    64       1024    512 |       8.06us       7.60us                         1.06x
    64       1024   1024 |       3.01us       2.66us                         1.13x
    64       2048    256 |       9.47us       8.38us                         1.13x
    64       2048    512 |       8.83us       8.35us                         1.06x
    64       2048   1024 |       8.29us       8.35us                         0.99x
    64       2048   2048 |       3.71us       3.33us                         1.12x
    64       4096    256 |       9.41us       8.74us                         1.08x
    64       4096    512 |       9.58us       8.86us                         1.08x
    64       4096   1024 |      10.34us       8.93us                         1.16x
    64       4096   2048 |       9.09us       8.61us                         1.06x
    64       4096   4096 |       4.70us       3.04us                         1.55x
    64      16384    256 |      13.06us      15.17us                         0.86x
    64      16384    512 |      13.86us      16.61us                         0.83x
    64      16384   1024 |      15.23us      16.80us                         0.91x
    64      16384   2048 |      16.45us      16.96us                         0.97x
    64      16384   4096 |      21.10us      17.44us                         1.21x
    64      65536    256 |      25.58us      21.89us                         1.17x
    64      65536    512 |      31.20us      22.02us                         1.42x
    64      65536   1024 |      31.87us      22.18us                         1.44x
    64      65536   2048 |      35.34us      28.45us                         1.24x
    64      65536   4096 |      41.31us      30.75us                         1.34x
    64     131072    256 |      42.14us      30.34us                         1.39x
    64     131072    512 |      42.80us      30.59us                         1.40x
    64     131072   1024 |      52.54us      30.85us                         1.70x
    64     131072   2048 |      54.40us      31.62us                         1.72x
    64     131072   4096 |      90.27us      49.18us                         1.84x
    64     262144    256 |      71.92us      48.66us                         1.48x
    64     262144    512 |      79.04us      48.56us                         1.63x
    64     262144   1024 |      79.22us      49.02us                         1.62x
    64     262144   2048 |      96.82us      49.54us                         1.95x
    64     262144   4096 |     146.72us      54.74us                         2.68x
    64     524288    256 |     158.80us      84.70us                         1.87x
    64     524288    512 |     158.82us      84.99us                         1.87x
    64     524288   1024 |     171.39us      85.76us                         2.00x
    64     524288   2048 |     172.91us      86.19us                         2.01x
    64     524288   4096 |     228.77us      90.02us                         2.54x
   256        256    256 |       3.74us       2.75us                         1.36x
   256        512    256 |      13.25us       8.72us                         1.52x
   256        512    512 |       3.81us       2.98us                         1.28x
   256       1024    256 |      15.84us       9.09us                         1.74x
   256       1024    512 |      13.47us       9.14us                         1.47x
   256       1024   1024 |       4.08us       3.36us                         1.21x
   256       2048    256 |      16.51us      10.29us                         1.60x
   256       2048    512 |      16.32us      10.37us                         1.57x
   256       2048   1024 |      14.53us      10.30us                         1.41x
   256       2048   2048 |       5.28us       3.97us                         1.33x
   256       4096    256 |      17.36us      11.82us                         1.47x
   256       4096    512 |      18.72us      11.97us                         1.56x
   256       4096   1024 |      18.43us      12.22us                         1.51x
   256       4096   2048 |      15.68us      11.42us                         1.37x
   256       4096   4096 |       7.52us       4.29us                         1.75x
   256      16384    256 |      26.72us      17.09us                         1.56x
   256      16384    512 |      28.35us      23.04us                         1.23x
   256      16384   1024 |      30.21us      23.97us                         1.26x
   256      16384   2048 |      33.22us      24.93us                         1.33x
   256      16384   4096 |      41.31us      26.30us                         1.57x
   256      65536    256 |      52.75us      43.46us                         1.21x
   256      65536    512 |      63.33us      44.13us                         1.44x
   256      65536   1024 |      66.08us      46.93us                         1.41x
   256      65536   2048 |      74.27us      78.90us                         0.94x
   256      65536   4096 |     152.87us      88.19us                         1.73x
   256     131072    256 |      89.89us      80.86us                         1.11x
   256     131072    512 |      90.99us      81.34us                         1.12x
   256     131072   1024 |     109.87us      82.70us                         1.33x
   256     131072   2048 |     114.05us      85.18us                         1.34x
   256     131072   4096 |     261.31us     162.07us                         1.61x
   256     262144    256 |     174.27us     154.00us                         1.13x
   256     262144    512 |     187.58us     154.53us                         1.21x
   256     262144   1024 |     189.57us     155.97us                         1.22x
   256     262144   2048 |     227.89us     158.94us                         1.43x
   256     262144   4096 |     422.98us     169.30us                         2.50x
   256     524288    256 |     322.55us     298.26us                         1.08x
   256     524288    512 |     323.62us     300.18us                         1.08x
   256     524288   1024 |     350.56us     302.34us                         1.16x
   256     524288   2048 |     354.67us     306.77us                         1.16x
   256     524288   4096 |     834.52us     316.07us                         2.64x

====================================================================================================
top_k_ragged_transform: Fused top-k + ragged index transform (dtype=FP32, deterministic=False, pattern=random)
====================================================================================================
 batch    seq_len      k |   FlashInfer     Clusters  Speedup Clusters vs. Default
-------------------------------------------------------------------------------------------------------------
     1        256    256 |       2.37us       1.76us                         1.35x
     1        512    256 |       3.58us       6.53us                         0.55x
     1        512    512 |       2.34us       1.82us                         1.28x
     1       1024    256 |       7.63us       6.94us                         1.10x
     1       1024    512 |       6.14us       6.88us                         0.89x
     1       1024   1024 |       2.75us       2.08us                         1.32x
     1       2048    256 |       6.72us       7.52us                         0.89x
     1       2048    512 |       7.97us       7.74us                         1.03x
     1       2048   1024 |       7.71us       7.68us                         1.00x
     1       2048   2048 |       2.85us       2.18us                         1.31x
     1       4096    256 |       8.22us       7.70us                         1.07x
     1       4096    512 |       7.23us       7.71us                         0.94x
     1       4096   1024 |       8.38us       7.86us                         1.07x
     1       4096   2048 |       6.83us       7.44us                         0.92x
     1       4096   4096 |       2.91us       2.30us                         1.26x
     1      16384    256 |      11.52us      11.87us                         0.97x
     1      16384    512 |      11.94us      12.51us                         0.95x
     1      16384   1024 |      12.74us      12.54us                         1.02x
     1      16384   2048 |      13.92us      12.51us                         1.11x
     1      16384   4096 |      17.50us      12.61us                         1.39x
     1      65536    256 |      30.88us      12.78us                         2.42x
     1      65536    512 |      31.14us      12.74us                         2.44x
     1      65536   1024 |      32.16us      12.74us                         2.53x
     1      65536   2048 |      33.07us      14.05us                         2.35x
     1      65536   4096 |      34.18us      14.21us                         2.41x
     1     131072    256 |      36.54us      14.94us                         2.45x
     1     131072    512 |      37.22us      14.91us                         2.50x
     1     131072   1024 |      37.41us      14.98us                         2.50x
     1     131072   2048 |      38.34us      14.98us                         2.56x
     1     131072   4096 |      39.84us      18.67us                         2.13x
     1     262144    256 |      41.28us      19.36us                         2.13x
     1     262144    512 |      41.68us      19.65us                         2.12x
     1     262144   1024 |      41.44us      19.55us                         2.12x
     1     262144   2048 |      42.88us      19.65us                         2.18x
     1     262144   4096 |      43.46us      19.49us                         2.23x
     1     524288    256 |      42.88us      28.00us                         1.53x
     1     524288    512 |      43.33us      27.97us                         1.55x
     1     524288   1024 |      43.49us      28.54us                         1.52x
     1     524288   2048 |      44.10us      28.46us                         1.55x
     1     524288   4096 |      44.13us      28.35us                         1.56x
    16        256    256 |       2.43us       1.86us                         1.31x
    16        512    256 |       6.42us       6.78us                         0.95x
    16        512    512 |       2.48us       1.92us                         1.29x
    16       1024    256 |       7.52us       6.85us                         1.10x
    16       1024    512 |       6.18us       7.01us                         0.88x
    16       1024   1024 |       2.43us       1.92us                         1.27x
    16       2048    256 |       7.87us       7.58us                         1.04x
    16       2048    512 |       7.90us       7.60us                         1.04x
    16       2048   1024 |       6.56us       7.65us                         0.86x
    16       2048   2048 |       2.53us       2.08us                         1.22x
    16       4096    256 |       8.16us       7.78us                         1.05x
    16       4096    512 |       8.35us       7.82us                         1.07x
    16       4096   1024 |       8.34us       8.00us                         1.04x
    16       4096   2048 |       7.97us       7.58us                         1.05x
    16       4096   4096 |       2.62us       2.21us                         1.19x
    16      16384    256 |      11.71us      14.37us                         0.82x
    16      16384    512 |      13.09us      15.65us                         0.84x
    16      16384   1024 |      13.12us      15.97us                         0.82x
    16      16384   2048 |      14.27us      15.84us                         0.90x
    16      16384   4096 |      17.60us      16.10us                         1.09x
    16      65536    256 |      23.79us      16.37us                         1.45x
    16      65536    512 |      28.91us      16.48us                         1.75x
    16      65536   1024 |      29.57us      16.74us                         1.77x
    16      65536   2048 |      32.03us      18.98us                         1.69x
    16      65536   4096 |      37.66us      19.46us                         1.94x
    16     131072    256 |      39.75us      20.67us                         1.92x
    16     131072    512 |      40.06us      20.80us                         1.93x
    16     131072   1024 |      49.31us      20.61us                         2.39x
    16     131072   2048 |      49.25us      20.48us                         2.40x
    16     131072   4096 |      43.62us      26.45us                         1.65x
    16     262144    256 |      45.54us      27.57us                         1.65x
    16     262144    512 |      45.63us      27.74us                         1.64x
    16     262144   1024 |      46.02us      27.65us                         1.66x
    16     262144   2048 |      46.43us      27.76us                         1.67x
    16     262144   4096 |      47.68us      28.23us                         1.69x
    16     524288    256 |      86.43us      42.54us                         2.03x
    16     524288    512 |      86.82us      42.75us                         2.03x
    16     524288   1024 |      87.07us      42.08us                         2.07x
    16     524288   2048 |      87.71us      42.38us                         2.07x
    16     524288   4096 |      89.17us      42.93us                         2.08x
    64        256    256 |       2.37us       1.79us                         1.32x
    64        512    256 |       7.46us       7.01us                         1.06x
    64        512    512 |       2.56us       1.95us                         1.31x
    64       1024    256 |       7.74us       7.14us                         1.09x
    64       1024    512 |       7.33us       7.10us                         1.03x
    64       1024   1024 |       2.53us       2.05us                         1.23x
    64       2048    256 |       8.00us       7.68us                         1.04x
    64       2048    512 |       8.03us       7.78us                         1.03x
    64       2048   1024 |       6.78us       7.71us                         0.88x
    64       2048   2048 |       2.59us       2.11us                         1.23x
    64       4096    256 |       9.20us       7.98us                         1.15x
    64       4096    512 |       8.54us       8.10us                         1.06x
    64       4096   1024 |       8.64us       8.13us                         1.06x
    64       4096   2048 |       8.29us       7.84us                         1.06x
    64       4096   4096 |       2.72us       2.27us                         1.20x
    64      16384    256 |      12.13us      14.11us                         0.86x
    64      16384    512 |      13.31us      15.36us                         0.87x
    64      16384   1024 |      14.27us      15.63us                         0.91x
    64      16384   2048 |      15.17us      15.74us                         0.96x
    64      16384   4096 |      18.10us      16.03us                         1.13x
    64      65536    256 |      25.06us      20.64us                         1.21x
    64      65536    512 |      29.25us      20.58us                         1.42x
    64      65536   1024 |      29.89us      20.67us                         1.45x
    64      65536   2048 |      32.94us      26.56us                         1.24x
    64      65536   4096 |      38.99us      27.26us                         1.43x
    64     131072    256 |      41.06us      28.88us                         1.42x
    64     131072    512 |      41.22us      28.99us                         1.42x
    64     131072   1024 |      50.37us      29.09us                         1.73x
    64     131072   2048 |      50.83us      29.22us                         1.74x
    64     131072   4096 |      86.02us      43.84us                         1.96x
    64     262144    256 |      70.35us      47.04us                         1.50x
    64     262144    512 |      76.61us      47.07us                         1.63x
    64     262144   1024 |      77.41us      47.26us                         1.64x
    64     262144   2048 |      93.22us      47.54us                         1.96x
    64     262144   4096 |     137.71us      47.97us                         2.87x
    64     524288    256 |     157.73us      83.46us                         1.89x
    64     524288    512 |     157.31us      83.46us                         1.88x
    64     524288   1024 |     169.62us      83.81us                         2.02x
    64     524288   2048 |     170.10us      84.21us                         2.02x
    64     524288   4096 |     222.91us      84.21us                         2.65x
   256        256    256 |       2.94us       2.22us                         1.32x
   256        512    256 |      12.10us       8.16us                         1.48x
   256        512    512 |       3.09us       2.27us                         1.36x
   256       1024    256 |      14.05us       8.67us                         1.62x
   256       1024    512 |      11.49us       8.67us                         1.32x
   256       1024   1024 |       3.39us       2.45us                         1.39x
   256       2048    256 |      15.84us       9.60us                         1.65x
   256       2048    512 |      14.88us       9.66us                         1.54x
   256       2048   1024 |      13.15us       9.76us                         1.35x
   256       2048   2048 |       3.74us       2.46us                         1.52x
   256       4096    256 |      16.48us      10.98us                         1.50x
   256       4096    512 |      16.16us      11.10us                         1.46x
   256       4096   1024 |      16.93us      11.33us                         1.49x
   256       4096   2048 |      14.26us      10.72us                         1.33x
   256       4096   4096 |       4.13us       2.66us                         1.55x
   256      16384    256 |      24.54us      16.35us                         1.50x
   256      16384    512 |      25.57us      22.05us                         1.16x
   256      16384   1024 |      27.52us      22.66us                         1.21x
   256      16384   2048 |      29.82us      23.07us                         1.29x
   256      16384   4096 |      35.14us      23.14us                         1.52x
   256      65536    256 |      50.02us      42.40us                         1.18x
   256      65536    512 |      59.97us      42.64us                         1.41x
   256      65536   1024 |      60.35us      43.10us                         1.40x
   256      65536   2048 |      65.46us      72.35us                         0.90x
   256      65536   4096 |     144.24us      74.11us                         1.95x
   256     131072    256 |      87.68us      79.49us                         1.10x
   256     131072    512 |      88.13us      79.78us                         1.10x
   256     131072   1024 |     106.06us      80.19us                         1.32x
   256     131072   2048 |     106.21us      80.48us                         1.32x
   256     131072   4096 |     250.90us     143.89us                         1.74x
   256     262144    256 |     172.16us     152.48us                         1.13x
   256     262144    512 |     185.03us     152.80us                         1.21x
   256     262144   1024 |     185.33us     153.22us                         1.21x
   256     262144   2048 |     220.74us     153.57us                         1.44x
   256     262144   4096 |     403.57us     154.13us                         2.62x
   256     524288    256 |     320.91us     295.36us                         1.09x
   256     524288    512 |     320.71us     296.06us                         1.08x
   256     524288   1024 |     346.91us     296.64us                         1.17x
   256     524288   2048 |     347.35us     297.58us                         1.17x
   256     524288   4096 |     815.83us     298.11us                         2.74x


```

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
* Added a clustered Top‑K option with public APIs, automatic dispatch,
and support for page‑table and ragged inputs.

* **Benchmarks**
* Added "clusters" measurement path, CUDA-graph timing, and
speedup-vs-default reporting in benchmark output.

* **Tests**
* New correctness and coverage tests for clustered Top‑K gated by
compute capability with dtype-specific accuracy thresholds.

* **Chores**
* Updated JIT/build to include clustered kernels and pass CUDA compile
flags; added a cached shared‑memory query utility.

* **Style**
* Tightened test assertions, improved GPU timing sync, and adjusted
benchmark output formatting.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Allan Lin <comms@aalanli.blog>

### [ce02358](https://github.com/flashinfer-ai/flashinfer/commit/ce02358d2b37ee7c86fc505da813497d6c596b6c)

- **作者**: xueweilnvidia
- **时间**: 2026-04-20T17:21:52Z
- **提交信息**: Add parallel attention (#2630)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add a `parallel_attention` module to FlashInfer that enables distributed
attention
computation using **Ulysses** (all-to-all head parallelism) and **Ring**
(P2P KV
exchange with online softmax merging) strategies, or a combination of
both.

### New files

- **`parallel_attention.py`** — `ParallelAttention` class: the main
entry point that
wraps any registered attention backend and applies Ulysses/Ring
parallelism
  transparently via decorators.
- **`parallel_config.py`** — Configuration classes:
- `AttnParallelConfig`: singleton that manages `ulysses_size`,
`ring_size`, device
    mesh creation, and process group accessors.
- `UnevenCPConfig`: handles uneven context parallelism where the total
sequence
    length is not divisible by `world_size`.
- `VarlenCPConfig`: handles variable-length (ragged) batching where
multiple
    sequences of different lengths are packed together.
- **`parallel_wrapper.py`** — Decorator implementations:
- `ulysses_wrapper`: performs all-to-all communication to split heads
across ranks,
    calls the inner function, then reverses the all-to-all.
- `ring_wrapper`: implements ring attention with P2P KV exchange and
online softmax
    correction across ring steps.
  - Helper functions: `all_to_all`, `ulysses_a2a_in/out`,
    `ring_fwd_out_correction`, `ring_fwd_softmax_lse_correction`,
    `ring_attn_p2p_communicate`.
- **`attention_ops.py`** — `AttentionOpManager` registry with
decorator-based
backend registration. Includes `FlashAttn3` as the first registered
backend.
- **`utils.py`** — Utility functions: `convert_qkv_layout`,
`convert_output_layout`,
  `split_varlen_input`.
- **`__init__.py`** — Package API re-exports.

### Tests

- **`tests/attention/test_parallel_attention.py`** — Pytest-based test
suite covering:
  - Combined Ulysses + Ring attention (`test_attn_parallel`)
  - Uneven context parallelism (`test_uneven_attn_parallel`)
  - Ulysses-only varlen attention (`test_ulysses_varlen_attn_parallel`)
  - Ring-only varlen attention (`test_ring_varlen_attn_parallel`)
  - Parametrized over `tensor_layout` (`"HND"` / `"NHD"`)

### Key design decisions

- **Backend-agnostic**: any attention function can be registered via
`@AttentionOpManager.register_attn("name")` and used with parallel
wrappers.
- **Decorator-based parallelism**: `@ulysses_wrapper` and
`@ring_wrapper` are
  composable decorators — they can be stacked or used independently.
- **No causal support yet**: `is_causal=True` raises
`NotImplementedError`.
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
* Parallel attention framework enabling distributed inference across
multiple GPUs
* Ulysses and Ring parallelism strategies to optimize throughput and
reduce latency
* Multiple pluggable attention backends with automatic kernel selection
based on hardware
* Variable-length sequence handling for flexible batch processing in
distributed settings
* Comprehensive utilities for tensor layout conversion and distributed
sequence management

* **Tests**
* Added comprehensive distributed test suite for parallel attention
scenarios
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Sam (Kesen Li) <lsam@nvidia.com>

### [06cb1b7](https://github.com/flashinfer-ai/flashinfer/commit/06cb1b76489ec539983b9e1289e4f336dbe1b969)

- **作者**: meena-at-work
- **时间**: 2026-04-20T16:16:50Z
- **提交信息**: Fix: Extend b12x FP4 GEMM support to SM121 (GB10/DGX Spark) (#3113)

SM121 (GB10, used in DGX Spark and RTX Pro 6000) supports the same b12x
CuTe DSL warp-level MMA FP4 GEMM kernels as SM120, but was excluded from
_b12x_gemm_fp4_requirement's supported_compute_capability list. On
SM121, calling mm_fp4(..., backend="b12x") raised:
BackendSupportedError: mm_fp4 does not support backend 'b12x' with
capability 121

Add 121 to the supported compute capability list so that mm_fp4(...,
backend="b12x") works correctly on SM121.

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

## Release Notes

* **New Features**
* Extended FP4 GEMM support to NVIDIA Hopper GPU architecture (SM121),
in addition to Ada GPUs (SM120), enabling optimized performance on a
broader range of NVIDIA GPUs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Meenakshi Venkataraman <meenakshiv@nvidia.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3406
- **最后更新**: 2026-04-20T07:51:29Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 33389
- **最后更新**: 2026-04-21T00:02:14Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 395
- **最后更新**: 2026-04-20T06:12:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12261
- **最后更新**: 2026-04-20T16:41:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 26142
- **最后更新**: 2026-04-20T23:48:47Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 17
- **主要提交者**: Kangyan-Zhou, jsheng_Linkedin, Shunkangz

## AI分析总结

根据提供的提交记录和README摘要（项目为SGLang，一个专注于高效语言模型推理的框架），以下是昨日更新的分析总结：

### 1. 主要更新类型
昨日提交以**Bug修复**和**性能优化**为主，同时包含**功能新增**、**文档/基础设施更新**和**CI/CD改进**。
- **Bug修复**：涉及CUDA图、内存管理、Docker构建、AMD平台兼容性等多个关键领域。
- **性能优化**：针对推测解码（EAGLE）、缓存策略和扩散模型进行了优化。
- **功能新增**：主要为推测解码和AMD平台支持添加了新功能。
- **文档/基础设施**：更新了文档站点和代码所有权文件。
- **CI/CD与构建**：修复了Docker构建、CI流程和工具链安装问题。

### 2. 关键变更点及其与项目方向的关系
SGLang的核心目标是提升LLM推理的**性能**和**效率**。昨日的更新紧密围绕这一目标：
- **推测解码优化** (`#21599`, `#23106`)：通过引入自适应推测步数和优化EAGLE算法的数据结构（O(1)视图），直接提升了推理速度，这是项目在**低延迟、高吞吐**方向上的核心进展。
- **运行时与内存修复** (`#22832`, `#23138`, `#23136`)：修复了CUDA图、批处理满度和CUDA内存拷贝的严重问题，确保了框架在**高性能GPU推理**时的**稳定性和正确性**。
- **多平台与硬件支持** (`#23219`, `#23247`, `#22003`)：增强了对AMD GPU（启用MTP、修复超时）和MoE模型配置的支持，体现了项目扩大**硬件兼容性**和**模型支持范围**的战略。
- **基础设施稳固** (`#23097`, `#23279`, `#23277`)：修复了Docker和CI流水线中的问题，保障了项目**持续交付**的可靠性。

### 3. 对项目的影响和潜在意义
- **正面影响**：
    - **性能提升**：推测解码和缓存的优化将直接转化为更快的终端用户推理体验。
    - **稳定性增强**：多个关键Bug的修复降低了生产环境崩溃的风险，提升了框架的健壮性。
    - **生态扩展**：对AMD和更多模型配置的支持吸引了更广泛的用户和开发者群体。
- **潜在风险**：部分提交（如CUDA图修复、缓存策略调整）涉及底层核心逻辑，需充分测试以确保不会引入新的回归问题。

### 4. 值得关注的技术点
- **自适应推测解码** (`#21599`)：根据上下文动态调整推测步数，是平衡推测成功率和计算开销的智能策略。
- **EAGLE算法的RadixKey O(1)视图** (`#23106`)：通过避免数据拷贝来优化大数据结构访问，是高性能C++/CUDA编程的典型技巧。
- **CUDA Graph Draft Extend修复** (`#22832`)：CUDA图是优化推理延迟的重要手段，此修复对保证其正确性至关重要。
- **多LoRA测试的Flaky Case处理** (`#23287`)：反映了项目对复杂功能（多LoRA）测试覆盖度和稳定性的重视。

### 5. 基于项目背景的提交影响分析
SGLang定位为“用于LLM的高效推理框架”。昨日的提交集体体现了项目在此愿景下的快速迭代：
- **强化核心优势**：绝大多数提交（推测解码、CUDA、缓存）都直接作用于推理**性能**这一生命线，不断打磨其核心竞争力。
- **提升生产就绪度**：通过修复Docker、CI、内存管理和跨平台问题，项目正从“可用”向“稳定、可靠、易部署”的**生产级框架**迈进。
- **构建开放生态**：支持AMD硬件、完善文档站点，有助于降低使用门槛，吸引社区贡献，促进**生态增长**。

**总结**：昨日的更新是一次典型的“夯实基础、优化核心”的迭代。团队在猛攻前沿性能特性（如推测解码）的同时，并未忽视基础设施的稳定性和跨平台支持，这为SGLang的长期发展和广泛应用奠定了坚实基础。

## 详细提交记录

### [712b01d](https://github.com/sgl-project/sglang/commit/712b01d875bc9f1a21d2602390f84736d0bbb43d)

- **作者**: Mingyi
- **时间**: 2026-04-20T23:48:41Z
- **提交信息**: Update CODEOWNERS to include new documentation paths for docs and doc… (#23293)

### [3e367f9](https://github.com/sgl-project/sglang/commit/3e367f9bcdf903ed580d328f9071acb3cb9ef2d7)

- **作者**: Tarushii Goel
- **时间**: 2026-04-20T23:29:16Z
- **提交信息**: [sgl] fix incorrect behavior in cuda graph draft extend  (#22832)

### [100b0f8](https://github.com/sgl-project/sglang/commit/100b0f86ddc1b94e2536a2bc8474b7a1e16fb34e)

- **作者**: Tarushii Goel
- **时间**: 2026-04-20T23:26:20Z
- **提交信息**: [sgl] add support for weight update function in spedec (#22088)

### [28f3a2d](https://github.com/sgl-project/sglang/commit/28f3a2d8ed6daf3ea4f42eabe5dcfa61950422e2)

- **作者**: Tarushii Goel
- **时间**: 2026-04-20T23:22:16Z
- **提交信息**: [sgl] multilayereagleworkerv2 fix (#22954)

### [57ecce9](https://github.com/sgl-project/sglang/commit/57ecce980735c2401d97684ba866374ac437c0ee)

- **作者**: Thomas Wang
- **时间**: 2026-04-20T23:09:07Z
- **提交信息**: [AMD] Enable MTP for GLM-5-mxfp4 model (#23219)

### [a3291b5](https://github.com/sgl-project/sglang/commit/a3291b5654a1790c5a70610e17007b7127380fe7)

- **作者**: Mingyi
- **时间**: 2026-04-20T22:10:22Z
- **提交信息**: Add new Mintlify documentation site (docs_new/) (#23001)

Co-authored-by: AdityaVKochar <adityavardhankochar@gmail.com>
Co-authored-by: mintlify[bot] <109931778+mintlify[bot]@users.noreply.github.com>
Co-authored-by: adhyan-jain <adhyanjain2006@gmail.com>
Co-authored-by: Adhyan Jain <71976554+adhyan-jain@users.noreply.github.com>
Co-authored-by: Maitri-shah29 <maitrirajivshah@gmail.com>
Co-authored-by: Adarsh Shirawalmath <114558126+adarshxs@users.noreply.github.com>
Co-authored-by: Maitri Shah <shah29maitri@gmail.com>
Co-authored-by: Aditya Vardhan Kochar <80113212+AdityaVKochar@users.noreply.github.com>
Co-authored-by: Rishit Shivam <164783543+pokymono@users.noreply.github.com>
Co-authored-by: Rishitshivam <164783543+Rishitshivam@users.noreply.github.com>
Co-authored-by: IshhanKheria <ishhankheria06@gmail.com>
Co-authored-by: Ishita Joshi <ishitata.joshi@gmail.com>
Co-authored-by: Richard Chen <104477092+Richardczl98@users.noreply.github.com>
Co-authored-by: longGGGGGG <553746008@qq.com>
Co-authored-by: Richard <richardchen@radixark.ai>
Co-authored-by: Nakul Sinha <nakul.new4socials@gmail.com>
Co-authored-by: Divyam Agrawal <ludicrouslytrue@gmail.com>
Co-authored-by: Richardczl98 <Zhenlinc@stanford.edu>
Co-authored-by: Krishang Zinzuwadia <krishangzinzuwadia@gmail.com>
Co-authored-by: nimeshas <nimesha.s106@gmail.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Jignas Paturu <86356085+JignasP@users.noreply.github.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>

### [575fdc2](https://github.com/sgl-project/sglang/commit/575fdc2c4c77d7b89b58d667641e0b4f42c506a5)

- **作者**: jsheng_Linkedin
- **时间**: 2026-04-20T21:43:25Z
- **提交信息**: [CI][LoRA] Drop flaky all-None batch from multi-LoRA parity test (#23287)

### [b65799c](https://github.com/sgl-project/sglang/commit/b65799cf8393e9a973cba80c0f800252e8da91d3)

- **作者**: shuwenn
- **时间**: 2026-04-20T21:25:04Z
- **提交信息**: [SPEC][1/N] feat: add adaptive speculative_num_steps for EAGLE topk=1 (#21599)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [dbcf745](https://github.com/sgl-project/sglang/commit/dbcf7459b51e1ee48fe2f3341a2c2e83cdffd24e)

- **作者**: shuwenn
- **时间**: 2026-04-20T21:14:00Z
- **提交信息**: fix: reset empty prefill batch fullness (#23138)

### [d8d9d32](https://github.com/sgl-project/sglang/commit/d8d9d32b29e2d713fbe08ae7661776f31d7bb066)

- **作者**: mispa-ms
- **时间**: 2026-04-20T20:44:05Z
- **提交信息**: [docker] Fix stray backslash dropping sgl-model-gateway COPY (#23097)

Signed-off-by: misunp <misunp@nvidia.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [6f6843c](https://github.com/sgl-project/sglang/commit/6f6843c58293481bf9828a8d65dab5d8ee3e0c1b)

- **作者**: ishandhanani
- **时间**: 2026-04-20T20:13:10Z
- **提交信息**: [Docker] Move Rust toolchain install to torch_deps stage (#23278)

### [fe9b9b2](https://github.com/sgl-project/sglang/commit/fe9b9b254b6c3a88a52c7fe1300be19f0ad03ea1)

- **作者**: Yuhao Yang
- **时间**: 2026-04-20T19:20:22Z
- **提交信息**: Fix segfault in cudaMemcpyBatchAsync on CUDA 13.0 (#23136)

Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Kangyan-Zhou <zky314343421@gmail.com>

### [8cb957c](https://github.com/sgl-project/sglang/commit/8cb957ccffa23da7ded70f1efdc5d5f5e9b6578a)

- **作者**: Liangsheng Yin
- **时间**: 2026-04-20T19:01:11Z
- **提交信息**: [Perf] Make EAGLE bigram key an O(1) view on `RadixKey` (#23106)

### [3dc1491](https://github.com/sgl-project/sglang/commit/3dc1491c95b48fb2950a469401f24a68764c9fd6)

- **作者**: Shunkangz
- **时间**: 2026-04-20T18:58:19Z
- **提交信息**: Support moe_dp_size = 1 for various attention_cp_size (#22003)

Co-authored-by: Shunkang <182541032+Shunkangz@users.noreply.github.co>

### [90d5271](https://github.com/sgl-project/sglang/commit/90d527195bd725d8e05503ee49df79abec292cb2)

- **作者**: ishandhanani
- **时间**: 2026-04-20T18:56:33Z
- **提交信息**: [CI] Fix nightly docker builds failing on root-owned workspace leftovers (#23279)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [b4bb036](https://github.com/sgl-project/sglang/commit/b4bb036b7308b8b77f8017870e6eb7a287d8eeca)

- **作者**: Lee Nau
- **时间**: 2026-04-20T18:49:33Z
- **提交信息**: fix legacy deepep path for flashinfer_cutedsl (#22925)

### [4698f4c](https://github.com/sgl-project/sglang/commit/4698f4cd107114362ea8ad51903ff1f976532a9d)

- **作者**: Kangyan-Zhou
- **时间**: 2026-04-20T18:16:10Z
- **提交信息**: [CI] Fix wait-for-jobs hanging when matrix job skipped at job level (#23277)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

### [b5d9a86](https://github.com/sgl-project/sglang/commit/b5d9a86e4cc3136234614ef919a4e822a9060c36)

- **作者**: ishandhanani
- **时间**: 2026-04-20T17:04:35Z
- **提交信息**: fix: add back priorty as radix cache policy (#23275)

### [332ec5e](https://github.com/sgl-project/sglang/commit/332ec5e5eea4f5ff036027f1fa49ed034b9959e3)

- **作者**: Alex Nails
- **时间**: 2026-04-20T16:50:08Z
- **提交信息**: [release] install rust toolchain in main dockerfile (#23014)

### [39c720d](https://github.com/sgl-project/sglang/commit/39c720d1b9cb4e98dac9805f4dd2d56412b1fe0a)

- **作者**: Makcum888e
- **时间**: 2026-04-20T16:34:11Z
- **提交信息**: [Diffusion][NPU][CI] update perf numbers (#23056)

Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [9a0fd2f](https://github.com/sgl-project/sglang/commit/9a0fd2ff0c830a30e8d7e67c493e928fa5fdbdae)

- **作者**: Mick
- **时间**: 2026-04-20T15:29:02Z
- **提交信息**: [diffusion] optimize: default to in-memory loading for URL/base64 image inputs (#23118)

### [0be6ab0](https://github.com/sgl-project/sglang/commit/0be6ab04dd4209e81f4afac10eb5832dd3b5e62b)

- **作者**: Mick
- **时间**: 2026-04-20T11:02:05Z
- **提交信息**: [diffusion] refactor: LTX2.3 code cleanup (#23207)

### [da62e90](https://github.com/sgl-project/sglang/commit/da62e909048854d3702067c7e71b8b9194de499f)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-04-20T10:36:08Z
- **提交信息**: [AMD] Fix multimodal timeout issue : rocm7.2 PR Test (#23247)

### [cf4b84f](https://github.com/sgl-project/sglang/commit/cf4b84f8390ed8fda2f3f28dc6ab5a88a3f0e5e5)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-04-20T10:18:24Z
- **提交信息**: [AMD] Update AMD workflow name (#23245)

Co-authored-by: bingxche <bingxche@amd.com>

### [4028a73](https://github.com/sgl-project/sglang/commit/4028a73c10835ad40b9bd47b7dd744629da23aee)

- **作者**: Vladislav Nosivskoy
- **时间**: 2026-04-20T09:34:38Z
- **提交信息**: [KV-Events] Fix kv events events publishing for CP (#22983)

Signed-off-by: Vladislav Nosivskoy <vladnosiv@gmail.com>

### [bea4c89](https://github.com/sgl-project/sglang/commit/bea4c895c1f312561221f6a0319bd76400c821f4)

- **作者**: Alex Nails
- **时间**: 2026-04-20T09:20:14Z
- **提交信息**: [gRPC] Pass --experimental_allow_proto3_optional to protoc in build.rs (#23226)

Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native Inference Engine with Cache Acceleration, Parallelism and Quantization for DiTs.
- **语言**: Python
- **星标数**: 1146
- **最后更新**: 2026-04-20T07:35:26Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 77452
- **最后更新**: 2026-04-21T00:00:16Z

## 提交统计

- **昨日提交总数**: 33
- **提交者数量**: 26
- **主要提交者**: larryli2-amd, Hashem Hashemi, aleksandaryanakiev

## AI分析总结

根据提供的提交记录和项目README摘要（vLLM：面向所有人的易用、快速、经济的LLM服务），以下是昨日更新的要点总结：

### 1. 主要更新类型
- **Bug修复**：占比最高，涉及MoE、XPU、ROCm、CPU、日志、API等多个模块。
- **功能新增/增强**：主要集中在**ROCm（AMD）支持**、**EPLB（高效并行负载均衡）**、**MoE（混合专家）** 和**量化**方面。
- **性能优化与重构**：包括缓存优化、通信模式改进、代码结构重构。
- **CI/测试与文档**：新增集成测试、修复测试用例、更新文档。
- **第三方库更新**：升级`flashinfer`推理库。

### 2. 关键变更点及其与项目方向的关系
| 关键变更点 | 涉及提交 | 与项目方向（易用、快速、经济）的关系 |
| :--- | :--- | :--- |
| **AMD ROCm生态强化** | 3, 6, 16, 17, 19, 30 | 提升对**AMD硬件**的支持广度和深度（如MLA融合、MoRI构建、新节点），扩大硬件覆盖，使服务更“经济”和普适。 |
| **MoE（混合专家）模型优化** | 1, 14, 15 | 修复共享专家重叠等问题，**提升MoE模型推理的正确性和性能**，对服务热门大模型（如DeepSeek-V2）至关重要。 |
| **EPLB（高效并行负载均衡）与通信重构** | 4, 9, 13, 20, 25, 26 | 重构和增强**分布式推理的通信与负载均衡**逻辑，旨在提升**大规模分布式部署的效率与稳定性**，是“快速”和“经济”的核心。 |
| **量化与低精度计算支持** | 15, 16, 21 | 修复和增强**XPU/AMD上的FP8量化**路径，直接降低显存占用、提升计算速度，实现更“经济”的部署。 |
| **核心性能与稳定性修复** | 7, 10, 12, 22, 28, 29 | 优化编译缓存、日志标签、CPU绑定等底层细节，提升**框架整体稳定性和性能基线**。 |
| **API与前端完善** | 23, 32, 33 | 完善Anthropic消息API、离线生成API等，提升**开发者体验和易用性**。 |

### 3. 对项目的影响和潜在意义
- **硬件生态扩展**：持续加大对**AMD ROCm**和**Intel XPU**的支持力度，降低用户对NVIDIA生态的依赖，符合“面向所有人”的开放目标。
- **生产就绪度提升**：大量**Bug修复**和**集成测试**的加入，表明项目正致力于提升在生产环境中的**稳定性和可靠性**。
- **架构演进**：对**EPLB**和**通信层**的持续重构，显示出项目在优化**超大规模模型分布式服务**架构方面的长期投入。
- **前沿模型支持**：针对**MoE**和**MLA（多头潜在注意力）** 等新兴模型架构的优化，确保vLLM能高效服务最新最热的开源模型。

### 4. 值得关注的技术点
- **MLA Dual RMS Norm Fusion**：针对DeepSeek/Kimi等模型的特定内核融合优化，体现了对**国产热门模型**的深度适配。
- **Nixl-based EPLB Communicator**：引入新的底层通信抽象，可能为未来更灵活的异构并行策略打下基础。
- **KV Offload with Sliding Window**：支持滑动窗口的KV缓存卸载，是优化**长上下文**场景内存经济性的关键技术。
- **在线MXFP8量化迁移至新前端**：量化流程的架构升级，可能带来更好的性能和易用性。

### 5. 基于项目背景的总体发展影响
vLLM的核心目标是降低LLM服务门槛。昨日的更新集体指向这一目标的深化：
- **易用性**：通过修复API、完善文档、增强对多种硬件的开箱即用支持，让更广泛的开发者能轻松使用。
- **快速性**：通过内核融合、通信优化、量化支持、缓存改进等多层次优化，持续压榨硬件性能，提升推理速度。
- **经济性**：通过强化对AMD/Intel等替代硬件的支持、推进低精度量化、优化内存/通信效率，直接帮助用户降低部署与运营成本。

**结论**：本次更新是一次以**稳定性修复**和**硬件生态扩展**为主的常规迭代，同时持续推进**分布式架构**和**前沿模型支持**等核心竞争力的建设。这符合vLLM作为一个成熟、活跃的推理框架，在扩大市场覆盖的同时，不断巩固技术护城河的发展路径。

## 详细提交记录

### [6867bcd](https://github.com/vllm-project/vllm/commit/6867bcd076191e8a60f0e49e90059b01910725be)

- **作者**: bnellnm
- **时间**: 2026-04-20T23:36:16Z
- **提交信息**: [Bugfix] Replace code that disabled shared expert overlap (#39222)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [c075702](https://github.com/vllm-project/vllm/commit/c075702eaee56ca2f4a315e742f3c89f5e4c6e71)

- **作者**: Matthew Bonanni
- **时间**: 2026-04-20T22:32:46Z
- **提交信息**: [Misc][UX] Suppress confusing `num_gpu_blocks` log lines (#40402)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [21b086d](https://github.com/vllm-project/vllm/commit/21b086d0aaea612bdf3fef0c313513eac8350083)

- **作者**: Rita Brugarolas
- **时间**: 2026-04-20T21:20:05Z
- **提交信息**: [ROCm] Hotfix: guard MLA dual RMS norm fusion against older AITer versions (#40386)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>

### [3173441](https://github.com/vllm-project/vllm/commit/3173441b0f73324771c5638e8c123a2cef784198)

- **作者**: Sage Moore
- **时间**: 2026-04-20T21:12:42Z
- **提交信息**: [EPLB] Consolidate is_unchanged/is_received_locally into TransferMetadata (#37341)

Signed-off-by: Sage Moore <sage@neuralmagic.com>

### [8b1f3be](https://github.com/vllm-project/vllm/commit/8b1f3bebcab8f501e13183f84b20635cf336ccc1)

- **作者**: Cao Qian
- **时间**: 2026-04-20T20:42:49Z
- **提交信息**: [LMCache MP Connector] Add num_lmcache_extra_cached_token in KVTransferParams (#39843)

Signed-off-by: aeon-x <talexcao@gmail.com>

### [2390caf](https://github.com/vllm-project/vllm/commit/2390caf157cbfb5f73c5994158bca654ddae2706)

- **作者**: Theresa Shan
- **时间**: 2026-04-20T18:17:59Z
- **提交信息**: Enable building MoRI with AMD AINIC stack (#38371)

Signed-off-by: Theresa Shan <thshan@smci355-ccs-aus-n08-21.prov.aus.ccs.cpe.ice.amd.com>
Signed-off-by: Theresa Shan <theresa.shan@amd.com>
Co-authored-by: Theresa Shan <thshan@smci355-ccs-aus-n08-21.prov.aus.ccs.cpe.ice.amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [87805fa](https://github.com/vllm-project/vllm/commit/87805fa11ea6d9f9aa7a7fc92ac957c613bc2163)

- **作者**: Frederik Gossen
- **时间**: 2026-04-20T18:06:15Z
- **提交信息**: [Core] Cache InductorPass.hash_source with functools.cache (#39328)

Signed-off-by: Frederik Gossen <frgossen@meta.com>

### [304d5ba](https://github.com/vllm-project/vllm/commit/304d5ba1a04b6cbfa2b5bd377c2a89d350a10921)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-04-20T18:05:44Z
- **提交信息**: [Bugfix][CI] Fix `tests/distributed/test_torchrun_example_moe.py` (#40349)

Signed-off-by: NickLucche <nlucches@redhat.com>

### [81d954f](https://github.com/vllm-project/vllm/commit/81d954f454d45425a0ad0a0a742de2695e4f043a)

- **作者**: Tyler Michael Smith
- **时间**: 2026-04-20T17:53:55Z
- **提交信息**: [WideEP] Remove naive all2all. Use allgather_reducescatter instead (#33728)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [47fcb8c](https://github.com/vllm-project/vllm/commit/47fcb8ca68c1027ba7eb7a9056bb4596ee284221)

- **作者**: Frederik Gossen
- **时间**: 2026-04-20T17:40:52Z
- **提交信息**: [Core] Pass donate_graph_module=True to standalone_compile (#39733)

Signed-off-by: Frederik Gossen <frgossen@meta.com>

### [191e3fd](https://github.com/vllm-project/vllm/commit/191e3fdaa1fd3dd09441e7b22d4f2ddef51c012c)

- **作者**: bai
- **时间**: 2026-04-20T17:37:23Z
- **提交信息**: Update flashinfer to 0.6.8 (#39959)

Signed-off-by: bai <v@gor.io>

### [b9cf629](https://github.com/vllm-project/vllm/commit/b9cf629bd0e924c69f3d8bfefbfdb77df5ffc7be)

- **作者**: Frederik Gossen
- **时间**: 2026-04-20T17:31:03Z
- **提交信息**: [Core] Label torch trace logging overhead with dynamo_timed (#39329)

Signed-off-by: Frederik Gossen <frgossen@meta.com>

### [3461c8b](https://github.com/vllm-project/vllm/commit/3461c8b0277f2d1df6c7ea1ec789881c1d01650b)

- **作者**: Sage Moore
- **时间**: 2026-04-20T17:05:41Z
- **提交信息**: [EPLB] Refactor Async EPLB synchronization logic (#37601)

Signed-off-by: Sage Moore <sage@neuralmagic.com>
Co-authored-by: Tyler Michael Smith <tyler@neuralmagic.com>

### [726efe1](https://github.com/vllm-project/vllm/commit/726efe177bf22874743d11dfdfef9247dbfb5ff0)

- **作者**: bnellnm
- **时间**: 2026-04-20T16:28:46Z
- **提交信息**: [MoE Refactor] Move the shared/fused expert output sum into MoERunnerBase (#35949)

Signed-off-by: Bill Nell <bnell@redhat.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>

### [5955626](https://github.com/vllm-project/vllm/commit/595562651a5a4539ffa910d8570c08fb5169bdc9)

- **作者**: Yan Ma
- **时间**: 2026-04-20T15:31:39Z
- **提交信息**: [XPU] fix MoE triton backend in online fp8 quantization  (#40109)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [3a30eaa](https://github.com/vllm-project/vllm/commit/3a30eaa1d7b6497ce70c15558d410e37d8399b87)

- **作者**: Hashem Hashemi
- **时间**: 2026-04-20T15:09:24Z
- **提交信息**: Properly enable wvSplitK fp8 path for RDNA (#37712)

Signed-off-by: Hashem Hashemi <hashem.hashemi@amd.com>

### [fb5635d](https://github.com/vllm-project/vllm/commit/fb5635d3f90635ce9d1acbc975baab6e911a262b)

- **作者**: Rita Brugarolas
- **时间**: 2026-04-20T14:56:27Z
- **提交信息**: [ROCm] Add MLA dual RMS norm fusion (Q, KV) pass for DeepSeek/Kimi-K2 (#39242)

Signed-off-by: Rita Brugarolas Brufau <rita.brugarolasbrufau@amd.com>

### [b42e878](https://github.com/vllm-project/vllm/commit/b42e878ec0182aafbaed5cc28708e99287ef6856)

- **作者**: Wentao Ye
- **时间**: 2026-04-20T14:52:32Z
- **提交信息**: [Bug] Fix dcp error message (#40053)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [7243e02](https://github.com/vllm-project/vllm/commit/7243e02aa1c6e01ab1d2a50aa7e27ebc9b2c6719)

- **作者**: larryli2-amd
- **时间**: 2026-04-20T14:44:43Z
- **提交信息**: [ROCm][Feature] Enable AITER MLA attention backend to work with Eagle3 speculative decoding on ROCm (#39616)

Signed-off-by: larryli2-amd <larryli2@amd.com>
Co-authored-by: TJian <tunjian.tan@embeddedllm.com>

### [def8f52](https://github.com/vllm-project/vllm/commit/def8f52200151c801867dde9ce27f829bce00105)

- **作者**: Sage Moore
- **时间**: 2026-04-20T14:22:54Z
- **提交信息**: [CI][EPLB] Add Async EPLB end-to-end integration test to CI (#40168)

Signed-off-by: Sage Moore <sage@neuralmagic.com>

### [38fa87c](https://github.com/vllm-project/vllm/commit/38fa87cacadc73aec9b28fea52fa70a31070cec4)

- **作者**: Vasiliy Kuznetsov
- **时间**: 2026-04-20T13:26:12Z
- **提交信息**: mxfp8 online quant move to new frontend (#40152)

Signed-off-by: Vasiliy Kuznetsov <vasiliy@meta.com>

### [a023edf](https://github.com/vllm-project/vllm/commit/a023edfa5bc1982ba5c6365ea2e36c6dfc48a9ef)

- **作者**: Galigator
- **时间**: 2026-04-20T13:19:57Z
- **提交信息**: [bugfix] Use only onlines CPUs in lscpu (#40161)

Signed-off-by: kse <kevin.sejourne@cloud-temple.com>
Co-authored-by: kse <kevin.sejourne@cloud-temple.com>

### [b82fc13](https://github.com/vllm-project/vllm/commit/b82fc1364d313a222bde7e9ac897fd847ad7b05b)

- **作者**: aleksandaryanakiev
- **时间**: 2026-04-20T13:10:45Z
- **提交信息**: [Anthropic][Frontend] Added chat_template_kwargs to /v1/messages (#40125)

Signed-off-by: Aleksandar Yanakiev <alexander.yanakiev@discretestack.com>
Co-authored-by: Aleksandar Yanakiev <alexander.yanakiev@discretestack.com>

### [e06de7f](https://github.com/vllm-project/vllm/commit/e06de7f0057fe1dfcc4fb039b52a61d39a079c4c)

- **作者**: Yan Ma
- **时间**: 2026-04-20T12:57:11Z
- **提交信息**: [XPU] enable triton attention test on XPU by removing cuda device binding (#39627)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [cc3993b](https://github.com/vllm-project/vllm/commit/cc3993b05d008be370778466865cce1959ac85a3)

- **作者**: zhanqiuhu
- **时间**: 2026-04-20T10:39:08Z
- **提交信息**: nixl refactor [2/N]: unify TpKVTopology + HeteroTPTransferConfig into TransferTopology (#39529)

Signed-off-by: Zhanqiu Hu <zhu@redhat.com>

### [50dd4cb](https://github.com/vllm-project/vllm/commit/50dd4cb42726777635acda9ed4f5440ae4a2e281)

- **作者**: Ilya Markov
- **时间**: 2026-04-20T10:24:23Z
- **提交信息**: [EPLB] Add nixl-based eplb communicator (#36276)

Signed-off-by: ilmarkov <markovilya197@gmail.com>
Signed-off-by: Markov Ilya <markovilya19@gmail.com>

### [f774ba0](https://github.com/vllm-project/vllm/commit/f774ba028afe08fab1ca96ecf7c0b40c0fa45357)

- **作者**: Or Ozeri
- **时间**: 2026-04-20T09:53:51Z
- **提交信息**: [kv_offload+HMA][4/N]: Support sliding window lookup (#36645)

Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [2aab9ac](https://github.com/vllm-project/vllm/commit/2aab9acf48b5f10a4ee0b29f152fc497a46c956d)

- **作者**: Fadi Arafeh
- **时间**: 2026-04-20T09:21:12Z
- **提交信息**: [CPU][BugFix] Fix inter-node pipeline parallel (#40150)

Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>

### [58631d7](https://github.com/vllm-project/vllm/commit/58631d7c3f9984f979e3cd5abf20a61590b36b1f)

- **作者**: nemanjaudovic
- **时间**: 2026-04-20T08:58:39Z
- **提交信息**: [Bugfix] Fix scaled_mm output narrowing for 3D input tensors (#38093)

Signed-off-by: nemanjaudovic <nudovic@amd.com>

### [a943839](https://github.com/vllm-project/vllm/commit/a943839e9a7c9ee00e57fcfabbbf0a453393cc97)

- **作者**: Andreas Karatzas
- **时间**: 2026-04-20T08:09:58Z
- **提交信息**: [ROCm][CI] Introducing new MI300 nodes (#39531)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [6d8b808](https://github.com/vllm-project/vllm/commit/6d8b80802ba0c6b7c119610af795f674bd78a73f)

- **作者**: milesial
- **时间**: 2026-04-20T08:09:44Z
- **提交信息**: [Docs] Fix thinking_token_budget docs (#40316)

Signed-off-by: milesial <milesial@users.noreply.github.com>

### [77fd2c8](https://github.com/vllm-project/vllm/commit/77fd2c863147a01c75e1080523425dea68fa75d7)

- **作者**: wuyingjun
- **时间**: 2026-04-20T07:56:56Z
- **提交信息**: [Bugfix] Forward mm_processor_kwargs in offline generate APIs (#40251)

Signed-off-by: wuyingjun <wuyingjun_yewu@cmss.chinamobile.com>

### [e729cc8](https://github.com/vllm-project/vllm/commit/e729cc823d313aa7623ecadefe4305ea241c3dce)

- **作者**: San-Nguyen
- **时间**: 2026-04-20T07:25:06Z
- **提交信息**: [Fix] Add Spacing when Requesting Output Token > max_model_len (#40324)

Signed-off-by: San-Nguyen <san.nguyen@ibm.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-04-21
**监控日期**: 2026-04-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 4429
- **最后更新**: 2026-04-20T23:34:22Z

## 提交统计

- **昨日提交总数**: 10
- **提交者数量**: 10
- **主要提交者**: John Liu BUAA, Sheral Kumar, fywc

## AI分析总结

根据提供的README摘要和提交记录，以下是vllm-omni项目昨日更新的分析总结：

### 1. 主要更新类型
- **Bug修复**：3项（音频提示截断、图像输出维度修复、Wan2.2提示长度限制回滚）
- **功能新增**：3项（FastGen DMD2蒸馏模型、Hunyuan-Image3示例、LTX-2模型HSDP支持）
- **CI/CD与部署**：2项（Docker镜像发布、性能测试调整）
- **文档更新**：1项（Ascend NPU使用指南）
- **性能与工具增强**：1项（PyTorch性能分析器）

### 2. 关键变更点与项目方向关系
- **多模态模型扩展**：新增FastGen DMD2（文/图生视频）、Hunyuan-Image3（图像生成）、LTX-2（HSDP支持）模型，直接强化项目“全模态（omni-modality）”服务能力
- **部署与硬件适配**：针对Ascend NPU、AMD Docker发布优化，体现项目“为所有人服务”的跨平台兼容性目标
- **稳定性与性能**：修复音频/图像处理Bug、回滚过度限制，确保服务“快速、稳定”的核心承诺

### 3. 对项目的影响和潜在意义
- **用户体验提升**：Bug修复和示例添加（如Hunyuan-Image3 end2end.py）降低了用户使用门槛
- **生产就绪度增强**：CI/CD优化和Docker发布流程改进，支持大规模部署
- **生态扩展**：支持更多模型（尤其是视频生成）和硬件（NPU/AMD），扩大项目适用场景

### 4. 值得关注的技术点
- **FastGen DMD2蒸馏模型**：可能意味着在视频生成任务上实现了效率与质量的平衡
- **HSDP（Hierarchical Software Data Parallelism）支持**：为LTX-2等大模型提供更高效的大规模分布式训练/推理能力
- **PyTorch Profiler集成**：为性能调优和资源监控提供底层工具支持
- **NPU特定优化**：针对华为Ascend芯片的文档，显示项目在专用AI硬件上的深入适配

### 5. 基于项目背景的提交影响分析
vllm-omni旨在提供“**简单、快速、廉价的全模态模型服务**”。昨日的更新：
- **强化“全模态”定位**：通过新增视频生成（T2V/I2V）、图像生成模型，覆盖文本、图像、音频、视频多模态场景
- **体现“为所有人”**：通过支持NPU、AMD环境及完善文档/示例，降低不同硬件和开发者的使用门槛
- **优化“快速、廉价”**：性能测试调整、Bug修复和Profiler工具有助于提升推理效率和稳定性，间接降低成本
- **展现项目成熟度**：从功能开发转向稳定性、部署和生态建设（CI/CD、跨平台发布），表明项目向生产就绪阶段迈进

**总结**：本次更新以**功能扩展和稳定性提升**为主线，紧密围绕项目的全模态、跨平台、生产级服务目标，既丰富了模型生态，又夯实了基础设施，是项目从“可用”向“好用、易用”演进的关键一步。

## 详细提交记录

### [618268d](https://github.com/vllm-project/vllm-omni/commit/618268d6b9e802545829e92bf5d779367c625f61)

- **作者**: SYLAR
- **时间**: 2026-04-20T16:40:29Z
- **提交信息**: [Bugfix] Truncate mimo-audio code2wav prompt to MAX_CODE2WAV_TOKENS (#2693)

Signed-off-by: lishunyang <lishunyang12@163.com>

### [400690f](https://github.com/vllm-project/vllm-omni/commit/400690f63bb8cb68b0d0095762c74e1228921f81)

- **作者**: Didan Deng
- **时间**: 2026-04-20T16:29:32Z
- **提交信息**: [CI] Remove small resolution test in Qwen-Image Perf test when vae patch parallel is enabled (#2872)

Signed-off-by: Didan Deng <33117903+wtomin@users.noreply.github.com>

### [dc8a9e2](https://github.com/vllm-project/vllm-omni/commit/dc8a9e2f1791a6336fbeb2ec387e824e29aefb23)

- **作者**: Ayush Agarwal
- **时间**: 2026-04-20T13:21:43Z
- **提交信息**: [Model] feat: FastGen DMD2-distilled Wan 2.1 pipelines (T2V, I2V)    (#2749)

Signed-off-by: ayushag <ayushag@nvidia.com>

### [71d81d4](https://github.com/vllm-project/vllm-omni/commit/71d81d475abf22b0ba00aa89defadc3d298e456f)

- **作者**: bjf-frz
- **时间**: 2026-04-20T12:58:14Z
- **提交信息**: [Enhancement] add pytorch profiler ops and memory record (#2472)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [461bddc](https://github.com/vllm-project/vllm-omni/commit/461bddca66e40d078d9a908a50998d2aa8063c81)

- **作者**: Sheral Kumar
- **时间**: 2026-04-20T12:52:22Z
- **提交信息**: CI: publish Omni images to a separate Docker Hub repository (#2829)

Signed-off-by: Sheral Kumar <shekumar@amd.com>

### [6128f6d](https://github.com/vllm-project/vllm-omni/commit/6128f6df1f354162c2a527ee6295bc8ac7345095)

- **作者**: John Liu BUAA
- **时间**: 2026-04-20T12:15:14Z
- **提交信息**: [Example] Add Hunyuan-Image3 end2end.py and README.md (#2590)

Signed-off-by: John Liu BUAA <liukecheng97@gmail.com>

### [23b2a95](https://github.com/vllm-project/vllm-omni/commit/23b2a95df65aefbe7cb7b627177eef4975bf78d1)

- **作者**: Canlin Guo
- **时间**: 2026-04-20T11:35:48Z
- **提交信息**: [Docs] Add Wan2.2 image-to-video recipe for Ascend NPU (A2/A3) (#2919)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [7e28eda](https://github.com/vllm-project/vllm-omni/commit/7e28eda9291002824acdb1a95ca4cea1d779836e)

- **作者**: Jared Wen
- **时间**: 2026-04-20T11:24:06Z
- **提交信息**:  [Bugfix] Fix GLM-Image output dimensions and image edit pipeline (#2320)

Signed-off-by: JaredforReal <w13431838023@gmail.com>
Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [c2859e9](https://github.com/vllm-project/vllm-omni/commit/c2859e9cd78bedd2bd89c81f24411b916fb2f1d1)

- **作者**: WeiQing Chen
- **时间**: 2026-04-20T11:19:38Z
- **提交信息**: [Revert] drop Wan2.2 prompt-length enforcement from #2847 (#2877)

Signed-off-by: david6666666 <530634352@qq.com>

### [d613864](https://github.com/vllm-project/vllm-omni/commit/d613864dbfca0669c91a289a82f41bde6a871c47)

- **作者**: fywc
- **时间**: 2026-04-20T10:51:16Z
- **提交信息**: [Model] Add HSDP support for LTX-2 (#2899)

Signed-off-by: hanzheli <hanzheli@kuaishou.com>
Signed-off-by: fywc <hanzheli@kuaishou.com>

---
