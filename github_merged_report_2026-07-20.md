# GitHub Stars 合并报告 - 2026-07-20

**合并日期**: 2026-07-21
**监控日期**: 2026-07-20
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


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2098
- **最后更新**: 2026-07-20T16:41:31Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bin Jia

## AI分析总结

好的，以下是对该仓库昨日提交记录的总结分析：

### 1. 主要更新类型
- **功能新增（Feat）**，且带有 `[perf]` 前缀，表明偏重性能分析相关能力。

### 2. 关键变更点及其与项目整体方向的关系
- **变更内容**：新增对 DeepSeek V4 模型的 MFU（Model FLOPS Utilization，模型浮点运算利用率）计算支持。
- **与项目方向的关系**：VeOmni 定位为“以模型为中心的分布式训练方案库”（Model-Centric Distributed Recipe Zoo），旨在高效训练多种模态的模型。支持热门大模型（如 DeepSeek V4）的 MFU 计算，是完善其“训练配方”生态的关键一步，直接服务于用户对训练效率的量化评估与调优。

### 3. 对项目的影响和潜在意义
- **对用户**：使用 VeOmni 训练 DeepSeek V4 的团队可准确获得 MFU 指标，从而诊断硬件利用率瓶颈、优化并行策略、调整批次大小等，提升训练效率。
- **对项目本身**：增强了工具链的实用性和吸引力，尤其是 DeepSeek V4 作为近期关注度高的模型，支持其性能度量可吸引更多用户采用 VeOmni 作为训练框架。
- **潜在意义**：MFU 计算通常需适配模型特有结构（如 MoE 路由、长注意力等），该提交可能隐含了对 DeepSeek V4 架构的深入理解，为后续支持更多架构奠定基础。

### 4. 值得关注的技术点
- **MFU 计算的实现方式**：需处理 DeepSeek V4 可能的多专家（MoE）层、稀疏注意力或特殊激活函数，确保计数准确。
- **与已有框架的兼容性**：需保证 MFU 计算在 VeOmni 的分布式训练环境下正确同步，不因并行策略（如张量并行、流水线并行）产生偏差。
- **性能开销**：MFU 计算本身不应显著影响训练速度，需留意实现是否轻量。

### 5. 基于项目背景，这些提交如何影响项目发展
- VeOmni 的 README 强调“扩展任意模态模型训练”，而支持 MFU 计算是量化训练效率的基石。此次提交使项目从“能训练 DeepSeek V4”提升到“能高效训练 DeepSeek V4”，符合其“Recipe Zoo”提供最佳实践的目标。
- 随着对更多流行模型（如 DeepSeek 系列）的性能分析能力增强，VeOmni 有望成为大模型训练领域的标准工具之一，吸引更多社区贡献和用户。

## 详细提交记录

### [49129dd](https://github.com/ByteDance-Seed/VeOmni/commit/49129dd1ad0aa5b2925dcedf75e59e029f2bc1d0)

- **作者**: Bin Jia
- **时间**: 2026-07-20T13:45:32Z
- **提交信息**: [perf] feat: support DeepSeek V4 MFU calculation (#944)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2511
- **最后更新**: 2026-07-20T22:36:39Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 5
- **主要提交者**: Shiqiao Gu (谷石桥), Bilang ZHANG, Yang Yong (雍洋)

## AI分析总结

### 1. 主要更新类型
- **功能新增**：支持 Cosmos3 Nano Policy（集成Isaac仿真环境与LingBot-VA）、支持 HunyuanImage-image3.0（文本到图像）、支持 Sekotalk 混合注意力机制、新增 Hy3d 平台、Flux2 平台及张量并行（TP）支持
- **性能优化**：WAN 2.1/2.2 的懒加载（lazy_load）与 CPU 卸载（cpu_offload）——减少显存占用
- **Bug修复**：修复 LTX2 AR DMD 训练阶段的问题

### 2. 关键变更点及其与项目整体方向的关系
- **HunyuanImage-image3.0 T2I** 是实现“Text-to-Image”功能的关键一步，扩展了项目从视频生成到图像生成的能力，并与已有的 T2V（文本到视频）形成互补，符合“视频+图像”的轻量生成推理框架定位。
- **Cosmos3 Nano Policy 集成**：引入**Isaac仿真环境**与**机器人操作数据集**（LingBot-VA + Libero/Robotwin），表明项目向具身智能（Embodied AI）场景延伸，支持机器人任务策略生成。
- **Sekotalk混合注意力**：可能是一种新的注意力机制改进，用于长视频或高分辨率生成，与框架追求效率的主旨一致。
- **WAN 2.1/2.2优化**：懒加载与CPU卸载直接降低推理时的显存占用，对轻量级部署场景（如边缘设备）至关重要。
- **Hy3d平台 & Flux2+TP**：新增推理平台支持（Hy3d）和 Flux2 模型的张量并行（TP），增强多卡扩展能力，推动框架支持更大模型和更高吞吐。

### 3. 对项目的影响和潜在意义
- **技术覆盖面扩大**：从纯视频生成扩展到图像生成（T2I）和机器人策略生成，使项目成为多模态生成推理的统一底座。
- **易用性与实用性提升**：Lazy load + CPU offload 让视频生成在显存受限设备上更可行，降低入门门槛。
- **生态兼容性增强**：支持多种新模型（HunyuanImage、Sekotalk、Cosmos3、Flux2），吸引更多下游用户和开发者。
- **训练与推理协同**：修复 LTX2 AR DMD 训练 bug，表明项目不仅关注推理，也关注训练流程的稳定性。

### 4. 值得关注的技术点
- **HunyuanImage-image3.0 T2I** 的并行策略：同时采用 FA2/FA3、FlashInfer、CFG并行（batch/serial/parallel）、序列并行（KV-all-gather SP、Ulysses SP）。这是当前大规模生成模型推理的热门优化方向，体现了项目对 SOTA 并行技术的整合。
- **Cosmos3与Isaac集成**：前景看好——机器人仿真→策略生成→视频验证的一条龙潜力。
- **Hy3d平台**：可能指3D或Hybrid 3D相关推理优化，需关注后续细节。
- **Sekotalk混合注意力**：若开源细节，可能为长序列视频生成提供新思路。

### 5. 基于README背景，这些提交如何影响项目发展
- 项目初始定位为“轻量视频生成推理框架”，本次更新**大幅拓宽了“轻量推理”的应用边界**：不再局限于视频生成，而是覆盖图像、机器人仿真策略生成。这有助于项目在 AI 生成内容（AIGC）与具身智能的交汇点上占据位置。
- 对 T2I 和 T2V 的统一支持，以及多种并行策略的整合，强化了框架作为**多模型推理引擎**的角色，符合 README 强调的“inference framework”特点。
- WAN 等模型的懒加载/卸载贴合“轻量”目标，而 Hy3d、Flux2+TP 则助力**可扩展性**，在轻量与高性能之间取得平衡。
- 整体来看，此次更新标志着项目从单一视频生成向**多模态、多平台、多场景的通用推理框架**演进，为后续吸引更多模型接入和社区贡献奠定了基础。

## 详细提交记录

### [0de319d](https://github.com/ModelTC/LightX2V/commit/0de319d6b40bdfcdd90311a017840c426f3debc1)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-07-20T20:51:18Z
- **提交信息**: support cosmos3 nano policy with isaac env and lingbot-va with libero/robotwin (#1243)

### [5d4720e](https://github.com/ModelTC/LightX2V/commit/5d4720e3989bfc66650b403c1f6ccf18a8bb2902)

- **作者**: Chernobyllight
- **时间**: 2026-07-20T12:11:10Z
- **提交信息**: Support HunyuanImage-image3.0 for t2i (#1270)

this lightx2v version support HunyuanImage-image3.0 for t2i, which
implements FA2/FA3, flashinfer, cfg parallel(batch, serial, parallel),
sequence parallel(kv-all-gather sp, ulysses sp)

---------

Co-authored-by: liuhongda <liuhongda@sensetime.com>

### [61570f5](https://github.com/ModelTC/LightX2V/commit/61570f5b2411d274c0c75d61fd2ce098d48edb40)

- **作者**: Bilang ZHANG
- **时间**: 2026-07-20T12:10:55Z
- **提交信息**: warmup: wan 2.1 2.2  lazy_load and cpu _offload (#1271)

### [c5229e5](https://github.com/ModelTC/LightX2V/commit/c5229e59788e1025466e7163f3c63a531070029d)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-07-20T07:55:32Z
- **提交信息**: Support Sekotalk hybrid attention and fix LTX2 AR DMD training bugs (#1269)

### [384f171](https://github.com/ModelTC/LightX2V/commit/384f17125605df0d1cad1864a6a0164cd63b8d9c)

- **作者**: Watebear
- **时间**: 2026-07-20T07:22:03Z
- **提交信息**: Hy3d platform (#1261)

Co-authored-by: wushuo1 <540295877@example.com>

### [bf91540](https://github.com/ModelTC/LightX2V/commit/bf91540f84320e15afeba97c41867aa77136dbcf)

- **作者**: Watebear
- **时间**: 2026-07-20T07:21:23Z
- **提交信息**: [platform]: flux2 & tp (#1212)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2175
- **最后更新**: 2026-07-20T12:43:54Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5988
- **最后更新**: 2026-07-20T23:15:08Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: NVJiangShao, Julian Huang, Alex Yang

## AI分析总结

### 1. 主要更新类型

- **功能新增**（2项）：MXFP4量化支持可配置缩放因子布局；MoE确定性子最终化模式。
- **Bug修复**（2项）：修复MoE专家权重输出缓存dtype错误；恢复MoE辅助函数的旧导入路径。
- **测试基础设施修复**（1项）：修复多节点通信测试中worker进程的模块导入问题。
- **重构/兼容性**（1项）：通过重新导出保持API向后兼容。

### 2. 关键变更点与项目方向的关系

| 变更 | 项目方向 | 关联说明 |
|------|----------|----------|
| MXFP4缩放因子布局可配置 (#3927) | 推理性能与精度灵活性 | 扩展量化支持，使FP4量化适配更多硬件布局（如B200），符合高性能推理场景对不同精度模式的需求。 |
| MoE确定性子最终化 (#3976) | 推理可复现性与调试 | 为CuTe DSL NVFP4 MoE增加非原子最终化路径，实现bitwise确定性输出，满足生产环境对结果一致性的要求。 |
| MoE专家权重分配类型修复 (#3925) | 正确性/可靠性 | 修正DeepSeekV3等模型在fp32路由logits下的数据错标问题，直接影响MoE推理的正确性。 |
| 恢复旧导入路径 (#4025) | 向后兼容 / 生态稳定性 | 维持下游用户（如vLLM、TGI等框架）对FlashInfer的依赖不中断，保障项目作为底层库的稳定性。 |
| 测试worker导入修复 (#4034) | 测试/CI可靠性 | 保障多节点通信测试能在CI中正确运行，提升代码质量保障流程。 |

### 3. 对项目的影响和潜在意义

- **定量化支持**：MXFP4布局可配置，使FlashInfer能适配未来不同GPU架构的块缩放要求，扩展了其在低精度推理领域的适用性。
- **MoE确定性**：为需要精确重放或数值敏感的场景（如CUDA图回放、模型调试）提供可选路径，虽引入～5-14%额外开销，但提升了工具链的可靠性。
- **Bug修复**：修复的专家权重类型错误是实际线上问题（主流DeepSeekV3使用fp32路由），直接提升了产品级MoE的正确性。
- **兼容性维护**：通过重新导出避免下游框架编译/报错，降低了升级阻力，体现了成熟开源库对生态的重视。

### 4. 值得关注的技术点

- **MXFP4缩放布局**：新增`layout_128x4`、`layout_8x4`、`layout_linear`三种布局，底层涉及CuTe DSL的scale张量形状修正（swizzled layout的padding问题）。
- **确定性最终化实现**：通过分离原子累积为两步（扩大输出空间+固定顺序 reduce），采用`moe_unpermute`并传入显式CUDA stream以支持CUDA图捕获，兼顾了性能与确定性间的权衡。
- **MoE类型bug根源**：自PR #2534起引入的`mDtypeScore`与`mDtypeOutput`混淆，导致输出buffer从路由logits dtype继承而非固定bf16——这是一个持续性技术债务的修复。
- **测试基础设施**：`mp.spawn`与`--import-mode=importlib`的兼容性问题，通过将项目根目录加入`sys.path`解决，属于Python多进程测试常见陷阱。

### 5. 基于项目背景，这些提交如何影响项目发展

根据README，FlashInfer定位为**高性能推理GPU内核**，核心用户是LLM推理框架（如vLLM、TGI、TensorRT-LLM）。这些提交推动项目向**更稳定、更灵活、更可调试**的方向发展：
- **稳定性**：Mo

## 详细提交记录

### [3f550f1](https://github.com/flashinfer-ai/flashinfer/commit/3f550f15812f0bc9b7cdd014210bdbc86d9aba9d)

- **作者**: Schwinn Saereesitthipitak
- **时间**: 2026-07-20T23:14:56Z
- **提交信息**: test(comm): make checkpoint worker importable (#4034)

## Description

PR #3968 added `tests/comm/test_trtllm_allreduce_checkpoint.py` to the
multi-node communication test job. That exposed a test-environment
failure before any worker or kernel code runs:

```text
ModuleNotFoundError: No module named 'tests'
```

`pytest.ini` uses `--import-mode=importlib`, and
`torch.multiprocessing.spawn` serializes the worker as
`tests.comm.test_trtllm_allreduce_checkpoint._run_worker`. Fresh Python
interpreters must be able to import that qualified module while
unpickling the process target.

Add the repository root to the parent process's `sys.path` immediately
before `mp.spawn`. Python copies that path into spawn preparation data
and restores it in each child before unpickling the worker. This follows
the existing pattern in `tests/comm/test_all_gather_matmul.py`.

This is a test harness/environment fix only; worker, checkpoint, graph
replay, all-reduce, and kernel behavior are unchanged.

## Related Issues

- Follow-up to #3968, which enabled this test in multi-node CI.
- #3966's missing-coverage request was addressed by #3968 and can be
closed.

## Tests

Passed:

- `git diff --check`
- `pre-commit run --files
tests/comm/test_trtllm_allreduce_checkpoint.py`
- Python syntax compilation
- Repository-root/path assertion (`parents[2]` resolves to the checkout
root containing `tests/__init__.py`)
- Standard-library `multiprocessing` spawn smoke test: a fresh child
successfully imported a module-qualified `tests.comm.*` target after the
parent inserted the temporary repo root into `sys.path`

The full two-GPU checkpoint replay test was not run locally because the
available Python environment does not have Torch or pytest installed.
The multi-node CI job enabled by #3968 provides the end-to-end
validation.

## Checklist

- [x] The change is limited to the affected test harness.
- [x] Pre-commit checks pass for the changed file.
- [x] The commit includes a DCO sign-off.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Improved multiprocessing test reliability by ensuring child processes
can correctly locate and import the test package during graph replay
validation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Schwinn Saereesitthipitak <schwinns@nvidia.com>

### [37d99a1](https://github.com/flashinfer-ai/flashinfer/commit/37d99a16fb131ffc89b198616dbecafeaaaf112a)

- **作者**: Julian Huang
- **时间**: 2026-07-20T23:14:03Z
- **提交信息**: feat(quantization): support configurable scale-factor layouts for MXFP4 (#3927)

## 📌 Description

This PR extends MXFP4 scale-factor layout support in three areas:

1. **Configurable MXFP4 quantization layout**  
`mxfp4_quantize` now accepts an optional `sfLayout` argument and
supports `layout_128x4`, `layout_8x4`, and `layout_linear`. The default
remains `SfLayout.layout_128x4`, preserving existing behavior.
`mxfp4_dequantize` accepts the corresponding layout for round-trip
conversion.

2. **8x4 dequantization support**  
`E2M1AndUFP8SFScaleToFloatV2` now supports `SfLayout.layout_8x4` with
the correct scale-factor index mapping and scale-buffer size validation.

3. **CuTe-DSL scale output shape fix**  
Fix the MXFP4 scale tensor reshape for swizzled layouts so that it
preserves the padded physical shape `(padded_rows,
padded_scale_columns)`. This avoids incorrect output shapes when the
number of scale columns requires 4-column padding.


## 🔍 Related Issues

N/A

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used my preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run `pre-commit run --all-files` and fixed all reported
issues.

## 🧪 Tests

Validated on NVIDIA B200 (SM100):

- Full `tests/utils/test_fp4_quantize.py` passed on both the baseline
and this PR (`10,300 passed` vs. `10,303 passed`).
- Baseline/PR benchmark comparison showed no performance regression;
observed differences were within expected run-to-run variance.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added support for multiple FP4 scale-factor layouts, including
`128x4`, `8x4`, and `linear`.
* Quantization and dequantization now take an explicit scale-factor
layout option.
  * Benchmarks now report and validate the selected layout.
* **Bug Fixes**
* Improved FP4 quantize/dequantize correctness via layout-aware
round-trip verification and backend consistency checks.
  * Enhanced scale-factor shape/index validation for supported layouts.
* **Documentation**
* Updated command-line help text and benchmark documentation to
accurately describe FP4 layout options.
* **Tests**
* Added coverage for layout-specific MXFP4 quantize/dequantize
round-trips across supported devices.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [2e1742a](https://github.com/flashinfer-ai/flashinfer/commit/2e1742a89f65819e800c2ef72e98372bb2ee8e94)

- **作者**: Alex Yang
- **时间**: 2026-07-20T23:00:48Z
- **提交信息**: fix(moe): allocate trtllm-gen expert_weights as bf16 in all launchers (#3925)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #3595 / #3644 (which fixed the FP4 op). The trtllm-gen
routing kernel **always** writes expert weights in bfloat16 —
`routingData.mDtypeOutput` is hard-set to `Bfloat16` in every branch of
`Routing::Runner::run` (`csrc/trtllm_fused_moe_runner.cu`), independent
of the `routing_logits` dtype.

But four launchers in `csrc/trtllm_fused_moe_kernel_launcher.cu`
allocated the `expert_weights` output buffer from the **routing-logits**
dtype (`dl_float32` when logits are fp32):

- `Bf16MoeLauncher`
- `Fp8PerTensorLauncher`
- `Fp8BlockScaleLauncher`
- `MxInt4BlockScaleLauncher`

The base `run()` returns that buffer verbatim on `do_finalize=false`,
and the Python wrappers hand it straight back via `torch.from_dlpack`.
So with fp32 routing logits (the conventional DeepSeekV3 case) +
`do_finalize=false`, the caller receives **bf16 data mislabeled as
fp32** and reads garbage — the same corruption #3644 fixed for FP4.

**Fix:** allocate `expert_weights` as `bfloat16` unconditionally to
match the kernel's actual output. No-op for the common bf16-logits path
and for `do_finalize=true` (internal workspace read back as bf16, just
avoids a 2× over-allocation). Also removes the now-dead `mDtypeScore`
member (write-only after this change).

**Why the fp32 branch existed:** a latent mismatch since #2534, which
added a configurable score dtype (`mDtypeScore`) to support fp32 routing
*logits*. But the expert-weights *output* (`mDtypeExpW`, later renamed
`mDtypeOutput`) was always bf16 in that same PR — the launcher
mistakenly sized/labeled the *output* buffer from `mDtypeScore` (an
input/score knob). **fp32 logits remain fully supported** — they still
flow to the kernel via `mRoutingLogitsDtype`/`mDtypeInput`; only the
output-buffer dtype is corrected.

## 🔍 Related Issues

- Follow-up to #3595 / #3644 (same bug class, FP4 op)
- Latent mismatch originated in #2534

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

Validation via GitHub CI (SM100-class trtllm-gen kernels). Suggested
follow-up: a regression test that runs each of the four ops with fp32
DeepSeekV3 routing logits + `do_finalize=False` and asserts the returned
`expert_weights.dtype == torch.bfloat16` (mirrors the FP4 test added in
#3644).

## Reviewer Notes

Focus areas: confirm the Llama4 `token_scales` aliasing of this buffer
is also fine as bf16, and that no caller depended on the (incorrect)
fp32 labeling.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed routing output and expert weight buffers to consistently use the
correct bfloat16 format.
* Prevented potential data mislabeling when routing results are returned
before finalization.
* Improved consistency across supported Mixture-of-Experts execution
modes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [ce29c1a](https://github.com/flashinfer-ai/flashinfer/commit/ce29c1a58dedb22424b2cbe123e7c244aa48544f)

- **作者**: Ziang Li
- **时间**: 2026-07-20T21:01:13Z
- **提交信息**: feat(moe): add deterministic CuTe DSL NVFP4 finalize mode (#3976)

<!-- .github/pull_request_template.md -->

## 📌 Description

@humansand

Add an optional bitwise-deterministic finalize mode to CuTe DSL NVFP4
MoE for eager execution and CUDA graph replay.

The existing GEMM2 fused finalize atomically scatters routed expert
outputs into each token row. Its accumulation order can vary when a
token has multiple local routes, causing bitwise output drift across
identical launches.

This PR mirrors the `cutlass_fused_moe` contract:

- `use_fused_finalize=True` remains the default for the existing atomic
fused path and best performance.
- `use_fused_finalize=False` makes GEMM2 write each active route to a
unique expanded `(token, top-k slot)` row, then uses `moe_unpermute` to
apply router weights and reduce top-k routes in fixed order.
- `bench_moe_deepseek.py --functional-api --no-fused-finalize` selects
the deterministic path for matched performance comparisons.
- `moe_unpermute` receives PyTorch's current CUDA stream explicitly so
the reduction is captured and replayed by CUDA graphs.
- The unified MoE fuzz contract continues to classify the default CuTe
DSL atomic path as nondeterministic; the existing CUDA graph replay test
now exercises both finalize modes.

The existing CuTe DSL CUDA graph replay matrix now runs both finalize
modes: the fused path retains its FP4 tolerance, while the deterministic
path requires bitwise-identical replay output.

## 🔍 Related Issues

- Follow-up to #3645.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
[pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated on NVIDIA B200 with CUDA 13:

```bash
FLASHINFER_DISABLE_VERSION_CHECK=1 python3 -m pytest -s \
  tests/moe/test_cute_dsl_fused_moe.py::TestCuteDslMoEWrapper::test_wrapper_accuracy \
  tests/moe/test_cute_dsl_fused_moe.py::TestCuteDslMoEWrapper::test_wrapper_cuda_graph \
  tests/moe/test_cute_dsl_fused_moe.py::TestExpertParallelism::test_functional_with_ep
# 76 complete matrix cases passed as part of an 81-case B200 run

CUDA_VISIBLE_DEVICES=0 FLASHINFER_DISABLE_VERSION_CHECK=1 python3 -m pytest -q \
  tests/moe/test_cute_dsl_fused_moe.py \
  -k test_deterministic_finalize_numerical_accuracy
# 2 passed in 20.25s

pre-commit run --all-files
# Passed
```

The 76-case regression matrix comprises the complete 48-case wrapper
accuracy matrix, complete
24-case CUDA graph matrix, and all four functional EP combinations. The
original
144-case functional numerical matrix remains unchanged for the default
fused
finalize path. Deterministic-finalize numerical coverage is isolated to
two
representative cases spanning both activations, both activation-scaling
modes,
and small and large top-k shapes; both passed on B200.

## 📊 Benchmark

Measured on NVIDIA B200 with CUDA 13, CUDA graphs enabled, per-token
activation scaling, and 4over6 disabled. Timing used CUPTI with
`cupti-python==13.3.0`, `nvidia-cuda-cupti==13.3.75`, and
`cuda-python==13.2.0`. A direct `bench_gpu_time(..., enable_cupti=True)`
smoke test returned five samples with a 0.001024 ms median, and neither
benchmark log reported a missing-CUPTI or timing-fallback warning.

```bash
# Atomic fused finalize (default)
python3 benchmarks/bench_moe_deepseek.py \
  --functional-api \
  --use-per-token-activation \
  --num-tokens 1,2,4,8,16,32,64,128,256,512,1024,2048,4096

# Deterministic two-stage finalize
python3 benchmarks/bench_moe_deepseek.py \
  --functional-api \
  --use-per-token-activation \
  --no-fused-finalize \
  --num-tokens 1,2,4,8,16,32,64,128,256,512,1024,2048,4096
```

| Tokens | Atomic fused (ms) | Deterministic (ms) | Deterministic
overhead |
|---:|---:|---:|---:|
| 1 | 0.064 | 0.073 | +14.1% |
| 2 | 0.100 | 0.112 | +12.0% |
| 4 | 0.156 | 0.174 | +11.5% |
| 8 | 0.263 | 0.282 | +7.2% |
| 16 | 0.444 | 0.465 | +4.7% |
| 32 | 0.693 | 0.715 | +3.2% |
| 64 | 0.933 | 0.953 | +2.1% |
| 128 | 1.023 | 1.045 | +2.2% |
| 256 | 1.062 | 1.078 | +1.5% |
| 512 | 1.073 | 1.088 | +1.4% |
| 1024 | 1.091 | 1.129 | +3.5% |
| 2048 | 1.138 | 1.200 | +5.4% |
| 4096 | 1.520 | 1.663 | +9.4% |

Geometric-mean deterministic overhead is **5.94%** across the full
sweep, **7.03%** for 1-128 tokens, and **4.21%** for 256-4096 tokens.
Values are calculated from the benchmark's printed millisecond results.

## Reviewer Notes

Please focus on the deterministic GEMM2 output layout and the
`input_is_expanded` mode added to `moe_unpermute`. The deterministic
`use_fused_finalize=False` path adds an expanded-route workspace and a
separate fixed-order reduction kernel; the atomic fused finalize remains
the default, matching `cutlass_fused_moe`.

### Why normalized `activation_type` uses a local `activation` binding

`normalize_cute_dsl_moe_activation_type` returns an `ActivationType`,
while the existing API parameter is annotated as `int`. Reassigning the
normalized value back to `activation_type` leaves mypy treating it as an
`int`, so subsequent `.value` and `.name` accesses fail type checking.
The local `activation` binding preserves the normalized enum type
without adding casts, type ignores, or unrelated public annotation
changes. This is typing-only and does not change runtime behavior.

### Why `moe_unpermute` receives an explicit CUDA stream

The deterministic finalize calls `moe_unpermute` from PyTorch and may
run inside a non-default stream or CUDA graph capture. The binding
function `get_current_stream()` resolves through `TVMFFIEnvGetStream`,
which does not track `torch.cuda.current_stream()`. Python therefore
passes the current PyTorch stream pointer explicitly so the reduction is
ordered after GEMM2 and captured in the same CUDA graph. All four
dtype-specialized `moe_unpermute` bindings carry the argument because
Python selects among them from the input and routing-scale dtypes. A
zero pointer retains the existing TVM FFI stream fallback. This follows
the established `moe_sort` and `moe_output_memset_inplace` pattern.

### Why this CuTe DSL change touches CUDA C++

The CuTe DSL MoE pipeline is hybrid: GEMM1 and GEMM2 are CuTe DSL
kernels, while routing and finalize utilities such as `moe_sort`,
`moe_permute`, and `moe_unpermute` are CUDA C++ kernels loaded through
the `moe_utils` JIT module. The deterministic path calls the existing
CUDA C++ `moeUnpermute` kernel after the CuTe DSL GEMM2 completes; the
atomic fused path does not call it.

Previously, `moeUnpermute` assumed its input rows were in
expert-permuted order and resolved every `(token, top-k slot)` through
`expanded_idx_to_permuted_idx`. The deterministic GEMM2 path instead
writes each route exactly once into a compact `[num_tokens * top_k,
hidden_size]` buffer in expanded `(token, top-k slot)` order.
`input_is_expanded=True` changes only the source-row selection to use
that expanded index directly. The mapping is still checked so masked or
non-local EP routes, represented by a negative permuted index, are
skipped.

Because this utility crosses the Python/JIT boundary, the new layout
mode must be threaded through
`flashinfer/fused_moe/cute_dsl/moe_utils.py`,
`csrc/moe_utils_binding.cu`, the C++ declaration, and the CUDA kernel
launcher. Keeping the old interface would require either a larger
expert-padded output workspace or a duplicate reduction kernel.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added `use_fused_finalize` option to switch MoE finalization between
fused (default) and deterministic modes, including the resulting output
layout.
* Added `input_is_expanded` support for MoE unpermutation to correctly
handle expanded vs unexpanded token layouts.
* Improved MoE unpermutation execution by honoring an explicit CUDA
stream.
* Added a benchmark CLI flag to compare fused vs deterministic finalize
modes.
* **Bug Fixes**
* Normalized activation handling consistently across MoE execution
paths.
* **Tests**
* Expanded accuracy and CUDA-graph coverage for both finalize modes,
with replay checks adjusted per mode.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c83607a](https://github.com/flashinfer-ai/flashinfer/commit/c83607a9bdaaff51413a1847df401b63a0481c99)

- **作者**: NVJiangShao
- **时间**: 2026-07-20T12:50:41Z
- **提交信息**: fix(moe): restore legacy fused_moe.core imports for interleave helpers (#4025)

## 📌 Description

PR #3738 moved the following helper APIs from
`flashinfer.fused_moe.core` to
`flashinfer.fused_moe.prepare`:

- `interleave_moe_scales_for_sm90_mixed_gemm`
- `interleave_moe_weights_for_sm90_mixed_gemm`

That module-path change breaks downstream users that still import these
public
helpers directly from `flashinfer.fused_moe.core`.

This PR restores backward compatibility by re-exporting both helpers
from
`flashinfer.fused_moe.core`, while keeping their implementations and
canonical
definitions in `flashinfer.fused_moe.prepare`. It does not change their
runtime
or CUDA behavior.

## 🔍 Related Issues

Fixes #4022.

Follow-up to #3738.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request,
please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used
  my preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed
  any reported issues.

> If you are unsure about how to set up `pre-commit`, see the
> [pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] `pre-commit run --all-files`
- [ ] Verify the legacy imports on H20:

  ```python
  from flashinfer.fused_moe.core import (
      interleave_moe_scales_for_sm90_mixed_gemm,
      interleave_moe_weights_for_sm90_mixed_gemm,
  )
  ```

- [ ] Run a representative Hopper mixed-input MoE correctness test on
H20.

## Reviewer Notes

- The explicit same-name aliases are intentional: they expose the
imported
  symbols as public module attributes and satisfy static linting.
- `prepare.py` remains the canonical implementation location; this PR
only
  restores the previous import path for compatibility.
- `prepare.py` does not import `core.py` during module initialization,
so these
  re-exports do not introduce an import-time circular dependency.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Refactor**
* Kept backward compatibility for existing callers of mixture-of-experts
weight and scale utilities.
* Consolidated where these utilities are sourced so they remain
available under the same public names and behave the same for current
users.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Jiang Shao <91270701+StudyingShao@users.noreply.github.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3863
- **最后更新**: 2026-07-20T22:59:17Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: William Lin, Adriel Fung

## AI分析总结

### 昨日更新要点总结（基于 `hao-ai-lab/FastVideo` 提交记录）

#### 1. 主要更新类型
- **功能新增**：1 项（LTX-2 和 LTX-2.3 微调支持）
- **性能优化**：1 项（LTX2 的 per-block torch.compile 与持久缓存）
- **CI/流程改进**：1 项（fork-PR 检出策略适配）

#### 2. 关键变更点与项目方向关联
| 提交 | 变更内容 | 与项目方向的关系 |
|------|----------|------------------|
| `[perf]` (521dee0) | 为 LTX2 模型启用逐块 `torch.compile` 并添加持久化缓存 | 针对视频生成模型推理/训练加速，直接提升 LTX2 的执行效率，符合 FastVideo “快速视频生成” 的核心目标 |
| `[ci]` (2294192) | 适配 GitHub Actions `actions/checkout` 安全变更，改用 fork-PR head 检出 | 保证开源协作流程稳定，支持社区 PR 贡献，增强项目可维护性 |
| `[feat]` (65f3b94) | 在模块化训练器中增加 LTX-2 和 LTX-2.3 的 fine-tuning 支持 | 扩展支持更多视频模型变体，强化 “模块化训练器” 的通用性，降低用户微调门槛 |

#### 3. 对项目的影响与潜在意义
- **性能提升**：`torch.compile` 与持久缓存可显著减少 LTX2 的编译开销，对迭代式训练和批量推理有实际加速效果，增强项目在高效视频生成领域的竞争力。
- **模型生态扩展**：新增 LTX-2.3 微调能力，填补了之前版本可能缺失的模型变体支持，吸引更多使用该系列模型的用户。
- **协作稳定性**：CI 修复确保第三方贡献者能正常提交 PR，避免因 GitHub 安全策略变更导致的构建阻塞，保障开源社区活跃度。

#### 4. 值得关注的技术点
- **per-block compile**：细粒度的编译策略（而非整个模型）可减少 JIT 编译内存占用，搭配持久缓存避免重复编译，是深度学习模型部署的常见优化手段。
- **模块化训练器结构**：提交 (65f3b94) 暗示项目采用可插拔的训练器设计，便于快速集成新模型，对后续扩展其他视频模型（如 Stable Video Diffusion、CogVideoX 等）有参考价值。

#### 5. 结合项目背景看发展影响
- FastVideo 定位于 **“快速视频生成”** 工具链，README 强调文档与快速开始入口。本次更新：
  - **性能层面**：强化 LTX2 这一主力模型的运行效率，直接响应用户对生成速度的硬需求。
  - **能力层面**：通过模块化训练器统一微调流程，降低用户从推理到定制训练的学习成本，完善从使用到调优的全链路支持。
  - **社区层面**：CI 改进保障协作顺畅，有助于吸引更多开发者共同改进模型支持，推动项目向多模型、高性能的通用视频生成框架演进。

> 总体而言，昨日更新聚焦于 **“让核心模型跑得更快、让更多模型能被微调、让协作更顺畅”**，精准服务于 FastVideo 的高效与易用定位。

## 详细提交记录

### [521dee0](https://github.com/hao-ai-lab/FastVideo/commit/521dee0e82a200272a064b12cff1140f24c577a6)

- **作者**: Adriel Fung
- **时间**: 2026-07-20T22:59:13Z
- **提交信息**: [perf]: enable per-block torch.compile for LTX2 with persistent cache (#1602)

Co-authored-by: SolitaryThinker <wlsaidhi@gmail.com>

### [2294192](https://github.com/hao-ai-lab/FastVideo/commit/229419208e5b90b69f5ffa0ea3d6e718d0a50112)

- **作者**: William Lin
- **时间**: 2026-07-20T20:12:22Z
- **提交信息**: [ci]: opt in to fork-PR head checkout after actions/checkout guard change (#1625)

### [65f3b94](https://github.com/hao-ai-lab/FastVideo/commit/65f3b946b929495cd38ecbb87e3ef726ed05587f)

- **作者**: William Lin
- **时间**: 2026-07-20T18:58:39Z
- **提交信息**: [feat] Add LTX-2 and LTX-2.3 fine-tuning to the modular trainer (#1624)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34118
- **最后更新**: 2026-07-20T23:16:43Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 4
- **主要提交者**: Atharva Joshi, Sayak Paul, Wang, Yi

## AI分析总结

根据仓库 `huggingface/diffusers` 的昨日提交记录，结合项目背景（专注于扩散模型实现、训练与推理，涵盖 Stable Diffusion、Cosmos、WAN 动画等多种管线），分析如下：

---

### 1. 主要更新类型
- **Bug 修复**：`Cosmos3 Edge generator K normalization`（#14246）、`fix cosmos3 tests`（#14229）、`fix test_pag_sdxl`（#13892）
- **代码清理 / 移除警告**：`remove experimental api warning from lora modules`（#14248）
- **测试架构重构**：`refactor wan animate pipeline tests to the new mixin structure`（#14239）

---

### 2. 关键变更点及其与项目整体方向的关系
| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| #14246 | 修复 Cosmos3 Edge 生成器中 K 归一化的计算错误 | 提升 Cosmos3 管线输出的正确性与一致性，符合项目“支持多种高质量扩散模型”的目标 |
| #14229 | 修复 Cosmos3 相关测试，确保测试通过 | 维护测试可靠性，对应项目对模型稳定性的重视 |
| #14248 | 移除 LoRA 模块中的实验性 API 警告 | 代码清理，表明 LoRA 功能已成熟，不再标记为实验性；促进用户信任，符合项目“生产就绪”演进方向 |
| #13892 | 修复 StableDiffusionXL **PAG**（*猜测为 Perturbed Attention Guidance*）管线集成测试 | 保证 SDXL 变体管线的兼容性与回归测试，支持社区常用功能 |
| #14239 | 重构 WAN 动画管线测试，采用新的 `mixin` 结构 | 统一测试框架，提升测试可维护性与扩展性，为后续更多动画管线（如 Video Diffusion）奠定基础 |

---

### 3. 对项目的影响和潜在意义
- **稳定性提升**：多组 Bug 修复直接减少了用户在使用 Cosmos3、SDXL-PAG 时可能遇到的错误。
- **技术债务减少**：移除实验性警告、重构测试框架降低了未来维护成本，使开发者更容易添加新功能。
- **社区友好度**：LoRA 警告移除暗示该功能已稳定，鼓励更多人尝试微调；测试重构减少了新贡献者写测试的门槛。
- **模型生态扩展**：WAN 动画测试重构为多模态（视频/图像）管线提供了标准化测试模式，助推项目从“纯图像扩散”向“图像+视频”混合能力迈进。

---

### 4. 值得关注的技术点
- **Cosmos3 K 归一化**：修复涉及生成器（可能指 `cosine_schedule` 或自定义归一化逻辑），需关注其数学实现是否影响生成质量。
- **LoRA 实验性标记移除**：意味着 LoRA 模块的 API 已冻结，未来不会破坏性变更，是生产级使用的信号。
- **测试 mixin 结构**：WAN 动画测试迁移到 mixin 体现了项目中测试抽象层的演进（类似 `PipelineTesterMixin`），便于复用断言与配置。
- **PAG 修复**：StableDiffusionXLPAGPipeline 是近期流行的注意力引导变体，修复集成测试保证了该功能的可用性。

---

### 5. 结合项目背景对发展的影响
- **强化多模型对齐**：同时修复 Cosmos3、SDXL-PAG、WAN 动画等问题，显示项目正努力让不同管线在同一代码基下保持高质量。
- **走向生产化**：移除实验警告、规范测试架构，标志着 diffusers 从快速迭代转向稳定发布阶段。
- **为视频扩散铺路**：WAN 动画测试重构是项目从图像到视频扩散的自然延伸，符合 HuggingFace 在生成式 AI 全模态生态的布局。
- **社区贡献友好度**：测试重构使用标准化 mixin，方便外部贡献者为新管线编写测试，符合项目社区驱动的特点。

---

**总结**：昨日更新以 Bug 修复和代码质量提升为主，无新功能引入，但通过修复关键管线错误、清理技术

## 详细提交记录

### [86e6dac](https://github.com/huggingface/diffusers/commit/86e6dac5360703ddf09fe250db50be667eb93662)

- **作者**: Atharva Joshi
- **时间**: 2026-07-20T17:16:30Z
- **提交信息**: Fix Cosmos3 Edge generator K normalization (#14246)

### [994a92d](https://github.com/huggingface/diffusers/commit/994a92dedd04fe8871d569e63e35044a84615613)

- **作者**: Sayak Paul
- **时间**: 2026-07-20T16:57:46Z
- **提交信息**: [tests] fix cosmos3 tests (#14229)

fix cosmos3 tests

### [e97c271](https://github.com/huggingface/diffusers/commit/e97c271b21a50686d65ad887deef19a0f4e15042)

- **作者**: Sayak Paul
- **时间**: 2026-07-20T12:55:37Z
- **提交信息**: [chore] remove experimental api warning from lora modules. (#14248)

remove experimental api warning from lora modules.

### [5512a2b](https://github.com/huggingface/diffusers/commit/5512a2be744718b9a3f520db3812b17e064d6ea6)

- **作者**: Wang, Yi
- **时间**: 2026-07-20T12:29:13Z
- **提交信息**: fix test_pag_sdxl::StableDiffusionXLPAGPipelineIntegrationTests (#13892)

Signed-off-by: Wang, Yi <yi.a.wang@intel.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [5cfbf05](https://github.com/huggingface/diffusers/commit/5cfbf05464d7e1a89555fbc69d705d2f9766ff6f)

- **作者**: Akshan Krithick
- **时间**: 2026-07-20T12:11:25Z
- **提交信息**: refactor wan animate pipeline tests to the new mixin structure (#14239)

* refactor wan animate pipeline tests to the new mixin structure

* assert against real value slice in wan animate test_inference

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 425
- **最后更新**: 2026-07-20T03:25:45Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12717
- **最后更新**: 2026-07-20T12:44:15Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30552
- **最后更新**: 2026-07-20T23:17:43Z

## 提交统计

- **昨日提交总数**: 23
- **提交者数量**: 19
- **主要提交者**: Yuan Luo, ashwini rathi, Liangsheng Yin

## AI分析总结

分析生成失败

## 详细提交记录

### [8905cbd](https://github.com/sgl-project/sglang/commit/8905cbd42f4a27dbecad6487cd3904278756fef8)

- **作者**: zijiexia
- **时间**: 2026-07-20T23:14:12Z
- **提交信息**: Fix MiniMax-M3 crash on ROCm by making its override fields resolvable (#31837)

### [0a2d3ca](https://github.com/sgl-project/sglang/commit/0a2d3ca0719f1655572f5ccebcec42f679d7b282)

- **作者**: zijiexia
- **时间**: 2026-07-20T22:43:35Z
- **提交信息**: [cookbook] Inkling: add measured accuracy numbers to benchmark cards (#31823)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [a82ead5](https://github.com/sgl-project/sglang/commit/a82ead53bde1dfae0ab485331982f08b5c132b56)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-20T22:21:00Z
- **提交信息**: Make Q contiguous before TRT-LLM MHA decode (#31667)

### [7fe9ad2](https://github.com/sgl-project/sglang/commit/7fe9ad25ac3cc777b304e4491780b8a8f38a3f3f)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-20T22:07:55Z
- **提交信息**: [Spec] Extract DFlash compact draft-cache rebuild helpers (#31677)

### [91b210f](https://github.com/sgl-project/sglang/commit/91b210f7b06cf28ccd3273633835cdc6ddfe9be5)

- **作者**: Kaixi
- **时间**: 2026-07-20T20:45:23Z
- **提交信息**: [GLM5][MoE] perf: Write FlashInfer TRT-LLM MoE output directly (#28416)

### [e856eae](https://github.com/sgl-project/sglang/commit/e856eae921980e58a38975fac36b0eb07e55f9b5)

- **作者**: wenxuewuhd
- **时间**: 2026-07-20T19:46:17Z
- **提交信息**: use sgl_kernel_npu rmsrope accelerate llada2 (#27127)

Co-authored-by: gemini-code-assist[bot] <176961590+gemini-code-assist[bot]@users.noreply.github.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [ff6c755](https://github.com/sgl-project/sglang/commit/ff6c755952bba2ccc6018549d8f402a6642b9d3c)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-20T19:44:27Z
- **提交信息**: [Refactor] Unify logprob results into a single `LogprobResult` and rename chunk env vars (#31733)

### [e149cdb](https://github.com/sgl-project/sglang/commit/e149cdb337503673dd5cc5e3157f4878843691f5)

- **作者**: Douglas Yang
- **时间**: 2026-07-20T19:16:47Z
- **提交信息**: docs(cookbook): revert MiniMax-M3 to dev image (model not yet in a release) (#31819)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [54aaedd](https://github.com/sgl-project/sglang/commit/54aaedd76d45ff609857ea598d3d2c78bd9c78a7)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-20T19:14:21Z
- **提交信息**: Clean up prefill CUDA graph runner (#31654)

### [4e8eb14](https://github.com/sgl-project/sglang/commit/4e8eb1457bd54560fa88ba1443b6b9b55cd3fa16)

- **作者**: Rockdu
- **时间**: 2026-07-20T18:32:02Z
- **提交信息**: [Diffusion] msgpack raw-bytes transport (drop base64/JSON) (#31565)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [5ab3d90](https://github.com/sgl-project/sglang/commit/5ab3d90b8115b85e7464a1b448287411c71968c1)

- **作者**: Ke Bao
- **时间**: 2026-07-20T15:23:15Z
- **提交信息**: Fix dropped Inkling reasoning at stream end (#31787)

### [7fc545b](https://github.com/sgl-project/sglang/commit/7fc545b6497f1f1ea20d6f37485cbdb8f7d31cc7)

- **作者**: Ke Bao
- **时间**: 2026-07-20T15:22:43Z
- **提交信息**: Align reasoning_effort schema across chat, tokenize, and responses (#31784)

### [b6be150](https://github.com/sgl-project/sglang/commit/b6be150798ec65e59a2117ab704720ae332f1477)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-20T15:16:10Z
- **提交信息**: [AMD] Split ROCm 7.2 Stage-B large 1-GPU tests into three partitions (#31792)

Co-authored-by: bingxche <bingxche@amd.com>

### [c41c573](https://github.com/sgl-project/sglang/commit/c41c573ce9ed2053d38aa711582e19a67a5e9755)

- **作者**: Yuan Luo
- **时间**: 2026-07-20T14:06:30Z
- **提交信息**: [GDN] Support ReplaySSM Ring Spec-Verify (#28695)

Co-authored-by: luoyuan.luo <luoyuan.luo@antgroup.com>
Co-authored-by: vincentzed <207368749+vincentzed@users.noreply.github.com>

### [d1c2a1d](https://github.com/sgl-project/sglang/commit/d1c2a1de080cb0aa55b95085c5cafef2f9bdc93d)

- **作者**: monkeyLoveding
- **时间**: 2026-07-20T14:01:28Z
- **提交信息**: [NPU] memfabric-zbal update (#31777)

### [370f454](https://github.com/sgl-project/sglang/commit/370f454e3d901853306fa72bbdc52f9f3bb2c4b1)

- **作者**: heziiop
- **时间**: 2026-07-20T12:32:57Z
- **提交信息**: [NPU] fix modelslim quant tensor name (#31456)

### [3d82dac](https://github.com/sgl-project/sglang/commit/3d82dacd580a2313064dd4efce482b9c51ee8698)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-20T09:11:59Z
- **提交信息**: Bump CuTe DSL to 4.6.0 (#31714)

### [97e0647](https://github.com/sgl-project/sglang/commit/97e0647bdc497edc015957c2de5284094775475b)

- **作者**: amote-i
- **时间**: 2026-07-20T08:31:27Z
- **提交信息**: [NPU] [DOC] Fix issues about npu docs found by aidd (#31302)

### [fce5c75](https://github.com/sgl-project/sglang/commit/fce5c75a308413b521f2aa0edac9dde83494eb26)

- **作者**: Jinyan Yi
- **时间**: 2026-07-20T08:20:33Z
- **提交信息**: [NPU] Fix vit graph tnd cu seqlens (#31701)

### [3f48245](https://github.com/sgl-project/sglang/commit/3f4824508039575fb8e6918f65624aa01f0fd384)

- **作者**: Alison Shao
- **时间**: 2026-07-20T08:19:24Z
- **提交信息**: [CI] Temporarily disable GB300 jobs (runner availability) (#31764)

### [fafa302](https://github.com/sgl-project/sglang/commit/fafa302e414750884f696dac5efbfb95825d9eb3)

- **作者**: ashwini rathi
- **时间**: 2026-07-20T08:15:50Z
- **提交信息**: [XPU][NIGHTLY] Add 8 XPU nightly tests, enable 1-gpu suite (#30246)

Co-authored-by: arathi-hlab <arathi-hlab@users.noreply.github.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [50c1187](https://github.com/sgl-project/sglang/commit/50c118704a0ec53eee7984dd51ff7dc2be922af5)

- **作者**: kangwangamd
- **时间**: 2026-07-20T07:50:17Z
- **提交信息**: [diffusion] disagg: handle numpy arrays in cross-role transfer field extraction (#31325)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [9668d9e](https://github.com/sgl-project/sglang/commit/9668d9ea72ae9385c96f8dc1202df38222b98208)

- **作者**: Baizhou Zhang
- **时间**: 2026-07-20T07:48:04Z
- **提交信息**: Support GPT-OSS zigzag CP with TRTLLM-MHA (#31732)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1234
- **最后更新**: 2026-07-20T09:15:03Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 86734
- **最后更新**: 2026-07-20T23:14:25Z

## 提交统计

- **昨日提交总数**: 29
- **提交者数量**: 26
- **主要提交者**: aoshen02, coltonottley, hcl

## AI分析总结

以下是根据提供的Git提交记录，对昨日更新的总结与分析：

---

### 1. 主要更新类型
- **Bug修复**（最多，约10+条）：涵盖推测解码、KV offload、量化缓存、XP

## 详细提交记录

### [58b2012](https://github.com/vllm-project/vllm/commit/58b2012aa26f2b85560ecd6988c8fa2a773804c1)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-20T23:08:11Z
- **提交信息**: [copy of #45208] CuMem slept-L1 fragmentation accounting (#49208)

Signed-off-by: haosdent <haosdent@gmail.com>
Signed-off-by: Justin Wood <justin.m.wood@me.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: haosdent <haosdent@gmail.com>
Co-authored-by: Claude Opus 4.7 (1M context) <noreply@anthropic.com>
Co-authored-by: Justin Wood <jwood@me.com>

### [b7c20d0](https://github.com/vllm-project/vllm/commit/b7c20d0cfa822c011e8d24ce63a2e09bb1cef431)

- **作者**: Ning Xie
- **时间**: 2026-07-20T22:15:28Z
- **提交信息**: [chore] adjust logo be more friendly to white background terminal (#48938)

Signed-off-by: Andy Xie <andy.xning@gmail.com>

### [a2b1f9f](https://github.com/vllm-project/vllm/commit/a2b1f9fc3be709c6780a45af20fa16ac824269a9)

- **作者**: TJian
- **时间**: 2026-07-20T22:12:38Z
- **提交信息**: [ROCm] [Release] [Bugfix] Fix the per commit wheel release pipeline. (#49245)

Signed-off-by: tjtanaa <tunjian.tan@embeddedllm.com>

### [642076d](https://github.com/vllm-project/vllm/commit/642076d26c98aab899a6cc3dc948856d38c7551b)

- **作者**: Fynn Schmitt-Ulms
- **时间**: 2026-07-20T21:52:43Z
- **提交信息**: Support loading sample_from_anchor flag from speculators config (#48639)

Signed-off-by: Fynn Schmitt-Ulms <fschmitt@redhat.com>
Co-authored-by: Michael Goin <mgoin64@gmail.com>

### [5feb395](https://github.com/vllm-project/vllm/commit/5feb3950e529278b1f9dbe0a4071470d3d382a3d)

- **作者**: Charlie Fu
- **时间**: 2026-07-20T21:39:33Z
- **提交信息**: [ROCm][CI] fix test_rocm_quick_reduce.py (#49234)

Signed-off-by: charlifu <charlifu@amd.com>

### [4ec199b](https://github.com/vllm-project/vllm/commit/4ec199b66a791070348f3baf847b3a873c48cdd9)

- **作者**: Oxana Korzh
- **时间**: 2026-07-20T20:50:58Z
- **提交信息**: [Bugfix][Spec-Decode] Populate draft seq_lens_cpu_upper_bound for spec-decode attention metadata (#44492)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Signed-off-by: okorzh-amd <okorzh-amd@users.noreply.github.com>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: okorzh-amd <okorzh-amd@users.noreply.github.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [7ca0177](https://github.com/vllm-project/vllm/commit/7ca017778fc04cfb1a96080e7c484b1b44fc3a64)

- **作者**: Roberto L. Castro
- **时间**: 2026-07-20T20:21:55Z
- **提交信息**: [Feat][Perf] Add new warmup infrastructure for JITs (#47451)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fbfe581](https://github.com/vllm-project/vllm/commit/fbfe58133d9fa7c09ad94b21073b43c3accb402b)

- **作者**: coltonottley
- **时间**: 2026-07-20T19:12:36Z
- **提交信息**: [Bugfix][KV Offload] Preserve reachable tails for hybrid SWA groups (#48911)

Signed-off-by: Colton Ottley <colton@ottleyengineering.com>
Co-authored-by: Colton Ottley <colton@ottleyengineering.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [9dd62d8](https://github.com/vllm-project/vllm/commit/9dd62d80abad5d2ebeb0a4a60ad005a23c23d0e9)

- **作者**: wkutak
- **时间**: 2026-07-20T18:31:48Z
- **提交信息**: Cosmos3 FP8 ModelOpt/Diffusers remapping (#48952)

Signed-off-by: Wojciech Kutak <wkutak@nvidia.com>
Signed-off-by: wkutak <wkutak@nvidia.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Roger Wang <hey@rogerw.io>

### [f878367](https://github.com/vllm-project/vllm/commit/f87836789800ab29d66c5ae7d034e86eff730eaf)

- **作者**: tc-mb
- **时间**: 2026-07-20T18:17:46Z
- **提交信息**: [Revert][Bugfix] Restore MiniCPM-V 4.6 ViT QKV weight loader (#49193)

Signed-off-by: wjinxu <1299461899@qq.com>
Co-authored-by: wjinxu <1299461899@qq.com>

### [bd09107](https://github.com/vllm-project/vllm/commit/bd091079cba0800d8b8ee8ed22feab5864d1b101)

- **作者**: Matthew Bonanni
- **时间**: 2026-07-20T17:53:27Z
- **提交信息**: [Attention] FlashAttention 4 SM100 FP8 kv cache support (#42569)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [b23bd73](https://github.com/vllm-project/vllm/commit/b23bd73f540175f9e117eaee5029cd7d8df63964)

- **作者**: Liangqiusong
- **时间**: 2026-07-20T15:32:54Z
- **提交信息**: [XPU]add sycl path for Mhc (#47245)

Signed-off-by: root <xiaolong.guo@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [e2d7ade](https://github.com/vllm-project/vllm/commit/e2d7adeb642bd6e6bdb4f3305005e8608765d7cf)

- **作者**: Bugen Zhao
- **时间**: 2026-07-20T15:22:24Z
- **提交信息**: [Rust Frontend] Bump `xgrammar-structural-tag` and enable local extension (#49161)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [15cb8e1](https://github.com/vllm-project/vllm/commit/15cb8e140dffd9d2a33737c083fcf1d696e1d1f6)

- **作者**: Isotr0py
- **时间**: 2026-07-20T13:42:45Z
- **提交信息**: [Multimodal] Allow keeping original image mode for ImageIO (#49159)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [f007cce](https://github.com/vllm-project/vllm/commit/f007cceb422599330495b202632d78c7b3b89e61)

- **作者**: Chang Guo
- **时间**: 2026-07-20T13:41:58Z
- **提交信息**: [KV Offload] Support self-describing KV events with TieringOffloadingSpec (#48679)

Signed-off-by: Change72 <changg@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [0a5069e](https://github.com/vllm-project/vllm/commit/0a5069e4e30996866d9d3cc5551f784b85408bb0)

- **作者**: wangqian
- **时间**: 2026-07-20T13:39:28Z
- **提交信息**: [Bugfix][Gemma4] Fix ModelOpt mixed-precision MoE config mapping (#48563)

Signed-off-by: wangqian <601731555@qq.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [8ce53a6](https://github.com/vllm-project/vllm/commit/8ce53a616ebfc337edb73f847fcefe8af8ba769b)

- **作者**: EdalatiAli
- **时间**: 2026-07-20T13:18:17Z
- **提交信息**: [Bugfix] Zero new KV blocks for quantized + sliding-window hybrid caches (#47574)

Signed-off-by: EdalatiAli <aliedalati@cohere.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: Nicolò Lucchesi <nlucches@redhat.com>

### [ae10e85](https://github.com/vllm-project/vllm/commit/ae10e855abf4ff5e24e2088aef16029ee1cb7de8)

- **作者**: Lena Onyshchenko
- **时间**: 2026-07-20T10:05:36Z
- **提交信息**: [Misc][Docs] Remove duplicate CodeGeex4 row in XPU model table (#47210)

Signed-off-by: oonyshch <xonyshch@gmail.com>

### [530ee36](https://github.com/vllm-project/vllm/commit/530ee36a0d99869804c0af68b41007072b609480)

- **作者**: hcl
- **时间**: 2026-07-20T10:04:50Z
- **提交信息**: fix(openai): reject non-numeric logprobs with 400 instead of 500 (#49144)

Signed-off-by: Chenglun Hu <chenglunhu@gmail.com>

### [d835ad5](https://github.com/vllm-project/vllm/commit/d835ad572ca76d8ed6308e81750813c814fb3343)

- **作者**: Salt Sato
- **时间**: 2026-07-20T10:00:06Z
- **提交信息**: [Bugfix][Rust Frontend] Map missing prompt logprobs for single-token prompts in chat and raw generate (#49111)

Signed-off-by: Feathbow <feathbow@gmail.com>

### [47d0597](https://github.com/vllm-project/vllm/commit/47d0597ca2259096f18c52029a47cf10f9d35e70)

- **作者**: Lena Onyshchenko
- **时间**: 2026-07-20T09:44:25Z
- **提交信息**: [Misc][Docs] Fix broken csrc kernel links in fusions doc (#47211)

Signed-off-by: oonyshch <xonyshch@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [818cf61](https://github.com/vllm-project/vllm/commit/818cf61e9149c3fdff302cddbb2d026090160aea)

- **作者**: Reid
- **时间**: 2026-07-20T09:39:13Z
- **提交信息**: [Rust Frontend] Fix macro-based content format detection (#49042)

Signed-off-by: reidliu41 <reid201711@gmail.com>

### [c01618f](https://github.com/vllm-project/vllm/commit/c01618fdc81524ed4e91652bbf85ed23d6ddc448)

- **作者**: Bugen Zhao
- **时间**: 2026-07-20T09:31:25Z
- **提交信息**: [Rust][Benchmark] Integrate `vllm-bench` to `vllm-rs` & `vllm` CLI (#48930)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [823eaf6](https://github.com/vllm-project/vllm/commit/823eaf667d33125259d2d280b0ed00747fa92440)

- **作者**: Xiaochang Wu
- **时间**: 2026-07-20T08:32:03Z
- **提交信息**: [XPU] FP8 o_proj with fp8_bmm and load-time scale transpose (#48334)

Signed-off-by: Wu, Xiaochang <xiaochang.wu@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [f1f1259](https://github.com/vllm-project/vllm/commit/f1f1259692004c909f8b7f8f371d42c7a7871fa3)

- **作者**: Sage
- **时间**: 2026-07-20T08:28:25Z
- **提交信息**: [Rust Frontend] Use zero-copy slicing for multimodal tensors (#48781)

Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [df13b5a](https://github.com/vllm-project/vllm/commit/df13b5aef55c5cf6a3111b28e8d48b4a71575d8d)

- **作者**: zofia
- **时间**: 2026-07-20T07:47:26Z
- **提交信息**: [XPU] [MoE] add quant input when prepare for fusedmoe (#47122)

Signed-off-by: mayuyuace <qiming1.zhang@intel.com>
Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Signed-off-by: zofia <110436990+zufangzhu@users.noreply.github.com>
Co-authored-by: mayuyuace <qiming1.zhang@intel.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [4938d44](https://github.com/vllm-project/vllm/commit/4938d44a3b818fd443cf45aea92e670f16973ba0)

- **作者**: Sihan Chen
- **时间**: 2026-07-20T07:33:13Z
- **提交信息**: [CPU] fixes heterogeneous NIXL KV transfer into CPU_ATTN decode workers (#47871)

Signed-off-by: Spycsh <sihan.chen@intel.com>
Co-authored-by: Li, Jiang <jiang1.li@intel.com>

### [37bf988](https://github.com/vllm-project/vllm/commit/37bf988c2f8de10165e279fff652e9d818556fe8)

- **作者**: Michał Ganczarenko
- **时间**: 2026-07-20T07:25:56Z
- **提交信息**: [XPU][Bugfix] Fix GroupCoordinator device_index (#47295)

Signed-off-by: Michal Ganczarenko <michal.ganczarenko@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9459fc6](https://github.com/vllm-project/vllm/commit/9459fc647105f10f754697b3bf136d194564d603)

- **作者**: aoshen02
- **时间**: 2026-07-20T07:02:56Z
- **提交信息**: [Bugfix][RL] Set vLLM config during weight reload (#45989)

Signed-off-by: aoshen02 <aoshen@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-21
**监控日期**: 2026-07-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5634
- **最后更新**: 2026-07-20T22:36:56Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: Shenglei Fu, leo, Mu GuanLin

## AI分析总结

### 昨日更新要点总结（结合 `vllm-omni` 多模态服务项目背景）

---

#### 1. 主要更新类型
- **Bug修复**：占多数（5/8），涉及连续批处理路由、MoE LoRA、信任远程代码、SoulX部署管线、Qwen3-TTS参考音频。
- **硬件适配**：新增Ascend NPU支持（MiniCPM-o 4.5）。
- **重构**：统一LTX-2/2.3管线运行时。
- **新功能/量化**：为FLUX.2-dev添加在线FP8量化支持。

---

#### 2. 关键变更点与项目方向关系
| 提交 | 变更内容 | 与项目“统一多模态服务”方向的关系 |
|------|----------|----------------------------------|
| `dacb8e6` | 修复连续批处理下语音码路由 | 保证高并发场景下音频模态的请求正确隔离，提升吞吐稳定性 |
| `e24bddf` | 修复Qwen3-Omni thinker融合MoE的LoRA | 消除多模态模型（文本+语音+视频）的推理微调兼容性问题 |
| `4d79999` | 增加信任远程代码选项 | 完善安全启动流程，兼容HuggingFace等需远程代码的模型 |
| `7d75095` | 修复SoulX-Singer部署管线注册 | 确保新语音合成模型（SoulX）的服务化流程正常 |
| `74f2742` | 为MiniCPM-o 4.5添加NPU支持 | 扩展硬件生态（华为Ascend），降低多模态模型在国产芯片上的部署门槛 |
| `a06664a` | 统一LTX-2/2.3管线运行时 | 消除视频生成管线代码冗余，便于维护和后续扩展新版本 |
| `6cd1ff7` | FLUX.2-dev Mistral TE在线FP8量化 | 优化图像生成模型的显存占用与推理速度，降低服务成本 |
| `7b2edd6` | 修复Qwen3-TTS参考音频的artifacts准备 | 提升语音合成质量，确保参考音频在模式感知（mode-aware）场景下正确加载 |

---

#### 3. 对项目的影响与潜在意义
- **稳定性提升**：多个Bugfix直接修复了连续批处理、部署注册、音频准备等关键路径的缺陷，减少线上事故。
- **性能与成本优化**：FP8量化支持（FLUX）及批处理路由修复均能提升吞吐，降低GPU显存需求，符合“cheap”愿景。
- **硬件兼容性扩展**：NPU支持使

## 详细提交记录

### [dacb8e6](https://github.com/vllm-project/vllm-omni/commit/dacb8e6f10f06ffee05f6705f61f084e186470a4)

- **作者**: Juan Pablo Zuluaga
- **时间**: 2026-07-20T17:22:45Z
- **提交信息**: [Bugfix][Perf] mimo_audio: fix per-request speech-code routing under continuous batching (#5070)

Signed-off-by: JuanPZuluaga <juanz9312@gmail.com>
Co-authored-by: Yueqian Lin <70319226+linyueqian@users.noreply.github.com>

### [e24bddf](https://github.com/vllm-project/vllm-omni/commit/e24bddfb22f1c04ab28470043ac9a3585db95f64)

- **作者**: leo
- **时间**: 2026-07-20T15:52:21Z
- **提交信息**: Fix Qwen3-Omni thinker fused MoE LoRA (#5191)

Signed-off-by: leo <yaoliu548926@gmail.com>

### [4d79999](https://github.com/vllm-project/vllm-omni/commit/4d799997d33f6ff9942c824e0faf0d36be328e31)

- **作者**: zhumingjue138
- **时间**: 2026-07-20T15:20:53Z
- **提交信息**: [Bugfix] Fix issue 5205, add trust-remote-code (#5213)

Signed-off-by: zhumingjue <zhumingjue@huawei.com>

### [7d75095](https://github.com/vllm-project/vllm-omni/commit/7d75095b842a352031528536b90d8c01b81e2e0a)

- **作者**: Yukim1
- **时间**: 2026-07-20T14:34:42Z
- **提交信息**: [BugFix] Fix SoulX-Singer deploy pipeline registration (#5210)

Signed-off-by: zwhzzz0821 <2831474076@qq.com>

### [74f2742](https://github.com/vllm-project/vllm-omni/commit/74f2742ac2773a0c2205a725dbfcb62ae00c6e6a)

- **作者**: amy-why-3459
- **时间**: 2026-07-20T13:45:28Z
- **提交信息**: [Hardware][Ascend][Model] Add NPU support for MiniCPM-o 4.5 talker/vo… (#5117)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a06664a](https://github.com/vllm-project/vllm-omni/commit/a06664a243d87fe4094bfbb5383e5e7bc5436262)

- **作者**: Mu GuanLin
- **时间**: 2026-07-20T12:02:30Z
- **提交信息**: [Refactor] Unify the LTX-2 and LTX-2.3 pipeline runtime (#5147)

Signed-off-by: mglyn <1203789601@qq.com>

### [6cd1ff7](https://github.com/vllm-project/vllm-omni/commit/6cd1ff7e645030e6e76adbe2ee2b15cf8bda968a)

- **作者**: Diya Peng
- **时间**: 2026-07-20T08:16:31Z
- **提交信息**: [Quantization] Add FLUX.2-dev Mistral TE online FP8 support (#5136)

Signed-off-by: diyapeng <50388704+diyapeng@users.noreply.github.com>
Co-authored-by: diyapeng <50388704+diyapeng@users.noreply.github.com>

### [7b2edd6](https://github.com/vllm-project/vllm-omni/commit/7b2edd66507823c20d30ea097e1df116e9f80984)

- **作者**: Shenglei Fu
- **时间**: 2026-07-20T07:38:07Z
- **提交信息**: [Bugfix][Qwen3-TTS] Mode-aware ref_audio artifact readiness (fixes #5049) (#5157)

---
