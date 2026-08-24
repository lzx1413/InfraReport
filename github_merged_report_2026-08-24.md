# GitHub Stars 合并报告 - 2026-08-24

**合并日期**: 2026-08-25
**监控日期**: 2026-08-24
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


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2170
- **最后更新**: 2026-08-24T12:39:48Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: zangyu, rootkiller6788, qcm1

## AI分析总结

### 主要更新类型
本次提交包含**功能新增**（2项）、**Bug修复**（2项）和**代码重构**（1项），无文档更新或性能优化。

### 关键变更点及与项目方向的关系
1. **移除SeedOmni V1模型栈**（aa0fd73）：这是破坏性变更，直接删除旧版模型代码，符合VeOmni“模型中心化分布式训练配方”的定位，推动项目向更精简、统一的架构演进。
2. **新增Qwen3.5-MoE LoRA训练支持**（d7fb88c）：扩展了模型适配范围，LoRA作为高效微调技术，与项目“任意模态模型训练”目标一致，增强了对主流开源模型的覆盖。
3. **新增MiniMax H3模型支持**（f7fd936）：进一步丰富模型库，H3是新一代混合架构模型，体现项目对前沿模型的快速跟进能力。
4. **修复muon_expert_zero_comm守卫逻辑**（45df8ef）：确保分布式训练中通信优化策略与计划匹配，提升系统稳定性。
5. **修复投影权重与偏置梯度归约**（128f0a1）：解决分布式训练中梯度聚合的维度问题，保证模型收敛正确性。

### 对项目的影响和潜在意义
- **架构精简**：移除旧模型栈降低维护成本，为后续统一接口铺路，但需注意兼容性迁移。
- **生态扩展**：新增两个模型支持，直接提升项目在开源社区的实用性和吸引力，尤其Qwen3.5-MoE的LoRA支持填补了高效微调场景的空白。
- **稳定性提升**：两个分布式修复针对训练核心环节，减少隐性错误风险，对大规模训练场景至关重要。

### 值得关注的技术点
- **LoRA与MoE结合**：Qwen3.5-MoE的LoRA支持涉及稀疏专家模型的参数高效微调，技术实现复杂，值得关注其适配策略。
- **梯度归约修复**：投影层权重与偏置的梯度维度处理是分布式训练常见坑点，修复方案可能对其他模型有借鉴意义。
- **破坏性变更管理**：移除V1栈的提交带有`[BREAKING]`标记，说明项目已进入快速迭代期，需关注版本兼容策略。

### 对项目发展的影响
结合README背景，VeOmni定位为“任意模态模型训练配方库”，本次提交体现了三个发展方向：
1. **聚焦核心能力**：通过移除旧栈，集中资源优化当前架构，符合“配方库”的模块化理念。
2. **紧跟模型前沿**：快速支持Qwen3.5-MoE和MiniMax H3，保持与业界最新模型同步，增强项目竞争力。
3. **夯实分布式基础**：两个修复强化了大规模训练可靠性，这是支撑“任意模态”训练的关键底座。

整体来看，本次提交是项目从“广度覆盖”向“深度优化”过渡的信号，既扩展了模型生态，又巩固了底层稳定性，为后续吸引更多社区贡献和实际应用打下基础。

## 详细提交记录

### [aa0fd73](https://github.com/ByteDance-Seed/VeOmni/commit/aa0fd736958a34fb40880a0b701407192fbcc67e)

- **作者**: Coach257
- **时间**: 2026-08-24T12:37:04Z
- **提交信息**: [BREAKING][omni, model, data] chore: remove the SeedOmni V1 model stack (#1082)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [d7fb88c](https://github.com/ByteDance-Seed/VeOmni/commit/d7fb88cc6663cf515090270fb2946b5be14644a5)

- **作者**: qcm1
- **时间**: 2026-08-24T11:25:24Z
- **提交信息**: [lora,model] feat: Add Qwen3.5-MoE LoRA training support (#1094)

### [45df8ef](https://github.com/ByteDance-Seed/VeOmni/commit/45df8efd687590b110a01e516ccf9ac90483a12f)

- **作者**: Coach257
- **时间**: 2026-08-24T11:24:13Z
- **提交信息**: [dist, ci] fix: make the muon_expert_zero_comm guard check the plan (#1095)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [f7fd936](https://github.com/ByteDance-Seed/VeOmni/commit/f7fd9364d2c5c467633f833bc9546719811aaa9d)

- **作者**: zangyu
- **时间**: 2026-08-24T09:48:27Z
- **提交信息**: [model, config] feat: add MiniMax H3 model support (#1075)

Co-authored-by: vvyuervv <2794113628@qq.com>

### [128f0a1](https://github.com/ByteDance-Seed/VeOmni/commit/128f0a19933389087db4a4ea257fe2c2d6942738)

- **作者**: rootkiller6788
- **时间**: 2026-08-24T09:20:27Z
- **提交信息**: [dist] fix: reduce projection weight & bias grads over batch dim (#1080)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2715
- **最后更新**: 2026-08-24T18:24:11Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 6
- **主要提交者**: qinxinyi, STwangyingrui, Chernobyllight

## AI分析总结

# LightX2V 提交分析总结

## 1. 主要更新类型

本次提交涵盖**性能优化**（占比最高）、**功能新增**、**Bug修复**和**架构重构**四类。核心聚焦于推理加速、资源管理和多模型支持扩展。

## 2. 关键变更点与项目方向

- **缓存复用机制（a34806c）**：为Wan、Qwen-Image、InfiniteTalk引入跨worker和前缀段缓存复用，将编码器输出与请求元数据持久化到共享磁盘缓存。这与LightX2V“轻量高效”的定位高度契合，通过消除重复计算直接降低推理成本。
- **SwiftVR图片超分（65fe600）**：新增原生图像恢复能力，扩展了视频生成框架的输入处理边界，符合多模态融合趋势。
- **HunyuanImage3优化（08c0d48, acb5c79）**：修复离线推理资源释放问题，并针对TP4自回归解码深度优化——引入Triton RMSNorm、紧凑MoE路由、top-k/top-p采样及共享专家流重叠，配合FlashInfer自动调优桶和CUDA Graph捕获。这体现了对特定硬件路径的极致性能挖掘。
- **MiniMax-H3 VAE优化（2516179, 8b6c7b7, d6d21d2）**：并行化编码器、增加分辨率适配的解码tile形状、新增XPU动态W8A8 INT8推理。三者协同提升VAE全链路效率，并拓展硬件适配性。
- **5090(sm120)支持（9f9ceff）**：新增sol_attn适配最新NVIDIA架构，保持对前沿硬件的及时跟进。

## 3. 项目影响与潜在意义

这些变更使LightX2V在**推理效率、硬件适配广度和模型覆盖度**三个维度同步增强。缓存复用机制可能带来数量级的延迟改善，尤其对多轮生成和批处理场景；HunyuanImage3的TP4优化展示了框架对复杂生成模型的深度定制能力；MiniMax-H3的XPU支持则打开了国产硬件生态的入口。整体上，项目正从“通用框架”向“针对特定模型-硬件组合的极致优化平台”演进。

## 4. 值得关注的技术点

- **缓存安全策略**：仅在生成成功后发布缓存，拒绝流式或张量返回请求的复用，兼顾正确性与效率。
- **CUDA Graph资源生命周期管理**：区分单次离线推理与服务器常驻场景，避免资源泄漏同时保持可复用性。
- **TP4解码专用kernel设计**：针对单token解码的访存模式定制RMSNorm和采样算子，而非通用kernel，体现对性能瓶颈的精准定位。
- **VAE tile形状的分辨率感知**：仅对验证过的横屏分辨率启用更大tile，在性能与画质间取得务实平衡。
- **P2P tile路径的跨rank并行**：利用balanced P2P通信优化长参考视频编码，是分布式推理的精细化设计。

## 5. 对项目发展的影响

结合README中“轻量视频生成推理框架”的定位，这些提交表明LightX2V正沿着**“广度扩展+深度优化”**双轨前进：一方面快速适配新模型（SwiftVR、HunyuanImage3、MiniMax-H3）和新硬件（XPU、sm120），另一方面对核心路径（VAE、AR解码、缓存）进行深度性能挖掘。这种策略有助于在竞争激烈的视频生成框架领域建立差异化优势——不仅“能用”，而且针对特定场景“好用”。缓存复用和资源管理优化则直击生产环境的核心痛点，为框架从研究工具走向规模化部署奠定基础。未来若能将TP4和VAE的优化模式推广到更多模型，并完善缓存跨节点一致性，项目有望成为高性能视频推理的事实标准之一。

## 详细提交记录

### [a34806c](https://github.com/ModelTC/LightX2V/commit/a34806c0b35841e12982f33d27c7fbae135fad4e)

- **作者**: Bilang ZHANG
- **时间**: 2026-08-24T17:41:02Z
- **提交信息**: reuse: support cross-worker and prefix-segment reuse (#1428)

- Persist encoder outputs and request metadata in shared disk caches for
Wan,
  Qwen-Image, and InfiniteTalk.
- Add InfiniteTalk prefix-segment reuse with cached motion boundaries
and
  previous-result prefix merging.
- Publish reuse caches only after successful generation and reject reuse
for
  streaming or tensor-returning requests.
- Add reuse capability checks, request schema wiring, cache
configuration, and
  a request example.

### [65fe600](https://github.com/ModelTC/LightX2V/commit/65fe600a6abcb27b0c1427ccd9c0593e301697df)

- **作者**: qinxinyi
- **时间**: 2026-08-24T15:51:59Z
- **提交信息**: feat(swiftvr): support native image restoration (#1427)

给swiftvr支持图片超分

### [08c0d48](https://github.com/ModelTC/LightX2V/commit/08c0d4808ae008d893090ef7ae0ff666393cdbc2)

- **作者**: Chernobyllight
- **时间**: 2026-08-24T12:06:31Z
- **提交信息**: fix(hunyuan-image3): release offline graph resources - #1426 (#1426)

Release HunyuanImage3 CUDA Graph and custom all-reduce resources before
distributed teardown for single-run offline inference. Preserve reusable
runner behavior for servers and multi-iteration benchmarks.

### [acb5c79](https://github.com/ModelTC/LightX2V/commit/acb5c792497f5b86fd3acecc5cb08646cc4d8305)

- **作者**: Chernobyllight
- **时间**: 2026-08-24T10:35:42Z
- **提交信息**: perf(hunyuan-image3): accelerate TP4 AR decode (#1423)

Extend the optimized HunyuanImage 3.0 four-GPU path with decode-specific
kernels and launch tuning.

For single-token TP4 AR decode, add Triton RMSNorm and fused Q/K
RMSNorm, compact MoE routing and top-k/top-p sampling, and shared-expert
stream overlap. Add a q=1 FlashInfer autotuning bucket and cache, and
select the native CUDA allocator required for reliable graph capture.

Both T2I and TI2I configurations retain native-GQA paged FlashAttention
3, full-decode CUDA Graph capture, graph-aware vLLM custom all-reduce,
and TP2+SP2 FlashAttention 3 denoising. The optimizations remain opt-in
through the existing dedicated scripts and configurations, with no
benchmark-only timing instrumentation.

### [9f9ceff](https://github.com/ModelTC/LightX2V/commit/9f9ceff0fd5c2b0321b8d652ad11e5b2a1cbcd73)

- **作者**: Shankun Wang
- **时间**: 2026-08-24T08:13:05Z
- **提交信息**: Add sol_attn for 5090(sm120) (#1385)

Co-authored-by: Yang Yong (雍洋) <yongyang1030@163.com>

### [2516179](https://github.com/ModelTC/LightX2V/commit/25161798e10d5dda94466fba6918519657031353)

- **作者**: STwangyingrui
- **时间**: 2026-08-24T08:09:21Z
- **提交信息**: Optimize MiniMax-H3 Video VAE encoder (#1422)

Parallelizes MiniMax-H3 Video VAE encoding across ranks using the
balanced P2P tile path, and extends vae_use_compile to the encoder. T2AV
is unaffected because it does not use the encoder; image-conditioned
tasks such as I2AV see limited impact, while Ref2AV benefits
substantially because it encodes long reference videos.

### [8b6c7b7](https://github.com/ModelTC/LightX2V/commit/8b6c7b74f9546f71660494f964ff715947545de3)

- **作者**: STwangyingrui
- **时间**: 2026-08-24T07:40:55Z
- **提交信息**: Add aggressive MiniMax-H3 VAE decode tile shapes (#1398)

Adds resolution-specific decode tile shapes for landscape 768p and 544p
workloads. Larger tiles improve VAE performance but may affect visual
quality, so the optimization is limited to validated landscape
resolutions.

### [d6d21d2](https://github.com/ModelTC/LightX2V/commit/d6d21d2a83e14079c52a5dbfd887ea96dc6db86d)

- **作者**: Xin Qiu
- **时间**: 2026-08-24T07:11:43Z
- **提交信息**:  feat(xpu): add dynamic W8A8 INT8 inference for MiniMax-H3 (#1420)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2201
- **最后更新**: 2026-08-24T14:08:47Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

# 提交分析：Update Lingbot Worl, Lingbot Video, Minimax-H3 and Minimax-H3 Control (#506)

## 1. 主要更新类型
本次提交属于**功能新增与模型集成**，核心是更新多个视频生成模型的接入支持。

## 2. 关键变更点及与项目方向的关系
- **Lingbot World 与 Lingbot Video**：新增或更新了这两个视频生成模型的适配，扩展了项目支持的模型生态。
- **Minimax-H3 及 Minimax-H3 Control**：引入或优化了 Minimax-H3 系列模型及其可控生成版本，强化了视频生成中的条件控制能力。

这些变更与 VideoX-Fun 作为多模型视频生成工具平台的定位高度一致——项目旨在集成多种前沿视频生成模型（如 CogVideoX、Wan 系列），本次更新进一步丰富了模型库，提升了平台兼容性。

## 3. 对项目的影响和潜在意义
- **生态扩展**：新增模型支持使项目覆盖更多主流视频生成方案，增强了对不同用户需求的适配能力。
- **可控性提升**：Minimax-H3 Control 的加入强化了视频生成中的精细控制能力，符合视频创作工具向可控化、专业化发展的趋势。
- **社区吸引力**：持续集成新模型有助于吸引更多开发者与创作者，提升项目活跃度和影响力。

## 4. 值得关注的技术点
- **多模型适配架构**：项目需维护统一的接口层以兼容不同模型的输入输出格式，本次更新验证了该架构的可扩展性。
- **Control 版本支持**：Minimax-H3 Control 涉及条件生成技术（如姿态、深度图等控制信号），其集成方式值得关注，可能为后续其他模型的可控版本提供参考模板。

## 5. 对项目发展的影响
基于 README 可知，VideoX-Fun 致力于打造一站式视频生成平台，并已支持 CogVideoX-Fun 和 Wan-Fun 等模型。本次提交延续了“模型多元化 + 可控生成”的发展路径，有助于：
- 巩固项目在视频生成工具领域的竞争力；
- 吸引更多基于不同模型生态的用户群体；
- 为后续引入更多先进模型（如 Sora 类、DiT 类）奠定架构基础。

整体而言，这是一次稳健的生态扩展型更新，符合项目长期发展方向。

## 详细提交记录

### [b0acf91](https://github.com/aigc-apps/VideoX-Fun/commit/b0acf916c215705ac212fc51b2d9007bbc6df51b)

- **作者**: Bubbliiiing
- **时间**: 2026-08-24T08:47:38Z
- **提交信息**: Update Lingbot Worl, Lingbot Video, Minimax-H3 and Minimax-H3 Control (#506)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6232
- **最后更新**: 2026-08-24T21:26:14Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 6
- **主要提交者**: eigen, Anthony Chang, Guangyun Han

## AI分析总结

# FlashInfer 提交分析总结

## 主要更新类型

本次提交包含**功能新增**（SM120 NVFP4 SVDQuant GEMM、Blackwell Mamba SSDCombined）、**性能优化**（GDN非CP启动开销降低）、**Bug修复**（sccache兼容性、MXFP8策略对齐）、**API行为对齐**（Unified MoE与Flat API一致性）。

## 关键变更点

1. **CI修复**：绕过CUDA 13.4下sccache对nvcc的解析错误，避免fatbinary构建失败，属基础设施维护。
2. **SM120 NVFP4 SVDQuant GEMM**：新增融合残差+BF16 LoRA更新内核，支持SM120/SM121，含自动调优和IKET性能分析。
3. **Blackwell Mamba SSDCombined**：为GB300/B200提供Cake实现，相比CuTe基线最高3.2倍加速，完成GSM8K准确率验证。
4. **GDN启动开销优化**：缓存内核对象和编译选项，通过原始TVM-FFI参数重放，消除eager路径重复准备。
5. **MoE API对齐**：统一`do_finalize=False`返回契约，支持多种精度格式，修复FP4权重处理缺陷。
6. **MXFP8策略修正**：分离plain/gated MoE tactic契约，调整FP8 stage策略并失效过期autotuner缓存。

## 项目影响与意义

这些提交强化了FlashInfer作为**高性能GPU推理内核库**的定位。新增的Blackwell和SM120支持直接扩展了硬件覆盖范围，性能数据（最高3.2x加速）巩固了其在高性能内核领域的竞争力。MoE API对齐和MXFP8策略修正提升了框架的**正确性和一致性**，对下游框架（如SGLang、TRTLLM）集成至关重要。

## 值得关注的技术点

- **融合内核设计**：将残差加法和LoRA更新融合进量化GEMM，减少内存往返。
- **Cake vs CuTe对比**：展示了不同DSL实现策略的性能差异。
- **缓存与重放机制**：通过对象缓存和原始参数传递降低启动开销。
- **契约对齐策略**：通过fake实现和数值验证确保API行为一致性。

## 对项目发展的影响

这些提交表明FlashInfer正沿着**多硬件支持**（Blackwell、SM120）、**多精度优化**（NVFP4、MXFP8、FP4）和**框架集成友好性**三个方向推进。CI修复和策略对齐体现了项目对**工程质量和生态兼容性**的重视，为吸引更多下游框架集成和社区贡献奠定基础。

## 详细提交记录

### [cf9a04d](https://github.com/flashinfer-ai/flashinfer/commit/cf9a04d9b6c97634051d7715aad72550277dd9e3)

- **作者**: Jonathan Dierksen
- **时间**: 2026-08-24T19:29:48Z
- **提交信息**: ci: disable sccache for cu134 nvcc (#4682)

## 📌 Description

CUDA 13.4 changes `nvcc --dryrun` output in a way that sccache v0.17.0
parses incorrectly. The missing compile steps later surface as
`fatbinary` failures because the expected cubins were never produced.

- Bypass sccache for cu134 NVCC invocations while keeping host C++
compilation cached.
- Accept both CUDA version forms used by the release/nightly (`13.4`)
and PR (`134`) build paths.
- Trigger the Release dry-run matrix when the shared JIT-cache helper
changes, so both cu134 architecture jobs exercise this workaround before
merge.
- Remove the guard once the pinned sccache release includes the upstream
CUDA 13.3+ fix.

## 🔍 Related Issues

- Upstream fix:
[mozilla/sccache#2722](https://github.com/mozilla/sccache/pull/2722)
- Failing nightly: [run
32544126473](https://github.com/flashinfer-ai/flashinfer/actions/runs/32544126473)

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

Focused validation passed:

- `bash -n scripts/jit_cache_build_common.sh`
- `shellcheck scripts/jit_cache_build_common.sh`
- Mocked launcher checks for CUDA `13.4`, `134`, and `13.0`
- Release workflow YAML parse
- `pre-commit run --all-files`
- `git diff --check`

## Reviewer Notes

This intentionally disables only the affected NVCC launcher for cu134.
The sccache server and host C++ launcher remain enabled so safe cache
hits are preserved. The Release workflow should provide the end-to-end
cu134 x86_64 and aarch64 validation.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved CUDA 13.4 build compatibility by avoiding an incompatible
compiler-cache path.
  * Preserved compiler caching for other supported CUDA versions.

* **Chores**
* Updated release automation to recognize changes affecting shared build
tooling.
* Added clearer build logs showing which compiler-cache launchers are
enabled.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [530897b](https://github.com/flashinfer-ai/flashinfer/commit/530897b20ae9a0168b70068ed0d48e57412d92f6)

- **作者**: Anthony Chang
- **时间**: 2026-08-24T17:00:10Z
- **提交信息**: feat: SM120 NVFP4 SVDQuant Gemm in CuteDSL (#4420)

## 📌 Description

This PR adds SM120/SM121 CuTe DSL support for NVFP4 SVDQuant GEMM under
the
existing FlashInfer API. It provides a true fused residual-plus-BF16
LoRA-up
kernel and retains the unfused composition as an explicit correctness
oracle.

The complete path also:

- adds fused and unfused SM120 dispatch to `mm_nvfp4_svdquant` and
  `svdquant_linear` without changing API contracts;
- fuses BF16 smoothing into NVFP4 activation quantization and executes
  LoRA-down on BF16 tensor cores;
- aliases LoRA-up correction storage with released residual-mainloop A/B
  stages and uses the same producer/consumer pipeline;
- autotunes fused versus unfused implementation choice and SM120 M/N/K
tile
  tactics;
- adds SM120/SM100 coverage plus SVDQuant trace templates, examples,
  and generated goldens; and
- instrument the sm120 gemm kernel with IKET regions. IKET is disabled
by default and
ordinary and instrumented specializations have distinct cache
identities.

### Performance

Reportable performance is from RTX PRO 6000 only. The tables below use
rank
32, CUDA Graph replay, and warm-L2 timing. They report complete
`svdquant_linear` latency, gains over hidden BF16 and per-tensor FP8
baselines,
and the fused/unfused correction comparison. `residual_fp4/fused`
compares
latency; TFLOPS and microseconds share one cell as `TFLOPS / us`.

Reproduce the benchmark script's complete default Qwen3-image sweep from
the
repository root on an idle, exclusive RTX PRO 6000. The defaults cover
three
`(N,K)` pairs, four `M` values, and rank 32:

```bash
python -u benchmarks/bench_nvfp4_svdquant_gemm.py \
  --svdquant-backend fused \
  --cuda-graph \
  --no-cold-l2-cache
```

| M | N | K | R | `svdquant_linear` us | gain vs BF16 | gain vs FP8 |
residual_fp4/fused | residual FP4 TF/s / us | fusion gain | fused TF/s /
us | unfused TF/s / us |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 4096 | 3072 | 3072 | 32 | 97.44 | +144.1% | +23.0% | 0.958 | 1173.00 /
65.91 | +97.7% | 1135.86 / 68.77 | 574.56 / 135.96 |
| 6889 | 3072 | 3072 | 32 | 127.65 | +170.4% | +41.3% | 0.953 | 1335.73
/ 97.34 | +100.6% | 1286.10 / 102.15 | 641.28 / 204.87 |
| 9216 | 3072 | 3072 | 32 | 182.14 | +152.6% | +35.6% | 0.950 | 1255.88
/ 138.51 | +100.3% | 1205.55 / 145.79 | 601.89 / 292.01 |
| 16384 | 3072 | 3072 | 32 | 358.98 | +137.8% | +24.8% | 0.939 | 1262.19
/ 245.00 | +167.9% | 1197.99 / 260.82 | 447.11 / 698.84 |
| 4096 | 12288 | 3072 | 32 | 308.59 | +171.5% | +45.1% | 0.950 | 1277.15
/ 242.13 | +174.5% | 1226.15 / 254.83 | 446.72 / 699.46 |
| 6889 | 12288 | 3072 | 32 | 486.36 | +176.0% | +49.7% | 0.938 | 1244.37
/ 417.96 | +197.4% | 1179.89 / 445.40 | 396.68 / 1324.81 |
| 9216 | 12288 | 3072 | 32 | 624.29 | +193.3% | +59.3% | 0.949 | 1271.11
/ 547.38 | +208.3% | 1219.34 / 576.57 | 395.54 / 1777.42 |
| 16384 | 12288 | 3072 | 32 | 1121.85 | +191.3% | +54.5% | 0.943 |
1276.91 / 968.71 | +211.2% | 1216.82 / 1027.13 | 391.04 / 3196.17 |
| 4096 | 3072 | 12288 | 32 | 348.53 | +145.9% | +33.5% | 0.991 | 1243.46
/ 248.69 | +24.2% | 1235.55 / 250.93 | 994.43 / 311.78 |
| 6889 | 3072 | 12288 | 32 | 633.92 | +115.2% | +13.8% | 0.986 | 1387.66
/ 374.80 | +32.7% | 1372.01 / 380.07 | 1033.84 / 504.39 |
| 9216 | 3072 | 12288 | 32 | 883.67 | +112.4% | +9.6% | 0.986 | 1296.19
/ 536.79 | +32.9% | 1281.84 / 544.21 | 964.17 / 723.52 |
| 16384 | 3072 | 12288 | 32 | 1552.04 | +116.1% | +14.6% | 0.980 |
1311.20 / 943.37 | +47.1% | 1287.78 / 963.03 | 875.48 / 1416.56 |

## 🔍 Related Issues

N/A.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
> [pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

```bash
python -m pytest -q tests/gemm/test_nvfp4_svdquant_gemm.py -k "sm120"
```

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added NVFP4 SVDQuant support across SM100/SM103 and SM120/SM121 GPUs.
* Added selectable fused, unfused, automatic, and CuTe DSL execution
backends.
  * Added BF16 smooth quantization and FP8 residual benchmark baselines.
* Added CUDA Graph, L2-cache, autotuning, and expanded performance
measurement options.
* Added trace definitions for NVFP4 SVDQuant GEMM, linear operations,
smooth quantization, and BF16 GEMM.

* **Bug Fixes**
* Updated SM120/SM121 backend selection to support CUDA 12.9 and newer.
  * Improved input, shape, dtype, and device validation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [624fce1](https://github.com/flashinfer-ai/flashinfer/commit/624fce191f36ec143b32189ed01d14afb75c4594)

- **作者**: eigen
- **时间**: 2026-08-24T14:15:15Z
- **提交信息**: feat(cake_mamba): add Blackwell Mamba SSDCombined (#4576)

| Evidence | Value |
|---|---|
| Tracker |
[#4254](https://github.com/flashinfer-ai/flashinfer/issues/4254) |
| SGLang integration |
[sgl-project/sglang#35444](https://github.com/sgl-project/sglang/pull/35444)
|
| Model |
`nvidia/Nemotron-H-8B-Base-8K@20acad0a529d386e3c7115b8635d482f9023e1b9`
|
| Hardware | BF16 TP2, 2x NVIDIA GB300 |
| Accuracy protocol | Full GSM8K test, 1,319 questions, 8 train-set CoT
shots, greedy, `max_new_tokens=512`, last-number exact match |
| Dataset SHA256 |
`3730d312f6e3440559ace48831e51066acaca737f6eabec99bccb9e4b3c39d14` |

| Kernel portfolio | Speedup rows | Minimum | Geometric mean | Maximum |
|---|---:|---:|---:|---:|
| GB300 / SM103 | 48 / 48 | 1.321x | 1.847x | 2.808x |
| B200 / SM100 | 48 / 48 | 1.319x | 1.919x | 3.222x |

| GB300 public API row | CuTe | Cake | Speedup | Output check |
Final-state check |
|---|---:|---:|---:|---|---|
| H128/G8 batched B1 x C1 | 0.070689 ms | 0.043328 ms | 1.6315x | pass |
pass |
| H128/G8 packed `[96,160]`, zero initial state, z gate | 0.113696 ms |
0.090384 ms | 1.2579x | pass, max abs 0.0625 | pass, max abs 0.00390625
|
| H8/G8 batched B1 x C1 | 0.070960 ms | 0.041968 ms | 1.6908x | pass |
pass |
| H8/G8 varlen S4 x C1 | 0.076385 ms | 0.072401 ms | 1.0550x | pass |
pass |

| Cache-on E2E run | Backend | Radix cache | Correct | Accuracy |
Invalid |
|---|---|---:|---:|---:|---:|
| Matched run | Existing `flashinfer` | On | 785 / 1,319 | 59.5148% | 0
|
| Matched run | Original `flashinfer_ssd` / CuTe | On | 770 / 1,319 |
58.3776% | 1 |
| Matched run | Cake | On | 751 / 1,319 | 56.9371% | 0 |
| Independent repeat | Cake | On | 766 / 1,319 | 58.0743% | 0 |

| E2E baseline | Workload | Baseline | Cake | Speedup |
|---|---|---:|---:|---:|
| Existing `flashinfer` | TTFT, input 4096 / output 1 / concurrency 1 |
50.717 ms | 37.159 ms | 1.3648x |
| Existing `flashinfer` | Total throughput, input 2048 / output 8 /
concurrency 16 | 84,140.9 tok/s | 126,098.0 tok/s | 1.4987x |
| Original `flashinfer_ssd` / CuTe | TTFT, input 4096 / output 1 /
concurrency 1 | 40.640 ms | 37.159 ms | 1.0937x |
| Original `flashinfer_ssd` / CuTe | Total throughput, input 2048 /
output 8 / concurrency 16 | 121,311.7 tok/s | 126,098.0 tok/s | 1.0395x
|

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: FlashInfer Source Export <flashinfer-source-export@example.invalid>

### [f47f2d2](https://github.com/flashinfer-ai/flashinfer/commit/f47f2d254d78afb7bf4600170f007edd4a6b556e)

- **作者**: Guangyun Han
- **时间**: 2026-08-24T11:31:00Z
- **提交信息**: perf(gdn): reduce non-CP CuTeDSL launch overhead (#4699)

Cache SM90 and SM120 non-CP kernel objects and compile options, and
construct CuTe tensor wrappers only during compilation. Replay compiled
kernels through raw TVM-FFI arguments to remove repeated launch
preparation from the eager path.

follow up of #4374 for non-CP launch path.

### [bf6a047](https://github.com/flashinfer-ai/flashinfer/commit/bf6a0471c0b3387c3707c1f97b8c89cf5b5660ce)

- **作者**: feih-nv
- **时间**: 2026-08-24T08:35:18Z
- **提交信息**: feat(moe): align unified MoE do_finalize behavior with flat API (#4614)

## 📌 Description

Aligns Unified MoE `do_finalize=False` behavior with the TRTLLM Flat
API.
- Returns `[gemm2_output, expert_weights, expanded_idx_to_permuted_idx]`
- Enables unfinalized output for TRTLLM BF16, FP8 block, FP8 per-tensor,
FP4, MxInt4, and MXFP8 runners
- Returns BF16 expert weights for `FromLogits` and `PackedPrecomputed`
routing
- Preserves caller-provided BF16/FP32 weights for `UnpackedPrecomputed`
routing
- Supports BF16 and FP32 routing logits, including MxInt4 logits and
bias
- Correctly returns packed FP4 routing weights without accessing an
undefined launcher tensor
- Models finalized and unfinalized return contracts in fake
implementations
- Adds numerical host-side recombination and permutation validation

## 🔍 Related Issues

Closes #3926

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests
Tested in `flashinfer/flashinfer-ci-cu130:latest` on SM100:
- 18/18 targeted unfinalized fuzz configurations passed
- Unified MoE contract and runner-support tests passed
- MxInt4 FP32 logits and bias tests passed
- Packed-precomputed tests passed across all targeted TRTLLM variants

## Reviewer Notes
Please focus on:
- Unified and Flat API unfinalized return-contract parity
- Ownership and unpacking of routing-weight buffers
- Packed FP4 expert-weight handling
- FakeTensor output contracts
- MxInt4 FP32 routing logits and bias support

### [ff22228](https://github.com/flashinfer-ai/flashinfer/commit/ff22228d2fa144e9ac6a0d841f2e9ba767ba0f0a)

- **作者**: CarstyYou
- **时间**: 2026-08-24T07:53:46Z
- **提交信息**: fix(sm120): align MXFP8 plain tactic and FP8 moe stage policy (#4660)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR separates the SM120 MXFP8 plain and gated MoE tactic contracts,
aligns the FP8 plain fallback/tuned stage policy, and invalidates stale
autotuner cache entries after the tactic and implementation changes.

MXFP8 tactic contract:

- plain GranK=32/128 supports `M128N128`
- gated GranK=32 supports `M128N64` and does not expose `M128N128`
- gated GranK=128 supports both `M128N64` and the existing `M128N128`
- Python registries, C++ validation, leaf dispatch, and forced-tactic
tests use the same contract

FP8 stage/store contract:

- plain fallback/tuned M32/M64/M128/SwapAB stages are `4/4/3/4`
- gated fallback/tuned stages remain `2/2/2/2`
- all FP8 blockscaling paths disable staged R2G
- gated non-SwapAB retains the existing load/store physical split;
SwapAB retains Direct-STG

The gated stage limit is resource-qualified on RTX PRO 6000 Blackwell
Server Edition. Stage3 requests for M32/M64/M128/SwapAB are
`120832/141312/117760/103424` bytes, all above the `101376`-byte opt-in
dynamic-SMEM cap. Gated GranK=32 `M128N128K64 S4` likewise compiles but
cannot launch because its dynamic-SMEM request is invalid, so it remains
excluded.

The PR contains only the 6KD-aligned SM120 CuTe C++ changes and
intentionally excludes the CuteDSL grouped MoE additions.

Validation on an exclusive 188-SM RTX PRO 6000 Blackwell Server Edition
GPU:

- `tests/grouped_mm/test_cute_sm120_fp8.py`: 107 passed
- `tests/grouped_mm/test_cute_sm120_mxfp8.py`: 343 passed
- gated GranK=128 `M128N128K64 S4`: JIT compile and forced correctness
passed
- `pre-commit run --all-files`: all hooks passed, including
clang-format, mypy, and ruff

## 🔍 Related Issues

N/A

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

Please focus on the plain/gated tactic separation, the GranK-dependent
gated `M128N128` guard, and the FP8 plain-versus-gated stage policy.

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4043
- **最后更新**: 2026-08-24T22:30:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: lpc0220

## AI分析总结

### 提交分析总结

**1. 主要更新类型**  
本次提交属于**性能优化**与**架构调整**，具体为针对特定硬件（NVIDIA sm_100a 架构）的**功能路由优化**，而非新增用户可见功能或修复缺陷。

**2. 关键变更点及与项目方向的关系**  
- 变更内容：将 block-sparse VSA（可变步长注意力）计算路径在 sm_100a 架构上改为**可选启用**（通过环境变量 `FASTVIDEO_VSA_SM100A` 控制），默认不激活。  
- 与项目方向关联：FastVideo 作为高性能视频生成/处理框架，其核心目标之一是**最大化硬件利用率**。此变更针对新一代 GPU 架构（sm_100a，即 Blackwell 系列）进行**专门优化路径的隔离**，避免在非目标硬件上引入兼容性风险，同时为高端硬件预留性能提升空间。这符合项目“面向未来硬件迭代”的技术路线。

**3. 对项目的影响和潜在意义**  
- **短期影响**：默认行为不变，现有用户无感知；但为 sm_100a 用户提供了**性能调优入口**，可手动开启更高效的稀疏注意力计算。  
- **长期意义**：  
  - 降低新架构适配风险，通过 opt-in 机制逐步验证稳定性，避免激进默认导致回归。  
  - 为后续 Blackwell 系列 GPU 的全面优化奠定基础，体现项目对**前沿硬件生态的主动跟进**。  
  - 代码结构上，将特定架构逻辑与通用路径解耦，提升可维护性。

**4. 值得关注的技术点**  
- **Block-sparse VSA**：一种针对长序列视频/图像生成的稀疏注意力机制，可显著降低计算量，但实现复杂，对硬件指令集敏感。  
- **sm_100a 架构**：NVIDIA 下一代数据中心 GPU，支持新的张量核心指令，此提交表明项目已开始针对其特性做**底层算子适配**。  
- **环境变量开关模式**：通过 `FASTVIDEO_VSA_SM100A` 控制，属于典型的“特性开关”设计，便于灰度发布和 A/B 测试。

**5. 对项目发展的影响（结合 README 背景）**  
FastVideo 定位为**高性能、可扩展的视频生成工具**，其文档强调快速上手和社区协作。本次提交虽小，但意义在于：  
- **技术前瞻性**：提前布局下一代硬件，保持项目在性能竞赛中的领先地位，吸引高端用户和开发者。  
- **稳定性优先**：通过 opt-in 机制，避免因新架构优化而影响主流用户（如 A100/H100）的体验，符合“快速迭代但稳定交付”的社区理念。  
- **生态建设**：为后续针对 Blackwell 的深度优化（如 FlashAttention-3 集成）铺路，可能成为项目在 2025 年硬件换代期的关键竞争力。

**总结**：这是一次**谨慎而前瞻**的底层优化提交，通过特性开关隔离新硬件路径，既保障了现有稳定性，又为未来性能突破预留了空间，体现了项目在工程严谨性与技术野心之间的平衡。

## 详细提交记录

### [7a42851](https://github.com/hao-ai-lab/FastVideo/commit/7a4285189f5e3dd057e57df98935e7aab685b857)

- **作者**: lpc0220
- **时间**: 2026-08-24T22:26:56Z
- **提交信息**: [kernel] Route block-sparse VSA to the sm_100a forward behind FASTVIDEO_VSA_SM100A (opt-in) (#1754)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34371
- **最后更新**: 2026-08-24T22:11:42Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Shivam Shrirao, Sayak Paul, Sreekant Baheti

## AI分析总结

### 主要更新类型
- **功能新增**：Fibo Edit 管道支持多参考图像条件化与批处理。
- **文档更新**：修正 Fibo Edit 文档、添加 `fp16_safetensors` 命令弃用说明。
- **Bug修复**：修正重复单词和拼写错误（纯文本，无行为变化）。

### 关键变更点与项目方向
- **Fibo Edit 升级**：从单一参考图像转向多参考图像和掩码处理，并改用 Gemini 提示词到 JSON 的流程，同时将模型 ID 更正为规范拼写（`Fibo-Edit-1.5-base/turbo`）。这直接响应了用户对复杂编辑场景（如多对象、多区域）的需求，强化了 diffusers 在图像编辑领域的实用性和灵活性。
- **代码简化**：在 Fibo 管道中，用 `self.image_processor.preprocess` 替代手动 numpy 归一化，并移除 `_vae_safe_size` 辅助函数，统一了参考图像处理逻辑，降低了维护成本。
- **文本清理**：修复八处错误消息和两处文档字符串中的重复词，以及一处拼写错误，提升了代码质量和用户可读性，虽无功能影响，但体现了对细节的重视。
- **弃用通知**：在 CLI 文档中标记 `fp16_safetensors` 为弃用，引导用户转向更现代或更安全的模型保存方式，符合项目持续演进和最佳实践的方向。

### 对项目的影响与潜在意义
- **增强编辑能力**：多参考条件化使 Fibo Edit 能处理更复杂的编辑任务（如多对象替换、区域掩码引导），扩大了应用场景，可能吸引更多专业用户。
- **提升可维护性**：简化参考图像编码和掩码处理逻辑，减少代码冗余，便于未来扩展和社区贡献。
- **改善用户体验**：文档修正和弃用提示降低了使用门槛，避免用户因错误信息或过时命令而困惑。

### 值得关注的技术点
- **注意力掩码处理**：将掩码分支简化为 `if not attention_mask.all():`，更高效地判断是否需要掩码，避免不必要的计算。
- **图像预处理统一**：依赖 `image_processor.preprocess` 确保与模型训练时的预处理一致，减少因手动归一化导致的潜在不一致问题。
- **批处理支持**：多参考图像和批处理能力暗示了底层张量操作的优化，可能涉及动态形状处理或内存管理，值得深入阅读代码。

### 对项目发展的影响
- 结合 README 中 diffusers 作为生成模型工具库的定位，这些提交体现了项目在**图像编辑**细分领域的深耕，通过功能增强和文档完善，巩固了其作为 Hugging Face 生态中图像生成与编辑核心库的地位。
- 弃用旧命令和清理文本反映了项目对**长期维护**和**用户友好性**的承诺，有助于保持代码库健康，吸引更多开发者参与。
- 整体上，这批提交是渐进式改进，既满足了当前用户需求，也为未来更复杂的编辑功能（如视频编辑或多模态条件）奠定了基础。

## 详细提交记录

### [06e0f2a](https://github.com/huggingface/diffusers/commit/06e0f2a81caaa6eaf4381e25cef07b0819582160)

- **作者**: Shivam Shrirao
- **时间**: 2026-08-24T21:13:05Z
- **提交信息**: Fibo Edit: multi-reference conditioning and batching (#14566)

* Fibo Edit: multi-reference conditioning, batching, timesteps

* docs: simplify Fibo Edit page, fix EXAMPLE_DOC_STRING to the VLM prompt flow

* docs: point Fibo Edit at the Gemini prompt-to-JSON block and the 1.5 base/turbo ids

briaai/FIBO-edit-prompt-to-JSON is retired in favor of
briaai/FIBO-edit-gemini-prompt-to-JSON, which handles multiple reference
images and masks. Also corrects the checkpoint ids to their canonical
briaai/Fibo-Edit-1.5-base and briaai/Fibo-Edit-1.5-turbo spellings.

* apply review feedback on reference handling and the attention mask

- collapse the mask branch to `if not attention_mask.all():` in both Fibo pipelines
- encode references via `self.image_processor.preprocess(...)`, dropping the manual
  numpy normalization and the `_vae_safe_size` helper
- normalize `image` into a reference list once in `__call__`, pass it to `check_inputs`

* make style

* make style

### [efabd60](https://github.com/huggingface/diffusers/commit/efabd60d61c2b7aabf9f182bee6b5b6058980304)

- **作者**: Sreekant Baheti
- **时间**: 2026-08-24T14:50:53Z
- **提交信息**: Fix duplicated words and a misspelling in messages and docstrings (#14287)

Remove accidental repeated words in eight "must have have batch size"
error messages raised by the modular pipelines, and in two docstrings
("Dimension to to encode", "image batch to be be inpainted"). Also fix
"arbitary" to "arbitrary" in the LTX2 pipeline docstring.

Text only, no behavior change.

### [9222edc](https://github.com/huggingface/diffusers/commit/9222edcce3cb9d16d0e2254d4ae8ac918ba2a3fc)

- **作者**: Sayak Paul
- **时间**: 2026-08-24T14:31:21Z
- **提交信息**: Deprecate 'fp16_safetensors' command in CLI documentation (#14583)

Add deprecation notice for 'fp16_safetensors' command.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 431
- **最后更新**: 2026-08-11T01:47:46Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12979
- **最后更新**: 2026-08-24T19:35:15Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Zhongjie Duan, Artiprocher, Yuze-e20

## AI分析总结

# 提交分析总结

## 1. 主要更新类型

本次提交记录包含**文档更新**（占比最大）、**Bug修复**和**代码清理**三类变更。核心工作是围绕README和项目文档体系的大规模重构，同时修复了Flux.2-dev处理器的已知问题。

## 2. 关键变更点

- **文档体系全面重构**：对README_zh.md、模型推理、加速推理、量化、显存管理、模型训练、GPU支持、模型详情、分片训练、差分训练、注意力机制等十余个文档模块进行了系统性更新，并引入Mermaid图表支持，优化了ReadTheDocs上的文档展示效果。
- **Flux.2-dev处理器Bug修复**：针对Flux.2-dev模型的处理逻辑进行了修复，通过合并PR方式合入主分支。
- **清理无用文件**：移除了项目中不再需要的文件，保持仓库整洁。

## 3. 对项目的影响和潜在意义

文档重构是本次提交的核心价值所在。DiffSynth-Studio作为一个功能丰富的扩散模型合成工具，涉及大量专业概念（量化、显存管理、分片训练等），文档质量直接影响用户上手体验和项目采用率。此次更新显著提升了文档的可读性、结构性和可维护性，降低了新用户的使用门槛。Flux.2-dev处理器修复则保证了模型生态的兼容性，避免因模型更新导致的功能失效。

## 4. 值得关注的技术点

- **Mermaid图表集成**：在ReadTheDocs中支持Mermaid图表，使得架构图、流程图等可视化内容可以直接在文档中渲染，大幅提升技术文档的表达效率。
- **文档与代码同步机制**：提交中多次出现“sync docs”操作，表明项目已建立文档与代码同步更新的工作流，这对保持文档时效性至关重要。
- **README多语言维护**：同步更新中英文README，体现了项目的国际化定位。

## 5. 对项目发展的影响

从README可知，DiffSynth-Studio是一个面向专业用户的扩散模型合成工具，其核心竞争力在于功能丰富度和易用性的平衡。本次文档重构直接服务于“降低使用门槛”这一目标，有助于吸引更多用户尝试和采用。同时，Flux.2-dev的及时修复体现了项目对主流模型生态的快速跟进能力，有助于维持其在快速演进的AI开源社区中的竞争力。整体来看，这些提交属于“夯实基础”型工作，为后续功能迭代和用户增长奠定了更好的体验基础。

## 详细提交记录

### [72fb128](https://github.com/modelscope/DiffSynth-Studio/commit/72fb128e07a145323dceb072fe15f902745e18fe)

- **作者**: Yuze-e20
- **时间**: 2026-08-24T10:37:26Z
- **提交信息**: Fix image issues in docs (#1631)

* a try for revise readme

* test

* 1

* 1

* 1

* 1

* 1

* 1

* 1

* 1

---------

Co-authored-by: yjy415 <2471352175@qq.com>

### [5b2f199](https://github.com/modelscope/DiffSynth-Studio/commit/5b2f1998edcb1a65fcc1df5ae0ed9dc42374a153)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-24T08:38:28Z
- **提交信息**: Merge pull request #1632 from modelscope/flux2-processor

Fix Flux.2-dev processor issue

### [9ce375d](https://github.com/modelscope/DiffSynth-Studio/commit/9ce375d3f340eb879e6e127cb106240c0a9196f8)

- **作者**: Artiprocher
- **时间**: 2026-08-24T08:36:28Z
- **提交信息**: remove unnecessary files

### [a96296c](https://github.com/modelscope/DiffSynth-Studio/commit/a96296c3e2909869b5b985d1ffcb1f591e70af6e)

- **作者**: Zhongjie Duan
- **时间**: 2026-08-24T07:29:14Z
- **提交信息**: Refactor Docs (#1630)

* update README_zh.md

* support mermaid on readthedocs

* update setup

* update model inference & accelerated inference

* update quantization

* update VRAM_management.md

* update Model_Training

* update GPU_support

* update GPU_support

* update Model_Details

* update index

* update Split_Training

* update Split_Training

* update Differential_Training

* update attention

* sync docs

* try fix mermaid

* try fix mermaid

* fix mermaid

* update docs main page

---------

Co-authored-by: mi804 <1576993271@qq.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 32378
- **最后更新**: 2026-08-24T22:29:44Z

## 提交统计

- **昨日提交总数**: 39
- **提交者数量**: 20
- **主要提交者**: BingjiaWang, Jimmy Shong, fzyzcjy

## AI分析总结

# sglang 仓库提交分析（第1/1批，共38条提交）

## 一、主要更新类型

本批提交涵盖**功能新增**（约15条）、**Bug修复**（约8条）、**性能优化**（约6条）、**文档更新**（2条）、**代码重构**（约4条）及**CI/基础设施改进**（3条），整体以功能扩展和性能优化为主导。

## 二、关键变更点与项目方向

**1. 扩散模型（Diffusion）支持大幅扩展**（约8条提交）
- 新增对MiniMax H3 GGUF文本编码器、Comfy NVFP4检查点、序列化FP8 CLIP图像编码器、序列化ConvRot W4A4检查点、剪枝MiniMax H3组件、自描述Quanto INT8编码器及混合W4A4/INT8检查点的加载支持
- 新增逐组件量化覆盖功能，提升模型加载灵活性和量化精度控制
- 修复Sana LN调制重命名后的测试导入问题

**2. AMD平台专项优化**（约6条提交）
- 修复Qwen3.5 MTP丢弃融合共享专家权重问题
- 将MoRI路由至Qwen MoE全对全路径
- 去重CP复制状态传输
- Quark共享专家门控识别尾部MTP层
- CI改进：命名实际运行的ROCm镜像、绕过本地注册表拉取

**3. 调度器内部状态增强**（约6条提交）
- 报告服务器全局world size、暴露声明的环境变量
- 支持门控启动以延迟启动内存分配
- 报告逐token权重版本跨度、跟踪已发布权重版本
- 提取`_make_abort_req`和`collect_inflight_reqs`以复用中止路径

**4. 新模型与后端支持**
- 新增MiniCPM-SALA支持
- Humming后端支持原生W4AFP8检查点模式和FP8 DeepEP调度
- Intel XPU支持仅预填充模型
- NPU修复转置批矩阵乘法K*B超限问题

**5. 性能优化**
- Triton滑动窗口扩展注意力KV循环绑定：SWA层-86.6%，预填充GPU-9.4%，位级一致
- ROCm gfx950扩展注意力tile至head_dim≤128：内核-43%，TTFT-14%
- 统一内存批量惰性压缩映射查找优化

**6. 其他修复与清理**
- 修复解码回缩时的循环状态丢失
- 清理重复的Mamba备份辅助函数
- 修复mini-lb转发flush_cache超时参数
- 移除GDN中XPU的causal_conv1d路径
- 文档更新：标记Ling-3.0-flash DSPARK在H200上四种量化验证、拆分Qwen3.8-27B NVFP4单元格

## 三、项目影响与潜在意义

**扩散模型生态扩展**是本批最显著的方向，大量检查点格式和编码器支持使sglang在图像/视频生成领域的兼容性大幅提升，有望吸引更多ComfyUI生态用户。**AMD平台持续优化**表明项目对ROCm/AMD GPU的重视程度加深，与行业趋势一致。**调度器内部状态透明化**为可观测性和运维能力奠定基础，门控启动功能则直接改善大规模部署的内存管理效率。

## 四、值得关注的技术点

- **Triton滑动窗口KV循环绑定**：-86.6%的SWA层加速且位级一致，是极具价值的优化
- **门控启动（Gated Launch）**：延迟启动内存分配，对大规模多模型部署意义重大
- **权重版本追踪**：为动态权重更新和热加载提供基础设施
- **W4A4/FP8混合量化支持**：顺应低精度推理趋势，提升硬件利用率
- **Humming原生W4AFP8模式**：深化MoE后端的量化支持

## 五、对项目发展的影响

sglang正从纯LLM推理引擎向**多模态推理平台**演进，扩散模型支持的快速扩展印证了这一方向。同时，项目在**多硬件平台（AMD/Intel/NPU）** 的持续投入，以及**量化格式兼容性**的深化，表明其目标是成为生产级、硬件无关的统一推理解决方案。调度器基础设施的完善则为大规模集群部署和动态资源管理铺平道路。整体来看，本批提交体现了项目在广度（多模态、多硬件）和深度（性能优化、内部机制）上的双线推进，发展态势积极。

## 详细提交记录

### [3c481b9](https://github.com/sgl-project/sglang/commit/3c481b9421024de4ecc6840159517f83c6acc84d)

- **作者**: BingjiaWang
- **时间**: 2026-08-24T21:49:20Z
- **提交信息**: [Benchmark] Add optional steady-state window for serving metrics (#30918)

### [24bce93](https://github.com/sgl-project/sglang/commit/24bce93c934f798414354341da238a00b4df9b6b)

- **作者**: AMD-yanfeiwang
- **时间**: 2026-08-24T21:43:52Z
- **提交信息**: [AMD][MORI] Deduplicate CP-replicated state transfers (#36025)

### [0d5b5ae](https://github.com/sgl-project/sglang/commit/0d5b5ae6202cbf95c849c55af07424b96405d82f)

- **作者**: jacky.cheng
- **时间**: 2026-08-24T20:18:42Z
- **提交信息**: [AMD] Fix Qwen3.5 MTP dropping fused shared-expert weights (#35719)

### [0665740](https://github.com/sgl-project/sglang/commit/06657409533db4badaf28a741a934e6d53628c37)

- **作者**: jacky.cheng
- **时间**: 2026-08-24T20:04:08Z
- **提交信息**: [AMD][Fix] Route MoRI through the Qwen MoE all-to-all path (#32039)

### [6e2f87d](https://github.com/sgl-project/sglang/commit/6e2f87d589410edd8740a87f8eb73b02e9cf0fe8)

- **作者**: Xinyuan Tong
- **时间**: 2026-08-24T18:05:32Z
- **提交信息**: docs: mark Ling-3.0-flash DSPARK verified for all four quantizations on H200 (#36204)

### [5030637](https://github.com/sgl-project/sglang/commit/5030637c65bab791ca3ec5bfdbe885568abf7df6)

- **作者**: Jimmy Shong
- **时间**: 2026-08-24T17:50:33Z
- **提交信息**: [docs] Split the Qwen3.8-27B NVFP4 cells by lm_head precision (#36020)

### [d10a656](https://github.com/sgl-project/sglang/commit/d10a656ad8601fb91aa0643683d79ade21c11386)

- **作者**: Ke Bao
- **时间**: 2026-08-24T16:52:37Z
- **提交信息**: Cleanup duplicate mamba backup helper (#36203)

### [586211b](https://github.com/sgl-project/sglang/commit/586211bc461c4dbd8df9932bf709aa3d018945d1)

- **作者**: Ke Bao
- **时间**: 2026-08-24T16:12:05Z
- **提交信息**: Add PD test for inkling with mxfp8 KV (#35840)

### [54ec2c4](https://github.com/sgl-project/sglang/commit/54ec2c4699ca29aacb1916e218cad2c78f8ee37b)

- **作者**: Ke Bao
- **时间**: 2026-08-24T16:11:05Z
- **提交信息**: Fix recurrent state loss on decode retraction (#35957)

### [30f9ed0](https://github.com/sgl-project/sglang/commit/30f9ed09d1c84f0fcbeabdb897fb2b027d90af0b)

- **作者**: Mick
- **时间**: 2026-08-24T15:00:49Z
- **提交信息**: [diffusion] feat: support loading minimax h3 gguf text encoders (#36055)

### [9b0007e](https://github.com/sgl-project/sglang/commit/9b0007ed195ff36db2d899541d931c6de7fe510b)

- **作者**: Mick
- **时间**: 2026-08-24T14:57:02Z
- **提交信息**: [diffusion] feat: support loading comfy nvfp4 minimax h3 checkpoints (#36044)

### [76d1401](https://github.com/sgl-project/sglang/commit/76d1401881f2593b0f781146b87ce27583b6209a)

- **作者**: Mick
- **时间**: 2026-08-24T12:35:11Z
- **提交信息**: [diffusion] feat: support mixed w4a4 and int8 checkpoints (#36040)

### [e586a6f](https://github.com/sgl-project/sglang/commit/e586a6f2c5f2d1e0626bbe0cb1580d56c12398a2)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:21:45Z
- **提交信息**: Report the whole server's world size in the scheduler's internal state (#35929)

### [6dd7957](https://github.com/sgl-project/sglang/commit/6dd79576cd97b5caf0e98161c9fc0201f75f88dc)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:20:29Z
- **提交信息**: Expose the declared sglang env vars of a scheduler in its internal state (#35928)

### [c56cee0](https://github.com/sgl-project/sglang/commit/c56cee0f80e7cd7fcfbe9f67fdf5cfe75479f875)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:19:45Z
- **提交信息**: Support gated launch to defer startup memory allocation (#35927)

### [3b24d89](https://github.com/sgl-project/sglang/commit/3b24d8981be52969e28446b22ca6360a25bec36d)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:18:52Z
- **提交信息**: Report per-token weight-version spans in generation meta info (#35926)

### [981dfa2](https://github.com/sgl-project/sglang/commit/981dfa2b83badaf6a8a6b2c14bbf24d7e267bb23)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:17:50Z
- **提交信息**: Make the scheduler track the published weight version (#35925)

### [02a3dca](https://github.com/sgl-project/sglang/commit/02a3dca7384840f6ef11f928284ebae1626dd3f1)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:16:38Z
- **提交信息**: Extract _make_abort_req from the scheduler's abort paths (#35924)

### [a37fdae](https://github.com/sgl-project/sglang/commit/a37fdae56213e7513389ba51187125a6adb62133)

- **作者**: fzyzcjy
- **时间**: 2026-08-24T12:15:09Z
- **提交信息**: Extract collect_inflight_reqs from abort_request for reusing (#35923)

### [9856b58](https://github.com/sgl-project/sglang/commit/9856b58de43dc5730b69c4aae24e48789d871f02)

- **作者**: Mick
- **时间**: 2026-08-24T11:59:35Z
- **提交信息**: [diffusion] feat: support loading serialized fp8 clip image encoders (#36056)

### [b4bd5f9](https://github.com/sgl-project/sglang/commit/b4bd5f91ee8a04135992287637182448db0bf38d)

- **作者**: Hert4
- **时间**: 2026-08-24T11:48:17Z
- **提交信息**: [diffusion] Fix test_model_fast_paths import after sana_ln_modulate rename (#36175)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [bfeae4e](https://github.com/sgl-project/sglang/commit/bfeae4e79a8dc4600e006f1a5fbc85321a01c1a3)

- **作者**: Mick
- **时间**: 2026-08-24T11:13:35Z
- **提交信息**: [diffusion] feat: support loading serialized convrot w4a4 checkpoints (#36039)

### [716a6bf](https://github.com/sgl-project/sglang/commit/716a6bf10ca35cab33309d5177961c954546f2c4)

- **作者**: guzekai01
- **时间**: 2026-08-24T10:59:27Z
- **提交信息**: feat(humming): support native W4AFP8 checkpoint schemas (#32033)

### [21258b7](https://github.com/sgl-project/sglang/commit/21258b7a35e941988409f96b016739713a55ec75)

- **作者**: guzekai01
- **时间**: 2026-08-24T10:59:07Z
- **提交信息**: feat(humming): FP8 DeepEP dispatch for humming MoE backend (#31429)

### [46b92b2](https://github.com/sgl-project/sglang/commit/46b92b22e2505be598a0804318942f7e92140302)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-08-24T10:02:00Z
- **提交信息**: [diffusion] Accelerate LingBot Video RMSNorm in quality=high (#35969)

### [d843386](https://github.com/sgl-project/sglang/commit/d8433868ce8f0e525648426c13c8df9e4f798af4)

- **作者**: Bingxu Chen
- **时间**: 2026-08-24T09:44:53Z
- **提交信息**: [AMD][CI] Temporarily bypass local-registry image pulls (#36171)

### [092d85e](https://github.com/sgl-project/sglang/commit/092d85eb87f6aa5978300767a64044d252f1a2cc)

- **作者**: cauphe
- **时间**: 2026-08-24T09:25:16Z
- **提交信息**: [Feature] Add MiniCPM-SALA support (#30360)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [d251fa2](https://github.com/sgl-project/sglang/commit/d251fa2453584dc3dfe5d149538d312dcf0ede49)

- **作者**: SuperSong
- **时间**: 2026-08-24T09:14:45Z
- **提交信息**: perf(unified-memory): batch lazy-compaction mapping lookup (#34066)

### [51b27f7](https://github.com/sgl-project/sglang/commit/51b27f747ade4a267f37a29457bc8c690100ca9e)

- **作者**: Mick
- **时间**: 2026-08-24T08:39:37Z
- **提交信息**: [diffusion] feat: support loading pruned minimax h3 components natively (#36070)

### [adc09a1](https://github.com/sgl-project/sglang/commit/adc09a1f63b5c8d94d19b13dace6d43c961f819e)

- **作者**: Mick
- **时间**: 2026-08-24T08:37:09Z
- **提交信息**: [diffusion] feat: support loading self-describing quanto int8 encoders (#36052)

### [5081ad5](https://github.com/sgl-project/sglang/commit/5081ad5d4e086caf01ec709b4fccff221351c354)

- **作者**: Mick
- **时间**: 2026-08-24T08:35:48Z
- **提交信息**: [diffusion] feat: add per-component quantization overrides (#36084)

### [317da09](https://github.com/sgl-project/sglang/commit/317da0964e77d35c8285e52305f783981b14ad9a)

- **作者**: gaopengff
- **时间**: 2026-08-24T08:25:47Z
- **提交信息**: [Intel XPU] support prefill only models for xpu (#35072)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [7de80e5](https://github.com/sgl-project/sglang/commit/7de80e566cc04c14a97d35ffd7270bb60186e9ba)

- **作者**: Bingxu Chen
- **时间**: 2026-08-24T08:07:25Z
- **提交信息**: [AMD][CI] Name the ROCm Image That Actually Ran in AMD Job Names (#35686)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [5c46223](https://github.com/sgl-project/sglang/commit/5c4622341ffdeb73109af0521fe7db0d79c42498)

- **作者**: jiayisunx
- **时间**: 2026-08-24T07:59:23Z
- **提交信息**: [GDN] remove XPU path of causal_conv1d_fn and causal_conv1d_update (#35775)

### [2070927](https://github.com/sgl-project/sglang/commit/2070927e00257d923758438c6230de69dc5e882d)

- **作者**: Alex Nails
- **时间**: 2026-08-24T07:58:52Z
- **提交信息**: [Triton] Bound the sliding-window extend-attention KV loop: -86.6% on SWA layers, -9.4% prefill GPU, bit-identical (#34462)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [7bbd0dd](https://github.com/sgl-project/sglang/commit/7bbd0ddeb5f3cae3044f5747eca7e340edffb4f6)

- **作者**: Jacob0226
- **时间**: 2026-08-24T07:53:52Z
- **提交信息**: [AMD] Quark shared-experts gate: recognise a trailing MTP layer (#36124)

Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Thomas Wang <thomawan@amd.com>

### [f464e77](https://github.com/sgl-project/sglang/commit/f464e77d17a3908ad0ea32547b1e8b039bcbd354)

- **作者**: Shangming Cai
- **时间**: 2026-08-24T07:32:57Z
- **提交信息**: fix(mini-lb): forward the flush_cache timeout param to workers (#36150)

### [666b08b](https://github.com/sgl-project/sglang/commit/666b08b4a5e908117e2fad8c5af20b8ac202349e)

- **作者**: Alex Nails
- **时间**: 2026-08-24T07:29:39Z
- **提交信息**: [ROCm] Extend the gfx950 extend-attention tile to head_dim <= 128: -43% kernel, -14% TTFT, bit-identical (#34461)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [c439e77](https://github.com/sgl-project/sglang/commit/c439e77872c9c89dce9cf00558cc327fcf6fb79c)

- **作者**: McZyWu
- **时间**: 2026-08-24T07:22:59Z
- **提交信息**: [bugfix] [NPU] fix transpose batch matmul K*B exceed 65536. (#34715)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1257
- **最后更新**: 2026-08-24T12:12:06Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 89898
- **最后更新**: 2026-08-24T22:30:26Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 18
- **主要提交者**: Lio Einaudi, Kevin H. Luu, wang.yuqi

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交涵盖**Bug修复**（约8项）、**性能优化**（3项）、**功能新增**（2项）、**重构**（3项）、**安全加固**（2项）及**文档更新**（1项），整体以稳定性和效率提升为核心。

### 2. 关键变更点与项目方向
- **安全强化**：强制对所有音频路径应用`VLLM_MAX_AUDIO_CLIP_FILESIZE_MB`限制，并文档化多模态媒体UUID的安全影响，呼应vLLM作为生产级服务对输入安全边界的重视。
- **投机解码扩展**：支持张量并行（TP>1）下的投机解码，并针对FlashAttention元数据重新应用分组几何，提升多GPU场景下的解码效率与正确性。
- **性能调优**：为批量不变持久化矩阵乘法引入按架构调优的配置，在RTX 4090D/H20上实现约3倍解码内核加速；BGE-M3同步池化吞吐提升3.13%，体现对硬件特性和模型推理链路的深度优化。
- **多模态处理**：修复混合CLIP/SigLIP池化批次中的文本编码问题，并缓存常见token序列，减少重复计算，强化多模态推理的准确性与速度。
- **架构重构**：重构批量不变性文件夹、清理废弃参数、移除重复的`VLLM_USE_DEEP_GEMM`检查，提升代码可维护性；新增`UnfinalizedMoEOutput`原型，为Kimi K3模型支持铺路。
- **前端与API**：将`run_batch.py`移出OpenAI文件夹，新增Cohere ChatV2渲染端点，扩展服务兼容性。

### 3. 对项目的影响与潜在意义
- **稳定性提升**：修复DCP稀疏MLA元数据、worker RPC负载释放、CUDA图剖析缺失元数据等问题，减少分布式推理中的潜在崩溃与内存泄漏。
- **生态扩展**：Cohere端点与Kimi K3支持表明vLLM正加速适配更多模型架构，巩固其作为“人人可用的LLM服务”定位。
- **性能竞争力**：内核级调优和投机解码增强，直接提升高负载场景下的吞吐与延迟表现，强化对生产环境的吸引力。

### 4. 值得关注的技术点
- **投机解码与TP结合**：在张量并行下实现投机解码，需协调目标与草稿模型的隐藏维度，是复杂且前沿的优化方向。
- **批量不变内核调优**：按架构定制配置而非通用方案，体现对GPU微架构差异的精细化利用。
- **DCP槽位映射修复**：处理内核块大小与稀疏MLA元数据，涉及分布式检查点的底层正确性，对长序列训练/推理至关重要。

### 5. 对项目发展的影响
结合README中“简单、快速、廉价”的愿景，本次提交通过**安全加固**保障服务可靠性，通过**性能优化**降低推理成本，通过**模型与API扩展**提升通用性。重构与清理则确保代码库在快速迭代中保持健康，为后续功能开发奠定基础。整体上，这些变更推动vLLM向更成熟、更高效、更安全的生产级推理平台演进，同时保持对前沿模型（如Kimi K3）和硬件特性的快速适配能力。

## 详细提交记录

### [0d7d5ed](https://github.com/vllm-project/vllm/commit/0d7d5ed0b2b61da53f682534f1754fe7d0251a34)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-24T21:37:02Z
- **提交信息**: fix(security): enforce VLLM_MAX_AUDIO_CLIP_FILESIZE_MB on all audio paths (#53561)

Signed-off-by: jperezde <jperezde@redhat.com>

### [23ab0cf](https://github.com/vllm-project/vllm/commit/23ab0cfdbc432888549d6f30bb65906aac5cdcda)

- **作者**: Khushali Desai
- **时间**: 2026-08-24T21:33:36Z
- **提交信息**: speculative decoding under tensor parallelism (TP>1) , workspace creation select max hidden dim of target and draft model (#52193)

Signed-off-by: khushali9 <khushali.desai9@gmail.com>

### [f59bb0b](https://github.com/vllm-project/vllm/commit/f59bb0bd8c5ad8a0144ae9abb123df9b2e9425a6)

- **作者**: Wentao Ye
- **时间**: 2026-08-24T21:31:36Z
- **提交信息**: [Refactor] Refactor batch invariance folder (#53619)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [6a9c69f](https://github.com/vllm-project/vllm/commit/6a9c69fa851389dcf1ee5d3a2363e27af665d26d)

- **作者**: Guan-Ming Chiu
- **时间**: 2026-08-24T18:43:57Z
- **提交信息**: [Attention][Spec Decode] Support varlen trtllm-gen decode for adaptive verification (#52157)

Signed-off-by: Guan-Ming (Wesley) Chiu <105915352+guan404ming@users.noreply.github.com>

### [342b8eb](https://github.com/vllm-project/vllm/commit/342b8ebd8bd4595826f29ff95dfc48679a03a95a)

- **作者**: Prudhvi Vuda
- **时间**: 2026-08-24T17:45:42Z
- **提交信息**: [Bugfix][Multimodal] Encode text in mixed CLIP/SigLIP pooling batches (#53165)

Signed-off-by: Prudhvivuda <prudhvi12042001@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [4f686e1](https://github.com/vllm-project/vllm/commit/4f686e182a3460b28df9b8e26b377a5069d519fa)

- **作者**: Jee Jee Li
- **时间**: 2026-08-24T17:19:04Z
- **提交信息**: [MISC] Cleanup deprecated parameters (#53559)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Signed-off-by: Cyrus Leung <cyrus.tl.leung@gmail.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [6648eb1](https://github.com/vllm-project/vllm/commit/6648eb118d77ad001a411cf52f9c6c4719476c83)

- **作者**: Ning Xie
- **时间**: 2026-08-24T16:30:50Z
- **提交信息**: [Core] drop duplicate VLLM_USE_DEEP_GEMM check (#48687)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [7797b60](https://github.com/vllm-project/vllm/commit/7797b6022c129b862e45ae6aed08822e65d1bccb)

- **作者**: Lio Einaudi
- **时间**: 2026-08-24T15:28:51Z
- **提交信息**: [Kernel][Perf] Per-architecture tuned configs for batch-invariant persistent matmul (~3x decode kernels on RTX 4090D/H20) (#53247)

Signed-off-by: LioEinaudi <zhao3024667639@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [29c9af5](https://github.com/vllm-project/vllm/commit/29c9af5211e618bfb78c4140db9e814f1a838aa7)

- **作者**: Wentao Ye
- **时间**: 2026-08-24T15:21:11Z
- **提交信息**: [Kimi K3 Refactor] Add `UnfinalizedMoEOutput` proto following up for #53152 (#53310)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [4c56e62](https://github.com/vllm-project/vllm/commit/4c56e62c85cea8fc2251efc25159836c214402aa)

- **作者**: Kevin H. Luu
- **时间**: 2026-08-24T15:16:28Z
- **提交信息**: [Bugfix][Kimi K3] Skip absent metadata during CUDA graph profiling (#53581)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Codex <codex@openai.com>

### [f620499](https://github.com/vllm-project/vllm/commit/f620499ee3fe18131d71b02e1e8e5f1cf984cf1c)

- **作者**: Misha Goin
- **时间**: 2026-08-24T15:08:43Z
- **提交信息**: [Bugfix][Spec Decode] Reapply group geometry for FlashAttention metadata (#53336)

Signed-off-by: mgoin <mgoin64@gmail.com>

### [9cef631](https://github.com/vllm-project/vllm/commit/9cef631f307dd2a96937bf97b591e64dc0ce85a4)

- **作者**: wang.yuqi
- **时间**: 2026-08-24T15:04:10Z
- **提交信息**: [Frontend] Move run_batch.py out openai folder (#53500)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [22099af](https://github.com/vllm-project/vllm/commit/22099afc6423efa2c6dac58ecaf0c5cbe652ece2)

- **作者**: cjackal
- **时间**: 2026-08-24T15:02:48Z
- **提交信息**: [Bugfix][DCP] Handle sparse MLA metadata after DCP Manager refactor (#52377)

Signed-off-by: cjackal <44624812+cjackal@users.noreply.github.com>

### [ecfa7bb](https://github.com/vllm-project/vllm/commit/ecfa7bb37316a3c1dab345fea4178d81f63b1ce4)

- **作者**: Cyrus Leung
- **时间**: 2026-08-24T14:48:10Z
- **提交信息**: [MM] Cache common token sequences (#53560)

Signed-off-by: DarkLight1337 <tlleungac@connect.ust.hk>
Signed-off-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [4ca856b](https://github.com/vllm-project/vllm/commit/4ca856b0b59d87c7b167d1bd8c748421719c9a57)

- **作者**: 石皮幼鸟
- **时间**: 2026-08-24T14:27:36Z
- **提交信息**: [Bugfix] Release worker RPC payload before next dequeue (#51979)

Signed-off-by: 石皮幼鸟 <2960474346@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [9f295fe](https://github.com/vllm-project/vllm/commit/9f295fe8cee4cbd2b21a5ce3066cec026e4bd2af)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-08-24T14:19:18Z
- **提交信息**: [Docs][Security] Document multimodal media UUID security implications (#53582)

Signed-off-by: jperezde <jperezde@redhat.com>

### [79bb395](https://github.com/vllm-project/vllm/commit/79bb395eea64dbfef99a55f010d2854db71f8571)

- **作者**: Taneem Ibrahim
- **时间**: 2026-08-24T12:33:32Z
- **提交信息**: [Pooling] Improve BGE-M3 sync pooling throughput by up to 3.13% (#53464)

Signed-off-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [41ae917](https://github.com/vllm-project/vllm/commit/41ae917c120f7036210053e0d79e0fb353fbdd46)

- **作者**: andrewbcohere
- **时间**: 2026-08-24T12:27:57Z
- **提交信息**: Add Cohere ChatV2 render endpoint (#53219)

### [e239947](https://github.com/vllm-project/vllm/commit/e239947777e18071c8053195ce599b6511717f67)

- **作者**: Tan Chao
- **时间**: 2026-08-24T11:33:44Z
- **提交信息**: [Bugfix][Frontend] Fix run_batch upload retrying on success and unawaited error body (#50588)

Signed-off-by: Chao Tan <chaos.tc@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0ecc284](https://github.com/vllm-project/vllm/commit/0ecc284790e5403f74b899524ef82ecb69f83cb3)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-08-24T07:28:38Z
- **提交信息**: [Bugfix][Kernel] Handle kernel block sizes in V2 DCP slot mapping (#51031)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-25
**监控日期**: 2026-08-24
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6298
- **最后更新**: 2026-08-24T21:18:50Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 7
- **主要提交者**: WeiQing Chen, Gao Han, bjf-frz

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本次提交记录涵盖**功能新增**（2项）、**Bug修复**（2项）、**CI测试修复**（1项，含两次回退与重试）、**文档更新**（1项），整体以功能增强和稳定性修复为主。

### 2. 关键变更点与项目方向

- **MiniMax-H3扩散连续批处理支持**：为MiniMax-H3模型新增扩散模型的连续批处理能力，直接扩展vLLM-Omni在多模态生成场景下的吞吐能力，与项目“易用、快速、低成本”的定位高度契合。
- **AsyncOmni的暂停/恢复与休眠/唤醒**：为自回归（AR）阶段增加生命周期管理能力，提升异步推理的灵活性和资源调度效率，强化项目在实时交互场景的实用性。
- **LTX-2.5分片加载Bug修复**：防止模型静默加载未索引的Diffusers分片，避免推理结果错误，提升模型加载的可靠性和可诊断性。
- **Wan DMD流水线测试对齐修复**：经过两次回退后重新提交，表明团队在CI测试稳定性上反复调试，最终确保测试与实现对齐。

### 3. 项目影响与潜在意义

- **性能与效率提升**：MiniMax-H3的连续批处理直接提升扩散模型的推理吞吐，降低服务成本，是vLLM-Omni在“便宜”维度上的重要进展。
- **可靠性增强**：LTX-2.5的修复避免了静默失败，对生产环境至关重要；CI测试的最终对齐保障了回归测试的有效性。
- **运维友好性**：AsyncOmni的暂停/恢复能力为资源调度和按需推理提供了基础，有助于多租户场景下的成本优化。

### 4. 值得关注的技术点

- **扩散模型连续批处理**：这是vLLM生态中较新的能力，MiniMax-H3的支持表明vLLM-Omni正积极跟进扩散模型的批处理优化，可能涉及注意力机制或去噪步数的动态调度。
- **AsyncOmni生命周期管理**：暂停/恢复与休眠/唤醒的实现涉及状态机设计和资源释放策略，对异步推理框架的工程复杂度有较高要求，值得关注其实现细节。
- **CI测试的反复回退**：Wan DMD测试经历两次Revert后重新提交，暗示该测试存在环境依赖或对齐逻辑的复杂性，最终修复方案可能涉及基准对齐或数值容差调整。

### 5. 对项目发展的影响

vLLM-Omni致力于成为“人人可用的多模态模型服务”平台。本次提交在**扩散模型支持广度**（新增MiniMax-H3）、**异步推理灵活性**（AsyncOmni生命周期管理）和**系统稳定性**（LTX-2.5修复、CI对齐）三个方向同步推进，表明项目正从“能跑”向“高效、可靠、易运维”演进。特别是扩散模型连续批处理和异步生命周期管理，为未来支持更多视频生成、语音合成等长时任务奠定了架构基础，有助于吸引更多生产级用户。文档更新（微信二维码）则反映了项目在社区运营上的投入，与开源生态建设相辅相成。整体来看，这些提交体现了vLLM-Omni在技术深度和工程成熟度上的双重提升。

## 详细提交记录

### [678aa25](https://github.com/vllm-project/vllm-omni/commit/678aa25864334286d778fb3853b3c34f4b2ef0a6)

- **作者**: Hongsheng Liu
- **时间**: 2026-08-24T15:40:01Z
- **提交信息**: Revert "Revert "[CI]Fix Wan DMD pipeline test alignment"" (#6578)

### [a94b258](https://github.com/vllm-project/vllm-omni/commit/a94b2580a193c8f0cd6d322bd69335f55f9d0401)

- **作者**: Gao Han
- **时间**: 2026-08-24T14:26:55Z
- **提交信息**: Revert "[CI]Fix Wan DMD pipeline test alignment" (#6574)

### [d150a4f](https://github.com/vllm-project/vllm-omni/commit/d150a4fde77d15d466102323a4048b0a8631d74c)

- **作者**: 汪志鹏
- **时间**: 2026-08-24T13:08:53Z
- **提交信息**: [Feature][MiniMax-H3] Support diffusion continuous batching (#5810)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [aa69acb](https://github.com/vllm-project/vllm-omni/commit/aa69acbd090d4b6e021ed2bc22966fca03504572)

- **作者**: Mu GuanLin
- **时间**: 2026-08-24T12:57:24Z
- **提交信息**: [Bugfix] Prevent LTX-2.5 from silently loading unindexed Diffusers shards (#6234)

Signed-off-by: mglyn <1203789601@qq.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [0e4b28f](https://github.com/vllm-project/vllm-omni/commit/0e4b28f491721af618525f4ba9f679f0eb5a7157)

- **作者**: bjf-frz
- **时间**: 2026-08-24T09:43:24Z
- **提交信息**: [CI]Fix Wan DMD pipeline test alignment (#6557)

Signed-off-by: bjf-frz <frz123db@gmail.com>

### [f446468](https://github.com/vllm-project/vllm-omni/commit/f446468c03e96a2359b74e372c258eb83e04d11a)

- **作者**: WeiQing Chen
- **时间**: 2026-08-24T08:46:02Z
- **提交信息**: [Doc] Update vLLM-Omni WeChat QR code (#6535)

Signed-off-by: David Chen <530634352@qq.com>

### [d15b7ca](https://github.com/vllm-project/vllm-omni/commit/d15b7ca3e12ce969a37547f7480470b5b755dbf3)

- **作者**: Nguyen Kha Nhat Long
- **时间**: 2026-08-24T08:21:32Z
- **提交信息**: [Feature]: Support pause / resume and sleep / wake for AR stages in AsyncOmni (#6084)

Signed-off-by: knlnguyen1802 <knlnguyen1802@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

---
