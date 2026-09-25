# GitHub Stars 合并报告 - 2026-09-24

**合并日期**: 2026-09-25
**监控日期**: 2026-09-24
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


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2225
- **最后更新**: 2026-09-24T05:19:34Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2857
- **最后更新**: 2026-09-24T17:05:53Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: STwangyingrui, Bilang ZHANG

## AI分析总结

根据对仓库 `ModelTC/LightX2V` 昨日提交的分析，结合其作为“轻量级视频生成推理框架”的项目背景，总结如下：

**1. 主要更新类型**
本次提交主要涵盖了 **功能新增**、**性能优化** 与 **代码重构**。其中，功能新增与性能优化紧密结合，旨在提升框架的核心推理能力；重构则专注于改善开发与使用体验。

**2. 关键变更点及其与项目方向的关系**
*   **核心性能深化**：提交 `a4b8ce3` 为 `qwen-image-2.1` 模型引入了 **DiT 张量并行 (TP)/序列并行 (SP)**、**QwenVL FP8 量化与张量并行**、**CPU 卸载与共享权重** 以及 **VAE 并行** 等一系列混合并行与内存优化技术。这直接响应了项目“轻量视频生成”的核心目标，通过优化计算与内存效率，使得在有限硬件资源上运行更大、更复杂的视频生成模型成为可能。
*   **易用性与可维护性提升**：提交 `65935ca` 对推理配置和示例脚本进行了简化与重构。这降低了新用户的入门门槛，同时使项目结构更清晰，符合框架长期维护与发展的需要。

**3. 对项目的影响和潜在意义**
*   **性能边界拓展**：通过引入更精细的并行策略和量化支持（如 FP8），框架在单卡及多卡环境下的吞吐量和模型支持规模有望得到显著提升，直接增强了其在实际生产环境中的竞争力。
*   **用户体验优化**：配置简化使得框架更易于集成和定制，有利于吸引更多开发者和研究者采用，从而扩大社区影响力。
*   **生态系统巩固**：更新后对 RTX 5090 等硬件的示例适配以及基准测试数据的更新，表明项目在积极跟进硬件发展，为用户提供最前沿的性能参考。

**4. 值得关注的技术点**
*   **混合并行策略**：同时应用 SP/TP 于 DiT，以及 TP 于 QwenVL，展示了框架在异构模型组件上灵活部署并行计算的能力。
*   **内存高效技巧**：CPU 卸载结合 **共享权重** 的设计，是一种创新的内存优化方法，能有效降低多模块模型（如 DiT+VAE）的总内存占用。
*   **精度-性能权衡**：引入 **FP8 VAE 解码** 作为可选方案，为用户提供了在精度与速度之间进行权衡的灵活性。

**5. 对项目发展的影响**
这些提交是项目向 **“更高效、更易用”** 目标迈进的关键一步。性能优化的提交夯实了框架的**技术核心**，证明了其有能力处理尖端的视频生成任务；而重构的提交则改善了框架的**工程表面**，使其更具吸引力。两者结合，共同推动 LightX2V 从一个技术原型向一个成熟、可靠且用户友好的生产级推理工具演进，强化了其在轻量视频生成领域的定位。

## 详细提交记录

### [a4b8ce3](https://github.com/ModelTC/LightX2V/commit/a4b8ce30ac73ae561ec9d1a8bc6629e4aed9d2d8)

- **作者**: STwangyingrui
- **时间**: 2026-09-24T17:05:45Z
- **提交信息**: feat(qwen-image-2.1): add parallel inference and memory optimizations (#1561)

Add DiT SP/TP, QwenVL FP8/TP, CPU offload with shared weights, and VAE
parallelism. Support DiT/VAE compilation and optional FP8 VAE decoding.
Simplify RTX 5090 T2I/I2I examples and update 1K/2K benchmarks.

### [65935ca](https://github.com/ModelTC/LightX2V/commit/65935cad7f778a04a9da052de1c92ff9d5e2b2fa)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-24T13:07:38Z
- **提交信息**: refactor: simplify inference configs and example scripts(v1) (#1560)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2255
- **最后更新**: 2026-09-24T07:52:22Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

基于提供的提交记录和README摘要，现将分析总结如下：

1.  **主要更新类型**：本次提交属于**功能新增与增强**，旨在扩展项目现有的图像与视频生成控制能力。

2.  **关键变更点及其与项目整体方向的关系**：
    *   变更核心围绕“**Qwen Image 2.1**”模型的“**Control**”和“**Flex Forcing**”功能进行更新。这表明项目正在积极集成或优化特定的、可能更先进的图像基础模型能力。
    *   与项目方向的关系：README显示项目包含“CogVideoX-Fun”和“Wan-Fun”等多个面向创意应用的生成模型。此次更新**直接增强了项目中基于图像控制（如参考图、结构图）进行视频生成或编辑的技术路径**，是对其核心功能“Fun”（即有趣、可玩的生成应用）的深化和扩展。

3.  **对项目的影响和潜在意义**：
    *   **直接影响**：为用户提供了关于图像控制（Control）和灵活强制引导（Flex Forcing）的新参数或模式，**提升了生成内容的可控性与多样性**。
    *   **潜在意义**：可能意味着项目在探索更高效、更精准的生成控制方法，或者为新版本的图像/视频模型做好了适配，这有助于**保持项目在AIGC应用领域的技术先进性**。

4.  **值得关注的技术点**：
    *   **Qwen Image 2.1**：这是一个需要关注的技术组件，其更新可能涉及新的架构或训练方法，是实现更强控制力的基础。
    *   **Flex Forcing**：此术语可能指代一种新颖的、更灵活的条件强制应用机制，其具体实现方式是理解本次更新价值的关键。

5.  **对项目发展的影响（基于README背景）**：
    README表明“VideoX-Fun”是一个提供多种模型演示（如Hugging Face Spaces）的创意应用集合。本次提交**增强了项目的技术“弹药库”**，使其能支持更复杂、更具控制性的生成任务。这有助于项目吸引更多开发者与创作者，巩固其作为**一站式、可玩性强的AIGC生成工具平台**的定位，并为后续推出更高级的应用奠定基础。

## 详细提交记录

### [67e3b4b](https://github.com/aigc-apps/VideoX-Fun/commit/67e3b4b8184ae8ff61ab3e3fbdb68bb817f41515)

- **作者**: Bubbliiiing
- **时间**: 2026-09-24T07:52:16Z
- **提交信息**: Update Qwen Image 2.1 Control and Flex Forcing (#519)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6502
- **最后更新**: 2026-09-24T23:44:53Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 6
- **主要提交者**: Mingyang Wang, Yang Xu, eigen

## AI分析总结

FlashInfer 仓库在昨日进行了一次重要的综合更新，涵盖功能新增、性能优化、硬件适配及工程化改进，共同推动项目向更高效、更稳定、更易用的方向发展。

**一、 主要更新类型**
本次更新聚焦于**功能拓展与核心优化**。在功能新增方面，主要集中在为**MiniMax-H3**视频生成模型提供完整的算子支持，包括量化解包、融合归一化及密集自注意力内核；同时为新一代硬件（NVIDIA B200/B300）引入了实验性的**NVFP4解码注意力内核**（针对DeepSeek-V4模型）。性能优化方面，通过调整GEMM内核的瓦片尺寸、重用cuDNN注意力计划以及优化TopK化简器，显著提升了计算效率与资源利用率。工程化建设上，对多处测试策略进行了确定性配对覆盖优化，并通过提取公共参数校验辅助函数进行了代码重构，增强了项目的健壮性与可维护性。

**二、 关键变更点**
1.  **模型专属深度优化**：针对MiniMax-H3模型，实现了从输入量化到注意力计算的全栈优化内核，体现了项目为关键模型构建高性能计算路径的策略。
2.  **前沿硬件与精度支持**：新增针对SM100/SM103架构的**NVFP4解码内核**，并扩展了原生TopK算子的硬件覆盖，展现了项目对前沿计算硬件和极低精度推理的快速跟进能力。
3.  **核心路径修复与提效**：修复了cuDNN注意力路径中的多个Bug（如元数据布局、设备句柄处理），并重用其计算计划以减少开销，直接提升了核心推理路径的稳定性和性能。
4.  **工程化与易用性提升**：将测试参数矩阵优化为配对覆盖策略，降低了CI耗时；统一了参数校验逻辑，改善了代码质量与开发体验。

**三、 项目影响**
这些变更对项目产生了多维度影响：**性能层面**，在特定硬件（B200/B300）和模型（MiniMax-H3、DeepSeek-V4）上实现了显著的推理加速；**可靠性层面**，修复了cuDNN等关键路径的潜在错误，夯实了生产环境的基础；**开发效率层面**，测试与代码的优化加速了迭代周期，降低了贡献门槛。整体上，这些更新进一步强化了FlashInfer作为**高性能、多硬件、高可靠**AI推理内核库的定位，正逐步演进为一个深度适配前沿硬件与关键模型的优化平台。

**四、 技术关注点**
值得深入研究的技术点包括：
*   **数据移动最小化设计**：如为MiniMax-H3实现的“一写即用”量化打包，在单次HBM传输中完成QKV处理，是典型的高性能计算优化思路。
*   **硬件感知的内核生成与调度**：利用代码生成器（Cake）为不同硬件架构自动生成优化内核，以及根据序列长度动态调度自注意力内核，体现了可扩展的优化方法论。
*   **异构精度融合计算**：NVFP4 MLA内核巧妙地结合了NVFP4（QK）与FP8（PV）的BMM，并通过专用核处理长序列，展示了针对特定软硬件组合的深度定制能力。
*   **状态管理与工程实践**：安全复用cuDNN计算计划涉及复杂的设备端状态管理，而将校验逻辑重构为公共辅助函数则是大型C++/Python绑定项目的良好工程实践。

## 详细提交记录

### [224042b](https://github.com/flashinfer-ai/flashinfer/commit/224042b41555de908b1f5e59da015803e8937be1)

- **作者**: eigen
- **时间**: 2026-09-24T23:44:48Z
- **提交信息**: feat(cake_backend): MiniMax-H3 one-pass QKV quantize-and-pack helpers (NVFP4 + MXFP8, SM100a/SM103a) (#5527)

## Summary

MiniMax-H3 one-pass QKV quantize-and-pack helpers for SM100a/SM103a
(issue #4532, candidate 7; tracker #4254).

`flashinfer.cake_minimax_h3.MiniMaxH3QkvQuantizePack` reads BF16 `Q`,
`K`, `V` `[M, 56, 128]` (three tensors or the kind slices of one fused
`[M, 56, 3, 128]` projection output, read in place) and writes the
destination-major Ulysses send buffer `[P, M, 56/P, 3, 128]` for `P in
{1, 2, 4, 8}`, quantized per destination in one HBM pass:

- `nvfp4`: `uint8 [P, M, 56/P, 3, 64]` E2M1 pairs + `uint8 [P,
round_up(R, 128) * 8]` block-16 E4M3 scales (swizzled 128x4 per
destination, static global scale) — the layout consumed by
`MiniMaxH3Nvfp4PreAttention` (#5496).
- `mxfp8`: `float8_e4m3fn [P, M, 56/P, 3, 128]` + `uint8 [P, round_up(R,
128) * 4]` block-32 UE8M0 scales (swizzled 128x4 per destination) — the
layout consumed by `MiniMaxH3Mxfp8PreAttention` (#5060).

Both outputs are byte-for-byte what the segmented path (`torch`
destination copies + `fp4_quantize` / `mxfp8_quantize` per destination)
produces, including the zeroed scale-tile padding rows, so consumers of
the fused pre-attention send buffers need no change. The kernel owns
every byte of the physical ABI; no host-side clear or allocation happens
in the hot path and the operation is CUDA-graph capturable (one kernel
launch).

## Files

- `csrc/cake_minimax_h3_qkv_quantize_pack/sm_10{0,3}a/`: 16 generated
kernel + TVM-FFI binding pairs (2 formats x P in {1, 2, 4, 8} x 2
architectures).
-
`flashinfer/jit/cake_minimax_h3_qkv_quantize_pack{,_sm100a,_sm103a}.py`,
`flashinfer/jit/cake_minimax_h3_qkv_pack.py`: JIT routers
(`CompilationContext` targets, one route per `(P, format)`, `M` is a
launch parameter) and the AOT entry.
- `flashinfer/diffusion_ops/cake_minimax_h3_qkv_pack.py`,
`flashinfer/cake_minimax_h3.py`: operation + public class.
- `tests/test_minimax_h3_qkv_quantize_pack.py`: host tests (route
tables, ABI/layout, fused-slice binding) and GPU tests (byte equality
against the segmented reference for both formats, all `P`, tails and `M
= 1`).
- `benchmarks/bench_minimax_h3_qkv_quantize_pack.py`.

## Validation

Every generated program was validated on B200 (sm_100a), B300 and GB300
(sm_103a) over 80 shapes per architecture (48 production rows: `P in {1,
2, 4, 8}`, `T in {33472, 38592, 48768, 58944, 74240, 109952}`, `M = T /
P`; 16 tails; smoke `M in {1, 127, 128, 129}`; fused-slice, wide-range
and zero-block rows): `out_q` and `out_sf` byte-exact against the
reference on all rows; paired CUPTI timing of the FlashInfer operation
against the source launcher at parity (geomean 0.998, production rows
0.996-1.000).

Against the segmented path on the 48 production rows (paired, cold L2,
CUPTI): 10.5-11.3x (`nvfp4`) and 15.2-17.2x (`mxfp8`) faster on B200,
B300 and GB300; the kernel streams at 5.5-7.3 TB/s, i.e. at the
byte-matched streaming-copy ceiling of each GPU (0.90-1.08 of a
`torch.add` moving the same bytes; the residual on the 40 us `P = 8`
rows is the launch ramp shared by any kernel of that size).

Gates: `compute-sanitizer` synccheck + memcheck clean; upstream
`pre-commit` (ruff, mypy) clean on the touched Python files; the
generated `csrc` tree is excluded from clang-format like the other
generated exports.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added one-pass MiniMax-H3 QKV quantize-and-pack for NVFP4 and MXFP8,
with prepared and convenience APIs that support caller-provided outputs.
* Added JIT and ahead-of-time support for SM100a and SM103a, plus trace
definitions and examples.
* **Tests**
* Added coverage for output correctness, supported formats, hardware
routing, output layouts, CUDA graph replay, and prepared API behavior.
* **Chores**
  * Updated pre-commit exclusions for generated files.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9f2e6ca](https://github.com/flashinfer-ai/flashinfer/commit/9f2e6ca3e8d78a9b3548361934deb523d7cea3d4)

- **作者**: eigen
- **时间**: 2026-09-24T23:42:42Z
- **提交信息**: perf(cake_diffusion): 256x448 GEMM tile for the MiniMax-H3 FC1+SwiGLU NVFP4 operator (SM100a/SM103a) (#5513)

## Summary

Regenerates the MiniMax-H3 fused RMSNorm + AdaLN + FC1 + SwiGLU
operators for SM100a / SM103a from the generator with a **256x448
CTA-pair GEMM tile for the NVFP4 (W4A4) kernel**: two N=224
`cta_group::2` MMAs per K-set,
alternating TMEM scale windows (488 of 512 columns), 21 % fewer operand
bytes per FLOP, and a packed BF16 drain that
releases the TMEM accumulator before any SwiGLU math. BF16 and MXFP8
kernels are unchanged (the generated files are
regenerated from the same tree, so their text is identical apart from
the NVFP4 kernel and the host tail).

Rebased on `main` after #5506 (256-column quantized tiles) merged; this
PR carries only the NVFP4 tile change.

## API / layout change (NVFP4 only)

The NVFP4 weight-scale layout follows the tile:
`prepare_fc1_weight_nvfp4` now emits **128 combined 224-row sub-tiles**
(`n_tile_rows=112`, `NVFP4_FC1_SCALE_TILE_BYTES = 128 * 84 * 1024`)
instead of 112 combined 256-row tiles. The public
function signature is unchanged; weights prepared with the previous
layout must be re-prepared (the kernel reads the
new layout; there is no compatibility shim, matching the existing MXFP8
/ BF16 preparation contract). MXFP8 keeps
`112 * 42 * 1024`.

## Measured (paired interleaved CUPTI, GEMM kernel only, bit-exact vs
the previous output)

| arch | M = 4824 / 9648 / 38592 / 109952 | previous TF | this PR TF |
ratio |
|---|---|---|---|---|
| B200 | | 6012 / 5515 / 5389 / 5227 | 6133 / 5752 / 5575 / 5391 | 1.020
/ 1.043 / 1.035 / 1.031 |
| B300 | | 6486 / 6046 / 5707 / 5567 | 6663 / 6176 / 5846 / 5687 | 1.027
/ 1.021 / 1.024 / 1.022 |

Fused NVFP4 operator vs bare `mm_fp4` on the 47-shape production
contract: B200 1.051-1.286x (geomean 1.130, was
1.093), B300 1.122-1.788x (geomean 1.525, was 1.494); vs the segmented
FlashInfer NVFP4 chain 1.81-3.51x / 2.12-2.87x.

## Validation

- Generator-side 47-shape production contracts 47/47 correct on B200 and
B300 (NVFP4 and MXFP8); compute-sanitizer synccheck + memcheck 0 errors
on
  both arches; e2e slice 6/6 both arches.
- The exported operators were JIT-built and validated through FlashInfer
on B200 and B300 with the same checks as
`tests/diffusion_ops/test_minimax_h3_fc1_swiglu.py` (bf16 / mxfp8 /
nvfp4, rows 1 / 257 / 4824).


🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Improvements**
* Updated MiniMax-H3 FC1 SwiGLU processing for MXFP8 and NVFP4,
including GPU execution layouts.
* Adjusted NVFP4 weight-scale handling to match its updated processing
layout; MXFP8 weight-scale sizing remains unchanged.
  * BF16 operator entry points remain available.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3090def](https://github.com/flashinfer-ai/flashinfer/commit/3090defb672fabec5dafba757d73e32015cc3edc)

- **作者**: Adrian
- **时间**: 2026-09-24T22:48:03Z
- **提交信息**: test: prune TensorRT-LLM decode parameter matrices (#5418)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_trtllm_gen_attention_decode.py` to
`parametrize_product`. Regular pytest runs use deterministic pairwise
coverage, while `pytest --full` retains the exhaustive matrices for
nightly testing.

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
* Updated validation for trtllm-gen decode scenarios to sample pairwise
combinations of selected settings. Key dimensions remain fully crossed,
and normal-softmax cases are retained for each sampled mixed-dtype
configuration.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [a27f4f2](https://github.com/flashinfer-ai/flashinfer/commit/a27f4f2ace7e3c51801c19483537d4d77afbf68a)

- **作者**: Adrian
- **时间**: 2026-09-24T22:46:34Z
- **提交信息**: test: prune XQA parameter matrix (#5420)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_xqa.py` to `parametrize_product`. Regular pytest
runs use deterministic pairwise coverage, while `pytest --full` retains
the exhaustive matrices for nightly testing.

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
* Reduced the number of generated attention test combinations by
switching selected parameters to pairwise coverage. The tests continue
to cover combinations across those parameters.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [33457fa](https://github.com/flashinfer-ai/flashinfer/commit/33457fa1c79a80a53ba7d88257bbde118324b166)

- **作者**: Adrian
- **时间**: 2026-09-24T22:44:54Z
- **提交信息**: test: prune batch decode parameter matrix (#5410)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_batch_decode_kernels.py` to `parametrize_product`.
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

- **Tests**
- Updated batch-decoding test coverage so each pairwise parameter
combination is tested with every head-dimension and KV data-type value.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [454e7e3](https://github.com/flashinfer-ai/flashinfer/commit/454e7e368f6718d6646f118b24ee24f52a029f70)

- **作者**: Adrian
- **时间**: 2026-09-24T22:41:28Z
- **提交信息**: test: prune batch prefill parameter matrices (#5411)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_batch_prefill_kernels.py` to
`parametrize_product`. Regular pytest runs use deterministic pairwise
coverage, while `pytest --full` retains the exhaustive matrices for
nightly testing.

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

- **Tests**
- Updated prefill kernel tests to combine the existing `kv_len`,
`qo_len`, and `causal` value tuples with each pairwise parameter case.
- Kept the parameter values unchanged while changing how the test
combinations are generated.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: mingyangw <mingyangw@nvidia.com>

### [4260f91](https://github.com/flashinfer-ai/flashinfer/commit/4260f91e5e69045f24b12b6835729c5eea89f221)

- **作者**: eigen
- **时间**: 2026-09-24T22:05:58Z
- **提交信息**: feat(cake_fused_norm_combine): SM100 eight-peer fused residual-add + RMSNorm + BF16 combine (#5528)

## Summary

Adds `flashinfer.comm.cake_fused_norm_combine`, a Cake-generated fused
**residual-add + two-track RMSNorm + eight-peer BF16 combine** for SM100
(B200), with a CUDA IPC peer-mapped workspace
(`cake_fused_norm_combine_create_workspace` /
`cake_fused_norm_combine_destroy_workspace`).

One launch per rank: `residual_out = bf16(x + residual)`, per-track
RMSNorm with per-track weights into `norm_out`, the two normalized
tracks averaged into one BF16 contribution, and that contribution
reduced across the eight peers in ascending rank order with BF16
rounding after every addition into the replicated `collective_out`.
Below 256 tokens the exchange is a one-shot Lamport publication with a
320-thread concurrent-track local body; at and above it is a fence-free
two-round owner reduce (token `t` is owned by peer `t % 8`), which moves
`1.875 T` payload stripes per rank instead of `8 T`. Payload words are
self-validating (BF16 negative-zero sentinel), so no per-round
system-scope release fence is needed.

Scope: eight ranks on one node with CUDA IPC peer access, SM100, hidden
size 2560, two tracks, contiguous BF16 tensors, `T <= max_tokens`.

## Files

- `csrc/cake_fused_norm_combine/sm_100a/*.cu` — generated device and
tvm-ffi binding translation units (one module per variant).
- `flashinfer/jit/cake_fused_norm_combine.py` — verified source-only JIT
loader (per-file SHA-256, token dispatch, exact `sm_100a` flags).
- `flashinfer/comm/cake_fused_norm_combine.py` — public API and
workspace helpers; re-exported from `flashinfer.comm`.
- `tests/comm/test_cake_fused_norm_combine.py` — CPU inventory /
dispatch / layout / validation tests and an eight-GPU SM100 distributed
test.
- `.pre-commit-config.yaml` — generated sources excluded from
formatting.

## Validation


## Generated-program export evidence

Baseline: **Cake shape-dispatched fused norm-combine on the shared peer
workspace** at Cake revision `dcda1c5a59a6759f68103e6e09bfd5e14114a5da`.

## Hardware stages

- `sm_100a` / world size `8`: GPUs `NVIDIA B200`, capabilities `10.0`,
drivers `580.82.07`, UUIDs `GPU-0ffd69bb-925f-51b7-5bf9-cf7d33b7dbf1,
GPU-178a3c30-6bf3-f646-c0b6-dd0d06c9a0d9,
GPU-13e8fee4-cda7-26e6-8dc4-1df713a14982,
GPU-79b3270a-726b-3a03-2a0c-b9dd55d315c7,
GPU-59e1b920-111f-3aa1-1fdb-471b4b7e60f9,
GPU-6bf95ab9-f847-48b6-363d-8ceca1e59e18,
GPU-8fbef57d-9331-7dc5-8b26-7db756415512,
GPU-8037ad95-3e5b-68aa-ea78-957ff7be5df6`; shapes `ws8_bf16_t1,
ws8_bf16_t8, ws8_bf16_t64, ws8_bf16_t256, ws8_bf16_t1024,
ws8_bf16_t2048`.

Target revision: `a21dcfd96a48aa7592e475841fefbf7f4a28bfa3`.

Benchmark execution: `distributed_rank_set`; 3 counterbalanced groups,
20.000 ms warmup and 200.000 ms reportable budget per arm/group.
Each sample follows one unmeasured same-arm launch, state restoration,
and a fresh cold-L2 flush.

The complete semantic arguments and machine-readable receipts remain in
`summary.json`; the tables below retain every registered shape without
repeating those arguments.

## Per-shape results

| Shape | GPU | Route | Source ms | Export ms | Source / Export |
Correctness | Verdict |
|---|---|---|---:|---:|---:|---|---|
| ws8_bf16_t1 | G0 | parallel_lamport_fused | 0.019232 | 0.019296 |
0.996683x | pass | pass |
| ws8_bf16_t8 | G0 | parallel_lamport_fused | 0.016416 | 0.016128 |
1.017857x | pass | pass |
| ws8_bf16_t64 | G0 | parallel_lamport_fused | 0.020031 | 0.020064 |
0.998355x | pass | pass |
| ws8_bf16_t256 | G0 | owner_lamport_fused | 0.022400 | 0.022209 |
1.008600x | pass | pass |
| ws8_bf16_t1024 | G0 | owner_lamport_fused | 0.038431 | 0.038368 |
1.001642x | pass | pass |
| ws8_bf16_t2048 | G0 | owner_lamport_fused | 0.059232 | 0.059264 |
0.999460x | pass | pass |

## Per-shape comparison: Unchanged customer fused residual-add + RMSNorm
+ one-shot BF16 combine kernel

| Shape | Baseline ms | Paired export ms | Baseline / Export |
|---|---:|---:|---:|
| ws8_bf16_t1 | 0.020032 | 0.019296 | 1.038143x |
| ws8_bf16_t8 | 0.018848 | 0.016128 | 1.168651x |
| ws8_bf16_t64 | 0.022656 | 0.020064 | 1.129187x |
| ws8_bf16_t256 | 0.034527 | 0.022209 | 1.554640x |

## Geomeans over all correct timed rows

Gate-failing performance rows remain in these geomeans; only rows
without valid correctness and timing are excluded and remain visible
above.

| Shape tag | Timed rows | Denominator | Source ms | Export ms | Source
/ Export |
|---|---:|---:|---:|---:|---:|
| all | 6 | 6 | 0.026187 | 0.026089 | 1.003739x |
| customer_resolved | 4 | 4 | 0.019400 | 0.019297 | 1.005338x |
| production | 6 | 6 | 0.026187 | 0.026089 | 1.003739x |

### Geomeans: Unchanged customer fused residual-add + RMSNorm + one-shot
BF16 combine kernel

| Shape tag | Timed rows | Denominator | Baseline ms | Paired export ms
| Baseline / Export |
|---|---:|---:|---:|---:|---:|
| all | 4 | 4 | 0.023312 | 0.019297 | 1.208048x |
| customer_resolved | 4 | 4 | 0.023312 | 0.019297 | 1.208048x |
| production | 4 | 4 | 0.023312 | 0.019297 | 1.208048x |

Complete denominator: **true** (6/6).

All gates passed: **true** (6/6).


## 🔍 Related Issues

Tracked in #4254 (Cake-generated kernel progress tracker,
Communication).

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

## Reviewer Notes

The generated `csrc/cake_fused_norm_combine/sm_100a/*.cu` files are
mechanically exported and excluded from formatting; review the loader,
the public API and the tests. The eight-GPU test is skipped
automatically on nodes without eight SM100 devices.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added a BF16 fused normalization and combine operation for supported
SM100 setups with eight peers.
* Added public APIs to create, manage, and query workspace requirements
for the operation.
* Added automatic kernel selection based on token count, with input and
hardware compatibility checks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [653d211](https://github.com/flashinfer-ai/flashinfer/commit/653d211e8e706d94db854a80d375d0affd95e611)

- **作者**: eigen
- **时间**: 2026-09-24T21:48:54Z
- **提交信息**: feat(cake_fmha): MiniMax-H3 dense BF16 self-attention for SM120 (Cake kernel route + benchmark) (#5472)

## Summary

Dense self-attention cut of the MiniMax-H3 video DiT, targeting SM120
(RTX 5090 / RTX PRO 6000 Blackwell):

- dense, non-causal, BF16, 56 heads, head_dim 128, batch 1, packed token
count `S` (dynamic, 1 .. 131072)
- inputs/outputs are contiguous BF16 `[S, 7168]` rows (element `[t, h *
128 + d]`); the NHD `[S, 56, 128]` view is zero-copy
- the query is pre-scaled in BF16 (`bf16(1/sqrt(128)) = 0.08837890625`,
product rounded before softmax) and attention runs with `sm_scale=1.0`
- representative `S` values from the model's request types (T2VA / FL2VA
/ REF2VA at 124 and 345 frames, normal and SR-base resolutions): 15493,
17147, 30224, 37804, 41870, 42554, 44208, 52535, 57287, 104060, 108126,
118793

### Fused route: `flashinfer.diffusion_ops.minimax_h3_dense_attention`

One runtime-variable kernel does the row<->head re-layout, the BF16
query scale and the attention for any `1 <= S <= 131072`:

- `csrc/cake_minimax_h3_dense_attention_sm120a.cu`: generated SM120
device code (128-row query tile x 64-key tiles, 256 threads, one
persistent CTA per SM, TMA tile loads with 128B swizzle into a two-stage
K/V ring, `ldmatrix` + `mma.sync` m16n8k16, exp2 online softmax,
register-resident scaled Q tile, deferred softmax denominator reduction,
FA3-style ping-pong between the two warp groups through hardware named
barriers with per-warp `mbarrier` stage release, head-major work loop,
the items of the last persistent wave split across idle CTAs by K/V
range and merged in-kernel through a small per-device workspace, TMA
zero-fill for short `S`, key mask on the last tile) plus the TVM-FFI
host entry (tensor-map encoding, launch plan). The source also compiles
for SM90a/SM100a/SM103a; SM120 is the performance target and the
validated one.
- `flashinfer/jit/cake_minimax_h3_dense_attention.py` (JIT spec),
`flashinfer/diffusion_ops/cake_minimax_h3_dense_attention.py` (custom op
`flashinfer::minimax_h3_dense_attention`, `minimax_h3_dense_attention(q,
k, v, out=None)`; the zero-filled split-KV workspace is allocated once
per device from `minimax_h3_dense_attention_workspace_size()` and the
kernel rewinds its counters after every launch)
- `tests/diffusion_ops/test_minimax_h3_dense_attention.py`: FP32-oracle
checks at S = 1, 63, 64, 65, 128, 257, 1023, 4097 (`atol=rtol=1e-2` and
the request's fixed `atol=0.01, rtol=0.02`), pre-allocated output,
repeated launches of different sizes sharing the workspace, argument
validation.

### Benchmark: `benchmarks/bench_minimax_h3_dense_attention.py`

Times the fused route (`cake`), `single_prefill_with_kv_cache` (`auto`,
which routes to `fmha_v2` on SM120, and `fa2`) and PyTorch SDPA
(`efficient` / `cudnn` / `flash`) at the same boundary (the BF16 Q-scale
launch is included, host transfers are not), with CUPTI cold-L2 timing,
and checks every backend against a chunked FP32 oracle.

```
python benchmarks/bench_minimax_h3_dense_attention.py --suite short
python benchmarks/bench_minimax_h3_dense_attention.py --suite all --backends cake flashinfer_auto torch_efficient --json h3.json
```

## Measurements: RTX PRO 6000 Blackwell Server Edition (GB202, CC 12.0,
188 SMs)

torch 2.13 (CUDA 13.3), TensorRT-RTX 1.6.1.120 (`tensorrt_rtx_cu13`),
FlashInfer JIT for 12.0a. Every backend runs in the same process on the
same synthetic inputs; cold-L2 CUPTI timing, median of 5 after 2
warmups. "TRT-RTX engine" is the model's native subgraph (Shuffle ->
BF16 mul -> `IAttention` -> Shuffle) built with the request package's
`build.py` and executed through the `tensorrt_rtx` bindings; the other
columns are the `fmha_v2` route
(`single_prefill_with_kv_cache(backend="auto")` + Q-scale launch) and
PyTorch SDPA backends at the same boundary.

| S | kernel ms | TFLOP/s | TRT-RTX engine ms (kernel speedup) | FI auto
ms (kernel speedup) | cuDNN SDPA ms (kernel speedup) | flash SDPA ms
(kernel speedup) | efficient SDPA ms (kernel speedup) |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 15493 | 16.7 | 412 | 21.4 (1.283x) | 17.9 (1.071x) | 17.6 (1.055x) |
20.1 (1.204x) | 51.4 (3.075x) |
| 17147 | 20.2 | 417 | 26.3 (1.301x) | 22.7 (1.123x) | 21.2 (1.050x) |
24.2 (1.196x) | 62.0 (3.070x) |
| 30224 | 67.4 | 388 | 80.5 (1.194x) | 70.8 (1.050x) | 69.9 (1.036x) |
76.7 (1.138x) | 191.9 (2.847x) |
| 37804 | 105.1 | 390 | 125.1 (1.190x) | 111.1 (1.057x) | 109.6 (1.043x)
| 120.1 (1.143x) | 298.4 (2.840x) |
| 41870 | 129.9 | 387 | 153.6 (1.182x) | 136.3 (1.049x) | 134.5 (1.036x)
| 147.1 (1.132x) | 365.7 (2.815x) |
| 42554 | 133.9 | 388 | 159.3 (1.189x) | 141.5 (1.056x) | 139.5 (1.042x)
| 152.5 (1.138x) | 377.4 (2.817x) |
| 44208 | 144.9 | 387 | 171.6 (1.184x) | 152.5 (1.053x) | 150.5 (1.039x)
| 164.7 (1.137x) | 407.8 (2.815x) |
| 52535 | 204.3 | 387 | 242.0 (1.184x) | 215.3 (1.054x) | 211.7 (1.036x)
| 232.0 (1.135x) | 574.1 (2.810x) |
| 57287 | 243.4 | 387 | 288.8 (1.186x) | 256.0 (1.052x) | 251.8 (1.035x)
| 275.8 (1.133x) | 682.8 (2.805x) |
| 104060 | 800.7 | 388 | 996.8 (1.245x) | 877.0 (1.095x) | 831.9
(1.039x) | 924.0 (1.154x) | 2240.7 (2.799x) |
| 108126 | 867.1 | 387 | 1081.8 (1.248x) | 957.0 (1.104x) | 899.8
(1.038x) | 1007.1 (1.161x) | 2421.3 (2.792x) |
| 118793 | 1046.9 | 386 | 1316.1 (1.257x) | 1168.7 (1.116x) | 1089.5
(1.041x) | 1236.2 (1.181x) | 2932.8 (2.801x) |
- The fused kernel is 1.18x-1.30x faster than the TensorRT-RTX native
attention subgraph at every representative `S`, 1.13x-1.20x faster than
torch flash SDPA, and 2.8x-3.1x faster than memory-efficient SDPA.
- It beats every other same-process backend at every representative `S`:
cuDNN SDPA 1.035x-1.055x (the strongest peer; the previous 64-row
schedule was 0.977x-0.998x), the `fmha_v2` route 1.049x-1.123x. All
three kernels run at the 600 W board limit with equal cycle counts, so
the schedule work targeted energy per FLOP: the 128-row query tile
halves K/V L2 traffic (+6 % sustained clock) and the ping-pong between
the two warp groups recovers the tensor-pipe idle time of eight
lock-step warps; a dedicated TMA producer warp, an unrolled two-stage
ring and K double-buffering of the 64-row tile were measured and
rejected on the same node. The last-wave split-KV then removes the idle
tail of the persistent grid (cycles per launch -1.3 % at S=15493, -0.6 %
at 37804/44208, unchanged where the grid divides the work evenly);
FA3-style grouped MMA bursts and K/V L2 eviction hints were measured and
rejected on the same node (slower, and no cycle difference,
respectively).
- Correctness on GB202: 16 shapes (S = 1, 128, 257, 4097 and the 12
above) match the FP32 oracle with max |err| <= 0.0078 (S = 63..65) and
<= 0.00049 for S >= 15493; the fixed `atol=0.01, rtol=0.02` check passes
on every row. compute-sanitizer synccheck and memcheck report 0 errors
on SM120. The regenerated source passes the JIT route check at S = 1,
63, 64, 65, 128, 257, 1023, 4097, 15493 with flashinfer 0.7.0 on SM120
(two launches per size, shared workspace).

## Checks

- `ruff check` / `ruff format` clean (pre-commit pinned version)
- Tests skip without a CC 9.0 / 10.x / 12.x GPU.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added MiniMax-H3 dense BF16 attention for supported NVIDIA GPUs, with
optional reuse of a preallocated output buffer.
* Added a benchmark comparing attention implementations across token
lengths, with accuracy and performance results and options to select
test suites and backends.
* **Tests**
* Added coverage for output accuracy and validity, supported input
formats, invalid inputs, and preallocated output buffers.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ba87a55](https://github.com/flashinfer-ai/flashinfer/commit/ba87a557493a1f39fd45d7b3ded295c0a7478e8e)

- **作者**: Mingyang Wang
- **时间**: 2026-09-24T17:44:53Z
- **提交信息**: feat(mla): MLA SM100 auto mode (#5463)

<!-- .github/pull_request_template.md -->

## 📌 Description

Previously, `BatchMLAPagedAttentionWrapper(backend="auto")` selected
between FA2/FA3 soley based on architecture during object
initialization, despite the wrapper also supporting the cutlass backend,
and after PRs https://github.com/flashinfer-ai/flashinfer/pull/4018 and
https://github.com/flashinfer-ai/flashinfer/pull/5070, the trtllm-gen,
xqa, cutedsl, and cutile backends. This change adds a deterministic
SM100 auto policy to select between all available backends. Auto
selection is moved to plan time to allow for selection based on planning
information (shapes, features, etc.).

This change also enables some backend features that were previously
supported but not enabled in plumbing:
- cuteDSL: fp16 inputs/outputs, causal
- trtllm-gen: causal
- cuTile: page size 1, relaxed head counts restrictions, CKV d256,
causal Q1
- cutlass: causal Q1

B200 execution measurements compare the new auto with the original
architecture-only selection. Across 120 configurations in eager and
graph modes (240 combinations): 225 conclusive passes at the 1%
regression threshold, 15 inconclusive comparisons selecting FA2 under
both policies, and zero confirmed regressions above 1%. All 93
changed-backend combinations were over 5% faster in every measured
block. The ranking and native execution code are unchanged since these
measurements; subsequent planner refactors have separate correctness
coverage.

Full results: [B200 original FA2/FA3 selection versus new
auto](https://docs.google.com/spreadsheets/d/1KjoyUzG-ktBcUyrhZHjzYSng4bRvdhatuAntG8s4Obo)
— all 240 configuration/mode combinations, the 15 inconclusive outcomes,
per-block timings, and 32 separate targeted controls with best-backend
measurements.

## 🔍 Related Issues

Related to #4037.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file pre-commit checks passed, including clang-format, mypy, and
Ruff. This was scoped to every changed existing/new file; `--all-files`
was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Full target run on B100: **439 passed, 10 skipped** (all skips require
SM12x XQA):

```sh
pytest tests/attention/test_mla_wrapper.py tests/attention/test_mla_auto_backend.py tests/attention/test_mla_auto_backend_warning.py tests/utils/test_logging.py -q -rs
```

Separate B100 cuTile target: `pytest
tests/attention/test_mla_decode_cutile.py -q -rs` — **54 passed**. No
full-repository run or final native non-SM100 validation is claimed.

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

- The B200 all-backend performance sweep twice encountered an
unspecified CUDA launch failure during repeated execution of explicit
cuTile: BF16, batch32, heads128, Q1, page64, packed, noncausal, ragged
KV lengths2048/4096/8193. The isolated case passed; the cause remains
unresolved. Partial timings were excluded. The completed two-role
auto/original-auto comparison does not close this all-backend gap.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Automatic MLA backend selection now considers workload details and can
fall back when a backend cannot support a plan.
- Added experimental cuTile MLA execution, available for automatic
selection when explicitly enabled.
- Expanded MLA support for variable-length queries, adjacent-split KV
layouts, and additional data types and attention modes where supported.
  - Added dense MLA head-tiling planning support.

- **Bug Fixes**
- Improved plan validation, dense metadata alignment, error reporting,
and recovery after failed plans.
  - Improved CUDA Graph planning and backend fallback reliability.
  - Warnings now more accurately identify the external caller.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [28ae778](https://github.com/flashinfer-ai/flashinfer/commit/28ae778e49ab8f6104c59cc9d43efdca4343f91f)

- **作者**: eigen
- **时间**: 2026-09-24T11:19:31Z
- **提交信息**: feat(cake_megamoe_topk_reduce): publish the SM103a reducer export and enable the native reducer on B300 (#5509)

## 📌 Description

Publish the frozen Cake MegaMoE TopK reducer for **SM103a (B300)** next
to the existing SM100a (B200) drop, and let the SM100 NVFP4 CuTeDSL
MegaMoE backend use the native reducer on compute capability 10.3 as
well as 10.0. Follow-up to #5431, where @yzh119 asked why the reducer
was sm_100a-only: the kernel uses no SM100-specific instructions (plain
vectorized `ld.global.L1::no_allocate` loads, ordered no-FTZ
`fma.rn.f32x2` accumulation, `__launch_bounds__(256)`), so the limit was
the B200-only validation boundary, not the code. Internal tracking:
CAKE-551.

What changes (the `.cu` files are regenerated through the Cake exporter,
never hand-edited):

-
`csrc/cake_megamoe_topk_reduce/sm100a/{cake_megamoe_topk_reduce_kernels.cu,manifest.json}`:
the #5431 bytes, moved (source sha256 `3b83507e…` unchanged).
-
`csrc/cake_megamoe_topk_reduce/sm103a/{cake_megamoe_topk_reduce_kernels.cu,manifest.json}`:
new SM103a export. The exporter produces a translation unit
byte-identical to the SM100a one (the schedule is arch-neutral); the
manifest carries `"arch": "sm_103a"`.
- `flashinfer/jit/cake_megamoe_topk_reduce.py`: one frozen module per
arch. `resolve_arch(device)` maps CC `(10, 0)` to `sm_100a` and `(10,
3)` to `sm_103a`; each module compiles with its own `-gencode`
(`sm100a_nvcc_flags` / `sm103a_nvcc_flags`) and has an arch-specific
URI. Callers of `get_…_module()`, `is_…_loaded()`, `run_…()` are
unchanged (device defaults to the current one).
- `cake_megamoe_topk_reduce_binding.cuh`: `CheckTarget` checks the exact
CC the module was compiled for
(`CAKE_MEGAMOE_TOPK_REDUCE_CC_MAJOR/MINOR` from the generated binding),
so an sm_100a module still refuses a B300 and vice versa.
- SM100 NVFP4 CuTeDSL backend `_uses_native_topk_reduce`: eligible on
`(10, 0)` and `(10, 3)`; the deferred-reduction launch path selects the
module by the partials' device.
- `flashinfer/aot.py`: new `cake_megamoe_topk_reduce_sm103a` capability
(`compute_103a`, CUDA >= 12.9).
- Tests/bench: new host-side
`tests/moe_ep/test_cake_megamoe_topk_reduce_frozen_sources.py` (identity
+ arch selection for both drops);
`test_mega_native_topk_reduce_multirank.py` runs on B300 too; the
benchmark reports the resolved arch.

## 🔍 Related Issues

- #4727 (MegaMoE workspace capacities / terminal reducer), #4819 (SM100a
reducer), #5431 (exporter refresh; the sm_100a-only question)

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

Validation:

- **Cake exporter (both SKUs):** the `sm_100a` and `sm_103a` profiles
regenerate to the same bytes (sha256 `3b83507e…`), `check=True` passes,
and NVRTC compiles the exported TU for `sm_100a` and `sm_103a`
(6776-byte cubins) on B200 (`nsc-svg-slurm-1-gpu-187`, driver 580.82.07)
and B300 (`pool0-0196`, driver 580.126.09). The generating Weave
schedule passes the Cake correctness slice (`-k
megamoe_workspace_topk_reduce_warps8`) on B200 as `sm_100a` and on B300
as `sm_103a`; a direct NVRTC `sm_103a` build of this exact TU launched
on B300 matches the ordered FP32 reference bit-exactly for (tokens,
capacity) in {(1,256), (8,256), (256,256), (1000,4096), (4096,4096)}.
- **FlashInfer on B300** (`aws-pdx` `pool0-0141`, 4x B300 SXM6 AC, CC
10.3, driver 580.126.09, torch 2.13.0a0+nv26.07 / CUDA 13.3,
nvidia-cutlass-dsl 4.8.0, this branch):
- `pytest tests/moe_ep/test_cake_megamoe_topk_reduce_frozen_sources.py`:
14 passed.
- `sm_103a` module JIT build + load: 5.1 s
(`cake_megamoe_topk_reduce_sm103a_…`); `run_cake_megamoe_topk_reduce`
matches the ordered FP32 reference on (tokens, capacity) in {(1,256),
(8,256), (256,256), (1000,4096), (4096,4096)} (max abs err 0, 1.2e-7 at
4096 tokens).
- `torchrun --nproc_per_node=4 -m pytest
tests/moe_ep/test_mega_native_topk_reduce_multirank.py -m "gpu_4 and
arch_blackwell"`: 1 passed on all four ranks (native reducer eligible on
CC 10.3, full MegaMoE data path vs the CuTeDSL reference).
- **B200:** the `sm100a` bytes are unchanged from #5431; the B200 path
is covered by `/bot run tests/moe_ep`.

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

## 📊 Performance

Reducer-kernel latency only (not end-to-end MoE), `python
benchmarks/bench_cake_megamoe_topk_reduce.py --json`: CUPTI activity
timing, cold L2, median of the measured iterations. The baseline is the
vendored CuTeDSL `topk_reduce.py` doing the same matched work (same live
`T`, `4*T` CTAs, `T x 6 x 4096` BF16 in / `T x 4096` BF16 out, 56 KiB
per token). Fixed-capacity comparisons where the baseline processes 4096
rows for a smaller live batch are excluded; unequal work is not kernel
speedup.

**B200 (SM100a, `sm100a/` bytes, unchanged from #5431; measured for
#4819 on `nsc-svg-slurm-1-gpu-187`):**

| live tokens T | capacity C | native (µs) | matched CuTeDSL (µs) |
CuTeDSL / native |
| ---: | ---: | ---: | ---: | ---: |
| 1 | 256 | 1.824 | 2.272 | 1.246x |
| 8 | 256 | 1.985 | 2.496 | 1.258x |
| 64 | 256 | 2.752 | 3.200 | 1.163x |
| 128 | 256 | 3.520 | 3.968 | 1.127x |
| 256 | 256 | 4.800 | 5.184 | 1.080x |
| 4096 | 4096 | 37.312 | 40.223 | 1.078x |
| geometric mean | | 4.295 | 4.967 | **1.156x** |

**B300 (SM103a, `sm103a/` bytes, this PR; `aws-pdx` `pool0-0061`, 1x
B300 SXM6 AC, CC 10.3, driver 580.126.09, torch 2.13.0a0+nv26.07 / CUDA
13.3, nvidia-cutlass-dsl 4.8.0, `sm_103a` JIT module
`cake_megamoe_topk_reduce_sm103a_3449753c9f62f908b1b7`):**

| live tokens T | capacity C | native (µs) | matched CuTeDSL (µs) |
CuTeDSL / native |
| ---: | ---: | ---: | ---: | ---: |
| 1 | 256 | 1.839 | 2.416 | 1.313x |
| 8 | 256 | 2.016 | 2.528 | 1.254x |
| 64 | 256 | 2.656 | 3.072 | 1.157x |
| 128 | 256 | 3.489 | 3.872 | 1.110x |
| 256 | 256 | 4.864 | 5.184 | 1.066x |
| 4096 | 4096 | 36.704 | 40.480 | 1.103x |
| geometric mean | | 4.279 | 4.979 | **1.164x** |

The native reducer is faster than the matched-work CuTeDSL baseline on
every shape on both SKUs (minimum 1.078x on B200, 1.066x on B300). At
T=4096 both GPUs move ~235 MB in ~37 µs (~6.3–6.4 TB/s, about 80% of the
8 TB/s HBM3e peak); the small-T rows are launch/latency bound at ~1.8–2
µs. Raw B300 JSON (sha256 `b52d872e62ce…`) is kept in the run workspace.

## Reviewer Notes

Both `.cu` files are exporter output and byte-identical to each other;
please review the JIT/binding/backend/AOT changes, the manifests, and CI
rather than the `.cu` diff. The per-arch directory layout follows
`csrc/cake_all_gather_matmul/{sm100a,sm103a}`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a21dcfd](https://github.com/flashinfer-ai/flashinfer/commit/a21dcfd96a48aa7592e475841fefbf7f4a28bfa3)

- **作者**: Alex Yang
- **时间**: 2026-09-24T08:32:11Z
- **提交信息**: test(cake_sampling): pin the nvcc sm_107 probe in the build-target test (#5511)

Since #5482, test_build_targets_follow_flashinfer_cuda_arch_list asserted that FLASHINFER_CUDA_ARCH_LIST=\"10.7 11.0\" yields compute_107a, but CompilationContext.get_nvcc_flags_list rewrites 10.7 to sm_100f whenever the local nvcc cannot emit compute_107 (every CUDA 12.x toolkit). The GitHub H100 lane runs the cu129 image, so this node failed on every PR merged with main since then (#5510).

The test is about which targets are named, not about the toolkit on the test host, so pin _nvcc_supports_sm107 to True for its duration.

Fixes #5510.

AI-assisted.

Co-Authored-By: Claude Fable 5.1 <noreply@anthropic.com>

### [7685a89](https://github.com/flashinfer-ai/flashinfer/commit/7685a893e9157f76672f5b9a27dbad9be731f280)

- **作者**: Yang Xu
- **时间**: 2026-09-24T08:01:16Z
- **提交信息**: Reuse cuDNN attention plans and fix metadata lifetime and layout (#5350)

<!-- .github/pull_request_template.md -->

## 📌 Description

Repeated cuDNN decode and prefill calls retain compatible prepared
graphs and static metadata. Decode query-length storage stays owned by
the wrapper across plan/capture/replay; replanning preserves compatible
prepared state. Decode sinks bind current values, including copies of
strided inputs during capture.

This also repairs adjacent cuDNN attention adapter bugs: paged prefill's
default softmax scale, real NHD/HND layouts, packed Stats, and omitted
CSR-derived metadata; complete prefill descriptor keys and device
identity; FP8 default/scalar scale bindings; and device/thread-local
cuDNN handles. Explicitly unsupported masking/scaling features raise
instead of being ignored. A shared resolver keeps public and prepared
prefill metadata consistent. Shape override declines noncontiguous
indptrs. Single-token GQA prefill LSE remains rejected because cuDNN
9.27 leaves heads unwritten (NVBug 6783545).

The public decode API also validates explicitly supplied Q/O offsets.
Legacy dense offsets remain accepted, including packed query strides and
multi-token decode. Non-dense CUDA offsets trigger a device assertion,
including if changed before captured replay. Checks stay on device and
are bypassed when offsets are omitted; prepared wrapper execution and
cubin offset forwarding are unchanged.

Regression tests include capture -> plan -> allocator poison -> replay,
prepared replacement while retaining a capture, changing sinks,
descriptor layouts, default scale, O and LSE references, and real replay
with poisoned outputs. The legacy BF16 prefill matrix now actually uses
its LSE and CUDA-graph parameters. The broad existing FP8 xfail is
retained; new targeted FP8 default/scalar tests execute on B200.

Production NVIDIA B200 (148 SMs, 1000 W), BF16, Hq/Hkv=32/8, D=128, NHD.
cuDNN 9.27, FE source `d3613cf599831ba74195e714b6c4591334d97761`, DSL
4.8. Both arms use the same native extension SHA256
`40541e6532cb1b7d4082cd05df1724eb850b46c9461e7a3f2f4a536ab6f818e8`.
Exact imports and product-file hashes are verified per process.

One plan serves many runs: new Q/K/V values do not require replan while
the plan contract remains compatible. Metadata resolution and static
descriptor/binding preparation happen in `plan()`. Warm `run()` checks
dynamic tensor descriptors and binds current pointers. Same-descriptor
replans retain compatible prepared state and stable CPU-metadata device
mirrors. Each call owns its variant pack.

**Correction to the earlier ragged GPU comparison:** the old 68.57 us
baseline is withdrawn. After capture, the benchmark replanned the
original wrapper, releasing GPU metadata still referenced by native
graph nodes. The initial replay check passed, but later temporary
allocations reused that storage; outputs from the timed loop had 5.8%
incorrect elements (maximum absolute error 3.0). Keeping the captured
integer metadata references alive restores both correctness and ~71.9 us
GPU time. The benchmark now validates outputs after timing as well as
before it. No runtime workaround was added for this investigation; the
current wrapper already owns stable metadata buffers.

Corrected ABBA comparison below: original runtime `e5faae23` versus
current runtime `f12964fb` (unchanged by benchmark/test follow-up
`56e95195`). The diagnostic harness retains captured wrapper metadata in
**both** arms; this lifetime repair belongs to the benchmark baseline,
not the old PR implementation. All four processes pass sampled
independent math and full replay checks before and after timing. Median
of two process medians, microseconds; ragged prefill B16/Q=KV512:

| Measurement | Original runtime with diagnostic capture retention |
Current runtime |
|---|---:|---:|
| Warm host enqueue | 38.52 | 33.76 |
| Run after plan | 47.01 | 44.10 |
| Host plan+run | 88.10 | 100.65 |
| CUDA graph GPU replay | 71.89 | 71.86 |

A separate same-graph/same-buffer experiment interleaves old and new
execution with identical tensor pointers, workspace and override
arguments: 73.84/73.85 us. Absolute timings differ with that
experiment's allocation arrangement; its paired result corroborates GPU
parity for this case.

The host plan+run cost remains real. Profiling identifies the complete
descriptor and compatibility checks in `_CudnnPrefillPlan.prepare`. A
fixed-contract diagnostic bypass reduces current plan+run from 99.36 to
82.06 us while warm enqueue and GPU time stay unchanged. That bypass is
**not shipped**: general replans must validate changed descriptors. This
PR improves repeated warm execution and preserves capture correctness;
it does not claim every-plan-plus-one-run is faster. These are component
measurements, not full-model speedups.

Historical decode measurements at `2293b566` remain separate evidence
(B64/Q1/KV1024/page16, same FE/native): warm host 34.55 -> 36.32 us; run
after plan 67.47 -> 49.61 us; host plan+run 470.48 -> 450.35 us; GPU
replay 42.96 -> 42.93 us. They were not remeasured during the ragged
attribution.

```bash
python benchmarks/bench_cudnn_wrapper_host.py --kind decode --batch 64 --kv 1024 --replan --output decode.json
python benchmarks/bench_cudnn_wrapper_host.py --kind ragged --batch 16 --q 512 --kv 512 --replan --output ragged.json
```

## 🔍 Related Issues

Follow-up to review of #5350 and adjacent cuDNN integration paths. Most
adapter defects predate this PR; the captured decode allocation lifetime
and plan-every-step prepared reuse are PR regressions. The v0.7.0
release does not contain #5350, but does contain the older
paged-layout/default-scale/Stats, descriptor-key, handle, and
FP8-binding defects. This patch targets current main's token-unit
wrapper contract; it is not a standalone v0.7.0 backport.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

**CodeRabbit follow-up (`71c7408d`):** focused
decode/cache-key/prepared/wrapper suites pass **170 tests / 1 skipped on
SM100** and **160 / 11 on H100**. This includes dense Q/O offset
compatibility for packed Q and multi-token decode, capture/replay,
metadata contract rejection, and unchanged cubin forwarding. Invalid GPU
offsets are tested in isolated subprocesses because a device assertion
invalidates that CUDA context. A capture/mutation negative control fails
on the previous `56e95195` runtime, which silently ignores the changed
offset.

The benchmark now restricts replan-after-capture to cuDNN while
continuing to measure eager plan+run for other backends. FA2 and cuDNN
pass both decode and ragged `--replan` smoke runs, cross-backend output
checks and the post-timing replay gate. JSON retains all raw timing
samples, imported package version, checkout commit and source dirty
state. Changed-file pre-commit, including mypy and Ruff, passes.

Prepared wrapper and graph execution source is unchanged. H100 ABBA
decode (B64/Q1/KV1024/page16, same FE/native) measures warm host 40.41
-> 40.44 us and GPU replay 93.62 -> 93.51 us. Ragged GPU replay differs
by less than 0.04%; host measurements are noisy and reverse direction
between repetitions, so those samples establish no ragged host
speedup/regression. Explicit offsets in the low-level API add device
validation work; ordinary prepared wrapper execution does not pay that
cost. This follow-up has no new B200 measurement.

**Benchmark/test follow-up (`56e95195`):** the benchmark refuses timings
if the final timed output fails its full one-ULP replay gate. The old
baseline fails this new guard; current code passes on B200. Ragged
direct and forced-legacy tests now capture O/LSE, replan with new CPU
metadata tensors, poison the allocator with integer buffers, and check
replay against independent math. The regression file passes **43 tests /
1 skipped on production B200**, **43 / 1 on the SM100 development GPU**,
and **37 / 7 on H100**. Changed-file pre-commit passed. Production files
are unchanged from `f12964fb`.

**Cleanup (`f12964fb`):** removes unused matcher/cache/decode forwarding
state and redundant paged KV staging while retaining public signatures
and plan-owned caches. Production growth versus the PR base is +991
lines. Focused contract/prepared/wrapper suites: **76 passed / 1 skipped
on SM100**, **70 / 7 on H100**; another **23 H100 public
decode/cache-key tests** passed. The public fallback probe counted 19
nonprepared plans and 19 fallback launches. Capability absence was
simulated by patching both wrapper and low-level aliases on the current
installation, rather than claiming tests on an older FE release.

FP8 default/scalar/tensor capture coverage, caller-owned metadata
protection, descriptor/layout changes, current pointer rebinding,
NHD/HND, packed O/LSE and workspace replacement remain covered.
Warm-path tests reject metadata resolution, static-key/binding
construction or override-argument rebuilding during warmed execution.

Historical broad scoped tests at `2293b566`: H100 **716 passed / 700
skipped** (installed FE 1.28/cuDNN 9.27); B200 **743 passed / 385
skipped / 288 xfailed** (verified FE 1.30 source/native). The existing
unconditional FP8 matrix remains xfailed; targeted FP8 regressions
execute separately. Two-device/thread handle isolation passed
separately. These broad results are attributed to that revision, not
reruns of the latest head.

Full GPU CI has been authorized for the latest head; results are
pending. The repository requires a fresh `run-ci` label event after each
push. A prior summary failure caused by absent authorization was not a
GPU test failure.

```bash
python -m pytest -q tests/attention/test_cudnn*.py
```

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

Review the captured allocation lifetime, descriptor equality versus
tensor identity, caller-owned GPU metadata protection, and call-local
bindings. Planning/workspace replacement must not race with execution on
the same wrapper. Explicit runtime FP8 scales and legacy backends retain
the public fallback; the warm-path claim applies to the prepared route.
Ragged plan+run retains the explicit per-plan validation cost above. The
earlier apparent GPU regression is traced to an invalid
captured-metadata lifetime in the old benchmark baseline.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added reusable cuDNN execution graphs for decode and prefill, with
reuse across compatible runs and replanning when runtime requirements
change.
* Added per-device execution, runtime sink updates, and variable query
lengths.
* Added a benchmark for measuring cuDNN and FlashInfer overhead and
checking numerical results.

* **Bug Fixes**
* Improved correctness for paged prefill workloads with large page
sizes.
* Added validation for cuDNN tensor devices, shapes, data types,
layouts, output buffers, and dense decode offsets.

* **Tests**
* Expanded coverage for graph reuse, rebinding, replanning, workspace
changes, validation, and numerical correctness.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4580806](https://github.com/flashinfer-ai/flashinfer/commit/4580806be6b194b4f2cdb9cf69c9b73e3094b623)

- **作者**: eigen
- **时间**: 2026-09-24T07:57:57Z
- **提交信息**: feat(cake_nvfp4_mla_decode): add experimental NVFP4 DeepSeek-V4 decode attention on SM100/SM103 (#5443)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add experimental NVFP4 DeepSeek-V4 decode attention (the kernel
requested in #5403) through
`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla(...,
backend="cake")`.

Semantics: paged MQA decode over a shared NVFP4 latent K=V cache, 64
heads, head_dim 512
(= v_head_dim), page size 64, query length derived from the query rows
(six per request for
DeepSeek-V4, the batch-32 / q_len-6 configuration of #5403), causal
within the query block,
optional per-head attention sinks; BF16 output plus natural-log LSE. Q,
K and V are NVFP4 E2M1
(two values per byte) with UE4M3 block-16 scales; BMM1 (QK) runs as an
NVFP4 block-scaled tensor
core MMA with the scales published to tensor memory, P is scaled by 2^8
and cast to FP8 E4M3, V is
requantized to FP8 E4M3 on chip, and BMM2 (PV) runs as an FP8 MMA. Long
sequences are split across
CTAs by a host work plan and combined by a small split-KV combine
kernel; a two-CTA cluster forms one tensor-core MMA over the 128 query
rows of a tile — 64 rows x 512 output dims per CTA — and shares a
multicast page stream. Split partials are BF16 and split-major; rows of
unsplit requests are written by the decode kernel directly and skipped
by the combine kernel.

Preparation validates inputs, builds the host work plan from the
sequence lengths (one D2H copy
unless `seq_lens_cpu` is given), carves partials, work table and index
tensors out of the
caller's `workspace_buffer`, and returns an `NVFP4MLADecodeRunner`.
Calling the runner launches the
decode kernel and, when the plan is split, the combine kernel, without
CUDA allocation. Prepare a
new runner when shapes, lengths or bindings change. Supported targets
are compute capability 10.0
(B200) and 10.3 (GB300/B300); SM120/SM121 are rejected because the
kernel needs tcgen05/TMEM.
Preparation, JIT registration, tests, a benchmark and the generated CUDA
are contained under
`flashinfer/experimental/nvfp4_mla_decode/`, `tests/experimental/` and
`benchmarks/`.

Correctness is checked against an FP32 reference that dequantizes the
NVFP4 inputs exactly
(atol/rtol 0.1 on the BF16 output, per-(row, head) relative L2 <= 0.05,
LSE atol 0.05); the
residual error (relative L2 0.01-0.04) is the on-chip V requantization
to E4M3. Known limits are
listed in the package README (D=512 only, MQA with shared K=V, page 64,
at least 128 packed query
rows per batch, SM100/SM103).

## 🔍 Related Issues

Requested in #5403 (DeepSeek-V4 FMHA decode, BS=32, Q_len=6, NVFP4
Q/K/V, NVFP4 BMM1, FP8 BMM2).
Tracking issue for the experimental path: #5403 (owner: @yyihuang;
graduation plan: promote once the
requester confirms the cache geometry and the backend has been exercised
from a serving stack).

## ⚡ Speedup vs FlashInfer FP8 CuTe-DSL MLA decode

Strongest existing FlashInfer kernel at this request geometry:
`trtllm_batch_decode_with_kv_cache_mla(query=[32, 6, 64, 576] fp8,
kv_cache=[pages, 1, 64, 576] fp8, ..., bmm1_scale=1/sqrt(576),
bmm2_scale=1.0, backend="cute-dsl")`
(FP8 E4M3 Q/K/V at D=576 = 512 latent + 64 rope, BF16 output). It reads
FP8 bytes, this kernel reads
NVFP4 bytes, so the comparison is end-to-end decode latency for the same
batch / query rows / heads /
KV length, not the same bytes.

Method: both kernels measured in the same job step on the same GPU,
alternating (FlashInfer first,
two rounds), kernel-only CUPTI GPU span (decode + split-KV combine for
this kernel; all kernels of one
FlashInfer call), cold L2 before every sample, `bench_gpu_time` medians.
BS=32, q_len=6, 64 heads, page 64,
one KV length per row.

| KV length | GB300 this kernel ms | GB300 FI FP8 CuTe-DSL ms | GB300
speedup | B200 this kernel ms | B200 FI FP8 CuTe-DSL ms | B200 speedup |
|---|---:|---:|---:|---:|---:|---:|
| 8K   | 0.0947 | 0.1000 | **1.057x** | 0.1120 | 0.1177 | **1.051x** |
| 16K  | 0.1643 | 0.1900 | **1.157x** | 0.1960 | 0.2119 | **1.081x** |
| 32K  | 0.3008 | 0.3647 | **1.213x** | 0.3915 | 0.4095 | **1.046x** |
| 64K  | 0.5789 | 0.7171 | **1.239x** | 0.7971 | 0.8246 | **1.035x** |
| 128K | 1.1641 | 1.4437 | **1.240x** | 1.6053 | 1.7817 | **1.110x** |

GB300 (SM103) and B200 (SM100): faster on every row on the measured
nodes (B200 node-to-node spread is about
+-1.5 % per side at identical reported clocks, so the B200 32K/64K
margins of 3-5 % are the least robust rows).
Relative to the previous revision of this PR the kernel is 1.5-6 %
faster on GB300 and 1.5-3 % faster on B200:
the FP4 -> FP8 V requantization rounds are software-pipelined three
deep, and the Q operand of the block-scaled
QK MMAs is published once per work item into tensor memory instead of
being re-read from shared memory on
every tile. The export receipts below are a different measurement
(source launcher vs exported entry,
drift/clock gated) and are not the baseline comparison.

## Generated-program export evidence

Source = the Cake production launcher (prepared launch, decode + combine
kernels), export = the exact exported TVM-FFI entries loaded through the
FlashInfer JIT route, same tensors and workspace, same host work plan
(recorded per arm in every receipt). Correctness of both arms is checked
against the FP32 reference before and after timing; source and export
outputs are bitwise identical on every row.

### Hardware and protocol

- `sm_103a`: NVIDIA GB300, driver 580.167.08, PyTorch
2.13.0a0+9186a08b2c.nv26.07, CUDA 13.3.
- `sm_100a`: NVIDIA B200, driver 580.82.07, PyTorch
2.13.0a0+9186a08b2c.nv26.07, CUDA 13.3.
- CUPTI GPU-span timing (first compute-kernel start to last
compute-kernel end of one call), cold L2 before every sample,
`symmetric_external_cuda_graph` for both arms, 3 counterbalanced groups,
800 warmup and 2400 reportable calls per arm and group (fixed counts;
the warmup runs after CUPTI is enabled so the first reportable sample
follows the last warmup launch without an idle gap); gates:
source/export >= 0.97, directional disagreement <= 0.02, endpoint drift
<= 0.02, SM clock >= 0.8 of the observed maximum in every
warmup/measurement phase.
- Target revision `a64cf168528b517dde144f6791b48554348ba030`; the
generated sources carry the module hashes recorded in `cake_jit.py`.

### Per-shape results

| Shape | Arch | Source ms | Export ms | Source / Export | Export
TFLOP/s | rel-L2 vs FP32 | SM clock MHz (phase min-max) | Verdict |
|---|---|---:|---:|---:|---:|---:|---|---|
| smoke | sm_100a | 0.0141 | 0.0140 | 1.0046 | — | 0.0457 | 1965-1965 |
pass |
| partial_pages_h8 | sm_100a | 0.0238 | 0.0228 | 1.0435 | — | 0.0346 |
1965-1965 | pass |
| no_sink_q1 | sm_100a | 0.0410 | 0.0408 | 1.0055 | — | 0.0386 |
1965-1965 | pass |
| bs32_q6_kv8k | sm_100a | 0.1128 | 0.1128 | 1.0003 | 1828 | 0.0232 |
1965-1965 | pass |
| bs32_q6_kv16k | sm_100a | 0.1991 | 0.1993 | 0.9990 | 2069 | 0.0211 |
1965-1965 | pass |
| bs32_q6_kv32k | sm_100a | 0.3972 | 0.3968 | 1.0010 | 2078 | 0.0158 |
1965-1965 | pass |
| bs32_q6_kv64k | sm_100a | 0.8169 | 0.8165 | 1.0005 | 2020 | 0.0157 |
1965-1965 | pass |
| bs32_q6_kv128k | sm_100a | 1.6421 | 1.6419 | 1.0001 | 2009 | 0.0101 |
1965-1965 | pass |
| smoke | sm_103a | 0.0129 | 0.0131 | 0.9877 | — | 0.0457 | 2070-2070 |
pass |
| partial_pages_h8 | sm_103a | 0.0222 | 0.0216 | 1.0297 | — | 0.0306 |
2070-2070 | pass |
| no_sink_q1 | sm_103a | 0.0364 | 0.0366 | 0.9965 | — | 0.0341 |
2070-2070 | pass |
| bs32_q6_kv8k | sm_103a | 0.0947 | 0.0949 | 0.9973 | 2171 | 0.0230 |
2070-2070 | pass |
| bs32_q6_kv16k | sm_103a | 0.1638 | 0.1640 | 0.9990 | 2515 | 0.0211 |
2070-2070 | pass |
| bs32_q6_kv32k | sm_103a | 0.3005 | 0.3008 | 0.9991 | 2741 | 0.0182 |
2070-2070 | pass |
| bs32_q6_kv64k | sm_103a | 0.5785 | 0.5788 | 0.9994 | 2849 | 0.0147 |
2070-2070 | pass |
| bs32_q6_kv128k | sm_103a | 1.1597 | 1.1594 | 1.0003 | 2845 | 0.0121 |
2070-2070 | pass |

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

`tests/experimental/test_cake_nvfp4_mla_decode.py`: host-side tests
(work plan geometry, workspace
sizing, input validation, backend/CC rejection) and GPU tests on B200
(SM100) and GB300 (SM103)
against the FP32 reference, including forced split plans, q_len 1 and
partial pages.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #5403
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
tests/experimental/test_cake_nvfp4_mla_decode.py
```

## Reviewer Notes

Both the API and the backend are experimental. Review the prepare/run
ownership contract (workspace
carving, zero-allocation runner), the SM100/SM103 routing, the JIT
source packaging (one extension
per stage; the combine kernel is built without fast-math), and the host
work plan (balanced
partition over SM count, two-CTA cluster pairs). Absolute latencies in
the evidence section are
kernel-only CUPTI spans (decode + combine), cold L2, symmetric external
CUDA graphs for both arms;
the informational FlashInfer MLA baselines in the README benchmark
script use FP8/BF16 KV at D=576
and are not the same bytes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an experimental NVFP4 MLA decode API for supported SM100 and
SM103 GPUs, with optional attention sinks and log-sum-exp output.
* Added a benchmark for measuring decode performance across configurable
KV-cache lengths, with an optional comparison to another backend.
* Added documentation covering API usage, supported configurations, and
workspace requirements.

* **Bug Fixes**
* Improved handling of split requests and output combination across
decode workloads.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b790758](https://github.com/flashinfer-ai/flashinfer/commit/b79075815639e60f544e49b96032542b8656b08f)

- **作者**: Zihao Ye
- **时间**: 2026-09-24T07:40:56Z
- **提交信息**: refactor(tvm_ffi_utils): add named tensor-argument check helpers (#5408)

## Summary

Add five named tensor-argument check helpers to `csrc/tvm_ffi_utils.h`:

- `check_cuda_tensor(t, name)`
- `check_dtype(t, DLDataType expected, name)`
- `check_contiguous(t, name)`
- `check_same_device(t, reference, name, reference_name)`
- `check_dense_leading_dims(t, trailing, name)`

The existing `CHECK_*` macros stringify the C++ variable and raise an
internal
error. These functions take the user-facing argument name and raise
`ValueError` or `TypeError` with a message that identifies the argument
and the
mismatch (device type, DLPack dtype triple, or the exact stride that
breaks a
dense fold), so a Python caller can act on the message without reading
the
binding.

Several generated binding families currently carry byte-identical
private
copies of these checks in every translation unit. With the helpers in
the
shared header those bindings can call them directly; a follow-up
regenerates
them without the inline copies.

## Test plan

- Compiled a translation unit that includes `csrc/tvm_ffi_utils.h` and
calls
  every new helper together with `ffi::CUDADeviceGuard` and `get_stream`
  (nvcc 13.3, tvm-ffi headers).
- Header-only additive change; no existing symbol or macro is modified.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added validation for CUDA placement, data types, contiguity, matching
devices, and dense leading dimensions.
* Improved validation errors by identifying the affected tensor
arguments and reporting clear error details.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4501
- **最后更新**: 2026-09-25T00:20:42Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34599
- **最后更新**: 2026-09-25T00:28:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Steven Liu

## AI分析总结

### 提交记录分析：`[docs] Adapters (#14842)`

1.  **主要更新类型**
    本次提交为**文档更新**。它并非新增代码功能或修复缺陷，而是专注于完善和系统化项目中“适配器（Adapters）”相关部分的文档说明。

2.  **关键变更点及其与项目整体方向的关系**
    *   **核心变更**：提交信息列举了对多个关键适配器文档的更新，包括：**LoRA**（参数高效微调）、**Legacy Adapters**（旧版适配器）、**IP-Adapter**（图像提示适配器）以及 **ControlNet**（条件控制）。
    *   **与项目方向的关系**：`diffusers`项目旨在提供最前沿、易用的扩散模型工具库。适配器是其核心生态的重要组成部分，允许用户在不修改原始模型的情况下，高效地添加新能力或进行微调。本次文档更新，正是为了**巩固和阐释这一核心架构**，确保开发者能够清晰地理解、选择和使用这些强大的模块化工具，这直接支持了项目的**易用性和可扩展性**目标。

3.  **对项目的影响和潜在意义**
    *   **影响**：提升了文档的完整性和用户体验，降低了新用户的学习门槛，使开发者能更快地找到并正确使用所需的适配器技术。
    *   **潜在意义**：系统化的适配器文档是项目走向成熟和专业化的标志。它有助于吸引更广泛的开发者社区，促进基于`diffusers`的生态创新（如社区开发新的、文档完善的适配器），从而**增强项目的竞争力和影响力**。

4.  **值得关注的技术点**
    文档需要清晰地阐述不同适配器的技术原理、应用场景和接口差异。例如，如何说明**LoRA的低秩矩阵分解原理**与**ControlNet的条件注入机制**的本质区别，以及它们各自在**微调效率**与**生成控制**上的优势。文档的深度和清晰度直接反映了项目团队对底层技术的理解和对用户友好的重视。

5.  **对项目发展的影响**
    基于README描述的扩散模型工具库定位，此次文档更新是项目**从功能实现向生态完善迈进的关键一步**。它不仅服务于现有用户，更是为未来的模型集成和社区贡献打下了坚实基础。完善的文档是开源项目成功的基石，这次提交有助于`diffusers`巩固其作为**行业标准工具**的地位，推动扩散模型技术更广泛、更规范地应用于研究与生产。

## 详细提交记录

### [4295ee3](https://github.com/huggingface/diffusers/commit/4295ee3ec58efa6577bc459e9b84ca3f63aa9a96)

- **作者**: Steven Liu
- **时间**: 2026-09-24T16:11:42Z
- **提交信息**: [docs] Adapters (#14842)

* lora

* legacy adapters

* ip adapter

* controlnet

* feedback

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
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


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13179
- **最后更新**: 2026-09-24T17:37:10Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36408
- **最后更新**: 2026-09-25T00:23:33Z

## 提交统计

- **昨日提交总数**: 52
- **提交者数量**: 34
- **主要提交者**: Qiaolin Yu, Yihao Wang, Liangsheng Yin

## AI分析总结

根据提交记录分析，SGLang项目在昨日进行了集中更新，主要方向如下：

**1. 主要更新类型**
*   **功能新增**：引入了Setwise评分API、支持统一内存解码池、添加了8节点AllReduce/AllGather等通信算法、增加了对多种新模型（如Qwen3.8 Flash, DSV4.1）的支持。
*   **性能优化与架构重构**：优化了PD（Prefill-Decode）队列、改进了DP（数据并行）注意力机制、重构了FFN全规约逻辑、优化了MoE专家的排序与量化路径。
*   **Bug修复**：修复了多个与分布式推理、DP协调、内存预算和采样相关的关键错误，提升了系统稳定性。
*   **硬件适配与优化**：针对AMD ROCm（MI355X, gfx950）和华为NPU（CANN 9.1.0）进行了大量内核优化、调优和CI构建更新。
*   **文档与工程**：更新了文档以启用新硬件支持，并改进了CI流程。

**2. 关键变更点及其与项目整体方向的关系**
*   **分布式与并行推理深化**：大量修复和重构集中在DP注意力、PD队列和全规约流程上，旨在**优化和稳定大规模分布式推理**，这是项目追求高吞吐、可扩展AI服务的核心。
*   **异构计算生态拓展**：对AMD和NPU的持续投入，表明项目在**积极构建广泛的硬件兼容性**，降低用户部署门槛。
*   **缓存与内存管理演进**：HiCache和PD内存池的改进（如延迟释放、统一内存池、智能降级）直接服务于**降低推理延迟和内存开销**，提升长上下文处理能力。

**3. 对项目的影响和潜在意义**
*   **提升生产就绪度**：大量针对性Bug修复和稳定性增强，使框架更适用于生产环境。
*   **扩大应用范围**：对新模型和硬件的支持，增强了框架的通用性和市场竞争力。
*   **奠定未来架构基础**：对通信层、缓存系统和并行机制的重构，为支持更复杂模型和更大规模部署打下基础。

**4. 值得关注的技术点**
*   **PD队列的 `none` 回退机制与子类接口**，增强了Prefill-Decode调度策略的灵活性。
*   **DP注意力中缓冲区的发布机制**，是优化分布式注意力通信的关键。
*   **在“HiCache”中将SWA KV写回主机而非丢弃**，是平衡内存与计算的精巧策略。
*   **针对特定模型（如DSV4）的FP8内核和内存预算修复**，体现了对模型级性能调优的深度。

**5. 基于项目背景，对发展的影响**
这些提交共同推动SGLang朝着一个**高性能、可扩展且硬件友好的AI推理引擎**发展。密集的分布式系统优化巩固了其在高并发服务场景的优势；持续的硬件适配降低了异构部署的成本；而针对前沿模型（如DSV4, Qwen3.8）的快速支持，则确保了其在技术前沿的竞争力。项目正从“功能实现”向“生产级优化与生态构建”阶段深化。

## 详细提交记录

### [2f2f9d1](https://github.com/sgl-project/sglang/commit/2f2f9d12f8485629e162c8fba0e44057fa5d8f97)

- **作者**: Sundara Raman Ramachandran
- **时间**: 2026-09-24T23:50:58Z
- **提交信息**: [Score API] Setwise Scoring Support (#38965)

### [7c5bdb9](https://github.com/sgl-project/sglang/commit/7c5bdb940cc24015aea6647c68e37e322e1d81d8)

- **作者**: metamergebot
- **时间**: 2026-09-24T23:13:54Z
- **提交信息**: [PD] Add a `none` decode retraction backup and subclass seams in the PD queues (#41103)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: Zhiqiang Xie <zqx@meta.com>

### [466e985](https://github.com/sgl-project/sglang/commit/466e985f4b4cab733558967bfd63caf2cb4c162e)

- **作者**: metamergebot
- **时间**: 2026-09-24T23:13:02Z
- **提交信息**: [HiCache] Batch buffer-only KV backups within each flush (#40960)

Co-authored-by: oss-sync bot (pranjalssh) <pranjalssh@users.noreply.github.com>
Co-authored-by: Jialin Ouyang <Jialin.Ouyang@gmail.com>

### [e047e50](https://github.com/sgl-project/sglang/commit/e047e50d4e304beec011730cc30e957b0c9274b0)

- **作者**: Caio Rocha
- **时间**: 2026-09-24T22:51:29Z
- **提交信息**: Add 8-node AllReduce/AllGather and MNVLS algorithm support to MSCCL++ (#37442)

Co-authored-by: Caio Rocha <caiorocha@microsft.com>

### [3ec8630](https://github.com/sgl-project/sglang/commit/3ec86307f20026a6c711daf267755916b9e9c016)

- **作者**: Yuwei An
- **时间**: 2026-09-24T22:41:49Z
- **提交信息**: Fix mixed chunk prefill with DP speculative coordination (#41179)

### [6bbd689](https://github.com/sgl-project/sglang/commit/6bbd689ab41606c1bc6894bd409d4466cf591916)

- **作者**: Apexsf
- **时间**: 2026-09-24T22:21:06Z
- **提交信息**: [Bugfix] Align DeepSeek-V4.1 reasoning effort budgets (#39929)

Co-authored-by: fengtinglei <fengtinglei@bytedance.com>
Co-authored-by: Liangsheng Yin <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [0c578d9](https://github.com/sgl-project/sglang/commit/0c578d97fe7ee19bdbbfa83fc69d767035a35c44)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-24T22:19:02Z
- **提交信息**: [DSV4] Size compressed pools from one per-ratio table in DSV4PoolConfigurator (#41049)

### [a1eb691](https://github.com/sgl-project/sglang/commit/a1eb691ab51bc461378b2fcca8991883add4f1b5)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-24T21:19:00Z
- **提交信息**: [Docs] Enable Qwen3.8 Flash Next NVIDIA NVFP4 on B200/B300/GB300 (#41046)

### [182f62d](https://github.com/sgl-project/sglang/commit/182f62d2deb2fa2ff335f1ea74cf5020c0d65f11)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-24T20:52:11Z
- **提交信息**: [Fix] Patch set_dp_buffer_len_from_batch in DP spec prefill coordination test (#41162)

### [961404b](https://github.com/sgl-project/sglang/commit/961404b0106f71d2ef944563bd33e9d599f25c45)

- **作者**: Shuwen Wang
- **时间**: 2026-09-24T20:25:00Z
- **提交信息**: [DSV4] Fix TRTLLM uniform FP8 KV memory budgeting (#41090)

### [36f5998](https://github.com/sgl-project/sglang/commit/36f59982faaaee22fc87ed6fdd072083c216c06a)

- **作者**: Chunan Zeng
- **时间**: 2026-09-24T20:18:18Z
- **提交信息**: MoE: small-batch sorting path with fused mxfp8 quantisation (#36559)

Co-authored-by: mikevin920 <mikevin920@yahoo.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Kevin Mi <mikevin920@gmail.com>
Co-authored-by: Kevin Mi <kevin.mi@radixark.ai>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [0b53305](https://github.com/sgl-project/sglang/commit/0b53305f480d87fbfc29baf4627339766a91a81d)

- **作者**: Chunan Zeng
- **时间**: 2026-09-24T20:16:59Z
- **提交信息**: MiniMax-M3: MXFP8 dense-only block convert + aiter MXFP8 MoE on gfx950 (#36574)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: mikevin920 <mikevin920@yahoo.com>
Co-authored-by: Kevin Mi <mikevin920@gmail.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: YC Yen-Ching Tseng <yctseng@amd.com>

### [b129504](https://github.com/sgl-project/sglang/commit/b129504f0efd0cac1cacaa179bb62c2e5bca8f95)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-24T20:13:34Z
- **提交信息**: [qwen 3.8 next] Fuse Qwen PLE gate and convolution preparation for target verify (#40041)

### [1446e24](https://github.com/sgl-project/sglang/commit/1446e24d13cc28fbea22beb19f68ade24523960d)

- **作者**: Thomas Wang
- **时间**: 2026-09-24T19:21:34Z
- **提交信息**: [AMD] Add .co for deepseek v4 fp8 decode kernel and add group decode opt (#41120)

### [5bb850d](https://github.com/sgl-project/sglang/commit/5bb850d536610595ddb6e90ce71342ef68ec7426)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:16:54Z
- **提交信息**: [Refactor] Split prepare_attn into a reduction step and per-quant-format residual steps (#41084)

### [a80055d](https://github.com/sgl-project/sglang/commit/a80055d3c6afd4ec9b96bce52d6689e333e48d0b)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:16:27Z
- **提交信息**: [Fix] Broadcast requests along attention CP before attention TP (#41083)

### [7c9f74c](https://github.com/sgl-project/sglang/commit/7c9f74c6e1097903a2259152e26ed90053fbd7fd)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:15:58Z
- **提交信息**: [Fix] Step-3.5: stop dense layers from summing their output twice under DP attention (#41082)

### [62ae032](https://github.com/sgl-project/sglang/commit/62ae032c4601e6f890a00bacad4cdafddc03ac24)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:15:33Z
- **提交信息**: [Refactor] Share the MoE output all-reduce between models (#41097)

### [5df1667](https://github.com/sgl-project/sglang/commit/5df1667077ab88adb6fd0cfd4ec1c88b6fc6e69b)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:15:07Z
- **提交信息**: [Refactor] Pass each layer stack's output through a communicator exit (#41081)

### [07a3735](https://github.com/sgl-project/sglang/commit/07a3735e9494d425c8f6b7525bd484a9c2f43eb6)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:14:39Z
- **提交信息**: [Fix] Complete the deferred FFN all-reduce before deepstack addition and aux hidden-state capture (#41080)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [928e683](https://github.com/sgl-project/sglang/commit/928e683f948a531528d3fb5cf511bda164b391f0)

- **作者**: Cheng Wan
- **时间**: 2026-09-24T19:13:57Z
- **提交信息**: [Fix] Complete the deferred FFN all-reduce before a pipeline-parallel send (#41079)

### [6a14b80](https://github.com/sgl-project/sglang/commit/6a14b801417adeb844ff690e8ebe314c126eeb97)

- **作者**: ChangLiu0709
- **时间**: 2026-09-24T19:02:01Z
- **提交信息**: [AMD] GLM-5.2 MI355X MXFP4: bump image to 20260923 daily (#41109)

### [1b03d31](https://github.com/sgl-project/sglang/commit/1b03d31b31a4ce7da037e6b90c6137ce42e70444)

- **作者**: Khoa Pham
- **时间**: 2026-09-24T19:00:09Z
- **提交信息**: [Test] Run the Qwen3.5 Triton DCP nightly with the radix cache enabled (#41155)

### [f404db9](https://github.com/sgl-project/sglang/commit/f404db94d425b1a10dd4954e9f9a70d6ecb65402)

- **作者**: Hanming Lu
- **时间**: 2026-09-24T18:34:19Z
- **提交信息**: [DP attention] Publish DP buffer sizes from a ForwardBatch (#40858)

Co-authored-by: hanminglu <hanminglu@fb.com>
Co-authored-by: oss-sync bot (pranjalssh) <pranjalssh@users.noreply.github.com>

### [86b3558](https://github.com/sgl-project/sglang/commit/86b3558b41bd87b3b6616b98bd506a3fb0306af7)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-24T18:19:28Z
- **提交信息**: [Fix] Skip the DCP target-verify MLA kernel during FlashInfer autotune (#41138)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [78b382b](https://github.com/sgl-project/sglang/commit/78b382b1ad36c729dd47db660d1cfa21c68801d9)

- **作者**: Yonghao Zhuang
- **时间**: 2026-09-24T18:02:15Z
- **提交信息**: Support unified memory decode host pools (#39478)

Co-authored-by: yhzhuang <yhzhuang@fb.com>
Co-authored-by: Lianmin Zheng <lianminzheng@gmail.com>
Co-authored-by: Yonghao Zhuang <yhzhuang@users.noreply.github.com>
Co-authored-by: Cheng Wan <cheng.wan@radixark.ai>

### [984994e](https://github.com/sgl-project/sglang/commit/984994e3aa15bd11baddbcaddb43983bace94e36)

- **作者**: Trevor Morris
- **时间**: 2026-09-24T17:25:35Z
- **提交信息**: fix: Triton 3.8 compatbility to support DSV4.1-Flash in CUDA 13.4 image (Rubin) (#40805)

### [5bb24e3](https://github.com/sgl-project/sglang/commit/5bb24e399d471dbb4f3d461972f7614a12a1484e)

- **作者**: Jackey Hua
- **时间**: 2026-09-24T16:30:01Z
- **提交信息**: [Quant] ModelOpt mixed precision: dispatch block-FP8 MoE experts and derive the block size (#38726)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8ec65e8](https://github.com/sgl-project/sglang/commit/8ec65e89c19d90c40499832b296531792191115f)

- **作者**: Xinyu Jiang
- **时间**: 2026-09-24T16:09:19Z
- **提交信息**: [AMD] ci: move the Miles ROCm 7.2 nightly build to 7.2.4 (#40387)

Co-authored-by: Zhiyao Jiang <jessicajiang324@gmail.com>

### [77173ff](https://github.com/sgl-project/sglang/commit/77173ffb08e94e474a719c1efd01fa534131c6a8)

- **作者**: Shangming Cai
- **时间**: 2026-09-24T15:56:17Z
- **提交信息**: [HiCache] Demote SWA KV to host on write_back eviction instead of dropping it (#40712)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [752801e](https://github.com/sgl-project/sglang/commit/752801e4d184574f9c4f860b7c0dcab9f4ed6d93)

- **作者**: Ting SUN
- **时间**: 2026-09-24T15:25:13Z
- **提交信息**: fix(sampling): validate sampling_seed is an int within int64 range (#28960)

Signed-off-by: Ting Sun <suntcrick@gmail.com>

### [17a7484](https://github.com/sgl-project/sglang/commit/17a7484c069c0499d77f304cbca93f8980048ed3)

- **作者**: Mick
- **时间**: 2026-09-24T14:56:41Z
- **提交信息**: [chore] surface the cookbook to users who pip install sglang (#40866)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [cd11037](https://github.com/sgl-project/sglang/commit/cd1103700941a11901f12536a9a29bf1bd4417cd)

- **作者**: Shangming Cai
- **时间**: 2026-09-24T14:35:11Z
- **提交信息**: [PD] Enable deferred decode-side KV release by default (#41023)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [4142235](https://github.com/sgl-project/sglang/commit/4142235c2bfa3b7ffd9945ae1b6a17bb92a9fe4f)

- **作者**: 黄孝君
- **时间**: 2026-09-24T13:35:31Z
- **提交信息**: [NPU] Update CANN version to 9.1.0 (#40524)

### [ec7eb6b](https://github.com/sgl-project/sglang/commit/ec7eb6bd795f6599f09de0fbee23f091a5c2e532)

- **作者**: WenhaoZhang
- **时间**: 2026-09-24T13:31:50Z
- **提交信息**: [diffusion] update code owner (#41130)

### [ea5baf4](https://github.com/sgl-project/sglang/commit/ea5baf4022e42ef13b089430ce2b1927a5c9d6f0)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-24T13:25:00Z
- **提交信息**: [Refactor] Retire the model-specific Kimi K3 kernel namespace (#40922)

### [28ec670](https://github.com/sgl-project/sglang/commit/28ec6700dade98786e948603fa80b472852a4b74)

- **作者**: paulzhang-tm
- **时间**: 2026-09-24T13:03:25Z
- **提交信息**: [HiCache] Make host reclamation independent of transfer order (#40512)

### [3177d10](https://github.com/sgl-project/sglang/commit/3177d10ca6f7fbdd9d0e5d2f2db3f86b546beaef)

- **作者**: Brayden Zhong
- **时间**: 2026-09-24T13:00:58Z
- **提交信息**: Refactor the Cute-DSL AR fusion to support DeepseekV2 archs (GLM-5.3, etc.) (#39816)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>
Co-authored-by: Mohammad Miadh Angkad <176301910+mmangkad@users.noreply.github.com>

### [ce06a14](https://github.com/sgl-project/sglang/commit/ce06a1444439d0615786a98ea35d99468e57784f)

- **作者**: ronnie_zheng
- **时间**: 2026-09-24T11:29:49Z
- **提交信息**: [Diffusion] migrate the whole _register_configs from registry.py to the model own config file (#40612)

### [c6565c1](https://github.com/sgl-project/sglang/commit/c6565c1a6d505f1bc755ef1d157fd5549c2fbfe0)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-24T11:21:32Z
- **提交信息**: [Diffusion] Enable lossless SANA-Video eager conv fusions for 12.6% lower latency (#40388)

### [a69583f](https://github.com/sgl-project/sglang/commit/a69583f70f8f94c16e30f42ee535a897f8ccb8c4)

- **作者**: Alan Kao
- **时间**: 2026-09-24T11:06:40Z
- **提交信息**: [AMD] Add tuned dsv4 shape (#40996)

### [0a59830](https://github.com/sgl-project/sglang/commit/0a59830114970ec5f3a671500c44083efd73993d)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-09-24T10:41:23Z
- **提交信息**: [AMD][DSV4] fp8 unified_kv decode: wave-aware split count past 40 tokens (#40878)

Signed-off-by: Yanfei Wang <yanfwang@crsuse2-m2m-v2-017.us-east2-a.compute.internal>

### [26c6333](https://github.com/sgl-project/sglang/commit/26c63335e2296100e47e6dca042320951ef69a06)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-24T10:41:10Z
- **提交信息**: [Diffusion] Fuse lossless LingBot World FP32 normalization (#40425)

### [d94d784](https://github.com/sgl-project/sglang/commit/d94d784441835f4ee285848ee4c7f9f3f8c041f8)

- **作者**: Zhang, Jiejing
- **时间**: 2026-09-24T10:21:53Z
- **提交信息**: [AMD] Tune Triton sparse MLA on gfx950 and make split-K workspaces graph-safe (#39059)

### [bb1c98b](https://github.com/sgl-project/sglang/commit/bb1c98baa240c62b4b3968e1864cffabfd13d90c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-24T09:44:55Z
- **提交信息**: Fix TBO child batch missing dp_spec_prefill_coordination_applied (#41096)

### [c85df5b](https://github.com/sgl-project/sglang/commit/c85df5becc0a27c140d8a443dd1f15e8c8a698d2)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-24T09:40:07Z
- **提交信息**: [Diffusion] Fuse lossless Wan VAE post-ops for LongLive 2 I2V (#40405)

### [261cb82](https://github.com/sgl-project/sglang/commit/261cb826e6c63b79ae984af6a8d40c10bcfd8571)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-09-24T09:27:56Z
- **提交信息**: [Diffusion] Fuse LongCat GELU+cat and support Edit-Turbo BCG (#40384)

### [174a5f3](https://github.com/sgl-project/sglang/commit/174a5f37b99d9027f355c954b6d52f4feff87c29)

- **作者**: Mick
- **时间**: 2026-09-24T09:00:13Z
- **提交信息**: [feature] add per-item candidate token scoring and calibration (#40826)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [41812af](https://github.com/sgl-project/sglang/commit/41812afe432a54308be1c361a4d587952356f958)

- **作者**: Cheng Xin
- **时间**: 2026-09-24T08:53:44Z
- **提交信息**: [NPU] Fix DSV4 hard-coding kv dtype (#40510)

### [81f2b43](https://github.com/sgl-project/sglang/commit/81f2b43ab512cbc1e2ca0aef97b93e224d400a69)

- **作者**: Yihao Wang
- **时间**: 2026-09-24T08:04:29Z
- **提交信息**: [ci] pr-gate: add generic require-label input and support pull_request_target (#40999)

### [d65503f](https://github.com/sgl-project/sglang/commit/d65503fece2cfe54c915c6e1fa354e4b760ae403)

- **作者**: pllimax
- **时间**: 2026-09-24T07:58:48Z
- **提交信息**: [NPU] Remove the LLaDA2.0-mini basic-function test case (#40905)

### [1417345](https://github.com/sgl-project/sglang/commit/1417345f5f66263ad1ddecb86cb6d15aa1600366)

- **作者**: Yuwei An
- **时间**: 2026-09-24T07:01:12Z
- **提交信息**: [Experimental] Preserve speculative decoding during prefill across DP ranks (#40118)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1286
- **最后更新**: 2026-09-24T16:23:53Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

1.  **主要更新类型**：本次提交属于**文档更新**。它专注于优化项目的README文件，改进了安装说明部分。

2.  **关键变更点及与项目方向的关系**：
    *   **变更核心**：移除了冗余的HTML标签，采用更简洁清晰的Markdown代码块来展示安装命令。
    *   **与项目方向关系**：此变更直接服务于项目的**可访问性与易用性**目标。一个清晰的安装指南能降低用户上手门槛，让更多开发者和用户能够快速开始使用cache-dit这一推理引擎，是项目推广和社区建设的基础性工作。

3.  **对项目的影响和潜在意义**：
    *   **直接影响**：提升了项目文档的质量和专业性，使新用户获取信息的体验更佳。
    *   **潜在意义**：良好的文档是开源项目成功的关键因素之一。此次优化有助于加速项目的社区采纳过程，吸引更多潜在用户和贡献者，为项目后续的功能迭代和生态发展奠定更好的基础。

4.  **值得关注的技术点**：
    *   本次提交虽未涉及引擎代码，但体现了**开发者体验优先**的理念。对于一个工具型项目，简洁的安装指令（如使用`pip install`）是降低使用复杂度的最有效方式之一。

5.  **对项目发展的影响**：
    基于README所述，cache-dit旨在提供强大的推理优化能力。此次文档更新是项目走向成熟和用户友好化的积极信号。它通过优化“第一步”（安装），强化了项目的可用性，这对于吸引更多用户试用并反馈、从而驱动项目在性能优化、功能完善等核心方向上的持续发展至关重要。这是一个必要的、服务于长期技术影响力的非功能性改进。

## 详细提交记录

### [f6b26c7](https://github.com/vipshop/cache-dit/commit/f6b26c77bee4339e0c3859f38db62438f8e6d302)

- **作者**: DefTruth
- **时间**: 2026-09-24T16:23:47Z
- **提交信息**: Update README with installation instructions

Removed unnecessary HTML tags and added a code block for installing the Cache-DiT model integration.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92641
- **最后更新**: 2026-09-25T00:17:17Z

## 提交统计

- **昨日提交总数**: 52
- **提交者数量**: 40
- **主要提交者**: Yejing Lai, Li, Jiang, Juntian Liu

## AI分析总结

根据提供的提交记录和项目背景，现对 vllm 项目昨日（2025-04-02）的提交进行总结分析：

### 1. 主要更新类型
*   **Bug 修复 (占比最高)：** 涉及多模态处理、量化（fp8, W4A8 MoE）、KV缓存、CUDA图、采样、前端及特定模型（如Ovis、Idefics3）等多个核心组件。
*   **性能优化：** 包括并行化CUDA/Triton内核预热、优化FlashInfer解量化、使用Conv3dLayer加速、利用MXFP8指令等，旨在降低启动延迟和提升推理速度。
*   **平台支持与CI增强：** 大量针对AMD ROCm和Intel XPU的修复、优化和CI测试改进，提升了硬件兼容性与自动化质量。
*   **架构清理与重构：** 移除过时功能（如在线量化、慢速分词器模式）、重构辅助文件、清理冗余测试和配置，以简化代码库并提升可维护性。
*   **功能微调与新增：** 新增启动填充模式、请求日志调试、权重缓存守护进程等待等实用功能。

### 2. 关键变更点及其与项目方向的关系
*   **强化多模态与量化核心功能：** 修复了多模态块哈希、图像分块计数及多种量化格式的问题，直接服务于项目“支持多样化、高效LLM服务”的核心目标，确保复杂模型在不同精度下稳定运行。
*   **优化启动与运行时性能：** 并行化预热、优化CUDA图捕获和推理内核，紧扣项目“快速”与“低成本”的目标，减少用户等待时间和计算开销。
*   **扩大硬件生态覆盖：** 对ROCm（MI355）、XPU（默认启用图模式）、CPU（Zen架构注意力）的持续投入，践行了“for everyone”的理念，降低特定硬件用户的使用门槛。
*   **提升代码健壮性与可维护性：** 清理冗余代码、重构测试、移除废弃API，为项目长期健康发展和技术迭代打下基础。

### 3. 对项目的影响和潜在意义
*   **短期影响：** 显著提升了模型在多种硬件和量化配置下的运行稳定性和性能，特别是修复了影响多模态与推理正确性的关键bug，增强了生产环境的可靠性。
*   **长期意义：** 通过对AMD和Intel平台的深度优化与测试，巩固了vLLM作为跨平台高性能LLM推理引擎的地位。代码库的持续清理与重构有助于降低未来贡献和维护的复杂度。

### 4. 值得关注的技术点
*   **硬件特异性优化：** 如针对AMD MI355使用MXFP8指令和分组FP8 GEMM，以及为Zen CPU优化注意力内核，展示了针对不同硬件特性进行深度适配的能力。
*   **系统稳定性增强：** 如在启用故障容忍时正确处理JIT预热、修复多解码P/D解耦中的竞态条件，体现了对生产级系统稳定性的关注。
*   **调试与可观测性：** 在Rust前端增加请求日志、修复调试跟踪干扰，有助于开发者诊断和解决问题。

### 5. 基于项目背景的提交影响总结
这些提交紧密围绕vLLM“**易用、快速、廉价**”的核心愿景。**Bug修复和稳定性增强**保障了服务的可靠性，这是“易用”的基础；**性能优化**直接降低了延迟和成本，体现了“快速”与“廉价”；**对多硬件平台的持续投入**则拓宽了“for everyone”的边界，让不同硬件背景的用户都能受益。同时，**架构清理与重构**为项目容纳更多功能和更复杂的模型提供了可持续发展的空间，确保了项目能长期、健康地朝着既定目标演进。

## 详细提交记录

### [7a94066](https://github.com/vllm-project/vllm/commit/7a9406690ebe2fc47236a81cf7ec33188c6565e2)

- **作者**: Zijing Liu
- **时间**: 2026-09-24T23:55:47Z
- **提交信息**: [KV Connector] Fix DecodeBench fp8 fill values and add a startup fill mode (#58472)

Signed-off-by: Zijing Liu <liuzijing2014@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [71891bd](https://github.com/vllm-project/vllm/commit/71891bdb94d79533049c9eb314884f53480eea3d)

- **作者**: Misha Goin
- **时间**: 2026-09-24T23:52:00Z
- **提交信息**: [Perf] Parallelize registered CUDA Triton kernel warmup at startup (#58582)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [d5051ab](https://github.com/vllm-project/vllm/commit/d5051abaf19a1cce19159756a79d27ccb0b2fccf)

- **作者**: Netanel Haber
- **时间**: 2026-09-24T23:46:42Z
- **提交信息**: [Bugfix][Mamba] Restore prompt-tail prefix-cache hits with MTP (#58368)

Signed-off-by: Netanel Haber <58652339+netanel-haber@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>

### [4f72bd0](https://github.com/vllm-project/vllm/commit/4f72bd0152e74f3485216aebb3f5d276b6726a9a)

- **作者**: Misha Goin
- **时间**: 2026-09-24T23:39:49Z
- **提交信息**: [Bugfix][Quantization] Give LM heads standard linear metadata (#58444)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [9ac3b7c](https://github.com/vllm-project/vllm/commit/9ac3b7c69f8294ef0e80f03c2991b32ab8379f96)

- **作者**: stefankoncarevic
- **时间**: 2026-09-24T23:38:25Z
- **提交信息**: [ROCm][CI] Mirror the DSv4-Flash disaggregated DP EP group on MI355 (#58558)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [f6aa291](https://github.com/vllm-project/vllm/commit/f6aa2919bc4afb93e286be55dbe2a4b1d778fbc3)

- **作者**: Sense_wang
- **时间**: 2026-09-24T23:25:01Z
- **提交信息**: [Bugfix][Core] Keep every multimodal feature in the partial-block KV event (#58288)

Signed-off-by: haosenwang1018 <haosenwang1018@users.noreply.github.com>
Co-authored-by: haosenwang1018 <haosenwang1018@users.noreply.github.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [bd4cb3f](https://github.com/vllm-project/vllm/commit/bd4cb3fe4efd1e19ceec1f31fcd4bfe599b0c3ac)

- **作者**: Miłosz Grunwald
- **时间**: 2026-09-24T23:18:54Z
- **提交信息**: [BUGFIX] fix ovis2_5 multimodal tokens (#52623)

Signed-off-by: Milosz Grunwald <milosz.grunwald@intel.com>

### [6a86bf6](https://github.com/vllm-project/vllm/commit/6a86bf626e32555a21018050d57befca1a704344)

- **作者**: snadampal
- **时间**: 2026-09-24T23:15:32Z
- **提交信息**: [PD][PushConnector] Record last activity of remotes on the D side (#52245)

Signed-off-by: Sunita Nadampalli <nadampal@amazon.com>
Co-authored-by: Nicolò Lucchesi <nicolo.lucchesi@mistral.ai>

### [f5b40fc](https://github.com/vllm-project/vllm/commit/f5b40fcdfefb66138cb20031f82c86ac0f53722a)

- **作者**: Andrey Talman
- **时间**: 2026-09-24T23:02:30Z
- **提交信息**: [CI] Report to CRCR after all jobs finish, gated on the build's long pole (#58628)

### [7edb27f](https://github.com/vllm-project/vllm/commit/7edb27f68e23410e73d74066e4e3ce9ba27d4421)

- **作者**: Fanli Lin
- **时间**: 2026-09-24T22:56:59Z
- **提交信息**: [XPU][CI] enable prompt embeds tests on XPU (#58283)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Signed-off-by: Fanli Lin <fanli.lin@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [e6c07ea](https://github.com/vllm-project/vllm/commit/e6c07ea5763bada5da789ed437851ee1526fd5a8)

- **作者**: Jellow
- **时间**: 2026-09-24T22:38:03Z
- **提交信息**: [Bugfix][KV Cache] Fix incremental multimodal block hashing (#51694)

Signed-off-by: Jellow <49915976+CZT0@users.noreply.github.com>
Signed-off-by: Jellow <dvdx@foxmail.com>

### [36f94d5](https://github.com/vllm-project/vllm/commit/36f94d5fe8a3953f1ad340de3c5aaec909765243)

- **作者**: Nick Hill
- **时间**: 2026-09-24T21:55:56Z
- **提交信息**: [Bugfix][Outlines] Fix EOS termination and unconstrained masks after rejected drafts (#58612)

### [04730e8](https://github.com/vllm-project/vllm/commit/04730e82700d0c9b957cda188dd1bbc8073e1fcd)

- **作者**: Juntian Liu
- **时间**: 2026-09-24T21:38:04Z
- **提交信息**: [DFlash] Capture the context K/V precompute in the draft CUDA graph (#57632)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [e33de82](https://github.com/vllm-project/vllm/commit/e33de821c0df5c15d0fad990a754f3b69a6478e3)

- **作者**: stefankoncarevic
- **时间**: 2026-09-24T20:36:36Z
- **提交信息**: [ROCm][CI] skip the ROCm MRV1 default where MRV1 cannot serve the config (#58535)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [0908116](https://github.com/vllm-project/vllm/commit/0908116dd9e27766efdd46f37a108c5a6b7ade53)

- **作者**: Aaron Kang
- **时间**: 2026-09-24T20:17:02Z
- **提交信息**: [Bugfix] Pass quant_config to DiffusionGemma's ParallelLMHead (#48521)

Signed-off-by: Aaron Kang <aaron.h.kang@icloud.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [ab3de6e](https://github.com/vllm-project/vllm/commit/ab3de6edf2b34507e066d998c09f2361a5c1d8ce)

- **作者**: Matt Mastracci
- **时间**: 2026-09-24T20:15:08Z
- **提交信息**: [Perf] DiffusionGemma: constrained reads over the request's logprob_token_ids (#58216)

Signed-off-by: Matt Mastracci <matthew@mastracci.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [92e9c6b](https://github.com/vllm-project/vllm/commit/92e9c6bf13138da9caa42c815e242affee046c20)

- **作者**: Vincent Cavé
- **时间**: 2026-09-24T19:52:43Z
- **提交信息**: [ROCm] Fix misrouting race-condition in multi-decode P/D disagg with mori-io (#51681)

Signed-off-by: Vincent Cave <vincent.cave@amd.com>
Signed-off-by: Shiksha Patel <shikpate@amd.com>
Co-authored-by: Shiksha Patel <shikpate@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [90a9515](https://github.com/vllm-project/vllm/commit/90a951500699b1aa499f350b3352450cdcc13340)

- **作者**: fxmarty-amd
- **时间**: 2026-09-24T19:48:14Z
- **提交信息**: [Cleanup] Remove online quantization support in `fp8.py` in favor of online shorthands (#53585)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mgoin <mgoin64@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [58aa2f1](https://github.com/vllm-project/vllm/commit/58aa2f1ef1fa993b7178ca454e0807f60e8d3dbc)

- **作者**: Misha Goin
- **时间**: 2026-09-24T19:38:56Z
- **提交信息**: [Refactor] Move auxiliary files out of the repository root (#58572)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [cd06e81](https://github.com/vllm-project/vllm/commit/cd06e81c41f7d1f92a5680a616ad9679232a9e7a)

- **作者**: Misha Goin
- **时间**: 2026-09-24T19:37:33Z
- **提交信息**: [Bugfix][Quantization] Add Humming to the W4A8 (INT4xFP8) MoE oracle (#58427)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [e773247](https://github.com/vllm-project/vllm/commit/e773247f8aee272d0262928117e3049cd2902b5e)

- **作者**: Xun Sun
- **时间**: 2026-09-24T19:18:04Z
- **提交信息**: [Fast Start] Wait for weight cache daemon readiness (#58370)

### [e30559b](https://github.com/vllm-project/vllm/commit/e30559b58fe8dc1f688de3c16a910ca6108a2c7d)

- **作者**: Nick Hill
- **时间**: 2026-09-24T19:08:16Z
- **提交信息**: [Core] Skip JIT monitor when JIT warmup is disabled (#58590)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>

### [074d57f](https://github.com/vllm-project/vllm/commit/074d57fce1a1f39426fdebe8b4affac02c6e749c)

- **作者**: Nick Hill
- **时间**: 2026-09-24T19:07:32Z
- **提交信息**: [Bugfix] Keep JIT warmup under enforce-eager when fault tolerance is on (#58593)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Kimi <noreply@moonshot.cn>

### [5b3f280](https://github.com/vllm-project/vllm/commit/5b3f280a6df68c4f8264014380249ba530173ed6)

- **作者**: nightcityblade
- **时间**: 2026-09-24T18:36:26Z
- **提交信息**: [Bugfix] Count unsplit Idefics3 image patches (#48760)

Signed-off-by: nightcityblade <nightcityblade@gmail.com>
Co-authored-by: nightcityblade <nightcityblade@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [8b84e15](https://github.com/vllm-project/vllm/commit/8b84e15066b07cf0064a0ff05f153cc85cb42817)

- **作者**: Thomas Ortner
- **时间**: 2026-09-24T16:33:06Z
- **提交信息**: [transformer] RMSNorm matching for alternative rsqrt (#54461)

Signed-off-by: Thomas Ortner <boh@zurich.ibm.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [09fe178](https://github.com/vllm-project/vllm/commit/09fe178dba08e6de4448ade1e37d14ae1dab3acf)

- **作者**: Nick Hill
- **时间**: 2026-09-24T15:48:36Z
- **提交信息**: Revert "[DSpark] Support pipeline-parallel targets in aggregated serving (#56956)" (#58484)

### [d636456](https://github.com/vllm-project/vllm/commit/d636456b1f9cc77706543203ea0e66a7598e490e)

- **作者**: Harry Mellor
- **时间**: 2026-09-24T15:48:28Z
- **提交信息**: [Frontend] Remove the slow tokenizer mode (#58545)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [344fcc2](https://github.com/vllm-project/vllm/commit/344fcc252ab15541fc50250ebdfcf691e92dd6e6)

- **作者**: Lucain
- **时间**: 2026-09-24T15:48:24Z
- **提交信息**: [Bugfix] Resolve the Hub revision once per repo (#56092)

Signed-off-by: Wauplin <lucainp@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a7d203e](https://github.com/vllm-project/vllm/commit/a7d203efe549de57d8289ad15dc4fdeccf1179be)

- **作者**: hcl
- **时间**: 2026-09-24T15:48:18Z
- **提交信息**: fix(config): apply presence_penalty/frequency_penalty from override-generation-config (#50769)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>
Signed-off-by: hclsys <chenglunhu@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [26f49e3](https://github.com/vllm-project/vllm/commit/26f49e336a1498300a442a0d95911c11f5284500)

- **作者**: Yueh-Ting (eop) Chen
- **时间**: 2026-09-24T14:42:08Z
- **提交信息**: [Perf][Attention] Bound FlashInfer prefill dequantization scratch (#57918)

Signed-off-by: Yueh-Ting Chen <yueh.ting.chen@gmail.com>

### [3c42385](https://github.com/vllm-project/vllm/commit/3c42385d7dcce60cc231bcd9127b56379f43f823)

- **作者**: Wentao Ye
- **时间**: 2026-09-24T14:29:56Z
- **提交信息**: [Refactor] Remove dead or duplicate tests (#58446)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [d881812](https://github.com/vllm-project/vllm/commit/d881812500b49bc77c8e1106664c75ffee16958e)

- **作者**: Harry Mellor
- **时间**: 2026-09-24T14:14:10Z
- **提交信息**: [Chore] Use Transformers v5 names and drop redundant processor `use_fast` (#58550)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [484c211](https://github.com/vllm-project/vllm/commit/484c211fe80d003b0ae03dee7676767bac753d8a)

- **作者**: Linze Shi
- **时间**: 2026-09-24T13:51:25Z
- **提交信息**: [Bugfix][Pooling] Fix JinaVL label configuration and restore multimodal tests (#57347)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [cccf7e1](https://github.com/vllm-project/vllm/commit/cccf7e1376ba082a2b14190a1a1fa963acb953b7)

- **作者**: Harry Mellor
- **时间**: 2026-09-24T12:57:23Z
- **提交信息**: Remove `.gemini/` and `CLAUDE.md` (#58541)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [721d0e5](https://github.com/vllm-project/vllm/commit/721d0e5c112a2e4e0bed9078fc8d953eaaf5abc2)

- **作者**: Fangzhou Ai
- **时间**: 2026-09-24T11:58:14Z
- **提交信息**: [ROCm][DSv4.1][Perf] Emit MXFP8 from the sparse decode reduce and run wo_a as a grouped FP8 GEMM (#58456)

Signed-off-by: fai <fangzhouai@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dcfc17e](https://github.com/vllm-project/vllm/commit/dcfc17e0b1cb4a4bb4eeca9a75c82b82d776f25e)

- **作者**: liuzhenwei
- **时间**: 2026-09-24T11:17:25Z
- **提交信息**: [XPU] enable XPU GRAPH by default (#51600)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>

### [f5a78f2](https://github.com/vllm-project/vllm/commit/f5a78f2ad73dda260e87477ae491157e59f5de1d)

- **作者**: Zijing Liu
- **时间**: 2026-09-24T10:47:50Z
- **提交信息**: [Multimodal] Reuse the supplied tokenizer in the MiniMax-M3 VL processor (#58460)

Signed-off-by: Zijing Liu <liuzijing2014@gmail.com>

### [5747d45](https://github.com/vllm-project/vllm/commit/5747d4500a085496b874bd03c5cafb01f51ace56)

- **作者**: SHREY GAJJAR
- **时间**: 2026-09-24T10:39:21Z
- **提交信息**: [Perf][Frontend] Offload streaming derender detokenization (#57528)

Signed-off-by: Shrey Gajjar <shreygajjar007@gmail.com>

### [f34a0e0](https://github.com/vllm-project/vllm/commit/f34a0e07978eb78c2586b88ef660e7f5308c036e)

- **作者**: Ganesh R
- **时间**: 2026-09-24T10:07:53Z
- **提交信息**: [CPU] Gate the AVX10.2 paths on compiler support (#58133)

Signed-off-by: R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [cfd5c20](https://github.com/vllm-project/vllm/commit/cfd5c20286b7f4be705fe976ad38d0307ba8cd6f)

- **作者**: Ziyang Ma
- **时间**: 2026-09-24T10:07:37Z
- **提交信息**: [XPU][UT] Align HF and vLLM inputs for Qwen2 embedding test by preventing Sentence Transformers from applying chat template (#58117)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>

### [e430f74](https://github.com/vllm-project/vllm/commit/e430f7421ff095d8f5fbf1b910438f7d35d9bdf3)

- **作者**: Reid
- **时间**: 2026-09-24T09:22:23Z
- **提交信息**: [Bugfix][Rust Frontend] Prevent MM timing from enabling debug tracing (#58378)

Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [bbd7c24](https://github.com/vllm-project/vllm/commit/bbd7c24d6e365dbad98543701a6bde363f1d8aa3)

- **作者**: Taneem Ibrahim
- **时间**: 2026-09-24T09:07:26Z
- **提交信息**: [MRV2] Validate MRV2 entrypoint logits processors (#57728)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [5963795](https://github.com/vllm-project/vllm/commit/5963795ec7d7beaf34a05a213cce113c6508a8d4)

- **作者**: Priyansh Jain
- **时间**: 2026-09-24T09:05:44Z
- **提交信息**: [Attention][CPU] Run Zen CPU encoder attention on zentorch SDPA (#54508)

Signed-off-by: priyansh jain <priyansh.jain2@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [14f98cb](https://github.com/vllm-project/vllm/commit/14f98cbe5d447d452bb9f670fa82a6e65e3f00e6)

- **作者**: Yejing Lai
- **时间**: 2026-09-24T09:05:26Z
- **提交信息**: [Bugfix][XPU] store the pointer raw bit pattern instead of its numeric value (#54514)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [c0c35dd](https://github.com/vllm-project/vllm/commit/c0c35ddd8e9c6dadd53a8f92e20e9a03a210da15)

- **作者**: stefankoncarevic
- **时间**: 2026-09-24T09:05:11Z
- **提交信息**: [Bugfix][CI] Fix the flaky sharded-sampling tests, and the engine teardown need (#58342)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [23110a0](https://github.com/vllm-project/vllm/commit/23110a0c9ef8823406f04f919fcd61e030da8b81)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-24T09:05:07Z
- **提交信息**: [Bugfix] Capture prefill kernels for mixed FULL graphs (#58275)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [bbc4dde](https://github.com/vllm-project/vllm/commit/bbc4ddeca9ece9851aad26f03afc4bab37c6e8df)

- **作者**: jackLei
- **时间**: 2026-09-24T08:40:47Z
- **提交信息**: [Bugfix][V1] Reject encoder-cache hits with mismatched embedding counts (#57696)

Signed-off-by: jackLei0901 <42642542+jackLei0901@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b44895c](https://github.com/vllm-project/vllm/commit/b44895cf932be890235b700b49b0753261cf5b97)

- **作者**: Li, Jiang
- **时间**: 2026-09-24T08:12:34Z
- **提交信息**: [CPU] Use pre-built triton (#58140)

Signed-off-by: jiang1.li <jiang1.li@intel.com>

### [28282ff](https://github.com/vllm-project/vllm/commit/28282ffe34ee073559149cf388008111da0b3b16)

- **作者**: Talor Abramovich
- **时间**: 2026-09-24T08:08:40Z
- **提交信息**: [Feature][Frontend] Request JSON body debug logging on `--enable-log-requests` flag (#58163)

Signed-off-by: talora <talora@nvidia.com>

### [00b7847](https://github.com/vllm-project/vllm/commit/00b7847c8036b667742b4efb21aab1de51fd4721)

- **作者**: Thien Tran
- **时间**: 2026-09-24T07:41:36Z
- **提交信息**: [Perf] Use Conv3dLayer for MiniMax M3 patch embedding (#58512)

Signed-off-by: OpenAI Codex <codex@openai.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [1291bdb](https://github.com/vllm-project/vllm/commit/1291bdb85edc3cf0a1232be408b7e866b9d3f10a)

- **作者**: GuorongYe
- **时间**: 2026-09-24T07:41:15Z
- **提交信息**: [EPD][Model Loader] Skip language-model checkpoint shards for `--mm-encoder-only` (#58086)

Signed-off-by: grYe99 <guorongye99@gmail.com>
Co-authored-by: grYe99 <guorongye99@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>

### [c3f5270](https://github.com/vllm-project/vllm/commit/c3f5270270aedf598b5f633088623c194c8f0b6c)

- **作者**: Andreas Karatzas
- **时间**: 2026-09-24T07:16:09Z
- **提交信息**: [ROCm][CI] Add the MI355 TurboQuant t3nc mirror (#58432)

Signed-off-by: Andreas Karatzas <andreas.karatzas@protonmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-25
**监控日期**: 2026-09-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7056
- **最后更新**: 2026-09-25T00:22:09Z

## 提交统计

- **昨日提交总数**: 32
- **提交者数量**: 26
- **主要提交者**: Yueqian Lin, andyluo7, NATURE

## AI分析总结

基于提交记录与项目背景，现对vllm-project/vllm-omni仓库近期更新进行总结分析：

**1. 主要更新类型**
本次提交以**Bug修复**和**CI/Build改进**为主，同时包含显著的**性能优化**。具体而言，约半数提交（如修复流式处理失败、跨硬件支持、资源回收等）属于核心稳定性修复；其次是持续强化测试基础设施（如添加测试组、修复基准测试）；另有多项针对特定模型（如MiniCPM-o， LingBot）的性能与功能优化。

**2. 关键变更点及其与项目方向的关系**
*   **稳定性与健壮性增强**：大量修复集中在前端（#7011, #6487）、核心调度（#56da589, #6228）和资源管理（#8082），直接提升了系统在生产环境中的可靠性，符合“简单可靠”的服务目标。
*   **多模态模型支持深化**：修复了MiniCPM-o（#7974, #7968）、Cosmos3（#8101, #7971）等多模态模型的具体问题，并优化了LingBot的流式解码（#7749），体现了项目对复杂多模态交互场景的持续聚焦。
*   **性能与效率优化**：引入精确投影缓存（#7987）和优化流式解码（#7749）等变更，直接响应项目“快速”的核心目标。
*   **跨平台与CI成熟度提升**：修复XPU支持（#7961）、NPU基准测试（#8107），并加强测试隔离性（#6337），为项目的可移植性和长期可维护性奠定基础。

**3. 对项目的影响和潜在意义**
这些变更标志着项目从功能快速迭代迈向**成熟化与生产就绪阶段**。大量边缘案例的修复和基础设施的加固，显著提高了系统稳定性，降低了部署风险。对特定高性能模型的深度优化，增强了其在真实场景中的可用性。持续的跨硬件适配则扩大了项目的应用范围。

**4. 值得关注的技术点**
*   **分布式推理协调**：如“跨SP同步TeaCache跳过决策”（#6228）涉及分布式系统中的一致性保障，是确保并行推理正确性的关键技术。
*   **高效内存管理**：“回收中止的块共享内存”（#8082）体现了对推理资源生命周期精细化的管控，对降低延迟和内存占用至关重要。
*   **动态模型配置**：如从配置文件读取隐藏层键（#5825）和替换硬编码默认值（#5814），增强了系统对不同模型变体的灵活性和兼容性。

**5. 对项目发展的整体影响**
结合README所述“为每个人提供简单、快速且低成本的全模态模型服务”这一愿景，本次提交批次通过**夯实底层稳定性、优化关键路径性能、并拓宽硬件与模型支持范围**，有力推动了项目向该目标迈进。这些工作虽非炫目的新功能，但构成了项目作为可靠基础设施不可或缺的基石，使其能够更好地服务于日益增长的全模态应用需求。

## 详细提交记录

### [4aac129](https://github.com/vllm-project/vllm-omni/commit/4aac1294f1d002b9ed1d8c97eb2e96c69c5125d5)

- **作者**: Jim Ban
- **时间**: 2026-09-24T23:50:43Z
- **提交信息**: [Bugfix][Frontend] Surface streaming terminal submit failures (#7011)

Signed-off-by: BANANASJIM <bananasjim1@gmail.com>
Signed-off-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [6fb2b36](https://github.com/vllm-project/vllm-omni/commit/6fb2b36a8165bc3dc320421a43166bf117663ae9)

- **作者**: Khairul Kabir
- **时间**: 2026-09-24T23:19:45Z
- **提交信息**: [CI][Diffusion] Add acceleration test groups for SD3 and Flux2 (#6625)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>

### [29d13e3](https://github.com/vllm-project/vllm-omni/commit/29d13e331134418316e882446be21aac6aeb0878)

- **作者**: Khairul Kabir
- **时间**: 2026-09-24T19:23:28Z
- **提交信息**: [CI][Diffusion] Add tiny model builder for StableDiffusion3Pipeline (#6423)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>

### [b539282](https://github.com/vllm-project/vllm-omni/commit/b539282a9a808364488cd869f1c26386d7918f05)

- **作者**: Joshna-Medisetty
- **时间**: 2026-09-24T18:57:38Z
- **提交信息**: [Bugfix][XPU] Enable LTX-2 family on XPU (#7961)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>

### [7b4dc76](https://github.com/vllm-project/vllm-omni/commit/7b4dc7633bde8642f0c05f77bd018751541df404)

- **作者**: Isotr0py
- **时间**: 2026-09-24T16:58:57Z
- **提交信息**: [Doc] Announce PR limitation to avoid agent spam (#8131)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [af46abe](https://github.com/vllm-project/vllm-omni/commit/af46abebb572f25ebcfdbbdef6e592a219428f2d)

- **作者**: ChoHee
- **时间**: 2026-09-24T16:56:41Z
- **提交信息**: [Bugfix][Diffusion] Bound diffusion execute RPCs with the DP wave timeout (#7745)

Signed-off-by: ChoHee15 <cc5281@126.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [b7c0e54](https://github.com/vllm-project/vllm-omni/commit/b7c0e541d2599b477b6e033899e22e8389a95d73)

- **作者**: Gao Han
- **时间**: 2026-09-24T16:38:43Z
- **提交信息**: [Bugfix] Print text alongside audio in multimodal chat example (#8130)

Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>

### [f58ef57](https://github.com/vllm-project/vllm-omni/commit/f58ef57ac4594b966441ee57cd36e2c331a6a056)

- **作者**: Aman
- **时间**: 2026-09-24T16:22:17Z
- **提交信息**: [Bugfix] Enable pipeline profiling for LingBot Video (#7744)

Signed-off-by: bezdarnost <amanurumbekov@gmail.com>

### [9376c21](https://github.com/vllm-project/vllm-omni/commit/9376c21eddd2cfaefab5805e69b15e4716ea82f4)

- **作者**: NumberWan
- **时间**: 2026-09-24T16:18:34Z
- **提交信息**: [Bugfix][Cosmos3] Resolve per-component transformer quantization config (#8101)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>
Co-authored-by: Oliver7th <fangzhengyi@huawei.com>

### [56da589](https://github.com/vllm-project/vllm-omni/commit/56da589a3e347d8f5482a77fb9a3682472eb1b20)

- **作者**: yzong-rh
- **时间**: 2026-09-24T16:17:27Z
- **提交信息**: [Bugfix] Sync TeaCache skip decision across SP to prevent deadlock (#6228)

Signed-off-by: Yifan Zong <yzong@redhat.com>

### [28c87cd](https://github.com/vllm-project/vllm-omni/commit/28c87cde19fffacc1a683de93e86812608ef2d3d)

- **作者**: Khairul Kabir
- **时间**: 2026-09-24T16:10:01Z
- **提交信息**: [Bugfix] Replace hardcoded Vivian speaker default with config-ordered default (#5814)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: Claude Opus 4.6 <noreply@anthropic.com>
Co-authored-by: Alex Brooks <albrooks@redhat.com>

### [cd2fed9](https://github.com/vllm-project/vllm-omni/commit/cd2fed99a7d122d1f390dc0a9c46cd9742c642ca)

- **作者**: Zhenghan Song
- **时间**: 2026-09-24T16:01:05Z
- **提交信息**: [CI/Build] Make benchmark CLI test hermetic (#6337)

Signed-off-by: HaningZS <resossr0v0@gmail.com>

### [8f58088](https://github.com/vllm-project/vllm-omni/commit/8f58088f31afd5c0067bc32c68956050991b8332)

- **作者**: devangpratap
- **时间**: 2026-09-24T15:59:42Z
- **提交信息**: [Bugfix] Fix OmniRequestOutput iteration in the MOSS-TTS-Nano offline example (#6583)

Signed-off-by: devangpratap <115096812+devangpratap@users.noreply.github.com>

### [2d00d86](https://github.com/vllm-project/vllm-omni/commit/2d00d86e5ec8d2a9f1bce06c69b4833c5b95e18b)

- **作者**: psv666
- **时间**: 2026-09-24T15:56:53Z
- **提交信息**: [CI/Build] Fix Qwen3-Omni Talker benchmark workload (#8057)

Signed-off-by: psv666 <2693925048@qq.com>

### [0295eeb](https://github.com/vllm-project/vllm-omni/commit/0295eeb6f3d62c7302f63e0b67c21649adb9c2c5)

- **作者**: Yancy
- **时间**: 2026-09-24T15:32:07Z
- **提交信息**: [Orchestrator] Implement cache reset RPC forwarding to AR stage engine cores (#6766)

Signed-off-by: Asthenia <asthenia0412@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Asthenia <asthenia0412@gmail.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [535bd35](https://github.com/vllm-project/vllm-omni/commit/535bd35b4252e3c031d4b64c60a6250cb78a579c)

- **作者**: SYLAR
- **时间**: 2026-09-24T15:30:42Z
- **提交信息**: [Perf] Add reusable exact projection caching with MiniMax-H3 integration (#7987)

Signed-off-by: lishunyang12 <lishunyang12@users.noreply.github.com>
Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>
Co-authored-by: lishunyang12 <lishunyang12@users.noreply.github.com>
Co-authored-by: Armaan Amatya <38102001+armaanamatya@users.noreply.github.com>

### [63bbd19](https://github.com/vllm-project/vllm-omni/commit/63bbd19a1d04aa7138528b6ee37cf9e17fc28386)

- **作者**: Khairul Kabir
- **时间**: 2026-09-24T15:19:41Z
- **提交信息**:  [Bugfix] Read hidden layer key from model config instead of hardcoding 24 (#5825)

Signed-off-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>
Co-authored-by: khairulkabir1661 <khairulkabir1661@users.noreply.github.com>

### [24b2127](https://github.com/vllm-project/vllm-omni/commit/24b21278c064dba313140d8616071684d6171376)

- **作者**: Zeng Chuang
- **时间**: 2026-09-24T14:36:19Z
- **提交信息**: [CI/Build][NPU] Run HunyuanVideo-1.5 perf step via run_benchmark.py (#8107)

Signed-off-by: zengchuang <zengchuang3@huawei.com>

### [7e5897b](https://github.com/vllm-project/vllm-omni/commit/7e5897b8482d67800b561d6a7a5736a67c6485a1)

- **作者**: wangyu
- **时间**: 2026-09-24T13:45:00Z
- **提交信息**: [CI/Build][Bugfix] Cover corrupt chat audio data URLs on Qwen3-Omni (#8108)

Signed-off-by: wangyu <410167048@qq.com>

### [9b08ac8](https://github.com/vllm-project/vllm-omni/commit/9b08ac8203fae9d3093b5ee1e4cef3b6ebf0caa4)

- **作者**: andyluo7
- **时间**: 2026-09-24T13:43:25Z
- **提交信息**: [Bugfix][Diffusion] Clean up inline worker lifecycle (#7986)

Signed-off-by: andyluo7 <andy.luo@amd.com>

### [0a0e188](https://github.com/vllm-project/vllm-omni/commit/0a0e1884f7eb692234d4ec9965bc53275c58e7b7)

- **作者**: Canlin Guo
- **时间**: 2026-09-24T13:34:00Z
- **提交信息**: [CI/Build] Initialize RoPE frequencies in MiniMax H3 TeaCache tests (#8125)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [ed5fc2b](https://github.com/vllm-project/vllm-omni/commit/ed5fc2b83b5dcfda6bae7132b4ac87a4b2ca54c2)

- **作者**: Zheng Wengang
- **时间**: 2026-09-24T12:35:24Z
- **提交信息**: [Hotfix][Core] PrefixCache: re-plan same-step prefix hits whose rows are written after the early prefetch (#7877)

Signed-off-by: ZhengWG <zwg0606@gmail.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9c1656c](https://github.com/vllm-project/vllm-omni/commit/9c1656c607103001daf387c33bb8b0b6b84990ad)

- **作者**: NATURE
- **时间**: 2026-09-24T12:18:56Z
- **提交信息**: [Model] Reduce MiniCPM-o 4.5 reference setup and Talker overhead (#7968)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: xjwu <wuxianjin633@gmail.com>
Co-authored-by: Eric(Qun) <186020953+0xtoward@users.noreply.github.com>

### [ba3d48e](https://github.com/vllm-project/vllm-omni/commit/ba3d48e1c783083634b3f70acbb8f2512658e65f)

- **作者**: Zhou Taichang
- **时间**: 2026-09-24T10:56:44Z
- **提交信息**: [LingBot World] Speed up streaming VAE decode and RGB frame delivery (#7749)

Signed-off-by: tzhouam <tzhouam@connect.ust.hk>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9f7dada](https://github.com/vllm-project/vllm-omni/commit/9f7dadaad5e5d98ce96df284cfa36f3d9ef50503)

- **作者**: 0z5a
- **时间**: 2026-09-24T10:18:42Z
- **提交信息**: [CI/Build] Stabilize MiniCPM-o mixed-input audio consistency test (#7710)

Signed-off-by: 0z5a <dezhen.lu@student.uni-tuebingen.de>

### [7650020](https://github.com/vllm-project/vllm-omni/commit/765002061878d6c260009f0b13e042cfbb491cc6)

- **作者**: NumberWan
- **时间**: 2026-09-24T10:08:46Z
- **提交信息**: [BugFix][Cosmos3] Register opt-in T2I pipeline so deploy-config applies (#7971)

Signed-off-by: NumberWan <wantszkin2003@gmail.com>

### [7a8d956](https://github.com/vllm-project/vllm-omni/commit/7a8d956ece21fe30667ea7e0a6b419fbdf61c957)

- **作者**: NATURE
- **时间**: 2026-09-24T10:04:28Z
- **提交信息**: [Bugfix] Fix MiniCPM-o 4.5 native duplex speech alignment (#7974)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: liuqihao <liuqihao970610@gmail.com>

### [d486bf0](https://github.com/vllm-project/vllm-omni/commit/d486bf097a8d2b31c30a105785c1de21f256a263)

- **作者**: NATURE
- **时间**: 2026-09-24T09:59:43Z
- **提交信息**: [Bugfix] Reclaim aborted chunk SHM and consumed connector state (#8082)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: Gagan Dhakrey <gagandhakrey@gmail.com>

### [3b02e53](https://github.com/vllm-project/vllm-omni/commit/3b02e5338ace4aafe9fec5c0fb7a1316e155c15a)

- **作者**: z2z23n0
- **时间**: 2026-09-24T08:38:05Z
- **提交信息**: [Bugfix][Frontend] Return 500 for unexpected speech failures (#6487)

Signed-off-by: z2z23n0 <51999056+z2z23n0@users.noreply.github.com>
Co-authored-by: Canlin Guo <canlinguosdu@gmail.com>

### [926ba72](https://github.com/vllm-project/vllm-omni/commit/926ba72793778e018e5e789f2ed81b1598d812c8)

- **作者**: ZacheryAU
- **时间**: 2026-09-24T08:34:23Z
- **提交信息**: [Frontend][Benchmark] Add judger and accuracy metrics for OmniInterac… (#7317)

Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [1d77e96](https://github.com/vllm-project/vllm-omni/commit/1d77e96d4de4bfd701bdb7b88113548ac0593530)

- **作者**: Yueqian Lin
- **时间**: 2026-09-24T07:29:22Z
- **提交信息**: [Bugfix] Validate Breeze PCM speech content and calibrate HNR guard (#8044)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [dbd6a35](https://github.com/vllm-project/vllm-omni/commit/dbd6a35dd2e3d406bf0452d42d15f328b965b1e1)

- **作者**: Haozhe Jiang
- **时间**: 2026-09-24T07:28:00Z
- **提交信息**: [Bugfix] Reject partially bound diffusion LoRA adapters (#8008)

Signed-off-by: Haozhe Jiang <162801044+provoke210@users.noreply.github.com>

---
