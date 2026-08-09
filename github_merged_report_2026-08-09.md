# GitHub Stars 合并报告 - 2026-08-09

**合并日期**: 2026-08-10
**监控日期**: 2026-08-09
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


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2135
- **最后更新**: 2026-08-07T20:53:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2609
- **最后更新**: 2026-08-09T21:46:15Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2192
- **最后更新**: 2026-08-09T04:09:22Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 6134
- **最后更新**: 2026-08-09T19:06:10Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Yuxi Chi

## AI分析总结

# 提交分析报告

## 1. 主要更新类型

本次提交为**Bug修复**，针对MoE（Mixture-of-Experts）推理内核中单专家（singleton expert）场景下的TMA（Tensor Memory Accelerator）描述符崩溃问题。

## 2. 关键变更点

- **根因定位**：当本地专家数为1时，静态形状细化会将权重专家模式重写为Python `1`，而CuTeDSL 4.6.0在将单例TMA批处理基序规范化后，反细化到内核ABI时触发段错误。
- **修复策略**：前端保持单例专家权重模式为运行时动态，内核在静态细化前保存运行时专家维度，并复用于FC1和FC2权重TMA描述符。多专家路径不受影响。
- **测试增强**：新增`E_local=1, topk=1`的NVFP4 MegaMoE回归测试，与现有独立torch-oracle测试集成。

## 3. 项目影响与意义

FlashInfer定位为高性能GPU推理内核库，MoE是其核心场景之一。该修复直接解决了单专家配置下的崩溃问题，填补了极端配置的空白，提升了库的鲁棒性和生产环境可用性。验证结果中单专家场景`rel_l2=0, max_abs=0`，表明修复后数值精度完全对齐参考实现。

## 4. 值得关注的技术点

- **TMA描述符生命周期管理**：展示了静态形状细化与运行时动态维度之间的微妙交互，以及如何在两者间保持一致性。
- **CuTeDSL版本兼容性**：问题与特定版本（4.6.0）的规范化行为相关，提示依赖版本升级可能引入的边界情况。
- **回归测试策略**：针对极端配置（单专家）的定向测试，体现了对边界条件的重视。

## 5. 对项目发展的影响

该修复强化了FlashInfer在MoE推理领域的可靠性，特别是对NVFP4量化MegaMoE模型的支持。通过解决单专家这一此前未覆盖的边界情况，项目向“开箱即用”的高性能推理库目标又迈进了一步，有助于吸引更广泛的用户群体，尤其是在小规模或特殊配置部署场景下的采用。

## 详细提交记录

### [4fbac49](https://github.com/flashinfer-ai/flashinfer/commit/4fbac49f30e1f40a0dcddd90512b8c56d68037f7)

- **作者**: Yuxi Chi
- **时间**: 2026-08-09T09:28:34Z
- **提交信息**: fix(moe_ep): preserve singleton expert TMA modes (#4296)

## Summary

- Keep the runtime expert extent visible in singleton-expert FC1 and FC2
weight TMA descriptors.
- Mark only the compact expert mode of singleton weight tensors dynamic
while retaining static hidden, intermediate, scheduler, workspace, and
epilogue specialization.
- Add an `E_local=1`, `topk=1` NVFP4 MegaMoE regression to the existing
independent torch-oracle test.

## Root cause

NVFP4 MegaMoE always supplies `static_expert_shape`. When the local
expert count is one, static shape refinement rewrites the weight expert
mode to a Python `1`. CuTeDSL 4.6.0 canonicalizes that singleton TMA
batch basis before the descriptor is derefined to the kernel ABI,
causing a segmentation fault during the first kernel compilation/launch.

The frontend now keeps the singleton weight expert mode runtime-dynamic,
and the kernel saves that runtime extent before static refinement and
reuses it for the FC1 and FC2 weight TMA descriptors. Multi-expert
launches follow the existing path unchanged.

## Validation

Tested on NVIDIA B200 with CUDA 13 and `nvidia-cutlass-dsl==4.6.0`.

Before the fix:

- `E_local=4`, `topk=4`: passes the torch oracle.
- `E_local=1`, `topk=1`: reproducibly segfaults at the first kernel
compile/launch after preprocessing, staging, and oracle computation
complete.

After the fix:

```text
tests/moe_ep/test_nvfp4_cutedsl_kernel_vs_reference.py
4 passed

regular-e4:   rel_l2=0.002695
tail-e4:      rel_l2=0.002707
singleton-e1: rel_l2=0, max_abs=0
```


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved Mixture-of-Experts kernel handling for configurations with a
single expert.
* Preserved correct runtime tensor dimensions during specialized
processing.
* Expanded validation across standard, tail-aligned, and
singleton-expert configurations to ensure results match the reference
implementation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3934
- **最后更新**: 2026-08-09T20:11:12Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Shao Duan, William Lin

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
本次提交以**功能新增**和**性能优化**为主，辅以**代码重构**。三个提交均围绕 MiniMax-H3 模型展开，体现了对特定模型架构的深度优化。

### 2. 关键变更点与项目方向
- **VSA稀疏注意力**（e0d702d）：为 MiniMax-H3 引入 packed mixed-modality sparse attention，支持混合模态数据的稀疏注意力计算，直接增强 FastVideo 对多模态视频生成场景的支持能力。
- **参数压缩**（541ef01）：通过 rank-reduced AdaLN 技术提供剪枝模型选项，减少39%参数和23GiB显存占用，显著降低推理门槛，符合项目降低部署成本的整体方向。
- **管线清理**（ffc1a7a）：重构 H3 管线，提取共享辅助函数、移除死代码、提升循环不变量的提取，为后续维护和扩展奠定更干净的基础。

### 3. 项目影响与潜在意义
- 显存占用的大幅降低使 MiniMax-H3 能在更小规模GPU上运行，扩大用户覆盖面，提升项目易用性。
- 稀疏注意力提升长序列混合模态数据的处理效率，直接增强 FastVideo 在复杂视频生成任务中的竞争力。
- 重构工作虽不直接产生用户可见功能，但降低后续迭代的技术债务，提升开发效率。

### 4. 值得关注的技术点
- **VSA稀疏注意力**：packed mixed-modality 设计表明项目正探索统一处理文本、图像、视频等多模态输入的注意力机制，这是视频生成领域的前沿方向。
- **rank-reduced AdaLN**：通过低秩近似压缩 AdaLN 层参数，在保持生成质量的同时显著减少模型体积，是模型压缩领域的实用技巧。
- **循环不变量的提升**：体现对推理性能的精细优化，说明项目不仅关注模型层面，也重视工程层面的执行效率。

### 5. 对项目发展的影响
结合 README 中 FastVideo 定位为高效视频生成平台的目标，本次提交通过**降低硬件门槛**和**提升多模态处理效率**，直接推动项目向“更易用、更高效”方向发展。MiniMax-H3 的专项优化表明项目正积极适配主流视频生成模型，而管线清理则为未来支持更多模型架构打下基础。整体来看，这些提交强化了 FastVideo 在低成本、高质量视频生成领域的竞争力，有助于吸引更广泛的用户和开发者社区。

## 详细提交记录

### [e0d702d](https://github.com/hao-ai-lab/FastVideo/commit/e0d702decbfd6b9765dd120f676763c1bf7095d5)

- **作者**: William Lin
- **时间**: 2026-08-09T20:10:51Z
- **提交信息**: [feat] VSA for MiniMax H3: packed mixed-modality sparse attention (#1695)

### [541ef01](https://github.com/hao-ai-lab/FastVideo/commit/541ef014eea86dbc98f7d848bb686bdcf43c4f92)

- **作者**: Shao Duan
- **时间**: 2026-08-09T19:31:57Z
- **提交信息**: [perf] MiniMax-H3: rank-reduced AdaLN pruned model option (-39% params, -23 GiB VRAM) (#1699)

### [ffc1a7a](https://github.com/hao-ai-lab/FastVideo/commit/ffc1a7a58b7b1ec70e4d1dc5925d83cc0e065b98)

- **作者**: William Lin
- **时间**: 2026-08-09T11:51:31Z
- **提交信息**: [refactor] H3 pipeline cleanup: shared helpers, dead machinery, loop-invariant hoists (#1698)

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34271
- **最后更新**: 2026-08-09T22:00:30Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
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


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12892
- **最后更新**: 2026-08-09T18:49:24Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 31585
- **最后更新**: 2026-08-09T21:46:20Z

## 提交统计

- **昨日提交总数**: 25
- **提交者数量**: 14
- **主要提交者**: WenhaoZhang, Ke Bao, Mick

## AI分析总结

# SGLang 昨日提交分析报告

## 一、主要更新类型

本次提交涵盖**配置系统重构**（6项）、**Bug修复**（5项）、**功能新增**（4项）、**测试优化**（3项）、**文档更新**（2项）、**性能优化**（2项）及**回滚操作**（1项），整体以配置架构重构和稳定性修复为主线。

## 二、关键变更点与项目方向

**配置系统深度重构**是本次最核心的变更。提交逐步将配置读取逻辑从业务代码中剥离，引入“bags”机制统一管理KV-cache配置、runner和scheduler的配置解析，并移除隐藏的全局回退配置。这标志着SGLang正从“分散读取配置”向“集中解析、统一分发”的架构演进，与项目追求高可维护性和可扩展性的方向一致。同时，runner的DCP拓扑改为从ParallelState派生，进一步强化了配置与运行时状态的解耦。

**确定性推理能力增强**是另一重要方向。新增gumbel采样中u=1的钳制处理，修复了掩码token可能被采样的逻辑漏洞；修复tp>1时的确定性all-reduce问题；新增logprob一致性测试技能。这些变更直接服务于SGLang对可复现推理的承诺，对离线评估和调试场景尤为关键。

**硬件适配与模型支持扩展**方面，新增flashinfer rmsnorm+quant融合（支持SM90/100/120）、FA4后端支持GLM4.7-flash、sol-attn稀疏注意力后端支持h3，以及Qwen35的language_model_only参数。这些体现了项目持续跟进最新硬件特性和模型架构的积极姿态。

## 三、项目影响与潜在意义

配置重构虽短期增加迁移成本，但长期将显著降低业务代码与配置源的耦合度，使新增配置项和调整默认值更加安全可控。确定性推理的修复对科学计算和自动化评测场景具有重要价值。AMD MI35x的DeepSeek-V4-Pro-DSpark夜间测试注册修复，则保障了特定硬件平台的质量门禁。

## 四、值得关注的技术点

- **Mamba状态内存修复**：修复specdec下sconv状态内存损坏问题，涉及状态管理正确性
- **并行请求生命周期回滚**：回滚#32588的并行请求追踪，说明该方案存在未预期问题，值得关注后续替代方案
- **CPU传输图像预处理优化**：将Kimi K3的CPU传输图像预处理移至vision owner，减少跨设备传输开销
- **批量Mamba边界掩码复用**：减少重复计算，提升推理效率

## 五、对项目发展的影响

这些提交表明SGLang正处于**架构收敛期**：一方面通过配置系统重构夯实工程基础，另一方面在确定性推理、多硬件支持和模型兼容性上持续投入。配置架构的演进为后续多后端、多硬件场景下的复杂配置管理铺平道路；确定性推理能力则巩固了其在需要严格可复现场景中的竞争力。整体来看，项目在保持功能快速迭代的同时，正有意识地强化内部一致性和可靠性，为规模化部署和生态扩展奠定更稳固的根基。

## 详细提交记录

### [57f2105](https://github.com/sgl-project/sglang/commit/57f2105118f84a8d08e39c7b692a3472ba18a6c5)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:46:14Z
- **提交信息**: docs(skill): record where config is read now that the seed is off limits (#34097)

### [b4284f3](https://github.com/sgl-project/sglang/commit/b4284f3eb729e2d8e61408dd22f1d077ab0eb5f1)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:45:42Z
- **提交信息**: config: the KV-cache configurator reads the bags (#34096)

### [e216c2b](https://github.com/sgl-project/sglang/commit/e216c2bc59ceca52ed2e21f0b6be79dd88ada442)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:45:11Z
- **提交信息**: config: the runner and scheduler read resolved config from the bags (#34095)

### [a2199c1](https://github.com/sgl-project/sglang/commit/a2199c1dee09c0f1063f526bf03d580e9d141769)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:44:39Z
- **提交信息**: config: pin that resolution is reproducible from the raw input (#34094)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [63833f8](https://github.com/sgl-project/sglang/commit/63833f8034fbfff45d1357af38aa4da568eb9a0a)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:44:08Z
- **提交信息**: config: business code no longer reads the published ServerArgs (#34081)

### [110bf7e](https://github.com/sgl-project/sglang/commit/110bf7e6a83b1b2bea74ffe52b7f6aa20f34b882)

- **作者**: Cheng Wan
- **时间**: 2026-08-09T21:43:28Z
- **提交信息**: config: retire the hidden global fallbacks and the mamba-extra-buffer instance reads (#34080)

### [967cac8](https://github.com/sgl-project/sglang/commit/967cac801ce3c1522e2f56b128e53ee064170f37)

- **作者**: Michael
- **时间**: 2026-08-09T21:10:28Z
- **提交信息**: [AMD] [CI] Register the DeepSeek-V4-Pro-DSpark MI35x nightly job so its suite actually runs (#34147)

### [bfeb9a8](https://github.com/sgl-project/sglang/commit/bfeb9a8af29cae971669a07fb242db4eeefc5a1c)

- **作者**: Zheng Li
- **时间**: 2026-08-09T18:47:36Z
- **提交信息**: [feat] Add language_model_only parameter support for Qwen35 (#22867)

Co-authored-by: 瑀澈 <yuche.lz@alibaba-inc.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [c2fbe2f](https://github.com/sgl-project/sglang/commit/c2fbe2f6d88692fa7756ed1be73ef9e85bd6b7cf)

- **作者**: Ke Bao
- **时间**: 2026-08-09T17:33:00Z
- **提交信息**: Add skill for the logprob consistency tests (#34169)

### [168eba3](https://github.com/sgl-project/sglang/commit/168eba32572841b05eced3aed7d9884fba6a0ec0)

- **作者**: Eric Zhang
- **时间**: 2026-08-09T16:56:36Z
- **提交信息**: [Fix] Speculative decoding crashes with DP-Attention (#33892)

### [2ab96d0](https://github.com/sgl-project/sglang/commit/2ab96d0fe0b156604a3dac29cdac739adb5e8e5a)

- **作者**: Ke Bao
- **时间**: 2026-08-09T16:55:55Z
- **提交信息**: Fix mlx unit test batch mock (#34181)

### [fb72a37](https://github.com/sgl-project/sglang/commit/fb72a37fdefa80ac00b23096130d5f815bbe2136)

- **作者**: Ke Bao
- **时间**: 2026-08-09T14:22:27Z
- **提交信息**: Add deterministic logprob-consistency test for inkling-small nvfp4 (#34168)

### [3fe65e0](https://github.com/sgl-project/sglang/commit/3fe65e065475ebaffdaa2492ff20f9116309d5f2)

- **作者**: Kurt Shuster
- **时间**: 2026-08-09T13:43:27Z
- **提交信息**: Deterministic gumbel sampling: clamp u=1 so masked tokens can't be sampled (#33423)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>

### [fc40684](https://github.com/sgl-project/sglang/commit/fc40684b3286255260e0f739cbcdceaff34cb741)

- **作者**: Eric Zhang
- **时间**: 2026-08-09T13:42:54Z
- **提交信息**: [srt] Fix sconv state memory corruption on specdec (#34043)

### [11d03ea](https://github.com/sgl-project/sglang/commit/11d03eaeefd87c867f3fcbdf63f58cc0ae04de39)

- **作者**: DevashishLal-CB
- **时间**: 2026-08-09T12:15:03Z
- **提交信息**: runtime: Add flashinfer rmsnorm + quant fusion support SM90, SM100, SM120- #32994 (#33471)

Signed-off-by: Devashish Lal <devcode@fb.com>
Co-authored-by: Devashish Lal <devcode@fb.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [7120f3e](https://github.com/sgl-project/sglang/commit/7120f3ee13de565cc737e0598110e7f7603c4e9f)

- **作者**: Yuzhen Zhou
- **时间**: 2026-08-09T12:05:38Z
- **提交信息**: fix: support FA4 backend for GLM4.7-flash (#33436)

### [71043b9](https://github.com/sgl-project/sglang/commit/71043b9dbbd8075f1b2ab7520b87c319daabb90a)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-09T10:10:02Z
- **提交信息**: Revert parallel request lifecycle tracking from #32588 (#34160)

Signed-off-by: Lianmin Zheng <lianminzheng@gmail.com>

### [fcc5468](https://github.com/sgl-project/sglang/commit/fcc5468cce63643436879575fee638a529475a04)

- **作者**: Ke Bao
- **时间**: 2026-08-09T10:08:14Z
- **提交信息**: Fix deterministic inference all-reduce for tp>1 (#34159)

### [c500674](https://github.com/sgl-project/sglang/commit/c500674124c6b8c4edca5f4284e8ec0189fcce09)

- **作者**: Ke Bao
- **时间**: 2026-08-09T08:49:49Z
- **提交信息**: Switch inkling per-commit test to nvfp4 (#32402)

### [78cd60b](https://github.com/sgl-project/sglang/commit/78cd60b4e3c24171e0c7fe56ffbaa5ab99bafaeb)

- **作者**: Leon Gao
- **时间**: 2026-08-09T08:47:05Z
- **提交信息**: [srt] Reuse batched Mamba boundary mask (#33477)

### [51470b3](https://github.com/sgl-project/sglang/commit/51470b376fbd6059e5998359cfe02683a203a11f)

- **作者**: WenhaoZhang
- **时间**: 2026-08-09T08:26:06Z
- **提交信息**: [diffusion] feat: support sol-attn sparse attention backend for h3 (#33702)

### [ce1b9f8](https://github.com/sgl-project/sglang/commit/ce1b9f88b6f56bae6edc67a6e09324b925cc8331)

- **作者**: Khoa Pham
- **时间**: 2026-08-09T08:18:24Z
- **提交信息**: config: derive the runner's DCP topology from its ParallelState (#34133)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [22e0035](https://github.com/sgl-project/sglang/commit/22e003580bc0032918f1ebd1111de4850e33ec0f)

- **作者**: Mick
- **时间**: 2026-08-09T08:13:20Z
- **提交信息**: [Kimi K3] optimize: preprocess cpu-transport images on the vision owner (#33921)

### [d0aa37b](https://github.com/sgl-project/sglang/commit/d0aa37b49b668d41345d0c5239ccf7028b9e13a7)

- **作者**: Kangrui Du
- **时间**: 2026-08-09T08:11:28Z
- **提交信息**: [diffusion] fix: update weight from tensor detects device by uuid (#32685)

### [bc285b2](https://github.com/sgl-project/sglang/commit/bc285b2064c0373227cfb6ada77a37e7b8c43510)

- **作者**: Lianmin Zheng
- **时间**: 2026-08-09T07:22:57Z
- **提交信息**: refactor: clean up logits processor helpers (#34158)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1244
- **最后更新**: 2026-08-09T20:22:25Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 88607
- **最后更新**: 2026-08-09T22:38:21Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 8
- **主要提交者**: Almog Tavor, Harry Mellor, Yifan Qiao

## AI分析总结

## 提交分析总结

### 1. 主要更新类型
- **Bug修复**：3项（混合缓存连接器范围、KV卸载调度器、加载死锁）
- **基础设施/CI优化**：2项（文档修复、ROCm CI镜像复用）
- **依赖升级**：1项（Flashinfer版本）
- **功能适配**：1项（TPU支持Kimi K3导入）
- **可观测性增强**：1项（KV卸载事件自描述）

### 2. 关键变更点与项目方向
- **KV Offload系列修复**（3项）：针对部分循环块事件、分块局部注意力调度、加载活锁问题，直接强化vLLM的KV缓存卸载能力，这是提升长序列推理效率的核心路径。
- **混合缓存Bug修复**：限定混合缓存命中范围到支持连接的组件，避免错误缓存传播，保障多模态/多后端场景下的正确性。
- **ROCm CI镜像复用**：通过复用等效镜像减少CI构建时间，降低AMD平台维护成本，扩大vLLM对ROCm生态的支持效率。
- **Flashinfer升级**：保持与最新内核库同步，持续获得性能优化和新注意力算法支持。

### 3. 项目影响与潜在意义
- **稳定性提升**：修复KV卸载中的活锁和调度问题，避免推理服务在长序列场景下卡死或失败，直接提升生产环境可靠性。
- **多硬件支持强化**：ROCm CI优化和TPU适配表明vLLM正加速覆盖AMD和Google TPU平台，巩固其“人人可用”的跨硬件愿景。
- **可观测性进步**：KV卸载事件自描述化便于开发者诊断和优化，降低高级功能的调试门槛。

### 4. 值得关注的技术点
- **KV Offload调度器**对分块局部注意力的处理，涉及复杂的内存管理和注意力窗口边界逻辑，是高性能推理的关键难点。
- **加载活锁修复**通过将查找判定标记为“未命中”打破死循环，体现了分布式缓存系统中状态一致性的精细处理。
- **混合缓存命中范围限定**提示vLLM的缓存系统正走向更细粒度的连接器感知，为异构硬件缓存共享铺路。

### 5. 对项目发展的影响
结合README中“Easy, fast, and cheap LLM serving for everyone”的目标，本批提交体现了vLLM在**可靠性**和**硬件覆盖**两方面的持续投入。KV Offload的成熟将直接降低长上下文推理的显存成本，符合“cheap”的承诺；ROCm和TPU的适配则拓展了“everyone”的边界。同时，CI和文档的维护保证了项目在快速迭代中保持可维护性，为后续功能开发奠定稳定基础。整体来看，这些提交虽以修复和基础设施为主，但都是支撑vLLM规模化落地和生态扩展的必要基石。

## 详细提交记录

### [d694130](https://github.com/vllm-project/vllm/commit/d6941300fcb9d4a8bbea19f8b610c2aff9fc5cc3)

- **作者**: Yifan Qiao
- **时间**: 2026-08-09T22:38:13Z
- **提交信息**: [BugFix] Scope divergent hybrid cache hits to capable connectors (#50344)

Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [83ad767](https://github.com/vllm-project/vllm/commit/83ad767eed3be3ee7f2df63be693bfaca5c7c922)

- **作者**: Harry Mellor
- **时间**: 2026-08-09T09:46:12Z
- **提交信息**: [CI] fix docs on `main` (#51539)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [04d13b5](https://github.com/vllm-project/vllm/commit/04d13b5d653725651f7a750f0022f06d095881dc)

- **作者**: Jeff (Junze) Ma
- **时间**: 2026-08-09T09:06:34Z
- **提交信息**: [K3] Allow tpu to import kimi_k3.common (#51529)

Signed-off-by: Jeff Ma <jeffjma@umich.edu>

### [c423998](https://github.com/vllm-project/vllm/commit/c4239986427a40389fd79c1a4f6afd48aea6512e)

- **作者**: Chauncey
- **时间**: 2026-08-09T08:28:44Z
- **提交信息**: [KV Offload] Emit self-describing events for partial recurrent blocks (#51243)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>

### [7f6432c](https://github.com/vllm-project/vllm/commit/7f6432cc0daf97c5b9a2df141641c595a766ff40)

- **作者**: Andreas Karatzas
- **时间**: 2026-08-09T08:25:03Z
- **提交信息**: [ROCm][CI] Reuse equivalent ROCm CI images (#48646)

Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [f18e10a](https://github.com/vllm-project/vllm/commit/f18e10a7e1c1eb37e898c31989ff625d79791657)

- **作者**: Wei Zhao
- **时间**: 2026-08-09T07:54:07Z
- **提交信息**: Bump Flashinfer version to 0.6.16.post3 (#50892)

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: jiahanc <173873397+jiahanc@users.noreply.github.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [eb24bc3](https://github.com/vllm-project/vllm/commit/eb24bc38cfc6818d6dc6d8440faf6e7062396f17)

- **作者**: Almog Tavor
- **时间**: 2026-08-09T07:25:57Z
- **提交信息**: [Bugfix][KV Offload] Handle chunked local attention in offloading scheduler (#51161)

Signed-off-by: almogtavor <almogtavor@gmail.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1b0ce31](https://github.com/vllm-project/vllm/commit/1b0ce31f3265dce4f0c638cd7e2cf27f5d8c0fbc)

- **作者**: Robbie J
- **时间**: 2026-08-09T07:25:36Z
- **提交信息**: [KV Offload] Fix failed-load livelock by marking the lookup verdict as a miss (#49328)

Signed-off-by: Robbie J <RobbieJ@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-08-10
**监控日期**: 2026-08-09
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5992
- **最后更新**: 2026-08-09T22:22:17Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 7
- **主要提交者**: linzhenpl07, yiminghub2024, Weiming Liao

## AI分析总结

## 提交分析总结

### 1. 主要更新类型

本批次提交涵盖**功能新增**（TeaCache支持、Cosmos3会话内存移植）、**Bug修复**（NPU平台RoPE崩溃）、**性能优化**（CUDA Graph加速）、**文档更新**（多平台部署配方）及**代码重构**（TTS模型检测逻辑）五类变更，整体呈现多元化发展态势。

### 2. 关键变更点与项目方向的关系

- **MiniMax-H3模型生态建设**（提交1、2、5、6）：围绕该模型新增RTX PRO 6000、DGX Spark、ROCm gfx950等多平台部署配方，并修复NPU上的RoPE崩溃问题。这与vLLM-Omni“为所有人提供易用、快速、廉价的omni-modality服务”的使命高度一致，通过降低多硬件适配门槛扩大用户覆盖。
- **TeaCache支持与Cache-DiT验证**（提交3）：为MiniMax-H3引入缓存加速机制，直接提升推理效率，契合项目“快速”的核心目标。
- **CUDA Graph优化**（提交4）：针对MiniCPM-O-4.5的HiFTGenerator模块，通过减少内核启动开销提升性能，属于典型的推理加速优化。
- **TTS模型检测重构**（提交7）：从硬编码检测转向基于适配器元数据推导，提升代码可维护性和扩展性，为后续新TTS模型接入奠定基础。
- **Cosmos3会话内存移植**（提交8）：实现RFC #4480 Phase 0，为UND文本K/V引入会话级内存管理，这是面向长对话场景的重要架构升级。

### 3. 对项目的影响和潜在意义

- **硬件生态扩展**：多平台配方（NVIDIA消费级、DGX、AMD ROCm、华为NPU）显著拓宽了项目支持的硬件矩阵，有助于吸引更广泛的开发者社区。
- **性能竞争力提升**：TeaCache和CUDA Graph优化直接改善用户体验，在omni-modality推理领域增强与竞品的性能优势。
- **架构前瞻性**：Cosmos3会话内存移植和TTS检测重构为未来功能扩展预留了清晰的技术路径，降低长期维护成本。

### 4. 值得关注的技术点

- **TeaCache机制**：一种针对DiT（Diffusion Transformer）的缓存加速方案，其与Cache-DiT的联合验证表明项目在探索系统级缓存优化策略。
- **NPU适配细节**：修复中强调“在mindiesd kernel前补充缺失的batch维度”，揭示了跨硬件后端（NPU vs GPU）时张量形状兼容性的常见陷阱。
- **CUDA Graph在生成模块的应用**：将CUDA Graph应用于HiFTGenerator而非传统注意力层，展示了性能优化的精细化方向。
- **基于元数据的模型检测**：通过适配器元数据而非代码硬编码识别TTS模型，体现了插件化架构设计思想。

### 5. 对项目发展的影响

结合README中“Easy, fast, and cheap omni-modality model serving”的定位，本批次提交呈现三个发展信号：**一是多模态模型覆盖持续扩大**，MiniMax-H3和MiniCPM-O-4.5的深度优化表明项目正积极跟进前沿omni模型；**二是硬件适配从主流GPU向多元化计算平台延伸**，NPU和ROCm的支持使项目在异构计算环境中更具实用性；**三是架构演进兼顾短期性能与长期可扩展性**，缓存优化和会话内存移植解决当前痛点，而重构工作则为未来模型接入铺平道路。整体来看，项目正从“支持更多模型”向“在更多硬件上高效运行模型”的方向深化，同时通过架构优化保持技术债可控，发展路径清晰且可持续。

## 详细提交记录

### [615de4e](https://github.com/vllm-project/vllm-omni/commit/615de4e041d1eeb78b3017845ab2f0600f2c9c41)

- **作者**: yiminghub2024
- **时间**: 2026-08-09T15:52:40Z
- **提交信息**: [doc]Add recipe for MiniMax-H3 on RTX PRO 6000 (#5863)

Signed-off-by: yiminghub2024 <482890@qq.com>

### [be48b07](https://github.com/vllm-project/vllm-omni/commit/be48b0797eb4c316113793bf126fe9aeb858a47c)

- **作者**: yiminghub2024
- **时间**: 2026-08-09T15:15:05Z
- **提交信息**: Add MiniMax-H3 recipe for DGX Spark (GB10) (#5946)

Signed-off-by: yiminghub2024 <482890@qq.com>

### [45629a8](https://github.com/vllm-project/vllm-omni/commit/45629a8e268f9fe9cde7e5eca0ad57f51c21d5c2)

- **作者**: Diya Peng
- **时间**: 2026-08-09T15:07:21Z
- **提交信息**: [MiniMax-H3] TeaCache support and Cache-DiT validation (#5840)

Signed-off-by: dpeng123 <diyapeng123@gmail.com>
Signed-off-by: lishunyang12 <lishunyang12@163.com>
Co-authored-by: lishunyang12 <lishunyang12@163.com>

### [fc8946f](https://github.com/vllm-project/vllm-omni/commit/fc8946fcf542cf108fa8b2fdc69de737bbfd52d8)

- **作者**: boatman
- **时间**: 2026-08-09T14:29:49Z
- **提交信息**: [Perf][MiniCPM-O-4.5]Add CUDA Graph For HiFTGenerator (#5869)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>

### [f01e4bd](https://github.com/vllm-project/vllm-omni/commit/f01e4bdddcb90193119f4fc95920af829965f201)

- **作者**: amd-xiaoyu12
- **时间**: 2026-08-09T14:18:24Z
- **提交信息**: [Recipe] Document MiniMax H3 ROCm (gfx950) BF16 serving (#5723)

Signed-off-by: Xiao Yu <xiao.yu@amd.com>
Signed-off-by: amd-xiaoyu12 <xiao.yu@amd.com>

### [5926370](https://github.com/vllm-project/vllm-omni/commit/592637015ffccec514401b700548768232d9590c)

- **作者**: Weiming Liao
- **时间**: 2026-08-09T14:08:43Z
- **提交信息**: [BugFix][NPU] MiniMax-H3 RoPE crash: add the missing batch dim before the mindiesd kernel (#5896)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [ebe93f5](https://github.com/vllm-project/vllm-omni/commit/ebe93f5d1e794202598e652a45fa74a29a7f698b)

- **作者**: Yueqian Lin
- **时间**: 2026-08-09T13:30:05Z
- **提交信息**: [Refactor][TTS] Derive TTS model detection from adapter metadata (#5682)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [8e2e9b6](https://github.com/vllm-project/vllm-omni/commit/8e2e9b6b53e86e6a479ed2c0a53782f655f60e04)

- **作者**: linzhenpl07
- **时间**: 2026-08-09T12:53:17Z
- **提交信息**: [Feat] Cosmos3 session-memory port for UND text K/V (RFC #4480 Phase 0) (#4657)

Signed-off-by: linzhenpl07 <linzhenpl07@gmail.com>
Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

---
