# GitHub Stars 合并报告 - 2026-11-18

**合并日期**: 2026-11-19
**监控日期**: 2026-11-18
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


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2296
- **最后更新**: 2026-11-18T10:18:21Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: sunrise-bx, wcj99, zpl1n

## AI分析总结

**1. 主要更新类型**  
本次提交集中于功能新增与文档/基础设施优化，无Bug修复或性能优化。具体包括：新增NPU CI自动生成与GPU迁移辅助技能（工具链扩展）、Ascend产品名称标准化（文档一致性）、以及Ascend A5容器镜像构建（部署支持）。

**2. 关键变更点与项目方向的关系**  
- **NPU CI与GPU迁移技能**：通过自动化CI配置和迁移辅助工具，降低开发者在NPU（昇腾）与GPU环境间切换的门槛，直接服务于VeOmni“跨硬件扩展训练”的核心目标。  
- **Ascend A5容器镜像**：提供预配置的昇腾A5环境镜像，加速开发者在国产NPU上的上手流程，呼应项目“任意硬件支持”的愿景。  
- **Ascend产品名标准化**：统一文档术语，提升跨平台（尤其是华为昇腾生态）的开发者体验，体现项目对国产硬件生态的重视。

**3. 对项目的影响和潜在意义**  
- **扩大硬件兼容性**：强化了VeOmni在国产NPU（昇腾）上的可用性，吸引更多国内开发者和企业用户。  
- **降低使用门槛**：通过容器化部署和自动化CI，减少环境配置成本，促进社区贡献和跨平台协作。  
- **增强工程成熟度**：标准化文档和基础设施，为后续多硬件扩展（如更多NPU/加速卡）奠定基础。

**4. 值得关注的技术点**  
- **CI自动生成技能**：可能涉及配置模板或脚本自动化，体现项目对可扩展工程实践的关注。  
- **容器镜像构建**：需关注镜像是否支持多架构（如ARM+昇腾），以及与现有GPU镜像的互操作性。  
- **硬件抽象层设计**：提交暗示项目可能通过抽象层管理不同硬件后端，这是“任意硬件训练”的关键。

**5. 基于README背景对项目发展的影响**  
VeOmni旨在通过“模型中心分布式配方库”扩展多模态训练至任意硬件。本次提交虽未直接涉及多模态算法，但通过夯实国产NPU（昇腾）的基础设施，**强化了项目在多元硬件生态中的竞争力**。这有助于实现README中“Scaling Any Modality Model Training”的长期愿景，吸引更多资源并推动社区向更广泛的硬件平台发展。总体而言，这些提交是项目从“GPU优先”向“全硬件支持”战略过渡的重要一步，为后续多硬件协同训练提供了实践基础。

## 详细提交记录

### [1d75284](https://github.com/ByteDance-Seed/VeOmni/commit/1d75284a4a4e83dd9d6fd7d58edbd1a111c8ab69)

- **作者**: sunrise-bx
- **时间**: 2026-11-18T10:39:42Z
- **提交信息**: [agent, ci] feat: add NPU CI generation and GPU migration skills (#1298)

### [53a744a](https://github.com/ByteDance-Seed/VeOmni/commit/53a744aa6185a0e507c232ff7ec8894af2bacdf2)

- **作者**: zpl1n
- **时间**: 2026-11-18T08:27:50Z
- **提交信息**: [docs] chore: standardize Ascend product names (#1479)

### [a65e278](https://github.com/ByteDance-Seed/VeOmni/commit/a65e278d5a79e6036fe8d3ed03405e498ff4fd0d)

- **作者**: wcj99
- **时间**: 2026-11-18T06:20:22Z
- **提交信息**: [docker, ci, docs] feat: add Ascend A5 container image (#1475)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 3011
- **最后更新**: 2026-11-18T05:47:12Z

## 提交统计

- **昨日提交总数**: 7
- **提交者数量**: 3
- **主要提交者**: Musisoul, Yang Yong (雍洋), Bilang ZHANG

## AI分析总结

## 1. 主要更新类型

本次提交以 **Bug修复** 和 **功能适配** 为主，辅以 **技能配置更新**。具体分布：

- **Bug修复**：3项（稀疏注意力kernel预热、H3 KV历史限制、DPCache热身）
- **功能新增/适配**：1项（ComfyUI适配重构后的主分支 + H3草稿工作流）
- **配置/元数据更新**：3项（skills更新）

---

## 2. 关键变更点及与项目方向的关系

- **ComfyUI适配重构主分支（#1734）**：这是本次最大的变更。LightX2V近期对主分支进行了重构，此提交将 `lightx2v_comfyui` 插件同步适配，确保生态工具链不落后于核心框架。同时新增了H3工作流——生成四张480p草稿供用户在画布上选择，再以768p重新生成，这体现了**轻量高效视频生成**的核心理念：先低成本预览、再高质量输出。
- **RelayVSR小数倍上采样（1.5x、2.5x）**：扩展了超分工具的灵活性，满足不同分辨率适配需求。
- **H3 KV历史跨运动段限制（#1731）**：修复了长序列生成时KV缓存可能膨胀的问题，直接关系到视频生成的**显存效率和生成质量稳定性**。
- **Sol-attention稀疏kernel预热（#1732）** 和 **DPCache热身（#1729）**：均属于推理性能优化，减少首次调用延迟，提升推理吞吐。
- **skills更新（3次）**：可能是内部开发技能描述或CI配置的同步，无实质性功能影响。

---

## 3. 对项目的影响和潜在意义

- **生态完整性提升**：ComfyUI适配确保了用户友好的可视化工作流与最新主分支同步，降低了用户的迁移成本。
- **生成质量与效率双优化**：H3相关修复（KV限制、DPCache热身）直接改善了MiniMax-H3模型在实际推理中的稳定性和显存占用，使**低显存设备上的视频生成更可行**。
- **推理延迟降低**：稀疏attention kernel预热减少了冷启动开销，对批量或流式推理场景有实际收益。

---

## 4. 值得关注的技术点

- **"先草稿后精修"工作流范式**：H3工作流让用户以480p低成本预览四种候选，再选择性地以768p精修，这种交互模式在视频生成领域具有很好的用户体验价值。
- **KV历史管理策略**：跨运动段限制KV缓存是长视频生成中的关键优化，涉及注意力机制的工程实现。
- **稀疏注意力（Sol-Attention）的预热机制**：说明框架采用了动态稀疏计算，kernel预热是性能调优的细节体现。
- **主分支重构后的生态同步**：表明项目正在经历较大规模的架构调整，ComfyUI作为插件需主动跟进。

---

## 5. 对项目发展的整体影响

结合README中"Light Video Generation Inference Framework"的定位，本次提交体现了项目在**重构过渡期的稳定性维护**策略：一方面通过ComfyUI适配和工作流创新巩固用户生态，另一方面通过多项精细修复保障核心推理路径的可靠性。这些提交虽单个规模不大，但共同指向一个方向——**在保持轻量推理优势的同时，提升长视频生成的稳定性和用户交互体验**，为后续版本发布奠定基础。

## 详细提交记录

### [0b6805e](https://github.com/ModelTC/LightX2V/commit/0b6805e7c4b4907cd4c678aebaaf025cb75ea584)

- **作者**: Musisoul
- **时间**: 2026-11-18T12:01:55Z
- **提交信息**: Adapt lightx2v_comfyui to the refactored LightX2V main branch and add H3 draft regeneration (#1734)

1. Adapt lightx2v_comfyui to the refactored LightX2V main branch.
2. Add an H3 example workflow that generates four 480p drafts and lets
users select one on the canvas to regenerate at 768p.
3. Support fractional RelayVSR upscale factors in ComfyUI, such as 1.5x
and 2.5x.

### [36291e7](https://github.com/ModelTC/LightX2V/commit/36291e76af8af7e36fcdb1542cb43f4661f3bd52)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-18T11:50:52Z
- **提交信息**: update skills (#1733)

### [005bc49](https://github.com/ModelTC/LightX2V/commit/005bc4929bac3fc6d01e9a8af5954bfad0af2e02)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-18T11:43:23Z
- **提交信息**: fix(sol-attn): warm up the sparse kernel (#1732)

### [3f95348](https://github.com/ModelTC/LightX2V/commit/3f95348949234984c13ca85c1834566f60c20d3d)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-18T10:45:09Z
- **提交信息**: fix: limit H3 KV history across motion segments (#1731)

### [af5a7f0](https://github.com/ModelTC/LightX2V/commit/af5a7f0fdac8c0424639d57338e181345b7738c7)

- **作者**: Bilang ZHANG
- **时间**: 2026-11-18T09:10:31Z
- **提交信息**: fix(minimax-h3): allow warmup with DPCache (#1729)

### [fc646ec](https://github.com/ModelTC/LightX2V/commit/fc646ec128a3170e0ce3282fe9578695691407ca)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-18T04:49:01Z
- **提交信息**: update skills (#1727)

### [691ebad](https://github.com/ModelTC/LightX2V/commit/691ebad3cd71c70be7c197dfdd99198ffb5e11b6)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-11-18T04:30:40Z
- **提交信息**: update skills (#1726)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2336
- **最后更新**: 2026-11-18T08:39:27Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Bubbliiiing

## AI分析总结

# VideoX-Fun 昨日提交分析

## 1. 主要更新类型
本次提交属于**性能优化与功能增强**的混合型更新，涵盖了推理加速、内存管理和推理模式改进等多个方面。

## 2. 关键变更点与项目方向的关系

- **EMA 模型更新（taehv）**：对 Taehv 模型的指数移动平均权重进行了更新，这直接关系到视频生成质量的提升。EMA 在扩散模型中用于稳定训练输出，说明团队在持续打磨模型的生成质量。
- **GPU 内存模式更新**：优化了显存使用策略，使模型在有限的 GPU 资源下能更高效运行。这对 VideoX-Fun 这类视频生成项目至关重要，因为视频生成模型通常对显存需求极高。
- **One-Forcing 推理模式**：引入或优化了 One-Forcing（单步/少步推理）模式，这意味着在推理时可以用更少的采样步数获得可接受的结果，大幅缩短生成时间。

## 3. 对项目的影响和潜在意义

- **降低使用门槛**：GPU 内存优化让更多普通开发者和研究者能在消费级显卡上运行视频生成模型，扩大了项目受众。
- **提升推理效率**：One-Forcing 模式显著降低了推理时间成本，使实时或近实时视频生成成为可能，这对视频生成的实用化部署意义重大。
- **质量与速度的平衡**：EMA 权重更新与少步推理的结合，体现了团队在"质量-速度-成本"三角中寻找更优平衡点的持续努力。

## 4. 值得关注的技术点

- **EMA 策略在视频扩散模型中的作用**：Taehv 模型采用 EMA 机制，这是扩散模型训练中稳定输出的经典手段，其更新细节可能包含权重衰减率或更新策略的调整。
- **One-Forcing 推理技术**：这可能是对一致性模型（Consistency Model）或蒸馏类加速方法的应用，值得深入研究其实现原理。
- **显存优化的具体策略**：可能涉及梯度检查点、模型分片、或量化推理等技术，对资源受限环境的部署有参考价值。

## 5. 对项目发展的整体影响

结合 README 中展示的项目定位——VideoX-Fun 是阿里 PAI 团队推出的视频生成系列项目（涵盖 CogVideoX-Fun 和 Wan-Fun 等模型），本次提交体现了团队从"能生成"向"生成得更好、更快、更省资源"的方向演进。这些更新有助于项目在开源视频生成社区中保持竞争力，同时为 Hugging Face Space 等在线演示平台提供更流畅的用户体验。项目的多语言支持（英、中、日）也表明其面向国际社区的开放战略，持续的性能优化将直接提升全球开发者的使用体验。

## 详细提交记录

### [395f1dc](https://github.com/aigc-apps/VideoX-Fun/commit/395f1dc5b7c361c865e6a729bd0570cbea1c5ddb)

- **作者**: Bubbliiiing
- **时间**: 2026-11-18T14:41:12Z
- **提交信息**: Update the ema model of taehv && Update new mode in gpu memory mode && Update One Forcing (#529)

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6961
- **最后更新**: 2026-11-19T02:34:00Z

## 提交统计

- **昨日提交总数**: 38
- **提交者数量**: 25
- **主要提交者**: Cindy Zhang, Bastian Hagedorn, Brian K. Ryu

## AI分析总结

# FlashInfer 近期提交综合分析

## 一、主要更新

近期变更集中在四条线上：**性能优化**（SM120 小批量 GEMM 的 swap-AB 换位、块稀疏注意力 epilogue、按专家 L2 缓存策略、GDN 序列切分与 Thor 加速）、**功能新增**（batch-invariant KDA/GDN 算子、SM107 NVFP4 MegaMoE 后端、FP8 split-KV MLA 解码、Windows arm64 构建、RL 用 `fc2_input_out` 输出、NVLS barrier 原语）、**Bug 修复**（CUTLASS MoE 非连续张量、DSMEM 集群内存序、E4M3 精度丢失、cuDNN 图生命周期与 SM120 NaN、autotuner 缓存覆盖、CI bot 命令误杀）以及**测试与基础设施加固**（跨平台断言适配、MoE cuDNN 图回归测试）。

## 二、关键变更与项目方向

- **确定性推理主线**：batch-invariant 模式从注意力推广到线性注意力 KDA 与 GDN，配合 Rubin 平台的 makespan 调度模型和程序化依赖启动（PDL），持续兑现位级一致的可复现推理承诺。
- **新硬件与平台铺开**：SM107（Rubin）MegaMoE 后端、SM110（Jetson Thor）GDN prefill、多 die locality domain、Windows arm64 构建与测试适配，保持对 NVIDIA 新架构的同步覆盖并降低多平台贡献门槛。
- **MoE/MLA 深水区优化**：MoE GEMM 栈引入分层 L2 缓存策略与分步输出，MLA 新增 FP8 split-KV 解码与波次感知 mega dispatch。
- **正确性优先**：MoE 非连续张量修复消除静默数据错误；集群作用域内存序六处统一修复；E4M3 行最大值精确计算以约 7% 性能代价换取 36–45% 精度恢复；cuDNN 图在缓存淘汰后被过早释放的问题在 5 个执行函数中补充 `_retain_cudnn_graph_if_capturing(graph)`，修复 BF16×FP4 GEMM 与 MoE grouped GEMM 图重放崩溃，并补充回归测试。

## 三、项目影响

解码路径在低延迟场景获得 1.5–3.3 倍级提速（SSD 状态槽位 geomean 2.10x、长序列 GDN 最高 3.31x、Thor 上 2.6–8.4x）；vLLM 在 Jetson Thor 不再回退 Triton，状态池槽位与多缓存调参降低集成摩擦；可合并 softmax 统计量直接服务 TensorRT-LLM 分区合并；RL 量化输出暴露将影响力从推理扩展到训练侧。稳定性方面，修复了 `CUDNN_CUDA_GRAPH_RETENTION=none` 或旧版 frontend 配置下的重放崩溃，增强生产可靠性；Windows arm64 适配扩大生态覆盖。需注明的破坏性变更是 `disable_split_kv` 在 CUDA-core decode 下改为显式抛错。

## 四、值得关注的技术点

swap-AB 变换（Dᵀ=Bᵀ·Aᵀ，scale 指针随操作数交换）与 wave 门控调度是低延迟 GEMM 的通用技巧；`st.async`+`mbarrier::complete_tx` 的集群内存序模式易错，统一修复体现深度把控；GDN batch-invariant 如实披露 decode 受状态读取限制的劣势区间并给出硬件归因；FP8 量化下 softmax 统计的 lazy correction 需要精确行最大值兜底；CUDA 图捕获会复制 cuDNN plan 的宿主缓冲区，图被淘汰后缓冲区释放导致 `cudaErrorIllegalInstruction`，且未文档化的 `CUDNN_ENABLE_DEFAULT_KERNEL_CACHE=0` 会暴露该缺陷；测试断言需考虑各平台 CUDA 错误输出格式差异。

## 五、总结

这些提交显示 FlashInfer 正从"内核集合"演进为系统级推理基座：纵向上覆盖 SM90–SM120 全谱系与 Windows 平台，横向上与 vLLM、TensorRT-LLM 深度绑定，同时通过正确性修复、资源生命周期治理、CI 门禁加固与回归测试补齐工程成熟度短板。项目在保持性能领先的同时，把重心部分转向大规模生产部署的可靠性与可维护性，巩固其作为生产级推理基础设施的可信度，也为后续功能迭代奠定稳固基础。

## 详细提交记录

### [e65caf5](https://github.com/flashinfer-ai/flashinfer/commit/e65caf5cbb90cbc1a6e90ad6aab1c38ff8132291)

- **作者**: Andreas
- **时间**: 2026-11-18T21:25:35Z
- **提交信息**: perf(gemm): swap-AB small-M tiles for the SM120 FP8 groupwise GEMM (#9464)

<!-- .github/pull_request_template.md -->

## 📌 Description

On SM120/SM121, `gemm_fp8_nt_groupwise` runs one 128×128×128 tile at
every `m`. At decode batch sizes most of that tile's rows are empty, and
it runs 1.59–1.88× slower than a swap-AB kernel at 1–32 tokens (#8702).

This PR adds swap-AB tiles for per-token scales (`scale_granularity_mnk
= (1, 128, 128)`):

| `m` | Tile |
|---|---|
| ≤ 32 | swap-AB 128×32×128 |
| 33–192 | swap-AB 128×64×128 (epilogue tile 128×32), when it needs no
more waves than 128×128 |
| otherwise | the existing 128×128×128 |

- **Swap-AB** computes Dᵀ = Bᵀ·Aᵀ: the weight goes in the A slot, the
tokens in the B slot, and the output is written column-major (n, m), the
same memory as row-major (m, n). Scale pointers and granularities swap
with the operands; `Sm1xxBlockwiseScaleConfig` builds SFA and SFB with
the same formula, so both `"MN"` and `"K"` scale layouts read the same
memory as before. This is the same transform
`CutlassGroupwiseScaledGEMMSM100LowLatency` uses on SM100.
- **Cutoffs 32 and 192** come from a sweep on an RTX PRO 6000
Workstation Edition (188 SMs, 600 W TDP) at a 300 W power limit: the 10
FP8 linear shapes of Qwen3.8-27B-FP8 and Muse-Glimmer-30B-FP8-block, 34
token counts from 1 to 4096, five passes, every CUTLASS swap-AB and
non-swap tile that builds. Swap-AB 128×32 is the fastest tile up to 32
tokens on all 10 shapes, and 128×128 wins above 192. The 128/256 cutoffs
proposed in #8702 cost 5.7–6.7% more decode GEMM time than 32/192.
- **Wave gate.** A fixed 192 cutoff still runs up to 1.17× slower than
today's kernel at 112–128 tokens on n ≥ 14336, where the 64-wide token
tile needs one more wave. The dispatcher takes 128×64 only when
`ceil(tiles_64 / SMs) <= ceil(tiles_128 / SMs)`, with the SM count from
`cudaDeviceGetAttribute`.
- **No Split-K / Stream-K.** This keeps the PR to tile selection. At
1–32 tokens swap-AB alone reads the weights at 1.28–1.56 TB/s on every
shape except n = 256, where Split-K would help (2 CTAs on 188 SMs); that
can follow.
- **Unchanged:** the 128×128 kernel body (only renamed to
`CutlassGroupwiseScaledGEMMSM120Default`), its C = D aliasing and error
returns, the `(128, 128, 128)` granularity, `csrc/` and the JIT
instantiations.
- **Also affected:** per-tensor `bmm_fp8` and `mm_fp8` with the CUTLASS
backend on SM120/SM121 use this launcher with per-token scales, so they
take the same swap-AB tiles.

Before/after on an RTX PRO 6000 Blackwell Workstation Edition (188 SMs,
600 W TDP) at a 300 W power limit: GEMM time per forward, summed over
all FP8 linear layers of the model, ms, `"MN"` scales, bf16 output, cold
L2, CUDA graphs, median of 5 passes. `main` is the prebuilt FlashInfer
0.7.2 module and this PR is built from source; at m > 192, where the
code is identical, the source build alone runs 3% faster, so about 3% of
each speedup is the build.

| m | Qwen3.8-27B-FP8 `main` | this PR | speedup |
Muse-Glimmer-30B-FP8-block `main` | this PR | speedup |
|---|---|---|---|---|---|---|
| 1 | 27.9 | 15.8 | 1.76× | 33.8 | 17.8 | 1.90× |
| 8 | 29.1 | 16.2 | 1.79× | 34.4 | 18.2 | 1.89× |
| 32 | 27.6 | 16.6 | 1.67× | 33.3 | 18.4 | 1.81× |
| 64 | 28.2 | 19.4 | 1.46× | 34.3 | 22.1 | 1.55× |
| 96 | 29.6 | 26.4 | 1.12× | 35.5 | 29.7 | 1.20× |
| 128 | 30.4 | 27.2 | 1.12× | 36.3 | 30.7 | 1.18× |
| 160 | 45.9 | 40.5 | 1.13× | 51.4 | 44.0 | 1.17× |
| 192 | 47.2 | 41.5 | 1.14× | 52.8 | 45.0 | 1.17× |

Against SGLang's SM120 swap-AB kernel (`fp8_blockwise_scaled_mm`), timed
the same way at 300 W, this PR is within 2% at m ≤ 32 and m = 160–192
and 8–28% faster at m = 64–128. On @AbdullahMadoun's card at its default
600 W the sign of the m = 48–128 band reverses: his table puts this PR
1.17–1.26× over his branch there, and his branch tracks SGLang to within
1%. That is the clock effect in the Reviewer Notes, not a different
tile. Any change to that band is left to a follow-up.

End to end in SGLang, output tokens/s, random 1024-token prompts with
256 output tokens, `--fp8-gemm-backend flashinfer_cutlass` (`main`, this
PR) and `cutlass` (SGLang's kernel). DFlash uses 8 draft tokens.

| Model | Concurrency | `main` | this PR | speedup | `cutlass` |
|---|---|---|---|---|---|
| Qwen3.8-27B-FP8 | 1 | 29.9 | 48.2 | 1.61× | 48.3 |
| Qwen3.8-27B-FP8 | 4 | 99.4 | 151.1 | 1.52× | 153.8 |
| Qwen3.8-27B-FP8 | 16 | 301.1 | 412.4 | 1.37× | 417.7 |
| Qwen3.8-27B-FP8 | 64 | 675.3 | 761.5 | 1.13× | 754.9 |
| Qwen3.8-27B-FP8 + DFlash | 1 | 99.9 | 140.9 | 1.41× | 149.6 |
| Qwen3.8-27B-FP8 + DFlash | 4 | 312.9 | 392.0 | 1.25× | 373.7 |
| Muse-Glimmer-30B-FP8-block | 1 | 27.0 | 43.5 | 1.61× | 43.4 |
| Muse-Glimmer-30B-FP8-block | 4 | 91.0 | 141.9 | 1.56× | 145.9 |
| Muse-Glimmer-30B-FP8-block | 16 | 283.3 | 399.6 | 1.41× | 409.0 |
| Muse-Glimmer-30B-FP8-block | 64 | 683.8 | 785.8 | 1.15× | 787.1 |

To reproduce per shape with FlashInfer's benchmark, with the testlist
below saved as `flashinfer.bench_testlist.txt`:

```bash
python benchmarks/flashinfer_benchmark.py --testlist flashinfer.bench_testlist.txt --output_path before.csv   # on upstream main
python benchmarks/flashinfer_benchmark.py --testlist flashinfer.bench_testlist.txt --output_path after.csv    # on this branch
```

<details>
<summary><code>flashinfer.bench_testlist.txt</code>: the 10 FP8 linear
shapes × 13 token counts</summary>

```
# SM120 gemm_fp8_nt_groupwise: FP8 linear shapes of Qwen3.8-27B-FP8 and Muse-Glimmer-30B-FP8-block, decode batch sizes
## Qwen3.8-27B-FP8
--routine gemm_fp8_nt_groupwise --m 1 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 4 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 8 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 16 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 32 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 48 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 64 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 96 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 112 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 128 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 160 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 192 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 256 --n 5120 --k 6144 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k6144"
--routine gemm_fp8_nt_groupwise --m 1 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 4 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 8 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 16 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 32 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 48 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 64 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 96 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 112 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 128 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 160 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 192 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 256 --n 34816 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n34816 k5120"
--routine gemm_fp8_nt_groupwise --m 1 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 4 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 8 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 16 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 32 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 48 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 64 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 96 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 112 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 128 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 160 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 192 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 256 --n 5120 --k 17408 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n5120 k17408"
--routine gemm_fp8_nt_groupwise --m 1 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 4 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 8 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 16 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 32 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 48 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 64 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 96 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 112 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 128 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 160 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 192 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 256 --n 16384 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n16384 k5120"
--routine gemm_fp8_nt_groupwise --m 1 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 4 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 8 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 16 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 32 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 48 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 64 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 96 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 112 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 128 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 160 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 192 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
--routine gemm_fp8_nt_groupwise --m 256 --n 14336 --k 5120 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Qwen3.8-27B-FP8 n14336 k5120"
## Muse-Glimmer-30B-FP8-block
--routine gemm_fp8_nt_groupwise --m 1 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 4 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 8 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 16 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 32 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 48 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 64 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 96 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 112 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 128 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 160 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 192 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 256 --n 4096 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n4096 k6656"
--routine gemm_fp8_nt_groupwise --m 1 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 4 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 8 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 16 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 32 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 48 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 64 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 96 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 112 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 128 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 160 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 192 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 256 --n 256 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n256 k6656"
--routine gemm_fp8_nt_groupwise --m 1 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 4 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 8 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 16 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 32 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 48 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 64 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 96 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 112 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 128 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 160 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 192 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 256 --n 6656 --k 4096 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k4096"
--routine gemm_fp8_nt_groupwise --m 1 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 4 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 8 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 16 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 32 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 48 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 64 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 96 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 112 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 128 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 160 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 192 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 256 --n 39936 --k 6656 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n39936 k6656"
--routine gemm_fp8_nt_groupwise --m 1 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 4 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 8 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 16 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 32 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 48 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 64 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 96 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 112 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 128 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 160 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 192 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
--routine gemm_fp8_nt_groupwise --m 256 --n 6656 --k 19968 --scale_major_mode MN --backends cutlass --refcheck --case_tag "Muse-Glimmer-30B-FP8-block n6656 k19968"
```

</details>

Accuracy, GSM8K through SGLang with `--fp8-gemm-backend
flashinfer_cutlass` (`sglang.test.few_shot_gsm8k`, all 1319 questions, 5
shots, greedy):

| Model | `main` | this PR |
|---|---|---|
| Qwen3.8-27B-FP8 | 0.954 | 0.949 |
| Muse-Glimmer-30B-FP8-block | 0.920 | 0.921 |

AI assistance: the patch, tests and this description were written with
Claude Opus 5.5 and reviewed by me; I ran the GPU tests and benchmarks.

## 🔍 Related Issues

Part of #8702.

- Duplicate search (open PRs, 2026-11-13): none changes
`gemm_groupwise_sm120.cuh`. #7421 (raise on CUTLASS failure in SM120
groupwise launchers) merged on 2026-11-13 and edited
`csrc/gemm_groupwise_sm120.cu` and this PR's test file; this branch is
rebased onto it. #8137 adds autotuner tactics for the per-tensor SM120
`bmm_fp8` kernel, a different kernel. @AbdullahMadoun released the issue
to me in #8702 and offered to review on a PRO 6000. His branch
[`perf/sm120-swap-ab-groupwise-gemm`](https://github.com/AbdullahMadoun/flashinfer/tree/perf/sm120-swap-ab-groupwise-gemm)
(not a PR) adds swap-AB with TileN 32/64/96 plus Split-K/Stream-K and
changes `csrc/`; this PR keeps to tile selection, and Split-K/Stream-K
from his branch can follow it.
- #4409: the SM100 swap-AB path raced in its `cp.async` scale loads in
under 1% of calls. The SM120 collective loads scales the same way, so
the new test repeats every call 1000 times and compares bit for bit.

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
reviewers may adjust): `tests/gemm/test_groupwise_scaled_gemm_fp8.py
tests/gemm/test_bmm_fp8.py`

Public runners have no SM120 or SM121 GPU, so the SM12x cases in these
files skip there. Internal pipeline #82998278 ran
`tests/gemm/test_groupwise_scaled_gemm_fp8.py` and
`tests/gemm/test_bmm_fp8.py` on 09e2f56b5: 27 of 30 jobs passed,
including RTX PRO 6000 and Spark. Both VR NVL72 jobs on CUDA 13.4
stopped before producing a JUnit report, and H100 on CUDA 13.0 is
reported as Unknown.

- `test_fp8_groupwise_gemm_small_batch_size` now runs on SM120/121 as
well as SM100/103.
- New `test_fp8_groupwise_gemm_sm120_tile_selection`: `m` at every
boundary (1, 4, 17, 31, 32, 33, 64, 65, 128, 129, 192, 193, 256) × `n` =
256, 4096, 16384 × `"MN"` and `"K"` scales, `k` = 1024. On 188 or 170
SMs every `n` runs both swap-AB tiles, and n = 16384 also takes the
128×128 tile at m = 65–192, so both sides of the wave gate run. Each
case is checked against the reference, then repeated 1000 times and
compared bit for bit.
- New `test_fp8_groupwise_gemm_sm120_tile_selection_cuda_graph`: m = 96,
n = 4096, k = 1024, `"MN"` and `"K"` scales. The kernel is captured in a
CUDA graph and replayed twice, and each replay is checked against the
reference.
- A separate stress run: 4000 calls at each of 60 points on the swap-AB
tiles (m = 24–32 and 48–192, n = 256 and 4096, k = 4096, both scale
layouts), 240k calls in all, each compared bit for bit with the first
call's output: 0 of 240000 calls differ.
- On the RTX PRO 6000, `pytest tests/gemm/test_bmm_fp8.py` gives 6
passed, 1 skipped (`cute-dsl`, SM107 only). Its b = 16, m = 128 cutlass
case runs the 128×64 tile.
- On the RTX PRO 6000, `pytest tests/gemm/test_unified_gemm_fuzz.py -k
"test_unified_gemm_fuzz and (bmm_fp8_cutlass or bmm_fp8_auto)"` gives
118 passed. With the cutlass backend and l > 1, 11 cases run the 128×32
tile and 6 run the 128×64 tile. Each case is checked against the
reference and for bit-identical repeat runs.
- On the RTX PRO 6000, `pytest tests/gemm/test_mm_fp8.py -k cutlass`
gives 30 skipped, because this file only runs on SM10x. `mm_fp8` was not
called directly on SM120. With the cutlass backend it uses the same
SM120 runner as `bmm_fp8`, with l = 1.
- On the RTX PRO 6000, `pytest
tests/gemm/test_groupwise_scaled_gemm_fp8.py -k "small_batch_size or
sm120_tile_selection or unsupported_shape_raises"` gives 106 passed, 8
skipped: 4 min 35 s from empty caches, 244 s of it the JIT build of the
SM120 module, and 6.4 s once the modules are built; the 78
`sm120_tile_selection` cases with their 1000 repeats take 2.4 s of that.
The 8 skips are the cuTile `small_batch_size` cases with `"MN"` scales,
since cuTile takes `"K"` scales only.
- The existing `pytest
tests/gemm/test_groupwise_scaled_gemm_fp8.py::test_fp8_groupwise_gemm`
gives 262 passed, 738 skipped in 75 s: all 250 CUTLASS cases with
per-token scales (m = 128 runs a swap-AB 128×64 tile or 128×128
depending on the wave gate, m ≥ 256 the unchanged 128×128 path) and the
12 cuTile cases with `"K"` scales in its reduced shape grid. The skips
are the backends that do not run on SM120 (`trtllm`, `cute-dsl`) and the
cuTile cases outside its grid.

### How to test this branch

On an SM120 or SM121 GPU, in a Python environment with a CUDA 13 build
of PyTorch and pytest, with the testlist from the description saved as
`flashinfer.bench_testlist.txt`:

```bash
git clone --recursive -b perf/sm120-fp8-groupwise-swap-ab https://github.com/AndreasBis/flashinfer.git
cd flashinfer
pip install --no-build-isolation -e . -v
pip uninstall -y flashinfer-jit-cache flashinfer-jit-cache-sm120f
python -c "from flashinfer.jit.gemm import gen_gemm_sm120_module; spec = gen_gemm_sm120_module(); assert not spec.is_aot, 'a prebuilt gemm_sm120 would load instead of this branch'; print('builds from source into', spec.build_dir)"
pytest tests/gemm/test_groupwise_scaled_gemm_fp8.py -k "small_batch_size or sm120_tile_selection"
python benchmarks/flashinfer_benchmark.py --testlist flashinfer.bench_testlist.txt --output_path after.csv
```

Uninstall `flashinfer-jit-cache` first. FlashInfer loads a prebuilt
`gemm_sm120` from it before it compiles anything (`JitSpec.try_load`),
and a jit-cache of the same version as this branch holds the kernel
built from `main`, so the tests and benchmarks would pass on the old
kernel. The `python -c` line fails if that would happen. Without the
jit-cache, the first call compiles the module from this branch's header.

End to end in SGLang, install this branch into the SGLang environment
the same way, with `--no-deps`, and uninstall the jit-cache there too.
Then serve a 128×128 block-FP8 checkpoint with this kernel, and with
`--fp8-gemm-backend cutlass` for comparison:

```bash
python -m sglang.launch_server --model-path Qwen/Qwen3.8-27B-FP8 --fp8-gemm-backend flashinfer_cutlass
```

SGLang pins its own FlashInfer release, so the rest of FlashInfer then
runs at this branch's version.

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

1. **Measured at 300 W with another process on the card; the cutoffs may
differ elsewhere.** Every number here is from one RTX PRO 6000
Workstation Edition (600 W TDP) held at a 300 W power limit, the
end-to-end and GSM8K runs included. `nvidia-smi` sampled every 10 s
across the sweep gives 2455 samples with `power.draw` median 299.98 W,
p90 300.06 W, max 320.18 W: the card sat at its limit for the whole run.
SM clock over the same samples:

  | window | samples | SM clock p10 / p25 / median / p90 (MHz) | power |
  |---|---|---|---|
  | all | 2455 | 1110 / 1185 / 1657 / 2880 | 300.0 W median |
| `utilization.gpu` > 90% | 2105 | 1117 / 1185 / 1560 / 2872 | 300.0 W
median |
| the above, and power >= 295 W | 1788 | 1117 / 1170 / **1372** / 2430 |
300.0 W |
| the above, and power < 280 W | 291 | 2176 / 2872 / 2895 / 2895 | 210.4
W median |
| the above, and > 50 GiB held by another process | 1044 | 1117 / 1132 /
**1245** / 2141 | 300.0 W |
| the above, and < 20 GiB held | 1061 | 1222 / 1575 / 2190 / 2895 |
300.0 W |

The memory clock was 13365 MHz in every load sample. That is why the
memory-bound half of the data agrees with a 600 W card and the
compute-bound half does not. The agreement is per card, not per absolute
time: at m = 4 on 5120 × 17408 this card reaches 82% of the Workstation
Edition's 1792 GB/s, and @AbdullahMadoun's run on the Server Edition
reaches 84% of that card's 1597 GB/s — the same kernel at the same
efficiency on a narrower bus.

Where the GEMM waits on compute, his numbers run about 2× faster than
ours (SGLang's kernel on 5120 × 17408 at m = 256: 83.2 µs there, 166.5
µs here), and his 128×128 timings do not rise with `m` up to 256 while
ours do. 274 TFLOP/s against 548 TFLOP/s needs about 1165 MHz where his
card held 2.31–2.35 GHz, and 1372 MHz is the measured median of the
cap-bound samples, so the gap tracks the power limit and the co-resident
process (the two clock-bound rows above are the same kernel 8% slower in
clock) rather than the tile. His build also differs: CUDA 12.8 / PyTorch
2.11 on `nvcr.io/nvidia/pytorch:25.03`, against CUDA 13.x / PyTorch 2.14
here, and his gist notes SGLang's kernel in that run lost
`-DCUTE_USE_PACKED_TUPLE=1`.

What is owed is a re-run of the sweep at 450 W with SM clocks locked,
which decides the 33–128 boundary; it has not been run yet, and no
published 300 W FP8 GEMM measurement on this SKU was found to compare
against. Every comparison *inside* this PR is A/B on this one card in
this one state, so the tile selection is not affected — only the
comparison to his card is open. Above 192 tokens this PR runs exactly
what `main` runs. On his card his branch's swap-AB tiles also beat
128×128 at 193–256 tokens, which a follow-up with his Stream-K / TileN
96 dispatch can take. Timings of this PR on another RTX PRO 6000 would
help to confirm the cutoffs.
I verified every figure in that block against gpu.csv (2455 samples,
power 299.98/300.06/320.18 W, the six clock rows, memory clock 13365 MHz
in all 2105 load samples). The 1165 MHz and TFLOP/s arithmetic is the
handoff's, unchanged. The nvcr.io/nvidia/pytorch:25.03 / CUDA 12.8 /
torch 2.11 / lost-PACKED_TUPLE clause I re-confirmed from his gist
today.

2. **Fixed heuristic or autotuner tactics?** #8702 asked this and no one
answered yet. This PR uses a fixed rule because `gemm_fp8_nt_groupwise`
has no tuning path on SM120 today; the three tiles could become tactics
later, as #8137 does for `bmm_fp8`.

3. **No C operand in the swap-AB kernel.** `beta` is 0, so the swap-AB
epilogue is built with `ElementC = void`, as in
`CutlassGroupwiseScaledGEMMSM100LowLatency` and the kernel the sweep
measured. It costs no mainloop stage either way (nvcc: 4 stages for
128×32, 3 for 128×64, with or without C); the 128×128 path keeps its C =
D aliasing.

4. **SM count per call.** For 33 ≤ m ≤ 192 the dispatcher calls
`cudaGetDevice` and
`cudaDeviceGetAttribute(cudaDevAttrMultiProcessorCount)`, as `norm.cuh`
and `pos_enc.cuh` do; both are host-only and allowed during CUDA graph
capture.

5. **`m` not a multiple of 4** (the docstring asks callers to pad): the
swap-AB tiles handle any `m` up to 192; above that the 128×128 path
behaves as today. The test covers m = 17, 31, 33, 65, 129 and 193.



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

- **New Features**
- Added an alternative execution path for groupwise FP8 matrix
multiplication on supported hardware. Execution strategy now adapts to
workload size, including smaller matrix dimensions, while preserving the
existing path for other cases.
- **Tests**
- Expanded coverage to additional GPU generations and parameterized
workloads, including checks for result accuracy, repeatability across
runs, and correctness when captured and replayed in a CUDA graph.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a1e0200](https://github.com/flashinfer-ai/flashinfer/commit/a1e0200c1e5ab0a3e78031a09322f80762bcee01)

- **作者**: eigen
- **时间**: 2026-11-18T21:11:48Z
- **提交信息**: feat(cake_gdn): opt-in Cake GDN sequence split on SM100 and SM107 (#9669)

### [100465c](https://github.com/flashinfer-ai/flashinfer/commit/100465cbef8c257cd376348f00f3e07ab18aa5e2)

- **作者**: Brian K. Ryu
- **时间**: 2026-11-18T18:57:19Z
- **提交信息**: perf(batch_invariant): Rubin placements of the batch-invariant attention class -- the decode launch grid, PDL and more (#9622)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

Placements of the batch-invariant attention class
(`attn.bf16.d{64,128,256}` behind `batch_invariant=True` on the paged
decode, paged prefill and ragged prefill wrappers; #8590, then #9301's
prefill placements, which this PR stacks on). Every change here moves
work between warp roles, memories, launch shapes or planner choices and
keeps the class's numeric term: the three wrappers give the bits of
upstream main for every configuration (55 / 55 output dumps
byte-identical across the decode / prefill / ragged grids at D = 64 /
128 / 256), and the suite's invariance tests (determinism and graph
replay, batch permutation and sub-batch invariance, configuration
agreement over the whole space, paged prefill = ragged prefill = paged
decode, chunked and multi-token forms, sliding window) pass unchanged.
No spec, fingerprint or Lean term moves.

Changes:
* **Decode launch grid (`plan.py`).** The Swaps-body planner's unit-kind
rules are replaced by one makespan model with declared-empirical
per-head-dim constants: a persistent walk is launched on an integral
number of waves (`Plan.grid`, launched unless `AttnConfig.grid` is set),
all-fused against all-split with the fixup's cost in the model. 96-128
concurrent CTAs stream HBM at 12.0-12.3 TB/s where a full 212-CTA grid
reaches 11.1-11.9 and leaves a part-filled tail wave; batches of 10-16
requests fuse instead of splitting. A device-free test pins the
decisions at 212 / 148 / 1000 SMs.
* **Programmatic dependent launch into the attention kernel (`swaps/`,
`fixup.py`, `engine.py`, `wrappers.py`).** The attention kernel waits on
its predecessor (`griddepcontrol.wait` in the load warp before the first
TMA) and the fixup triggers at its start; the wrappers' `enable_pdl`
defaults from the device. Visible only in chained execution (below).
* **Paired placement fixes at D = 64 (`operands.py`, `correction.py`).**
One softmax instantiation per warpgroup under the paired placement (the
replicated-row instantiation sharing its code region made ptxas emit
7-10 stall cycles before every exponential), and 8-column correction
pieces under it (the ragged compile's correction spilled its per-tile
loop).
* **Per-head-dim register budget for the one-warpgroup body
(`operands.py`):** softmax 200 / correction 96 at D = 64, where the
correction stays spill-free; D = 128 keeps 192 / 128.
* **D = 64 pairing by GQA group (`engine.py`, `wrappers.py`):** the
paired placement for prefill and ragged batches from group 4, the
one-warpgroup body below and for decode; a test pins the table.
* **Hardware row maximum (`blocks/softmax.py`, `compile.py`,
`engine.py`):** `tcgen05.ld.red` takes the tile row maximum on the parts
that have it (sm_103 / sm_107) at D <= 128; the maximum is exact and
order-free, so the bits are the register tree's (pinned on finite and
non-finite rows).
* **Fixup geometry (`fixup.py`):** group fields read before the
dependent-launch wait, two rows per block at D <= 128.
* **The paired placement at D = 128 as an explicit configuration**
(`AttnConfig(q2=True, softmax_wgs=2, kv_slots=3)` on 328 KB parts, P
over S, three-slot ring; `blocks/mma.py`, `producer.py`, `kernel.py`):
bit-identical to the one-warpgroup body and tested, NOT a default
(slower on SM107: its per-tile chain is serial while the one-warpgroup
body overlaps the next QK with the softmax).


### Performance

Measured against upstream main with #9301 merged (74cb235c8) on Vera
Rubin (sm_107, 212 SMs), bf16, page 32, cold L2 (the L2 flushed before
every iteration), CUPTI kernel sums including the fixup kernel, 30
iterations, two interleaved passes agreeing within 1 %, the GPU
otherwise idle. "Fastest other backend" is the fastest
non-batch-invariant FlashInfer backend of the same cell on the same
machine (cute-dsl, trtllm-gen, cuDNN, prims-ts or auto), from the same
bench.

| regime | cells | main / this PR (geomean) | range | fastest other /
this PR (geomean) |
|---|---|---|---|---|
| D = 128 paged decode | 34 | 1.049 | 0.99 .. 1.15 (B >= 16 at L >= 8K:
1.07 .. 1.15) | 0.89 (B >= 16 cells 0.95 .. 1.03) |
| D = 128 decode, 4-step graph chains | 7 | 1.05 .. 1.13 per step | | |
| D = 256 paged decode | 12 | 1.046 | 0.99 .. 1.17 | 0.84 |
| D = 64 paged decode | 12 | 1.049 | 0.99 .. 1.20 | 0.76 |
| D = 128 paged prefill | 14 | 1.027 | 1.01 .. 1.05 | 0.80 |
| D = 128 ragged prefill | 14 | 1.034 | 1.01 .. 1.08 | 0.95 |
| D = 64 paged prefill | 8 | 1.044 | 1.02 .. 1.09 | 0.85 |
| D = 64 ragged prefill | 3 | 1.665 | 1.54 .. 1.83 | -- |
| D = 256 paged / ragged prefill | 8 / 3 | 1.000 / 1.001 | | 0.64 |



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

* **Performance**
* Attention workloads now use workload-aware planning to select work
partitioning and launch sizes.
* Paired attention is supported for head dimension 128, with
hardware-assisted row-maximum processing on supported devices.
* Swaps operations can use programmatic dependent launches, with an
option to control their use.
* **Compatibility**
* Kernel selection and compilation account for available device shared
memory.
* Paired-attention configuration selection covers additional eligible
prefill workloads and adapts to device capacity.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <34876120+Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: mingyangw <35635157+saltyminty@users.noreply.github.com>

### [d02fd66](https://github.com/flashinfer-ai/flashinfer/commit/d02fd66d3d8dea84c2168c4c3d13a625cd4dbc23)

- **作者**: eigen
- **时间**: 2026-11-18T18:39:36Z
- **提交信息**: perf(cake_sage_block_sparse_attention): overlapped tile epilogue for many-block rows and the SM103 tail split (#9648)

The Sage FP8 block-sparse attention kernels take FP8 E4M3 Q/K/V with
per-token Q scales, per-16-token K scales and per-channel V scales. They
select KV blocks block-sparsely. This PR adds a new attention build on
sm_100a and sm_103a. The build uses two S buffers (double-S) and hands
each tile's output merge and store to a separate warpgroup, so this work
overlaps the next tile. Rows with 23 to 127 selected KV blocks per row
run this build when the grid has at least one tile per SM. Below 23
blocks per row, it also replaces the default, split-QK and p3 builds in
some windows of selected blocks per row and tiles per SM.

On sm_103a only, a tail-split row (a row whose partial last wave is
split across 2 CTAs) runs a tail-split build with the same
separate-warpgroup epilogue. This applies to rows with 24 to 64 selected
blocks per row once the grid holds a tile per SM. sm_103a now also
splits rows with 24 to 31 selected blocks per row. On sm_100a, split
rows keep the existing tail-split build.

The softmax step in the existing builds also changed:
- The running row maximum is updated with a select.
- The double-S builds release a consumed S buffer one step later.
- On sm_103a, the double-S and p3 builds keep eight K/V stages in flight
instead of six.

Outputs have the same bits as main, with one exception: the sm_103a rows
with 24 to 31 selected blocks per row that are now tail-split. Those
rows sum a split tile in a different order. They stay within the
kernel's tolerances and give the same bits on every run.

Compared with the previous Cake version of this kernel (current
FlashInfer main), the speedup across all 36 measured rows per GPU is:

| GPU | combined API | quantize + attention |
|---|---:|---:|
| B200 | 0.999x to 1.099x | 0.998x to 1.099x |
| GB300 | 0.998x to 1.078x | 0.996x to 1.083x |

The largest combined-API gains on B200 are B8/H32/Hkv32/S4096 sel 23 at
1.099x, B1/H32/Hkv8/S4096 sel 16 at 1.091x, B8/H32/Hkv32/S4096 sel 11 at
1.070x and B8/H32/Hkv32/S4096 sel 16 at 1.068x. On GB300 they are
B1/H5/Hkv5/S4096 sel 24 at 1.078x, B1/H8/Hkv8/S4096 sel 24 at 1.061x,
B8/H32/Hkv32/S4096 sel 58 at 1.051x and B1/H40/Hkv40/S32768 sel 51 at
1.051x. The two sel 24 rows are rows that sm_103a now tail-splits.

No row on either GPU counts as slower. A row counts as slower only if
its median paired ratio exceeds 1 by more than the run-to-run noise and
this PR is slower in at least 14 of 16 rounds. These cells are below
1.000:
- B200: B1/H4/Hkv4/S4096 sel 5 at 0.998 (quantize + attention), and
B1/H32/Hkv8/S4096 sel 6 at 0.999 (combined API).
- GB300: B1/H32/Hkv8/S4096 sel 6 at 0.998 (combined API) and 0.999
(quantize + attention), and B1/H1/Hkv1/S4096 sel 32 at 0.996 (quantize +
attention).

Each of these cells is within 0.4 % of main, and that gap is smaller
than its noise figure. This PR is slower in at most 11 of 16 rounds for
each of them.

Latencies are medians over 16 paired rounds of CUDA graph replay.
"Combined API" is quantize + attention in one call. "Quantize +
attention" is two separate calls. Speedup is main latency divided by
this PR's latency, so a value above 1 means this PR is faster. `sel` is
the number of KV blocks selected per row. Head dim is 128. B, H, Hkv and
S are batch, query heads, KV heads and sequence length.

**NVIDIA B200 (sm_100a, 148 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B1/H8/Hkv8/S4096 | 5 | 23.90 | 23.84 | 1.003 | 23.93 | 23.79 | 1.006 |
| B1/H8/Hkv8/S4096 | 6 | 23.14 | 22.74 | 1.018 | 23.21 | 22.77 | 1.019 |
| B1/H8/Hkv8/S4096 | 7 | 25.42 | 24.86 | 1.023 | 25.43 | 24.85 | 1.023 |
| B1/H8/Hkv8/S4096 | 24 | 40.64 | 39.99 | 1.016 | 40.62 | 40.02 | 1.015
|
| B1/H8/Hkv8/S4096 | 32 | 47.42 | 46.46 | 1.021 | 47.46 | 46.55 | 1.020
|
| B1/H8/Hkv8/S4096 | 58 | 68.97 | 67.74 | 1.018 | 69.02 | 67.75 | 1.019
|
| B8/H32/Hkv32/S4096 | 6 | 464.04 | 462.95 | 1.002 | 464.03 | 462.81 |
1.003 |
| B8/H32/Hkv32/S4096 | 9 | 561.34 | 551.93 | 1.017 | 561.10 | 552.26 |
1.016 |
| B8/H32/Hkv32/S4096 | 10 | 550.87 | 548.05 | 1.005 | 550.77 | 548.12 |
1.005 |
| B8/H32/Hkv32/S4096 | 11 | 638.77 | 596.82 | 1.070 | 638.39 | 596.56 |
1.070 |
| B8/H32/Hkv32/S4096 | 16 | 729.71 | 682.99 | 1.068 | 729.81 | 684.09 |
1.067 |
| B8/H32/Hkv32/S4096 | 23 | 990.22 | 901.07 | 1.099 | 990.10 | 900.58 |
1.099 |
| B8/H32/Hkv32/S4096 | 32 | 1161.48 | 1087.34 | 1.068 | 1167.18 |
1098.06 | 1.063 |
| B8/H32/Hkv32/S4096 | 58 | 1889.69 | 1840.08 | 1.027 | 1863.09 |
1815.17 | 1.026 |
| B1/H40/Hkv40/S32768 | 51 | 2206.95 | 2113.85 | 1.044 | 2164.93 |
2143.16 | 1.010 |
| B1/H40/Hkv40/S32768 | 128 | 4911.60 | 4808.50 | 1.021 | 4918.01 |
4820.50 | 1.020 |
| B1/H40/Hkv40/S32768 | 256 | 9317.84 | 9191.22 | 1.014 | 9319.57 |
9195.25 | 1.014 |
| B2/H24/Hkv24/S16384 | 32 | 867.68 | 815.82 | 1.064 | 867.82 | 818.74 |
1.060 |
| B1/H2/Hkv2/S4096 | 6 | 12.32 | 12.29 | 1.002 | 12.38 | 12.19 | 1.016 |
| B1/H2/Hkv2/S4096 | 58 | 25.28 | 25.02 | 1.010 | 25.34 | 25.02 | 1.013
|
| B1/H4/Hkv4/S4096 | 5 | 15.87 | 15.87 | 1.000 | 15.84 | 15.87 | 0.998 |
| B1/H4/Hkv4/S4096 | 6 | 15.62 | 15.40 | 1.014 | 15.61 | 15.46 | 1.010 |
| B1/H4/Hkv4/S4096 | 58 | 41.55 | 40.58 | 1.024 | 41.57 | 40.54 | 1.025
|
| B1/H32/Hkv8/S4096 | 6 | 52.42 | 52.48 | 0.999 | 52.46 | 52.47 | 1.000
|
| B1/H32/Hkv8/S4096 | 16 | 88.66 | 81.24 | 1.091 | 88.72 | 81.22 | 1.092
|
| B1/H1/Hkv1/S4096 | 5 | 10.83 | 10.82 | 1.001 | 10.85 | 10.83 | 1.002 |
| B1/H1/Hkv1/S4096 | 6 | 10.70 | 10.54 | 1.015 | 10.67 | 10.54 | 1.012 |
| B1/H1/Hkv1/S4096 | 32 | 15.26 | 15.26 | 1.000 | 15.23 | 15.23 | 1.000
|
| B1/H1/Hkv1/S4096 | 58 | 18.82 | 18.62 | 1.011 | 18.78 | 18.54 | 1.013
|
| B1/H5/Hkv5/S4096 | 24 | 30.86 | 30.65 | 1.007 | 30.87 | 30.60 | 1.009
|
| B1/H5/Hkv5/S4096 | 32 | 35.78 | 35.22 | 1.016 | 35.68 | 35.18 | 1.014
|
| B1/H5/Hkv5/S4096 | 58 | 51.26 | 50.50 | 1.015 | 51.27 | 50.53 | 1.015
|
| B1/H16/Hkv16/S4096 | 9 | 44.28 | 43.03 | 1.029 | 44.21 | 43.01 | 1.028
|
| B1/H16/Hkv16/S4096 | 10 | 43.50 | 42.82 | 1.016 | 43.48 | 42.83 |
1.015 |
| B1/H16/Hkv16/S4096 | 11 | 48.81 | 46.34 | 1.053 | 48.89 | 46.38 |
1.054 |
| B1/H5/Hkv5/S8192 | 96 | 125.66 | 123.55 | 1.017 | 125.59 | 123.58 |
1.016 |

**NVIDIA GB300 (sm_103a, 152 SMs), CUDA 13.3 (torch
2.13.0a0+9186a08b2c.nv26.07)**

| shape | sel | main, combined API, graph (µs) | this PR (µs) | speedup
| main, quantize + attention, graph (µs) | this PR (µs) | speedup |
|---|---:|---:|---:|---:|---:|---:|---:|
| B1/H8/Hkv8/S4096 | 5 | 21.73 | 21.20 | 1.025 | 21.73 | 21.21 | 1.025 |
| B1/H8/Hkv8/S4096 | 6 | 21.63 | 21.10 | 1.025 | 21.52 | 21.12 | 1.019 |
| B1/H8/Hkv8/S4096 | 7 | 23.20 | 22.82 | 1.017 | 23.18 | 22.83 | 1.015 |
| B1/H8/Hkv8/S4096 | 24 | 34.53 | 32.55 | 1.061 | 34.52 | 32.55 | 1.061
|
| B1/H8/Hkv8/S4096 | 32 | 38.43 | 37.25 | 1.032 | 38.33 | 37.16 | 1.031
|
| B1/H8/Hkv8/S4096 | 58 | 54.13 | 52.28 | 1.035 | 54.13 | 52.30 | 1.035
|
| B8/H32/Hkv32/S4096 | 6 | 429.78 | 429.88 | 1.000 | 430.00 | 430.10 |
1.000 |
| B8/H32/Hkv32/S4096 | 9 | 514.77 | 501.83 | 1.026 | 514.91 | 501.91 |
1.026 |
| B8/H32/Hkv32/S4096 | 10 | 504.56 | 499.82 | 1.009 | 504.73 | 499.66 |
1.010 |
| B8/H32/Hkv32/S4096 | 11 | 549.74 | 536.70 | 1.024 | 549.70 | 536.87 |
1.024 |
| B8/H32/Hkv32/S4096 | 16 | 605.89 | 601.07 | 1.008 | 605.98 | 601.09 |
1.008 |
| B8/H32/Hkv32/S4096 | 23 | 776.39 | 754.28 | 1.029 | 776.35 | 754.35 |
1.029 |
| B8/H32/Hkv32/S4096 | 32 | 937.50 | 893.19 | 1.050 | 937.55 | 893.17 |
1.050 |
| B8/H32/Hkv32/S4096 | 58 | 1422.19 | 1352.64 | 1.051 | 1422.26 |
1352.20 | 1.052 |
| B1/H40/Hkv40/S32768 | 51 | 1639.64 | 1560.72 | 1.051 | 1639.70 |
1563.10 | 1.049 |
| B1/H40/Hkv40/S32768 | 128 | 3495.46 | 3445.19 | 1.015 | 3467.31 |
3409.80 | 1.017 |
| B1/H40/Hkv40/S32768 | 256 | 6651.31 | 6484.77 | 1.026 | 6657.02 |
6545.45 | 1.017 |
| B2/H24/Hkv24/S16384 | 32 | 700.94 | 669.58 | 1.047 | 700.90 | 669.62 |
1.047 |
| B1/H2/Hkv2/S4096 | 6 | 11.42 | 11.39 | 1.003 | 11.50 | 11.49 | 1.001 |
| B1/H2/Hkv2/S4096 | 58 | 20.75 | 20.60 | 1.007 | 20.80 | 20.57 | 1.011
|
| B1/H4/Hkv4/S4096 | 5 | 14.94 | 14.50 | 1.030 | 14.94 | 14.53 | 1.028 |
| B1/H4/Hkv4/S4096 | 6 | 14.78 | 14.35 | 1.030 | 14.78 | 14.37 | 1.029 |
| B1/H4/Hkv4/S4096 | 58 | 33.42 | 32.42 | 1.031 | 33.41 | 32.37 | 1.032
|
| B1/H32/Hkv8/S4096 | 6 | 47.39 | 47.50 | 0.998 | 47.48 | 47.51 | 0.999
|
| B1/H32/Hkv8/S4096 | 16 | 69.90 | 69.78 | 1.002 | 69.88 | 69.81 | 1.001
|
| B1/H1/Hkv1/S4096 | 5 | 10.04 | 9.81 | 1.023 | 10.02 | 9.84 | 1.018 |
| B1/H1/Hkv1/S4096 | 6 | 9.90 | 9.68 | 1.023 | 9.90 | 9.70 | 1.021 |
| B1/H1/Hkv1/S4096 | 32 | 13.54 | 13.53 | 1.001 | 13.52 | 13.58 | 0.996
|
| B1/H1/Hkv1/S4096 | 58 | 15.98 | 15.79 | 1.012 | 15.94 | 15.79 | 1.009
|
| B1/H5/Hkv5/S4096 | 24 | 27.36 | 25.37 | 1.078 | 27.43 | 25.32 | 1.083
|
| B1/H5/Hkv5/S4096 | 32 | 29.48 | 28.64 | 1.029 | 29.49 | 28.66 | 1.029
|
| B1/H5/Hkv5/S4096 | 58 | 40.67 | 39.54 | 1.029 | 40.68 | 39.56 | 1.028
|
| B1/H16/Hkv16/S4096 | 9 | 40.97 | 40.03 | 1.023 | 41.20 | 40.22 | 1.024
|
| B1/H16/Hkv16/S4096 | 10 | 39.82 | 39.58 | 1.006 | 39.62 | 39.38 |
1.006 |
| B1/H16/Hkv16/S4096 | 11 | 43.08 | 42.29 | 1.019 | 43.50 | 42.60 |
1.021 |
| B1/H5/Hkv5/S8192 | 96 | 97.69 | 95.78 | 1.020 | 97.62 | 95.69 | 1.020
|

The same FP8 attention also runs on pre-quantized E4M3 inputs
(`bsa_attn_sm100_sage_fwd_cake`) or behind the fused BF16 quantizer
(`sage_fp8_quantize_sm100`, `bsa_attn_sm100_sage_quantize_fwd_cake`) on
sm_100a and sm_103a, and the family's INT8-QK / FP8-PV variant
(`bsa_attn_sm120_blk64_sage_fwd_cake`) ships for SM120.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added architecture-specific block-sparse attention variants, including
SDP3 and tail-split options for supported GPUs.
* Tail-split routes are selected when workload criteria are met and take
precedence over other specialized routes.
* **Performance**
* Updated routing to account for GPU architecture, block counts, and
occupancy.
  * Expanded attention pipelines for supported GPU architectures.
* **Bug Fixes**
* Improved handling of rows with no valid attention blocks and refined
softmax maximum updates.
* **Tests**
* Expanded coverage for routing, output consistency, determinism, and
architecture-specific builds.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [6a4e4d5](https://github.com/flashinfer-ai/flashinfer/commit/6a4e4d5c0f3827b4e4b82c6249f5198262a9e7a6)

- **作者**: eigen
- **时间**: 2026-11-18T18:38:09Z
- **提交信息**: feat(cake_gdn): several sequences per call in the opt-in Cake GDN sequence split (#9663)

The Cake GDN (Gated DeltaNet) chunked prefill
(`chunk_gated_delta_rule(..., backend="cake_gdn")`) has three routes.
They are the unsplit (non-CP) route, the context-parallel route
(`use_cp`), and the opt-in sequence split (`use_affine_split=True`). All
three take BF16 q/k/v with FP32 gates and state. The split route came in
#9628. It ran on SM103 only and took one sequence per call (N=1). With
this PR it takes any number of sequences per call (N >= 1). It is still
SM103 only, with head dim 128. It stays keyword-only, and the default
`False` is unchanged.

At N=1, this PR matches the shipped split from #9628 (0.99-1.02x). The
exception is 1K at shapes (2, 4) and (4, 8), at 0.94-0.95x. A sequence
of 960 tokens or fewer is now never split. The old cutoff was 1024
tokens, so these 1K sequences now split into 2 segments.

N>1 was rejected before, so there is no previous split to compare
against. The N>1 baselines are the unsplit route (`use_cp=False`) and
the context-parallel default (`use_cp=True`). With two long sequences
and 4 or 8 value heads, the split beats the unsplit route, by up to
1.88x at (2, 4), N=2, 8K. It is often slower than the context-parallel
default at long lengths. At N=4 it is slower than both baselines
wherever it splits. The one exception is (2, 4), 1K, where it is 1.10x
faster than the context-parallel default. With 16 or 32 value heads, it
never beats the unsplit route at N>1. So the split pays off mainly for
one or two long sequences per call.

The Cake GDN prefill also ships the unsplit and context-parallel routes,
with FP32 and aligned state layouts, on sm_100a, sm_103a and sm_107a.
The split route in this PR is sm_103a only.

**Table 1. N=1, this PR vs the shipped split from #9628.** NVIDIA GB300
(SM103, sm_103a), CUDA 13.4 (nvcc 13.4.92), driver 580.159.03, torch
2.14.1+cu130. CUDA graph, cold L2, median of 5 alternating groups × 50
replays. Two rounds were run, and the median of the two is shown. BF16
q/k/v, FP32 gates/state, initial state present, final state written,
`max_seqlen` passed. Latency is in µs. Shape is (num q heads, num v
heads), with head dim 128. T is tokens per sequence. P is segments per
sequence, and P=1 means one kernel. "P before" is the shipped split's
segment count. Ratio = baseline latency / this PR's latency, so a value
above 1 means this PR is faster. A **bold** ratio means this PR is
slower.

| Shape | T | P before | P | Shipped split (µs) | This PR (µs) | Shipped
/ this PR |
|---|---|---|---|---|---|---|
| (2, 4) | 1K | 1 | 2 | 31.03 | 33.02 | **0.94x** |
| (2, 4) | 2K | 4 | 4 | 36.67 | 36.57 | 1.00x |
| (2, 4) | 3K | 6 | 6 | 40.14 | 39.46 | 1.02x |
| (2, 4) | 4K | 8 | 8 | 44.27 | 44.21 | 1.00x |
| (2, 4) | 8K | 8 | 8 | 60.42 | 60.68 | 1.00x |
| (4, 8) | 1K | 1 | 2 | 31.04 | 32.61 | **0.95x** |
| (4, 8) | 2K | 4 | 4 | 39.92 | 38.98 | 1.02x |
| (4, 8) | 3K | 5 | 5 | 47.38 | 47.29 | 1.00x |
| (4, 8) | 4K | 5 | 5 | 56.59 | 55.74 | 1.02x |
| (4, 8) | 8K | 5 | 5 | 83.22 | 82.97 | 1.00x |
| (8, 16) | 1K | 1 | 1 | 31.38 | 31.29 | 1.00x |
| (8, 16) | 2K | 2 | 2 | 51.29 | 51.92 | **0.99x** |
| (8, 16) | 3K | 2 | 2 | 66.53 | 66.33 | 1.00x |
| (8, 16) | 4K | 2 | 2 | 82.21 | 81.82 | 1.00x |
| (8, 16) | 8K | 2 | 2 | 150.49 | 149.83 | 1.00x |
| (16, 32) | 1K | 1 | 1 | 31.87 | 31.88 | 1.00x |
| (16, 32) | 2K | 1 | 1 | 56.52 | 56.57 | 1.00x |
| (16, 32) | 3K | 1 | 1 | 81.22 | 81.29 | 1.00x |
| (16, 32) | 4K | 1 | 1 | 105.78 | 105.82 | 1.00x |
| (16, 32) | 8K | 1 | 1 | 204.22 | 204.15 | 1.00x |

**Table 2. N=2 and N=4, this PR vs the unsplit route (`use_cp=False`)
and the context-parallel default (`use_cp=True`).** NVIDIA GB300 (SM103,
sm_103a), CUDA 13.4 (nvcc 13.4.92), driver 580.159.03, torch
2.14.1+cu130. The measurement setup and the definitions of Shape, T, P
and ratio are the same as in Table 1. N is sequences per call, all of
length T. A **bold** ratio means this PR is slower than that baseline.

| Shape | N | T per seq | P | Unsplit (µs) | CP default (µs) | This PR
(µs) | Unsplit / this PR | CP default / this PR |
|---|---|---|---|---|---|---|---|---|
| (2, 4) | 2 | 1K | 2 | 31.08 | 41.91 | 36.86 | **0.84x** | 1.14x |
| (2, 4) | 2 | 2K | 4 | 54.94 | 52.67 | 40.28 | 1.36x | 1.31x |
| (2, 4) | 2 | 3K | 6 | 78.74 | 59.76 | 62.85 | 1.25x | **0.95x** |
| (2, 4) | 2 | 4K | 8 | 102.57 | 64.50 | 70.44 | 1.46x | **0.92x** |
| (2, 4) | 2 | 8K | 8 | 197.85 | 86.38 | 105.17 | 1.88x | **0.82x** |
| (2, 4) | 4 | 1K | 2 | 31.18 | 47.46 | 43.16 | **0.72x** | 1.10x |
| (2, 4) | 4 | 2K | 4 | 55.11 | 59.97 | 70.86 | **0.78x** | **0.85x** |
| (2, 4) | 4 | 3K | 6 | 79.16 | 69.59 | 100.78 | **0.79x** | **0.69x** |
| (2, 4) | 4 | 4K | 8 | 102.95 | 75.27 | 130.23 | **0.79x** | **0.58x**
|
| (2, 4) | 4 | 8K | 8 | 198.43 | 107.16 | 204.30 | **0.97x** | **0.52x**
|
| (4, 8) | 2 | 1K | 2 | 31.22 | 47.37 | 38.22 | **0.82x** | 1.24x |
| (4, 8) | 2 | 2K | 4 | 55.42 | 59.92 | 65.25 | **0.85x** | **0.92x** |
| (4, 8) | 2 | 3K | 5 | 79.53 | 69.31 | 78.42 | 1.01x | **0.88x** |
| (4, 8) | 2 | 4K | 5 | 103.40 | 75.34 | 95.58 | 1.08x | **0.79x** |
| (4, 8) | 2 | 8K | 5 | 199.35 | 107.27 | 151.92 | 1.31x | **0.71x** |
| (4, 8) | 4 | 1K | 2 | 31.66 | 51.46 | 63.86 | **0.50x** | **0.81x** |
| (4, 8) | 4 | 2K | 4 | 55.64 | 67.65 | 103.65 | **0.54x** | **0.65x** |
| (4, 8) | 4 | 3K | 5 | 80.01 | 92.33 | 151.18 | **0.53x** | **0.61x** |
| (4, 8) | 4 | 4K | 5 | 104.05 | 99.78 | 186.25 | **0.56x** | **0.54x**
|
| (4, 8) | 4 | 8K | 5 | 200.51 | 162.68 | 295.14 | **0.68x** | **0.55x**
|
| (8, 16) | 2 | 1K | 1 | 31.65 | 51.59 | 31.66 | 1.00x | 1.63x |
| (8, 16) | 2 | 2K | 2 | 55.98 | 67.63 | 88.27 | **0.63x** | **0.77x** |
| (8, 16) | 2 | 3K | 2 | 80.37 | 92.71 | 119.49 | **0.67x** | **0.78x**
|
| (8, 16) | 2 | 4K | 2 | 104.54 | 99.68 | 152.53 | **0.69x** | **0.65x**
|
| (8, 16) | 2 | 8K | 2 | 201.57 | 162.91 | 277.79 | **0.73x** |
**0.59x** |
| (8, 16) | 4 | 1K | 1 | 32.51 | 64.30 | 32.53 | 1.00x | 1.98x |
| (8, 16) | 4 | 2K | 2 | 56.90 | 96.32 | 143.36 | **0.40x** | **0.67x**
|
| (8, 16) | 4 | 3K | 2 | 81.39 | 128.64 | 191.99 | **0.42x** | **0.67x**
|
| (8, 16) | 4 | 4K | 2 | 105.81 | 159.15 | 242.54 | **0.44x** |
**0.66x** |
| (8, 16) | 4 | 8K | 2 | 203.45 | 285.37 | 446.98 | **0.46x** |
**0.64x** |
| (16, 32) | 2 | 1K | 1 | 32.94 | 64.22 | 32.98 | 1.00x | 1.95x |
| (16, 32) | 2 | 2K | 1 | 57.74 | 96.78 | 57.79 | 1.00x | 1.67x |
| (16, 32) | 2 | 3K | 1 | 82.62 | 128.96 | 82.59 | 1.00x | 1.56x |
| (16, 32) | 2 | 4K | 1 | 107.18 | 159.90 | 107.25 | 1.00x | 1.49x |
| (16, 32) | 2 | 8K | 1 | 206.06 | 286.98 | 206.04 | 1.00x | 1.39x |
| (16, 32) | 4 | 1K | 1 | 39.26 | 100.19 | 65.43 | **0.60x** | 1.53x |
| (16, 32) | 4 | 2K | 1 | 66.70 | 162.87 | 115.77 | **0.58x** | 1.41x |
| (16, 32) | 4 | 3K | 1 | 94.30 | 226.86 | 165.63 | **0.57x** | 1.37x |
| (16, 32) | 4 | 4K | 1 | 121.62 | 289.47 | 215.54 | **0.56x** | 1.34x |
| (16, 32) | 4 | 8K | 1 | 231.45 | 543.13 | 414.70 | **0.56x** | 1.31x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added support for running affine-split GDN prefill across multiple
sequences in a batch, with separate state handling for each sequence.
* Split planning adapts to the longest sequence and available
sequence-length information; sequences are split independently. The
default plan uses one segment through 960 tokens and two starting at
961.
* Empty-token batches are handled without launching a kernel.
One-segment runs use the unsplit path when supported; other cases use
the affine-split path.
* **Bug Fixes**
* Improved validation of sequence offsets, state layouts, and supported
batch limits, with clearer errors for unsupported inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [4a93672](https://github.com/flashinfer-ai/flashinfer/commit/4a936721275d5e0d50ff4cc08805669556885a5b)

- **作者**: eigen
- **时间**: 2026-11-18T18:29:03Z
- **提交信息**: feat(cake_ssd_combined): read and write states in a caller state pool by slot (#9644)

FlashInfer's Cake backend for the Mamba2 SSD combined prefill
(`ssd_combined_fwd(..., backend="cake")`) has three program families.
The first is an exact sequential scan, either fused or using precomputed
chunk state, with a tail variant. The second is a three-phase
chunk-parallel program, and the third is a look-back chunk-parallel
program. The families run on batched and packed-varlen layouts with
bf16, f16 or f32 SSM states. This PR adds the state-slot variant for
packed varlen. In one call, it reads initial states from a caller-owned
state pool and writes final and checkpoint states back into that pool in
place, using a per-sequence slot index. vLLM uses this layout for its
Mamba state cache. The baseline is the previous Cake SSD combined used
the way vLLM uses it today: gather the states, zero the rows without an
initial state, make one dense call, then scatter the states back.
Against that baseline, the slot call has a geomean speedup of 2.10x on
B200 (1.04x-4.10x), 2.10x on GB300 (1.04x-4.23x) and 2.68x on VR200
(1.05x-5.79x) over 48 shapes. It needs no extra device memory for
gathered or scattered copies.

The 17 new state-slot programs cover all three families and all three
state types, the dense Cake calls are unchanged, and the family ships on
sm_100a, sm_103a and sm_107a.

Mamba2 SSD combined prefill on NVIDIA B200 (sm_100a, CUDA 13.4), NVIDIA
GB300 (sm_103a, CUDA 13.4) and NVIDIA VR200 (sm_107a, CUDA 13.5). The
shapes are vLLM Nemotron-H Nano (64 heads) and Super (128 heads) per
tensor-parallel rank, with f32 state pools, head dim 64, state dim 128
and one checkpoint per sequence. **flow** is the gather, dense call and
scatter sequence on the previous Cake kernel. **slot** is one slot call
on the pool. Latencies are CUDA-graph medians in µs. Speedup = flow /
slot, and higher is better.

| Model | TP | Heads | Batch | Tokens | B200 flow (µs) | B200 slot (µs)
| B200 speedup | GB300 flow (µs) | GB300 slot (µs) | GB300 speedup |
VR200 flow (µs) | VR200 slot (µs) | VR200 speedup |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Nano | 1 | 64 | 8x2048 | 16384 | 266.8 | 209.7 | 1.27x | 246.7 | 195.2
| 1.26x | 158.6 | 107.0 | 1.48x |
| Nano | 1 | 64 | 64x512 | 32768 | 878.7 | 421.4 | 2.09x | 823.5 | 387.2
| 2.13x | 621.1 | 212.5 | 2.92x |
| Nano | 1 | 64 | 256x128 | 32768 | 2460 | 653.4 | 3.77x | 2342 | 605.4
| 3.87x | 1992 | 366.2 | 5.44x |
| Nano | 1 | 64 | 1024x1 | 1024 | 9385 | 2314 | 4.06x | 8993 | 2148 |
4.19x | 7626 | 1323 | 5.76x |
| Nano | 1 | 64 | 1x32768 | 32768 | 788.3 | 755.4 | 1.04x | 732.7 |
699.9 | 1.05x | 554.4 | 529.9 | 1.05x |
| Nano | 1 | 64 | 4x2048 + 60x(1-64) | 10011 | 832.6 | 374.9 | 2.22x |
833.0 | 394.7 | 2.11x | 602.6 | 192.4 | 3.13x |
| Nano | 2 | 32 | 8x2048 | 16384 | 147.6 | 111.7 | 1.32x | 138.2 | 106.2
| 1.30x | 95.8 | 67.0 | 1.43x |
| Nano | 2 | 32 | 64x512 | 32768 | 450.2 | 217.3 | 2.07x | 426.5 | 205.3
| 2.08x | 319.1 | 113.5 | 2.81x |
| Nano | 2 | 32 | 256x128 | 32768 | 1243 | 334.4 | 3.72x | 1186 | 308.5
| 3.85x | 1009 | 186.8 | 5.40x |
| Nano | 2 | 32 | 1024x1 | 1024 | 4722 | 1160 | 4.07x | 4518 | 1070 |
4.22x | 3840 | 669.0 | 5.74x |
| Nano | 2 | 32 | 1x32768 | 32768 | 775.9 | 744.2 | 1.04x | 723.8 |
693.1 | 1.04x | 320.6 | 297.2 | 1.08x |
| Nano | 2 | 32 | 4x2048 + 60x(1-64) | 10011 | 448.4 | 210.8 | 2.13x |
465.0 | 240.1 | 1.94x | 322.9 | 115.8 | 2.79x |
| Nano | 4 | 16 | 8x2048 | 16384 | 84.0 | 59.9 | 1.40x | 79.4 | 57.3 |
1.39x | 64.3 | 41.8 | 1.54x |
| Nano | 4 | 16 | 64x512 | 32768 | 232.4 | 114.7 | 2.03x | 220.2 | 108.2
| 2.04x | 161.5 | 60.7 | 2.66x |
| Nano | 4 | 16 | 256x128 | 32768 | 634.9 | 170.6 | 3.72x | 604.8 |
159.1 | 3.80x | 513.2 | 98.0 | 5.23x |
| Nano | 4 | 16 | 1024x1 | 1024 | 2381 | 581.2 | 4.10x | 2277 | 544.2 |
4.18x | 1941 | 340.3 | 5.70x |
| Nano | 4 | 16 | 1x32768 | 32768 | 274.2 | 253.5 | 1.08x | 255.6 |
234.4 | 1.09x | 175.0 | 151.7 | 1.15x |
| Nano | 4 | 16 | 4x2048 + 60x(1-64) | 10011 | 286.2 | 170.9 | 1.67x |
310.6 | 199.2 | 1.56x | 166.0 | 67.1 | 2.47x |
| Nano | 8 | 8 | 8x2048 | 16384 | 72.3 | 58.4 | 1.24x | 68.3 | 55.3 |
1.24x | 51.8 | 39.9 | 1.30x |
| Nano | 8 | 8 | 64x512 | 32768 | 126.7 | 68.6 | 1.85x | 119.4 | 65.2 |
1.83x | 89.2 | 39.8 | 2.24x |
| Nano | 8 | 8 | 256x128 | 32768 | 329.8 | 92.4 | 3.57x | 315.8 | 87.3 |
3.62x | 263.3 | 54.5 | 4.83x |
| Nano | 8 | 8 | 1024x1 | 1024 | 1211 | 301.2 | 4.02x | 1158 | 280.3 |
4.13x | 992.8 | 177.9 | 5.58x |
| Nano | 8 | 8 | 1x32768 | 32768 | 153.0 | 134.1 | 1.14x | 141.4 | 123.5
| 1.15x | 99.8 | 77.5 | 1.29x |
| Nano | 8 | 8 | 4x2048 + 60x(1-64) | 10011 | 144.7 | 87.0 | 1.66x |
135.0 | 83.0 | 1.63x | 101.5 | 53.4 | 1.90x |
| Super | 1 | 128 | 8x2048 | 16384 | 488.3 | 369.1 | 1.32x | 457.6 |
347.9 | 1.32x | 288.6 | 189.3 | 1.52x |
| Super | 1 | 128 | 64x512 | 32768 | 1731 | 832.3 | 2.08x | 1621 | 761.1
| 2.13x | 1212 | 409.7 | 2.96x |
| Super | 1 | 128 | 256x128 | 32768 | 4904 | 1296 | 3.78x | 4652 | 1192
| 3.90x | 3964 | 717.8 | 5.52x |
| Super | 1 | 128 | 1024x1 | 1024 | 18726 | 4641 | 4.04x | 17931 | 4307
| 4.16x | 15239 | 2633 | 5.79x |
| Super | 1 | 128 | 1x32768 | 32768 | 813.5 | 776.3 | 1.05x | 760.0 |
723.8 | 1.05x | 571.5 | 540.7 | 1.06x |
| Super | 1 | 128 | 4x2048 + 60x(1-64) | 10011 | 1525 | 626.8 | 2.43x |
1450 | 583.3 | 2.49x | 1119 | 306.0 | 3.66x |
| Super | 2 | 64 | 8x2048 | 16384 | 266.3 | 209.9 | 1.27x | 245.3 |
195.4 | 1.26x | 158.2 | 106.9 | 1.48x |
| Super | 2 | 64 | 64x512 | 32768 | 878.3 | 420.9 | 2.09x | 823.7 |
387.2 | 2.13x | 621.4 | 212.9 | 2.92x |
| Super | 2 | 64 | 256x128 | 32768 | 2452 | 653.4 | 3.75x | 2340 | 600.8
| 3.89x | 1992 | 359.8 | 5.54x |
| Super | 2 | 64 | 1024x1 | 1024 | 9384 | 2294 | 4.09x | 9002 | 2127 |
4.23x | 7637 | 1331 | 5.74x |
| Super | 2 | 64 | 1x32768 | 32768 | 787.9 | 755.5 | 1.04x | 732.7 |
699.9 | 1.05x | 554.3 | 530.2 | 1.05x |
| Super | 2 | 64 | 4x2048 + 60x(1-64) | 10011 | 830.4 | 373.5 | 2.22x |
830.3 | 391.7 | 2.12x | 602.9 | 193.0 | 3.12x |
| Super | 4 | 32 | 8x2048 | 16384 | 147.3 | 112.1 | 1.31x | 138.0 |
105.6 | 1.31x | 95.8 | 66.9 | 1.43x |
| Super | 4 | 32 | 64x512 | 32768 | 450.6 | 216.7 | 2.08x | 426.7 |
204.5 | 2.09x | 318.8 | 113.5 | 2.81x |
| Super | 4 | 32 | 256x128 | 32768 | 1247 | 332.9 | 3.74x | 1183 | 308.1
| 3.84x | 1009 | 186.3 | 5.42x |
| Super | 4 | 32 | 1024x1 | 1024 | 4722 | 1154 | 4.09x | 4517 | 1070 |
4.22x | 3840 | 672.4 | 5.71x |
| Super | 4 | 32 | 1x32768 | 32768 | 775.3 | 744.2 | 1.04x | 723.8 |
693.0 | 1.04x | 314.7 | 295.1 | 1.07x |
| Super | 4 | 32 | 4x2048 + 60x(1-64) | 10011 | 448.6 | 211.2 | 2.12x |
464.6 | 239.7 | 1.94x | 323.3 | 116.4 | 2.78x |
| Super | 8 | 16 | 8x2048 | 16384 | 83.3 | 59.8 | 1.39x | 79.6 | 56.7 |
1.40x | 63.7 | 41.9 | 1.52x |
| Super | 8 | 16 | 64x512 | 32768 | 232.3 | 114.9 | 2.02x | 220.2 |
108.5 | 2.03x | 160.1 | 60.6 | 2.64x |
| Super | 8 | 16 | 256x128 | 32768 | 636.5 | 171.4 | 3.71x | 604.8 |
158.6 | 3.81x | 513.4 | 98.7 | 5.20x |
| Super | 8 | 16 | 1024x1 | 1024 | 2386 | 582.9 | 4.09x | 2279 | 545.0 |
4.18x | 1940 | 342.7 | 5.66x |
| Super | 8 | 16 | 1x32768 | 32768 | 273.3 | 253.6 | 1.08x | 254.7 |
234.7 | 1.09x | 176.3 | 153.3 | 1.15x |
| Super | 8 | 16 | 4x2048 + 60x(1-64) | 10011 | 286.5 | 168.6 | 1.70x |
311.1 | 199.4 | 1.56x | 165.6 | 67.2 | 2.46x |


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added packed variable-length sequence support for sharing state pools
through per-sequence slots, with optional initial-state flags,
final-state pools, and checkpoint capture.
* Added state-pool options to the combined SSD APIs and tracing,
including caller-provided token-major outputs.
* Added benchmark options to compare slot-based results with dense
results and report separate timing.
* **Bug Fixes**
* Improved validation for slot inputs and overlapping state-pool
storage. Invalid or null initial slots use zero state; invalid or null
final slots skip writes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [f946321](https://github.com/flashinfer-ai/flashinfer/commit/f946321c43fe9960f02245072805d4054d37bec3)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-18T18:22:31Z
- **提交信息**: feat(batch_invariant): recurrent_kda(batch_invariant=True), the KDA class kda.bf16.c16 (#9294)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds the first linear-attention operator of the batch-invariant
mode (#8361): a keyword-only `batch_invariant: bool = False` on
`flashinfer.recurrent_kda`, backed by the class `kda.bf16.c16` in
`flashinfer/batch_invariant/kda/`. It depends on #8833 (fp32 state pools
for the recurrent KDA decode kernels), which is merged: the class takes
the same fp32 pool the frameworks already keep for KDA.

### Performance
**Ratio to today's fastest non-invariant KDA kernels (today's time / the
class's, geomean of the column's cells; above 1 the class is faster)**

| part | decode O(10), chunk average | decode O(100), chunk average |
completing step | prefill, whole chunks, 8+ sequences | prefill, single
sequence | prefill, ragged | multi-token | cells >= 0.80 (decode chunk
average / prefill / multi-token) |
|---|---|---|---|---|---|---|---|---|
| Vera Rubin NVL72 (SM107) | 0.75 | 1.00 | 0.37 | 0.95 | 0.57 | 0.62 |
0.65 | 6/10 / 6/14 / 13/32 |
| Vera Rubin NVL4 (SM107) | 0.68 | 0.95 | 0.35 | 0.94 | 0.57 | 0.62 |
0.65 | 5/10 / 6/14 / 12/32 |
| GB300 (SM103) | 0.68 | 0.96 | 0.34 | 0.95 | 0.64 | 0.69 | 0.69 | 5/10
/ 6/14 / 15/32 |
| GB200 (SM100) | 0.69 | 0.97 | 0.35 | 0.95 | 0.65 | 0.69 | 0.68 | 6/10
/ 6/14 / 14/32 |
| B200 (SM100) | 0.69 | 0.97 | 0.35 | 0.95 | 0.65 | 0.70 | 0.63 | 7/10 /
7/14 / 13/32 |

O(10) is batch 8 and 16, O(100) is batch 64, 128 and 256, with 16 and 32
heads; the chunk average is the measured time average over the 16 steps
of a chunk, which is what a request pays per token; the completing step
is the 16th. CUPTI GPU time with a cold L2, each cell in two fresh
processes with the variants in opposite orders; the protocol, the
baselines and every cell are under "Performance details" below.

Regimes: (1) the completing step (0.34 to 0.37) is the worst column on
every part: one step in sixteen reads the fp32 state and writes it and
its bf16 copy, 220 KB per (request, head) against 65.5 KB for today's
step; it is inside the chunk average, and a batch at unaligned phases
pays it in most launches (mixed phases: 0.64 to 0.68). (2) Decode at
O(10) (0.68 to 0.75) is a single wave of blocks and latency-bound: the
step has three rounds of cold loads where today's kernel has two; batch
1 pays the same chain (0.52 to 0.60). At O(100) the step is memory-bound
and moves fewer bytes than today's kernel on 15 of 16 steps (0.95 to
1.00). (3) Multi-token steps (0.63 to 0.69) are one launch that loops
over a request's tokens; by tokens per request the geomean is 0.73 to
0.84 at 2, 0.97 to 1.05 at 4, 0.65 to 0.70 at 8 and 0.35 to 0.37 at 16,
where the loop's chain is paid per token against today's chunked `[B,
T]` call. (4) Ragged prefill (0.62 to 0.70) is the prefill kernel on the
whole chunks plus one launch of the step kernel for the 0 to 15 tokens
past them, and staging between the two. (5) Prefill is today's kernel,
unchanged; the ratio is against `backend="auto"`, which does not always
run it the same way. With 8 or more sequences of whole chunks `auto`
takes the same route and the class adds one small launch that writes its
boundary state (0.94 to 0.95). With a single sequence (0.57 to 0.65)
`auto` switches to a two-kernel decomposition that is faster and gives
other bits, and the class keeps the one route so that a sequence's bits
do not depend on what shares its call.

**Why.** RL rollouts need the sampler's decode output of a token to
match the trainer's prefill output of the same token bit for bit. For
KDA they do not match today: prefill runs the chunked CuTe-DSL kernel on
an fp32 state, decode runs a rank-1 recurrence (on a bf16 or, since
#8833, an fp32 state) with another operation order, and the chunked
kernel itself has two routes (the two-kernel decomposition when `n_seq *
heads * 2 <= sm_count`, else the persistent engine) that give different
bits, so a request's prefill bits also depend on how many sequences
share its call.

**What the flag guarantees.** With `batch_invariant=True` a sequence's
output rows, and its state at every multiple of 16 tokens, are the
native SM100 / SM103 / SM107 chunked prefill kernel's on its pinned
`engine` route, from the sequence's own inputs and initial state alone:

| | Property | Meaning |
|---|---|---|
| R1 | Run-to-run determinism | same inputs: same bits, across processes
and CUDA-graph replay |
| R2 | Batch invariance | a sequence's bits do not depend on the batch
size, its neighbours, its position or its slot |
| R4 | Cross-path agreement | **prefill == chunked prefill == decode**
for the same token |

R3 is not claimed: the kernels are hand-written and expose no
configuration space; the class is one route of the prefill kernel plus
one decode kernel that computes the same term, and
`fingerprint("recurrent_kda")` digests both kernel sources, the decode
kernel's launcher and build flags, and the installed CuTe-DSL version
(so the identifier differs between environments with different DSL
builds).

**How.** The chunked prefill kernel is deterministic, batch-invariant
and prefix-stable, and resuming it from its own fp32 state is exact at
multiples of 16 tokens. Prefill is therefore that kernel, unchanged,
pinned to its engine route (`kda_prefill_cute.force_route`, internal;
the operator's automatic rule is untouched for everyone else). Decode is
a new step kernel (`include/flashinfer/kda/batch_invariant_decode.cuh`,
built through the nvcc JIT and registered for AOT): one launch per step,
one CTA per (request, head), reading and writing the pool directly. It
computes row `p` of the open 16-token chunk exactly as the prefill
kernel does: the same scalar chain for the gate, the decay and the l2
norms, and every tensor-core product (the two state projections, the
`KK` / `QK` row, the 16 x 16 inverse, the update column, the output row
and, on the 16th row, the state delta) issued as `mma.sync` from
registers with the prefill's operands, k-order and starting accumulator.
`mma.sync` and the prefill kernel's `tcgen05` products give identical
bits at every one of these shapes on SM100, SM103 and SM107 (probed
stage by stage, and checked end to end by the tests), and the three
architectures give one set of bits for the same inputs. What rows `0 ..
p-1` contribute to row `p` is cached next to the pool per (slot, head):
the decayed-inverse key rows in bf16 and fp32, the `rhs` and `update`
rows, the rows of `L`, the running decay prefix and a bf16 copy of the
boundary state (21 KB plus the 32 KB copy). The 16th row of a chunk
commits the next fp32 boundary state to the pool. Count and phase live
on the device, so a decode step reads no host metadata and is one node
of a captured CUDA graph.

The step kernel is one template with two instantiations: the decode step
(one row per block) and a span form in which a block loops over several
rows of its slot in one launch, staging the next token's rows while it
computes the current one and committing every chunk it completes. A
prefill call runs whole chunks through the pinned prefill kernel and its
tails (shorter than 16 tokens) through one launch of the span form, so
the slot is left ready for decode.
`flashinfer.batch_invariant.kda.api.recurrent_kda_batch_invariant_extend`
appends several tokens per request to open chunks: fewer than 32 per
request in one launch of the span form, with the open-row count read on
the device; longer calls with the span form up to the boundary, the
prefill kernel over whole chunks and the span form for the tail, a split
that depends on the count and the token number only.

### API

```python
out, pool = flashinfer.recurrent_kda(q, k, v, g, beta, A_log=A_log, dt_bias=dt_bias, lower_bound=-5.0,
    use_gate_in_kernel=True, use_qk_l2norm_in_kernel=True, beta_is_logit=True,
    initial_state=pool, ssm_state_indices=slots, cu_seqlens=cu_seqlens, output_final_state=True,
    backend="auto", batch_invariant=True)
```

* `batch_invariant=True` requires `backend="auto"` (the class replaces
the backends). Without the flag nothing changes for anyone.
* The state is an fp32 pool `[slots, HV, 128, 128]` addressed by
`ssm_state_indices` (`arange` when omitted) and updated in place;
`output_final_state=True` returns the pool. A slot holds the state at
the sequence's last 16-token boundary, so a chunked prefill cuts at
multiples of 16 tokens from the sequence start except for its last
piece, and a call with one token per sequence (packed `[1, B]` with
`cu_seqlens`, or `[B, 1]`) is a decode step.
* Supported: bf16 `q / k / v / g / beta`, head dim 128, `HV == H` with a
head count that is a multiple of 8, or 1 to 10, or 12 (16 / 32 / 64;
Kimi-K3's 96 heads and its 48 / 24 / 12 / 6 per rank under tensor
parallelism are covered; other counts such as 11, 14 or 20 raise: that
is what the pinned prefill route's beta transport carries, and
`flashinfer.batch_invariant.kda.spec.heads_supported(n)` answers it
without a call), the fused contract (`A_log`, `dt_bias`,
`use_gate_in_kernel`, `use_qk_l2norm_in_kernel`, `beta_is_logit`, a
finite negative `lower_bound`), packed and fixed layouts, `output`,
SM100 / SM103 / SM107.
* Never falls back: speculative decode (`num_spec_tokens`), checkpoints,
`initial_state_source`, `seq_order`, `prefill_workspace`, the
frozen-verify arguments, a bf16 state, GQA or another head dim raise
`flashinfer.batch_invariant.BatchInvariantUnsupportedError`. Prefill,
multi-token and reset calls also refuse duplicate or out-of-range slots
(a multi-token call on the default slots has nothing to read back and
can be captured in a CUDA graph); a pool first used inside a CUDA graph
capture is refused (one eager call first). A decode step with a slot
outside the pool returns NaN rows for that sequence and writes nothing
else (checked on the device, so the step stays capturable).
* A slot whose state the caller replaced since the class last wrote it
(a new request loaded into the slot) is recognised by a stamp of the
first fp32 values of each head's state and starts a new chunk. The one
case the stamp cannot see is a slot recycled with a state whose first
values are unchanged (for example reset to the same zeros after a
request shorter than 16 tokens):
`flashinfer.batch_invariant.kda.api.recurrent_kda_batch_invariant_reset(pool,
slots)` declares such slots explicitly (all of the pool's slots when
called without indices); without it the recycled slot's rows are wrong
and nothing raises.
* The pool is identified by its storage, offset and shape, so a full
view or a `detach()` of the same extent is the same pool; a view of
another extent that overlaps a pool in use (`pool[:n]`) is refused, as
is a pool that does not start at a 16-byte boundary and an `output` that
shares memory with the pool. The cached rows of a pool are released when
its storage is freed.

### Lean

`lean/BIKernels/Kda.lean` models the kernel as an opaque chunk step and
proves, under the causality hypothesis the GPU tests check bit for bit
(the outputs of a chunk prefix are the prefix of the chunk's outputs),
that the decode row equals the prefill row at every position
(`decode_eq_prefill`), that the pool's commit rule carries exactly the
prefill's boundary states (`pool_eq_stateAfter`), and that a packed call
is the per-sequence terms (`batch_term`); the generated `KdaCases.lean`
pins the count arithmetic on the Python specification's cases (kernel
`decide` only; nothing added to the axiom policy, `lake exe axioms`: 0
sorry, 0 violations). The statements are those of the class; that the
step kernel's cached-row form is the chunk step's row `p` is the
hardware-side hypothesis, discharged bit for bit by the tests below.

### Performance details

CUPTI GPU time with a cold L2 (512 MiB flush before every iteration),
medians, every cell measured in two fresh processes with the variants in
opposite orders (A B B A) and reported as the geometric mean of the two
(`benchmarks/bench_batch_invariant_recurrent_kda.py`, `--grid` for the
decode table). `ratio` = today's time / the class's; above 1 means the
class is faster. Vera Rubin NVL72 and NVL4: CUDA 13.4, torch 2.15, one
GPU of a four-GPU node; GB300 and GB200: CUDA 13.0, torch 2.14, one GPU
of a node; B200: CUDA 13.0, torch 2.14, a node with no other job,
measured before the rebase on main and before the last commit (comments,
argument checks, tests), neither of which changes the kernels.

**Decode.** One step with one token per request, as the serving
frameworks call it, replayed as a CUDA graph. The baseline is the
fastest non-invariant decode FlashInfer has for the cell: the
`recurrent_kda` T = 1 decode kernel alone (its own CUPTI records, no
pool gather or scatter around it), the fastest of the bf16 and fp32 pool
in the packed `[1, B]` and the `[B, 1]` layout (the bf16 pool in the
`[B, 1]` layout in all but a few cells). The class's time is its whole
call. A step's cost depends on its position in the 16-token chunk:
positions 0 to 14 read the boundary state and write a few rows, position
15 also commits the fp32 state. The table gives single steps at phase 0,
8 and 15, a batch whose requests sit at mixed phases (one fixed draw),
and the measured time average over a full 16-step chunk. Microseconds
per step, Vera Rubin NVL72:

| heads | B | today's decode kernel | phase 0 | phase 8 | phase 15 |
mixed | chunk average | ratio, chunk average |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 | 2.7 | 4.4 | 4.4 | 8.3 | - | 4.6 | **0.59** |
| 16 | 8 | 3.6 | 4.7 | 4.7 | 8.9 | 8.5 | 5.0 | **0.71** |
| 16 | 16 | 4.0 | 5.2 | 5.3 | 12.1 | 9.1 | 5.7 | **0.71** |
| 16 | 64 | 9.4 | 10.7 | 11.1 | 28.3 | 16.3 | 12.1 | **0.78** |
| 16 | 128 | 16.9 | 16.6 | 17.1 | 46.8 | 23.2 | 18.9 | **0.90** |
| 16 | 256 | 35.4 | 27.6 | 28.3 | 82.4 | 35.3 | 31.6 | **1.13** |
| 32 | 1 | 2.8 | 4.4 | 4.4 | 8.5 | - | 4.7 | **0.61** |
| 32 | 8 | 4.0 | 5.2 | 5.4 | 12.1 | 9.2 | 5.7 | **0.70** |
| 32 | 16 | 6.3 | 6.3 | 6.5 | 15.6 | 10.0 | 7.0 | **0.90** |
| 32 | 64 | 16.9 | 16.7 | 17.2 | 47.0 | 23.6 | 18.9 | **0.89** |
| 32 | 128 | 35.5 | 27.7 | 28.4 | 82.6 | 35.7 | 31.7 | **1.12** |
| 32 | 256 | 69.6 | 48.3 | 48.4 | 153.7 | 58.7 | 55.0 | **1.27** |

By regime (tokens in the step across the batch):

| GPU | regime | chunk average: geomean | min | cells >= 0.80 | single
steps (phase 0 / 8 / 15 / mixed): geomean | min | cells >= 0.80 |
|---|---|---|---|---|---|---|---|
| Vera Rubin NVL72 | O(10): B = 8, 16 | **0.750** | 0.699 | 1 / 4 |
0.577 | 0.328 | 2 / 16 |
| Vera Rubin NVL72 | O(100): B = 64, 128, 256 | **1.000** | 0.776 | 5 /
6 | 0.801 | 0.332 | 15 / 24 |
| Vera Rubin NVL72 | B = 1 | **0.601** | 0.591 | 0 / 2 | 0.510 | 0.332 |
0 / 6 |
| Vera Rubin NVL4 | O(10): B = 8, 16 | **0.678** | 0.636 | 0 / 4 | 0.534
| 0.310 | 2 / 16 |
| Vera Rubin NVL4 | O(100): B = 64, 128, 256 | **0.953** | 0.723 | 5 / 6
| 0.773 | 0.311 | 14 / 24 |
| Vera Rubin NVL4 | B = 1 | **0.556** | 0.553 | 0 / 2 | 0.483 | 0.320 |
0 / 6 |
| GB300 | O(10): B = 8, 16 | **0.683** | 0.636 | 0 / 4 | 0.541 | 0.319 |
2 / 16 |
| GB300 | O(100): B = 64, 128, 256 | **0.959** | 0.757 | 5 / 6 | 0.779 |
0.310 | 15 / 24 |
| GB300 | B = 1 | **0.519** | 0.515 | 0 / 2 | 0.448 | 0.286 | 0 / 6 |
| GB200 | O(10): B = 8, 16 | **0.689** | 0.639 | 1 / 4 | 0.545 | 0.321 |
2 / 16 |
| GB200 | O(100): B = 64, 128, 256 | **0.972** | 0.791 | 5 / 6 | 0.793 |
0.330 | 15 / 24 |
| GB200 | B = 1 | **0.555** | 0.554 | 0 / 2 | 0.477 | 0.312 | 0 / 6 |
| B200 | O(10): B = 8, 16 | **0.690** | 0.634 | 1 / 4 | 0.542 | 0.317 |
2 / 16 |
| B200 | O(100): B = 64, 128, 256 | **0.973** | 0.807 | 6 / 6 | 0.792 |
0.331 | 15 / 24 |
| B200 | B = 1 | **0.552** | 0.546 | 0 / 2 | 0.472 | 0.311 | 0 / 6 |

<details><summary>The same table on Vera Rubin NVL4</summary>

| heads | B | today's decode kernel | phase 0 | phase 8 | phase 15 |
mixed | chunk average | ratio, chunk average |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 | 2.7 | 4.6 | 4.6 | 8.6 | - | 4.9 | **0.55** |
| 16 | 8 | 3.5 | 5.1 | 5.1 | 9.4 | 9.0 | 5.4 | **0.65** |
| 16 | 16 | 3.9 | 5.7 | 5.7 | 12.7 | 9.5 | 6.2 | **0.64** |
| 16 | 64 | 9.6 | 11.6 | 12.1 | 30.9 | 17.2 | 13.3 | **0.72** |
| 16 | 128 | 17.3 | 18.3 | 19.1 | 51.9 | 25.3 | 21.0 | **0.83** |
| 16 | 256 | 38.5 | 30.7 | 31.3 | 93.5 | 39.0 | 35.2 | **1.09** |
| 32 | 1 | 2.8 | 4.8 | 4.8 | 8.8 | - | 5.0 | **0.56** |
| 32 | 8 | 4.0 | 5.7 | 5.7 | 12.8 | 9.6 | 6.2 | **0.64** |
| 32 | 16 | 6.2 | 6.9 | 7.1 | 17.4 | 10.8 | 7.7 | **0.80** |
| 32 | 64 | 17.4 | 18.3 | 19.2 | 51.8 | 25.8 | 21.1 | **0.82** |
| 32 | 128 | 38.3 | 30.8 | 31.4 | 93.4 | 38.5 | 35.3 | **1.08** |
| 32 | 256 | 77.9 | 52.3 | 52.1 | 176.4 | 62.7 | 60.2 | **1.29** |

</details>

<details><summary>The same table on GB300</summary>

| heads | B | today's decode kernel | phase 0 | phase 8 | phase 15 |
mixed | chunk average | ratio, chunk average |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 | 2.9 | 5.2 | 5.1 | 9.9 | - | 5.5 | **0.52** |
| 16 | 8 | 4.0 | 5.8 | 5.9 | 11.2 | 10.3 | 6.2 | **0.64** |
| 16 | 16 | 5.2 | 7.0 | 7.1 | 16.3 | 11.5 | 7.7 | **0.66** |
| 16 | 64 | 14.5 | 16.5 | 17.4 | 46.6 | 23.7 | 19.2 | **0.76** |
| 16 | 128 | 28.3 | 29.6 | 30.7 | 83.9 | 38.8 | 33.9 | **0.84** |
| 16 | 256 | 63.6 | 50.9 | 51.7 | 154.7 | 62.1 | 57.8 | **1.10** |
| 32 | 1 | 3.0 | 5.4 | 5.4 | 10.0 | - | 5.7 | **0.51** |
| 32 | 8 | 5.1 | 7.0 | 7.1 | 16.4 | 11.6 | 7.7 | **0.66** |
| 32 | 16 | 8.4 | 9.2 | 9.7 | 26.2 | 13.7 | 10.7 | **0.78** |
| 32 | 64 | 28.4 | 29.6 | 30.9 | 83.8 | 39.3 | 33.9 | **0.84** |
| 32 | 128 | 64.5 | 51.2 | 52.1 | 155.0 | 62.2 | 57.9 | **1.11** |
| 32 | 256 | 122.9 | 89.0 | 91.2 | 297.7 | 104.9 | 103.2 | **1.19** |

</details>

<details><summary>The same table on GB200</summary>

| heads | B | today's decode kernel | phase 0 | phase 8 | phase 15 |
mixed | chunk average | ratio, chunk average |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 | 3.2 | 5.4 | 5.4 | 10.1 | - | 5.7 | **0.56** |
| 16 | 8 | 4.2 | 6.2 | 6.2 | 11.6 | 10.7 | 6.6 | **0.64** |
| 16 | 16 | 5.3 | 7.3 | 7.4 | 16.3 | 11.8 | 8.0 | **0.66** |
| 16 | 64 | 14.9 | 16.4 | 17.1 | 45.0 | 22.7 | 18.8 | **0.79** |
| 16 | 128 | 27.4 | 29.1 | 30.0 | 80.0 | 38.4 | 33.0 | **0.83** |
| 16 | 256 | 62.6 | 49.7 | 50.1 | 145.1 | 60.3 | 56.0 | **1.13** |
| 32 | 1 | 3.2 | 5.4 | 5.5 | 10.2 | - | 5.8 | **0.55** |
| 32 | 8 | 5.3 | 7.3 | 7.3 | 16.3 | 11.9 | 8.0 | **0.66** |
| 32 | 16 | 8.6 | 9.5 | 9.7 | 25.3 | 13.8 | 10.8 | **0.80** |
| 32 | 64 | 27.4 | 29.1 | 29.9 | 80.2 | 38.3 | 33.0 | **0.82** |
| 32 | 128 | 63.0 | 49.9 | 50.2 | 145.1 | 60.1 | 56.0 | **1.13** |
| 32 | 256 | 120.1 | 85.7 | 86.8 | 275.6 | 101.3 | 98.1 | **1.23** |

</details>

<details><summary>The same table on B200</summary>

| heads | B | today's decode kernel | phase 0 | phase 8 | phase 15 |
mixed | chunk average | ratio, chunk average |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 | 3.3 | 5.6 | 5.6 | 10.3 | - | 5.9 | **0.55** |
| 16 | 8 | 4.3 | 6.4 | 6.5 | 12.1 | 11.1 | 6.8 | **0.63** |
| 16 | 16 | 5.5 | 7.6 | 7.7 | 17.0 | 12.2 | 8.3 | **0.67** |
| 16 | 64 | 15.7 | 16.9 | 17.9 | 47.3 | 24.4 | 19.5 | **0.81** |
| 16 | 128 | 29.1 | 31.0 | 31.9 | 84.3 | 40.4 | 34.9 | **0.83** |
| 16 | 256 | 66.6 | 53.2 | 53.5 | 153.5 | 64.2 | 59.7 | **1.13** |
| 32 | 1 | 3.4 | 5.8 | 5.9 | 10.7 | - | 6.1 | **0.56** |
| 32 | 8 | 5.5 | 7.6 | 7.7 | 17.1 | 12.4 | 8.3 | **0.66** |
| 32 | 16 | 9.0 | 9.8 | 10.2 | 26.8 | 14.2 | 11.2 | **0.81** |
| 32 | 64 | 29.1 | 31.0 | 32.0 | 84.6 | 40.6 | 35.0 | **0.83** |
| 32 | 128 | 66.9 | 53.2 | 53.7 | 153.7 | 63.4 | 59.8 | **1.12** |
| 32 | 256 | 128.2 | 92.5 | 93.9 | 292.1 | 108.7 | 105.7 | **1.21** |

</details>

At 64 or more requests the step is memory-bound, and on 15 of 16 steps
it moves fewer bytes than today's kernel: 38 to 49 KB per (request,
head), the bf16 copy of the boundary state plus a few cached rows, with
no state write, against 65.5 KB for a bf16 state read and written. That
is where the ratios above 1 come from; the chunk average is 0.78 to 1.27
on Vera Rubin NVL72 and 0.81 to 1.21 on B200. The 16th step of a chunk
reads the fp32 state and writes it and its bf16 copy, 220 KB against
65.5 KB, a byte ratio of 0.30, and measures 0.33 to 0.45 on Vera Rubin
NVL72 (0.33 to 0.44 on B200). It is the class's own boundary state and
one step in sixteen, but a launch takes as long as its slowest block, so
a batch whose requests sit at independent phases contains a completing
request in 40 % of steps at batch 8 and in nearly all from batch 64: the
`mixed` column, not the chunk average, is what unaligned serving sees
(0.58 to 1.19 at 64 or more requests, 0.42 to 0.63 at 8 or 16, Vera
Rubin NVL72).

At 8 or 16 requests the launch is a single wave of blocks and
latency-bound: 4.7 to 6.5 us mid-chunk against 3.6 to 6.3 us on Vera
Rubin NVL72 (6.4 to 10.2 against 4.3 to 9.0 us on B200). The time is
load rounds, not arithmetic: the slot index, then the count and the
state tile, then the cached rows the count selects, each a round of cold
loads, where today's kernel has two. A block also loads through one SM,
at about 27 GB/s on B200: the 32 KB state tile arrives about 2.3 us
after it is issued. Batch 1 pays the same chain: 0.60 on Vera Rubin
NVL72, 0.55 on B200.

SM107 has no placement of its own: the step kernel has no SM-count,
cache-size or wave-size threshold, and at most four of its blocks fit an
SM on SM100, SM103 and SM107 alike. One SM107 candidate was measured on
Vera Rubin NVL72 and NVL4 and not adopted: a second instantiation for
launches of at most two blocks per SM that stages both fp32 half-states
of the 16th step at once is bit-identical and takes 5 to 7 % off the
completing step and the mixed-phase step at batch 8 (and at batch 16
with 16 heads), 1 to 2 % off the chunk average there, and nothing from
batch 64.

Against the first revision of this pull request, same B200 node and
protocol: chunk average 0.92 to 0.97 at 64 or more requests (3 to 6 of 6
cells at or above 0.80), 0.66 to 0.69 at 8 or 16, 0.51 to 0.55 at batch
1; the completing step 0.32 to 0.35; mixed phases 0.61 to 0.68. Two
changes account for it: a step waits for its cached rows at its second
barrier instead of its first, and the commit of the 16th step issues its
loads ahead of their use (the first fp32 half-state as soon as the state
tile's room is free, the fp32 key rows in one round instead of four).

Levers, none in this PR: at batch 1 to 4, split a (request, head) by
state rows over several blocks so that its loads go through several SMs;
derive the 16th step's projection operand from the fp32 state instead of
also reading the bf16 copy (220 to 187 KB, at most 4 % of the chunk
average, and it costs the latency regime a load round unless the launch
size selects it).

**Prefill.** The class against `backend="auto"` on the same fp32 pool,
eager calls, kernel time of the call (microseconds for Vera Rubin NVL72,
the ratio for the other parts):

| heads | sequences x tokens | Vera Rubin NVL72 `auto` | Vera Rubin
NVL72 class | Vera Rubin NVL72 ratio | Vera Rubin NVL4 ratio | GB300
ratio | GB200 ratio | B200 ratio |
|---|---|---|---|---|---|---|---|---|
| 16 | 1 x 4096 | 108 | 196 | **0.55** | 0.55 | 0.62 | 0.62 | 0.62 |
| 16 | 1 x 32768 | 777 | 1456 | **0.53** | 0.54 | 0.58 | 0.60 | 0.60 |
| 16 | 8 x 4096 | 192 | 199 | **0.96** | 0.96 | 0.97 | 0.96 | 0.96 |
| 16 | 64 x 1024 | 279 | 294 | **0.95** | 0.94 | 0.96 | 0.96 | 0.95 |
| 16 | 256 x 256 | 421 | 459 | **0.92** | 0.91 | 0.91 | 0.92 | 0.92 |
| 16 | 8 x 4096 + 0..15 | 193 | 275 | **0.70** | 0.70 | 0.73 | 0.73 |
0.73 |
| 16 | 64 x 1024 + 0..15 | 283 | 548 | **0.52** | 0.51 | 0.61 | 0.62 |
0.62 |
| 32 | 1 x 4096 | 119 | 197 | **0.60** | 0.61 | 0.69 | 0.70 | 0.69 |
| 32 | 1 x 32768 | 866 | 1457 | **0.59** | 0.60 | 0.67 | 0.68 | 0.68 |
| 32 | 8 x 4096 | 380 | 389 | **0.98** | 0.97 | 0.98 | 0.98 | 0.97 |
| 32 | 64 x 1024 | 545 | 568 | **0.96** | 0.96 | 0.96 | 0.96 | 0.96 |
| 32 | 256 x 256 | 794 | 854 | **0.93** | 0.91 | 0.91 | 0.92 | 0.92 |
| 32 | 8 x 4096 + 0..15 | 381 | 486 | **0.78** | 0.78 | 0.79 | 0.80 |
0.81 |
| 32 | 64 x 1024 + 0..15 | 555 | 1048 | **0.53** | 0.52 | 0.63 | 0.63 |
0.64 |

With 8 or more sequences of whole chunks the class runs today's kernel
on the route `auto` also takes, plus one small boundary launch: 0.91 to
0.98 over the parts. A single sequence is 0.53 to 0.70 because `auto`
runs the two-kernel decomposition there, which is faster and a different
term; the class pins the engine route for every call so that a
sequence's bits do not depend on what shares its call. The engine route
walks a (sequence, head)'s chunks in series on one block at about 0.9 us
per chunk whatever else is in the call, and the decomposition gets to
0.6 us per chunk at one sequence by running its token-local stages ahead
on the idle SMs; this ratio is the ratio of those two chains and does
not move without another prefill placement. Ragged lengths (0 to 15
tokens past a multiple of 16 per sequence) are 0.51 to 0.81 over the
parts (B200 geomean 0.70; 0.63 in the first revision): the tails are one
launch of the step kernel's span form, written in place; what remains is
staging around the prefill kernel, which takes contiguous segments, so
the tails become segments of their own from a zero state or the whole
chunks are gathered. The lever is a tail path in the prefill kernel that
writes the cached rows itself.

**Multi-token decode steps** (secondary).
`recurrent_kda_batch_invariant_extend` with 2 to 16 tokens per request
against the cheapest of the operator's `[B, T]` call and `T`
single-token decode kernels, 16 heads, batch 1 / 8 / 64, kernel time;
each cell is the geomean over the starting phases (0, 8, mixed) with its
range:

| GPU | B | 2 tokens | 4 tokens | 8 tokens | 16 tokens |
|---|---|---|---|---|---|
| Vera Rubin NVL72 | 1 | 0.69 (0.67 to 0.70) | 0.96 (0.95 to 0.96) |
0.62 (0.56 to 0.68) | 0.33 (0.33 to 0.34) |
| Vera Rubin NVL72 | 8 | 0.74 (0.56 to 0.87) | 0.80 (0.65 to 0.90) |
0.49 (0.45 to 0.56) | 0.26 (0.26 to 0.27) |
| Vera Rubin NVL72 | 64 | 0.96 (0.75 to 1.13) | 1.31 (1.10 to 1.48) |
0.91 (0.79 to 1.10) | 0.47 (0.46 to 0.48) |
| Vera Rubin NVL4 | 1 | 0.66 (0.64 to 0.68) | 0.92 (0.88 to 0.96) | 0.63
(0.56 to 0.69) | 0.34 (0.33 to 0.35) |
| Vera Rubin NVL4 | 8 | 0.71 (0.54 to 0.84) | 0.80 (0.66 to 0.90) | 0.50
(0.46 to 0.57) | 0.27 (0.27 to 0.28) |
| Vera Rubin NVL4 | 64 | 0.93 (0.74 to 1.06) | 1.28 (1.08 to 1.42) |
0.90 (0.78 to 1.09) | 0.47 (0.46 to 0.48) |
| GB300 | 1 | 0.66 (0.65 to 0.68) | 0.89 (0.88 to 0.91) | 0.62 (0.56 to
0.68) | 0.33 (0.32 to 0.33) |
| GB300 | 8 | 0.75 (0.55 to 0.88) | 0.84 (0.67 to 0.94) | 0.51 (0.47 to
0.58) | 0.28 (0.27 to 0.28) |
| GB300 | 64 | 1.09 (0.88 to 1.24) | 1.48 (1.22 to 1.67) | 1.05 (0.92 to
1.29) | 0.55 (0.54 to 0.56) |
| GB200 | 1 | 0.65 (0.64 to 0.65) | 0.91 (0.90 to 0.91) | 0.60 (0.55 to
0.67) | 0.33 (0.32 to 0.33) |
| GB200 | 8 | 0.70 (0.53 to 0.81) | 0.80 (0.64 to 0.89) | 0.50 (0.46 to
0.57) | 0.28 (0.27 to 0.28) |
| GB200 | 64 | 1.10 (0.89 to 1.26) | 1.50 (1.24 to 1.67) | 1.05 (0.92 to
1.27) | 0.55 (0.54 to 0.57) |
| B200 | 1 | 0.57 (0.56 to 0.57) | 0.83 (0.83 to 0.83) | 0.57 (0.52 to
0.62) | 0.31 (0.31 to 0.32) |
| B200 | 8 | 0.62 (0.48 to 0.71) | 0.73 (0.60 to 0.80) | 0.46 (0.43 to
0.52) | 0.26 (0.25 to 0.26) |
| B200 | 64 | 1.04 (0.83 to 1.18) | 1.43 (1.20 to 1.59) | 0.99 (0.85 to
1.21) | 0.52 (0.50 to 0.53) |

Vera Rubin NVL72: geomean 0.65 over 32 cells (0.26 to 1.48). B200: 0.63
(0.25 to 1.59); the first revision was at 0.15 (0.04 to 0.53), with 25
of 27 launches of a 2-token call at batch 8 being helper launches. A
call with fewer than 32 tokens per request is now one launch: each block
loops over its rows, stages the next token's rows while it computes the
current one, and commits the chunks it completes; the count is read on
the device. What remains at 8 and 16 tokens is the loop's chain per
token (about 2.3 us at batch 1 on B200) against about 0.9 us per token
for today's chunked `[B, T]` call.

## 🔍 Related Issues

Follows #8361 (the mode) and #8833 (fp32 state pools for the recurrent
KDA decode kernels, the pool this class shares). Supersedes #9281, which
exposed the same mechanism as a separate API.

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

- [x] Tests have been added or updated as needed:
`tests/kda/test_batch_invariant_recurrent_kda.py` (bitwise: shape, dtype
and the integer view of every compared tensor: prefill then
token-by-token decode equals the one-shot prefill at six split points x
heads 16 / 32 x two gate profiles; decode of 1, 16, 50, 1023 and 4096
tokens from a nonzero state equals the prefill, steep and long-memory
gates; six requests at mixed chunk phases on scattered slots, prefilled
in one packed call and decoded together in the packed and the fixed
layout, equal their one-shot prefills and the same requests decoded
alone, and a committed slot equals the prefix prefill's state; chunked
prefill cut at multiples of 16 equals the one-shot; multi-token steps of
2 / 5 / 16 / 23 / 31 / 32 / 40 tokens from mixed phases equal the
one-shot (under 32 in one launch that commits the chunks it completes),
also after a replaced state; a multi-token step of 3 and of 20 tokens
captured as a CUDA graph and replayed across chunk boundaries equals the
one-shot; a multi-token step refuses duplicate and out-of-range caller
slots; a captured CUDA graph equals the eager step; cached rows past the
count are inert; a replaced slot state starts a new chunk and an
explicit reset does the same; aliases of one buffer share one state and
a pool handed over as a fresh view on every call keeps it; a first use
inside a graph capture and duplicate or out-of-range slots are refused;
another `lower_bound` and 8 heads; the operator's unpinned route and its
recurrent decode kernel are other terms; the unsupported contracts raise
and nothing runs, 20 heads among them; at 6 / 12 / 24 / 48 / 96 heads a
head's rows and final state equal the same head's rows in a 16-head
call, through prefill then decode; `FLASHINFER_KDA_BI_HEADS` runs the
head-parametrized cases at other head counts; every head count from 1 to
15 is run or refused exactly as the pinned prefill route does; three
requests at unaligned starts on 6 and 12 heads from views at odd token
offsets; a 700-token multi-token step; strided activations, another
default dtype, a misaligned pool or row, an overlapping pool extent and
an output inside the pool), `tests/batch_invariant/test_kda_lean.py`
(device-free: the generated cases are current, the count and split
arithmetic's invariants; with `lake`: the proofs build and the
conformance lines match the Python specification).
- [x] All tests are passing:
`tests/kda/test_batch_invariant_recurrent_kda.py` and
`tests/batch_invariant/test_kda_lean.py` 92 passed / 1 skipped (the
`lake` step, no toolchain in the image) in two processes each on Vera
Rubin NVL72 and Vera Rubin NVL4 (SM107, CUDA 13.4), GB300 and B300
(SM103), GB200 and a B100 (SM100), on this head rebased on main; the
second process asserts the output hashes the first recorded. On the x86
SM100 and SM103 hosts the 48 hashes recorded for the earlier revisions
of this PR are unchanged (the 28 of the first revision among them) and
14 new ones (multi-token steps) are equal across the two architectures.
torch's CUDA `randn` draws other inputs for the same seed on the aarch64
hosts and in the CUDA 13.4 build, so the hash files of GB200 / GB300 and
of the two Vera Rubin systems are their own (equal within each pair); on
inputs generated on the host (numpy), the class's prefill rows and
states and 67 decode steps have the same digests on every one of these
parts, for 16 and 32 heads. The existing files
`tests/kda/test_recurrent_kda_prefill.py`,
`test_recurrent_kda_fp32_state.py`,
`test_kda_prefill_route_predicates.py`,
`test_recurrent_kda_prefill_layout.py`, `test_kda_prefill_padding.py`,
`test_recurrent_kda.py` and `tests/batch_invariant/` run whole on the
same head: 482 to 483 passed / 12 to 13 skipped on B100, B300, GB200 and
GB300, 335 passed / 160 skipped on Vera Rubin NVL72 and NVL4. Lean: no
KDA Lean or specification file changed in this revision; `lake build`,
`lake exe kdaconformance` and `lake exe axioms` (0 with sorry, 0
violations) were re-run with Lean 4.15.0 on this head, whose import list
now also carries the MoE files from main. Internal CI on the first
revision passed its GB200, GB300 and SM107 lanes; on the SM107 lane the
class's tests skipped then, and they have not run with that lane's CUDA
13.4 image. **Head-count revision (the last two commits: the head-count
change, then a merge of main):** the earlier power-of-two rule was an
API check only; the kernels and the class fingerprint are unchanged. On
B200 the output hashes recorded on this PR's previous head are asserted
on the new head (103 passed: the 88 cases of the file plus 15 head-count
cases), the head-parametrized cases pass at 12 / 24 / 48 / 96 heads (167
passed) and at 6 heads (14 passed), and the device-free Lean and
registry tests pass (6 passed / 3 skipped). On Vera Rubin NVL72 and NVL4
the same steps passed on the head-count change before the merge of main.
The other parts and the other test files listed above were not rerun on
this head. **Current head:** on B200 (SM100), B300 (SM103) and Vera
Rubin NVL4 (SM107, CUDA 13.4) the class's file passes (127 passed) with
the 77 output hashes recorded on the head-count revision asserted and
the class fingerprint unchanged; the head-parametrized cases pass at 12
/ 24 / 48 / 96 heads (191 passed) and at 6 heads (95 passed); the
existing files `test_recurrent_kda_prefill.py`,
`test_recurrent_kda_fp32_state.py`,
`test_kda_prefill_route_predicates.py` and `test_recurrent_kda.py` pass
with the mode off (433 passed / 6 skipped on B200, 320 passed / 119
skipped on Vera Rubin NVL4, where the frozen-prefill cases skip).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/kda/test_batch_invariant_recurrent_kda.py
tests/batch_invariant/test_kda_lean.py
tests/kda/test_recurrent_kda_prefill.py
tests/kda/test_recurrent_kda_fp32_state.py
tests/kda/test_kda_prefill_route_predicates.py
tests/kda/test_recurrent_kda.py`

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

This revision adds four things to the one-launch step kernel of the
previous one; the API, the error type, the guarantees, the Lean
statements and the recorded output hashes are unchanged. (1) The step
kernel has a span form that loops over several rows of a slot in one
launch; prefill tails and multi-token steps use it. (2) A decode step
waits for its cached rows at its second barrier. (3) The commit of the
16th step issues its loads ahead of their use. (4) SM107 is supported.
The first draft's decode was a replay of the open chunk through the
prefill kernel (three launches, 0.21 to 0.35 of today's decode).

Limitations and things worth a look:

* **The class's bits rest on three toolchain facts** that only the tests
can show: `mma.sync` equals the prefill kernel's `tcgen05` products at
the shapes used; the prefill kernel's gate increment `tanh * h + h` is
compiled as one fused multiply-add, which the step kernel reproduces
with an explicit `fma` while everything else is built with `-fmad=false`
and no fast math; and the approximate `tanh` / `exp2` / `rsqrt` / `rcp`
instructions are the same on both sides. A CuTe-DSL or nvcc version that
contracts differently would break decode == prefill and the bitwise
tests would fail; the fingerprint includes the DSL version and the flags
for that reason. `FLASHINFER_EXTRA_CUDAFLAGS` can still override the
flags.
* **One token per sequence inside a multi-sequence prefill call is a
prefill of one token** (the slot starts a new chunk), while a call in
which every sequence has one token is a decode step. This is the first
draft's rule, documented in the docstring; a caller that mixes
continuing one-token requests with new prompts in one call must split
the call.
* **The replaced-state stamp is per head** and compares eight fp32
values; the reset entry exists for the case it cannot see. The decode
step bounds its slots on the device (it stays free of host reads for
graph capture); duplicate slots in one decode step are not checked and
are the caller's error, as for the operator's own pool decode.
* **The guarantee is stated for finite inputs.** A non-finite value
inside a 16-token chunk shows from the chunk's first row in a prefill
and from its own row in a decode step; other sequences of the batch stay
exact.
* **Multi-token steps are not reachable through `recurrent_kda`** (its
`[B, T > 1]` form is a prefill from the slot's state, as today); the
`extend` entry is importable from the class's module and not exported at
the top level. With fewer than 32 tokens per request it reads no count
on the host and, like a decode step, takes the heads of a slot to hold
one count; only a call on the default slots can be captured in a graph,
because caller-given slots are read back and checked. Speculative decode
on the class (`num_spec_tokens` / `num_accepted_tokens`) is a follow-up.
* The decode launcher checks dtypes, element counts, the device of `q`
and of the slot indices against the pool, and the alignment of every
pointer the kernels read 16 bytes at a time. The span launcher does not
validate its start and length tensors on the device; the Python callers
build them from prefix sums of the call's lengths.
* **One placement, no launch-size rule.** A decode step runs the same
kernel at every batch; variants that would have selected another
placement for small launches were measured and not adopted (under 5 %).
* **SM107** was verified and timed on Vera Rubin NVL72 and Vera Rubin
NVL4 with the CUDA 13.4 image, one GPU of a four-GPU node. Earlier Rubin
bring-up and pre-production boards on older drivers run the step kernel
up to 1.5x slower with today's kernel unchanged (decode at O(10): 0.46
to 0.55); those rows are not in the tables. No end-to-end serving
number.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added batch-invariant mode for recurrent KDA, supporting prefill,
decode, and multi-token extension with pooled state and reset
operations.
  * Added fingerprint identification for the KDA batch-invariant class.
  * Added scoped selection of the KDA prefill route.
* **Documentation**
* Documented supported inputs, state handling, usage conditions, and
limitations for batch-invariant KDA.
* **Tests**
* Added coverage for KDA correctness across prefill, decode, extension,
state management, and chunk boundaries.
* **Benchmarks**
* Added benchmarks for batch-invariant KDA across decode, prefill, and
extension modes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [a6234a6](https://github.com/flashinfer-ai/flashinfer/commit/a6234a606b56437359e2d5addd89b43871b8118d)

- **作者**: eigen
- **时间**: 2026-11-18T17:18:43Z
- **提交信息**: perf(cake_batch_deepgemm_fp8): locality-domain serving GEMM for dual-die SM107a (#9660)

### [f963060](https://github.com/flashinfer-ai/flashinfer/commit/f963060eb0f87c14eabab6bcff7d810eb9e87e34)

- **作者**: oiiai-oiiai
- **时间**: 2026-11-18T15:58:30Z
- **提交信息**: fix(autotuner): keep previously loaded cache files when entering autotune(cache=...) (#8766)

## 📌 Description

`autotune(cache=path)` cleared `_file_configs` / `_file_config_policies`
on entry before loading the file, so a process that uses several cache
files loses the first file's configs when it enters the second context.
Example: a serving engine tunes its target model under
`autotune(cache=target.json)` and its speculative draft model under
`autotune(cache=draft.json)` (different config hashes, so different
files). Entering the draft context drops the target's loaded configs; a
later target lookup that the in-process profiling cache cannot answer
silently falls back to the default tactic (-1). Calling `load_configs()`
directly already behaves additively; only `autotune()` cleared.

## 🔍 Changes

- `autotune(cache=path)` no longer clears loaded file configs on entry.
The file's entries are added to those already loaded; for a key present
in several files the file loaded last wins (policy replaced per key, as
`load_configs` already does).
- Namespaced product records keep their single-writer-per-path
semantics: still reset and re-read from the entered file. Save-on-exit
is unchanged.
- Docstring and `docs/autotuning.rst` updated.

Note on save: `save_configs` already snapshots every loaded config plus
all in-process profiling results into the saved file (pre-existing,
documented as a "complete, self-contained config"). With this fix the
second file's exit-save therefore also contains the first file's loaded
entries; the new test asserts this.

## 🔍 Related Issues

Found while serving a target model and its speculative draft from two
autotune cache files in one process.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

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
      Reason: not needed; Python-only autotuner change.

Suggested CI test targets: `tests/autotuner/test_autotune_cache_merge.py
tests/autotuner/test_autotuner_core.py
tests/autotuner/test_autotune_cache_v2.py`

New `tests/autotuner/test_autotune_cache_merge.py` (CPU, fake
profiling): load A, enter `autotune(cache=B)`: A-only key still served,
key in both files takes B's value, B-only key served; exit-save of B
keeps B's entries plus the new result and leaves A untouched;
re-entering A makes it last-loaded again; entering a not-yet-existing
cache path keeps loaded configs. Both tests fail on main without the
fix. Existing autotuner cache tests unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified that loading an autotune cache retains configs already
loaded in the process. For duplicate keys, the most recently loaded file
takes precedence.
* Explained that configs for the same workload remain distinct across
runner classes, with selection based on caller runner order.
* Clarified that saving a cache can include configs loaded from multiple
files and newly tuned results, without changing earlier cache files.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4fec890](https://github.com/flashinfer-ai/flashinfer/commit/4fec89015f3d456b20b42a1c067543b564efd4e0)

- **作者**: eigen
- **时间**: 2026-11-18T15:55:30Z
- **提交信息**: perf(cake_gdp): retune five n = 3 static decode programs on SM90 and SM103 (#9654)

The Cake Gated DeltaProduct (GDP) kernel family has four decode routes,
`decode_nh1` to `decode_nh4`, one for each number of Householder updates
per token (n = 1, 2, 3 and 4). On SM90 it also has chunked varlen
prefill programs. All four decode routes use head sizes K = 128 and V =
64, an FP32 recurrent state and fused q/k L2 normalization, and they
serve decode and MTP verification on SM90, SM100 and SM103. A decode
call launches the static-token-count program for its token count T if
two conditions hold: that program exists, and its band admits the call's
batch x heads on the device's SM count. Otherwise the call launches the
route's runtime-token-count program. The n = 3 route has
static-token-count programs for T = 1, 2, 3, 4, 5, 6, 7, 8 and 16. Each
T has an `l8r4` program. T = 5, 6, 7, 8 and 16 also have an `l8r2`
program, which is used while batch x heads is small, and T = 1 and T = 4
have further programs for other batch x heads bands.

This PR changes the generated code of five of these n = 3 programs and
nothing else:

- On SM90: the `l8r4` programs for T = 6, 7 and 16, and the `l8r2`
program for T = 16.
- On SM103: the `l8r2` program for T = 6.

Routing, program names and every other program are unchanged. No SM100
program changes. The baseline is the same programs on FlashInfer main,
which is the previous Cake version.

Speedup is previous / this PR, so a value above 1 means faster. Each row
uses median kernel time (CUPTI kernel time, cold L2), with both sides
measured on the same GPU in one process using CUDA 13.4. Each GPU's
table has 144 rows: heads 80, 24, 20, 10 x batch 1, 16, 64, 256 x T 1,
2, 3, 4, 5, 6, 7, 8, 16. The "program changed" column marks rows whose
program is one of the five changed programs on that GPU. Rows marked
"no" run the same code in both columns.

- H100: 38 changed-program rows, geomean 1.0750x, min 1.0270x, max
1.2027x; all 144 rows geomean 1.0185x.
- B200: no SM100 program changes; all 144 rows geomean 1.0002x (same
code in both columns).
- GB300: 5 changed-program rows, geomean 1.0185x, min 1.0139x, max
1.0270x; all 144 rows geomean 1.0005x.

The other Cake GDP variants (the n = 1, 2 and 4 decode routes, all other
n = 3 programs including the runtime-token-count program, and the SM90
chunked varlen prefill programs) are unchanged, and the family ships on
`sm_90a`, `sm_100a` and `sm_103a`.

<details>
<summary>NVIDIA H100 80GB HBM3, SM90 (sm_90a, 132 SMs), CUDA 13.4:
median kernel time in microseconds</summary>

| T | heads | batch | program changed | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|:---:|---:|---:|---:|
| 1 | 80 | 1 | no | 4.22 | 4.26 | 0.993x |
| 1 | 80 | 16 | no | 24.80 | 25.01 | 0.992x |
| 1 | 80 | 64 | no | 113.31 | 113.47 | 0.999x |
| 1 | 80 | 256 | no | 465.95 | 465.96 | 1.000x |
| 1 | 24 | 1 | no | 3.33 | 3.30 | 1.010x |
| 1 | 24 | 16 | no | 9.44 | 9.54 | 0.990x |
| 1 | 24 | 64 | no | 32.22 | 32.32 | 0.997x |
| 1 | 24 | 256 | no | 137.77 | 137.76 | 1.000x |
| 1 | 20 | 1 | no | 3.30 | 3.26 | 1.010x |
| 1 | 20 | 16 | no | 8.90 | 8.93 | 0.996x |
| 1 | 20 | 64 | no | 26.11 | 26.14 | 0.999x |
| 1 | 20 | 256 | no | 114.43 | 114.58 | 0.999x |
| 1 | 10 | 1 | no | 2.94 | 2.94 | 1.000x |
| 1 | 10 | 16 | no | 5.52 | 5.54 | 0.997x |
| 1 | 10 | 64 | no | 13.60 | 13.54 | 1.005x |
| 1 | 10 | 256 | no | 55.52 | 55.55 | 0.999x |
| 2 | 80 | 1 | no | 5.22 | 5.25 | 0.994x |
| 2 | 80 | 16 | no | 31.38 | 31.65 | 0.991x |
| 2 | 80 | 64 | no | 121.82 | 121.92 | 0.999x |
| 2 | 80 | 256 | no | 481.76 | 482.03 | 0.999x |
| 2 | 24 | 1 | no | 4.74 | 4.80 | 0.987x |
| 2 | 24 | 16 | no | 12.29 | 12.32 | 0.998x |
| 2 | 24 | 64 | no | 37.54 | 37.79 | 0.993x |
| 2 | 24 | 256 | no | 145.47 | 145.42 | 1.000x |
| 2 | 20 | 1 | no | 4.74 | 4.77 | 0.993x |
| 2 | 20 | 16 | no | 10.94 | 11.07 | 0.988x |
| 2 | 20 | 64 | no | 31.20 | 31.10 | 1.003x |
| 2 | 20 | 256 | no | 121.57 | 121.44 | 1.001x |
| 2 | 10 | 1 | no | 4.58 | 4.61 | 0.993x |
| 2 | 10 | 16 | no | 7.36 | 7.42 | 0.991x |
| 2 | 10 | 64 | no | 19.81 | 19.87 | 0.997x |
| 2 | 10 | 256 | no | 61.76 | 61.68 | 1.001x |
| 3 | 80 | 1 | no | 5.98 | 5.98 | 1.000x |
| 3 | 80 | 16 | no | 36.00 | 35.78 | 1.006x |
| 3 | 80 | 64 | no | 126.93 | 126.94 | 1.000x |
| 3 | 80 | 256 | no | 492.83 | 492.92 | 1.000x |
| 3 | 24 | 1 | no | 5.47 | 5.47 | 1.000x |
| 3 | 24 | 16 | no | 13.92 | 13.92 | 1.000x |
| 3 | 24 | 64 | no | 42.29 | 42.16 | 1.003x |
| 3 | 24 | 256 | no | 150.85 | 150.90 | 1.000x |
| 3 | 20 | 1 | no | 5.47 | 5.51 | 0.994x |
| 3 | 20 | 16 | no | 12.58 | 12.54 | 1.003x |
| 3 | 20 | 64 | no | 35.39 | 35.52 | 0.996x |
| 3 | 20 | 256 | no | 126.72 | 126.93 | 0.998x |
| 3 | 10 | 1 | no | 5.38 | 5.38 | 1.000x |
| 3 | 10 | 16 | no | 8.67 | 8.64 | 1.004x |
| 3 | 10 | 64 | no | 22.80 | 22.88 | 0.997x |
| 3 | 10 | 256 | no | 66.02 | 66.40 | 0.994x |
| 4 | 80 | 1 | no | 6.08 | 6.11 | 0.995x |
| 4 | 80 | 16 | no | 40.03 | 39.93 | 1.002x |
| 4 | 80 | 64 | no | 132.99 | 132.96 | 1.000x |
| 4 | 80 | 256 | no | 504.92 | 504.64 | 1.001x |
| 4 | 24 | 1 | no | 5.57 | 5.57 | 1.000x |
| 4 | 24 | 16 | no | 14.98 | 15.07 | 0.994x |
| 4 | 24 | 64 | no | 47.14 | 47.26 | 0.997x |
| 4 | 24 | 256 | no | 157.47 | 157.02 | 1.003x |
| 4 | 20 | 1 | no | 5.57 | 5.57 | 1.000x |
| 4 | 20 | 16 | no | 13.70 | 13.60 | 1.007x |
| 4 | 20 | 64 | no | 39.55 | 39.23 | 1.008x |
| 4 | 20 | 256 | no | 132.64 | 132.64 | 1.000x |
| 4 | 10 | 1 | no | 5.47 | 5.47 | 1.000x |
| 4 | 10 | 16 | no | 9.66 | 9.63 | 1.003x |
| 4 | 10 | 64 | no | 25.20 | 25.06 | 1.006x |
| 4 | 10 | 256 | no | 70.32 | 70.05 | 1.004x |
| 5 | 80 | 1 | no | 7.04 | 7.07 | 0.996x |
| 5 | 80 | 16 | no | 48.38 | 48.42 | 0.999x |
| 5 | 80 | 64 | no | 151.41 | 151.74 | 0.998x |
| 5 | 80 | 256 | no | 555.26 | 555.68 | 0.999x |
| 5 | 24 | 1 | no | 6.46 | 6.46 | 1.000x |
| 5 | 24 | 16 | no | 17.54 | 17.60 | 0.996x |
| 5 | 24 | 64 | no | 55.81 | 55.94 | 0.998x |
| 5 | 24 | 256 | no | 178.48 | 178.57 | 1.000x |
| 5 | 20 | 1 | no | 6.43 | 6.43 | 1.000x |
| 5 | 20 | 16 | no | 15.90 | 15.90 | 1.000x |
| 5 | 20 | 64 | no | 47.78 | 48.29 | 0.989x |
| 5 | 20 | 256 | no | 151.29 | 151.84 | 0.996x |
| 5 | 10 | 1 | no | 6.37 | 6.37 | 1.000x |
| 5 | 10 | 16 | no | 10.62 | 10.62 | 1.000x |
| 5 | 10 | 64 | no | 29.95 | 29.87 | 1.003x |
| 5 | 10 | 256 | no | 81.84 | 82.05 | 0.998x |
| 6 | 80 | 1 | no | 7.71 | 7.74 | 0.996x |
| 6 | 80 | 16 | yes | 52.96 | 44.40 | 1.193x |
| 6 | 80 | 64 | yes | 165.17 | 152.13 | 1.086x |
| 6 | 80 | 256 | yes | 603.08 | 571.96 | 1.054x |
| 6 | 24 | 1 | no | 7.13 | 7.10 | 1.004x |
| 6 | 24 | 16 | yes | 19.17 | 17.95 | 1.068x |
| 6 | 24 | 64 | yes | 60.13 | 51.14 | 1.176x |
| 6 | 24 | 256 | yes | 194.53 | 180.41 | 1.078x |
| 6 | 20 | 1 | no | 7.07 | 7.07 | 1.000x |
| 6 | 20 | 16 | yes | 17.47 | 16.83 | 1.038x |
| 6 | 20 | 64 | yes | 52.67 | 44.51 | 1.183x |
| 6 | 20 | 256 | yes | 164.67 | 152.02 | 1.083x |
| 6 | 10 | 1 | no | 7.04 | 7.07 | 0.996x |
| 6 | 10 | 16 | no | 11.87 | 11.90 | 0.997x |
| 6 | 10 | 64 | yes | 33.42 | 27.79 | 1.203x |
| 6 | 10 | 256 | yes | 89.53 | 79.94 | 1.120x |
| 7 | 80 | 1 | no | 8.48 | 8.48 | 1.000x |
| 7 | 80 | 16 | yes | 56.26 | 53.18 | 1.058x |
| 7 | 80 | 64 | yes | 181.41 | 170.54 | 1.064x |
| 7 | 80 | 256 | yes | 674.89 | 633.79 | 1.065x |
| 7 | 24 | 1 | no | 7.81 | 7.81 | 1.000x |
| 7 | 24 | 16 | yes | 20.67 | 19.71 | 1.049x |
| 7 | 24 | 64 | yes | 64.00 | 60.77 | 1.053x |
| 7 | 24 | 256 | yes | 213.95 | 200.61 | 1.067x |
| 7 | 20 | 1 | no | 7.75 | 7.74 | 1.000x |
| 7 | 20 | 16 | yes | 19.14 | 18.24 | 1.049x |
| 7 | 20 | 64 | yes | 56.05 | 52.80 | 1.062x |
| 7 | 20 | 256 | yes | 181.53 | 170.30 | 1.066x |
| 7 | 10 | 1 | no | 7.71 | 7.71 | 1.000x |
| 7 | 10 | 16 | no | 13.06 | 13.02 | 1.002x |
| 7 | 10 | 64 | yes | 35.46 | 33.28 | 1.065x |
| 7 | 10 | 256 | yes | 97.79 | 91.65 | 1.067x |
| 8 | 80 | 1 | no | 8.90 | 8.83 | 1.007x |
| 8 | 80 | 16 | no | 57.22 | 57.22 | 1.000x |
| 8 | 80 | 64 | no | 194.11 | 194.37 | 0.999x |
| 8 | 80 | 256 | no | 731.71 | 731.75 | 1.000x |
| 8 | 24 | 1 | no | 8.22 | 8.26 | 0.996x |
| 8 | 24 | 16 | no | 21.81 | 21.84 | 0.999x |
| 8 | 24 | 64 | no | 64.85 | 64.93 | 0.999x |
| 8 | 24 | 256 | no | 230.35 | 230.56 | 0.999x |
| 8 | 20 | 1 | no | 8.22 | 8.22 | 1.000x |
| 8 | 20 | 16 | no | 20.45 | 20.45 | 1.000x |
| 8 | 20 | 64 | no | 58.05 | 57.92 | 1.002x |
| 8 | 20 | 256 | no | 194.43 | 194.69 | 0.999x |
| 8 | 10 | 1 | no | 8.16 | 8.16 | 1.000x |
| 8 | 10 | 16 | no | 13.38 | 13.44 | 0.995x |
| 8 | 10 | 64 | no | 35.42 | 35.39 | 1.001x |
| 8 | 10 | 256 | no | 102.77 | 102.62 | 1.001x |
| 16 | 80 | 1 | yes | 14.34 | 13.95 | 1.027x |
| 16 | 80 | 16 | yes | 101.57 | 95.34 | 1.065x |
| 16 | 80 | 64 | yes | 358.97 | 333.98 | 1.075x |
| 16 | 80 | 256 | yes | 1380.57 | 1279.42 | 1.079x |
| 16 | 24 | 1 | yes | 13.41 | 13.06 | 1.027x |
| 16 | 24 | 16 | yes | 35.62 | 33.66 | 1.058x |
| 16 | 24 | 64 | yes | 118.81 | 111.52 | 1.065x |
| 16 | 24 | 256 | yes | 428.48 | 398.40 | 1.075x |
| 16 | 20 | 1 | yes | 13.39 | 12.99 | 1.031x |
| 16 | 20 | 16 | yes | 34.53 | 32.38 | 1.066x |
| 16 | 20 | 64 | yes | 101.36 | 95.39 | 1.063x |
| 16 | 20 | 256 | yes | 359.60 | 334.78 | 1.074x |
| 16 | 10 | 1 | yes | 13.41 | 12.99 | 1.032x |
| 16 | 10 | 16 | yes | 25.36 | 24.00 | 1.057x |
| 16 | 10 | 64 | yes | 63.68 | 59.63 | 1.068x |
| 16 | 10 | 256 | yes | 190.01 | 177.60 | 1.070x |

</details>

<details>
<summary>NVIDIA B200, SM100 (sm_100a, 148 SMs), CUDA 13.4: median kernel
time in microseconds</summary>

| T | heads | batch | program changed | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|:---:|---:|---:|---:|
| 1 | 80 | 1 | no | 3.968 | 3.968 | 1.000x |
| 1 | 80 | 16 | no | 13.633 | 13.664 | 0.998x |
| 1 | 80 | 64 | no | 49.328 | 49.216 | 1.002x |
| 1 | 80 | 256 | no | 199.904 | 199.919 | 1.000x |
| 1 | 24 | 1 | no | 3.328 | 3.328 | 1.000x |
| 1 | 24 | 16 | no | 6.912 | 6.913 | 1.000x |
| 1 | 24 | 64 | no | 15.648 | 15.647 | 1.000x |
| 1 | 24 | 256 | no | 59.008 | 58.752 | 1.004x |
| 1 | 20 | 1 | no | 3.360 | 3.391 | 0.991x |
| 1 | 20 | 16 | no | 6.624 | 6.624 | 1.000x |
| 1 | 20 | 64 | no | 13.664 | 13.696 | 0.998x |
| 1 | 20 | 256 | no | 49.280 | 48.976 | 1.006x |
| 1 | 10 | 1 | no | 3.264 | 3.264 | 1.000x |
| 1 | 10 | 16 | no | 4.800 | 4.800 | 1.000x |
| 1 | 10 | 64 | no | 8.865 | 8.960 | 0.989x |
| 1 | 10 | 256 | no | 24.128 | 24.352 | 0.991x |
| 2 | 80 | 1 | no | 5.152 | 5.216 | 0.988x |
| 2 | 80 | 16 | no | 19.264 | 19.296 | 0.998x |
| 2 | 80 | 64 | no | 61.328 | 61.376 | 0.999x |
| 2 | 80 | 256 | no | 228.800 | 228.752 | 1.000x |
| 2 | 24 | 1 | no | 5.120 | 5.088 | 1.006x |
| 2 | 24 | 16 | no | 8.511 | 8.480 | 1.004x |
| 2 | 24 | 64 | no | 22.176 | 22.208 | 0.999x |
| 2 | 24 | 256 | no | 72.671 | 72.704 | 1.000x |
| 2 | 20 | 1 | no | 5.056 | 5.056 | 1.000x |
| 2 | 20 | 16 | no | 8.224 | 8.223 | 1.000x |
| 2 | 20 | 64 | no | 19.295 | 19.328 | 0.998x |
| 2 | 20 | 256 | no | 61.504 | 61.504 | 1.000x |
| 2 | 10 | 1 | no | 5.120 | 5.120 | 1.000x |
| 2 | 10 | 16 | no | 6.464 | 6.496 | 0.995x |
| 2 | 10 | 64 | no | 12.704 | 12.735 | 0.998x |
| 2 | 10 | 256 | no | 33.216 | 33.216 | 1.000x |
| 3 | 80 | 1 | no | 5.920 | 5.888 | 1.005x |
| 3 | 80 | 16 | no | 22.304 | 22.304 | 1.000x |
| 3 | 80 | 64 | no | 71.872 | 71.904 | 1.000x |
| 3 | 80 | 256 | no | 266.847 | 266.784 | 1.000x |
| 3 | 24 | 1 | no | 5.663 | 5.663 | 1.000x |
| 3 | 24 | 16 | no | 9.920 | 9.920 | 1.000x |
| 3 | 24 | 64 | no | 25.856 | 25.888 | 0.999x |
| 3 | 24 | 256 | no | 85.056 | 85.056 | 1.000x |
| 3 | 20 | 1 | no | 5.696 | 5.664 | 1.006x |
| 3 | 20 | 16 | no | 9.664 | 9.632 | 1.003x |
| 3 | 20 | 64 | no | 22.367 | 22.336 | 1.001x |
| 3 | 20 | 256 | no | 72.096 | 72.128 | 1.000x |
| 3 | 10 | 1 | no | 5.568 | 5.536 | 1.006x |
| 3 | 10 | 16 | no | 7.553 | 7.329 | 1.031x |
| 3 | 10 | 64 | no | 14.528 | 14.496 | 1.002x |
| 3 | 10 | 256 | no | 39.264 | 39.215 | 1.001x |
| 4 | 80 | 1 | no | 5.824 | 5.856 | 0.995x |
| 4 | 80 | 16 | no | 24.463 | 24.480 | 0.999x |
| 4 | 80 | 64 | no | 81.648 | 81.568 | 1.001x |
| 4 | 80 | 256 | no | 304.224 | 304.095 | 1.000x |
| 4 | 24 | 1 | no | 5.664 | 5.664 | 1.000x |
| 4 | 24 | 16 | no | 10.976 | 11.008 | 0.997x |
| 4 | 24 | 64 | no | 28.640 | 28.608 | 1.001x |
| 4 | 24 | 256 | no | 96.671 | 96.671 | 1.000x |
| 4 | 20 | 1 | no | 5.600 | 5.600 | 1.000x |
| 4 | 20 | 16 | no | 10.784 | 10.753 | 1.003x |
| 4 | 20 | 64 | no | 24.480 | 24.480 | 1.000x |
| 4 | 20 | 256 | no | 81.791 | 81.792 | 1.000x |
| 4 | 10 | 1 | no | 5.664 | 5.664 | 1.000x |
| 4 | 10 | 16 | no | 8.064 | 8.064 | 1.000x |
| 4 | 10 | 64 | no | 15.264 | 15.232 | 1.002x |
| 4 | 10 | 256 | no | 44.096 | 44.112 | 1.000x |
| 5 | 80 | 1 | no | 7.104 | 7.104 | 1.000x |
| 5 | 80 | 16 | no | 30.687 | 30.624 | 1.002x |
| 5 | 80 | 64 | no | 102.240 | 102.208 | 1.000x |
| 5 | 80 | 256 | no | 383.936 | 383.855 | 1.000x |
| 5 | 24 | 1 | no | 6.753 | 6.753 | 1.000x |
| 5 | 24 | 16 | no | 13.216 | 13.216 | 1.000x |
| 5 | 24 | 64 | no | 35.744 | 35.744 | 1.000x |
| 5 | 24 | 256 | no | 121.376 | 121.344 | 1.000x |
| 5 | 20 | 1 | no | 6.720 | 6.688 | 1.005x |
| 5 | 20 | 16 | no | 12.864 | 12.896 | 0.998x |
| 5 | 20 | 64 | no | 30.608 | 30.592 | 1.000x |
| 5 | 20 | 256 | no | 102.432 | 102.464 | 1.000x |
| 5 | 10 | 1 | no | 6.848 | 6.848 | 1.000x |
| 5 | 10 | 16 | no | 9.696 | 9.728 | 0.997x |
| 5 | 10 | 64 | no | 19.264 | 19.264 | 1.000x |
| 5 | 10 | 256 | no | 55.168 | 55.137 | 1.001x |
| 6 | 80 | 1 | no | 7.488 | 7.489 | 1.000x |
| 6 | 80 | 16 | no | 35.616 | 35.648 | 0.999x |
| 6 | 80 | 64 | no | 118.431 | 118.400 | 1.000x |
| 6 | 80 | 256 | no | 444.576 | 444.464 | 1.000x |
| 6 | 24 | 1 | no | 7.248 | 7.200 | 1.007x |
| 6 | 24 | 16 | no | 15.104 | 15.072 | 1.002x |
| 6 | 24 | 64 | no | 41.856 | 41.824 | 1.001x |
| 6 | 24 | 256 | no | 140.416 | 140.416 | 1.000x |
| 6 | 20 | 1 | no | 7.200 | 7.232 | 0.996x |
| 6 | 20 | 16 | no | 14.720 | 14.720 | 1.000x |
| 6 | 20 | 64 | no | 35.616 | 35.599 | 1.000x |
| 6 | 20 | 256 | no | 118.655 | 118.593 | 1.000x |
| 6 | 10 | 1 | no | 7.136 | 7.136 | 1.000x |
| 6 | 10 | 16 | no | 10.528 | 10.560 | 0.997x |
| 6 | 10 | 64 | no | 22.432 | 22.400 | 1.001x |
| 6 | 10 | 256 | no | 64.128 | 64.160 | 1.000x |
| 7 | 80 | 1 | no | 8.032 | 8.064 | 0.996x |
| 7 | 80 | 16 | no | 38.912 | 38.880 | 1.001x |
| 7 | 80 | 64 | no | 130.336 | 130.304 | 1.000x |
| 7 | 80 | 256 | no | 490.208 | 490.127 | 1.000x |
| 7 | 24 | 1 | no | 7.712 | 7.744 | 0.996x |
| 7 | 24 | 16 | no | 16.352 | 16.352 | 1.000x |
| 7 | 24 | 64 | no | 45.792 | 45.824 | 0.999x |
| 7 | 24 | 256 | no | 154.720 | 154.688 | 1.000x |
| 7 | 20 | 1 | no | 7.744 | 7.744 | 1.000x |
| 7 | 20 | 16 | no | 16.064 | 16.032 | 1.002x |
| 7 | 20 | 64 | no | 39.008 | 38.976 | 1.001x |
| 7 | 20 | 256 | no | 130.752 | 130.816 | 1.000x |
| 7 | 10 | 1 | no | 7.808 | 7.776 | 1.004x |
| 7 | 10 | 16 | no | 11.680 | 11.648 | 1.003x |
| 7 | 10 | 64 | no | 24.416 | 24.448 | 0.999x |
| 7 | 10 | 256 | no | 70.688 | 70.688 | 1.000x |
| 8 | 80 | 1 | no | 8.032 | 8.064 | 0.996x |
| 8 | 80 | 16 | no | 42.319 | 42.336 | 1.000x |
| 8 | 80 | 64 | no | 143.791 | 143.808 | 1.000x |
| 8 | 80 | 256 | no | 543.055 | 542.960 | 1.000x |
| 8 | 24 | 1 | no | 7.743 | 7.713 | 1.004x |
| 8 | 24 | 16 | no | 17.328 | 17.344 | 0.999x |
| 8 | 24 | 64 | no | 50.048 | 50.048 | 1.000x |
| 8 | 24 | 256 | no | 170.784 | 170.720 | 1.000x |
| 8 | 20 | 1 | no | 7.775 | 7.776 | 1.000x |
| 8 | 20 | 16 | no | 17.024 | 17.024 | 1.000x |
| 8 | 20 | 64 | no | 42.304 | 42.304 | 1.000x |
| 8 | 20 | 256 | no | 144.080 | 144.063 | 1.000x |
| 8 | 10 | 1 | no | 7.776 | 7.776 | 1.000x |
| 8 | 10 | 16 | no | 12.255 | 12.256 | 1.000x |
| 8 | 10 | 64 | no | 26.080 | 26.111 | 0.999x |
| 8 | 10 | 256 | no | 77.456 | 77.441 | 1.000x |
| 16 | 80 | 1 | no | 13.120 | 13.120 | 1.000x |
| 16 | 80 | 16 | no | 75.328 | 75.264 | 1.001x |
| 16 | 80 | 64 | no | 264.351 | 264.416 | 1.000x |
| 16 | 80 | 256 | no | 1014.752 | 1014.688 | 1.000x |
| 16 | 24 | 1 | no | 12.736 | 12.736 | 1.000x |
| 16 | 24 | 16 | no | 29.472 | 29.472 | 1.000x |
| 16 | 24 | 64 | no | 89.632 | 89.600 | 1.000x |
| 16 | 24 | 256 | no | 315.104 | 315.120 | 1.000x |
| 16 | 20 | 1 | no | 12.800 | 12.800 | 1.000x |
| 16 | 20 | 16 | no | 29.184 | 29.184 | 1.000x |
| 16 | 20 | 64 | no | 75.424 | 75.360 | 1.001x |
| 16 | 20 | 256 | no | 265.056 | 265.023 | 1.000x |
| 16 | 10 | 1 | no | 12.672 | 12.672 | 1.000x |
| 16 | 10 | 16 | no | 21.088 | 21.088 | 1.000x |
| 16 | 10 | 64 | no | 45.344 | 45.344 | 1.000x |
| 16 | 10 | 256 | no | 140.895 | 140.832 | 1.000x |

</details>

<details>
<summary>NVIDIA GB300, SM103 (sm_103a, 152 SMs), CUDA 13.4: median
kernel time in microseconds</summary>

| T | heads | batch | program changed | previous Cake (us) | this PR
(us) | speedup |
|---:|---:|---:|:---:|---:|---:|---:|
| 1 | 80 | 1 | no | 3.744 | 3.776 | 0.992x |
| 1 | 80 | 16 | no | 13.440 | 13.344 | 1.007x |
| 1 | 80 | 64 | no | 47.471 | 47.296 | 1.004x |
| 1 | 80 | 256 | no | 194.048 | 193.888 | 1.001x |
| 1 | 24 | 1 | no | 3.184 | 3.200 | 0.995x |
| 1 | 24 | 16 | no | 6.752 | 6.720 | 1.005x |
| 1 | 24 | 64 | no | 14.880 | 14.880 | 1.000x |
| 1 | 24 | 256 | no | 57.024 | 57.088 | 0.999x |
| 1 | 20 | 1 | no | 3.200 | 3.200 | 1.000x |
| 1 | 20 | 16 | no | 6.368 | 6.368 | 1.000x |
| 1 | 20 | 64 | no | 13.264 | 13.296 | 0.998x |
| 1 | 20 | 256 | no | 47.552 | 47.232 | 1.007x |
| 1 | 10 | 1 | no | 3.200 | 3.200 | 1.000x |
| 1 | 10 | 16 | no | 4.576 | 4.576 | 1.000x |
| 1 | 10 | 64 | no | 8.608 | 8.432 | 1.021x |
| 1 | 10 | 256 | no | 22.496 | 22.656 | 0.993x |
| 2 | 80 | 1 | no | 4.896 | 4.960 | 0.987x |
| 2 | 80 | 16 | no | 18.176 | 18.208 | 0.998x |
| 2 | 80 | 64 | no | 56.704 | 56.640 | 1.001x |
| 2 | 80 | 256 | no | 214.657 | 214.944 | 0.999x |
| 2 | 24 | 1 | no | 4.864 | 4.864 | 1.000x |
| 2 | 24 | 16 | no | 8.160 | 8.192 | 0.996x |
| 2 | 24 | 64 | no | 20.768 | 20.864 | 0.995x |
| 2 | 24 | 256 | no | 67.552 | 67.455 | 1.001x |
| 2 | 20 | 1 | no | 4.800 | 4.832 | 0.994x |
| 2 | 20 | 16 | no | 7.840 | 7.904 | 0.992x |
| 2 | 20 | 64 | no | 18.113 | 18.208 | 0.995x |
| 2 | 20 | 256 | no | 56.944 | 57.152 | 0.996x |
| 2 | 10 | 1 | no | 4.896 | 4.896 | 1.000x |
| 2 | 10 | 16 | no | 6.304 | 6.272 | 1.005x |
| 2 | 10 | 64 | no | 12.160 | 12.128 | 1.003x |
| 2 | 10 | 256 | no | 30.400 | 30.176 | 1.007x |
| 3 | 80 | 1 | no | 5.664 | 5.664 | 1.000x |
| 3 | 80 | 16 | no | 20.864 | 20.847 | 1.001x |
| 3 | 80 | 64 | no | 65.376 | 65.440 | 0.999x |
| 3 | 80 | 256 | no | 244.992 | 245.088 | 1.000x |
| 3 | 24 | 1 | no | 5.376 | 5.376 | 1.000x |
| 3 | 24 | 16 | no | 9.440 | 9.408 | 1.003x |
| 3 | 24 | 64 | no | 23.872 | 23.872 | 1.000x |
| 3 | 24 | 256 | no | 77.409 | 77.440 | 1.000x |
| 3 | 20 | 1 | no | 5.376 | 5.408 | 0.994x |
| 3 | 20 | 16 | no | 9.184 | 9.184 | 1.000x |
| 3 | 20 | 64 | no | 20.832 | 20.864 | 0.999x |
| 3 | 20 | 256 | no | 65.504 | 65.504 | 1.000x |
| 3 | 10 | 1 | no | 5.312 | 5.312 | 1.000x |
| 3 | 10 | 16 | no | 7.008 | 7.040 | 0.996x |
| 3 | 10 | 64 | no | 13.568 | 13.632 | 0.995x |
| 3 | 10 | 256 | no | 35.360 | 35.360 | 1.000x |
| 4 | 80 | 1 | no | 5.536 | 5.536 | 1.000x |
| 4 | 80 | 16 | no | 22.944 | 22.912 | 1.001x |
| 4 | 80 | 64 | no | 74.112 | 74.048 | 1.001x |
| 4 | 80 | 256 | no | 279.168 | 279.232 | 1.000x |
| 4 | 24 | 1 | no | 5.408 | 5.408 | 1.000x |
| 4 | 24 | 16 | no | 10.496 | 10.432 | 1.006x |
| 4 | 24 | 64 | no | 26.464 | 26.368 | 1.004x |
| 4 | 24 | 256 | no | 87.680 | 87.712 | 1.000x |
| 4 | 20 | 1 | no | 5.344 | 5.312 | 1.006x |
| 4 | 20 | 16 | no | 10.144 | 10.144 | 1.000x |
| 4 | 20 | 64 | no | 22.816 | 22.848 | 0.999x |
| 4 | 20 | 256 | no | 73.983 | 73.952 | 1.000x |
| 4 | 10 | 1 | no | 5.344 | 5.344 | 1.000x |
| 4 | 10 | 16 | no | 7.680 | 7.680 | 1.000x |
| 4 | 10 | 64 | no | 14.353 | 14.304 | 1.003x |
| 4 | 10 | 256 | no | 39.552 | 39.649 | 0.998x |
| 5 | 80 | 1 | no | 6.720 | 6.752 | 0.995x |
| 5 | 80 | 16 | no | 28.384 | 28.448 | 0.998x |
| 5 | 80 | 64 | no | 92.960 | 93.024 | 0.999x |
| 5 | 80 | 256 | no | 353.344 | 353.361 | 1.000x |
| 5 | 24 | 1 | no | 6.400 | 6.400 | 1.000x |
| 5 | 24 | 16 | no | 12.448 | 12.512 | 0.995x |
| 5 | 24 | 64 | no | 32.960 | 32.960 | 1.000x |
| 5 | 24 | 256 | no | 110.719 | 110.752 | 1.000x |
| 5 | 20 | 1 | no | 6.368 | 6.368 | 1.000x |
| 5 | 20 | 16 | no | 12.160 | 12.160 | 1.000x |
| 5 | 20 | 64 | no | 28.512 | 28.448 | 1.002x |
| 5 | 20 | 256 | no | 92.928 | 92.960 | 1.000x |
| 5 | 10 | 1 | no | 6.432 | 6.432 | 1.000x |
| 5 | 10 | 16 | no | 9.216 | 9.216 | 1.000x |
| 5 | 10 | 64 | no | 18.112 | 18.048 | 1.004x |
| 5 | 10 | 256 | no | 49.136 | 49.120 | 1.000x |
| 6 | 80 | 1 | yes | 7.296 | 7.104 | 1.027x |
| 6 | 80 | 16 | no | 32.032 | 32.064 | 0.999x |
| 6 | 80 | 64 | no | 104.736 | 104.768 | 1.000x |
| 6 | 80 | 256 | no | 397.793 | 397.761 | 1.000x |
| 6 | 24 | 1 | yes | 6.976 | 6.848 | 1.019x |
| 6 | 24 | 16 | no | 14.080 | 14.016 | 1.005x |
| 6 | 24 | 64 | no | 37.504 | 37.472 | 1.001x |
| 6 | 24 | 256 | no | 124.608 | 124.640 | 1.000x |
| 6 | 20 | 1 | yes | 7.008 | 6.912 | 1.014x |
| 6 | 20 | 16 | no | 13.568 | 13.600 | 0.998x |
| 6 | 20 | 64 | no | 32.064 | 32.064 | 1.000x |
| 6 | 20 | 256 | no | 104.992 | 105.024 | 1.000x |
| 6 | 10 | 1 | yes | 6.944 | 6.848 | 1.014x |
| 6 | 10 | 16 | yes | 10.240 | 10.048 | 1.019x |
| 6 | 10 | 64 | no | 20.384 | 20.352 | 1.002x |
| 6 | 10 | 256 | no | 55.617 | 55.617 | 1.000x |
| 7 | 80 | 1 | no | 7.744 | 7.744 | 1.000x |
| 7 | 80 | 16 | no | 36.512 | 36.480 | 1.001x |
| 7 | 80 | 64 | no | 120.704 | 120.672 | 1.000x |
| 7 | 80 | 256 | no | 460.320 | 460.288 | 1.000x |
| 7 | 24 | 1 | no | 7.456 | 7.520 | 0.992x |
| 7 | 24 | 16 | no | 15.584 | 15.584 | 1.000x |
| 7 | 24 | 64 | no | 42.864 | 42.848 | 1.000x |
| 7 | 24 | 256 | no | 143.615 | 143.584 | 1.000x |
| 7 | 20 | 1 | no | 7.488 | 7.520 | 0.996x |
| 7 | 20 | 16 | no | 15.200 | 15.264 | 0.996x |
| 7 | 20 | 64 | no | 36.512 | 36.512 | 1.000x |
| 7 | 20 | 256 | no | 120.704 | 120.672 | 1.000x |
| 7 | 10 | 1 | no | 7.584 | 7.584 | 1.000x |
| 7 | 10 | 16 | no | 11.200 | 11.232 | 0.997x |
| 7 | 10 | 64 | no | 22.928 | 22.944 | 0.999x |
| 7 | 10 | 256 | no | 63.648 | 63.680 | 1.000x |
| 8 | 80 | 1 | no | 7.744 | 7.744 | 1.000x |
| 8 | 80 | 16 | no | 38.880 | 38.911 | 0.999x |
| 8 | 80 | 64 | no | 130.112 | 130.160 | 1.000x |
| 8 | 80 | 256 | no | 498.272 | 498.144 | 1.000x |
| 8 | 24 | 1 | no | 7.520 | 7.520 | 1.000x |
| 8 | 24 | 16 | no | 16.352 | 16.289 | 1.004x |
| 8 | 24 | 64 | no | 45.792 | 45.792 | 1.000x |
| 8 | 24 | 256 | no | 154.976 | 155.008 | 1.000x |
| 8 | 20 | 1 | no | 7.584 | 7.584 | 1.000x |
| 8 | 20 | 16 | no | 16.032 | 16.000 | 1.002x |
| 8 | 20 | 64 | no | 38.848 | 38.848 | 1.000x |
| 8 | 20 | 256 | no | 130.048 | 130.016 | 1.000x |
| 8 | 10 | 1 | no | 7.616 | 7.584 | 1.004x |
| 8 | 10 | 16 | no | 11.552 | 11.456 | 1.008x |
| 8 | 10 | 64 | no | 24.224 | 24.160 | 1.003x |
| 8 | 10 | 256 | no | 68.224 | 68.192 | 1.000x |
| 16 | 80 | 1 | no | 12.192 | 12.128 | 1.005x |
| 16 | 80 | 16 | no | 69.407 | 69.376 | 1.000x |
| 16 | 80 | 64 | no | 241.312 | 241.296 | 1.000x |
| 16 | 80 | 256 | no | 935.744 | 935.793 | 1.000x |
| 16 | 24 | 1 | no | 11.904 | 11.872 | 1.003x |
| 16 | 24 | 16 | no | 27.424 | 27.424 | 1.000x |
| 16 | 24 | 64 | no | 82.656 | 82.656 | 1.000x |
| 16 | 24 | 256 | no | 289.024 | 289.088 | 1.000x |
| 16 | 20 | 1 | no | 12.032 | 12.000 | 1.003x |
| 16 | 20 | 16 | no | 27.200 | 27.232 | 0.999x |
| 16 | 20 | 64 | no | 69.344 | 69.312 | 1.000x |
| 16 | 20 | 256 | no | 241.472 | 241.472 | 1.000x |
| 16 | 10 | 1 | no | 11.968 | 11.968 | 1.000x |
| 16 | 10 | 16 | no | 19.232 | 19.552 | 0.984x |
| 16 | 10 | 64 | no | 41.824 | 41.856 | 0.999x |
| 16 | 10 | 256 | no | 124.769 | 124.736 | 1.000x |

</details>


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Updates**
* Updated GPU computation on select hardware, including changes to
floating-point accumulation and kernel execution.
* Small differences in numerical results may occur because some
calculations now combine values in a different order.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Avery H <averyh@nvidia.com>

### [a1cebab](https://github.com/flashinfer-ai/flashinfer/commit/a1cebab0def38dde8133370c02bfedaf7c1995cd)

- **作者**: eigen
- **时间**: 2026-11-18T15:41:23Z
- **提交信息**: feat(gemm): offer Cake as the last autotuning candidate for bmm_bf16, svdquant and per-token mm_fp4 (#9656)

### [25bc267](https://github.com/flashinfer-ai/flashinfer/commit/25bc267eb84dd1b28997f62aa4c282a09184c952)

- **作者**: Cindy Zhang
- **时间**: 2026-11-18T11:27:32Z
- **提交信息**: test: isolate MegaMoE CPU tests from visible GPU architecture (#9655)

Default BF16, MXFP8, MXFP4 and NVFP4 host admission and cache tests to
device-free CUDA discovery while preserving explicit architecture mocks.
Match the offending BF16 field in negative configuration checks.

Validation: 342 tests passed with no GPU, simulated SM120, and simulated
SM107; changed-file pre-commit checks passed.

## 📌 Description
MegaMoE batch-invariant CPU tests can fail depending on the visible GPU
architecture.
For example, on an SM120 host,
test_pinned_and_reapplied_knobs_cannot_bypass_admission fails during
base-config construction with:
```
  ValueError: unsupported batch_invariant BF16 MegaMoE architecture: 'sm_120'
```
The test never reaches its intended invalid-knob checks because
configuration validation probes the real CUDA device.

Add a shared, opt-in fixture that defaults CUDA availability to False
for the BF16, MXFP8, MXFP4, and NVFP4 host-test modules.
Architecture-specific tests retain their explicit device mocks. Also
tighten the BF16 invalid-config assertions to match the offending field,
preventing unrelated architecture errors from satisfying those
assertions.

This change only modifies tests; production architecture restrictions
remain unchanged.
## 🔍 Related Issues
Fix https://github.com/flashinfer-ai/flashinfer/issues/9653 

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

  Suggested CI test targets 
  tests/cpu/moe_ep/test_bf16_megamoe_batch_invariant.py
  tests/cpu/moe_ep/test_mxfp8_megamoe_batch_invariant.py
  tests/cpu/moe_ep/test_mxfp4_megamoe_batch_invariant.py
  tests/cpu/moe_ep/test_nvfp4_megamoe_batch_invariant.py


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
The fixture is function-scoped and enabled only for the four affected
modules. Existing device-admission, SM107 compile-target, and
architecture-specific shared-memory tests continue to override discovery
explicitly.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* CPU-only test coverage for MoE batch-invariant scenarios now
explicitly disables GPU availability, making test conditions more
consistent across environments.
* Configuration rejection checks now verify that errors identify the
specific field that is not accepted.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5e578a6](https://github.com/flashinfer-ai/flashinfer/commit/5e578a6c6e1c6fa8f67fdd892e96a3d75bbb7be4)

- **作者**: Szymon Ożóg
- **时间**: 2026-11-18T11:04:34Z
- **提交信息**: Add missing backends for unified MoE benchmark (#9604)

<!-- .github/pull_request_template.md -->

## 📌 Description

Updated the benchmarking route for unifed MoE with missing backends. Low
latency ones capped at 8 tokens because they're slowing down
benchmarking a lot beyond this point

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
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/...`

## Reviewer Notes

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

## Summary

* **New Features**
* Added benchmark options for Prims-TS, Frost low-latency, Cake StepFun,
and cuDNN Frost backends.
  * Added DeepSeek FP8 options for CUTLASS, TRT-LLM, and Prims-TS.
* Added benchmark support for Frost low-latency configurations with up
to 8 tokens.
  * Added renormalized routing support for Cake StepFun benchmarks.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [1dd551c](https://github.com/flashinfer-ai/flashinfer/commit/1dd551c1d94f43a4c95f6d27149e319eb344e57a)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-18T10:50:20Z
- **提交信息**: feat(batch_invariant): `chunk_gated_delta_rule(batch_invariant=True)`, the GDN class `gdn.bf16.c64` (#9405)

<!-- .github/pull_request_template.md -->

## 📌 Description

This PR adds GDN to the batch-invariant mode (#8361): a keyword-only
`batch_invariant: bool = False` on `flashinfer.chunk_gated_delta_rule`,
backed by the class `gdn.bf16.c64` in `flashinfer/batch_invariant/gdn/`.
It is the GDN sibling of the KDA class in #9294 and follows the same
shape: one flag on the existing operator, a typed error that never falls
back, a fingerprint, a documented contract, Lean statements.

### Performance
**Speed against today's non-invariant GDN kernels (ratio = today's time
/ the class's, geomean per regime)**

| part | decode O(10), chunk average | decode O(100), chunk average |
completing step | prefill, whole chunks | prefill, ragged | multi-token
steps | cells >= 0.80 (decode chunk average, whole-chunk prefill) |
|---|---|---|---|---|---|---|---|
| Vera Rubin NVL72 (SM107) | 0.66 | 0.71 | 0.25 | 0.92 | 0.67 | 0.38 | 1
/ 10, 21 / 36 |
| Vera Rubin NVL4 (SM107) | 0.65 | 0.75 | 0.26 | 0.86 | 0.63 | 0.38 | 2
/ 10, 21 / 36 |
| GB300 (SM103) | 0.70 | 0.77 | 0.26 | 0.83 | 0.59 | 0.33 | 2 / 10, 16 /
36 |
| GB200 (SM100) | 0.71 | 0.72 | 0.26 | 0.81 | 0.61 | 0.33 | 1 / 10, 15 /
36 |
| B200 (SM100) | 0.71 | 0.70 | 0.25 | 0.83 | 0.65 | 0.32 | 1 / 10, 17 /
36 |

Regimes: (1) Decode trails 0.80 on every part: a step reads the 32 KB
bf16 state of a (request, v-head) like today's kernel, plus the open
64-token chunk's cached rows (about 28 KB at row 32), through an SM that
loads at a fixed rate, so the chunk average follows the bytes; five
load-order and load-path variants were measured and rejected (two of
them rerun on Vera Rubin NVL72 and GB300). O(10) is lower on the Vera
Rubin parts because today's kernel is faster there at small batch. (2)
The completing step (row 63 of a chunk, one step in 64) folds the chunk
into the fp32 state and is at 0.25 everywhere; it costs the chunk
average about 3 % and a batch at mixed rows more. (3) Ragged prefill is
one prefill call plus one small launch; kernel time is at 0.95 to 1.01
of `auto`, the rest of the gap is host work between the call's metadata
upload and its first kernel, and the tail's cached rows are built by the
slot's next call. (4) Multi-token steps are one launch but a serial
chain of about 3 us per token. Whole-chunk prefill runs the kernel
`auto` picks at high parallelism (kernel time 1.01 to 1.23 of `auto` by
part, above 1 where `auto` takes a slower context-parallel program);
before its first kernel it reads its slot indices back on the host to
refuse a repeated or out-of-range slot, 32 to 84 us per call by part
(median over the grid), which is what puts the column below 1. Rubin
NVL8: not measured (no access). Detail tables are under "Performance
details" below.

**Why.** RL rollouts need the sampler's decode output of a token to
match the trainer's prefill output of the same token bit for bit. For
GDN they do not match today: prefill runs a chunked kernel on an fp32
state, decode runs a per-token recurrence
(`gated_delta_rule_decode_pretranspose`, `gated_delta_rule_mtp`) with
another operation order, and the prefill operator itself has several
routes (the context-parallel programs `auto` picks at low parallelism,
cuDNN, Cake, the native chunked kernel) that give different bits, so a
request's prefill bits also depend on what shares its call.

**What the flag guarantees.** With `batch_invariant=True` a sequence's
output rows, and its state at every multiple of 64 tokens, are those of
the native SM100 / SM103 / SM107 chunked prefill kernel without context
parallelism, from the sequence's own inputs and initial state alone:

| | Property | Meaning |
|---|---|---|
| R1 | Run-to-run determinism | same inputs: same bits, across processes
and CUDA-graph replay |
| R2 | Batch invariance | a sequence's bits do not depend on the batch
size, its neighbours, its position in the call or its slot |
| R3 | Configuration invariance | the class has one configuration
choice, the placement of a multi-token call, and both placements give
the same bits |
| R4 | Cross-path agreement | **prefill == prefill in pieces == decode
== multi-token steps** for the same token |

**How.** The chunked prefill kernel
(`gdn_kernels/blackwell/gated_delta_net_chunked.py`, 64-token chunks) is
deterministic, batch-invariant and prefix-stable, and its fp32 state at
a multiple of 64 tokens is an exact resume point. Prefill is therefore
that kernel, unchanged, pinned to the route without context parallelism
(the operator's automatic rule is untouched for everyone else). Decode
is a new step kernel
(`include/flashinfer/gdn/batch_invariant_decode.cuh`, built through the
nvcc JIT and registered for AOT on SM100 / SM103 / SM107): one launch
per step, one CTA per (request, v-head). It does not update the state
token by token. The pool slot holds the state at the sequence's last
chunk boundary; next to the pool the class keeps the rows since that
boundary and the rows of the open chunk's solve that row `p` depends on
(normalized keys, log2 gates and betas, the M and X rows of the blocked
inverse, the VKS and NV rows, a bf16 copy of the boundary state, the
open-row count). The step computes row `p` of the prefill from them:
every tensor-core product of the prefill is a `tcgen05` bf16 fold, and
the `mma.sync.aligned.m16n8k16` fold with the same operands, k-order and
starting accumulator gives the same fp32 bits, so the step issues them
as `mma.sync` from registers and repeats the prefill's scalar epilogues
operation for operation (built without fast math and with `-fmad=false`;
the one fused multiply-add is the prefill's own, in the 8 x 8
Gauss-Jordan). The 64th row of a chunk folds the next boundary state and
writes it to the pool.

Calls with several tokens per sequence take placements of the same term,
chosen by the call's shape alone (`spec.STEP_MAX_TOKENS = 64`). A call
whose sequences bring fewer than 64 tokens is one launch of the step
kernel's span form: it appends each sequence's run of rows in a loop
with the open chunk's tiles resident in shared memory, commits a chunk
inside the loop when a run crosses a boundary and checks `prefix_lens`
against the slot's count on the device, so it reads nothing on the host
and can be captured in a CUDA graph. A call that brings whole chunks
from chunk boundaries is one prefill call in place over the caller's
tensors: it returns the rows of the open tails too and stores each
sequence's last boundary state as a checkpoint in its pool slot; one
more launch keeps the tails' raw rows, and their cached rows are built
by one span launch before the slot's next call.

### API

```python
out, pool = flashinfer.chunk_gated_delta_rule(q, k, v, g, beta, initial_state=pool, state_indices=slots,
    cu_seqlens=cu_seqlens, use_qk_l2norm_in_kernel=True, gate_domain="log", output_final_state=True,
    backend="auto", batch_invariant=True)
```

* `batch_invariant=True` requires `backend="auto"` (the class replaces
the backends). Without the flag nothing changes for anyone.
* The state is an fp32 pool `[slots, HV, 128, 128]` addressed by int32
`state_indices` and updated in place; `output_final_state=True` returns
the pool. A slot holds the state at the sequence's last 64-token
boundary; the rows since it live next to the pool.
* A call with one token per sequence is a decode step: it reads nothing
on the host and is capturable in a CUDA graph. A call with more tokens
than sequences is a prefill from the slot's state as a chunk boundary.
`prefix_lens` (the operator's existing keyword) says how many tokens
each sequence already has and continues an open chunk: multi-token
steps, and prefill pieces cut anywhere.
* Supported: bf16 packed `q / k [T, HQ, 128]` and `v [T, HV, 128]` with
`HV` a multiple of `HQ`, fp32 log-domain `g` and fp32 `beta` `[T, HV]`,
`use_qk_l2norm_in_kernel=True`, `cu_seqlens` / `cu_seqlens_cpu`,
`output`, a torch build on CUDA 13, SM100 / SM103 / SM107.
* Never falls back: `use_cp`, checkpoints (`state_checkpoints`,
`checkpoint_cu_starts`, `checkpoint_every_n_tokens`,
`checkpoint_state_indices`), `output_state_indices`, the fused gate
(`use_gate_in_kernel`, `A_log`, `dt_bias`, `beta_is_logit`),
linear-domain gates, a bf16 or fp16 state, other head sizes and other
architectures raise
`flashinfer.batch_invariant.BatchInvariantUnsupportedError`. A call that
brings whole chunks reads its slots on the host and refuses duplicate or
out-of-range slots and a `prefix_lens` that disagrees with what the slot
holds; a call of fewer than 64 tokens per sequence checks on the device
and returns NaN rows for a sequence whose slot is outside the pool or
whose `prefix_lens` disagrees with what the slot holds, leaving its slot
as it was (duplicate slots are not detected there); inside a CUDA graph
capture a prefill of whole chunks from chunk boundaries does not read
its slots and trusts them.
* A slot whose cached rows are not built (after a prefill that left an
open tail and before the pool's next step or span call, which builds
them first), a slot index outside the pool, and a sequence whose
`prefix_lens` is not where its slot's open chunk ends return NaN rows
instead of another sequence's bits; the slot is left as it was. A step
captured in a CUDA graph cannot build a tail: run the first call after a
prefill eagerly (capturing it raises).
* The pool is identified by its storage, offset and head count, so a
view from the pool's first slot or a `detach()` of the same buffer is
the same pool (a view that starts at another slot is another pool, with
its own open rows), and the cached rows (4.6 MB per slot at 16 / 48
heads, 1.1 MB more once a prefill has left an open tail in the pool) are
released with the storage. They are allocated at the pool's first call
for every slot the storage holds from the pool's offset, so a pool
carved from a larger buffer should get a storage of its own; that first
call cannot be captured in a CUDA graph.
* `flashinfer.batch_invariant.fingerprint("chunk_gated_delta_rule")`
digests the prefill kernel source, the l2-norm source, the gate
conversion, the step kernel header, its launcher and the module that
sets the step kernel's build flags.

### Lean

`lean/BIKernels/Gdn.lean` models the kernel as an opaque chunk step and
proves, under the causality hypothesis the GPU tests check bit for bit
(the outputs of a chunk prefix are the prefix of the chunk's outputs),
that the decode row equals the prefill row at every position
(`decode_eq_prefill`), that replaying the open chunk through the prefill
gives the same row (`replay_eq_prefill`, the second placement), that the
pool's commit rule carries exactly the prefill's boundary states
(`pool_eq_stateAfter`, `extend_boundary`), and that a packed call is the
per-sequence terms (`batch_term`); the generated `GdnCases.lean` pins
the count arithmetic on the Python specification's cases. `lake build`,
`lake exe gdnconformance` and `lake exe axioms` (0 sorry, 0 violations)
pass on this head with the MoE class of #9283 in the same library. The
pool's bookkeeping is not modelled; that the step kernel's cached-row
form is the chunk step's row `p` is the hardware-side hypothesis,
discharged bit for bit by the tests below.


### Performance details

**The mode trades decode speed for the guarantee.** A decode step runs
at 0.56 to 0.83 of today's fastest non-invariant decode averaged over a
chunk (table above); prefill of whole chunks is at parity with `auto` in
kernel time and at 0.83 first kernel to last, the difference being a
read of the slot indices on the host before the first kernel; a prefill
with open tails is at 0.95 in kernel time and 0.64 first kernel to last;
multi-token steps are at 0.32.

Vera Rubin NVL72 and Vera Rubin NVL4 (SM107, CUDA 13.4 image), GB300
(SM103), GB200 (SM100) and B200 (SM100), one GPU each (on the four-GPU
nodes other GPUs were in use during some grids), CUPTI GPU time with a
cold L2 (flush before every iteration), medians, every cell measured in
two fresh processes with the variants in opposite orders (A B B A) and
reported as the geometric mean of the two. `ratio` = today's time / the
class's; above 1 means the class is faster. The tables below are B200
unless they name another part; `benchmarks/bench_batch_invariant_gdn.py`
reproduces the decode chunk average and the whole-chunk prefill rows.

**Decode.** One step with one token per request, replayed as a CUDA
graph. The baseline is the fastest non-invariant decode FlashInfer has
for the cell (`gated_delta_rule_decode_pretranspose` over a bf16 state
pool in every cell). A step's cost depends on its row in the 64-token
chunk, so the table gives single steps at the chunk start (row 0),
mid-chunk (row 32) and the chunk-completing step (row 63, every request
commits), a batch whose requests sit at mixed rows, and the measured
average over the 64 steps of a chunk, which is the number to read.

| heads | B | today | row 0 | row 32 | row 63 | mixed | chunk average |
ratio |
|---|---|---|---|---|---|---|---|---|
| 16 x 48 | 1 | 3.7 | 6.0 | 7.1 | 14.5 | - | 7.2 | **0.51** |
| 16 x 48 | 8 | 9.6 | 9.3 | 11.5 | 27.6 | 11.4 | 11.5 | **0.83** |
| 16 x 48 | 16 | 12.9 | 14.9 | 18.7 | 49.6 | 29.1 | 19.1 | **0.68** |
| 16 x 48 | 64 | 36.7 | 39.7 | 51.7 | 155.3 | 59.3 | 52.6 | **0.70** |
| 16 x 48 | 128 | 68.2 | 70.8 | 91.6 | 292.4 | 91.7 | 92.9 | **0.73** |
| 16 x 48 | 256 | 129.4 | 132.2 | 170.4 | 570.5 | 174.1 | 172.9 |
**0.75** |
| 16 x 32 | 1 | 3.0 | 5.8 | 6.9 | 14.2 | - | 7.0 | **0.43** |
| 16 x 32 | 8 | 6.0 | 7.9 | 9.5 | 21.9 | 9.5 | 9.6 | **0.62** |
| 16 x 32 | 16 | 9.8 | 10.4 | 13.1 | 35.6 | 20.3 | 13.3 | **0.73** |
| 16 x 32 | 64 | 24.6 | 29.0 | 38.9 | 106.8 | 46.5 | 39.1 | **0.63** |
| 16 x 32 | 128 | 45.2 | 50.4 | 65.3 | 199.7 | 65.7 | 66.1 | **0.68** |
| 16 x 32 | 256 | 85.7 | 91.6 | 118.5 | 385.1 | 120.3 | 120.1 | **0.71**
|

By regime (tokens in the step across the batch), geomean / min / cells
at or above 0.80:

| regime | measured | head |
|---|---|---|
| O(10): B = 8, 16 | 64-step chunk average | 0.712 / 0.619 / 1 of 4 |
| O(10): B = 8, 16 | chunk start (row 0) | 1.334 / 0.861 / 4 of 4 |
| O(10): B = 8, 16 | mid-chunk (row 32) | 0.722 / 0.631 / 1 of 4 |
| O(10): B = 8, 16 | completing step (row 63) | 0.287 / 0.260 / 0 of 4 |
| O(10): B = 8, 16 | mixed rows | 0.580 / 0.444 / 1 of 4 |
| O(100): B = 64, 128, 256 | 64-step chunk average | 0.700 / 0.629 / 0
of 6 |
| O(100): B = 64, 128, 256 | chunk start (row 0) | 0.923 / 0.849 / 6 of
6 |
| O(100): B = 64, 128, 256 | mid-chunk (row 32) | 0.709 / 0.633 / 0 of 6
|
| O(100): B = 64, 128, 256 | completing step (row 63) | 0.229 / 0.222 /
0 of 6 |
| O(100): B = 64, 128, 256 | mixed rows | 0.668 / 0.528 / 0 of 6 |
| B = 1 | 64-step chunk average | 0.466 / 0.426 / 0 of 2 |
| B = 1 | chunk start (row 0) | 0.562 / 0.513 / 0 of 2 |
| B = 1 | mid-chunk (row 32) | 0.473 / 0.433 / 0 of 2 |
| B = 1 | completing step (row 63) | 0.231 / 0.210 / 0 of 2 |

Both regimes trail the 0.80 line on the chunk average, and the reason is
the bytes a step reads. A CTA's loads go through its SM at about 27 GB/s
whatever the batch. Today's kernel reads the 32 KB bf16 state of a
(request, v-head) and writes it back. The step reads the same 32 KB copy
of the boundary state plus the open chunk's cached rows: the normalized
keys, the VKS and NV rows (256 B each per open row) and the X and M rows
of the blocked inverse, 0 KB at row 0, about 28 KB at row 32 and 57 KB
at row 63, where the commit adds the 64 KB fp32 state and writes 96 KB.
At batch 256 with 48 heads that is 737 MB at row 32 over 148 SMs, 184 us
against 170 us measured, and the chunk average sits at the mid-chunk
figure; row 0 is near parity (0.74 to 1.02). The rows cannot be folded
into fewer bytes without changing the prefill's rounding: row `p` of the
chunk is a product over the `p` rows before it.

Tried in this iteration and rejected with measurements, each
bitwise-equal where it ran: the state tile issued before the slot's
count is known (6.2 to 6.1 us at batch 1, nothing elsewhere); the
token's rows issued before the slot index is used (5.7 to 5.5 us at row
0 of batch 1, the chunk average 3 to 10 % worse from batch 8); the state
tile through one bulk copy (6.1 to 7.2 us at batch 1, 9.3 to 12.3 at
batch 8) or through plain register loads (131 to 167 us at batch 256);
the cached rows and the output row written as 16-byte stores (no
change).

Levers, none in this PR: a step whose (request, v-head) is split over
several SMs when the launch leaves SMs idle (batch 1 to 4); a commit
spread over the following step was considered and not taken, because the
pool would lag the sequence by a chunk for a caller that reads or
migrates the slot.

On Vera Rubin NVL72 today's decode kernel is faster at small batch than
on B200 (5.7 against 9.6 us at batch 8 with 48 heads, 3.9 against 6.0
with 32) and so is the step (7.6 against 11.5 us), so the picture is the
same with lower ratios below batch 64. No Rubin-specific rule was added:
the kernel has no launch-size threshold to set, and the variants
measured there (token rows and state tile issued early: the chunk
average 5 to 10 % slower from batch 8; cached rows written as 16-byte
stores: within 2 % either way) were not kept. Vera Rubin NVL72, head, us
per step:

| heads | B | today | row 0 | row 32 | row 63 | mixed | chunk average |
ratio |
|---|---|---|---|---|---|---|---|---|
| 16 x 48 | 1 | 3.0 | 4.9 | 5.9 | 11.7 | - | 5.9 | **0.52** |
| 16 x 48 | 8 | 5.7 | 6.2 | 7.6 | 17.4 | 7.6 | 7.6 | **0.75** |
| 16 x 48 | 16 | 6.6 | 8.2 | 10.3 | 26.8 | 16.3 | 10.3 | **0.64** |
| 16 x 48 | 64 | 18.8 | 23.4 | 29.2 | 86.4 | 35.8 | 29.4 | **0.64** |
| 16 x 48 | 128 | 33.8 | 40.5 | 51.7 | 162.9 | 51.4 | 52.0 | **0.65** |
| 16 x 48 | 256 | 63.6 | 75.0 | 95.7 | 311.4 | 96.3 | 96.2 | **0.66** |
| 16 x 32 | 1 | 2.6 | 4.8 | 5.7 | 11.6 | - | 5.8 | **0.46** |
| 16 x 32 | 8 | 3.9 | 5.8 | 7.0 | 16.2 | 6.9 | 7.0 | **0.56** |
| 16 x 32 | 16 | 6.1 | 7.1 | 8.8 | 21.3 | 14.4 | 8.8 | **0.70** |
| 16 x 32 | 64 | 18.1 | 18.2 | 22.4 | 62.6 | 29.4 | 22.5 | **0.80** |
| 16 x 32 | 128 | 27.9 | 29.8 | 36.7 | 112.1 | 36.4 | 36.9 | **0.75** |
| 16 x 32 | 256 | 51.6 | 52.9 | 66.9 | 212.7 | 66.5 | 67.2 | **0.77** |

**Prefill.** The class against `backend="auto"`, eager calls, time from
the call's first kernel to its last in microseconds (`kernel time` sums
the kernels' own durations and leaves out host gaps), B200; geomean /
min / cells at or above 0.80:

| grid | head |
|---|---|
| whole chunks, L = 64 .. 32768 | 0.828 / 0.629 / 17 of 36 (kernel time
1.012) |
| an open tail only, L = 16 | 1.756 / 1.418 / 4 of 4 (kernel time 0.673)
|
| ragged packings (open tails) | 0.648 / 0.490 / 1 of 8 (kernel time
0.947) |

| heads | sequences x tokens | auto | head (ratio) | head, kernel-time
ratio |
|---|---|---|---|---|
| 16 x 32 | 1 x 16 | 158 | 49 (**3.23**) | 0.92 |
| 16 x 32 | 1 x 1024 | 165 | 140 (**1.18**) | 1.20 |
| 16 x 32 | 1 x 1024 + tails | 171 | 207 (**0.83**) | 1.27 |
| 16 x 32 | 1 x 4096 | 202 | 231 (**0.88**) | 0.84 |
| 16 x 32 | 1 x 8192 + tails | 299 | 449 (**0.67**) | 0.77 |
| 16 x 32 | 1 x 32768 | 720 | 1125 (**0.64**) | 0.65 |
| 16 x 32 | 4 x 16 | 72 | 51 (**1.42**) | 0.56 |
| 16 x 32 | 4 x 1024 | 102 | 146 (**0.70**) | 0.94 |
| 16 x 32 | 4 x 1024 + tails | 113 | 230 (**0.49**) | 0.92 |
| 16 x 32 | 4 x 4096 | 214 | 258 (**0.83**) | 0.96 |
| 16 x 32 | 4 x 8192 + tails | 384 | 529 (**0.72**) | 0.93 |
| 16 x 32 | 4 x 32768 | 1326 | 1383 (**0.96**) | 0.98 |
| 16 x 48 | 1 x 16 | 70 | 49 (**1.42**) | 0.54 |
| 16 x 48 | 1 x 1024 | 97 | 141 (**0.69**) | 0.94 |
| 16 x 48 | 1 x 1024 + tails | 102 | 208 (**0.49**) | 0.93 |
| 16 x 48 | 1 x 4096 | 189 | 234 (**0.81**) | 0.97 |
| 16 x 48 | 1 x 8192 + tails | 310 | 444 (**0.70**) | 0.92 |
| 16 x 48 | 1 x 32768 | 1068 | 1125 (**0.95**) | 0.98 |
| 16 x 48 | 4 x 16 | 90 | 61 (**1.46**) | 0.74 |
| 16 x 48 | 4 x 1024 | 149 | 187 (**0.79**) | 1.02 |
| 16 x 48 | 4 x 1024 + tails | 151 | 259 (**0.59**) | 0.98 |
| 16 x 48 | 4 x 4096 | 348 | 386 (**0.90**) | 0.99 |
| 16 x 48 | 4 x 8192 + tails | 633 | 799 (**0.79**) | 0.93 |
| 16 x 48 | 4 x 32768 | 2330 | 2395 (**0.97**) | 0.99 |

Whole chunks run the kernel `auto` also picks whenever the call has
enough parallelism, on the caller's tensors, so the kernel time is at
0.93 to 1.10 of `auto` there; it is above that where `auto` takes a
context-parallel program that is slower for the shape, and 0.65 for one
32768-token sequence with 32 heads, where that program is faster. First
kernel to last, a whole-chunk call is at 0.63 to 0.97 with 48 heads,
lowest for the shortest calls: before its first kernel it reads its slot
indices back on the host to refuse a repeated or out-of-range slot,
which adds 33 to 66 us (median 39) to the span on B200. A prefill with
open tails is the same kernel in one call (kernel time 0.95) plus one
launch that keeps the tails' rows; what remains of the gap first kernel
to last is host work: the checkpoint metadata is uploaded before the
prefill entry validates its arguments. The cost that call defers is the
first call on the slot afterwards, which builds the tail's cached rows
in one span launch (B200, 48 heads, a step after a prefill that left 5 /
37 / 63 open rows, against a plain step): batch 1 52 / 136 / 220 us
against 6 to 7; batch 8 78 / 283 / 487 us against 9 to 11; batch 64 0.29
/ 1.41 / 2.56 ms against 40 to 53 us. On Vera Rubin NVL72: batch 1 43 /
106 / 169 us against 5 to 6; batch 8 48 / 127 / 207 us against 6 to 8;
batch 64 0.18 / 0.78 / 1.40 ms against 24 to 30 us.

**Multi-token decode steps** (secondary). 2 to 32 tokens per request
through the same flag with `prefix_lens`, against the cheaper of today's
multi-token decode kernel and the `auto` prefill, heads 16 x 48, eager
calls, B200:

| B | 2 tokens | 4 tokens | 8 tokens | 16 tokens | 32 tokens |
|---|---|---|---|---|---|
| 1 | 0.44 | 0.34 | 0.34 | 0.33 | 0.32 |
| 8 | 0.36 | 0.33 | 0.33 | 0.34 | 0.32 |
| 64 | 0.33 | 0.32 | 0.33 | 0.35 | 0.22 |
| 256 | 0.31 | 0.31 | 0.33 | 0.35 | 0.19 |

all cells: 0.320 (min 0.171, 0 of 60 at or above 0.80)

Every cell is one launch. The loop's chain is about 3 us per row at
batch 1 (inverse row 0.7, the two state products 0.6, output row 0.6,
row loads and normalization 0.6) against about 1 us per token for
today's multi-token kernel, and the span form keeps its tiles resident
at two CTAs per SM, which is why 32-token steps at batch 64 and 256 are
the lowest cells (0.19 to 0.22).

## 🔍 Related Issues

Follows #8361 (the mode) and mirrors #9294 (the KDA class, same API
shape).

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

- [x] Tests have been added or updated as needed:
`tests/gdn/test_batch_invariant_gdn.py` (bitwise, `torch.equal`
throughout: a prefill followed by token-by-token decode equals the
one-call prefill over head shapes, steep and long-memory gates, lengths
and split points; decode of 1023 and 4096 tokens from zero (`--full`); a
sequence's bits do not change with the batch, its neighbours or its
slot; prefill in pieces cut at multiples of 64 and, with `prefix_lens`,
anywhere; multi-token steps of 2 / 4 / 8 / 16 / 32 tokens; the two
placements of a multi-token call agree; a captured CUDA graph equals the
eager step; a step on a slot without rebuilt rows, or outside the pool,
returns NaN; views of the pool share its state; a replaced state starts
a new chunk through a prefill call; `HV == HQ` and uneven calls; more
than 32 ragged sequences; the operator's other routes give other bits
(so the test would notice the class silently taking one); every refused
argument and an unsupported device raise
`BatchInvariantUnsupportedError`; the fingerprint, the registry and the
specification's arithmetic) and `tests/batch_invariant/test_gdn_lean.py`
(device-free: the generated Lean cases match the Python specification;
the `lake` step runs where a toolchain is installed). Added with the
span form: one span launch against one step per token (2 to 63 tokens),
a wrong `prefix_lens` returns NaN and keeps the slot, a ragged prefill
followed by decode on six slots, a multi-token step replayed as a CUDA
graph, crossing spans on a grid larger than the device with v-heads
sharing a key head, calls of every kind after a ragged prefill, and
capture with a pending tail.
- [x] All tests are passing: the two files above, 104 passed / 2 skipped
(the `lake` step, no toolchain in the image, and the test that spawns
its own pair of processes, which the two recorded runs replace), in two
processes on Vera Rubin NVL72 (SM107); on B200 (SM100) the same files
ran before the seven newest tests were added (97 passed / 1 skipped),
and on Vera Rubin NVL4 (SM107), GB300 and B300 (SM103) and GB200 (SM100)
without those and the two pool-view tests (95 passed / 1 skipped); those
earlier runs predate the four `__syncwarp()` calls in the step kernel,
with which the gate's hash lines are unchanged on B200 and Vera Rubin
NVL72; the second process asserts the output hashes the first recorded.
A separate gate script checks, for head shapes 16 x 32 and 16 x 48,
steep and long-memory gates, lengths 1, 64, 200, 1023, 4096 and 32768
and a nonzero initial state, that stepped decode == one-call prefill ==
prefill in pieces == multi-token steps at every row, at every
chunk-boundary state and at the final state, plus a 40-request batch on
permuted slots: it passes in two processes on each of those parts, and
on B200 and B300 its 26 hash lines are the ones recorded at this PR's
first head. Across architectures the bits are compared on host-generated
inputs, because torch's CUDA `randn` returns other values on parts with
another SM count, host architecture or torch build (which is why hash
lines of device-generated inputs differ on a B300 PCIe card, on the
Grace hosts and on Rubin): the pinned prefill, the class's prefill with
open tails, 200 decode steps and 7-token steps give one digest on B200,
B300, GB200, GB300, Vera Rubin NVL72 and Vera Rubin NVL4. The existing
`tests/gdn` files were run per file on B200 at the first head of this
PR; `lake build`, `lake exe gdnconformance` and `lake exe axioms` (0
sorry, 0 violations) pass on this head.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gdn/test_batch_invariant_gdn.py
tests/batch_invariant/test_gdn_lean.py
tests/gdn/test_prefill_delta_rule.py
tests/gdn/test_prefill_state_indices.py
tests/gdn/test_prefill_auto_backend.py
tests/gdn/test_decode_delta_rule.py`

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

Design choices worth a look:

* **The class is the uncut kernel at every length; there is no
fixed-piece chain.** An earlier design cut long prefills into fixed
pieces to bound latency. A piece boundary inside a chunk is another
arithmetic that a stepped decode cannot reproduce, so it would break
decode == prefill past the first piece. Pieces are still supported, as
calls: cut at multiples of 64 tokens, or anywhere with `prefix_lens`.
* **No replaced-state detection.** The KDA class (#9294) recognises a
slot whose state the caller replaced by a stamp of its first values.
Here a one-token call without `prefix_lens` continues what the slot
holds: the step reads only its count on the device, and a stamp compare
would add a dependent load to every step. A new sequence loaded into a
slot starts with a prefill call (more tokens than sequences) or carries
`prefix_lens`. Say so if the stamp is preferred for symmetry with KDA.
* **The flag is on `chunk_gated_delta_rule` only.** The decode entries
(`gated_delta_rule_decode_pretranspose`, `gated_delta_rule_mtp`) do not
take it; a decode step of the class is the same operator called with one
token per sequence, so one entry and one pool serve every phase.
* **A decode-shaped call's offsets are taken to be `arange(N + 1)`.**
`cu_seqlens_cpu` is validated when given; a device-only `cu_seqlens` is
not read (a decode step reads nothing back). `cu_seqlens` and
`cu_seqlens_cpu` that disagree are a caller error, as on the operator's
other routes.
* **`output_final_state` returns the pool**, whose slots hold boundary
states, not the state after the last token. `max_seqlen` is accepted and
ignored.
* **Calls are traced under the regular prefill trace template**; the
flag is one more keyword of the same signature.

Limitations:

* **The class's bits rest on toolchain facts that only the tests can
show**: `mma.sync` equals the prefill kernel's `tcgen05` products at the
shapes used; the step's `expf` equals the `torch.exp` the prefill path
applies to the gates; and nvcc keeps the step's scalar chain
uncontracted under `-fmad=false`. A toolchain that breaks one of them
fails the bitwise tests (steep and long gates, every row).
`FLASHINFER_EXTRA_CUDAFLAGS` can still override the flags. The
fingerprint digests six source files, the step kernel's build flags
among them, not the toolchain versions.
* **A prefill with open tails defers part of its work.** It is one
prefill call plus one small launch, at 0.95 of `auto` in kernel time and
0.64 first kernel to last, the difference being host work of the
checkpointed prefill entry between the metadata upload and its first
kernel. The tail's cached rows are built at the slot's next call by one
span launch, about 3.4 us per open row at batch 1 (table above). A
builder that computes a tail's rows together instead of row by row is
the follow-up.
* **Multi-token steps are one launch but a serial chain per token**:
about 3 us per row against about 1 us for today's multi-token kernel,
and two CTAs per SM, so 32-token steps at batch 64 and above are slower
than before (0.2).
* **The chunk-completing step is the slow one** and a batch at
independent chunk positions meets it often; see the `mixed` column.
* A decode step and a span call do not validate slots beyond the pool
bounds; duplicate slots in one such call are undefined, as for the
operator's own pool decode. A span call's device-only `cu_seqlens` is
not read on the host; runs outside the call's tokens are ignored on the
device.
* Speculative decode on the class and a fused gate are follow-ups. SM107
is gated and measured on Vera Rubin NVL72 and Vera Rubin NVL4; Rubin
NVL8 is not measured (no access).
* Timings are kernel-level; no end-to-end serving number is included.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an opt-in batch-invariant mode for GDN supporting prefill,
decode, and multi-token processing with per-sequence state. Unsupported
configurations raise an error rather than silently falling back. The
mode supports selected CUDA 13+ GPU architectures.
* **Documentation**
* Added guidance on supported inputs, state-pool requirements, decode
behavior, and batch-invariant GDN usage.
* **Tests**
* Added coverage for GDN consistency across processing modes, chunk
boundaries, varied sequence layouts, state handling, and CUDA graph
replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [9e53ceb](https://github.com/flashinfer-ai/flashinfer/commit/9e53cebb811606a3ee8aa704e1994cd245865bc8)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-11-18T10:02:39Z
- **提交信息**: fix(moe): reject non-contiguous CUTLASS MoE operands (#9640)

<!-- .github/pull_request_template.md -->

## 📌 Description

`cutlass_fused_moe` assumes packed tensor storage but previously
accepted strided views and silently read the wrong elements. For
example, a BF16 `[64, 1024]` slice of a `[64, 2048]` allocation
reproduced the issue on B300: only 1/64 rows matched the contiguous
copy, with a maximum absolute difference of 0.640625.

Reject non-contiguous activations, routing tensors, expert
weights/biases, and output before Python autotuning and in both C++
runner entry points. Callers can explicitly materialize these operands
with `.contiguous()`. Quantization scales and `input_sf` retain their
existing layout contracts.

## 🔍 Related Issues

Fixes #9508

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
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_trtllm_cutlass_fused_moe.py`

Validated with a source JIT build on NVIDIA B300 (SM103), PyTorch
2.13.0+cu130 and CUDA toolkit 13.0.1, on base `1bdba8725` plus this
patch. No installed `flashinfer-jit-cache` artifact was used.

**90 passed, 0 skipped** (744.43 s):
- 32 new cases: eight operands × two strided layouts × public/registered
entry points; each also checks contiguous results against the PyTorch
reference.
- 4 existing FP16 cases and 3 FP8 cases.
- 48 NVFP4 cases, including autotuning and 4over6, plus the
linear/swizzled input-scale comparison.
- Buffered/unbuffered workspace equivalence and CUDA Graph
capture/replay.

```bash
python3 -m pytest -q -ra -x \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_rejects_noncontiguous_operands \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_fp8 \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_nvfp4 \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_moe_nvfp4_unswizzled_input_sf \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_workspace_buffered_matches_unbuffered \
  tests/moe/test_trtllm_cutlass_fused_moe.py::test_workspace_cuda_graph_capture_replay
```

Changed-file pre-commit checks passed, including clang-format, mypy, and
Ruff. Full-repository hooks and the full test suite were not run.

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

AI assistance: implementation and validation were assisted by OpenAI
Codex.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Fused MoE operations now check that inputs, outputs, routing data, and
expert weights are contiguous, and provide a clear error when they are
not.
* Optional scale and bias tensors are also checked for contiguity when
supplied. Make non-contiguous tensors contiguous before calling these
operations to avoid validation errors.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a416ab4](https://github.com/flashinfer-ai/flashinfer/commit/a416ab46e591f2e079285d1c70b0886797fa5496)

- **作者**: Alex Yang
- **时间**: 2026-11-18T09:10:07Z
- **提交信息**: fix(ci): run @flashinfer-bot commands posted by the bot account itself (#9650)

<!-- .github/pull_request_template.md -->

## 📌 Description

Restores `@flashinfer-bot` commands posted by the `flashinfer-bot`
account itself. Maintainer automation, such as the PR watcher, posts
explicit triggers like `@flashinfer-bot run tests/<path>` with that
account's token. Those triggers started CI until #6814, which added a
job guard skipping every comment authored by `flashinfer-bot` so the
handler's own AI scope notes could not trigger it again. Since then
every bot-posted trigger has been skipped before any step runs. There is
no label, no reaction and no error.

Evidence on `ci-bot-commands.yml` runs:

| PR | Bot-posted trigger (UTC) | CI Bot Commands run | Result |
|---|---|---|---|
| #6880 | 2026-11-01 18:20 | 41336141708 success | PR Test started 35 s
later |
| #4738 | 2026-10-26 19:05 | 40383643908 success | PR Test started 33 s
later |
| #6880 | 2026-11-10 06:18 (same command text) | 42767626379 skipped, 0
steps | no CI |
| #7197 | 2026-11-10 06:15 | 42767314520 skipped | no CI until a
maintainer re-posted the command |

All six bot triggers between 10-26 and 11-01 started CI; all five since
the guard landed (on 11-10: #6458, #7180, #7197, #6880, #6711) were
dropped.

Changes:

- **Bot commands run.** The job guard no longer excludes the bot
account. `Check permission` authorizes `flashinfer-bot` by its token
when the whole comment is one `@flashinfer-bot run|rerun|stop` line,
which is what automation posts.
- **Bot echoes never run.** The GitLab CI mirror also posts as
`flashinfer-bot` and echoes text an outsider controls: failure reports
quote JUnit classnames that PR test code can set, newlines included;
"Unknown Command" replies quote the whole original comment; and its AI
notes put model text on a line of its own. Any other bot comment is
refused without consulting the account's admin role, so an echo cannot
launder `@flashinfer-bot run all` onto a head pushed after review.
- **Loop safety keys on content, not author.** Every note the run step
posts goes through `post_note()`, which appends the hidden marker `<!--
flashinfer-bot:ci-bot-commands-note -->`. The job guard skips bot
comments carrying it before checkout, so a note is never read back as a
command and costs no job.
- **Mention stripping closes a bypass.** `_public_prose` removed a
single `@` before the handle, so model text such as `@@flashinfer-bot
run all` became a live command on the reason line of a note, which
starts its own line. It now removes every `@` before the handle,
restoring the line-anchored parser as an independent second layer.
- **Docs.** The design doc describes the rule.

## 🔍 Related Issues

Regression from #6814 (its job guard, added in review to stop notes from
re-triggering the handler).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (The hooks ran on the changed files at
commit time and passed.)

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
`tests/infra/test_sharding/test_bot_run_workflow.py`

`tests/infra/test_sharding/test_bot_run_workflow.py` passes (33 tests,
CPU-only; run locally with a GNU `timeout` on `PATH`). New cases:

- `flashinfer-bot` is authorized for single-line `run`, `run all`,
`rerun failed` and `stop` comments, and refused for a mirror failure
report, an "Unknown Command" echo, an AI note, two command lines and
prose, all without any role lookup.
- Every posting path (advisory, AI full suite, rejection with and
without helper text, head move, label failure, failed post) ends with
the marker.
- The job guard and the run step use the same marker string, and the
guard no longer excludes the account.
- Reasons such as `@@flashinfer-bot run all` and `@@@FlashInfer-Bot
rerun` produce notes the `Parse command` step classifies as `unknown`.

The new cases fail against the current workflow and sanitizer.

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

- `issue_comment` workflows run from the default branch, so this PR
cannot exercise its own handler; the behavior takes effect on merge. The
CPU tests run the checked-in bash steps directly.
- Before #6814 the bot's admin role authorized any of its comments, so
the mirror echoes above could already run commands; #6814 closed that by
accident. This PR keeps it closed while restoring the single-line
triggers. The mirror itself should still neutralize the handle in echoed
text; that is a separate ci-bot change.
- A `flashinfer-bot` comment that mentions the handle and is not one of
this job's marked notes still starts a short job that ends without
executing anything, as before #6814.

AI-assisted.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* The CI bot now accepts valid, single-line `run`, `rerun`, and `stop`
commands from its account. It ignores its own marked notes to prevent
them from being treated as commands.
* Bot-generated guidance and validation messages are marked to
distinguish them from commands.
* **Bug Fixes**
* Repeated `@` characters before the bot handle are now removed from
generated explanations and validation messages.
* **Documentation**
* Updated guidance to describe bot command authorization and marked
notes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [87265fc](https://github.com/flashinfer-ai/flashinfer/commit/87265fcbccee26d5e897e662d7231c77036d9ba0)

- **作者**: feih-nv
- **时间**: 2026-11-18T09:09:35Z
- **提交信息**: test(moe): the Llama4 warp routing path reports local expert indices (#9638)

## 📌 Description

#9513 made `routingIndicesWarpKernel` (Llama4 routing, fewer than 4
tokens) write local expert indices into the CTA map like every other
routing path, but `test_routing_tile_padding` kept a special case
expecting global indices from that path. The two `llama4-warp-ep` cases
fail on `main` since the merge (got local index 0, wanted 32) on every
Blackwell CI target. This drops the special case; the common expectation
(`tile_experts + local_offset == selected expert`) is the contract.

## 🔍 Related Issues

Follow-up to #9513.

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
reviewers may adjust): `tests/moe/test_trtllm_gen_routing.py`

`tests/moe/test_trtllm_gen_routing.py` on B200 (CUDA 13.0 CI container)
at `main` 4d20ab497: 688 passed, 2 failed before; 690 passed, 24 skipped
after.

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

Test-only. The kernel change in #9513 is the intended behavior (local
indices under expert parallelism, as the GEMMs index this rank's
weights); the test's special case was the leftover from the pre-fix
behavior.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Corrected expert ID reconstruction in a padding test so local offsets
are applied consistently across routing paths.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [aab7205](https://github.com/flashinfer-ai/flashinfer/commit/aab72055cb3bc76dc26eb8ecc3c5eba90bc1211f)

- **作者**: Zhang Shuai
- **时间**: 2026-11-18T09:08:21Z
- **提交信息**: feat(moe): optional fc2_input_out for the per-token NvFP4 trtllm-gen MoE (#9232)

<!-- .github/pull_request_template.md -->

## 📌 Description

<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

On the per-token NvFP4 path of the trtllm-gen MoE, the FC2 input is
requantized to FP4 inside `MoE::Runner::run`. The kernel uses those
codes and scales for GEMM2 and then discards them. The caller cannot see
them.

We need them for RL training with an NvFP4 rollout engine: the trainer
replays the exact FP4 rounding the rollout used for the FC2 input.
Otherwise the trainer's fake-quant forward and the rollout kernel round
some values differently, and the log-probs of the two disagree. Today
the only way to get them is to patch the FlashInfer sources at runtime.
This PR adds a supported way.

`trtllm_fp4_block_scale_moe` and `trtllm_fp4_block_scale_routed_moe` get
an optional argument, `fc2_input_out=(codes, block_scales,
token_scales)`. When it is given, a small kernel runs right after the
per-token requantization and copies its output into these caller
buffers:

- `codes`: `uint8 [T, top_k, I/2]`, packed E2M1
- `block_scales`: `e4m3 [T, top_k, I/16]`, linear layout
- `token_scales`: `fp32 [T, top_k]`

The rows are in (token, top-k slot) order, and each row dequantizes as
`e2m1(codes) * block_scales * token_scales`.

Behaviour:

- The default `None` adds no work.
- The buffers may have more rows than the batch, so one allocation can
be reused under CUDA graphs (same pattern as `routing_replay_out`).
- Slots routed to non-local experts are zero-filled.
- Autotuning runs do not write the buffers.
- Requires `per_token_scale`. It is rejected with fused shared experts
or `routing_metadata`.

## 🔍 Related Issues

<!-- Link any related issues here -->

Related: #3024 (`routing_replay_out`, same caller-buffer pattern), #3987
/ #4574 (exposing the FC1 activation for LoRA). RL context: #7939 (the
alternative of running the inference kernel as the training forward).

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

The hooks were run on the files this PR changes (`pre-commit run
--from-ref origin/main --to-ref HEAD`), not with `--all-files`; all pass
(clang-format, mypy, ruff check, ruff format).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/moe/test_trtllm_gen_per_token_moe.py
tests/moe/test_trtllm_gen_routed_fused_moe.py`

`test_fc2_input_out` runs with 1 and 1024 tokens (covering both GEMM2
scale layouts), with and without expert parallelism. It checks that:

- the MoE output is bitwise unchanged;
- rows past `num_tokens` and non-local slots are handled as described;
- the copy matches the reference SwiGLU output after dequantization;
- GEMM2 + finalize recomputed from the copy reproduces the kernel
output;
- CUDA-graph replay writes the same bytes.

`test_fc2_input_out_requires_per_token_scale` and
`test_fc2_input_out_bypasses_trace_apply` cover the argument check and
the Trace Apply fallback.

On GB200, merged with main b7a92c0e4:

- `tests/moe/test_trtllm_gen_per_token_moe.py`: 59 passed, 16 skipped (9
of the 59 are new in this PR).
- `tests/moe/test_trtllm_gen_routed_fused_moe.py`: 375 passed.

Cost when enabled, measured as GPU kernel time of one routed MoE call
with Qwen3-30B-A3B shapes (H=2048, I=768, E=128, top-8):

| tokens | MoE kernels | copy kernel |
|---|---|---|
| 64 | 77 µs | 3.2 µs |
| 1024 | 132 µs | 4.4 µs |
| 8192 | 459 µs | 17.6 µs |
| 16384 | 830 µs | 37.8 µs |

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
* FP4 block-scale MoE calls can optionally save FC2 input values, block
scales, and per-row token scales to caller-provided buffers.
* Capture supports per-token NVFP4, preserves the MoE output, zero-fills
nonlocal expert slots, and leaves unused buffer rows untouched.
  * CUDA graph replay is supported with capture buffers.
* **Limitations**
* Capture requires per-token scales and is not supported with fused
shared experts or prepared routing metadata.
* **Compatibility**
* Trace Apply falls back to the original API when capture is requested.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Shuai Zhang (Worldwide Field Ops) <shuazhang@login-ptyche01.ptyche.clusters.nvidia.com>

### [d6dc1be](https://github.com/flashinfer-ai/flashinfer/commit/d6dc1bec61d669c0aa0fe4f6643a3c8b3b570b8d)

- **作者**: x41lakazam
- **时间**: 2026-11-18T08:30:15Z
- **提交信息**: feat(moe-ep): opt-in multimem (NVLS) NVLink barrier for MegaMoE (#9389)

## 📌 Description

Replace EP barrier (`TokenInPullTokenBackPush.nvlink_barrier`) from a
loop of atomics (`red.release.sys.global.add.s32`) by a single NVLS
reduction (`multimem.red`)

Gated behind `MEGA_MULTIMEM_BARRIER` (default **OFF** → generated code
is
bit-identical to today). When ON, the host resolves the NVLS multicast
base
(`get_multicast_tensor`) and passes it to the kernel; if NVLS is
unavailable the
code falls back to the peer-atomics loop. Requires Blackwell NVL
(NVSwitch/NVLS).

Isolated, the primitive is ~1.8× faster (GB200 barrier micro-bench, flat
across world 2–16), and numerics are bitwise-identical with the gate OFF
and ON.
Disclaimer: end-to-end it doesn't improve performance at the shapes
tested (EP4, tok
8/64): small-batch MegaMoE is bound by the megakernel's fixed structural
latency,
not the barrier (~2 µs of the kernel time). So this lands as a correct,
reusable
NVLS barrier primitive for cases where the barrier is actually the
bottleneck
(higher EP / sync-bound shapes), not as a measured e2e win yet.

## 🔍 Related Issues

_None._

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Numerics: multi-rank bitwise-equality test (M02) passes with the
gate OFF **and** ON on 4× GB200.
- [x] Barrier micro-benchmark (GB200): single `multimem.red` vs the
peer-atomics loop = 1.54/1.88/1.88/1.81× at world 2/4/8/16.
- [ ] Added/updated repo unit tests (change is behind an off-by-default
env gate).

## Reviewer Notes

- Default-OFF, bit-identical baseline — no risk to the current path.
- E2E is honestly neutral at EP4 (tok8: 65.7→65.2 µs; tok64 +0.7%,
noise). Value is a correct NVLS barrier primitive, not an e2e win for
these shapes.
- `multimem` applies only to the barrier; the combine (token-back) is a
reduce-scatter to one owner, so NVLS does not fit it.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added optional multicast-based synchronization for distributed MoE
operations, enabled with `MEGA_MULTIMEM_BARRIER=1` when supported.
* When multicast mapping is unavailable or fails, operations continue
using the existing synchronization method. The option remains disabled
unless explicitly enabled, preserving current behavior by default.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [9e37595](https://github.com/flashinfer-ai/flashinfer/commit/9e37595004d839e934a5444b4a71d6026034b136)

- **作者**: Panda
- **时间**: 2026-11-18T08:06:02Z
- **提交信息**: fix(decode): reject unsupported CUDA-core split disabling (#6458)

<!-- .github/pull_request_template.md -->

## 📌 Description

Reject `disable_split_kv=True` when `BatchDecodeWithPagedKVCacheWrapper`
resolves to CUDA-core decode. That planner has no disable-split
argument, so `plan()`, `workspace_size()`, and `fast_decode_plan()`
previously accepted the option while silently leaving split scheduling
enabled.

The error is raised before metadata transfer or compiled planning. The
default `False` and supported FA2 tensor-core controls remain unchanged;
the message directs callers that need the option to
`use_tensor_cores=True, backend="fa2"`. Auto cuDNN resolution remains
ahead of this check. A rejected CUDA-core replan preserves the previous
valid cuDNN route, so the wrapper can still run its existing plan.

`workspace_size()` also rejects the cuTile backend with
`NotImplementedError`, consistently with the existing
unsupported-backend gate. cuTile planning bypasses the C++ planner and
its run path allocates scratch internally; querying the CUDA-core module
would report another backend's buffer requirements. This applies with
the split flag both off and on, and leaves ordinary cuTile `plan()`
behavior unchanged.

**Release note (compatibility):** CUDA-core decode now raises
`ValueError` for `disable_split_kv=True` in `plan()`,
`fast_decode_plan()`, and `workspace_size()`; these calls previously
ignored the flag. Use `backend="fa2", use_tensor_cores=True` to disable
splitting, or retain `disable_split_kv=False` for CUDA-core decode. The
same migration note is included in the rendered attention API
documentation.

## 🔍 Related Issues

Related to the `disable_split_kv` side note in #5107. This does not
close the issue's FP32-partial precision problem or replace #5166, which
changes the split partial buffers rather than the Python flag contract.

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
Reason: not requested; the suggested targets cover the affected decode
contract and kernels.

Suggested CI test targets: `tests/utils/test_decode_split_contract.py
tests/attention/test_batch_decode_kernels.py`

Current rebase on main `9df33e23`, final head `a08d5ee6`:

- Reproduced the reported planner-argument assertion on rebased
`cf8b036e`: **12 failed, 32 passed**. Indexing `disable_split_kv` from
the front (15 for workspace sizing, 17 for both planning entry points)
gives **44 passed, 0 skipped** with the same suite. The Boolean identity
assertion still checks both flag values, all three entry points, and
both metadata modes.
- RTX 5060 Ti / SM120, Torch 2.13.0+cu130, CUDA toolkit 13.2: fresh
source JIT in an isolated cache passed **6 expected CUDA-core rejections
and 12 FP64 forward comparisons**. B1/Hq8/Hkv2/D128/page16/S256,
FP16/NHD; CUDA-core default and FA2 tensor-core with flag off/on, each
in both metadata modes. Maximum absolute error: 0.0001448553; maximum
NRMSE: 0.0003287165. This uses the same probe and numerical thresholds
as the earlier validation.
- All applicable changed-file pre-commit hooks passed, including mypy
and pinned Ruff. The API compatibility note parses as reStructuredText.
Full repository hooks, full Sphinx build, and the upstream hardware CI
matrix were not run.

CPU reproduction command, before and after the test-only fix:

```bash
CUDA_VISIBLE_DEVICES='' PYTHONPATH=. .venv/bin/python -m pytest -q \
  tests/utils/test_decode_split_contract.py
```

GPU checks used the current checkout's Python and newly built kernels,
with the existing dependency environment and matching pinned third-party
sources; no packages were installed. The final code changes after these
runs are documentation-only, and the executable Python AST is unchanged.
No cuTile-kernel, captured CUDA graph, B100 batch-invariance, or
performance result is claimed. Final-head upstream CI still requires
maintainer authorization.

<details>
<summary>Historical validation before this rebase (published head
9e13a030)</summary>

Added actual-public-API CPU regression tests for all three entry points,
default/tensor-core controls, validation before metadata copies, and
cuDNN/cuTile/auto dispatch boundaries. Validation:
- Normal upstream pytest collection: 44 CPU public-API tests passed (2
existing Cutlass deprecation warnings). The prior 36-case suite failed
in 4 rejected-replan cases against the initial PR implementation and
passed after route preservation. The final 44-case suite fails in all 8
new cuTile workspace-query cases against `8bc2096`, then all 44 pass
after adding cuTile to the unsupported-query gate. The new cases cover
both split-flag values, tensor-core flags, and wrapper metadata modes,
and reject before metadata transfer or module selection. The
rejected-replan cases create a valid cuDNN auto plan, reject a CUDA-core
replan through `plan()` or `fast_decode_plan()`, and verify that the
existing plan still routes to cuDNN through a backend spy. They do not
execute cuDNN kernels.
- RTX 5060 Ti, SM120, Torch 2.13.0+cu130; JIT kernels built from the
pinned source checkout and reused for the Python-only review fix: all 6
fresh-wrapper unsupported calls raised the expected `ValueError`. This
smoke was rerun on the final Python implementation.
- B1/Hq8/Hkv2/D128/page16/S256, FP16/NHD: CUDA-core default and FA2
tensor-core with the flag off/on, each in both wrapper metadata modes.
All 12 post-plan/post-fast-plan forward comparisons passed against FP64
attention of the same FP16 inputs (max abs 0.000144856; max NRMSE
0.000328717).
- Changed-file pre-commit hooks passed. The full repository hooks and
full hardware test matrix were not run.

No graph capture/replay or performance claim. The GPU smoke validates a
small supported case, not every device/shape.

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

The cuTile follow-up is documented: `plan()` currently ignores this flag
on that backend. Its execution behavior is unchanged in this patch. The
public parameter docs now distinguish FA2 tensor-core and CuTe-DSL
planning support from CUDA-core rejection.

This deliberately changes an unsupported combination from silent
acceptance to `ValueError`; it does not add no-split support to the
CUDA-core scheduler. A custom caller that passes `disable_split_kv=True`
on CUDA-core decode will now fail. The source audit below narrows the
known downstream exposure; it does **not** make the API behavior change
globally non-breaking or settle release/deprecation policy.

<details>
<summary>Downstream compatibility: pinned source audit,
2026-10-14</summary>

| Project / inspected revision | Actual flag and wrapper path | Exposure
to the new CUDA-core rejection |
| --- | --- | --- |
| vLLM `8a8e2baa` | Batch invariance can set
[`disable_split_kv=True`](https://github.com/vllm-project/vllm/blob/8a8e2baa02cdd3d98ee99dbead0a8c9943a97410/vllm/v1/attention/backends/flashinfer.py#L760-L767).
Both eager and CUDA-graph `BatchDecodeWithPagedKVCacheWrapper`
constructors explicitly set
[`use_tensor_cores=True`](https://github.com/vllm-project/vllm/blob/8a8e2baa02cdd3d98ee99dbead0a8c9943a97410/vllm/v1/attention/backends/flashinfer.py#L1311-L1348);
regular and fast planning preserve that wrapper. | No affected call
identified in this revision. |
| SGLang `c82e8bd5` | Ordinary decode passes `False`. Graph decode
passes `True` only in the [deterministic branch, which first forces
tensor
cores](https://github.com/sgl-project/sglang/blob/c82e8bd5fe9cad787c2cd3ccf067a1ba5b95e0c4/python/sglang/srt/layers/attention/flashinfer_backend.py#L411-L425).
Both
[eager](https://github.com/sgl-project/sglang/blob/c82e8bd5fe9cad787c2cd3ccf067a1ba5b95e0c4/python/sglang/srt/layers/attention/flashinfer_backend.py#L523-L530)
and [graph
wrappers](https://github.com/sgl-project/sglang/blob/c82e8bd5fe9cad787c2cd3ccf067a1ba5b95e0c4/python/sglang/srt/layers/attention/flashinfer_backend.py#L1102-L1114)
use that selection with FA2. Multi-step draft and fast-plan replay
preserve the same relation. | No affected call identified in this
revision. |
| TensorRT-LLM `78313690` | The ordinary batch decode [`plan()` passes
literal
`False`](https://github.com/NVIDIA/TensorRT-LLM/blob/783136904ce2b03303fca05dc74412989ea67fb2/tensorrt_llm/_torch/attention/backends/flashinfer.py#L2242-L2304),
even when CUDA cores are selected. CSA2's `True` calls use FA2 [ragged
prefill](https://github.com/NVIDIA/TensorRT-LLM/blob/783136904ce2b03303fca05dc74412989ea67fb2/tensorrt_llm/_torch/attention/backends/sparse/csa2/backend.py#L745-L792)
and [paged
prefill](https://github.com/NVIDIA/TensorRT-LLM/blob/783136904ce2b03303fca05dc74412989ea67fb2/tensorrt_llm/_torch/attention/backends/sparse/csa2/backend.py#L808-L851)
wrappers. | These calls do not reach the new rejection. CSA2's `True`
sites are separate prefill APIs. |

This is static control/data-flow inspection at the linked commits, not
an end-to-end run of these three engines with this patch. It does not
cover all historical releases, forks, custom integrations, or unrelated
backend compatibility. No affected built-in call was identified in the
inspected paths, so this revision retains the explicit error; callers
outside this audit remain subject to the behavior change above.

</details>

Prepared with AI assistance; the API change, backend boundaries, cuTile
scratch ownership, and scope of the tests have been reviewed.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Decode planning now rejects `disable_split_kv=True` for CUDA-core
decode before making planner calls or transferring metadata.
  * Rejected plans no longer change the active cuDNN routing state.
* `fast_decode_plan()` and `workspace_size()` also reject
`disable_split_kv=True` for CUDA-core decode.
* **Documentation**
* Clarified backend support and restrictions for decode workspace
queries and planning, including the unsupported cuTile workspace query.
  * Documented how to disable split-KV using tensor-core decode.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Lewis <khjhs102109@gmail.com>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [820766c](https://github.com/flashinfer-ai/flashinfer/commit/820766cc90a2ac9492e086372e46212f88ed5e32)

- **作者**: Xiyou Zhou
- **时间**: 2026-11-18T07:49:44Z
- **提交信息**: feat(cake_mega_moe): add SM107 NVFP4 MegaMoE EP backend (#9603)

The Cake MegaMoE for NVFP4 activations × NVFP4 expert weights → BF16 on
sm_107a has two fused variants: a route-major mega program, and a
rank-major one with a deduplicated combine. This PR adds both as the
`MoEEpLayer` mega backend `sm107_nvfp4_nvfp4_bf16_cake`, at
expert-parallel world 4 on DeepSeek-V4-Pro's MoE slice (48 experts,
top-6, hidden 7168, intermediate 3072). The route-major variant serves
1024 tokens per rank, the rank-major one 4096 and 8192. A whole
`MoEEpLayer.forward` runs 1.02× to 1.12× faster than FlashInfer's
`sm107_nvfp4_nvfp4_bf16_cutedsl` backend with its cached tuned knobs.

FlashInfer's other Cake MegaMoE backends cover other data types on SM90,
SM100, SM103 and SM120; this one ships on sm_107a only.

| tokens per rank | cake (µs) | cutedsl (µs) | speedup |
| --: | --: | --: | --: |
| 1024 | 146.3 | 149.1 | 1.02× |
| 4096 | 381.1 | 421.1 | 1.10× |
| 8192 | 721.3 | 807.2 | 1.12× |

`MoEEpLayer.forward` (activation staging, router, mega program, top-k
reduce), slowest of 4 ranks, warm-L2 median, mean of 2 interleaved runs,
random top-6 routes. 4× NVIDIA VR NVL72 GPUs (Rubin, sm_107a), CUDA
13.5.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an SM107 Cake NVFP4 MegaMoE backend with configurable execution
across token-size tiers, input staging, routing, and output reduction.
* Added support for quantized or prequantized inputs, optional scaling
values, and strided or unaligned output tensors.
* Added public configuration and backend availability checks for
compatible hardware.

* **Tests**
* Added host-side checks and GPU integration coverage for token tiers,
routing scenarios, and output handling.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b2719b5](https://github.com/flashinfer-ai/flashinfer/commit/b2719b58f617f4a9e2ee1f1628b7ffcae759a9c7)

- **作者**: Bastian Hagedorn
- **时间**: 2026-11-18T07:29:32Z
- **提交信息**: fix(gemm, norm, attention): acquire at cluster scope before reading peer-written DSMEM in the blockscaled split-K GEMMs and the cluster reductions (#8853)

## 📌 Description

Six CuTe DSL kernels wait on an mbarrier with the default CTA-scope
acquire and then read data that a **peer CTA's thread** delivered with
`st.async ... mbarrier::complete_tx` into this CTA's shared memory:

- `flashinfer/gemm/kernels/dense_blockscaled_gemm_sm100_splitk.py`: the
peers fill `reduce_mailbox` with
`st.async.shared::cluster.mbarrier::complete_tx::bytes`
(`_store_shared_remote_v4`); the owner runs
`cute.arch.mbarrier_wait(reduce_mbar_ptr, phase=0)` and reads the
mailbox.
- `flashinfer/gemm/kernels/cute_dsl/low_latency_blockscaled_gemm.py`:
the peers use `cute.arch.store_async_dsmem(..., mailbox_mbar, peer)`
(the same `st.async` complete-tx), the owner runs
`cute.arch.mbarrier_wait(mailbox_mbar, 0)` and loads the shards.
- `flashinfer/cute_dsl/fp4_common.py` `cluster_reduce` (the RMSNorm +
FP4 quant kernels at hidden sizes that need `cluster_n > 1`): every warp
`st.async`s its partial into every rank's `reduction_buffer` slot and
completes that rank's mbarrier; the owner runs
`cute.arch.mbarrier_wait(mbar_ptr, phase=0)` and sums all `cluster_n`
slots.
- `flashinfer/norm/utils.py` `cluster_reduce_multirow` (rmsnorm,
fused_add_rmsnorm, layernorm at the same hidden sizes): the same
all-to-all exchange, with `cute.arch.mbarrier_wait(mbar_ptr,
phase=phase)` before the sum.
- `flashinfer/norm/kernels/gated_residual_next_rmsnorm.py` `_row_sum4`
(cluster of 8 on every call): the peers push their partials with
`st.async ... complete_tx` through inline PTX into this CTA's slot; the
owner runs `cute.arch.mbarrier_wait(mbar, 0)` and loads the slot.
- `flashinfer/cute_dsl/attention/gqa_decode.py`, the
`reduction_mode="atomic"` split-KV path (what `reduction="auto"` selects
for small batches): in each butterfly round the peer stores its colmax /
colsum partial into this CTA's `sR` slot with `CopyDsmemStoreOp` on
`local_mbar`; the owner runs `cute.arch.mbarrier_wait(local_mbar,
phase=0)` and loads the slot. Two waits, four unrolled rounds each.

`cute.arch.mbarrier_wait` lowers to `mbarrier.try_wait.parity` with no
scope qualifier, which is `.acquire.cta`. The peer's complete-tx is a
release at `.cluster` scope performed by the peer CTA's thread. Under
the PTX memory model an acquire at CTA scope only synchronizes with
releases by threads of the same CTA, so the reads after the wait have no
happens-before edge to the peers' stores. (TMA complete-tx is different:
there the async proxy acts for the issuing thread, which is in the
waiting CTA, and `.acquire.cta` suffices.)
`dense_bf16_gemm_sm100_splitk.py` has exactly this situation and fixed
it in #7443 with `_mbarrier_wait_acquire_cluster`, an inline
`mbarrier.try_wait.parity.acquire.cluster.shared::cta.b64` spin; these
six kernels still have the plain wait.

**Change**: add one `mbarrier_wait_acquire_cluster` helper to
`flashinfer/cute_dsl/utils.py` and use it at the wait that guards the
peer-written slots in all six kernels. The helper is a `@cute.jit` loop
over `cutlass.experimental.primitives.mbarrier_try_wait_parity(...,
scope=MBarrierScope.CLUSTER, order=MemOrder.RELAXED)` followed by
`primitives.fence_sync_restrict(MemOrder.ACQUIRE)`, i.e.
`mbarrier.try_wait.parity.relaxed.cluster` plus
`fence.acquire.sync_restrict::shared::cluster.cluster`. That is the
memory model's acquire pattern (a strong read that observes the
completion, then an acquire fence) restricted to `shared::cluster`,
which is where the peers' `st.async` payload lives; it is also the ISA's
own example for acquiring shared memory through the generic proxy. An
`.acquire.cluster` try_wait would also be correct, but it has to cover
global memory as well, so ptxas invalidates L1 after every try_wait; the
restricted fence costs no SASS instruction. In `gqa_decode.py` the two
`cute.arch.fence_acq_rel_cta()` calls that sat directly before these
waits are removed: a CTA-scope fence cannot order anything against the
peer CTA, and the wait now carries the acquire. Nothing else changes;
the other waits in these kernels are on barriers completed by this CTA's
own threads or its async proxy.

No wrong result was observed on hardware, and I do not expect one on
current parts: payload and complete-tx travel together on the DSMEM
path. The ISA does not promise that, which is why #7443 made the same
change. Cost: one relaxed cluster-scope wait and one zero-instruction
fence per split-K reduction, per cluster reduction, or per butterfly
round; the `gqa_decode.py` path loses one `MEMBAR.ALL.CTA` per round.

## 🔍 Related Issues

#7443 (the same fix in `dense_bf16_gemm_sm100_splitk.py`). The six sites
here are every remaining CTA-scope acquire on a barrier completed by a
peer CTA's `st.async` that I found in the FlashInfer CuTe DSL kernels.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff 0.12.8 check + format and codespell
on the changed files; mypy not run.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (Not applicable:
memory-model conformance, no observable failure to test for.)
- [ ] All tests are passing (`unittest`, etc.). (Scoped CI run on the
previous head passed; all six kernels compile with the change.)
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).

Suggested CI test targets:
`tests/gemm/test_low_latency_blockscaled_gemm.py
tests/gemm/test_mm_fp4.py tests/gemm/test_cute_dsl_blockscaled_gemm.py
tests/utils/test_norm.py tests/norm/test_rmsnorm_fp4_quant_cute_dsl.py
tests/norm/test_add_rmsnorm_fp4_quant_cute_dsl.py
tests/norm/test_gated_residual_next_rmsnorm.py
tests/attention/test_cute_dsl_decode.py`

## Reviewer Notes

`cute.arch.mbarrier_wait` itself has no scope argument, so the helper
spells scope and order through the Primitives `mbarrier_try_wait_parity`
and `fence_sync_restrict` (both in `nvidia-cutlass-dsl` 4.8; the tree
already uses the RELEASE form of the fence).
`cutlass.experimental.primitives` is imported when a kernel first traces
the helper, not at module scope, so `flashinfer.cute_dsl` keeps
importing on a DSL older than 4.7 and only these six kernels raise the
usual "needs CuTe DSL 4.7 or newer" error there. Revision history: the
first commits used an inline-asm `.acquire.cluster` spin copied from the
bf16 kernel, then the Primitives `.acquire.cluster` wait; the current
form is the relaxed wait plus the restricted acquire fence, in one
shared helper. `dense_bf16_gemm_sm100_splitk.py` keeps its inline-asm
`.acquire.cluster` spin from #7443, which pays the L1 invalidation;
switching it to the shared helper is a follow-up.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved coordination while split-K matrix operations and clustered
attention, FP4, and normalization workloads wait for shared computation
results.
* These workloads now wait for cluster-level synchronization to complete
before continuing, reducing the risk of using incomplete results. The
update applies consistently across the affected computations and
supports more reliable execution when work is coordinated across compute
units.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b7a92c0](https://github.com/flashinfer-ai/flashinfer/commit/b7a92c0e402eb93411191d79fbd382a59487241f)

- **作者**: kangbintNV
- **时间**: 2026-11-18T05:00:12Z
- **提交信息**: fix(ci): restore documentation checker imports after infra script move (#9639)

<!-- .github/pull_request_template.md -->

## 📌 Description

#8993 moved `pr_checks` into `scripts/infra/`, but the PR documentation
adapter still launched its subprocesses from `scripts/`. As a result,
`python -m pr_checks.check_api_docs` failed with `ModuleNotFoundError`
before producing a report.

Change only the subprocess working directory to `scripts/infra/`,
restoring discovery of all three checker modules. Keep the existing
finding rules and non-blocking workflow behavior unchanged.

## 🔍 Related Issues

Follow-up to #8993. Split out of #9637 so the infrastructure fix can
merge independently.

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

- Verified all three checker modules resolve in real Python subprocesses
using the adapter's configured working directory.
- Before splitting, ran the identical adapter source end-to-end with
`--strict` against main and the #9637 documentation changes: zero new
findings, exit 0 and JSON report produced. Confirmed this PR contains
that exact adapter source.
- Changed-file pre-commit hooks and `git diff --check` pass.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: One-line CPU checker path correction; no GPU tests required.

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): None (checker module resolution and adapter
execution validated directly).

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

AI-assisted fix. Only `SCRIPTS_DIR` changes; no navigation, API
documentation, package code or finding-rule changes. The previous green
workflow included a non-blocking checker execution failure, so
validation checks actual report generation rather than the aggregate job
status.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Chores**
* Updated internal pull request validation tooling to run from its
designated infrastructure location, keeping automated checks aligned
with the repository structure. This maintenance change does not alter
product functionality or the experience of using the application. No new
features, user-facing fixes, or behavior changes are included in this
release.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [8fcbf65](https://github.com/flashinfer-ai/flashinfer/commit/8fcbf653c03f6649e096a256ecc8ac86bab850f9)

- **作者**: Jimmy Zhou
- **时间**: 2026-11-18T04:55:12Z
- **提交信息**: feat(moe): add locality domains for trtllm-gen NVFP4 MoE (#9538)

## Summary

Two changes:

1. **Cubin bump.** `TRTLLM_GEN_BMM` in `flashinfer/artifacts.py` moves
the trtllm-gen batched-GEMM (MoE) cubin package from generator `fdba669`
to `e28a3f0`. The package has the same kernel configs and the same 8,350
cubins. The new generator adds strided MoE outputs (a GEMM can write its
columns into a slice of a wider shared buffer) and shortens kernel names
to stay under nvcc's file-name limit (for example `_fLoadSf` becomes
`_fLdSf`). The headers ship inside the artifact; the new fields default
to the old contiguous layout, so the existing launcher builds unchanged.

2. **Locality Domain support for the NVFP4 MoE**, built on the strided
outputs. On a GPU with two locality domains (dies), both expert GEMMs
are split across the dies. Each die runs its share on its own stream (a
green context) over weights stored in its own memory, so weight reads
stay on the die.
- FC1: die `d` computes intermediate columns `[d*I/2, (d+1)*I/2)` and
writes them into the shared FC1 output.
- FC2: die `d` computes hidden columns `[d*H/2, (d+1)*H/2)` over the
full intermediate size.
- Routing and finalize stay on the caller's stream. The fork/join works
under CUDA graph capture.

## API

- `trtllm_fp4_block_scale_moe` and `trtllm_fp4_block_scale_routed_moe`
gain `localized_weights` (one dict of shuffled weight shards per die),
`localized_streams` (one stream per die) and `localized_sm_count` (SMs
per die stream). This mirrors the CuTe-DSL MoE's localization arguments.
- `split_fp4_moe_weights_by_locality_domain` cuts unshuffled weights
into the per-die shards; shuffle each shard like the full weights.
- `trtllm_get_valid_localized_moe_configs` lists tactics valid at the
per-die shapes; the default tactic and the autotuner use it when
localized.
- Scope: NVFP4 activations and weights with a gated activation, hidden
and intermediate sizes multiples of 256. Biases, per-token scales, LoRA
deltas, fused shared experts, valid (padded) dims, `workspace_buffer`
and routing metadata are rejected. All other paths are unchanged.

No new kernels are needed: every kernel in the package uses TMA stores
and none use output multicast, so all can write a slice.

## Verification

- Cubin package: the public `checksums.txt` hashes to the new
`CheckSumHash`; all 18 headers and a sample of cubins match their
entries.
- New `tests/moe/test_trtllm_gen_localized_moe.py`: 10/10 pass on a
two-die SM107 GPU using per-die green-context streams. Localized output
matches the ordinary launch at 1/64/1024 tokens and two shapes; the
routed path replays under CUDA graph capture; autotuning; argument
checks.
- Existing NVFP4 MoE tests (`test_trtllm_gen_routed_fused_moe.py`,
`test_trtllm_gen_moe_autotune_tactics.py`, NVFP4 cases) pass on the same
GPU.

## Notes for reviewers

- Kernel names changed, so without autotuning a few default picks
between equally ranked kernels may change.
- Localization keeps the full-width weights in the regular arguments for
validation and needs one extra copy of the expert weights for the
shards.
- Performance is not characterized here.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional NVFP4 Mixture-of-Experts execution path that splits
work across two GPU locality domains.
* Added a helper to split FP4 MoE weights and scales into per-domain
shards.
* Added localized tactic discovery and validation based on available GPU
multiprocessors; unsupported configurations are excluded.
* Added support for partitioned GEMM output writes used by localized
execution.
* **Tests**
* Added coverage for localized and routed workloads, CUDA graph replay,
autotuning, and invalid inputs.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [c032cb5](https://github.com/flashinfer-ai/flashinfer/commit/c032cb58be1c8c69fbbac04506e89c47c8912694)

- **作者**: kangbintNV
- **时间**: 2026-11-18T04:11:19Z
- **提交信息**: docs: fix API contracts, Returns rendering and examples (#9358)

<!-- .github/pull_request_template.md -->

## 📌 Description

Correct API documentation that misstates argument names, input
constraints, return types, or backend support, and repair malformed
Returns rendering and REPL examples.

- Give existing Returns sections explicit types and correct indentation,
including FMHA, MNNVL and the Sage quantizer; separate the quantizer
tuple forms from their explanation.
- Correct attention mask names and the meaning of LSE, document Cake
caller-owned LSE buffers, explain PDL auto selection, scope BSA MHA-only
constraints to the CuTe-DSL backend, and include SM107 in GDN state-pool
support.
- Document sampling tuple returns and mode-dependent dtype/shape and
invariance contracts. Clarify replayed-row constraints, communication
dtype overrides and launch counts, and TIRx scheduling inputs.
- Repair multiline prompts in four RoPE examples and qualify the
installation overhead claim and resolved-backend summary.

Only docstrings and RST prose change. API signatures, defaults and
executable behavior are unchanged. Rebased onto main at `a7d9e1865`;
preserve #9326's removal of CAKE training interfaces and drop their
obsolete docstring edits.

## 🔍 Related Issues

Follow-up to #9307.

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

- Compared executable Python ASTs after stripping docstrings: all
changed package Python files match the main base.
- Built six extracted Returns sections with Sphinx: zero warnings or
problematic nodes.
- Parsed and compiled the REPL statements in all four affected RoPE
examples (syntax validation, no GPU execution).
- Changed-file pre-commit hooks and `git diff --check` pass.

- [ ] Tests have been added or updated as needed.
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
      Reason: Documentation-only changes; no GPU test run requested.

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

AI-assisted documentation fix. Rendering checks use isolated Sphinx
projects without importing GPU modules; they do not constitute a
full-site build or GPU correctness validation. No checker, instruction
or test files are added or modified.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Documentation**
* Clarified return values and LSE descriptions across attention,
sampling, and communication APIs.
* Updated guidance on dtype overrides, launch paths, work-list cost
factors, and kernel-download overhead.
* Expanded backend and architecture details, including MHA constraints,
backend selection, PDL behavior, and indexed state-pool handling.
* Clarified replay-path validity and padding rules, plus supported batch
dimensions, input shapes, and output types for sampling.
  * Standardized formatting in RoPE examples.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [639106b](https://github.com/flashinfer-ai/flashinfer/commit/639106be4e25aac87c3f6d32f381d7372e4edbf5)

- **作者**: ranx2026
- **时间**: 2026-11-18T04:09:32Z
- **提交信息**: feat: Windows arm64 build support with the MSVC host compiler (#8431)

<!-- .github/pull_request_template.md -->

## 📌 Description

This series makes FlashInfer build and run on native Windows arm64 with
the MSVC host compiler. It is split into four commits so each can be
reviewed on its own.

1. Build layer: the JIT and AOT paths drive MSVC as the host compiler
(`/bigobj`, the C++ standard flag order MSVC needs, CUDA paths with
spaces, a JIT cache layout under the 260-character path limit, the CCCL
target). Every MSVC switch is gated to Windows; the Linux command lines
are unchanged. apply_cutlass_patches rewrites 3rdparty/cutlass only on
Windows (the sm103 NoSmem epilogue pipeline header under MSVC); Linux
installs leave the submodule untouched.
2. MSVC-compatible headers and attention instantiation templates: no
statement expressions or VLA-style constructs, explicit instantiation
templates that MSVC accepts, Windows-safe math constants, and the two
overflow checks of the trtllm-gen FMHA header written without the GCC
`__builtin_*_overflow` intrinsics.
3. TRT-LLM MoE and quantization kernels: the CUTLASS and TRT-LLM kernel
sources compile with the MSVC host (always_inline lambdas, integer width
assumptions, a launcher struct in place of a generic lambda).
4. JIT spdlog overlay for the MSVC build, and LF line endings for the
digest-checked generated sources.

Behavior on Linux: every change is guarded by the platform or the host
compiler. On Windows the JIT compiles the trtllm-gen GEMM, MoE and
moe_utils modules against a patched copy of the export header
trtllm/gen/CommonUtils.h (XLargeN as a 64-bit constant); a republished
export removes the patch. With the patch in place, moe_utils shows a
second, unrelated failure on Windows (the CUDA device compiler fails on
moeUtils.cu under the MSVC host), tracked separately.

## 🔍 Related Issues

- Follow-ups come as separate PRs: Windows re-assembly of the trtllm-gen
cubins, a Windows CI lane, and the remaining per-kernel Windows fixes.

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).
- [x] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: the build layer touches the JIT flag assembly for every module.

Suggested CI test targets: `tests/attention/test_single_prefill.py
tests/attention/test_rope.py tests/norm/test_gated_residual_rmsnorm.py
tests/gemm/test_mm_bf16.py tests/gemm/test_bmm_fp8.py
tests/utils/test_quantization.py
tests/moe/test_trtllm_gen_fused_moe_routing_renormalize_bf16.py
tests/jit/test_batch_attention_generator_runtime.py`

Linux (GB300, this series on top of the base commit): the eight files
above pass (single_prefill 206 passed, rope 296 passed,
gated_residual_rmsnorm 45 passed, mm_bf16 and bmm_fp8 clean,
quantization 38 passed, moe_routing 16 passed, jit_uri_names 4 passed).
Windows arm64 (GB300 and RTX PRO 6000, MSVC host): the full `tests/`
tree has a result per file on both GPUs; the remaining Windows-specific
failures are tracked separately and not touched here; the MoE call that
motivated the work runs end to end.

## Reviewer Notes

The JIT URI names are shortened on Windows only (commit 1), so Linux
cache paths and the generator runtime test stay as they are.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Expanded Windows support for installation, JIT compilation, and CUDA
runtime loading.
* Windows builds can generate and use attention, GEMM, and
mixture-of-experts kernels.
* Added Windows-specific JIT cache handling, including a shorter default
path with restricted access.
  * JIT cache packages now support Windows library files.
* Improved CLI output when the Windows console cannot encode certain
characters.

* **Bug Fixes**
* Improved compatibility of CUDA and GPU kernel builds with Windows
toolchains.
  * Preserved consistent source-file line endings across checkouts.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: vortex-captain <75063846+vortex-captain@users.noreply.github.com>

### [6919f3d](https://github.com/flashinfer-ai/flashinfer/commit/6919f3d9d4db8c5cb8ffb4d83aac360179acd15b)

- **作者**: eigen
- **时间**: 2026-11-18T03:44:15Z
- **提交信息**: feat(cake_ssd_combined): explicit state_dtype, caller-owned final_states, no final-state storage without final states (#9550)

### [a7d9e18](https://github.com/flashinfer-ai/flashinfer/commit/a7d9e18658d3954527675a3d3a9e7b2ec75b2eae)

- **作者**: eigen
- **时间**: 2026-11-18T02:36:14Z
- **提交信息**: feat(cake_gdn): opt-in exact sequence split for the Cake GDN prefill on SM103 (#9628)

The Cake GDN (Gated DeltaNet) chunked prefill in FlashInfer
(`chunk_gated_delta_rule(..., backend="cake_gdn")`) has two routes: an
unsplit (non-CP) route and a context-parallel route (`use_cp`). Both use
BF16 q/k/v with FP32 state. This PR adds a third route that is opt-in:
`use_affine_split=True`. It is keyword-only and defaults to `False`, so
existing behavior is unchanged. The route is an exact sequence split.
Each sequence is divided into chunk-aligned segments. Pass 1 runs the
existing prefill on each segment along with an identity-column chain,
which yields per-token coefficients and each segment's transfer and
offset. Pass 2 composes the incoming state across segments and corrects
the outputs. The math is exact. The route is SM103 only and takes one
sequence per call (N=1). Sequences of 1024 tokens or fewer run the
unsplit kernel.

NVIDIA GB300 (SM103, sm_103a), CUDA 13.4 (nvcc 13.4.92), driver
580.159.03, torch 2.14.1+cu130. CUDA graph, cold L2, median of 5
alternating groups × 50 replays. N=1, BF16 q/k/v, FP32 gates/state,
initial state present, final state written. Latency is in µs. Shape is
(num q heads, num v heads) with head dim 128. P is the number of
segments, and P=1 means the unsplit kernel runs. Each ratio is baseline
latency divided by split latency, so a value above 1 means the split is
faster. A **bold** ratio means the split is slower than that baseline.

| Shape | T | P | Unsplit (µs) | CP default, `use_cp=True` (µs) | Split
(µs) | Unsplit / split | CP default / split |
|---|---|---|---|---|---|---|---|
| (2, 4) | 1K | 1 | 31.12 | 40.82 | 31.01 | 1.00x | 1.32x |
| (2, 4) | 2K | 4 | 54.82 | 49.60 | 37.06 | 1.48x | 1.34x |
| (2, 4) | 3K | 6 | 78.46 | 56.99 | 40.38 | 1.94x | 1.41x |
| (2, 4) | 4K | 8 | 102.48 | 59.23 | 44.46 | 2.30x | 1.33x |
| (2, 4) | 8K | 8 | 197.50 | 77.89 | 59.62 | 3.31x | 1.31x |
| (4, 8) | 1K | 1 | 31.10 | 41.95 | 30.96 | 1.00x | 1.35x |
| (4, 8) | 2K | 4 | 55.17 | 52.62 | 40.10 | 1.38x | 1.31x |
| (4, 8) | 3K | 5 | 79.17 | 59.71 | 47.44 | 1.67x | 1.26x |
| (4, 8) | 4K | 5 | 103.07 | 64.56 | 55.30 | 1.86x | 1.17x |
| (4, 8) | 8K | 5 | 198.99 | 86.58 | 83.52 | 2.38x | 1.04x |
| (8, 16) | 1K | 1 | 31.36 | 47.42 | 31.33 | 1.00x | 1.51x |
| (8, 16) | 2K | 2 | 55.58 | 59.89 | 52.22 | 1.06x | 1.15x |
| (8, 16) | 3K | 2 | 79.94 | 68.45 | 66.35 | 1.20x | 1.03x |
| (8, 16) | 4K | 2 | 104.11 | 75.47 | 81.78 | 1.27x | **0.92x** |
| (8, 16) | 8K | 2 | 200.78 | 107.55 | 150.50 | 1.33x | **0.71x** |
| (16, 32) | 1K | 1 | 31.95 | 51.60 | 31.90 | 1.00x | 1.62x |
| (16, 32) | 2K | 1 | 56.64 | 67.87 | 56.66 | 1.00x | 1.20x |
| (16, 32) | 3K | 1 | 81.36 | 84.38 | 81.36 | 1.00x | 1.04x |
| (16, 32) | 4K | 1 | 105.97 | 100.29 | 105.92 | 1.00x | **0.95x** |
| (16, 32) | 8K | 1 | 204.42 | 163.28 | 204.43 | 1.00x | **0.80x** |

The Cake GDN prefill also ships the unsplit and context-parallel routes,
with FP32 and aligned state layouts, on sm_100a, sm_103a and sm_107a.
The split route in this PR is sm_103a only.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an opt-in affine-split route for gated delta rule prefill on
supported NVIDIA SM103 hardware, with segmented processing and optional
final-state output.
  * Added automatic split planning and an optional split-count override.
  * Added plan reuse, CUDA graph capture, and concurrent-stream support.
* Existing behavior remains the default unless affine split is enabled.
* **Bug Fixes**
* Added checks that reject unsupported configurations before writing
outputs or launching a kernel.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>

### [e790af2](https://github.com/flashinfer-ai/flashinfer/commit/e790af2e413e07899b691736e60bbf877bb48193)

- **作者**: yeh-sudo
- **时间**: 2026-11-18T02:32:52Z
- **提交信息**: feat(gdn): run GDN prefill on SM110 (Jetson Thor) (#7827)

<!-- .github/pull_request_template.md -->

## 📌 Description

Run `chunk_gated_delta_rule` (GDN prefill) on SM110 (Jetson Thor). Today
the public API rejects SM110, so vLLM on Thor falls back to Triton/FLA.
On Thor, FlashInfer's SM100 kernel is 2.6–8.4× faster than that fallback
(FlashInfer 0.7.2.post1, H=16, Hv=48, head size 128, bf16; 1×512 tokens:
629 → 242 µs, 1×32768: 52.9 → 6.28 ms).

**Changes**

- **Routing:** SM110 uses the SM100 CuTe-DSL kernels for both the non-CP
and the context-parallel (CP) paths. CUDA 13 is required, as for the
other SM110 kernels.
- **CP fixup fix, all architectures:** the fixup kind (`simt_row4` or
`utcmma64/128`) now depends only on the state count and SM count.
Before, an output state pool whose strides weren't 16-byte aligned
(transposed or strided slots) fell back to the fp32 SIMT fixup. So the
same problem gave TF32 or fp32 results depending on the pool layout, and
`test_prefill_state_indices_preserves_inner_strides[flashinfer-cp]`
failed on Thor (20 SMs). The UTCMMA fixup now takes an
`aligned_output_state` compile-time flag, part of its cache key. When
the flag is false, the kernel drops the forced 16-byte store alignment
and uses the narrower stores the layout allows.
- **`use_cp="auto"` on SM110 (`should_use_cp_sm110_host`):** CP only for
`num_parallel_work` ≤ 4, and only from a minimum `max_seq_len`: 2048 for
1, 3072 for 2–3, 4096 for 4. The SM100 rule (`num_parallel_work * 4 <
num_sms`) would send 1–4 states to CP at any length on Thor's 20 SMs.
`max_seq_len` comes from `max_seqlen` or `cu_seqlens_cpu`, with no
device sync; when neither is given, the rule uses `ceil(total_seq_len /
num_seqs)`. SM100, SM103 and SM107 decide exactly as before.
- **F/P ratio on SM110:** `cp_short_workload_ratio_host` returns 4/5 for
SM110 (the default is 1). It sets `cp_chunk_len` for short CP inputs,
which on Thor means one sequence of 2048–4608 tokens.
- **Tests and benchmark:** the GDN prefill tests run on SM110.
`tests/cpu/gdn/test_cp_auto_rule.py` pins the SM110 thresholds and F/P
ratio without hardware. `benchmarks/routines/gdn.py` adds `--use_cp
{auto,true,false}`, which forces either kernel and is recorded in the
CSV; with `--use_cp true` it passes `max_seqlen=s_qo`, so batched runs
don't plan CP chunks for the packed length.

**Benchmark**

Setup: Jetson Thor (SM110, 20 SMs, GPU clock 1386 MHz), driver 595.78,
CUDA 13.2. `benchmarks/flashinfer_benchmark.py --routine
chunk_gated_delta_rule` with its default timing (CUPTI, CUDA graphs,
cold L2), bf16, `head_size` 128, one sequence, `num_parallel_work` 1–20
× `max_seq_len` 1024–65536 (180 shapes), each run with `--use_cp true`
and `--use_cp false`.

On these 180 shapes the new rule picks the faster kernel everywhere
except one tie (`num_parallel_work` 5 at 8192: non-CP 0.340 ms vs CP
0.339 ms). The new rule changes the pick on 8 shapes, all from CP to
non-CP, where the SM100 rule took CP although non-CP is faster:

| num_parallel_work | max_seq_len | SM100 rule (CP) | New rule (non-CP)
| Speedup |
|---:|---:|---:|---:|---:|
| 1 | 1024 | 0.067 ms | 0.054 ms | 1.23× |
| 2 | 1024 | 0.082 ms | 0.057 ms | 1.46× |
| 2 | 2048 | 0.109 ms | 0.095 ms | 1.15× |
| 3 | 1024 | 0.092 ms | 0.057 ms | 1.61× |
| 3 | 2048 | 0.109 ms | 0.098 ms | 1.11× |
| 4 | 1024 | 0.098 ms | 0.059 ms | 1.67× |
| 4 | 2048 | 0.117 ms | 0.096 ms | 1.21× |
| 4 | 3072 | 0.154 ms | 0.137 ms | 1.12× |

F/P: over 21 lengths from 2048 to 4608, with every `cp_chunk_len` that
is a multiple of 64 timed, 4/5 picks a `cp_chunk_len` 1.2% slower than
the fastest on average (default 1: 2.1%), and never more than 3.5%
slower. The full sweep tables are in [my reply to the
review](https://github.com/flashinfer-ai/flashinfer/pull/7827#issuecomment-6789845117).

Every Qwen3.5 config in `benchmarks/bench_gdn_prefill.py` has
`num_parallel_work` ≥ 8, so both rules pick non-CP for all of them and
their dispatch on Thor doesn't change.

<details>
<summary>Before/after with 1–4 heads:
<code>microbenchmark/bench_gdn_prefill_sm110_rule.py --use-cupti
--use-cuda-graph --small-heads</code> (<code>bench_fi</code> from
<code>bench_gdn_prefill.py</code>, CUPTI with CUDA graphs)</summary>

```
GPU: NVIDIA Thor [SM110]
old = SM100 rule (num_parallel_work * 4 < num_sms), new = should_use_cp_sm110_host, d=128

Heads            Seqlens           h_qk   h_v  CP old/new      Before       After    Speedup   TFLOPS
-----------------------------------------------------------------------------------------------------
1 head           1x65536              1     1         y/y     0.817ms     0.806ms    1.01x +      5.3
1 head           1x32768              1     1         y/y     0.393ms     0.392ms    1.00x +      5.5
1 head           1x16384              1     1         y/y     0.229ms     0.227ms    1.01x +      4.7
1 head           1x8192               1     1         y/y     0.169ms     0.170ms    0.99x -      3.2
1 head           1x4096               1     1         y/y     0.117ms     0.116ms    1.01x +      2.3
1 head           1x2048               1     1         y/y     0.089ms     0.089ms    1.00x +      1.5
1 head           6144+2048            1     1         y/y     0.176ms     0.178ms    0.99x -      3.0
1 head           4096+4096            1     1         y/y     0.160ms     0.161ms    1.00x -      3.3
1 head           2048+6144            1     1         y/y     0.179ms     0.179ms    1.00x +      3.0
1 head           1024+7168            1     1         y/y     0.183ms     0.183ms    1.00x -      2.9
1 head           2048x4               1     1         y/n     0.148ms     0.110ms    1.35x +      4.9
1 head           1024x8               1     1         n/n     0.098ms     0.100ms    0.98x -      5.4
1 head           8192x8               1     1         n/n     0.415ms     0.437ms    0.95x -      9.8
1 head           8192x16              1     1         n/n     0.582ms     0.582ms    1.00x -     14.8
1 head           8192x32              1     1         n/n     1.151ms     1.154ms    1.00x -     14.9
1 head           1x1024               1     1         y/n     0.070ms     0.064ms    1.08x +      1.0
1 head           1x3072               1     1         y/y     0.099ms     0.102ms    0.97x -      2.0

2 heads          1x65536              2     2         y/y     1.425ms     1.255ms    1.14x +      6.8
2 heads          1x32768              2     2         y/y     0.626ms     0.616ms    1.02x +      7.0
2 heads          1x16384              2     2         y/y     0.340ms     0.342ms    1.00x -      6.3
2 heads          1x8192               2     2         y/y     0.196ms     0.195ms    1.00x +      5.5
2 heads          1x4096               2     2         y/y     0.162ms     0.163ms    0.99x -      3.3
2 heads          1x2048               2     2         y/n     0.120ms     0.106ms    1.14x +      2.5
2 heads          6144+2048            2     2         y/y     0.210ms     0.215ms    0.97x -      5.0
2 heads          4096+4096            2     2         y/y     0.209ms     0.208ms    1.01x +      5.2
2 heads          2048+6144            2     2         y/y     0.217ms     0.217ms    1.00x +      5.0
2 heads          1024+7168            2     2         y/y     0.222ms     0.222ms    1.00x -      4.8
2 heads          2048x4               2     2         n/n     0.165ms     0.164ms    1.01x +      6.5
2 heads          1024x8               2     2         n/n     0.168ms     0.164ms    1.03x +      6.6
2 heads          8192x8               2     2         n/n     0.686ms     0.688ms    1.00x -     12.5
2 heads          8192x16              2     2         n/n     1.154ms     1.151ms    1.00x +     14.9
2 heads          8192x32              2     2         n/n     2.435ms     2.438ms    1.00x -     14.1
2 heads          1x1024               2     2         y/n     0.090ms     0.064ms    1.39x +      2.1
2 heads          1x3072               2     2         y/y     0.126ms     0.125ms    1.00x +      3.2

3 heads          1x65536              3     3         y/y     1.818ms     1.813ms    1.00x +      7.1
3 heads          1x32768              3     3         y/y     0.902ms     0.893ms    1.01x +      7.2
3 heads          1x16384              3     3         y/y     0.490ms     0.476ms    1.03x +      6.8
3 heads          1x8192               3     3         y/y     0.243ms     0.244ms    1.00x -      6.6
3 heads          1x4096               3     3         y/y     0.180ms     0.181ms    1.00x -      4.4
3 heads          1x2048               3     3         y/n     0.133ms     0.108ms    1.23x +      3.7
3 heads          6144+2048            3     3         n/n     0.293ms     0.292ms    1.00x +      5.5
3 heads          4096+4096            3     3         n/n     0.230ms     0.230ms    1.00x +      7.0
3 heads          2048+6144            3     3         n/n     0.303ms     0.301ms    1.01x +      5.3
3 heads          1024+7168            3     3         n/n     0.322ms     0.322ms    1.00x -      5.0
3 heads          2048x4               3     3         n/n     0.218ms     0.217ms    1.00x +      7.4
3 heads          1024x8               3     3         n/n     0.254ms     0.255ms    0.99x -      6.3
3 heads          8192x8               3     3         n/n     1.182ms     1.071ms    1.10x +     12.0
3 heads          8192x16              3     3         n/n     1.766ms     1.771ms    1.00x -     14.6
3 heads          8192x32              3     3         n/n     3.375ms     3.366ms    1.00x +     15.3
3 heads          1x1024               3     3         y/n     0.100ms     0.066ms    1.52x +      3.1
3 heads          1x3072               3     3         y/y     0.140ms     0.138ms    1.01x +      4.4

4 heads          1x65536              4     4         y/y     2.405ms     2.403ms    1.00x +      7.1
4 heads          1x32768              4     4         y/y     1.229ms     1.227ms    1.00x +      7.0
4 heads          1x16384              4     4         y/y     0.619ms     0.615ms    1.01x +      7.0
4 heads          1x8192               4     4         y/y     0.323ms     0.323ms    1.00x -      6.6
4 heads          1x4096               4     4         y/y     0.183ms     0.183ms    1.00x +      5.9
4 heads          1x2048               4     4         y/n     0.151ms     0.117ms    1.29x +      4.6
4 heads          6144+2048            4     4         n/n     0.329ms     0.327ms    1.01x +      6.6
4 heads          4096+4096            4     4         n/n     0.268ms     0.264ms    1.01x +      8.1
4 heads          2048+6144            4     4         n/n     0.292ms     0.292ms    1.00x -      7.3
4 heads          1024+7168            4     4         n/n     0.320ms     0.319ms    1.00x +      6.7
4 heads          2048x4               4     4         n/n     0.254ms     0.252ms    1.01x +      8.5
4 heads          1024x8               4     4         n/n     0.270ms     0.273ms    0.99x -      7.9
4 heads          8192x8               4     4         n/n     1.326ms     1.157ms    1.15x +     14.8
4 heads          8192x16              4     4         n/n     2.433ms     2.435ms    1.00x -     14.1
4 heads          8192x32              4     4         n/n     4.494ms     4.495ms    1.00x -     15.3
4 heads          1x1024               4     4         y/n     0.112ms     0.068ms    1.65x +      4.0
4 heads          1x3072               4     4         y/n     0.170ms     0.148ms    1.15x +      5.4
```

</details>

<details>
<summary>FlashInfer vs FLA/Triton, Qwen3.5 configs: <code>python
benchmarks/bench_gdn_prefill.py --use-cupti --use-cuda-graph
--skip-cudnn</code> (CUPTI with CUDA graphs)</summary>

```
GPU: NVIDIA Thor [SM110]
Models: Qwen3.5 family (397B, 122B, 35B, 27B, 9B, 4B, 2B, 0.8B), d=128

Heads            Seqlens           h_qk  h_v                FI SM110   TFLOPS  FLA/Triton   Speedup
---------------------------------------------------------------------------------------------------
397B/122B TP8    1x65536              2    8                  2.547ms    13.5     12.121ms     4.76x +
397B/122B TP8    1x32768              2    8                  1.287ms    13.3      5.303ms     4.12x +
397B/122B TP8    1x16384              2    8                  0.660ms    13.0      2.485ms     3.77x +
397B/122B TP8    1x8192               2    8                  0.377ms    11.4      1.165ms     3.09x +
397B/122B TP8    1x4096               2    8                  0.204ms    10.5      0.613ms     3.00x +  drift 8.7%
397B/122B TP8    1x2048               2    8                  0.132ms     8.1      0.314ms     2.37x +
397B/122B TP8    6144+2048            2    8                  0.345ms    12.4      1.462ms     4.23x +  drift 2.4%
397B/122B TP8    4096+4096            2    8                  0.288ms    14.9      1.434ms     4.99x +
397B/122B TP8    2048+6144            2    8                  0.348ms    12.4      1.424ms     4.10x +  drift 2.7%
397B/122B TP8    1024+7168            2    8                  0.371ms    11.6      1.400ms     3.78x +  drift 2.1%
397B/122B TP8    2048x4               2    8                  0.309ms    13.9      1.475ms     4.77x +  drift 5.9%
397B/122B TP8    1024x8               2    8                  0.352ms    12.2      1.462ms     4.15x +  drift 2.6%
397B/122B TP8    8192x8               2    8                  1.933ms    17.8     11.006ms     5.69x +  drift 21.7%
397B/122B TP8    8192x16              2    8                  3.063ms    22.4     21.672ms     7.08x +
397B/122B TP8    8192x32              2    8                  5.871ms    23.4     43.296ms     7.37x +

397B/122B TP4    1x65536              4   16                  3.013ms    22.8     22.129ms     7.34x +
397B/122B TP4    1x32768              4   16                  1.567ms    21.9     10.849ms     6.92x +
397B/122B TP4    1x16384              4   16                  0.802ms    21.4      4.885ms     6.09x +
397B/122B TP4    1x8192               4   16                  0.432ms    19.9      2.279ms     5.27x +
397B/122B TP4    1x4096               4   16                  0.237ms    18.1      1.109ms     4.68x +
397B/122B TP4    1x2048               4   16                  0.192ms    11.2      0.597ms     3.11x +
397B/122B TP4    6144+2048            4   16                  0.562ms    15.3      2.892ms     5.15x +
397B/122B TP4    4096+4096            4   16                  0.556ms    15.4      2.849ms     5.12x +  drift 4.9%
397B/122B TP4    2048+6144            4   16                  0.569ms    15.1      2.851ms     5.01x +
397B/122B TP4    1024+7168            4   16                  0.575ms    14.9      2.852ms     4.96x +  drift 2.7%
397B/122B TP4    2048x4               4   16                  0.626ms    13.7      2.928ms     4.68x +
397B/122B TP4    1024x8               4   16                  0.639ms    13.4      2.988ms     4.67x +  drift 2.4%
397B/122B TP4    8192x8               4   16                  3.578ms    19.2     22.458ms     6.28x +  drift 23.3%
397B/122B TP4    8192x16              4   16                  6.058ms    22.7     44.442ms     7.34x +
397B/122B TP4    8192x32              4   16                 12.032ms    22.8     88.565ms     7.36x +

397B/122B TP2    1x65536              8   32                  6.276ms    21.9     43.897ms     6.99x +
397B/122B TP2    1x32768              8   32                  3.144ms    21.9     21.842ms     6.95x +
397B/122B TP2    1x16384              8   32                  1.592ms    21.6     10.440ms     6.56x +
397B/122B TP2    1x8192               8   32                  0.835ms    20.6      4.762ms     5.70x +
397B/122B TP2    1x4096               8   32                  0.447ms    19.2      2.354ms     5.26x +
397B/122B TP2    1x2048               8   32                  0.290ms    14.8      1.399ms     4.83x +  drift 15.8%
397B/122B TP2    6144+2048            8   32                  1.024ms    16.8      5.403ms     5.27x +  drift 17.8%
397B/122B TP2    4096+4096            8   32                  1.066ms    16.1      4.953ms     4.64x +  drift 23.0%
397B/122B TP2    2048+6144            8   32                  0.905ms    19.0      4.967ms     5.49x +
397B/122B TP2    1024+7168            8   32                  0.894ms    19.2      4.889ms     5.47x +
397B/122B TP2    2048x4               8   32                  0.905ms    19.0      5.006ms     5.53x +
397B/122B TP2    1024x8               8   32                  0.977ms    17.6      5.028ms     5.14x +
397B/122B TP2    8192x8               8   32                  6.124ms    22.4     44.219ms     7.22x +
397B/122B TP2    8192x16              8   32                 12.211ms    22.5     88.180ms     7.22x +
397B/122B TP2    8192x32              8   32                 24.494ms    22.4    176.005ms     7.19x +

397B/122B TP1    1x65536             16   64                 13.541ms    20.3     92.076ms     6.80x +
397B/122B TP1    1x32768             16   64                  6.806ms    20.2     46.155ms     6.78x +
397B/122B TP1    1x16384             16   64                  3.477ms    19.8     22.747ms     6.54x +
397B/122B TP1    1x8192              16   64                  1.762ms    19.5     10.180ms     5.78x +
397B/122B TP1    1x4096              16   64                  0.953ms    18.0      4.988ms     5.23x +  drift 2.1%
397B/122B TP1    1x2048              16   64                  0.539ms    15.9      2.554ms     4.74x +
397B/122B TP1    6144+2048           16   64                  1.769ms    19.4     10.135ms     5.73x +  drift 2.4%
397B/122B TP1    4096+4096           16   64                  1.692ms    20.3     10.299ms     6.09x +  drift 3.4%
397B/122B TP1    2048+6144           16   64                  1.750ms    19.6     10.249ms     5.86x +
397B/122B TP1    1024+7168           16   64                  1.799ms    19.1     10.218ms     5.68x +  drift 2.6%
397B/122B TP1    2048x4              16   64                  1.735ms    19.8     10.230ms     5.90x +
397B/122B TP1    1024x8              16   64                  1.936ms    17.7     10.470ms     5.41x +
397B/122B TP1    8192x8              16   64                 12.291ms    22.4     91.668ms     7.46x +
397B/122B TP1    8192x16             16   64                 24.662ms    22.3    185.360ms     7.52x +
397B/122B TP1    8192x32             16   64                 48.913ms    22.5    369.919ms     7.56x +

35B/9B/4B TP1    1x65536             16   32                  6.957ms    19.8     44.277ms     6.36x +
35B/9B/4B TP1    1x32768             16   32                  3.525ms    19.5     21.981ms     6.24x +
35B/9B/4B TP1    1x16384             16   32                  1.789ms    19.2     10.428ms     5.83x +
35B/9B/4B TP1    1x8192              16   32                  0.963ms    17.8      4.987ms     5.18x +  drift 4.3%
35B/9B/4B TP1    1x4096              16   32                  0.514ms    16.7      2.482ms     4.83x +
35B/9B/4B TP1    1x2048              16   32                  0.291ms    14.8      1.249ms     4.29x +
35B/9B/4B TP1    6144+2048           16   32                  1.164ms    14.8      5.102ms     4.38x +  drift 23.0%
35B/9B/4B TP1    4096+4096           16   32                  1.063ms    16.2      5.123ms     4.82x +
35B/9B/4B TP1    2048+6144           16   32                  1.005ms    17.1      5.094ms     5.07x +
35B/9B/4B TP1    1024+7168           16   32                  0.983ms    17.5      5.064ms     5.15x +
35B/9B/4B TP1    2048x4              16   32                  1.033ms    16.6      5.113ms     4.95x +
35B/9B/4B TP1    1024x8              16   32                  1.111ms    15.5      5.191ms     4.67x +
35B/9B/4B TP1    8192x8              16   32                  7.053ms    19.5     44.505ms     6.31x +
35B/9B/4B TP1    8192x16             16   32                 14.057ms    19.6     89.081ms     6.34x +
35B/9B/4B TP1    8192x32             16   32                 28.159ms    19.5    178.060ms     6.32x +

27B TP1          1x65536             16   48                 10.636ms    19.4     67.585ms     6.35x +
27B TP1          1x32768             16   48                  5.365ms    19.2     33.633ms     6.27x +
27B TP1          1x16384             16   48                  2.737ms    18.8     15.711ms     5.74x +
27B TP1          1x8192              16   48                  1.417ms    18.2      7.437ms     5.25x +
27B TP1          1x4096              16   48                  0.758ms    17.0      3.693ms     4.87x +
27B TP1          1x2048              16   48                  0.426ms    15.1      1.843ms     4.32x +
27B TP1          6144+2048           16   48                  1.593ms    16.2      7.366ms     4.62x +  drift 25.2%
27B TP1          4096+4096           16   48                  1.338ms    19.3      7.320ms     5.47x +
27B TP1          2048+6144           16   48                  1.395ms    18.5      7.426ms     5.32x +
27B TP1          1024+7168           16   48                  1.420ms    18.1      7.442ms     5.24x +
27B TP1          2048x4              16   48                  1.417ms    18.2      7.464ms     5.27x +
27B TP1          1024x8              16   48                  1.538ms    16.8      7.633ms     4.96x +
27B TP1          8192x8              16   48                 10.232ms    20.1     67.210ms     6.57x +
27B TP1          8192x16             16   48                 20.135ms    20.5    134.095ms     6.66x +
27B TP1          8192x32             16   48                 39.969ms    20.6    269.007ms     6.73x +

2B/0.8B TP1      1x65536             16   16                  4.414ms    15.6     23.114ms     5.24x +
2B/0.8B TP1      1x32768             16   16                  2.262ms    15.2     11.378ms     5.03x +
2B/0.8B TP1      1x16384             16   16                  1.157ms    14.8      5.566ms     4.81x +
2B/0.8B TP1      1x8192              16   16                  0.615ms    14.0      2.707ms     4.40x +
2B/0.8B TP1      1x4096              16   16                  0.336ms    12.8      1.355ms     4.04x +  drift 2.3%
2B/0.8B TP1      1x2048              16   16                  0.259ms     8.3      0.781ms     3.02x +
2B/0.8B TP1      6144+2048           16   16                  0.726ms    11.8      3.501ms     4.82x +  drift 25.3%
2B/0.8B TP1      4096+4096           16   16                  0.638ms    13.5      3.091ms     4.84x +
2B/0.8B TP1      2048+6144           16   16                  0.721ms    11.9      2.774ms     3.85x +  drift 25.8%
2B/0.8B TP1      1024+7168           16   16                  0.724ms    11.9      2.735ms     3.78x +  drift 25.1%
2B/0.8B TP1      2048x4              16   16                  0.780ms    11.0      2.811ms     3.60x +  drift 18.7%
2B/0.8B TP1      1024x8              16   16                  0.777ms    11.1      2.816ms     3.62x +  drift 23.7%
2B/0.8B TP1      8192x8              16   16                  4.546ms    15.1     23.261ms     5.12x +
2B/0.8B TP1      8192x16             16   16                  8.948ms    15.4     46.681ms     5.22x +
2B/0.8B TP1      8192x32             16   16                 17.800ms    15.4     92.669ms     5.21x +

Sym h32          1x65536             32   32                  9.097ms    15.1     45.972ms     5.05x +
Sym h32          1x32768             32   32                  4.558ms    15.1     23.034ms     5.05x +
Sym h32          1x16384             32   32                  2.335ms    14.7     11.513ms     4.93x +
Sym h32          1x8192              32   32                  1.215ms    14.1      5.683ms     4.68x +
Sym h32          1x4096              32   32                  0.641ms    13.4      2.837ms     4.43x +  drift 5.0%
Sym h32          1x2048              32   32                  0.368ms    11.7      1.417ms     3.85x +
Sym h32          6144+2048           32   32                  1.462ms    11.8      5.708ms     3.91x +  drift 24.6%
Sym h32          4096+4096           32   32                  1.309ms    13.1      5.742ms     4.39x +
Sym h32          2048+6144           32   32                  1.265ms    13.6      5.701ms     4.51x +
Sym h32          1024+7168           32   32                  1.221ms    14.1      5.667ms     4.64x +
Sym h32          2048x4              32   32                  1.285ms    13.4      5.724ms     4.45x +
Sym h32          1024x8              32   32                  1.367ms    12.6      5.859ms     4.29x +
Sym h32          8192x8              32   32                  9.091ms    15.1     46.639ms     5.13x +
Sym h32          8192x16             32   32                 18.118ms    15.2     93.756ms     5.17x +
Sym h32          8192x32             32   32                 36.439ms    15.1    192.643ms     5.29x +
```

</details>

Reproduce the sweep:

```bash
for s in 1024 2048 3072 4096 6144 8192 16384 32768 65536; do
  for h in $(seq 1 20); do
    for cp in true false; do
      echo "--routine chunk_gated_delta_rule --backends flashinfer --batch_size 1 --s_qo $s" \
           "--num_q_heads $h --num_k_heads $h --num_v_heads $h --head_size 128 --use_cp $cp"
    done
  done
done > gdn_cp_sm110_testlist.txt
python benchmarks/flashinfer_benchmark.py --testlist gdn_cp_sm110_testlist.txt --output_path gdn_cp_sm110.csv
```

## 🔍 Related Issues

None.

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
reviewers may adjust): `tests/gdn/ tests/cpu/gdn/`

`pytest tests/gdn/ tests/cpu/gdn/` passes on Jetson Thor (SM110, CUDA
13.2). `test_prefill_state_indices.py` adds a `flashinfer-cp-16-heads`
case and runs the transposed-pool test on SM110.

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

1. **The CP fixup change affects SM100/SM103/SM107 too.** For an output
pool with unaligned strides above the SIMT threshold:
- it now runs the UTCMMA fixup (TF32) with narrower stores, where it
used to fall back to `simt_row4` (fp32);
- the private `_kernel_kind="utcmma*"` override no longer raises
`ValueError` for such pools.

An output pool whose base address isn't 16-byte aligned is still
rejected, as before.
2. **Not tested on B200.** I have no SM100 machine. I checked the B200
kernel choices on Thor by faking 148 SMs: transposed, stride-2 and
misaligned-slot pools gave bit-identical results to a contiguous pool
with `utcmma64`, `utcmma128` and `simt_row4`. The speed of the narrower
stores on strided pools isn't measured on any GPU.
3. **The SM110 thresholds come from single-sequence sweeps.** Without
`max_seqlen`, `chunk_gated_delta_rule` gives the CP kernels the packed
length as their bound (`total_seq_len`, from #5661, unchanged here), so
with several sequences CP plans its chunks for the whole batch. On Thor,
4×4096 with 1 head: `auto` takes CP at 0.271 ms, non-CP takes 0.229 ms,
and passing `max_seqlen` brings CP to 0.244 ms.
4. **`arch = "sm_100"` stays hardcoded** in the non-CP kernel class.
It's only used to look up the tensor-memory column count, and CuTe DSL
has no `sm_110` entry for that.
5. **`backend="cake_gdn"` still rejects SM110.**
6. **Benchmark support table:** `"11.0": ["flashinfer"]` is added for
`chunk_gated_delta_rule` in `flashinfer_benchmark_utils.py` so the
routine runs on Thor. The architecture table in `benchmarks/README.md`
is unchanged.

AI assistance: I used Claude Code to help write the code, tests and
benchmark scripts, run the benchmarks on my Jetson Thor, and draft this
description.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7012479](https://github.com/flashinfer-ai/flashinfer/commit/70124795c5a1b3bb28b259722ff8b521879b01e5)

- **作者**: Bo Li
- **时间**: 2026-11-18T02:13:59Z
- **提交信息**: fix(prims-ts): select weight cache policy per expert (#8496)

## 📌 Description

Prims-TS batched GEMMs choose the L2 cache policy of the weights per
expert: evict-first for experts with a single token tile, the normal
policy for experts whose weights several token tiles reuse. The policy
operands are built through CUTLASS primitives instead of a magic
constant.

- Reuse is determined from adjacent expert ids with the live routing
bounds.
- Operand and scale-factor policy state is prepared once per work tile,
and loop-carried policy state is initialized before the persistent
early-exit scopes.
- The policy covers the runner's tile mapping and the extended TMA
multicast paths.
- BatchM and wider token CGAs, whose routing records span several CTAs,
keep normal caching; explicit policy configuration is validated
accordingly.

A second commit gives the config stub of the captured-schedule CPU tests
the new `weight_l2_evict_first` flag (modelled off); without it three of
those tests fail with an `AttributeError`.

The first commit is Anthony Chang's (@rosenrodt).

### TODO

- [ ] Pass the weight L2 hint to the CastA weight and scale loads of the
MXFP4 x BF16 tactics, after measuring its effect; until then the
per-expert policy does not reach those loads
(https://github.com/flashinfer-ai/flashinfer/pull/8496#discussion_r4489281203).
- [ ] Extend the per-expert policy to BatchM and to token CGAs wider
than one CTA
(https://github.com/flashinfer-ai/flashinfer/pull/8496#discussion_r4492321021).

## 🔍 Related Issues

Layer 2 of the stack
https://github.com/flashinfer-ai/flashinfer/stack/8499 (four PRs):
1. #8495 routing and finalize for precomputed top-k
2. #8496 **this PR**: Prims-TS weight cache policy per expert
3. #8497 Prims-TS MXFP4 x MXFP8 MoE GEMMs
4. #8498 split layer: finalize the experts into the combine input

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

Validated on 8 B300s at the top of the stack (#8498, 7564ad77d) against
plain `main` (4d0c28d83, which includes #7585); no failure that `main`
does not also have. `pre-commit run --from-ref main` passes. The
performance numbers above were measured on an earlier `main` (5f79e6f26)
and have not been re-measured after the rebase.

- `tests/prims_ts` (every file): pass, except the failures `main` has as
well: `test_batched_gemm_fp4_fc1.py::test_eltwise_swap_epilogue_quant`
(6),
`test_batched_gemm_mx.py::TestMxFc1QuantizedEpilogue::test_eltwise_to_mxfp8`
(6) and
`test_batched_gemm_c_row_stride.py::test_partition_offset_{nvfp4,mxfp8}_output`
(4). With the tests the stack adds, `test_batched_gemm_mx.py` runs 67
passed (43 on `main`) and `test_moe_bf16_support.py` 84 passed (53 on
`main`).
- `tests/cpu/prims_ts`: 370 passed;
`tests/jit/test_cute_dsl_strict_key_closure.py`: 33 passed.
- `tests/moe/test_unified_moe_prims_ts.py`: 39 passed, 1 xfailed;
`tests/moe/test_prims_ts_fp8_block_scale_moe.py`: 11 passed.

After the review, rerun at the stack top 45cae150a: this PR adds
63b912c33, which trims the policy tests and makes the FC2 evict-first
test route a single token tile to every expert, so that its weight and
scale loads select evict-first (with the previous token count every tile
kept the normal policy). `tests/prims_ts/test_batched_gemm_mx.py`: 55
passed, 1 skipped, with the same 6 failures as `main`;
`test_moe_bf16_support.py`: 70 passed.

Rebased onto main at 1bdba8725. #8666 added the scale-block argument of
its [32,32] blocks to the DeepSeek FP8 tactic mapping that this PR wraps
in `apply_weight_l2_policy`; the rebase keeps both, so the DeepSeek FP8
tactics with 32-element scale blocks get the per-expert policy as well,
and `test_moe_bf16_support.py` keeps the tests of both. The other
commits are unchanged. At 7ca01ceff:
`tests/prims_ts/test_batched_gemm_mx.py -k evict_first_weights` 2
passed; `test_batched_gemm_fp8_block.py` 34 passed;
`test_moe_bf16_support.py` 63 passed;
`tests/moe/test_prims_ts_fp8_block_scale_moe.py` 12 passed;
`tests/cpu/prims_ts` 369 passed, 2 skipped.

Rebased onto main at 88077bda8 without conflicts; the commits are
unchanged. At aa9006ef0: `tests/prims_ts/test_batched_gemm_mx.py -k
evict_first_weights` 2 passed; `test_batched_gemm_fp8_block.py` 34
passed; `test_moe_bf16_support.py` 63 passed;
`tests/moe/test_prims_ts_fp8_block_scale_moe.py` 12 passed;
`tests/cpu/prims_ts` 369 passed, 2 skipped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **New Features**
* Added an optional L2 cache eviction policy for weight and scale-factor
loads in supported batched GEMM and MoE configurations. Eligible
configurations can apply the policy automatically, while incompatible
settings are rejected during validation.
* **Tests**
* Added regression coverage across supported MX-format configurations,
scheduling modes, and tile settings, including checks for policy
eligibility and validation of incompatible configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Bo Li <22713281+bobboli@users.noreply.github.com>
Co-authored-by: Anthony Chang <27950904+rosenrodt@users.noreply.github.com>

### [4395091](https://github.com/flashinfer-ai/flashinfer/commit/4395091eafddd97746038ade04316aff3ca0e608)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-11-18T02:13:02Z
- **提交信息**: fix(cudnn): keep SM120 prefill kernel off explicit-length token-offset graphs (#9458)

## 📌 Description

On SM120 and SM121, `cudnn_batch_prefill_with_kv_cache` with ragged
offsets and explicit `actual_seq_lens_q` / `actual_seq_lens_kv` returns
NaN or wrong values when the Q/KV storage has padding between sequences,
i.e. when the offsets are not the cumulative sum of the lengths. This
happens with token-unit offsets and with the legacy element-unit
offsets. The cuDNN frontend's SM120 prefill kernel
(`sdpa_fwd_prefill_sm120`) derives each sequence's length from the
prefix sums of the ragged offsets and ignores the explicit lengths, so
it attends to the padding.

This PR deselects that engine for graphs that have ragged offsets and
explicit lengths and do not use `cu_seq_lens`, which leaves the cuDNN
backend engine, and that one honors them. Graphs without explicit
lengths (cumulative lengths), graphs without ragged offsets, the
`cu_seq_lens` path and every other architecture are unchanged. The
deselect runs once per graph build inside the cached builder, not per
call.


`test_cudnn_prefill_explicit_lengths_exclude_storage_padding[False-{q,kv,both}]`
already covers the token-unit case and fails on SM120 and SM121; the
`backend_only=True` variants passed, which isolated the Python engine. A
new test,
`test_cudnn_prefill_element_offsets_explicit_lengths_exclude_storage_padding`,
covers the element-unit case.

## 🔍 Related Issues

The test and the explicit-length contract come from #7438. Found by the
v0.7.5rc1 release validation, where it fails on the RTX PRO 6000
Blackwell and DGX Spark lanes.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

### 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

## Reviewer Notes

Run on a single RTX PRO 6000 Blackwell Server Edition (SM120) with CUDA
13.0, cuDNN backend 9.24 and cuDNN frontend 1.32.3.
`tests/attention/test_cudnn_prefill_token_indptr.py` goes from 3 failed,
138 passed on the unpatched tree to 142 passed with this change,
including the new element-unit test. The element-unit case on the
unpatched tree returned NaN or wrong values, and was correct with the
backend engine only and with unpadded storage.
`test_cudnn_ragged_shape_override.py` gives 10 passed and
`test_cudnn_wrapper_regressions.py` gives 169 passed;
`test_cudnn_prefill_paged_cu_seqlens.py` is skipped on this cuDNN
version. The two `test_cudnn_native_log2.py` failures on that tree are
unrelated and fixed by #9425.

Explicit-length prefill with ragged offsets on SM120 now runs on the
backend engine only; its speed was not measured, and a config that only
the SM120 Python engine could serve would no longer build for such calls
(the existing tests do not hit one). Paged KV with explicit lengths
takes the same path and has no dedicated test. This is a workaround
until the frontend kernel honors explicit lengths. Not run on SM121,
where CI shows the same failure from the same kernel, and not run on
other architectures, where no engine of this name is selected.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved cuDNN attention engine selection for requests that combine
element offsets with explicit sequence lengths, helping ensure padded
storage is excluded from results.

* **Tests**
* Added coverage comparing attention output for padded query and
key/value tensors against a per-sequence reference.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: kahyunnam <kahyunnam@users.noreply.github.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [21e077f](https://github.com/flashinfer-ai/flashinfer/commit/21e077fc80d5f600f8c3f82407d6264333073abe)

- **作者**: Harrison Zhang
- **时间**: 2026-11-18T02:02:49Z
- **提交信息**: fix(prims_ts): exact row max for E4M3 V in fmha context (#8549)

<!-- .github/pull_request_template.md -->

## 📌 Description
<!-- What does this PR do? Briefly describe the changes and why they’re
needed. -->

**Need to change this parameter back to threshold 0 for correctness.**

With E4M3 V, the lazy correction (threshold 8) let P reach 2^8, so the P
scale before the E4M3 cast was 1 and every P below 2^-10 rounded to zero
while the fp32 row sum still counted it. Rows with spread attention lost
part of their probability mass and the output shrank by that fraction,
up to 36-45% on single heads of MiniMax-H3 captures and 2 to 3 dB end to
end on HunyuanVideo-1.5 and H3.

The exact per-tile row max keeps P at or below 1, scaled by 448, which
holds P down to 2^-18. BF16 V keeps the lazy correction, as its P never
passes through E4M3.

**Performance:**
On GB300, FP8 causal H32/Hkv8 D128 S16K went from 816.91 to 880.42 us
(+7.77% mean), and dense S4K went from 150.15 to 160.41 us (+6.83%).
Eight of fifteen all-FP8 cases exceeded 5% in all three runs. These are
cold-L2 CUDA-event measurements; this acceptance is scoped to the
measured cases, not a general performance waiver.

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

- [X] Tests have been added or updated as needed.
- [X] All tests are passing (`unittest`, etc.).
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

* **Bug Fixes**
* Skip-correction threshold setup now applies only when skip-correction
is enabled, VC-Attention is disabled, and values use a 16-bit dtype.
* **Tests**
* Added regression coverage for long-sequence dense attention with BF16
or E4M3 queries and keys, and E4M3 values. The test checks output
against the shared reference when one key dominates.
* Updated reference-model coverage to match E4M3 attention probability
scaling.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [4d20ab4](https://github.com/flashinfer-ai/flashinfer/commit/4d20ab49775258406e4309329962d25c71fcefbc)

- **作者**: Jonathan Dierksen
- **时间**: 2026-11-18T01:22:32Z
- **提交信息**: refactor(infra): move infra scripts and tests into scripts/infra and tests/infra (#8993)

<!-- .github/pull_request_template.md -->

## 📌 Description

Per the CODEOWNERS/test-organization discussion, move infra-owned files
into dedicated `infra` subdirectories so infra can own them without
requiring leads/managers to approve op-PIC reviews:

- `scripts/*` CI/build/test-runner/release tooling → `scripts/infra/`
(incl. `test_sharding/`, `pr_checks/`, `tests/`)
- Op-specific scripts stay in `scripts/`:
`generate_moe_activation_matrix.py`, `sanitize_cute_dsl_moe_swap_ab.py`,
`check_cake_build_manifests.py`, `list_apis.sh`, `modal_runner.py`
- `tests/test_sharding/`, `tests/test_artifacts.py`,
`tests/test_whl_index.py` → `tests/infra/`
- Updated references (workflows, Jenkinsfile, pre-commit, docs,
CLAUDE.md), `scripts.*` → `scripts.infra.*` imports, relative-path depth
in moved scripts/tests, and the nightly staging of the pytest plugin.
- CODEOWNERS: new `scripts/infra/` and `tests/infra/` rules; removed the
now-redundant test_sharding / test_artifacts rules.

Not included (separate PR by @bkryu): redistributing
`tests/test_helpers` and `tests/cpu` into per-op directories.

## 🔍 Related Issues

Slack thread on CODEOWNERS and test file organization.

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
Ran `tests/infra` + `scripts/infra/tests` locally on macOS (no
GPU/torch): the failure set is identical to `main` at the old paths
(environment-dependent torchrun/mpi/timeout tests); `test_artifacts.py`
not run locally (needs flashinfer deps). Moved CPU tests under
`tests/cpu` that touch these scripts pass.
- [x] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: moves CI entrypoints (`scripts/task_*.sh`) and the test runner
used by every lane.

  Suggested CI test targets (optional): `tests/infra/ tests/cpu/`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Refactor**
* Relocated CI, testing, and release tools into a dedicated
infrastructure area, while keeping compatibility entry points for
existing commands.
* Updated automated workflows and test commands to use the relocated
tools; existing workflow conditions and test-selection behavior remain
unchanged.
* Added support for rebuilding test-duration estimates from test results
and monitoring test-run resources.

* **Documentation**
* Updated setup, testing, release, and CI guidance to reflect the tool
relocation.
  * Clarified how targeted test runs relate to GPU test coverage.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [01962ff](https://github.com/flashinfer-ai/flashinfer/commit/01962ffad7e26447e21ed3de4e11c5c9923a5d07)

- **作者**: Guangyun Han
- **时间**: 2026-11-18T01:15:14Z
- **提交信息**: feat(mla): add FP8 split-KV decode and wave-aware mega dispatch (#9274)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replace homogeneous DSv4.1 FP8 sparse-MLA decode with a cooperative CuTe
C++ implementation and reuse the FP8 prefill backbone for throughput.
Public `run` and `run_mega` accept `impl="auto" | "decode-splitkv" |
"decode"` for inline and footer FP8 caches, H=8/16/32/64, D=512. Auto
selects from query/head tasks, SM count, and resident CTA waves.

The low-latency core uses four compute warps per eight-head group, with
a separate loader warp and CUTLASS transaction pipelines for
double-buffered bulk gathers. Eight-head tasks use 32-candidate tiles;
sixteen-head tasks use 64. QK partitions candidates across cooperating
warps; PV partitions the 512 output features. Unfused attention uses
independent CTAs plus a separate merge. The workspace-managed mega path
performs cluster finalization inside the attention launch.
Single-buffered scores have their own consumer-reuse barrier, separate
from the two-stage KV pipeline.

Mega fuses query RoPE and quantization, sparse QK/softmax/PV with sink
normalization, BF16 context rounding, inverse output RoPE, and FP8
output/scales. Learned projections, query normalization, cache
construction, and sparse-index selection remain caller operations.

Caller-managed entries use the same CuTe core while preserving their
scratch strides, 64-candidate chunk boundaries, pitched indices, partial
heads, and separate merge contract. Their reduction supports more than
32 splits. Both cache layouts handle independent main/extra page sizes,
page gaps, and nonzero aligned origins.

The replaced homogeneous FP8 kernel instantiations, the register-heavy
one-warp variant, its unused gather machinery, and the obsolete
tiny-footer cutoff are removed. Shared legacy bodies remain where other
model/cache formats and BF16 computation still use them. Existing
licenses and original baseline library/kernel sources were not changed.

Implementation and validation were prepared with Codex assistance.

Review follow-up at `49425854d`: corrected the two new launch files to
Apache-2.0, documented implementation selection versus mega fusion and
CTA ownership at the cluster barrier, and kept the decode scheduling
benchmark harness local. Migration and legacy-removal tracking: #9599.
These commits change comments/licenses and remove the local-only
benchmark from the PR; executable C++ tokens and Python test logic are
unchanged from the validated `310a1ed89`. Changed-file pre-commit checks
pass, and all 157 decode test cases still collect. GPU and benchmark
results below retain their actual measured revision.

### Matched performance

RTX PRO 6000 Blackwell Server Edition, 188 SMs, 96 GB, driver 615.71.10.
Baseline is original main `18fb0bfcc6d7e8a0c25a7784af559cc1e58124cb`;
replacement is `310a1ed89`. Both checkouts use the same external fixture
and transform helpers, with identical input hashes. Compilation and
setup are outside timing.

Public `auto`; warm-L2 CUDA Graph replay; 100 ms warmup and 1000 ms
measurement per mode; CUDA-event timing, natural clocks, serialized GPU
execution, alternating mode order. Times below are medians in
microseconds. Attention-only includes partial reduction. Complete
separate pipelines include Q RoPE, attention, inverse output RoPE, and
FP8 casting/scales. Mega is compared with that complete original
pipeline and checked exactly against the current separate
implementation.

Across all 46 cases, **unfused attention ranges from 0.2% slower at its
worst point to 2.33x faster**, and **mega is 1.16x–2.49x faster than the
original complete pipeline**. The worst attention-only point is
T1/H64/K512 inline: 9.766 us original versus 9.786 us CuTe, a 0.020 us
difference. There are no public-auto mega regressions in this matrix.
The complete separate-transform chain still has three inline cases
3.7–5.2% slower (at most 0.62 us), despite attention-core parity; those
measurements are retained below.

Canonical dual-cache workload: H64, D512, T=7B, 128 SWA + 512 compressed
FP8 entries, independent 32,768-token histories per request.

| Local Q | Gathered KV | Layout | Baseline separate kernels | CuTe
separate kernels | CuTe mega | Baseline / mega | Baseline / CuTe
separate |
| --- | --- | --- | ---: | ---: | ---: | ---: | ---: |
| 7 | 128 + 512 | inline | 20.24 | 16.96 | 14.70 | 1.376x | 1.193x |
| 49 | 128 + 512 | inline | 88.23 | 42.66 | 39.49 | 2.234x | 2.068x |
| 98 | 128 + 512 | inline | 158.45 | 87.90 | 80.60 | 1.966x | 1.803x |
| 119 | 128 + 512 | inline | 160.22 | 89.66 | 81.18 | 1.974x | 1.787x |
| 140 | 128 + 512 | inline | 162.68 | 90.67 | 80.88 | 2.011x | 1.794x |
| 280 | 128 + 512 | inline | 321.96 | 150.38 | 129.28 | 2.490x | 2.141x
|

<details>
<summary>All 46 paired cases, including unfused attention</summary>

Single-cache sweep: T=1/4/16/32/64, H=8/16/32/64, K=512, inline/footer,
1,048,576 cached tokens. The six canonical rows use the dual-cache
workload above.

| T | H | KV | Layout | Original attention | CuTe attention | Original
complete | CuTe separate | CuTe mega | Original complete / mega |
|---:|---:|---|---|---:|---:|---:|---:|---:|---:|
| 1 | 64 | 512 | inline | 9.77 | 9.79 | 12.04 | 12.04 | 10.35 | 1.163x |
| 1 | 8 | 512 | inline | 9.38 | 8.97 | 11.42 | 11.62 | 8.76 | 1.304x |
| 1 | 16 | 512 | inline | 9.97 | 9.77 | 11.83 | 11.84 | 9.99 | 1.184x |
| 1 | 32 | 512 | inline | 9.79 | 9.79 | 11.84 | 12.45 | 10.20 | 1.161x |
| 4 | 64 | 512 | inline | 10.38 | 9.99 | 12.45 | 12.45 | 10.60 | 1.174x
|
| 4 | 8 | 512 | inline | 9.38 | 8.97 | 11.43 | 11.63 | 8.97 | 1.274x |
| 4 | 16 | 512 | inline | 10.20 | 9.79 | 11.84 | 12.04 | 10.20 | 1.160x
|
| 4 | 32 | 512 | inline | 9.80 | 9.79 | 12.04 | 12.65 | 10.40 | 1.157x |
| 16 | 64 | 512 | inline | 24.10 | 16.52 | 25.98 | 19.00 | 17.77 |
1.462x |
| 16 | 8 | 512 | inline | 9.17 | 8.97 | 11.22 | 11.64 | 9.17 | 1.223x |
| 16 | 16 | 512 | inline | 9.99 | 9.77 | 12.04 | 12.04 | 10.20 | 1.180x
|
| 16 | 32 | 512 | inline | 13.25 | 12.23 | 15.62 | 14.50 | 12.45 |
1.254x |
| 32 | 64 | 512 | inline | 34.78 | 23.31 | 38.26 | 27.20 | 23.92 |
1.599x |
| 32 | 8 | 512 | inline | 12.45 | 9.79 | 14.70 | 11.84 | 9.99 | 1.471x |
| 32 | 16 | 512 | inline | 13.48 | 12.25 | 15.73 | 14.70 | 12.60 |
1.248x |
| 32 | 32 | 512 | inline | 23.31 | 16.14 | 26.17 | 19.00 | 17.57 |
1.489x |
| 64 | 64 | 512 | inline | 61.83 | 31.71 | 67.76 | 37.46 | 33.55 |
2.020x |
| 64 | 8 | 512 | inline | 21.26 | 13.07 | 23.81 | 15.73 | 13.48 | 1.767x
|
| 64 | 16 | 512 | inline | 23.31 | 16.34 | 26.38 | 19.41 | 17.59 |
1.500x |
| 64 | 32 | 512 | inline | 34.39 | 23.29 | 38.34 | 27.09 | 24.12 |
1.589x |
| 1 | 64 | 512 | footer | 10.20 | 9.38 | 12.24 | 11.43 | 9.79 | 1.250x |
| 1 | 8 | 512 | footer | 9.75 | 8.56 | 11.82 | 10.40 | 8.15 | 1.450x |
| 1 | 16 | 512 | footer | 10.20 | 9.38 | 12.23 | 11.43 | 9.58 | 1.277x |
| 1 | 32 | 512 | footer | 10.20 | 9.38 | 12.25 | 11.61 | 9.62 | 1.274x |
| 4 | 64 | 512 | footer | 10.38 | 9.56 | 12.65 | 11.84 | 9.99 | 1.265x |
| 4 | 8 | 512 | footer | 10.20 | 8.97 | 12.04 | 10.81 | 8.56 | 1.407x |
| 4 | 16 | 512 | footer | 10.60 | 9.79 | 12.66 | 12.03 | 10.20 | 1.241x
|
| 4 | 32 | 512 | footer | 10.20 | 9.58 | 12.45 | 11.63 | 9.79 | 1.272x |
| 16 | 64 | 512 | footer | 25.56 | 20.03 | 28.21 | 22.69 | 21.26 |
1.327x |
| 16 | 8 | 512 | footer | 9.81 | 8.56 | 12.04 | 10.81 | 8.56 | 1.406x |
| 16 | 16 | 512 | footer | 10.41 | 9.56 | 12.65 | 11.64 | 9.99 | 1.265x
|
| 16 | 32 | 512 | footer | 14.29 | 13.07 | 16.75 | 15.32 | 13.27 |
1.262x |
| 32 | 64 | 512 | footer | 37.19 | 33.06 | 40.92 | 36.84 | 33.56 |
1.219x |
| 32 | 8 | 512 | footer | 13.68 | 9.79 | 15.93 | 12.04 | 9.99 | 1.594x |
| 32 | 16 | 512 | footer | 14.29 | 13.05 | 16.75 | 15.52 | 13.27 |
1.262x |
| 32 | 32 | 512 | footer | 25.54 | 20.03 | 28.42 | 22.80 | 21.26 |
1.337x |
| 64 | 64 | 512 | footer | 64.68 | 37.00 | 70.62 | 42.97 | 38.46 |
1.836x |
| 64 | 8 | 512 | footer | 23.92 | 15.73 | 26.57 | 18.19 | 15.72 | 1.691x
|
| 64 | 16 | 512 | footer | 25.52 | 20.01 | 28.63 | 23.11 | 21.26 |
1.347x |
| 64 | 32 | 512 | footer | 37.21 | 33.04 | 41.14 | 36.91 | 33.55 |
1.226x |
| 7 | 64 | 128+512 | inline | 17.98 | 14.50 | 20.24 | 16.96 | 14.70 |
1.376x |
| 49 | 64 | 128+512 | inline | 83.32 | 37.74 | 88.23 | 42.66 | 39.49 |
2.234x |
| 98 | 64 | 128+512 | inline | 150.38 | 78.19 | 158.45 | 87.90 | 80.60 |
1.966x |
| 119 | 64 | 128+512 | inline | 150.39 | 78.91 | 160.22 | 89.66 | 81.18
| 1.974x |
| 140 | 64 | 128+512 | inline | 150.59 | 78.50 | 162.68 | 90.67 | 80.88
| 2.011x |
| 280 | 64 | 128+512 | inline | 299.28 | 128.60 | 321.96 | 150.38 |
129.28 | 2.490x |

</details>

Raw timings, plans, input hashes, numerical checks, source hashes, and
the exact external comparison driver are preserved in the measurement
workspace at `results/low_h_release/` (`results.jsonl`,
`provenance.json`, `run.py`, `report.md`), with shared worker
`results/pr9274_matched/worker.py`. Baseline `flashinfer/`, `csrc/`, and
`include/` remain unchanged.

### Profiler-guided correction

The earlier regression was in the unfused attention core: the one-warp
schedule carried all 512 PV features per warp and used 255
registers/thread for H8, while cluster finalization also burdened
unfused calls. The cooperative rewrite reduces per-warp work, restores
independent-CTA unfused execution, and shares reduction arithmetic with
mega. For T16/H8/K512 inline, final NCU reports 113 registers/thread,
160 threads/CTA, 43,648 shared bytes/CTA, and 128 independent CTAs; the
previous CuTe kernel used 255 registers/thread and 64 threads/CTA.
Achieved active warps/SM rose from 1.80 to 4.89. The separate merge uses
40 registers/thread and 64 threads/CTA.

The final report captures both kernels, with source/SASS embedded and
verified: `results/low_h_diagnosis/cute-final.ncu-repz` (1,030,861
bytes; SHA256
`40e588f7bbc1c7a478101d1f9ead1b5c9e9326ef3e33c9281a0bf26d8b0322a6`).
Basic + scheduler/warp-state sections, 16 replay passes/kernel,
`--clock-control none --pipeline-boost-state dynamic --cache-control
none`; measured SM frequency 2.31/2.28 GHz for decode/merge. Replayed
profiler durations are not used as benchmark latencies. Race-isolation
binaries, source/SASS, and before/after evidence are preserved under
`results/low_h_race/`.

## 🔍 Related Issues

Stack: `main` (merged #8747, FP8 prefill) → this PR → #9356 (NVFP4
prefill) → #9439 (NVFP4 decode).

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

At `310a1ed89` on RTX PRO 6000 Blackwell Server:

- **1,430 tests passed** across all 13
`tests/attention/test_sparse_mla_sm120*.py` files with `--full`.
- **12 final memcheck cases passed, zero errors**, covering multi-tile
execution, inline page gaps, and more-than-warp split reduction.
- **Five racecheck cases passed with zero hazards/errors/warnings**: the
original failing mutable-graph case plus H8/H16 × inline/footer
multi-tile cases with live lengths 1024/513/0. The score-buffer reuse
barrier is verified in SASS. Kernel checks target
`dsv4_fp8_splitkv_decode` decode/merge, excluding unrelated PyTorch
reference kernels.
- **Four synccheck multi-tile graph cases passed, zero errors**,
covering H8/H16 and inline/footer.

- Independent numerical tolerances are unchanged. Exact fused/separate,
poisoned-output, mutable CUDA Graph replay, page-pitch, caller-scratch,
empty-row, and kernel-identity coverage is retained.
- Changed-file pre-commit hooks pass. The downstream NVFP4 commits are
restacked without changes to their patches.
- Actual GB10 validation at the same head: **1,430 passed, zero
failed/skipped**, all 13 sparse-MLA files through
`scripts/task_run_unit_tests.sh` (complete deterministic CI run, no
sampling), 7m05s. Internal CUDA 13.0 image `20261106-54b9f685`, Python
3.10.22, PyTorch 2.14.1+cu130, Triton 3.8.0; GB10 48 SMs, driver
580.142. Fresh JIT/Triton caches. The RTX PRO 6000 lane also completed
**1,430 passed, zero failed/skipped** using the same internal CI image
and runner, 7m31s; the earlier RTX sanitizer checks above remain
separate results. The first RTX setup attempt hit an artifact-index
network timeout; the unchanged retry passed. Both runs cover all 13
affected sparse-MLA files, not the repository-wide suite.
- [x] Tests have been added or updated as needed.
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI targets: the 13 `tests/attention/test_sparse_mla_sm120*.py`
files.

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

FP8 decode scope. The attention core is within 0.3% of baseline at worst
in the paired measurements, and mega beats the original complete
pipeline throughout the matrix. The separate-transform chain's three
small slowdowns are reported explicitly rather than hidden by the fused
comparison.

### [1a9f361](https://github.com/flashinfer-ai/flashinfer/commit/1a9f361db34977801e4a676eb54b0379527479b9)

- **作者**: Yuxian Qiu
- **时间**: 2026-11-18T01:10:04Z
- **提交信息**: feat(prims-ts): add merge-compatible softmax statistics and MLA KV bounds (#5489)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add merge-compatible softmax statistics to PrimTS contiguous/paged
prefill, standard paged decode and dense MLA decode, plus per-query MLA
KV-prefix bounds. These support partition merging and Helix/linear-MTP
integration in [TensorRT-LLM
#19395](https://github.com/NVIDIA/TensorRT-LLM/pull/19395). Aligned
runtime-strided V and separately reviewable scheduling optimizations are
included.

Current head: `772e460928025d9f2c3a8717d5c3f5889aaabe57`, rebased onto
FlashInfer main `1bdba872568a87391f64ffb91910e52aeff9479d`.

- `plan(store_softmax_stats=True)` selects the specialization;
`run(softmax_stats=...)` binds caller-owned FP32 storage shaped
`[*out.shape[:-1], 2]`.
- Export natural-log token maximum `m` and `s = sum(exp(logit - m))`,
independently of LSE/output scaling. Decode sinks contribute once to the
denominator without changing the token maximum.
- Preserve original natural FP32 scales and exact maxima through direct,
fused, cluster and standalone reductions, including MLA 1CTA/2CTA. Exact
context statistics coexist with zero-threshold no-op correction
skipping.
- Treat per-query MLA KV bounds as runtime operands. Supported empty
local partitions write zero output and neutral statistics; bounds/scales
can change under valid graph replay.
- Accept aligned non-overlapping V row/batch strides for contiguous
prefill, with compact head/channel axes.
- Keep statistics opt-in and preserve statistics-disabled behavior
except for the explicitly separated scheduling optimizations.

### Scope and limits

Statistics cover ordinary contiguous/paged prefill, standard decode
(including sinks), and dense MLA decode, alongside independent LSE.
Context statistics reject VC, Sage, MXFP8 Q/K and context sinks;
standard-decode statistics reject Sage. Dense MLA statistics require
`softmax_rescale_threshold_log2=0`. Sparse/NVFP4 MLA APIs do not expose
these statistics/bounds options.

Dense contiguous context permits empty request-local K/V segments when
physical storage contains at least one token overall. Paged/causal
context requires positive KV lengths. Unbounded inactive decode requests
preserve caller storage; bounded MLA initializes neutral rows.

For CUDA graphs, preallocate outputs/statistics/metadata, warm the
required plans, and capture with `validate=False`. This does not claim
that host-checking `validate=True` is capture-safe. Scalar/tensor scale
kinds are fixed by planning; scale values and addresses are not
compile-cache keys.

### Review order

Twenty rebased feature commits followed by test-only consolidation
commits form the review series. Review the final test diff against main:
the latest cleanup deliberately narrows coverage to Kimi K3. The
shape-specific single-split commit is not in this feature history.

1. `aeae6cc3e`, `a409211bc`, `d34d585ff`: context statistics, public
naming, then paged/decode/MLA statistics.
2. `5b0b851c9`: per-query MLA KV bounds.
3. `2714b23a5`, `bcfb960d8`, `cc0ee1e73`: packed-query coverage,
full-tile LDRED, and initial request-local dense domains.
4. `317881d78`, `2f779ffc5`, `a6f1a338c`: original-scale correctness and
numerical fixtures.
5. `19996545d`: runtime-strided V.
6. `99e674d08`, `da7f5b931`, `338d06f90`, `6c414df33`: refreshed APIs,
consolidated coverage, MXFP8 scope and reducer scale fix.
7. `70ecb5ea4`, `f7585f01a`: trusted workspace sizing and header
cleanup.
8. `66a774651`: exact context statistics with no-op correction skipping.
9. `e7b832a50`: ordinary FP16/BF16/FP8 packed-dense domain
generalization.
10. `a99a6dcde`: type-only narrowing of the trace output tensor.

11. `f7f0d73bb`: initial host-test consolidation.
12. `0796c77ace2d4704da526af1e0e0bd568dbbd33c`: aggressively reduce new
tests to Kimi K3 prefill, FP8 MLA/MTP, Helix bounds and merge
statistics.
13. `d5e23c5a7`: account for statistics scratch and clarify
helper/buffer contracts.
14. `2a936b7ae`: canonical trace templates and the CPU trace-apply CI
fix.
15. `feab3c958`: restore the focused BF16 boundary regression with its
probability-rounding reference.
16. `010508a0b`: share causal/dense right-bound masking without changing
their boundaries.
17. `772e46092`: optional bounded-MLA empty-row initialization and
LSE-contract clarification.

The rebase preserves all 20 feature commits; the latest test-only
cleanup leaves production code unchanged. Conflicts in the 1CTA MLA
kernel retain main's KV-producer/output-descriptor operands and this
PR's statistics/bounds. The existing scale-replay test uses main's
relocated PDL helper import.

The shape-specific SM107 single-split override is not in this PR. It
remains on [the held performance
branch](https://github.com/yuxianq/flashinfer/tree/prims-ts-mla-prefill--flashinfer-perf)
at `9dacdaa1b`, based on pre-rebase `f118184d6`; it is not a
current-main A/B baseline.

### Downstream relationship

TRT-LLM now pins temporary source
`946b484d2cd7918dafbbd28493b087c690e067f1`, based on canonical
`trtllm-prims-ts-dev-20261107` at
`911d6a9d62308b6c8a5249e8dc4aabc7518020f1`. The upstream review and
downstream branches intentionally have different heads. The new shared
production patches match across both branches, and local vendor
materialization checks pass. The earlier 14 exact normalized-edit
matches refer to the previous pin. The canonical branch is unchanged;
the TRT-LLM pin advances through #19395.

## 🔍 Related Issues

- [NVIDIA/TensorRT-LLM
#19395](https://github.com/NVIDIA/TensorRT-LLM/pull/19395): downstream
MLA prefill, FP8 KV, MTP/Helix and Rubin integration.
- NVIDIA/TensorRT-LLM#21354: canonical source refresh.
- Prerequisites #4839, #5059 and broader query pruning #6774 are already
in the base.

## 🚀 Pull Request Checklist

- Signed commits; formatting, lint, mypy and syntax checks passed on the
changed files.
- AI assistance was used for the implementation and test consolidation;
the retained numerical regressions were executed and checked against
their references.
- No registration in `flashinfer/aot.py`; existing experimental wrapper
usage remains explicit opt-in.
- Functionality, scheduling optimizations, correctness fixes and API
adaptations remain separately reviewable.
- Full upstream GPU CI and unresolved experimental-track checklist items
are not claimed complete.

## 🧪 Tests

<!-- zero-empty-optout-20261116:5489 -->
### Helix caller opt-out and CI diagnosis — 2026-11-16

- TRT-LLM `25b5c49f81b0e060e94544f91cc8a8728638eba4` plans dense MLA
with `zero_empty_rows=False` at runtime and during warmup. Helix already
neutralizes empty O/statistics through NCCL reformatting, FIFO-v1
sanitization or the FIFO-v2 sender before combination. Per-token MTP
bounds and Q1 local-length masking remain intact. This removes one
redundant launch from bounded MLA; no measured speedup is claimed.
Non-Helix decode and context are unaffected.
- The standalone FlashInfer default stays `True`; source heads and TRT's
dev pin `946b484d2cd7918dafbbd28493b087c690e067f1` are unchanged. No
FlashInfer source update was required by the CI diagnosis.
- Reused coverage: **37 focused CPU checks passed**
(adapter/planning/cache/warmup plus existing Helix mask/sanitization
checks). Selected current modules match the isolated dependency prefix;
its native dependencies remain the older CI70292 wheel, not full
new-main native qualification. The existing two-GPU strict MTP7
regression now poisons empty raw O/statistics and compares raw graph
parity only on nonempty rows; its final full-output/reference tolerance
is unchanged. That updated multi-GPU test has not been rerun locally.
Prior B200 opt-out kernel results remain historical.
- Changed-file hooks pass. The all-file sweep retains the existing main
F811 duplicate import in `test_mamba_cache_manager.py`; advisory Pyrefly
is unavailable. No new GPU allocation, e2e or performance experiment was
run. TRT-LLM CI is requested separately with `/bot run
--disable-fail-fast`; no CI pass is claimed here.

FlashInfer CPU CI [job
551865695](https://gitlab-master.nvidia.com/dl/flashinfer/flashinfer-ci/-/jobs/551865695)
in pipeline82543944 completed all tests: **10,971 passed, 20 skipped, 0
failed**, with `suite_complete=true`. The general archive upload
succeeded; the GitLab runner helper was then **Killed while uploading
the gzip JUnit report**, and the job became failed. This explains why
the bot could not extract a test failure.

This is a report-upload failure, not a PrimTS test failure. The trace
does not establish the reason for the kill; a memory-limit diagnosis
needs runner evidence. Per maintainer direction, the FlashInfer retry is
left to CI ownership. No source patch, waiver or CI retry was made for
this event.




<!-- prims-perkz-fixes-20261116:5489 -->
### Perkz review follow-up — 2026-11-16

- Shared causal/dense score-mask and maximum-reduction loop, preserving
distinct visibility bounds, tile coordinates and the full-tile fast
path.
- Added `zero_empty_rows=True` to dense MLA planning and the one-shot
API. Disabling it omits the neutral initialization launch, not prefix
masking; empty-row contents are unspecified. The effective flag selects
a compiled launch variant but does not change workspace sizing. TRT-LLM
runtime and startup planning now disable the extra initialization launch
and rely on the existing Helix zero-row sanitization before combination.
- Clarified that the existing base-2 LSE API remains independent of the
natural-log maximum/sum export; both can coexist. Reused existing tests,
adding opt-out controls to the 1CTA Q1 and 2CTA Q8 graph cases without
adding test definitions or a broad matrix.
- Upstream `772e460928025d9f2c3a8717d5c3f5889aaabe57` and pinned dev
`946b484d2cd7918dafbbd28493b087c690e067f1` carry the same two follow-up
patches. TRT-LLM head `053e80782bc230eef4d9df24cdf665a7344fb66e` imports
them. Its compatibility patch was regenerated only to re-anchor context;
every added/removed patch line remains identical. Canonical dev is
unchanged.
- Actual B200 / CUDA 13.4 / CuTe DSL 4.8 validation: **11 passed, 0
failed/skipped**, including bounds, empty rows, graph opt-out,
dense-domain replay, chunk merging and simultaneous stats/LSE. Source
hashes checked before/after; the allocation was released.
- Host-only checks with CUDA hidden: upstream **1,271 passed / 2
skipped**, pinned dev **1,248 passed / 2 skipped**. All changed-file
FlashInfer hooks passed. TRT-LLM validated 30 focused CPU checks (16
initial passes plus 14 passes after correcting an existing profile
assertion); changed modules are byte-identical to the tested isolated
prefix, but dependencies/native files remain the older CI70292 runtime,
not full new-main native qualification.
- The broader local trace run was **not CPU-only**: 2,133 passed / 341
skipped / 2 failed. Both failures were in unchanged persistent
`BatchAttention` on local SM86: cooperative-grid launch limit, then
inherited CUDA error. No unrelated fix, skip or tolerance change was
added. TRT-LLM all-file lint also retains the pre-existing main F811
duplicate import in `test_mamba_cache_manager.py`; changed-file checks
pass. Advisory Pyrefly is unavailable.
- No new end-to-end/performance experiment or CI command was issued for
these follow-ups. Historical performance tables retain their original
source/hardware scope.



<!-- prims-review-update-20261116:5489 -->
### Review and CI follow-up — 2026-11-16

- Follow-up head: `feab3c95865e2a23c2b4f8425914eaf6d79360dc`. Review
fixes, canonical trace-template routing, and the BF16 boundary reference
correction are separate commits (`d5e23c5a7`, `2a936b7ae`, `feab3c958`).
The corresponding fixes are backported to the TRT-LLM dev source
`95546a07288ce7beaf3f88f7cffda090eed68313`.
- Statistics-aware shared-memory estimates now use the same fanout
footprint as allocation; helper ownership/units, matching workspace
flags, and the all-empty merge identity are documented. No attention
arithmetic or numerical tolerance was changed.
- The two CPU failures in [CI comment
6907293628](https://github.com/flashinfer-ai/flashinfer/pull/5489#issuecomment-6907293628)
were caused by noncanonical cached templates, which made replacement
routing fall through to CUDA validation. A fresh-process one-module
revert control reproduces 2 failures / 40 passes; fixed source passes
all 42 CPU trace-apply tests. CUDA validation remains intact.
- Relevant upstream trace/CPU suites: 1,308 passed / 2 skipped.
Corresponding dev suites: 1,285 passed / 2 skipped. Focused
planning/trace checks also passed, along with mypy/Ruff/pre-commit.
These are local results, not a new CI pass; no FlashInfer CI command was
issued.
- Added one host shared-memory-budget regression and restored one BF16
Helix-boundary regression, without restoring the removed broad matrices.
The BF16 reference explicitly models probability rounding only for its
guarded single-tile case; independent merged-attention/statistics checks
and all tolerances remain. The earlier B200 run passed 7/7 bounds cases;
the current explicitly scoped oracle also passes that retained
exact-input capture. This last check is not a new GPU run.

These AI-assisted follow-ups supersede older status notes below; earlier
numerical/performance measurements retain their original source and
hardware scope.



### Kimi K3-focused consolidation (2026-11-13)

Per review feedback, narrow the newly added coverage to the K3
integration rather than a generic cross-product of all supported APIs,
dtypes, layouts and schedulers.

- Total PR-added test lines: **7,453 → 1,465** (about **80% fewer**),
including trace fixtures.
- Added attention-test lines: **6,668 → 1,160**. Only two new
attention-test files remain instead of eight.
- Actual affected attention collection: **2,338 → 1,879** cases; the
base has 1,857. The net addition is therefore **481 → 22** cases. The
new trace contract shrinks from eight cases to one.
- Existing pre-PR tests remain; their necessary API-signature/mock
updates are retained. Remove broad new standard-attention,
FP16/FP8-prefill, packed-MLA, scheduler, source-AST and duplicate
validation matrices. One trace example/snapshot remains for the new
statistics/bounds outputs.
- No production code, downstream vendor pin, tolerances or numerical
pass criteria change. This is not a measured CI-time speedup.

Retained coverage:

| K3 contract | Focus |
|---|---|
| BF16 expanded MLA prefill | QK192/V128; H6 TP16 and H96 DP;
fixed/packed strided V; dense-prefix/causal-suffix merge |
| Exact statistics | Small maximum increases, original-scale maxima
shared by BF16 context and FP8 MLA, zero-threshold correction policy |
| Cached packed context | Runtime KV-length changes before graph replay,
tile boundaries, empty chunks, adversarial neighboring sequences |
| FP8 absorbed MLA | Latent512/RoPE64, page128; H6/Q1 and H96/Q6/Q8;
split reduction, output and statistics reference checks |
| Helix | CP8 page ownership at 128/1024-token boundaries, neutral empty
ranks, merged reference, graph-reloaded bounds/pages/lengths |
| Host/API | Trusted MLA workspace-size parity, existing planner/run
contracts, one bounded-MLA trace contract |

### Validation

- Retained GPU cases: **13 passed, zero failures/skips on B300
(SM103)**, Torch 2.14.0a0 and CUTLASS DSL 4.8.0. Exact source/import/GPU
identities were verified. The first run exposed a missing required
`packed_query=False` in the consolidated test setup; after fixing that
fixture, all 13 passed together.

- Selected host/API checks: **21 passed**.
- Changed-file pre-commit, Ruff and diff checks passed.
- No FlashInfer CI command or label was issued. Local B300 checks are
not a Rubin or full-model performance qualification.
- The earlier BF16-KV Helix tolerance failure remains unresolved
historical evidence. BF16-KV decode variants are now outside this
explicitly FP8-KV-focused suite; their removal is not a fix or a passing
result.
- Current-head full-model K3 accuracy and DEP16/Helix8 throughput/TTFT
remain pending; the downstream experiment continues separately with its
frozen source.

## 🔬 Experimental Track

- [x] This extends existing experimental PrimTS APIs; tracking context:
#4829, #5059, #5082.
- [ ] The tracking issue names an owner, reason, and graduation plan
with a target release.
  - [ ] Core changes are limited to a thin entry point.
- [ ] Tests live in `tests/experimental/` and include a runnable
example.
- [x] Nothing is registered in `flashinfer/aot.py`; calling the
experimental wrapper remains explicit opt-in.
  - [x] Shared experimental test scope is declared below.

```experimental-tests
tests/experimental/test_experimental_api.py
```

The existing PrimTS implementation and numerical tests remain in
`flashinfer/attention/prims_ts/` and `tests/attention/`. This
experimental-track scope covers shared opt-in machinery, not kernel
correctness; the targeted attention tests above cover the kernels.
Backend relocation is outside this change.

## Reviewer Notes

Please focus on the maximum/denominator contract, original-scale
rounding, row ownership, compact split-workspace indexing, per-query
bounds, strided V and graph-live buffers/scales. Low-precision
probability rounding is checked against independent references; bitwise
output equivalence with statistics disabled is not promised.

<details>
<summary>Historical validation and performance — older snapshots, not
current-head qualification</summary>

### Earlier review follow-up (`f118184d6`)

- Statistics plans use exact maxima (lazy threshold0) while skipping
no-op output corrections. Positive-threshold statistics are rejected
before task-resource construction; statistics-disabled defaults and
synchronization are preserved.
- Request-local dense domains now cover homogeneous FP16/BF16/FP8 Q/K/V
with16bit output, public query-paired geometries128/128 and192/128,
across supported architectures. Paged/causal/window, uniform-packed,
single-instance/two-CTA and VC/Sage/MXFP8 paths keep their existing
behavior.
- **B200:22 GPU cases passed,0failed,0skipped**:7 domain graph cases,11
exact-statistics regressions and4 unchanged-path controls. Hashes
remained frozen. Supported-architecture scope is not a claim that every
architecture was executed; Rubin remains pending.
- Focused host groups13+15 passed. Trace typing correction passes24
existing CPU cases. Full repository pre-commit now passes, including the
previously failing mypy check; the fix is a type-only `cast(Tensor,...)`
after confirming every helper caller supplies a tensor.
- Test consolidation: factory cases8→4; domain suite15→22 with seven
explicit GPU specializations, no dtype×geometry×scheduler Cartesian
expansion. Existing strict references and original FP8 replay boundaries
remain.
- Downstream current-source validation passed7 native B200 anchors with
no skips and316 adapter host cases. New CP2/CP8 tests are
authored/collected but not yet executed.
- Header cleanup removes this PR's extra NVIDIA notices while preserving
pre-existing upstream notices and Apache license text. TRT-specific
notices belong in its compatibility patch.
- No new Rubin K3 throughput/TTFT result is available. Earlier
measurements below remain historical, not this head's qualification. No
FlashInfer CI bot command was issued.


### Trusted workspace sizing — `55dfca9b2`

- Standard and MLA decode workspace-size helpers now accept keyword-only
`validate=True`. Trusted callers may pass `False` to skip repeated
optional argument/device checks and packed-Q metadata readbacks; valid
inputs produce the same policy and scratch size. Alias agreement and
dtype/device resolution remain.
- Cold policy resolution can still query hardware or compile a small
occupancy probe. Warm the policy outside CUDA-graph capture; this is not
a cold-capture guarantee.
- B200 validation: **32 focused host tests passed**, plus **six targeted
numerical/graph cases and four existing replanning anchors passed**.
Cases cover BF16/FP8, fixed/packed Q, split/no-split, statistics, KV
bounds, exact default/trusted/plan byte equality and graph replay.
Captured warm queries forbid metadata readback and optional device
checks.
- Test consolidation adds 12 inexpensive host cases, with the two
affected files collecting 1514→1526. Trusted sizing and capture
assertions reuse existing GPU tests: **no new GPU parameter cases**.
- On the monitored B200 sizing microbenchmark, trusted uncached MLA full
preparation took **5.46–5.63 us** versus **2.40–2.55 us** for the
existing TRT-LLM size cache. Consequently the downstream cache stays.
Standard decode baseline/trusted preparation took **23.50–24.50 /
17.85–18.21 us**. These are case-median ranges over 32 geometries, not
model throughput or kernel-latency claims.
- Ruff, formatting, changed-source mypy and independent incremental
review passed. The trace-output mypy diagnostic present during this
earlier validation was subsequently fixed by the type-only narrowing in
`f118184d6`; current full pre-commit passes.
- At that historical checkpoint, the source and downstream temporary
branches were synchronized. The current upstream review branch has since
been rebased separately; current head/pin relationships are described
above.

### Previous refresh validation

B200, CUDA13.4, CUTLASS DSL4.8.0:

- Full selected changed-test run at `b570fdf7b`: **525 passed, 8
skipped, 2 failed**.
- One failure was a device-scale reducer compilation regression:
assigning a float back to a pointer variable inside a dynamic CuTe
branch. `26b197614` keeps a branch-local natural scale. All **22
targeted rerun cases passed**, including the failing graph/prepared
case, compact split reductions, and strict sink-scale cases. These
overlap the full run and are not additive unique counts.
- The remaining BF16 Helix page-boundary tolerance failure reproduces
identically on both pre-refresh sources: upstream-port `a4b6e9028` and
old pinned-dev `64273c074`. It affects 2/884736 output elements, with
greatest absolute difference 0.0006412482 (absolute tolerance 0.0005).
The test, input domain, reference and tolerances are retained unchanged;
this is a known pre-existing failure, not a newly passing qualification.
- The eight skips require SM107/212-SM or the normal LDTM.STAT-enabled
policy; B200 does not qualify those policy-specific tests.
- Test consolidation: the same 13 affected files collect **2391→2373**
cases. Context statistics shrink 48→24 while retaining every
input-dtype/layout/mask/geometry combination and representative output
conversions; targeted scale/graph coverage is added. No proportional
runtime-speedup claim.
- No new full-model or performance experiment. No manual FlashInfer CI
command was issued.

### Historical Rubin qualification and measurements (pre-refresh
sources)

Focused, overlapping CPU selections passed: standard decode/precision
**298**, MLA bounds plus SM107 policy **111**, context contracts **41**,
shared statistics **42**, trace consistency **97**, query-pruning
contracts **11**, LDRED contracts **2**, and runtime-KV-domain contracts
**13**. These phase-specific counts must not be summed as unique tests;
GPU skips in local runs are not passes.

The original-scale fix additionally passed focused source/CPU review: 66
upstream and 92 dev CPU cases, with GPU cases skipped locally. The FP8
fixture correction passed seven CPU contract checks executing both
fixture bodies with dependency doubles; those are not native GPU
qualification.

On Rubin, exact head `005d91701b95e88a3495da84e6d384efccc606d7` passed
**104 selected GPU tests with zero skips**: context 31, standard decode
38, and MLA 35. Hecate job 927548 used a fresh full-source FlashInfer
0.7.3 package, not a PrimTS overlay on an older installed wheel. This
includes all 12 new original-scale regression cases.

The same allocation independently tested the older canonical-dev API
adaptation at `eef263b`: 13 passed, one failed, and seven were not
executed. Its original-scale sink case `[2-disabled]` exposed an
approximately 11% denominator error whose exact arithmetic signature is
multiplication/subtraction contraction. The dev-only explicit-rounding
correction at `069139a65aad98f3e5c61f049c761e28eff0b14e` then passed
**all 21 selected GPU cases with zero skips** in Hecate job 927692,
without weakening tolerances. The upstream cases above passed unchanged.
The first allocation exited with failure and did not time; the follow-up
keeps that failure record separate from its successful dev rerun.
Downstream TRT-LLM head `a7da965b611830fbc1347e84646b687adc177f67`,
pinning this dev correction, also passed **26 matching-runtime B200
regression checks with zero skips**: four native sparse-MLA GPU cases
and 22 host/contract cases. This is focused regression coverage, not a
full-model rerun. Upstream CI triggering is handled by the maintainer,
not this qualification run.

After both correctness gates passed, job 927692 completed 36
fresh-process prepared-wrapper receipts: three ABBA blocks for each of
three synthetic cases. Baseline
`e2203f939e6c95475d7ec609fadfb916c04a2bec` and candidate
`005d91701b95e88a3495da84e6d384efccc606d7` contain the same
original-scale correctness fix; their production delta is only LDRED
plus request-local KV domains.

| Synthetic case | Baseline graph latency | Optimized graph latency |
Mean paired change | Sample SD |
|---|---:|---:|---:|---:|
| One request, statistics ON | 100.212 us | 91.859 us | -8.335% | 0.089
pp |
| Two ragged/empty requests, statistics ON | 376.195 us | 102.620 us |
-72.721% | 0.018 pp |
| One request, statistics OFF | 73.045 us | 72.087 us | -1.312% | 0.040
pp |

These packed dense FP8 E4M3 cases use H96, Dqk192/Dv128, and BF16
output. B1 uses Q/K lengths 1920/1920 and capacities 2048/2048. B2 uses
Q lengths `[1664,256]`, K lengths `[0,3840]`, and capacities
Q2048/K4096. Both arms pass actual runtime maxima. All eager, graph, and
post-timing numerical checks passed; all input identities were
unchanged. Independent audit recomputed 360 raw CUDA-event samples and
all nine block summaries. Percentages average paired block ratios; SD is
across three blocks in one allocation, not independent allocation
replications. This measures prepared-wrapper graph replay only, not
native-attention or K3 end-to-end performance. The empty-partition
result does not establish its frequency in serving, and statistics
ON/OFF changes precision policy as well as output storage.

### FP8 empty-context fixture diagnosis

Before changing the output tolerance, nine exact-input controls compared
the pre-performance-port source `f5ec2e580`, the combined source
`b787f5692`, and older dev `76e822974`, with and without the empty
neighbor and with statistics on/off. All six statistics-enabled active
outputs were identical across sources/layouts and exactly matched the
BF16-rounded explanatory model that rounds P to E4M3 for PV while
retaining the FP32 denominator. The original strict FP32-oracle check
missed 2 of 49,920 elements; relative L2 was 2.302%, within the
pre-existing expanded-FP8 contract. Empty outputs/statistics and tight
active m/s checks passed. This supports the single finite-input fixture
correction, not a general hardware-emulator claim or qualification of
the subsequent original-scale fix. BF16 thresholds and exact empty
checks remain unchanged; the revised FP8 test also requires relative L2
below 5%, active m/s agreement, and a TF32-disabled independent
reference.


### Historical downstream evidence and limits

The earlier Rubin K3 FP8+MTP DEP16 experiment reached near throughput
parity with CuTeDSL plus trtllm-gen: mean paired-block changes +2.18% at
concurrency 128 and +0.56% at concurrency 256, with sample SDs 2.57 and
2.03 percentage points. Those pre-refresh measurements do not qualify
this head or establish a robust speedup or output equivalence. Native
GSM8K was 96.5125% versus PrimTS 95.8302% in that configuration; both
cleared the reused 93.2975% gate, but the nine-answer difference
remains. Exact sources, workloads and limitations are recorded in
NVIDIA/TensorRT-LLM#19395.

Historical CP8 timings are prepared-attention/FIFO2 component
measurements, not full-model Helix results. That historical experiment
excluded strict 8-GPU aggregated Helix. Current TRT-LLM has a
development-only experimental path, but current-head full-model Helix
qualification is still pending. No KDA behavior or Small-BH NaN fix is
included.

</details>

---------

Signed-off-by: Yuxian Qiu <142763828+yuxianq@users.noreply.github.com>

### [f7cdba7](https://github.com/flashinfer-ai/flashinfer/commit/f7cdba7e5814311bc814996e592e4a24a97310fb)

- **作者**: ranx2026
- **时间**: 2026-11-18T01:09:07Z
- **提交信息**: fix(jit): find nvcc.exe for the cake_gdn cubin compile on Windows (#9481)

## 📌 Description

On native Windows arm64, every `cake_gdn` cubin compile fails before the
compiler runs: `RuntimeError: nvcc was not found at <CUDA
home>\bin\nvcc`.

- `_nvcc_identity()` in `flashinfer/jit/cake_gdn.py` builds `<CUDA
home>/bin/nvcc` and requires that file to exist.
- On Windows the binary is `nvcc.exe`.

This change uses `nvcc.exe` as the binary name on Windows. Other
platforms keep `nvcc`.

Finding the compiler makes a second failure visible on native Windows:
the two cases that compile the generated device source now fail inside
that compile. That failure is tracked separately and is not addressed
here.

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
- [ ] All tests are passing (`unittest`, etc.).
- [ ] This PR requires **full-scope** CI, not targeted tests (expensive;
justify below).
Reason: <!-- e.g. cross-cutting change to shared infrastructure -->

Suggested CI test targets (optional; paths under `tests/`,
whitespace-separated — a starting
point for `@flashinfer-bot run <targets>` / `/bot run <targets>`,
reviewers may adjust): `tests/gdn/test_paged_state.py`

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
- `tests/gdn/test_paged_state.py`: 100 passed, 2 failed, 18 skipped with
this change.
- The "nvcc was not found" error is gone: `nvcc.exe` is found and the
compile starts.
- Without this change the cases that compile the device source fail
earlier, with the nvcc error.
- The 2 remaining failures are the second failure named in the
description.
- Cases:
`test_paged_decode_reads_previous_page_on_a_new_page[heads0-state_dtype1]`
and `test_paged_decode_slots_reused_across_layers`.
- Error: `cake_gdn_device_common.cuh(28): invalid redeclaration of type
name "uint64_t"`, then the LP64 host-ABI assertion of the generated
source.
- On Windows `long` is 32 bits wide, which the generated source does not
expect.
- Linux is unchanged: the name stays `nvcc` unless `os.name == "nt"`.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* CUDA compiler detection now recognizes the appropriate executable name
on Windows and other platforms. This allows the compiler to be located
using the platform-specific naming convention when building, while
checks for a missing compiler or an unsuccessful version check continue
to work as before.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [5b6f9f6](https://github.com/flashinfer-ai/flashinfer/commit/5b6f9f692b65c866090688f15d7343840b302948)

- **作者**: ranx2026
- **时间**: 2026-11-18T01:08:47Z
- **提交信息**: test: accept the Windows device-assert text in test_replayssm_tree_verify (#9480)

## 📌 Description

On native Windows arm64,
`test_validation_flag_accepts_trees_and_rejects_a_forward_parent` in
`tests/gdn/test_replayssm_tree_verify.py` fails although the child
process dies on the expected device-side assert.

- The child prints the failed assertion (`input[0] != 0`) and then
`RuntimeError: CUDA Error Code: 710`.
- The test accepts the child's output only when it holds `device-side
assert`, `CUDA error` or `_assert_async_cuda_kernel`.
- The Windows text matches none of the three markers.

This change adds `CUDA Error Code` to the accepted markers.

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
reviewers may adjust): `tests/gdn/test_replayssm_tree_verify.py`

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
- `tests/gdn/test_replayssm_tree_verify.py`: 12 passed with this change.
  - Without this change: 1 failed, 11 passed.
- Linux is unchanged: the existing markers keep matching the Linux text,
and the tuple only gains one accepted marker.
- The tuple spans several lines now because the formatter wraps it.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Tests**
* Updated validation checks to recognize `CUDA Error Code: 710` as an
accepted CUDA failure marker. This expands the CUDA error messages
covered by the existing device-side validation test. The change is
limited to test coverage; it does not add or alter user-facing
functionality.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [046ec14](https://github.com/flashinfer-ai/flashinfer/commit/046ec1452567885fb8d0ac6c494eb9ec01424cea)

- **作者**: yuy-blip
- **时间**: 2026-11-18T00:02:07Z
- **提交信息**: fix(gemm, grouped_mm): keep BF16 x FP4 and MoE cuDNN graphs used by captured CUDA graphs alive across cache eviction (#8188)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #6239, for this part of @kahyunnam's
[review](https://github.com/flashinfer-ai/flashinfer/pull/6239#pullrequestreview-5660768008):

> One follow-up for a separate PR, since it has no line in this diff:
`execute_cudnn_bf16_fp4_graph` /
`execute_cudnn_bf16_fp4_graph_override_shape` in
`flashinfer/gemm/gemm_bf16_fp4_cudnn.py` and the three
`_run_cudnn_moe_*` functions in `flashinfer/grouped_mm/cudnn/core.py`
execute graphs from bounded `lru_cache` builders keyed on the token
count without calling `_retain_cudnn_graph_if_capturing`, so they look
exposed to the same eviction once a captured shape falls out of the
cache.

This PR calls `_retain_cudnn_graph_if_capturing(graph)` in those five
functions, before each graph is executed, and adds a regression test for
the MoE path.

When it matters: with the cudnn-frontend that main requires (>= 1.32),
the frontend keeps these graphs alive by default, so a default install
does not fail. cudnn-frontend 1.32 also lets this be turned off with
`CUDNN_CUDA_GRAPH_RETENTION=none`, and its header then says that "the
application keeps the graph's execution plans and host-copy data alive".
Only FlashInfer can do that for its own caches; the eight paths from
#6239 do, these five did not. With `none`, a captured MoE grouped GEMM
fails on replay (`cudaErrorIllegalInstruction`) once its graph is
evicted: the captured graph copies a host buffer held by the cuDNN plan,
and the buffer is freed with the graph. The same happens with
cudnn-frontend older than 1.31, which is below main's requirement.

For BF16 x FP4, `none` (or frontend 1.30) alone did not make it fail on
cuDNN 9.23.2. It failed only with cuDNN's default kernel cache also
turned off (`CUDNN_ENABLE_DEFAULT_KERNEL_CACHE=0`, not documented): the
captured `mm_bf16_fp4` graph then crashed without this change (3/3) and
replayed bit-exact with it (3/3). The kernel apparently stays loaded
while it is in that size-limited cache; evicting from it was not tested.
cuDNN 9.27.0 did not fail either way. `mm_bf16_fp4` takes the
override-shape executor on every supported cuDNN, so the other
executor's call is reached only through the tactic fallback.

Not included: the torch >= 2.14 graph-scoped path and skipping retention
when cudnn-frontend retains the graph, from the [retention
thread](https://github.com/flashinfer-ai/flashinfer/pull/6239#discussion_r4383863886).
I'd keep those two together in a separate PR.

## 🔍 Related Issues

Follow-up to #6239. Related: #6237.

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
reviewers may adjust):
`tests/grouped_mm/test_cudnn_moe_cuda_graph_lifetime.py
tests/gemm/test_cudnn_gemm_cuda_graph_lifetime.py
tests/grouped_mm/test_grouped_mm_bf16.py
tests/grouped_mm/test_grouped_mm_mxfp8.py
tests/grouped_mm/test_grouped_mm_fp4.py tests/gemm/test_mm_bf16_fp4.py`

New `tests/grouped_mm/test_cudnn_moe_cuda_graph_lifetime.py`, written
like the FP8 test from #6239: in a subprocess with
`CUDNN_CUDA_GRAPH_RETENTION=none`, it captures one CUDA graph per cuDNN
plan through `grouped_mm_bf16(..., tactic=t)`, clears
`_build_cudnn_moe_grouped_gemm_graph`, replays and compares bit-for-bit.
It skips with the markers in `tests/grouped_mm/conftest.py`.

Results on RTX PRO 6000 Blackwell Server Edition (SM120), torch
2.13.0+cu130, FlashInfer main (fec6b56) with only the new test vs. the
test plus this change. The container ships cuDNN 9.20.0 / cudnn-frontend
1.30.0; the other versions were installed over it with `pip install
--no-deps`.

| cuDNN / cudnn-frontend | test only | test + this change |
|---|---|---|
| 9.23.2 / 1.32.0 | FAILED (2/2) | PASSED (2/2) |
| 9.27.0 / 1.32.0 | FAILED | PASSED |
| 9.27.0 / 1.31.0 | PASSED (1.31 has no `none` mode and retains) |
PASSED |
| 9.23.2 / 1.30.0 | FAILED | PASSED |
| 9.20.0 / 1.30.0 | not run | SKIPPED (needs cuDNN >= 9.21) |

Every failure was `cudaErrorIllegalInstruction` on replay. The FP8 test
from #6239 passed in every run. Each run of the two files took 22–27 s.

Not tested: other GPUs (SM90/SM100) and the full suite (I'd rely on CI).
The block-scale MoE runners (mxfp8 / fp4) were checked with a standalone
script and fail and pass the same way as bf16 (see the review thread),
but the test does not cover them yet. No BF16 x FP4 test is added, since
making it fail needs that undocumented switch.

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

- Same helper as #6239, called before each graph is executed; no new
logic.
- I used an AI assistant (Claude) for parts of the investigation and
drafting; I reviewed every line, and all numbers above are from my own
runs on the GPU server described above.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of cuDNN-based BF16 and FP4 matrix operations
during CUDA graph capture and replay.
* Captured grouped matrix operations now continue to replay correctly
after cached execution plans are cleared, helping prevent failures in
graph-based workloads.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4828
- **最后更新**: 2026-11-18T23:51:16Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34942
- **最后更新**: 2026-11-19T01:42:05Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: Sayak Paul, YiYi Xu

## AI分析总结

## 分析总结：huggingface/diffusers 近期提交

### 1. 主要更新类型
本次提交属于**维护与基础设施优化**类型，包括**文档更新**（PR 模板和 agent 文档）以及 **CI 基础设施升级**，没有涉及核心功能新增或 Bug 修复。

### 2. 关键变更点及其与项目整体方向的关系

- **PR 模板更新**：调整了 PR 中应 @ 的维护者/审核者标签。这反映了项目协作流程的持续优化——随着贡献者数量增长，明确的代码审查路由有助于加速合并流程、减少沟通摩擦。对 diffusers 这样活跃的开源项目来说，高效的 PR 处理流程直接影响到功能迭代速度。

- **Agent 文档添加缓存上下文参考**：为 AI 代理（agent）工作流补充了缓存上下文相关的参考文档。这表明项目正在积极适配 AI 辅助开发的工作方式，体现了团队对 AI 工具链在开发流程中应用的前瞻性布局。缓存上下文的规范化有助于提高 AI 代理处理复杂任务时的一致性和效率。

- **CI 中 numpy 版本升级**：这是一项关键的基础设施维护。numpy 是深度学习生态的基础依赖，版本升级可以带来性能改进、API 更新以及兼容性保障。CI 环境的及时更新能确保代码在最新依赖环境下正常运行，提前暴露潜在的兼容性问题，避免在发布版本时才暴露风险。

### 3. 对项目的影响和潜在影响

- **短期**：CI 升级可能触发短暂的构建问题，但一旦稳定，将提高整个开发流水线的可靠性。文档和模板更新立即改善贡献者体验。
- **长期**：持续的依赖管理（如 numpy 升级）降低了技术债务累积的风险；AI 代理文档的完善为未来更大规模的自动化开发奠定基础；PR 模板优化则持续改善项目的社区治理效率。

### 4. 值得关注的技术点

- **numpy 版本管理策略**：值得关注升级到了哪个版本，以及是否涉及 API 破坏性变更（如 `np.float` 移除等）。在 diffusers 中 numpy 主要用于后处理和数值运算，版本敏感性较低但不容忽视。
- **Agent 文档中的缓存上下文**：这暗示项目可能在探索将缓存机制系统化地集成到 AI 辅助开发流程中，这在当前 AI 驱动开发趋势下具有前瞻性。

### 5. 对项目发展的整体影响

diffusers 是 HuggingFace 生态中面向扩散模型的核心库，其 README 虽然仅展示许可证信息，但项目本质上致力于让扩散模型的使用更加便捷和标准化。本次的三笔提交虽然看似琐碎，但它们共同体现了**开源项目成熟期的典型特征**：不追求功能爆发，而是通过持续的基础设施维护、协作流程优化和文档完善来保障项目的健康运转。这种"小步快跑"的维护模式确保了 diffusers 能够在快速变化的扩散模型领域中保持稳定性和竞争力，为后续的功能开发提供坚实的基础设施支撑。

## 详细提交记录

### [8edb6d8](https://github.com/huggingface/diffusers/commit/8edb6d8c9466313ff39d7d441474700ac2a442b1)

- **作者**: YiYi Xu
- **时间**: 2026-11-18T19:05:02Z
- **提交信息**: Update PR template (#15324)

Update who to tag in the PR template

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [da26931](https://github.com/huggingface/diffusers/commit/da26931462895b5745a84df6145e6130828b3f80)

- **作者**: Sayak Paul
- **时间**: 2026-11-18T19:04:48Z
- **提交信息**: [agent-doc] add a reference to adding caching context (#15327)

add a reference to adding caching context

### [2bb9468](https://github.com/huggingface/diffusers/commit/2bb9468a8d64c2a1e7da8b52ab3221a53cd507ad)

- **作者**: Sayak Paul
- **时间**: 2026-11-18T07:50:52Z
- **提交信息**: [ci] upgrade numpy version in ci. (#15326)

upgrade numpy version in ci.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
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


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13386
- **最后更新**: 2026-11-19T02:13:23Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Hong Zhang

## AI分析总结

## 仓库 DiffSynth-Studio 昨日提交分析（1/1）

### 1. 主要更新类型
- **Bug修复 + 代码重构**：修复 MiniMax-H3-Image 编辑训练的多个问题，同时对模型函数和数据集逻辑进行了适度重构。

### 2. 关键变更点及与项目方向的关系
- **修复编辑训练流程**：解决 MiniMax-H3-Image 模型在编辑任务训练时的问题，确保图像编辑能力的训练链路正确运行。
- **重构 H3-Image 模型函数（modelfn）**：对模型调用逻辑进行结构化整理，使模型前向传播/训练逻辑更清晰，降低后续维护成本。
- **修复编辑数据集**：修正编辑任务数据集的加载或预处理问题，确保训练数据与目标任务对齐。
- **与项目整体方向的关系**：DiffSynth-Studio 是一个统一的扩散模型合成与微调框架，本次提交直接服务于其"支持多样化模型的训练与微调"这一核心目标，确保 MiniMax 系列模型的编辑（edit）训练能力可用。

### 3. 对项目的影响和潜在意义
- 提高了 MiniMax-H3-Image 模型编辑训练的**稳定性和可靠性**，使用户在使用编辑微调功能时不再遇到阻断性问题。
- 重构部分虽不改变功能，但提升了代码**可维护性**，为后续扩展更多编辑任务或模型变体奠定基础。
- 数据集修复意味着**训练数据管线的正确性**得到保障，直接影响微调效果的质量。
- 整体来看，这是一次针对特定模型训练链路的**质量加固**，体现了项目从"功能可用"向"稳定可靠"演进的趋势。

### 4. 值得关注的技术点
- **模型函数（modelfn）的重构模式**：将模型调用逻辑抽象化，这种模式可能被推广到其他模型的训练支持中，值得关注其设计是否形成可复用范式。
- **编辑任务数据集的修复细节**：编辑任务通常涉及输入-输出图像对的配对和条件注入（如 mask、参考图），修复可能涉及数据对齐、条件编码或损失计算的细微问题，这类问题往往是图像编辑训练效果不佳的根因。
- 提交信息简洁直接，**单次提交涵盖修复+重构+数据集三个层面**，说明作者对训练链路有较完整的诊断和修复能力。

### 5. 对项目发展的影响（结合 README 背景）
DiffSynth-Studio 作为 ModelScope 生态下的扩散模型微调工具，其竞争力在于**广泛支持不同架构模型的训练/推理**。本次提交通过修复 MiniMax-H3-Image 编辑训练，增强了该框架在**图像编辑微调**这一高需求场景的覆盖度。这种针对单一模型链路的深入修复，是项目保持**模型支持广度与深度**的关键持续工作，有助于提升用户在实际编辑任务中的微调成功率，进而巩固项目在开源微调工具中的生态地位。项目正处于功能完善与质量稳定并重的阶段，此类修复型提交是其走向生产可用的重要组成部分。

## 详细提交记录

### [fc8b4be](https://github.com/modelscope/DiffSynth-Studio/commit/fc8b4be56759de06cac585929f608227ac58766b)

- **作者**: Hong Zhang
- **时间**: 2026-11-18T02:32:08Z
- **提交信息**: Fix MiniMax-H3-Image edit training (#1833)

* fix edit training

* refactor h3-image modelfn

* fix edit dataset

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 39044
- **最后更新**: 2026-11-19T02:36:49Z

## 提交统计

- **昨日提交总数**: 93
- **提交者数量**: 45
- **主要提交者**: qiaonan02, pllimax, Xinyuan Tong

## AI分析总结

# sgl-project/sglang 昨日提交综合分析（93 个提交）

## 一、主要更新类型

- **功能新增**：约占一半，集中在 rust-server 的 API 路由补全、新模型适配、多硬件算子扩展。
- **性能优化**：约 10 项，涉及 PDL 内核启动、FP8 DeepGEMM 预填充、logprobs 主机拷贝、NPU 推测解码路径、NVIDIA MoE 融合内核配置。
- **Bug 修复**：约 18 项，覆盖调度器、disaggregation、JIT 内核、hicache、LoRA、模型加载器、分布式与多模态编码器等。
- **CI、文档与重构**：约 15 项，含多硬件平台测试门禁、多模态 token-space 重构、server_args 废弃参数清理、内核包与 CODEOWNERS 调整。

## 二、关键变更

- **Rust 前端功能对等**：一批连续提交补齐 Anthropic Messages、Ollama、OpenAI completions/chat、/v1/responses、/v1/score、embedding/classify/rerank、会话管理、PD 角色切换、LoRA/权重更新控制、NGRAM 外部语料等路由，并配合 api-codegen 实现"一套 schema、多协议输出"。可观测性同步增强：spec_verify 计数、请求调度时间戳、HTTP 延迟指标、含 decode 池与 host-staged 传输的 /v1/loads 报告。
- **前沿模型持续适配**：DeepSeek-V4/V4.1（NVIDIA SM12x、Hopper FP8、AMD gfx950）、Kimi-K3/K3.1（AMD MI350X、DWDP、共享专家权重）、dsv41-flash Indexer 调优、GLM-5.3-Flash 的 TMA down-projection 配置。
- **多硬件生态扩张**：AMD gfx950 拿到 KDA、A8W4 MoE、稀疏 MLA、FP4、latent-tail、LL collective、DCP top-k 等全套内核；Intel 获得 XPU LoRA 后端与 FP8/INT8 量化算子；NPU 补齐 Hicache 的 MLA fp8 / GQA mxfp8 KV 支持与 DFlash 去镜像 seq_lens 优化。
- **分布式与稳定性**：DP attention 负载发布、abort echo 路由、disaggregation 重复注册、mooncake 传输黑名单、dspark 在 prefill 阶段同时启用 dp-attention 与 PP/CP 等修复。
- **工程治理**：多平台回归测试门禁（MI35x MMMU、weekly CPU、128k 解码前缀）、sgl-router 独立发布渠道（router-v* 标签）、outlines 版本钉住。

## 三、项目影响

Rust 前端功能基本齐备，为默认化或正式发布铺路，有望显著降低高并发下 Python 层的延迟与内存开销；OpenAI/Anthropic/Ollama/Vertex/SageMaker 多协议支持扩大生态兼容面，降低迁移成本。AMD、Intel、NPU 内核与量化能力补齐，降低了非 NVIDIA 加速卡的部署门槛，扩大用户与贡献者群体。分散在缓存、LoRA、加载器、编码器的修复减少长尾故障，直接提升线上稳定性；测试门禁与参数治理则为后续迭代提供回归保障。整体上，SGLang 正从"功能跑通"迈向"多硬件、大规模、生产级"的成熟阶段，在异构算力时代保持高性能推理框架的竞争力。

## 四、值得关注的技术点

PDL（programmatic dependent launch）用于 qk-norm/KV-prepare/gate 内核，是 Hopper 上隐藏 launch 开销的新路径；megakernel、FlashInfer CuTe DSL 与 DeepGEMM MegaMoE 算子显示底层内核持续深化；Qwen 多模态 token-space 重构接近尾声；JIT benchmark 结构化记录与 mbarrier 内存 clobber 修复体现编译层健壮性投入；outlines 双端钉版本提示其语法后端兼容性风险需持续跟踪。此外，多个提交带 Claude/Cursor 共同署名，表明项目已规模化采用 AI 辅助开发流程。

## 详细提交记录

### [6eaca42](https://github.com/sgl-project/sglang/commit/6eaca42f573c34656d848249f788d1b39f2ae9d5)

- **作者**: Yue Fei
- **时间**: 2026-11-18T23:43:01Z
- **提交信息**: [Fix] [NVIDIA] deepseek_v4: Start DeepSeek-V4.1 on SM12x with TP8/EP8 defaults (#45261)

Co-authored-by: moria97 <feiyue2533@gmail.com>
Co-authored-by: juliankang4 <200967947+juliankang4@users.noreply.github.com>

### [d75d741](https://github.com/sgl-project/sglang/commit/d75d74142b9e267283a49ba78d5b16f811c4e191)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T23:16:35Z
- **提交信息**: [CI] sgl-router: Build a dispatched release from the router-v<version> tag, not a branch (#51120)

### [aa83b03](https://github.com/sgl-project/sglang/commit/aa83b0376b23c647b1272fbb0f47f64e2a74b8bd)

- **作者**: MANOJ KUMAR YADAV
- **时间**: 2026-11-18T22:01:05Z
- **提交信息**: [Doc] ci: Add OSS CI Hub usage notice (#51357)

### [0b42e63](https://github.com/sgl-project/sglang/commit/0b42e6344af830c1b0fc3a1951d7445f92d1ed91)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:44:48Z
- **提交信息**: [Feat] rust-server: The stateless /v1/responses API over the chat route (#49748)

### [be9cc54](https://github.com/sgl-project/sglang/commit/be9cc54f706a2daa800b0cafad62a150e58b23cb)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:14:36Z
- **提交信息**: [Feat] rust-server: Vertex and SageMaker generation wrappers, PUT /generate and slashed model ids (#49747)

### [b0909b3](https://github.com/sgl-project/sglang/commit/b0909b3f0429f54161177fa13efc7f2e7edc7df3)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:14:09Z
- **提交信息**: [Feat] rust-server: /v1/score, and the embeddings, classify, rerank and tokenize schema (#49746)

### [541606a](https://github.com/sgl-project/sglang/commit/541606a0751127bb1588f5c3678b6ccb1124eebf)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:13:40Z
- **提交信息**: [Feat] api: The OpenAI completions and chat completions schema and gRPC surface (#49745)

### [483f28b](https://github.com/sgl-project/sglang/commit/483f28b7ee92c8e407dccd87ecf8c84a89c91690)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:13:14Z
- **提交信息**: [Feat] rust-server: The Anthropic Messages API over HTTP and gRPC (#49744)

### [173cbe4](https://github.com/sgl-project/sglang/commit/173cbe4558afc1e9ef1db63b20752fa078d591d5)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:12:03Z
- **提交信息**: [Fix] scheduler: Publish load on every idle batch result under DP attention (#51038)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [de53a1a](https://github.com/sgl-project/sglang/commit/de53a1ae2b767537a004460511cb643ae1a8b5e2)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:11:40Z
- **提交信息**: [Fix] rust-server: Report meta_info.dp_rank as null without data parallelism, as the Python server does (#50851)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [3ab330c](https://github.com/sgl-project/sglang/commit/3ab330cd3c20e9269d8029fc23aca3a39506775a)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:11:28Z
- **提交信息**: [Feat] rust-server: Record sglang:spec_verify_calls_total in the Rust frontend (#50831)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [6c5a0ee](https://github.com/sgl-project/sglang/commit/6c5a0eedca29b68629beeb7376adfd3bf9d768eb)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:10:52Z
- **提交信息**: [Fix] rust-server: Time the latency metrics from an HTTP layer's request start (#50854)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [6963e3e](https://github.com/sgl-project/sglang/commit/6963e3e0a10b904a7b67b6634e268b153b4e7d41)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:10:26Z
- **提交信息**: [Feat] rust-server: Record on a generate request when it was handed to the scheduler (#50832)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [42109d4](https://github.com/sgl-project/sglang/commit/42109d4c9a74d0f00a1dc7c46735968e276f921b)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:10:17Z
- **提交信息**: [Chore] rust-server: Update the known-gap reason for per-request speculative-decoding stats (#50952)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [b51c781](https://github.com/sgl-project/sglang/commit/b51c7814b90495b93f7231d7c41ee009768abc55)

- **作者**: metamergebot
- **时间**: 2026-11-18T21:09:50Z
- **提交信息**: [Feat] disaggregation: Report a full decode host pool and landed host-staged transfers in /v1/loads (#50853)

Co-authored-by: metamergebot <324680979+metamergebot@users.noreply.github.com>
Co-authored-by: hanming-lu <hanming-lu@users.noreply.github.com>

### [d59b154](https://github.com/sgl-project/sglang/commit/d59b1542d024cc13a38d2c43ce67b002254c3ec3)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:06:22Z
- **提交信息**: [Feat] rust-server: The Ollama routes over HTTP and gRPC (#49743)

### [682657a](https://github.com/sgl-project/sglang/commit/682657a365927c9b1b270f19efd764bc38dec04a)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:05:55Z
- **提交信息**: [Feat] rust-server: configure_logging, the dumper routes, the HiCache L3 layout and elastic EP state (#49742)

### [ac584ef](https://github.com/sgl-project/sglang/commit/ac584ef1a02ba45780e0655c41cc69afe23e641f)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:05:25Z
- **提交信息**: [Feat] rust-server: /open_session, /close_session and session_params on generate (#49741)

### [b0ce736](https://github.com/sgl-project/sglang/commit/b0ce7369f9ee66d71d14e7b435a9cf9b2d69307c)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:04:58Z
- **提交信息**: [Feat] rust-server: External corpus routes for NGRAM speculative decoding (#49740)

### [07e72a9](https://github.com/sgl-project/sglang/commit/07e72a91dde12590b8e02cf5cd485bc4a06458fa)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:04:29Z
- **提交信息**: [Feat] rust-server: /parse_function_call and /separate_reasoning (#49739)

### [9e7f407](https://github.com/sgl-project/sglang/commit/9e7f4072a877d9504fc27299f826788df9096dcb)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:04:00Z
- **提交信息**: [Feat] rust-server: Weight reads, update groups, weight updates and LoRA refusals (#49738)

### [2e2c622](https://github.com/sgl-project/sglang/commit/2e2c622f2774675118c72be3e08f8f96e38fd91f)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:03:35Z
- **提交信息**: [Feat] rust-server: pd_role_switch and update_weight_version over the model-facts cache (#49737)

### [120c91c](https://github.com/sgl-project/sglang/commit/120c91cf32d958379698bc526e9de29d9b064466)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:02:40Z
- **提交信息**: [Feat] rust-server: set_internal_state, profiling, expert distribution, slow_down and memory occupation controls (#49736)

### [f01462f](https://github.com/sgl-project/sglang/commit/f01462f3b3d04af5d7f03b8701ce37cbc93b7f69)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:01:30Z
- **提交信息**: [Feat] rust-server: Pause and continue generation, freeze_gc, ping and ready, and the frontend state (#49735)

### [15c760c](https://github.com/sgl-project/sglang/commit/15c760cc31e2543a3bd27afdc0a455be0db5f9cc)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T21:01:11Z
- **提交信息**: [Feat] api-codegen: Tagged payload presence rules and multi-arm untagged lists (#49734)

### [6c2db99](https://github.com/sgl-project/sglang/commit/6c2db9966004a9e586e7b9cb9b8ab8edebf94b7e)

- **作者**: Rain Jiang
- **时间**: 2026-11-18T20:42:46Z
- **提交信息**: [Fix] kimi-k3: Read load_format through the model namespace accessor (#51311)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [9fbab1f](https://github.com/sgl-project/sglang/commit/9fbab1f6edc118e3eb499883a21e8899ef10ed2e)

- **作者**: Edwin Mascarenhas
- **时间**: 2026-11-18T19:20:18Z
- **提交信息**: [Perf] attention: Launch the qk-norm, KV-prepare and gate kernels with PDL (#51080)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: YAMY <74099316+YAMY1234@users.noreply.github.com>

### [8be74d4](https://github.com/sgl-project/sglang/commit/8be74d4137daf7061c0ef4a171bd079d01b8e658)

- **作者**: Woody-Hu
- **时间**: 2026-11-18T19:12:20Z
- **提交信息**: [Fix] diffusion/h3: Keep the projected AdaLN LoRA in the adapter dtype (#50611)

### [d08f4fe](https://github.com/sgl-project/sglang/commit/d08f4feee76e6a434d4ea414a30b4419f2f809f2)

- **作者**: Michael
- **时间**: 2026-11-18T18:46:49Z
- **提交信息**: [CI] [AMD] spur: Stop the log streamer's SIGPIPE from cancelling healthy jobs (#50727)

### [935055b](https://github.com/sgl-project/sglang/commit/935055b42ace8027e1f0a09251633c31d439c876)

- **作者**: Zhichen Zeng
- **时间**: 2026-11-18T18:02:52Z
- **提交信息**: [Doc] cookbook: Add DaisyRose-27B cookbook (#51290)

### [37f3b27](https://github.com/sgl-project/sglang/commit/37f3b2730bca1cc875126f8b94c4487ec1331a95)

- **作者**: Tri Dao
- **时间**: 2026-11-18T16:12:59Z
- **提交信息**: [Feat] kimi-k3: DWDP for KDA and shared-expert weights on PD prefill (#50842)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: kpham-sgl <khoa.pham@radixark.ai>

### [d89bc5b](https://github.com/sgl-project/sglang/commit/d89bc5b57477d89ab1411264599b153b6e34e78d)

- **作者**: 黄孝君
- **时间**: 2026-11-18T12:56:45Z
- **提交信息**: [CI] [NPU] chore: Bump SGLang kernel NPU tag to 2026.11.0.post8 (#51219)

Co-authored-by: Even Zhou <even.y.zhou@outlook.com>

### [21dae9b](https://github.com/sgl-project/sglang/commit/21dae9b17ef1f505b68066e63a40ac5df686e9fe)

- **作者**: Siyuan Chen
- **时间**: 2026-11-18T12:09:51Z
- **提交信息**: [Perf] dsv41-flash: Add FP8 DeepGEMM prefill scoring on Hopper (#49066)

### [44227af](https://github.com/sgl-project/sglang/commit/44227af064b6081e983efad379f0a2cf3566b87c)

- **作者**: esarafian
- **时间**: 2026-11-18T12:08:08Z
- **提交信息**: [Fix] routed-experts: return no tokens in the abort echo of a request whose routing is gone (#48254)

Signed-off-by: Elad Sarafian <esarafian@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>

### [440086b](https://github.com/sgl-project/sglang/commit/440086bdd8484df273ddab6134b5586ec3993ec1)

- **作者**: Rumit Desai
- **时间**: 2026-11-18T12:02:43Z
- **提交信息**: [Refactor] graph: Decouple eager_on_graph from CUDA capture (2/3) (#49457)

Co-authored-by: Alex Nails <alex.nails@radixark.ai>

### [ea93e2f](https://github.com/sgl-project/sglang/commit/ea93e2fcd0d1566f4817c0fe8ddfe6d8006908fd)

- **作者**: Kevin Mi
- **时间**: 2026-11-18T11:58:29Z
- **提交信息**: [Feat] [AMD] kimi-k3: Serve Kimi-K3.1 on MI350X / MI355X (gfx950) (#51000)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: AMD-yanfeiwang <yanfei.wang@amd.com>

### [e0decbc](https://github.com/sgl-project/sglang/commit/e0decbc3388fbc0bf02882311df5a1aa33502018)

- **作者**: Gregory Leleytner
- **时间**: 2026-11-18T11:20:39Z
- **提交信息**: [Perf] scheduler: Copy decode top logprobs to the host once per step (#50124)

Co-authored-by: Gregory Leleytner <9316547+RunFMe@users.noreply.github.com>

### [c2e9301](https://github.com/sgl-project/sglang/commit/c2e9301c5bd5d8d6fe72898fbb20edede62ff020)

- **作者**: Chunan Zeng
- **时间**: 2026-11-18T11:20:32Z
- **提交信息**: [Feat] inkling2: Add the FlashInfer CuTe DSL and DeepGEMM MegaMoE kernel ops (#51048)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a8db62b](https://github.com/sgl-project/sglang/commit/a8db62b8a4aaca89109f64b4a6886d27fb5dc828)

- **作者**: DarkSharpness
- **时间**: 2026-11-18T11:19:59Z
- **提交信息**: [Feat] jit: Record structured per-case results from the benchmark marker (#51030)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ac59b47](https://github.com/sgl-project/sglang/commit/ac59b471d389e1ebc10e86f22a867afddbcad017)

- **作者**: Kangrui Du
- **时间**: 2026-11-18T11:03:16Z
- **提交信息**: [Refactor] multimodal: [MM refactor 8/9] Check token-space Qwen output against the legacy processor (#46414)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [009b31b](https://github.com/sgl-project/sglang/commit/009b31b0100d45629797261c5b61b3f8eaed5ad0)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T10:46:39Z
- **提交信息**: [Feat] sgl-router: Add --dp-rank-policy least_tokens for engine-reported KV balance (#51147)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [f04d886](https://github.com/sgl-project/sglang/commit/f04d886bf79aa3d6237cbb12a3311838eb9f9bd8)

- **作者**: zijiexia
- **时间**: 2026-11-18T09:48:34Z
- **提交信息**: [Fix] utils: Keep the alignment helpers #48781 moved importable from utils.common (#51215)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6a31888](https://github.com/sgl-project/sglang/commit/6a31888b3304b4b1e3d2f7336b73a93b343e925c)

- **作者**: pllimax
- **时间**: 2026-11-18T09:46:02Z
- **提交信息**: [Test] [Ascend] npu: Rotate GLM-5.3 DCP/PCP accuracy suites by date parity and disable EPLB (#50965)

Co-authored-by: pllimax <pllimax@users.noreply.github.com>

### [0893ad0](https://github.com/sgl-project/sglang/commit/0893ad02f11491688219b320d44b1563360bf3a6)

- **作者**: Siyuan Chen
- **时间**: 2026-11-18T09:22:29Z
- **提交信息**: [Perf] dsv41-flash: Increase the prefill Indexer score tile budget (#49067)

### [0299a10](https://github.com/sgl-project/sglang/commit/0299a10a5a57cdfa0274723285b30c5bc949389c)

- **作者**: DarkSharpness
- **时间**: 2026-11-18T09:19:53Z
- **提交信息**: [Fix] jit: Add memory clobbers to the mbarrier wrappers (#51034)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8b546b8](https://github.com/sgl-project/sglang/commit/8b546b85d7c4ee37d955e3e564ca7b7268a5dd1d)

- **作者**: Eddie A. Tsai
- **时间**: 2026-11-18T09:09:10Z
- **提交信息**: [Fix] [AMD] diffusion: install amd-smi so FLUX.3 serves on ROCm on gfx1151 (#47756)

Co-authored-by: jacky.cheng <yichiche@amd.com>

### [bbf0b4e](https://github.com/sgl-project/sglang/commit/bbf0b4e89b84ceffe78af250f3a08b5edbd7ff6b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-18T09:06:51Z
- **提交信息**: [Refactor] kernels: Fix silent failures and prune dead code in the kernels package (3/4) (#50805)

Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [225cb59](https://github.com/sgl-project/sglang/commit/225cb59c677373e03ece5070349b053e3f264d31)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-11-18T09:06:45Z
- **提交信息**: [Perf] diffusion/qwen-image-2.1: Pack BCG prefix K/V once per request (#50519)

### [3a41a59](https://github.com/sgl-project/sglang/commit/3a41a599192906eee6aace241798136a6db2b9ad)

- **作者**: Yuhao Yang
- **时间**: 2026-11-18T08:45:18Z
- **提交信息**: [Fix] tests: Use image_processor_backend in the Qwen token-space test (#51207)

### [4693deb](https://github.com/sgl-project/sglang/commit/4693deba5a1603cb471820750f22dee8617953f4)

- **作者**: Kangrui Du
- **时间**: 2026-11-18T08:25:24Z
- **提交信息**: [Refactor] multimodal: [MM refactor 7/9] Add a token-space strategy for Qwen VL models (#46413)

Signed-off-by: rockdu <kangrdu@gmail.com>
Co-authored-by: Teng Ma <sima.mt@alibaba-inc.com>

### [da52796](https://github.com/sgl-project/sglang/commit/da52796a0500671b9d149edd77ddec52a56ac622)

- **作者**: Xinyuan Tong
- **时间**: 2026-11-18T08:09:12Z
- **提交信息**: [Fix] openai: Render DSV4.1 message tools with recipe (#49514)

Co-authored-by: Jimmy Shong <69131491+Jiminator@users.noreply.github.com>

### [4dfbb95](https://github.com/sgl-project/sglang/commit/4dfbb953eb55c56e5c592cebce1a1db0d04fe6bc)

- **作者**: MingxuZh
- **时间**: 2026-11-18T07:34:14Z
- **提交信息**: [CI] [Intel] xeon: Move all PR test suites to two SPR runners (#49488)

Co-authored-by: Ma Mingfei <mingfei.ma@intel.com>

### [160adb6](https://github.com/sgl-project/sglang/commit/160adb6db98d1820256d8df8964f040704f0d21b)

- **作者**: Jimmy Shong
- **时间**: 2026-11-18T07:22:57Z
- **提交信息**: [Fix] trtllm_mha: Pack a graph-built page table for eager reads (#47703)

### [0e0f003](https://github.com/sgl-project/sglang/commit/0e0f003efcafd4272fd4332ce1c6125ff8cee666)

- **作者**: Jimmy Shong
- **时间**: 2026-11-18T07:22:15Z
- **提交信息**: [Fix] dflash: Stage the draft sampler only for batches its buffers hold (#47644)

### [c808dca](https://github.com/sgl-project/sglang/commit/c808dcac9007155d6ea44aa23f71c768a92b9b2d)

- **作者**: shun8686
- **时间**: 2026-11-18T06:52:19Z
- **提交信息**: [CI] [NPU] test: Select the Mooncake PD transfer backend in DSV4-Flash cases (#51177)

### [5dae4ee](https://github.com/sgl-project/sglang/commit/5dae4eec305d63ed8459811416f0737b9ec8720a)

- **作者**: Alex Nails
- **时间**: 2026-11-18T06:49:54Z
- **提交信息**: [CI] chore: add CI permissions for rumitdesai and akashpalla (#51176)

### [da395ae](https://github.com/sgl-project/sglang/commit/da395ae0913ab92e57d9c1faeb5ab6b33a914b23)

- **作者**: zijie
- **时间**: 2026-11-18T06:41:02Z
- **提交信息**: [Feat] [AMD] muse-spark: Add gfx1250 support (#50707)

Co-authored-by: zijiecode <zijiecode@users.noreply.github.com>
Co-authored-by: Zijie Chen <300606707+zijiecode@users.noreply.github.com>

### [9eb3904](https://github.com/sgl-project/sglang/commit/9eb3904d1c310ecd2ca746bddd10ed43bb7f0d5a)

- **作者**: em-dreyer
- **时间**: 2026-11-18T06:36:59Z
- **提交信息**: [CI] megakernel: Run only the sgl-nvidia-mega models a PR asks for (#51087)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4af099e](https://github.com/sgl-project/sglang/commit/4af099e86edb34c724e447be9e3f907405ecc161)

- **作者**: Kevin Mi
- **时间**: 2026-11-18T06:33:08Z
- **提交信息**: [Feat] [AMD] speculative: MLA draft verify, DFLASH MLA context and target-only sampling kernels (#50999)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [7a04e8f](https://github.com/sgl-project/sglang/commit/7a04e8f44339e54429bc0084c6a7a432b31deba8)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T06:30:39Z
- **提交信息**: [Fix] disaggregation: Close the PP consensus store when a KV manager is torn down (#51134)

### [79db781](https://github.com/sgl-project/sglang/commit/79db781e5b613b5ae92b10899025d43fcbc6eb76)

- **作者**: ZY Y
- **时间**: 2026-11-18T06:30:24Z
- **提交信息**: [Test] [NPU] deepseek-v4: Restore the combined CP + DSPARK cases in the nightly multi-node pipeline (#51171)

### [4d200ca](https://github.com/sgl-project/sglang/commit/4d200caec7f0f52aceae01acbcd0298aa0cf2845)

- **作者**: iridiumine
- **时间**: 2026-11-18T06:20:09Z
- **提交信息**: [Perf] [NPU] dsv4: mirrorless seq_lens path for DFlash-family spec decode (#50763)

### [9d3c71c](https://github.com/sgl-project/sglang/commit/9d3c71cbbe0e27a527b6cbdd2e02529ed8f64a4f)

- **作者**: chuyeh
- **时间**: 2026-11-18T05:43:39Z
- **提交信息**: [Doc] [AMD] cookbook: Qwen3.5 MI355X FP8 agentic sets SGLANG_AITER_HONOR_EXPLICIT_MEM_FRACTION=1 on the v0.5.23 image (#51152)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [c8dc16d](https://github.com/sgl-project/sglang/commit/c8dc16dc2340673dbb8408129cd7897ad5aef4ec)

- **作者**: EdwardXuy
- **时间**: 2026-11-18T05:15:16Z
- **提交信息**: [Test] [NPU] kimi_k3: retune the 128k decode prefix case to C6 (#48894)

Co-authored-by: zhang-chunli01 <zhangchunli19@huawei.com>

### [9e5c4a7](https://github.com/sgl-project/sglang/commit/9e5c4a78e82823375115926e651337f335641771)

- **作者**: Kevin Mi
- **时间**: 2026-11-18T05:00:46Z
- **提交信息**: [Feat] [AMD] kimi-k3: gfx950 KDA verify, A8W4 MoE, latent-tail and LL collective kernels (#50998)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [8d72d2e](https://github.com/sgl-project/sglang/commit/8d72d2ea11901b49d694bcea543f1cffccf27629)

- **作者**: Kevin Mi
- **时间**: 2026-11-18T04:45:16Z
- **提交信息**: [Feat] [AMD] dsa: gfx950 sparse MLA, DCP top-k and FP4 index-K kernels for Kimi-K3.1 (#50997)

Co-authored-by: kk <43161300+kkHuang-amd@users.noreply.github.com>
Co-authored-by: Xinyi Song <xinyisong0111@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e1f0fc9](https://github.com/sgl-project/sglang/commit/e1f0fc95dbfb41779e22a2d3f4aac1cd6f8364fe)

- **作者**: qiaonan02
- **时间**: 2026-11-18T04:28:54Z
- **提交信息**: [Perf] [NVIDIA] fused_moe: Add H20 down-projection (TMA) configs for GLM-5.3-Flash TP8/TP4 (#48313)

### [0ad6477](https://github.com/sgl-project/sglang/commit/0ad64771d64f65eb76b5e2cf5bed3067e1fb1c74)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:25:28Z
- **提交信息**: [Fix] hicache: Expect the KV dtype suffix in page-unified L3 object names (#51081)

### [47d0034](https://github.com/sgl-project/sglang/commit/47d00340ba64c76b791fc600b3fdc7099f128b4d)

- **作者**: zijiexia
- **时间**: 2026-11-18T04:25:22Z
- **提交信息**: [Doc] cookbook: Add Hy4-flash cookbook (#51160)

### [ca89fae](https://github.com/sgl-project/sglang/commit/ca89faed521beafb5a353cea8b5987e1fd4364f3)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:25:01Z
- **提交信息**: [Fix] lora: Expose the bias and deferred-finalize flags on LoRA-wrapped layers (#51083)

### [bf5af3d](https://github.com/sgl-project/sglang/commit/bf5af3dee5eee18b95ff1118ab63cb9a1894f3f7)

- **作者**: Sam Shleifer
- **时间**: 2026-11-18T04:19:44Z
- **提交信息**: [Fix] model-loader: Support RunAI for PP Nemotron MTP drafts (#49348)

Co-authored-by: Erik Wijmans <erik@thinkingmachines.ai>

### [013c0fb](https://github.com/sgl-project/sglang/commit/013c0fbcbc5cd0d16255f1a8bfd33ff09329e1d5)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:19:33Z
- **提交信息**: [Fix] cpu: Pin outlines to the version the outlines grammar backend imports (#51086)

### [063d9d4](https://github.com/sgl-project/sglang/commit/063d9d4af835c0a2bf250e8ed4b9ae0b239cc227)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:19:02Z
- **提交信息**: [Fix] tests: Update the weekly CPU unit tests for recent model and linear changes (#51085)

### [386edff](https://github.com/sgl-project/sglang/commit/386edff54da2d6cc35c6f2c38c55afcb5ca95368)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:12:45Z
- **提交信息**: [CI] slash-command: Refresh the CI-states block after commands that add labels or rerun (#51093)

### [7946e58](https://github.com/sgl-project/sglang/commit/7946e589c54dc72baf7a88ba3b036f6c8ac27770)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T04:09:12Z
- **提交信息**: [Refactor] server_args: Remove deprecated flags, choice values and environment variables (#51074)

### [b085beb](https://github.com/sgl-project/sglang/commit/b085beba3dbf35e499df7dd99e367fcf096a6a1a)

- **作者**: vstone-w
- **时间**: 2026-11-18T03:54:23Z
- **提交信息**: [Fix] [NPU] dspark: Support enabling dspark&dp attention during prefill while also enabling pp or cp (#50783)

### [f61c3b5](https://github.com/sgl-project/sglang/commit/f61c3b51f5f2f5b68168328c1d7d3cf33917b049)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T03:52:56Z
- **提交信息**: [Chore] CODEOWNERS: Add Shunkangz as a weight_cache owner (#51149)

### [b1a02a5](https://github.com/sgl-project/sglang/commit/b1a02a53719c6fac2f9e1c86756c894bb53d0dcd)

- **作者**: Ma Mingfei
- **时间**: 2026-11-18T03:14:49Z
- **提交信息**: [Fix] [Intel] cpu: Pin Outlines to compatible version (#51124)

### [dd7daa9](https://github.com/sgl-project/sglang/commit/dd7daa93117414b692f367a5a054ec3f9242dcbe)

- **作者**: Michael
- **时间**: 2026-11-18T03:01:53Z
- **提交信息**: [CI] [AMD] muse-spark: Add a MI35x nightly MMMU accuracy gate (#49749)

### [acf9d94](https://github.com/sgl-project/sglang/commit/acf9d94231c63135a6c77f6d9fbd82fe80b3a31d)

- **作者**: DarkSharpness
- **时间**: 2026-11-18T02:57:55Z
- **提交信息**: [CI] cpu: Register test_quant_ops to the renamed extra-test-cpu-intel suite (#51133)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [255a084](https://github.com/sgl-project/sglang/commit/255a0844b11d144ab49bba9d15e25c322b0d623b)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T02:20:49Z
- **提交信息**: [Fix] encoder: Reject scalar hashes, accept an empty feature list, and keep media payloads out of load errors (#51114)

### [8f2e5fe](https://github.com/sgl-project/sglang/commit/8f2e5fe54efabf30a87138c6e6477676412686d4)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T02:11:45Z
- **提交信息**: [Fix] encoder: Keep a result reached in the timeout tick and format the gRPC receive URL IPv6-safe (#51123)

### [bff44f5](https://github.com/sgl-project/sglang/commit/bff44f5fd7a1f5d7662c45382be4aa8011ed4225)

- **作者**: YanbingJiang
- **时间**: 2026-11-18T01:53:36Z
- **提交信息**: [Feat] [CPU] quantization: Add CPU FP8/INT8 quant ops and compressed-tensors support (#41329)

### [8c6ee5d](https://github.com/sgl-project/sglang/commit/8c6ee5d5e6e37dfdc9af8558ffbb582ad4d9f7b4)

- **作者**: LinyuanLi
- **时间**: 2026-11-18T01:33:04Z
- **提交信息**: [Feat] [NPU] hicache: Support modelslim MLA fp8 kv and GQA mxfp8 kv for L2 Hicache (#50023)

### [add961d](https://github.com/sgl-project/sglang/commit/add961dab2c0ee18e18f8a46fc26ab34292536ab)

- **作者**: Baizhou Zhang
- **时间**: 2026-11-18T01:30:41Z
- **提交信息**: [Refactor] muse-spark: Delete unreachable kernels and dispatch modes (#51116)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [457cfa3](https://github.com/sgl-project/sglang/commit/457cfa33e88efd2e0094cd9587379847e543886a)

- **作者**: srujan-thomdapu
- **时间**: 2026-11-18T01:30:09Z
- **提交信息**: [Feat] [Intel] lora: Add intel_xpu LoRA backend (#44769)

### [78b8523](https://github.com/sgl-project/sglang/commit/78b8523f77ea6b930d065c9dd128a97b222a35c9)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T01:14:57Z
- **提交信息**: [Doc] sgl-router: Document the PyPI and container installs in one place (#51118)

### [6f35d41](https://github.com/sgl-project/sglang/commit/6f35d412f2f98c922fb80e168cbf03147c6aa019)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T01:03:27Z
- **提交信息**: [Fix] disaggregation: Count a prefill rank once in the bootstrap server however often it registers (#51111)

### [cd3045f](https://github.com/sgl-project/sglang/commit/cd3045fa6e12ef3b426af906137634b6f5cac956)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T00:38:17Z
- **提交信息**: [Fix] mooncake: Snapshot a room's transfer infos in the worker and blacklist the session on an aux write failure (#51077)

### [7fed639](https://github.com/sgl-project/sglang/commit/7fed639806be1b03ef4eaba3fc4ad2117a8f2be4)

- **作者**: Shangming Cai
- **时间**: 2026-11-18T00:34:15Z
- **提交信息**: [CI] sgl-router: Release the router image and PyPI wheel from router-v* tags (#50076)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [0fcd253](https://github.com/sgl-project/sglang/commit/0fcd253a8768e659994875cee1b0fd96374f1fc7)

- **作者**: Liangsheng Yin
- **时间**: 2026-11-18T00:33:50Z
- **提交信息**: [Test] rust-server: Decouple the request-log fixture from the request classes' fields (#51101)

### [445bb97](https://github.com/sgl-project/sglang/commit/445bb971292275570eecfbab3020642f0a86d844)

- **作者**: Michael
- **时间**: 2026-11-18T00:24:22Z
- **提交信息**: [CI] [AMD] diffusion: Fix two layerwise-offload unit tests on ROCm (#49930)

### [0f15098](https://github.com/sgl-project/sglang/commit/0f1509829b3920780aaea05bfc72b33db350a2e8)

- **作者**: Lee Nau
- **时间**: 2026-11-18T00:21:31Z
- **提交信息**: [Fix] moe: Pad NVFP4 trtllm hidden size to a multiple of 256 (#50008)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1308
- **最后更新**: 2026-11-18T07:57:31Z

## 提交统计

- **昨日提交总数**: 41
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

# cache-dit 仓库昨日提交分析总结

## 1. 主要更新类型

- **功能新增**：新算法（HiCache 校准器）、新模型支持（P-H3-Image、Pika-H3-Flex）、VAE-P 分块并行解码器
- **Bug 修复**：FP8 基准测试因被移除的 `use_ws` 参数导致 72 行报错、`calibrator_kwargs` 为 null 时的崩溃、vendored scheduler 配置丢失
- **文档更新**：占比最大，README 反复精简、发布/内核技能刷新、HiCache 与量化说明补充
- **工程化**：v1.5.5 发布注解、构建与打标签顺序规则、平台标签派生逻辑

## 2. 关键变更点与项目方向的关系

- **HiCache 落地（#1359/#1362）**：这是核心算法演进。HiCache 复用 TaylorSeer 的有限差分阶梯，仅通过 `_basis_term` 钩子替换外推基函数为阻尼 Hermite 多项式，保持单拷贝状态。实测在同一 harness 下 FLUX 达 33.33 dB，优于 reuse(31.72) 和 TaylorSeer-o2(30.91)，且 sigma→0 会坍缩到 24.99，复现了论文的 sigma 消融——说明项目在缓存算法上从"实现"走向"可验证对标"。
- **模型矩阵扩张**：P-H3-Image（8 步 MiniMax-H3 图像模型，复用视频模型的块/CP/TP 计划）与 Pika-H3-Flex（diffusers 原生模块化管线 + 视频 VAE 分块并行）持续扩大 60+ DiT 管线覆盖面，是项目差异化竞争力。
- **README 治理**：大量提交把根 README 精简为"简介/社区/引用"，模型表迁至 `docs/README.md`，并用技能（skill）显式禁止回填——这是为了遏制文档漂移，形成单一权威来源。

## 3. 影响与潜在意义

- 新校准器通过 CLI（`--calibrator hicache`）即可启用，配合五路互斥配置，用户侧接入成本低；同时修复 `refresh_context()` 重置路径的 `NoneType.copy` 崩溃，提升了缓存上下文刷新的健壮性。
- 修正发布技能中错误的 32MB wheel、`svdq_is_available()`、"先打标签后构建"等承诺，避免未来发版写出错误数字或卡在缺失标签上——发布流程从"隐性经验"固化为"显性契约"。
- 文档与模型注册路径统一后，贡献者集成新模型/新缓存算法的路径更清晰，降低协作摩擦。

## 4. 值得关注的技术点

- **基函数 vs 调度的归因**：命中位置跨行完全一致、mask-pinned 配对保持排序，证明性能差来自外推基而非调度，这种实验设计保证了结论可信。
- **防退化测试**：测试钉死具体状态类型、接线后的 sigma、以及"预测≠锚点"的非等值断言——并明确记录 RandPipeline 下"输出不同"不能证明接线正确，避免后续集成者重踩坑。
- **签名漂移防护**：基准测试记录 `inspect.signature(fp8_gemm).parameters`，使未来签名变更不会静默失效某个测试分支。
- **VAE-P 分块策略**：`_decode_clip` 的 256px 分块 + 64px 重叠是唯一可无损切分的单位，round-robin 分发并回传 rank 0 保持位级一致。

## 5. 对项目发展的整体影响

这些提交体现了 cache-dit 从"功能堆叠"转向"可验证、可维护的成熟工程"：算法层面用同 harness 对标论文建立可信度，模型层面持续扩张 DiT 生态并补齐并行能力（CP/TP/VAE-P），文档与发布流程则通过技能和单一来源约束来抑制技术债。缓存算法的钩子化架构（`_basis_term`）为后续更多外推基留出了低成本扩展点，是本次最重要的结构性收益。

## 详细提交记录

### [a08768c](https://github.com/vipshop/cache-dit/commit/a08768c9c8d103229b1aaf978c76ec24605bc9ff)

- **作者**: DefTruth
- **时间**: 2026-11-18T12:04:47Z
- **提交信息**: docs(skill): record the HiCache outcome and the reset-path gotcha (#1362)

Judge the case as implemented rather than "worth integrating": HiCache ships as
calibrators/hicache.py (#1359), the landing point moved from "a basis switch on
Taylor" to the _basis_term hook plus a separate calibrator, and the same-harness
numbers now exist (FLUX 1.7x: 33.33 dB vs reuse 31.72 and TaylorSeer-o2 30.91,
sigma=1 collapses to 24.99 which reproduces the paper's sigma ablation).

Also record two things the next integration should not rediscover:

- a new calibrator's to_kwargs() must tolerate a null calibrator_kwargs, because
  refresh_context() rebuilds through empty(); TaylorSeer/DMD/SVD crashed there
  until #1359;
- RandPipeline feeds the same hidden_states to every step, so a predictor's
  forecast equals the anchor and "the output differs" cannot prove the wiring.

landscape.md gains the measured table (4.5): hit positions are identical across
rows, and a mask-pinned pair keeps the ordering, so the gap is the basis and not
the schedule.

### [79a9555](https://github.com/vipshop/cache-dit/commit/79a955530a68acea78e68e39d2bcb89920ba7847)

- **作者**: DefTruth
- **时间**: 2026-11-18T11:55:48Z
- **提交信息**: chore(docs): Add 'HiCache' to cache acceleration description (#1360)

* Update README.md

* Fix typos in README.md regarding cache types

* Add 'HiCache' to cache acceleration description

Updated the README to include 'HiCache' in the cache acceleration list.

* Enhance README with additional quantization details

Updated the README to include quantization methods (SVDQ/FP8/FP4).

* Modify quantization details in README.md

Updated quantization options in the README.

* Update README.md

* Fix formatting in README.md for Cache-DiT section

* Revise Cache-DiT support details in README

Updated the support information for Cache-DiT to reflect current capabilities.

* Enhance README with quantization and DiT support info

Updated the README to include quantization details and improved clarity on DiT pipeline support.

* Update README.md

* Update README.md

### [de3044b](https://github.com/vipshop/cache-dit/commit/de3044bf7f1d684a59435e2e776b455736134b74)

- **作者**: DefTruth
- **时间**: 2026-11-18T11:37:35Z
- **提交信息**: feat(cache): add HiCache damped-Hermite calibrator (#1359)

* feat(cache): add HiCache damped-Hermite calibrator

HiCache (arXiv 2508.16984) keeps TaylorSeer's finite-difference ladder and
replaces only the extrapolation basis with H~_k(x) = sigma^k * H_k(sigma * x),
where H is the physicist Hermite polynomial. The ladder stays single-copy:
TaylorSeerState gains a _basis_term hook and hicache.py overrides only that,
so a missing override degrades loudly (tests pin the concrete state type, the
wired sigma and a non-equal forecast against TaylorSeer).

- new HiCacheCalibratorConfig (hicache_order <= 4, hicache_sigma in (0, 1]),
  factory alias, five-way mutual exclusion in load_configs, and
  --calibrator hicache --calibrator-params order=,sigma= on the CLI
- docs: CACHE_API chapter plus comparison table, EXAMPLES help snapshot
- tests: hand-computed Hermite table (k=0..4), sigma=1 undamped control,
  sigma -> 0 anchor collapse, bit-exact max_cached_steps=0 run, pipeline wiring
- FLUX.1-dev 1024^2/28 steps/rdt 0.12: 12 cached steps at identical positions
  in every row; HiCache o2 sigma=0.5 reaches 33.33 dB/0.9781 vs reuse
  31.72/0.9706 and TaylorSeer o2 30.91/0.9733 at the same 9.88 s

* fix(cache): tolerate a null calibrator_kwargs after a config reset

cache_dit.refresh_context(transformer, **shorthand) is the only reset=True caller: it rebuilds
the config through CalibratorConfig.empty(), which nulls every non-constant field including
calibrator_kwargs, and the rebuilt context then calls Calibrator(config) -> to_kwargs().
TaylorSeer/DMD/SVD still did self.calibrator_kwargs.copy() there, so refreshing a cache context
into one of those three calibrators raised AttributeError: 'NoneType' object has no attribute
'copy' (FoCa already returned a literal {} and HiCache was written with dict(... or {})).

- base CalibratorConfig.to_kwargs() and the TaylorSeer/DMD/SVD overrides now use
  dict(self.calibrator_kwargs or {}); the result is still a fresh shallow copy, so the in-place
  field writes in the overrides stay safe
- tests/api/test_calibrator_reset.py: five reset=True factory cases, the base config, explicit
  params surviving the reset, and the public refresh_context() path starting from a
  calibrator-free cache (the branch that replaces calibrator_config wholesale); reverting any of
  the four lines fails 4 of those tests

### [ed926ee](https://github.com/vipshop/cache-dit/commit/ed926eeee12b30b9935d6c655d006bec744fee2b)

- **作者**: DefTruth
- **时间**: 2026-11-18T08:50:58Z
- **提交信息**: chore: update docs (#1356)

* Enhance README with new features and compatibility details

Updated README to include support for 60+ DiT pipeline families and clarified compatibility with torch.compile.

* Enhance README with description of Cache-DiT

Added a note emphasizing that Cache-DiT is fast, easy to use, and flexible for various DiTs.

* Update README to specify hybrid cache acceleration

* Remove 'hybrid' from Cache-DiT description

* Revise README for Cache-DiT features and support

Updated the README to reflect changes in parallelism options and added details about support for DiT pipeline families.

* Update README with new parallelism options

Updated the README to reflect changes in parallelism options.

* Clarify description of Cache-DiT in README

Updated the README to specify 'various DiTs' instead of 'DiTs'.

* Revise README for Cache-DiT features and compatibility

Updated README to enhance clarity and detail about Cache-DiT features and compatibility.

### [2e84bba](https://github.com/vipshop/cache-dit/commit/2e84bbaae1c7946e581150fad5dec363355f8a50)

- **作者**: DefTruth
- **时间**: 2026-11-18T07:24:52Z
- **提交信息**: docs(skills): register model support in docs/README.md only (#1355)

Root README.md is now intentionally minimal (intro / community integration /
citations) and no longer carries the supported-model table, so the skill and
its references must stop pointing model registration at it.

- cache-dit-model-integration: Phase 7.6 and the documentation table now name
  docs/README.md as the single authoritative model list; add an explicit
  "do not add a model table to the root README" row.
- rfc_pending_models 7.2: drop the stale Boogu-Image row (it is vendored under
  models/pipelines/boogu_image and listed in docs/README.md); keep the payoff
  caveat.
- cache-dit-cache-integration extension points: new cache algorithms go to
  docs/user_guide/CACHE_API.md + docs/README.md, not the root README.

### [a773996](https://github.com/vipshop/cache-dit/commit/a7739960e6fed46d79e748016192767bcc9da17c)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:46:45Z
- **提交信息**: Merge pull request #1353 from vipshop/dev

docs: keep README.md simple

### [24b0221](https://github.com/vipshop/cache-dit/commit/24b0221c3e429ff547678ff2927a67665787e696)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:45:59Z
- **提交信息**: Merge branch 'main' into dev

### [a17d107](https://github.com/vipshop/cache-dit/commit/a17d10799299223c3bfe435f3b9c85912c65e1b9)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:44:35Z
- **提交信息**: Add celebration emojis to DiT pipeline support section

Updated README to include celebration emojis for DiT pipeline families and variants.

### [a66775f](https://github.com/vipshop/cache-dit/commit/a66775f1ab6b41be6da5f9febe10a1bd07bc6a81)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:43:52Z
- **提交信息**: Update README.md

### [f322e7e](https://github.com/vipshop/cache-dit/commit/f322e7e49c639e2d63b230651bd0386b547ef775)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:41:56Z
- **提交信息**: Update README.md

### [68b4850](https://github.com/vipshop/cache-dit/commit/68b4850f32011252b02b7e2cb75d8d873971e95e)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:37:59Z
- **提交信息**: Update README to reflect Cache-DiT support changes

### [d367663](https://github.com/vipshop/cache-dit/commit/d367663e0acf85acaa6117d375ebb36e5fa87da5)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:36:30Z
- **提交信息**: Update README to highlight support for DiT pipelines

### [a577536](https://github.com/vipshop/cache-dit/commit/a577536a54b08925945960076ca32f3706428814)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:33:21Z
- **提交信息**: Revise Cache-DiT description in README.md

### [1074b32](https://github.com/vipshop/cache-dit/commit/1074b32a88e2eeceefb4163023d560ad6dc5ebcc)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:31:40Z
- **提交信息**: Update README.md

### [56a8535](https://github.com/vipshop/cache-dit/commit/56a8535da69116391d2ea928dbfdb41e7f649046)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:31:03Z
- **提交信息**: Update README.md

### [8e28b19](https://github.com/vipshop/cache-dit/commit/8e28b197e3778813611468a3198c626daf4458be)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:30:27Z
- **提交信息**: Revise README to clarify Cache-DiT features

### [16740fe](https://github.com/vipshop/cache-dit/commit/16740fe10d0d96bf531e7c3c17ab7ca65bb87961)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:28:29Z
- **提交信息**: Revise Cache-DiT description in README

Updated the description of Cache-DiT for clarity and conciseness.

### [e39fcb7](https://github.com/vipshop/cache-dit/commit/e39fcb71e1cd0cdc326b8168dd01aabd6bc24e80)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:26:53Z
- **提交信息**: Update README.md

### [c14b152](https://github.com/vipshop/cache-dit/commit/c14b152e5a0756aa17226c52128a2a93df3019a7)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:24:37Z
- **提交信息**: docs: keep README.md simple

### [837e070](https://github.com/vipshop/cache-dit/commit/837e0700882f816912f987b446a77050747d5ad6)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:23:44Z
- **提交信息**: docs: keep README.md simple

### [d588de9](https://github.com/vipshop/cache-dit/commit/d588de9af345b91d0c1629312d3ed6a41ce9ea9b)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:23:08Z
- **提交信息**: docs: keep README.md simple

### [3880d6f](https://github.com/vipshop/cache-dit/commit/3880d6f5e1bdcecdbe48efab8410d2d6caba2dc7)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:19:10Z
- **提交信息**: docs: keep README.md simple

### [77d21e5](https://github.com/vipshop/cache-dit/commit/77d21e5643c24a328b669b0932496845da0c17bd)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:18:31Z
- **提交信息**: docs: keep README.md simple

### [5572089](https://github.com/vipshop/cache-dit/commit/5572089e4d8c9819884c9ae702a27b77ac079d3a)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:16:22Z
- **提交信息**: docs: keep README.md simple

### [35d9ada](https://github.com/vipshop/cache-dit/commit/35d9ada2c8058f7c4e50df64134ca62625f31cd4)

- **作者**: DefTruth
- **时间**: 2026-11-18T06:14:38Z
- **提交信息**: docs: keep README.md simple

### [b92b64e](https://github.com/vipshop/cache-dit/commit/b92b64e5296c45a2b182ece9cbc1dc8397afa280)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:53:02Z
- **提交信息**: Update README.md

### [6089f17](https://github.com/vipshop/cache-dit/commit/6089f17c34c7ecce8e0d7cf2373c2495d0fe505a)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:52:46Z
- **提交信息**: Fix CUDA version specification in README

### [346c4ed](https://github.com/vipshop/cache-dit/commit/346c4ed0845d7cba74dc38b06a612434ffbc0b32)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:51:54Z
- **提交信息**: Update CUDA and PyTorch requirements in README

### [e76ad28](https://github.com/vipshop/cache-dit/commit/e76ad285233d53bee616c485391ed4b6cc654625)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:50:58Z
- **提交信息**: Update README with new requirements and instructions

### [d4bcaf2](https://github.com/vipshop/cache-dit/commit/d4bcaf2384694547c7b8ec35d2f06c7f6c7a43e2)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:46:07Z
- **提交信息**: Merge pull request #1352 from vipshop/docs/post-release-1.5.5

docs: refresh the release and kernel skills after v1.5.5

### [dd37064](https://github.com/vipshop/cache-dit/commit/dd3706488c94dd0701eb86273a26334c2a9c247a)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:43:21Z
- **提交信息**: docs: refresh the release and kernel skills after v1.5.5

The release skill still promised 32 MB wheels on manylinux_2_38, called the removed `svdq_is_available()`, and told the operator to tag before building. None of that matches the v1.5.5 artifacts or the scripts' contracts; a future run would either write the wrong numbers or trip over a missing tag.

- product table: ~8 MB wheels, ~1.4 MB pure wheel, and the platform tag/floor are derived by `repair_wheel_platform_tag.py` (`2_34` for 1.5.5, `2_38` for 1.5.3) instead of a constant
- add the two ordering rules this release produced: build before tag/publish, and assert `HEAD == v<V>^{commit}` before `publish_index.sh` (its `--target` is the running HEAD). Tag creation moved to the end of step 2, which is what step 3 needs
- verification: one `pip download` only covers the running interpreter's cp wheel; `github.com:443` is flaky rather than blocked; PyPI parity is a JSON digest check; the install check runs outside the repo tree and asserts `cache_dit.__file__`
- arch coverage: v1.5.5 ships `sm_89` + `sm_120a` only; Ampere lost its cubins while Hopper never had one, which belongs in the release notes' Upgrade Notes
- install-and-index: v1.5.5 facts on top, v1.5.3 demoted to history, host environment moved out of the history block
- custom-kernel: `fp8_gemm` has no `use_ws` since the CUTLASS collective migration; the WS reasoning and measurements are marked as history instead of instructions, with a superseded banner in `references/fp8.md`
- tools: usage examples move to 1.5.5, and `build_releases.sh`'s arch comment is corrected to the real default set (89,120a)

### [8f9b28c](https://github.com/vipshop/cache-dit/commit/8f9b28ca23749ccb57d8747f0fb456815c1f9389)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:07:40Z
- **提交信息**: Merge pull request #1351 from vipshop/docs/release-1.5.5

release: prepare the v1.5.5 annotations and repair the FP8 benchmark

### [7d5d43b](https://github.com/vipshop/cache-dit/commit/7d5d43be73917cebe97f5527be95a36b0258489c)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:04:35Z
- **提交信息**: fix(bench): drop the removed `use_ws` arms from the FP8 benchmark

`eced0158` removed `use_ws` from `fp8_gemm`, but the bench kept passing it, so `gemm_ws`/`gemm_nonws`/`chain_ws`/`chain_nonws` failed on every shape and mode: 72 ERROR rows on the default suite. CUTLASS picks the mainloop and the warp specialization now, so that contrast cannot be measured any more.

- fold `cache_chain(use_ws)` into a parameterless `cache_chain`
- keep one `cache_dit_gemm` / `cache_dit_chain` arm each
- add `cache_dit_gemm_scaled_mm` (`use_native=False`) as the remaining second GEMM path; per_block has no `_scaled_mm` reference, so it is not registered there
- record `inspect.signature(fp8_gemm).parameters` in the metadata so a further signature change cannot silently invalidate an arm

Fixes #1350

### [85a66e9](https://github.com/vipshop/cache-dit/commit/85a66e9772581061044ab14032c87c29a956b24b)

- **作者**: DefTruth
- **时间**: 2026-11-18T03:04:30Z
- **提交信息**: docs: point the built-in pipeline annotations at v1.5.5

The built-in pipeline table still names `cache-dit@main`, which stops being true once the release is cut. Name the minimum version instead, and make the source link resolve to the same tag.

- README.md, docs/README.md: 14 `cache-dit@main` annotations -> `@1.5.5`, and `[cache-dit-url]` -> tree/v1.5.5
- P-H3-Image (Edit) carried `diffusers@m0.43.0`; drop the stray `m`
- docs/user_guide/INSTALL.md: release examples 1.5.3 -> 1.5.5, and the full profile reaches py311..py314 (py310 is no longer a release target)

### [56ca62c](https://github.com/vipshop/cache-dit/commit/56ca62cba87f8417450eb03cae63e91ce0369e8c)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:38:14Z
- **提交信息**: Update SANA-Video 2B entries in README

### [4760e06](https://github.com/vipshop/cache-dit/commit/4760e064549620b1fdad12649200192eeb4afc0d)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:37:47Z
- **提交信息**: Update README.md

### [e507998](https://github.com/vipshop/cache-dit/commit/e507998e6cdcf230edca95ac18a3b9021dc68cad)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:35:45Z
- **提交信息**: Update model sources and C/P/Q/OF status in README

### [26fd18c](https://github.com/vipshop/cache-dit/commit/26fd18c9e3ebc15880d9b039afe8dcfc005a443e)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:35:00Z
- **提交信息**: Update P-H3-Image model version references

Updated version references for P-H3-Image models.

### [977d7b9](https://github.com/vipshop/cache-dit/commit/977d7b96ab3cfd0675e3023fc41bb319cfa8d9d8)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:33:39Z
- **提交信息**: Update README.md

### [0ac303c](https://github.com/vipshop/cache-dit/commit/0ac303ce655c50fc1d349c1f26cae2154d0a4109)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:31:48Z
- **提交信息**: feat(model): support P-H3-Image (8-step MiniMax-H3 based image model) (#1348)

* feat(model): support P-H3-Image with cache/CP/TP/TE-P/VAE-P

P-H3-Image (PrunaAI/P-H3-Image) is the post-trained image MiniMax-H3: it drives the
video MiniMaxH3Transformer3DModel over one packed [text | audio | image] sequence with
eight guidance-free steps, so the block contract, the CP plan and the TP plan are the
video ones and only the pipeline layer differs.

- register the PH3Image adapter prefix (delegates to the MiniMax-H3 adapter) and add it
  to the verified modular-pipeline whitelist
- add the ph3_image / ph3_image_edit CLI examples: the prompt-upsampler step is popped
  for benchmarking (--prompt-enhancer keeps it), the eight-step cache budget caps the
  warmup at two, and the MiniMax-H3 quantization exclusions carry over
- add the AutoencoderKLPH3Image VAE-P planner: the model tiles inside _encode_clip /
  _decode_clip over 5-D tiles, so the planner distributes those tiles and stitches on
  rank 0, which keeps the decode bit-identical to the serial path
- read the conditioning noise level from P-H3-Image's keyframe_noise_aug as well, so
  --adaln-online sees the two-row timestep vectors of an edit request
- add the CP/TP aliases to the summary matrix and the model rows to README, docs/README
  and the NVIDIA GPU matrix
- add CPU guards: prefix/whitelist/signature, both workflows, the upsampler pop, the
  cache budget, the AdaLN timestep sets, the VAE planner, and a two-rank gloo tile test

* fix(cli): keep the prompt-upsampler step for --prompt-enhancer

The hook popped the step unconditionally and then reloaded the components, so pointing
--prompt-enhancer at the checkpoint kept paying the upsampler's residency while the short
request was still rendered verbatim (measured: 5.56 s at 512^2, identical to the popped
run). Keep the step when the directory is the checkpoint the pipeline was loaded from, so
the upsampler actually rewrites the prompt (14.08 s at 512^2, 67.10 GiB), and only pop +
reload when it names a different directory.

* fix(model): address the review of the P-H3-Image wiring

- keep the prompt-upsampler step whenever --prompt-enhancer names a directory: the
  earlier hook popped it unconditionally and then reloaded the components, so the step
  never ran (update_components swaps pipe.prompt_upsampler but cannot put the block back)
- promote the step-count warning to ValueError: the eight steps are the checkpoint's
  sigma grid and there is no --sigmas-style escape hatch, so an explicit request is
  unsatisfiable rather than ignorable
- log the cache-budget clamps (max_warmup_steps, max_continuous_cached_steps) instead of
  silently pinning them, and read them off the CLI
- log the keyframe_noise_aug fallback in the AdaLN grid reader
- neutralise the --prompt-enhancer help text, which hard-coded the MiniMax-H3-Image-PE
  repository and an aspect-ratio rule that do not hold for P-H3-Image
- cite diffusers main (0.44.0.dev0) in the model table: p_h3_image is not in v0.42.0 nor
  v0.43.0
- move the AdaLN grid guards to tests/api/test_adaln_plan.py, pin the workflow pruning to
  the measured 8/12 steps and the 6-block tree, add a real-PH3ImageModularPipeline case
  that proves pipe.blocks is a deepcopy, and make the planner guard independent of the
  order test files ran in

* test(model): close the P-H3-Image review comments

- drive enable_cache with a real PH3ImageModularPipeline so the prefix match, the
  whitelist and the adapter's resolve_transformer are actually exercised, instead of only
  enabling cache on a bare transformer
- keep the prompt-upsampler step for a foreign enhancer directory on a real pipeline, with
  the loaders stubbed on PreTrainedModel/AutoProcessor (patching the transformers module
  attributes does not take once _LazyModule materialised the class)
- reject --prompt-enhancer under torchrun: every rank would load its own 18.8 GiB copy
- drop the fake block pop from the fake pipeline, which is what let the earlier no-op
  enhancer pass its test
- assert the VAE-P tile path to the last bit (rtol=0, atol=0) instead of the default 1.3e-6
- warn once when VAE-P runs with tiling disabled, where it silently costs world_size
  times the serial VAE
- correct the both-names AdaLN comment: neither checkpoint declares both

* docs(model): mark P-H3-Image cache and quantization as not usable

The matrix records usability, not whether a switch runs. At the checkpoint's eight-step grid
DBCache accepts three of eight steps and lands at 15.04 dB / 0.5955 SSIM (18.11 / 0.6954 with
a two-step mask), and fp8 per-row lands at 17.04 dB / 0.6832 (11.93 / 0.4958 at 2912^2), both
below their gates, so both columns become crossings like MAGI-2 Preview. Parallelism stays
checked (21-23 dB is the checkpoint's own rerun floor, 22.58 dB, i.e. deterministic reduction
order rather than drift) and offload stays checked (byte-identical to the baseline).

### [6b1b8d4](https://github.com/vipshop/cache-dit/commit/6b1b8d448e99b6a24adbe2966fa79ee6fe58f0cc)

- **作者**: DefTruth
- **时间**: 2026-11-18T01:27:28Z
- **提交信息**: feat(model): support Pika-H3-Flex (diffusers-native modular pipeline) (#1349)

* feat(model): support the official diffusers Pika H3 Flex pipeline

The released checkpoint is diffusers' PikaH3FlexModularPipeline; cache-dit's
vendored copy stays as the diffusers < 0.43 fallback. resolve_pika_h3_flex()
returns the pipeline, its block factory and its reference package as one
binding, because the official block tree is resolved by name out of diffusers
and its reference types live in their own module.

- fix the vendored scheduler losing stochastic_sampling / shift_provided_sigmas
  to the parent's register_to_config on a diffusers whose parent names them
  (a silent fall-back to the deterministic Euler ladder), and drop a deprecate()
  call whose removal version has been reached
- take the row indices back to the host in build_row_timesteps, as upstream does
- rework the drift guard into version-conditional assertions plus a
  re-noising equivalence check against the installed release
- add the six CLI entry points (resolver-based and explicit vendored), the
  PIKA_H3_FLEX_DIR path mapping, and a CUDA indices regression case
- move the model's table rows from the built-in list to the diffusers list
  (0.43.0) and add the supported-matrix rows

* feat(vae-p): tile-parallel decoder for the MiniMax-H3 video VAE

Pika H3 Flex decodes 124 frames per request and the video VAE takes 34% of a
single-GPU run, so distribute its spatial tiles instead of leaving VAE-P out.

`AutoencoderKLMiniMaxH3._decode_clip` lays 256-pixel tiles with a 64-pixel
overlap over the pixel grid of one clip and stitches them back with
`_stitch_tiles`; a tile is the only unit that can be split without changing the
result. The planner hands the tiles of every clip round-robin, keeps the
temporal chunk loop replicated, and sends the decoded tiles back to rank 0
through `TileSafeP2PComm` with `set_dims(5)`. The audio VAE stays serial: the
CLI only offers `pipe.vae` to `--parallel-vae`.

- take the scheduler guards off the module constant so the fallback half is a
  function the tests can drive, and assert the resolver leaves the vendored
  class out when the installed release owns the contract
- rebuild the re-noising equivalence check against an independent
  reconstruction of the update, then compare the installed release to it
- decide the row-timestep host cast with a `torch.Tensor.cpu` spy: torch >= 2.0
  returns the right plan either way, so a traceback cannot separate the two
- flip the drift guard and the matrix from "no planner" to "video covered,
  audio not", and refresh the adapter comment that claimed the released
  pipeline was absent from diffusers

* docs(model): mark Pika-H3-Flex quantization as a memory-for-fidelity trade

The acceptance matrix measures fp8 per-row at 0.73x the async offload reference
with SSIM 0.585 / mel_ssim 0.582, and W4A4 nvfp4 r64 at 1.34x with SSIM 0.490 /
SI-SDR -7.3 dB, both below the same-config rerun floor. Neither is a quality-
preserving configuration, so the quantization column cannot read as supported.

* fix(pika-h3): review follow-ups on the cache evidence and the VAE-P binding

- bind the tile-parallel `_decode_clip` on the auto-encoder instance instead of its class, as the
  MiniMax-H3-Image planner already does: `dispatch.py` only refuses a second apply through
  `_is_parallelized`, so a class-level patch would leak this rank's group and comm into every other
  `AutoencoderKLMiniMaxH3` in the same process
- list `PikaH3Flex` in the CP/TP alias table of `summary.py` so `supported_matrix()` stops reporting
  a missing planner for a model that runs CP2 at 2.16x; add `FastH3` to the tensor axis only, its VSA
  compression gate has no verified context-parallel path
- drop `_pika_h3_flex_blocks()`, dead since the example started taking `binding.blocks_factory`
- correct the drift module docstring, which still described VAE-P as unresolvable for the MiniMax-H3
  autoencoders while the assertions below it require the video one to resolve
- document that `--parallel-vae` only takes `pipe.vae`, so the audio decoder of Pika H3 Flex,
  MiniMax-H3 and FastH3 always runs serially

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 97189
- **最后更新**: 2026-11-19T03:36:04Z

## 提交统计

- **昨日提交总数**: 110
- **提交者数量**: 84
- **主要提交者**: Lantao Jin, Jee Jee Li, fxmarty-amd

## AI分析总结

# vLLM 昨日提交总结（110 条）

## 一、主要更新类型

- **性能优化**占比最高，涉及 GLM-5.3-Flash、MoE、KV Cache、注意力内核、Triton 内核、视觉塔等多处热路径。
- **Bug 修复**数量紧随其后，集中在 Rust 前端、ROCm 后端、KV Offload、多模态、LoRA、量化、指标统计与 NIXL/KV 传输。
- **功能新增**包括多结构化输出后端、GPU 计时指标、TorchCodec 解码后端、Muse Spark 解析器迁移、Inkling 2 Small 与 HY4 Flash 配方等。
- **重构与基建**包括 LinearKernel 基类抽取、vLLM IR 算子化（RoPE）、编码器 CUDA graph 共享、pytest 9.2 升级、flaky 测试清理与文档规范提升。

## 二、关键变更与项目方向

- **ROCm/AMD 生态持续深化**：约三分之一提交涉及 ROCm/AITER（性能、CI、Recipe、MLA/DCP、MXFP4、gfx942、DSv4.1、Muse Spark MoE 归约），AMD 后端正从"可用"走向"高性能生产级"，与 NVIDIA 投入并重，契合"人人可用"的目标。
- **Rust 前端集中打磨**：修复流式 HTTP 指标、finish_reason、tool call 约束、gRPC 默认温度，并新增共享内存对象存储，正走向生产可用。
- **KV Offload 与 PD 分离打磨**：修复解码器抢占后的重复 KV 拉取、为每 rank 分配独立 CPU 区域、NIXL 多 KV 组失败上报，直接服务于低成本长上下文服务。
- **MoE 与量化演进**：支持 ModelOpt INT8_PB_WO 路由专家、SM107 MXFP4 专家、GLM-5.3 在线量化扩展到 BF16 注意力投影，以及 MXFP8 量化选择优化。
- **模型覆盖扩展**：Kimi-K3、DeepSeek V4/V4.1、Qwen4Exp、MiniMax-M3、gpt-oss、Pixtral、Nemotron 等均有专属优化或修复。
- **结构化输出与解析引擎统一**：Muse Spark 移植、工具名增量扫描、多后端共存、DeepSeek-V4.1 工具搜索渲染、allocate_token_bitmask 简化。

## 三、影响与意义

性能类提交直接降低 serving 延迟与显存开销，兑现 "fast and cheap" 的核心承诺。Rust 前端的密集修复减少生产环境协议兼容与可观测性问题，降低迁移风险。抢占恢复、磁盘写满误报、SIGTERM 处理保留等修复减少罕见但致命的故障；安全方面，多模态条目上限默认 999、启动时拒绝 LoRA 批分片采样提升了默认配置安全性。RL 链路的 direct reload 参数校验与词嵌入重绑修复支撑训练推理一体化。CI 系统性升级为高频合并提供可靠回归防线。

## 四、值得关注的技术点

- **LinearKernel 基类**与 **vLLM IR RoPE 算子化**为跨 CUDA/ROCm 内核统一抽象奠基，利于长期后端解耦。
- **KDA 走 FlashInfer**、**AiterFlashAttention K/V 视图缓存**体现算子库跨厂商复用趋势。
- **NIXL 远程 prefill 在 KV 租约过期后拒绝读取**是分布式 KV 传输正确性的关键加固。
- **抢占指标改为调度器计数**与**空区间日志时钟重启**修正监控语义，影响容量规划判断。
- 精细内核技巧：融合量化到生产者、块级 TP 切分 MXFP4 专家、Triton 弃用 `tl.make_block_ptr`、HIP VMM 跨 DP rank 共享 Engram 主机表。
- **AI 辅助开发常态化**：超过 70% 提交含 Claude/Codex 等共同署名，AI 智能体已深度嵌入开发流程。

## 五、整体影响

vLLM 正处于"性能深水区 + 生产级工程化"并行推进阶段：一方面通过多硬件适配扩大部署覆盖面，通过 Rust 前端与解析引擎统一提升服务化质量；另一方面以量化扩展、内核抽象和 CI 加固为高频迭代提供底座。项目正稳步向稳定、成熟的大规模生产服务平台演进。

## 详细提交记录

### [6f687a0](https://github.com/vllm-project/vllm/commit/6f687a0836363e636740919b0ee4510aff80098f)

- **作者**: Sriram Kumar
- **时间**: 2026-11-18T23:56:51Z
- **提交信息**: [ROCm][Perf][GLM-5.3-Flash] Drop int32/int64 copies in the kpool sparse indexer (#63910)

Signed-off-by: Sriram Kumar <sriramkumar.kishorekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f3f612e](https://github.com/vllm-project/vllm/commit/f3f612ecfa76e6c541362ce6a7bd80f06c197273)

- **作者**: Ao Tang
- **时间**: 2026-11-18T23:55:08Z
- **提交信息**: [Perf][GLM-5.3-Flash] KDA decode and prefill through FlashInfer (#63544)

Signed-off-by: Ao Tang <aot@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5d4a24e](https://github.com/vllm-project/vllm/commit/5d4a24ea337e53e3fdc5dabbea05f188af4c8d3c)

- **作者**: Chenjie Luo
- **时间**: 2026-11-18T23:54:41Z
- **提交信息**: [Quantization] Support ModelOpt INT8_PB_WO routed experts (#66717)

Signed-off-by: Chenjie Luo <chenjiel@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2aa3f0e](https://github.com/vllm-project/vllm/commit/2aa3f0ec1eb29eb3e42d979da2c53fb4cb02b15f)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T22:45:50Z
- **提交信息**: [CI] Say when /ci rocm cache comes before the base image is pushed (#68480)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7f17bc](https://github.com/vllm-project/vllm/commit/f7f17bcfe8aad602a0cfd50a5db02021293afc01)

- **作者**: Samay
- **时间**: 2026-11-18T22:14:29Z
- **提交信息**: [Frontend] Port the Muse Spark parsers to the streaming parser engine (#62728)

Signed-off-by: Samay <samay.piduru@gmail.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [57936fd](https://github.com/vllm-project/vllm/commit/57936fd5c155c266c4b5c3fb98f0d724af956e7c)

- **作者**: Mirza Halilčević
- **时间**: 2026-11-18T22:00:54Z
- **提交信息**: [Bugfix] Fix GPU sync check failures in NemotronLabsDiffusion (#68376)

Signed-off-by: Mirza Halilcevic <mirza.halilcevic@amd.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [b24eda7](https://github.com/vllm-project/vllm/commit/b24eda7127a9c5c317f699db3f580135eec7322b)

- **作者**: Hongkuan Zhou
- **时间**: 2026-11-18T21:26:11Z
- **提交信息**: [Feature] Add optional GPU timing to iteration metrics (#61690)

Signed-off-by: hongkuanz <hongkuanz@nvidia.com>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>
Co-authored-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e52665b](https://github.com/vllm-project/vllm/commit/e52665b860a4683f92009c33c19dd25e7283113f)

- **作者**: yzong-rh
- **时间**: 2026-11-18T21:23:30Z
- **提交信息**: [Structured Output] Simplify allocate_token_bitmask (#68484)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [855fba3](https://github.com/vllm-project/vllm/commit/855fba32deab06bf01c34a6b6cf8290f533be6c2)

- **作者**: Mingyuan Ma
- **时间**: 2026-11-18T20:37:25Z
- **提交信息**: [MoE][NVIDIA] Support MXFP4 experts on SM107 in flashinfer_moe_ep_cutedsl (#66158)

Signed-off-by: Mingyuan Ma <mingyuanm@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [1282680](https://github.com/vllm-project/vllm/commit/1282680cd6ebed079a7e9a2d8b539888c41a6a9a)

- **作者**: Kushal
- **时间**: 2026-11-18T20:13:03Z
- **提交信息**: [Bugfix][Core] Reject batch-sharded sampling with LoRA at startup (#56074)

Signed-off-by: Kushal <72650064+kushaldabbe@users.noreply.github.com>
Signed-off-by: Kushal Dabbe <72650064+kushaldabbe@users.noreply.github.com>
Co-authored-by: opencode <noreply@opencode.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [21ff7e0](https://github.com/vllm-project/vllm/commit/21ff7e018f4d0d5b1f564e9f4b643f0768dbc9d8)

- **作者**: Concurrensee
- **时间**: 2026-11-18T20:10:44Z
- **提交信息**: [ROCm][Test] Skip the AITER MoE alignment test where AITER isn't supported (#62527)

Signed-off-by: Yida Wu <yida.wu@amd.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [1846120](https://github.com/vllm-project/vllm/commit/1846120b2b71c43ff6dd0b8c51f933a4b4b09e6b)

- **作者**: Leizhen Zhang
- **时间**: 2026-11-18T20:09:09Z
- **提交信息**: [Bugfix] ParserEngine: scan for the tool name incrementally while streaming (#67156)

Signed-off-by: LeizhenZhang <zhangleizhen645@gmail.com>
Co-authored-by: Flora Feng <4florafeng@gmail.com>

### [2409a8f](https://github.com/vllm-project/vllm/commit/2409a8f844e9af4664e604c39c9846846c770f14)

- **作者**: Misha Goin
- **时间**: 2026-11-18T20:05:14Z
- **提交信息**: [Quantization] Give linear kernels a common LinearKernel base class (#68019)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a01451b](https://github.com/vllm-project/vllm/commit/a01451befcf4a0f7cc7247235a486fc42d9f3006)

- **作者**: hshrivastava-droid
- **时间**: 2026-11-18T19:16:24Z
- **提交信息**: [Recipe] MiniMax-M3.1-Flash: add H100 AgentX TP8 DSpark preset (#68487)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [86e675f](https://github.com/vllm-project/vllm/commit/86e675ffef381b4d7d12ce5d48271e0eecb4881e)

- **作者**: hshrivastava-droid
- **时间**: 2026-11-18T19:15:47Z
- **提交信息**: [Recipe] MiniMax-M3.1-Flash: add H200 AgentX TP8 DSpark preset (#68486)

Signed-off-by: hshrivastava-droid <hshrivastava@nvidia.com>
Co-authored-by: Claude Sonnet 5.5 <noreply@anthropic.com>

### [067624f](https://github.com/vllm-project/vllm/commit/067624f48776455e57d3bbaf1418575be84d3e44)

- **作者**: Hugo Abonizio
- **时间**: 2026-11-18T18:54:03Z
- **提交信息**: [Bugfix][NIXL] Decline remote prefill reads after the producer's KV lease expired (#66011)

Signed-off-by: Hugo Abonizio <hugo.abonizio@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Nick Hill <16958488+njhill@users.noreply.github.com>
Co-authored-by: binxuwang2002-lang <232507676+binxuwang2002-lang@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [c0d8697](https://github.com/vllm-project/vllm/commit/c0d8697c5b0a9d7715550514e955d7821bcf9c23)

- **作者**: Robert Shaw
- **时间**: 2026-11-18T18:39:00Z
- **提交信息**: [Frontend][DeepSeek-V4.1] Render tool search like deepseek-recipe (#68211)

Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>

### [5bde00b](https://github.com/vllm-project/vllm/commit/5bde00bb198e1755139d66704ddb674906d7183e)

- **作者**: Misha Goin
- **时间**: 2026-11-18T18:28:35Z
- **提交信息**: [Core] Log the backends each kind of layer selected after model load (#67526)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5ff924e](https://github.com/vllm-project/vllm/commit/5ff924e5b90a466cd8adb57e637f1afc9a88e728)

- **作者**: Amir Friedman
- **时间**: 2026-11-18T18:22:35Z
- **提交信息**: [Bugfix][KV Offload] Report the final SWA tail in first_live_chunk_idx (#68359)

Signed-off-by: Amir Friedman <Amir.Friedman1@ibm.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [01533e4](https://github.com/vllm-project/vllm/commit/01533e426c4798c36e824a62325241aaf61996c8)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-18T18:21:09Z
- **提交信息**: [CI] Make the Nemotron GSM8K offload entries exercise the CPU reload (#67916)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0dd1aad](https://github.com/vllm-project/vllm/commit/0dd1aad1e7dd6efeed34ea82e965f19d3ef48ec3)

- **作者**: frida-andersson
- **时间**: 2026-11-18T18:15:22Z
- **提交信息**: [ROCm][Recipe] Qwen3.8-Flash-Next: verify BF16 on MI325X with AITER (#66911)

Signed-off-by: Frida Andersson <fanderss@amd.com>

### [536f3ca](https://github.com/vllm-project/vllm/commit/536f3caa2873682ee4f9913fcc9609955d58b6f5)

- **作者**: Vinayak Gokhale
- **时间**: 2026-11-18T18:01:14Z
- **提交信息**: [Bugfix][ROCm][MiniMax-M3.1] Fix the decode glue crash with preshuffled MXFP8 weights (#68454)

Signed-off-by: Vinayak Gokhale <vinayak.gokhale@amd.com>
Co-authored-by: Fangzhou Ai <31551580+Fangzhou-Ai@users.noreply.github.com>

### [5f0f87e](https://github.com/vllm-project/vllm/commit/5f0f87e80ad3fec558a23ce0c37e6749edbd0cdd)

- **作者**: Ao Tang
- **时间**: 2026-11-18T18:00:04Z
- **提交信息**: [Quantization][GLM-5.3] Let online quantization reach the BF16 attention projections (#64373)

Signed-off-by: Ao Tang <aot@nvidia.com>

### [2be71b1](https://github.com/vllm-project/vllm/commit/2be71b1831385115258a3158103ae0a711e3e037)

- **作者**: Shivji Kumar Jha
- **时间**: 2026-11-18T17:35:15Z
- **提交信息**: [Bugfix][Metrics] Count preemptions in the scheduler, not on resume (#65317)

Signed-off-by: Shivji Jha <shiv4289@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e7f0e63](https://github.com/vllm-project/vllm/commit/e7f0e63cf19a6c2c0b7af23086658ad62af28b00)

- **作者**: Martin Hickey
- **时间**: 2026-11-18T17:25:50Z
- **提交信息**: [Frontend][Multimodal] Return mm_hashes from /inference/v1/generate (#68135)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [abe1fab](https://github.com/vllm-project/vllm/commit/abe1fab59c10bf5ce33957d7acffad71c8e0ef00)

- **作者**: Mirza Halilčević
- **时间**: 2026-11-18T17:16:39Z
- **提交信息**: [ROCm][CI] Force the ASM path in test_online_mxfp4_hadamard[aiter-asm] (#68188)

Signed-off-by: Mirza Halilcevic <mirza.halilcevic@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [abb8194](https://github.com/vllm-project/vllm/commit/abb8194dc35e4d72e0b81a41ed7d786a96b97e7c)

- **作者**: Woosuk Kwon
- **时间**: 2026-11-18T17:14:32Z
- **提交信息**: [Model] Add Inkling 2 Small for Blackwell (#67325)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c1f6a9f](https://github.com/vllm-project/vllm/commit/c1f6a9f84f2693e4089c35f35b8a6021f2438786)

- **作者**: xaguilar-amd
- **时间**: 2026-11-18T17:11:27Z
- **提交信息**: [ROCm][Bugfix] Fix AITER shared-expert fusion routing for gate-less MoE (DeepSeek-V2-Lite) (#64737)

Signed-off-by: xaguilar-amd <xavier.aguilarfruto@amd.com>
Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [e00e02e](https://github.com/vllm-project/vllm/commit/e00e02e0093ff8be59862764e424d33520b47862)

- **作者**: WatchTree-19
- **时间**: 2026-11-18T17:10:01Z
- **提交信息**: [Bugfix][Metrics] Restart the logging interval clock on empty intervals (#55474)

Signed-off-by: WatchTree-19 <119982314+WatchTree-19@users.noreply.github.com>

### [6092bb9](https://github.com/vllm-project/vllm/commit/6092bb9b59a97b9b5b1eaca9581da179ceff3e05)

- **作者**: Matvei Pashkovskii
- **时间**: 2026-11-18T17:07:53Z
- **提交信息**: [vLLM IR][RoPE] Port base RotaryEmbedding to a vLLM IR op (CUDA + ROCm/AITER) (#58838)

Signed-off-by: Oleksandr Kachur <oleksandr.kachur@amd.com>
Signed-off-by: Matvei Pashkovskii <mpashkov@amd.com>
Co-authored-by: Icey <1790571317@qq.com>
Co-authored-by: Oleksandr Kachur <oleksandr.kachur@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: root <root@chalupa-4cb4-host.dal-spse>
Co-authored-by: Simon Danielsson <70206058+simondanielsson@users.noreply.github.com>
Co-authored-by: Rohan Potdar <rohan.potdar@amd.com>

### [11aa136](https://github.com/vllm-project/vllm/commit/11aa1369e297f67bc4dc26e119d10830f39956c6)

- **作者**: stefankoncarevic
- **时间**: 2026-11-18T16:15:14Z
- **提交信息**: [CI][Test] Expect the decode-crossed Mamba hit in test_qwen_mtp_mamba_prefix_cache_hit_is_bounded (#68356)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [46d94c9](https://github.com/vllm-project/vllm/commit/46d94c97ce051f4038f921bf6965310fb727355a)

- **作者**: yzong-rh
- **时间**: 2026-11-18T16:09:10Z
- **提交信息**: [Feat] Support multiple structured-output backends on one server (#67335)

Signed-off-by: Yifan Zong <yzong@redhat.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [dbf3b25](https://github.com/vllm-project/vllm/commit/dbf3b25bbdac6e5e5ac7f311ff32677ea235801a)

- **作者**: Zohaib Moti
- **时间**: 2026-11-18T16:04:21Z
- **提交信息**: [ROCm][Bugfix] W4A16 dense prefill cache: drop the load-time memory budget check (#64744)

Signed-off-by: Zohaib Moti <zohaib.moti@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [e423cfa](https://github.com/vllm-project/vllm/commit/e423cfae1255ecb8b5e1d35c4e8c94d4a729972f)

- **作者**: Harry Mellor
- **时间**: 2026-11-18T15:52:39Z
- **提交信息**: [Docs] List speculative decoding methods supported by the Transformers backend (#68449)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [578be86](https://github.com/vllm-project/vllm/commit/578be86c94a26dda09eceb00c67c7ca62deefeb0)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T15:49:11Z
- **提交信息**: [ROCm][Perf][MoE] Dequantize only distinct routed experts in OCP MX emulation (#68086)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [36f738e](https://github.com/vllm-project/vllm/commit/36f738e51b59c0c099917201ec855e1761921c0e)

- **作者**: sahirema
- **时间**: 2026-11-18T15:48:42Z
- **提交信息**: [Benchmark] Add --random-mm-video-encode-fps to random-mm (#65493)

Signed-off-by: sanirema <santosh.hiremath@amd.com>
Co-authored-by: Claude Sonnet 5 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [fc982d4](https://github.com/vllm-project/vllm/commit/fc982d42c6344c5e3db6f9e0829b1cf19abd37bf)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T15:45:41Z
- **提交信息**: [ROCm][CI] Make test_amd_ci_fast_exit independent of inherited signal state (#67567)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [ffe3137](https://github.com/vllm-project/vllm/commit/ffe31372b043244fa1b009e180a087b4d57f1838)

- **作者**: Daniel Quintas
- **时间**: 2026-11-18T15:40:57Z
- **提交信息**: [Feature][Multimodal] Name every uncached item in the cache-miss error (#68429)

Signed-off-by: danielquintas8 <daniel.quintas.lopes@gmail.com>

### [ea75c00](https://github.com/vllm-project/vllm/commit/ea75c00c758dfacbc515a49e2ba3072eb7bdb7a0)

- **作者**: Pham Binh
- **时间**: 2026-11-18T15:35:59Z
- **提交信息**: [ROCm][Perf] Cache AiterFlashAttention K/V cache views per tensor (#66541)

Signed-off-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>
Co-authored-by: Pham Binh <194774975+phambinhfin@users.noreply.github.com>

### [191565a](https://github.com/vllm-project/vllm/commit/191565a2cd0c42a1e4fd4d063f53d0ce383b364f)

- **作者**: xaguilar-amd
- **时间**: 2026-11-18T15:19:14Z
- **提交信息**: [ROCm][MLA][DCP] Serve the non-causal DSpark draft on TRITON_MLA under DCP (#64261)

Signed-off-by: Yichao Zhu <Yichao.Zhu@amd.com>
Signed-off-by: Xavier Aguilar <xavier.aguilarfruto@amd.com>
Co-authored-by: Yichao Zhu <Yichao.Zhu@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [8f3c672](https://github.com/vllm-project/vllm/commit/8f3c672dc02b2f0804cb96ebe4611835715bb193)

- **作者**: fxmarty-amd
- **时间**: 2026-11-18T15:00:12Z
- **提交信息**: [Docs] Raise the bar for PR descriptions (#68404)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>

### [eca61f5](https://github.com/vllm-project/vllm/commit/eca61f52c1e40752f7589b25ce24b4f0e4108e55)

- **作者**: Avinash Paul
- **时间**: 2026-11-18T14:56:04Z
- **提交信息**: [ROCm][Disagg][CI] Fix the NIXL cells broken by UCX 1.23's ROCm DMABUF default (#66514)

Signed-off-by: avpaul <avpaul@amd.com>
Co-authored-by: avpaul <avpaul@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [abfa95d](https://github.com/vllm-project/vllm/commit/abfa95d34fe8bd3f1e63414bb534a5a82e683224)

- **作者**: stefankoncarevic
- **时间**: 2026-11-18T14:51:39Z
- **提交信息**: [ROCm][CI][Test] Spawn the workers in the DSv4.1 mono merge AB test (#68391)

Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [cbb38c4](https://github.com/vllm-project/vllm/commit/cbb38c458499f0cb3d81741318b8465678b3fbd1)

- **作者**: wang.yuqi
- **时间**: 2026-11-18T14:31:19Z
- **提交信息**: [Entrypoint] Use tri-state for add_special_tokens in pooling entrypoint. (#68344)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [092b7aa](https://github.com/vllm-project/vllm/commit/092b7aaa658050ab321d1ba9a64498c905281ee6)

- **作者**: Reid
- **时间**: 2026-11-18T14:08:53Z
- **提交信息**: [Bugfix] [Rust Frontend] Fix HTTP metrics for streaming and cancelled requests (#61856)

Signed-off-by: reidliu41 <reid201711@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e8d4bc6](https://github.com/vllm-project/vllm/commit/e8d4bc63a3b98d1f3c21705a23fbe7bd0d410e68)

- **作者**: Bharath
- **时间**: 2026-11-18T14:06:50Z
- **提交信息**: [Bugfix][Rust Frontend] Return 400 when auto tool parser is unavailable (#63843)

Signed-off-by: Primefury <bharathbhukya2002@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2d4ebf9](https://github.com/vllm-project/vllm/commit/2d4ebf923903b4f9881ffae8d0246a53a05fbd85)

- **作者**: Deepak G
- **时间**: 2026-11-18T14:05:20Z
- **提交信息**: [Bugfix][Rust Frontend] Include null finish_reason in streaming chat choices (#63739)

Signed-off-by: Deepak <deepak.g@bcinformatics.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Deepak <deepak.g@bcinformatics.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f7486b4](https://github.com/vllm-project/vllm/commit/f7486b452a14cd4b0cee64089baa82b2f7b46f20)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-18T14:03:47Z
- **提交信息**: fix(security): default multimodal item limit to 999 for unconfigured modalities (#52602)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [745f683](https://github.com/vllm-project/vllm/commit/745f683b03bc9a7df14002d040a2960a2e8ea97f)

- **作者**: Liangliang Ma
- **时间**: 2026-11-18T13:54:14Z
- **提交信息**: [XPU] Run Transformers backend attention sinks test on XPU (#68349)

Signed-off-by: Ma, Liangliang <liangliang.ma@intel.com>

### [267c065](https://github.com/vllm-project/vllm/commit/267c0656410d6a01c1e2f4f0bf9bad996a195673)

- **作者**: Jared Wen
- **时间**: 2026-11-18T13:51:27Z
- **提交信息**: [ROCm][Perf][GDN] Export Triton and AITER FlyDSL prefill checkpoints on ROCm (#68310)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: yuttian1 <224218912+yuttian1@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [4bf7222](https://github.com/vllm-project/vllm/commit/4bf7222187fb47efef19e4783803ecad138ac2a3)

- **作者**: Arian Boukani
- **时间**: 2026-11-18T13:39:26Z
- **提交信息**: [Bugfix][Rust Frontend] Serve gpt-oss when vllm serve omits the parser flags (#66998)

Signed-off-by: Arian Boukani <boukani.arian@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1a268df](https://github.com/vllm-project/vllm/commit/1a268dfd8aa40e95a04631173f3a9a18e00113fe)

- **作者**: Arian Boukani
- **时间**: 2026-11-18T13:38:05Z
- **提交信息**: [Bugfix][Rust Frontend] Constrain to a single tool call when parallel_tool_calls is false (#66988)

Signed-off-by: Arian Boukani <boukani.arian@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fea42ed](https://github.com/vllm-project/vllm/commit/fea42edb07ae82ac237e9ad8178f6ae4c0c2428f)

- **作者**: fxmarty-amd
- **时间**: 2026-11-18T13:36:00Z
- **提交信息**: [Tests] Reuse single-rank parallel groups for faster GPU unit tests (#68162)

Signed-off-by: Felix Marty <Felix.Marty@amd.com>
Co-authored-by: Tomas Ruiz <tomas.ruiz.te@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [5bf4f7a](https://github.com/vllm-project/vllm/commit/5bf4f7a2b074df335506a8cf1ca008f9f3b20fb7)

- **作者**: aoshen02
- **时间**: 2026-11-18T13:22:10Z
- **提交信息**: [Model Loader] Direct reload reruns post-load processing on the cold-start modules (LoRA) (#68345)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ae9faa8](https://github.com/vllm-project/vllm/commit/ae9faa8472af20e19586a88b03ed406f39ad39c6)

- **作者**: Bugen Zhao
- **时间**: 2026-11-18T13:15:21Z
- **提交信息**: [Rust Frontend] Serve the scale-out render routes on the main server (#67889)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vinayak <singhvinayak288@gmail.com>

### [92fd8cc](https://github.com/vllm-project/vllm/commit/92fd8cc66899b9e9c76eda66db3c2f70fda1df42)

- **作者**: Isotr0py
- **时间**: 2026-11-18T12:44:49Z
- **提交信息**: [1/4][Rust Frontend] Add rust shm obj storage implementation (#67902)

Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [9062519](https://github.com/vllm-project/vllm/commit/90625197443ed5739cb8f97f8dde737e24ed3065)

- **作者**: anhtra3889
- **时间**: 2026-11-18T12:44:03Z
- **提交信息**: [Spec Decode] Pass multimodal embeddings to NemotronH MTP (#68153)

Signed-off-by: Anh Tran <anhtra@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: tomeras91 <57313761+tomeras91@users.noreply.github.com>

### [2e119a3](https://github.com/vllm-project/vllm/commit/2e119a3e847cc88463aa600974832af1b2b85565)

- **作者**: JulienDarve
- **时间**: 2026-11-18T12:43:51Z
- **提交信息**: [Rust Frontend] Use the model's default temperature when a gRPC request omits it (#68253)

Signed-off-by: Julien Darve <jdarve@NVIDIA.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [123f1cb](https://github.com/vllm-project/vllm/commit/123f1cb71d4f28b00bbe2e96b349bcd8b345f160)

- **作者**: Tianyao Wu
- **时间**: 2026-11-18T12:41:42Z
- **提交信息**: [Frontend] Stream diarized_json transcriptions as segment events (#65779)

Signed-off-by: Tianyao Wu <rayroy31@gmail.com>
Signed-off-by: Anh Tu Do <anhtud@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Anh Tu Do <anhtud@nvidia.com>

### [3a1c6c4](https://github.com/vllm-project/vllm/commit/3a1c6c43df5eb5344a3f853c34fac93c274a372f)

- **作者**: Medhavin
- **时间**: 2026-11-18T12:39:13Z
- **提交信息**: [Rust Frontend] Support --override-generation-config (#65915)

Signed-off-by: Virri Praneeth Reddy <praneeth.v181@gmail.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [891778b](https://github.com/vllm-project/vllm/commit/891778ba3d206e9d381281f94a9331c367f21f4d)

- **作者**: Luis 🚀
- **时间**: 2026-11-18T12:34:14Z
- **提交信息**: [Perf][Frontend] Load chat `prompt_embeds` from the `base64` str not an encoded copy (#68236)

Signed-off-by: Luis Robaina <luis@protopia.ai>

### [4dbd382](https://github.com/vllm-project/vllm/commit/4dbd382be7e2f482fb117bbf59de006b4d2d8e11)

- **作者**: Bowen Wang
- **时间**: 2026-11-18T11:29:53Z
- **提交信息**: [Bugfix][Kimi-K3] Reduce the shared expert for MegaMoE without sequence parallelism (#68373)

Signed-off-by: Bowen Wang <bowen@inferact.ai>
Co-authored-by: Claude Fable 5.2 <noreply@anthropic.com>

### [f2d0d84](https://github.com/vllm-project/vllm/commit/f2d0d8418efc017cd5f6e4fd46dfb0b89874fb28)

- **作者**: waizuichougou
- **时间**: 2026-11-18T11:24:12Z
- **提交信息**: [Bugfix][KV Offload][P2P] Prevent repeated PD KV fetches after decoder preemption (#67497)

Signed-off-by: waizuichougou <2082431897@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e802354](https://github.com/vllm-project/vllm/commit/e802354272b5aedf268863efee15d5fbc186916d)

- **作者**: Đỗ Anh Tú
- **时间**: 2026-11-18T11:19:47Z
- **提交信息**: [Bugfix][Quantization] Honor activation scheme in MXFP8 linear selection (#65288)

Signed-off-by: Anh Tu Do <anhtud@nvidia.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Codex <noreply@openai.com>

### [3521784](https://github.com/vllm-project/vllm/commit/3521784d8c98b04d54947edbb3704005e36bfffb)

- **作者**: Tomasz Zielinski
- **时间**: 2026-11-18T11:05:17Z
- **提交信息**: [Bugfix][XPU] Forward num_splits to the XPU flash attention kernel (#58131)

Signed-off-by: tzielinski-habana <tomasz.zielinski@intel.com>
Co-authored-by: Claude Opus 5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [fd99b40](https://github.com/vllm-project/vllm/commit/fd99b402afea698d2e4752c5502d8eac9088765d)

- **作者**: Lantao Jin
- **时间**: 2026-11-18T10:47:39Z
- **提交信息**: [CI] Upgrade to pytest 9.2 and fix the tests that break on it (#67673)

Signed-off-by: Lantao Jin <ltjin@amazon.com>
Signed-off-by: Bugen Zhao <i@bugenzhao.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Bugen Zhao <i@bugenzhao.com>

### [075f526](https://github.com/vllm-project/vllm/commit/075f52626b8d1733cbeadf800cdea6f8ed08038c)

- **作者**: Maroon Ayoub
- **时间**: 2026-11-18T10:44:05Z
- **提交信息**: [Bugfix][NIXL] Report failed pulls per request with several KV cache groups (#61499)

Signed-off-by: Maroon Ayoub <mayoub@redhat.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [7c85560](https://github.com/vllm-project/vllm/commit/7c85560a26d2885771cdb3df2367cad736dd6bd6)

- **作者**: Tianyu Guo
- **时间**: 2026-11-18T10:39:35Z
- **提交信息**: [ROCm] Add AITER CK DASH attention for Unlimited-OCR-2 (#66031)

Signed-off-by: Tianyu Guo <guoty9@mail2.sysu.edu.cn>

### [81a8cb0](https://github.com/vllm-project/vllm/commit/81a8cb063e6247fe254d7caf7e98a6691d71022a)

- **作者**: bogdan-petkovic
- **时间**: 2026-11-18T09:46:42Z
- **提交信息**: [CI] Restore the default device after test_fc_layer_quant_config_usage (#68350)

Signed-off-by: bogdan-petkovic <bpetkovi@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b5b9f79](https://github.com/vllm-project/vllm/commit/b5b9f7982cc82a2925e6f83cbe2e9b39aaf7fb47)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T09:20:45Z
- **提交信息**: [ROCm][Test] Check the AITER delayed mHC pre against the residual it wrote (#68300)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [aaf5620](https://github.com/vllm-project/vllm/commit/aaf5620d0965be2908f7ee6a0f87dec86d6465cc)

- **作者**: Chauncey
- **时间**: 2026-11-18T09:12:58Z
- **提交信息**: [Perf] Optimize DeepSeek V4/V4.1 vision operations with Triton kernels (#68097)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>

### [bffbfcc](https://github.com/vllm-project/vllm/commit/bffbfccb7e0b8ce77e65e9a7b87489bf335ab747)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T08:57:00Z
- **提交信息**: [ROCm][CI] Measure process-local GPU memory in the Qwen3-VL leak test (#68342)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [0c80c3a](https://github.com/vllm-project/vllm/commit/0c80c3a6aa0201d1b4f71915f90c03fd64837cec)

- **作者**: Aaravos
- **时间**: 2026-11-18T08:26:05Z
- **提交信息**: [Perf][Frontend] Bound completed hypothesis histories in online beam search (#66841)

Signed-off-by: tgghzyh <430211065@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [df76396](https://github.com/vllm-project/vllm/commit/df763962fc61f8d0047e89aa39079efe0e70e678)

- **作者**: Itay Etelis
- **时间**: 2026-11-18T07:24:40Z
- **提交信息**: [KV Offload] Give each rank its own CPU region outside the replicated layout (#59547)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [626d9d7](https://github.com/vllm-project/vllm/commit/626d9d79fe2c4166cd15452d541768865795d228)

- **作者**: Marcel Yeonghyeon Ko
- **时间**: 2026-11-18T07:21:52Z
- **提交信息**: [Bugfix][KV Offload] Report FS-tier short writes as a likely full disk instead of EIO (#66278)

Signed-off-by: YeonghyeonKO <dk02315@gmail.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e975177](https://github.com/vllm-project/vllm/commit/e9751779031701d477085cbe204996c82434a945)

- **作者**: Nicolas Hug
- **时间**: 2026-11-18T06:43:32Z
- **提交信息**: [Multimodal] Add TorchCodec image decoding backend (#63369)

Signed-off-by: Nicolas Hug <contact@nicolas-hug.com>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [7643c43](https://github.com/vllm-project/vllm/commit/7643c43f5e2fb1deb63f3e1b34823ca696105cff)

- **作者**: Zheng Gong
- **时间**: 2026-11-18T06:40:40Z
- **提交信息**: [ROCm][Bugfix][DSv4.1] Build the gfx942 top-512 extension from a copy in its build directory (#67936)

Signed-off-by: Zheng Gong <zgong@amd.com>
Co-authored-by: Shanshan Shen <467638484@qq.com>

### [95be27a](https://github.com/vllm-project/vllm/commit/95be27ae635bd56b1a954ecc6697d2eee6eb2161)

- **作者**: Shanshan Shen
- **时间**: 2026-11-18T06:28:02Z
- **提交信息**: [ROCm][Perf][DSv4.1] Fuse the MXFP8 input quant of fused_wqa_wkv and the shared expert into their producers (#67906)

Signed-off-by: shen-shanshan <467638484@qq.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [e3036e8](https://github.com/vllm-project/vllm/commit/e3036e896604b8a976c9f616c389b97cca9e087c)

- **作者**: fanxingran
- **时间**: 2026-11-18T06:03:29Z
- **提交信息**: [ROCm][Perf] Muse Spark: finalize the token-sharded MoE reduction in one reduce-scatter (#63254)

Signed-off-by: fanxingran <xingran.fan@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [7c3a930](https://github.com/vllm-project/vllm/commit/7c3a9302f5ac2441ad199134129e973d22a46797)

- **作者**: majunqi
- **时间**: 2026-11-18T05:48:54Z
- **提交信息**: [Bugfix][Model] Avoid host synchronization in the Dots3Note vision tower (#66783)

Signed-off-by: majunqi <majq92@163.com>
Co-authored-by: DeepSeek V4.1 Flash <noreply@deepseek.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [a156bb0](https://github.com/vllm-project/vllm/commit/a156bb084381b04499aea80fdf1f0a5bc9eda202)

- **作者**: Aaron Hao
- **时间**: 2026-11-18T05:11:14Z
- **提交信息**: [Bugfix][gpt-oss] Split streamed MXFP4 experts in whole blocks across TP; keep the caller's w2_bias (#65353)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [5cba3d7](https://github.com/vllm-project/vllm/commit/5cba3d7b550359dd393bebc56a89b9190a7c8138)

- **作者**: Aaron Hao
- **时间**: 2026-11-18T05:10:48Z
- **提交信息**: [RL][Model Loader] Direct reload: check that an update loaded every parameter (#65799)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Signed-off-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [b197db7](https://github.com/vllm-project/vllm/commit/b197db7d95be327e3cb8c891c0a15b0832adc2ee)

- **作者**: Jared Wen
- **时间**: 2026-11-18T04:59:02Z
- **提交信息**: [Perf][KDA] Export Triton prefill checkpoints for Kimi-Linear (#68157)

Signed-off-by: Jared Wen <jaredwen@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [5e0855d](https://github.com/vllm-project/vllm/commit/5e0855d3059eef2a93cd1df390abb5a076ca53a7)

- **作者**: Yibo Liu
- **时间**: 2026-11-18T04:46:01Z
- **提交信息**: [Bugfix][Multimodal] Pixtral (HF): honor the processor's size override (#67904)

Signed-off-by: Yibo Liu <yibol9768@gmail.com>

### [06e7b4f](https://github.com/vllm-project/vllm/commit/06e7b4fc7233ea5f66943d25a418b6c120c88f63)

- **作者**: Drago1234
- **时间**: 2026-11-18T04:41:14Z
- **提交信息**: [Bugfix][EPLB][Hardware][Ascend] Set device_index for NPU in async EPLB worker (#66376)

Signed-off-by: drago1234 <32420036+drago1234@users.noreply.github.com>

### [c0323ee](https://github.com/vllm-project/vllm/commit/c0323ee0ec4b889a1f8d97893daeb71a54072e7d)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T04:40:53Z
- **提交信息**: [ROCm][Bugfix] Probe AITER mHC support when the op is built, not at import (#68027)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [51d9b9a](https://github.com/vllm-project/vllm/commit/51d9b9ab07f18797c5db0092671b20171a621728)

- **作者**: Jee Jee Li
- **时间**: 2026-11-18T04:22:38Z
- **提交信息**: [Recipe] Add HY4 Flash (#68295)

### [2ab8393](https://github.com/vllm-project/vllm/commit/2ab8393191d2d0489e14ba84b67799bd3ab2c079)

- **作者**: Divakar Verma
- **时间**: 2026-11-18T04:18:01Z
- **提交信息**: [CI][ROCm] float64 reference + specialized decode format primitives (T1 of #68016) (#67135)

Signed-off-by: Divakar Verma <divakar.verma@amd.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1895228](https://github.com/vllm-project/vllm/commit/1895228ed81191b4fa71762086f67fc387a7fa9e)

- **作者**: Shuojie
- **时间**: 2026-11-18T03:52:45Z
- **提交信息**: [CI][Test] Remove the failure mechanisms of two flaky tests (#66409)

Signed-off-by: Shuojie Wang <latioswang@gmail.com>
Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [d30c732](https://github.com/vllm-project/vllm/commit/d30c732cd1cfd279be437c02b5e85c5ea82f36d0)

- **作者**: Wei-Cheng (Wayne) Chiu
- **时间**: 2026-11-18T03:50:50Z
- **提交信息**: [Kernel][MiniMax-M3] Drop tl.make_block_ptr from the Hopper sparse prefill (#66099)

Signed-off-by: WEI CHENG CHIU <waynehacking8@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [83b2e39](https://github.com/vllm-project/vllm/commit/83b2e39440bd1b4e4241f39bf0f5458fda422e89)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-18T03:49:19Z
- **提交信息**: [CI] Add the CPU image's toolchain PPA without the Launchpad API (#67087)

Signed-off-by: khluu <khluu000@gmail.com>
Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [e1f91c4](https://github.com/vllm-project/vllm/commit/e1f91c4ec4fe30074e60f77bcf0861fb554f6bb0)

- **作者**: hhwxx
- **时间**: 2026-11-18T03:40:14Z
- **提交信息**: [Bugfix][Frontend] Encode special-token text as plain text in gpt-oss legacy tool-call headers (#65771)

Signed-off-by: Wenxuan Xu <wenxuan@elastix.ai>
Co-authored-by: Wenxuan Xu <wenxuan@elastix.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Chauncey <chaunceyjiang@gmail.com>

### [a7b75c9](https://github.com/vllm-project/vllm/commit/a7b75c977da92789278e6bcf818c888643459881)

- **作者**: Kevin H. Luu
- **时间**: 2026-11-18T03:15:19Z
- **提交信息**: [CI][XPU] Compare inactive default mm LoRA runs via top-k logprobs (#68266)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e23cf17](https://github.com/vllm-project/vllm/commit/e23cf178844e6ae9d73bb1135c083dc6da53f6b1)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T03:14:32Z
- **提交信息**: [ROCm][Quantization] Serve ModelOpt INT8_PB_WO on ROCm with an 8-bit Triton WNA16 kernel (#67302)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [bd455e1](https://github.com/vllm-project/vllm/commit/bd455e1f91af85dc029784da63aabd64e0f78840)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T03:13:43Z
- **提交信息**: [ROCm][DSv4.1] Share Engram host tables across DP ranks with HIP VMM (#65595)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [29caa16](https://github.com/vllm-project/vllm/commit/29caa168f50a1be1853e9fee2d05078249ed0821)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T03:12:51Z
- **提交信息**: [Bugfix][Ray] Keep the DP frontend's SIGTERM handler across ray.init() (#68091)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [24a03fd](https://github.com/vllm-project/vllm/commit/24a03fd9ec989aa7b5f37f67be9998e80e3b7b38)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T03:11:19Z
- **提交信息**: [ROCm][Bugfix] Refresh AITER env flags in forked processes (#68089)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [2c1fc9b](https://github.com/vllm-project/vllm/commit/2c1fc9b3d37551e106fd6991ca6a369436ec7bdb)

- **作者**: Wei Zhao
- **时间**: 2026-11-18T02:30:21Z
- **提交信息**: [CI][KV Connector] Wait for vLLM processes and GPU memory between NIXL PD runs (#67818)

Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [0c4fe70](https://github.com/vllm-project/vllm/commit/0c4fe70662363193189f2212ecd9d55d39d5349e)

- **作者**: Hokwang Choi
- **时间**: 2026-11-18T02:24:21Z
- **提交信息**: [Bugfix][LoRA] Count base requests in the specialized CUDA graph LoRA key (#67787)

Signed-off-by: Hokwang Choi <choi920330@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [1fd6c68](https://github.com/vllm-project/vllm/commit/1fd6c682359e8636396efaf359d08cc480514024)

- **作者**: zofia
- **时间**: 2026-11-18T02:22:15Z
- **提交信息**: [XPU] Remove VLLM_XPU_FORCE_N_CONTIG_WEIGHT (#67864)

Signed-off-by: Zhu, Zufang <zufang.zhu@intel.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [22e08e2](https://github.com/vllm-project/vllm/commit/22e08e286468357cc9c6755f6816ea7da440e0d5)

- **作者**: Thien Tran
- **时间**: 2026-11-18T02:17:01Z
- **提交信息**: [Perf][Qwen4Exp] Raster the fused HC up+gate mix tiles N-fastest (#68154)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [fd89c66](https://github.com/vllm-project/vllm/commit/fd89c6662c4e89f7a15712f0eb55d091885dd351)

- **作者**: Bo Pang
- **时间**: 2026-11-18T02:15:06Z
- **提交信息**: [Bugfix][Multimodal] Kimi-VL encoder CUDA graph: size max_seqlen in patches (#66679)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [bd3e00f](https://github.com/vllm-project/vllm/commit/bd3e00f0600c84c511119e4e7a1e52a12b0a2643)

- **作者**: Bo Pang
- **时间**: 2026-11-18T02:14:54Z
- **提交信息**: [Refactor][Multimodal] Share encoder CUDA graph code: Qwen2-VL-style mixin + default budget range (#66067)

Signed-off-by: Bo Pang <bopang314@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [fcf5ffa](https://github.com/vllm-project/vllm/commit/fcf5ffad73791f35fa33031e920991e3378318a3)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-11-18T02:07:06Z
- **提交信息**: [Bug][KVEvents]: Use effective block size in DCP full KV cache report (#50118)

Signed-off-by: jperezde <jperezde@redhat.com>
Signed-off-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Robert Shaw <robertgshaw2@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

### [f55dbdf](https://github.com/vllm-project/vllm/commit/f55dbdfb9d74577dacb66d1a8d025fe1d5055995)

- **作者**: swappy
- **时间**: 2026-11-18T01:35:49Z
- **提交信息**: [Bugfix][RL] Don't re-tie word embeddings on direct reload (#66487)

Signed-off-by: swappy <59965507+rycerzes@users.noreply.github.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Kevin H. Luu <khluu000@gmail.com>

### [5276760](https://github.com/vllm-project/vllm/commit/52767604d08f5d3a2a3367b46b74e419492cbe90)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-11-18T01:35:32Z
- **提交信息**: [Core][Mamba] Retain decode-crossed Mamba boundary states under sparse retention (#67053)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>
Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a291575](https://github.com/vllm-project/vllm/commit/a2915755bf1dcaf80623e36d079713bfb190c1e7)

- **作者**: Aaron Hao
- **时间**: 2026-11-18T00:46:18Z
- **提交信息**: [Direct reload] Flag padded params with fill_on_reload at construction (#67563)

Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [266b74b](https://github.com/vllm-project/vllm/commit/266b74b494a9bfb86d6a4f0a033f93b96c5d48a1)

- **作者**: Josh Schell
- **时间**: 2026-11-18T00:37:03Z
- **提交信息**: [CI][AMD] Run every AMD step when the ROCm image or AMD CI changes (#66682)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: vllm-agent <claw@inferact.ai>
Co-authored-by: Andreas Karatzas <akaratza@amd.com>

### [7cdde17](https://github.com/vllm-project/vllm/commit/7cdde1751524a563270adc5d07e386e77b8b5a0d)

- **作者**: Andreas Karatzas
- **时间**: 2026-11-18T00:35:16Z
- **提交信息**: [Bugfix][Ray] Keep EngineCore's SIGTERM handler across ray.init() (#68026)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [dc645a1](https://github.com/vllm-project/vllm/commit/dc645a166847542a1d3261d6d273b4cb9b4e3880)

- **作者**: Sheral Kumar
- **时间**: 2026-11-18T00:34:34Z
- **提交信息**: [ROCm][CI] Lock every render node for multi-GPU DPX jobs (#68256)

Signed-off-by: Sheral Kumar <shekumar@amd.com>
Co-authored-by: vllm-agent <claw@inferact.ai>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-11-19
**监控日期**: 2026-11-18
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7840
- **最后更新**: 2026-11-19T02:49:46Z

## 提交统计

- **昨日提交总数**: 26
- **提交者数量**: 21
- **主要提交者**: Xinpei Wang, y-null, Ziang Tang

## AI分析总结

# vllm-omni 昨日提交分析（第1/1批，共26条）

## 1. 主要更新类型

- **Bug修复**：占比最高（约10条），涵盖扩散模型、双工会话、图捕获、ROCm兼容性等
- **CI/Build 稳定性**：约7条，集中在CI测试加固与ROCm NIGHTLY质量门禁
- **功能/性能**：新增模型（Cosmos3-Nano）、性能融合（CosyVoice3 QKV）、双工批量感知等
- **文档与重构**：VoxCPM2并发调优文档、对齐vLLM 0.34并移除旧ModelRunner等

## 2. 关键变更点与项目方向的关系

- **对齐上游 vLLM**：移除ModelRunner V1、适配vLLM 0.34、恢复ROCm V2部署配置，体现项目紧跟vLLM核心演进，保证"omni模态服务"底座的一致性。
- **双工（duplex）会话可靠性**：多条提交针对MiniCPM双工会话超时、末场景答案截断恢复、PersonaPlex超3000帧窗口服务、Nemotron双工感知批量化——这与README强调的实时语音交互体验直接相关。
- **扩散（Diffusion）模态栈成熟化**：防止worker孤儿进程、MXFP8 E8M0尺度支持、图捕获时机修正、DiffusionTTSAdapter接入在线服务，说明扩散TTS/视频模态正从实验走向可服务化。
- **ROCm平台投入加大**：多条提交要求MI300 NIGHTLY性能基线成为阻断性检查，并准备BAGEL/双工资格认证，表明AMD GPU支持被提升到与CUDA同等的质量标准。

## 3. 对项目的影响与潜在意义

- **稳定性提升**：CI加固（CPU扩散测试文件锁、duplex超时稳定化、Wan I2V提示清理对齐）减少flaky，加速合并节奏。
- **多模态覆盖面扩大**：新增Cosmos3-Nano-Sim-Bimanual（双手操作仿真）拓展了项目"omni"边界到机器人操作场景。
- **服务性能**：QKV融合、批量双工感知、并发调优文档直接改善TTS与语音会话的吞吐和延迟，呼应"easy, fast, cheap"的定位。

## 4. 值得关注的技术点

- **图捕获时机问题**：Qwen3-Omni/TTS的Code2Wav图捕获需避开vLLM加载期分割限制，以及MiniCPM flow encoder需防循环GC干扰——CUDA图与Python GC的交互是分布式推理的隐蔽坑。
- **输入尾部重放（input-tail replay）**：用于恢复双工e2e中被截断的末场景回答，是双工流式推理的创新健壮性手段。
- **MXFP8 E8M0 在 DLO AllGather 中的支持**：低精度通信尺度格式在扩散模型分布式层的落地，值得量化精度跟踪。
- **ROCm 上 Qwen3-TTS 时间卷积需 ieee input_precision**：GPU后端数值精度差异的典型适配案例。
- **Codex/Claude 等AI协作署名**：多条提交由AI辅助完成，反映项目开发工作流的变化。

## 5. 对项目发展的影响

结合README"为所有人提供易用、快速、低成本的全模态模型服务"的目标，这批提交呈现三条主线：**(a)** 通过频繁对齐上游vLLM和修复边缘Bug来夯实服务底座的可靠性；**(b)** 持续打磨双工语音与扩散TTS的实时服务质量（延迟、截断恢复、并发），这正是全模态交互的核心卖点；**(c)** 将ROCm的NIGHTLY性能/精度提升为阻断性门禁，为AMD硬件上的生产级部署铺路。整体上，项目正从"功能可用"阶段迈向"多后端、多模态、可生产"的成熟期，同时通过新增仿真操作模型为未来的机器人全模态服务预留空间。

## 详细提交记录

### [08c3380](https://github.com/vllm-project/vllm-omni/commit/08c33802a9ec636261a0d8d87140feb36a5862fb)

- **作者**: Linze Shi
- **时间**: 2026-11-18T20:43:43Z
- **提交信息**: [CI/Build] Use file rendezvous in three CPU diffusion tests (#10625)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [b376774](https://github.com/vllm-project/vllm-omni/commit/b376774c18700ca2f85096d012d86d1a93875d7c)

- **作者**: Nick Cao
- **时间**: 2026-11-18T19:38:10Z
- **提交信息**: [Frontend] Support WAV streaming over the speech WebSocket (#10123)

Signed-off-by: Nick Cao <ncao@redhat.com>
Co-authored-by: Codex <noreply@openai.com>

### [aae3f38](https://github.com/vllm-project/vllm-omni/commit/aae3f386b8786aea7542d960c1a741d66698bf12)

- **作者**: lm10-arg
- **时间**: 2026-11-18T18:37:19Z
- **提交信息**: [CI/Build] Stabilize duplex session failure timeout (#10678)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>

### [1db21ca](https://github.com/vllm-project/vllm-omni/commit/1db21ca892dddf6c8bb3d4e66bb6077366da3426)

- **作者**: NATURE
- **时间**: 2026-11-18T18:22:59Z
- **提交信息**: [Bugfix][BAGEL] Align two-stage contexts with reference inference (#10634)

Signed-off-by: natureofnature <wzliu@connect.hku.hk>
Co-authored-by: Ding Zuhao <e1583181@u.nus.edu>

### [714c0c7](https://github.com/vllm-project/vllm-omni/commit/714c0c7991675c5bc5623f59a413a8545f4ae105)

- **作者**: Yunzenn
- **时间**: 2026-11-18T17:54:46Z
- **提交信息**: [Doc][VoxCPM2] Document concurrency tuning and streaming latency tradeoffs (#5071)

Signed-off-by: Yunzenn <209125778+Yunzenn@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [451addd](https://github.com/vllm-project/vllm-omni/commit/451adddf7bf6345be802a29f72264107c317c9b9)

- **作者**: dongbo910220
- **时间**: 2026-11-18T17:19:54Z
- **提交信息**: [Model] Fuse CosyVoice3 QKV projections for compiled cuDNN DiT (#10381)

Signed-off-by: dongbo910220 <1275604947@qq.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [d17f55f](https://github.com/vllm-project/vllm-omni/commit/d17f55f928a58ba3f6e32b468e8e1ed11dc70843)

- **作者**: lm10-arg
- **时间**: 2026-11-18T16:47:56Z
- **提交信息**: [Bugfix][ROCm] Restore V2 deploy profiles after vLLM 0.34 (#10630)

Signed-off-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Signed-off-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: lm10-arg <347490427+lm10-arg@users.noreply.github.com>
Co-authored-by: Andy Luo <43718156+andyluo7@users.noreply.github.com>

### [8eb8565](https://github.com/vllm-project/vllm-omni/commit/8eb8565079fd4e056befebb5d09202e2d1f00368)

- **作者**: Hang Zhengyang
- **时间**: 2026-11-18T16:43:21Z
- **提交信息**: [Bugfix] Capture Qwen3-Omni and Qwen3-TTS Code2Wav graphs after load, not under vLLM's load-time split limit (#10593)

Signed-off-by: Hang Zhengyang <hang.zhengyang1010@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [07dd3d0](https://github.com/vllm-project/vllm-omni/commit/07dd3d0cdea3325d8026a93485b60dfe3be6f29d)

- **作者**: y-null
- **时间**: 2026-11-18T12:57:32Z
- **提交信息**: [Bugfix] Recover truncated last-scene answers in MiniCPM duplex e2e via input-tail replay (#10546)

Signed-off-by: y_null <y_null@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [777dc7a](https://github.com/vllm-project/vllm-omni/commit/777dc7ad79fe9871d0117ce52228b3d86df3b994)

- **作者**: boatman
- **时间**: 2026-11-18T10:26:49Z
- **提交信息**: Make MRV2 the default for VoxCPM2 on CUDA (#9585)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [e7c7be4](https://github.com/vllm-project/vllm-omni/commit/e7c7be499da21d57a086f9e28c9e3145c21eaec0)

- **作者**: MaciejBalaNV
- **时间**: 2026-11-18T10:21:49Z
- **提交信息**: Add Cosmos3-Nano-Sim-Bimanual model (#6919)

Signed-off-by: Maciej Bala <mbala@nvidia.com>
Signed-off-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>
Co-authored-by: Yuliya Zhautouskaya <yzhautouskay@nvidia.com>

### [7f3b7d8](https://github.com/vllm-project/vllm-omni/commit/7f3b7d8342009117635980efc44d4c4470911036)

- **作者**: Sheng GAO
- **时间**: 2026-11-18T08:52:10Z
- **提交信息**: [CI/Build] Align Wan I2V reference prompt cleaning with Omni (#10509)

Signed-off-by: sheng <sheng.gao.dev@gmail.com>

### [bc7a0f4](https://github.com/vllm-project/vllm-omni/commit/bc7a0f487937cc16f2bc5dcfc3a48713cd3dd51e)

- **作者**: Sheng GAO
- **时间**: 2026-11-18T07:38:50Z
- **提交信息**: [Bugfix] Prevent diffusion worker orphans during startup (#10440)

Signed-off-by: Sheng GAO <sheng.gao.dev@gmail.com>
Signed-off-by: sheng <sheng.gao.dev@gmail.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [db2b78e](https://github.com/vllm-project/vllm-omni/commit/db2b78eb2ef49a93876243f374399f538f2b3b7b)

- **作者**: Dong1017
- **时间**: 2026-11-18T06:41:50Z
- **提交信息**: [Bugfix] Guard MiniCPM-o flow encoder graph capture against cyclic GC (#10581)

Signed-off-by: Dong1017 <55723162+Dong1017@users.noreply.github.com>
Signed-off-by: GUOGUO <xwdong1998@163.com>

### [709dc42](https://github.com/vllm-project/vllm-omni/commit/709dc427ef59b9a1a1e0b092efd0236d3f70f723)

- **作者**: Zhou Taichang
- **时间**: 2026-11-18T06:29:22Z
- **提交信息**: [Core] Align with vLLM 0.34.0 and remove ModelRunner V1 (#10365)

Signed-off-by: Codex <codex@openai.com>
Signed-off-by: Chendi Xue <chendi.xue@intel.com>
Co-authored-by: Codex <codex@openai.com>
Co-authored-by: Chendi Xue <chendi.xue@intel.com>

### [ca9398d](https://github.com/vllm-project/vllm-omni/commit/ca9398dc9f18b6536daa05fd1980e2e9d370ed4f)

- **作者**: boatman
- **时间**: 2026-11-18T03:39:24Z
- **提交信息**: [Refactor] Wire DiffusionTTSAdapter into diffusion-mode online serving (#8011)

Signed-off-by: boatman <109857087+sphinxkkkbc@users.noreply.github.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [51adb7b](https://github.com/vllm-project/vllm-omni/commit/51adb7b5457a49a6e9e87f0a5522ed8a1bdeaa57)

- **作者**: searlion
- **时间**: 2026-11-18T03:27:20Z
- **提交信息**: [Bugfix][Qwen3-TTS] Reject blank text sent through model_intermediate_buffer (#10554)

Signed-off-by: Lewis Won <lewis.won@gmail.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [09d6599](https://github.com/vllm-project/vllm-omni/commit/09d6599de1fceed6032421f75c89668bb43a3f1c)

- **作者**: Arifuzzaman Joy
- **时间**: 2026-11-18T02:41:47Z
- **提交信息**: [CI/Build] Add nightly CosyVoice3 cross-request voice check (#8689)

Signed-off-by: Arifuzzamanjoy <s1710374103@ru.ac.bd>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [0698abe](https://github.com/vllm-project/vllm-omni/commit/0698abe49253fdf51da9c584f06a65f75830c95d)

- **作者**: Xinpei Wang
- **时间**: 2026-11-18T02:15:33Z
- **提交信息**: [Model] Batch cache-aware Nemotron VoiceChat duplex perception (#8597)

Signed-off-by: Xinpei Wang <wangxinpei@tju.edu.cn>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [ad2153c](https://github.com/vllm-project/vllm-omni/commit/ad2153caac49d092aad68e9a89003339c591f2bd)

- **作者**: xiangrong zhong
- **时间**: 2026-11-18T01:35:59Z
- **提交信息**: [Misc] Read diffusion_attention_schedule directly from the config (#10375)

Signed-off-by: zhongc1211 <huixindaddy@yahoo.com>
Co-authored-by: Zhengyuan Su (苏政渊) <su.zhengyuan@u.nus.edu>

### [0f9420c](https://github.com/vllm-project/vllm-omni/commit/0f9420c1c12aedc11cd76cfcc2f2fa12232b0db0)

- **作者**: Yi Liu
- **时间**: 2026-11-18T01:27:52Z
- **提交信息**: [Bugfix][Diffusion] Support MXFP8 E8M0 scales in DLO AllGather (#10403)

Signed-off-by: yiliu30 <yi4.liu@intel.com>

### [16ad661](https://github.com/vllm-project/vllm-omni/commit/16ad661a496c6466b09e85860b4c8647bce0c7da)

- **作者**: hac17
- **时间**: 2026-11-18T01:06:20Z
- **提交信息**: [CI/Build][ROCm] Require MI300 NIGHTLY performance baselines (#10562)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: Claude Code <noreply@anthropic.com>

### [01d2dab](https://github.com/vllm-project/vllm-omni/commit/01d2dab677c2bc40a9749b50af8bb567b6808d4a)

- **作者**: menglcai
- **时间**: 2026-11-18T01:03:37Z
- **提交信息**: [Bugfix][ROCm] Use ieee input_precision in Qwen3-TTS time-major conv on ROCm (#10510)

Signed-off-by: menglcai <menglcai@amd.com>
Signed-off-by: Yueqian Lin <linyueqian@outlook.com>
Co-authored-by: Yueqian Lin <linyueqian@outlook.com>

### [d9f5502](https://github.com/vllm-project/vllm-omni/commit/d9f55027fd64d37e196ad48caa6380ec547441ea)

- **作者**: Ziang Tang
- **时间**: 2026-11-18T00:17:11Z
- **提交信息**: [Model][PersonaPlex] Serve duplex calls past the 3000-frame window (RFC #7389 W6) (#8783)

Signed-off-by: Ziang Tang <ztang2370@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [01eba2d](https://github.com/vllm-project/vllm-omni/commit/01eba2d7c053cbdd3f1c858eed32ff05430dcfb9)

- **作者**: hac17
- **时间**: 2026-11-18T00:16:41Z
- **提交信息**: [CI/Build][ROCm] Prepare BAGEL and duplex NIGHTLY qualification (#10561)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>

### [c4e36fb](https://github.com/vllm-project/vllm-omni/commit/c4e36fbc3bda361f77f81863aec6013d7c8584c5)

- **作者**: hac17
- **时间**: 2026-11-18T00:15:54Z
- **提交信息**: [CI/Build][ROCm] Promote NIGHTLY MiniMax-H3 accuracy to blocking (#10560)

Signed-off-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Signed-off-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>
Co-authored-by: hac17 <29197483+hacZ17@users.noreply.github.com>
Co-authored-by: andyluo7 <43718156+andyluo7@users.noreply.github.com>

---
