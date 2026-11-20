# GitHub Stars 合并报告 - 2026-11-19

**合并日期**: 2026-11-20
**监控日期**: 2026-11-19
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


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2297
- **最后更新**: 2026-11-19T03:41:45Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Coach257, YLlllllllllll, Wangshiyu

## AI分析总结

# ByteDance-Seed/VeOmni 昨日提交分析（第 1/1 批，共 3 条）

## 1. 主要更新类型
- **功能新增**：为 SeedOmni 引入 Janus 多模态模型支持（#1449）。
- **Bug 修复**：修正 Janus 权重来源优先级，保证加载行为一致（#1483）。
- **重构 + 性能优化**：对 fla_npu 算子进行变长表提升（hoisting）与分组 Q/K 跳过逻辑调整（#1476）。
- 整体以模型侧功能扩展为主线，辅以配套修复与底层算子优化。

## 2. 关键变更点与项目整体方向的关系
- VeOmni 的核心目标是"以模型为中心的分布式配方库"支撑任意模态训练；**Janus 接入 SeedOmni** 正是扩展"any modality"能力的直接体现，新增了一类视觉-语言统一建模范式的配方。
- 随后的**权重优先级修复**表明团队在合入新模型后立即收敛加载语义，符合框架对多权重来源（本地/Hub/自定义）统一管理的设计要求。
- **fla_npu 优化**针对 NPU（昇腾）后端的算子调度与内存访问，呼应 README 中跨硬件高效训练的定位，属于"配方可扩展到生产级硬件"的基础设施投入。

## 3. 对项目的影响和潜在意义
- 功能面：用户可直接在 SeedOmni 中微调/训练 Janus 系列模型，扩大了模型动物园（recipe zoo）的覆盖面，增强对研究社区的吸引力。
- 稳定性面：权重优先级对齐降低了"同一模型不同环境加载结果不一致"这类隐性风险，提升开箱即用体验。
- 性能面：NPU 算子重构有望降低变长序列场景下的开销，为大规模长上下文或多模态混合训练提供吞吐收益。

## 4. 值得关注的技术点
- **变长（varlen）表 hoisting**：将 fla_npu 的变长查找表提升到更外层作用域，避免重复计算/分配，是典型的算子级热点治理手法。
- **分组 Q/K 跳过逻辑**：将 fla_npu 纳入跳过条件，说明不同注意力变体在特定分组形状下存在精度或性能权衡，需要按算子来源分流处理。
- **权重来源优先级**：多源权重解析的优先级顺序（如自定义路径 vs. 预训练仓库）被显式固定，是多模态框架配置体系中的易错点。

## 5. 基于 README 背景对项目发展的影响
这批提交延续了 VeOmni"以模型为中心、多模态、多硬件"的演进路线：新增 Janus 支持进一步充实了 SeedOmni 的模态覆盖，与论文所述的可扩展训练配方理念一致；配套修复与 NPU 算子优化则表明项目正从"能跑通新模型"迈向"在真实硬件上稳定高效地跑"，为后续吸引更多模型配方贡献和工业级落地奠定了基础。综上，本次提交在扩展模型能力的同时兼顾工程质量，是项目向更完整、更生产可用的多模态训练框架演进的稳健一步。

## 详细提交记录

### [99d4358](https://github.com/ByteDance-Seed/VeOmni/commit/99d43585ec39b8068bc835f38fa9c12eb49079fa)

- **作者**: YLlllllllllll
- **时间**: 2026-11-19T11:28:11Z
- **提交信息**: [model, ckpt] fix: align Janus weight source priority (#1483)

### [acae13e](https://github.com/ByteDance-Seed/VeOmni/commit/acae13e7daba5c26aaaa12d343d4fdae67a9f4e2)

- **作者**: Wangshiyu
- **时间**: 2026-11-19T08:37:08Z
- **提交信息**: [ops, model, perf] refactor: hoist fla_npu varlen tables and add fla_npu to the grouped q/k skip (#1476)

### [82db1ef](https://github.com/ByteDance-Seed/VeOmni/commit/82db1ef8afbcd8affbee65cf87b81ce3c54c1866)

- **作者**: Coach257
- **时间**: 2026-11-19T06:15:24Z
- **提交信息**: [omni, model, config, docs] feat: support Janus in SeedOmni (#1449)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3012
- **最后更新**: 2026-11-20T03:09:23Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 4
- **主要提交者**: Du jinyang, Wang Boyuan, zhengxinwei

## AI分析总结

## 1. 主要更新类型

- **性能优化**：Qwen-Image-2.1 在 Ascend NPU 上的算子级加速（RoPE、Q/K RMSNorm）与 MXFP8 W8A8 在线量化。
- **功能新增**：RelayVSR 支持显式输出尺寸、MXFP4 QAT 量化器、贡献者指南。
- **Bug 修复**：MiniMax-H3 参考媒体中不可解码音视频包的容错处理。
- **文档更新**：H3 README 更新。

## 2. 关键变更点与项目方向的关系

本次提交集中在两条主线：

- **NPU 硬件适配与推理加速**：新增 `torch_npu` 原生 RoPE/RMSNorm 算子（可配置、保留 PyTorch 回退路径），以及 MXFP8 W8A8 在线权重量化（加载时量化、推理时动态量化激活，无需离线转换）。这与 LightX2V "轻量视频生成推理框架" 的定位直接契合——降低显存占用与延迟是框架核心价值。
- **推理管线的灵活性与鲁棒性**：RelayVSR 的 `sr` 任务接受 `size [HEIGHT, WIDTH]`，允许两轴独立缩放，覆盖非均匀画布场景（如 1344×768 → 2560×1440 的 16:9 2K 输出），与 SwiftVR 的请求字段对齐；`relayvsr_x2` 保持严格 2x 契约并拒绝 `size`。参考媒体解码改为逐包解码并跳过 `InvalidDataError`，对齐 ffmpeg/托管 API 行为。

## 3. 对项目的影响与潜在意义

- NPU 优化提供了可量化收益：MXFP8 在 Ascend 950PR 上实现 T2I 1.30×/I2I 1.28× DiT 加速、峰值显存降约 20%；原生 RoPE 在 Ascend A5 上 T2I DiT/step 降约 9.9%，RMSNorm 再降约 2.5%。这显著提升了国产硬件上的可用性与部署性价比。
- RelayVSR 尺寸支持解除了固定缩放比限制，使框架能更好地对接真实产品的固定分辨率画布需求。
- 修复了用户实际遇到的拼接 MP3 导致请求失败的问题（#1736），提高了参考媒体输入的兼容性，减少线上失败率。
- 单元测试覆盖（几何、算子契约、scale 布局、配置校验）增强了量化路径与几何逻辑的可回归性。

## 4. 值得关注的技术点

- **MXFP8 在线量化设计**：E4M3 权重/激活 + group-32 E8M0 scale，加载时打包并处理奇数 scale 组 padding，FP32 bias；明确拒绝 CPU offload、TP/SP、LoRA、量化注意力等不支持组合，边界清晰。
- **数值等价性保持**：RMSNorm 用 unit gamma 调用原生算子、事后 BF16 施加学习 scale，以保留原始舍入边界；`dit_original_ckpt` 覆盖项通过原始 checkpoint loader 路由得以保留。
- **容错解码策略**：仅跳过坏包并计数日志，全空文件仍抛出原有错误——精细化的降级而非静默吞错。
- **算子加速的可配置回退**：原生 NPU 算子不可用时自动回落 PyTorch 实现，保证可移植性。
- 贡献者技能文件（#1740）的加入，说明项目开始规范化协作流程。

## 5. 对项目发展的整体影响

结合 README 中"轻量视频生成推理框架"的定位，这批提交体现了项目从"跑得通"向"跑得快、跑得稳、跑在国产硬件上"的演进方向。NPU 原生算子与量化能力构成了 Ascend 生态的差异化竞争力，配合 RelayVSR 灵活的输出尺寸控制和参考媒体容错，框架在真实生产场景中的适配度与鲁棒性明显提升。整体上，这些变更强化了 LightX2V 在高效推理和多硬件支持上的核心壁垒，为后续吸引更多硬件后端贡献与生产级部署奠定了基础。

## 详细提交记录

### [a095581](https://github.com/ModelTC/LightX2V/commit/a0955817fb2cefa85893498b23b172dd066cfdae)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-19T08:42:23Z
- **提交信息**: Add contribution skill (#1740)

### [8bbaabd](https://github.com/ModelTC/LightX2V/commit/8bbaabdefb5ffd3c4f0f1029feb780974464fba6)

- **作者**: zhengxinwei
- **时间**: 2026-11-19T08:14:19Z
- **提交信息**: feat(relayvsr): accept an explicit output size for x4 (#1735)

## Summary

RelayVSR x4 resizes its native 4x result to the requested output size
with a single bicubic pass (`RelayVSRRunner.postprocess`). Today that
size can only be derived from `sr_ratio`
(`RelayVSRGeometry.output_size`), so both axes are always scaled by the
same factor.

Some callers need a fixed output canvas rather than a uniform factor.
Example: MiniMax-H3 renders a 16:9 request at 768P as 1344×768 (area cap
768×1344, sides on multiples of 32). Upscaling that to the 16:9 2K
canvas 2560×1440 needs 1.905× horizontally and 1.875× vertically, which
`sr_ratio` cannot express (it yields 2520×1440).

This PR lets the `sr` task of RelayVSR accept `size` `[HEIGHT, WIDTH]`,
the same request field SwiftVR already uses.

## Changes

- `relayvsr/request_spec.py`: `size` becomes a request argument of the
`sr` task (it was a context-only field).
- `RelayVSRGeometry.output_size`: when `size` is set, the target is
exactly `size`, each axis scaled independently, and `sr_ratio` is
ignored. Without `size`, the existing `sr_ratio` path is unchanged.
- `RelayVSRRunner.create_input_info`: `sr_ratio` is validated only when
`size` is not set.
- `relayvsr_x2` keeps its exact 2x output contract and rejects `size`.
- The resize happens inside the existing bicubic step, so there is no
extra compute or encode pass. Even-dimension rounding for video output
is unchanged.
- `tests/test_relayvsr_geometry.py`: unit tests for the geometry (loads
the module directly, no GPU needed).

## Test

```
python3 tests/test_relayvsr_geometry.py
```

7 tests pass: uniform `sr_ratio`, `size` per-axis scaling (1344×768 →
2560×1440, 1408×736 → 2656×1376), `size` overriding `sr_ratio`, missing
`size`, invalid shapes, x2 rejection, and `sr_ratio` validation without
`size`.

---------

Co-authored-by: ZhengXinwei-F <ZhengXinwei-F@users.noreply.github.com>
Co-authored-by: Yang Yong (雍洋) <yongyang1030@163.com>

### [98e7fd2](https://github.com/ModelTC/LightX2V/commit/98e7fd2f8f8b6e468ba6e59fb9bd99f274143e1a)

- **作者**: Wang Boyuan
- **时间**: 2026-11-19T08:11:45Z
- **提交信息**: feat(qwen-image-2.1): add NPU MXFP8 W8A8 linear (#1669)

## Summary

Add online MXFP8 W8A8 linear quantization for Qwen-Image-2.1 on Ascend
NPU, covering both text-to-image and image-to-image inference. Weights
are quantized once when loading the original BF16/FP16 checkpoint, and
activations are dynamically quantized during inference. No offline
conversion or prequantized checkpoint is required.

On a single Ascend 950PR at 1024×1024 and 50 steps, this provides
**1.30× T2I / 1.28× I2I DiT speedup** and reduces peak allocated NPU
memory by **approximately 20%** versus BF16.

## Changes

- Register the `mxfp8-npu` linear backend using
`torch_npu.npu_dynamic_mx_quant` and `torch_npu.npu_quant_matmul`, with
E4M3 weights/activations and group-32 E8M0 scales.
- Quantize and pack weights/scales at load time, including padding for
an odd number of scale groups. Preserve the activation dtype and output
shape, and use FP32 bias for quantized matmul.
- Enable `mxfp8-npu` in the Qwen-Image-2.1 runner and the shared DiT
quantization scheme list. Route online loading through the original
checkpoint loader so `dit_original_ckpt` overrides are honored.
- Validate device, weight/activation dtype, dimensions, and unsupported
configurations before execution. This initial path targets resident
single-NPU inference; CPU offload, TP/SP, shared CPU weights, disk
streaming, LoRA, and quantized attention combinations are rejected.
- Add unit tests for registration, operator contracts, scale layouts,
shape restoration, checkpoint loading, and configuration validation.

## Performance

Measured on **1× Ascend 950PR**, CANN 9.1.0 / PyTorch 2.10.0 with
`torch_npu`, using the original Qwen-Image-2.1 checkpoint. Both
configurations use 1024×1024, 50 steps, CFG=1.0, `npu_flash_attn`, and
no compile, feature caching, offload, or LoRA. T2I uses seed 142; I2I
uses seed 42 with the same reference image.

Results are the median of **5 measured requests after 1 warmup**,
without profiling. DiT latency covers condition KV prefill through the
final scheduler update; text encoding, VAE processing, and HTTP overhead
are outside this timing boundary.

| Task | BF16 DiT latency | MXFP8 DiT latency | Speedup |
|---|---:|---:|---:|
| T2I | 14,800.1 ms | 11,358.8 ms | **1.303×** |
| I2I | 17,567.0 ms | 13,697.9 ms | **1.282×** |

| Task | BF16 peak allocated | MXFP8 peak allocated | Reduction |
|---|---:|---:|---:|
| T2I | 31.34 GiB | 25.06 GiB | **20.0%** |
| I2I | 31.70 GiB | 25.42 GiB | **19.8%** |

### Image quality

Paired comparisons against BF16 on one fixed input per task, with the
same seed and initial latents:

| Task | PSNR | SSIM | DINO feature cosine |
|---|---:|---:|---:|
| T2I | 35.20 dB | 0.9961 | 0.99649 |
| I2I | 18.97 dB | 0.9501 | 0.99053 |

T2I remains close to BF16; I2I shows larger pixel-level differences.
Side-by-side review found the degradation acceptable on the tested
inputs.

## Usage

Set the following fields in an Ascend Qwen-Image-2.1 configuration:

```json
{
  "dit_quantized": true,
  "dit_quant_scheme": "mxfp8-npu"
}
```

Use the original BF16/FP16 checkpoint via `model_path` or
`dit_original_ckpt`; `dit_quantized_ckpt` can be omitted. Requires an
Ascend NPU runtime with the MXFP8 quantization and matmul operators
above. Text encoder and VAE remain BF16 in the measured configuration.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added MXFP8 quantization support for Qwen Image 2.1 on Ascend NPU,
including loading from an original checkpoint without a pre-quantized
checkpoint.
* This mode requires an Ascend NPU and does not support CPU offload,
parallelism, shared CPU weights, disk streaming, LoRA, or
`npu_quant_flash_attn`.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: helloyongyang <yongyang1030@163.com>

### [1048e79](https://github.com/ModelTC/LightX2V/commit/1048e79eb9a26d58776a3f27ba3cd7378a4b5806)

- **作者**: Wang Boyuan
- **时间**: 2026-11-19T07:48:59Z
- **提交信息**: perf(qwen-image-2.1): accelerate Ascend inference with native RoPE and Q/K RMSNorm (#1662)

## Summary

This PR accelerates Qwen-Image-2.1 inference on Ascend NPU by
introducing native implementations for two performance-critical
operators:

- Q/K RoPE based on `torch_npu.npu_rotary_mul`
- Q/K RMSNorm based on `torch_npu.npu_rms_norm`

Both optimizations are configurable and retain the original PyTorch
implementations as fallbacks.

## Changes

- Add `qwen_image_21_npu_rope` for native Ascend RoPE.
  - Compute and cache the FP32 cosine/sine tables once per request.
- Support both the original tensor cache and the native `(cos, sin)`
cache.
  - Preserve the existing sequence-parallel slicing semantics.
- Add `qwen_image_21_npu_rms_norm` for native Q/K RMSNorm.
  - Use unit gamma in `npu_rms_norm`.
- Apply the learned scale afterward in BF16 to preserve the original
rounding boundary.
- Add a BF16 Ascend configuration enabling both optimizations.
- Enable native RoPE in the existing Ascend DMD configuration.
- Add operator and cache-slicing regression tests.
- Preserve the original implementation when the native operator is
disabled or unavailable.

## Performance

Benchmark environment:

- Device: Ascend A5 NPU
- Precision: BF16
- Resolution: 1024 × 1024
- Batch size: 1
- CFG scale: 1
- Sampling steps: 50
- Protocol: 1 warm-up run followed by 3 measured runs

`DiT/step` is calculated from the complete DiT wall time divided by 50.
It includes condition KV prefill, denoising, and scheduler updates, but
excludes VLM/VAE encoding, initial noise generation, and VAE decoding.

### Individual optimizations

| Optimization | T2I DiT/step | T2I HTTP E2E | I2I DiT/step | I2I HTTP
E2E |
| --- | ---: | ---: | ---: | ---: |
| Native NPU RoPE | 289.592 → 260.911 ms (-9.904%) | 14813.981 →
13348.741 ms (-9.891%) | 342.574 → 325.462 ms (-4.995%) | 17625.527 →
16812.481 ms (-4.613%) |
| Native NPU Q/K RMSNorm | 292.366 → 285.112 ms (-2.481%) | 14945.864 →
14547.365 ms (-2.666%) | 335.572 → 327.679 ms (-2.352%) | 17285.402 →
16877.942 ms (-2.357%) |

Each row uses its own adjacent baseline from the same benchmark session;
absolute baseline latency across different sessions should not be
compared directly.

### Combined configuration

The following same-device adjacent A/B run measures the incremental
benefit of enabling Q/K RMSNorm on top of native RoPE:

| Task | DiT/step, RoPE → RoPE + RMSNorm | Change | HTTP E2E, RoPE →
RoPE + RMSNorm | Change |
| --- | ---: | ---: | ---: | ---: |
| T2I | 256.482 → 252.584 ms | -1.520% | 13212.967 → 12945.290 ms |
-2.026% |
| I2I | 310.959 → 292.547 ms | -5.921% | 16015.293 → 15146.319 ms |
-5.426% |

## Accuracy

| Configuration | Task | SSIM | PSNR | MAE | Result |
| --- | --- | ---: | ---: | ---: | --- |
| Native NPU RoPE | T2I | 1.000000 | ∞ | 0 | Byte-identical |
| Native NPU RoPE | I2I | 1.000000 | ∞ | 0 | Byte-identical |
| RoPE + Q/K RMSNorm | T2I | 0.997181 | 48.67 dB | 0.437 | Subject and
composition preserved |
| RoPE + Q/K RMSNorm | I2I | 0.958448 | 22.95 dB | 2.730 | Subject and
composition preserved |

The combined configuration produces the same output bytes as the
RMSNorm-only configuration, confirming that native RoPE introduces no
additional numerical difference. RMSNorm is not bit-exact because of the
native kernel's numerical behavior, but the generated subject and
overall composition remain unchanged.

Repeated runs used identical initial latents and produced stable output
hashes within each configuration.

## Usage

Enable both optimizations in the Qwen-Image-2.1 model configuration:

```json
{
  "rope_type": "qwen_image_21_npu_rope",
  "rms_norm_type": "qwen_image_21_npu_rms_norm"
}
```
The native implementations are registered only for the Ascend NPU
platform. Existing non-Ascend configurations and execution paths remain
unchanged.
Verification
- Completed T2I and I2I performance and accuracy measurements on Ascend
A5.
- Passed the original 7 native RoPE and RMSNorm operator tests in the
Ascend environment.
- Added regression coverage for:
  - Original tensor RoPE cache behavior
  - Native (cos, sin) cache slicing
  - Sequence-parallel tuple-cache slicing
- Passed Ruff lint and formatting checks.
- Validated the added JSON configuration files.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Summary

* **New Features**
* Added an Ascend NPU configuration for Qwen Image 2.1 BF16 generation
at 1024 resolution with 40 inference steps.
* Added Ascend NPU support for Qwen Image 2.1 rotary embeddings and RMS
normalization, with fallback behavior when native operations are
unavailable.
* **Updates**
* Updated the Qwen Image 2.1 DMD 4-step configuration to use the
matching Ascend NPU rotary embedding.
  * Improved inference compatibility with different rotary data formats.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: YawningPants <asef2JO-bERQOuyw.YawningPants@noreply.gitcode.com>
Co-authored-by: helloyongyang <yongyang1030@163.com>

### [671fc89](https://github.com/ModelTC/LightX2V/commit/671fc893bc02766f9bd485aa7ff9dbd6a5f8acb6)

- **作者**: Du jinyang
- **时间**: 2026-11-19T05:26:34Z
- **提交信息**: add MXFP4 qat quantizer support (#1739)

Add a MXFP4 fake quantizer (fp4_e2m1 elements with E8M0 per-32-element
scales)

### [7702ec0](https://github.com/ModelTC/LightX2V/commit/7702ec0c3c553c2aa538243a3bd2993dca7cd70a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-19T04:20:20Z
- **提交信息**: update h3 readme (#1738)

### [9732be7](https://github.com/ModelTC/LightX2V/commit/9732be7a5ed69c92c2ff6c608a06f0e4629fdc2a)

- **作者**: zhengxinwei
- **时间**: 2026-11-19T03:12:55Z
- **提交信息**: fix(minimax_h3): skip undecodable packets in reference media (#1737)

Fixes #1736

## What

`_decode_reference_soundtrack` and `decode_reference_video` in
`minimax_h3/packing_ref2av.py` now decode through a small helper that
demuxes packet by packet and skips packets raising
`av.error.InvalidDataError`, logging how many were skipped. Behaviour
for clean files is unchanged; files that decode nothing still raise the
existing "contains no samples" / "No video frames" errors.

## Why

A reference MP3 made by joining two MP3 files byte for byte keeps the
second file's ID3 tag mid-stream. PyAV raises `InvalidDataError
([mp3float] Header missing)` on that single packet and the request
fails, whereas ffmpeg, players and the hosted MiniMax-H3 API drop it and
keep decoding.

## Test

With the reproduction from #1736 (`cat a.mp3 b.mp3 > joined.mp3`, 2.0 s
+ 0.5 s):

- before: `decode_reference_audio("joined.mp3")` raises
`InvalidDataError`
- after: returns ~2.5 s of audio and logs `Skipped 1 undecodable audio
packet(s) ...`

Also checked on a real user upload with the same structure (188 + 5 MP3
frames separated by an ID3 tag): decodes 4.608 s, matching `ffmpeg -f
null`. `ruff check` / `ruff format --check` clean on the changed file
(the remaining PIE810 on `__all__` predates this change).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2337
- **最后更新**: 2026-11-19T08:42:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

## 提交分析总结（批次 1/1）

### 1. 主要更新类型
**代码清理与性能微优化**——属于小型维护性提交，非功能性变更。

### 2. 关键变更点及与项目整体方向的关系
- 移除了 Wan2.1 实现中的 `torch.cuda.synchronize()` 调用。
- 该调用属于不必要的显式同步操作，移除后可减少 GPU 流水线阻塞，让 CUDA 异步执行更高效。
- 此改动由外部贡献者通过 PR (#533) 提交，说明项目社区对 Wan-Fun（即 README 中提到的 Wan2.1-Fun 系列）核心推理代码保持活跃关注。
- 项目整体方向围绕视频生成（CogVideoX-Fun、Wan-Fun）的模型开源与推理优化，此类改动属于对推理性能的持续打磨。

### 3. 对项目的影响和潜在意义
- **正面影响**：在推理批量生成或多帧输出时，减少不必要的同步等待可略微提升吞吐量。
- **风险较低**：若代码中其他逻辑已正确处理异步与同步的时序（如在数据读取前隐式同步），则删除不会引入竞态；但若在需要确定性结果的关键路径上删除，可能带来细微的行为差异。
- **象征意义**：此类小改动体现了项目从"功能堆叠"阶段逐步进入"工程打磨"阶段，重视推理链路的每一步开销。

### 4. 值得关注的技术点
- `torch.cuda.synchronize()` 用于强制 CPU 等待 GPU 完成当前所有 CUDA 操作。频繁调用会打断异步流水线，是常见的性能反模式。
- 判断是否应删除同步，需要结合上下文确认：在数据写入磁盘、返回 Python 对象、或进行计时统计等场景下，同步往往是必要的。PR 中的删除应已通过测试验证。
- 提交以 `#533` 标号形式合入，说明使用了 PR 合并流程而非直接推送，反映了较为规范的开源协作流程。

### 5. 结合项目背景对项目发展的影响
根据 README，VideoX-Fun 是阿里云 PAI 团队开源的视频生成框架，包含 CogVideoX-Fun 和 Wan-Fun 两条主线，并提供 Hugging Face Space 在线试用。此类对 Wan2.1 推理代码的微调，虽然单独看影响有限，但与项目持续优化推理性能、降低用户生成成本的长期目标一致。在多模型并行演进（CogVideoX、Wan 系列）的背景下，这类"减负"型提交有助于让代码库保持轻量与高效，也为后续更复杂的分布式推理优化奠定基础。项目正处于功能完善向性能与工程质量提升过渡的阶段。

## 详细提交记录

### [32f7582](https://github.com/aigc-apps/VideoX-Fun/commit/32f7582451c1f716e67158500de7506999a41f0b)

- **作者**: Bubbliiiing
- **时间**: 2026-11-19T02:52:13Z
- **提交信息**: Delete torch.cuda.synchronize() in Wan2.1 (#533)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6963
- **最后更新**: 2026-11-19T23:40:09Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 13
- **主要提交者**: Theodore-Liu, eigen, Akaash Parthasarathy

## AI分析总结

# FlashInfer 昨日 24 个提交分析总结

## 1. 主要更新类型
- **性能优化**（约 8 项）：QToken 稀疏注意力 group size 扩展至 16/32、batch-invariant 注意力与 GEMM 启动开销削减、MXFP8 量化内核融合 padding、GDN 局部性域解码内核、bmm_fp8 偏置融合、FP4 编译 worker 复用、SM107 状态槽优化。
- **功能新增**（约 6 项）：VC-Attention 的 QK-INT8 量化配方、Cake GDP 的 FP16 状态池、MoE 专家迁移权重暴露、batch-invariant 采样扩展到 top-k/top-p/min-p、bmm_fp8 偏置支持、SM120 FP4 GEMM 关闭 Stream-K 开关。
- **Bug 修复与工程维护**（约 10 项）：BF16 decode 特性放行 64 宽 V head、Cake GDN 对齐检查、CI 安装脚本路径、MoE warp-decode 越界专家 id 处理、MoE-EP 测试守卫、decode 元数据设备校验、Windows arm64 兼容三项、JIT 对象路径匹配等。

## 2. 关键变更点与项目方向的关系
- **新硬件覆盖**：稀疏注意力服务 NVFP4 prefill；INT8 配方与 FP16 状态池对齐 B200/B300；GDN 局部性域孪生内核面向 sm_107a（VR200），跨双 die 提升访存局部性；Rubin 部署与 SM107 优化延续 SM100/103 适配路线。
- **可复现与确定性推理**：batch-invariant 系列扩展到注意力、GEMM 与采样，保证输出只依赖行自身数据与 (seed, offset)，并将主机启动开销削减 37–60us；FP4 GEMM 新增 `FLASHINFER_FP4_GEMM_DISABLE_STREAM_K` 环境变量，校验 autotuner 缓存 tactic，解决 vLLM 复现的末位差异。
- **MoE 与下游生态**：MegaMoE 权重 getter 公开为可写别名并整合 EP2–32 测试矩阵，支持专家迁移；bmm_fp8 偏置融入 cuBLASLt epilogue，直接响应 SGLang 需求；越界专家 id 内核内处理以 0.85–1.01x 性能换取鲁棒性。

## 3. 对项目的影响与潜在意义
自动 group size 建议（误差 ≤1.04×）降低调优门槛；MXFP8 padding 融合消除两遍额外访存；bmm_fp8 偏置使 SGLang 端到端 GPU 时间从 107.3ms 降至 83.0ms；FP4 编译 worker 复用让冷缓存 warmup 缩短约一半。对齐检查、设备校验与 trait 放行修复提升了鲁棒性，减少生产环境非法内存访问风险；CI 修复恢复 15 个 nightly 测试任务，Windows arm64 修复扩大了贡献者与 CI 覆盖面。

## 4. 值得关注的技术点
- 稀疏元数据用 `ceil(G/8)` 页主序字节平面存储成员关系，配合共享内存前缀映射，是紧凑索引设计的范例。
- "延迟模型 + 硬件常数拟合"的自动调参方法可推广到其他内核选择。
- FP16 状态池用硬件 `cvt.rs` + Philox 随机舍入，在内存减半下快照行最高提速 1.46×。
- batch-invariant GEMM 通过 `_has_tune_data` 短路与 memoise dispatcher 实现零位变化的开销削减。
- epilogue 融合需同步修改 autotune 缓存 key 与 trace 定义，同时保持无偏置调用位级不变；同一 tile shape 下不同 reduction 拓扑导致的 Stream-K 数值非确定性，是 GPU autotuning 的深层陷阱。
- 编译进程池的惰性创建、嵌套上下文继承与异常退出释放，是并行编译基础设施的典型设计。

## 5. 对项目发展的整体影响
这批提交呈现三条主线同步推进：**性能上限**（kernel 融合、worker 复用、新架构孪生内核）、**生产可靠性**（可复现性开关、输入与对齐校验、CI 修复）、**生态适配**（响应 vLLM/SGLang 的专家迁移、偏置融合与可复现采样）。整体强化了 FlashInfer 作为跨架构、可生产部署的高性能推理内核库的定位，使其不仅在微基准上领先，更在真实推理服务的稳定性与部署体验上走向成熟，巩固了主流 LLM 推理引擎底层加速库的地位。

## 详细提交记录

### [8cf6cb1](https://github.com/flashinfer-ai/flashinfer/commit/8cf6cb1b1d95abc5dbf3065f0cd91a57aafbfca0)

- **作者**: Perkz Zheng
- **时间**: 2026-11-19T23:59:34Z
- **提交信息**: perf(prims-ts): QToken sparse group sizes 16 and 32 and a latency-model group policy for NVFP4 prefill (#9659)

<!-- .github/pull_request_template.md -->

## 📌 Description

Speeds up D256 Prims-TS QToken block-sparse attention with NVFP4 K/V for
packed-query (prefill) calls. Follows #9375.

- **Group sizes 16 and 32.** Groups wider than 8 queries store page
memberships in `ceil(G / 8)` page-major byte planes; queries `8p..8p+7`
use plane `p`. Validation, workspace sizing, the metadata kernels and
the Q128 KeepsMmaAb softmax read these planes.
- G16/G32 require packed queries (`qo_indptr`), K/V fragments
(`gcd(kv_block_size, page_size)`) of at most 16 tokens and the
KeepsMmaAb recipe. `plan` rejects other configurations.
- Their metadata keeps a map of the model's whole block prefix
(`max_seq_len_kv / kv_block_size`) in shared memory. `plan` and
workspace sizing reject a prefix whose map does not fit the device.
  - The membership tensor must have exactly `ceil(G / 8)` planes.
- **Group-size suggestion for NVFP4 K/V.** With `nvfp4_kv=True`,
`suggest_q_token_kv_block_sparse_group_size` returns the G in {1, 2, 4,
8, 16, 32} with the lowest modeled latency: `waves × (KV128 tiles per
work item × tile cost + item cost) + metadata + split reduction`. A
group's K/V tiles are estimated as `selected × G ** union_exponent`,
capped at `seq_len_kv`. New optional arguments: `union_exponent`,
`nvfp4_kv`, `seq_len_kv` and `packed_query`; G16/G32 are suggested only
with `packed_query=True` and `kv_block_size <= 16`. With constants
fitted on GB300, the suggested G is within 1.001× of the best explicit G
on geomean and 1.04× in the worst case. BF16/FP8 caches keep main's
coverage rule (G1–G8).
- **D256 recipe choice.** Raw BF16/FP8 caches and FP8 Q with NVFP4 K/V
take SwapsMmaAb only for groups of at most 16 Q rows per KV head (Swaps
Q32 trailed Keeps Q64 by 10–110%). Everything else keeps main's rules.
- **Grouped metadata.**
- G9–G32 use a membership-entry map, which skips the separate membership
pass, when the prefix fits without lowering occupancy; otherwise a bit
map with an optional word-rank array.
- When the warps divide the group's queries evenly, each warp enumerates
one query.
- G32 runs the bit-map kernel with 1024 threads (57 → 32 µs at 4K
queries); G2–G4 keep four 512-thread CTAs per SM.
- The packed-Q path issues the selected-block loads before route
validation.
- **NVFP4 KeepsMmaAb loader, separate scales, grouped routes.** Several
raw stages are kept in flight in registers, and the loader runs up to
one tile further ahead. G1 routes and the interleaved-row layout are
unchanged.
- **Docs.** `QTokenKvBlockSparsePagedTSWrapper.run` documents
framework-side NVFP4 → BF16 conversion (see below). No conversion code
is added.

### Performance

GB300 (SM103, 152 SMs), BF16 Q, NVFP4 K/V, D256, one request, real
sparse-indexer top-k (512 blocks of 4 tokens), page 128, causal. Prefix
0/32K/64K, 1–4096 packed queries (`qo_indptr`), `split_kv=True`. Both
trees use the group from their own
`suggest_q_token_kv_block_sparse_group_size` (with `packed_query=True`
on this PR). Times are CUDA-graph GPU spans from the metadata kernel
through the split reduction, in µs, with identical inputs (checked by
hash) on the same GPU.

Summary over the full grid (3 prefixes × 13 query counts):

| Hq/Hkv | Layout | Cases | Geomean speedup | Min | Max | Max row rel.
L2 vs FP32 |
|---|---|---:|---:|---:|---:|---:|
| 4/1 | separate scales | 39 | 1.21x | 0.99x | 2.85x | 0.0033 |
| 4/1 | interleaved rows | 39 | 1.20x | 0.99x | 2.94x | 0.0033 |
| 16/2 | separate scales | 39 | 1.13x | 0.99x | 2.33x | 0.0031 |
| 16/2 | interleaved rows | 39 | 1.12x | 0.98x | 2.39x | 0.0031 |

The only cases below 1.0x are G1 launches with at most 128 queries
(0.98–0.99x), which run the same kernel on both trees.

| Hq/Hkv | Prefix | Queries | main, separate scales | PR, separate
scales | Speedup | main, interleaved | PR, interleaved | Speedup |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 4/1 | 0 | 256 | 19.2 (G2) | 17.3 (G4) | 1.11x | 18.5 | 17.1 | 1.09x |
| 4/1 | 0 | 1024 | 69.5 (G1) | 24.4 (G16) | 2.85x | 71.2 | 24.2 | 2.94x
|
| 4/1 | 0 | 4096 | 123.6 (G8) | 68.2 (G32) | 1.81x | 119.1 | 64.6 |
1.84x |
| 4/1 | 32K | 64 | 29.5 (G4) | 26.3 (G4) | 1.12x | 29.1 | 26.3 | 1.11x |
| 4/1 | 32K | 256 | 49.7 (G4) | 35.5 (G16) | 1.40x | 48.9 | 34.7 | 1.41x
|
| 4/1 | 32K | 1024 | 198.1 (G1) | 75.1 (G16) | 2.64x | 204.1 | 73.4 |
2.78x |
| 4/1 | 32K | 4096 | 286.3 (G8) | 214.0 (G16) | 1.34x | 281.2 | 217.6 |
1.29x |
| 4/1 | 64K | 1024 | 202.0 (G1) | 75.7 (G16) | 2.67x | 206.5 | 75.3 |
2.74x |
| 4/1 | 64K | 4096 | 302.6 (G8) | 231.0 (G16) | 1.31x | 295.3 | 234.2 |
1.26x |
| 16/2 | 0 | 256 | 22.6 (G8) | 18.3 (G4) | 1.24x | 22.7 | 18.3 | 1.24x |
| 16/2 | 0 | 1024 | 41.2 (G8) | 33.5 (G16) | 1.23x | 41.2 | 32.3 | 1.27x
|
| 16/2 | 0 | 4096 | 194.5 (G8) | 155.0 (G16) | 1.25x | 191.7 | 155.7 |
1.23x |
| 16/2 | 32K | 64 | 34.6 (G8) | 30.4 (G8) | 1.14x | 34.5 | 30.4 | 1.13x
|
| 16/2 | 32K | 1024 | 166.2 (G8) | 157.9 (G8) | 1.05x | 163.6 | 159.0 |
1.03x |
| 16/2 | 32K | 4096 | 483.4 (G8) | 454.5 (G8) | 1.06x | 468.1 | 458.7 |
1.02x |
| 16/2 | 64K | 1024 | 169.3 (G8) | 159.4 (G8) | 1.06x | 164.9 | 160.2 |
1.03x |
| 16/2 | 64K | 4096 | 504.9 (G8) | 476.5 (G8) | 1.06x | 489.0 | 480.0 |
1.02x |

Single-query cases take 12–18 µs on both trees.

### No-regression check against main

Every case was compared with main on GB300 with identical inputs. main
and this PR alternate on one GPU (main, PR, main, PR), and a case counts
as a regression when the PR's best run is more than 1% slower than
main's worst. Heads 4/1, 16/2, 8/1, 2/1 and 1/1; prefix 0/32K/64K;
1–4096 packed queries with explicit G1–G8 and with the suggested G;
fixed-Q decode with 64–512 requests at 8K/32K context and G1–G8.

| K/V cache | Q | Suggested G: geomean PR/main time | Cases |
|---|---|---:|---:|
| NVFP4, separate scales and interleaved rows | BF16 | 0.85 | 312 |
| NVFP4, separate scales and interleaved rows | FP8 | 0.85 | 312 |
| BF16 | BF16 | 0.94 | 156 |
| FP8 | FP8 | 0.96 | 156 |

No case regresses. G1 launches with at most 16 queries show end-to-end
deltas of up to 1.4 µs in either direction; both trees launch the same
kernels with the same grids and the same GPU span there.

FP8 Q with NVFP4 K/V (review question): for groups of at most 16 Q rows,
Keeps vs Swaps depends on the scale layout, which `plan()` does not see.
With more work items than SMs, Keeps is 13–17% faster with separate
scale tensors but 2–12% slower with interleaved rows, and 2–5% slower
for G1 decode in both layouts. The PR therefore keeps main's FP8 rule
(Keeps from G5) and only adds the 16-row bound (Keeps Q64 was 2–26%
faster than Swaps Q32 at 32 rows in every measured case).

### When a separate NVFP4 → BF16 K/V conversion pays in prefill

The kernel dequantizes NVFP4 K/V for every route that reads a tile, so
overlapping routes repeat the work: at 4K queries over a 64K prefix,
each selected token is dequantized about 90 times. A framework can
instead convert each request's visible NVFP4 pages to a BF16 paged cache
once per call and run the wrapper with `kv_dtype=torch.bfloat16`. This
applies to BF16 Q only (FP8 Q rounds K/V to E4M3). Results are then
bit-identical, since every E2M1 × E4M3 product is exact in BF16, and
Prims-TS needs no change. Measured with a prototype on GB300 (D256, real
indexer top-k, 512 blocks of 4 tokens, 0–64K prefixes):

- **Cost:** about 13 µs per 64K tokens per KV head (about 6.4 TB/s),
plus a BF16 scratch cache of 3.6× the NVFP4 size (128 MB per request at
64K tokens × 2 KV heads).
- **Saving:** 1.45 µs per KV128 tile for TileQ128 groups (`group_size ×
Hq / Hkv > 64`) and 0.18 µs for 64-row tiles. It grows with the number
of queries, not with context length.
- **Measured speedup vs the best NVFP4 launch:** 1.02–1.37× at 1K–4K
queries, 0.84–1.11× at 512, 0.63–1.0× at 128–256.
- **Use it** for TileQ128 groups with at least 1K packed queries (512 at
8 Q heads per KV head) and contexts up to 64K.
- **Skip it** for 64-row tiles, fewer queries, memory-constrained
deployments and unmeasured long contexts (at 1M tokens × 2 KV heads,
conversion would take about 420 µs and 2 GB per request).
- **Gate fitted on 0–64K data:** convert when `(KV128 tiles / SMs) ×
per-tile saving > visible tokens × KV heads × 0.042 ns + 5 µs`, with a
per-tile saving of 1.453 µs (Q128) or 0.179 µs (Q64).
- Converting only the selected blocks does not help: marking them costs
more than it saves.
- When converting, pass `nvfp4_kv=False` to the group suggestion, and
overlap the conversion with independent work such as the indexer top-k.

## 🔍 Related Issues

Follows #9375.

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/attention/test_attention_ts_q_token_kv_block_sparse_metadata.py
tests/attention/test_attention_ts_decode.py`

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

- Tested on GB300 (SM103):
`test_attention_ts_q_token_kv_block_sparse_metadata.py` 317 passed,
`test_attention_ts_decode.py` 1207 passed and 96 skipped. The wide-group
attention test checks every query of G16/G32 routes, including a short
tail route, padded Q rows and per-KV-head patterns, against an FP32
reference for BF16 D128/D256 and NVFP4 D256 K/V, with and without
split-KV.
- The review fixes left NVFP4 latency unchanged or better on the same
GPU with identical inputs. Precomputing the membership plane stride per
CTA makes 16/2-head G16 (Q128) at prefix 0 with 2K-4K queries 4-7%
faster than the tables above, which predate it; G2–G4 metadata is also
faster now (G4 at 4K queries: 14.6 µs on main, 11.4 µs here). Other
cases are within 0.2%.
- pre-commit does not run on my machine. `ruff check`, `ruff format`
(0.15), clang-format 19.1.1 and `git diff --check` pass on the changed
files.
- The group-policy constants are relative costs fitted on GB300 (D256,
block 4, top-k 512, page 128); only their argmin matters. An explicit G
passed to `plan`/`run` is never overridden.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Sparse attention now supports packed-query groups of up to 32, with
expanded membership tracking for wide groups.
* Group-size recommendations now account for NVFP4 workloads and
additional runtime characteristics.
* Added a way to check shared-memory requirements for wide-group
metadata.
* **Bug Fixes**
* Improved handling of wide-group metadata limits, with validation to
flag configurations that exceed available capacity.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Perkz Zheng <67892460+PerkzZheng@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5ae5c80](https://github.com/flashinfer-ai/flashinfer/commit/5ae5c8086d613dabfdb88d385041346cbb04d14c)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-19T23:56:57Z
- **提交信息**: perf(batch_invariant): more Rubin placements of the batch-invariant attention class (#9726)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Placements of the batch-invariant attention class on top of #9622
(merged; it stacks on #9301 and #8590): every change keeps the class's
numeric term, so the three wrappers give the bits of upstream main for
every configuration (output dumps byte-identical to main over the decode
/ prefill / ragged grids at D = 64 / 128 / 256; the suite's invariance
tests pass unchanged); no spec, fingerprint or Lean term moves.

* **The causal mask as per-key selects (`blocks/softmax.py`, D <=
128).** The per-key `if` over a tile's scores lowered to a predicate
chain of several hundred instructions on uniform-register key sums, paid
once per causal unit (one in eight tiles of the 1K-row cells). Each key
now takes one `selp` against the row's tile-relative bounds: a select,
not an arithmetic op, so the values are the same. The two-stage body at
D = 256 keeps the per-key compare (the select form raises its register
pressure past the launch budget there).
* **Two TMEM loads in flight in the correction's epilogue
(`blocks/correction.py`).** The unit's first chunk merge and the
single-chunk copy of the merged state have both buffers free, so their
loads go out together: two round trips instead of four on the unit
boundary's chain. Same operations, same order.
* **The paired placement at D = 128 (`AttnConfig(q2=True)`, an explicit
configuration, never a default): the streamed exponential form and a 184
/ 80 / 64 register split (`blocks/operands.py`, `softmax.py`).** The MMA
warp's spills at 32 registers next to the 300 KB smem plan cost an L2
round trip per barrier step of the per-tile chain; the paired body gets
1.17-1.26x faster and stays explicit (the one-warpgroup body remains the
default at D = 128).
* **Decode launch ramp, two placements of the Swaps body
(`swaps/producer.py`, `plan.py`):** the first unit's TMA burst gated on
its first K tile (later units free-running; a static guard keeps the
gate only where four tiles fit the ring), and the page lookup started
from the descriptor's own fields when every CTA walks one unit. Both
help the one-unit-per-CTA regime (B <= 8) only.
* 
### Performance

Measured against upstream main with #9622 merged (the same kernels as
#9622's head) on Vera Rubin (sm_107, 212 SMs), bf16, page 32, cold L2,
CUPTI kernel sums including the fixup kernel, 30 iterations, two
interleaved passes, the GPU otherwise idle.

| regime | cells | main / this PR (geomean) | range |
|---|---|---|---|
| D = 128 paged prefill | 14 | 1.121 | 1.03 .. 1.30 |
| D = 128 ragged prefill | 14 | 1.097 | 1.03 .. 1.24 |
| D = 64 paged prefill | 10 | 1.152 | 1.03 .. 1.33 |
| D = 64 ragged prefill | 4 | 1.095 | 1.06 .. 1.15 |
| D = 256 paged prefill | 10 | 0.996 .. 1.001 (the mask's select form is
gated off at D = 256; the body is unchanged there) | |
| D = 128 paged decode | 28 | 1.012 | 0.99 .. 1.15 (B = 1 cells) |
| D = 64 / D = 256 paged decode | 8 / 8 | 1.013 / 1.018 | |

Against the fastest other FlashInfer backend of each cell (cute-dsl,
trtllm-gen, cuDNN): D = 128 paged prefill moves from 0.80 to 0.90,
ragged from 0.95 to 1.05, D = 64 paged prefill from 0.85 to 0.94.

## 🔍 Related Issues

<!-- Link any related issues here -->

#9009

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved batch-invariant attention performance for supported
dimensions, with faster score masking and output merging across single-
and multi-chunk workloads.
* Improved coordination of KV-page loading across attention work units,
including workloads with fewer units than available processing capacity.
* **Bug Fixes**
* Attention runs now validate that the KV page layout matches the one
used when planning. Mismatched layouts or entry counts raise a clear
error.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <34876120+Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [6c41a72](https://github.com/flashinfer-ai/flashinfer/commit/6c41a72bd7e586fd22cbc198623ac23205a0658b)

- **作者**: Harrison Zhang
- **时间**: 2026-11-19T22:50:41Z
- **提交信息**: feat(prims_ts): VC-Attention QK-INT8 for context fmha (#8551)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Adds the paper's B200 recipe to VC-Attention-QK8: the Hadamard-rotated Q
and K are quantized to INT8 with the same one scale per 128-token block
as the E4M3 recipe (`amax / 127`).

`vc_quantize_int8` and `vc_quantize_repair_int8` write INT8 codes;
`vc_quantize_fp8` and `vc_quantize_repair` keep writing E4M3. The
pre-pass kernel picks the packer from the output tensor's element type
at compile time. `VCAttentionPreprocessor` follows the device, as the
paper configures B200 (INT8) and B300 (E4M3); `vc_qk8_dtype(device)`
returns that code type.

The context kernel runs the INT8 tcgen05 MMA onto the `INT32_SCORE_BIAS`
float bias as the Sage INT8 path does; the VC row max and the ExpCast
exp2 remove the bias where they apply the per-tile and per-row scales.
The plan accepts INT8 Q/K with `vc_config` on SM100, with V defaulting
to E4M3 and the output to bf16.

## 🔍 Related Issues

<!-- Link any related issues here -->

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [X] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [X] I have installed the hooks with `pre-commit install`.
- [X] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

The QK8 rows of the VC recipe matrix run with the device's code type,
and the fused-vs-reference preparation check covers every QK8 quantizer
the GPU can run (E4M3 and INT8 on SM100). On a B200:
`tests/attention/test_attention_ts_vc.py` and
`tests/attention/test_attention_ts_context_sage.py`, 50 passed.

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/attention/test_attention_ts_vc.py
tests/attention/test_attention_ts_context_sage.py`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added INT8 Q/K support for VC-Attention on B200, including
quantization, repair preparation, and attention planning. Q/K dtype is
selected based on the device.
* INT8 Q/K plans default to E4M3 V and BF16 output, and require a Sage
or VC-Attention recipe.
* **Documentation**
* Updated attention guides to describe INT8 and E4M3 Q/K support and the
supported VC-Attention path.
* **Bug Fixes**
  * Corrected score-bias handling for INT32 scores in VC-Attention.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c07e0b8](https://github.com/flashinfer-ai/flashinfer/commit/c07e0b8d18b955520b2b6366cecf522a54891358)

- **作者**: TwoHalves
- **时间**: 2026-11-19T22:33:24Z
- **提交信息**: fix(b12x): admit 64-wide V heads in BF16 decode traits (#7180)

## 📌 Description

The generic 16-row decode family only considers one KV MMA tile. An
inherited odd-tile rule rejects that candidate when the V head is 64
wide, although the exact-plane BF16 kernel accepts this layout. Permit
that combination only for BF16 Q/K/V/output, a 16-row query tile, QK
width 64/128/192/256, V width 64, one query warp and one KV MMA tile.
Other combinations retain the existing check.

Expand the existing decode reference test across QK/V dimensions
`(64,64)`, `(128,64)`, `(192,64)`, `(256,64)`, `(128,128)` and
`(256,256)`, page sizes 64/128, and query/KV head counts 8/1 and 14/2.
On a DGX Spark (GB10, CUDA 13.0), unchanged upstream fails the sixteen
V=64 cases and passes eight controls. With the patch, all 24 satisfy the
existing maximum-error and cosine-similarity checks.

Nine additional boundary cases verify that FP16 Q/KV/output, FP8 KV,
unsupported query tiles/QK widths, and larger odd KV MMA counts remain
rejected. These cases pass against unchanged upstream; five exposed
under-gating in the first patch and all nine pass after tightening the
exception.

## 🔍 Related Issues

Fixes #6977 (the requested BF16 decode trait change).

The report's separate long-extend warmup problem remains unaddressed.
This does not establish full vLLM/model startup or CUDA-graph behavior
for head dimension 64.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.) in the declared scope:
107 passed across paged execution, trait selection, planning and
architecture lint, including the 24 numerical regression cases and nine
boundary cases. The entire repository/GPU matrix was not run.

The CUDA configuration validator also passes. All tests and CI checks
above ran on the Spark, using PyTorch 2.13.0+cu130 and Cutlass DSL
4.7.1. The numerical regression file is byte-identical in its upstream
failing and final passing runs.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it changes code under
`flashinfer/experimental/`. Tracking issue: #6909 (this PR repairs the
existing b12x backend; the defect is #6977).
- [ ] The tracking issue names an owner, the reason for the experimental
path, and a graduation plan with a target release. #6909 names the owner
and the reason and sets a graduation review (2026-11-17); no target
release is assigned yet.
- [x] Core changes are limited to a thin entry point. No core files
change.
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable example is included below.
- [x] Nothing is registered in `flashinfer/aot.py`, and no automatic
backend-selection behavior changes.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/b12x/attention/test_paged.py
tests/experimental/b12x/attention/test_attention_paged_traits.py
tests/experimental/b12x/attention/test_attention_paged_planner.py
tests/experimental/b12x/lint/test_arch_flags.py
```

## Reviewer Notes

From the checkout, with the b12x dependencies available, the small
reproducer is:

```sh
export PYTHONPATH=.:flashinfer/experimental/b12x/_compat
python - <<'PY'
import torch
from b12x.attention.paged.traits import select_paged_forward_traits
traits = select_paged_forward_traits(
    cta_tile_q=16, head_dim_qk=64, head_dim_vo=64,
    q_dtype=torch.bfloat16, kv_dtype=torch.bfloat16,
)
assert traits.num_mma_kv == 1
print("head_dim=64: one KV MMA tile, selection passed")
PY
```

The recorded test commands use `--confcutdir=tests/experimental/b12x` to
isolate this backend from the repository-root integration conftest. A
full FlashInfer extension installation was not used. No model was
downloaded or run.

Prepared with AI assistance; reproduced and tested locally. The
failing-then-passing test is included.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* BF16 paged-attention decode now supports single-query-warp
configurations with one KV MMA when the query/key dimensions are 64,
128, 192, or 256 and the value dimension is 64.
* **Bug Fixes**
* Unsupported paged-attention configurations are rejected with a clear
indication that no valid KV MMA configuration is available.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e19164c](https://github.com/flashinfer-ai/flashinfer/commit/e19164cba52bd313bd78016c2abb954b2db78670)

- **作者**: Aditya Kane
- **时间**: 2026-11-19T20:02:21Z
- **提交信息**: Optionally fuse padding in MXFP8 quantize kernel (#9429)

<!-- .github/pull_request_template.md -->

## 📌 Description

`mxfp8_quantize(..., backend="cute-dsl")` with the linear scale layout
pads K up to `alignment` on the host: it allocates `torch.zeros(m,
padded_k)`, copies the input into it, and quantizes the padded copy.
That is two extra passes over the activations (a memset and a copy) for
columns that only ever become zeros. This shows up wherever a hidden
size is padded for a block-scaled GEMM. For example, vLLM's gpt-oss MoE
backend that runs FlashInfer's TRT-LLM kernels with MXFP8 activations
(`FLASHINFER_TRTLLM_MXFP4_MXFP8`) quantizes the MoE input through this
path with the linear layout and `alignment=256`, padding the 2880-wide
hidden states to 3072 in every MoE layer.

This PR moves the padding into `MXFP8QuantizeLinearKernel`, which now
reads the unpadded `[M, K]` input and writes the padded `[M, padded_K]`
output and scales itself:

- When `K < padded_K`, 15 of the CTA's 16 warps quantize the input's
scale blocks; the last warp writes the zero FP8 columns `[K, padded_K)`
(8-byte stores) and the zero scale bytes of every row its CTA owns. The
block keeps its 512 threads.
- An all-zero 32-element block quantizes to FP8 zero with scale 0, so
the output is byte-identical to quantizing the zero-padded copy.
- Scales are indexed per output row (`row * padded_K/32 + col`) instead
of by the flat block index.
- The kernel is compiled per `(K, dtype, pdl, use_2t, padded_K)`. When
`K == padded_K` it is the same kernel as before. Swizzled layouts
(128x4, 8x4) are unchanged and still pad on the host.
- No new input constraints: K and `alignment` must already be multiples
of 32, which keeps the 8-byte zero stores aligned.

A second commit fixes `benchmarks/routines/quantization.py` so the
`mxfp8_quantize` routine can measure this case. It required `k %
alignment == 0` (treating `--alignment` as the scale vector size), so
any K that `mxfp8_quantize` would pad was rejected. It now checks K and
`--alignment` against 32, compares only the first K columns in
`--refcheck`, and counts the padded output bytes in the bandwidth
figure.

### Performance

B200, bf16 input, linear scale layout, PDL off. Median of 3 runs per
tree, alternating, on the same GPU.

`python benchmarks/flashinfer_benchmark.py --routine mxfp8_quantize --m
<M> --k <K> --alignment <A> --no_sf_swizzled_layout --backends cute-dsl
--input_dtype bfloat16 --num_iters 1000 --dry_run_iters 100`

This times the whole call, including the host-side pad on main, in a
CUDA graph with rotating input buffers (cold L2), using CUDA events
(`cupti-python` was not installed). "main" is main plus only the
benchmark fix, since main's routine rejects these shapes. The `cuda`
backend column is for reference; this PR does not touch it.

`alignment=128`:

| M | K → padded K | main, cute-dsl (µs) | this PR, cute-dsl (µs) |
speedup | cuda backend (µs) |
|---:|---|---:|---:|---:|---:|
| 1 | 2880 → 2944 | 3.85 | 1.80 | 2.1x | 2.82 |
| 8 | 2880 → 2944 | 4.66 | 1.80 | 2.6x | 3.02 |
| 64 | 2880 → 2944 | 5.07 | 1.80 | 2.8x | 3.03 |
| 512 | 2880 → 2944 | 7.74 | 2.62 | 3.0x | 3.44 |
| 2048 | 2880 → 2944 | 22.29 | 4.87 | 4.6x | 5.90 |
| 8192 | 2880 → 2944 | 77.17 | 13.27 | 5.8x | 18.60 |
| 2048 | 1568 → 1664 | 12.46 | 3.22 | 3.9x | 4.65 |
| 2048 | 4000 → 4096 | 29.25 | 6.09 | 4.8x | 6.52 |

`alignment=256`, as in the vLLM path above (K = 2880 → 3072):

| M | main, cute-dsl (µs) | this PR, cute-dsl (µs) | speedup | cuda
backend (µs) |
|---:|---:|---:|---:|---:|
| 1 | 3.64 | 1.80 | 2.0x | 2.82 |
| 8 | 4.67 | 1.80 | 2.6x | 3.03 |
| 64 | 4.87 | 1.80 | 2.7x | 3.03 |
| 512 | 7.74 | 2.62 | 3.0x | 3.44 |
| 2048 | 22.47 | 4.85 | 4.6x | 5.90 |
| 8192 | 78.60 | 13.27 | 5.9x | 17.77 |

Before this PR the padded cute-dsl path was slower than the `cuda`
backend at every shape in both tables; with it, it is faster at every
one. Calls whose K is already a multiple of `alignment` run the same
kernel as before.

### Testing

- New
`tests/utils/test_fp8_quantize.py::test_mxfp8_quantize_cute_dsl_linear_pads_in_kernel`:
180 cases (M = 1, 3, 127, 1024, 8192; K/alignment = 2880/128, 2880/256,
96/128, 32/256, 1056/1024, 4064/4096; fp16/bf16/fp32; PDL on/off). Each
compares the output byte for byte, padding included, with quantizing an
explicitly zero-padded input, after poisoning the caching allocator with
0xFF so unwritten padding would show. With the zero-fill warp disabled,
all 180 fail.
- The existing `test_mxfp8_quantize_alignment_torch_device` (linear and
swizzled, K = 1568, alignment 64 and 128) exercises this path as well.
- On B200, `pytest tests/utils/test_fp8_quantize.py
tests/utils/test_mxfp8_dispatch.py`: 1290 passed, 185 skipped, 0 failed.
`flashinfer_benchmark.py --refcheck` on the padded shapes (K = 2880 and
1568 at alignment 128, K = 2880 at alignment 256) finds 0 mismatched
elements for both the `cuda` and `cute-dsl` backends.

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/utils/test_fp8_quantize.py
tests/utils/test_mxfp8_dispatch.py`

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

- The kernel change is confined to the `has_pad` branches in
`MXFP8QuantizeLinearKernel` (the warp split, the zero-fill loop) and the
scale index; with `K == padded_K` the generated kernel is unchanged.
- Each CTA's zero-fill warp covers rows `bidx, bidx + gridDim.x, ...`,
so every row's padding is written exactly once across the grid. The
padding bytes and the quantized blocks never overlap, so it does not
matter which CTA quantized a row's blocks.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MXFP8 quantization can produce output padded to a requested width
alignment. Padded output columns and their scale values are set to zero.
* **Bug Fixes**
* Quantization round-trip checks now exclude padded columns when
comparing results.
* Benchmark bandwidth estimates account for padded output elements and
scale values. Benchmark inputs now require both width and alignment to
be divisible by 32, and widths are padded to the requested alignment.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d3f59f0](https://github.com/flashinfer-ai/flashinfer/commit/d3f59f09106185147e2d0d09ac9dc6452f6712b0)

- **作者**: eigen
- **时间**: 2026-11-19T16:54:39Z
- **提交信息**: fix(cake_gdn): reject unaligned inputs in the pretranspose decode (#9725)

The Cake pretranspose decode kernels read q and k in up to 16-byte vectors
(8-byte with an FP32 state), read v and write the output in 8-byte vectors
on some rows, and move the state and the checkpoint buffer in up to 16-byte
copies. No host check looked at a base address, so a contiguous view at an
unaligned storage offset passed every check and would fault asynchronously
("misaligned address"). The BF16 rows and the FP32 MTP rows also add the
q/k/v strides and the pool's slot (and FP32 head) strides to those vector
addresses, so a view whose strides break the alignment would fault the same
way.

_run_cake_gdn_decode_pretranspose now checks both after its contract checks
and before the slot checks, the resolver and the loader, for every row and
architecture:

- q and k must start 16-byte aligned with a BF16 state (8-byte with an FP32
  state), v and the output 8-byte aligned, and the state pool and the
  checkpoint buffer 16-byte aligned. A miss raises ValueError, under
  backend="auto" as under "cake_gdn": the FlashInfer kernels that "auto"
  falls back to assume 16-byte (FP32 state) or 32-byte (BF16 state) aligned
  bases and refuse a misaligned one at launch.
- Every q/k/v/state stride of a dimension longer than 1 must be a whole
  number of those vectors. A miss raises CakeGDNUnsupportedError: these
  kernels do not serve that layout, and the FlashInfer kernels accept such
  strides (as runtime strides or by compiling for them), so "auto" falls
  back and "cake_gdn" fails closed.

a, b, A_log, dt_bias and the slot indices are read one element at a time and
need only their element alignment. The API docs and the public docstring
state the requirements.

On Rubin, "auto" sends a T=1 BF16-state call with B * HV >= 512 that falls
back to the Rubin-tuned kernel. That kernel compiles a strided pool with its
strides baked into 16-byte state copies, and it failed to build for a pool
whose slot or head stride is not a multiple of 8 elements. "auto" now checks
every pool stride except the last (slot, head and row) and keeps the generic
kernel (the same bits) unless all of them are multiples of 8 elements,
instead of raising at compile time.

Tests: host-only tests with fake CUDA tensors check, for the direct helper,
"auto" and "cake_gdn", that each misaligned tensor raises ValueError before
any slot check, resolve, load, launch or fallback, on
sm_100a/sm_103a/sm_107a (after an aligned call launched once) and SM90, and
that on the first three each alignment-breaking stride raises
CakeGDNUnsupportedError or falls back once with the same tensors, while
production layouts (fused QKV, packed gates, padded pools) launch. GPU tests
check that misaligned views are refused before the row resolves with the
state, output and checkpoint untouched and that the aligned call then
matches the reference recurrence, and, in a child process, that "auto" on an
alignment-breaking view gives the bits that "flashinfer" gives on a
contiguous copy, for each FlashInfer kernel such a view can fall back to
(BF16 T=1, including the wide and the Rubin kernels, BF16 MTP and FP32 MTP).
A host-only test checks that "auto" on sm_107a takes the Rubin kernel for
pools whose slot, head and row strides are multiples of 8 elements (also
with slots 8 elements past a whole number of heads) and the generic kernel
when only the slot, only the head or only the row stride is not.

### [31b17a4](https://github.com/flashinfer-ai/flashinfer/commit/31b17a4740af9f0b597c335c576748ce2bfa40a7)

- **作者**: Cindy Zhang
- **时间**: 2026-11-19T15:38:03Z
- **提交信息**: fix(ci): resolve CUTLASS DSL setup from the checkout root (#9688)

Account for the installer moving into scripts/infra so nightly shards
running outside the checkout import the source build helper and its CI
configuration. Add a CPU regression test that runs the installer from an
isolated directory without installing dependencies.
<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
Fix nightly package tests failing during environment setup after #8993
moved `install_cutlass_dsl.sh` into `scripts/infra/`.

The script still walked up one directory to locate the repository root,
resolving to `/workspace/scripts` instead of `/workspace`. Running from
the checkout root masked the error. Once nightly switched to its
isolated test directory, Python imported the installed `build_utils.py`,
which could not find its relative `ci/cuda-versions.json`.

This caused all 15 nightly package-test jobs across CUDA 12.9, 13.0, and
13.4 to fail before pytest started.

  This PR:
  - Corrects the repository-root calculation to walk up two directories.
- Adds a CPU regression test that runs the real installer from outside
the checkout, with a simulated installed helper lacking the CI
configuration. Package installation is stubbed to avoid changing the
test environment.

## 🔍 Related Issues

<!-- Link any related issues here -->
Fix https://github.com/flashinfer-ai/flashinfer/issues/9686
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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Reason: The change corrects a CI helper path. Focused CPU regression
coverage and validation through the nightly package-test path are
appropriate.

  Validation:
- Before the fix, the new regression test reproduces `FileNotFoundError:
.../site-packages/ci/cuda-versions.json`.
- After the fix, the regression test and existing nightly
package-validation tests pass: **7 passed**.
- Changed-file pre-commit hooks, `bash -n`, and `git diff --check` pass.
- The full GPU nightly matrix has not been rerun. All 15 original
failures occur before pytest starts, so downstream GPU test results
remain unverified.

Command:
```
      python3 -m pytest --confcutdir=tests/cpu \
        tests/cpu/infra/test_install_cutlass_dsl.py \
        tests/cpu/infra/test_validate_nightly_packages.py -q
```
  Suggested CI test targets:
`tests/cpu/infra/test_install_cutlass_dsl.py
tests/cpu/infra/test_validate_nightly_packages.py`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* The CUTLASS DSL installer now works when launched from outside the
repository checkout. Its dependency installation and version
verification behavior remain unchanged.
* **Tests**
* Added automated checks for running the installer outside the checkout,
confirming successful completion, the expected CUDA 13 package
selection, and the reported CuTe DSL version.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a75cd12](https://github.com/flashinfer-ai/flashinfer/commit/a75cd12eaa8fb138f71d9d44d5151749cf699217)

- **作者**: eigen
- **时间**: 2026-11-19T14:07:32Z
- **提交信息**: feat(cake_gdp): FP16 state pool with stochastic rounding for the decode routes on SM100 and SM103 (#9720)

The Cake Gated DeltaProduct (GDP) kernel family has four decode routes,
`decode_nh1` to `decode_nh4`, one for each number of Householder updates
per token (n = 1, 2, 3 and 4). All four routes use head sizes K = 128
and V = 64 and fused q/k L2 normalization. On SM90 the family also has
chunked varlen prefill programs. The recurrent state pool now comes in
two data types. FP32 is available on all three targets. FP16 is
available on SM100 and SM103, and it stores with either round to nearest
even or stochastic rounding.

This PR adds the FP16 state pool. It adds an FP16 twin for each of the
21 decode programs the family ships on SM100 and SM103 (42 libraries for
`sm_100a` and `sm_103a`). An FP16 call launches the FP16 twin of the
program an FP32 call would launch, with the same routes and the same
bands. The recurrence runs in FP32. The kernel reads the state from FP16
and rounds every store to FP16. This halves the pool's memory and the
state bytes a decode step reads and writes.
`cake_gated_delta_product_mtp` / `flashinfer.cake_gdp` take two new
trailing keywords. With the default `rand_seed=None`, stores round to
nearest even. If `rand_seed` is a one-element int64 CUDA tensor, stores
round stochastically with the hardware `cvt.rs` instruction and
Philox-4x32 random bits. `philox_rounds=10` accepts 5 to 16.

The baseline is the previous Cake version: the same decode call over an
FP32 state pool on FlashInfer main. Speedup is FP32 time / FP16 time, so
a value above 1 means the FP16 pool is faster. With default stochastic
rounding, the geomean is 0.954x (B200) and 0.961x (GB300) on final-state
rows. On per-token snapshot rows it is 1.171x and 1.189x. With round to
nearest even, the same figures are 1.077x / 1.083x and 1.442x / 1.458x.

The other Cake GDP variants, the FP32 state pool on all three targets
and the SM90 chunked varlen prefill programs, are unchanged; the FP16
pool is SM100 and SM103 only, and the family ships on `sm_90a`,
`sm_100a` and `sm_103a`.

Three FP16 arms were measured: stochastic rounding with 10 rounds (R10,
the default), stochastic rounding with 5 rounds (R5), and round to
nearest even (RNE). Each row is the median kernel time (CUPTI, cold L2).
Both sides ran on the same GPU in one process with CUDA 13.4. Results
are pooled over two runs with reversed row order. Each GPU has three row
sets:

- Final-state (144 rows): heads 80, 24, 20, 10 x batch 1, 16, 64, 256 x
T 1, 2, 3, 4, 5, 6, 7, 8, 16, storing the final state only.
- Snapshot (64 rows): the same heads x batch at T 2, 4, 8, 16, storing
every token's state.
- Runtime snapshot (12 rows): T 10 and 12 (the runtime-token-count
program) x batch 16, 64, 256 x heads 80, 20, storing every token's
state.

Geomean per GPU (min..max; rows below 1):

- B200 (`sm_100a`) final-state: R10 0.954x (0.814x..1.165x; 129 of 144),
R5 1.011x (0.909x..1.392x; 70), RNE 1.077x (0.994x..1.542x; 4).
- B200 snapshot: R10 1.171x (0.883x..1.576x; 15 of 64), R5 1.268x, RNE
1.442x.
- B200 runtime snapshot: R10 1.422x (1.274x..1.486x), R5 1.663x, RNE
1.936x.
- GB300 (`sm_103a`) final-state: R10 0.961x (0.833x..1.240x; 126 of
144), R5 1.018x (0.924x..1.479x; 56), RNE 1.083x (0.971x..1.624x; 6).
- GB300 snapshot: R10 1.189x (0.905x..1.605x; 15 of 64), R5 1.283x, RNE
1.458x.
- GB300 runtime snapshot: R10 1.446x (1.292x..1.490x), R5 1.691x, RNE
1.962x.

R10 is slower than FP32 on most final-state rows, down to 0.814x on B200
and 0.833x on GB300. The cost comes from the Philox draws. R5 is near
parity on those rows but still below 1 on 70 rows (B200) and 56 rows
(GB300), down to 0.909x and 0.924x. RNE is below 1 on 4 and 6 rows, down
to 0.994x and 0.971x. R10 is faster on large T = 1 rows. For example,
GB300 at T 1, heads 80, batch 256 goes from 194.11 us to 156.51 us
(1.240x). On snapshot rows, R10 is slower on 15 of 64 rows per GPU, down
to 0.883x (B200) and 0.905x (GB300).

Per-row median kernel times (microseconds) follow, one table per GPU and
row set.

<details>
<summary>NVIDIA B200, SM100 (sm_100a, 148 SMs), CUDA 13.4: owner rows
(final state only), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 80 | 1 | 3.94 | 4.51 | 0.872x | 4.16 | 0.946x | 3.74 | 1.051x |
| 1 | 80 | 16 | 13.62 | 14.46 | 0.941x | 12.80 | 1.064x | 11.01 | 1.237x
|
| 1 | 80 | 64 | 49.28 | 45.98 | 1.072x | 40.29 | 1.223x | 33.54 | 1.469x
|
| 1 | 80 | 256 | 200.21 | 171.84 | 1.165x | 143.87 | 1.392x | 129.85 |
1.542x |
| 1 | 24 | 1 | 3.39 | 3.81 | 0.891x | 3.65 | 0.930x | 3.23 | 1.050x |
| 1 | 24 | 16 | 6.94 | 6.75 | 1.028x | 6.18 | 1.124x | 5.54 | 1.254x |
| 1 | 24 | 64 | 15.68 | 16.70 | 0.939x | 14.72 | 1.065x | 12.61 | 1.244x
|
| 1 | 24 | 256 | 59.26 | 54.50 | 1.087x | 47.87 | 1.238x | 40.38 |
1.467x |
| 1 | 20 | 1 | 3.36 | 3.78 | 0.890x | 3.62 | 0.929x | 3.23 | 1.040x |
| 1 | 20 | 16 | 6.62 | 6.46 | 1.025x | 5.89 | 1.125x | 5.25 | 1.262x |
| 1 | 20 | 64 | 13.73 | 14.50 | 0.947x | 12.90 | 1.065x | 11.06 | 1.242x
|
| 1 | 20 | 256 | 49.22 | 46.40 | 1.061x | 40.67 | 1.210x | 34.11 |
1.443x |
| 1 | 10 | 1 | 3.20 | 3.55 | 0.901x | 3.46 | 0.926x | 3.07 | 1.042x |
| 1 | 10 | 16 | 4.77 | 5.86 | 0.814x | 5.25 | 0.909x | 4.67 | 1.021x |
| 1 | 10 | 64 | 8.90 | 9.34 | 0.952x | 8.45 | 1.053x | 7.33 | 1.214x |
| 1 | 10 | 256 | 24.10 | 25.12 | 0.959x | 22.02 | 1.094x | 18.59 |
1.296x |
| 2 | 80 | 1 | 5.28 | 5.79 | 0.912x | 5.50 | 0.959x | 5.15 | 1.025x |
| 2 | 80 | 16 | 19.26 | 20.19 | 0.954x | 18.37 | 1.049x | 16.58 | 1.162x
|
| 2 | 80 | 64 | 61.34 | 65.66 | 0.934x | 60.21 | 1.019x | 54.53 | 1.125x
|
| 2 | 80 | 256 | 228.93 | 245.98 | 0.931x | 225.09 | 1.017x | 202.94 |
1.128x |
| 2 | 24 | 1 | 5.09 | 5.70 | 0.893x | 5.41 | 0.941x | 5.06 | 1.006x |
| 2 | 24 | 16 | 8.51 | 8.77 | 0.971x | 8.13 | 1.047x | 7.49 | 1.137x |
| 2 | 24 | 64 | 22.21 | 23.42 | 0.948x | 21.41 | 1.037x | 19.42 | 1.143x
|
| 2 | 24 | 256 | 72.96 | 78.78 | 0.926x | 72.03 | 1.013x | 65.02 |
1.122x |
| 2 | 20 | 1 | 5.05 | 5.63 | 0.898x | 5.34 | 0.946x | 4.99 | 1.013x |
| 2 | 20 | 16 | 8.22 | 8.61 | 0.955x | 7.97 | 1.032x | 7.30 | 1.127x |
| 2 | 20 | 64 | 19.33 | 20.22 | 0.956x | 18.40 | 1.050x | 16.64 | 1.162x
|
| 2 | 20 | 256 | 61.60 | 66.37 | 0.928x | 60.54 | 1.017x | 54.75 |
1.125x |
| 2 | 10 | 1 | 4.96 | 5.54 | 0.896x | 5.25 | 0.945x | 4.96 | 1.000x |
| 2 | 10 | 16 | 6.50 | 6.94 | 0.935x | 6.50 | 1.000x | 6.02 | 1.080x |
| 2 | 10 | 64 | 12.70 | 13.02 | 0.975x | 12.00 | 1.059x | 10.82 | 1.175x
|
| 2 | 10 | 256 | 33.18 | 35.87 | 0.925x | 32.70 | 1.015x | 29.60 |
1.121x |
| 3 | 80 | 1 | 5.81 | 6.18 | 0.940x | 5.89 | 0.986x | 5.54 | 1.049x |
| 3 | 80 | 16 | 22.37 | 23.26 | 0.961x | 21.50 | 1.040x | 19.87 | 1.126x
|
| 3 | 80 | 64 | 72.19 | 77.79 | 0.928x | 71.71 | 1.007x | 66.59 | 1.084x
|
| 3 | 80 | 256 | 267.09 | 290.08 | 0.921x | 268.26 | 0.996x | 248.86 |
1.073x |
| 3 | 24 | 1 | 5.54 | 6.01 | 0.920x | 5.70 | 0.972x | 5.38 | 1.030x |
| 3 | 24 | 16 | 9.95 | 10.05 | 0.990x | 9.44 | 1.054x | 8.77 | 1.135x |
| 3 | 24 | 64 | 25.95 | 27.28 | 0.951x | 25.22 | 1.029x | 23.33 | 1.112x
|
| 3 | 24 | 256 | 85.38 | 92.22 | 0.926x | 85.06 | 1.004x | 78.94 |
1.081x |
| 3 | 20 | 1 | 5.73 | 6.11 | 0.937x | 5.82 | 0.983x | 5.50 | 1.041x |
| 3 | 20 | 16 | 9.71 | 9.92 | 0.979x | 9.28 | 1.047x | 8.64 | 1.124x |
| 3 | 20 | 64 | 22.34 | 23.20 | 0.963x | 21.50 | 1.039x | 19.87 | 1.124x
|
| 3 | 20 | 256 | 72.00 | 77.54 | 0.929x | 71.58 | 1.006x | 66.43 |
1.084x |
| 3 | 10 | 1 | 5.57 | 5.98 | 0.930x | 5.70 | 0.978x | 5.38 | 1.036x |
| 3 | 10 | 16 | 7.33 | 7.68 | 0.954x | 7.23 | 1.013x | 6.78 | 1.080x |
| 3 | 10 | 64 | 14.46 | 14.50 | 0.998x | 13.44 | 1.076x | 12.48 | 1.159x
|
| 3 | 10 | 256 | 39.17 | 41.86 | 0.936x | 38.56 | 1.016x | 35.68 |
1.098x |
| 4 | 80 | 1 | 5.89 | 6.37 | 0.925x | 6.08 | 0.968x | 5.73 | 1.028x |
| 4 | 80 | 16 | 24.61 | 26.40 | 0.932x | 24.67 | 0.997x | 23.04 | 1.068x
|
| 4 | 80 | 64 | 82.02 | 89.47 | 0.917x | 83.46 | 0.983x | 78.21 | 1.049x
|
| 4 | 80 | 256 | 304.51 | 333.57 | 0.913x | 310.88 | 0.980x | 293.15 |
1.039x |
| 4 | 24 | 1 | 5.63 | 6.24 | 0.903x | 5.95 | 0.946x | 5.63 | 1.000x |
| 4 | 24 | 16 | 11.01 | 11.49 | 0.958x | 10.82 | 1.018x | 10.18 | 1.082x
|
| 4 | 24 | 64 | 28.70 | 31.04 | 0.925x | 28.96 | 0.991x | 27.04 | 1.062x
|
| 4 | 24 | 256 | 97.02 | 106.08 | 0.915x | 99.01 | 0.980x | 93.28 |
1.040x |
| 4 | 20 | 1 | 5.66 | 6.21 | 0.912x | 5.95 | 0.952x | 5.63 | 1.006x |
| 4 | 20 | 16 | 10.72 | 11.20 | 0.957x | 10.59 | 1.012x | 9.95 | 1.077x
|
| 4 | 20 | 64 | 24.51 | 26.37 | 0.930x | 24.67 | 0.994x | 23.07 | 1.062x
|
| 4 | 20 | 256 | 81.90 | 89.41 | 0.916x | 83.39 | 0.982x | 78.50 |
1.043x |
| 4 | 10 | 1 | 5.60 | 6.21 | 0.902x | 5.90 | 0.949x | 5.54 | 1.011x |
| 4 | 10 | 16 | 8.03 | 8.48 | 0.947x | 8.03 | 1.000x | 7.62 | 1.055x |
| 4 | 10 | 64 | 15.20 | 16.13 | 0.943x | 15.10 | 1.006x | 14.05 | 1.082x
|
| 4 | 10 | 256 | 44.19 | 48.06 | 0.919x | 44.90 | 0.984x | 42.08 |
1.050x |
| 5 | 80 | 1 | 7.07 | 7.26 | 0.973x | 6.94 | 1.018x | 6.66 | 1.062x |
| 5 | 80 | 16 | 30.69 | 32.06 | 0.957x | 30.27 | 1.014x | 28.56 | 1.074x
|
| 5 | 80 | 64 | 102.75 | 110.18 | 0.933x | 103.49 | 0.993x | 97.28 |
1.056x |
| 5 | 80 | 256 | 384.16 | 414.46 | 0.927x | 389.02 | 0.987x | 365.33 |
1.052x |
| 5 | 24 | 1 | 6.78 | 7.10 | 0.955x | 6.82 | 0.995x | 6.50 | 1.044x |
| 5 | 24 | 16 | 13.25 | 13.34 | 0.993x | 12.70 | 1.043x | 12.13 | 1.092x
|
| 5 | 24 | 64 | 35.81 | 37.79 | 0.948x | 35.62 | 1.005x | 33.54 | 1.068x
|
| 5 | 24 | 256 | 121.95 | 130.85 | 0.932x | 123.01 | 0.991x | 115.50 |
1.056x |
| 5 | 20 | 1 | 6.77 | 7.07 | 0.957x | 6.78 | 0.998x | 6.46 | 1.047x |
| 5 | 20 | 16 | 12.96 | 13.18 | 0.983x | 12.54 | 1.033x | 11.90 | 1.089x
|
| 5 | 20 | 64 | 30.70 | 32.06 | 0.958x | 30.27 | 1.014x | 28.54 | 1.076x
|
| 5 | 20 | 256 | 102.75 | 110.24 | 0.932x | 103.61 | 0.992x | 97.28 |
1.056x |
| 5 | 10 | 1 | 6.75 | 7.04 | 0.959x | 6.75 | 1.000x | 6.43 | 1.050x |
| 5 | 10 | 16 | 9.73 | 10.14 | 0.959x | 9.60 | 1.013x | 9.12 | 1.067x |
| 5 | 10 | 64 | 19.31 | 19.68 | 0.981x | 18.69 | 1.033x | 17.70 | 1.091x
|
| 5 | 10 | 256 | 55.13 | 58.94 | 0.935x | 55.44 | 0.995x | 52.10 |
1.058x |
| 6 | 80 | 1 | 7.46 | 7.87 | 0.947x | 7.55 | 0.987x | 7.26 | 1.026x |
| 6 | 80 | 16 | 35.68 | 35.90 | 0.994x | 34.18 | 1.044x | 32.41 | 1.101x
|
| 6 | 80 | 64 | 118.43 | 124.06 | 0.955x | 117.70 | 1.006x | 111.14 |
1.066x |
| 6 | 80 | 256 | 444.96 | 470.14 | 0.946x | 445.28 | 0.999x | 419.65 |
1.060x |
| 6 | 24 | 1 | 7.23 | 7.68 | 0.942x | 7.39 | 0.978x | 7.10 | 1.018x |
| 6 | 24 | 16 | 15.02 | 14.94 | 1.005x | 14.30 | 1.050x | 13.73 | 1.094x
|
| 6 | 24 | 64 | 41.98 | 42.72 | 0.983x | 40.61 | 1.034x | 38.50 | 1.091x
|
| 6 | 24 | 256 | 140.30 | 147.36 | 0.952x | 139.65 | 1.005x | 131.81 |
1.064x |
| 6 | 20 | 1 | 7.20 | 7.65 | 0.941x | 7.36 | 0.978x | 7.04 | 1.023x |
| 6 | 20 | 16 | 14.82 | 14.82 | 1.000x | 14.18 | 1.045x | 13.57 | 1.092x
|
| 6 | 20 | 64 | 35.71 | 35.97 | 0.993x | 34.18 | 1.045x | 32.38 | 1.103x
|
| 6 | 20 | 256 | 118.77 | 124.48 | 0.954x | 118.05 | 1.006x | 111.55 |
1.065x |
| 6 | 10 | 1 | 7.14 | 7.62 | 0.937x | 7.33 | 0.974x | 7.01 | 1.018x |
| 6 | 10 | 16 | 10.56 | 11.20 | 0.943x | 10.67 | 0.990x | 10.21 | 1.034x
|
| 6 | 10 | 64 | 22.37 | 21.86 | 1.024x | 20.80 | 1.075x | 19.78 | 1.131x
|
| 6 | 10 | 256 | 64.19 | 66.59 | 0.964x | 63.14 | 1.017x | 59.71 |
1.075x |
| 7 | 80 | 1 | 8.06 | 8.42 | 0.958x | 8.14 | 0.990x | 7.84 | 1.029x |
| 7 | 80 | 16 | 38.98 | 40.19 | 0.970x | 38.46 | 1.013x | 36.64 | 1.064x
|
| 7 | 80 | 64 | 130.66 | 138.70 | 0.942x | 132.25 | 0.988x | 125.79 |
1.039x |
| 7 | 80 | 256 | 490.37 | 523.73 | 0.936x | 498.46 | 0.984x | 473.37 |
1.036x |
| 7 | 24 | 1 | 7.71 | 8.19 | 0.941x | 7.87 | 0.980x | 7.62 | 1.013x |
| 7 | 24 | 16 | 16.29 | 16.22 | 1.004x | 15.62 | 1.043x | 15.01 | 1.085x
|
| 7 | 24 | 64 | 45.86 | 47.42 | 0.967x | 45.28 | 1.013x | 43.15 | 1.063x
|
| 7 | 24 | 256 | 155.23 | 164.70 | 0.942x | 156.93 | 0.989x | 149.18 |
1.041x |
| 7 | 20 | 1 | 7.74 | 8.19 | 0.945x | 7.90 | 0.980x | 7.62 | 1.017x |
| 7 | 20 | 16 | 16.19 | 15.94 | 1.016x | 15.36 | 1.054x | 14.72 | 1.100x
|
| 7 | 20 | 64 | 39.01 | 39.97 | 0.976x | 38.21 | 1.021x | 36.38 | 1.072x
|
| 7 | 20 | 256 | 130.74 | 138.27 | 0.946x | 131.90 | 0.991x | 125.50 |
1.042x |
| 7 | 10 | 1 | 7.74 | 8.21 | 0.943x | 7.90 | 0.980x | 7.62 | 1.017x |
| 7 | 10 | 16 | 11.58 | 12.29 | 0.943x | 11.74 | 0.986x | 11.30 | 1.025x
|
| 7 | 10 | 64 | 24.38 | 24.32 | 1.003x | 23.26 | 1.048x | 22.21 | 1.098x
|
| 7 | 10 | 256 | 70.85 | 74.24 | 0.954x | 70.85 | 1.000x | 67.42 |
1.051x |
| 8 | 80 | 1 | 8.03 | 8.35 | 0.962x | 8.06 | 0.996x | 7.74 | 1.037x |
| 8 | 80 | 16 | 42.43 | 43.52 | 0.975x | 41.73 | 1.017x | 40.00 | 1.061x
|
| 8 | 80 | 64 | 144.51 | 152.93 | 0.945x | 146.43 | 0.987x | 139.87 |
1.033x |
| 8 | 80 | 256 | 543.36 | 579.77 | 0.937x | 554.43 | 0.980x | 528.89 |
1.027x |
| 8 | 24 | 1 | 7.78 | 8.22 | 0.946x | 7.93 | 0.980x | 7.62 | 1.021x |
| 8 | 24 | 16 | 17.50 | 17.41 | 1.005x | 16.77 | 1.044x | 16.16 | 1.083x
|
| 8 | 24 | 64 | 50.18 | 51.84 | 0.968x | 49.70 | 1.010x | 47.58 | 1.054x
|
| 8 | 24 | 256 | 170.97 | 181.37 | 0.943x | 173.55 | 0.985x | 165.85 |
1.031x |
| 8 | 20 | 1 | 7.68 | 8.13 | 0.945x | 7.84 | 0.980x | 7.52 | 1.021x |
| 8 | 20 | 16 | 17.02 | 17.02 | 1.000x | 16.35 | 1.041x | 15.74 | 1.081x
|
| 8 | 20 | 64 | 42.34 | 43.46 | 0.974x | 41.70 | 1.015x | 39.97 | 1.059x
|
| 8 | 20 | 256 | 144.58 | 152.86 | 0.946x | 146.37 | 0.988x | 139.84 |
1.034x |
| 8 | 10 | 1 | 7.74 | 8.16 | 0.949x | 7.87 | 0.984x | 7.58 | 1.021x |
| 8 | 10 | 16 | 12.16 | 12.75 | 0.953x | 12.22 | 0.995x | 11.78 | 1.033x
|
| 8 | 10 | 64 | 26.14 | 26.11 | 1.001x | 25.09 | 1.042x | 24.10 | 1.085x
|
| 8 | 10 | 256 | 77.53 | 81.18 | 0.955x | 77.76 | 0.997x | 74.40 |
1.042x |
| 16 | 80 | 1 | 13.18 | 13.44 | 0.981x | 13.12 | 1.005x | 12.86 | 1.025x
|
| 16 | 80 | 16 | 75.52 | 78.30 | 0.964x | 76.51 | 0.987x | 74.82 |
1.009x |
| 16 | 80 | 64 | 265.50 | 279.12 | 0.951x | 272.51 | 0.974x | 266.17 |
0.997x |
| 16 | 80 | 256 | 1015.22 | 1072.21 | 0.947x | 1045.97 | 0.971x |
1021.08 | 0.994x |
| 16 | 24 | 1 | 12.77 | 13.12 | 0.973x | 12.83 | 0.995x | 12.54 | 1.018x
|
| 16 | 24 | 16 | 29.66 | 30.14 | 0.984x | 29.54 | 1.004x | 28.93 |
1.025x |
| 16 | 24 | 64 | 90.02 | 93.76 | 0.960x | 91.58 | 0.983x | 89.50 |
1.006x |
| 16 | 24 | 256 | 315.10 | 331.76 | 0.950x | 323.81 | 0.973x | 316.16 |
0.997x |
| 16 | 20 | 1 | 12.67 | 13.02 | 0.973x | 12.70 | 0.997x | 12.42 | 1.021x
|
| 16 | 20 | 16 | 29.22 | 29.66 | 0.985x | 29.02 | 1.007x | 28.42 |
1.028x |
| 16 | 20 | 64 | 75.49 | 78.30 | 0.964x | 76.51 | 0.987x | 74.82 |
1.009x |
| 16 | 20 | 256 | 265.50 | 279.30 | 0.951x | 272.64 | 0.974x | 266.33 |
0.997x |
| 16 | 10 | 1 | 12.67 | 13.05 | 0.971x | 12.77 | 0.992x | 12.48 | 1.015x
|
| 16 | 10 | 16 | 21.09 | 21.28 | 0.991x | 20.77 | 1.015x | 20.35 |
1.036x |
| 16 | 10 | 64 | 45.34 | 46.53 | 0.975x | 45.47 | 0.997x | 44.48 |
1.019x |
| 16 | 10 | 256 | 140.99 | 147.71 | 0.955x | 144.22 | 0.978x | 140.93 |
1.000x |

</details>

<details>
<summary>NVIDIA B200, SM100 (sm_100a, 148 SMs), CUDA 13.4: snap rows
(every token's state (snapshots)), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2 | 80 | 1 | 5.82 | 6.05 | 0.963x | 5.73 | 1.017x | 5.38 | 1.084x |
| 2 | 80 | 16 | 25.02 | 22.05 | 1.135x | 20.32 | 1.231x | 17.89 | 1.399x
|
| 2 | 80 | 64 | 85.15 | 73.15 | 1.164x | 67.49 | 1.262x | 58.98 | 1.444x
|
| 2 | 80 | 256 | 320.99 | 272.67 | 1.177x | 251.17 | 1.278x | 219.04 |
1.465x |
| 2 | 24 | 1 | 5.66 | 5.92 | 0.957x | 5.66 | 1.000x | 5.34 | 1.060x |
| 2 | 24 | 16 | 10.43 | 9.70 | 1.076x | 8.93 | 1.168x | 8.06 | 1.294x |
| 2 | 24 | 64 | 29.73 | 25.76 | 1.154x | 23.82 | 1.248x | 20.96 | 1.418x
|
| 2 | 24 | 256 | 101.04 | 86.69 | 1.166x | 79.94 | 1.264x | 70.05 |
1.442x |
| 2 | 20 | 1 | 5.63 | 5.95 | 0.946x | 5.63 | 1.000x | 5.25 | 1.073x |
| 2 | 20 | 16 | 10.14 | 9.47 | 1.071x | 8.74 | 1.161x | 7.84 | 1.294x |
| 2 | 20 | 64 | 25.22 | 22.05 | 1.144x | 20.35 | 1.239x | 17.98 | 1.402x
|
| 2 | 20 | 256 | 85.41 | 73.28 | 1.166x | 67.65 | 1.263x | 59.26 |
1.441x |
| 2 | 10 | 1 | 5.66 | 5.98 | 0.947x | 5.73 | 0.989x | 5.38 | 1.054x |
| 2 | 10 | 16 | 7.71 | 7.46 | 1.034x | 6.98 | 1.106x | 6.37 | 1.211x |
| 2 | 10 | 64 | 15.90 | 14.05 | 1.132x | 12.90 | 1.233x | 11.62 | 1.369x
|
| 2 | 10 | 256 | 45.86 | 39.39 | 1.164x | 36.35 | 1.261x | 31.87 |
1.439x |
| 4 | 80 | 1 | 7.68 | 7.39 | 1.039x | 7.17 | 1.071x | 6.88 | 1.116x |
| 4 | 80 | 16 | 40.29 | 31.87 | 1.264x | 30.37 | 1.327x | 27.10 | 1.486x
|
| 4 | 80 | 64 | 142.01 | 109.86 | 1.293x | 104.99 | 1.353x | 93.12 |
1.525x |
| 4 | 80 | 256 | 544.06 | 412.48 | 1.319x | 394.62 | 1.379x | 349.36 |
1.557x |
| 4 | 24 | 1 | 7.52 | 7.26 | 1.035x | 7.01 | 1.073x | 6.75 | 1.114x |
| 4 | 24 | 16 | 15.97 | 13.31 | 1.200x | 12.77 | 1.251x | 11.62 | 1.375x
|
| 4 | 24 | 64 | 48.16 | 37.82 | 1.273x | 36.06 | 1.335x | 32.22 | 1.495x
|
| 4 | 24 | 256 | 168.83 | 130.69 | 1.292x | 124.83 | 1.352x | 110.72 |
1.525x |
| 4 | 20 | 1 | 7.52 | 7.30 | 1.031x | 7.01 | 1.073x | 6.72 | 1.119x |
| 4 | 20 | 16 | 15.62 | 12.93 | 1.208x | 12.38 | 1.261x | 11.30 | 1.382x
|
| 4 | 20 | 64 | 40.30 | 31.90 | 1.263x | 30.40 | 1.326x | 27.04 | 1.491x
|
| 4 | 20 | 256 | 142.14 | 110.05 | 1.292x | 105.25 | 1.351x | 93.34 |
1.523x |
| 4 | 10 | 1 | 7.49 | 7.13 | 1.049x | 6.85 | 1.093x | 6.66 | 1.125x |
| 4 | 10 | 16 | 11.26 | 9.95 | 1.132x | 9.50 | 1.185x | 8.67 | 1.299x |
| 4 | 10 | 64 | 24.35 | 19.71 | 1.235x | 18.59 | 1.310x | 16.67 | 1.461x
|
| 4 | 10 | 256 | 75.74 | 59.07 | 1.282x | 56.38 | 1.343x | 50.05 |
1.513x |
| 8 | 80 | 1 | 15.14 | 10.21 | 1.483x | 9.92 | 1.526x | 9.15 | 1.654x |
| 8 | 80 | 16 | 73.73 | 55.49 | 1.329x | 53.98 | 1.366x | 48.77 | 1.512x
|
| 8 | 80 | 64 | 266.08 | 196.91 | 1.351x | 191.68 | 1.388x | 172.05 |
1.547x |
| 8 | 80 | 256 | 1029.97 | 752.47 | 1.369x | 732.22 | 1.407x | 653.91 |
1.575x |
| 8 | 24 | 1 | 14.34 | 9.98 | 1.436x | 9.70 | 1.479x | 8.93 | 1.606x |
| 8 | 24 | 16 | 27.81 | 21.57 | 1.289x | 20.99 | 1.325x | 19.33 | 1.439x
|
| 8 | 24 | 64 | 88.42 | 66.11 | 1.337x | 64.35 | 1.374x | 58.05 | 1.523x
|
| 8 | 24 | 256 | 317.08 | 234.17 | 1.354x | 227.87 | 1.392x | 204.09 |
1.554x |
| 8 | 20 | 1 | 14.21 | 10.02 | 1.419x | 9.70 | 1.465x | 8.96 | 1.586x |
| 8 | 20 | 16 | 27.20 | 21.09 | 1.290x | 20.56 | 1.323x | 18.85 | 1.443x
|
| 8 | 20 | 64 | 73.60 | 55.39 | 1.329x | 53.86 | 1.367x | 48.64 | 1.513x
|
| 8 | 20 | 256 | 266.30 | 197.07 | 1.351x | 191.81 | 1.388x | 172.06 |
1.548x |
| 8 | 10 | 1 | 13.66 | 9.89 | 1.382x | 9.60 | 1.423x | 8.86 | 1.542x |
| 8 | 10 | 16 | 21.54 | 15.65 | 1.376x | 15.14 | 1.423x | 13.82 | 1.558x
|
| 8 | 10 | 64 | 43.28 | 33.09 | 1.308x | 32.06 | 1.350x | 29.09 | 1.488x
|
| 8 | 10 | 256 | 139.87 | 104.35 | 1.340x | 101.53 | 1.378x | 91.23 |
1.533x |
| 16 | 80 | 1 | 27.28 | 17.31 | 1.576x | 16.99 | 1.605x | 15.68 | 1.740x
|
| 16 | 80 | 16 | 140.51 | 152.77 | 0.920x | 120.06 | 1.170x | 90.72 |
1.549x |
| 16 | 80 | 64 | 518.80 | 556.06 | 0.933x | 432.00 | 1.201x | 323.55 |
1.603x |
| 16 | 80 | 256 | 2033.25 | 2165.20 | 0.939x | 1673.78 | 1.215x |
1247.11 | 1.630x |
| 16 | 24 | 1 | 26.13 | 17.09 | 1.529x | 16.77 | 1.558x | 15.49 | 1.687x
|
| 16 | 24 | 16 | 49.82 | 56.43 | 0.883x | 44.74 | 1.114x | 34.50 |
1.444x |
| 16 | 24 | 64 | 168.13 | 182.78 | 0.920x | 142.91 | 1.176x | 107.94 |
1.558x |
| 16 | 24 | 256 | 619.42 | 663.64 | 0.933x | 514.79 | 1.203x | 385.23 |
1.608x |
| 16 | 20 | 1 | 25.86 | 16.90 | 1.530x | 16.61 | 1.557x | 15.33 | 1.687x
|
| 16 | 20 | 16 | 49.41 | 55.97 | 0.883x | 44.29 | 1.116x | 33.98 |
1.454x |
| 16 | 20 | 64 | 140.19 | 152.67 | 0.918x | 120.03 | 1.168x | 90.69 |
1.546x |
| 16 | 20 | 256 | 518.62 | 555.90 | 0.933x | 432.00 | 1.201x | 324.19 |
1.600x |
| 16 | 10 | 1 | 25.07 | 16.96 | 1.478x | 16.67 | 1.504x | 15.42 | 1.626x
|
| 16 | 10 | 16 | 37.38 | 27.36 | 1.366x | 26.82 | 1.394x | 24.51 |
1.525x |
| 16 | 10 | 64 | 80.90 | 89.58 | 0.903x | 70.94 | 1.140x | 53.70 |
1.507x |
| 16 | 10 | 256 | 269.73 | 291.62 | 0.925x | 227.49 | 1.186x | 171.12 |
1.576x |

</details>

<details>
<summary>NVIDIA B200, SM100 (sm_100a, 148 SMs), CUDA 13.4: rsnap rows
(runtime-T program, every token's state), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 80 | 16 | 209.13 | 140.77 | 1.486x | 121.06 | 1.728x | 104.89 |
1.994x |
| 10 | 80 | 64 | 656.45 | 455.65 | 1.441x | 392.00 | 1.675x | 337.98 |
1.942x |
| 10 | 80 | 256 | 2447.52 | 1710.26 | 1.431x | 1488.42 | 1.644x |
1287.63 | 1.901x |
| 10 | 20 | 16 | 71.01 | 55.68 | 1.275x | 45.98 | 1.544x | 38.85 |
1.828x |
| 10 | 20 | 64 | 208.54 | 140.70 | 1.482x | 120.99 | 1.724x | 104.67 |
1.992x |
| 10 | 20 | 256 | 654.91 | 454.89 | 1.440x | 391.18 | 1.674x | 337.29 |
1.942x |
| 12 | 80 | 16 | 245.34 | 166.24 | 1.476x | 142.75 | 1.719x | 123.30 |
1.990x |
| 12 | 80 | 64 | 778.20 | 540.46 | 1.440x | 464.09 | 1.677x | 398.56 |
1.953x |
| 12 | 80 | 256 | 2899.22 | 2028.92 | 1.429x | 1760.50 | 1.647x |
1517.69 | 1.910x |
| 12 | 20 | 16 | 84.22 | 66.11 | 1.274x | 54.53 | 1.545x | 45.73 |
1.842x |
| 12 | 20 | 64 | 245.73 | 166.08 | 1.480x | 142.56 | 1.724x | 123.07 |
1.997x |
| 12 | 20 | 256 | 774.12 | 539.64 | 1.435x | 462.67 | 1.673x | 397.50 |
1.947x |

</details>

<details>
<summary>NVIDIA GB300, SM103 (sm_103a, 152 SMs), CUDA 13.4: owner rows
(final state only), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 1 | 80 | 1 | 3.81 | 4.32 | 0.881x | 4.03 | 0.944x | 3.58 | 1.062x |
| 1 | 80 | 16 | 13.28 | 13.66 | 0.972x | 12.19 | 1.089x | 10.69 | 1.243x
|
| 1 | 80 | 64 | 47.38 | 41.73 | 1.135x | 36.42 | 1.301x | 30.82 | 1.537x
|
| 1 | 80 | 256 | 194.11 | 156.51 | 1.240x | 131.26 | 1.479x | 119.50 |
1.624x |
| 1 | 24 | 1 | 3.20 | 3.49 | 0.917x | 3.33 | 0.962x | 3.01 | 1.064x |
| 1 | 24 | 16 | 6.66 | 6.43 | 1.035x | 5.86 | 1.137x | 5.31 | 1.253x |
| 1 | 24 | 64 | 14.85 | 15.30 | 0.971x | 13.57 | 1.094x | 11.84 | 1.254x
|
| 1 | 24 | 256 | 57.12 | 49.66 | 1.150x | 43.55 | 1.312x | 37.22 |
1.535x |
| 1 | 20 | 1 | 3.26 | 3.62 | 0.903x | 3.49 | 0.936x | 3.07 | 1.062x |
| 1 | 20 | 16 | 6.27 | 6.18 | 1.016x | 5.60 | 1.120x | 5.06 | 1.241x |
| 1 | 20 | 64 | 13.31 | 13.76 | 0.967x | 12.27 | 1.085x | 10.69 | 1.246x
|
| 1 | 20 | 256 | 47.30 | 41.92 | 1.128x | 36.70 | 1.289x | 31.14 |
1.519x |
| 1 | 10 | 1 | 3.04 | 3.39 | 0.896x | 3.26 | 0.931x | 2.94 | 1.033x |
| 1 | 10 | 16 | 4.64 | 5.57 | 0.833x | 5.02 | 0.924x | 4.45 | 1.043x |
| 1 | 10 | 64 | 8.54 | 8.96 | 0.954x | 8.03 | 1.064x | 7.17 | 1.192x |
| 1 | 10 | 256 | 22.75 | 22.75 | 1.000x | 20.16 | 1.129x | 17.34 |
1.312x |
| 2 | 80 | 1 | 5.06 | 5.60 | 0.903x | 5.34 | 0.946x | 4.96 | 1.019x |
| 2 | 80 | 16 | 18.11 | 18.78 | 0.964x | 17.12 | 1.058x | 15.58 | 1.162x
|
| 2 | 80 | 64 | 56.45 | 59.76 | 0.945x | 54.43 | 1.037x | 48.99 | 1.152x
|
| 2 | 80 | 256 | 215.01 | 226.18 | 0.951x | 205.28 | 1.047x | 184.26 |
1.167x |
| 2 | 24 | 1 | 4.86 | 5.44 | 0.894x | 5.18 | 0.938x | 4.86 | 1.000x |
| 2 | 24 | 16 | 8.10 | 8.32 | 0.973x | 7.68 | 1.054x | 7.10 | 1.140x |
| 2 | 24 | 64 | 20.42 | 21.60 | 0.945x | 19.74 | 1.034x | 17.89 | 1.141x
|
| 2 | 24 | 256 | 67.58 | 71.49 | 0.945x | 65.06 | 1.039x | 58.46 |
1.156x |
| 2 | 20 | 1 | 4.77 | 5.34 | 0.892x | 5.12 | 0.931x | 4.80 | 0.993x |
| 2 | 20 | 16 | 7.81 | 8.10 | 0.964x | 7.49 | 1.043x | 6.91 | 1.130x |
| 2 | 20 | 64 | 18.03 | 18.72 | 0.963x | 17.09 | 1.055x | 15.49 | 1.164x
|
| 2 | 20 | 256 | 56.70 | 60.16 | 0.943x | 54.72 | 1.036x | 49.18 |
1.153x |
| 2 | 10 | 1 | 4.74 | 5.31 | 0.892x | 5.06 | 0.937x | 4.74 | 1.000x |
| 2 | 10 | 16 | 6.11 | 6.59 | 0.927x | 6.21 | 0.985x | 5.73 | 1.067x |
| 2 | 10 | 64 | 12.13 | 12.35 | 0.982x | 11.46 | 1.059x | 10.40 | 1.166x
|
| 2 | 10 | 256 | 30.21 | 32.22 | 0.937x | 29.34 | 1.029x | 26.46 |
1.141x |
| 3 | 80 | 1 | 5.57 | 5.86 | 0.951x | 5.60 | 0.994x | 5.25 | 1.061x |
| 3 | 80 | 16 | 20.58 | 21.28 | 0.967x | 19.68 | 1.046x | 18.14 | 1.134x
|
| 3 | 80 | 64 | 65.31 | 69.60 | 0.938x | 64.37 | 1.015x | 59.59 | 1.096x
|
| 3 | 80 | 256 | 244.96 | 264.57 | 0.926x | 244.61 | 1.001x | 226.27 |
1.083x |
| 3 | 24 | 1 | 5.25 | 5.66 | 0.927x | 5.41 | 0.970x | 5.09 | 1.031x |
| 3 | 24 | 16 | 9.38 | 9.38 | 1.000x | 8.83 | 1.062x | 8.19 | 1.145x |
| 3 | 24 | 64 | 23.90 | 24.99 | 0.956x | 23.07 | 1.036x | 21.38 | 1.118x
|
| 3 | 24 | 256 | 77.41 | 82.88 | 0.934x | 76.45 | 1.013x | 70.72 |
1.095x |
| 3 | 20 | 1 | 5.41 | 5.82 | 0.929x | 5.54 | 0.977x | 5.22 | 1.037x |
| 3 | 20 | 16 | 9.12 | 9.22 | 0.990x | 8.58 | 1.063x | 7.94 | 1.149x |
| 3 | 20 | 64 | 20.61 | 21.25 | 0.970x | 19.68 | 1.047x | 18.14 | 1.136x
|
| 3 | 20 | 256 | 65.41 | 69.60 | 0.940x | 64.38 | 1.016x | 59.62 |
1.097x |
| 3 | 10 | 1 | 5.15 | 5.57 | 0.925x | 5.28 | 0.976x | 4.99 | 1.032x |
| 3 | 10 | 16 | 6.94 | 7.23 | 0.960x | 6.78 | 1.024x | 6.40 | 1.085x |
| 3 | 10 | 64 | 13.60 | 13.60 | 1.000x | 12.61 | 1.079x | 11.68 | 1.164x
|
| 3 | 10 | 256 | 35.17 | 37.02 | 0.950x | 34.24 | 1.027x | 31.71 |
1.109x |
| 4 | 80 | 1 | 5.50 | 5.86 | 0.940x | 5.60 | 0.983x | 5.28 | 1.042x |
| 4 | 80 | 16 | 22.69 | 23.94 | 0.948x | 22.34 | 1.016x | 20.99 | 1.081x
|
| 4 | 80 | 64 | 74.14 | 80.16 | 0.925x | 74.53 | 0.995x | 70.11 | 1.058x
|
| 4 | 80 | 256 | 279.87 | 306.05 | 0.914x | 284.19 | 0.985x | 267.74 |
1.045x |
| 4 | 24 | 1 | 5.38 | 5.79 | 0.928x | 5.54 | 0.971x | 5.22 | 1.031x |
| 4 | 24 | 16 | 10.37 | 10.56 | 0.982x | 9.89 | 1.049x | 9.38 | 1.106x |
| 4 | 24 | 64 | 26.46 | 28.32 | 0.934x | 26.40 | 1.002x | 24.61 | 1.075x
|
| 4 | 24 | 256 | 87.78 | 95.36 | 0.920x | 88.77 | 0.989x | 83.14 |
1.056x |
| 4 | 20 | 1 | 5.34 | 5.79 | 0.923x | 5.57 | 0.960x | 5.25 | 1.018x |
| 4 | 20 | 16 | 10.21 | 10.46 | 0.976x | 9.82 | 1.039x | 9.25 | 1.104x |
| 4 | 20 | 64 | 22.72 | 24.03 | 0.945x | 22.46 | 1.011x | 21.09 | 1.077x
|
| 4 | 20 | 256 | 73.95 | 79.94 | 0.925x | 74.43 | 0.994x | 69.89 |
1.058x |
| 4 | 10 | 1 | 5.22 | 5.66 | 0.921x | 5.44 | 0.959x | 5.09 | 1.025x |
| 4 | 10 | 16 | 7.49 | 7.78 | 0.963x | 7.39 | 1.013x | 6.96 | 1.076x |
| 4 | 10 | 64 | 14.37 | 14.94 | 0.961x | 14.02 | 1.025x | 13.09 | 1.098x
|
| 4 | 10 | 256 | 39.52 | 42.24 | 0.936x | 39.42 | 1.002x | 37.07 |
1.066x |
| 5 | 80 | 1 | 6.66 | 6.80 | 0.979x | 6.53 | 1.020x | 6.21 | 1.072x |
| 5 | 80 | 16 | 28.35 | 29.31 | 0.967x | 27.65 | 1.025x | 26.11 | 1.086x
|
| 5 | 80 | 64 | 92.83 | 98.56 | 0.942x | 92.58 | 1.003x | 86.98 | 1.067x
|
| 5 | 80 | 256 | 353.54 | 379.01 | 0.933x | 355.65 | 0.994x | 333.70 |
1.059x |
| 5 | 24 | 1 | 6.43 | 6.69 | 0.962x | 6.40 | 1.005x | 6.08 | 1.058x |
| 5 | 24 | 16 | 12.45 | 12.38 | 1.005x | 11.81 | 1.054x | 11.26 | 1.105x
|
| 5 | 24 | 64 | 32.80 | 34.37 | 0.954x | 32.42 | 1.012x | 30.56 | 1.073x
|
| 5 | 24 | 256 | 110.56 | 117.73 | 0.939x | 110.50 | 1.001x | 103.78 |
1.065x |
| 5 | 20 | 1 | 6.34 | 6.62 | 0.957x | 6.37 | 0.995x | 6.05 | 1.048x |
| 5 | 20 | 16 | 12.22 | 12.32 | 0.992x | 11.71 | 1.044x | 11.17 | 1.095x
|
| 5 | 20 | 64 | 28.35 | 29.28 | 0.968x | 27.65 | 1.025x | 26.11 | 1.086x
|
| 5 | 20 | 256 | 92.96 | 98.78 | 0.941x | 92.83 | 1.001x | 87.17 |
1.066x |
| 5 | 10 | 1 | 6.14 | 6.37 | 0.965x | 6.11 | 1.005x | 5.84 | 1.052x |
| 5 | 10 | 16 | 9.12 | 9.38 | 0.973x | 8.86 | 1.029x | 8.38 | 1.088x |
| 5 | 10 | 64 | 17.98 | 18.11 | 0.993x | 17.15 | 1.049x | 16.27 | 1.105x
|
| 5 | 10 | 256 | 48.96 | 51.49 | 0.951x | 48.46 | 1.010x | 45.60 |
1.074x |
| 6 | 80 | 1 | 7.07 | 7.39 | 0.957x | 7.10 | 0.995x | 6.82 | 1.038x |
| 6 | 80 | 16 | 31.90 | 32.86 | 0.971x | 31.20 | 1.023x | 29.54 | 1.080x
|
| 6 | 80 | 64 | 104.54 | 111.55 | 0.937x | 105.44 | 0.991x | 99.49 |
1.051x |
| 6 | 80 | 256 | 398.06 | 429.15 | 0.928x | 405.31 | 0.982x | 381.79 |
1.043x |
| 6 | 24 | 1 | 6.82 | 7.23 | 0.942x | 6.94 | 0.982x | 6.66 | 1.024x |
| 6 | 24 | 16 | 13.95 | 13.89 | 1.005x | 13.31 | 1.048x | 12.77 | 1.093x
|
| 6 | 24 | 64 | 37.15 | 38.66 | 0.961x | 36.67 | 1.013x | 34.72 | 1.070x
|
| 6 | 24 | 256 | 124.42 | 133.21 | 0.934x | 125.89 | 0.988x | 118.75 |
1.048x |
| 6 | 20 | 1 | 6.78 | 7.20 | 0.942x | 6.94 | 0.977x | 6.59 | 1.029x |
| 6 | 20 | 16 | 13.63 | 13.60 | 1.002x | 13.02 | 1.047x | 12.48 | 1.092x
|
| 6 | 20 | 64 | 31.97 | 32.74 | 0.977x | 31.10 | 1.028x | 29.47 | 1.085x
|
| 6 | 20 | 256 | 104.83 | 111.65 | 0.939x | 105.63 | 0.992x | 99.65 |
1.052x |
| 6 | 10 | 1 | 6.59 | 7.01 | 0.941x | 6.75 | 0.976x | 6.46 | 1.020x |
| 6 | 10 | 16 | 9.89 | 10.53 | 0.939x | 10.08 | 0.981x | 9.57 | 1.033x |
| 6 | 10 | 64 | 20.26 | 20.00 | 1.013x | 19.07 | 1.062x | 18.14 | 1.116x
|
| 6 | 10 | 256 | 55.55 | 58.30 | 0.953x | 55.23 | 1.006x | 52.19 |
1.064x |
| 7 | 80 | 1 | 7.71 | 7.87 | 0.980x | 7.62 | 1.013x | 7.36 | 1.048x |
| 7 | 80 | 16 | 36.35 | 36.38 | 0.999x | 34.72 | 1.047x | 33.12 | 1.098x
|
| 7 | 80 | 64 | 120.53 | 125.09 | 0.964x | 119.10 | 1.012x | 113.12 |
1.065x |
| 7 | 80 | 256 | 460.93 | 483.04 | 0.954x | 459.46 | 1.003x | 435.97 |
1.057x |
| 7 | 24 | 1 | 7.52 | 7.74 | 0.971x | 7.49 | 1.004x | 7.23 | 1.040x |
| 7 | 24 | 16 | 15.55 | 15.17 | 1.025x | 14.62 | 1.063x | 14.02 | 1.110x
|
| 7 | 24 | 64 | 42.66 | 43.23 | 0.987x | 41.25 | 1.034x | 39.26 | 1.086x
|
| 7 | 24 | 256 | 143.55 | 149.63 | 0.959x | 142.37 | 1.008x | 135.23 |
1.062x |
| 7 | 20 | 1 | 7.46 | 7.71 | 0.967x | 7.42 | 1.004x | 7.17 | 1.040x |
| 7 | 20 | 16 | 15.10 | 14.91 | 1.013x | 14.30 | 1.056x | 13.73 | 1.100x
|
| 7 | 20 | 64 | 36.35 | 36.48 | 0.996x | 34.78 | 1.045x | 33.15 | 1.097x
|
| 7 | 20 | 256 | 120.51 | 125.02 | 0.964x | 119.04 | 1.012x | 113.06 |
1.066x |
| 7 | 10 | 1 | 7.46 | 7.70 | 0.969x | 7.42 | 1.004x | 7.14 | 1.045x |
| 7 | 10 | 16 | 11.17 | 11.55 | 0.967x | 11.07 | 1.009x | 10.66 | 1.048x
|
| 7 | 10 | 64 | 22.82 | 22.21 | 1.027x | 21.28 | 1.072x | 20.35 | 1.121x
|
| 7 | 10 | 256 | 63.81 | 65.25 | 0.978x | 62.14 | 1.027x | 59.14 |
1.079x |
| 8 | 80 | 1 | 7.68 | 8.06 | 0.952x | 7.78 | 0.988x | 7.49 | 1.026x |
| 8 | 80 | 16 | 38.82 | 39.97 | 0.971x | 38.34 | 1.013x | 36.74 | 1.057x
|
| 8 | 80 | 64 | 130.46 | 138.01 | 0.945x | 132.10 | 0.988x | 126.40 |
1.032x |
| 8 | 80 | 256 | 498.03 | 531.90 | 0.936x | 508.77 | 0.979x | 486.64 |
1.023x |
| 8 | 24 | 1 | 7.54 | 7.97 | 0.946x | 7.68 | 0.981x | 7.39 | 1.019x |
| 8 | 24 | 16 | 16.26 | 16.19 | 1.004x | 15.58 | 1.043x | 15.04 | 1.081x
|
| 8 | 24 | 64 | 45.60 | 47.42 | 0.962x | 45.50 | 1.002x | 43.58 | 1.046x
|
| 8 | 24 | 256 | 154.94 | 164.83 | 0.940x | 157.73 | 0.982x | 150.88 |
1.027x |
| 8 | 20 | 1 | 7.49 | 7.94 | 0.944x | 7.65 | 0.979x | 7.36 | 1.017x |
| 8 | 20 | 16 | 15.87 | 15.82 | 1.003x | 15.23 | 1.042x | 14.69 | 1.081x
|
| 8 | 20 | 64 | 38.66 | 40.00 | 0.966x | 38.34 | 1.008x | 36.70 | 1.053x
|
| 8 | 20 | 256 | 130.08 | 137.79 | 0.944x | 131.90 | 0.986x | 126.18 |
1.031x |
| 8 | 10 | 1 | 7.33 | 7.74 | 0.946x | 7.46 | 0.983x | 7.18 | 1.020x |
| 8 | 10 | 16 | 11.68 | 12.16 | 0.961x | 11.71 | 0.997x | 11.26 | 1.037x
|
| 8 | 10 | 64 | 23.87 | 24.13 | 0.989x | 23.20 | 1.029x | 22.24 | 1.073x
|
| 8 | 10 | 256 | 68.06 | 71.30 | 0.955x | 68.35 | 0.996x | 65.44 |
1.040x |
| 16 | 80 | 1 | 12.16 | 12.96 | 0.938x | 12.70 | 0.957x | 12.42 | 0.979x
|
| 16 | 80 | 16 | 69.31 | 71.68 | 0.967x | 70.05 | 0.989x | 68.42 |
1.013x |
| 16 | 80 | 64 | 241.54 | 251.87 | 0.959x | 245.89 | 0.982x | 239.97 |
1.007x |
| 16 | 80 | 256 | 935.89 | 978.62 | 0.956x | 955.20 | 0.980x | 931.78 |
1.004x |
| 16 | 24 | 1 | 11.90 | 12.77 | 0.932x | 12.51 | 0.951x | 12.22 | 0.974x
|
| 16 | 24 | 16 | 27.26 | 27.68 | 0.985x | 27.10 | 1.006x | 26.53 |
1.028x |
| 16 | 24 | 64 | 82.59 | 85.63 | 0.964x | 83.65 | 0.987x | 81.70 |
1.011x |
| 16 | 24 | 256 | 288.96 | 301.76 | 0.958x | 294.62 | 0.981x | 287.46 |
1.005x |
| 16 | 20 | 1 | 11.84 | 12.74 | 0.930x | 12.45 | 0.951x | 12.19 | 0.971x
|
| 16 | 20 | 16 | 27.10 | 27.49 | 0.986x | 26.91 | 1.007x | 26.34 |
1.029x |
| 16 | 20 | 64 | 69.31 | 71.62 | 0.968x | 70.02 | 0.990x | 68.42 |
1.013x |
| 16 | 20 | 256 | 242.05 | 252.26 | 0.960x | 246.32 | 0.983x | 240.35 |
1.007x |
| 16 | 10 | 1 | 11.94 | 12.80 | 0.932x | 12.51 | 0.954x | 12.22 | 0.976x
|
| 16 | 10 | 16 | 19.20 | 20.19 | 0.951x | 19.74 | 0.972x | 19.33 |
0.993x |
| 16 | 10 | 64 | 41.76 | 42.72 | 0.978x | 41.76 | 1.000x | 40.83 |
1.023x |
| 16 | 10 | 256 | 124.61 | 129.38 | 0.963x | 126.40 | 0.986x | 123.39 |
1.010x |

</details>

<details>
<summary>NVIDIA GB300, SM103 (sm_103a, 152 SMs), CUDA 13.4: snap rows
(every token's state (snapshots)), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 2 | 80 | 1 | 5.54 | 5.79 | 0.956x | 5.50 | 1.006x | 5.15 | 1.075x |
| 2 | 80 | 16 | 23.46 | 20.48 | 1.145x | 18.98 | 1.236x | 16.77 | 1.399x
|
| 2 | 80 | 64 | 78.62 | 65.41 | 1.202x | 60.48 | 1.300x | 53.09 | 1.481x
|
| 2 | 80 | 256 | 298.69 | 248.00 | 1.204x | 228.77 | 1.306x | 200.48 |
1.490x |
| 2 | 24 | 1 | 5.44 | 5.66 | 0.960x | 5.41 | 1.006x | 5.09 | 1.069x |
| 2 | 24 | 16 | 9.92 | 9.09 | 1.092x | 8.48 | 1.170x | 7.65 | 1.297x |
| 2 | 24 | 64 | 27.42 | 23.36 | 1.174x | 21.63 | 1.268x | 19.07 | 1.438x
|
| 2 | 24 | 256 | 93.79 | 78.18 | 1.200x | 72.32 | 1.297x | 63.78 |
1.471x |
| 2 | 20 | 1 | 5.34 | 5.60 | 0.954x | 5.31 | 1.006x | 5.02 | 1.064x |
| 2 | 20 | 16 | 9.76 | 9.02 | 1.082x | 8.42 | 1.160x | 7.62 | 1.282x |
| 2 | 20 | 64 | 23.49 | 20.42 | 1.150x | 18.93 | 1.241x | 16.77 | 1.401x
|
| 2 | 20 | 256 | 79.01 | 65.70 | 1.203x | 60.80 | 1.299x | 53.62 |
1.474x |
| 2 | 10 | 1 | 5.22 | 5.50 | 0.948x | 5.25 | 0.994x | 4.93 | 1.058x |
| 2 | 10 | 16 | 7.33 | 7.07 | 1.036x | 6.66 | 1.101x | 6.11 | 1.199x |
| 2 | 10 | 64 | 15.07 | 13.25 | 1.138x | 12.22 | 1.233x | 11.07 | 1.361x
|
| 2 | 10 | 256 | 41.98 | 35.04 | 1.198x | 32.51 | 1.291x | 28.80 |
1.458x |
| 4 | 80 | 1 | 7.26 | 6.82 | 1.066x | 6.56 | 1.107x | 6.37 | 1.141x |
| 4 | 80 | 16 | 37.50 | 29.12 | 1.288x | 27.74 | 1.352x | 24.80 | 1.512x
|
| 4 | 80 | 64 | 130.91 | 98.43 | 1.330x | 94.14 | 1.391x | 83.62 |
1.566x |
| 4 | 80 | 256 | 505.47 | 376.16 | 1.344x | 360.03 | 1.404x | 319.17 |
1.584x |
| 4 | 24 | 1 | 7.14 | 6.59 | 1.083x | 6.37 | 1.121x | 6.24 | 1.144x |
| 4 | 24 | 16 | 15.10 | 12.38 | 1.220x | 11.90 | 1.269x | 10.88 | 1.388x
|
| 4 | 24 | 64 | 44.58 | 34.24 | 1.302x | 32.64 | 1.366x | 29.09 | 1.532x
|
| 4 | 24 | 256 | 155.90 | 117.63 | 1.325x | 112.42 | 1.387x | 99.70 |
1.564x |
| 4 | 20 | 1 | 7.17 | 6.66 | 1.077x | 6.43 | 1.114x | 6.21 | 1.155x |
| 4 | 20 | 16 | 14.59 | 11.97 | 1.219x | 11.46 | 1.274x | 10.40 | 1.403x
|
| 4 | 20 | 64 | 37.47 | 29.09 | 1.288x | 27.71 | 1.352x | 24.82 | 1.510x
|
| 4 | 20 | 256 | 130.96 | 98.37 | 1.331x | 94.10 | 1.392x | 83.58 |
1.567x |
| 4 | 10 | 1 | 7.07 | 6.75 | 1.047x | 6.53 | 1.083x | 6.27 | 1.128x |
| 4 | 10 | 16 | 10.91 | 9.34 | 1.168x | 8.96 | 1.218x | 8.19 | 1.332x |
| 4 | 10 | 64 | 22.62 | 17.89 | 1.265x | 16.83 | 1.344x | 15.23 | 1.485x
|
| 4 | 10 | 256 | 67.94 | 51.68 | 1.315x | 49.38 | 1.376x | 44.10 |
1.541x |
| 8 | 80 | 1 | 14.59 | 9.82 | 1.485x | 9.54 | 1.530x | 8.86 | 1.646x |
| 8 | 80 | 16 | 68.54 | 50.91 | 1.346x | 49.50 | 1.385x | 44.67 | 1.534x
|
| 8 | 80 | 64 | 244.38 | 179.49 | 1.362x | 174.59 | 1.400x | 156.54 |
1.561x |
| 8 | 80 | 256 | 951.87 | 693.57 | 1.372x | 675.58 | 1.409x | 603.94 |
1.576x |
| 8 | 24 | 1 | 14.02 | 9.63 | 1.455x | 9.34 | 1.500x | 8.64 | 1.622x |
| 8 | 24 | 16 | 25.95 | 20.13 | 1.289x | 19.55 | 1.327x | 18.05 | 1.438x
|
| 8 | 24 | 64 | 82.11 | 60.61 | 1.355x | 58.98 | 1.392x | 53.28 | 1.541x
|
| 8 | 24 | 256 | 292.22 | 213.73 | 1.367x | 208.06 | 1.404x | 186.40 |
1.568x |
| 8 | 20 | 1 | 13.70 | 9.54 | 1.436x | 9.28 | 1.476x | 8.61 | 1.591x |
| 8 | 20 | 16 | 25.38 | 19.71 | 1.287x | 19.10 | 1.328x | 17.57 | 1.444x
|
| 8 | 20 | 64 | 68.48 | 51.01 | 1.343x | 49.57 | 1.382x | 44.77 | 1.530x
|
| 8 | 20 | 256 | 244.19 | 179.04 | 1.364x | 174.24 | 1.401x | 156.11 |
1.564x |
| 8 | 10 | 1 | 13.57 | 9.50 | 1.428x | 9.22 | 1.472x | 8.51 | 1.594x |
| 8 | 10 | 16 | 20.19 | 14.78 | 1.366x | 14.24 | 1.418x | 12.99 | 1.554x
|
| 8 | 10 | 64 | 40.22 | 30.66 | 1.312x | 29.66 | 1.356x | 26.94 | 1.493x
|
| 8 | 10 | 256 | 125.44 | 92.54 | 1.355x | 90.02 | 1.394x | 80.86 |
1.551x |
| 16 | 80 | 1 | 26.45 | 16.48 | 1.605x | 16.19 | 1.633x | 14.91 | 1.774x
|
| 16 | 80 | 16 | 131.36 | 140.32 | 0.936x | 111.58 | 1.177x | 83.78 |
1.568x |
| 16 | 80 | 64 | 477.82 | 504.48 | 0.947x | 397.73 | 1.201x | 295.84 |
1.615x |
| 16 | 80 | 256 | 1878.66 | 1974.91 | 0.951x | 1551.84 | 1.211x |
1150.69 | 1.633x |
| 16 | 24 | 1 | 25.33 | 16.35 | 1.549x | 16.06 | 1.577x | 14.78 | 1.713x
|
| 16 | 24 | 16 | 46.50 | 51.36 | 0.905x | 41.57 | 1.119x | 32.06 |
1.450x |
| 16 | 24 | 64 | 157.22 | 168.29 | 0.934x | 133.22 | 1.180x | 99.42 |
1.581x |
| 16 | 24 | 256 | 573.38 | 605.44 | 0.947x | 476.42 | 1.204x | 353.79 |
1.621x |
| 16 | 20 | 1 | 25.36 | 16.32 | 1.554x | 16.03 | 1.582x | 14.72 | 1.723x
|
| 16 | 20 | 16 | 46.11 | 50.98 | 0.905x | 41.22 | 1.119x | 31.62 |
1.459x |
| 16 | 20 | 64 | 131.17 | 140.10 | 0.936x | 111.36 | 1.178x | 83.52 |
1.570x |
| 16 | 20 | 256 | 477.41 | 504.35 | 0.947x | 397.34 | 1.202x | 295.57 |
1.615x |
| 16 | 10 | 1 | 24.58 | 16.35 | 1.503x | 16.06 | 1.530x | 14.75 | 1.666x
|
| 16 | 10 | 16 | 35.01 | 25.66 | 1.364x | 25.15 | 1.392x | 23.07 |
1.517x |
| 16 | 10 | 64 | 75.68 | 82.27 | 0.920x | 65.89 | 1.149x | 49.70 |
1.523x |
| 16 | 10 | 256 | 242.11 | 256.91 | 0.942x | 203.26 | 1.191x | 151.76 |
1.595x |

</details>

<details>
<summary>NVIDIA GB300, SM103 (sm_103a, 152 SMs), CUDA 13.4: rsnap rows
(runtime-T program, every token's state), median kernel time</summary>

| T | heads | batch | FP32 state (us) | FP16 R10 (us) | speedup | FP16
R5 (us) | speedup | FP16 RNE (us) | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 10 | 80 | 16 | 196.83 | 132.22 | 1.489x | 113.66 | 1.732x | 98.62 |
1.996x |
| 10 | 80 | 64 | 613.49 | 412.54 | 1.487x | 356.58 | 1.720x | 309.47 |
1.982x |
| 10 | 80 | 256 | 2294.24 | 1579.94 | 1.452x | 1372.74 | 1.671x |
1189.22 | 1.929x |
| 10 | 20 | 16 | 67.66 | 52.29 | 1.294x | 43.20 | 1.566x | 36.58 |
1.850x |
| 10 | 20 | 64 | 196.67 | 132.03 | 1.490x | 113.34 | 1.735x | 98.08 |
2.005x |
| 10 | 20 | 256 | 611.58 | 412.03 | 1.484x | 355.65 | 1.720x | 308.67 |
1.981x |
| 12 | 80 | 16 | 232.83 | 156.38 | 1.489x | 133.98 | 1.738x | 115.94 |
2.008x |
| 12 | 80 | 64 | 725.23 | 488.82 | 1.484x | 420.93 | 1.723x | 363.79 |
1.994x |
| 12 | 80 | 256 | 2716.98 | 1873.73 | 1.450x | 1622.75 | 1.674x |
1397.82 | 1.944x |
| 12 | 20 | 16 | 80.10 | 62.00 | 1.292x | 51.10 | 1.567x | 42.91 |
1.866x |
| 12 | 20 | 64 | 231.78 | 155.68 | 1.489x | 133.41 | 1.737x | 115.23 |
2.011x |
| 12 | 20 | 256 | 722.16 | 487.91 | 1.480x | 420.03 | 1.719x | 362.98 |
1.990x |

</details>



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Cake GDP decode supports FP16 state pools on SM100 and SM103, while
recurrence calculations remain FP32. FP16 state storage uses
round-to-nearest-even by default, or stochastic rounding with a seed and
configurable Philox rounds.
* Support checks and route selection now account for state-pool dtype.
Unsupported dtype and seed combinations are rejected.
* **Documentation**
* Updated API guidance on FP16 state pools, rounding behavior, and
reproducibility.
* **Tests**
* Expanded coverage for FP16 pools, rounding modes, route support, and
argument validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery H <averyh@nvidia.com>

### [f914c29](https://github.com/flashinfer-ai/flashinfer/commit/f914c298473ae8a19acb2c4560f5a5625a1f960a)

- **作者**: eigen
- **时间**: 2026-11-19T12:15:57Z
- **提交信息**: fix(cake_gdn): reject unaligned q/k/state in the nontranspose decode; check the twin runs in its race gate (#9712)

The Cake nontranspose T=1 decode kernels read q and k in 8-byte vectors and
the state in 16-byte copies (cp.async or TMA). A contiguous q or k view that
starts at an unaligned storage offset passed every host check and faulted
asynchronously; a misaligned state was refused only on the TMA-state routes.
_run_cake_gdn_decode_nontranspose now raises ValueError for
such q, k or state before it resolves or launches anything, for the
whole-GPU kernel and the locality-domain twin alike. The public-path test
of a misaligned TMA-state call now expects the refusal before the row
resolves its launch (the aligned call resolves it once).

test_twin_race_gate compared every launch with the whole-GPU kernel's bits,
so a twin that failed to build, load or launch (and fell back to the whole
kernel) passed too. It now checks that the twin launch is live after the
first launch and after the stress loop.

Docs: the twin's input requirements and its two fallbacks, the
`localize_gdn_decode_state(...) is state` check, the homed copy's memory,
the race-gate environment variable, and why the eager counter pairs are
cached per thread.

### [61a1f50](https://github.com/flashinfer-ai/flashinfer/commit/61a1f50110be9d6845fe215a61f93ebf6dcfa94b)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-19T11:07:06Z
- **提交信息**: feat(moe_ep): expose prepared weights for expert migration (#9621)

<!-- .github/pull_request_template.md -->

## 📌 Description

MegaMoE preprocessing can create new weight and scale buffers, so an
engine that migrates experts needs access to those prepared tensors.
Promote the getter to `MoEEpMegaLayer.get_transformed_weights()` to
return writable aliases in the backend's runtime layout and reject
access after destruction. Internal execution and selection use the same
accessor. The caller owns placement, physical route IDs, and ordering
weight transfers before the next forward.

Use the existing block-scaled suite for the same test matrix at
EP2/4/8/16/32. The expert bank grows when a wider group needs more
physical slots. Captured replica installation, route remapping and
in-place weight/scale updates now run as shared tests for standard and
GenPhase kernels. Remove the dedicated EP16/32 wrapper file. The
provider kernels from #9426 are unchanged.

## 🔍 Related Issues

Builds on #9426.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on changed files with `pre-commit run --files
...`.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] Affected host tests pass. GPU validation is described below.

Host checks on the accessor consolidation: **123 passed, 311
GPU-dependent cases skipped**, including layer validation, selection and
collection of the affected GPU suites. Changed-file hooks pass.
Collection and pre-CUDA admission checks confirm the same **124-case
block-scaled matrix** at all five widths. GPU qualification at
`41b48eb09` passes both shared migration cases on every rank at EP2, EP4
and EP8, with no skips. Every used GPU pair passes the direct-access
probe, and allocation cleanup passes. These runs cover standard and
GenPhase kernels, replica installation, physical route remapping,
in-place updates of both projections/scales, pointer stability and
unchanged outputs for unaffected rows. These GPU runs precede the
accessor consolidation; distributed GPU tests were not rerun for that
refactor.

Earlier SM107 GPU qualification covered EP16/32 lifecycle and captured
expert remapping with MXFP4 weights/MXFP8 activations. Those wide runs
used the pre-merge refresh candidate; the full EP16/32 matrix has not
been rerun on this head.

- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: targeted MoE EP coverage is sufficient.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe_ep/test_mega_layer_validation.py
tests/moe_ep/test_ep_selection.py
tests/moe_ep/test_sm107_routing_graph_multirank.py
tests/moe_ep/test_moe_ep_sm107_block_scaled_mega_multirank.py
tests/moe_ep/test_mega_tuned_knobs_multirank.py
tests/moe_ep/test_mega_workspace_knobs_multirank.py
tests/moe_ep/test_moe_ep_sm120_w4a8_nosync_mega.py
tests/moe_ep/test_sm107_block_scaled_kernel_vs_reference.py
tests/moe_ep/test_sm107_variant_selection_multirank.py`

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

AI assistance: Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a public accessor for prepared weights, returning writable
aliases. Callers can update weights while preserving the existing
storage and captured bindings; the accessor raises an error if the layer
has been destroyed.
* **Documentation**
* Expanded guidance on expert placement, replication, routing, weight
updates, and requirements for distributed runs.
* **Tests**
* Added coverage for updating expert weights during graph replay and
expanded distributed test coverage to larger expert-parallel
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f907f26](https://github.com/flashinfer-ai/flashinfer/commit/f907f268b556676e654c25f5575346a51f71df9f)

- **作者**: ranx2026
- **时间**: 2026-11-19T10:44:07Z
- **提交信息**: test: accept the mangled sentinel kernel name in cake_profiler (#9479)

## 📌 Description

On native Windows arm64, 4 of the 8 cases of
`tests/kda/test_recurrent_kda_decode_call_shapes.py` fail with
`AssertionError: no CUDA record of the sentinel kernel '::spin_kernel('
among [...]`.

- `tests/cake/test_helpers/cake_profiler.py` recognizes the sentinel
kernel by the demangled substring `::spin_kernel(`.
- On Windows, `torch.profiler` reports the mangled symbol, which ends in
`11spin_kernelEx`.
- No record matches, so every launch-census assertion fails.

This change lets `is_sentinel` accept the mangled form of the same
symbol, `11spin_kernelE`, as well.

## 🔍 Related Issues

Related: #8431 (native Windows arm64 build support).

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust):
`tests/kda/test_recurrent_kda_decode_call_shapes.py`

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

- Verified on a Windows 11 arm64 workstation with a Blackwell GPU, on
main at `646988d` with the build support of #8431 applied.
- `tests/kda/test_recurrent_kda_decode_call_shapes.py`: 6 passed, 2
xfailed with this change.
  - Without this change: 4 failed, 2 passed, 2 xfailed.
- The two xfails are the strict xfail of
`test_batched_indexed_decode_is_one_launch`.
- Linux is unchanged: the profiler reports demangled names there, and
the existing substring keeps matching them.
- `11spin_kernelE` is the length-prefixed name inside the mangled
symbol, so the match is as specific as the demangled one.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Improved recognition of profiler sentinel records in Windows test
results.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b2d4fb1](https://github.com/flashinfer-ai/flashinfer/commit/b2d4fb1a0ea3fd8167b30f3d0f54a4b7099ebe6f)

- **作者**: ranx2026
- **时间**: 2026-11-19T10:43:22Z
- **提交信息**: fix(comm): load malloc and free from ucrtbase on Windows (#9478)

## 📌 Description

`import flashinfer.comm` fails on native Windows arm64 with `TypeError:
LoadLibrary() argument 1 must be str, not None`.

- `flashinfer/cake_ulysses_backend/cake_backend.py` runs `_LIBC =
ctypes.CDLL(None)` at import to reach `malloc` and `free`.
- On POSIX, `CDLL(None)` opens the running process. On Windows it calls
`LoadLibrary(None)` and raises.
- Test files that import `flashinfer.comm` then fail at collection, or
in the cases that import it.

This change loads `malloc` and `free` from `ucrtbase`, the universal C
runtime, on Windows. Other platforms keep `ctypes.CDLL(None)`.

## 🔍 Related Issues

Related: #8431 (native Windows arm64 build support).

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/comm/test_dlpack_utils.py
tests/comm/test_ulysses_exchange_chunks.py
tests/comm/test_ulysses_lowp.py tests/comm/test_ulysses_lowp_boundary.py
tests/comm/test_ulysses_qkv.py tests/comm/test_ulysses_communicator.py
tests/cpu/cake/test_cake_packages_standalone.py
tests/cpu/comm/test_cake_moe_finalize_dispatch.py
tests/cpu/comm/test_fp8_rowwise_gemm_allreduce_cake.py
tests/trace/test_mla_swa.py tests/trace/test_sparse_mla_dsv4_trace.py
tests/trace/test_ulysses_exchange_chunks_trace.py
tests/trace/test_ulysses_qkv_trace.py
tests/cpu/moe_ep/test_communication.py
tests/autotuner/test_autotune_cache_v2.py`

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

- Verified on a Windows 11 arm64 workstation with a Blackwell GPU, on
main at `646988d` with the build support of #8431 applied.
- The 15 test files listed as CI targets import and run: 1,010 passed,
571 skipped, 1 xfailed, no failure and no error.
- The skips are multi-GPU cases, cases for other GPU architectures and
four cases that need an optional reference package.
- `tests/comm/test_ulysses_communicator.py` shows 88 passed and 93
skipped, the same as on Linux.
- Without this change these files fail at collection, or in the cases
that import `flashinfer.comm`.
- `malloc` and `free` come from the same runtime, so each block is
released by the allocator that created it.
- Linux is unchanged: `os.name == "nt"` selects the new branch on
Windows only.
- Not touched:
`flashinfer/moe_ep/backends/split/comm/nccl_ep/_mask_ffi.py` calls
`ctypes.CDLL(None)` inside a function on an NCCL path.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Improved DLPack memory handling compatibility on Windows.
  * Existing behavior on other platforms remains unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [dc00b0e](https://github.com/flashinfer-ai/flashinfer/commit/dc00b0e516609ef71899be389628c23194271388)

- **作者**: eigen
- **时间**: 2026-11-19T09:27:20Z
- **提交信息**: perf(cake_gdn): sm_107a locality-domain GDN decode for homed states (B>=48) (#9706)

The Cake GDN decode family in FlashInfer has five variants, split by
state type, state layout and token count. This PR adds a locality-domain
twin to one of them: the FP32-state, K-major (nontranspose),
single-token decode (H=16, HV=32, both query scales). The twin targets
sm_107a GPUs with 212 SMs. It runs the `hqsplit_tma3` body in one launch
over a decode state whose batch rows the opt-in helper
`flashinfer.gdn_decode.localize_gdn_decode_state` has homed across the
two dies. The twin is used from batch 48 on, and only for a state homed
by that helper. Other batches, other SM counts, unhomed states and
sm_100a/sm_103a keep the existing whole path unchanged. On NVIDIA VR200
the twin is 1.026–1.163x faster than FI main (the shipped whole
`hqsplit_tma3` Cake path) in CUDA graphs and 1.107–1.258x faster in
back-to-back calls. Against the strongest non-Cake implementation,
FlashInfer's Triton reference decode `triton_gdn_decode` (Triton 3.8.0,
FP32 state), it is 1.184–1.475x faster in CUDA graphs and 1.325–1.456x
faster back to back.

The family's other four Cake variants are FP32 state in the pretranspose
layout at T=1 and in multi-token (MTP) form, and BF16 state in the
pretranspose layout at T=1 and in multi-token form; the family ships on
sm_100a, sm_103a and sm_107a, and the twin added here is built for
sm_107a only.

NVIDIA VR200, sm_107a, 212 SMs, measured on two boards with 106/106 and
110/102 SM die splits. FlashInfer kernels were JIT-compiled with CUDA
13.5 (nvcc 13.5.37); torch 2.14.1+cu130. Rows are H=16, HV=32, head dim
128, batch B, query scale K^-0.5 or 1.0. graph = CUPTI kernel time per
CUDA-graph replay, with the L2 flushed by a read before each replay. b2b
= CUDA-event time per call over 100 back-to-back calls. Every value is
the median of 8 timed rounds after 1 warm-up, with a fresh process per
round and arm. FI main = FlashInfer main at `9e6fb322`, the shipped
whole Cake path (`mid4_rc_kq128` at B1 and B9, `hqsplit_tma3` from B31
on). PR = this branch, with the state homed by
`localize_gdn_decode_state`. Best non-Cake = whichever of these two is
faster for each row and mode:
- E: the Triton reference `triton_gdn_decode` (Triton 3.8.0, FP32 state)
- D: FlashInfer's CuTe DSL decode (`backend="flashinfer"`,
nvidia-cutlass-dsl 4.8.1)

Speedup = baseline µs / PR µs, computed from the displayed µs. Values
below 1.000 mean the PR is slower.

**Graph, twin rows (B >= 48)**

| row | dies | FI main µs | PR µs | speedup vs FI main | best non-Cake
µs | speedup vs non-Cake |
|---|---|---:|---:|---:|---|---:|
| B48 K^-0.5 | 106/106 | 17.86 | 17.34 | 1.030 | E 20.74 | 1.196 |
| B48 K^-0.5 | 110/102 | 17.73 | 17.28 | 1.026 | E 20.74 | 1.200 |
| B56 K^-0.5 | 106/106 | 21.33 | 18.75 | 1.138 | E 23.84 | 1.271 |
| B56 K^-0.5 | 110/102 | 21.12 | 18.72 | 1.128 | E 23.81 | 1.272 |
| B63 K^-0.5 | 106/106 | 23.50 | 20.22 | 1.162 | E 26.43 | 1.307 |
| B63 K^-0.5 | 110/102 | 23.11 | 20.06 | 1.152 | E 26.30 | 1.311 |
| B64 K^-0.5 | 106/106 | 23.63 | 20.32 | 1.163 | E 27.14 | 1.336 |
| B64 K^-0.5 | 110/102 | 23.28 | 20.34 | 1.145 | E 27.14 | 1.334 |
| B72 K^-0.5 | 106/106 | 25.98 | 22.51 | 1.154 | E 30.10 | 1.337 |
| B72 K^-0.5 | 110/102 | 25.73 | 22.78 | 1.129 | E 30.11 | 1.322 |
| B96 K^-0.5 | 106/106 | 33.81 | 29.68 | 1.139 | E 39.86 | 1.343 |
| B96 K^-0.5 | 110/102 | 33.49 | 29.73 | 1.126 | E 39.71 | 1.336 |
| B127 K^-0.5 | 106/106 | 43.67 | 38.25 | 1.142 | E 52.96 | 1.385 |
| B127 K^-0.5 | 110/102 | 43.18 | 38.10 | 1.133 | E 52.94 | 1.390 |
| B128 K^-0.5 | 106/106 | 44.03 | 38.54 | 1.142 | E 53.89 | 1.398 |
| B128 K^-0.5 | 110/102 | 43.65 | 38.65 | 1.129 | E 53.95 | 1.396 |
| B256 K^-0.5 | 106/106 | 83.66 | 74.13 | 1.129 | E 107.03 | 1.444 |
| B256 K^-0.5 | 110/102 | 83.35 | 73.92 | 1.128 | E 107.30 | 1.452 |
| B512 K^-0.5 | 106/106 | 162.77 | 144.79 | 1.124 | E 212.19 | 1.466 |
| B512 K^-0.5 | 110/102 | 162.31 | 144.38 | 1.124 | E 213.03 | 1.475 |
| B48 1.0 | 106/106 | 18.14 | 17.52 | 1.035 | E 20.74 | 1.184 |
| B48 1.0 | 110/102 | 17.94 | 17.44 | 1.029 | E 20.74 | 1.189 |
| B63 1.0 | 106/106 | 23.39 | 20.54 | 1.139 | E 26.38 | 1.284 |
| B63 1.0 | 110/102 | 23.10 | 20.42 | 1.131 | E 26.32 | 1.289 |
| B64 1.0 | 106/106 | 23.54 | 20.58 | 1.144 | E 27.15 | 1.319 |
| B64 1.0 | 110/102 | 23.34 | 20.75 | 1.125 | E 27.15 | 1.308 |
| B128 1.0 | 106/106 | 43.81 | 39.09 | 1.121 | E 53.54 | 1.370 |
| B128 1.0 | 110/102 | 43.56 | 39.30 | 1.108 | E 53.57 | 1.363 |

**Back-to-back, twin rows (B >= 48)**

| row | dies | FI main µs | PR µs | speedup vs FI main | best non-Cake
µs | speedup vs non-Cake |
|---|---|---:|---:|---:|---|---:|
| B48 K^-0.5 | 106/106 | 18.25 | 16.23 | 1.124 | E 22.56 | 1.390 |
| B48 K^-0.5 | 110/102 | 18.27 | 16.24 | 1.125 | E 22.55 | 1.389 |
| B56 K^-0.5 | 106/106 | 23.13 | 18.39 | 1.258 | E 26.28 | 1.429 |
| B56 K^-0.5 | 110/102 | 23.12 | 18.75 | 1.233 | E 26.26 | 1.401 |
| B63 K^-0.5 | 106/106 | 25.49 | 20.51 | 1.243 | E 29.29 | 1.428 |
| B63 K^-0.5 | 110/102 | 25.49 | 20.42 | 1.248 | E 29.27 | 1.433 |
| B64 K^-0.5 | 106/106 | 25.83 | 20.71 | 1.247 | E 29.69 | 1.434 |
| B64 K^-0.5 | 110/102 | 25.88 | 20.89 | 1.239 | E 29.67 | 1.420 |
| B72 K^-0.5 | 106/106 | 28.06 | 23.97 | 1.171 | E 32.85 | 1.370 |
| B72 K^-0.5 | 110/102 | 28.09 | 24.29 | 1.156 | E 32.87 | 1.353 |
| B96 K^-0.5 | 106/106 | 35.81 | 31.96 | 1.120 | E 42.52 | 1.330 |
| B96 K^-0.5 | 110/102 | 35.83 | 32.03 | 1.119 | E 42.44 | 1.325 |
| B127 K^-0.5 | 106/106 | 45.69 | 40.60 | 1.125 | E 56.30 | 1.387 |
| B127 K^-0.5 | 110/102 | 45.65 | 40.69 | 1.122 | E 56.11 | 1.379 |
| B128 K^-0.5 | 106/106 | 45.99 | 40.94 | 1.123 | E 57.24 | 1.398 |
| B128 K^-0.5 | 110/102 | 45.98 | 41.01 | 1.121 | E 57.25 | 1.396 |
| B256 K^-0.5 | 106/106 | 85.49 | 76.44 | 1.118 | E 109.94 | 1.438 |
| B256 K^-0.5 | 110/102 | 85.45 | 76.26 | 1.121 | E 110.12 | 1.444 |
| B512 K^-0.5 | 106/106 | 164.69 | 147.10 | 1.120 | E 213.64 | 1.452 |
| B512 K^-0.5 | 110/102 | 164.57 | 146.92 | 1.120 | E 213.94 | 1.456 |
| B48 1.0 | 106/106 | 18.45 | 16.10 | 1.146 | E 22.54 | 1.400 |
| B48 1.0 | 110/102 | 18.45 | 16.08 | 1.147 | E 22.53 | 1.401 |
| B63 1.0 | 106/106 | 25.57 | 21.14 | 1.210 | E 29.22 | 1.382 |
| B63 1.0 | 110/102 | 25.56 | 21.14 | 1.209 | E 29.13 | 1.378 |
| B64 1.0 | 106/106 | 25.84 | 21.42 | 1.206 | E 29.61 | 1.382 |
| B64 1.0 | 110/102 | 25.85 | 21.62 | 1.196 | E 29.63 | 1.370 |
| B128 1.0 | 106/106 | 46.07 | 41.47 | 1.111 | E 56.64 | 1.366 |
| B128 1.0 | 110/102 | 46.06 | 41.60 | 1.107 | E 56.71 | 1.363 |

**Rows below 48 (whole route)**

These rows run the same whole kernel as FI main; graph cells of
0.990–0.996x appear in a process that also homes twin rows, and the
other cells below 1.000 are within FI main's own run-to-run spread.

| row | dies | graph FI main µs | graph PR µs | speedup vs FI main |
graph best non-Cake µs | speedup vs non-Cake | b2b FI main µs | b2b PR
µs | speedup vs FI main | b2b best non-Cake µs | speedup vs non-Cake |
|---|---|---:|---:|---:|---|---:|---:|---:|---:|---|---:|
| B1 K^-0.5 | 106/106 | 2.80 | 2.80 | 1.000 | E 3.15 | 1.125 | 7.37 |
7.39 | 0.997 | D 9.37 | 1.268 |
| B1 K^-0.5 | 110/102 | 2.77 | 2.77 | 1.000 | E 3.14 | 1.134 | 7.36 |
7.57 | 0.972 | D 9.23 | 1.219 |
| B9 K^-0.5 | 106/106 | 6.29 | 6.34 | 0.992 | E 6.70 | 1.057 | 7.32 |
7.47 | 0.980 | D 9.22 | 1.234 |
| B9 K^-0.5 | 110/102 | 6.26 | 6.32 | 0.991 | E 6.70 | 1.060 | 7.31 |
7.43 | 0.984 | D 9.18 | 1.236 |
| B31 K^-0.5 | 106/106 | 12.99 | 12.99 | 1.000 | E 13.82 | 1.064 | 10.77
| 10.75 | 1.002 | D 19.27 | 1.793 |
| B31 K^-0.5 | 110/102 | 12.93 | 12.99 | 0.995 | E 13.73 | 1.057 | 10.79
| 10.79 | 1.000 | D 19.23 | 1.782 |
| B32 K^-0.5 | 106/106 | 13.38 | 13.41 | 0.998 | E 14.14 | 1.054 | 10.98
| 10.90 | 1.007 | D 17.46 | 1.602 |
| B32 K^-0.5 | 110/102 | 13.28 | 13.39 | 0.992 | E 14.08 | 1.052 | 10.95
| 10.89 | 1.006 | D 17.43 | 1.601 |
| B37 K^-0.5 | 106/106 | 14.67 | 14.70 | 0.998 | E 16.26 | 1.106 | 13.06
| 12.89 | 1.013 | D 20.10 | 1.559 |
| B37 K^-0.5 | 110/102 | 14.53 | 14.66 | 0.991 | E 16.22 | 1.106 | 13.12
| 12.99 | 1.010 | D 20.14 | 1.550 |
| B44 K^-0.5 | 106/106 | 16.80 | 16.77 | 1.002 | E 18.87 | 1.125 | 15.98
| 16.00 | 0.999 | E 20.85 | 1.303 |
| B44 K^-0.5 | 110/102 | 16.59 | 16.74 | 0.991 | E 18.85 | 1.126 | 15.99
| 16.00 | 0.999 | E 20.72 | 1.295 |
| B47 K^-0.5 | 106/106 | 17.73 | 17.70 | 1.002 | E 20.37 | 1.151 | 17.75
| 17.70 | 1.003 | E 22.00 | 1.243 |
| B47 K^-0.5 | 110/102 | 17.58 | 17.70 | 0.993 | E 20.30 | 1.147 | 17.74
| 17.70 | 1.002 | E 22.07 | 1.247 |
| B32 1.0 | 106/106 | 13.47 | 13.50 | 0.998 | E 14.18 | 1.050 | 11.11 |
10.90 | 1.019 | D 17.35 | 1.592 |
| B32 1.0 | 110/102 | 13.41 | 13.47 | 0.996 | E 14.11 | 1.048 | 11.11 |
10.91 | 1.018 | D 17.34 | 1.589 |
| B47 1.0 | 106/106 | 17.70 | 17.70 | 1.000 | E 20.38 | 1.151 | 17.92 |
17.85 | 1.004 | E 22.10 | 1.238 |
| B47 1.0 | 110/102 | 17.54 | 17.71 | 0.990 | E 20.35 | 1.149 | 17.95 |
17.86 | 1.005 | E 22.08 | 1.236 |

**Host time and single cold calls on twin rows**

Compared with FI main, a homed call spends +0.60 to +1.12 µs more host
time on the default stream and +1.30 to +1.58 µs more on a side stream.
A single cold eager call on the default stream is 1.2–2.0 % slower at
B48; from B56 on it is faster. On a side stream, a single cold call
spends +1.47 to +1.83 µs more host time. Its event time is 4.5–12.6 %
longer at B48, between 4.3 % shorter and 3.9 % longer at B64, and
shorter at B128. Back-to-back time per call is not slower on either
stream.
- host = host time per call over back-to-back eager calls.
- side stream = a non-default `torch.cuda.Stream`.
- cold, default stream = one eager call after an L2-flushing read and a
synchronize. It is timed either by CUDA events around the call
("events") or with CUPTI from call entry to the end of the call's last
kernel ("from the call").
- cold, side stream = one cold call on a side stream. It is timed either
by its host time ("host") or by CUDA events around it ("events").

| measure | row | 106/106 FI main → PR µs | speedup | 110/102 FI main →
PR µs | speedup |
|---|---|---|---:|---|---:|
| host, default stream | B48 K^-0.5 | 7.76 → 8.55 | 0.908 | 7.65 → 8.51
| 0.899 |
| host, default stream | B56 K^-0.5 | 7.65 → 8.43 | 0.907 | 7.57 → 8.37
| 0.904 |
| host, default stream | B63 K^-0.5 | 7.65 → 8.50 | 0.900 | 7.79 → 8.39
| 0.928 |
| host, default stream | B64 K^-0.5 | 7.58 → 8.52 | 0.890 | 7.65 → 8.53
| 0.897 |
| host, default stream | B72 K^-0.5 | 7.63 → 8.61 | 0.886 | 7.66 → 8.60
| 0.891 |
| host, default stream | B96 K^-0.5 | 7.64 → 8.54 | 0.895 | 7.68 → 8.68
| 0.885 |
| host, default stream | B127 K^-0.5 | 7.85 → 8.72 | 0.900 | 7.89 → 8.55
| 0.923 |
| host, default stream | B128 K^-0.5 | 7.64 → 8.73 | 0.875 | 7.80 → 8.66
| 0.901 |
| host, default stream | B256 K^-0.5 | 7.79 → 8.77 | 0.888 | 7.82 → 8.70
| 0.899 |
| host, default stream | B512 K^-0.5 | 7.97 → 8.99 | 0.887 | 8.00 → 8.99
| 0.890 |
| host, default stream | B48 1.0 | 7.59 → 8.39 | 0.905 | 7.62 → 8.48 |
0.899 |
| host, default stream | B63 1.0 | 7.65 → 8.59 | 0.891 | 7.71 → 8.59 |
0.898 |
| host, default stream | B64 1.0 | 7.57 → 8.69 | 0.871 | 7.52 → 8.58 |
0.876 |
| host, default stream | B128 1.0 | 7.79 → 8.79 | 0.886 | 7.71 → 8.77 |
0.879 |
| host, side stream | B48 K^-0.5 | 7.56 → 8.93 | 0.847 | 7.60 → 8.94 |
0.850 |
| host, side stream | B64 K^-0.5 | 7.59 → 9.07 | 0.837 | 7.60 → 9.03 |
0.842 |
| host, side stream | B128 K^-0.5 | 7.72 → 9.27 | 0.833 | 7.66 → 9.04 |
0.847 |
| host, side stream | B48 1.0 | 7.66 → 8.96 | 0.855 | 7.58 → 9.07 |
0.836 |
| host, side stream | B64 1.0 | 7.61 → 9.19 | 0.828 | 7.65 → 9.05 |
0.845 |
| host, side stream | B128 1.0 | 7.57 → 9.07 | 0.835 | 7.66 → 9.04 |
0.847 |
| cold call, default stream, events | B48 K^-0.5 | 26.62 → 27.10 | 0.982
| 26.49 → 27.02 | 0.980 |
| cold call, default stream, events | B48 1.0 | 26.54 → 26.91 | 0.986 |
26.76 → 27.08 | 0.988 |
| cold call, default stream, from the call | B48 K^-0.5 | 31.80 → 32.20
| 0.988 | 31.81 → 32.24 | 0.987 |
| cold call, default stream, from the call | B48 1.0 | 31.75 → 32.26 |
0.984 | 31.77 → 32.27 | 0.985 |
| cold call, side stream, host | B48 K^-0.5 | 8.70 → 10.24 | 0.850 |
8.76 → 10.30 | 0.850 |
| cold call, side stream, host | B64 K^-0.5 | 8.79 → 10.47 | 0.840 |
8.91 → 10.38 | 0.858 |
| cold call, side stream, host | B128 K^-0.5 | 8.76 → 10.59 | 0.827 |
8.90 → 10.41 | 0.855 |
| cold call, side stream, host | B48 1.0 | 8.87 → 10.38 | 0.855 | 8.90 →
10.38 | 0.857 |
| cold call, side stream, host | B64 1.0 | 8.89 → 10.40 | 0.855 | 8.92 →
10.42 | 0.856 |
| cold call, side stream, host | B128 1.0 | 8.82 → 10.35 | 0.852 | 8.86
→ 10.43 | 0.849 |
| cold call, side stream, events | B48 K^-0.5 | 26.41 → 28.26 | 0.935 |
26.42 → 27.62 | 0.957 |
| cold call, side stream, events | B64 K^-0.5 | 32.08 → 32.93 | 0.974 |
32.30 → 30.90 | 1.045 |
| cold call, side stream, events | B128 K^-0.5 | 52.26 → 51.12 | 1.022 |
52.56 → 51.02 | 1.030 |
| cold call, side stream, events | B48 1.0 | 26.66 → 30.02 | 0.888 |
26.66 → 29.89 | 0.892 |
| cold call, side stream, events | B64 1.0 | 32.02 → 33.27 | 0.962 |
32.07 → 32.33 | 0.992 |
| cold call, side stream, events | B128 1.0 | 52.51 → 51.41 | 1.021 |
52.50 → 51.55 | 1.018 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional state localization for supported GDN decode workloads
on dual-die SM107a GPUs.
* Eligible non-transposed FP32, single-token decodes can use a
locality-aware kernel. Unsupported configurations continue to use the
existing whole-GPU path.
* Documented supported workloads, state placement, and CUDA graph
capture requirements.

* **Bug Fixes**
* Added fallback to the existing decode path if the locality-aware
launch fails.

* **Tests**
* Added coverage for result equivalence, dispatch, fallback behavior,
state placement, and CUDA graph capture.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [855eece](https://github.com/flashinfer-ai/flashinfer/commit/855eece4e9b5b796a46148664a3e27da571cd98b)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-19T04:24:23Z
- **提交信息**: feat(batch_invariant): batch-invariant top-k / top-p / min-p sampling (#9619)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Third batch-invariant sampling PR. 
- `flashinfer.sampling.top_k_sampling_from_probs(probs, top_k, ...,
batch_invariant=True)`,
- `top_p_sampling_from_probs(probs, top_p, ...)`, 
- `min_p_sampling_from_probs(probs, min_p, ...)`,
- `top_k_top_p_sampling_from_probs(probs, top_k, top_p, indices,
filter_apply_order, ...)` and
- `top_k_top_p_sampling_from_logits(logits, top_k, top_p, indices,
filter_apply_order, ...)`
draw one token per row from the kept set of the row's filters with a
specified, fingerprinted dataflow whose bits depend on the row's own
values, its parameters and its `(seed, offset)` key alone -- never on
the row's slot, the batch size or the kernel configuration. Without the
flag the five entries are unchanged. The operators' own
`deterministic=True` kernels are run-to-run deterministic but key their
Philox stream by the batch slot, so a row's token moves with its
position (the probe in
`test_batch_invariance_the_way_the_operator_was_probed` prints the
count); under the flag it does not.

Training forward support: `log_probs(logits, token_ids, temperature,
batch_invariant=True, top_k=, top_p=, min_p=, filter_apply_order=)`
gives the log-probability of a given token under the sampler's kept-set
distribution

### Performance

Method: `flashinfer.testing.bench_gpu_time(enable_cupti=True,
cold_l2_cache=True, use_cuda_graph=False)`, median; N {32768, 128256,
152064} x M {1, 8, 64, 512, 4096}, the softmax of `randn * 2` logits
(the operator's own probe rows), `k = 40` / `p = 0.9` / `min_p = 0.05`,
one key per row on both paths; the flag on bf16 and fp32 rows against
the operator's deterministic kernels (`deterministic=True`, the default)
on fp32 rows (`bench/bench_fi_sampling_draw_support.py` of the sandbox).
Ratios are `default / ours` (above 1 the flag is faster), the geomean
over the three vocabularies with the minimum in parentheses; decode M
{1, 8}, mid M 64, prefill M {512, 4096}.

**Rubin NVL8 (SM107)**

| entry | bf16 decode | bf16 mid | bf16 prefill | f32 decode | f32 mid |
f32 prefill |
|---|---|---|---|---|---|---|
| `top_k_sampling_from_probs` | 3.03x (min 1.00x) | 3.76x (min 1.72x) |
2.03x (min 1.29x) | 2.80x (min 0.83x) | 2.52x (min 1.72x) | 0.98x (min
0.76x) |
| `top_p_sampling_from_probs` | 1.58x (min 0.99x) | 0.84x (min 0.79x) |
0.28x (min 0.13x) | 1.08x (min 0.74x) | 0.61x (min 0.46x) | 0.17x (min
0.08x) |
| `min_p_sampling_from_probs` | 2.60x (min 1.55x) | 1.85x (min 1.37x) |
0.95x (min 0.49x) | 2.36x (min 1.40x) | 0.89x (min 0.51x) | 0.31x (min
0.24x) |
| `top_k_top_p_sampling_from_probs` | 1.48x (min 0.97x) | 1.64x (min
1.18x) | 2.36x (min 1.70x) | 1.38x (min 0.82x) | 1.12x (min 0.93x) |
1.38x (min 0.86x) |
| `top_k_top_p_sampling_from_logits` | 2.20x (min 1.17x) | 2.19x (min
1.42x) | 2.89x (min 1.98x) | 2.10x (min 1.08x) | 1.63x (min 1.38x) |
1.85x (min 1.16x) |

Regime geomeans over the five entries (default / ours; min): bf16 decode
2.10x (0.97x), mid 1.84x (0.79x), prefill 1.30x (0.13x); f32 decode
1.83x (0.74x), mid 1.20x (0.46x), prefill 0.66x (0.08x).

**B200 (SM100)**

| entry | bf16 decode | bf16 mid | bf16 prefill | f32 decode | f32 mid |
f32 prefill |
|---|---|---|---|---|---|---|
| `top_k_sampling_from_probs` | 3.51x (min 1.17x) | 4.43x (min 2.54x) |
2.24x (min 1.30x) | 3.26x (min 1.02x) | 2.90x (min 1.96x) | 1.23x (min
0.62x) |
| `top_p_sampling_from_probs` | 1.27x (min 0.90x) | 0.75x (min 0.51x) |
0.28x (min 0.11x) | 0.88x (min 0.63x) | 0.48x (min 0.27x) | 0.15x (min
0.06x) |
| `min_p_sampling_from_probs` | 2.37x (min 1.65x) | 1.49x (min 1.13x) |
0.80x (min 0.39x) | 2.15x (min 1.52x) | 1.02x (min 0.67x) | 0.40x (min
0.19x) |
| `top_k_top_p_sampling_from_probs` | 1.68x (min 1.12x) | 2.29x (min
1.35x) | 2.38x (min 1.54x) | 1.67x (min 1.01x) | 1.49x (min 0.98x) |
1.33x (min 0.76x) |
| `top_k_top_p_sampling_from_logits` | 2.29x (min 1.47x) | 2.82x (min
1.65x) | 2.67x (min 1.68x) | 2.21x (min 1.44x) | 1.85x (min 1.21x) |
1.57x (min 0.87x) |

Regime geomeans over the five entries (default / ours; min): bf16 decode
2.10x (0.90x), mid 2.00x (0.51x), prefill 1.26x (0.11x); f32 decode
1.87x (0.63x), mid 1.31x (0.27x), prefill 0.69x (0.06x).

#### Against what is used by frameworks today 
What the frameworks call today (vLLM, SGLang and Megatron-LM inference
for the rollout; ver, Miles and NeMo RL for the trainer; read from their
checkouts): vLLM's sampler takes an fp32 copy of the logits, divides the
temperature in place, pre-masks min-p to `-inf` and calls the operator's
`top_k_top_p_sampling_from_logits(logits, k, p, deterministic=True)`
with per-row int32 `k` (the vocabulary size when off) and `p` (1.0 when
off), no seed / offset; its fallbacks are a Triton exact-k kernel or a
pure-torch sort (`apply_top_k_top_p_pytorch`) plus a Gumbel-max draw;
its `processed_logprobs` is the kept-set value. SGLang takes fp32
probabilities from a fused softmax and calls
`top_k_top_p_sampling_from_probs(probs, ks, ps,
filter_apply_order="joint")` (sentinels `1 << 30` / `1.0` / `0`), min-p
through the renorm entries; its deterministic mode leaves FlashInfer for
a torch sort + cumsum backend; its `token_logprobs` is the unfiltered
value. Megatron-LM inference runs the same four-way dispatch with
`deterministic=True` and a generator. On the trainer side NeMo RL
re-applies the filters itself (`apply_top_k_top_p`: ties kept, top-k
first) before `log_softmax` + gather, verl re-scores the full
vocabulary, Miles replays SGLang's sampling mask. The flagged entries
take these call shapes as they stand: the sentinels keep everything or
are no-ops, pre-masked `-inf` logits have zero weight, SGLang's order is
`filter_apply_order="joint"`, `return_kept_logprob` is vLLM's processed
value and `return_logprob` SGLang's `token_logprobs`, and
`log_probs(..., top_k=, top_p=)` is NeMo RL's recompute in one launch.
Two things to know: an engine must pass the row's `(seed, offset)` (none
does today), and ties at a top-p cut are kept whole (the kept set is
upward-closed) where vLLM's torch fallback splits a tie group by sort
order -- on bf16 logits (ties among the top 40 of every row) the two
kept sets differ at the boundary in about half the rows (the processed
log-probability by up to 0.1 nat there, 1 % of our drawn tokens outside
its set); on fp32 logits without ties every drawn token lies in its kept
set and the log-probabilitiels agree to 7e-7.

Rubin NVL8 (SM107), the rollout call (ours =
`top_k_top_p_sampling_from_logits(x_bf16, k, p, seed=, offset=,
batch_invariant=True)`: 18-35 us at M <= 8, 0.40 / 1.75 / 4.16 ms at M =
4096 for the three vocabularies):

| path | geomean | min | max | decode (M <= 8) | mid (M = 64) | prefill
(M >= 512) |
|---|---|---|---|---|---|---|
| ours + both log-probabilities | 1.11 | 1.01 | 1.25 | 1.09 | 1.10 |
1.14 |
| ours on fp32 logits | 1.33 | 1.01 | 1.93 | 1.07 | 1.40 | 1.60 |
| vLLM: fp32 copy + FlashInfer fused (deterministic=True) | 4.50 | 2.89
| 7.12 | 4.61 | 4.17 | 4.55 |
| vLLM: torch fallback (sort) + Gumbel-max | 18.67 | 6.77 | 44.54 |
10.50 | 21.42 | 30.99 |
| SGLang: fp32 softmax + FlashInfer fused (joint) | 4.56 | 2.19 | 9.41 |
4.84 | 5.30 | 3.97 |
| SGLang: torch backend (sort + cumsum + multinomial) | 19.06 | 7.31 |
40.80 | 11.91 | 22.67 | 27.97 |
| vLLM fused over ours, both on fp32 logits | 3.39 | 1.65 | 5.68 | 4.31
| 2.98 | 2.84 |
| SGLang fused over ours, both on fp32 logits | 3.44 | 1.44 | 7.44 |
4.52 | 3.80 | 2.48 |

Rubin NVL8 (SM107), the trainer-side value (ours = `log_probs(x_bf16,
ids, batch_invariant=True, top_k=k, top_p=p)`: 12-21 us at M <= 8, 0.21
/ 0.91 / 2.24 ms at M = 4096 for the three vocabularies):

| path | geomean | min | max | decode (M <= 8) | mid (M = 64) | prefill
(M >= 512) |
|---|---|---|---|---|---|---|
| ours: log_probs without filters | 0.19 | 0.11 | 0.27 | 0.21 | 0.23 |
0.15 |
| NeMo RL: apply_top_k_top_p + log_softmax + gather | 21.31 | 7.86 |
58.74 | 11.36 | 21.85 | 39.47 |
| torch: log_softmax + gather (no filter) | 1.67 | 0.87 | 3.10 | 1.35 |
1.37 | 2.30 |

B200 (SM100), the rollout call (ours =
`top_k_top_p_sampling_from_logits(x_bf16, k, p, seed=, offset=,
batch_invariant=True)`: 15-49 us at M <= 8, 0.38 / 1.69 / 3.98 ms at M =
4096 for the three vocabularies):

| path | geomean | min | max | decode (M <= 8) | mid (M = 64) | prefill
(M >= 512) |
|---|---|---|---|---|---|---|
| ours + both log-probabilities | 1.13 | 1.07 | 1.21 | 1.12 | 1.10 |
1.16 |
| ours on fp32 logits | 1.43 | 1.01 | 2.63 | 1.09 | 1.65 | 1.75 |
| vLLM: fp32 copy + FlashInfer fused (deterministic=True) | 3.88 | 2.12
| 6.94 | 4.01 | 4.40 | 3.53 |
| vLLM: torch fallback (sort) + Gumbel-max | 15.43 | 6.68 | 32.13 | 8.70
| 20.31 | 23.86 |
| SGLang: fp32 softmax + FlashInfer fused (joint) | 3.81 | 1.70 | 7.74 |
4.28 | 5.14 | 2.92 |
| SGLang: torch backend (sort + cumsum + multinomial) | 16.32 | 7.04 |
33.00 | 9.78 | 22.05 | 23.41 |
| vLLM fused over ours, both on fp32 logits | 2.71 | 1.09 | 4.96 | 3.67
| 2.66 | 2.02 |
| SGLang fused over ours, both on fp32 logits | 2.66 | 0.87 | 5.48 |
3.92 | 3.11 | 1.67 |

B200 (SM100), the trainer-side value (ours = `log_probs(x_bf16, ids,
batch_invariant=True, top_k=k, top_p=p)`: 15-48 us at M <= 8, 0.37 /
1.57 / 3.82 ms at M = 4096 for the three vocabularies):

| path | geomean | min | max | decode (M <= 8) | mid (M = 64) | prefill
(M >= 512) |
|---|---|---|---|---|---|---|
| ours: log_probs without filters | 0.18 | 0.12 | 0.27 | 0.19 | 0.25 |
0.15 |
| NeMo RL: apply_top_k_top_p + log_softmax + gather | 17.36 | 7.87 |
41.10 | 9.39 | 22.34 | 28.30 |
| torch: log_softmax + gather (no filter) | 1.20 | 0.83 | 1.81 | 1.08 |
1.19 | 1.34 |

## 🔍 Related Issues

<!-- Link any related issues here -->

#9009

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Summary

* **New Features**
* Added batch-invariant top-k, top-p, and min-p sampling for probability
and logits inputs, including combined filters with configurable order.
* Added filtered log-probability scoring, with excluded tokens assigned
negative infinity, and optional full-distribution or kept-set
log-probability outputs.
* Added validity and kept-mass results, caller-provided output buffers,
and temperature scaling for supported logits sampling. Invalid rows
return token `-1`.
* **Documentation**
* Expanded guidance on filtered sampling, scoring, and filter
parameters.
* **Tests**
* Added coverage for filtering behavior, edge cases, output options, and
sampling consistency.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9e6fb32](https://github.com/flashinfer-ai/flashinfer/commit/9e6fb322fce82f9a4a8a538328060c78ad6e1c22)

- **作者**: eigen
- **时间**: 2026-11-19T02:44:28Z
- **提交信息**: fix(moe): Cake warp-decode MoE kernels drop out-of-range expert ids in-kernel (#9682)

The Cake warp-decode NVFP4 routed-MoE decode kernels in FlashInfer's
fused MoE (FC1, FC2 and finalize; BF16 activations/output, NVFP4
weights) come in 31 variants: 16 expert geometries on `sm_100a` and 15
on `sm_103a`. This PR updates all 31 so they drop out-of-range expert
ids (for example -1 padding) inside the kernel. Compared with the
previous Cake kernels on FlashInfer main, these kernels are at parity or
slower. Speedup (main/PR) is 0.85x–1.01x on B200 and 0.85x–1.00x on
GB300, and the PR is up to ~18% slower at T=1–2 on some geometries.
Latency is end-to-end Cake MoE layer time, autotuned. It was measured
with CUPTI kernel time over CUDA-graph replay with cold L2 and is the
median of 3 medians. Values below 1.00x mean this PR is slower.

The family has no other Cake variants outside this PR; it ships on
`sm_100a` (16 geometries, including the DeepSeek-V4 ones) and `sm_103a`
(15 geometries).

**B200 (Blackwell, `sm_100a`), CUDA 13.5**

| Geometry (experts / intermediate / top-k) | Tokens | main (us) | this
PR (us) | speedup (main/PR) |
|---|---:|---:|---:|---:|
| E=60, I=1536, k=4 | 1 | 11.87 | 12.74 | 0.93x |
| E=60, I=1536, k=4 | 2 | 15.07 | 16.96 | 0.89x |
| E=60, I=1536, k=4 | 4 | 19.68 | 21.54 | 0.91x |
| E=60, I=1536, k=4 | 8 | 30.34 | 33.22 | 0.91x |
| E=60, I=1536, k=4 | 16 | 40.48 | 43.42 | 0.93x |
| E=60, I=1536, k=4 | 32 | 49.92 | 49.98 | 1.00x |
| E=512, I=512, k=10 | 1 | 12.22 | 12.48 | 0.98x |
| E=512, I=512, k=10 | 2 | 15.30 | 16.29 | 0.94x |
| E=512, I=512, k=10 | 4 | 20.35 | 21.18 | 0.96x |
| E=512, I=512, k=10 | 8 | 29.70 | 29.79 | 1.00x |
| E=512, I=512, k=10 | 16 | 45.63 | 48.35 | 0.94x |
| E=512, I=512, k=10 | 32 | 82.18 | 87.62 | 0.94x |
| E=256, I=1536, k=8 | 1 | 17.57 | 20.74 | 0.85x |
| E=256, I=1536, k=8 | 2 | 25.70 | 29.22 | 0.88x |
| E=256, I=1536, k=8 | 4 | 43.46 | 43.52 | 1.00x |
| E=256, I=1536, k=8 | 8 | 73.50 | 73.54 | 1.00x |
| E=256, I=1536, k=8 | 16 | 115.39 | 118.75 | 0.97x |
| E=256, I=1536, k=8 | 32 | 180.35 | 184.32 | 0.98x |
| E=256, I=512, k=8 | 1 | 11.68 | 11.62 | 1.01x |
| E=256, I=512, k=8 | 2 | 14.14 | 14.21 | 1.00x |
| E=256, I=512, k=8 | 4 | 17.44 | 17.86 | 0.98x |
| E=256, I=512, k=8 | 8 | 24.10 | 26.59 | 0.91x |
| E=256, I=512, k=8 | 16 | 36.73 | 37.47 | 0.98x |
| E=256, I=512, k=8 | 32 | 52.48 | 53.15 | 0.99x |
| E=128, I=768, k=8 | 1 | 12.19 | 12.86 | 0.95x |
| E=128, I=768, k=8 | 2 | 16.51 | 16.32 | 1.01x |
| E=128, I=768, k=8 | 4 | 20.22 | 20.67 | 0.98x |
| E=128, I=768, k=8 | 8 | 29.28 | 31.04 | 0.94x |
| E=128, I=768, k=8 | 16 | 39.07 | 42.11 | 0.93x |
| E=128, I=768, k=8 | 32 | 51.49 | 54.50 | 0.94x |
| E=128, I=1536, k=8 | 1 | 20.29 | 23.97 | 0.85x |
| E=128, I=1536, k=8 | 2 | 31.39 | 35.81 | 0.88x |
| E=128, I=1536, k=8 | 4 | 48.58 | 49.02 | 0.99x |
| E=128, I=1536, k=8 | 8 | 85.41 | 85.86 | 0.99x |
| E=128, I=1536, k=8 | 16 | 115.94 | 120.22 | 0.96x |
| E=128, I=1536, k=8 | 32 | 166.56 | 170.91 | 0.97x |
| E=896, I=3072, k=16 | 1 | 58.94 | 59.46 | 0.99x |
| E=896, I=3072, k=16 | 2 | 103.36 | 104.26 | 0.99x |
| E=896, I=3072, k=16 | 4 | 187.97 | 188.74 | 1.00x |
| E=896, I=3072, k=16 | 8 | 355.39 | 357.04 | 1.00x |
| E=896, I=3072, k=16 | 16 | 692.80 | 696.15 | 1.00x |
| E=896, I=3072, k=16 | 32 | 1357.41 | 1371.52 | 0.99x |

**GB300 (Blackwell Ultra, `sm_103a`), CUDA 13.5**

| Geometry (experts / intermediate / top-k) | Tokens | main (us) | this
PR (us) | speedup (main/PR) |
|---|---:|---:|---:|---:|
| E=60, I=1536, k=4 | 1 | 11.46 | 12.22 | 0.94x |
| E=60, I=1536, k=4 | 2 | 14.78 | 14.78 | 1.00x |
| E=60, I=1536, k=4 | 4 | 19.65 | 21.66 | 0.91x |
| E=60, I=1536, k=4 | 8 | 29.47 | 31.20 | 0.94x |
| E=60, I=1536, k=4 | 16 | 39.04 | 41.09 | 0.95x |
| E=60, I=1536, k=4 | 32 | 48.80 | 51.17 | 0.95x |
| E=512, I=512, k=10 | 1 | 11.81 | 12.93 | 0.91x |
| E=512, I=512, k=10 | 2 | 13.70 | 15.71 | 0.87x |
| E=512, I=512, k=10 | 4 | 19.65 | 21.60 | 0.91x |
| E=512, I=512, k=10 | 8 | 28.38 | 30.27 | 0.94x |
| E=512, I=512, k=10 | 16 | 45.98 | 48.96 | 0.94x |
| E=512, I=512, k=10 | 32 | 82.72 | 87.74 | 0.94x |
| E=256, I=1536, k=8 | 1 | 16.86 | 19.94 | 0.85x |
| E=256, I=1536, k=8 | 2 | 25.22 | 28.29 | 0.89x |
| E=256, I=1536, k=8 | 4 | 42.91 | 45.57 | 0.94x |
| E=256, I=1536, k=8 | 8 | 77.70 | 80.22 | 0.97x |
| E=256, I=1536, k=8 | 16 | 124.32 | 127.10 | 0.98x |
| E=256, I=1536, k=8 | 32 | 187.20 | 190.21 | 0.98x |
| E=256, I=512, k=8 | 1 | 11.01 | 11.58 | 0.95x |
| E=256, I=512, k=8 | 2 | 13.41 | 13.98 | 0.96x |
| E=256, I=512, k=8 | 4 | 15.90 | 17.76 | 0.90x |
| E=256, I=512, k=8 | 8 | 23.01 | 25.12 | 0.92x |
| E=256, I=512, k=8 | 16 | 36.03 | 38.46 | 0.94x |
| E=256, I=512, k=8 | 32 | 51.14 | 53.71 | 0.95x |
| E=128, I=768, k=8 | 1 | 11.81 | 12.51 | 0.94x |
| E=128, I=768, k=8 | 2 | 14.85 | 16.38 | 0.91x |
| E=128, I=768, k=8 | 4 | 20.00 | 21.66 | 0.92x |
| E=128, I=768, k=8 | 8 | 28.19 | 30.66 | 0.92x |
| E=128, I=768, k=8 | 16 | 39.26 | 41.15 | 0.95x |
| E=128, I=768, k=8 | 32 | 49.76 | 52.51 | 0.95x |
| E=128, I=1536, k=8 | 1 | 19.65 | 22.66 | 0.87x |
| E=128, I=1536, k=8 | 2 | 30.14 | 33.70 | 0.89x |
| E=128, I=1536, k=8 | 4 | 52.22 | 55.18 | 0.95x |
| E=128, I=1536, k=8 | 8 | 84.06 | 87.01 | 0.97x |
| E=128, I=1536, k=8 | 16 | 129.50 | 132.93 | 0.97x |
| E=128, I=1536, k=8 | 32 | 170.40 | 174.02 | 0.98x |
| E=896, I=3072, k=16 | 1 | 58.85 | 58.98 | 1.00x |
| E=896, I=3072, k=16 | 2 | 104.38 | 104.96 | 0.99x |
| E=896, I=3072, k=16 | 4 | 193.66 | 194.50 | 1.00x |
| E=896, I=3072, k=16 | 8 | 372.67 | 374.34 | 1.00x |
| E=896, I=3072, k=16 | 16 | 726.70 | 730.14 | 1.00x |
| E=896, I=3072, k=16 | 32 | 1432.48 | 1441.25 | 0.99x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Cake warp-decode can now be considered automatically as a default
backend when it is eligible and faster than earlier options. Automatic
selection can be disabled with an environment setting.
* Added public autotuner utilities for checking Cake candidate
availability and group-tuning status.
* Cake can fall back to another backend when it is ineligible or its
kernel module cannot be loaded.
* **Bug Fixes**
* Out-of-range expert IDs are ignored, including their weights. Tokens
with no valid routes produce zero output.
* **Documentation**
* Clarified backend selection, routing behavior, and CUDA Graph
workspace warmup requirements, including that unseen workspace shapes
are rejected during capture.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [dc22dd5](https://github.com/flashinfer-ai/flashinfer/commit/dc22dd5b300ddfc0806a673feae8c81dc2ec9562)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-19T02:00:41Z
- **提交信息**: fix(jit): match object paths to Ninja output names (#9681)

<!-- .github/pull_request_template.md -->

## 📌 Description

`get_object_paths()` omits the source-directory prefix used by Ninja, so
MLC compilation tries to link object files that do not exist. Return the
existing prefixed filenames.

## 🔍 Related Issues

Addresses the getter mismatch also covered by #6038, without its
collision-handling changes.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually for the changed files and fixed any
reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

The four CPU regression cases fail before the fix and pass afterward.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Only the object-path getter changes.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra/test_jit_object_paths.py`

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

AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Build outputs now distinguish source files with the same name in
different directories, helping prevent object-file conflicts. CUDA and
C++ object file types remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [03288fe](https://github.com/flashinfer-ai/flashinfer/commit/03288fe1e07993055c63c0184c54521ccf995cb0)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-19T01:36:49Z
- **提交信息**: perf(batch_invariant): cut the host launch overhead of the batch-invariant GEMM entries (bit-identical) (#9620)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

A decode-shaped call of the public GEMM entries under
`batch_invariant=True` (`mm_bf16`, `bmm_fp8`, `mm_fp4`, `mm_mxfp8`,
`gemm_fp8_nt_groupwise`, `mm_mxfp8_mxfp4`) spent 37 to 60 us on the host
against 4 to 16 us of kernel time. After #8598 removed the backend
selection, what remained was in our own path. This PR removes five
host-side costs; no kernel, record space, dispatcher rule or autotuning
behaviour changes, so every call runs the same configuration of the same
compiled kernel on the same operand views and the output bits are
identical (checked eager, under graph replay, untuned and tuned, on both
parts).

1. **The autotuner lookup runs only where it can hit.** In a process
that never tuned the op, `AutoTuner.choose_one` takes the lock, buckets
the shape and searches every cache source, then returns the fallback:
the dispatcher's pick. A private helper, `AutoTuner._has_tune_data(op)`,
says whether any source could answer (tuning mode, replay diagnostics, a
managed store, bundled or loaded configs, an in-memory winner of the
op); where it is False the entries take the dispatcher's pick directly,
where it is True they call `choose_one` exactly as before.
2. **The operands are validated once.** The autotuner entries validated
the operands and then re-entered the public class entry, which validated
them again. The class entries' launches are now private functions on
prepared operands, and the autotuner entries hand them the prepared
operands with the runner's configuration. The class entries are
unchanged for direct callers and remain what the autotuner profiles;
every refusal is raised by the same check with the same message.
3. **The dispatcher's pick is memoised.** `default_config` rebuilt the
ranked list on every call and `enumerate_space` re-filtered the knob
product on every ranking miss. Both are memoised on their full argument
tuples (shape, chunks, layout, SM count, family, format), bounded,
returning copies; the memos clear together with the rankings whenever a
device's registered numbers change. A device-free test checks the
memoised pick against the fresh computation over a grid of shapes on
every part.
4. **The aliasing check is skipped for the entry's own output.**
`_require_disjoint` compared the output's byte span against every
operand before each launch. An output the entry allocated in the same
call aliases nothing, so that case is skipped; every caller-provided
output and workspace is checked as before, and each suite refuses a
caller's output over an operand's bytes through the public API.
5. **One pass over the operands, cached launch handles.** Strides and
bases are read once instead of per helper, the weight's kernel view is
derived from the API's layout instead of viewed twice, a flat scale
buffer is handed over as is, the record's acceptance is memoised, and
the compiled kernel is cached per (device index, record, compile
parameters) once the device's persistent grid is final.

Not touched: the kernels, the record spaces and chunk rule, the ranking
heuristic and its constants, the autotuner's profiling and cache
semantics, the class entries' contract, and the MoE backends that share
the engine (their suites are in the gates).

### Performance

Host side only; the kernels are unchanged. Public API with
`batch_invariant=True`, 1000 calls in a loop with one synchronize at the
end, host us per call = the loop's wall before the synchronize, median
of 5 repeats; kernel us from `torch.profiler` device durations; one
process per measurement, warm JIT cache, Rubin (sm_107) with no other
process on the GPU. BEFORE is upstream `main` at 778f57e4d, AFTER is
this branch. Graph-replay time per call (5 to 18 us) is unchanged, as
are the GPU-bound prefill rows; both are in the long form of this
description with the full attribution tables.

**Summary: public API host time per call at M = 1, N x K = 4096x4096**
(kernel time for scale; it is unchanged).

| entry (batch-invariant class) | host us before | host us after |
kernel us |
|---|---|---|---|
| mm_bf16 (bf16) | 37.7 | 13.7 | 7.6 |
| bmm_fp8 b=1 (fp8 per-tensor) | 38.1 | 16.7 | 5.3 |
| mm_fp4 (NVFP4) | 57.5 | 20.3 | 4.1 |
| mm_mxfp8 (MXFP8) | 59.6 | 17.3 | 5.0 |
| gemm_fp8_nt_groupwise (fp8 block-scale) | 59.1 | 26.7 | 9.0 |
| mm_mxfp8_mxfp4 (mixed) | 36.4 | 17.2 | 3.9 |

**Per case** (M = 1 and 64 at 4096x4096, M = 1 at 8192x8192):

| entry (batch-invariant class) | M | N x K | host us before | host us
after | kernel us |
|---|---|---|---|---|---|
| mm_bf16 (bf16) | 1 | 4096x4096 | 37.7 | 13.7 | 7.6 |
| mm_bf16 (bf16) | 64 | 4096x4096 | 40.0 | 15.2 | 7.4 |
| mm_bf16 (bf16) | 1 | 8192x8192 | 39.6 | 14.7 | 16.3 |
| bmm_fp8 b=1 (fp8 per-tensor) | 1 | 4096x4096 | 38.1 | 16.7 | 5.3 |
| bmm_fp8 b=1 (fp8 per-tensor) | 64 | 4096x4096 | 39.0 | 17.6 | 5.4 |
| bmm_fp8 b=1 (fp8 per-tensor) | 1 | 8192x8192 | 38.6 | 16.7 | 8.9 |
| mm_fp4 (NVFP4) | 1 | 4096x4096 | 57.5 | 20.3 | 4.1 |
| mm_fp4 (NVFP4) | 64 | 4096x4096 | 57.7 | 20.1 | 5.2 |
| mm_fp4 (NVFP4) | 1 | 8192x8192 | 57.2 | 21.4 | 5.7 |
| mm_mxfp8 (MXFP8) | 1 | 4096x4096 | 59.6 | 17.3 | 5.0 |
| mm_mxfp8 (MXFP8) | 64 | 4096x4096 | 60.4 | 17.2 | 5.8 |
| mm_mxfp8 (MXFP8) | 1 | 8192x8192 | 53.5 | 17.3 | 7.4 |
| gemm_fp8_nt_groupwise (fp8 block-scale) | 1 | 4096x4096 | 59.1 | 26.7
| 9.0 |
| gemm_fp8_nt_groupwise (fp8 block-scale) | 64 | 4096x4096 | 57.4 | 28.0
| 7.8 |
| gemm_fp8_nt_groupwise (fp8 block-scale) | 1 | 8192x8192 | 63.9 | 26.5
| 15.7 |
| mm_mxfp8_mxfp4 (mixed) | 1 | 4096x4096 | 36.4 | 17.2 | 3.9 |
| mm_mxfp8_mxfp4 (mixed) | 64 | 4096x4096 | 37.1 | 17.2 | 5.0 |
| mm_mxfp8_mxfp4 (mixed) | 1 | 8192x8192 | 37.1 | 17.3 | 5.5 |

## 🔍 Related Issues

<!-- Link any related issues here -->

#9009

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

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
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Batch-invariant GEMM APIs now handle supported weight layouts
consistently and preserve results across direct calls and CUDA graph
replay.
  * Reject caller-provided output buffers that overlap input data.
* Improve tuning selection when tuning data is available, while avoiding
unnecessary lookups when it is not.

* **Performance**
* Cache GEMM dispatch rankings and configuration enumeration to reduce
repeated work.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [adef2ea](https://github.com/flashinfer-ai/flashinfer/commit/adef2ea3045d0a4695405a5fd7ebc1c830c5598f)

- **作者**: Akaash Parthasarathy
- **时间**: 2026-11-19T01:36:33Z
- **提交信息**: test(moe_ep): fix W8A16 guards and scalar reset expectations (#9671)

<!-- .github/pull_request_template.md -->

## 📌 Description

Skip W8A16 batch-invariant and outer-selection tests before input
preparation on CUDA toolkits older than 13. Update the W4A16
runtime-scalar test to expect configured defaults when overrides are
omitted.

## 🔍 Related Issues

Follow-up to #9454.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually for the changed files and fixed any
reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe_ep/test_a16_megamoe_batch_invariant.py
tests/moe_ep/test_blackwell_bi_outer_autoconfig.py
tests/moe_ep/test_nvfp4_cutedsl_kernel_vs_reference.py`

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

AI-assisted.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated test coverage to skip unsupported non-W4A16 cases when
required CUDA support is unavailable, with W8A16 tests indicating the
CUDA 13+ requirement. Supported W4A16 cases continue to run.
* Test setup now creates configurations before generating inputs,
including in autotune disk-reload coverage.
* Added checks confirming that omitting runtime overrides restores
configured defaults and produces output matching the default reference
exactly. These changes affect test execution and validation, not
user-facing application behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f369be4](https://github.com/flashinfer-ai/flashinfer/commit/f369be47343b72dae9155ed92996f7835c43aca0)

- **作者**: eigen
- **时间**: 2026-11-19T01:23:33Z
- **提交信息**: fix(cake_locality): keep the caller's thread state across devices, sync the freeing context, retry pools after a PyTorch memory-limit refusal (#9673)

### [58ed89d](https://github.com/flashinfer-ai/flashinfer/commit/58ed89d8bb0f31b6afa44fa3d2349f79910bb45b)

- **作者**: eigen
- **时间**: 2026-11-19T01:15:21Z
- **提交信息**: perf(cake_ssd_combined): state-slot claim and wrap programs on SM107 (#9679)

### [a591ec2](https://github.com/flashinfer-ai/flashinfer/commit/a591ec2375af7dddfe14d9909794b2c99a109cf4)

- **作者**: Hanjun Cho
- **时间**: 2026-11-19T01:03:38Z
- **提交信息**: feat(gemm): add a bias to bmm_fp8's cuBLAS backend (#8811)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds an optional `bias` (shape `(n,)`, output dtype) to `bmm_fp8`. The
cuBLAS backend applies it in the cuBLASLt bias epilogue, so a biased FP8
linear is one kernel instead of a GEMM plus an add, and autotuning ranks
the algos cuBLASLt lists for that epilogue.

- Only `backend="cublas"` takes a bias (`"auto"` resolves to it); the
other backends and `batch_invariant=True` raise `ValueError`, also with
`skip_check=True`.
- The bias must be contiguous and 16-byte aligned. cuBLASLt lists no FP8
algo otherwise, so anything else raises `ValueError`.
- Unbiased calls keep their runner inputs, tuning cache keys and trace
definition; outputs are bitwise unchanged. A biased call gets its own
trace definition (`bmm_fp8_bias_*`).

Motivation: SGLang's per-tensor FP8 linear adds the bias in a separate
kernel after `bmm_fp8` (sgl-project/sglang#44486).

RTX PRO 6000 (SM120), CUDA 13.0, torch 2.14.1. `bmm_fp8(bias=)` vs
`bmm_fp8` + add on 12 linear shapes x M 1 to 16384 x FP16/BF16 (264
points), `bench_gpu_time` with CUDA graph and cold L2:

| | PR / main, median | range | slower points |
|---|---|---|---|
| untuned | 0.74 | 0.55 to 0.98 | 0 / 264 |
| tuned | 0.74 | 0.51 to 0.98 | 0 / 264 |

<details><summary>Examples, tuned (µs)</summary>

| dtype | N x K | M | main | PR |
|---|---|---|---|---|
| FP16 | 1152 x 896 | 1 | 4.20 | 3.46 |
| BF16 | 3072 x 1024 | 64 | 5.49 | 3.85 |
| BF16 | 3072 x 1024 | 16384 | 280.70 | 160.57 |
| BF16 | 4608 x 3584 | 16384 | 904.56 | 731.91 |

</details>

SGLang end to end, bge-reranker-v2-m3 FP8, 128 x 320 tokens: GPU time
107.3 → 83.0 ms. Host time of an unbiased call: +0.2 µs
(`bench_host_overhead.py`, `bmm_fp8(cublas)` 21.27 → 21.48 µs).

## 🔍 Related Issues

#2290

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/gemm/test_bmm_fp8.py
tests/gemm/test_mm_fp8.py tests/autotuner/test_autotuner_bmm_fp8.py
tests/autotuner/test_autotuner_cublaslt_tactics.py
tests/trace/test_bmm_fp8_reference_correctness.py`

New: `test_bmm_fp8_bias`, `test_bmm_fp8_bias_rejected`,
`test_bmm_fp8_bias_tuning_key`, and a bias case in the trace reference
test. On SM120 they pass (the trace test with its SM100/SM103 skip
lifted locally), as do the existing `bmm_fp8`, `mm_fp8` and autotuner
tests and the 310 `bmm_fp8` fuzz cases.

## Reviewer Notes

`bmm_fp8_internal_cublaslt` now reuses `Fp8GemmDescriptors`, so the
epilogue is set in one place. The bias is appended to the runner inputs
only when given, which keeps the unbiased tuning cache keys; a biased
key also carries the bias alignment, which the cuBLASLt algorithms
depend on, and so does the C++ memo of the resolved descriptor (as in
the BF16 cuBLASLt runner).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added optional per-column bias support to FP8 batched matrix
multiplication with the cuBLAS backend. Bias must match the output dtype
and meet shape, contiguity, and alignment requirements.
- Bias is supported during algorithm selection, execution, and tracing.
Automatic backend selection routes biased calls to cuBLAS; other
backends and batch-invariant calls reject bias.
- **Tests**
- Added coverage for biased results, reference correctness, invalid bias
inputs, and bias-aware tuning behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [267030a](https://github.com/flashinfer-ai/flashinfer/commit/267030a9adb5d6303f2582bc3cd76bec7ee740a0)

- **作者**: Theodore-Liu
- **时间**: 2026-11-19T01:01:22Z
- **提交信息**: feat(gemm): opt-in flag to keep the SM120 FP4 GEMM autotuner off stream-K tactics (#7819)

## 📌 Description

On SM120, `CutlassFp4GemmRunner::getConfigs()`
(`fp4_gemm_cutlass_template_sm120.h`) gives each of the 8 tile shapes
four configs: two data-parallel and two stream-K. The autotuner sees all
32 tactics and picks by time. A stream-K tactic sums a tile's K range in
more than one CTA, so its output can differ in the last bits from the
data-parallel tactics of the same shape.

This matters when the choice changes between processes. In vLLM 0.32.0
(which re-tunes `fp4_gemm` at every start) serving Qwen3-8B-NVFP4 on an
RTX 5090, 8 fresh starts gave two different greedy outputs for the same
16 prompts. The start that differed was the only one that picked tactic
6 (128x32x128, stream-K) instead of tactic 4 (same tile, data-parallel)
for the attention output projection at M = 1. With all other tactic
choices fixed, switching only that entry between 4 and 6 moved the
output between the two versions in both directions.
vllm-project/vllm#62820 reports the same symptom on Qwen3.8-27B-NVFP4,
and an independent reproduction there (2026-10-26) traced it to the
autotuner moving one `fp4_gemm` call (M = 252, down projection) to
stream-K tactic 22; forcing tactic 21 (same tile, data-parallel)
restored the untuned output. That comment asks for "a way to keep
Stream-K tactics out of `fp4_gemm` tuning when reproducibility matters",
which is what this flag is; the workaround suggested there,
`VLLM_FLASHINFER_AUTOTUNE_SKIP_OPS=fp4_gemm`, gives up tuning among the
data-parallel tactics as well.

This PR adds `FLASHINFER_FP4_GEMM_DISABLE_STREAM_K`. When it is set to
1, the SM120 CUTLASS FP4 runner offers the autotuner only its 16
data-parallel tactics, and its new `validate_tactic` rejects a stream-K
tactic loaded from a saved autotune cache, so a cache written before the
flag was set cannot bring stream-K back. The autotuner treats such an
entry as a miss: during autotuning it re-tunes the entry, and outside
autotuning the call takes the untuned default (with `backend="cutlass"`,
the runner's default data-parallel config). The default is unchanged,
and the flag does not affect the SM100/SM103 runners. Any other value,
or no value, keeps all 32 tactics.

`validate_tactic` also rejects a cached tactic index outside the
runner's config list, for example one from a module with more configs.
Such an entry is re-tuned instead of reaching the C++ check. This range
check is in the factory the CUTLASS FP4 runners share, so it applies to
all of them. Each runner counts its configs once, since
`validate_tactic` runs on every cache hit.

Measured on an RTX 5090 with FlashInfer 0.7.0.post1 and the same change
applied, unless a row says otherwise:

| check | result |
|---|---|
| All 432 FP4 GEMM calls of a Qwen3-8B-NVFP4 generation, every tactic
run on vLLM's own operands | with the flag, the 16 offered tactics
return identical bits on every call; stream-K tactics differ from them
on 3 calls |
| vLLM greedy output over fresh starts, 16 prompts x 200 tokens |
default: 2 different outputs in 8 starts; with the flag: 1 output in 31
starts |
| Same, autotune cache emptied before each of 16 starts
(`VLLM_FLASHINFER_AUTOTUNE_CACHE_DIR`) | default: 2 outputs with
FlashInfer 0.7.0.post1 (the 16 starts split 9 and 7), 4 outputs with
0.7.2.post1; with the flag (this PR's branch built from source): 1
output in 16 starts, and none of the 16 saved caches holds a stream-K
tactic |
| vLLM generate time, same workload | 15.1-16.2 s with the flag,
15.6-17.4 s default (not a paired benchmark) |

## 🔍 Related Issues

vllm-project/vllm#62820 (symptom, independent root cause, and the
request for this option)

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

`tests/gemm/test_mm_fp4.py::test_mm_fp4_cutlass_sm120_disable_stream_k`
checks, at M = 1, 16 and 128 (skipped off SM12x), that with the flag the
runner offers only data-parallel tactics, that `validate_tactic` rejects
every excluded stream-K tactic and accepts the offered ones and the
default -1, and that every offered tactic returns the same bits as the
first. It also checks that `0`, an empty value, `false` and `true` keep
all tactics, that `1` keeps exactly half, and that an index past the
config list is rejected. At M = 16 and 128 it also requires some
stream-K tactic to differ from them on the generated operands, so the
bit-equality check is shown able to fail. All three cases pass on an RTX
5090 with this branch built from source, under CUDA 12.9 (PyTorch 2.13),
CUDA 13.0 (PyTorch 2.14) and CUDA 13.4 (PyTorch 2.16 nightly), after
merging main. pre-commit passes on the three changed files.

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

The filter relies on the config order in `getConfigs()` (index % 4 >= 2
is stream-K), which a comment next to
`_sm120_fp4_gemm_tactic_is_stream_k` points to. If you would rather
expose the stream-K bit from C++, or make the choice an `autotune()`
argument instead of an environment variable, I can change it.

---------

Signed-off-by: Jingze Liu <110184138+Theodore-Liu@users.noreply.github.com>

### [6018abf](https://github.com/flashinfer-ai/flashinfer/commit/6018abff613be3fc217d576fdddc8c9857555f19)

- **作者**: Adrian
- **时间**: 2026-11-19T00:41:52Z
- **提交信息**: perf: reuse FP4 compile workers during autotuning (#9327)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reuse FP4 compile workers across preparation batches within the
outermost `autotune(True)` context, avoiding repeated process startup
and CuTe/CUDA initialization. Pools are created lazily, inherited by
nested tuning contexts, and released on normal or exceptional exit.
Direct preparation keeps temporary pools. **The default remains four
workers.**

Complete cold-cache warmup of M=8 then M=128, N=K=8192, BF16 output,
scalar alpha, PDL, CuTe-DSL backend:

| Format | Temporary pools, 4 workers | Shared pools, 4 workers |
| --- | ---: | ---: |
| NVFP4 | 62.17 s | 34.39 s |
| MXFP4 | 62.91 s | 30.37 s |

Three-run medians from separate sessions on the same SM100 GPU (148 SMs,
reported name `NVIDIA Graphics Device`) and AMD EPYC 9124 host. Timing
includes compilation, profiling, output checks and pool teardown; parent
imports and input/reference construction are excluded. This measures API
warmup, not full vLLM startup. The GPU was not exclusive, so these
results should not be treated as a universal speedup.

## 🔍 Related Issues

Related workload/configuration investigation: #7036.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed, including mypy and Ruff. Hooks were run on
the five changed files rather than the entire repository.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

93 targeted CPU tests passed (`test_compile_resources.py`,
`test_autotuner_configs.py`, `test_tuning_protocol.py`). Across 18 GPU
shared-pool warmup trials, output, CUDA graph replay, and worker-cleanup
checks passed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/autotuner/ tests/gemm/test_mm_fp4.py`

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

Pools are keyed by device and effective worker count, preserving
existing per-batch sizing and the memory-based cap. Different effective
counts can retain separate pools until context exit. Kernel candidates
and numerical execution are unchanged. The four-worker default is
retained; a single shared 16-worker pool showed no clear advantage.

<details>
<summary>Reproduce the cold-warmup comparison</summary>

Save the following as `warmup_fp4.py`. Run each revision in a fresh
process with a new cache directory, without precompiled provider
packages, three times per format. Set `SF=16` for NVFP4 and `SF=32` for
MXFP4. The script exercises the same warmup and timing boundary as the
measurements above.

```python
import os
import tempfile
import time


def main():
    workspace = tempfile.mkdtemp(prefix="fp4-warmup-")
    os.environ["FLASHINFER_WORKSPACE_BASE"] = workspace
    os.environ["CUTE_DSL_CACHE_DIR"] = workspace + "/dsl-cache"
    os.environ["CUDA_CACHE_PATH"] = workspace + "/cuda-cache"
    os.environ["FLASHINFER_MM_FP4_CUTE_DSL_COMPILE_WORKERS"] = "4"
    import torch
    import flashinfer

    sf = int(os.environ.get("SF", "16"))
    n = k = 8192
    torch.manual_seed(7036)
    lut = torch.tensor(
        [0, .5, 1, 1.5, 2, 3, 4, 6, 0, -.5, -1, -1.5, -2, -3, -4, -6],
        device="cuda",
    )
    values = torch.tensor([0, 1, 2, 9, 10], dtype=torch.uint8, device="cuda")
    cb = values[torch.randint(0, len(values), (n, k), device="cuda")]
    b = (cb[:, ::2] | cb[:, 1::2] << 4).contiguous().T

    def scales(rows):
        return torch.full(
            (((rows + 127) // 128) * 128, k // sf),
            56 if sf == 16 else 127, dtype=torch.uint8, device="cuda",
        )

    sb = scales(n).T
    alpha = torch.tensor([.5], dtype=torch.float32, device="cuda")
    cases = []
    for m in (8, 128):
        ca = values[torch.randint(0, len(values), (m, k), device="cuda")]
        packed = (ca[:, ::2] | ca[:, 1::2] << 4).contiguous()
        reference = ((lut[ca.long()] @ lut[cb.long()].T) * .5).to(torch.bfloat16)
        cases.append((packed, scales(m), reference))
    torch.cuda.synchronize()
    start = time.perf_counter()
    with flashinfer.autotune(True):
        for packed, sa, reference in cases:
            with flashinfer.autotune(True):
                out = flashinfer.mm_fp4(
                    packed, b, sa, sb, alpha, out_dtype=torch.bfloat16,
                    block_size=sf, use_nvfp4=sf == 16, enable_pdl=True,
                    backend="cute-dsl",
                )
            torch.cuda.synchronize()
            torch.testing.assert_close(out, reference, rtol=0, atol=0)
    print(f"Complete warmup: {time.perf_counter() - start:.3f} s")


if __name__ == "__main__":
    main()
```

</details>

AI-assisted implementation and review.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Autotuning now reuses compilation workers across nested tuning
operations, reducing repeated worker setup.
* Compilation workers are released when the outermost tuning operation
finishes, including when an error occurs.
* Worker pools are created only when needed and remain consistent
throughout a tuning operation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4b01bc0](https://github.com/flashinfer-ai/flashinfer/commit/4b01bc0799671564240d4e5bb997d952fa0bd2aa)

- **作者**: Aniruddh Krovvidi
- **时间**: 2026-11-19T00:10:10Z
- **提交信息**: fix(decode): reject off-device metadata in fast_decode_plan (#6711)

<!-- .github/pull_request_template.md -->

## 📌 Description

`fast_decode_plan()` adopts `indptr` / `indices` / `last_page_len` as
the wrapper's metadata buffers without copying, so metadata on the host
or on another device reached the kernel as raw pointers and faulted with
an illegal memory access at the next synchronization, with nothing
pointing back at the cause. `plan()` accepts host metadata because it
copies it over; the fast path exists to skip that copy, so it now raises
a `ValueError` naming the tensor and the wrapper's device instead, as
`cake_dcp.py` and `xqa.py` do for the same class of input.

## 🔍 Related Issues

Fixes #6391

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (`pre-commit run --files
flashinfer/decode.py tests/attention/test_batch_decode_kernels.py`: all
hooks pass, including mypy, ruff check and ruff format.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Verified on 2x Tesla T4 (Kaggle, torch 2.11.0+cu128, upstream `53e3168`
plus this diff; the branch was then rebased onto current `main` with the
same 50-line diff and no conflicts), calling the new test function
directly:

```
BEFORE (decode.py at 53e3168):
cpu    -> FAIL: RuntimeError Error in standard plan: ... (metadata accepted, plan reached)
cuda:1 -> FAIL: RuntimeError Error in standard plan: ... (metadata accepted, plan reached)
AFTER (this diff):
cpu    -> PASS: ValueError raised before plan state changed
cuda:1 -> PASS: ValueError raised before plan state changed
```

Before the diff both off-device inputs are adopted and planning proceeds
(on that box the kernel module was never loaded, so it stops there; with
a loaded module they reach the kernel, which is #6391). After the diff
both are rejected at entry.

The test was invoked directly rather than through `pytest` because that
image cannot link the module's `warmup_jit` fixture (`ld: cannot find
-lcuda`, no `libcuda.so` stub); the fixture is unrelated to this change.
`test_fast_decode_plan_rejects_metadata_off_wrapper_device` itself
raises before any JIT build; its `cuda:1` case skips on a single-GPU
host.

## 🔬 Experimental Track

<!-- Not experimental. -->

## Reviewer Notes

- The check applies only outside CUDA graphs, where the passed tensors
become the wrapper's buffers. In CUDA-graph mode `run()` reads the
wrapper's own buffers and the passed `indptr` / `last_page_len` are
host-side planning inputs: vLLM's graph replay calls
`fast_decode_plan(..., indptr=indptr_cpu, ...,
last_page_len=last_page_len_cpu)`, which a graph-mode device check
rejects (`indptr must be on the wrapper's device cuda:0, got cpu`). The
second commit added that check after review; the third reverts it.
- It runs before any plan state is touched, so a rejected call leaves a
previously planned wrapper exactly as it was.
- `plan()` remains the path for host metadata; the docstring and the
error message say so.
- 15 production lines, 35 test lines. The branch's net diff equals the
first commit, which is the code the GPU evidence above was run on.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* `fast_decode_plan` now reports a clear error when metadata tensors are
on a different device than the wrapper, outside CUDA Graph mode. Use
`BatchDecodeWithPagedKVCacheWrapper.plan` when working with host
metadata.
* **Tests**
  * Added coverage for mismatched CPU and CUDA devices.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: watcher <watcher@example.invalid>
Co-authored-by: flashinfer-bot <flashinfer-bot@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4831
- **最后更新**: 2026-11-20T02:13:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yixing Wang

## AI分析总结

## 提交分析：[1fce9fb] Batch H3 vision frames with PyTorch varlen attention (#2050)

### 1. 主要更新类型
- **性能优化（[perf]）**，属于内部推理/训练加速层面的改进，无新增用户可见功能，也不涉及缺陷修复。

### 2. 关键变更点及与项目方向的关系
- 将 H3（层级化的第三层或特定阶段）处理中的 **vision frames 批处理**，改用 **PyTorch 的 varlen（变长）attention** 内核（通常对应 FlashAttention 的 varlen 接口，如 `flash_attn_varlen_func`），以支持序列长度不一致的视觉帧在同一 batch 内高效计算。
- 这与 FastVideo 作为**高速视频生成推理框架**的定位直接相关：视频生成中不同帧、不同分辨率、不同上下文长度的视觉 token 长度天然不齐，传统做法要么 pad 浪费算力、要么逐条处理无法利用 GPU 并行。变长注意力正是解决这一痛点的核心技术。
- 提交以 PR #2050 合入，并由 leo 联合署名，说明这是主仓库的常规迭代分支，由核心开发者推动的优化工作流的一部分。

### 3. 对项目的影响和潜在意义
- **吞吐与延迟改善**：批内变长注意力消除了 padding 开销并利用连续内存访问，预期降低 H3 阶段的计算浪费，从而提升端到端视频生成速度——这正是 FastVideo 对标 "fast" 的核心承诺。
- **显存效率**：避免为对齐长度而分配冗余张量，对长视频、高分辨率场景的显存压力有缓解作用。
- **可扩展性**：为后续支持更复杂的多模态/多分辨率混合批处理奠定基础，符合项目持续围绕高效视频扩散模型（如结合 Wan、HunyuanVideo 等）优化推理管线的路线。
- 对社区用户而言，属于"无感升级"——接口不变，速度更快。

### 4. 值得关注的技术点
- **PyTorch varlen attention 的引入方式**：是直接调用 `torch.nn.functional` 封装的 SDPA 变体，还是依赖 FlashAttention-2/3 的 varlen 内核？前者兼容性好但加速有限，后者性能高但要求特定 CUDA 环境——README 中文档与 Quick Start 是否同步说明该依赖值得关注。
- **`cu_seqlens` 的构造与正确性**：变长批处理的正确性高度依赖序列边界索引的计算，回归测试是否覆盖变长边界场景是质量信号。
- **H3 阶段的具体含义**：若指 Transformer 的某一注意力层或分层采样阶段，需确认改动是否与 KV cache 复用、CFG（无分类器引导）批处理等已有机制协同，避免语义偏差。
- **PyTorch 版本下限是否提升**：varlen 接口对 PyTorch/CUDA 版本有要求，可能影响下游用户环境。

### 5. 结合 README 背景对项目发展的影响
FastVideo 定位为面向研究者与工程师的高性能视频生成工具链，README 提供了文档、Cookbook、Quick Start 以及每周开发会议等完善的社区协作入口，表明项目处于**活跃的持续工程化迭代期**。
- 本次提交印证了项目的**核心演进主线之一就是不断压缩推理成本**：从算子级（varlen attention）到系统级（批处理调度）的逐层优化，而非单纯追加模型支持——这是"Fast"之名得以维持的根基。
- 配合其周会与开放 PR 流程，这类 perf 标签的提交显示出团队有节奏地进行性能基线追踪，有助于建立可信的速度基准，增强学术引用与工业采用的说服力。
- 长期来看，视觉帧变长批处理的成熟将使 FastVideo 更容易支持**交互式、变速率、异构输入**的真实应用形态，巩固其在开源视频生成加速赛道中的差异化竞争力。

## 详细提交记录

### [1fce9fb](https://github.com/hao-ai-lab/FastVideo/commit/1fce9fbc933a11d0b260f0e4db7f3eba4ee57a4f)

- **作者**: Yixing Wang
- **时间**: 2026-11-19T22:49:03Z
- **提交信息**: [perf] Batch H3 vision frames with PyTorch varlen attention (#2050)

Co-authored-by: leo <yixingwang@YIXINGs-MacBook-Pro.local>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34955
- **最后更新**: 2026-11-20T03:07:53Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Sayak Paul, menglcai, Hsu, Chan Fu

## AI分析总结

# huggingface/diffusers 近期提交分析

## 1. 主要更新类型

- **功能新增**：新增 RFD4-Proteina LoRA 训练示例、支持 musubi-tuner HunyuanVideo LoRA 格式。
- **Bug 修复**：修复 KolorsPAGPipeline 的 LoRA 加载问题。
- **重构**：将 pipeline 级别的模型组件迁移到对应的模型模块中，shap-e 正式废弃。
- **CI/工程改进**：重写测试获取脚本为基于 AST 的导入图选择器，优化测试矩阵。
- **文档更新**：补充上下文并行（Ring Attention）使用注意事项。

## 2. 关键变更点及与项目方向的关系

- **代码组织重构（#15187）**：把 pipeline 内定义的模型组件下沉到 models 目录，符合 diffusers 将 pipeline 视为"编排层"、模型组件独立复用的架构理念，提升模块化与可维护性。
- **多格式 LoRA 生态扩展**：支持 musubi-tuner 的 HunyuanVideo LoRA、修复 Kolors PAG 的 LoRA 加载，延续了项目"降低模型适配门槛、统一 LoRA 加载接口（LoraLoaderMixin）"的方向。
- **训练示例体系完善**：RFD4-Proteina LoRA 示例遵循现有示例约定（PEFT 保存、`_collate_lora_metadata`、`--push_to_hub`），展示了如何在蛋白质结构生成模型上做微调，扩展了 diffusers 在科学计算/生物领域的应用面。
- **CI 精准化**：AST 级测试选择器 + core 标记机制，减少无关测试运行，加快 PR 反馈，属于大规模仓库的持续工程优化。

## 3. 对项目的影响和潜在意义

- 架构重构会涉及大量 import 路径变动，短期内可能影响下游依赖旧路径的代码，但长期利于组件复用与维护。
- LoRA 兼容性修复与新格式支持直接惠及用户：多 transformer pipeline（如 Wan 2.2 A14B）用户不再踩坑，视频模型用户获得更广的预训练 LoRA 生态接入。
- 新训练示例降低了特定领域（蛋白质生成）的贡献门槛，有助于社区扩展 diffusers 的应用场景。
- CI 优化对高频协作的开源仓库意义显著，可减少资源浪费并提高测试可信度。

## 4. 值得关注的技术点

- **AST 导入图分析**：`tests_fetcher.py` 从简单文件匹配升级为解析 Python AST 构建导入图，精准计算"改动文件的测试可达范围"，并输出带 feature 分组的矩阵，是值得借鉴的 CI 设计。
- **core 标记派生机制**：`conftest.py` 从 `is_*` 装饰器动态推导 `NON_CORE_MARKERS`，避免维护重复的标记列表；同时处理了同名 legacy mixin 导致的误调度问题（exit code 5），体现了细节打磨。
- **多 transformer 并行陷阱**：`enable_parallelism` 仅作用于被调用的模型实例，文档明确此点避免用户在混合专家 pipeline 中误用。
- **musubi-tuner 检测策略**：通过 `lora_unet_` 前缀识别格式，与 Wan 加载器保持一致的启发式方案。

## 5. 对项目发展的整体影响

结合 README 中 diffusers 作为 Apache 2.0 许可的开源扩散模型库定位，这批提交体现了三条并行主线：**架构治理**（组件归位、废弃旧模块）、**生态兼容**（LoRA 格式、并行文档、训练示例）和**工程效能**（CI 重写）。它们共同支撑了项目"保持 API 整洁、快速响应社区需求、在高吞吐协作下维持质量"的长期目标，使 diffusers 在模型格式碎片化和贡献者众多的背景下仍能稳健演进。

## 详细提交记录

### [4f78832](https://github.com/huggingface/diffusers/commit/4f788320e9fa974d4bfe0cf5aabc3bd213c39af2)

- **作者**: menglcai
- **时间**: 2026-11-19T17:30:25Z
- **提交信息**: [docs] Add note for context parallelism: call enable_parallelism on every transformer in the pipeline (#15334)

* [docs] Note that enable_parallelism only applies to the model it's called on

The context parallelism guide only calls `pipeline.transformer.enable_parallelism(...)`. A pipeline with more than one transformer, such as Wan 2.2 A14B with `transformer` and `transformer_2`, needs it on each one, or the steps the other transformers run aren't split across GPUs. Add a short note after the Ring Attention example.

Signed-off-by: menglcai <menglcai@amd.com>

* Move the enable_parallelism note to the intro and apply review wording

Signed-off-by: menglcai <menglcai@amd.com>

---------

Signed-off-by: menglcai <menglcai@amd.com>

### [d5df05e](https://github.com/huggingface/diffusers/commit/d5df05ed2a2d310c2e515f5de55bd9e7eb63235d)

- **作者**: Sayak Paul
- **时间**: 2026-11-19T07:22:06Z
- **提交信息**: [core] move pipeline-level model components to appropriate models. (#15187)

* move pipeline-level model components to appropriate models.

* style

* move heads to others.

* more relocations.

* shap-e.

* actually deprecate shap-e.

### [47e9b10](https://github.com/huggingface/diffusers/commit/47e9b10bbe0e9951089db66d541d98a4d6ca28ba)

- **作者**: Hsu, Chan Fu
- **时间**: 2026-11-19T06:38:27Z
- **提交信息**: [Kolors] Fix LoRA loading in KolorsPAGPipeline (#15350)

* [Kolors] Use StableDiffusionLoraLoaderMixin in KolorsPAGPipeline

* [Kolors] State why the KolorsPAGPipeline LoRA tests cover the UNet only

* [Kolors] Add LoRA x memory tests for KolorsPAGPipeline

* [Kolors] Say why the LoRA memory tests cover the UNet only

---------

Co-authored-by: ChanFu, Hsu <228416682+IvenHsu01@users.noreply.github.com>

### [3d23f55](https://github.com/huggingface/diffusers/commit/3d23f555becd54b9c2c0fc37fd69026e3858885e)

- **作者**: Hsu, Chan Fu
- **时间**: 2026-11-19T06:38:08Z
- **提交信息**: [LoRA] support musubi-tuner HunyuanVideo LoRAs (#15346)

* [LoRA] support musubi-tuner HunyuanVideo LoRAs

* Address self-review: pop alpha like the Wan converter, move musubi test to the pipeline LoRA tests

* Detect musubi HunyuanVideo LoRAs by the lora_unet_ prefix, like the Wan loader

* Remove the musubi HunyuanVideo LoRA test (review)

---------

Co-authored-by: ChanFu, Hsu <228416682+IvenHsu01@users.noreply.github.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [1c2926d](https://github.com/huggingface/diffusers/commit/1c2926d2183d1f9bd69b1f4a90707f868f4ceab3)

- **作者**: Dhruv Nair
- **时间**: 2026-11-19T06:01:04Z
- **提交信息**: [CI] Update test fetcher script (#14607)

* [CI] Rewrite `tests_fetcher.py` as an AST-based import-graph selector with feature-split matrix output

* [tests] Import pipeline/model classes inside the tests that use them so the fetcher does not over-select through shared mixins

* [CI] Give `single_file` model tests their own fetcher job; they need an HF token, not an accelerator

* [tests] Keep `create_flux_ip_adapter_state_dict` in `test_models_transformer_flux.py` instead of a separate `utils.py`

* update

* [CI] Detect the `main` branch by name in `tests_fetcher.py`; a branch checkout has no local `main` ref

* [CI] Mark the workspace as a git safe directory before running `tests_fetcher.py` in the container

* [CI] Select core tests with a `core` marker derived from the `is_*` decorators

`tests/conftest.py` derives `NON_CORE_MARKERS` from the markers the `is_*` decorators in
`testing_utils.py` apply and marks every test carrying none of them as `core` at collection time.
The fetcher imports that set instead of keeping its own list and emits `-m core` for the core jobs in
place of the `not (...)` complement expression. Also drop `-v` from the pytest run, which no other
workflow passes.

* [CI] Credit mixin markers only for bases imported from `testing_utils`; legacy mixins share their names

The legacy cache and IP-Adapter mixins in `test_pipelines_common.py` are unmarked but have the same
class names as the marked ones, so matching by bare name scheduled a `pipelines-cache` job whose
`-m cache` run collected nothing and failed with exit code 5.

* fix(ci): harden GitHub Actions workflows (#14607) (#14945)

fix(ci): harden workflow files flagged on #14607

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

* [CI] Count test files in the fetcher summary and add a row for modified test files outside the listed reach

* [CI] Compare each modified file's test reach to the base commit in the fetcher summary

* [CI] Show each modified file's reach on branch and on main in the fetcher summary

* [tests] Use the concrete pipeline classes instead of `AutoPipeline*` in PAG, Kandinsky3, and flashpack tests

* [tests] Ban `AutoPipeline*` imports in tests and switch the SD and SDXL tests to the concrete classes

* [CI] Summarize the selection per changed file with a collapsible import tree, and drop the base-commit comparison

* [CI] Flag test files that import a module which imports much of the library in the fetcher summary

* [CI] Give the tail of a wide diff its own nested dropdowns in the fetcher summary

* [CI] Call out changed files that run no tests and move the import trees into one Details section

* [tests] Import the Flux and SD3 transformers at module level in `test_modeling_common.py`; the file is a leaf

* [tests] Document `marker_decorators` with an example, name the file it reads, and explain the `core` collection hook

* [CI] Obtain the Hub token for single-file tests through OIDC in the fetcher workflow

* [CI] Simplify `tests_fetcher.py` and use dashed CLI flags

* [CI] Write the matrix before the summary so a report failure cannot schedule the full suite

---------

Co-authored-by: hf-security-analysis[bot] <265538906+hf-security-analysis[bot]@users.noreply.github.com>

### [b41f85a](https://github.com/huggingface/diffusers/commit/b41f85a31da535637d19cdaf9b6edc22bfd1785f)

- **作者**: Kieran Didi
- **时间**: 2026-11-19T03:05:55Z
- **提交信息**: Add an RFD4-Proteina LoRA training example (#15155)

* Add an RFD4-Proteina LoRA training example

Trains PEFT adapters on the denoiser with the released recipe, saved in the format RFD4ProteinaPipeline.load_lora_weights reads.

* Follow the established LoRA save pattern

Save the adapter the way the current LoRA examples do: the PEFT state dict
goes out unconverted, and `_collate_lora_metadata` records rank, alpha and
target modules alongside it.

Resolve `--resume_from_checkpoint` against `--output_dir`, so naming a
checkpoint works as well as passing its path.

* Make RFD4 LoRA data preparation and checkpointing distributed-safe

* Trim RFD4 example docs and keep focused dataset tests

* Address RFD4 example follow-up review

* Show held-out validation for the RFD4 LoRA example

Train on 40 of the fifty published structures and score the remaining ten
with the adapter toggled on and off over identical noise draws. Held-out
flow-matching loss falls 11%, on every held-out structure.

* Remove benchmark results from the example README

* Cyclic peptide check

* Write a model card and support pushing to the Hub

Every run now writes a model card next to the adapter, naming the base
checkpoint and the structures trained on, with a snippet that generates from
the result. `--push_to_hub`, `--hub_model_id` and `--hub_token` upload the
adapter and that card at the end of training, as the other LoRA examples do.

* Add Hub support to the RFD4 LoRA example

* Align RFD4 LoRA example conventions

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-11-12T08:10:11Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13415
- **最后更新**: 2026-11-20T00:59:19Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

## DiffSynth-Studio 昨日提交分析

### 1. 主要更新类型

本次提交属于**功能新增与对齐调优**相结合的类型。其中 #1839 为新增文档（新增 MiniMax-H3-Image 训练适配器的文档），#1836 为训练流程的功能对齐与调整（将 MiniMax-H3-Image 训练对齐到 6 步推理）。总体来看，两条提交共同围绕**MiniMax-H3-Image 模型的训练支持**展开，属于针对特定模型的功能扩展与完善。

### 2. 关键变更点及与项目整体方向的关系

- **#1839（文档新增）**：为 MiniMax-H3-Image 添加了训练适配器的文档，说明该项目已在代码层面支持了该模型的训练适配器，此次补充文档以降低用户的使用门槛。
- **#1836（训练对齐）**：将 MiniMax-H3-Image 的训练配置从原来的步数调整为 **6 步**，与模型的少步推理（few-step inference）能力保持一致。该提交还涉及 FlowMatch SFT（监督微调）中**调度器时间步精度的保留**、**移除了 FlowMatch SFT 损失测试**、**回退了部分损失变更**，说明在对齐过程中对训练稳定性做了多轮调试和修正。

与项目整体方向的关系：DiffSynth-Studio 是 ModelScope 生态下专注扩散合成模型训练与推理的工具库，其核心目标是让使用者便捷地训练各类扩散/Flow Matching 模型。这两条提交直接扩展了该仓库对 **MiniMax-H3-Image**（推测为 MiniMax 家族的图像生成模型）的训练支持，体现了仓库持续集成新模型、降低多模型训练门槛的发展方向。

### 3. 对项目的影响和潜在影响

- **提升模型覆盖度**：新增对 MiniMax-H3-Image 训练的支持和文档，使项目支持的模型谱系进一步扩大，增强其作为"一站式扩散模型训练 Studio"的定位。
- **提高训练-推理一致性**：将训练步数对齐到 6 步，有助于用户在微调后获得与官方少步推理配置一致的效果，减少"训出来好、推出来差"的不匹配问题。
- **潜在风险**：移除 FlowMatch SFT 损失测试并回退部分损失变更，暗示该方向的训练流程可能尚未完全稳定，后续或需进一步的测试覆盖和质量保障。

### 4. 值得关注的技术点

- **调度器时间步精度保留**：在 FlowMatch SFT 中保留时间步的高精度，说明训练过程中对 timestep 的数值精度较为敏感，这是 Flow Matching 类训练中值得关注的细节。
- **6 步少步训练对齐**：将训练目标从多步调整到 6 步，涉及对调度器（scheduler）、噪声调度策略等多方面的联动调整，是少步扩散模型训练中的关键工程实践。
- **移除损失测试的决策**：删除 FlowMatch SFT 的损失测试并回退损失相关变更，反映了在功能对齐过程中对训练稳定性的取舍，值得后续关注是否会有更完善的测试重新引入。

### 5. 基于项目背景的综合影响评估

结合 README 可知，DiffSynth-Studio 的目标是提供一个易于使用的扩散模型训练与推理 Studio，依托 PyPI 分发并持续扩展模型适配范围。本次两条提交围绕 MiniMax-H3-Image 这一新增模型完成了从**训练代码对齐**到**用户文档补充**的完整闭环，符合该仓库"新模型快速接入 + 文档同步完善"的迭代节奏。这不仅增强了项目对 MiniMax 生态模型的覆盖，也向贡献者展示了标准的新模型接入流程（先实现适配器、再对齐训练配置、最后补充文档），有助于吸引更多社区贡献。整体而言，这些提交稳步推进了项目作为多模型扩散训练中心平台的发展目标，但在训练流程的测试覆盖方面仍有提升空间。

## 详细提交记录

### [35e7214](https://github.com/modelscope/DiffSynth-Studio/commit/35e72140b917cfae1ff66932373bb8f83d66e7aa)

- **作者**: Hong Zhang
- **时间**: 2026-11-19T08:02:57Z
- **提交信息**: Add MiniMax-H3-Image training adapter docs (#1839)

### [ca883a7](https://github.com/modelscope/DiffSynth-Studio/commit/ca883a76d8f6c005b0c335bbafa826c27ec84148)

- **作者**: Hong Zhang
- **时间**: 2026-11-19T02:12:07Z
- **提交信息**: Align MiniMax-H3-Image training to 6 steps (#1836)

* Preserve scheduler timestep precision in FlowMatch SFT

* Remove flow match SFT loss test

* update 6step training

* revert loss

---------

Co-authored-by: 石怡昊 <1635219023@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38865
- **最后更新**: 2026-11-20T02:28:43Z

## 提交统计

- **昨日提交总数**: 82
- **提交者数量**: 55
- **主要提交者**: Siyuan Chen, Benjamin Truong, Yuhao Yang

## AI分析总结

# sgl-project/sglang 昨日提交分析（共 82 条）

## 1. 主要更新类型
- **性能优化占比最高**（约 30 条）：集中在扩散模型、DSA/投机解码、MoE 内核与 CUDA Graph 融合。
- **功能新增**（约 25 条）：调度策略、路由 API、新模型支持（Inkling-2、MiniMax-M3）、FP8 KV cache、L3 存储后端、Intel XPU 等。
- **Bug 修复**（约 15 条）：多为多硬件后端、分布式与混合精度场景的边界问题，另有文档、CI、测试与依赖维护。

## 2. 关键变更与项目方向
- **扩散/多模态推理成为重点投入**：flux3、cosmos3、wan 成批优化 VAE、CFG 并行与条件哈希缓存；qwen-image、Pi0.5 获得错误码规范、流式回退与响应序列化修复，对应 README「多模态快速推理」的核心定位。
- **投机解码与 DSA 持续深化**：DCP 分离式传输、FP4 indexer、DFLASH/dspark 草稿修正，EAGLE 拒绝采样内核融合、decode slot 单次 launch，强化长上下文与低延迟优势。
- **架构规模化**：NIXL 统一内存 PD 分离、mooncake 后端、vmm_fd 传输与统一内存页设计，支撑 Prefill-Decode 分离和权重缓存的长期布局。
- **硬件生态多元化**：NVIDIA（SM90/SM103/SM120 内核、RTX PRO 5000/6000）、NPU（MindIE-SD 稀疏注意力、JPEG 解码）、AMD（mono-kernel、夜间基准）、Intel XPU 并进。
- **服务与工程化增强**：UniBoost 调度、sgl-router 的 OpenAI Responses API 与 DP rank 负载策略、逐请求 sampling_seed、Cookbook 命令注册，降低接入门槛。

## 3. 影响与潜在意义
系统级融合（CUDA Graph 内融合 all-reduce、VAE 分片、软件+采样与槽位分配合并 launch）可显著降低扩散与 LLM 推理的时延和显存；FP8 KV cache 与 Q8 prefill 大幅压缩长上下文显存，对大规模服务成本有直接收益。修复类提交集中在多节点、分片注意力与调度器关闭时序，说明项目正从「跑得快」转向「跑得稳」，面向生产部署。

## 4. 值得关注的技术点
- **GPU BLAKE3 加速条件哈希**与缓存复用，是扩散推理缓存设计的新思路。
- **MXFP8 KV scales 存入统一内存页**，为低精度 KV 缓存的可扩展性铺路。
- **Marlin 量化在 SM100 上保留**，说明 Blackwell 上 AWQ/GPTQ 内核生态仍在演进。
- **pybase64 + orjson** 替换以纯库方案提升图像响应吞吐，轻量有效的工程优化。
- **逐层 FlashAttention 覆写与块锚定窗口**提供细粒度注意力控制。
- 大量提交由 Claude 系列 AI 助手协同完成，反映开发流程 AI 化趋势。

## 5. 对项目发展的影响
这些提交延续并强化了 README 所述愿景：一手抓扩散模型与投机解码的极限性能，一手通过 PD 分离、统一内存、多存储后端和调度路由标准化补齐工程化短板，同时以多硬件适配扩大部署场景。文档与 CI 的同步更新保障了复杂功能的可维护性与发布质量，整体上使 SGLang 从性能优先的 LLM 推理引擎向**稳定、通用、生态完善的多模态多硬件推理平台**演进；后续可关注扩散推理与 DSA 路线的整合成熟度，以及 NPU/NVIDIA 双栈的一致性表现。

## 详细提交记录

### [03fde9c](https://github.com/sgl-project/sglang/commit/03fde9cc392a5f84a54a365635ffed0061cdf1b8)

- **作者**: Khoa Pham
- **时间**: 2026-11-19T23:54:17Z
- **提交信息**: [Perf] disagg: Pack a DCP-collapsed draft with the target rows in DCP-1 -> DCP-N transfers (#51455)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [0ab0e9d](https://github.com/sgl-project/sglang/commit/0ab0e9d5d0d71b26f0a2007f49353d6776af9ae9)

- **作者**: zijiexia
- **时间**: 2026-11-19T23:49:55Z
- **提交信息**: [Perf] MiniMax-M3: overlap the shared expert with MegaMoE under CUDA graph (#51382)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>

### [51ccc1f](https://github.com/sgl-project/sglang/commit/51ccc1f6994530b2f16ed1160e728c13a4c0b283)

- **作者**: Pinjie Xu
- **时间**: 2026-11-19T23:32:32Z
- **提交信息**: [Perf] diffusion/cosmos3: batch clean refresh and enable VAE fast paths for Bimanual model (#49532)

### [fccaf68](https://github.com/sgl-project/sglang/commit/fccaf681a2a0ed5d46f2cc389368ce6b046e7c9c)

- **作者**: Pinjie Xu
- **时间**: 2026-11-19T23:30:57Z
- **提交信息**: [Perf] diffusion: Accelerate conditioning hashing with GPU BLAKE3 (#46603)

Signed-off-by: pinjie <pinjiex@nvidia.com>

### [fb97472](https://github.com/sgl-project/sglang/commit/fb97472771cff2810821acfe81a177b6b0be721e)

- **作者**: Mick
- **时间**: 2026-11-19T23:28:24Z
- **提交信息**: [Perf] diffusion/flux3: Encode prompts through the conditioning cache (#51411)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [5cee3ad](https://github.com/sgl-project/sglang/commit/5cee3ad8080518a257b90ad9c351e2ede55de8b3)

- **作者**: Devashish Lal
- **时间**: 2026-11-19T23:21:23Z
- **提交信息**: [CI] permissions: update name for DevashishLal-CB to dlal-sgl (#51391)

Signed-off-by: dlal-sgl <devashish.lal@radixark.ai>
Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [99e4233](https://github.com/sgl-project/sglang/commit/99e4233f633a9835987308e6f0a7fb262fc34d62)

- **作者**: yl3469
- **时间**: 2026-11-19T22:46:39Z
- **提交信息**: [Feat] scheduler: Add UniBoost tail-aware schedule policy with a rank-invariant TP/PP mode (#35637)

Co-authored-by: Yueying Li <yueyingl@nvidia.com>

### [c80444d](https://github.com/sgl-project/sglang/commit/c80444d5510797c6a1b0daefb816ab8ab3ebd3d3)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-19T22:40:49Z
- **提交信息**: [Fix] scheduler: Send Engine.collective_rpc through the control request path (#51521)

Co-authored-by: Hao Liu <liuha@montclair.edu>
Co-authored-by: xuan <liyingxuan7@tju.edu.cn>

### [e627fed](https://github.com/sgl-project/sglang/commit/e627fed679dc93ee1c50503a862550e0718770e3)

- **作者**: ybyang
- **时间**: 2026-11-19T22:29:21Z
- **提交信息**: [Feat] sgl-router: Serve the OpenAI Responses API on /v1/responses (#42314)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [a3fd615](https://github.com/sgl-project/sglang/commit/a3fd615a9714a11f389ce9ca114dc15f27a07bb9)

- **作者**: Jessica Zhong
- **时间**: 2026-11-19T22:28:09Z
- **提交信息**: [Feat] sampling: Honor per-request sampling_seed without deterministic inference (#49246)

Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [ab2ebbf](https://github.com/sgl-project/sglang/commit/ab2ebbf4215d10de2ace657d5e5056930eb175a6)

- **作者**: Atharva Joshi
- **时间**: 2026-11-19T22:20:09Z
- **提交信息**: [Fix] [NVIDIA] cosmos3: Fix multi-node execution (#48220)

### [3b0e693](https://github.com/sgl-project/sglang/commit/3b0e693f46b74ae48d99abb610225b9cd37cbf63)

- **作者**: Mick
- **时间**: 2026-11-19T21:55:13Z
- **提交信息**: [Perf] diffusion/flux3: Keep static streams across steps under CFG parallel (#51380)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [7c08c30](https://github.com/sgl-project/sglang/commit/7c08c3040c7f84b92c6344927875884b23682558)

- **作者**: Mick
- **时间**: 2026-11-19T21:54:42Z
- **提交信息**: [Perf] diffusion/flux3: Shard the image VAE decode only with --vae-sp (#51406)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [5730875](https://github.com/sgl-project/sglang/commit/5730875f20f82293d83b6a89b733b3fce09bb74f)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T21:21:54Z
- **提交信息**: [Fix] spec: Clear moe_dense_tp_size for a draft narrowed to plain TP (#51607)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [78cb42e](https://github.com/sgl-project/sglang/commit/78cb42ebbc28b9bc24b821860db6927ddf51117d)

- **作者**: Mick
- **时间**: 2026-11-19T20:58:42Z
- **提交信息**: [Fix] diffusion/flux3: Honor --component-precisions.vae (#51529)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [d4824c7](https://github.com/sgl-project/sglang/commit/d4824c7cb8696d7cf3bd8f0a7f1a206e0b8923a5)

- **作者**: Mick
- **时间**: 2026-11-19T20:58:17Z
- **提交信息**: [Perf] diffusion: Pick the plain Ulysses exchange's transport by payload (#51554)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [da8325b](https://github.com/sgl-project/sglang/commit/da8325b10e878b194a586cdaa68fbdba4561d22c)

- **作者**: Mick
- **时间**: 2026-11-19T20:57:07Z
- **提交信息**: [Doc] diffusion: Clarify native Wan video request dimensions (#51600)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [be322a8](https://github.com/sgl-project/sglang/commit/be322a83387276368893aff7c669d7f5c3d33a4c)

- **作者**: Shangming Cai
- **时间**: 2026-11-19T20:29:38Z
- **提交信息**: [Feat] sgl-router: Add --decode-dp-rank-policy and rank least_tokens by expected KV (#51415)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [17a9168](https://github.com/sgl-project/sglang/commit/17a9168f1f99f9eeb17ee7a97717f8a100abf4d8)

- **作者**: Khoa Pham
- **时间**: 2026-11-19T18:59:04Z
- **提交信息**: [Perf] [NVIDIA] dsa: Fuse the FP4 indexer key store and head gate (#51515)

### [f4bfe14](https://github.com/sgl-project/sglang/commit/f4bfe143ddf60ed687766431bc08d0f780b5b60b)

- **作者**: elvischenv
- **时间**: 2026-11-19T18:57:12Z
- **提交信息**: [Fix] dsa: Attend the sharded indexer's local slots in trtllm / prims_ts DCP decode (#51289)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2bf882a](https://github.com/sgl-project/sglang/commit/2bf882aefcfc11d089f4f1cedaed9e872b722fe4)

- **作者**: Mick
- **时间**: 2026-11-19T18:30:29Z
- **提交信息**: [Perf] diffusion/flux3: Run the native SwiGLU through the shared SiluAndMul layer (#51387)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [54d6812](https://github.com/sgl-project/sglang/commit/54d68123dcc672bc6920371ee6d90ee4ab73edaf)

- **作者**: jacky.cheng
- **时间**: 2026-11-19T17:03:09Z
- **提交信息**: [Chore] [AMD] mono-kernel: Pin sgl-amd-mono at 32a1220 for the Qwen3.5 FP8 state_layer_cache fix (#51518)

### [6515ac2](https://github.com/sgl-project/sglang/commit/6515ac29d3c2206ec4a9b54c40e6b2b25c3a43a3)

- **作者**: Ke Bao
- **时间**: 2026-11-19T15:35:20Z
- **提交信息**: [Feat] inkling2: Support Inkling-2-Small (#50186)

Co-authored-by: Aurick Qiao <aurickq@users.noreply.github.com>
Co-authored-by: Chunan Zeng <zcnrex@gmail.com>
Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: Qiaolin Yu <liin1211@outlook.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: zijiexia <37504505+zijiexia@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5e32149](https://github.com/sgl-project/sglang/commit/5e32149fd6b58a30a4a72bbaa779aafc1bb6119a)

- **作者**: micha
- **时间**: 2026-11-19T14:47:11Z
- **提交信息**: [Feat] [NPU] multimodal: Add JPEG decoding to the shared image loader (#45792)

Co-authored-by: Codex <codex@localhost>
Co-authored-by: SGLang local candidate <local-candidate@invalid>

### [a679ebe](https://github.com/sgl-project/sglang/commit/a679ebe4347a971a80c03adf6af51178f0e6a516)

- **作者**: shun8686
- **时间**: 2026-11-19T14:39:25Z
- **提交信息**: [CI] [NPU] ci: Split extra-b-test-1/2 into two partitions to avoid timeouts (#51551)

### [9667988](https://github.com/sgl-project/sglang/commit/9667988e9cc9a99292d92855cec271c454431d4d)

- **作者**: jain-ria
- **时间**: 2026-11-19T13:45:35Z
- **提交信息**: [Chore] rust: Bump sglang-api-types to 0.1.1 (#50028)

Signed-off-by: jain-ria <riajain@NVIDIA.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cefe8d3](https://github.com/sgl-project/sglang/commit/cefe8d3be526c37bf4d7cabb2c72c7066832e60b)

- **作者**: DUAN Zhendong
- **时间**: 2026-11-19T13:42:59Z
- **提交信息**: [Feat] [NPU] attention: Add MindIE-SD sparse attention backend (#40580)

### [4ba6970](https://github.com/sgl-project/sglang/commit/4ba697002facfb028b9127b49564e513b489b488)

- **作者**: Артем Савкин
- **时间**: 2026-11-19T13:05:14Z
- **提交信息**: [Fix] [NPU] diffusion: Clean up warnings (#44329)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [1d4ff95](https://github.com/sgl-project/sglang/commit/1d4ff95e9c8d1539100f45877cc6390d7fb50d30)

- **作者**: Javen
- **时间**: 2026-11-19T12:47:35Z
- **提交信息**: [Fix] [NPU] modelslim: Fix Qwen3.8-27B-W8A8 loading (#36426)

Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: fishAndShrimp <ruiyuanqian@foxmail.com>
Co-authored-by: Артем Савкин <58187114+OrangeRedeng@users.noreply.github.com>

### [b6d4389](https://github.com/sgl-project/sglang/commit/b6d4389a77970e31817536c3e182256fae6a6f73)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-19T11:49:17Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main df623226 (#51504)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cb97061](https://github.com/sgl-project/sglang/commit/cb970616d46d2346ec1aedfb111aa512cea93982)

- **作者**: jain-ria
- **时间**: 2026-11-19T10:54:44Z
- **提交信息**: [Feat] mm: Add --disable-multimodal to serve a multimodal model text-only (#47977)

Signed-off-by: jain-ria <riajain@NVIDIA.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f9dacff](https://github.com/sgl-project/sglang/commit/f9dacff70159864f5d15ba16cb5b3006fc6ea8c4)

- **作者**: ishandhanani
- **时间**: 2026-11-19T10:47:33Z
- **提交信息**: [Fix] grpc: Allow --tokenizer-worker-num > 1 with --grpc-port in Rust-server mode (#51270)

Signed-off-by: Ishan Dhanani <ishandhanani@gmail.com>

### [63038e7](https://github.com/sgl-project/sglang/commit/63038e7c99f340c2182f82d2d23f1b55525a15e3)

- **作者**: Shuwen Wang
- **时间**: 2026-11-19T10:44:38Z
- **提交信息**: [Feat] linker: Expose external cache linker lookup, load, offload and wait metrics (#49127)

### [9aa3b9e](https://github.com/sgl-project/sglang/commit/9aa3b9e3381685650a86c19dfae475fb24a6a3d0)

- **作者**: fengshaoyi-amd
- **时间**: 2026-11-19T10:14:40Z
- **提交信息**: [Doc] [AMD] cookbook: Add the GLM-5.3-Flash MI300X and MI325X AgentX commands from InferenceX (#51172)

Co-authored-by: fengshaoyi-amd <220679416+fengshaoyi-amd@users.noreply.github.com>

### [3331567](https://github.com/sgl-project/sglang/commit/33315670abdc581eaddf976282363ca8d9beb01f)

- **作者**: wuyaole
- **时间**: 2026-11-19T10:11:19Z
- **提交信息**: [Fix] cli: resync Cookbook command registry with main (#51517)

Signed-off-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>
Co-authored-by: wuyaole <112309453+LeslieWylie@users.noreply.github.com>

### [01497af](https://github.com/sgl-project/sglang/commit/01497afbd4c6fba300435eb991a21b0839daeb73)

- **作者**: Khoa Pham
- **时间**: 2026-11-19T09:46:59Z
- **提交信息**: [Feat] [NVIDIA] dsa: Support the FP4 indexer for Kimi-K3.1 and under DCP (#51450)

### [6c722ac](https://github.com/sgl-project/sglang/commit/6c722acbcdaad01682b12e666225bcda44249e74)

- **作者**: Long Wu
- **时间**: 2026-11-19T09:34:47Z
- **提交信息**: [Fix] dflash: Preserve captured custom_mask on idle DP ranks (#51458)

Co-authored-by: Long Wu <wulong@zetyun.com>

### [b1970bc](https://github.com/sgl-project/sglang/commit/b1970bc473cfff1731c068e7d23e9e61b794b0c0)

- **作者**: Yichi Zhang
- **时间**: 2026-11-19T08:52:37Z
- **提交信息**: [Feat] cli: Export Cookbook commands for every config-driven LLM/VLM page (#50106)

### [a735253](https://github.com/sgl-project/sglang/commit/a735253e8433d5fc57bf585b3eef93e4b4cfa885)

- **作者**: Mick
- **时间**: 2026-11-19T07:55:15Z
- **提交信息**: [Test] diffusion: exercise action HTTP and WebSocket client contracts (#51360)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [33a03ba](https://github.com/sgl-project/sglang/commit/33a03ba42ee4c6036d75c22e71b9bb8600c79355)

- **作者**: yuhuang.89
- **时间**: 2026-11-19T07:17:15Z
- **提交信息**: [Fix] disaggregation: Register the NextN draft DSA index cache for hybrid pools (#41334)

Co-authored-by: Yizheng Jiao <andy.jiao@baseten.co>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>

### [8761838](https://github.com/sgl-project/sglang/commit/8761838757360f74f59b61c337a5e69f5d502d12)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:17:11Z
- **提交信息**: [Feat] mem_cache: Store MXFP8 KV scales in unified memory pages (#51296)

Co-authored-by: Cheng Wan <54331508+ch-wan@users.noreply.github.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0b1064b](https://github.com/sgl-project/sglang/commit/0b1064bdf9f7484fd9c0dbf615efcb76e08e497d)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:16:35Z
- **提交信息**: [Refactor] model_loader: Let models name their safetensors index file (#51299)

Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [91c88c6](https://github.com/sgl-project/sglang/commit/91c88c669769d816f482d51dec06b65be24df008)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:16:07Z
- **提交信息**: [Feat] attention: Add per-layer FA overrides and block-anchored windows (#51297)

Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [21be218](https://github.com/sgl-project/sglang/commit/21be2189de65d7b70467dbd61d833b17106c6d46)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:15:37Z
- **提交信息**: [Feat] dspark: Let the draft fold its verify commit and cap step logits (#51298)

Co-authored-by: Qiaolin Yu <liin1211@outlook.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d814a39](https://github.com/sgl-project/sglang/commit/d814a39f470e8c8bafded1aba335ae75de6ac5db)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:15:11Z
- **提交信息**: [Feat] inkling2: Add SM90 Marlin, expert and MTP kernel ops (#51302)

Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ecc5ab3](https://github.com/sgl-project/sglang/commit/ecc5ab3a38a7e203784274d2787e03b279687c46)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:14:47Z
- **提交信息**: [Feat] linker: Place hybrid-SWA sidecar draft pools on the target pages (#51300)

Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c97d47b](https://github.com/sgl-project/sglang/commit/c97d47b872c4bc8ec4435493212ab0bdc1b64777)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T07:14:14Z
- **提交信息**: [Feat] inkling2: Render and parse chat through the inkling2 renderer spec (#51301)

Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [81844a3](https://github.com/sgl-project/sglang/commit/81844a31d791f4fadd7949371f5f6c8800594063)

- **作者**: ZY Y
- **时间**: 2026-11-19T07:00:59Z
- **提交信息**: [Test] [NPU] multi-node: Fix the PD warmup race and raise the DSV4-Flash 128K prefill memory fraction (#51417)

### [fb60c29](https://github.com/sgl-project/sglang/commit/fb60c297720498baa7df670c8dd930dd21761a86)

- **作者**: Jimmy Shong
- **时间**: 2026-11-19T06:48:41Z
- **提交信息**: [Feat] [NVIDIA] beam: Add the SM103 single-token BF16 MoE kernel (#46401)

Co-authored-by: BBuf <1182563586@qq.com>
Co-authored-by: Caihua Li <caihua.li@bytedance.com>
Co-authored-by: Florent Gbelidji <florentgbelidji@Florents-MacBook-Pro.local>
Co-authored-by: iaroslav-reflection <iaroslav@reflection.ai>
Co-authored-by: Jinze Xue <jinzex@nvidia.com>
Co-authored-by: mloh <mloh@nvidia.com>
Co-authored-by: neilkg <33635204+neilkg@users.noreply.github.com>
Co-authored-by: thibautbar <t.barroyer@icloud.com>

### [f29cc39](https://github.com/sgl-project/sglang/commit/f29cc397a29a1d918079516f12d9e0a93c3e9c92)

- **作者**: esarafian
- **时间**: 2026-11-19T06:43:50Z
- **提交信息**: [Perf] qwen4: pin the offloaded PLE table at its exact size (#48249)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [b05e9c6](https://github.com/sgl-project/sglang/commit/b05e9c68ce2451bc88228d14160187b049b111c8)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-19T06:35:44Z
- **提交信息**: [Chore] sglang-processor: Bump dynamo-renderer to 10.4.3 and dynamo-tokenizers to 4.3.1 (#50721)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: ShangmingCai <csmthu@gmail.com>

### [8625aed](https://github.com/sgl-project/sglang/commit/8625aed698c80f1ee614a54cd18979c3ee2bf7e7)

- **作者**: guanam
- **时间**: 2026-11-19T06:24:22Z
- **提交信息**: [Test] [NPU] graph: Drop tp1 compile_graph test and run tp2 in base-b PR CI (#50972)

### [1ed3e1d](https://github.com/sgl-project/sglang/commit/1ed3e1d04b25ab007b4c80481b7b6e3a36836eb7)

- **作者**: Nguyễn Thế Duy
- **时间**: 2026-11-19T05:59:32Z
- **提交信息**: [Chore] inkling: Bump tml-renderers to 0.4.2 (#51231)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [981becd](https://github.com/sgl-project/sglang/commit/981becd7afebb330891492bdff0ca8cd59f8b616)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-19T05:29:20Z
- **提交信息**: [Fix] spec/dflash: Turn the DFLASH draft KV ring off by default (#51386)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [27997a8](https://github.com/sgl-project/sglang/commit/27997a872f3d49f724b519157d4c0b8e48346b5a)

- **作者**: Benjamin Truong
- **时间**: 2026-11-19T04:47:06Z
- **提交信息**: [Perf] [NVIDIA] gemma4: run the fused all-reduce sites for decode batches inside the decode CUDA graphs (#50228)

### [f49d6c4](https://github.com/sgl-project/sglang/commit/f49d6c493e953b61ed4a12fb1898b1f488daaf8e)

- **作者**: Siyuan Chen
- **时间**: 2026-11-19T04:34:55Z
- **提交信息**: [Perf] dsv41-flash: Fuse Hopper prefill candidate selection and writeback (#49069)

### [e4353c9](https://github.com/sgl-project/sglang/commit/e4353c97807b9e9c33bb1684ce941f511e352a92)

- **作者**: Siyuan Chen
- **时间**: 2026-11-19T04:34:46Z
- **提交信息**: [Perf] dsv41-flash: Reuse paged Indexer key tiles during verification (#49068)

### [2e80690](https://github.com/sgl-project/sglang/commit/2e80690d10870ea7959f73e1f048fdba7735a2af)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-19T04:34:37Z
- **提交信息**: [Fix] attention: Fix KDA prefill overflow past 2**31 token offsets (#50775)

### [5aee953](https://github.com/sgl-project/sglang/commit/5aee953e1a6e9715f1d0d06de0fa9a64cbc5f866)

- **作者**: lingxling
- **时间**: 2026-11-19T04:34:27Z
- **提交信息**: [Fix] [NVIDIA] DSA: Fix BF16 TileLang shared memory overflow on SM120 (#50752)

### [8983bd6](https://github.com/sgl-project/sglang/commit/8983bd6a664851bf7ad07edf2a554d4febe6c712)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-11-19T04:34:17Z
- **提交信息**: [Perf] [NVIDIA] DSA: Pick any divisor of the tile count for the TileLang sparse decode split (#45274)

Co-authored-by: Han Han <hanhan7630@outlook.com>

### [5eeeb11](https://github.com/sgl-project/sglang/commit/5eeeb116e1cd23601a5f7c7ff8e8a5b10c086667)

- **作者**: DarkSharpness
- **时间**: 2026-11-19T04:33:53Z
- **提交信息**: [Perf] spec: Fused draft softmax + sample kernel for EAGLE rejection sampling (#50620)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8eba7fb](https://github.com/sgl-project/sglang/commit/8eba7fb3d37ccebdaafff7dd8fd80689bbf02dea)

- **作者**: yzk1989
- **时间**: 2026-11-19T04:33:18Z
- **提交信息**: [Feat] dsa: Support raw FP8 KV cache with Q8 prefill on CUDA (#44217)

### [b08f70c](https://github.com/sgl-project/sglang/commit/b08f70c1f94433cd42c48e32c81a7741d48418a5)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-19T04:33:08Z
- **提交信息**: [Fix] quantization: Keep the Marlin conversion for AWQ/GPTQ checkpoints on SM100 (#51162)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [eae4bcb](https://github.com/sgl-project/sglang/commit/eae4bcb70bc20aeb482278a641a0c09ec44f6395)

- **作者**: Yuhao Yang
- **时间**: 2026-11-19T04:32:59Z
- **提交信息**: [Fix] tokenizer_manager: Stop the schedulers only after every tokenizer worker drains (#50518)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [5b478f1](https://github.com/sgl-project/sglang/commit/5b478f175b188ee0298decdab1df2f2981d7dcc1)

- **作者**: Chunan Zeng
- **时间**: 2026-11-19T04:16:12Z
- **提交信息**: [Perf] mem_cache: Allocate decode slots and write req_to_token in one launch (#51295)

Co-authored-by: ispobock <ispobaoke@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f7e7ccb](https://github.com/sgl-project/sglang/commit/f7e7ccbd9f1b9fc7f9373de19ea5ea91a81d359b)

- **作者**: Mick
- **时间**: 2026-11-19T03:57:35Z
- **提交信息**: [Doc] diffusion: clarify image edit inputs and URL responses (#51358)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [e840dbe](https://github.com/sgl-project/sglang/commit/e840dbeaab47159373c62521207dad8b49e89b2b)

- **作者**: Mick
- **时间**: 2026-11-19T03:57:05Z
- **提交信息**: [Doc] diffusion: note Pi0.5 tokenizer access prerequisite (#51361)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [5decba4](https://github.com/sgl-project/sglang/commit/5decba407a2e26c824ddba82bfccb2365fd5e4a8)

- **作者**: Mick
- **时间**: 2026-11-19T03:56:36Z
- **提交信息**: [Fix] diffusion: exit nonzero when generate produces no results (#51362)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [145647c](https://github.com/sgl-project/sglang/commit/145647c55fdf1b99fb3e7514ad9845fbc0a5f8a8)

- **作者**: Yoray Zack
- **时间**: 2026-11-19T03:35:04Z
- **提交信息**: [Feat] disaggregation: Support unified-memory PD with NIXL (#50767)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c86973c](https://github.com/sgl-project/sglang/commit/c86973c11cd412592b791c9f3426064a3d365fc3)

- **作者**: Jimmy Shong
- **时间**: 2026-11-19T03:16:02Z
- **提交信息**: [Doc] cookbook: Add an RTX PRO 6000 recipe for DeepSeek-V4.1 (#51410)

### [091cdce](https://github.com/sgl-project/sglang/commit/091cdce69982575b139d3e9d12697c7b2470c430)

- **作者**: Mick
- **时间**: 2026-11-19T03:09:03Z
- **提交信息**: [Perf] diffusion: Serialize image responses with pybase64 and orjson (#51318)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Mythos 5.2 <noreply@anthropic.com>

### [5a0e808](https://github.com/sgl-project/sglang/commit/5a0e808c59b82eb7d435bcef63a7cf9c1b4bc2c9)

- **作者**: kpjeeja
- **时间**: 2026-11-19T02:39:26Z
- **提交信息**: [Feat] [Intel] disaggregation: Support Intel XPU in the EPD multimodal encoder path (#47961)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2886093](https://github.com/sgl-project/sglang/commit/2886093fa9b6980a70d3d3a07c085b758ed4986e)

- **作者**: chx96642264
- **时间**: 2026-11-19T02:30:27Z
- **提交信息**: [Fix] [NPU] qwen3_5_mtp: adapt mtp.fc quantization as ReplicatedLinear (#49790)

### [44ffcde](https://github.com/sgl-project/sglang/commit/44ffcdead51ed06410217adbb000213f4df45a22)

- **作者**: Lissie
- **时间**: 2026-11-19T02:20:21Z
- **提交信息**: [Perf] [NVIDIA] quantization: Add tuned channelwise FP8 GEMM tile configs for RTX PRO 5000 (#49275)

Co-authored-by: zhanglixi <zhanglixi@modelbest.cn>

### [72fae91](https://github.com/sgl-project/sglang/commit/72fae9100822704ea8628490fd9c4d1155ec32c6)

- **作者**: BourneSun0527
- **时间**: 2026-11-19T02:20:08Z
- **提交信息**: [Doc] Deepseekv4: modify dsv4 npu best practice (#51235)

### [9304abb](https://github.com/sgl-project/sglang/commit/9304abb5321dcf27b28235d53060ecc1438df0f5)

- **作者**: Bingxu Chen
- **时间**: 2026-11-19T01:45:00Z
- **提交信息**: [Test] [AMD] sana-video2: Skip the BF16 softmax attention test when the build is not CUDA (#50220)

### [cde63d2](https://github.com/sgl-project/sglang/commit/cde63d2d9eddc593ca930fbee77ff2662f5492e3)

- **作者**: Michael
- **时间**: 2026-11-19T01:26:29Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX Kimi-K3.1-Pro MXFP4 DFlash curve on MI35x (#50490)

### [8073aea](https://github.com/sgl-project/sglang/commit/8073aea66af5010a700152d8c8d9d2d66b7b49fa)

- **作者**: Shunkangz
- **时间**: 2026-11-19T01:23:20Z
- **提交信息**: [Feat] UnifiedL3: support mooncake storage backend (#46499)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a3eae55](https://github.com/sgl-project/sglang/commit/a3eae555453777c3f4c5ab41e19ef1c9577e0785)

- **作者**: zanes-ops
- **时间**: 2026-11-19T01:00:02Z
- **提交信息**: [Feat] weight_cache: Add the vmm_fd transport (#46953)

Signed-off-by: Zane <zanes@nvidia.com>
Co-authored-by: Shunkang Zhang <182541032+Shunkangz@users.noreply.github.com>
Co-authored-by: Mohammed Abdulwahhab <21993679+mohammedabdulwahhab@users.noreply.github.com>
Co-authored-by: Mohammed Abdulwahhab <furkhan324@berkeley.edu>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [7bb4884](https://github.com/sgl-project/sglang/commit/7bb4884d734e0121058335f3c8210b24c58627fc)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-19T00:36:01Z
- **提交信息**: [Fix] diffusion/qwen-image: Stream the DiT in auto mode when it does not fit the GPU (#50440)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [1f2d76c](https://github.com/sgl-project/sglang/commit/1f2d76c79d425e3c82edb0dad22bdb74d22cb659)

- **作者**: Tan Trinh
- **时间**: 2026-11-19T00:22:24Z
- **提交信息**: [Fix] [AMD] distributed: Fix custom AR capture for DSA DP dual graphs (#36088)

Co-authored-by: Hubert Lu <Hubert.Lu@amd.com>
Co-authored-by: Kevin Mi <45493463+kevin-mii@users.noreply.github.com>
Co-authored-by: Kevin Mi <mikevin920@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6b374a5](https://github.com/sgl-project/sglang/commit/6b374a5502dc840cf2b5d03fff73a4e71873dd89)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-19T00:12:22Z
- **提交信息**: [CI] release: Run weekly, Arm64, MUSA and PPU suites on release branch cut, and test the cut branch (#51368)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-18T07:57:31Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 昨日提交分析（vipshop/cache-dit，6条提交）

### 1. 主要更新类型
- **功能新增**为主：原生FP8融合MLP、多种DBCache校准器（BRACE、BeziCast）、可选SeaCache探针。
- **重构**：移除DBPrune并统一校准器CLI。
- **文档更新**：2026年DiT缓存算法调研归档及各集成结果文档。

### 2. 关键变更点与项目方向的关系
- **FP8融合MLP**直接呼应README中"量化（Quantization）"这一核心能力，将原生FP8支持下沉到算子融合层面，属于推理引擎底层优化的自然延伸。
- **BRACE、BeziCast校准器与SeaCache探针**均为DBCache（一种缓存算法）的校准/评测组件，说明项目正在系统性地构建缓存算法的研究与集成框架，与"Cache"核心定位一致。
- **统一校准器CLI并移除DBPrune**是一次收敞性重构，表明缓存算法生态在快速试错后开始标准化接口，降低维护成本。

### 3. 对项目的影响和潜在意义
- 量化路径（FP8融合）与缓存路径（多校准器）双线并行推进，分别提升推理吞吐和缓存决策质量。
- CLI统一后，未来接入新缓存算法（如SeaCache）的成本显著降低，形成"调研→原型→集成→标准化"的完整研发闭环。
- 文档化调研成果（2026算法综述）有助于沉淀团队在DiT缓存领域的技术积累，提升项目在社区中的专业影响力。

### 4. 值得关注的技术点
- FP8原生融合MLP的精度保持策略与硬件兼容性（是否仅限特定GPU架构）。
- SeaCache作为"可选探针"的插件式设计，以及它与DBCache校准器的协同机制。
- 多校准器（BRACE/BeziCast）在缓存预算分配上的算法差异及实测效果对比文档。
- CLI统一的向后兼容性，以及DBPrune移除后原有工作流的迁移路径。

### 5. 结合README背景对项目发展的影响
cache-dit定位为"具备缓存、并行、量化与CPU卸载的PyTorch原生DiT推理引擎"。本批提交中，FP8融合强化了**量化**支柱，多校准器与SeaCache探针强化了**缓存**支柱，而CLI统一则为持续扩张的算法矩阵提供了稳定的工程基座。整体来看，项目正从"功能堆叠"阶段转向"能力体系化"阶段——通过标准化接口和结构化文档，将散点式算法实验沉淀为可持续演进的引擎能力，这将直接支撑其在DiT高效推理领域的开源竞争力与长期演进。

## 详细提交记录

### [453c1b0](https://github.com/vipshop/cache-dit/commit/453c1b05f9578cfe2a89c4d3e2840cc38439bf5a)

- **作者**: DefTruth
- **时间**: 2026-11-19T14:54:07Z
- **提交信息**: feat: add fused MLP support for native FP8 (#1371)

### [50539e9](https://github.com/vipshop/cache-dit/commit/50539e9ad377040c8862d1a35c1aff53a3065c3e)

- **作者**: DefTruth
- **时间**: 2026-11-19T12:09:43Z
- **提交信息**: feat: add optional SeaCache probe for DBCache (#1370)

* Add optional SeaCache probe for DBCache

* Document SeaCache integration results

### [2640373](https://github.com/vipshop/cache-dit/commit/2640373f045dc3fc67de5929fcf33f10ad9afde2)

- **作者**: DefTruth
- **时间**: 2026-11-19T09:31:59Z
- **提交信息**: feat: add BeziCast calibrator for DBCache (#1369)

* Add BeziCast calibrator for DBCache

* Document BeziCast integration results

### [56c045c](https://github.com/vipshop/cache-dit/commit/56c045c9147cd770fa6ec69a916521daafe1c763)

- **作者**: DefTruth
- **时间**: 2026-11-19T08:15:30Z
- **提交信息**: feat: add BRACE calibrator for DBCache (#1368)

* Add BRACE calibrator for DBCache

* Document BRACE cache integration results

* Fix cache research archive reference

### [a98ba73](https://github.com/vipshop/cache-dit/commit/a98ba733a43835d179b016b60093061dff7369e6)

- **作者**: DefTruth
- **时间**: 2026-11-19T06:28:40Z
- **提交信息**: Remove DBPrune and unify calibrator CLI (#1366)

Closes #1365

### [cea1c67](https://github.com/vipshop/cache-dit/commit/cea1c67b751477748f64af060a6b0ca0a67a7f6c)

- **作者**: DefTruth
- **时间**: 2026-11-19T03:58:44Z
- **提交信息**: docs: add 2026 cache algorithm research (#1364)

Archive the 2026 DiT cache algorithm survey in the cache integration skill.

Closes #1363.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97235
- **最后更新**: 2026-11-20T02:39:25Z

## 提交统计

- **昨日提交总数**: 124
- **提交者数量**: 95
- **主要提交者**: Lantao Jin, trienebutdiene, crunz

## AI分析总结

# vLLM 昨日提交（124 条）综合分析

## 一、主要更新类型
- **Bug 修复占比最高**（约 56 条）：覆盖内核数值、KV 缓存、调度器、多模态、结构化输出、投机解码水印与前端 API 兼容性。
- **性能优化次之**（约 34 条）：集中在 MoE、MLA、量化（W4A4/W4A16/FP8/MXFP4）、ROCm/CPU 路径与投机解码专用 drafter。
- **功能新增与模型生态**（约 24 条）：Inkling 2、HY4 Flash、GLM-5.3 LoRA、Qwen3.5 XPU 等新模型/LoRA 支持，Rust 前端能力扩展，HiSparse 新特性，CUDA Graph 覆盖。
- **CI/基础设施与重构**（约 10 条）：Python 3.14 默认化、CI 自动分片、CUDA graph 策略下沉 Platform、torchao 装饰器移除。

## 二、关键变更与项目方向
- **多硬件平台深度投入**：ROCm/AMD 提交 15 条以上（AITER 升级、gfx1250 性能调优、split-KV 内核、MXFP4 在线量化）；Intel XPU 获采样内核、MoE 转换与 CI 扩充；CPU 获 AArch64 top-k/top-p 内核。契合 README"为所有人提供易用、快速、低成本服务"的普惠目标。
- **服务架构现代化**：Rust 前端批量补全、EPD 握手、Responses API 修复；KV Connector 启动通知、MultiConnector 握手修复、NIXL push 停滞修复、EC 分层连接器；RL 权重打包传输统一 NCCL/IPC 单缓冲区布局。
- **长上下文与投机解码突破**：HiSparse（QSA 支持、页管理、共享 KV 层绑定）、Mooncake 限额与传输校验；Kimi K3.1/DSpark 专用 drafter、Newton 步拒绝、MTP re-prefill 边界、DeepSeek-4.1 Flash Dynamo 预设。
- **快速启动与加载**：移除 copy 模式、WNA16 预处理权重、加载计划 copy-time 优化、CPU offload 层级重载保留 Engram。

## 三、项目影响与潜在意义
- 内核级修复（MXFP8 非对齐维度、`fused_qk_norm_rope` 溢出、DeepGEMM SwiGLU clamp 缺失、chunk_scaled_dot_kkt beta 时机）直接提升数值正确性，消除难复现的静默错误。
- 峰值内存、调度公平性（encoder 限制下不被后序图像请求抢占）、DoS 防护（`max_tokenize_tokens` 上限）等增强生产健壮性。
- 量化路径吞吐提升（W4A16 解码最高 +44%）、SM90 融合（Qwen4Exp 上投影与门控混合）直接改善用户可感知的推理成本。
- 多平台内核与 CI 扩充降低硬件碎片化维护风险，提升 AMD/Intel/ARM 社区吸引力；批不变性修复与 API 兼容性修复守住正确性底线。

## 四、值得关注的技术点
- **AI 辅助开发常态化**：绝大多数提交含 Claude/Codex/Cursor/vllm-agent 共同署名，人机协作已成该仓库核心工程流程。
- **分层量化与端到端算子融合**：gfx1250 W4A4 融合 silu+量化+预洗牌权重、MXFP4 混合专家首末层、ITER tuned GEMM 用于 Router。
- **按架构分档定制内核**：LFM3-VL 编码器图、FA4 SplitKV 预热、paged dense prefill 特化、SM90 专属融合，贡献者需关注 target-specific 路径。
- **细粒度资源治理**：grammar bitmask 不固定、查询缓存释放、CPU offload 随 connector 关闭释放、异步调度深度可配置（Model Runner V2）。
- **多模态流水线显式化**：Omni embedding placement 信息透传，避免视频音频宿主端冗余读取，placement 语义在链路中逐步贯通。

## 五、整体发展意义
这批提交表明 vLLM 正同时推进三条主线：**多硬件后端性能与正确性对齐**、**服务架构现代化**（Rust 前端、KV 分层卸载、NIXL/RL 传输）、**长上下文与投机解码效率突破**。项目已从"功能扩张"转向"多平台深度优化 + 工程质量加固"并重，CI 分片与 Python 版本升级支撑高吞吐持续交付。在 README"Easy, fast, and cheap"定位下，这些变更共同强化吞吐/成本竞争力，并巩固其作为生产级 LLM 推理引擎的可靠性基线，为更大规模分布式推理与训练一体化铺路，进一步巩固其主流 LLM 服务框架地位。

## 详细提交记录

### [54bf2e7](https://github.com/vllm-project/vllm/commit/54bf2e700e05cc70f59ae23272640bfe3ebf776a)

- **作者**: Josh Schell
- **时间**: 2026-11-19T23:49:18Z
- **提交信息**: [ROCm] AITER v0.1.29.post1 (#67959)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0e2e6a4](https://github.com/vllm-project/vllm/commit/0e2e6a44b3808dc24f743ba50f097483395e8040)

- **作者**: Micah Williamson
- **时间**: 2026-11-19T23:16:15Z
- **提交信息**: [ROCm][MiniMax-M3] Select the whole-layer mono decode with --monokernel and remove mono/envs.py (#66184)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [55bc73e](https://github.com/vllm-project/vllm/commit/55bc73ecd0f5ece5328a5e7a48b63d3f9b599e8e)

- **作者**: Matthew Bonanni
- **时间**: 2026-11-19T23:12:50Z
- **提交信息**: [HiSparse] Batch owner bookkeeping when unpinning pages (#66631)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [54f7630](https://github.com/vllm-project/vllm/commit/54f7630a1cbf9813079408052e22a1b82f4b59b1)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-19T22:52:10Z
- **提交信息**: [Bugfix][KV Offload] Release SimpleCPUOffload CPU caches on connector shutdown (#68710)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abbddbf](https://github.com/vllm-project/vllm/commit/abbddbfb74dbba42aec881610d5e8684c50b3b96)

- **作者**: Shao-Chun Lee
- **时间**: 2026-11-19T22:44:41Z
- **提交信息**: [ROCm][Perf][DSv4] gfx1250 W4A4 MoE: fused silu + fused quant + preshuffled weights  (#63396)

Signed-off-by: ShaoChunLee <Shao-Chun.Lee@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [ab91867](https://github.com/vllm-project/vllm/commit/ab91867b58c255205fe4b70c2dafc73b230316ac)

- **作者**: Shao-Chun Lee
- **时间**: 2026-11-19T22:40:58Z
- **提交信息**: [ROCm][Perf][DSv4] Use AITER tuned GEMM for the Router GEMM on gfx1250 (#63243)

Signed-off-by: ShaoChunLee <Shao-Chun.Lee@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [44303ec](https://github.com/vllm-project/vllm/commit/44303eca78ecc3d61dfbae90ba5f87d58a3e7597)

- **作者**: my-git9
- **时间**: 2026-11-19T22:35:41Z
- **提交信息**: [Bugfix][HiSparse] Keep shared KV layers bound when the target is host-resident (#68586)

Signed-off-by: xin.li <xin.li@daocloud.io>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b582592](https://github.com/vllm-project/vllm/commit/b582592d5a628cc24d3899da1e17f835a346b854)

- **作者**: Hanyu Yang
- **时间**: 2026-11-19T21:55:03Z
- **提交信息**: [Bugfix][CPU] Reject -1 placeholder drafts in the C++ rejection sampler (#61127)

Signed-off-by: Hanyu <hanyu.yang.92@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [878ae13](https://github.com/vllm-project/vllm/commit/878ae13ff03875d95928585ca2704455581c8700)

- **作者**: Divakar Verma
- **时间**: 2026-11-19T21:17:21Z
- **提交信息**: [CI][ROCm] Clean up the specialized decode test primitives (follow-up to #67135) (#68311)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bc93224](https://github.com/vllm-project/vllm/commit/bc93224f7c03e629c67cb2ac97baf16d9f18f478)

- **作者**: Li, Jiang
- **时间**: 2026-11-19T20:49:58Z
- **提交信息**: [Bugfix][Transformers backend] Fuse packed qkv that is sliced, not split (#68698)

Signed-off-by: jiang1.li <jiang1.li@intel.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e69731f](https://github.com/vllm-project/vllm/commit/e69731fd6f34b281a8ff026a0df5e86963ee9e74)

- **作者**: zhenwenqi2024
- **时间**: 2026-11-19T20:44:01Z
- **提交信息**: [Bugfix][HiSparse] Skip GPU restores for cancelled KV imports (#68729)

Signed-off-by: zhenwenqi2024 <zhenwenqi_2022@qq.com>

### [f777885](https://github.com/vllm-project/vllm/commit/f7778853fb52e44ad510c1e9404baa4432f365f6)

- **作者**: Seyfal Sultanov
- **时间**: 2026-11-19T20:33:46Z
- **提交信息**: [Bugfix][FA4] Cover paged dense prefill specializations in the warmup (#63279)

Signed-off-by: Seyfal Sultanov <seyfal.s@outlook.com>
Signed-off-by: LopezCastroRoberto <robertol.c510@gmail.com>
Co-authored-by: LopezCastroRoberto <robertol.c510@gmail.com>

### [9e17d4a](https://github.com/vllm-project/vllm/commit/9e17d4a9865dc0294db1c6126be16d7341bc787d)

- **作者**: aoshen02
- **时间**: 2026-11-19T20:26:36Z
- **提交信息**: [Bugfix][MoE] Fix missing SwiGLU clamp in batched DeepGEMM (#68084)

Signed-off-by: fh3 <a@b>
Co-authored-by: fh3 <a@b>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Codex <codex@openai.com>

### [f510422](https://github.com/vllm-project/vllm/commit/f5104227323978ce51e707456407e8fc6fd38923)

- **作者**: Misha Goin
- **时间**: 2026-11-19T20:21:43Z
- **提交信息**: [Kimi K3.1][Specialized decode] Serve GQA DSpark drafts on the specialized drafter (#68701)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [076fe95](https://github.com/vllm-project/vllm/commit/076fe95164c4c4fa5f5885713dee92b6d397da93)

- **作者**: Roberto L. Castro
- **时间**: 2026-11-19T20:17:23Z
- **提交信息**: [Kernel] Restructure DSA kernels (#68009)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>

### [5328ae2](https://github.com/vllm-project/vllm/commit/5328ae2fefc42039c15e8ecae9aefb5587df8efd)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-19T20:04:40Z
- **提交信息**: [Kernel][Perf] Run GLM-5.3-Flash FP8 routed experts in SM90 DeepGEMM Mega MoE (#66812)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a510470](https://github.com/vllm-project/vllm/commit/a51047055c8b0f1d93db8f36cc9e4f8b38adb45f)

- **作者**: Thang Nguyen
- **时间**: 2026-11-19T19:36:04Z
- **提交信息**: [CI] Enroll 10 steps in automatic sharding (#68257)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9b8bfd7](https://github.com/vllm-project/vllm/commit/9b8bfd73ed31bbbe5510e6adccd5e1cd72e096f7)

- **作者**: Banghao Xu
- **时间**: 2026-11-19T19:34:00Z
- **提交信息**: [MM][CG] Add encoder CUDA graph support for LFM3-VL (#67976)

Signed-off-by: shuoyue21 <xbh2002@outlook.com>

### [ae8144b](https://github.com/vllm-project/vllm/commit/ae8144bc1dde44e96be5b8ff3416874517a65efc)

- **作者**: Luca Motz
- **时间**: 2026-11-19T19:32:57Z
- **提交信息**: [Bugfix][Structured Output] Don't pin the grammar bitmask (#68764)

Signed-off-by: Luca Motz <luca.motz@icloud.com>

### [0222f86](https://github.com/vllm-project/vllm/commit/0222f863c6c1701779512c80fae686e6624d6cec)

- **作者**: danielafrimi
- **时间**: 2026-11-19T19:27:48Z
- **提交信息**: [Bugfix][Kernel] Fix MXFP8 linear layers whose N is not a multiple of 8 or 32 (#68353)

Signed-off-by: Daniel Afrimi <dafrimi@nvidia.com>
Co-authored-by: Omer Ullman Argov <118735753+omera-nv@users.noreply.github.com>
Co-authored-by: Daniel Serebrenik <daserebrenik@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cdb3593](https://github.com/vllm-project/vllm/commit/cdb3593068fc338ac0fbe1e96dd4eacafc2eb141)

- **作者**: Jonathan Buck
- **时间**: 2026-11-19T19:18:15Z
- **提交信息**: [Bugfix][Scheduler] Don't let later image requests overtake a request deferred for encoder limits (#67385)

Signed-off-by: Jonathan Buck <jonabuck@amazon.com>
Co-authored-by: Jonathan Buck <jonabuck@amazon.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fab6445](https://github.com/vllm-project/vllm/commit/fab6445e755c82fce10cba833e372436a7ea3629)

- **作者**: seansie0830
- **时间**: 2026-11-19T18:51:05Z
- **提交信息**: [Frontend] Enforce max_tokenize_tokens limit to prevent unbounded inputs and DoS (#67348)

Signed-off-by: seansie <seansie0830@gmail.com>
Signed-off-by: seansie0830 <85049950+seansie0830@users.noreply.github.com>

### [b2c92fa](https://github.com/vllm-project/vllm/commit/b2c92fa9c1d8be6790ddd0852b547bbf927bfbd0)

- **作者**: Jonathan Buck
- **时间**: 2026-11-19T18:29:55Z
- **提交信息**: [Bugfix][FA4] Warm the SplitKV combine kernel for the layer's query heads (#67981)

Signed-off-by: Jonathan Buck <jonabuck@amazon.com>
Co-authored-by: Jonathan Buck <jonabuck@amazon.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [0ae7032](https://github.com/vllm-project/vllm/commit/0ae7032d732db4cdffc3a0a7677f88d23fb12c06)

- **作者**: Mengdi Wu
- **时间**: 2026-11-19T18:24:08Z
- **提交信息**: [Bugfix][Kernel] Add __syncwarp before the lane-0 stores in the fused KDA decode block reductions (#65241)

Signed-off-by: Mengdi Wu <wmengd@gmail.com>

### [0d8b46b](https://github.com/vllm-project/vllm/commit/0d8b46bf33b26c37c08d59ad3caa7db97f3d0bd3)

- **作者**: lucas-santos-amd
- **时间**: 2026-11-19T18:19:25Z
- **提交信息**: [ROCm][Perf][MLA] Use AITER Triton bf16 BMM for the decode W_UV when tuned (#63397)

Signed-off-by: Lucas Santos <Lucas.Santos@amd.com>
Signed-off-by: lucas-santos-amd <Lucas.Santos@amd.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [3128d19](https://github.com/vllm-project/vllm/commit/3128d196a7d49010660bf2c6ec9b45bd6b9f804b)

- **作者**: danielafrimi
- **时间**: 2026-11-19T18:16:57Z
- **提交信息**: [KV Cache] Allow mixed page sizes in a layer-compact KV layout (for Nemotron Shortcut) (#67941)

Signed-off-by: Daniel Afrimi <dafrimi@nvidia.com>
Co-authored-by: Netanel Haber <nhaber@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6cd35ed](https://github.com/vllm-project/vllm/commit/6cd35edf3a31f5e24b25795e74991ae9d27ee635)

- **作者**: trienebutdiene
- **时间**: 2026-11-19T17:54:06Z
- **提交信息**: [Perf][MoE] Select full-warp top-k rows with redux.sync and keep selections in registers (SM80+) (#62912)

Signed-off-by: kimseunghyun <incongnito12@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Gin-Sin <ginxian@foxmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2359b44](https://github.com/vllm-project/vllm/commit/2359b442c6872ea54f3fe78200033eb55abf81de)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-19T17:30:54Z
- **提交信息**: [Model][Perf] Inkling 2: Humming expert GEMMs on Hopper (#68761)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4ae5147](https://github.com/vllm-project/vllm/commit/4ae51478154cbc4e2fc8aa7d664ddbc0b249102c)

- **作者**: Wentao Ye
- **时间**: 2026-11-19T16:58:50Z
- **提交信息**: [Refactor] Remove dead code in models (#68510)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [a5a2cde](https://github.com/vllm-project/vllm/commit/a5a2cdefd1dd9abf28e97da8547f6e976654062d)

- **作者**: afriedri-amd
- **时间**: 2026-11-19T16:48:29Z
- **提交信息**: [ROCm] Move AITER MXFP4 linear op registration into _aiter_ops (#65251)

Signed-off-by: Andy Friedrich <afriedri@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d33bfee](https://github.com/vllm-project/vllm/commit/d33bfeef40edb158ddae320038737ee7923ad66f)

- **作者**: shaohuaxi
- **时间**: 2026-11-19T16:27:54Z
- **提交信息**: [Bugfix][Pooling] Release cached queries when Flash scoring is cancelled (#56617)

Signed-off-by: 子华 <huaxi.shx@alibaba-inc.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [d2da27e](https://github.com/vllm-project/vllm/commit/d2da27eb2defb88377636fba83d9a41ad35bf44d)

- **作者**: Harry Mellor
- **时间**: 2026-11-19T15:44:06Z
- **提交信息**: [Bugfix][torch.compile] Find the compiled module through `*args` in the bytecode hook (#68717)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9f6c850](https://github.com/vllm-project/vllm/commit/9f6c850b40d983a384671a20eea3ba16974c279a)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-19T15:35:49Z
- **提交信息**: [Feature][Frontend] Add metadata value to mm_payload on render requests (#65018)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>

### [9a2e603](https://github.com/vllm-project/vllm/commit/9a2e60358dc851dacfaa2dbf82286cec1ed60096)

- **作者**: Bugen Zhao
- **时间**: 2026-11-19T15:08:44Z
- **提交信息**: [Rust Frontend] Support batched prompts on /v1/completions (#68390)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: muonchaser <1507272310@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8cc54e2](https://github.com/vllm-project/vllm/commit/8cc54e23c9de35ea6a1671939733f0c5ae2560e7)

- **作者**: Bugen Zhao
- **时间**: 2026-11-19T15:07:44Z
- **提交信息**: [Rust Frontend] Serve /generative_scoring (#68612)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: jesco-absolut <team@srswti.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8828834](https://github.com/vllm-project/vllm/commit/8828834fb105e71cd2da399f5e05941fb35c923a)

- **作者**: Canlin Guo
- **时间**: 2026-11-19T15:06:48Z
- **提交信息**: [Bugfix][Rust Frontend] Decode the Mooncake store's lookup_lease stats (#68584)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8283763](https://github.com/vllm-project/vllm/commit/8283763f58569d9e90e998b005d02463de33449c)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-19T15:02:59Z
- **提交信息**: [ROCm][CI] Dump child process stacks before the Model Executor test timeout (#68652)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6bc4849](https://github.com/vllm-project/vllm/commit/6bc4849aa413c3952b198a7c1a94c4fa681f16fc)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-19T14:46:31Z
- **提交信息**: [Bugfix][Kernel] fused_qk_norm_rope: fix int32 offset overflow and NeoX partial-rotary corruption (#68386)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5e921de](https://github.com/vllm-project/vllm/commit/5e921de215cd9b4c1c129473198c94b8c4e4556c)

- **作者**: Hairui Luo
- **时间**: 2026-11-19T14:46:01Z
- **提交信息**: [Hisparse] Support HiSparse for QSA  (#59209)

Signed-off-by: lHrHenry233 <2381623149@qq.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [79e9376](https://github.com/vllm-project/vllm/commit/79e937641247236e124b94860d71e42b3d6d768d)

- **作者**: Tianyu Guo
- **时间**: 2026-11-19T14:36:10Z
- **提交信息**: [Rust Frontend][EPD] Report metadata-only input capability in engine handshake (#68565)

Signed-off-by: Tianyu Guo <guoty@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2986b5c](https://github.com/vllm-project/vllm/commit/2986b5cb092cb0f1a1fafcb1f031b2a59b1d7448)

- **作者**: WMC
- **时间**: 2026-11-19T14:30:25Z
- **提交信息**: [ROCm][Perf] W4A16: fix the gfx1151 bf16 tile cliff at decode-sized M (up to +44% decode throughput) (#66133)

Signed-off-by: weimin023 <tnwilly@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fd774d6](https://github.com/vllm-project/vllm/commit/fd774d6d89b7fcbef84c3f93e3cb13aec830cb57)

- **作者**: zofia
- **时间**: 2026-11-19T14:28:19Z
- **提交信息**: [XPU] Add VLLM_XPU_SUPPORT_FP8_QUERY to control FP8 query in flash attention (#67860)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Signed-off-by: zofia <110436990+zufangzhu@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e805e25](https://github.com/vllm-project/vllm/commit/e805e2546ee408fe4e4a61b7aae3364e2abde50d)

- **作者**: ChengYM
- **时间**: 2026-11-19T14:17:37Z
- **提交信息**: [Bugfix][ROCm][MoRIIO] Fix heterogeneous-TP WRITE of NVFP4 KV pages and replicated indexer caches (#68072)

Signed-off-by: ChengYM5685 <Yueming.Cheng@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [8ff4edd](https://github.com/vllm-project/vllm/commit/8ff4edd0b67d40bc70712c6dec351ed42476735a)

- **作者**: stefankoncarevic
- **时间**: 2026-11-19T14:08:02Z
- **提交信息**: [ROCm][Bugfix] Avoid torch 2.13 Inductor gather bug in Nemotron diffusion sampler (#68694)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [fe537b1](https://github.com/vllm-project/vllm/commit/fe537b1785f3a636365306d532e4fa0daf959698)

- **作者**: simon-veitner-redhat
- **时间**: 2026-11-19T13:55:14Z
- **提交信息**: [Bugfix][Watermarking] Detect repeated contexts across the prompt boundary in speculative rows (#67947)

### [a3b845e](https://github.com/vllm-project/vllm/commit/a3b845e2265c495e20661e788003cddf2cb05953)

- **作者**: Himanshu Jaju
- **时间**: 2026-11-19T13:27:39Z
- **提交信息**: [KV Connector] Honor per-request Mooncake offload limits (#68529)

Signed-off-by: Himanshu Jaju <hj@mistral.ai>

### [1ae1b64](https://github.com/vllm-project/vllm/commit/1ae1b64807ff6be2a0d3f942dbad0a59a663a02a)

- **作者**: crunz
- **时间**: 2026-11-19T12:40:24Z
- **提交信息**: [Bugfix][Frontend] Preserve assistant refusal history in the HF renderer (#67954)

Signed-off-by: crunz <317506543+crunz-ailab@users.noreply.github.com>

### [fd2b7ac](https://github.com/vllm-project/vllm/commit/fd2b7ac40fba94906ad44c84b6a51e77c9fae8a8)

- **作者**: fxmarty-amd
- **时间**: 2026-11-19T12:15:02Z
- **提交信息**: [Quantization] Lower peak memory of online requantization, support block-FP8 to MXFP4 (#68171)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [283bf21](https://github.com/vllm-project/vllm/commit/283bf21b69686a9091fc59fa74b6c46303d365cc)

- **作者**: Archit Shukla
- **时间**: 2026-11-19T12:12:18Z
- **提交信息**: [Bugfix][Multimodal] Accept NumPy images in vLLM's own HF processors (#68655)

Signed-off-by: Archit Shukla <architshukla546@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e2c9644](https://github.com/vllm-project/vllm/commit/e2c96445a5814fa44f1ba79cb299b3656c634481)

- **作者**: Samu Tamminen
- **时间**: 2026-11-19T12:06:00Z
- **提交信息**: [Bugfix][ROCm] Kimi-K3: don't bake the fused decode MLA path into PIECEWISE graphs (#66578)

Signed-off-by: Samu Tamminen <samu.tamminen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bd95fa0](https://github.com/vllm-project/vllm/commit/bd95fa0e689f81246b46f91a4b9710e439d882c4)

- **作者**: yhcheong (vllmellm)
- **时间**: 2026-11-19T12:05:44Z
- **提交信息**: [Bugfix][Quantization] Remove the Qwen3.5 MTP draft quantization workaround (#67414)

Signed-off-by: vllmellm <vllm.ellm@embeddedllm.com>

### [3487a1c](https://github.com/vllm-project/vllm/commit/3487a1c10c3718f0fe427148dd184ed16ca15d24)

- **作者**: Isotr0py
- **时间**: 2026-11-19T12:04:12Z
- **提交信息**: [Rust Frontend] Add server-level mm processor kwargs support (#68186)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f0c592b](https://github.com/vllm-project/vllm/commit/f0c592bfddc1394b5e74abc0a9d340e947aba41f)

- **作者**: AlexHuang
- **时间**: 2026-11-19T11:45:47Z
- **提交信息**: [Bugfix][KV Offload] Scope block reuse fences to the source pool (#68058)

Signed-off-by: Alex <alex.tech.lab@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [2a55c28](https://github.com/vllm-project/vllm/commit/2a55c28737f5ef7f6839509649d023d8a6151b75)

- **作者**: Ylean
- **时间**: 2026-11-19T11:00:08Z
- **提交信息**: [Bugfix][Multimodal] Normalize negative-stride image inputs (#68367)

Signed-off-by: Ylean <61880605+Woolgathererer@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [370a3a7](https://github.com/vllm-project/vllm/commit/370a3a7adcd2fe279b06730a55eec2122b1cc41e)

- **作者**: Oxana Korzh
- **时间**: 2026-11-19T10:58:25Z
- **提交信息**: [ROCm][Perf][DSv4.1] Pack the decode sparse-MLA ragged top-k in one launch from the MXFP4 indexer's row bounds (#67365)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bca3871](https://github.com/vllm-project/vllm/commit/bca3871c5a8d0f8c0a56947756500293fcc11396)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-19T10:43:09Z
- **提交信息**: [Bugfix][Kernel] Pass packed rows to the sm90 FlashInfer FP8 block-scale GEMM (#64040)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [fe7ab1d](https://github.com/vllm-project/vllm/commit/fe7ab1d910b474d9f85a55256e11c3866f31534e)

- **作者**: Yibo Liu
- **时间**: 2026-11-19T10:38:28Z
- **提交信息**: [Bugfix][Multimodal] LFM2-VL: honor do_image_splitting and use_thumbnail (#68055)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>

### [392ed87](https://github.com/vllm-project/vllm/commit/392ed873c7fed4c41fafaad022f83f7d0fe9f57a)

- **作者**: anhtra3889
- **时间**: 2026-11-19T10:15:54Z
- **提交信息**: [Perf][Parser] Skip per-tick conversion of non-JSON DeepSeek DSML argument values (#68070)

Signed-off-by: anhtra3889 <288260823+anhtra3889@users.noreply.github.com>
Co-authored-by: anhtra3889 <288260823+anhtra3889@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [c5db9bd](https://github.com/vllm-project/vllm/commit/c5db9bd35fb0b0ca75a670d037b7a1d9aa8cfcc8)

- **作者**: Thang Nguyen
- **时间**: 2026-11-19T10:03:20Z
- **提交信息**: [Build] Cap nvidia-cudnn-frontend below 1.33 (#68566)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a38ff11](https://github.com/vllm-project/vllm/commit/a38ff116244ef03dc16a587be963ceb41fe836b9)

- **作者**: Himanshu Jaju
- **时间**: 2026-11-19T09:57:42Z
- **提交信息**: [KV Connector] Validate Mooncake results and complete failed transfers (#67939)

Signed-off-by: Himanshu Jaju <hj@mistral.ai>

### [438e9e8](https://github.com/vllm-project/vllm/commit/438e9e8ac7e5e8ec3bedb84d28370ea7e2a1c0c0)

- **作者**: Jared Wen
- **时间**: 2026-11-19T09:39:29Z
- **提交信息**: [CI][Test] Skip HYV4 and Inkling in PP equivalence below Hopper (#68604)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [309ef69](https://github.com/vllm-project/vllm/commit/309ef692859a6972f1e63c8b8ea9bc6aee9ca05d)

- **作者**: Jared Wen
- **时间**: 2026-11-19T09:35:23Z
- **提交信息**: [ROCm][Perf][Qwen4Exp] Export PLE short-conv prefill checkpoints on ROCm (#68574)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cc5dafc](https://github.com/vllm-project/vllm/commit/cc5dafc1362cca0e5117fc07b5dcaf905f9abbff)

- **作者**: micyan01
- **时间**: 2026-11-19T09:27:21Z
- **提交信息**: [CPU] Add AArch64 top-k and top-p sampling kernels (#62440)

Signed-off-by: Tianmu Li <tianmu.li@intel.com>
Signed-off-by: Fadi Arafeh <fadi.arafeh@arm.com>
Signed-off-by: Rehan Khan <Rehan.Khan7@ibm.com>
Signed-off-by: Michael Yang <michael.yang@arm.com>
Co-authored-by: Tianmu Li <tianmu.li@intel.com>
Co-authored-by: Fadi Arafeh <fadi.arafeh@arm.com>
Co-authored-by: Rehan Khan <Rehan.Khan7@ibm.com>
Co-authored-by: Akash kaothalkar <akash.kaothalkar@ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b4853f2](https://github.com/vllm-project/vllm/commit/b4853f2f4953a9f3a2d7ce10fe7c540246382326)

- **作者**: Tianyu Guo
- **时间**: 2026-11-19T09:06:30Z
- **提交信息**: [Bugfix] Make Unlimited-OCR-2 DASH routing batch invariant (#68563)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [33fa579](https://github.com/vllm-project/vllm/commit/33fa579edcf4f90d76c62e82db6ec6c9aefd73f5)

- **作者**: Shoufa Zhang
- **时间**: 2026-11-19T08:49:14Z
- **提交信息**: [Bugfix][Spec Decode] Add packed_modules_mapping to DeepSeek-V4 DSpark models (#65647)

Signed-off-by: Shoufa Zhang <peterzhang987723@users.noreply.github.com>
Co-authored-by: Shoufa Zhang <peterzhang987723@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5173b1d](https://github.com/vllm-project/vllm/commit/5173b1d5607ac9f0592e7600955fe8567f72e14b)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-19T08:35:51Z
- **提交信息**: [Bugfix][Multimodal] Turn off the extensible KV cache for Unlimited-OCR-2 (#68254)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a87e3a6](https://github.com/vllm-project/vllm/commit/a87e3a6554891f43ad81168a2a89397de91e9654)

- **作者**: Matt
- **时间**: 2026-11-19T08:11:06Z
- **提交信息**: [ROCm][Attention] AITER FA: dedicated split-KV kernels for decode and speculative-decode verify (GQA 8, head 64, FP8 KV) (#67133)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [7a62ca0](https://github.com/vllm-project/vllm/commit/7a62ca0666e9153bd67b6ac24c4e10b1f0f6fa64)

- **作者**: liuzhenwei
- **时间**: 2026-11-19T08:06:36Z
- **提交信息**: [XPU][CI] Enable sampler-flag and logits-processor tests on XPU (#68541)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dac27b6](https://github.com/vllm-project/vllm/commit/dac27b601633cdc48f096dcbd643fe15c1b33c59)

- **作者**: Yejing Lai
- **时间**: 2026-11-19T07:54:10Z
- **提交信息**: [XPU][UT]Convert awq-packed MoE qweight to the gptq-equivalent layout on xpu (#48552)

Signed-off-by: Lai, Yejing <yejing.lai@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [d9162cc](https://github.com/vllm-project/vllm/commit/d9162cc8fcd202ab5bf2fb586dd17cde46e96280)

- **作者**: yang zhejun
- **时间**: 2026-11-19T07:49:12Z
- **提交信息**: [Do Not Merge][Build] Point vllm-flash-attn at vllm-project/flash-attention#222 for CI (#68348)

Signed-off-by: yzj <zjyang@mail.ustc.edu.cn>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [4c1ddc6](https://github.com/vllm-project/vllm/commit/4c1ddc6d9f38230bad4daa4844219a3ca3765673)

- **作者**: ℍ𝕠𝕝𝕝𝕠𝕨 𝕄𝕒𝕟
- **时间**: 2026-11-19T07:44:44Z
- **提交信息**: [LoRA][Model] Add LoRA support for GLM-5.3-Flash (#56327)

Signed-off-by: Hollow Man <hollowman@opensuse.org>
Co-authored-by: Jack Rao <jack.rao@baseten.co>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2ecd940](https://github.com/vllm-project/vllm/commit/2ecd940907832da41a07729153baa87e15bab892)

- **作者**: Ondre
- **时间**: 2026-11-19T07:44:16Z
- **提交信息**: [Bugfix][LoRA] Allow non-divisible BLIP-2 encoder budgets (#67271)

Signed-off-by: huangwanjun <huangwanjun@shizhuang-inc.com>
Co-authored-by: huangwanjun <huangwanjun@shizhuang-inc.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: linitra24 <renshuang.zhou@daocloud.io>

### [ecc827e](https://github.com/vllm-project/vllm/commit/ecc827ebbf627792e97a44f328fddac95e293129)

- **作者**: xiangdong
- **时间**: 2026-11-19T06:54:55Z
- **提交信息**: [XPU][CI]Expand attention and worker tests in Intel GPU CI (#67833)

Signed-off-by: zengxian <xiangdong.zeng@intel.com>

### [949de05](https://github.com/vllm-project/vllm/commit/949de0581ae886c12dfc9b10910f4123b60847d5)

- **作者**: Michael Schmid
- **时间**: 2026-11-19T06:51:33Z
- **提交信息**: [Core] Configurable async scheduling depth for Model Runner V2 (#64145)

Signed-off-by: Michael Schmid <mschmid@mirantis.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5e2b45e](https://github.com/vllm-project/vllm/commit/5e2b45e993cc04edc12a3d18aabbf2e55b268558)

- **作者**: Oxana Korzh
- **时间**: 2026-11-19T06:40:34Z
- **提交信息**: [ROCm][Perf][DSv4.1] Insert the compressed KV cache inside the compression launch (#67364)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [485ff49](https://github.com/vllm-project/vllm/commit/485ff495438faf54a859bed9c8351284999bbd3b)

- **作者**: Oxana Korzh
- **时间**: 2026-11-19T06:38:52Z
- **提交信息**: [ROCm][Perf][DSv4.1] Build the MXFP4 indexer decode metadata in one launch (#67363)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7d38ee9](https://github.com/vllm-project/vllm/commit/7d38ee9f61a87290bdeee9a353a31480cffe0dc6)

- **作者**: Aaron Hao
- **时间**: 2026-11-19T06:35:43Z
- **提交信息**: [Frontend] generate: keep sample logprobs as engine rows and render them without objects (#60542)

Signed-off-by: hao-aaron <aaronhao@inferact.ai>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [791d86d](https://github.com/vllm-project/vllm/commit/791d86d2659a9a971b39f8dce8de79382e0f9687)

- **作者**: Nick Hill
- **时间**: 2026-11-19T06:31:25Z
- **提交信息**: [CI/Build] Make Python 3.14 the default for images and CI (#68457)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [d2d7263](https://github.com/vllm-project/vllm/commit/d2d7263541a20a8249cd0ea149784be4bd98fd23)

- **作者**: Ronald
- **时间**: 2026-11-19T06:20:49Z
- **提交信息**: [Bugfix][Model Loader] Preserve CPU-offloaded Engram storage during layerwise reload (#68048)

Signed-off-by: Ronald1995 <ronaldautomobile@163.com>

### [c58477b](https://github.com/vllm-project/vllm/commit/c58477b516f67808993699265bd04125538b3351)

- **作者**: Francesco Fusco
- **时间**: 2026-11-19T06:18:33Z
- **提交信息**: [Bugfix][Spec Decode] Reject non-finite Newton steps in the acceptance estimator refit (#68164)

Signed-off-by: Francesco Fusco <ffu@zurich.ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f4b4d19](https://github.com/vllm-project/vllm/commit/f4b4d194d0b91bcad5679df749aea94948066c6f)

- **作者**: Vivian Chen NV
- **时间**: 2026-11-19T06:18:24Z
- **提交信息**: [Bugfix][Core] Fix Gemma-4 MTP prefix-cache hit loss when lookahead block hashes are off (#65263)

Signed-off-by: Vivian Chen <140748220+xuanzic@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2480ed2](https://github.com/vllm-project/vllm/commit/2480ed2fad5223309f32746be3b35b709036500f)

- **作者**: Jared Wen
- **时间**: 2026-11-19T06:15:16Z
- **提交信息**: [CI][Test] Ignore the key file path when checking that the watermark key is not quoted (#68592)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9c1d45c](https://github.com/vllm-project/vllm/commit/9c1d45c21836370104d4eb51d3b46eda20719c47)

- **作者**: aoshen02
- **时间**: 2026-11-19T05:50:14Z
- **提交信息**: [Model Loader] Remove the torchao reload decorator (#68329)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [dd60cb8](https://github.com/vllm-project/vllm/commit/dd60cb85406ebb0e7222a3f6b8fbaf27951996d6)

- **作者**: Wang, Jian4
- **时间**: 2026-11-19T05:43:33Z
- **提交信息**: [Models][XPU] Port eager Qwen3.5 models and fuse MoE decode (#64687)

Signed-off-by: hzjane <a1015616934@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9727942](https://github.com/vllm-project/vllm/commit/972794206ccc5770b47d0bdc839f32893dc14df6)

- **作者**: Aaron Hao
- **时间**: 2026-11-19T05:42:10Z
- **提交信息**: [RL][Weight Transfer] Packed transfer: one buffer-sized chunk layout for NCCL and IPC (#68043)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [5a80377](https://github.com/vllm-project/vllm/commit/5a803779c39d6f71d4534aebf8715d2b423d3eef)

- **作者**: Ganesh R
- **时间**: 2026-11-19T05:31:56Z
- **提交信息**: [CPU] Warm up the remaining sampling kernels before serving (#64522)

Signed-off-by: Ganesh R <Ganesh.R@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [174ae55](https://github.com/vllm-project/vllm/commit/174ae553252fb85daf1b1db69cd84790c152239d)

- **作者**: Sheral Kumar
- **时间**: 2026-11-19T05:26:35Z
- **提交信息**: [ROCm][CI] Retarget `mi300_dpx` jobs to `mi300_1` queue temporarily (#68568)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cf2e8d0](https://github.com/vllm-project/vllm/commit/cf2e8d036a5dd28a3bde0d831a9794a0b1e036dd)

- **作者**: Bo Pang
- **时间**: 2026-11-19T05:19:49Z
- **提交信息**: [Refactor] Move CUDA graph sizing policy into Platform (#68552)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Codex <noreply@openai.com>

### [0c1fcdb](https://github.com/vllm-project/vllm/commit/0c1fcdb649bb84ea178379c7badf2953fe1c4fcf)

- **作者**: Cr
- **时间**: 2026-11-19T05:04:59Z
- **提交信息**: [Bugfix][Frontend] Preserve DP rank in beam search and speech-to-text requests (#67001)

Signed-off-by: Cr <60964294+Chr0mium24@users.noreply.github.com>

### [669d4b0](https://github.com/vllm-project/vllm/commit/669d4b0ad31ccc7d59e25115999791bcd59adec2)

- **作者**: Flora Feng
- **时间**: 2026-11-19T05:01:08Z
- **提交信息**: [Bugfix] Keep Marlin out of MXFP4 linear selection under VLLM_BATCH_INVARIANT (#68008)

Signed-off-by: Flora Feng <4florafeng@gmail.com>

### [9438027](https://github.com/vllm-project/vllm/commit/9438027e3b35bb6bde9126a842a2a5776b0e60e1)

- **作者**: 최재영
- **时间**: 2026-11-19T04:43:16Z
- **提交信息**: [Bugfix][Multimodal] Size image placeholders from request-level processor kwargs in DeepSeek-OCR/VL2, LightOnOCR and Molmo2 (#68127)

Signed-off-by: 최재영 <144660874+Jaeyeong-CHOI@users.noreply.github.com>
Co-authored-by: OpenAI Codex (GPT-6 Astra) <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3eeb381](https://github.com/vllm-project/vllm/commit/3eeb3815e4cbd0d89dbee9b60acd440b7c6b9dbc)

- **作者**: aoshen02
- **时间**: 2026-11-19T04:38:19Z
- **提交信息**: [Model Loader] Load plan: plan copy-time casts and setitem writes as direct; faster overlap check (#67836)

Signed-off-by: aoshen02 <aoshen02@users.noreply.github.com>
Signed-off-by: aoshen524 <aoshen524@gmail.com>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: aoshen02 <aoshen02@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen524 <aoshen524@gmail.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4f4ead1](https://github.com/vllm-project/vllm/commit/4f4ead13ab205d8d01ac9ada022c905a7d7ed807)

- **作者**: Xu Jixian
- **时间**: 2026-11-19T04:33:49Z
- **提交信息**: [Bugfix] Apply max_tokens caps to explicit null on generate (#66233)

Signed-off-by: xu797 <xjxian02@gmail.com>

### [bfa9f67](https://github.com/vllm-project/vllm/commit/bfa9f671c89fe1c0274795bbb3c67c028cf18c46)

- **作者**: Isotr0py
- **时间**: 2026-11-19T04:32:54Z
- **提交信息**: [Fast Start] Remove copy mode for fast start IPC loader (#68388)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7a59edd](https://github.com/vllm-project/vllm/commit/7a59edd859a5d8f3bc92a19347c632a03f07e642)

- **作者**: Xun Sun
- **时间**: 2026-11-19T04:12:45Z
- **提交信息**: [Fast Start] Support compressed-tensors WNA16 pre-processed weights (#68328)

Signed-off-by: Xun Sun <UNIDY2002@outlook.com>
Co-authored-by: Codex <noreply@openai.com>

### [0aecc81](https://github.com/vllm-project/vllm/commit/0aecc818a9bf584d2249910962bae26bf8033483)

- **作者**: Jared Wen
- **时间**: 2026-11-19T04:08:46Z
- **提交信息**: [Perf][Step5] Keep PrimTS SWA verify batches on the decode plan (#68129)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5201ec0](https://github.com/vllm-project/vllm/commit/5201ec057449b927eed95411cd64ef93ac27032d)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-19T04:07:11Z
- **提交信息**: [Model] Inkling 2: Hopper (SM90) support (#67880)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cefcae8](https://github.com/vllm-project/vllm/commit/cefcae8bd09ef9b2e2940f3e0b326bc73e4a07f2)

- **作者**: Yongye Zhu
- **时间**: 2026-11-19T04:06:47Z
- **提交信息**: [Bugfix][NIXL] Push: stop WRITE submission stalls and early block release; lock the NIXL agent (#66795)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [601066c](https://github.com/vllm-project/vllm/commit/601066c91ca20f07975c344af5b4e63bf7e4b026)

- **作者**: YiSheng5
- **时间**: 2026-11-19T03:27:27Z
- **提交信息**: [XPU][Test] Enable Ray-based test_comm_ops tests on XPU (#66975)

Signed-off-by: yisustc <yisustc@users.noreply.github.com>
Co-authored-by: yisustc <yisustc@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5b37b1c](https://github.com/vllm-project/vllm/commit/5b37b1c42e87857ca889e97d1d972e1bffea4727)

- **作者**: Qiming Zhang
- **时间**: 2026-11-19T03:26:47Z
- **提交信息**: [XPU] SamplingMaskTensors use sycl kernel on XPU (#64231)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [545ef08](https://github.com/vllm-project/vllm/commit/545ef081895681ba4c2aa3c6699326e3a2f3cbf7)

- **作者**: Juntian Liu
- **时间**: 2026-11-19T03:14:52Z
- **提交信息**: [Recipe] DeepSeek-V4.1-Flash: GB300 Dynamo AgentX presets from InferenceX #5015 (#68556)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3e469e9](https://github.com/vllm-project/vllm/commit/3e469e9ffbef4c54595327df14d209ba9c2481f7)

- **作者**: XiaobingZhang
- **时间**: 2026-11-19T03:13:04Z
- **提交信息**: [ROCm] wvSplitK: keep bf16 N=5 at YTILE 2 on wave64 to avoid VGPR spills (#66444)

Signed-off-by: XiaobingZhang <xiaobingzhangupc@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [78c938b](https://github.com/vllm-project/vllm/commit/78c938b840931df2926587566b5d8b6608013a2b)

- **作者**: Matt
- **时间**: 2026-11-19T03:10:27Z
- **提交信息**: [ROCm][Muse Spark] Online MXFP4 target for the BF16 first/last-layer experts (#67191)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [da7acd6](https://github.com/vllm-project/vllm/commit/da7acd6f4284e3b9b1a5a4359e2a0690e6276ec2)

- **作者**: Matt
- **时间**: 2026-11-19T03:09:09Z
- **提交信息**: [Perf][Frontend] Seed the fast detokenizer with a prompt tail, not the full prompt (#67153)

Signed-off-by: Matthew Wong <Matthew.Wong2@amd.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [253ff4e](https://github.com/vllm-project/vllm/commit/253ff4e7ccf59c684b1c7fac33221ffafb55674f)

- **作者**: Lantao Jin
- **时间**: 2026-11-19T03:07:55Z
- **提交信息**: [Model][LoRA] Enable LoRA for GTE (bert_with_rope) embedding and reranker models (#68049)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Co-authored-by: Yuanchun Shen <yuanchu@amazon.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4092096](https://github.com/vllm-project/vllm/commit/4092096fef1fb0b1fcda9e1bc697b72e5eb55522)

- **作者**: Robert Shaw
- **时间**: 2026-11-19T02:41:38Z
- **提交信息**: [Bugfix][KV Cache] Don't size KV cache groups from draft-only sliding-window buckets (#68533)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [428c371](https://github.com/vllm-project/vllm/commit/428c371b32c18a788def35abea1cb9f579278381)

- **作者**: cjackal
- **时间**: 2026-11-19T01:48:58Z
- **提交信息**: [Misc] Use torch 2.14 custom class API for LayerName registration (#64314)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [8700cc9](https://github.com/vllm-project/vllm/commit/8700cc9ba0016bf14d8f2756f3b673e93fbcf2fd)

- **作者**: Akine-Ko
- **时间**: 2026-11-19T01:30:34Z
- **提交信息**: [EC Connector] Add ECTieringConnector filesystem tiering for encoder cache (#63294)

Signed-off-by: Akine-Ko <2923601304@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [34aac94](https://github.com/vllm-project/vllm/commit/34aac94f9c349c76be42e8d1c8849b69ad6303e1)

- **作者**: Yifei Wang
- **时间**: 2026-11-19T01:25:46Z
- **提交信息**: [Bugfix][KV Connector] Fix MultiConnector handshake metadata routing (#67174)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d951bd5](https://github.com/vllm-project/vllm/commit/d951bd5fbe6f1bb73bdd8339ebb414765e85659e)

- **作者**: aaryamonvikram
- **时间**: 2026-11-19T01:25:39Z
- **提交信息**: [Bugfix][Responses] Keep empty reasoning blocks in Responses output (#67189)

Signed-off-by: aaryamonvikram <aaryamonvikram@gmail.com>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [b067b6f](https://github.com/vllm-project/vllm/commit/b067b6f6fa509a8c98c5a79d75b2aa3742d539c6)

- **作者**: Jee Jee Li
- **时间**: 2026-11-19T01:22:17Z
- **提交信息**: [Model] Add HY4 Flash and multimodal support (#68296)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: chengvjiang <chengvjiang@tencent.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Ruinan Ma <97484148+mrn3088@users.noreply.github.com>
Co-authored-by: thisjiang <thisjiang@qq.com>
Co-authored-by: Summer Yang <girasoleyang@gmail.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Giancarlo Delfin <32987265+TheEpicDolphin@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [0e98bba](https://github.com/vllm-project/vllm/commit/0e98bbaf8afc455216e57d0c2fc4c1ce31f29440)

- **作者**: Luyi Xiao
- **时间**: 2026-11-19T01:17:40Z
- **提交信息**: [Bugfix][Spec Decode] Bound multi-module MTP re-prefill to valid request history (#66951)

Signed-off-by: Luyi Xiao <81631911+luyixiao95@users.noreply.github.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [79897d9](https://github.com/vllm-project/vllm/commit/79897d9f47cfe9727749a79253c5b220e71acb39)

- **作者**: Thang Nguyen
- **时间**: 2026-11-19T01:03:12Z
- **提交信息**: [CI] Enroll 8 CPU steps in automatic sharding (#67534)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [37235a2](https://github.com/vllm-project/vllm/commit/37235a2bac9a035640d03f112742868198ba7231)

- **作者**: Thang Nguyen
- **时间**: 2026-11-19T01:02:49Z
- **提交信息**: [CI] Enroll Entrypoints Integration (API Server) and Rust Frontend Serve/Admin in automatic sharding (#64128)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e9671c8](https://github.com/vllm-project/vllm/commit/e9671c8ea788e43c4182e0c63448c705d38e6227)

- **作者**: Thang Nguyen
- **时间**: 2026-11-19T01:02:34Z
- **提交信息**: [CI] Upload command spans first and give big job-end flushes more time (#68208)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c408dfc](https://github.com/vllm-project/vllm/commit/c408dfc678e306b87e8260fa527b6c44d21a41fa)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-19T01:00:27Z
- **提交信息**: [CI] Move H100 fault tolerance E2E to nightly (#68494)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [34f1fc8](https://github.com/vllm-project/vllm/commit/34f1fc8497a906dabc74be125b8e423f8cbdd915)

- **作者**: potoior
- **时间**: 2026-11-19T00:52:19Z
- **提交信息**: [Bugfix][Core] Drop streaming updates that would overflow max_model_len (#63113)

Signed-off-by: potoior <2986486901@qq.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: opencode <noreply@opencode.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [84aacd2](https://github.com/vllm-project/vllm/commit/84aacd24826de28dc5131c2068ad56e3fbb90f42)

- **作者**: cjackal
- **时间**: 2026-11-19T00:50:48Z
- **提交信息**: [Multimodal] Allow disabling embed inputs per modality in `--limit-mm-per-prompt` (#67995)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [cee2b09](https://github.com/vllm-project/vllm/commit/cee2b09cb9f341b776a14a2da9e86af2276e9de6)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-19T00:37:57Z
- **提交信息**: [Perf][Ray] Kill RayExecutorV2 actors before joining the monitor thread (#68526)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [62e9eab](https://github.com/vllm-project/vllm/commit/62e9eab589945a1a188efe80afca845c731b60a0)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-19T00:37:21Z
- **提交信息**: [Bugfix] Peek at the EngineCore exit status instead of reaping it in the liveness monitor (#68288)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8749fc0](https://github.com/vllm-project/vllm/commit/8749fc0a383a036555ff1a6d5c933a1197fa17a9)

- **作者**: maobaolong
- **时间**: 2026-11-19T00:35:35Z
- **提交信息**: [Feature][KV Connector] Notify connectors after startup KV cache preparation (#66574)

Signed-off-by: baoloongmao <307499405@qq.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [e1dceab](https://github.com/vllm-project/vllm/commit/e1dceabda959711952b8cc5f3da87bc7b8b5eeb7)

- **作者**: Cheng Rui
- **时间**: 2026-11-19T00:30:14Z
- **提交信息**: [Perf][Qwen4Exp] Fuse HyperConnection up projection and gate mix on SM90 (#66791)

Signed-off-by: <chengrui4@lenovo.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6dd7ce8](https://github.com/vllm-project/vllm/commit/6dd7ce86b6131dd1708bc738e906986ef149b0fe)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-19T00:29:11Z
- **提交信息**: [Multimodal] Pass placement with Omni embeddings to drop the audio-in-video host read (#68200)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b209d98](https://github.com/vllm-project/vllm/commit/b209d984d88121208526c09ec3b9e980850efe9d)

- **作者**: Chinmay Shrivastava
- **时间**: 2026-11-19T00:26:45Z
- **提交信息**: [Bugfix][Kernel] Apply beta after the K loop in chunk_scaled_dot_kkt (#67812)

Signed-off-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: JonSnow1807 <JonSnow1807@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-20
**监控日期**: 2026-11-19
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7856
- **最后更新**: 2026-11-20T03:08:54Z

## 提交统计

- **昨日提交总数**: 67
- **提交者数量**: 51
- **主要提交者**: Zhang Ziyu, wangyu, suntp

## AI分析总结

# vllm-omni 昨日提交总结（共 67 条）

## 一、主要更新类型

昨日提交以 **Bug 修复**（约 48 条）为主，集中在双工语音会话、TTS 模型正确性、图像/扩散模型批处理边界与多模态输入解码。其次是 **CI/构建**（约 16 条）、**性能优化**（约 5 条）、**功能新增**（约 6 条）及少量文档更新。整体属于稳定性打磨与工程加固批次，无大型重构。

## 二、关键变更点

**双工语音链路**是核心主线：编排器独立进程运行（#9588）、恢复时机段推进（#10755）、barge-in 播放清理（#10714）、空闲租约刷新（#10617）、静音延续死线抖动（#9537）等修复共同支撑低延迟、高交互性的全双工体验。

**多模态正确性**：修复 AAC/WebM/MP4 语音上传解码并规范化 MIME 类型（#10673）；SAGE_ATTN 尾部填充前缀切片（#10729）、Fish attention 跨步 KV 回退（#5943）等注意力核布局修复；文件 rendezvous 替代 TCP 端口（#10689）根除扩散测试端口竞争；fork 后重建 PNG 编码池（#10682）解决多进程资源生命周期问题；全负载跨抢占/中止状态一致性修复（#10692）。

**TTS 可靠性**：Breeze-TTS-2 在 Transformers 5.x 上的兼容修复（#10651）、CosyVoice3/Voxtral 超预算截断时向用户显式报告（#10654）、种子化请求位级可复现（#9937），避免静默失败并保障生产可审计性。

**多硬件投入**：XPU、ROCm、NPU、MUSA、Ascend 专项修复，XPU 每 PR 测试从 154 扩至 9.2k，多项 NIGHTLY 升级为阻塞式门禁，NPU 升级至 v0.34.0。

**功能与性能**：DP+HSDP 支持、输入时钟双工会话、Drama 3 参考采样；Qwen3-TTS 融合算子、Qwen-Image 调制与 RoPE 融合、SM89 VAE 融合算子。

**文档与体验**：H100 Attention 后端推荐、单张 RTX 4090 的 H3-Image 配方（#8657、#10255）降低个人开发者门槛；token 预算截断的前端可见性提示；黄金基准重新生成与 rope shim 测试兼容化。

## 三、项目影响与意义

- **用户侧**：语音上传成功率提升、TTS 超预算不再无声截断、模型加载不再因依赖版本漂移崩溃、硬件配方文档降低部署门槛。
- **开发侧**：阻塞式 CI 与基准重生成显著降低回归风险和假阳性噪音，多硬件碎片化得到系统性防护。
- **方向信号**：项目正从功能铺设转向生产级稳定性加固，以双工语音与多模态推理正确性为核心，同步扩展多硬件覆盖与可复现性，为后续模型接入建立可靠基础。

## 四、值得关注的技术点

1. **注意力核 padding/packed 布局正确性**：SAGE_ATTN 与 Fish attention 的修复模式可复用至其他注意力后端。
2. **依赖版本敏感性**：Transformers 5.x 持续引入破坏性变更，建议建立兼容矩阵或版本上限策略。
3. **MIME 规范化**：音视频容器类型统一判定，可扩展至图像/视频上传路径。
4. **token 预算可见性**：前端与调度器的信息传递是后续配额管理、计费统计的伏笔。
5. **部分提交出现 Claude、Cursor 等 AI 工具联署**，反映开发流程正在变化。

## 五、整体评价

昨日 67 个提交表明 vllm-omni 已进入成熟期的打磨阶段：以双工语音和多模态输入的生产可用性为重心，辅以多硬件 CI 扩容、性能融合优化和硬件落地文档，持续兑现 README 中 "easy, fast, cheap omni-modality serving for everyone" 的承诺，为吸引更多模型接入与生产级用户铺平道路。

## 详细提交记录

### [87b22ab](https://github.com/vllm-project/vllm-omni/commit/87b22ab124c0c12f9ec5cd6be02a74344d44fda8)

- **作者**: Alessio Netti
- **时间**: 2026-11-19T23:30:41Z
- **提交信息**: [Perf] Allow running full duplex orchestrator in a dedicated process (#9588)

Signed-off-by: Alessio Netti <26897207+AlessioNetti@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [d6c4b88](https://github.com/vllm-project/vllm-omni/commit/d6c4b8814b50bc7b9f90d240c447c72b6ac98f5b)

- **作者**: He Yingxu
- **时间**: 2026-11-19T22:52:45Z
- **提交信息**: [Bugfix] Apply REST speech parameters on the speech WebSocket (#10739)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cb718fd](https://github.com/vllm-project/vllm-omni/commit/cb718fd704310940a5939afd2c92e59dd3c89fff)

- **作者**: dengyunyang
- **时间**: 2026-11-19T20:14:43Z
- **提交信息**: [CI/Build] Preserve OmniServer stderr after readiness (#10727)

Signed-off-by: dengyunyang <584797741@qq.com>

### [9f40564](https://github.com/vllm-project/vllm-omni/commit/9f40564828b8665828e9f1cf1c7e902bea58bdb8)

- **作者**: y-null
- **时间**: 2026-11-19T20:13:46Z
- **提交信息**: [Bugfix] Preserve MiniCPM-o duplex turn decisions and replay bounds (#10743)

Signed-off-by: y_null <y_null@qq.com>

### [97273e8](https://github.com/vllm-project/vllm-omni/commit/97273e85f4670e12c92c1c61c0f05416a031e70d)

- **作者**: Weiming Liao
- **时间**: 2026-11-19T19:46:42Z
- **提交信息**: [NPU] upgrade to v0.34.0 (#10691)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Signed-off-by: chenqi49 <479148871@qq.com>
Co-authored-by: chenqi49 <479148871@qq.com>

### [52c4467](https://github.com/vllm-project/vllm-omni/commit/52c446704d5002a6d055bc460f67f7f73d7c37fe)

- **作者**: tastysoup-s
- **时间**: 2026-11-19T19:30:06Z
- **提交信息**: [Bugfix] Advance the segment generation when a duplex receiver resumes (#10755)

Signed-off-by: tastysoup-s <175210099+tastysoup-s@users.noreply.github.com>
Co-authored-by: tastysoup-s <175210099+tastysoup-s@users.noreply.github.com>

### [69e3d1a](https://github.com/vllm-project/vllm-omni/commit/69e3d1a53beb94c2f080bb5047de7a965bf83e57)

- **作者**: Ricardo Noriega
- **时间**: 2026-11-19T18:59:05Z
- **提交信息**: [Bugfix] Add jitter margin to silence-continuation deadline to prevent step-rate doubling (#9537)

Signed-off-by: Ricardo Noriega De Soto <rnoriega@redhat.com>
Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: natureofnature <wzliu@connect.hku.hk>

### [341e519](https://github.com/vllm-project/vllm-omni/commit/341e519a2f8142f2188dbf17e79d0bbdba477214)

- **作者**: Hikari
- **时间**: 2026-11-19T18:37:03Z
- **提交信息**: [Perf][JoyAI] Enable fused Qwen3-TTS code predictor and Code2Wav convolution options in the duplex profile (#10671)

Signed-off-by: altale <extsuioku@gmail.com>

### [862d351](https://github.com/vllm-project/vllm-omni/commit/862d35130c4c732492b9e26977edfd3846f94974)

- **作者**: hac17
- **时间**: 2026-11-19T17:44:26Z
- **提交信息**: [Bugfix][ROCm] Enable diffusion INT8 through upstream linear kernels (#10708)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [7a82705](https://github.com/vllm-project/vllm-omni/commit/7a827054152275de4fa43653f45155138945bbd8)

- **作者**: tastysoup-s
- **时间**: 2026-11-19T17:14:11Z
- **提交信息**: [Bugfix] Refresh duplex idle lease for buffered speech (#10617)

Signed-off-by: tastysoup-s <175210099+tastysoup-s@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: tastysoup-s <175210099+tastysoup-s@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [12b63df](https://github.com/vllm-project/vllm-omni/commit/12b63df68b55698be22d8b27bbe0da4def802bb0)

- **作者**: Chendi.Xue
- **时间**: 2026-11-19T17:00:04Z
- **提交信息**: [CI/Build][XPU] XPU CI on one and two cards: 154 -> 9.2k tests per PR (#10341)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [0a4adb8](https://github.com/vllm-project/vllm-omni/commit/0a4adb888050fc6bd1e5cf235b33e0eeb8a86860)

- **作者**: Zeng Chuang
- **时间**: 2026-11-19T16:47:57Z
- **提交信息**: [Bugfix] Reduce silent collapses in Drama 3 speech generation (#10669)

Signed-off-by: zengchuang <zengchuang3@huawei.com>

### [56af9e0](https://github.com/vllm-project/vllm-omni/commit/56af9e0595a88cd3c5e5b717f1adccf89faba75a)

- **作者**: Sheng GAO
- **时间**: 2026-11-19T16:33:28Z
- **提交信息**: [Bugfix][NPU] Forward the profiler stack flag (#10629)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Jose Alexis Roman Martinez <alexisromtz-lab@users.noreply.github.com>

### [65502aa](https://github.com/vllm-project/vllm-omni/commit/65502aa313eabbbedfd197e8d3cacde6ffc7f177)

- **作者**: Qingyi Ji
- **时间**: 2026-11-19T16:32:07Z
- **提交信息**: [Bugfix] Adjust CosyVoice3 CUDA duration threshold  (#9656)

Signed-off-by: JQY <jqy021018@gmail.com>
Co-authored-by: Weiming Liao <liaowm5@gmail.com>

### [e74e948](https://github.com/vllm-project/vllm-omni/commit/e74e948589d68f6b330febdadeb3fc15b661cf97)

- **作者**: hac17
- **时间**: 2026-11-19T16:26:21Z
- **提交信息**: [CI/Build][ROCm] Add blocking NIGHTLY Wan2.2 device-postprocess equivalence (#10685)

Signed-off-by: Zhang <haichzha@amd.com>
Co-authored-by: Zhang <haichzha@amd.com>

### [1013b66](https://github.com/vllm-project/vllm-omni/commit/1013b6688e7433d12a0ec874df849e58ef806ac3)

- **作者**: Shivnarayan S
- **时间**: 2026-11-19T16:24:47Z
- **提交信息**: [CI/Build] Widen the video server test wait budget (#10687)

Signed-off-by: Shivnarayan <shivnarayan4077@gmail.com>

### [f661183](https://github.com/vllm-project/vllm-omni/commit/f6611837e694f4362642ff5ce0eaa7207ae6fb03)

- **作者**: Ding Zuhao
- **时间**: 2026-11-19T15:41:03Z
- **提交信息**: [Bugfix][BAGEL] Condition single-stage image inputs like the reference inferencer: SigLIP path, ViT-only understanding, image preprocessing (#8321)

Signed-off-by: Ding Zuhao <e1583181@u.nus.edu>
Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: natureofnature <wzliu@connect.hku.hk>

### [56885e5](https://github.com/vllm-project/vllm-omni/commit/56885e58fc0d4205cfff919a1807f0ba3b96b90d)

- **作者**: hac17
- **时间**: 2026-11-19T15:25:32Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY BAGEL sleep mode to blocking (#10684)

Signed-off-by: Zhang <haichzha@amd.com>
Co-authored-by: Zhang <haichzha@amd.com>

### [881a244](https://github.com/vllm-project/vllm-omni/commit/881a2447bde1aff2a2d0e326905e563d0fba04ec)

- **作者**: alex7092
- **时间**: 2026-11-19T15:06:52Z
- **提交信息**: [CI/Build] Use file rendezvous in the remaining CPU diffusion tests to avoid TCP port races (#10689)

Signed-off-by: 刘星 <15105576+alex7092@users.noreply.github.com>

### [aa44316](https://github.com/vllm-project/vllm-omni/commit/aa44316c7d6887e21709153c4987c90e33381182)

- **作者**: Sam Tibo
- **时间**: 2026-11-19T15:05:05Z
- **提交信息**: [Kernel] Fix Fish attention fallback on strided KV cache (#5943)

Signed-off-by: pxljs <1621352782@qq.com>

### [edbdd95](https://github.com/vllm-project/vllm-omni/commit/edbdd95b34ab349967feaf533b09fc6bf1771795)

- **作者**: Ryn Wang
- **时间**: 2026-11-19T15:01:14Z
- **提交信息**: [Feature] Isolate seeded TTS requests so they stay bit-reproducible (#9937)

Signed-off-by: Ryn Wang <Ryn.Wang@outlook.com>

### [d189bad](https://github.com/vllm-project/vllm-omni/commit/d189bad1ecda2c0899dac77d30354cd3283a4976)

- **作者**: 菠萝吹雪
- **时间**: 2026-11-19T14:27:18Z
- **提交信息**: [Bugfix] Fix loopback replica host in NIXL sender info (#9651)

Signed-off-by: Xiaotangyuan-xty <193046655+Xiaotangyuan-xty@users.noreply.github.com>

### [bb58e45](https://github.com/vllm-project/vllm-omni/commit/bb58e450352a5474f584b20b569c982a2adc57f4)

- **作者**: suntp
- **时间**: 2026-11-19T14:13:00Z
- **提交信息**: [Doc] Read merged audio from choices[0] in Qwen3-Omni examples (#10746)

Signed-off-by: suntp <20786998+suntp@users.noreply.github.com>
Co-authored-by: suntp <20786998+suntp@users.noreply.github.com>

### [bfc4eed](https://github.com/vllm-project/vllm-omni/commit/bfc4eed9c2a1f4ddbcdefe2fb5ea1cee949dfcbc)

- **作者**: amy-why-3459
- **时间**: 2026-11-19T13:57:38Z
- **提交信息**: [Bugfix] Restore MRv2 transport across audio pipelines (#10721)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [f8e6501](https://github.com/vllm-project/vllm-omni/commit/f8e650153f51d766da00adb077fa92890c8cccf6)

- **作者**: Ziyuan_Li
- **时间**: 2026-11-19T13:53:03Z
- **提交信息**: [Hardware][NVIDIA][MiniMax-H3] Enable VAE decoder fused ops on SM89 (#10516)

Signed-off-by: Ziyuan Li <zyuanli204@gmail.com>

### [4fb3703](https://github.com/vllm-project/vllm-omni/commit/4fb3703f35808e3de31496c834ee503c19a983c0)

- **作者**: Dong1017
- **时间**: 2026-11-19T13:37:46Z
- **提交信息**: [CI][bugfix] Use latest MiniMax-H3 revision in quantization quality test (#10715)

Signed-off-by: Dong1017 <Dong1017@users.noreply.github.com>
Co-authored-by: Dong1017 <Dong1017@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [a005a48](https://github.com/vllm-project/vllm-omni/commit/a005a48cdf667351b41757e7b9100df5226a49d0)

- **作者**: Lingwei1943
- **时间**: 2026-11-19T13:19:45Z
- **提交信息**: [Bugfix][VoxCPM2] stabilize edge digit pronunciation: prosodic lead-in, sentence-final stop, lone-zero lookbehind (#9697)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [900e80c](https://github.com/vllm-project/vllm-omni/commit/900e80ca3d9312ee304bc4c33d0d67c83bbbbc8c)

- **作者**: 汪志鹏
- **时间**: 2026-11-19T13:16:05Z
- **提交信息**: [Bugfix] Let SAGE_ATTN slice the valid K/V prefix for packed tail padding (#10729)

Signed-off-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [394a617](https://github.com/vllm-project/vllm-omni/commit/394a617ffe7def7912cd9b8290bcca293170b53f)

- **作者**: Hoseung Kim
- **时间**: 2026-11-19T13:08:35Z
- **提交信息**: [Bugfix] Return 400 for vLLM client errors in /v1/audio/speech (#8277)

Signed-off-by: Hoseung Kim <hoseung.kim@navercorp.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [6024662](https://github.com/vllm-project/vllm-omni/commit/6024662a814c03e4381d8546b2c44c470f6afbe4)

- **作者**: Wang, Chang
- **时间**: 2026-11-19T12:33:44Z
- **提交信息**: [Bugfix] Load re-saved Z-Image text encoder weights (#9640)

Signed-off-by: changwangss <chang1.wang@intel.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [6fb2989](https://github.com/vllm-project/vllm-omni/commit/6fb2989022887187f4162896bee23e49a0836b18)

- **作者**: R0CKSTAR
- **时间**: 2026-11-19T12:27:52Z
- **提交信息**: [Perf][MUSA] Qwen-Image-2.1: shared and broadcast modulation, RoPE and fused QK norm+RoPE in compiled regions, VAE norm epilogue (#9845)

Signed-off-by: Xiaodong Ye <xiaodong.ye@mthreads.com>

### [4c5e61e](https://github.com/vllm-project/vllm-omni/commit/4c5e61ef5eeff5fd283167de6414ea7c1235c19c)

- **作者**: psv666
- **时间**: 2026-11-19T12:27:43Z
- **提交信息**: [Hardware][Ascend] Skip Qwen3-Omni Talker payloads for text-only batches (#10631)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4b34747](https://github.com/vllm-project/vllm-omni/commit/4b347471dbce9740fa133d2fa5780a6feea82819)

- **作者**: MaciejBalaNV
- **时间**: 2026-11-19T12:18:42Z
- **提交信息**: [feature] Enable DP with HSDP (#8514)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: MaciejBalaNV <mbala@nvidia.com>

### [2858ea3](https://github.com/vllm-project/vllm-omni/commit/2858ea3d2cd635c3450700e4001d0b21a97fcbb8)

- **作者**: Sheng GAO
- **时间**: 2026-11-19T12:18:24Z
- **提交信息**: [Bugfix][FLUX.2] Reject output sizes that produce empty latent grids (#10737)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: starsstreaming <2946843254lw@gmail.com>

### [6dece8b](https://github.com/vllm-project/vllm-omni/commit/6dece8b10ee0d8844f0308deee2a195a6dcbf0f7)

- **作者**: boatman
- **时间**: 2026-11-19T11:50:07Z
- **提交信息**: [Bugfix] Preserve MRv2 FULL graph candidates for Tensor outputs (#10636)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [935a130](https://github.com/vllm-project/vllm-omni/commit/935a13098bc1728ff3fe9a216ef3b28d3d79f0db)

- **作者**: Wang  fuyin
- **时间**: 2026-11-19T11:49:13Z
- **提交信息**: [CI/Build] Skip unavailable SANA-Video golden cases (#10690)

Signed-off-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: Acerak01-fy <187926210+Acerak01-fy@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [b4aba05](https://github.com/vllm-project/vllm-omni/commit/b4aba05b0b3e41be5447e317429b7965df6eccb3)

- **作者**: Ziyuan_Li
- **时间**: 2026-11-19T11:49:06Z
- **提交信息**: [Doc] Add PersonaPlex RTX 5080 Laptop 16GB recipe (#10362)

Signed-off-by: Ziyuan Li <zyuanli204@gmail.com>

### [261b555](https://github.com/vllm-project/vllm-omni/commit/261b555f7324a63d8b667964642a787bf1822c01)

- **作者**: Nick Cao
- **时间**: 2026-11-19T11:47:15Z
- **提交信息**: [CI/Build] Add pipeline-parallel group to tiny-model diffusion tests (#10472)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [2c62b6b](https://github.com/vllm-project/vllm-omni/commit/2c62b6b999f5f8f0418071719d5f2d6ba371b4c3)

- **作者**: y-null
- **时间**: 2026-11-19T11:30:42Z
- **提交信息**: [Bugfix] Clear completed duplex playback on barge-in (#10714)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e267ac1](https://github.com/vllm-project/vllm-omni/commit/e267ac188f704601e4b300f22152ce212558482a)

- **作者**: Chiquan Mo
- **时间**: 2026-11-19T11:14:57Z
- **提交信息**: [Bugfix] Warn on unsupported --stage-overrides fields (#9650)

Signed-off-by: MciG-ggg <mcigggg399026@gmail.com>
Signed-off-by: Gao Han <hgaoaf@connect.ust.hk>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [fb41f81](https://github.com/vllm-project/vllm-omni/commit/fb41f81b96ab3c4f6bc7e888ed8e47b07583795b)

- **作者**: psv666
- **时间**: 2026-11-19T11:13:16Z
- **提交信息**: [Bugfix] Fail serving benchmarks early on VAD and warmup errors (#10626)

Signed-off-by: psv666 <2693925048@qq.com>

### [8326b13](https://github.com/vllm-project/vllm-omni/commit/8326b133d0e688b8c272053321f4cb0eb3f7bb5c)

- **作者**: zzh
- **时间**: 2026-11-19T11:12:11Z
- **提交信息**: [Bugfix] Fix full-payload accumulation across preemption and aborts (#10692)

Signed-off-by: bezdarnost <amanurumbekov@gmail.com>
Signed-off-by: Zhiheng Zhang <67720593+BLANKETusers@users.noreply.github.com>
Signed-off-by: zzh <943967662@qq.com>
Co-authored-by: bezdarnost <amanurumbekov@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [e13bd17](https://github.com/vllm-project/vllm-omni/commit/e13bd170e801a678294d9fc248c007ca22d194c4)

- **作者**: easonyu
- **时间**: 2026-11-19T11:09:34Z
- **提交信息**: [Bugfix][Qwen-Image-2.1] Use per-request image RoPE in mixed-length Qwen-Image-2.1 batches (#10376)

Signed-off-by: m0_51593568 <vyu112@foxmail.com>

### [4895274](https://github.com/vllm-project/vllm-omni/commit/4895274923a77e8539261049a7645e5907464eb8)

- **作者**: Dong1017
- **时间**: 2026-11-19T11:04:27Z
- **提交信息**: [Bugfix][NPU] Fall back to pageable memory when pinned host allocation fails (#9957)

Signed-off-by: Dong1017 <xwdong1998@163.com>
Signed-off-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: Claude Code <noreply@anthropic.com>
Co-authored-by: wujingjing-hw <340480870+JingjingWu6@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [15fdf86](https://github.com/vllm-project/vllm-omni/commit/15fdf86307fbf82159c9df386745881590bb9b47)

- **作者**: lm10-arg
- **时间**: 2026-11-19T10:45:45Z
- **提交信息**: [Bugfix][ROCm] Repair vLLM 0.34 AMD CI regressions (#10683)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [51f54de](https://github.com/vllm-project/vllm-omni/commit/51f54de16b08416182926b8f071034422561f99c)

- **作者**: psv666
- **时间**: 2026-11-19T09:57:35Z
- **提交信息**: [CI/Build] Allow Qwen3-Omni LoRA test more startup time (#10700)

Signed-off-by: psv666 <2693925048@qq.com>

### [4cbec05](https://github.com/vllm-project/vllm-omni/commit/4cbec0521724ee50e4f34be9dc1b17b011d52106)

- **作者**: Zhang Ziyu
- **时间**: 2026-11-19T09:16:52Z
- **提交信息**: [Bugfix][Ascend] Avoid circular import during A5 platform initialization (#10707)

Signed-off-by: z00899456 <zhangziyu24@huawei.com>
Co-authored-by: z00899456 <zhangziyu24@huawei.com>

### [c64a0ff](https://github.com/vllm-project/vllm-omni/commit/c64a0ff7402f776f772be55344db025f2310fcb9)

- **作者**: hac17
- **时间**: 2026-11-19T08:50:11Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY Qwen-Image 2.1 T2I accuracy to blocking (#10680)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [55e7868](https://github.com/vllm-project/vllm-omni/commit/55e786893ae3f373bdcd0568691f50ea334e3b0a)

- **作者**: Zheng Jiayi
- **时间**: 2026-11-19T08:33:01Z
- **提交信息**: [Bugfix][Model] Qwen3-Omni: guard empty talker input projection before torch.cat (#8155)

Signed-off-by: zhengjiayi1206 <zhengjiayi1206@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: zhengjiayi1206 <zhengjiayi1206@users.noreply.github.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [9a2ae28](https://github.com/vllm-project/vllm-omni/commit/9a2ae280e6bc3f92f57d22a2243bd064fe7a2faf)

- **作者**: Pratik Gandhi
- **时间**: 2026-11-19T08:03:54Z
- **提交信息**: [Docs] Fix broken relative links in example and recipe READMEs (#8526)

Signed-off-by: Pratik Gandhi <travpreneur@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [7971aaf](https://github.com/vllm-project/vllm-omni/commit/7971aaff1a19888c182314442d34f6282457ebb4)

- **作者**: Linze Shi
- **时间**: 2026-11-19T07:23:31Z
- **提交信息**: [Bugfix] Recreate the PNG encode pool in forked processes (#10682)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [512fd99](https://github.com/vllm-project/vllm-omni/commit/512fd99d13fd22f019ab1b85e819cb3d795b0f80)

- **作者**: Stefan Wang
- **时间**: 2026-11-19T06:47:11Z
- **提交信息**: [Bugfix] Report TTS synthesis errors in batch and streaming (#9671) (#9693)

Signed-off-by: 1fanwang <1fannnw@gmail.com>
Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [51c99e8](https://github.com/vllm-project/vllm-omni/commit/51c99e80b7ad84a4cb48e63556e013a94dc85f8a)

- **作者**: Laceprndpm
- **时间**: 2026-11-19T06:35:45Z
- **提交信息**: [Bugfix] Preserve per-request HunyuanImage3 VAE RNG across batching and cache hits (#9382)

Signed-off-by: Laceprndpm <Laceprndpm.64@outlook.com>
Signed-off-by: Laceprndpm <laceprndpm.64@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [0ccac41](https://github.com/vllm-project/vllm-omni/commit/0ccac41aaa6ae844c72b4090b816e282248579d4)

- **作者**: wangyu
- **时间**: 2026-11-19T06:35:37Z
- **提交信息**: [CI/Build] Strengthen Qwen3-Omni runtime OOM fault workload (#10698)

Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: wangyu <410167048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b11d315](https://github.com/vllm-project/vllm-omni/commit/b11d3152d9d2f4b00b4a9baec5e071a424fc176b)

- **作者**: sdli1995
- **时间**: 2026-11-19T06:27:42Z
- **提交信息**: [Model] Drama 3: add reference sampling with a per-request epsilon_cutoff behind a switch (#9503)

Signed-off-by: stone.li <mmlmonkey@163.com>
Signed-off-by: SunskyXH <sunskyxh@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: SunskyXH <sunskyxh@gmail.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [f33467c](https://github.com/vllm-project/vllm-omni/commit/f33467c800c7efa85b49b0842814325b958b0fb7)

- **作者**: hac17
- **时间**: 2026-11-19T06:12:47Z
- **提交信息**: [CI/Build][ROCm] Promote nine stable NIGHTLY 4-GPU diffusion cases to blocking (#10679)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [cf457a6](https://github.com/vllm-project/vllm-omni/commit/cf457a688ff406d70ff9e6d0257428958fae5b52)

- **作者**: 梧桐雨
- **时间**: 2026-11-19T06:00:10Z
- **提交信息**: [Bugfix] Clean request artifacts on pre-registration rejection (#7100)

Signed-off-by: wutongyuonce <147830929+wutongyuonce@users.noreply.github.com>
Co-authored-by: GUOGUO <xwdong1998@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [5363d0b](https://github.com/vllm-project/vllm-omni/commit/5363d0b5a3378dffb7f095c6c9e2970bfeef2919)

- **作者**: Yinhong Liu
- **时间**: 2026-11-19T05:56:34Z
- **提交信息**: [Core] Input-clocked duplex sessions (clock: "input") and a per-session silence_continuation option (#8485)

Signed-off-by: williamLyh <williamliuyinhong@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [1a19178](https://github.com/vllm-project/vllm-omni/commit/1a19178e1e234bd32bcfc7f5a3e900139f2db72e)

- **作者**: dengyunyang
- **时间**: 2026-11-19T05:44:44Z
- **提交信息**: [Bugfix] Preserve HunyuanImage3 sampling constraints on MR2 (#10092)

Signed-off-by: dengyunyang <584797741@qq.com>

### [f175351](https://github.com/vllm-project/vllm-omni/commit/f175351ce30b0e4e9a1dca04bfc3a731a746e4c6)

- **作者**: ooooooye
- **时间**: 2026-11-19T04:18:41Z
- **提交信息**: [Bugfix][NPU] Generalize the packed varlen contract to local-Q/global-KV (#8632)

Signed-off-by: brandneway <gyuan4892@gmail.com>

### [f16f02f](https://github.com/vllm-project/vllm-omni/commit/f16f02f4337dd93af159d7ea4db8efe898f71e70)

- **作者**: jeffaa729
- **时间**: 2026-11-19T04:01:36Z
- **提交信息**: [Doc][Ming-Image] Recommend Attention Backend for H100 (#8657)

Signed-off-by: jeffaa729 <hoiwanglo@gmail.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [ace3dc7](https://github.com/vllm-project/vllm-omni/commit/ace3dc777fc13ce3bd8a5fa213467aa2c8770109)

- **作者**: He Yingxu
- **时间**: 2026-11-19T03:56:26Z
- **提交信息**: [Bugfix] Decode AAC/WebM/MP4 voice uploads and normalize MIME types (#10673)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4afeefb](https://github.com/vllm-project/vllm-omni/commit/4afeefb0edaee3613f4cf5d30febef27e7c3a88c)

- **作者**: He Yingxu
- **时间**: 2026-11-19T03:56:12Z
- **提交信息**: [Frontend] Report token-budget truncation for CosyVoice3 and Voxtral TTS (#10654)

Signed-off-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: He Yingxu <28558142+YingxuH@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [62d0e88](https://github.com/vllm-project/vllm-omni/commit/62d0e880a2c7c42903cc384d3b805af4c21a3326)

- **作者**: Dong1017
- **时间**: 2026-11-19T03:38:54Z
- **提交信息**: [Bugfix][test]: accept both staged-write representations in rope shim test (#10633)

Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>

### [09946ce](https://github.com/vllm-project/vllm-omni/commit/09946cec27c9b66f68d5d95586bb712f1e97a20e)

- **作者**: yiminghub2024
- **时间**: 2026-11-19T02:32:47Z
- **提交信息**: [Doc] Enable verified single RTX 4090 H3-Image recipe selection (#10255)

Signed-off-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>
Co-authored-by: yiminghub2024 <202503791+yiminghub2024@users.noreply.github.com>

### [35792be](https://github.com/vllm-project/vllm-omni/commit/35792bea762f8fe80475d37013939d711751d794)

- **作者**: searlion
- **时间**: 2026-11-19T02:11:19Z
- **提交信息**: [Bugfix][Breeze-TTS-2] Load the reference codec on Transformers 5.22 (#10651)

Signed-off-by: Lewis Won <lewis.won@gmail.com>

### [2e3ad0a](https://github.com/vllm-project/vllm-omni/commit/2e3ad0a4ff6e7cd143b3d6e979ba66f6009cb8d5)

- **作者**: lm10-arg
- **时间**: 2026-11-19T00:48:44Z
- **提交信息**: [CI/Build] Re-golden BAGEL shared-memory connector output (#10681)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

---
