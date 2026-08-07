# GitHub Stars 合并报告 - 2026-08-07

**合并日期**: 2026-08-08
**监控日期**: 2026-08-07
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


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2135
- **最后更新**: 2026-08-07T20:53:05Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Wyett

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交为**功能新增**，具体为在VLM（视觉语言模型）训练器中引入LoRA（低秩适配）支持。

**2. 关键变更点与项目方向的关系**  
- **变更点**：在`[lora, trainer]`模块中，为VLM训练器添加了LoRA微调能力。LoRA是一种参数高效微调技术，通过冻结预训练权重并注入低秩矩阵，大幅减少可训练参数量。  
- **与项目方向的关系**：VeOmni的核心目标是“以模型为中心的分布式训练配方库”，强调多模态（任意模态）模型的高效训练。LoRA支持直接契合这一方向——它降低了多模态模型微调的计算和存储成本，使研究者能更灵活地在不同规模、不同模态组合下快速适配模型，从而扩展“配方库”的实用性和覆盖面。

**3. 对项目的影响和潜在意义**  
- **影响**：VLM训练器现在支持两种微调范式（全量微调与LoRA），用户可根据资源或任务需求选择。这提升了训练器的通用性，尤其对资源受限的团队或快速迭代场景友好。  
- **潜在意义**：LoRA支持可能吸引更多社区用户（如学术研究者、中小团队）参与多模态模型定制，促进VeOmni生态的活跃度。同时，它也为后续支持更多参数高效方法（如Adapter、Prefix-tuning）奠定架构基础。

**4. 值得关注的技术点**  
- **实现层面**：需关注LoRA注入位置（如注意力层的Q/K/V/O矩阵）、秩（rank）的默认配置、与现有分布式训练（如张量并行、数据并行）的兼容性，以及是否支持与其他优化（如梯度检查点）协同工作。  
- **设计考量**：LoRA的引入可能涉及训练器配置接口的扩展（如新增`use_lora`参数），需确保与现有配置系统的向后兼容性。

**5. 对项目发展的影响（结合README背景）**  
VeOmni定位为“分布式训练配方库”，其核心价值在于提供可复现、可扩展的训练方案。LoRA支持使该库从“全量训练”扩展到“高效微调”场景，直接回应了多模态模型落地中的资源瓶颈问题。这一更新：  
- **扩展了配方库的适用场景**：从预训练、全量微调，延伸至轻量化适配，覆盖模型生命周期更多阶段。  
- **强化了“模型中心”理念**：通过降低微调门槛，让更多模型架构（如不同规模的VLM）能快速集成到VeOmni流程中，推动多模态训练的民主化。  
- **为后续功能铺路**：LoRA的模块化实现可能成为其他参数高效技术（如QLoRA、DoRA）的模板，加速项目在高效训练方向上的迭代。

**总结**：本次提交是VeOmni在“高效多模态训练”方向上的关键一步，通过引入LoRA，项目从“大规模训练”向“灵活适配”延伸，既符合其“配方库”的扩展性目标，也增强了社区吸引力。技术实现上的兼容性设计值得后续关注，以确保与现有分布式训练框架的无缝集成。

## 详细提交记录

### [6efdf22](https://github.com/ByteDance-Seed/VeOmni/commit/6efdf2217d46dedf4e517bf02783625aac8e75cc)

- **作者**: Wyett
- **时间**: 2026-08-07T20:52:59Z
- **提交信息**: [lora, trainer] feat: Add lora support for VLM trainer (#1018)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2591
- **最后更新**: 2026-08-07T18:16:00Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

### 1. 主要更新类型
本次提交属于**性能优化与功能增强**，核心围绕 `minimax_h3` 模型的 **warmup（预热）** 与 **compile（编译）** 机制展开。

### 2. 关键变更点及与项目方向的关系
- **变更点**：为 `minimax_h3` 模型引入 warmup 流程，并在推理前执行模型编译（compile），以提前完成算子融合、内核选择等耗时操作。
- **与项目方向的关系**：LightX2V 定位为“轻量视频生成推理框架”，核心目标是降低推理延迟、提升吞吐量。warmup 与 compile 是推理性能优化的关键手段，直接服务于“轻量”与“高效”的框架宗旨，尤其针对 `minimax_h3` 这类复杂视频生成模型，可显著减少首次推理的冷启动开销。

### 3. 对项目的影响和潜在意义
- **影响**：优化后，`minimax_h3` 模型在正式推理时的首token延迟和端到端耗时预计明显下降，提升用户体验；同时，编译后的内核可复用，降低多次推理的平均成本。
- **潜在意义**：该机制为后续支持更多视频生成模型（如类似架构的扩散或自回归模型）提供了可复用的性能优化范式，增强框架对不同模型族的适配能力，巩固 LightX2V 在视频生成推理领域的竞争力。

### 4. 值得关注的技术点
- **warmup 策略**：需关注预热数据规模、迭代次数如何平衡（过少则编译不充分，过多则增加启动时间）。
- **compile 方式**：可能涉及 `torch.compile` 或自定义图优化，需关注其与动态形状（视频帧数可变）的兼容性，以及编译缓存的管理。
- **与现有推理管线集成**：warmup/compile 是否自动触发，还是需用户显式配置，影响易用性。

### 5. 对项目发展的影响（结合README背景）
LightX2V 强调“轻量”与“开箱即用”，本次提交通过自动化 warmup 与 compile，降低了用户手动调优的门槛，使框架更易部署。同时，性能提升有助于吸引更多开发者基于该框架构建视频生成应用，推动生态繁荣。长远看，此类底层优化为框架支持更大规模模型（如更高分辨率视频生成）预留了性能空间，符合项目从“可用”向“好用”演进的方向。

## 详细提交记录

### [231e230](https://github.com/ModelTC/LightX2V/commit/231e2307f15b9eb60fe3f877f7eed945c8d8d717)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-07T07:03:15Z
- **提交信息**: minimax_h3 warmup and compile (#1339)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2188
- **最后更新**: 2026-08-06T10:24:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6128
- **最后更新**: 2026-08-07T16:41:41Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: EricChen02

## AI分析总结

### 1. 主要更新类型
- **性能优化**：针对Blackwell SM12x架构优化了gated MoE（混合专家）动态NVFP4内核。
- **功能增强**：将优化的gated激活路径集成到常规CuTeDSL调度中，支持SiLU、GELU-tanh和SwiGLU-OAI，无需环境变量切换。

### 2. 关键变更点及与项目方向的关系
- **代码拆分**：将动态MoE实现拆分为`generic.py`（通用回退）和`gated.py`（优化实现），保持公共API不变。
- **激活调度**：通过激活类型自动分发到优化内核，非gated激活（如`relu2`）仍走通用路径。
- **数据流优化**：在N64 FC1数据流中配对gate和up投影，减少中间暂存和累加器生命周期。
- **与项目方向一致**：FlashInfer专注于高性能GPU推理内核，此优化直接提升Blackwell架构上MoE模型的推理效率，符合项目“高性能”核心目标。

### 3. 对项目的影响和潜在意义
- **性能提升**：gated MoE是LLM推理中常见计算模式，配对分支可减少内存开销和延迟，尤其对SM12x（Blackwell）用户有显著收益。
- **易用性增强**：无需环境变量切换，通过激活类型自动选择最优路径，降低用户使用门槛。
- **架构演进**：为后续更多架构特定优化提供了模块化范式（拆分通用/专用路径），便于扩展。

### 4. 值得关注的技术点
- **分支配对调度**：将gate和up投影配对执行，缩短中间值生命周期，减少寄存器/共享内存压力。
- **激活公式复用**：GELU-tanh和SwiGLU-OAI复用规范公式，同时保持优化数据流，避免重复实现。
- **保留SiLU的PTX路径**：显式内联PTX倒数实现被保留，确保数值精度和性能平衡。
- **FC2保持非gated路径**：避免不必要的分支配对，保持执行路径简洁。

### 5. 对项目发展的影响
- **强化Blackwell支持**：FlashInfer持续针对最新GPU架构优化，此提交巩固了其在Blackwell上的竞争力，吸引高端推理用户。
- **模块化设计趋势**：拆分通用/专用路径为未来架构特定优化（如Hopper、Ampere）提供可复用模式，加速迭代。
- **生态吸引力**：自动调度减少用户配置负担，可能提升项目在LLM推理框架（如vLLM、SGLang）中的集成度，扩大社区影响力。

**总结**：这是一次针对Blackwell架构的精准性能优化，通过模块化拆分和分支配对调度，在不改变API的前提下显著提升gated MoE推理效率，同时为后续架构扩展奠定基础，符合FlashInfer“高性能GPU推理内核”的定位。

## 详细提交记录

### [553c228](https://github.com/flashinfer-ai/flashinfer/commit/553c2280a88581c7ede39aa571a54d1232854b81)

- **作者**: EricChen02
- **时间**: 2026-08-07T10:17:26Z
- **提交信息**: feat: optimize gated SM12x dynamic NVFP4 MoE (#4329)

Route gated activations through the optimized branch-paired dynamic
kernel while preserving the generic fallback for non-gated activations.
Support SiLU, GELU-tanh, and SwiGLU-OAI without an environment toggle.

<!-- .github/pull_request_template.md -->
## 📌 Description

This PR integrates an optimized branch-paired dynamic NVFP4 MoE kernel
for gated activations on Blackwell SM12x into the regular FlashInfer
CuTeDSL dispatch path.

### What changed

- Split the dynamic MoE implementation into:
  - `_moe_dynamic/generic.py`: the existing generic fallback.
  - `_moe_dynamic/gated.py`: the optimized gated implementation.
- Dispatch `silu`, `gelu_tanh`, and `swigluoai_uninterleave` to the
optimized gated kernel.
- Preserve the generic dynamic path for non-gated activations such as
`relu2`.
- Pair the gate and up projections in the N64 FC1 dataflow to reduce
staging and accumulator lifetimes.
- Preserve the tuned explicit inline-PTX reciprocal path for SiLU.
- Reuse the canonical activation formulas for GELU-tanh and SwiGLU-OAI
while keeping them on the optimized gated dataflow.
- Keep FC2 on the non-gated execution path.
- Keep the public `MoEDynamicKernel` API unchanged.
- Enable the optimized path through normal activation-based dispatch
without an environment-variable switch.

### Why

A gated MoE FC1 computes two projections:

```text
output = activation(gate_projection) * up_projection
```

The previous generic dynamic implementation handled the two branches
without exploiting their shared scheduling structure.

The new implementation pairs the gate and up branch work in the dynamic
N64 kernel. This shortens intermediate lifetimes and reduces staging
overhead while preserving the existing routing, NVFP4 quantization, FC2,
and scatter behavior.

The top-level activation dispatch selects the gated implementation. The
internal `is_gated` distinction is still required because the same
kernel object participates in both stages:

- FC1 is gated and uses the paired gate/up path.
- FC2 is not gated and continues to use the regular projection path.

### Correctness

Validated on an SM120 Blackwell GPU against the BF16 reference with:

```text
M = 384
H = 256
I = 512
E = 8
topk = 2
```

| Activation | Result | Finite output |
| --- | ---: | ---: |
| `silu` | 100% within the existing NVFP4 tolerance | Yes |
| `gelu_tanh` | 100% within the existing NVFP4 tolerance | Yes |
| `swigluoai_uninterleave` | 100% within the existing NVFP4 tolerance |
Yes |

No NaN or Inf values were observed.

Static validation also passed:

```text
ruff check
ruff format --check
python -m py_compile
```

### Performance

The benchmark compares this PR against the native FlashInfer CuTeDSL
implementation at the PR's current upstream base. No kernel overlay or
environment-variable kernel override was used.

Compared revisions:

- Upstream base: `d7e390c17844f493db23320cb7952375f03bc6c4`
- PR head: `594ca394c9328db582a689591392e13adcab092b`

Benchmark environment:

- GPU: NVIDIA RTX PRO 5000 72GB Blackwell, SM120
- PyTorch 2.11.0+cu130 and CuTeDSL 4.6.1
- CUDA Graph event timing
- 192 MiB L2 flush before every timed replay
- Warmup / iterations / repeats: 5 / 50 / 5
- 22 token-count points from M=1 to M=8192
- Qwen3.5-122B uses a 100-file routing trace replay
- Qwen3.5-35B and Qwen3.5-397B use seeded random unique top-k routing
- M<96 uses the existing static/micro backend; M>=96 uses the dynamic
backend changed by this PR

Both revisions were measured on the same GPU with the same benchmark
command and protocol. Each revision used an isolated JIT/cache
directory. Lower latency is better.

| Model configuration | M | Upstream native CuTeDSL (us) | This PR (us)
| Latency reduction |
| --- | ---: | ---: | ---: | ---: |
| Qwen3.5-35B TP1 | 4096 | 1012.692 | 586.782 | 42.06% |
| Qwen3.5-35B TP1 | 8192 | 1749.317 | 927.645 | 46.97% |
| Qwen3.5-122B TP2 | 4096 | 1461.020 | 938.726 | 35.75% |
| Qwen3.5-122B TP2 | 8192 | 2517.957 | 1441.407 | 42.75% |
| Qwen3.5-122B TP4 | 4096 | 932.632 | 639.082 | 31.48% |
| Qwen3.5-122B TP4 | 8192 | 1618.032 | 1027.254 | 36.51% |
| Qwen3.5-397B TP4 | 4096 | 1829.354 | 1626.127 | 11.11% |
| Qwen3.5-397B TP4 | 8192 | 3064.157 | 2453.747 | 19.92% |
| Qwen3.5-397B TP8 | 4096 | 1285.750 | 1112.290 | 13.49% |
| Qwen3.5-397B TP8 | 8192 | 2330.589 | 1856.785 | 20.33% |

Geometric-mean latency reduction across the sweep:

| Model configuration | All 22 M points | Dynamic path, M>=96 |
| --- | ---: | ---: |
| Qwen3.5-35B TP1 | 20.24% | 31.74% |
| Qwen3.5-122B TP2 | 17.12% | 27.17% |
| Qwen3.5-122B TP4 | 12.71% | 20.43% |
| Qwen3.5-397B TP4 | 3.88% | 6.49% |
| Qwen3.5-397B TP8 | 4.83% | 8.15% |

The static/micro M<96 subset changed by only -0.19% to +0.22% across the
five configurations, consistent with measurement noise on the unchanged
path. The larger full-sweep gains therefore come from the dynamic path
targeted by this PR.
## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Please pay particular attention to:

- The activation-based dispatch boundary between the generic and gated
implementations.
- The distinction between top-level gated-kernel selection and internal
FC1/FC2 `is_gated` behavior.
- SiLU's explicit inline-PTX reciprocal emission path.
- Correctness of the GELU-tanh and SwiGLU-OAI activation formulas inside
the optimized gated dataflow.

The non-gated fallback and public `MoEDynamicKernel` interface are
intentionally unchanged.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added dynamic fused Mixture-of-Experts support for Blackwell
SM120/SM121 GPUs.
* Added NVFP4 processing with routed-token packing, quantization, expert
computation, and weighted output scattering.
* Added support for gated and non-gated activations, including SiLU,
SwiGLU, ReLU2, GELU-tanh, and SwiGLU-OAI variants.
* Added configurable fast math, scaling, cross-expert input sharing, and
SwiGLU parameters.

* **Refactor**
  * Unified dynamic MoE kernel selection across activation types.
  * Added automatic fallback for unsupported shapes and configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: EricChen02 <EricChen02@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3933
- **最后更新**: 2026-08-07T13:16:02Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34256
- **最后更新**: 2026-08-07T20:15:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Sayak Paul

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于**测试修复**（Bug修复类别），具体针对torchao相关的测试用例进行修正，未涉及新功能或核心代码改动。

**2. 关键变更点及与项目方向的关系**  
- 修复了`torchao`集成测试中的失败问题，确保与PyTorch量化生态的兼容性测试稳定通过。  
- 这与diffusers项目“支持多样化硬件加速和量化方案”的方向一致，因为torchao是PyTorch官方的低精度计算库，用于优化推理性能。修复测试意味着维护者对量化路径的可靠性保持持续关注。

**3. 对项目的影响和潜在意义**  
- **直接意义**：消除CI（持续集成）中的不稳定因素，避免因测试失败阻塞其他PR合并，提升开发效率。  
- **间接意义**：保障用户在使用torchao量化功能时的体验，减少因底层库更新导致的兼容性回归风险，增强项目在边缘设备部署场景的可用性。

**4. 值得关注的技术点**  
- 测试修复往往反映底层依赖（如`torchao`）的API变动或行为变化，需关注其与diffusers的交互逻辑是否隐含潜在兼容性调整。  
- 提交由社区贡献者（dg845）协作完成，体现开源协作模式对项目质量保障的支撑。

**5. 对项目发展的影响（结合README背景）**  
- diffusers作为生成式AI模型库，核心目标是提供“易用、高效、可扩展”的推理工具。本次修复虽小，但维护了量化路径的稳定性，间接支持了项目在**资源受限环境**（如移动端、边缘设备）的部署愿景。  
- 持续修复测试也表明项目在快速迭代中重视质量门槛，为后续引入更复杂的量化策略（如混合精度、动态量化）奠定基础。  
- 整体上，这类“小步快跑”的维护性提交是项目长期健康发展的基石，确保核心功能在依赖生态演进中不退化。

**总结**  
本次提交是典型的测试维护工作，虽无用户可见的功能变化，但通过稳定torchao集成测试，保障了项目在量化部署场景的可靠性，与diffusers“高效推理”的长期目标一致，体现了开源项目对质量与兼容性的严谨态度。

## 详细提交记录

### [50e7158](https://github.com/huggingface/diffusers/commit/50e7158093710f9c1b4ea9ff100137a91c9228f3)

- **作者**: Sayak Paul
- **时间**: 2026-08-07T12:10:08Z
- **提交信息**: [tests] fix torchao tests (#14258)

fix torchao tests

Co-authored-by: dg845 <58458699+dg845@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 430
- **最后更新**: 2026-08-05T05:40:44Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12874
- **最后更新**: 2026-08-07T18:28:53Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 1
- **主要提交者**: Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 昨日提交分析

## 1. 主要更新类型

本次提交全部为**功能新增**，集中在视频生成与训练管线的能力扩展上，无Bug修复、性能优化或文档更新。

## 2. 关键变更点及与项目方向的关系

- **音频兜底支持**（b1c02ce）：当视频数据无音轨时，自动使用静音音频作为替代，避免因缺音轨导致处理失败。这完善了视频生成管线的鲁棒性。
- **无音频训练支持**（a5a54d8）：允许Minimax模型在无音频数据下进行训练，解耦了视频与音频的强绑定，扩大了训练数据适用范围。
- **Flash-Attention-4适配**（a13c094）：集成最新版Flash-Attention加速库，保持与前沿注意力计算优化同步。
- **FP8精度与纯视频加载**（4197824）：支持FP8低精度计算以降低显存占用，同时支持仅加载视频数据（不加载音频），进一步轻量化数据管线。

这些变更均围绕**视频生成管线的灵活性与效率**展开，与DiffSynth-Studio“一站式视频合成”的定位高度一致。

## 3. 对项目的影响和潜在意义

- **降低使用门槛**：音频兜底与无音频训练使开发者无需强制准备音频数据，简化了数据准备流程，尤其利好短视频、无声素材等场景。
- **扩大模型适用范围**：Minimax等模型可基于纯视频数据训练，拓展了训练数据来源，可能提升模型对视觉内容的专注度。
- **提升训练效率**：FP8支持与Flash-Attention-4适配，在保持精度的前提下降低显存需求并加速计算，使更大规模训练或消费级GPU训练成为可能。

## 4. 值得关注的技术点

- **FP8训练**：属于低精度训练前沿方向，需关注数值稳定性与收敛性，DiffSynth-Studio的实践可为社区提供参考。
- **Flash-Attention-4**：新版本可能引入新的内存访问模式或内核优化，适配工作需验证与现有模型的兼容性。
- **音频-视频解耦设计**：通过“静音兜底”和“纯视频加载”双路径，实现了音频作为可选模态的优雅处理，体现了模块化设计思想。

## 5. 对项目发展的影响

结合README，DiffSynth-Studio定位为面向创作者和开发者的高效视频合成工具，强调易用性与前沿技术集成。本次提交通过**降低数据门槛**和**提升训练效率**，直接强化了其“让视频生成更简单”的核心理念。FP8与Flash-Attention-4的适配表明项目持续跟进最新硬件与算法趋势，有助于保持技术领先性。无音频训练支持则可能吸引更多非传统视频领域（如动画、无声内容）的用户，扩大社区生态。整体来看，这些变更巩固了项目在视频生成工具链中的竞争力，并为后续更复杂的多模态功能（如音频条件生成）奠定了更灵活的基础架构。

## 详细提交记录

### [b1c02ce](https://github.com/modelscope/DiffSynth-Studio/commit/b1c02ce76aabc989f6bf534756b2da84532249e5)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-07T09:29:41Z
- **提交信息**: support using silent audio as a fallback when no audio track is present in the video data (#1575)

### [a5a54d8](https://github.com/modelscope/DiffSynth-Studio/commit/a5a54d83a964fcb30098d8b4baeb0fbfae97aa37)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-07T09:11:05Z
- **提交信息**: support training minimax without audio data (#1574)

### [a13c094](https://github.com/modelscope/DiffSynth-Studio/commit/a13c0946f7123d9445b938102286609ecb3182c0)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-07T07:31:20Z
- **提交信息**: support flash-attention-4 (#1573)

### [4197824](https://github.com/modelscope/DiffSynth-Studio/commit/419782458803b8cb53fa05e7bf2c8d60c62f57a7)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-07T07:08:08Z
- **提交信息**: support fp8 & load pure video (#1572)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31503
- **最后更新**: 2026-08-07T22:38:53Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 27
- **主要提交者**: Hanming Lu, Xiaoyu Zhang, Dmitrii Sergeev

## AI分析总结

# SGLang 昨日提交分析（40条提交）

## 一、主要更新类型

- **性能优化**（约15条）：CUDA graph 优化、logprobs 计算优化、checkpoint 加载加速等
- **Bug修复**（约10条）：EOS/Stop 处理、IndexError、off-by-one、溢出问题等
- **功能新增**（约8条）：Responses API、CUDA VMM 多模态、lingbot-video 模型支持等
- **Diffusion 专项**（约10条）：SANA/LTX-2/Z-Image 的 CUDA graph 加速、健康检查、分布式初始化修复
- **文档与CI**（约5条）：Kimi 镜像、Ascend NPU 文档、CI 测试矩阵优化
- **重构与清理**（约3条）：删除废弃组件、路由重构、诊断功能重做

## 二、关键变更点与项目方向

1. **Diffusion 模型支持大幅增强**：多条提交围绕 SANA、LTX-2、Z-Image 等模型的 CUDA graph 加速和分布式优化，端到端性能提升显著（如 LTX-2 提升 1.56x），表明项目正积极扩展多模态生成能力。
2. **硬件适配深化**：MXFP8 在 SM120 上改用 FlashInfer CUTLASS、DeepEP 安装方式更新、Ascend NPU 文档升级，体现对多硬件平台的支持策略。
3. **推理引擎核心优化**：FlashAttention 后端修复、prefill CP graph 溢出修复、Triton 诊断功能重做，持续强化核心推理路径的稳定性与可观测性。
4. **API 生态扩展**：Responses API 支持是重要功能新增，与 OpenAI 兼容生态对齐。

## 三、项目影响与潜在意义

- **性能提升显著**：多个端到端加速案例（H200 上 26%、1.56x 等），直接提升产品竞争力。
- **稳定性增强**：大量边界条件修复（off-by-one、溢出、IndexError）降低生产环境风险。
- **多模态战略推进**：Diffusion 相关提交占比约 25%，显示项目正从纯 LLM 推理向多模态生成平台演进。
- **开发者体验改善**：CI 矩阵优化、日志降噪、checkpoint 加载加速，降低开发和调试成本。

## 四、值得关注的技术点

1. **Breakable CUDA graph**：为 Diffusion 模型引入可中断的 CUDA graph，解决长序列生成中的显存和调度问题。
2. **FlashInfer CUTLASS 替代 Triton**：在特定硬件上放弃 Triton 路径，转向更底层的 CUTLASS 实现，追求极致性能。
3. **Logprobs 计算优化**：避免物化全词表 log-softmax，是推理引擎的经典优化技巧。
4. **DCP 拓扑路由重构**：通过 `get_parallel()` 统一路由，简化分布式配置管理。
5. **Speculative decoding 修复**：EOS/Stop 在 spec accept 运行中的优先级问题修复，保证生成正确性。

## 五、对项目发展的影响

结合 README 中 SGLang 作为高性能 LLM 推理框架的定位，这些提交表明项目正沿着**“性能极致优化 + 多模态扩展 + 多硬件适配”**三条主线快速发展。Diffusion 支持的大规模投入暗示项目目标已从纯文本生成扩展到图像/视频生成领域，而 MXFP8、NPU 等适配则巩固其作为通用推理引擎的地位。大量性能优化和 bug 修复保证了核心竞争力的持续领先，Responses API 等生态兼容工作则降低了用户迁移成本。整体来看，项目正处于功能丰富度和工程成熟度同步提升的快速成长期。

## 详细提交记录

### [eb3cc87](https://github.com/sgl-project/sglang/commit/eb3cc879e0cd417212e55680979d25c0ca44da36)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-07T22:38:44Z
- **提交信息**: Install DeepEP from release wheels (#33932)

### [115cd7b](https://github.com/sgl-project/sglang/commit/115cd7bde1b5e5b5d444a7bdd6c21b534f871bfe)

- **作者**: Faradawn Yang
- **时间**: 2026-08-07T22:26:07Z
- **提交信息**: docs: update checkpoint to Qwen3.5 NVFP4 V2 for InfX (#32945)

### [b2f9603](https://github.com/sgl-project/sglang/commit/b2f9603f93ea8ee3f921557c95e5a8c4c3ce720a)

- **作者**: Shiyan Deng
- **时间**: 2026-08-07T22:18:14Z
- **提交信息**: [bugfix] Stop/EOS inside a spec accept run beats the max_new_tokens finish (#33758)

Signed-off-by: Shiyan Deng <dsy842974287@meta.com>
Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>
Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: Hanming Lu <hanminglu@meta.com>

### [0729704](https://github.com/sgl-project/sglang/commit/07297049e941db1d8388832610bea870acb6bff5)

- **作者**: Khoa Pham
- **时间**: 2026-08-07T21:53:54Z
- **提交信息**: config: route DCP topology reads through get_parallel() (#33925)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [df3aa20](https://github.com/sgl-project/sglang/commit/df3aa20d89f343e34252f67d2db52d3a1b974bbc)

- **作者**: cctry
- **时间**: 2026-08-07T21:51:43Z
- **提交信息**: Reland serving-time Triton load diagnostics (#33908)

Co-authored-by: kangwangamd <100359556+kangwangamd@users.noreply.github.com>

### [8fc66d1](https://github.com/sgl-project/sglang/commit/8fc66d1a623561d9c5445f8f1f7bec1050e6710d)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-07T21:49:26Z
- **提交信息**: docker: pin Kimi images to SGLang commit (#34030)

### [0da25ee](https://github.com/sgl-project/sglang/commit/0da25ee6f79af3fbaf88cc5bfe540237f6e8fb07)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-07T21:46:51Z
- **提交信息**: Docs: Ling-3.0-flash cookbook — serve native 256K, drop YaRN override (#33882)

### [8600457](https://github.com/sgl-project/sglang/commit/860045773171abd4183780c7d5d7a6c706bb87c9)

- **作者**: Nan Jiang
- **时间**: 2026-08-07T21:42:30Z
- **提交信息**: [Spec] Propagate state capture outputs in DFlash (#34026)

### [9e3f6b7](https://github.com/sgl-project/sglang/commit/9e3f6b746b564882a08a24af044bb9be327817b6)

- **作者**: YAMY
- **时间**: 2026-08-07T21:31:48Z
- **提交信息**: fix(mamba): widen causal_conv1d token offsets to int64 (#33665)

### [b3ee679](https://github.com/sgl-project/sglang/commit/b3ee679467fbc0e423d893608fe5753f44e9dc67)

- **作者**: Brayden Zhong
- **时间**: 2026-08-07T21:30:43Z
- **提交信息**: [MXFP8] Use FlashInfer CUTLASS for dense GEMM on SM120, delete Triton path (#33208)

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

### [699fcdc](https://github.com/sgl-project/sglang/commit/699fcdc936c49c2a24fed3a0702a7c40b71c24d0)

- **作者**: Dmitrii Sergeev
- **时间**: 2026-08-07T21:06:48Z
- **提交信息**: Fix _pa_swa_prefill_lens off-by-one in FlashAttentionBackend (#33379)

### [62a2819](https://github.com/sgl-project/sglang/commit/62a28197c07169f774bb40b8450ed0b1ef10461c)

- **作者**: Sam Shleifer
- **时间**: 2026-08-07T21:06:05Z
- **提交信息**: Autotune flashinfer extend buckets at warmup (#32556)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [1480687](https://github.com/sgl-project/sglang/commit/1480687cff5a11c3b28fa8c952045ceb72f4cc4f)

- **作者**: Zhangheng
- **时间**: 2026-08-07T21:03:27Z
- **提交信息**: [CP]: Support CP V2 Strategy for dsv4 (#33532)

### [8e7d361](https://github.com/sgl-project/sglang/commit/8e7d361defe7d70b3e321ae6fcc8a01706b29933)

- **作者**: Sam Shleifer
- **时间**: 2026-08-07T21:01:08Z
- **提交信息**: [perf] Compute input logprobs without materializing the full-vocab log-softmax (#31958)

### [8a22b83](https://github.com/sgl-project/sglang/commit/8a22b8305d5993d6b5cf76d14f96df4b469afc35)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-07T20:50:44Z
- **提交信息**: docker: add Kimi K3 artifacts and build hpc-ops with C++20 (#33956)

### [b53a39c](https://github.com/sgl-project/sglang/commit/b53a39c5e4e3cbe59ad0d3ef68fae5d4aa2efef2)

- **作者**: Hanming Lu
- **时间**: 2026-08-07T20:41:19Z
- **提交信息**: Limit prefill delayer debug logs to rank zero (#34020)

Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>

### [7f6b4cb](https://github.com/sgl-project/sglang/commit/7f6b4cb94bdb9283740610930334ed9ef95c3626)

- **作者**: Oguz Ulgen
- **时间**: 2026-08-07T20:39:54Z
- **提交信息**: Add CUDA VMM multimodal feature transport (#33899)

Co-authored-by: Yinghai Lu <yinghai@meta.com>

### [3c51e29](https://github.com/sgl-project/sglang/commit/3c51e29debed99757a433d5e96f36f4dabb46734)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-07T20:21:46Z
- **提交信息**: Responses support (#32689)

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Harmya Bhatt <harmyacs@gmail.com>
Co-authored-by: harmya <harmya@modal.com>
Co-authored-by: Xinyuan <xinyuan@radixark.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [6c74981](https://github.com/sgl-project/sglang/commit/6c7498113f19c2cac9c4c0b2c20f4498b25f6bba)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-07T15:54:39Z
- **提交信息**: [diffusion] Enable breakable CUDA graph for SANA (H200 1024px e2e -26%, bit-exact) (#33989)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [12de7fb](https://github.com/sgl-project/sglang/commit/12de7fb1f65aeaae0757d94b50134a5d4e10d4ee)

- **作者**: Zhangheng
- **时间**: 2026-08-07T15:01:40Z
- **提交信息**: Remove the HiMambaRadixTree that is no longer in use (#33468)

### [d4be483](https://github.com/sgl-project/sglang/commit/d4be483efb2674385d39774232c11e4135217ea6)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-07T14:29:14Z
- **提交信息**: [diffusion] Enable breakable CUDA graph for LTX-2 (H200 two-stage e2e 10.75 s -> 6.90 s, 1.56x) (#33885)

### [bc148df](https://github.com/sgl-project/sglang/commit/bc148dfdc8478bcc438e5200eb5c12ad05d0c9bb)

- **作者**: Yifei Suo
- **时间**: 2026-08-07T13:33:23Z
- **提交信息**: [diffusion] feat: make scheduler rpc deadlines explicit (#33965)

Co-authored-by: suoyf <suoyf@nscc-tj.cn>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [bc8c037](https://github.com/sgl-project/sglang/commit/bc8c0370415547726d07081b05cfaabf9c65e306)

- **作者**: Ke Bao
- **时间**: 2026-08-07T12:45:19Z
- **提交信息**: Fix vae fast path test after the gate refactor (#33983)

### [4020bc9](https://github.com/sgl-project/sglang/commit/4020bc95a7b5b88b8de5f354f4850a9b1f881298)

- **作者**: danielafrimi
- **时间**: 2026-08-07T12:00:28Z
- **提交信息**: Fix Nemotron W4A16 NVFP4 MoE backend (#33543)

Signed-off-by: dafrimi <dafrimi@nvidia.com>

### [5ca734f](https://github.com/sgl-project/sglang/commit/5ca734fc3d0e314fb0b0993f9f7bbcd5a991bdb5)

- **作者**: Mick
- **时间**: 2026-08-07T11:23:30Z
- **提交信息**: [diffusion] UX: speed up tp and fsdp checkpoint loading (#33960)

### [1034977](https://github.com/sgl-project/sglang/commit/1034977318ea4f113142ba57f6fe7ac379e61630)

- **作者**: Dayananda V
- **时间**: 2026-08-07T11:01:58Z
- **提交信息**: [diffusion] fix: bind each rank to accelerator before distributed init (#33054)

### [acb64db](https://github.com/sgl-project/sglang/commit/acb64db9e27e8c6969fb1c69748e514d1375c68c)

- **作者**: Yihao Wang
- **时间**: 2026-08-07T11:01:05Z
- **提交信息**: [diffusion] fix: enable bcg with tp (#33421)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [fe52b49](https://github.com/sgl-project/sglang/commit/fe52b49827e6560692d0c6b7dff2a719f5731fde)

- **作者**: Dayananda V
- **时间**: 2026-08-07T10:58:04Z
- **提交信息**: Fix IndexError in Triton backend with pipeline parallelism (#30340)

Co-authored-by: Claude Sonnet 4.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [7af3d00](https://github.com/sgl-project/sglang/commit/7af3d000f294f230e3b277ceeb022aaf6e16147f)

- **作者**: Lennox Fu
- **时间**: 2026-08-07T09:59:23Z
- **提交信息**: [diffusion] feat: gate /health and /health_generate on warmup completion and add liveness endpoint (#33787)

Co-authored-by: Mick <mickjagger19@icloud.com>

### [a42683e](https://github.com/sgl-project/sglang/commit/a42683eb629b0aed12e34bd4f2d5a59c61098dc6)

- **作者**: Pan Li
- **时间**: 2026-08-07T09:57:01Z
- **提交信息**: [diffusion] model: support lingbot-video moe 30b t2v (#32341)

Signed-off-by: Pan Li <pandalee@ustc.edu>
Co-authored-by: Mick <mickjagger19@icloud.com>

### [13938fe](https://github.com/sgl-project/sglang/commit/13938fed3f06a8df06f23961bc338b911066dd61)

- **作者**: Mick
- **时间**: 2026-08-07T09:55:44Z
- **提交信息**: [diffusion] feat: make ring admission a backend capability (#33928)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [28b43bf](https://github.com/sgl-project/sglang/commit/28b43bf693a8d93d9241ef0a71a11eb245f6f3de)

- **作者**: Mick
- **时间**: 2026-08-07T09:55:15Z
- **提交信息**: [diffusion] perf: build qwen's masked varlen metadata host-side (#33954)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [0756a1d](https://github.com/sgl-project/sglang/commit/0756a1d2b070bb98f6c788c4c4c7346c68da164a)

- **作者**: Ke Bao
- **时间**: 2026-08-07T09:49:07Z
- **提交信息**: Move SWA chunk-cap hatch tests into the registered suite (#33975)

### [470807e](https://github.com/sgl-project/sglang/commit/470807ef746977b2e6a9170ffe72b3fd551e771f)

- **作者**: amote-i
- **时间**: 2026-08-07T09:45:00Z
- **提交信息**: [NPU] [DOC] Upgrade recommendeded sglang version on Ascend NPU (#33976)

### [572434e](https://github.com/sgl-project/sglang/commit/572434e2f6a855725fc4f56977f36f2e222ac939)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-07T09:03:28Z
- **提交信息**: [diffusion] Z-Image bit-exact fused qk-norm (H200 Turbo 1024px e2e -6.4%) (#33886)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5e60363](https://github.com/sgl-project/sglang/commit/5e60363960db96d56b519617d7a75be871f15a0e)

- **作者**: Baizhou Zhang
- **时间**: 2026-08-07T08:33:14Z
- **提交信息**: Fix prefill CP graph overflow with larger bucket search (#33906)

### [7395ee8](https://github.com/sgl-project/sglang/commit/7395ee833e61c62b8928bd2a6cab4b825313e2f1)

- **作者**: Liangsheng Yin
- **时间**: 2026-08-07T08:22:22Z
- **提交信息**: [CI] Share VLM engines and prune launch matrices on the per-commit H100/H200 suites (#33944)

### [3ed2a0a](https://github.com/sgl-project/sglang/commit/3ed2a0adf3d87b0f527c173a500dfb40d64b572f)

- **作者**: Trevor Morris
- **时间**: 2026-08-07T08:01:33Z
- **提交信息**: feat: Add flashinfer mHC fusion for DSV4 (#33616)

### [85d611a](https://github.com/sgl-project/sglang/commit/85d611a055a1503fe65fcf6dfccc2a3836e1aff4)

- **作者**: Mick
- **时间**: 2026-08-07T07:45:50Z
- **提交信息**: [diffusion] fix: scope the masked-path replicated guard to sp runs (#33953)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [5e58af1](https://github.com/sgl-project/sglang/commit/5e58af150339ca2f570cdbed523724f19eceafb2)

- **作者**: weireweire
- **时间**: 2026-08-07T07:45:07Z
- **提交信息**: Fix fractional simulated acceptance in DSpark (#33463)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1242
- **最后更新**: 2026-08-07T20:55:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88464
- **最后更新**: 2026-08-07T22:16:01Z

## 提交统计

- **昨日提交总数**: 40
- **提交者数量**: 34
- **主要提交者**: Michael Goin, Elvir Crnčević, haic0

## AI分析总结

# vLLM 昨日提交分析（第1/1批，共40条）

## 一、主要更新类型

本批提交涵盖**性能优化**（约10条）、**Bug修复**（约9条）、**新功能支持**（约7条）、**重构**（约4条）、**测试与CI改进**（约5条）、**平台适配**（ROCm/XPU相关约8条）等类型，整体呈现多维度并行推进态势。

## 二、关键变更点与项目方向

**性能优化方面**，多条提交聚焦DeepSeek系列模型：优化DSv3.2 eager CUDA graph区域、跳过短prefill topk计算（kernel延迟降低97.9%）、优化K3 dspark fused KV（4.5~4.6x性能提升）、将Blackwell CUDA graph捕获默认值提升至1024。这些优化直接服务于vLLM“快速、低成本”的核心目标，且针对当前最热门的开源模型进行深度调优。

**新功能方面**，引入在线MXFP4量化支持、NVFP4 KV cache scale搜索、MR v2权重卸载、磁盘卸载支持等，显著扩展了量化与内存管理能力，与项目“易用、便宜”的定位高度契合。

**平台适配**方面，大量ROCm相关提交（AITER MLA注册、MI325X配置、Qwen3.8支持、pinned memory等）表明AMD平台正成为重要支持目标，XPU平台也在积极跟进（Triton测试、量化UT修复）。

## 三、项目影响与潜在意义

本批提交体现了vLLM在**多硬件平台（NVIDIA/AMD/Intel/XPU）**、**多模型架构（DeepSeek/Qwen/Mistral/Mamba）**、**多量化方案（MXFP4/NVFP4/INT8/FP8）** 上的全面布局。特别是对DeepSeek系列模型的密集优化，反映出项目对前沿开源模型的快速响应能力。同时，MoE后端重构、Mamba attention重构等基础性工作为长期架构演进奠定基础。

## 四、值得关注的技术点

1. **在线MXFP4量化**：AMD主导的实时量化路径，对推理灵活性和显存效率有重要意义
2. **EPLB扩展至Mistral Large 3**：专家并行负载均衡能力增强，对MoE模型规模化部署关键
3. **NVML初始化修复**：避免重复初始化带来的性能开销，属于基础设施级优化
4. **PD（Prefill-Decode）分离架构持续完善**：包括prefix caching修复、远程连接清理、NixlPush优化等，表明该架构正走向成熟
5. **多模态路径加固**：Transformers建模后端多模态路径的强化，为多模态模型支持铺路

## 五、对项目发展的影响

结合README中“Easy, fast, and cheap LLM serving for everyone”的定位，本批提交从三个维度推动项目前进：**性能维度**通过kernel级优化和CUDA graph调优持续压低延迟；**易用性维度**通过量化支持扩展、平台适配和bug修复降低用户使用门槛；**架构维度**通过重构和PD架构完善确保长期可扩展性。特别是对AMD ROCm和Intel XPU的持续投入，正在将vLLM从NVIDIA专属工具转变为真正的多平台LLM服务框架，这对“for everyone”的目标至关重要。整体来看，项目正处于功能丰富期与性能深挖期并行的快速发展阶段。

## 详细提交记录

### [a801e71](https://github.com/vllm-project/vllm/commit/a801e71cb86ecd45cd8cb8f7d1bc08390f2bd68f)

- **作者**: Andrii Skliar
- **时间**: 2026-08-07T22:15:54Z
- **提交信息**: [Perf] Improve `--linear-backend` filtering (#48735)

Signed-off-by: Aleksandr Skliar <askliar@nvidia.com>
Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Aleksandr Skliar <askliar@nvidia.com>

### [46b5864](https://github.com/vllm-project/vllm/commit/46b58640541274334e2ee502a9c744841fb310b3)

- **作者**: Woosuk Kwon
- **时间**: 2026-08-07T21:37:43Z
- **提交信息**: [Perf] Narrow DeepSeek V3.2 eager CUDA graph region (#51425)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>

### [c8fe1d5](https://github.com/vllm-project/vllm/commit/c8fe1d5715a75a0e71712ec6717dd7ff71d1a8d0)

- **作者**: Michael Goin
- **时间**: 2026-08-07T21:07:55Z
- **提交信息**: [Spec Decode] Register Qwen3.6 dSpark acceptance coverage (#51310)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9823714](https://github.com/vllm-project/vllm/commit/9823714346164d9a15d6556eb3ee163d5e168cb9)

- **作者**: Nick Hill
- **时间**: 2026-08-07T20:49:00Z
- **提交信息**: [Bugfix] Drop stale layer kwarg from online MXFP4 kernel creation (fix precommit) (#51442)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [27d7303](https://github.com/vllm-project/vllm/commit/27d73038025599890772ffc288217a24d08a7953)

- **作者**: Jiangyun Zhu
- **时间**: 2026-08-07T20:45:29Z
- **提交信息**: [CI] Fix Batch Invariance (B200) (#51417)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [4a11ed5](https://github.com/vllm-project/vllm/commit/4a11ed5bc4c2f4e818e1e33010da160449d59159)

- **作者**: Wentao Ye
- **时间**: 2026-08-07T20:30:42Z
- **提交信息**: [DSv32/GLM Perf] Skip short prefill topk for dense mha layer, 97.9% kernel level latency reduction (#51298)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [99950b0](https://github.com/vllm-project/vllm/commit/99950b0b86463867bfaa210b7da56d7ce41eb35a)

- **作者**: Elvir Crnčević
- **时间**: 2026-08-07T20:29:59Z
- **提交信息**: [Profiler] Stamp vLLM version/commit into torch profiler trace metadata (#51389)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>

### [1c94e8d](https://github.com/vllm-project/vllm/commit/1c94e8dc7da43d12c8686f05cc5d2eab3fd9528f)

- **作者**: Wei-Ming Chen
- **时间**: 2026-08-07T20:22:27Z
- **提交信息**: Add NVFP4 KV 4-over-6 scale search (#45187)

Signed-off-by: weimingc <17592131+meenchen@users.noreply.github.com>

### [70456e5](https://github.com/vllm-project/vllm/commit/70456e5e6fb4ee86b8ffd985f918e44ba632d925)

- **作者**: Walter Beller-Morales
- **时间**: 2026-08-07T19:45:52Z
- **提交信息**: [Bugfix] when loading weights skip empty expert bias if model does not support them (#50937)

Signed-off-by: walterbm <walter.beller.morales@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [ac70ce9](https://github.com/vllm-project/vllm/commit/ac70ce96e0b9f69dd834bd1b0cd2d2b4c4a9db46)

- **作者**: Nick Hill
- **时间**: 2026-08-07T19:40:24Z
- **提交信息**: [Frontend] Disable uvicorn signal handlers instead of racing them (#50916)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [3518110](https://github.com/vllm-project/vllm/commit/3518110f2f4532c4605d8b1ea2a9bdc7d61b9f04)

- **作者**: fxmarty-amd
- **时间**: 2026-08-07T19:39:46Z
- **提交信息**: [Online quantization] Add online MXFP4 quantization support (#49347)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [a671679](https://github.com/vllm-project/vllm/commit/a671679e9f04742aecb2c9b35cd513a024c1321f)

- **作者**: Wentao Ye
- **时间**: 2026-08-07T19:20:21Z
- **提交信息**: [MRv2 Feature] MR v2 weight offloading support (#51413)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [021b7d9](https://github.com/vllm-project/vllm/commit/021b7d985b54264393b4c339f2823d783080942a)

- **作者**: Lucas Wilkinson
- **时间**: 2026-08-07T19:18:14Z
- **提交信息**: [Perf] Raise Blackwell CUDA graph capture default to 1024 (#49390)

### [56a4b63](https://github.com/vllm-project/vllm/commit/56a4b63d44c71784de75e6f2d6cbe28adf74635f)

- **作者**: Wentao Ye
- **时间**: 2026-08-07T19:16:11Z
- **提交信息**: [K3 Perf] Optimize k3 dspark fused kv, 4.5~4.6x kernel performance improvement (#50585)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0df620d](https://github.com/vllm-project/vllm/commit/0df620d429261fb4e3c1200c6b8414209587a86c)

- **作者**: coltonottley
- **时间**: 2026-08-07T19:11:09Z
- **提交信息**: [Test] Add packed DeepSeek-V4 KV zeroer geometry regression (#51288)

Signed-off-by: Colton Ottley <colton@ottleyengineering.com>
Co-authored-by: Colton Ottley <colton@ottleyengineering.com>

### [a0056e1](https://github.com/vllm-project/vllm/commit/a0056e103e214d5b0b73ca9e24003e09f8cbec63)

- **作者**: Aarushi Jain
- **时间**: 2026-08-07T19:07:31Z
- **提交信息**: [Test] Add ROCm AITER MLA op registration and env gating tests (#50930)

Signed-off-by: Aarushi Jain <aarushi@amd.com>
Co-authored-by: Aarushi Jain <aarushi@amd.com>

### [ebb2972](https://github.com/vllm-project/vllm/commit/ebb2972562bf05e949f7bbe73f496a2aeb5fdc25)

- **作者**: stefankoncarevic
- **时间**: 2026-08-07T18:55:34Z
- **提交信息**: [ROCm][CI][Bugfix] Do not microbatch a step that splits a prefix from its writer (#51402)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [4eccf90](https://github.com/vllm-project/vllm/commit/4eccf906ca8778bc02cb7549bab38e8b53cd9a90)

- **作者**: wangxiyuan
- **时间**: 2026-08-07T18:27:10Z
- **提交信息**: [Attention] Mamba attention module refactor - Final part (#44857)

### [45273b8](https://github.com/vllm-project/vllm/commit/45273b8dcbfb2d2c300c2f4a55c4dc283adca06a)

- **作者**: Harry Mellor
- **时间**: 2026-08-07T17:30:43Z
- **提交信息**: [1/N] Harden Transformers modelling backend multi-modal path (#51408)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [fcde8e1](https://github.com/vllm-project/vllm/commit/fcde8e1460589849c8142d617420ccdc406d5bc9)

- **作者**: Jinzhen Lin
- **时间**: 2026-08-07T17:03:19Z
- **提交信息**: [Refactor] refactor humming linear and moe backends to use explicit layer configs (#49610)

Signed-off-by: Jinzhen Lin <jinzhen.ljz@antgroup.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [e229fdb](https://github.com/vllm-project/vllm/commit/e229fdbc873b689bd9eb61559c4f8828b7e1a2f9)

- **作者**: vanshbhatia-amd
- **时间**: 2026-08-07T16:58:36Z
- **提交信息**: [ROCm] Add tuned selective_state_update float32 config for AMD Instinct MI325X (#50007)

Signed-off-by: vanshbhatia-amd <vansh.bhatia@amd.com>

### [34c1cd2](https://github.com/vllm-project/vllm/commit/34c1cd20a58e96f197d4b5927336a2d9facafa58)

- **作者**: Jack Hu
- **时间**: 2026-08-07T16:54:55Z
- **提交信息**: [Bugfix][ROCm] Fix ROCM_AITER_FA & ROCM_AITER_UNIFIED_ATTN QK-Norm+RoPE+KVCache fusion for the packed KV-cache [BLOCKS, HEADS, BLOCK_SIZE, 2*HEAD_DIM] layout (#49373)

Signed-off-by: Jack Hu <Jack.Hu@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7e85d3a](https://github.com/vllm-project/vllm/commit/7e85d3a42cc180d8b8fa85ca815c3e90bf2cb970)

- **作者**: Flora Cui
- **时间**: 2026-08-07T15:43:42Z
- **提交信息**: [ROCm] Enable pinned memory on supported WSL2 kernels (#50126)

Signed-off-by: Flora Cui <flora.cui@amd.com>

### [448344c](https://github.com/vllm-project/vllm/commit/448344c0e29383adfe606a5c7ede72dd74705321)

- **作者**: aoshen02
- **时间**: 2026-08-07T14:39:33Z
- **提交信息**: [Bugfix] Fix get_open_port() livelock on DP-reserved ports and cover get_open_ports_list (#50965)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Chenglun Hu <chenglunhu@gmail.com>
Co-authored-by: ferkans-amir <amir.rezaei@tu-berlin.de>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [47228db](https://github.com/vllm-project/vllm/commit/47228db84ce59321e6e464f20fabe0ef86e6aef5)

- **作者**: limeward
- **时间**: 2026-08-07T14:23:33Z
- **提交信息**: [Bugfix][KV-transfer] MoRIIO: per-layer READ-completion barrier in wait_for_layer_load (#48534)

Signed-off-by: Edwin Lim <edwin.lim@mangoboost.io>
Signed-off-by: Redwan Khan <redwan.khan@mangoboost.io>
Signed-off-by: harishk-mangoboost <harish.kambhampaty@mangoboost.io>
Signed-off-by: limeward <32970461+edwinlim0919@users.noreply.github.com>
Signed-off-by: QinPR <1905873179@qq.com>
Co-authored-by: Jaeyoun Kim <jaeyoun.kim@mangoboost.io>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
Co-authored-by: Redwan Khan <redwan.khan@mangoboost.io>
Co-authored-by: harishk-mangoboost <harish.kambhampaty@mangoboost.io>
Co-authored-by: rkhan055 <redwankhan055@gmail.com>
Co-authored-by: Peiran Qin <66068739+QinPR@users.noreply.github.com>
Co-authored-by: QinPR <1905873179@qq.com>

### [d4ecb75](https://github.com/vllm-project/vllm/commit/d4ecb75ba2f53a1e445cf5ac277ea8a5e78d516b)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-07T14:21:17Z
- **提交信息**: [PD][NixlPush][Bugfix] Fix prefix caching (#48758)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [f2bfad9](https://github.com/vllm-project/vllm/commit/f2bfad9167a29e963f29f9ea79f2811513566ea6)

- **作者**: haic0
- **时间**: 2026-08-07T13:19:07Z
- **提交信息**: [Model] Enable Qwen3.8 for AMD Rocm (#50068)

Signed-off-by: haic0 <haic0@users.noreply.github.com>
Signed-off-by: haic0 <haichzha@amd.com>

### [a231c5c](https://github.com/vllm-project/vllm/commit/a231c5ceac87451b6dcf5ccdf0eef7a3634bc5d4)

- **作者**: music-dino
- **时间**: 2026-08-07T12:55:50Z
- **提交信息**: [Bugfix] Skip fetching revision for model when model and weights_model are different (#51260)

Signed-off-by: Dino Music <Dino.Music@amd.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [d5aae2b](https://github.com/vllm-project/vllm/commit/d5aae2b4641c5091e604e235617e51e60a564710)

- **作者**: Xiaochang Wu
- **时间**: 2026-08-07T12:32:56Z
- **提交信息**: Fix ROCm architecture import on non-ROCm platforms (#51357)

Signed-off-by: Wu, Xiaochang <xiaochang.wu@intel.com>
Signed-off-by: Xiaochang Wu <xiaochang.wu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ae934ba](https://github.com/vllm-project/vllm/commit/ae934ba8a5577c580c33e3489290ff7d8bf1f83e)

- **作者**: Julien Debache
- **时间**: 2026-08-07T12:32:52Z
- **提交信息**: feat: extended EPLB support for Mistral Large 3 and additional MoE backends (#48355)

Signed-off-by: jdebache <jdebache@nvidia.com>

### [8d9b52f](https://github.com/vllm-project/vllm/commit/8d9b52f7c2514490bdadfd5eb0c931e58625df2e)

- **作者**: Yan Ma
- **时间**: 2026-08-07T10:25:31Z
- **提交信息**: [XPU] quick fix online quantization UT break (#51365)

Signed-off-by: Yan Ma <yan.ma@intel.com>

### [6b5bec7](https://github.com/vllm-project/vllm/commit/6b5bec7bedffa949fbd393fce720faf35831d746)

- **作者**: pmanczak
- **时间**: 2026-08-07T09:53:03Z
- **提交信息**: [Misc] Add and enable Triton kernel unit tests on XPU (#45694)

Signed-off-by: pmanczak <pmanczak@users.noreply.github.com>
Signed-off-by: pmanczak <pawel.manczak@intel.com>
Co-authored-by: pmanczak <pmanczak@users.noreply.github.com>

### [5ec47f3](https://github.com/vllm-project/vllm/commit/5ec47f3e48e7f6da9b6caa1c804b3887f832a788)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-07T09:43:29Z
- **提交信息**: [PD][PushConnector] Record last activity of remotes to allow clean up of stale ones (#50234)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4f76c8a](https://github.com/vllm-project/vllm/commit/4f76c8ad9d8ec06e91ac9c84895e07a1913d7726)

- **作者**: Sebastian Woo
- **时间**: 2026-08-07T08:30:00Z
- **提交信息**: [Bugfix][Platform] Stop re-initializing NVML on every device-capability check (fixes #50381) (#50393)

Signed-off-by: seewoo <seewoo@ucsc.edu>
Co-authored-by: Claude <noreply@anthropic.com>

### [b8db7f4](https://github.com/vllm-project/vllm/commit/b8db7f4abd2c864d5a7045b6d36fa36c2c7bb1e1)

- **作者**: Hank_
- **时间**: 2026-08-07T08:21:13Z
- **提交信息**: [Bugfix][Quantization] Fix dynamic INT8 W8A8 MoE config being built as W8A16 (#50833)

Signed-off-by: Hank <hcc.mayday@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [c84789c](https://github.com/vllm-project/vllm/commit/c84789c40b506a40d6a1ec15a704d53397c564a6)

- **作者**: Wentao Ye
- **时间**: 2026-08-07T08:20:19Z
- **提交信息**: [Refactor] Remove kernel dead code (#51051)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [da78833](https://github.com/vllm-project/vllm/commit/da788334bc0683cc44a58b4624e3f5a3c09a09e0)

- **作者**: jimmy-adams
- **时间**: 2026-08-07T08:19:31Z
- **提交信息**: Support DeepSeek-V4 AMD Quark NVFP4 with emulation kernel  (#47972)

Signed-off-by: Jimmy Adams <Adam_ji@outlook.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Signed-off-by: huji <huidong.ji@amd.com>
Signed-off-by: jimmy-adams <41593649+jimmy-adams@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: huji <huidong.ji@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [0de0362](https://github.com/vllm-project/vllm/commit/0de0362ea1c69b93f9ed36126a1b5c94f0ce2f22)

- **作者**: stefankoncarevic
- **时间**: 2026-08-07T08:19:26Z
- **提交信息**: [ROCm][CI] Loosen block-FP8 fused MoE test tolerance for large-K shapes (#48847)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [58fcaa0](https://github.com/vllm-project/vllm/commit/58fcaa0baaa32ba0c34e1119f6ce4554ef8a6256)

- **作者**: Guanyi Chen
- **时间**: 2026-08-07T07:37:47Z
- **提交信息**: [Feat][Core] Add disk offloading support to SimpleCPUOffloadConnector (#49644)

Signed-off-by: Guanyi Chen <939416532@qq.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [21ea5b4](https://github.com/vllm-project/vllm/commit/21ea5b4fa1062a379dd7e6795497ad6becd5a856)

- **作者**: Aaron Hao
- **时间**: 2026-08-07T07:35:59Z
- **提交信息**: [rl] Stateful Trainer Send: NCCL + Sparse NCCL [3/N] (#50902)

Signed-off-by: haoaaron <ahao@anyscale.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-08
**监控日期**: 2026-08-07
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5940
- **最后更新**: 2026-08-07T22:12:20Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 6
- **主要提交者**: NumberWan, dengyunyang, NATURE

## AI分析总结

### 主要更新类型
本次提交涵盖**功能新增**、**Bug修复**、**性能优化**和**CI改进**四类，无文档或纯重构内容。

### 关键变更点与项目方向
- **Batched Chat Completions（#5317）**：新增批量聊天补全接口，直接提升多模态模型服务的高吞吐场景能力，契合“Easy, fast, cheap”的定位，是面向规模化部署的关键功能。
- **Minimax-H3 动态加载/卸载（#5853）**：支持按需加载模型权重，配合Cache-DiT实现显存优化，强化了“cheap”目标，尤其适合多模型切换或资源受限环境。
- **FlashInfer 注意力刷新与量化支持（#5344）**：引入Blackwell架构的QK16/V8量化注意力，显著提升推理速度与显存效率，是“fast”路线的底层性能升级。
- **多个Bug修复**：包括`fa_deterministic`配置投影、Qwen-Image精度、Cache-DiT模块发现、图像数量检查等，主要保障CI稳定性和模型正确性，属于质量加固。

### 对项目的影响与潜在意义
- 批量接口和动态加载功能将扩大vllm-omni在**生产环境**的适用性，吸引更多需要高并发或灵活资源调度的用户。
- FlashInfer量化支持使项目在**最新硬件**上保持竞争力，为未来多模态大模型（如视频、3D）的推理效率奠定基础。
- CI修复虽不直接面向用户，但降低了维护成本，加速后续迭代节奏。

### 值得关注的技术点
- **Cache-DiT动态加载**：涉及模型权重与KV缓存的协同管理，是显存优化的前沿实践，可能成为后续多模态模型的标准特性。
- **Blackwell量化注意力**：QK16/V8方案在保持精度的同时大幅降低带宽需求，对长序列多模态输入（如视频）尤为重要。
- **批量补全的协议设计**：需兼容不同模态的输入格式，其实现方式可能影响未来API扩展。

### 对项目发展的影响
结合README强调的“人人可用的多模态服务”，这些提交从**功能丰富度**（批量、动态加载）、**性能上限**（量化注意力）和**稳定性**（CI修复）三个维度同步推进。短期看，它们巩固了vllm-omni作为多模态推理框架的实用性；长期看，动态加载和量化支持为处理更大规模、更多模态（如音频流、交互式生成）铺平了道路，符合“omni-modality”的愿景。整体上，本次提交是项目从“可用”迈向“高效且易扩展”的重要一步。

## 详细提交记录

### [b15d4e6](https://github.com/vllm-project/vllm-omni/commit/b15d4e6a64f80725a9b33e3fa4bba2fbf100d44c)

- **作者**: Alex Brooks
- **时间**: 2026-08-07T22:12:09Z
- **提交信息**: [Frontend] Implement Batched Chat Completions (#5317)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [18bf7e0](https://github.com/vllm-project/vllm-omni/commit/18bf7e0ff9310000c8c3b5d38e55727cbd94b2ee)

- **作者**: NumberWan
- **时间**: 2026-08-07T15:22:01Z
- **提交信息**: [BugFix][CI] Project fa_deterministic into OmniDiffusionConfig fields (#5897)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [cfa6d66](https://github.com/vllm-project/vllm-omni/commit/cfa6d66ed6aab7d763142bff0d9aa3489848f650)

- **作者**: NumberWan
- **时间**: 2026-08-07T09:15:22Z
- **提交信息**: [BugFix][Nightly CI] Opt in FA deterministic for Qwen-Image accuracy (#5887)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [d8c3566](https://github.com/vllm-project/vllm-omni/commit/d8c35663b47e54346062e6eac312e7b65bbb6829)

- **作者**: Mu GuanLin
- **时间**: 2026-08-07T09:07:23Z
- **提交信息**: [Model][Feat] Support Minimax-H3 quality grading requests through dynamic loading/unloading with Cache-DiT (#5853)

Signed-off-by: mglyn <1203789601@qq.com>

### [e906f41](https://github.com/vllm-project/vllm-omni/commit/e906f41dc8ea12cecdee85a59b62e1e488253d3b)

- **作者**: NATURE
- **时间**: 2026-08-07T09:02:42Z
- **提交信息**: [bugfix][CI] Fix Cache-DiT nested module discovery [issue 5879] (#5884)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [f114113](https://github.com/vllm-project/vllm-omni/commit/f11411340978a80fbec06d6d7ef389a6d84e697e)

- **作者**: dengyunyang
- **时间**: 2026-08-07T08:50:24Z
- **提交信息**: [Bugfix] Fix image num check error (#5838)

Signed-off-by: dengyunyang <584797741@qq.com>

### [ab459b3](https://github.com/vllm-project/vllm-omni/commit/ab459b36c26d5c7903f623156d88ab2ae06f0a97)

- **作者**: RuQing Xu
- **时间**: 2026-08-07T08:14:26Z
- **提交信息**: [Kernel] Refresh FlashInfer attention; Add quantized attention support (Blackwell QK16/V8) (#5344)

Signed-off-by: Ruqing Xu <7891482+xrq-phys@users.noreply.github.com>

---
