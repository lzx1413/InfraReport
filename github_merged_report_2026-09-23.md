# GitHub Stars 合并报告 - 2026-09-23

**合并日期**: 2026-09-24
**监控日期**: 2026-09-23
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


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2224
- **最后更新**: 2026-09-23T09:02:19Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: NancyFyong

## AI分析总结

### 1. 主要更新类型
**功能新增**。本次提交为项目添加了基于Hugging Face Hub的FlashAttention后端支持。

### 2. 关键变更点及其与项目整体方向的关系
- **关键变更**：在模型的注意力机制部分，集成了来自Hugging Face生态的高效FlashAttention实现。
- **与项目方向的关系**：VeOmni的核心目标之一是“以模型为中心的分布式训练配方”，旨在提升多模态大模型训练的效率与可扩展性。FlashAttention是一种通过优化内存访问模式来大幅提升Transformer模型训练与推理速度（尤其是长序列场景）的关键技术。本次集成为VeOmni的“配方库”提供了另一个高性能的基础设施组件，直接服务于其提升训练效率的核心使命。

### 3. 对项目的影响和潜在意义
- **直接影响**：为使用VeOmni进行模型训练的用户提供了新的、高效的注意力计算后端选项，可能显著降低特定模型（尤其是基于Transformer的多模态模型）的显存占用并提升计算速度。
- **潜在意义**：
    - **增强生态兼容性**：通过支持Hugging Face Hub，加强了与主流机器学习生态的集成，方便用户复用已有的模型或优化库。
    - **提升项目实用性**：提供了更多“即插即用”的性能优化组件，使VeOmni作为分布式训练框架更具吸引力和竞争力。
    - **推动性能边界**：有助于在更大规模或更复杂（如超长上下文）的多模态模型训练中实现更好的性能表现。

### 4. 值得关注的技术点
- **后端抽象与可插拔设计**：提交表明VeOmni的架构设计考虑了对不同计算后端（如此处新增的FlashAttention）的灵活支持，体现了其“配方库”模块化和可扩展的技术特点。
- **与Hugging Face Hub的集成**：这不仅仅是调用一个函数，可能涉及对模型权重加载、配置管理或与`transformers`库交互流程的适配，展示了项目在工程集成方面的考量。
- **FlashAttention的引入背景**：FlashAttention是目前优化大模型训练的核心技术之一，其集成意味着VeOmni能直接受益于该算法在减少IO访问、加速计算方面的理论收益。

### 5. 基于README了解的项目背景，这些提交如何影响项目发展
根据README，VeOmni致力于“扩展任何模态模型训练”，是一个面向未来的分布式训练框架。本次提交：
- **夯实性能基础**：通过引入业界领先的计算内核（FlashAttention），直接增强了框架的核心性能竞争力，使其更有可能在实际的大规模训练任务中被采纳。
- **完善“配方库”**：这正是README中“Model-Centric Distributed Recipe Zoo”理念的具体实践——不断扩充高效、可靠的底层技术组件，让用户可以根据模型和任务需求，灵活组合出最优的训练方案。
- **迈向生态化**：与Hugging Face生态的对接，暗示项目正从一个自成体系的工具，向更开放、更易用的平台演进，这有利于降低用户使用门槛，扩大社区影响力。

## 详细提交记录

### [c4e7db8](https://github.com/ByteDance-Seed/VeOmni/commit/c4e7db83d6ef3ee014638020aaefabcc2db13dd9)

- **作者**: NancyFyong
- **时间**: 2026-09-23T07:11:25Z
- **提交信息**: [ops, model] feat: add Hugging Face Hub FlashAttention backends (#1214)

Co-authored-by: Coach257 <45021066+Coach257@users.noreply.github.com>
Co-authored-by: NancyFyong <nancy@example.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2853
- **最后更新**: 2026-09-23T12:31:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bilang ZHANG

## AI分析总结

**1. 主要更新类型**
本次提交属于**文档更新**。具体是为项目添加了对“SwiftVR”工作的引用，不涉及功能代码、性能优化或错误修复。

**2. 关键变更点及其与项目整体方向的关系**
变更内容是在文档中增加了学术引用。这表明项目团队注重学术交流与认可，与其作为开源研究框架的定位相符。虽然不直接影响代码功能，但有助于丰富项目的学术生态和可追溯性。

**3. 对项目的影响和潜在意义**
*   **直接影响**：无功能性影响，属于文档完善工作。
*   **潜在意义**：增强了项目的学术严谨性与社区贡献认可度。通过引用相关工作，建立了与其他研究的联系，有助于提升项目在学术界和开源社区中的影响力。

**4. 值得关注的技术点**
*   提交中引用的“SwiftVR”可能是一项与视频生成或推理优化相关的技术。关注其具体贡献点，可能间接反映LightX2V项目的技术社区互动或潜在的技术路线参考。

**5. 基于项目背景对发展的影响**
LightX2V旨在打造轻量级视频生成推理框架。此类文档更新虽非核心技术推进，但对于构建活跃、健康的开源项目生态至关重要。它体现了项目维护者对社区规范（如尊重学术贡献）的遵循，有利于吸引更多研究者和开发者关注与参与，从而间接支持项目的长期发展。

## 详细提交记录

### [4ff8267](https://github.com/ModelTC/LightX2V/commit/4ff8267e7ca09a30dace323f3c024529de7d4a30)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-23T10:51:18Z
- **提交信息**: docs: add SwiftVR citation (#1553)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2255
- **最后更新**: 2026-09-22T13:06:43Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6498
- **最后更新**: 2026-09-24T00:16:06Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 12
- **主要提交者**: Brian K. Ryu, Ziming Wang, Zhejian Peng

## AI分析总结

FlashInfer仓库昨日的提交活动密集且方向明确，主要围绕扩展硬件与算法支持、提升性能与内核开发效率、以及强化项目工程结构三大核心展开，共同推进其成为覆盖前沿硬件的高性能GPU推理内核库的目标。

**主要更新与关键变更**
1.  **新硬件与量化格式支持**：为即将推出的NVIDIA Blackwell（SM120/SM100/SM103）和Rubin（SM107）架构，新增了针对NVFP4、MXFP8等新量化格式的融合计算内核（如W4A16、MiniMax-H3算子）。这直接扩展了项目在新硬件上的性能优势与覆盖范围。
2.  **内核性能优化与功能增强**：为Softmax、采样流程等关键算子提供了针对特定硬件架构的优化实现。新增了确定性模式（`top_k_renorm_probs`），解决了分布式推理中的结果一致性问题；并引入了融合投机解码内核，通过算子融合减少开销，提升端到端吞吐。
3.  **CuTe DSL后端扩展与重构**：广泛采用**CuTe DSL**作为新的内核开发后端，通过`backend="cute-dsl"`参数支持动态选择。同时对核心API进行了重构，统一分页解码入口，简化工作空间管理，清理冗余代码，使接口更清晰、一致且高性能。
4.  **工程与测试改进**：优化了CI测试策略，使用参数化积减少测试矩阵并区分测试模式，提升了效率与稳定性。修正了基准测试的验证标准，确保了性能评估的准确性。代码所有者信息和自审流程的更新则增强了项目治理。

**对项目的影响与潜在意义**
这些变更系统性地增强了FlashInfer的核心竞争力：
*   **技术前瞻性**：对Blackwell等新架构的提前支持，确保了项目在下一代GPU推理优化领域的领先地位。
*   **生产可靠性与性能**：确定性模式、融合投机解码内核等特性，直接提升了模型在大规模分布式部署中的结果可靠性和计算效率，使框架更适用于生产环境。
*   **开发效率与可维护性**：CuTe DSL的引入标志着内核开发范式向更高效的DSL演进。API重构和工程流程优化显著降低了内部复杂度，提升了代码质量和长期可维护性，为后续快速迭代奠定了基础。
*   **生态适用性**：更广泛的量化格式支持与动态后端选择机制，使FlashInfer能更灵活地满足不同模型在精度、性能和硬件适配上的差异化需求。

**值得关注的技术点**
*   **融合算子设计**：多个提交实现了将归一化、量化、线性层和激活函数深度融合的单内核，这是减少内存访问、突破性能瓶颈的关键。
*   **高性能开发模式**：CuTe DSL展示了其在编写和维护高性能CUDA内核方面的有效性。`plan()`/`run()`模式与`validate`参数的设计，体现了在灵活性和极致性能间的精心权衡。
*   **算法与系统创新**：通过整数原子操作实现确定性归一化；以及“行缓存集群”等新的Softmax计算模式，是解决GPU并行计算中非确定性与内存访问开销的精巧方案。

综上所述，昨日的提交从硬件支持、算法创新、内核开发范式到工程基础设施，对FlashInfer进行了全方位的增强与夯实，有力地支撑了其向高性能、全硬件覆盖的端到端推理解决方案演进的长期目标。

## 详细提交记录

### [ea728cb](https://github.com/flashinfer-ai/flashinfer/commit/ea728cb558c32a3c58ec8fbd5a154ff676b9ab70)

- **作者**: eigen
- **时间**: 2026-09-23T23:49:21Z
- **提交信息**: perf(cake_megamoe_topk_reduce): regenerate the SM100a reducer from the current Cake exporter (#5431)

## 📌 Description

Regenerate
`csrc/cake_megamoe_topk_reduce/cake_megamoe_topk_reduce_kernels.cu` and
its `manifest.json` from the current Cake exporter so the public bytes
are reproducible with the exporter's `--check` mode (internal tracking:
CAKE-551). The kernel is the same eight-warp, 256-thread BF16x4 SM100a
reducer shipped in #4819 under the unchanged one-symbol ABI
`kernel_cake_megamoe_workspace_topk_reduce_bfloat16_h4096_k6`, same
launch (`4 * num_tokens` CTAs, 256 threads, 0 dynamic smem), same
ordered no-FTZ `fma.rn.f32x2` accumulation.

What changed in the translation unit (boilerplate only; the kernel body
is identical):
- helper `#define`s (`CAKE_INF`, `NUM_MAIN_STAGES`, `THREADS`) now sit
next to the kernel and are `#undef`'d after it;
- the unused `warp`/`lane` locals use the shared `make_warp_uniform(tid
/ 32)` / `tid % 32` idiom;
- `#pragma unroll` formatting in an unused helper, and the unused
`mul_f32x2*` helper family gained a no-FTZ variant.

`manifest.json` `source_sha256` and
`flashinfer/jit/cake_megamoe_topk_reduce.py::_SOURCE_SHA256` move to
`3b83507e0d50dd5089389650c692fd4c17283ebe1f371a62ccb2a7d07b854dda`. No
API, binding header, or test change.

## 🔍 Related Issues

- #4727 (MegaMoE workspace capacities / terminal reducer)
- Follow-up to #4819

## 🧪 Tests

- [x] Cake-side: exporter `--check` reproduces these bytes;
`loom/tests/e2e/test_megamoe_topk_reduce_source_export.py` pins the
identity (CPU); NVRTC sm_100a compile and the B200
`megamoe_workspace_topk_reduce` slice — see validation notes below.
- [ ] `/bot run tests/moe_ep` (B200 CI:
`tests/moe_ep/test_mega_native_topk_reduce_multirank.py`,
`test_mega_workspace_api.py`)

Validation (Cake side, B200 `nsc-svg-slurm-1-gpu-112`, driver
580.82.07): exporter `--check` reproduces these exact bytes (sha256
`3b83507e…`); NVRTC `sm_100a` compile of this translation unit succeeds;
the generating Weave schedule passes the Cake B200 correctness slice
against the torch reference at BF16 `atol=rtol=1e-2`. The kernel body is
byte-identical to the #4819 drop; only the boilerplate listed above
changed.

## Reviewer Notes

The source is generated; please review the manifest/JIT pin and CI
rather than the `.cu` diff.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Performance**
- Improved numerical handling in the top-k reduction kernel by
preserving very small floating-point values during multiplication.
  - Streamlined GPU thread and warp identification for kernel execution.

- **Maintenance**
- Updated source integrity metadata to match the revised GPU
implementation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2f3bc5a](https://github.com/flashinfer-ai/flashinfer/commit/2f3bc5acff26e239696b57fe27d86af1624a8f86)

- **作者**: Stefano Castagnetta
- **时间**: 2026-09-23T23:29:52Z
- **提交信息**: Native-layout NVFP4 W4A16 in CuTe DSL on SM12x (#5242)

## 📌 Description

Add a CuTe DSL W4A16 backend for SM120/SM121 that consumes the same
packed NVFP4 weights and scales as W4A4, **without additional weight
preparation or a second weight copy**. Sharing one layout enables
serving frameworks to select W4A16 or W4A4 dynamically for each call,
using W4A16 where avoiding activation quantization helps and W4A4 where
its throughput is better.

Call it with `mm_bf16_fp4(..., backend="cute-dsl-native")`. It reads
canonical packed weights and 128x4-swizzled E4M3 scales directly; its
optional preparation API returns the original objects.

On **RTX PRO 6000 Max-Q (300 W), Qwen3.8-27B NVFP4**, native W4A16
achieves **1.348x versus CuTe W4A4 and 1.253x versus Marlin** for the
complete M=1 down operation. The associated dynamic vLLM policy reduces
time per output token by **6.6% to 7.2%** versus CuTe W4A4, with MTP
disabled. Kernel timing includes activation work and excludes
preparation. Serving uses a qualified W4A4 overlay.

For M > 16, the integrated staged kernel reuses decoded weights across
64/128 activation rows and tunes two tile traversal orders. Small-M
kernels and tactic menus are unchanged. General fallbacks retain support
for unaligned inputs and N/K tails. JIT, warmup and temporary split-K
scratch remain necessary.

Supports positive M/N, K divisible by 16, contiguous BF16 activations,
packed uint8 weights and BF16/FP16 output. Weights require 4-byte
alignment; scales use compact padded 128x4 layout. M*K, N*K and M*N must
each be below 2^31.

## Performance

### RTX PRO 6000 Max-Q (SM120): model-specific crossover

Qwen3.8-27B NVFP4, 300 W Max-Q. Complete down operation (SiLU/multiply
plus projection, including activation quantization for W4A4), with
preparation excluded. **Native W4A16 speedup = baseline time / native
time.** Measured source: job `2193605`, foundations and benchmark hash
below. The larger-M changes in `7baddbe` preserve the small-M kernels
and tactic menu. Prepared FlashInfer W4A16 was not measured in this
cohort.

Four balanced rounds of 200 CUPTI samples per provider/shape/round, CUDA
graphs and cold L2. Values are medians of four window medians. Synthetic
weights use the checkpoint dimensions: down N=5120/K=17408, gate/up
N=34816/K=5120, head N=248320/K=5120. This complete-operation comparison
has a different scope from the pure-GEMM Spark grid below.

| Down M | vs stock W4A4 | vs CuTe W4A4 | vs Marlin W4A16 |
| ---: | ---: | ---: | ---: |
| 1 | 1.305x | 1.348x | 1.253x |
| 4 | 1.217x | 1.264x | 1.170x |
| 8 | 1.265x | 1.312x | 1.221x |
| 16 | 1.197x | 1.236x | 1.178x |

<details>
<summary>All 12 Max-Q crossover shapes and speedups</summary>

| Projection | M | Native (us) | vs stock W4A4 | vs CuTe W4A4 | vs
Marlin W4A16 |
| --- | --- | --- | --- | --- | --- |
| down | 1 | 38.784 | 1.305x | 1.348x | 1.253x |
| down | 4 | 41.872 | 1.217x | 1.264x | 1.170x |
| down | 8 | 39.993 | 1.265x | 1.312x | 1.221x |
| down | 16 | 42.592 | 1.197x | 1.236x | 1.178x |
| gate_up | 1 | 70.225 | 0.987x | 0.996x | 1.050x |
| gate_up | 4 | 71.168 | 0.987x | 0.994x | 1.041x |
| gate_up | 8 | 74.008 | 0.964x | 0.966x | 1.005x |
| gate_up | 16 | 75.984 | 0.956x | 0.949x | 1.010x |
| head | 1 | 480.243 | 0.973x | 0.974x | 0.975x |
| head | 4 | 503.178 | 0.957x | 0.961x | 0.943x |
| head | 8 | 519.402 | 0.939x | 0.941x | 0.920x |
| head | 16 | 539.242 | 0.919x | 0.921x | 0.920x |

</details>

Foundations: FlashInfer `93e9eef092c11bc93a6f432a16404054e85d19c5`, vLLM
`2671fedfc7ae604761990603fc736c0c4f21de57`, with task overlays.
Benchmark SHA256:
`bb25bf1f8628f4f1690936c175e8494fa03dc500a414eaac3feb0a8577b92568`. The
associated four serving runs (`policy-2195415`) all report
`speculative_config=None`; they use down cutoff 1 and ordinary-linear
cutoff 0. Wins at M=4/8/16 here do not establish an MTP serving gain.

### DGX Spark (SM121): official shape grid

Spark SM121, native W4A16 at `7baddbe`. **All 159 shapes passed**,
including default and autotuned native execution, graph replay with
changed inputs/live alpha, and both prepared baselines.

**Speedup = baseline time / integrated-native time; higher is better.**
Preparation and tuning are excluded.

| Shapes | Speedup vs Marlin |
| --- | ---: |
| All 159 | 0.933x |
| M <= 16 (78) | 0.925x |
| M > 16 (81) | 0.941x |

Geometric means with equal weight per shape. Minimum speedup versus
Marlin is 0.758x; native wins 35/159 shapes against Marlin. Small-M code
and tactic menus are unchanged.

Pure BF16 x NVFP4 GEMM, without activation quantization or SiLU. Each
provider uses its public autotuner before fresh-input correctness and
two balanced rounds of 50 CUPTI samples, CUDA graphs and cold L2. All
outputs are checked against an independently dequantized FP32 reference
rounded to BF16 (atol=0.03, rtol=0.01). This grid measures SM121 kernel
performance; Max-Q operation results are reported separately above.

FlashInfer foundation: `93e9eef0`; vLLM/Marlin foundation: `2671fedf`.
Torch 2.13.0+cu130, CuTe DSL 4.7.1, driver 580.95.05.

<details>
<summary>All 159 shapes: absolute timings in microseconds and
speedups</summary>

| M | N | K | Integrated native (us) | Marlin (us) | Prepared FI (us) |
Speedup vs Marlin |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 512 | 7168 | 24.344 | 27.704 | 25.232 | 1.138x |
| 1 | 896 | 1024 | 6.928 | 10.032 | 9.585 | 1.448x |
| 1 | 896 | 5120 | 27.584 | 29.936 | 28.377 | 1.085x |
| 1 | 1024 | 7168 | 42.232 | 41.849 | 41.785 | 0.991x |
| 1 | 1280 | 8192 | 57.569 | 56.568 | 54.409 | 0.983x |
| 1 | 1792 | 5120 | 49.857 | 51.096 | 49.832 | 1.025x |
| 1 | 1856 | 2688 | 32.817 | 31.728 | 32.408 | 0.967x |
| 1 | 2560 | 8192 | 108.297 | 102.633 | 101.721 | 0.948x |
| 1 | 2688 | 1856 | 37.160 | 30.744 | 28.728 | 0.827x |
| 1 | 2688 | 3712 | 58.672 | 54.080 | 52.616 | 0.922x |
| 1 | 3584 | 5120 | 93.968 | 92.281 | 96.241 | 0.982x |
| 1 | 3712 | 2688 | 58.337 | 54.856 | 54.368 | 0.940x |
| 1 | 4608 | 7168 | 150.041 | 145.786 | 145.593 | 0.972x |
| 1 | 5120 | 640 | 22.280 | 22.128 | 21.816 | 0.993x |
| 1 | 5120 | 1024 | 30.392 | 32.360 | 33.096 | 1.065x |
| 1 | 5120 | 1280 | 35.720 | 38.368 | 39.752 | 1.074x |
| 1 | 5120 | 2048 | 57.441 | 56.104 | 60.416 | 0.977x |
| 1 | 5120 | 2560 | 68.312 | 69.320 | 73.537 | 1.015x |
| 1 | 5120 | 4096 | 103.520 | 104.320 | 105.745 | 1.008x |
| 1 | 5120 | 5120 | 125.409 | 125.241 | 125.601 | 0.999x |
| 1 | 5120 | 8192 | 179.825 | 170.049 | 168.241 | 0.946x |
| 1 | 5120 | 16384 | 290.506 | 271.219 | 262.618 | 0.934x |
| 1 | 7168 | 256 | 12.416 | 15.352 | 13.864 | 1.236x |
| 1 | 7168 | 512 | 21.720 | 25.152 | 24.537 | 1.158x |
| 1 | 7168 | 4608 | 149.961 | 146.281 | 144.273 | 0.975x |
| 1 | 7168 | 5120 | 162.441 | 158.466 | 153.561 | 0.976x |
| 1 | 8192 | 1024 | 45.168 | 46.832 | 47.672 | 1.037x |
| 1 | 8192 | 2048 | 82.857 | 86.840 | 84.593 | 1.048x |
| 1 | 8192 | 3584 | 138.961 | 136.538 | 133.906 | 0.983x |
| 1 | 8192 | 4096 | 150.417 | 147.185 | 147.457 | 0.979x |
| 1 | 8192 | 7168 | 218.570 | 212.377 | 207.570 | 0.972x |
| 1 | 8192 | 8192 | 244.722 | 231.938 | 224.050 | 0.948x |
| 1 | 8192 | 14336 | 375.651 | 355.675 | 341.138 | 0.947x |
| 1 | 8192 | 28672 | 685.943 | 637.293 | 609.949 | 0.929x |
| 1 | 9216 | 7168 | 236.890 | 226.962 | 220.194 | 0.958x |
| 1 | 10240 | 8192 | 287.899 | 267.938 | 266.514 | 0.931x |
| 4 | 512 | 7168 | 28.664 | 27.464 | 24.280 | 0.958x |
| 4 | 896 | 1024 | 9.232 | 10.128 | 11.032 | 1.097x |
| 4 | 1024 | 7168 | 45.264 | 42.488 | 41.465 | 0.939x |
| 4 | 4608 | 7168 | 167.393 | 146.402 | 143.433 | 0.875x |
| 4 | 7168 | 256 | 16.072 | 15.248 | 13.880 | 0.949x |
| 4 | 7168 | 512 | 27.624 | 24.816 | 23.408 | 0.898x |
| 4 | 7168 | 2304 | 99.353 | 86.201 | 83.993 | 0.868x |
| 4 | 7168 | 4608 | 167.082 | 146.849 | 142.233 | 0.879x |
| 4 | 9216 | 7168 | 269.282 | 227.202 | 217.850 | 0.844x |
| 8 | 896 | 5120 | 35.768 | 30.616 | 30.616 | 0.856x |
| 8 | 1280 | 8192 | 70.977 | 57.785 | 58.833 | 0.814x |
| 8 | 1792 | 5120 | 60.633 | 51.489 | 51.080 | 0.849x |
| 8 | 2560 | 8192 | 127.697 | 103.409 | 103.793 | 0.810x |
| 8 | 3584 | 5120 | 109.073 | 92.617 | 94.593 | 0.849x |
| 8 | 5120 | 640 | 26.592 | 22.209 | 21.608 | 0.835x |
| 8 | 5120 | 1024 | 36.849 | 32.736 | 30.200 | 0.888x |
| 8 | 5120 | 1280 | 44.680 | 38.304 | 35.720 | 0.857x |
| 8 | 5120 | 2048 | 69.561 | 56.160 | 53.240 | 0.807x |
| 8 | 5120 | 2560 | 83.432 | 70.017 | 65.232 | 0.839x |
| 8 | 5120 | 4096 | 121.577 | 106.033 | 106.041 | 0.872x |
| 8 | 5120 | 5120 | 141.945 | 125.833 | 123.313 | 0.886x |
| 8 | 5120 | 8192 | 206.002 | 170.425 | 161.034 | 0.827x |
| 8 | 5120 | 16384 | 333.979 | 270.914 | 258.947 | 0.811x |
| 8 | 7168 | 5120 | 180.609 | 157.265 | 152.705 | 0.871x |
| 8 | 8192 | 1024 | 58.105 | 47.368 | 44.961 | 0.815x |
| 8 | 8192 | 2048 | 100.081 | 87.376 | 82.376 | 0.873x |
| 8 | 8192 | 3584 | 157.602 | 137.089 | 130.297 | 0.870x |
| 8 | 8192 | 4096 | 172.329 | 147.705 | 145.009 | 0.857x |
| 8 | 8192 | 7168 | 250.298 | 212.137 | 205.314 | 0.848x |
| 8 | 8192 | 8192 | 283.074 | 232.850 | 219.874 | 0.823x |
| 8 | 8192 | 14336 | 435.156 | 356.548 | 335.787 | 0.819x |
| 8 | 8192 | 28672 | 807.232 | 642.382 | 605.245 | 0.796x |
| 8 | 10240 | 8192 | 335.899 | 268.699 | 262.219 | 0.800x |
| 16 | 512 | 7168 | 34.288 | 31.536 | 28.608 | 0.920x |
| 16 | 896 | 1024 | 11.272 | 11.024 | 11.168 | 0.978x |
| 16 | 1024 | 7168 | 55.344 | 45.360 | 47.408 | 0.820x |
| 16 | 4608 | 7168 | 171.545 | 148.754 | 144.737 | 0.867x |
| 16 | 7168 | 256 | 20.008 | 16.681 | 14.872 | 0.834x |
| 16 | 7168 | 512 | 31.441 | 26.480 | 23.984 | 0.842x |
| 16 | 7168 | 2304 | 102.769 | 87.056 | 87.817 | 0.847x |
| 16 | 7168 | 4608 | 172.921 | 147.522 | 144.041 | 0.853x |
| 16 | 9216 | 7168 | 276.859 | 229.370 | 222.874 | 0.828x |
| 64 | 512 | 7168 | 52.720 | 43.281 | 45.344 | 0.821x |
| 64 | 896 | 1024 | 17.544 | 17.152 | 12.112 | 0.978x |
| 64 | 896 | 5120 | 45.056 | 41.601 | 40.112 | 0.923x |
| 64 | 1280 | 8192 | 85.008 | 73.288 | 70.545 | 0.862x |
| 64 | 1792 | 5120 | 73.241 | 62.065 | 55.409 | 0.847x |
| 64 | 2560 | 8192 | 138.137 | 115.793 | 106.481 | 0.838x |
| 64 | 3584 | 5120 | 118.801 | 107.633 | 109.649 | 0.906x |
| 64 | 4608 | 7168 | 178.058 | 158.545 | 146.138 | 0.890x |
| 64 | 5120 | 640 | 34.088 | 34.856 | 26.368 | 1.023x |
| 64 | 5120 | 1024 | 44.048 | 46.849 | 33.593 | 1.064x |
| 64 | 5120 | 1280 | 52.817 | 52.953 | 40.257 | 1.003x |
| 64 | 5120 | 2048 | 77.424 | 69.921 | 56.720 | 0.903x |
| 64 | 5120 | 2560 | 92.417 | 84.000 | 70.577 | 0.909x |
| 64 | 5120 | 4096 | 129.353 | 118.657 | 104.353 | 0.917x |
| 64 | 5120 | 5120 | 150.482 | 136.905 | 123.760 | 0.910x |
| 64 | 5120 | 8192 | 216.762 | 183.090 | 165.089 | 0.845x |
| 64 | 5120 | 16384 | 350.723 | 292.795 | 269.426 | 0.835x |
| 64 | 7168 | 256 | 30.041 | 31.104 | 19.600 | 1.035x |
| 64 | 7168 | 512 | 43.489 | 41.280 | 29.145 | 0.949x |
| 64 | 7168 | 2304 | 119.865 | 99.641 | 94.489 | 0.831x |
| 64 | 7168 | 4608 | 189.833 | 156.657 | 156.609 | 0.825x |
| 64 | 7168 | 5120 | 196.745 | 167.617 | 159.866 | 0.852x |
| 64 | 8192 | 1024 | 68.393 | 62.744 | 50.880 | 0.917x |
| 64 | 8192 | 2048 | 107.809 | 100.873 | 88.881 | 0.936x |
| 64 | 8192 | 3584 | 171.386 | 146.929 | 136.233 | 0.857x |
| 64 | 8192 | 4096 | 181.458 | 157.370 | 150.345 | 0.867x |
| 64 | 8192 | 7168 | 264.474 | 222.746 | 215.586 | 0.842x |
| 64 | 8192 | 8192 | 304.370 | 246.002 | 235.754 | 0.808x |
| 64 | 8192 | 14336 | 472.948 | 382.220 | 370.964 | 0.808x |
| 64 | 8192 | 28672 | 881.817 | 677.079 | 686.743 | 0.768x |
| 64 | 9216 | 7168 | 293.403 | 242.978 | 235.826 | 0.828x |
| 64 | 10240 | 8192 | 362.149 | 295.291 | 272.603 | 0.815x |
| 128 | 1856 | 2688 | 58.648 | 56.969 | 45.432 | 0.971x |
| 128 | 2688 | 1856 | 56.425 | 53.360 | 42.465 | 0.946x |
| 128 | 2688 | 3712 | 85.545 | 81.032 | 69.160 | 0.947x |
| 128 | 3712 | 2688 | 84.361 | 79.969 | 72.761 | 0.948x |
| 256 | 512 | 7168 | 78.984 | 83.297 | 67.881 | 1.055x |
| 256 | 896 | 1024 | 25.088 | 27.928 | 20.552 | 1.113x |
| 256 | 1024 | 7168 | 115.737 | 101.033 | 97.017 | 0.873x |
| 256 | 4608 | 7168 | 270.331 | 232.066 | 223.090 | 0.858x |
| 256 | 7168 | 256 | 59.353 | 47.552 | 41.304 | 0.801x |
| 256 | 7168 | 512 | 66.785 | 66.480 | 52.272 | 0.995x |
| 256 | 7168 | 2304 | 161.889 | 154.578 | 131.929 | 0.955x |
| 256 | 7168 | 4608 | 278.259 | 259.786 | 245.314 | 0.934x |
| 256 | 9216 | 7168 | 443.884 | 580.653 | 408.340 | 1.308x |
| 512 | 896 | 5120 | 106.584 | 126.665 | 133.057 | 1.188x |
| 512 | 1280 | 8192 | 169.761 | 198.650 | 193.882 | 1.170x |
| 512 | 1792 | 5120 | 186.033 | 174.018 | 184.673 | 0.935x |
| 512 | 2560 | 8192 | 325.978 | 258.226 | 352.019 | 0.792x |
| 512 | 3584 | 5120 | 279.946 | 242.034 | 291.227 | 0.865x |
| 512 | 5120 | 640 | 93.657 | 82.401 | 74.377 | 0.880x |
| 512 | 5120 | 1024 | 116.089 | 103.161 | 95.529 | 0.889x |
| 512 | 5120 | 1280 | 132.521 | 118.521 | 111.073 | 0.894x |
| 512 | 5120 | 2048 | 183.578 | 166.778 | 156.985 | 0.908x |
| 512 | 5120 | 2560 | 215.322 | 199.754 | 188.001 | 0.928x |
| 512 | 5120 | 4096 | 313.730 | 288.635 | 282.779 | 0.920x |
| 512 | 5120 | 5120 | 375.836 | 348.226 | 347.482 | 0.927x |
| 512 | 5120 | 8192 | 568.317 | 514.469 | 545.420 | 0.905x |
| 512 | 5120 | 16384 | 1061.409 | 968.088 | 1092.825 | 0.912x |
| 512 | 7168 | 5120 | 517.500 | 487.356 | 482.100 | 0.942x |
| 512 | 8192 | 1024 | 163.897 | 149.945 | 134.921 | 0.915x |
| 512 | 8192 | 2048 | 264.682 | 259.354 | 228.698 | 0.980x |
| 512 | 8192 | 3584 | 410.212 | 410.996 | 375.499 | 1.002x |
| 512 | 8192 | 4096 | 460.532 | 462.644 | 447.476 | 1.005x |
| 512 | 8192 | 7168 | 750.238 | 840.343 | 724.791 | 1.120x |
| 512 | 8192 | 8192 | 857.496 | 949.952 | 838.919 | 1.108x |
| 512 | 8192 | 14336 | 1431.126 | 1597.463 | 1414.269 | 1.116x |
| 512 | 8192 | 28672 | 2984.222 | 3172.432 | 2809.147 | 1.063x |
| 512 | 10240 | 8192 | 1076.763 | 1498.095 | 1036.450 | 1.391x |
| 1024 | 512 | 7168 | 169.258 | 187.314 | 202.218 | 1.107x |
| 1024 | 896 | 1024 | 60.377 | 60.416 | 61.008 | 1.001x |
| 1024 | 1024 | 7168 | 245.858 | 271.771 | 267.691 | 1.105x |
| 1024 | 4608 | 7168 | 858.184 | 763.679 | 822.079 | 0.890x |
| 1024 | 7168 | 256 | 154.329 | 121.913 | 115.225 | 0.790x |
| 1024 | 7168 | 512 | 198.154 | 150.258 | 125.425 | 0.758x |
| 1024 | 7168 | 4608 | 879.767 | 803.119 | 823.190 | 0.913x |
| 1024 | 9216 | 7168 | 1630.545 | 2125.525 | 1577.528 | 1.304x |
| 2000 | 1856 | 2688 | 304.098 | 335.667 | 330.515 | 1.104x |
| 2000 | 2688 | 1856 | 323.523 | 313.923 | 360.523 | 0.970x |
| 2000 | 2688 | 3712 | 564.645 | 573.749 | 575.349 | 1.016x |
| 2000 | 3712 | 2688 | 588.061 | 583.884 | 595.901 | 0.993x |

</details>

## 🧪 Tests

SM121 validation covers **59 native tests, 117 backend-contract tests
and 15 trace tests**, plus **all 159 official shapes with default and
autotuned execution**. Coverage includes full-output references,
BF16/FP16 output, tails, alignment fallback, cold-L2 autotuning and
cache reuse for offset activation/weight/scale views, split-K, live
inputs/alpha in captured graphs and bitwise tile-traversal equivalence.

```bash
.venv/bin/python -m pytest tests/gemm/test_native_bf16_fp4.py -v
.venv/bin/python -m pytest tests/gemm/test_mm_bf16_fp4.py -k cute-dsl-native -v
.venv/bin/python -m pytest tests/trace/test_mm_bf16_fp4_reference_correctness.py -k native -v
```

## 🔍 Related Issues

[vLLM #54614](https://github.com/vllm-project/vllm/pull/54614) consumes
this backend;
[#5100](https://github.com/flashinfer-ai/flashinfer/pull/5100) supplies
W4A4 but is not required by this standalone PR. Duplicate checks found
no equivalent canonical-layout dense W4A16 proposal.

## 🚀 Pull Request Checklist

- [x] Pre-commit installed; changed-file hooks, GitHub pre-commit and
documentation build passed.
- [ ] Complete upstream GPU CI, which requires maintainer authorization.

AI assistance was used for implementation, experiments and drafting.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added the `cute-dsl-native` backend for BF16 × NVFP4 dense GEMM on
supported SM120/SM121 GPUs. It accepts canonical packed weights and
swizzled scales, supports BF16 or FP16 output, and includes backend
selection and autotuning support.
* Added trace export support for this backend, including preservation of
output-buffer dtype and scale-layout metadata.
* **Documentation**
* Added guidance on backend usage, supported configurations, and kernel
selection.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Stefano Castagnetta <scastagnetta@nvidia.com>

### [0f96675](https://github.com/flashinfer-ai/flashinfer/commit/0f96675312288fc87ef8132a05304521584186e3)

- **作者**: eigen
- **时间**: 2026-09-23T22:46:16Z
- **提交信息**: feat(cake_minimax_h3): SM120 FP8/NVFP4 fused MiniMax-H3 pre-attention (RTX 5090 / RTX PRO 6000) (#5493)

## Summary

Adds the SM120 (GB202: RTX 5090 / RTX PRO 6000 Blackwell) FP8 and NVFP4
**fused MiniMax-H3 pre-attention** requested in #4532 (candidate
`5090-K1`), tracked in #4254.

Two `sm_120a` launches per call: (1) RMSNorm + indexed AdaLN +
activation quantization (per-token E4M3, or block-16 NVFP4 with
`fp4_quantize` semantics), (2) a persistent `mma.sync` (`kind::f8f6f4` /
`kind::mxf4nvf4`) QKV GEMM 5376→21504 with the fused dequant → BF16 →
Q/K RMSNorm → 3-D RoPE epilogue writing Q/K/V `[M, 56, 128]` as BF16,
E4M3 (+ per-tensor descales) or NVFP4 (+ block-16 scales).

## API

```python
from flashinfer.diffusion_ops import (
    minimax_h3_fp8_pre_attention, minimax_h3_nvfp4_pre_attention,
    quantize_minimax_h3_qkv_weight_fp8, quantize_minimax_h3_qkv_weight_nvfp4,
)
```

- `csrc/cake_minimax_h3_sm120_quant_pre_attention_sm120a.cu` — generated
device code + TVM-FFI host (tensor-map encoding, launch plan).
- `flashinfer/jit/cake_minimax_h3_sm120_quant_pre_attention.py`,
`flashinfer/diffusion_ops/cake_minimax_h3_sm120_quant_pre_attention.py`
— JIT spec and route (`@supported_compute_capability([120])`).
- `tests/diffusion_ops/test_minimax_h3_sm120_quant_pre_attention.py`,
`benchmarks/bench_minimax_h3_sm120_quant_pre_attention.py`, docs entry.

## Results (complete operator, CUPTI cold-L2 medians; correctness vs the
exact emulation of the quantized operands, 36/36 shapes per device)

**RTX PRO 6000 Blackwell Server Edition (96 GB, 188 SMs)**

| variant | out | M | fused ms | best baseline chain ms (backend) |
speedup | bare GEMM ms (backend) | fused peak GiB | status |
|---|---|---|---|---|---|---|---|---|
| fp8 | bf16 | 33472 | 11.79 | 36.59 (torch_scaled_mm_rowwise) | 3.10x |
10.66 (torch_scaled_mm_rowwise) | 2.28 | correct |
| fp8 | bf16 | 38592 | 13.62 | 42.31 (torch_scaled_mm_rowwise) | 3.11x |
12.39 (torch_scaled_mm_rowwise) | 3.98 | correct |
| fp8 | bf16 | 48768 | 17.35 | 53.57 (torch_scaled_mm_rowwise) | 3.09x |
15.67 (torch_scaled_mm_rowwise) | 4.74 | correct |
| fp8 | bf16 | 58944 | 21.02 | 64.93 (torch_scaled_mm_rowwise) | 3.09x |
19.07 (torch_scaled_mm_rowwise) | 5.71 | correct |
| fp8 | bf16 | 74240 | 26.76 | 81.98 (torch_scaled_mm_rowwise) | 3.06x |
24.10 (torch_scaled_mm_rowwise) | 6.97 | correct |
| fp8 | bf16 | 109952 | 39.83 | 121.99 (torch_scaled_mm_rowwise) | 3.06x
| 35.93 (torch_scaled_mm_rowwise) | 9.56 | correct |
| nvfp4 | bf16 | 33472 | 7.07 | 27.49 (flashinfer_mm_fp4_b12x) | 3.89x |
5.88 (flashinfer_mm_fp4_b12x) | 2.06 | correct |
| nvfp4 | bf16 | 38592 | 8.15 | 31.90 (flashinfer_mm_fp4_auto) | 3.91x |
6.84 (flashinfer_mm_fp4_cutlass) | 3.74 | correct |
| nvfp4 | bf16 | 48768 | 10.33 | 40.52 (flashinfer_mm_fp4_cutlass) |
3.92x | 8.62 (flashinfer_mm_fp4_cutlass) | 4.49 | correct |
| nvfp4 | bf16 | 58944 | 12.51 | 49.08 (flashinfer_mm_fp4_cutlass) |
3.92x | 10.44 (flashinfer_mm_fp4_cutlass) | 5.44 | correct |
| nvfp4 | bf16 | 74240 | 15.80 | 61.95 (flashinfer_mm_fp4_cutlass) |
3.92x | 13.13 (flashinfer_mm_fp4_cutlass) | 6.66 | correct |
| nvfp4 | bf16 | 109952 | 23.40 | 92.21 (flashinfer_mm_fp4_cutlass) |
3.94x | 19.44 (flashinfer_mm_fp4_cutlass) | 9.17 | correct |
| fp8 | e4m3 | 38592 | 13.87 | 58.02 (torch_scaled_mm_rowwise) | 4.18x |
12.81 (torch_scaled_mm_rowwise) | 1.79 | correct |
| fp8 | nvfp4 | 38592 | 13.97 | 44.26 (torch_scaled_mm_rowwise) | 3.17x
| 12.85 (torch_scaled_mm_rowwise) | 2.30 | correct |
| nvfp4 | e4m3 | 38592 | 7.98 | 47.32 (flashinfer_mm_fp4_b12x) | 5.93x |
6.80 (flashinfer_mm_fp4_cutlass) | 1.85 | correct |
| nvfp4 | nvfp4 | 38592 | 8.10 | 33.54 (flashinfer_mm_fp4_auto) | 4.14x
| 6.84 (flashinfer_mm_fp4_cutlass) | 2.32 | correct |

**RTX 5090 (32 GB, 170 SMs)**

| variant | out | M | fused ms | best baseline chain ms (backend) |
speedup | bare GEMM ms (backend) | fused peak GiB | status |
|---|---|---|---|---|---|---|---|---|
| fp8 | bf16 | 33472 | 17.85 | 40.19 (flashinfer_bmm_fp8_cublas) | 2.25x
| 15.99 (flashinfer_bmm_fp8_cublas) | 2.28 | correct |
| fp8 | bf16 | 38592 | 20.63 | 46.62 (torch_scaled_mm_tensorwise) |
2.26x | 18.65 (torch_scaled_mm_tensorwise) | 3.98 | correct |
| fp8 | bf16 | 48768 | 26.35 | 58.44 (flashinfer_bmm_fp8_cublas) | 2.22x
| 22.61 (flashinfer_bmm_fp8_cublas) | 4.74 | correct |
| fp8 | bf16 | 58944 | 31.92 | 71.95 (torch_scaled_mm_tensorwise) |
2.25x | 29.02 (torch_scaled_mm_tensorwise) | 5.71 | correct |
| fp8 | bf16 | 74240 | 41.31 | 89.67 (flashinfer_bmm_fp8_cublas) | 2.17x
| 35.04 (flashinfer_bmm_fp8_cublas) | 6.97 | correct |
| fp8 | bf16 | 109952 | 61.29 | OOM | n/a | 52.67
(torch_scaled_mm_tensorwise) | 9.56 | correct |
| nvfp4 | bf16 | 33472 | 7.40 | 27.32 (flashinfer_mm_fp4_cutlass) |
3.69x | 6.35 (flashinfer_mm_fp4_cutlass) | 2.06 | correct |
| nvfp4 | bf16 | 38592 | 8.57 | 31.61 (flashinfer_mm_fp4_cudnn) | 3.69x
| 7.43 (flashinfer_mm_fp4_cudnn) | 3.74 | correct |
| nvfp4 | bf16 | 48768 | 11.15 | 40.12 (flashinfer_mm_fp4_cudnn) | 3.60x
| 9.46 (flashinfer_mm_fp4_cudnn) | 4.49 | correct |
| nvfp4 | bf16 | 58944 | 13.55 | 48.72 (flashinfer_mm_fp4_cutlass) |
3.60x | 11.62 (flashinfer_mm_fp4_cudnn) | 5.44 | correct |
| nvfp4 | bf16 | 74240 | 17.53 | 61.73 (flashinfer_mm_fp4_cutlass) |
3.52x | 15.06 (flashinfer_mm_fp4_cutlass) | 6.66 | correct |
| nvfp4 | bf16 | 109952 | 26.47 | OOM | n/a | 22.35
(flashinfer_mm_fp4_cudnn) | 9.17 | correct; baseline memory_limited (OOM
on this device) |
| fp8 | e4m3 | 38592 | 21.39 | 61.74 (flashinfer_bmm_fp8_cublas) | 2.89x
| 19.16 (flashinfer_bmm_fp8_cublas) | 1.79 | correct |
| fp8 | nvfp4 | 38592 | 21.10 | 48.51 (torch_scaled_mm_tensorwise) |
2.30x | 19.24 (torch_scaled_mm_tensorwise) | 2.30 | correct |
| nvfp4 | e4m3 | 38592 | 8.94 | 46.55 (flashinfer_mm_fp4_cudnn) | 5.21x
| 7.75 (flashinfer_mm_fp4_cudnn) | 1.85 | correct |
| nvfp4 | nvfp4 | 38592 | 8.96 | 33.38 (flashinfer_mm_fp4_cutlass) |
3.73x | 8.04 (flashinfer_mm_fp4_cutlass) | 2.32 | correct |

Baselines are the fastest same-device segmented chains: torch
norm/AdaLN/quant + `torch._scaled_mm` row-wise (FP8) or FlashInfer
`mm_fp4` (best of cutlass/cudnn/b12x/auto) + torch Q/K RMSNorm/RoPE. At
M = 109952 the segmented baselines run out of memory on the 32 GB RTX
5090 (`memory_limited`); the fused operator fits.

FlashInfer route validation on both GPUs: **RTX 5090**:
`tests/diffusion_ops/test_minimax_h3_sm120_quant_pre_attention.py` 18/18
passed (this source JIT-compiled on top of the released 0.7.0 wheel);
`benchmarks/bench_minimax_h3_sm120_quant_pre_attention.py` (CUPTI, cold
L2) NVFP4 6.90 / 8.45 ms vs 27.15 / 31.44 ms for the segmented
`fp4_quantize` + `mm_fp4` chain (3.94x / 3.72x), FP8 17.58 / 20.35 ms vs
45.90 / 52.92 ms for the `torch._scaled_mm` chain (2.61x / 2.60x) at M =
33472 / 38592; fused peak memory 2.2-2.6 GiB vs 7.3-8.5 GiB. **RTX PRO
6000 Blackwell Server Edition**:
`tests/diffusion_ops/test_minimax_h3_sm120_quant_pre_attention.py` all
18 tests passed (pytest exit 0, same overlay on the released 0.7.0
wheel); benchmark (CUPTI, cold L2) NVFP4 6.49 / 7.74 ms vs 27.50 / 31.64
ms for the segmented `fp4_quantize` + `mm_fp4` chain (4.24x / 4.09x),
FP8 11.68 / 13.42 ms vs 37.20 / 42.92 ms for the `torch._scaled_mm`
chain (3.19x / 3.20x) at M = 33472 / 38592; fused peak memory 2.3-2.7
GiB vs 7.4-8.5 GiB.

## Notes

- SP1 only (no Ulysses relayout). SGLang / Sol Engine integration
belongs to the requester.
- TMA `.multicast::cluster` was measured at ~100 ms per operation on
GB202 (functionally correct, unusable), so the kernel deliberately loads
every operand per CTA.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused MiniMax-H3 pre-attention operations for FP8 and NVFP4 on
supported Blackwell GPUs, with BF16, E4M3, and NVFP4 output options.
* Added utilities for quantizing QKV weights and deriving quantization
scales.
* **Documentation**
* Expanded the diffusion operations API reference with the new
MiniMax-H3 operations.
* **Tests**
* Added coverage for quantization modes, output formats, varied input
sizes, and invalid inputs.
* **Benchmarks**
* Added a benchmark comparing fused operations with PyTorch and
FlashInfer baselines.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5c586da](https://github.com/flashinfer-ai/flashinfer/commit/5c586da4dc31f7bad97f02e1965015861c9cf1a7)

- **作者**: Haozheng Fan
- **时间**: 2026-09-23T21:56:52Z
- **提交信息**: feat(cake_mega_moe): add CuTe DSL backend for experimental MXFP8 MegaMoE EP16 (#5433)

## 📌 Description

Add an explicit CuTe-DSL backend to the experimental MXFP8 MegaMoE EP16
session, allowing callers to select an alternative implementation
through the
existing API. CUDA remains the default; there is no automatic selection
or
fallback.

### API

```python
weights = preprocess_cake_mxfp8_megamoe_ep16_weights(w13, w2)
session = CakeMxfp8MegaMoeEp16(weights, topk_ids, backend="cute_dsl")
output = session.run(
    hidden_states, topk_ids, topk_weights, out=session.workspace_output
)
```

Omitting `backend`, or using `backend="cuda"`, retains the existing
path.
All ranks must choose the same backend; agreement is checked
collectively
before symmetric workspace allocation. CuTe dependencies are loaded
lazily.

The supported contract remains 16 expert-parallel ranks, 512 experts,
top-k 8,
hidden size 3072, intermediate size 5120, and 16/32/64 tokens per rank,
with
BF16 activations and MXFP8 weights. Routing is fixed when the session is
created, with at most 64 routes per expert. Exact SM103a and NVSHMEM are
required. Calls on one session must be serialized on one stream; CUDA
Graph
capture is not supported.

### Export

The experimental package includes three generated CuTe-DSL kernel
sources:
two fused variants and the route reducer. A host adapter connects them
to the
existing session and FlashInfer's CuTe JIT cache. Compilation, workspace
allocation, and tensor-map metadata preparation belong to session setup.
Each forward submits the fused computation and route reduction without
allocating device storage. Cache keys include the kernel and adapter
sources.
This backend is JIT-only and is not registered for AOT packaging.

### Validation

Added CPU tests for backend selection, lazy imports, peer argument
validation,
source-cache invalidation, and the example's rank-to-device selection.
The
EP16 test is configured for both backends at all three supported token
counts,
using the existing analytical reference and tolerances. It performs 32
forwards per session with paired changing inputs to check repeated
results
and synchronization-bank reuse. The runnable example accepts
`--backend cute_dsl`.

CPU validation: **62 passed**, with the two multi-GPU tests deselected.
Ruff 0.12.8 lint and formatting checks pass for the changed Python
files.
The formatted generated sources retain the same Python AST as the
exports.
Public-path JIT compilation and both EP16 GPU tests passed on 16 GB300
GPUs:
default CUDA and CuTe DSL, each covering 16/32/64 tokens per rank and 32
forwards per session. All 16 ranks passed with zero failures or skips.
A fresh 16-rank process also passed the CuTe test with JIT disabled,
loading
all three kernels from persistent cache with unchanged artifacts.
The CuTe EP16 test passed synccheck on all 16 ranks.
Single-pass racecheck completed on all 16 ranks at 16/32/64 tokens per
rank,
covering both generated fused variants and the top-k reducer. All logs
reported zero errors and zero warnings, but the sanitizer returned a
nonzero
exit code with kernel-launch dumping enabled; this is not counted as a
passing sanitizer gate.

### Performance

On 16 NVIDIA GB300 GPUs, across six EP16 cases (16/32/64 tokens per
rank,
balanced and hotset routing), CuTe DSL was faster than CUDA in every
case in
each of three fresh-process trials (CUDA/CuTe latency ratio:
1.053–1.077×).
Measurements use CUPTI activity tracing with cold L2, excluding
compilation
and setup. Each trial includes 32 correctness replays per backend and
three
interleaved measurement blocks.

The table shows the range of per-trial GPU-span medians, in
microseconds.
Every case was evaluated separately in each trial; results were not
pooled
across trials.

| Tokens/rank | Routing | Default CUDA (µs) | CuTe DSL (µs) |
| --- | --- | ---: | ---: |
| 16 | Balanced | 702.2–702.6 | 661.7–666.7 |
| 32 | Balanced | 721.0–722.4 | 675.0–676.7 |
| 64 | Balanced | 736.0–738.4 | 692.9–699.0 |
| 16 | Hotset | 706.8–708.9 | 662.3–665.4 |
| 32 | Hotset | 717.8–723.8 | 670.8–676.1 |
| 64 | Hotset | 770.8–775.9 | 730.1–732.6 |

The benchmark harness performed collective NVSHMEM cleanup after
measurement;
all trial processes exited normally. Saved outputs and raw timings were
independently rechecked.

## 🔍 Related Issues

Tracking:
[#4969](https://github.com/flashinfer-ai/flashinfer/issues/4969).

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #4969.
- [x] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [x] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [x] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [x] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

```experimental-tests
tests/experimental/test_cake_mxfp8_megamoe_ep16.py
```

## Reviewer Notes

Please review the default-backend compatibility, collective backend
agreement,
descriptor/peer metadata binding, and cache-key dependency coverage.
Remaining
validation is listed above.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added an optional CuTe-DSL backend for the EP16 Cake MXFP8 MegaMoE
session. CUDA remains the default; all ranks must select the same
backend.
* Updated the example to support launching with either backend and
report the selected backend and output shape.

* **Bug Fixes**
* Improved distributed setup checks for rank metadata, GPU requirements,
process-group size, and backend consistency.

* **Documentation**
* Added backend selection, requirements, supported behavior, and example
commands to the EP16 guide.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e838a85](https://github.com/flashinfer-ai/flashinfer/commit/e838a8585bdc33b128d451e4e46d77f2494d4521)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-23T21:36:35Z
- **提交信息**: chore: add jimmyzho to gemm codeowners (#5505)

## Summary
- Add `@jimmyzho` as a codeowner for the `# ── GEMM ──` and `# ──
Grouped GEMM ──` sections of `.github/CODEOWNERS`

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated review ownership for GEMM and Grouped GEMM areas. No
user-facing behavior changed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>

### [ea7f48c](https://github.com/flashinfer-ai/flashinfer/commit/ea7f48c1e1632fe085cede8ce37caaed179f0b14)

- **作者**: Adrian
- **时间**: 2026-09-23T21:10:32Z
- **提交信息**: test: prune batch attention parameter matrix (#5409)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_batch_attention.py` to `parametrize_product`.
Regular pytest runs use deterministic pairwise coverage, while `pytest
--full` retains the exhaustive matrices for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Repository commit hooks passed for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Expanded batch attention correctness testing to evaluate each
configured sequence-length pair with representative pairwise
combinations of the other parameters.
* Coverage continues to include block sizes, attention head counts,
dimensions, scaling, causal settings, layouts, data types, and related
options. This improves coverage of interactions between sequence lengths
and the other tested configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [f476158](https://github.com/flashinfer-ai/flashinfer/commit/f476158e9527fd93e3f08e69472aca4f5e057622)

- **作者**: Adrian
- **时间**: 2026-09-23T20:50:10Z
- **提交信息**: test: prune attention sink parameter matrix (#5407)

## 📌 Description

Convert the Cartesian parameter matrix in
`tests/attention/test_attention_sink.py` to `parametrize_product`.
Regular pytest runs use deterministic pairwise coverage, while `pytest
--full` retains the exhaustive matrix for nightly testing.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Ran pre-commit hooks for the modified file.

## 🧪 Tests

- [x] Python compilation and diff validation passed.

## 🔬 Experimental Track

- [ ] This PR is experimental.

## Reviewer Notes

This PR intentionally changes only one test file so each pruning
candidate can be reviewed independently.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

- **Tests**
- Updated attention sink test coverage to use pairwise combinations of
data types, sizes, heads, windows, causal settings, and backends.
- Preserved coverage of the existing parameter combinations through the
revised test organization.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [cb3d503](https://github.com/flashinfer-ai/flashinfer/commit/cb3d503f93252bdf07391e6a97ec61986c7964fb)

- **作者**: Ziming Wang
- **时间**: 2026-09-23T20:37:46Z
- **提交信息**: [moe_ep] Batch NVFP4 epilogue staging copies (#5132)

## 📌 Description

I batch the present NVFP4 epilogue tensors with `torch._foreach_copy_`.
Contiguous CUDA inputs stage `fc1_alpha`, `fc2_alpha`, and
`fc1_norm_const` in one kernel. Existing workspace buffers, optional
values, dtype conversion, and shared-workspace layer order remain in
place. Sources that overlap workspace storage use the original ordered
copies.

## 🔍 Related Issues

Related to #5077.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Project hooks pass on both changed files.

## 🧪 Tests

- [x] Epilogue value, alias-order, and shared-workspace graph
regressions are included.
- [x] The epilogue tests pass on CPU after merging current main.
- [ ] Run the complete SM100 MegaMoE path.

The isolated staging method passes H100 value and graph checks,
including dtype conversion, broadcast and strided inputs, optional
fields, special FP32 values, source independence, and cross-source
aliases. Activation quantization is isolated in these checks.

### Staging benchmark

H100 80 GB HBM3, CUDA 13.0, PyTorch 2.13.0+cu130. A CUDA graph stages
three FP32 tensors of 16 values for each of 61 layers into a shared
workspace. The table reports medians from twelve alternating-order
CUDA-event samples of 300 replays each.

| Measurement | Baseline | This PR |
|---|---:|---:|
| 61-layer staging latency | 164.641 µs | 70.663 µs |
| CUDA copy operations | 183 | 61 |

These timings cover epilogue staging. The quantizer, workspace
addresses, thunk cache, and MegaMoE compute kernel retain their existing
implementation.

## 🔬 Experimental Track

- [ ] This PR is **experimental** and adds or changes code under
`flashinfer/experimental/` or an `@flashinfer_experimental_api`.
Tracking issue #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point with signature,
shared validation, feature-gate check, backend selection and handoff.
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] AOT registration is excluded. Automatic experimental backend
selection requires `FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`.
Calling an experimental API or naming an experimental backend explicitly
supplies opt-in.
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets.

```experimental-tests
```

## Reviewer Notes

The merge retains the warmup checks added on main.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **Bug Fixes**
- Improved workspace staging to safely handle overlapping buffers while
preserving correct copy ordering.
- Ensured staged values remain independent from source changes and
retain expected prior values when inputs are omitted.
- Improved consistency across CPU, CUDA, varied tensor layouts, optional
inputs, shared workspaces, and CUDA graph replay.

- **Tests**
- Added coverage for NVFP4 workspace staging, aliasing behavior, device
compatibility, and field-to-workspace mapping.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6b1946b](https://github.com/flashinfer-ai/flashinfer/commit/6b1946b2afddd8e4d177054e86add69f5102018c)

- **作者**: eigen
- **时间**: 2026-09-23T20:32:16Z
- **提交信息**: feat(cake_diffusion): add MiniMax-H3 fused RMSNorm + AdaLN + FC1 + SwiGLU for SM100 and SM103 (#5491)

## Summary

Three fused MiniMax-H3 FFN-prologue operators for SM100 (B200) and SM103
(B300), each two kernel launches per call:

| operator | activations / weights | scales | kernels |
|---|---|---|---|
| `minimax_h3_fc1_swiglu` | BF16 / BF16 | – |
`kernel_minimax_h3_norm_adaln_bf16` →
`kernel_minimax_h3_fc1_swiglu_bf16` |
| `minimax_h3_fc1_swiglu_mxfp8` | E4M3 / E4M3 | UE8M0 per 32 (128x4
swizzle) | `kernel_minimax_h3_norm_adaln_mxfp8` →
`kernel_minimax_h3_fc1_swiglu_e4m3` |
| `minimax_h3_fc1_swiglu_nvfp4` | E2M1 / E2M1 | UE4M3 per 16 + static
global scale (128x4 swizzle) | `kernel_minimax_h3_norm_adaln_nvfp4` →
`kernel_minimax_h3_fc1_swiglu_e2m1` |

Computation per call (hidden 5376, FC1 5376 → 2·14336, batch 1, T tokens
after Ulysses split):

`h = rmsnorm(x) * (1 + scale[idx]) + shift[idx]` → `[gate | up] = h @
W_fc1ᵀ` → `y = silu(gate) * up` (BF16 `[T, 14336]`)

* Kernel 1 (row-parallel, 4 rows per CTA): RMSNorm + indexed AdaLN,
writes the BF16 activation, or quantizes it in place (MXFP8 / NVFP4
recipes are bit-exact with `mxfp8_quantize` / `nvfp4_quantize`).
* Kernel 2 (persistent `cta_group::2` tcgen05 GEMM): one 2-CTA cluster
owns a 256-row × N tile pair, the leader CTA streams the gate weight
rows and the peer the matching up rows, so the SwiGLU epilogue reads
both halves from TMEM and writes `y` directly with the BF16 rounding
points of the unfused chain. Tiles are handed out by a
cluster-launch-control scheduler (one `try_cancel` ahead, 4-deep
multicast response ring); TMA OOB fill handles the row tails;
block-scaled variants load all K-set scale tiles with one TMA per stage.
* Weight preparation (`prepare_minimax_h3_fc1_weight_mxfp8` / `_nvfp4`)
quantizes offline and builds the paired gate/up scale tiles that
`cta_group::2` block-scaled MMA expects (both CTAs read the B scales
from the leader's TMEM indexed by the combined N).

## Performance

Complete operator (both launches), CUPTI kernel time, cold L2, median of
interleaved samples against the segmented FlashInfer chain (`rmsnorm` →
modulate → [`mxfp8_quantize` | `nvfp4_quantize`] →
[`bmm`/`mm_mxfp8`/`mm_fp4`] → `silu_and_mul`) on 47 shapes (production
centers P ∈ {1,2,4,8} × T ∈ {33472, 38592, 48768, 58944, 74240, 109952},
±64/32/16/8 aligned tails, ±1 tails, small M):

| run | shapes | speedup vs incumbent (min / geomean / max) | FC1-equiv
TFLOP/s (min–max) | vs GEMM-only FlashInfer/cuBLAS call |
|---|---|---|---|---|
| B200 BF16 | 47/47 pass | 1.021 / 1.148 / 1.248 (vs
`segmented_flashinfer_bf16`) | 1365–1623 | 0.85–1.14
(`cublas_fc1_gemm_only`) |
| B200 MXFP8 | 47/47 pass | 1.468 / 1.659 / 1.873 (vs
`segmented_flashinfer_mxfp8`) | 2511–2903 | 1.05–1.55
(`flashinfer_mm_mxfp8_only`) |
| B200 NVFP4 | 47/47 pass | 1.388 / 1.624 / 2.283 (vs
`segmented_flashinfer_nvfp4`) | 3994–4413 | 0.81–0.96
(`flashinfer_mm_fp4_only`) |
| B300 BF16 | 47/47 pass | 1.058 / 1.155 / 1.214 (vs
`segmented_flashinfer_bf16`) | 1409–1751 | 0.91–1.09
(`cublas_fc1_gemm_only`) |
| B300 MXFP8 | 47/47 pass | 1.481 / 1.672 / 2.008 (vs
`segmented_flashinfer_mxfp8`) | 2524–3125 | 1.02–1.63
(`flashinfer_mm_mxfp8_only`) |
| B300 NVFP4 | 47/47 pass | 1.721 / 1.930 / 2.202 (vs
`segmented_flashinfer_nvfp4`) | 4387–5106 | 0.87–1.36
(`flashinfer_mm_fp4_only`) |

Bench-regression style single-shape numbers (P=8, M=4824, complete
operator): B200 BF16 1416 / MXFP8 2539 / NVFP4 4094 TFLOP/s
FC1-equivalent; B300 1466 / 2595 / 4530.


## Validation

* Output vs the BF16 unfused reference on the same quantized operands:
bounded violation count at atol 1e-2 / rtol 1.6e-2; FP32-oracle fairness
(the fused kernel is never worse than the unfused chain against an FP32
oracle on its own operands).
* Quantized activations bit-exact with `mxfp8_quantize` /
`nvfp4_quantize` (NVFP4: exact rounding ties excluded, both directions
are equally accurate).
* `compute-sanitizer` synccheck + memcheck clean for all six kernels on
B200 and B300.
* `tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py`: bit-exact
quantized activations vs `mxfp8_quantize` / `nvfp4_quantize`, output
checks and workspace/argument validation for M in {1, 127, 128, 129,
257, 4824}; the same checks pass through the JIT path on B200 and B300
(smoke logs kept with the internal evidence bundle).

## Limits (memory, features, topology)

* **Architectures**: CC 10.0 (B200/GB200) and 10.3 (B300/GB300) only —
tcgen05 MMA + TMEM + cluster-launch-control; other devices raise at
module build. One cubin per arch (device code differs in smem-address
lowering); the host dispatches on exact CC.
* **Topology**: GEMM kernels launch 2-CTA clusters
(`__cluster_dims__(2,1,1)`, 192 threads: TMA warp, MMA warp, 4 epilogue
warps); persistent grid = one cluster per SM pair (148 SMs → 74
clusters); tiles are handed out by CLC `try_cancel`, so the grid is
independent of M. Single GPU, no multi-GPU or DSM traffic.
* **Shared memory**: BF16 GEMM 230,528 B (7 stages × A 16 KiB + B 16
KiB), MXFP8 193,536 B (3 stages × 256-deep), NVFP4 221,184 B (6 stages);
the norm kernels use no dynamic smem. **TMEM**: BF16 2 × 256 accumulator
columns; block-scaled variants 2 × 224 accumulator + 8+16 (MXFP8) /
16+32 (NVFP4) scale columns — the 512-column budget is what fixes N=224
for the quantized variants.
* **Workspaces** (caller-provided or allocated by the wrapper): BF16
activation `[M, 5376]` BF16 (10.5 KiB/row); MXFP8 `[M, 5376]` E4M3 +
`ceil(M/128) × 42 × 512 B` UE8M0 scale tiles; NVFP4 `[M, 2688]` packed
E2M1 (uint32 view) + `ceil(M/128) × 84 × 512 B` UE4M3 scale tiles.
Weights are prepared once offline
(`prepare_minimax_h3_fc1_weight_{mxfp8,nvfp4}`): quantized `[28672,
5376]` + paired gate/up scale tiles (2 × 512 B per K-set per 224-column
tile).
* **Shapes**: hidden 5376 and FC1 28672 (2 × 14336) are compile-time
constants; any M ≥ 1 (row tails via TMA OOB fill and predicated stores);
batch is folded into M (2-D `[M, 5376]` input); `adaln_index` is int32
`[M]` selecting the AdaLN row; `eps` fixed at 1e-5. NVFP4 needs the
activation global scale (`nvfp4_global_scale`, calibrated per
shape/model) and `alpha = 1/(g_a·g_w)`.
* **Numerics**: BF16 round points of the unfused chain are preserved (h,
gate, up, silu(gate), product); MXFP8/NVFP4 activation quantization is
bit-exact with `mxfp8_quantize` / `nvfp4_quantize` (NVFP4 modulo
exact-tie direction); accumulation FP32 in TMEM.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added BF16, MXFP8, and NVFP4 fused operations for the MiniMax-H3 video
model, combining normalization, conditioning, and SwiGLU processing.
* Added utilities to prepare quantized weights and calculate activation
workspace sizes and quantization scales.
* Added support for generating and selecting operation builds for
Blackwell compute architectures.
* **Tests**
* Added coverage for supported data formats, output accuracy, invalid
inputs, and supplied output buffers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [06aa49c](https://github.com/flashinfer-ai/flashinfer/commit/06aa49c11458d7f6d268d70b0578247d65af7759)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-23T19:33:40Z
- **提交信息**: docs: add self-review skill and fix contributor entry links (#5501)

## 📌 Description

- **Self-review skill** (`.claude/skills/self-review/SKILL.md`): walks a
diff through `docs/code_review_guidance.md` and the `CONTRIBUTING.md` PR
rules before a PR is opened, reporting findings as "fix before opening"
vs "mention in Reviewer Notes". Links to the docs rather than restating
them. Hooked from `CLAUDE.md` as strongly recommended but informal — not
a gate, and not needed for local-only changes. Codex reaches it via the
existing `AGENTS.md` redirect.
- **Broken links**: `CLAUDE.md` pointed at `.claude/skills/*/skill.md`;
the files are `SKILL.md`.
- **README**: new "Contributing" section linking `CONTRIBUTING.md`. 

No changes to the review guidance docs.

## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] Pre-commit hooks pass locally.

## 🧪 Tests

Docs-only. All markdown links in the changed files resolve; the skill's
shell
snippets were dry-run on a real branch.

## Reviewer Notes

The skill is deliberately thin so the guidance docs stay the single
source of
truth. Wording describes the self-review as applying the repository's
published
guidance, not as equivalent to reviewer criteria.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Documentation**
* Added optional guidance for reviewing changes before opening a pull
request, including how to categorize findings and document public API
changes.
  * Added links to contribution and review guidance in the README.
  * Corrected links to skill guides in contributor documentation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [08e3477](https://github.com/flashinfer-ai/flashinfer/commit/08e3477fa0d698f8535eebf7375317ac6e49df07)

- **作者**: Brian K. Ryu
- **时间**: 2026-09-23T19:30:47Z
- **提交信息**: ci: intersect targeted A10G/T4 scopes with their bare-run shard lists (#5476)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Introduces one rule for `@flashinfer-bot run <paths>`: **a targeted run
on a lane never tests more than the bare run tests (`@flashinfer-bot
run`) on that lane.**

- H100's bare run covers `tests/`, so its targeted scope is the request
unchanged (no behavior change).
- A10G and T4 bare runs are the fixed shard lists in
`scripts/task_jit_run_tests_part{1-5}.sh` (A10G) and `part3.sh` (T4), so
their targeted scope is now the request intersected with those lists. A
lane left with nothing is not scheduled instead of claiming an on-demand
runner.
  
Why: today a targeted run can be *stricter* than a full run. A file the
bare run never exercises on sm86/sm75 can fail there on an unrelated PR
and — since all cells share one fail-fast matrix — cancel the H100 cell
that actually covers it. Intersecting with the shard lists makes
targeted and bare runs consistent and protects the meaningful result.

`scripts/pr_checks/targeted_lane_scope.py` derives coverage by reading
the shard scripts, so there is no second list to keep in sync: adding a
file to a shard both covers it on every bare run and makes it eligible
for targeted runs on that lane. Bare runs are untouched.

Example:
| request | cells |
|---|---|
| bare run | 5× A10G shards, T4, H100 — unchanged |
| `tests/utils/test_topk.py` | A10G, T4, H100 (each with the file) |
| `tests/kda/test_recurrent_kda_prefill.py` | H100 only |
| `tests/attention/ tests/utils/test_sampling.py` | A10G: 9
shard-covered attention files + sampling; T4: sampling; H100: request as
given |

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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Testing**
* Targeted GPU test runs now limit A10G and T4 to tests covered by their
standard shard assignments.
* A10G and T4 lanes are skipped when no tests match the requested scope;
H100 continues using the requested scope directly.
* Validation now flags cases where standard shard coverage cannot be
detected, helping prevent incomplete targeted test runs.

* **Documentation**
* Clarified lane-specific coverage limits and scheduling behavior for
targeted runs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9c05c0a](https://github.com/flashinfer-ai/flashinfer/commit/9c05c0a9c7cd11f893393b0aa6cb8fb166fb8c88)

- **作者**: Jimmy Zhou
- **时间**: 2026-09-23T18:49:35Z
- **提交信息**: bench: sm107 whitelist and updates (#4981)

<!-- .github/pull_request_template.md -->

## 📌 Description

## 1. Norm — fp8 refcheck compared in the wrong units

`benchmarks/routines/norm.py`

The three fp8 refcheck sites cast an fp8 result and a float reference to
float
and called `torch.isclose(rtol=1e-1, atol=1e-1)`. Both bounds were
wrong, in
opposite directions.

`rtol=1e-1` is **stricter than the dtype can represent**: adjacent fp8
codes are
12.5% apart (e4m3) and 25% apart (e5m2), so a single element where the
kernel and
torch round a tie to neighbouring codes exceeded rtol and failed the
case.

`atol=1e-1` is **far too loose**, and dominates at small magnitudes.
Sweeping the
old predicate over every finite e4m3 code:

| ref | furthest `out` that passed | codes apart |
|---|---|---|
| 4.0 | 3.5 | 2 |
| 1.0 | 0.8125 | 3 |
| 0.25 | 0.140625 | 7 |
| 0.1 | 0.00195 | 28 |

Replaced with `_fp8_code_stats`, an exact comparison in fp8 **code
space**. Both
tensors are already the same fp8 dtype, so their codes are mapped to a
monotonic
sign-magnitude index and subtracted: distance 0 is bit-equal, 1 is
adjacent codes
(a rounding tie), and >1 is a real mismatch. No `rtol`, no `atol`.

Verified across all 256 codes of both dtypes: consecutive finite values
differ by
exactly 1, `+0`/`-0` compare equal, subnormals order correctly. NaN is
excluded
from the distance and handled separately. Ties are reported at
`verbose>=1` so a
systematic one-code bias stays visible rather than silently tolerated.

## 2. Norm — timing closures could not rotate their inputs

`benchmarks/routines/norm.py`

`bench_gpu_time` achieves a cold L2 by cloning the tensors in
`input_args` and
rotating between the copies; its docs require `fn` to accept them. The
DiT
layernorm and QK-rmsnorm-rope benchmarks passed **zero-argument
closures** that
captured their inputs, so every iteration re-read one address, L2 stayed
warm and
the reported times were optimistic.

`fused_fn`/`eager_fn` now take `(input_t, residual)` and `run_fused`
takes `qkv`,
with the matching `input_args`.

Separately, `testFusedDitLayernorm` hardcoded
`enable_cupti=True, dry_run_iters=10, repeat_iters=100` and never
graph-captured,
so `--use_cuda_events`, `--dry_run_iters` and `--num_iters` were inert
and this
one routine was timed on a different path from every sibling in the
file. It now
honours the flags and CUDA-graphs like the others.

## 3. MoE — fp4_quantize scale-factor padding

`benchmarks/routines/moe.py`

`fp4_quantize` zero-pads the **scale** tensor on both dims — outer to
128
(swizzled SF layout), inner to 4 — while the **data** tensor is
unpadded. The
nvfp4 path reshaped the scales with the raw extents.

Two consequences, the second more serious:

1. Where the dims were not already aligned the reshape raised — e.g.
gpt-oss at
   `hidden_size=2880`.
2. Where it did not raise, the benchmark **silently substituted
`torch.ones()`
for the scale factors**. 51 of 82 runnable `trtllm_fp4_block_scale_moe`
lines
(~62% of benchmarked *and refchecked* cases) were measured and
"validated"
   against fabricated scales.

Now uses the padded extents via `_sf_outer`/`_sf_inner`. The cutlass
path in the
same file already did this via `round_up(...)`; this was an
inconsistency within
one file. **Any nvfp4 MoE number produced by an unpatched harness at
`num_tokens % 128 != 0` should be treated as void.**

## 4. RoPE — `cos_sin_cache` must be fp32

`benchmarks/routines/rope.py`

`apply_rope_with_cos_sin_cache` asserts `cos_sin_cache.dtype ==
torch.float32`
(`flashinfer/rope.py:1209`), but the benchmark built it with
`input_dtype`, so
every case failed with `cos_sin_cache should be float32` on **every**
architecture. That is why this routine had no testlist on any branch.
The three
sibling call sites in the same file already used fp32.

The bandwidth term is corrected to match — the cache read is 4 bytes per
element.

## 5. Compilation-flag fixes

`flashinfer/compilation_context.py`, `flashinfer/jit/tinygemm2.py`

`cutlass_supports_sm107()` decided whether to emit native `compute_107a`
by
grepping a CUTLASS header for `struct Sm107`. That describes the
*template
library*, not the *toolkit* — `compute_107a` only lands in CUDA 13.4. A
tree
pairing a Sm107-aware CUTLASS with CUDA 13.2/13.3 emitted a `-gencode`
its own
nvcc rejects:

```
nvcc fatal : Unsupported gpu architecture 'compute_107a'
```

which the JIT swallowed into a generic "Ninja build failed" at `rc=0`.
All ten
attention testlists produced zero rows while the job looked green.
`FLASHINFER_CUDA_ARCH_LIST=10.0f` does not work around it.

Now asks nvcc directly via `--list-gpu-arch`, resolved the same way the
JIT
resolves nvcc, failing closed to the sm100f family target. The fallback
is
unconditional rather than gated on `map_sm107_to_100f`, because ~15
`gen_*_module` callers (norm, sampling, topk) never opt in and were
emitting the
bad target regardless.

`gen_tinygemm2_module()` additionally needs `map_sm107_to_100f=True`:
the no-bias
path (`routergemm.py:509`) reaches this generic module on SM107,
bypassing
`gen_tinygemm2_sm100_module()`.

## 6. Attention — GQA group_size 16 dispatch

`include/flashinfer/utils.cuh`

`DISPATCH_GQA_GROUP_SIZE` handled 1/2/3/4/6/8 and sent everything else
to
`FLASHINFER_ERROR`. A GQA ratio of 16 (Nemotron 16/1 and 32/2) therefore
raised
at dispatch, and because a raise aborts the whole benchmark line it also
took
down every other backend sharing that line. Adding the arm took
`attention_decode_fp8` from 15 to 21 `[PERF]` rows.

## 7. cc 10.7 backend rows for 46 routines

`benchmarks/routines/flashinfer_benchmark_utils.py`

`filter_backends_by_compute_capability` does
`cc_to_supported_backends.get(compute_capability, [])`, so a missing key
drops
every backend and the case prints `[ERROR] No backends to test` and
exits 0.
Only 10 of 59 routines had a `"10.7"` key; this adds 46, taking it to
56.

Every backend listed is backed by an observed `[PERF]` row on GR100
(cc10.7) or
B200 (cc10.0). Nothing is inferred from the sibling `10.3` row — a
plausible-looking row that was never run is the exact failure mode being
fixed.

**Five rows deliberately differ from `10.3` and should not be "fixed" to
match:**

| Routine | Difference | Reason |
|---|---|---|
| `mm_mxfp8` | drops `cudnn` | library *raises* at cc10.7, killing the
whole line. `bmm_mxfp8` keeps cudnn — the guard is per-routine |
| `mxfp4_quantize` | drops `cute-dsl` | no `[PERF]` observed at cc10.7 |
| `chunk_gated_delta_rule` | drops `fla` | **environment, not
capability** — `flash-linear-attention` is absent from the image, so it
could not emit `[PERF]`. Re-add and verify if CI installs it |
| `recurrent_kda_prefill` | `10.7` empty | observed: the library rejects
with `requires compute capability 12.0, got sm_107` |
| `recurrent_kda_prefill` | `10.0` populated | see below |


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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
  * Added support for grouped-query attention with a group size of 16.
* Improved compatibility with NVIDIA SM107 hardware and CUDA toolchains,
including automatic fallback handling when needed.

* **Bug Fixes**
* Corrected FP4 mixture-of-experts benchmark handling for padded scale
tensors.
* Improved FP8 output validation to detect code-level mismatches more
accurately.

* **Benchmarking**
* Updated normalization and rotary-position-embedding benchmarks for
more consistent configurable execution.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [f2f2279](https://github.com/flashinfer-ai/flashinfer/commit/f2f227977102dc91d1eba837d7f2377d401fe1c4)

- **作者**: Zhejian Peng
- **时间**: 2026-09-23T18:23:43Z
- **提交信息**: feat: add is_deterministic mode to top_k_renorm_probs (#4831)

## Problem

`top_k_renorm_probs` returns bitwise-different results on repeated calls
with bitwise-identical input. On GB300 (192x131072 fp32, k=50): 19/19
repeated invocations differed, max_abs_diff ~3e-8.

This matters for replicated execution: tensor-parallel LLM serving runs
sampling/spec-decode verify redundantly on every TP rank with identical
inputs, and per-invocation nondeterminism makes ranks compute
rank-divergent `target_probs`. With shared rejection-sampling coins,
committed tokens then flip exactly at inverse-CDF boundaries (measured
~1e-7..1e-5 per sampling decision, roughly linear in top_k), which
diverges rank-local radix caches and eventually surfaces as
collective-shape mismatch hangs — the exact chain independently
root-caused in sgl-project/sglang#22458.

## Root cause

The radix **pivot selection is already deterministic** (integer
histogram accumulation) — we verified the kept support is stable 20/20
across calls. The only nondeterministic step is the multi-CTA
**renormalization sum**: per-CTA partial sums are combined with float
`atomicAdd(&state->sum_topk, block_sum)`, so CTA arrival order changes
the rounding of the normalizer, wobbling every output value in its last
bits.

## Fix

Mirror `top_p_renorm_probs`' existing deterministic option: an
`is_deterministic` flag (default `False`, existing behavior and
performance unchanged) that switches the multi-CTA accumulation to
order-independent fixed-point integer atomics:

- `RadixRowState` gains a `sum_topk_fixed` (u64) field; contributions
are quantized at 2^44 scale and combined with integer `atomicAdd`
(associative, order-independent).
- Overflow bound is a kept mass of 2^20 — far above probability-input
magnitudes (docs note the assumption); quantization error (≤2^-44 per
CTA) is below fp32 ulp.
- Single-CTA path already sums in a fixed block-reduction order and is
unaffected; the flag only changes the multi-CTA path.
- Plumbed through `csrc/renorm.cu`, the sampling binding, and the Python
API with the same signature/doc shape as `top_p_renorm_probs`.

## Validation (GB300, JIT build, 192x131072 fp32)

```
[det=True ] bitwise-different: 0/19            (was 19/19)
[det=False] bitwise-different: 19/19           (default unchanged)
[correct  ] same_support_vs_default=True  max_val_diff=1.5e-08  row_sum_err=2.4e-07
[k=2000   ] bitwise-different: 0/9             (per-row top_k tensor)
[perf     ] default=0.148ms  deterministic=0.151ms  overhead=+2.6%
```

Added `test_top_k_renorm_probs_deterministic` (bitwise stability across
10 calls, support equality vs default, value closeness, row-sum
normalization) across batch/vocab/k/dtype parametrizations.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optional deterministic execution mode for top-k probability
renormalization.
  * Supports both scalar and per-row top-k values.
* Works with float32, float16, and bfloat16 inputs while preserving
existing default behavior.
* Deterministic execution produces consistent results across repeated
calls.

* **Tests**
* Added coverage for deterministic and non-deterministic modes across
supported data types and top-k configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Ka-Hyun Nam <knam@nvidia.com>

### [0833fa9](https://github.com/flashinfer-ai/flashinfer/commit/0833fa9dc4d48214373082a1bda4fc8db5ae34a1)

- **作者**: Qiang Xu
- **时间**: 2026-09-23T18:21:05Z
- **提交信息**: feat(kda): add CuTe DSL small-BH KDA prefill backend for Blackwell (#5032)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

- Added a `small-bh` backend for KDA prefill that points to a CuTe DSL
implementation with high performance when BxH <= SM count / 2
- Updated `auto` backend logic to automatically select 'small-bh' when
eligible and when BxH is small
- Updated `bench_recurrent_kda_prefill.py` to support cuda graph
capture, as CUPTI alone captures the host overhead between the 2 kernels
of `small-bh` backend

Performance on GB200:

For small BxH cases, On average 1.32x faster than current cute-dsl
backend, and 1.29x faster than cake.

| Case | cute-dsl | cake | small-bh | vs cute-dsl | vs cake |
| ---------------------- | --------- | --------- | --------- |
----------- | ------- |
| **small BxH cases** | | | | | |
| h64_fixed8192 | 396.4 | 415.313 | 327.505 | 1.210 | 1.268 |
| h12_fixed_512 | 34.049 | 28.48 | 21.792 | 1.562 | 1.307 |
| h12_fixed_8192 | 274.833 | 274.689 | 209.985 | 1.309 | 1.308 |
| h12_packed_mixed | 137.488 | 137.713 | 110.4 | 1.245 | 1.247 |
| h8_fixed_65536 | 1982.95 | 2007.447 | 1527.044 | 1.299 | 1.315 |
| h4_fixed_65536_holdout | 1904.918 | 1912.677 | 1460.116 | 1.305 |
1.310 |
| h1_fixed_131072 | 3674.298 | 3642.314 | 2819.769 | 1.303 | 1.292 |
| h1_fixed_1048576 | 29279.811 | 28914.739 | 22390.911 | 1.308 | 1.291 |
| **large BxH cases** | | | | | |
| h96_fixed8192 | 452.369 | 415.745 | 539.122 | 0.839 | 0.771 |
| h96_mixed | 331.137 | 331.457 | 512.833 | 0.646 | 0.646 |
| h96_uniform | 375.473 | 361.217 | 479.01 | 0.784 | 0.754 |
| h64_mixed | 220.896 | 233.793 | 381.313 | 0.579 | 0.613 |
| h64_uniform | 252.816 | 242.785 | 328.288 | 0.770 | 0.740 |
| h12_packed_512x32 | 108.064 | 107.872 | 139.009 | 0.777 | 0.776 |
| h12_packed_128x8 | 16.336 | 16.432 | 21.344 | 0.765 | 0.770 |
| h12_packed_1024x8 | 65.664 | 62.385 | 79.824 | 0.823 | 0.782 |

The 'auto' backend automatically selects the most performant backend:

```
h96_fixed8192      cute-dsl engine        453.249 us
h96_mixed          cute-dsl engine        331.185 us
h96_uniform        cute-dsl engine        375.473 us
h64_fixed8192      small-bh k1_k2         327.361 us
h64_mixed          cute-dsl engine        222.288 us
h64_uniform        cute-dsl engine        252.321 us
h12_packed_512x32  cute-dsl engine        108.033 us
h12_packed_128x8   cute-dsl engine         16.320 us
h12_fixed_512      small-bh k1_k2          21.824 us
h12_fixed_8192     small-bh k1_k2         209.936 us
h12_packed_mixed   small-bh k1_k2         110.352 us
h12_packed_1024x8  cute-dsl engine         65.184 us
h8_fixed_65536     small-bh k1_k2        1527.476 us
h4_fixed_65536_holdout small-bh k1_k2        1460.341 us
h1_fixed_131072    small-bh k1_k2        2819.640 us
h1_fixed_1048576   small-bh k1_k2       22408.993 us
```

vs FlashKDA:

```
h96_fixed8192      k1_k2 PR    538.514 us  raw   1024.051 us 1.9016x  adapted   1025.579 us 1.9045x
h96_mixed          k1_k2 PR    513.458 us  raw    832.266 us 1.6209x  adapted    837.123 us 1.6304x
h96_uniform        k1_k2 PR    479.522 us  raw    668.554 us 1.3942x  adapted    677.066 us 1.4120x
h64_fixed8192      k1_k2 PR    328.065 us  raw    938.051 us 2.8593x  adapted    939.259 us 2.8630x
h64_mixed          k1_k2 PR    381.361 us  raw    642.530 us 1.6848x  adapted    648.217 us 1.6997x
h64_uniform        k1_k2 PR    330.249 us  raw    454.817 us 1.3772x  adapted    459.889 us 1.3926x
h12_packed_512x32  k1_k2 PR    138.816 us  raw    204.097 us 1.4703x  adapted    208.705 us 1.5035x
h12_packed_128x8   k1_k2 PR     21.200 us  raw     33.704 us 1.5898x  adapted     35.728 us 1.6853x
h12_fixed_512      k1_k2 PR     21.392 us  raw     61.569 us 2.8781x  adapted     63.841 us 2.9843x
h12_fixed_8192     k1_k2 PR    210.137 us  raw    789.322 us 3.7562x  adapted    790.474 us 3.7617x
h12_packed_mixed   k1_k2 PR    110.048 us  raw    333.241 us 3.0281x  adapted    335.473 us 3.0484x
h12_packed_1024x8  k1_k2 PR     79.624 us  raw    146.400 us 1.8386x  adapted    148.849 us 1.8694x
h8_fixed_65536     k1_k2 PR   1530.573 us  raw   6122.114 us 3.9999x  adapted   6118.514 us 3.9975x
h4_fixed_65536_holdout k1_k2 PR   1459.828 us  raw   6026.122 us 4.1280x  adapted   6034.401 us 4.1336x
h1_fixed_131072    k1_k2 PR   2816.712 us  raw  11827.210 us 4.1989x  adapted  11823.195 us 4.1975x
h1_fixed_1048576   k1_k2 PR  22405.818 us  raw  94403.420 us 4.2133x  adapted  94476.852 us 4.2166x
```

Without cuda graph, the smallest shapes have large overhead:

```
h96_fixed8192      small-bh k1_k2         543.778 us
h96_mixed          small-bh k1_k2         516.339 us
h96_uniform        small-bh k1_k2         482.562 us
h64_fixed8192      small-bh k1_k2         330.978 us
h64_mixed          small-bh k1_k2         384.018 us
h64_uniform        small-bh k1_k2         331.986 us
h12_packed_512x32  small-bh k1_k2         140.481 us
h12_packed_128x8   small-bh k1_k2          33.344 us
h12_fixed_512      small-bh k1_k2          37.232 us
h12_fixed_8192     small-bh k1_k2         213.169 us
h12_packed_mixed   small-bh k1_k2         113.569 us
h12_packed_1024x8  small-bh k1_k2          81.968 us
h8_fixed_65536     small-bh k1_k2        1537.273 us
h4_fixed_65536_holdout small-bh k1_k2        1474.903 us
h1_fixed_131072    small-bh k1_k2        2824.159 us
h1_fixed_1048576   small-bh k1_k2       22416.620 us
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

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added a workload-aware `small-bh` prefill backend for eligible NVIDIA
SM100a and SM103a hardware.
- Automatic backend selection now considers logical batch size and head
count.
  - Added CUDA Graph timing support to recurrent KDA prefill benchmarks.

- **Documentation**
- Updated KDA documentation to explain workload-dependent backend
selection and hardware support.

- **Bug Fixes**
- Improved validation and fallback behavior when the small-BH backend is
unavailable or unsupported.
- Improved benchmark handling for generated Cake routes and graph-based
timing scenarios.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b35e48a](https://github.com/flashinfer-ai/flashinfer/commit/b35e48a9e67a5bea6ecf276625352ca0820d9988)

- **作者**: Duncan Moss
- **时间**: 2026-09-23T17:17:42Z
- **提交信息**: feat(kda): add fused speculative decode kernel (#4809)

## 📌 Description

Add `flashinfer.fused_kda_decode_packed`, an SM10x CuTe DSL kernel that
fuses
Kimi-K3 short convolution, recurrent KDA, and gated RMS normalization
for
packed speculative verification (`T >= 1`). The API updates convolution
and
recurrent caches according to accepted-token metadata, supports ragged
and
empty rows, accepts caller-owned output storage, and is safe to capture
with
dynamic CUDA Graph metadata.

The change also adds public API documentation, FI trace coverage and a
trace
fixture, focused correctness/validation tests, and a benchmark driver.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All focused tests are passing.

On one NVIDIA B300 (SM103):

```text
pytest -q tests/kda/test_fused_kda_decode.py \
  tests/trace/test_fi_trace_template_consistency.py \
  tests/trace/test_fi_trace.py
829 passed, 2 warnings in 21.47s
```

On eight NVIDIA B300s with synthetic Kimi-K3 weights, DSpark with six
draft
tokens, 8,192-token inputs, and 1,024-token outputs, the fused vLLM
integration
matched the baseline checksum and improved total output throughput by
2.63%,
2.54%, 3.29%, 1.76%, and 1.75% at concurrency 1, 4, 8, 16, and 32.

## Reviewer Notes

The implementation is intentionally limited to D=128, W=4, BF16
activation
and convolution state, FP32 recurrent state, bounded gates, supported
Kimi-K3
head counts, and the SD convolution-cache layout. The cluster
synchronization
around split-head state updates and the accepted-token cache commit
semantics
are the highest-value review areas.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added packed, multi-token fused KDA decoding with support for
recurrent state checkpoints and ragged sequences.
  * Exposed the new decoding API at the package’s top level.
* Added support for fused convolution, recurrence, and normalization
during packed decoding.

* **Documentation**
  * Documented the new packed and fused KDA decoding APIs.

* **Tests**
* Added coverage for correctness, compatibility, dynamic metadata,
determinism, CUDA graph capture, and trace generation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [37b4d30](https://github.com/flashinfer-ai/flashinfer/commit/37b4d30eac39b89f198b893dd11914bd76f5fcf8)

- **作者**: eigen
- **时间**: 2026-09-23T12:29:19Z
- **提交信息**: perf(cake_sampling): qualify the radix sampling pipeline on SM90 (H100) and SM107 (Rubin R200); select JIT targets through CompilationContext (#5482)

## Summary

Qualifies `flashinfer.cake_sampling` (#5439, the fused radix top-k →
top-p → sampling pipeline shipped as one generated source with a JIT
flag table for compute capability 9.0 / 10.0 / 10.3 / 10.7 / 11.0) on
the two capability classes that #5439 listed as compile targets only,
and makes the JIT table safe on toolkits that cannot build a listed
target:

1. **Build targets through `CompilationContext`**
(`flashinfer/jit/cake_sampling.py`). The per-capability flag table and
per-capability modules are gone: the frozen source is compiled once into
a single fatbin with
`CompilationContext().get_nvcc_flags_list(supported_major_versions=[9,
10, 11, 12])`, i.e. one `-gencode` per `FLASHINFER_CUDA_ARCH_LIST` entry
(AOT builds on hosts without a GPU) or per visible device, like
`jit/xqa.py`. The kernels use only clusters, distributed shared memory,
PDL and `redux.sync`, so every 9.x–12.x architecture is admitted.
`supported_capability` returns `None` for a device whose architecture is
not a build target, which routes it to `top_k_first`; the binding checks
the fatbin actually holds an image for the device
(`cudaFuncGetAttributes`) and names `FLASHINFER_CUDA_ARCH_LIST` in the
error otherwise. The module is registered in `flashinfer/aot.py` under
`add_misc`. Stage-1 variants whose dynamic shared memory exceeds the
device opt-in limit are excluded from dispatch (on 12.x, 99 KB, the
streaming variants drop out and vocabularies above 196608 take
`top_k_first`). Tests: arch-list-driven target/flag selection,
unsupported-major rejection, fallback route on a GPU left out of the
arch list (bitwise-identical samples), and the shared-memory filter.
2. **SM90 (H100) validated.** All tests and the benchmark set below ran
on an H100 SXM (132 SMs, driver 535.216.03, CUDA 13.3). Measuring every
frozen stage-1 variant per cell showed the B200-fitted single-wave CTA
table mis-ranking on 132 SMs: 128 cluster-4 CTAs are one wave on B200
but two on H100, so the dispatcher streamed `B = 32` rows of a large
vocabulary with clusters of 4 (38–56 % slower than clusters of 2). The
wave table is now keyed by SM count (148 = B200 / B300, 132 = H100;
other devices use the nearest measured table); the cost constants are
unchanged and `choose_stage1` takes an optional `sm_count` (defaults to
the current device).
3. **SM107 (Rubin R200) validated.** The same tests and benchmark set
ran on a VR200 NVL72 node (212 SMs, driver 620.43) with an internal CUDA
13.5 toolkit whose nvcc lists `compute_107`; the generated unit also
compile-checks for `sm_107a`, `sm_110a` and `sm_100a` there. **SM110
(11.0)** remains a compile target: the unit compiles with CUDA 13.3
`nvcc -arch=sm_110a`, but no 11.0 device was available, so it has not
been run.

Docs (`docs/api/cake_sampling.rst`) now list what was measured (H100,
B200, B300 / GB300, R200) instead of "compile targets only", describe
the `CompilationContext` target selection, and carry the H100 and R200
tables below.

## Tests

- `tests/utils/test_cake_sampling.py`: 40 passed (35 + 5 guard tests) on
H100 and on R200 with the earlier nvcc-probe guard; 39 passed (35 + 4
build-target tests) on H100 after the switch to `CompilationContext`
(see the last commit).
- `tests/utils/test_cake_sampling_upstream.py`: 207 passed / 18 skipped
on H100 and on R200 (the skips are the `k ≥ vocab` cases, as upstream
and as on B200).
- Generator-side gates (cluster/DSM kernels compiled natively for
`sm_90a` and `sm_107a`): e2e slice and the adversarial pipeline suite
(38 passed / 1 skipped) pass on both devices; the eight registered
regression cells were measured on both.

## Performance

`python benchmarks/bench_cake_sampling.py --cupti --batches
1,8,16,32,64,128 --vocabs 32768,128256,151936,262144` with `--top-k 50`
/ `--top-k 1000`, stream launch and `--cuda-graph`
(`flashinfer.testing.bench_gpu_time`, CUPTI kernel time, p = 0.9, median
µs). Each cell is `top_k_first → cake_sampling (speedup)`.

### H100 SXM (sm_90a, 132 SMs)

| V | B | k=50 | k=1000 | k=50, CUDA graph | k=1000, CUDA graph |
|---|---|---|---|---|---|
| 32768 | 1 | 45.4 → 19.3 (2.35x) | 45.8 → 25.5 (1.80x) | 45.7 → 30.6
(1.49x) | 45.4 → 36.7 (1.24x) |
| 32768 | 8 | 49.5 → 19.7 (2.52x) | 49.8 → 26.0 (1.91x) | 48.8 → 31.6
(1.55x) | 55.7 → 38.0 (1.47x) |
| 32768 | 16 | 52.8 → 20.5 (2.57x) | 53.0 → 26.9 (1.97x) | 54.0 → 31.8
(1.70x) | 55.7 → 38.0 (1.47x) |
| 32768 | 32 | 54.4 → 22.5 (2.41x) | 54.5 → 29.2 (1.87x) | 55.2 → 34.0
(1.63x) | 57.9 → 40.6 (1.43x) |
| 32768 | 64 | 55.6 → 28.2 (1.97x) | 56.0 → 56.1 (1.00x) | 59.1 → 40.0
(1.48x) | 60.4 → 67.9 (0.89x) |
| 32768 | 128 | 57.8 → 28.4 (2.04x) | 58.6 → 56.7 (1.03x) | 64.1 → 39.6
(1.62x) | 66.6 → 67.9 (0.98x) |
| 128256 | 1 | 111.0 → 27.1 (4.10x) | 66.9 → 32.8 (2.04x) | 80.9 → 38.6
(2.09x) | 74.3 → 44.4 (1.67x) |
| 128256 | 8 | 111.9 → 28.8 (3.89x) | 82.0 → 34.9 (2.35x) | 86.1 → 40.7
(2.12x) | 92.3 → 46.5 (1.98x) |
| 128256 | 16 | 111.6 → 30.9 (3.61x) | 92.8 → 37.1 (2.50x) | 86.9 → 42.6
(2.04x) | 108.6 → 48.7 (2.23x) |
| 128256 | 32 | 114.6 → 35.8 (3.20x) | 106.6 → 42.4 (2.52x) | 92.4 →
47.8 (1.93x) | 119.9 → 54.2 (2.21x) |
| 128256 | 64 | 114.6 → 45.4 (2.52x) | 167.9 → 73.3 (2.29x) | 101.8 →
57.4 (1.77x) | 185.3 → 85.1 (2.18x) |
| 128256 | 128 | 115.7 → 60.2 (1.92x) | 236.7 → 88.9 (2.66x) | 121.7 →
72.0 (1.69x) | 267.3 → 100.3 (2.66x) |
| 151936 | 1 | 112.4 → 30.1 (3.73x) | 75.5 → 36.0 (2.10x) | 86.9 → 42.3
(2.05x) | 97.0 → 48.0 (2.02x) |
| 151936 | 8 | 112.8 → 31.2 (3.61x) | 92.1 → 37.4 (2.46x) | 92.3 → 43.9
(2.10x) | 163.6 → 49.7 (3.29x) |
| 151936 | 16 | 112.7 → 32.4 (3.48x) | 105.3 → 38.7 (2.72x) | 93.1 →
44.6 (2.09x) | 119.6 → 50.4 (2.37x) |
| 151936 | 32 | 113.5 → 39.4 (2.88x) | 122.0 → 45.9 (2.66x) | 97.9 →
52.0 (1.88x) | 122.5 → 58.1 (2.11x) |
| 151936 | 64 | 115.8 → 50.2 (2.30x) | 195.8 → 78.1 (2.51x) | 115.5 →
63.1 (1.83x) | 211.4 → 90.4 (2.34x) |
| 151936 | 128 | 159.6 → 66.9 (2.39x) | 279.9 → 95.3 (2.94x) | 174.0 →
79.3 (2.20x) | 293.9 → 107.4 (2.74x) |
| 262144 | 1 | 111.5 → 34.8 (3.20x) | 91.2 → 40.8 (2.23x) | 88.1 → 47.6
(1.85x) | 97.7 → 53.2 (1.84x) |
| 262144 | 8 | 112.6 → 36.4 (3.10x) | 122.4 → 42.5 (2.88x) | 93.9 → 49.8
(1.88x) | 171.8 → 55.2 (3.11x) |
| 262144 | 16 | 113.4 → 38.1 (2.98x) | 144.9 → 44.4 (3.26x) | 96.6 →
51.2 (1.89x) | 142.7 → 56.6 (2.52x) |
| 262144 | 32 | 128.2 → 51.4 (2.49x) | 231.4 → 57.8 (4.00x) | 143.4 →
65.1 (2.20x) | 253.7 → 70.8 (3.58x) |
| 262144 | 64 | 134.9 → 66.6 (2.03x) | 317.7 → 94.5 (3.36x) | 150.6 →
80.2 (1.88x) | 356.1 → 107.5 (3.31x) |
| 262144 | 128 | 158.2 → 94.3 (1.68x) | 471.0 → 123.3 (3.82x) | 174.5 →
107.4 (1.63x) | 479.6 → 135.5 (3.54x) |

92 of 96 cells are faster than `top_k_first` (1.24x–4.10x). The four
exceptions are `V = 32768, k = 1000, B ∈ {64, 128}`: ties under stream
launch (56.0 → 56.1, 58.6 → 56.7) and slower under CUDA-graph replay
(60.4 → 67.9, 66.6 → 67.9). At that vocabulary `top_k_first` is cheap
while the stage-2/3 sort of a 1024-entry slab per row dominates the
pipeline; the same cells at `k = 50` are 1.5–2.0x. As on B200, the
single-kernel `joint` rejection sampler is the fastest route at `V =
32768, k = 1000, B = 1` (it is not a same-semantics fallback and the
dispatcher does not route to it).

Per-variant stage-1 sweep (24 cells, k = 50 and k = 1000) after the
wave-table change: the dispatcher picks the measured-best variant in 20
cells; in `V = 32768, B = 32–64` the register-resident 2-CTA variant it
picks is 12–17 % slower than the streaming 1-CTA variant, which the B200
cost constants cannot express without regressing `V = 128256, B ≤ 8`
(kept; those cells are still 1.9–2.4x over `top_k_first`).

### Rubin R200 (sm_107a, 212 SMs, internal CUDA 13.5 toolkit)

| V | B | k=50 | k=1000 | k=50, CUDA graph | k=1000, CUDA graph |
|---|---|---|---|---|---|
| 32768 | 1 | 29.8 → 15.9 (1.88x) | 30.6 → 21.1 (1.45x) | 32.3 → 24.8
(1.30x) | 37.4 → 30.0 (1.25x) |
| 32768 | 8 | 33.2 → 17.4 (1.91x) | 33.5 → 22.2 (1.51x) | 42.1 → 25.6
(1.64x) | 39.1 → 30.8 (1.27x) |
| 32768 | 16 | 35.5 → 17.2 (2.06x) | 35.2 → 22.5 (1.56x) | 37.8 → 26.5
(1.42x) | 42.6 → 31.6 (1.35x) |
| 32768 | 32 | 36.8 → 18.0 (2.05x) | 37.2 → 23.1 (1.61x) | 45.3 → 26.7
(1.70x) | 43.1 → 31.5 (1.37x) |
| 32768 | 64 | 38.4 → 19.4 (1.98x) | 38.3 → 24.6 (1.56x) | 45.6 → 28.2
(1.62x) | 45.0 → 33.3 (1.35x) |
| 32768 | 128 | 39.0 → 20.4 (1.91x) | 39.3 → 32.0 (1.23x) | 45.8 → 28.9
(1.58x) | 46.6 → 40.4 (1.15x) |
| 128256 | 1 | 70.4 → 22.3 (3.16x) | 56.1 → 27.3 (2.06x) | 69.3 → 31.7
(2.19x) | 74.3 → 36.3 (2.04x) |
| 128256 | 8 | 70.1 → 23.9 (2.94x) | 68.1 → 28.6 (2.38x) | 73.8 → 32.0
(2.31x) | 74.9 → 37.8 (1.98x) |
| 128256 | 16 | 70.1 → 25.1 (2.79x) | 76.2 → 30.2 (2.53x) | 76.7 → 33.9
(2.26x) | 100.0 → 39.4 (2.54x) |
| 128256 | 32 | 72.0 → 26.1 (2.76x) | 84.2 → 31.1 (2.70x) | 76.0 → 34.8
(2.19x) | 84.3 → 39.7 (2.13x) |
| 128256 | 64 | 72.2 → 30.1 (2.39x) | 91.6 → 35.5 (2.58x) | 76.4 → 38.9
(1.96x) | 99.2 → 44.3 (2.24x) |
| 128256 | 128 | 72.2 → 38.4 (1.88x) | 138.9 → 50.5 (2.75x) | 77.5 →
47.4 (1.64x) | 149.2 → 59.0 (2.53x) |
| 151936 | 1 | 69.8 → 24.5 (2.85x) | 64.2 → 29.4 (2.18x) | 71.2 → 34.4
(2.07x) | 83.7 → 39.4 (2.13x) |
| 151936 | 8 | 70.3 → 26.3 (2.67x) | 77.3 → 30.9 (2.50x) | 77.8 → 34.8
(2.24x) | 86.0 → 39.4 (2.18x) |
| 151936 | 16 | 70.0 → 26.5 (2.64x) | 87.6 → 31.6 (2.77x) | 80.5 → 35.9
(2.24x) | 106.8 → 40.2 (2.66x) |
| 151936 | 32 | 69.9 → 27.4 (2.55x) | 95.9 → 32.4 (2.95x) | 78.8 → 36.9
(2.14x) | 108.9 → 41.7 (2.61x) |
| 151936 | 64 | 72.1 → 33.0 (2.19x) | 107.2 → 38.4 (2.79x) | 80.3 → 42.3
(1.90x) | 118.9 → 47.1 (2.52x) |
| 151936 | 128 | 73.5 → 43.3 (1.70x) | 162.1 → 55.1 (2.94x) | 89.9 →
52.2 (1.72x) | 171.2 → 63.2 (2.71x) |
| 262144 | 1 | 70.1 → 28.4 (2.47x) | 80.1 → 33.6 (2.39x) | 76.4 → 38.0
(2.01x) | 129.4 → 43.4 (2.98x) |
| 262144 | 8 | 70.1 → 30.1 (2.33x) | 103.0 → 34.8 (2.96x) | 78.3 → 39.0
(2.01x) | 109.7 → 43.3 (2.53x) |
| 262144 | 16 | 70.1 → 30.5 (2.30x) | 119.5 → 35.6 (3.36x) | 81.0 → 39.9
(2.03x) | 114.2 → 44.1 (2.59x) |
| 262144 | 32 | 70.2 → 31.8 (2.21x) | 134.3 → 36.8 (3.65x) | 78.8 → 41.2
(1.91x) | 153.1 → 45.6 (3.36x) |
| 262144 | 64 | 87.8 → 41.7 (2.10x) | 196.4 → 47.1 (4.17x) | 100.2 →
51.0 (1.96x) | 218.8 → 56.3 (3.88x) |
| 262144 | 128 | 107.2 → 61.4 (1.75x) | 295.6 → 73.2 (4.04x) | 119.7 →
70.4 (1.70x) | 307.4 → 81.8 (3.76x) |

All 96 cells are faster than `top_k_first` (1.15x–4.17x). The wave table
used is the B200 one (nearest SM count); every dispatcher pick matched
the pattern measured on B200, so no Rubin-specific re-fit was made.

B200 and B300 numbers are unchanged from #5439 (the wave-table change
only affects devices whose SM count is nearer 132 than 148).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Cake sampling now supports a single build covering compute-capability
families 9.x–12.x, with automatic fallback to `top_k_first` when a
device or kernel variant is unavailable.
* Stage-1 kernel selection now accounts for the device’s shared-memory
limit, helping avoid unsupported variants.
* Added Cake sampling to ahead-of-time builds for supported GPU targets.
* **Documentation**
* Expanded architecture, routing, performance, and benchmark guidance,
including H100 and Rubin R200 latency results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [bb676eb](https://github.com/flashinfer-ai/flashinfer/commit/bb676eb062cb58ce574f7b94d1f18dcc850f2dd3)

- **作者**: eigen
- **时间**: 2026-09-23T10:21:31Z
- **提交信息**: feat(cake_softmax): add optimized Blackwell softmax (#4282)

## Description

This PR adds an optimized Blackwell FP32 softmax dispatcher behind the
existing `flashinfer.sampling.softmax` API for SM100 and SM103. The
public ABI and output semantics stay unchanged: 2-D CUDA logits,
temperature absent/scalar/per-row, PDL support, and a fresh non-aliasing
output. Unsupported devices and launches retain the existing
OnlineSoftmax fallback.

This refresh (head `73e45691`, rebased on current `main`) adds a
**row-caching cluster route** and re-qualifies the whole dispatcher on
both GB300 (SM103) and B200 (SM100). The previous head `f0edac69` read
every large row twice (cooperative bootstrap) or made three L2 passes
over it (rowwise); the new route reads and writes each row exactly once.

### Row-caching cluster route (route 5)

`csrc/blackwell_softmax_cached_cluster.cu` holds ten generated kernels,
`C x T` for `C in {1, 2, 4, 8, 16}` CTAs per row and `T in {4, 8}` tiles
of 8 fp32 per thread:

- a row is split across a cluster of `C` 256-thread CTAs; each CTA loads
its chunk once with 256-bit vectors into registers, computes its local
max/sum over the register cache, publishes them to shared memory, and
after **one** `barrier.cluster` pulls the `C` peer pairs through DSM to
form the row statistics;
- the normalized chunk is written back with 256-bit vectors; no
workspace, 128 B of dynamic shared memory;
- the variant policy (smallest cluster of at most 8 CTAs whose 32 KiB
chunks cover the row, 64 KiB chunks for rows wider than 256 KiB,
spreading short grids over more CTAs until the machine is covered twice,
4-tile specialization whenever the spread chunk fits) mirrors the
audited Cake dispatcher; clusters of 16 CTAs set
`cudaFuncAttributeNonPortableClusterSizeAllowed`;
- eligibility: 32-byte aligned `logits` and `output` base pointers,
`vocab_size % 8 == 0`, `vocab_size <= 262144`.

### Dispatch policy

| Route | Selection |
|---|---|
| 4 (SM103 MR515 exp2 t512/vec4) | `vocab_size == 32000`,
`temperature=None`, PDL disabled, `rows in {128, 512, 1024}` — the only
32K shapes where the frozen kernel still measures ahead of the cluster
route |
| 1 (warp-packed) | `rows <= 128`, `vocab_size <= 257`, scalar or
per-row temperature |
| 5 (row-caching cluster) | aligned rows as above |
| 2 (rowwise) / 3 (bootstrap) | the previous measured buckets for
`vocab_size % 8 != 0` |
| 0 (OnlineSoftmax fallback) | non-Blackwell devices, empty shapes, and
buffers whose base pointer is not 32-byte aligned (every generated route
issues 128/256-bit vector accesses; the previous head let a 16-byte
aligned storage-offset view reach the bootstrap kernel, which faults
with `cudaErrorMisalignedAddress`) |

The route observer exposes IDs `0..5` through `softmax_route` for tests.

## Evidence

Timing is GPU-only CUPTI activity tracing with cold-L2 flushing;
candidate and baseline are interleaved in the same process on the same
GPU. The Cake audit binds the kernel source hashes, the ratified 376-row
manifest and the harness into every lane receipt.

| | GB300 (SM103) | B200 (SM100) |
|---|---:|---:|
| 376-row manifest correctness | 376/376 | 376/376 |
| 41-row performance set, every row faster than FlashInfer 0.6.16 |
41/41 | 41/41 |
| geomean speedup vs FlashInfer 0.6.16 `sampling.softmax` | 2.194x
(worst row 1.144x) | 2.140x (worst row 1.146x) |
| geomean speedup vs this PR's previous head routes | 1.325x (min 0.991)
| 1.371x (min 1.000) |

### Same-session comparison against the previous head (`f0edac69`)

Public `flashinfer.sampling.softmax` built from source at both heads,
measured on the 41-row Cake performance set with identical protocol on
the same GPU:

| | GB300 | B200 |
|---|---:|---:|
| geomean PR-head time / refreshed-export time | **1.330x** | **1.374x**
|
| min ratio (rows at 0.99-1.00 are identical-kernel rows) | 0.996 |
0.998 |
| routes observed | [2, 4, 5] | [2, 5] |
| outputs match `torch.softmax` (atol=rtol=1e-3) | True | True |

### Roofline position

HBM-bound rows run at 0.53-0.79 of a same-session device-to-device copy
of the same bytes. The remaining gap is the one `barrier.cluster` per
row: its `arrive.release` lowers to `MEMBAR.ALL.GPU`, which drains the
SM's outstanding loads once per wave. Persistent register-pipelined and
TMA-bulk-staged variants that try to hide it were built and measured
slower (per-warp memory-level parallelism and smem-pass issue rate); the
analysis is recorded in the Cake evidence document.

## Correctness

- `tests/utils/test_sampling.py -k "softmax or blackwell"` from this
source tree: 381 passed / 12 skipped on B200 (final tree); 392 passed on
GB300 for the same kernels before the `cake_` file rename.
- Cake 376-row manifest (PyTorch oracle, `atol=rtol=1e-3`, all
temperature forms, all-`-inf` rows, PDL, fresh output): 376/376 on GB300
and on B200.
- compute-sanitizer memcheck, synccheck and racecheck: `0 errors` / `0
hazards` on GB300 and B200 for every `C x T` variant with
none/scalar/per-row temperature including all-`-inf` and half-`-inf`
rows.
- FusedTemperatureSoftmaxOp keeps calling the public dispatch path, so
`LogitsPipe([Temperature(), Softmax()])` matches direct calls.

## Checklist

- [x] JIT and AOT registration cover the dispatcher and all five device
translation units.
- [x] ABI, validation errors, temperature forms, PDL, route selection,
alignment fallback and fresh-output ownership are covered by tests.
- [x] 376/376 correctness and complete route coverage on GB300 and B200.
- [x] 41/41 contract performance floors on GB300 and B200; no row slower
than the previous head.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4876a10](https://github.com/flashinfer-ai/flashinfer/commit/4876a10ffd932c4a98f0cc6b275c2a0749236d81)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-09-23T09:45:45Z
- **提交信息**: feat(moe_ep): add SM107 block-scaled MegaMoE backends (#5384)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add NVFP4 and MXFP8 (E4M3/E5M2) support to `MoEEpLayer` on Rubin
(SM107),
with BF16 combine and output. In-kernel reduction is off by default
because
it uses nondeterministic atomics.

The kernels come from CuTe DSL MegaMoE `1667b47a`
([export
details](https://github.com/akaashrp/flashinfer/blob/sm107-megamoe/flashinfer/moe_ep/kernel_src/sm107/next_cutedsl_megamoe/VENDOR.md)).
The adapter handles Rubin's weight and scale layouts, clears combine
slots
for masked routes, and returns a separate output tensor by default so a
later
call cannot overwrite a previous result.

## 🔍 Related Issues

Based on #4601. The SM100 package move was merged separately in
[#5371](https://github.com/flashinfer-ai/flashinfer/pull/5371).

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

The CPU test run passed 222 tests and skipped 17 that need a GPU.
`pre-commit run --all-files` passed.

GPU testing covered CUDA graph replay and shared workspaces:
50 single-GPU cases and 16 EP4 cases per rank passed. Those runs used
`5bd5aeef`, which has the same Rubin execution code and benchmark as
this branch.

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release.
- [ ] Core changes are limited to a thin entry point (signature, shared
validation, feature-gate check, backend selection, handoff).
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included.
- [ ] Nothing is registered in `flashinfer/aot.py`, and no experimental
backend is reachable from `backend="auto"` without
`FLASHINFER_ALLOW_EXPERIMENTAL_AUTO_BACKENDS=1`. (Calling an
`@flashinfer_experimental_api` or naming a backend explicitly is itself
the opt-in and needs no environment variable.)
- [ ] **Test scope declared below.** The experimental CI lane runs
exactly these targets, so keep them as narrow as the change allows.

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
# One target per line: a directory or a file. (A pytest ::selector is not
# supported -- the sharding runner cannot consume one.) Must be under
# tests/experimental/ and must exist. Delete these comment lines and add yours, e.g.
#
#   tests/experimental/test_my_backend.py
#   tests/experimental/my_backend/
#
# Declaring the whole tree (tests/experimental/) is allowed but means every
# experimental PR pays for every other feature's tests, in every matrix cell.
```

## Reviewer Notes

GenPhase, `combine_nvfp4` and `combine_mxfp8` are follow-up work.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added SM107 (Rubin) MegaMoE support for distributed expert-parallel
inference.
  - Added NVFP4 and MXFP8 E4M3/E5M2 quantization with BF16 outputs.
- Added architecture-aware tuning, benchmarking, reusable tuning
results, and `--arch` selection.
- Added CUDA Graph-compatible execution and expanded input, routing, and
weight validation.
  - Added manual SM107 qualification workflows with preserved test logs.

- **Documentation**
- Added SM107 architecture, qualification, tuning, and operational
guidance.

- **Tests**
- Added correctness, boundary, distributed, staging, tuning, and runtime
qualification coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Md Saidul Hoque Anik <mhoqueanik@login-hecate04.hecate.clusters.nvidia.com>

### [d2c7d15](https://github.com/flashinfer-ai/flashinfer/commit/d2c7d153759127d39bdf25acba589c89a8c368fc)

- **作者**: Yuxian Qiu
- **时间**: 2026-09-23T07:04:07Z
- **提交信息**: [None][refactor] Unify PrimTS paged decode entry points (#5084)

## 📌 Description

Unify PrimTS FMHA and MLA paged decode around the existing reusable
wrappers:
`batch_decode_with_paged_kv_cache` and
`batch_mla_decode_with_paged_kv_cache`
now support both internally allocated and caller-owned workspace through
the
same wrapper `plan()` / `run()` path.

Current head: `1eb01e13a852dbb7dfe7cc10d761fd0563f46d6a`.
The branch was rebased onto `main` at
`711d3bc94e6d2130af8607320eec612899600084`.
#5082 is now merged into `main`; its `@flashinfer_experimental_api`
decorators
and experimental documentation/trace policy are preserved.

- When workspace is omitted, calculate its size, allocate it, and pass
it to the
wrapper. Caller-provided workspace uses the same execution path; there
is no
  separate caller-workspace launch helper.
- Keep `validate=True` as the default. Trusted execution uses
`validate=False`,
caller-owned workspace, explicit `max_kv_len`, and an explicit packed-Q
bound
when applicable. For capture, also provide output storage and warm the
exact
topology outside capture. This avoids metadata readback and tensor
allocation
  in the warmed, preallocated path.
- Keep FMHA convenience-call length specialization, fixed/packed Q,
supported
dtypes/cache layouts, scales, masks/windows, and output layout. FMHA
planning
preserves initialized external scratch with
`initialize_workspace=False`;
  callers still own workspace initialization, capacity, and lifetime.
- Remove the superseded standalone decode entry points and their
exports/lazy
imports. Workspace-sizing helpers, prepared plans, and reusable wrappers
remain.
- Separate device normalization from runtime CUDA validation and reuse
the same
resolver in both validated and trusted planning. Preserve explicit
device
  validation in the affected block-sparse callers.
- Remove capture-state checks from the four internal policy/compiler
cache
functions. Warmup remains the caller's responsibility; public
convenience
  API capture checks remain.
- Update existing attention tests, trace templates/examples, and
documentation.
  No new benchmark file or dedicated experimental test file is included.
No attention-kernel implementation or TensorRT-LLM source changes are
included.

## 🔍 Related Issues

Follow-up to #4829. Experimental API annotation changes were merged
separately
as #5082 and are now inherited from `main`.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` (using the existing installation).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`.

Changed-file/staged pre-commit checks passed, including mypy and Ruff.
`git diff --check` passed. The full-repository hook run is not claimed.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Latest local validation for the code committed as `1eb01e13`, on an
NVIDIA A40:

| Suite | Passed | Skipped |
| --- | ---: | ---: |
| FMHA decode, MLA decode, block-sparse attention, sparse metadata | 452
| 367 |
| Trace registry and template consistency | 697 | 0 |
| Total | **1,149** | **367** |

No failures in these local runs. Hardware-dependent tests were skipped;
the A40 does not validate the Blackwell attention kernels.

Attention targets (CUDA was initialized before invoking pytest for the
CUTLASS policy tests):

```python
import torch
import pytest

torch.cuda.init()
raise SystemExit(pytest.main([
    "-q",
    "tests/attention/test_attention_ts_decode.py",
    "tests/attention/test_attention_ts_mla_decode.py",
    "tests/attention/test_attention_ts_block_sparse.py",
    "tests/attention/test_attention_ts_q_token_kv_block_sparse_metadata.py",
    "--disable-warnings", "--tb=short",
]))
```

Trace targets:

```sh
CUDA_VISIBLE_DEVICES='' python -m pytest -q \
  tests/trace/test_template_registry.py \
  tests/trace/test_fi_trace_template_consistency.py
```

These runs used the existing development runtime with the worktree on
`PYTHONPATH` and `FLASHINFER_DISABLE_VERSION_CHECK=1`.

### B200 performance rerun — 2026-09-17

**Result: no meaningful GPU latency regression was observed in the eight
sampled
explicit-workspace cases, but the allocating MLA convenience API has a
reproducible wall-time regression. This is not an unconditional
no-regression
signoff.**

- Before: PR base `711d3bc94e6d2130af8607320eec612899600084`.
- After: current shared-wrapper implementation
`1eb01e13a852dbb7dfe7cc10d761fd0563f46d6a`, clean worktree.
- NVIDIA B200, 1000 W power limit; driver 610.57.04; Python 3.12.3;
  PyTorch 2.12.0a0+5aff3928d8.nv26.05 / CUDA 13.2; CUTLASS DSL 4.7.0.
- Same GPU and process for each A/B pair. Baseline API modules were
loaded from an
immutable Git archive in an isolated module namespace; common runtime
support
  is shared. Kernel Python source digests match exactly:
  `a31bc4e9fcc915aa7d08a8b4c7d90144fb4bceb09c795324234503f44bdfefc1`.
- Qwen-shaped FMHA: Hq=28, Hkv=4, D=128. DeepSeek-Lite-shaped MLA: H=32,
  latent=512, RoPE=64. Page size=32. BF16 uses fixed Q=1, B=1/64;
FP8 E4M3 uses packed Q=4, B=4, with FP16 FMHA output / BF16 MLA output.
- Five alternating-order rounds, 50 eager warmup calls per API; GPU
timing uses
FlashInfer CUDA-graph timing, 10 warmup replays and 100 measured replays
per
round, 10 calls per graph, warm L2. Reported values are medians of the
five
round medians. One-time compilation and correctness checks are excluded;
per-call planning, validation, and allocation remain in the eager/API
timings.
- The old standalone APIs are compared with the new canonical APIs using
  caller-owned workspace, explicit KV/Q bounds, preallocated output, and
  `validate=False`. Each pair uses identical input **and identical
workspace/output addresses**, sequentially, to remove
allocation-placement
bias. Host API time averages 100 calls per round and excludes the final
  synchronization; it is not a pure-Python self-time metric.
- All eight cases passed bitwise old/new eager-output equality,
convenience-output
equality, and explicit-API CUDA-graph replay equality. This checks
equivalence,
  not an independent numerical oracle or the full GPU test suite.

#### Explicit-workspace API

| Case | KV / Q | GPU µs, before → after | Latency Δ | Kernel ktoken/s,
before → after | Host API µs, before → after | Host Δ |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| Qwen B1 BF16 | 1536 / 1 | 9.776 → 9.776 | +0.00% | 102.29 → 102.29 |
98.27 → 70.49 | -28.27% |
| Qwen B64 BF16 | 1536 / 1 | 33.334 → 33.430 | +0.29% | 1919.94 →
1914.43 | 101.21 → 72.97 | -27.90% |
| DeepSeek-Lite B1 BF16 | 1536 / 1 | 9.981 → 9.981 | +0.00% | 100.19 →
100.19 | 214.77 → 196.92 | -8.31% |
| DeepSeek-Lite B64 BF16 | 1536 / 1 | 29.638 → 29.840 | +0.68% | 2159.36
→ 2144.77 | 65.49 → 47.96 | -26.77% |
| Qwen B4 FP8 | 257 / 4 | 5.885 → 5.885 | +0.00% | 2718.87 → 2718.87 |
100.12 → 70.26 | -29.83% |
| Qwen B4 FP8 | 4097 / 4 | 13.667 → 13.770 | +0.75% | 1170.69 → 1161.98
| 100.63 → 70.60 | -29.84% |
| DeepSeek-Lite B4 FP8 | 257 / 4 | 14.282 → 14.282 | +0.00% | 1120.32 →
1120.32 | 73.85 → 56.06 | -24.09% |
| DeepSeek-Lite B4 FP8 | 4097 / 4 | 17.968 → 17.968 | +0.00% | 890.47 →
890.47 | 74.61 → 56.63 | -24.10% |

Throughput is `B × Q / GPU latency`, expressed in thousands of query
tokens/s
for **one attention operation**, not end-to-end model-serving
throughput.
GPU latency changes are 0.00% to +0.75%, with overlapping per-round
ranges.
Explicit-workspace host API time decreases 8.3%–29.8%.

<details>
<summary>Per-round GPU median ranges (10 calls/graph)</summary>

| Case | KV | Before GPU µs, min–max | After GPU µs, min–max |
| --- | ---: | ---: | ---: |
| qwen B1 | 1536 | 9.571–9.981 | 9.571–9.776 |
| qwen B64 | 1536 | 33.022–33.533 | 33.018–33.533 |
| deepseek B1 | 1536 | 9.978–9.981 | 9.779–9.981 |
| deepseek B64 | 1536 | 29.027–30.096 | 28.822–30.250 |
| qwen B4 | 257 | 5.680–5.885 | 5.680–5.885 |
| qwen B4 | 4097 | 13.667–13.875 | 13.667–13.872 |
| deepseek B4 | 257 | 14.282–14.282 | 14.282–14.282 |
| deepseek B4 | 4097 | 17.968–17.971 | 17.968–17.973 |

</details>

#### Allocating convenience API — remaining regression

Here both revisions use their canonical API with workspace and KV bound
omitted,
default validation enabled, and preallocated output. These calls perform
allocation/metadata synchronization, so they are measured eagerly, not
captured.

| Case | KV | Before µs | After µs | Change |
| --- | ---: | ---: | ---: | ---: |
| Qwen B1 BF16 | 1536 | 226.65 | 223.43 | -1.42% |
| Qwen B64 BF16 | 1536 | 809.84 | 544.88 | -32.72% |
| DeepSeek-Lite B1 BF16 | 1536 | 314.80 | 353.51 | +12.30% |
| DeepSeek-Lite B64 BF16 | 1536 | 448.30 | 462.90 | +3.26% |
| Qwen B4 FP8 | 257 | 266.50 | 265.04 | -0.55% |
| Qwen B4 FP8 | 4097 | 349.40 | 309.05 | -11.55% |
| DeepSeek-Lite B4 FP8 | 257 | 197.22 | 204.81 | +3.85% |
| DeepSeek-Lite B4 FP8 | 4097 | 239.01 | 246.42 | +3.10% |

MLA convenience calls regress **3.1%–12.3%** in this run. The final
synchronization
adds less than 0.4 µs/call to these medians, so the synchronized eager
timings show
the same conclusion. Qwen convenience calls are not slower in the
measured matrix.

#### Independent core repeat

A fresh process repeated all four BF16 cases with **100 calls/graph**,
keeping
the same five-round / 100-replay / identical-storage controls. Absolute
GPU times
depend on graph length; compare before/after within each row.

| BF16 case | Before GPU µs | After GPU µs | GPU Δ | Convenience host
µs, before → after | Convenience Δ |
| --- | ---: | ---: | ---: | ---: | ---: |
| qwen B1 | 9.4051 | 9.4054 | +0.00% | 226.43 → 223.40 | -1.33% |
| qwen B64 | 32.9664 | 32.9570 | -0.03% | 814.84 → 543.18 | -33.34% |
| deepseek B1 | 9.3030 | 9.2928 | -0.11% | 316.21 → 350.64 | +10.89% |
| deepseek B64 | 31.6141 | 31.5218 | -0.29% | 447.73 → 465.18 | +3.90% |

The MLA convenience regression persists: +10.89% (B1), +3.90% (B64).
No source fix was made as part of this measurement request. The
shared-wrapper
implementation therefore meets the sampled GPU-latency goal, but still
needs
follow-up on allocating MLA API overhead before claiming no regression
across
all call modes.

Artifacts are outside the PR/worktrees:
`/home/yuxianq/scratch/prims-ts-perf-results/20260917-pr5084-1eb01e13/`
contains `bench.py`, `run-gpu.sh`, immutable `baseline/`, and
`core.log`, `extended.log`, `confirm.log` (all round samples, eager
timings,
and reusable-wrapper controls). No benchmark file was added back to the
PR.

Reproduction in the recorded Blackwell runtime, with the current
worktree on
`PYTHONPATH` and `FLASHINFER_DISABLE_VERSION_CHECK=1`:

```sh
python /path/to/artifacts/bench.py --baseline /path/to/artifacts/baseline
python /path/to/artifacts/bench.py --baseline /path/to/artifacts/baseline --extended
python /path/to/artifacts/bench.py --baseline /path/to/artifacts/baseline --graph-calls 100
```

### Remaining validation

- The B200 microbenchmark above validates sampled old/new output
equivalence,
CUDA-graph replay, and performance on the current head. The complete
Blackwell
correctness suite and end-to-end model-serving performance were not
rerun.
- Allocating MLA convenience API overhead still regresses; see the
measured
results above. A blanket no-performance-regression signoff remains open.
- As of 2026-09-17, the latest [public GPU CI
summary](https://github.com/flashinfer-ai/flashinfer/actions/runs/35203216623/job/105142716868)
reports **CI skipped — pending authorization**; the GPU matrix did not
run.
This is not a reported kernel-test failure. An authorized CI trigger is
still needed.

## 🔬 Experimental Track

- [x] This PR changes existing `@flashinfer_experimental_api` entries.
Experimental status comes from merged #5082; this refactor adds no new
backend.
- [ ] A new tracking issue with owner and graduation plan has been
provided.
- [ ] Core changes are limited to a thin entry point.
- [ ] Tests live in `tests/experimental/` and were validated on the
intended hardware.
- [x] No AOT registration or automatic experimental backend selection is
added.
- [ ] Experimental-lane test scope is declared below.

Per review, regression coverage stays in the existing `tests/attention/`
and
`tests/trace/` suites; the added experimental test module was removed.
The experimental scope parser only accepts existing targets under
`tests/experimental/`, so a valid declaration for that lane remains
unresolved.
The deleted target is not advertised as runnable, and unrelated
experimental
tests are not substituted. The existing targets above can be requested
explicitly
through the CI bot.

```experimental-tests
# No applicable target under tests/experimental/ is included in this PR.
# Existing attention/trace targets are listed above; experimental-lane scope remains open.
```

## Reviewer Notes

- Review workspace ownership/initialization and shared wrapper routing,
especially
  trusted capture calls and FMHA length specialization.
- Confirm use of the existing attention/trace suites for this refactor.
- Sampled B200 parity/capture checks passed. Full GPU-suite signoff and
the
  allocating MLA API performance regression remain outstanding.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Paged decode APIs now support caller-provided workspace buffers,
explicit maximum KV lengths, and optional validation.
- Trusted execution paths can support CUDA graph capture when required
inputs and workspace are supplied.
- Decode planning can optionally skip validation and workspace
initialization.

- **API Changes**
- Legacy standalone PrimTS decode entry points and exports have been
removed.
- Existing paged-cache APIs now provide the consolidated decode
interface.

- **Bug Fixes**
- Improved runtime-device resolution and validation across decode and
block-sparse operations.
  - Preserved published plans when replanning fails.

- **Documentation**
  - Updated API references and examples for the paged-cache interfaces.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4497
- **最后更新**: 2026-09-24T00:04:02Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 1
- **主要提交者**: Aryan Kumar

## AI分析总结

基于提供的提交记录和项目README，分析如下：

1.  **主要更新类型**：
    主要为**功能新增**。提交明确标记为`feat`，核心是为FastH3模型添加了新的推理模式和优化策略。

2.  **关键变更点及其与项目整体方向的关系**：
    *   **关键变更**：新增了针对FastH3模型、在MLX框架上运行的**8步推理**能力，并引入了“narrow ladder”优化。
    *   **与项目方向的关系**：FastVideo项目的目标是“快速”视频生成。这些提交直接服务于此目标，通过优化特定模型（FastH3）在特定硬件/框架（MLX，常用于Apple Silicon）上的推理流程（8步而非更多步数），旨在**提升推理速度、降低计算成本**。

3.  **对项目的影响和潜在意义**：
    *   **扩展能力与可及性**：为使用Apple Silicon设备的用户提供了新的、高效的推理选择，降低了硬件门槛。
    *   **保持架构灵活性**：提交说明强调“保留四步统一AdaLN缓存”，仅在特定条件下（快照声明自己的调度器偏移）启用新策略（显式DMD rungs）。这体现了在追求性能的同时，对现有代码架构和计算图简洁性的**维护**，有助于项目长期的可维护性。
    *   **增强模型生态**：丰富了项目支持的模型及其配置选项。

4.  **值得关注的技术点**：
    *   **AdaLN缓存的复用**：优化时复用现有的缓存机制，是效率与稳定性平衡的体现。
    *   **条件式调度策略**：使用“显式DMD rungs”的条件逻辑，表明优化是模型特定的，而非一刀切，这是一种精细化的性能调优手段。
    *   **“Ladder”优化**：“narrow ladder”可能指一种分步或分块的计算优化策略，旨在进一步减少中间计算或内存占用。

5.  **对项目发展的影响**：
    结合README可知，FastVideo是一个注重**可用性**（有文档、快速开始指南、定期开发会议）和**性能**的开源视频生成项目。本次提交：
    *   **强化性能优势**：直接贡献于“Fast”的核心价值，使项目在特定平台上的竞争力更强。
    *   **推动易用性**：MLX后端支持能让更多开发者（尤其是Apple生态开发者）更方便地使用和集成。
    *   **体现社区活跃与方向**：合并到主分支的流程显示了项目活跃的开发状态。提交内容表明社区正在积极进行**模型推理的深度优化**，这是项目走向成熟和广泛部署的关键一步。

## 详细提交记录

### [8760eb7](https://github.com/hao-ai-lab/FastVideo/commit/8760eb7a0677cc2582ce4c990e2e1c3a121eb149)

- **作者**: Aryan Kumar
- **时间**: 2026-09-23T19:42:03Z
- **提交信息**: [feat] Add FastH3 8-Step V2 MLX inference (#1863)

Keep the four-step uniform AdaLN cache, and use explicit DMD rungs only when the snapshot declares its own scheduler shifts.

### [361f919](https://github.com/hao-ai-lab/FastVideo/commit/361f919c882d058a13cb6ca5ed75c97a0e68f427)

- **作者**: Aryan Kumar
- **时间**: 2026-09-23T18:06:55Z
- **提交信息**: [feat]: add a narrow FastH3 8-step MLX ladder

Keep the four-step uniform AdaLN cache, and use explicit DMD rungs only when the snapshot declares its own scheduler shifts.

### [8b5377a](https://github.com/hao-ai-lab/FastVideo/commit/8b5377aab2db28d2252191192a031f79f56edc7d)

- **作者**: Aryan Kumar
- **时间**: 2026-09-23T17:52:20Z
- **提交信息**: Merge remote-tracking branch 'origin/main' into aryan/pr-1863-fasth3-8step

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34593
- **最后更新**: 2026-09-23T21:05:33Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: hf-security-analysis[bot]

## AI分析总结

**1. 主要更新类型**
安全加固与CI/CD（持续集成/持续部署）基础设施维护。

**2. 关键变更点及其与项目整体方向的关系**
*   **固定GitHub Actions版本至具体提交哈希值**：此变更旨在防止因上游Action版本（如标签`v4`）被篡改而导致的供应链攻击，确保每次构建使用的代码版本是确定且可审计的。
*   **精细化配置作业（Job）的GITHUB_TOKEN权限**：每个CI作业仅被授予执行其特定步骤所需的最小必要权限，避免了因权限过大而可能产生的潜在安全风险。
这两个变更均属于DevSecOps（开发安全运维）范畴，其关系到项目自动化开发与发布流程的安全性，是保障这个被广泛使用的开源库供应链安全的关键环节。

**3. 对项目的影响和潜在意义**
*   **提升安全基线**：显著增强了仓库及其下游用户的CI/CD管道安全性，降低了恶意代码注入的风险。
*   **增强可信度**：体现了维护团队对项目安全性的高度重视，有助于建立开发者社区的信任。
*   **符合行业最佳实践**：将安全控制点左移到开发流程中，为项目长期、健康的演进提供了更坚实的基础设施保障。

**4. 值得关注的技术点**
*   **供应链安全防护**：具体实践了“固定依赖版本”这一关键安全原则。
*   **最小权限原则应用**：通过`permissions`字段实现作业级别的访问控制，是GitHub Actions安全配置的范例。

**5. 基于项目背景对项目发展的影响**
diffusers作为HuggingFace生态中广泛使用的核心生成模型库，其构建、测试和发布流程的可靠性与安全性至关重要。这些提交并非添加新功能，而是对项目“看不见的”开发基础设施进行至关重要的安全加固。它们确保了项目自身的开发过程本身是安全、可靠的，这对于一个被大量开发者和应用所依赖的开源项目来说，是保障其长期可持续发展和维护良好声誉的基石。

## 详细提交记录

### [0377f0c](https://github.com/huggingface/diffusers/commit/0377f0c1b34e3ff313d41edad1bd79c2ed8bb5ec)

- **作者**: hf-security-analysis[bot]
- **时间**: 2026-09-23T14:05:59Z
- **提交信息**: Pin GitHub Actions to commit SHAs (#14853)

A tag is mutable: whoever controls the action's repository can move
`v4` to different code, and the next run picks it up with no diff to
review. Pinning to the commit SHA freezes the code that runs today.

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [256e9fb](https://github.com/huggingface/diffusers/commit/256e9fbc0bf9447aab4ec58cb74b419a4586e7b8)

- **作者**: hf-security-analysis[bot]
- **时间**: 2026-09-23T12:39:08Z
- **提交信息**: Scope GITHUB_TOKEN permissions per job (#14852)

A job with no `permissions:` block inherits whatever the repository
hands out. Each block added here grants what that job's own steps
need and nothing more.

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-08-31T08:28:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13174
- **最后更新**: 2026-09-23T16:57:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36381
- **最后更新**: 2026-09-23T23:49:42Z

## 提交统计

- **昨日提交总数**: 44
- **提交者数量**: 23
- **主要提交者**: linhu-nv, iridiumine, zijiexia

## AI分析总结

根据提交记录分析，SGlang仓库昨日提交的更新呈现多元化、深层次的特点，主要体现在以下几个方面：

**1. 主要更新类型**
*   **重构与优化**：占比最大，尤其是围绕 `LayerCommunicator` 对多个MoE模型（如Qwen3-MoE、DeepSeek-V2等）的通信路径进行整合与统一，并优化了服务器配置和运行时上下文注释。
*   **性能提升**：包含针对特定硬件（如AMD ROCm、NPU）和模型（如MiniMax-M3、Diffusion模型）的算子融合、计算图优化与内存访问改进，旨在提升推理吞吐量和降低延迟。
*   **功能增强**：新增了对特定模型架构（如Kimi K3）的支持（D FLASH），并引入了新的指标监控（前向占用率）。
*   **Bug修复与稳定性**：解决了潜在的死锁、重复残差、配置迁移遗留问题等，并修复了在特定场景下CUDA图重放不正确、专家计数错误等问题。
*   **文档与测试**：更新了H200的使用配方，清理了过时的测试代码。

**2. 关键变更点及其与项目整体方向的关系**
*   **统一通信抽象**：对大量MoE模型引入/扩展 `LayerCommunicator` 的使用，是项目代码架构向更统一、可维护方向演进的关键一步，有助于简化新模型的集成。
*   **多硬件后端适配**：大量提交涉及AMD ROCm、NPU（昇腾）等后端的优化与功能支持，体现了项目致力于构建一个**高性能、跨硬件平台**的LLM推理引擎的战略方向。
*   **特定模型与场景优化**：对MiniMax-M3、Nemotron、Diffusion模型等的深度优化，表明项目正在从通用推理引擎向能**高效支持前沿、复杂模型**的平台发展。
*   **内存与计算效率**：在 `mem_cache`、JIT编译器、CUDA图等方面的改进，直接服务于降低推理资源消耗和延迟的核心目标。

**3. 对项目的影响和潜在意义**
*   **提升代码质量与维护性**：大规模的重构将降低未来开发和维护复杂模型的成本。
*   **扩大硬件生态**：对AMD、NPU等后端的持续优化，将吸引更多使用不同硬件生态的开发者和用户，拓宽项目的应用基础。
*   **增强核心性能**：性能优化提交持续积累，将巩固SGlang在推理效率上的竞争力。
*   **提高系统健壮性**：大量的Bug修复提升了生产环境下的稳定性和可靠性。

**4. 值得关注的技术点**
*   **LayerCommunicator重构**：通过统一不同MoE模型的FFN退出和并行放置逻辑，是架构上的重要创新。
*   **D FLASH支持**：为Kimi K3等模型提供新的FlashAttention变体支持，可能是为了处理特定内存访问模式。
*   **无损融合**：在Diffusion模型中（如SenseNova RoPE、QKV拼接）实现“无损”算子融合，表明优化在追求极致性能的同时保持了计算精度。
*   **Speculative KV**：通过请求拥有的推测性KV缓存来降低解码启动延迟，是投机执行思想在KV缓存管理上的应用。

**5. 对项目发展的影响**
这些提交共同推动SGlang向一个**更成熟、更高效、更易用**的工业级推理框架演进。通过统一内部抽象、深耕多硬件支持、针对前沿模型进行深度优化，项目正在增强其**作为一站式高性能LLM部署解决方案**的吸引力，为未来支持更大规模、更复杂的模型部署奠定了坚实的技术基础。

## 详细提交记录

### [ffac53d](https://github.com/sgl-project/sglang/commit/ffac53d779c08dcdab2d07e5e2a41dba83f0e65c)

- **作者**: zijiexia
- **时间**: 2026-09-23T23:49:35Z
- **提交信息**: [Doc] Add H200 recipes to MiMo-V2.6 cookbook (#40969)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [542a043](https://github.com/sgl-project/sglang/commit/542a043f1b68796d269ef1ee11be7865f8d4a5f1)

- **作者**: Yueming Yuan
- **时间**: 2026-09-23T23:06:02Z
- **提交信息**: [RL] Release the weight-checker snapshot once compare passes (#37284)

### [208f6f7](https://github.com/sgl-project/sglang/commit/208f6f7501f748e70b3aaab9fc96ec659d39463b)

- **作者**: James Liu
- **时间**: 2026-09-23T22:58:39Z
- **提交信息**: [Spec] Support DFLASH for Kimi K3 (#40794)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3f69789](https://github.com/sgl-project/sglang/commit/3f697899a3a549379b7f534847ebd7f0c2683e11)

- **作者**: Alison Shao
- **时间**: 2026-09-23T22:55:02Z
- **提交信息**: ci: reinstall torch/triton left incomplete by a cancelled job (#40819)

### [0010f56](https://github.com/sgl-project/sglang/commit/0010f56a0d3cdb13b6254a8fe2ac5fd94010959c)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T22:33:54Z
- **提交信息**: [Test] Remove obsolete configuration migration guards (#40976)

### [6fe4b66](https://github.com/sgl-project/sglang/commit/6fe4b66f5c80a1179e130b6c01c1ba6728bfefd9)

- **作者**: Yueming Yuan
- **时间**: 2026-09-23T22:13:42Z
- **提交信息**: [RL] Keep pause_generation and weight updates from deadlocking each other (#40779)

Co-authored-by: maocheng23 <maocheng@berkeley.edu>
Co-authored-by: Zhichenzzz <zczeng@uw.edu>

### [79fec59](https://github.com/sgl-project/sglang/commit/79fec592a8fd6160e31d14d79b6506dc125d1047)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:57:25Z
- **提交信息**: [Refactor] Read parallel placement in consumers (#40638)

### [f2a1366](https://github.com/sgl-project/sglang/commit/f2a1366584e1ca152fa7afce719e9254e06e0f8b)

- **作者**: Chunan Zeng
- **时间**: 2026-09-23T21:50:13Z
- **提交信息**: MiniMax-M3: wave64 histogram-select decode top-k, and raise kMaxNumBlocks for CUDA graphs (#36560)

Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <mikevin920@gmail.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [4fa2c9c](https://github.com/sgl-project/sglang/commit/4fa2c9c1de7bf585f51fa07b5cb0fcc9644f71aa)

- **作者**: Chunan Zeng
- **时间**: 2026-09-23T21:49:10Z
- **提交信息**: MiniMax-M3: run the sparse prefill main attention through AITER Gluon paged attention (#36546)

Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Alex Sun <alex.s@amd.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: Kevin Mi <mikevin920@gmail.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>
Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>

### [f766397](https://github.com/sgl-project/sglang/commit/f766397f2eda00dca68a7f94c3634dfc7709392f)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:47:13Z
- **提交信息**: [Refactor] Trim server configuration and runtime context comments (#40971)

### [c39a1c0](https://github.com/sgl-project/sglang/commit/c39a1c06632bf0d5c42a3c252d7ddf55f35cdc6d)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-23T21:46:28Z
- **提交信息**: [mem_cache] Free the rows below the SWA evict floor on all-SWA request release (#40798)

### [ab0c31b](https://github.com/sgl-project/sglang/commit/ab0c31bd94f3724723e001d68ec701a6f011f2e9)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:43:41Z
- **提交信息**: [Refactor] Move eleven more MoE models to LayerCommunicator.ffn_exit (#40871)

### [e1048a2](https://github.com/sgl-project/sglang/commit/e1048a215ce9bbf0d43f9ee0a4c4a2a9a94ecec7)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:42:58Z
- **提交信息**: [Refactor] Let LayerCommunicator own the FFN exit in Qwen3-MoE, DeepSeek-V2 and GLM4-MoE (#40870)

### [7dd9640](https://github.com/sgl-project/sglang/commit/7dd96407524de43be39c39265b62fce412671f63)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:41:55Z
- **提交信息**: [Refactor] Compare token layouts instead of group sizes when selecting communicator paths (#40869)

### [e31cbc0](https://github.com/sgl-project/sglang/commit/e31cbc01a2932d50cd16ad601ee1001b98970f38)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:41:14Z
- **提交信息**: [Fix] Stop deferring the last layer's FFN all-reduce in five models (#40868)

### [701cf7e](https://github.com/sgl-project/sglang/commit/701cf7e47e6815d49ce9aa4124e61d3db8e16f8a)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:40:33Z
- **提交信息**: [Refactor] Run Nemotron-H DP attention through the standard layer communicator (#40867)

### [379e8f9](https://github.com/sgl-project/sglang/commit/379e8f916b7ef74515e23abbcfdbe0d5d0dfcf5b)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:39:50Z
- **提交信息**: [Fix] Capture complete Nemotron auxiliary hidden states (#40801)

### [9ebe422](https://github.com/sgl-project/sglang/commit/9ebe42238baf923f5a9a214e891c8483cffbcf25)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:39:04Z
- **提交信息**: [Fix] Reduce Nemotron MTP attention outputs once (#40800)

### [0e80c73](https://github.com/sgl-project/sglang/commit/0e80c73c925eaaa9e8c9e22b5f4a0bc4b7c23096)

- **作者**: Cheng Wan
- **时间**: 2026-09-23T21:37:39Z
- **提交信息**: [Fix] Avoid duplicate residual in LongCat MoE shortcut (#40799)

### [9544585](https://github.com/sgl-project/sglang/commit/954458567e10257f1d8d5ff808d2dbc74fc26967)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-23T20:22:58Z
- **提交信息**: [mem_cache] Remove unreachable RadixCache paths in KV canary and HiCache accessors (#40807)

### [2909f84](https://github.com/sgl-project/sglang/commit/2909f84e3b2fc627bbc9de76ac71d1c295639a8c)

- **作者**: metamergebot
- **时间**: 2026-09-23T18:49:34Z
- **提交信息**: [JIT] Add an occupancy-preserving L1 carveout preference (#40767)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Oguz Ulgen <oulgen7@gmail.com>

### [890a960](https://github.com/sgl-project/sglang/commit/890a9605ce4f90766ba9005b03d9ff90d3c6e59b)

- **作者**: metamergebot
- **时间**: 2026-09-23T18:48:31Z
- **提交信息**: [Metrics] Log forward and forward+idle occupancy over total wall time (#40802)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>

### [4bb5611](https://github.com/sgl-project/sglang/commit/4bb5611dba682a2d3581456f1782e659aa3f96a7)

- **作者**: metamergebot
- **时间**: 2026-09-23T18:48:03Z
- **提交信息**: [Fix] Give the full prefill CUDA graph replay view the captured bucket's input_ids (#40851)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: fei-xx <135589532+fei-xx@users.noreply.github.com>

### [f2f223e](https://github.com/sgl-project/sglang/commit/f2f223e6978534a41a2725811659762e2cebea3e)

- **作者**: metamergebot
- **时间**: 2026-09-23T18:39:22Z
- **提交信息**: Allow attention layers to opt out of the prefill wrapper (#40683)

Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>
Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>

### [f2eebd5](https://github.com/sgl-project/sglang/commit/f2eebd5533a932adfc66fb7525a6ba741a61f417)

- **作者**: Byron Hsu
- **时间**: 2026-09-23T18:18:04Z
- **提交信息**: [RL] Fix Kimi K3 expert-count lookup for routed-expert capture (#40700)

### [7fef014](https://github.com/sgl-project/sglang/commit/7fef014d512e3f61e3a3f8b156a726142952f5be)

- **作者**: linhu-nv
- **时间**: 2026-09-23T17:31:13Z
- **提交信息**: feat(kv-hints): add kv hint envelope to request transport (#38891)

Co-authored-by: ishandhanani <82981111+ishandhanani@users.noreply.github.com>
Co-authored-by: Ishan Dhanani <ishandhanani@gmail.com>

### [5c154c2](https://github.com/sgl-project/sglang/commit/5c154c214df569403cb42c5dbb874e4f865aa379)

- **作者**: Even Zhou
- **时间**: 2026-09-23T15:38:14Z
- **提交信息**: Revert " [NPU] Enable piecewise CUDA graph support on NPU" (#40895)

### [c3e9852](https://github.com/sgl-project/sglang/commit/c3e985203a89cfb4a9abcb407f209006939754de)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-23T14:42:03Z
- **提交信息**: [Diffusion] Remove unused standalone benchmarks and deduplicate kernel tests (#40924)

### [8993f79](https://github.com/sgl-project/sglang/commit/8993f790be4cb25a955d90c9cde6882d2dcddb99)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-23T14:37:22Z
- **提交信息**: [Diffusion] Fuse lossless SenseNova RoPE for 5% faster H200 inference (#40374)

### [4e60d70](https://github.com/sgl-project/sglang/commit/4e60d70ba406ef195a7d2090e55ad040ba584e1c)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-23T14:20:14Z
- **提交信息**: [Diffusion] Fuse Joy Image Edit QKV concatenation and avoid QK copies (#40494)

### [172b1b4](https://github.com/sgl-project/sglang/commit/172b1b4825ac9865076b78ef2c0daa66c7cc39dd)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-23T13:16:58Z
- **提交信息**: [Diffusion] Accelerate Cosmos3 Edge on Hopper with lossless fusions (#40386)

### [16e353d](https://github.com/sgl-project/sglang/commit/16e353d93e4e6d870623bee3fe1ea62936475886)

- **作者**: iridiumine
- **时间**: 2026-09-23T13:02:54Z
- **提交信息**: [NPU] Skip fused gmm1+swiglu for swiglu_limit (SiLU-with-clamp) checkpoints (#40438)

### [3fdd63a](https://github.com/sgl-project/sglang/commit/3fdd63a5620df8e18074ecbf0b70532186ee1406)

- **作者**: iridiumine
- **时间**: 2026-09-23T13:02:39Z
- **提交信息**: [NPU] Fuse FIA KV-cache K/V writes into one npu_scatter_pa_kv_cache call (#40445)

### [abef3ef](https://github.com/sgl-project/sglang/commit/abef3efb643134ab340f77c84500509488f3f298)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-23T11:55:48Z
- **提交信息**: [Diffusion] Fuse rounded SwiGLU for quantized MiniMax-H3 MLPs (#40378)

### [2d25767](https://github.com/sgl-project/sglang/commit/2d257677598134fbb091ecf5f023d1d678ee8c26)

- **作者**: hanwlax
- **时间**: 2026-09-23T09:30:30Z
- **提交信息**:  [NPU] Enable piecewise CUDA graph support on NPU (#28417)

### [58f622e](https://github.com/sgl-project/sglang/commit/58f622ebc4b7cae7f330cc2ade6c498d08ce1e6f)

- **作者**: inkcherry
- **时间**: 2026-09-23T09:24:53Z
- **提交信息**: Reduce decode bootstrap latency with request-owned speculative KV (#38978)

Signed-off-by: inkcherry <mingzhi.liu@amd.com>
Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [4cd63da](https://github.com/sgl-project/sglang/commit/4cd63da9961950357414255a1df214aec017266f)

- **作者**: TianDi101
- **时间**: 2026-09-23T09:15:01Z
- **提交信息**: [Unified Cache] Dedup replicated MLA/DSA KV in the UMBP direct linker (#38778)

Co-authored-by: Duyi-Wang <duyi.wang@amd.com>

### [a89f849](https://github.com/sgl-project/sglang/commit/a89f8491589189e30e980c3bb9d9f31d73b9aa55)

- **作者**: xiaobochen-amd
- **时间**: 2026-09-23T09:07:54Z
- **提交信息**: [ROCm] Fuse the MLA q absorb into the RoPE + KV-write kernel on gfx950 (#38340)

Co-authored-by: JohnQinAMD <zhengsheng1997@gmail.com>
Co-authored-by: RuibinCheung <ruibzhan@amd.com>

### [401d5ae](https://github.com/sgl-project/sglang/commit/401d5aedf391657867470f255683be0b1a85431f)

- **作者**: siliangchen-amd
- **时间**: 2026-09-23T08:59:15Z
- **提交信息**: [AMD] Drop the unreachable vLLM fallback from ROCm FP8 activation quant (#40879)

### [de123f3](https://github.com/sgl-project/sglang/commit/de123f38bbc95ea9b14c5c01bab2cac89832b9e1)

- **作者**: Yoray Zack
- **时间**: 2026-09-23T08:51:30Z
- **提交信息**: [3/N] elastic-ep: Recapture decode CUDA graphs after scale-up (#33723)

### [aa0b65c](https://github.com/sgl-project/sglang/commit/aa0b65c7c79ca67ba96f0484de814f22b980cc6e)

- **作者**: Wang, FangYuan
- **时间**: 2026-09-23T08:35:56Z
- **提交信息**: [AMD] Fix DeepSeek-V4 accuracy by not passing num_token_non_padded to MoE topk (#39804)

Co-authored-by: Thomas Wang <thomawan@amd.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [48c3854](https://github.com/sgl-project/sglang/commit/48c3854620dd2e111ffaa357f4f986954bb86cc3)

- **作者**: RuibinCheung
- **时间**: 2026-09-23T08:24:08Z
- **提交信息**: [ROCm] feat: enable aiter allreduce fusion for GLM models (#39790)

Co-authored-by: xiaobochen-amd <xiaobo.chen@amd.com>

### [d4dcce1](https://github.com/sgl-project/sglang/commit/d4dcce12d4fcdb3eb694d54d6afd31628c2eb7ce)

- **作者**: MatsueYu
- **时间**: 2026-09-23T07:23:51Z
- **提交信息**: [npu] decoding procedure optimization on qwen3.5/3.6 (#35958)

### [0b0f947](https://github.com/sgl-project/sglang/commit/0b0f94726555fe9434a48284603dc4d4d5465030)

- **作者**: Ziru
- **时间**: 2026-09-23T07:12:43Z
- **提交信息**: [CPU] Add fused_sigmod_mul_cpu operators to the Meta Muse Glimmer model. (#39538)

Co-authored-by: Niu Ziru <niuziru@a4bf018d3341.jf.intel.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1285
- **最后更新**: 2026-09-23T07:30:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92546
- **最后更新**: 2026-09-24T00:26:17Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 30
- **主要提交者**: jack, aoshen02, Nicolò Lucchesi

## AI分析总结

基于vllm仓库的提交记录分析，主要更新类型、关键变更点及其影响如下：

**1. 主要更新类型**
*   **Bug修复**：这是本次提交的核心，尤其在**ROCm（AMD GPU）后端**、**JIT编译**、**量化模块**和**特定模型支持**方面，修复了内存错误、数值精度、编译失败等问题。
*   **性能优化**：重点优化了**MoE模型路由**、**Attention计算**（如避免CPU-GPU同步、RDNA架构特化）和**CUDA图应用**，旨在提升推理吞吐与降低延迟。
*   **CI/测试增强**：大量工作用于**稳定和扩展持续集成流程**，特别是针对新的AMD硬件（MI355）和修复测试环境问题。
*   **新功能/模型支持**：包括为**DeepSeek-V4**添加FIM渲染，以及支持**DiffusionGemma**等模型。
*   **重构与清理**：对量化接口和代码进行了模块化重构，提升了可维护性。
*   **文档更新**：修正了文档中的拼写错误。

**2. 关键变更点及其与项目整体方向的关系**
*   **深化多硬件支持，尤其是AMD生态**：大量ROCm相关的修复、优化与测试（约占1/3），体现了项目致力于成为**多硬件（CUDA、ROCm、XPU等）通用、低成本**LLM服务平台的核心目标，确保AMD用户也能获得稳定高效的体验。
*   **优化核心推理性能与效率**：对**MoE路由逻辑、Attention内核、CUDA图编译策略**的优化，直接服务于项目“**快速（fast）**”和“**廉价（cheap）**”的愿景，通过软件层面提升硬件利用率。
*   **提升量化技术的稳定性与灵活性**：修复了FP8、NVFP4等量化格式的问题，并重构了相关接口，旨在让**更复杂的低精度计算**更可靠、更易用，这对降低显存占用和成本至关重要。
*   **增强系统鲁棒性与开发者体验**：对CI的广泛改进（如修复初始化快照、调整测试配置）和代码清理，旨在提升项目开发流程的可靠性和代码质量，保障项目长期健康发展。

**3. 对项目的影响和潜在意义**
*   **短期影响**：显著提升了**系统稳定性**（尤其是修复各类崩溃和数值错误）和**特定场景的推理性能**。对AMD用户的支持力度明显加强。
*   **长期意义**：这些变更进一步巩固了vLLM作为**功能全面、硬件友好、生产就绪**的LLM推理引擎的定位。持续的后端优化和新模型支持，有助于吸引更广泛的开发者和企业用户，保持技术领先性。

**4. 值得关注的技术点**
*   **JIT编译策略调整**：默认关闭VllmRunner的JIT预热，并将MRV2采样器的JIT预热限定于ROCm，这表明项目团队正在**精细化管理**即时编译的启动开销与运行时性能的平衡。
*   **“VLLM_BATCH_INVARIANT”模式下的性能优化**：在该模式下默认使用可中断CUDA图而非`torch.compile`，使调优后的矩阵乘法配置能感知实际的批量大小（M值），体现了**对性能调优场景的深度考量**。
*   **Attention后端的动态适配**：修复了KV块大小未被所有Attention后端支持的问题，显示了项目在管理**多样化Attention实现**时的复杂性，需确保底层配置的兼容性。
*   **底层内核优化**：如为RDNA架构缩小Triton预填充KV分块、融合AITER静态FP8注意力输出等，展现了在**算子层面的持续精耕**。

**5. 基于README背景对项目发展的影响**
这些提交紧密围绕“**为所有人提供简单、快速、廉价的LLM服务**”的项目宗旨。通过**不断打磨多硬件支持**（特别是AMD平台），降低了用户的硬件锁定风险与成本。**密集的性能与稳定性修复**，直接提升了服务的可靠性和经济性。**新模型与功能的跟进**（如FIM渲染）则确保了项目的易用性和功能先进性。**CI与代码质量的提升**为应对未来的快速迭代和功能扩展打下了坚实基础，支撑项目持续向更成熟、更强大的服务框架演进。

## 详细提交记录

### [310f15d](https://github.com/vllm-project/vllm/commit/310f15d3548aef7c80d3a43ffd7899ea076006ea)

- **作者**: Nick Hill
- **时间**: 2026-09-23T23:54:48Z
- **提交信息**: [Bugfix][MRV2] Align dummy idx_mapping dtype to avoid runtime jit (#58462)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [89d9fd8](https://github.com/vllm-project/vllm/commit/89d9fd83e2888405bea16ac36bea0045e352a074)

- **作者**: Misha Goin
- **时间**: 2026-09-23T23:53:58Z
- **提交信息**: [CI] Disable JIT warmup by default in VllmRunner (#58452)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [21ee743](https://github.com/vllm-project/vllm/commit/21ee743f474a35a056e8d5ade2c9aa744e726e6e)

- **作者**: Kevin H. Luu
- **时间**: 2026-09-23T23:11:50Z
- **提交信息**: [CI][Bugfix] Limit MRV2 sampler JIT warmup registration to ROCm (#58465)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5fcc6e7](https://github.com/vllm-project/vllm/commit/5fcc6e7c7380c67ab1e1305ed2197b127f0535e5)

- **作者**: djramic
- **时间**: 2026-09-23T23:03:45Z
- **提交信息**: [ROCm][Bugfix] Fix TileLang mHC fused RMSNorm on 64-wide wavefronts (#58419)

Signed-off-by: Djordje Ramic <djoramic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8b660ce](https://github.com/vllm-project/vllm/commit/8b660ce96bc2e7ef164e7c9c26b969495a88f82c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T21:16:51Z
- **提交信息**: [ROCm][Test] Cover MoRI graph replay and output lifetime (#58093)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [97b1b12](https://github.com/vllm-project/vllm/commit/97b1b121176d405bcec861960dc605e9e41227e2)

- **作者**: 陈志谦
- **时间**: 2026-09-23T20:36:57Z
- **提交信息**: [Docs] Fix docstring typos (output_dytpe, kwrags, Abbrivations) (#55936)

Signed-off-by: simpleqt <89645338+simpleqt@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e26547a](https://github.com/vllm-project/vllm/commit/e26547adfb4970f3e3958695256a84566683a683)

- **作者**: Divy
- **时间**: 2026-09-23T20:36:35Z
- **提交信息**: [Bugfix] Pick a KV block size supported by every attention backend (#49845)

Signed-off-by: Divy <divy@coralbricks.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [34b0690](https://github.com/vllm-project/vllm/commit/34b069080d9f1622321333c6849fc50c08664d36)

- **作者**: Thang Nguyen
- **时间**: 2026-09-23T20:08:51Z
- **提交信息**: [CI] Select one GPU for the H200 initialized snapshot E2E step (#58351)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [711fc55](https://github.com/vllm-project/vllm/commit/711fc55c10a2bbbefcb12456c43ba5eca01be3f6)

- **作者**: Lio Einaudi
- **时间**: 2026-09-23T18:39:38Z
- **提交信息**: [Perf] Use breakable CUDA graphs (no torch.compile) by default under VLLM_BATCH_INVARIANT so the tuned matmul configs see the runtime M (#57586)

Signed-off-by: LioEinaudi <zhao3024667639@gmail.com>

### [f9ad9dd](https://github.com/vllm-project/vllm/commit/f9ad9dd6b495f7492fa975e0ac48164b090d99ad)

- **作者**: CBP
- **时间**: 2026-09-23T17:14:30Z
- **提交信息**: Doc: add DiffusionGemma to supported models (#46466)

Signed-off-by: Bruce <Bruce798858117@gmail.com>
Signed-off-by: Misha Goin <mgoin64@gmail.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [b5ea0c7](https://github.com/vllm-project/vllm/commit/b5ea0c71078bdbb0f1f9afd934d55156273fe5f8)

- **作者**: Simon Danielsson
- **时间**: 2026-09-23T16:44:12Z
- **提交信息**: [Bugfix][ROCm] Fix startup OOM in AITER MLA FP8 prefill workspace sizing (#57923)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>

### [c4f6ce4](https://github.com/vllm-project/vllm/commit/c4f6ce48749a092b02525af16947350305650573)

- **作者**: Dao007forever
- **时间**: 2026-09-23T16:39:04Z
- **提交信息**: [Bugfix][NIXL] Restore successful push completion reporting (#58188)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [c4cfd70](https://github.com/vllm-project/vllm/commit/c4cfd7007bad6f1125ef938feb656707b3ccab76)

- **作者**: Oxana Korzh
- **时间**: 2026-09-23T16:25:51Z
- **提交信息**: [CI][ROCm] Add an MI355 Kimi-K3 unit test group (#58012)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [8033bd0](https://github.com/vllm-project/vllm/commit/8033bd08c1d3626d499de040279d7476b6cd2a4a)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T16:16:31Z
- **提交信息**: [ROCm][CI] Validate Mooncake and NIXL prefill/decode accuracy (#58095)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [b715699](https://github.com/vllm-project/vllm/commit/b715699df45f091325b307c0f5ac874010fbb23e)

- **作者**: vorapolsiloai
- **时间**: 2026-09-23T16:11:57Z
- **提交信息**: [ROCm][Perf] Extend QK-norm/RoPE/KV-cache fusion to MRoPE (#50212)

Signed-off-by: Vorapol Assavasangthong <Vorapol.Assavasangthong@amd.com>
Co-authored-by: Santosh Hiremath <Santosh.Hiremath@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [0549e8d](https://github.com/vllm-project/vllm/commit/0549e8d0ab88d3edf152147e14171f964c6e6f07)

- **作者**: fxmarty-amd
- **时间**: 2026-09-23T15:35:30Z
- **提交信息**: [Quark] Remove quark-specific silent online quantization (#51800)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [f69cc7c](https://github.com/vllm-project/vllm/commit/f69cc7c178d5bd47cd9bc5cf4c2f41530b878aae)

- **作者**: Jinzhen Lin
- **时间**: 2026-09-23T15:22:45Z
- **提交信息**: [Quantization][Bugfix] Bump humming-kernels to 0.1.16 (#58054)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [9f07d02](https://github.com/vllm-project/vllm/commit/9f07d023d07f73d806a67b8616a0a35258da2fc5)

- **作者**: HDCharles
- **时间**: 2026-09-23T14:23:11Z
- **提交信息**: [Quantization] Enable humming wNaM asymmetric quant (zero_point) with compressed-tensors (#46528)

### [88afb9d](https://github.com/vllm-project/vllm/commit/88afb9dcac7672f8e4a16590e67c2f09fe173dff)

- **作者**: Ankit-Jaiswal-AMD
- **时间**: 2026-09-23T13:55:09Z
- **提交信息**: [CPU] Adds support for fp32 attention sinks (#56252)

Signed-off-by: Ankit Jaiswal <ankit.jaiswal@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [9ed8158](https://github.com/vllm-project/vllm/commit/9ed81581a896a5bf0448b26d43f52486a435f799)

- **作者**: Shuolei Wang
- **时间**: 2026-09-23T13:03:21Z
- **提交信息**: [Perf][MoE] Skip top-k slots routed to non-local experts in TritonExp… (#58051)

Signed-off-by: Shuolei Wang <shuoleiwang123@gmail.com>
Signed-off-by: Shuolei Wang <948904026@qq.com>

### [d95a896](https://github.com/vllm-project/vllm/commit/d95a896ea612a072ba986a708d7efb4de1547019)

- **作者**: jack
- **时间**: 2026-09-23T13:02:00Z
- **提交信息**: [Feature][Frontend] Add DeepSeek-V4 FIM completion rendering (#44229)

Signed-off-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: QwertyJack <7554089+QwertyJack@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [157bcb7](https://github.com/vllm-project/vllm/commit/157bcb7c489689dd34cf28d9c9970a465d326a03)

- **作者**: Gabriel Wu
- **时间**: 2026-09-23T11:52:28Z
- **提交信息**: [DSpark] Support pipeline-parallel targets in aggregated serving (#56956)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [15ed126](https://github.com/vllm-project/vllm/commit/15ed1262e70873a65582d82f7973784a0f11e5a2)

- **作者**: Nikhil Kulkarni
- **时间**: 2026-09-23T10:37:40Z
- **提交信息**: [Bugfix][Tool Parser] Migrate Granite to the streaming Parser Engine (#49648)

Signed-off-by: Nikhil Kulkarni <nikhilkulkarni1755@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [c961121](https://github.com/vllm-project/vllm/commit/c9611215195eaaaa49a9ef6b65c1b28abd15e8ed)

- **作者**: Tianyu Guo
- **时间**: 2026-09-23T09:25:32Z
- **提交信息**: [Bugfix] Disable prefix caching for encoder-only before model config hooks (#58287)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>

### [a22c637](https://github.com/vllm-project/vllm/commit/a22c637ed97d81aa342789f7c56c2690ee118bfc)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T09:19:58Z
- **提交信息**: [ROCm][Test] Check GDN prefill numerics and output ownership (#58091)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [e34489a](https://github.com/vllm-project/vllm/commit/e34489a54348717c84891e313b5066854b967225)

- **作者**: Yan Ma
- **时间**: 2026-09-23T09:18:52Z
- **提交信息**: [XPU] upgrade to PyTorch 2.14 (#56013)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Signed-off-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [c843f0c](https://github.com/vllm-project/vllm/commit/c843f0cab78b413f2b0a5c2282cb71e3a3937b11)

- **作者**: Gabriel Wu
- **时间**: 2026-09-23T09:03:20Z
- **提交信息**: [Bugfix][SM120][MLA] Support NoPE sparse MLA (GLM-5.3-Flash) on the FlashInfer SM120 backend (#55277)

Signed-off-by: Zihua Wu <13583761+lucifer1004@users.noreply.github.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [afec265](https://github.com/vllm-project/vllm/commit/afec265bca16d02350a2da1855cbb90dd4c7123b)

- **作者**: Nick Hill
- **时间**: 2026-09-23T08:51:52Z
- **提交信息**: [MRV2] Miscellaneous code cleanup (#57980)

### [36bc694](https://github.com/vllm-project/vllm/commit/36bc694889df8b6e12639c6c70464b9b37b1d536)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T08:44:54Z
- **提交信息**: [ROCm][CI] Include Python tooling in ROCm CI artifacts (#58271)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [56b3acb](https://github.com/vllm-project/vllm/commit/56b3acb55bb27c4c9df8c48e6effc343b986929c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T08:42:33Z
- **提交信息**: [ROCm][Bugfix] Keep zero MiniMax MXFP8 activation blocks finite (#58089)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [1904ed9](https://github.com/vllm-project/vllm/commit/1904ed9402ce81e7db4391841c2205bf785380d9)

- **作者**: lijipeng
- **时间**: 2026-09-23T08:39:27Z
- **提交信息**: [Perf][ROCm][Attention] Narrow the Triton prefill-attention KV tile on RDNA3/RDNA4 (#58225)

Signed-off-by: Jipeng Li <jipengli@amd.com>
Co-authored-by: GitHub Copilot CLI <noreply@github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [955bd6a](https://github.com/vllm-project/vllm/commit/955bd6abef5a253f43c462cedb4d7279edc9ddc3)

- **作者**: vllm-agent
- **时间**: 2026-09-23T08:29:11Z
- **提交信息**: [CI][Bugfix] Extend groupwise rms_norm scale tolerance to CUDA (#58252)

Signed-off-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>
Co-authored-by: kimi-no-na-wa <kimi-no-na-wa@users.noreply.github.com>

### [6632ed5](https://github.com/vllm-project/vllm/commit/6632ed559e2a02e2a71a4464ddff52bdd0809874)

- **作者**: Jiangyun Zhu
- **时间**: 2026-09-23T08:28:43Z
- **提交信息**: [Perf][Attention] Avoid CPU-GPU sync in DCP sequence lengths (#58169)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [96e203b](https://github.com/vllm-project/vllm/commit/96e203b08ed4b935051151989f550c9b6c6eba6e)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T08:17:13Z
- **提交信息**: [ROCm][Bugfix] Register MRV2 sampler JIT warmups (#58092)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [26879f3](https://github.com/vllm-project/vllm/commit/26879f3260425889401f2281f38b45303e0db70b)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T08:16:52Z
- **提交信息**: [ROCm][Compile] Fuse AITER static FP8 attention output (#58099)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [973a3be](https://github.com/vllm-project/vllm/commit/973a3be780bd8b0d2f69c3727fb022e90a06ed74)

- **作者**: aoshen02
- **时间**: 2026-09-23T08:16:20Z
- **提交信息**: [Refactor][Quantization] Make FP8 and MLA weight transforms reusable pure functions (#57732)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Yongye Zhu <zyy1102000@gmail.com>

### [9488318](https://github.com/vllm-project/vllm/commit/9488318c6a40d1923614fb2d189ca93dbeb25920)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-09-23T08:15:45Z
- **提交信息**: [Mooncake] Address review nits from #56855 (#57174)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Yifan Qiao <17067717+ivanium@users.noreply.github.com>

### [153242a](https://github.com/vllm-project/vllm/commit/153242a314153637999eb6ebe8dd830e63433bb6)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T08:06:15Z
- **提交信息**: [ROCm][CI] Add MI355 dense NVFP4 and MoRI kernel mirrors (#58281)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [a9f07d0](https://github.com/vllm-project/vllm/commit/a9f07d0bc59604d3979ba0f232469f4a80eb8175)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T07:37:23Z
- **提交信息**: [ROCm][CI] Mirror the three TurboQuant evaluation groups on MI355 (#58282)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [9127170](https://github.com/vllm-project/vllm/commit/9127170b880dc86e032c4acaf649c225fdeff3b1)

- **作者**: Matej Sirovatka
- **时间**: 2026-09-23T07:30:58Z
- **提交信息**: [Quantization] Select per-token NVFP4 MoE backends explicitly (#57176)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: S1ro1 <matej.sirovatka@gmail.com>
Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0f2a15c](https://github.com/vllm-project/vllm/commit/0f2a15c9277f34c9afe141cf578d1f02b3bebdfe)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-23T07:04:22Z
- **提交信息**: [Tests] Select V2 for diffusion scheduler unit tests (#58272)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-24
**监控日期**: 2026-09-23
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7034
- **最后更新**: 2026-09-24T00:27:23Z

## 提交统计

- **昨日提交总数**: 18
- **提交者数量**: 18
- **主要提交者**: Zhou Taichang, Yukim1, akshatvishu

## AI分析总结

根据提交记录和项目背景，vllm-omni 仓库昨日的提交可总结如下：

**1. 主要更新类型**
*   **Bug修复为主**：提交绝大多数标记为[Bugfix]，集中解决了核心调度、异步处理、硬件适配、模型推理等多个层面的稳定性问题。
*   **新模型支持**：新增了对“Ming-Image”图像生成模型的支持。
*   **功能与优化**：包括在Diffusion阶段引入请求级前缀缓存、通过NIXL优化AR到Diffusion的数据传输。
*   **工程与测试**：进行了NPU升级、CI流程增强（如添加评分守护）及代码清理。

**2. 关键变更点与项目方向关系**
*   **核心稳定性夯实**：多个修复（如修复阶段初始化锁反转、保护会话队列取消状态、清理AR运行器输出）直接关系到多模态模型服务（Omni-Duplex）在高并发和复杂交互场景下的健壮性。
*   **多模态能力拓展**：新增“Ming-Image”模型支持，延续了项目作为通用多模态服务平台的目标。
*   **硬件与性能适配**：NPU版本升级、Wan RMSNorm的NPU作用域限定，体现了对多样化硬件后端的持续优化。
*   **运维与质量保障**：CI增加夜间评分守护，旨在自动监控模型服务质量，保障项目持续集成和交付的可靠性。

**3. 对项目的影响和潜在意义**
*   **提升生产可靠性**：大量基础Bug修复显著提升了系统作为在线服务的稳定性和用户体验，这是项目走向成熟的关键一步。
*   **强化多模态支持**：新模型的加入直接丰富了平台的服务能力，吸引更多用户。
*   **优化资源利用**：缓存与传输优化旨在降低推理成本与延迟，符合项目“快速、低成本”的愿景。
*   **完善开发流程**：CI与代码清理有助于维护大型开源项目的代码质量和可持续发展。

**4. 值得关注的技术点**
*   **并发与状态管理**：修复“spawn-lock/device-lock inversion”、“cancellation preservation”等问题，反映了在复杂异步、多阶段调度系统中管理状态和锁的挑战。
*   **跨阶段数据流**：修复“Mooncake cross-stage KV layout mismatch”和“AR-to-diffusion payloads over NIXL”功能，涉及模型不同组件间高效、正确的数据传递。
*   **模型特异性优化**：如针对“Qwen-Image”的“短序列Fused QK-norm+RoPE”和“HunyuanImage3”的“DiT LoRA binding”修复，显示了对不同模型架构细节的深度适配。

**5. 对项目发展的影响**
结合项目“提供简单、快速、低成本的跨模态模型服务”的目标，这批提交表明项目正从功能构建阶段迈向**工程化完善与生产就绪阶段**。通过密集的Bug修复提升系统底座的稳定性，通过新模型支持扩大覆盖面，并通过性能优化和CI建设保障服务效率和质量。这有助于建立用户信心，吸引更多社区贡献者，并为在实际生产环境中部署大规模多模态应用奠定坚实基础。

## 详细提交记录

### [6daf5b3](https://github.com/vllm-project/vllm-omni/commit/6daf5b30f07cc0b3db87766d22fdf433f8a1a7c9)

- **作者**: wuli666
- **时间**: 2026-09-23T19:32:40Z
- **提交信息**: [Bugfix] Preserve cancellation in duplex session control queues (#7782)

Signed-off-by: wuli666 <421774554@qq.com>

### [5e6b904](https://github.com/vllm-project/vllm-omni/commit/5e6b9047c95eca49fa15587afd991b59e5e89fe0)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-23T18:36:56Z
- **提交信息**: [Bugfix] Drain the omni connector output on the main thread in the AR runner (#7750)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [b4737d3](https://github.com/vllm-project/vllm-omni/commit/b4737d30669c94f1a85a8c688e4106fb5a46aa63)

- **作者**: akshatvishu
- **时间**: 2026-09-23T17:04:51Z
- **提交信息**: [BugFix] Download Anima assets for README CI test (#7928)

Signed-off-by: akshatvishu <akshatnayak197@gmail.com>

### [d38566a](https://github.com/vllm-project/vllm-omni/commit/d38566ae80afd80ae362327d2e4c1cbc4011859a)

- **作者**: Zhou Taichang
- **时间**: 2026-09-23T17:03:06Z
- **提交信息**: [Bugfix][Core] Fix stage initialization spawn-lock/device-lock inversion (#7926)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>

### [7f867fb](https://github.com/vllm-project/vllm-omni/commit/7f867fb782f709a92776432ed47acaf3e4d5fec3)

- **作者**: summer
- **时间**: 2026-09-23T16:58:46Z
- **提交信息**: [Bugfix][Diffusion] Drop aborted request's orphaned async output (fix #6413) (#6439)

Signed-off-by: summer <128961079+zhang-keliang@users.noreply.github.com>
Co-authored-by: multica-agent <github@multica.ai>

### [1934d12](https://github.com/vllm-project/vllm-omni/commit/1934d121e2856a8a85a9c22a1cceaaa798094c02)

- **作者**: NumberWan
- **时间**: 2026-09-23T16:12:29Z
- **提交信息**: [Bugfix] Gate Qwen-Image fused QK-norm+RoPE on short sequences (#7780) (#7965)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [a473ae7](https://github.com/vllm-project/vllm-omni/commit/a473ae78c32ec6590e04831c60dad7c2540401a3)

- **作者**: Yancy
- **时间**: 2026-09-23T16:06:54Z
- **提交信息**: [Bugfix][HunyuanImage3] Fix DiT LoRA binding: namespace alias + GQA QKV de-interleave (#6802)

Signed-off-by: Asthenia <asthenia0412@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Asthenia <asthenia0412@gmail.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [21f167e](https://github.com/vllm-project/vllm-omni/commit/21f167eacd9b6fcc185097027e4d6b9bc0b70f46)

- **作者**: chickeyton
- **时间**: 2026-09-23T15:48:35Z
- **提交信息**: [CI/Build][MiniCPM-o] Gate Seed-TTS WER over chat completions instead of the native duplex path (#7963)

Signed-off-by: chickeyton <ngton2014@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [205aa01](https://github.com/vllm-project/vllm-omni/commit/205aa01c7b8e8a135ca7498cd6e6cf60919ac4ec)

- **作者**: Yukim1
- **时间**: 2026-09-23T15:34:56Z
- **提交信息**: [Diffusion][HunyuanImage3] Add request paged prefix caching (#7719)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [9a1a05f](https://github.com/vllm-project/vllm-omni/commit/9a1a05facdf1f93e87b56be1177a2030492eef27)

- **作者**: MichaelCaoo
- **时间**: 2026-09-23T15:17:45Z
- **提交信息**: [Bugfix][Core] Preserve static KV staging inputs in AR-Diffusion (#7921)

Signed-off-by: MichaelCaoo <139663530+MichaelCao0@users.noreply.github.com>

### [81bc711](https://github.com/vllm-project/vllm-omni/commit/81bc7116c19cfbdde95b1b8240435604f5c3ce6f)

- **作者**: Weiming Liao
- **时间**: 2026-09-23T14:59:29Z
- **提交信息**: [NPU] upgrade to v0.30.0 (#8027)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [d319d27](https://github.com/vllm-project/vllm-omni/commit/d319d276f98badee8f6ae1be2c40244343e49529)

- **作者**: Wang  fuyin
- **时间**: 2026-09-23T14:57:45Z
- **提交信息**: [Bugfix] Fix native Mooncake cross-stage KV layout mismatch (#8003)

Signed-off-by: Acerak01-fy <wfy2003324@163.com>

### [732d608](https://github.com/vllm-project/vllm-omni/commit/732d6085be530df75b9f0cdcce9ccb2d0abdc55b)

- **作者**: RyanYun09
- **时间**: 2026-09-23T14:48:10Z
- **提交信息**: [CI][Omni-DuplexEval] Add nightly scoring CI guard (#7773)

Signed-off-by: RyanYun09 <318555231+RyanYun09@users.noreply.github.com>

### [d521b3f](https://github.com/vllm-project/vllm-omni/commit/d521b3f917f68300cbc08b7592d9eebc1f7a1547)

- **作者**: Nick Cao
- **时间**: 2026-09-23T13:09:19Z
- **提交信息**: [Misc] remove legacy full_duplex alias for auto_response (#8024)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [71125f8](https://github.com/vllm-project/vllm-omni/commit/71125f80ad2f1ee473a7d46c81930e8c61681bb6)

- **作者**: Yuanheng Zhao
- **时间**: 2026-09-23T12:20:06Z
- **提交信息**: [New Model] Ming-Image (inclusionAI/Ming-Image-0.1-Design) Support (#8021)

Signed-off-by: Yuanheng <jonathan.zhaoyh@gmail.com>

### [cb5f508](https://github.com/vllm-project/vllm-omni/commit/cb5f508212befb16b48e5760f3b7508c457d6413)

- **作者**: Yuan Wu
- **时间**: 2026-09-23T10:26:53Z
- **提交信息**: [Feature] Transfer AR-to-diffusion payloads over NIXL (#6264)

Signed-off-by: yuanwu <yuan.wu@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [8953d08](https://github.com/vllm-project/vllm-omni/commit/8953d082c0327f1990e07d3804298d626a8550f3)

- **作者**: Sy03
- **时间**: 2026-09-23T10:17:53Z
- **提交信息**: [Bugfix] Fix Qwen3-TTS prefill probe on MRv2 runner (#8065)

Signed-off-by: Sy03 <1370724210@qq.com>

### [57d3e9f](https://github.com/vllm-project/vllm-omni/commit/57d3e9fdf82c06094ee0c0b39c79d24b247fe8c3)

- **作者**: Dong1017
- **时间**: 2026-09-23T07:08:02Z
- **提交信息**: [BugFix][Diffusion] Scope Wan RMSNorm patch to NPU (#8047)

Signed-off-by: GUOGUO <xwdong1998@163.com>

---
