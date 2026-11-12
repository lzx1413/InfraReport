# GitHub Stars 合并报告 - 2026-11-11

**合并日期**: 2026-11-12
**监控日期**: 2026-11-11
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


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2289
- **最后更新**: 2026-11-11T10:39:54Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Coach257, Zeren Chen, LeoCristallo

## AI分析总结

## VeOmni 昨日提交总结

### 1. 主要更新类型
以**功能新增**与**Bug修复**为主，辅以**性能优化**和**重构**，另有一项CI工作流修复。6个提交中3个是新功能（Bagel支持、视觉指令微调），2个是修复（分布训练、掩码统一），1个是性能重构（MoE内核），1个是CI配置修复。

### 2. 关键变更点及与项目方向的关系
- **多模态模型扩展**：提交#1402为SeedOmni新增Bagel模型支持，#1429通过组合Qwen3与Qwen3-VL ViT实现视觉指令微调——这两项直接服务于VeOmni"Scaling Any Modality Model Training"的核心目标，扩展了模型配方库（Recipe Zoo）的覆盖面，使框架能训练更丰富的多模态模型组合。
- **分布式训练稳定性**：#1391将Gloo进程组默认改为CPU，修复分布式训练中的潜在问题；#1443修复自动打标签工作流。这些提升了训练基础设施的可靠性。
- **推理与算子正确性**：#1410统一了packed causal与sliding-window掩码的实现，消除模型中不同注意力模式的不一致性。
- **性能优化**：#1323收紧了合并MoE同NK形状的launch边界，优化GPU内核调度效率。

### 3. 对项目的影响和潜在意义
- **功能层面**：新模型支持和视觉指令微调能力使VeOmni从"能训多模态"向"能训更先进多模态配方"迈进，增强了对下游研究和应用的支撑力。
- **稳定性层面**：分布式和掩码修复降低了用户在复杂训练场景下的踩坑概率，对开源项目的口碑和采用率有直接正面影响。
- **性能层面**：MoE内核优化对大规模MoE模型训练的吞吐量有实际收益，与项目"分布式配方"定位高度契合。

### 4. 值得关注的技术点
- **Qwen3 + Qwen3-VL ViT组合**：体现了VeOmni"模型为中心"的组合式设计理念——用配方拼装出新模型，而非从零构建，这是框架方法论的一次成功实践。
- **掩码统一修复**：涉及causal与sliding-window注意力混合使用时的正确性，这类隐蔽Bug在长序列或多模态训练中影响深远。
- **MoE同NK边界收紧**：针对GEMM合并调度的精细优化，反映项目在算子级性能调优上的持续投入。
- 部分提交由**Cursor AI协作**完成（2/6），值得关注AI辅助开发在核心基础设施项目中的应用趋势。

### 5. 对项目发展的整体影响
结合README定位，VeOmni致力于提供"模型为中心的分布式配方库"来支撑任意模态的模型训练。本次提交中，Bagel支持与视觉指令微调直接扩充了**配方库的内容广度**；分布式修复与掩码统一保障了**训练基础设施的健壮性**；MoE性能优化提升了**大规模训练的效率**。三者分别对应"能训什么"、"训得稳不稳"、"训得快不快"三个维度，整体推动项目向更成熟、更易用的多模态训练平台演进，与论文中展示的规模化训练能力形成呼应，有利于吸引更多研究者和工程师采用该框架。

## 详细提交记录

### [95f93e3](https://github.com/ByteDance-Seed/VeOmni/commit/95f93e35f6ca5fae0b2994203a86b15b73e6a66b)

- **作者**: Coach257
- **时间**: 2026-11-11T09:39:48Z
- **提交信息**: [ci] fix: define action and target in the issue branch of auto-label workflow (#1443)

### [e5b027c](https://github.com/ByteDance-Seed/VeOmni/commit/e5b027cc6986337025c3afc27c54a0864a37e3ac)

- **作者**: YLlllllllllll
- **时间**: 2026-11-11T07:53:06Z
- **提交信息**: [dist] fix: choose CPU for default Gloo process group (#1391)

### [19e3d3d](https://github.com/ByteDance-Seed/VeOmni/commit/19e3d3dd45c2a494152332541bc099b6ad86affc)

- **作者**: Zeren Chen
- **时间**: 2026-11-11T07:49:15Z
- **提交信息**: [omni, model, ops, ckpt, config, docs] feat: support Bagel in SeedOmni (#1402)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [bf1338c](https://github.com/ByteDance-Seed/VeOmni/commit/bf1338c1f58b608dd8d8eeba683d431883c4c022)

- **作者**: Coach257
- **时间**: 2026-11-11T07:35:15Z
- **提交信息**: [omni, model, config, docs] feat: visual instruction tuning by composing Qwen3 with the Qwen3-VL ViT (#1429)

### [bef2986](https://github.com/ByteDance-Seed/VeOmni/commit/bef298642eafca027148b68336cc0892dd4b28d5)

- **作者**: LeoCristallo
- **时间**: 2026-11-11T04:26:33Z
- **提交信息**: [ops, perf] refactor: tighten merged MoE same-NK launch bounds (#1323)

### [777f7ae](https://github.com/ByteDance-Seed/VeOmni/commit/777f7ae596046b7b6ff2ff29e876547094c90bd5)

- **作者**: Zeren Chen
- **时间**: 2026-11-11T04:17:13Z
- **提交信息**: [model, ops] fix: unify packed causal and sliding-window masks in mask_utils (#1410)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3001
- **最后更新**: 2026-11-11T17:59:06Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 3
- **主要提交者**: Yang Yong (雍洋), Bilang ZHANG, Youyang Qu

## AI分析总结

# LightX2V 昨日提交分析（8 条记录）

## 1. 主要更新类型

- **功能新增**（占比最高）：MiniMax-H3 相关支持（图像生成、INT8 推理、VAE 编译、流式推理）、OpenCV 图像保存
- **Bug 修复/环境清理**：移除 CUDA compat 依赖设置
- **配置与文档更新**：配置文件、启动脚本及 README 图片同步更新

## 2. 关键变更点及与项目方向的关系

- **MiniMax-H3 全面支持**是本轮核心主线，涵盖四层递进：
  - `#1690`：基础图像生成支持（h3 image）
  - `#1672`：MPS 平台上的 INT8 量化推理，扩展硬件覆盖面
  - `#1694`：VAE 编译优化，提升图像生成管线效率
  - `#1692`：causal v0.1 流式推理，支持 RefA2AV/RefA2V 参考驱动场景——这是视频生成中参考图/参考视频条件生成的重要能力
- 这些变更直接呼应项目定位——"轻量视频生成推理框架"，通过量化、编译、流式推理持续压低推理成本。
- `#1691` 的 OpenCV 图像保存是通用基础设施改进，服务于多模态输出场景。
- `#1693` 移除 CUDA compat 设置属于依赖精简，与"轻量"理念一致。

## 3. 对项目的影响和潜在意义

- 项目对 MiniMax-H3 生态的支持从"能跑"演进到"跑得快、跑得省、场景全"，形成了完整的部署闭环。
- INT8 + VAE 编译的组合可显著降低显存与延迟，有利于消费级 GPU 部署，扩大用户群体。
- 流式（streaming）推理支持意味着可以面向实时或低延迟交互场景，是产品化的重要一步。
- 配置和 README 的持续同步说明团队重视开箱即用体验。

## 4. 值得关注的技术点

- **MPS 平台 INT8 推理**：Apple Silicon 上的量化推理相对少见，值得关注其实现方式与精度取舍。
- **VAE 编译**：推测利用 torch.compile 或类似技术加速解码，是视频生成中常见的性能瓶颈。
- **causal v0.1 流式推理**：因果注意力结构下的流式生成，涉及 KV 缓存管理与帧间一致性，技术难度较高。
- **依赖瘦身**：移除 CUDA compat 说明项目在简化环境配置，降低用户安装门槛。

## 5. 对项目发展的综合影响

基于 README 可知，LightX2V 的目标是提供轻量、跨平台的视频生成推理框架，并配套完善的中英文文档。本轮提交表明项目正处于**快速扩展模型支持矩阵**的阶段：以 MiniMax-H3 为切入点，同时打磨性能（量化、编译）、扩展场景（流式、参考生成）、完善工程细节（配置、保存、依赖）。这些工作将强化其"轻量推理"的核心卖点，推动项目从研究导向的推理框架向可落地的生产级工具演进，也为后续接入更多模型积累了可复用的优化模式。

## 详细提交记录

### [5c02db8](https://github.com/ModelTC/LightX2V/commit/5c02db82c8dcaad0165f70ae13dc12c4a733a4a4)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-11T15:03:46Z
- **提交信息**: update h3 image readme (#1696)

### [5450e2e](https://github.com/ModelTC/LightX2V/commit/5450e2ef0e1ec772a9c3b4045fc0d9039de0f89e)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-11T14:51:55Z
- **提交信息**: update configs and bash (#1695)

### [220a9e7](https://github.com/ModelTC/LightX2V/commit/220a9e735c24b747c8f6f7f8992476def6f310d8)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-11T13:49:08Z
- **提交信息**: Support vae compile for h3 image and update readme (#1694)

### [7d9cd35](https://github.com/ModelTC/LightX2V/commit/7d9cd357919478ee6f26b85f814595d6c3c06425)

- **作者**: Youyang Qu
- **时间**: 2026-11-11T12:55:17Z
- **提交信息**: feat(mps): add MiniMax-H3 INT8 inference (#1672)


---------

Co-authored-by: q6y6y6 <203597611+q6y6y6@users.noreply.github.com>

### [7ddac09](https://github.com/ModelTC/LightX2V/commit/7ddac095c43a87fce6a3e358a281140b2a22816c)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-11T12:47:16Z
- **提交信息**: fix: remove CUDA compat setup (#1693)

Co-authored-by: zhangbilang <2045966653@qq.com>

### [985accb](https://github.com/ModelTC/LightX2V/commit/985accb59c94e7f69110e8eb8bd13b5e8d69d1b3)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-11T12:40:44Z
- **提交信息**: feat(minimax-h3): add causal v0.1 streaming inference for RefA2AV and… (#1692)

… RefA2V

Co-authored-by: zhangbilang <2045966653@qq.com>

### [52547a2](https://github.com/ModelTC/LightX2V/commit/52547a294a3a553852c85ec12f315b6b621d1d0f)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-11T12:04:43Z
- **提交信息**: support opencv for save image (#1691)

### [0f66206](https://github.com/ModelTC/LightX2V/commit/0f66206a388814696a47b0fb0b9f599c534f737b)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-11T09:32:51Z
- **提交信息**: support h3 image (#1690)

Co-authored-by: WateBear <540295877@qq.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2332
- **最后更新**: 2026-11-12T02:49:20Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6900
- **最后更新**: 2026-11-12T02:30:35Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 11
- **主要提交者**: Adrian, Chunan Zeng, kangbintNV

## AI分析总结

# flashinfer-ai/flashinfer 昨日提交分析

## 一、主要更新类型

昨日 19 个提交覆盖五大方向：**功能新增**（SM107 MXFP8 融合 GEMM、batch-invariant MoE、NVLink 同步协议、SM12x NVFP4 融合 MoE）、**性能优化**（cuDNN paged 缓存复用、CI 构建提速）、**Bug 修复**（2-CTA TGV 竞态、SDSA keys 限制、文档测试、Windows 测试兼容）、**CI/构建改进**（架构错配检测、CPU 测试 lane、cubin 磁盘优化、shim 构建瘦身、sccache nvcc 缓存）、**文档与工程治理**（AGENTS.md 重构、CLI 安装文档）。

## 二、关键变更与项目方向

- **低精度推理端到端优化**：MXFP8 融合 GEMM 为 DeepSeek-V4.1 注意力输出投影提供单次 kernel launch 的量化+GEMM 融合，其 128×4 swizzled UE8M0 scale 布局与内部格式完全对齐，级联时无需转换；SM12x NVFP4 融合 MoE 算子沿用既有权重 ABI 和零拷贝视图，支持 SwiGLU/SiTU/ReLU2 激活与 CUDA Graph，基于执行桶几何与设备 SM 数做能力判定（188-SM 设备有专属路径），体现"渐进式增强"的算子演进策略。
- **启动与预热延迟系统性消除**：GDN delta-rule 内核磁盘持久化以源码指纹+SHA-256 作为失效条件，消除 vLLM 每次启动的重复编译；cuDNN paged 修复使 warm 场景 host 提交延迟从约 100μs 降至约 22μs，三者叠加对 serving 吞吐有可量化提升。
- **生产稳定性加固**：2-CTA TGV kernel 修复解决 CUDA Graph + PDL 下双 CTA 异步退出崩溃（Xid 13），仅对 `use_2cta` 编译的集群级退出屏障是精妙的最小化修复，1-CTA 路径零开销，已波及 SGLang 下游；SDSA 解除 2^20 keys 限制（按 131,072 步渐进增长），支持 1M token 上下文 prefill，服务 vLLM 长上下文场景。
- **MoE 统一抽象完善**：新增 `BatchInvariantBf16Config` 后端扩展跨 batch 输出一致性计算模式，配套文档矩阵与 runner 注册表一致性 CI 检查，防止文档漂移。
- **通信栈精简**：NVLink 移除 CFT counted writes 路径，保留 fence 与新增的 "sentinel" 无标志协议，Lamport transport 已覆盖原场景，降低 EP 每步通信开销。
- **CI/构建基础设施体系化**：PR 阶段用 CPU runner 检查 gencode 目标（此前夜间才暴露架构错配）；CPU 测试进入必过矩阵（修复 132 个失败）；cubin 构建改用 CPU torch 避免磁盘耗尽；JIT-cache shim 轮子在 runner 上构建（去掉 8.2 GB 无用镜像依赖，单作业 7.5 分钟降至约 1 分钟）；PR AOT 采用 rapidsai/sccache 分支缓存 nvcc 预处理（warm 命中构建 208–214 秒降至 30–35 秒），并通过 `cuobjdump -sass` 验证语义等价；Windows arm64 测试修复 bash 依赖与 cp1252 编码问题（显式传 `encoding="utf-8"` 而非 try/except）。

## 三、项目影响与潜在意义

这批提交共同推进 FlashInfer 从"单次 kernel 高性能"向"完整推理系统端到端低延迟"演进：核心能力上向最新量化格式（MXFP8、NVFP4）与最新架构（SM107、SM12x）推进；生态责任上主动修复已渗入 SGLang、vLLM 的生产问题；工程治理上构建覆盖 CPU/GPU、架构/发布/文档、多平台（含 Windows arm64）的分层防线。CI 反馈回路缩短与 nightly 成本下降直接服务内核开发效率，为多平台分发和更大规模贡献者协作奠定基础。各提交普遍附带量化基准与 run 链接，延续了项目可复现、可度量的工程文化，也反映出正向更成熟协作流程过渡。

## 四、值得关注的技术点

MXFP8 128×4 swizzled scale 布局的格式对齐设计、编译缓存键对 `repr()` 内存地址的防御、NVLink sentinel 无标志到达检测、TGV relaxed arrive 延长 CTA 生命周期的最小化修复、key bitmap 渐进增长策略、shim wheel 纯元数据硬编码 manylinux 标签的最小信任链设计、sccache `-M` 依赖缓存跳过 nvcc 预处理、Windows 编码问题的根因修复（同步修正 `ci/validate_cuda_versions.py`），均体现了该项目在内核与基础设施两端的深度工程素养。

## 详细提交记录

### [a293631](https://github.com/flashinfer-ai/flashinfer/commit/a2936316aa6abc139d90045c7e2f78f6f8b83534)

- **作者**: Chunan Zeng
- **时间**: 2026-11-11T23:22:13Z
- **提交信息**: feat(gemm): SM107 cute-dsl bmm_mxfp8 with MXFP8 output and strided A/out (#9003)

## 📌 Description

Adds a `cute-dsl` backend to `bmm_mxfp8` on SM107 that runs the whole
batch in one launch of `Sm107BlockScaledPersistentDenseGemmKernel`, and
lets it write **MXFP8 output**: `dtype=torch.float8_e4m3fn` plus a new
`out_scale` argument that receives FlashInfer's 128x4-swizzled UE8M0
scales. A and `out` may be strided views (row-major per batch), so a
grouped projection can read `[m, b, k]` storage and write `[m, b * n]`
storage that the next MXFP8 GEMM consumes directly.

Motivation: DeepSeek-V4.1's attention output projection (`wo_a`,
`bhr,hdr->bhd` over 8 head groups) feeds `wo_b`, an MXFP8 GEMM. Today
that needs a bf16 GEMM followed by `mxfp8_quantize` (or another
library's fused kernel). With this change one launch produces `wo_b`'s
FP8 input and its swizzled scales.

### Changes

- `dense_blockscaled_gemm_sm107.py` (defaults unchanged, both are
opt-in):
- `strided_ac=True` takes A's row/batch strides and C's batch stride
from new `a_ld` / `a_batch_stride` / `c_batch_stride` arguments (K-major
A, row-major C).
- `sfc_ptr` turns on an MXFP8 epilogue: C is `Float8E4M3FN`, each
32-column block of a row gets a UE8M0 scale. The scale tensor is laid
out as FlashInfer's 128x4 swizzle of the 2-D matrix holding C (row pitch
`sfc_row_pitch`, per-batch byte offset `sfc_batch_offset`) and
partitioned exactly like C, so each epilogue thread's scale bytes line
up with its accumulators.
- `epilogue_utils.epilogue_tma_store_mxfp8`: the per-tile epilogue.
Values are scaled by alpha in fp32, rounded to bf16, then quantized as
`mxfp8_quantize` would quantize that bf16 tensor (UE8M0 of absmax / 448
rounded up, RN saturating e4m3), reusing `float_to_ue8m0_fast` /
`ue8m0_to_inv_scale_fast` and the MXFP8-output pattern of the CuTe-DSL
MoE act-fusion kernel.
- `bmm_mxfp8`: `backend="cute-dsl"` (SM107), `out_scale` argument, an
autotuned runner (`bmm_mxfp8_cute_dsl_sm107`) over the non-swapped SM107
tactics, and requirement checks (m, n multiples of 128; `B.transpose(1,
2)` contiguous; 16-byte-aligned operands and strides; for MXFP8 output,
`out_scale` large enough, 4-byte aligned, with 128-aligned batch
offsets). The cuDNN / CUTLASS backends reject `float8_e4m3fn` /
`out_scale`; `auto` only picks `cute-dsl` when no other backend applies.
- MXFP8 output stores its scales without bounds checks, so its tactics
must keep every CTA, including the ones that round the grid up to whole
clusters, inside m, n and its own batch, and use 128-wide N tiles.
- Tuning is per M bucket (the `get_hybrid_num_tokens_buckets` values
that are multiples of 128), under CUDA graphs from a cold L2, on the
tuner's own buffers; a bucket's tactic that does not fit the call's M
falls back to the untuned pick.
- `benchmarks/routines`: `flashinfer_benchmark.py --routine bmm_mxfp8`
runs `cute-dsl` on SM107; `--out_dtype fp8_e4m3` selects MXFP8 output.

### Results

SM107 (CC 10.7). `flashinfer_benchmark.py` defaults: CUDA graph, cold
L2, median of 100 iterations; every GEMM autotuned (`--autotune`); each
cell averages two runs on one GPU. Baseline: cuDNN `bmm_mxfp8` with bf16
output, then `mxfp8_quantize` (`cuda` backend) of that output.

| b x m x n x k | cute-dsl, MXFP8 out (µs) | cute-dsl, bf16 out (µs) |
cuDNN, bf16 out (µs) | `mxfp8_quantize` (µs) | cuDNN + quantize (µs) |
MXFP8 out / (cuDNN + quantize) |
|---|---|---|---|---|---|---|
| 8 x 16384 x 1024 x 4096 | 132.4 | 131.7 | 128.4 | 59.7 | 188.2 | 0.70
|
| 8 x 512 x 1024 x 4096 | 12.3 | 11.0 | 10.6 | 5.6 | 16.2 | 0.76 |

Commands (run from `benchmarks/`; use `--m 512` and `--m 4096` for the
second row):

```bash
python flashinfer_benchmark.py --routine bmm_mxfp8 --batch_size 8 --m 16384 --n 1024 --k 4096 --num_iters 100 --out_dtype fp8_e4m3 --backends cute-dsl --autotune
python flashinfer_benchmark.py --routine bmm_mxfp8 --batch_size 8 --m 16384 --n 1024 --k 4096 --num_iters 100 --out_dtype bfloat16 --backends cute-dsl cudnn --autotune
python flashinfer_benchmark.py --routine mxfp8_quantize --m 131072 --k 1024 --input_dtype bfloat16 --backends cuda --num_iters 100
```

## 🧪 Tests

- `tests/gemm/test_bmm_mxfp8.py`:
- two `cute-dsl` rows in the smoke set (bf16 output, autotune on and
off);
- `test_bmm_mxfp8_cute_dsl_mxfp8_output` (b x m x n x k = 8 x 512 x 1024
x 1024 and 2 x 384 x 384 x 512; contiguous and `[m, b, *]`-interleaved A
/ out; autotune on and off): FP8 bytes and `out_scale` equal the bf16
result passed through `mxfp8_quantize(..., is_sf_swizzled_layout=True)`
bit for bit, and the guard bytes after `out_scale` stay untouched;
- `test_bmm_mxfp8_fp8_output_needs_out_scale`, and CPU tests of the
`out_scale` geometry and the MXFP8-output tactic rule.
- `tests/gemm/test_unified_gemm_fuzz.py`: a `bmm_mxfp8_cute_dsl` adapter
(SM107) with m and n random multiples of 128; for bf16 output it also
checks the MXFP8-output mode bit for bit, with guard bytes. It shares
`bmm_mxfp8`'s declared convention, so the conformance test cross-checks
it against cuDNN.
- On SM107: `test_bmm_mxfp8.py` 27 passed, 2 skipped (SM12x CUTLASS
rows), including `autotune(True)` and `autotune_v2(mode="tune")` on
batched bf16 and MXFP8-output calls; `test_unified_gemm_fuzz.py -k
"bmm_mxfp8_cute_dsl or conformance"` with
`FLASHINFER_GEMM_FUZZ_NUM_TESTS=300`: 35 passed;
`tests/trace/test_fi_trace.py -k "bmm or mxfp8"`: 3 passed; every 12th
`cute-dsl` case of `test_mm_mxfp8.py` (30 cases, the SM107 kernel's
default bf16 path) passed.
- End to end: DeepSeek-V4.1 prefill with `wo_a` on this path (sglang
side, separate PR) gives the same `wo_a` bytes as DeepGEMM's
`fp8_einsum`; prefill step time ratio 0.994-0.996 vs that path (two
nodes, alternating order), measured before the cluster-padding fix in
980678b77.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added a CuTe-DSL backend for batched MXFP8 matrix multiplication on
supported SM107 hardware, with automatic selection when existing
backends are unavailable.
* Added FP8 output with a caller-provided output-scale buffer, including
support for eligible strided layouts.
* **Behavior Changes**
* FP8 output requires an output-scale buffer. BF16 and FP16 output
remain supported by existing backends.
* **Tests**
* Added coverage for supported layouts, output scales, result accuracy,
and autotuning configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [36186cb](https://github.com/flashinfer-ai/flashinfer/commit/36186cb4d2fe57fba4180bebbb8b99ee68f017e2)

- **作者**: Alberto Massidda
- **时间**: 2026-11-11T21:42:09Z
- **提交信息**: gdn: persist delta-rule DSL kernels in the CuTe-DSL disk cache (#9357)

## 📌 Description

The delta-rule prefill kernels in
`flashinfer/gdn_kernels/delta_rule_dsl` (SM80, SM90 and SM12x paths,
e.g. `FullyFusedDeltaRuleSm120`) are compiled through
`custom_compile_cache.cached_compile`, which keeps compiled kernels in
an in-process dict only. Every new process (each vLLM start, each engine
worker) therefore recompiles them with CuTe-DSL, while GDN decode and
the Blackwell GDN prefill already persist their kernels with
`build_and_load_cute_dsl_kernel`.

This PR is step 1: `cached_compile` now routes compiles that use TVM-FFI
(all delta-rule DSL kernels do) through
`build_and_load_cute_dsl_kernel`, under the module `gdn_delta_rule_dsl`.
- The on-disk kernel name is the class name plus a truncated SHA-256 (24
hex digits) of `repr()` of the existing compile key (kernel
configuration + compile options). If that repr contains an object
address (`at 0x`) it would never hit across processes, so such kernels
stay in memory only; this guards that pattern, not every conceivable
unstable repr.
- The `delta_rule_dsl` sources are the key files, so editing any of them
invalidates the module; arch and CuTe-DSL stack fingerprints come from
`JitSpecCuteDsl` as for the other CuTe-DSL kernels.
- The SM12x PTX check still runs inside every fresh compile, before
anything is exported. `FLASHINFER_CUTE_DSL_DISABLE_CACHE=1` restores the
previous behavior; non-TVM-FFI compiles are unchanged.

A natural follow-up is shipping these SM12x GDN kernels prebuilt in
`flashinfer-jit-cache` for `sm120a` / `sm121a`, so that even the first
start skips the compilation.

## 🔍 Related Issues

Startup-time work in vLLM: vllm-project/vllm#48193 (roadmap),
vllm-project/vllm#65981 (weight snapshot).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks on the changed files (`pre-commit run --files
...`) and they pass.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New `tests/gdn/test_delta_rule_dsl_disk_cache.py`:
- CPU: stable and configuration-specific disk names; address-dependent
keys not persisted; only TVM-FFI compiles use the disk cache, once per
key; `FLASHINFER_CUTE_DSL_DISABLE_CACHE=1` compiles without writing
artifacts; a failing compile or PTX check propagates and exports
nothing.
- GPU (`test_second_process_reloads_without_compiling`): a subprocess
runs `chunk_gated_delta_rule` and must export a `gdn_delta_rule_dsl`
artifact; a second subprocess with the same workspace runs with
`cute.compile` replaced by a function that raises, and its output and
final state must be bitwise equal to the first.

Ran on: GB10 (sm_121a, flashinfer 0.7.2 + this file; 8 passed), H100
PCIe (sm_90; this branch; reload test passed), RTX 4090 Laptop (sm_89,
SM80 path; this branch; 9 passed).

End-to-end startup on DGX Spark (GB10), vLLM 0.32.1rc1.dev9+gfe8f2140e
serving `nvidia/Qwen3.8-27B-NVFP4` @ `482ca0f3` (GDN layers) with
flashinfer 0.7.2, one exclusive node, both arms in the same job. Per
arm: one discarded warm-up start (it also seeds this PR's disk cache),
then 3 measured starts with the OS page cache evicted and all other
caches (vLLM/Inductor/Triton compile caches, FlashInfer autotune, weight
snapshot) kept warm in both arms. So this measures restarts with a warm
compiled-kernel cache, not the first cold compile. ± is the sample
standard deviation.

| `custom_compile_cache.py` | Time to `/health` ready, per start | mean
± sd |
|---|---|---|
| current | 106.3 / 96.1 / 95.1 s | 99.2 ± 6.2 s |
| this PR | 83.9 / 84.8 / 78.0 s | 82.2 ± 3.7 s |

About 17 s (17%) less per restart in this setup. FlashInfer logs show
the two delta-rule kernels compiled and persisted in the warm-up start
and no delta-rule compilation in the measured starts. The greedy
completion of a fixed 32-token request had the same hash (`d2261771`) in
all 8 starts of both arms, and a ~3k-token request returned HTTP 200 in
all of them; this is a check that serving output is unchanged for these
requests, not a bitwise or accuracy evaluation (the GPU test above
covers bitwise equality of the reloaded kernel).

<details><summary>Server command</summary>

```
vllm serve nvidia/Qwen3.8-27B-NVFP4 --quantization modelopt_fp4 --kv-cache-dtype fp8 --max-model-len 36608 --max-num-batched-tokens 2048 --gpu-memory-utilization 0.8 --max-num-seqs 1 --safetensors-load-strategy prefetch --attention-backend FLASHINFER --async-scheduling --speculative-config '{"method":"mtp","num_speculative_tokens":3}' --language-model-only --kv-cache-memory-bytes 77309411328
```
</details>

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Eligible delta-rule kernels can now reuse compiled results across runs
and processes, reducing repeated compilation.
* Cached results are kept separate for different kernel configurations.
* When persistent caching is unavailable, kernels continue to compile
normally; compiled results remain available for reuse during the current
process.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Alberto Massidda <amassidda@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <43616432+bkryu@users.noreply.github.com>

### [990f90f](https://github.com/flashinfer-ai/flashinfer/commit/990f90f9ba5b9cb6109ee06556d77bf77ab2b5c5)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-11T20:42:43Z
- **提交信息**: docs(moe): regenerate the unified MoE activation matrix for the batch-invariant bf16 backend (#9369)

…-invariant bf16 backend

#9283 added `BatchInvariantBf16Config` to the unified MoE runner
registry without regenerating `docs/design_docs/flashinfer_moe_api.md`,
so `tests/cpu/moe/test_unified_moe_activation_matrix.py` fails on main
(the documented matrix must match the registry). The row is the
generator's output: `python scripts/generate_moe_activation_matrix.py
--write`.

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->
#9283 added `BatchInvariantBf16Config` to the unified `MoELayer` runner
registry without regenerating `docs/design_docs/flashinfer_moe_api.md`,
so `tests/cpu/moe/test_unified_moe_activation_matrix.py` (the documented
matrix must match the registry) fails on `main`: two nodes,
`test_documented_activation_matrix_matches_runner_registry` and
`test_activation_matrix_round_trip_ignores_locale_encoding`. This PR
commits the generator's output (`python
scripts/generate_moe_activation_matrix.py --write`): one table row for
`batch_invariant_bf16` with its eleven typed activations. No code
changes.

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

* **Documentation**
* Added documentation for the batch-invariant BF16 MoE activation
matrix, including its quantization and supported activations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [3db2f47](https://github.com/flashinfer-ai/flashinfer/commit/3db2f474e4053a6400d3128ba0683cbd4a05f5a4)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-11T16:58:21Z
- **提交信息**: feat(batch_invariant): batch-invariant bf16 MoE backend for the unified `MoELayer` (`BatchInvariantBf16Config`) (#9283)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

The first MoE PR of the batch-invariant series.
`BatchInvariantBf16Config()` is a new backend candidate of the unified
MoE layer (`backend_key = "batch_invariant_bf16"`), selected explicitly
through `BackendOptions` (it is not in the default candidate list):

```python
from flashinfer.fused_moe import (BackendOptions, BatchInvariantBf16Config, ExpertConfig, MoEActivationPack, MoEConfig,
                                  MoELayer, MoEWeightPack, QuantConfig, RoutingConfig, SwiGLU)
from flashinfer.fused_moe.api import RoutingInputMode, RoutingMethodType

cfg = MoEConfig(routing=RoutingConfig(num_experts=E, top_k=k, method=RoutingMethodType.Renormalize), quant=QuantConfig(),
                experts=ExpertConfig(intermediate_size=I), activation=SwiGLU(), backend=BackendOptions((BatchInvariantBf16Config(),)))
layer = MoELayer(cfg)
weights = MoEWeightPack()
weights.prepare_for("batch_invariant_bf16", BatchInvariantBf16Config.prepare_weights(w1, w2, num_local_experts=E, hidden_size=H,
                                                                               intermediate_size=I, activation=SwiGLU()))
out = layer(MoEActivationPack(x, None, routing_input_mode=RoutingInputMode.FromLogits, routing_logits=logits), weights)
```

The backend takes the three routing input modes of the TRTLLM-Gen
backends (`FromLogits`): the class's own routing from bf16 or fp32
logits. Supports every typed activation of the layer. Support for SM100
/ SM103 / SM107.

Attribution: Optimization ideas were gathered from the existing Prims
TS, CUTLASS, CuTe-DSL MoE.

### Performance

**Summary** -- the best existing FlashInfer MoE backend's time over the
batch-invariant backend's time through the unified `MoELayer` (> 1:
batch-invariant faster), geometric means per regime over the five models
(Qwen3-30B-A3B, Qwen3-235B-A22B, Mixtral-8x7B, DeepSeek-V3, Nemotron-3
ReLU2); the best existing backend is taken per cell among TRTLLM-Gen
bf16 (`trtllm_bf16_routed`), CUTLASS bf16, cuDNN Frost bf16 (Rubin) and
prims-TS (B200); the TRTLLM-Gen column beside it is the same ratio
against that backend alone. **untuned** = each backend's first pick in a
process that never autotunes; **autotuned** = each backend after one
`autotune(True)` pass at the batch size. Pre-routed: every backend fed
one common routing from outside the timed region; from logits: the
backends that route inside the op (batch-invariant, TRTLLM-Gen,
prims-TS).

| part | mode | form | vs best existing: decode (T <= 16) / mid (64 ..
1024) / prefill (>= 4096) / all | vs TRTLLM-Gen: decode / mid / prefill
/ all | cells |
|---|---|---|---|---|---|
| rubin | untuned | pre-routed | 1.01 / 1.02 / 1.08 / **1.03** | 1.01 /
1.24 / 1.40 / **1.18** | 40 |
| rubin | untuned | from logits | 0.86 / 1.19 / 1.38 / **1.09** | 0.86 /
1.19 / 1.38 / **1.09** | 39 |
| rubin | autotuned | pre-routed | 1.01 / 0.97 / 1.02 / **1.00** | 1.02
/ 1.00 / 1.13 / **1.03** | 40 |
| rubin | autotuned | from logits | 0.88 / 0.96 / 1.10 / **0.96** | 0.88
/ 0.96 / 1.10 / **0.96** | 39 |
| b200 | untuned | pre-routed | 0.96 / 1.00 / 0.97 / **0.98** | 0.97 /
1.11 / 1.16 / **1.06** | 37 |
| b200 | untuned | from logits | 0.85 / 1.05 / 0.90 / **0.94** | 0.85 /
1.09 / 1.13 / **1.00** | 37 |
| b200 | autotuned | pre-routed | 0.96 / 0.91 / 0.83 / **0.91** | 0.96 /
0.93 / 1.00 / **0.96** | 37 |
| b200 | autotuned | from logits | 0.85 / 0.90 / 0.85 / **0.87** | 0.85
/ 0.91 / 0.97 / **0.90** | 37 |

Method: both backends through `MoELayer`, each layer with that single
candidate, in two modes measured in separate processes; then the wall
time of one layer call captured in a CUDA graph and replayed behind a
2x-L2 flush: an op of several kernels under programmatic dependent
launch, where a sum of CUPTI kernel durations would count the overlapped
waits twice, so the op is timed by events, and the timer is named per
row.

### Functional parity with TRTLLM-Gen bf16 and CUTLASS bf16

A survey comparing `TrtllmBf16Config` and, as a second functional
reference, `CutlassBf16Config` drove one factor at a time around a base
cell (T = 64, E = 128, k = 8, H = 2048, I = 768, SwiGLU, Renormalize),
and recorded per cell who runs and, where a backend runs, FlashInfer's
own bf16 tolerance (`BF16Moe.get_tolerances`: atol 0.1 / rtol 0.85 on
92.5 % of the elements) against the shared torch reference:

A survey, drove both backends through `MoELayer` over the surface
`TrtllmBf16Config` accepts, one factor at a time around a base cell (T =
64, E = 128, k = 8, H = 2048, I = 768, SwiGLU, Renormalize), and
recorded what runs on Rubin (SM107):

| outcome | cells | what |
|---|---|---|
| batch-invariant and TRTLLM-Gen both run | 52 | every cell within
FlashInfer's bf16 tolerance on both sides; the two outputs differ by
1e-3 .. 8e-3 (different rounding points), bit-equal at top_k = 1; the
operator surface added `TopK`, `Llama4`, `TopKSigmoid` and grouped
`DeepSeekV3` from logits, `do_finalize = False` and the expert-parallel
slices to this column |
| batch-invariant only | 15 | the activations TRTLLM-Gen has no bf16
kernel for (GeGLU, GeGLUTanh, SiTU, PowLU, Identity, GELU, ReLU, SiLU
and parameter variants; CUTLASS bf16 runs all but the clamped SiTU), H
and I that are multiples of 8 but not of its shuffle block, T = 0 |
| TRTLLM-Gen only | 2 | E > 1024 and k > 16 (this backend's caps) |
| neither | 5 | H = 2049, I = 769, fp16 output, fused shared experts at
this cell |

Two properties of TRTLLM-Gen's bf16 path the survey recorded, both fixed
by construction here: its finalize chooses a different fold order below
a batch-size threshold, so its bits change with T at small T; and above
16 tokens it assigns expert slots with an `atomicAdd`, so the row
placement in its permuted buffer is not run-to-run stable (its finalized
bits are).


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

* **New Features**
* Added an opt-in batch-invariant BF16 backend for fused MoE on
supported GPU architectures.
* Added routing, permutation-planning, pre-routed input, and
grouped-GEMM configuration options.
* Added `MoELayer` support for documented routing methods, gated and
ungated activations, and expert-parallel execution.
* **Documentation**
* Expanded guidance on supported operators, configuration limits, and
conformance checks.
* **Tests**
* Added CPU and GPU coverage for activations, routing, deterministic
outputs, and batch-invariance behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [cfa0318](https://github.com/flashinfer-ai/flashinfer/commit/cfa0318a1316e8838bdee32c2a2014e22001dabe)

- **作者**: Yang Xu
- **时间**: 2026-11-11T14:02:58Z
- **提交信息**: fix(attention): reuse paged cuDNN preparation on 9.24 (#9351)

<!-- .github/pull_request_template.md -->

## 📌 Description

On cuDNN 9.24, paged prefill incorrectly treats explicit per-request
Q/KV mask lengths as requiring the 9.25 mixed-length API. The wrapper
consequently skips its prepared plan and calls
`prepare_cudnn_batch_prefill` on every warm execution. This change
admits explicit Q/KV lengths with token-offset multipliers on 9.24 and
lowers the existing paged-auto runtime floor from 9.27 to 9.24.

The helper is shared by metadata resolution and wrapper preparation,
including explicit `backend="cudnn"`. Genuine
cumulative-Q/per-request-KV inputs and FP8 retain the 9.25 requirement;
the single-token GQA Stats workaround retains its 9.27 guard. Stable FE
1.32, matching native capabilities, DSL availability, and all existing
auto shape/architecture restrictions remain.

Warm B200 comparison (148 SMs, BF16, causal HND/page16, B1 Q128 H16/2
D128, O+LSE; Torch2.14.1+cu130, official FE1.32.0, actual
cuDNN9.24.0.43):

| KV length | Parent host submission (us) | Candidate host submission
(us) | Parent graph replay (us) | Candidate graph replay (us) |
|---|---:|---:|---:|---:|
| 512 | 102.94–125.09 | 22.01–22.61 | 20.56 | 16.42–16.99 |
| 8192 | 102.31–109.73 | 27.98–36.92 | 30.77–30.78 | 26.67 |

Ranges are the two process medians in parent/candidate/candidate/parent
order. Both arms select the same backend engine8 and knobs per shape;
graph-build count remains1 throughout timing. Warm profiling records32
prepare calls on the parent versus0 on the candidate. These are host
submission and complete graph replay measurements, not isolated
attention-kernel or serving speedups. JIT and prewarm are excluded.

Reproducer added: `python benchmarks/bench_cudnn_paged_prepare.py
--kv-length 512` (repeat with8192), run on each revision with identical
dependencies. It checks the actual loaded backend version, FP64 O/LSE,
capture correctness and constant graph-build count. Qualification also
checked mapped cuDNN-library hashes to detect loader-order conflicts.

## 🔍 Related Issues

Follow-up to #6231 (paged-auto runtime qualification); no issue closure
claimed.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks pass (`pre-commit run --files ...`), including mypy,
Ruff and formatting. Repository guidance calls for scoped checks;
`--all-files` was not run.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets:
`tests/cpu/attention/test_cudnn_prepared_contract.py
tests/attention/test_cudnn_prepared_graph.py
tests/attention/test_cudnn_wrapper_regressions.py
tests/attention/test_cudnn_prefill_paged_cu_seqlens.py`

Local validation:
- 116 CPU contract tests pass with CUDA uninitialized; parent negative
control has7 expected failures.
- 6 new permanent B200 GPU tests pass on actual9.24 + official FE1.32.0:
BF16 auto/explicit and FP16 explicit, each O-only/O+LSE, strided Q and
changed-length/page-table/payload retained replay. Parent explicit
control fails the prepared-plan assertion.
- 12 bounded-provider probes pass with official FE1.32.0/1.32.3, default
FROST plus backend8/10 controls: FP64 O/LSE, fresh output bindings and
retained capture. This earlier bounded qualification is separate from
the final six explicit-path tests.
- 8 matched warm timing observations pass eager/captured FP64 O/LSE.
Wider GPU suites and CI remain pending.

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

AI-assisted implementation and validation. Please focus on the
distinction between mask lengths and physical offsets: explicit Q
lengths must remain authoritative even when shorter than their physical
partitions.

No public API signature, FE provider ranking, kernel implementation,
resource-retention policy, auto shape rule, or vLLM execution model is
changed. This PR does not enable new D64/D256 packed-GQA dispatch or
claim a serving TTFT improvement.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Paged cuDNN prefill can use cuDNN 9.24 when both query and KV lengths
are provided explicitly.
* Prepared prefill plans can be reused during graph replay, including
after inputs and page-table order change.
* **Documentation**
* Clarified version requirements: mixed query/KV length formats and FP8
still require cuDNN 9.25, while the single-token GQA Stats workaround
requires 9.27.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d2981ed](https://github.com/flashinfer-ai/flashinfer/commit/d2981ed4a64e926530ebd236168f9c39363c88e1)

- **作者**: kangbintNV
- **时间**: 2026-11-11T05:27:02Z
- **提交信息**: docs: fix API documentation and improve checker guidance (#9307)

<!-- .github/pull_request_template.md -->

## 📌 Description

Complete the public CAKE training API parameter documentation for GDN,
KDA, grouped GEMM and deterministic LM-head helpers. Add the 42 missing
Parameters sections and complete or separate the parameter entries
behind 10 argument-consistency findings, while preserving the existing
detailed contracts.

Restore the Conv1d backward-workspace restriction omitted in #9215: a
workspace must never be shared by backward launches that can overlap,
including CUDA graphs replayed on different streams. These API changes
affect docstrings only.

Also add category-specific **How to fix** instructions to documentation
summary and inline comments, including structured parameter templates
and an environment-variable row template matching
`docs/development/environment_variables.md`. Matching existing bot
comments are updated in place on reruns. The public API summary heading
is `🚨 POTENTIAL API BREAK 🚨`.

This incorporates the final changes from #9310.

Correct the deterministic Conv1d backward Returns structure so Sphinx
renders the `dx` formula as one continuous inline code fragment, without
problematic-markup anchors or splitting its multiplication across list
items. The formula and existing contract are unchanged.

Apply minimal corrections for 12 additional source-verified
documentation issues: Ulysses dtype exceptions, shape-dependent QKV
launch thresholds, restricted SM107 MSA coverage, separate output-buffer
descriptions and RMSNorm leading dimensions, mHC tuple-return rendering,
decode/sampling dtype defaults, GDN architecture coverage, and the
malformed deprecation notice. The notice retains the formal `deprecated`
directive with version `0.6.7`: #2730 introduced it after v0.6.6, and
v0.6.7 is the first release containing it. Its original explanation and
the planned 0.8.0 default change are preserved. The existing `fmha_v2`
auto-selection description is unchanged; no explicit backend enumeration
is added. SM107 support is restricted to packed-NVFP4 paged-KV, with a
short reference to the existing SM100/SM103 route requirements. Matching
public/backend RMSNorm docstrings stay consistent.

Also correct six remaining documentation groups: keep the four
ordinary/KCP KDA backward tuple descriptions together; separate DSA
return values from Notes and repair both no-PE stride literals; separate
nondeterministic Conv1d and RMSNorm output-buffer entries (including N-D
reciprocal-RMS shape); distinguish GQA query/KV shapes, output/LSE, and
workspace dimensions; and distinguish DSA indexer int32 indices from
FP32 scores. Existing return contracts and explanatory prose are
preserved.


## 🔍 Related Issues

Follow-up to #9215.

The 52 static-check findings in the original scope were already present
when these current public API names were introduced. Attribution was
checked against each introducing commit, the source snapshot
`a991a2b2e`, and this PR's base:

| Source PR | Public API family | Missing Parameters sections |
Argument-consistency findings | Total |
| --- | --- | ---: | ---: | ---: |
| #8959 | GDN det/nondet, single-rank and KCP | 15 | 4 | 19 |
| #9017 | KDA nondet single-rank and det/nondet KCP | 10 | 6 | 16 |
| #8963 | Grouped GEMM det/nondet | 12 | 0 | 12 |
| #8925 | Deterministic LM head | 4 | 0 | 4 |
| #9008 | Deterministic single-rank KDA | 1 | 0 | 1 |
| **Total** | | **42** | **10** | **52** |

This attributes the gaps to the public names entering the checker; some
prose was inherited from older implementations. It does not identify a
kernel regression.

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

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Docstrings only; executable ASTs, signatures, defaults and
kernels are unchanged.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): Not requested; validation uses CPU-only
documentation checks.

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

Validation:
- Parsed the comment workflow YAML and executed its actual
summary/inline JavaScript in a local Node harness with mocked
GitHub/artifact APIs. Verified all nine guidance categories,
existing-comment updates and idempotence, duplicate/cap handling,
unchanged inline public API warnings, incomplete reports and
clean-summary removal. No live comments were posted by this validation.
- The comment workflow runs from the default branch; the new guidance
takes effect after merge and a subsequent check run.
- All 52 scoped findings reproduce in the introducing commits,
`a991a2b2e`, and the base, and are absent after this change.
- Before the latest main sync, the full docstring scan covered 623
decorated functions, with **0 docstring-completeness failures and 0
argument-consistency failures**.
- Before the latest main sync, API/RST coverage was **0 MISSING**; that
snapshot had **132 STALE warnings**. The API/RST checker returns nonzero
for those warnings; it is not claimed to be warning-free.
- The preceding revision passed isolated Napoleon/docutils parsing for
67 modified function/class docstrings (reference roles treated as
literals). For this follow-up, Sphinx HTML rendering and registered
deprecation metadata confirm `Deprecated since version 0.6.7`; the
original explanation is unchanged.
- After stripping docstrings, the executable ASTs of all 29 modified
library Python files match current main exactly. The built-in checker
matches main without changes.
- Built the 17 docstrings changed in this follow-up into an isolated
Sphinx HTML project without warnings. Checked KDA tuple descriptions,
DSA Returns/Notes boundaries and intact stride literals, and individual
parameter dtype/shape descriptions. Cross-reference targets and the full
documentation site were not validated by this isolated build.
- Synced main at `a3ea68269` (including #9332). Workflow guidance now
points to the environment-variable reference, testing architecture
guards, and the actual reported Markdown path; the nine-category mocked
workflow harness and changed-file pre-commit checks pass.
- Changed-file pre-commit checks (including mypy and Ruff) and `git diff
--check` pass. The full-tree pre-commit checkbox remains unticked
because checks were scoped to the changed files.

Library runtime code and agent-guide content are unchanged. The built-in
checker already follows `AGENTS.md` and the linked development
references on main; this PR retains that implementation without
compatibility helpers. The comment workflow changes reporting and repair
guidance. A full Sphinx site build and GPU tests were not run; remote CI
will report separately.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Expanded training API guidance for inputs, defaults, outputs, device
support, workspace and saved-data sizing, backend options, packed
inputs, and forward/backward parameters.
* Clarified partition layouts, cut-point formats, grouped GEMM offsets,
accumulation behavior, buffer shapes and dtypes, output dtype defaults,
and empty-input backward behavior.
* Updated documented architecture and backend support, including
restricted SM107 packed-NVFP4 routes.
* Clarified workspace concurrency cautions and added actionable guidance
to documentation-check comments, updating existing comments when
guidance changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a3ea682](https://github.com/flashinfer-ai/flashinfer/commit/a3ea68269b7160f0f0821d27395a9e9c22dd2833)

- **作者**: Adrian
- **时间**: 2026-11-11T04:30:53Z
- **提交信息**: docs: reorganize AGENTS.md for clearer agent guidance (#9332)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reorganize `AGENTS.md` into a concise entry point so agents can find and
follow the relevant instructions. Keep everyday workflow rules in the
main file and move detailed JIT/build, backend, testing, and environment
guidance into four linked references.

Retain the settings and architecture requirements, remove repetition,
and add a resource-lifetime review checklist.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Changed-file hooks passed; the full-repository hook run was not
performed.

## 🧪 Tests

Documentation only; runtime tests not run. Validated local
links/anchors, setting preservation, and all 13 reference table blocks.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Not required for this documentation change.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): None (documentation only).

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

The architecture table includes the corrected SM89 FP8 guard.
AI-assisted editing.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Added development guidance covering backend behavior, environment
settings, builds, testing, and resource lifetimes.
* Expanded reference material with configuration defaults, validation
considerations, and practical constraints.
* **Chores**
* Updated documentation checks to recognize guidance across multiple
development documents and report findings with their locations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Alex Yang <aleyang@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a4cd87c](https://github.com/flashinfer-ai/flashinfer/commit/a4cd87cd731442a950c76003b0973c531f70054b)

- **作者**: Bo Li
- **时间**: 2026-11-11T03:53:43Z
- **提交信息**: feat(moe_ep)!: select the NVLink one-sided sync protocol with sync_protocol, without CFT counted writes; name the flag-free protocol "sentinel" (#8770)

## 📌 Description

The NVLink one-sided all-to-all selects how a rank learns that a step's
rows have arrived with one field, `sync_protocol`, between two
protocols: fence and the flag-free protocol, named "sentinel" after its
mechanism in Python and C++. CFT counted writes, a third way, are no
longer used.

### CFT counted writes no longer used

`NVLinkOneSidedAlltoAll` no longer uses CFT counted writes. They were
added to carry small steps (`fabric.try_put.counted` into CUDA logical
endpoints, with receivers waiting on hardware byte counters instead of
completion flags). The Lamport transport (#7498) now carries those steps
with less latency, so the CFT data path only added a collective vote, an
endpoint binding, checkpoint handling and a third transport choice to
every step.

- `NVLinkOneSidedAlltoAll` drops its CFT vote, logical-endpoint binding,
checkpoint/restore and destroy handling and its CFT transport choice.
The workspace is laid out without the CFT receive inbox and counters.
- The CFT kernels and the `moe_a2a_cft_*` ops stay in the module, unused
by the all-to-all. The logical-endpoint binding moves to
`nvlink_one_sided/cft.py`: `cft_unsupported_reason` and `CftEndpoints`
(`bind`, `ids`, `release`, `rebind`, `destroy`, each collective over the
EP group) bind one logical endpoint per rank to its workspace slice, so
that a data path can move workspace rows with CFT fabric operations by
endpoint ID and offset. The endpoints hold a reference to the workspace
until they are destroyed, so destroying the all-to-all first leaves them
usable; a process holds one binding at a time.
- Tests: the CFT cases go. The one-sided suites assert that no dispatch
or combine requests CFT counted writes. `test_cft_endpoints` checks that
every rank sees the same endpoint ID per rank, that a rebind after a
release keeps the IDs, that a second binding in the same process is
refused, and that the endpoints stay usable after the all-to-all is
destroyed and free its workspace when they are destroyed; it skips on
every rank when any rank lacks NVLink one-sided support, and where the
workspace cannot use FABRIC handles (in a container, that needs IMEX
channel 0, e.g. `--device /dev/nvidia-caps-imex-channels/channel0`).

### `NVLinkOneSidedConfig.sync_protocol`

- `"fence"`: senders publish per-peer completion flags behind a
system-scope fence; carries every step.
- `"sentinel"`: every landing row holds a sentinel word that no payload
word takes, and every 16-byte vector a sender pushes replaces it, so
receivers poll the data itself (the transport called Lamport so far). It
takes every step it can carry, up to `max_tokens_per_rank` tokens; the
512-token cap of its regions is gone.
- `"auto"` (default): sentinel for steps whose busiest rank sends at
most `AUTO_SENTINEL_MAX_TOKENS` = 256 tokens, fence for the others. On
B300 EP8 the sentinel round trip is ~1% faster at 256 tokens per rank
and the fence one ~4% faster at 512. Its regions hold 256 tokens per
rank, instead of the 159..512 default derived from the SM count and the
region size.

Every rank must pass the same `sync_protocol`; ranks that differ raise.
Where a rank cannot run the sentinel protocol, every rank uses fence, as
before. The split layer keeps kernels that pack their dispatch rows on
`"fence"`. The benchmarks take `--sync_protocol` instead of `--lamport`.

### Deprecations

`lamport`, `lamport_max_tokens`, `cft`, `cft_max_tokens_for_dispatch`
and `cft_max_tokens_for_combine` still work and emit a
`DeprecationWarning`: `lamport=False` and `cft=True` select `"fence"`,
`lamport_max_tokens` sets the sentinel limit under `"auto"`, the CFT
limits do nothing. They combine with `sync_protocol="auto"` only.
`NVLinkOneSidedAlltoAll` exposes the read-only properties
`sentinel_max_tokens` (the largest step the sentinel protocol takes,
fixed at construction; 0 without it) and `sentinel_enabled`;
`lamport_max_tokens` and `lamport_enabled` remain as deprecated
properties.

### C++ names

- `include/flashinfer/comm/moe_alltoall_lamport.cuh` ->
`moe_alltoall_sentinel.cuh` (namespace `moe_alltoall_sentinel`),
`csrc/nvlink_one_sided_lamport.cu` -> `nvlink_one_sided_sentinel.cu`,
`tests/moe_ep/test_nvlink_one_sided_lamport.py` ->
`test_nvlink_one_sided_sentinel.py`;
- ops `moe_a2a_lamport_{extend_workspace_layout,row_bytes,available}` ->
`moe_a2a_sentinel_*`; exported constants `MOE_A2A_LAMPORT_*` and
metainfo indices `LAMPORT_*_INDEX` -> `SENTINEL_*` (same values);
- the test defect switch `FLASHINFER_TEST_MOE_A2A_LAMPORT_DEFECT` ->
`FLASHINFER_TEST_MOE_A2A_SENTINEL_DEFECT`; scripts and docs follow.

The header is internal to the one-sided module and gets no forwarding
copy under its old name. The SM107 build of the kernels (#8419) carries
over.

### Rank-skew test

`test_rounds_under_rank_skew` copies its landing rows at the start and
expects them back after every phase. A sentinel dispatch writes into its
peers' landing rows without a handshake, so on a rank that took its copy
late, the copy could already hold a faster rank's first-round rows,
which every phase then reported as not reset. The ranks now synchronize
the copy and meet at a barrier before the first round.

## 🔍 Related Issues

Layer 1 of the stack
https://github.com/flashinfer-ai/flashinfer/stack/8774 (three PRs):
1. #8770 NVLink one-sided: `sync_protocol`; CFT counted writes no longer
used; the flag-free protocol named "sentinel" (**this PR**)
2. #8771 NVLink one-sided: sentinel cleanup; the workspace laid out in
one op
3. #9117 NVLink one-sided: the CFT counted-write path removed

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).

Validation:

- CPU, `tests/cpu/moe_ep/test_communication.py` and `test_config.py`: 58
passed after the first commit, 68 at the head.
- B300 x8, first commit: `test_nvlink_one_sided.py` 63 passed (with IMEX
channel 0 in the container, so `test_cft_endpoints` runs);
`test_moe_ep_communication_multirank.py` 38 passed (4 ranks);
`test_nvlink_one_sided_lamport.py` 70 passed, 3 skipped (8 ranks; the
skipped cases need 16 ranks); `test_layer_single_gpu.py` and
`test_split_kernels.py` 19 passed, 2 skipped.
- B300 x8, head: `test_nvlink_one_sided.py` 63 passed;
`test_moe_ep_communication_multirank.py` 38 passed;
`test_nvlink_one_sided_sentinel.py` 68 passed, 3 skipped;
`test_layer_single_gpu.py` and `test_split_kernels.py` 19 passed, 2
skipped.
- B300 x8, head with the rank-skew test fix (f342f2d7d):
`test_nvlink_one_sided_sentinel.py` 68 passed, 3 skipped.
- B300 x8, head 61500717a (rebased on main bf1d29092): CPU 68 passed;
`test_nvlink_one_sided.py` 63 passed;
`test_moe_ep_communication_multirank.py` 38 passed;
`test_nvlink_one_sided_sentinel.py` 68 passed, 3 skipped;
`test_layer_single_gpu.py` and `test_split_kernels.py` 19 passed, 2
skipped.
- GR100 (SM107): pending a GR100 node.


🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* NVLink one-sided MoE communication supports sentinel synchronization
alongside fence synchronization. Choose `auto`, `fence`, or `sentinel`;
`auto` selects sentinel for eligible smaller steps and fence otherwise.
* Sentinel synchronization uses fence synchronization when unavailable
or when a step is ineligible.
* CFT endpoint management is available for binding, release, and rebind
workflows.
* **Compatibility**
* CFT and Lamport configuration options are deprecated and may emit
warnings. Some combinations with explicit protocol selection are
rejected.
* **Documentation**
* Updated benchmark examples and architecture guidance to describe
protocol choices and support limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>

### [3dfe81d](https://github.com/flashinfer-ai/flashinfer/commit/3dfe81de82662f14f2d74ce77778373014222269)

- **作者**: CarstyYou
- **时间**: 2026-11-11T02:44:38Z
- **提交信息**: feat(moe): add SM12x NVFP4 fused MoE (#6510)

## Description

Integrates native SM120/SM121 CuTe-DSL NVFP4 MoE operators into the
existing `sm12x_nvfp4` runner, retaining the monolithic [baseline
(#5863)](https://github.com/flashinfer-ai/flashinfer/pull/5863) for
compatible shapes.

- Keeps the canonical prepared-weight ABI, existing backend key,
12-tensor packed inputs, and zero-copy weight-view sharing with W4A16.
No checkpoint-weight conversion is added to forward.
- Provides Q0/routing, grouped GEMM, fused FC1 activation/Q1, and FC2
finalization. Uses packed E2M1 with CUTLASS-compatible 128x4 E4M3 weight
scales.
- Preserves live FP32 per-expert weight scales `[num_experts]` and
per-layer activation quantization multipliers `[1]`; scales are not read
back or folded into cached Python values.
- Supports default SwiGLU, finite positive SwiGLU limits, supported SiTU
parameters, unary ReLU2, CUDA Graph replay, and PDL in the native path.
- Drops invalid/padded expert IDs on GPU, including bucket padding; no
GPU-to-CPU range check is added. Native scratch is cached by execution
shape and must be warmed before capture.
- Leaves the existing monolithic kernel and W4A16 execution behavior
intact.

## Dispatch

Capability checks precede performance selection. The performance
heuristic uses execution-bucket geometry and the cached device SM count,
not model names.

| Ordered condition | Path |
|---|---|
| Non-default supported SwiGLU limit, SiTU, or explicit PDL request |
Native modular operators |
| Default gated SwiGLU with only 64-column intermediate alignment |
Existing baseline |
| Jointly supported configuration on devices other than 188 SMs |
Existing baseline |
| ReLU2 on 188-SM devices | Native |
| Native FC1 heuristic selects BM8 | Existing baseline |
| Otherwise, I >= 1024 and bucket assignments / experts < 96 | Existing
baseline |
| Remaining jointly supported 188-SM shapes | Native |

Native gated operators require I % 128 == 0; unsupported native-only
combinations are rejected rather than silently changing activation
semantics. Default SwiGLU retains the baseline's I % 64 support.

The measurements below cover the four existing model-shape families.
They do **not** directly validate the default-SwiGLU, I >= 1024, MPE=96
boundary: DSv4 uses limit=10 and therefore requires native by
capability.

## Validation

- Complete PR-diff pre-commit: all applicable hooks passed for 27 files
at `5fbcceac9`.
- Targeted FlashInfer regression: 84 passed, 0 failed, 0 skipped (native
module plus the unified W4A4 subset; not the full FI suite).
- Compute Sanitizer: invalid-ID T2048 case (1), FP8 Q0 route (16), and
MXFP8 Q0 route (12), all passed with zero errors.
- Source-repository validation additionally passed 436 kernel tests and
the original 13-module / 274-test memcheck scope, with zero
skips/errors.
- Each performance point passed the declared pre/post/poisoned-graph
reference and actual-binary qualification. Production test tolerances
were not relaxed.

## Latest TP=1 comparison with baseline (#5863)

Published source: `5fbcceac9`. This is a fresh **actual unified API**
comparison, replacing the earlier low-level-chain table.

All three arms call `MoELayer(BF16 activation pack, canonical prepared
weight pack)`:

- **Baseline**: benchmark-only instance override selecting the retained
monolithic implementation.
- **Native**: benchmark-only instance override selecting the modular
operators.
- **Mixed**: unmodified production dispatch.

Inputs, routes, prepared weights/scales, and ceiling=32768 are shared;
workspaces are independent. Table columns show real tokens, actual
padded bucket, both MPEs, and the branch actually selected. DSv4's
forced-baseline reference includes the two-site limit=10 benchmark
adapter; this does not claim that the production baseline natively
supports that feature.

| Model-shape label | H | I | Experts | Top-k | Activation |
|---|---:|---:|---:|---:|---|
| dsv4 | 4096 | 2048 | 256 | 6 | SwiGLU(limit=10) |
| flash_next | 2560 | 640 | 512 | 10 | SwiGLU |
| qwen30b | 2048 | 768 | 128 | 8 | SwiGLU |
| nemotron | 2688 | 1856 | 128 | 6 | ReLU2 |

TP=1, PDL off; one exclusive RTX PRO 6000 Blackwell Server Edition (188
SMs, 96 GB), default 600 W limit, no clock locking applied. Timings are
**CUDA Graph GPU replay latency**, not CPU request latency or model
end-to-end results. Packing/padding GPU work, Q0/routing,
FC1/activation/Q1, FC2/finalization, and required chain-start
initialization are included. Compilation, weight
preparation/calibration, warmup, and capture are excluded. No
stage-boundary clear, copy, flush, or synchronization is inserted.

Each case uses N-B-M and M-B-N orders, five warmups and 100 samples per
arm/order, with a 256 MiB flush outside timing. Latencies are pooled
medians of 200 samples per arm; B/M order spans preserve both separate
ratios. B/N = baseline/native, B/M = baseline/mixed; greater than 1
means faster than baseline.

| Model | Tokens | Bucket | Real / bucket MPE | Mixed | Baseline us |
Native us | Mixed us | B/N | B/M | B/M order span |
|---|---:|---:|---:|---|---:|---:|---:|---:|---:|---:|
| dsv4 | 64 | 64 | 1.50 / 1.50 | native | 1900.512 | 1908.720 | 1907.712
| 0.996x | 0.996x | 0.996..0.996x |
| dsv4 | 683 | 768 | 16.01 / 18.00 | native | 2476.032 | 2545.664 |
2547.392 | 0.973x | 0.972x | 0.972..0.972x |
| dsv4 | 1024 | 1024 | 24.00 / 24.00 | native | 2488.320 | 2598.912 |
2594.816 | 0.957x | 0.959x | 0.959..0.959x |
| dsv4 | 1366 | 1536 | 32.02 / 36.00 | native | 2547.712 | 2664.448 |
2659.328 | 0.956x | 0.958x | 0.958..0.958x |
| dsv4 | 2048 | 2048 | 48.00 / 48.00 | native | 2568.192 | 2830.336 |
2865.008 | 0.907x | 0.896x | 0.896..0.897x |
| dsv4 | 2731 | 3072 | 64.01 / 72.00 | native | 2666.496 | 2743.152 |
2736.128 | 0.972x | 0.975x | 0.974..0.975x |
| dsv4 | 4096 | 4096 | 96.00 / 96.00 | native | 2848.112 | 2820.096 |
2821.120 | 1.010x | 1.010x | 1.009..1.010x |
| dsv4 | 5462 | 8192 | 128.02 / 192.00 | native | 3401.728 | 3280.896 |
3299.040 | 1.037x | 1.031x | 1.031..1.032x |
| dsv4 | 8192 | 8192 | 192.00 / 192.00 | native | 4195.328 | 4211.696 |
4218.368 | 0.996x | 0.995x | 0.995..0.995x |
| dsv4 | 10880 | 16384 | 255.00 / 384.00 | native | 5632.864 | 4178.656
| 4180.832 | 1.348x | 1.347x | 1.342..1.354x |
| dsv4 | 10923 | 16384 | 256.01 / 384.00 | native | 5700.608 | 4266.496
| 4275.056 | 1.336x | 1.333x | 1.329..1.336x |
| dsv4 | 16384 | 16384 | 384.00 / 384.00 | native | 7618.416 | 5534.720
| 5544.944 | 1.376x | 1.374x | 1.374..1.376x |
| dsv4 | 21846 | 32768 | 512.02 / 768.00 | native | 10624.000 | 7594.864
| 7623.664 | 1.399x | 1.394x | 1.389..1.399x |
| flash_next | 1 | 1 | 0.02 / 0.02 | baseline | 47.104 | 51.200 | 47.104
| 0.920x | 1.000x | 1.000..1.000x |
| flash_next | 16 | 16 | 0.31 / 0.31 | baseline | 345.088 | 343.040 |
345.088 | 1.006x | 1.000x | 1.000..1.000x |
| flash_next | 64 | 64 | 1.25 / 1.25 | baseline | 725.712 | 729.088 |
724.992 | 0.995x | 1.001x | 1.000..1.002x |
| flash_next | 256 | 256 | 5.00 / 5.00 | baseline | 1006.560 | 1010.688
| 1005.568 | 0.996x | 1.001x | 1.000..1.001x |
| flash_next | 820 | 1024 | 16.02 / 20.00 | baseline | 1039.360 |
1063.616 | 1040.352 | 0.977x | 0.999x | 0.999..1.000x |
| flash_next | 1024 | 1024 | 20.00 / 20.00 | baseline | 1054.688 |
1067.712 | 1053.696 | 0.988x | 1.001x | 1.000..1.001x |
| flash_next | 1229 | 1280 | 24.00 / 25.00 | baseline | 1063.936 |
1081.312 | 1065.952 | 0.984x | 0.998x | 0.998..0.999x |
| flash_next | 1434 | 1536 | 28.01 / 30.00 | baseline | 1077.968 |
1098.720 | 1076.224 | 0.981x | 1.002x | 1.001..1.002x |
| flash_next | 1536 | 1536 | 30.00 / 30.00 | baseline | 1088.512 |
1096.672 | 1088.512 | 0.993x | 1.000x | 1.000..1.000x |
| flash_next | 1639 | 1792 | 32.01 / 35.00 | native | 1088.192 |
1086.432 | 1086.432 | 1.002x | 1.002x | 1.002..1.002x |
| flash_next | 2048 | 2048 | 40.00 / 40.00 | native | 1116.160 |
1091.584 | 1093.248 | 1.023x | 1.021x | 1.021..1.021x |
| flash_next | 2458 | 2560 | 48.01 / 50.00 | native | 1131.520 |
1123.616 | 1123.328 | 1.007x | 1.007x | 1.007..1.007x |
| flash_next | 3277 | 3584 | 64.00 / 70.00 | native | 1178.624 |
1149.952 | 1148.928 | 1.025x | 1.026x | 1.026..1.027x |
| flash_next | 4096 | 4096 | 80.00 / 80.00 | native | 1254.400 |
1155.776 | 1154.048 | 1.085x | 1.087x | 1.086..1.087x |
| flash_next | 8192 | 8192 | 160.00 / 160.00 | native | 1823.744 |
1453.056 | 1449.952 | 1.255x | 1.258x | 1.258..1.258x |
| nemotron | 16 | 16 | 0.75 / 0.75 | native | 343.040 | 336.864 |
336.864 | 1.018x | 1.018x | 1.018..1.018x |
| nemotron | 342 | 512 | 16.03 / 24.00 | native | 594.944 | 577.504 |
577.536 | 1.030x | 1.030x | 1.030..1.030x |
| nemotron | 512 | 512 | 24.00 / 24.00 | native | 599.040 | 577.536 |
577.536 | 1.037x | 1.037x | 1.037..1.039x |
| nemotron | 683 | 768 | 32.02 / 36.00 | native | 629.760 | 589.824 |
588.800 | 1.068x | 1.070x | 1.068..1.070x |
| nemotron | 1024 | 1024 | 48.00 / 48.00 | native | 658.432 | 596.960 |
594.912 | 1.103x | 1.107x | 1.106..1.107x |
| nemotron | 1366 | 1536 | 64.03 / 72.00 | native | 720.896 | 644.096 |
642.048 | 1.119x | 1.123x | 1.121..1.123x |
| nemotron | 8192 | 8192 | 384.00 / 384.00 | native | 2403.328 |
1342.176 | 1343.344 | 1.791x | 1.789x | 1.788..1.791x |
| qwen30b | 1 | 1 | 0.06 / 0.06 | baseline | 40.960 | 41.984 | 41.952 |
0.976x | 0.976x | 0.976..0.976x |
| qwen30b | 16 | 16 | 1.00 / 1.00 | baseline | 220.160 | 216.064 |
220.160 | 1.019x | 1.000x | 1.000..1.000x |
| qwen30b | 64 | 64 | 4.00 / 4.00 | baseline | 303.104 | 301.792 |
303.072 | 1.004x | 1.000x | 1.000..1.000x |
| qwen30b | 256 | 256 | 16.00 / 16.00 | baseline | 306.176 | 311.296 |
307.904 | 0.984x | 0.994x | 0.995..0.995x |
| qwen30b | 384 | 512 | 24.00 / 32.00 | baseline | 316.384 | 324.208 |
317.440 | 0.976x | 0.997x | 0.996..0.997x |
| qwen30b | 512 | 512 | 32.00 / 32.00 | baseline | 321.504 | 334.528 |
318.464 | 0.961x | 1.010x | 1.003..1.010x |
| qwen30b | 576 | 768 | 36.00 / 48.00 | native | 326.368 | 324.576 |
324.288 | 1.006x | 1.006x | 1.005..1.007x |
| qwen30b | 640 | 768 | 40.00 / 48.00 | native | 319.456 | 323.552 |
323.552 | 0.987x | 0.987x | 0.984..0.987x |
| qwen30b | 768 | 768 | 48.00 / 48.00 | native | 328.704 | 325.600 |
326.336 | 1.010x | 1.007x | 1.007..1.009x |
| qwen30b | 1024 | 1024 | 64.00 / 64.00 | native | 341.984 | 327.680 |
326.656 | 1.044x | 1.047x | 1.046..1.047x |
| qwen30b | 2048 | 2048 | 128.00 / 128.00 | native | 414.432 | 367.456 |
365.568 | 1.128x | 1.134x | 1.134..1.134x |
| qwen30b | 4096 | 4096 | 256.00 / 256.00 | native | 695.296 | 471.776 |
473.088 | 1.474x | 1.470x | 1.467..1.470x |
| qwen30b | 8192 | 8192 | 512.00 / 512.00 | native | 1295.360 | 794.624
| 793.600 | 1.630x | 1.632x | 1.632..1.633x |

### Interpretation and limits

Larger-token FlashNext/Qwen and the ReLU2 family show advantages, but
this is not an all-case win. Slow points are retained, including DSv4 at
lower MPE and T8192 and Qwen T640. DSv4's native-only activation
requirement takes precedence over a faster patched benchmark reference.
Small differences between independent graph/workspace instances are
retained and are not interpreted as isolated dispatch overhead.

The fixture uses seed=42+tokens and a shared weight-encoding multiplier
of 512. It reuses the committed `bench_sm12x_nvfp4_ops.Fixture` tensors
and already-canonical `main_w1/main_sf1` views. The performance refcheck
follows the baseline benchmark's original BF16 oracle (`rtol=0.25,
atol=1.0`) for all arms; quantized-reference differences remain
observations. This is separate from the unchanged stricter production
tests and their nonuniform per-expert-scale coverage. Near-ties/order
ranges are descriptive, not confidence intervals or guarantees for
unmeasured shapes, routing skew, or other GPUs.

To exercise the integrated public API through the existing built-in
benchmark (its fixture differs from the calibrated three-arm comparison
above):

```bash
python benchmarks/flashinfer_benchmark.py --routine unified_moe --backends sm12x --quant-variant nvfp4 --num_tokens 8192 --hidden_size 2048 --intermediate_size 768 --num_experts 128 --top_k 8 --activation-type Swiglu --input_dtype bfloat16
```

The older `bench_sm12x_nvfp4_ops.py` command remains a low-level
operator-chain benchmark; it should not be labeled as reproducing this
unified-frontend table.

## Related Issues

Reference: #5863.

## Experimental Track

Not applicable; no code is added under `flashinfer/experimental/`.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added SM12x NVFP4 support for grouped MoE GEMM, FC1 activation and
quantization, FC2 finalization, and routed execution.
* Added support for SwiGLU, SiTU, and ReLU² in applicable NVFP4 FC1
operations, with tile selection and autotuning.
* Added benchmark options for routing scale, SwiGLU limits, precision
metrics, and GPU telemetry.
* **Bug Fixes**
* Improved handling of padded routes and worklist generation for routed
MoE operations.
* Added safeguards for scatter stores and corrected scheduler sentinel
values.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [24630ce](https://github.com/flashinfer-ai/flashinfer/commit/24630ce2404ebcd2b8d2f65720709362e25e3305)

- **作者**: Chunan Zeng
- **时间**: 2026-11-11T02:05:00Z
- **提交信息**: fix(gemm): add a cluster exit barrier to the 2-CTA TGV kernel (#9146)

## 📌 Description

The 2-CTA tactics of the BF16 TGV kernel
(`flashinfer/gemm/kernels/tgv_gemm_cute_ext.py`, tactics 16-28 and
39-46) synchronize the cluster only at kernel entry
(`cluster_arrive_relaxed` / `cluster_wait`). After that, the two CTAs
keep sending each other cross-CTA traffic until the end of the kernel:

- the peer's mbarrier arrives and TMA `complete_tx`, redirected to the
leader's `bar_full`;
- the multicast `tcgen05.commit` (`commit_mask = 0b11`);
- the cluster-coherent `dealloc_tmem(..., is_two_cta=True)`.

So one CTA can retire while its peer still has operations in flight that
target it. Under CUDA graph + PDL, the dependent kernel takes SMs
mid-graph, so the two CTAs can finish at different times. The straggler
then faults on the CTA that has already exited, with
`CUDBG_EXCEPTION_CLUSTER_BLOCK_NOT_PRESENT` (Xid 13, "CTA Not Present").

This adds a cluster-wide exit barrier after the warp dispatch, compiled
in only for `use_2cta`. All 8 warps of both CTAs fall through to it, so
neither CTA can exit until the other's tail work has landed. It is a
relaxed arrive, because it only extends CTA lifetime; every cross-CTA
datum already flows through mbarrier phases. 1-CTA tactics are unchanged
(the barrier is behind `const_expr`).

SGLang's vendored copy of this kernel received the same fix after
production crashes (sgl-project/sglang#32907, fixed in
sgl-project/sglang#32954). The FlashInfer copy still lacked it. SGLang
hit the crash again as soon as `mm_bf16(backend="auto", pdl=True)` let
the autotuner pick FlashInfer's TGV: CUDA core dumps name
`TgvGemmCuteExtKernel` with `CLUSTER_BLOCK_NOT_PRESENT` in a Qwen4-Exp
PD nightly (8x B200), and the change was reverted in
sgl-project/sglang#49118.

## 🔍 Related Issues

- sgl-project/sglang#32907 (root cause and CUDA core dump analysis)
- sgl-project/sglang#32954 (same fix in SGLang's vendored kernel)
- sgl-project/sglang#49118 (SGLang revert after the crash through
`mm_bf16` autotune)

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [ ] Tests have been added or updated as needed. No deterministic
reproducer exists: the race needs uneven scheduling of the two CTAs. It
did not reproduce on a single B300 for SGLang either, matching
sgl-project/sglang#32907.
- [x] All tests are passing (`unittest`, etc.).

Suggested CI test targets: `tests/gemm/test_mm_bf16.py
tests/gemm/test_tgv_gemm.py`

Validation on 1x B300 (SM103), nvidia-cutlass-dsl 4.8.0. The patch was
applied to the v0.7.3 copy of the file, which differs from main by 4
unrelated lines:

- Correctness: all 29 SM100 tactics (0-28), with and without bias,
`pdl=True`, at (M, N, K) = (1, 2048, 1024), (8, 6144, 2560), (16, 4096,
8192), (32, 8192, 2048), (64, 1024, 2048). All within 1e-2 relative
error of an FP32 reference, and no tactic was skipped.
- `tests/gemm/test_tgv_gemm.py`: 94 passed.
- Cost of the barrier, per launch: 2-CTA tactics 16/19/22/25/26, each
timed in a CUDA graph with PDL, rotating at least 1 GiB of weights so L2
is cold. Arms ran in base/fix/fix/base order; the table shows the min of
each arm's two runs.

  | (M, N, K) | without (us) | with (us) | ratio |
  |---|---:|---:|---:|
  | (8, 6144, 2560), 5 tactics | 6.86-7.24 | 6.88-7.24 | 1.001-1.003 |
| (16, 4096, 8192), 5 tactics | 15.35-16.54 | 15.50-16.80 | 1.010-1.017
|
| (32, 8192, 2048), 5 tactics | 6.81-10.53 | 6.88-10.71 | 1.003-1.016 |

Geomean 1.008x, worst 1.017x. On (16, 4096, 8192) the baseline's own two
runs differ by up to 2.4%.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during two-CTA execution. Both CTAs now
complete their shared-resource cleanup before either exits, ensuring
more consistent completion of the operation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c5c39b0](https://github.com/flashinfer-ai/flashinfer/commit/c5c39b0e87f027011c86881aa2935a83e1ce53e7)

- **作者**: Netanel Haber
- **时间**: 2026-11-11T01:46:08Z
- **提交信息**: [SDSA] Let group_union_masks take more than 2^20 keys; move token_sparse into flashinfer.sdsa (#9323)

<!-- .github/pull_request_template.md -->

## 📌 Description

`group_union_masks` now takes more than 1,048,576 keys. Before, it
raised `ValueError` above that, which blocked prefill above 1M tokens of
context in vLLM.

- Above 1,048,576 keys, the key bitmap grows in steps of 131,072 keys
instead of doubling. Below, nothing changes.
- New `union_key_limit(group, top_k, device=None)`: the most keys
`group_union_masks` takes on the device. On SM100 with `top_k=2048`, it
is 1,441,792 keys for groups of up to 4 rows, 1,310,720 for 8 and
1,179,648 for 32.
- `flashinfer.token_sparse` moves to `flashinfer.sdsa.token_sparse`. The
old path stays as a compatibility alias. Its trace op types become
`sdsa_token_sparse_kv_indices` and `sdsa_group_union_masks`. Its tests
and trace outputs move to `tests/sdsa/` and `fi_trace_out/sdsa_*`, under
the SDSA CODEOWNERS. `tests/attention/test_trtllm_gen_token_sparse.py`
and the trtllm-gen decode stay in attention.
- `docs/design_docs/sdsa.md` replaces `sdsa_indexer.md` and
`token_sparse_attention.md`, as one SDSA design doc.

Based on a fix by @jinhangchoi. @Kipok reported the bug.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

`pre-commit run --files` on the changed files passes.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: `tests/sdsa/
tests/trace/test_fi_trace_template_consistency.py
tests/trace/test_template_registry.py
tests/attention/test_trtllm_gen_token_sparse.py`

Tested on GB200: `tests/sdsa/` (21 token-sparse tests, including the
kernel at exactly `union_key_limit` keys and the doctest; 90 indexer
tests), the trace template consistency and registry tests (1213 passed,
2 skipped), and `tests/attention/test_trtllm_gen_token_sparse.py` (73
passed). Not tested on other SM10x GPUs.

## Reviewer Notes

None.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added utilities for converting token positions into cache-slot lists
and building grouped key unions with per-token masks.
* Added a device-aware limit query for supported group-union sizes.
These utilities are available through the SDSA API, and existing imports
remain supported.
* **Documentation**
* Consolidated token-sparse attention guidance into the SDSA
documentation, covering APIs, layouts, limits, tracing, CUDA graph
replay, and validation.
  * Updated API references to include the group-union limit query.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Jinhang Choi <jinhangc@nvidia.com>

### [907726e](https://github.com/flashinfer-ai/flashinfer/commit/907726e092b5c338d694b2e890e85dbafdfa8a80)

- **作者**: Mingyang Wang
- **时间**: 2026-11-11T01:13:10Z
- **提交信息**: Replace CLAUDE.md guidance with AGENTS.md (#5328)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replace the root and experimental `CLAUDE.md` guidance with `AGENTS.md`,
and migrate all tracked references, readers, and related identifiers.
Preserve upstream guidance from `main` at `e9a6912189`; no legacy
guidance files or compatibility code are retained. The rebase retains
the new CPU-test, AOT cache, and provider-target lint instructions,
together with the latest README installation guidance.

Correct the FP8 GEMM capability example to compare the full capability
tuple against `(8, 9)`, including SM89.

Exclude the generated wheel marker `KERNEL_SOURCES_EXCLUDED.txt` from
static source-path existence checks while retaining checks for ordinary
missing paths.

Original motivation: [agent-guidance
announcement](https://x.com/trq212/status/2101009392611278961).

## 🔍 Related Issues

No linked issue.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
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
reviewers may adjust): none (documentation/static tooling only)

Validation:

- Targeted pre-commit hooks passed for the root guidance and README
changed by the rebase; prior passing hooks apply to the unchanged
migration files.
- Exact content-preservation checks against the new base passed,
including the new upstream guidance, the SM89 correction, and the
absence of legacy guidance filenames or references.
- Five real cross-source checks on both revisions introduced no
findings; the same three existing environment-variable warnings remain.
This comparison reads the base's substantive guidance directly.
- Reused the generated-marker negative control and previous strict PR
documentation adapter result for unchanged checker code. The full
adapter was not rerun for this rebase; the fresh content and
cross-source checks cover the changed inputs.
- Diff whitespace checks and independent scoped review passed.

GPU and full-repository tests were not run: this change covers
documentation and static tooling.

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

The documentation adapter reads `AGENTS.md` for both revisions. When the
base predates this migration, its redirect can cause newly omitted
environment-variable documentation to be suppressed as existing debt.
This historical-comparison limitation is accepted for the direct
replacement; a separate content-preservation comparison verified the
migration. Three existing environment-variable documentation warnings
remain unchanged.

Claude automatic discovery of `AGENTS.md` remains unverified.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Updated contributor, development, and feature guides to reference
`AGENTS.md` as the source of repository guidance.
  * Removed the `CLAUDE.md` guidance document.
* **Chores**
* Updated documentation checks to recognize legacy guidance files while
preserving current guidance.
  * Added tests for documentation-checking behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [e9a6912](https://github.com/flashinfer-ai/flashinfer/commit/e9a69121898d032082bb080c9b15a1fc1a455d56)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:59:43Z
- **提交信息**: ci: catch provider CUDA-target mismatches on PRs (spec lint + cuobjdump check) (#8718)

<!-- .github/pull_request_template.md -->

## 📌 Description

Release and nightly builds reject a provider wheel whose modules carry
SASS for another architecture, or any PTX. PRs never ran that
inspection: the `AOT Build Import` lane builds every provider wheel
(1h47m-2h49m per job, six jobs) but only checks the module inventory.
#4924 registered `ulysses_lowp` with both `sm_89` and `sm_120a`
gencodes, passed every PR check, and the nightly has been red since
(#8482, fix in #8487). This adds the check to PRs, cheaply and early:

- **Provider Spec Lint job** (`pr-test.yml`, one per published CUDA
image, CPU runner, no GPU): `scripts/task_check_jit_spec_gencodes.sh`
generates the AOT spec list for every provider architecture and fails if
a spec's explicit `-gencode` flags name a target its provider cannot
run, or embed PTX. Part of `Test Results Summary`. The AOT lanes repeat
the lint first thing, so their fail-fast still cancels the matrix.
- **Post-build inspection in the AOT lane:**
`scripts/verify_jit_cache_provider_architectures.py` runs the release
builds' `cuobjdump` check over every provider wheel the lane builds.
- **Plumbing:** `flashinfer/aot.py` gains `generate_jit_specs()`, split
out of `compile_and_package_modules` so the lint reuses the exact spec
generation (the build is unchanged). The nvcc flag parser and
per-provider rule live in `flashinfer/jit/_cuda_architecture.py`.

Modules without explicit `-gencode` flags follow the provider-filtered
compilation context and are not checked; compile errors are still only
caught by the full builds.

## 🔍 Related Issues

Related: #4924 (introduced the mismatch), #8482 (issue), #8487 (fix for
`ulysses_lowp`).

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/jit/test_jit_spec_gencode_lint.py
tests/cpu/jit/test_jit_cache_release.py`

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

- Verified locally: the new CPU tests and
`tests/cpu/jit/test_jit_cache_release.py` pass; pre-commit hooks pass on
the changed files; `actionlint` reports the same findings on
`pr-test.yml` as `main`. **Not verified:** spec generation end to end
(needs torch and nvcc, which my machine lacks) and its run time (the
build script's comment puts spec generation at 60-75 s per provider).
The first CI run is the real test; the main risk is a false positive
from a module whose flags look wrong but whose binary passes the release
check.
- Moving the lint into its own job does not stop the AOT builds when it
fails; the AOT lanes' copy of the lint does that through fail-fast.
Dropping that copy, or gating the test lanes on this job, are follow-ups
I did not take.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added automated checks for CUDA architecture targets before builds
across supported providers. Failures are reported in pull-request and
package-build workflows.
* Added verification that built provider packages contain the expected
CUDA architectures.
* Added a way to generate JIT build specifications without compiling
them.
* **Tests**
* Added CPU-only tests for architecture checks and workflow integration,
without requiring a GPU.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [d5ee302](https://github.com/flashinfer-ai/flashinfer/commit/d5ee302a1aed060b3cda4b7ad2cfc6895739dc41)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:59:11Z
- **提交信息**: feat(cli): consistent kernel-wheel install options; docs: recommend download-kernels and document upgrades (#9328)

<!-- .github/pull_request_template.md -->

## 📌 Description

Makes `flashinfer download-kernels` the documented way to add pre-built
kernels, lets it auto-detect the GPU like `install-jit-cache-wheel`
does, and documents the upgrade pitfalls.

```bash
pip install flashinfer-python
flashinfer download-kernels                 # all architectures (default, unchanged)
flashinfer download-kernels --mode minimal  # only the visible GPUs
```

**CLI (`flashinfer/__main__.py`)**
- `download-kernels` gains `--mode all|minimal`, the same option
`install-jit-cache-wheel` already has. `--mode minimal` installs only
the jit-cache providers for the visible GPUs. The default is unchanged:
`minimal` when `--sm` is given, otherwise `all`.
- The `--mode`/`--sm` combination and the `--sm` spellings are now
validated before anything is installed. Previously, `--sm hopper` or
`--mode all --sm sm90a` first downloaded the ~1.7 GB cubin wheel and
only then failed on the jit-cache step.
- An unsupported explicit `--cuda-version` is now also rejected before
anything is installed. Auto-detected CUDA is still resolved only for the
jit-cache step, so a host without CUDA can still install the cubin
wheel.
- `install-cubin-wheel`, `install-jit-cache-wheel` and
`download-kernels` now share one definition of each common option
(`--cuda-version`, `--flashinfer-version`, `--mode`, `--sm`,
`--nightly`, `--dry-run`), so their names, help text and order match.
Before, the help text had drifted. The single-wheel commands also accept
download-kernels' `--cubin-index-url` / `--jit-cache-index-url`
spellings next to the existing `--index-url`. A test checks that the
shared help text stays identical.

**Docs**
- **README.md**: the quick-start uses `download-kernels` instead of the
separate `install-cubin-wheel` / `install-jit-cache-wheel` commands,
with notes on download size, `--mode minimal` / `--sm`, and upgrading.
The nightly section uses `download-kernels --nightly`.
- **docs/installation.rst**: replaces the unpinned `pip install
flashinfer-cubin --index-url ...` / `flashinfer-jit-cache --index-url
.../cu129` commands, which do not pin the version to the installed
`flashinfer-python`. Adds an **Upgrading** section: the kernel wheels
are pinned to one `flashinfer-python` version and must be reinstalled
after every upgrade (otherwise they are ignored with a warning). It also
notes that `flashinfer-cubin` stopped publishing to PyPI after 0.6.13
(#3853), so unpinned or PyPI-resolved installs pick up a stale wheel.
- **docs/cli.rst**: documents `download-kernels --mode minimal`, the
up-front validation, and the shared options across the install commands.

## 🔍 Related Issues

None; follows up on a request for a simpler, least-surprising install
path.

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cli/test_cli_cmds.py`

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

The commands were checked against the v0.7.3 release: `download-kernels`
exists there, and the matching `flashinfer-cubin` and
`flashinfer-jit-cache` wheels (cu129/cu130, x86_64/aarch64) are on
https://flashinfer.ai/whl. By default the jit-cache install pulls every
architecture provider (about 1.5 GB for cu130 x86_64, more for cu130
aarch64, which adds sm110a/sm121a), plus the 1.7 GB cubin wheel.

The new CLI tests in `tests/cli/test_cli_cmds.py` were **not run
locally** (no torch in my local environment); only pre-commit (ruff,
mypy) was run. The Sphinx build was not run either.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Updated installation guidance to use `flashinfer download-kernels` for
matching kernel wheels, including nightly builds.
* Documented default, minimal, and explicit GPU architecture selection,
version matching, upgrade steps, and fallback behavior.
* Clarified package index options and that `flashinfer-cubin` is no
longer published to PyPI.
* **Bug Fixes**
* Improved validation of mode, architecture, and CUDA version options
before installation.
* Added support for shared index URL options across kernel installation
commands.
* **Tests**
* Added coverage for GPU-aware provider selection, invalid options,
index URL aliases, and CLI help consistency.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [44f2475](https://github.com/flashinfer-ai/flashinfer/commit/44f2475fbbf20057dadefb22c8cbe1c2e4fe7064)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:58:35Z
- **提交信息**: ci: run tests/cpu in a CPU-only lane on every PR Test run (#9293)

<!-- .github/pull_request_template.md -->

## 📌 Description

A targeted run (`@flashinfer-bot run tests/...`) executes only the named
paths, and `tests/cpu` otherwise runs only inside the H100 lane's full
suite. Three PRs merged after green targeted runs while breaking
`tests/cpu` tests their targets did not select. Together they account
for the 132 failures on `main`'s scheduled H100 run:

| PR | Broken test | Cause |
|---|---|---|
| #9155 | `tests/cpu/test_cake_kcp_partition_parity.py` (125) | adds a
second public `kcp_partition_digest` to `cake_kcp_plan.py` |
| #8666 | `tests/cpu/prims_ts/test_moe_runner_ffi_tensors.py` (4),
`test_batched_gemm_captured_schedule_tasks.py` (1) | new
`cfg.use_deepseek_fp8` read and `k_subblock=` argument |
| #8590 | `tests/cpu/attention/test_cudnn_prepared_contract.py` (2) |
`reset_workspace_buffer()` reads `self._batch_invariant` |

This adds a **CPU Unittest** entry to the PR Test matrix. It runs all of
`tests/cpu`, whatever scope was requested, through
`task_run_unit_tests.sh --workers 16 --test-path tests/cpu` with
`ci/bash.sh --no-gpu`. It uses the existing `[self-hosted, linux, x64,
cpu, on-demand]` pool that the x64 AOT lanes already use
(flashinfer-ai/ci-infra `cpu-x64-ondemand.yaml`: 64–96 vCPU, 384–512
GiB, max 50 runners), so no infrastructure change is needed.

Because it is part of the single test matrix:
- it counts toward the required `Test Results Summary` check, so branch
protection needs no change;
- through fail-fast, a broken `tests/cpu` stops the GPU lanes after
minutes instead of after the H100 lane.

Details:
- **Runtime:** main's H100 timings put `tests/cpu` at about 28
CPU-minutes over 162 files. With 16 workers that is about 5 minutes; the
slowest file, about 250 s, sets the floor.
- **Lane identity:** `ci/bash.sh --no-gpu` forwards no lane-identity
variables, so the lane passes `CI_GPU_NAME`, `CI_TEST_SCRIPT` and
`CI_MATRIX_CUDA` itself.
- **Caching:** sccache and the compile cache are off for it, since it
compiles nothing.
- **Results:** its JUnit artifact (`junit-cpu-*`) feeds the skip-all
check, and the scoped-run note now says `tests/cpu` also ran.
- **Docs:** `CLAUDE.md` and `CONTRIBUTING.md` say `tests/cpu` always
runs and must not need a GPU.
- **No duplicate on GPU runners:** the H100 lane now ignores `tests/cpu`
(`PYTEST_ADDOPTS=--ignore=tests/cpu`, as `ci/bash.sh` already does for
`tests/test_sharding`). Targeted runs drop `tests/cpu` targets from the
H100 scope, so a request naming only `tests/cpu` schedules no H100 job.
A10G/T4 shard lists name no `tests/cpu` file.

## 🔍 Related Issues

Scheduled PR Test failing on `main` (132 `tests/cpu` failures from
#9155, #8666, #8590).

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
reviewers may adjust): `tests/cpu`

Checked locally:
- **Matrix step:** the real "Build Test Matrix" step, run for each mode:
  - full run: 14 jobs, including CPU Unittest;
  - targeted run: AOT, CPU Unittest and Targeted H100;
  - `skip_gpu`: no CPU lane.
- **Docker command:** the Run Test step with `ci/bash.sh` stubbed builds
`--no-gpu ... --workers 16 --test-path tests/cpu`.
- **Lint:** `actionlint` reports no new findings, and `pre-commit`
passes.

Not yet verified:
- **First real run:** the lane has not run in CI. The `tests/cpu` tests
have only ever run with a GPU attached; a grep found only mocked or
`FakeTensorMode` CUDA use, but this PR's own run is the first proof.
- **Expected failure:** the lane will fail, both here and on every PR,
until main's 132 failures are fixed. Those fixes should land first or
together with this.

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

- **Why a lane, not a separate workflow on every push:** self-hosted
runners only take authorized runs, because PRs can come from forks. A
GitHub-hosted job would have to rebuild the torch/CUTLASS-DSL
environment without the CI image. Merging already needs an authorized
run on the head commit, and every authorized run now includes this lane.
- **Cost:** the CPU pool keeps no idle runners, so a cold start can take
up to 10 minutes, and instances bill at least 10 minutes. That is
roughly $0.60–$0.90 per run.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Public CI runs now include the full CPU test suite, even when tests
are scoped to selected targets. CPU tests run in a GPU-free lane, and
their results are included in CI reporting.
* Docs-only or otherwise skipped-path changes run no tests. Manual runs
configured to skip GPU tests also omit the CPU test lane.

* **Documentation**
* Updated CI guidance to explain when CPU tests run and which conditions
skip them.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f77184b](https://github.com/flashinfer-ai/flashinfer/commit/f77184bf8472df1510b38eeaaa20c8cd2ddfc7b0)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:57:38Z
- **提交信息**: ci(release-build): build flashinfer-cubin with CPU torch to stop runner disk exhaustion (#8822)

<!-- .github/pull_request_template.md -->

## 📌 Description

`build / build-flashinfer-cubin` in the nightly/release pipeline can
fail with `OSError: [Errno 28] No space left on device` ([example
run](https://github.com/flashinfer-ai/flashinfer/actions/runs/41933587066/job/126936928424)).
The job's own `df` shows the hosted runner's root disk at 89% before the
build (72 GB total, 8.1 GB free). `python -m build --wheel` then creates
an isolated PEP 517 environment that installs the default CUDA `torch`
wheel plus its `nvidia-*` dependencies (cudnn, nccl, nvshmem, cusparse,
triton, ...) and fills what is left.

Why torch is needed at all: the cubin backend calls
`flashinfer.artifacts.download_artifacts`. Importing it pulls in
`jit.core`, `compilation_context` and `jit.cpp_ext`, which import
`torch` at module level. No CUDA is used, and removing torch from that
import chain would be a change to the JIT core, so this PR does not do
that.

This PR installs the CPU `torch` wheel (`download.pytorch.org/whl/cpu`)
into the job environment, installs the rest of `flashinfer-cubin`'s
`[build-system].requires` read from `pyproject.toml` (so the list cannot
drift), and builds with `--no-isolation --skip-dependency-check`. The
skipped check only covers the CUTLASS DSL requirement that the backend
adds for the provider wheels and the cubin build never imports. The
`TMPDIR` override is dropped because no large environment is created
under `/tmp` any more; the job still pins `ubuntu-24.04` and prints `df
-h /`.

## 🔍 Related Issues

Found while running CI for #8722.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Run on the changed file; it passes.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Workflow-only change;
the check is the cubin job itself.)
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets: none needed beyond the `build /
build-flashinfer-cubin` job, which runs on this PR (`release.yml`
triggers on `release-build.yml` changes).

## Reviewer Notes

**Verified locally (macOS, CPU torch):** the requirement extraction,
`import build_backend`, and `import flashinfer.artifacts` all work with
only the CPU torch, `apache-tvm-ffi`, `filelock`, `requests`, `tqdm`,
`numpy` and `nvidia-ml-py` installed (no `nvidia-cutlass-dsl`).

**Not verified:** the actual wheel build on the Linux runner. It needs
the download step and the CPU wheel install to succeed there, so please
check the `build / build-flashinfer-cubin` result and that the cubin
wheel contents match a previous run.

AI-assisted.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated the release build process to prepare its build environment
before creating distribution packages. The build now uses a simplified
wheel-generation workflow and no longer relies on an isolated build
environment or custom temporary-directory configuration. These changes
affect package production rather than application features.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [1b8a770](https://github.com/flashinfer-ai/flashinfer/commit/1b8a77034094d26d2f3ad973f48a66ab102e3b62)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:57:06Z
- **提交信息**: ci: build the jit-cache shim wheel on the runner, not in the builder image (#8983)

<!-- .github/pull_request_template.md -->

## 📌 Description

The JIT-cache **shim** wheel is metadata only:
`flashinfer-jit-cache/build_backend.py` writes `_build_meta.py` and the
exact `flashinfer-jit-cache-smXX==<version>` pins, then hands off to
setuptools. It hardcodes the `manylinux_2_28_<machine>` platform tag,
and the package imports only the standard library. It needs no torch,
CUDA toolkit or manylinux image.

Even so, each shim job pulled the full builder image and pip-installed
torch + CUDA wheels it never used. Timings from the 2026-10-31 nightly
([run
41171886142](https://github.com/flashinfer-ai/flashinfer/actions/runs/41171886142)),
self-hosted on-demand CPU runners (cold image pull every job):

| Shim job | Image pull | pip torch/CUDA | Rest | Total |
|---|---|---|---|---|
| cu130 x86_64 | 4.7 min (`pytorch/manylinux2_28-builder:cuda13.0`, 8.2
GB) | 1.3 min (3.0 GB of wheels) | ~0.8 min | 7.5 min |

All six shim jobs took 7.2–8.7 min. This PR:

- adds `scripts/build_jit_cache_shim_wheel.sh`, which builds the shim
with the runner's Python in a throwaway venv (`setuptools>=77`, `wheel`,
`build`). It checks that the wheel is tagged `manylinux_2_28_${ARCH}`,
installs it with `--no-deps`, and asserts the version is
`<version.txt>[.devN]+<cuda label>`;
- switches the shim job in `release-build.yml` to `actions/setup-python`
+ that script, and drops the submodule checkout;
- adds the script to `release.yml`'s PR dry-run paths.

Provider builds are unchanged. Expected effect: shim jobs drop from
about 7.5 min to about 1 min each, about 40 runner-minutes per nightly.
**Wall-clock is unchanged**: shims already run in parallel with the
10–40 min provider builds, which are the critical path into
`validate-flashinfer-jit-cache-providers`.

## 🔍 Related Issues

Follow-up to #8722 (pre-baked AOT builder image). The measurements above
showed the baked image saves little on cold runners, while shims didn't
need an image at all.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ran on the changed files.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
(`test_shim_builds_on_runner_without_builder_image` in
`tests/cpu/jit/test_jit_cache_release.py`)
- [x] All tests are passing (`unittest`, etc.).
(`tests/cpu/jit/test_jit_cache_release.py`,
`tests/cpu/test_build_flashinfer_jit_cache_artifact.py`: 22 passed)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

  Suggested CI test targets: `tests/cpu/jit/`

Ran the script locally on macOS: it produced the same 4.6 KB wheel with
the expected `Version` and three `Requires-Dist` pins. The `ARCH` tag
check rejected the non-manylinux tag as intended. The real Linux build
is exercised by this PR's release dry run.

## Reviewer Notes

- **Conflict with #8722:** both PRs edit the shim job's `env` block
(#8722 sets `DOCKER_IMAGE: ${{ matrix.builder_image }}`). Whichever
lands second should keep this PR's version: the shim job no longer has a
`DOCKER_IMAGE`.
- `build_flashinfer_jit_cache_whl.sh` still accepts
`FLASHINFER_JIT_CACHE_BUILD_TARGET=shim`. CI no longer uses that path; I
left it for local reproduction and can remove it if preferred.
- setuptools prints its existing `project.license` deprecation warning
during the build; that is unrelated to this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Release Builds**
* The JIT-cache shim wheel is now built directly in the release workflow
and checked for the expected version and platform compatibility.
  * Updates to the wheel build process now trigger the release workflow.
* The build runs with a 15-minute limit and no longer uses the previous
container-based artifact build steps.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [33a94c3](https://github.com/flashinfer-ai/flashinfer/commit/33a94c37c69109ccf121c7b872c5bb2c5ced85f2)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:56:16Z
- **提交信息**: ci(aot): cache PR AOT nvcc compiles with the rapidsai/sccache fork (host C++ uncached) (#9031)

## 📌 Description

Caches the PR AOT lane's nvcc compiles with the
[rapidsai/sccache](https://github.com/rapidsai/sccache) fork,
`v0.18.0-rapids.8`, instead of upstream sccache 0.18.0. Host C++ is left
**uncached** on that lane. Release and nightly builds and the GPU test
lanes are unchanged and stay on upstream.

**Why:** PR AOT builds are about 100% cache hits, yet each upstream nvcc
hit costs about 7.4 host CPU-s, because upstream reruns nvcc's
preprocessing to compute the key. The fork caches each translation
unit's dependency list (`-M`) and hashes file contents, so a hit skips
preprocessing entirely.

**Trial: sm80 provider only, x64 cu130.** Runner: AWS self-hosted CPU,
AMD EPYC 7R13 with 64 vCPU, `MAX_JOBS=61`, provider concurrency 1, image
`flashinfer-ci-cu130:20260930-b1420f1`, 1317 nvcc translation units. All
runs were `workflow_dispatch` runs of the trial branch
`jdierksen/sccache-fork-trial-16437d`.

| sccache | provider build | host CPU-s over the build | hit rate |
|---|---|---|---|
| upstream 0.18.0 | 208–214 s (×5) | 9768 / 9860 / 9770 | 100% |
| fork, cold (seeding a new prefix) | 897 s | – | 2.8% |
| fork, warm | **30–35 s (×4)** | **329 / 372 / 437** | 100% |

- **Outputs:** compiled objects aren't byte-identical across the two
flavors, but plain nvcc isn't run-to-run deterministic either: two
direct compiles of the same file to the same `-o` differ. For 40 sampled
objects the `cuobjdump -sass` output is identical. Section tables are
also identical except `.strtab`, which holds symbol names (+21 bytes).
All provider modules pass the lane's import and verification step.

**Full CI, all six AOT lanes.** Seeded by run 42329099609 (cold, 3–5.6 h
per AOT job), then measured by run 42355275083. Baseline: four
upstream-only PR runs from the same day (42347615601, 42346087724,
42345763488, 42345449088). AOT job wall time in minutes:

| lane | upstream (4 runs) | this PR | sibling #9032 (fork + upstream
C++) |
|---|---|---|---|
| x64 cu129 | 43.6–44.8 | **13.2** | 13.2 |
| x64 cu130 | 40.9–44.9 | **11.9** | 12.2 |
| x64 cu134 | 47.6–53.2 | **13.2** | 13.6 |
| arm64 cu129 | 46.2–52.7 | **14.7** | 14.5 |
| arm64 cu130 | 54.3–61.8 | **15.5** | 15.6 |
| arm64 cu134 | 65.6–71.9 | **12.0** | 16.9 |

Per provider on x64 cu130:
- **sm80/sm89** (built in parallel): 6:04 upstream, 0:41 here.
- **sm90a**: 18:52 upstream, 1:15 here, 1:13 on #9032. sm90a has the 413
host-C++ compiles, so caching them buys nothing measurable.

**Changes**
- `scripts/jit_cache_build_common.sh`
  - Adds `FLASHINFER_SCCACHE_NVCC_IMPL=upstream|rapids`.
- `rapids` installs the pinned fork release. The sha256 values are
pinned in the script: GitHub's published asset digests for x86_64 and
aarch64.
- The fork is installed as `/usr/local/libexec/sccache-rapids/sccache`.
Under any other executable name, sccache treats the name as a compiler
to wrap and even `--version` hangs.
- The fork runs as the only server, under key prefix `<tag>-rapids`. Its
keys are incompatible with upstream's, so production prefixes are
untouched.
  - Clears `FLASHINFER_CXX_LAUNCHER`.
- `scripts/task_test_jit_cache_package_build_import.sh`: the PR AOT lane
defaults to `rapids`.
- `tests/cpu/infra/test_jit_cache_providers.py`: covers the `rapids`
setup path (prefix, launchers, and that control commands go to the fork)
and rejection of unknown values.
- `CLAUDE.md`: documents the above.

**Why host C++ is uncached:** `v0.18.0-rapids.8` fails **fatally**, with
no fallback to compiling, on `g++ -MMD` for any file that includes
`<vector>`: `Error computing digest: while reading '/'`. Reproduction on
ubuntu:22.04 with g++ 11:
```
printf '#include <vector>\nint f(){return 1;}\n' > a.cc
sccache c++ -MMD -c a.cc -o a.o   # rc 255
```
`-MD` works, and nvcc's own dependency flags work. A full x64 cu130
build has 530 host-C++ compiles against 16,162 nvcc compiles. 413 of the
C++ compiles are on sm90a, 388 of them `csrc/xqa/tensorMap.cpp`. Leaving
those uncached is this PR's cost. The sibling PR keeps them on upstream.

## 🔍 Related Issues

Supersedes the comparison variant #9032 (fork for nvcc + upstream
sccache for host C++), closed after measurement: same AOT time, more
shell.

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

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/cpu/infra/test_jit_cache_providers.py`

Any CI run includes the AOT lanes, which are what this PR changes. The
`<tag>-rapids` S3 prefixes are already seeded (run 42329099609).

Checked locally (macOS + podman ubuntu:22.04): the new CPU tests in
`tests/cpu/infra/test_jit_cache_providers.py` plus the existing
`test_sccache_setup_uses_server_side_compilation`, run standalone (the
module imports torch); and a smoke test of the real
install/setup/collect path with the pinned aarch64 binaries against the
public bucket in read-only mode (servers start, a compile goes through
each launcher, stats are collected, no daemon left behind).

## 🔬 Experimental Track

- [ ] This PR is **experimental**.

```experimental-tests
```

## Reviewer Notes

- **Sibling #9032** (closed) ran a second, upstream server for host C++
at the cost of more shell (two servers, two stats sets); measured AOT
time was the same.
- **Pin maintenance:** the fork is about 1600 commits ahead of upstream
0.18.0. The checksums are pinned in `jit_cache_build_common.sh`.
- **Cold rebuild on fork bumps:** changing the fork version or key
prefix rebuilds every provider cold once (3–5.6 h per AOT job when
seeding these prefixes).
- **GPU test lanes:** they still read the upstream prefix. It is now
refreshed by nightly/release builds and the GPU lanes themselves rather
than by PR AOT lanes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated GPU build validation to use a verified compiler cache for
NVIDIA device compilation, with separate cache entries from release and
nightly builds.
* Host C++ compilation remains uncached in this configuration.
Unsupported cache selections now fail with an error.
* **Documentation**
* Clarified how compiler caching differs across pull request, release,
nightly, and GPU test builds.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6ff8295](https://github.com/flashinfer-ai/flashinfer/commit/6ff8295d3b6087708c91c71d76ef4449d5bac762)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-11T00:55:21Z
- **提交信息**: test(jit): skip Linux CI bash cases on Windows; read repo files as UTF-8 (#9288)

<!-- .github/pull_request_template.md -->

## 📌 Description

`tests/cpu/infra/test_jit_cache_release.py` fails 7 of 13 cases on
native Windows arm64; all pass on Linux and under WSL2.

- **Six cases are skipped on Windows**
(`test_jit_cache_python_setup_hardens_incomplete_downloads` and the five
`test_sccache_uses_release_for_all_cuda_versions` cases). They `bash -c`
a script that sources `scripts/jit_cache_build_common.sh`. That helper
is Linux release tooling: it downloads the `unknown-linux-musl` sccache,
accepts only `x86_64|aarch64`, and relies on `/proc` and `docker run
--rm`. Only Linux build scripts and `release.yml` use it, so a Windows
wheel build would need its own driver rather than this script. On native
Windows, the bash that ships with Git starts and then fails inside the
script (`CalledProcessError`). For that reason the gate checks
`sys.platform == "win32"` instead of whether bash exists. Linux CI still
runs these cases.
- **Repo files are read as UTF-8.** `Path.read_text()` with no encoding
uses the locale's code page, which is cp1252 on Windows. Reading
`.github/workflows/pr-test.yml` that way fails on a UTF-8 emoji
(`UnicodeDecodeError: 'charmap' codec can't decode byte 0x8f`). Every
repo-file read in the test now passes `encoding="utf-8"`, and so do the
four reads in `ci/validate_cuda_versions.py` that the test exercises.
`requirements.txt` and `pyproject.toml` have em dashes in comments:
cp1252 decodes them as garbled text, and cp932 (Japanese-locale Windows)
raises `UnicodeDecodeError`. `release.yml` and `nightly-release.yml`
also contain non-ASCII characters, so the workflow-structure tests would
fail on Windows the same way.

This changes tests and CI tooling only; no runtime or kernel code
changes. Editing the validator triggers the Release dry run and the CI
image builds on this PR.

## 🔍 Related Issues

Part of the native Windows (WoA) bring-up; related to #8431.

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

  Suggested CI test targets: `tests/cpu/infra/test_jit_cache_release.py`

Local runs, on macOS arm64 only:
- `pytest tests/cpu/infra/test_jit_cache_release.py`: 17 passed.
- Loading the module with `sys.platform` set to `win32` evaluates the
skip on exactly the six bash-driven cases.

Not run on native Windows yet.

## Reviewer Notes

The pre-commit hooks ran on the changed files only (`pre-commit run
--files`), not with `--all-files`.

I think the skip should be permanent rather than temporary. These cases
test Linux CI scripts, and Linux CI covers them no matter which platform
runs the test. When Windows wheel builds land, their build driver should
get its own tests.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Automated checks now account for platform differences when running
shell-script cases, improving test-suite compatibility across Windows
and Linux environments.
* Configuration and workflow files are read with explicit text encoding
in relevant checks, supporting consistent test results across
environments.
* CUDA version validation also reads its configuration and related files
with explicit text encoding; validation rules and command-line behavior
remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4808
- **最后更新**: 2026-11-11T22:32:58Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: FV SuperAgent

## AI分析总结

## FastVideo 仓库昨日提交记录分析（1/1 批，共 2 条提交）

### 1. 主要更新类型
- **文档更新**为主：两条提交均属于文档/维护类变更，无核心功能代码修改。
- 包含一条轻微的 Bug 修复（首页新闻断言更新）。

### 2. 关键变更点及与项目整体方向的关系
- **README 链接修复与支持矩阵更新（#2089）**：将 README 链接修复与模型/硬件支持矩阵的更新合并提交。支持矩阵是 FastVideo 这类推理加速框架的核心文档元素，它向用户清晰展示哪些模型、量化方案、GPU 后端得到支持，直接影响用户选型和使用预期。链接修复则保证文档导航（Documentation、Cookbook、Quick Start 等入口）的可用性。
- **首页新闻断言更新（#2088）**：将首页 news 区块的公告内容更新为 "PAN 2" 发布消息。这表明项目正积极跟进最新研究成果（PAN 2 可能是新的视频生成/加速模型或论文），保持官网/README 作为项目动态的第一窗口。

### 3. 对项目的影响和潜在意义
- 这类提交虽然不涉及核心算法或性能代码，但对**用户体验和项目专业度**有直接提升：支持矩阵的准确性帮助用户快速判断是否适用于自身环境，减少试错成本。
- 新闻公告的及时更新体现了项目**活跃维护状态**，有助于在开源社区维持关注度和可信度。
- "合并提交"的工作方式（把链接修复和支持矩阵更新合并为一个 PR）也反映出团队在文档维护上追求更清晰、原子化的变更历史。

### 4. 值得关注的技术点
- **支持矩阵的结构**：值得关注矩阵覆盖的维度——是否包含新模型系列（如 Wan、HunyuanVideo、Mochi 等）、新量化方法（FP8、DeepSeek 风格量化）、新硬件（H100/H200/B200）以及分布式并行策略的支持情况，这些是 FastVideo 核心竞争力的体现。
- **PAN 2 的含义**：需结合提交 diff 或项目 discussions 判断 PAN 2 是新论文、新模型还是新功能发布，这可能预示下一阶段的功能路线。
- 两条提交均带有 Co-authored-by 标记，其中 #2088 的合作者为 `fv-superagent`，暗示项目可能引入了**自动化 agent 辅助维护**的协作流程，这是当前 AI 辅助开发趋势的一个缩影。

### 5. 基于 README 背景对项目发展的影响
FastVideo 是 hao-ai-lab 推出的视频生成推理加速框架，README 中提供了 Documentation、Cookbook、Quick Start、Weekly Dev Meeting 等完善的社区与文档体系，并配有 Slack 社区入口，说明项目处于**高速迭代、积极运营**的阶段。

昨日这两条提交虽属"轻量级"维护，但与项目发展方向高度一致：
- **支持矩阵更新**是 FastVideo 核心价值主张（广模型、广硬件、广后端兼容）的直接文档映射，确保文档与代码能力同步演进，避免"文档漂移"。
- **首页 news 更新**则持续对外传递项目进展（PAN 2 公告），配合 Slack、周会等渠道，构成完整的开发者沟通闭环。
- 两者共同强化了项目的**文档质量和社区透明度**，这是开源框架获取用户信任、吸引贡献者的基础工程。

总体而言，这组提交属于项目健康运营的日常维护，虽不改变技术路线，但对保持文档准确性、用户转化率和社区活跃度具有持续的正向作用。

## 详细提交记录

### [eee667d](https://github.com/hao-ai-lab/FastVideo/commit/eee667df7702aa3b115be7746b97c9ab11bc6a2d)

- **作者**: FV SuperAgent
- **时间**: 2026-11-11T21:32:10Z
- **提交信息**: [docs] Combine the README link fix and the support-matrix update (#2089)

Co-authored-by: Aryan Kumar <156166681+aryan5v@users.noreply.github.com>

### [8611b44](https://github.com/hao-ai-lab/FastVideo/commit/8611b444497959c94fe38c8a8a7722fd76d4f752)

- **作者**: FV SuperAgent
- **时间**: 2026-11-11T21:31:37Z
- **提交信息**: [bugfix] Update the homepage news assertion to the PAN 2 announcement (#2088)

Co-authored-by: fv-superagent <352344047+fv-superagent@users.noreply.github.com>

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34911
- **最后更新**: 2026-11-12T01:45:12Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Sayak Paul, Akhil Gupta, Dhruv Nair

## AI分析总结

# huggingface/diffusers 昨日提交分析（1/1 批，共 4 条）

## 1. 主要更新类型

- **重构与代码质量提升**：类型注解补全、依赖版本检查机制规范化、测试文件清理，占主导地位。
- **Bug 修复**：LoRA 文本编码器 alpha_pattern 键派生逻辑的修复。
- 整体属于维护性迭代周期，无大规模新功能引入。

## 2. 关键变更点与项目方向的关系

- **类型注解更新（#15089）**：为模型补齐返回类型标注，提升静态检查与 IDE 体验，符合大型开源库工程化的长期方向。
- **移除冒烟测试文件（#15160）**：精简测试基础设施，减少维护负担。
- **LoRA alpha_pattern 修复（#14972）**：改为从 LoRA 模块名派生文本编码器的 alpha_pattern 键，并使用 `removesuffix` 重构，属于 PEFT/LoRA 适配层的健壮性修复，直接影响用户加载 LoRA 权重的正确性。
- **依赖最低版本强制检查（#15148）**：在可用性检查中加入版本下限校验，解析失败时"fail closed"，并从统一依赖表读取版本下限生成升级提示。这使 diffusers 对 PyTorch、accelerate、bitsandbytes 等生态依赖的兼容性管理从"被动探测"转为"主动约束"。

## 3. 对项目的影响和潜在意义

- LoRA 修复直接降低用户在文生图/微调场景中权重加载出错的概率，提升核心工作流可靠性。
- 依赖版本门控能在问题发生前给出明确的升级指引，减少由环境不一致导致的"幽灵 bug"报告，降低维护者排障成本。
- 类型与测试清理为后续 CI 严格化和自动化重构铺路。
- 冒烟测试移除需留意：若无等价覆盖，可能削弱对基础生成流程的回归保护。

## 4. 值得关注的技术点

- alpha_pattern 键与模块命名的耦合方式：依赖命名约定的派生逻辑需与 PEFT 上游保持同步，存在潜在脆弱点。
- "fail closed"的版本解析策略与统一依赖表（deps table）设计：体现了配置集中化、错误信息可操作化（带 `-U` 升级提示）的工程实践，值得其他库借鉴。
- `removesuffix` 的使用反映了对 Python 版本基线的隐含依赖，需与最低支持版本策略一致。

## 5. 基于 README 背景的项目发展影响

diffusers 是 Apache 2.0 许可的扩散模型生成库，长期目标是提供稳定、可扩展的模型加载与推理接口。本批提交虽属维护性工作，但方向高度一致：通过类型、依赖约束和 PEFT 修复提升库的**可靠性与可维护性**，这正是开源扩散模型生态走向生产级应用的必要基础。短期看，用户将获得更清晰的兼容性报错和更正确的 LoRA 加载行为；长期看，这些质量基础设施为后续新模型架构和量化功能（如 SDNQ 相关安装提示所示）的稳定落地提供了支撑。综合而言，这批提交强化了项目的工程质量底座，使 diffusers 在功能迭代之外持续巩固其作为扩散模型标准基础设施的地位。

## 详细提交记录

### [0905b66](https://github.com/huggingface/diffusers/commit/0905b667fe3f37f43b6ef9c6e05ad20636206938)

- **作者**: Sayak Paul
- **时间**: 2026-11-11T10:39:07Z
- **提交信息**: [chore] update return type annotations for models. (#15089)

update return type annotations for models.

### [918ed48](https://github.com/huggingface/diffusers/commit/918ed48b25d4e659e0a2439d2edf06e1b8365710)

- **作者**: Sayak Paul
- **时间**: 2026-11-11T10:38:45Z
- **提交信息**: [chore] remove smoke test file. (#15160)

remove smoke test file.

### [2458000](https://github.com/huggingface/diffusers/commit/2458000e824a9db14a4771ae5f451f226e3bd816)

- **作者**: Akhil Gupta
- **时间**: 2026-11-11T09:55:53Z
- **提交信息**: fix: derive text-encoder alpha_pattern keys from the LoRA module name (#14972)

* fix: derive text-encoder alpha_pattern keys from the LoRA module name

* fix: derive text-encoder alpha_pattern keys from the LoRA module name

* upload updated peft_utils.py

* Delete src/diffusers/utils/peft_utils.py

* use removesuffix per review feedback

---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [44406f1](https://github.com/huggingface/diffusers/commit/44406f1ee93cd5d23ac1b6c2b6f4f0457bed12b4)

- **作者**: Dhruv Nair
- **时间**: 2026-11-11T09:47:15Z
- **提交信息**: [core] Enforce minimum supported versions in availability checks (#15148)

* [core] Enforce minimum supported versions in availability checks

* Apply style fixes

* Address review: version-parse fallback, accelerate messages, inline nn.LayerNorm, remaining floor checks

* Test above-floor version in availability check

* Fail closed on unparseable dependency versions

* Read version floors in quantizer messages from the deps table

* Use upgrade-capable install hints and drop duplicate bitsandbytes check

* Add -U to the SDNQ install hint

---------

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 432
- **最后更新**: 2026-10-19T05:38:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13360
- **最后更新**: 2026-11-11T14:12:15Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 2
- **主要提交者**: Zhongjie Duan, Hong Zhang

## AI分析总结

# DiffSynth-Studio 昨日提交分析

## 1. 主要更新类型
- **功能新增为主**：新增 MiniMax-H3-Image 模型支持，包括 pruned 模型（table-pruned DiT、entropack）、量化 VAE、Lora 层等
- **文档更新**：补充 MiniMax-H3-Image 相关文档和 news
- **版本迭代**：连续发布 2.2.1 → 2.2.2 版本，发布节奏较快

## 2. 关键变更点及与项目方向的关系

- **MiniMax-H3-Image 全链路集成（#1815、#1818）**：从基础模型支持到 CFG、Lora、pruned 变体，是一次完整的模型接入流程，体现了项目作为**多模型聚合推理平台**的核心定位——持续接入业界最新的图像生成模型。
- **模型配置基于 JSON 注册（#1819）**：将模型配置从硬编码迁移到 JSON 文件驱动，属于**架构层面的重构**，降低了后续新增模型的接入成本，符合项目长期扩展需求。
- **pruned 模型支持（#1818）**：支持 table-pruned DiT、entropack 压缩及量化 VAE，表明项目开始关注**推理效率和模型轻量化**，这对部署场景意义重大。

## 3. 对项目的影响和潜在意义

- **降低资源门槛**：pruned 和量化支持使用户可以在更少的显存下运行高质量模型，扩大用户覆盖面
- **工程化水平提升**：JSON 配置注册机制使模型管理更规范，减少维护负担
- **快速迭代信号**：一天内连续 8 个提交、跨 3 个版本号，说明团队在积极跟进 MiniMax 生态，保持技术竞争力

## 4. 值得关注的技术点

- **Lora 路径复用与 TE（Text Encoder）重用**：体现了对多模型共享组件的优化思路，可减少重复加载开销
- **entropack 压缩格式**：较新的模型压缩方案，值得深入研究其在图像生成任务中的精度-速度权衡
- **JSON 驱动的模型注册机制**：可作为其他模型框架的参考设计模式

## 5. 对项目发展的整体影响

结合 README 可知 DiffSynth-Studio 是 ModelScope 生态中的**统一扩散模型推理/训练框架**，本次提交群体现了两条清晰的发展线：一是**模型覆盖广度**上快速跟进 MiniMax-H3-Image 等新模型；二是**工程深度**上通过配置解耦和模型压缩提升框架的可扩展性与实用性。两者结合有助于项目在开源社区中巩固"一站式扩散模型平台"的定位，吸引更多模型贡献者和部署场景用户。

## 详细提交记录

### [55fdfb2](https://github.com/modelscope/DiffSynth-Studio/commit/55fdfb23987672528d2cf71f4a9d44aba44c1863)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T13:46:06Z
- **提交信息**: update minimax-h3-image docs (#1822)

### [da8e83b](https://github.com/modelscope/DiffSynth-Studio/commit/da8e83b588977a98a8cd7bac082219a312942e82)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T13:12:10Z
- **提交信息**: update to version 2.2.2 (#1821)

### [19dd71a](https://github.com/modelscope/DiffSynth-Studio/commit/19dd71afb9b45c27c32ebdb27b9a2dd266d33454)

- **作者**: Hong Zhang
- **时间**: 2026-11-11T11:38:21Z
- **提交信息**: update entropack example (#1820)

### [05d7575](https://github.com/modelscope/DiffSynth-Studio/commit/05d7575329046a041434f6999bebe2969fe3cca4)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T11:29:26Z
- **提交信息**: register model config based on json files (#1819)

### [3cc1b7b](https://github.com/modelscope/DiffSynth-Studio/commit/3cc1b7b034f896861de8215ec4993224e9d5b8bc)

- **作者**: Hong Zhang
- **时间**: 2026-11-11T10:28:52Z
- **提交信息**: Support MiniMax-H3-image pruned models (#1818)

* support table-pruned dit and entropack

* refine lora path

* minor fix

* reuse te

* quant vae

* minor fix

* update news

* update news

### [c84af15](https://github.com/modelscope/DiffSynth-Studio/commit/c84af15258b76e074586522f55328b4c8565195b)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T08:24:25Z
- **提交信息**: Update lora layers of minimax-h3-image (#1817)

* update version to 2.2.1

* update lora layers of minimax-h3-image

### [563963d](https://github.com/modelscope/DiffSynth-Studio/commit/563963d16ac67be86db7eaec65405632ca0f4a4c)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T07:55:23Z
- **提交信息**: update version to 2.2.1 (#1816)

### [6ccfd64](https://github.com/modelscope/DiffSynth-Studio/commit/6ccfd64d90421ef600326644697d80ae5eb74aff)

- **作者**: Zhongjie Duan
- **时间**: 2026-11-11T06:13:14Z
- **提交信息**: support MiniMax-H3-Image (#1815)

* support MiniMax-H3-Image

* support minimax-h3-image cfg

* refine code

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38768
- **最后更新**: 2026-11-12T02:32:01Z

## 提交统计

- **昨日提交总数**: 98
- **提交者数量**: 57
- **主要提交者**: dingdangmao, Po-Han Huang (NVIDIA), Yuhao Yang

## AI分析总结

# SGLang 昨日提交综合分析（98 条）

## 1. 主要更新
- **性能优化（约 26 条）**：attention 内核、投机解码、MoE GEMM、diffusion 编码器与分布式通信。
- **Bug 修复（约 35 条）**：覆盖调度器、API 参数校验、指标与 tokenizer、多模态占位符、约束解码、AMD 后端、diffusion 加载等。
- **功能新增（约 14 条）**：Kimi-K3.1 DFlash2、LTX-2.5、Unlimited-OCR、GLM-4.7-Flash 等新模型，NPU 权重缓存、kv-events 多模态路由、HEIF 解码、FA4 FP8 KV cache、投机解码接受率估计器、sgl-router 生产 API。
- **重构（约 13 条）**：设备中立图后端、MoE 后端清理、内核打包调整、调度器请求列表统一编辑入口。
- **CI 与文档（约 10 条）**：AMD Spur/nightly runner 迁移、Arm64 与 CUDA 13.4 镜像、基准测试与调优文档。

## 2. 关键变更与项目方向
- **旗舰模型内核级压榨**：DeepSeek-V4/V4.1 的 `expand_prefill_causally` 批内 token block 扩展、top-k 缓冲移入动态共享内存、DSA FP8/DSv4.1 FP4 的 LiteTopK indexer 与稀疏 MLA prefill 小头优化；Kimi-K3.1 的 Per-M decode GEMM、侧流 attention GEMM、多机 NVLink multimem logits all-gather、gfx1250 aiter Triton MLA decode。
- **投机解码形成体系**：radix top-k verify、split-KV EAGLE verify 支持 attention sink、FlashInfer `uniform_q_len` 接入 EAGLE plan、DSFlash/DSpark 在 ReplaySSM spec ring 验证，以及 DSpark confidence-scheduled verification 的在线接受率估计器。
- **MoE 架构收敛**：移除 triton_kernel 后端与 SM120 top-22 路径，改为 JIT 内核反量化 MXFP4 权重；Ascend MoE AllGather 优化、overlap 启动加载并行推进。
- **多模态与扩散成熟化**：SANA-Video、FLUX.2、MiniMax-H3、Anima、LTX 均有提交；placeholder token 修复、CFG 归一化、HEIF/BMP/TIFF 支持、客户端媒体错误分类，标志链路从"能跑"走向健壮可用。
- **跨硬件与生产化**：NPU 权重缓存、Apple MPS BF16、Arm CPU 镜像；AMD 侧 breakless graph 原位写回、fused KDA BF16 state + Quark 权重、host sync 消除、MoRI DSA 状态配对；sgl-router 生产 API 与小请求体跳过 worker handoff。

## 3. 项目影响
性能提交直接提升 DeepSeek 与投机解码的吞吐延迟，强化 "Fast inference" 卖点；大规模 API 校验（logprob_start_len、top_logprobs、scheduler-recv-interval、tool call 缺函数名返回 400 而非 500）与错误语义规范化（4xx 直通）降低生产误用。PP prefill 中断清理、调度器死亡即退出、llguidance matcher 免中毒等修复显著降低长时运行挂死风险。sgl-kernel 停止捆绑 triton_kernels 并改为 JIT，减小 wheel 体积、消除上游依赖漂移。调度器 move() + retirer 统一入口显示调度路径正收敛为单一安全编辑点，减少状态不一致。

## 4. 技术关注点
- **BF16x3 混合精度**用于 Blackwell decode 的 mHC mix，是新数值格式的生产化尝试。
- **attention sinks 进入 EAGLE verify kernel**，将滑动窗口机制与投机解码结合。
- **FA4 SM90 FP8 e4m3 KV cache**（head_dim 256/512，面向 Gemma-4），是长上下文低成本推理关键。
- **设备中立图后端基类分三步落地**，为非 CUDA 后端抽象铺路，后续提交值得追踪。
- **custom-ar-v2 push epoch / pull semaphore 重构**，影响多卡通信正确性。
- **CPU offload 下 DSA indexer 参数常驻 GPU**，是性能与显存的典型权衡。
- AI 辅助开发深度化：Claude Opus/Fable、Cursor 等频繁共同署名，解释了高提交吞吐。

## 5. 总体判断
结合 README 定位，三条主线清晰：围绕 DeepSeek-V4.1、Kimi-K3 等前沿模型持续做内核级调优以保持速度领先；投机解码与 MoE 优化已成系统性技术栈而非零散修补；从单 GPU 内核向多硬件（NPU/Arm/MPS/AMD）、多模态（diffusion/OCR/video）、生产服务（sgl-router）全面铺开。项目正从研究型推理引擎演进为通用生产级多模态推理平台，并进入稳定性优先的成熟期。

## 详细提交记录

### [fc6d3b6](https://github.com/sgl-project/sglang/commit/fc6d3b6f91bb3aecc03aff8183c212d0ef8888a1)

- **作者**: Chunan Zeng
- **时间**: 2026-11-11T22:40:37Z
- **提交信息**: [Perf] dsv4: Size expand_prefill_causally's token block by batch size (#49499)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [026a145](https://github.com/sgl-project/sglang/commit/026a145a3aece77a4dc7e46ccbc791e4d19fe60e)

- **作者**: weireweire
- **时间**: 2026-11-11T22:39:43Z
- **提交信息**: [Perf] [NVIDIA] dsv41: Run the side-stream mHC mix in BF16x3 for Blackwell decode batches (#48456)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [d800cb8](https://github.com/sgl-project/sglang/commit/d800cb859e85fc00e7b0e494d72f30fbd1dcbca1)

- **作者**: WenhaoZhang
- **时间**: 2026-11-11T21:41:51Z
- **提交信息**: [Feat] comfyui: Run LTX-2.5 / LTX-2.3 in SGLD integrated mode (#43583)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [1017f57](https://github.com/sgl-project/sglang/commit/1017f576607a4f3a3318352e0cfc35d9a8909fc0)

- **作者**: Jian Chen
- **时间**: 2026-11-11T21:30:22Z
- **提交信息**: [Feat] gdn: run DFLASH and DSPARK verify on the ReplaySSM spec ring (#46185)

Co-authored-by: Jian Chen <jic188@ucsd.edu>
Co-authored-by: Zihan Zhang <tiancaizhangdaxian@sjtu.edu.cn>
Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [884d29b](https://github.com/sgl-project/sglang/commit/884d29b20728263ce42f4bec98cc07d291d251f1)

- **作者**: Jian Chen
- **时间**: 2026-11-11T21:28:23Z
- **提交信息**: [Perf] spec: radix top-k for speculative verify target probabilities (#46186)

Co-authored-by: Jian Chen <jic188@ucsd.edu>
Co-authored-by: Zihan Zhang <tiancaizhangdaxian@sjtu.edu.cn>
Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [ba4356d](https://github.com/sgl-project/sglang/commit/ba4356ddde71d0a78a12613819c6904c93c28fce)

- **作者**: Shangming Cai
- **时间**: 2026-11-11T21:03:03Z
- **提交信息**: [Fix] sgl-router: Skip the worker handoff for small request bodies (#49646)

### [e87d36a](https://github.com/sgl-project/sglang/commit/e87d36aeb13aed4ea4284857b11520480aebecc6)

- **作者**: Shangming Cai
- **时间**: 2026-11-11T21:02:04Z
- **提交信息**: [Refactor] mm: import MM_PAD_SHIFT_VALUE instead of re-declaring it (#49715)

### [94a4c44](https://github.com/sgl-project/sglang/commit/94a4c4481372fca9bd24d1a20f6af1269b9af1aa)

- **作者**: DonggeYang
- **时间**: 2026-11-11T19:34:51Z
- **提交信息**: [Feat] [Apple] mps: Serve Unlimited-OCR v2 BF16 on the Torch MPS runtime (#47921)

### [9cda0f6](https://github.com/sgl-project/sglang/commit/9cda0f637b5e570afb88b8b9a73ec28c0dbbd0a0)

- **作者**: Mick
- **时间**: 2026-11-11T19:32:23Z
- **提交信息**: [CI] diffusion: Stabilize test execution and resource usage (#49564)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [9599979](https://github.com/sgl-project/sglang/commit/95999790a4a201caf8a142c95711fe5af329a39b)

- **作者**: gausah01
- **时间**: 2026-11-11T19:04:51Z
- **提交信息**: [CI] arm64: Publish Arm CPU Docker images (#48410)

### [56e38df](https://github.com/sgl-project/sglang/commit/56e38dfe0fdb964af402ba22693bb11898ce88d8)

- **作者**: akhilg-nv
- **时间**: 2026-11-11T18:33:42Z
- **提交信息**: [Fix] dsv4/topk_v2: Move the cluster kernels' top-k buffer to dynamic shared memory (#49476)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [07a6c95](https://github.com/sgl-project/sglang/commit/07a6c9554881379075dd2bea575be788e40c21b9)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-11T18:33:04Z
- **提交信息**: [Perf] flashinfer-autotune: Tune MoE with varied warm-up tokens (#49497)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [7e9c559](https://github.com/sgl-project/sglang/commit/7e9c55927f147b31f580854778a37b1fcbd416df)

- **作者**: Michael
- **时间**: 2026-11-11T18:19:55Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX GLM-5.2 MXFP4 MTP curve on MI35x (#49614)

### [8da0649](https://github.com/sgl-project/sglang/commit/8da0649395617a9c7d38fa799b049829ffd38cfc)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-11T17:47:12Z
- **提交信息**: [Fix] openai: Reject assistant tool calls without a function name (HTTP 500 -> 400) (#49475)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a99de6](https://github.com/sgl-project/sglang/commit/4a99de617f35c84138df9de541ea5fffd64235a2)

- **作者**: DarkSharpness
- **时间**: 2026-11-11T17:47:04Z
- **提交信息**: [Perf] [NVIDIA] attention: Add opt-in LiteTopK prefill indexer top-k for DSA (FP8) and DeepSeek-V4.1 (FP4) on SM100 (#47469)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Ziqi Yin <ziqi003@e.ntu.edu.sg>

### [983455a](https://github.com/sgl-project/sglang/commit/983455aeed423cf5b46931218e0a3f60b6745124)

- **作者**: DarkSharpness
- **时间**: 2026-11-11T17:10:13Z
- **提交信息**: [Fix] test: Seed the retracted queue through move() in test_prealloc_token_usage (#49868)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b174f4b](https://github.com/sgl-project/sglang/commit/b174f4bb4fe0f316cf625aa5441f0ea5bd65cd84)

- **作者**: Saigyouji-Yuyuko
- **时间**: 2026-11-11T14:59:09Z
- **提交信息**: [Fix] simulator: Keep the replaced HiCache storage workers alive (#49825)

### [88590cf](https://github.com/sgl-project/sglang/commit/88590cf536d01c8b669fe0a7adb9dcf7de4612ce)

- **作者**: Michael
- **时间**: 2026-11-11T14:33:21Z
- **提交信息**: [CI] [AMD] spur: Schedule stage-c-test-large-8-gpu-amd-mi35x on the Spur runners (#49387)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5ba41e2](https://github.com/sgl-project/sglang/commit/5ba41e2905c6f26703a8bff4cda81306bb42a947)

- **作者**: Michael
- **时间**: 2026-11-11T14:32:58Z
- **提交信息**: [CI] [AMD] spur: Run PR Test (AMD)'s scheduled stage-b MI35x job on the Spur runners (#49389)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7b4cf85](https://github.com/sgl-project/sglang/commit/7b4cf8589e727956adaa3facaec332f6c83d54c5)

- **作者**: Ziyi Xu
- **时间**: 2026-11-11T14:13:12Z
- **提交信息**: [Refactor] custom-ar-v2: Move the DPX pair stages into their own header (#49370)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [426e604](https://github.com/sgl-project/sglang/commit/426e60459831389e2a89402b29976ab094a85bb2)

- **作者**: vOv
- **时间**: 2026-11-11T14:12:22Z
- **提交信息**: [Perf] diffusion: Run SANA-Video 2.0 anchor attention on BF16 inputs at quality=high (#49219)

Signed-off-by: cr-gao <gaochenrui@sjtu.edu.cn>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [aef6cf1](https://github.com/sgl-project/sglang/commit/aef6cf1ab49392da64b89abd5333c4c235ece99c)

- **作者**: Kolade Fajimi
- **时间**: 2026-11-11T14:11:54Z
- **提交信息**: [Fix] GLM-4.7-Flash: Load compressed-tensors W4A16 checkpoints (#49531)

### [163c242](https://github.com/sgl-project/sglang/commit/163c2424aaae00bea7c990dcd12bac4756e1a486)

- **作者**: yz-wqf
- **时间**: 2026-11-11T14:11:20Z
- **提交信息**: [Perf] [SM100] attention: optimize sparse MLA prefill for small heads (#48891)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0f0ed7f](https://github.com/sgl-project/sglang/commit/0f0ed7f24fef75dadeffcc3e9311dcacda472cbd)

- **作者**: misha-chertushkin
- **时间**: 2026-11-11T14:10:53Z
- **提交信息**: [Perf] attention: Support attention sinks in the split-KV EAGLE verify kernel (gpt-oss) (#47513)

Co-authored-by: Hasegawa Takuya <7776462+rluisr@users.noreply.github.com>

### [bf8c994](https://github.com/sgl-project/sglang/commit/bf8c994ca87d9076a7894b21a202939c4b9fb92b)

- **作者**: SovietPower
- **时间**: 2026-11-11T14:10:25Z
- **提交信息**: [Fix] metrics: Populate pending_prealloc_token_usage (#44236)

### [23a45fd](https://github.com/sgl-project/sglang/commit/23a45fd33921164fa440fd7c28cc63341259c28c)

- **作者**: Michael
- **时间**: 2026-11-11T12:31:36Z
- **提交信息**: [CI] [AMD] nightly: Stop running DeepSeek-V3.2 (#49763)

### [426cca6](https://github.com/sgl-project/sglang/commit/426cca6aa7a516e265b042202abf77b2cb5ac61d)

- **作者**: Yuhao Yang
- **时间**: 2026-11-11T12:30:43Z
- **提交信息**: [Feat] dflash: Serve the Kimi-K3.1 DFlash2 sliding-window MLA draft (#49621)

Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [4bf9ca2](https://github.com/sgl-project/sglang/commit/4bf9ca2a3bf7f8dd2e1c2ea6e63d8d8059b46426)

- **作者**: chenxu214
- **时间**: 2026-11-11T12:12:14Z
- **提交信息**: [Fix] [NPU] MoE: Optimize Ascend MoE AllGather (#49277)

Co-authored-by: Even Zhou <even.y.zhou@outlook.com>

### [f3937da](https://github.com/sgl-project/sglang/commit/f3937daee1cb575d5a8081a0f0455be7382a79e3)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-11T11:53:35Z
- **提交信息**: [Test] dsa: Stub _dcp_topk_length_buffer in the eager-metadata no-host-sync test (#49821)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6047c17](https://github.com/sgl-project/sglang/commit/6047c17aeb558ffefc284121216b1b5a10894928)

- **作者**: dingdangmao
- **时间**: 2026-11-11T11:13:11Z
- **提交信息**: [Fix] scheduler: Reserve member rows of beam leaders admitted in the same prefill (#46855)

Co-authored-by: apex-mochen <265981728+apex-mochen@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [7699e31](https://github.com/sgl-project/sglang/commit/7699e31092b46945a7e00f704e87c7b29be012c4)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T11:00:51Z
- **提交信息**: [Refactor] scheduler: Remove the remaining direct request-list edits (#49751)

### [b4ef5cc](https://github.com/sgl-project/sglang/commit/b4ef5cc9b52d3e0012c0ce26e2eb4f742d76e623)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-11T10:45:23Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main a0f8080c (#49787)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0662d5c](https://github.com/sgl-project/sglang/commit/0662d5c44aa9c2fb7cd476754e27c68a61493c14)

- **作者**: 黄孝君
- **时间**: 2026-11-11T10:36:02Z
- **提交信息**: [CI] [NPU] docker: Bump SGLANG_KERNEL_NPU_TAG to 2026.11.0.post3 (#49750)

### [f39ac6b](https://github.com/sgl-project/sglang/commit/f39ac6b55b5556a82c6b8a7c129adaf8754a1fad)

- **作者**: dorado269
- **时间**: 2026-11-11T10:24:25Z
- **提交信息**: [Fix] metrics: Avoid blocking the scheduler on KV metrics backpressure (#46820)

Signed-off-by: yihou <yihou@amd.com>

### [75e8d54](https://github.com/sgl-project/sglang/commit/75e8d543dcc2b462632d25e0f9f1dc9364fda291)

- **作者**: dorado269
- **时间**: 2026-11-11T10:22:27Z
- **提交信息**: [Fix] dsa: Remove host syncs from rank-divergent eager paths (#46830)

Signed-off-by: yihou <yihou@amd.com>

### [34dfacc](https://github.com/sgl-project/sglang/commit/34dfaccc57d928f046317c2e3d9e16bd69837d9b)

- **作者**: Alan Kao
- **时间**: 2026-11-11T10:02:09Z
- **提交信息**: [Perf] [AMD] aiter: write the breakable-graph attention output in place (#49567)

### [ebd957c](https://github.com/sgl-project/sglang/commit/ebd957c89325238612773ce88e380a04fa86a449)

- **作者**: Yu-Yun Chang
- **时间**: 2026-11-11T09:53:39Z
- **提交信息**: [Perf] [AMD] kimi-k3: Run the fused KDA decode with a BF16 state and Quark weights (#41794)

### [2c5b680](https://github.com/sgl-project/sglang/commit/2c5b680aa6294bcd246366aba197a42f876b75f7)

- **作者**: Shuwen Wang
- **时间**: 2026-11-11T09:07:20Z
- **提交信息**: [Fix] responses: Merge replayed tool calls into the preceding commentary message (#47096)

### [6be0d75](https://github.com/sgl-project/sglang/commit/6be0d75ae060699396a6cab5f356ef499b90de5a)

- **作者**: WenhaoZhang
- **时间**: 2026-11-11T09:02:44Z
- **提交信息**: [Fix] diffusion: MiniMax-H3 follow-ups: load the public H3-Image snapshot, keep H3 video conditioning, fix profiler test pollution (#49574)

### [99da28d](https://github.com/sgl-project/sglang/commit/99da28d6fd7ce5d2347464165c444dc7e447157c)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T08:55:20Z
- **提交信息**: [Perf] diffusion: Size FLUX.2 checkpoints for the all-resident auto tier (#49444)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [68339b5](https://github.com/sgl-project/sglang/commit/68339b5511d43658e0f17b766244b96628c7c469)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-11T08:55:02Z
- **提交信息**: [Perf] diffusion/anima: Reuse timestep modulation across serial CFG branches (#49504)

### [23f12b7](https://github.com/sgl-project/sglang/commit/23f12b7cb600d02a07c122bdedee0ca3c7134ca3)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T08:54:45Z
- **提交信息**: [Fix] diffusion: Stop normalizing bright edit inputs a second time before VAE encoding (#49570)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [3d13fb3](https://github.com/sgl-project/sglang/commit/3d13fb3848255db8f4c87a1e4279575a81ad2374)

- **作者**: syang-genai
- **时间**: 2026-11-11T08:54:26Z
- **提交信息**: [Doc] diffusion: Document IMAGEIO_FFMPEG_EXE for faster MP4 encoding (#48200)

Co-authored-by: syang-genai <syang0827@gmail.com>

### [b917769](https://github.com/sgl-project/sglang/commit/b917769fa7bd93fe76ee0711167b1dfbef8759ab)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T08:54:07Z
- **提交信息**: [Fix] diffusion/flux2: Size edit outputs from an input image that needs no resize (#49447)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [72d9b67](https://github.com/sgl-project/sglang/commit/72d9b6788d5eb3f187ebf183ff7ed5d002700d16)

- **作者**: Zheng Gong
- **时间**: 2026-11-11T08:53:53Z
- **提交信息**: [Fix] [AMD] aiter: Skip the unused decode workspace on the vectorized_5d KV layout (#47911)

Signed-off-by: ZhengGong-amd <zgong@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [affb3eb](https://github.com/sgl-project/sglang/commit/affb3eb5021f18145a5538752321ccbfb4d2630f)

- **作者**: nathanx-modal
- **时间**: 2026-11-11T08:27:44Z
- **提交信息**: [Feat] kimi-k3: add video support via frame sampling (#49458)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8d57126](https://github.com/sgl-project/sglang/commit/8d571268943222fdaf7ac18970f72b745f7d04fb)

- **作者**: Michael
- **时间**: 2026-11-11T08:26:19Z
- **提交信息**: [CI] [AMD] nightly-benchmark: Run InferenceX's AgentX Qwen3.5 MXFP4 MTP curve on MI35x (#49534)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b2568f7](https://github.com/sgl-project/sglang/commit/b2568f706b5caa2daf800355b015b042d8dbb535)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T07:54:58Z
- **提交信息**: [Feat] sgl-router: Add production API compatibility (#49727)

### [b95f22f](https://github.com/sgl-project/sglang/commit/b95f22fcc513ee5f202f07ca615a996568947934)

- **作者**: WenhaoZhang
- **时间**: 2026-11-11T07:41:32Z
- **提交信息**: [CI] diffusion: refresh 5090 host-anon baselines for two cases (#49718)

### [5fbfcc7](https://github.com/sgl-project/sglang/commit/5fbfcc7170235064125d23feac4b64e5dbe41414)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T07:17:07Z
- **提交信息**: [Fix] tokenizer_manager: Reject logprob_start_len below -1 with a 400 (#49758)

### [e0e4d2b](https://github.com/sgl-project/sglang/commit/e0e4d2bffcf3863787f5058a3d6adfcf8aa25e1c)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T07:16:44Z
- **提交信息**: [Fix] server_args: Reject --scheduler-recv-interval above 1 with pipeline parallelism (#49756)

### [c2ca326](https://github.com/sgl-project/sglang/commit/c2ca326d8c5b762929e3a1968bf5cd78cdb4231b)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T07:16:12Z
- **提交信息**: [Chore] sgl-router: Remove a local design-doc path from the crate docs (#49755)

### [8bbea70](https://github.com/sgl-project/sglang/commit/8bbea70985b6677ad68f4f955be5c8919f4e2f3a)

- **作者**: wl55721
- **时间**: 2026-11-11T07:06:48Z
- **提交信息**: [Feat] [NPU] startup-weight-load: Support overlap mode on NPU (#40141)

### [38bdb79](https://github.com/sgl-project/sglang/commit/38bdb79bafa996fa691eab39a5d93081a351345a)

- **作者**: wl55721
- **时间**: 2026-11-11T07:05:47Z
- **提交信息**: [Feat] [NPU] weight-cache: Add NPU weight cache support (#41495)

### [eef6d87](https://github.com/sgl-project/sglang/commit/eef6d87111ca94083f2840821de02d037463c174)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T06:23:31Z
- **提交信息**: [Refactor] scheduler: Edit request lists only through move and the retirer (#49677)

### [f138b2d](https://github.com/sgl-project/sglang/commit/f138b2d2efc536d0c14892f7c95c197032a575e4)

- **作者**: mustafa-khalid
- **时间**: 2026-11-11T06:14:52Z
- **提交信息**: [Feat] [AMD] tokenizer: Install fastokens in the ROCm image (#47923)

Co-authored-by: mkhalidm <mustafa.khalid@silo.ao>
Co-authored-by: Pedram Ghazi <183694844+amd-pedghazi@users.noreply.github.com>

### [baadc31](https://github.com/sgl-project/sglang/commit/baadc3120b69288d5bef42564013bd17c9844711)

- **作者**: kk
- **时间**: 2026-11-11T06:13:02Z
- **提交信息**: [Fix] [AMD] monokernels: Pin sgl-amd-mono at 7113024f for DSpark on current SGLang (#49428)

Co-authored-by: wunhuang <wunhuang@amd.com>

### [8703b47](https://github.com/sgl-project/sglang/commit/8703b47e0a23a799c9493f2620eb04620c96e1a0)

- **作者**: Serge Panev
- **时间**: 2026-11-11T06:01:20Z
- **提交信息**: [Fix] logprobs: Bound top_logprobs to [0,vocab_size] (#49414)

Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [45ae922](https://github.com/sgl-project/sglang/commit/45ae92278f4c5345af31d0d4e44fc2dc22ee60f3)

- **作者**: Archer
- **时间**: 2026-11-11T06:00:23Z
- **提交信息**: [Fix] offload: Keep DSA indexer parameters resident on GPU under CPU offload (#48316)

Signed-off-by: Archer <42709353+hsthanb4@users.noreply.github.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c8c0941](https://github.com/sgl-project/sglang/commit/c8c0941f548c62f24e14dca22816db6b27c73341)

- **作者**: Brandon Zhang
- **时间**: 2026-11-11T05:59:38Z
- **提交信息**: [Perf] [NVIDIA] flashinfer: Pass uniform_q_len to the target-verify plan for EAGLE speculative decoding (#44115)

Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [5ff617c](https://github.com/sgl-project/sglang/commit/5ff617c12bf17dd4ccf9c8398a76e8a222f857a5)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T05:58:18Z
- **提交信息**: [Fix] scheduler: Apply pending chunked-prefill aborts in the PP PD prefill loop (#49722)

### [adea078](https://github.com/sgl-project/sglang/commit/adea078db2f35200b5a31f5266387e0201c11cc9)

- **作者**: Michael
- **时间**: 2026-11-11T05:46:30Z
- **提交信息**: [CI] [AMD] nightly: Drop models older than the latest two generations (#49620)

### [936d12c](https://github.com/sgl-project/sglang/commit/936d12c3cf9183d07d6bbcc5b8236c5015fba181)

- **作者**: esarafian
- **时间**: 2026-11-11T05:35:41Z
- **提交信息**: [Fix] multimodal: keep placeholder token ids at multimodal positions of input_ids (#48385)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yangmin Li <yangminl@nvidia.com>

### [1ef2446](https://github.com/sgl-project/sglang/commit/1ef2446c51ff3f657db74e9db8d86c0927dece2b)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T05:01:25Z
- **提交信息**: [Doc] cookbook: Drop the PP chunk sizing flags from the Kimi-K3.1-Pro prefill cells (#49716)

### [6685123](https://github.com/sgl-project/sglang/commit/6685123903c97d52a5c014598031ac0577a376ea)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-11-11T04:53:40Z
- **提交信息**: [Perf] kimi-k3.1: Per-M decode GEMM tactics and side-stream attention GEMMs (#49478)

Co-authored-by: Ziyi Xu <76582120+DarkSharpness@users.noreply.github.com>
Co-authored-by: Yuhao Yang <47235274+yhyang201@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [3ff87c5](https://github.com/sgl-project/sglang/commit/3ff87c57f5bc3ef79f980dd6aa6414bc71bed60d)

- **作者**: Mahesh Bapatu
- **时间**: 2026-11-11T04:43:04Z
- **提交信息**: [Feat] kv-events: Report caller multimodal routing labels as block spans (#45737)

Signed-off-by: maheshrbapatu <maheshbapatu@gmail.com>
Signed-off-by: maheshrbapatu <mbapatu@nvidia.com>
Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: maheshrbapatu <mbapatu@nvidia.com>

### [72f72cc](https://github.com/sgl-project/sglang/commit/72f72ccacb3a73fcd99d401e25ca986bda6144c8)

- **作者**: Yanbin Jiang
- **时间**: 2026-11-11T04:17:13Z
- **提交信息**: [Fix] kernels: Synchronize AOT MoE prefix before expert lookup (#49656)

### [b4f7530](https://github.com/sgl-project/sglang/commit/b4f7530440552a1b2bf2a2ed7d798f7a04fa8277)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T04:07:43Z
- **提交信息**: [Feat] multimodal: Decode HEIF images and read relative BMP, TIFF and HEIF paths (#49673)

### [5b8a907](https://github.com/sgl-project/sglang/commit/5b8a907869b675816566de427de6c0b8509c5ec6)

- **作者**: Theresa Shan
- **时间**: 2026-11-11T03:40:55Z
- **提交信息**: [Fix] [AMD] disaggregation: Pair MoRI DSA state across PP prefill stages (#48382)

Co-authored-by: billishyahao <bill.he@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [43d0ecf](https://github.com/sgl-project/sglang/commit/43d0ecf9e1b32faceb1522e7c8cec681564e1355)

- **作者**: Rumit Desai
- **时间**: 2026-11-11T03:20:21Z
- **提交信息**: [Refactor] graph: Introduce device-neutral graph backend bases (1/3) (#49402)

### [9e2d3df](https://github.com/sgl-project/sglang/commit/9e2d3dfb1bf049642815ec54aa6fd3e6008c04c0)

- **作者**: Mick
- **时间**: 2026-11-11T03:18:55Z
- **提交信息**: [CI] diffusion: Bound async video lifecycle polling (#49652)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [6548b53](https://github.com/sgl-project/sglang/commit/6548b5311b308efbe883866887801667a5d84bed)

- **作者**: Michael
- **时间**: 2026-11-11T03:05:49Z
- **提交信息**: [CI] [AMD] nightly: Drop the MiniCPM 2.6 models from the VLM MMMU test (#49615)

### [62eab14](https://github.com/sgl-project/sglang/commit/62eab14422549a4634cb3772fe799c98692da18b)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-11T02:58:41Z
- **提交信息**: [Chore] sgl-kernel: Stop bundling triton_kernels in the sglang-kernel wheel (#49662)

### [ed15b28](https://github.com/sgl-project/sglang/commit/ed15b28dccb05e4af5429fc0cc96df6fbd4f24de)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-11T02:55:37Z
- **提交信息**: [Refactor] mxfp4: Dequantize MXFP4 MoE weights with a JIT kernel instead of triton_kernels (#49661)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [10163c2](https://github.com/sgl-project/sglang/commit/10163c2811d7de3e27f2e7498b047d971449a92d)

- **作者**: Shangming Cai
- **时间**: 2026-11-11T02:54:37Z
- **提交信息**: [Fix] constrained: Reject a token in llguidance without poisoning the matcher (#49655)

Co-authored-by: paoloap <58889145+paoloap-py@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [49f1a44](https://github.com/sgl-project/sglang/commit/49f1a44ee348373d29c9292ea36cd45f054ba18a)

- **作者**: Jaeyeon Kim(김재연)
- **时间**: 2026-11-11T02:19:40Z
- **提交信息**: [Refactor] hisparse: unify device-pool mapping and selection (#30893)

Signed-off-by: Jaeyeon Kim <anencore94@gmail.com>
Co-authored-by: Zhiqiang Xie <xiezhq@stanford.edu>

### [a93e89f](https://github.com/sgl-project/sglang/commit/a93e89fd4a4eefb52c3ce73a609317d716d2a6ab)

- **作者**: Benjamin Truong
- **时间**: 2026-11-11T01:27:42Z
- **提交信息**: [Feat] [NVIDIA] flash-attn: FA4 SM90 FP8 e4m3 KV cache for head_dim 256 and 512 (Gemma-4) (#46965)

### [2dcc93b](https://github.com/sgl-project/sglang/commit/2dcc93b624056817f39bc639ab5f2f6ed1c76c36)

- **作者**: 渺如星辰
- **时间**: 2026-11-11T01:16:57Z
- **提交信息**: [Fix] moe: Validate the scale grid and use logical K for even_Ks in the GPTQ/AWQ Triton MoE kernel (#49337)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: hn1209 <44727020+hn1209@users.noreply.github.com>
Co-authored-by: scdotbox <128663994+scdotbox@users.noreply.github.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [e11c958](https://github.com/sgl-project/sglang/commit/e11c9583e68eac806b6a9fa1057023c72ac184c3)

- **作者**: Qiaolin Yu
- **时间**: 2026-11-11T01:15:26Z
- **提交信息**: [Feat] spec: Online acceptance estimator for DSpark confidence-scheduled verification (#44588)

Co-authored-by: Jian Chen <141193260+jianc99@users.noreply.github.com>
Co-authored-by: maocheng23 <35615230+maocheng23@users.noreply.github.com>

### [df4ec2e](https://github.com/sgl-project/sglang/commit/df4ec2e074b308bf8c47b8e2f1a32d0bd49776aa)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-11T01:14:07Z
- **提交信息**: [Refactor] moe: Remove the triton_kernel MoE runner backend (#49660)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2f209ae](https://github.com/sgl-project/sglang/commit/2f209ae03427ea1531bfe59d60087954435748f9)

- **作者**: Ziyi Xu
- **时间**: 2026-11-11T01:00:47Z
- **提交信息**: [Refactor] custom-ar-v2: Single-word push epoch and consume-style pull semaphores (#49365)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [505120f](https://github.com/sgl-project/sglang/commit/505120f0c3026b198ee0dd81a486389a9f82ce27)

- **作者**: ChengYao-amd
- **时间**: 2026-11-11T00:58:23Z
- **提交信息**: [Fix] [AMD] moe: Stop dropping FP32 partials in GLM Gluon TP8 32K MoE (#48397)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [edf98a4](https://github.com/sgl-project/sglang/commit/edf98a427d179a2137d3aeb1b63f5383d4ffd45f)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T00:58:02Z
- **提交信息**: [Perf] diffusion: Apply the Qwen3 text encoder's RoPE with one FlashInfer kernel (#49448)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [7bd4130](https://github.com/sgl-project/sglang/commit/7bd4130168397daa967ff81e46a642d12d3c4bac)

- **作者**: leon
- **时间**: 2026-11-11T00:57:47Z
- **提交信息**: [Doc] GLM-5.3-Flash: Add B300 TP4 AgentX tuning results (#49071)

### [14aa18a](https://github.com/sgl-project/sglang/commit/14aa18aa516694451f96477aab841c93702c0051)

- **作者**: Haishuo.Kong
- **时间**: 2026-11-11T00:57:24Z
- **提交信息**: [Fix] [AMD] mxfp4: Keep MoE weight layout and dispatch consistent with the selected runner (#48810)

Signed-off-by: Haishuo.Kong <haiskong@amd.com>

### [6bf4635](https://github.com/sgl-project/sglang/commit/6bf4635036a92b414aad3261625b6395d9f5f610)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T00:57:11Z
- **提交信息**: [Fix] compressed-tensors: Size the FP8 MoE w13 by the layer's gating (#49357)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [d89680b](https://github.com/sgl-project/sglang/commit/d89680b2679d13b75747c3b86f2864a2f66d94cd)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T00:56:58Z
- **提交信息**: [Fix] diffusion: Compute CFG normalization over the whole latent under sequence parallelism (Z-Image) (#49279)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [f12fb5f](https://github.com/sgl-project/sglang/commit/f12fb5fc74260c8639a160161fcc7210caa1595e)

- **作者**: Han-Yin Chang
- **时间**: 2026-11-11T00:56:45Z
- **提交信息**: [Fix] diffusion/qwen-image-edit: Run n > 1 edit outputs one by one (#49442)

Signed-off-by: Han-Yin Chang <nick20350@gmail.com>

### [0f5a47d](https://github.com/sgl-project/sglang/commit/0f5a47de2af17705f4b42df0f73872eae5dd2eb5)

- **作者**: Ziyi Xu
- **时间**: 2026-11-11T00:56:32Z
- **提交信息**: [Refactor] moe: Remove the SM120 top-22 small-M router path (#49538)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d279271](https://github.com/sgl-project/sglang/commit/d279271a57f83c0c7508d3482468baaaa839003f)

- **作者**: Ziyi Xu
- **时间**: 2026-11-11T00:56:13Z
- **提交信息**: [Doc] skills: One implementation per kernel contract, plus JIT kernel style rules (#49568)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1c70246](https://github.com/sgl-project/sglang/commit/1c70246e087c5e19e0bffe1f8e704783bdca640a)

- **作者**: jiaryang
- **时间**: 2026-11-11T00:54:56Z
- **提交信息**: [Perf] [AMD] attention: Use aiter's Triton MLA decode in the aiter backend on gfx1250 (#44458)

### [21adb48](https://github.com/sgl-project/sglang/commit/21adb48ae089b9ea7b43d66088bfe0c3aadac97d)

- **作者**: weireweire
- **时间**: 2026-11-11T00:50:21Z
- **提交信息**: [Perf] distributed: Keep the multimem logits all-gather on a multi-node NVLink clique (#49524)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [1cfc812](https://github.com/sgl-project/sglang/commit/1cfc8128d226c8f2b16d589313d791193b36b917)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-11T00:46:02Z
- **提交信息**: [Fix] sgl-router: pass a streaming prefill's in-band 4xx through to the client (#49622)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ddd9cc9](https://github.com/sgl-project/sglang/commit/ddd9cc925fabecd8a09f6995d3533739d67abd76)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-11T00:33:50Z
- **提交信息**: [Fix] multimodal: Fail bad client media with a client error (#48778)

### [34132db](https://github.com/sgl-project/sglang/commit/34132db51c97cc873b608d06e347b97b1d8229ad)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-11-11T00:33:05Z
- **提交信息**: [Perf] kda-replayssm: Reuse the verify-fused commit step indices (#44396)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>
Co-authored-by: Liangsheng Yin <hnyls2002@gmail.com>

### [57f688f](https://github.com/sgl-project/sglang/commit/57f688f507e550fd1bd275fa8b95dda0e763c13c)

- **作者**: Kangyan-Zhou
- **时间**: 2026-11-11T00:25:00Z
- **提交信息**: [Fix] http_server: Exit when a scheduler dies with multiple tokenizer workers (#49397)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [22e3f47](https://github.com/sgl-project/sglang/commit/22e3f4722ff1279727f25c7227542edfa73c2084)

- **作者**: zijiexia
- **时间**: 2026-11-11T00:22:40Z
- **提交信息**: [CI] [NVIDIA] docker: Publish the CUDA 13.4 nightly image for x86_64 as well as aarch64 (#47999)

### [314bce7](https://github.com/sgl-project/sglang/commit/314bce7cfcc743b15bd8d670c4affef021d8b23c)

- **作者**: Lee Nau
- **时间**: 2026-11-11T00:14:46Z
- **提交信息**: [Fix] watchdog: Let py-spy attach to watched processes in CI (#48938)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Sundara Raman Ramachandran <sundar24295@gmail.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1303
- **最后更新**: 2026-11-12T02:50:13Z

## 提交统计

- **昨日提交总数**: 14
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

## 1. 主要更新类型

本次提交涵盖四类核心工作：**大规模模块重构**（重命名去下划线前缀、包结构重组）、**性能优化**（SVDQuant 调度与 GEMM 内核、Qwen-Image 2.1 融合算子）、**测试修复**（fp8 cudagraph 后端分发匹配）以及**文档更新**（模型集成运行手册、量化相关文档同步）。

## 2. 关键变更点及与项目方向的关系

**命名规范化与包结构重组（#1291-#1294）**：将 `src/cache_dit` 下所有以 `_` 开头的模块/包重命名，如 `_utils` → `cli`、`_scaled_mm` → `scaled_mm`、分布式 `core/` 拆分为 `communicate/` 与 `parallel/`、CUDA 扩展四合一为 `_C_ops`。这与 cache-dit 作为 PyTorch 原生推理引擎的工程化目标一致——消除"私有前缀"误导，让包布局直接表达职责，为后续功能扩展和外部贡献降低认知成本。

**性能优化（#1274-#1285）**：Qwen-Image 2.1 融合四个 CUDA 算子（qk-norm+RoPE、LayerNorm+modulation、gated residual、SwiGLU gate），单 GPU eager 下 -11.8% 延迟；SVDQuant 跳过无用 dense 输出省 96 MiB 内核缓冲、LoRA 调度调优、CuTe FP4 mainloop 索引简化。这些直接服务于项目"Cache + Parallelism + Quantization + CPU Offload"的核心卖点。

**测试修复（#1289）**：fp8 cudagraph 测试因 torchao AUTO 后端在 sm120 上误派发 mslk kernel 而失败，通过固定 `KernelPreference.TORCH` 修复，确保测试覆盖 cache-dit 自身配置的代码路径。

## 3. 对项目的影响与潜在意义

- **API 破坏性变更**：per-family CUDA 可用性 getter 移除、模块路径变更意味着所有下游 import 需同步更新，但这是为长期可维护性付出的一次性成本。
- **性能基准可复现**：每次重构均以 FLUX.1-dev 1024×1024 位一致输出验证，确保重构零行为变化，为后续功能迭代建立可靠基线。
- **Qwen-Image 2.1 成为第三个融合模型模板**：配合 #1281 的 `_NAME` second-pass 运行手册，形成了"保留 diffusers 模块 + 优化 pass + 融合算子"的可复制模式，加速后续模型适配。

## 4. 值得关注的技术点

- **块级 patch functor 陷阱**：`block._idx` 导致 recompile_limit 在 block 9 触发并静默回退 eager（420→372 ms/step），是 PyTorch compile 的隐蔽坑。
- **Welford 递倒数 + `__frcp_rn`**、modulation 折叠为 per-sample (R,D) 行、16 bytes/lane 访问模式：体现内核级内存布局优化。
- **模块级 `_qwenimage21_prepare_qkv` 插桩点**：融合可与 CP/flex attention/TP 组合，CP2 输出与单卡位一致，展示 seam 选择的重要性。
- **`write_dense` 开关设计**：通过 out-absent 分支复用既有内核路径，避免新增 kernel 分支，设计克制。

## 5. 对项目发展的整体影响

cache-dit 正处于**从功能可用向工程成熟过渡**的阶段。本批提交体现了三条发展主线：(1) 通过系统性重构清理历史包袱，为社区贡献和模块化扩展铺路；(2) 持续压榨量化推理性能，SVDQuant 与融合算子使 cache-dit 在 DiT 推理上与原生 diffusers 拉开可量化差距；(3) 通过运行手册与测试纪律建立"可复制的模型适配流程"，将单点优化经验转化为组织能力。这些工作共同支撑项目作为 PyTorch 原生 DiT 推理引擎的定位，为其在生产环境中的采用奠定基础。

## 详细提交记录

### [1c3ce5c](https://github.com/vipshop/cache-dit/commit/1c3ce5c9c04e6a1b5cd365fa27cd8c7e82c54d55)

- **作者**: DefTruth
- **时间**: 2026-11-11T13:07:29Z
- **提交信息**: docs(quantization): name the torch operator explicitly after the scaled_mm rename (#1294)

Now that the module is `quantization/torchao/scaled_mm.py`, a bare
`_scaled_mm` in prose is ambiguous: it either means torch's `_scaled_mm`
operator or our wrapper module. Spell out `torch._scaled_mm` wherever the
operator is meant.

- quantization/torchao/scaled_mm.py module docstring + lowering comments
- quantize_ao.py scale-clamp docstring, and the skip / fallback reasons now
  read "torch._scaled_mm: DTensor + bias NOT supported"
- quantization/config.py comment on float8 per-row memory layout
- tests/kernels/{test_rowwise_cudagraph_partition,test_opaque_scaled_mm}.py
- .agents/skills/cache-dit-model-integration/references/modular_pipeline.md

Left untouched on purpose: the `AssertionError("_scaled_mm on DTensors
doesn't support bias")` quote in quantize_ao.py, which reproduces torch's own
message verbatim.

### [c625fdd](https://github.com/vipshop/cache-dit/commit/c625fdd262c39754a14ba2e773d95e389746e6c0)

- **作者**: DefTruth
- **时间**: 2026-11-11T13:02:28Z
- **提交信息**: refactor: drop the last leading underscores from module file names (#1293)

Completes the module naming cleanup started in #1291 / #1292: the two
remaining `_name.py` modules are renamed, so no tracked feature module in
src/cache_dit carries a private-looking prefix (only `__init__.py` does).

- quantization/torchao/_scaled_mm.py -> quantization/torchao/scaled_mm.py
- ray/_tree.py                       -> ray/tree.py

Only import paths change: quantization/torchao/__init__.py, the lazy import
in cli/utils.py, ray/engine.py + ray/worker.py, two kernel tests, and the
CUDA-graph / quantization / modular-pipeline docs. `torch._scaled_mm` (the
torch operator) is of course untouched.

Import checks: `cache_dit.quantization.torchao.scaled_mm`,
`from cache_dit.quantization.torchao import enable_opaque_torchao_float8_scaled_mm`,
`cache_dit.ray.{tree,engine,worker}` and `python -m cache_dit.generate list`
all import cleanly; compileall over both packages is clean; repo-wide grep for
the old module paths returns nothing.

### [8618225](https://github.com/vipshop/cache-dit/commit/8618225edb416d3569070aa5ab31dc09937b7707)

- **作者**: DefTruth
- **时间**: 2026-11-11T12:56:31Z
- **提交信息**: refactor: drop leading underscores from module and package names (#1292)

* refactor(attention): drop leading underscores in module file names

The attention package now uses the same file naming as the rest of the
codebase (no private-looking `_name.py`), matching autoencoders/ and
transformers/.

- _interface.py        -> interface.py
- _backend_selector.py -> backend_selector.py
- _diffusers_bridge.py -> diffusers_bridge.py

Only import paths change: attention/__init__.py and
tests/parallelism/test_attention_dispatch.py. No behaviour change.

* refactor(kernels): drop leading underscores from module and package names

Same naming rule as the attention package and cli: no private-looking
`_name.py` under src/cache_dit. Class-level `_{NAME}` naming is untouched —
that convention still marks "subclass of diffusers' `NAME`".

- _attn.py    -> attn.py       (_comm.py -> comm.py, _cuda_ext.py -> cuda_ext.py)
- _svdquant.py -> svdquant.py
- _flashinfer/ -> flashinfer/  (_flashinfer/_svdquant.py -> flashinfer/svdquant.py)
- _models/     -> models/      (_models/_boogu.py -> models/boogu.py,
                                _models/_qwen_image21.py -> models/qwen_image21.py)
- models/pipelines/_qwen_image21/ -> models/pipelines/qwen_image21/

Call sites updated in src (kernels/__init__.py, kernels submodule imports,
boogu_image and qwen_image21 fused_ops, quantization/svdquant/fused.py,
caching/block_adapters, cli/examples, the qwen_image21 CP planner), in tests
(kernels + api), and in the custom-kernel / model-integration skills.

test_ops_dispatch::test_public_api_matches_all now ignores module objects:
the renamed submodules are public package attributes but not part of the
operator API surface.

Verification: kernels 248 passed (the single cudagraph_partition failure also
fails on unmodified main), parallelism 175 passed (same pre-existing wan_s2v
ordering failure), tests/api failure set identical to the pre-refactor
baseline, and FLUX.1-dev 1024x1024 seed 0 is bit-identical to the baseline
(PSNR inf, SSIM 1.0).

* docs(skills): align module paths with the new underscore-free naming

Follow-up to the attention / kernels / qwen_image21 renames: the model
integration and custom-kernel skills still described the old layout.

- custom_models model-integration worked example (§15, `_QwenImage21`):
  package layout `pipelines/_<model>/` -> `pipelines/<model>/`, kernel bridge
  `kernels/models/_<model>.py` -> `kernels/models/<model>.py`, and the
  `from .._cuda_ext import` snippet now uses `..cuda_ext`. Class prefixes
  `_<Model>...` are unchanged (they mark "subclass of diffusers `<Model>`").
- custom-kernel skill: `kernels/_init__.py` -> `kernels/__init__.py`,
  `kernels/models/_<model>.py` -> `kernels/models/<model>.py` (`boogu.py`),
  `from ._cuda_ext` -> `from .cuda_ext`, `from ._comm` -> `from .comm`, and
  the `__all__` rule now says submodules (`attn`/`comm`/`cuda_ext`/`models`/
  `svdquant`) are package attributes but stay out of `__all__`.

Every `src/cache_dit/...` path referenced by the skills is validated to exist;
the only remaining non-path token is the intentional `functor_my_model.py`
template. The quantization skill needed no change (it already points at
`src/cache_dit/cli/utils.py`; its `_svdq_test_utils.py` entries are test
helpers and keep their names).

### [53f8618](https://github.com/vipshop/cache-dit/commit/53f8618353435b140bee35957ee5111285e4db36)

- **作者**: DefTruth
- **时间**: 2026-11-11T12:35:36Z
- **提交信息**: refactor(cli): rename the _utils package to cli (#1291)

The package under src/cache_dit/_utils is the command-line surface of
cache-dit: argument parsing (utils.py), example factories (examples.py),
example registration (registers.py) and the entrypoint (generate.py). Calling
it `_utils` hides that role behind a generic private name, so rename it to
`cli` to match the rest of the package layout.

- src/cache_dit/_utils/ -> src/cache_dit/cli/ (file names unchanged)
- src/cache_dit/generate.py imports the entrypoint from .cli
- 26 test modules switch from cache_dit._utils.* to cache_dit.cli.*
- docs and skills updated: docs/EXAMPLES.md, docs/developer_guide/
  SUPPORT_NEW_MODEL.md, examples/README.md and 10 skill files. The two
  EXAMPLES/README links pointed at src/_utils/examples.py, which was already
  the wrong path (missing the cache_dit segment); they now point at
  src/cache_dit/cli/examples.py.

No behaviour change: `python -m cache_dit.generate list`, an FLUX.1-dev
1024x1024 run and `cache-dit-metrics` all work, and the generated image is
bit-identical (PSNR inf, SSIM 1.0) to the pre-rename baseline. tests/api +
tests/utils show no new failures (only the pre-existing ffpa / load_configs
ones, ffpa-attn is not built in this env).

### [5a428b6](https://github.com/vipshop/cache-dit/commit/5a428b664eb875750d0886e3142930519badcd74)

- **作者**: DefTruth
- **时间**: 2026-11-11T12:34:42Z
- **提交信息**: refactor(distributed): split core into communicate/parallel and nest async_ulysses (#1290)

Restructure src/cache_dit/distributed so the package layout states what each
module does, with no runtime behaviour change.

- Move distributed/async_ulysses/ to distributed/transformers/async_ulysses/:
  async Ulysses patches only ever target transformers, so it now lives under
  the transformer package. The directory, file names and the __package__ based
  _safe_import anchors of the registry are kept as-is; relative imports gain
  one dot of depth.
- Split distributed/core/ by responsibility, then delete it (no compat shim):
  - communicate/primitives.py: all-to-all / Ring p2p collectives, head
    pad-unpad helpers, comm metadata, fp8 comm kernel bindings.
  - parallel/{config,hooks,context_parallel,runtime,diffusers_bridge}.py:
    CP config/plan types, hook registry, CP hook runtime, enablement entry and
    diffusers bridging.
  - parallel/{ulysses,ring,usp}.py: the templated CP attention implementations.
- Expose stable per-package API surfaces so call sites import from
  distributed.parallel or distributed.communicate by symbol ownership; file
  names drop the leading underscore to match autoencoders/ and transformers/.
- Rewire every call site: 78 source files, 10 test modules and 3 skill
  documents. The lazy diffusers_bridge -> attention import is preserved so no
  new top-level import cycle is introduced.

Verification: planner registry identical to main (cp 56 / tp 60); tests/api
failure set identical to main; FLUX.1-dev 1024x1024 28 steps seed 0 gives
PSNR=inf / SSIM=1.0 against the pre-refactor baseline, and CP2 ulysses, CP2
ring, TP2 and USP4 (ring2 x ulysses2) all reproduce the baseline image.

### [6fdca9b](https://github.com/vipshop/cache-dit/commit/6fdca9b29fc68ec97e68176aed1282421299089c)

- **作者**: DefTruth
- **时间**: 2026-11-11T11:10:25Z
- **提交信息**: test(kernels): pin the torch `_scaled_mm` path for the fp8 cudagraph tests (#1289)

The three failures tracked in #1286 were a backend dispatch mismatch: `Float8Tensor.from_hp()` defaults to `KernelPreference.AUTO`, torchao's AUTO picks mslk on any sm90+, and mslk 1.4.0 ships only Sm90/Sm100 fp8 rowwise kernels -- on sm120 `getDeviceArch()` returns 12, so an Sm90 kernel is dispatched and aborts with `RuntimeError: cutlass cannot initialize`.

Pin `KernelPreference.TORCH` in both repros, which is the path Cache-DiT itself configures for float8_per_row (`quantize_ao.py`) and the one `enable_opaque_torchao_float8_scaled_mm()` patches, so the tests now exercise the code they were written for instead of being short-circuited into mslk.

The raw hang repro is skipped: with the torch path the hang no longer reproduces on torch 2.15 / torchao 0.18, and on sm12x the mslk path aborts before it can, so the premise is unobservable here. The tagged-wrapper case stays as the regression guard.

`tests/kernels`: 249 passed, 1 skipped (was 247 passed, 3 failed).

Fixes #1286

### [768e2f1](https://github.com/vipshop/cache-dit/commit/768e2f1a0a538ce496f5b7e362a14cc7f932f277)

- **作者**: DefTruth
- **时间**: 2026-11-11T10:42:41Z
- **提交信息**: refactor(kernels): merge the four CUDA extensions into one `_C_ops` module (#1288)

The four optional extensions (`_C_svdquant` / `_C_comm` / `_C_attn` / `_C_models`) each carried their own `PYBIND11_MODULE`, source manifest, `-gencode` set, `depends=` list and Python loader. They now link into one `cache_dit._C_ops` module.

- C++: `csrc/kernels/ops.cpp` is the only `PYBIND11_MODULE`; each family exports `register_<family>_ops`. File names are uniform (`<family>/<family>.h` + `<family>/<family>.cpp`), the SVDQ dispatchers moved from the header into `svdq.cpp`, and `svdq::ops` became `cache_dit::svdq`.
- Build: one source list (25 TUs), one `depends=` over `csrc/kernels/**`, one flag set, one arch predicate (`>=sm89`, excluding `sm90`); the default arch set narrowed to `("89", "120a")`.
- Python: `kernels/_cuda_ext.py` is the only loader, with `cuda_ext_is_available()` as the only availability API; the eight per-family getters (including the `cache_dit.quantization` re-exports) are removed.
- Docs/tooling: INSTALL, QUANTIZATION, the wheel inspector and four skills follow the single-extension layout.

Breaking: Hopper gets no CUDA operators, `sm100` is out of the default arch set (pass `CACHE_DIT_CUDA_ARCH_LIST` to add it), and the per-family availability getters are gone.

Closes #1287

### [db12521](https://github.com/vipshop/cache-dit/commit/db1252156073897bc773389e78a75c397c4ebd4a)

- **作者**: DefTruth
- **时间**: 2026-11-11T08:08:12Z
- **提交信息**: perf(svdq): tune row-major LoRA schedule and document limits (#1285)

Select main-first only for 16K rows and wide 8K row-major tiles, keep LoRA-first elsewhere, and record the remaining producer and GEMM profiling priorities.

### [3439fb1](https://github.com/vipshop/cache-dit/commit/3439fb11fe8c8bbb24275a25e315d34f42f2f4dd)

- **作者**: DefTruth
- **时间**: 2026-11-11T06:17:45Z
- **提交信息**: perf(svdq): simplify CuTe FP4 mainloop indexing (#1284)

Use the K-tile index as the consumer loop induction variable while preserving ring stage and phase order. This removes loop-metadata spills from LoRA-first instances and fixes stale stage documentation.

### [d2ee88e](https://github.com/vipshop/cache-dit/commit/d2ee88e8fdbb3fefa6b22e946ebd7a6a1188fedb)

- **作者**: DefTruth
- **时间**: 2026-11-11T04:48:04Z
- **提交信息**: docs(model-integration): `_NAME` second-pass runbook for diffusers models (#1281)

`custom_models.md` documented two shapes: the model is absent from diffusers (vendor / depend), or cache-dit absorbs it. The `_QwenImage21` work added a third, cheaper one: keep diffusers' implementation and ship an optimized pass over it as a `_<Model>Pipeline` subclass with fused operators.

- §1.3 records the entry-point decision (seams only -> subclass; attention math / block loop / tensor layout / checkpoint keys -> absorb)
- §15 is the runbook, worked on `_QwenImage21`: package layout, `from_pretrained` in-place class swap, the `_NAME` registry checklist with a symptom per missing entry, seam selection (module-level QKV helper composes with CP / flex / TP; a processor subclass does not), the fast-math numerical contract, "fold per-sample constants before writing kernels", the two compile checks (per-block constants out of the graph; inductor already fuses most pointwise chains), the acceptance protocol, the measured matrix, and a trap table
- `SKILL.md` routes to it as route 3 and updates the routing table, reference table, phase-0 checklist and GATE CHECK scope

### [2847645](https://github.com/vipshop/cache-dit/commit/284764587609e08e7962a298bdf28659073eb60a)

- **作者**: DefTruth
- **时间**: 2026-11-11T04:36:32Z
- **提交信息**: perf(qwen21): fused CUDA ops for Qwen-Image 2.1 (#1274)

Second-pass pipeline for Qwen-Image 2.1: `_QwenImage21Pipeline` keeps diffusers' modules and state dict and rebinds the block / SwiGLU / attention-QKV seams around four fused CUDA operators in `cache_dit._C_models`.

- fix the patch functor tracing `block._idx`: one graph per block tripped `recompile_limit` at block 9 and silently fell back to eager (420.6 -> 372.8 ms/step with cache + compile)
- operators: qk-norm+RoPE, LayerNorm+modulation, gated residual, SwiGLU gate; 16 bytes per lane on every access, modulation folded into per-sample (R, D) rows, Welford reciprocals precomputed with `__frcp_rn`
- fusion is installed on the module-level `_qwenimage21_prepare_qkv`, so it composes with context parallelism, flex attention and tensor parallelism (CP2 output is bit-identical to single-GPU)
- measured (1024^2, 40 steps, no DBCache): single GPU eager 403.0 -> 355.3 ms/step (-11.8%), single GPU compile 361.3 -> 352.5 (-2.4%), CP2 eager 256.8 -> 238.0 (-7.3%), CP2+compile 223.8 -> 222.5; operator deviation 43.74 dB PSNR / 0.9920 SSIM vs stock+compile, same magnitude as compile's own drift

### [ad12f1e](https://github.com/vipshop/cache-dit/commit/ad12f1e8714c3fe2269d08d4ac168ea6885252a8)

- **作者**: DefTruth
- **时间**: 2026-11-11T02:40:40Z
- **提交信息**: refactor(svdq): shorten svdq_extension_is_available to svdq_is_available (#1280)

### [ef008ba](https://github.com/vipshop/cache-dit/commit/ef008baa0447f8e5b9e5b53a5bb84f49102bc89b)

- **作者**: DefTruth
- **时间**: 2026-11-11T02:21:02Z
- **提交信息**: bench(svdq): rename the SVDQuant bench and add a --fused-mlp chain mode (#1278)

Rename bench/kernels/bench_svdquant_kernels.py to bench_svdquant.py and add --fused-mlp, which times the two-layer MLP chain instead of a single GEMM: unfused-mlp (fc2(gelu(fc1(x)))), fused-mlp (fused_gelu_mlp) and fused-mlp+dense (the same pass with the dense store forced back on). In that mode N is fc1's hidden width and the pass is native-runtime only.

Rows also report the peak allocation delta per chain, so the write_dense win from #1276 has a reproducible measurement: on NVFP4 at M=4096/n=12288/k=3072 the fused chain runs 1.25x the unfused one, and the dense store alone is worth 43 us (~4.4%) plus 72 MiB of peak.

Sync the script name in QUANTIZATION.md and the in-repo custom-kernel skill.

### [3eba882](https://github.com/vipshop/cache-dit/commit/3eba8821d8cc53211c107ba59d36e1570e4a6d51)

- **作者**: DefTruth
- **时间**: 2026-11-11T02:04:20Z
- **提交信息**: perf(svdq): skip the discarded dense output in the fused MLP pass (#1276)

fused_gelu_mlp ran EpilogueDefault and stored a full [M, N] fp16 buffer that the pass never reads (96 MiB per FLUX FF call at M=4096/N=12288).

Add a write_dense switch to svdq_gemm_w4a4: False leaves the dense out to the kernel's existing out-absent branch, so only EpilogueQuantize runs and qout/oscales/lora_act_out come out bitwise-identically. The switch requires the native fused qout path plus qout, oscales and smooth_factor (and, on NVFP4, one of the remaining dtype sources), and returns a 0-element placeholder.

fused_gelu_proj keeps the dense output. Adds the first execution coverage for the fused MLP path and guard tests for the rejected combinations.

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 96777
- **最后更新**: 2026-11-12T02:35:14Z

## 提交统计

- **昨日提交总数**: 87
- **提交者数量**: 59
- **主要提交者**: Mikko Tukiainen, mispa-ms, A&W

## AI分析总结

# vLLM 昨日提交分析（共 87 条）

## 1. 主要更新类型
- **Bug 修复占比最高**：约三分之一，覆盖投机解码、池化、KV cache、注意力内核、前端请求校验、Tokenizers 及模型层等。
- **性能优化**：集中在 MoE、量化（FP8/MXFP8/NVFP4）、投机解码、Mamba/DSpark 草稿采样，以及 Blackwell/H20 等硬件调优。
- **功能与模型支持**：Ling VL、Qwen2-MoE、MiniMax、Kimi-K3、DSV4.1、DomynEdge 等新模型与新架构接入。
- **硬件生态**：ROCm、XPU、Rubin CUDA 等各平台专属修复与调优。
- **CI 与文档**：测试分片、不稳定用例跳过、AMD 验证配方及各模型部署指南更新。

## 2. 关键变更及与项目方向的关系
- **投机解码（Spec Decode）是核心主题**：DSpark/DSv4.1 草稿模型、DCP 滑动窗口 MLA、自适应验证、GLM-5.3 FP8 KV cache、跨 TP 的 DSpark 决策同步与 FP32 残差截断修复，直接服务 README 降低延迟与成本的目标。
- **多硬件生态扩张**：ROCm 提交约 15 条（gfx942/gfx1151 attention 后端、AITer GEMM、在线量化），叠加 XPU 与 Rubin VR200/B300 预设，践行"easy serving for everyone"的跨平台承诺。
- **Rust 前端走向成熟**：JSON 日志、统计行、权重版本增量、tool_choice 对齐 Python 语义及基准测试与 Python 结果对齐，正从实验走向与 Python 实现功能对等。
- **Transformers 建模后端完善**：M-RoPE CUDA graph 修复、GLU 融合量化、CPU offload 修复，降低新模型接入门槛。
- **KV 缓存与 PD 分离**：Mooncake TransferEngine 复用、二级 KV 警告，推进 prefill-decode 分离架构成熟。
- **并发正确性**：FlashInfer plan buffer 竞态、SSD prefill 扫描、duplicate resume 集合通信不匹配等修复，针对生产级多卡部署稳定性。

## 3. 对项目的影响与潜在意义
大量竞态与内存访问修复显著提升多卡/流水线并行下的可靠性，减少生产环境崩溃；Blackwell（SM100/110）与 H20 针对性调优保持性能领先。批不变性（batch-invariant）主题在池化、MoE 配置、CI 测试中反复出现，系统性保证输出一致性，对评测与 A/B 对比至关重要。错误信息改进（请求校验行号、未知角色报错）提升排障体验。Recipe 化交付与 CI 分片提速缓解测试膨胀压力，降低部署与维护开销。

## 4. 值得关注的技术点
- **自适应投机解码的分布式一致性**：TP 各 rank 需同步 DSpark 决策，是隐蔽的正确性陷阱。
- **混合精度量化细节**：ModelOpt NVFP4 W4A16 混合精度加载、AutoGPTQ 保留未量化路由专家、流水线边界 FP32 残差截断。
- **Engram 与 DSv4.1 的 128 行查找 tile、GPU 表分引擎拆分**：大规模 KV/检索结构的工程优化。
- **FlashInfer SSD prefill 与 ReplaySSM 种子**：Mamba 类模型状态重放的性能与可复现性权衡。
- **关键帧感知视频采样**：PyNvVideoCodec 后端优化长视频多模态输入效率。
- **AI 辅助开发常态化**：绝大多数提交带 Claude/Copilot/Codex/vllm-agent 共同署名，vLLM 已深度采用 AI agent 参与开发流程。

## 5. 对项目发展的整体影响
vLLM 正处于**广度扩张（多硬件、多模型、Rust 前端）与深度加固（并发正确性、批不变性、量化精度）并重**的阶段。性能调优持续围绕 MoE 与投机解码两大降本杠杆，与"easy, fast, cheap"愿景高度一致；跨厂商贡献者（AMD、NVIDIA、Intel、社区）的活跃参与进一步强化其作为开放标准推理引擎的生态位。总体而言，这些变更将推动 vLLM 在保持性能领先的同时，向生产级可靠性和更广泛的全平台覆盖迈进。

## 详细提交记录

### [3bc0f43](https://github.com/vllm-project/vllm/commit/3bc0f430883c575d4076280d8d10d77cd4bfc07c)

- **作者**: Mai Hoàng Đức
- **时间**: 2026-11-11T23:26:46Z
- **提交信息**: [Bugfix][Pooling] Make MEAN pooling batch invariant when the flag asks for it (#60035)

Signed-off-by: Mazukiri <maihoangduc04@gmail.com>
Co-authored-by: Mazukiri <maihoangduc04@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [2199d6f](https://github.com/vllm-project/vllm/commit/2199d6f4885ee91b9e6319d3dfd04f9bd0e8724a)

- **作者**: Nick Hill
- **时间**: 2026-11-11T23:24:06Z
- **提交信息**: [Bugfix] Size extensible KV cache reserve on the full token budget (#66731)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [73a1377](https://github.com/vllm-project/vllm/commit/73a1377b6bebf27e48d025191cf5e20ea9620a04)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-11T22:59:57Z
- **提交信息**: [Bugfix] Fix FlashInfer plan buffer race causing illegal memory access with PP (#64165)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6dccaff](https://github.com/vllm-project/vllm/commit/6dccafffc056c44f84b971258caa57d9f35a1ddc)

- **作者**: keneoneth
- **时间**: 2026-11-11T22:48:52Z
- **提交信息**: [ROCm] Avoid DSpark placeholder shared vocab allocations (#54820)

Signed-off-by: keneoneth <keneoneth18@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4ad27d8](https://github.com/vllm-project/vllm/commit/4ad27d8a73a7046e83a0801c862e7cd55e29fbcb)

- **作者**: Lucas Wilkinson
- **时间**: 2026-11-11T22:46:20Z
- **提交信息**: [Core][Kimi K3.1] Write draft KV at block-stride slots instead of translating slot mappings (#66604)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [772dafd](https://github.com/vllm-project/vllm/commit/772dafd2958bf0557751539f73e123ec4a015f98)

- **作者**: Rishi Puri
- **时间**: 2026-11-11T22:28:37Z
- **提交信息**: [Quantization] Load ModelOpt NVFP4 W4A16 token embeddings in mixed-precision checkpoints (#64767)

Signed-off-by: Rishi Puri <riship@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [055f8da](https://github.com/vllm-project/vllm/commit/055f8da959117731038a6bfea00055466cd9cf00)

- **作者**: Lucas Wilkinson
- **时间**: 2026-11-11T22:01:27Z
- **提交信息**: [CI/Build][NVIDIA] Move Rubin nightly images to CUDA 13.5 (#65765)

Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shang Wang <samshang.wang@mail.utoronto.ca>

### [24a6e0f](https://github.com/vllm-project/vllm/commit/24a6e0fe58850f2e9f57c97ff9707c2d83e1ab20)

- **作者**: Thien Tran
- **时间**: 2026-11-11T21:54:02Z
- **提交信息**: [Perf][Quantization] Honor FP8 activations for Humming linear on SM100/SM110 (#65077)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Kimi Code <noreply@moonshot.ai>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d74f39c](https://github.com/vllm-project/vllm/commit/d74f39c5a60aed2c8a11c2c482cf0ec8a3a2602e)

- **作者**: yifanFengg
- **时间**: 2026-11-11T21:24:45Z
- **提交信息**: [Perf] Tuned batch-invariant fused MoE configs on Blackwell (#63627)

Signed-off-by: Yifan Feng <evanfengff@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [d46cb72](https://github.com/vllm-project/vllm/commit/d46cb724ddaeb1146da9c9b882bf7679e049890b)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-11T21:17:39Z
- **提交信息**: [ROCm][Perf][MoE] Fuse SiLU-and-mul with per-token FP8 quant in TritonExperts and skip remote EP routes (#63721)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5d94702](https://github.com/vllm-project/vllm/commit/5d9470252e947e25e9be42fa2c87bb258e430463)

- **作者**: Yaoyao Ding
- **时间**: 2026-11-11T21:14:53Z
- **提交信息**: [Perf][DSv4.1] DSpark draft on the specialized decode (#61869)

Signed-off-by: Yaoyao Ding <yaoyaod@nvidia.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7be53a](https://github.com/vllm-project/vllm/commit/f7be53ae746e05ca2c5c5b1b879326945c5a6868)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-11T20:18:09Z
- **提交信息**: [Bugfix] Forward shutdown() in LMCacheConnectorV1 so EngineCore is not force-killed (#64324)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [aeadf92](https://github.com/vllm-project/vllm/commit/aeadf9252586e9db0e7658312d562036b45cd217)

- **作者**: Micah Williamson
- **时间**: 2026-11-11T19:48:57Z
- **提交信息**: [ROCm][MiniMax-M3.1] MXFP8 linear on AITER's tuned FlyDSL GEMM (#65479)

Signed-off-by: Micah Williamson <micah.williamson@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [52a9ce9](https://github.com/vllm-project/vllm/commit/52a9ce94fe29ea0a3d8dde04fdf1c25cdc215164)

- **作者**: olka-amd
- **时间**: 2026-11-11T19:21:47Z
- **提交信息**: [ROCm][Spec Decode] Enable adaptive DSpark verification for MiniMax M3 (#56451)

Signed-off-by: Oleksandr Kachur <oleksandr.kachur@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [277d49c](https://github.com/vllm-project/vllm/commit/277d49c53ef8f041d7fee7285e58e5f0171c2cc9)

- **作者**: Nikhil Kulkarni
- **时间**: 2026-11-11T19:11:43Z
- **提交信息**: [Bugfix][Transformers] Infer mm encoder dynamic_arg_dims from forward signature (#63636)

Signed-off-by: Nikhil Kulkarni <nikhilkulkarni1755@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3f4fbd6](https://github.com/vllm-project/vllm/commit/3f4fbd6fc983a7f7d89b68df4f2add335332dabd)

- **作者**: Yifei Wang
- **时间**: 2026-11-11T19:09:53Z
- **提交信息**: [MRV2][PP] Support different CUDA graph padding across pipeline stages (#66465)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b32a870](https://github.com/vllm-project/vllm/commit/b32a87094afc8e9ec349107db8526bebd552069d)

- **作者**: technovelist
- **时间**: 2026-11-11T19:02:57Z
- **提交信息**: [Bugfix][Offload] Apply --cpu-offload-gb to models served by the Transformers modeling backend (#66419)

Signed-off-by: Steve Heller <sheller@streamingkv.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: francesco-bertolotti <francesco.bertolotti@domyn.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ace415c](https://github.com/vllm-project/vllm/commit/ace415c06892a6119c88c8c57ed6fd761b722e32)

- **作者**: MohitAMD
- **时间**: 2026-11-11T18:39:23Z
- **提交信息**: [ROCm][Perf][DSA] Honor skip_kv_gather in the ROCm sparse-indexer prefill loop (#63878)

Signed-off-by: Mohit Deopujari <Mohit.Deopujari@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fe3ed68](https://github.com/vllm-project/vllm/commit/fe3ed684ce82ac822127facba4183001ac9516ef)

- **作者**: Vadim Gimpelson
- **时间**: 2026-11-11T18:00:03Z
- **提交信息**: [Bugfix] Apply the layer q_scale only to FP8 queries in FlashInfer (#64329)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7cc0a8a](https://github.com/vllm-project/vllm/commit/7cc0a8a2b1ef6888b44973933c8a208e91122229)

- **作者**: indivats
- **时间**: 2026-11-11T17:44:17Z
- **提交信息**: [Docs][ROCm] Add AMD verified autotrust/JEV-27B-VL recipe (#66625)

Signed-off-by: Indira Vats <Indira.Vats@amd.com>

### [adff2e8](https://github.com/vllm-project/vllm/commit/adff2e86fb12b1e964426e56600728fce6d401e4)

- **作者**: Divakar Verma
- **时间**: 2026-11-11T17:31:24Z
- **提交信息**: [CI][ROCm] Pin the AMD monokernel steps to explicit test files (#67038)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [dd07002](https://github.com/vllm-project/vllm/commit/dd07002d2d20ddd315914504ad0f92734688a509)

- **作者**: indivats
- **时间**: 2026-11-11T17:28:57Z
- **提交信息**: [Docs][ROCm] Add AMD verified ricursiveAI/Ripple-65B-Preview recipe (#66721)

Signed-off-by: Indira Vats <Indira.Vats@amd.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>

### [bc11b62](https://github.com/vllm-project/vllm/commit/bc11b62ca8203aff20440a84c601864531a8df75)

- **作者**: Wentao Ye
- **时间**: 2026-11-11T17:01:28Z
- **提交信息**: [GLM 5.3 Perf] enable fp8 kv cache for glm 5.3 flash draft model, 790MB GPU memory saved each rank (#66292)

Signed-off-by: yewentao256 <zhyanwentao@126.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [e8783e5](https://github.com/vllm-project/vllm/commit/e8783e54132a2847e62ff67ba6a5bd21f9a59700)

- **作者**: indivats
- **时间**: 2026-11-11T16:58:15Z
- **提交信息**: [Docs][ROCm] Add AMD verified inclusionAI/Ming-3.0-asr-tiny recipe (#66689)

Signed-off-by: Indira Vats <Indira.Vats@amd.com>

### [c64134c](https://github.com/vllm-project/vllm/commit/c64134cbc4f67f6ce348050d877d5d5475d79a75)

- **作者**: Giuseppe Grossi
- **时间**: 2026-11-11T16:24:00Z
- **提交信息**: [Bugfix][Kernel] Fix reshape & cache dropping KV heads past 512 chunks (#64087)

Signed-off-by: Giuseppe Grossi <ggrossi@amd.com>

### [a794844](https://github.com/vllm-project/vllm/commit/a7948445cc244475903f33169d65b12fe9bd6562)

- **作者**: Prajjwal Chittori
- **时间**: 2026-11-11T16:08:37Z
- **提交信息**: [Bugfix][Quantization] Keep unquantized routed experts unquantized under AutoGPTQ (#49539)

Signed-off-by: pjdurden <prajjwalchittori1@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c3d1ce6](https://github.com/vllm-project/vllm/commit/c3d1ce62b0f11d814696ff022259e70edb3046b5)

- **作者**: S.J. Lee
- **时间**: 2026-11-11T16:05:03Z
- **提交信息**: [Bugfix][Attention] Enable FlashInfer mm-prefix attention (#46558)

Signed-off-by: lesj0610 <lesj0610@users.noreply.github.com>
Signed-off-by: lesj0610 <lesj0610@gmail.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: lesj0610 <lesj0610@users.noreply.github.com>
Co-authored-by: Claude Fable 5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [62529d6](https://github.com/vllm-project/vllm/commit/62529d6a2d22586c72c19aaf993840f4e064a680)

- **作者**: A&W
- **时间**: 2026-11-11T16:01:46Z
- **提交信息**: [Bugfix][Pooling] Use the SigLIP chat template over the Gemma one for SigLIP2 (#66624)

Signed-off-by: Alex-Wengg <hanweng9@gmail.com>

### [783abce](https://github.com/vllm-project/vllm/commit/783abce9b3a26894be16cc4b2e84775ecfe22c76)

- **作者**: Mikko Tukiainen
- **时间**: 2026-11-11T15:55:29Z
- **提交信息**: [ROCm][Perf][Muse Spark] Enable the bf16x3 router GEMM on gfx942 (#63724)

Signed-off-by: Mikko Tukiainen <Mikko.Tukiainen@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [1c76375](https://github.com/vllm-project/vllm/commit/1c7637504238247acacbfbf1dabe42e057c73044)

- **作者**: Jee Jee Li
- **时间**: 2026-11-11T15:18:25Z
- **提交信息**: [Bugfix][Muse Spark] Avoid the FlashInfer Cake PDL race in gated_residual_rmsnorm (#66986)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [5be8acb](https://github.com/vllm-project/vllm/commit/5be8acb7f2e7a9dd22246df3fbbadb173795160e)

- **作者**: Bruno Volpato
- **时间**: 2026-11-11T15:08:39Z
- **提交信息**: [Bugfix][DP] Prevent mismatched collectives on duplicate resume (#55229)

Signed-off-by: Bruno Volpato <brunocvcunha@gmail.com>
Signed-off-by: bvolpato <brunocvcunha@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3c5cdcf](https://github.com/vllm-project/vllm/commit/3c5cdcfee76bbd4fd26a77fd2b97520ecaa78e38)

- **作者**: mengziheng
- **时间**: 2026-11-11T13:49:54Z
- **提交信息**: [Perf] Tune GLM-5.3-Flash block-FP8 MoE for H20 (#58986)

Signed-off-by: mengziheng <121283369+mengziheng@users.noreply.github.com>
Signed-off-by: mengziheng <zhmeng.cn@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: TRAE CLI <traecli@bytedance.com>

### [2e9a6ad](https://github.com/vllm-project/vllm/commit/2e9a6ad8100cf648d1c87c03f723dfe34fe5d12a)

- **作者**: Robert Esclapez
- **时间**: 2026-11-11T13:34:11Z
- **提交信息**: [ROCm][gfx1151] ROCM_RDNA_ATTN: attention backend for RDNA (#63383)

Signed-off-by: Robert Esclapez Garcia <robert.garcia@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [5c08d2c](https://github.com/vllm-project/vllm/commit/5c08d2c72aae7527a94f6b2281270ef8ad0e833b)

- **作者**: zexplorerhj
- **时间**: 2026-11-11T13:32:26Z
- **提交信息**: [Model] Add Ling VL video, YaRN, and vision DP support (#65848)

Signed-off-by: zexplorerhj <zhjoneson@163.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b0fbb3c](https://github.com/vllm-project/vllm/commit/b0fbb3cc6796cf509e43debe0ae4f28f0f47eb71)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T13:12:36Z
- **提交信息**: [CI] Only warn on VibeVoice-ASR mixed-length syncs before Transformers 5.23 (#67026)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f6cbdda](https://github.com/vllm-project/vllm/commit/f6cbdda2b6f54fee19823db25b068a08fd0f2313)

- **作者**: Zaoyi Zheng
- **时间**: 2026-11-11T12:56:54Z
- **提交信息**: [Metrics] Export scheduler-state gauges before the first request with --api-server-count > 1 (#60001)

Signed-off-by: Roy Zheng <39311511+roy6n23@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8d5b613](https://github.com/vllm-project/vllm/commit/8d5b613174f34b2fa67985701820618638a9795e)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T12:45:08Z
- **提交信息**: [Transformers backend] Serve Qwen2-MoE with the Transformers modeling backend (#66827)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [92f3ee5](https://github.com/vllm-project/vllm/commit/92f3ee5ae4abb86f2b175b13e623dab4a21b0986)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T12:39:09Z
- **提交信息**: [Model] Move MiniMax-M3 to `AutoWeightsLoader` (#65904)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6653573](https://github.com/vllm-project/vllm/commit/665357362de6e2b3d48068fa9f2ab8a636772f02)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-11T12:33:29Z
- **提交信息**: [Spec Decode][DCP] DSpark: run sliding-window MLA drafts under DCP (#63796)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>

### [1c4211f](https://github.com/vllm-project/vllm/commit/1c4211fb29e55c4083bbb19dac2fbaa195625884)

- **作者**: Chauncey
- **时间**: 2026-11-11T11:50:14Z
- **提交信息**: [Perf][GLM-5.3] Extend ShardQ token sharding to norms and A projections (#66549)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2acfc19](https://github.com/vllm-project/vllm/commit/2acfc19eeb6a4b9e11573ae43eeb9ea8eadb76ab)

- **作者**: Juntian Liu
- **时间**: 2026-11-11T11:43:47Z
- **提交信息**: [Perf][DSv4.1] Engram: 128-row lookup tiles; split GPU tables across engines (#66552)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [61efa50](https://github.com/vllm-project/vllm/commit/61efa50b1660a2b8148878af4321d25cad5e07d3)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T11:18:25Z
- **提交信息**: Remove the dual-chunk attention leftovers (#66834)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f5f451f](https://github.com/vllm-project/vllm/commit/f5f451f7d83bdaf746a4e13043bf9d9eea1048cb)

- **作者**: Subhash Polisetti
- **时间**: 2026-11-11T10:49:48Z
- **提交信息**: [CI][Multimodal] Run the Unlimited-OCR-2 preemption test batch-invariant (#66994)

Signed-off-by: subhash polisetti <subhashr161347@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7f07922](https://github.com/vllm-project/vllm/commit/7f079220d12e76b9451a4e41a6070893109c549e)

- **作者**: CharlesWu
- **时间**: 2026-11-11T10:37:51Z
- **提交信息**: [UMBP][9/10] Add lazy GPU cache offloading (#61797)

Signed-off-by: CharlesWu <Charles.Wu@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [cdd0970](https://github.com/vllm-project/vllm/commit/cdd09707378563a4228270bd0bb5b83bcb0d1acc)

- **作者**: Thang Nguyen
- **时间**: 2026-11-11T10:24:21Z
- **提交信息**: [CI] Run the NIXL PD accuracy core sweep as pytest and shard it (#66196)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [3848326](https://github.com/vllm-project/vllm/commit/38483263f4f79d46fca60f0b39c2d8436781798e)

- **作者**: Bugen Zhao
- **时间**: 2026-11-11T10:13:09Z
- **提交信息**: [Rust Frontend] Run more Python server tests against the Rust frontend (#66781)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2ee8250](https://github.com/vllm-project/vllm/commit/2ee8250eaf67059b4e8bc3c1bfb4cfb1c88892a7)

- **作者**: Yunt1
- **时间**: 2026-11-11T10:00:54Z
- **提交信息**: [Bugfix][Frontend] Reject empty messages in ChatCompletionRequest (#66489)

Signed-off-by: Yunt1 <Yunt1@users.noreply.github.com>
Co-authored-by: Yunt1 <Yunt1@users.noreply.github.com>
Co-authored-by: Kscc <noreply@owtffssent.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [01fba62](https://github.com/vllm-project/vllm/commit/01fba62494f4fd61c6f36c0dafbe4eae13d90833)

- **作者**: Roy Wang
- **时间**: 2026-11-11T09:06:01Z
- **提交信息**: [Rust][Benchmark] Align vllm-bench result files and requests with Python (#65541)

Signed-off-by: esmeetu <jasonailu87@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8d902b4](https://github.com/vllm-project/vllm/commit/8d902b41379ff8fbeba3c14b1748f6ae92705386)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T08:52:54Z
- **提交信息**: [Transformers backend] Fix M-RoPE models under CUDA graphs (#66833)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [63ac0a4](https://github.com/vllm-project/vllm/commit/63ac0a4ee118db1cae5bed52b2b9e5e9bf279abe)

- **作者**: Yifei Wang
- **时间**: 2026-11-11T08:46:10Z
- **提交信息**: [Bugfix][Model] Fix GraniteMoeHybrid pipeline-parallel startup (#66007)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Niket Jain <51831161+nikJ13@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a9185fc](https://github.com/vllm-project/vllm/commit/a9185fc5c5644690d58891d274b9c823a4715ecc)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T08:44:19Z
- **提交信息**: [Transformers backend] Fuse the GLU activation with the down projection's input quant (#66809)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a0a462](https://github.com/vllm-project/vllm/commit/5a0a4622201678382ee2edccc4e82688520fb834)

- **作者**: Ziyang Ma
- **时间**: 2026-11-11T08:34:38Z
- **提交信息**: [XPU][UT] Add device-specific logic to enable DFlash MXFP8 context KV test for XPU (#66952)

Signed-off-by: RyanMa29 <ziyang.ma@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [ef1a85b](https://github.com/vllm-project/vllm/commit/ef1a85bce2e76c8f7a6be243d7dded71e018d481)

- **作者**: alberto
- **时间**: 2026-11-11T08:33:23Z
- **提交信息**: [Bugfix][Frontend] Reject Anthropic max_tokens=0 prewarm with an actionable error (#65976)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [ff270c5](https://github.com/vllm-project/vllm/commit/ff270c5b04b59ede63b8afcb470c8956f1b056bc)

- **作者**: Bugen Zhao
- **时间**: 2026-11-11T08:27:23Z
- **提交信息**: [Rust Frontend] Support the JSON log formatter (#66539)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e769014](https://github.com/vllm-project/vllm/commit/e76901475804e4b3aa51ad1df6fe5db834fc5ac8)

- **作者**: Bugen Zhao
- **时间**: 2026-11-11T08:26:04Z
- **提交信息**: [Rust Frontend] Log the finished request count in the periodic stats line (#66979)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [54598fd](https://github.com/vllm-project/vllm/commit/54598fdaa474ca119605b951759a060775ab7119)

- **作者**: Bugen Zhao
- **时间**: 2026-11-11T08:24:39Z
- **提交信息**: [Rust Frontend] Carry weight versions as per-output deltas (#66780)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f9eb432](https://github.com/vllm-project/vllm/commit/f9eb4324318b10da7267aa9dce8f304c16560550)

- **作者**: Bugen Zhao
- **时间**: 2026-11-11T08:22:54Z
- **提交信息**: [Rust Frontend] Resolve tool_choice without tools like Python (#66980)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8551e3a](https://github.com/vllm-project/vllm/commit/8551e3a13f5ea07f46bb70a18c800990c9fd2a6a)

- **作者**: Akshat Anand
- **时间**: 2026-11-11T08:06:30Z
- **提交信息**: [Bugfix][Tool Parser] Olmo3: stream plain text that starts with "<" (#65936)

Signed-off-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [fcc1015](https://github.com/vllm-project/vllm/commit/fcc1015e33fd05f7d290d8a1f07cf089fd6ab398)

- **作者**: Harry Mellor
- **时间**: 2026-11-11T07:41:17Z
- **提交信息**: [torch.compile] Only flag `_buffers.update` in the cudagraph buffer assignment check (#65446)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bbadbc1](https://github.com/vllm-project/vllm/commit/bbadbc1545a664c25e4943f73708b96927fc9483)

- **作者**: Cr
- **时间**: 2026-11-11T07:40:48Z
- **提交信息**: [Frontend] Log outputs for batched chat completions (#66853)

Signed-off-by: Cr <60964294+Chr0mium24@users.noreply.github.com>

### [bafa5c6](https://github.com/vllm-project/vllm/commit/bafa5c6c30b8397e64fb6a73740b9ebe71a18f05)

- **作者**: Fanli Lin
- **时间**: 2026-11-11T07:01:00Z
- **提交信息**: [CI][XPU] skip one more TP=2 test in Distributed Shutdown job (#66568)

Signed-off-by: Lin, Fanli <fanli.lin@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3ea131c](https://github.com/vllm-project/vllm/commit/3ea131ca2c28b02e1a83ed1490bf8a3c69ddbfe0)

- **作者**: liuzhenwei
- **时间**: 2026-11-11T06:46:48Z
- **提交信息**: [XPU][CI] Skip LMCacheMPConnector tests when lmcache is not installed (#66924)

Signed-off-by: zhenwei-intel <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [078f855](https://github.com/vllm-project/vllm/commit/078f855f9c0577750a02128a1d517c038d872c03)

- **作者**: Yifei Wang
- **时间**: 2026-11-11T06:43:44Z
- **提交信息**: [Bugfix][Step5] Fix FP32 residual truncation at pipeline boundaries (#65755)

Signed-off-by: Yifei Wang <yifei.w@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3ec1b24](https://github.com/vllm-project/vllm/commit/3ec1b24a751612659cde537cc1636dadce4de545)

- **作者**: Zhehao Hu
- **时间**: 2026-11-11T06:05:38Z
- **提交信息**: [Model][DSV4.1] Support MXFP4-packed Engram embedding tables (#61530)

Signed-off-by: Zhehao Hu <zhehaoh@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [f5d9329](https://github.com/vllm-project/vllm/commit/f5d93296c8ec82b7e7dabdb308d24d43cb1907bf)

- **作者**: Martin Hickey
- **时间**: 2026-11-11T05:50:05Z
- **提交信息**: [Bugfix][Frontend] Honor --response-role and echo in chat derender (#63357)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [32cdd79](https://github.com/vllm-project/vllm/commit/32cdd79b0ca865687ff24461dd149a3d3de3518c)

- **作者**: Rudransh Shekhar
- **时间**: 2026-11-11T05:45:44Z
- **提交信息**: [Bugfix][Tokenizers] Raise ValueError on unknown message role in deepseek_v41_encoding (#66848)

Signed-off-by: rudy-07 <kanhaiffco2007@gmail.com>

### [31bfd6f](https://github.com/vllm-project/vllm/commit/31bfd6f7138b445bcae0bd889e73556766aac4f6)

- **作者**: Archit Shukla
- **时间**: 2026-11-11T05:45:04Z
- **提交信息**: [Bugfix][Frontend] Report the line of a run-batch request rejected by request validators (#65029)

Signed-off-by: Archit Shukla <architshukla546@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [176a74c](https://github.com/vllm-project/vllm/commit/176a74c8e056db5c9876a0ed1698892a4901bb7b)

- **作者**: Yan Ma
- **时间**: 2026-11-11T05:05:03Z
- **提交信息**: [XPU] fix test_dots_ocr.py::test_dots_ocr_vision_without_host_sync (#66758)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>

### [ba0ef82](https://github.com/vllm-project/vllm/commit/ba0ef8297d880efcc46b7d187cff15fa880759c0)

- **作者**: Akshat Anand
- **时间**: 2026-11-11T04:32:24Z
- **提交信息**: [KV Offload] Warn when secondary-tier KV is tied to the parallel config (#62566)

Signed-off-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: cipheraxat <cipheraxat@users.noreply.github.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>

### [595b151](https://github.com/vllm-project/vllm/commit/595b1514e837ba38df7ae51c411807783e227b78)

- **作者**: Jee Jee Li
- **时间**: 2026-11-11T03:23:29Z
- **提交信息**: [Perf][Muse Spark] Fuse DSpark draft norms and Markov sampling on NVIDIA (#66764)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a58e84c](https://github.com/vllm-project/vllm/commit/a58e84c8cb3d75d1879e16bc6f8459bbc6c3a4dd)

- **作者**: Jhao-Ting Chen
- **时间**: 2026-11-11T03:02:21Z
- **提交信息**: [Perf][Mamba] Opt-in FlashInfer SSD prefill scan; per-step ReplaySSM seed (#61501)

Signed-off-by: Jhao-Ting Chen <jhaotingc@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [960f5c1](https://github.com/vllm-project/vllm/commit/960f5c1bb14533ed759344fdd745b623c474f901)

- **作者**: Justin Davis
- **时间**: 2026-11-11T02:02:24Z
- **提交信息**: [Multimodal] Add keyframe-aware sampling to PyNvVideoCodec backend (#66073)

Signed-off-by: justincdavis <judavis@nvidia.com>
Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Brandon Pelfrey <bpelfrey@nvidia.com>

### [ff870bf](https://github.com/vllm-project/vllm/commit/ff870bf622e5a91916d9c9507e0250844282acad)

- **作者**: mispa-ms
- **时间**: 2026-11-11T02:02:11Z
- **提交信息**: [Recipe] Kimi-K3.1-Pro: add B300 AgentX presets, align with InferenceX#4871 (#66433)

Signed-off-by: Mi Sun Park <misunp@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>

### [bcd6bd8](https://github.com/vllm-project/vllm/commit/bcd6bd810f77b850ac21792ee60de90f470e68c3)

- **作者**: Oxana Korzh
- **时间**: 2026-11-11T02:00:15Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono: tuned K1 at TP8 (#64152)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [80ac42b](https://github.com/vllm-project/vllm/commit/80ac42b811ffea9dd8f2d2b1ea67beab5e20f7cf)

- **作者**: Oxana Korzh
- **时间**: 2026-11-11T01:58:42Z
- **提交信息**: [Bugfix][Spec Decode] Synchronize adaptive DSpark decisions across TP ranks (#62769)

Signed-off-by: Cedric Huang <38417461+CedricHwong@users.noreply.github.com>
Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Cedric Huang <38417461+CedricHwong@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c7dd34c](https://github.com/vllm-project/vllm/commit/c7dd34ccea7a9845324b2dc55bd57c174172144d)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-11T01:41:38Z
- **提交信息**: [ROCm][Bugfix] Allow lut_b_moe online quantization on ROCm (#66876)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f1cf166](https://github.com/vllm-project/vllm/commit/f1cf1663f852cdc3924dc280d8f1a0aed5fbca52)

- **作者**: Josh Schell
- **时间**: 2026-11-11T01:38:10Z
- **提交信息**: [ROCm][Kimi-K3] Keep the AttnRes block bank in a persistent workspace (#63838)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [54b29e2](https://github.com/vllm-project/vllm/commit/54b29e254bf6ba607c8d5d68f91c7f3e4270e46b)

- **作者**: Roy Wang
- **时间**: 2026-11-11T01:34:48Z
- **提交信息**: [Doc][Recipe] Muse Spark Open: DSpark + specialized decode mode; gate Kimi-K3.1 low-latency decode off AMD (#66203)

### [9cb56aa](https://github.com/vllm-project/vllm/commit/9cb56aae70d0f6cae61413a0a3d0b5b5d6cdc864)

- **作者**: Roy Wang
- **时间**: 2026-11-11T01:33:48Z
- **提交信息**: [Recipe] Qwen3.5: keep configuration-specific content out of the guides (#64070)

### [3025c1e](https://github.com/vllm-project/vllm/commit/3025c1e641f84faec4d2f9b973cf5da50a1cef8d)

- **作者**: Roy Wang
- **时间**: 2026-11-11T01:33:30Z
- **提交信息**: [Recipe] Kimi-K3, MiniMax-M3.1-Flash: add Rubin VR200 support (#65400)

### [6e3367c](https://github.com/vllm-project/vllm/commit/6e3367c33a9be4d99c634c6dea5abe73253089b9)

- **作者**: Stary
- **时间**: 2026-11-11T01:24:03Z
- **提交信息**: [KVConnector] Reuse the Mooncake PD TransferEngine in the store connector (#65943)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [e3ddbdb](https://github.com/vllm-project/vllm/commit/e3ddbdbd60f3a3e97b3c128ef94e92169a86c081)

- **作者**: Thang Nguyen
- **时间**: 2026-11-11T01:22:23Z
- **提交信息**: [CI] Split the platform and stat logger plugin tests out of Plugin Integration and shard it (#66645)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [25a6a8b](https://github.com/vllm-project/vllm/commit/25a6a8bd1058e8359629a74485b2b37154c0947e)

- **作者**: Thang Nguyen
- **时间**: 2026-11-11T01:04:14Z
- **提交信息**: [CI] Enroll Language Models (Extended Generation) in automatic sharding; spawn in test_gemma's dummy-loader test (#65979)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9e11f3c](https://github.com/vllm-project/vllm/commit/9e11f3ca7d5f54ca6a151f60457e3b033aecb72f)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-11-11T01:03:09Z
- **提交信息**: [Bugfix][Model] Let DomynEdge mix sliding and full attention layers (#66819)

Signed-off-by: jiaqiang-dot-liu <jiaqiang.liu@amd.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [1bf45bb](https://github.com/vllm-project/vllm/commit/1bf45bb23d1f3e7811157b1202acdf8ac1353bc3)

- **作者**: Thang Nguyen
- **时间**: 2026-11-11T01:03:04Z
- **提交信息**: [CI] Enroll Language Models (Hybrid) and Granite Compatibility in automatic sharding (#64604)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [cf4af0a](https://github.com/vllm-project/vllm/commit/cf4af0ae5fbfc6ed8311fdc51009005ce79bed99)

- **作者**: Reid
- **时间**: 2026-11-11T00:56:53Z
- **提交信息**: [Perf][Rust][Benchmark] Reuse allowed tokens in multi-turn generation (#65768)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c3cee35](https://github.com/vllm-project/vllm/commit/c3cee35ab85ccd1b9f2fb618927d4aa93183dd61)

- **作者**: liuzhenwei
- **时间**: 2026-11-11T00:12:13Z
- **提交信息**: [XPU][CI] Keep all devices visible for external LB (#66446)

Signed-off-by: liuzhenwei <zhenwei.liu@intel.com>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-12
**监控日期**: 2026-11-11
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7705
- **最后更新**: 2026-11-12T02:33:21Z

## 提交统计

- **昨日提交总数**: 46
- **提交者数量**: 26
- **主要提交者**: DarkMatter, wangyu, Chendi.Xue

## AI分析总结

## 一、主要更新类型

- **CI/Build（约 17 条）**：占比最高，集中在 ROCm/AMD 每周与夜间任务的覆盖扩展、稳定性修复、任务隔离与按变更定向运行。
- **Bugfix（约 12 条）**：涉及多模态模型（MiniMax-H3、Audex、MiniCPM-o、MOSS、Wan VAE）在 NPU/ROCm/XPU 上的正确性问题。
- **Model/Feature（约 10 条）**：新增模型支持（MiniMax-H3-Image、LFM3/LFM3-Audio-2B）与核心运行时能力（MRv2、CFG 批处理、TP 分片）。
- **文档与重构**：少量文档修复与 Diffusion 采样器重构。

## 二、关键变更点与项目方向的关系

项目目标是"为所有人提供简单、快速、低成本的全模态模型服务"。本批提交围绕三条主线：

1. **多硬件平台成熟化**：ROCm、NPU（昇腾）、Intel XPU 均有大量修复与优化（如 gfx11 强制 math SDPA、XPU 视频 VAE 解码快速路径、NPU codec 采样主机化），体现"人人可用"的跨硬件普惠定位。
2. **新模型持续接入**：MiniMax-H3-Image 文生图与图像编辑、LFM3 系列 CUDA 支持，直接扩展全模态能力边界。
3. **运行时核心演进**：Model Runner V2（MRv2）在多处启用（JoyAI-VL、MiniCPM-o NPU 全三阶段服务、CUDA E2E 周测、AR 阶段 draft tokens），表明 MRv2 正在成为统一执行路径。

## 三、对项目的影响和潜在意义

- CI 层面从"跑通"转向"可信"：NIGHTLY 任务晋升为阻塞项、证据守护、隔离测试环境，显著提升回归防线质量，减少硬件差异导致的假阴性。
- 模型覆盖从语音/文本扩展到图像生成与编辑（MiniMax-H3-Image），强化了 omni（全模态）定位。
- NPU 上 MiniCPM-o 4.5 全 MRv2 默认开启、Talker K-step K=8，说明华为团队在端侧多模态推理上深度投入，有利于生态多元化。

## 四、值得关注的技术点

- **CFG 批处理优化**：将 CFG 双分支合并为单次 denoiser 调用，是 Diffusion 性能的关键杠杆。
- **通用 HF 文本编码器 TP 支持 + AdaLN 投影分片**：为大图像模型的多卡扩展奠定基础。
- **设备图（device graph）捕获回放**（XPU Diffusion）：针对 denoise 步骤的延迟优化。
- **自定义语音 prefill 奇偶校验与 BF16 漂移隔离**：反映了对数值精度的精细化管控。
- **MiniCPM-o eager codec cache 拷贝减少**、可移植 speaker 放置：内存与部署灵活性改进。

## 五、对项目发展的影响

这批提交表明 vllm-omni 已进入"多硬件、多模型并行打磨"的工程化深水区：通过大规模 CI 加固保证质量底线，通过 MRv2 统一执行框架收敛架构，通过持续接入图像/语音新模型兑现"全模态"承诺。短期看会提升各平台周测的稳定性与模型覆盖广度；长期看，MRv2 与跨硬件修复的积累将降低新增模型的移植成本，推动项目向"人人可用的全模态服务"目标稳步靠近。

## 详细提交记录

### [a72de09](https://github.com/vllm-project/vllm-omni/commit/a72de0985bdc15c2b4fd9690fc895f0bb46ce2c7)

- **作者**: hac17
- **时间**: 2026-11-11T23:53:27Z
- **提交信息**: [CI/Build][ROCm] Isolate CustomVoice prefill parity from BF16 decoder drift (#10209)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [02d7bc4](https://github.com/vllm-project/vllm-omni/commit/02d7bc47e7afae1412598df18b3889b495e5fd4a)

- **作者**: wangyu
- **时间**: 2026-11-11T20:34:42Z
- **提交信息**: [Test] Relax cancel-bounds cleanup abort harness bound to 5s (#10183)

Signed-off-by: yenuo26 <410167048@qq.com>

### [7a47bbb](https://github.com/vllm-project/vllm-omni/commit/7a47bbb72d029eb6c7d0361026380f3d50ce5d9a)

- **作者**: lm10-arg
- **时间**: 2026-11-11T18:41:38Z
- **提交信息**: [CI/Build][ROCm] Add weekly Audex, CosyVoice3, and Qwen3-TTS coverage (#10180)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [d3414a3](https://github.com/vllm-project/vllm-omni/commit/d3414a3b03b1ca55ac342e4d4f4e8778c3b2b7be)

- **作者**: xiangrong zhong
- **时间**: 2026-11-11T18:09:23Z
- **提交信息**: [Bugfix] Clamp MiniMax-H3 shifted sigmas to [0, 1] (#10158)

Signed-off-by: zhongc1211 <huixindaddy@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e7528f2](https://github.com/vllm-project/vllm-omni/commit/e7528f24333a63f37a47d8291f914df7e1451ade)

- **作者**: William Ren
- **时间**: 2026-11-11T17:58:24Z
- **提交信息**: [Doc] Fix stale import path and moved links in contributor docs (#10156)

Signed-off-by: Wei Ren <Williamren97@gmail.com>

### [b32b8bd](https://github.com/vllm-project/vllm-omni/commit/b32b8bd7793ce81912315ef78b6e7c26152498cf)

- **作者**: lm10-arg
- **时间**: 2026-11-11T17:43:22Z
- **提交信息**: [Bugfix][ROCm] Force math SDPA for Wan VAE on gfx11 (#10205)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [ed0e43f](https://github.com/vllm-project/vllm-omni/commit/ed0e43fe407656e287806556d8d2029ffbda0720)

- **作者**: Hyoseop Song
- **时间**: 2026-11-11T16:19:58Z
- **提交信息**: [Bugfix] Read SHM wakeup scope from flat config (#10171)

Signed-off-by: Hyoseop Song <crad_on25@naver.com>

### [a91c3bd](https://github.com/vllm-project/vllm-omni/commit/a91c3bde18d0dfcd69631f030bfa9ede0e886c14)

- **作者**: yzhautouskay
- **时间**: 2026-11-11T16:03:51Z
- **提交信息**: [Bugfix][Diffusion] Fix Cosmos3 Transfer SeaCache artifacts with target-only indicators (#7939)

Signed-off-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>

### [9b70b3a](https://github.com/vllm-project/vllm-omni/commit/9b70b3a0d470715ce9a20f48deef9e3690f75d79)

- **作者**: lm10-arg
- **时间**: 2026-11-11T15:10:04Z
- **提交信息**: [Bugfix] Handle scalar pooling outputs in stage metrics (#10188)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [c03f729](https://github.com/vllm-project/vllm-omni/commit/c03f72934d9eeadcd0f2a2edac2a7e93a2810e6d)

- **作者**: Chendi.Xue
- **时间**: 2026-11-11T15:07:13Z
- **提交信息**: [Hardware][Intel][MiniMax-H3] XPU video VAE decoder fast paths and geometry-chosen tile gather (#9437)

Signed-off-by: heyuanliu-intel <heyuan.liu@intel.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: heyuanliu-intel <90166842+heyuanliu-intel@users.noreply.github.com>

### [f23dd4c](https://github.com/vllm-project/vllm-omni/commit/f23dd4c279ff8f350a1e2a2bdafa16ac71cd9068)

- **作者**: NATURE
- **时间**: 2026-11-11T14:26:30Z
- **提交信息**: [Model] Enable MRv2 for JoyAI-VL-Interaction on CUDA (#10149)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>

### [2b3c2ac](https://github.com/vllm-project/vllm-omni/commit/2b3c2acbf7959bb7650abc100a236963a27d39c6)

- **作者**: ooooooye
- **时间**: 2026-11-11T14:06:21Z
- **提交信息**: [Doc][NPU] Add the MiniMax-H3-Image Ascend NPU recipe (#10155)

### [6883516](https://github.com/vllm-project/vllm-omni/commit/68835163aca835037a054da96c2b22cb8886d135)

- **作者**: lm10-arg
- **时间**: 2026-11-11T13:51:09Z
- **提交信息**: [Bugfix][ROCm] Fix Audex Code2Wav startup metadata (#10187)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [c47ea33](https://github.com/vllm-project/vllm-omni/commit/c47ea33839041e6b835c4b39eb489123b15cd480)

- **作者**: heyew
- **时间**: 2026-11-11T13:45:01Z
- **提交信息**: [Bugfix][NPU] Correct MOSS codec shared streaming attention masks (#10104)

Signed-off-by: heyew <2025190973@qq.com>
Co-authored-by: Weiming Liao <liaowm5@gmail.com>

### [ac98192](https://github.com/vllm-project/vllm-omni/commit/ac98192be11551845327952d33be5387a70170e0)

- **作者**: y-null
- **时间**: 2026-11-11T13:12:32Z
- **提交信息**: [Model][NPU] Host-side codec sampling and device K-step chain removal for MiniCPM-o 4.5 (#9990)

Signed-off-by: y_null <y_null@qq.com>
Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9374f39](https://github.com/vllm-project/vllm-omni/commit/9374f3914a5b3b03fcb0110cd7a1ba5f2806e0c2)

- **作者**: lm10-arg
- **时间**: 2026-11-11T13:11:17Z
- **提交信息**: [CI/Build][ROCm] Extend pause-keep cold AITER JIT budget (#10189)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [bdcf5a2](https://github.com/vllm-project/vllm-omni/commit/bdcf5a2a2a9760a1aee4f84f59923a2d84cd0718)

- **作者**: wangyu
- **时间**: 2026-11-11T12:25:26Z
- **提交信息**: [CI/Build] Enable Model Runner V2 on weekly CUDA E2E jobs (#10073)

Signed-off-by: wangyu <410167048@qq.com>

### [17a5336](https://github.com/vllm-project/vllm-omni/commit/17a53366973e68f7670625745fd5359f26bfc810)

- **作者**: lm10-arg
- **时间**: 2026-11-11T11:59:41Z
- **提交信息**: [CI/Build] Repair deterministic pre-merge collection guards (#10182)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [bb59825](https://github.com/vllm-project/vllm-omni/commit/bb5982587ed2830a26fdb7273598ba148e4083cc)

- **作者**: Ranran
- **时间**: 2026-11-11T10:50:35Z
- **提交信息**: [Bugfix][MiniCPM-o] Support portable Torch speaker placement (#9722)

Signed-off-by: Ranran Haoran Zhang <ranranhaoranzhang@gmail.com>
Signed-off-by: Ranran Haoran Zhang <haorzhang@ebay.com>

### [7e9d75b](https://github.com/vllm-project/vllm-omni/commit/7e9d75bc45e6400f0cb8a3736c80b492e698fe7a)

- **作者**: Ranran
- **时间**: 2026-11-11T10:50:30Z
- **提交信息**: [Model] Reduce MiniCPM-o eager codec cache copies (#9723)

Signed-off-by: Ranran Haoran Zhang <ranranhaoranzhang@gmail.com>
Signed-off-by: Ranran Haoran Zhang <haorzhang@ebay.com>

### [35ec29d](https://github.com/vllm-project/vllm-omni/commit/35ec29d47f2d317b8d39587b4215bb606adf2fdc)

- **作者**: dongbo910220
- **时间**: 2026-11-11T10:25:52Z
- **提交信息**: [Core] Propose draft tokens on MRv2 AR stages; DSpark and padded DiT compilation for CosyVoice3 (#9692)

Signed-off-by: dongbo910220 <1275604947@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [e53517e](https://github.com/vllm-project/vllm-omni/commit/e53517e8b1da0f8896023f7caa6869eba2807acd)

- **作者**: dengyunyang
- **时间**: 2026-11-11T10:09:17Z
- **提交信息**: [CI/Build] Isolate diffusion attention test environments (#10172)

Signed-off-by: dengyunyang <584797741@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [78b6828](https://github.com/vllm-project/vllm-omni/commit/78b6828504f36825a21732cd6b79ce9a7ccfc504)

- **作者**: lm10-arg
- **时间**: 2026-11-11T10:06:55Z
- **提交信息**: [CI/Build][ROCm] Stabilize AMD invalid-parameter weekly jobs (#10159)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [27a5ae9](https://github.com/vllm-project/vllm-omni/commit/27a5ae972b51684edb9c43457ad841e1df8152f2)

- **作者**: Lingwei1943
- **时间**: 2026-11-11T10:04:39Z
- **提交信息**: [NPU][VoxCPM2] Expose cfg_value as VLLM_OMNI_SPEECH_CFG_VALUE for deployment tuning (#9699)

Signed-off-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Signed-off-by: yenuo26 <410167048@qq.com>
Signed-off-by: wangyu <410167048@qq.com>
Signed-off-by: [Your Name] <your.email@example.com>
Signed-off-by: zhuhh97 <zhuhonghan@huawei.com>
Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: Lingwei1943 <lingwei1943@users.noreply.github.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Honghan Zhu <zhuhonghan@huawei.com>
Co-authored-by: dengyunyang <584797741@qq.com>
Co-authored-by: y-null <y_null@qq.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>

### [4e26cdc](https://github.com/vllm-project/vllm-omni/commit/4e26cdcb457b6a863d444d905f5957e3d2b9fca3)

- **作者**: ZhIMQ
- **时间**: 2026-11-11T09:09:29Z
- **提交信息**: [Bugfix][MiniMax-H3] Wait for peers before tearing down the prestart test's process group (#9587)

Signed-off-by: ZhIMQ <15000371166@163.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: dengyunyang <584797741@qq.com>

### [7465c0f](https://github.com/vllm-project/vllm-omni/commit/7465c0f52bcb46a55f62c1b8613846cda30d0083)

- **作者**: nodeeeeee
- **时间**: 2026-11-11T08:54:47Z
- **提交信息**: [Refactor][Diffusion] Let samplers control model calls and latent updates (#9088)

Signed-off-by: nodeeeeee <zhangkai.nodeee@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>

### [8e63fa5](https://github.com/vllm-project/vllm-omni/commit/8e63fa5975c492a309f26a7aa29e1186d7d040a3)

- **作者**: DarkMatter
- **时间**: 2026-11-11T08:44:03Z
- **提交信息**: [CI/Build] Temporarily remove the Ulysses symmetric memory NPU Ready (#10146)

Signed-off-by: DarkMatter9527 <1376576122@qq.com>

### [4bc3408](https://github.com/vllm-project/vllm-omni/commit/4bc340899368f817c1c481b9c5a060c705270304)

- **作者**: wuli666
- **时间**: 2026-11-11T08:07:26Z
- **提交信息**: [CI/Build] Calibrate LFM3-Omni streaming HNR floor (#10166)

Signed-off-by: wuli666 <421774554@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [0b74da1](https://github.com/vllm-project/vllm-omni/commit/0b74da131f963ab2fd60f7eba813145672cf81e4)

- **作者**: Sheng GAO
- **时间**: 2026-11-11T07:36:28Z
- **提交信息**: [Bugfix] Forward images num_frames for LingBot T2I (#10137)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [eb8b991](https://github.com/vllm-project/vllm-omni/commit/eb8b991ff692c3c304472044ef18772c65bc7eee)

- **作者**: 汪志鹏
- **时间**: 2026-11-11T07:32:43Z
- **提交信息**: [Model] Add MiniMax-H3-Image text-to-image and image editing (#10120)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Hongxia Yang <hongxia.yang@amd.com>

### [702917b](https://github.com/vllm-project/vllm-omni/commit/702917be6b58afff29cb71cfd012e84e1cffddab)

- **作者**: y-null
- **时间**: 2026-11-11T07:19:39Z
- **提交信息**: [NPU] MiniCPM-o 4.5: full-MRv2 three-stage serving (default on NPU, Talker K-step K=8 + stop latch) (#10062)

Signed-off-by: y-null <213026468+y-null@users.noreply.github.com>
Signed-off-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: y-null <213026468+y-null@users.noreply.github.com>
Co-authored-by: y-null <y-null@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [a12cc3a](https://github.com/vllm-project/vllm-omni/commit/a12cc3a0f268587225ca3d0178fa90d2d79e82ad)

- **作者**: wangyu
- **时间**: 2026-11-11T07:17:41Z
- **提交信息**: [CI/Build] Share one MiniMax-H3 DP2 DLO server for FL2VA and Ref2VA (#10063)

Signed-off-by: wangyu <53896905+yenuo26@users.noreply.github.com>
Co-authored-by: wangyu <yenuo26@users.noreply.github.com>

### [2cbf670](https://github.com/vllm-project/vllm-omni/commit/2cbf670761c55d6de0e000728d9c7eeec87f60e6)

- **作者**: lm10-arg
- **时间**: 2026-11-11T07:10:09Z
- **提交信息**: [CI/Build][ROCm] Add Covo-Audio weekly coverage (#10160)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [c826ea4](https://github.com/vllm-project/vllm-omni/commit/c826ea4be3e2f285385c1b2faee68ef4a48b6dc2)

- **作者**: lm10-arg
- **时间**: 2026-11-11T06:59:58Z
- **提交信息**: [Bugfix][ROCm] Fix Audex TTA startup metadata (#10154)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [2b93e29](https://github.com/vllm-project/vllm-omni/commit/2b93e29e708e9ae11253a8d58b2d2e923234e821)

- **作者**: lm10-arg
- **时间**: 2026-11-11T05:13:23Z
- **提交信息**: [CI/Build][ROCm] Expand AMD weekly reliability coverage (#10148)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [6d003ce](https://github.com/vllm-project/vllm-omni/commit/6d003ce41f86d18a6a0b4d1fa5a62ddcae3d31d8)

- **作者**: wuli666
- **时间**: 2026-11-11T05:10:30Z
- **提交信息**: [Model] LFM3: CUDA support and LFM3-Audio-2B (#9968)

Signed-off-by: wuli666 <421774554@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [9227fb6](https://github.com/vllm-project/vllm-omni/commit/9227fb6e7ff73b08acd19aef979401268adc19eb)

- **作者**: psv666
- **时间**: 2026-11-11T04:42:46Z
- **提交信息**: [CI/Build] Keep Qwen3-Omni nightly evaluations for shared runtime changes (#10036)

Signed-off-by: psv666 <150513104+psv666@users.noreply.github.com>

### [64951bd](https://github.com/vllm-project/vllm-omni/commit/64951bd05cf15935c2c4e997c81c0de6619b3f1a)

- **作者**: amy-why-3459
- **时间**: 2026-11-11T03:46:30Z
- **提交信息**: [Bugfix] Initialize HunyuanVideo attention test biases (#10147)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [08f03e9](https://github.com/vllm-project/vllm-omni/commit/08f03e9e7fd4eb3d3cf416b51b62634bb7dbcac6)

- **作者**: lm10-arg
- **时间**: 2026-11-11T03:39:53Z
- **提交信息**: [CI/Build][ROCm] Target AMD nightly PRs to changed jobs (#10140)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [290b69b](https://github.com/vllm-project/vllm-omni/commit/290b69bab4a6da6f6b10d57d922d3da0c4b5c5a8)

- **作者**: Chendi.Xue
- **时间**: 2026-11-11T03:28:32Z
- **提交信息**: [Perf][Diffusion] CFG batching: run both CFG branches as one denoiser call on one CFG rank (#9797)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>

### [3f37f0b](https://github.com/vllm-project/vllm-omni/commit/3f37f0b1e0167b107641bb2f9a9425d2295c3aae)

- **作者**: lm10-arg
- **时间**: 2026-11-11T03:01:01Z
- **提交信息**: [CI/Build][ROCm] Guard AMD weekly reliability evidence (#10127)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [c792d3a](https://github.com/vllm-project/vllm-omni/commit/c792d3aef476876f3d7af93f3f95d37b469d11ad)

- **作者**: Chendi.Xue
- **时间**: 2026-11-11T02:02:16Z
- **提交信息**: [Feature][Diffusion] Generic Hugging Face text-encoder TP; enable for Qwen-Image and Qwen-Image-2.1 (#9438)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [51abdc9](https://github.com/vllm-project/vllm-omni/commit/51abdc9bb3605758e208374901d89c61ba0c743b)

- **作者**: Chendi.Xue
- **时间**: 2026-11-11T02:02:02Z
- **提交信息**: [Model][Qwen-Image] Shard AdaLN modulation projections under TP (#9440)

Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [5f08570](https://github.com/vllm-project/vllm-omni/commit/5f08570af9af6ec0064c93fbfd2306eaa56c2cd0)

- **作者**: hac17
- **时间**: 2026-11-11T01:13:46Z
- **提交信息**: [CI/Build] Promote six AMD NIGHTLY jobs to blocking (#10125)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

### [9f95053](https://github.com/vllm-project/vllm-omni/commit/9f95053f95b65d072b37a8bbaea9ff8551266e9a)

- **作者**: Qing7364
- **时间**: 2026-11-11T00:53:56Z
- **提交信息**: [Core] Add duplex L1 context ledger and stage views (#9441)

Signed-off-by: qingpeng <vera.xpq@gmail.com>
Signed-off-by: qingpeng <qing.peng@zoom.us>
Co-authored-by: qingpeng <qing.peng@zoom.us>

### [0eb5d5b](https://github.com/vllm-project/vllm-omni/commit/0eb5d5bb63898ea5fea129c5af1421dbfc90befd)

- **作者**: Iryna Boiko
- **时间**: 2026-11-11T00:21:44Z
- **提交信息**: [XPU][Feature][Diffusion] Device graph capture and replay for denoise steps (#9306)

Signed-off-by: Iryna Boiko <iboiko@habana.ai>

---
