# GitHub Stars 合并报告 - 2026-09-20

**合并日期**: 2026-09-21
**监控日期**: 2026-09-20
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


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2214
- **最后更新**: 2026-09-20T10:01:36Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Feng, qcm1

## AI分析总结

# VeOmni 昨日提交分析（第 1/1 批）

## 1. 主要更新类型

本批次包含两类提交：
- **功能新增**：为 Qwen3.5 dense 与 MoE 模型支持 MTP（Multi-Token Prediction）训练。
- **Bug 修复**：修复 DiT（Diffusion Transformer）恢复训练时设备与条件模型 RNG 状态未持久化的问题。

整体呈现“新模型能力扩展 + 训练稳定性修复”的双线推进。

## 2. 关键变更点与项目方向的关系

- **MTP 训练支持（#1088）**：MTP 是当前大模型训练中提升推理效率与训练信号密度的主流技术。将其扩展到 Qwen3.5 的 dense 与 MoE 两种架构，说明 VeOmni 正持续扩大对前沿模型结构与训练范式的覆盖范围，契合其“任意模态模型训练”的定位。
- **DiT 恢复训练 RNG 修复（#1189）**：确保 device 与 condition-model 的随机数状态在断点续训时被正确保存与恢复。这直接关系到扩散模型训练的可复现性与长周期训练的可靠性。

## 3. 对项目的影响与潜在意义

- MTP 支持让 VeOmni 在多模态/大语言模型训练配方上更具竞争力，尤其 MoE 场景下的 MTP 是较新的工程挑战，体现框架对复杂并行与稀疏结构的适配能力。
- RNG 持久化修复消除了 DiT 续训中潜在的训练偏差与结果不可复现问题，对研究型用户和生产级长训练任务都是关键保障。

## 4. 值得关注的技术点

- MoE 架构下 MTP 的实现方式（辅助头与路由、负载均衡的交互）。
- RNG 状态持久化的粒度：是否覆盖数据加载、dropout、扩散采样等多个随机源。
- 断点续训的“完全确定性”是否已达成，仍是分布式训练中的难点。

## 5. 基于 README 背景的项目发展影响

VeOmni 定位为“以模型为中心的分布式配方动物园”，强调跨模态、可扩展的训练能力。本次提交一方面通过 MTP 扩展了 LLM/MoE 训练配方，强化“任意模态”叙事；另一方面通过 DiT 续训修复巩固了扩散模型这一重要模态的训练可靠性。两者共同推动项目从“能训”走向“训得稳、训得可复现”，符合其面向大规模多模态训练的长期目标。

## 详细提交记录

### [262b4a5](https://github.com/ByteDance-Seed/VeOmni/commit/262b4a537f53a6e46382fde1e0c71901b4cbf023)

- **作者**: qcm1
- **时间**: 2026-09-20T10:01:31Z
- **提交信息**: [model] feat: support mtp training for Qwen3.5 dense and moe model (#1088)

### [c21de9a](https://github.com/ByteDance-Seed/VeOmni/commit/c21de9a79e748e69bf732d2fd692df9a0c7184f4)

- **作者**: Feng
- **时间**: 2026-09-20T10:01:21Z
- **提交信息**: [ckpt, trainer] fix: persist device and condition-model RNG across DiT resume (#1189)

Co-authored-by: Feng0w0 <Feng0w0@users.noreply.github.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2834
- **最后更新**: 2026-09-20T18:52:12Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 3
- **主要提交者**: Yang Yong (雍洋), Bilang ZHANG, STwangyingrui

## AI分析总结

## 1. 主要更新类型

- **性能优化**：RTX 5090 FP8 推理优化、MiniMax-H3 因果流式预热与编译、Qwen-Image-2.1 预热支持。
- **功能新增**：MiniMax-H3 因果流式 RefA2V 推理、Qwen-Image-2.1 的 T2I/I2I 优化路径。
- **兼容性对齐**：输出尺寸与 diffusers 对齐。
- **工程改进**：改用 OpenCV 保存结果。
- **文档更新**：Qwen-Image-2.1 README 多次更新。

## 2. 关键变更点与项目方向

- **RTX 5090 FP8 优化**是核心：引入 stage 级 condition-encoder CPU offload、FP8 DiT 线性推理（fp8-sgl 与 SM120 FP16 累加后端）、专用量化配置（weight qmax 14 / activation qmax 7），并推荐 dense SageAttention2。这直接服务于 LightX2V 作为“轻量视频生成推理框架”的定位——降低显存占用、提升推理速度。
- **MiniMax-H3 因果流式推理**扩展了模型覆盖面，支持 RefA2V 场景，并加入 warmup 与 compile，体现对“流式/实时生成”能力的持续投入。
- **Qwen-Image-2.1 系列**（预热、OpenCV 保存、尺寸对齐、文档）显示该模型正被系统性地打磨为稳定可用的推理路径。

## 3. 对项目的影响与潜在意义

- 显存优化与 FP8 量化使大模型在消费级旗舰 GPU（5090）上更易部署，降低使用门槛。
- 预热与 compile 支持可显著减少首次推理延迟，改善实际体验。
- 输出尺寸对齐 diffusers 提升了与主流生态的互操作性，便于用户迁移与对比。
- 流式因果推理的完善为视频生成向实时/交互场景演进奠定基础。

## 4. 值得关注的技术点

- **SM120 FP16 累加后端**：针对新架构的 FP8 累加策略，是精度与速度权衡的关键。
- **stage 级 CPU offload**：在 DiT 去噪前释放显存，属于细粒度显存调度。
- **SageAttention2/3 与动态稀疏 SLA**：作为可选激进实验，需人工评估画质，反映团队在注意力加速上的探索。
- **warmup + compile**：对推理稳定性和延迟的双重优化。

## 5. 结合项目背景的发展影响

LightX2V 定位为轻量视频生成推理框架，本批提交延续了“多模型支持 + 极致推理优化”的主线：一方面通过 FP8、CPU offload、注意力加速持续压低显存与延迟；另一方面扩展 MiniMax-H3 等模型并强化流式能力。整体上，这些更新增强了框架在高端消费级 GPU 上的实用性与竞争力，同时通过生态对齐和文档完善提升可用性，符合项目向“高效、易用、多模型”方向演进的趋势。

## 详细提交记录

### [8d0c1a5](https://github.com/ModelTC/LightX2V/commit/8d0c1a5fa7add4a76a22977675738d784bca7c65)

- **作者**: STwangyingrui
- **时间**: 2026-09-20T14:11:24Z
- **提交信息**: optimize(qwen-image-2.1): add RTX 5090 FP8 inference optimizations (#1543)

Add an optimized Qwen-Image-2.1 inference path for RTX 5090, covering
both text-to-image and image-to-image workloads.

- Add stage-level condition-encoder CPU offload to release GPU memory
before DiT denoising.
- Add FP8 DiT linear inference with both `fp8-sgl` and SM120
FP16-accumulation backends.
- Add a Qwen-Image-2.1 conversion profile using weight qmax 14 and
activation qmax 7 for FP16 accumulation.
- Use dense SageAttention2 in the recommended RTX 5090 configuration.
- Add paired T2I/I2I configs and launch scripts.
- Add optional SageAttention3 and dynamic sparse SLA configs as
aggressive experiments that require manual image-quality review.
- Document model conversion, optimized usage, and measured RTX 5090
performance.

### [4074476](https://github.com/ModelTC/LightX2V/commit/40744764aacc141166d9aa9c9596ba47ab1eab0e)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-20T12:10:56Z
- **提交信息**: feat(minimax_h3_causal): add warmup and compile support, optimize vid… (#1542)

…eo output

### [2773aec](https://github.com/ModelTC/LightX2V/commit/2773aecb5db497091aa304c322c15a1e3bbb0706)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T10:25:52Z
- **提交信息**: Use opencv for qwen-image-2.1 saving result. (#1541)

### [c83f435](https://github.com/ModelTC/LightX2V/commit/c83f43571bb79498be4ff169a96a02ea807e260e)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T10:08:55Z
- **提交信息**: Support warmup for qwen-image-2.1 (#1540)

### [d43f15f](https://github.com/ModelTC/LightX2V/commit/d43f15f769d1d1ba129caa298ca431e0b39af39b)

- **作者**: Bilang ZHANG
- **时间**: 2026-09-20T09:58:36Z
- **提交信息**: feat: support MiniMax-H3 causal streaming RefA2V inference (#1539)

### [a918b2d](https://github.com/ModelTC/LightX2V/commit/a918b2daec3a9e758bd79922f1d382a577e205d2)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T09:17:09Z
- **提交信息**: Align output sizes with diffusers for qwen-image-2.1 (#1538)

### [8b5df72](https://github.com/ModelTC/LightX2V/commit/8b5df725f7e807b3e1123da7ac49bdcbb978183a)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T08:11:21Z
- **提交信息**:  Update qwen-image-2.1 readme. (#1537)

### [2da731b](https://github.com/ModelTC/LightX2V/commit/2da731be7cd912a0fd87b26b92ec2653577da0c5)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-09-20T07:57:32Z
- **提交信息**: Update qwen-image-2.1 readme. (#1536)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2253
- **最后更新**: 2026-09-19T18:15:55Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6461
- **最后更新**: 2026-09-20T20:44:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4484
- **最后更新**: 2026-09-20T14:20:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34553
- **最后更新**: 2026-09-20T23:34:18Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
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


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13148
- **最后更新**: 2026-09-20T14:32:23Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Hong Zhang, Zhongjie Duan

## AI分析总结

# DiffSynth-Studio 昨日提交分析（第 1/1 批，共 3 条）

## 1. 主要更新类型

- **功能新增与模型适配**：核心是为 Qwen-Image 2.1 提供支持，并同步更新相关示例。
- **版本发布**：发布 v2.1.8。
- **文档更新**：随功能同步更新 README 与示例说明。
- **兼容性修复/重构**：修复 scheduler、文本编码器，并加入兼容补丁。

## 2. 关键变更点与项目方向

- 新增对 **Qwen-Image 2.1** 的支持，并复用 Qwen-Image 的 scheduler，体现项目“快速跟进主流扩散模型”的一贯方向。
- 重命名 model id、更新 `lora_target_modules`，说明在统一模型注册与 LoRA 微调接口上做了对齐。
- 加入 **compatible patch**，保证新旧行为兼容，降低升级对既有用户的破坏。
- 修复 scheduler 与 text encoder 的细节问题，属于稳定性打磨。

## 3. 对项目的影响与潜在意义

- 让 DiffSynth-Studio 能第一时间支持 Qwen-Image 2.1，保持其在多模型推理/训练框架中的竞争力。
- 复用 scheduler 与兼容补丁降低了维护成本，避免为每个新模型重复造轮子。
- 版本号推进到 2.1.8，表明这是一次常规但完整的迭代发布，用户可直接通过 PyPI 获取。

## 4. 值得关注的技术点

- **scheduler 复用策略**：新模型沿用已有调度器，是工程上“最小改动接入”的典型做法。
- **LoRA target modules 调整**：直接影响微调效果与显存占用，是训练侧用户需关注的点。
- **兼容补丁机制**：在模型行为升级时保留旧路径，是长期维护多模型框架的关键设计。
- **文本编码器修复**：文本侧问题往往影响生成质量，值得验证。

## 5. 结合 README 背景看项目发展

README 显示 DiffSynth-Studio 定位为面向扩散模型的综合工具链（推理、微调、多模型支持）。本次提交延续了其“紧跟社区新模型、快速集成”的路线：通过支持 Qwen-Image 2.1 扩展模型生态，通过复用 scheduler 和兼容补丁强化框架的可持续性。整体看，这是一次以**模型适配 + 稳定性修复 + 版本发布**为主的迭代，巩固了项目作为多模型扩散工具平台的价值，也为后续接入更多新模型积累了可复用的工程模式。

## 详细提交记录

### [d2d684a](https://github.com/modelscope/DiffSynth-Studio/commit/d2d684ad1f912949eae08453b9411ae40c5ec0ab)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-20T09:27:36Z
- **提交信息**: update to version 2.1.8 (#1696)

### [982abec](https://github.com/modelscope/DiffSynth-Studio/commit/982abec6856227c287d798b87ed761af94d924e6)

- **作者**: Zhongjie Duan
- **时间**: 2026-09-20T08:57:45Z
- **提交信息**: update Qwen-Image-2.1 examples (#1695)

### [7f31eff](https://github.com/modelscope/DiffSynth-Studio/commit/7f31effabd63310dfd43e57a0a7d08c44a437dc7)

- **作者**: Hong Zhang
- **时间**: 2026-09-20T07:54:01Z
- **提交信息**: update qwen-image-2.1 to latested behavior (#1694)

* support qwen-image2.1

* fix scheduler

* rename model id

* reuse qwen-image scheduler

* update lora_target_modules

* update readme

* add compatible patch to qwenimage2.1

* minor fix

* minor fix for text encoder

---------

Co-authored-by: Artiprocher <wangye87v5@hotmail.com>

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36218
- **最后更新**: 2026-09-21T00:09:23Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 26
- **主要提交者**: Mick, Ruiyan Ma, luoroger37

## AI分析总结

# sglang 昨日提交分析总结（37 条）

## 1. 主要更新类型分布

- **重构（sgl-router 为主）**：约 5 条，集中在路由器的模块布局、状态管理、CLI 配置与启动逻辑。
- **CI/测试基础设施**：约 8 条，是当日最大板块，涉及 kernel lane 拆分、runner 表驱动、权限、测试选择与修复。
- **功能新增**：MoE 路由（bf16/mxfp4）、rust-renderer 独立预处理、NPU 精度测试流水线、Diffusion 相关支持等。
- **Bug 修复**：NVFP4 MoE 后端调度、TopK v2 回退、HiCache 层 ID、CUDA graph 契约、Simulator 内存预算等。
- **性能优化**：mHC 注意力-MLP 边界融合、异步采样 pinned memory、专家权重 O(1) 查找、DCP 传输边界控制。
- **文档**：NPU 文档修正、Qwen-Image cookbook 简化。

## 2. 关键变更点与项目方向

- **sgl-router 系统性重构**（#40241/#40272/#39867/#39861）：将 BucketResolver、Bucket、EngineGroup 重新布局，策略状态下沉到 `src/state`，并实现 PowerOfTwo 策略。这表明路由器正从原型走向工程化、可维护的架构。
- **模型支持持续扩张**：MiMo V2、Kimi-K3、DeepSeek-V4.1、Qwen4-Exp、MiniMax-H3、SenseNova-U1 等新模型/变体密集接入，体现 sglang 作为多模型推理引擎的定位。
- **移除 swa 与 mamba radix cache**（#a8a4d86）：清理历史包袱，简化缓存体系，是架构收敛的重要信号。
- **PD 分离与 DCP/DSpark 深化**：Kimi-K3 的 pp prefill + dcp decode、AMD gfx950 上 DSpark 启用，说明分离式推理与硬件适配是核心演进方向。

## 3. 对项目的影响与潜在意义

- 路由器重构与缓存简化降低了长期维护成本，为后续策略扩展打基础。
- CI 从"复制 job 块"转向"runner 表驱动"、按注册类型派生测试种类，显著提升 CI 可扩展性与准确性，减少误报。
- 移除 radix cache 变体可能影响部分用户行为，需关注兼容性与迁移说明。
- 多项内存/传输优化（pinned memory、pack capacity 边界、meta device 构建）直接改善大模型推理的显存与吞吐表现。

## 4. 值得关注的技术点

- **PowerOfTwo 路由策略**：负载均衡的新选择。
- **meta device 构建 PLE 表**（#e97614d）：避免在加速器上实体化，是显存优化的巧妙手法。
- **O(1) 专家权重查找**（#c2c3629）：解决大 MoE 加载瓶颈。
- **prefill CUDA graph 契约保持**（#d229952）：图捕获与模型 runner 接口的兼容性难题。
- **rust-renderer 独立预处理**（#7b1c2ed）：渲染器与主流程解耦，可能指向服务化/多语言栈方向。

## 5. 结合 README 的项目发展意义

sglang 定位为高性能大模型推理服务框架，强调吞吐、多模型与部署灵活性。昨日提交整体呈现"**架构收敛 + 模型扩张 + 基础设施加固**"三条主线：路由器与缓存的重构夯实工程底座，新模型与硬件适配扩大覆盖面，CI 与内存优化保障规模化可靠性。这表明项目正从快速功能堆叠转向可持续的工程化阶段，为支撑更多生产级部署场景做准备。

## 详细提交记录

### [aedda83](https://github.com/sgl-project/sglang/commit/aedda8377e4521ec402192b3f3aaa9534175b544)

- **作者**: Kan Wu
- **时间**: 2026-09-20T23:57:07Z
- **提交信息**: [sgl-router] refactor - layout BucketResolver, Bucket, EngineGroup and implement PowerOfTwo (#40241)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [4a9dc5c](https://github.com/sgl-project/sglang/commit/4a9dc5c4af9631b658c6f9d61129f5d2ac32e500)

- **作者**: Kan Wu
- **时间**: 2026-09-20T23:49:23Z
- **提交信息**: [sgl-router] refactor - move policy-required states under src/state (#40272)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [acd20a5](https://github.com/sgl-project/sglang/commit/acd20a516ed2a3274ef574f9506939360de2ba22)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T23:46:53Z
- **提交信息**: [CI] Give the kernel lane a 5090 suite and move kernel-only tests off the general lane (#40496)

### [42875bc](https://github.com/sgl-project/sglang/commit/42875bcd2a7f2d9685eb3dd98fd787b54e3787d1)

- **作者**: Divy
- **时间**: 2026-09-20T23:28:54Z
- **提交信息**: fix(modelopt): dispatch NVFP4 MoE on the cached backend, not the live global (#38932)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [2fa6b94](https://github.com/sgl-project/sglang/commit/2fa6b94e3440d28dab7460246f0b34426a4e4b80)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T23:20:37Z
- **提交信息**: [Perf] Fuse the glm5_next mHC attn->MLP boundary (#39200)

Co-authored-by: mmangkad <mohammad.angkad@radixark.ai>

### [983e643](https://github.com/sgl-project/sglang/commit/983e643854f15cf9ef4370a49dfd74b6af54c3e3)

- **作者**: ollybbmonster
- **时间**: 2026-09-20T23:13:59Z
- **提交信息**: [Feature] support bf16 MoE router and mxfp4 MoE for MiMo V2 (#40448)

### [2e2d8a2](https://github.com/sgl-project/sglang/commit/2e2d8a2fda5c3bb9a8f62601679bfc2b18ec67d6)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T22:43:46Z
- **提交信息**: [CI] Drive per-commit stage jobs from a runner table instead of copied job blocks (#40495)

### [d97aed2](https://github.com/sgl-project/sglang/commit/d97aed2c908df22a68bc9b787395f1836970eee3)

- **作者**: luoroger37
- **时间**: 2026-09-20T22:41:41Z
- **提交信息**: Fix TopK v2 fallback when 16-block cluster capacity is zero (#40163)

Co-authored-by: Hank Han <hanhan7630@outlook.com>

### [f31a7bd](https://github.com/sgl-project/sglang/commit/f31a7bd45c6ab86796aa012ebfd2378bc42e1a59)

- **作者**: Yuxuan Zhang
- **时间**: 2026-09-20T22:31:31Z
- **提交信息**: Use pinned memory for asynchronous sampling metadata transfers (#39777)

Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [95521da](https://github.com/sgl-project/sglang/commit/95521da18df4780e9c63f5e2ddd284ecd9ca9b1c)

- **作者**: Harmya Bhatt
- **时间**: 2026-09-20T21:43:19Z
- **提交信息**: [DeepSeek-V4.1] Bound dense prefill indexer memory (#40217)

### [c2c3629](https://github.com/sgl-project/sglang/commit/c2c3629f2dc0d4fa9386e90ea1a63e6ed5d50580)

- **作者**: JinYan Su
- **时间**: 2026-09-20T21:39:45Z
- **提交信息**: [Kimi-K3] O(1) expert weight lookup in load_weights (#38805)

Signed-off-by: JinYan Su <751080330@qq.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [f6483e4](https://github.com/sgl-project/sglang/commit/f6483e479fc7de2ee67230f6004722966bfe71bf)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T21:36:02Z
- **提交信息**: [Test] Drop cause-less disabled tests, fix XPU lane, demote quality gates off base-c (#40288)

### [d229952](https://github.com/sgl-project/sglang/commit/d229952e25b4df459e7d9bf74336717e3883e906)

- **作者**: Aurick Qiao
- **时间**: 2026-09-20T20:53:14Z
- **提交信息**: [Fix] Preserve model runner contracts in prefill CUDA graphs (#35452)

Co-authored-by: Oasis-Git <ayw.sirius19@gmail.com>
Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [745de73](https://github.com/sgl-project/sglang/commit/745de73ba3c136b6f99b7a3e2177ed1a8eef4a56)

- **作者**: Shangming Cai
- **时间**: 2026-09-20T17:37:50Z
- **提交信息**: Add CODEOWNERS entry for sglang-renderer (#40483)

### [b3e4d19](https://github.com/sgl-project/sglang/commit/b3e4d198af5e74e5070e541475fd767302342be9)

- **作者**: Khoa Pham
- **时间**: 2026-09-20T17:17:15Z
- **提交信息**: [PD] Bound cached-prefix DCP transfers by pack capacity (#40376)

### [80da443](https://github.com/sgl-project/sglang/commit/80da4432d085ed4d6166ef643d9fd2b829dbb0c5)

- **作者**: Shuwen Wang
- **时间**: 2026-09-20T16:42:55Z
- **提交信息**: [Simulator] Fix meta host memory budgets on constrained runners (#40440)

### [3dbdd70](https://github.com/sgl-project/sglang/commit/3dbdd700e2e99460cb5aa3e1da1b7567b96ef7d7)

- **作者**: WenhaoZhang
- **时间**: 2026-09-20T16:07:37Z
- **提交信息**: [CI] update CI permissions (#40474)

### [e97614d](https://github.com/sgl-project/sglang/commit/e97614d10c8e2c90a72387276086dc33f21bba67)

- **作者**: Jimmy Shong
- **时间**: 2026-09-20T15:28:25Z
- **提交信息**: [Qwen4-Exp] Build the offloaded PLE table on the meta device so --ple-offload-embedding never materialises it on the accelerator (#39928)

Co-authored-by: Yangmin Li <yangminl@nvidia.com>

### [5f017ff](https://github.com/sgl-project/sglang/commit/5f017ffabb6ab8d214f6a4616ee8bd98a376034a)

- **作者**: ZY Y
- **时间**: 2026-09-20T14:42:00Z
- **提交信息**: Update test cases and performance testing framework (#40392)

### [404dee1](https://github.com/sgl-project/sglang/commit/404dee10c040daa6e58d75dba98ae020d5f4acdd)

- **作者**: chenyang08056032
- **时间**: 2026-09-20T14:40:55Z
- **提交信息**: [NPU] add coverage-based precision test selection pipeline (#38339)

### [8923f4d](https://github.com/sgl-project/sglang/commit/8923f4d779b54ff8e0103ea80179311c6a3c3cb3)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T14:39:34Z
- **提交信息**: [Test] Fix optimistic prefill disaggregation test after mamba radix cache removal (#40469)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [791c785](https://github.com/sgl-project/sglang/commit/791c7850d0960fd768102f71e7d999b036bb75ba)

- **作者**: faceless void
- **时间**: 2026-09-20T14:08:02Z
- **提交信息**: [Diffusion] Enable shared RMSNorm dispatch for SenseNova-U1 (#39705)

Signed-off-by: syd520zy <529477025@qq.com>
Co-authored-by: ronnie_zheng <zl19940307@163.com>

### [7b1c2ed](https://github.com/sgl-project/sglang/commit/7b1c2ed0a423718492069a56db48bd451b5ec994)

- **作者**: Sage
- **时间**: 2026-09-20T14:03:12Z
- **提交信息**: [rust-renderer] Standalone preprocessing (#36718)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>
Co-authored-by: Rain Jiang <96632942+rainj-me@users.noreply.github.com>

### [6880a47](https://github.com/sgl-project/sglang/commit/6880a4795533640f41ebb3db9e4ae0af5a371a1f)

- **作者**: Mick
- **时间**: 2026-09-20T12:39:26Z
- **提交信息**: [diffusion] docs: simplify Qwen-Image 2.1 cookbook (#40455)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [c610c40](https://github.com/sgl-project/sglang/commit/c610c403990255e6ffe41d7314f6fb748a53085f)

- **作者**: Kan Wu
- **时间**: 2026-09-20T11:40:04Z
- **提交信息**: [sgl-router] refactor - config and organize CLI options (#39867)

### [efa7be2](https://github.com/sgl-project/sglang/commit/efa7be2091282e96318f0d9d22d9f78dde099848)

- **作者**: Ruiyan Ma
- **时间**: 2026-09-20T10:00:06Z
- **提交信息**: [Simulator][Compatibility] Adapt to latest KV cache pool interfaces (#40418)

### [0024efa](https://github.com/sgl-project/sglang/commit/0024efa0de38794ee309ba10ab00ebb891a3d050)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T09:01:22Z
- **提交信息**: [CI] Derive registered-test kind from the registry call instead of the path (#40294)

### [671630a](https://github.com/sgl-project/sglang/commit/671630abf1b783cafcfc9277f7afdc3f56abc338)

- **作者**: Kan Wu
- **时间**: 2026-09-20T08:55:34Z
- **提交信息**: [sgl-router] refactor - main startup logic (#39861)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [2a0cb2f](https://github.com/sgl-project/sglang/commit/2a0cb2f04edbd85778f1fb8c26272c7f668d9c34)

- **作者**: HuangJi
- **时间**: 2026-09-20T08:40:28Z
- **提交信息**: [Diffusion][MiniMax-H3] Add SM120 Sage compute for SubBlock sparse attention (#40116)

### [414adef](https://github.com/sgl-project/sglang/commit/414adef060f41977e3a4888cdb35cb0b1f4b8858)

- **作者**: Mick
- **时间**: 2026-09-20T08:33:23Z
- **提交信息**: [CI] skip srt rust extension builds for diffusion-only PRs (#40293)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [dc002c8](https://github.com/sgl-project/sglang/commit/dc002c85fcc94b8b145207d6bfbd57d60a3113f5)

- **作者**: Liangsheng Yin
- **时间**: 2026-09-20T08:25:34Z
- **提交信息**: [Test] Fix OOT DFlash hook test resolving the draft config over the network (#40427)

### [9f3d275](https://github.com/sgl-project/sglang/commit/9f3d2759407f2e3b9c097b41f90ddac3a499beb5)

- **作者**: Shuwen Wang
- **时间**: 2026-09-20T08:24:24Z
- **提交信息**: [HiCache] Fix sparse hybrid transfer layer IDs (#37870)

Co-authored-by: Seokhoon Kang <sh.kang@postech.ac.kr>

### [e540092](https://github.com/sgl-project/sglang/commit/e54009240a84bf52eb7a21ec532ea49f1b9dd941)

- **作者**: amd-danli103
- **时间**: 2026-09-20T08:16:39Z
- **提交信息**: [AMD][DSV4] feat: enable DSpark with fp8 unified_kv on gfx950 (#38901)

Co-authored-by: HAI <hixiao@gmail.com>

### [a8a4d86](https://github.com/sgl-project/sglang/commit/a8a4d86be9f483fabd097350b06b6ae6e6905874)

- **作者**: Ke Bao
- **时间**: 2026-09-20T08:16:27Z
- **提交信息**: Remove swa and mamba radix cache (#40313)

### [5c69e32](https://github.com/sgl-project/sglang/commit/5c69e32abe013fa1b913022682a3104c79105f37)

- **作者**: amote-i
- **时间**: 2026-09-20T07:15:58Z
- **提交信息**: [NPU] [DOC] fix typos, heading levels and terminology in NPU docs (#40402)

### [f4c2563](https://github.com/sgl-project/sglang/commit/f4c256354cc8a15d18b11f970f01a82d7394a715)

- **作者**: Qiaolin Yu
- **时间**: 2026-09-20T07:15:28Z
- **提交信息**: [kimi k3][pd disagg] support pp prefill + dcp decode with dspark (#40045)

### [22f02cc](https://github.com/sgl-project/sglang/commit/22f02cc3399dcd59380fc546de8d3c89fba6fa3a)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-09-20T07:08:04Z
- **提交信息**: [Test] Fix scheduler fixtures after prefill burst counting (#40411)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1283
- **最后更新**: 2026-09-20T17:40:48Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 92259
- **最后更新**: 2026-09-21T00:13:25Z

## 提交统计

- **昨日提交总数**: 17
- **提交者数量**: 15
- **主要提交者**: Wentao Ye, Chauncey, Misha Goin

## AI分析总结

# vLLM 昨日提交分析总结（共17条）

## 1. 主要更新类型分布

- **Bug修复**：5条（XPU UT精度问题、GLM-5.3-Flash kpool索引、KV Offload跳过不可缓存组、前端多模态扩展后prompt边界、ROCm CI显存查询）
- **功能新增**：4条（Humming集成、DSV4.1编码器CUDA Graph、MiMo V2的bf16 MoE路由与mxfp4、前端per-request投机解码指标）
- **性能优化**：3条（GLM kpool尾部槽位Triton融合、ROCm FP8 WO_A输出投影、Marlin/Humming持久化工作区共享）
- **重构/清理**：2条（移除死内核代码、重命名mamba细粒度前缀缓存参数）
- **KV连接器/模型支持**：3条（MoRIIO混合mamba/KDA状态READ模式、VoyageQwen3 LoRA、GLM-5.3-Flash稀疏索引调度）

## 2. 关键变更点与项目方向

- **多硬件后端持续深化**：XPU、ROCm、NVIDIA三线并进，ROCm侧既有CI稳定性修复又有FP8性能优化，体现vLLM“跨平台高效服务”的核心定位。
- **新模型快速适配**：GLM-5.3-Flash、DeepSeek-V4.1、MiMo V2、VoyageQwen3等密集落地，说明项目紧跟前沿模型生态，保持“开箱即用”的竞争力。
- **KV缓存与稀疏注意力架构演进**：MoRIIO混合状态传输、kpool尾部索引修复、SparseIndexerTopk统一调度，指向长上下文与混合架构推理的工程化深耕。
- **Humming特性集成与工作区共享**：新特性引入同时复用Marlin持久化工作区，体现性能与内存效率并重的设计取向。

## 3. 对项目的影响与潜在意义

- 修复类提交直接提升XPU/ROCm/GLM等场景的**数值正确性与CI可靠性**，降低用户踩坑概率。
- Humming集成与Marlin工作区共享可能带来**显存占用下降与吞吐提升**，对大规模部署有实际价值。
- 前端暴露per-request投机解码指标，增强**可观测性**，利于用户调优与问题定位。
- 移除死代码与参数重命名改善**可维护性**，为后续迭代减负。

## 4. 值得关注的技术点

- **MoRIIO READ模式传输混合mamba/KDA循环状态**：KV连接器对非Transformer架构的支持是关键扩展。
- **GLM-5.3-Flash kpool尾部槽位的Triton融合与stride寻址修复**：涉及稀疏注意力内核的精细正确性。
- **Humming + Marlin持久化工作区共享**：跨内核复用workspace是显存优化的新思路。
- **DSV4.1编码器CUDA Graph支持**：将图捕获扩展到编码器路径，有望降低调度开销。

## 5. 结合README背景的项目发展影响

vLLM定位为“Easy, fast, and cheap LLM serving for everyone”。本批提交从三个维度强化该目标：**广度**上通过多硬件（XPU/ROCm）与新模型适配扩大可用范围；**速度**上以Triton融合、FP8投影、工作区共享持续压低延迟与显存；**易用性**上通过前端指标暴露与Bug修复提升稳定性。整体看，项目正从“支持主流Transformer模型”向“覆盖混合架构、稀疏注意力与多厂商硬件”的通用推理引擎演进，生态护城河进一步加深。

## 详细提交记录

### [17e50b9](https://github.com/vllm-project/vllm/commit/17e50b9b761023d5f2499f062507df1ff49092a4)

- **作者**: YiSheng5
- **时间**: 2026-09-20T22:50:25Z
- **提交信息**: [XPU][UT]Bugfix when the process can't see all the world_size meet accuracy issue. (#57779)

Signed-off-by: yisheng <yi.sheng@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [9679173](https://github.com/vllm-project/vllm/commit/96791737887224c8bfec0a791517759f62e4d93b)

- **作者**: YukioZzz
- **时间**: 2026-09-20T21:30:34Z
- **提交信息**: [KVConnector][MoRIIO] Transfer hybrid mamba/KDA recurrent state in READ mode (#51052)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>

### [01f1f58](https://github.com/vllm-project/vllm/commit/01f1f58f10c616850a5f5ade129a7b58d62075fb)

- **作者**: Sheral Kumar
- **时间**: 2026-09-20T20:20:39Z
- **提交信息**: [ROCm][CI] Query HIP device memory for test GPU teardown waits. (#57450)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Signed-off-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Andreas Karatzas <Andreas.Karatzas@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [4868312](https://github.com/vllm-project/vllm/commit/4868312128172a424a7cf4c90f25c53b49186346)

- **作者**: Wentao Ye
- **时间**: 2026-09-20T17:39:23Z
- **提交信息**: [Refactor] Remove dead kernel code (#57621)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [49ee12d](https://github.com/vllm-project/vllm/commit/49ee12d742b4a5524d2a3a3ee6c3fb77e4913073)

- **作者**: roikoren755
- **时间**: 2026-09-20T16:50:34Z
- **提交信息**: [Misc] Rename --enable-mamba-fine-grained-prefix-cache (#53945 follow-up) (#57382)

Signed-off-by: Roi Koren <roik@nvidia.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [7d99c2c](https://github.com/vllm-project/vllm/commit/7d99c2c4fd61cdeebd29cc7b60584bad10d1ef99)

- **作者**: Jinzhen Lin
- **时间**: 2026-09-20T15:11:01Z
- **提交信息**: [Feature][Humming] Humming feature integration (#56685)

Signed-off-by: jinzhen.ljz <jinzhen.ljz@antgroup.com>
Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mgoin <mgoin64@gmail.com>

### [27757dd](https://github.com/vllm-project/vllm/commit/27757dde020ecda4f9b0e2c5ca2df1c29badc82f)

- **作者**: Isotr0py
- **时间**: 2026-09-20T13:51:13Z
- **提交信息**: [DSV4.1] Add encoder cuda graph support for deepseek-v4.1-flash (#56625)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>

### [9b2f34c](https://github.com/vllm-project/vllm/commit/9b2f34cad446f73b1699e8236ec0b611a65f48af)

- **作者**: Zyann
- **时间**: 2026-09-20T13:25:56Z
- **提交信息**: [Feature] support bf16 MoE router and mxfp4 MoE for MiMo V2 (#57784)

Signed-off-by: Zyann7 <62597503+Zyann7@users.noreply.github.com>
Co-authored-by: Abatom <182586866+Abatom@users.noreply.github.com>

### [10e6a7f](https://github.com/vllm-project/vllm/commit/10e6a7f21094b76c65efb029b39b3f2227516418)

- **作者**: Hongxin Xu
- **时间**: 2026-09-20T12:21:33Z
- **提交信息**: [Frontend] Expose per-request spec decode metrics in generate API (#43310)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Codex <codex@openai.com>

### [bf01fc4](https://github.com/vllm-project/vllm/commit/bf01fc4a313cc90863c470f37a26e41fd7b16fd1)

- **作者**: Chauncey
- **时间**: 2026-09-20T11:17:59Z
- **提交信息**: [GLM-5.3-Flash] Route kpool indexer top-k through the shared   SparseIndexerTopk dispatcher (#57546)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [f648eed](https://github.com/vllm-project/vllm/commit/f648eed23dc48fcc8ba64be0c4182f8e775b5bfa)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:58:55Z
- **提交信息**: [Bugfix][KV Offload] Skip non-prefix-cacheable groups in SimpleCPUOffload (GLM-5.3-Flash kpool tail and QSA) (#56810)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Zhewen Li <zhewenli@inferact.ai>

### [1b9fa3e](https://github.com/vllm-project/vllm/commit/1b9fa3eaa8ff23d1a583f2f77dd2b33c9f896ee8)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:20:55Z
- **提交信息**: [Perf][GLM] Fuse the kpool tail slot mapping into one Triton kernel (#57534)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [db1bfdd](https://github.com/vllm-project/vllm/commit/db1bfdd4fb0dd7b8226402ee00abc7a987561b7c)

- **作者**: Jared Wen
- **时间**: 2026-09-20T10:15:04Z
- **提交信息**: [Bugfix][GLM-5.3-Flash] Address kpool tail blocks by the padded indexer stride in the NVIDIA prefill seed kernel (#57477)

Signed-off-by: Jared Wen <w13431838023@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0748d3b](https://github.com/vllm-project/vllm/commit/0748d3bd57cb5c4303e58c8465e21f069629480d)

- **作者**: mahird3
- **时间**: 2026-09-20T09:50:00Z
- **提交信息**: [Model][LoRA] Enable LoRA support for VoyageQwen3BidirectionalEmbedModel (#57708)

Signed-off-by: Mahir Dursunoglu <142054011+mahird3@users.noreply.github.com>

### [e5fce7b](https://github.com/vllm-project/vllm/commit/e5fce7b56b07cdf992febd0862bfd599d6dca3fd)

- **作者**: Misha Goin
- **时间**: 2026-09-20T09:28:33Z
- **提交信息**: [Core][Kernel] Share persistent workspaces for Marlin and Humming (#57421)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: ErinYin <liang.yin@daocloud.io>

### [0e110f6](https://github.com/vllm-project/vllm/commit/0e110f696db450f5645ce1daf9945241212d6ef3)

- **作者**: yinfengLiu
- **时间**: 2026-09-20T09:13:55Z
- **提交信息**: [ROCm][DSV4][Perf] Use FP8 WO_A output projection (#54894)

Signed-off-by: Liuyinfeng01 <yinfeliu@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [27b7757](https://github.com/vllm-project/vllm/commit/27b7757f6364be5b0b714793ccdc3e3931443bca)

- **作者**: Dilber
- **时间**: 2026-09-20T08:52:27Z
- **提交信息**: [Bugfix][Frontend] Bound the prompt after multimodal expansion (#57076)

Signed-off-by: Dilber P Shakir <dilbersha@gmail.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-09-21
**监控日期**: 2026-09-20
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 6940
- **最后更新**: 2026-09-20T23:06:32Z

## 提交统计

- **昨日提交总数**: 13
- **提交者数量**: 13
- **主要提交者**: amy-why-3459, tlysanhuo, 汪志鹏

## AI分析总结

# vllm-omni 昨日提交分析总结

## 1. 主要更新类型

本批 13 个提交以 **Bugfix（5 个）** 和 **功能新增（4 个）** 为主，辅以 **性能优化（2 个）**、**重构（1 个）** 和 **Benchmark 扩展（1 个）**，另有一次功能移除。整体呈现“修复稳定性 + 拓展多模态能力”的双主线。

## 2. 关键变更点与项目方向

- **性能与硬件适配**：MOSS-TTS 编解码流式解码接入 NPUGraph（#7280），并在 Ascend 上改用增量 KV-cache 解码深度 Transformer（#6967），强化昇腾平台推理效率。
- **多模态生成能力扩展**：新增扩散流式生成的相机交互（LingBot World 2，#7198）、MiniMax-H3 长视频潜变量续接与驱动音频（#7838），以及 AR→DiT 的原生 Mooncake KV 传输（#7166），推动“全模态服务”向视频/音频/扩散统一调度演进。
- **稳定性修复**：修复 HunyuanImage3 文本聊天路由、Qwen3-Omni 实时播放中断、HEVC 解码挂起（改用 PyAV）、MOSS 批次释放与波形 GC 扫描、VoxCPM2 请求级种子等问题。
- **架构整理**：将单模型层移入各自模型目录（#5908），提升代码可维护性；移除 Dynin-Omni 与 dots.tts 支持（#7655），聚焦核心模型。

## 3. 对项目的影响与潜在意义

- 修复类提交直接提升多模型在线服务的**稳定性与资源回收效率**，减少长时运行的内存泄漏与解码卡死风险。
- 相机交互与长视频续接等新功能，使 vllm-omni 从“文本+语音”向**世界模型/视频生成**场景延伸，契合“omni-modality serving”定位。
- Mooncake KV 传输打通 AR 与 DiT 之间的缓存复用，为**异构模型流水线**提供基础设施。
- 移除冷门模型支持，体现项目在快速迭代中**收敛维护面**、集中资源于主流模型的策略。

## 4. 值得关注的技术点

- NPUGraph 捕获流式解码：图捕获与动态流式输出的结合是昇腾性能优化的关键难点。
- AR→DiT 的 KV 传输：跨模型架构的缓存迁移，可能成为多阶段生成的标准范式。
- PyAV 替代 ffmpeg 子进程：规避 HEVC 解码挂起，反映多媒体依赖治理思路。
- 请求级种子在 CFM 噪声中的落实：对生成可复现性至关重要。

## 5. 结合 README 的项目发展影响

README 强调“Easy, fast, and cheap omni-modality model serving”。本批提交一方面通过 NPUGraph、增量 KV-cache、Mooncake 传输落实 **fast/cheap**；另一方面通过视频、音频、扩散交互扩展 **omni** 边界；同时以密集 Bugfix 保障 **easy** 的稳定体验。整体看，项目正从多模态推理框架向**跨模型、跨硬件、跨模态的统一服务引擎**稳步演进。

## 详细提交记录

### [ae3880f](https://github.com/vllm-project/vllm-omni/commit/ae3880f0e39df4ba7376481ae78d9269fc42e09c)

- **作者**: Wallbreazzz
- **时间**: 2026-09-20T22:38:23Z
- **提交信息**: [Performance] Capture MOSS-TTS codec streaming decode with NPUGraph (#7280)

Signed-off-by: Wallbreazzz <110282866+Wallbreazzz@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Gao Han <hgaoaf@connect.ust.hk>

### [e36babd](https://github.com/vllm-project/vllm-omni/commit/e36babd48ff2eee3443c16166b1a6890e62e44e0)

- **作者**: Zeyu Huang | 黃澤宇
- **时间**: 2026-09-20T16:19:41Z
- **提交信息**: [Core][Diffusion] Camera interaction for diffusion streaming generation (LingBot World 2 as example) (#7198)

Signed-off-by: Huang, Zeyu <11222265+fhfuih@users.noreply.github.com>

### [139a47a](https://github.com/vllm-project/vllm-omni/commit/139a47a578e01eb7cd4a0c3d35a02eba4b4ded6a)

- **作者**: 汪志鹏
- **时间**: 2026-09-20T15:44:33Z
- **提交信息**: [Model] Add MiniMax-H3 long-video latent continuation with driving audio (#7838)

Signed-off-by: princepride <wangzhipeng628@gmail.com>

### [16734bb](https://github.com/vllm-project/vllm-omni/commit/16734bbdf3850bc7407bafb3484de613a73efd84)

- **作者**: DanaerLee
- **时间**: 2026-09-20T15:23:53Z
- **提交信息**: [Bugfix] Route text-only chat as per-request comprehension in HunyuanImage3 AR sampler (#6111)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>

### [102ba71](https://github.com/vllm-project/vllm-omni/commit/102ba716bf814cfeb77624157e14ad73f49c658b)

- **作者**: Wu JIAZHEN
- **时间**: 2026-09-20T14:44:55Z
- **提交信息**: [Feat] Add native Mooncake KV transfer from AR to DiT (#7166)

Signed-off-by: asukaqaq-s <1311722138@qq.com>
Signed-off-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: Acerak01-fy <wfy2003324@163.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2d0b03f](https://github.com/vllm-project/vllm-omni/commit/2d0b03f717e96fc8030859dcadbf96e7f8ea8145)

- **作者**: psv666
- **时间**: 2026-09-20T14:42:17Z
- **提交信息**: [Bugfix] Fix Qwen3-Omni realtime playback interruption and conversation history (#7791)

Signed-off-by: psv666 <2693925048@qq.com>

### [d3396fc](https://github.com/vllm-project/vllm-omni/commit/d3396fc5fb16c9b4de6c8fb9ed0f67cc732b7af2)

- **作者**: RyanYun09
- **时间**: 2026-09-20T14:37:09Z
- **提交信息**: # [Bugfix] Replace ffmpeg subprocess with PyAV to avoid HEVC decoder hang (#7364) (#7504)

Signed-off-by: RyanYun09 <318555231+RyanYun09@users.noreply.github.com>

### [4d87778](https://github.com/vllm-project/vllm-omni/commit/4d877780d38cbf93e273aef73e99a100d38e2768)

- **作者**: Canlin Guo
- **时间**: 2026-09-20T12:36:52Z
- **提交信息**: [Bugfix] Avoid waveform-list GC scans and release completed MOSS batches (#7885)

Signed-off-by: Canlin Guo <canlinguosdu@gmail.com>

### [23f4126](https://github.com/vllm-project/vllm-omni/commit/23f41264456684c793283502f811aab7dcda2c88)

- **作者**: jingchengtian
- **时间**: 2026-09-20T10:34:25Z
- **提交信息**: [Hardware][Ascend] Use incremental KV-cache decode for MOSS-TTS depth transformer (#6967)

Signed-off-by: jingchengtian <tjc1995@126.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [d02681b](https://github.com/vllm-project/vllm-omni/commit/d02681bf01a5d9d1608570aff958dfb15e2bbf8e)

- **作者**: Alicia
- **时间**: 2026-09-20T10:19:24Z
- **提交信息**: [Refactor][Diffusion] Move single-model layers into their model directories (#5908)

Signed-off-by: congw729 <115451386+congw729@users.noreply.github.com>
Signed-off-by: Alicia <115451386+congw729@users.noreply.github.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [9f55213](https://github.com/vllm-project/vllm-omni/commit/9f5521351e4471d6538e74ca66cb63cde23b9140)

- **作者**: amy-why-3459
- **时间**: 2026-09-20T09:15:53Z
- **提交信息**: [Benchmark][MiniCPM-o] Port Video-MME dataset support to Omni bench s… (#6987)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ea62f86](https://github.com/vllm-project/vllm-omni/commit/ea62f86718a4e0e0004a3daf18b033b940c0ada0)

- **作者**: tlysanhuo
- **时间**: 2026-09-20T08:24:38Z
- **提交信息**: [Bugfix] Honor request-level seed in VoxCPM2 CFM noise (#7866)

Signed-off-by: tly <2200895168@qq.com>

### [6a03e45](https://github.com/vllm-project/vllm-omni/commit/6a03e45c340a60553884432ff4fc4a31a6219d55)

- **作者**: wangyu
- **时间**: 2026-09-20T07:28:29Z
- **提交信息**: [Misc] Remove Dynin-Omni and dots.tts support (#7655)

Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

---
