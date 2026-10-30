# GitHub Stars 合并报告 - 2026-10-29

**合并日期**: 2026-10-30
**监控日期**: 2026-10-29
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


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2267
- **最后更新**: 2026-10-29T10:00:07Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 1
- **主要提交者**: YLlllllllllll

## AI分析总结

## 1. 主要更新类型

这两条提交均属于**测试补强/质量保障**类更新，而非功能新增或Bug修复：
- 第1条为模型测试更新（model + test）
- 第2条为算子测试更新（ops + test）

## 2. 关键变更点及与项目方向的关系

**[089e360] 保留Qwen4-Exp dummy vision attention契约**：
- 针对Qwen4实验模型，确保在dummy vision attention场景下的接口契约保持不变
- 与VeOmni"任意模态模型训练"的方向直接相关——多模态模型中视觉注意力模块的接口稳定性，是支持灵活组合不同视觉/语言骨干的前提

**[694edaa] 覆盖chunk CE与激活卸载+checkpointing组合**：
- 为chunk-wise交叉熵（cross-entropy）算子补充测试，覆盖其与激活卸载（activation offload）和梯度检查点（checkpointing）配合使用的场景
- 与VeOmni"分布式训练配方"的核心方向高度契合——激活卸载和checkpointing正是大规模分布式训练中节省显存的关键技术，确保chunk CE算子在这些场景下正确工作，对训练稳定性和正确性至关重要

**Co-authored-by: Cursor** 表明部分工作由AI编程助手辅助完成，反映了团队在开发流程中引入AI工具的趋势。

## 3. 对项目的影响和潜在意义

- **提升训练正确性保障**：多模态混合训练涉及大量算子组合（chunk CE + offload + checkpoint），测试覆盖不足容易引入静默错误。这次补测降低了分布式训练中因算子交互导致精度异常或崩溃的风险
- **保护接口稳定性**：Qwen4-Exp的attention契约测试可防止后续重构无意间破坏实验模型的兼容性
- **为规模扩展铺路**：VeOmni主打"scaling"，而scaling的前提是低层算子在各种显存优化策略下行为正确，这两项测试直接服务于这一目标

## 4. 值得关注的技术点

- **Chunk-wise CE**：将交叉熵按chunk计算，用于支持超大词表或长序列下的显存优化，其与offload/checkpoint的兼容性是实现长上下文多模态训练的关键细节
- **激活卸载与checkpointing的组合测试**：这两种技术单独使用常见，但组合使用时梯度重计算与显存交换的时序容易出错，针对性测试体现了工程成熟度
- **Qwen4-Exp**：暗示项目正在跟踪/集成最新的Qwen系列实验模型，保持对前沿模型架构的适配能力

## 5. 对项目整体发展的影响

VeOmni的目标是构建"以模型为中心的分布式训练配方库"，支持任意模态、任意规模的模型训练。本次提交虽然只是测试层面的更新，但覆盖的正是项目核心价值链条上的薄弱环节：

1. **多模态正确性**：vision attention契约测试保障了模态扩展时的接口可靠性
2. **分布式训练稳定性**：chunk CE与显存优化技术的组合测试，确保大规模训练配方在极端显存约束下的正确性
3. **可持续演进**：严格的契约测试让项目可以放心地进行后续重构和模型扩展

这类"看不见的基础设施"更新，往往是项目从研究原型走向生产级训练系统的关键标志，与README中宣称的Scaling Any Modality Model Training愿景是一致的务实推进。

## 详细提交记录

### [089e360](https://github.com/ByteDance-Seed/VeOmni/commit/089e3605ddd4d9968b3488ab0aae0f842a4321d3)

- **作者**: YLlllllllllll
- **时间**: 2026-10-29T10:00:01Z
- **提交信息**: [model] test: preserve Qwen4-Exp dummy vision attention contract (#1331)

### [694edaa](https://github.com/ByteDance-Seed/VeOmni/commit/694edaa3ca36b8b137dc53fc2f39de89739d5322)

- **作者**: YLlllllllllll
- **时间**: 2026-10-29T08:19:23Z
- **提交信息**: [ops] test: cover chunk CE with activation offload and checkpointing (#1004)

Co-authored-by: Cursor <cursoragent@cursor.com>

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2972
- **最后更新**: 2026-10-29T19:21:12Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: Bilang ZHANG, Watebear, Yang Yong (雍洋)

## AI分析总结

# LightX2V 昨日提交分析（第 1/1 批，共 6 条）

## 1. 主要更新类型
- **功能新增**：LoRA 提取与重构工作流（支持 Qwen-Image、Wan）、Hopper FP8 GEMM、RelayVSR 2x 支持。
- **性能优化**：Text Encoder 的 pin memory 优化、Hopper 硬件 GEMM 与 QKV cache 融合更新。
- **文档更新**：RelayVSR README 更新，LoRA 提取/合并的中英文指南与示例配置。
- **清理重构**：移除过时示例，LoRA 提取器升级为配置驱动。

## 2. 关键变更点与项目方向的关系
本次提交集中在三条主线，均紧扣 LightX2V "轻量视频生成推理" 的核心定位：
- **推理性能挖掘**：pin memory 减少主机到显存的数据搬运开销；Hopper FP8-FP32 GEMM 与 fused QKV cache 针对 H800/H100 等 Hopper 架构做底层算子级优化，直接提升吞吐并降低显存峰值，是"轻量"目标的硬件落地。
- **模型生态扩展**：Qwen-Image 2.1 校准、学生模型导出与 Wan 支持，使框架从单一视频模型向多模态（图像+视频）推理平台演进。
- **训练-推理闭环**：LoRA 提取、秩/alpha 缩放合并、重构方法与 lightx2v_train 模型对接，让用户能将训练产物无缝转为轻量推理，形成训练到部署的完整链路。
- **RelayVSR 增强**：2x 超分能力扩展了视频生成后处理环节的工具链。

## 3. 对项目的影响和潜在意义
- 短期看，硬件算子优化与内存策略可直接带来可量化的推理加速，强化项目在推理框架竞争中的性能口碑。
- 中期看，多模型（Qwen-Image/Wan）与 LoRA 工作流降低了用户定制门槛，有利于社区贡献与模型生态繁荣。
- 长期看，训练-推理打通使 LightX2V 不再只是"推理壳"，而逐步成为覆盖微调导出到高效部署的一站式轻量平台，提升用户粘性与项目护城河。

## 4. 值得关注的技术点
- **Hopper FP8-FP32 GEMM 与 fused QKV cache 更新**：展示项目对新硬件低精度计算与注意力缓存融合的深度优化能力，是评估其性能上限的关键。
- **LoRA 合并的 rank/alpha 缩放与多 key 格式适配**：细节决定合并正确性，需关注不同底模下的数值一致性。
- **pin memory 在 Text Encoder 上的应用**：编码阶段常成瓶颈，此项优化对长文本或多并发场景收益明显。
- **学生模型导出与校准流程**：涉及量化/蒸馏精度控制，影响最终生成质量，需在实际数据集上验证。

## 5. 结合项目背景的发展影响
README 表明 LightX2V 定位为"轻量视频生成推理框架"，本次提交正是这一愿景的多层次推进：硬件层（Hopper FP8）、内存层（pin memory）、算子层（fused QKV）的优化夯实了"轻量高效"的技术底座；模型层（Qwen-Image、Wan、RelayVSR 2x）与工具层（LoRA 提取/合并/重构）的扩展则拓宽了适用边界与用户场景；文档与示例的同步完善保证了新能力的可及性。整体而言，这批提交使项目在保持推理性能优势的同时，向多模型、可定制、训练推理一体化的方向稳步演进，进一步巩固其在轻量生成推理领域的差异化定位，并为后续更多底模适配和硬件平台扩展打下坚实基础。

## 详细提交记录

### [880b7b1](https://github.com/ModelTC/LightX2V/commit/880b7b156a4eb3ae8af8979a8d44b5e5945e17d2)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-29T15:32:22Z
- **提交信息**: update relayvsr readme (#1661)

### [c251da4](https://github.com/ModelTC/LightX2V/commit/c251da430b33f51af8bacac98f9a6fa20fa3ca1c)

- **作者**: Watebear
- **时间**: 2026-10-29T13:11:56Z
- **提交信息**: feat: support Text encoder  pin memory  (#1655)

### [a04447e](https://github.com/ModelTC/LightX2V/commit/a04447e5d89d08597847d011acb5d3271cd757e6)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-29T11:19:08Z
- **提交信息**: remove example (#1660)

### [4fa9645](https://github.com/ModelTC/LightX2V/commit/4fa9645a4fec3aa7e26d63395b6f4ac72c5638e7)

- **作者**: Zhuguanyu Wu
- **时间**: 2026-10-29T11:11:47Z
- **提交信息**: update lora extractor (#1659)

- support qwenimage and wan
- support models from lightx2v_train
- support reconstruction methods

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added configuration-based LoRA extraction with selectable layers,
rank, alpha, and output dtype.
* Added Qwen-Image 2.1 calibration and LoRA reconstruction workflows,
plus student-checkpoint export.
* LoRA merging now applies adapter alpha/rank scaling and supports
additional model key formats.
* **Documentation**
* Added English and Chinese guides for extraction, reconstruction,
checkpoint export, and updated merger options.
  * Added example configurations for Wan and Qwen-Image 2.1.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8ef2821](https://github.com/ModelTC/LightX2V/commit/8ef282137f46bb5cd694d2e0270c9cf21b98fa9d)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-29T10:18:24Z
- **提交信息**: support relayvsr 2x (#1658)

### [d08f0c0](https://github.com/ModelTC/LightX2V/commit/d08f0c013d502bfcaf874af539e5c8f8d987e6fb)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-29T08:22:55Z
- **提交信息**: feat(h3_causal): add Hopper FP8-FP32 GEMM and fused QKV cache updates (#1657)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2318
- **最后更新**: 2026-10-28T11:56:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6817
- **最后更新**: 2026-10-30T01:40:37Z

## 提交统计

- **昨日提交总数**: 72
- **提交者数量**: 15
- **主要提交者**: Yang Xu, Yanqin Zhai, Netanel Haber

## AI分析总结

# FlashInfer 近期提交综合分析

## 主要更新
昨日 72 个提交以性能优化为绝对主体（约六成），辅以功能新增、正确性修复与基准改进。核心动向有四条：其一，**稀疏注意力（SDSA）落地**，单头索引器 + MQA 核心的 token-sparse 注意力通过 group-union mask（相邻 token 的 Top-K key 取并集并按组映射为 varlen 条目）让稠密内核承载稀疏语义；其二，**训练路径大幅扩展**，Cake mHC/KDA/KCP 训练、MoE 训练、GEMM dgrad、LM head loss 等表明项目正从纯推理内核库走向推理与训练并重；其三，**Blackwell/Rubin 全系精调**，按 GB200、GB300、B200、RTX PRO 6000/5090（SM120）乃至 Rubin 区分工作单元顺序、CTA 路由与重叠上界；其四，**多后端智能路由**，Cake、CuTe、cuDNN 并存，按形状、精度、硬件自动选择更快实现。

## 关键变更
核心策略是"不动 kernel 本体、只调宿主侧调度"，全程保证输出与梯度 bitwise 一致。优化覆盖注意力（FMHA、KDA、GDN、paged）、GEMM 与量化、归一化、采样、卷积及 MoE 路由：MXFP8 权重融合单发射量化器耗时从约 51ms 降至 1.5ms，整层训练最高提速 2.67 倍；小 token 场景 dense GEMM 路由八 warp CTA 最高提速 1.74 倍；Ulysses all-to-all 引入向量化与 144-CTA NVLink 路径（1.45–1.73 倍）；Kimi-K3 融合 MoE router（896 专家、top-16）在 B200/GB300 上提速至 1.10 倍；专为 sm_107a 设计的 PACKED_M64_N8 tile kernel 扩展至 sm_100a/sm_103a，并新增无偏置 GEMM 路由窗口。调度上从持久 CTA 转向 Cluster Launch Control/PDL 动态调度，L2 预取、TMEM 复用、evict_last 等针对 Blackwell 存储层次精细调优。

修复项包括：`cake_lm_head_loss` 预算模式内存规划器漏算缓冲区（峰值超标约 1.97 倍）、split-K GEMM 三处 mbarrier/tcgen05 同步缺陷、GDN softplus 批次 16 起 100% NaN、MSA Ops 精度偏差、FP4 权重解码缺陷、MoE 无效路由污染、CUDA 12.9/13.0 非法指令故障，以及 ReplaySSM `flat_slot` Int32 溢出导致的非法地址访问（SGLang tp=4 首次 commit 即崩溃）。新增功能含 SDSA token-sparse MQA 解码、MegaMoE TP/EP 路由、mHC 训练 head 与 Hopper 变长稀疏注意力新程序。

## 项目影响
各项 1%–1.7 倍微优化叠加后端到端收益可观，多数包取得 1.02–1.35 倍几何均值加速；内存修复与 EP tile 修复直接消除长上下文训练 OOM 与专家并行部署风险；Recompute handle 让 checkpoint 反向重算免去两次集合通信，并统一至 conv、GDN、KDA。Windows on ARM 构建修复与 KCP 参考实现内迁（691 个测试免外部依赖）扩大硬件与贡献者覆盖。覆盖 Kimi Delta Attention、Kimi-K3 LatentMoE、MiniMax-H3、DeepSeek 系列等新兴架构，统一支撑 Hopper 到 Rubin 全硬件线，为下游 SGLang、vLLM 的生产部署提供可靠基础。

## 技术关注点
- **硬件感知调度**：按 SM 数量与 shape 定制程序路由、工作单元顺序，单包程序数已达 82–127 个，内核库演化为"多程序 + 智能选择"专家系统。
- **PTX 同步陷阱**：mbarrier parity 语义需显式等待 phase 0 才能避免 TMEM 提前释放。
- **微架构权衡**：寄存器数、指令数、占用率精确取舍，含因收益为负而回退的诚实决策；softmax 为达 1e-6 精度接受约 4% 回退。
- **重叠与预取**：通信-计算重叠、z 预取、环绕计划等多组 Rubin 程序扩展。
- **验证方法论**：A/A 噪声带、位级验收、32 观测 × 多 tactic 诊断矩阵、边界二分测试，方法论严谨；但需警惕程序膨胀带来的维护成本与 cost model 复杂度上升。

## 总体判断
FlashInfer 正沿**稀疏化、硬件广度、训练延伸、生产级稳健性**四条主线演进，从"高效 attention 库"演进为覆盖全模型栈、全硬件线的推理与训练基座，通过严谨的 bitwise 验证与逐 shape 基准文化持续巩固其跨架构、跨精度统一高性能 GPU 内核平台的底层壁垒。

## 详细提交记录

### [0d5bbf5](https://github.com/flashinfer-ai/flashinfer/commit/0d5bbf50b3fb3695dd2a4cf9feddabd2ab172412)

- **作者**: eigen
- **时间**: 2026-10-29T23:40:57Z
- **提交信息**: fix(cake_lm_head_loss): with grad, budget planner models every live buffer and the allocator's block rounding (#7909)

Follow-up to #7865 for #7545. The opt-in budget mode
(`memory_mode="budget"`) is meant to keep the step peak at or below B,
which is the bytes of a head that materializes the logits of the valid
rows. Its planner left three buffers out of its count: the copy of X,
the dx cast, and allocator block rounding. With `compact_rows=False` it
also sized the budget by all rows instead of the valid rows. As a
result, some calls it planned as fitting went over B, by up to 1.97061
B. The planner now counts those buffers and budgets an uncompacted call
by its valid rows. Calls it plans as fitting now stay at or below B. The
default path and every kernel are unchanged, since the diff only touches
the opt-in planner, the README and the tests. Default-path speed is
therefore unchanged, and outputs match both main and the default path on
every measured row. Two budget-mode behaviors are new. Without
`num_valid_rows`, an uncompacted loss forward and an uncompacted
log-probability backward now count valid rows on the host, so they wait
for GPU work queued ahead of them. Passing `num_valid_rows` avoids that
wait. At the #7545 issue shapes the budget step stays within the
targets:
- H6144/T16384 peaks at 4.9906 GiB on GB200 and GB300 and at 5.0199 GiB
on B200. The highest peak over repeated steps is 5.0248 GiB, against a
target of 5.04 GiB.
- H4096/T16384 stays at or below 3.8880 GiB, against a target of 4.41
GiB.

| Case (H, V, T, chunk; entry; rows) | X | B | main peak (× B) | fix
peak (× B) | fix plans a fit |
|---|---|---|---|---|---|
| H512 V2048 T2048 c512; CE loss; all valid | contig | 12.00 MiB | 12.08
MiB (1.0068) | 9.06 MiB (0.7550) | no |
| H512 V2048 T2048 c512; log-prob; all valid | pad1 | 12.00 MiB | 15.56
MiB (1.2967) | 14.05 MiB (1.1709) | no |
| H1024 V4096 T2048 c256; log-prob; all valid | pad1 | 28.00 MiB | 36.02
MiB (1.2866) | 22.67 MiB (0.8098) | yes |
| H1024 V4096 T4096 c1024; CE loss; all valid | contig | 48.00 MiB |
48.22 MiB (1.0045) | 42.18 MiB (0.8788) | yes |
| H1024 V4096 T4096 c1024; log-prob; 1/3 ignored, uncompacted | pad1 |
36.93 MiB | 62.18 MiB (1.6838) | 52.18 MiB (1.4130) | no |
| H512 V4096 T8192 c2048; log-prob; 1/3 ignored, `dx_finalize=False` |
contig | 54.49 MiB | 58.40 MiB (1.0717) | 46.88 MiB (0.8603) | yes |
| H512 V65536 T8192 c2048; log-prob; T_v = 1024 | contig | 200.00 MiB |
394.12 MiB (1.9706) | 189.58 MiB (0.9479) | yes |
| H1024 V151552 T16384 c4096; log-prob; T_v = 3000 | contig | 1195.19
MiB | 2097.38 MiB (1.7549) | 1164.94 MiB (0.9747) | yes |
| H4096 V154880 T16384 c4096; log-prob; 1/3 ignored, uncompacted | pad1
| 4595.19 MiB | 5435.13 MiB (1.1828) | 4225.13 MiB (0.9195) | yes |
| H6144 V154880 T16384 c4096; CE loss; 1/3 ignored, uncompacted | contig
| 5256.81 MiB | 5637.06 MiB (1.0723) | 5145.19 MiB (0.9788) | yes |
| H6144 V154880 T16384 c4096; policy loss; 1/3 ignored, uncompacted |
contig | 5292.85 MiB | 5638.06 MiB (1.0652) | 5182.19 MiB (0.9791) | yes
|
| H6144 V154880 T16384 c4096; log-prob; 1/3 ignored, uncompacted | pad1
| 5284.87 MiB | 5915.13 MiB (1.1193) | 5171.13 MiB (0.9785) | yes |
| Issue shape H6144 T16384; CE loss | – | 5.0961 GiB | 8.4672 GiB
(default step) | 4.9906 GiB (0.9793) | – |
| Issue shape H6144 T16384; policy loss | – | 5.0961 GiB | 8.4672 GiB
(default step) | 4.9896 GiB (0.9791) | – |
| Issue shape H6144 T16384; log-prob | – | 5.0961 GiB | 7.2834 GiB
(default step) | 4.9896 GiB (0.9791) | – |
| Issue shape H4096 T16384; CE loss | – | 4.4543 GiB | 6.3827 GiB
(default step) | 3.8864 GiB (0.8725) | – |
| Issue shape H4096 T16384; log-prob | – | 4.4543 GiB | 5.1933 GiB
(default step) | 3.8865 GiB (0.8725) | – |

*Measured on GB200 (sm_100a) with PyTorch 2.14.1+cu130 and nvcc 13.4.92.
GB300 (sm_103a, CUDA 13.4) gave identical values for every row shown.
B200 (sm_100a, CUDA 13.4) gave identical values for the smaller shapes.
On the H4096 and H6144 rows its B and some peaks differ slightly because
T_v differs.*

*How the numbers are defined:*
- *Step peak is `torch.cuda.max_memory_allocated` above the pre-step
bytes, from forward through backward with outputs included. It is the
larger of the first call and the measured call.*
- *B = 2·T_v·V + 2·V·H + 2·T·H bytes.*
- *X is either contiguous (contig) or padded (pad1).*
- *For the upper rows, main is main's budget-mode step. For the issue
shapes, main is main's default step and T_v = 10871 (H6144) or 10911
(H4096).*

*Main planned a fit but went over B on 50 of 198 rows per GPU. The fix
plans 24 of those 50 as fitting, with a maximum of 0.97909 B. It reports
the other 26 as not fitting. 13 of those 26 still exceed B, all with a
lower peak than on main. Across all 198 rows, the fix plans 143 as
fitting and none of them exceeds B. The maximum is 0.97926 B on GB200
and GB300 and 0.97940 B on B200.*

These numbers cover the kernel's BF16 path in all three entry forms (CE
loss, policy loss and log-probability), on sm_100a (GB200, B200) and
sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Memory-budget planning now accounts for valid rows, input copies, and
additional memory used during processing, providing more representative
peak-memory estimates.
* If no plan fits the requested budget, the planner selects the option
with the lowest predicted peak; actual usage may still exceed the
budget.
* **Documentation**
* Clarified how valid-row counts affect budget estimates and documented
the allocator and backward-pass assumptions.
* Updated reported peak-memory measurements across GB200, GB300, and
B200 systems.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7cbc5a7](https://github.com/flashinfer-ai/flashinfer/commit/7cbc5a78742ed85c9150a7dc0f88646749d4ad77)

- **作者**: eigen
- **时间**: 2026-10-29T23:17:32Z
- **提交信息**: perf(cake_nvfp4_mla_decode): reverse the per-unit piece order of long-row decode plans on GB300 (#7907)

This PR speeds up `cake_nvfp4_mla_decode`
(`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla`,
experimental), the MLA decode with NVFP4 queries and KV cache, over its
previous Cake version in `main`. The kernel has one variant (one data
type, one layout, no fused forms), and this PR changes that variant. On
GB300 (sm_103a, 152 SMs), long-row decode plans now run each work unit's
pieces in reverse order, as `main` does on GB200. The device programs
and the B200, GB200 and 148-SM sm_103a plans are unchanged. Each latency
is the median over two GPUs of the median CUDA graph replay time with a
cold L2, and each speedup is the median over the same two GPUs of each
GPU's paired ratio of the `main` time to this PR's time, so it can
differ slightly from the quotient of the two latency columns.

On GB300 at batch 32 with 64 heads and 6 query tokens, the measured
speedups are 1.008x at 8K keys each, 1.019x at 16K, 1.028x at 32K,
1.030x at 64K and 1.027x at 128K.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| batch 32, 8K keys each, 64 heads, 6 query tokens | 82.46 | 81.81 |
1.008x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 143.43 | 140.78 |
1.019x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 262.29 | 255.07 |
1.028x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 495.53 | 481.12 |
1.030x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 957.94 | 933.16 |
1.027x |

Cake has no other variants of this decode (no other data type, layout or
fused form), and the kernel covers sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Balanced long-decode plans now support reversed piece ordering on
152-SM SM103 devices, alongside existing support on SM100 devices. Plans
for 148-SM devices continue to use request-major ordering.
* This keeps piece ordering aligned with the selected device
configuration and decode plan.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [627daca](https://github.com/flashinfer-ai/flashinfer/commit/627daca2d8dbf697ac5b83a3caf3709c1243dd11)

- **作者**: eigen
- **时间**: 2026-10-29T23:17:11Z
- **提交信息**: perf(cake_minimax_h3): head-major pre-processing for long sequential SM120 FP8 varlen plans (#7906)

The MiniMax-H3 non-causal packed-varlen attention kernel runs on
sm_120a. FlashInfer has four Cake variants of it: three NVFP4-QK forms
and one FP8 form. This PR changes the FP8 form,
`minimax_h3_sm120_varlen_attention_fp8`. The change is host-side only.
The kernel programs do not change. Today, long sequential plans run
their pre-processing as two launches. The first launch computes K/V
statistics, and the second one quantizes. This PR runs the
pre-processing as one launch of the existing head-major pre-processing
program. That program computes statistics and quantizes per head, so the
second read of K and V hits L2. The attention program and the overlapped
form do not change. The single launch applies to sequential plans with
at most 65536 tokens on the RTX 5090 (170 SMs). On the RTX PRO 6000 (188
SMs), the limit is 98304 tokens. Longer plans keep the two launches.
Outputs are bitwise equal to FlashInfer main. The baseline is the
previous Cake version of the same op, which is FlashInfer main.
FlashInfer main already contains the lazy output rescale PR. Latency is
the median GPU time per call of the whole op, with cold L2. Each table
cell is the mean over two GPUs. Speedup = FlashInfer main / this PR.

The gains are modest, at most 1.6 %. Each GPU runs 25 representative
shapes. On the RTX PRO 6000, 10 shapes are faster, by 1.003x to 1.016x.
For example, center_4s runs at 1.010x and x3_l26000 at 1.016x. There, 6
shapes are within noise and 9 are unchanged. On the RTX 5090, 6 shapes
are faster, by 1.003x to 1.012x. For example, center_4s runs at 1.005x
and x3_l26000 at 1.012x. There, 9 shapes are within noise and 10 are
unchanged. Rows marked "(within noise)" are not claimed as speedups. m1
on the RTX PRO 6000 (0.983x) is within run-to-run noise. seg_133_300_900
on the RTX 5090 (0.985x) is also within run-to-run noise. Both launch
exactly the programs of FlashInfer main. Rows marked "(unchanged)"
launch the same programs as FlashInfer main.

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | FI main (us) | this PR (us) | speedup |
|---|---|---|---|---|
| center_4s | 33472 | 46218.90 | 45756.79 | 1.010x |
| center_5s | 38592 | 61000.48 | 60469.16 | 1.009x |
| center_6s | 48768 | 96953.49 | 96506.54 | 1.005x |
| center_8s | 58944 | 141319.97 | 140612.89 | 1.005x |
| center_10s | 74240 | 222350.70 | 221650.09 | 1.003x |
| center_15s | 109952 | 484991.65 | 485062.82 | 1.000x (unchanged) |
| tail_5s_a | 38531 | 61023.79 | 60460.21 | 1.009x |
| tail_5s_b | 38629 | 61015.73 | 60473.20 | 1.009x |
| pad_15s | 109952 | 484783.92 | 484904.69 | 1.000x (unchanged) |
| seg4 | 33472 | 12297.36 | 12291.80 | 1.000x (unchanged) |
| seg3_ragged | 4824 | 955.61 | 955.34 | 1.000x (unchanged) |
| seg_empty | 500 | 59.02 | 58.98 | 1.001x (within noise) |
| single_4096 | 4096 | 827.75 | 827.59 | 1.000x (unchanged) |
| m1 | 1 | 16.38 | 16.66 | 0.983x (within noise) |
| m128 | 128 | 26.56 | 26.48 | 1.003x (unchanged) |
| m129 | 129 | 30.29 | 30.44 | 0.995x (unchanged) |
| seg_133_300_900 | 900 | 103.64 | 103.62 | 1.000x (unchanged) |
| s6144 | 6144 | 1671.70 | 1671.89 | 1.000x (within noise) |
| x3_l26000 | 26000 | 28192.17 | 27754.43 | 1.016x |
| x3_l2x25000 | 50000 | 52419.06 | 51797.71 | 1.012x |
| x3_lrag3 | 53000 | 73434.93 | 72801.18 | 1.009x (within noise) |
| x3_l52000p | 52000 | 109695.05 | 109102.71 | 1.005x |
| x3_s1500 | 1500 | 210.59 | 210.36 | 1.001x (within noise) |
| x3_s3x900 | 2700 | 340.33 | 339.76 | 1.002x (unchanged) |
| s2048 | 2048 | 314.52 | 313.69 | 1.003x (within noise) |

### NVIDIA GeForce RTX 5090 (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | FI main (us) | this PR (us) | speedup |
|---|---|---|---|---|
| center_4s | 33472 | 52397.64 | 52120.58 | 1.005x |
| center_5s | 38592 | 69658.52 | 69385.47 | 1.004x |
| center_6s | 48768 | 110781.08 | 110499.79 | 1.003x (within noise) |
| center_8s | 58944 | 162047.45 | 161826.68 | 1.001x (within noise) |
| center_10s | 74240 | 253313.27 | 253431.09 | 1.000x (unchanged) |
| center_15s | 109952 | 553361.73 | 553747.30 | 0.999x (unchanged) |
| tail_5s_a | 38531 | 69671.94 | 69348.50 | 1.005x |
| tail_5s_b | 38629 | 69213.16 | 68849.08 | 1.005x |
| pad_15s | 109952 | 553227.41 | 553574.00 | 0.999x (unchanged) |
| seg4 | 33472 | 13942.44 | 13952.30 | 0.999x (unchanged) |
| seg3_ragged | 4824 | 1002.10 | 1003.62 | 0.998x (unchanged) |
| seg_empty | 500 | 43.57 | 43.44 | 1.003x (unchanged) |
| single_4096 | 4096 | 865.33 | 866.00 | 0.999x (unchanged) |
| m1 | 1 | 14.68 | 14.61 | 1.005x (unchanged) |
| m128 | 128 | 21.48 | 21.59 | 0.995x (unchanged) |
| m129 | 129 | 25.09 | 24.73 | 1.014x (within noise) |
| seg_133_300_900 | 900 | 86.01 | 87.31 | 0.985x (within noise) |
| s6144 | 6144 | 1796.81 | 1794.34 | 1.001x (unchanged) |
| x3_l26000 | 26000 | 31877.39 | 31504.78 | 1.012x |
| x3_l2x25000 | 50000 | 59606.69 | 59219.49 | 1.007x (within noise) |
| x3_lrag3 | 53000 | 83714.77 | 83427.90 | 1.003x |
| x3_l52000p | 52000 | 125532.54 | 125280.40 | 1.002x (within noise) |
| x3_s1500 | 1500 | 195.18 | 194.16 | 1.005x (within noise) |
| x3_s3x900 | 2700 | 326.61 | 324.64 | 1.006x (within noise) |
| s2048 | 2048 | 333.01 | 331.74 | 1.004x (within noise) |

This SM120 family ships for sm_120a only, and its other Cake variants
are `minimax_h3_sm120_varlen_attention_nvfp4` (SageAttention3 FP4
recipe, compensated), `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`
(uncompensated) and the NVFP4-QK / FP8-PV form selected by
`pv_mode="fp8"` on the NVFP4 entry, while the same MiniMax-H3
packed-varlen attention op also ships for sm_100a (B200) and sm_103a
(GB300) as `minimax_h3_varlen_attention`, in BF16 and two NVFP4 forms
(`pv_mode="fp4"` and `pv_mode="fp8"`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added a sequential processing path for eligible 56-head workloads on
supported hardware, including workloads above the previous overlap
range.
* The path applies to workloads of up to 65,536 tokens on 170-SM devices
and 98,304 tokens on 188-SM devices. Other workloads continue to use
their existing processing paths.
* **Tests**
* Added coverage for eligible workloads, token limits, unsupported
configurations, and output consistency.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0ec193b](https://github.com/flashinfer-ai/flashinfer/commit/0ec193b8a30d29ab3a99b42f53bf4a3930256521)

- **作者**: eigen
- **时间**: 2026-10-29T23:16:53Z
- **提交信息**: perf(cake_minimax_h3): WS-IL lead and tail and a 53248-token overlap bound for uncompensated SM120 NVFP4 varlen attention on 188-SM parts (#7904)

This PR changes the MiniMax-H3 non-causal packed-varlen NVFP4 attention
kernel on sm_120a. The kernel has two NVFP4 forms. The default form is
`minimax_h3_sm120_varlen_attention_nvfp4`, which is compensated. The
second form is `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, which
is uncompensated. This PR changes only the uncompensated form, and only
on 188-SM parts. These are the RTX PRO 6000 Blackwell Server Edition.
Launches on the RTX 5090 (170 SMs) do not change. The default form does
not change either. Let m be the attention-weighted mean segment length
of a plan. It is m = sum of squared segment lengths / tokens. On 188
SMs, uncompensated overlapped plans with m >= 2560 now use a new build
of the ws-poll lead and tail programs. This build is interleaved and
warp-specialized (WS-IL). Plans below 2560 keep the programs of
FlashInfer main. For long uncompensated plans, the bound of the
overlapped form also rises. It goes from a mean segment of 40960 tokens
to 53248 tokens, with WS-IL. Plans with 40960 < m <= 53248 now overlap
instead of running separate launches. The PR adds the two WS-IL program
units. It renames the two existing ws-poll lead and tail units, whose
text is identical up to the symbol. It also updates the host routing and
the tests. In every timed configuration, outputs are bitwise equal to
FlashInfer main. The baseline is the previous Cake version of the same
op, which is FlashInfer main. FlashInfer main already contains the
plan-dependent overlap width PR. Latency is the median GPU time per call
of the whole op, with cold L2. Each table cell is the mean over two
GPUs. Speedup = FlashInfer main / this PR.

The gains are small, at most 0.6 %. In the uncompensated form, 36 plans
change their launch. Of these, 17 run faster on both GPUs, by
1.001x-1.006x. The other 19 are within run-to-run noise on at least one
GPU. The table marks them "(within noise)", and we do not claim a
speedup for them. The representative table has 13 shapes in both forms.
In the default form, all 13 launch the same programs as on FlashInfer
main. The table marks them "(unchanged)" and shows their times to
confirm this. In the uncompensated form, 8 shapes run faster, by
1.002x-1.005x. One shape, cu_seqlens (0, 257, 4567, 4824), is within
noise. The other 4 launch unchanged.

**Representative shapes, NVIDIA RTX PRO 6000 Blackwell Server Edition
(sm_120a, 188 SMs), CUDA 13.4**

Latency per call in us (mean of two GPUs); speedup = FlashInfer main /
this PR.

| shape | cu_seqlens | default main us | default PR us | speedup |
nodelta main us | nodelta PR us | speedup |
|---|---|---|---|---|---|---|---|
| 33472 x 56 x 128 | (0, 33472) | 32465.61 | 32459.45 | 1.000x
(unchanged) | 30671.86 | 30558.92 | 1.004x |
| 38592 x 56 x 128 | (0, 38592) | 43529.78 | 43520.46 | 1.000x
(unchanged) | 40413.26 | 40249.31 | 1.004x |
| 48768 x 56 x 128 | (0, 48768) | 69222.93 | 69207.29 | 1.000x
(unchanged) | 63336.43 | 63184.18 | 1.002x |
| 58944 x 56 x 128 | (0, 58944) | 101215.30 | 101190.24 | 1.000x
(unchanged) | 91485.64 | 91575.92 | 0.999x (unchanged) |
| 74240 x 56 x 128 | (0, 74240) | 159606.18 | 159609.03 | 1.000x
(unchanged) | 144674.13 | 144540.62 | 1.001x (unchanged) |
| 109952 x 56 x 128 | (0, 109952) | 346899.82 | 346919.67 | 1.000x
(unchanged) | 314138.08 | 313988.49 | 1.000x (unchanged) |
| 38531 x 56 x 128 | (0, 38531) | 43586.53 | 43563.02 | 1.001x
(unchanged) | 40466.17 | 40282.05 | 1.005x |
| 38629 x 56 x 128 | (0, 38629) | 43610.52 | 43607.15 | 1.000x
(unchanged) | 40408.15 | 40223.88 | 1.005x |
| 109952 x 56 x 128 | (0, 109901, 109952) | 346951.58 | 346942.15 |
1.000x (unchanged) | 313940.10 | 313740.19 | 1.001x (unchanged) |
| 33472 x 56 x 128 | (0, 8368, 16736, 25104, 33472) | 9321.95 | 9321.56
| 1.000x (unchanged) | 8684.22 | 8647.23 | 1.004x |
| 4824 x 56 x 128 | (0, 257, 4567, 4824) | 729.77 | 729.66 | 1.000x
(unchanged) | 671.73 | 670.37 | 1.002x (within noise) |
| 500 x 56 x 128 | (0, 0, 129, 129, 500) | 49.29 | 49.23 | 1.001x
(unchanged) | 47.76 | 47.67 | 1.002x (unchanged) |
| 4096 x 56 x 128 | (0, 4096) | 633.73 | 633.49 | 1.000x (unchanged) |
584.24 | 582.60 | 1.003x |

**Uncompensated (nodelta) plans whose launch changes, NVIDIA RTX PRO
6000 Blackwell Server Edition (sm_120a, 188 SMs), CUDA 13.4**

Latency per call in us (mean of two GPUs); speedup = FlashInfer main /
this PR. m = sum(len^2) / tokens.

| plan | segment lengths | m | change | main us | PR us | speedup |
|---|---|---|---|---|---|---|
| t_7x2560 | 7 x 2560 | 2560 | WS-IL | 1693.26 | 1691.51 | 1.001x
(within noise) |
| t_s2560 | 2560 | 2560 | WS-IL | 307.01 | 306.59 | 1.001x (within
noise) |
| t_mix2571 | 3200, 2200, 2600, 1900 | 2571 | WS-IL | 982.18 | 980.65 |
1.002x (within noise) |
| t_lmix2571 | 3200, 2200, 2600, 1900, 3200, 2200, 2600, 1900 | 2571 |
WS-IL | 1949.58 | 1945.07 | 1.002x (within noise) |
| vl_rag2579 | 6000, 1000, 1000, 1000, 1000, 1000, 1000, 1000, ... |
2579 | WS-IL | 1901.19 | 1901.12 | 1.000x (within noise) |
| vl_20x2600 | 20 x 2600 | 2600 | WS-IL | 5641.16 | 5629.49 | 1.002x
(within noise) |
| t_3x2600 | 3 x 2600 | 2600 | WS-IL | 796.20 | 794.15 | 1.003x (within
noise) |
| t_9x2700 | 9 x 2700 | 2700 | WS-IL | 2607.47 | 2593.90 | 1.005x
(within noise) |
| vl_7x2700 | 7 x 2700 | 2700 | WS-IL | 1990.24 | 1990.82 | 1.000x
(within noise) |
| t_2x2800 | 2 x 2800 | 2800 | WS-IL | 603.57 | 601.95 | 1.003x (within
noise) |
| v_5x3000 | 5 x 3000 | 3000 | WS-IL | 1688.82 | 1687.99 | 1.000x
(within noise) |
| t_12x3000 | 12 x 3000 | 3000 | WS-IL | 4202.92 | 4198.14 | 1.001x |
| s3072 | 3072 | 3072 | WS-IL | 376.36 | 375.94 | 1.001x (within noise)
|
| t_rag3351 | 4500, 1200, 3100, 2000, 3600 | 3351 | WS-IL | 1735.05 |
1730.90 | 1.002x (within noise) |
| t_rag_l3461 | 5000, 800, 2600, 1900, 3400, 2200, 4100 | 3461 | WS-IL |
2491.57 | 2486.84 | 1.002x (within noise) |
| seg3_ragged | 257, 4310, 257 | 3878 | WS-IL | 671.73 | 670.37 | 1.002x
(within noise) |
| vl_5x3900 | 5 x 3900 | 3900 | WS-IL | 2657.39 | 2649.23 | 1.003x
(within noise) |
| single_4096 | 4096 | 4096 | WS-IL | 584.24 | 582.60 | 1.003x |
| s5120 | 5120 | 5120 | WS-IL | 840.69 | 837.45 | 1.004x |
| s6144 | 6144 | 6144 | WS-IL | 1167.41 | 1163.76 | 1.003x |
| s8192 | 8192 | 8192 | WS-IL | 1962.23 | 1960.37 | 1.001x (within
noise) |
| fused_max | 8000, 8384 | 8196 | WS-IL | 4096.97 | 4083.49 | 1.003x |
| seg4 | 4 x 8368 | 8368 | WS-IL | 8684.22 | 8647.23 | 1.004x |
| long_ragged | 5000, 0, 16000, 129 | 13300 | WS-IL | 8158.30 | 8128.93
| 1.004x |
| long_min | 16512 | 16512 | WS-IL | 7662.50 | 7632.31 | 1.004x |
| center_4s | 33472 | 33472 | WS-IL | 30671.86 | 30558.92 | 1.004x |
| tail_5s_a | 38531 | 38531 | WS-IL | 40466.17 | 40282.05 | 1.005x |
| center_5s | 38592 | 38592 | WS-IL | 40413.26 | 40249.31 | 1.004x |
| tail_5s_b | 38629 | 38629 | WS-IL | 40408.15 | 40223.88 | 1.005x |
| b_s44032 | 44032 | 44032 | overlap + WS-IL | 52486.76 | 52151.85 |
1.006x |
| x45056 | 45056 | 45056 | overlap + WS-IL | 54805.38 | 54582.40 |
1.004x (within noise) |
| center_6s | 48768 | 48768 | overlap + WS-IL | 63336.43 | 63184.18 |
1.002x |
| x2s49152 | 2 x 49152 | 49152 | overlap + WS-IL | 130601.83 | 130305.48
| 1.002x |
| b_2x50000 | 2 x 50000 | 50000 | overlap + WS-IL | 135434.95 |
135242.98 | 1.001x |
| b_s52224 | 52224 | 52224 | overlap + WS-IL | 73381.65 | 73272.69 |
1.001x |
| b_rag60000 | 10000, 60000 | 52857 | overlap + WS-IL | 99781.96 |
99683.11 | 1.001x (within noise) |

This SM120 family ships for sm_120a only, and its other Cake variants
are the NVFP4-QK / FP8-PV form (`pv_mode="fp8"` on the NVFP4 entry) and
the FP8 packed-varlen form `minimax_h3_sm120_varlen_attention_fp8`,
while the same MiniMax-H3 packed-varlen attention op also ships for
sm_100a (B200) and sm_103a (GB300) as `minimax_h3_varlen_attention`, in
BF16 and two NVFP4 forms (`pv_mode="fp4"` and `pv_mode="fp8"`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## New Features
- Added WS-IL lead/tail program variants for NVFP4 variable-length
attention.
- On 188-SM devices, uncompensated overlap now selects WS-IL variants
when the attention-weighted mean segment length is at least 2,560
tokens. The supported long-plan overlap limit increases to 53,248
tokens.

## Tests
- Expanded coverage for program selection, launch metadata, and overlap
limits.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [97beaeb](https://github.com/flashinfer-ai/flashinfer/commit/97beaeba99b4f6abd25ca37a3c9444f7cbe0eea1)

- **作者**: eigen
- **时间**: 2026-10-29T23:16:07Z
- **提交信息**: perf(cake_moe_finalize_allreduce_fusion): issue the residual and norm weight ahead of the one-shot poll (#7905)

`cake_moe_finalize_allreduce_fusion` fuses several steps at hidden size
7168: MoE finalize, the all-reduce across the ranks of one NVLink node,
the residual add and RMSNorm. MoE finalize uses the top-k expert rows
with routing scale, plus an optional shared-expert row. The kernel is
called through `flashinfer.comm.allreduce_fusion(...,
moe_finalize_backend="cake")`. It has 40 programs per architecture, and
this PR does not change that number. The programs come from 2 data types
(fp16, bf16) x 2 epilogues (BF16/FP16 output, packed NVFP4 output) x 10
program kinds. World size 2 has small-token, persistent and large-token
programs. World size 4 has small-token, persistent, two-shot and
deferred two-shot programs. World size 8 has small-token, two-shot and
deferred two-shot programs. This PR changes 16 programs: the small-token
programs at world sizes 2, 4 and 8 and the world-size-4 persistent
program, each for both data types and both epilogues. Before the
all-reduce poll, these programs now load a token's residual and its norm
weight as two packed 16-byte loads, and they unpack them after the poll.
Addresses, values and arithmetic stay the same. The other 24 programs
are unchanged. Dispatch changes in one place: at world size 4, two-shot
now starts at 72 tokens instead of 88, and it is still tested before the
small-token checks. So at world size 4, batches of 72-87 tokens move
from the one-shot programs to two-shot. With the default
`small_token_max` of 64, these batches ran the persistent program
before. Batches of 71 tokens or fewer still run one-shot. The other
thresholds are unchanged: two-shot from 56 tokens at world size 8, the
deferred form from 1536 tokens at world size 4 and 768 tokens at world
size 8 (with the world-size-8 top-k 4, no shared expert, BF16/FP16
output exception), the small-token extension (71) and the world-size-2
large-token thresholds (512 and 1280). No table shape falls in the moved
range (72-87 tokens at world size 4). No table shape runs the
world-size-4 persistent program either, because none has 17-71 tokens at
world size 4. So the table shapes that run a changed program are exactly
those with 16 tokens or fewer: 480 shapes, 160 per world size. The
baseline is the previous Cake version on FlashInfer main (PR #7813).
Across all 720 shapes, the geomean speedup is 1.010x on B300 (min
0.984x, max 1.059x) and 1.011x on B200 (min 0.983x, max 1.062x). For the
480 changed-program shapes, the geomean speedup is 1.015x on B300 (min
0.984x, max 1.059x) and 1.016x on B200 (min 0.983x, max 1.062x). Of
these, 62 on B300 and 59 on B200 measure below 1.000. Group geomeans
(B300 / B200) for the changed programs:
- World size 2 small-token, 1-16 tokens: 1.019 / 1.021.
- World size 4 small-token, 1-16 tokens: 1.019 / 1.020.
- World size 8 small-token, 1-16 tokens: 1.006 / 1.007. Here 53 of 160
shapes on B300 and 57 on B200 measure below 1.000, with min 0.984 /
0.983. The overall minima above come from this group.

The other 240 shapes run the same programs as before. Their geomean is
1.001x on B300 (min 0.990x, max 1.021x) and 1.000x on B200 (min 0.988x,
max 1.012x). The dispatch change was measured separately at world size 4
with 72 tokens, outside the table shapes, where two-shot now runs.
Across those 32 shapes, the geomean is 1.025x on B300 (min 1.001x, max
1.051x) and 1.027x on B200 (min 1.003x, max 1.048x).

The kernel has no other Cake variants: it ships only in this fused form
and covers sm_100a and sm_103a.

The tables below give one row per shape, measured on NVIDIA B300 SXM6 AC
(sm_103a) and NVIDIA B200 (sm_100a) with CUDA 13.4: the previous and
this-PR columns are the median CUPTI kernel time in microseconds, taking
the minimum over ranks; speedup is the median of paired previous/this-PR
ratios from interleaved runs, where values above 1 mean this PR is
faster; in the flag columns (PDL, NVFP4 out, shared expert), 1 means yes
and 0 means no.

World size 2:

|tokens|dtype|top-k|PDL|NVFP4 out|shared expert|B300 previous (us)|B300
this PR (us)|B300 speedup|B200 previous (us)|B200 this PR (us)|B200
speedup|
|--:|--|--:|:-:|:-:|:-:|--:|--:|--:|--:|--:|--:|
|1|fp16|4|0|0|0|8.99|8.67|1.029|7.76|7.34|1.053|
|1|fp16|4|0|0|1|9.01|8.53|1.039|7.79|7.46|1.044|
|1|fp16|4|0|1|0|9.09|8.62|1.059|7.84|7.46|1.057|
|1|fp16|4|0|1|1|8.78|8.69|1.024|7.73|7.54|1.028|
|1|fp16|4|1|0|0|8.72|8.32|1.034|7.81|7.54|1.036|
|1|fp16|4|1|0|1|8.93|8.58|1.056|7.90|7.52|1.032|
|1|fp16|4|1|1|0|8.83|8.54|1.030|8.10|7.70|1.057|
|1|fp16|4|1|1|1|9.12|8.78|1.031|8.10|7.73|1.054|
|1|fp16|8|0|0|0|8.90|8.69|1.032|8.19|7.79|1.051|
|1|fp16|8|0|0|1|9.15|8.86|1.033|8.24|8.00|1.028|
|1|fp16|8|0|1|0|9.30|8.99|1.035|8.29|7.81|1.057|
|1|fp16|8|0|1|1|9.26|9.19|1.012|8.38|7.97|1.038|
|1|fp16|8|1|0|0|9.22|8.66|1.030|8.03|7.63|1.038|
|1|fp16|8|1|0|1|9.30|8.99|1.029|8.24|7.82|1.048|
|1|fp16|8|1|1|0|9.15|8.86|1.033|8.18|7.81|1.034|
|1|fp16|8|1|1|1|9.39|9.18|1.030|8.27|8.02|1.055|
|1|bf16|4|0|0|0|8.74|8.45|1.034|7.76|7.42|1.044|
|1|bf16|4|0|0|1|8.83|8.54|1.043|7.73|7.44|1.043|
|1|bf16|4|0|1|0|8.96|8.72|1.031|7.60|7.33|1.050|
|1|bf16|4|0|1|1|8.96|8.77|1.025|7.98|7.62|1.040|
|1|bf16|4|1|0|0|8.86|8.53|1.046|7.57|7.23|1.051|
|1|bf16|4|1|0|1|8.98|8.56|1.043|7.74|7.44|1.062|
|1|bf16|4|1|1|0|8.74|8.35|1.045|7.95|7.62|1.060|
|1|bf16|4|1|1|1|8.88|8.70|1.029|8.00|7.79|1.028|
|1|bf16|8|0|0|0|9.12|8.74|1.051|7.90|7.52|1.043|
|1|bf16|8|0|0|1|9.09|8.72|1.021|8.11|7.81|1.049|
|1|bf16|8|0|1|0|9.15|8.59|1.051|8.03|7.60|1.045|
|1|bf16|8|0|1|1|9.31|8.90|1.032|8.08|7.84|1.024|
|1|bf16|8|1|0|0|9.12|8.78|1.051|7.78|7.47|1.045|
|1|bf16|8|1|0|1|9.17|8.80|1.041|8.00|7.82|1.037|
|1|bf16|8|1|1|0|9.07|8.77|1.037|8.16|7.94|1.043|
|1|bf16|8|1|1|1|9.15|8.98|1.019|8.29|8.05|1.028|
|2|fp16|4|0|0|0|10.10|9.92|1.021|7.68|7.55|1.011|
|2|fp16|4|0|0|1|10.30|10.06|1.017|7.87|7.57|1.047|
|2|fp16|4|0|1|0|10.22|10.10|1.014|7.82|7.57|1.030|
|2|fp16|4|0|1|1|10.38|10.22|1.011|7.87|7.70|1.013|
|2|fp16|4|1|0|0|9.86|9.76|1.024|7.46|7.34|1.022|
|2|fp16|4|1|0|1|10.40|9.92|1.051|7.68|7.52|1.046|
|2|fp16|4|1|1|0|10.13|9.97|1.021|8.00|7.74|1.032|
|2|fp16|4|1|1|1|10.30|10.21|1.018|7.82|7.65|1.035|
|2|fp16|8|0|0|0|10.43|10.16|1.030|8.08|7.86|1.027|
|2|fp16|8|0|0|1|10.40|10.30|1.012|7.98|7.84|1.023|
|2|fp16|8|0|1|0|10.61|10.37|1.017|8.21|8.03|1.034|
|2|fp16|8|0|1|1|10.70|10.61|1.019|8.26|8.21|1.022|
|2|fp16|8|1|0|0|10.19|10.08|1.003|8.00|7.94|1.018|
|2|fp16|8|1|0|1|10.66|10.40|1.026|8.13|7.95|1.022|
|2|fp16|8|1|1|0|10.35|9.97|1.036|7.89|7.73|1.020|
|2|fp16|8|1|1|1|10.77|10.61|1.015|8.24|7.94|1.040|
|2|bf16|4|0|0|0|9.81|9.73|1.018|7.49|7.28|1.039|
|2|bf16|4|0|0|1|10.34|10.00|1.030|7.66|7.42|1.035|
|2|bf16|4|0|1|0|10.19|9.98|1.017|7.65|7.49|1.019|
|2|bf16|4|0|1|1|10.43|10.24|1.009|7.81|7.74|1.021|
|2|bf16|4|1|0|0|9.92|9.87|1.015|7.34|7.25|1.027|
|2|bf16|4|1|0|1|10.22|10.02|1.009|7.70|7.36|1.035|
|2|bf16|4|1|1|0|10.27|10.05|1.013|7.71|7.60|1.017|
|2|bf16|4|1|1|1|10.48|10.26|1.020|7.71|7.58|1.019|
|2|bf16|8|0|0|0|10.34|10.08|1.012|7.58|7.47|1.017|
|2|bf16|8|0|0|1|10.46|10.22|1.026|7.90|7.68|1.032|
|2|bf16|8|0|1|0|10.37|10.19|1.027|7.68|7.60|1.025|
|2|bf16|8|0|1|1|10.45|10.37|1.009|8.24|7.98|1.026|
|2|bf16|8|1|0|0|10.43|10.16|1.023|8.02|7.73|1.038|
|2|bf16|8|1|0|1|10.53|10.29|1.031|7.98|7.90|1.012|
|2|bf16|8|1|1|0|10.46|10.24|1.014|8.13|7.94|1.028|
|2|bf16|8|1|1|1|10.74|10.54|1.021|8.00|7.84|1.024|
|4|fp16|4|0|0|0|10.26|10.05|1.022|9.50|9.28|1.020|
|4|fp16|4|0|0|1|10.43|10.24|1.023|9.57|9.55|1.002|
|4|fp16|4|0|1|0|10.40|10.29|1.020|9.68|9.54|1.008|
|4|fp16|4|0|1|1|10.59|10.35|1.027|9.79|9.70|1.005|
|4|fp16|4|1|0|0|10.22|10.13|1.006|9.65|9.44|1.016|
|4|fp16|4|1|0|1|10.59|10.30|1.022|9.63|9.47|1.014|
|4|fp16|4|1|1|0|10.24|10.05|1.029|9.63|9.42|1.015|
|4|fp16|4|1|1|1|10.53|10.42|1.017|9.92|9.68|1.021|
|4|fp16|8|0|0|0|10.56|10.26|1.023|9.76|9.57|1.015|
|4|fp16|8|0|0|1|10.72|10.53|1.018|9.79|9.70|1.008|
|4|fp16|8|0|1|0|10.74|10.56|1.020|9.86|9.68|1.011|
|4|fp16|8|0|1|1|10.90|10.64|1.023|10.14|9.98|1.015|
|4|fp16|8|1|0|0|10.43|10.34|1.009|9.70|9.65|1.010|
|4|fp16|8|1|0|1|10.74|10.50|1.018|10.08|9.86|1.021|
|4|fp16|8|1|1|0|10.67|10.46|1.018|9.89|9.74|1.010|
|4|fp16|8|1|1|1|10.85|10.59|1.026|10.13|9.92|1.018|
|4|bf16|4|0|0|0|10.14|10.02|1.011|9.44|9.23|1.021|
|4|bf16|4|0|0|1|10.35|10.22|1.022|9.66|9.49|1.026|
|4|bf16|4|0|1|0|10.37|10.18|1.013|9.70|9.47|1.017|
|4|bf16|4|0|1|1|10.51|10.32|1.016|9.78|9.73|1.005|
|4|bf16|4|1|0|0|10.14|9.98|1.012|9.39|9.31|1.011|
|4|bf16|4|1|0|1|10.42|10.21|1.019|9.71|9.58|1.012|
|4|bf16|4|1|1|0|10.35|10.10|1.017|9.52|9.39|1.007|
|4|bf16|4|1|1|1|10.51|10.37|1.018|9.70|9.62|1.002|
|4|bf16|8|0|0|0|10.54|10.35|1.028|9.84|9.60|1.011|
|4|bf16|8|0|0|1|10.80|10.58|1.024|10.00|9.84|1.015|
|4|bf16|8|0|1|0|10.66|10.48|1.014|9.98|9.84|1.010|
|4|bf16|8|0|1|1|10.83|10.64|1.015|10.19|9.94|1.023|
|4|bf16|8|1|0|0|10.53|10.40|1.011|9.86|9.68|1.013|
|4|bf16|8|1|0|1|10.62|10.54|1.015|9.94|9.79|1.015|
|4|bf16|8|1|1|0|10.53|10.37|1.022|9.87|9.71|1.010|
|4|bf16|8|1|1|1|10.82|10.62|1.018|9.97|9.90|1.019|
|8|fp16|4|0|0|0|10.26|10.16|1.003|9.60|9.50|1.012|
|8|fp16|4|0|0|1|10.50|10.45|1.025|9.65|9.74|0.998|
|8|fp16|4|0|1|0|10.43|10.32|1.014|9.78|9.70|1.010|
|8|fp16|4|0|1|1|10.56|10.46|1.009|9.87|9.79|1.007|
|8|fp16|4|1|0|0|10.26|10.19|1.008|9.66|9.54|1.018|
|8|fp16|4|1|0|1|10.46|10.13|1.020|9.74|9.60|1.016|
|8|fp16|4|1|1|0|10.38|10.37|1.005|9.84|9.66|1.013|
|8|fp16|4|1|1|1|10.58|10.48|1.011|9.86|9.86|1.007|
|8|fp16|8|0|0|0|10.67|10.59|1.000|10.05|9.92|1.005|
|8|fp16|8|0|0|1|10.82|10.67|1.014|10.13|10.03|1.011|
|8|fp16|8|0|1|0|10.72|10.72|1.003|10.18|10.00|1.016|
|8|fp16|8|0|1|1|10.99|10.88|1.010|10.37|10.21|1.016|
|8|fp16|8|1|0|0|10.64|10.48|1.020|9.98|9.86|1.002|
|8|fp16|8|1|0|1|10.75|10.72|0.997|10.19|10.05|1.003|
|8|fp16|8|1|1|0|10.78|10.66|1.015|10.08|10.05|1.008|
|8|fp16|8|1|1|1|10.83|10.72|1.014|10.22|10.13|1.010|
|8|bf16|4|0|0|0|10.29|10.24|1.003|9.58|9.52|1.002|
|8|bf16|4|0|0|1|10.30|10.18|1.020|9.66|9.58|1.007|
|8|bf16|4|0|1|0|10.37|10.26|1.009|9.71|9.58|1.009|
|8|bf16|4|0|1|1|10.50|10.34|1.020|9.84|9.73|1.015|
|8|bf16|4|1|0|0|10.14|10.10|1.010|9.47|9.36|1.012|
|8|bf16|4|1|0|1|10.40|10.18|1.022|9.70|9.55|1.012|
|8|bf16|4|1|1|0|10.34|10.14|1.019|9.60|9.50|1.012|
|8|bf16|4|1|1|1|10.54|10.30|1.017|9.94|9.82|1.010|
|8|bf16|8|0|0|0|10.53|10.45|1.003|9.90|9.86|1.000|
|8|bf16|8|0|0|1|10.72|10.56|1.011|9.98|10.00|1.005|
|8|bf16|8|0|1|0|10.67|10.54|1.011|10.10|9.99|1.003|
|8|bf16|8|0|1|1|10.78|10.78|0.999|10.22|10.06|1.016|
|8|bf16|8|1|0|0|10.64|10.51|1.009|10.00|9.84|1.021|
|8|bf16|8|1|0|1|10.69|10.53|1.012|10.00|9.95|1.010|
|8|bf16|8|1|1|0|10.59|10.54|1.006|9.98|9.94|1.005|
|8|bf16|8|1|1|1|10.78|10.69|1.012|10.22|10.00|1.014|
|16|fp16|4|0|0|0|10.35|10.24|1.014|9.54|9.65|1.009|
|16|fp16|4|0|0|1|10.45|10.34|1.016|9.92|9.79|1.021|
|16|fp16|4|0|1|0|10.43|10.40|1.009|9.84|9.65|1.020|
|16|fp16|4|0|1|1|10.78|10.53|1.020|10.22|9.98|1.019|
|16|fp16|4|1|0|0|10.50|10.34|1.019|9.94|9.70|1.022|
|16|fp16|4|1|0|1|10.58|10.48|1.011|10.05|9.82|1.016|
|16|fp16|4|1|1|0|10.62|10.42|1.014|10.08|9.84|1.018|
|16|fp16|4|1|1|1|10.78|10.67|1.012|10.24|9.95|1.019|
|16|fp16|8|0|0|0|10.79|10.85|0.993|10.27|10.21|1.011|
|16|fp16|8|0|0|1|10.96|10.91|1.003|10.53|10.29|1.023|
|16|fp16|8|0|1|0|10.99|10.96|1.004|10.53|10.35|1.017|
|16|fp16|8|0|1|1|11.20|10.98|1.020|10.54|10.40|1.014|
|16|fp16|8|1|0|0|10.88|10.82|1.009|10.18|10.18|1.000|
|16|fp16|8|1|0|1|10.93|10.88|1.008|10.26|10.18|1.010|
|16|fp16|8|1|1|0|10.96|10.83|1.015|10.27|10.16|1.011|
|16|fp16|8|1|1|1|11.10|11.01|1.013|10.46|10.45|1.011|
|16|bf16|4|0|0|0|10.40|10.29|1.013|9.71|9.68|1.008|
|16|bf16|4|0|0|1|10.61|10.45|1.017|10.03|9.81|1.018|
|16|bf16|4|0|1|0|10.42|10.38|1.011|10.02|9.86|1.013|
|16|bf16|4|0|1|1|10.72|10.61|1.014|10.22|9.98|1.013|
|16|bf16|4|1|0|0|10.37|10.26|1.014|9.84|9.73|1.013|
|16|bf16|4|1|0|1|10.62|10.37|1.020|9.95|9.86|1.012|
|16|bf16|4|1|1|0|10.51|10.42|1.011|10.03|9.95|1.010|
|16|bf16|4|1|1|1|10.69|10.54|1.014|10.14|10.00|1.013|
|16|bf16|8|0|0|0|10.85|10.61|1.020|10.30|10.08|1.019|
|16|bf16|8|0|0|1|10.83|10.83|1.009|10.35|10.22|1.019|
|16|bf16|8|0|1|0|10.91|10.80|1.009|10.30|10.22|1.000|
|16|bf16|8|0|1|1|11.02|10.99|1.004|10.51|10.32|1.019|
|16|bf16|8|1|0|0|10.70|10.50|1.018|10.02|9.92|1.005|
|16|bf16|8|1|0|1|10.94|10.88|1.006|10.43|10.30|1.010|
|16|bf16|8|1|1|0|10.93|10.85|1.015|10.34|10.27|1.006|
|16|bf16|8|1|1|1|11.02|10.91|1.010|10.46|10.42|1.018|
|128|fp16|4|0|0|0|12.85|13.18|1.010|12.85|12.83|1.012|
|128|fp16|4|0|0|1|13.78|13.63|0.995|13.39|13.38|1.001|
|128|fp16|4|0|1|0|13.42|13.31|0.997|13.04|13.01|1.004|
|128|fp16|4|0|1|1|14.06|14.05|1.006|13.68|13.73|1.000|
|128|fp16|4|1|0|0|13.25|13.20|0.998|12.74|12.86|0.996|
|128|fp16|4|1|0|1|13.74|13.90|0.991|13.33|13.41|1.001|
|128|fp16|4|1|1|0|13.42|13.34|1.010|13.02|13.09|1.000|
|128|fp16|4|1|1|1|13.95|13.90|0.995|13.66|13.66|1.000|
|128|fp16|8|0|0|0|14.96|14.96|0.998|14.67|14.69|0.998|
|128|fp16|8|0|0|1|15.62|15.58|0.996|15.31|15.25|1.003|
|128|fp16|8|0|1|0|15.20|15.22|0.995|14.94|14.98|1.006|
|128|fp16|8|0|1|1|15.78|15.92|0.998|15.54|15.57|0.999|
|128|fp16|8|1|0|0|14.98|14.98|1.006|14.62|14.70|1.002|
|128|fp16|8|1|0|1|15.57|15.52|1.001|15.30|15.30|1.002|
|128|fp16|8|1|1|0|15.04|15.20|0.999|14.83|14.90|0.998|
|128|fp16|8|1|1|1|15.76|15.74|1.007|15.54|15.60|1.002|
|128|bf16|4|0|0|0|13.15|13.14|0.994|12.69|12.75|0.994|
|128|bf16|4|0|0|1|13.73|13.78|0.994|13.34|13.47|0.996|
|128|bf16|4|0|1|0|13.33|13.41|0.996|12.98|13.02|0.994|
|128|bf16|4|0|1|1|13.92|13.95|1.001|13.57|13.71|0.990|
|128|bf16|4|1|0|0|13.12|13.09|0.998|12.66|12.70|1.000|
|128|bf16|4|1|0|1|13.76|13.82|0.999|13.39|13.42|1.000|
|128|bf16|4|1|1|0|13.28|13.44|0.991|12.99|12.98|1.003|
|128|bf16|4|1|1|1|14.05|13.90|0.993|13.73|13.66|0.999|
|128|bf16|8|0|0|0|14.88|15.07|0.994|14.56|14.53|0.999|
|128|bf16|8|0|0|1|15.52|15.49|0.998|15.20|15.15|0.996|
|128|bf16|8|0|1|0|15.12|15.23|0.998|14.75|14.85|0.997|
|128|bf16|8|0|1|1|15.65|15.55|1.001|15.42|15.41|1.002|
|128|bf16|8|1|0|0|14.78|14.99|1.006|14.56|14.56|1.000|
|128|bf16|8|1|0|1|15.33|15.36|1.010|15.20|15.10|0.998|
|128|bf16|8|1|1|0|15.17|15.06|1.001|14.78|14.85|0.998|
|128|bf16|8|1|1|1|15.76|15.84|1.001|15.33|15.50|0.997|
|512|fp16|4|0|0|0|26.28|26.12|1.010|25.69|25.66|0.997|
|512|fp16|4|0|0|1|27.61|27.06|1.005|26.50|26.42|1.003|
|512|fp16|4|0|1|0|27.37|27.36|0.999|26.80|26.81|0.998|
|512|fp16|4|0|1|1|28.30|28.38|1.001|27.56|27.53|1.003|
|512|fp16|4|1|0|0|26.33|26.44|0.996|25.80|25.82|0.998|
|512|fp16|4|1|0|1|27.38|27.16|0.997|26.53|26.51|0.999|
|512|fp16|4|1|1|0|27.23|27.26|0.998|26.74|26.70|0.997|
|512|fp16|4|1|1|1|28.58|28.37|1.009|27.55|27.63|1.000|
|512|bf16|4|0|0|0|26.17|26.16|1.002|25.56|25.68|0.995|
|512|bf16|4|0|0|1|27.42|27.23|1.005|26.28|26.32|0.999|
|512|bf16|4|0|1|0|27.24|27.24|1.002|26.74|26.78|0.998|
|512|bf16|4|0|1|1|28.26|28.73|0.995|27.56|27.50|1.003|
|512|bf16|4|1|0|0|26.00|26.07|1.001|25.63|25.72|0.995|
|512|bf16|4|1|0|1|27.34|27.52|0.997|26.26|26.30|1.000|
|512|bf16|4|1|1|0|27.18|27.23|1.003|26.61|26.61|0.998|
|512|bf16|4|1|1|1|28.82|28.70|0.999|27.42|27.46|0.998|
|1024|fp16|4|0|0|0|42.78|42.94|1.000|42.04|42.03|1.001|
|1024|fp16|4|0|0|1|45.51|45.71|1.000|45.33|45.30|1.002|
|1024|fp16|4|0|1|0|44.52|44.41|1.002|44.17|44.25|0.999|
|1024|fp16|4|0|1|1|48.05|48.15|1.002|47.50|47.32|1.003|
|1024|fp16|4|1|0|0|42.05|42.26|0.996|41.97|42.05|0.998|
|1024|fp16|4|1|0|1|45.74|46.13|0.999|45.34|45.53|0.997|
|1024|fp16|4|1|1|0|44.45|44.47|0.996|44.14|44.02|1.002|
|1024|fp16|4|1|1|1|48.02|49.14|1.001|47.63|47.64|1.000|
|1024|bf16|4|0|0|0|42.39|42.14|1.004|41.72|41.77|1.003|
|1024|bf16|4|0|0|1|46.21|46.47|1.001|45.00|45.16|0.996|
|1024|bf16|4|0|1|0|44.28|44.25|0.998|44.11|44.24|0.998|
|1024|bf16|4|0|1|1|48.35|47.73|0.999|47.04|46.97|1.001|
|1024|bf16|4|1|0|0|42.30|42.42|0.997|41.86|41.70|1.001|
|1024|bf16|4|1|0|1|47.32|47.16|1.004|45.21|45.23|0.999|
|1024|bf16|4|1|1|0|44.34|44.53|0.998|44.10|44.02|1.002|
|1024|bf16|4|1|1|1|49.05|48.91|1.008|47.42|47.21|1.004|
|2048|fp16|4|0|0|0|71.16|71.18|1.000|72.10|72.13|1.000|
|2048|fp16|4|0|0|1|79.10|78.90|1.003|80.44|80.50|1.001|
|2048|fp16|4|0|1|0|74.82|74.60|1.001|75.78|75.77|1.001|
|2048|fp16|4|0|1|1|82.45|82.54|1.000|84.10|84.15|1.000|
|2048|fp16|4|1|0|0|71.06|71.28|0.999|72.26|72.16|0.999|
|2048|fp16|4|1|0|1|78.92|78.86|1.001|80.49|80.52|0.999|
|2048|fp16|4|1|1|0|74.70|74.79|1.000|75.93|75.86|0.999|
|2048|fp16|4|1|1|1|82.23|82.23|0.999|84.03|84.04|1.001|
|2048|fp16|8|0|0|0|98.59|98.30|1.001|99.76|99.70|1.001|
|2048|fp16|8|0|0|1|105.46|105.37|1.001|107.07|107.14|0.999|
|2048|fp16|8|0|1|0|100.61|100.79|0.995|102.15|102.10|1.000|
|2048|fp16|8|0|1|1|107.82|107.69|1.000|109.60|109.44|1.002|
|2048|fp16|8|1|0|0|98.39|98.54|1.000|99.82|99.76|1.000|
|2048|fp16|8|1|0|1|105.50|105.58|0.999|107.18|107.04|1.002|
|2048|fp16|8|1|1|0|100.78|100.60|1.002|102.17|102.22|1.001|
|2048|fp16|8|1|1|1|107.73|107.49|1.001|109.57|109.56|1.000|
|2048|bf16|4|0|0|0|70.72|70.59|1.001|71.57|71.58|0.999|
|2048|bf16|4|0|0|1|78.25|78.24|0.999|79.91|79.90|1.000|
|2048|bf16|4|0|1|0|74.59|74.40|1.002|75.60|75.57|1.001|
|2048|bf16|4|0|1|1|82.17|82.13|1.000|83.72|83.68|1.000|
|2048|bf16|4|1|0|0|70.78|70.76|1.000|71.50|71.62|0.999|
|2048|bf16|4|1|0|1|78.27|78.23|1.000|79.96|79.94|0.999|
|2048|bf16|4|1|1|0|74.76|74.78|0.999|75.70|75.80|0.998|
|2048|bf16|4|1|1|1|82.06|82.06|1.000|83.84|83.65|1.002|
|2048|bf16|8|0|0|0|98.06|97.98|1.001|99.18|99.26|1.000|
|2048|bf16|8|0|0|1|104.86|105.07|0.999|106.52|106.58|1.000|
|2048|bf16|8|0|1|0|100.23|100.59|0.999|101.91|101.98|0.999|
|2048|bf16|8|0|1|1|107.22|107.10|1.001|108.82|108.98|0.999|
|2048|bf16|8|1|0|0|97.96|97.98|1.000|99.31|99.22|1.001|
|2048|bf16|8|1|0|1|104.98|104.69|1.001|106.54|106.52|0.999|
|2048|bf16|8|1|1|0|100.65|100.42|1.001|101.91|101.94|0.999|
|2048|bf16|8|1|1|1|107.36|107.10|1.001|109.24|109.22|0.999|

World size 4:

|tokens|dtype|top-k|PDL|NVFP4 out|shared expert|B300 previous (us)|B300
this PR (us)|B300 speedup|B200 previous (us)|B200 this PR (us)|B200
speedup|
|--:|--|--:|:-:|:-:|:-:|--:|--:|--:|--:|--:|--:|
|1|fp16|4|0|0|0|8.69|8.40|1.042|9.01|8.72|1.047|
|1|fp16|4|0|0|1|8.90|8.69|1.046|9.06|8.82|1.041|
|1|fp16|4|0|1|0|9.02|8.66|1.042|9.10|8.75|1.050|
|1|fp16|4|0|1|1|9.14|8.72|1.053|9.15|8.75|1.040|
|1|fp16|4|1|0|0|8.61|8.46|1.025|9.01|8.62|1.049|
|1|fp16|4|1|0|1|8.93|8.64|1.038|9.04|8.66|1.038|
|1|fp16|4|1|1|0|8.96|8.64|1.040|9.07|8.56|1.054|
|1|fp16|4|1|1|1|9.07|8.74|1.038|9.15|8.69|1.050|
|1|fp16|8|0|0|0|9.14|8.86|1.030|9.15|8.88|1.033|
|1|fp16|8|0|0|1|9.31|8.91|1.049|9.42|9.02|1.043|
|1|fp16|8|0|1|0|9.30|8.93|1.044|9.34|8.93|1.047|
|1|fp16|8|0|1|1|9.34|8.94|1.047|9.44|9.06|1.038|
|1|fp16|8|1|0|0|9.28|8.85|1.034|9.15|8.83|1.039|
|1|fp16|8|1|0|1|9.30|8.82|1.038|9.20|8.91|1.036|
|1|fp16|8|1|1|0|9.38|8.91|1.043|9.44|8.98|1.050|
|1|fp16|8|1|1|1|9.42|9.02|1.046|9.47|9.06|1.039|
|1|bf16|4|0|0|0|8.72|8.45|1.039|8.83|8.38|1.049|
|1|bf16|4|0|0|1|8.90|8.53|1.049|9.01|8.53|1.050|
|1|bf16|4|0|1|0|8.98|8.64|1.040|8.98|8.61|1.049|
|1|bf16|4|0|1|1|8.93|8.61|1.042|8.99|8.78|1.028|
|1|bf16|4|1|0|0|8.67|8.51|1.039|8.72|8.51|1.041|
|1|bf16|4|1|0|1|8.78|8.51|1.055|8.99|8.58|1.051|
|1|bf16|4|1|1|0|8.75|8.48|1.038|9.09|8.74|1.041|
|1|bf16|4|1|1|1|9.09|8.74|1.037|9.14|8.72|1.052|
|1|bf16|8|0|0|0|8.99|8.70|1.050|9.20|8.70|1.055|
|1|bf16|8|0|0|1|9.09|8.74|1.051|9.18|8.90|1.032|
|1|bf16|8|0|1|0|9.31|8.82|1.048|9.17|8.77|1.045|
|1|bf16|8|0|1|1|9.17|8.90|1.040|9.30|8.99|1.033|
|1|bf16|8|1|0|0|8.94|8.70|1.040|9.09|8.78|1.033|
|1|bf16|8|1|0|1|8.96|8.77|1.033|9.18|8.77|1.047|
|1|bf16|8|1|1|0|9.09|8.80|1.039|9.39|8.90|1.048|
|1|bf16|8|1|1|1|9.28|8.93|1.038|9.28|8.98|1.032|
|2|fp16|4|0|0|0|9.63|9.49|1.021|9.92|9.71|1.020|
|2|fp16|4|0|0|1|9.76|9.84|0.998|10.02|9.87|1.018|
|2|fp16|4|0|1|0|9.58|9.55|1.014|10.03|9.79|1.031|
|2|fp16|4|0|1|1|9.78|9.81|1.008|10.24|10.16|1.015|
|2|fp16|4|1|0|0|9.90|9.39|1.037|9.97|9.89|1.013|
|2|fp16|4|1|0|1|9.70|9.81|1.014|9.98|9.98|1.006|
|2|fp16|4|1|1|0|9.74|9.58|1.034|10.00|9.90|1.019|
|2|fp16|4|1|1|1|9.74|9.66|1.019|10.10|10.08|1.018|
|2|fp16|8|0|0|0|9.71|9.65|1.012|10.03|9.95|1.016|
|2|fp16|8|0|0|1|9.82|9.86|1.023|10.35|10.11|1.024|
|2|fp16|8|0|1|0|10.02|9.70|1.028|10.43|10.30|1.011|
|2|fp16|8|0|1|1|10.43|9.84|1.034|10.64|10.37|1.023|
|2|fp16|8|1|0|0|9.92|9.95|1.007|10.14|10.02|1.023|
|2|fp16|8|1|0|1|10.40|9.94|1.015|10.43|10.22|1.020|
|2|fp16|8|1|1|0|10.02|9.94|1.021|10.48|10.27|1.017|
|2|fp16|8|1|1|1|10.16|9.98|1.014|10.53|10.35|1.015|
|2|bf16|4|0|0|0|9.87|9.07|1.026|9.78|9.62|1.032|
|2|bf16|4|0|0|1|9.44|9.90|0.998|9.98|9.82|1.023|
|2|bf16|4|0|1|0|9.79|9.46|1.007|10.05|9.98|1.017|
|2|bf16|4|0|1|1|9.94|9.95|1.011|10.27|10.02|1.022|
|2|bf16|4|1|0|0|9.66|9.49|1.048|9.95|9.70|1.026|
|2|bf16|4|1|0|1|9.71|9.55|1.016|10.08|9.87|1.025|
|2|bf16|4|1|1|0|9.76|9.44|1.025|10.11|9.94|1.016|
|2|bf16|4|1|1|1|9.79|9.71|1.013|10.22|10.02|1.022|
|2|bf16|8|0|0|0|9.71|9.65|1.019|10.21|10.10|1.018|
|2|bf16|8|0|0|1|9.89|9.42|1.025|10.24|10.03|1.027|
|2|bf16|8|0|1|0|10.14|9.76|1.038|10.27|10.03|1.024|
|2|bf16|8|0|1|1|9.81|9.63|1.047|10.53|10.29|1.022|
|2|bf16|8|1|0|0|9.84|9.60|1.019|10.18|10.02|1.017|
|2|bf16|8|1|0|1|9.30|9.86|1.015|10.34|10.11|1.024|
|2|bf16|8|1|1|0|10.02|9.74|1.023|10.24|10.16|1.018|
|2|bf16|8|1|1|1|9.98|9.98|1.031|10.43|10.26|1.016|
|4|fp16|4|0|0|0|10.64|10.48|1.014|10.19|10.11|1.009|
|4|fp16|4|0|0|1|10.64|10.58|1.012|10.43|10.22|1.027|
|4|fp16|4|0|1|0|10.67|10.48|1.020|10.45|10.32|1.016|
|4|fp16|4|0|1|1|10.86|10.77|1.016|10.50|10.35|1.011|
|4|fp16|4|1|0|0|10.46|10.38|1.016|10.08|10.02|1.013|
|4|fp16|4|1|0|1|10.74|10.64|1.006|10.30|10.27|1.011|
|4|fp16|4|1|1|0|10.62|10.53|1.012|10.38|10.29|1.009|
|4|fp16|4|1|1|1|10.77|10.69|1.024|10.51|10.32|1.019|
|4|fp16|8|0|0|0|10.77|10.78|1.002|10.53|10.40|1.015|
|4|fp16|8|0|0|1|10.85|10.72|1.011|10.77|10.58|1.023|
|4|fp16|8|0|1|0|11.01|10.61|1.012|10.62|10.50|1.009|
|4|fp16|8|0|1|1|11.02|10.78|1.012|10.74|10.66|1.003|
|4|fp16|8|1|0|0|10.75|10.59|1.012|10.53|10.40|1.008|
|4|fp16|8|1|0|1|11.01|10.93|1.016|10.74|10.53|1.012|
|4|fp16|8|1|1|0|11.12|10.77|1.023|10.66|10.56|1.012|
|4|fp16|8|1|1|1|11.14|11.07|1.020|10.77|10.69|1.015|
|4|bf16|4|0|0|0|10.46|10.34|1.016|10.13|10.06|1.006|
|4|bf16|4|0|0|1|10.67|10.46|1.006|10.37|10.18|1.022|
|4|bf16|4|0|1|0|10.64|10.53|1.016|10.38|10.18|1.019|
|4|bf16|4|0|1|1|10.74|10.69|1.008|10.45|10.26|1.017|
|4|bf16|4|1|0|0|10.43|10.29|1.009|10.19|10.05|1.011|
|4|bf16|4|1|0|1|10.58|10.50|1.016|10.30|10.21|1.008|
|4|bf16|4|1|1|0|10.53|10.32|1.014|10.24|10.14|1.014|
|4|bf16|4|1|1|1|10.61|10.58|1.010|10.43|10.35|1.008|
|4|bf16|8|0|0|0|10.64|10.54|1.017|10.48|10.35|1.011|
|4|bf16|8|0|0|1|10.82|10.88|1.009|10.64|10.43|1.021|
|4|bf16|8|0|1|0|10.86|10.78|1.010|10.74|10.51|1.014|
|4|bf16|8|0|1|1|10.91|10.86|1.014|10.74|10.58|1.012|
|4|bf16|8|1|0|0|10.53|10.61|1.017|10.45|10.30|1.011|
|4|bf16|8|1|0|1|10.85|10.66|1.020|10.54|10.32|1.016|
|4|bf16|8|1|1|0|10.93|10.74|1.022|10.48|10.38|1.012|
|4|bf16|8|1|1|1|10.85|10.80|1.012|10.72|10.51|1.020|
|8|fp16|4|0|0|0|10.70|10.50|0.994|10.40|10.26|1.005|
|8|fp16|4|0|0|1|10.82|10.88|1.005|10.42|10.37|1.006|
|8|fp16|4|0|1|0|10.86|10.74|1.005|10.38|10.40|0.997|
|8|fp16|4|0|1|1|10.94|10.94|1.006|10.67|10.58|1.005|
|8|fp16|4|1|0|0|10.67|10.58|1.012|10.35|10.22|1.006|
|8|fp16|4|1|0|1|10.94|10.78|1.015|10.53|10.34|1.008|
|8|fp16|4|1|1|0|10.82|10.83|1.009|10.50|10.45|1.011|
|8|fp16|4|1|1|1|10.82|10.86|1.003|10.59|10.54|1.005|
|8|fp16|8|0|0|0|10.93|10.88|1.003|10.69|10.59|1.004|
|8|fp16|8|0|0|1|11.09|11.06|1.004|10.80|10.74|1.012|
|8|fp16|8|0|1|0|11.17|11.25|0.997|10.78|10.74|1.008|
|8|fp16|8|0|1|1|11.41|11.26|1.010|10.99|10.93|1.006|
|8|fp16|8|1|0|0|10.96|10.82|1.001|10.69|10.70|1.005|
|8|fp16|8|1|0|1|11.26|11.09|1.003|10.90|10.72|1.010|
|8|fp16|8|1|1|0|11.18|11.04|1.010|10.80|10.83|1.000|
|8|fp16|8|1|1|1|11.20|11.28|1.004|10.99|10.93|1.007|
|8|bf16|4|0|0|0|10.50|10.51|1.008|10.27|10.21|1.006|
|8|bf16|4|0|0|1|10.66|10.67|1.010|10.48|10.32|1.017|
|8|bf16|4|0|1|0|10.78|10.64|1.014|10.51|10.35|1.012|
|8|bf16|4|0|1|1|11.04|10.54|1.020|10.59|10.48|1.009|
|8|bf16|4|1|0|0|10.54|10.34|1.013|10.29|10.27|1.002|
|8|bf16|4|1|0|1|10.62|10.48|1.000|10.50|10.34|1.015|
|8|bf16|4|1|1|0|10.51|10.59|1.016|10.37|10.34|1.006|
|8|bf16|4|1|1|1|10.66|10.56|1.021|10.56|10.37|1.015|
|8|bf16|8|0|0|0|10.70|10.62|1.012|10.53|10.45|1.008|
|8|bf16|8|0|0|1|10.69|10.64|1.002|10.61|10.56|1.003|
|8|bf16|8|0|1|0|10.98|10.83|1.015|10.80|10.58|1.022|
|8|bf16|8|0|1|1|11.14|11.01|1.016|10.82|10.77|1.006|
|8|bf16|8|1|0|0|10.77|10.83|1.016|10.58|10.43|1.008|
|8|bf16|8|1|0|1|10.70|10.94|1.004|10.64|10.54|1.004|
|8|bf16|8|1|1|0|10.70|10.72|1.012|10.77|10.66|1.012|
|8|bf16|8|1|1|1|11.02|11.07|1.022|10.88|10.72|1.015|
|16|fp16|4|0|0|0|11.26|11.14|1.009|10.78|10.67|1.016|
|16|fp16|4|0|0|1|11.36|11.14|1.012|10.88|10.80|1.017|
|16|fp16|4|0|1|0|11.31|11.17|1.021|10.96|10.78|1.015|
|16|fp16|4|0|1|1|11.31|11.20|1.008|11.02|10.90|1.019|
|16|fp16|4|1|0|0|11.12|10.94|1.009|10.88|10.67|1.017|
|16|fp16|4|1|0|1|11.15|11.07|1.003|10.98|10.82|1.016|
|16|fp16|4|1|1|0|11.38|11.07|1.022|10.99|10.88|1.016|
|16|fp16|4|1|1|1|11.38|11.20|1.009|11.14|10.93|1.016|
|16|fp16|8|0|0|0|11.68|11.42|1.006|11.25|11.07|1.017|
|16|fp16|8|0|0|1|11.70|11.55|1.019|11.36|11.15|1.017|
|16|fp16|8|0|1|0|11.70|11.65|1.003|11.38|11.28|1.017|
|16|fp16|8|0|1|1|11.62|11.62|1.006|11.46|11.26|1.013|
|16|fp16|8|1|0|0|11.39|11.25|0.997|11.22|11.02|1.015|
|16|fp16|8|1|0|1|11.41|11.28|1.008|11.23|11.07|1.016|
|16|fp16|8|1|1|0|11.71|11.44|1.016|11.39|11.20|1.013|
|16|fp16|8|1|1|1|11.70|11.41|1.004|11.39|11.33|1.011|
|16|bf16|4|0|0|0|11.12|10.90|1.010|10.74|10.53|1.021|
|16|bf16|4|0|0|1|10.94|11.12|1.010|10.78|10.62|1.014|
|16|bf16|4|0|1|0|11.12|11.01|1.014|10.88|10.74|1.018|
|16|bf16|4|0|1|1|11.31|11.12|1.010|11.02|10.80|1.021|
|16|bf16|4|1|0|0|10.98|10.94|1.016|10.85|10.59|1.020|
|16|bf16|4|1|0|1|11.20|10.98|1.020|10.94|10.74|1.018|
|16|bf16|4|1|1|0|11.23|10.98|1.010|10.94|10.74|1.021|
|16|bf16|4|1|1|1|11.33|11.04|0.994|11.09|10.90|1.015|
|16|bf16|8|0|0|0|11.36|11.07|1.010|11.06|10.98|1.009|
|16|bf16|8|0|0|1|11.39|11.12|1.008|11.14|10.99|1.012|
|16|bf16|8|0|1|0|11.57|11.38|1.008|11.22|11.04|1.016|
|16|bf16|8|0|1|1|11.60|11.50|1.010|11.33|11.15|1.017|
|16|bf16|8|1|0|0|11.44|11.34|1.006|11.23|11.06|1.019|
|16|bf16|8|1|0|1|11.47|11.42|1.004|11.31|11.10|1.014|
|16|bf16|8|1|1|0|11.68|11.47|1.016|11.39|11.15|1.023|
|16|bf16|8|1|1|1|11.78|11.57|1.003|11.41|11.26|1.010|
|128|fp16|4|0|0|0|16.27|16.24|1.002|15.47|15.47|1.001|
|128|fp16|4|0|0|1|16.75|16.85|0.990|16.42|16.32|0.999|
|128|fp16|4|0|1|0|16.08|16.10|1.002|15.63|15.55|1.002|
|128|fp16|4|0|1|1|16.82|16.85|1.004|16.43|16.35|1.005|
|128|fp16|4|1|0|0|15.94|16.03|1.005|15.36|15.42|0.993|
|128|fp16|4|1|0|1|16.82|16.72|1.004|16.34|16.16|1.005|
|128|fp16|4|1|1|0|16.22|16.22|0.999|15.66|15.68|0.999|
|128|fp16|4|1|1|1|17.07|17.02|0.999|16.50|16.61|0.993|
|128|fp16|8|0|0|0|18.02|18.06|0.999|17.52|17.52|1.002|
|128|fp16|8|0|0|1|18.37|18.50|0.995|18.10|17.98|0.999|
|128|fp16|8|0|1|0|18.00|18.05|0.995|17.78|17.86|0.995|
|128|fp16|8|0|1|1|18.74|18.59|1.001|18.35|18.32|1.001|
|128|fp16|8|1|0|0|17.94|17.97|0.996|17.54|17.63|0.995|
|128|fp16|8|1|0|1|18.46|18.38|1.003|18.11|18.13|0.996|
|128|fp16|8|1|1|0|18.19|18.11|0.999|17.79|17.86|0.997|
|128|fp16|8|1|1|1|18.69|18.66|0.997|18.35|18.30|1.000|
|128|bf16|4|0|0|0|16.11|16.05|1.004|15.52|15.62|0.994|
|128|bf16|4|0|0|1|16.88|17.02|0.994|16.24|16.29|1.000|
|128|bf16|4|0|1|0|16.46|16.14|1.015|15.62|15.55|1.004|
|128|bf16|4|0|1|1|16.98|17.22|0.998|16.45|16.32|1.000|
|128|bf16|4|1|0|0|16.05|16.10|0.999|15.42|15.52|1.000|
|128|bf16|4|1|0|1|17.07|17.04|1.004|16.32|16.21|1.007|
|128|bf16|4|1|1|0|16.35|16.38|1.005|15.63|15.60|1.000|
|128|bf16|4|1|1|1|17.15|17.12|1.005|16.35|16.35|1.001|
|128|bf16|8|0|0|0|17.66|17.74|1.005|17.06|17.07|1.004|
|128|bf16|8|0|0|1|18.45|18.42|0.997|17.68|17.73|0.999|
|128|bf16|8|0|1|0|17.82|17.82|0.997|17.14|17.18|0.998|
|128|bf16|8|0|1|1|18.50|18.53|1.004|17.65|17.68|0.995|
|128|bf16|8|1|0|0|17.65|17.65|1.000|16.96|16.93|0.996|
|128|bf16|8|1|0|1|18.26|18.38|0.996|17.68|17.62|0.996|
|128|bf16|8|1|1|0|17.76|17.65|1.004|17.06|17.14|0.995|
|128|bf16|8|1|1|1|18.38|18.38|0.996|17.81|17.81|0.995|
|2048|fp16|4|0|0|0|80.87|81.22|0.996|81.77|81.41|1.003|
|2048|fp16|4|0|0|1|87.49|87.30|1.004|89.18|89.07|1.001|
|2048|fp16|4|0|1|0|84.33|84.33|1.003|85.75|85.98|0.998|
|2048|fp16|4|0|1|1|90.58|90.66|1.000|92.70|92.84|1.000|
|2048|fp16|4|1|0|0|81.56|81.54|1.000|82.22|82.12|1.001|
|2048|fp16|4|1|0|1|87.44|87.65|0.997|89.30|89.34|0.999|
|2048|fp16|4|1|1|0|84.41|84.30|1.000|85.78|86.05|0.998|
|2048|fp16|4|1|1|1|90.78|90.92|0.999|92.51|92.50|0.999|
|2048|fp16|8|0|0|0|98.87|98.98|0.999|101.10|100.88|1.002|
|2048|fp16|8|0|0|1|107.78|107.80|0.999|110.18|110.24|0.999|
|2048|fp16|8|0|1|0|103.29|103.35|0.999|105.61|105.64|1.000|
|2048|fp16|8|0|1|1|111.67|111.63|1.000|114.28|114.35|1.000|
|2048|fp16|8|1|0|0|99.01|98.83|1.001|100.97|101.02|0.999|
|2048|fp16|8|1|0|1|107.82|107.99|0.999|110.06|110.03|1.000|
|2048|fp16|8|1|1|0|103.31|103.29|1.000|105.47|105.50|0.998|
|2048|fp16|8|1|1|1|111.63|111.69|0.999|114.34|114.22|0.999|
|2048|bf16|4|0|0|0|81.38|81.47|0.997|82.62|82.57|1.002|
|2048|bf16|4|0|0|1|88.33|88.20|1.001|90.29|90.23|0.999|
|2048|bf16|4|0|1|0|85.46|85.58|0.997|87.13|87.24|0.999|
|2048|bf16|4|0|1|1|91.62|91.79|0.998|93.70|93.85|0.998|
|2048|bf16|4|1|0|0|82.15|81.88|1.002|83.65|83.24|1.001|
|2048|bf16|4|1|0|1|88.47|88.15|1.002|90.19|90.41|1.000|
|2048|bf16|4|1|1|0|85.61|85.34|1.000|87.23|86.90|1.000|
|2048|bf16|4|1|1|1|91.55|91.34|1.001|93.34|93.28|0.998|
|2048|bf16|8|0|0|0|99.89|99.90|1.000|101.91|102.03|0.998|
|2048|bf16|8|0|0|1|108.12|108.28|1.000|110.49|110.48|1.000|
|2048|bf16|8|0|1|0|103.58|103.47|1.000|105.81|105.75|0.999|
|2048|bf16|8|0|1|1|111.66|111.74|0.999|114.16|114.15|1.001|
|2048|bf16|8|1|0|0|99.75|99.72|1.001|101.76|101.83|1.001|
|2048|bf16|8|1|0|1|108.42|108.51|0.999|110.47|110.52|1.000|
|2048|bf16|8|1|1|0|103.55|103.79|0.998|105.83|105.81|1.002|
|2048|bf16|8|1|1|1|111.90|111.72|1.002|114.22|114.30|0.999|

World size 8:

|tokens|dtype|top-k|PDL|NVFP4 out|shared expert|B300 previous (us)|B300
this PR (us)|B300 speedup|B200 previous (us)|B200 this PR (us)|B200
speedup|
|--:|--|--:|:-:|:-:|:-:|--:|--:|--:|--:|--:|--:|
|1|fp16|4|0|0|0|9.54|9.42|1.024|9.47|9.31|1.022|
|1|fp16|4|0|0|1|9.39|9.34|1.005|9.42|9.28|1.015|
|1|fp16|4|0|1|0|9.47|9.28|1.026|9.52|9.33|1.019|
|1|fp16|4|0|1|1|9.65|9.38|1.040|9.70|9.28|1.036|
|1|fp16|4|1|0|0|9.49|9.14|1.039|9.46|9.25|1.023|
|1|fp16|4|1|0|1|9.44|9.28|1.031|9.52|9.33|1.020|
|1|fp16|4|1|1|0|9.60|9.44|1.028|9.66|9.38|1.030|
|1|fp16|4|1|1|1|9.58|9.42|1.014|9.54|9.26|1.029|
|1|fp16|8|0|0|0|9.73|9.42|1.032|9.65|9.30|1.040|
|1|fp16|8|0|0|1|9.84|9.62|1.018|9.74|9.49|1.032|
|1|fp16|8|0|1|0|9.82|9.70|1.002|9.79|9.52|1.027|
|1|fp16|8|0|1|1|9.95|9.58|1.026|9.70|9.54|1.022|
|1|fp16|8|1|0|0|9.54|9.55|0.997|9.55|9.33|1.022|
|1|fp16|8|1|0|1|9.86|9.54|1.017|9.78|9.46|1.031|
|1|fp16|8|1|1|0|9.76|9.57|1.003|9.71|9.47|1.029|
|1|fp16|8|1|1|1|9.82|9.65|1.012|9.86|9.63|1.026|
|1|bf16|4|0|0|0|9.41|9.17|1.028|9.30|9.02|1.043|
|1|bf16|4|0|0|1|9.42|9.36|1.005|9.50|9.18|1.037|
|1|bf16|4|0|1|0|9.54|9.22|1.037|9.41|9.15|1.031|
|1|bf16|4|0|1|1|9.70|9.54|1.007|9.57|9.39|1.029|
|1|bf16|4|1|0|0|9.46|9.18|1.032|9.31|9.07|1.030|
|1|bf16|4|1|0|1|9.50|9.44|1.014|9.42|9.07|1.028|
|1|bf16|4|1|1|0|9.60|9.41|1.015|9.49|9.23|1.033|
|1|bf16|4|1|1|1|9.57|9.44|1.000|9.55|9.41|1.016|
|1|bf16|8|0|0|0|9.74|9.49|1.034|9.74|9.38|1.035|
|1|bf16|8|0|0|1|9.81|9.66|1.025|9.73|9.36|1.023|
|1|bf16|8|0|1|0|9.89|9.73|1.015|9.71|9.58|1.018|
|1|bf16|8|0|1|1|9.89|9.70|1.010|9.78|9.55|1.024|
|1|bf16|8|1|0|0|9.76|9.54|1.023|9.73|9.34|1.033|
|1|bf16|8|1|0|1|9.84|9.62|1.032|9.68|9.34|1.033|
|1|bf16|8|1|1|0|9.89|9.54|1.033|9.66|9.46|1.030|
|1|bf16|8|1|1|1|10.00|9.66|1.029|9.79|9.46|1.027|
|2|fp16|4|0|0|0|10.67|10.22|1.037|10.53|10.46|1.015|
|2|fp16|4|0|0|1|10.67|10.62|1.019|10.53|10.45|1.011|
|2|fp16|4|0|1|0|10.85|10.77|1.009|10.67|10.54|1.006|
|2|fp16|4|0|1|1|10.62|10.64|0.999|10.82|10.69|1.007|
|2|fp16|4|1|0|0|10.67|10.66|1.000|10.40|10.43|1.000|
|2|fp16|4|1|0|1|10.82|10.75|1.015|10.74|10.48|1.017|
|2|fp16|4|1|1|0|10.53|10.77|1.000|10.70|10.54|1.014|
|2|fp16|4|1|1|1|11.01|11.07|0.997|10.90|10.75|1.024|
|2|fp16|8|0|0|0|10.96|10.93|1.000|10.80|10.78|0.999|
|2|fp16|8|0|0|1|10.99|10.78|1.010|10.91|10.90|1.009|
|2|fp16|8|0|1|0|11.23|11.07|1.017|11.04|10.96|1.006|
|2|fp16|8|0|1|1|11.31|11.28|0.999|11.14|11.06|1.007|
|2|fp16|8|1|0|0|10.99|11.10|1.000|10.90|10.85|1.000|
|2|fp16|8|1|0|1|11.01|11.10|0.997|10.94|10.86|1.013|
|2|fp16|8|1|1|0|11.26|11.23|1.001|11.04|11.01|1.001|
|2|fp16|8|1|1|1|11.14|11.20|1.005|11.18|10.96|1.015|
|2|bf16|4|0|0|0|10.96|10.88|1.004|10.61|10.51|1.011|
|2|bf16|4|0|0|1|11.01|10.85|1.034|10.75|10.54|1.014|
|2|bf16|4|0|1|0|10.96|10.98|1.003|10.67|10.62|1.009|
|2|bf16|4|0|1|1|11.12|11.01|1.010|10.80|10.67|1.012|
|2|bf16|4|1|0|0|11.01|10.74|1.013|10.54|10.42|1.014|
|2|bf16|4|1|0|1|11.07|10.86|1.015|10.78|10.61|1.016|
|2|bf16|4|1|1|0|11.10|10.96|1.007|10.74|10.62|1.014|
|2|bf16|4|1|1|1|11.14|11.07|1.007|10.85|10.66|1.017|
|2|bf16|8|0|0|0|11.06|10.94|1.010|10.72|10.56|1.019|
|2|bf16|8|0|0|1|11.28|11.30|1.011|10.96|10.82|1.009|
|2|bf16|8|0|1|0|11.28|11.14|1.013|10.85|10.72|1.006|
|2|bf16|8|0|1|1|11.42|11.15|1.021|10.96|10.86|1.004|
|2|bf16|8|1|0|0|11.07|11.20|1.000|10.77|10.69|1.006|
|2|bf16|8|1|0|1|11.34|11.17|1.010|10.93|10.83|1.007|
|2|bf16|8|1|1|0|11.26|11.20|1.013|10.90|10.77|1.012|
|2|bf16|8|1|1|1|11.28|11.26|1.014|11.15|10.94|1.022|
|4|fp16|4|0|0|0|11.22|11.22|0.997|10.70|10.78|0.994|
|4|fp16|4|0|0|1|11.54|11.44|0.995|10.83|10.82|1.000|
|4|fp16|4|0|1|0|11.49|11.49|1.004|10.82|10.88|0.999|
|4|fp16|4|0|1|1|11.58|11.65|0.992|10.98|10.96|1.001|
|4|fp16|4|1|0|0|11.34|11.26|1.006|10.69|10.64|1.009|
|4|fp16|4|1|0|1|11.34|11.31|0.999|10.91|10.80|1.001|
|4|fp16|4|1|1|0|11.36|11.38|1.003|10.88|10.85|0.994|
|4|fp16|4|1|1|1|11.65|11.57|1.017|10.96|11.04|0.999|
|4|fp16|8|0|0|0|11.54|11.54|1.013|10.98|11.02|0.996|
|4|fp16|8|0|0|1|11.71|11.65|1.008|11.12|11.02|1.010|
|4|fp16|8|0|1|0|11.84|11.84|1.003|11.18|11.23|0.996|
|4|fp16|8|0|1|1|11.86|11.84|1.003|11.28|11.20|1.006|
|4|fp16|8|1|0|0|11.62|11.55|1.004|10.94|11.01|0.993|
|4|fp16|8|1|0|1|11.78|11.58|1.004|11.12|11.10|0.999|
|4|fp16|8|1|1|0|11.81|11.73|1.014|11.15|11.17|0.993|
|4|fp16|8|1|1|1|11.78|11.86|0.997|11.30|11.23|1.003|
|4|bf16|4|0|0|0|11.26|11.18|1.001|10.72|10.69|1.004|
|4|bf16|4|0|0|1|11.50|11.33|1.013|10.75|10.78|0.997|
|4|bf16|4|0|1|0|11.46|11.34|1.008|10.80|10.82|0.999|
|4|bf16|4|0|1|1|11.54|11.52|1.004|10.98|10.88|1.000|
|4|bf16|4|1|0|0|11.28|11.22|1.001|10.69|10.64|0.999|
|4|bf16|4|1|0|1|11.41|11.18|1.014|10.82|10.75|1.006|
|4|bf16|4|1|1|0|11.39|11.38|1.004|10.85|10.77|1.012|
|4|bf16|4|1|1|1|11.47|11.47|0.997|10.96|10.90|1.004|
|4|bf16|8|0|0|0|11.50|11.52|1.004|10.94|10.93|1.001|
|4|bf16|8|0|0|1|11.41|11.46|0.997|11.07|10.98|1.007|
|4|bf16|8|0|1|0|11.66|11.54|1.004|11.10|11.10|0.999|
|4|bf16|8|0|1|1|11.71|11.81|0.997|11.14|11.17|1.003|
|4|bf16|8|1|0|0|11.46|11.58|0.987|10.96|10.90|1.010|
|4|bf16|8|1|0|1|11.66|11.46|1.013|11.07|10.99|1.007|
|4|bf16|8|1|1|0|11.84|11.63|1.019|11.14|11.07|1.001|
|4|bf16|8|1|1|1|11.63|11.81|0.993|11.20|11.14|1.006|
|8|fp16|4|0|0|0|11.76|11.89|0.988|11.04|11.10|0.993|
|8|fp16|4|0|0|1|11.73|11.78|0.996|11.22|11.23|0.997|
|8|fp16|4|0|1|0|11.79|11.90|0.986|11.26|11.26|0.996|
|8|fp16|4|0|1|1|11.95|11.98|0.995|11.38|11.28|1.003|
|8|fp16|4|1|0|0|11.79|11.70|1.008|11.09|11.01|1.000|
|8|fp16|4|1|0|1|11.86|11.84|1.007|11.22|11.26|0.996|
|8|fp16|4|1|1|0|11.68|11.79|1.003|11.23|11.18|1.010|
|8|fp16|4|1|1|1|11.94|11.94|0.997|11.28|11.30|0.997|
|8|fp16|8|0|0|0|11.92|11.92|1.003|11.41|11.41|0.996|
|8|fp16|8|0|0|1|12.00|11.97|1.003|11.50|11.50|0.999|
|8|fp16|8|0|1|0|12.24|12.05|1.024|11.49|11.55|0.994|
|8|fp16|8|0|1|1|12.21|12.16|0.995|11.62|11.63|0.999|
|8|fp16|8|1|0|0|12.00|12.00|0.992|11.47|11.44|1.004|
|8|fp16|8|1|0|1|12.10|12.14|1.000|11.54|11.52|1.003|
|8|fp16|8|1|1|0|12.08|12.14|0.999|11.58|11.58|0.996|
|8|fp16|8|1|1|1|12.24|12.40|0.987|11.66|11.71|0.996|
|8|bf16|4|0|0|0|11.71|11.68|1.009|10.98|11.01|1.000|
|8|bf16|4|0|0|1|11.68|11.79|0.999|11.18|11.22|0.999|
|8|bf16|4|0|1|0|11.60|11.76|0.986|11.20|11.20|0.997|
|8|bf16|4|0|1|1|11.70|11.76|0.989|11.31|11.33|1.000|
|8|bf16|4|1|0|0|11.62|11.70|0.997|11.04|11.10|0.996|
|8|bf16|4|1|0|1|11.70|11.76|0.996|11.14|11.15|0.993|
|8|bf16|4|1|1|0|11.58|11.82|0.986|11.14|11.22|0.993|
|8|bf16|4|1|1|1|11.76|11.92|0.996|11.25|11.31|0.992|
|8|bf16|8|0|0|0|11.86|11.92|1.000|11.42|11.33|1.003|
|8|bf16|8|0|0|1|11.84|11.95|1.012|11.42|11.41|0.992|
|8|bf16|8|0|1|0|11.98|11.97|1.003|11.44|11.50|0.994|
|8|bf16|8|0|1|1|12.16|12.08|1.009|11.55|11.63|0.997|
|8|bf16|8|1|0|0|11.92|11.90|0.992|11.41|11.34|1.003|
|8|bf16|8|1|0|1|11.98|11.89|1.004|11.41|11.31|1.011|
|8|bf16|8|1|1|0|11.87|12.19|0.992|11.47|11.41|1.003|
|8|bf16|8|1|1|1|11.87|11.98|0.988|11.47|11.46|0.999|
|16|fp16|4|0|0|0|12.75|12.91|1.004|12.13|12.18|1.001|
|16|fp16|4|0|0|1|13.06|12.93|1.008|12.21|12.34|0.983|
|16|fp16|4|0|1|0|13.04|13.02|0.998|12.29|12.24|0.999|
|16|fp16|4|0|1|1|13.14|13.01|1.011|12.42|12.45|0.999|
|16|fp16|4|1|0|0|12.90|12.80|1.001|12.16|12.11|1.000|
|16|fp16|4|1|0|1|12.91|12.98|0.999|12.30|12.32|0.992|
|16|fp16|4|1|1|0|13.06|12.96|1.001|12.37|12.37|0.997|
|16|fp16|4|1|1|1|13.06|13.01|0.991|12.42|12.30|1.010|
|16|fp16|8|0|0|0|13.17|13.14|1.007|12.61|12.66|0.996|
|16|fp16|8|0|0|1|13.22|13.15|1.009|12.56|12.46|1.009|
|16|fp16|8|0|1|0|13.18|13.26|0.994|12.64|12.62|1.004|
|16|fp16|8|0|1|1|13.39|13.30|1.005|12.62|12.74|0.990|
|16|fp16|8|1|0|0|13.12|13.06|1.008|12.48|12.51|1.000|
|16|fp16|8|1|0|1|13.06|13.28|0.987|12.54|12.53|0.997|
|16|fp16|8|1|1|0|13.33|13.28|0.999|12.62|12.66|0.997|
|16|fp16|8|1|1|1|13.38|13.31|1.010|12.67|12.82|0.992|
|16|bf16|4|0|0|0|12.78|12.64|1.012|12.10|12.11|0.997|
|16|bf16|4|0|0|1|12.67|12.74|0.999|12.10|12.16|0.997|
|16|bf16|4|0|1|0|12.75|12.83|0.995|12.21|12.19|0.999|
|16|bf16|4|0|1|1|12.77|12.78|0.994|12.29|12.34|0.992|
|16|bf16|4|1|0|0|12.58|12.72|0.989|12.11|12.16|0.992|
|16|bf16|4|1|0|1|12.78|12.82|0.994|12.21|12.16|1.005|
|16|bf16|4|1|1|0|12.86|12.88|0.998|12.29|12.22|1.003|
|16|bf16|4|1|1|1|13.01|13.04|0.995|12.42|12.48|0.996|
|16|bf16|8|0|0|0|13.14|13.14|1.011|12.35|12.37|1.000|
|16|bf16|8|0|0|1|13.07|13.25|0.998|12.59|12.53|0.999|
|16|bf16|8|0|1|0|13.30|13.26|0.999|12.67|12.70|0.994|
|16|bf16|8|0|1|1|13.20|13.34|0.984|12.67|12.69|0.996|
|16|bf16|8|1|0|0|13.04|13.07|0.995|12.50|12.51|0.999|
|16|bf16|8|1|0|1|13.09|13.14|1.008|12.54|12.54|1.004|
|16|bf16|8|1|1|0|13.33|13.17|0.992|12.64|12.72|0.994|
|16|bf16|8|1|1|1|13.28|13.50|0.989|12.67|12.70|0.995|
|128|fp16|4|0|0|0|17.66|17.71|1.001|16.96|17.02|1.000|
|128|fp16|4|0|0|1|18.74|18.64|1.003|17.92|18.10|0.988|
|128|fp16|4|0|1|0|18.27|18.06|1.021|17.33|17.31|1.003|
|128|fp16|4|0|1|1|18.64|18.82|0.991|18.21|18.13|0.996|
|128|fp16|4|1|0|0|17.87|17.68|1.011|16.99|17.02|0.998|
|128|fp16|4|1|0|1|18.64|18.66|1.002|18.05|18.03|1.002|
|128|fp16|4|1|1|0|18.11|18.10|1.004|17.31|17.22|1.001|
|128|fp16|4|1|1|1|18.70|18.66|1.009|18.08|17.97|1.003|
|128|fp16|8|0|0|0|19.22|19.18|1.004|18.54|18.58|0.999|
|128|fp16|8|0|0|1|19.98|20.10|0.994|19.25|19.17|1.004|
|128|fp16|8|0|1|0|19.36|19.57|0.991|18.85|18.85|1.007|
|128|fp16|8|0|1|1|20.61|20.61|1.006|19.92|19.78|1.005|
|128|fp16|8|1|0|0|19.39|19.36|1.007|18.66|18.59|1.007|
|128|fp16|8|1|0|1|20.02|19.95|1.007|19.34|19.30|0.997|
|128|fp16|8|1|1|0|19.58|19.54|1.002|18.96|19.02|1.003|
|128|fp16|8|1|1|1|20.67|20.70|1.000|19.82|19.89|0.998|
|128|bf16|4|0|0|0|17.97|17.94|1.003|17.17|17.18|1.003|
|128|bf16|4|0|0|1|18.54|18.50|1.003|17.73|17.84|0.992|
|128|bf16|4|0|1|0|17.92|18.00|1.004|17.28|17.34|1.000|
|128|bf16|4|0|1|1|18.93|18.90|1.007|18.13|18.03|1.003|
|128|bf16|4|1|0|0|18.11|18.02|1.004|17.14|17.25|0.992|
|128|bf16|4|1|0|1|18.74|18.69|1.006|17.98|18.00|0.996|
|128|bf16|4|1|1|0|18.00|17.90|1.007|17.17|17.14|0.997|
|128|bf16|4|1|1|1|18.66|18.64|1.001|17.94|18.06|0.994|
|128|bf16|8|0|0|0|19.52|19.36|1.013|18.54|18.51|1.004|
|128|bf16|8|0|0|1|20.02|20.16|1.002|19.25|19.28|1.001|
|128|bf16|8|0|1|0|19.41|19.26|1.010|18.59|18.69|0.998|
|128|bf16|8|0|1|1|20.29|20.22|1.006|19.54|19.46|1.002|
|128|bf16|8|1|0|0|19.28|19.15|1.002|18.58|18.50|1.003|
|128|bf16|8|1|0|1|20.34|20.02|1.010|19.36|19.33|1.001|
|128|bf16|8|1|1|0|19.52|19.23|1.009|18.56|18.64|0.999|
|128|bf16|8|1|1|1|20.30|20.27|1.004|19.46|19.42|1.003|
|512|fp16|4|0|0|0|35.09|35.11|0.995|34.51|34.98|0.988|
|512|fp16|4|0|0|1|37.02|37.17|0.995|36.81|36.70|1.004|
|512|fp16|4|0|1|0|36.05|35.89|0.999|35.52|35.61|1.002|
|512|fp16|4|0|1|1|37.37|37.30|1.007|37.31|37.38|0.998|
|512|fp16|4|1|0|0|35.29|35.14|1.003|34.92|34.96|0.994|
|512|fp16|4|1|0|1|36.78|36.82|0.994|37.04|36.96|1.004|
|512|fp16|4|1|1|0|35.92|35.72|1.006|35.44|35.34|0.997|
|512|fp16|4|1|1|1|37.25|37.20|0.998|37.22|37.12|1.003|
|512|bf16|4|0|0|0|35.12|35.52|0.990|35.10|35.09|0.998|
|512|bf16|4|0|0|1|37.09|37.19|0.996|37.30|37.31|1.006|
|512|bf16|4|0|1|0|36.03|36.19|0.997|35.90|35.90|1.004|
|512|bf16|4|0|1|1|37.76|37.47|1.008|37.61|37.68|0.996|
|512|bf16|4|1|0|0|35.32|35.41|0.998|35.10|35.11|1.002|
|512|bf16|4|1|0|1|37.02|37.22|0.995|37.33|37.34|1.000|
|512|bf16|4|1|1|0|35.94|35.90|1.001|35.71|35.74|1.002|
|512|bf16|4|1|1|1|37.74|37.80|0.998|37.84|37.64|1.004|
|2048|fp16|4|0|0|0|98.50|98.16|1.006|96.10|96.22|0.999|
|2048|fp16|4|0|0|1|98.47|98.73|1.002|97.62|97.57|1.002|
|2048|fp16|4|0|1|0|100.20|99.90|1.006|99.66|99.34|1.003|
|2048|fp16|4|0|1|1|98.26|98.54|0.996|97.62|97.50|1.001|
|2048|fp16|4|1|0|0|98.90|98.99|1.004|96.68|96.58|0.999|
|2048|fp16|4|1|0|1|99.20|99.09|1.001|97.05|97.73|0.995|
|2048|fp16|4|1|1|0|99.69|100.32|1.008|99.84|99.74|1.001|
|2048|fp16|4|1|1|1|98.17|98.31|1.006|97.68|97.46|1.003|
|2048|fp16|8|0|0|0|103.66|103.89|0.997|105.66|105.54|0.999|
|2048|fp16|8|0|0|1|111.57|111.26|1.002|113.28|113.32|0.999|
|2048|fp16|8|0|1|0|105.34|105.38|1.000|107.51|107.56|1.000|
|2048|fp16|8|0|1|1|112.07|112.30|0.999|114.67|114.75|0.999|
|2048|fp16|8|1|0|0|103.49|103.77|0.997|105.39|105.60|1.000|
|2048|fp16|8|1|0|1|111.19|111.33|0.998|113.41|113.33|1.000|
|2048|fp16|8|1|1|0|105.28|105.50|0.997|107.90|107.97|0.999|
|2048|fp16|8|1|1|1|112.55|112.56|0.999|114.66|114.61|1.000|
|2048|bf16|4|0|0|0|97.83|97.67|1.000|96.74|96.43|1.005|
|2048|bf16|4|0|0|1|98.62|99.25|0.996|97.59|97.83|0.995|
|2048|bf16|4|0|1|0|99.31|99.60|0.999|99.68|100.24|0.996|
|2048|bf16|4|0|1|1|98.31|98.02|1.003|97.82|98.06|0.996|
|2048|bf16|4|1|0|0|97.87|97.78|0.999|97.02|97.05|0.998|
|2048|bf16|4|1|0|1|98.60|98.39|1.004|97.57|97.52|1.002|
|2048|bf16|4|1|1|0|99.38|99.19|1.002|100.37|99.74|1.011|
|2048|bf16|4|1|1|1|98.02|98.07|1.004|97.57|98.10|0.994|
|2048|bf16|8|0|0|0|103.52|103.92|0.998|105.64|105.79|1.000|
|2048|bf16|8|0|0|1|110.97|110.91|1.000|113.02|112.90|1.002|
|2048|bf16|8|0|1|0|105.47|105.56|0.998|107.99|108.10|0.997|
|2048|bf16|8|0|1|1|112.25|112.50|0.999|114.60|114.66|0.998|
|2048|bf16|8|1|0|0|103.63|103.61|1.002|105.54|105.62|0.999|
|2048|bf16|8|1|0|1|111.18|111.09|0.999|112.82|113.06|0.999|
|2048|bf16|8|1|1|0|105.74|105.46|1.002|107.84|108.26|1.003|
|2048|bf16|8|1|1|1|112.54|112.29|1.001|114.55|114.80|0.998|


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **Performance**
- The two-shot communication path is now selected at 72 tokens for world
size 4, down from 88. The threshold for world size 8 is unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e6f901b](https://github.com/flashinfer-ai/flashinfer/commit/e6f901b5a023bfe55ac79baabc3933b6c1fced3f)

- **作者**: eigen
- **时间**: 2026-10-29T23:07:02Z
- **提交信息**: perf(cake_dense_projection_gemm): plan the shipped eight-warp CTA programs for three SM103a input-gradient rows (#7902)

The Cake `dense_projection_gemm` kernel has 127 programs built from 124
templates. Its 120 dense templates take BF16 operands and write BF16
output (82) or FP32 output (38) in four operand layouts (`kk`, `kn`,
`nk`, `nn`). The FP32 router GEMM runs through BF16x3 emulation. This PR
adds no program. It routes three more BF16-output input-gradient (dgrad)
rows on `sm_103a` (GB300) to the two eight-warp CTA programs that
already ship for `sm_103a`. The 4096→1024 row now runs
`dense_proj_gemm_kn_n256_tma1_w8rs`. The 5120→1024 and 4096→48 rows run
`dense_proj_gemm_kn_n256_tma1_w8r`. These two programs already serve the
`sm_103a` 4096→512, 5120→512 and 6144→576 input-gradient rows. The
baseline is each row's previous Cake program, which is a ten-warp
program, on the same GPU (`sm_103a`, CUDA 13.4). On the 294-row shape
list, 4096→1024 drops from 74.2 to 71.7 µs (1.036) at T = 16231 and from
74.9 to 72.0 µs (1.041) at T = 16384. 5120→1024 drops from 92.5 to 89.4
µs (1.034) at T = 16231 and from 91.9 to 89.1 µs (1.031) at T = 16384.
4096→48 drops from 23.6 to 22.9 µs (1.029) at T = 16231 and from 23.7 to
23.3 µs (1.016) at T = 16384. A separate same-GPU comparison covers
small token counts outside the shape list. In it, 4096→1024 at T = 512
drops from 16.7 to 9.6 µs (1.74), and 5120→1024 at T = 256 drops from
15.8 to 9.8 µs (1.61). 4096→48 is slower at T = 512, where the tiles
fill one wave, rising from 4.78 to 5.07 µs (0.943). At T = 2560 its
ratio is 1.005. The other 288 rows of the 294-row shape list keep their
previous programs, and their measured ratios of 0.988 to 1.010 are
run-to-run variation.

The kernel's other variants cover BF16 and FP32 outputs, K-major and
MN-major operand layouts, row-major and transposed outputs, 64 / 128 /
256-row tiles, batched head-projection, split-tail and stream-K forms,
and the FP32 router GEMM through BF16x3 emulation, and the package ships
programs for `sm_100a` (GB200), `sm_103a` (GB300) and `sm_107a` (Rubin)
in 254 build entries (81 / 86 / 87) and 127 registry records, all
unchanged by this PR, with the eight-warp CTA form on `sm_100a` (one
program) and `sm_103a` (two programs).

**NVIDIA GB300 (sm_103a), driver 580.159.03, CUDA 13.4 (nvcc 13.4.92).
Cold-L2 CUPTI GPU time per iteration, median of 5 alternating groups ×
20 iterations, both sides in the same session. Latency in µs; speedup =
previous version / this PR. Four rows of unchanged programs (8192→128
dgrad BF16 at both T, o_proj dgrad FP32 at T = 16172 and 17408→5120
wgrad FP32 at T = 16231) come from a repeat session on another GB300.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
140.6 | 140.6 | 1.000 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
140.2 | 140.5 | 0.998 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 136.4
| 136.6 | 0.999 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 137.3
| 137.2 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
145.6 | 145.5 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
146.5 | 146.3 | 1.001 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 144.0
| 144.3 | 0.998 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 144.7
| 145.1 | 0.998 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
212.6 | 212.8 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
212.4 | 212.5 | 0.999 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
215.5 | 215.3 | 1.001 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
215.2 | 216.1 | 0.996 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
207.6 | 208.5 | 0.996 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
207.9 | 207.6 | 1.001 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
216.2 | 215.7 | 1.002 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
216.7 | 216.9 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
217.6 | 217.9 | 0.999 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
218.0 | 217.8 | 1.001 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 569.9 |
570.8 | 0.999 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 568.9 |
570.0 | 0.998 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 571.3 |
571.9 | 0.999 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 570.2 |
571.5 | 0.998 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 542.5 |
542.6 | 1.000 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 544.0 |
543.6 | 1.001 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 557.8 |
558.4 | 0.999 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 560.4 |
560.1 | 1.001 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 564.1 |
564.8 | 0.999 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 565.0 |
566.1 | 0.998 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 23.1 | 23.2 |
0.997 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 23.4 | 23.4 |
0.999 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 42.8 | 42.7 | 1.003
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 43.2 | 43.1 | 1.003
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 27.0 | 27.1 | 0.996
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 26.6 | 26.5 | 1.001
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.4 | 28.4 |
0.999 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.4 | 28.4 |
1.001 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.4 | 28.3 | 1.002
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.5 | 28.6 | 0.997
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 23.6 | 22.9 |
1.029 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 23.7 | 23.3 |
1.016 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 43.4 | 43.4 | 0.999
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 43.5 | 43.6 | 0.996
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.9 | 27.0 | 0.995
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 26.7 | 26.7 | 1.001
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.4 | 28.6 |
0.994 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.7 | 28.6 |
1.002 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.6 | 28.6 | 0.999
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 28.7 | 28.7 | 0.999
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 23.4 | 23.5 |
0.996 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 23.7 | 23.7 |
0.997 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 43.4 | 43.4 | 1.000
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 43.6 | 43.5 | 1.002
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 27.2 | 27.3 | 0.998
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 27.0 | 27.0 | 1.001
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.9 | 28.8 |
1.004 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.6 | 28.6 |
1.000 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.7 | 28.8 | 0.995
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.5 | 28.6 | 0.996
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 24.4 | 24.4 |
1.001 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 24.4 | 24.5 |
0.996 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 44.8 | 44.7 |
1.003 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 45.2 | 45.0 |
1.006 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 27.9 | 28.0 | 0.998
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 27.4 | 27.5 | 0.998
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.4 | 29.5 |
0.997 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.4 | 29.4 |
0.998 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.3 | 29.4 |
0.998 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.5 | 29.4 |
1.002 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 41.3 | 41.2 |
1.002 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 41.2 | 41.2 |
1.001 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 60.2 | 60.6 |
0.994 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 60.2 | 60.3 |
0.998 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 48.5 | 48.3 | 1.004
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 48.3 | 48.1 | 1.004
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 43.5 | 43.4 |
1.002 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 43.7 | 43.7 |
1.000 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 43.1 | 43.1 |
1.000 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 43.5 | 43.7 |
0.995 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 74.2 | 71.7 |
1.036 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 74.9 | 72.0 |
1.041 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 74.4 | 74.9 |
0.992 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 74.8 | 74.7 |
1.002 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 73.2 | 73.4 |
0.998 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 73.9 | 73.9 |
1.000 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 75.3 | 75.1 |
1.003 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 75.8 | 75.6 |
1.003 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 266.6 | 266.4 |
1.001 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 265.3 | 266.1 |
0.997 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 265.9 | 265.6 |
1.001 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 265.8 | 265.9 |
1.000 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 276.8 | 276.4 |
1.001 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 279.0 | 278.6 |
1.002 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 281.2 | 281.6 |
0.999 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 283.8 | 284.1 |
0.999 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 824.4 | 823.5 |
1.001 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 825.0 | 825.6 |
0.999 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 805.4 | 802.6 |
1.003 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 804.2 | 806.2 |
0.998 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 820.8 | 820.3 |
1.001 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 827.5 | 827.6 |
1.000 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 846.0 | 847.1 |
0.999 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 852.0 | 849.1 |
1.003 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 27.6 | 27.7 |
0.998 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 27.7 | 27.6 |
1.001 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 51.4 | 51.5 | 1.000
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 51.9 | 51.9 | 1.000
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 31.6 | 31.6 | 0.999
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 32.7 | 32.8 | 0.998
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 34.1 | 34.0 |
1.002 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 34.2 | 34.3 |
1.000 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 34.2 | 34.3 | 0.997
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 34.3 | 34.5 | 0.996
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 27.9 | 27.9 |
1.002 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 27.9 | 28.0 |
0.998 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 52.0 | 52.0 | 1.001
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 52.4 | 52.5 | 0.998
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 31.6 | 31.7 | 0.997
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 32.7 | 32.7 | 0.999
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 34.4 | 34.5 |
0.999 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 34.7 | 34.6 |
1.002 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 34.4 | 34.4 | 1.000
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 34.8 | 34.7 | 1.002
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 27.9 | 27.9 |
1.000 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 28.2 | 28.1 |
1.003 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 52.3 | 52.4 | 0.998
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 52.5 | 52.6 | 0.998
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 32.3 | 32.2 | 1.002
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 33.1 | 33.0 | 1.001
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 34.5 | 34.6 |
0.997 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 34.7 | 34.8 |
0.996 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 34.5 | 34.5 | 0.999
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 34.8 | 34.6 | 1.005
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 29.2 | 29.2 |
0.998 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 29.3 | 29.3 |
1.002 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 54.3 | 54.2 |
1.001 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 54.3 | 54.3 |
1.000 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 33.5 | 33.5 | 1.000
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 33.2 | 33.4 | 0.995
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 35.9 | 35.9 |
1.000 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 36.2 | 36.3 |
0.999 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 35.6 | 35.7 |
0.996 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 36.0 | 36.1 |
0.998 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 49.9 | 49.8 |
1.003 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 49.9 | 49.9 |
1.001 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 73.8 | 73.8 |
1.000 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 74.2 | 74.4 |
0.997 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 58.4 | 58.4 | 0.998
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 58.5 | 58.3 | 1.003
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 53.2 | 53.3 |
0.998 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 53.4 | 53.5 |
0.999 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 55.2 | 54.8 |
1.007 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 55.0 | 54.9 |
1.001 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 92.5 | 89.4 |
1.034 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 91.9 | 89.1 |
1.031 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 92.0 | 92.8 |
0.992 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 92.6 | 92.4 |
1.002 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 97.2 | 97.2 |
1.000 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 97.9 | 97.8 |
1.001 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 98.5 | 98.5 |
1.001 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 99.0 | 99.2 |
0.998 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 419.5 | 421.9 |
0.994 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 420.3 | 420.6 |
0.999 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 419.5 | 419.9 |
0.999 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 420.4 | 420.7 |
0.999 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 426.3 | 426.1 |
1.000 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 428.9 | 429.7 |
0.998 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 426.3 | 428.6 |
0.994 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 432.4 | 432.2 |
1.001 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1443.1 | 1449.2
| 0.996 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1454.6 | 1451.1
| 1.002 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1425.0 | 1434.3 |
0.993 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1432.4 | 1441.2 |
0.994 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1432.4 | 1428.5
| 1.003 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1452.4 | 1440.8
| 1.008 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1434.7 | 1434.6
| 1.000 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1440.0 | 1445.0
| 0.997 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 32.8
| 32.9 | 0.995 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 32.6
| 32.6 | 0.999 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 58.3 |
58.3 | 1.000 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 58.6 |
58.7 | 1.000 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 37.6 |
37.5 | 1.004 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 37.5 |
37.5 | 1.000 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 39.4
| 39.4 | 1.000 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 39.3
| 39.2 | 1.002 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 39.4 |
39.3 | 1.001 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 39.3 |
39.3 | 1.000 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 34.2
| 34.3 | 0.999 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 34.2
| 34.2 | 0.999 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 62.0 |
62.1 | 0.999 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 62.0 |
61.9 | 1.001 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 38.8 |
38.8 | 0.999 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 38.7 |
38.8 | 0.997 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 40.7
| 40.6 | 1.003 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 41.3
| 41.1 | 1.004 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 40.5 |
40.7 | 0.994 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 41.2 |
41.1 | 1.002 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 64.1 |
64.2 | 0.998 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 64.0 |
64.2 | 0.996 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 91.9 | 91.9
| 1.000 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 92.6 | 92.8
| 0.998 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 72.3 | 72.0
| 1.004 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 72.7 | 72.1
| 1.008 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 65.1 |
64.8 | 1.004 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 65.0 |
65.2 | 0.997 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 65.8 | 65.8
| 1.001 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 65.4 | 65.7
| 0.996 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 207.4 |
207.5 | 0.999 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 207.5 |
207.4 | 1.001 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 218.9 |
218.8 | 1.001 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 219.3 |
218.8 | 1.002 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 207.8 |
207.9 | 0.999 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 207.2 |
207.2 | 1.000 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 216.0 |
216.1 | 1.000 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 216.7 |
216.7 | 1.000 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 216.3 |
216.7 | 0.998 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 217.0 |
217.6 | 0.997 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
207.2 | 207.1 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
207.2 | 208.0 | 0.996 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
219.0 | 218.9 | 1.000 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
219.5 | 219.3 | 1.001 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
207.8 | 207.8 | 1.000 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
207.9 | 208.3 | 0.998 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
215.8 | 215.8 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
216.9 | 216.7 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
217.4 | 217.1 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
218.0 | 218.4 | 0.998 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1205.9 | 1205.7 | 1.000 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1218.2 | 1210.0 | 1.007 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1214.9 | 1220.3 | 0.996 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1226.2 | 1223.8 | 1.002 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 44.0 | 44.1 |
0.997 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 44.1 | 44.0 |
1.003 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 85.1 | 85.3 |
0.998 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 84.8 | 85.0 |
0.999 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 48.6 | 48.5 | 1.002
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 49.1 | 49.0 | 1.003
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 45.6 | 45.6 |
1.001 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 46.0 | 45.9 |
1.003 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 45.4 | 45.5 |
0.998 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 45.9 | 45.8 |
1.002 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 806.8 | 809.0 |
0.997 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 806.0 | 807.1 |
0.999 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 819.8 | 823.7 |
0.995 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 821.7 | 822.3 |
0.999 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 809.3 | 811.3 |
0.998 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 813.8 | 816.5 |
0.997 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 837.9 | 838.9 |
0.999 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 840.2 | 841.8 |
0.998 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1202.6 | 1201.6 | 1.001 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1215.9 | 1203.4 | 1.010 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1207.8 | 1208.1 | 1.000 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1214.0 | 1215.4 | 0.999 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1618.2
| 1634.5 | 0.990 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1618.7
| 1616.1 | 1.002 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1672.9
| 1670.2 | 1.002 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1649.3
| 1659.3 | 0.994 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1641.7 |
1661.5 | 0.988 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1648.3 |
1639.3 | 1.006 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1623.1
| 1626.2 | 0.998 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1618.5
| 1621.5 | 0.998 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1628.8
| 1627.6 | 1.001 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1638.5
| 1639.3 | 1.000 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1423.3 | 1419.6
| 1.003 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1437.1 | 1436.2
| 1.001 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1446.2 | 1435.4 |
1.008 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1439.9 | 1437.6 |
1.002 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1423.8 | 1417.7
| 1.004 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1464.3 | 1450.4
| 1.010 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1431.2 | 1431.7
| 1.000 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1438.7 | 1442.8
| 0.997 |
| qabs | dgrad | bf16 | 16172 | previous version | 232.2 | 232.5 | 0.999
|
| qabs | dgrad | bf16 | 16231 | previous version | 230.7 | 230.7 | 1.000
|
| qabs | fwd | bf16 | 16172 | previous version | 241.6 | 241.6 | 1.000 |
| qabs | fwd | bf16 | 16231 | previous version | 245.9 | 246.0 | 1.000 |
| qabs | wgrad | bf16 | 16172 | previous version | 218.7 | 218.9 | 0.999
|
| qabs | wgrad | bf16 | 16231 | previous version | 220.3 | 219.8 | 1.002
|
| vproj | dgrad | bf16 | 16172 | previous version | 265.5 | 265.4 |
1.001 |
| vproj | dgrad | bf16 | 16231 | previous version | 264.2 | 264.3 |
1.000 |
| vproj | fwd | bf16 | 16172 | previous version | 252.8 | 252.8 | 1.000
|
| vproj | fwd | bf16 | 16231 | previous version | 256.9 | 256.9 | 1.000
|
| vproj | wgrad | bf16 | 16172 | previous version | 236.6 | 237.0 |
0.998 |
| vproj | wgrad | bf16 | 16231 | previous version | 237.6 | 237.7 |
0.999 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 173.3 |
173.5 | 0.999 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 165.1 | 165.3
| 0.998 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 162.1 |
161.7 | 1.002 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 225.8 |
225.8 | 1.000 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 194.6 | 194.9
| 0.998 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 207.5 |
207.7 | 0.999 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 260.5 |
260.5 | 1.000 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 262.7 |
263.2 | 0.998 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 225.9 | 225.8
| 1.000 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 224.3 | 224.8
| 0.998 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 213.1 |
213.0 | 1.000 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 213.3 |
213.9 | 0.997 |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Expanded SM103 input-gradient coverage to six shape rows, with
eight-warp programs available for additional cases.
* Updated program selection for several shapes, including 4096→48,
4096→1024, and 5120→1024.
* Clarified when the eight-warp form yields to the ten-warp program and
documented the corresponding raster groups.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8f5f156](https://github.com/flashinfer-ai/flashinfer/commit/8f5f156e2ef2be48039f408d9aa8fc56e14ea129)

- **作者**: eigen
- **时间**: 2026-10-29T23:06:49Z
- **提交信息**: perf(cake_kda_train): communication-free KCP checkpoint recompute with a recompute handle (#7901)

Part of #7815 (checkpoint recompute with less communication).

Under `torch.utils.checkpoint`, the backward re-runs the forward of the
checkpointed region. For `chunk_kda_kcp`, that re-runs the forward state
exchange, which is 2 collectives per call (forward c1/c2). A
checkpointed KDA KCP layer therefore pays the forward exchange twice and
waits on slow ranks twice. This PR adds an optional recompute handle.
The original forward exchanges as before and stores its incoming states
`S_in` in the handle. The recompute inside the backward reads them back
and launches only rank-local programs, so it runs no collective and does
no wait. The backward still exchanges. Without a handle, behavior is
unchanged. Outputs and gradients are bitwise equal with a handle, with a
plain checkpoint and without a checkpoint.

The handle contract is the same as in #7846 (context-parallel halo
convolution, key `"conv"`) and #7852 (GDN). Related: #7872, #7855,
#7841, #7840.

## What changed
- `flashinfer.kda_train.chunk_kda_kcp` has two new public keyword-only
arguments:
  - `recompute_handle`: the default `None` keeps the current behavior.
  - `checkpoint_keep`: `"states"` (default) or `"transfer"`.
- `flashinfer.kda_train.KcpRecomputeHandle` is the handle class. It
follows the same contract as the conv handle of #7846. Any object with
an `entries` dict works. One handle can serve both the KDA call (key
`"kda"`) and one convolution call of the same layer.
- `checkpoint_keep="states"` keeps only `S_in` and runs with
`save_transfer=False`. This is bitwise the default form. `"transfer"`
also keeps the owner's c1 receive tensor and runs with
`save_transfer=True`. It cannot be used with `exchange="ring"`. If an
explicit `save_transfer` contradicts `checkpoint_keep`, the entry point
and the byte queries raise `ValueError`.
- `kcp_saved_bytes(ctx, H=..., checkpoint_keep=..., with_conv=...)`
returns the retained bytes. `kcp_comm_bytes(ctx, ...,
checkpoint_keep=...)` returns the step traffic.
- Usage rules:
- Create handles outside the outermost checkpoint region, one per layer
and micro-step.
- A forward outside the backward that finds an existing entry raises.
This catches reuse across micro-steps.
- A recompute whose entry came from a different context or call
configuration raises (fingerprint check).
- The handle is refused with `graph="replay"`, during CUDA-graph
capture, and with `debug_sequence`, `spec3_probe` and
`boundary_mode="replay"`.
- Every rank must pass a handle for the same call, or no rank may pass
one, at the same nesting level. A mismatch hangs or corrupts data. This
is not checked.
- Phase detection uses `torch._C._current_graph_task_id()`. If torch
does not have it, the handle is refused.
- Without a handle, a checkpoint retains nothing extra (0 bytes), as
before. A new test asserts this.
- Bug fix, in a separate commit: with the overlap schedule test option
and the ring exchange, when a context needs no hop (`max_hops == 0`),
the document start/end rows of `out` were never written, so they held
NaN or wrong values. Main can reach this through the overlap test
option. A probe on main gave an all-NaN `out` on two rows, and
12,280,532 of 12,288,000 `out` elements were wrong on a third. The fix
only touches the overlap path. The default `wait_first` schedule is
unchanged. A new test row fails with the fix reverted and passes with
it.
- A new section in `flashinfer/experimental/cake_kda_train/README.md`
documents the handle. Its usage example uses three conv handles, and the
KDA call shares the q handle.
- Changed files: `README.md`, `cake_kcp.py`, `cake_kcp_plan.py`,
`flashinfer/kda_train.py`. Tests: `test_cake_kda_train_api.py`,
`test_cake_kda_train_kcp.py`, `test_cake_kda_train_kcp_dist.py`. Diff:
+2313/-62.

## Collectives
Collectives per call, as original forward / recompute / backward. The
counts are identical on every rank, row and GPU.

| case | collectives |
|---|---|
| no checkpoint | 2/0/2 |
| checkpoint, no handle | 2/2/2 |
| checkpoint, handle, `states` | 2/0/2 |
| checkpoint, handle, `transfer` | 2/0/2 |
| reentrant checkpoint, no handle | 2/0/4 |
| reentrant checkpoint, handle | 2/0/2 |
| nested checkpoint, handle created outside | 2/0/2 |
| nested checkpoint, handle created inside | 2/2/2 (correct, not
communication-free) |
| ring exchange, handle | recompute 0 |
| whole layer core (3 KCP convolutions + q/k normalization + KDA in one
checkpoint), no handles | 5/5/5 |
| same, with handles | 5/0/5 |

Waits follow the same pattern. In the reentrant rows, the recompute runs
inside the backward pass. The counter therefore puts a no-handle
recompute's 2 collectives in the backward column (2/0/4).

## Validation
- `out`, `dq`, `dk`, `dv`, `dg` and `dbeta` are bitwise equal across
handle, plain checkpoint and no checkpoint, on every rank and row. So is
the downstream gradient that reads the recomputed `out`. The recompute's
`out` is bitwise equal to the original forward's `out`.
- Retained bytes are 0 without a handle. With a handle, they equal the
tensor `nbytes` and `kcp_saved_bytes` for both `checkpoint_keep`
options. Bytes sent and received per phase equal
`kcp_comm_bytes(checkpoint_keep=...)`. Example retained bytes per rank
at W=4, H=64, per-document zigzag (`s2048_5_3000_1`): 25,165,824 B with
`states` and 62,914,560 B with `transfer`.
- Multi-GPU rows at W=2 and W=4 cover contiguous, zigzag, per-document
zigzag and ragged layouts. The ragged rows include one where no document
crosses a rank. 9/9 checkpoint rows pass on GB200, and on GB300 and R200
on the previous base.
- CP8 on 2 GB200 nodes x 4 GPUs: 3/3 rows (zigzag, per-document zigzag,
ragged) pass on all 8 ranks.
- `ruff`, `ruff format` and `mypy` (pre-commit) are clean.

Test counts as passed/skipped/failed, main -> this PR, on main at
9f5c44ea10 unless noted:

| GPU | `test_cake_kda_train_kcp.py` | `test_cake_kda_train_kcp_dist.py`
| `test_cake_kda_train_api.py` |
|---|---|---|---|
| GB200 (sm_100a) | 697/0/0 -> 722/0/0 | 14/3/0 -> 23/3/0 | 11 -> 12 |
| GB300 (sm_103a) | 697/0/0 -> 722/0/0 | previous base: 14/3/0 -> 23/3/0
| previous base: 11 -> 12 |
| R200 (sm_107a) | previous base (same commits, before #7840): 697/0/0
-> 722/0/0 | previous base: 14/3/0 -> 23/3/0 | previous base: 11 -> 12 |

- The 3 skips in the dist file are existing upload rows that need 8 GPUs
and were run on 4-GPU nodes.
- New test ids: +25, +9 and +1. None were removed.
- The conv KCP test files are unchanged and pass on all three GPUs on
the previous base (38, 8, 11, 3, 7 + 3 skipped).

## Limits
- Asymmetric handle use across ranks is documented but not checked.
- `graph="replay"` is refused with a handle.
- Phase detection uses the private torch binding
`torch._C._current_graph_task_id`, which was checked on torch 2.14.1.
- Full-model timing at CP8/CP16 is being measured, and the results will
be posted on #7815.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added checkpoint recomputation handles for KCP training. Recompute can
reuse saved incoming states to avoid repeating state exchanges while
preserving outputs and gradients.
* Choose a `"states"` or `"transfer"` retention tier, and query
estimated saved-memory and communication costs for each tier.
* Handles require consistent use across ranks and are unavailable with
certain execution modes, including graph replay and ring exchange for
the `"transfer"` tier.
* **Documentation**
* Added guidance on retention options, handle use, and configuration
requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [76eb3f6](https://github.com/flashinfer-ai/flashinfer/commit/76eb3f629f05d89a273d6aa9a9527b2281316213)

- **作者**: Sam
- **时间**: 2026-10-29T23:03:36Z
- **提交信息**: perf(gemm): launch FP4/MXFP8/SVDQuant CUTLASS GEMMs and CUTLASS MLA without re-initializing (#6282)

<!-- .github/pull_request_template.md -->

## 📌 Description

Seven CUTLASS launchers call `initialize(args, workspace, stream)` and
then `run(args, workspace, stream, ...)`. That `run` overload
initializes again before it launches (`gemm_universal_adapter.h`, and
`sm100_mla.hpp` for MLA), so every call builds its TMA descriptors
twice. The GEMM adapters also set the kernel's dynamic shared memory
attribute twice; the MLA adapter skips that on re-initialization
(`is_initialized()`, `sm100_mla.hpp`), so for MLA only the descriptor
work is duplicated. This PR launches the params the first `initialize`
stored, the way `fp8_gemm_template_sm100.h` and
`bf16_gemm_template_sm100.h` already do:

```diff
   auto initStatus = gemm.initialize(args, workspace, stream);
-  auto runStatus = gemm.run(args, workspace, stream, nullptr, /*enablePDL=*/true);
+  auto runStatus = gemm.run(stream, nullptr, /*enablePDL=*/true);
```

Changed: `fp4_gemm_template_sm100.h`, `fp4_gemm_template_sm103.h`,
`fp4_gemm_template_sm120.h`, `mxfp8_gemm_template_sm100.h`,
`mxfp8_gemm_template_sm120.h`, `nvfp4_svdquant_gemm_template_sm100.h`,
`attention/cutlass_mla.cuh`. A search of `include/` and `csrc/` found no
other launcher that initializes and then calls `run(args, ...)`.

The kernel, its arguments, workspace initialization and the PDL flag are
unchanged. Only the second, identical `initialize` is gone.

Host cost only shows when it exceeds the kernel, i.e. eager small-M
GEMMs without CUDA graphs (#4674 makes the same argument one layer up,
for the Python dispatch path). GPU time is untouched, except for the
SM120 FP4 StreamK tactics: their `initialize` zeroes the barrier
workspace with `cudaMemsetAsync`, so the second `initialize` also queued
a second memset. @waynehacking8 measured an isolated call at M=4 going
from 10.14 to 9.31 µs on an RTX PRO 6000 Blackwell Max-Q
([comment](https://github.com/flashinfer-ai/flashinfer/pull/6282#issuecomment-6236757523)).

### Per-call CUDA API work (counted by an LD_PRELOAD shim around cudart)

| launcher | GPU | `cudaFuncSetAttribute` | `cuTensorMapEncodeTiled` |
|---|---|--:|--:|
| fp4 / mxfp8, SM100 template | B200 (SM100), Thor (SM110) | 3 → 2 | 18
→ 9 |
| fp4, SM103 template | B300 (SM103) | 3 → 2 | 16 → 8 |
| fp4 / mxfp8, SM120 template | DGX Spark GB10 (SM121) | 2 → 1 | 10 → 5
|
| nvfp4 svdquant | B200 (SM100) | 3 → 2 | 26 → 13 |
| cutlass_mla | Thor (SM110) | 1 → 1 | 40 → 20 |

### Host enqueue time (bf16 out, M=64 N=4096 K=1536)

Enqueue rate over 200 calls with no per-call sync, median of 15. Run the
script below on the base and on this branch in separate processes. Each
number is the median of 3 alternating rounds.

| GPU | fp4 runner | mxfp8 runner | svdquant module call (rank 32) |
`torch._scaled_mm` fp8 |
|---|--:|--:|--:|--:|
| B200 (SM100, Modal) | 12.9 → **10.3 µs** | 12.2 → **9.7 µs** | 13.0 →
**9.5 µs** | 7.2 µs |
| B300 (SM103, Modal) ¹ | 19.6 → **16.5 µs** | 18.8 → **17.6 µs** | 20.6
→ **14.5 µs** | 11.8–15.4 µs |
| Thor (SM110) | 20.5 → **16.4 µs** | 19.2 → **15.0 µs** | — | 13.2 µs |
| DGX Spark GB10 (SM121) | 10.9 → **8.5 µs** | 10.0 → **7.7 µs** | — |
7.5 µs |

Rounds varied by up to 0.2 µs on B200, 0.4 µs on Thor and 0.1 µs on
GB10.

¹ The B300 host was noisy. The unchanged `torch._scaled_mm` reference
itself moved by 3.6 µs between rounds. Every "after" number is lower
than its "before", but the size of the B300 deltas is within that noise.
B200 and B300 ran on different Modal hosts, so only compare before/after
within a row.

CUTLASS MLA, through
`BatchMLAPagedAttentionWrapper(backend="cutlass").run` (batch 1, 128
heads, kv_len 1024, page 16): Thor 70.6 → **65.9 µs**, B200 35.2 →
**33.4 µs**. Rounds varied by up to 2.4 µs. Most of the wrapper's time
is Python, so the descriptor work this PR removes is a smaller share
there.

<details><summary>host_enqueue.py</summary>

```python
import statistics
import time

import torch
import flashinfer
from flashinfer import SfLayout, nvfp4_quantize
from flashinfer.fp8_quantization import mxfp8_quantize
from flashinfer.gemm import gemm_base

M, N, K = 64, 4096, 1536
CALLS, REPEATS = 200, 15


def enqueue_us(fn):
    for _ in range(50):
        fn()
    torch.cuda.synchronize()
    samples = []
    for _ in range(REPEATS):
        start = time.perf_counter()
        for _ in range(CALLS):
            fn()
        samples.append((time.perf_counter() - start) / CALLS * 1e6)
        torch.cuda.synchronize()
    return statistics.median(samples)


cc = torch.cuda.get_device_capability()
x = torch.randn(M, K, device="cuda", dtype=torch.bfloat16)
w = torch.randn(N, K, device="cuda", dtype=torch.bfloat16)
out = torch.empty(M, N, device="cuda", dtype=torch.bfloat16)
workspace = torch.empty(32 << 20, device="cuda", dtype=torch.uint8)

one = torch.ones(1, device="cuda")
a4, a4_sf = (t.view(torch.uint8) for t in nvfp4_quantize(x, one, sfLayout=SfLayout.layout_128x4, do_shuffle=False))
w4, w4_sf = (t.view(torch.uint8) for t in nvfp4_quantize(w, one, sfLayout=SfLayout.layout_128x4, do_shuffle=False))
fp4 = gemm_base.get_cutlass_fp4_gemm_module(*cc).cutlass_fp4_gemm_runner()
fp4_inputs = [a4, w4.T, a4_sf, w4_sf.T, one, torch.bfloat16, out, 16, True, workspace]

a8, a8_sf = mxfp8_quantize(x, sf_swizzle_layout=SfLayout.layout_128x4)
w8, w8_sf = mxfp8_quantize(w, sf_swizzle_layout=SfLayout.layout_128x4)
mxfp8 = gemm_base.get_cutlass_mxfp8_gemm_module(cc[0]).cutlass_mxfp8_gemm_runner()
mxfp8_inputs = [a8, w8.T, a8_sf, w8_sf, torch.bfloat16, out, workspace]

x8, w8_e4m3 = x.to(torch.float8_e4m3fn), w.to(torch.float8_e4m3fn)
unit = torch.ones((), device="cuda")
print(f"{torch.cuda.get_device_name()} sm_{cc[0]}{cc[1]}, M={M} N={N} K={K}, host enqueue us/call:")
print(f"  cutlass fp4 runner    {enqueue_us(lambda: fp4(inputs=fp4_inputs, tactic=-1)):6.1f}")
print(f"  cutlass mxfp8 runner  {enqueue_us(lambda: mxfp8(inputs=mxfp8_inputs, tactic=-1)):6.1f}")
print(f"  torch._scaled_mm fp8  {enqueue_us(lambda: torch._scaled_mm(x8, w8_e4m3.T, unit, unit, out_dtype=torch.bfloat16)):6.1f}")

if cc[0] in (10, 11):
    pages, page_size, seq_len = 8192, 16, 1024
    q_nope = torch.randn(1, 128, 512, device="cuda", dtype=torch.bfloat16)
    q_pe = torch.randn(1, 128, 64, device="cuda", dtype=torch.bfloat16)
    ckv = torch.randn(pages, page_size, 512, device="cuda", dtype=torch.bfloat16)
    kpe = torch.randn(pages, page_size, 64, device="cuda", dtype=torch.bfloat16)
    kv_len = torch.full((1,), seq_len, device="cuda", dtype=torch.int32)
    page_table = torch.randint(0, pages, (1, seq_len // page_size), device="cuda", dtype=torch.int32)
    mla = flashinfer.mla.BatchMLAPagedAttentionWrapper(torch.empty(128 << 20, device="cuda", dtype=torch.int8), backend="cutlass")
    mla_out = torch.empty_like(q_nope)
    print(f"  cutlass MLA wrapper   {enqueue_us(lambda: mla.run(q_nope, q_pe, ckv, kpe, out=mla_out, kv_len=kv_len, page_table=page_table)):6.1f}  (batch 1, 128 heads, kv_len {seq_len}, page {page_size})")

if cc[0] == 10:
    from flashinfer.gemm.gemm_svdquant import DEFAULT_WORKSPACE_SIZE, get_nvfp4_svdquant_module

    rank = 32
    x_scale = ((448.0 * 6.0) / x.float().abs().max()).reshape(1)
    w_scale = ((448.0 * 6.0) / w.float().abs().max()).reshape(1)
    sq_x, sq_x_sf = (t.view(torch.uint8) for t in nvfp4_quantize(x, x_scale, sfLayout=SfLayout.layout_128x4, do_shuffle=False))
    sq_w, sq_w_sf = (t.view(torch.uint8) for t in nvfp4_quantize(w, w_scale, sfLayout=SfLayout.layout_128x4, do_shuffle=False))
    sq_alpha = (1.0 / (x_scale * w_scale)).float()
    lora_down = torch.randn(M, rank, device="cuda", dtype=torch.bfloat16)
    lora_up = torch.randn(N, rank, device="cuda", dtype=torch.bfloat16)
    bias = torch.randn(N, device="cuda", dtype=torch.bfloat16)
    svdquant = get_nvfp4_svdquant_module()
    sq_workspace = torch.empty(DEFAULT_WORKSPACE_SIZE, device="cuda", dtype=torch.uint8)
    args = (sq_x, sq_w, sq_x_sf.reshape(-1), sq_w_sf.reshape(-1), sq_alpha, lora_down, lora_up, bias, out, sq_workspace, 0, True)
    print(f"  svdquant module call  {enqueue_us(lambda: svdquant.nvfp4_svdquant_gemm(*args)):6.1f}  (rank {rank}, tactic 0)")
```
</details>

`benchmarks/flashinfer_benchmark.py --routine mm_fp4 --backends cutlass
--use_128x4_sf_layout --use_nvfp4 --refcheck` on GB10 shows unchanged
GPU time with CUDA graphs: 0.019 / 0.245 / 0.050 / 0.039 ms before vs
0.019 / 0.248 / 0.052 / 0.038 ms after, for (m,n,k) = (64,4096,1536),
(64,21888,4096), (272,4096,4096), (512,1024,7168).

### Verification

The before and after builds were compiled side by side from identical
sources. The only difference was the changed headers, with separate
`FLASHINFER_WORKSPACE_BASE` so the JIT caches could not mix.

- **Bitwise:** outputs are identical for every advertised tactic. Each
case ran 3 times and matched run to run. A corrupted-output control was
detected.
  - fp4 SM100 (Thor): 7 shapes × 32 tactics.
  - fp4 SM103 (B300): 7 shapes × 63 tactics.
  - fp4 SM120 (GB10): 7 shapes × 32 tactics.
  - mxfp8 SM100 (Thor): 5 shapes × 32 tactics.
  - mxfp8 SM120 (GB10): 5 shapes × 6 tactics.
  - nvfp4 svdquant SM100 (B200): 4 (m, n, k, rank) shapes × 27 tactics.
  - cutlass_mla (Thor): 4 (batch, seq_len, page_size) cases.
- **Unit tests:** before and after give the same results, with no
failures.
  - `tests/gemm/test_mm_fp4.py` on Thor and GB10.
- `tests/gemm/test_nvfp4_svdquant_gemm.py -k per_tactic` (8 passed) on
B200.
  - `tests/gemm/test_mm_mxfp8_sm120.py` (228 passed) on GB10.
- `tests/gemm/test_mm_mxfp8.py` +
`tests/attention/test_cutlass_mla_fp8_output.py` with `-k "cutlass and
not True"` (306 passed) on Thor. Autotune-on cases were filtered out for
time.
- **compute-sanitizer:**
- `memcheck` reports only the 34 `cuGetProcAddress_v2` lookups that
happen during `import flashinfer`. The count is the same before and
after, and the same with no GEMM at all. No device frames.
  - `initcheck` is clean.
  - Both were run on Thor and GB10 only.

### Not run

- `tests/gemm/test_mm_fp4_sm103.py` passed on B300 with the base build
(2 passed). With this branch it did not finish inside my time budget,
because of the JIT compile. The SM103 change is covered by the bitwise
comparison above.

### Possible follow-up

Each launcher spells out the `get_workspace_size` / `can_implement` /
`initialize` / `run` sequence by hand, which is how this crept in. A
shared helper, e.g. `launch(op, args, workspace, bytes, stream, pdl,
name)`, would make the order impossible to get wrong. I kept that out of
this PR to keep the diff minimal.

## 🔍 Related Issues

None. Related in spirit: #4674 and #3873, which reduce per-call host
overhead in the Python GEMM dispatch path.

## 🚀 Pull Request Checklist

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

## 🔬 Experimental Track

- [ ] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #

## Reviewer Notes

No new tests: the existing tests cover these launchers, and the change
has no observable output difference to test against.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Improvements**
* Updated attention and FP4, MXFP8, and NVFP4 GEMM operations to launch
through their configured execution streams. The GEMM launches now enable
programmatic dependent launch (PDL). Existing workspace handling,
validation, and error reporting remain unchanged. These updates apply
across supported GPU architectures and preserve existing operation
interfaces.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [b52749f](https://github.com/flashinfer-ai/flashinfer/commit/b52749f059a3548d6a3148f9842cdf7e89edd072)

- **作者**: Netanel Haber
- **时间**: 2026-10-29T22:42:13Z
- **提交信息**: [SDSA 2/6][Attention] Add key unions and masks for token-sparse attention on dense kernels (#6421)

Query tokens that are near each other often select many of the same
keys. For example, the prefill tokens of one request do this.

This PR adds `group_union_masks`. It lets a dense attention kernel that
takes a mask for each query run token-sparse attention:
- For each group of consecutive tokens, it writes the union of their
keys, as cache rows in key order.
- For each token, it writes a bitmask over the union of its group.
- Each group then runs as one varlen entry of the dense kernel.

For example, take one group of 2 tokens, where token 0 uses keys 3 and
9, and token 1 uses keys 9 and 12:
```
union = [[row of key 3, row of key 9, row of key 12]]
mask  = [[0b011],   # token 0: union columns 0 and 1
         [0b110]]   # token 1: union columns 1 and 2
```

This PR also rewrites the token-sparse design doc in plain words.

This PR is part 2 of 6 of SDSA: sparse attention with a one-head indexer
and an MQA core. The indexer selects the Top-K keys of each query token,
and the MQA core attends to these keys. Parts 1-2 add token-sparse
attention, and parts 3-6 add the indexer. The previous part, #6420, is
merged. The next part is #6422.

I used AI assistance.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added group-union mask generation for token-sparse attention,
producing per-group unions of valid key positions and per-token masks.
- Out-of-range positions are skipped. The feature supports CUDA graph
replay and configurable group sizes and key-context limits.

- **Documentation**
- Expanded the design documentation with guidance on token-sparse decode
and group-union masks, including supported inputs, limits, dispatch
behavior, and validation coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Netanel Haber <nhaber@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [854a896](https://github.com/flashinfer-ai/flashinfer/commit/854a896b3f3170417eb6b0a7b798f7c8602cc8d6)

- **作者**: Kaixi
- **时间**: 2026-10-29T22:41:38Z
- **提交信息**: fix(gemm): order the TMEM and DSMEM hand-offs of the cluster split-K BF16 GEMM (#7443)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes three synchronization defects in the cluster split-K BF16 GEMM
(`flashinfer/gemm/kernels/dense_bf16_gemm_sm100_splitk.py`, a runner of
`mm_bf16(backend="cute-dsl")`):

1. **TMEM freed before the epilogue reads it (#6786).** The MMA warp
made its `bar_tmem_alloc` release arrival and then waited on parity 1,
without first waiting for phase 0. If two or more epilogue warps had not
yet made their phase-0 arrival, that release arrival counted toward
phase 0. The parity-1 wait then returned at once, because `phaseParity`
names the current or the immediately preceding phase (PTX ISA,
`mbarrier.try_wait`), and `tcgen05.dealloc` ran early. The MMA warp now
waits for phase 0 first.
2. **Cluster-scope acquire of the peer partials.** The owner CTA waited
for the peers' `st.async` partials at the default `.acquire.cta`. Their
complete-tx releases at `.cluster` scope, which a `.cta` acquire does
not synchronize with. The owner now waits with
`mbarrier.try_wait.parity.acquire.cluster`.
3. **tcgen05 fences.** Every mbarrier hand-off of tcgen05 work now has
`tcgen05.fence::before_thread_sync` before the arrival and
`tcgen05.fence::after_thread_sync` after the wait, following the PTX
ISA's canonical tcgen05 synchronization patterns.

Tiles, K slices, MMA order, reduction order and rounding are unchanged,
so outputs are bitwise identical to main (checked at the 20 shapes
below).

**Repro** (script in #6786). It runs copies of the kernel with two
test-only edits: two epilogue warps sleep ~100 µs before their phase-0
arrival, and the launch requests only the SMEM the tactic uses, so CTAs
share an SM. On main, 20/20 launches return wrong results (max |err|
7.5); with this PR, 0/20. Each edit alone gives 0/20 on both. Without
the injected delay no failure was observed on GB300: the shipped launch
requests the full per-CTA SMEM, so nothing can reuse the freed TMEM
columns. Fixes 2 and 3 are memory-model conformance with no observed
effect.

**Perf** (GB300): no measurable cost. Each measurement is a CUDA-graph
replay of 20 back-to-back PDL launches, with both kernels in one
process, interleaved ABBA, at the default tactic. Over 20 shapes × 3
runs the median delta is +0.000 µs, and 47 of 60 deltas are within ±0.02
µs. The largest, at 7168×2048 M=32 (+0.08 / +0.08 / +0.12 µs, ≤ 1.8 %),
did not reproduce in a separate 16-round run on 4 GPUs (+0.00 to +0.01
µs). In that run, two separately loaded copies of the unchanged kernel
differed by up to 0.04 µs.

<details><summary>Per-shape times (median of 3 runs, µs per
GEMM)</summary>

| N x K | M | tactic (mma_m, mma_n, split_k, stages) | main | this PR |
delta per run |
|---|---|---|---|---|---|
| 256 x 6144 | 1 | (64, 8, 4, 12) | 3.077 | 3.078 | +0.000, +0.000,
+0.001 |
| 256 x 6144 | 8 | (64, 8, 4, 12) | 3.083 | 3.079 | +0.011, -0.095,
-0.004 |
| 256 x 6144 | 16 | (64, 8, 4, 12) | 3.178 | 3.178 | +0.001, +0.000,
+0.000 |
| 256 x 6144 | 32 | (64, 8, 4, 12) | 3.181 | 3.181 | +0.000, +0.000,
+0.000 |
| 1024 x 6144 | 1 | (128, 8, 4, 6) | 4.001 | 3.997 | -0.103, -0.003,
-0.003 |
| 1024 x 6144 | 8 | (128, 8, 4, 6) | 4.202 | 4.200 | -0.001, -0.002,
-0.002 |
| 1024 x 6144 | 16 | (128, 16, 4, 5) | 4.924 | 4.924 | +0.001, -0.003,
+0.003 |
| 1024 x 6144 | 32 | (64, 32, 2, 9) | 5.328 | 5.329 | +0.004, +0.001,
-0.001 |
| 2112 x 7168 | 1 | (128, 8, 4, 6) | 4.411 | 4.410 | +0.002, -0.001,
-0.001 |
| 2112 x 7168 | 8 | (128, 8, 4, 6) | 4.610 | 4.611 | +0.003, +0.001,
+0.000 |
| 2112 x 7168 | 16 | (128, 16, 4, 5) | 5.509 | 5.532 | +0.001, +0.045,
+0.023 |
| 2112 x 7168 | 32 | (64, 32, 2, 9) | 6.084 | 6.050 | +0.000, -0.023,
-0.036 |
| 4096 x 4096 | 1 | (64, 8, 2, 12) | 4.325 | 4.327 | +0.002, +0.002,
+0.001 |
| 4096 x 4096 | 8 | (64, 8, 2, 12) | 4.193 | 4.193 | -0.002, -0.003,
+0.000 |
| 4096 x 4096 | 16 | (64, 16, 2, 11) | 4.505 | 4.511 | +0.007, +0.004,
+0.006 |
| 4096 x 4096 | 32 | (64, 32, 2, 9) | 4.925 | 4.925 | +0.000, +0.000,
-0.001 |
| 7168 x 2048 | 1 | (64, 8, 2, 12) | 5.623 | 5.628 | +0.001, +0.007,
+0.005 |
| 7168 x 2048 | 8 | (64, 8, 2, 12) | 5.336 | 5.339 | +0.025, -0.002,
+0.002 |
| 7168 x 2048 | 16 | (64, 16, 2, 11) | 5.847 | 5.877 | +0.055, +0.021,
+0.032 |
| 7168 x 2048 | 32 | (64, 32, 2, 9) | 6.819 | 6.942 | +0.075, +0.075,
+0.123 |

</details>

## 🔍 Related Issues

Fixes #6786

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

On GB300 (CUDA 13.0, torch 2.14.1+cu130, nvidia-cutlass-dsl 4.8.0):
- New `tests/gemm/test_mm_bf16_cute_dsl_splitk_sync.py` (split_k 2/3/4 ×
M 1/8/17/32): 12 passed. Each case runs 500 CUDA-graph replays and 20
eager rounds of 16 PDL launches, compares every launch bitwise with the
first, and checks the first against an FP64 reference.
- `tests/gemm/test_mm_bf16.py`: 27 passed, 4 skipped.
`tests/gemm/test_bmm_bf16.py`: 273 passed, 97 skipped. Both are
identical to main; the skips are cuTile not installed, TGV non-BF16
output, and cuDNN FP16 output on SM103.

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

- The new test also passes on main: it guards bitwise-stable replays and
is not a repro, because the race needs an injected delay (see #6786).
The test calls `run_splitk_dense` with explicit tactics, since
`mm_bf16(backend="cute-dsl")` reaches this kernel only through
autotuning.
- Fences: the PTX patterns spell out the MMA-done → `tcgen05.ld` and
`tcgen05.ld` → TMEM release → `tcgen05.dealloc` hand-offs. The
TMEM-pointer and operands-full → MMA hand-offs are fenced the same way,
for one uniform form at no measurable cost.
- The two new helpers use inline PTX, like the file's existing `mapa` /
`st.async` helpers. The wait loop has the same form as CUTLASS's
`ClusterBarrier::wait`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved the consistency of split-K BF16 GEMM results across repeated
CUDA graph replays and eager launches.
* Updated synchronization for split-K computations to help ensure
results remain stable across supported hardware, including SM100, SM103,
and SM107.
* Verified stability across multiple matrix sizes and split-K
configurations, with repeated runs using different activation functions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: coderabbitai[bot] <136622811+coderabbitai[bot]@users.noreply.github.com>

### [4b1cea6](https://github.com/flashinfer-ai/flashinfer/commit/4b1cea665f48da65a37c7222280fc2f00d9a83cb)

- **作者**: orbiri
- **时间**: 2026-10-29T22:34:41Z
- **提交信息**: fix(moe): offer expert-parallel tile_N candidates to the TRT-LLM-gen MoE autotuner (#6542)

## 📌 Description

Under expert parallelism (EP), the TRT-LLM-gen MoE autotuner is never
offered the small tile that decode-sized batches
need. This PR offers it, under EP only.

**Problem.** The launchers offer the `tile_N` values around `num_tokens
* top_k / num_local_experts`. An EP caller often
passes every row the rank received, with global expert ids (for example
after a one-sided all-to-all), so the estimate is
too large by up to `num_experts / num_local_experts`. Example: 128
experts, top-8, EP4, 256 tokens per rank. The launcher
assumes 256 rows per expert and offers only `{128, 192, 256}`, but the
real mean is 64.

**Fix.** Also pass the global `num_experts`. When `num_experts >
num_local_experts`, keep today's tiles (with the tuner
window from #6788) and add one: the tile covering `num_tokens * top_k /
num_experts`, if it is below all of today's tiles.
In the example, the set becomes `{64, 128, 192, 256}`. The launcher
cannot tell whether the rows were already filtered to
local experts, so it keeps today's set and lets the autotuner measure
the extra tile. The change applies to all six
launchers that share `computeSelectedTileN`: BF16, FP8 ×3, MxInt4 and
FP4.

**Why it is safe.**
- **No EP** (TP, TEP, single GPU): the candidates, and so the tuning,
are exactly today's.
- **EP:** today's set plus at most one tile, and only one below today's
smallest. It never adds tile 192 (on every ladder
that has 192, today's smallest tile is at most 128), so EP + `gemm1`
LoRA cannot newly break.
- **Untuned fallback** (`selectDefaultTileN`, tactic `-1`): unchanged.
- **Output:** bitwise identical to main, and across every tactic
(Tests).
- **API:** two internal module bindings, `trtllm_get_valid_moe_configs`
and `trtllm_get_valid_moe_factorizations`, gain one
positional argument after `num_local_experts`. Every in-tree caller is
updated. No public Python API changes.

**Performance.** GB300, NVFP4 `trtllm_fp4_block_scale_moe`,
`benchmarks/flashinfer_benchmark.py --autotune` with the
default `tune_max_num_tokens` (8192), CUPTI timing, four runs per build.
Tile = the `tile_N` the autotuner picked. The
launcher's estimate is too large by the EP size, and the gains are
larger at EP16 to EP64 than at EP4 / EP8. The largest
is at Qwen3-235B EP16 with 32 tokens per rank. There are about 32 rows
per expert, but main offers only
`{128, 192, 256}`. This PR adds 32, and the MoE takes 40.88 µs instead
of 46.89 µs (0.872). This PR adds a tile at 18 of the 29
measured points (EP4 to EP64, and no EP). At six of them it was faster
by more than 3× the run-to-run spread:

| Model | EP, tokens per rank | main µs (tile) | this PR µs (tile) |
this PR / main |
|---|---|---|---|---|
| Qwen3-235B | EP16, 32 | 46.89 (128) | 40.88 (32) | **0.872** |
| Qwen3-235B | EP64, 8 | 33.85 (128) | 30.11 (32) | **0.890** |
| Qwen3-235B | EP32, 8 | 34.13 (128) | 30.49 (16) | **0.893** |
| DeepSeek-V3 | EP16, 32 | 104.83 (128) | 98.75 (16) | **0.942** |
| Qwen3-235B | EP8, 128 | 65.56 (128) | 61.81 (64) | **0.943** |
| DeepSeek-V3 | EP16, 128 | 119.52 (128) | 116.85 (64) | **0.978** |
| DeepSeek-V3 | EP32, 32 | 73.84 (128) | 70.04 (32) | 0.949 |
| Qwen3-235B | EP4, 256 | 95.68 (128) | 92.04 (64) | 0.962 |
| DeepSeek-V3 | EP8, 128 | 166.40 (128) | 162.86 (32) | 0.979 |

- **Bold** = changed by more than 3× the run-to-run spread, with every
run of this PR faster than every run of main.
- DeepSeek-V3 EP32, 32: every run of this PR was faster than every run
of main (0.941 to 0.966 run by run). One run of main
measured 72.58 µs, against 74.24 to 74.29 µs in the other three. That
widened the spread, so the change (5.1 %) is
  under 3× the spread (8.3 %).
- DeepSeek-V3 EP8, 128: every run of this PR was faster than every run
of main (0.976 to 0.982 run by run), but the
  change is just under 3× the spread (2.12 % vs 2.15 %).
- Qwen3-235B EP4, 256: 0.947 to 0.952 in three runs. In the fourth, this
PR measured 95.73 µs with the same tile and
  config as the third run (90.78 µs). The cause is not established.

The other 20 points did not change by more than 3× the spread (0.975 to
1.008). They include all 4 without EP and one
EP16 point where this PR adds no tile. None was slower by that rule. The
added tile helped little where main already
offers a small one (Qwen3-235B EP16, 8 tokens per rank: main offers 32,
0.975; DeepSeek-V3 EP16, 8: 16, 1.000). At
DeepSeek-V3 EP32, 8 the autotuner kept 128 (0.995). Where 64 is added
(Qwen3-235B EP32, 32 and DeepSeek-V3 EP64, 32), it
picked 64 in only 1 and 3 of 4 runs, and the time did not change (0.985,
0.996). The EP4 / EP8 and the EP16 / 32 / 64
points were measured in two sessions on different GB300 nodes, with the
same builds and method. The full tables are in
the details below.

**Tuning cost.** Autotune wall time in seconds for the first call of
each shape, which tunes every bucket up to 8192
(mean of four runs):

| Shape | main | this PR |
|---|---|---|
| Qwen3, EP4 | 33.9 | 32.7 |
| Qwen3, EP8 | 27.4 | 31.1 |
| Qwen3, no EP | 85.9 | 83.5 |
| DeepSeek-V3, EP4 | 75.5 | 76.6 |
| DeepSeek-V3, EP8 | 51.3 | 61.5 |
| DeepSeek-V3, no EP | 355.1 | 352.5 |
| Qwen3, EP16 | 27.8 | 30.2 |
| Qwen3, EP32 | 22.1 | 27.2 |
| Qwen3, EP64 | 20.1 | 23.5 |
| DeepSeek-V3, EP16 | 44.3 | 54.1 |
| DeepSeek-V3, EP32 | 37.6 | 48.5 |
| DeepSeek-V3, EP64 | 31.5 | 40.8 |

Tuning takes at most 10.9 s (1.3×) longer, only under EP; without EP it
is unchanged. An earlier version of this PR
offered the whole window around the global estimate as well. Measured
separately on GB300, it picked the same tiles at the
three points above but took 1.5 to 2.3× main's tuning time under EP
(DeepSeek-V3 EP8: 119.0 s vs 51.1 s).

<details><summary>Method, full results and repro commands</summary>

- **Method.** Each value is the mean of four runs; each run is the
median of 200 iterations. The two builds alternated on
the same GPU (main / this PR, four times). Each model and EP size ran as
one process: its first point tunes every
bucket, and the later points reuse those results. Routing logits are
random, so routing is near-uniform; real routing is
  skewed, so gains in serving may differ.
- **Spread** = (max − min of the four run medians) / mean, at least 0.10
µs.
- **Code measured:** this PR and its base, main f8664bf0 (which includes
#6788), on GB300 (sm_103).
- `num_tokens` = EP × tokens per rank; local experts = experts / EP.
Where the picked tile varied, the tile of each run is
shown. At DeepSeek-V3 EP4, 256 tokens per rank both builds offer the
same tiles; this PR's 0.996 there is its first run
picking 64 (276.69 µs) where every other run of either build picked 32.

Qwen3-235B-A22B MoE (hidden 4096, intermediate 1536, 128 experts, top-8,
`renormalize`):

| Setup | `num_tokens` | local experts | main µs (tile) | this PR µs
(tile) | this PR / main |
|---|---|---|---|---|---|
| EP4, 32 tok/rank | 128 | 32 | 80.62 (16) | 80.57 (16) | 0.999 |
| EP4, 128 tok/rank | 512 | 32 | 86.77 (32) | 86.49 (32) | 0.997 |
| EP4, 256 tok/rank | 1024 | 32 | 95.68 (128) | 92.04 (64) | 0.962 |
| EP8, 32 tok/rank | 256 | 16 | 55.19 (32) | 55.11 (16 / 16 / 32 / 16) |
0.999 |
| EP8, 128 tok/rank | 1024 | 16 | 65.56 (128) | 61.81 (64) | **0.943** |
| EP8, 256 tok/rank | 2048 | 16 | 73.69 (128) | 74.30 (128) | 1.008 |
| no EP | 128 | 128 | 224.10 (8) | 223.86 (8) | 0.999 |
| no EP | 1024 | 128 | 251.36 (64) | 251.26 (64) | 1.000 |

DeepSeek-V3 MoE (hidden 7168, intermediate 2048, 256 experts, top-8,
`deepseek_v3` routing, n_group 8, topk_group 4,
routing bias):

| Setup | `num_tokens` | local experts | main µs (tile) | this PR µs
(tile) | this PR / main |
|---|---|---|---|---|---|
| EP4, 32 tok/rank | 128 | 64 | 255.04 (16 / 16 / 8 / 16) | 255.55 (8 /
8 / 8 / 16) | 1.002 |
| EP4, 128 tok/rank | 512 | 64 | 266.88 (32) | 267.66 (32) | 1.003 |
| EP4, 256 tok/rank | 1024 | 64 | 279.93 (32) | 278.81 (64 / 32 / 32 /
32) | 0.996 |
| EP8, 32 tok/rank | 256 | 32 | 150.78 (16 / 16 / 32 / 16) | 150.14 (16)
| 0.996 |
| EP8, 128 tok/rank | 1024 | 32 | 166.40 (128) | 162.86 (32) | 0.979 |
| EP8, 256 tok/rank | 2048 | 32 | 178.43 (128) | 179.01 (128) | 1.003 |
| no EP | 128 | 256 | 895.69 (8) | 895.48 (8) | 1.000 |
| no EP | 1024 | 256 | 958.90 (64) | 958.86 (64) | 1.000 |

EP16 / 32 / 64, same two models. At 8 to 256 tokens per rank (up to 8192
tokens), this PR adds a tile at 12 of 22 points.
At the other 10, the mean is at least 128 rows per expert and both
builds offer `{128, 192, 256}`. The table has the 12
points and one of the 10:

| Model | Setup | `num_tokens` | local experts | main µs (tile) | this
PR µs (tile) | this PR / main |
|---|---|---|---|---|---|---|
| Qwen3-235B | EP16, 8 tok/rank | 128 | 8 | 37.50 (32) | 36.56 (8) |
0.975 |
| Qwen3-235B | EP16, 32 tok/rank | 512 | 8 | 46.89 (128) | 40.88 (32) |
**0.872** |
| Qwen3-235B | EP16, 128 tok/rank (no tile added) | 2048 | 8 | 58.61
(128) | 59.03 (128) | 1.007 |
| Qwen3-235B | EP32, 8 tok/rank | 256 | 4 | 34.13 (128) | 30.49 (16) |
**0.893** |
| Qwen3-235B | EP32, 32 tok/rank | 1024 | 4 | 39.95 (128) | 39.37 (128 /
128 / 64 / 128) | 0.985 |
| Qwen3-235B | EP64, 8 tok/rank | 512 | 2 | 33.85 (128) | 30.11 (32) |
**0.890** |
| DeepSeek-V3 | EP16, 8 tok/rank | 128 | 16 | 88.70 (16) | 88.72 (16 / 8
/ 8 / 8) | 1.000 |
| DeepSeek-V3 | EP16, 32 tok/rank | 512 | 16 | 104.83 (128) | 98.75 (16)
| **0.942** |
| DeepSeek-V3 | EP16, 128 tok/rank | 2048 | 16 | 119.52 (128) | 116.85
(64) | **0.978** |
| DeepSeek-V3 | EP32, 8 tok/rank | 256 | 8 | 66.29 (128) | 65.94 (128) |
0.995 |
| DeepSeek-V3 | EP32, 32 tok/rank | 1024 | 8 | 73.84 (128) | 70.04 (32)
| 0.949 |
| DeepSeek-V3 | EP64, 8 tok/rank | 512 | 4 | 52.36 (128) | 51.48 (16) |
0.983 |
| DeepSeek-V3 | EP64, 32 tok/rank | 2048 | 4 | 66.13 (128) | 65.84 (64 /
64 / 64 / 128) | 0.996 |

At Qwen3-235B EP16, 128 tokens per rank, both builds offer the same
tiles and pick 128. This PR measured 0.006 to 0.010
slower in each run, within 3× the spread. A same-tile difference of this
size also appeared at DeepSeek-V3 EP4, 128
(1.003).

```bash
# main vs this PR. Run each four times, alternating builds on the same GPU.
# The tables ran each model and EP size as one --testlist file of these lines (its first point tunes every bucket).
python benchmarks/flashinfer_benchmark.py --routine trtllm_fp4_block_scale_moe --autotune --use_shuffled_weight \
  --num_iters 200 --dry_run_iters 20 \
  --hidden_size 4096 --intermediate_size 1536 --num_experts 128 --top_k 8 --routing_method renormalize \
  --local_num_experts 16 --local_expert_offset 0 --num_tokens 1024
# EP4 at 256 tok/rank: --local_num_experts 32 --num_tokens 1024; no EP: --local_num_experts 128
# EP16 at 32 tok/rank: --local_num_experts 8 --num_tokens 512; EP64 at 8 tok/rank: --local_num_experts 2 --num_tokens 512
# DeepSeek-V3 shape:
#   --hidden_size 7168 --intermediate_size 2048 --num_experts 256 --top_k 8 --n_group 8 --topk_group 4 \
#   --routed_scaling_factor 2.5 --use_routing_bias --routing_method deepseek_v3 --local_num_experts 32 --num_tokens 1024
```

</details>

## 🔍 Related Issues

- #6788 widened the autotuner window by one more smaller tile, so main
now offers tile 128 where it offered only
{192, 256}. This PR builds on it: today's tiles keep that window, and
the one added tile sits below it. On GB300, main
after #6788 is already faster than main before it at 6 of the 7 points
the first version of this PR improved; this PR
  is still faster at 3 of them (table above).
- #5534 offers every FP4 tile to fix the same problem. This PR is the
gated variant suggested in that PR's review: EP only,
never tile 192, all six launchers, one extra tile. #3998 is an earlier
draft of the same idea.
- #3537 (the autotuner is not EP/DP-aware): this PR covers only the
candidate tiles. It does not address cross-rank
  consistency or the profiling distribution.

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

- **New tests**, in the existing
`tests/moe/test_trtllm_gen_moe_autotune_tactics.py`: 12 cases, 21 s on
GB300 (17 s of
it the all-tactics case). All 12 fail on main. They check properties of
the candidates rather than restating the rule:
- `test_expert_parallel_adds_at_most_one_smaller_tile`: with
`num_experts > num_local_experts`,
`trtllm_get_valid_moe_configs` and `trtllm_get_valid_moe_factorizations`
keep every tile offered for the local count
and add at most one, smaller than all of them (3 shapes × the 2
bindings).
- `test_expert_parallel_with_lora_does_not_add_tile_192`: EP + `gemm1`
LoRA succeeds and is not offered tile 192 unless
the local count already gets it (NvFP4 and MxFP4×MxFP8; 16 and 128
tokens, 32 of 256 experts, top-8). This is the
EP + LoRA case asked for in #5534's review: 192 has no LoRA kernel
there, so offering it fails the whole query and
    leaves the autotuner with no tactics.
- `test_autotuner_queries_global_expert_count`:
`trtllm_fp4_block_scale_moe` under `autotune` is offered tile 8 at an
EP shape where main starts at 16, so the Python runner passes the global
expert count.
- `test_trtllm_fp4_routed_moe_all_tactics_correctness_expert_parallel`:
the existing all-tactics correctness sweep on
one EP shape (NvFP4, 256 tokens, 32 of 256 experts, top-8), restricted
to the tile EP adds there (tile 8, 336
    tactics); the other tiles are already swept by the non-EP cases.
- Without EP the candidates are today's by construction: the added code
runs only when
    `num_experts > num_local_experts`.
- **Existing tests:** 24 passed on main and on this PR (GB300; list
below).
- **Bitwise:** the MoE output has the same SHA-256 on main and on this
PR at all 29 points, in every run. At the 25 EP points
it is also the same for every tactic this PR offers, including `-1`: 113
to 1,009 per Qwen3 point and 209 to 1,305 per
  DeepSeek-V3 point.

<details><summary>Existing tests run</summary>

`tests/autotuner/test_trtllm_fused_moe_autotuner_integration.py`; in
`tests/moe/test_trtllm_gen_moe_autotune_tactics.py`:
`test_nvfp4_per_tensor_small_shape_all_tactics_are_correct`,
`test_fp4_block_scale_moe_fused_shared_experts_autotune`,
and the `routed_moe_all_tactics_correctness` cases for NvFP4,
MxFP4×MxFP8, DeepSeekFp8 and MxFp8.

</details>

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

- **One tile, not a window.** The earlier, wider version also offered
the other tiles around the global estimate.
Besides the tuning time, it picked tile 64 at Qwen3-235B EP8, 256 tokens
per rank, up to 2 % slower than main's 128:
the autotuner times with CUDA events, which fall on a ≈ 2 µs grid on
GB300, coarser than the gap. This PR does not add
  64 there.
- **Addition, not replacement.** Some callers already filter rows to
local experts; keeping today's tiles keeps theirs. For
those callers the extra tile is measured and rejected, which costs only
tuning time.
- **Fallback unchanged on purpose.** Feeding the global estimate to
`selectDefaultTileN` would change the untuned tile under
  EP. This PR does not measure that.
- **Persisted tuning results** from an earlier build keep their old
picks until re-tuned.
- **Not changed:** the Prims-TS copy of this policy (`_selected_tile_ns`
in `flashinfer/prims_ts/moe/config_mapper.py`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* MoE configuration selection now accounts for both global and local
expert counts, including expert-parallel workloads. This can make
additional tile configurations available when selecting tactics across
supported data types.
* Tactic queries also account for fused shared experts and GEMM1
LoRA-delta state, helping configuration results reflect the workload’s
settings.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [6238131](https://github.com/flashinfer-ai/flashinfer/commit/6238131d7e920b9c60ba336c3477c9437db520fd)

- **作者**: eigen
- **时间**: 2026-10-29T22:34:19Z
- **提交信息**: perf(cake_ulysses): faster world-8 bf16 direct scatter, early first-unit zone (#7891)

### [71f60a9](https://github.com/flashinfer-ai/flashinfer/commit/71f60a9eca3a744e98e9ddfa6654cc2d42a84cdb)

- **作者**: eigen
- **时间**: 2026-10-29T22:33:56Z
- **提交信息**: perf(cake_rmsnorm): retuned backward windows for H=512 on SM100 / SM107 and H=1536 on SM103 (#7889)

### [0f90ac4](https://github.com/flashinfer-ai/flashinfer/commit/0f90ac4b7198b18487f00bb9dfed7dafa3078835)

- **作者**: eigen
- **时间**: 2026-10-29T22:33:36Z
- **提交信息**: perf(cake_dense_projection_gemm): sm_107a rules for the N = 128 weight gradients of the 4096 / 5120 / 8192 rows (#7886)

### [437956b](https://github.com/flashinfer-ai/flashinfer/commit/437956b18b44af7b9da9904114995ac35262cbdb)

- **作者**: eigen
- **时间**: 2026-10-29T22:33:21Z
- **提交信息**: perf(cake_moe_grouped_gemm): 3 / 3 head / tail wide tile on sm_103a forward and dgrad (#7881)

### [ebdad91](https://github.com/flashinfer-ai/flashinfer/commit/ebdad91fae84cbe538cbb9dafe78d25a3a532825)

- **作者**: eigen
- **时间**: 2026-10-29T22:10:02Z
- **提交信息**: feat(cake_vsa_sm90): second Sage-FP8 grouped-query pin program, faster compact program and a short-tile queue vf tier (#7890)

FlashInfer's Cake backend for variable block-sparse attention on Hopper
(`VariableBlockSparseAttentionWrapper(backend="cake")`, sm_90a) supports
two data types, BF16 and Sage-FP8 (E4M3 inputs with per-head scales,
BF16 output), and each data type has multi-head (MHA) programs and
grouped-query programs (num_qo_heads = g × num_kv_heads, g ∈ {2, 4, 8}).
The grouped-query programs were added in #7167 and retuned in place in
#7185, #7412, #7580, #7634 and #7682; #7743 added the position-selected
Sage-FP8 grouped-query static program `attention_fp8_gqa_pin`, #7775
lowered its threshold `PIN_MIN_CTA_LOOP_ITERS` from 14 to 8, and #7832
added the second BF16 grouped-query queue program
`attention_gqa_queue_vf` with the route `QUEUE_VF_MIN_TILE_POS` = 24
ring positions and `QUEUE_VF_MIN_CTA_LOOP_ITERS` = 440 main-loop
iterations. This PR, on current main (which contains #7832), changes
three grouped-query variants. First, it adds the Sage-FP8 program
`attention_fp8_gqa_pin_vf`, which is the pin program
(`attention_fp8_gqa_pin`) with the per-position V^T wait moved from the
joint K / V^T gate before the next QK to just after the QK issue; it
waits on the same slot and generation, only later in the same iteration,
so the output bits are the pin program's. `cake_planner.py` selects it
(predicate `fp8_gqa_pin_vf`) for pair-mode pin plans of tiles of at
least `PIN_VF_MIN_TILE_POS` = 24 ring positions whose lightest CTA runs
at least `PIN_VF_MIN_CTA_LOOP_ITERS` = 40 main-loop iterations;
split-mode and shorter pin plans keep `attention_fp8_gqa_pin` byte for
byte. Its main loop is 637 instructions against the pin program's 633,
the whole program is 4216 instructions for both, and it uses 168
registers with no spills. Second, in the Sage-FP8 grouped-query compact
program `attention_fp8_gqa_compact`, the arrive that releases each V
stage back to the loader now issues one instruction after the wait that
retires the PV matrix multiply instead of 272 instructions after it, so
the loader can refill the V stage earlier; output bits are unchanged,
and the main loop goes from 627 to 633 instructions, the whole program
from 4304 to 4312, with 168 registers and no spills. Third, without a
new program, the BF16 queue vf route gets a short-tile tier: a pair-mode
BF16 grouped-query queue plan also takes `attention_gqa_queue_vf` when
its tiles have at least `QUEUE_VF_SHORT_TILE_POS` = 16 ring positions
and its lightest CTA runs at least `QUEUE_VF_SHORT_MIN_CTA_LOOP_ITERS` =
1000 main-loop iterations, while the existing tier (24 positions / 440
iterations) is unchanged. The package goes from 82 to 83 generated
kernel units, the added unit being `attention_fp8_gqa_pin_vf`; no other
unit's machine code changes, and the multi-head programs keep their
machine code byte for byte. The baseline is the previous Cake version of
this backend, the package of #7832, measured on the same node with the
same run form, on an NVIDIA H100 80GB HBM3 (Hopper, sm_90a) with the
CUDA 13.4 toolkit (JIT-compiled; PyTorch CUDA build 13.0) and driver
535.216.03: two processes, a and b, each with 9 groups × 256 samples per
row, CUPTI kernel-sum timing, cold L2 (L2 flushed before each sample)
and both interleaving orders against the same reference kernels; speedup
is previous / this. The change affects the 7 rows of the table (11
entries of the 284-row shape list, since some shapes appear in two
subsets of the list): 4 Sage-FP8 rows that now take
`attention_fp8_gqa_pin_vf` instead of `attention_fp8_gqa_pin`, 2
Sage-FP8 rows of `attention_fp8_gqa_compact` and 1 BF16 row that now
takes `attention_gqa_queue_vf` instead of `attention_gqa_queue`; every
other row keeps its program. Over the 7 affected rows the geometric-mean
speedup is 1.0097 in process a and 1.0105 in process b; per variant (a /
b) it is 1.0097 / 1.0093 for pin vf (4 rows), 1.0114 / 1.0062 for
compact (2 rows) and 1.0062 / 1.0244 for the short-tile queue vf tier (1
row). Per row the speedup spans 1.0054–1.0168 in process a and
1.0050–1.0244 in process b, and all 7 rows are faster in both processes.
The largest speedup in process a is
`h16-m8192-n8192-k5-ragged0-scale0-g4` (e4m3, compact), 48.544 → 47.744
µs (1.0168), and the smallest is `h8-m4096-n4096-k64-ragged0-scale1-g4`
(e4m3, pin vf), 98.175 → 97.647 µs (1.0054). The other-dtype rows of the
same 7 shapes run unchanged programs and measured as controls at
0.9871–1.0102 (a) and 0.9915–1.0066 (b), i.e. within run-to-run noise.
Both packages pass every one of the 284 rows against the two reference
baselines.

Grouped-query variable block-sparse attention forward, NVIDIA H100 80GB
HBM3 (Hopper, sm_90a), CUDA 13.4 toolkit (JIT-compiled; PyTorch CUDA
build 13.0), driver 535.216.03: the previous Cake version of this
backend (the package of #7832) vs this version, each measured in its own
run of the same two-process form (process a shown; 9 groups × 256
samples per row, CUPTI kernel-sum timing, cold L2, both interleaving
orders against the same reference kernels) on the same node; speedup =
previous / this.

| shape | dtype | program | previous µs | this µs | speedup |
|---|---|---|---|---|---|
| h8-m32768-n32768-k64-ragged1-scale0-g4 | e4m3 |
attention_fp8_gqa_pin_vf | 391.678 | 386.814 | 1.0126 |
| h8-m32768-n32768-k64-ragged1-scale0-g8 | e4m3 |
attention_fp8_gqa_pin_vf | 398.432 | 392.673 | 1.0147 |
| h8-m4096-n4096-k64-ragged0-scale1-g4 | e4m3 | attention_fp8_gqa_pin_vf
| 98.175 | 97.647 | 1.0054 |
| h8-m4096-n4096-k64-ragged0-scale1-g8 | e4m3 | attention_fp8_gqa_pin_vf
| 97.681 | 97.073 | 1.0063 |
| h16-m8192-n8192-k5-ragged0-scale0-g4 | e4m3 |
attention_fp8_gqa_compact | 48.544 | 47.744 | 1.0168 |
| h16-m8192-n8192-k5-ragged0-scale0-g8 | e4m3 |
attention_fp8_gqa_compact | 48.256 | 47.967 | 1.0060 |
| h12-m109632-n109632-k32-ragged0-scale0-g4 | bf16 |
attention_gqa_queue_vf | 2630.190 | 2614.078 | 1.0062 |

The other Cake variants (the BF16 and Sage-FP8 multi-head programs and
the other grouped-query programs) are unchanged by this PR, and the
family ships only on sm_90a (Hopper); other architectures have their own
Cake block-sparse attention backends.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optimized execution path for eligible FP8 grouped-query
attention workloads.
* Expanded automatic routing for BF16 grouped-query attention to include
additional queue workloads.
* **Improvements**
* Improved attention score handling for negative scaling and per-tile
data selection in applicable workloads.
* **Tests**
* Added coverage for routing decisions, output consistency, and CUDA
graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f5cb50d](https://github.com/flashinfer-ai/flashinfer/commit/f5cb50d624c9fb31202fa92092810ef05569d4c5)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-29T22:07:18Z
- **提交信息**: fix(gemm): rename 'interface' parameter in trtllm-gen GEMM runners (Windows build) (#7895)

<!-- .github/pull_request_template.md -->

## 📌 Description

On Windows, `<windows.h>` (through `objbase.h`) defines `interface` as a
macro for `struct`. Once a Windows header is in the translation unit,
`trtllm_gemm_runner.cu` stops compiling: the parameter `const
gemm::gemm::GemmInterface& interface` in `select_kernel_fp8` expands to
`... & struct`, and nvcc reports `expected a ")"` plus follow-on errors
where the parameter is used. As a result the trtllm-gen GEMM JIT module
cannot be built on Windows.

This PR renames the parameter to `gemm_interface`. It makes the same
rename in `select_kernel` in `trtllm_low_latency_gemm_runner.cu`, which
has the same pattern but does not currently pull in a Windows header.
There is no functional change.

## 🔍 Related Issues

Windows on Arm bring-up: the trtllm-gen GEMM paths do not build natively
on Windows.

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
reviewers may adjust): `tests/gemm/test_mm_fp8.py
tests/gemm/test_groupwise_scaled_gemm_fp8.py tests/gemm/test_mm_mxfp8.py
tests/gemm/test_mm_fp4.py`

Validated on a GB300 (SM103) under native Windows 11 arm64 (CUDA 13.5).
Before this change the trtllm-gen GEMM module fails to build with
`expected a ")"`. After it, `tests/gemm/test_mm_fp8.py` passes, along
with the `trtllm` cases of `test_groupwise_scaled_gemm_fp8.py`,
`test_mm_mxfp8.py` and `test_mm_fp4.py`. That Windows run also needed a
separate, Windows-only header fix that is not part of this PR. No test
is added: Linux CI cannot reproduce a Windows header macro.

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

Rename only; the two kernel-selection functions behave exactly as
before.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Updated internal naming for GEMM configuration selection across
standard and low-latency operations. This change does not alter
functionality or affect the experience of using the product.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [49e254e](https://github.com/flashinfer-ai/flashinfer/commit/49e254ebf03e8e750f60f46b335c4624576cf985)

- **作者**: S.J. Lee
- **时间**: 2026-10-29T21:58:06Z
- **提交信息**: feat(qsa): add FP8 and BF16 caches and speed up NVFP4 in the SM80-SM90 QSA kernel (#7794)

<!-- .github/pull_request_template.md -->

## 📌 Description

`qsa_sparse_paged_attention` only took NVFP4 caches on SM80–SM90. This
extends the `default` kernel in `flashinfer/experimental/qsa_nvfp4` to
FP8 e4m3 and BF16 K/V caches and speeds up its NVFP4 path.
`backend="auto"` now sends FP8 and BF16 caches there while NVFP4 still
goes to Cake.

### FP8 and BF16

The kernel is one template over the cache format. FP8 and BF16 follow
the vLLM Triton kernel's numerics: K is decoded exactly to BF16 for QK,
FP8 runs PV on FP16 operands, the per-tensor K/V scales fold into the
softmax and output scales, and BF16 ignores them. BF16 uses 32-token
tiles so its two stages stay under the 99 KB per-block shared memory of
SM86/SM89. BF16 rows aren't padded: 16-byte chunk c of token r sits at c
^ (r % 8), which keeps the reads free of bank conflicts and fits three
BF16 CTAs on an sm_90 SM instead of two. An FP8 cache stored as uint8
has to be passed as a `float8_e4m3fn` view, since uint8 means NVFP4
here.

The load path changed for all three formats. Each warp copies its own
K/V rows, reading the selection, block table and addresses a few tiles
ahead, and K and V wait separately. For FP8 and BF16 the split count
fills one wave of resident CTAs from the occupancy query instead of a
fixed target, except that BF16 stays at one CTA per SM until each split
would get eight or more tiles; its one- and two-tile splits ran slower
on sm_80 and sm_90. The merge spreads the splits over several warps and
issues each group's loads before using them; the old loop kept about
three loads in flight per thread, and at one or two rows the merge was
about half of the run time. NVFP4 merges on up to four warps. BF16 and
FP8 go up to 16, with the partial sums in dynamic shared memory sized to
the warps launched, so a row with 65 splits merges in one pass.

Kernel time with CUDA graphs on real-model shapes (head dim 256, top-k
2048, page size 3136), against the vLLM Triton kernel on the same
inputs, as the geometric mean over the 14 shapes below:

| arch | BF16 | FP8 |
|---|---|---|
| sm_80 | 0.78x | 0.80x |
| sm_89 | 0.87x | 0.78x |
| sm_90 | 0.99x | 0.94x |

FP8 on sm_89 and sm_90 goes through the `float8_e4m3fn` view vLLM hands
Triton there.

sm_90 BF16 only just gets past the line: 0.991x on 12/1 and 0.983x on
24/2, down from 1.09x and 1.07x before the merge, layout and BF16 split
changes. Up to four rows it is still slower, 1.01-1.17x. On sm_89 the
layout and merge changes cost 2-5% on mid-sized BF16 shapes (0.3% and
1.1% on the 12/1 and 24/2 means): it still fits one BF16 CTA per SM, so
it pays for the swizzle's address math without gaining a CTA. BF16 there
is still faster than Triton on every shape.

<details><summary>Per-shape times (µs)</summary>

sm_80

| heads (q/kv) | rows | Triton BF16 | ours BF16 | Triton FP8 | ours FP8
|
|---|---|---|---|---|---|
| 12/1 | 1 | 10.4 | 11.1 (1.07x) | 13.7 | 10.7 (0.78x) |
| 12/1 | 2 | 13.4 | 11.9 (0.89x) | 13.3 | 11.0 (0.82x) |
| 12/1 | 4 | 19.8 | 14.5 (0.73x) | 15.5 | 14.1 (0.91x) |
| 12/1 | 8 | 30.9 | 22.0 (0.71x) | 20.7 | 18.5 (0.90x) |
| 12/1 | 16 | 52.5 | 34.1 (0.65x) | 37.0 | 24.5 (0.66x) |
| 12/1 | 32 | 72.5 | 56.3 (0.78x) | 55.7 | 40.4 (0.73x) |
| 12/1 | 64 | 120.5 | 100.5 (0.83x) | 88.6 | 70.7 (0.80x) |
| 24/2 | 1 | 13.3 | 11.7 (0.88x) | 13.3 | 10.9 (0.82x) |
| 24/2 | 2 | 19.7 | 14.3 (0.73x) | 15.7 | 14.2 (0.91x) |
| 24/2 | 4 | 30.8 | 21.8 (0.71x) | 20.7 | 18.3 (0.88x) |
| 24/2 | 8 | 52.4 | 34.0 (0.65x) | 36.8 | 24.2 (0.66x) |
| 24/2 | 16 | 72.4 | 56.4 (0.78x) | 55.9 | 40.0 (0.72x) |
| 24/2 | 32 | 119.2 | 100.0 (0.84x) | 89.1 | 70.6 (0.79x) |
| 24/2 | 64 | 221.0 | 181.0 (0.82x) | 152.8 | 128.2 (0.84x) |

sm_89

| heads (q/kv) | rows | Triton BF16 | ours BF16 | Triton FP8 | ours FP8
|
|---|---|---|---|---|---|
| 12/1 | 1 | 10.1 | 8.3 (0.82x) | 8.8 | 8.4 (0.95x) |
| 12/1 | 2 | 26.9 | 23.7 (0.88x) | 14.2 | 9.2 (0.65x) |
| 12/1 | 4 | 49.9 | 45.6 (0.91x) | 32.1 | 24.5 (0.76x) |
| 12/1 | 8 | 99.4 | 90.4 (0.91x) | 60.4 | 46.6 (0.77x) |
| 12/1 | 16 | 248.4 | 178.3 (0.72x) | 134.6 | 87.4 (0.65x) |
| 12/1 | 32 | 382.4 | 344.9 (0.90x) | 206.3 | 178.0 (0.86x) |
| 12/1 | 64 | 719.4 | 654.8 (0.91x) | 387.1 | 335.6 (0.87x) |
| 24/2 | 1 | 27.2 | 23.4 (0.86x) | 14.3 | 9.1 (0.64x) |
| 24/2 | 2 | 50.0 | 45.5 (0.91x) | 32.6 | 24.2 (0.74x) |
| 24/2 | 4 | 98.5 | 90.2 (0.92x) | 60.2 | 47.7 (0.79x) |
| 24/2 | 8 | 246.8 | 178.2 (0.72x) | 134.8 | 90.2 (0.67x) |
| 24/2 | 16 | 381.7 | 336.4 (0.88x) | 204.4 | 170.4 (0.83x) |
| 24/2 | 32 | 720.3 | 653.4 (0.91x) | 383.3 | 334.6 (0.87x) |
| 24/2 | 64 | 1398.7 | 1304.9 (0.93x) | 736.0 | 665.5 (0.90x) |

sm_90

| heads (q/kv) | rows | Triton BF16 | ours BF16 | Triton FP8 | ours FP8
|
|---|---|---|---|---|---|
| 12/1 | 1 | 7.7 | 8.4 (1.09x) | 10.2 | 9.1 (0.89x) |
| 12/1 | 2 | 8.3 | 9.5 (1.15x) | 10.1 | 9.3 (0.93x) |
| 12/1 | 4 | 11.0 | 11.4 (1.03x) | 10.8 | 10.4 (0.96x) |
| 12/1 | 8 | 14.4 | 14.4 (1.00x) | 14.0 | 13.4 (0.96x) |
| 12/1 | 16 | 22.4 | 20.6 (0.92x) | 18.5 | 18.4 (1.00x) |
| 12/1 | 32 | 42.7 | 36.3 (0.85x) | 31.7 | 26.4 (0.83x) |
| 12/1 | 64 | 70.6 | 65.5 (0.93x) | 53.0 | 50.5 (0.95x) |
| 24/2 | 1 | 8.2 | 9.6 (1.17x) | 10.2 | 9.3 (0.91x) |
| 24/2 | 2 | 11.0 | 11.4 (1.04x) | 10.9 | 10.5 (0.96x) |
| 24/2 | 4 | 14.4 | 14.5 (1.01x) | 14.0 | 13.5 (0.97x) |
| 24/2 | 8 | 22.2 | 20.8 (0.93x) | 18.7 | 18.6 (0.99x) |
| 24/2 | 16 | 42.3 | 35.7 (0.84x) | 31.9 | 27.1 (0.85x) |
| 24/2 | 32 | 71.1 | 65.5 (0.92x) | 53.0 | 50.4 (0.95x) |
| 24/2 | 64 | 133.6 | 133.3 (1.00x) | 94.4 | 95.5 (1.01x) |

</details>

### NVFP4

The load path and merge changes above already bring the NVFP4 `default`
path to 0.83x the time of the pre-PR implementation on sm_80, comparing
separate runs across the same 14 shapes. The last commit takes another
4-9% off on SM80-SM90, as the geometric mean per head shape, and up to
15% on single shapes. It changes only the NVFP4 attention kernel and the
NVFP4 split count.

Both kernels use four warps per CTA and two-stage buffering, but their
split counts differed. On sm_80 the NVFP4 tile loop took 1579
instructions per tile against Cake's 1359, and kernel time followed the
instruction count (0.920x time for 0.916x instructions on one shape of
an early variant). The last commit cuts the count to 1386:

- Each lane gathers a tile's copy addresses once with shuffles, and K
and V reuse them.
- The page lookup divides by multiply-shift.
- The E2M1 values carry a 2^120 factor and the E4M3 block scales 2^-120.
Both conversions stay exact, and so does their product, which drops the
bias multiply of the E4M3 conversion.
- V is decoded straight into the token pairs of the PV B fragments.

K/V copies also use the L2 evict-first policy, since a CTA reads each
K/V row once. NVFP4 now splits for two CTAs per SM and keeps every
split, instead of filling the resident wave and then trimming to the
fewest splits with the same tiles per split. On its own the split change
gives 0.98x on sm_80, 1.00x on sm_89 (where it changes two shapes) and
0.97x on sm_90, and costs up to 1.6% on single shapes on sm_80 and 2.7%
on sm_90.

Kernel time on the same shapes plus 128 rows on 12/1, with the previous
commit, this PR and Cake (`backend="cake"`) timed in the same process in
forward then reverse order, as the geometric mean over rows 2-128 on
12/1 heads and 2-64 on 24/2:

| arch | vs previous commit, 12/1 | vs previous commit, 24/2 | vs Cake,
12/1 | vs Cake, 24/2 | vs Cake, per shape |
|---|---|---|---|---|---|
| sm_80 | 0.925x | 0.914x | 1.029x | 1.022x | 0.99-1.06x |
| sm_89 | 0.941x | 0.963x | 0.994x | 1.028x | 0.95-1.05x |
| sm_90 | 0.929x | 0.927x | 0.979x | 1.019x | 0.84-1.06x |

The single-row shape is the first one timed in each process, and in some
runs its rounds came out bimodal (14% apart on sm_89 24/2 here), so it
is left out of the means; the per-shape tables below still list it.
Against Cake the result now depends on the shape: on 12/1 heads this PR
is 0.6% faster on sm_89, within run-to-run noise, and 2.1% faster on
sm_90, while it is 2.9% slower on sm_80 and 2-3% slower on 24/2 on all
three. This PR doesn't close that gap. The sm_90 numbers come from a
132-SM part; the NVFP4 split count follows the SM count, so sm_90 parts
with other SM counts can land differently.

<details><summary>NVFP4 per-shape times (µs)</summary>

sm_80

| heads (q/kv) | rows | previous commit | this PR | Cake |
|---|---|---|---|---|
| 12/1 | 1 | 10.7 | 10.7 (1.00x) | 9.9 (1.08x) |
| 12/1 | 2 | 11.4 | 11.4 (1.00x) | 10.7 (1.06x) |
| 12/1 | 4 | 13.8 | 13.7 (0.99x) | 13.8 (0.99x) |
| 12/1 | 8 | 17.5 | 16.9 (0.96x) | 16.5 (1.02x) |
| 12/1 | 16 | 26.6 | 22.7 (0.85x) | 22.0 (1.03x) |
| 12/1 | 32 | 40.7 | 36.0 (0.89x) | 34.7 (1.04x) |
| 12/1 | 64 | 68.8 | 63.8 (0.93x) | 61.3 (1.04x) |
| 12/1 | 128 | 131.9 | 115.1 (0.87x) | 113.1 (1.02x) |
| 24/2 | 1 | 11.4 | 11.3 (0.99x) | 10.8 (1.06x) |
| 24/2 | 2 | 13.8 | 13.8 (1.00x) | 13.9 (0.99x) |
| 24/2 | 4 | 17.7 | 17.0 (0.96x) | 16.5 (1.03x) |
| 24/2 | 8 | 26.7 | 22.6 (0.85x) | 22.2 (1.02x) |
| 24/2 | 16 | 40.5 | 36.3 (0.89x) | 34.8 (1.04x) |
| 24/2 | 32 | 69.5 | 64.1 (0.92x) | 61.5 (1.04x) |
| 24/2 | 64 | 131.8 | 115.2 (0.87x) | 113.5 (1.01x) |

sm_89

| heads (q/kv) | rows | previous commit | this PR | Cake |
|---|---|---|---|---|
| 12/1 | 1 | 8.8 | 8.7 (0.99x) | 8.4 (1.04x) |
| 12/1 | 2 | 10.8 | 9.1 (0.85x) | 9.7 (0.95x) |
| 12/1 | 4 | 13.3 | 13.3 (1.00x) | 12.8 (1.04x) |
| 12/1 | 8 | 30.2 | 29.6 (0.98x) | 29.1 (1.02x) |
| 12/1 | 16 | 55.7 | 54.0 (0.97x) | 52.4 (1.03x) |
| 12/1 | 32 | 104.9 | 99.1 (0.94x) | 97.4 (1.02x) |
| 12/1 | 64 | 224.6 | 205.4 (0.91x) | 213.8 (0.96x) |
| 12/1 | 128 | 395.7 | 370.6 (0.94x) | 390.5 (0.95x) |
| 24/2 | 1 | 10.8 | 10.0 (0.93x) | 11.0 (0.91x) |
| 24/2 | 2 | 13.2 | 13.0 (0.98x) | 12.5 (1.04x) |
| 24/2 | 4 | 30.5 | 29.8 (0.98x) | 29.1 (1.02x) |
| 24/2 | 8 | 55.9 | 54.2 (0.97x) | 52.5 (1.03x) |
| 24/2 | 16 | 102.9 | 100.8 (0.98x) | 98.8 (1.02x) |
| 24/2 | 32 | 230.9 | 213.8 (0.93x) | 212.4 (1.01x) |
| 24/2 | 64 | 432.5 | 409.0 (0.95x) | 390.6 (1.05x) |

sm_90

| heads (q/kv) | rows | previous commit | this PR | Cake |
|---|---|---|---|---|
| 12/1 | 1 | 10.1 | 9.9 (0.98x) | 10.1 (0.99x) |
| 12/1 | 2 | 10.3 | 10.2 (0.98x) | 10.2 (1.00x) |
| 12/1 | 4 | 11.0 | 10.8 (0.99x) | 11.4 (0.95x) |
| 12/1 | 8 | 13.1 | 12.7 (0.97x) | 15.1 (0.84x) |
| 12/1 | 16 | 18.3 | 15.5 (0.85x) | 15.3 (1.01x) |
| 12/1 | 32 | 25.1 | 22.0 (0.88x) | 21.5 (1.02x) |
| 12/1 | 64 | 45.5 | 40.1 (0.88x) | 40.0 (1.00x) |
| 12/1 | 128 | 78.7 | 76.1 (0.97x) | 73.4 (1.04x) |
| 24/2 | 1 | 10.3 | 10.1 (0.98x) | 10.2 (1.00x) |
| 24/2 | 2 | 10.9 | 10.9 (0.99x) | 10.8 (1.00x) |
| 24/2 | 4 | 12.9 | 12.7 (0.99x) | 12.0 (1.06x) |
| 24/2 | 8 | 18.3 | 15.6 (0.85x) | 15.8 (0.99x) |
| 24/2 | 16 | 25.1 | 22.0 (0.88x) | 21.7 (1.01x) |
| 24/2 | 32 | 45.1 | 41.8 (0.93x) | 41.3 (1.01x) |
| 24/2 | 64 | 81.9 | 77.0 (0.94x) | 73.8 (1.04x) |

</details>

## 🔍 Related Issues

Tracking issue: #6803

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually on the files this PR changes
(`pre-commit run --from-ref origin/main --to-ref HEAD`) and fixed any
reported issues.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## 🔬 Experimental Track

<!-- Only for PRs submitted under the experimental policy
(CONTRIBUTING.md → "Experimental APIs and Backends").
     Leave this section untouched for normal PRs. -->

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/` and/or an `@flashinfer_experimental_api`.
Tracking issue: #6803
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

<!-- Required for experimental PRs. Replace the commented lines below
with your targets.
Do not delete the fence or change its `experimental-tests` tag — the
experimental-track
watcher reads it verbatim to decide which targets to ask CI for. -->

```experimental-tests
tests/experimental/test_qsa_nvfp4.py
tests/experimental/test_cake_qsa_nvfp4_api.py
```

## Reviewer Notes

`tests/experimental/test_qsa_nvfp4.py` runs its existing matrix
(layouts, splits, CUDA graph replay, invalid inputs) for all three
formats and takes the split count from `_num_splits`, so it covers the
new NVFP4 split rule too. `test_cake_qsa_nvfp4_api.py` checks that auto
routes FP8 and BF16 to `default`. At this revision both files pass on
sm_80 (64 tests). On sm_89 and sm_90, `test_qsa_nvfp4.py` (46 tests)
passes on an equivalent build of the last commit (same SASS and split
counts), and both files passed there on the previous revision. The
existing example covers NVFP4; FP8 and BF16 take the same call without
`k_sf` / `v_sf`. Outside the package, the change is the dtype check in
the `backend="auto"` route and the docstring in `flashinfer/sparse.py`.

The BF16 row layout, BF16/FP8 merge and BF16 split commits leave the
NVFP4 kernels at the same SASS on sm_80, sm_89 and sm_90, and NVFP4 and
FP8 at the same split counts. The sm_90 BF16 numbers reuse an earlier
run whose BF16 kernels and split counts match this revision. The last
commit leaves the FP8 and BF16 attention kernels and the merge kernels
at the same SASS on all three, and FP8 and BF16 at the same split
counts. Run with the old split counts, its NVFP4 output is bit-identical
to the previous commit's on all three, across every non-NaN E4M3 scale
byte, invalid indices and short rows; the new split counts only reorder
the reduction.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Sparse paged attention now supports NVFP4, FP8-e4m3, and BF16
key/value caches.
* NVFP4 uses global scale factors; FP8 requires per-tensor scale
factors; BF16 ignores scale factors.
* Automatic backend selection routes FP8 and BF16 caches to the
reference implementation. NVFP4 routing continues to depend on device
capability.
* **Documentation**
* Clarified cache format support, scale-factor requirements, and backend
selection.
* **Tests**
* Expanded coverage for cache formats, backend routing, reference
comparisons, and CUDA graph replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: lesj0610 <lesj0610@gmail.com>

### [73beeb0](https://github.com/flashinfer-ai/flashinfer/commit/73beeb0e0a6c4e8de5c48a90a6c4d7b3f5a71a5b)

- **作者**: Cui Hangbin
- **时间**: 2026-10-29T21:40:47Z
- **提交信息**: feat(gdn): add experimental SM120 CuTe prefill backend (#6342)

## 📌 Description

Replace the original pipeline32 stable-path opt-in with the explicit
experimental `backend="sm120_cute"` on `chunk_gated_delta_rule`. The
CuTe backend and CP policy live under
`flashinfer/experimental/gdn_sm120_cute/`; stable automatic dispatch and
official kernels remain unchanged. The separate local-fusion prototype
is not included.

The qualified fast domain is RTX6000D (SM120/156 SMs), D=128, BF16/FP16
QKV, finite native FP32 log gates, FP32 beta/state, and matching
immutable CPU sequence metadata. Checkpoints, state pools, non-FP32
state, linear/raw gates and unsupported configurations use the official
FlashInfer implementation. The original aggregate checkpoint ceil check
is removed with the old pipeline32 path.

The follow-up `34e729954` moves launch-grid dimensions out of the
compile keys and passes them at runtime. Kernels are reused across
sequence lengths within the same static configuration/path; dtype, head
shape, state layout/options and V128 full-chunk specializations remain
separate. Sequence-plan caching still has its existing 64-layout limit.
`dc13c07f0619` also includes the backend README/license and CP
coefficient CSV in Python wheels; the kernels remain JIT-only.

The follow-up `c3ea09e14` preserves the public zero-scale sentinel:
`scale=0.0` now uses the default `1/sqrt(d)` on the experimental path,
matching the official route. Public forward tests cover `None`, `0.0`
and a nonzero scale across CP modes, full/tail layouts and caller-owned
outputs.

The follow-up `312a7bcb6d` makes plan-cache overflow visible with a
one-time warning, keeps fallback tests active on all SM120 SKUs, and
corrects the eager benchmark timing/input documentation. Existing plans
are retained for captured-graph lifetime; no eviction is introduced.

## 🔍 Related Issues

Tracking/owner/graduation plan: #7118 (owner @cuihangbin, review target
2026-11-20).

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Configured changed-file pre-commit passed for `312a7bcb6d` on the
adapter, public tests and both changed READMEs, including mypy and Ruff.
Direct Ruff check/format and `git diff --check` also passed.
Repository-wide tests were not run locally; GPU CI still needs
maintainer authorization.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] The complete experimental test directory passes locally on
RTX6000D at `312a7bcb6d43ada5a1deccec3e01f50e1b019bb5`: **100 passed**
(78.11 seconds; exit code 0). Upstream CI remains required.

Coverage includes independent FP64 recurrence, normalization, BF16/FP16,
full/tail and int32/int64 cache switching, strided inputs, CUDA graphs,
mutated sequence metadata with matching CPU offsets, and public-API
fallback.

Checkpoint regression cases `[100]`, `[64,32]`, `[200,200]` at
interval64 use exactly 1, 1 and 6 entries; `[32]` uses zero.
FP32/BF16/FP16 checkpoint buffers and BF16/FP16/FP8 initial/final state
fallback are tested. `checkpoint_cu_starts` consistency remains the
official caller precondition.

The following sanitizer results belong to the previously submitted
`92cdd3d8ae` source and were not rerun for this follow-up:

- Public-API memcheck: 35 tests passed, zero kernel memory errors.
- Public forward racecheck: 12 tests passed, zero hazards.
- Sanitizers use `--report-api-errors no` for known machine CUDA-hook
startup/symbol-probe noise; kernel checks remain enabled. This is not an
all-workload sanitizer claim.

Latest follow-up validation:

- The public adapter cache regression warms 64 distinct layouts, checks
a one-time warning and exact official fallback on the next two layouts,
retains all cached plan identities, confirms an old layout still uses
CuTe, and replays its previously captured graph correctly after
overflow.
- Public fallback/numerical tests now run on any SM120. Only the
CuTe-specific cache test requires 156 SMs. Two tests simulate
unqualified 170/188-SM adapter views on RTX6000D; a separate local
170-SM adapter/test-view run passes 61 public tests and skips only the
CuTe cache test. These are software simulations, not other-SKU hardware
results; those remain for CI.

- Before the zero-scale fix, the added public regression failed with
relative L2 error 1.0 (all-zero experimental output). After the fix, all
36 public forward cases pass, including 12 zero-scale cases. The tests
assert that the CuTe entry executes and compare output/final state to
the official route.

- Four new regression cases cover CP/fused × V64/V128 with Q/K
normalization enabled. Each grows and shrinks token, sequence and
segment counts in one process, asserts no additional compile-cache
entries after the first invocation, and compares output/final state
against an independent FP64 recurrence (relative error ≤0.02).
- The author also reports a separate RTX6000D 4B-shape check
(Hq/Hv=16/32): 6001 tokens compiled six kernels; 7019, 8193 and 4096
added zero compilations, with relative error about 0.0035. This
author-run check is separate from the automated regression above.
- A fused-only warmup does not compile CP's Warmup/PrepareH/CorrectH
kernels; the first CP call still compiles them. Different static
specializations may also compile separately.
- Changed-file Ruff check/format, project-configured mypy and the PR
diff whitespace check passed after merging upstream `7ccb13b8e781`.
- The upstream conflict in the `cu_seqlens_cpu` documentation is
resolved, preserving both the SM8x and experimental SM120 contracts.

## 🔬 Experimental Track

- [x] This PR is **experimental**: it adds or changes code under
`flashinfer/experimental/`. Tracking issue: #7118.
- [x] The tracking issue names the owner, reason, graduation criteria
and four-week review target.
- [x] Core changes are limited to a thin explicit backend entry point
and documentation.
- [x] Tests live in `tests/experimental/` and were validated on the
intended hardware; a runnable public-call example and benchmark are
included.
- [x] Nothing is registered in `flashinfer/aot.py`; stable
`backend="auto"` never selects this backend. Explicit selection emits
the standard experimental warning.
  - [x] **Test scope declared below.**

```experimental-tests
tests/experimental/gdn_sm120_cute
```

## Reviewer Notes

Public-call measurements below use code commit
`3cd6473fd4a30e117982fd193384bac3517e544b`, with evidence submitted at
`92cdd3d8ae`. The follow-ups change launch-grid compilation reuse,
packaging, zero-scale compatibility, cache fallback visibility, test
coverage and documentation; the 46-case performance matrix has **not**
been rerun at the current head, so those results remain historical
evidence for their recorded commit. All earlier
pipeline32/internal-kernel figures are superseded for this revised
proposal.

Both implementations receive the same native FP32 log gates, CPU
sequence offsets, normalized BF16 Q/K and unnormalized BF16 V, nonzero
FP32 initial state, and preallocated output/state buffers. Official gate
materialization and experimental buffer copies are included. Timing uses
`bench_gpu_time(enable_cupti=True, cold_l2_cache=True)`, three
alternating rounds, warmup10/repeat100; JIT and input generation are
excluded. These are eager, host-dependent measurements: CUPTI spans run
from the first kernel start to the last kernel end and include
inter-kernel host launch gaps, so CPU overhead is not fully excluded. No
CUDA-graph performance numbers are claimed. TP denotes per-rank head
shapes, without distributed communication.

Across 46 cases: **24 faster, 18 slower, 4 within 2%** of the actual
official default route, not the minimum of forced CP/fused measurements.
All experimental matrix calls were traced to CuTe, with no hidden
official fallback. Output/final-state relative L2 is below 0.02 (maximum
0.005389).

| TP / B / per-sequence length | Official default route | Official ms |
CuTe ms | Speedup |
|---|---|---:|---:|---:|
| TP1 / 1 / 32K | cp | 3.848770 | 3.173749 | 1.21x |
| TP1 / 4 / 16K | fused | 5.496085 | 4.577398 | 1.20x |
| TP2 / 2 / 32K | cp | 3.844528 | 2.707056 | 1.42x |
| TP1 / 2 / 4K | fused | 0.401167 | 0.598878 | 0.67x |
| TP2 / 4 / 2K | fused | 0.220161 | 0.296640 | 0.74x |

[Complete 46-case table, timing contract and raw-sample
locations](https://github.com/cuihangbin/flashinfer/blob/312a7bcb6d43ada5a1deccec3e01f50e1b019bb5/benchmarks/results/README_gdn_sm120_cute.md).
Representative commands:

```bash
pytest -q tests/experimental/gdn_sm120_cute
python benchmarks/bench_gdn_sm120_cute.py --tp 1 --preallocated --output tp1.json
python benchmarks/bench_gdn_sm120_cute.py --tp 2 --preallocated --output tp2.json
```

These results support an experimental proposal, not all-shape speedups
or production/model end-to-end gains. Linear/raw-gate workloads use the
official fallback and are not claimed optimized. Only RTX6000D was
qualified. Maintainer review and scoped CI are still required.

The CuTe algorithm and host CP policy are adapted from Qwen
FlashQLA5538c35; MIT notices and provenance are retained. No FlashQLA,
TileLang or FLA runtime dependency or performance comparison is
included. AI assistance was used for implementation, validation and PR
preparation; owner @cuihangbin.

---------

Signed-off-by: cuihangbin <cuihangbin@didiglobal.com>
Co-authored-by: cuihangbin <cuihangbin@didiglobal.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [7e80826](https://github.com/flashinfer-ai/flashinfer/commit/7e8082600cf0e4dfdfcf5ed49e6dcc911c89da50)

- **作者**: chengmingz-nv
- **时间**: 2026-10-29T21:37:28Z
- **提交信息**: fix(norm): preserve FP32 precision in BF16 FP4 RMSNorm weighting (#7705)

## Description

The BF16 fused FP4 RMSNorm path rounded `x * weight` to BF16 before FP32
normalization, changing packed values and block scales near quantization
boundaries. Keep both operands and the normalized intermediate in FP32
in NVFP4 and MXFP4; FP16 arithmetic is unchanged.

The BF16 comparison tests now use the same FP32 mathematical reference
for **packed bytes, block scales and dequantized values**, addressing
the review finding that the separate BF16-rounded path is a different
oracle. Extend the shared MXFP4 reference to accept FP32 inputs.
Preserve the deterministic packed-byte/scale regressions and every
existing tolerance.

## Validation (2026-10-29)

Validated the tree published as
`2b5803c6a782cfd7d0fdc60814e2c0b69ad5b1c5`, including main `269ba55a2`:

- Complete `tests/norm/test_rmsnorm_fp4_quant_cute_dsl.py`: **1,011
passed on Galaxy RTX PRO 4000 Blackwell (SM120)** and **1,011 passed on
Galaxy GB300 (SM103)**.
- The reviewer’s hidden-size=4096, batch-size=128 shapes, NVFP4/MXFP4
and BF16/FP16: **4 passed before and 4 passed after** on Galaxy RTX. The
reported RTX 5090 failure did **not** reproduce on this GPU; the
reference correction is source-backed and regression-tested, not claimed
as a locally reproduced 5090 fix.

Galaxy (Windows on ARM, Ubuntu 24.04 WSL), Python 3.12.3, PyTorch
2.14.1+cu130, CUDA toolkit 13.5, CUTLASS DSL 4.8.0, quack 0.6.5. A fresh
virtual environment, separate source checkouts and per-attempt JIT
caches were used. Source hashes were checked before execution.

The internal pipeline using mirror `f844760d` predates this follow-up.
Please rerun the scoped norm CI, including the RTX 5090 case, on the
current head. The separately noted large-hidden-size
`add_rmsnorm_fp4quant` global path remains a follow-up, as permitted in
review.


## Related issues

Maintenance of existing functionality; the reproducible cases are
described above.

## Pre-commit checks

- [x] Repository pre-commit hooks passed for the changed files.
- [x] No numerical tolerances were relaxed.

## Review / CI

This branch remains open for review. The latest public Test Results
Summary is pending authorization; a contributor with the repository’s CI
permission needs to start scoped CI for this revision. Device validation
below is not a substitute for the required CI/approval gates.

### [453a7e2](https://github.com/flashinfer-ai/flashinfer/commit/453a7e24501b8dabc9fdf80e0ff54708c64f11d2)

- **作者**: eigen
- **时间**: 2026-10-29T21:33:53Z
- **提交信息**: perf(cake_mhc): contention-aware routing of the mHC with-grad mapping and column-slab passes on SM100 / SM103 (#7893)

`cake_mhc_train` is Cake's four-stream mHC training backend, made up of
`forward_prepare` (which contains the forward map kernel) and
`backward_finish`. This PR moves the forward map kernel and
`backward_finish` to forms that keep running when other CUDA streams
hold some or all SMs, and adds two forward map kernel variants. The
baseline is the previous Cake version of these kernels on FlashInfer
`main`.

Input is BF16 X `[T, 4, 4096]`, and each load runs on a side stream.
**none** means no load. **16 x 640** means 16 CTAs of 640 threads.
**full-SM hold** means one 128-thread CTA per SM at maximum
shared-memory carveout (148 CTAs on B200, 152 on GB200 and GB300). Times
are the median per-call time in ms, measured with CUDA events over
back-to-back calls. Speedup = main / PR, taken as the median of
per-group ratios and rounded to two decimals; above 1 means the PR is
faster. **blocked** means main does not complete while the hold is
resident.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| forward_prepare | 4096 | none | 0.0594 | 0.0594 | 1.00x |
| forward_prepare | 4096 | 16 x 640 | 0.0594 | 0.0594 | 1.00x |
| forward_prepare | 4096 | full-SM hold | 0.0758 | 0.0758 | 1.00x |
| forward_prepare | 14928 | none | 0.1976 | 0.1976 | 1.00x |
| forward_prepare | 14928 | 16 x 640 | 0.2355 | 0.2355 | 1.00x |
| forward_prepare | 14928 | full-SM hold | 0.2437 | 0.2437 | 1.00x |
| forward_prepare | 16263 | none | 0.2068 | 0.2069 | 1.00x |
| forward_prepare | 16263 | 16 x 640 | 0.2376 | 0.2376 | 1.00x |
| forward_prepare | 16263 | full-SM hold | 0.2559 | 0.2558 | 1.00x |
| backward_finish | 4096 | none | 0.1346 | 0.1351 | 1.00x |
| backward_finish | 4096 | 16 x 640 | 0.2068 | 0.2068 | 1.00x |
| backward_finish | 14928 | none | 0.4070 | 0.4065 | 1.00x |
| backward_finish | 14928 | 16 x 640 | 0.6675 | 0.5393 | 1.24x |
| backward_finish | 14928 | full-SM hold | blocked | 0.4196 | — |
| backward_finish | 16263 | none | 0.4413 | 0.4359 | 1.01x |
| backward_finish | 16263 | 16 x 640 | 0.7766 | 0.5412 | 1.43x |
| backward_finish | 16263 | full-SM hold | blocked | 0.4487 | — |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| forward_prepare | 4096 | none | 0.0562 | 0.0563 | 1.00x |
| forward_prepare | 4096 | 16 x 640 | 0.0555 | 0.0557 | 1.00x |
| forward_prepare | 4096 | full-SM hold | 0.0717 | 0.0717 | 1.00x |
| forward_prepare | 14928 | none | 0.1933 | 0.1936 | 1.00x |
| forward_prepare | 14928 | 16 x 640 | 0.2271 | 0.2266 | 1.00x |
| forward_prepare | 14928 | full-SM hold | 0.2376 | 0.2376 | 1.00x |
| forward_prepare | 16263 | none | 0.2021 | 0.2023 | 1.00x |
| forward_prepare | 16263 | 16 x 640 | 0.2370 | 0.2375 | 1.00x |
| forward_prepare | 16263 | full-SM hold | 0.2491 | 0.2489 | 1.00x |
| backward_finish | 4096 | none | 0.1300 | 0.1300 | 1.00x |
| backward_finish | 4096 | 16 x 640 | 0.1783 | 0.1782 | 1.00x |
| backward_finish | 14928 | none | 0.3841 | 0.3814 | 1.01x |
| backward_finish | 14928 | 16 x 640 | 0.6020 | 0.4490 | 1.34x |
| backward_finish | 14928 | full-SM hold | blocked | 0.3899 | — |
| backward_finish | 16263 | none | 0.4096 | 0.4047 | 1.01x |
| backward_finish | 16263 | 16 x 640 | 0.7243 | 0.5585 | 1.30x |
| backward_finish | 16263 | full-SM hold | blocked | 0.4147 | — |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| Kernel | T | Load | main ms | PR ms | Speedup |
|---|---|---|---|---|---|
| forward_prepare | 4096 | none | 0.0561 | 0.0563 | 1.00x |
| forward_prepare | 4096 | 16 x 640 | 0.0553 | 0.0553 | 1.00x |
| forward_prepare | 4096 | full-SM hold | 0.0696 | 0.0614 | 1.13x |
| forward_prepare | 14928 | none | 0.1874 | 0.1864 | 1.01x |
| forward_prepare | 14928 | 16 x 640 | 0.2294 | 0.1864 | 1.23x |
| forward_prepare | 14928 | full-SM hold | 0.2314 | 0.2028 | 1.14x |
| forward_prepare | 16263 | none | 0.1976 | 0.1976 | 1.00x |
| forward_prepare | 16263 | 16 x 640 | 0.2305 | 0.2028 | 1.14x |
| forward_prepare | 16263 | full-SM hold | 0.2493 | 0.2191 | 1.14x |
| backward_finish | 4096 | none | 0.1362 | 0.1362 | 1.00x |
| backward_finish | 4096 | 16 x 640 | 0.1454 | 0.1454 | 1.00x |
| backward_finish | 4096 | full-SM hold | 0.1393 | 0.1397 | 1.00x |
| backward_finish | 14928 | none | 0.3861 | 0.3813 | 1.01x |
| backward_finish | 14928 | 16 x 640 | 0.6039 | 0.4504 | 1.34x |
| backward_finish | 14928 | full-SM hold | blocked | 0.3894 | — |
| backward_finish | 16263 | none | 0.4106 | 0.4057 | 1.01x |
| backward_finish | 16263 | 16 x 640 | 0.7209 | 0.5524 | 1.30x |
| backward_finish | 16263 | full-SM hold | blocked | 0.4150 | — |

Cake also ships the mHC training head (forward mean, writing backward
and accumulating backward) in `cake_mhc_train_head`, and the mHC
training family ships on sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Added optimized forward-mapping options for supported GPU
architectures, including workloads with different grid and tile sizes.
* Updated backward-mapping selection for supported architectures, with a
broader range of workloads using the newer default path.
* Extended the backward-reduction configuration range for one supported
architecture.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [37b6c98](https://github.com/flashinfer-ai/flashinfer/commit/37b6c98314e192c98dca34b3df667562977b5943)

- **作者**: rmhaskar
- **时间**: 2026-10-29T21:22:49Z
- **提交信息**: fix(msa_ops sm90): accurate CuTe DSL sparse prefill and measured Cake / CuTe routing (#7887)

## 📌 Description

Fixes accuracy failures in the SM90 `msa_ops` CuTe DSL sparse prefill
and routes each shape to the faster accurate backend.

- **Single-token schedule gave wrong output** at 801–4096 pages. The fp8
P relabel mixed rows `r` and `r+8` in one register.
- **Union schedule was ~18x less accurate than Cake** (3e-2 vs 1.7e-3
rel-L2). Q and P now use fp8 hi/lo pairs, bringing it to ~1.9e-3.
- **~0.8% low bias** when V has a nonzero mean, caused by fp8 WGMMA
accumulation. Each block's P·V is now added to the output in f32.
- **Batch > 16 with > 4096 pages** now runs instead of raising.
- **Dispatch:** CuTe is preferred over Cake only where it's faster at
matched accuracy (≤ 800 pages and ≥ 8192 query tokens per sequence).

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

 Suggested CI test targets: `tests/msa_ops/`
`tests/msa_ops/test_msa_sm90.py`: 157 passed on H100. Adds a
constant-mean-V accuracy case, an 8192-token union case, and tightens
the bound to 3e-3.\

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved sparse-prefill scheduling for long queries and supported
workloads, with routing tuned to workload size and layout.
  * Expanded support for larger batches in the single-token schedule.

* **Accuracy**
* Improved sparse-prefill numerical accuracy through updated query and
probability processing, with regression coverage across varied
workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [9a81c96](https://github.com/flashinfer-ai/flashinfer/commit/9a81c96b465a26f3d6ec7c82c7984b9cff4c563b)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-29T21:20:27Z
- **提交信息**: fix(gdn): branch before exp in saturating softplus; raise on ReplaySSM gates (#6229)

<!-- .github/pull_request_template.md -->

## 📌 Description

Two small correctness fixes on the GDN decode and MTP verify paths,
independent of each other and of the tree-verify work in #6155. Split
out of the `accept_paths` follow-up because they touch the same files
and would otherwise be reviewed inside a much larger feature diff.

**Several GDN decode kernels return NaN on a saturating softplus, and in
the fp32-state MTP path whether you hit it depends only on batch size.**
Nine kernel sites computed `exp(softplus_beta * x)` unconditionally and
then blended the two softplus branches with a 0/1 mask, so for
`softplus_beta * x` beyond roughly 88 the masked `0 * inf` produced NaN.
The MTP selector picks the inline kernel when `B * HV <= 128` and the
warp-specialized one above that, so in the fp32-state path the same
input was finite at batch 16 and 100% NaN at batch 17 with 8 value
heads. The fix is one shared `@cute.jit` helper, `softplus_fp32` in
`flashinfer/gdn_kernels/_softplus.py`, that takes the branch before the
exp, used at every site: the inline, warp-specialized and
ReplaySSM-window kernels in `gdn_decode_mtp.py`, all five sites in
`gdn_decode_bf16_state.py` across
`gdn_decode_bf16state_mtp_ilp4_kernel`, `gdn_wide_vec_kernel` and
`gdn_wide_vec_kernel_t1`, which are the kernels behind
`gdn_decode_bf16_state.gated_delta_rule` and `gated_delta_rule_mtp` that
SGLang launches today, and the Rubin T=1 bf16-state kernel in
`gdn_decode_bf16_state_rubin.py` that `gated_delta_rule_decode` runs on
a uGPU pool on SM107. The helper's source file is part of every affected
kernel's cache key. Below the threshold the new code is the same
expression in the same precision and the same fastmath flags, so finite
outputs are unchanged.

**The ReplaySSM verify gates were bare `assert`s.** The
frozen-checkpoint gate in particular matters: under `python -O` it
vanishes, verify mutates the checkpoint it promises to leave frozen, and
the subsequent `gated_delta_rule_replayssm_commit` returns a silently
wrong state. The `disable_state_update` default is deprecated and flips
to `False` in 0.8.0 (#5306), so an unqualified `cache_replayssm=True`
call will reach that gate by omission. The two mutual-exclusion gates
(`intermediate_states_buffer`, `ssm_state_indices`) are the same hazard
class: under `-O` a caller could combine either with
`cache_replayssm=True` and silently fall off the tcgen05 dispatch. This
converts every gate in the `cache_replayssm` block, and the matching
`else` branch, to `ValueError`, which is what the commit path already
raises. The `ssm_state_indices` asserts outside that block are
untouched, since existing tests pin their exception type.

## 🔍 Related Issues

Builds on #5314. Precedes the commit-side `accept_paths` change, which
edits the same validation block.

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

Both failures were reproduced on unpatched `main` (`b5e50c20b`) on a
B200 before applying the fix, by running the new tests against the
unpatched package. The saturating tests compare values against the
PyTorch references, not just finiteness: the fp32-state MTP cases
against the fp64 trace reference `_gdn_mtp_reference`, the bf16-state
cases against `decode_delta_rule` stepped with a bf16 state, both of
which apply `softplus` with the same threshold of 20.

- `test_verify_kernel_mtp_saturating_softplus[inline|warp_specialized]`
in `tests/gdn/test_decode_delta_rule.py` fills one draft step with `a =
100` and runs at batch 16 and 17 so the two cases straddle the kernel
selector, then checks the output against `_gdn_mtp_reference` at atol
1e-2, rtol 1e-2. On `main` the inline case passes and the
warp-specialized case is 100% NaN; with the fix both match the
reference. `test_verify_kernel_mtp_saturating_softplus_matches_inline`
checks the two kernels agree on the same inputs once the branch is
taken.
-
`test_gdn_decode_bf16_state_mtp_saturating_softplus[ilp4|wide_vec_128|wide_vec]`
and
`test_gdn_decode_bf16_state_t1_saturating_softplus[ilp4_t1|wide_vec_t1]`
run the same input through the bf16-state dispatcher at batch sizes that
select each of the three bf16-state kernels and check the output against
`decode_delta_rule` with a bf16 state at atol 1e-3, rtol 5e-3, the
tolerance the existing bf16-state MTP test uses. Results on unpatched
`main` are listed in the review notes below.
- `test_rubin_t1_saturating_softplus_matches_reference[16|512]` in
`tests/gdn/test_decode_bf16_state_rubin.py` does the same for the Rubin
kernel at both ends of its batch range. It carries the file's
`arch_rubin` marker, so it runs only on SM107; it was not executed
locally and relies on the VR200 lane of the internal matrix.
- `test_replayssm_verify_validation` in
`tests/gdn/test_replayssm_spec_fold.py` now requires `ValueError` from
all eight gates instead of accepting either exception type. On `main`
six of them raise `AssertionError`.
- Regression on B200 after the rebase onto `193e270ab`:
`tests/gdn/test_replayssm_spec_fold.py` as a whole 200 passed, 16
skipped; the saturating cases plus the existing
`test_verify_kernel_mtp*`, `test_gdn_decode_bf16_state_kernel`,
`_t1_kernel`, `_mtp_kernel` and `_wide_vec_mtp_kernel` cases 118 passed,
10 skipped.

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
with your test targets. -->
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

Softplus equivalence: below the threshold the old blend was `1 *
((1/beta) * log(1 + exp(beta_x))) + 0 * x`, and the new helper is the
same product with the same `fastmath=True` on exp and log and the same
`Float32` types, so finite outputs do not move. Above the threshold the
old code was `0 * inf + 1 * x`, which is NaN, and the new code is `x`.
The branch is a warp-uniform scalar `if`, the same form
`gdn_decode_nontranspose.py` and `gdn_decode_pretranspose.py` already
use inline. The bf16-state sites had two spellings of the same block,
one with mixed `_val`/`_v` suffixes, which is why the fix is a shared
helper rather than nine edited copies.

Unpatched `main` on B200, same inputs: fp32-state MTP inline kernel
finite, warp-specialized 100% NaN; bf16-state `mtp_ilp4`, `wide_vec`
(batch 16 and 17), `wide_vec_t1` and the T=1 ilp4 path all 100% NaN.
With the fix every case is finite.

Regression counts are in the Tests section. The `scatter` case of
`test_replayssm_verify_validation` still expects `AssertionError`,
because `ssm_state_indices` with `disable_state_update=True` trips the
pre-existing assert outside the ReplaySSM block before reaching the
converted gate.

The `assert` to `ValueError` conversion changes the exception type
callers see for malformed ReplaySSM inputs, which no caller in the repo
catches.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* GDN decoding now avoids non-finite outputs for large input values
across supported MTP and BF16-state decoding paths, with results checked
against reference behavior.
* Invalid ReplaySSM cache configurations now raise `ValueError` for the
covered validation failures, including supplying ReplaySSM buffers when
caching is disabled.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c58617e](https://github.com/flashinfer-ai/flashinfer/commit/c58617e6dab88872d498a58026d62fb7f3c90b42)

- **作者**: Adrian
- **时间**: 2026-10-29T21:02:22Z
- **提交信息**: test(comm): fix Ulysses initialization fault injection (#7876)

<!-- .github/pull_request_template.md -->

## 📌 Description

The communicator now initializes NVLink through
`_init_ulysses_a2a_configured`, but the initialization-fault test still
patches the public `init_ulysses_a2a` wrapper. The injected exception is
bypassed, so `[nvlink-init]` unexpectedly succeeds and `[auto-init]`
stays on NVLink instead of falling back to NCCL.

Patch the configured initializer used by the communicator so the
existing tests exercise the intended initialization failure and staged
cleanup path.

## 🔍 Related Issues

Related to #7015.

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

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: Targeted coverage of the existing Ulysses communicator tests is
sufficient.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/comm/test_ulysses_communicator.py`

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

Validation completed:

- CPU probe executing the existing injection and the communicator's
actual stage-C statements fails before the change and passes afterward.
- Pre-commit hooks for the changed file passed, including Ruff 0.12.8
lint and formatting; Python syntax and `git diff --check` also passed.

The two-GPU tests remain unrun locally because the host has no usable
CUDA driver or PyTorch. Please validate the existing `[nvlink-init]` and
`[auto-init]` cases on two NVLink-connected GPUs. No production code
changes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated automated checks for initialization failure handling to
reflect the current initialization flow.
  * No end-user behavior changes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4b660a4](https://github.com/flashinfer-ai/flashinfer/commit/4b660a4ec3de211e80cef86d0ea6a8e0114bb681)

- **作者**: eigen
- **时间**: 2026-10-29T20:17:20Z
- **提交信息**: fix(cake_fmha): context JIT routes complete on tiles without a visible key (#7879)

cake_fmha's paged context path has five hand-written JIT routes: BF16,
FP8, FP8 Q with NVFP4 KV, FP8 head dim 256, and FP16 head dim 256. This
PR changes all five so they finish on tiles that have no visible key.
Those are a request with zero KV length, a causal tile whose rows see no
key and, on the FP8 head dim 256 route, a partial last L2 section. On
main, these inputs hang. With this PR, rows without keys return O = 0
and LSE = -inf, and rows with keys are bitwise identical to main. The
table below compares latency against FlashInfer main on shapes that
complete on both.

NVIDIA B200 (sm_100a) and NVIDIA GB300 (sm_103a), CUDA 13.0. Base =
FlashInfer main, new = this PR, and times are in us (median over 5
memory layouts, cold L2). Speedup = base/new, given as the median over
the layouts with the minimum layout in brackets. WIN means above 1 and
above the A/A (new against new) noise band in every layout. LOSS means
below min(1, A/A lower edge) in every layout. TIE is everything else.

| route | shape | GPU | base us | new us | speedup base/new, median [min
layout] | A/A band | verdict |
|---|---|---|---:|---:|---|---|---|
| FP8 | B=4, q=511, kv=2047, heads 32/4, page 16 | B200 | 68.00 | 68.53
| 0.9939 [0.9900] | 0.9801..1.0104 | TIE |
| FP8 | B=4, q=511, kv=2047, heads 32/4, page 16 | GB300 | 59.89 | 60.16
| 0.9976 [0.9881] | 0.9825..1.0124 | TIE |
| FP8 | B=8, q=1024, kv=4096, heads 32/8, page 32 | B200 | 349.44 |
349.97 | 0.9985 [0.9978] | 0.9979..1.0010 | TIE |
| FP8 | B=8, q=1024, kv=4096, heads 32/8, page 32 | GB300 | 276.45 |
276.86 | 0.9985 [0.9966] | 0.9968..1.0032 | TIE |
| FP8 | B=16, q=128, kv=4096, heads 8/1, page 64 | B200 | 117.39 |
117.01 | 1.0037 [1.0008] | 0.9951..1.0022 | TIE |
| FP8 | B=16, q=128, kv=4096, heads 8/1, page 64 | GB300 | 98.26 | 98.53
| 0.9950 [0.9821] | 0.6333..1.0079 | TIE |
| FP8 | B=256, q=32, kv=1024, heads 32/4, page 64 | B200 | 119.02 |
119.30 | 0.9979 [0.9896] | 0.9976..1.0102 | TIE |
| FP8 | B=256, q=32, kv=1024, heads 32/4, page 64 | GB300 | 106.30 |
106.40 | 0.9991 [0.9947] | 0.9955..1.0039 | TIE |
| FP8 | B=2, q=2048, kv=2048, heads 64/8, page 64 | B200 | 122.90 |
122.93 | 0.9980 [0.9943] | 0.9984..1.0023 | TIE |
| FP8 | B=2, q=2048, kv=2048, heads 64/8, page 64 | GB300 | 100.30 |
100.30 | 1.0016 [0.9968] | 0.9917..1.0080 | TIE |
| FP8 Q / NVFP4 KV | B=4, q=511, kv=2047, heads 32/4, page 16 | B200 |
84.70 | 84.80 | 0.9981 [0.9957] | 0.9580..1.0204 | TIE |
| FP8 Q / NVFP4 KV | B=4, q=511, kv=2047, heads 32/4, page 16 | GB300 |
86.16 | 86.46 | 0.9974 [0.9900] | 0.9889..1.0138 | TIE |
| FP8 Q / NVFP4 KV | B=8, q=1024, kv=4096, heads 32/8, page 16 | B200 |
483.04 | 483.81 | 0.9991 [0.9984] | 0.9926..1.0058 | TIE |
| FP8 Q / NVFP4 KV | B=8, q=1024, kv=4096, heads 32/8, page 16 | GB300 |
457.28 | 457.63 | 0.9990 [0.9980] | 0.9972..1.0024 | TIE |
| FP8 Q / NVFP4 KV | B=16, q=128, kv=4096, heads 8/1, page 16 | B200 |
83.14 | 82.99 | 1.0004 [0.9984] | 0.9815..1.0197 | TIE |
| FP8 Q / NVFP4 KV | B=16, q=128, kv=4096, heads 8/1, page 16 | GB300 |
86.54 | 86.35 | 1.0004 [0.9983] | 0.9872..1.0097 | TIE |
| FP8 Q / NVFP4 KV | B=2, q=2048, kv=2048, heads 64/8, page 16 | B200 |
180.91 | 181.02 | 0.9985 [0.9982] | 0.9864..1.0270 | TIE |
| FP8 Q / NVFP4 KV | B=2, q=2048, kv=2048, heads 64/8, page 16 | GB300 |
172.10 | 172.26 | 0.9986 [0.9984] | 0.9919..1.0054 | TIE |
| FP8, head dim 256 | B=4, q=512, kv=2048, heads 16/8, page 16 | B200 |
414.83 | 414.86 | 1.0000 [0.9998] | 0.9992..1.0010 | TIE |
| FP8, head dim 256 | B=4, q=512, kv=2048, heads 16/8, page 16 | GB300 |
374.69 | 374.69 | 1.0000 [0.9999] | 0.9995..1.0010 | TIE |
| FP8, head dim 256 | B=1, q=4096, kv=4096, heads 8/4, page 64 | B200 |
315.60 | 315.52 | 1.0002 [0.9998] | 0.9957..1.0020 | TIE |
| FP8, head dim 256 | B=1, q=4096, kv=4096, heads 8/4, page 64 | GB300 |
277.09 | 277.25 | 0.9996 [0.9991] | 0.9979..1.0017 | TIE |
| FP8, head dim 256 | B=16, q=128, kv=4096, heads 32/8, page 32 | B200 |
793071.16 | 793122.03 | 0.9999 [0.9998] | 0.9993..1.0007 | TIE |
| FP8, head dim 256 | B=16, q=128, kv=4096, heads 32/8, page 32 | GB300
| 739345.35 | 739322.44 | 1.0000 [0.9998] | 0.9965..1.0033 | TIE |
| FP16, head dim 256 | B=4, q=512, kv=2048, heads 16/8, page 16 | B200 |
668.94 | 669.26 | 0.9995 [0.9994] | 0.9994..1.0002 | TIE |
| FP16, head dim 256 | B=4, q=512, kv=2048, heads 16/8, page 16 | GB300
| 621.62 | 621.82 | 0.9997 [0.9996] | 0.9993..1.0004 | TIE |
| FP16, head dim 256 | B=1, q=4096, kv=4096, heads 8/4, page 64 | B200 |
508.73 | 509.34 | 0.9989 [0.9986] | 0.9990..1.0003 | LOSS |
| FP16, head dim 256 | B=1, q=4096, kv=4096, heads 8/4, page 64 | GB300
| 467.84 | 467.73 | 1.0002 [1.0001] | 0.9995..1.0004 | TIE |
| FP16, head dim 256 | B=16, q=128, kv=4096, heads 32/8, page 32 | B200
| 833579.73 | 833660.98 | 1.0002 [0.9995] | 0.9990..1.0009 | TIE |
| FP16, head dim 256 | B=16, q=128, kv=4096, heads 32/8, page 32 | GB300
| 789684.17 | 789367.01 | 1.0000 [0.9999] | 0.9989..1.0066 | TIE |
| BF16 | B=4, q=511, kv=2047, heads 10/2, page 32 | B200 | 47.66 | 48.08
| 0.9833 [0.9793] | 0.9960..1.5045 | LOSS |
| BF16 | B=4, q=511, kv=2047, heads 10/2, page 32 | GB300 | 70.91 |
69.86 | 1.0023 [0.9836] | 0.9481..1.0860 | TIE |
| BF16 | B=4, q=257, kv=1024, heads 10/2, page 1024 | B200 | 44.51 |
44.22 | 1.0003 [0.9315] | 0.7197..1.0021 | TIE |
| BF16 | B=4, q=257, kv=1024, heads 10/2, page 1024 | GB300 | 47.22 |
47.87 | 1.0117 [0.9804] | 0.9741..1.0275 | TIE |
| BF16 | B=4, q=511, kv=2047, heads 32/4, page 16 | B200 | 76.10 | 76.21
| 0.9962 [0.9950] | 0.9547..1.0155 | TIE |
| BF16 | B=4, q=511, kv=2047, heads 32/4, page 16 | GB300 | 73.79 |
72.94 | 1.0021 [0.9821] | 0.9776..1.0288 | TIE |
| BF16 | B=8, q=1024, kv=4096, heads 32/8, page 32 | B200 | 418.70 |
419.86 | 0.9978 [0.9913] | 0.9911..1.0082 | TIE |
| BF16 | B=8, q=1024, kv=4096, heads 32/8, page 32 | GB300 | 344.94 |
344.13 | 1.0023 [1.0002] | 0.9908..1.0124 | TIE |
| BF16 | B=16, q=128, kv=4096, heads 8/1, page 64 | B200 | 123.47 |
123.66 | 0.9984 [0.9983] | 0.9808..1.0093 | TIE |
| BF16 | B=16, q=128, kv=4096, heads 8/1, page 64 | GB300 | 123.24 |
122.98 | 1.0029 [0.9911] | 0.9858..1.0158 | TIE |

The two LOSS rows are on B200 and are the cost of the fix. FP16 head dim
256 at B=1, q=4096, kv=4096 goes from 508.73 us to 509.34 us, and BF16
at B=4, q=511, kv=2047, heads 10/2, page 32 goes from 47.66 us to 48.08
us. Both shapes are TIE on GB300.

cake_fmha also ships generated paged context programs (FP8 KV, BF16) and
paged decode routes, and the family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention handling for empty key/value sequences and causal
queries with no visible keys, preventing invalid results in these edge
cases.
* Fixed output mapping for incomplete attention tiles, including partial
sections.
* Improved synchronization during attention processing to support
reliable results across supported data formats.
* **Tests**
* Added coverage for empty and key-invisible rows, partial tiles, and
output comparisons across attention implementations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9f5c44e](https://github.com/flashinfer-ai/flashinfer/commit/9f5c44ea103e50840b57643465e6d0c40d6b349f)

- **作者**: eigen
- **时间**: 2026-10-29T19:51:16Z
- **提交信息**: test(cake_kda): add in-tree FP64 reference helpers for KCP tests (#7840)

Follow-up to #6919. Several KCP tests depend on an FP64 reference: the
rows of record, a seeded operand generator, and the FP64 reference
computation. Until now that reference lived outside the repository and
was imported as optional modules from `PYTHONPATH`. When those modules
were missing, the partition, plan, GPU table-parity and FP64
fake-backend tests in `tests/experimental/test_cake_kda_train_kcp.py`
were skipped. This PR moves the reference into the repository, so those
tests run by default. Only tests change; library code is untouched.

## What changed

- Added three helpers under `tests/test_helpers/`:
`cake_kda_kcp_shapes.py`, `cake_kda_kcp_inputs.py` and
`cake_kda_kcp_reference.py`. They keep the same rows, seeds, draw order
and FP64 arithmetic as the external modules they replace. Their names
match the `tests/test_helpers/*kda*` globs used by CODEOWNERS and the
labeler.
- `test_cake_kda_train_kcp.py` and
`tests/test_helpers/cake_kcp_fake_backend.py` now import these helpers
directly. The optional `PYTHONPATH` lookup is gone.
- The fake backend always computes the reference on the CPU
(`compute_reference`).
- The transfer check is renamed to
`test_fake_backend_transfer_matches_basis_transfer`.

5 files changed, +819/-109.

## Validation

Ran on the PR head against `main` (base `f8b29214`), with no external
modules on `PYTHONPATH`:

- On R200 (sm_107a) and GB300 (sm_103a),
`tests/experimental/test_cake_kda_train_kcp.py` collects 691 tests: 691
pass, 0 skipped, 0 failed. With the old external modules on
`PYTHONPATH`, `main` collects the same 691 tests. Test ids and outcomes
match except for the one rename.
- The in-tree helpers produce the same rows, inputs and FP64 references
as the previous external modules. All 76 compared items are equal.
- `pre-commit` passes.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Expanded packed KDA context-parallel coverage across varied document
lengths, data regimes, and partition layouts.
* Added deterministic test data and CPU reference checks for outputs,
gradients, and state transfers.
* Updated GPU parity and fake-backend checks to use consistent test
cases and reference calculations.
  * Added coverage for empty inputs and uneven document partitions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [55a2823](https://github.com/flashinfer-ai/flashinfer/commit/55a28232ee1431da083b07cec9d17c8b3e7ca5fb)

- **作者**: eigen
- **时间**: 2026-10-29T19:44:29Z
- **提交信息**: perf(cake_gated_act_mxfp8): band-path programs for one SM100 and one SM103 backward entry (#7880)

The Cake fused SwiGLU + MXFP8 quantization kernel computes silu(gate) *
up from a BF16 input [M, 2K] and quantizes the result to MXFP8. It
stores one E8M0 scale (RCEIL rounding) per 32 E4M3 values, in the
swizzled 128 x 4 layout. The kernel has one data type and six forms. The
forward form is `flashinfer.silu_and_mul_mxfp8_quantize` and the
backward form is `flashinfer.silu_and_mul_mxfp8_quantize_backward`. Each
can write rowwise, colwise or both outputs.
`flashinfer.cake_gated_act_mxfp8_backend` runs one program per call and
picks it by M * K for each architecture. This PR changes program
selection for two backward entries. On sm_100a (B200), backward colwise
with M * K in [2^22, 2^24) now runs the packed-sigmoid form with the
called band path at 10 CTAs per SM. On sm_103a (GB300), backward both
with M * K in [2^24, 3 * 2^24) now runs the two-row form with
L1::no_allocate loads, packed sigmoid and the called band path at 7 CTAs
per SM. The sm_100a entry already uses these settings from 2^24.

The baseline is the previous Cake version of this kernel, which is the
package on FlashInfer main from #7783. With block-scaled inputs the
changed rows are faster: B200 4096 x 2048 backward colwise is 1.112x,
and GB300 4096 x 7168 backward both is 1.030x. With unit-normal inputs,
both changed rows are ties within the run-to-run spread. Every other row
runs the same machine code as before and stays within run-to-run noise.
On B200, the 131072 x 8192 block-scaled rows read 0.996x to 1.014x under
the GPU power cap, with the same program on both sides. That is noise,
not a gain or a loss. With unit-normal inputs, all rows are ties within
the spread: 0.992x to 1.010x on B200 and 0.998x to 1.001x on GB300.

Both versions run in the same process on the same GPU, in 8 alternating
paired rounds, with a cold L2 before every launch. Latency is the mean
over pairs of each sample's median CUPTI kernel time, in microseconds.
Speedup is the previous latency divided by this PR's latency, so a value
above 1 means this PR is faster. Block-scaled inputs are normals with
per-32-block scales spread over a wide exponent range. The GB300 run
used a package with the same machine code as this PR. The package goes
from 72 to 74 per-arch programs across 61 records. One record is new,
and one existing sm_100a record gains sm_103a. The exporter regenerates
the other kernel.cu files, and their machine code is unchanged. Outputs
are byte-identical to the previous version, and the public API is
unchanged.

### NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4

| M x K | Pass | Unit normals: previous Cake (µs) | This PR (µs) |
Speedup | Block-scaled: previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| 128 x 128 | fwd rowwise | 2.27 | 2.27 | 1.001x | 2.62 | 2.62 | 1.000x
|
| 128 x 128 | fwd colwise | 2.33 | 2.33 | 0.999x | 2.65 | 2.65 | 1.000x
|
| 128 x 128 | fwd both | 2.46 | 2.46 | 1.000x | 2.80 | 2.79 | 1.001x |
| 128 x 128 | bwd rowwise | 2.43 | 2.42 | 1.000x | 2.64 | 2.64 | 1.000x
|
| 128 x 128 | bwd colwise | 2.54 | 2.54 | 1.000x | 2.68 | 2.68 | 1.000x
|
| 128 x 128 | bwd both | 2.72 | 2.72 | 1.000x | 2.88 | 2.88 | 0.999x |
| 4096 x 2048 | fwd rowwise | 9.76 | 9.76 | 1.000x | 10.00 | 10.00 |
1.000x |
| 4096 x 2048 | fwd colwise | 10.46 | 10.46 | 1.000x | 12.85 | 12.85 |
1.000x |
| 4096 x 2048 | fwd both | 11.66 | 11.66 | 1.000x | 13.68 | 13.67 |
1.000x |
| 4096 x 2048 | bwd rowwise | 14.08 | 14.08 | 1.000x | 14.56 | 14.56 |
1.000x |
| 4096 x 2048 | bwd colwise | 15.02 | 15.02 | 1.000x | 18.54 | 16.67 |
1.112x |
| 4096 x 2048 | bwd both | 18.00 | 18.00 | 1.000x | 19.64 | 19.64 |
1.000x |
| 4096 x 7168 | fwd rowwise | 25.39 | 25.38 | 1.000x | 25.08 | 25.08 |
1.000x |
| 4096 x 7168 | fwd colwise | 26.51 | 26.50 | 1.000x | 31.97 | 31.97 |
1.000x |
| 4096 x 7168 | fwd both | 31.28 | 31.29 | 1.000x | 35.69 | 35.69 |
1.000x |
| 4096 x 7168 | bwd rowwise | 39.41 | 39.41 | 1.000x | 40.55 | 40.56 |
1.000x |
| 4096 x 7168 | bwd colwise | 41.45 | 41.46 | 1.000x | 46.07 | 46.08 |
1.000x |
| 4096 x 7168 | bwd both | 50.57 | 50.57 | 1.000x | 51.91 | 51.91 |
1.000x |
| 16384 x 7168 | fwd rowwise | 90.18 | 90.19 | 1.000x | 89.27 | 89.26 |
1.000x |
| 16384 x 7168 | fwd colwise | 92.21 | 92.22 | 1.000x | 101.59 | 101.54
| 1.001x |
| 16384 x 7168 | fwd both | 108.83 | 108.82 | 1.000x | 122.87 | 122.87 |
1.000x |
| 16384 x 7168 | bwd rowwise | 140.48 | 140.47 | 1.000x | 144.19 |
144.20 | 1.000x |
| 16384 x 7168 | bwd colwise | 144.72 | 144.73 | 1.000x | 159.71 |
159.70 | 1.000x |
| 16384 x 7168 | bwd both | 186.45 | 186.56 | 0.999x | 185.77 | 185.77 |
1.000x |
| 131072 x 8192 | fwd rowwise | 761.64 | 761.01 | 1.001x | 822.26 |
811.22 | 1.014x |
| 131072 x 8192 | fwd colwise | 794.20 | 791.10 | 1.004x | 921.09 |
918.40 | 1.003x |
| 131072 x 8192 | fwd both | 987.24 | 983.91 | 1.003x | 1143.59 |
1148.47 | 0.996x |
| 131072 x 8192 | bwd rowwise | 1219.66 | 1229.47 | 0.992x | 1403.14 |
1393.85 | 1.007x |
| 131072 x 8192 | bwd colwise | 1380.15 | 1370.43 | 1.007x | 1540.72 |
1531.41 | 1.006x |
| 131072 x 8192 | bwd both | 1743.41 | 1725.95 | 1.010x | 1991.55 |
1968.00 | 1.012x |

### NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4

| M x K | Pass | Unit normals: previous Cake (µs) | This PR (µs) |
Speedup | Block-scaled: previous Cake (µs) | This PR (µs) | Speedup |
|---|---|---:|---:|---:|---:|---:|---:|
| 128 x 128 | fwd rowwise | 1.99 | 2.00 | 0.998x | 2.29 | 2.29 | 1.001x
|
| 128 x 128 | fwd colwise | 2.06 | 2.06 | 1.000x | 2.36 | 2.36 | 1.000x
|
| 128 x 128 | fwd both | 2.16 | 2.16 | 1.000x | 2.46 | 2.46 | 1.000x |
| 128 x 128 | bwd rowwise | 2.13 | 2.13 | 1.001x | 2.23 | 2.23 | 0.999x
|
| 128 x 128 | bwd colwise | 2.27 | 2.27 | 0.998x | 2.42 | 2.42 | 0.999x
|
| 128 x 128 | bwd both | 2.40 | 2.40 | 0.998x | 2.56 | 2.56 | 1.000x |
| 4096 x 2048 | fwd rowwise | 9.04 | 9.04 | 1.000x | 9.51 | 9.51 |
1.000x |
| 4096 x 2048 | fwd colwise | 9.71 | 9.71 | 1.000x | 12.36 | 12.35 |
1.000x |
| 4096 x 2048 | fwd both | 10.99 | 10.98 | 1.000x | 13.31 | 13.30 |
1.001x |
| 4096 x 2048 | bwd rowwise | 13.49 | 13.48 | 1.001x | 13.80 | 13.80 |
1.000x |
| 4096 x 2048 | bwd colwise | 14.19 | 14.19 | 1.000x | 17.15 | 17.16 |
1.000x |
| 4096 x 2048 | bwd both | 16.97 | 16.97 | 1.000x | 19.25 | 19.25 |
1.000x |
| 4096 x 7168 | fwd rowwise | 24.04 | 24.03 | 1.000x | 25.06 | 25.07 |
1.000x |
| 4096 x 7168 | fwd colwise | 25.37 | 25.37 | 1.000x | 29.32 | 29.33 |
1.000x |
| 4096 x 7168 | fwd both | 29.97 | 29.97 | 1.000x | 34.68 | 34.68 |
1.000x |
| 4096 x 7168 | bwd rowwise | 37.91 | 37.91 | 1.000x | 39.65 | 39.65 |
1.000x |
| 4096 x 7168 | bwd colwise | 39.67 | 39.68 | 1.000x | 43.26 | 43.26 |
1.000x |
| 4096 x 7168 | bwd both | 47.84 | 47.80 | 1.001x | 50.10 | 48.65 |
1.030x |
| 16384 x 7168 | fwd rowwise | 86.77 | 86.80 | 1.000x | 90.66 | 90.66 |
1.000x |
| 16384 x 7168 | fwd colwise | 90.03 | 90.00 | 1.000x | 96.05 | 96.04 |
1.000x |
| 16384 x 7168 | fwd both | 104.99 | 104.94 | 1.000x | 113.59 | 113.59 |
1.000x |
| 16384 x 7168 | bwd rowwise | 135.37 | 135.37 | 1.000x | 139.17 |
139.16 | 1.000x |
| 16384 x 7168 | bwd colwise | 139.23 | 139.23 | 1.000x | 148.32 |
148.31 | 1.000x |
| 16384 x 7168 | bwd both | 175.40 | 175.43 | 1.000x | 176.95 | 176.97 |
1.000x |
| 131072 x 8192 | fwd rowwise | 738.02 | 738.06 | 1.000x | 755.48 |
755.40 | 1.000x |
| 131072 x 8192 | fwd colwise | 756.59 | 756.59 | 1.000x | 816.21 |
816.21 | 1.000x |
| 131072 x 8192 | fwd both | 906.47 | 906.42 | 1.000x | 954.61 | 954.76
| 1.000x |
| 131072 x 8192 | bwd rowwise | 1170.76 | 1170.73 | 1.000x | 1203.50 |
1203.53 | 1.000x |
| 131072 x 8192 | bwd colwise | 1220.39 | 1220.37 | 1.000x | 1293.39 |
1293.41 | 1.000x |
| 131072 x 8192 | bwd both | 1563.22 | 1563.39 | 1.000x | 1559.46 |
1559.47 | 1.000x |

Cake has no other variants of this kernel beyond these six BF16-to-MXFP8
forms with the swizzled scale layout, and the family ships on sm_100a
(B200), sm_103a (GB300) and sm_107a (R200).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added MXFP8 gated-activation kernel support for additional GPU
architectures, including `sm_100a` and `sm_103a`.
* Expanded kernel selection for backward operations across supported
architectures and workload sizes.
* **Refactor**
* Updated internal kernel implementations without changing their
existing calculations or output behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7304e8e](https://github.com/flashinfer-ai/flashinfer/commit/7304e8e5b6010e22bab0217ea7147b0ac3a8cb9e)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-29T19:41:47Z
- **提交信息**: fix(kda): accept 2-D dt_bias and reject non-bf16 state in the CuTe decode path (#6893)

## Summary

`recurrent_kda` falls through from the flash prefill route to the CuTe
grouped/one-warp kernels whenever a packed batch has no more tokens than
sequences (for example every sequence extends exactly one token). Those
kernels have a stricter contract than the docstring advertises, which
surfaced downstream in sgl-project/sglang#45018:

- `dt_bias` is documented as `[H*K]` or `[H, K]`, but the kernels bind
it as a flat tensor, so a `[H, K]` view fails at launch (`expected
ndim=1`; with older CuTe: `Expected strides[leading_dim] == 1`). It is
now flattened before launch.
- The kernels load the state pool as bf16, so a float32 pool failed with
an opaque tvm-ffi/CuTe dtype error. It now raises `TypeError` naming the
bfloat16 requirement. float32 pools remain supported by plain
multi-token prefill, which returns before this check. The
`initial_state` docstring now says so.

## Test plan

- Reproduced on B200 against `afbe429cc`: with the SGLang-shaped call
(packed `cu_seqlens`, `ssm_state_indices`, `use_gate_in_kernel`,
`lower_bound=-5`, `beta_is_logit=True`), bf16 state + flat `dt_bias`
works for all batch shapes; `[H, K]` `dt_bias` and float32 state fail
only when total tokens equal the sequence count.
- Added `test_one_token_per_sequence_accepts_2d_dt_bias` (4 and 32
sequences, covering the grouped and one-warp kernels) and
`test_one_token_per_sequence_rejects_fp32_state` to
`tests/kda/test_recurrent_kda.py`. Both fail on `afbe429cc` and pass
with this change.
- B200: `tests/kda/test_recurrent_kda.py` 74 passed, 5 skipped; with
`test_fused_kda_decode_dispatch.py`,
`test_cake_fused_kda_decode_dispatch.py`, `test_kda_output_only.py` and
`test_bf16_one_wave_route.py`, 2422 passed, 5 skipped.
- Not run: the other `tests/kda` files (prefill, cudnn, persistent
backends), and other architectures.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved validation for recurrent KDA state tensors, clearly rejecting
unsupported FP32 state usage.
  * Added consistent handling for multi-dimensional `dt_bias` inputs.
* Clarified supported state data types for prefill, decode, speculative
decode, and packed operations.

* **Tests**
* Added coverage confirming equivalent results for flattened and
multi-dimensional bias inputs.
  * Added validation tests for rejecting unsupported FP32 state.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [8d0fa1c](https://github.com/flashinfer-ai/flashinfer/commit/8d0fa1cea05117c1daefafb4f8529a3749197515)

- **作者**: eigen
- **时间**: 2026-10-29T19:33:23Z
- **提交信息**: perf(cake_mok_bf16): faster MXFP8 weight quantization and Rubin EP8 comm-SM defaults (#7870)

`flashinfer.experimental.cake_mok_bf16` is the MoK fused persistent
MegaMoE training kernel exposed through `flashinfer.mok`, and it has 8
training variants. For #7821, this PR speeds up the MXFP8 variant,
measured with clamped SwiGLU and FP32 weight-gradient accumulation. It
adds a fused single-launch MXFP8 weight quantizer, which cuts weight
quantization from 51.04-51.30 ms to 1.57-1.58 ms per layer. It also adds
Rubin EP8 communication-SM defaults: the `auto` split now resolves to
60:60 forward:backward communication SMs, or 72:60 when max/mean expert
load is ≥ 1.5. Compared with the previous Cake version of this package,
the MoE training update is 1.99-2.67x faster than that version at the
issue's 40:28 split and 1.54-2.44x faster than that version hand-tuned
to 60:60. Outputs are bitwise identical at equal communication splits
and peak memory is unchanged. The MXFP8 training update is now
1.30-1.48x faster than BF16 on the same build.

**MXFP8: previous version at 40:28 vs this PR (default `auto`)**,
previous / new (speedup)

| Tokens per rank, routing | Forward (ms) | Backward (ms) | Microbatch
(ms) | Training update (ms) |
|---|---|---|---|---|
| 27,116 (issue), uniform | 4.80 / 4.22 (1.14x) | 9.60 / 6.78 (1.42x) |
70.49 / 16.99 (4.15x) | 446.64 / 167.56 (2.67x) |
| 32,768 (capacity), uniform | 7.71 / 6.06 (1.27x) | 11.93 / 8.84
(1.35x) | 78.56 / 22.73 (3.46x) | 528.64 / 218.37 (2.42x) |
| 27,116, skewed (max/mean expert load 1.51) | 8.80 / 6.60 (1.33x) |
15.91 / 11.00 (1.45x) | 84.99 / 25.95 (3.28x) | 587.96 / 251.99 (2.33x)
|
| 27,116, skewed (max/mean expert load 3.05) | 17.01 / 11.71 (1.45x) |
36.30 / 23.17 (1.57x) | 121.53 / 48.26 (2.52x) | 956.78 / 479.79 (1.99x)
|

*NVIDIA Vera Rubin (R200, sm_107a, 212 SMs), 8 GPUs (2 x 4, one NVLink
domain), driver 620.62, CUDA 13.4 toolkit, PyTorch 2.14.1+cu130. Shape:
hidden 4096, intermediate 2048, 288 experts, top-8, clamped SwiGLU limit
10, EP8, FP32 weight gradients. Times are in ms, median, max over ranks.
Microbatch = one MXFP8 weight quantization + forward + full-forward
checkpoint replay + backward. Training update = MoE part of one
optimizer update: 5 layers x 2 microbatches, with one weight
quantization per layer, then per microbatch a forward pass over all
layers and, in reverse, replay + backward. 40:28 = forward:backward
communication SMs used in the issue report.*

**MXFP8: previous version hand-tuned to 60:60 vs this PR (default
`auto`)**, previous / new (speedup)

| Tokens per rank, routing | Forward (ms) | Backward (ms) | Microbatch
(ms) | Training update (ms) |
|---|---|---|---|---|
| 27,116 (issue), uniform | 4.14 / 4.22 (0.98x) | 6.71 / 6.78 (0.99x) |
64.13 / 16.99 (3.78x) | 409.10 / 167.56 (2.44x) |
| 32,768 (capacity), uniform | 6.13 / 6.06 (1.01x) | 8.81 / 8.84 (1.00x)
| 72.53 / 22.73 (3.19x) | 466.10 / 218.37 (2.13x) |
| 27,116, skewed (max/mean expert load 1.51) | 7.15 / 6.60 (1.08x) |
10.98 / 11.00 (1.00x) | 76.40 / 25.95 (2.94x) | 505.80 / 251.99 (2.01x)
|
| 27,116, skewed (max/mean expert load 3.05) | 12.72 / 11.71 (1.09x) |
23.07 / 23.17 (1.00x) | 99.73 / 48.26 (2.07x) | 740.70 / 479.79 (1.54x)
|

*Same setup and definitions as above. Here the previous version is
hand-tuned to 60:60, the new Rubin default. Forward and backward are
0.98-1.09x.*

**Training update, MXFP8 (this PR) vs BF16 (same build)**

| Tokens per rank, routing | BF16 at 40:28 (ms) | BF16 at 28:32 (ms) |
MXFP8, this PR (ms) | MXFP8 speedup vs best BF16 |
|---|---|---|---|---|
| 27,116 (issue), uniform | 232.8 | 232.4 | 167.6 | 1.39x |
| 32,768 (capacity), uniform | 283.5 | 295.0 | 218.4 | 1.30x |
| 27,116, skewed (max/mean expert load 1.51) | 349.6 | 353.1 | 252.0 |
1.39x |
| 27,116, skewed (max/mean expert load 3.05) | 711.8 | 729.9 | 479.8 |
1.48x |

*Same setup and definitions as above. BF16 is run at forward:backward
communication-SM splits 40:28 and 28:32.*

The family's other seven Cake variants cover the remaining combinations
of precision (BF16, MXFP8), activation (SwiGLU, clamped SwiGLU) and
weight-gradient accumulator (BF16, FP32). All eight ship forward,
recompute and backward programs for sm_100a, sm_103a and sm_107a (48
libraries per architecture).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Rubin-specific MXFP8 communication settings and device-aware
imbalance thresholds.
* CUDA-based MXFP8 weight quantization now supports CUDA Graph capture,
with a PyTorch fallback that produces matching results.
* **Bug Fixes**
* Improved use of completed routed-load observations when selecting
communication settings.
* **Documentation**
* Expanded guidance and benchmark results for Rubin MXFP8 and BF16,
including quantization behavior and validation coverage.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [35d0b53](https://github.com/flashinfer-ai/flashinfer/commit/35d0b531f51015e481cdfdc82dc7a727528abdad)

- **作者**: eigen
- **时间**: 2026-10-29T18:40:14Z
- **提交信息**: perf(cake_grouped_fp8_gemm): window-segment KG1 program for validated FP32-scale layouts with expert runs inside a 128-row window (#7877)

The Cake contiguous grouped FP8 GEMM (`cake_grouped_fp8_gemm`) is used
through `flashinfer.gemm.prepare_group_gemm_fp8_nt_groupwise_contiguous`
and its launch. It takes FP8 E4M3 inputs and produces BF16 output, with
rows grouped by `m_indices`. It supports two scale formats: FP32 per-128
block scales and packed UE8M0 block scales. This PR changes only
validated FP32-scale launches that take the expert-aligned scale-group-1
(KG1) program and whose expert runs start inside a 128-row window. Let
window_runs be the largest number of expert runs in one 128-row window.
When ceil(M / 128) x window_runs x ceil(N / 64) CTAs fit in one wave,
such a launch now takes a new KG1 program with 128 x 64 output tiles.
The new program gives each window window_runs CTAs per column tile, and
each CTA computes one expert run. It reads the runs from `m_indices` at
every launch, so it stays correct when a later `m_indices` has more runs
per window. Outside the program's launch contract (1 <= M <= 2**24, 64
<= N <= 2**19), the host keeps the expert-aligned program. The baseline
is FlashInfer main, which includes the previous Cake version of this
kernel. In the tables below, only correctness_unaligned_transition and
random_s9_m777_g8_n256_k512 change program. Every other row keeps its
program.

Latency per call is in microseconds, the median over 3 runs (3 seeds). q
is the median over the 3 runs of this PR / FlashInfer main, and speedup
= 1 / q. So the speedup can differ slightly from the ratio of the two
latencies. The verdict is FASTER, TIE or SLOWER against the row's noise
band, shown in brackets. "TIE (same program both sides)" means that both
sides run the same program. "TIE [arm-swap A/A]" means that both sides
run the same program and that the row was re-timed with the two sides
swapped, which read TIE. The CuTe-DSL column is FlashInfer's CuTe-DSL
grouped GEMM on the per-expert 128-row-padded layout. It is shown for
the 2 rows that change program, with WIN, TIE or BEHIND against its
noise band.

**NVIDIA GB300, sm_103a (152 SMs), faster board class, driver
580.159.03, nvcc 13.4, torch 2.14.1+cu130 (CUDA 13.0 runtime); 45 rows
(the 2 rows that change program and the 43-row shape list); baseline
FlashInfer main**

| # | shape | M | N | K | groups | program (this PR) | FI main (us) |
this PR (us) | speedup | verdict [noise] | CuTe-DSL (us) | vs CuTe-DSL
[noise] |
|---:|---|---:|---:|---:|---:|---|---:|---:|---:|---|---:|---|
| 1 | correctness_unaligned_transition | 65 | 128 | 128 | 2 |
deepk_c2_kg1_wseg 4 CTAs | 5.728 | 4.320 | 1.326x | FASTER [0.0056] |
4.448 | WIN [0.0056] |
| 2 | random_s9_m777_g8_n256_k512 | 777 | 256 | 512 | 8 |
deepk_c2_kg1_wseg 84 CTAs | 6.720 | 4.896 | 1.373x | FASTER [0.0066] |
5.776 | WIN [0.0066] |
| 3 | correctness_128_64 | 192 | 128 | 128 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.256 | 4.256 | 1.008x | TIE [0.0075]
| - | - |
| 4 | correctness_cross_m256_k896 | 257 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 6 CTAs | 5.056 | 5.056 | 1.000x | TIE [0.0159]
| - | - |
| 5 | correctness_exact_m128 | 128 | 128 | 512 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.480 | 4.464 | 1.004x | TIE (same
program both sides) [0.0072] | - | - |
| 6 | correctness_exact_m256_k768 | 256 | 512 | 768 | 1 |
deepk_c2_kg1_n64_k_blocks 16 CTAs | 5.120 | 5.120 | 1.000x | TIE
[0.0063] | - | - |
| 7 | correctness_final_127_k1152 | 255 | 256 | 1152 | 2 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 5.728 | 5.728 | 1.000x | TIE [0.0111]
| - | - |
| 8 | correctness_final_129_k1408 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 6.272 | 6.256 | 1.000x | TIE
[0.0077] | - | - |
| 9 | correctness_internal_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.480 | 4.512 | 0.993x | TIE [0.0071]
| - | - |
| 10 | correctness_leading_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.544 | 4.544 | 0.997x | TIE [0.0071]
| - | - |
| 11 | correctness_stream_k128 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.224 | 4.224 | 1.000x | TIE
[0.0076] | - | - |
| 12 | correctness_tail_1 | 1 | 128 | 128 | 1 |
deepk_c2_kg1_direct_store_m32 1 CTAs | 4.416 | 4.416 | 1.000x | TIE
[0.0073] | - | - |
| 13 | correctness_tail_127_k256 | 127 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.384 | 4.384 | 1.000x | TIE [0.0073]
| - | - |
| 14 | correctness_tail_255_k640 | 255 | 640 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 20 CTAs | 4.768 | 4.768 | 1.000x | TIE
[0.0068] | - | - |
| 15 | correctness_tail_64 | 64 | 256 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.416 | 4.416 | 1.000x | TIE [0.0146]
| - | - |
| 16 | correctness_two_full_k1280 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 5.744 | 5.744 | 1.000x | TIE
[0.0084] | - | - |
| 17 | attr_m128_n128_k1152 | 128 | 128 | 1152 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.520 | 5.568 | 0.991x | TIE [0.0116]
| - | - |
| 18 | attr_m128_n128_k128 | 128 | 128 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.192 | 4.160 | 1.008x | TIE [0.0150]
| - | - |
| 19 | attr_m128_n128_k1408 | 128 | 128 | 1408 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 6.112 | 6.112 | 1.000x | TIE [0.0053]
| - | - |
| 20 | attr_m128_n128_k256 | 128 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.384 | 4.384 | 1.000x | TIE [0.0000]
| - | - |
| 21 | attr_m128_n128_k384 | 128 | 128 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.432 | 4.432 | 1.000x | TIE [0.0143]
| - | - |
| 22 | attr_m128_n128_k640 | 128 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.800 | 4.800 | 1.000x | TIE [0.0067]
| - | - |
| 23 | attr_m128_n128_k896 | 128 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.184 | 5.184 | 1.000x | TIE [0.0062]
| - | - |
| 24 | attr_m128_n1536_k640 | 128 | 1536 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.800 | 4.800 | 1.000x | TIE
[0.0067] | - | - |
| 25 | attr_m128_n512_k640 | 128 | 512 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.800 | 4.800 | 1.000x | TIE [0.0067]
| - | - |
| 26 | attr_m64_n128_k640 | 64 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.768 | 4.768 | 1.000x | TIE [0.0068]
| - | - |
| 27 | b144_g4_k896 | 2303 | 512 | 896 | 4 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 10.752 | 10.752 | 1.000x | TIE [0.0090] | - | - |
| 28 | b144_k128 | 1152 | 1024 | 128 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 4.288 | 4.320 | 0.996x | TIE [0.0149] | - | - |
| 29 | b144_k1408 | 2304 | 512 | 1408 | 1 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 6.336 | 6.336 | 1.000x | TIE [0.0051] | - | - |
| 30 | b144_k640 | 2304 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.024 | 5.024 | 1.000x | TIE [0.0064] | - | - |
| 31 | b144t_k640 | 2303 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.024 | 4.992 | 1.000x | TIE [0.0064] | - | - |
| 32 | b152_k640 | 2432 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 152
CTAs | 5.088 | 5.088 | 1.000x | TIE [0.0063] | - | - |
| 33 | b72_k640 | 1152 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 72
CTAs | 4.928 | 4.944 | 0.997x | TIE [0.0065] | - | - |
| 34 | eanear_m256_n384_k1280_g2_b1 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 7.936 | 7.936 | 1.000x | TIE
[0.0040] | - | - |
| 35 | eanear_m257_n512_k1408_g2_b1 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 7.616 | 7.616 | 1.000x | TIE
[0.0042] | - | - |
| 36 | eanear_m768_n256_k128_g4_b1 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.672 | 4.672 | 1.000x | TIE
[0.0034] | - | - |
| 37 | n64e_m129_n128_k256 | 129 | 128 | 256 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.352 | 4.352 | 1.000x | TIE [0.0073]
| - | - |
| 38 | n64e_m4096_n128_k128 | 4096 | 128 | 128 | 8 |
deepk_c2_kg1_n64_k_blocks 64 CTAs | 4.384 | 4.384 | 1.000x | TIE
[0.0073] | - | - |
| 39 | smallk_m48_n1536_k128 | 48 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.192 | 4.192 | 1.000x | TIE
[0.0077] | - | - |
| 40 | smallk_m48_n1536_k256 | 48 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.288 | 4.288 | 1.000x | TIE
[0.0000] | - | - |
| 41 | smallk_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.160 | 4.160 | 1.000x | TIE
[0.0000] | - | - |
| 42 | smallk_m64_n1536_k256 | 64 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.256 | 4.288 | 0.996x | TIE
[0.0075] | - | - |
| 43 | smallk_m64_n256_k128 | 64 | 256 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 3.873 | 3.888 | 0.996x | TIE [0.0164]
| - | - |
| 44 | smallm_m48_n2048_k640 | 48 | 2048 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 32 CTAs | 4.784 | 4.768 | 1.003x | TIE
[0.0067] | - | - |
| 45 | smallm_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.160 | 4.160 | 1.000x | TIE
[0.0000] | - | - |

**NVIDIA GB300, sm_103a (152 SMs), slower board class, driver
580.159.03, nvcc 13.4, torch 2.14.1+cu130 (CUDA 13.0 runtime); 45 rows
(the 2 rows that change program and the 43-row shape list); baseline
FlashInfer main**

| # | shape | M | N | K | groups | program (this PR) | FI main (us) |
this PR (us) | speedup | verdict [noise] | CuTe-DSL (us) | vs CuTe-DSL
[noise] |
|---:|---|---:|---:|---:|---:|---|---:|---:|---:|---|---:|---|
| 1 | correctness_unaligned_transition | 65 | 128 | 128 | 2 |
deepk_c2_kg1_wseg 4 CTAs | 5.184 | 4.096 | 1.266x | FASTER [0.0158] |
4.464 | WIN [0.0158] |
| 2 | random_s9_m777_g8_n256_k512 | 777 | 256 | 512 | 8 |
deepk_c2_kg1_wseg 84 CTAs | 6.640 | 4.736 | 1.402x | FASTER [0.0073] |
5.888 | WIN [0.0073] |
| 3 | correctness_128_64 | 192 | 128 | 128 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.000 | 4.016 | 0.996x | TIE [0.0080]
| - | - |
| 4 | correctness_cross_m256_k896 | 257 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 6 CTAs | 5.056 | 5.056 | 1.000x | TIE [0.0064]
| - | - |
| 5 | correctness_exact_m128 | 128 | 128 | 512 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.544 | 4.576 | 0.993x | TIE (same
program both sides) [0.0070] | - | - |
| 6 | correctness_exact_m256_k768 | 256 | 512 | 768 | 1 |
deepk_c2_kg1_n64_k_blocks 16 CTAs | 4.896 | 4.896 | 1.000x | TIE
[0.0130] | - | - |
| 7 | correctness_final_127_k1152 | 255 | 256 | 1152 | 2 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 5.376 | 5.392 | 0.997x | TIE [0.0059]
| - | - |
| 8 | correctness_final_129_k1408 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 5.984 | 5.984 | 1.003x | TIE
[0.0053] | - | - |
| 9 | correctness_internal_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.304 | 4.304 | 1.000x | TIE [0.0147]
| - | - |
| 10 | correctness_leading_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.304 | 4.288 | 1.004x | TIE [0.0074]
| - | - |
| 11 | correctness_stream_k128 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.224 | 4.224 | 1.000x | TIE
[0.0076] | - | - |
| 12 | correctness_tail_1 | 1 | 128 | 128 | 1 |
deepk_c2_kg1_direct_store_m32 1 CTAs | 4.048 | 4.032 | 1.000x | TIE
[0.0080] | - | - |
| 13 | correctness_tail_127_k256 | 127 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.176 | 4.160 | 1.004x | TIE [0.0115]
| - | - |
| 14 | correctness_tail_255_k640 | 255 | 640 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 20 CTAs | 4.608 | 4.608 | 1.000x | TIE
[0.0069] | - | - |
| 15 | correctness_tail_64 | 64 | 256 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.256 | 4.256 | 1.000x | TIE [0.0076]
| - | - |
| 16 | correctness_two_full_k1280 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 5.728 | 5.728 | 1.000x | TIE
[0.0056] | - | - |
| 17 | attr_m128_n128_k1152 | 128 | 128 | 1152 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.408 | 5.408 | 0.994x | TIE [0.0175]
| - | - |
| 18 | attr_m128_n128_k128 | 128 | 128 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.096 | 4.096 | 1.000x | TIE [0.0079]
| - | - |
| 19 | attr_m128_n128_k1408 | 128 | 128 | 1408 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 6.112 | 6.112 | 1.000x | TIE [0.0159]
| - | - |
| 20 | attr_m128_n128_k256 | 128 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.144 | 4.160 | 0.996x | TIE [0.0115]
| - | - |
| 21 | attr_m128_n128_k384 | 128 | 128 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.352 | 4.352 | 1.000x | TIE [0.0073]
| - | - |
| 22 | attr_m128_n128_k640 | 128 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.592 | 4.593 | 1.000x | TIE [0.0069]
| - | - |
| 23 | attr_m128_n128_k896 | 128 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.120 | 5.136 | 1.000x | TIE [0.0063]
| - | - |
| 24 | attr_m128_n1536_k640 | 128 | 1536 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.736 | 4.736 | 1.000x | TIE
[0.0000] | - | - |
| 25 | attr_m128_n512_k640 | 128 | 512 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.592 | 4.592 | 1.000x | TIE [0.0102]
| - | - |
| 26 | attr_m64_n128_k640 | 64 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.592 | 4.576 | 1.004x | TIE [0.0069]
| - | - |
| 27 | b144_g4_k896 | 2303 | 512 | 896 | 4 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 11.424 | 11.424 | 1.000x | TIE [0.0056] | - | - |
| 28 | b144_k128 | 1152 | 1024 | 128 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 4.240 | 4.256 | 0.996x | TIE [0.0152] | - | - |
| 29 | b144_k1408 | 2304 | 512 | 1408 | 1 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 6.320 | 6.304 | 1.002x | TIE [0.0051] | - | - |
| 30 | b144_k640 | 2304 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.024 | 5.024 | 1.000x | TIE [0.0064] | - | - |
| 31 | b144t_k640 | 2303 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.024 | 5.024 | 1.000x | TIE [0.0064] | - | - |
| 32 | b152_k640 | 2432 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 152
CTAs | 5.024 | 5.024 | 1.000x | TIE [0.0064] | - | - |
| 33 | b72_k640 | 1152 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 72
CTAs | 4.928 | 4.896 | 1.006x | TIE [0.0065] | - | - |
| 34 | eanear_m256_n384_k1280_g2_b1 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 7.776 | 7.776 | 1.000x | TIE
[0.0041] | - | - |
| 35 | eanear_m257_n512_k1408_g2_b1 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 7.840 | 7.872 | 0.996x | TIE
[0.0061] | - | - |
| 36 | eanear_m768_n256_k128_g4_b1 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.416 | 4.416 | 1.000x | TIE
[0.0000] | - | - |
| 37 | n64e_m129_n128_k256 | 129 | 128 | 256 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.144 | 4.144 | 1.000x | TIE [0.0115]
| - | - |
| 38 | n64e_m4096_n128_k128 | 4096 | 128 | 128 | 8 |
deepk_c2_kg1_n64_k_blocks 64 CTAs | 4.352 | 4.384 | 1.000x | TIE
[0.0073] | - | - |
| 39 | smallk_m48_n1536_k128 | 48 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.064 | 4.064 | 1.000x | TIE
[0.0078] | - | - |
| 40 | smallk_m48_n1536_k256 | 48 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.192 | 4.192 | 1.000x | TIE
[0.0076] | - | - |
| 41 | smallk_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.096 | 4.096 | 1.000x | TIE
[0.0079] | - | - |
| 42 | smallk_m64_n1536_k256 | 64 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.224 | 4.224 | 1.000x | TIE
[0.0076] | - | - |
| 43 | smallk_m64_n256_k128 | 64 | 256 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 3.936 | 3.936 | 1.000x | TIE [0.0123]
| - | - |
| 44 | smallm_m48_n2048_k640 | 48 | 2048 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 32 CTAs | 4.896 | 4.896 | 1.000x | TIE
[0.0066] | - | - |
| 45 | smallm_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.096 | 4.096 | 1.000x | TIE
[0.0000] | - | - |

**NVIDIA B200, sm_100a (148 SMs), driver 580.82.07, nvcc 13.4, torch
2.14.1+cu130 (CUDA 13.0 runtime); 44 rows (the 2 rows that change
program and the 42-row shape list); baseline FlashInfer main**

| # | shape | M | N | K | groups | program (this PR) | FI main (us) |
this PR (us) | speedup | verdict [noise] | CuTe-DSL (us) | vs CuTe-DSL
[noise] |
|---:|---|---:|---:|---:|---:|---|---:|---:|---:|---|---:|---|
| 1 | correctness_unaligned_transition | 65 | 128 | 128 | 2 |
deepk_c2_kg1_wseg 4 CTAs | 5.312 | 4.192 | 1.267x | FASTER [0.0039] |
4.496 | WIN [0.0070] |
| 2 | random_s9_m777_g8_n256_k512 | 777 | 256 | 512 | 8 |
deepk_c2_kg1_wseg 84 CTAs | 6.880 | 5.024 | 1.369x | FASTER [0.0063] |
6.048 | WIN [0.0063] |
| 3 | correctness_128_64 | 192 | 128 | 128 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.192 | 4.192 | 1.000x | TIE [0.0002]
| - | - |
| 4 | correctness_cross_m256_k896 | 257 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 6 CTAs | 5.312 | 5.328 | 0.997x | TIE [0.0092]
| - | - |
| 5 | correctness_exact_m128 | 128 | 128 | 512 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.640 | 4.640 | 1.000x | TIE (same
program both sides) [0.0068] | - | - |
| 6 | correctness_exact_m256_k768 | 256 | 512 | 768 | 1 |
deepk_c2_kg1_n64_k_blocks 16 CTAs | 5.120 | 5.120 | 1.000x | TIE
[0.0062] | - | - |
| 7 | correctness_final_127_k1152 | 255 | 256 | 1152 | 2 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 5.600 | 5.585 | 1.003x | TIE [0.0086]
| - | - |
| 8 | correctness_final_129_k1408 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 6.304 | 6.336 | 0.995x | TIE
[0.0076] | - | - |
| 9 | correctness_internal_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.480 | 4.480 | 1.000x | TIE [0.0036]
| - | - |
| 10 | correctness_leading_empty | 129 | 256 | 384 | 3 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.431 | 4.431 | 1.004x | TIE [0.0071]
| - | - |
| 11 | correctness_stream_k128 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.320 | 4.320 | 1.000x | TIE
[0.0145] | - | - |
| 12 | correctness_tail_1 | 1 | 128 | 128 | 1 |
deepk_c2_kg1_direct_store_m32 1 CTAs | 4.304 | 4.303 | 0.997x | TIE
[0.0111] | - | - |
| 13 | correctness_tail_127_k256 | 127 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.272 | 4.272 | 1.000x | TIE [0.0113]
| - | - |
| 14 | correctness_tail_255_k640 | 255 | 640 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 20 CTAs | 4.832 | 4.832 | 1.000x | TIE
[0.0133] | - | - |
| 15 | correctness_tail_64 | 64 | 256 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.416 | 4.416 | 1.000x | TIE [0.0073]
| - | - |
| 16 | correctness_two_full_k1280 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 5.968 | 5.984 | 1.000x | TIE
[0.0107] | - | - |
| 17 | attr_m128_n128_k1152 | 128 | 128 | 1152 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.632 | 5.632 | 1.000x | TIE [0.0057]
| - | - |
| 18 | attr_m128_n128_k128 | 128 | 128 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.176 | 4.192 | 1.000x | TIE [0.0076]
| - | - |
| 19 | attr_m128_n128_k1408 | 128 | 128 | 1408 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 6.113 | 6.112 | 1.000x | TIE [0.0078]
| - | - |
| 20 | attr_m128_n128_k256 | 128 | 128 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.288 | 4.288 | 1.000x | TIE [0.0149]
| - | - |
| 21 | attr_m128_n128_k384 | 128 | 128 | 384 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.480 | 4.480 | 1.000x | TIE
[arm-swap A/A] | - | - |
| 22 | attr_m128_n128_k640 | 128 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.736 | 4.720 | 1.003x | TIE [0.0066]
| - | - |
| 23 | attr_m128_n128_k896 | 128 | 128 | 896 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 5.248 | 5.248 | 1.000x | TIE [0.0180]
| - | - |
| 24 | attr_m128_n1536_k640 | 128 | 1536 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.944 | 4.960 | 0.997x | TIE
[0.0063] | - | - |
| 25 | attr_m128_n512_k640 | 128 | 512 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 8 CTAs | 4.800 | 4.800 | 1.000x | TIE [0.0067]
| - | - |
| 26 | attr_m64_n128_k640 | 64 | 128 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 2 CTAs | 4.720 | 4.704 | 1.003x | TIE [0.0102]
| - | - |
| 27 | b144_g4_k896 | 2303 | 512 | 896 | 4 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 11.873 | 11.856 | 1.001x | TIE [0.0054] | - | - |
| 28 | b144_k128 | 1152 | 1024 | 128 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 4.384 | 4.384 | 1.000x | TIE [0.0073] | - | - |
| 29 | b144_k1408 | 2304 | 512 | 1408 | 1 | deepk_c2_kg1_n64_k_blocks
144 CTAs | 6.705 | 6.688 | 1.000x | TIE [0.0048] | - | - |
| 30 | b144_k640 | 2304 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.280 | 5.280 | 1.000x | TIE [0.0059] | - | - |
| 31 | b144t_k640 | 2303 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 144
CTAs | 5.280 | 5.280 | 1.000x | TIE [arm-swap A/A] | - | - |
| 32 | b72_k640 | 1152 | 512 | 640 | 1 | deepk_c2_kg1_n64_k_blocks 72
CTAs | 5.152 | 5.152 | 1.000x | TIE [0.0062] | - | - |
| 33 | eanear_m256_n384_k1280_g2_b1 | 256 | 384 | 1280 | 2 |
deepk_c2_kg1_n64_k_blocks 12 CTAs | 8.256 | 8.224 | 1.000x | TIE
[0.0039] | - | - |
| 34 | eanear_m257_n512_k1408_g2_b1 | 257 | 512 | 1408 | 2 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 8.096 | 8.080 | 1.002x | TIE
[0.0078] | - | - |
| 35 | eanear_m768_n256_k128_g4_b1 | 768 | 256 | 128 | 4 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.608 | 4.608 | 1.000x | TIE
[0.0069] | - | - |
| 36 | n64e_m129_n128_k256 | 129 | 128 | 256 | 2 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.288 | 4.320 | 0.993x | TIE [0.0075]
| - | - |
| 37 | n64e_m4096_n128_k128 | 4096 | 128 | 128 | 8 |
deepk_c2_kg1_n64_k_blocks 64 CTAs | 4.576 | 4.559 | 1.004x | TIE
[0.0141] | - | - |
| 38 | smallk_m48_n1536_k128 | 48 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.240 | 4.256 | 0.996x | TIE
[0.0075] | - | - |
| 39 | smallk_m48_n1536_k256 | 48 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.399 | 4.383 | 1.004x | TIE
[0.0145] | - | - |
| 40 | smallk_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.224 | 4.224 | 1.000x | TIE
[0.0152] | - | - |
| 41 | smallk_m64_n1536_k256 | 64 | 1536 | 256 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.383 | 4.384 | 1.000x | TIE
[arm-swap A/A] | - | - |
| 42 | smallk_m64_n256_k128 | 64 | 256 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 4 CTAs | 4.080 | 4.064 | 1.004x | TIE [0.0156]
| - | - |
| 43 | smallm_m48_n2048_k640 | 48 | 2048 | 640 | 1 |
deepk_c2_kg1_n64_k_blocks 32 CTAs | 5.152 | 5.152 | 1.000x | TIE
[0.0064] | - | - |
| 44 | smallm_m64_n1536_k128 | 64 | 1536 | 128 | 1 |
deepk_c2_kg1_n64_k_blocks 24 CTAs | 4.224 | 4.224 | 1.000x | TIE
[0.0076] | - | - |

Cake also ships the UE8M0 block-scaled programs of this kernel and three
sibling kernels: the masked batched FP8 GEMM
(`flashinfer.gemm.batch_deepgemm_fp8_nt_groupwise(...,
backend="cake")`), the fused grouped FP8 GEMM + SwiGLU + FP8
quantization (`cake_grouped_fp8_fused_silu_quant`) and the grouped MXFP8
quantizer (`cake_grouped_mxfp8_quantize`); the whole family ships for
sm_100a (B200) and sm_103a (GB300), and every program of this kernel is
built for both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optimized route for grouped FP8 matrix multiplication on
supported GPUs. It adapts launch planning to input layout and device
limits, including layouts with multiple group runs within a row window.
* **Bug Fixes**
* Improved handling of changing group-index layouts, including during
CUDA graph replay. When the optimized route exceeds launch constraints,
the operation falls back to an available alternative.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [193e270](https://github.com/flashinfer-ai/flashinfer/commit/193e270ab4a9956a79fb166d4ff96a3a435eff5d)

- **作者**: eigen
- **时间**: 2026-10-29T18:08:08Z
- **提交信息**: perf(cake_minimax_h3): lazy output rescale in the sequential SM120 FP8 varlen attention (#7871)

The MiniMax-H3 non-causal packed-varlen attention kernel takes THD
tensors ([tokens, 56 heads, 128 head dim]) with int32 `cu_seqlens`.
FlashInfer has four Cake variants of it, all on sm_120a: three NVFP4-QK
forms and one FP8 form. This PR changes the FP8 form,
`minimax_h3_sm120_varlen_attention_fp8`, in the attention program of its
sequential form. Before each online-softmax output rescale, each warp
now votes. If no row maximum of the warp moved on that K tile, every
rescale factor is exactly 1.0, and the warp skips the multiplies. Since
x * 1.0 == x, outputs are bitwise equal to FlashInfer main. The baseline
is the previous Cake version of the same op, which is FlashInfer main.
Latency is the median GPU time per call of the whole op, with cold L2.
Speedup = FlashInfer main / this PR.

Long sequential shapes run faster on both GPUs. For example, center_15s
runs at 1.017x on both GPUs. Rows marked "(within noise)" are not
claimed as speedups. m1 on the RTX PRO 6000 (0.984x) and seg_133_300_900
on the RTX 5090 (0.992x) are within run-to-run noise. Rows marked
"(unchanged)" use the overlapped form. Their programs did not change.

### NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | FI main (us) | this PR (us) | speedup |
|---|---|---|---|---|
| center_4s | 33472 | 48222.90 | 47539.40 | 1.014x |
| center_5s | 38592 | 63645.22 | 62688.56 | 1.015x |
| center_6s | 48768 | 100688.75 | 99154.64 | 1.015x |
| center_8s | 58944 | 146714.95 | 144326.55 | 1.017x |
| center_10s | 74240 | 231167.98 | 227086.72 | 1.018x |
| center_15s | 109952 | 504077.56 | 495508.70 | 1.017x |
| tail_5s_a | 38531 | 63660.67 | 62732.51 | 1.015x |
| tail_5s_b | 38629 | 63722.54 | 62750.67 | 1.015x |
| pad_15s | 109952 | 504066.22 | 495429.75 | 1.017x |
| seg4 | 33472 | 12605.52 | 12608.28 | 1.000x (unchanged) |
| seg3_ragged | 4824 | 964.98 | 964.83 | 1.000x (unchanged) |
| seg_empty | 500 | 58.81 | 58.62 | 1.003x (within noise) |
| single_4096 | 4096 | 835.48 | 835.05 | 1.001x (unchanged) |
| m1 | 1 | 15.98 | 16.24 | 0.984x (within noise) |
| m128 | 128 | 26.40 | 26.12 | 1.011x (within noise) |
| m129 | 129 | 30.52 | 30.50 | 1.000x (within noise) |
| seg_133_300_900 | 900 | 103.02 | 102.01 | 1.010x |
| s6144 | 6144 | 1687.91 | 1687.38 | 1.000x (unchanged) |
| x3_l26000 | 26000 | 29140.58 | 28748.62 | 1.014x |
| x3_l2x25000 | 50000 | 54773.71 | 54009.54 | 1.014x |
| x3_lrag3 | 53000 | 76692.34 | 75566.88 | 1.015x |
| x3_l52000p | 52000 | 114104.68 | 112552.48 | 1.014x |
| x3_s1500 | 1500 | 205.86 | 204.97 | 1.004x (within noise) |
| x3_s3x900 | 2700 | 341.00 | 338.56 | 1.007x |
| s2048 | 2048 | 315.22 | 314.72 | 1.002x |

NVIDIA RTX PRO 6000 Blackwell Server Edition: 25 shapes; faster 16,
within noise 5, unchanged 4.

### NVIDIA GeForce RTX 5090 (sm_120, CUDA 13.4)

FI main vs this PR, latency per call in us (mean of two GPUs), speedup =
FI main / this PR.

| shape | tokens | FI main (us) | this PR (us) | speedup |
|---|---|---|---|---|
| center_4s | 33472 | 50888.36 | 50142.65 | 1.015x |
| center_5s | 38592 | 67727.53 | 66690.41 | 1.016x |
| center_6s | 48768 | 108336.60 | 106682.05 | 1.016x |
| center_8s | 58944 | 159025.67 | 156463.15 | 1.016x |
| center_10s | 74240 | 250861.79 | 246810.28 | 1.016x |
| center_15s | 109952 | 548106.85 | 538732.21 | 1.017x |
| tail_5s_a | 38531 | 67748.71 | 66781.41 | 1.014x |
| tail_5s_b | 38629 | 67742.72 | 66721.85 | 1.015x |
| pad_15s | 109952 | 547923.43 | 538577.81 | 1.017x |
| seg4 | 33472 | 13386.33 | 13402.13 | 0.999x (unchanged) |
| seg3_ragged | 4824 | 996.64 | 996.40 | 1.000x (unchanged) |
| seg_empty | 500 | 43.98 | 43.42 | 1.013x (within noise) |
| single_4096 | 4096 | 858.43 | 858.88 | 0.999x (unchanged) |
| m1 | 1 | 14.71 | 14.55 | 1.011x (within noise) |
| m128 | 128 | 21.63 | 21.71 | 0.997x (within noise) |
| m129 | 129 | 25.45 | 24.95 | 1.020x |
| seg_133_300_900 | 900 | 87.04 | 87.73 | 0.992x (within noise) |
| s6144 | 6144 | 1771.19 | 1770.22 | 1.001x (unchanged) |
| x3_l26000 | 26000 | 31011.93 | 30570.12 | 1.014x |
| x3_l2x25000 | 50000 | 57742.07 | 56936.75 | 1.014x |
| x3_lrag3 | 53000 | 81406.80 | 80228.54 | 1.015x |
| x3_l52000p | 52000 | 123154.10 | 121210.93 | 1.016x |
| x3_s1500 | 1500 | 195.90 | 195.49 | 1.002x (within noise) |
| x3_s3x900 | 2700 | 326.00 | 323.43 | 1.008x |
| s2048 | 2048 | 334.77 | 333.50 | 1.004x (within noise) |

NVIDIA GeForce RTX 5090: 25 shapes; faster 15, within noise 6, unchanged
4.

This SM120 family ships for sm_120a only, and its other Cake variants
are `minimax_h3_sm120_varlen_attention_nvfp4` (SageAttention3 FP4
recipe, compensated), `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`
(uncompensated) and the NVFP4-QK / FP8-PV form selected by
`pv_mode="fp8"` on the NVFP4 entry, while the same MiniMax-H3
packed-varlen attention op also ships for sm_100a (B200) and sm_103a
(GB300) as `minimax_h3_varlen_attention`, in BF16 and two NVFP4 forms
(`pv_mode="fp4"` and `pv_mode="fp8"`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Updated quantized variable-length attention processing with revised
score and normalization calculations.
* The operation’s parameters and configuration remain unchanged; no
changes to how it is called.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f62d3e1](https://github.com/flashinfer-ai/flashinfer/commit/f62d3e11087a8b9915f50000f44368f373b91f80)

- **作者**: eigen
- **时间**: 2026-10-29T18:07:54Z
- **提交信息**: perf(cake_ssd_combined): sm_107a wrap-around plan, z-prefetch and one-CTA-cluster programs, wider claim and pair routes (#7869)

`cake_ssd_combined` holds FlashInfer's Mamba2 SSD combined chunk-scan
prefill kernels, with 56 programs in seven families: retained exact scan
(11), fused exact scan `exactfused` (11, ring and no-ring schedules),
two-kernel exact scan `exactpre` (12, including the tail-wave pair
programs), metadata-stage fused varlen `exactmeta` (5), one-launch fused
varlen `exactone` (5), chunk-parallel `chunkpar` (6) and three-phase
chunk-parallel `chunkpar3` (6). This PR changes sm_107a (Rubin) only;
the sm_100a and sm_103a programs and routes are unchanged. It adds 2
fused batched z-prefetch programs, `exactfused_{bf16,f32}_batched_zpf`.
These are the fused batched ring program with an epilogue that loads the
next chunk's first z columns right after the current chunk has read
them. Fused batched calls with z of at least two chunks per item take
them. It also adds 5 one-CTA-cluster twins, which run the same device
code with a static 1x1x1 cluster attribute:
`exactpre_{bf16,f32}_varlen_unit` for static-order varlen calls of at
most 384 (sequence, head) items,
`exactone_{bf16,f32}_varlen_tablefirstunit` for one-sequence calls of at
most 8 heads, and `exactone_f32_varlen_tablerolesunit` for calls of at
least 128 tokens per sequence on average. In
`exactone_{bf16,f16}_varlen_noring`, each of the 7 warp roles now passes
the sequence-table barrier right before its work loop instead of in the
prologue. Two routes change. Batched bf16 calls without z and initial
states, of 768 to 4096 (sequence, head) items of 16 to 32 chunks, now
take the existing `exactpre` tail-pair program. fp32 one-chunk
packed-varlen calls now take the existing claim program from 1024 items
and 4 items per CTA (previously more than 2048 items and 8 per CTA).
Finally, the PR adds 2 wrap-around plan programs,
`exactpre_{bf16,f32}_varlen_wrap`. These are the two-kernel varlen
program, launched like the one-CTA pair programs (one CTA per SM), with
a grid-wide plan. Each CTA draws a slot from a ticket and runs one
contiguous range of the call's (sequence, head) items, with each item
weighing its chunks plus one. An item cut between two slots hands its
fp32 state to the next slot through two parked output rows and one flag
bit per slot boundary. Varlen bf16 / fp32 calls without z, with more
items than SMs and at least 16 chunks per item, take it when the plan
cuts their chunk makespan to at most 0.9 of the current program's.
Outputs and final states are bitwise those of the programs these calls
ran before. The baseline is the previous Cake sm_107a round (#7740),
which is on FlashInfer main. Of the 93 shapes, 30 run a program or route
that this PR changes: 6 on the z-prefetch programs, 18 on the
one-CTA-cluster twins (11 `exactpre` unit, 5 `tablefirstunit`, 2
`tablerolesunit`), 1 on the bf16 no-ring table-barrier change
(`nem_v64_64_bfloat16`), 2 on the batched bf16 pair route, 2 on the
wider fp32 claim route and 1 on the wrap-around plan
(`perf_varlen_32x32`). Their pooled speedup is 1.005 to 1.125, with a
geometric mean of 1.023. The largest is on `perf_varlen_32x32`, from
112.59 to 100.04 µs. Of these 30, 28 are faster in both runs. The other
2 (`nem_v1000_bfloat16` and `nem_v1000_float32`, pooled 1.006 and 1.005)
are within measurement noise in one run. The other 63 shapes run the
same machine code and launches as the previous version and measure 0.997
to 1.001 (geometric mean 1.000). The geometric-mean speedup over all 93
shapes is 1.0073.

**NVIDIA R200 (sm_107a, Rubin), CUDA 13.4.** Latency of one whole
`cake_ssd_combined` call, including the preprocess and the main kernel
where the route uses two kernels. L2 is cold, and each value is the mean
over 16 rounds of 4 input copies, from two runs on two different
GPUs/nodes. Both sides were measured on the same GPU in each run.
Speedup = previous / this PR.

| Shape | Previous (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| perf_varlen_1x1 | 7.20 | 7.20 | 1.000 |
| perf_varlen_4x1 | 7.38 | 7.38 | 1.000 |
| perf_varlen_8x1 | 7.67 | 7.67 | 1.000 |
| perf_varlen_32x1 | 11.91 | 11.91 | 1.000 |
| perf_varlen_64x1 | 16.05 | 16.05 | 1.000 |
| perf_varlen_128x1 | 24.29 | 24.29 | 1.000 |
| perf_varlen_256x1 | 41.54 | 41.54 | 1.000 |
| perf_varlen_4x8 | 20.76 | 20.76 | 1.000 |
| perf_varlen_8x8 | 21.07 | 21.08 | 1.000 |
| perf_varlen_16x8 | 24.34 | 24.07 | 1.011 |
| perf_varlen_32x8 | 38.99 | 38.99 | 1.000 |
| perf_varlen_64x8 | 60.76 | 60.75 | 1.000 |
| perf_varlen_32x32 | 112.59 | 100.04 | 1.125 |
| perf_varlen_64x32 | 180.17 | 180.17 | 1.000 |
| perf_varlen_128x32 | 348.04 | 348.05 | 1.000 |
| perf_batched_1x1 | 5.78 | 5.79 | 0.999 |
| perf_batched_1x4 | 10.67 | 10.67 | 1.000 |
| perf_batched_4x1 | 5.97 | 5.98 | 0.999 |
| perf_batched_4x4 | 10.89 | 10.89 | 1.000 |
| perf_batched_16x1 | 6.89 | 6.90 | 0.999 |
| perf_batched_16x4 | 12.32 | 12.32 | 1.000 |
| perf_batched_16x16 | 33.55 | 33.55 | 1.000 |
| perf_batched_64x1 | 12.54 | 12.54 | 1.000 |
| perf_batched_64x4 | 29.70 | 29.71 | 1.000 |
| perf_batched_64x16 | 88.06 | 88.06 | 1.000 |
| perf_batched_128x1 | 18.63 | 18.63 | 1.000 |
| perf_batched_128x4 | 48.45 | 48.45 | 1.000 |
| perf_batched_128x16 | 161.50 | 159.69 | 1.011 |
| perf_batched_256x1 | 32.47 | 32.48 | 1.000 |
| perf_batched_256x4 | 88.63 | 88.63 | 1.000 |
| perf_batched_256x16 | 315.07 | 308.38 | 1.022 |
| perf_batched_512x2 | 92.65 | 92.65 | 1.000 |
| correctness_base_b2_n1 | 5.89 | 5.89 | 1.000 |
| correctness_D_head_dim | 5.80 | 5.80 | 1.000 |
| correctness_no_D | 5.77 | 5.77 | 1.000 |
| correctness_initial_bf16 | 5.89 | 5.89 | 1.001 |
| correctness_varlen_single_256 | 9.47 | 9.31 | 1.017 |
| correctness_varlen_nonaligned_z | 10.41 | 10.41 | 0.999 |
| correctness_preallocated_output | 5.77 | 5.78 | 0.999 |
| correctness_no_final_states | 5.76 | 5.78 | 0.998 |
| correctness_seq_idx_int64 | 9.50 | 9.51 | 0.999 |
| correctness_fp16_state | 5.92 | 5.92 | 1.001 |
| correctness_z_b1_n1 | 6.54 | 6.54 | 1.000 |
| perf_nemotron_h_8b_c128_projection_batched_b1x1 | 7.99 | 7.99 | 0.999
|
| perf_nemotron_h_8b_c128_projection_varlen_4x1 | 19.18 | 19.16 | 1.001
|
| nem_v1x128_bfloat16 | 9.80 | 9.80 | 1.000 |
| nem_v4x128_bfloat16 | 19.23 | 19.22 | 1.000 |
| nem_v16x128_bfloat16 | 48.11 | 48.12 | 1.000 |
| nem_v64x128_bfloat16 | 173.11 | 173.11 | 1.000 |
| nem_v160x128_bfloat16 | 419.48 | 419.48 | 1.000 |
| nem_v64_64_bfloat16 | 14.21 | 13.80 | 1.030 |
| nem_v8x64_bfloat16 | 28.56 | 28.54 | 1.001 |
| nem_v1024_bfloat16 | 28.49 | 28.24 | 1.009 |
| nem_v1024x2_bfloat16 | 45.20 | 45.18 | 1.000 |
| nem_v2048_bfloat16 | 48.46 | 47.93 | 1.011 |
| nem_v128p896_bfloat16 | 30.03 | 29.23 | 1.028 |
| nem_v96p160_bfloat16 | 16.59 | 16.59 | 1.000 |
| nem_v1000_bfloat16 | 28.43 | 28.27 | 1.006 |
| nem_v1024p100_bfloat16 | 33.48 | 32.77 | 1.022 |
| nem_b1x1024_bfloat16 | 25.29 | 24.57 | 1.029 |
| nem_b1x2048_bfloat16 | 44.42 | 43.70 | 1.016 |
| nem_b1x1000_bfloat16 | 25.22 | 24.49 | 1.030 |
| nem_v1x128_float32 | 10.09 | 9.94 | 1.015 |
| nem_v4x128_float32 | 19.52 | 19.57 | 0.997 |
| nem_v16x128_float32 | 49.08 | 47.63 | 1.030 |
| nem_v64x128_float32 | 161.76 | 161.77 | 1.000 |
| nem_v160x128_float32 | 389.03 | 389.04 | 1.000 |
| nem_v64_64_float32 | 13.53 | 13.53 | 1.000 |
| nem_v8x64_float32 | 28.11 | 27.70 | 1.015 |
| nem_v1024_float32 | 28.84 | 28.62 | 1.008 |
| nem_v1024x2_float32 | 45.99 | 45.96 | 1.001 |
| nem_v2048_float32 | 49.18 | 48.68 | 1.010 |
| nem_v128p896_float32 | 30.57 | 29.60 | 1.033 |
| nem_v96p160_float32 | 17.29 | 16.71 | 1.035 |
| nem_v1000_float32 | 28.58 | 28.42 | 1.005 |
| nem_v1024p100_float32 | 33.94 | 33.14 | 1.024 |
| nem_b1x1024_float32 | 25.35 | 24.66 | 1.028 |
| nem_b1x2048_float32 | 44.89 | 44.10 | 1.018 |
| nem_b1x1000_float32 | 25.12 | 24.60 | 1.021 |
| short_varlen_1 | 7.05 | 6.88 | 1.025 |
| short_varlen_8 | 7.05 | 6.86 | 1.027 |
| short_varlen_8_f32 | 7.55 | 7.37 | 1.025 |
| short_varlen_127 | 8.76 | 8.63 | 1.016 |
| short_varlen_64_60 | 7.29 | 7.29 | 1.000 |
| short_batched_2x50 | 10.14 | 10.15 | 0.999 |
| short_batched_1x1 | 6.00 | 6.00 | 1.000 |
| perf_batched_1x16 | 20.29 | 20.32 | 0.999 |
| perf_batched_1x64 | 34.23 | 34.21 | 1.001 |
| perf_batched_1x256 | 68.87 | 68.87 | 1.000 |
| perf_batched_4x16 | 32.50 | 32.50 | 1.000 |
| perf_batched_4x64 | 65.92 | 65.92 | 1.000 |
| cp_b1h32c16 | 31.89 | 31.88 | 1.000 |
| cp_b4h8c16 | 32.80 | 32.79 | 1.000 |

The same 56 programs also ship for sm_100a and sm_103a (Blackwell B200 /
B300) in all three state dtypes and both layouts, and this PR leaves
them unchanged. On sm_107a, 64 programs build their own sm_107a module;
24 of them are sm_107a-only programs, and this PR adds 9 of those.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved Mamba SSD execution on Rubin GPUs with additional optimized
paths for batched and variable-length workloads, including workloads
that use auxiliary state or `z` inputs.
* Kernel selection now adapts to workload size, data type, and GPU
configuration, helping improve execution efficiency across supported
cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [00341e8](https://github.com/flashinfer-ai/flashinfer/commit/00341e8a6694d4348697fdfd68c2947c09226150)

- **作者**: eigen
- **时间**: 2026-10-29T18:07:25Z
- **提交信息**: perf(cake_warp_decode): per-row FC1 pool sizes and FC2 launch choices on SM100/SM103 decode rows (#7868)

`cake_warp_decode` is Cake's NVFP4 routed fused-MoE decode for 1 to 32
tokens. It is called through
`flashinfer.fused_moe.trtllm_fp4_block_scale_routed_moe(...)` with
`CakeWarpDecodeConfig(backend="cake")`. It has one data type (NVFP4
W4A4, BF16 output), five activation variants and one fused form: FC1
with the activation, FC2 and the top-k finalize. This PR updates that
one fused form.

This PR changes only host-side launch choices. Device code and output
bits are unchanged.

- **FC1 CTA pool sizes.** The FC1 CTA pool size is now picked per row.
- **sm_100a, 2 changed rows.** `e128_i1536_k8` at 9 tokens launches the
existing K256 FC2 sibling build. That build claims work items before it
waits on FC1. `h4096_e512_i512_k10` at 2 tokens gets a new FC1 pool
size.
- **sm_103a, 7 changed rows.** `h3072_e256_i384_k8` at 7 tokens launches
a linear 152-CTA FC2 program. Six rows get new FC1 pool sizes:
`h3072_e256_i384_k8` at 3 and 4 tokens, `h3072_e256_i768_k8` at 2
tokens, `h4096_e512_i256_k10` at 4 tokens and `h4096_e512_i512_k10` at 2
and 4 tokens.
- **Other rows.** Every other row launches the same kernels as before:
510 rows on sm_100a and 473 on sm_103a.

The baseline is the current Cake version on FlashInfer main.

- On sm_100a (NVIDIA GB200, CUDA 13.4), no row of 512 in 16 geometries
is faster in both cold-L2 modes. One row is faster in the read mode:
`h4096_e512_i512_k10` at 2 tokens, 1.069x. No row is slower.
- On sm_103a (NVIDIA GB300, CUDA 13.4), 3 of 480 rows in 15 geometries
are faster in both cold-L2 modes, and 6 are faster in at least one. The
largest speedups are 1.051x with the memset flush and 1.074x with the
read flush, both on `h3072_e256_i768_k8` at 2 tokens. One row is slower
in one mode, and this PR does not change it: `e192_i1536_k4_silu` at 14
tokens, read, 73.33 us previous and 73.87 us new (ratio 1.007).

Every row that is faster in at least one mode is a row this PR changes.
That covers 1 of the 2 changed rows on sm_100a and 6 of the 7 on
sm_103a.

On changed rows across both modes, the speedup on sm_100a ranges from
1.003x to 1.069x (median 1.024x). On sm_103a it ranges from 0.997x to
1.074x (median 1.024x).

On sm_100a, no changed row prints a ratio above 1.000 (largest 0.997).
On sm_103a, one changed row does: `h3072_e256_i384_k8` at 7 tokens,
read, ratio 1.003. That row is not slower under the rule below. Every
other printed ratio above 1.000 is on an unchanged row. These reach at
most 1.013 on sm_100a (`e512_i512_k10`, 4 tokens, read;
`e192_i1536_k4_silu`, 1 token, read) and 1.013 on sm_103a
(`e384_i768_k4`, 4 tokens, read; `e192_i1536_k4_silu`, 4 tokens,
memset).

The "memset" and "read" column groups are two cold-L2 modes. Before
every call, we flush L2 with either a memset of a large buffer or a read
of one.

Each table value is the mean of four measurements: two GPUs (one on each
of two nodes), each measured in two separate processes. Each measurement
is the median over 6 rounds of the per-round median over 40 calls.

A row counts as faster (or slower) in a mode only when all four
measurements show it faster (or slower) by more than run-to-run noise.
That means every round agrees, and the median beats both a 0.5 % floor
and the A/A noise band.

Speedups in the summary tables are previous / new, so higher is better.
The per-row tables give ratio = new / previous, so lower is better
there.

**sm_100a** (NVIDIA GB200, CUDA 13.4)

| Geometry | Rows faster in both modes (of 32) | Best speedup, memset
(tokens) | Best speedup, read (tokens) |
|---|---|---|---|
| `h4096_e512_i512_k10` | 0 | — | 1.069x (2) |
| `e128_i1536_k8` | 0 | — | — |
| `e128_i3072_k4_swiglu_oa` | 0 | — | — |
| `e128_i768_k8` | 0 | — | — |
| `e192_i1536_k4_silu` | 0 | — | — |
| `e256_i1536_k8` | 0 | — | — |
| `e256_i2048_k6_clamp10` | 0 | — | — |
| `e256_i512_k8` | 0 | — | — |
| `e384_i768_k4` | 0 | — | — |
| `e512_i1024_k10` | 0 | — | — |
| `e512_i512_k10` | 0 | — | — |
| `e60_i1536_k4` | 0 | — | — |
| `e896_i3072_k16_situ` | 0 | — | — |
| `h3072_e256_i384_k8` | 0 | — | — |
| `h3072_e256_i768_k8` | 0 | — | — |
| `h4096_e512_i256_k10` | 0 | — | — |

**sm_103a** (NVIDIA GB300, CUDA 13.4)

| Geometry | Rows faster in both modes (of 32) | Best speedup, memset
(tokens) | Best speedup, read (tokens) |
|---|---|---|---|
| `h3072_e256_i768_k8` | 1 | 1.051x (2) | 1.074x (2) |
| `h3072_e256_i384_k8` | 1 | 1.038x (3) | 1.025x (4) |
| `h4096_e512_i512_k10` | 1 | 1.037x (2) | 1.034x (2) |
| `h4096_e512_i256_k10` | 0 | — | 1.038x (4) |
| `e128_i1536_k8` | 0 | — | — |
| `e128_i3072_k4_swiglu_oa` | 0 | — | — |
| `e128_i768_k8` | 0 | — | — |
| `e192_i1536_k4_silu` | 0 | — | — |
| `e256_i1536_k8` | 0 | — | — |
| `e256_i512_k8` | 0 | — | — |
| `e384_i768_k4` | 0 | — | — |
| `e512_i1024_k10` | 0 | — | — |
| `e512_i512_k10` | 0 | — | — |
| `e60_i1536_k4` | 0 | — | — |
| `e896_i3072_k16_situ` | 0 | — | — |

`e192_i1536_k4_silu` at 14 tokens is slower in the read mode: 73.33 us
previous, 73.87 us new (ratio 1.007).

**sm_100a** (NVIDIA GB200, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens: this PR changes the row's launches. Plain: the row launches
the same kernels as the previous version.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.24|14.27|1.002|12.60|12.55|0.996|
|2|18.13|18.12|0.999|15.87|15.79|0.995|
|3|21.76|21.68|0.996|18.44|18.33|0.994|
|4|23.79|23.94|1.006|19.71|19.77|1.003|
|5|28.12|28.14|1.001|22.94|22.83|0.995|
|6|31.10|31.09|1.000|24.77|24.72|0.998|
|7|36.01|35.98|0.999|27.97|27.78|0.993|
|8|39.65|39.62|0.999|30.67|30.70|1.001|
|9|42.69|42.61|0.998|33.23|33.14|0.997|
|10|44.89|44.95|1.001|35.21|35.28|1.002|
|11|48.00|48.04|1.001|37.66|37.56|0.997|
|12|51.36|51.32|0.999|40.07|40.00|0.998|
|13|54.84|54.84|1.000|42.71|42.79|1.002|
|14|57.94|57.97|1.001|45.20|45.20|1.000|
|15|61.08|61.04|0.999|47.77|47.79|1.000|
|16|64.70|64.71|1.000|51.14|51.08|0.999|
|17|66.84|66.74|0.999|53.01|53.03|1.000|
|18|69.42|69.47|1.001|55.41|55.46|1.001|
|19|71.46|71.49|1.000|57.13|57.01|0.998|
|20|70.65|70.77|1.002|56.46|56.43|0.999|
|21|70.72|70.69|1.000|56.57|56.52|0.999|
|22|70.68|70.64|0.999|56.59|56.51|0.999|
|23|70.69|70.80|1.002|56.60|56.54|0.999|
|24|70.61|70.66|1.001|56.49|56.53|1.001|
|25|70.81|70.80|1.000|56.69|56.77|1.001|
|26|70.84|70.66|0.997|56.79|56.65|0.998|
|27|70.80|70.80|1.000|56.71|56.81|1.002|
|28|70.41|70.83|1.006|56.73|56.77|1.001|
|29|70.92|70.87|0.999|56.79|56.81|1.000|
|30|70.85|70.86|1.000|56.89|56.81|0.999|
|31|70.80|70.85|1.001|56.79|56.79|1.000|
|32|72.21|72.29|1.001|57.93|57.93|1.000|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.75|16.86|1.007|15.68|15.75|1.004|
|**2**|22.70|21.75|0.958|21.16|19.80|0.936|
|3|25.97|25.95|0.999|23.88|23.90|1.001|
|4|31.89|31.76|0.996|28.73|28.76|1.001|
|5|36.08|35.98|0.997|32.70|32.71|1.000|
|6|41.09|41.06|0.999|37.21|37.23|1.001|
|7|45.69|45.76|1.002|41.37|41.55|1.004|
|8|50.01|50.09|1.002|45.32|45.47|1.003|
|9|55.25|55.45|1.004|49.70|50.16|1.009|
|10|59.46|59.64|1.003|53.60|53.83|1.004|
|11|64.66|64.56|0.998|58.45|58.39|0.999|
|12|68.60|68.51|0.999|62.02|62.09|1.001|
|13|73.54|73.58|1.001|66.74|66.87|1.002|
|14|78.02|77.90|0.998|70.70|70.58|0.998|
|15|82.71|82.62|0.999|74.99|74.69|0.996|
|16|86.88|87.02|1.002|78.57|78.79|1.003|
|17|91.71|91.51|0.998|83.28|82.92|0.996|
|18|96.00|96.11|1.001|87.03|87.25|1.003|
|19|100.53|100.50|1.000|91.44|91.33|0.999|
|20|105.12|105.28|1.002|95.53|95.52|1.000|
|21|110.10|110.24|1.001|99.87|100.18|1.003|
|22|114.51|114.35|0.999|104.08|103.98|0.999|
|23|118.75|118.80|1.000|107.96|107.88|0.999|
|24|123.13|123.26|1.001|111.82|112.33|1.005|
|25|128.18|128.29|1.001|116.89|116.64|0.998|
|26|132.80|132.80|1.000|120.83|120.86|1.000|
|27|137.01|137.23|1.002|124.71|124.80|1.001|
|28|141.38|141.51|1.001|128.71|128.81|1.001|
|29|145.75|145.99|1.002|132.79|133.01|1.002|
|30|150.15|150.17|1.000|136.80|137.03|1.002|
|31|154.65|154.57|0.999|141.28|141.12|0.999|
|32|158.95|158.76|0.999|145.22|144.89|0.998|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.43|14.37|0.996|13.64|13.61|0.998|
|2|16.60|16.67|1.004|15.44|15.54|1.006|
|3|19.62|19.61|0.999|18.14|18.16|1.001|
|4|22.75|22.77|1.001|20.89|21.00|1.005|
|5|25.22|25.13|0.996|23.22|23.25|1.001|
|6|27.27|27.26|1.000|25.20|25.17|0.999|
|7|30.09|30.08|1.000|27.55|27.55|1.000|
|8|32.90|32.92|1.001|30.22|30.27|1.002|
|9|35.45|35.43|0.999|32.51|32.53|1.001|
|10|37.85|37.92|1.002|34.72|34.78|1.002|
|11|40.32|40.31|1.000|37.09|37.12|1.001|
|12|42.80|42.86|1.001|39.55|39.67|1.003|
|13|45.44|45.47|1.001|41.98|42.15|1.004|
|14|47.82|47.92|1.002|44.22|44.27|1.001|
|15|50.45|50.43|1.000|46.63|46.57|0.999|
|16|52.56|52.54|1.000|48.67|48.75|1.002|
|17|55.21|55.11|0.998|51.27|51.15|0.998|
|18|57.70|57.79|1.002|53.63|53.59|0.999|
|19|60.38|60.43|1.001|56.10|56.22|1.002|
|20|62.65|62.58|0.999|58.32|58.22|0.998|
|21|65.21|65.30|1.001|60.69|60.69|1.000|
|22|67.81|68.01|1.003|63.10|63.29|1.003|
|23|70.44|70.30|0.998|65.63|65.49|0.998|
|24|72.85|72.82|1.000|67.87|67.72|0.998|
|25|75.03|75.40|1.005|69.98|70.20|1.003|
|26|77.82|77.77|0.999|72.70|72.59|0.998|
|27|80.42|80.32|0.999|75.02|74.89|0.998|
|28|82.95|82.66|0.997|77.34|77.20|0.998|
|29|85.28|85.06|0.997|79.61|79.47|0.998|
|30|87.72|87.73|1.000|81.95|81.95|1.000|
|31|90.41|90.18|0.997|84.69|84.38|0.996|
|32|92.81|92.43|0.996|86.81|86.53|0.997|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.28|16.23|0.997|14.74|14.72|0.999|
|2|21.76|21.69|0.997|19.66|19.62|0.998|
|3|25.11|25.08|0.999|22.49|22.49|1.000|
|4|28.80|28.81|1.000|25.89|25.82|0.997|
|5|34.01|34.05|1.001|30.25|30.15|0.997|
|6|37.89|37.81|0.998|33.68|33.64|0.999|
|7|42.02|42.02|1.000|37.44|37.42|0.999|
|8|46.17|46.21|1.001|41.08|41.09|1.000|
|9|50.55|50.48|0.999|45.10|45.05|0.999|
|10|54.61|54.60|1.000|48.68|48.68|1.000|
|11|58.48|58.52|1.001|52.26|52.27|1.000|
|12|62.35|62.34|1.000|55.72|55.68|0.999|
|13|66.50|66.57|1.001|59.44|59.54|1.002|
|14|70.49|70.44|0.999|63.05|63.05|1.000|
|15|74.58|74.59|1.000|67.03|67.01|1.000|
|16|74.50|74.50|1.000|66.81|66.76|0.999|
|17|74.68|74.60|0.999|67.03|66.99|0.999|
|18|74.60|74.64|1.001|66.85|67.06|1.003|
|19|74.72|74.64|0.999|67.10|66.92|0.997|
|20|74.63|74.62|1.000|66.85|66.96|1.002|
|21|74.71|74.85|1.002|67.04|67.14|1.001|
|22|74.69|74.68|1.000|66.97|67.11|1.002|
|23|74.66|74.60|0.999|67.05|66.86|0.997|
|24|74.59|74.67|1.001|66.90|67.00|1.001|
|25|74.76|74.75|1.000|67.11|67.27|1.002|
|26|74.86|74.79|0.999|67.20|67.22|1.000|
|27|74.87|74.77|0.999|67.20|67.16|0.999|
|28|74.81|74.67|0.998|67.11|67.06|0.999|
|29|74.91|74.85|0.999|67.23|67.35|1.002|
|30|74.83|74.79|0.999|67.17|67.19|1.000|
|31|74.89|74.94|1.001|67.23|67.31|1.001|
|32|74.83|74.87|1.001|67.14|67.15|1.000|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.02|14.00|0.999|13.14|13.15|1.001|
|2|16.61|16.60|0.999|15.22|15.26|1.003|
|3|19.05|19.04|0.999|17.35|17.35|1.000|
|4|21.35|21.24|0.995|19.36|19.40|1.002|
|5|23.60|23.57|0.999|21.50|21.57|1.003|
|6|25.96|25.88|0.997|23.36|23.28|0.997|
|7|28.60|28.67|1.002|25.70|25.86|1.006|
|8|29.89|29.94|1.002|27.07|27.13|1.002|
|9|32.71|32.75|1.001|29.42|29.49|1.002|
|10|34.51|34.49|0.999|31.21|31.14|0.998|
|11|36.55|36.60|1.001|32.99|33.06|1.002|
|12|38.44|38.41|0.999|34.82|34.80|0.999|
|13|40.53|40.53|1.000|36.79|36.79|1.000|
|14|42.62|42.54|0.998|38.70|38.66|0.999|
|15|44.53|44.49|0.999|40.55|40.55|1.000|
|16|44.46|44.42|0.999|40.47|40.42|0.999|
|17|44.64|44.62|1.000|40.62|40.62|1.000|
|18|44.61|44.70|1.002|40.60|40.63|1.001|
|19|44.68|44.68|1.000|40.66|40.64|1.000|
|20|44.66|44.63|0.999|40.66|40.60|0.999|
|21|44.65|44.64|1.000|40.63|40.65|1.000|
|22|44.74|44.74|1.000|40.72|40.71|1.000|
|23|44.74|44.74|1.000|40.70|40.76|1.001|
|24|44.63|44.67|1.001|40.77|40.74|0.999|
|25|44.93|44.83|0.998|40.85|40.87|1.000|
|26|44.89|44.87|1.000|40.88|40.96|1.002|
|27|44.90|44.91|1.000|40.89|40.90|1.000|
|28|44.92|44.88|0.999|40.88|40.91|1.001|
|29|44.91|44.89|1.000|40.86|40.96|1.002|
|30|45.01|44.96|0.999|40.97|40.94|0.999|
|31|45.00|44.97|0.999|40.99|40.97|1.000|
|32|44.99|44.90|0.998|40.97|40.87|0.998|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.77|13.72|0.996|12.27|12.37|1.008|
|2|17.19|17.15|0.998|14.88|14.91|1.002|
|3|20.06|20.05|1.000|17.12|17.09|0.998|
|4|23.22|23.45|1.010|19.00|19.25|1.013|
|5|25.20|25.30|1.004|20.53|20.49|0.998|
|6|28.80|28.87|1.002|23.07|23.16|1.004|
|7|32.64|32.72|1.002|25.75|25.80|1.002|
|8|35.44|35.60|1.005|27.93|28.17|1.009|
|9|38.45|38.45|1.000|30.06|30.04|0.999|
|10|41.00|41.05|1.001|32.54|32.55|1.000|
|11|43.98|44.05|1.002|34.59|34.58|1.000|
|12|46.53|46.49|0.999|36.81|36.93|1.003|
|13|49.45|49.56|1.002|39.07|39.09|1.001|
|14|52.11|52.18|1.001|41.29|41.34|1.001|
|15|55.02|55.12|1.002|43.71|43.77|1.001|
|16|57.58|57.47|0.998|45.99|45.92|0.998|
|17|60.08|60.15|1.001|48.04|48.12|1.002|
|18|62.78|62.82|1.001|50.40|50.48|1.002|
|19|65.25|65.19|0.999|52.44|52.71|1.005|
|20|67.64|67.71|1.001|54.92|54.94|1.000|
|21|69.96|69.97|1.000|57.15|57.17|1.000|
|22|72.21|72.26|1.001|59.44|59.36|0.999|
|23|74.61|74.61|1.000|61.68|61.49|0.997|
|24|77.01|77.04|1.000|63.65|63.75|1.002|
|25|79.48|79.57|1.001|66.11|66.33|1.003|
|26|81.91|81.98|1.001|68.33|68.32|1.000|
|27|84.90|84.85|0.999|71.03|71.08|1.001|
|28|87.40|87.31|0.999|73.28|73.25|1.000|
|29|89.99|89.94|0.999|75.53|75.41|0.998|
|30|93.59|93.61|1.000|78.59|78.57|1.000|
|31|95.83|96.02|1.002|80.59|80.76|1.002|
|32|97.36|97.53|1.002|82.24|82.37|1.002|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.92|13.68|0.983|12.28|12.17|0.991|
|2|16.99|16.94|0.997|15.11|15.10|0.999|
|3|20.54|20.49|0.998|17.78|17.62|0.991|
|4|23.22|23.35|1.006|19.74|19.87|1.007|
|5|26.84|26.75|0.997|21.76|21.88|1.006|
|6|28.85|28.88|1.001|23.02|23.06|1.002|
|7|31.72|31.75|1.001|24.90|24.92|1.001|
|8|34.40|34.38|0.999|27.34|27.41|1.003|
|9|36.80|36.79|1.000|28.65|28.66|1.000|
|10|39.46|39.47|1.000|30.80|30.86|1.002|
|11|41.57|41.52|0.999|32.22|32.23|1.000|
|12|42.23|42.21|1.000|33.26|33.30|1.001|
|13|43.94|43.95|1.000|34.58|34.56|0.999|
|14|45.29|45.22|0.998|35.62|35.48|0.996|
|15|47.66|47.60|0.999|37.51|37.45|0.998|
|16|48.96|49.02|1.001|38.40|38.15|0.993|
|17|51.57|51.62|1.001|40.37|40.37|1.000|
|18|53.54|53.37|0.997|41.98|41.93|0.999|
|19|55.18|55.28|1.002|43.29|43.41|1.003|
|20|56.81|56.79|1.000|44.76|44.77|1.000|
|21|58.39|58.49|1.002|46.15|46.20|1.001|
|22|60.29|60.31|1.000|47.58|47.58|1.000|
|23|61.91|61.86|0.999|48.97|49.03|1.001|
|24|63.50|63.45|0.999|50.45|50.47|1.000|
|25|65.53|65.53|1.000|51.99|52.05|1.001|
|26|67.25|67.29|1.001|53.57|53.52|0.999|
|27|67.23|67.23|1.000|53.53|53.54|1.000|
|28|67.32|67.29|1.000|53.51|53.52|1.000|
|29|67.23|67.22|1.000|53.66|53.53|0.998|
|30|67.32|67.26|0.999|53.59|53.57|1.000|
|31|67.24|67.28|1.001|53.62|53.51|0.998|
|32|66.74|66.66|0.999|53.00|52.99|1.000|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|19.47|19.60|1.007|17.13|17.35|1.013|
|2|25.33|25.40|1.003|20.58|20.42|0.992|
|3|30.73|30.82|1.003|24.65|24.77|1.005|
|4|38.11|38.42|1.008|29.81|29.92|1.004|
|5|42.77|42.50|0.994|33.15|33.03|0.996|
|6|47.61|47.59|1.000|37.12|37.16|1.001|
|7|54.21|54.37|1.003|42.17|42.16|1.000|
|8|59.03|59.10|1.001|46.12|45.88|0.995|
|9|63.55|63.60|1.001|49.63|49.58|0.999|
|10|68.59|68.67|1.001|54.96|54.81|0.997|
|11|72.84|72.85|1.000|58.60|58.57|0.999|
|12|77.29|77.31|1.000|62.72|62.56|0.997|
|13|82.04|82.06|1.000|67.49|67.80|1.005|
|14|86.60|86.58|1.000|71.70|72.11|1.006|
|15|90.95|91.00|1.001|75.74|75.86|1.002|
|16|95.52|95.65|1.001|80.65|80.48|0.998|
|17|99.80|99.86|1.001|84.83|84.86|1.000|
|18|104.13|104.19|1.001|88.81|89.12|1.003|
|19|109.01|109.10|1.001|93.37|93.41|1.000|
|20|113.03|113.07|1.000|97.73|97.87|1.001|
|21|117.70|117.33|0.997|102.16|101.90|0.997|
|22|122.07|121.98|0.999|106.40|106.21|0.998|
|23|126.80|126.77|1.000|110.86|110.73|0.999|
|24|130.86|130.78|0.999|114.90|114.78|0.999|
|25|135.42|135.58|1.001|119.26|119.34|1.001|
|26|139.96|140.28|1.002|123.67|123.75|1.001|
|27|144.47|144.32|0.999|127.91|127.61|0.998|
|28|148.77|148.90|1.001|132.20|132.22|1.000|
|29|153.15|153.36|1.001|136.49|136.75|1.002|
|30|157.39|157.58|1.001|140.56|140.75|1.001|
|31|161.77|161.86|1.001|144.85|144.96|1.001|
|32|166.05|166.26|1.001|149.23|149.52|1.002|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.06|12.00|0.995|10.97|10.91|0.995|
|2|14.27|14.14|0.991|12.69|12.61|0.994|
|3|16.47|16.40|0.996|14.58|14.59|1.001|
|4|18.84|18.95|1.006|16.69|16.88|1.011|
|5|20.63|20.66|1.001|17.72|17.75|1.002|
|6|22.73|22.56|0.993|19.00|18.86|0.993|
|7|25.05|25.14|1.004|21.09|21.04|0.998|
|8|27.07|27.00|0.997|22.12|21.98|0.994|
|9|28.51|28.49|0.999|23.06|22.96|0.996|
|10|31.11|30.77|0.989|25.47|25.38|0.996|
|11|32.51|32.30|0.994|26.31|26.15|0.994|
|12|34.07|33.90|0.995|27.30|27.10|0.993|
|13|35.78|35.70|0.998|28.85|28.84|1.000|
|14|37.50|37.56|1.002|30.06|30.11|1.002|
|15|39.08|39.08|1.000|31.00|30.89|0.996|
|16|40.82|40.74|0.998|32.37|32.22|0.995|
|17|42.41|42.46|1.001|33.81|33.88|1.002|
|18|44.06|43.97|0.998|34.80|34.90|1.003|
|19|45.84|45.96|1.003|36.09|36.13|1.001|
|20|47.49|47.42|0.999|37.51|37.47|0.999|
|21|49.16|49.06|0.998|38.82|38.86|1.001|
|22|51.12|51.05|0.999|40.29|40.20|0.998|
|23|52.71|52.68|0.999|41.64|41.80|1.004|
|24|54.52|54.47|0.999|42.86|42.78|0.998|
|25|56.18|56.09|0.998|44.34|44.51|1.004|
|26|57.96|57.79|0.997|45.77|45.81|1.001|
|27|59.75|59.56|0.997|47.11|47.14|1.001|
|28|61.19|61.13|0.999|48.48|48.48|1.000|
|29|62.81|62.82|1.000|50.04|49.93|0.998|
|30|64.17|64.21|1.001|51.14|51.07|0.999|
|31|65.78|65.79|1.000|52.58|52.59|1.000|
|32|67.27|67.28|1.000|54.01|54.00|1.000|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.75|24.65|0.996|20.49|20.44|0.998|
|2|38.47|38.32|0.996|30.10|29.97|0.996|
|3|52.88|52.83|0.999|41.39|41.38|1.000|
|4|63.64|63.56|0.999|50.27|50.24|0.999|
|5|75.27|75.18|0.999|60.82|60.84|1.000|
|6|86.26|86.36|1.001|71.07|71.02|0.999|
|7|96.65|96.62|1.000|81.55|81.55|1.000|
|8|107.28|107.54|1.002|91.46|91.54|1.001|
|**9**|118.37|117.85|0.996|102.09|101.80|0.997|
|10|127.88|127.91|1.000|111.54|111.58|1.000|
|11|138.05|137.91|0.999|121.41|121.32|0.999|
|12|147.37|147.33|1.000|130.54|130.52|1.000|
|13|157.12|157.12|1.000|140.16|140.22|1.000|
|14|167.07|167.00|1.000|150.11|149.98|0.999|
|15|176.79|176.83|1.000|159.84|159.86|1.000|
|16|186.59|186.55|1.000|169.67|169.55|0.999|
|17|194.04|194.24|1.001|176.91|177.08|1.001|
|18|201.04|200.90|0.999|183.92|183.84|1.000|
|19|207.81|208.04|1.001|190.87|190.96|1.000|
|20|208.09|208.02|1.000|190.99|190.91|1.000|
|21|208.11|208.06|1.000|191.10|191.06|1.000|
|22|208.19|208.15|1.000|191.22|191.13|1.000|
|23|208.09|208.25|1.001|191.16|191.22|1.000|
|24|208.21|208.21|1.000|191.37|191.23|0.999|
|25|208.87|208.88|1.000|192.16|192.08|1.000|
|26|208.77|208.88|1.001|192.08|192.16|1.000|
|27|208.85|208.93|1.000|192.22|192.23|1.000|
|28|209.13|208.85|0.999|192.26|192.24|1.000|
|29|208.89|209.12|1.001|192.28|192.44|1.001|
|30|209.12|209.12|1.000|192.50|192.40|0.999|
|31|209.22|209.31|1.000|192.46|192.39|1.000|
|32|209.20|209.22|1.000|192.43|192.51|1.000|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.96|12.96|1.000|11.60|11.61|1.001|
|2|15.44|15.42|0.999|13.86|13.84|0.999|
|3|18.29|18.29|1.000|15.98|15.94|0.997|
|4|19.55|19.48|0.996|16.52|16.58|1.004|
|5|23.56|23.50|0.997|19.55|19.52|0.998|
|6|25.03|24.98|0.998|20.48|20.38|0.995|
|7|27.65|27.78|1.005|21.97|22.14|1.008|
|8|29.58|29.56|0.999|23.30|23.27|0.999|
|9|32.55|32.56|1.000|25.41|25.40|1.000|
|10|34.64|34.74|1.003|27.24|27.43|1.007|
|11|36.98|37.02|1.001|28.83|28.82|1.000|
|12|39.09|39.08|1.000|30.80|30.72|0.997|
|13|41.27|41.32|1.001|32.33|32.32|1.000|
|14|43.28|43.30|1.000|34.06|34.02|0.999|
|15|45.43|45.55|1.003|35.89|35.90|1.000|
|16|46.59|46.69|1.002|36.70|36.70|1.000|
|17|46.71|46.71|1.000|36.64|36.76|1.003|
|18|46.71|46.75|1.001|36.69|36.77|1.002|
|19|46.82|46.85|1.001|36.77|36.81|1.001|
|20|46.70|46.71|1.000|36.73|36.71|0.999|
|21|46.91|46.84|0.999|36.72|36.77|1.001|
|22|46.90|46.92|1.000|36.88|36.92|1.001|
|23|47.09|46.88|0.996|36.92|36.76|0.996|
|24|46.88|46.84|0.999|36.80|36.69|0.997|
|25|46.91|46.93|1.000|36.95|36.87|0.998|
|26|46.90|46.99|1.002|36.90|36.94|1.001|
|27|46.91|47.01|1.002|36.98|36.94|0.999|
|28|46.93|46.88|0.999|36.92|36.86|0.998|
|29|47.01|47.00|1.000|36.94|37.08|1.004|
|30|46.96|46.99|1.001|36.90|36.97|1.002|
|31|46.94|47.03|1.002|36.97|36.93|0.999|
|32|46.95|47.01|1.001|36.92|37.12|1.005|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|23.73|23.65|0.997|20.40|20.14|0.987|
|2|34.33|34.30|0.999|27.39|27.34|0.998|
|3|44.93|44.93|1.000|35.48|35.30|0.995|
|4|55.74|55.68|0.999|43.49|43.65|1.004|
|5|65.73|65.69|0.999|52.29|52.31|1.000|
|6|75.53|75.62|1.001|60.93|60.96|1.000|
|7|84.73|84.86|1.002|69.69|69.72|1.000|
|8|95.62|95.60|1.000|80.03|79.96|0.999|
|9|104.73|104.78|1.000|88.66|88.69|1.000|
|10|113.62|113.63|1.000|97.13|97.11|1.000|
|11|122.11|122.18|1.001|105.40|105.52|1.001|
|12|130.64|130.71|1.001|113.81|113.82|1.000|
|13|139.00|139.00|1.000|122.29|122.31|1.000|
|14|147.69|147.53|0.999|130.71|130.55|0.999|
|15|156.19|156.14|1.000|139.15|139.08|0.999|
|16|164.52|164.47|1.000|147.37|147.47|1.001|
|17|173.22|173.46|1.001|156.07|156.19|1.001|
|18|181.63|181.58|1.000|164.44|164.42|1.000|
|19|189.93|190.10|1.001|172.76|172.96|1.001|
|20|198.32|198.41|1.000|181.04|181.21|1.001|
|21|206.93|206.87|1.000|189.67|189.57|0.999|
|22|215.16|215.30|1.001|197.97|198.07|1.001|
|23|223.49|223.46|1.000|206.17|206.22|1.000|
|24|232.07|231.88|0.999|214.82|214.56|0.999|
|25|240.65|240.67|1.000|223.41|223.44|1.000|
|26|249.67|249.42|0.999|232.30|232.11|0.999|
|27|257.76|258.05|1.001|240.30|240.63|1.001|
|28|266.44|266.28|0.999|249.02|248.88|0.999|
|29|274.45|274.73|1.001|257.29|257.34|1.000|
|30|282.94|282.68|0.999|265.46|265.50|1.000|
|31|291.30|291.13|0.999|274.02|273.86|0.999|
|32|299.14|299.19|1.000|281.82|282.04|1.001|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|21.78|21.72|0.997|18.48|18.37|0.994|
|2|32.69|32.90|1.006|26.01|26.05|1.002|
|3|42.69|42.59|0.998|33.62|33.53|0.997|
|4|52.08|52.21|1.002|40.94|40.82|0.997|
|5|61.79|61.80|1.000|48.28|48.29|1.000|
|6|69.98|69.94|0.999|56.09|56.13|1.001|
|7|78.12|78.13|1.000|63.71|63.61|0.998|
|8|86.28|86.23|0.999|71.34|71.18|0.998|
|9|93.92|94.07|1.002|78.85|78.79|0.999|
|10|101.77|101.62|0.999|86.33|86.26|0.999|
|11|109.69|109.71|1.000|93.85|93.84|1.000|
|12|117.36|117.31|1.000|101.39|101.33|0.999|
|13|125.23|125.28|1.000|108.91|108.86|1.000|
|14|132.75|132.73|1.000|116.25|116.24|1.000|
|15|140.32|140.19|0.999|123.79|123.72|0.999|
|16|140.65|140.55|0.999|123.73|123.62|0.999|
|17|141.07|141.09|1.000|124.05|124.06|1.000|
|18|141.04|141.04|1.000|123.98|124.01|1.000|
|19|141.18|141.22|1.000|124.16|124.16|1.000|
|20|141.14|141.19|1.000|124.13|124.20|1.001|
|21|141.25|141.25|1.000|124.27|124.26|1.000|
|22|141.23|141.28|1.000|124.21|124.22|1.000|
|23|141.32|141.25|1.000|124.38|124.28|0.999|
|24|141.24|141.15|0.999|124.37|124.32|1.000|
|25|141.60|141.64|1.000|125.00|124.94|1.000|
|26|141.66|141.72|1.000|125.03|125.00|1.000|
|27|141.23|141.13|0.999|124.39|124.40|1.000|
|28|141.21|141.17|1.000|124.51|124.46|1.000|
|29|141.99|141.85|0.999|125.26|125.20|1.000|
|30|141.26|141.20|1.000|124.56|124.55|1.000|
|31|141.80|141.89|1.001|125.03|125.23|1.002|
|32|141.30|141.32|1.000|124.67|124.71|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|35.58|35.65|1.002|28.19|28.27|1.003|
|2|51.55|51.69|1.003|39.68|39.69|1.000|
|3|67.25|67.40|1.002|52.55|52.68|1.002|
|4|80.82|80.83|1.000|65.75|65.68|0.999|
|5|93.72|93.67|0.999|77.62|77.54|0.999|
|6|107.15|107.03|0.999|90.75|90.42|0.996|
|7|120.08|120.14|1.000|103.14|103.51|1.004|
|8|132.94|132.90|1.000|115.96|116.00|1.000|
|9|146.21|146.01|0.999|128.42|128.44|1.000|
|10|159.37|159.42|1.000|141.48|141.45|1.000|
|11|171.69|171.73|1.000|154.10|154.16|1.000|
|12|184.55|184.49|1.000|166.89|166.79|0.999|
|13|196.56|196.77|1.001|178.80|178.85|1.000|
|14|209.02|209.15|1.001|191.44|191.45|1.000|
|15|221.60|221.72|1.001|203.88|203.84|1.000|
|16|234.40|234.28|0.999|216.22|216.27|1.000|
|17|248.56|248.61|1.000|230.99|231.00|1.000|
|18|261.25|261.08|0.999|243.36|243.60|1.001|
|19|273.41|273.38|1.000|255.98|255.93|1.000|
|20|281.61|281.47|1.000|264.29|264.26|1.000|
|21|290.00|289.84|0.999|272.60|272.62|1.000|
|22|298.26|298.20|1.000|281.14|281.10|1.000|
|23|306.57|306.49|1.000|289.45|289.47|1.000|
|24|315.14|314.98|0.999|297.98|297.80|0.999|
|25|323.72|323.76|1.000|306.49|306.56|1.000|
|26|332.30|332.09|0.999|314.99|315.16|1.001|
|27|340.62|340.48|1.000|323.27|323.36|1.000|
|28|348.80|348.73|1.000|331.70|331.73|1.000|
|29|357.11|357.08|1.000|339.95|340.17|1.001|
|30|365.60|365.35|0.999|348.48|348.38|1.000|
|31|373.96|374.02|1.000|356.74|356.94|1.001|
|32|382.25|382.07|1.000|365.17|365.09|1.000|

`e256_i2048_k6_clamp10`: hidden 4096, intermediate 2048, 256 experts,
top-6, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.37|24.43|1.002|20.01|19.86|0.993|
|2|37.91|37.88|0.999|29.46|29.41|0.998|
|3|50.02|50.00|1.000|38.48|38.49|1.000|
|4|61.45|61.45|1.000|48.12|48.16|1.001|
|5|72.40|72.33|0.999|58.13|58.18|1.001|
|6|82.58|82.56|1.000|67.36|67.45|1.001|
|7|92.85|92.89|1.000|77.47|77.56|1.001|
|8|104.75|104.82|1.001|89.24|89.38|1.002|
|9|114.55|114.50|1.000|98.34|98.23|0.999|
|10|124.18|124.01|0.999|107.50|107.57|1.001|
|11|133.89|133.98|1.001|117.09|117.02|0.999|
|12|143.06|143.09|1.000|126.24|126.23|1.000|
|13|152.96|152.90|1.000|135.94|135.96|1.000|
|14|162.09|162.06|1.000|144.63|144.70|1.000|
|15|171.57|171.59|1.000|154.17|154.24|1.000|
|16|171.61|171.69|1.000|154.34|154.39|1.000|
|17|172.31|172.27|1.000|155.07|154.92|0.999|
|18|172.38|172.35|1.000|155.12|155.12|1.000|
|19|172.46|172.39|1.000|155.24|155.24|1.000|
|20|172.26|172.39|1.001|155.17|155.26|1.001|
|21|172.64|172.49|0.999|155.35|155.22|0.999|
|22|172.56|172.56|1.000|155.28|155.27|1.000|
|23|172.67|172.71|1.000|155.65|155.74|1.001|
|24|172.44|172.47|1.000|155.29|155.27|1.000|
|25|173.56|173.69|1.001|156.19|156.18|1.000|
|26|173.72|173.57|0.999|156.34|156.15|0.999|
|27|173.70|173.73|1.000|156.31|156.43|1.001|
|28|173.73|173.80|1.000|156.35|156.55|1.001|
|29|173.72|173.84|1.001|156.45|156.40|1.000|
|30|174.11|173.91|0.999|156.88|156.75|0.999|
|31|173.89|173.90|1.000|156.81|156.90|1.001|
|32|173.94|173.97|1.000|156.95|157.07|1.001|

`e896_i3072_k16_situ`: hidden 3584, intermediate 3072, 896 experts,
top-16, situ

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|70.62|70.46|0.998|59.72|59.35|0.994|
|2|113.52|113.66|1.001|102.99|102.70|0.997|
|3|151.47|151.70|1.002|142.88|142.97|1.001|
|4|193.32|193.25|1.000|185.83|185.42|0.998|
|5|232.07|231.95|0.999|224.72|224.60|0.999|
|6|272.69|272.74|1.000|265.46|265.57|1.000|
|7|313.63|313.85|1.001|306.60|306.89|1.001|
|8|354.39|354.08|0.999|347.06|347.25|1.001|
|9|395.02|394.70|0.999|388.10|387.55|0.999|
|10|435.79|435.73|1.000|428.61|429.09|1.001|
|11|478.67|478.94|1.001|472.00|472.37|1.001|
|12|519.74|519.80|1.000|512.84|513.02|1.000|
|13|560.51|560.46|1.000|553.55|553.70|1.000|
|14|601.24|601.25|1.000|594.51|594.73|1.000|
|15|640.78|640.39|0.999|633.89|633.83|1.000|
|16|682.37|682.39|1.000|675.54|675.90|1.001|
|17|723.13|723.11|1.000|716.57|716.48|1.000|
|18|763.65|763.89|1.000|757.44|757.40|1.000|
|19|804.06|804.48|1.001|797.38|797.83|1.001|
|20|844.85|844.73|1.000|838.14|838.09|1.000|
|21|885.43|885.39|1.000|878.86|878.81|1.000|
|22|926.57|926.83|1.000|920.07|919.95|1.000|
|23|967.00|966.58|1.000|960.32|959.97|1.000|
|24|1008.00|1007.47|0.999|1001.05|1000.71|1.000|
|25|1048.06|1048.44|1.000|1041.31|1041.91|1.001|
|26|1088.91|1088.48|1.000|1082.15|1081.94|1.000|
|27|1129.43|1129.63|1.000|1122.78|1122.83|1.000|
|28|1169.83|1170.23|1.000|1163.29|1163.16|1.000|
|29|1209.82|1209.98|1.000|1203.19|1203.23|1.000|
|30|1251.17|1250.24|0.999|1244.29|1243.66|0.999|
|31|1291.45|1291.90|1.000|1285.00|1285.21|1.000|
|32|1331.60|1332.09|1.000|1324.94|1325.92|1.001|

**sm_103a** (NVIDIA GB300, CUDA 13.4). Latency in us of one routed-MoE
call (FC1, FC2, finalize), cold L2; previous = the current Cake version
(FlashInfer main), new = this PR; ratio = new / previous. **Bold**
num_tokens: this PR changes the row's launches. Plain: the row launches
the same kernels as the previous version.

`e128_i768_k8`: hidden 2048, intermediate 768, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.01|13.98|0.998|12.41|12.37|0.997|
|2|17.82|17.81|0.999|15.53|15.41|0.992|
|3|21.57|21.60|1.001|18.25|18.28|1.002|
|4|23.88|23.84|0.998|19.68|19.69|1.001|
|5|28.22|28.26|1.001|22.99|22.97|0.999|
|6|31.15|31.19|1.001|24.91|24.84|0.997|
|7|34.67|34.78|1.003|27.18|27.24|1.002|
|8|35.04|35.06|1.001|31.02|31.01|1.000|
|9|38.72|38.77|1.001|34.29|34.34|1.001|
|10|41.45|41.37|0.998|36.77|36.67|0.997|
|11|44.52|44.53|1.000|39.43|39.38|0.999|
|12|46.97|46.97|1.000|41.67|41.62|0.999|
|13|49.77|49.80|1.001|44.21|44.21|1.000|
|14|52.50|52.45|0.999|46.59|46.59|1.000|
|15|55.10|55.07|0.999|49.13|49.13|1.000|
|16|57.74|57.64|0.998|51.52|51.43|0.998|
|17|59.70|59.73|1.001|53.31|53.33|1.000|
|18|61.58|61.65|1.001|54.98|55.11|1.002|
|19|63.39|63.48|1.001|56.85|56.83|1.000|
|20|64.04|64.02|1.000|57.00|56.95|0.999|
|21|64.32|64.37|1.001|57.36|57.53|1.003|
|22|64.64|64.63|1.000|57.54|57.61|1.001|
|23|64.21|64.13|0.999|57.08|57.03|0.999|
|24|63.91|63.98|1.001|56.91|56.93|1.000|
|25|64.33|64.32|1.000|57.15|57.19|1.001|
|26|64.77|64.77|1.000|57.73|57.68|0.999|
|27|64.95|64.86|0.999|57.82|57.71|0.998|
|28|64.82|64.83|1.000|57.72|57.69|0.999|
|29|64.89|64.91|1.000|57.76|57.77|1.000|
|30|64.90|64.88|1.000|57.78|57.81|1.001|
|31|64.96|64.90|0.999|57.68|57.79|1.002|
|32|64.94|64.98|1.001|57.73|57.69|0.999|

`h4096_e512_i512_k10`: hidden 4096, intermediate 512, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|16.59|16.61|1.001|15.23|15.24|1.001|
|**2**|22.56|21.76|0.965|20.64|19.97|0.968|
|3|25.89|25.88|1.000|23.83|23.83|1.000|
|**4**|31.45|31.40|0.998|28.71|28.44|0.991|
|5|35.95|35.86|0.997|32.83|32.63|0.994|
|6|41.11|40.99|0.997|37.53|37.42|0.997|
|7|45.83|45.82|1.000|41.71|41.70|1.000|
|8|50.55|50.49|0.999|46.22|46.20|1.000|
|9|55.41|55.54|1.002|50.39|50.67|1.006|
|10|59.89|60.05|1.003|54.65|54.76|1.002|
|11|64.92|64.86|0.999|59.16|59.23|1.001|
|12|69.32|69.22|0.999|63.29|63.20|0.999|
|13|74.23|74.15|0.999|67.94|67.84|0.999|
|14|78.94|78.75|0.998|72.01|71.78|0.997|
|15|83.91|83.67|0.997|76.78|76.53|0.997|
|16|88.04|88.07|1.000|80.30|80.43|1.002|
|17|93.00|92.84|0.998|85.21|85.02|0.998|
|18|97.39|97.49|1.001|89.03|89.11|1.001|
|19|101.97|101.88|0.999|93.65|93.52|0.999|
|20|106.72|106.75|1.000|97.74|97.73|1.000|
|21|111.69|111.67|1.000|102.39|102.54|1.001|
|22|116.12|116.18|1.001|106.51|106.58|1.001|
|23|120.53|120.54|1.000|110.70|110.69|1.000|
|24|125.03|125.00|1.000|114.74|114.91|1.001|
|25|130.12|130.12|1.000|119.59|119.48|0.999|
|26|134.79|134.82|1.000|123.80|123.99|1.002|
|27|139.11|139.30|1.001|127.66|127.89|1.002|
|28|143.53|143.58|1.000|131.94|132.00|1.000|
|29|148.07|148.22|1.001|136.10|136.35|1.002|
|30|152.47|152.54|1.000|140.26|140.47|1.001|
|31|157.05|157.02|1.000|144.67|144.59|0.999|
|32|161.53|161.20|0.998|148.90|148.50|0.997|

`h4096_e512_i256_k10`: hidden 4096, intermediate 256, 512 experts,
top-10, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|14.10|14.02|0.994|13.26|13.11|0.989|
|2|16.18|16.26|1.005|14.94|15.01|1.005|
|3|19.37|19.36|0.999|17.87|17.83|0.998|
|**4**|22.21|21.75|0.979|20.48|19.73|0.963|
|5|24.64|24.74|1.004|22.75|22.71|0.998|
|6|26.90|26.87|0.999|24.77|24.77|1.000|
|7|29.71|29.69|0.999|27.34|27.33|1.000|
|8|32.57|32.74|1.005|29.95|30.14|1.006|
|9|35.04|35.00|0.999|32.25|32.30|1.002|
|10|37.44|37.50|1.002|34.46|34.57|1.003|
|11|39.94|39.93|1.000|36.92|36.93|1.000|
|12|42.44|42.48|1.001|39.51|39.60|1.002|
|13|45.23|45.32|1.002|42.05|42.10|1.001|
|14|47.56|47.61|1.001|44.17|44.27|1.002|
|15|50.26|50.22|0.999|46.64|46.55|0.998|
|16|52.27|52.29|1.000|48.69|48.81|1.002|
|17|55.14|55.00|0.997|51.45|51.29|0.997|
|18|57.55|57.69|1.002|53.68|53.71|1.001|
|19|60.29|60.39|1.002|56.22|56.36|1.002|
|20|62.61|62.54|0.999|58.49|58.47|1.000|
|21|65.18|65.25|1.001|60.95|60.97|1.000|
|22|67.87|67.93|1.001|63.51|63.51|1.000|
|23|70.41|70.24|0.998|65.79|65.61|0.997|
|24|72.92|72.70|0.997|68.20|67.90|0.996|
|25|75.08|75.53|1.006|70.40|70.80|1.006|
|26|78.07|77.94|0.998|73.26|73.15|0.998|
|27|80.44|80.45|1.000|75.43|75.34|0.999|
|28|83.10|82.74|0.996|77.82|77.66|0.998|
|29|85.41|85.24|0.998|80.09|79.95|0.998|
|30|87.71|87.71|1.000|82.45|82.69|1.003|
|31|90.47|90.15|0.996|85.12|84.85|0.997|
|32|92.77|92.43|0.996|87.41|86.97|0.995|

`h3072_e256_i768_k8`: hidden 3072, intermediate 768, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|15.95|15.98|1.002|14.41|14.46|1.003|
|**2**|21.72|20.66|0.951|19.70|18.34|0.931|
|3|24.93|24.97|1.002|22.45|22.53|1.004|
|4|28.84|28.88|1.001|26.18|26.16|0.999|
|5|33.89|33.85|0.999|30.46|30.39|0.998|
|6|37.57|37.54|0.999|33.61|33.57|0.999|
|7|42.22|42.20|1.000|37.87|37.97|1.003|
|8|46.16|46.16|1.000|41.48|41.58|1.002|
|9|50.82|50.65|0.997|45.88|45.80|0.998|
|10|54.82|54.95|1.002|49.47|49.49|1.000|
|11|59.06|59.14|1.001|53.41|53.56|1.003|
|12|62.86|62.88|1.000|56.75|56.71|0.999|
|13|67.11|67.25|1.002|60.70|60.83|1.002|
|14|71.32|71.26|0.999|64.49|64.51|1.000|
|15|75.51|75.56|1.001|68.50|68.47|1.000|
|16|75.26|75.19|0.999|68.15|68.12|1.000|
|17|75.57|75.49|0.999|68.52|68.35|0.998|
|18|75.42|75.55|1.002|68.28|68.39|1.002|
|19|75.53|75.39|0.998|68.42|68.22|0.997|
|20|75.53|75.44|0.999|68.32|68.27|0.999|
|21|75.56|75.69|1.002|68.39|68.51|1.002|
|22|75.62|75.60|1.000|68.39|68.49|1.001|
|23|75.55|75.41|0.998|68.44|68.18|0.996|
|24|75.45|75.54|1.001|68.19|68.27|1.001|
|25|75.77|75.70|0.999|68.54|68.60|1.001|
|26|75.88|75.74|0.998|68.67|68.61|0.999|
|27|75.80|75.70|0.999|68.52|68.54|1.000|
|28|75.57|75.59|1.000|68.41|68.45|1.001|
|29|75.75|75.79|1.001|68.58|68.60|1.000|
|30|75.72|75.72|1.000|68.52|68.59|1.001|
|31|75.84|75.82|1.000|68.53|68.69|1.002|
|32|75.81|75.84|1.000|68.51|68.44|0.999|

`h3072_e256_i384_k8`: hidden 3072, intermediate 384, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.88|13.74|0.990|12.95|12.86|0.993|
|2|16.45|16.46|1.001|15.01|15.00|0.999|
|**3**|18.79|18.11|0.964|16.96|16.60|0.979|
|**4**|21.11|20.62|0.977|19.10|18.64|0.976|
|5|23.22|23.22|1.000|21.10|21.17|1.003|
|6|25.53|25.44|0.996|23.12|23.02|0.996|
|**7**|28.24|27.92|0.989|25.29|25.36|1.003|
|8|29.41|29.44|1.001|26.80|26.80|1.000|
|9|32.30|32.43|1.004|29.27|29.36|1.003|
|10|34.27|34.19|0.998|31.05|31.02|0.999|
|11|36.17|36.35|1.005|32.85|32.94|1.003|
|12|38.15|38.12|0.999|34.67|34.64|0.999|
|13|40.27|40.22|0.999|36.73|36.69|0.999|
|14|42.38|42.27|0.997|38.76|38.68|0.998|
|15|44.37|44.28|0.998|40.60|40.53|0.998|
|16|44.19|44.31|1.003|40.46|40.49|1.001|
|17|44.50|44.44|0.999|40.70|40.68|1.000|
|18|44.39|44.45|1.001|40.57|40.69|1.003|
|19|44.41|44.42|1.000|40.66|40.64|1.000|
|20|44.39|44.36|0.999|40.60|40.65|1.001|
|21|44.50|44.47|0.999|40.71|40.67|0.999|
|22|44.47|44.37|0.998|40.62|40.60|1.000|
|23|44.46|44.44|1.000|40.65|40.70|1.001|
|24|44.35|44.44|1.002|40.68|40.70|1.000|
|25|44.76|44.74|1.000|40.84|40.85|1.000|
|26|44.70|44.79|1.002|40.84|40.99|1.004|
|27|44.69|44.72|1.001|40.82|40.89|1.002|
|28|44.66|44.72|1.001|40.87|40.84|0.999|
|29|44.74|44.77|1.001|40.91|40.93|1.000|
|30|44.87|44.76|0.998|40.98|40.96|1.000|
|31|44.76|44.74|1.000|40.87|40.84|0.999|
|32|44.79|44.90|1.002|40.90|40.84|0.999|

`e512_i512_k10`: hidden 2048, intermediate 512, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.56|13.49|0.995|12.01|12.10|1.007|
|2|17.01|16.91|0.994|14.67|14.71|1.003|
|3|19.78|19.74|0.998|17.08|17.02|0.996|
|4|24.05|24.10|1.002|19.98|20.06|1.004|
|5|25.12|25.06|0.998|20.46|20.44|0.999|
|6|28.70|28.73|1.001|23.04|23.24|1.009|
|7|32.44|32.50|1.002|25.84|25.92|1.003|
|8|35.58|35.67|1.003|28.14|28.38|1.009|
|9|38.49|38.49|1.000|30.24|30.25|1.000|
|10|41.11|41.09|1.000|32.76|32.75|1.000|
|11|44.07|44.12|1.001|35.00|34.92|0.998|
|12|46.72|46.67|0.999|37.35|37.52|1.005|
|13|49.56|49.57|1.000|39.48|39.40|0.998|
|14|52.18|52.18|1.000|41.72|41.75|1.001|
|15|55.16|55.18|1.000|44.35|44.39|1.001|
|16|57.94|57.77|0.997|46.65|46.62|0.999|
|17|60.23|60.28|1.001|48.89|48.89|1.000|
|18|63.02|62.98|0.999|51.16|51.15|1.000|
|19|65.57|65.57|1.000|53.34|53.50|1.003|
|20|68.13|68.15|1.000|55.89|55.91|1.000|
|21|70.52|70.56|1.001|58.12|58.09|0.999|
|22|72.88|72.95|1.001|60.43|60.41|1.000|
|23|75.47|75.34|0.998|62.83|62.57|0.996|
|24|77.91|78.01|1.001|64.98|64.93|0.999|
|25|80.36|80.40|1.000|67.38|67.52|1.002|
|26|82.69|82.58|0.999|69.66|69.59|0.999|
|27|85.64|85.59|0.999|72.47|72.41|0.999|
|28|89.16|89.12|1.000|75.30|75.36|1.001|
|29|90.67|90.72|1.001|76.90|76.95|1.001|
|30|94.39|94.39|1.000|80.12|80.02|0.999|
|31|96.85|97.01|1.002|82.34|82.36|1.000|
|32|98.22|98.32|1.001|83.73|83.91|1.002|

`e60_i1536_k4`: hidden 2048, intermediate 1536, 60 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|13.29|13.07|0.983|11.85|11.70|0.987|
|2|16.56|16.48|0.995|14.60|14.63|1.002|
|3|19.92|19.95|1.002|16.92|17.12|1.012|
|4|22.62|22.52|0.996|19.04|18.87|0.991|
|5|26.61|26.58|0.999|21.51|21.57|1.003|
|6|29.46|29.30|0.995|23.26|23.23|0.999|
|7|32.22|32.18|0.999|25.26|25.35|1.004|
|8|34.92|34.82|0.997|27.43|27.42|1.000|
|9|37.28|37.32|1.001|28.89|28.87|0.999|
|10|39.87|39.87|1.000|30.84|30.84|1.000|
|11|41.17|41.22|1.001|33.15|33.07|0.998|
|12|38.46|38.50|1.001|34.08|34.07|1.000|
|13|40.02|39.97|0.999|35.49|35.60|1.003|
|14|41.66|41.76|1.002|36.92|36.92|1.000|
|15|43.24|43.24|1.000|38.37|38.26|0.997|
|16|44.71|44.80|1.002|39.65|39.59|0.998|
|17|46.70|46.68|1.000|41.24|41.18|0.999|
|18|48.43|48.42|1.000|42.87|42.84|0.999|
|19|49.99|49.98|1.000|44.07|44.12|1.001|
|20|51.54|51.46|0.998|45.48|45.44|0.999|
|21|52.97|52.94|0.999|46.70|46.79|1.002|
|22|54.40|54.45|1.001|48.09|48.14|1.001|
|23|56.00|56.08|1.001|49.49|49.47|1.000|
|24|57.52|57.54|1.000|50.84|50.85|1.000|
|25|59.46|59.44|1.000|52.42|52.56|1.003|
|26|61.07|61.03|0.999|53.91|53.89|1.000|
|27|61.09|61.07|1.000|53.89|53.91|1.000|
|28|61.06|61.01|0.999|53.94|53.90|0.999|
|29|61.08|61.16|1.001|53.95|53.83|0.998|
|30|61.14|61.05|0.999|53.92|53.91|1.000|
|31|61.01|61.06|1.001|53.96|53.93|0.999|
|32|61.01|61.03|1.000|53.81|53.89|1.001|

`e192_i1536_k4_silu`: hidden 6144, intermediate 1536, 192 experts,
top-4, silu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|19.39|19.58|1.010|17.33|17.43|1.006|
|2|25.32|25.42|1.004|20.63|20.44|0.991|
|3|30.78|30.92|1.005|24.81|24.94|1.005|
|4|38.29|38.78|1.013|30.48|30.66|1.006|
|5|42.99|42.68|0.993|33.86|33.69|0.995|
|6|48.08|47.80|0.994|37.77|37.83|1.002|
|7|54.74|54.84|1.002|42.94|43.13|1.004|
|8|59.42|59.48|1.001|46.85|46.78|0.999|
|9|64.05|63.98|0.999|50.59|50.54|0.999|
|10|69.31|69.25|0.999|55.81|55.93|1.002|
|11|73.47|73.46|1.000|59.97|60.03|1.001|
|12|78.00|78.00|1.000|64.15|64.06|0.999|
|13|82.94|83.07|1.002|68.99|69.16|1.002|
|14|87.73|87.62|0.999|73.33|73.87|1.007|
|15|92.02|91.95|0.999|77.70|77.94|1.003|
|16|96.45|96.73|1.003|82.35|82.29|0.999|
|17|100.99|101.13|1.001|86.89|87.01|1.001|
|18|105.39|105.41|1.000|91.06|91.41|1.004|
|19|110.30|110.41|1.001|95.71|95.78|1.001|
|20|114.63|114.59|1.000|100.12|100.11|1.000|
|21|119.39|119.17|0.998|104.59|104.51|0.999|
|22|124.00|123.90|0.999|108.94|108.83|0.999|
|23|128.84|128.85|1.000|113.42|113.48|1.001|
|24|133.06|132.88|0.999|117.66|117.55|0.999|
|25|137.68|137.66|1.000|122.22|122.26|1.000|
|26|142.27|142.70|1.003|126.63|126.86|1.002|
|27|146.90|146.51|0.997|131.15|130.77|0.997|
|28|151.29|151.20|0.999|135.28|135.35|1.001|
|29|155.82|155.90|1.001|139.90|140.07|1.001|
|30|159.95|160.22|1.002|144.14|144.32|1.001|
|31|164.35|164.52|1.001|148.41|148.61|1.001|
|32|168.91|169.22|1.002|153.10|153.41|1.002|

`e384_i768_k4`: hidden 2560, intermediate 768, 384 experts, top-4,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|11.98|11.91|0.994|10.97|10.88|0.992|
|2|14.13|14.02|0.992|12.59|12.49|0.992|
|3|16.17|16.29|1.007|14.40|14.49|1.006|
|4|18.28|18.28|1.000|15.87|16.07|1.013|
|5|19.75|19.68|0.996|16.92|16.99|1.004|
|6|21.78|21.82|1.002|18.55|18.52|0.998|
|7|23.68|23.69|1.000|20.08|19.95|0.994|
|8|25.48|25.50|1.001|21.23|21.22|1.000|
|9|27.40|27.35|0.998|22.81|22.64|0.993|
|10|29.41|29.41|1.000|24.28|24.15|0.995|
|11|30.95|30.83|0.996|25.01|24.94|0.997|
|12|32.97|33.04|1.002|26.43|26.46|1.001|
|13|34.89|34.90|1.000|27.94|28.05|1.004|
|14|36.55|36.58|1.001|29.12|29.13|1.000|
|15|38.33|38.30|0.999|30.51|30.52|1.000|
|16|40.26|40.09|0.996|32.04|32.05|1.000|
|17|41.88|41.92|1.001|33.36|33.33|0.999|
|18|43.59|43.67|1.002|34.71|34.71|1.000|
|19|45.44|45.38|0.999|36.23|36.16|0.998|
|20|47.04|47.06|1.000|37.58|37.60|1.001|
|21|48.89|48.97|1.002|38.84|38.92|1.002|
|22|50.82|50.72|0.998|40.38|40.38|1.000|
|23|52.45|52.49|1.001|41.86|41.87|1.000|
|24|54.28|54.28|1.000|43.24|43.20|0.999|
|25|55.91|55.95|1.001|44.56|44.76|1.004|
|26|57.56|57.53|0.999|45.93|46.03|1.002|
|27|59.10|59.00|0.998|47.46|47.42|0.999|
|28|60.63|60.66|1.000|48.93|48.93|1.000|
|29|62.27|62.25|1.000|50.31|50.18|0.997|
|30|63.71|63.78|1.001|51.52|51.55|1.001|
|31|65.41|65.38|1.000|53.07|53.14|1.001|
|32|66.94|66.97|1.000|54.53|54.52|1.000|

`e128_i1536_k8`: hidden 4096, intermediate 1536, 128 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.57|24.59|1.001|20.43|20.41|0.999|
|2|39.23|39.13|0.997|30.95|30.84|0.996|
|3|53.11|53.12|1.000|41.90|41.82|0.998|
|4|64.82|64.65|0.997|51.95|51.97|1.000|
|5|76.38|76.19|0.998|62.02|62.15|1.002|
|6|79.77|79.71|0.999|72.44|72.38|0.999|
|7|90.38|90.30|0.999|82.27|82.17|0.999|
|8|100.97|101.06|1.001|92.26|92.37|1.001|
|9|112.36|112.30|0.999|103.10|103.16|1.001|
|10|123.03|123.00|1.000|113.02|112.99|1.000|
|11|133.49|133.47|1.000|122.77|122.80|1.000|
|12|144.05|144.04|1.000|132.69|132.60|0.999|
|13|154.65|154.62|1.000|142.62|142.65|1.000|
|14|165.23|165.20|1.000|152.39|152.43|1.000|
|15|175.73|175.59|0.999|162.43|162.43|1.000|
|16|186.03|186.08|1.000|172.33|172.39|1.000|
|17|194.26|194.10|0.999|179.97|179.83|0.999|
|18|201.72|201.68|1.000|186.98|186.99|1.000|
|19|209.03|209.06|1.000|193.96|194.03|1.000|
|20|208.99|208.99|1.000|193.77|193.95|1.001|
|21|209.12|209.05|1.000|193.98|194.00|1.000|
|22|209.04|209.10|1.000|193.93|194.01|1.000|
|23|209.10|209.11|1.000|193.94|193.95|1.000|
|24|209.30|209.27|1.000|193.93|194.05|1.001|
|25|209.98|209.95|1.000|194.90|194.79|0.999|
|26|209.92|209.84|1.000|194.83|194.60|0.999|
|27|210.00|209.92|1.000|194.87|194.77|0.999|
|28|209.92|209.89|1.000|194.79|194.73|1.000|
|29|210.01|209.94|1.000|194.79|194.78|1.000|
|30|209.97|209.97|1.000|194.90|194.80|0.999|
|31|210.02|209.95|1.000|194.74|194.74|1.000|
|32|209.98|209.92|1.000|194.87|194.79|1.000|

`e256_i512_k8`: hidden 2048, intermediate 512, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|12.66|12.72|1.005|11.44|11.48|1.003|
|2|15.35|15.35|1.000|13.61|13.61|1.000|
|3|18.08|18.05|0.998|15.74|15.64|0.994|
|4|19.29|19.41|1.006|16.31|16.35|1.002|
|5|23.41|23.48|1.003|19.43|19.40|0.998|
|6|24.78|24.73|0.998|20.30|20.26|0.998|
|7|27.56|27.68|1.004|22.10|22.16|1.003|
|8|29.66|29.60|0.998|23.29|23.34|1.002|
|9|32.47|32.35|0.996|25.40|25.50|1.004|
|10|34.71|34.88|1.005|27.57|27.60|1.001|
|11|37.13|37.06|0.998|29.19|29.16|0.999|
|12|39.06|39.12|1.002|31.01|31.01|1.000|
|13|41.32|41.31|1.000|32.51|32.49|0.999|
|14|43.39|43.41|1.000|34.32|34.26|0.998|
|15|45.64|45.69|1.001|35.98|36.11|1.004|
|16|42.07|42.13|1.001|37.06|37.09|1.001|
|17|42.89|42.81|0.998|37.71|37.73|1.001|
|18|47.30|47.19|0.998|37.32|37.27|0.999|
|19|42.91|42.82|0.998|37.68|37.83|1.004|
|20|42.91|42.82|0.998|37.84|37.80|0.999|
|21|42.87|42.79|0.998|37.79|37.67|0.997|
|22|42.92|42.89|0.999|37.83|37.83|1.000|
|23|42.90|42.80|0.998|37.73|37.69|0.999|
|24|42.93|42.90|0.999|37.86|37.87|1.000|
|25|43.04|43.00|0.999|37.88|37.87|1.000|
|26|43.02|43.02|1.000|37.83|37.93|1.003|
|27|43.11|43.07|0.999|37.98|37.91|0.998|
|28|43.05|42.97|0.998|37.85|37.75|0.997|
|29|43.15|42.96|0.996|37.89|37.99|1.003|
|30|47.41|47.46|1.001|37.62|37.69|1.002|
|31|47.36|47.45|1.002|37.60|37.73|1.003|
|32|43.04|43.02|1.000|37.94|38.00|1.002|

`e512_i1024_k10`: hidden 4096, intermediate 1024, 512 experts, top-10,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|24.46|24.35|0.996|20.94|20.84|0.995|
|2|35.52|35.52|1.000|28.55|28.54|1.000|
|3|45.89|45.89|1.000|36.40|36.30|0.997|
|4|56.62|56.73|1.002|45.39|45.46|1.002|
|5|60.91|60.89|1.000|55.07|55.09|1.000|
|6|70.21|70.23|1.000|63.43|63.57|1.002|
|7|79.65|79.67|1.000|72.21|72.17|0.999|
|8|88.91|88.78|0.999|81.03|80.96|0.999|
|9|98.58|98.50|0.999|89.78|89.73|0.999|
|10|107.82|107.90|1.001|98.35|98.23|0.999|
|11|117.02|117.08|1.001|106.58|106.76|1.002|
|12|126.16|126.29|1.001|115.34|115.36|1.000|
|13|135.44|135.54|1.001|123.95|124.13|1.001|
|14|144.54|144.52|1.000|132.36|132.25|0.999|
|15|153.69|153.63|1.000|140.86|140.90|1.000|
|16|162.59|162.61|1.000|149.08|149.17|1.001|
|17|172.27|172.28|1.000|158.09|158.07|1.000|
|18|181.31|181.27|1.000|166.71|166.63|1.000|
|19|190.23|190.27|1.000|175.05|175.04|1.000|
|20|199.25|199.22|1.000|183.41|183.51|1.001|
|21|208.31|208.24|1.000|192.13|192.07|1.000|
|22|217.24|217.35|1.001|200.69|200.81|1.001|
|23|226.38|226.32|1.000|209.19|209.05|0.999|
|24|235.51|235.34|0.999|217.93|217.76|0.999|
|25|244.72|244.79|1.000|226.55|226.55|1.000|
|26|254.49|254.35|0.999|238.51|238.37|0.999|
|27|262.99|263.45|1.002|246.90|247.12|1.001|
|28|271.96|271.70|0.999|255.67|255.49|0.999|
|29|280.50|280.56|1.000|264.31|264.34|1.000|
|30|288.99|288.94|1.000|272.70|272.66|1.000|
|31|297.64|297.45|0.999|281.34|281.17|0.999|
|32|305.69|305.79|1.000|289.45|289.61|1.001|

`e256_i1536_k8`: hidden 3072, intermediate 1536, 256 experts, top-8,
swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|21.27|21.14|0.994|18.14|18.07|0.996|
|2|32.35|32.40|1.002|25.07|25.02|0.998|
|3|42.80|42.71|0.998|33.99|33.92|0.998|
|4|52.47|52.63|1.003|41.55|41.52|0.999|
|5|62.18|62.18|1.000|49.35|49.36|1.000|
|6|70.69|70.68|1.000|57.25|57.29|1.001|
|7|79.09|79.10|1.000|65.31|65.15|0.998|
|8|87.41|87.30|0.999|73.19|73.03|0.998|
|9|95.31|95.35|1.000|80.83|80.94|1.001|
|10|103.25|103.21|1.000|88.58|88.53|0.999|
|11|111.41|111.31|0.999|96.34|96.35|1.000|
|12|119.26|119.19|0.999|104.08|104.08|1.000|
|13|127.13|127.18|1.000|111.85|111.77|0.999|
|14|134.90|134.87|1.000|119.58|119.49|0.999|
|15|138.30|138.27|1.000|125.27|125.24|1.000|
|16|138.20|138.25|1.000|125.25|125.28|1.000|
|17|138.67|138.66|1.000|125.50|125.50|1.000|
|18|138.68|138.63|1.000|125.53|125.51|1.000|
|19|138.68|138.69|1.000|125.51|125.54|1.000|
|20|138.64|138.69|1.000|125.49|125.59|1.001|
|21|138.73|138.77|1.000|125.58|125.58|1.000|
|22|138.69|138.70|1.000|125.57|125.51|1.000|
|23|138.72|138.76|1.000|125.57|125.57|1.000|
|24|138.81|138.76|1.000|125.45|125.41|1.000|
|25|139.22|139.15|0.999|126.01|125.98|1.000|
|26|139.30|139.30|1.000|126.03|126.06|1.000|
|27|139.29|139.30|1.000|126.06|126.04|1.000|
|28|139.21|139.28|1.001|125.98|126.08|1.001|
|29|139.32|139.31|1.000|126.22|126.17|1.000|
|30|139.30|139.36|1.000|126.09|126.11|1.000|
|31|139.28|139.32|1.000|126.04|126.09|1.000|
|32|139.29|139.30|1.000|126.05|125.99|1.000|

`e128_i3072_k4_swiglu_oa`: hidden 6144, intermediate 3072, 128 experts,
top-4, swiglu

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|31.64|31.72|1.003|28.57|28.51|0.998|
|2|46.28|46.14|0.997|41.40|41.31|0.998|
|3|60.15|60.16|1.000|53.92|53.96|1.001|
|4|74.07|74.03|0.999|66.80|66.72|0.999|
|5|88.05|88.07|1.000|79.38|79.34|0.999|
|6|102.09|102.13|1.000|92.10|92.18|1.001|
|7|115.94|115.94|1.000|104.68|104.68|1.000|
|8|129.88|129.96|1.001|117.29|117.34|1.000|
|9|145.43|145.47|1.000|131.79|131.84|1.000|
|10|159.45|159.36|0.999|144.63|144.59|1.000|
|11|172.97|172.96|1.000|157.22|157.18|1.000|
|12|186.74|186.90|1.001|170.07|170.24|1.001|
|13|200.44|200.41|1.000|182.93|182.91|1.000|
|14|213.96|213.96|1.000|195.71|195.61|0.999|
|15|227.47|227.40|1.000|208.44|208.47|1.000|
|16|238.69|238.70|1.000|222.00|221.94|1.000|
|17|253.11|253.08|1.000|236.62|236.56|1.000|
|18|266.03|265.94|1.000|249.49|249.45|1.000|
|19|278.84|278.62|0.999|262.31|262.23|1.000|
|20|287.17|287.28|1.000|270.88|270.94|1.000|
|21|295.80|295.87|1.000|279.43|279.49|1.000|
|22|304.13|304.12|1.000|288.08|288.10|1.000|
|23|312.87|312.66|0.999|296.68|296.54|1.000|
|24|321.48|321.43|1.000|305.37|305.24|1.000|
|25|331.60|331.65|1.000|315.32|315.48|1.001|
|26|340.17|340.06|1.000|324.01|323.99|1.000|
|27|348.56|348.76|1.001|332.61|332.50|1.000|
|28|357.22|357.26|1.000|340.98|340.97|1.000|
|29|365.70|365.58|1.000|349.61|349.71|1.000|
|30|374.26|374.38|1.000|358.41|358.45|1.000|
|31|382.88|382.81|1.000|366.86|366.89|1.000|
|32|391.54|391.67|1.000|375.60|375.59|1.000|

`e896_i3072_k16_situ`: hidden 3584, intermediate 3072, 896 experts,
top-16, situ

|num_tokens|memset prev|memset new|ratio|read prev|read new|ratio|
|--:|--:|--:|--:|--:|--:|--:|
|1|70.35|70.39|1.001|59.83|59.50|0.994|
|2|114.64|114.60|1.000|104.93|104.79|0.999|
|3|155.26|155.51|1.002|148.68|148.52|0.999|
|4|198.22|198.05|0.999|193.66|193.41|0.999|
|5|242.35|242.25|1.000|237.93|237.70|0.999|
|6|286.83|286.60|0.999|283.40|283.37|1.000|
|7|331.39|331.33|1.000|327.88|327.95|1.000|
|8|376.02|375.55|0.999|372.99|373.04|1.000|
|9|419.86|420.03|1.000|416.87|417.01|1.000|
|10|465.42|465.10|0.999|461.61|461.52|1.000|
|11|509.11|509.42|1.001|506.09|506.21|1.000|
|12|554.58|554.21|0.999|551.34|551.29|1.000|
|13|598.58|598.60|1.000|595.54|595.64|1.000|
|14|643.66|643.65|1.000|640.73|640.42|1.000|
|15|688.22|687.32|0.999|685.17|685.27|1.000|
|16|732.07|732.48|1.001|728.86|729.04|1.000|
|17|776.92|776.75|1.000|773.97|773.75|1.000|
|18|821.43|821.49|1.000|818.04|818.18|1.000|
|19|865.54|865.80|1.000|861.67|862.58|1.001|
|20|910.21|909.96|1.000|906.98|906.80|1.000|
|21|954.20|954.46|1.000|950.79|950.65|1.000|
|22|1000.46|1000.22|1.000|996.77|996.50|1.000|
|23|1043.81|1043.49|1.000|1040.59|1040.53|1.000|
|24|1089.14|1089.05|1.000|1085.35|1085.56|1.000|
|25|1132.17|1132.94|1.001|1128.81|1129.14|1.000|
|26|1178.27|1177.96|1.000|1174.06|1174.21|1.000|
|27|1222.37|1222.08|1.000|1217.80|1217.68|1.000|
|28|1265.78|1266.12|1.000|1261.88|1262.23|1.000|
|29|1309.59|1309.36|1.000|1305.69|1305.90|1.000|
|30|1354.95|1354.04|0.999|1351.06|1351.11|1.000|
|31|1398.62|1398.80|1.000|1394.67|1394.76|1.000|
|32|1442.40|1443.23|1.001|1439.18|1439.33|1.000|

Cake ships no other data types, layouts or fused forms for
`cake_warp_decode`, and this family ships on sm_100a and sm_103a.

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [9323e48](https://github.com/flashinfer-ai/flashinfer/commit/9323e48094d2cc8a4c2b8d91d80e20c2681af1b1)

- **作者**: eigen
- **时间**: 2026-10-29T18:07:05Z
- **提交信息**: fix(cake_softmax): keep whole tiles for 6-tile high-cut 8-CTA launches on B200 (#7867)

`flashinfer.sampling.softmax` on Blackwell has one data type (FP32) and
one layout (row-major `[rows, vocab]`). It can fuse a scalar or per-row
temperature and can use PDL launches. This PR builds on the previous
Cake version (#7822), which is the current main. It adds no program and
changes no kernel code. It changes one dispatcher rule, on B200
(sm_100a) only. A tile is 2048 elements. The balanced per-CTA chunk is
ceil(vocab / CTAs) rounded up to 32 elements. The cut is the whole-tile
chunk minus the balanced chunk, as a fraction of the whole-tile chunk.

On B200, the 8-CTA shared-tile and persistent programs now keep whole
tiles at every row count when the whole-tile chunk is 6 tiles and the
cut is at least 1/10. Before this PR, they took the balanced chunk.
Since #7822, GB300 (sm_103a) has limited these programs to 79 rows
(shared-tile) and 92 rows (persistent). This PR does not change GB300.
With the balanced chunk, some rows of these B200 launches had a maximum
relative error above 1e-6 against a float64 reference; on the 122 B200
shapes in the tables below, the maximum relative error is 9.659e-7 with
this PR, versus 1.020e-6 with #7822. These shapes are slower than with
#7822. This is a cost, not a speedup.

On B200, the 41 listed shapes keep their launch: 1.000×–1.003×,
geometric mean 1.000× (Table A). On B200, 81 measured shapes change
their per-CTA chunk (rows 45–497 × vocab 81928–88320), and all are
slower: 0.933×–0.997×, geometric mean 0.959× (Table B). The changed
programs are the 8-CTA shared-tile and 8-CTA persistent programs, for
example 10272 → 12288 elements per CTA. On GB300 (sm_103a), no launch
changes: 765 checked shapes, including the 41 listed shapes, keep their
launch and give bitwise-identical output, so there is no GB300 table.

**Table A.** The 41 listed shapes: latency in µs (median, cold L2) for
the previous Cake version (#7822) and this PR on B200 (sm_100a), CUDA
13.4 (nvcc 13.4.2), PyTorch 2.14.1+cu130; speedup is the median of
paired ratios, so it can differ slightly from the ratio of the medians
shown.

| rows × vocab | previous (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|
| 1 × 32000 | 2.40 | 2.40 | 1.000× |
| 1 × 64000 | 2.78 | 2.78 | 1.000× |
| 1 × 128000 | 3.30 | 3.30 | 1.000× |
| 1 × 256000 | 4.45 | 4.45 | 1.000× |
| 4 × 32000 | 2.64 | 2.64 | 1.000× |
| 4 × 64000 | 2.91 | 2.91 | 1.000× |
| 4 × 128000 | 3.49 | 3.49 | 1.000× |
| 4 × 256000 | 4.85 | 4.85 | 1.000× |
| 8 × 32000 | 2.72 | 2.72 | 1.000× |
| 8 × 64000 | 3.26 | 3.26 | 1.000× |
| 8 × 128000 | 4.32 | 4.32 | 1.000× |
| 8 × 256000 | 6.69 | 6.69 | 1.000× |
| 16 × 32000 | 3.01 | 3.01 | 1.000× |
| 16 × 64000 | 3.81 | 3.81 | 1.000× |
| 16 × 128000 | 5.71 | 5.71 | 1.000× |
| 16 × 256000 | 9.66 | 9.66 | 1.000× |
| 32 × 32000 | 3.55 | 3.55 | 1.000× |
| 32 × 64000 | 5.15 | 5.15 | 1.000× |
| 32 × 128000 | 7.92 | 7.92 | 1.000× |
| 32 × 256000 | 13.46 | 13.46 | 1.000× |
| 64 × 32000 | 4.74 | 4.72 | 1.000× |
| 64 × 64000 | 7.20 | 7.20 | 1.000× |
| 64 × 128000 | 12.02 | 12.00 | 1.003× |
| 64 × 256000 | 20.92 | 20.93 | 1.000× |
| 128 × 32000 | 7.10 | 7.10 | 1.000× |
| 128 × 64000 | 11.39 | 11.39 | 1.000× |
| 128 × 128000 | 18.67 | 18.70 | 1.000× |
| 128 × 256000 | 36.64 | 36.64 | 1.000× |
| 256 × 32000 | 10.91 | 10.91 | 1.000× |
| 256 × 64000 | 19.02 | 19.04 | 1.000× |
| 256 × 128000 | 35.90 | 35.95 | 1.001× |
| 256 × 256000 | 76.58 | 76.59 | 1.000× |
| 512 × 32000 | 18.29 | 18.29 | 1.000× |
| 512 × 64000 | 36.26 | 36.26 | 1.000× |
| 512 × 128000 | 77.04 | 77.05 | 1.000× |
| 512 × 256000 | 152.76 | 152.75 | 1.000× |
| 1024 × 32000 | 35.20 | 35.20 | 1.000× |
| 1024 × 64000 | 73.09 | 73.09 | 1.000× |
| 1024 × 128000 | 151.90 | 151.86 | 1.000× |
| 1024 × 256000 | 302.30 | 302.17 | 1.000× |
| 64 × 32000 (scalar temperature, PDL) | 4.70 | 4.70 | 1.000× |
| geometric mean | | | 1.000× |

**Table B.** The 81 measured B200 (sm_100a) shapes that change their
per-CTA chunk: rows × vocab, program, elements per CTA before → after,
and latency in µs (median, cold L2) for the previous Cake version
(#7822) and this PR, CUDA 13.4 (nvcc 13.4.2), PyTorch 2.14.1+cu130;
speedup is the median of paired ratios, so it can differ slightly from
the ratio of the medians shown.

| rows × vocab | program | elements per CTA before → after | previous
(µs) | this PR (µs) | speedup |
|---|---|---|---:|---:|---:|
| 45 × 81928 | 8-CTA shared-tile | 10272 → 12288 | 7.70 | 8.22 | 0.938×
|
| 45 × 81928 (scalar temperature) | 8-CTA shared-tile | 10272 → 12288 |
7.73 | 8.22 | 0.938× |
| 45 × 81928 (scalar temperature, PDL) | 8-CTA shared-tile | 10272 →
12288 | 7.74 | 8.21 | 0.942× |
| 79 × 81928 | 8-CTA persistent | 10272 → 12288 | 10.85 | 11.30 | 0.960×
|
| 79 × 81928 (scalar temperature) | 8-CTA persistent | 10272 → 12288 |
10.86 | 11.34 | 0.958× |
| 79 × 81928 (scalar temperature, PDL) | 8-CTA persistent | 10272 →
12288 | 10.90 | 11.33 | 0.961× |
| 93 × 81928 | 8-CTA persistent | 10272 → 12288 | 11.66 | 12.22 | 0.953×
|
| 93 × 81928 (scalar temperature) | 8-CTA persistent | 10272 → 12288 |
11.66 | 12.22 | 0.955× |
| 93 × 81928 (scalar temperature, PDL) | 8-CTA persistent | 10272 →
12288 | 11.74 | 12.26 | 0.956× |
| 128 × 81928 | 8-CTA persistent | 10272 → 12288 | 14.27 | 15.04 |
0.949× |
| 128 × 81928 (scalar temperature) | 8-CTA persistent | 10272 → 12288 |
14.24 | 15.04 | 0.947× |
| 128 × 81928 (scalar temperature, PDL) | 8-CTA persistent | 10272 →
12288 | 14.24 | 15.01 | 0.947× |
| 180 × 81928 | 8-CTA persistent | 10272 → 12288 | 18.46 | 19.33 |
0.955× |
| 180 × 81928 (scalar temperature) | 8-CTA persistent | 10272 → 12288 |
18.37 | 19.33 | 0.954× |
| 180 × 81928 (scalar temperature, PDL) | 8-CTA persistent | 10272 →
12288 | 18.40 | 19.30 | 0.952× |
| 231 × 81928 | 8-CTA persistent | 10272 → 12288 | 22.34 | 23.90 |
0.933× |
| 231 × 81928 (scalar temperature) | 8-CTA persistent | 10272 → 12288 |
22.37 | 23.97 | 0.933× |
| 231 × 81928 (scalar temperature, PDL) | 8-CTA persistent | 10272 →
12288 | 22.34 | 23.90 | 0.933× |
| 296 × 81928 | 8-CTA shared-tile | 10272 → 12288 | 29.70 | 30.98 |
0.959× |
| 296 × 81928 (scalar temperature) | 8-CTA shared-tile | 10272 → 12288 |
29.84 | 31.04 | 0.963× |
| 296 × 81928 (scalar temperature, PDL) | 8-CTA shared-tile | 10272 →
12288 | 29.73 | 30.98 | 0.959× |
| 370 × 81928 | 8-CTA shared-tile | 10272 → 12288 | 36.13 | 37.66 |
0.960× |
| 370 × 81928 (scalar temperature) | 8-CTA shared-tile | 10272 → 12288 |
36.10 | 37.70 | 0.958× |
| 370 × 81928 (scalar temperature, PDL) | 8-CTA shared-tile | 10272 →
12288 | 36.03 | 37.66 | 0.957× |
| 497 × 81928 | 8-CTA shared-tile | 10272 → 12288 | 47.47 | 49.15 |
0.967× |
| 497 × 81928 (scalar temperature) | 8-CTA shared-tile | 10272 → 12288 |
47.43 | 49.09 | 0.967× |
| 497 × 81928 (scalar temperature, PDL) | 8-CTA shared-tile | 10272 →
12288 | 47.50 | 49.15 | 0.966× |
| 45 × 82944 | 8-CTA shared-tile | 10368 → 12288 | 7.74 | 8.24 | 0.938×
|
| 79 × 82944 | 8-CTA persistent | 10368 → 12288 | 10.88 | 11.33 | 0.960×
|
| 93 × 82944 | 8-CTA persistent | 10368 → 12288 | 11.65 | 12.19 | 0.955×
|
| 128 × 82944 | 8-CTA persistent | 10368 → 12288 | 14.19 | 14.98 |
0.947× |
| 180 × 82944 | 8-CTA persistent | 10368 → 12288 | 18.26 | 19.23 |
0.953× |
| 231 × 82944 | 8-CTA persistent | 10368 → 12288 | 22.34 | 23.87 |
0.937× |
| 296 × 82944 | 8-CTA shared-tile | 10368 → 12288 | 29.81 | 30.59 |
0.976× |
| 370 × 82944 | 8-CTA shared-tile | 10368 → 12288 | 36.51 | 37.12 |
0.984× |
| 497 × 82944 | 8-CTA shared-tile | 10368 → 12288 | 48.05 | 48.38 |
0.994× |
| 45 × 84000 | 8-CTA shared-tile | 10528 → 12288 | 7.81 | 8.26 | 0.942×
|
| 79 × 84000 | 8-CTA persistent | 10528 → 12288 | 10.94 | 11.33 | 0.963×
|
| 93 × 84000 | 8-CTA persistent | 10528 → 12288 | 11.74 | 12.19 | 0.961×
|
| 128 × 84000 | 8-CTA persistent | 10528 → 12288 | 14.27 | 14.95 |
0.954× |
| 180 × 84000 | 8-CTA persistent | 10528 → 12288 | 18.37 | 19.17 |
0.957× |
| 231 × 84000 | 8-CTA persistent | 10528 → 12288 | 22.46 | 23.81 |
0.943× |
| 296 × 84000 | 8-CTA shared-tile | 10528 → 12288 | 29.99 | 31.17 |
0.963× |
| 370 × 84000 | 8-CTA shared-tile | 10528 → 12288 | 36.50 | 37.76 |
0.967× |
| 497 × 84000 | 8-CTA shared-tile | 10528 → 12288 | 48.45 | 49.28 |
0.983× |
| 45 × 84840 | 8-CTA shared-tile | 10624 → 12288 | 7.84 | 8.26 | 0.950×
|
| 79 × 84840 | 8-CTA persistent | 10624 → 12288 | 11.01 | 11.42 | 0.964×
|
| 93 × 84840 | 8-CTA persistent | 10624 → 12288 | 11.84 | 12.32 | 0.961×
|
| 128 × 84840 | 8-CTA persistent | 10624 → 12288 | 14.43 | 15.10 |
0.955× |
| 180 × 84840 | 8-CTA persistent | 10624 → 12288 | 18.56 | 19.33 |
0.962× |
| 231 × 84840 | 8-CTA persistent | 10624 → 12288 | 22.72 | 24.03 |
0.945× |
| 296 × 84840 | 8-CTA shared-tile | 10624 → 12288 | 30.50 | 31.97 |
0.955× |
| 370 × 84840 | 8-CTA shared-tile | 10624 → 12288 | 37.06 | 38.82 |
0.955× |
| 497 × 84840 | 8-CTA shared-tile | 10624 → 12288 | 48.86 | 50.56 |
0.967× |
| 45 × 86016 | 8-CTA shared-tile | 10752 → 12288 | 7.97 | 8.34 | 0.954×
|
| 79 × 86016 | 8-CTA persistent | 10752 → 12288 | 11.01 | 11.36 | 0.969×
|
| 93 × 86016 | 8-CTA persistent | 10752 → 12288 | 11.76 | 12.26 | 0.961×
|
| 128 × 86016 | 8-CTA persistent | 10752 → 12288 | 14.34 | 14.99 |
0.955× |
| 180 × 86016 | 8-CTA persistent | 10752 → 12288 | 18.53 | 19.41 |
0.953× |
| 231 × 86016 | 8-CTA persistent | 10752 → 12288 | 22.59 | 23.90 |
0.946× |
| 296 × 86016 | 8-CTA shared-tile | 10752 → 12288 | 30.30 | 31.62 |
0.959× |
| 370 × 86016 | 8-CTA shared-tile | 10752 → 12288 | 36.66 | 38.34 |
0.958× |
| 497 × 86016 | 8-CTA shared-tile | 10752 → 12288 | 49.02 | 49.89 |
0.982× |
| 45 × 87040 | 8-CTA shared-tile | 10880 → 12288 | 7.98 | 8.30 | 0.960×
|
| 79 × 87040 | 8-CTA persistent | 10880 → 12288 | 11.01 | 11.39 | 0.963×
|
| 93 × 87040 | 8-CTA persistent | 10880 → 12288 | 11.76 | 12.21 | 0.961×
|
| 128 × 87040 | 8-CTA persistent | 10880 → 12288 | 14.40 | 15.04 |
0.956× |
| 180 × 87040 | 8-CTA persistent | 10880 → 12288 | 18.40 | 19.40 |
0.951× |
| 231 × 87040 | 8-CTA persistent | 10880 → 12288 | 22.66 | 23.90 |
0.948× |
| 296 × 87040 | 8-CTA shared-tile | 10880 → 12288 | 30.62 | 31.74 |
0.965× |
| 370 × 87040 | 8-CTA shared-tile | 10880 → 12288 | 37.28 | 38.50 |
0.969× |
| 497 × 87040 | 8-CTA shared-tile | 10880 → 12288 | 49.92 | 50.34 |
0.992× |
| 45 × 88320 | 8-CTA shared-tile | 11040 → 12288 | 8.10 | 8.34 | 0.969×
|
| 79 × 88320 | 8-CTA persistent | 11040 → 12288 | 11.09 | 11.42 | 0.969×
|
| 93 × 88320 | 8-CTA persistent | 11040 → 12288 | 11.89 | 12.29 | 0.969×
|
| 128 × 88320 | 8-CTA persistent | 11040 → 12288 | 14.53 | 15.14 |
0.960× |
| 180 × 88320 | 8-CTA persistent | 11040 → 12288 | 18.67 | 19.46 |
0.961× |
| 231 × 88320 | 8-CTA persistent | 11040 → 12288 | 22.94 | 24.13 |
0.952× |
| 296 × 88320 | 8-CTA shared-tile | 11040 → 12288 | 31.20 | 31.94 |
0.977× |
| 370 × 88320 | 8-CTA shared-tile | 11040 → 12288 | 37.86 | 38.69 |
0.980× |
| 497 × 88320 | 8-CTA shared-tile | 11040 → 12288 | 50.74 | 50.82 |
0.997× |
| geometric mean | | | | | 0.959× |

Cake ships this softmax with no temperature, a scalar temperature, or a
per-row temperature, each with or without PDL, for B200 (sm_100a) and
GB300 (sm_103a).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Adjusted Blackwell softmax chunk selection for specific 8-CTA
launches, keeping whole-tile chunks for positive row counts when the cut
is at least one tenth.
* **Tests**
* Updated coverage for balanced chunk sizes, routing behavior, per-row
temperatures, and additional row counts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3292e01](https://github.com/flashinfer-ai/flashinfer/commit/3292e011804a99c7a235c1a0de95e5e44f5c6a45)

- **作者**: eigen
- **时间**: 2026-10-29T18:06:38Z
- **提交信息**: feat(cake_lm_head_loss): opt-in step-peak budget and caller's valid-row count (#7865)

FlashInfer's Cake chunked LM-head + loss backend
(`flashinfer.chunked_lm_head`) fuses the chunked large-vocabulary
projection (BF16 GEMM, FP32 accumulation) with log-sum-exp and the loss,
with a memory-bounded backward. It has one data type (BF16 X/W, FP32
statistics and loss) and three entry forms: cross-entropy
(`chunked_lm_head_loss(..., objective="ce")`), clipped policy-gradient
(`chunked_lm_head_loss(..., objective="policy")`), and differentiable
per-token log-probability (`chunked_lm_head_logprob`). This PR adds two
opt-in options: a step-peak budget mode (`memory_mode`) and a
caller-supplied valid-row count (`num_valid_rows`). In budget mode, the
step peak covers forward through backward, outputs included. The mode
bounds that peak by B, the bytes of a head that materializes the BF16
logits of the valid rows (B = 2·T_v·V + 2·V·H + 2·T·H, where T_v of the
T rows are valid). The planner targets B less a 2 % margin, and
`num_valid_rows` lets the caller pass T_v. The default path
(`memory_mode=None`, `num_valid_rows=None`) runs main's entry unchanged,
and it is the path timed below. An explicit `memory_mode="fast"` goes
through the opt-in dispatch before that entry, and those extra Python
calls were not timed.

Step-peak memory was measured on GB200 only, not on B200 or GB300. In
budget mode it is within both targets from #7545:

- **H=6144, V=154880, T=16384 (target ≤ 5.04 GiB):** 4.9906 GiB for a
single call, 4.9896 GiB for the first call, and at most 5.0248 GiB over
repeated calls with new valid-row counts. That is 15.6 MiB (0.3 %) below
the target.
- **H=4096 (target ≤ 4.41 GiB):** 3.8865, 3.8865 and at most 3.8879 GiB,
which is 0.5221 GiB below.

Budget-mode peaks stayed within B in all 12 measured configurations and
all 88 repeated calls, and the highest reading was 0.9801 B. In the
default mode, peaks equal main's and are above B on every measured
shape.

Compared with the previous Cake version on FlashInfer main, the default
path's speed at CUDA 13.4.92 is unchanged within measurement noise. The
device code is byte-identical in both packages. The geometric-mean ratio
(this PR / main) over 59 shapes is:

- **B200:** 0.99978 (95% CI 0.99963 to 1.00001) cooled and 1.00005
(0.99964 to 1.00049) hot.
- **GB300:** 0.99997 (0.99973 to 1.00017) cooled and 0.99987 (0.99934 to
1.00023) hot.

No shape was slower at the family-wise (Bonferroni) level on either GPU.
In their first reading, four shape-states were nominally slower in GPU
span: on GB300, policy loss T=16231 chunk 8192 cooled by 0.12 %,
cross-entropy T=16231 chunk 4096 with no ignored rows hot by 0.31 %, and
log-probability T=1 hot by 0.29 % (+7.31 us, of which +6.61 us was GPU
idle time; kernel-time ratio 0.9999); on B200, policy loss T=16231 chunk
4096 H=8192 V=128256 hot by 0.46 %. Re-run with twice the rounds, the
three whose kernel time was also nominally slower read 1.0006 (95% CI
0.9999 to 1.0012), 0.9981 (0.9966 to 0.9998) and 1.0004 (0.9987 to
1.0019) in kernel time, and the T=1 shape was not re-run because its
kernel time showed no difference. Cake ships no other data type, layout
or fused form of this kernel, and the backend covers sm_100a
(B200/GB200) and sm_103a (B300/GB300).

<!-- b200: 59 rows -->
| entry | T | chunk | H | V | ignored rows | cooled main (ms) | cooled
this PR (ms) | cooled speedup | hot main (ms) | hot this PR (ms) | hot
speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|
| loss, ce | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 57.123 | 57.069
| 1.001x | 65.442 | 65.533 | 0.999x |
| loss, policy | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 56.086 |
56.083 | 1.000x | 63.859 | 63.775 | 1.001x |
| loss, ce | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 57.098 | 57.127
| 0.999x | 63.780 | 63.874 | 0.999x |
| loss, policy | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 56.122 |
56.150 | 0.999x | 62.628 | 62.645 | 1.000x |
| loss, ce | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 7.637 | 7.638 |
1.000x | 7.550 | 7.550 | 1.000x |
| loss, policy | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 7.439 | 7.439
| 1.000x | 7.463 | 7.457 | 1.001x |
| loss, ce | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 29.198 | 29.212 |
1.000x | 31.106 | 31.109 | 1.000x |
| loss, policy | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 28.578 |
28.570 | 1.000x | 30.904 | 30.966 | 0.998x |
| loss, ce | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 119.132 |
119.008 | 1.001x | 134.767 | 135.010 | 0.998x |
| loss, policy | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 118.057 |
118.129 | 0.999x | 128.139 | 128.069 | 1.001x |
| loss, ce | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 251.771 |
251.731 | 1.000x | 264.669 | 264.699 | 1.000x |
| loss, policy | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 249.807 |
249.681 | 1.001x | 263.812 | 263.638 | 1.001x |
| loss, ce | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 58.514 | 58.478
| 1.001x | 65.611 | 65.508 | 1.002x |
| loss, policy | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 57.863 |
57.814 | 1.001x | 65.573 | 65.726 | 0.998x |
| loss, ce | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 58.653 | 58.622
| 1.001x | 64.851 | 65.010 | 0.998x |
| loss, policy | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 57.637 |
57.647 | 1.000x | 63.568 | 63.383 | 1.003x |
| loss, ce | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 14.808 | 14.808 |
1.000x | 15.001 | 15.003 | 1.000x |
| loss, policy | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 14.786 |
14.759 | 1.002x | 14.743 | 14.746 | 1.000x |
| loss, ce | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 55.670 | 55.691
| 1.000x | 63.772 | 63.925 | 0.998x |
| loss, policy | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 54.807 |
54.789 | 1.000x | 61.141 | 61.166 | 1.000x |
| loss, ce | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 63.136 | 63.083
| 1.001x | 70.688 | 70.632 | 1.001x |
| loss, policy | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 61.611 |
61.591 | 1.000x | 70.959 | 71.288 | 0.995x |
| log-probability | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 75.439 |
75.536 | 0.999x | 84.048 | 84.120 | 0.999x |
| log-probability | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 74.798 |
74.750 | 1.001x | 85.404 | 85.172 | 1.003x |
| log-probability | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 10.746 |
10.747 | 1.000x | 10.771 | 10.765 | 1.001x |
| log-probability | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 39.115 |
39.092 | 1.001x | 41.656 | 41.340 | 1.008x |
| log-probability | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 156.159
| 156.196 | 1.000x | 169.465 | 169.639 | 0.999x |
| log-probability | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 323.339
| 323.135 | 1.001x | 349.387 | 349.306 | 1.000x |
| log-probability | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 76.538 |
76.577 | 0.999x | 87.768 | 87.514 | 1.003x |
| log-probability | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 76.649 |
76.615 | 1.000x | 85.011 | 85.014 | 1.000x |
| log-probability | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 20.428 |
20.437 | 1.000x | 20.527 | 20.457 | 1.003x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.349 | 1.348 | 1.001x
| 1.362 | 1.365 | 0.998x |
| loss, ce | 4095 | 4096 | 6144 | 154880 | 205 (5 %) | 14.747 | 14.738 |
1.001x | 14.983 | 14.988 | 1.000x |
| loss, ce | 4097 | 4096 | 6144 | 154880 | 205 (5 %) | 15.031 | 15.026 |
1.000x | 15.052 | 15.052 | 1.000x |
| loss, ce | 16231 | 1024 | 6144 | 154880 | 812 (5 %) | 68.454 | 68.431
| 1.000x | 77.447 | 77.389 | 1.001x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 0 (0 %) | 61.129 | 61.149 |
1.000x | 68.670 | 68.621 | 1.001x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 4869 (30 %) | 42.750 |
42.817 | 0.998x | 47.117 | 47.065 | 1.001x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.215 | 1.215 | 1.000x
| 1.225 | 1.225 | 1.000x |
| loss, ce | 16 | 4096 | 6144 | 154880 | 1 (6 %) | 1.312 | 1.309 |
1.002x | 1.336 | 1.337 | 1.000x |
| loss, ce | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 1.391 | 1.389 |
1.002x | 1.419 | 1.420 | 0.999x |
| loss, ce | 512 | 4096 | 6144 | 154880 | 26 (5 %) | 2.385 | 2.385 |
1.000x | 2.361 | 2.361 | 1.000x |
| loss, ce | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 4.038 | 4.039 |
1.000x | 4.087 | 4.089 | 1.000x |
| loss, ce | 1536 | 4096 | 6144 | 154880 | 77 (5 %) | 5.731 | 5.732 |
1.000x | 5.754 | 5.755 | 1.000x |
| loss, ce | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 11.080 | 11.082 |
1.000x | 11.093 | 11.088 | 1.000x |
| loss, ce | 6144 | 4096 | 6144 | 154880 | 307 (5 %) | 21.961 | 21.955 |
1.000x | 23.052 | 23.045 | 1.000x |
| loss, ce | 8193 | 4096 | 6144 | 154880 | 410 (5 %) | 29.068 | 29.084 |
0.999x | 31.448 | 31.625 | 0.994x |
| loss, ce | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 43.035 | 43.010
| 1.001x | 47.506 | 47.581 | 0.998x |
| loss, ce | 24576 | 4096 | 6144 | 154880 | 1229 (5 %) | 90.365 | 90.413
| 0.999x | 100.469 | 100.515 | 1.000x |
| loss, ce | 49152 | 4096 | 6144 | 154880 | 2458 (5 %) | 190.688 |
190.582 | 1.001x | 202.651 | 202.726 | 1.000x |
| log-probability | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 2.343 | 2.341 |
1.001x | 2.344 | 2.345 | 0.999x |
| log-probability | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 2.619 | 2.622
| 0.999x | 2.628 | 2.626 | 1.000x |
| log-probability | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 6.181 |
6.178 | 1.001x | 6.167 | 6.169 | 1.000x |
| log-probability | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 15.294 |
15.290 | 1.000x | 15.348 | 15.353 | 1.000x |
| log-probability | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 57.523 |
57.484 | 1.001x | 63.583 | 63.480 | 1.002x |
| loss, policy | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.230 | 1.228 |
1.002x | 1.239 | 1.239 | 1.000x |
| loss, policy | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 1.639 | 1.639 |
1.000x | 1.664 | 1.663 | 1.001x |
| loss, policy | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 4.072 | 4.072
| 1.000x | 4.031 | 4.031 | 1.000x |
| loss, policy | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 10.882 |
10.885 | 1.000x | 10.906 | 10.922 | 0.999x |
| loss, policy | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 42.330 |
42.267 | 1.001x | 47.338 | 47.251 | 1.002x |

Measured on NVIDIA B200 (sm_100a, driver 580.82.07), both packages built
by nvcc 13.4.92; both sides are called through the public
`flashinfer.chunked_lm_head` entry with default arguments. Each time
covers one forward + backward call: the GPU span from the first to the
last kernel, measured with CUPTI with the L2 flushed. "Cooled": the GPU
is idle-cooled before each call. "Hot": calls begin 2.0 ms apart without
cooling. Each time is the geometric mean over 2 runs of each run's
median over 64 interleaved A/B rounds per state. Speedup = main / this
PR. Geometric mean of this PR / main over 59 shapes: cooled 0.99978 (95%
CI 0.99963 to 1.00001), hot 1.00005 (95% CI 0.99964 to 1.00049).

<!-- gb300: 59 rows -->
| entry | T | chunk | H | V | ignored rows | cooled main (ms) | cooled
this PR (ms) | cooled speedup | hot main (ms) | hot this PR (ms) | hot
speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|
| loss, ce | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 47.127 | 47.100
| 1.001x | 51.461 | 51.287 | 1.003x |
| loss, policy | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 46.525 |
46.516 | 1.000x | 50.602 | 50.587 | 1.000x |
| loss, ce | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 47.122 | 47.095
| 1.001x | 51.366 | 51.348 | 1.000x |
| loss, policy | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 46.444 |
46.450 | 1.000x | 50.546 | 50.510 | 1.001x |
| loss, ce | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 6.339 | 6.339 |
1.000x | 6.328 | 6.328 | 1.000x |
| loss, policy | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 6.247 | 6.249
| 1.000x | 6.235 | 6.236 | 1.000x |
| loss, ce | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 24.310 | 24.338 |
0.999x | 25.597 | 25.671 | 0.997x |
| loss, policy | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 23.821 |
23.816 | 1.000x | 25.028 | 24.976 | 1.002x |
| loss, ce | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 98.578 | 98.573
| 1.000x | 106.115 | 106.006 | 1.001x |
| loss, policy | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 97.094 |
97.122 | 1.000x | 104.192 | 104.271 | 0.999x |
| loss, ce | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 205.181 |
205.277 | 1.000x | 216.291 | 216.233 | 1.000x |
| loss, policy | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 202.400 |
202.360 | 1.000x | 213.479 | 213.387 | 1.000x |
| loss, ce | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 48.236 | 48.297
| 0.999x | 52.847 | 52.847 | 1.000x |
| loss, policy | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 47.724 |
47.727 | 1.000x | 51.979 | 51.999 | 1.000x |
| loss, ce | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 47.197 | 47.192
| 1.000x | 51.796 | 51.759 | 1.001x |
| loss, policy | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 46.222 |
46.280 | 0.999x | 50.527 | 50.637 | 0.998x |
| loss, ce | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 12.158 | 12.159 |
1.000x | 12.484 | 12.465 | 1.002x |
| loss, policy | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 11.932 |
11.927 | 1.000x | 12.231 | 12.233 | 1.000x |
| loss, ce | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 45.250 | 45.227
| 1.001x | 49.683 | 49.784 | 0.998x |
| loss, policy | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 44.853 |
44.828 | 1.001x | 49.074 | 49.023 | 1.001x |
| loss, ce | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 51.616 | 51.580
| 1.001x | 56.773 | 57.025 | 0.996x |
| loss, policy | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 50.827 |
50.843 | 1.000x | 56.205 | 56.118 | 1.002x |
| log-probability | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 62.115 |
62.139 | 1.000x | 68.578 | 68.505 | 1.001x |
| log-probability | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 62.108 |
62.075 | 1.001x | 68.461 | 68.413 | 1.001x |
| log-probability | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 9.079 |
9.078 | 1.000x | 9.475 | 9.475 | 1.000x |
| log-probability | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 31.773 |
31.772 | 1.000x | 34.391 | 34.304 | 1.003x |
| log-probability | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 129.136
| 129.155 | 1.000x | 139.393 | 139.317 | 1.001x |
| log-probability | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 265.945
| 265.933 | 1.000x | 283.520 | 283.590 | 1.000x |
| log-probability | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 63.432 |
63.496 | 0.999x | 70.172 | 70.172 | 1.000x |
| log-probability | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 62.405 |
62.395 | 1.000x | 68.677 | 68.736 | 0.999x |
| log-probability | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 16.890 |
16.888 | 1.000x | 17.668 | 17.697 | 0.998x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.298 | 1.300 | 0.998x
| 1.428 | 1.426 | 1.001x |
| loss, ce | 4095 | 4096 | 6144 | 154880 | 205 (5 %) | 12.241 | 12.238 |
1.000x | 12.553 | 12.544 | 1.001x |
| loss, ce | 4097 | 4096 | 6144 | 154880 | 205 (5 %) | 12.261 | 12.260 |
1.000x | 12.581 | 12.571 | 1.001x |
| loss, ce | 16231 | 1024 | 6144 | 154880 | 812 (5 %) | 55.290 | 55.266
| 1.000x | 58.950 | 58.834 | 1.002x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 0 (0 %) | 49.076 | 49.039 |
1.001x | 54.204 | 54.370 | 0.997x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 4869 (30 %) | 34.365 |
34.360 | 1.000x | 37.665 | 37.445 | 1.006x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.278 | 1.278 | 1.000x
| 1.283 | 1.282 | 1.001x |
| loss, ce | 16 | 4096 | 6144 | 154880 | 1 (6 %) | 1.424 | 1.421 |
1.002x | 1.431 | 1.441 | 0.993x |
| loss, ce | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 1.523 | 1.520 |
1.002x | 1.522 | 1.522 | 1.000x |
| loss, ce | 512 | 4096 | 6144 | 154880 | 26 (5 %) | 2.050 | 2.053 |
0.998x | 2.047 | 2.046 | 1.000x |
| loss, ce | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 3.442 | 3.444 |
0.999x | 3.423 | 3.426 | 0.999x |
| loss, ce | 1536 | 4096 | 6144 | 154880 | 77 (5 %) | 4.850 | 4.851 |
1.000x | 4.840 | 4.841 | 1.000x |
| loss, ce | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 9.210 | 9.206 |
1.000x | 9.183 | 9.187 | 1.000x |
| loss, ce | 6144 | 4096 | 6144 | 154880 | 307 (5 %) | 18.370 | 18.370 |
1.000x | 18.850 | 18.866 | 0.999x |
| loss, ce | 8193 | 4096 | 6144 | 154880 | 410 (5 %) | 24.120 | 24.123 |
1.000x | 25.482 | 25.528 | 0.998x |
| loss, ce | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 35.539 | 35.540
| 1.000x | 38.357 | 38.149 | 1.005x |
| loss, ce | 24576 | 4096 | 6144 | 154880 | 1229 (5 %) | 73.075 | 73.107
| 1.000x | 78.599 | 78.596 | 1.000x |
| loss, ce | 49152 | 4096 | 6144 | 154880 | 2458 (5 %) | 153.033 |
153.027 | 1.000x | 160.287 | 160.262 | 1.000x |
| log-probability | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 2.488 | 2.489 |
1.000x | 2.519 | 2.527 | 0.997x |
| log-probability | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 2.722 | 2.724
| 0.999x | 2.793 | 2.797 | 0.999x |
| log-probability | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 5.451 |
5.451 | 1.000x | 5.482 | 5.481 | 1.000x |
| log-probability | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 12.987 |
12.973 | 1.001x | 12.990 | 13.003 | 0.999x |
| log-probability | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 46.998 |
47.034 | 0.999x | 50.581 | 50.504 | 1.002x |
| loss, policy | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.289 | 1.289 |
1.000x | 1.316 | 1.314 | 1.002x |
| loss, policy | 128 | 4096 | 6144 | 154880 | 6 (5 %) | 1.918 | 1.915 |
1.002x | 1.995 | 1.991 | 1.002x |
| loss, policy | 1024 | 4096 | 6144 | 154880 | 51 (5 %) | 3.441 | 3.439
| 1.001x | 3.421 | 3.420 | 1.000x |
| loss, policy | 3072 | 4096 | 6144 | 154880 | 154 (5 %) | 9.138 | 9.137
| 1.000x | 9.096 | 9.104 | 0.999x |
| loss, policy | 12288 | 4096 | 6144 | 154880 | 614 (5 %) | 35.013 |
35.016 | 1.000x | 37.552 | 37.458 | 1.003x |

Measured on NVIDIA GB300 (sm_103a, driver 580.159.03), both packages
built by nvcc 13.4.92; both sides are called through the public
`flashinfer.chunked_lm_head` entry with default arguments. Each time
covers one forward + backward call: the GPU span from the first to the
last kernel, measured with CUPTI with the L2 flushed. "Cooled": the GPU
is idle-cooled before each call. "Hot": calls begin 2.0 ms apart without
cooling. Each time is the geometric mean over 2 runs of each run's
median over 32 interleaved A/B rounds per state. Speedup = main / this
PR. Geometric mean of this PR / main over 59 shapes: cooled 0.99997 (95%
CI 0.99973 to 1.00017), hot 0.99987 (95% CI 0.99934 to 1.00023).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional memory modes for chunked language-model head loss
calculations, including a budget mode designed to reduce memory use.
* Added optional valid-row counts and validation for loss and
log-probability calculations.
* Added an experimental preload option for CUDA devices. Existing calls
without the new options continue to use the default behavior.
* **Documentation**
  * Expanded guidance on memory modes, valid-row counts, and preloading.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [311b6c2](https://github.com/flashinfer-ai/flashinfer/commit/311b6c22059cd5bd34fb18fff84bb6bb47f68fb6)

- **作者**: eigen
- **时间**: 2026-10-29T18:06:23Z
- **提交信息**: perf(cake_nvfp4_mla_decode): reverse the per-unit piece order of long-row decode plans on GB200 (#7861)

This PR changes `cake_nvfp4_mla_decode`
(`flashinfer.mla.prepare_nvfp4_batch_decode_with_kv_cache_mla`,
experimental), the MLA decode with NVFP4 queries and KV cache. The
kernel has one variant (one data type, one layout, no fused forms), and
this PR changes that variant. On GB200 (sm_100a with 152 SMs), the
host-side work plan of long-row decodes now runs the pieces of each work
unit in reverse order. The device programs are the same as in `main`,
and B200 (148 SMs) and GB300 (sm_103a) plans are unchanged. The baseline
is the previous Cake version of this kernel in `main`. Each latency is
the median over two GPUs of the median CUDA graph replay time with a
cold L2, and each speedup is the median over the same two GPUs of each
GPU's paired ratio of the `main` time to this PR's time, so it can
differ slightly from the quotient of the two latency columns.

On GB200, batch 32 with 64 heads and 6 query tokens speeds up by 1.008x
at 8K keys each, 1.042x at 16K, 1.043x at 32K, 1.041x at 64K and 1.038x
at 128K.

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| Shape | `main` (µs) | This PR (µs) | Speedup |
|---|---:|---:|---:|
| batch 32, 8K keys each, 64 heads, 6 query tokens | 100.13 | 99.18 |
1.008x |
| batch 32, 16K keys each, 64 heads, 6 query tokens | 179.12 | 172.12 |
1.042x |
| batch 32, 32K keys each, 64 heads, 6 query tokens | 328.47 | 314.96 |
1.043x |
| batch 32, 64K keys each, 64 heads, 6 query tokens | 609.68 | 585.81 |
1.041x |
| batch 32, 128K keys each, 64 heads, 6 query tokens | 1175.18 | 1131.76
| 1.038x |

Cake has no other variants of this decode (no other data type, layout or
fused form), and the kernel covers sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Balanced decode plans on the supported SM100 configuration now use a
different piece order for long rows, while preserving row-pair order and
unit boundaries.
* Short-row plans and configurations outside this case retain their
existing piece order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [aa69286](https://github.com/flashinfer-ai/flashinfer/commit/aa692863569afe6f9c1c5256ba2de423c6578a80)

- **作者**: eigen
- **时间**: 2026-10-29T18:06:10Z
- **提交信息**: perf(cake_deepgemm): SM120 paged MQA-logits: per-device tuned programs for RTX 5090 and RTX PRO 6000 (#7860)

The SM120a paged FP8 MQA logits kernel
(`flashinfer/experimental/deepgemm_sm120_paged_mqa_logits`, the
DeepSeek-V3.2 / V4.1-Flash decode lightning indexer) ships one program
per route, covering FP8 E4M3 inputs, page sizes 64 and 128, 32 or 64
heads, and next_n 1-6. This PR adds per-device routes that are selected
by the GPU's SM count. RTX 5090 (170 SMs) gets 33 tuned programs, and
RTX PRO 6000 (188 SMs) gets 55, 22 of which use a dynamic-tail schedule.
These routes serve 138 of the 216 measured shapes on each GPU, and the
other 78 keep the shipped programs. Compared with the shipped Cake
routes on current main, the geometric-mean speedup on the 138 routed
shapes over two independent runs is 1.077x / 1.079x on RTX 5090 (per
shape 1.006x-1.439x) and 1.058x / 1.059x on RTX PRO 6000 (per shape
1.006x-1.371x), and the logits stay bitwise identical to DeepGEMM.

Table: kernel time of one call (scheduler + logits kernels) on NVIDIA
GeForce RTX 5090 and NVIDIA RTX PRO 6000 Blackwell Server Edition (both
sm_120a, Blackwell GB202, CUDA 13.4). There is one row per shape (heads,
page size, next_n, batch, context tokens), with shipped and new latency
in µs and the speedup for two independent runs. Rows marked ¹ keep the
shipped program, so both sides run the same program.

**RTX 5090**

| heads | page | next_n | batch | context | shipped µs | new µs |
speedup | shipped µs | new µs | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | 10.34 | 10.34 | 1.000× | 10.18 | 10.18 |
1.000× ¹ |
| 32 | 64 | 1 | 64 | 4096 | 32.70 | 32.73 | 0.999× | 32.58 | 32.58 |
1.000× ¹ |
| 32 | 64 | 1 | 256 | 4096 | 110.40 | 106.46 | 1.037× | 110.05 | 106.21
| 1.036× |
| 32 | 64 | 1 | 1 | 16384 | 9.25 | 9.06 | 1.021× | 9.09 | 8.86 | 1.025×
|
| 32 | 64 | 1 | 8 | 16384 | 19.52 | 19.52 | 1.000× | 19.71 | 19.71 |
1.000× ¹ |
| 32 | 64 | 1 | 32 | 16384 | 56.61 | 55.14 | 1.027× | 56.41 | 54.91 |
1.027× |
| 32 | 64 | 1 | 64 | 16384 | 107.39 | 104.25 | 1.030× | 106.88 | 103.45
| 1.033× |
| 32 | 64 | 1 | 128 | 16384 | 206.05 | 197.21 | 1.045× | 205.37 | 196.45
| 1.045× |
| 32 | 64 | 1 | 256 | 16384 | 397.63 | 379.84 | 1.047× | 395.68 | 379.58
| 1.042× |
| 32 | 64 | 1 | 8 | 65536 | 60.26 | 58.50 | 1.030× | 60.06 | 58.37 |
1.029× |
| 32 | 64 | 1 | 32 | 65536 | 199.58 | 191.49 | 1.042× | 198.98 | 191.26
| 1.040× |
| 32 | 64 | 1 | 128 | 65536 | 747.43 | 724.63 | 1.031× | 744.62 | 721.53
| 1.032× |
| 32 | 64 | 2 | 8 | 4096 | 11.07 | 11.07 | 1.000× | 10.94 | 10.94 |
1.000× ¹ |
| 32 | 64 | 2 | 64 | 4096 | 35.07 | 35.07 | 1.000× | 34.66 | 34.66 |
1.000× ¹ |
| 32 | 64 | 2 | 256 | 4096 | 115.90 | 110.85 | 1.046× | 115.10 | 110.11
| 1.045× |
| 32 | 64 | 2 | 1 | 16384 | 9.54 | 9.25 | 1.031× | 9.44 | 9.15 | 1.031×
|
| 32 | 64 | 2 | 8 | 16384 | 20.70 | 20.70 | 1.000× | 20.61 | 20.61 |
1.000× ¹ |
| 32 | 64 | 2 | 32 | 16384 | 59.20 | 56.58 | 1.046× | 58.85 | 56.26 |
1.046× |
| 32 | 64 | 2 | 64 | 16384 | 112.03 | 107.71 | 1.040× | 111.45 | 107.17
| 1.040× |
| 32 | 64 | 2 | 128 | 16384 | 216.32 | 207.71 | 1.041× | 215.04 | 207.06
| 1.039× |
| 32 | 64 | 2 | 256 | 16384 | 418.62 | 400.15 | 1.046× | 416.86 | 398.84
| 1.045× |
| 32 | 64 | 2 | 8 | 65536 | 62.88 | 60.10 | 1.046× | 62.46 | 59.81 |
1.044× |
| 32 | 64 | 2 | 32 | 65536 | 208.25 | 200.83 | 1.037× | 207.58 | 200.57
| 1.035× |
| 32 | 64 | 2 | 128 | 65536 | 791.80 | 764.33 | 1.036× | 785.21 | 759.51
| 1.034× |
| 32 | 64 | 3 | 8 | 4096 | 11.39 | 11.39 | 1.000× | 11.20 | 11.20 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 4096 | 37.15 | 37.15 | 1.000× | 37.06 | 37.06 |
1.000× ¹ |
| 32 | 64 | 3 | 256 | 4096 | 124.25 | 118.08 | 1.052× | 123.81 | 117.06
| 1.058× |
| 32 | 64 | 3 | 1 | 16384 | 10.01 | 9.31 | 1.075× | 9.98 | 9.31 | 1.072×
|
| 32 | 64 | 3 | 8 | 16384 | 22.30 | 22.30 | 1.000× | 21.89 | 21.89 |
1.000× ¹ |
| 32 | 64 | 3 | 32 | 16384 | 63.04 | 59.23 | 1.064× | 62.72 | 58.88 |
1.065× |
| 32 | 64 | 3 | 64 | 16384 | 119.55 | 113.98 | 1.049× | 119.23 | 113.66
| 1.049× |
| 32 | 64 | 3 | 128 | 16384 | 225.66 | 219.52 | 1.028× | 224.80 | 218.08
| 1.031× |
| 32 | 64 | 3 | 256 | 16384 | 436.95 | 425.15 | 1.028× | 435.10 | 421.98
| 1.031× |
| 32 | 64 | 3 | 8 | 65536 | 66.40 | 62.66 | 1.060× | 66.02 | 62.24 |
1.061× |
| 32 | 64 | 3 | 32 | 65536 | 218.53 | 211.96 | 1.031× | 216.93 | 211.26
| 1.027× |
| 32 | 64 | 3 | 128 | 65536 | 832.24 | 808.40 | 1.029× | 831.13 | 808.26
| 1.028× |
| 32 | 64 | 4 | 8 | 4096 | 11.68 | 10.50 | 1.113× | 11.55 | 10.43 |
1.107× |
| 32 | 64 | 4 | 64 | 4096 | 40.29 | 40.32 | 0.999× | 39.58 | 39.58 |
1.000× ¹ |
| 32 | 64 | 4 | 256 | 4096 | 131.65 | 124.89 | 1.054× | 131.77 | 124.54
| 1.058× |
| 32 | 64 | 4 | 1 | 16384 | 10.34 | 9.50 | 1.087× | 10.21 | 9.44 |
1.081× |
| 32 | 64 | 4 | 8 | 16384 | 23.87 | 23.87 | 1.000× | 23.13 | 23.13 |
1.000× ¹ |
| 32 | 64 | 4 | 32 | 16384 | 67.87 | 67.90 | 1.000× | 67.33 | 67.33 |
1.000× ¹ |
| 32 | 64 | 4 | 64 | 16384 | 125.73 | 120.38 | 1.044× | 125.25 | 119.71
| 1.046× |
| 32 | 64 | 4 | 128 | 16384 | 237.92 | 231.10 | 1.029× | 235.52 | 228.99
| 1.029× |
| 32 | 64 | 4 | 256 | 16384 | 457.79 | 447.55 | 1.023× | 450.01 | 443.96
| 1.014× |
| 32 | 64 | 4 | 8 | 65536 | 70.40 | 65.28 | 1.078× | 70.40 | 65.21 |
1.079× |
| 32 | 64 | 4 | 32 | 65536 | 229.56 | 224.03 | 1.025× | 226.53 | 221.31
| 1.024× |
| 32 | 64 | 4 | 128 | 65536 | 853.83 | 854.38 | 0.999× | 862.26 | 862.71
| 0.999× ¹ |
| 32 | 64 | 5 | 8 | 4096 | 13.25 | 11.68 | 1.134× | 13.09 | 11.52 |
1.136× |
| 32 | 64 | 5 | 64 | 4096 | 43.01 | 43.01 | 1.000× | 42.72 | 42.72 |
1.000× ¹ |
| 32 | 64 | 5 | 256 | 4096 | 137.53 | 137.53 | 1.000× | 139.10 | 139.13
| 1.000× ¹ |
| 32 | 64 | 5 | 1 | 16384 | 11.14 | 10.18 | 1.094× | 11.01 | 10.08 |
1.092× |
| 32 | 64 | 5 | 8 | 16384 | 24.61 | 24.61 | 1.000× | 24.67 | 24.67 |
1.000× ¹ |
| 32 | 64 | 5 | 32 | 16384 | 74.43 | 68.45 | 1.087× | 72.67 | 66.53 |
1.092× |
| 32 | 64 | 5 | 64 | 16384 | 133.31 | 133.34 | 1.000× | 134.62 | 134.59
| 1.000× ¹ |
| 32 | 64 | 5 | 128 | 16384 | 246.81 | 245.44 | 1.006× | 244.35 | 241.79
| 1.011× |
| 32 | 64 | 5 | 256 | 16384 | 470.01 | 460.98 | 1.020× | 465.59 | 457.02
| 1.019× |
| 32 | 64 | 5 | 8 | 65536 | 76.48 | 70.53 | 1.084× | 75.87 | 70.40 |
1.078× |
| 32 | 64 | 5 | 32 | 65536 | 235.26 | 235.55 | 0.999× | 236.35 | 236.61
| 0.999× ¹ |
| 32 | 64 | 5 | 128 | 65536 | 905.18 | 897.59 | 1.008× | 951.00 | 949.48
| 1.002× ¹ |
| 32 | 64 | 6 | 8 | 4096 | 13.47 | 11.58 | 1.163× | 13.34 | 11.46 |
1.165× |
| 32 | 64 | 6 | 64 | 4096 | 47.90 | 42.66 | 1.123× | 46.78 | 42.14 |
1.110× |
| 32 | 64 | 6 | 256 | 4096 | 161.47 | 157.38 | 1.026× | 157.89 | 153.63
| 1.028× |
| 32 | 64 | 6 | 1 | 16384 | 11.17 | 10.01 | 1.115× | 11.10 | 9.95 |
1.116× |
| 32 | 64 | 6 | 8 | 16384 | 27.36 | 25.25 | 1.084× | 27.01 | 24.61 |
1.098× |
| 32 | 64 | 6 | 32 | 16384 | 85.38 | 76.45 | 1.117× | 83.33 | 72.96 |
1.142× |
| 32 | 64 | 6 | 64 | 16384 | 154.43 | 150.91 | 1.023× | 151.36 | 147.23
| 1.028× |
| 32 | 64 | 6 | 128 | 16384 | 285.76 | 276.42 | 1.034× | 280.83 | 271.93
| 1.033× |
| 32 | 64 | 6 | 256 | 16384 | 550.42 | 534.07 | 1.031× | 538.11 | 523.32
| 1.028× |
| 32 | 64 | 6 | 8 | 65536 | 85.92 | 78.05 | 1.101× | 83.97 | 74.78 |
1.123× |
| 32 | 64 | 6 | 32 | 65536 | 275.64 | 266.59 | 1.034× | 270.89 | 262.49
| 1.032× |
| 32 | 64 | 6 | 128 | 65536 | 1076.48 | 1077.11 | 0.999× | 1045.15 |
1044.93 | 1.000× ¹ |
| 32 | 128 | 1 | 8 | 4096 | 10.30 | 10.30 | 1.000× | 10.18 | 10.18 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 4096 | 32.77 | 32.77 | 1.000× | 32.74 | 32.74 |
1.000× ¹ |
| 32 | 128 | 1 | 256 | 4096 | 110.24 | 106.30 | 1.037× | 110.24 | 106.21
| 1.038× |
| 32 | 128 | 1 | 1 | 16384 | 9.28 | 9.25 | 1.003× | 9.15 | 9.15 | 1.000×
¹ |
| 32 | 128 | 1 | 8 | 16384 | 19.62 | 19.62 | 1.000× | 19.65 | 19.65 |
1.000× ¹ |
| 32 | 128 | 1 | 32 | 16384 | 56.64 | 56.64 | 1.000× | 56.48 | 56.48 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 16384 | 107.26 | 103.68 | 1.035× | 107.01 | 103.48
| 1.034× |
| 32 | 128 | 1 | 128 | 16384 | 205.63 | 197.12 | 1.043× | 205.66 |
196.96 | 1.044× |
| 32 | 128 | 1 | 256 | 16384 | 395.13 | 379.23 | 1.042× | 394.68 |
378.39 | 1.043× |
| 32 | 128 | 1 | 8 | 65536 | 60.29 | 58.46 | 1.031× | 59.97 | 58.24 |
1.030× |
| 32 | 128 | 1 | 32 | 65536 | 199.65 | 191.48 | 1.043× | 198.62 | 190.78
| 1.041× |
| 32 | 128 | 1 | 128 | 65536 | 747.24 | 723.70 | 1.033× | 747.61 |
721.70 | 1.036× |
| 32 | 128 | 2 | 8 | 4096 | 11.17 | 11.17 | 1.000× | 10.91 | 10.91 |
1.000× ¹ |
| 32 | 128 | 2 | 64 | 4096 | 34.85 | 34.85 | 1.000× | 34.82 | 34.81 |
1.000× ¹ |
| 32 | 128 | 2 | 256 | 4096 | 116.16 | 111.58 | 1.041× | 116.22 | 111.26
| 1.045× |
| 32 | 128 | 2 | 1 | 16384 | 9.66 | 9.31 | 1.038× | 9.63 | 9.22 | 1.045×
|
| 32 | 128 | 2 | 8 | 16384 | 20.45 | 20.45 | 1.000× | 20.58 | 20.58 |
1.000× ¹ |
| 32 | 128 | 2 | 32 | 16384 | 59.42 | 59.42 | 1.000× | 59.01 | 59.04 |
0.999× ¹ |
| 32 | 128 | 2 | 64 | 16384 | 112.00 | 107.94 | 1.038× | 111.90 | 107.90
| 1.037× |
| 32 | 128 | 2 | 128 | 16384 | 214.75 | 207.84 | 1.033× | 214.59 |
207.10 | 1.036× |
| 32 | 128 | 2 | 256 | 16384 | 416.47 | 400.95 | 1.039× | 415.23 |
398.34 | 1.042× |
| 32 | 128 | 2 | 8 | 65536 | 62.69 | 59.97 | 1.045× | 62.34 | 59.81 |
1.042× |
| 32 | 128 | 2 | 32 | 65536 | 208.35 | 201.92 | 1.032× | 207.49 | 200.22
| 1.036× |
| 32 | 128 | 2 | 128 | 65536 | 798.04 | 765.59 | 1.042× | 789.36 |
761.19 | 1.037× |
| 32 | 128 | 3 | 8 | 4096 | 11.42 | 11.42 | 1.000× | 11.20 | 11.20 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 4096 | 37.44 | 37.41 | 1.001× | 37.12 | 37.12 |
1.000× ¹ |
| 32 | 128 | 3 | 256 | 4096 | 124.13 | 117.85 | 1.053× | 123.97 | 117.69
| 1.053× |
| 32 | 128 | 3 | 1 | 16384 | 10.05 | 10.05 | 1.000× | 9.98 | 9.98 |
1.000× ¹ |
| 32 | 128 | 3 | 8 | 16384 | 22.02 | 22.02 | 1.000× | 21.66 | 21.66 |
1.000× ¹ |
| 32 | 128 | 3 | 32 | 16384 | 63.20 | 59.55 | 1.061× | 62.59 | 59.17 |
1.058× |
| 32 | 128 | 3 | 64 | 16384 | 119.90 | 114.81 | 1.044× | 118.78 | 113.53
| 1.046× |
| 32 | 128 | 3 | 128 | 16384 | 225.60 | 219.26 | 1.029× | 225.25 |
218.05 | 1.033× |
| 32 | 128 | 3 | 256 | 16384 | 436.35 | 424.40 | 1.028× | 434.94 |
423.31 | 1.027× |
| 32 | 128 | 3 | 8 | 65536 | 66.59 | 63.04 | 1.056× | 66.11 | 62.75 |
1.054× |
| 32 | 128 | 3 | 32 | 65536 | 217.47 | 213.25 | 1.020× | 216.12 | 211.71
| 1.021× |
| 32 | 128 | 3 | 128 | 65536 | 825.38 | 810.14 | 1.019× | 832.99 |
812.47 | 1.025× |
| 32 | 128 | 4 | 8 | 4096 | 11.65 | 11.65 | 1.000× | 11.49 | 11.52 |
0.997× ¹ |
| 32 | 128 | 4 | 64 | 4096 | 40.64 | 40.64 | 1.000× | 40.42 | 40.41 |
1.000× ¹ |
| 32 | 128 | 4 | 256 | 4096 | 131.61 | 124.25 | 1.059× | 132.38 | 124.80
| 1.061× |
| 32 | 128 | 4 | 1 | 16384 | 10.37 | 10.40 | 0.997× | 10.24 | 10.24 |
1.000× ¹ |
| 32 | 128 | 4 | 8 | 16384 | 24.42 | 24.42 | 1.000× | 23.97 | 23.97 |
1.000× ¹ |
| 32 | 128 | 4 | 32 | 16384 | 68.45 | 68.42 | 1.000× | 68.38 | 68.42 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 16384 | 126.37 | 120.38 | 1.050× | 126.75 | 121.09
| 1.047× |
| 32 | 128 | 4 | 128 | 16384 | 239.55 | 230.85 | 1.038× | 236.70 |
229.34 | 1.032× |
| 32 | 128 | 4 | 256 | 16384 | 456.99 | 447.58 | 1.021× | 454.52 |
444.92 | 1.022× |
| 32 | 128 | 4 | 8 | 65536 | 71.33 | 65.41 | 1.091× | 70.33 | 64.70 |
1.087× |
| 32 | 128 | 4 | 32 | 65536 | 230.40 | 223.97 | 1.029× | 228.19 | 221.47
| 1.030× |
| 32 | 128 | 4 | 128 | 65536 | 869.29 | 853.14 | 1.019× | 864.58 |
851.49 | 1.015× |
| 32 | 128 | 5 | 8 | 4096 | 13.31 | 11.71 | 1.137× | 13.15 | 11.58 |
1.135× |
| 32 | 128 | 5 | 64 | 4096 | 42.94 | 42.94 | 1.000× | 42.85 | 42.85 |
1.000× ¹ |
| 32 | 128 | 5 | 256 | 4096 | 137.31 | 137.31 | 1.000× | 139.58 | 139.58
| 1.000× ¹ |
| 32 | 128 | 5 | 1 | 16384 | 11.10 | 10.21 | 1.088× | 11.04 | 10.11 |
1.092× |
| 32 | 128 | 5 | 8 | 16384 | 24.51 | 22.46 | 1.091× | 24.61 | 22.46 |
1.095× |
| 32 | 128 | 5 | 32 | 16384 | 72.61 | 72.64 | 1.000× | 73.66 | 73.62 |
1.001× ¹ |
| 32 | 128 | 5 | 64 | 16384 | 133.41 | 133.41 | 1.000× | 134.24 | 134.24
| 1.000× ¹ |
| 32 | 128 | 5 | 128 | 16384 | 243.39 | 243.77 | 0.998× | 245.37 |
245.41 | 1.000× ¹ |
| 32 | 128 | 5 | 256 | 16384 | 470.36 | 461.21 | 1.020× | 466.65 |
454.49 | 1.027× |
| 32 | 128 | 5 | 8 | 65536 | 76.90 | 71.07 | 1.082× | 75.17 | 69.53 |
1.081× |
| 32 | 128 | 5 | 32 | 65536 | 235.36 | 235.33 | 1.000× | 236.61 | 236.86
| 0.999× ¹ |
| 32 | 128 | 5 | 128 | 65536 | 901.24 | 898.77 | 1.003× | 880.09 |
880.65 | 0.999× ¹ |
| 32 | 128 | 6 | 8 | 4096 | 13.50 | 11.62 | 1.163× | 13.44 | 11.46 |
1.173× |
| 32 | 128 | 6 | 64 | 4096 | 48.00 | 42.82 | 1.121× | 46.62 | 41.15 |
1.133× |
| 32 | 128 | 6 | 256 | 4096 | 161.76 | 157.15 | 1.029× | 158.11 | 154.24
| 1.025× |
| 32 | 128 | 6 | 1 | 16384 | 11.26 | 10.14 | 1.110× | 11.14 | 10.05 |
1.108× |
| 32 | 128 | 6 | 8 | 16384 | 27.26 | 24.58 | 1.109× | 27.01 | 24.96 |
1.082× |
| 32 | 128 | 6 | 32 | 16384 | 84.42 | 76.09 | 1.109× | 81.98 | 72.35 |
1.133× |
| 32 | 128 | 6 | 64 | 16384 | 154.56 | 150.44 | 1.027× | 151.84 | 148.06
| 1.026× |
| 32 | 128 | 6 | 128 | 16384 | 286.43 | 277.12 | 1.034× | 280.83 |
271.81 | 1.033× |
| 32 | 128 | 6 | 256 | 16384 | 551.03 | 551.55 | 0.999× | 538.81 |
538.49 | 1.001× ¹ |
| 32 | 128 | 6 | 8 | 65536 | 86.53 | 78.81 | 1.098× | 84.09 | 74.62 |
1.127× |
| 32 | 128 | 6 | 32 | 65536 | 277.02 | 267.52 | 1.036× | 271.23 | 262.46
| 1.033× |
| 32 | 128 | 6 | 128 | 65536 | 1083.98 | 1084.58 | 0.999× | 1044.72 |
1048.87 | 0.996× ¹ |
| 64 | 64 | 1 | 8 | 4096 | 11.04 | 11.04 | 1.000× | 10.88 | 10.88 |
1.000× ¹ |
| 64 | 64 | 1 | 64 | 4096 | 34.11 | 34.11 | 1.000× | 33.95 | 33.92 |
1.001× ¹ |
| 64 | 64 | 1 | 256 | 4096 | 113.31 | 108.03 | 1.049× | 113.12 | 107.45
| 1.053× |
| 64 | 64 | 1 | 1 | 16384 | 9.54 | 9.22 | 1.035× | 9.44 | 9.06 | 1.042×
|
| 64 | 64 | 1 | 8 | 16384 | 20.32 | 20.32 | 1.000× | 20.42 | 20.42 |
1.000× ¹ |
| 64 | 64 | 1 | 32 | 16384 | 57.95 | 55.61 | 1.042× | 57.79 | 55.39 |
1.043× |
| 64 | 64 | 1 | 64 | 16384 | 109.57 | 104.70 | 1.046× | 109.02 | 104.29
| 1.045× |
| 64 | 64 | 1 | 128 | 16384 | 210.88 | 198.85 | 1.061× | 209.05 | 197.89
| 1.056× |
| 64 | 64 | 1 | 256 | 16384 | 400.96 | 382.14 | 1.049× | 401.69 | 380.89
| 1.055× |
| 64 | 64 | 1 | 8 | 65536 | 61.50 | 59.01 | 1.042× | 61.21 | 58.72 |
1.043× |
| 64 | 64 | 1 | 32 | 65536 | 202.40 | 192.38 | 1.052× | 201.37 | 192.09
| 1.048× |
| 64 | 64 | 1 | 128 | 65536 | 755.19 | 726.49 | 1.040× | 753.27 | 727.02
| 1.036× |
| 64 | 64 | 2 | 8 | 4096 | 12.67 | 11.04 | 1.148× | 12.58 | 10.98 |
1.146× |
| 64 | 64 | 2 | 64 | 4096 | 38.50 | 38.50 | 1.000× | 38.50 | 38.50 |
1.000× ¹ |
| 64 | 64 | 2 | 256 | 4096 | 123.70 | 115.30 | 1.073× | 124.48 | 115.49
| 1.078× |
| 64 | 64 | 2 | 1 | 16384 | 10.53 | 9.73 | 1.082× | 10.27 | 9.44 |
1.088× |
| 64 | 64 | 2 | 8 | 16384 | 22.72 | 22.72 | 1.000× | 22.56 | 22.56 |
1.000× ¹ |
| 64 | 64 | 2 | 32 | 16384 | 63.55 | 63.55 | 1.000× | 63.55 | 63.55 |
1.000× ¹ |
| 64 | 64 | 2 | 64 | 16384 | 118.30 | 111.49 | 1.061× | 117.89 | 111.01
| 1.062× |
| 64 | 64 | 2 | 128 | 16384 | 227.23 | 213.37 | 1.065× | 223.42 | 212.16
| 1.053× |
| 64 | 64 | 2 | 256 | 16384 | 430.27 | 411.98 | 1.044× | 428.09 | 409.60
| 1.045× |
| 64 | 64 | 2 | 8 | 65536 | 67.14 | 61.98 | 1.083× | 66.46 | 61.58 |
1.079× |
| 64 | 64 | 2 | 32 | 65536 | 217.53 | 206.24 | 1.055× | 215.45 | 204.57
| 1.053× |
| 64 | 64 | 2 | 128 | 65536 | 807.89 | 787.13 | 1.026× | 798.26 | 775.91
| 1.029× |
| 64 | 64 | 3 | 8 | 4096 | 14.40 | 11.94 | 1.206× | 14.40 | 11.84 |
1.216× |
| 64 | 64 | 3 | 64 | 4096 | 45.73 | 39.14 | 1.168× | 44.70 | 39.04 |
1.145× |
| 64 | 64 | 3 | 256 | 4096 | 149.02 | 149.06 | 1.000× | 153.63 | 153.76
| 0.999× ¹ |
| 64 | 64 | 3 | 1 | 16384 | 11.49 | 10.43 | 1.101× | 11.33 | 10.24 |
1.106× |
| 64 | 64 | 3 | 8 | 16384 | 26.46 | 23.49 | 1.127× | 26.05 | 23.17 |
1.124× |
| 64 | 64 | 3 | 32 | 16384 | 77.12 | 69.50 | 1.110× | 74.43 | 65.25 |
1.141× |
| 64 | 64 | 3 | 64 | 16384 | 143.87 | 143.87 | 1.000× | 147.71 | 147.77
| 1.000× ¹ |
| 64 | 64 | 3 | 128 | 16384 | 267.73 | 267.52 | 1.001× | 272.19 | 272.38
| 0.999× ¹ |
| 64 | 64 | 3 | 256 | 16384 | 525.15 | 525.05 | 1.000× | 512.22 | 512.15
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 65536 | 79.45 | 71.58 | 1.110× | 76.29 | 68.61 |
1.112× |
| 64 | 64 | 3 | 32 | 65536 | 257.74 | 257.95 | 0.999× | 261.40 | 261.15
| 1.001× ¹ |
| 64 | 64 | 3 | 128 | 65536 | 1024.88 | 1028.31 | 0.997× | 985.21 |
985.77 | 0.999× ¹ |
| 64 | 64 | 4 | 8 | 4096 | 14.75 | 11.84 | 1.246× | 14.59 | 11.81 |
1.236× |
| 64 | 64 | 4 | 64 | 4096 | 53.60 | 53.57 | 1.001× | 54.69 | 54.69 |
1.000× ¹ |
| 64 | 64 | 4 | 256 | 4096 | 192.48 | 189.79 | 1.014× | 188.22 | 185.38
| 1.015× |
| 64 | 64 | 4 | 1 | 16384 | 11.97 | 10.40 | 1.151× | 11.81 | 10.24 |
1.153× |
| 64 | 64 | 4 | 8 | 16384 | 32.67 | 32.67 | 1.000× | 32.61 | 32.61 |
1.000× ¹ |
| 64 | 64 | 4 | 32 | 16384 | 97.12 | 97.12 | 1.000× | 94.85 | 94.85 |
1.000× ¹ |
| 64 | 64 | 4 | 64 | 16384 | 185.52 | 183.84 | 1.009× | 181.76 | 179.97
| 1.010× |
| 64 | 64 | 4 | 128 | 16384 | 349.98 | 350.01 | 1.000× | 342.33 | 342.24
| 1.000× ¹ |
| 64 | 64 | 4 | 256 | 16384 | 685.63 | 686.97 | 0.998× | 664.67 | 664.38
| 1.000× ¹ |
| 64 | 64 | 4 | 8 | 65536 | 100.38 | 84.96 | 1.182× | 98.24 | 76.74 |
1.280× |
| 64 | 64 | 4 | 32 | 65536 | 338.27 | 338.20 | 1.000× | 330.88 | 330.85
| 1.000× ¹ |
| 64 | 64 | 4 | 128 | 65536 | 1362.85 | 1360.50 | 1.002× | 1313.33 |
1316.47 | 0.998× ¹ |
| 64 | 64 | 5 | 8 | 4096 | 17.22 | 13.79 | 1.248× | 17.02 | 13.63 |
1.249× |
| 64 | 64 | 5 | 64 | 4096 | 76.86 | 56.48 | 1.361× | 75.42 | 53.18 |
1.418× |
| 64 | 64 | 5 | 256 | 4096 | 249.12 | 249.34 | 0.999× | 255.18 | 255.10
| 1.000× ¹ |
| 64 | 64 | 5 | 1 | 16384 | 13.60 | 11.42 | 1.190× | 13.44 | 11.30 |
1.190× |
| 64 | 64 | 5 | 8 | 16384 | 41.06 | 31.14 | 1.319× | 40.80 | 30.98 |
1.317× |
| 64 | 64 | 5 | 32 | 16384 | 143.30 | 117.02 | 1.225× | 142.08 | 115.78
| 1.227× |
| 64 | 64 | 5 | 64 | 16384 | 269.92 | 218.30 | 1.236× | 266.65 | 219.04
| 1.217× |
| 64 | 64 | 5 | 128 | 16384 | 499.87 | 500.22 | 0.999× | 490.83 | 490.84
| 1.000× ¹ |
| 64 | 64 | 5 | 256 | 16384 | 936.36 | 935.58 | 1.001× | 916.38 | 916.57
| 1.000× ¹ |
| 64 | 64 | 5 | 8 | 65536 | 150.53 | 122.81 | 1.226× | 148.29 | 121.15 |
1.224× |
| 64 | 64 | 5 | 32 | 65536 | 554.87 | 554.43 | 1.001× | 549.05 | 548.86
| 1.000× ¹ |
| 64 | 64 | 5 | 128 | 65536 | 1912.56 | 1911.95 | 1.000× | 1875.51 |
1874.71 | 1.000× ¹ |
| 64 | 64 | 6 | 8 | 4096 | 17.34 | 13.82 | 1.255× | 17.18 | 13.63 |
1.261× |
| 64 | 64 | 6 | 64 | 4096 | 77.25 | 59.04 | 1.308× | 75.81 | 52.67 |
1.439× |
| 64 | 64 | 6 | 256 | 4096 | 278.49 | 278.49 | 1.000× | 273.66 | 273.69
| 1.000× ¹ |
| 64 | 64 | 6 | 1 | 16384 | 13.57 | 13.57 | 1.000× | 13.50 | 13.50 |
1.000× ¹ |
| 64 | 64 | 6 | 8 | 16384 | 41.82 | 30.91 | 1.353× | 41.09 | 30.59 |
1.343× |
| 64 | 64 | 6 | 32 | 16384 | 144.57 | 118.91 | 1.216× | 142.78 | 116.29
| 1.228× |
| 64 | 64 | 6 | 64 | 16384 | 270.59 | 270.46 | 1.000× | 266.72 | 266.72
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 16384 | 521.77 | 521.31 | 1.001× | 509.34 | 509.63
| 0.999× ¹ |
| 64 | 64 | 6 | 256 | 16384 | 1037.81 | 1043.24 | 0.995× | 1007.18 |
1002.94 | 1.004× ¹ |
| 64 | 64 | 6 | 8 | 65536 | 150.81 | 122.08 | 1.235× | 148.77 | 120.09 |
1.239× |
| 64 | 64 | 6 | 32 | 65536 | 537.83 | 537.88 | 1.000× | 532.19 | 532.43
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 65536 | 2074.33 | 2071.40 | 1.001× | 2003.39 |
2007.42 | 0.998× ¹ |

**RTX PRO 6000**

| heads | page | next_n | batch | context | shipped µs | new µs |
speedup | shipped µs | new µs | speedup |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 32 | 64 | 1 | 8 | 4096 | 14.40 | 14.40 | 1.000× | 14.43 | 14.43 |
1.000× ¹ |
| 32 | 64 | 1 | 64 | 4096 | 44.45 | 44.45 | 1.000× | 44.32 | 44.32 |
1.000× ¹ |
| 32 | 64 | 1 | 256 | 4096 | 145.09 | 132.06 | 1.099× | 145.41 | 132.22
| 1.100× |
| 32 | 64 | 1 | 1 | 16384 | 11.71 | 11.58 | 1.011× | 11.74 | 11.58 |
1.014× |
| 32 | 64 | 1 | 8 | 16384 | 27.23 | 27.23 | 1.000× | 27.23 | 27.23 |
1.000× ¹ |
| 32 | 64 | 1 | 32 | 16384 | 74.94 | 73.44 | 1.020× | 75.87 | 73.98 |
1.026× |
| 32 | 64 | 1 | 64 | 16384 | 141.50 | 128.48 | 1.101× | 142.02 | 129.28
| 1.099× |
| 32 | 64 | 1 | 128 | 16384 | 258.82 | 229.79 | 1.126× | 258.69 | 229.47
| 1.127× |
| 32 | 64 | 1 | 256 | 16384 | 462.08 | 432.16 | 1.069× | 460.51 | 430.72
| 1.069× |
| 32 | 64 | 1 | 8 | 65536 | 79.90 | 78.56 | 1.017× | 80.03 | 78.75 |
1.016× |
| 32 | 64 | 1 | 32 | 65536 | 252.16 | 223.33 | 1.129× | 251.52 | 222.69
| 1.129× |
| 32 | 64 | 1 | 128 | 65536 | 850.50 | 819.56 | 1.038× | 849.44 | 818.98
| 1.037× |
| 32 | 64 | 2 | 8 | 4096 | 14.78 | 14.79 | 1.000× | 14.69 | 14.69 |
1.000× ¹ |
| 32 | 64 | 2 | 64 | 4096 | 44.86 | 44.86 | 1.000× | 44.83 | 44.83 |
1.000× ¹ |
| 32 | 64 | 2 | 256 | 4096 | 148.13 | 136.67 | 1.084× | 147.71 | 136.64
| 1.081× |
| 32 | 64 | 2 | 1 | 16384 | 12.13 | 12.00 | 1.011× | 12.10 | 11.97 |
1.011× |
| 32 | 64 | 2 | 8 | 16384 | 27.42 | 27.42 | 1.000× | 27.58 | 27.58 |
1.000× ¹ |
| 32 | 64 | 2 | 32 | 16384 | 75.49 | 74.21 | 1.017× | 75.90 | 74.14 |
1.024× |
| 32 | 64 | 2 | 64 | 16384 | 143.46 | 132.74 | 1.081× | 142.98 | 132.83
| 1.076× |
| 32 | 64 | 2 | 128 | 16384 | 263.43 | 237.76 | 1.108× | 263.46 | 237.63
| 1.109× |
| 32 | 64 | 2 | 256 | 16384 | 473.70 | 446.18 | 1.062× | 473.25 | 446.72
| 1.059× |
| 32 | 64 | 2 | 8 | 65536 | 80.74 | 79.78 | 1.012× | 81.03 | 79.33 |
1.021× |
| 32 | 64 | 2 | 32 | 65536 | 255.91 | 230.53 | 1.110× | 256.00 | 230.40
| 1.111× |
| 32 | 64 | 2 | 128 | 65536 | 875.40 | 848.13 | 1.032× | 876.23 | 849.28
| 1.032× |
| 32 | 64 | 3 | 8 | 4096 | 15.17 | 15.17 | 1.000× | 15.14 | 15.14 |
1.000× ¹ |
| 32 | 64 | 3 | 64 | 4096 | 45.54 | 45.54 | 1.000× | 45.34 | 45.34 |
1.000× ¹ |
| 32 | 64 | 3 | 256 | 4096 | 149.31 | 140.42 | 1.063× | 150.08 | 140.51
| 1.068× |
| 32 | 64 | 3 | 1 | 16384 | 12.61 | 12.45 | 1.013× | 12.54 | 12.42 |
1.010× |
| 32 | 64 | 3 | 8 | 16384 | 27.74 | 27.74 | 1.000× | 27.71 | 27.71 |
1.000× ¹ |
| 32 | 64 | 3 | 32 | 16384 | 76.51 | 75.71 | 1.011× | 76.51 | 75.20 |
1.017× |
| 32 | 64 | 3 | 64 | 16384 | 144.83 | 136.54 | 1.061× | 144.96 | 136.64
| 1.061× |
| 32 | 64 | 3 | 128 | 16384 | 269.57 | 245.09 | 1.100× | 269.98 | 245.82
| 1.098× |
| 32 | 64 | 3 | 256 | 16384 | 487.23 | 461.63 | 1.055× | 488.03 | 462.47
| 1.055× |
| 32 | 64 | 3 | 8 | 65536 | 80.70 | 79.42 | 1.016× | 81.09 | 79.81 |
1.016× |
| 32 | 64 | 3 | 32 | 65536 | 261.19 | 237.73 | 1.099× | 260.83 | 236.99
| 1.101× |
| 32 | 64 | 3 | 128 | 65536 | 897.73 | 873.54 | 1.028× | 899.36 | 873.86
| 1.029× |
| 32 | 64 | 4 | 8 | 4096 | 15.20 | 15.10 | 1.006× | 15.17 | 15.07 |
1.006× |
| 32 | 64 | 4 | 64 | 4096 | 46.50 | 46.50 | 1.000× | 45.89 | 45.89 |
1.000× ¹ |
| 32 | 64 | 4 | 256 | 4096 | 153.79 | 145.34 | 1.058× | 155.17 | 146.27
| 1.061× |
| 32 | 64 | 4 | 1 | 16384 | 13.47 | 13.34 | 1.010× | 13.47 | 13.34 |
1.010× |
| 32 | 64 | 4 | 8 | 16384 | 27.84 | 27.84 | 1.000× | 27.94 | 27.94 |
1.000× ¹ |
| 32 | 64 | 4 | 32 | 16384 | 77.92 | 77.92 | 1.000× | 77.57 | 77.57 |
1.000× ¹ |
| 32 | 64 | 4 | 64 | 16384 | 147.36 | 140.64 | 1.048× | 147.65 | 140.38
| 1.052× |
| 32 | 64 | 4 | 128 | 16384 | 276.07 | 253.60 | 1.089× | 275.94 | 252.67
| 1.092× |
| 32 | 64 | 4 | 256 | 16384 | 500.36 | 476.19 | 1.051× | 498.40 | 475.11
| 1.049× |
| 32 | 64 | 4 | 8 | 65536 | 82.46 | 80.93 | 1.019× | 81.89 | 80.06 |
1.023× |
| 32 | 64 | 4 | 32 | 65536 | 266.05 | 243.11 | 1.094× | 266.37 | 244.38
| 1.090× |
| 32 | 64 | 4 | 128 | 65536 | 924.36 | 924.23 | 1.000× | 922.47 | 922.53
| 1.000× ¹ |
| 32 | 64 | 5 | 8 | 4096 | 16.06 | 15.84 | 1.014× | 16.06 | 15.84 |
1.014× |
| 32 | 64 | 5 | 64 | 4096 | 47.07 | 47.07 | 1.000× | 47.17 | 47.17 |
1.000× ¹ |
| 32 | 64 | 5 | 256 | 4096 | 159.87 | 159.87 | 1.000× | 160.10 | 160.03
| 1.000× ¹ |
| 32 | 64 | 5 | 1 | 16384 | 13.79 | 13.47 | 1.024× | 13.73 | 13.50 |
1.017× |
| 32 | 64 | 5 | 8 | 16384 | 28.48 | 28.48 | 1.000× | 28.22 | 28.22 |
1.000× ¹ |
| 32 | 64 | 5 | 32 | 16384 | 79.36 | 77.76 | 1.021× | 79.62 | 77.98 |
1.021× |
| 32 | 64 | 5 | 64 | 16384 | 152.48 | 152.48 | 1.000× | 151.55 | 151.52
| 1.000× ¹ |
| 32 | 64 | 5 | 128 | 16384 | 283.75 | 262.47 | 1.081× | 282.69 | 260.61
| 1.085× |
| 32 | 64 | 5 | 256 | 16384 | 514.69 | 492.58 | 1.045× | 515.49 | 492.87
| 1.046× |
| 32 | 64 | 5 | 8 | 65536 | 84.19 | 82.53 | 1.020× | 83.01 | 81.12 |
1.023× |
| 32 | 64 | 5 | 32 | 65536 | 270.88 | 270.88 | 1.000× | 272.48 | 272.51
| 1.000× ¹ |
| 32 | 64 | 5 | 128 | 65536 | 951.11 | 951.20 | 1.000× | 948.26 | 948.55
| 1.000× ¹ |
| 32 | 64 | 6 | 8 | 4096 | 16.00 | 15.90 | 1.006× | 16.13 | 15.94 |
1.012× |
| 32 | 64 | 6 | 64 | 4096 | 49.02 | 48.32 | 1.015× | 48.96 | 48.22 |
1.015× |
| 32 | 64 | 6 | 256 | 4096 | 164.99 | 156.19 | 1.056× | 163.81 | 155.81
| 1.051× |
| 32 | 64 | 6 | 1 | 16384 | 13.73 | 13.50 | 1.017× | 13.66 | 13.44 |
1.017× |
| 32 | 64 | 6 | 8 | 16384 | 29.41 | 28.64 | 1.027× | 29.31 | 28.51 |
1.028× |
| 32 | 64 | 6 | 32 | 16384 | 81.44 | 80.61 | 1.010× | 81.63 | 80.00 |
1.020× |
| 32 | 64 | 6 | 64 | 16384 | 155.30 | 149.15 | 1.041× | 155.91 | 149.38
| 1.044× |
| 32 | 64 | 6 | 128 | 16384 | 290.27 | 268.42 | 1.081× | 290.66 | 268.90
| 1.081× |
| 32 | 64 | 6 | 256 | 16384 | 528.58 | 508.42 | 1.040× | 528.42 | 508.80
| 1.039× |
| 32 | 64 | 6 | 8 | 65536 | 85.66 | 84.29 | 1.016× | 87.49 | 85.79 |
1.020× |
| 32 | 64 | 6 | 32 | 65536 | 279.62 | 259.70 | 1.077× | 278.50 | 259.20
| 1.074× |
| 32 | 64 | 6 | 128 | 65536 | 972.13 | 972.28 | 1.000× | 977.38 | 977.22
| 1.000× ¹ |
| 32 | 128 | 1 | 8 | 4096 | 14.40 | 14.37 | 1.002× | 14.43 | 14.43 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 4096 | 44.96 | 44.96 | 1.000× | 44.67 | 44.67 |
1.000× ¹ |
| 32 | 128 | 1 | 256 | 4096 | 145.28 | 131.91 | 1.101× | 145.06 | 131.97
| 1.099× |
| 32 | 128 | 1 | 1 | 16384 | 11.75 | 11.75 | 1.000× | 11.78 | 11.75 |
1.003× ¹ |
| 32 | 128 | 1 | 8 | 16384 | 27.23 | 27.23 | 1.000× | 27.42 | 27.42 |
1.000× ¹ |
| 32 | 128 | 1 | 32 | 16384 | 76.26 | 76.26 | 1.000× | 75.62 | 75.62 |
1.000× ¹ |
| 32 | 128 | 1 | 64 | 16384 | 141.54 | 128.64 | 1.100× | 141.60 | 128.77
| 1.100× |
| 32 | 128 | 1 | 128 | 16384 | 258.53 | 229.34 | 1.127× | 257.95 |
228.93 | 1.127× |
| 32 | 128 | 1 | 256 | 16384 | 460.29 | 430.63 | 1.069× | 460.23 |
430.53 | 1.069× |
| 32 | 128 | 1 | 8 | 65536 | 80.10 | 78.62 | 1.019× | 79.94 | 78.40 |
1.020× |
| 32 | 128 | 1 | 32 | 65536 | 251.81 | 222.94 | 1.129× | 251.11 | 222.05
| 1.131× |
| 32 | 128 | 1 | 128 | 65536 | 848.16 | 817.54 | 1.037× | 849.03 |
816.60 | 1.040× |
| 32 | 128 | 2 | 8 | 4096 | 14.79 | 14.81 | 0.998× | 14.82 | 14.82 |
1.000× ¹ |
| 32 | 128 | 2 | 64 | 4096 | 45.41 | 45.38 | 1.001× | 44.99 | 44.99 |
1.000× ¹ |
| 32 | 128 | 2 | 256 | 4096 | 147.39 | 136.61 | 1.079× | 147.58 | 136.35
| 1.082× |
| 32 | 128 | 2 | 1 | 16384 | 12.16 | 12.06 | 1.008× | 12.13 | 11.94 |
1.016× |
| 32 | 128 | 2 | 8 | 16384 | 27.55 | 27.55 | 1.000× | 27.46 | 27.46 |
1.000× ¹ |
| 32 | 128 | 2 | 32 | 16384 | 75.81 | 75.81 | 1.000× | 75.49 | 75.49 |
1.000× ¹ |
| 32 | 128 | 2 | 64 | 16384 | 142.69 | 132.70 | 1.075× | 142.30 | 131.91
| 1.079× |
| 32 | 128 | 2 | 128 | 16384 | 263.39 | 237.47 | 1.109× | 263.57 |
237.54 | 1.110× |
| 32 | 128 | 2 | 256 | 16384 | 472.64 | 445.54 | 1.061× | 472.48 |
445.76 | 1.060× |
| 32 | 128 | 2 | 8 | 65536 | 80.58 | 79.62 | 1.012× | 80.23 | 79.33 |
1.011× |
| 32 | 128 | 2 | 32 | 65536 | 255.01 | 229.28 | 1.112× | 255.36 | 229.89
| 1.111× |
| 32 | 128 | 2 | 128 | 65536 | 874.37 | 846.72 | 1.033× | 875.91 |
847.57 | 1.033× |
| 32 | 128 | 3 | 8 | 4096 | 15.23 | 15.23 | 1.000× | 15.23 | 15.23 |
1.000× ¹ |
| 32 | 128 | 3 | 64 | 4096 | 45.54 | 45.54 | 1.000× | 45.66 | 45.66 |
1.000× ¹ |
| 32 | 128 | 3 | 256 | 4096 | 150.59 | 141.54 | 1.064× | 150.37 | 141.31
| 1.064× |
| 32 | 128 | 3 | 1 | 16384 | 12.61 | 12.61 | 1.000× | 12.64 | 12.61 |
1.003× ¹ |
| 32 | 128 | 3 | 8 | 16384 | 27.81 | 27.81 | 1.000× | 27.58 | 27.58 |
1.000× ¹ |
| 32 | 128 | 3 | 32 | 16384 | 76.55 | 75.10 | 1.019× | 76.16 | 75.04 |
1.015× |
| 32 | 128 | 3 | 64 | 16384 | 144.74 | 136.86 | 1.058× | 143.91 | 136.61
| 1.053× |
| 32 | 128 | 3 | 128 | 16384 | 269.60 | 244.29 | 1.104× | 269.38 |
245.34 | 1.098× |
| 32 | 128 | 3 | 256 | 16384 | 487.20 | 461.70 | 1.055× | 486.26 |
460.71 | 1.055× |
| 32 | 128 | 3 | 8 | 65536 | 81.12 | 79.91 | 1.015× | 81.31 | 80.06 |
1.016× |
| 32 | 128 | 3 | 32 | 65536 | 260.42 | 236.71 | 1.100× | 260.32 | 236.77
| 1.099× |
| 32 | 128 | 3 | 128 | 65536 | 894.50 | 869.80 | 1.028× | 897.83 |
872.92 | 1.029× |
| 32 | 128 | 4 | 8 | 4096 | 15.17 | 15.17 | 1.000× | 15.14 | 15.14 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 4096 | 46.30 | 46.30 | 1.000× | 46.02 | 46.02 |
1.000× ¹ |
| 32 | 128 | 4 | 256 | 4096 | 154.72 | 146.43 | 1.057× | 154.47 | 146.24
| 1.056× |
| 32 | 128 | 4 | 1 | 16384 | 13.54 | 13.54 | 1.000× | 13.47 | 13.47 |
1.000× ¹ |
| 32 | 128 | 4 | 8 | 16384 | 28.03 | 28.03 | 1.000× | 28.06 | 28.06 |
1.000× ¹ |
| 32 | 128 | 4 | 32 | 16384 | 77.47 | 77.47 | 1.000× | 77.66 | 77.63 |
1.000× ¹ |
| 32 | 128 | 4 | 64 | 16384 | 148.16 | 141.28 | 1.049× | 146.15 | 140.45
| 1.041× |
| 32 | 128 | 4 | 128 | 16384 | 276.00 | 252.42 | 1.093× | 275.42 |
252.59 | 1.090× |
| 32 | 128 | 4 | 256 | 16384 | 499.17 | 475.51 | 1.050× | 499.33 |
474.75 | 1.052× |
| 32 | 128 | 4 | 8 | 65536 | 81.47 | 80.00 | 1.018× | 81.66 | 79.94 |
1.022× |
| 32 | 128 | 4 | 32 | 65536 | 266.15 | 244.26 | 1.090× | 266.34 | 244.19
| 1.091× |
| 32 | 128 | 4 | 128 | 65536 | 922.37 | 900.10 | 1.025× | 921.41 |
898.50 | 1.026× |
| 32 | 128 | 5 | 8 | 4096 | 16.10 | 15.84 | 1.016× | 16.00 | 15.81 |
1.012× |
| 32 | 128 | 5 | 64 | 4096 | 47.01 | 46.98 | 1.001× | 46.72 | 46.72 |
1.000× ¹ |
| 32 | 128 | 5 | 256 | 4096 | 160.26 | 160.26 | 1.000× | 159.30 | 159.30
| 1.000× ¹ |
| 32 | 128 | 5 | 1 | 16384 | 13.66 | 13.41 | 1.019× | 13.67 | 13.41 |
1.019× |
| 32 | 128 | 5 | 8 | 16384 | 28.35 | 28.19 | 1.006× | 28.70 | 28.48 |
1.008× |
| 32 | 128 | 5 | 32 | 16384 | 78.75 | 78.75 | 1.000× | 79.81 | 79.81 |
1.000× ¹ |
| 32 | 128 | 5 | 64 | 16384 | 152.10 | 152.10 | 1.000× | 152.42 | 152.42
| 1.000× ¹ |
| 32 | 128 | 5 | 128 | 16384 | 282.50 | 282.50 | 1.000× | 283.36 |
283.42 | 1.000× ¹ |
| 32 | 128 | 5 | 256 | 16384 | 513.41 | 490.72 | 1.046× | 514.56 |
491.97 | 1.046× |
| 32 | 128 | 5 | 8 | 65536 | 85.44 | 83.94 | 1.018× | 85.38 | 83.27 |
1.025× |
| 32 | 128 | 5 | 32 | 65536 | 272.26 | 272.29 | 1.000× | 271.17 | 271.14
| 1.000× ¹ |
| 32 | 128 | 5 | 128 | 65536 | 945.03 | 945.03 | 1.000× | 945.09 |
945.16 | 1.000× ¹ |
| 32 | 128 | 6 | 8 | 4096 | 16.13 | 15.94 | 1.012× | 16.06 | 15.90 |
1.010× |
| 32 | 128 | 6 | 64 | 4096 | 49.22 | 48.48 | 1.015× | 48.48 | 47.91 |
1.012× |
| 32 | 128 | 6 | 256 | 4096 | 164.74 | 156.16 | 1.055× | 165.09 | 156.54
| 1.055× |
| 32 | 128 | 6 | 1 | 16384 | 13.60 | 13.44 | 1.012× | 13.70 | 13.50 |
1.014× |
| 32 | 128 | 6 | 8 | 16384 | 29.15 | 28.45 | 1.025× | 29.41 | 28.64 |
1.027× |
| 32 | 128 | 6 | 32 | 16384 | 82.11 | 81.09 | 1.013× | 82.53 | 80.96 |
1.019× |
| 32 | 128 | 6 | 64 | 16384 | 156.45 | 149.86 | 1.044× | 156.77 | 149.82
| 1.046× |
| 32 | 128 | 6 | 128 | 16384 | 289.95 | 270.72 | 1.071× | 289.86 |
270.47 | 1.072× |
| 32 | 128 | 6 | 256 | 16384 | 529.60 | 529.54 | 1.000× | 528.83 |
528.84 | 1.000× ¹ |
| 32 | 128 | 6 | 8 | 65536 | 85.92 | 84.42 | 1.018× | 87.68 | 86.62 |
1.012× |
| 32 | 128 | 6 | 32 | 65536 | 278.50 | 258.37 | 1.078× | 278.34 | 257.95
| 1.079× |
| 32 | 128 | 6 | 128 | 65536 | 973.38 | 973.45 | 1.000× | 973.48 |
973.41 | 1.000× ¹ |
| 64 | 64 | 1 | 8 | 4096 | 14.59 | 14.59 | 1.000× | 14.53 | 14.53 |
1.000× ¹ |
| 64 | 64 | 1 | 64 | 4096 | 45.31 | 45.31 | 1.000× | 45.03 | 45.06 |
0.999× ¹ |
| 64 | 64 | 1 | 256 | 4096 | 146.98 | 133.41 | 1.102× | 147.17 | 133.34
| 1.104× |
| 64 | 64 | 1 | 1 | 16384 | 12.00 | 11.87 | 1.011× | 12.00 | 11.81 |
1.016× |
| 64 | 64 | 1 | 8 | 16384 | 27.20 | 27.20 | 1.000× | 27.55 | 27.55 |
1.000× ¹ |
| 64 | 64 | 1 | 32 | 16384 | 76.19 | 74.59 | 1.021× | 75.58 | 74.24 |
1.018× |
| 64 | 64 | 1 | 64 | 16384 | 142.27 | 129.44 | 1.099× | 142.43 | 129.70
| 1.098× |
| 64 | 64 | 1 | 128 | 16384 | 260.23 | 231.78 | 1.123× | 260.22 | 231.39
| 1.125× |
| 64 | 64 | 1 | 256 | 16384 | 463.78 | 433.15 | 1.071× | 464.86 | 434.95
| 1.069× |
| 64 | 64 | 1 | 8 | 65536 | 80.45 | 78.94 | 1.019× | 80.64 | 79.01 |
1.021× |
| 64 | 64 | 1 | 32 | 65536 | 252.55 | 223.49 | 1.130× | 252.90 | 224.48
| 1.127× |
| 64 | 64 | 1 | 128 | 65536 | 853.97 | 824.20 | 1.036× | 854.50 | 824.29
| 1.037× |
| 64 | 64 | 2 | 8 | 4096 | 15.39 | 15.14 | 1.017× | 15.52 | 15.20 |
1.021× |
| 64 | 64 | 2 | 64 | 4096 | 45.79 | 45.79 | 1.000× | 46.27 | 46.30 |
0.999× ¹ |
| 64 | 64 | 2 | 256 | 4096 | 152.16 | 139.87 | 1.088× | 152.13 | 140.13
| 1.086× |
| 64 | 64 | 2 | 1 | 16384 | 12.61 | 12.35 | 1.021× | 12.61 | 12.42 |
1.015× |
| 64 | 64 | 2 | 8 | 16384 | 28.10 | 28.10 | 1.000× | 27.94 | 27.94 |
1.000× ¹ |
| 64 | 64 | 2 | 32 | 16384 | 77.34 | 77.34 | 1.000× | 77.12 | 77.12 |
1.000× ¹ |
| 64 | 64 | 2 | 64 | 16384 | 145.83 | 135.52 | 1.076× | 145.63 | 135.20
| 1.077× |
| 64 | 64 | 2 | 128 | 16384 | 268.00 | 241.38 | 1.110× | 267.65 | 240.83
| 1.111× |
| 64 | 64 | 2 | 256 | 16384 | 479.75 | 451.62 | 1.062× | 481.70 | 452.90
| 1.064× |
| 64 | 64 | 2 | 8 | 65536 | 81.44 | 79.71 | 1.022× | 81.15 | 79.27 |
1.024× |
| 64 | 64 | 2 | 32 | 65536 | 258.56 | 232.74 | 1.111× | 258.78 | 232.86
| 1.111× |
| 64 | 64 | 2 | 128 | 65536 | 883.14 | 856.45 | 1.031× | 882.34 | 855.75
| 1.031× |
| 64 | 64 | 3 | 8 | 4096 | 15.87 | 15.74 | 1.008× | 15.87 | 15.62 |
1.016× |
| 64 | 64 | 3 | 64 | 4096 | 48.42 | 47.81 | 1.013× | 48.35 | 47.74 |
1.013× |
| 64 | 64 | 3 | 256 | 4096 | 160.58 | 160.58 | 1.000× | 158.78 | 158.75
| 1.000× ¹ |
| 64 | 64 | 3 | 1 | 16384 | 13.31 | 12.99 | 1.025× | 13.28 | 12.99 |
1.022× |
| 64 | 64 | 3 | 8 | 16384 | 28.93 | 28.19 | 1.026× | 28.80 | 28.22 |
1.020× |
| 64 | 64 | 3 | 32 | 16384 | 79.36 | 77.60 | 1.023× | 79.23 | 77.63 |
1.021× |
| 64 | 64 | 3 | 64 | 16384 | 150.46 | 150.46 | 1.000× | 151.71 | 151.78
| 1.000× ¹ |
| 64 | 64 | 3 | 128 | 16384 | 278.53 | 278.50 | 1.000× | 277.98 | 278.02
| 1.000× ¹ |
| 64 | 64 | 3 | 256 | 16384 | 501.06 | 501.31 | 0.999× | 503.39 | 503.59
| 1.000× ¹ |
| 64 | 64 | 3 | 8 | 65536 | 84.03 | 82.08 | 1.024× | 83.55 | 82.30 |
1.015× |
| 64 | 64 | 3 | 32 | 65536 | 268.71 | 268.74 | 1.000× | 269.30 | 269.28
| 1.000× ¹ |
| 64 | 64 | 3 | 128 | 65536 | 915.30 | 914.98 | 1.000× | 914.31 | 914.24
| 1.000× ¹ |
| 64 | 64 | 4 | 8 | 4096 | 16.03 | 15.68 | 1.022× | 15.97 | 15.68 |
1.018× |
| 64 | 64 | 4 | 64 | 4096 | 50.78 | 50.78 | 1.000× | 50.85 | 50.85 |
1.000× ¹ |
| 64 | 64 | 4 | 256 | 4096 | 169.02 | 156.77 | 1.078× | 169.41 | 156.51
| 1.082× |
| 64 | 64 | 4 | 1 | 16384 | 14.21 | 13.95 | 1.018× | 14.21 | 13.98 |
1.016× |
| 64 | 64 | 4 | 8 | 16384 | 31.14 | 31.14 | 1.000× | 30.59 | 30.59 |
1.000× ¹ |
| 64 | 64 | 4 | 32 | 16384 | 83.33 | 83.33 | 1.000× | 83.65 | 83.68 |
1.000× ¹ |
| 64 | 64 | 4 | 64 | 16384 | 160.16 | 148.80 | 1.076× | 155.94 | 146.59
| 1.064× |
| 64 | 64 | 4 | 128 | 16384 | 289.15 | 289.09 | 1.000× | 290.08 | 290.02
| 1.000× ¹ |
| 64 | 64 | 4 | 256 | 16384 | 519.49 | 519.75 | 1.000× | 519.83 | 519.78
| 1.000× ¹ |
| 64 | 64 | 4 | 8 | 65536 | 87.30 | 85.34 | 1.023× | 87.49 | 85.44 |
1.024× |
| 64 | 64 | 4 | 32 | 65536 | 278.24 | 278.11 | 1.000× | 278.14 | 278.14
| 1.000× ¹ |
| 64 | 64 | 4 | 128 | 65536 | 943.65 | 944.13 | 0.999× | 943.83 | 943.56
| 1.000× ¹ |
| 64 | 64 | 5 | 8 | 4096 | 17.82 | 16.93 | 1.053× | 17.66 | 16.99 |
1.039× |
| 64 | 64 | 5 | 64 | 4096 | 59.39 | 54.37 | 1.092× | 59.81 | 54.88 |
1.090× |
| 64 | 64 | 5 | 256 | 4096 | 256.13 | 256.10 | 1.000× | 255.33 | 255.36
| 1.000× ¹ |
| 64 | 64 | 5 | 1 | 16384 | 14.69 | 14.53 | 1.011× | 14.75 | 14.62 |
1.009× |
| 64 | 64 | 5 | 8 | 16384 | 36.29 | 34.34 | 1.057× | 35.81 | 34.02 |
1.053× |
| 64 | 64 | 5 | 32 | 16384 | 113.34 | 87.84 | 1.290× | 113.76 | 87.46 |
1.301× |
| 64 | 64 | 5 | 64 | 16384 | 219.17 | 159.81 | 1.371× | 218.47 | 159.59
| 1.369× |
| 64 | 64 | 5 | 128 | 16384 | 416.00 | 415.91 | 1.000× | 416.55 | 416.71
| 1.000× ¹ |
| 64 | 64 | 5 | 256 | 16384 | 919.40 | 919.62 | 1.000× | 920.55 | 920.58
| 1.000× ¹ |
| 64 | 64 | 5 | 8 | 65536 | 124.67 | 92.61 | 1.346× | 125.12 | 92.86 |
1.347× |
| 64 | 64 | 5 | 32 | 65536 | 509.67 | 509.67 | 1.000× | 508.80 | 508.67
| 1.000× ¹ |
| 64 | 64 | 5 | 128 | 65536 | 1741.74 | 1741.29 | 1.000× | 1736.49 |
1736.84 | 1.000× ¹ |
| 64 | 64 | 6 | 8 | 4096 | 17.82 | 17.38 | 1.026× | 17.89 | 17.41 |
1.028× |
| 64 | 64 | 6 | 64 | 4096 | 60.93 | 56.83 | 1.072× | 60.74 | 56.29 |
1.079× |
| 64 | 64 | 6 | 256 | 4096 | 262.40 | 262.37 | 1.000× | 261.70 | 261.76
| 1.000× ¹ |
| 64 | 64 | 6 | 1 | 16384 | 14.72 | 14.72 | 1.000× | 14.82 | 14.82 |
1.000× ¹ |
| 64 | 64 | 6 | 8 | 16384 | 36.00 | 32.70 | 1.101× | 35.87 | 32.64 |
1.099× |
| 64 | 64 | 6 | 32 | 16384 | 113.47 | 93.98 | 1.207× | 113.50 | 94.27 |
1.204× |
| 64 | 64 | 6 | 64 | 16384 | 216.54 | 216.58 | 1.000× | 216.29 | 216.32
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 16384 | 420.64 | 420.67 | 1.000× | 419.94 | 420.10
| 1.000× ¹ |
| 64 | 64 | 6 | 256 | 16384 | 933.09 | 933.06 | 1.000× | 930.79 | 930.82
| 1.000× ¹ |
| 64 | 64 | 6 | 8 | 65536 | 124.19 | 96.35 | 1.289× | 124.48 | 95.81 |
1.299× |
| 64 | 64 | 6 | 32 | 65536 | 519.95 | 520.16 | 1.000× | 518.60 | 518.59
| 1.000× ¹ |
| 64 | 64 | 6 | 128 | 65536 | 1735.47 | 1735.00 | 1.000× | 1735.66 |
1735.80 | 1.000× ¹ |

The kernel's other Cake variants are the dense FP4 and FP8
lightning-indexer logits and the paged FP8 MQA logits for SM100a/SM103a
(`deepgemm_dense_mqa`), while this paged FP8 package ships on sm_120a
only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* SM120 paged MQA logits can select tuned routes for supported GPUs when
device, CTA budget, batch size, and context hint match; other cases use
the default route.
* Dynamic routes use a private scheduling buffer. Supplied schedule
metadata is validated but not modified.
* Benchmarks accept context hints and report the selected route and
schedule type.
* **Documentation**
* Expanded guidance on device-specific route selection, scheduling
behavior, and benchmark options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [cf14a96](https://github.com/flashinfer-ai/flashinfer/commit/cf14a964ff46f9fa209d5eb370da5792e3ad6291)

- **作者**: eigen
- **时间**: 2026-10-29T18:05:52Z
- **提交信息**: perf(cake_minimax_h3): plan-dependent overlap width for SM120 NVFP4 varlen attention (#7854)

This PR changes the MiniMax-H3 non-causal packed-varlen NVFP4 attention
kernel on sm_120a. The kernel has two NVFP4 forms. The default form is
`minimax_h3_sm120_varlen_attention_nvfp4`, which is compensated. The
second form is `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`, which
is uncompensated. This PR changes both forms on the RTX 5090 and the RTX
PRO 6000.

The change is host-side only. Overlapped plans run the pre-processing
producers on a set of tail CTAs beside the attention. On FlashInfer
main, the number of these CTAs (the producer width) is fixed per GPU. It
is 42 on the RTX 5090 (170 SMs) and 46 on the RTX PRO 6000 (188 SMs).
Long light plans on the RTX 5090 use 64. This PR picks the width from
the attention-weighted mean segment length of the plan. This length is m
= sum of squared segment lengths / tokens. Plans with short or
mid-length segments get more producers. On the RTX 5090, the width goes
from 42 to 64, 56 or 50. On the RTX PRO 6000, it goes from 46 to 80, 64
or 56. On the RTX 5090, long light plans go from 64 to 48. The kernel
programs do not change. Only the width that the host passes changes. In
both forms, outputs are bitwise equal to FlashInfer main.

The speedup is in the plans whose width changes. On the RTX 5090, 51
plans change: 23 in the default form and 28 in the uncompensated form.
Plans whose width rises from 42 run 1.027x-1.347x faster. Long light
plans (64 -> 48) run 1.004x-1.052x faster. One RTX 5090 plan, vl_24x2150
in the default form at 1.005x, is within run-to-run noise. The table
marks it "(within noise)", and we do not claim a speedup for it. On the
RTX PRO 6000, 30 plans change, 15 per form. All of them run faster, by
1.020x-1.301x. Each GPU has 13 representative shapes in both forms. All
of them launch exactly as on FlashInfer main. The tables mark them
"(unchanged)" and show them to confirm that they do not change.

The baseline is the previous Cake version of the same op, which is
FlashInfer main. Latency is the median GPU time per call of the whole
op, with cold L2. Speedup = FlashInfer main / this PR.

**Representative shapes: NVIDIA GeForce RTX 5090 (sm_120a, 170 SMs),
CUDA 13.4.92**

| shape | cu_seqlens | default main us | default PR us | speedup |
nodelta main us | nodelta PR us | speedup |
|---|---|---|---|---|---|---|---|
| 33472 x 56 x 128 | (0, 33472) | 36761.93 | 36769.55 | 1.000x
(unchanged) | 32534.28 | 32531.00 | 1.000x (unchanged) |
| 38592 x 56 x 128 | (0, 38592) | 49201.28 | 49206.37 | 1.000x
(unchanged) | 43254.06 | 43311.73 | 0.999x (unchanged) |
| 48768 x 56 x 128 | (0, 48768) | 79762.98 | 79813.30 | 0.999x
(unchanged) | 70079.49 | 70020.59 | 1.001x (unchanged) |
| 58944 x 56 x 128 | (0, 58944) | 118317.53 | 118367.80 | 1.000x
(unchanged) | 106698.06 | 106832.02 | 0.999x (unchanged) |
| 74240 x 56 x 128 | (0, 74240) | 185207.72 | 185172.06 | 1.000x
(unchanged) | 168155.75 | 168127.28 | 1.000x (unchanged) |
| 109952 x 56 x 128 | (0, 109952) | 405862.85 | 406094.49 | 0.999x
(unchanged) | 369313.76 | 369290.62 | 1.000x (unchanged) |
| 38531 x 56 x 128 | (0, 38531) | 50323.17 | 50326.80 | 1.000x
(unchanged) | 45435.43 | 45461.63 | 0.999x (unchanged) |
| 38629 x 56 x 128 | (0, 38629) | 50324.08 | 50363.61 | 0.999x
(unchanged) | 45539.81 | 45545.18 | 1.000x (unchanged) |
| 109952 x 56 x 128 | (0, 109901, 109952) | 405673.67 | 405565.96 |
1.000x (unchanged) | 368876.97 | 368923.58 | 1.000x (unchanged) |
| 33472 x 56 x 128 | (0, 8368, 16736, 25104, 33472) | 10330.94 |
10325.48 | 1.001x (unchanged) | 9396.99 | 9403.77 | 0.999x (unchanged) |
| 4824 x 56 x 128 | (0, 257, 4567, 4824) | 775.42 | 774.47 | 1.001x
(unchanged) | 714.63 | 713.72 | 1.001x (unchanged) |
| 500 x 56 x 128 | (0, 0, 129, 129, 500) | 38.38 | 38.50 | 0.997x
(unchanged) | 36.96 | 37.06 | 0.997x (unchanged) |
| 4096 x 56 x 128 | (0, 4096) | 673.67 | 673.27 | 1.001x (unchanged) |
612.09 | 612.76 | 0.999x (unchanged) |

**Representative shapes: NVIDIA RTX PRO 6000 Blackwell Server Edition
(sm_120a, 188 SMs), CUDA 13.4.92**

| shape | cu_seqlens | default main us | default PR us | speedup |
nodelta main us | nodelta PR us | speedup |
|---|---|---|---|---|---|---|---|
| 33472 x 56 x 128 | (0, 33472) | 33112.67 | 33105.91 | 1.000x
(unchanged) | 29967.27 | 29943.09 | 1.001x (unchanged) |
| 38592 x 56 x 128 | (0, 38592) | 43997.75 | 44003.11 | 1.000x
(unchanged) | 40070.90 | 40097.38 | 0.999x (unchanged) |
| 48768 x 56 x 128 | (0, 48768) | 69662.80 | 69599.79 | 1.001x
(unchanged) | 63355.50 | 63469.32 | 0.998x (unchanged) |
| 58944 x 56 x 128 | (0, 58944) | 101660.64 | 101702.02 | 1.000x
(unchanged) | 92485.55 | 92279.18 | 1.002x (unchanged) |
| 74240 x 56 x 128 | (0, 74240) | 160258.64 | 160259.73 | 1.000x
(unchanged) | 145569.08 | 145493.61 | 1.001x (unchanged) |
| 109952 x 56 x 128 | (0, 109952) | 349615.25 | 349639.85 | 1.000x
(unchanged) | 316449.66 | 316393.34 | 1.000x (unchanged) |
| 38531 x 56 x 128 | (0, 38531) | 43959.85 | 43947.84 | 1.000x
(unchanged) | 40098.59 | 40115.09 | 1.000x (unchanged) |
| 38629 x 56 x 128 | (0, 38629) | 44015.53 | 43964.92 | 1.001x
(unchanged) | 40125.53 | 40124.48 | 1.000x (unchanged) |
| 109952 x 56 x 128 | (0, 109901, 109952) | 349615.96 | 349680.22 |
1.000x (unchanged) | 316329.40 | 316227.53 | 1.000x (unchanged) |
| 33472 x 56 x 128 | (0, 8368, 16736, 25104, 33472) | 9205.44 | 9202.26
| 1.000x (unchanged) | 8449.13 | 8454.20 | 0.999x (unchanged) |
| 4824 x 56 x 128 | (0, 257, 4567, 4824) | 735.87 | 735.55 | 1.000x
(unchanged) | 672.83 | 672.50 | 1.000x (unchanged) |
| 500 x 56 x 128 | (0, 0, 129, 129, 500) | 51.15 | 50.96 | 1.004x
(unchanged) | 49.15 | 49.01 | 1.003x (unchanged) |
| 4096 x 56 x 128 | (0, 4096) | 637.28 | 636.43 | 1.001x (unchanged) |
581.87 | 580.32 | 1.003x (unchanged) |

**Changed plans: NVIDIA GeForce RTX 5090 (sm_120a, 170 SMs), CUDA
13.4.92**

Op `minimax_h3_sm120_varlen_attention_nvfp4`:

| plan | segment lengths (m) | width main -> PR | main us | PR us |
speedup |
|---|---|---|---|---|---|
| v_32x256 | 32 x 256 (m 256) | 42 -> 64 | 617.21 | 460.35 | 1.341x |
| v_6x700 | 6 x 700 (m 700) | 42 -> 64 | 359.79 | 299.21 | 1.202x |
| v_tiny975 | 1000, 950 (m 976) | 42 -> 64 | 202.89 | 180.54 | 1.124x |
| fused_min | 1100, 1000 (m 1052) | 42 -> 64 | 218.73 | 193.23 | 1.132x
|
| v_rag_e1186 | 300, 1500, 900, 1300, 0, 1100 (m 1186) | 42 -> 64 |
473.88 | 410.11 | 1.155x |
| v_3x1200 | 3 x 1200 (m 1200) | 42 -> 64 | 342.09 | 297.18 | 1.151x |
| v_5x1300 | 5 x 1300 (m 1300) | 42 -> 56 | 608.15 | 527.79 | 1.152x |
| v_10x1450 | 10 x 1450 (m 1450) | 42 -> 56 | 1353.55 | 1201.60 | 1.126x
|
| v_2x1600 | 2 x 1600 (m 1600) | 42 -> 50 | 326.67 | 306.90 | 1.064x |
| v_4x1792 | 4 x 1792 (m 1792) | 42 -> 50 | 683.67 | 634.12 | 1.078x |
| vl_10x1800 | 10 x 1800 (m 1800) | 64 -> 48 | 1733.63 | 1708.10 |
1.015x |
| vl_9x1850 | 9 x 1850 (m 1850) | 64 -> 48 | 1603.92 | 1575.06 | 1.018x
|
| vl_10x1900 | 10 x 1900 (m 1900) | 64 -> 48 | 1818.54 | 1792.21 |
1.015x |
| vl_rag1900 | 4500, 13 x 1000 (m 1900) | 64 -> 48 | 1704.27 | 1674.06 |
1.018x |
| v_l9x2000 | 9 x 2000 (m 2000) | 64 -> 48 | 1778.21 | 1758.27 | 1.011x
|
| vl_40x2048 | 40 x 2048 (m 2048) | 64 -> 48 | 8259.81 | 8099.53 |
1.020x |
| vl_14x2050 | 14 x 2050 (m 2050) | 64 -> 48 | 2960.00 | 2930.29 |
1.010x |
| vl_24x2150 | 24 x 2150 (m 2150) | 64 -> 48 | 5409.00 | 5381.13 |
1.005x (within noise) |
| vl_e2200 | 2 x 2200, 0, 7 x 2200 (m 2200) | 64 -> 48 | 2121.43 |
2096.70 | 1.012x |
| vl_8x2400 | 8 x 2400 (m 2400) | 64 -> 48 | 2107.40 | 2076.76 | 1.015x
|
| vl_rag2447 | 3000, 1500, 2500, 2000, 1000, 3500, 2200, 1800 (m 2447) |
64 -> 48 | 1963.36 | 1955.36 | 1.004x |
| vl_e2500 | 4 x 2500, 0, 4 x 2500 (m 2500) | 64 -> 48 | 2290.19 |
2255.91 | 1.015x |
| vl_7x2550 | 7 x 2550 (m 2550) | 64 -> 48 | 2035.54 | 2009.96 | 1.013x
|
Op `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`:

| plan | segment lengths (m) | width main -> PR | main us | PR us |
speedup |
|---|---|---|---|---|---|
| v_32x256 | 32 x 256 (m 256) | 42 -> 64 | 618.66 | 459.16 | 1.347x |
| v_6x700 | 6 x 700 (m 700) | 42 -> 64 | 353.88 | 292.83 | 1.208x |
| v_tiny975 | 1000, 950 (m 976) | 42 -> 64 | 199.18 | 175.55 | 1.135x |
| fused_min | 1100, 1000 (m 1052) | 42 -> 64 | 214.27 | 187.77 | 1.141x
|
| v_rag_e1186 | 300, 1500, 900, 1300, 0, 1100 (m 1186) | 42 -> 64 |
461.98 | 387.48 | 1.192x |
| v_3x1200 | 3 x 1200 (m 1200) | 42 -> 64 | 335.59 | 281.65 | 1.192x |
| v_5x1300 | 5 x 1300 (m 1300) | 42 -> 56 | 593.24 | 496.83 | 1.194x |
| v_10x1450 | 10 x 1450 (m 1450) | 42 -> 56 | 1318.09 | 1142.95 | 1.153x
|
| v_2x1600 | 2 x 1600 (m 1600) | 42 -> 50 | 320.91 | 294.78 | 1.089x |
| v_4x1792 | 4 x 1792 (m 1792) | 42 -> 50 | 667.13 | 597.42 | 1.117x |
| vl_10x1800 | 10 x 1800 (m 1800) | 64 -> 48 | 1666.27 | 1595.26 |
1.045x |
| vl_9x1850 | 9 x 1850 (m 1850) | 64 -> 48 | 1523.35 | 1485.67 | 1.025x
|
| v_6x1900 | 6 x 1900 (m 1900) | 42 -> 50 | 1056.12 | 1010.42 | 1.045x |
| vl_10x1900 | 10 x 1900 (m 1900) | 64 -> 48 | 1757.21 | 1670.64 |
1.052x |
| vl_rag1900 | 4500, 13 x 1000 (m 1900) | 64 -> 48 | 1631.14 | 1567.68 |
1.040x |
| v_rag1925 | 2600, 1400, 1800, 600 (m 1925) | 42 -> 50 | 621.63 |
596.47 | 1.042x |
| v_l9x2000 | 9 x 2000 (m 2000) | 64 -> 48 | 1690.93 | 1642.59 | 1.029x
|
| s2048 | 2048 (m 2048) | 42 -> 50 | 233.45 | 223.36 | 1.045x |
| seg2_4096 | 2 x 2048 (m 2048) | 42 -> 50 | 399.61 | 388.97 | 1.027x |
| v_e2048 | 2 x 2048, 0, 2048 (m 2048) | 42 -> 50 | 585.72 | 561.55 |
1.043x |
| vl_40x2048 | 40 x 2048 (m 2048) | 64 -> 48 | 7886.69 | 7672.66 |
1.028x |
| vl_14x2050 | 14 x 2050 (m 2050) | 64 -> 48 | 2803.57 | 2748.61 |
1.020x |
| vl_24x2150 | 24 x 2150 (m 2150) | 64 -> 48 | 5137.13 | 5069.41 |
1.013x |
| vl_e2200 | 2 x 2200, 0, 7 x 2200 (m 2200) | 64 -> 48 | 2011.21 |
1961.66 | 1.025x |
| vl_8x2400 | 8 x 2400 (m 2400) | 64 -> 48 | 1997.09 | 1959.16 | 1.019x
|
| vl_rag2447 | 3000, 1500, 2500, 2000, 1000, 3500, 2200, 1800 (m 2447) |
64 -> 48 | 1841.97 | 1823.10 | 1.010x |
| vl_e2500 | 4 x 2500, 0, 4 x 2500 (m 2500) | 64 -> 48 | 2170.60 |
2112.70 | 1.027x |
| vl_7x2550 | 7 x 2550 (m 2550) | 64 -> 48 | 1915.77 | 1881.61 | 1.018x
|

**Changed plans: NVIDIA RTX PRO 6000 Blackwell Server Edition (sm_120a,
188 SMs), CUDA 13.4.92**

Op `minimax_h3_sm120_varlen_attention_nvfp4`:

| plan | segment lengths (m) | width main -> PR | main us | PR us |
speedup |
|---|---|---|---|---|---|
| v_32x256 | 32 x 256 (m 256) | 46 -> 80 | 674.59 | 528.82 | 1.276x |
| v_6x700 | 6 x 700 (m 700) | 46 -> 80 | 395.49 | 304.03 | 1.301x |
| v_tiny975 | 1000, 950 (m 976) | 46 -> 80 | 227.46 | 198.35 | 1.147x |
| fused_min | 1100, 1000 (m 1052) | 46 -> 80 | 237.31 | 210.34 | 1.128x
|
| v_rag_e1186 | 300, 1500, 900, 1300, 0, 1100 (m 1186) | 46 -> 80 |
493.06 | 420.13 | 1.174x |
| v_3x1200 | 3 x 1200 (m 1200) | 46 -> 80 | 361.25 | 299.71 | 1.205x |
| v_5x1300 | 5 x 1300 (m 1300) | 46 -> 64 | 645.73 | 513.73 | 1.257x |
| v_10x1450 | 10 x 1450 (m 1450) | 46 -> 64 | 1377.91 | 1203.06 | 1.145x
|
| v_2x1600 | 2 x 1600 (m 1600) | 46 -> 56 | 344.03 | 309.09 | 1.113x |
| v_4x1792 | 4 x 1792 (m 1792) | 46 -> 56 | 690.02 | 615.84 | 1.120x |
| v_6x1900 | 6 x 1900 (m 1900) | 46 -> 56 | 1087.70 | 1045.07 | 1.041x |
| v_rag1925 | 2600, 1400, 1800, 600 (m 1925) | 46 -> 56 | 651.55 |
614.47 | 1.060x |
| s2048 | 2048 (m 2048) | 46 -> 56 | 252.59 | 238.77 | 1.058x |
| seg2_4096 | 2 x 2048 (m 2048) | 46 -> 56 | 410.77 | 402.64 | 1.020x |
| v_e2048 | 2 x 2048, 0, 2048 (m 2048) | 46 -> 56 | 606.72 | 575.12 |
1.055x |
Op `minimax_h3_sm120_varlen_attention_nvfp4_nodelta`:

| plan | segment lengths (m) | width main -> PR | main us | PR us |
speedup |
|---|---|---|---|---|---|
| v_32x256 | 32 x 256 (m 256) | 46 -> 80 | 654.32 | 524.56 | 1.247x |
| v_6x700 | 6 x 700 (m 700) | 46 -> 80 | 381.17 | 298.34 | 1.278x |
| v_tiny975 | 1000, 950 (m 976) | 46 -> 80 | 226.43 | 194.38 | 1.165x |
| fused_min | 1100, 1000 (m 1052) | 46 -> 80 | 234.16 | 207.10 | 1.131x
|
| v_rag_e1186 | 300, 1500, 900, 1300, 0, 1100 (m 1186) | 46 -> 80 |
477.15 | 389.62 | 1.225x |
| v_3x1200 | 3 x 1200 (m 1200) | 46 -> 80 | 354.70 | 278.88 | 1.272x |
| v_5x1300 | 5 x 1300 (m 1300) | 46 -> 64 | 618.02 | 480.06 | 1.287x |
| v_10x1450 | 10 x 1450 (m 1450) | 46 -> 64 | 1332.48 | 1095.81 | 1.216x
|
| v_2x1600 | 2 x 1600 (m 1600) | 46 -> 56 | 335.57 | 302.62 | 1.109x |
| v_4x1792 | 4 x 1792 (m 1792) | 46 -> 56 | 672.42 | 586.45 | 1.147x |
| v_6x1900 | 6 x 1900 (m 1900) | 46 -> 56 | 1044.43 | 948.16 | 1.102x |
| v_rag1925 | 2600, 1400, 1800, 600 (m 1925) | 46 -> 56 | 631.62 |
566.23 | 1.115x |
| s2048 | 2048 (m 2048) | 46 -> 56 | 249.66 | 233.78 | 1.068x |
| seg2_4096 | 2 x 2048 (m 2048) | 46 -> 56 | 405.12 | 386.63 | 1.048x |
| v_e2048 | 2 x 2048, 0, 2048 (m 2048) | 46 -> 56 | 587.97 | 529.89 |
1.110x |

This SM120 family ships for sm_120a only, and its other Cake variants
are the NVFP4-QK / FP8-PV form (`pv_mode="fp8"` on the NVFP4 entry) and
the FP8 packed-varlen form `minimax_h3_sm120_varlen_attention_fp8`,
while the same MiniMax-H3 packed-varlen attention op also ships for
sm_100a (B200) and sm_103a (GB300) as `minimax_h3_varlen_attention`, in
BF16 and two NVFP4 forms (`pv_mode="fp4"` and `pv_mode="fp8"`).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved variable-length attention execution on supported SM120
hardware, with launch sizing that adapts to different segment patterns
and plan sizes.
* Overlapped and sequential execution paths continue to produce matching
results across the tested cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [710f9b5](https://github.com/flashinfer-ai/flashinfer/commit/710f9b5b92296686e42b61fb9857dee98aaabd9f)

- **作者**: eigen
- **时间**: 2026-10-29T18:05:35Z
- **提交信息**: perf(cake_kda): short bounded direct N32 launches take plain work bins where a per-task cost makes bins pay (#7849)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR adds no module and changes no kernel text. It
changes only the host route.

Some bounded direct M128 N32 BF16 launches (gate lower bound set) are
kept at one task per CTA by the strict work-bin test. Such a launch now
uses its module's plain work-binned build when three conditions hold: it
has more tasks than SMs, its longest sequence has at most 8 chunks of 32
tokens, and charging every task a fixed per-task cost still leaves a
large enough margin in the bin assignment. The rule is the same on
sm_100a and sm_103a; TF32 direct, N16 and N32 FT slab launches never
take it, and launches outside this domain keep their route, program and
bin table.

The table covers all 56 shapes of the list.

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 218.05 | 218.11 | 1.00x TIE | 214.51 | 214.40 |
1.00x TIE |
| 12 | none | 16384 | 378.14 | 377.69 | 1.00x TIE | 365.95 | 365.81 |
1.00x TIE |
| 12 | none | 32768 | 685.58 | 686.21 | 1.00x TIE | 646.85 | 646.40 |
1.00x TIE |
| 12 | none | 2x8192 | 371.94 | 372.46 | 1.00x TIE | 358.66 | 358.45 |
1.00x TIE |
| 12 | none | 3000+13384 | 393.95 | 394.21 | 1.00x TIE | 383.79 | 383.46
| 1.00x TIE |
| 12 | none | 4x4096 | 249.73 | 249.60 | 1.00x TIE | 235.49 | 235.65 |
1.00x TIE |
| 12 | none | 2x(8128+64) | 375.15 | 375.18 | 1.00x TIE | 364.19 |
363.71 | 1.00x TIE |
| 12 | none | 8x(1024+64) | 109.12 | 109.22 | 1.00x TIE | 101.54 |
101.52 | 1.00x TIE |
| 12 | none | BS4 x T64 | 16.16 | 16.16 | 1.00x TIE | 15.23 | 15.23 |
1.00x TIE |
| 12 | none | BS16 x T64 | 25.54 | 25.54 | 1.00x TIE | 23.23 | 23.20 |
1.00x TIE |
| 12 | none | BS64 x T64 | 58.83 | 58.62 | 1.00x TIE | 54.30 | 54.38 |
1.00x TIE |
| 12 | none | BS16 x T128 | 38.08 | 38.11 | 1.00x TIE | 34.24 | 34.30 |
1.00x TIE |
| 12 | none | BS16 x T256 | 63.78 | 63.81 | 1.00x TIE | 56.77 | 56.77 |
1.00x TIE |
| 12 | none | BS16 x T(17..255) | 37.28 | 37.26 | 1.00x TIE | 35.33 |
35.33 | 1.00x TIE |
| 16 | none | 8192 | 267.45 | 267.65 | 1.00x TIE | 267.27 | 266.47 |
1.00x TIE |
| 16 | none | 16384 | 465.61 | 465.87 | 1.00x TIE | 445.70 | 445.12 |
1.00x TIE |
| 16 | none | 32768 | 878.14 | 878.30 | 1.00x TIE | 824.31 | 823.81 |
1.00x TIE |
| 16 | none | 2x8192 | 486.08 | 485.95 | 1.00x TIE | 466.16 | 466.50 |
1.00x TIE |
| 16 | none | 3000+13384 | 477.65 | 477.42 | 1.00x TIE | 457.84 | 457.59
| 1.00x TIE |
| 16 | none | 4x4096 | 263.84 | 263.87 | 1.00x TIE | 245.73 | 245.89 |
1.00x TIE |
| 16 | none | 2x(8128+64) | 492.03 | 492.32 | 1.00x TIE | 478.63 |
478.08 | 1.00x TIE |
| 16 | none | 8x(1024+64) | 111.78 | 111.97 | 1.00x TIE | 104.64 |
104.62 | 1.00x TIE |
| 16 | none | BS4 x T64 | 16.38 | 16.38 | 1.00x TIE | 15.46 | 15.46 |
1.00x TIE |
| 16 | none | BS16 x T64 | 25.92 | 25.95 | 1.00x TIE | 23.62 | 23.62 |
1.00x TIE |
| 16 | none | BS64 x T64 | 69.28 | 69.28 | 1.00x TIE | 65.41 | 65.41 |
1.00x TIE |
| 16 | none | BS16 x T128 | 39.17 | 39.20 | 1.00x TIE | 35.42 | 35.41 |
1.00x TIE |
| 16 | none | BS16 x T256 | 66.37 | 66.40 | 1.00x TIE | 58.72 | 58.72 |
1.00x TIE |
| 16 | none | BS16 x T(17..255) | 41.54 | 41.60 | 1.00x TIE | 37.38 |
37.41 | 1.00x TIE |
| 12 | -5 | 8192 | 160.70 | 160.61 | 1.00x TIE | 153.92 | 154.31 | 1.00x
TIE |
| 12 | -5 | 16384 | 260.93 | 261.30 | 1.00x TIE | 247.59 | 248.50 |
1.00x TIE |
| 12 | -5 | 32768 | 459.04 | 459.31 | 1.00x TIE | 428.67 | 429.33 |
1.00x TIE |
| 12 | -5 | 2x8192 | 359.81 | 359.78 | 1.00x TIE | 244.55 | 244.66 |
1.00x TIE |
| 12 | -5 | 3000+13384 | 273.47 | 273.26 | 1.00x TIE | 259.20 | 259.44 |
1.00x TIE |
| 12 | -5 | 4x4096 | 192.69 | 192.70 | 1.00x TIE | 179.71 | 179.71 |
1.00x TIE |
| 12 | -5 | 2x(8128+64) | 356.41 | 356.41 | 1.00x TIE | 248.88 | 249.52
| 1.00x TIE |
| 12 | -5 | 8x(1024+64) | 110.94 | 110.94 | 1.00x TIE | 103.30 | 103.20
| 1.00x TIE |
| 12 | -5 | BS4 x T64 | 11.23 | 11.23 | 1.00x TIE | 10.53 | 10.50 |
1.00x TIE |
| 12 | -5 | BS16 x T64 | 28.26 | 28.22 | 1.00x TIE | 26.72 | 26.72 |
1.00x TIE |
| 12 | -5 | BS64 x T64 | 73.73 | 73.70 | 1.00x TIE | 69.57 | 69.60 |
1.00x TIE |
| 12 | -5 | BS16 x T128 | 33.31 | 33.31 | 1.00x TIE | 31.27 | 31.26 |
1.00x TIE |
| 12 | -5 | BS16 x T256 | 47.68 | 47.74 | 1.00x TIE | 44.99 | 44.99 |
1.00x TIE |
| 12 | -5 | BS16 x T(17..255) | 31.17 | 31.17 | 1.00x TIE | 29.44 |
29.44 | 1.00x TIE |
| 16 | -5 | 8192 | 195.13 | 195.65 | 1.00x TIE | 188.87 | 189.38 | 1.00x
TIE |
| 16 | -5 | 16384 | 322.05 | 322.13 | 1.00x TIE | 313.50 | 313.95 |
1.00x TIE |
| 16 | -5 | 32768 | 576.40 | 576.91 | 1.00x TIE | 551.36 | 553.44 |
1.00x TIE |
| 16 | -5 | 2x8192 | 361.15 | 361.10 | 1.00x TIE | 343.52 | 343.46 |
1.00x TIE |
| 16 | -5 | 3000+13384 | 338.05 | 337.90 | 1.00x TIE | 320.61 | 321.27 |
1.00x TIE |
| 16 | -5 | 4x4096 | 205.09 | 205.09 | 1.00x TIE | 182.18 | 182.21 |
1.00x TIE |
| 16 | -5 | 2x(8128+64) | 358.69 | 358.69 | 1.00x TIE | 341.25 | 341.28
| 1.00x TIE |
| 16 | -5 | 8x(1024+64) | 88.80 | 88.80 | 1.00x TIE | 76.58 | 76.58 |
1.00x TIE |
| 16 | -5 | BS4 x T64 | 11.68 | 11.68 | 1.00x TIE | 10.85 | 10.85 |
1.00x TIE |
| 16 | -5 | BS16 x T64 | 25.82 | 25.82 | 1.00x TIE | 24.02 | 24.03 |
1.00x TIE |
| 16 | -5 | BS64 x T64 | 72.43 | 72.42 | 1.00x TIE | 67.71 | 67.71 |
1.00x TIE |
| 16 | -5 | BS16 x T128 | 34.24 | 34.24 | 1.00x TIE | 32.16 | 32.16 |
1.00x TIE |
| 16 | -5 | BS16 x T256 | 49.09 | 49.06 | 1.00x TIE | 45.89 | 45.92 |
1.00x TIE |
| 16 | -5 | BS16 x T(17..255) | 38.66 | 36.64 | 1.05x | 36.13 | 34.27 |
1.05x |

B200: NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07. GB300: NVIDIA
GB300, sm_103a, 152 SMs, driver 580.159.03. CUDA 13.4 (nvcc), PyTorch
2.14.1+cu130.

Latency is in microseconds and is the run-half median per call of the
timing pair, with BF16 q/k/v and FP32 recurrent state. "main" is
FlashInfer main at c710080a329c, the previous Cake version of this
kernel. Speedup is main / this PR. TIE means no difference beyond the
measurement band. On both GPUs, 1 row is faster and the other 55 are
TIE. The faster row is 16 heads, gate lower bound -5, BS16 x T(17..255):
38.66 -> 36.64 us on B200 and 36.13 -> 34.27 us on GB300, 1.05x on each.

Outside the 56-shape list, a sweep covered further short bounded launch
shapes that the rule moves: 318 on B200 and 306 on GB300. On each GPU,
all but 2 are faster (up to 1.28x on both GPUs), those 2 tie, and none
is slower.

The kernel's other Cake variants are unchanged: the TF32-input modules
and the BF16-state forms; the family ships on sm_100a and sm_103a, and
this PR covers both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Improved execution scheduling for certain bounded sequence workloads,
including launches with many tasks and relatively short sequences.
Eligible workloads can now use a work distribution better suited to
their size.
* Unbounded workloads retain their existing scheduling behavior, and
bounded workloads that do not meet the eligibility conditions continue
using the existing approach.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [47442df](https://github.com/flashinfer-ai/flashinfer/commit/47442df64e69d50229d4b4e79226ca4eefb040ca)

- **作者**: eigen
- **时间**: 2026-10-29T18:05:19Z
- **提交信息**: perf(cake_grouped_mxfp8_quantize): head-window L2 prefetch for two row-2D problem shapes (#7848)

`cake_grouped_mxfp8_quantize` takes a BF16 or F16 `x[B, M, K]` and an
int32 `mask[B]` that gives the valid rows per group. It writes FP8 E4M3
values and UE8M0 block scales, one per 32 elements, in the 128x4
grouped-GEMM scale layout. The host picks the program from B, M and K.
It never reads the mask's values. Before this PR the kernel had 12
programs. They are row-2D, bulk-copy, 128-thread row-tiled, and three
per-K row-tiled programs, each for BF16 and F16 input. The per-K
row-tiled programs use 224 threads at K = 7168, 256 threads at K = 4096
and 128 threads at K = 2048. This PR adds two prefetch variants of
row-2D, for BF16 and F16 input (4 programs). That makes 16 programs.
Each variant is the row-2D program plus two L2 bulk prefetches issued at
the start. Each CTA whose part of x starts within the first 2 MiB of x
prefetches that part into L2. The other variant uses a 4 MiB window. One
CTA prefetches the whole mask. Outputs are bitwise identical to row-2D.
[8, 512, 2048] now routes to the 2 MiB window, and [64, 128, 4096]
routes to the 4 MiB window. This applies only when the mask's address is
16-byte aligned. Otherwise these shapes use row-2D, as before. All other
shapes route exactly as before.

The baseline is the previous Cake version of this kernel, already in
FlashInfer main (#7778). FlashInfer's host chooses the program on both
sides. On both re-routed shapes, the previous version ran row-2D. Each
pair of numbers below is GB300 / GB200. With a full mask, [8, 512, 2048]
gains 1.0536x / 1.0486x (6.940 -> 6.589 µs / 7.080 -> 6.753 µs). With a
full mask, [64, 128, 4096] gains 1.0264x / 1.0236x (19.010 -> 18.525 µs
/ 19.024 -> 18.579 µs). The other 20 rows of the standard shape list
keep their program and measure 0.9989–1.0015 / 0.9993–1.0008. None of
them is slower than before beyond the run's A/A noise band. The rows
marked ¶ test other masks on the two re-routed shapes. Sparse masks with
most rows valid are faster, by up to 1.0521x. Masks with no valid rows
are slower. [8, 512, 2048] measures 0.9977x / 0.9791x (3.459 -> 3.468 µs
/ 3.512 -> 3.584 µs). [64, 128, 4096] measures 0.9948x / 0.9927x. With
16 valid rows per group, [8, 512, 2048] measures 1.0016x / 0.9948x. With
128 valid rows per group, it measures 0.9957x / 0.9939x.

Speedup = previous µs / this PR µs, the median of paired per-round
ratios over 12 interleaved rounds with a cold L2, with its 95 % CI;
above 1 is faster.
† Same program before and after, so the two columns are an A/A pair of
that program.
‡ Extra sparse-mask rows at K = 2048, beyond the standard shape list.
¶ Extra rows of the two re-routed shapes with other masks, beyond the
standard shape list.

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | previous program | this
PR program | previous (µs) | this PR (µs) | speedup [95% CI] |
|---|---|---|---:|---|---|---:|---:|---|
| [2, 256, 4096] † | BF16 | full | 512 | bulk-copy | bulk-copy | 3.509 |
3.512 | 0.9991 [0.9986, 1.0003] |
| [3, 256, 2048] † | BF16 | full | 768 | bulk-copy | bulk-copy | 3.134 |
3.133 | 1.0000 [0.9984, 1.0016] |
| [32, 1024, 7168] † | BF16 | 16 / group | 512 | K = 7168 row-tiled (224
threads) | K = 7168 row-tiled (224 threads) | 11.056 | 11.066 | 0.9995
[0.9988, 1.0005] |
| [32, 1024, 7168] † | BF16 | 512 in group 0 | 512 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 10.786 | 10.788 |
1.0000 [0.9997, 1.0003] |
| [32, 1024, 7168] † | BF16 | Zipf, 4096 total | 4096 | K = 7168
row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 21.109 |
21.113 | 0.9999 [0.9994, 1.0003] |
| [32, 1024, 4096] † | BF16 | 16 / group | 512 | K = 4096 row-tiled (256
threads) | K = 4096 row-tiled (256 threads) | 6.270 | 6.270 | 1.0000
[0.9962, 1.0021] |
| [32, 1024, 2048] † | BF16 | full | 32768 | K = 2048 row-tiled (128
threads) | K = 2048 row-tiled (128 threads) | 34.466 | 34.483 | 0.9996
[0.9987, 1.0003] |
| [32, 1024, 2048] † ‡ | BF16 | Zipf, 4096 total | 4096 | K = 2048
row-tiled (128 threads) | K = 2048 row-tiled (128 threads) | 7.422 |
7.429 | 0.9989 [0.9981, 1.0005] |
| [2, 256, 4096] † | F16 | full | 512 | bulk-copy | bulk-copy | 3.507 |
3.505 | 1.0003 [0.9989, 1.0014] |
| [8, 512, 2048] | BF16 | full | 4096 | row-2D | row-2D + L2 prefetch (2
MiB window) | 6.940 | 6.589 | 1.0536 [1.0517, 1.0556] |
| [32, 1024, 7168] † | BF16 | 32 / group | 1024 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 11.804 | 11.806 |
0.9999 [0.9990, 1.0005] |
| [32, 1024, 7168] † | BF16 | 1024 in group 0 | 1024 | K = 7168
row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 12.683 |
12.684 | 0.9999 [0.9993, 1.0003] |
| [32, 1024, 7168] † | BF16 | full | 32768 | K = 7168 row-tiled (224
threads) | K = 7168 row-tiled (224 threads) | 104.508 | 104.524 | 0.9998
[0.9996, 1.0001] |
| [32, 1024, 4096] † | BF16 | 128 / group | 4096 | K = 4096 row-tiled
(256 threads) | K = 4096 row-tiled (256 threads) | 11.601 | 11.599 |
1.0002 [0.9993, 1.0006] |
| [32, 1024, 2048] † ‡ | BF16 | 16 / group | 512 | K = 2048 row-tiled
(128 threads) | K = 2048 row-tiled (128 threads) | 5.924 | 5.915 |
1.0015 [0.9998, 1.0020] |
| [2, 128, 4096] † | BF16 | full | 256 | bulk-copy | bulk-copy | 2.842 |
2.844 | 0.9993 [0.9986, 1.0000] |
| [64, 128, 4096] | BF16 | full | 8192 | row-2D | row-2D + L2 prefetch
(4 MiB window) | 19.010 | 18.525 | 1.0264 [1.0253, 1.0271] |
| [32, 1024, 7168] † | BF16 | 128 / group | 4096 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 18.036 | 18.040 |
0.9993 [0.9986, 1.0001] |
| [32, 1024, 7168] † | BF16 | 1024 in group 0, 99 in others | 4093 | K =
7168 row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 19.449
| 19.463 | 0.9996 [0.9984, 1.0004] |
| [32, 1024, 7168] † | F16 | 128 / group | 4096 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 17.999 | 18.005 |
1.0000 [0.9993, 1.0002] |
| [32, 1024, 4096] † | BF16 | full | 32768 | K = 4096 row-tiled (256
threads) | K = 4096 row-tiled (256 threads) | 62.419 | 62.416 | 1.0000
[0.9995, 1.0009] |
| [32, 1024, 2048] † ‡ | BF16 | 128 / group | 4096 | K = 2048 row-tiled
(128 threads) | K = 2048 row-tiled (128 threads) | 7.369 | 7.366 |
1.0007 [0.9993, 1.0016] |
| [8, 512, 2048] ¶ | BF16 | 16 / group | 128 | row-2D | row-2D + L2
prefetch (2 MiB window) | 3.768 | 3.760 | 1.0016 [1.0003, 1.0035] |
| [64, 128, 4096] ¶ | BF16 | 64 / group | 4096 | row-2D | row-2D + L2
prefetch (4 MiB window) | 11.746 | 11.579 | 1.0140 [1.0132, 1.0153] |
| [64, 128, 4096] ¶ | BF16 | 0 / group | 0 | row-2D | row-2D + L2
prefetch (4 MiB window) | 5.507 | 5.536 | 0.9948 [0.9942, 0.9953] |
| [8, 512, 2048] ¶ | BF16 | 128 / group | 1024 | row-2D | row-2D + L2
prefetch (2 MiB window) | 4.127 | 4.143 | 0.9957 [0.9949, 0.9973] |
| [64, 128, 4096] ¶ | BF16 | 127 / group | 8128 | row-2D | row-2D + L2
prefetch (4 MiB window) | 18.859 | 18.429 | 1.0234 [1.0225, 1.0244] |
| [8, 512, 2048] ¶ | BF16 | 511 / group | 4088 | row-2D | row-2D + L2
prefetch (2 MiB window) | 6.910 | 6.586 | 1.0492 [1.0483, 1.0506] |
| [64, 128, 4096] ¶ | BF16 | 16 / group | 1024 | row-2D | row-2D + L2
prefetch (4 MiB window) | 6.549 | 6.482 | 1.0103 [1.0094, 1.0128] |
| [8, 512, 2048] ¶ | BF16 | 0 / group | 0 | row-2D | row-2D + L2
prefetch (2 MiB window) | 3.459 | 3.468 | 0.9977 [0.9965, 0.9983] |

**NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4**

| shape [B, M, K] | dtype | mask | valid rows | previous program | this
PR program | previous (µs) | this PR (µs) | speedup [95% CI] |
|---|---|---|---:|---|---|---:|---:|---|
| [2, 256, 4096] † | BF16 | full | 512 | bulk-copy | bulk-copy | 3.566 |
3.566 | 1.0000 [0.9983, 1.0009] |
| [2, 256, 4096] † | F16 | full | 512 | bulk-copy | bulk-copy | 3.537 |
3.538 | 1.0000 [0.9992, 1.0006] |
| [2, 128, 4096] † | BF16 | full | 256 | bulk-copy | bulk-copy | 2.850 |
2.852 | 0.9993 [0.9982, 1.0004] |
| [3, 256, 2048] † | BF16 | full | 768 | bulk-copy | bulk-copy | 3.189 |
3.188 | 1.0006 [0.9987, 1.0019] |
| [8, 512, 2048] | BF16 | full | 4096 | row-2D | row-2D + L2 prefetch (2
MiB window) | 7.080 | 6.753 | 1.0486 [1.0465, 1.0504] |
| [64, 128, 4096] | BF16 | full | 8192 | row-2D | row-2D + L2 prefetch
(4 MiB window) | 19.024 | 18.579 | 1.0236 [1.0224, 1.0259] |
| [32, 1024, 7168] † | BF16 | 16 / group | 512 | K = 7168 row-tiled (224
threads) | K = 7168 row-tiled (224 threads) | 11.464 | 11.458 | 1.0006
[0.9993, 1.0011] |
| [32, 1024, 7168] † | BF16 | 32 / group | 1024 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 12.261 | 12.264 |
0.9998 [0.9991, 1.0006] |
| [32, 1024, 7168] † | BF16 | 128 / group | 4096 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 18.673 | 18.673 |
1.0000 [0.9994, 1.0005] |
| [32, 1024, 7168] † | BF16 | 512 in group 0 | 512 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 11.169 | 11.168 |
1.0002 [1.0000, 1.0004] |
| [32, 1024, 7168] † | BF16 | 1024 in group 0 | 1024 | K = 7168
row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 13.119 |
13.116 | 1.0003 [0.9999, 1.0007] |
| [32, 1024, 7168] † | BF16 | 1024 in group 0, 99 in others | 4093 | K =
7168 row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 19.972
| 19.968 | 1.0001 [0.9993, 1.0007] |
| [32, 1024, 7168] † | BF16 | Zipf, 4096 total | 4096 | K = 7168
row-tiled (224 threads) | K = 7168 row-tiled (224 threads) | 21.547 |
21.551 | 0.9998 [0.9995, 1.0002] |
| [32, 1024, 7168] † | BF16 | full | 32768 | K = 7168 row-tiled (224
threads) | K = 7168 row-tiled (224 threads) | 103.750 | 103.750 | 1.0000
[0.9998, 1.0001] |
| [32, 1024, 7168] † | F16 | 128 / group | 4096 | K = 7168 row-tiled
(224 threads) | K = 7168 row-tiled (224 threads) | 18.640 | 18.637 |
1.0000 [0.9998, 1.0007] |
| [32, 1024, 4096] † | BF16 | 16 / group | 512 | K = 4096 row-tiled (256
threads) | K = 4096 row-tiled (256 threads) | 6.460 | 6.460 | 1.0002
[0.9978, 1.0012] |
| [32, 1024, 4096] † | BF16 | 128 / group | 4096 | K = 4096 row-tiled
(256 threads) | K = 4096 row-tiled (256 threads) | 11.833 | 11.837 |
1.0000 [0.9985, 1.0005] |
| [32, 1024, 4096] † | BF16 | full | 32768 | K = 4096 row-tiled (256
threads) | K = 4096 row-tiled (256 threads) | 62.123 | 62.105 | 1.0003
[0.9997, 1.0004] |
| [32, 1024, 2048] † | BF16 | full | 32768 | K = 2048 row-tiled (128
threads) | K = 2048 row-tiled (128 threads) | 34.521 | 34.517 | 1.0005
[0.9994, 1.0013] |
| [32, 1024, 2048] † ‡ | BF16 | 16 / group | 512 | K = 2048 row-tiled
(128 threads) | K = 2048 row-tiled (128 threads) | 6.156 | 6.154 |
1.0002 [0.9995, 1.0007] |
| [32, 1024, 2048] † ‡ | BF16 | 128 / group | 4096 | K = 2048 row-tiled
(128 threads) | K = 2048 row-tiled (128 threads) | 7.602 | 7.597 |
0.9997 [0.9992, 1.0007] |
| [32, 1024, 2048] † ‡ | BF16 | Zipf, 4096 total | 4096 | K = 2048
row-tiled (128 threads) | K = 2048 row-tiled (128 threads) | 7.635 |
7.630 | 1.0008 [0.9993, 1.0014] |
| [8, 512, 2048] ¶ | BF16 | 16 / group | 128 | row-2D | row-2D + L2
prefetch (2 MiB window) | 3.833 | 3.855 | 0.9948 [0.9925, 0.9961] |
| [8, 512, 2048] ¶ | BF16 | 128 / group | 1024 | row-2D | row-2D + L2
prefetch (2 MiB window) | 4.263 | 4.290 | 0.9939 [0.9909, 0.9944] |
| [8, 512, 2048] ¶ | BF16 | 511 / group | 4088 | row-2D | row-2D + L2
prefetch (2 MiB window) | 6.986 | 6.642 | 1.0521 [1.0508, 1.0532] |
| [64, 128, 4096] ¶ | BF16 | 16 / group | 1024 | row-2D | row-2D + L2
prefetch (4 MiB window) | 6.800 | 6.741 | 1.0084 [1.0076, 1.0097] |
| [64, 128, 4096] ¶ | BF16 | 64 / group | 4096 | row-2D | row-2D + L2
prefetch (4 MiB window) | 11.636 | 11.493 | 1.0122 [1.0117, 1.0138] |
| [64, 128, 4096] ¶ | BF16 | 127 / group | 8128 | row-2D | row-2D + L2
prefetch (4 MiB window) | 18.943 | 18.494 | 1.0238 [1.0225, 1.0249] |
| [8, 512, 2048] ¶ | BF16 | 0 / group | 0 | row-2D | row-2D + L2
prefetch (2 MiB window) | 3.512 | 3.584 | 0.9791 [0.9785, 0.9799] |
| [64, 128, 4096] ¶ | BF16 | 0 / group | 0 | row-2D | row-2D + L2
prefetch (4 MiB window) | 5.728 | 5.771 | 0.9927 [0.9922, 0.9931] |

The kernel's other Cake variants in FlashInfer are row-2D, bulk-copy,
128-thread row-tiled and three per-K row-tiled programs, each for BF16
and F16 input; all 16 programs ship for sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added specialized grouped MXFP8 quantization support for float16 and
bfloat16 inputs at select shapes, with fallback behavior for other
shapes and unaligned masks.
* Added support for quantization programs optimized to warm the GPU
cache for these workloads.
* **Tests**
* Expanded coverage for program selection and verified outputs against
the reference for aligned and misaligned masks.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5cc23cd](https://github.com/flashinfer-ai/flashinfer/commit/5cc23cde4a08ff97c95443cddbcc87402d5d3650)

- **作者**: eigen
- **时间**: 2026-10-29T18:05:08Z
- **提交信息**: perf(cake_muse_spark_norm): retune the gated residual RMSNorm routes on GB300 and the next-RMSNorm routes on B200, GB300 and R200 (#7844)

The package ships three Cake kernels: gated residual RMSNorm (mode 0
without a weight, mode 1 with a weight and gain center 1.0; plain and
PDL routes), gated residual next-RMSNorm (alpha tensor + post weight,
alpha scalar without a post weight, alpha scalar + post weight) and
RMSNorm + sigmoid gate (bf16; plain and PDL routes). The speedup
baseline is the previous Cake package on FlashInfer main, which ships 80
programs and 148 libraries. This PR's package ships 85 programs and 154
libraries (51 for `sm_100a`, 49 for `sm_103a`, 54 for `sm_107a`). In the
descriptions and tables below, M is the number of rows.

On B200 (`sm_100a`), only the next-RMSNorm route with an alpha tensor
and a post weight changes: M = 960-1151 moves to a one-CTA TMA-staged
ring with evict_last row fills.

On GB300 (`sm_103a`), the gated residual RMSNorm plain routes change
above a row threshold:
- Mode 0 at M > 8192 takes a new prologue program that issues the alpha
/ beta plane loads after the row's residual loads.
- Mode 1 at M > 4096 takes the prologue program with coherent evict_last
plane loads, built as a plain route.

The GB300 next-RMSNorm routes change as follows:
- Alpha tensor + post weight: M = 513-832 and 960-3584 move to a
four-CTA persistent program with a two-row prefetch, and M = 833-959
moves to the TMA-staged program.
- Alpha scalar without a post weight: M = 257-320 and 385-3072 move to a
program with evict_last loads.

On R200 (`sm_107a`), the next-RMSNorm alpha tensor + post weight route
uses four programs: the eight-CTA program for M <= 383, its
evict_last-load form for 384-512, the four-CTA two-row-prefetch form for
513-1280 and the evict_last ring for 1281 and above. The R200 alpha
scalar route without a post weight takes the four-CTA evict_last-load
two-row-prefetch form at M = 384-1024 only. Rows 1025-4096 keep the
previous program, so Table 3 leaves out 2048, 4095 and 4096.

**B200 Table 1.** Gated residual next-RMSNorm, alpha tensor + post
weight, NVIDIA B200 (`sm_100a`), CUDA 13.0, driver 580.82.07, PDL
default. Each kernel is timed alone (CUPTI kernel-active median, cold
L2, memset flush). Previous = the previous Cake package on FlashInfer
main, this PR = this PR's package. The data come from 6 interleaved
sessions on two GPUs, with per-session medians (s1 / s2 / s3 / s4 / s5 /
s6) and a pooled speedup.

| variant | M | previous us (per session) | this PR us (per session) |
speedup (previous / this PR) |
|---|---|---|---|---|
| alpha tensor + post_weight | 1 | 2.859 / 2.860 / 2.855 / 2.854 / 2.868
/ 2.866 | 2.859 / 2.861 / 2.862 / 2.865 / 2.861 / 2.857 | 0.9995 |
| alpha tensor + post_weight | 128 | 4.935 / 4.935 / 4.932 / 4.944 /
4.953 / 4.947 | 4.937 / 4.941 / 4.931 / 4.946 / 4.955 / 4.949 | 0.9992 |
| alpha tensor + post_weight | 2048 | 33.752 / 33.904 / 33.848 / 33.840
/ 33.856 / 33.856 | 33.928 / 33.968 / 34.048 / 33.960 / 33.840 / 33.896
| 0.9973 |
| alpha tensor + post_weight | 16384 | 241.480 / 241.344 / 241.072 /
241.088 / 241.392 / 241.096 | 241.032 / 241.440 / 241.472 / 241.168 /
241.520 / 241.544 | 0.9990 |
| alpha tensor + post_weight | 8 | 2.982 / 2.982 / 2.980 / 3.029 / 3.028
/ 3.033 | 2.977 / 2.974 / 2.977 / 3.026 / 3.033 / 3.027 | 1.0012 |
| alpha tensor + post_weight | 16 | 3.124 / 3.128 / 3.123 / 3.154 /
3.149 / 3.148 | 3.121 / 3.118 / 3.127 / 3.152 / 3.155 / 3.150 | 0.9999 |
| alpha tensor + post_weight | 32 | 3.391 / 3.389 / 3.387 / 3.384 /
3.388 / 3.379 | 3.387 / 3.385 / 3.394 / 3.377 / 3.378 / 3.384 | 1.0009 |
| alpha tensor + post_weight | 64 | 4.008 / 4.014 / 4.016 / 4.029 /
4.034 / 4.030 | 4.015 / 4.011 / 4.011 / 4.030 / 4.030 / 4.025 | 1.0007 |
| alpha tensor + post_weight | 256 | 7.314 / 7.313 / 7.316 / 7.346 /
7.355 / 7.345 | 7.319 / 7.312 / 7.310 / 7.350 / 7.352 / 7.357 | 0.9996 |
| alpha tensor + post_weight | 383 | 9.425 / 9.415 / 9.406 / 9.422 /
9.420 / 9.428 | 9.417 / 9.418 / 9.411 / 9.406 / 9.411 / 9.404 | 1.0011 |
| alpha tensor + post_weight | 384 | 9.437 / 9.457 / 9.451 / 9.491 /
9.489 / 9.494 | 9.448 / 9.446 / 9.452 / 9.482 / 9.480 / 9.484 | 1.0008 |
| alpha tensor + post_weight | 512 | 11.624 / 11.584 / 11.624 / 11.568 /
11.584 / 11.616 | 11.616 / 11.616 / 11.584 / 11.568 / 11.584 / 11.600 |
1.0007 |
| alpha tensor + post_weight | 959 | 17.968 / 18.040 / 18.080 / 18.088 /
18.072 / 18.080 | 18.008 / 18.008 / 17.984 / 18.120 / 18.088 / 18.024 |
1.0033 |
| alpha tensor + post_weight | 960 | 18.024 / 18.056 / 18.024 / 18.104 /
18.136 / 18.088 | 17.760 / 17.744 / 17.720 / 17.944 / 17.960 / 17.944 |
1.0123 |
| alpha tensor + post_weight | 961 | 18.304 / 18.352 / 18.376 / 18.432 /
18.369 / 18.432 | 17.632 / 17.688 / 17.672 / 17.976 / 17.952 / 17.872 |
1.0333 |
| alpha tensor + post_weight | 1024 | 20.056 / 20.096 / 20.080 / 20.056
/ 20.001 / 20.072 | 17.912 / 18.008 / 17.912 / 17.944 / 18.000 / 18.000
| 1.1164 |
| alpha tensor + post_weight | 1150 | 21.200 / 21.272 / 21.168 / 21.256
/ 21.280 / 21.240 | 19.600 / 19.680 / 19.615 / 19.856 / 19.920 / 19.968
| 1.0749 |
| alpha tensor + post_weight | 1151 | 21.208 / 21.144 / 21.136 / 21.208
/ 21.335 / 21.280 | 19.664 / 19.680 / 19.664 / 19.904 / 19.952 / 19.912
| 1.0716 |
| alpha tensor + post_weight | 1152 | 20.855 / 20.912 / 20.888 / 20.864
/ 20.808 / 20.800 | 21.128 / 20.872 / 20.888 / 20.832 / 20.840 / 20.840
| 1.0002 |
| alpha tensor + post_weight | 1536 | 26.992 / 26.976 / 27.040 / 27.008
/ 26.976 / 27.008 | 26.975 / 26.984 / 26.992 / 26.976 / 26.999 / 27.048
| 1.0004 |
| alpha tensor + post_weight | 3072 | 49.056 / 49.080 / 49.088 / 48.928
/ 48.880 / 49.000 | 49.144 / 49.184 / 49.184 / 48.864 / 48.976 / 48.832
| 0.9993 |
| alpha tensor + post_weight | 4096 | 64.176 / 64.152 / 64.216 / 63.856
/ 63.816 / 63.792 | 64.336 / 64.168 / 64.183 / 63.872 / 63.832 / 63.872
| 0.9998 |
| alpha tensor + post_weight | 4097 | 65.080 / 64.976 / 64.880 / 64.928
/ 65.072 / 65.096 | 65.024 / 64.935 / 65.064 / 64.976 / 64.992 / 64.928
| 1.0006 |
| alpha tensor + post_weight | 8192 | 124.216 / 124.128 / 124.192 /
124.200 / 124.168 / 124.384 | 123.952 / 124.367 / 124.376 / 124.264 /
124.128 / 124.256 | 0.9995 |

**GB300 Table 2.** Gated residual RMSNorm plain routes (units u3, u4)
and gated residual next-RMSNorm (units u1, u2), NVIDIA GB300
(`sm_103a`), CUDA 13.0, driver 580.159.03. The RMSNorm rows run with PDL
off (the plain route) and the next-RMSNorm rows with PDL default. Each
kernel is timed alone (CUPTI kernel-active median, cold L2, memset
flush). Previous = the previous Cake package on FlashInfer main, this PR
= this PR's package. Each unit is one GPU with 3 interleaved sessions,
per-session medians (s1 / s2 / s3 or s4 / s5 / s6) and its own pooled
speedup.

| variant | M | unit | previous us (per session) | this PR us (per
session) | speedup (previous / this PR) |
|---|---|---|---|---|---|
| mode 0 | 1 | u3 | 2.079 / 2.081 / 2.077 | 2.086 / 2.081 / 2.078 |
0.9993 |
| mode 0 | 16 | u3 | 2.227 / 2.220 / 2.226 | 2.233 / 2.220 / 2.226 |
1.0000 |
| mode 0 | 128 | u3 | 4.301 / 4.305 / 4.298 | 4.307 / 4.304 / 4.307 |
0.9987 |
| mode 0 | 1024 | u3 | 15.240 / 15.144 / 15.128 | 15.128 / 15.144 /
15.136 | 1.0005 |
| mode 0 | 16384 | u3 | 193.928 / 193.911 / 193.888 | 192.873 / 192.783
/ 192.816 | 1.0057 |
| mode 1 | 1 | u3 | 2.916 / 2.874 / 2.876 | 2.877 / 2.872 / 2.886 |
1.0000 |
| mode 1 | 16 | u3 | 3.283 / 3.295 / 3.276 | 3.289 / 3.302 / 3.291 |
0.9974 |
| mode 1 | 128 | u3 | 4.437 / 4.450 / 4.442 | 4.437 / 4.444 / 4.440 |
1.0003 |
| mode 1 | 1024 | u3 | 15.232 / 15.296 / 15.232 | 15.256 / 15.232 /
15.256 | 0.9984 |
| mode 1 | 16384 | u3 | 196.936 / 197.040 / 197.008 | 193.384 / 193.360
/ 193.327 | 1.0189 |
| mode 0 | 8191 | u3 | 98.840 / 98.784 / 98.792 | 98.824 / 98.768 /
98.784 | 1.0001 |
| mode 0 | 8192 | u3 | 98.816 / 98.769 / 98.768 | 98.800 / 98.840 /
98.815 | 0.9995 |
| mode 0 | 8193 | u3 | 98.968 / 99.064 / 99.080 | 98.616 / 98.600 /
98.656 | 1.0045 |
| mode 1 | 4095 | u3 | 51.928 / 51.880 / 51.872 | 51.768 / 51.888 /
51.816 | 1.0012 |
| mode 1 | 4096 | u3 | 51.920 / 51.888 / 51.952 | 51.920 / 51.976 /
51.816 | 1.0000 |
| mode 1 | 4097 | u3 | 51.976 / 51.848 / 51.960 | 51.504 / 51.632 /
51.672 | 1.0064 |
| mode 0 | 1 | u4 | 2.108 / 2.107 / 2.107 | 2.109 / 2.108 / 2.109 |
0.9993 |
| mode 0 | 16 | u4 | 2.229 / 2.228 / 2.229 | 2.226 / 2.237 / 2.240 |
0.9966 |
| mode 0 | 128 | u4 | 4.299 / 4.296 / 4.303 | 4.300 / 4.296 / 4.301 |
0.9999 |
| mode 0 | 1024 | u4 | 15.096 / 15.120 / 15.088 | 15.096 / 15.104 /
15.128 | 0.9995 |
| mode 0 | 16384 | u4 | 193.760 / 193.903 / 193.832 | 192.745 / 192.768
/ 192.720 | 1.0056 |
| mode 1 | 1 | u4 | 2.901 / 2.901 / 2.897 | 2.897 / 2.895 / 2.895 |
1.0019 |
| mode 1 | 16 | u4 | 3.280 / 3.278 / 3.279 | 3.278 / 3.313 / 3.273 |
1.0003 |
| mode 1 | 128 | u4 | 4.438 / 4.439 / 4.439 | 4.443 / 4.440 / 4.443 |
0.9991 |
| mode 1 | 1024 | u4 | 15.216 / 15.256 / 15.240 | 15.256 / 15.240 /
15.232 | 1.0000 |
| mode 1 | 16384 | u4 | 196.921 / 196.983 / 196.945 | 193.256 / 193.264
/ 193.192 | 1.0191 |
| mode 0 | 8191 | u4 | 98.752 / 98.776 / 98.728 | 98.824 / 98.728 /
98.743 | 1.0001 |
| mode 0 | 8192 | u4 | 98.800 / 98.816 / 98.752 | 98.776 / 98.752 /
98.783 | 1.0002 |
| mode 0 | 8193 | u4 | 99.056 / 99.017 / 99.032 | 98.647 / 98.616 /
98.576 | 1.0042 |
| mode 1 | 4095 | u4 | 51.824 / 51.840 / 51.872 | 51.832 / 51.840 /
51.864 | 1.0000 |
| mode 1 | 4096 | u4 | 51.856 / 51.776 / 51.928 | 51.824 / 51.816 /
51.768 | 1.0008 |
| mode 1 | 4097 | u4 | 51.976 / 51.888 / 51.880 | 51.527 / 51.624 /
51.456 | 1.0070 |
| alpha tensor + post_weight | 1 | u1 | 2.770 / 2.761 / 2.765 | 2.766 /
2.761 / 2.771 | 0.9998 |
| alpha tensor + post_weight | 128 | u1 | 4.702 / 4.698 / 4.699 | 4.704
/ 4.691 / 4.699 | 1.0000 |
| alpha tensor + post_weight | 2048 | u1 | 32.424 / 32.272 / 32.248 |
32.264 / 32.168 / 32.368 | 1.0002 |
| alpha tensor + post_weight | 16384 | u1 | 236.856 / 236.608 / 236.720
| 237.264 / 236.888 / 236.768 | 0.9993 |
| alpha scalar, no post_weight | 1 | u1 | 2.722 / 2.729 / 2.720 | 2.722
/ 2.716 / 2.719 | 1.0009 |
| alpha scalar, no post_weight | 128 | u1 | 4.759 / 4.760 / 4.776 |
4.765 / 4.764 / 4.764 | 0.9993 |
| alpha scalar, no post_weight | 2048 | u1 | 32.384 / 32.272 / 32.352 |
32.273 / 32.336 / 32.352 | 1.0005 |
| alpha scalar, no post_weight | 16384 | u1 | 237.472 / 236.480 /
236.944 | 237.280 / 237.560 / 237.488 | 0.9977 |
| alpha tensor + post_weight | 511 | u1 | 11.024 / 11.008 / 11.048 |
11.016 / 11.024 / 11.008 | 1.0007 |
| alpha tensor + post_weight | 512 | u1 | 11.008 / 11.056 / 11.032 |
11.008 / 11.024 / 10.984 | 1.0022 |
| alpha tensor + post_weight | 513 | u1 | 11.192 / 11.168 / 11.208 |
11.224 / 11.176 / 11.184 | 1.0007 |
| alpha tensor + post_weight | 831 | u1 | 16.152 / 16.176 / 16.144 |
15.632 / 15.624 / 15.632 | 1.0333 |
| alpha tensor + post_weight | 832 | u1 | 16.168 / 16.136 / 16.136 |
15.704 / 15.672 / 15.696 | 1.0280 |
| alpha tensor + post_weight | 833 | u1 | 15.776 / 15.759 / 15.768 |
15.752 / 15.776 / 15.784 | 0.9995 |
| alpha tensor + post_weight | 958 | u1 | 17.576 / 17.624 / 17.560 |
17.616 / 17.544 / 17.688 | 0.9977 |
| alpha tensor + post_weight | 959 | u1 | 17.632 / 17.632 / 17.664 |
17.640 / 17.576 / 17.616 | 1.0009 |
| alpha tensor + post_weight | 960 | u1 | 17.592 / 17.616 / 17.664 |
17.096 / 17.104 / 17.104 | 1.0299 |
| alpha tensor + post_weight | 3583 | u1 | 55.121 / 55.080 / 55.144 |
55.152 / 55.320 / 55.216 | 0.9983 |
| alpha tensor + post_weight | 3584 | u1 | 54.944 / 55.352 / 55.089 |
54.984 / 55.257 / 55.344 | 0.9970 |
| alpha tensor + post_weight | 3585 | u1 | 56.400 / 56.440 / 56.296 |
56.416 / 56.376 / 56.424 | 0.9997 |
| alpha scalar, no post_weight | 383 | u1 | 8.116 / 8.106 / 8.119 |
8.109 / 8.113 / 8.103 | 1.0009 |
| alpha scalar, no post_weight | 384 | u1 | 8.125 / 8.135 / 8.130 |
8.130 / 8.135 / 8.128 | 0.9999 |
| alpha scalar, no post_weight | 385 | u1 | 7.980 / 7.988 / 7.988 |
7.991 / 7.981 / 7.983 | 1.0006 |
| alpha scalar, no post_weight | 3071 | u1 | 47.048 / 46.944 / 46.984 |
46.328 / 46.360 / 46.392 | 1.0135 |
| alpha scalar, no post_weight | 3072 | u1 | 46.952 / 47.056 / 46.920 |
46.320 / 46.528 / 46.464 | 1.0105 |
| alpha scalar, no post_weight | 3073 | u1 | 46.848 / 46.816 / 46.960 |
46.864 / 46.825 / 46.856 | 0.9998 |
| alpha tensor + post_weight | 1 | u2 | 2.856 / 2.859 / 2.855 | 2.857 /
2.863 / 2.852 | 0.9996 |
| alpha tensor + post_weight | 128 | u2 | 4.775 / 4.774 / 4.774 | 4.775
/ 4.781 / 4.767 | 0.9998 |
| alpha tensor + post_weight | 2048 | u2 | 32.496 / 32.400 / 32.344 |
32.304 / 32.480 / 32.456 | 0.9983 |
| alpha tensor + post_weight | 16384 | u2 | 236.912 / 237.063 / 236.912
| 236.760 / 237.088 / 237.008 | 0.9996 |
| alpha scalar, no post_weight | 1 | u2 | 2.814 / 2.811 / 2.808 | 2.810
/ 2.819 / 2.812 | 0.9998 |
| alpha scalar, no post_weight | 128 | u2 | 4.837 / 4.840 / 4.835 |
4.839 / 4.840 / 4.838 | 0.9995 |
| alpha scalar, no post_weight | 2048 | u2 | 32.504 / 32.568 / 32.512 |
32.456 / 32.488 / 32.456 | 1.0017 |
| alpha scalar, no post_weight | 16384 | u2 | 237.720 / 237.615 /
237.703 | 237.672 / 238.232 / 237.824 | 0.9995 |
| alpha tensor + post_weight | 511 | u2 | 11.120 / 11.088 / 11.104 |
11.064 / 11.080 / 11.096 | 1.0021 |
| alpha tensor + post_weight | 512 | u2 | 11.096 / 11.096 / 11.104 |
11.120 / 11.136 / 11.128 | 0.9971 |
| alpha tensor + post_weight | 513 | u2 | 11.280 / 11.304 / 11.272 |
11.320 / 11.304 / 11.320 | 0.9964 |
| alpha tensor + post_weight | 831 | u2 | 16.120 / 16.096 / 16.120 |
15.712 / 15.784 / 15.768 | 1.0223 |
| alpha tensor + post_weight | 832 | u2 | 16.128 / 16.048 / 16.088 |
15.720 / 15.728 / 15.776 | 1.0229 |
| alpha tensor + post_weight | 833 | u2 | 16.048 / 15.912 / 15.928 |
15.936 / 15.960 / 15.992 | 0.9980 |
| alpha tensor + post_weight | 958 | u2 | 18.072 / 17.936 / 18.040 |
18.096 / 17.872 / 18.040 | 1.0000 |
| alpha tensor + post_weight | 959 | u2 | 17.992 / 18.184 / 18.016 |
18.104 / 18.024 / 18.088 | 0.9960 |
| alpha tensor + post_weight | 960 | u2 | 18.024 / 18.032 / 18.120 |
17.184 / 17.120 / 17.096 | 1.0533 |
| alpha tensor + post_weight | 3583 | u2 | 55.104 / 55.256 / 55.080 |
55.280 / 55.360 / 55.104 | 0.9968 |
| alpha tensor + post_weight | 3584 | u2 | 55.368 / 55.208 / 55.192 |
55.152 / 55.376 / 55.232 | 0.9996 |
| alpha tensor + post_weight | 3585 | u2 | 56.448 / 56.400 / 56.584 |
56.496 / 56.632 / 56.408 | 0.9992 |
| alpha scalar, no post_weight | 383 | u2 | 8.214 / 8.237 / 8.225 |
8.236 / 8.223 / 8.238 | 0.9987 |
| alpha scalar, no post_weight | 384 | u2 | 8.254 / 8.245 / 8.257 |
8.256 / 8.248 / 8.244 | 1.0006 |
| alpha scalar, no post_weight | 385 | u2 | 8.066 / 8.065 / 8.073 |
8.063 / 8.069 / 8.060 | 1.0004 |
| alpha scalar, no post_weight | 3071 | u2 | 47.144 / 47.064 / 47.032 |
46.392 / 46.576 / 46.528 | 1.0115 |
| alpha scalar, no post_weight | 3072 | u2 | 47.040 / 47.056 / 47.072 |
46.408 / 46.544 / 46.616 | 1.0110 |
| alpha scalar, no post_weight | 3073 | u2 | 46.952 / 46.872 / 46.968 |
46.920 / 47.064 / 46.976 | 0.9995 |

**R200 Table 3.** Gated residual next-RMSNorm, alpha tensor + post
weight and alpha scalar without a post weight, NVIDIA R200 (`sm_107a`),
CUDA 13.0, driver 620.62, PDL default. Each kernel is timed alone (CUPTI
kernel-active median, cold L2, memset flush). Previous = the previous
Cake package on FlashInfer main, this PR = this PR's package. The data
come from 6 interleaved sessions on two GPUs, with per-session medians
(s1 / s2 / s3 / s4 / s5 / s6) and a pooled speedup. Rows 2048, 4095 and
4096 of the alpha-scalar route without a post weight are outside this
PR's window and are not shown.

| variant | M | previous us (per session) | this PR us (per session) |
speedup (previous / this PR) |
|---|---|---|---|---|
| alpha tensor + post_weight | 1 | 2.156 / 2.153 / 2.157 / 2.144 / 2.151
/ 2.149 | 2.157 / 2.153 / 2.157 / 2.150 / 2.147 / 2.150 | 1.0003 |
| alpha tensor + post_weight | 128 | 3.747 / 3.754 / 3.749 / 3.764 /
3.763 / 3.758 | 3.752 / 3.754 / 3.754 / 3.759 / 3.763 / 3.758 | 1.0000 |
| alpha tensor + post_weight | 16384 | 126.442 / 126.754 / 127.225 /
123.969 / 123.962 / 123.681 | 117.314 / 117.362 / 117.345 / 117.377 /
117.458 / 117.394 | 1.0668 |
| alpha scalar, no post_weight | 1 | 2.230 / 2.228 / 2.230 / 2.222 /
2.224 / 2.225 | 2.229 / 2.233 / 2.229 / 2.215 / 2.224 / 2.219 | 0.9997 |
| alpha scalar, no post_weight | 128 | 3.679 / 3.675 / 3.676 / 3.688 /
3.690 / 3.694 | 3.677 / 3.674 / 3.674 / 3.688 / 3.687 / 3.690 | 1.0005 |
| alpha scalar, no post_weight | 16384 | 127.241 / 127.034 / 127.097 /
127.017 / 127.202 / 127.202 | 127.345 / 127.482 / 127.465 / 127.329 /
127.481 / 127.161 | 0.9980 |
| alpha tensor + post_weight | 382 | 6.189 / 6.189 / 6.184 / 6.214 /
6.204 / 6.209 | 6.187 / 6.191 / 6.191 / 6.204 / 6.203 / 6.206 | 1.0000 |
| alpha tensor + post_weight | 383 | 6.195 / 6.191 / 6.191 / 6.225 /
6.226 / 6.225 | 6.189 / 6.191 / 6.193 / 6.227 / 6.224 / 6.221 | 1.0005 |
| alpha tensor + post_weight | 384 | 6.234 / 6.239 / 6.237 / 6.252 /
6.245 / 6.258 | 6.194 / 6.199 / 6.195 / 6.208 / 6.211 / 6.210 | 1.0062 |
| alpha tensor + post_weight | 511 | 7.515 / 7.515 / 7.518 / 7.485 /
7.486 / 7.488 | 7.400 / 7.400 / 7.400 / 7.383 / 7.381 / 7.382 | 1.0149 |
| alpha tensor + post_weight | 512 | 7.524 / 7.522 / 7.520 / 7.494 /
7.493 / 7.498 | 7.399 / 7.405 / 7.401 / 7.384 / 7.387 / 7.389 | 1.0155 |
| alpha tensor + post_weight | 513 | 8.554 / 8.564 / 8.555 / 8.616 /
8.613 / 8.613 | 7.434 / 7.437 / 7.436 / 7.458 / 7.459 / 7.457 | 1.1533 |
| alpha tensor + post_weight | 640 | 10.186 / 10.190 / 10.191 / 10.160 /
10.216 / 10.192 | 8.421 / 8.421 / 8.420 / 8.422 / 8.424 / 8.431 | 1.2100
|
| alpha tensor + post_weight | 768 | 10.304 / 10.312 / 10.304 / 10.496 /
10.552 / 10.536 | 9.616 / 9.611 / 9.615 / 9.643 / 9.642 / 9.644 | 1.0805
|
| alpha tensor + post_weight | 1024 | 12.136 / 12.128 / 12.152 / 12.185
/ 12.160 / 12.176 | 11.712 / 11.720 / 11.736 / 11.784 / 11.776 / 11.776
| 1.0340 |
| alpha tensor + post_weight | 1279 | 14.552 / 14.553 / 14.544 / 14.616
/ 14.560 / 14.616 | 13.904 / 13.888 / 13.896 / 13.888 / 13.888 / 13.904
| 1.0478 |
| alpha tensor + post_weight | 1280 | 14.552 / 14.552 / 14.528 / 14.616
/ 14.528 / 14.544 | 13.952 / 13.952 / 13.928 / 13.904 / 13.880 / 13.912
| 1.0451 |
| alpha tensor + post_weight | 1281 | 14.664 / 14.648 / 14.656 / 14.656
/ 14.696 / 14.696 | 14.240 / 14.224 / 14.168 / 14.376 / 14.472 / 14.416
| 1.0246 |
| alpha tensor + post_weight | 8192 | 61.809 / 61.793 / 61.793 / 61.769
/ 61.480 / 61.593 | 60.889 / 60.905 / 60.880 / 61.025 / 60.992 / 61.025
| 1.0137 |
| alpha scalar, no post_weight | 382 | 5.778 / 5.769 / 5.769 / 5.800 /
5.801 / 5.798 | 5.772 / 5.784 / 5.779 / 5.797 / 5.801 / 5.790 | 1.0001 |
| alpha scalar, no post_weight | 383 | 5.781 / 5.775 / 5.778 / 5.801 /
5.800 / 5.799 | 5.768 / 5.769 / 5.772 / 5.803 / 5.793 / 5.800 | 1.0013 |
| alpha scalar, no post_weight | 384 | 5.783 / 5.779 / 5.779 / 5.808 /
5.807 / 5.805 | 5.770 / 5.768 / 5.769 / 5.792 / 5.802 / 5.794 | 1.0022 |
| alpha scalar, no post_weight | 640 | 7.860 / 7.857 / 7.863 / 7.867 /
7.870 / 7.864 | 7.764 / 7.759 / 7.751 / 7.764 / 7.772 / 7.766 | 1.0128 |
| alpha scalar, no post_weight | 768 | 8.940 / 8.942 / 8.944 / 8.972 /
8.974 / 8.964 | 8.759 / 8.764 / 8.757 / 8.799 / 8.792 / 8.798 | 1.0201 |
| alpha scalar, no post_weight | 1024 | 11.032 / 11.016 / 11.048 /
11.064 / 11.064 / 11.040 | 10.744 / 10.760 / 10.729 / 10.744 / 10.736 /
10.728 | 1.0283 |
| alpha scalar, no post_weight | 4097 | 35.664 / 35.729 / 35.753 /
35.681 / 35.649 / 35.640 | 35.600 / 35.576 / 35.560 / 35.529 / 35.529 /
35.528 | 1.0036 |
| alpha scalar, no post_weight | 8192 | 65.953 / 66.009 / 65.937 /
65.936 / 65.922 / 65.905 | 65.945 / 65.952 / 65.905 / 65.904 / 65.809 /
65.872 | 1.0005 |

The package also ships the gated residual RMSNorm PDL routes, the alpha
scalar + post weight route of the next-RMSNorm kernel and the RMSNorm +
sigmoid gate kernel unchanged, and covers `sm_100a`, `sm_103a` and
`sm_107a` only.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected normalization calculations that skipped or misaligned BF16
input pairs, ensuring all values contribute to the result.
* **New Features**
* Expanded Muse Spark normalization support with additional GPU-specific
execution paths and occupancy queries.
* **Tests**
* Updated API coverage for revised routing behavior, row ranges, and
supported GPU execution forms.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [f319fc1](https://github.com/flashinfer-ai/flashinfer/commit/f319fc1addc66319f52b798e9ca6602751bf3dcc)

- **作者**: eigen
- **时间**: 2026-10-29T18:04:18Z
- **提交信息**: perf(cake_fmha): GB300 FP8 context programs keep P in the other stage's S columns, B200 smaller-pack split plans (#7839)

FlashInfer main ships Cake paged context (prefill) attention in
`flashinfer.cake_fmha`, reached through
`flashinfer.prefill.trtllm_batch_context_with_kv_cache(...,
backend="cake")`. Its FP8 programs include exact programs. One takes
host scales and the other reads the attention scales from device
tensors. They also include runtime-size programs
`RUNTIME_PACK<g>[_PAGE64]` and split-KV runtime-size programs (g = 1, 2,
4, 8 query heads per KV head). A host planner with a fitted cost model
per target chooses among the runtime-size programs. On GB300 (sm_103a),
the exact FP8 programs already use a 4-stage K/V ring (`B256_KV4`,
`B256_SCALE_PTR_KV4`).

This PR makes two changes. On GB300 (sm_103a), it adds 10 FP8 programs,
the `_PX` builds: `B256_PX`, `B256_SCALE_PTR_PX`, `RUNTIME_PACK<g>_PX`
and `RUNTIME_PACK<g>_PAGE64_PX`. They use a 4-stage K/V ring. Each stage
keeps its P tile (the softmax probabilities fed to the P·V MMA) in the
tensor-memory columns of the other stage's score tile, which that stage
no longer needs. This is what lets the runtime-size programs take 4
stages. sm_103a now routes the exact and runtime-size FP8 launches to
the `_PX` programs, and its cost model is refit for them. Short launches
keep the previous programs. Exact launches of at most 256 keys keep
`B256_KV4` / `B256_SCALE_PTR_KV4`. Runtime-size launches of at most 128
keys keep the 3-stage `RUNTIME_PACK<g>[_PAGE64]` programs. On B200
(sm_100a), the programs are unchanged. The FP8 split-KV planner may now
serve a launch that spans more than one m-block (query tile) with the
split plan of a smaller pack (fewer query heads per KV head per CTA). It
does this only when that pack holds the launch in one m-block and its
tiles fit in one wave of CTAs. With more than one wave of tiles, the
smaller pack was not faster overall, so it is not offered there. The
split-KV programs are unchanged. Against FlashInfer main, 16 of the 44
GB300 shapes are faster, 1.024x to 1.124x. All of them are FP8 shapes
that now run a `_PX` program. On B200, one shape changes plan (FP8, B=2,
q=128, kv=1500, heads 32/4, page 16) and measures 1.037x. Every other
shape keeps its program and plan and measures 0.999x to 1.003x. That is
noise. Outputs of launches that keep their plan are bitwise identical to
FlashInfer main. The trtllm-gen columns are given for reference.

| Shape (paged KV, head dim 128) | B200 previous (µs) | B200 this PR
(µs) | B200 speedup | B200 trtllm-gen (µs) | GB300 previous (µs) | GB300
this PR (µs) | GB300 speedup | GB300 trtllm-gen (µs) |
|---|---:|---:|---|---:|---:|---:|---|---:|
| BF16, B=1, q=8192, kv=8192, heads 64/8, page 16 | 896.88 | 896.42 |
1.000x (min 0.999x) | 1067.07 | 614.01 | 614.28 | 1.000x (min 0.995x) |
674.17 |
| BF16, B=4, q=511, kv=2047, heads 10/2, page 32 | 34.50 | 34.50 |
1.000x (min 0.999x) | 37.66 | 27.01 | 27.01 | 1.000x (min 1.000x) |
30.21 |
| BF16, B=128, q=64, kv=2048, heads 32/4, page 16 | 242.18 | 242.11 |
1.001x (min 0.999x) | 1013.96 | 178.24 | 177.69 | 1.003x (min 0.998x) |
721.16 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64 | 109.89 | 109.79 |
1.000x (min 1.000x) | 783.51 | 85.39 | 83.39 | 1.024x (min 1.022x) |
514.08 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16 | 57.79 |
57.81 | 1.001x (min 0.999x) | 62.19 | 51.23 | 51.23 | 1.000x (min
1.000x) | 52.27 |
| BF16, B=4, q=257, kv=1024, heads 10/2, page 1024 | 20.86 | 20.83 |
1.002x (min 1.000x) | 23.14 | 16.96 | 16.96 | 1.000x (min 1.000x) |
18.48 |
| FP8, B=256, q=64, kv=1024, heads 32/4, page 64 | 203.84 | 203.86 |
1.000x (min 0.998x) | 795.65 | 162.91 | 147.46 | 1.104x (min 1.103x) |
524.73 |
| FP8, B=128, q=128, kv=1024, heads 32/8, page 64 | 203.66 | 203.39 |
1.000x (min 0.999x) | 410.99 | 162.75 | 147.30 | 1.105x (min 1.104x) |
282.46 |
| FP8, B=256, q=32, kv=1024, heads 128/1, page 64 | 393.05 | 392.81 |
1.001x (min 0.999x) | 3092.46 | 300.03 | 268.82 | 1.118x (min 1.115x) |
1986.01 |
| FP8, B=16, q=256, kv=2048, heads 32/32, page 64 | 115.66 | 115.74 |
1.000x (min 0.998x) | 116.29 | 97.92 | 87.12 | 1.124x (min 1.123x) |
93.15 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16 | 110.77 | 110.88 |
1.000x (min 0.998x) | 788.74 | 94.27 | 86.02 | 1.096x (min 1.094x) |
532.57 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 16, device scales | 110.85
| 110.91 | 0.999x (min 0.999x) | 800.35 | 94.11 | 85.87 | 1.096x (min
1.094x) | 577.15 |
| FP8, B=2, q=300, kv=1500, heads 32/4, page 16 | 25.68 | 25.70 | 1.000x
(min 0.999x) | 26.77 | 21.68 | 19.70 | 1.098x (min 1.098x) | 19.90 |
| FP8, B=256, q=32, kv=1024, heads 32/4, page 64, device scales | 109.58
| 109.57 | 1.000x (min 0.999x) | 795.50 | 85.22 | 83.31 | 1.024x (min
1.023x) | 558.98 |
| FP8 Q / NVFP4 KV, B=4, q=511, kv=2047, heads 32/4, page 16, device
scales | 57.92 | 57.94 | 1.000x (min 0.999x) | 79.78 | 51.40 | 51.46 |
1.000x (min 0.999x) | 94.30 |
| BF16, B=1, q=64, kv=16384, heads 32/4, page 16 | 195.62 | 195.68 |
1.000x (min 1.000x) | 215.18 | 158.02 | 158.02 | 1.000x (min 1.000x) |
191.68 |
| BF16, B=one wave of CTAs (18 on B200, 19 on GB300), q=64, kv=2048,
heads 32/4, page 16 | 37.18 | 37.25 | 1.000x (min 0.998x) | 135.06 |
32.70 | 32.70 | 1.000x (min 0.998x) | 108.80 |
| FP8, B=1, q=300, kv=1500, heads 32/4, page 16 | 24.51 | 24.51 | 1.000x
(min 0.999x) | 25.34 | 21.47 | 19.52 | 1.100x (min 1.098x) | 19.01 |
| FP8, B=2, q=300, kv=3000, heads 32/4, page 16 | 41.92 | 41.92 | 1.000x
(min 0.999x) | 45.92 | 34.11 | 32.38 | 1.057x (min 1.053x) | 33.28 |
| FP8, B=2, q=300, kv=6000, heads 32/4, page 16 | 72.94 | 72.96 | 1.000x
(min 0.999x) | 81.47 | 59.97 | 55.65 | 1.077x (min 1.075x) | 58.56 |
| FP8, B=2, q=128, kv=1500, heads 32/4, page 16 | 24.85 | 23.94 | 1.037x
(min 1.034x) | 24.61 | 21.70 | 19.65 | 1.102x (min 1.100x) | 18.75 |
| FP8, B=16, q=256, kv=4096, heads 32/32, page 64 | 204.30 | 204.34 |
1.000x (min 0.999x) | 221.95 | 172.77 | 157.12 | 1.100x (min 1.096x) |
169.63 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 64 | 44.67 | 44.67 | 1.000x
(min 1.000x) | 187.36 | 39.42 | 39.42 | 1.000x (min 1.000x) | 138.05 |
| FP8, B=1, q=32, kv=4096, heads 32/4, page 64 | 27.39 | 27.42 | 0.999x
(min 0.999x) | 51.55 | 23.78 | 23.78 | 1.000x (min 1.000x) | 38.11 |
| FP8, B=1, q=32, kv=8192, heads 32/4, page 64 | 33.28 | 33.31 | 1.000x
(min 0.999x) | 96.99 | 29.79 | 29.79 | 1.000x (min 0.999x) | 71.58 |
| FP8, B=1, q=32, kv=32768, heads 32/4, page 64 | 59.30 | 59.26 | 1.000x
(min 1.000x) | 366.38 | 52.74 | 52.72 | 1.000x (min 1.000x) | 272.32 |
| FP8, B=2, q=32, kv=16384, heads 32/4, page 64 | 48.42 | 48.42 | 1.000x
(min 0.999x) | 188.99 | 41.70 | 41.66 | 1.001x (min 1.000x) | 139.73 |
| FP8, B=4, q=32, kv=16384, heads 32/4, page 64 | 54.50 | 54.50 | 1.000x
(min 0.999x) | 191.95 | 49.02 | 49.02 | 1.000x (min 1.000x) | 142.69 |
| FP8, B=8, q=32, kv=8192, heads 32/4, page 64 | 47.39 | 47.46 | 0.999x
(min 0.999x) | 198.58 | 42.34 | 42.34 | 1.000x (min 0.999x) | 146.82 |
| FP8, B=1, q=128, kv=16384, heads 32/4, page 64 | 52.70 | 52.74 |
1.000x (min 0.999x) | 188.42 | 45.76 | 45.76 | 1.000x (min 1.000x) |
138.59 |
| FP8, B=1, q=512, kv=16384, heads 32/4, page 64 | 116.42 | 116.42 |
1.000x (min 0.999x) | 195.33 | 93.31 | 93.31 | 1.000x (min 1.000x) |
140.64 |
| FP8, B=2, q=300, kv=2000, heads 32/4, page 16 | 29.86 | 29.86 | 1.000x
(min 1.000x) | 33.34 | 25.70 | 24.06 | 1.072x (min 1.066x) | 24.45 |
| FP8, B=1, q=300, kv=3000, heads 32/4, page 16 | 31.04 | 31.04 | 1.000x
(min 0.998x) | 43.84 | 27.20 | 27.20 | 1.000x (min 1.000x) | 31.95 |
| FP8, B=16, q=256, kv=3072, heads 32/32, page 64 | 160.77 | 160.70 |
1.000x (min 0.998x) | 166.24 | 135.81 | 122.13 | 1.110x (min 1.109x) |
131.49 |
| FP8, B=1, q=32, kv=2048, heads 32/4, page 64 | 20.83 | 20.83 | 1.000x
(min 0.999x) | 28.29 | 18.62 | 18.62 | 1.000x (min 1.000x) | 21.15 |
| FP8, B=1, q=32, kv=12000, heads 32/4, page 64 | 40.03 | 40.05 | 1.000x
(min 0.999x) | 139.78 | 34.77 | 34.75 | 1.000x (min 1.000x) | 102.72 |
| FP8, B=3, q=32, kv=16384, heads 32/4, page 64 | 52.54 | 52.54 | 1.000x
(min 0.999x) | 190.77 | 47.28 | 47.26 | 1.000x (min 0.999x) | 141.14 |
| FP8, B=16, q=32, kv=16384, heads 32/4, page 64 | 120.66 | 120.58 |
1.000x (min 0.999x) | 764.55 | 102.03 | 102.02 | 1.000x (min 1.000x) |
543.03 |
| FP8, B=1, q=256, kv=16384, heads 32/4, page 64 | 71.46 | 71.47 |
1.000x (min 0.999x) | 193.47 | 58.59 | 58.62 | 0.999x (min 0.999x) |
139.71 |
| FP8, B=1, q=32, kv=16384, heads 32/8, page 64 | 45.18 | 45.18 | 1.000x
(min 1.000x) | 188.74 | 40.26 | 40.26 | 1.000x (min 1.000x) | 147.10 |
| FP8, B=1, q=32, kv=16384, heads 64/8, page 64 | 47.71 | 47.71 | 1.000x
(min 0.999x) | 188.99 | 41.54 | 41.50 | 1.001x (min 1.001x) | 139.49 |
| FP8, B=1, q=32, kv=16384, heads 16/2, page 64 | 43.17 | 43.20 | 1.000x
(min 0.999x) | 187.01 | 38.11 | 38.14 | 1.000x (min 0.999x) | 137.28 |
| FP8, B=1, q=32, kv=16384, heads 32/4, page 16 | 45.17 | 45.18 | 1.000x
(min 1.000x) | 189.63 | 39.68 | 39.68 | 1.000x (min 1.000x) | 143.71 |
| FP8, B=1, q=256, kv=8192, heads 32/32, page 64 | 47.23 | 47.23 |
1.000x (min 1.000x) | 103.65 | 42.13 | 42.14 | 1.000x (min 1.000x) |
81.22 |

Previous = FlashInfer main; this PR = the branch head; trtllm-gen = the
`trtllm-gen` backend on the same inputs. B200: NVIDIA B200 (sm_100a,
compute capability 10.0, 148 SMs), driver 580.82.07, PyTorch 2.14.1 with
the CUDA 13.0 runtime, CUDA 13.4 toolkit. GB300: NVIDIA GB300 (sm_103a,
compute capability 10.3, 152 SMs), driver 580.159.03, PyTorch 2.14.1
with the CUDA 13.0 runtime, CUDA 13.4 toolkit. Times are the median over
5 address layouts of each layout's median of 6 rounds (cold L2); speedup
= median over layouts of previous/this PR, with the minimum layout in
parentheses (above 1 = this PR faster).

In FlashInfer, Cake ships this context attention family for BF16 KV, FP8
(Q, KV and output) and NVFP4 KV (FP8 Q), with paged KV at page sizes 16
to 1024, on sm_100a (B200) and sm_103a (GB300), and Cake also ships
paged decode attention in `flashinfer.cake_fmha`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optimized FP8 context-attention execution paths for `sm103a`
GPUs, including support for runtime sequence lengths and PAGE64
configurations.
  * Added dedicated handling for short key/value sequences.

* **Improvements**
* Updated attention route and split selection to better match workload
size and GPU execution constraints, which may improve performance across
supported configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [19af158](https://github.com/flashinfer-ai/flashinfer/commit/19af158f301893c44d6f555e0557aed31064b4b7)

- **作者**: eigen
- **时间**: 2026-10-29T18:04:03Z
- **提交信息**: perf(gdn): sm_120 slot calls read and write state rows as element pairs (#7837)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR follows #7785 and #7795. On RTX PRO 6000, paged prefill with
bf16 state was slower than the in-place no-ckpt reference in
`benchmarks/bench_gdn_paged_state.py`. fp32 state did not have this gap.
At ecdae59b (#7795, mean of 2 runs), bf16 `64x reuse 16K + 256` took
0.4683 ms paged vs 0.4153 ms no-ckpt. That row has no page checkpoint,
so each sequence reads one row and writes one row: the same bytes as
no-ckpt. bf16 `4x reuse` was 0.1899 vs 0.1767 ms, and `16x reuse` was
0.3753 vs 0.3479 ms. With fp32 state, `64x reuse` was 0.4755 vs 0.4764
ms. With this PR, bf16 `64x reuse` paged goes from 0.4672 to 0.3766 ms.
That is now 0.907 of the no-ckpt time, down from 1.129.

**Cause** (Nsight Compute 2026.3.1, bf16 `64x reuse`, caches flushed:
paged 474.1 us, no-ckpt 425.5 us)

- Both specializations read and write the state one element at a time:
64 `LDG.E.U16` and 64 `STG.E.U16` per thread. The pool strides are
dynamic, so each access has its own 64-bit address. `F2FP.PACK_AB` +
`PRMT` feed the stores.
- In the slot specialization, the final-store block holds 20.2 % of the
warp samples (no-ckpt: 17.8 %). The stalls are long scoreboard on the
`PRMT`s that overwrite registers still read by queued `STG.U16`, and LSU
throttle. The state-load block holds 11.2 % vs 8.6 %.
- fp32 stores need no `PRMT` split. The final-store block holds 8.6–9.0
% in both arms, so fp32 has no gap.
- In the `4x reuse` and `16x reuse` rows, the last block writes the last
checkpoint (the final state) through the element-wise slot store. The
run checkpoints are already written as pairs.

**Change**

- Some slot calls have a state or initial state with dense `[H, D, D]`
rows, i.e. inner strides `(D*D, D, 1)`. These are pool rows with
`state_indices`, or packed per-sequence states. These calls now read the
initial state and write the final state as 2-element vector accesses
through a view with static inner strides. `kv_load_pairs` is new.
`kv_store_pairs` is the same path that the pool-row checkpoints already
use.
- The first-block and last-block pool-row checkpoints now go through
`store_slot_checkpoint_run`, so they are also written as pairs, like the
run checkpoints.
- The host computes the alignment in elements of the state rows and the
initial-state rows (base address and row stride, from
`checkpoint_row_align` of the tensor). It passes these values as the
compile-key attributes `state_row_align` / `init_state_row_align`, and
only for slot calls.
- The kernel writes the same values to the same addresses, so results
are bitwise equal.
- Nsight Compute, same row, with the state load/store part of the change
alone: 474.1 -> 380.3 us. Global load/store instructions go from
1.20M/1.05M to 0.68M/0.52M, and L2 write sectors from 12.79M to 8.59M.

**Scope**

- Changed files:
`flashinfer/gdn_kernels/delta_rule_dsl/delta_rule_sm120.py` (+177 / -33)
and `tests/gdn/test_paged_state.py` (+391).
- Old calls (no slot arguments) compile to the same kernel. PTX, SASS
and cubin are identical to main for 10 of 10 direct-entry specs, and for
23 of 23 specs in a second set that adds 13 bench-shaped public-API
specs.
- `_FullyFusedDeltaRuleSm80` has its own `__init__`,
`kv_load`/`kv_store`, `run_math_role` and host function, so the SM80
code does not change.
- The context-parallel kernels do not subclass this class.
- Pools whose rows are not aligned to 2 elements keep the element-wise
path.
- SM121 dispatches to this kernel. I did not run this PR on SM121
hardware.

### Performance

Setup: RTX PRO 6000 Blackwell Server Edition (sm_120, 188 SMs), driver
595.84.01, torch 2.14.1+cu130, CUDA 13.0, nvidia-cutlass-dsl 4.8.1.
Script: `benchmarks/bench_gdn_paged_state.py`, heads q/k/v = (16, 16,
32), `page_size=1024`. "Before" is ecdae59b, whose GDN files are the
same as main. "After" is this PR. I ran each tree 4 times, interleaved,
with the GPU otherwise idle. Values are medians. The mean SM clock was
2408 MHz (min 2340), mean power was 340 W, and there were no clock event
reasons. Rows `1x new 8K` to `64x reuse` compare paged with packed+copy.
Rows `1x 32K` to `64x 1K` compare selected with all+gather. Speedup is
the other time divided by the paged or selected time.

**float32 state**

| workload | paged / selected ms (before -> after) | packed+copy /
all+gather ms | speedup | no-ckpt ms | paged / no-ckpt |
|---|---:|---:|---:|---:|---:|
| 1x new 8K | 0.6513 -> 0.6487 | 0.6635 -> 0.6630 | 1.019 -> 1.022 |
0.6362 -> 0.6364 | 1.024 -> 1.019 |
| 4x reuse 4K + 2K | 0.1882 -> 0.1838 | 0.2114 -> 0.2118 | 1.123 ->
1.152 | 0.1730 -> 0.1738 | 1.088 -> 1.058 |
| 16x reuse 8K + 1K | 0.3711 -> 0.3540 | 0.4675 -> 0.4679 | 1.260 ->
1.322 | 0.3467 -> 0.3473 | 1.070 -> 1.020 |
| 8x mixed | 0.4803 -> 0.4662 | 0.5730 -> 0.5723 | 1.193 -> 1.228 |
0.4571 -> 0.4567 | 1.051 -> 1.021 |
| 64x reuse 16K + 256 | 0.4750 -> 0.4670 | 0.8395 -> 0.8395 | 1.767 ->
1.797 | 0.4777 -> 0.4779 | 0.994 -> 0.977 |
| 1x 32K | 2.6770 -> 2.6741 | 3.5227 -> 3.5206 | 1.316 -> 1.317 | 2.5568
-> 2.5571 | |
| 8x 8K | 1.4827 -> 1.4777 | 2.9749 -> 2.9765 | 2.006 -> 2.014 | 1.4373
-> 1.4373 | |
| 32x 2K | 1.2525 -> 1.2531 | 2.9154 -> 2.9166 | 2.328 -> 2.328 | 1.2011
-> 1.2009 | |
| 64x 1K | 1.3022 -> 1.3001 | 2.9923 -> 2.9914 | 2.298 -> 2.301 | 1.2067
-> 1.2067 | |

**bfloat16 state**

| workload | paged / selected ms (before -> after) | packed+copy /
all+gather ms | speedup | no-ckpt ms | paged / no-ckpt |
|---|---:|---:|---:|---:|---:|
| 1x new 8K | 0.6549 -> 0.6492 | 0.6903 -> 0.6905 | 1.054 -> 1.063 |
0.6392 -> 0.6391 | 1.025 -> 1.016 |
| 4x reuse 4K + 2K | 0.1898 -> 0.1801 | 0.2203 -> 0.2199 | 1.160 ->
1.221 | 0.1767 -> 0.1763 | 1.074 -> 1.022 |
| 16x reuse 8K + 1K | 0.3759 -> 0.3464 | 0.4628 -> 0.4626 | 1.231 ->
1.335 | 0.3474 -> 0.3485 | 1.082 -> 0.994 |
| 8x mixed | 0.4798 -> 0.4617 | 0.5556 -> 0.5560 | 1.158 -> 1.204 |
0.4584 -> 0.4568 | 1.047 -> 1.011 |
| 64x reuse 16K + 256 | 0.4672 -> 0.3766 | 0.6043 -> 0.6052 | 1.293 ->
1.607 | 0.4139 -> 0.4150 | 1.129 -> 0.907 |
| 1x 32K | 2.6774 -> 2.6753 | 4.3253 -> 4.3223 | 1.615 -> 1.616 | 2.5568
-> 2.5571 | |
| 8x 8K | 1.4835 -> 1.4746 | 2.8105 -> 2.8136 | 1.895 -> 1.908 | 1.4371
-> 1.4371 | |
| 32x 2K | 1.2372 -> 1.2329 | 2.5046 -> 2.5052 | 2.024 -> 2.032 | 1.2008
-> 1.2008 | |
| 64x 1K | 1.2511 -> 1.2531 | 2.5130 -> 2.5133 | 2.009 -> 2.006 | 1.2064
-> 1.2069 | |

- No cell of 0.01 ms or more is more than 0.5 % slower (means over
runs).
- The slowest cell of the changed kernel is bf16 `64x 1K` selected, at
+0.2 %.
- The slowest old-call cells are fp32 `4x reuse` no-ckpt (+0.4 %) and
bf16 `64x reuse` no-ckpt (+0.3 %). The kernels for these cells are
identical before and after.
- The decode rows do not change beyond noise. This PR does not change
the decode kernels.

### Validation

All runs on RTX PRO 6000 (sm_120).

- Tests:
- `tests/gdn/test_paged_state.py` +
`tests/gdn/test_prefill_state_indices.py`: 225 passed / 93 skipped / 0
failed (216 existing + 9 new).
- Full `tests/gdn`: 4594 passed / 2011 skipped. This is the same as main
with the new test file added. 0 outcome differences.
- New tests (SM120 only; on other architectures they are skipped with a
reason):
- `test_sm120_slot_state_rows_at_every_alignment` (fp32, bf16, fp16,
e4m3fn, e5m2 state). It uses pools whose rows are aligned to 16 bytes
and to every power of two from 1 element up to that.
`checkpoint_row_align` asserts each alignment. The test uses one shared
pool for all roles, then initial, final and checkpoint pools with
different alignments, and then the first pools again (bitwise equal).
The calls use `state_indices`, `output_state_indices`,
`checkpoint_state_indices` (one `-1` entry) and `prefix_lens`. The
sequences cover: no prefix, a partial page read and written in place, no
final state, and no new tokens. Rows that a call must not write, and the
row padding, keep their contents. The results match the oracle. Finally,
`output_state_indices` alone at maximal alignment is bitwise equal to
alignment 1.
- `test_sm120_packed_slot_states_match_pool_rows` (bf16, fp16, e4m3fn,
e5m2 state). Packed per-sequence initial and final states with
`prefix_lens` are bitwise equal to the same call on 1-element-aligned
pool rows. The results also match the oracle.
- The fp8 oracle checks use the whole-tensor relative error: < 0.1 for
e4m3 and < 0.2 for e5m2. The other dtypes use the existing tolerances of
the file. No existing tolerance changes.
- Bitwise results:
- Every bench arm variant (15) on the 9 bench workloads, one call from a
reset state: 310 of 310 tensors equal before vs after, fp32 and bf16.
- Hash of every SM120 call in `test_paged_state.py` +
`test_prefill_state_indices.py`: 3275 of 3275 tensors equal.
- New tests: 72 SM120 calls, 930 of 930 tensors equal between main and
this PR.
- Determinism: 40 identical calls from a reset state, run serially and
in two concurrent processes. This covered fp32 and bf16 state, and slot
and old-call variants. 198 records, 1 distinct result each.
- compute-sanitizer 2025.3.1 on the 9 new tests: memcheck 0 errors,
racecheck 0 hazards.
- 64-bit offset probes: big16 9/9, big32 9/9 and empty_out 3/3 pass, the
same as before.

## 🔍 Related Issues

Follow-up to #7785 and #7795. Related: #2873.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

I did not run `pre-commit run --all-files` or mypy. I ran ruff 0.12.8
(`ruff check` and `ruff format --check`), and both are clean.

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
reviewers may adjust): `tests/gdn/test_paged_state.py
tests/gdn/test_prefill_state_indices.py`

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

- Old calls (no slot arguments) compile to the same kernel. PTX, SASS
and cubin are identical to main for every old-call spec checked.
- `_FullyFusedDeltaRuleSm80` has its own `__init__`,
`kv_load`/`kv_store`, `run_math_role` and host function, so the SM80
code does not change.
- Pools whose rows are not aligned to 2 elements keep the element-wise
path. The new alignment test covers alignment 1 and every power of two
up to 16 bytes.
- SM121 dispatches to this kernel, but I did not run this PR on SM121
hardware.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Improvements**
* Improved slot-based state handling across a wider range of row
alignments, including for initial, final, and checkpoint states.
* Added paired access for aligned state data while retaining existing
access for unaligned data.
* Expanded validation across supported state types and routing
configurations, including checks for outputs, stored states, and
untouched memory regions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bd98569](https://github.com/flashinfer-ai/flashinfer/commit/bd98569258195ae57f7d10ad26b949adcac9c65b)

- **作者**: eigen
- **时间**: 2026-10-29T18:03:47Z
- **提交信息**: perf(cake_dense_projection_gemm): eight-warp CTA program for the SM100a 4096 -> 512, 4096 -> 1024, 5120 -> 512, 5120 -> 1024 and 6144 -> 576 input-gradient rows (#7835)

The Cake `dense_projection_gemm` kernel has 127 programs built from 124
templates. Its 120 dense templates take BF16 operands and write BF16
output (82) or FP32 output (38) in four operand layouts (`kk`, `kn`,
`nk`, `nn`). The FP32 router GEMM runs through BF16x3 emulation. This PR
adds the knob-free eight-warp CTA form as one new `sm_100a` program,
`dense_proj_gemm_kn_n256_tma1_w8`. Every other `sm_100a` program of the
kernel uses the ten-warp pipeline. The new program computes the
BF16-output input gradient in the `kn` layout. It serves five rows:
4096→512, 4096→1024, 5120→512, 5120→1024 and kv_a (6144→576). The
baseline is the previous Cake program of each of these rows, which is
one ten-warp program for all five. On 4096→512, latency drops from 51.9
to 50.6 µs at T = 16231 token rows (1.025) and from 52.0 to 50.6 µs at T
= 16384 (1.028). On 4096→1024, it drops from 95.0 to 93.9 µs at T =
16231 (1.012) and from 94.9 to 93.7 µs at T = 16384 (1.013). On
5120→512, it drops from 66.8 to 64.1 µs at T = 16231 (1.042) and from
66.7 to 64.0 µs at T = 16384 (1.041). On 5120→1024, it drops from 115.8
to 113.6 µs at T = 16231 (1.019) and from 116.0 to 114.0 µs at T = 16384
(1.017). On kv_a, it drops from 86.1 to 84.6 µs at T = 16172 (1.018) and
from 86.3 to 84.4 µs at T = 16231 (1.022). The other 284 rows keep their
previous programs.

Every variant listed above ships in this package, which has programs for
`sm_100a` (GB200), `sm_103a` (GB300) and `sm_107a`: 254 build entries
(81 / 86 / 87) and 127 registry records, up from 253 (80 / 86 / 87) and
126 in the previous version; the added entry is the new `sm_100a`
program, and the eight-warp CTA form now ships on `sm_100a` (one
knob-free program) and `sm_103a` (two programs). (BF16 and FP32 outputs,
K-major and MN-major operand layouts, row-major and transposed outputs,
64 / 128 / 256-row tiles, batched head-projection, split-tail and
stream-K forms, the whole-tile tile resolve, the paced output stores,
the `sm_103a` eight-warp programs, and the FP32 router GEMM through
BF16x3 emulation are the other variants, 126 further programs.)

**NVIDIA GB200 (sm_100a), driver 580.126.20, CUDA 13.4 (nvcc 13.4.92);
node nvl72137-T15. Cold-L2 CUPTI GPU time per iteration, median of 5
alternating groups × 20 iterations, both sides in the same session.
Latency in µs; speedup = previous version / this PR.**

| shape (K→N) | op | out | T | baseline | baseline µs | this PR µs |
speedup |
|---|---|---|---:|---|---:|---:|---:|
| indexer_q (2048→4096) | dgrad | bf16 | 16172 | previous version |
176.9 | 176.1 | 1.005 |
| indexer_q (2048→4096) | dgrad | bf16 | 16231 | previous version |
176.3 | 176.7 | 0.998 |
| indexer_q (2048→4096) | fwd | bf16 | 16172 | previous version | 172.1
| 172.5 | 0.998 |
| indexer_q (2048→4096) | fwd | bf16 | 16231 | previous version | 172.9
| 173.1 | 0.999 |
| indexer_q (2048→4096) | wgrad | bf16 | 16172 | previous version |
181.7 | 181.5 | 1.001 |
| indexer_q (2048→4096) | wgrad | bf16 | 16231 | previous version |
182.4 | 182.3 | 1.000 |
| indexer_q (2048→4096) | wgrad | f32 | 16172 | previous version | 179.9
| 180.3 | 0.998 |
| indexer_q (2048→4096) | wgrad | f32 | 16231 | previous version | 180.8
| 181.1 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16172 | previous version |
262.0 | 262.2 | 0.999 |
| shared_down (2048→6144) | dgrad | bf16 | 16231 | previous version |
260.2 | 259.8 | 1.001 |
| shared_down (2048→6144) | dgrad | f32 | 16172 | previous version |
265.4 | 266.5 | 0.996 |
| shared_down (2048→6144) | dgrad | f32 | 16231 | previous version |
267.1 | 263.2 | 1.015 |
| shared_down (2048→6144) | fwd | bf16 | 16172 | previous version |
254.1 | 253.2 | 1.003 |
| shared_down (2048→6144) | fwd | bf16 | 16231 | previous version |
250.3 | 250.2 | 1.000 |
| shared_down (2048→6144) | wgrad | bf16 | 16172 | previous version |
266.1 | 266.2 | 1.000 |
| shared_down (2048→6144) | wgrad | bf16 | 16231 | previous version |
263.9 | 259.5 | 1.017 |
| shared_down (2048→6144) | wgrad | f32 | 16172 | previous version |
264.4 | 267.6 | 0.988 |
| shared_down (2048→6144) | wgrad | f32 | 16231 | previous version |
266.5 | 267.4 | 0.997 |
| q_b (2048→16384) | dgrad | bf16 | 16172 | previous version | 668.5 |
656.9 | 1.018 |
| q_b (2048→16384) | dgrad | bf16 | 16231 | previous version | 657.1 |
657.9 | 0.999 |
| q_b (2048→16384) | dgrad | f32 | 16172 | previous version | 657.0 |
656.7 | 1.000 |
| q_b (2048→16384) | dgrad | f32 | 16231 | previous version | 658.5 |
657.7 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16172 | previous version | 622.2 |
621.5 | 1.001 |
| q_b (2048→16384) | fwd | bf16 | 16231 | previous version | 622.7 |
624.3 | 0.998 |
| q_b (2048→16384) | wgrad | bf16 | 16172 | previous version | 645.2 |
644.4 | 1.001 |
| q_b (2048→16384) | wgrad | bf16 | 16231 | previous version | 647.6 |
647.5 | 1.000 |
| q_b (2048→16384) | wgrad | f32 | 16172 | previous version | 660.5 |
657.5 | 1.005 |
| q_b (2048→16384) | wgrad | f32 | 16231 | previous version | 661.9 |
662.6 | 0.999 |
| 4096→32 | dgrad | bf16 | 16231 | previous version | 23.9 | 23.9 |
1.001 |
| 4096→32 | dgrad | bf16 | 16384 | previous version | 24.4 | 24.2 |
1.006 |
| 4096→32 | dgrad | f32 | 16231 | previous version | 44.9 | 44.6 | 1.008
|
| 4096→32 | dgrad | f32 | 16384 | previous version | 45.1 | 45.0 | 1.001
|
| 4096→32 | fwd | bf16 | 16231 | previous version | 26.4 | 26.4 | 0.999
|
| 4096→32 | fwd | bf16 | 16384 | previous version | 26.2 | 26.1 | 1.001
|
| 4096→32 | wgrad | bf16 | 16231 | previous version | 28.3 | 28.2 |
1.003 |
| 4096→32 | wgrad | bf16 | 16384 | previous version | 28.1 | 28.0 |
1.003 |
| 4096→32 | wgrad | f32 | 16231 | previous version | 28.3 | 28.3 | 1.000
|
| 4096→32 | wgrad | f32 | 16384 | previous version | 28.0 | 28.1 | 0.997
|
| 4096→48 | dgrad | bf16 | 16231 | previous version | 24.5 | 24.5 |
1.000 |
| 4096→48 | dgrad | bf16 | 16384 | previous version | 24.6 | 24.6 |
0.997 |
| 4096→48 | dgrad | f32 | 16231 | previous version | 45.0 | 44.9 | 1.001
|
| 4096→48 | dgrad | f32 | 16384 | previous version | 45.5 | 45.4 | 1.004
|
| 4096→48 | fwd | bf16 | 16231 | previous version | 26.5 | 26.4 | 1.002
|
| 4096→48 | fwd | bf16 | 16384 | previous version | 26.2 | 26.3 | 0.998
|
| 4096→48 | wgrad | bf16 | 16231 | previous version | 28.4 | 28.4 |
1.000 |
| 4096→48 | wgrad | bf16 | 16384 | previous version | 28.3 | 28.2 |
1.003 |
| 4096→48 | wgrad | f32 | 16231 | previous version | 28.3 | 28.3 | 0.999
|
| 4096→48 | wgrad | f32 | 16384 | previous version | 28.5 | 28.4 | 1.003
|
| 4096→64 | dgrad | bf16 | 16231 | previous version | 24.4 | 24.4 |
1.000 |
| 4096→64 | dgrad | bf16 | 16384 | previous version | 24.5 | 24.5 |
0.999 |
| 4096→64 | dgrad | f32 | 16231 | previous version | 45.2 | 45.4 | 0.996
|
| 4096→64 | dgrad | f32 | 16384 | previous version | 45.4 | 45.4 | 0.999
|
| 4096→64 | fwd | bf16 | 16231 | previous version | 26.7 | 26.7 | 1.000
|
| 4096→64 | fwd | bf16 | 16384 | previous version | 26.6 | 26.5 | 1.004
|
| 4096→64 | wgrad | bf16 | 16231 | previous version | 28.6 | 28.8 |
0.992 |
| 4096→64 | wgrad | bf16 | 16384 | previous version | 28.3 | 28.4 |
0.996 |
| 4096→64 | wgrad | f32 | 16231 | previous version | 28.7 | 28.8 | 0.998
|
| 4096→64 | wgrad | f32 | 16384 | previous version | 28.6 | 28.4 | 1.004
|
| 4096→128 | dgrad | bf16 | 16231 | previous version | 25.6 | 25.7 |
0.998 |
| 4096→128 | dgrad | bf16 | 16384 | previous version | 25.8 | 25.9 |
0.998 |
| 4096→128 | dgrad | f32 | 16231 | previous version | 47.3 | 47.2 |
1.003 |
| 4096→128 | dgrad | f32 | 16384 | previous version | 47.6 | 47.4 |
1.004 |
| 4096→128 | fwd | bf16 | 16231 | previous version | 27.5 | 27.5 | 1.001
|
| 4096→128 | fwd | bf16 | 16384 | previous version | 27.2 | 27.2 | 1.002
|
| 4096→128 | wgrad | bf16 | 16231 | previous version | 29.5 | 29.5 |
0.999 |
| 4096→128 | wgrad | bf16 | 16384 | previous version | 29.1 | 29.2 |
0.998 |
| 4096→128 | wgrad | f32 | 16231 | previous version | 29.4 | 29.4 |
0.998 |
| 4096→128 | wgrad | f32 | 16384 | previous version | 29.3 | 29.2 |
1.003 |
| 4096→512 | dgrad | bf16 | 16231 | previous version | 51.9 | 50.6 |
1.025 |
| 4096→512 | dgrad | bf16 | 16384 | previous version | 52.0 | 50.6 |
1.028 |
| 4096→512 | dgrad | f32 | 16231 | previous version | 72.0 | 71.9 |
1.002 |
| 4096→512 | dgrad | f32 | 16384 | previous version | 72.1 | 72.0 |
1.000 |
| 4096→512 | fwd | bf16 | 16231 | previous version | 57.5 | 57.4 | 1.002
|
| 4096→512 | fwd | bf16 | 16384 | previous version | 57.5 | 57.3 | 1.003
|
| 4096→512 | wgrad | bf16 | 16231 | previous version | 52.5 | 52.5 |
0.999 |
| 4096→512 | wgrad | bf16 | 16384 | previous version | 53.3 | 53.2 |
1.002 |
| 4096→512 | wgrad | f32 | 16231 | previous version | 52.5 | 52.4 |
1.001 |
| 4096→512 | wgrad | f32 | 16384 | previous version | 52.9 | 53.0 |
0.998 |
| 4096→1024 | dgrad | bf16 | 16231 | previous version | 95.0 | 93.9 |
1.012 |
| 4096→1024 | dgrad | bf16 | 16384 | previous version | 94.9 | 93.7 |
1.013 |
| 4096→1024 | fwd | bf16 | 16231 | previous version | 97.0 | 97.4 |
0.996 |
| 4096→1024 | fwd | bf16 | 16384 | previous version | 97.1 | 97.2 |
0.998 |
| 4096→1024 | wgrad | bf16 | 16231 | previous version | 97.7 | 98.0 |
0.996 |
| 4096→1024 | wgrad | bf16 | 16384 | previous version | 98.3 | 98.7 |
0.996 |
| 4096→1024 | wgrad | f32 | 16231 | previous version | 99.6 | 99.9 |
0.996 |
| 4096→1024 | wgrad | f32 | 16384 | previous version | 100.6 | 100.3 |
1.003 |
| 4096→4096 | dgrad | bf16 | 16231 | previous version | 318.8 | 324.0 |
0.984 |
| 4096→4096 | dgrad | bf16 | 16384 | previous version | 320.0 | 319.3 |
1.002 |
| 4096→4096 | fwd | bf16 | 16231 | previous version | 320.1 | 320.0 |
1.000 |
| 4096→4096 | fwd | bf16 | 16384 | previous version | 320.3 | 320.9 |
0.998 |
| 4096→4096 | wgrad | bf16 | 16231 | previous version | 339.4 | 333.6 |
1.017 |
| 4096→4096 | wgrad | bf16 | 16384 | previous version | 335.4 | 335.4 |
1.000 |
| 4096→4096 | wgrad | f32 | 16231 | previous version | 335.7 | 335.1 |
1.002 |
| 4096→4096 | wgrad | f32 | 16384 | previous version | 337.3 | 337.0 |
1.001 |
| 4096→12288 | dgrad | bf16 | 16231 | previous version | 942.3 | 941.9 |
1.000 |
| 4096→12288 | dgrad | bf16 | 16384 | previous version | 943.3 | 946.4 |
0.997 |
| 4096→12288 | fwd | bf16 | 16231 | previous version | 905.2 | 905.9 |
0.999 |
| 4096→12288 | fwd | bf16 | 16384 | previous version | 905.6 | 894.5 |
1.012 |
| 4096→12288 | wgrad | bf16 | 16231 | previous version | 941.6 | 939.4 |
1.002 |
| 4096→12288 | wgrad | bf16 | 16384 | previous version | 948.4 | 946.9 |
1.002 |
| 4096→12288 | wgrad | f32 | 16231 | previous version | 940.9 | 938.5 |
1.003 |
| 4096→12288 | wgrad | f32 | 16384 | previous version | 949.1 | 959.5 |
0.989 |
| 5120→32 | dgrad | bf16 | 16231 | previous version | 28.7 | 28.6 |
1.002 |
| 5120→32 | dgrad | bf16 | 16384 | previous version | 29.2 | 29.1 |
1.002 |
| 5120→32 | dgrad | f32 | 16231 | previous version | 53.5 | 53.5 | 0.999
|
| 5120→32 | dgrad | f32 | 16384 | previous version | 54.2 | 54.1 | 1.001
|
| 5120→32 | fwd | bf16 | 16231 | previous version | 31.4 | 31.4 | 1.003
|
| 5120→32 | fwd | bf16 | 16384 | previous version | 32.2 | 32.2 | 0.998
|
| 5120→32 | wgrad | bf16 | 16231 | previous version | 32.9 | 33.0 |
0.996 |
| 5120→32 | wgrad | bf16 | 16384 | previous version | 33.4 | 33.6 |
0.992 |
| 5120→32 | wgrad | f32 | 16231 | previous version | 32.8 | 33.0 | 0.996
|
| 5120→32 | wgrad | f32 | 16384 | previous version | 33.4 | 33.2 | 1.004
|
| 5120→48 | dgrad | bf16 | 16231 | previous version | 29.1 | 29.0 |
1.003 |
| 5120→48 | dgrad | bf16 | 16384 | previous version | 29.4 | 29.3 |
1.002 |
| 5120→48 | dgrad | f32 | 16231 | previous version | 54.2 | 54.3 | 0.998
|
| 5120→48 | dgrad | f32 | 16384 | previous version | 54.8 | 54.7 | 1.003
|
| 5120→48 | fwd | bf16 | 16231 | previous version | 31.4 | 31.5 | 0.999
|
| 5120→48 | fwd | bf16 | 16384 | previous version | 32.1 | 32.2 | 0.997
|
| 5120→48 | wgrad | bf16 | 16231 | previous version | 33.6 | 33.5 |
1.002 |
| 5120→48 | wgrad | bf16 | 16384 | previous version | 34.2 | 34.2 |
0.998 |
| 5120→48 | wgrad | f32 | 16231 | previous version | 33.7 | 33.7 | 1.000
|
| 5120→48 | wgrad | f32 | 16384 | previous version | 34.2 | 33.9 | 1.008
|
| 5120→64 | dgrad | bf16 | 16231 | previous version | 29.2 | 29.2 |
0.999 |
| 5120→64 | dgrad | bf16 | 16384 | previous version | 29.4 | 29.4 |
0.998 |
| 5120→64 | dgrad | f32 | 16231 | previous version | 54.7 | 54.5 | 1.004
|
| 5120→64 | dgrad | f32 | 16384 | previous version | 54.9 | 54.8 | 1.002
|
| 5120→64 | fwd | bf16 | 16231 | previous version | 32.0 | 31.9 | 1.002
|
| 5120→64 | fwd | bf16 | 16384 | previous version | 32.6 | 32.6 | 0.998
|
| 5120→64 | wgrad | bf16 | 16231 | previous version | 33.7 | 33.7 |
0.999 |
| 5120→64 | wgrad | bf16 | 16384 | previous version | 33.8 | 33.8 |
1.000 |
| 5120→64 | wgrad | f32 | 16231 | previous version | 33.6 | 33.7 | 0.997
|
| 5120→64 | wgrad | f32 | 16384 | previous version | 33.9 | 33.9 | 0.999
|
| 5120→128 | dgrad | bf16 | 16231 | previous version | 31.0 | 31.0 |
1.003 |
| 5120→128 | dgrad | bf16 | 16384 | previous version | 30.8 | 30.9 |
0.997 |
| 5120→128 | dgrad | f32 | 16231 | previous version | 56.9 | 56.9 |
0.999 |
| 5120→128 | dgrad | f32 | 16384 | previous version | 57.2 | 57.2 |
1.000 |
| 5120→128 | fwd | bf16 | 16231 | previous version | 33.2 | 33.3 | 0.998
|
| 5120→128 | fwd | bf16 | 16384 | previous version | 32.9 | 32.8 | 1.001
|
| 5120→128 | wgrad | bf16 | 16231 | previous version | 34.1 | 34.3 |
0.997 |
| 5120→128 | wgrad | bf16 | 16384 | previous version | 34.7 | 34.7 |
1.001 |
| 5120→128 | wgrad | f32 | 16231 | previous version | 34.3 | 34.1 |
1.005 |
| 5120→128 | wgrad | f32 | 16384 | previous version | 34.7 | 34.6 |
1.003 |
| 5120→512 | dgrad | bf16 | 16231 | previous version | 66.8 | 64.1 |
1.042 |
| 5120→512 | dgrad | bf16 | 16384 | previous version | 66.7 | 64.0 |
1.041 |
| 5120→512 | dgrad | f32 | 16231 | previous version | 88.7 | 88.7 |
1.000 |
| 5120→512 | dgrad | f32 | 16384 | previous version | 88.5 | 88.4 |
1.001 |
| 5120→512 | fwd | bf16 | 16231 | previous version | 71.9 | 71.9 | 0.999
|
| 5120→512 | fwd | bf16 | 16384 | previous version | 72.4 | 72.0 | 1.005
|
| 5120→512 | wgrad | bf16 | 16231 | previous version | 71.3 | 71.4 |
0.999 |
| 5120→512 | wgrad | bf16 | 16384 | previous version | 71.7 | 71.7 |
1.000 |
| 5120→512 | wgrad | f32 | 16231 | previous version | 71.4 | 71.7 |
0.996 |
| 5120→512 | wgrad | f32 | 16384 | previous version | 72.7 | 72.3 |
1.006 |
| 5120→1024 | dgrad | bf16 | 16231 | previous version | 115.8 | 113.6 |
1.019 |
| 5120→1024 | dgrad | bf16 | 16384 | previous version | 116.0 | 114.0 |
1.017 |
| 5120→1024 | fwd | bf16 | 16231 | previous version | 118.0 | 118.4 |
0.996 |
| 5120→1024 | fwd | bf16 | 16384 | previous version | 118.8 | 118.3 |
1.004 |
| 5120→1024 | wgrad | bf16 | 16231 | previous version | 124.1 | 124.1 |
1.000 |
| 5120→1024 | wgrad | bf16 | 16384 | previous version | 125.5 | 124.9 |
1.005 |
| 5120→1024 | wgrad | f32 | 16231 | previous version | 125.7 | 125.5 |
1.001 |
| 5120→1024 | wgrad | f32 | 16384 | previous version | 126.6 | 126.2 |
1.003 |
| 5120→5120 | dgrad | bf16 | 16231 | previous version | 492.4 | 491.2 |
1.002 |
| 5120→5120 | dgrad | bf16 | 16384 | previous version | 493.9 | 493.7 |
1.000 |
| 5120→5120 | fwd | bf16 | 16231 | previous version | 491.8 | 491.1 |
1.002 |
| 5120→5120 | fwd | bf16 | 16384 | previous version | 492.9 | 492.2 |
1.001 |
| 5120→5120 | wgrad | bf16 | 16231 | previous version | 498.8 | 498.5 |
1.000 |
| 5120→5120 | wgrad | bf16 | 16384 | previous version | 503.3 | 503.7 |
0.999 |
| 5120→5120 | wgrad | f32 | 16231 | previous version | 500.1 | 500.5 |
0.999 |
| 5120→5120 | wgrad | f32 | 16384 | previous version | 505.2 | 506.4 |
0.998 |
| 5120→17408 | dgrad | bf16 | 16231 | previous version | 1640.0 | 1649.7
| 0.994 |
| 5120→17408 | dgrad | bf16 | 16384 | previous version | 1647.1 | 1657.3
| 0.994 |
| 5120→17408 | fwd | bf16 | 16231 | previous version | 1580.5 | 1596.2 |
0.990 |
| 5120→17408 | fwd | bf16 | 16384 | previous version | 1602.3 | 1635.8 |
0.980 |
| 5120→17408 | wgrad | bf16 | 16231 | previous version | 1602.9 | 1614.8
| 0.993 |
| 5120→17408 | wgrad | bf16 | 16384 | previous version | 1629.0 | 1649.2
| 0.988 |
| 5120→17408 | wgrad | f32 | 16231 | previous version | 1605.0 | 1620.5
| 0.990 |
| 5120→17408 | wgrad | f32 | 16384 | previous version | 1619.7 | 1624.2
| 0.997 |
| indexer_hw (6144→32) | dgrad | bf16 | 16172 | previous version | 34.7
| 34.3 | 1.012 |
| indexer_hw (6144→32) | dgrad | bf16 | 16231 | previous version | 34.4
| 34.3 | 1.002 |
| indexer_hw (6144→32) | dgrad | f32 | 16172 | previous version | 61.3 |
61.3 | 1.001 |
| indexer_hw (6144→32) | dgrad | f32 | 16231 | previous version | 61.5 |
61.6 | 0.998 |
| indexer_hw (6144→32) | fwd | bf16 | 16172 | previous version | 37.1 |
37.0 | 1.001 |
| indexer_hw (6144→32) | fwd | bf16 | 16231 | previous version | 37.0 |
37.1 | 0.999 |
| indexer_hw (6144→32) | wgrad | bf16 | 16172 | previous version | 38.1
| 38.2 | 0.999 |
| indexer_hw (6144→32) | wgrad | bf16 | 16231 | previous version | 38.2
| 38.1 | 1.001 |
| indexer_hw (6144→32) | wgrad | f32 | 16172 | previous version | 38.2 |
38.0 | 1.006 |
| indexer_hw (6144→32) | wgrad | f32 | 16231 | previous version | 38.1 |
38.2 | 1.000 |
| indexer_k (6144→128) | dgrad | bf16 | 16172 | previous version | 35.9
| 36.0 | 0.998 |
| indexer_k (6144→128) | dgrad | bf16 | 16231 | previous version | 36.1
| 36.2 | 0.998 |
| indexer_k (6144→128) | dgrad | f32 | 16172 | previous version | 66.6 |
66.5 | 1.001 |
| indexer_k (6144→128) | dgrad | f32 | 16231 | previous version | 66.6 |
66.4 | 1.003 |
| indexer_k (6144→128) | fwd | bf16 | 16172 | previous version | 38.6 |
38.6 | 0.998 |
| indexer_k (6144→128) | fwd | bf16 | 16231 | previous version | 38.5 |
38.5 | 1.001 |
| indexer_k (6144→128) | wgrad | bf16 | 16172 | previous version | 39.3
| 39.4 | 0.998 |
| indexer_k (6144→128) | wgrad | bf16 | 16231 | previous version | 39.4
| 39.4 | 1.001 |
| indexer_k (6144→128) | wgrad | f32 | 16172 | previous version | 39.2 |
39.2 | 0.999 |
| indexer_k (6144→128) | wgrad | f32 | 16231 | previous version | 39.3 |
39.4 | 0.998 |
| kv_a (6144→576) | dgrad | bf16 | 16172 | previous version | 86.1 |
84.6 | 1.018 |
| kv_a (6144→576) | dgrad | bf16 | 16231 | previous version | 86.3 |
84.4 | 1.022 |
| kv_a (6144→576) | dgrad | f32 | 16172 | previous version | 110.9 |
111.0 | 0.999 |
| kv_a (6144→576) | dgrad | f32 | 16231 | previous version | 111.5 |
111.3 | 1.002 |
| kv_a (6144→576) | fwd | bf16 | 16172 | previous version | 95.9 | 96.4
| 0.996 |
| kv_a (6144→576) | fwd | bf16 | 16231 | previous version | 96.1 | 96.4
| 0.996 |
| kv_a (6144→576) | wgrad | bf16 | 16172 | previous version | 85.6 |
85.8 | 0.999 |
| kv_a (6144→576) | wgrad | bf16 | 16231 | previous version | 85.9 |
85.7 | 1.002 |
| kv_a (6144→576) | wgrad | f32 | 16172 | previous version | 87.1 | 87.3
| 0.998 |
| kv_a (6144→576) | wgrad | f32 | 16231 | previous version | 87.4 | 87.3
| 1.002 |
| q_a (6144→2048) | dgrad | bf16 | 16172 | previous version | 253.6 |
249.3 | 1.018 |
| q_a (6144→2048) | dgrad | bf16 | 16231 | previous version | 251.4 |
254.6 | 0.988 |
| q_a (6144→2048) | dgrad | f32 | 16172 | previous version | 263.4 |
262.5 | 1.003 |
| q_a (6144→2048) | dgrad | f32 | 16231 | previous version | 264.0 |
262.9 | 1.004 |
| q_a (6144→2048) | fwd | bf16 | 16172 | previous version | 255.7 |
253.3 | 1.010 |
| q_a (6144→2048) | fwd | bf16 | 16231 | previous version | 253.8 |
254.3 | 0.998 |
| q_a (6144→2048) | wgrad | bf16 | 16172 | previous version | 263.0 |
263.0 | 1.000 |
| q_a (6144→2048) | wgrad | bf16 | 16231 | previous version | 263.2 |
263.2 | 1.000 |
| q_a (6144→2048) | wgrad | f32 | 16172 | previous version | 264.5 |
264.4 | 1.001 |
| q_a (6144→2048) | wgrad | f32 | 16231 | previous version | 265.4 |
264.9 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16172 | previous version |
251.7 | 251.2 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | bf16 | 16231 | previous version |
251.4 | 250.9 | 1.002 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16172 | previous version |
264.0 | 263.7 | 1.001 |
| shared_gate_up (6144→2048) | dgrad | f32 | 16231 | previous version |
263.6 | 263.8 | 0.999 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16172 | previous version |
253.7 | 254.2 | 0.998 |
| shared_gate_up (6144→2048) | fwd | bf16 | 16231 | previous version |
255.0 | 254.4 | 1.003 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16172 | previous version |
262.7 | 262.6 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | bf16 | 16231 | previous version |
263.9 | 264.0 | 1.000 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16172 | previous version |
264.3 | 264.0 | 1.001 |
| shared_gate_up (6144→2048) | wgrad | f32 | 16231 | previous version |
265.1 | 265.3 | 0.999 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16172 | previous version |
1378.1 | 1379.0 | 0.999 |
| dense_gate_up (6144→12288) | wgrad | bf16 | 16231 | previous version |
1373.3 | 1371.6 | 1.001 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16172 | previous version |
1384.8 | 1393.8 | 0.994 |
| dense_gate_up (6144→12288) | wgrad | f32 | 16231 | previous version |
1375.0 | 1335.9 | 1.029 |
| 8192→128 | dgrad | bf16 | 16231 | previous version | 47.4 | 50.8 |
0.934 |
| 8192→128 | dgrad | bf16 | 16384 | previous version | 47.7 | 47.7 |
1.000 |
| 8192→128 | dgrad | f32 | 16231 | previous version | 90.7 | 90.8 |
0.999 |
| 8192→128 | dgrad | f32 | 16384 | previous version | 90.0 | 90.0 |
1.000 |
| 8192→128 | fwd | bf16 | 16231 | previous version | 48.9 | 48.8 | 1.001
|
| 8192→128 | fwd | bf16 | 16384 | previous version | 49.5 | 49.4 | 1.001
|
| 8192→128 | wgrad | bf16 | 16231 | previous version | 45.1 | 45.2 |
0.999 |
| 8192→128 | wgrad | bf16 | 16384 | previous version | 45.6 | 45.5 |
1.001 |
| 8192→128 | wgrad | f32 | 16231 | previous version | 45.0 | 45.2 |
0.997 |
| 8192→128 | wgrad | f32 | 16384 | previous version | 45.4 | 45.3 |
1.002 |
| 12288→4096 | dgrad | bf16 | 16231 | previous version | 907.1 | 909.4 |
0.998 |
| 12288→4096 | dgrad | bf16 | 16384 | previous version | 904.1 | 924.6 |
0.978 |
| 12288→4096 | fwd | bf16 | 16231 | previous version | 938.5 | 932.3 |
1.007 |
| 12288→4096 | fwd | bf16 | 16384 | previous version | 935.3 | 947.0 |
0.988 |
| 12288→4096 | wgrad | bf16 | 16231 | previous version | 903.7 | 923.5 |
0.979 |
| 12288→4096 | wgrad | bf16 | 16384 | previous version | 937.9 | 929.5 |
1.009 |
| 12288→4096 | wgrad | f32 | 16231 | previous version | 936.2 | 917.7 |
1.020 |
| 12288→4096 | wgrad | f32 | 16384 | previous version | 943.6 | 932.1 |
1.012 |
| dense_down (12288→6144) | wgrad | bf16 | 16172 | previous version |
1366.7 | 1338.5 | 1.021 |
| dense_down (12288→6144) | wgrad | bf16 | 16231 | previous version |
1370.3 | 1358.5 | 1.009 |
| dense_down (12288→6144) | wgrad | f32 | 16172 | previous version |
1379.3 | 1359.9 | 1.014 |
| dense_down (12288→6144) | wgrad | f32 | 16231 | previous version |
1369.1 | 1350.8 | 1.014 |
| o_proj (16384→6144) | dgrad | bf16 | 16172 | previous version | 1889.4
| 1811.4 | 1.043 |
| o_proj (16384→6144) | dgrad | bf16 | 16231 | previous version | 1823.7
| 1831.7 | 0.996 |
| o_proj (16384→6144) | dgrad | f32 | 16172 | previous version | 1853.1
| 1841.1 | 1.007 |
| o_proj (16384→6144) | dgrad | f32 | 16231 | previous version | 1850.6
| 1868.5 | 0.990 |
| o_proj (16384→6144) | fwd | bf16 | 16172 | previous version | 1839.5 |
1816.6 | 1.013 |
| o_proj (16384→6144) | fwd | bf16 | 16231 | previous version | 1866.0 |
1850.5 | 1.008 |
| o_proj (16384→6144) | wgrad | bf16 | 16172 | previous version | 1765.6
| 1773.2 | 0.996 |
| o_proj (16384→6144) | wgrad | bf16 | 16231 | previous version | 1909.7
| 1802.2 | 1.060 |
| o_proj (16384→6144) | wgrad | f32 | 16172 | previous version | 1786.0
| 1777.5 | 1.005 |
| o_proj (16384→6144) | wgrad | f32 | 16231 | previous version | 1824.0
| 1820.2 | 1.002 |
| 17408→5120 | dgrad | bf16 | 16231 | previous version | 1605.1 | 1605.4
| 1.000 |
| 17408→5120 | dgrad | bf16 | 16384 | previous version | 1657.4 | 1635.2
| 1.014 |
| 17408→5120 | fwd | bf16 | 16231 | previous version | 1629.4 | 1603.8 |
1.016 |
| 17408→5120 | fwd | bf16 | 16384 | previous version | 1614.0 | 1627.3 |
0.992 |
| 17408→5120 | wgrad | bf16 | 16231 | previous version | 1616.5 | 1601.8
| 1.009 |
| 17408→5120 | wgrad | bf16 | 16384 | previous version | 1619.4 | 1611.3
| 1.005 |
| 17408→5120 | wgrad | f32 | 16231 | previous version | 1614.7 | 1609.1
| 1.004 |
| 17408→5120 | wgrad | f32 | 16384 | previous version | 1625.8 | 1615.9
| 1.006 |
| qabs | dgrad | bf16 | 16172 | previous version | 241.9 | 241.6 | 1.001
|
| qabs | dgrad | bf16 | 16231 | previous version | 239.1 | 239.1 | 1.000
|
| qabs | fwd | bf16 | 16172 | previous version | 266.6 | 266.7 | 0.999 |
| qabs | fwd | bf16 | 16231 | previous version | 275.4 | 275.3 | 1.000 |
| qabs | wgrad | bf16 | 16172 | previous version | 216.3 | 216.1 | 1.001
|
| qabs | wgrad | bf16 | 16231 | previous version | 217.6 | 217.6 | 1.000
|
| vproj | dgrad | bf16 | 16172 | previous version | 290.2 | 290.3 |
1.000 |
| vproj | dgrad | bf16 | 16231 | previous version | 291.3 | 291.8 |
0.998 |
| vproj | fwd | bf16 | 16172 | previous version | 264.3 | 264.6 | 0.999
|
| vproj | fwd | bf16 | 16231 | previous version | 267.1 | 266.9 | 1.001
|
| vproj | wgrad | bf16 | 16172 | previous version | 237.6 | 237.2 |
1.002 |
| vproj | wgrad | bf16 | 16231 | previous version | 238.5 | 238.0 |
1.002 |
| router 4096→256 | dgrad | f32 | 16231 | previous version | 189.5 |
191.6 | 0.989 |
| router 4096→256 | fwd | f32 | 16231 | previous version | 194.1 | 194.1
| 1.000 |
| router 4096→256 | wgrad | f32 | 16231 | previous version | 189.3 |
190.3 | 0.995 |
| router 5120→256 | dgrad | f32 | 16231 | previous version | 237.2 |
237.0 | 1.000 |
| router 5120→256 | fwd | f32 | 16231 | previous version | 228.9 | 228.3
| 1.003 |
| router 5120→256 | wgrad | f32 | 16231 | previous version | 238.5 |
239.0 | 0.998 |
| router 6144→256 | dgrad | f32 | 16172 | previous version | 273.0 |
272.7 | 1.001 |
| router 6144→256 | dgrad | f32 | 16231 | previous version | 274.5 |
274.2 | 1.001 |
| router 6144→256 | fwd | f32 | 16172 | previous version | 264.5 | 264.9
| 0.998 |
| router 6144→256 | fwd | f32 | 16231 | previous version | 263.2 | 262.8
| 1.002 |
| router 6144→256 | wgrad | f32 | 16172 | previous version | 252.5 |
252.0 | 1.002 |
| router 6144→256 | wgrad | f32 | 16231 | previous version | 252.3 |
251.8 | 1.002 |

<!-- generated by g6_w8_table_r10.py from fibench_gb200.json sha256
3ea8a3a2ddf0d6897c5fdb3424691f5200d4643bc5d69e349bdcb0d6639886f1; run
run-gb200-r10d-w8; NEW a49462c104dc83f72138bc73ef08e249189ff1cb (package
tree dd3d87a527f8dad84402211ea3dc2b910ccc082e) PREV
1af7b1146a8d30ac6e082923b7bd4b37bc486bbd (package tree
6078719736daea6dddf9d9fb0336c825c8be7c82); rows whose program changes:
4096->512|dgrad|bf16|T16231: dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 4096->512|dgrad|bf16|T16384:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 4096->1024|dgrad|bf16|T16231:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 4096->1024|dgrad|bf16|T16384:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 5120->512|dgrad|bf16|T16231:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 5120->512|dgrad|bf16|T16384:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 5120->1024|dgrad|bf16|T16231:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; 5120->1024|dgrad|bf16|T16384:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; kv_a|dgrad|bf16|T16172:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8; kv_a|dgrad|bf16|T16231:
dense_proj_gemm_kn_n256_tma1_pd2_pro15 ->
dense_proj_gemm_kn_n256_tma1_w8 -->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for an eight-warp dense projection GEMM program on SM100
GPUs, including a knob-free option for five input-gradient rows.
* Expanded eight-warp program support for SM103 GPUs handling three
input-gradient rows.
* **Performance**
* Updated selected input-gradient workloads on SM100 to use the
eight-warp program, including a 6144-to-576 shape.
* **Documentation**
* Updated the dense projection GEMM guide with the new program options
and architecture support.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b83db54](https://github.com/flashinfer-ai/flashinfer/commit/b83db5402c91a0a1fb252e4af9423d52b5beebeb)

- **作者**: eigen
- **时间**: 2026-10-29T18:03:29Z
- **提交信息**: perf(cake_sampling): GB300 and B200 host launch choices for two cells (#7830)

`cake_sampling` is FlashInfer's Cake top-k/top-p sampling from float32
probability rows (`top_k_top_p_sampling_from_probs` with a Philox
seed/offset). Stage 1 is a radix top-k select, and stages 2/3
renormalize the sparse top-p set and sample from it. Stage-1 builds come
in resident and streaming forms, with clusters of 1, 2, 4 or 8 CTAs and
4 to 48 entries per thread; below, (cluster, ept) names a stream by
cluster size and entries per thread. This PR follows #7750 (round 17) on
main and changes only two host launch rules. It adds no build and leaves
the kernel source unchanged, so every target compiles to the same
kernels as on main. On GB300 with 152 SMs, vocab 151936 with 128 rows at
top-k 769 up to the fused-tail cap (1024) now runs the (1, 32) stream's
integer-tested whole-CTA tail in one launch instead of a two-launch
chain. On B200, vocab 24577-32768 with 33-64 rows at top-k 21-50 now
runs the (1, 16) stream instead of the cost model's (1, 32) pick, and
65-128 rows keep the cost model's pick. In the shape list below, each
rule changes two rows: top-k 1000, vocab 151936, batch 128 on GB300, and
top-k 50, vocab 32768, batch 64 on B200 (eager and graph). Every other
row keeps main's launch choice.

Speedup against #7750 on GB300 (sm_103a) and B200 (sm_100a), CUDA 13.4,
over 192 shapes per GPU: top-k {10, 50, 1000} x vocab {32768, 128256,
151936, 262144} x batch {1, 2, 4, 8, 16, 32, 64, 128} x mode {eager,
graph}. The per-shape tables with absolute latencies follow.

| GPU | rows whose launch choice changes | speedup on those rows | other
rows |
|---|---:|---:|---:|
| GB300 | 2 | 1.155x-1.166x | 0.997x-1.016x (190 rows) |
| B200 | 2 | 1.019x-1.021x | 0.999x-1.001x (190 rows) |

<details>
<summary>GB300 (sm_103a): all 192 shapes</summary>

NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 (nvcc 13.4.92), PyTorch
2.14.1+cu130. Baseline: the `cake_sampling` module on FlashInfer main
(round 17, #7750). Latency in µs of one sampling call (median CUPTI time
from a cold L2 over 12 rounds after a warm-up round, contiguous float32
probability rows); speedup = baseline / this PR, the median of the 12
per-round paired ratios.

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 10 | 32768 | 1 | eager | 6.976 | 6.976 | 1.000x |
| 10 | 32768 | 1 | graph | 7.120 | 7.136 | 1.000x |
| 10 | 32768 | 2 | eager | 7.072 | 7.072 | 1.000x |
| 10 | 32768 | 2 | graph | 7.360 | 7.360 | 1.000x |
| 10 | 32768 | 4 | eager | 7.136 | 7.136 | 1.000x |
| 10 | 32768 | 4 | graph | 7.424 | 7.424 | 1.000x |
| 10 | 32768 | 8 | eager | 7.264 | 7.264 | 1.000x |
| 10 | 32768 | 8 | graph | 7.520 | 7.520 | 1.000x |
| 10 | 32768 | 16 | eager | 7.520 | 7.520 | 1.000x |
| 10 | 32768 | 16 | graph | 7.776 | 7.776 | 1.000x |
| 10 | 32768 | 32 | eager | 8.064 | 8.064 | 1.000x |
| 10 | 32768 | 32 | graph | 8.320 | 8.320 | 1.000x |
| 10 | 32768 | 64 | eager | 9.664 | 9.664 | 1.000x |
| 10 | 32768 | 64 | graph | 9.888 | 9.888 | 1.000x |
| 10 | 32768 | 128 | eager | 10.720 | 10.720 | 1.000x |
| 10 | 32768 | 128 | graph | 10.944 | 10.944 | 1.000x |
| 10 | 128256 | 1 | eager | 7.936 | 7.936 | 1.000x |
| 10 | 128256 | 1 | graph | 8.096 | 8.096 | 1.000x |
| 10 | 128256 | 2 | eager | 8.064 | 8.064 | 1.000x |
| 10 | 128256 | 2 | graph | 8.304 | 8.320 | 1.000x |
| 10 | 128256 | 4 | eager | 8.224 | 8.224 | 1.000x |
| 10 | 128256 | 4 | graph | 8.512 | 8.512 | 1.000x |
| 10 | 128256 | 8 | eager | 8.608 | 8.608 | 1.000x |
| 10 | 128256 | 8 | graph | 8.864 | 8.864 | 1.000x |
| 10 | 128256 | 16 | eager | 10.368 | 10.368 | 1.000x |
| 10 | 128256 | 16 | graph | 10.656 | 10.656 | 1.000x |
| 10 | 128256 | 32 | eager | 11.552 | 11.552 | 1.000x |
| 10 | 128256 | 32 | graph | 11.840 | 11.840 | 1.000x |
| 10 | 128256 | 64 | eager | 14.688 | 14.688 | 1.000x |
| 10 | 128256 | 64 | graph | 14.992 | 15.008 | 1.000x |
| 10 | 128256 | 128 | eager | 20.768 | 20.768 | 1.000x |
| 10 | 128256 | 128 | graph | 20.984 | 20.992 | 1.000x |
| 10 | 151936 | 1 | eager | 8.800 | 8.800 | 1.000x |
| 10 | 151936 | 1 | graph | 8.992 | 8.992 | 1.000x |
| 10 | 151936 | 2 | eager | 8.880 | 8.880 | 1.000x |
| 10 | 151936 | 2 | graph | 9.120 | 9.120 | 1.000x |
| 10 | 151936 | 4 | eager | 9.120 | 9.120 | 1.000x |
| 10 | 151936 | 4 | graph | 9.408 | 9.408 | 1.000x |
| 10 | 151936 | 8 | eager | 9.536 | 9.536 | 1.000x |
| 10 | 151936 | 8 | graph | 9.824 | 9.824 | 1.000x |
| 10 | 151936 | 16 | eager | 11.072 | 11.072 | 1.000x |
| 10 | 151936 | 16 | graph | 11.328 | 11.328 | 1.000x |
| 10 | 151936 | 32 | eager | 12.160 | 12.160 | 1.000x |
| 10 | 151936 | 32 | graph | 12.448 | 12.448 | 1.000x |
| 10 | 151936 | 64 | eager | 16.160 | 16.160 | 1.000x |
| 10 | 151936 | 64 | graph | 16.448 | 16.448 | 1.000x |
| 10 | 151936 | 128 | eager | 24.320 | 24.320 | 1.000x |
| 10 | 151936 | 128 | graph | 24.576 | 24.576 | 1.000x |
| 10 | 262144 | 1 | eager | 9.424 | 9.424 | 1.000x |
| 10 | 262144 | 1 | graph | 9.600 | 9.600 | 1.000x |
| 10 | 262144 | 2 | eager | 9.504 | 9.504 | 1.000x |
| 10 | 262144 | 2 | graph | 9.728 | 9.728 | 1.000x |
| 10 | 262144 | 4 | eager | 9.792 | 9.792 | 1.000x |
| 10 | 262144 | 4 | graph | 10.048 | 10.048 | 1.000x |
| 10 | 262144 | 8 | eager | 10.496 | 10.496 | 1.000x |
| 10 | 262144 | 8 | graph | 10.752 | 10.752 | 1.000x |
| 10 | 262144 | 16 | eager | 12.768 | 12.784 | 1.000x |
| 10 | 262144 | 16 | graph | 13.024 | 13.024 | 1.000x |
| 10 | 262144 | 32 | eager | 14.816 | 14.816 | 1.000x |
| 10 | 262144 | 32 | graph | 15.104 | 15.104 | 1.000x |
| 10 | 262144 | 64 | eager | 23.744 | 23.712 | 1.000x |
| 10 | 262144 | 64 | graph | 24.000 | 24.000 | 1.000x |
| 10 | 262144 | 128 | eager | 35.440 | 35.456 | 1.000x |
| 10 | 262144 | 128 | graph | 35.712 | 35.712 | 1.000x |
| 50 | 32768 | 1 | eager | 7.584 | 7.584 | 1.000x |
| 50 | 32768 | 1 | graph | 7.744 | 7.744 | 1.000x |
| 50 | 32768 | 2 | eager | 7.664 | 7.680 | 1.000x |
| 50 | 32768 | 2 | graph | 7.920 | 7.920 | 1.000x |
| 50 | 32768 | 4 | eager | 7.712 | 7.712 | 1.000x |
| 50 | 32768 | 4 | graph | 8.000 | 8.000 | 1.000x |
| 50 | 32768 | 8 | eager | 7.952 | 7.936 | 1.000x |
| 50 | 32768 | 8 | graph | 8.160 | 8.160 | 1.000x |
| 50 | 32768 | 16 | eager | 8.160 | 8.160 | 1.000x |
| 50 | 32768 | 16 | graph | 8.416 | 8.416 | 1.000x |
| 50 | 32768 | 32 | eager | 8.704 | 8.704 | 1.000x |
| 50 | 32768 | 32 | graph | 8.960 | 8.960 | 1.000x |
| 50 | 32768 | 64 | eager | 10.208 | 10.208 | 1.000x |
| 50 | 32768 | 64 | graph | 10.400 | 10.400 | 1.000x |
| 50 | 32768 | 128 | eager | 11.264 | 11.264 | 1.000x |
| 50 | 32768 | 128 | graph | 11.488 | 11.488 | 1.000x |
| 50 | 128256 | 1 | eager | 9.248 | 9.248 | 1.000x |
| 50 | 128256 | 1 | graph | 9.376 | 9.376 | 1.000x |
| 50 | 128256 | 2 | eager | 9.440 | 9.440 | 1.000x |
| 50 | 128256 | 2 | graph | 9.696 | 9.712 | 1.000x |
| 50 | 128256 | 4 | eager | 9.584 | 9.568 | 1.000x |
| 50 | 128256 | 4 | graph | 9.888 | 9.888 | 1.000x |
| 50 | 128256 | 8 | eager | 10.016 | 10.016 | 1.000x |
| 50 | 128256 | 8 | graph | 10.272 | 10.272 | 1.000x |
| 50 | 128256 | 16 | eager | 11.680 | 11.680 | 1.000x |
| 50 | 128256 | 16 | graph | 11.968 | 11.968 | 1.000x |
| 50 | 128256 | 32 | eager | 12.992 | 13.008 | 1.000x |
| 50 | 128256 | 32 | graph | 13.312 | 13.312 | 1.000x |
| 50 | 128256 | 64 | eager | 15.744 | 15.744 | 1.000x |
| 50 | 128256 | 64 | graph | 16.032 | 16.048 | 1.000x |
| 50 | 128256 | 128 | eager | 21.536 | 21.536 | 1.000x |
| 50 | 128256 | 128 | graph | 21.760 | 21.744 | 1.000x |
| 50 | 151936 | 1 | eager | 10.080 | 10.080 | 1.000x |
| 50 | 151936 | 1 | graph | 10.208 | 10.208 | 1.000x |
| 50 | 151936 | 2 | eager | 10.176 | 10.176 | 1.000x |
| 50 | 151936 | 2 | graph | 10.336 | 10.344 | 1.000x |
| 50 | 151936 | 4 | eager | 10.400 | 10.400 | 1.000x |
| 50 | 151936 | 4 | graph | 10.720 | 10.720 | 1.000x |
| 50 | 151936 | 8 | eager | 10.912 | 10.912 | 1.000x |
| 50 | 151936 | 8 | graph | 11.168 | 11.168 | 1.000x |
| 50 | 151936 | 16 | eager | 12.416 | 12.416 | 1.000x |
| 50 | 151936 | 16 | graph | 12.672 | 12.688 | 1.000x |
| 50 | 151936 | 32 | eager | 13.536 | 13.536 | 1.000x |
| 50 | 151936 | 32 | graph | 13.824 | 13.824 | 1.000x |
| 50 | 151936 | 64 | eager | 17.312 | 17.312 | 1.000x |
| 50 | 151936 | 64 | graph | 17.600 | 17.600 | 1.000x |
| 50 | 151936 | 128 | eager | 24.928 | 24.928 | 1.000x |
| 50 | 151936 | 128 | graph | 25.136 | 25.120 | 1.000x |
| 50 | 262144 | 1 | eager | 10.560 | 10.560 | 1.000x |
| 50 | 262144 | 1 | graph | 10.752 | 10.720 | 1.000x |
| 50 | 262144 | 2 | eager | 10.784 | 10.784 | 1.000x |
| 50 | 262144 | 2 | graph | 11.056 | 11.056 | 1.000x |
| 50 | 262144 | 4 | eager | 11.040 | 11.040 | 1.000x |
| 50 | 262144 | 4 | graph | 11.312 | 11.312 | 1.000x |
| 50 | 262144 | 8 | eager | 11.840 | 11.840 | 1.000x |
| 50 | 262144 | 8 | graph | 12.096 | 12.096 | 1.000x |
| 50 | 262144 | 16 | eager | 13.856 | 13.856 | 1.000x |
| 50 | 262144 | 16 | graph | 14.176 | 14.144 | 1.001x |
| 50 | 262144 | 32 | eager | 16.064 | 16.064 | 1.000x |
| 50 | 262144 | 32 | graph | 16.352 | 16.352 | 1.000x |
| 50 | 262144 | 64 | eager | 24.096 | 24.096 | 1.000x |
| 50 | 262144 | 64 | graph | 24.352 | 24.368 | 1.000x |
| 50 | 262144 | 128 | eager | 35.840 | 35.840 | 1.000x |
| 50 | 262144 | 128 | graph | 36.096 | 36.096 | 1.000x |
| 1000 | 32768 | 1 | eager | 15.744 | 16.000 | 1.000x |
| 1000 | 32768 | 1 | graph | 14.176 | 14.112 | 1.000x |
| 1000 | 32768 | 2 | eager | 16.560 | 16.464 | 1.007x |
| 1000 | 32768 | 2 | graph | 14.224 | 14.224 | 1.000x |
| 1000 | 32768 | 4 | eager | 16.672 | 17.040 | 0.997x |
| 1000 | 32768 | 4 | graph | 14.368 | 14.384 | 1.000x |
| 1000 | 32768 | 8 | eager | 16.640 | 16.608 | 1.016x |
| 1000 | 32768 | 8 | graph | 14.464 | 14.448 | 1.000x |
| 1000 | 32768 | 16 | eager | 17.024 | 17.360 | 1.014x |
| 1000 | 32768 | 16 | graph | 14.736 | 14.752 | 1.000x |
| 1000 | 32768 | 32 | eager | 16.592 | 16.368 | 1.004x |
| 1000 | 32768 | 32 | graph | 15.560 | 15.568 | 1.000x |
| 1000 | 32768 | 64 | eager | 16.416 | 16.368 | 1.000x |
| 1000 | 32768 | 64 | graph | 16.480 | 16.496 | 1.000x |
| 1000 | 32768 | 128 | eager | 17.856 | 17.872 | 1.000x |
| 1000 | 32768 | 128 | graph | 18.080 | 18.064 | 1.000x |
| 1000 | 128256 | 1 | eager | 14.992 | 14.976 | 1.000x |
| 1000 | 128256 | 1 | graph | 15.104 | 15.104 | 1.000x |
| 1000 | 128256 | 2 | eager | 15.120 | 15.184 | 1.000x |
| 1000 | 128256 | 2 | graph | 15.440 | 15.440 | 1.000x |
| 1000 | 128256 | 4 | eager | 15.200 | 15.200 | 1.000x |
| 1000 | 128256 | 4 | graph | 15.552 | 15.520 | 1.000x |
| 1000 | 128256 | 8 | eager | 15.744 | 15.744 | 1.000x |
| 1000 | 128256 | 8 | graph | 16.032 | 16.032 | 1.000x |
| 1000 | 128256 | 16 | eager | 19.024 | 18.928 | 1.002x |
| 1000 | 128256 | 16 | graph | 19.040 | 19.088 | 1.000x |
| 1000 | 128256 | 32 | eager | 20.096 | 20.112 | 1.000x |
| 1000 | 128256 | 32 | graph | 20.528 | 20.544 | 1.000x |
| 1000 | 128256 | 64 | eager | 22.944 | 22.992 | 1.000x |
| 1000 | 128256 | 64 | graph | 23.360 | 23.328 | 1.000x |
| 1000 | 128256 | 128 | eager | 32.352 | 32.368 | 1.000x |
| 1000 | 128256 | 128 | graph | 32.768 | 32.768 | 1.001x |
| 1000 | 151936 | 1 | eager | 16.288 | 16.288 | 1.000x |
| 1000 | 151936 | 1 | graph | 16.448 | 16.416 | 1.000x |
| 1000 | 151936 | 2 | eager | 16.688 | 16.672 | 1.000x |
| 1000 | 151936 | 2 | graph | 16.976 | 16.976 | 1.000x |
| 1000 | 151936 | 4 | eager | 16.928 | 16.912 | 1.000x |
| 1000 | 151936 | 4 | graph | 17.248 | 17.248 | 1.000x |
| 1000 | 151936 | 8 | eager | 17.312 | 17.320 | 1.000x |
| 1000 | 151936 | 8 | graph | 17.584 | 17.616 | 1.000x |
| 1000 | 151936 | 16 | eager | 19.744 | 19.808 | 1.000x |
| 1000 | 151936 | 16 | graph | 20.032 | 20.048 | 1.000x |
| 1000 | 151936 | 32 | eager | 20.640 | 20.689 | 1.000x |
| 1000 | 151936 | 32 | graph | 21.216 | 21.200 | 1.000x |
| 1000 | 151936 | 64 | eager | 25.072 | 25.072 | 1.000x |
| 1000 | 151936 | 64 | graph | 25.712 | 25.696 | 1.001x |
| 1000 | 151936 | 128 | eager | 36.992 | 32.000 | 1.155x |
| 1000 | 151936 | 128 | graph | 37.568 | 32.232 | 1.166x |
| 1000 | 262144 | 1 | eager | 16.944 | 16.832 | 1.000x |
| 1000 | 262144 | 1 | graph | 16.928 | 16.928 | 1.000x |
| 1000 | 262144 | 2 | eager | 16.944 | 16.864 | 1.000x |
| 1000 | 262144 | 2 | graph | 17.152 | 17.136 | 1.000x |
| 1000 | 262144 | 4 | eager | 17.616 | 17.632 | 1.000x |
| 1000 | 262144 | 4 | graph | 17.952 | 17.952 | 1.000x |
| 1000 | 262144 | 8 | eager | 18.240 | 18.240 | 1.000x |
| 1000 | 262144 | 8 | graph | 18.528 | 18.528 | 1.000x |
| 1000 | 262144 | 16 | eager | 22.336 | 22.336 | 1.000x |
| 1000 | 262144 | 16 | graph | 22.592 | 22.592 | 1.001x |
| 1000 | 262144 | 32 | eager | 23.424 | 23.440 | 1.000x |
| 1000 | 262144 | 32 | graph | 24.064 | 24.048 | 1.000x |
| 1000 | 262144 | 64 | eager | 31.040 | 31.216 | 1.000x |
| 1000 | 262144 | 64 | graph | 31.664 | 31.680 | 1.000x |
| 1000 | 262144 | 128 | eager | 46.608 | 46.512 | 1.001x |
| 1000 | 262144 | 128 | graph | 46.856 | 46.752 | 1.000x |

</details>

<details>
<summary>B200 (sm_100a): all 192 shapes</summary>

NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4 (nvcc 13.4), PyTorch
2.14.1+cu130. Baseline: the `cake_sampling` module on FlashInfer main
(round 17, #7750). Latency in µs of one sampling call (median CUPTI time
from a cold L2 over 12 rounds after a warm-up round, contiguous float32
probability rows); speedup = baseline / this PR, the median of the 12
per-round paired ratios.

| top-k | vocab | batch | mode | baseline µs | this PR µs | speedup |
|---:|---:|---:|---|---:|---:|---:|
| 10 | 32768 | 1 | eager | 6.880 | 6.880 | 1.000x |
| 10 | 32768 | 1 | graph | 7.248 | 7.248 | 1.000x |
| 10 | 32768 | 2 | eager | 7.040 | 7.040 | 1.000x |
| 10 | 32768 | 2 | graph | 7.424 | 7.455 | 1.000x |
| 10 | 32768 | 4 | eager | 7.200 | 7.200 | 1.000x |
| 10 | 32768 | 4 | graph | 7.520 | 7.503 | 1.000x |
| 10 | 32768 | 8 | eager | 7.360 | 7.344 | 1.000x |
| 10 | 32768 | 8 | graph | 7.616 | 7.616 | 1.000x |
| 10 | 32768 | 16 | eager | 7.616 | 7.616 | 1.000x |
| 10 | 32768 | 16 | graph | 7.903 | 7.873 | 1.000x |
| 10 | 32768 | 32 | eager | 8.160 | 8.160 | 1.000x |
| 10 | 32768 | 32 | graph | 8.416 | 8.416 | 1.000x |
| 10 | 32768 | 64 | eager | 9.312 | 9.312 | 1.000x |
| 10 | 32768 | 64 | graph | 9.568 | 9.568 | 1.000x |
| 10 | 32768 | 128 | eager | 10.928 | 10.928 | 1.000x |
| 10 | 32768 | 128 | graph | 11.152 | 11.152 | 1.000x |
| 10 | 128256 | 1 | eager | 7.936 | 7.936 | 1.000x |
| 10 | 128256 | 1 | graph | 8.287 | 8.272 | 1.000x |
| 10 | 128256 | 2 | eager | 8.064 | 8.064 | 1.000x |
| 10 | 128256 | 2 | graph | 8.416 | 8.416 | 1.000x |
| 10 | 128256 | 4 | eager | 8.368 | 8.383 | 1.000x |
| 10 | 128256 | 4 | graph | 8.607 | 8.607 | 1.000x |
| 10 | 128256 | 8 | eager | 8.752 | 8.768 | 1.000x |
| 10 | 128256 | 8 | graph | 8.992 | 8.992 | 1.000x |
| 10 | 128256 | 16 | eager | 10.367 | 10.367 | 1.000x |
| 10 | 128256 | 16 | graph | 10.624 | 10.624 | 1.000x |
| 10 | 128256 | 32 | eager | 11.552 | 11.552 | 1.000x |
| 10 | 128256 | 32 | graph | 11.840 | 11.871 | 1.000x |
| 10 | 128256 | 64 | eager | 14.655 | 14.640 | 1.000x |
| 10 | 128256 | 64 | graph | 14.928 | 14.944 | 1.000x |
| 10 | 128256 | 128 | eager | 21.216 | 21.232 | 1.000x |
| 10 | 128256 | 128 | graph | 21.503 | 21.503 | 1.000x |
| 10 | 151936 | 1 | eager | 8.849 | 8.864 | 1.000x |
| 10 | 151936 | 1 | graph | 9.232 | 9.248 | 1.000x |
| 10 | 151936 | 2 | eager | 8.912 | 8.912 | 1.000x |
| 10 | 151936 | 2 | graph | 9.296 | 9.312 | 1.000x |
| 10 | 151936 | 4 | eager | 9.184 | 9.184 | 1.000x |
| 10 | 151936 | 4 | graph | 9.472 | 9.472 | 1.000x |
| 10 | 151936 | 8 | eager | 9.616 | 9.616 | 1.000x |
| 10 | 151936 | 8 | graph | 9.872 | 9.872 | 1.000x |
| 10 | 151936 | 16 | eager | 11.104 | 11.135 | 1.000x |
| 10 | 151936 | 16 | graph | 11.392 | 11.392 | 1.000x |
| 10 | 151936 | 32 | eager | 12.320 | 12.320 | 1.000x |
| 10 | 151936 | 32 | graph | 12.640 | 12.640 | 1.000x |
| 10 | 151936 | 64 | eager | 16.320 | 16.320 | 1.000x |
| 10 | 151936 | 64 | graph | 16.639 | 16.639 | 1.000x |
| 10 | 151936 | 128 | eager | 24.032 | 24.032 | 1.000x |
| 10 | 151936 | 128 | graph | 24.320 | 24.320 | 1.000x |
| 10 | 262144 | 1 | eager | 9.504 | 9.504 | 1.000x |
| 10 | 262144 | 1 | graph | 9.872 | 9.888 | 1.000x |
| 10 | 262144 | 2 | eager | 9.663 | 9.664 | 1.000x |
| 10 | 262144 | 2 | graph | 10.048 | 10.048 | 1.000x |
| 10 | 262144 | 4 | eager | 9.984 | 9.984 | 1.000x |
| 10 | 262144 | 4 | graph | 10.272 | 10.288 | 1.000x |
| 10 | 262144 | 8 | eager | 10.559 | 10.559 | 1.000x |
| 10 | 262144 | 8 | graph | 10.864 | 10.864 | 1.000x |
| 10 | 262144 | 16 | eager | 13.088 | 13.088 | 1.000x |
| 10 | 262144 | 16 | graph | 13.376 | 13.377 | 1.000x |
| 10 | 262144 | 32 | eager | 15.464 | 15.456 | 1.000x |
| 10 | 262144 | 32 | graph | 15.743 | 15.744 | 1.000x |
| 10 | 262144 | 64 | eager | 21.856 | 21.856 | 1.000x |
| 10 | 262144 | 64 | graph | 22.144 | 22.144 | 1.000x |
| 10 | 262144 | 128 | eager | 37.375 | 37.375 | 1.000x |
| 10 | 262144 | 128 | graph | 37.680 | 37.695 | 1.000x |
| 50 | 32768 | 1 | eager | 7.551 | 7.535 | 1.000x |
| 50 | 32768 | 1 | graph | 7.919 | 7.935 | 1.000x |
| 50 | 32768 | 2 | eager | 7.649 | 7.680 | 1.000x |
| 50 | 32768 | 2 | graph | 8.048 | 8.064 | 1.000x |
| 50 | 32768 | 4 | eager | 7.824 | 7.824 | 1.000x |
| 50 | 32768 | 4 | graph | 8.128 | 8.128 | 1.000x |
| 50 | 32768 | 8 | eager | 8.096 | 8.096 | 1.000x |
| 50 | 32768 | 8 | graph | 8.320 | 8.320 | 1.000x |
| 50 | 32768 | 16 | eager | 8.304 | 8.304 | 1.000x |
| 50 | 32768 | 16 | graph | 8.575 | 8.560 | 1.000x |
| 50 | 32768 | 32 | eager | 8.896 | 8.896 | 1.000x |
| 50 | 32768 | 32 | graph | 9.184 | 9.184 | 1.000x |
| 50 | 32768 | 64 | eager | 10.432 | 10.240 | 1.019x |
| 50 | 32768 | 64 | graph | 10.672 | 10.464 | 1.021x |
| 50 | 32768 | 128 | eager | 11.488 | 11.488 | 1.000x |
| 50 | 32768 | 128 | graph | 11.744 | 11.744 | 1.000x |
| 50 | 128256 | 1 | eager | 9.344 | 9.344 | 1.000x |
| 50 | 128256 | 1 | graph | 9.664 | 9.664 | 1.000x |
| 50 | 128256 | 2 | eager | 9.504 | 9.504 | 1.000x |
| 50 | 128256 | 2 | graph | 9.904 | 9.904 | 1.000x |
| 50 | 128256 | 4 | eager | 9.760 | 9.791 | 1.000x |
| 50 | 128256 | 4 | graph | 10.048 | 10.048 | 1.000x |
| 50 | 128256 | 8 | eager | 10.176 | 10.176 | 1.000x |
| 50 | 128256 | 8 | graph | 10.463 | 10.463 | 1.000x |
| 50 | 128256 | 16 | eager | 11.584 | 11.584 | 1.000x |
| 50 | 128256 | 16 | graph | 11.855 | 11.855 | 1.000x |
| 50 | 128256 | 32 | eager | 12.960 | 12.960 | 1.000x |
| 50 | 128256 | 32 | graph | 13.279 | 13.280 | 1.000x |
| 50 | 128256 | 64 | eager | 15.776 | 15.760 | 1.000x |
| 50 | 128256 | 64 | graph | 16.064 | 16.071 | 1.000x |
| 50 | 128256 | 128 | eager | 22.016 | 22.016 | 1.000x |
| 50 | 128256 | 128 | graph | 22.303 | 22.272 | 1.000x |
| 50 | 151936 | 1 | eager | 10.207 | 10.200 | 1.000x |
| 50 | 151936 | 1 | graph | 10.544 | 10.559 | 1.000x |
| 50 | 151936 | 2 | eager | 10.304 | 10.304 | 1.000x |
| 50 | 151936 | 2 | graph | 10.656 | 10.655 | 1.000x |
| 50 | 151936 | 4 | eager | 10.624 | 10.624 | 1.000x |
| 50 | 151936 | 4 | graph | 10.880 | 10.896 | 1.000x |
| 50 | 151936 | 8 | eager | 11.055 | 11.055 | 1.000x |
| 50 | 151936 | 8 | graph | 11.328 | 11.328 | 1.000x |
| 50 | 151936 | 16 | eager | 12.288 | 12.303 | 1.000x |
| 50 | 151936 | 16 | graph | 12.591 | 12.576 | 1.000x |
| 50 | 151936 | 32 | eager | 13.728 | 13.728 | 1.000x |
| 50 | 151936 | 32 | graph | 14.048 | 14.048 | 1.000x |
| 50 | 151936 | 64 | eager | 17.504 | 17.504 | 1.000x |
| 50 | 151936 | 64 | graph | 17.792 | 17.807 | 1.000x |
| 50 | 151936 | 128 | eager | 24.735 | 24.704 | 1.000x |
| 50 | 151936 | 128 | graph | 25.024 | 25.055 | 1.000x |
| 50 | 262144 | 1 | eager | 10.720 | 10.736 | 1.000x |
| 50 | 262144 | 1 | graph | 11.072 | 11.073 | 1.000x |
| 50 | 262144 | 2 | eager | 10.912 | 10.912 | 1.000x |
| 50 | 262144 | 2 | graph | 11.264 | 11.264 | 1.000x |
| 50 | 262144 | 4 | eager | 11.296 | 11.296 | 1.000x |
| 50 | 262144 | 4 | graph | 11.536 | 11.536 | 1.000x |
| 50 | 262144 | 8 | eager | 12.064 | 12.064 | 1.000x |
| 50 | 262144 | 8 | graph | 12.336 | 12.335 | 1.000x |
| 50 | 262144 | 16 | eager | 14.400 | 14.400 | 1.000x |
| 50 | 262144 | 16 | graph | 14.720 | 14.720 | 1.000x |
| 50 | 262144 | 32 | eager | 16.864 | 16.872 | 1.000x |
| 50 | 262144 | 32 | graph | 17.152 | 17.168 | 1.000x |
| 50 | 262144 | 64 | eager | 22.976 | 22.976 | 1.000x |
| 50 | 262144 | 64 | graph | 23.295 | 23.296 | 1.000x |
| 50 | 262144 | 128 | eager | 37.904 | 37.888 | 1.000x |
| 50 | 262144 | 128 | graph | 38.216 | 38.208 | 1.000x |
| 1000 | 32768 | 1 | eager | 13.968 | 13.968 | 1.000x |
| 1000 | 32768 | 1 | graph | 14.463 | 14.463 | 1.000x |
| 1000 | 32768 | 2 | eager | 14.176 | 14.176 | 1.000x |
| 1000 | 32768 | 2 | graph | 14.543 | 14.544 | 1.000x |
| 1000 | 32768 | 4 | eager | 14.303 | 14.304 | 1.000x |
| 1000 | 32768 | 4 | graph | 14.608 | 14.624 | 1.000x |
| 1000 | 32768 | 8 | eager | 14.416 | 14.400 | 1.000x |
| 1000 | 32768 | 8 | graph | 14.704 | 14.704 | 1.000x |
| 1000 | 32768 | 16 | eager | 14.816 | 14.816 | 1.000x |
| 1000 | 32768 | 16 | graph | 15.136 | 15.120 | 1.000x |
| 1000 | 32768 | 32 | eager | 15.488 | 15.456 | 1.000x |
| 1000 | 32768 | 32 | graph | 15.984 | 15.984 | 1.000x |
| 1000 | 32768 | 64 | eager | 17.104 | 17.088 | 1.000x |
| 1000 | 32768 | 64 | graph | 17.471 | 17.520 | 1.000x |
| 1000 | 32768 | 128 | eager | 18.191 | 18.623 | 0.999x |
| 1000 | 32768 | 128 | graph | 18.688 | 18.703 | 1.000x |
| 1000 | 128256 | 1 | eager | 14.800 | 14.784 | 1.000x |
| 1000 | 128256 | 1 | graph | 15.152 | 15.152 | 1.000x |
| 1000 | 128256 | 2 | eager | 14.920 | 14.912 | 1.000x |
| 1000 | 128256 | 2 | graph | 15.297 | 15.296 | 1.000x |
| 1000 | 128256 | 4 | eager | 15.296 | 15.296 | 1.000x |
| 1000 | 128256 | 4 | graph | 15.647 | 15.647 | 1.000x |
| 1000 | 128256 | 8 | eager | 15.648 | 15.648 | 1.000x |
| 1000 | 128256 | 8 | graph | 15.920 | 15.904 | 1.000x |
| 1000 | 128256 | 16 | eager | 18.847 | 18.863 | 1.000x |
| 1000 | 128256 | 16 | graph | 19.087 | 19.072 | 1.000x |
| 1000 | 128256 | 32 | eager | 20.415 | 20.399 | 1.000x |
| 1000 | 128256 | 32 | graph | 20.656 | 20.656 | 1.000x |
| 1000 | 128256 | 64 | eager | 23.744 | 23.759 | 1.000x |
| 1000 | 128256 | 64 | graph | 24.015 | 24.015 | 1.000x |
| 1000 | 128256 | 128 | eager | 32.960 | 33.168 | 1.000x |
| 1000 | 128256 | 128 | graph | 33.520 | 33.487 | 1.000x |
| 1000 | 151936 | 1 | eager | 16.160 | 16.160 | 1.000x |
| 1000 | 151936 | 1 | graph | 16.527 | 16.520 | 1.000x |
| 1000 | 151936 | 2 | eager | 16.496 | 16.512 | 1.000x |
| 1000 | 151936 | 2 | graph | 16.912 | 16.912 | 1.000x |
| 1000 | 151936 | 4 | eager | 16.832 | 16.848 | 1.000x |
| 1000 | 151936 | 4 | graph | 17.184 | 17.200 | 1.000x |
| 1000 | 151936 | 8 | eager | 17.264 | 17.279 | 0.999x |
| 1000 | 151936 | 8 | graph | 17.568 | 17.568 | 1.000x |
| 1000 | 151936 | 16 | eager | 20.128 | 20.129 | 1.000x |
| 1000 | 151936 | 16 | graph | 20.472 | 20.464 | 1.000x |
| 1000 | 151936 | 32 | eager | 21.520 | 21.520 | 1.000x |
| 1000 | 151936 | 32 | graph | 22.016 | 22.016 | 1.000x |
| 1000 | 151936 | 64 | eager | 25.824 | 25.823 | 1.000x |
| 1000 | 151936 | 64 | graph | 26.319 | 26.303 | 1.000x |
| 1000 | 151936 | 128 | eager | 37.343 | 37.407 | 1.000x |
| 1000 | 151936 | 128 | graph | 37.983 | 37.936 | 1.000x |
| 1000 | 262144 | 1 | eager | 16.800 | 16.800 | 1.000x |
| 1000 | 262144 | 1 | graph | 17.169 | 17.168 | 1.000x |
| 1000 | 262144 | 2 | eager | 17.504 | 17.504 | 1.000x |
| 1000 | 262144 | 2 | graph | 17.888 | 17.904 | 1.000x |
| 1000 | 262144 | 4 | eager | 17.840 | 17.840 | 1.000x |
| 1000 | 262144 | 4 | graph | 18.176 | 18.176 | 1.000x |
| 1000 | 262144 | 8 | eager | 18.431 | 18.416 | 1.000x |
| 1000 | 262144 | 8 | graph | 18.688 | 18.688 | 1.000x |
| 1000 | 262144 | 16 | eager | 22.111 | 22.112 | 1.000x |
| 1000 | 262144 | 16 | graph | 22.416 | 22.416 | 1.000x |
| 1000 | 262144 | 32 | eager | 23.791 | 23.791 | 1.000x |
| 1000 | 262144 | 32 | graph | 24.416 | 24.416 | 1.000x |
| 1000 | 262144 | 64 | eager | 31.327 | 31.328 | 1.000x |
| 1000 | 262144 | 64 | graph | 31.872 | 31.904 | 1.000x |
| 1000 | 262144 | 128 | eager | 48.127 | 48.128 | 1.000x |
| 1000 | 262144 | 128 | graph | 48.287 | 48.272 | 1.001x |

</details>

Cake ships no other data type, layout or fused form of this kernel: its
single source compiles into one module with one `-gencode` per target
and ships on every compute capability 9.x, 10.x, 11.x and 12.x target
FlashInfer builds (sm_90a, sm_100a, sm_103a, sm_107a, sm_110a, sm_120a,
sm_120f, sm_121a), and this PR leaves the launch choices on every other
GPU, including H100, R200 and RTX PRO 6000, as they are on main.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Performance**
* Updated sampling plan selection for specific B200 and GB300
configurations, including high top-k workloads. Other top-k values
continue to use the existing selection logic.
* Added coverage for these device- and workload-specific selections,
including checks that unaffected devices and configurations retain their
existing plans.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8d7d03c](https://github.com/flashinfer-ai/flashinfer/commit/8d7d03c481f60a0acc72f12d3a9078bbc44672fc)

- **作者**: eigen
- **时间**: 2026-10-29T18:03:12Z
- **提交信息**: fix(cake_kda): release the compute warps' TMEM map writes to the prefix epilogue (#7828)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR adds no module. It changes the kernel text of
one generated program: the map-prefix kernel of the split form
(`csrc/kda/prefill/cake_kda_prefill_0c19a9863fa28a7dad1a_kernel.cu`),
built for sm_100a and sm_103a. The program name stays the same.

Before this change, only `tcgen05.commit` signalled the `m_ready`
mbarrier. As a result, nothing ordered the compute warps' `tcgen05.st`
writes of the decayed map before the epilogue's `tcgen05.ld` reads of
the same TMEM region. Now the elected MMA thread also arrives on
`m_ready` after the commit, behind `tcgen05.fence::before_thread_sync`,
and `m_ready`'s init count goes from 1 to 2.

The table covers the 12 shapes of the 56-shape list that run the changed
kernel: 12 and 16 heads, no gate lower bound.

| heads | gate lower bound | sequence lengths | B200 main | B200 this PR
| speedup | GB300 main | GB300 this PR | speedup |
|---:|---|---|---:|---:|---:|---:|---:|---:|
| 12 | none | 8192 | 217.86 | 217.54 | 1.00x TIE | 211.30 | 211.78 |
1.00x TIE |
| 12 | none | 16384 | 378.98 | 378.26 | 1.00x TIE | 359.23 | 359.71 |
1.00x TIE |
| 12 | none | 32768 | 684.83 | 684.38 | 1.00x TIE | 646.82 | 646.29 |
1.00x TIE |
| 12 | none | 2x8192 | 368.94 | 369.18 | 1.00x TIE | 354.59 | 354.50 |
1.00x TIE |
| 12 | none | 3000+13384 | 393.76 | 393.95 | 1.00x TIE | 378.18 | 378.50
| 1.00x TIE |
| 12 | none | 2x(8128+64) | 374.27 | 374.24 | 1.00x TIE | 358.18 |
358.56 | 1.00x TIE |
| 16 | none | 8192 | 267.62 | 267.62 | 1.00x TIE | 258.40 | 258.94 |
1.00x TIE |
| 16 | none | 16384 | 465.46 | 464.75 | 1.00x TIE | 440.54 | 441.22 |
1.00x TIE |
| 16 | none | 32768 | 875.04 | 876.16 | 1.00x TIE | 826.53 | 826.59 |
1.00x TIE |
| 16 | none | 2x8192 | 486.72 | 486.38 | 1.00x TIE | 465.71 | 466.30 |
1.00x TIE |
| 16 | none | 3000+13384 | 477.57 | 477.44 | 1.00x TIE | 452.62 | 453.31
| 1.00x TIE |
| 16 | none | 2x(8128+64) | 491.58 | 491.74 | 1.00x TIE | 470.43 |
470.50 | 1.00x TIE |

B200: NVIDIA B200, sm_100a, 148 SMs, driver 580.82.07. GB300: NVIDIA
GB300, sm_103a, 152 SMs, driver 580.159.03. CUDA 13.4 (nvcc), PyTorch
2.14.1+cu130.

Latency is in microseconds and is the run-half median per call of the
timing pair, with BF16 q/k/v and FP32 recurrent state. "main" is
FlashInfer main at c710080a329c (its KDA prefill kernels equal the
measured base). Speedup is main / this PR. TIE means no difference
beyond the measurement band; all 12 rows are TIE on both GPUs.

The other 44 shapes of the list run kernels whose text this PR does not
change.

The kernel's other Cake variants are unchanged: the TF32-input modules
and the BF16-state forms; the family ships on sm_100a and sm_103a, and
this PR covers both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization during kernel execution to help ensure
operations wait for the required participants.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [8d52829](https://github.com/flashinfer-ai/flashinfer/commit/8d52829f8bbbe91656dbbfd5cb10f1fd7e5c063d)

- **作者**: eigen
- **时间**: 2026-10-29T17:55:02Z
- **提交信息**: perf(cake_causal_conv1d): with grad, communication-free KCP checkpoint recompute with a recompute handle (#7846)

Under non-reentrant `torch.utils.checkpoint`, `cake_causal_conv1d_kcp`
repeats its forward halo exchange (gather + `all_to_all_single` + wait)
during recompute because the checkpoint drops saved tensors.
`cake_causal_conv1d_kcp` is the context-parallel (KCP) packed width-4
depthwise conv + SiLU, with a cross-rank halo. This PR adds an opt-in
recompute handle. The original forward stores its history rows in the
handle, and the recompute reuses them, so it runs no collective. Without
a handle, behavior is unchanged.

Part of #7815. This is the convolution half of #7818; the GDN half is
#7852, with the same handle semantics.

## API

```python
from torch.utils.checkpoint import checkpoint
from flashinfer.cake_causal_conv1d_train import KcpRecomputeHandle, cake_causal_conv1d_kcp

def layer(handle, *conv_args):
    ...
    return cake_causal_conv1d_kcp(*conv_args, recompute_handle=handle)

# One handle per convolution call and per micro-step, created outside the
# outermost checkpoint region and passed as an argument of the checkpointed function.
handle = KcpRecomputeHandle()
y = checkpoint(layer, handle, *conv_args, use_reentrant=False)
y.sum().backward()  # recompute reuses the stored history rows: no gather, collective or wait
handle.clear()      # only once no backward that needs it is pending
```

## What changed

- New keyword-only argument `recompute_handle=None` on
`flashinfer.cake_causal_conv1d_train.cake_causal_conv1d_kcp` and the
backend.
- New public class
`flashinfer.cake_causal_conv1d_train.KcpRecomputeHandle` with an
`entries` dict, `clear()` and `nbytes()`. Any object with an `entries`
dict is accepted. The class is listed in the API docs.
- The original forward exchanges as it does today. It then stores its
history rows under the key `"conv"`. These rows are the saved set's own
`[n_hist_rows, C]` BF16 tensor, not a copy. When torch recomputes that
forward inside the backward, the forward binds the stored rows and
launches the same forward kernel with no gather, collective or wait. The
backward exchange is unchanged.
- Entries are not popped, so `retain_graph` double backward works.
- If no entry is present, the call exchanges and stores. This also
applies inside an outer recompute, so nested checkpoints work. If an
entry is present outside a backward, the call raises, which catches a
handle reused across steps or micro-steps.
- With a handle, graph capture, `graph="replay"` and debug modes are
refused. Both the wrapper and the autograd Function enforce this.
- Phase detection uses torch's current graph-task id
(`torch._C._current_graph_task_id`), checked once. This was validated on
PyTorch 2.14.1+cu130.
- Retained memory with a handle is exactly the history rows,
`n_hist_rows * C * 2` bytes (equal to `nbytes()`). Without a handle it
is 0, as before.
- The saved set, kernels, launch order and output bits are unchanged.
`recompute_handle=None` keeps today's path.
- The following usage rules are documented but not checked at runtime:
- Use one handle per convolution call. A layer with separate Q/K/V
convolutions needs one handle for each convolution call.
- Every rank of `ctx.group` must pass a handle for the same call, or
none, at the same nesting level. A mismatch pairs one rank's recompute
exchange with another rank's backward exchange and hangs.
- Never share a handle between two convolution calls, and never
`clear()` or reuse it while a backward that needs it is pending.

## Measurements

| Mode | Collectives (forward / recompute / backward) |
|---|---|
| No checkpoint | 1 / 0 / 1 |
| Checkpoint, no handle | 1 / 1 / 1 |
| Checkpoint with handle | 1 / 0 / 1 |
| Reentrant checkpoint with handle | 1 / 0 / 1 |
| retain_graph, two backwards, with handle | 1 / 0 / 2 |
| Nested checkpoint, handle created outside | 1 / 0 / 1 |
| Nested checkpoint, handle created inside | 1 / 1 / 1 |

In every mode the waits match the calls. Outputs `y` and gradients `dx`
and `dweight` are bitwise equal across all modes.

## Validation

All runs used this head on GB200 (sm_100a), GB300 (sm_103a) and R200
(sm_107a), PyTorch 2.14.1+cu130.

- `recompute_handle=None` vs main: `y`, `dx`, `dweight` and history are
bitwise identical on all three architectures (312 compared per
architecture, 0 differ; W = 1/2/4).
- `tests/test_cake_causal_conv1d_train_kcp.py`: 38 pass (21 on main + 17
new).
- `tests/cpu/test_cake_causal_conv1d_train_kcp_knobs.py`: 11 pass (6 + 5
new).
- The build and API test files are unchanged and pass.
- New multi-GPU test `tests/test_cake_causal_conv1d_train_kcp_dist.py`:
CP2/CP4 rows pass on 4 GPUs, and CP8 rows pass on 8 GPUs over 2 nodes
(GB300).
- The new tests cover:
- `recompute_handle=None` bitwise vs main, and checkpoint with vs
without a handle bitwise.
  - A reused handle raising.
- Collective counts per phase, with positive controls on both host
paths.
- Reentrant and non-reentrant checkpoints, `retain_graph`, and nested
regions.
- Refusals (graph replay, capture, invalid handle) in both the wrapper
and the autograd Function.
  - Retained bytes equal to `nbytes()`.
  - Importing the module not loading the KCP host module.
- The docs build passes with no new warnings.
- A check of the generated kernels confirmed that the convolution
backward's `dweight` accumulates only the rank's own `dy` and its own
input and history rows. Received halo gradients go only into `dx`. This
PR does not change that behavior.

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [27932c3](https://github.com/flashinfer-ai/flashinfer/commit/27932c357b7d423a4890bf77bcc2ed04682b8d4e)

- **作者**: eigen
- **时间**: 2026-10-29T17:52:07Z
- **提交信息**: perf(cake_kda_train): nonblocking KCP table uploads (#7872)

Part of #7815 (KCP host synchronization: no blocking table uploads in
calls or pack preparation).

KCP calls and pack preparation copied launch tables from pageable host
memory with blocking copies. A blocking copy makes the host wait for all
work already queued on the stream. With `workspace=None`, every call
copied its tables again. A trainer that prepares the next pack while the
current one runs, or that issues calls ahead of the GPU, therefore
stalled on the host until all queued work finished. This PR uses pinned,
non-blocking copies, and a context copies its tables once. It changes
only host-side Python. Kernels, records, launch order and numerics are
unchanged, and outputs and gradients are bitwise identical to main.

## What changed
- `build_kcp_context` in `flashinfer.kda_train` copies the context's
tables to the device in one pinned, non-blocking copy on a stream. It
has two new keyword-only options. `heads=` takes an int or a sequence of
ints and derives the head plans during preparation, as host work only.
`stream=` sets the stream for the copy and defaults to the device's
current stream. The host never waits for device work, so pack N+1 can be
prepared while pack N runs. Because the current stream is per thread, a
thread other than the compute thread must pass `stream=`.
- The launch tables of a (context, H) pair now live on the context.
Every workspace and every `workspace=None` call shares them. The first
call that reads a table copies it once, in one asynchronous pinned copy
on the call's stream.
- `ctx.wait_ready(stream)` orders a context prepared on another stream
on the calling stream with an event wait, without a host wait. It also
records the pinned blob on that stream. The KDA KCP entry points and the
conv halo entry points call it on every call. Copies are refused during
CUDA-graph capture, and `graph="replay"` runs the first call of a key
eagerly.
- Ring exchange caches the hop chains per table set, so their tables are
copied once instead of on every call.
- Two private test knobs keep the previous copies reachable for A/B
checks: `upload="blocking"` and `table_cache="workspace"`. The second
works only together with the first.
- A new "Host synchronization" section in
`flashinfer/experimental/cake_kda_train/README.md` documents this
behavior and what it does not cover. It also has a note on CPU binding.
At high CP, eager KCP calls are host-bound. Bind each rank's threads to
the cores of its GPU's socket, because unbound torch threads from
several ranks oversubscribe the CPUs.
- Changed files: `flashinfer/kda_train.py`,
`flashinfer/experimental/cake_kda_train/cake_kcp_plan.py`,
`cake_kcp.py`, `cake_kcp_jit.py`, `README.md` and
`flashinfer/cake_causal_conv1d_train_backend/kcp.py`. Tests: new
`tests/experimental/test_cake_kda_train_kcp_upload.py`, a new helper
`tests/test_helpers/cake_host_sync.py`, and new rows in
`tests/experimental/test_cake_kda_train_kcp_dist.py`.

## Measurements
Measured on one NVIDIA GB200 with PyTorch 2.14.1+cu130. Values are host
time per operation. "Queued" means 200 ms of work was queued on the
stream first. Each tree ran twice with 15 repetitions per run, and each
value is the median of the per-run medians. The cases are `small_P>1
H2`, `small_P=1 H64` and `issue_doc0 H16`. P is the number of
state-passing segments per fragment, and `issue_doc0` is a document from
the #7815 pack. Each case ran with `workspace=None` and with a reused
workspace.

Pack preparation (CP16 issue pack, per rank: context + 64-head plan +
byte queries), host ms with the GPU idle and with 200 ms of work queued
on the stream:

| layout | main idle | main queued | main pageable copies | this PR idle
| this PR queued | this PR pageable copies |
|---|---:|---:|---:|---:|---:|---:|
| zigzag | 2.26 | 173.15 | 36 | 1.44 | 1.43 | 0 |
| per-document zigzag | 3.94 | 174.77 | 36 | 2.88 | 2.89 | 0 |

Calls (host ms, forward / backward; "first" = first call of a new
context, "steady" = later calls; copies are per forward + backward
pair):

| case | workspace | steady idle, main | steady idle, this PR | steady
queued, main | steady queued, this PR | steady copies main -> this PR |
first idle, main | first idle, this PR | first queued, main | first
queued, this PR | first copies main -> this PR |
|---|---|---:|---:|---:|---:|---|---:|---:|---:|---:|---|
| small_P>1 H2 | `None` | 3.246 / 3.655 | 0.930 / 1.254 | 173.349 /
173.588 | 0.930 / 1.264 | 27 pageable -> 0 pageable, 0 pinned | 4.395 /
3.950 | 5.221 / 3.938 | 175.410 / 173.912 | 5.436 / 4.165 | 37 pageable
-> 0 pageable, 14 pinned |
| small_P>1 H2 | reused | 0.446 / 0.562 | 0.473 / 0.578 | 0.465 / 0.584
| 0.503 / 0.608 | 0 pageable -> 0 pageable, 0 pinned | 5.844 / 3.261 |
5.473 / 3.935 | 174.669 / 171.864 | 4.642 / 3.520 | 33 pageable -> 0
pageable, 14 pinned |
| small_P=1 H64 | `None` | 0.968 / 1.394 | 0.631 / 0.960 | 171.505 /
171.806 | 0.647 / 0.979 | 10 pageable -> 0 pageable, 0 pinned | 1.731 /
1.480 | 1.704 / 1.595 | 172.474 / 171.849 | 1.695 / 1.649 | 19 pageable
-> 0 pageable, 8 pinned |
| small_P=1 H64 | reused | 0.297 / 0.459 | 0.306 / 0.470 | 0.331 / 0.475
| 0.351 / 0.497 | 0 pageable -> 0 pageable, 0 pinned | 2.307 / 1.464 |
2.326 / 1.794 | 172.393 / 171.658 | 1.756 / 1.426 | 16 pageable -> 0
pageable, 8 pinned |
| issue_doc0 H16 | `None` | 4.566 / 5.309 | 0.954 / 1.298 | 174.784 /
175.398 | 0.889 / 1.206 | 27 pageable -> 0 pageable, 0 pinned | 5.237 /
5.350 | 4.771 / 3.969 | 176.189 / 175.449 | 4.917 / 3.978 | 37 pageable
-> 0 pageable, 14 pinned |
| issue_doc0 H16 | reused | 0.498 / 0.611 | 0.502 / 0.606 | 0.503 /
0.616 | 0.499 / 0.617 | 0 pageable -> 0 pageable, 0 pinned | 7.383 /
4.676 | 6.353 / 4.862 | 176.564 / 173.588 | 7.084 / 3.979 | 33 pageable
-> 0 pageable, 14 pinned |

- Preparation: pageable copies drop from 36 to 0. With 200 ms queued,
host time drops from 173.15 to 1.43 ms (zigzag) and from 174.77 to 2.89
ms (per-document zigzag). Idle preparation also gets cheaper: 2.26 ->
1.44 ms and 3.94 -> 2.88 ms.
- Calls with 200 ms queued: on main, every `workspace=None` call waits
for the queue (171-175 ms). With this PR they take 0.6-1.3 ms. Steady
`workspace=None` calls are also cheaper with the GPU idle because the
tables are no longer copied again. For example, the `issue_doc0` forward
drops from 4.566 to 0.954 ms.
- Steady calls with a reused workspace show no change beyond noise, with
ratios of 0.99-1.08. The largest relative change is the queued
`small_P>1 H2` forward: 0.465 -> 0.503 ms (1.08x, +0.038 ms).
- First call of a new context with the GPU idle: mixed, at 0.74-1.23x of
main. These numbers are noisy because each tree ran only twice. The
first call now allocates pinned memory and does one batched upload. For
example, the `small_P>1 H2` forward goes from 4.395 to 5.221 ms. With
work queued, the first call no longer waits: about 172-176 ms becomes
1.4-7.1 ms.
- Copies per forward + backward pair: first calls go from 37/33/19/16
pageable copies on main to 0 pageable and 14 or 8 pinned. Steady
`workspace=None` calls go from 27/10 pageable to 0.

We also measured this PR combined with #7855 and #7846 in a full model:
a 34-layer model step on 16 GB200 GPUs with activation checkpointing and
the next step's packs prepared on a side thread. Pageable host-to-device
copies per step dropped from 5176 to 0 with `workspace=None` and from
232 to 0 with one workspace per pack. Median step time with
`workspace=None` dropped from 6980 to 5957 ms, and with one workspace
per pack from 6008 to 5969 ms.

## Validation
- GB200 (sm_100a), GB300 (sm_103a) and R200 (sm_107a): main had 761
passed. This PR had 783 passed, 3 skipped and 0 failed on each GPU. The
3 skips are the 8-rank rows on a 4-GPU node. Those rows ran on 2 GB200
nodes, and 24/24 passed (3 rows x 8 ranks).
- Results per file: `test_cake_kda_train_kcp.py` 691/691 on both trees,
`test_cake_kda_train_kcp_build.py` 25,
`test_cake_causal_conv1d_train_kcp*.py` 21 + 8 + 6, the new
`test_cake_kda_train_kcp_upload.py` 18/18, and
`test_cake_kda_train_kcp_dist.py` 14 passed + 3 skipped (10 on main).
- The new tests check for no pageable copy and no synchronizing
operation in pack preparation, in the first call and in steady calls.
They cover runs with and without a workspace, graph replay, and
preparation on a side stream or a side thread. The previous path is the
negative control: its pageable copies equal its synchronization
warnings, 103 and 34 in two windows. The tests also check the following:
  - First calls do at least one pinned copy (14 and 8).
  - Steady calls do 0 copies and no device allocation.
- A context cached on one stream and used on a second stream waits for
its upload.
  - Repeated ring calls add no uploads.
  - Releasing a context frees its tables without the cycle collector.
- The copy counter does not need device tracing, so these checks also
run on R200, where the profiler cannot trace the device.
- Bitwise equality with main covers outputs and gradients of the saved,
`workspace=None`, replay, checkpoint and graph-replay paths, plus the
conv halo. On the final head, 198/198 at 2 ranks and 528/528 at 4 ranks
were identical. The 1056/1056 at 8 ranks ran on an earlier revision of
this PR, before the review fixes. On the final head, the 8-rank rows
(24/24) check that the new path equals the previous blocking path
bitwise inside the same tree.
- `ruff`, `ruff format` and `mypy` are clean.

## Limits
- `workspace=None` calls still allocate their pools on every call. A
miss in the caching allocator can call `cudaMalloc`, and an
out-of-memory retry synchronizes. Under memory pressure, reuse a
workspace.
- The debug paths (`spec3_probe`, `debug_sequence`) and
`TORCH_NCCL_BLOCKING_WAIT=1` are not covered.
- The copy counter in the tests cannot see a copy issued directly from
C++. Where the profiler can trace the device, the counter and the
profiler agreed in every window.
- One case is not tested: `wait_ready(S)` while S is capturing and the
current stream is not.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* KCP contexts can upload device tables asynchronously, with an option
to select the stream used for uploads.
  * Head plans can be prepared in advance for one or more head counts.
  * Added a readiness check for coordinating table use across streams.
  * Asynchronous uploads are not supported during CUDA graph capture.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fd2b1f1](https://github.com/flashinfer-ai/flashinfer/commit/fd2b1f160a596c7ece256c5c3c0fcbc62306592e)

- **作者**: eigen
- **时间**: 2026-10-29T17:47:23Z
- **提交信息**: perf(cake_kda_train): bisect the KCP halo-plan owner lookup (#7855)

Part of #7815 (KCP coverage and host cost at CP8-CP64).

Building the context-parallel (KCP) plan for the Cake KDA training
backend spent too much host time at large CP. To find the fragment that
owns each halo row, `_halo_sources` scanned the document's fragment
chain. That costs O(chain length) per row and O(CP^2) per pack at large
CP. It now bisects each document's sorted fragment offsets. This changes
host-side planning only. The halo tables it produces are identical, and
no kernel, device table, launch or numerics change.

## What changed

- `_halo_sources` in
`flashinfer/experimental/cake_kda_train/cake_kcp_plan.py` now bisects
each document's sorted fragment offsets to find the owner fragment,
where it used to scan the document's chain.
`flashinfer.kda_train.build_kcp_context` uses this code.
- New CPU tests in `tests/experimental/test_cake_kda_train_kcp.py` check
the bisect against a copy of the old scan.

## Measurements

Packs: `issue5` is the 5-document pack from #7815 (56843, 59310, 72971,
23218 and 38408 tokens). `seed6` is a seeded 6-document pack. Each pack
runs at CP 8/16/32/64 with contiguous, zigzag and per-document zigzag
layouts. The last two columns are the per-rank time to build the KCP
context plus the 64-head plan. Measured on a CPU node with Python 3.12
and PyTorch 2.14.1; each value is the median of 7 repeats.

| pack | CP | layout | fragments | `_halo_sources` main (ms) | this PR
(ms) | speedup | context + head plan per rank, main (ms) | this PR (ms)
|
|---|---:|---|---:|---:|---:|---:|---:|---:|
| issue5 | 8 | contiguous | 12 | 0.029 | 0.028 | 1.0x | 0.71 | 0.69 |
| issue5 | 8 | zigzag | 20 | 0.064 | 0.056 | 1.1x | 1.76 | 1.74 |
| issue5 | 8 | per-document zigzag | 80 | 0.555 | 0.273 | 2.0x | 2.78 |
2.50 |
| issue5 | 16 | contiguous | 20 | 0.065 | 0.058 | 1.1x | 0.65 | 0.64 |
| issue5 | 16 | zigzag | 36 | 0.162 | 0.116 | 1.4x | 1.83 | 1.78 |
| issue5 | 16 | per-document zigzag | 160 | 1.831 | 0.580 | 3.2x | 4.38
| 3.12 |
| issue5 | 32 | contiguous | 36 | 0.167 | 0.119 | 1.4x | 0.83 | 0.79 |
| issue5 | 32 | zigzag | 68 | 0.457 | 0.239 | 1.9x | 2.22 | 2.00 |
| issue5 | 32 | per-document zigzag | 320 | 6.566 | 1.201 | 5.5x | 10.00
| 4.59 |
| issue5 | 64 | contiguous | 68 | 0.456 | 0.239 | 1.9x | 1.38 | 1.16 |
| issue5 | 64 | zigzag | 132 | 1.438 | 0.490 | 2.9x | 3.57 | 2.62 |
| issue5 | 64 | per-document zigzag | 640 | 24.924 | 2.760 | 9.0x |
30.50 | 8.15 |
| seed6 | 8 | contiguous | 13 | 0.028 | 0.029 | 1.0x | 0.73 | 0.72 |
| seed6 | 8 | zigzag | 21 | 0.062 | 0.057 | 1.1x | 0.92 | 0.92 |
| seed6 | 8 | per-document zigzag | 96 | 0.666 | 0.330 | 2.0x | 3.32 |
2.97 |
| seed6 | 16 | contiguous | 21 | 0.062 | 0.058 | 1.1x | 0.71 | 0.70 |
| seed6 | 16 | zigzag | 37 | 0.152 | 0.117 | 1.3x | 1.89 | 1.86 |
| seed6 | 16 | per-document zigzag | 192 | 2.218 | 0.691 | 3.2x | 5.25 |
3.75 |
| seed6 | 32 | contiguous | 37 | 0.153 | 0.118 | 1.3x | 0.90 | 1.02 |
| seed6 | 32 | zigzag | 69 | 0.412 | 0.237 | 1.7x | 2.27 | 2.06 |
| seed6 | 32 | per-document zigzag | 384 | 8.048 | 1.604 | 5.0x | 12.20
| 5.68 |
| seed6 | 64 | contiguous | 69 | 0.417 | 0.239 | 1.7x | 1.35 | 1.17 |
| seed6 | 64 | zigzag | 133 | 1.249 | 0.482 | 2.6x | 3.44 | 2.66 |
| seed6 | 64 | per-document zigzag | 768 | 30.126 | 3.369 | 8.9x | 37.07
| 9.90 |

- Per-document zigzag benefits most. At CP64, `_halo_sources` drops from
24.9 to 2.8 ms (`issue5`, 9.0x) and from 30.1 to 3.4 ms (`seed6`, 8.9x).
Context plus 64-head plan per rank drops from 30.5 to 8.2 ms and from
37.1 to 9.9 ms. At CP16 the `_halo_sources` times go from 1.8 to 0.6 ms
and from 2.2 to 0.7 ms.
- Contiguous and zigzag rows are 1.0-2.9x faster in `_halo_sources`. One
context-plus-plan row is slower: `seed6` at CP32 with the contiguous
layout, 0.90 to 1.02 ms (+0.12 ms), while its `_halo_sources` time is
1.3x faster.

## Validation

- Bisect vs. old scan on random ragged partitions: 378 partitions at W =
2..64 (per W, 3 random tables plus contiguous, zigzag and per-document
zigzag), each at halo widths 1-4. All 1512 comparisons are equal, and
the test asserts the partition count.
- Bisect vs. old scan on every (row, CP, layout) of the existing test
cases at halo widths 1, 3 and 4: all equal.
- `tests/experimental/test_cake_kda_train_kcp.py` on CPU: 646 passed
(644 on main plus the 2 new tests), 0 failed. GPU rows skip on CPU. The
14 FP64 fake-backend rows pass on both main and this PR, and the KCP
build tests pass 25/25.
- On GB300 (sm_103a, PyTorch 2.14.1+cu130), the full
`tests/experimental/test_cake_kda_train_kcp.py` passes 693/693 with this
PR (691/691 on main), and the multi-GPU KCP rows (W = 2 and 4) pass.
- `ruff`, `ruff format` and `mypy` are clean.

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [78b4734](https://github.com/flashinfer-ai/flashinfer/commit/78b4734b2d6245c096d9780f5664c40cb7548fa5)

- **作者**: eigen
- **时间**: 2026-10-29T17:46:17Z
- **提交信息**: perf(cake_kda_kcp): with grad, lower the forward-only workspace of the KCP route (#7841)

A KCP workspace that had only run forwards was sized like a backward
workspace. This covers the first forward of a training step before any
backward, and evaluation forwards. This PR gives a forward-only
workspace its own, smaller layout. It also allocates pools that only a
backward or a saving forward needs on first read instead of up front.
This is a follow-up to #6919, where the forward-only (B1) peak was above
1.0x of the FLA KCP baseline.

Scope: `chunk_kda_kcp`, `chunk_kda_kcp_fwd`, the caller-held
`KcpWorkspace` and `kcp_workspace_bytes` in `flashinfer.kda_train`.
Backward arenas, kernels, records and launches do not change. A backward
still upgrades a forward-only workspace to the backward size as before.
Outputs, saved sets and gradients are bitwise identical to main.

## What changed

- **Forward-only arena layout.** A forward-only rank arena now uses a
KCP forward layout, `fwd_kcp`. It has no segment state blocks, and
`akk_int` sits under the h tape beside `kb`. The arena now needs 2432 B
per internal token-head, down from 2560.
- **Lazy pools.** A forward-only workspace now allocates its c1 receive,
transfer staging and carry pools on first read. A forward that returns a
saved set writes fresh saved-set tensors instead, so it never allocates
these pools.
- **Exact prediction.** `kcp_arena_layout`, `kcp_workspace_bytes(...,
backward=False, save_transfer=...)` and `workspace_bytes` now predict
both forward-only states exactly, and they honor `save_transfer`.
Without `save_transfer`, a saving forward reads the c1 receive and
transfer staging pools, so those pools are counted. The ring exchange
never allocates the c1 receive pool. The public `kcp_workspace_bytes`
now defaults `save_transfer` to `None` and resolves it the way the a2a
forward does (to `True`).
- **Graph cache.** Some graph-cache entries pin the workspace, and their
keys held the forward-only lazy pools. When `pool()` first allocates one
of those pools, these entries are dropped, since they and their captured
memory could no longer be reached.

## Measurements

Setup:
- GB300 (sm_103a), PyTorch 2.14.1+cu130. Values are in MiB, max over
ranks.
- Pack Q1: 249,856 tokens in 4 documents, H = 64.
- B1: one forward with autograd of the causal-conv1d (8192 channels,
with the context-parallel halo) + KDA module, run on a fresh, empty
workspace in a fresh process.
- "First B1 peak": the peak allocated during that first call, above the
allocation after building the inputs.
- "FLA KCP B1": the steady B1 peak of the FLA KCP baseline (FLA commit
9d478fac, `use_tf32x3_affine_chain=True`) for the same call. The
per-document zigzag rows use FLA's contiguous number, which is its
better layout.

| CP | layout | forward-only workspace, main | this PR | first B1 peak,
main | this PR | change | FLA KCP B1 | main / FLA | this PR / FLA |
|---:|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 4 | contiguous | 9965.1 | 9362.1 | 12039.6 | 11437.6 | -602.0 |
10742.1 | 1.121 | 1.065 |
| 4 | zigzag | 10093.1 | 9425.1 | 12240.3 | 11571.3 | -669.0 | 10746.2 |
1.139 | 1.077 |
| 4 | per-document zigzag | 10076.1 | 9522.1 | 12121.3 | 11567.3 |
-554.0 | 10742.1 | 1.128 | 1.077 |
| 8 | per-document zigzag | 5254.1 | 4939.1 | 6350.5 | 6036.5 | -314.0 |
5374.1 | 1.182 | 1.123 |

Results:
- The steady B1 per-call peak, excluding the workspace, is unchanged in
every row (+0.0 MiB). The whole saving comes from the workspace.
- The first B1 peak is still above the FLA KCP baseline: 1.065-1.077x at
CP4 and 1.123x at CP8.
- GB200 (sm_100a) gives the same byte counts as GB300 in all four rows.
- On R200 (sm_107a), the first B1 peak is lower by 554-765 MiB at CP4
(0.939-0.954x of main), 314 MiB at CP8 (0.951x) and 190 MiB at CP16
(0.943x). CP8 and CP16 use per-document zigzag.
- Training step (B3: forward, checkpoint replay and backward under
`torch.utils.checkpoint(use_reentrant=False)`): the first-step peak,
retained workspace and steady peak equal main (+0.0 MiB) at CP4, CP8 and
CP16 on GB300, GB200 and R200.
- Latency is unchanged. The PR/main ratio at CP4 on GB300 is
0.9993-1.0000, with 95% CIs inside 0.98-1.02. On GB200, every CI is
inside 0.98-1.02.

## Validation

- **Bitwise A/B against main (GB300).** At CP4 (packs Q1 and Q2;
contiguous, zigzag and per-document zigzag), 1056/1056 KDA and 1536/1536
module tensor digests are identical. With per-document zigzag, 336/336
KDA and 512/512 module digests are identical at CP8, and 672/672 and
1024/1024 at CP16. CP4 gives the same result on GB200 (1008/1008) and
R200.
- **Forward-only A/B.** Over the explicit, autograd, upgraded-workspace,
NaN-poisoned and `workspace=None` modes, all digests are equal except
the never-written carry bytes, which are excluded by construction.
- **New tests:**
  - Host byte tests for layout bytes and for the prediction.
- GPU tests for bitwise outputs, saved sets and gradients with a
NaN-filled arena.
  - Tests for the backward upgrade and for `workspace=None`.
  - Graph replay on the forward-only layout followed by a backward.
  - Graph replay after a forward without a saved set.
- **Carry plane comparison.** A test helper compares only the written
bytes of the saved carry plane. The plane is a fresh `torch.empty`
tensor, and some of its slots are never written and never read: the
slots beyond `n_in` on a rank with `n_out > n_in`, and the slots of
zero-length fragments. The multi-GPU test fills those slots with NaN
before the backward, still requires bitwise gradients, and reports the
poisoned bytes per rank.
- **Test runs.** `tests/experimental/test_cake_kda_train_kcp.py` passes
695 tests on the PR (691 on main plus 4 new), with 0 skipped and 0
failed, on GB300, GB200 and R200. The KCP build, multi-GPU (W = 2 and 4)
and causal-conv KCP test files pass unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an option to use a more compact workspace layout for
forward-only context-parallel workloads.
* Forward-only workspaces can allocate certain memory pools on first use
and allocate additional memory when needed. Workspaces can also be
upgraded to support backward passes.
* When `save_transfer` is omitted, workspace sizing now uses the
configured default; explicitly setting it still overrides that default.
* The compact layout produces equivalent forward results to the existing
layout, including during graph replay.

* **Documentation**
* Clarified workspace memory requirements for forward-only and
backward-capable workloads, including how saved transfers and ring
exchange affect allocation.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [202850d](https://github.com/flashinfer-ai/flashinfer/commit/202850d5ddeabed6d07af6bf1c6833222593d773)

- **作者**: eigen
- **时间**: 2026-10-29T17:44:50Z
- **提交信息**: perf(cake_ulysses): faster world-8 bf16 direct gather, early first-unit zone (#7808)

Cake's Ulysses all-to-all for `flashinfer.comm` sequence parallelism
(scatter heads / gather heads over NVLink) has 48 programs: bf16 / f16 /
f32 × world sizes 2 / 4 / 6 / 8 × both directions × two routes. The
staged route serves plain outputs. The direct route writes straight into
peers' registered outputs from `allocate_output`. This PR updates 1 of
them: the direct-route program at world size 8 for bf16, gather heads.
It now loads the first part of its first chunk before waiting for the
destination's entry token. If the destination has not entered the launch
yet, those first units go into a zone at the tail of the destination's
signal allocation, and the destination copies them into its output
before its launch ends; if the token is already there, the CTA stores
straight into the output and skips one CTA barrier. The zone grows the
signal allocation from 864 to 1,138,688 32-bit words (4,554,752 bytes
per rank), and outputs are bit-identical. The baseline is the previous
Cake version of the same program, which FlashInfer main ships today
(merged in #7688). At world size 8 with gather heads the speedup over it
is 1.016x on B300 and 1.030x on B200. On the other seven rows both
columns run the same program (only the signal allocation size differs),
so their differences are spread between two builds of the same code
(0.997x to 1.001x on B300, 0.997x to 1.000x on B200).

**NVIDIA B300 SXM6 AC (sm_103a), 8 GPUs, CUDA 13.4, PyTorch
2.14.1+cu130.** bf16, batch 1, global sequence length 32760, head dim
128, heads 40 at world 2 / 4 / 8 and 48 at world 6 (local sequence 16380
/ 8190 / 5460 / 4095 at world 2 / 4 / 6 / 8), outputs allocated with
`allocate_output` (registered). Latency is in us per call, measured from
the beginning of the last rank's kernel to the end of the last rank's
kernel (max over ranks of kernel end time minus max over ranks of kernel
begin time), median over 20 rounds (two sessions of 10 interleaved
rounds, 15 calls per round), with both versions measured in the same
process on the same outputs. Speedup = previous Cake / this PR.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---|---|---|---|---|---|
| 2 | 40 | scatter heads | 128.538 | 128.851 | 0.998x |
| 2 | 40 | gather heads | 127.755 | 127.839 | 0.999x |
| 4 | 40 | scatter heads | 103.429 | 103.294 | 1.001x |
| 4 | 40 | gather heads | 103.591 | 103.917 | 0.997x |
| 6 | 48 | scatter heads | 93.457 | 93.520 | 0.999x |
| 6 | 48 | gather heads | 94.715 | 94.962 | 0.997x |
| 8 | 40 | scatter heads | 66.095 | 66.260 | 0.998x |
| 8 | 40 | gather heads | 66.928 | 65.886 | 1.016x |

**NVIDIA B200 (sm_100a), 8 GPUs, CUDA 13.4, PyTorch 2.14.1+cu130.** Same
shapes, outputs, latency definition, median and same-process measurement
as above. Speedup = previous Cake / this PR.

| world | heads | direction | previous Cake (us) | this PR (us) |
speedup |
|---|---|---|---|---|---|
| 2 | 40 | scatter heads | 128.778 | 128.751 | 1.000x |
| 2 | 40 | gather heads | 128.117 | 128.118 | 1.000x |
| 4 | 40 | scatter heads | 102.376 | 102.697 | 0.997x |
| 4 | 40 | gather heads | 102.904 | 103.082 | 0.998x |
| 6 | 48 | scatter heads | 92.707 | 92.880 | 0.998x |
| 6 | 48 | gather heads | 94.253 | 94.357 | 0.999x |
| 8 | 40 | scatter heads | 65.770 | 65.950 | 0.997x |
| 8 | 40 | gather heads | 66.405 | 64.502 | 1.030x |

Cake also ships the staged route (plain outputs) for all three data
types and the direct route for the other 23 programs (world sizes 2, 4
and 6 for bf16 / f16 / f32 in both directions, plus world size 8 for f16
/ f32 in both directions and for bf16 scatter heads), all unchanged by
this PR, and the whole family ships on sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved correctness of world-8 bf16 direct-gather operations when
participating streams reach a launch at different times. Data for
destinations that have not yet entered the launch is now handled when
those destinations become available. This behavior is also covered
across unaligned inputs, chunk and slot boundaries, CUDA graph replays,
and alternating staged routes. Other gather paths and data types remain
unaffected.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [c3d8e27](https://github.com/flashinfer-ai/flashinfer/commit/c3d8e27d183e68afcc0c400dca98f2e6340fa67f)

- **作者**: eigen
- **时间**: 2026-10-29T17:42:44Z
- **提交信息**: perf(cake_gdn): communication-free KCP checkpoint recompute with a recompute handle (#7852)

Part of #7818 (GDN half; the convolution half is #7846).

## Problem

With `torch.utils.checkpoint(..., use_reentrant=False)`, torch runs the
checkpointed forward a second time inside `.backward()` to rebuild the
saved tensors. The non-reentrant checkpoint keeps none of the forward's
saved tensors. As a result, `flashinfer.gdn_train.chunk_gdn_kcp` repeats
its cross-rank state exchanges during that recompute.

## Change

This PR adds a public type, `flashinfer.gdn_train.KcpRecomputeHandle`,
and a `recompute_handle=None` keyword on `chunk_gdn_kcp`:

```python
def layer(x, handle):
    ...  # convolution, split, gates
    return chunk_gdn_kcp(q, k, v, g, beta, ctx, recompute_handle=handle)

y = torch.utils.checkpoint.checkpoint(layer, x, KcpRecomputeHandle(), use_reentrant=False)
```

- **Original forward:** exchanges states as before. It stores this
rank's incoming boundary states `S_in` in the handle under key `"gdn"`.
This is the saved set's own tensor, not a copy.
- **Recompute:** reads `S_in` back and runs no collective. It skips the
state exchange, the summary walk over the crossing fragments and the
owner merge. It still runs the prep program, the local segment walks,
the carry merges (only when a fragment has several segments), the state
walk from `S_in` and the output program.
- **Backward:** exchanges as before. Gradients are bitwise identical to
the same checkpoint without a handle and to the non-checkpointed
autograd path.

**Memory.** The handle keeps only `S_in`: `n_in * HV * 128 * 128 * 4`
bytes per rank and layer, which is `gdn_kcp_saved_bytes(ctx, H_qk=...,
HV=..., save_mode="light", save_transfer=False, with_conv=False)`. It
holds this until the checkpoint frame holding the handle is freed.
Without a handle, the checkpointed forward still keeps nothing.

**Rules**
- Use one handle per layer and micro-step, and create it outside the
outermost checkpoint region.
- A handle holds one entry per key. It serves one GDN call and at most
one context-parallel convolution call, whose halo rows go under key
`"conv"` (#7846).
- The handle requires `boundary_mode="saved"` and `graph="off"`, and
implies `save_transfer=False`.
- If a forward finds no entry, it exchanges and stores one. This also
covers nested checkpoint regions. If an entry is found outside the
backward, the call raises. That catches a handle reused across
micro-steps.

## Tests

CPU tests cover:
- bitwise equality (one and two segments, with and without the kept
recompute tapes)
- retention
- a second backward with `retain_graph`
- the entry rules

Multi-GPU rows count `torch.distributed` collectives and waits per phase
through `tests/test_helpers/kcp_collective_shims.py`. Whole-layer rows
run context-parallel convolution, L2 norm and GDN in one checkpointed
region.

## Results

Both setups use torch 2.14.1+cu130.

| Setup | Hardware | Rows | Status |
|---|---|---|---|
| CP2, CP4 | NVIDIA GB200 (SM100) | 13 multi-GPU rows: contiguous,
zigzag, per-document zigzag and ragged splits, including empty ranks and
1-token ranks | All 42 rank records pass |
| CP8 | One node, 8x NVIDIA B200 (SM100) | C6, C8 (below) | All checks
pass on all 8 ranks |

### GDN: collectives / waits per rank

The counts are the same at CP2, CP4 and CP8, on all ranks.

| | original forward | recompute | backward |
|---|---|---|---|
| plain checkpoint | 2 / 2 | 2 / 2 | 2 / 2 |
| with handle | 2 / 2 | 0 / 0 | 2 / 2 |

- CP2/CP4: rows whose ranks hold no crossing fragment issue 0 in every
phase.
- CP2/CP4: with the ring exchange, the recompute also issues 0
point-to-point batches.
- On every rank, results are bitwise equal to the plain checkpoint and
to the direct pass.
- On every rank, the retained bytes equal `S_in`. For example, 1,572,864
B on one rank of a 4-rank per-document zigzag row with 4 Q/K heads and
12 value heads.

### GDN: CP8 correctness rows

| Row | Tokens | Heads | Split | Retained bytes (= `S_in`) |
|---|---|---|---|---|
| C6 | 65,553 | (16, 48) | zigzag | 3,145,728 B on rank 0; 6,291,456 B
on ranks 1-7 |
| C8 | documents of 10,240 / 8,192 / 2,085 | (16, 48) | contiguous, 2-3
segments per rank | equal to `S_in` |

- Outputs and all five gradients are bitwise equal to the plain
checkpoint and to the direct pass on all 8 ranks.
- A second backward with `retain_graph` reuses the entry.

### GDN: CP8 step time

These numbers are for one checkpointed GDN layer with heads (16, 48),
per-document zigzag split, at CP8. Each value is the median of the
slowest rank over 20 steps after 3 warm-ups. Plain and handle runs were
interleaved. `bwd` includes the recompute. Ratio = handle / plain.

| Pack (total tokens / documents) | fwd+bwd plain ms | fwd+bwd handle ms
| ratio | bwd plain ms | bwd handle ms | ratio |
|---|---|---|---|---|---|---|
| 241,817 / 6 | 7.655 | 6.614 | 0.864 | 5.015 | 3.976 | 0.793 |
| 254,976 / 1 | 8.174 | 7.087 | 0.867 | 5.370 | 4.278 | 0.797 |

Outputs and gradients are bitwise equal between plain and handle on all
8 ranks.

### Whole layer: collectives / waits per rank

This covers context-parallel convolution, L2 norm and GDN in one
checkpointed region, with the convolution taking the same handle
(#7846).

| Setup | Rows |
|---|---|
| CP4 | GB200 |
| CP8 | B200: L8 (per-document zigzag), L8r (ragged, with empty ranks) |

The counts are the same in both setups, on all ranks:

| | original forward | recompute | backward |
|---|---|---|---|
| plain checkpoint | 3 / 3 | 3 / 3 | 3 / 3 |
| with handle | 3 / 3 | 0 / 0 | 3 / 3 |

Outputs and gradients are bitwise equal to the plain checkpoint and to
the direct pass on every rank.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional recomputation handle for checkpointed GDN workloads.
During backward recomputation, it reuses saved incoming state and avoids
communication exchanges; backward still performs required exchanges.
* The handle can retain saved state across repeated backward passes and
can be cleared when no longer needed.
* Handle use requires saved boundary mode and graph mode off. Separate
handles are needed for separate convolution calls.
* **Documentation**
  * Added guidance on using the handle and its requirements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5b937e7](https://github.com/flashinfer-ai/flashinfer/commit/5b937e70282df53ad05732a6d5c26927f728ad08)

- **作者**: eigen
- **时间**: 2026-10-29T17:38:45Z
- **提交信息**: perf(cake_kda_train): WY, dAqk and fused-gradient programs take one-CTA-per-item work from Cluster Launch Control (#7873)

The experimental `cake_kda_train` backend handles packed Kimi Delta
Attention chunked training: forward and backward, head dim 128, chunk
length 64, BF16 q/k/v and an FP32 gate. This PR changes three of its
kernel programs in all 12 compiled forms: the WY representation, dAqk
and fused dq/dk/dg gradient programs. They no longer run on a persistent
grid of one CTA per SM. Instead they launch one CTA per work item and
get their items from Cluster Launch Control. A kernel resident on
another stream now slows the KDA step in proportion to the SMs it
occupies, where before even one resident 1-thread block caused a fixed
second-wave penalty. Compared with current `main`, time with nothing
else resident is unchanged. With a side-stream kernel resident, the
forward pass takes 0.899–0.934× main's time and the backward pass
0.799–0.864×.

*NVIDIA GB200 (sm_100a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130. One
packed batch of 4 documents (lengths 120001, 70707, 65537, 5148; S =
261393 tokens), H = 4. Times are the median of 42 runs per cell (2
processes × 3 rounds × 7 reps). "Side stream" is what is resident on
another stream during the KDA call. Slowdown is relative to the same
arm's time with nothing resident. Ideal = 152/(152−k) for k occupied
SMs.*

| Pass | Side stream | main (ms) | this PR (ms) | PR / main (lower is
better) | main slowdown | PR slowdown | ideal |
|---|---|---:|---:|---:|---:|---:|---:|
| fwd | none | 1.3963 | 1.3964 | 1.000 | 1.000 | 1.000 | 1.000 |
| fwd | 1 block × 1 thread | 1.5602 | 1.4025 | 0.899 | 1.117 | 1.004 |
1.007 |
| fwd | 1 block × 128 threads | 1.5602 | 1.4025 | 0.899 | 1.117 | 1.004
| 1.007 |
| fwd | 16 blocks × 640 threads | 1.6524 | 1.5131 | 0.916 | 1.183 |
1.084 | 1.118 |
| fwd | 32 blocks × 640 threads | 1.7875 | 1.6688 | 0.934 | 1.280 |
1.195 | 1.267 |
| bwd | none | 3.2171 | 3.2227 | 1.002 | 1.000 | 1.000 | 1.000 |
| bwd | 1 block × 1 thread | 4.0972 | 3.2754 | 0.799 | 1.274 | 1.016 |
1.007 |
| bwd | 1 block × 128 threads | 4.0967 | 3.2764 | 0.800 | 1.273 | 1.017
| 1.007 |
| bwd | 16 blocks × 640 threads | 4.1847 | 3.4618 | 0.827 | 1.301 |
1.074 | 1.118 |
| bwd | 32 blocks × 640 threads | 4.3808 | 3.7854 | 0.864 | 1.362 |
1.175 | 1.267 |

The backend also provides the `chunk_kda`, `chunk_kda_fwd` and
`chunk_kda_bwd` entry points with segmented and serial routes, "light"
and "tape" saved-activation sets, and a context-parallel (KCP) variant,
and it targets sm_100a, sm_103a and sm_107a (B200/GB200, B300/GB300,
R200), though these measurements cover only GB200 (sm_100a).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved validation for oversized tensor tiles, with errors that
identify the affected dimension and clarify when edge tiles may extend
beyond the source.
* Corrected output calculations in one training-kernel path and expanded
loading of gradient values across each warp’s positions.

* **Improvements**
* Updated work distribution across training kernels to handle items
dynamically, with launch grids sized to the work rather than capped by
the number of streaming multiprocessors.
* Revised chunk and sequence indexing for more reliable handling of
boundary cases.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [2d1a97b](https://github.com/flashinfer-ai/flashinfer/commit/2d1a97b50fed01cf8547cb190def81af491a1370)

- **作者**: eigen
- **时间**: 2026-10-29T17:36:53Z
- **提交信息**: benchmark(cake_dsa_indexer_sampling): time with the call's own max_seqlen_k (#7829)

Follow-up to #7825 that addresses its three review comments.

- `--time` builds both timed arms with the loaded call's `max_seqlen_k`,
not `max(seg_k)`. The timed plan is now the plan the script prints. The
`--json` timing section records the bound.
- The `--time` argument checks (a CUDA device, no `--arch` / `--num-sms`
override) run before the host replay. On a CPU device the script exits
in seconds, not after the replay.
- The README says the console prints totals, per-segment and per-CTA
counts. Per-unit records come from `--csv` or `--json`.

Checked on GB300: a saved rank with `max_seqlen_k` raised to 262144
times with that bound, and its printed and timed plans agree. Output
bits are identical in both arms.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified that benchmark reports include total failed work-unit
counts, per-segment counts, and a CTA summary with the number of CTAs
reporting failures, the maximum failures on one CTA, and a histogram.
* Documented that individual work-unit records are available in JSON and
CSV output, and that timing comparisons use `sample_tiles_max=0`.
* **Improvements**
* Timing reports now include the sequence-length bound used for each
result.
* CUDA device and architecture compatibility are checked before replay
begins.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Avery Huang <averyh@nvidia.com>

### [615d9f9](https://github.com/flashinfer-ai/flashinfer/commit/615d9f9b78d3689aad35f5555636b97423228f00)

- **作者**: eigen
- **时间**: 2026-10-29T17:30:03Z
- **提交信息**: perf(cake_fused_qk_rope_fp8_append): persistent stage for B200 prefill of few requests (#7842)

The Cake fused QK RMSNorm + NeoX RoPE + paged KV-cache append kernel has
two data-type variants in FlashInfer: BF16 (`cake_fused_qk_rope_append`)
and FP8 E4M3 (`cake_fused_qk_rope_fp8_append`). This PR changes only the
FP8 variant. The stage `fp8_e4m3_min_blocks10_persistent1`, which #7820
added for sm_103a, now also ships for sm_100a. On B200 (sm_100a, 148
SMs), a prefill call with 1 to 16 requests and more than four waves
(`(num_rows + num_requests) x num_kv_heads` above 4 x 9 x 148 CTAs) now
uses this stage instead of `fp8_e4m3_min_blocks10`. B300 already uses
the same bound. All other calls keep their stages. The stage launches a
persistent grid: ten resident CTAs per SM times the SM count, rounded
down to a multiple of the KV-head count and capped at the item count
(`(num_rows + num_requests) x num_kv_heads`). Each resident CTA runs the
table validation scan, the scale loads and the validity vote once. It
then loops over its items of one KV head with the same per-item math and
stores as the existing stages. Its outputs are bitwise identical to the
existing stage on every measured row. The baseline is the FP8 package on
FlashInfer main (caa3fd0f20), which is the previous Cake version. The
changed row, `X_prefill_64x8_B1_Q1024_q1_n2`, goes from 17.168 to 15.285
µs, a 1.1232x speedup (1.1207x to 1.1225x per session). The other 43
rows run identical device code and launch grids in both packages. Their
ratios of 0.9859 to 1.0111 are measurement spread, and the 44-row
geomean is 1.0033x. Stage selection on H100 (sm_90a), B300 and GB300
(sm_103a) is unchanged.

Measured with the same harness as #7772. Speedup = FlashInfer main /
this PR, from CUPTI kernel time with a cold L2 and CUDA-graph replay.
For each side, the value is the mean over 8 sessions of the 10 %-trimmed
mean. Both packages are built by FlashInfer's JIT with CUDA 13.4, called
through the public API and timed interleaved on the same GPU in one
process. "This PR" is the mean of the PR package and a second, identical
build of it. A `*` after a shape name marks the row whose stage changes.
Row names: `64x8`/`8x1` are query/KV heads (head_dim 128). `q1`/`q2`
mean Q is quantized with a dynamic per-token/per-head scale (`q1`) or a
static scale (`q2`). `n0`/`n1`/`n2` mean no RMSNorm, RoPE then RMSNorm,
or RMSNorm then RoPE. `P_decode` is 32 requests x 1 new token and
`P_prefill` is 8 requests x 16 new tokens, with 2048 cached tokens and
page size 64 unless the name says otherwise.
`E_prefill_*_q127/q128/q129` is 4 requests x 127/128/129 new tokens,
which is the 128-row scale-padding boundary. In `X_*` rows,
`B1`/`B128`/`B256` = 1/128/256 requests, `Q1024` = 1024 new tokens,
`page16`/`page128` = page size 16/128, `ctx32768` = 32768 cached tokens,
`outkv` = caller-owned `out_k`/`out_v`, `ragged` = 8 requests with
ragged new-token counts, and `maxseq1024` = 8 requests x 16 new tokens
with max_seqlen 1024.

**NVIDIA B200, sm_100a (148 SMs), CUDA 13.4. Speedup = FlashInfer main /
this PR.**

| shape | FlashInfer main (µs) | this PR (µs) | speedup (main / this PR)
|
|---|---:|---:|---:|
| `E_prefill_64x8_q127` | 9.989 | 10.002 | 0.9987 |
| `E_prefill_64x8_q128` | 10.067 | 10.103 | 0.9964 |
| `E_prefill_64x8_q129` | 10.096 | 10.089 | 1.0007 |
| `E_prefill_8x1_q127` | 3.726 | 3.736 | 0.9975 |
| `E_prefill_8x1_q128` | 3.741 | 3.714 | 1.0071 |
| `E_prefill_8x1_q129` | 3.744 | 3.749 | 0.9988 |
| `P_decode_64x8_q1_n0` | 3.678 | 3.696 | 0.9952 |
| `P_decode_64x8_q1_n1` | 3.789 | 3.775 | 1.0036 |
| `P_decode_64x8_q1_n2` | 3.743 | 3.754 | 0.9972 |
| `P_decode_64x8_q2_n0` | 3.638 | 3.626 | 1.0034 |
| `P_decode_64x8_q2_n1` | 3.679 | 3.698 | 0.9948 |
| `P_decode_64x8_q2_n2` | 3.679 | 3.661 | 1.0051 |
| `P_decode_8x1_q1_n0` | 3.105 | 3.077 | 1.0091 |
| `P_decode_8x1_q1_n1` | 3.227 | 3.210 | 1.0052 |
| `P_decode_8x1_q1_n2` | 3.178 | 3.204 | 0.9920 |
| `P_decode_8x1_q2_n0` | 3.064 | 3.034 | 1.0099 |
| `P_decode_8x1_q2_n1` | 3.129 | 3.147 | 0.9943 |
| `P_decode_8x1_q2_n2` | 3.143 | 3.121 | 1.0072 |
| `P_prefill_64x8_q1_n0` | 4.095 | 4.103 | 0.9983 |
| `P_prefill_64x8_q1_n1` | 4.326 | 4.322 | 1.0010 |
| `P_prefill_64x8_q1_n2` | 4.310 | 4.320 | 0.9978 |
| `P_prefill_64x8_q2_n0` | 4.028 | 4.032 | 0.9990 |
| `P_prefill_64x8_q2_n1` | 4.286 | 4.289 | 0.9993 |
| `P_prefill_64x8_q2_n2` | 4.285 | 4.286 | 0.9999 |
| `P_prefill_8x1_q1_n0` | 3.227 | 3.235 | 0.9977 |
| `P_prefill_8x1_q1_n1` | 3.369 | 3.349 | 1.0058 |
| `P_prefill_8x1_q1_n2` | 3.338 | 3.342 | 0.9989 |
| `P_prefill_8x1_q2_n0` | 3.179 | 3.165 | 1.0046 |
| `P_prefill_8x1_q2_n1` | 3.294 | 3.284 | 1.0031 |
| `P_prefill_8x1_q2_n2` | 3.275 | 3.267 | 1.0026 |
| `X_decode_64x8_B128_q1_n2` | 7.134 | 7.156 | 0.9969 |
| `X_decode_64x8_B1_q1_n2` | 3.027 | 3.043 | 0.9949 |
| `X_decode_64x8_B256_q1_n2` | 12.042 | 12.055 | 0.9989 |
| `X_decode_8x1_B128_q1_n2` | 3.540 | 3.512 | 1.0078 |
| `X_decode_8x1_B1_q1_n2` | 2.950 | 2.992 | 0.9859 |
| `X_decode_8x1_B256_q1_n2` | 4.112 | 4.098 | 1.0035 |
| `X_decode_8x1_q1_n2_ctx32768` | 3.271 | 3.267 | 1.0010 |
| `X_decode_8x1_q1_n2_outkv` | 3.068 | 3.072 | 0.9988 |
| `X_decode_8x1_q1_n2_page128` | 3.287 | 3.251 | 1.0111 |
| `X_decode_8x1_q1_n2_page16` | 3.218 | 3.261 | 0.9871 |
| `X_prefill_64x8_B1_Q1024_q1_n2` * | 17.168 | 15.285 | 1.1232 |
| `X_prefill_8x1_B1_Q1024_q1_n2` | 4.529 | 4.497 | 1.0072 |
| `X_prefill_8x1_q1_n2_maxseq1024` | 3.362 | 3.338 | 1.0069 |
| `X_prefill_8x1_ragged_q1_n2` | 3.432 | 3.417 | 1.0044 |

The BF16 variant `cake_fused_qk_rope_append` is unchanged, and the FP8
package ships programs for sm_90a, sm_100a and sm_103a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for B200 GPUs for qualifying long-prefill attention
workloads, including selection of persistent or nonpersistent processing
stages based on workload characteristics. This extends the available GPU
coverage for the fused FP8 attention operation.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [fd9893c](https://github.com/flashinfer-ai/flashinfer/commit/fd9893c43e3723a4e37f7e3c859e97604c6f2aeb)

- **作者**: eigen
- **时间**: 2026-10-29T17:27:36Z
- **提交信息**: feat(cake_vsa_sm90): planner-routed second BF16 grouped-query queue program for long pair-mode queue plans (#7832)

FlashInfer's Cake backend for variable block-sparse attention on Hopper
(`VariableBlockSparseAttentionWrapper(backend="cake")`, sm_90a) supports
two data types, BF16 and Sage-FP8 (E4M3 inputs with per-head scales,
BF16 output), and each data type has multi-head (MHA) programs and
grouped-query programs (num_qo_heads = g × num_kv_heads, g ∈ {2, 4, 8}).
The grouped-query programs were added in #7167 and retuned in place in
#7185, #7412, #7580, #7634 and #7682; #7743 added the position-selected
Sage-FP8 grouped-query static program `attention_fp8_gqa_pin`, and #7775
lowered its threshold `PIN_MIN_CTA_LOOP_ITERS` from 14 to 8. This PR, on
top of #7775, adds one BF16 grouped-query program,
`attention_gqa_queue_vf`, and a planner rule that routes to it. The new
program is the queue program with the per-position V^T wait moved from
the joint K / V^T gate before the next QK to just before the PV issue;
it waits on the same slot and generation, only later in the same
iteration, so the output bits are the queue program's. The package goes
from 81 to 82 generated kernel units, and no existing unit's source or
machine code changes. Routing (`cake_planner.py`): a pair-mode BF16
grouped-query queue plan of tiles of at least `QUEUE_VF_MIN_TILE_POS` (=
24) ring positions whose lightest CTA runs at least
`QUEUE_VF_MIN_CTA_LOOP_ITERS` (= 440) main-loop iterations carries
`queue_vf` and takes the new program (predicate `bf16_gqa_queue_vf`).
Measured on the generated machine code of this package, the new
program's main loop is 604 instructions against the queue program's 605,
the whole program is 3432 instructions for both, and the new program
uses 168 registers with no spills. The affected rows of the shape list
are the 15 BF16 rows of the 15 shapes listed in the table (15 entries of
the 284-row list; each shape appears once per data type), and every
other row keeps its program byte for byte. The baseline is the previous
Cake version of this backend, the package of #7775, measured on the same
node with the same run form, on an NVIDIA H100 80GB HBM3 (Hopper,
sm_90a) with the CUDA 13.4 toolkit (JIT-compiled; PyTorch CUDA build
13.0) and driver 535.216.03. The run form is two processes, a and b,
each with 9 groups × 256 samples per row, CUPTI kernel-sum timing, cold
L2 (L2 flushed before each sample) and both interleaving orders
(previous→this→this→previous and the reverse). Each version is measured
in its own run, interleaved in both orders against the same reference
kernels, and speedup = previous / this. Over the affected rows the
geometric-mean speedup is 1.0063 in process a and 1.0067 in process b,
with per-row ranges of 1.0002–1.0097 (a) and 0.9984–1.0118 (b). In
process a all 15 affected rows are faster (15 of 15); in process b 13 of
15 are faster. The two rows below 1.0 in process b are
`h8-m109632-n109632-k64-ragged1-scale0-g4`, 1693.905 → 1696.578 µs
(0.9984; process a 1.0017), and
`h8-m32768-n32768-k64-ragged0-scale0-g8`, 883.215 → 883.743 µs (0.9994;
process a 1.0062), both of which lie inside the control band of the e4m3
rows described below. In process a the largest gain is
`h12-m109632-n109632-k64-ragged0-scale0-g4`, 5017.796 → 4969.445 µs
(1.0097; `h12-m75648-n75648-k64-ragged0-scale0-g4` ties it at four
decimals), and the smallest is
`h8-m109632-n109632-k64-ragged0-scale0-g4`, 3355.393 → 3354.786 µs
(1.0002). The e4m3 rows of the same shapes run unchanged code and
measured as controls at 0.9961–1.0014 (a) and 0.9953–1.0075 (b), i.e.
within noise. Both packages pass every one of the 284 rows against the
two reference baselines.

BF16 grouped-query variable block-sparse attention forward, NVIDIA H100
80GB HBM3 (Hopper, sm_90a), CUDA 13.4 toolkit (JIT-compiled; PyTorch
CUDA build 13.0), driver 535.216.03: the previous Cake version of this
backend (the package of #7775) vs this version, each measured in its own
run of the same two-process form (process a shown; 9 groups × 256
samples per row, CUPTI kernel-sum timing, cold L2, both interleaving
orders against the same reference kernels) on the same node; speedup =
previous / this.

| shape | dtype | previous µs | this µs | speedup |
|---|---|---|---|---|
| h12-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 5017.796 | 4969.445
| 1.0097 |
| h12-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 2624.749 | 2601.230
| 1.0090 |
| h12-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 1359.911 | 1349.175 |
1.0080 |
| h12-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 3432.910 | 3400.030 |
1.0097 |
| h12-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1715.060 | 1702.564 |
1.0073 |
| h8-m109632-n109632-k64-ragged0-scale0-g4 | bf16 | 3355.393 | 3354.786
| 1.0002 |
| h8-m109632-n109632-k64-ragged0-scale0-g8 | bf16 | 3305.740 | 3274.284
| 1.0096 |
| h8-m109632-n109632-k64-ragged1-scale0-g4 | bf16 | 1733.945 | 1731.018
| 1.0017 |
| h8-m109632-n109632-k64-ragged1-scale0-g8 | bf16 | 1627.877 | 1620.294
| 1.0047 |
| h8-m32768-n32768-k64-ragged0-scale0-g4 | bf16 | 922.781 | 915.116 |
1.0084 |
| h8-m32768-n32768-k64-ragged0-scale0-g8 | bf16 | 892.379 | 886.923 |
1.0062 |
| h8-m75648-n75648-k64-ragged0-scale0-g4 | bf16 | 2275.575 | 2269.272 |
1.0028 |
| h8-m75648-n75648-k64-ragged0-scale0-g8 | bf16 | 2198.930 | 2188.611 |
1.0047 |
| h8-m75648-n75648-k64-ragged1-scale0-g4 | bf16 | 1156.556 | 1148.940 |
1.0066 |
| h8-m75648-n75648-k64-ragged1-scale0-g8 | bf16 | 1108.586 | 1101.946 |
1.0060 |

The other Cake variants (the BF16 and Sage-FP8 multi-head programs and
the other grouped-query programs, including the Sage-FP8
position-selected program) are unchanged by this PR, and the family
ships only on sm_90a (Hopper); other architectures have their own Cake
block-sparse attention backends.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optimized processing option for eligible BF16 grouped-query
attention workloads. It is selected automatically for qualifying queued
workloads; other workload types continue using their existing processing
paths.
* Expanded support for BF16 grouped-query attention queue
configurations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ce6dc7d](https://github.com/flashinfer-ai/flashinfer/commit/ce6dc7d604a5edb42625a15b46909ac6789c59c6)

- **作者**: eigen
- **时间**: 2026-10-29T17:27:26Z
- **提交信息**: perf(cake_mm_fp4): row-strided bf16 x of the per-token quantizer keeps the cluster-split plan (#7836)

`cake_mm_fp4` (`flashinfer.experimental.cake_nvfp4_per_token`,
experimental) quantizes activations to NVFP4 per token. Then it runs an
NVFP4 x NVFP4 GEMM. The family has two kernels and one fused form:

- **Activation quantizer:** bf16 activations; bf16 with the GEMM output
scale folded into the per-token scale (`out_scale`); fp16 activations (K
= 7168).
- **GEMM** (block-16 scales, per-token alpha epilogue): bf16 output and
fp16 output.
- **Fused form:** the quantize -> GEMM chain (programmatic dependent
launch).

This PR changes only the standalone quantizer, for bf16 activations with
and without folded `out_scale`, when x is a row-strided view (unit
stride along the row). Before this PR, these views ran one CTA per
padded row. They now run the same plan as a contiguous x of the same
shape: a cluster of 2, 4 or 8 CTAs per row, a pad-chunked tail or a late
`out_scale` read. Outputs are bit-identical to those from a contiguous
copy.

Speedup over the previous Cake version (FlashInfer main after #7797):
1.019x to 1.338x on B200 (24 shapes) and 1.028x to 1.320x on GB300 (27
shapes).

**B200 (sm_100a, 148 SMs), CUDA 13.4: standalone quantizer, bf16 x as
the [M, K] view of an [M, K + 64] tensor. Latency is kernel-active time
(CUPTI) with a cold L2, taken as the median of each of 8 interleaved
groups and averaged over two sessions on two GPUs. Speedup is the median
per-group ratio (previous / this PR), averaged over the two sessions.**

|K|M|out_scale|previous Cake µs|this PR µs|speedup|
|--:|--:|---|--:|--:|--:|
|16384|8|none|2.98|2.59|1.149|
|16384|8|folded|2.97|2.57|1.155|
|16384|17|none|3.11|2.67|1.168|
|16384|17|folded|3.09|2.65|1.170|
|16384|32|none|3.21|2.83|1.133|
|16384|32|folded|3.21|2.81|1.143|
|16384|130|none|4.05|3.98|1.020|
|16384|130|folded|4.04|3.96|1.019|
|18432|8|none|3.10|2.54|1.219|
|18432|8|folded|3.12|2.54|1.227|
|18432|17|none|3.24|2.75|1.176|
|18432|17|folded|3.27|2.76|1.181|
|18432|32|none|3.32|2.92|1.138|
|18432|32|folded|3.34|2.93|1.139|
|18432|130|none|4.37|4.17|1.047|
|18432|130|folded|4.35|4.16|1.043|
|28672|8|none|3.52|2.64|1.338|
|28672|8|folded|3.50|2.65|1.328|
|28672|17|none|3.68|2.91|1.264|
|28672|17|folded|3.67|2.92|1.253|
|28672|32|none|3.81|3.13|1.216|
|28672|32|folded|3.80|3.14|1.207|
|28672|130|none|5.34|4.99|1.069|
|28672|130|folded|5.30|5.01|1.059|

**GB300 (sm_103a, 152 SMs), CUDA 13.4: standalone quantizer, bf16 x as
the [M, K] view of an [M, K + 64] tensor. Measured the same way as on
B200. The shape K 8192, M 32, out_scale none keeps its previous route
and is not listed.**

|K|M|out_scale|previous Cake µs|this PR µs|speedup|
|--:|--:|---|--:|--:|--:|
|8192|17|none|2.57|2.47|1.044|
|8192|17|folded|2.58|2.47|1.040|
|16384|8|none|2.92|2.55|1.142|
|16384|8|folded|2.92|2.55|1.144|
|16384|17|none|3.01|2.62|1.153|
|16384|17|folded|3.03|2.61|1.157|
|16384|32|none|3.09|2.69|1.148|
|16384|32|folded|3.09|2.70|1.144|
|16384|130|none|3.94|3.78|1.042|
|16384|130|folded|3.94|3.77|1.046|
|18432|8|none|3.00|2.49|1.198|
|18432|8|folded|3.05|2.49|1.226|
|18432|17|none|3.12|2.70|1.153|
|18432|17|folded|3.17|2.71|1.172|
|18432|32|none|3.18|2.83|1.124|
|18432|32|folded|3.23|2.84|1.134|
|18432|130|none|4.11|3.99|1.032|
|18432|130|folded|4.11|4.00|1.028|
|28672|8|none|3.40|2.58|1.319|
|28672|8|folded|3.40|2.57|1.320|
|28672|17|none|3.56|2.85|1.245|
|28672|17|folded|3.56|2.86|1.244|
|28672|32|none|3.64|3.04|1.195|
|28672|32|folded|3.63|3.04|1.196|
|28672|130|none|5.12|4.86|1.052|
|28672|130|folded|5.11|4.86|1.053|
|28672|512|folded|9.68|9.27|1.044|

The other Cake variants (contiguous x, single rows, the fp16 quantizer,
both GEMM outputs and the fused quantize -> GEMM chain) keep their
plans, and the family ships on sm_100a (B200) and sm_103a (GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Per-token NVFP4 quantization now accepts row-strided inputs, including
in quantizer-only and quantize-plus-GEMM workflows.
  * Added optimized handling for selected row-strided input shapes.
* **Bug Fixes**
* Improved processing plans for row-strided inputs while preserving
existing behavior for contiguous inputs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e19044e](https://github.com/flashinfer-ai/flashinfer/commit/e19044efd8556e82308f0029361aa4fed06ee21f)

- **作者**: eigen
- **时间**: 2026-10-29T17:27:19Z
- **提交信息**: perf(cake_kimi_k3_latent_moe): faster Kimi-K3 LatentMoE decode tails and front (#7843)

This PR updates the Cake programs for the Kimi-K3 Stable LatentMoE front
and tail projections of one rank in
`flashinfer.experimental.kimi_k3_latent_moe` (BF16, `sm_100a` and
`sm_103a`). The package has four variants: the front and the tail
projection, each for TP1 and TP8. For T <= 128 tokens each variant runs
a decode instance, and the tail fuses the RMSNorm and the reduction of P
routed partials into it. For T > 128 each variant runs a prefill GEMM.
The baseline is the Cake programs currently on FlashInfer main, which
shipped in #7673 and #7742 ("previous"), and speedup = previous / this
PR. This PR changes the decode paths of all four variants. On GB200 and
GB300 it also changes the TP1 tail prefill GEMM at N 192. On every
changed row the outputs stay bitwise those of the previous program. A
host route table sends decode tails from 9 to 128 tokens to the
split-finalize instance of one routed partial at N_PAD 32, 64 or 128.
That instance serves every token count up to its N_PAD and every partial
count, and it sums the partials in the order of the row's own instance.
The route table covers selected TP1 shapes from 9 to 32 tokens,
including the rows of one partial at 9-16 and 24-32 tokens. It also
covers every TP1 and every TP8 shape with several partials from 33 to
128 tokens. The TP1 rows with 2 partials at 9 and 16 tokens keep main's
route. The routed rows gain 1.011-1.028x for TP1 with one partial,
1.016-1.096x for TP1 with several partials and 1.049-1.090x for TP8. The
changed front programs are the TP1 decode front programs of one CTA per
tile at N_PAD 64 and 128 and the TP8 split-finalize front program at
N_PAD 64. For a full tile (as many tokens as N_PAD), they now store the
finalize outputs as straight-line code instead of one guarded store per
element. A partial tile runs the guarded stores as before, and the TP8
program at N_PAD 128 keeps its code. The TP1 front rows at 64 and 128
tokens gain 1.011-1.027x, and the TP8 front row at 64 tokens gains
1.017-1.021x. The TP1 fused-norm tail GEMM at N 192 serves the TP1 tail
rows of 129 to 512 tokens on GB200 and GB300 (152 SMs). It now finishes
a split tile in its last K segment and sums every contributor in the
fixed segment order. On a launch without split K, only the warp that
owns a norm row reads its routed partials. Its rows at 129 and 256
tokens gain 1.056-1.074x. Its rows at 300, 384 and 512 tokens show no
change within measurement noise (0.999-1.004x); they count as changed
only because they run the changed N 192 program. On B200 and B300 these
rows run other GEMM programs, which this PR does not change. The PR
changes 18 rows on B200, 18 on B300, 23 on GB200 and 23 on GB300. Except
for the GB200 and GB300 rows at 300 to 512 tokens, the changed rows gain
1.011-1.096x. All other rows run the same machine code as on main, so
both of their columns show one measurement, taken from the table of
#7742.

| Projection | TP | Tokens | B200 previous (µs) | B200 this PR (µs) |
B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300 speedup |
GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup | GB300
previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| front | 1 | 1 | 42.88 | 42.88 | 1.000x | 42.90 | 42.90 | 1.000x |
41.50 | 41.50 | 1.000x | 41.49 | 41.49 | 1.000x |
| front | 1 | 2 | 42.13 | 42.13 | 1.000x | 43.02 | 43.02 | 1.000x |
41.50 | 41.50 | 1.000x | 41.60 | 41.60 | 1.000x |
| front | 1 | 4 | 42.05 | 42.05 | 1.000x | 42.93 | 42.93 | 1.000x |
41.41 | 41.41 | 1.000x | 41.70 | 41.70 | 1.000x |
| front | 1 | 5 | 42.05 | 42.05 | 1.000x | 43.12 | 43.12 | 1.000x |
41.39 | 41.39 | 1.000x | 41.71 | 41.71 | 1.000x |
| front | 1 | 8 | 41.86 | 41.86 | 1.000x | 42.85 | 42.85 | 1.000x |
41.31 | 41.31 | 1.000x | 41.79 | 41.79 | 1.000x |
| front | 1 | 9 | 42.06 | 42.06 | 1.000x | 42.91 | 42.91 | 1.000x |
41.49 | 41.49 | 1.000x | 41.97 | 41.97 | 1.000x |
| front | 1 | 16 | 42.34 | 42.34 | 1.000x | 43.34 | 43.34 | 1.000x |
41.94 | 41.94 | 1.000x | 42.53 | 42.53 | 1.000x |
| front | 1 | 32 | 42.66 | 42.66 | 1.000x | 43.49 | 43.49 | 1.000x |
41.92 | 41.92 | 1.000x | 42.42 | 42.42 | 1.000x |
| front | 1 | 64 | 44.75 | 44.26 | 1.011x | 45.04 | 44.43 | 1.014x |
43.73 | 43.25 | 1.011x | 44.19 | 43.58 | 1.014x |
| front | 1 | 128 | 50.19 | 49.09 | 1.022x | 50.13 | 48.90 | 1.025x |
49.76 | 48.46 | 1.027x | 49.22 | 48.03 | 1.025x |
| front | 1 | 200 | 50.78 | 50.78 | 1.000x | 52.29 | 52.29 | 1.000x |
51.15 | 51.15 | 1.000x | 48.53 | 48.53 | 1.000x |
| front | 1 | 256 | 51.04 | 51.04 | 1.000x | 52.48 | 52.48 | 1.000x |
52.03 | 52.03 | 1.000x | 48.83 | 48.83 | 1.000x |
| front | 1 | 512 | 85.44 | 85.44 | 1.000x | 79.71 | 79.71 | 1.000x |
92.45 | 92.45 | 1.000x | 68.21 | 68.21 | 1.000x |
| front | 1 | 768 | 126.77 | 126.77 | 1.000x | 128.29 | 128.29 | 1.000x
| 141.66 | 141.66 | 1.000x | 108.75 | 108.75 | 1.000x |
| front | 1 | 1024 | 167.33 | 167.33 | 1.000x | 165.51 | 165.51 | 1.000x
| 170.29 | 170.29 | 1.000x | 131.97 | 131.97 | 1.000x |
| front | 1 | 2048 | 324.30 | 324.30 | 1.000x | 314.63 | 314.63 | 1.000x
| 312.98 | 312.98 | 1.000x | 250.75 | 250.75 | 1.000x |
| front | 1 | 4096 | 614.83 | 614.83 | 1.000x | 547.78 | 547.78 | 1.000x
| 640.60 | 640.60 | 1.000x | 528.51 | 528.51 | 1.000x |
| front | 1 | 8192 | 1220.26 | 1220.26 | 1.000x | 1080.59 | 1080.59 |
1.000x | 1317.63 | 1317.63 | 1.000x | 1092.76 | 1092.76 | 1.000x |
| front | 1 | 16384 | 2404.14 | 2404.14 | 1.000x | 2213.30 | 2213.30 |
1.000x | 2668.08 | 2668.08 | 1.000x | 2193.13 | 2193.13 | 1.000x |
| front | 8 | 1 | 18.99 | 18.99 | 1.000x | 18.88 | 18.88 | 1.000x |
18.32 | 18.32 | 1.000x | 18.40 | 18.40 | 1.000x |
| front | 8 | 2 | 18.93 | 18.93 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 4 | 18.94 | 18.94 | 1.000x | 19.02 | 19.02 | 1.000x |
18.32 | 18.32 | 1.000x | 18.46 | 18.46 | 1.000x |
| front | 8 | 5 | 19.12 | 19.12 | 1.000x | 18.93 | 18.93 | 1.000x |
18.38 | 18.38 | 1.000x | 18.38 | 18.38 | 1.000x |
| front | 8 | 8 | 19.10 | 19.10 | 1.000x | 18.99 | 18.99 | 1.000x |
18.37 | 18.37 | 1.000x | 18.37 | 18.37 | 1.000x |
| front | 8 | 9 | 19.18 | 19.18 | 1.000x | 19.10 | 19.10 | 1.000x |
18.46 | 18.46 | 1.000x | 18.43 | 18.43 | 1.000x |
| front | 8 | 16 | 19.14 | 19.14 | 1.000x | 19.20 | 19.20 | 1.000x |
18.54 | 18.54 | 1.000x | 18.51 | 18.51 | 1.000x |
| front | 8 | 32 | 19.65 | 19.65 | 1.000x | 19.70 | 19.70 | 1.000x |
18.88 | 18.88 | 1.000x | 18.94 | 18.94 | 1.000x |
| front | 8 | 64 | 20.86 | 20.51 | 1.017x | 20.80 | 20.38 | 1.020x |
20.10 | 19.73 | 1.019x | 20.24 | 19.82 | 1.021x |
| front | 8 | 128 | 25.74 | 25.74 | 1.000x | 25.68 | 25.68 | 1.000x |
25.30 | 25.30 | 1.000x | 24.62 | 24.62 | 1.000x |
| front | 8 | 200 | 29.92 | 29.92 | 1.000x | 29.12 | 29.12 | 1.000x |
29.47 | 29.47 | 1.000x | 28.03 | 28.03 | 1.000x |
| front | 8 | 256 | 29.95 | 29.95 | 1.000x | 29.38 | 29.38 | 1.000x |
29.82 | 29.82 | 1.000x | 27.97 | 27.97 | 1.000x |
| front | 8 | 512 | 45.14 | 45.14 | 1.000x | 42.37 | 42.37 | 1.000x |
45.07 | 45.07 | 1.000x | 40.13 | 40.13 | 1.000x |
| front | 8 | 640 | 46.96 | 46.96 | 1.000x | 44.06 | 44.06 | 1.000x |
46.80 | 46.80 | 1.000x | 41.84 | 41.84 | 1.000x |
| front | 8 | 768 | 47.28 | 47.28 | 1.000x | 46.26 | 46.26 | 1.000x |
47.71 | 47.71 | 1.000x | 42.27 | 42.27 | 1.000x |
| front | 8 | 769 | — | — | — | — | — | — | 74.35 | 74.35 | 1.000x |
58.66 | 58.66 | 1.000x |
| front | 8 | 800 | — | — | — | — | — | — | 74.94 | 74.94 | 1.000x |
58.83 | 58.83 | 1.000x |
| front | 8 | 897 | — | — | — | — | — | — | 71.38 | 71.38 | 1.000x |
57.98 | 57.98 | 1.000x |
| front | 8 | 960 | — | — | — | — | — | — | 71.76 | 71.76 | 1.000x |
58.08 | 58.08 | 1.000x |
| front | 8 | 1000 | — | — | — | — | — | — | 74.50 | 74.50 | 1.000x |
58.85 | 58.85 | 1.000x |
| front | 8 | 1024 | 67.18 | 67.18 | 1.000x | 65.47 | 65.47 | 1.000x |
74.88 | 74.88 | 1.000x | 58.34 | 58.34 | 1.000x |
| front | 8 | 1793 | 114.55 | 114.55 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 1800 | 114.91 | 114.91 | 1.000x | 110.59 | 110.59 | 1.000x
| 123.63 | 123.63 | 1.000x | 95.81 | 95.81 | 1.000x |
| front | 8 | 1900 | 116.06 | 116.06 | 1.000x | — | — | — | — | — | — |
— | — | — |
| front | 8 | 2000 | 114.52 | 114.52 | 1.000x | 112.45 | 112.45 | 1.000x
| 127.89 | 127.89 | 1.000x | 98.13 | 98.13 | 1.000x |
| front | 8 | 2048 | 119.73 | 119.73 | 1.000x | 114.37 | 114.37 | 1.000x
| 129.41 | 129.41 | 1.000x | 98.50 | 98.50 | 1.000x |
| front | 8 | 4096 | 235.01 | 235.01 | 1.000x | 230.29 | 230.29 | 1.000x
| 240.68 | 240.68 | 1.000x | 190.99 | 190.99 | 1.000x |
| front | 8 | 8192 | 492.32 | 492.32 | 1.000x | 480.21 | 480.21 | 1.000x
| 471.60 | 471.60 | 1.000x | 383.97 | 383.97 | 1.000x |
| front | 8 | 16384 | 909.49 | 909.49 | 1.000x | 800.25 | 800.25 |
1.000x | 959.91 | 959.91 | 1.000x | 804.95 | 804.95 | 1.000x |
| tail | 1 | 1 | 26.42 | 26.42 | 1.000x | 26.64 | 26.64 | 1.000x | 25.71
| 25.71 | 1.000x | 25.76 | 25.76 | 1.000x |
| tail | 1 | 2 | 26.42 | 26.42 | 1.000x | 26.72 | 26.72 | 1.000x | 25.70
| 25.70 | 1.000x | 25.86 | 25.86 | 1.000x |
| tail | 1 | 4 | 26.54 | 26.54 | 1.000x | 26.82 | 26.82 | 1.000x | 25.74
| 25.74 | 1.000x | 25.92 | 25.92 | 1.000x |
| tail | 1 | 5 | 26.48 | 26.48 | 1.000x | 26.88 | 26.88 | 1.000x | 25.74
| 25.74 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 8 | 26.50 | 26.50 | 1.000x | 26.78 | 26.78 | 1.000x | 25.78
| 25.78 | 1.000x | 26.03 | 26.03 | 1.000x |
| tail | 1 | 9 | 28.50 | 27.98 | 1.018x | 28.34 | 27.66 | 1.024x | 27.63
| 26.88 | 1.028x | 27.46 | 26.82 | 1.024x |
| tail | 1 | 16 | 28.54 | 28.02 | 1.019x | 28.34 | 27.76 | 1.021x |
27.54 | 26.88 | 1.024x | 27.58 | 27.01 | 1.021x |
| tail | 1 | 32 | 28.21 | 27.63 | 1.021x | 27.95 | 27.59 | 1.013x |
27.22 | 26.78 | 1.016x | 27.10 | 26.80 | 1.011x |
| tail | 1 | 64 | 27.58 | 27.58 | 1.000x | 27.89 | 27.89 | 1.000x |
27.06 | 27.06 | 1.000x | 26.83 | 26.83 | 1.000x |
| tail | 1 | 128 | 29.60 | 29.60 | 1.000x | 30.02 | 30.02 | 1.000x |
28.80 | 28.80 | 1.000x | 28.62 | 28.62 | 1.000x |
| tail | 1 | 129 | 41.36 | 41.36 | 1.000x | 40.80 | 40.80 | 1.000x |
39.55 | 36.98 | 1.070x | 37.86 | 35.84 | 1.056x |
| tail | 1 | 256 | 42.45 | 42.45 | 1.000x | 42.14 | 42.14 | 1.000x |
41.01 | 38.19 | 1.074x | 38.74 | 36.67 | 1.056x |
| tail | 1 | 300 | 54.00 | 54.00 | 1.000x | 52.64 | 52.64 | 1.000x |
48.56 | 48.35 | 1.004x | 41.52 | 41.57 | 0.999x |
| tail | 1 | 384 | 54.62 | 54.62 | 1.000x | 52.67 | 52.67 | 1.000x |
47.78 | 47.63 | 1.003x | 41.41 | 41.42 | 1.000x |
| tail | 1 | 512 | 55.70 | 55.70 | 1.000x | 53.33 | 53.33 | 1.000x |
51.70 | 51.68 | 1.000x | 42.46 | 42.50 | 0.999x |
| tail | 1 | 1024 | 98.61 | 98.61 | 1.000x | 95.79 | 95.79 | 1.000x |
105.65 | 105.65 | 1.000x | 83.09 | 83.09 | 1.000x |
| tail | 1 | 2048 | 192.64 | 192.64 | 1.000x | 188.91 | 188.91 | 1.000x
| 189.74 | 189.74 | 1.000x | 147.74 | 147.74 | 1.000x |
| tail | 1 | 4096 | 387.46 | 387.46 | 1.000x | 385.22 | 385.22 | 1.000x
| 368.18 | 368.18 | 1.000x | 293.95 | 293.95 | 1.000x |
| tail | 1 | 8192 | 718.12 | 718.12 | 1.000x | 651.83 | 651.83 | 1.000x
| 743.41 | 743.41 | 1.000x | 625.10 | 625.10 | 1.000x |
| tail | 1 | 16384 | 1446.74 | 1446.74 | 1.000x | 1291.42 | 1291.42 |
1.000x | 1521.33 | 1521.33 | 1.000x | 1284.41 | 1284.41 | 1.000x |
| tail | 8 | 1 | 7.87 | 7.87 | 1.000x | 7.86 | 7.86 | 1.000x | 7.74 |
7.74 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 2 | 7.90 | 7.90 | 1.000x | 7.84 | 7.84 | 1.000x | 7.65 |
7.65 | 1.000x | 7.58 | 7.58 | 1.000x |
| tail | 8 | 4 | 7.92 | 7.92 | 1.000x | 7.86 | 7.86 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 5 | 7.95 | 7.95 | 1.000x | 7.79 | 7.79 | 1.000x | 7.70 |
7.70 | 1.000x | 7.65 | 7.65 | 1.000x |
| tail | 8 | 8 | 8.00 | 8.00 | 1.000x | 7.97 | 7.97 | 1.000x | 7.76 |
7.76 | 1.000x | 7.68 | 7.68 | 1.000x |
| tail | 8 | 9 | 8.70 | 8.70 | 1.000x | 8.59 | 8.59 | 1.000x | 8.45 |
8.45 | 1.000x | 8.40 | 8.40 | 1.000x |
| tail | 8 | 16 | 9.34 | 9.34 | 1.000x | 8.94 | 8.94 | 1.000x | 9.16 |
9.16 | 1.000x | 8.94 | 8.94 | 1.000x |
| tail | 8 | 32 | 10.26 | 10.26 | 1.000x | 10.32 | 10.32 | 1.000x | 9.87
| 9.87 | 1.000x | 9.95 | 9.95 | 1.000x |
| tail | 8 | 64 | 10.85 | 10.85 | 1.000x | 10.67 | 10.67 | 1.000x |
10.45 | 10.45 | 1.000x | 10.45 | 10.45 | 1.000x |
| tail | 8 | 128 | 12.58 | 12.58 | 1.000x | 12.24 | 12.24 | 1.000x |
12.19 | 12.19 | 1.000x | 12.05 | 12.05 | 1.000x |
| tail | 8 | 256 | 14.94 | 14.94 | 1.000x | 14.05 | 14.05 | 1.000x |
14.51 | 14.51 | 1.000x | 14.03 | 14.03 | 1.000x |
| tail | 8 | 300 | 18.88 | 18.88 | 1.000x | 17.62 | 17.62 | 1.000x |
18.78 | 18.78 | 1.000x | 17.90 | 17.90 | 1.000x |
| tail | 8 | 512 | 18.69 | 18.69 | 1.000x | 17.66 | 17.66 | 1.000x |
18.66 | 18.66 | 1.000x | 17.68 | 17.68 | 1.000x |
| tail | 8 | 1024 | 26.00 | 26.00 | 1.000x | 23.97 | 23.97 | 1.000x |
23.81 | 23.81 | 1.000x | 22.67 | 22.67 | 1.000x |
| tail | 8 | 2048 | 39.12 | 39.12 | 1.000x | 36.48 | 36.48 | 1.000x |
32.83 | 32.83 | 1.000x | 30.80 | 30.80 | 1.000x |
| tail | 8 | 4096 | 62.72 | 62.72 | 1.000x | 58.86 | 58.86 | 1.000x |
57.54 | 57.54 | 1.000x | 51.84 | 51.84 | 1.000x |
| tail | 8 | 8192 | 111.60 | 111.60 | 1.000x | 102.42 | 102.42 | 1.000x
| 112.70 | 112.70 | 1.000x | 93.39 | 93.39 | 1.000x |
| tail | 8 | 16384 | 219.62 | 219.62 | 1.000x | 213.55 | 213.55 | 1.000x
| 222.29 | 222.29 | 1.000x | 182.40 | 182.40 | 1.000x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over two
passes, the second in reversed order; each value is the mean of the two
per-pass medians on one GPU; rows this PR does not change show the value
of #7742 in both columns; speedup = previous / this PR; tail rows reduce
one routed partial; B200 and GB200 NVL72 (`sm_100a`), B300 and GB300
NVL72 (`sm_103a`); B200 and B300 have 148 SMs, GB200 and GB300 152; CUDA
13.4; "—" = the row is not on that part's shape list.*

| Projection | TP | Tokens | Partials | B200 previous (µs) | B200 this
PR (µs) | B200 speedup | B300 previous (µs) | B300 this PR (µs) | B300
speedup | GB200 previous (µs) | GB200 this PR (µs) | GB200 speedup |
GB300 previous (µs) | GB300 this PR (µs) | GB300 speedup |
|:--|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|--:|
| tail | 1 | 1 | 2 | 26.45 | 26.45 | 1.000x | 26.67 | 26.67 | 1.000x |
25.68 | 25.68 | 1.000x | 25.66 | 25.66 | 1.000x |
| tail | 1 | 1 | 5 | 26.70 | 26.70 | 1.000x | 26.77 | 26.77 | 1.000x |
25.78 | 25.78 | 1.000x | 25.97 | 25.97 | 1.000x |
| tail | 1 | 1 | 6 | 28.32 | 28.32 | 1.000x | 27.42 | 27.42 | 1.000x |
27.47 | 27.47 | 1.000x | 27.02 | 27.02 | 1.000x |
| tail | 1 | 1 | 7 | 29.36 | 29.36 | 1.000x | 29.31 | 29.31 | 1.000x |
28.18 | 28.18 | 1.000x | 28.27 | 28.27 | 1.000x |
| tail | 1 | 1 | 8 | 29.90 | 29.90 | 1.000x | 29.62 | 29.62 | 1.000x |
28.75 | 28.75 | 1.000x | 28.56 | 28.56 | 1.000x |
| tail | 1 | 1 | 16 | 34.21 | 34.21 | 1.000x | 34.74 | 34.74 | 1.000x |
32.86 | 32.86 | 1.000x | 32.83 | 32.83 | 1.000x |
| tail | 1 | 2 | 5 | 27.01 | 27.01 | 1.000x | 26.88 | 26.88 | 1.000x |
26.51 | 26.51 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 2 | 6 | 28.90 | 28.90 | 1.000x | 28.32 | 28.32 | 1.000x |
27.26 | 27.26 | 1.000x | 26.58 | 26.58 | 1.000x |
| tail | 1 | 2 | 7 | 29.34 | 29.34 | 1.000x | 29.46 | 29.46 | 1.000x |
28.32 | 28.32 | 1.000x | 28.34 | 28.34 | 1.000x |
| tail | 1 | 2 | 8 | 29.71 | 29.71 | 1.000x | 29.62 | 29.62 | 1.000x |
28.54 | 28.54 | 1.000x | 28.58 | 28.58 | 1.000x |
| tail | 1 | 2 | 16 | 34.88 | 34.88 | 1.000x | 34.10 | 34.10 | 1.000x |
33.36 | 33.36 | 1.000x | 33.23 | 33.23 | 1.000x |
| tail | 1 | 3 | 5 | 27.07 | 27.07 | 1.000x | 26.85 | 26.85 | 1.000x |
26.75 | 26.75 | 1.000x | 26.16 | 26.16 | 1.000x |
| tail | 1 | 3 | 6 | 29.39 | 29.39 | 1.000x | 28.62 | 28.62 | 1.000x |
28.34 | 28.34 | 1.000x | 27.71 | 27.71 | 1.000x |
| tail | 1 | 3 | 7 | 29.39 | 29.39 | 1.000x | 29.52 | 29.52 | 1.000x |
28.18 | 28.18 | 1.000x | 28.38 | 28.38 | 1.000x |
| tail | 1 | 3 | 8 | 29.87 | 29.87 | 1.000x | 29.63 | 29.63 | 1.000x |
28.43 | 28.43 | 1.000x | 28.56 | 28.56 | 1.000x |
| tail | 1 | 3 | 16 | 34.66 | 34.66 | 1.000x | 34.35 | 34.35 | 1.000x |
33.39 | 33.39 | 1.000x | 33.34 | 33.34 | 1.000x |
| tail | 1 | 4 | 5 | 26.91 | 26.91 | 1.000x | 26.88 | 26.88 | 1.000x |
26.05 | 26.05 | 1.000x | 25.95 | 25.95 | 1.000x |
| tail | 1 | 4 | 6 | 28.59 | 28.59 | 1.000x | 27.87 | 27.87 | 1.000x |
28.08 | 28.08 | 1.000x | 27.42 | 27.42 | 1.000x |
| tail | 1 | 4 | 7 | 29.70 | 29.70 | 1.000x | 29.41 | 29.41 | 1.000x |
28.34 | 28.34 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 4 | 8 | 29.68 | 29.68 | 1.000x | 29.73 | 29.73 | 1.000x |
28.59 | 28.59 | 1.000x | 28.67 | 28.67 | 1.000x |
| tail | 1 | 4 | 16 | 34.93 | 34.93 | 1.000x | 34.21 | 34.21 | 1.000x |
33.46 | 33.46 | 1.000x | 33.18 | 33.18 | 1.000x |
| tail | 1 | 5 | 2 | 26.56 | 26.56 | 1.000x | 26.86 | 26.86 | 1.000x |
25.76 | 25.76 | 1.000x | 25.78 | 25.78 | 1.000x |
| tail | 1 | 5 | 3 | 26.85 | 26.85 | 1.000x | 26.93 | 26.93 | 1.000x |
26.26 | 26.26 | 1.000x | 26.06 | 26.06 | 1.000x |
| tail | 1 | 5 | 4 | 28.66 | 28.66 | 1.000x | 28.94 | 28.94 | 1.000x |
27.94 | 27.94 | 1.000x | 28.02 | 28.02 | 1.000x |
| tail | 1 | 5 | 5 | 28.96 | 28.96 | 1.000x | 28.90 | 28.90 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 5 | 6 | 29.33 | 29.33 | 1.000x | 29.01 | 29.01 | 1.000x |
28.05 | 28.05 | 1.000x | 28.08 | 28.08 | 1.000x |
| tail | 1 | 5 | 7 | 29.23 | 29.23 | 1.000x | 29.30 | 29.30 | 1.000x |
28.38 | 28.38 | 1.000x | 28.46 | 28.46 | 1.000x |
| tail | 1 | 5 | 8 | 29.76 | 29.76 | 1.000x | 29.66 | 29.66 | 1.000x |
28.51 | 28.51 | 1.000x | 28.75 | 28.75 | 1.000x |
| tail | 1 | 5 | 16 | 34.96 | 34.96 | 1.000x | 34.14 | 34.14 | 1.000x |
33.39 | 33.39 | 1.000x | 33.31 | 33.31 | 1.000x |
| tail | 1 | 6 | 3 | 27.07 | 27.07 | 1.000x | 27.12 | 27.12 | 1.000x |
26.32 | 26.32 | 1.000x | 26.19 | 26.19 | 1.000x |
| tail | 1 | 6 | 4 | 28.74 | 28.74 | 1.000x | 28.98 | 28.98 | 1.000x |
28.02 | 28.02 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 6 | 5 | 28.98 | 28.98 | 1.000x | 28.85 | 28.85 | 1.000x |
27.90 | 27.90 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 6 | 6 | 29.01 | 29.01 | 1.000x | 29.12 | 29.12 | 1.000x |
28.05 | 28.05 | 1.000x | 28.19 | 28.19 | 1.000x |
| tail | 1 | 6 | 7 | 29.46 | 29.46 | 1.000x | 29.25 | 29.25 | 1.000x |
28.38 | 28.38 | 1.000x | 28.45 | 28.45 | 1.000x |
| tail | 1 | 6 | 8 | 29.90 | 29.90 | 1.000x | 29.78 | 29.78 | 1.000x |
28.61 | 28.61 | 1.000x | 28.72 | 28.72 | 1.000x |
| tail | 1 | 6 | 16 | 34.37 | 34.37 | 1.000x | 34.26 | 34.26 | 1.000x |
33.76 | 33.76 | 1.000x | 33.10 | 33.10 | 1.000x |
| tail | 1 | 7 | 3 | 27.06 | 27.06 | 1.000x | 26.91 | 26.91 | 1.000x |
26.69 | 26.69 | 1.000x | 26.37 | 26.37 | 1.000x |
| tail | 1 | 7 | 4 | 28.78 | 28.78 | 1.000x | 28.96 | 28.96 | 1.000x |
27.92 | 27.92 | 1.000x | 27.98 | 27.98 | 1.000x |
| tail | 1 | 7 | 5 | 29.12 | 29.12 | 1.000x | 29.06 | 29.06 | 1.000x |
27.89 | 27.89 | 1.000x | 27.95 | 27.95 | 1.000x |
| tail | 1 | 7 | 6 | 28.96 | 28.96 | 1.000x | 29.06 | 29.06 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 7 | 7 | 29.76 | 29.76 | 1.000x | 29.30 | 29.30 | 1.000x |
28.27 | 28.27 | 1.000x | 28.40 | 28.40 | 1.000x |
| tail | 1 | 7 | 8 | 29.55 | 29.55 | 1.000x | 29.78 | 29.78 | 1.000x |
28.54 | 28.54 | 1.000x | 28.72 | 28.72 | 1.000x |
| tail | 1 | 7 | 16 | 34.64 | 34.64 | 1.000x | 34.18 | 34.18 | 1.000x |
33.65 | 33.65 | 1.000x | 33.54 | 33.54 | 1.000x |
| tail | 1 | 8 | 2 | 26.82 | 26.82 | 1.000x | 27.07 | 27.07 | 1.000x |
25.82 | 25.82 | 1.000x | 25.84 | 25.84 | 1.000x |
| tail | 1 | 8 | 3 | 27.74 | 27.74 | 1.000x | 27.22 | 27.22 | 1.000x |
26.69 | 26.69 | 1.000x | 26.35 | 26.35 | 1.000x |
| tail | 1 | 8 | 4 | 28.69 | 28.69 | 1.000x | 28.91 | 28.91 | 1.000x |
28.00 | 28.00 | 1.000x | 28.03 | 28.03 | 1.000x |
| tail | 1 | 8 | 5 | 28.88 | 28.88 | 1.000x | 28.94 | 28.94 | 1.000x |
28.02 | 28.02 | 1.000x | 27.92 | 27.92 | 1.000x |
| tail | 1 | 8 | 6 | 29.02 | 29.02 | 1.000x | 28.99 | 28.99 | 1.000x |
28.03 | 28.03 | 1.000x | 28.13 | 28.13 | 1.000x |
| tail | 1 | 8 | 7 | 29.74 | 29.74 | 1.000x | 29.39 | 29.39 | 1.000x |
28.40 | 28.40 | 1.000x | 28.43 | 28.43 | 1.000x |
| tail | 1 | 8 | 8 | 29.73 | 29.73 | 1.000x | 29.65 | 29.65 | 1.000x |
28.58 | 28.58 | 1.000x | 28.61 | 28.61 | 1.000x |
| tail | 1 | 8 | 16 | 35.01 | 35.01 | 1.000x | 34.35 | 34.35 | 1.000x |
33.70 | 33.70 | 1.000x | 33.26 | 33.26 | 1.000x |
| tail | 1 | 9 | 2 | 28.38 | 28.38 | 1.000x | 28.40 | 28.40 | 1.000x |
27.49 | 27.49 | 1.000x | 27.25 | 27.25 | 1.000x |
| tail | 1 | 9 | 8 | 31.14 | 30.16 | 1.032x | 30.86 | 29.97 | 1.030x |
30.21 | 29.38 | 1.028x | 30.03 | 29.10 | 1.032x |
| tail | 1 | 16 | 2 | 28.35 | 28.35 | 1.000x | 28.56 | 28.56 | 1.000x |
27.60 | 27.60 | 1.000x | 27.33 | 27.33 | 1.000x |
| tail | 1 | 16 | 8 | 31.26 | 30.21 | 1.035x | 30.98 | 30.08 | 1.030x |
30.37 | 29.63 | 1.025x | 30.48 | 29.66 | 1.028x |
| tail | 1 | 32 | 2 | 29.01 | 28.08 | 1.033x | 28.96 | 28.02 | 1.034x |
28.00 | 27.28 | 1.026x | 28.03 | 27.18 | 1.031x |
| tail | 1 | 32 | 8 | 31.23 | 29.98 | 1.042x | 30.75 | 30.02 | 1.024x |
29.89 | 28.99 | 1.031x | 30.02 | 29.04 | 1.034x |
| tail | 1 | 64 | 2 | 30.08 | 28.42 | 1.059x | 30.32 | 28.50 | 1.064x |
29.23 | 27.61 | 1.059x | 29.07 | 27.52 | 1.056x |
| tail | 1 | 64 | 8 | 31.07 | 30.45 | 1.020x | 31.12 | 30.64 | 1.016x |
30.10 | 29.54 | 1.019x | 30.00 | 29.46 | 1.018x |
| tail | 1 | 128 | 2 | 32.93 | 30.21 | 1.090x | 33.30 | 30.38 | 1.096x |
32.30 | 29.52 | 1.094x | 31.87 | 29.31 | 1.087x |
| tail | 1 | 128 | 8 | 34.21 | 32.94 | 1.038x | 34.29 | 33.17 | 1.034x |
32.99 | 31.89 | 1.035x | 32.88 | 31.78 | 1.035x |
| tail | 8 | 1 | 2 | 10.86 | 10.86 | 1.000x | 10.40 | 10.40 | 1.000x |
10.53 | 10.53 | 1.000x | 10.35 | 10.35 | 1.000x |
| tail | 8 | 1 | 5 | 13.62 | 13.62 | 1.000x | 14.00 | 14.00 | 1.000x |
13.73 | 13.73 | 1.000x | 13.52 | 13.52 | 1.000x |
| tail | 8 | 1 | 6 | 14.70 | 14.70 | 1.000x | 13.89 | 13.89 | 1.000x |
14.29 | 14.29 | 1.000x | 14.00 | 14.00 | 1.000x |
| tail | 8 | 1 | 7 | 15.04 | 15.04 | 1.000x | 14.86 | 14.86 | 1.000x |
14.93 | 14.93 | 1.000x | 14.58 | 14.58 | 1.000x |
| tail | 8 | 1 | 8 | 15.06 | 15.06 | 1.000x | 15.06 | 15.06 | 1.000x |
15.50 | 15.50 | 1.000x | 14.77 | 14.77 | 1.000x |
| tail | 8 | 1 | 16 | 19.42 | 19.42 | 1.000x | 19.47 | 19.47 | 1.000x |
19.42 | 19.42 | 1.000x | 19.20 | 19.20 | 1.000x |
| tail | 8 | 2 | 4 | 13.42 | 13.42 | 1.000x | 13.20 | 13.20 | 1.000x |
12.98 | 12.98 | 1.000x | 12.72 | 12.72 | 1.000x |
| tail | 8 | 2 | 5 | 13.07 | 13.07 | 1.000x | 13.76 | 13.76 | 1.000x |
13.44 | 13.44 | 1.000x | 13.28 | 13.28 | 1.000x |
| tail | 8 | 2 | 6 | 14.50 | 14.50 | 1.000x | 13.94 | 13.94 | 1.000x |
14.24 | 14.24 | 1.000x | 13.50 | 13.50 | 1.000x |
| tail | 8 | 2 | 7 | 14.53 | 14.53 | 1.000x | 14.99 | 14.99 | 1.000x |
14.46 | 14.46 | 1.000x | 14.45 | 14.45 | 1.000x |
| tail | 8 | 2 | 8 | 15.60 | 15.60 | 1.000x | 14.86 | 14.86 | 1.000x |
14.98 | 14.98 | 1.000x | 14.86 | 14.86 | 1.000x |
| tail | 8 | 2 | 16 | 19.79 | 19.79 | 1.000x | 19.39 | 19.39 | 1.000x |
19.15 | 19.15 | 1.000x | 18.83 | 18.83 | 1.000x |
| tail | 8 | 3 | 4 | 12.70 | 12.70 | 1.000x | 12.66 | 12.66 | 1.000x |
12.96 | 12.96 | 1.000x | 12.34 | 12.34 | 1.000x |
| tail | 8 | 3 | 5 | 13.07 | 13.07 | 1.000x | 13.12 | 13.12 | 1.000x |
13.25 | 13.25 | 1.000x | 13.36 | 13.36 | 1.000x |
| tail | 8 | 3 | 6 | 14.34 | 14.34 | 1.000x | 13.98 | 13.98 | 1.000x |
13.82 | 13.82 | 1.000x | 13.74 | 13.74 | 1.000x |
| tail | 8 | 3 | 7 | 14.00 | 14.00 | 1.000x | 14.45 | 14.45 | 1.000x |
14.34 | 14.34 | 1.000x | 14.16 | 14.16 | 1.000x |
| tail | 8 | 3 | 8 | 15.49 | 15.49 | 1.000x | 14.91 | 14.91 | 1.000x |
14.93 | 14.93 | 1.000x | 14.62 | 14.62 | 1.000x |
| tail | 8 | 3 | 16 | 19.15 | 19.15 | 1.000x | 19.52 | 19.52 | 1.000x |
19.25 | 19.25 | 1.000x | 18.94 | 18.94 | 1.000x |
| tail | 8 | 4 | 2 | 11.33 | 11.33 | 1.000x | 11.01 | 11.01 | 1.000x |
10.96 | 10.96 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 4 | 4 | 13.12 | 13.12 | 1.000x | 12.67 | 12.67 | 1.000x |
12.72 | 12.72 | 1.000x | 12.59 | 12.59 | 1.000x |
| tail | 8 | 4 | 5 | 13.79 | 13.79 | 1.000x | 13.54 | 13.54 | 1.000x |
13.25 | 13.25 | 1.000x | 13.07 | 13.07 | 1.000x |
| tail | 8 | 4 | 6 | 13.62 | 13.62 | 1.000x | 13.66 | 13.66 | 1.000x |
13.86 | 13.86 | 1.000x | 13.50 | 13.50 | 1.000x |
| tail | 8 | 4 | 7 | 14.18 | 14.18 | 1.000x | 14.24 | 14.24 | 1.000x |
14.40 | 14.40 | 1.000x | 14.18 | 14.18 | 1.000x |
| tail | 8 | 4 | 8 | 15.36 | 15.36 | 1.000x | 15.23 | 15.23 | 1.000x |
14.83 | 14.83 | 1.000x | 14.70 | 14.70 | 1.000x |
| tail | 8 | 4 | 16 | 19.07 | 19.07 | 1.000x | 19.28 | 19.28 | 1.000x |
19.17 | 19.17 | 1.000x | 18.86 | 18.86 | 1.000x |
| tail | 8 | 5 | 2 | 11.12 | 11.12 | 1.000x | 11.06 | 11.06 | 1.000x |
10.77 | 10.77 | 1.000x | 10.80 | 10.80 | 1.000x |
| tail | 8 | 5 | 8 | 15.55 | 15.55 | 1.000x | 15.30 | 15.30 | 1.000x |
15.18 | 15.18 | 1.000x | 15.12 | 15.12 | 1.000x |
| tail | 8 | 8 | 2 | 11.12 | 11.12 | 1.000x | 10.94 | 10.94 | 1.000x |
10.82 | 10.82 | 1.000x | 10.69 | 10.69 | 1.000x |
| tail | 8 | 8 | 8 | 15.57 | 15.57 | 1.000x | 15.49 | 15.49 | 1.000x |
15.36 | 15.36 | 1.000x | 15.17 | 15.17 | 1.000x |
| tail | 8 | 9 | 2 | 11.23 | 11.23 | 1.000x | 11.01 | 11.01 | 1.000x |
10.91 | 10.91 | 1.000x | 10.82 | 10.82 | 1.000x |
| tail | 8 | 9 | 8 | 15.89 | 15.89 | 1.000x | 15.62 | 15.62 | 1.000x |
15.42 | 15.42 | 1.000x | 15.14 | 15.14 | 1.000x |
| tail | 8 | 16 | 2 | 11.25 | 11.25 | 1.000x | 11.26 | 11.26 | 1.000x |
10.98 | 10.98 | 1.000x | 10.85 | 10.85 | 1.000x |
| tail | 8 | 16 | 8 | 15.97 | 15.97 | 1.000x | 15.66 | 15.66 | 1.000x |
15.46 | 15.46 | 1.000x | 15.34 | 15.34 | 1.000x |
| tail | 8 | 32 | 2 | 11.74 | 11.74 | 1.000x | 11.62 | 11.62 | 1.000x |
11.52 | 11.52 | 1.000x | 11.46 | 11.46 | 1.000x |
| tail | 8 | 32 | 8 | 16.40 | 16.40 | 1.000x | 16.10 | 16.10 | 1.000x |
15.92 | 15.92 | 1.000x | 15.94 | 15.94 | 1.000x |
| tail | 8 | 64 | 2 | 12.51 | 11.87 | 1.054x | 12.45 | 11.66 | 1.067x |
12.34 | 11.63 | 1.061x | 12.27 | 11.50 | 1.067x |
| tail | 8 | 64 | 8 | 17.47 | 16.48 | 1.060x | 17.06 | 16.26 | 1.049x |
17.02 | 16.18 | 1.052x | 16.83 | 16.05 | 1.049x |
| tail | 8 | 128 | 2 | 14.56 | 13.36 | 1.090x | 14.38 | 13.22 | 1.088x |
14.29 | 13.22 | 1.081x | 14.00 | 12.90 | 1.086x |
| tail | 8 | 128 | 8 | 19.57 | 18.35 | 1.066x | 19.23 | 18.05 | 1.066x |
18.96 | 17.86 | 1.062x | 18.64 | 17.52 | 1.064x |

*Times are µs per call on one rank from `bench_gpu_time_with_cupti` with
cold L2 and CUDA graph replay; both sides interleave in groups over two
passes, the second in reversed order; each value is the mean of the two
per-pass medians on one GPU; rows this PR does not change show the value
of #7742 in both columns; speedup = previous / this PR; decode tail rows
reduce P routed partials; B200 and GB200 NVL72 (`sm_100a`), B300 and
GB300 NVL72 (`sm_103a`); B200 and B300 have 148 SMs, GB200 and GB300
152; CUDA 13.4.*

Cake also ships a TP12 fused tail of this block for GB200/GB300 NVL72 in
`kimi_k3_tp12_tail`; both packages are BF16 only and target `sm_100a`
and `sm_103a`.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded decode-tail routing to cover additional token counts and
partial-count configurations, including split-finalize cases.
* **Bug Fixes**
* Improved output handling for larger token batches and multi-segment
normalization, with more reliable completion of partial results.
* **Tests**
* Added coverage for route boundaries, registered kernels, repeatability
across launches and graph replays, and routed-result comparisons.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b5be99d](https://github.com/flashinfer-ai/flashinfer/commit/b5be99dd308f0af52abe7406700d80eeb5067e34)

- **作者**: eigen
- **时间**: 2026-10-29T17:20:11Z
- **提交信息**: fix(cake_lm_head_loss): sm_100a expect-tx arrive first under nvcc 12.9 and 13.0; sm_100a toolkit floor 12.9 (#7858)

FlashInfer's Cake chunked LM-head + loss backend
(`flashinfer.chunked_lm_head`) fuses the chunked large-vocabulary
projection (BF16 GEMM, FP32 accumulation) with log-sum-exp and the loss,
with a memory-bounded backward. It has one data type (BF16 X/W, FP32
statistics and loss) and three entry forms: cross-entropy
(`chunked_lm_head_loss(..., objective="ce")`), clipped policy-gradient
(`chunked_lm_head_loss(..., objective="policy")`), and differentiable
per-token log-probability (`chunked_lm_head_logprob`). This PR changes
only the sm_100a programs, and only when nvcc 12.9 or 13.0 compiles
them. With those toolkits, the 2-CTA GEMM producer loops (logits, dX,
dW) now issue each pipeline stage's expect-tx arrive before that stage's
TMA loads. That build had faulted intermittently on GB200 with an
illegal instruction, so this addresses the GB200 fault reported in
#7545. Builds by CUDA 13.1 to 13.4 keep the previously shipped machine
code. The sm_103a programs are unchanged at every toolkit. The package's
minimum toolkit for sm_100a is now CUDA 12.9. Compared with the previous
Cake version on FlashInfer main, speed is unchanged within measurement
noise at CUDA 13.0.88. The geometric-mean ratio (this PR / previous)
over 37 shapes is 0.99987 (95% CI 0.99955 to 1.00022) cooled and 1.00022
(0.99970 to 1.00076) hot. No shape was slower at the family-wise
(Bonferroni) level. Two shape-states were nominally slower in kernel
time: log-probability T=16231 chunk 4096, cooled, by 0.45 %, and
log-probability T=8117, hot, by 0.56 %. CUDA 12.9 was not timed.

| entry | T | chunk | H | V | ignored rows | cooled previous (ms) |
cooled this PR (ms) | cooled speedup | hot previous (ms) | hot this PR
(ms) | hot speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|
| log-probability | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 75.853 |
75.853 | 1.000x | 84.955 | 85.049 | 0.999x |
| log-probability | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 77.318 |
77.316 | 1.000x | 87.195 | 87.359 | 0.998x |
| loss, policy | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 58.031 |
58.028 | 1.000x | 65.337 | 65.438 | 0.998x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 57.441 | 57.340
| 1.002x | 64.811 | 64.590 | 1.003x |
| loss, ce | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 56.092 | 56.045
| 1.001x | 63.069 | 62.965 | 1.002x |
| loss, policy | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 56.305 |
56.320 | 1.000x | 63.348 | 63.330 | 1.000x |
| loss, policy | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 62.179 |
62.282 | 0.998x | 70.245 | 70.344 | 0.999x |
| loss, ce | 1 | 4096 | 6144 | 154880 | 0 (0 %) | 1.356 | 1.354 | 1.001x
| 1.363 | 1.361 | 1.001x |
| log-probability | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 10.796 |
10.794 | 1.000x | 10.764 | 10.775 | 0.999x |
| loss, ce | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 122.370 |
122.274 | 1.001x | 132.900 | 132.918 | 1.000x |
| loss, ce | 4095 | 4096 | 6144 | 154880 | 205 (5 %) | 14.780 | 14.778 |
1.000x | 15.006 | 14.969 | 1.002x |
| log-probability | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 329.436
| 329.587 | 1.000x | 346.930 | 346.939 | 1.000x |
| loss, policy | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 28.704 |
28.699 | 1.000x | 30.779 | 30.710 | 1.002x |
| loss, ce | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 57.568 | 57.590
| 1.000x | 64.646 | 64.762 | 0.998x |
| loss, policy | 16172 | 4096 | 6144 | 154880 | 809 (5 %) | 56.453 |
56.477 | 1.000x | 63.520 | 63.416 | 1.002x |
| loss, ce | 16231 | 2048 | 6144 | 154880 | 812 (5 %) | 59.252 | 59.245
| 1.000x | 66.727 | 66.745 | 1.000x |
| loss, ce | 16231 | 4096 | 8192 | 128256 | 812 (5 %) | 63.675 | 63.592
| 1.001x | 71.824 | 71.687 | 1.002x |
| log-probability | 16231 | 4096 | 6144 | 154880 | 812 (5 %) | 75.900 |
76.250 | 0.995x | 85.679 | 85.544 | 1.002x |
| loss, policy | 16231 | 4096 | 7168 | 129280 | 812 (5 %) | 55.121 |
55.096 | 1.000x | 61.862 | 61.986 | 0.998x |
| loss, policy | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 7.481 | 7.482
| 1.000x | 7.487 | 7.488 | 1.000x |
| log-probability | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 157.290
| 157.095 | 1.001x | 172.290 | 172.286 | 1.000x |
| loss, policy | 32463 | 4096 | 6144 | 154880 | 1623 (5 %) | 118.465 |
118.267 | 1.002x | 130.001 | 129.962 | 1.000x |
| loss, ce | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 14.926 | 14.922 |
1.000x | 15.087 | 15.037 | 1.003x |
| loss, ce | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 253.330 |
253.457 | 0.999x | 268.589 | 268.534 | 1.000x |
| loss, ce | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 29.535 | 29.516 |
1.001x | 31.338 | 31.384 | 0.999x |
| loss, ce | 16231 | 1024 | 6144 | 154880 | 812 (5 %) | 68.625 | 68.631
| 1.000x | 76.157 | 76.338 | 0.998x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 0 (0 %) | 61.918 | 61.857 |
1.001x | 68.891 | 68.798 | 1.001x |
| loss, ce | 16231 | 4096 | 6144 | 154880 | 4869 (30 %) | 43.183 |
43.164 | 1.000x | 47.086 | 47.187 | 0.998x |
| loss, ce | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 59.275 | 59.311
| 0.999x | 65.703 | 65.631 | 1.001x |
| log-probability | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 77.596 |
77.480 | 1.001x | 85.414 | 85.444 | 1.000x |
| loss, policy | 16231 | 8192 | 6144 | 154880 | 812 (5 %) | 58.151 |
58.178 | 1.000x | 64.154 | 64.367 | 0.997x |
| loss, ce | 2048 | 4096 | 6144 | 154880 | 102 (5 %) | 7.707 | 7.707 |
1.000x | 7.517 | 7.521 | 0.999x |
| log-probability | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 20.552 |
20.543 | 1.000x | 20.497 | 20.526 | 0.999x |
| loss, policy | 4096 | 4096 | 6144 | 154880 | 205 (5 %) | 14.891 |
14.882 | 1.001x | 14.765 | 14.786 | 0.999x |
| loss, ce | 4097 | 4096 | 6144 | 154880 | 205 (5 %) | 15.131 | 15.140 |
0.999x | 15.003 | 15.027 | 0.998x |
| loss, policy | 65031 | 4096 | 6144 | 154880 | 3252 (5 %) | 251.219 |
251.241 | 1.000x | 265.756 | 265.740 | 1.000x |
| log-probability | 8117 | 4096 | 6144 | 154880 | 406 (5 %) | 39.379 |
39.384 | 1.000x | 41.514 | 41.731 | 0.995x |

Measured on B200 (sm_100a), with both packages built by nvcc 13.0.88,
the toolkit where the machine code differs. The table covers 37 shapes
in two timing states. Each time covers one forward + backward call: the
GPU span from the first to the last kernel, measured with CUPTI with the
L2 flushed. "Cooled": the GPU is idle-cooled before each call. "Hot":
calls begin 2.0 ms apart without cooling. Each value is the median
pooled over 2 x 64 interleaved A/B rounds per state. Speedup = previous
/ this PR.

Cake ships no other data type, layout or fused form of this kernel, and
the backend covers sm_100a (B200/GB200) and sm_103a (B300/GB300).


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Compatibility**
* The experimental CAKE language-model head loss now requires CUDA
Toolkit 12.9 or later.

* **Bug Fixes**
* Adjusted data-loading order for selected GPU and CUDA toolkit
combinations. CUDA 13.0 fault mitigations remain in place; they address
observed faults but do not resolve their underlying cause.

* **Documentation**
* Updated notes on toolkit-specific behavior, reported faults, and
timing observations.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bc5093b](https://github.com/flashinfer-ai/flashinfer/commit/bc5093b1220d4c891bd58fb4ea3dc352d7379212)

- **作者**: eigen
- **时间**: 2026-10-29T17:19:13Z
- **提交信息**: feat(cake_mhc_train): head (stream mean) forward / backward kernels with an autograd node (#7856)

The mHC training head is the BF16 mean over the 4 mHC residual streams:
it computes `Y = X.mean(1)` on a `[T, 4, H]` input and also provides the
gradient. Issue #7046 §2 reported that no kernel existed for it. The
kernel has three variants: the forward, the writing backward (`dX = dY *
0.25`) and the accumulating backward (`dX += dY * 0.25`, the
AccumulateGrad form). This PR adds all three as the new package
`cake_mhc_train_head` with an autograd node. There is no earlier Cake
version, so the baseline is PyTorch: `X.mean(dim=1)` (fwd),
`torch.autograd.grad` through MeanBackward (bwd), and autograd backward
into a leaf whose `.grad` already exists, i.e. AccumulateGrad (acc).
Times are CUPTI kernel time in microseconds with the L2 cache flushed
before each call, and speedup is PyTorch / Cake.

**NVIDIA B200 (sm_100a), CUDA 13.4, PyTorch 2.14.1+cu130, L2 flushed
before each call**

| T | H | fwd Cake us | fwd PyTorch us | fwd speedup | bwd Cake us | bwd
PyTorch us | bwd speedup | acc Cake us | acc PyTorch us | acc speedup |
|---|---|---|---|---|---|---|---|---|---|---|
| 1024 | 4096 | 9.26 | 19.16 | 2.07x | 7.34 | 40.17 | 5.47x | 13.66 |
53.80 | 3.94x |
| 4096 | 4096 | 27.54 | 66.03 | 2.40x | 27.36 | 149.77 | 5.47x | 46.50 |
211.13 | 4.54x |
| 16263 | 4096 | 98.44 | 249.09 | 2.53x | 101.73 | 581.91 | 5.72x |
175.72 | 814.14 | 4.63x |
| 65536 | 4096 | 384.51 | 991.11 | 2.58x | 403.03 | 2333.28 | 5.79x |
697.81 | 3256.00 | 4.67x |
| 4096 | 5120 | 33.54 | 81.18 | 2.42x | 33.66 | 185.83 | 5.52x | 57.40 |
261.63 | 4.56x |
| 16263 | 5120 | 122.02 | 309.90 | 2.54x | 126.70 | 726.75 | 5.74x |
218.67 | 1015.35 | 4.64x |
| 4096 | 7168 | 45.54 | 111.94 | 2.46x | 46.16 | 258.72 | 5.60x | 79.14
| 363.30 | 4.59x |
| 16263 | 7168 | 169.52 | 431.75 | 2.55x | 176.34 | 1016.30 | 5.76x |
304.82 | 1418.97 | 4.66x |

**NVIDIA GB200 (sm_100a), CUDA 13.4, PyTorch 2.14.1+cu130, L2 flushed
before each call**

| T | H | fwd Cake us | fwd PyTorch us | fwd speedup | bwd Cake us | bwd
PyTorch us | bwd speedup | acc Cake us | acc PyTorch us | acc speedup |
|---|---|---|---|---|---|---|---|---|---|---|
| 1024 | 4096 | 8.99 | 17.54 | 1.95x | 7.16 | 37.55 | 5.24x | 13.19 |
50.50 | 3.83x |
| 4096 | 4096 | 26.58 | 61.75 | 2.32x | 26.24 | 139.59 | 5.32x | 44.99 |
198.80 | 4.42x |
| 16263 | 4096 | 96.09 | 232.26 | 2.42x | 97.39 | 542.83 | 5.57x |
169.66 | 765.94 | 4.51x |
| 65536 | 4096 | 373.53 | 922.61 | 2.47x | 385.30 | 2175.88 | 5.65x |
673.81 | 3061.96 | 4.54x |
| 4096 | 5120 | 32.55 | 75.93 | 2.33x | 32.20 | 173.82 | 5.40x | 55.50 |
246.91 | 4.45x |
| 16263 | 5120 | 118.91 | 288.76 | 2.43x | 121.14 | 678.38 | 5.60x |
211.29 | 956.10 | 4.53x |
| 4096 | 7168 | 44.28 | 104.44 | 2.36x | 44.29 | 242.21 | 5.47x | 76.50
| 342.82 | 4.48x |
| 16263 | 7168 | 164.62 | 402.14 | 2.44x | 168.65 | 950.33 | 5.63x |
294.46 | 1337.44 | 4.54x |

**NVIDIA GB300 (sm_103a), CUDA 13.4, PyTorch 2.14.1+cu130, L2 flushed
before each call**

| T | H | fwd Cake us | fwd PyTorch us | fwd speedup | bwd Cake us | bwd
PyTorch us | bwd speedup | acc Cake us | acc PyTorch us | acc speedup |
|---|---|---|---|---|---|---|---|---|---|---|
| 1024 | 4096 | 8.95 | 17.23 | 1.92x | 7.17 | 36.84 | 5.14x | 13.14 |
49.51 | 3.77x |
| 4096 | 4096 | 26.56 | 61.10 | 2.30x | 26.17 | 137.52 | 5.26x | 45.27 |
196.93 | 4.35x |
| 16263 | 4096 | 96.40 | 230.77 | 2.39x | 97.28 | 535.08 | 5.50x |
170.89 | 760.50 | 4.45x |
| 65536 | 4096 | 373.30 | 917.06 | 2.46x | 385.42 | 2145.66 | 5.57x |
678.06 | 3043.89 | 4.49x |
| 4096 | 5120 | 32.57 | 75.19 | 2.31x | 32.01 | 171.17 | 5.35x | 56.08 |
244.88 | 4.37x |
| 16263 | 5120 | 118.56 | 286.82 | 2.42x | 121.09 | 668.74 | 5.52x |
212.82 | 948.71 | 4.46x |
| 4096 | 7168 | 44.22 | 103.59 | 2.34x | 44.00 | 238.76 | 5.43x | 77.14
| 340.33 | 4.41x |
| 16263 | 7168 | 164.64 | 399.66 | 2.43x | 168.70 | 936.43 | 5.55x |
296.53 | 1325.70 | 4.47x |

The head kernels support H 4096 / 5120 / 7168 on sm_100a and sm_103a and
H 4096 on sm_107a, while Cake ships the rest of the four-stream mHC
training path (the forward prepare / mapping and backward finish
kernels) in `cake_mhc_train`, and the mHC training family ships on
sm_100a, sm_103a and sm_107a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added BF16 mean-head operations for four-stream residual tensors,
including forward, backward, and autograd support.
* Added support for hidden sizes 4096, 5120, and 7168 on supported GPU
architectures; size 4096 is also supported on SM107.
* Added a support query and documented the head APIs and their results.
* **Tests**
* Added coverage for numerical results, edge cases, autograd, activation
checkpointing, and CUDA graph capture.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4c3d69a](https://github.com/flashinfer-ai/flashinfer/commit/4c3d69a1f996c4d67965eeddab02cdb005ec8572)

- **作者**: eigen
- **时间**: 2026-10-29T17:14:33Z
- **提交信息**: perf(cake_blackwell_bf16_fp4): read alpha once, early, in the SM100 small-M split-K reduce-scatter program (#7863)

FlashInfer `mm_bf16_fp4` multiplies BF16 activations by FP4 (E2M1)
weights with E4M3 block scales and FP32 accumulation. Cake ships it as
97 programs in two backend variants: `blackwell-native` (cuDNN-ABI
layouts, BF16 or FP16 output) and `blackwell-tiled` (CuTe-ABI
prepared-tile layouts, BF16 output). This PR regenerates 1 of the 97. It
is the small-M split-K reduce-scatter `blackwell-tiled` program with
alpha and BF16 output, which serves the 1/4096/4096 `blackwell-tiled`
row. Only its sm_100a program changes. Its sm_103a program and every
other program are unchanged, so there is no GB300 table. In the previous
program, the warps that add and store the output slices read alpha
through the non-coherent path after their mailbox wait, which put that
load on the critical path of the stores. Now one warp per CTA reads
alpha once, with a coherent load right after griddepcontrol.wait and the
A tile load issue. The load completes during decode, and the slice
stores scale by that register. The baseline is the previous Cake
programs, and speedup is previous time / this PR's time. On B200 the
1/4096/4096 `blackwell-tiled` row measures 1.020x (6.416 -> 6.288 us).
All other rows run unchanged programs and measure 0.998x-1.000x.

**NVIDIA B200 (sm_100a), CUDA 13.4:** mean over separate processes of
the per-process median CUPTI kernel time in us (two processes per side;
four for the 1/4096/4096 row (blackwell-tiled)), cold L2, PDL on; alpha
passed and BF16 output unless the variant column notes otherwise.

| Shape M/N/K | Variant | Previous Cake (us) | This PR (us) | Speedup |
|---|---|---:|---:|---:|
| 1/4096/4096 | blackwell-native | 7.168 | 7.168 | 1.000x |
| 1/4096/4096 | blackwell-tiled | 6.416 | 6.288 | 1.020x |
| 768/2112/2048 | blackwell-native | 9.056 | 9.060 | 1.000x |
| 768/2112/2048 | blackwell-tiled | 10.084 | 10.082 | 1.000x |
| 7/4160/192 | blackwell-tiled | 2.832 | 2.832 | 1.000x |
| 13/11008/128 | blackwell-tiled | 3.088 | 3.093 | 0.998x |
| 17/3072/3072 | blackwell-tiled | 7.626 | 7.624 | 1.000x |
| 16/1024/1024 | blackwell-tiled, alpha=None | 3.000 | 3.000 | 1.000x |
| 16/1024/1024 | blackwell-native, FP16 output | 3.016 | 3.016 | 1.000x
|
| 16/1024/1024 | blackwell-native, caller-provided `out` | 3.019 | 3.020
| 1.000x |
| 16/1024/1024 | blackwell-tiled, caller-provided `out` | 2.968 | 2.968
| 1.000x |

Cake has no other variants of this kernel: FP16 output is only on
`blackwell-native`, there are no fused forms, and every program ships
for sm_100a (B200) and sm_103a (GB300).

Co-authored-by: Avery Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [5708bb6](https://github.com/flashinfer-ai/flashinfer/commit/5708bb619179de28a9e1dbc857c8e07632c2c844)

- **作者**: Netanel Haber
- **时间**: 2026-10-29T16:55:35Z
- **提交信息**: [SDSA 1/6][Attention] Add token-sparse MQA decode to trtllm-gen (#6420)

In token-sparse attention, each query token attends only to its own list
of keys. For example, a DSA indexer selects the Top-K keys of each
token. trtllm-gen has kernels for this, but FlashInfer uses them only
for MLA.

This PR adds `sparse_top_k=K` to `trtllm_batch_decode_with_kv_cache`,
for MQA:
- Each query token is its own request, over cache pages of one token.
MTP draft tokens are requests too.
- `block_tables` gives, for each token, the cache rows of the keys it
attends to: one list for K and one for V. `seq_lens` gives how many
entries of each list the token uses.
- `token_sparse_kv_indices` makes `block_tables` and `seq_lens` from the
Top-K key positions of each token and the block table of its request.
- A call with `sparse_top_k` has its own trace template,
`trtllm_batch_decode_token_sparse`.

For example, with 2 query tokens and `sparse_top_k=4`:
```
block_tables = [[[7, 2, 9, -1], [7, 2, 9, -1]],  # token 0: K rows, V rows
                [[5, 1, 8,  3], [5, 1, 8,  3]]]  # token 1: K rows, V rows
seq_lens = [3, 4]                                # token 0 uses 3 entries, token 1 uses 4
```

The limits are:
- The KV cache must have one KV head (MQA), because the kernels cannot
select a KV head.
- The call rejects a sliding window, attention sinks and head dim 512.
For head dim 512 (MLA), use `trtllm_batch_decode_with_kv_cache_mla`.

MLA and dense attention do not change. The trtllm-gen decode,
block-sparse and MLA tests give the same results as on `main`.

This PR is part 1 of 6 of SDSA: sparse attention with a one-head indexer
and an MQA core. The indexer selects the Top-K keys of each query token,
and the MQA core attends to these keys. Parts 1-2 add token-sparse
attention, and parts 3-6 add the indexer. The next part is #6421.

I used AI assistance.

---------

Signed-off-by: Netanel Haber <nhaber@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Brian K. Ryu <bryu@nvidia.com>

### [c4ea174](https://github.com/flashinfer-ai/flashinfer/commit/c4ea1741afa2829f9bdcc716473f2f08e23d0bcb)

- **作者**: eigen
- **时间**: 2026-10-29T15:59:52Z
- **提交信息**: perf(cake_minimax_h3_varlen_attention): B200 tail schedules and eight-CTA fp4 quantizer build (#7862)

This PR updates `flashinfer.experimental.minimax_h3_varlen_attention`,
the Cake MiniMax-H3 packed variable-length attention kernel (packed
segments, optional split-KV).
The kernel has three data-type variants: BF16, NVFP4 with fp4 P·V
(`pv_mode="fp4"`), and NVFP4 with fp8 P·V (`pv_mode="fp8"`). The shapes
cover two Q/K/V layouts: contiguous and a fused-QKV view.
This PR updates the sm_100a (B200) programs and host plans of all three
variants; the sm_103a (GB300) programs and plans are unchanged from the
previous version.
The baseline ("previous") is the Cake version of this kernel on
FlashInfer main before this PR. The three tables below compare it with
this PR on B200, one table per variant. The geomeans and row counts
below are computed from the tables.

- NVFP4, fp4 P·V: every row is faster in both runs. Geomean 1.0064x /
1.0061x (run 1 / run 2); rows range from 1.0017x to 1.0141x.
- NVFP4, fp8 P·V: every row is faster in run 1. In run 2, two rows are
below 1.0000x: `center_10s_p2_m37120` at 0.9998x and
`center_15s_p2_m54976` at 0.9985x. Geomean 1.0080x / 1.0076x.
- BF16: geomean 1.0052x / 1.0079x. 9 of 42 rows are below 1.0000x in run
1 and 4 of 42 in run 2. The lowest is `center_5s_p2_m19296` at 0.9641x
in run 1, which is 1.0138x in run 2. The lowest in run 2 is
`tail_5s_p1_m38531` at 0.9943x.

### B200 (sm_100a) · BF16

NVIDIA B200 (`sm_100a`), CUDA 13.4, BF16 variant. "Previous" and "this
PR" are GPU latency in ms per call with a cold L2, measured interleaved
in the same process. Run 1 and run 2 were measured on two different B200
GPUs. Speedup is the median over timing groups of previous / this PR
(above 1.0000x means this PR is faster), so it can differ from the ratio
of the two latency columns.

| shape | tokens | segments | heads | layout | run 1 previous (ms) | run
1 this PR (ms) | run 1 speedup | run 2 previous (ms) | run 2 this PR
(ms) | run 2 speedup |
|---|---:|---:|---:|---|---:|---:|---:|---:|---:|---:|
| `center_4s_p1_m33472` | 33472 | 1 | 56 | contiguous | 22.1340 |
22.1892 | 0.9961x | 22.4940 | 22.4975 | 1.0009x |
| `center_4s_p2_m16736` | 16736 | 1 | 28 | contiguous | 2.5368 | 2.5076
| 1.0220x | 2.5414 | 2.5330 | 1.0062x |
| `center_4s_p4_m8368` | 8368 | 1 | 14 | contiguous | 0.3219 | 0.3183 |
1.0112x | 0.3298 | 0.3268 | 1.0089x |
| `center_4s_p8_m4184` | 4184 | 1 | 7 | contiguous | 0.0542 | 0.0538 |
1.0083x | 0.0563 | 0.0557 | 1.0098x |
| `center_5s_p1_m38592` | 38592 | 1 | 56 | contiguous | 29.5951 |
29.3073 | 1.0117x | 30.1647 | 29.9612 | 1.0049x |
| `center_5s_p2_m19296` | 19296 | 1 | 28 | contiguous | 3.4381 | 3.4285
| 0.9641x | 3.5201 | 3.4722 | 1.0138x |
| `center_5s_p4_m9648` | 9648 | 1 | 14 | contiguous | 0.4172 | 0.4137 |
1.0086x | 0.4259 | 0.4220 | 1.0093x |
| `center_5s_p8_m4824` | 4824 | 1 | 7 | contiguous | 0.0621 | 0.0616 |
1.0094x | 0.0650 | 0.0644 | 1.0094x |
| `center_6s_p1_m48768` | 48768 | 1 | 56 | contiguous | 47.0081 |
47.2623 | 0.9958x | 47.7718 | 48.0690 | 0.9977x |
| `center_6s_p2_m24384` | 24384 | 1 | 28 | contiguous | 5.6718 | 5.6604
| 1.0017x | 5.7168 | 5.6679 | 1.0086x |
| `center_6s_p4_m12192` | 12192 | 1 | 14 | contiguous | 0.7098 | 0.7017
| 1.0103x | 0.7110 | 0.7031 | 1.0113x |
| `center_6s_p8_m6096` | 6096 | 1 | 7 | contiguous | 0.0944 | 0.0936 |
1.0092x | 0.0989 | 0.0980 | 1.0098x |
| `center_8s_p1_m58944` | 58944 | 1 | 56 | contiguous | 69.0276 |
68.8377 | 1.0023x | 70.3358 | 70.1150 | 1.0031x |
| `center_8s_p2_m29472` | 29472 | 1 | 28 | contiguous | 8.1127 | 8.0203
| 1.0115x | 8.1397 | 8.1473 | 1.0015x |
| `center_8s_p4_m14736` | 14736 | 1 | 14 | contiguous | 0.9989 | 0.9747
| 1.0125x | 1.0055 | 1.0004 | 1.0046x |
| `center_8s_p8_m7368` | 7368 | 1 | 7 | contiguous | 0.1388 | 0.1375 |
1.0093x | 0.1453 | 0.1437 | 1.0111x |
| `center_10s_p1_m74240` | 74240 | 1 | 56 | contiguous | 109.0792 |
109.1317 | 0.9994x | 110.8420 | 110.9417 | 1.0031x |
| `center_10s_p2_m37120` | 37120 | 1 | 28 | contiguous | 13.1773 |
12.9242 | 0.9937x | 13.5553 | 13.2372 | 1.0240x |
| `center_10s_p4_m18560` | 18560 | 1 | 14 | contiguous | 1.5916 | 1.5736
| 1.0138x | 1.6128 | 1.6147 | 0.9986x |
| `center_10s_p8_m9280` | 9280 | 1 | 7 | contiguous | 0.2064 | 0.2043 |
1.0105x | 0.2117 | 0.2092 | 1.0119x |
| `center_15s_p1_m109952` | 109952 | 1 | 56 | contiguous | 240.9190 |
240.9229 | 1.0014x | 244.1437 | 244.3654 | 0.9987x |
| `center_15s_p2_m54976` | 54976 | 1 | 28 | contiguous | 29.9700 |
30.0677 | 0.9968x | 30.1652 | 29.9791 | 1.0062x |
| `center_15s_p4_m27488` | 27488 | 1 | 14 | contiguous | 3.5283 | 3.5001
| 0.9985x | 3.5949 | 3.5423 | 1.0120x |
| `center_15s_p8_m13744` | 13744 | 1 | 7 | contiguous | 0.4296 | 0.4261
| 1.0080x | 0.4253 | 0.4211 | 1.0099x |
| `tail_5s_p1_m38531` | 38531 | 1 | 56 | contiguous | 29.8772 | 29.6149
| 1.0089x | 30.0510 | 29.7844 | 0.9943x |
| `tail_5s_p1_m38629` | 38629 | 1 | 56 | contiguous | 29.8594 | 29.2121
| 1.0226x | 30.0231 | 29.9815 | 1.0047x |
| `tail_5s_p2_m19235` | 19235 | 1 | 28 | contiguous | 3.4421 | 3.4145 |
1.0057x | 3.5248 | 3.4785 | 1.0133x |
| `tail_5s_p2_m19333` | 19333 | 1 | 28 | contiguous | 3.5013 | 3.4493 |
1.0025x | 3.5488 | 3.4697 | 1.0269x |
| `tail_5s_p4_m9587` | 9587 | 1 | 14 | contiguous | 0.4210 | 0.4178 |
1.0077x | 0.4169 | 0.4126 | 1.0104x |
| `tail_5s_p4_m9685` | 9685 | 1 | 14 | contiguous | 0.4255 | 0.4222 |
1.0079x | 0.4210 | 0.4173 | 1.0089x |
| `tail_5s_p8_m4763` | 4763 | 1 | 7 | contiguous | 0.0628 | 0.0623 |
1.0087x | 0.0630 | 0.0625 | 1.0092x |
| `tail_5s_p8_m4861` | 4861 | 1 | 7 | contiguous | 0.0630 | 0.0625 |
1.0087x | 0.0633 | 0.0627 | 1.0092x |
| `pad_5s_p4_used9611_total9664` | 9664 | 2 | 14 | contiguous | 0.4289 |
0.4254 | 1.0081x | 0.4258 | 0.4212 | 1.0107x |
| `pad_15s_p1_used109901_total109952` | 109952 | 2 | 56 | contiguous |
239.6636 | 241.0853 | 0.9941x | 242.1651 | 242.0619 | 1.0001x |
| `dit_t2va_p1_m32640` | 32640 | 1 | 56 | contiguous | 21.1850 | 20.9164
| 1.0095x | 21.2180 | 21.0801 | 1.0013x |
| `dit_2seg_p1_m16320x2` | 32640 | 2 | 56 | contiguous | 10.1987 |
10.1385 | 0.9935x | 10.3987 | 10.1608 | 1.0234x |
| `dit_short_p1_m3072_1024` | 4096 | 2 | 56 | contiguous | 0.1965 |
0.1950 | 1.0079x | 0.1957 | 0.1942 | 1.0078x |
| `dit_tiny_p1_m9_9` | 18 | 2 | 56 | contiguous | 0.0037 | 0.0037 |
1.0000x | 0.0037 | 0.0037 | 1.0000x |
| `dit_t2va_p1_m32640_fused_qkv_view` | 32640 | 1 | 56 | fused_qkv_view
| 20.9476 | 20.6238 | 1.0140x | 21.0650 | 20.6467 | 1.0156x |
| `dit_2seg_p1_m16320x2_fused_qkv_view` | 32640 | 2 | 56 |
fused_qkv_view | 10.2558 | 10.2006 | 1.0051x | 10.4026 | 10.3158 |
1.0117x |
| `dit_short_p1_m3072_1024_fused_qkv_view` | 4096 | 2 | 56 |
fused_qkv_view | 0.1969 | 0.1954 | 1.0079x | 0.1958 | 0.1943 | 1.0079x |
| `dit_tiny_p1_m9_9_fused_qkv_view` | 18 | 2 | 56 | fused_qkv_view |
0.0037 | 0.0037 | 1.0000x | 0.0037 | 0.0037 | 1.0000x |

### B200 (sm_100a) · NVFP4, pv_mode="fp4"

NVIDIA B200 (`sm_100a`), CUDA 13.4, NVFP4 variant with fp4 P·V
(`pv_mode="fp4"`). "Previous" and "this PR" are GPU latency in ms per
call with a cold L2, measured interleaved in the same process. Run 1 and
run 2 were measured on two different B200 GPUs. Speedup is the median
over timing groups of previous / this PR (above 1.0000x means this PR is
faster), so it can differ from the ratio of the two latency columns.

| shape | tokens | segments | heads | layout | run 1 previous (ms) | run
1 this PR (ms) | run 1 speedup | run 2 previous (ms) | run 2 this PR
(ms) | run 2 speedup |
|---|---:|---:|---:|---|---:|---:|---:|---:|---:|---:|
| `center_4s_p1_m33472` | 33472 | 1 | 56 | contiguous | 16.2230 |
16.1584 | 1.0040x | 16.2040 | 16.1590 | 1.0027x |
| `center_4s_p2_m16736` | 16736 | 1 | 28 | contiguous | 2.1516 | 2.1432
| 1.0039x | 2.1730 | 2.1656 | 1.0035x |
| `center_4s_p4_m8368` | 8368 | 1 | 14 | contiguous | 0.3312 | 0.3292 |
1.0061x | 0.3315 | 0.3294 | 1.0062x |
| `center_4s_p8_m4184` | 4184 | 1 | 7 | contiguous | 0.0586 | 0.0579 |
1.0110x | 0.0588 | 0.0582 | 1.0093x |
| `center_5s_p1_m38592` | 38592 | 1 | 56 | contiguous | 21.4887 |
21.3872 | 1.0047x | 21.4936 | 21.3845 | 1.0047x |
| `center_5s_p2_m19296` | 19296 | 1 | 28 | contiguous | 2.8342 | 2.8217
| 1.0045x | 2.8615 | 2.8490 | 1.0043x |
| `center_5s_p4_m9648` | 9648 | 1 | 14 | contiguous | 0.4208 | 0.4187 |
1.0049x | 0.4211 | 0.4188 | 1.0056x |
| `center_5s_p8_m4824` | 4824 | 1 | 7 | contiguous | 0.0663 | 0.0656 |
1.0112x | 0.0667 | 0.0658 | 1.0141x |
| `center_6s_p1_m48768` | 48768 | 1 | 56 | contiguous | 33.9992 |
33.7619 | 1.0070x | 34.0000 | 33.7570 | 1.0072x |
| `center_6s_p2_m24384` | 24384 | 1 | 28 | contiguous | 4.4884 | 4.4671
| 1.0049x | 4.5207 | 4.5033 | 1.0039x |
| `center_6s_p4_m12192` | 12192 | 1 | 14 | contiguous | 0.6556 | 0.6497
| 1.0090x | 0.6649 | 0.6587 | 1.0093x |
| `center_6s_p8_m6096` | 6096 | 1 | 7 | contiguous | 0.1004 | 0.1001 |
1.0026x | 0.1006 | 0.1004 | 1.0025x |
| `center_8s_p1_m58944` | 58944 | 1 | 56 | contiguous | 49.4582 |
49.3078 | 1.0031x | 49.4595 | 49.3000 | 1.0032x |
| `center_8s_p2_m29472` | 29472 | 1 | 28 | contiguous | 6.3639 | 6.3244
| 1.0063x | 6.3641 | 6.3247 | 1.0062x |
| `center_8s_p4_m14736` | 14736 | 1 | 14 | contiguous | 0.8892 | 0.8827
| 1.0073x | 0.8853 | 0.8772 | 1.0094x |
| `center_8s_p8_m7368` | 7368 | 1 | 7 | contiguous | 0.1458 | 0.1452 |
1.0042x | 0.1460 | 0.1455 | 1.0033x |
| `center_10s_p1_m74240` | 74240 | 1 | 56 | contiguous | 77.6847 |
77.1018 | 1.0077x | 77.7190 | 77.1354 | 1.0076x |
| `center_10s_p2_m37120` | 37120 | 1 | 28 | contiguous | 9.9351 | 9.8627
| 1.0073x | 9.9420 | 9.8684 | 1.0075x |
| `center_10s_p4_m18560` | 18560 | 1 | 14 | contiguous | 1.3308 | 1.3283
| 1.0020x | 1.3307 | 1.3283 | 1.0017x |
| `center_10s_p8_m9280` | 9280 | 1 | 7 | contiguous | 0.2151 | 0.2135 |
1.0075x | 0.2152 | 0.2144 | 1.0033x |
| `center_15s_p1_m109952` | 109952 | 1 | 56 | contiguous | 169.6876 |
168.3908 | 1.0077x | 169.7969 | 168.5214 | 1.0076x |
| `center_15s_p2_m54976` | 54976 | 1 | 28 | contiguous | 21.5885 |
21.4433 | 1.0068x | 21.6010 | 21.4539 | 1.0069x |
| `center_15s_p4_m27488` | 27488 | 1 | 14 | contiguous | 2.8944 | 2.8806
| 1.0046x | 2.9201 | 2.9068 | 1.0046x |
| `center_15s_p8_m13744` | 13744 | 1 | 7 | contiguous | 0.4176 | 0.4163
| 1.0032x | 0.4171 | 0.4156 | 1.0037x |
| `tail_5s_p1_m38531` | 38531 | 1 | 56 | contiguous | 21.4592 | 21.3529
| 1.0054x | 21.4573 | 21.3577 | 1.0047x |
| `tail_5s_p1_m38629` | 38629 | 1 | 56 | contiguous | 21.4631 | 21.3387
| 1.0058x | 21.4613 | 21.3525 | 1.0051x |
| `tail_5s_p2_m19235` | 19235 | 1 | 28 | contiguous | 2.8340 | 2.8210 |
1.0046x | 2.8608 | 2.8482 | 1.0045x |
| `tail_5s_p2_m19333` | 19333 | 1 | 28 | contiguous | 2.8546 | 2.8405 |
1.0049x | 2.8815 | 2.8677 | 1.0048x |
| `tail_5s_p4_m9587` | 9587 | 1 | 14 | contiguous | 0.4161 | 0.4138 |
1.0054x | 0.4156 | 0.4134 | 1.0053x |
| `tail_5s_p4_m9685` | 9685 | 1 | 14 | contiguous | 0.4208 | 0.4185 |
1.0054x | 0.4206 | 0.4183 | 1.0055x |
| `tail_5s_p8_m4763` | 4763 | 1 | 7 | contiguous | 0.0665 | 0.0656 |
1.0137x | 0.0662 | 0.0653 | 1.0128x |
| `tail_5s_p8_m4861` | 4861 | 1 | 7 | contiguous | 0.0665 | 0.0656 |
1.0132x | 0.0663 | 0.0655 | 1.0122x |
| `pad_5s_p4_used9611_total9664` | 9664 | 2 | 14 | contiguous | 0.4324 |
0.4286 | 1.0090x | 0.4313 | 0.4286 | 1.0062x |
| `pad_15s_p1_used109901_total109952` | 109952 | 2 | 56 | contiguous |
169.6883 | 168.4701 | 1.0073x | 169.8421 | 168.5861 | 1.0075x |

### B200 (sm_100a) · NVFP4, pv_mode="fp8"

NVIDIA B200 (`sm_100a`), CUDA 13.4, NVFP4 variant with fp8 P·V
(`pv_mode="fp8"`). "Previous" and "this PR" are GPU latency in ms per
call with a cold L2, measured interleaved in the same process. Run 1 and
run 2 were measured on two different B200 GPUs. Speedup is the median
over timing groups of previous / this PR (above 1.0000x means this PR is
faster), so it can differ from the ratio of the two latency columns.

| shape | tokens | segments | heads | layout | run 1 previous (ms) | run
1 this PR (ms) | run 1 speedup | run 2 previous (ms) | run 2 this PR
(ms) | run 2 speedup |
|---|---:|---:|---:|---|---:|---:|---:|---:|---:|---:|
| `center_4s_p1_m33472` | 33472 | 1 | 56 | contiguous | 16.9549 |
16.8465 | 1.0064x | 16.9445 | 16.8382 | 1.0090x |
| `center_4s_p2_m16736` | 16736 | 1 | 28 | contiguous | 2.1771 | 2.1578
| 1.0089x | 2.2010 | 2.1797 | 1.0097x |
| `center_4s_p4_m8368` | 8368 | 1 | 14 | contiguous | 0.3297 | 0.3267 |
1.0094x | 0.3302 | 0.3272 | 1.0093x |
| `center_4s_p8_m4184` | 4184 | 1 | 7 | contiguous | 0.0583 | 0.0578 |
1.0083x | 0.0581 | 0.0578 | 1.0055x |
| `center_5s_p1_m38592` | 38592 | 1 | 56 | contiguous | 22.6644 |
22.3470 | 1.0072x | 22.5302 | 22.4709 | 1.0048x |
| `center_5s_p2_m19296` | 19296 | 1 | 28 | contiguous | 2.8624 | 2.8370
| 1.0090x | 2.8930 | 2.8661 | 1.0094x |
| `center_5s_p4_m9648` | 9648 | 1 | 14 | contiguous | 0.4186 | 0.4148 |
1.0093x | 0.4188 | 0.4149 | 1.0093x |
| `center_5s_p8_m4824` | 4824 | 1 | 7 | contiguous | 0.0660 | 0.0653 |
1.0118x | 0.0666 | 0.0659 | 1.0107x |
| `center_6s_p1_m48768` | 48768 | 1 | 56 | contiguous | 35.9899 |
35.7339 | 1.0041x | 35.8768 | 35.6564 | 1.0058x |
| `center_6s_p2_m24384` | 24384 | 1 | 28 | contiguous | 4.5156 | 4.4894
| 1.0058x | 4.5559 | 4.5295 | 1.0058x |
| `center_6s_p4_m12192` | 12192 | 1 | 14 | contiguous | 0.6571 | 0.6497
| 1.0113x | 0.6651 | 0.6574 | 1.0116x |
| `center_6s_p8_m6096` | 6096 | 1 | 7 | contiguous | 0.0985 | 0.0976 |
1.0095x | 0.0992 | 0.0985 | 1.0078x |
| `center_8s_p1_m58944` | 58944 | 1 | 56 | contiguous | 52.5691 |
52.1158 | 1.0096x | 52.3937 | 52.1947 | 1.0059x |
| `center_8s_p2_m29472` | 29472 | 1 | 28 | contiguous | 6.4022 | 6.3700
| 1.0050x | 6.4321 | 6.3501 | 1.0134x |
| `center_8s_p4_m14736` | 14736 | 1 | 14 | contiguous | 0.9047 | 0.8960
| 1.0097x | 0.8984 | 0.8903 | 1.0091x |
| `center_8s_p8_m7368` | 7368 | 1 | 7 | contiguous | 0.1440 | 0.1426 |
1.0097x | 0.1440 | 0.1426 | 1.0094x |
| `center_10s_p1_m74240` | 74240 | 1 | 56 | contiguous | 81.1955 |
80.8205 | 1.0059x | 81.7547 | 81.5052 | 1.0036x |
| `center_10s_p2_m37120` | 37120 | 1 | 28 | contiguous | 10.1051 |
10.0153 | 1.0053x | 10.1532 | 10.1429 | 0.9998x |
| `center_10s_p4_m18560` | 18560 | 1 | 14 | contiguous | 1.3299 | 1.3151
| 1.0114x | 1.3290 | 1.3140 | 1.0115x |
| `center_10s_p8_m9280` | 9280 | 1 | 7 | contiguous | 0.2156 | 0.2135 |
1.0099x | 0.2140 | 0.2119 | 1.0100x |
| `center_15s_p1_m109952` | 109952 | 1 | 56 | contiguous | 177.8153 |
177.3751 | 1.0038x | 179.7716 | 178.5273 | 1.0057x |
| `center_15s_p2_m54976` | 54976 | 1 | 28 | contiguous | 22.3346 |
22.1624 | 1.0071x | 22.6474 | 22.6809 | 0.9985x |
| `center_15s_p4_m27488` | 27488 | 1 | 14 | contiguous | 2.9191 | 2.8977
| 1.0073x | 2.9491 | 2.9270 | 1.0075x |
| `center_15s_p8_m13744` | 13744 | 1 | 7 | contiguous | 0.4152 | 0.4110
| 1.0101x | 0.4141 | 0.4099 | 1.0104x |
| `tail_5s_p1_m38531` | 38531 | 1 | 56 | contiguous | 22.1512 | 22.0757
| 1.0034x | 22.4803 | 22.3333 | 1.0053x |
| `tail_5s_p1_m38629` | 38629 | 1 | 56 | contiguous | 22.3294 | 22.1156
| 1.0063x | 22.5208 | 22.4980 | 1.0022x |
| `tail_5s_p2_m19235` | 19235 | 1 | 28 | contiguous | 2.8619 | 2.8363 |
1.0090x | 2.8919 | 2.8647 | 1.0095x |
| `tail_5s_p2_m19333` | 19333 | 1 | 28 | contiguous | 2.8785 | 2.8531 |
1.0089x | 2.9096 | 2.8820 | 1.0095x |
| `tail_5s_p4_m9587` | 9587 | 1 | 14 | contiguous | 0.4141 | 0.4100 |
1.0100x | 0.4133 | 0.4094 | 1.0095x |
| `tail_5s_p4_m9685` | 9685 | 1 | 14 | contiguous | 0.4200 | 0.4158 |
1.0101x | 0.4187 | 0.4146 | 1.0098x |
| `tail_5s_p8_m4763` | 4763 | 1 | 7 | contiguous | 0.0668 | 0.0664 |
1.0063x | 0.0660 | 0.0656 | 1.0068x |
| `tail_5s_p8_m4861` | 4861 | 1 | 7 | contiguous | 0.0671 | 0.0666 |
1.0067x | 0.0660 | 0.0656 | 1.0073x |
| `pad_5s_p4_used9611_total9664` | 9664 | 2 | 14 | contiguous | 0.4247 |
0.4202 | 1.0107x | 0.4237 | 0.4194 | 1.0105x |
| `pad_15s_p1_used109901_total109952` | 109952 | 2 | 56 | contiguous |
177.9543 | 177.1987 | 1.0052x | 180.2910 | 179.2821 | 1.0047x |

This kernel ships on sm_100a and sm_103a; FlashInfer main also has other
Cake variants of this attention, the all-FP8
`cake_minimax_h3_varlen_fp8_attention` for sm_100a and sm_103a and SM120
variants for sm_120a (NVFP4, NVFP4 with fp8 P·V, and FP8 quantized), so
together the Cake variants cover sm_100a, sm_103a and sm_120a.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added additional attention execution schedules on supported GPUs,
including multi-stream options for eligible workloads.
  * Added an optimized FP4 quantization option for eligible workloads.
* **Bug Fixes**
* Improved handling of tail tiles and tensor-boundary validation, with
clearer errors identifying invalid dimensions.
* Updated attention calculations and synchronization for selected GPU
architectures.
* **Tests**
* Expanded quantizer and scheduling coverage, including multi-stream
execution checks, and made GPU replay checks more repeatable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [d9fe063](https://github.com/flashinfer-ai/flashinfer/commit/d9fe063a68200764b1f5b0355cc0cd34c53ba6de)

- **作者**: eigen
- **时间**: 2026-10-29T15:06:42Z
- **提交信息**: perf(cake_kda): long M64 FP32-state launches of up to 36 tasks take an owner/helper build (#7866)

The Cake chunked KDA (Kimi Delta Attention) prefill behind
`flashinfer.recurrent_kda(..., backend="cake")` has 85 modules: 51 with
BF16 inputs and 34 with TF32 inputs. They come in a fused single-kernel
form (M128, M64 value split, N16 chain) and a split form (map prefix,
carry scan, affine apply), with FP32 or BF16 state and optional
checkpoint rows. This PR adds no module. It adds an owner/helper build
of the M64 value-split BF16-input FP32-state module, rendered as 2
programs: one for sm_100a and one for sm_103a. The rendered program
count goes from 58 to 60. In this build, helper CTAs prepare each chunk
once, and the two value-half owner CTAs of a task read the prepared
chunk. Outputs are bit-identical to the existing pair-share build.

On both GPUs, long M64 FP32-state launches take the owner/helper build
with two helper CTAs per task when they have at most 36 tasks and at
least 1024 tokens per task. If the cooperative launch is refused, the
launch falls back to the pair-share build. Other launches keep their
route and program.

The table covers the 3 cells of the 56-shape list where the rule changes
the program. All other shapes keep their program. On GB300, the 12-head
2x8192 shape takes another route and is unchanged.

| GPU | heads | gate lower bound | sequence lengths | main | this PR |
speedup |
|---|---:|---|---|---:|---:|---:|
| B200 | 12 | -5 | 2x8192 | 360.17 | 282.54 | 1.27x |
| B200 | 16 | -5 | 2x8192 | 366.52 | 285.76 | 1.28x |
| GB300 | 16 | -5 | 2x8192 | 343.44 | 273.54 | 1.26x |

B200: NVIDIA B200, sm_100a, 148 SMs. GB300: NVIDIA GB300, sm_103a, 152
SMs. CUDA 13.4.

Latency is in microseconds. It is the median per call over the run half
and the arm-swapped half of the timing pair, with BF16 q/k/v and FP32
recurrent state. "main" is the route FlashInfer main ships (the
pair-share M64 build), measured on the same build with the new rule off.
Speedup is main / this PR.

The rule also serves launch shapes outside the list. On B200, all 128
measured shapes are faster (1.12x to 1.32x). On GB300, 101 of 119 are
faster (1.12x to 1.28x, each confirmed on a second GPU node), and 18
launches have no verdict because the measurement drifted beyond the
noise bound in every attempt. None is slower on either GPU.

The kernel's other Cake variants are unchanged: the TF32-input modules
and the BF16-state forms. The family ships on sm_100a and sm_103a, and
this PR covers both.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an owner/helper execution schedule for eligible KDA prefill
workloads on supported GPUs, with automatic fallback to existing
schedules when cooperative launch is unavailable.
  * Added generated prefill routes for supported GPU architectures.

* **Bug Fixes**
* Improved handling of sequence-window ranking to keep each window’s
rank independent.

* **Tests**
* Added coverage for schedule selection, launch planning, result
consistency, and fallback behavior.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bd460fc](https://github.com/flashinfer-ai/flashinfer/commit/bd460fcb23c01cba946ec3ddf8468c836f6bd8e5)

- **作者**: Yang Xu
- **时间**: 2026-10-29T14:43:56Z
- **提交信息**: fix: correct Frost FP4 weight decoding in wide loads (#7845)

<!-- .github/pull_request_template.md -->

## 📌 Description

Native eight-value NVFP4/MXFP4 weight-only loads can produce incorrect
outputs, including FP16 tactics advertised on SM100. Decode the two
packed halfwords through explicit byte extraction in the wide path.
Four-value native conversion, Hopper software decoding, INT4 decoding,
scale rounding and tactic admission retain their existing behavior.
Extend the warm-cache/fresh-storage regression to FP16 using its typed
reference.

On main `9318fc8621f385ffd3d03861865b8947e8006d24`, all 24 wide
observations in a 32-observation NVFP4/MXFP4 × BF16/FP16 × load-width ×
live-mutation diagnostic failed; all eight four-value controls passed.
Twelve failures used advertised SM100 FP16 tactics. This is a
correctness repair, not a new tuning expansion.

## 🔍 Related Issues

Found while closing the Frost audit. Related: #7838 repairs the separate
MX-activation FFMA decoder and invalid-route contract; this PR fixes the
shared weight-only decoder and is independently based on main.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped `pre-commit run --files` passed for both changed files. The
all-files and hook-installation boxes are deliberately unchecked; those
commands were not run.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets: `tests/moe/test_frost_low_latency_fp4_wide.py
tests/moe/test_frost_low_latency_weight_only_fp16.py`

Final-source native validation: **156 passed, 4 Hopper-only architecture
skips, 0 failures**, including all advertised FP16 widths, live CUDA
Graph changes, invalid IDs/scores, activation tails, raw/finalized
outputs and fresh-storage cache binding. Source manifests were verified
before and after execution. The unchanged numerical tolerances and typed
FP16 reference are retained.

Environment: SM100, 148 SMs (inventory B100 SXM; runtime reports a
generic GPU name), driver 580.159.03, Torch 2.14.1+cu130, CuTe DSL 4.8.0
with actual compiler CUDA 12.9, isolated cuda-bindings 13.0.3. An
additional **16 CUDA 13.4 offline SM100a compilations** passed; these
are not CUDA 13 runtime qualification. The existing targeted native CI
has now completed successfully ([bot
result](https://github.com/flashinfer-ai/flashinfer/pull/7845#issuecomment-6498133443)).
Its synthetic integration source is
`94d3e6d954e05f9f95a06cb4a3578ff458d976d2`; all 47 relevant
API/kernel/test files and modes match this PR head
`297e84bfed37c73a38b30e144f9daea8f15074e5`. Required public checks also
pass.

Native regression command:
```bash
pytest -q tests/moe/test_frost_low_latency_fp4_wide.py tests/moe/test_frost_low_latency_weight_only_fp16.py -k 'fp4_wide or hopper_advertised or (advertised_widths and (nvfp4 or mxfp4)) or ((activations_live_graph or dtype_cache_and_outputs) and (nvfp4 or mxfp4))'
```

Bounded cost controls compare the same main with this final patch on
**correct four-value paths only**: SwiGLU, unpacked finalized output,
warm resident weights, fixed `("ffma", 2, 4)`, ordinary scales 2^-6,
shared first-k expert routes. Serial ABBA×4; each arm has eight blocks
of 40 CUDA-event samples with graph batch 64. Fixtures/references match
across arms; pre/post replay correctness and source hashes pass. The
table reports the median of block medians for the full
FC1/activation/FC2/combine call.

| T,H,I,E,k | Weight / activation | Main µs | Fix µs | Change |
|---|---|---:|---:|---:|
| 2,256,128,8,3 | nvfp4 / bf16 | 4.461 | 4.653 | +4.31% |
| 2,256,128,8,3 | nvfp4 / fp16 | 4.397 | 4.557 | +3.64% |
| 2,256,128,8,3 | mxfp4 / bf16 | 4.653 | 4.877 | +4.81% |
| 2,256,128,8,3 | mxfp4 / fp16 | 4.589 | 4.781 | +4.18% |
| 8,2048,512,16,4 | nvfp4 / bf16 | 30.173 | 30.369 | +0.65% |
| 8,2048,512,16,4 | nvfp4 / fp16 | 27.425 | 28.045 | +2.26% |
| 8,2048,512,16,4 | mxfp4 / bf16 | 32.253 | 32.429 | +0.55% |
| 8,2048,512,16,4 | mxfp4 / fp16 | 32.149 | 32.333 | +0.57% |

Observed block ranges overlap in all eight controls. Small cases still
show roughly 0.16–0.22 µs median differences, so this is not a universal
no-regression claim. Incorrect wide baseline outputs are excluded from
timing ratios. No complete-pool, preparation/communication, or serving
E2E result is claimed.

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

Please review native wide decode independence and typed rounding. Static
review confirms no pointer/shape/mask/synchronization changes; Hopper
software and INT4 helper ASTs are unchanged. Ready for independent
review after required public checks and targeted native CI completed.
Auto-merge remains disabled until the current head receives formal
approval. The separate extreme-E8M0-scale audit finding remains open.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved handling of packed FP4 weights in the native execution path.
* **Tests**
* Expanded FP4 cache-binding coverage to include FP16 activations
alongside BF16. Output checks now use format-appropriate references.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [f416759](https://github.com/flashinfer-ai/flashinfer/commit/f416759b9c97e40ad21ad6fa5b5534ac8b60d4ed)

- **作者**: Yang Xu
- **时间**: 2026-10-29T09:41:30Z
- **提交信息**: fix(moe): mask invalid Frost routes and repair MXFP4 FFMA decoding (#7838)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fix three correctness failures found while qualifying the existing Frost
low-latency MX/NVFP4 paths:

- MXFP8/MXFP4 finalization previously multiplied zero partials by
invalid-route NaN/Inf scores, contaminating output. Check live expert
IDs before reading and multiplying those scores in TC and FFMA
finalization.
- NVFP4 raw output left invalid-route rows unwritten. Write zero every
call so stale data cannot survive eager execution or CUDA Graph replay.
- The MXFP4 FFMA unrolled dot specialization produced incorrect
valid-route output with CuTeDSL 4.8.0 / CUDA 12.9. Decode each packed
byte explicitly through the existing FP4-to-FP16-to-FP32 helpers. The
observed adjacent-halfword low-pair reuse is reproduced;
compiler/library ownership is not yet established.

Document the bounded invalid-ID contract for MXFP8 activations with
MXFP8/MXFP4 weights and NVFP4/NVFP4. Raw routing scores are preserved
(including packed BF16 rounding), so downstream reducers must mask
invalid IDs before multiplication. Other format pairs still require
valid IDs. Public signatures/defaults and expert-parallel support are
unchanged.

Add reference regressions for both invalid bounds,
individual/all-invalid slots, NaN/Inf scores, poisoned output/scratch,
packed/unpacked routing, raw/finalized output, and route changes after
CUDA Graph capture. Each test checks every advertised tactic and
restores valid routes after invalid-route replay.

## 🔍 Related Issues

Related audit of the existing Frost paths. This patch targets main and
is separate from the grouped NVFP4 candidate expansion in #7384; it does
not qualify that PR's final integrated head.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Scoped `pre-commit run --files` passed on all eight changed files, along
with `git diff --check`. The all-files checkbox is intentionally
unchecked; unrelated files were not reformatted.

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
`tests/moe/test_frost_low_latency_invalid_routes.py
tests/moe/test_frost_low_latency.py
tests/moe/test_frost_low_latency_nvfp4.py`

Native SM100 validation on the main-integrated patch:

```bash
pytest -q tests/moe/test_frost_low_latency_invalid_routes.py \
  tests/moe/test_frost_low_latency.py::test_frost_graph_reference
```

- 32 passed, 0 failed/skipped: 24 new invalid-route cases plus 8
existing valid-route graph cases. Corrected regression on the frozen
pre-fix baseline had 8 pass / 16 fail; the intermediate masking-only fix
had 16 pass / 8 fail, exposing the MXFP4 decode issue. No tolerance
relaxation.
- Targeted Compute Sanitizer on three MXFP4/MXFP8/NVFP4 cases: zero
errors, exit 0, no suppressions. This was the prior frozen candidate;
repaired kernels and regression bytes are identical in the main
integration. An initial incompatible-binding run failed API probes;
isolated cuda-bindings 13.0.3 resolved that environment failure without
suppressions or shared-environment changes.
- CuTeDSL 4.8.0 / CUDA 13.4 offline compilation: 32 successful SM100a
specializations. This is compile evidence only. The completed native CI
below separately exercises the configured CUDA runtime matrix; the
actual DSL compiler version was not recorded by those CI jobs.
- Completed final-head CI: [public targeted run
40837839482](https://github.com/flashinfer-ai/flashinfer/actions/runs/40837839482)
succeeded on `31c7f9ba3b9b241ce2d9aae53f009b8906ccd17a`; required
summary and pre-commit checks pass. The [native CI
completion](https://github.com/flashinfer-ai/flashinfer/pull/7838#issuecomment-6492546634)
reports 29/29 executed test jobs passed. B200/cu129, cu130 and cu134
each have 60 passed / 2 skipped / 0 failed (JUnit verified). H100 has
only 4 host tests passed / 58 skipped and is not GPU qualification for
these routes. Native CI tested synthetic merge
`c19225e542f12d13684083aa263529e9b86a43a9`; all 48 relevant
API/Frost/test files match the PR head and CI source manifest. CI
harness SHA is distinct from the tested source. Manual lanes are not
counted as executed.
- 32 candidate full-call benchmark profiles passed pre/post-replay
reference checks. Four incorrect original MXFP4 FFMA profiles are
excluded from baseline timings. The other 28 baseline comparisons
completed.

Runtime environment: B100 SXM inventory, SM100 / 148 SM, driver
580.159.03, Torch 2.14.1+cu130, CuTeDSL 4.8.0 with actual DSL compiler
CUDA 12.9, cuda-bindings 13.0.3. This is not B200 performance evidence.

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

Current-head automated independent review completed without actionable
comments, and the requested public/native CI passed. This PR is Ready
for formal review; exact-head approval is still required and auto-merge
remains disabled. Please review the invalid-route contract and MXFP4
decode workaround in particular. This fixes correctness and is not a
claim of a faster candidate pool, new EP support, or serving E2E gains.
The separate extreme-scale audit item is not resolved by this patch.

The repair has an observable cost on some finalized MX TC paths: a
focused repeat measured about +0.10–0.48 us at T=1 and +0.14–0.30 us at
T=4. T=1 raw controls also fluctuate, so those percentages cannot all be
attributed to the mask. We are retaining the cost in the report rather
than claiming broad performance neutrality.

<details>
<summary>Bounded same-main full-call performance comparison</summary>

Both arms use main `1259b4427d89e5c9e4956ac5a641091d008dcfbc`, with only
this patch in the candidate. H=2048, I=512, E=32, top-k=4;
SwiGLU(alpha=1.7,beta=1,limit=7). PDL enabled for T=1. Fixed advertised
tactics; identical fixture/reference hashes, isolated source
imports/caches and serial ABBA blocks; no autotuning or competing GPU
jobs. Warm resident weights.

Timing uses `flashinfer.testing.bench_gpu_time` with explicit CUDA
events (`enable_cupti=False`, `use_cuda_graph=True`, `dry_run_iters=10`,
`repeat_iters=40`, `num_iters_within_graph=16`, `cold_l2_cache=False`).
Four ABBA rounds produce eight blocks per arm; report the median of
block medians. Includes routed FC1/activation/FC2/combine (or raw expert
output), excludes preparation, router network, communication, host
enqueue and serving. Output is reference-checked after timed replay.
These are small fixed-shape correctness-repair overhead measurements,
not a model-wide performance qualification.

| Format | T | Routing/output | Tactic | Before us | After us | Delta |
|---|---:|---|---|---:|---:|---:|
| mxfp8 | 1 | unpacked/final | 128 | 9.2680 | 9.7160 | +4.83% |
| mxfp8 | 1 | unpacked/final | 256 | 9.3320 | 9.4600 | +1.37% |
| mxfp8 | 1 | unpacked/final | ['ffma', 1] | 15.4760 | 15.6040 | +0.83%
|
| mxfp8 | 1 | packed/raw | 128 | 8.8795 | 9.0760 | +2.21% |
| mxfp8 | 1 | packed/raw | 256 | 8.8200 | 8.6920 | -1.45% |
| mxfp8 | 1 | packed/raw | ['ffma', 1] | 17.0760 | 16.9480 | -0.75% |
| mxfp8 | 4 | packed/final | 128 | 13.1255 | 13.3640 | +1.82% |
| mxfp8 | 4 | packed/final | 256 | 12.9805 | 13.2370 | +1.98% |
| mxfp8 | 4 | packed/final | ['ffma', 1] | 27.1880 | 27.2520 | +0.24% |
| mxfp8 | 4 | unpacked/raw | 128 | 12.7240 | 12.5960 | -1.01% |
| mxfp8 | 4 | unpacked/raw | 256 | 12.4680 | 12.3400 | -1.03% |
| mxfp8 | 4 | unpacked/raw | ['ffma', 1] | 28.9800 | 28.8520 | -0.44% |
| mxfp4 | 1 | unpacked/final | 128 | 9.2680 | 9.9080 | +6.91% |
| mxfp4 | 1 | unpacked/final | 256 | 9.2680 | 9.5880 | +3.45% |
| mxfp4 | 1 | unpacked/final | ['ffma', 1] | incorrect; excluded |
11.5720 | not defined |
| mxfp4 | 1 | packed/raw | 128 | 8.8840 | 9.2040 | +3.60% |
| mxfp4 | 1 | packed/raw | 256 | 8.8840 | 8.8200 | -0.72% |
| mxfp4 | 1 | packed/raw | ['ffma', 1] | incorrect; excluded | 12.7045 |
not defined |
| mxfp4 | 4 | packed/final | 128 | 12.9800 | 13.2360 | +1.97% |
| mxfp4 | 4 | packed/final | 256 | 12.7240 | 12.9800 | +2.01% |
| mxfp4 | 4 | packed/final | ['ffma', 1] | incorrect; excluded | 20.0520
| not defined |
| mxfp4 | 4 | unpacked/raw | 128 | 12.5960 | 12.5960 | +0.00% |
| mxfp4 | 4 | unpacked/raw | 256 | 12.3400 | 12.3400 | +0.00% |
| mxfp4 | 4 | unpacked/raw | ['ffma', 1] | incorrect; excluded | 21.3485
| not defined |
| nvfp4 | 1 | unpacked/final | ['nvfp4_ffma', 2] | 7.9880 | 8.1800 |
+2.40% |
| nvfp4 | 1 | unpacked/final | ['nvfp4_ffma', 4] | 9.3320 | 9.3320 |
+0.00% |
| nvfp4 | 1 | packed/raw | ['nvfp4_ffma', 2] | 9.5240 | 9.2680 | -2.69%
|
| nvfp4 | 1 | packed/raw | ['nvfp4_ffma', 4] | 10.8040 | 10.5480 |
-2.37% |
| nvfp4 | 4 | packed/final | ['nvfp4_ffma', 2] | 14.1320 | 14.3240 |
+1.36% |
| nvfp4 | 4 | packed/final | ['nvfp4_ffma', 4] | 13.1720 | 13.1720 |
+0.00% |
| nvfp4 | 4 | unpacked/raw | ['nvfp4_ffma', 2] | 15.6680 | 15.6680 |
+0.00% |
| nvfp4 | 4 | unpacked/raw | ['nvfp4_ffma', 4] | 14.5160 | 14.5160 |
+0.00% |

A separate timing-resolution check changes only the graph batch to 128
and checks both MX formats / TC tactics at T=1 finalized, T=1 raw
control and T=4 finalized. These measurements are not pooled with
batch16 or selected for the better result:

| Format | T | Routing/output | Tactic | Before us | After us | Delta |
|---|---:|---|---|---:|---:|---:|
| mxfp8 | 1 | unpacked/final | 128 | 9.1345 | 9.5875 | +4.96% |
| mxfp8 | 1 | unpacked/final | 256 | 9.1748 | 9.2705 | +1.04% |
| mxfp8 | 1 | packed/raw | 128 | 8.6705 | 8.8705 | +2.31% |
| mxfp8 | 1 | packed/raw | 256 | 8.6307 | 8.5385 | -1.07% |
| mxfp8 | 4 | packed/final | 128 | 12.9905 | 13.2065 | +1.66% |
| mxfp8 | 4 | packed/final | 256 | 12.8143 | 13.1184 | +2.37% |
| mxfp4 | 1 | unpacked/final | 128 | 9.1346 | 9.6166 | +5.28% |
| mxfp4 | 1 | unpacked/final | 256 | 9.0945 | 9.3305 | +2.59% |
| mxfp4 | 1 | packed/raw | 128 | 8.6385 | 8.9226 | +3.29% |
| mxfp4 | 1 | packed/raw | 256 | 8.5812 | 8.5346 | -0.54% |
| mxfp4 | 4 | packed/final | 128 | 12.8305 | 13.0065 | +1.37% |
| mxfp4 | 4 | packed/final | 256 | 12.5745 | 12.7185 | +1.15% |

The four original MXFP4 FFMA paths fail numerical checks, so no baseline
time or speedup is reported for them. All samples, block ranges,
fixture/source fingerprints and startup failures are retained in the
qualification artifacts. Two harness-only startup issues (missing einops
and hashing a scalar NVFP4 scale) were corrected without production
changes; already completed MX measurements were retained and only
missing NVFP4 measurement continued.

</details>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* For supported Frost MXFP8 and NVFP4 format combinations, out-of-range
expert IDs are treated as unrouted slots and do not contribute to
finalized output, even when their scores are NaN or infinite.
* In raw-output mode, unrouted expert rows are zeroed while route
mappings are preserved; scores retain their supplied values, with BF16
rounding in packed mode.
* **Documentation**
* Clarified which Frost format combinations support unrouted slots and
that other combinations or backends may require in-range expert IDs.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [82e9362](https://github.com/flashinfer-ai/flashinfer/commit/82e93625e87b196a9cb0d83fd5d85a29b8e7bdc7)

- **作者**: forrestl
- **时间**: 2026-10-29T09:10:38Z
- **提交信息**: perf(comm): accelerate portable Ulysses NVLink all-to-all (#7015)

<!-- .github/pull_request_template.md -->

## 📌 Description

The portable NVLink Ulysses path currently uses at most 36 CTAs,
scatters 8-byte-aligned rows with scalar copies, and stages gather
output through a second device copy. This change adds 8-byte
vectorization, a peer-partitioned 144-CTA path with aligned transfer
ranges, paired 16-byte stores for odd 8-byte row widths, and a gather
path that reads peer staging buffers into the final output. The raw API
retains its original single-signal-slot behavior; `UlyssesCommunicator`
allocates four separate slots for the faster path and exchanges each
rank's occupancy capacity to use a common safe CTA cap. Other shapes use
the existing portable fallback.

`nvlink_kernel="portable"` lets callers explicitly choose this
implementation when a Cake export is also available; `"cake"` forces
Cake, and the default `"auto"` preserves the existing architecture-based
route. The requested policy is checked across ranks during construction.

On one 8×H20 NVLink node, generic BF16 scatter shapes measured through
the public communicator API show:

| Shape `[B, S_local, H, D]` | Previous portable | This PR (`portable`)
| NCCL | Speedup vs NCCL |
| --- | ---: | ---: | ---: | ---: |
| `[1, 4096, 48, 34]` | 0.471 ms | 0.055 ms | 0.095 ms | 1.73× |
| `[1, 65536, 48, 66]` | 8.719 ms | 1.416 ms | 2.236 ms | 1.58× |

Across all six generic shapes (`S_local` 4096/16384/65536, `D` 34/66),
speedup over the NCCL backend is **1.56–1.73× for scatter** and
**1.45–1.58× for gather**. Times are medians of five trials of 50 calls,
using the maximum rank's CUDA-event time per trial; the NCCL path
includes the public API's pack/all-to-all/unpack. The benchmark checks
exact output before timing. Reproduce with `torchrun --standalone
--nproc_per_node=8 benchmarks/comm/bench_ulysses_a2a_vector.py --output
results.json --nvlink-kernel portable`. `--include-dir` accepts an
alternate include tree and rejects AOT artifacts that would bypass it.

## 🔍 Related Issues

None.

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
- [x] All tests are passing (`unittest`, etc.).

On one 8×H20 node, the full communicator suite passed (89 tests),
including mixed rank-alignment and mixed rank-capacity cases; the raw
API tests passed (3 tests). The public benchmark's output checks passed,
and a separate private workload validation passed 40/40 exact
correctness checks with repeated changing inputs after the capacity fix.
`python -m pre_commit run --files
benchmarks/comm/bench_ulysses_a2a_vector.py csrc/ulysses_all_to_all.cu
flashinfer/comm/ulysses.py
include/flashinfer/comm/ulysses_all_to_all.cuh
tests/comm/test_ulysses_communicator.py`: passed.

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

The fast path requires batch size one and an 8-byte-aligned row; other
inputs keep the original mover. All ranks choose the same
synchronization protocol from shape and communicator configuration and
use the minimum CTA capacity across the group; each rank can choose
scalar or vector transfers for its own operand alignment. The default
Cake route remains unchanged. After merging current upstream `main`, a
focused 8×H20 communicator/raw suite passed 26/26 cases. A full 8×H20
three-route validation passed exact output checks for every call; the
`auto` route used portable and remained faster than the NCCL backend
across all measured generic operation categories. Additional B200
measurements are kept out of this PR because their shapes are not part
of the public benchmark.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added NVLink kernel selection with automatic, portable, and Cake-only
options.
* Added configurable signal slots to the raw Ulysses all-to-all API; the
default retains one-slot behavior.
* Added a distributed benchmark for Ulysses scatter and gather
operations.
* **Performance**
* Improved Ulysses communication transfers for compatible 8-byte-aligned
data, while retaining fallback handling for other layouts.
* **Tests**
* Expanded coverage for additional tensor shapes, alignment scenarios,
and NVLink kernel selection across multiple rank configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8cc2453](https://github.com/flashinfer-ai/flashinfer/commit/8cc2453f0225464ef7c93b5b2fdc2a5e476af9d5)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-29T08:47:02Z
- **提交信息**: optimize-rubin-megamoe-decoding-perf (#7806)

<!-- .github/pull_request_template.md -->

## 📌 Description

1. Fuse routing validation into MXFP8 input quantization, preserving
checks while reducing kernel launches.
2. Write TopkReduce directly to aligned, contiguous caller output over
live tokens, eliminating the output copy and padded-row reduction.
3. Fuse routing tail masking into quantization, retaining separate-fill
fallbacks for empty batches and tails with insufficient parallelism.

8× Rubin, EP8, MXFP8×MXFP4, H4096/I2048/E256/top-k6, capacity256,
uniform routing. Full-call CUDA graph latency:

| Tokens | Without this PR (µs) | With this PR (µs) | Reduction |
DeepGEMM (µs) |
|---:|---:|---:|---:|---:|
| 32 | 146.0 | 136.4 | 6.6% | 135.9 |
| 192 | 156.9 | 141.5 | 9.8% | 143.0 |
| 256 | 158.0 | 143.8 | 9.0% | 145.7 |

Compared parent `04fc0358` with PR head `f9265928`; averages of two runs
per version on shared GPUs, without changing clock settings.

Validation: 441 related local tests and pre-commit passed.


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
* MoE inference can write results directly into compatible
caller-provided output buffers, including during graph replay.
* MXFP8 staging can handle trailing routing rows during quantization,
reducing the need for separate cleanup.
* **Bug Fixes**
* Routing checks detect out-of-range or duplicate expert IDs and invalid
scores in supported staging paths.
* Reusing a shared workspace with updated inputs now returns results for
the current inputs.
* **Documentation**
* Updated guidance describes routing validation, trailing-row handling,
and output-buffer behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [10bd87c](https://github.com/flashinfer-ai/flashinfer/commit/10bd87cec0365e790a1bb431d14e65e70836da5e)

- **作者**: eigen
- **时间**: 2026-10-29T08:31:26Z
- **提交信息**: feat(cake_mega_moe_v3): TP4/TP8 and EP-local rank routes for sm_103a (DeepSeek V4.1 Flash W4A8) (#7633)

`flashinfer.experimental.mega_moe_v3` runs the Cake MegaMoE v3 prepared
pipeline for the 384-expert, top-6, hidden-5120 model with activation
clamp 10. Each call is one kernel launch covering dispatch, FC1, clamped
SwiGLU, MXFP8 activation quantization, FC2 and weighted combine. With
this PR the kernel has four variants: the three already on main and the
tensor-parallel/expert-parallel rank variant this PR delivers. The rank
variant adds 32 routes (32 programs), one per shape below:
- TP4 EP1: 384 experts, physical intermediate width 640
- TP8 EP1: 384 experts, width 384
- TP4 EP4: 96 local experts per rank, intermediate 2304
- TP8 EP8: 48 local experts per rank, intermediate 2304

Each configuration runs at 1, 4, 16, 32, 128, 512, 1024 and 4096 tokens.
Routed weights are FP4 E2M1 with UE8M0 per-32 scales, and activations
are FP8 E4M3. The EP routes apply the local expert filter and produce
the rank's partial output, including local dispatch and weighted
combine. No previous Cake version ships these rank shapes, so the
baseline is FlashInfer's existing autotuned
`trtllm_fp4_block_scale_routed_moe` at the same shapes, inputs,
precision and timing scope. Both sides include local dispatch and
combine. Both exclude input preparation, input quantization, routing and
inter-rank communication. Speedup is baseline latency divided by
`mega_moe_v3` latency, so a value above 1 means `mega_moe_v3` is faster.
Results:
- `mega_moe_v3` is faster than the baseline on all 32 shapes, from
1.012x to 1.160x in the table below.
- Two independent replicates, each run alone on the node, were both
faster on every one of the 32 shapes. The table reports the first
replicate. The second replicate ranged from 1.012x to 1.161x.

*Per-call latency on NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4 toolkit,
driver 580.159.03, PyTorch 2.14.1+cu130. CUDA-graph replays, paired
interleaved arms, median of 21 rounds. Speedup = baseline µs /
`mega_moe_v3` µs.*

| Case | Tokens | Baseline `trtllm_fp4_block_scale_routed_moe` (µs) |
`mega_moe_v3` (µs) | Speedup |
|---|---:|---:|---:|---:|
| TP4 EP1 (I=640) | 1 | 14.31 | 13.72 | 1.044 |
| TP4 EP1 (I=640) | 4 | 30.33 | 26.15 | 1.160 |
| TP4 EP1 (I=640) | 16 | 88.47 | 81.85 | 1.081 |
| TP4 EP1 (I=640) | 32 | 160.73 | 152.82 | 1.052 |
| TP4 EP1 (I=640) | 128 | 310.18 | 300.16 | 1.033 |
| TP4 EP1 (I=640) | 512 | 319.90 | 311.02 | 1.029 |
| TP4 EP1 (I=640) | 1024 | 337.28 | 332.07 | 1.016 |
| TP4 EP1 (I=640) | 4096 | 444.96 | 439.70 | 1.012 |
| TP8 EP1 (I=384) | 1 | 13.40 | 12.21 | 1.097 |
| TP8 EP1 (I=384) | 4 | 18.71 | 18.23 | 1.027 |
| TP8 EP1 (I=384) | 16 | 57.60 | 53.65 | 1.074 |
| TP8 EP1 (I=384) | 32 | 105.96 | 96.46 | 1.099 |
| TP8 EP1 (I=384) | 128 | 202.58 | 189.67 | 1.068 |
| TP8 EP1 (I=384) | 512 | 214.73 | 199.37 | 1.077 |
| TP8 EP1 (I=384) | 1024 | 229.54 | 213.84 | 1.073 |
| TP8 EP1 (I=384) | 4096 | 320.59 | 315.82 | 1.015 |
| TP4 EP4 (96 local experts) | 1 | 15.40 | 14.31 | 1.076 |
| TP4 EP4 (96 local experts) | 4 | 26.25 | 24.11 | 1.089 |
| TP4 EP4 (96 local experts) | 16 | 76.79 | 72.85 | 1.054 |
| TP4 EP4 (96 local experts) | 32 | 143.21 | 140.10 | 1.022 |
| TP4 EP4 (96 local experts) | 128 | 273.98 | 268.65 | 1.020 |
| TP4 EP4 (96 local experts) | 512 | 280.41 | 275.49 | 1.018 |
| TP4 EP4 (96 local experts) | 1024 | 288.57 | 282.43 | 1.022 |
| TP4 EP4 (96 local experts) | 4096 | 367.41 | 347.36 | 1.058 |
| TP8 EP8 (48 local experts) | 1 | 14.19 | 12.97 | 1.093 |
| TP8 EP8 (48 local experts) | 4 | 16.24 | 15.92 | 1.020 |
| TP8 EP8 (48 local experts) | 16 | 44.76 | 39.36 | 1.137 |
| TP8 EP8 (48 local experts) | 32 | 79.96 | 75.82 | 1.055 |
| TP8 EP8 (48 local experts) | 128 | 147.39 | 142.51 | 1.034 |
| TP8 EP8 (48 local experts) | 512 | 151.92 | 147.22 | 1.032 |
| TP8 EP8 (48 local experts) | 1024 | 160.98 | 146.68 | 1.097 |
| TP8 EP8 (48 local experts) | 4096 | 209.12 | 195.34 | 1.071 |

The other three Cake variants on main ship on sm_100a and sm_103a, with
10 routes and 13 programs in total: the single-rank routed-FP4 pipeline
(intermediate 2304; 1, 16, 128, 512, 1024 and 4096 tokens), the
single-rank routed-FP8 pipeline (16 tokens) and the grouped-GEMM routes
(`grouped_fused`, `grouped_l1`, `grouped_l2`); the rank variant added
here ships on sm_103a only, so the routes table becomes
per-architecture.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added support for tensor- and expert-parallel MegaMoE routes,
including rank-specific expert windows and global routing IDs.
- Added logical-width padding for intermediate dimensions and expanded
route handling across supported device architectures and SM counts.
- Added configurable control-buffer allocation modes and support for
activation-backed inputs in eligible routes.

- **Documentation**
- Updated MegaMoE guidance with supported shapes, routing behavior,
padding, control-buffer options, and test coverage.

- **Tests**
- Expanded coverage for parallel routes, padding equivalence, replay
behavior, workspace reuse, and preparation contracts.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [9318fc8](https://github.com/flashinfer-ai/flashinfer/commit/9318fc8621f385ffd3d03861865b8947e8006d24)

- **作者**: eigen
- **时间**: 2026-10-29T07:16:09Z
- **提交信息**: perf(cake_tinygemm2_tcgen05): build PACKED_M64_N8 for sm_100a/sm_103a and add unbiased routing windows (#7826)

`cake_tinygemm2_tcgen05` is the Cake backend of
`flashinfer.gemm.tinygemm_bf16`, which computes BF16 `out = input @
weight.T (+ bias)` for small batches. It supports only BF16. It contains
36 generated tcgen05 programs: nine tiles, each built with and without
bias and with and without PDL. #7302 added the backend, and #7370
unrolled its narrow tile and retuned its windows. #7519 added the
swap-AB per-chain-accumulator tile, early tensor-memory free, two M=64
packed tiles and retuned windows. #7588 promoted the sm_107a narrow
tile's tensor maps to L2 256 B and sent 17-23-row unbiased GEMMs with
small activations to the packed tile on sm_107a. #7656 added
PACKED_BOX8, the packed tile with an 8-row activation box and 8 batch
rows per CTA. #7735 added PACKED_M64_N8, an M=64 tile that computes 16
output features and 8 batch rows per CTA with an exact 8-row activation
box, built for sm_107a only, and widened the sm_107a windows for 8-row
unbiased GEMMs. This PR builds PACKED_M64_N8 for sm_100a and sm_103a as
well. Its four programs (bias x PDL) are regenerated with an
sm_100a/sm_103a code path, and their sm_107a machine code is unchanged.
No program is added or removed, and the other 32 programs are
regenerated unchanged.

The PR also adds routing windows for unbiased GEMMs only: 9 on sm_100a
(B200), 10 on sm_103a (GB300) and 6 on sm_107a (R200). They route
measured shapes with 1-8 rows (B200, GB300) or 4-8 rows (R200),
3584-16384 output features and K 2048-16384 to PACKED_M64_N8 or
PACKED_BOX8, and, on R200 only, 4-row shapes to the existing
PACKED_M64_N4 tile. Some windows apply only when K is a multiple of 64.
Routing with a bias does not change, shapes outside the new windows keep
their current kernel, and outputs stay bit-for-bit equal to FlashInfer's
`csrc/tinygemm2.cu`. The baseline is what `tinygemm_bf16` runs on
FlashInfer main today: the reference `tinygemm2` kernel in every
rerouted case, and `tinygemm2_sm100` (with bias) or the reference kernel
(without bias) for any shape main does not route to Cake. Per-case
speedup is baseline median / Cake median, each median over 3 runs on 3
GPUs. The new routing is 1.04-1.35x faster than main on B200 (122
measured unbiased cases, 120 shapes; 27 with PDL on, 95 with PDL off),
1.03-1.38x on GB300 (159 cases, 155 shapes; 32 with PDL on, 127 with PDL
off) and 1.05-1.50x on R200 (271 cases, 175 shapes; 96 with PDL on, 175
with PDL off).

The per-GPU tables below show CUPTI kernel times in µs for 16 shapes
(batch x out x K), with and without bias, PDL off, cold L2; each time is
the median over 3 runs on 3 GPUs of that product. None of these 16
shapes changes kernel on any GPU, so each row runs the same kernel on
both sides and the 0.99x-1.02x ratios are noise. A † marks rows that
neither side routes to a Cake program, so both columns time the same
FlashInfer kernel. A ‡ marks rows where both sides run the same Cake
program, and this PR does not change that program's machine code.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.90 / 2.90 | 1.00x † | 3.04 / 3.04 | 1.00x † |
| 1 x 128 x 14336 | 6.37 / 6.38 | 1.00x ‡ | 6.35 / 6.37 | 1.00x ‡ |
| 2 x 16 x 256 | 2.83 / 2.85 | 0.99x † | 2.96 / 2.96 | 1.00x † |
| 4 x 2880 x 2880 | 6.75 / 6.75 | 1.00x † | 7.14 / 7.14 | 1.00x ‡ |
| 7 x 128 x 4096 | 3.97 / 3.94 | 1.01x ‡ | 3.94 / 3.97 | 0.99x ‡ |
| 8 x 128 x 7168 | 4.64 / 4.64 | 1.00x ‡ | 4.64 / 4.64 | 1.00x ‡ |
| 8 x 1024 x 1024 | 3.10 / 3.10 | 1.00x † | 3.23 / 3.23 | 1.00x † |
| 13 x 1024 x 2048 | 4.00 / 4.00 | 1.00x † | 4.10 / 4.10 | 1.00x † |
| 16 x 2880 x 2880 | 7.17 / 7.17 | 1.00x ‡ | 7.18 / 7.20 | 1.00x ‡ |
| 64 x 4096 x 3072 | 9.09 / 9.09 | 1.00x ‡ | 8.96 / 8.96 | 1.00x ‡ |
| 16 x 1024 x 1024 | 3.07 / 3.07 | 1.00x † | 3.17 / 3.17 | 1.00x † |
| 8 x 2048 x 2048 | 4.80 / 4.82 | 1.00x † | 4.83 / 4.83 | 1.00x † |
| 8 x 4096 x 4096 | 9.63 / 9.63 | 1.00x † | 10.06 / 10.05 | 1.00x ‡ |
| 16 x 4096 x 3072 | 8.38 / 8.38 | 1.00x ‡ | 8.35 / 8.35 | 1.00x ‡ |
| 64 x 4096 x 4096 | 11.84 / 11.87 | 1.00x ‡ | 11.36 / 11.36 | 1.00x ‡ |
| 4 x 128 x 256 | 2.74 / 2.75 | 0.99x † | 2.94 / 2.93 | 1.01x † |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.64 / 2.66 | 0.99x † | 2.78 / 2.78 | 1.00x † |
| 1 x 128 x 14336 | 6.11 / 6.11 | 1.00x ‡ | 6.08 / 6.11 | 0.99x ‡ |
| 2 x 16 x 256 | 2.50 / 2.45 | 1.02x † | 2.69 / 2.69 | 1.00x † |
| 4 x 2880 x 2880 | 6.54 / 6.53 | 1.00x † | 6.94 / 6.94 | 1.00x ‡ |
| 7 x 128 x 4096 | 3.74 / 3.74 | 1.00x ‡ | 3.71 / 3.70 | 1.00x ‡ |
| 8 x 128 x 7168 | 4.45 / 4.45 | 1.00x ‡ | 4.42 / 4.42 | 1.00x ‡ |
| 8 x 1024 x 1024 | 2.91 / 2.91 | 1.00x † | 3.04 / 3.04 | 1.00x † |
| 13 x 1024 x 2048 | 3.90 / 3.90 | 1.00x † | 4.10 / 4.10 | 1.00x † |
| 16 x 2880 x 2880 | 6.94 / 6.94 | 1.00x ‡ | 6.88 / 6.88 | 1.00x ‡ |
| 64 x 4096 x 3072 | 8.77 / 8.77 | 1.00x ‡ | 8.74 / 8.74 | 1.00x ‡ |
| 16 x 1024 x 1024 | 3.01 / 3.01 | 1.00x † | 3.07 / 3.07 | 1.00x † |
| 8 x 2048 x 2048 | 4.58 / 4.58 | 1.00x † | 4.70 / 4.70 | 1.00x † |
| 8 x 4096 x 4096 | 9.12 / 9.12 | 1.00x † | 9.41 / 9.41 | 1.00x ‡ |
| 16 x 4096 x 3072 | 7.97 / 7.97 | 1.00x ‡ | 7.97 / 7.97 | 1.00x ‡ |
| 64 x 4096 x 4096 | 10.43 / 10.46 | 1.00x ‡ | 10.37 / 10.37 | 1.00x ‡ |
| 4 x 128 x 256 | 2.46 / 2.46 | 1.00x † | 2.69 / 2.66 | 1.01x † |

**NVIDIA R200 (sm_107a, 212 SMs), CUDA 13.4, PyTorch 2.14.1+cu130**

| batch x out x K | with bias: baseline / Cake (µs) | speedup | without
bias: baseline / Cake (µs) | speedup |
| --- | --- | --- | --- | --- |
| 1 x 128 x 720 | 2.56 / 2.53 | 1.01x † | 2.66 / 2.66 | 1.00x † |
| 1 x 128 x 14336 | 5.25 / 5.22 | 1.01x ‡ | 5.25 / 5.25 | 1.00x ‡ |
| 2 x 16 x 256 | 2.24 / 2.24 | 1.00x † | 2.42 / 2.43 | 0.99x † |
| 4 x 2880 x 2880 | 4.51 / 4.51 | 1.00x ‡ | 4.54 / 4.51 | 1.01x ‡ |
| 7 x 128 x 4096 | 3.42 / 3.42 | 1.00x ‡ | 3.39 / 3.39 | 1.00x ‡ |
| 8 x 128 x 7168 | 4.02 / 4.00 | 1.00x ‡ | 4.00 / 4.00 | 1.00x ‡ |
| 8 x 1024 x 1024 | 2.72 / 2.72 | 1.00x † | 2.85 / 2.85 | 1.00x † |
| 13 x 1024 x 2048 | 3.14 / 3.14 | 1.00x † | 3.30 / 3.30 | 1.00x † |
| 16 x 2880 x 2880 | 4.77 / 4.74 | 1.01x ‡ | 4.80 / 4.77 | 1.01x ‡ |
| 64 x 4096 x 3072 | 6.64 / 6.62 | 1.00x ‡ | 6.62 / 6.59 | 1.00x ‡ |
| 16 x 1024 x 1024 | 2.66 / 2.66 | 1.00x † | 2.78 / 2.78 | 1.00x † |
| 8 x 2048 x 2048 | 3.49 / 3.49 | 1.00x † | 3.65 / 3.65 | 1.00x † |
| 8 x 4096 x 4096 | 5.86 / 5.86 | 1.00x † | 5.98 / 5.98 | 1.00x ‡ |
| 16 x 4096 x 3072 | 5.60 / 5.60 | 1.00x ‡ | 5.63 / 5.63 | 1.00x ‡ |
| 64 x 4096 x 4096 | 7.62 / 7.62 | 1.00x ‡ | 7.55 / 7.55 | 1.00x ‡ |
| 4 x 128 x 256 | 2.46 / 2.43 | 1.01x † | 2.59 / 2.59 | 1.00x † |

The window table has one row per new window, per GPU, in routing order:
the batch, output-feature and K ranges ("multiple of 64" where
required), the Cake tile, the measured cases it serves (PDL-on count in
parentheses), their speedup range, and the baseline / Cake times of the
cases with the smallest and largest speedup. A shape uses the first
window that admits it, so a later window serves only shapes that earlier
ones do not take, and each case is counted once. A ¹ on an output range
marks windows that apply only while PACKED's grid, ceil(out / 32) x
ceil(batch / 16) CTAs, fits in one wave (at most the GPU's SM count).
Times are measured as in the tables above, and "PDL" after a shape marks
a PDL-on case.

| GPU | batch | out | K | tile | cases (PDL on) | speedup | slowest
gain: baseline / Cake (µs) | fastest gain: baseline / Cake (µs) |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| B200 | 1-7 | 4480-4608 | 2048-8192 | PACKED_BOX8 | 23 (2) | 1.07-1.30x
| 6x4608x8192: 19.62 / 18.34 | 5x4496x2056: 9.86 / 7.58 |
| B200 | 1-7 | 3584-4608 | 6152-8192 | PACKED_BOX8 | 8 (3) | 1.07-1.16x
| 4x4224x8000: 18.56 / 17.31 | 1x3584x6152: 15.01 / 12.99 |
| B200 | 8 | 8192 | 2048-8192, multiple of 64 | PACKED_M64_N8 | 15 (5) |
1.08-1.34x | 8x8192x8128: 33.15 / 30.81 | 8x8192x2048 PDL: 13.66 / 10.18
|
| B200 | 1-7 | 8192 | 2048-8192, multiple of 64 | PACKED_M64_N8 | 22 (3)
| 1.07-1.35x | 6x8192x7680 PDL: 32.13 / 29.89 | 7x8192x2048: 13.66 /
10.14 |
| B200 | 8 | 8192 | 2048-8192 | PACKED_BOX8 | 11 (3) | 1.10-1.34x |
8x8192x8136: 37.09 / 33.76 | 8x8192x2056 PDL: 17.31 / 12.93 |
| B200 | 1-7 | 8192 | 2048-8192 | PACKED_BOX8 | 7 (3) | 1.10-1.33x |
7x8192x8136 PDL: 37.06 / 33.70 | 1x8192x2056: 16.32 / 12.29 |
| B200 | 1-7 | 4480-8192 | 2048-6152 | PACKED_M64_N8 | 18 (3) |
1.04-1.30x | 6x4864x3072 PDL: 11.33 / 10.88 | 3x8000x2056: 16.22 / 12.51
|
| B200 | 1-7 | 7000-8192 | 2048-8192, multiple of 64 | PACKED_M64_N8 | 4
(2) | 1.08-1.11x | 3x7680x7168 PDL: 28.11 / 26.08 | 2x8000x6656: 28.64 /
25.78 |
| B200 | 8 | 12288 | 2048-16384, multiple of 64 | PACKED_M64_N8 | 14 (3)
| 1.04-1.35x | 8x12288x16320: 78.43 / 75.39 | 8x12288x2048: 18.30 /
13.54 |
| GB300 | 8 | 4480-4608 | 2048-12288 | PACKED_BOX8 | 25 (5) | 1.05-1.28x
| 8x4608x12224: 26.27 / 24.99 | 8x4608x2104: 9.98 / 7.78 |
| GB300 | 8 | 8192 | 2048-8192, multiple of 64 | PACKED_M64_N8 | 15 (5)
| 1.10-1.33x | 8x8192x8192: 31.87 / 28.99 | 8x8192x2048: 13.28 / 10.02 |
| GB300 | 1-7 | 8192 | 2048-8192, multiple of 64 | PACKED_M64_N8 | 22
(3) | 1.09-1.34x | 1x8192x8192: 31.62 / 29.06 | 6x8192x2048: 13.54 /
10.08 |
| GB300 | 8 | 8192 | 2048-8192 | PACKED_BOX8 | 11 (3) | 1.10-1.35x |
8x8192x8184: 36.54 / 33.26 | 8x8192x2056 PDL: 16.74 / 12.35 |
| GB300 | 1-7 | 8192 | 2048-8192 | PACKED_BOX8 | 7 (3) | 1.10-1.29x |
7x8192x8136 PDL: 36.16 / 32.99 | 1x8192x2056: 15.23 / 11.81 |
| GB300 | 8 | 4480-16384 | 2048-6152, multiple of 64 | PACKED_M64_N8 |
44 (3) | 1.03-1.38x | 8x6656x5120 PDL: 18.85 / 18.24 | 8x16384x2048:
23.62 / 17.15 |
| GB300 | 1-7 | 4609-8192 | 2048-6152 | PACKED_M64_N8 | 18 (3) |
1.06-1.28x | 5x5120x6152: 21.63 / 20.48 | 3x8000x2056: 15.87 / 12.45 |
| GB300 | 8 | 8192 | 2048-12288, multiple of 64 | PACKED_M64_N8 | 5 (2)
| 1.06-1.12x | 8x8192x12224: 44.32 / 41.82 | 8x8192x8256 PDL: 34.50 /
30.78 |
| GB300 | 8 | 12288 | 2048-12288, multiple of 64 | PACKED_M64_N8 | 7 (3)
| 1.04-1.09x | 8x12288x12224: 61.62 / 59.47 | 8x12288x8256 PDL: 47.52 /
43.52 |
| GB300 | 8 | 3584 | 12289-16384, multiple of 64 | PACKED_M64_N8 | 5 (2)
| 1.04-1.10x | 8x3584x16384: 29.12 / 28.10 | 8x3584x13312 PDL: 24.13 /
21.86 |
| R200 | 8 | 4097-6143 | 2561-8192, multiple of 64 | PACKED_M64_N8 | 76
(24) | 1.11-1.26x | 8x6128x6656 PDL: 11.71 / 10.53 | 8x4224x3584: 7.55 /
5.98 |
| R200 | 8 | 3584-6784 ¹ | 2056-2560 | PACKED_BOX8 | 50 (17) |
1.12-1.50x | 8x5904x2432 PDL: 7.20 / 6.40 | 8x3584x2056: 7.20 / 4.80 |
| R200 | 8 | 6144-6784 | 2561-3071, multiple of 64 | PACKED_M64_N8 | 17
(8) | 1.15-1.20x | 8x6160x2624: 7.36 / 6.40 | 8x6768x3008: 8.00 / 6.66 |
| R200 | 8 | 3584-6784 ¹ | 2561-8184 | PACKED_BOX8 | 82 (29) |
1.07-1.36x | 8x6784x8184 PDL: 14.66 / 13.70 | 8x3600x6152 PDL: 11.23 /
8.29 |
| R200 | 4 | 4097-6144 | 3072-6144, multiple of 64 | PACKED_M64_N4 | 26
(10) | 1.05-1.25x | 4x5120x6144 PDL: 11.46 / 10.88 | 4x6128x3136: 10.32
/ 8.26 |
| R200 | 4-5 | 3584-4608 | 2048 | PACKED_M64_N8 | 20 (8) | 1.07-1.21x |
4x4592x2048 PDL: 6.90 / 6.43 | 4x3584x2048: 6.18 / 5.10 |

Cake has no other data type, layout or fused form of this kernel,
`tinygemm2_sm100` remains the with-bias path outside the windows, and
the family covers sm_100a, sm_103a and sm_107a (B200, GB300 and R200
class GPUs), with every tile, PACKED_M64_N8 included, now built for all
three.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for additional optimized tiny GEMM tile configurations
on SM100 and SM103 GPUs, alongside SM107.
* Expanded shape and dimension ranges that can use optimized tile
selections across supported architectures.

* **Improvements**
* Updated architecture-specific GPU execution settings to better match
each supported device.
* Added coverage for routing choices across a wider range of shapes,
bias settings, and aligned or unaligned dimensions.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e7a17d2](https://github.com/flashinfer-ai/flashinfer/commit/e7a17d27f531025539d1d33aeb5d1071e1c9aadc)

- **作者**: eigen
- **时间**: 2026-10-29T07:13:34Z
- **提交信息**: perf(cake_kimi_k3_fused_router): up to 1.10x faster routing on B200 and GB300 (#7824)

`flashinfer.fused_moe.kimi_k3_fused_router` is FlashInfer's experimental
Kimi-K3 fused MoE router. It takes FP32 gate logits and an FP32 bias
(896 experts, top-16) and, in one launch, selects the top-16 experts per
token and builds the expert-aligned route plan (the
`moe_align_block_size` layout) that grouped MoE GEMMs consume. The
router has one variant: FP32 logits and bias with `block_m` 8 and 16.
This PR covers it on sm_100a and sm_103a. The API is unchanged, and the
outputs are exact on every measured cell. On both architectures, `Q4S`,
`Q4S_E16`, `Q4SB` and `Q4SB_LBW` keep each cluster's slice byte map in
their owner CTAs, so they launch up to 1024 tokens (`Q4SB_LBW`: 1150).
`GW`, the program of the 4096- and 8192-token cells, gets a new kernel
body on both architectures, and the 256-token program `M` gets one on
sm_103a. On sm_100a above device capacity, `Q4SB` (`Q4S` with a next-row
prefetch) now runs up to 832 tokens at `block_m` 8 and up to 1024 tokens
at `block_m` 16. At `block_m` 16, `Q4SB_LBW` (`Q4SB` with a slice byte
map spanning a full map row) runs from 1025 to 1136 tokens and `Q4SP_LR`
from 1137. Also on sm_100a, `Q4S_E16` and `Q4SP_PG` take their candidate
floor from the owners of the published bounds. The 32-token cell at
`block_m` 16 runs `LCG_LW_OWN`, the `LCG_LW` kernel with that floor,
from 29 tokens, while sm_103a keeps `LCG_LW` there. "FlashInfer main" in
the tables is the previous Cake version of this kernel, which means the
router programs FlashInfer main ships today (from #7748). On B200,
latency at 512 tokens drops from 7.840 us to 7.104 us at `block_m` 8 and
to 7.152 us at `block_m` 16 (1.10x each), and at 1024 tokens with
`block_m` 16 from 10.272 us to 9.536 us (1.08x). On GB300, it drops from
9.472 us to 8.864 us at 1024 tokens with `block_m` 16 and from 7.552 us
to 7.072 us at 512 tokens with `block_m` 8 (1.07x each). On the changed
cells the speedup ranges from 1.01x to 1.10x on B200 and from 1.01x to
1.07x on GB300.

NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.4, median kernel latency per
cell (28 cells); speedup = FlashInfer main / this PR; `new` marks the 9
cells whose device program this PR changes, and ratios on `same` cells
are measurement noise, not speedups.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.792 | 2.815 | 0.99x | same |
| 1 | 16 | 2.720 | 2.720 | 1.00x | same |
| 2 | 8 | 3.200 | 3.391 | 0.94x | same |
| 2 | 16 | 3.343 | 3.345 | 1.00x | same |
| 4 | 8 | 2.991 | 3.008 | 0.99x | same |
| 4 | 16 | 3.168 | 3.168 | 1.00x | same |
| 8 | 8 | 3.104 | 3.120 | 0.99x | same |
| 8 | 16 | 3.216 | 3.232 | 0.99x | same |
| 16 | 8 | 3.168 | 3.200 | 0.99x | same |
| 16 | 16 | 3.296 | 3.296 | 1.00x | same |
| 32 | 8 | 3.535 | 3.520 | 1.00x | same |
| 32 | 16 | 3.583 | 3.520 | 1.02x | new |
| 64 | 8 | 5.104 | 5.104 | 1.00x | same |
| 64 | 16 | 5.120 | 5.152 | 0.99x | same |
| 128 | 8 | 5.440 | 5.472 | 0.99x | same |
| 128 | 16 | 5.536 | 5.472 | 1.01x | same |
| 256 | 8 | 5.696 | 5.729 | 0.99x | same |
| 256 | 16 | 5.744 | 5.760 | 1.00x | same |
| 512 | 8 | 7.840 | 7.104 | 1.10x | new |
| 512 | 16 | 7.840 | 7.152 | 1.10x | new |
| 1024 | 8 | 10.160 | 9.680 | 1.05x | new |
| 1024 | 16 | 10.272 | 9.536 | 1.08x | new |
| 2048 | 8 | 12.448 | 12.576 | 0.99x | same |
| 2048 | 16 | 12.320 | 12.608 | 0.98x | same |
| 4096 | 8 | 17.408 | 17.232 | 1.01x | new |
| 4096 | 16 | 17.471 | 17.200 | 1.02x | new |
| 8192 | 8 | 23.168 | 22.944 | 1.01x | new |
| 8192 | 16 | 23.232 | 23.056 | 1.01x | new |

NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.4, median kernel latency per
cell (28 cells); speedup = FlashInfer main / this PR; `new` marks the 10
cells whose device program this PR changes, and ratios on `same` cells
are measurement noise, not speedups.

| tokens | block_m | FlashInfer main (us) | this PR (us) | speedup |
kernel |
|---:|---:|---:|---:|---:|---|
| 1 | 8 | 2.720 | 2.672 | 1.02x | same |
| 1 | 16 | 2.656 | 2.624 | 1.01x | same |
| 2 | 8 | 3.264 | 3.104 | 1.05x | same |
| 2 | 16 | 3.040 | 3.024 | 1.01x | same |
| 4 | 8 | 3.104 | 3.104 | 1.00x | same |
| 4 | 16 | 3.232 | 3.232 | 1.00x | same |
| 8 | 8 | 3.008 | 3.008 | 1.00x | same |
| 8 | 16 | 2.976 | 2.976 | 1.00x | same |
| 16 | 8 | 3.264 | 3.264 | 1.00x | same |
| 16 | 16 | 3.040 | 3.008 | 1.01x | same |
| 32 | 8 | 3.392 | 3.376 | 1.00x | same |
| 32 | 16 | 3.360 | 3.392 | 0.99x | same |
| 64 | 8 | 4.992 | 4.992 | 1.00x | same |
| 64 | 16 | 4.928 | 4.896 | 1.01x | same |
| 128 | 8 | 5.312 | 5.344 | 0.99x | same |
| 128 | 16 | 5.376 | 5.360 | 1.00x | same |
| 256 | 8 | 5.664 | 5.568 | 1.02x | new |
| 256 | 16 | 5.712 | 5.664 | 1.01x | new |
| 512 | 8 | 7.552 | 7.072 | 1.07x | new |
| 512 | 16 | 7.488 | 7.008 | 1.07x | new |
| 1024 | 8 | 9.472 | 8.928 | 1.06x | new |
| 1024 | 16 | 9.472 | 8.864 | 1.07x | new |
| 2048 | 8 | 11.808 | 11.904 | 0.99x | same |
| 2048 | 16 | 11.648 | 11.792 | 0.99x | same |
| 4096 | 8 | 16.688 | 16.512 | 1.01x | new |
| 4096 | 16 | 16.704 | 16.576 | 1.01x | new |
| 8192 | 8 | 22.272 | 21.888 | 1.02x | new |
| 8192 | 16 | 22.336 | 21.632 | 1.03x | new |

Cake ships no other data type, layout or fused form of this router, and
the family ships on sm_100a and sm_103a only, so these two tables cover
all of its variants and architectures.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added Kimi K3 routing options for additional GPU architectures and
batch sizes, including support for up to 1,150 tokens in selected
configurations.
* Expanded routing and sorting coverage across small and large batches.
* **Bug Fixes**
  * Improved top-expert selection and tie handling.
  * Updated validation to reject unsupported batch sizes.
* **Tests**
* Expanded coverage for routing choices, batch-size boundaries, and
launch limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [4bddce5](https://github.com/flashinfer-ai/flashinfer/commit/4bddce58c377095932aa6be3fb605fd10737a8fc)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-29T07:11:08Z
- **提交信息**: fix(gdn): index the ReplaySSM commit checkpoint by Int64 flat slot (#6496)

<!-- .github/pull_request_template.md -->

## 📌 Description

Both ReplaySSM commit folds (`gdn_replayssm_spec_fold.py` and
`gdn_replayssm_spec_fold_tcgen.py`) address the all-layer checkpoint
through a flattened `[layers * slots, HV, V, K]` view and compute the
flat slot index in Int32. The element offset `flat_slot * HV * V * K`
overflows once `layers * slots * HV * V * K` passes 2^31 elements, and
the fold then reads and writes an illegal address. A 36-layer model with
a 1036-slot fp32 pool reaches that at HV = 8 (4.9e9 elements);
Qwen3-Next at tp=4 on B200 in SGLang faults on its first commit, while
tp=1 pools of 65 to 105 slots never cross the boundary, which is why it
went unnoticed.

The fix computes `flat_slot` (and the track slot) as `cutlass.Int64` in
both kernels. Below the boundary the behaviour is unchanged.

Bisected standalone on B200 before the fix: 36 layers x 400 slots x HV 8
(1.9e9 elements) passes on both backends; 36 x 700 (3.3e9) and 36 x 1036
(4.9e9) fault on both. After the fix all five pass.

## 🔍 Related Issues

Pre-existing since #5314. Found while running the SGLang integration of
#6155 / #6257 at tp=4; independent of both.

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

`test_replayssm_commit_pool_beyond_int32_elements[simt|tcgen05]` in
`tests/gdn/test_replayssm_spec_fold.py` allocates a 70 x 1000 x 2 x 128
x 128 checkpoint (9.2 GB; skipped when less than 12 GB is free) and
commits slot 998 across all layers, so the last layer's element offset
is past 2^31 while the total pool is modest. It requires the last layer
to equal the first and both neighbouring slots to stay zero. On an
unpatched tree both cases die with `cudaErrorIllegalAddress`; with the
fix they pass. A first version of the test committed a low slot and
passed on the unpatched tree too, which is why the committed slot sits
at the top of the pool. The whole file passes on B200: 200 passed, 16
skipped.

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
with your test targets. -->
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

The ReplaySSM verify kernel takes a per-layer pool, so its offsets stay
below 2^31 for any realistic single-layer pool and are not changed here.
The tcgen05 fold's TMA coordinate `state_flat = flat_slot * HV + i_hv`
stays well inside 32 bits (300k at the failing shape); the overflow was
in the element offset the Int32 coordinate produced against the Int32
stride, which the Int64 coordinate now avoids.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* Fixed ReplaySSM state indexing for large checkpoint pools, preventing
overflow when selecting slots across many layers.
* **Tests**
* Added regression coverage for both commit backends, verifying state
updates and that neighboring slots remain unchanged.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4758
- **最后更新**: 2026-10-29T14:12:05Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34834
- **最后更新**: 2026-10-30T01:45:43Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 3
- **主要提交者**: Sylvan Liu, Aloys Jehwin, YiYi Xu

## AI分析总结

# huggingface/diffusers 昨日提交分析

## 1. 主要更新类型

本次提交涵盖**功能新增**（新模型、新注意力后端）、**Bug修复**（分片保存清理逻辑）、**文档更新**和**日志级别调整**四类，功能新增占比最高。

## 2. 关键变更点及与项目方向的关系

- **新增 Pika H3 Flex 模型**（#15150）及配套文档：作为 diffusers 核心使命——提供最先进的扩散模型实现——的直接延续，扩展了项目支持的模型生态。文档还介绍了通过 components manager 复用已加载的 MiniMax-H3 组件，反映了项目向**模块化组件复用**方向发展的趋势。
- **新增 `aiter_sage_hub` 注意力后端**（#15060）：面向 AMD RDNA4 (gfx1201) GPU 引入 SageAttention（INT8 QK^T + FP8 PV），通过 Hub 分发内核，不支持的场景自动回退至原生 SDPA，同时支持 Ulysses 上下文并行。这体现了项目持续**扩展硬件加速覆盖面**（尤其是 AMD 生态）的承诺。
- **修复 `save_pretrained` 分片清理 Bug**（#14844）：保存默认权重时可能误删另一变体的分片文件，导致变体无法加载；重新保存为单文件时还会残留过期索引。修复方案精确锚定到本变体/格式的分片命名模式，并清理自身过期索引。这是一个影响用户数据完整性的**关键 Bug 修复**。
- **组件重复注册日志级别 warn→debug**（#15152）：配合 modular 架构，同一组件以自身名称重复注册时不再产生警告噪音，属于**开发者体验优化**，反映了项目向模块化（components manager）架构演进的方向。

## 3. 对项目的影响和潜在意义

- **分片保存 Bug 修复**直接解决了 #14719 报告的用户可见问题，提升了 checkpoint 管理的可靠性，对训练/微调工作流影响深远，避免了潜在的数据丢失。
- **Pika H3 Flex + 组件复用文档**降低了用户使用新模型和复用已有模型组件的门槛，推动生态繁荣。
- **AMD RDNA4 后端**填补了 AMD 新一代 GPU 上高效注意力的空白，通过 Hub 内核分发机制保持了灵活性和可维护性。
- **日志级别调整**虽小，但信号清晰：项目正在将 modular/components manager 架构作为一等公民对待，容忍重复注册而非视为异常。

## 4. 值得关注的技术点

- **SageAttention 内核的回退策略设计**：仅在 head_dim=128 且 bf16 等条件下走快路径，其余情况自动回退 SDPA，且考虑到 VAE 等组件也遵循当前后端，这种防御性设计值得借鉴。
- **分片清理的正则锚定方案**：使用 `_REGEX_SHARD` 精确匹配 `<weights_name>-NNNNN-of-NNNNN` 模式而非裸前缀匹配，是处理多变体共存 checkpoint 的正确思路。
- **Hub 内核分发模式**（`kernels-community/aiter-sage-attention`）：将硬件特定内核从主仓库解耦到 Hub，是社区驱动加速生态的范式。

## 5. 对项目发展的整体影响

结合 README 中 HuggingFace 团队对 diffusers 的定位——Apache 2.0 协议的开源扩散模型库——这些提交共同推进了三个核心方向：**模型生态扩展**（新模型 + 组件复用）、**硬件加速广度**（AMD GPU 支持）和**基础设施稳健性**（checkpoint 保存可靠性）。组件管理器相关的连续变更（重复注册容忍 + 复用文档）表明项目正向更加模块化、可组合的架构演进，这将使未来模型集成和用户自定义更加便捷。整体而言，这是一个成熟项目在功能、稳定性和生态三方面均衡推进的典型一天。

## 详细提交记录

### [d8c1b13](https://github.com/huggingface/diffusers/commit/d8c1b13c756df0059bcdb6e477a1eafcd502098d)

- **作者**: YiYi Xu
- **时间**: 2026-10-29T23:14:02Z
- **提交信息**: [components manager] when a component is registered again: warn -> debug (#15152)

[modular] don't warn when a component is registered again under its own name

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [0a48830](https://github.com/huggingface/diffusers/commit/0a48830128b0590d6a0c13a9f44fc91d07ce9f44)

- **作者**: YiYi Xu
- **时间**: 2026-10-29T23:13:09Z
- **提交信息**: [docs] Pika H3 Flex: add a section on reusing minimax h3 components (#15153)

[docs] Pika H3 Flex: reuse a loaded MiniMax-H3 through the components manager

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d0b9b1b](https://github.com/huggingface/diffusers/commit/d0b9b1b5a540e5f9df2f8ec236347bf9c5aa7d1f)

- **作者**: YiYi Xu
- **时间**: 2026-10-29T16:49:51Z
- **提交信息**: Pika h3 flex (#15150)

* add pika h3 flex.


---------

Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

### [aae97e7](https://github.com/huggingface/diffusers/commit/aae97e79e8e6a55e0b43114f9c8916c06d4bca8c)

- **作者**: Aloys Jehwin
- **时间**: 2026-10-29T09:41:07Z
- **提交信息**: fix: scope save_pretrained shard cleanup to the saved variant (avoid deleting another variant's shards) (#14844)

* fix(modeling): scope save_pretrained shard cleanup to the saved variant

The previous-save cleanup in save_pretrained matched shards by a bare
prefix startswith plus a generic shard regex. Saving default weights
(weights_name 'diffusion_pytorch_model') into a directory holding another
variant's sharded checkpoint ('diffusion_pytorch_model.ema-00001-of-...')
matched and deleted that variant's shards while leaving its index, so the
variant could no longer be reloaded. A formerly-sharded checkpoint
re-saved as a single file also left a stale index that load then followed
instead of the new weights.

Anchor the match to the exact per-variant/format shard name
(<weights_without_ext>-NNNNN-of-NNNNN) and remove this checkpoint's own
now-obsolete index when it is no longer sharded.

Fixes #14719

* simplify variant shard cleanup using _REGEX_SHARD

* Apply style fixes

---------

Co-authored-by: DN6 <dhruv.nair@gmail.com>
Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>

### [a05aefa](https://github.com/huggingface/diffusers/commit/a05aefa8b970765a8366b70537edc6e3a9cb2c93)

- **作者**: Sylvan Liu
- **时间**: 2026-10-29T09:40:31Z
- **提交信息**: Add `aiter_sage_hub` attention backend for AMD RDNA4 (gfx1201) (#15060)

* Add aiter_sage_hub attention backend for AMD RDNA4 (gfx1201)

SageAttention (INT8 QK^T, FP8 PV) for gfx1201 through the
kernels-community/aiter-sage-attention Hub kernel. Calls the kernel cannot
take (head dim other than 128, non-bf16, masks, causal, unequal Q/K/V
shapes) fall back to native SDPA, since components such as the VAE follow
the active backend. Supports Ulysses context parallelism.

Signed-off-by: Sylvan Liu <Sylvan.Liu@amd.com>

* Add gfx1201 GPU tests for the aiter_sage_hub backend

Add aiter_sage_hub to the attention backend tester parameters, skipped
unless a gfx1201 GPU and `kernels` are available. The tiny test models
use head dims below 128, so they only exercise the native fallback;
TestAiterSageHubKernel checks the real kernel on head dim 128 against
SDPA.

Signed-off-by: Sylvan Liu <Sylvan.Liu@amd.com>

---------

Signed-off-by: Sylvan Liu <Sylvan.Liu@amd.com>
Co-authored-by: Sayak Paul <spsayakpaul@gmail.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
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


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13324
- **最后更新**: 2026-10-29T16:34:33Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 38367
- **最后更新**: 2026-10-30T01:55:05Z

## 提交统计

- **昨日提交总数**: 60
- **提交者数量**: 35
- **主要提交者**: jacky.cheng, metamergebot, YC Yen-Ching Tseng

## AI分析总结

# SGLang 昨日提交分析总结

## 1. 主要更新类型

昨日共 60 个提交，构成为：
- **性能优化**：约 17 个（28%），占比最大
- **功能新增**：约 20 个（33%），实际最多
- **Bug 修复**：约 15 个（25%）
- **重构**：约 7 个（12%）
- **文档/CI**：约 8 个（13%，与上述有重叠）

## 2. 关键变更点及与项目方向的关系

SGLang 的目标是为 LLM 和多模态模型提供高速推理。本次提交体现了几条清晰主线：

**（1）核心推理内核持续压榨性能**：多个提交针对 MoE、MLA、投机解码等核心路径做 CUDA/Triton 内核级优化（如 `mhc` 按 batch 拆分行、MoE 窄缓冲区填充、mamba 卷积验证窗口 tile 化、pooled indexer top-k 的 3-CTA tier）。这直接服务"Fast inference"的项目定位。

**（2）投机解码（Spec Decoding）生态扩张**：新增 DSpark 投机解码支持（Hopper 上的 MiniMax-M3.1-Flash）、DSPARK watermark 支持、GLM NextN PTPC 量化修复、DeepSeek-V4/V4.1 的 rust 端解析支持、DSpark draft KV 注入位置修复。这是近期最重要的功能方向，表明项目在积极扩展前沿模型的加速能力。

**（3）分布式与 PD 分离（Prefill-Decode Disaggregation）**：多步提交修复 PP 阶段间 KV 传输结果一致性（prefill 和 decode 各一个）、解码端统一 page-envelope 主机池接收、prefill 循环等待前向结果时轮询已完成 KV 传输。这些是大规模部署的关键可靠性与吞吐改进。

**（4）多硬件后端扩张**：AMD（MI35x、gfx1151/1250 的 Quark MXFP4 MoE、diffusion 量化注意力后端）、NPU（Qwen3.6 FP8 MoE、kimi-k3 修复、覆盖率基线自动化）、MUSA（portable capture status）、NVIDIA（deep_select）。项目正从" CUDA 优先"转向真正的多厂商推理平台。

**（5）Rust 服务器持续成熟**：报告模型启动字段、线程绑核优化（共享 CPU 集而非每核一个）、多模态 MM processor 就绪前拒绝请求、提供 profile 接口。rust-server 正成为生产级前端。

**（6）多模态/扩散模型**：Qwen-Image-2.1-Turbo VAE tiling 色带修复、Wan VAE 解码优化、OpenAI 视频任务取消接口、HY-Nomas 与 FastH3 Omni 索引、joy-image GELU 融合。表明 SGLang 在 LLM 之外认真投入多模态推理。

**（7）系统重构**：调度器 KV 长度通过 ReqKvInfo 方法统一写入、删除死代码、typed customized_info、detokenizer 增量解码状态迁移、投机解码 ragged-verify 图 tier 单点解析。这些降低长期维护成本。

## 3. 对项目的影响和潜在意义

- **性能层面**：内核优化与调度器输出统计仅在变化时发送等改动，对高吞吐服务的 P99 延迟和 GPU 利用率有直接收益。
- **可靠性层面**：PP 阶段间 KV 传输结果一致性的修复，解决了多阶段流水线下容易出现的静默数据不一致问题，对大规模生产部署意义重大。
- **生态层面**：对 DeepSeek-V4、GLM5、MiniMax-M3.1、Qwen3.6 等新模型的紧跟支持，使 SGLang 保持在主流开源模型推理的最前沿。
- **商业层面**：AMD/NVIDIA/MUSA 多后端投入，有利于降低用户对单一硬件厂商的依赖，扩大用户基数。

## 4. 值得关注的技术点

- **投机解码的多实现并行推进**（DSpark、NextN、draft KV TP placement），说明团队认为这是提升 decode 吞吐的主路径。
- **rust-server 线程绑核改为共享 CPU 集**：一个看似小的改动，反映对前端 CPU 竞争与缓存局部性的理解。
- **Claude 等 AI 协作署名频繁出现**（多处 Co-authored-by: Claude Opus），表明该项目已高度采用 AI 辅助开发流程，值得其他开源项目参考。
- **EPLB（Expert-Parallel Load Balancing）与模拟路由**下的逐层 glue 代码移除，显示 MoE 推理路径正在从"能跑"走向"精简"。

## 5. 结合项目背景的整体评估

README 强调 SGLang 是"Fast inference for LLMs and multimodal models"。这批提交完美呼应了这一使命：通过内核级性能优化兑现"Fast"，通过 DSpark/DeepSeek-V4/GLM5 等支持兑现"LLM"，通过 VAE/扩散模型/视频任务支持兑现"multimodal"。同时，多硬件后端（AMD/NPU/MUSA）、PD 分离与 PP 一致性修复，标志着项目正从一个"研究向的快速推理引擎"向"可承载生产负载的多厂商推理平台"演进。整体发展势头健康，架构演进（重构 + typed 状态）也为后续迭代打下基础。昨日一天 60 个提交的节奏，也体现了社区与自动化协作流程的高效运转。

## 详细提交记录

### [302b78c](https://github.com/sgl-project/sglang/commit/302b78ccf078b91ee68b154d5e46b0be79bfedff)

- **作者**: akhilg-nv
- **时间**: 2026-10-29T23:56:55Z
- **提交信息**: [Perf] mhc: Split hc_combine_norm_mxfp8 rows by batch size and zero padding scales in the kernel (#46024)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [add6f6d](https://github.com/sgl-project/sglang/commit/add6f6d093351e24aaa0ba5e1f46b74d4a100af3)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T23:32:58Z
- **提交信息**: [Refactor] detokenizer: Move the incremental decode state and step into incremental_detokenize.py (#47338)

### [da4ffac](https://github.com/sgl-project/sglang/commit/da4ffac806d61d89aa7e0a2c1e9be9a2746b1cc4)

- **作者**: Chunan Zeng
- **时间**: 2026-10-29T23:31:59Z
- **提交信息**: [Perf] [NVIDIA] deep_select: Add a 3-CTA tier for the paged indexer top-k (#47328)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [20036b7](https://github.com/sgl-project/sglang/commit/20036b7add8c573cf74364028d13a3ec18bdd3c6)

- **作者**: metamergebot
- **时间**: 2026-10-29T21:46:23Z
- **提交信息**: [Perf] moe: Fill padded rows of large narrow buffers with a strided grid (#47115)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: charlotte12l <charlotte12l@users.noreply.github.com>

### [45fbc06](https://github.com/sgl-project/sglang/commit/45fbc06e210dffb4fa8b2a6ecdd2cdc55177e998)

- **作者**: Chunan Zeng
- **时间**: 2026-10-29T21:45:58Z
- **提交信息**: [Perf] dsv41: Drop per-layer routing glue under simulated routing with EPLB (#47304)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d89a1b1](https://github.com/sgl-project/sglang/commit/d89a1b1ae3244f81c711c2b29b019567c16f93dc)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T21:35:27Z
- **提交信息**: [Test] managers: Check output_ids in the router grouping test (#47335)

### [9748316](https://github.com/sgl-project/sglang/commit/974831643fd5a4944b506439d4404ae64fe69539)

- **作者**: Jian Chen
- **时间**: 2026-10-29T21:14:32Z
- **提交信息**: [Perf] mamba: write the deduplicated conv verify window as one tile (#46184)

Co-authored-by: Jian Chen <jic188@ucsd.edu>
Co-authored-by: Zihan Zhang <tiancaizhangdaxian@sjtu.edu.cn>

### [fbc90a8](https://github.com/sgl-project/sglang/commit/fbc90a860ec0ae4cd7a458d679bc68eefbbbcdc6)

- **作者**: Eric.Chin.AMD
- **时间**: 2026-10-29T21:11:46Z
- **提交信息**: [Fix] attention: Skip the MSA-v1 QMUL4 prefill case when QMUL4 is unavailable (#47286)

Co-authored-by: Thomas Wang <thomawan@amd.com>

### [d71bf63](https://github.com/sgl-project/sglang/commit/d71bf63fb57c5981bed031884637aebe4c1109c5)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-29T21:11:17Z
- **提交信息**: [Feat] watermark: Add DSPARK speculative decoding support (#44200)

### [dfdee25](https://github.com/sgl-project/sglang/commit/dfdee259c52b2ed3a42e516dcdab21fb4b330d1e)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T21:09:06Z
- **提交信息**: [Refactor] scheduler: Drop the dead Req.decoded_text and BatchTokenIDOutput.decoded_texts (#47249)

### [f3f23d1](https://github.com/sgl-project/sglang/commit/f3f23d128cd576352492334534be7e20fdd8fab6)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T20:59:43Z
- **提交信息**: [Refactor] scheduler: Write every request KV length through ReqKvInfo methods (#43895)

### [f5f79c5](https://github.com/sgl-project/sglang/commit/f5f79c5c1820c104c04379cc1d3c357963b8e8e7)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T20:54:32Z
- **提交信息**: [Perf] scheduler: Send the per-request output stats only when they may have changed (#47178)

### [5696215](https://github.com/sgl-project/sglang/commit/56962151685adca10aa8ca7552c1b0aead261746)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T20:49:11Z
- **提交信息**: [Refactor] Spec: Resolve the ragged-verify graph tier at a single point (#34038)

Co-authored-by: Qiaolin-Yu <liin1211@outlook.com>

### [259f013](https://github.com/sgl-project/sglang/commit/259f0131c926c31a82afa165e2079e37e8f1f998)

- **作者**: Glen Liu
- **时间**: 2026-10-29T20:42:44Z
- **提交信息**: [Feat] LoRA: revamp LoRADrainer for better performance (#46500)

Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>

### [3a3a861](https://github.com/sgl-project/sglang/commit/3a3a8611a45f5a81fd07ffa6b0ed3ba33e7a4db9)

- **作者**: weireweire
- **时间**: 2026-10-29T18:45:27Z
- **提交信息**: [Fix] eplb: Warm default-group P2P transports on multi-node layouts (#46592)

Co-authored-by: weireweire <20922698+weireweire@users.noreply.github.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [15bb4a0](https://github.com/sgl-project/sglang/commit/15bb4a0fc967d59e65ab065ebe56608fa6046014)

- **作者**: Yonghao Zhuang
- **时间**: 2026-10-29T18:35:06Z
- **提交信息**: [Feat] cp: Add KV layout hooks and padded storage accounting (#45434)

### [acdad27](https://github.com/sgl-project/sglang/commit/acdad27d74d00448bb181ce1ea2b38c111a48a40)

- **作者**: metamergebot
- **时间**: 2026-10-29T18:32:33Z
- **提交信息**: [Feat] disaggregation: Decode host receive on the unified page-envelope host pool (#47124)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [6c61cec](https://github.com/sgl-project/sglang/commit/6c61cecca72efd19a7e3da5916eb26be0e436436)

- **作者**: metamergebot
- **时间**: 2026-10-29T18:32:16Z
- **提交信息**: [Refactor] engine: Make the follower-rank SIGTERM handler an overridable classmethod (#47158)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: 842974287 <842974287@users.noreply.github.com>

### [f18d5e6](https://github.com/sgl-project/sglang/commit/f18d5e6c19cb0f0890782d98a13206c2af9c6938)

- **作者**: metamergebot
- **时间**: 2026-10-29T18:01:53Z
- **提交信息**: [Refactor] tokenizer_manager: Move the crash-dump writer into a utils module (#47107)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [1b16e2a](https://github.com/sgl-project/sglang/commit/1b16e2aa6a9f4b254fc811c4731bde43f5d08f5a)

- **作者**: metamergebot
- **时间**: 2026-10-29T18:01:33Z
- **提交信息**: [Feat] scheduler: Add typed per-token and per-request customized_info values (#47072)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: cctry <cctry@users.noreply.github.com>

### [2749b94](https://github.com/sgl-project/sglang/commit/2749b946de28f4b1022f90a828cfcf50ad29972a)

- **作者**: metamergebot
- **时间**: 2026-10-29T18:00:50Z
- **提交信息**: [Perf] pd: Poll finished KV transfers while the prefill loop waits for a forward result (#47015)

Co-authored-by: metamergebot <metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [0580e94](https://github.com/sgl-project/sglang/commit/0580e941eff5b491a91fe878a82921ac9371941e)

- **作者**: Ying_Zhou
- **时间**: 2026-10-29T17:47:35Z
- **提交信息**: [Feat] [MUSA] breakable: Support portable capture status (#47034)

Co-authored-by: yingzhou-bjtu <yingzhou-bjtu@users.noreply.github.com>
Co-authored-by: R0CKSTAR <yeahdongcn@gmail.com>

### [d213124](https://github.com/sgl-project/sglang/commit/d213124956421e8c16d52d0b0e677a49b0a1868b)

- **作者**: Ke Bao
- **时间**: 2026-10-29T17:33:30Z
- **提交信息**: [Doc] cookbook: Add MiniMax-M3.1-Flash B300 TP2 SPF AgentX points (#47303)

### [46008a7](https://github.com/sgl-project/sglang/commit/46008a7afc27b6fea4007f870f800ffbc3e3819d)

- **作者**: metamergebot
- **时间**: 2026-10-29T17:09:28Z
- **提交信息**: [Feat] rust-server: Report the model's launch-time fields in /model_info (#47169)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [5ed1433](https://github.com/sgl-project/sglang/commit/5ed14333769d26cb6960c30c9ab8ca6f6b867efd)

- **作者**: metamergebot
- **时间**: 2026-10-29T17:09:17Z
- **提交信息**: [Perf] rust-server: Pin frontend threads to one shared CPU set, not one core each (#47161)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>
Co-authored-by: Lu Fang <30275821+houseroad@users.noreply.github.com>

### [8773d60](https://github.com/sgl-project/sglang/commit/8773d60f25b57b1889a7e23af1019014ddd8f028)

- **作者**: metamergebot
- **时间**: 2026-10-29T17:09:07Z
- **提交信息**: [Fix] rust-server: Admit a multimodal model's generations only once its MM processor is installed (#47108)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [8705d35](https://github.com/sgl-project/sglang/commit/8705d359b90ec14c1d6dc7118ce9c832d148a3ac)

- **作者**: metamergebot
- **时间**: 2026-10-29T17:08:57Z
- **提交信息**: [Feat] rust-server: Serve /start_profile and /stop_profile (#46968)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2c6b95e](https://github.com/sgl-project/sglang/commit/2c6b95e035e8d01e9b00ce203a0fba98f552f9e0)

- **作者**: jacky.cheng
- **时间**: 2026-10-29T16:59:17Z
- **提交信息**: [Feat] [AMD] Quark: Run Quark MXFP4 MoE as W4A16 via triton_kernels on RDNA (gfx1151) (#41389)

Co-authored-by: Hubert Lu <Hubert.Lu@amd.com>

### [b142fcd](https://github.com/sgl-project/sglang/commit/b142fcde837e8d58104f5af3c7f5c8e7b6919e07)

- **作者**: Ke Bao
- **时间**: 2026-10-29T16:40:07Z
- **提交信息**: [Feat] minimax-m3.1: Support DSpark on Hopper (#46868)

### [686cf98](https://github.com/sgl-project/sglang/commit/686cf984704b79cb1b3f7145827c6f1922c4445d)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-10-29T15:47:59Z
- **提交信息**: [CI] [AMD] workflows: Run scheduled Extra tests, stop skipping nightly tests, merge MI35x 1-GPU jobs- #47238 (#47244)

Co-authored-by: Bingxu Chen <Bingxu.Chen@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [de6c211](https://github.com/sgl-project/sglang/commit/de6c211a490588b542c42eee95b6610f0712f4ba)

- **作者**: Yuedong Wu
- **时间**: 2026-10-29T14:17:32Z
- **提交信息**: [Fix] [AMD] quark: Skip no-copy loads after MXFP4 quantization (#45802)

Signed-off-by: Yuedong Wu <dwcn22@outlook.com>

### [ebfbd3e](https://github.com/sgl-project/sglang/commit/ebfbd3ea35acf6e9facbe74e627d37c3542e5fc1)

- **作者**: Yuedong Wu
- **时间**: 2026-10-29T14:09:45Z
- **提交信息**: [Fix] GLM: Preserve NextN PTPC quantization for excluded experts (#45800)

Signed-off-by: Yuedong Wu <dwcn22@outlook.com>
Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [d39c8f9](https://github.com/sgl-project/sglang/commit/d39c8f94f0df7a296f6aaa3eb4b0ea5b58f5c4a5)

- **作者**: Torches
- **时间**: 2026-10-29T14:09:02Z
- **提交信息**: [Feat] glm5: Expose per-layer MLA key buffer and use_fused_topk in binding (#45765)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [8b6de67](https://github.com/sgl-project/sglang/commit/8b6de6719dc2076dd2fb88f2266c4152699968df)

- **作者**: Quanli Li
- **时间**: 2026-10-29T14:00:49Z
- **提交信息**: [Fix] diffusion: fix colored seams in single-GPU Qwen-Image-2.1-Turbo VAE tiling (#47092)

### [390acf8](https://github.com/sgl-project/sglang/commit/390acf84e31d3b63dac64e021911d94770e55a8c)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-29T13:42:12Z
- **提交信息**: [Doc] cookbook: Add a new cookbook page (WIP) (#47212)

### [68e57f4](https://github.com/sgl-project/sglang/commit/68e57f40057175ff22a17ea0bdbe7ecbc69d9d91)

- **作者**: Yuhao Yang
- **时间**: 2026-10-29T12:56:09Z
- **提交信息**: [Fix] usage: Clamp reasoning tokens after stop truncation (#47116)

### [f664962](https://github.com/sgl-project/sglang/commit/f6649627836699f76a3054d0812c05ac332932c0)

- **作者**: 黄孝君
- **时间**: 2026-10-29T12:41:51Z
- **提交信息**: [Fix] [NPU] docker: Bump SGLANG_KERNEL_NPU_TAG to 2026.9.0.post12 (#47217)

### [1f80b2b](https://github.com/sgl-project/sglang/commit/1f80b2b21d060975b32acd5013e1d8f0badb847e)

- **作者**: ybyang
- **时间**: 2026-10-29T12:22:50Z
- **提交信息**: [Fix] disaggregation: Agree on each prefill KV transfer's outcome across PP stages (#47045)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e6ca928](https://github.com/sgl-project/sglang/commit/e6ca9285e4117b95efcf897190d3387c10fec65b)

- **作者**: Thanhhao
- **时间**: 2026-10-29T12:13:39Z
- **提交信息**: [Fix] dspark/MiniMax-M3.1-Flash: Inject decode-step draft KV under the draft's TP placement (#46851)

Co-authored-by: Hao Phan <htphan@nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [05c59bb](https://github.com/sgl-project/sglang/commit/05c59bb323c131a4e91623fc914ee6afad21288e)

- **作者**: akhilg-nv
- **时间**: 2026-10-29T12:11:04Z
- **提交信息**: [Fix] mem_cache: Build an empty KVLayerRouter from empty layer maps (#47127)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5007cbd](https://github.com/sgl-project/sglang/commit/5007cbd6a57515bf5e008ff2fd2bdb834356b53c)

- **作者**: Shangming Cai
- **时间**: 2026-10-29T10:59:11Z
- **提交信息**: [CI] slash-command: Write the /run-cpu-ci result back to its reply comment (#47246)

### [03864d7](https://github.com/sgl-project/sglang/commit/03864d7b2f11cfa1b6a083b83fcbe66df7182819)

- **作者**: Shangming Cai
- **时间**: 2026-10-29T10:25:59Z
- **提交信息**: [Fix] disaggregation: Agree on each decode KV transfer's outcome across PP stages (#47063)

### [16a4337](https://github.com/sgl-project/sglang/commit/16a4337813f0306f6b9e493b604b5801ee1791e8)

- **作者**: ehuaa
- **时间**: 2026-10-29T10:25:36Z
- **提交信息**: [Fix] pp: Post the first rank's output recv after its own forward (#46027)

### [1ab008f](https://github.com/sgl-project/sglang/commit/1ab008f5b090e6595479ba57934e9211ab083565)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-29T09:20:43Z
- **提交信息**: [Perf] joy-image: Fuse image MLP GELU on SM120 in high quality (#47022)

### [d1512ad](https://github.com/sgl-project/sglang/commit/d1512ad9e97ba817c8c2d899b4d5405493cad97c)

- **作者**: chenyang08056032
- **时间**: 2026-10-29T09:16:28Z
- **提交信息**: [CI] [NPU] coverage: Automated OBS baseline upload and retry-safe attempt merging (#47230)

Co-authored-by: sglang-npu-bot <sglangnpu@163.com>

### [019008a](https://github.com/sgl-project/sglang/commit/019008afe0b0a61aa46c1f32dbcd6478f1c09220)

- **作者**: hanwlax
- **时间**: 2026-10-29T09:11:56Z
- **提交信息**: [Feat] [NPU] Quant: support Qwen3.6-35B-A3B-FP8 which is block FP8 MOE. (#46212)

sglang/test/registered/unit/mem_cache/test_hicache_nixl_storage.py failed but not caused by this PR.

### [f3bc7a1](https://github.com/sgl-project/sglang/commit/f3bc7a1c1bf23948926763ad41c0b75b17b06fd7)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-29T09:11:37Z
- **提交信息**: [Fix] cuda_graph: Release base storage held by empty break inputs (#46737)

### [970cbb5](https://github.com/sgl-project/sglang/commit/970cbb5fa64424768ca6380585c88d9baba75f24)

- **作者**: Michael
- **时间**: 2026-10-29T09:09:42Z
- **提交信息**: [CI] [AMD] ci: Spread out tests and prefer today's images (#47162)

Co-authored-by: Bingxu Chen <bingxche@amd.com>

### [7df65d9](https://github.com/sgl-project/sglang/commit/7df65d970df80235ecda9862ea67fa210bc6d7b9)

- **作者**: jacky.cheng
- **时间**: 2026-10-29T08:44:47Z
- **提交信息**: [Perf] [AMD] diffusion: Optimize the Wan VAE decode for gfx1250 (#46722)

### [9e9296f](https://github.com/sgl-project/sglang/commit/9e9296fdf352d767e66d49367b8763fd788184b6)

- **作者**: Mick
- **时间**: 2026-10-29T08:33:30Z
- **提交信息**: [Doc] diffusion: Index HY-Nomas and FastH3 Omni (#47176)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [149dc27](https://github.com/sgl-project/sglang/commit/149dc279d9757af14d756d39f1c84cc4d99bfb36)

- **作者**: zhaozx-cn
- **时间**: 2026-10-29T08:33:00Z
- **提交信息**: [Fix] [NPU] kimi-k3: fix npu fused_sigmoid_gating_delta_rule (#47061)

### [4aad328](https://github.com/sgl-project/sglang/commit/4aad3283bdd620b289334563636e89b66d23115c)

- **作者**: Mick
- **时间**: 2026-10-29T08:32:31Z
- **提交信息**: [Refactor] diffusion/bcg: Share graph-pool output management (#46709)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [8b0f2f9](https://github.com/sgl-project/sglang/commit/8b0f2f929f05a4eb447fe143ecd3ba54e688f33a)

- **作者**: Haim Rozenblum
- **时间**: 2026-10-29T08:29:20Z
- **提交信息**: [Feat] diffusion/openai: Cancel video jobs on DELETE (#47055)

Co-authored-by: Haim Rozenblum <hrozenblum@crusoe.ai>
Co-authored-by: Chi McIsaac <153383231+qimcis@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [58214f6](https://github.com/sgl-project/sglang/commit/58214f648c812c70bfd57f0b4196de494f75c0bc)

- **作者**: Aleksi Vesanto
- **时间**: 2026-10-29T08:11:01Z
- **提交信息**: [Feat] [AMD] diffusion: Add quantized attention backends for GFX942/GFX950 (#35151)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [d7522db](https://github.com/sgl-project/sglang/commit/d7522db332b3c6473bade8dd55705631a93430f4)

- **作者**: Vinsmoke86
- **时间**: 2026-10-29T07:54:59Z
- **提交信息**: [Feat] sail: support sail fa3 and flashmla [3/N] (#45946)

Co-authored-by: shiyunzhi <shiyunzhi.syz@alibaba-inc.com>

### [3abe1c8](https://github.com/sgl-project/sglang/commit/3abe1c85273ea4dc51cea3eaee49191d12caa0e9)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-29T07:49:57Z
- **提交信息**: [Feat] rust: Parse DeepSeek-V4/V4.1 output with deepseek-recipe (#46780)

Co-authored-by: Shangming Cai <csmthu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b069d22](https://github.com/sgl-project/sglang/commit/b069d22a9c379e903c0af3f9d9fb0332e3c8d298)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-29T07:49:03Z
- **提交信息**: [Doc] cookbook: Refresh SemiAnalysis AgentX launches to InferenceX main 70a76017 (#47214)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bd1eb0b](https://github.com/sgl-project/sglang/commit/bd1eb0bb899b5c65a0791d4e69eaef214b2bc1eb)

- **作者**: Thomas Wang
- **时间**: 2026-10-29T07:26:31Z
- **提交信息**: [Perf] [AMD] dsv41: Drop the per-step whole-vocab gather of draft logits via sharded accept (#44465)

### [9df3d27](https://github.com/sgl-project/sglang/commit/9df3d27eed88d8c47a0b7f0cad9e4eafcbdcaed2)

- **作者**: jacky.cheng
- **时间**: 2026-10-29T07:22:50Z
- **提交信息**: [Perf] [AMD] diffusion: Replace the gfx1250 bf16 scale-shift torch fallback with a bit-exact Triton kernel (#46723)

### [46caa54](https://github.com/sgl-project/sglang/commit/46caa54562a97e71d9b937c62875c90b39274b0d)

- **作者**: Shuwen Wang
- **时间**: 2026-10-29T07:04:01Z
- **提交信息**: [Fix] hicache: Isolate NIXL storage tests from background eviction (#47197)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for 100+ DiTs.
- **语言**: Python
- **星标数**: 1295
- **最后更新**: 2026-10-30T00:51:53Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# cache-dit 仓库昨日提交分析

## 1. 主要更新类型

本次 5 个提交可分为两大类：**功能新增**（2 个）和**文档/构建更新**（3 个）。功能新增占比虽少，但均为重大模型支持，代码体量和影响力远超文档提交。无纯 Bug 修复或性能优化提交，但 Wan-Animate-2 提交中附带了一处 offload 健壮性修复。

## 2. 关键变更点与项目方向的关系

项目定位是 PyTorch 原生的 DiT 推理引擎，核心能力围绕缓存、并行（CP/TP）、量化和 CPU offload。本次更新高度契合这一方向：

- **Wan-Animate-2 支持**（#1178）：一次性覆盖 base 和 distilled 两个 checkpoint，完整实现了缓存（Pattern_3 block adapter、PatchFunctor）、上下文并行（Ulysses attention + flex block mask）、张量并行（colwise/rowwise plans）、CPU offload 以及 CLI 集成。这是项目"全栈推理能力"定位的典型体现。
- **SANA-WM 支持**（#1177）：引入双 stage（DiT + LTX-2 refiner）的块级缓存，TP 采用"分片注意力权重 + 复制激活"的折衷方案，并显式拒绝 CP（因 GDN 时序递归不适合 all-to-all）。展现了引擎在非标准架构上的适配能力。
- **构建配置调整**（#1179）：setup.py 默认编译全架构（89, 90a, 100, 120a on CUDA 13），降低用户构建门槛，是工程体验的改进。
- **文档同步**（#1184, #1182）：保持文档一致性，将算子迁移指南限定为 CUDA-only，反映项目实际只支持 CUDA 后端的现实。

## 3. 对项目的影响和潜在意义

- **模型生态显著扩展**：Wan-Animate-2 和 SANA-WM 均为当前热门的视频生成/动画模型，支持它们直接扩大了 cache-dit 的用户覆盖面和实用性。
- **推理鲁棒性提升**：`pin_memory()` 被拒绝时回退到 pageable memory 的修复，解决了 CUDA 驱动层面偶发 `cudaErrorInvalidValue` 导致整个 offload 初始化失败的问题，使 CPU offload 在实际生产环境中更可靠。
- **分布式能力的边界更加清晰**：SANA-WM 显式拒绝 CP 并给出解释（GDN 递归需要 halo/state 交换），避免用户在不支持的场景下浪费时间调试，体现了成熟的工程判断。

## 4. 值得关注的技术点

- **WanAnimate2PatchFunctor 的设计**：在 block 内解析 per-layer reference K/V，重放 layer 9 的无条件跳过，绕过缓存 wrapper 进行 per-segment extract pass，并从 latents 推导 RoPE 设备——这些细节体现了对模型内部机制的深度理解。
- **SANA-WM 的注册机制**：单一 "SanaWM" 注册根据 block stack 名称（"blocks" vs "transformer_blocks"）自动分派到 stage 1 或 refiner，避免了重复注册。
- **TP 方案的权衡**：SANA-WM stage 1 因 fused QKV reshape、全局 RMSNorm 和 depthwise 时序卷积需要全宽，故采用注意力权重分片 + 激活复制的混合策略，是实用主义的工程选择。
- **全架构默认构建**：将 `CACHE_DIT_RELEASE_ARCH` 留空设为硬性规则，统一了发布构建的架构覆盖面。

## 5. 对项目发展的综合影响

cache-dit 正处于快速扩展模型支持的阶段。本次提交集中体现了"新模型接入"这一核心发展路径：每个新模型都完整覆盖缓存、并行、offload、CLI 和测试，说明项目已形成了成熟的模型接入范式和工具链。同时，构建配置的简化和 offload 健壮性的修复表明项目开始关注工程质量和用户体验，这是从"能用"走向"好用"的关键信号。文档的持续同步和算子迁移指南的 CUDA 限定，则反映了项目对支持边界的诚实态度。整体来看，这些提交强化了 cache-dit 作为"DiT 推理全栈解决方案"的定位，为其在视频生成生态中的竞争力奠定了基础。

## 详细提交记录

### [4ddf61f](https://github.com/vipshop/cache-dit/commit/4ddf61f83fcf05ff95bde10c86dff15112ef345d)

- **作者**: DefTruth
- **时间**: 2026-10-29T09:40:44Z
- **提交信息**: docs: sync docs/README.md with README.md (#1184)

* docs: update docs

* docs: update docs

* docs: sync docs/README.md with README.md

### [5293f06](https://github.com/vipshop/cache-dit/commit/5293f06b1afdf17dc3d7ec6acf6755b24d278047)

- **作者**: DefTruth
- **时间**: 2026-10-29T09:17:48Z
- **提交信息**: docs(skill): make the operator migration guide CUDA-only (#1182)

* docs(skill): make the operator migration guide CUDA-only

* chore: replace hardcoded cdit interpreter paths with portable defaults

### [b7518bc](https://github.com/vipshop/cache-dit/commit/b7518bc0133969368b541a97f4d694380d972d0d)

- **作者**: DefTruth
- **时间**: 2026-10-29T08:55:32Z
- **提交信息**: docs(skill): default to full-arch release builds (#1179)

setup.py now compiles the full default arch set (89, 90a, 100, 120a on CUDA 13).
Make leaving CACHE_DIT_RELEASE_ARCH empty a hard rule in cache-dit-build-release and
refresh the stale 80/86/89/120a/121a lists in SKILL.md and its references.

### [4ef6730](https://github.com/vipshop/cache-dit/commit/4ef6730f64d837a6443828e79627c8deca44140a)

- **作者**: DefTruth
- **时间**: 2026-10-29T08:45:20Z
- **提交信息**: feat: support Wan-Animate-2 (base + distilled) (#1178)

* feat: add Wan-Animate-2 support (cache, CP, TP, offload, CLI)

- WanAnimate2 block adapter (Pattern_3, 40-layer 'blocks' list) that derives separate-CFG
  from the guider so the base (CFG 3.0) and distilled (guidance 1.0) checkpoints both work
- WanAnimate2PatchFunctor: resolves the per-layer reference K/V inside the block, replays the
  unconditional skip of layer 9, bypasses the cached wrapper for the per-segment extract pass,
  and derives the RoPE device from the latents so layerwise offload stays correct
- CP: full-sequence Ulysses attention with head-sharded reference KV over the packed
  [generation | reference] flex block mask; ring attention and ulysses_anything are rejected
- TP: colwise/rowwise plans for self_attn/cross_attn/ffn plus DistributedRMSNorm for the
  full-width norm_q/norm_k/norm_added_k
- CLI: wan_animate_2 / wan_animate_2_distilled with driving-video inputs, ANIMATE task type and
  modular 'videos' output handling
- docs, README tables, verified modular pipelines and the predefined separate-CFG prefix list

* docs: correct the Wan-Animate-2 offload note (pin_memory failure is transient, not mmap)

* fix: degrade layerwise offload to pageable memory when pinning is refused

`_prepare_async_target` called `pin_memory()` unguarded, so a refused pinned allocation
(a transient driver-side cudaErrorInvalidValue has been observed, twice, then never again)
aborted the whole offload setup even though pinning is only the staging optimisation.

- mirror through `_pinned_cpu_mirror()`, which falls back to pageable memory on a refused
  pin (both the CPU-source and the CUDA-source `empty_like(pin_memory=True)` paths)
- warn once with module/tensor/dtype/size, then keep quiet; host OOM is still re-raised
- tests cover the CPU-source fallback (sync and bucketed async) and the CUDA-source fallback

* docs: note the pin fallback in the Wan-Animate-2 offload entry

* feat(cli): let --num-frames size the Wan-Animate-2 driving clip

* docs(skill): record the measured GEMM/attn/compile split for Wan-Animate-2

### [ac8df99](https://github.com/vipshop/cache-dit/commit/ac8df99ca69816b6ab9e27cea497df491174b8b6)

- **作者**: DefTruth
- **时间**: 2026-10-29T07:45:28Z
- **提交信息**: feat: support SANA-WM camera-controlled image-to-video (#1177)

* feat: support SANA-WM camera-controlled image-to-video

Add block-level caching for the SANA-WM stage-1 DiT and the stage-2 LTX-2
refiner, tensor parallelism for stage 1, and an explicit context-parallel
refusal.

- adapters: one "SanaWM" registration dispatches on the block stack
  ("blocks" for stage 1, "transformer_blocks" for the refiner); stage 1 is
  Pattern_3 with check_forward_pattern=False (block params are x/y) and needs
  no PatchFunctor because the block loop passes every extra input positionally
  from values built outside the loop.
- functor_sana_wm_refiner: resolve the shared KV container into each layer's
  slice after the block list collapses, replay the originals on the two
  KV-writing passes, and refresh the cache context at every chunk boundary.
- distributed/transformers/sana_wm: TP shards the attention weights with
  replicated activations (fused QKV reshape, global Q/K RMSNorm and the
  depthwise temporal convolution all need full width); the Conv2d FFN is left
  replicated. CP is refused with an explanation: the GDN recurrence runs along
  the temporal axis and needs halo/state exchange, not an all-to-all.
- cli: sana_wm I2V example (action derived from num_frames, intrinsics
  estimated from the source image) plus SANA_WM_DIR / SANA_WM_REFINER_DIR.
- tests: CPU adapter/functor tests and a 2-GPU TP parity test.

* Update README.md

---------

Co-authored-by: DefTruth <deftruth@vipshop.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 95869
- **最后更新**: 2026-10-30T01:49:37Z

## 提交统计

- **昨日提交总数**: 74
- **提交者数量**: 63
- **主要提交者**: milesial, Andrew Sansom, Tomasz Zielinski

## AI分析总结

# vLLM 昨日提交综合分析（共 74 条提交）

## 一、主要更新类型分布

- **Bug 修复**（约 31 条，占比最高）：集中在 KV Offload、KV Connector、量化、Rust 前端解析、投机解码、模型执行等领域。
- **性能优化**（约 17 条）：围绕 DeepSeek-V4.1、MoE、稀疏注意力、GEMM 微调、跨后端算子等展开。
- **ROCm/AMD 平台支持**（约 13 条）：涉及 CI 镜像、部署配方、量化测试、内核与句柄修复。
- **文档更新**（约 10 条）：部署配方、自定义算子生态、模型交叉引用、集成清单。
- **CI/基础设施与功能新增**（约 8 条）：自动分片、镜像构建、Responses API 新特性等。

## 二、关键变更点与项目方向

**KV 缓存与显存管理走向生产级。** 约十条提交集中修复 KV Offload 边界问题——P2P 握手竞态、传输去重、错误请求残留块、跨节点层级限制、telemetry 丢失、GPU 命中前缀的 CPU LRU 刷新、SimpleCPUOffload 零填充规避、MooncakeStoreConnector 睡眠模式支持等。这表明 KV 缓存卸载正从实验特性转向可靠生产路径，直接支撑离线/弹性推理场景下的显存成本优化，是 vLLM"低成本服务"核心目标的关键抓手。

**DeepSeek-V4.1 持续深度优化。** 涵盖 MoE 路由 NaN 防护、Engram 主机表跨 DP 共享、压缩 KV 批量采集、NVFP4 重量化、单体解码 TP8 调优，说明 DSv4.1 是当前性能攻关的旗舰场景。

**多后端硬件生态体系化扩展。** ROCm 侧：MI355X Mistral Large 4 部署配方、AITER MXFP4 测试解禁、FlyDSL JIT 监控与 host launcher 复用、hipBLASLt 句柄修复、Elastic DP 兼容性；另有 Intel XPU 的 MROPE kernel、Iluvatar 自定义算子文档。AMD 及国产平台支持已从"能跑"转向"可维护、可发布"。

## 三、对项目的影响与潜在意义

- **稳定性大幅提升**：KV 缓存损坏回退、NCCL 权重传输静默失败改显式报错、模型执行前 prompt embedding 哨兵 ID 消费、`--max-concurrency 0` 挂起修复等，显著降低生产环境的隐蔽正确性风险。
- **模型矩阵持续扩张**：Ming3-ASR、Nemotron 3.5 Super VL、Muse Spark NVFP4 混合执行、OLMoE 迁移、RADIO 编码器、OpenVLA 模板等多模态与新模型覆盖不断加宽。
- **生态互操作增强**：Mistral common 1.13、Transformers 5.21.1 升级、Anthropic API 内联 system 消息探测、k8s-aibom 集成，强化周边兼容性。
- **API 与工具链打磨**：Responses API 新增 thinking_token_budget 支持；Rust vllm-bench 快速补齐与 Python 版的功能一致性；请求模板信任强制（Security 标签）填补结构化输出的信任边界。

## 四、值得关注的技术点

- **投机解码栈日趋成熟**：GLM-5.3-Flash 自适应验证、PP 下 draft token 广播修复、GLM 低延迟 BF16 GEMM 启用，以及 MRV2 logits-stats kernel 去特化减少编译时间与二进制体积。
- **EPLB 对称内存权重迁移**：symm_mem 后端 + MegaMoE 副本映射融合，是大规模 MoE 弹性负载均衡的新基础设施。
- **SM100（Blackwell）Qwen3.8 skinny GEMM**：TP=1 小矩阵乘法优化，对单卡低延迟推理用户价值显著。
- **GDN + FlashInfer 就地写**：省去中间缓冲区分配，延续零拷贝式内核设计思路。
- **弹性伸缩信号**：睡眠模式与 KV Connector 的结合，暗示 vLLM 正向 Serverless 化推理服务演进。
- **AI 辅助开发常态化**：大量提交共同署名 Claude/Codex/Codex/agent，AI 已深度参与内核级优化与 CI 维护，加速迭代的同时需加强审查。

## 五、总体影响

这批提交体现 vLLM 在"Easy, Fast, Cheap"定位下三线并进：以 KV Offload 可靠性夯实长上下文成本优势；以 DSv4.1/ROCm/XPU 优化扩大高性能硬件覆盖；以模型、API 与工具链兼容性巩固生态位。工程重心明显从功能铺开转向**性能精修、多硬件生态与稳定性加固并重**的成熟期，为大规模生产部署与多平台推广奠定了更坚实的基础。

## 详细提交记录

### [8084f06](https://github.com/vllm-project/vllm/commit/8084f0624dba24aba6ebac62d8e10cc00730a0fe)

- **作者**: Dao007forever
- **时间**: 2026-10-29T23:46:17Z
- **提交信息**: [Bugfix][KV Connector][NIXL] Fix Mamba region stride on block-outermost layouts (#64582)

Signed-off-by: Dao Le <Dao007forever@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [10579b7](https://github.com/vllm-project/vllm/commit/10579b71ebccaf2f5f02ff390718403d368da89e)

- **作者**: Hongxia Yang
- **时间**: 2026-10-29T23:44:06Z
- **提交信息**: [Docs][ROCm] Mistral Large 4 recipe: ROCm image tag, MI355X, TP4 replica launch (#64544)

### [255431b](https://github.com/vllm-project/vllm/commit/255431b5ed8777b7524c65e9d3dfadeb2319abfc)

- **作者**: Maroon Ayoub
- **时间**: 2026-10-29T23:30:24Z
- **提交信息**: [Bugfix][Parser] Parse closed GLM-4.7 tool arguments once while streaming (#64535)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [4b47db9](https://github.com/vllm-project/vllm/commit/4b47db922b833b83f8f1e067a9f5ac9fed16c769)

- **作者**: Or Ozeri
- **时间**: 2026-10-29T21:58:47Z
- **提交信息**: [CI][KV Offload][P2P] Wait for the handshake in the idle peer-hit tests (#64555)

Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [434eadc](https://github.com/vllm-project/vllm/commit/434eadcbf81b664e34f0772cfd71419f7569849c)

- **作者**: Thang Nguyen
- **时间**: 2026-10-29T21:45:23Z
- **提交信息**: [CI] Enroll two steps and two AMD mirrors in automatic sharding (#64115)

Signed-off-by: Thang Nguyen <thangnguyenvn647@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f97a8d6](https://github.com/vllm-project/vllm/commit/f97a8d664796124384fc1f6c2c54030502caa1e8)

- **作者**: Oxana Korzh
- **时间**: 2026-10-29T21:36:16Z
- **提交信息**: [ROCm][Perf][DSv4.1] Mono decode at TP8 on MI355X (#64101)

Signed-off-by: Oxana Korzh <okorzh@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2abde62](https://github.com/vllm-project/vllm/commit/2abde627d973ad28d577133bdac5472bb00ee255)

- **作者**: Yongye Zhu
- **时间**: 2026-10-29T20:58:53Z
- **提交信息**: [ROCm][Quantization] NVFP4 MoE re-quantization and fused shared experts through online quantization (#64378)

Signed-off-by: Yongye Zhu <zyy1102000@gmail.com>
Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: fxmarty-amd <felmarty@amd.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Hongxia Yang <62075498+hongxiayang@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Felix Marty <Felix.Marty@amd.com>

### [aa738c3](https://github.com/vllm-project/vllm/commit/aa738c38c3cf9861f63332b981a87bdf85166791)

- **作者**: JunjieChen
- **时间**: 2026-10-29T20:46:04Z
- **提交信息**: [KV Connector][Mooncake] Renew prefill KV leases from the decoder (#64193)

Signed-off-by: CJJ1008 <843515223@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e18e2c7](https://github.com/vllm-project/vllm/commit/e18e2c70c5cd299bf0d066c2c8118f57dd8bc6eb)

- **作者**: frida-andersson
- **时间**: 2026-10-29T20:41:08Z
- **提交信息**: [Bugfix][ROCm][DSv4.1] Guard NaN scores in gfx942 mono routing (#63816)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [4e0ad57](https://github.com/vllm-project/vllm/commit/4e0ad572036166a8bdf1782f4a07b4e33016646b)

- **作者**: Juntian Liu
- **时间**: 2026-10-29T19:45:05Z
- **提交信息**: [Perf][DSv4.1] Share Engram host tables as host-NUMA cuMem across DP ranks (#62359)

Signed-off-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0124e16](https://github.com/vllm-project/vllm/commit/0124e16a6c06818e4d91bbabb821df7498645e3e)

- **作者**: Simon Danielsson
- **时间**: 2026-10-29T19:43:02Z
- **提交信息**: [ROCm] Monitor FlyDSL JIT compilation after warmup (#62481)

Signed-off-by: simondanielsson <simon.danielsson99@hotmail.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [b2f46e7](https://github.com/vllm-project/vllm/commit/b2f46e785fe1584ecc654e5ef1bdc3fccc2c597a)

- **作者**: Bowen Wang
- **时间**: 2026-10-29T19:20:17Z
- **提交信息**: [Perf][EPLB][DSv4] Add a symm_mem weight-migration backend and fuse MegaMoE replica mapping (#62009)

Signed-off-by: Bowen Wang <bowen@inferact.ai>
Co-authored-by: Juntian Liu <Juntianl777@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [dc45a5f](https://github.com/vllm-project/vllm/commit/dc45a5f552a8513b9f4bc5b2cde05f51b7543fa1)

- **作者**: Glen Messenger
- **时间**: 2026-10-29T18:15:31Z
- **提交信息**: [Doc] Add k8s-aibom to deployment integrations (#60899)

Signed-off-by: Glen Messenger <57537684+glenmessenger@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bc57dc9](https://github.com/vllm-project/vllm/commit/bc57dc9d5308a5b983326e17fe435b16c3bacc55)

- **作者**: Harry Mellor
- **时间**: 2026-10-29T18:15:06Z
- **提交信息**: [Transformers backend] Migrate OLMoE and fix MoE LoRA (#63384)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [bba4d9a](https://github.com/vllm-project/vllm/commit/bba4d9afec5caa9f23cfc5863727da0e298fe502)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-29T18:12:19Z
- **提交信息**: [ROCm] Revamp CI/release deployment: collapse image tiers, unify build pipeline (#61939)

Signed-off-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>
Signed-off-by: Eddie Zhou <edward.zhou@amd.com>
Co-authored-by: Andreas Karatzas <AndreasKaratzas@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Eddie Zhou <edward.zhou@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>

### [b91df5a](https://github.com/vllm-project/vllm/commit/b91df5a9f76a7b0b574e6918f31860484bdef231)

- **作者**: Harry Mellor
- **时间**: 2026-10-29T18:02:09Z
- **提交信息**: [Docs] Diff against the merge base in the docs build gate (#64554)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [98fc6da](https://github.com/vllm-project/vllm/commit/98fc6da9d7355d2cc85141980439fded9a5fb61c)

- **作者**: Canlin Guo
- **时间**: 2026-10-29T17:41:08Z
- **提交信息**: [Perf][DSv4.1] Gather the compressed KV once per KV-source group in prefill (#59131)

Signed-off-by: Canlin <canlinguosdu@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4541fcd](https://github.com/vllm-project/vllm/commit/4541fcdd837c15345087b45e9aa85f2a28b57883)

- **作者**: Srijan Upadhyay
- **时间**: 2026-10-29T17:07:49Z
- **提交信息**: [Doc] Add Scheduler section to V1 architecture overview (#38741)

Signed-off-by: Srijan Upadhyay <srjnupadhyay@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [6c71831](https://github.com/vllm-project/vllm/commit/6c71831f2505c27bc5ba2e0a5a31c2cb3652dd08)

- **作者**: Divakar Verma
- **时间**: 2026-10-29T17:07:44Z
- **提交信息**: [CI][ROCm][MoE] Add AITER_MOE_SORT_BACKEND MXFP4 DSV4 test coverage (#62976)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e3f03f4](https://github.com/vllm-project/vllm/commit/e3f03f4f895cbbeeccc2440ca27430df09b3b45d)

- **作者**: Divakar Verma
- **时间**: 2026-10-29T17:07:00Z
- **提交信息**: [ROCm][Tests] Un-skip AITER MXFP4 padding-matrix and token-padding tests (#62996)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [55b677b](https://github.com/vllm-project/vllm/commit/55b677b2d107db6394f47fc52694908ade09ba55)

- **作者**: waizuichougou
- **时间**: 2026-10-29T16:57:11Z
- **提交信息**: [Bugfix][KV Offload] Deduplicate in-flight partial-tail loads (#64400)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9957f74](https://github.com/vllm-project/vllm/commit/9957f74617cf3a00ebae40602371bb8291c46cfe)

- **作者**: Zohaib Moti
- **时间**: 2026-10-29T16:54:54Z
- **提交信息**: [Bugfix] Add chat template fallback for OpenVLA (#64362)

Signed-off-by: Zohaib Moti <zohaib.moti@amd.com>

### [d04560f](https://github.com/vllm-project/vllm/commit/d04560f56bd9d9a0e29b44ec2b0efa4e9338b37e)

- **作者**: Chun Fang
- **时间**: 2026-10-29T16:45:34Z
- **提交信息**: [Doc] DeepSeek-V4-Pro: add MI355X AgentX source profiles (#64322)

Signed-off-by: Chun Fang <chun.fang@amd.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d8fdf4f](https://github.com/vllm-project/vllm/commit/d8fdf4f61bb606e2eb216230cd821096b2a64d3e)

- **作者**: Nick Hill
- **时间**: 2026-10-29T16:41:38Z
- **提交信息**: [MRV2][PP] Fix spec-decode draft/sampled-token broadcast issues (#64458)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [0309891](https://github.com/vllm-project/vllm/commit/03098917ad67740d15a97ae0ce32ecc05fbb25a0)

- **作者**: Tomasz Zielinski
- **时间**: 2026-10-29T16:39:11Z
- **提交信息**: [Bugfix] Fail loudly instead of no-op NCCL weight transfer (#57022)

Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: Chendi.Xue <chendi.xue@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [de83f55](https://github.com/vllm-project/vllm/commit/de83f5584821f908f8aed04ad303b69572684893)

- **作者**: frida-andersson
- **时间**: 2026-10-29T16:36:10Z
- **提交信息**: [ROCm][DSv4.1] Lift the skinny-GEMM cap in the gfx942 draft lm_head test (#64532)

Signed-off-by: Frida Andersson <fanderss@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [971378f](https://github.com/vllm-project/vllm/commit/971378f4663271c74ed1c10ea1bdae5109863bef)

- **作者**: Robert Shaw
- **时间**: 2026-10-29T16:29:31Z
- **提交信息**: [Bugfix][Frontend] Probe non-jinja renderers for inline system message support (Anthropic API) (#63594)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [51be9ea](https://github.com/vllm-project/vllm/commit/51be9ea6a3a356b42e3b72a0fc6e8cb8c8975944)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-29T16:27:28Z
- **提交信息**: [Security] Enforce request template trust for structured decisions (#64503)

Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>

### [604b961](https://github.com/vllm-project/vllm/commit/604b961640ee2fed1f82abd7d640f2df45d69f9f)

- **作者**: saipakalapati
- **时间**: 2026-10-29T16:18:21Z
- **提交信息**: [Bugfix] Avoid eager torch.compile in Kimi K2.5 vision helper (#53011)

Signed-off-by: sai <saikumar@sais-MacBook-Pro.local>
Signed-off-by: saipakalapati <79748893+saichowdary007@users.noreply.github.com>
Signed-off-by: Rohan Potdar <rohanpotdar138@gmail.com>
Co-authored-by: sai <saikumar@sais-MacBook-Pro.local>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>
Co-authored-by: Rohan Potdar <rohanpotdar138@gmail.com>

### [28dd46d](https://github.com/vllm-project/vllm/commit/28dd46d791981ad062be76f6ed4f0b3e2938164a)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-29T16:17:19Z
- **提交信息**: [Perf][HiSparse] Fuse per-layer slot invalidation and shorten the all-resident resolver path (#60103)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a8a0520](https://github.com/vllm-project/vllm/commit/a8a0520e4336c1b212f980e4335c3a7e718949a4)

- **作者**: Akshay Babbar
- **时间**: 2026-10-29T16:14:57Z
- **提交信息**: [Bugfix] [Frontend] Preserve prompt_logprobs in /v1/completions/derender (#57990)

Signed-off-by: Akshay Babbar <19975437+akshay-babbar@users.noreply.github.com>
Co-authored-by: ZCode <agent@zcode.local>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4440f0e](https://github.com/vllm-project/vllm/commit/4440f0e2632abacbefd7690338b9eea91055034b)

- **作者**: Sohom chakraborty
- **时间**: 2026-10-29T15:57:33Z
- **提交信息**: [Bugfix][KV Offload] Make reset_cache re-entrant (#59099)

Signed-off-by: Sohom Chakraborty <16609933+sohom-cs@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4158395](https://github.com/vllm-project/vllm/commit/41583951088f77c0c2f2890ce089e8aaf4e6a5d5)

- **作者**: alberto
- **时间**: 2026-10-29T15:56:55Z
- **提交信息**: [Bugfix][KV Offload] Let idle P2P-only engines park (#63618)

Signed-off-by: Alberto Perdomo <aperdomo@redhat.com>
Signed-off-by: alberto <aperdomo@redhat.com>
Co-authored-by: Or Ozeri <or@ozery.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5a4f307](https://github.com/vllm-project/vllm/commit/5a4f307d9c6c75f4d5ad82c069ced8239cc73ed0)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-10-29T15:50:38Z
- **提交信息**: [MM] Move Nemotron VL image normalization to device (#57924)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Signed-off-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>
Co-authored-by: Brandon Pelfrey <bpelfrey@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [262eefc](https://github.com/vllm-project/vllm/commit/262eefc9f2ce6c4a04997757397e68b00b8de1f9)

- **作者**: Jee Jee Li
- **时间**: 2026-10-29T15:44:07Z
- **提交信息**: [Model] Support hybrid MegaMoE/TRT-LLM execution for Muse Spark NVFP4 (#64525)

Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>

### [9a0f9b4](https://github.com/vllm-project/vllm/commit/9a0f9b45df86b91664923ad076f27a50f69c4766)

- **作者**: Jakub Zakrzewski
- **时间**: 2026-10-29T15:08:32Z
- **提交信息**: [Bugfix][Pooling] Skip weight tying for omitted LM heads (#64019)

Signed-off-by: Jakub Zakrzewski <jzakrzewski@nvidia.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Taneem Ibrahim <taneem.ibrahim@gmail.com>

### [4a8c0da](https://github.com/vllm-project/vllm/commit/4a8c0da9e26c24c0d9d3d024be1a945ae7b3e2ff)

- **作者**: javieratomic
- **时间**: 2026-10-29T15:07:50Z
- **提交信息**: [KV Offload] Reject secondary tiers on engines that span nodes (#62930)

Signed-off-by: Javier López <59578422+javieratomic@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [24e80c2](https://github.com/vllm-project/vllm/commit/24e80c261428cc45200b28f77fd0e2fdc36a56a8)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-29T14:37:51Z
- **提交信息**: [CI/Build] Add nixl auto-label rule and assign topic owners (#64113)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Mistral Vibe <vibe@mistral.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5cdbd05](https://github.com/vllm-project/vllm/commit/5cdbd0520e15c22e76aaf75acc1f30f42c7cd4d9)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-10-29T14:33:27Z
- **提交信息**: [Docs] Add Mistral-Large-4-1T-A52B recipe (#64527)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [482e473](https://github.com/vllm-project/vllm/commit/482e473253dfeeb7af4badf5bf5174d04afc6743)

- **作者**: Kaloyan Naumov
- **时间**: 2026-10-29T14:23:45Z
- **提交信息**: [Bugfix][KV Offload] Pin a shared-prefix junction when a sparse group cuts the offload hit (#63566)

Signed-off-by: Kaloyan Naumov <knaumov@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a57d256](https://github.com/vllm-project/vllm/commit/a57d25617f6ac44003dd47464c4282be106cfbd7)

- **作者**: sungsoo ha
- **时间**: 2026-10-29T14:23:15Z
- **提交信息**: [Bugfix][KV Offload][OBJ] Don't lose a completed transfer when telemetry is unavailable (#63788)

Signed-off-by: Sungsoo Ha <sungsooh@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8d4c968](https://github.com/vllm-project/vllm/commit/8d4c96804bbde82abbacabb21c7094068e825e80)

- **作者**: Harry Mellor
- **时间**: 2026-10-29T14:22:30Z
- **提交信息**: [CI] Bump Transformers version to 5.21.1 (#64049)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [974927f](https://github.com/vllm-project/vllm/commit/974927f80416f333a69b6c25bfcafe0f48013a49)

- **作者**: Eugenio "Jay" Zuccarelli
- **时间**: 2026-10-29T14:17:48Z
- **提交信息**: [Bugfix][Parser] Stream DeepSeek V4/V3.2 string tool arguments incrementally (#58780)

Signed-off-by: Eugenio "Jay" Zuccarelli <11176606+jayzuccarelli@users.noreply.github.com>
Signed-off-by: Ben Browning <56071+bbrowning@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Ben Browning <56071+bbrowning@users.noreply.github.com>

### [cebe109](https://github.com/vllm-project/vllm/commit/cebe1097232eaaba46aeae230dfe0887c88f634f)

- **作者**: jonahsamost
- **时间**: 2026-10-29T14:14:29Z
- **提交信息**: [Spec Decode][GLM-5.3-Flash] Support adaptive verification (#60229)

Signed-off-by: jonah <jsamost@gmail.com>

### [491067f](https://github.com/vllm-project/vllm/commit/491067f445306bcb974984cce7cdf6c111364465)

- **作者**: liranschour
- **时间**: 2026-10-29T14:12:22Z
- **提交信息**: [Bugfix][KV Offload][P2P] Fault a peer whose source WRITE stalls (#64251)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [d0ab3ba](https://github.com/vllm-project/vllm/commit/d0ab3ba9b4b9bff3d4ed748e511e8933cd2467df)

- **作者**: milesial
- **时间**: 2026-10-29T14:12:08Z
- **提交信息**: [Perf][KV Offload] Avoid repeated hash-prefix scans (#59322)

Signed-off-by: Alexandre Milesi <milesial@users.noreply.github.com>
Signed-off-by: milesial <milesial@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [914d61f](https://github.com/vllm-project/vllm/commit/914d61fc538a84e8487cb16fe8241a70f6f4bf9e)

- **作者**: Thien Tran
- **时间**: 2026-10-29T13:53:45Z
- **提交信息**: [Perf] Qwen3.5 GDN: overlap in_proj_ba with in_proj_qkvz on the aux stream (#64425)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [d1ad431](https://github.com/vllm-project/vllm/commit/d1ad431de60f995585e75d66bb5bea55f313ca96)

- **作者**: Eric Schreiber
- **时间**: 2026-10-29T13:51:14Z
- **提交信息**: [Bugfix][Compile] Fix KV-cache corruption under whole-graph compile (revert #42129) (#64279)

Signed-off-by: Eric Schreiber <eric.schreiber@aleph-alpha-research.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [510d15c](https://github.com/vllm-project/vllm/commit/510d15c49e9858814ca868c3dbf0344e3d3b42b5)

- **作者**: roikoren755
- **时间**: 2026-10-29T13:40:47Z
- **提交信息**: [Bugfix][Model] Nemotron 3.5 Super VL: support the native transformers config (#64506)

Signed-off-by: Roi Koren <roik@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [429eb22](https://github.com/vllm-project/vllm/commit/429eb22788c80f713f1683b27a1d8bab0902332c)

- **作者**: Sohom chakraborty
- **时间**: 2026-10-29T13:38:09Z
- **提交信息**: [Bugfix][KV Offload] Do not offload the partially computed block of a request that finished with an error (#63937)

Signed-off-by: Sohom Chakraborty <16609933+sohom-cs@users.noreply.github.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8b286ac](https://github.com/vllm-project/vllm/commit/8b286ac2b40b7c3072dcf5f557185be1457d8027)

- **作者**: liranschour
- **时间**: 2026-10-29T13:37:11Z
- **提交信息**: [Bugfix][KV Offload][P2P] Prefill locally while a peer handshake is pending (#64501)

Signed-off-by: Liran Schour <lirans@il.ibm.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [31f173d](https://github.com/vllm-project/vllm/commit/31f173d26d93d3e268c541b624969ffc35829c49)

- **作者**: potatoi_G
- **时间**: 2026-10-29T13:34:35Z
- **提交信息**: [Bugfix][NIXL] Dedup transfer regions by (base_addr, block_len) (#57662)

Signed-off-by: 葛昊宇 <haoyu_ge@intsig.net>

### [f126668](https://github.com/vllm-project/vllm/commit/f1266682b26d5242e9ba00d2fb15a5c93a26a86a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-29T13:31:58Z
- **提交信息**: [Bugfix][ROCm][DBO] Create hipBLASLt handles in microbatch threads before graph capture (#64423)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [1ca0dfb](https://github.com/vllm-project/vllm/commit/1ca0dfb97612ce47e5632a72c4b9680fffd72e4e)

- **作者**: namgyu-youn
- **时间**: 2026-10-29T13:31:38Z
- **提交信息**: [Perf][GLM-5.3] Enable GLM low-latency BF16 GEMM on SM100 (#64481)

Signed-off-by: namgyu-youn <namgyu.dev@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e5571b9](https://github.com/vllm-project/vllm/commit/e5571b97fce27ae33243c40907807a993692709d)

- **作者**: Julien Denize
- **时间**: 2026-10-29T13:21:38Z
- **提交信息**: [Mistral] Use get_grammar_for_chat_request in MistralParser and require mistral-common 1.13.0 (#64169)

Signed-off-by: Julien Denize <40604584+juliendenize@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>

### [21db9ec](https://github.com/vllm-project/vllm/commit/21db9ecf2a6271ab7e745cbd5537fcc70bd69c99)

- **作者**: Yuanheng Zhao
- **时间**: 2026-10-29T13:21:24Z
- **提交信息**: [Model] Support Ming3-ASR (inclusionAI/Ming-3.0-asr-tiny) (#63585)

Signed-off-by: Yuanheng <jonathan.zhaoyh@gmail.com>
Co-authored-by: codex <codex@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [cf3f640](https://github.com/vllm-project/vllm/commit/cf3f6405b849f2b672d93af0c4cf4e5e6dc6bd1b)

- **作者**: jbottleson-nvidia
- **时间**: 2026-10-29T13:07:56Z
- **提交信息**: [Bugfix] Default Nemotron Omni mamba_ssm_cache_dtype to float32 (#63218)

Signed-off-by: Jeremy Bottleson <jbottleson@nvidia.com>
Signed-off-by: jbottleson-nvidia <jbottleson@nvidia.com>
Co-authored-by: Cyrus Leung <tlleungac@connect.ust.hk>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5cf5c8f](https://github.com/vllm-project/vllm/commit/5cf5c8fa6d13ea7bef6ad799e32760530beca88f)

- **作者**: Wenfei (Charles) Qi
- **时间**: 2026-10-29T13:01:00Z
- **提交信息**: [Bugfix][Quantization] Fix Humming FP8 linear for per-tensor/per-channel FP8 weights (#60163)

Signed-off-by: wenfei qi <ms1419344875@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [d83a7df](https://github.com/vllm-project/vllm/commit/d83a7df60aa34f80d88414789a452c0b85728d2e)

- **作者**: Shengliang Xu
- **时间**: 2026-10-29T12:55:57Z
- **提交信息**: [Model] Update RADIO vision encoder to match the current Transformers version (#58468)

Signed-off-by: Shengliang Xu <shengliangx@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [61a6f81](https://github.com/vllm-project/vllm/commit/61a6f8138fd81f89467af762dc1b74674f544300)

- **作者**: Yiliu Dong
- **时间**: 2026-10-29T12:51:03Z
- **提交信息**: [Bugfix][Bench] Aggregate DP running requests for profiling (#61777)

Signed-off-by: qianlihuang <yiliu.dong@qq.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5c19391](https://github.com/vllm-project/vllm/commit/5c19391400c58ae10feca2483f55c547df211715)

- **作者**: Vegetog
- **时间**: 2026-10-29T12:48:29Z
- **提交信息**: [Frontend] Support thinking_token_budget in the Responses API (#63896)

Signed-off-by: Vegetog <110553275+Vegetog@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [a1e2127](https://github.com/vllm-project/vllm/commit/a1e212757c409ce56a15109a7b1342eef4d814b1)

- **作者**: SIDDARTHA REDDY
- **时间**: 2026-10-29T12:46:35Z
- **提交信息**: [Bugfix][Rust Frontend] Rust vllm-bench accepts --max-concurrency 0 and hangs forever (Python rejects it since #54887) (#64390)

Signed-off-by: SIDDARTHA REDDY <75976672+SIDDARTHAREDDY8@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fb7def9](https://github.com/vllm-project/vllm/commit/fb7def9ef9fa27fb794f655fb993a41e0b9bfe0c)

- **作者**: Felix Li
- **时间**: 2026-10-29T12:39:55Z
- **提交信息**: [ROCm][Perf] Reuse compiled FlyDSL host launchers (#64008)

Signed-off-by: Felix Li <felix.li@amd.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [d8e6fbe](https://github.com/vllm-project/vllm/commit/d8e6fbe461f54ec17274fc49000e94d332347e6a)

- **作者**: Andrew Sansom
- **时间**: 2026-10-29T12:30:28Z
- **提交信息**: [Bugfix] Consume prompt embedding sentinel IDs before model execution (#64367)

Signed-off-by: Andrew Sansom <andrew@protopia.ai>
Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>

### [bfa4d6d](https://github.com/vllm-project/vllm/commit/bfa4d6d2ad7f39afd7c9baf8aa6435303f252f08)

- **作者**: aoshen02
- **时间**: 2026-10-29T12:06:55Z
- **提交信息**: [KV Connector] Support sleep mode with MooncakeStoreConnector (#59934)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Dakai An <77474977+andakai@users.noreply.github.com>

### [5082c45](https://github.com/vllm-project/vllm/commit/5082c45853ca93ae809c58255e6126cfe20c415f)

- **作者**: Rex Mingjiang Lee
- **时间**: 2026-10-29T11:44:30Z
- **提交信息**: [Docs] Add vllm-iluvatar to custom_op.md (#62500)

Signed-off-by: mingjiang.li <mingjiang.li@iluvatar.com>

### [ee1056b](https://github.com/vllm-project/vllm/commit/ee1056b3179adfd4523dfdceb87b0a079801b6f4)

- **作者**: freyfwt
- **时间**: 2026-10-29T11:38:42Z
- **提交信息**: [Doc] Fix MiniMax-M3 docstring cross-references (#64474)

Signed-off-by: freyfwt <freytian1996@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [3765000](https://github.com/vllm-project/vllm/commit/3765000a372042125f9a17c203558368a21f0803)

- **作者**: namgyu-youn
- **时间**: 2026-10-29T11:32:08Z
- **提交信息**: [Perf][Qwen3.8] Add SM100 skinny GEMM plans for TP=1 (#64482)

Signed-off-by: namgyu-youn <namgyu.dev@gmail.com>

### [3c39dda](https://github.com/vllm-project/vllm/commit/3c39dda2a5da9e4b71b5eb61db686bf669374569)

- **作者**: Sherif Waly
- **时间**: 2026-10-29T11:06:03Z
- **提交信息**: [Performance][KV Offload] Avoid zero-filling the SimpleCPUOffload host KV pool (#64345)

Signed-off-by: Sherif Waly <sherif.waly@mistral.ai>
Co-authored-by: Mistral Vibe <vibe@mistral.ai>

### [c1b7dff](https://github.com/vllm-project/vllm/commit/c1b7dffa1457f4ffe7eafb08092eb2505a9651e4)

- **作者**: Hexiang Wang
- **时间**: 2026-10-29T11:01:26Z
- **提交信息**: [Bugfix][KV Offload] Refresh CPU LRU for GPU-hit prefixes in eager SimpleCPUOffload (#62444)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [fa1cf1d](https://github.com/vllm-project/vllm/commit/fa1cf1d436a0364a230c56f8e2c53a3d5043d231)

- **作者**: Thien Tran
- **时间**: 2026-10-29T09:59:54Z
- **提交信息**: [Perf][GDN] Allocate GDN core output uninitialized, write FlashInfer prefill in place (#64419)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Kimi Code <noreply@moonshot.cn>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0d6f92a](https://github.com/vllm-project/vllm/commit/0d6f92ae7c83f1d338d1b6a742ebcd79ab0fc2bb)

- **作者**: Ayushman Singh
- **时间**: 2026-10-29T09:46:03Z
- **提交信息**: [Bugfix][Spec Decode] Don't specialize MRV2 logits-stats kernels on num_logits (#64137)

Signed-off-by: Ayushman Singh <40520701+ayush1399@users.noreply.github.com>

### [a0e31b7](https://github.com/vllm-project/vllm/commit/a0e31b7353cc46232e8a9152b883b14726a024ab)

- **作者**: qli88
- **时间**: 2026-10-29T09:27:22Z
- **提交信息**: [CI][ROCM][Bug] Elastic DP doesn't work with AITER-on (#63053)

Signed-off-by: Qiang Li <qiang.li2@amd.com>

### [34091a0](https://github.com/vllm-project/vllm/commit/34091a07c7d78230e54d53d92b66b125b0f21a26)

- **作者**: Yan Ma
- **时间**: 2026-10-29T08:55:05Z
- **提交信息**: [XPU] use multimodal_rotary_embedding xpu kernel for mrope (#59938)

Signed-off-by: Yan Ma <yan.ma@intel.com>
Co-authored-by: Kunshang Ji <kunshang.ji@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-30
**监控日期**: 2026-10-29
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7415
- **最后更新**: 2026-10-30T01:55:43Z

## 提交统计

- **昨日提交总数**: 24
- **提交者数量**: 18
- **主要提交者**: Sheng GAO, hac17, Armaan Amatya

## AI分析总结

# vllm-omni 昨日提交分析（1/1 批，共 24 条）

## 1. 主要更新类型

- **Bug 修复占比最高**（约 9 条）：涵盖视频流会话历史、MoE Triton 配置预热、CUDA/NPU 模型状态、NIXL 传输顺序、FLUX.2-dev 输入校验等。
- **功能新增**（约 6 条）：SAM 3/SAM 3.1 图像与视频分割、MiniMax-H3 ControlNet Union 服务、MXFP8/MXFP4 量化 checkpoint 加载、文本编码器 CPU offload 等。
- **CI/构建优化**（约 7 条）：集中在 ROCm 平台的 MI300/MI325 READY 测试矩阵调整，以及 Qwen3-Omni 构件裁剪。
- **性能优化**（2 条）：Omni 输出/空闲生成开销降低、Qwen3-Omni 音频编码器 CUDA Graph 捕获。
- **工程治理**：新增 committers 与 CODEOWNERS。

## 2. 关键变更点与项目方向的关系

- **多模态能力扩展**：SAM 3 系列（图像分割 + 视频概念分割跟踪）、MiniMax-H3 的 Fun ControlNet 与量化支持，直接服务于 README 宣称的"全模态模型服务"目标，补齐视觉理解与生成链路。
- **量化与显存优化**：MXFP8-DiT/MXFP4-TE checkpoint 加载、文本编码器 CPU offload 解锁 Cache-DiT，体现了"cheap serving"（低成本服务）的核心诉求——用更低显存跑更大模型。
- **平台兼容性**：大量 ROCm 提交（fail-closed 测试策略、VoxCPM2 音频默认行为）表明项目在积极拓展 AMD 硬件生态，不局限于 NVIDIA。
- **稳定性与正确性**：NIXL 传输顺序修复、Drama 3 NPU 状态修复、MoE Triton 配置预热，均针对分布式推理中易出错的边缘场景。

## 3. 对项目的影响和潜在意义

- **模型覆盖面显著拓宽**：SAM 3 视频分割是全新任务类型（从生成/对话扩展到感知任务），可能吸引更多 CV 与具身智能用户。
- **生产就绪度提升**：批量 CI 修复（HunyuanImage 超时、空 prompt 拒绝、流式视频历史修复）减少线上偶发故障。
- **社区治理成型**：CODEOWNERS 与新增 committers 意味着项目进入更规范的协作阶段，长尾 PR（如 #7479、#8093 等编号靠前的提交）开始被集中消化。
- **性能与成本平衡**：输出开销削减 + CUDA Graph 音频编码器 + 量化支持，三者叠加可显著降低单请求推理成本。

## 4. 值得关注的技术点

- **SAM 3 双提交**（图像 + 视频）：视频概念分割与跟踪是近期热门方向，与已有视频理解能力（MiniCPM-o 长视频识别修复）形成互补。
- **fail-closed CI 策略**：多条 ROCm 提交采用"选择性标记 + fail-close"模式，只保核心用例、维持命令预算，说明测试矩阵已膨胀到需要精细裁剪的规模。
- **AutoRound 量化加载**：Intel 参与贡献 MXFP4/MXFP8 支持，暗示跨厂商硬件协同在加深。
- **NIXL（NVIDIA 推理链路）传输顺序修复**：涉及多流写入依赖，是 GPU 异步编程的典型隐患，修复价值高。
- **AI 辅助开发痕迹明显**：多条提交 co-author 为 Claude/Cursor/Grok 等，反映项目已常态化使用 AI 工具辅助维护。

## 5. 结合项目背景对发展的影响

README 的定位是"人人可用的易、快、廉价全模态服务"。本批提交中：量化与 CPU offload 支撑"廉价"，CUDA Graph 与输出开销优化支撑"快速"，丰富的 bug 修复与 ROCm CI 覆盖支撑"人人可用"（硬件无门槛），而 SAM 3、ControlNet、多语音模型则持续兑现"全模态"承诺。总体看，项目正从"功能堆叠期"转向"质量与生态并重期"，同时社区治理结构也在同步完善，为后续稳定发布奠定基础。

## 详细提交记录

### [cfaf8a3](https://github.com/vllm-project/vllm-omni/commit/cfaf8a38248f72df495f2882758b88c597ce1e74)

- **作者**: Yi Liu
- **时间**: 2026-10-29T21:28:21Z
- **提交信息**: [AutoRound][Model][MiniMax-H3] support MXFP8-DiT and MXFP4-TE quantized checkpoint loading (#9363)

Signed-off-by: yiliu30 <yi4.liu@intel.com>

### [ca52db0](https://github.com/vllm-project/vllm-omni/commit/ca52db059e9f8614c688a9d92bf1da71805b4e15)

- **作者**: haic0
- **时间**: 2026-10-29T21:18:36Z
- **提交信息**: [CI/Build][ROCm] Add one-card worker GPU cases to MI300 READY (#9552)

Add a fail-closed NonBlocking MI325 lane for 32 one-card worker GPU cases while leaving R2-01 and its 1416-node collection unchanged.

### [5b23495](https://github.com/vllm-project/vllm-omni/commit/5b234955e0b81765020eae3a76a312a390e6955d)

- **作者**: haic0
- **时间**: 2026-10-29T20:34:49Z
- **提交信息**: [CI/Build][ROCm] Select marked Qwen3-TTS CustomVoice core cases on MI300 READY (#9550)

Fail-close the Blocking MI325 Qwen3-TTS READY job on four selected CustomVoice core cases while retaining the existing 30-minute command budget.

### [e45e43b](https://github.com/vllm-project/vllm-omni/commit/e45e43bcc1d49970e34916140eb51acd60c27563)

- **作者**: Armaan Amatya
- **时间**: 2026-10-29T19:24:57Z
- **提交信息**: [Bugfix] Keep streaming video session history text-only (#9568)

Signed-off-by: Armaan Amatya <armaanamatya2014@gmail.com>

### [e99d274](https://github.com/vllm-project/vllm-omni/commit/e99d274276b22698ead6666135374e048bc9b660)

- **作者**: Mesut Oezdil
- **时间**: 2026-10-29T18:50:11Z
- **提交信息**: [Model] Replace deprecated transformers config validators in Qwen3-TTS and VoxCPM2 (#9596)

Signed-off-by: mesutoezdil <mesudozdil@gmail.com>

### [1841fe6](https://github.com/vllm-project/vllm-omni/commit/1841fe6a952836794a5dc17e584372552c6d8d7d)

- **作者**: haic0
- **时间**: 2026-10-29T18:44:13Z
- **提交信息**: [CI/Build][ROCm] Select the marked async-engine abort case on MI300 READY (#9549)

Fail-close the existing Blocking MI325 Engine READY job on the marked async-engine abort test while retaining the 15-minute command budget.

### [5d365c0](https://github.com/vllm-project/vllm-omni/commit/5d365c0ceae568a7fd8c6a128c72ad1ccbe6342b)

- **作者**: haic0
- **时间**: 2026-10-29T17:49:15Z
- **提交信息**: [CI/Build][ROCm] Fail-close the Wan2.2 MI300 READY node (#9548)

Fail-close the existing Blocking Wan2.2 READY job on the one-card MI325 node while retaining the 40-minute command budget.

### [b69d123](https://github.com/vllm-project/vllm-omni/commit/b69d1238ecae24b4452b0800ee31b10ffc5e2ed8)

- **作者**: H.Z
- **时间**: 2026-10-29T16:09:59Z
- **提交信息**: [Model][Frontend] Add MiniMax-H3 Fun ControlNet Union serving (CTRL-01) (#7479)

Signed-off-by: Hu <hu.zhu@connect.polyu.hk>
Signed-off-by: H.Z <hu.zhu@connect.polyu.hk>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a74cb59](https://github.com/vllm-project/vllm-omni/commit/a74cb5976c15bd2547d622e38c77a71baefe92f5)

- **作者**: Inesh Reddy Chappidi
- **时间**: 2026-10-29T15:12:07Z
- **提交信息**: [Bugfix] Warm prefill-sized fused-MoE Triton configs at startup (#9499)

Signed-off-by: Inesh Reddy <ineshreddy249@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [46766eb](https://github.com/vllm-project/vllm-omni/commit/46766eb27f3eb8deeefa21c6edc3f52a5a407cf0)

- **作者**: NATURE
- **时间**: 2026-10-29T14:33:20Z
- **提交信息**: [Bugfix] Restore MiniCPM-o CUDA duplex long-video recognition (#9544)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [ee8be2d](https://github.com/vllm-project/vllm-omni/commit/ee8be2d0820c2dc30afd0c16f56ac9831ce93ba5)

- **作者**: 汪志鹏
- **时间**: 2026-10-29T14:14:26Z
- **提交信息**: [Model] SAM 3: video concept segmentation and tracking (#9579)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4ac72cc](https://github.com/vllm-project/vllm-omni/commit/4ac72cc5b8e46957c00f093b3e299a74bf4d3c14)

- **作者**: hac17
- **时间**: 2026-10-29T13:51:47Z
- **提交信息**: [Bugfix][ROCm] Expect VoxCPM2 v1 audio defaults off CUDA (#9561)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [838b809](https://github.com/vllm-project/vllm-omni/commit/838b8095bcecb95adb85c75e1e84754c2453b688)

- **作者**: Sheng GAO
- **时间**: 2026-10-29T13:39:27Z
- **提交信息**: [Bugfix][Diffusion] Reject empty prompt and num_inference_steps<=0 for FLUX.2-dev (#9580)

Signed-off-by: Cursor Agent <cursoragent@cursor.com>
Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: Cursor Agent <cursoragent@cursor.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [8f24d0b](https://github.com/vllm-project/vllm-omni/commit/8f24d0b88d540f6455394973700a97631c351050)

- **作者**: andyluo7
- **时间**: 2026-10-29T11:57:00Z
- **提交信息**: [CI/Build][ROCm] Add MiniCPM-o 4.5 offline, online, and duplex READY coverage (#7689)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: haic0 <149741444+haic0@users.noreply.github.com>
Co-authored-by: Grok 4.7 <noreply@x.ai>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [6c01325](https://github.com/vllm-project/vllm-omni/commit/6c01325db473a523136ca4fd38c1809da580853a)

- **作者**: Krzysztof Tomala
- **时间**: 2026-10-29T11:06:34Z
- **提交信息**: [Bugfix] Order NIXL transfers after the stream writes they depend on (#9422)

Signed-off-by: Krzysztof Tomala <ktomala@nvidia.com>
Co-authored-by: 汪志鹏 <wangzhipeng628@gmail.com>

### [1745eee](https://github.com/vllm-project/vllm-omni/commit/1745eeef64c603c16e982d05bf495770ecb85b19)

- **作者**: Harry Li
- **时间**: 2026-10-29T10:48:50Z
- **提交信息**: [Model][MiniMax-H3] Support optional text encoder CPU offload to unlock Cache-DiT (#8093)

Signed-off-by: Harry Li <harrymingh@gmail.com>

### [f898d96](https://github.com/vllm-project/vllm-omni/commit/f898d962bfe0d39e7fdfc3085abe7c10b902dcec)

- **作者**: amy-why-3459
- **时间**: 2026-10-29T10:15:50Z
- **提交信息**: [CI/Build] Remove MiniCPM-o Seed-TTS BF16 attention-cache test (#9181)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [cbf35fb](https://github.com/vllm-project/vllm-omni/commit/cbf35fb0ccf46c5d7ff740f74ebb6201e33c23a3)

- **作者**: amy-why-3459
- **时间**: 2026-10-29T09:23:02Z
- **提交信息**: [Bugfix] Keep Drama 3 on its NPU model state under Model Runner V2 (#9560)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [bbf1fe5](https://github.com/vllm-project/vllm-omni/commit/bbf1fe570cfd9cecc2fee799309e4162239f3483)

- **作者**: amy-why-3459
- **时间**: 2026-10-29T08:49:56Z
- **提交信息**: [Core] Reduce Omni output and idle generation overhead (#9526)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [de2c39b](https://github.com/vllm-project/vllm-omni/commit/de2c39b9a04e7d4fa08b8b4acb0f54912f227358)

- **作者**: 汪志鹏
- **时间**: 2026-10-29T08:46:56Z
- **提交信息**: [Model] Add SAM 3 / SAM 3.1 promptable image segmentation (#9543)

Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [3266a6f](https://github.com/vllm-project/vllm-omni/commit/3266a6fa4db50b239eb46eaf4ef238fec883e97b)

- **作者**: zzh
- **时间**: 2026-10-29T08:41:01Z
- **提交信息**: [Bugfix][CI] Raise HunyuanImage-3 online I2I stage init timeout (#9471)

Signed-off-by: zzh <943967662@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [b13f175](https://github.com/vllm-project/vllm-omni/commit/b13f175c97aa04f8b9de16bfee26aabd843fe6a7)

- **作者**: DanaerLee
- **时间**: 2026-10-29T08:08:53Z
- **提交信息**: [Perf][Qwen3-Omni] Capture the thinker audio encoder with CUDA graphs (part of #7452) (#9010)

Signed-off-by: MrlixiangWE <mrdanaer@gmail.com>
Co-authored-by: zijianc2 <157244773+zijianc2@users.noreply.github.com>
Co-authored-by: Yifan Tian <221685243+Sendoh-code@users.noreply.github.com>
Co-authored-by: amy-why-3459 <221522807+amy-why-3459@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [400be0b](https://github.com/vllm-project/vllm-omni/commit/400be0b02379980be0d780603363716082cd7407)

- **作者**: psv666
- **时间**: 2026-10-29T07:33:05Z
- **提交信息**: [CI/Build] Trim Qwen3-Omni artifacts and remove duplex Seed-TTS perf jobs (#9531)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [6b0efc8](https://github.com/vllm-project/vllm-omni/commit/6b0efc84fb1486fab22552e789a88b6b41b84eda)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-29T07:01:52Z
- **提交信息**: [Welcome] Add committers and CODEOWNERS: timzsu, haic0, ZhengWG, FayeSpica (#9564)

Signed-off-by: hsliuustc0106 <liuhongsheng4@huawei.com>

---
