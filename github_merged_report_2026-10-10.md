# GitHub Stars 合并报告 - 2026-10-10

**合并日期**: 2026-10-11
**监控日期**: 2026-10-10
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


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2234
- **最后更新**: 2026-10-10T11:15:04Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: murphyy, Coach257, Avaya Aggarwal

## AI分析总结

## 1. 主要更新类型

本批次提交以 **Bug 修复为主（2 项）**，辅以 **1 项新功能开发**，集中在分布式训练正确性和多模态模型训练能力扩展上。

## 2. 关键变更点与项目方向的关系

- **Ulysses 序列并行（SP）梯度缩放修复**：修正 MiniMax H3 模型在 Ulysses 并行下梯度未按 SP 规模归一化的问题，确保分布式训练的数学等价性。这直接呼应 VeOmni "Model-Centric Distributed Recipe" 的核心定位——提供可扩展、结果可靠的分布式训练配方。
- **LTX-2.3 的 SP padding 与音视频交叉注意力修复**：解决了序列并行场景下的 padding 边界问题，以及音频与视频模态间交叉注意力的实现缺陷，强化了项目对视频-音频联合理想的支持。
- **H3 CFG 校准的 Ref2VA 训练功能**：引入带无分类器引导（CFG）校准的参考图到视频-音频（Ref2VA）生成训练流程，扩展了模型支持的任务形态。

## 3. 对项目的影响和潜在意义

- **训练正确性提升**：前两个修复防止了分布式训练中的静默错误（梯度错误、注意力失效），避免用户在扩展并行规模时得到次优或错误的模型结果，增强了社区对项目分布式配方的信任度。
- **多模态覆盖面拓宽**：Ref2VA 训练能力使 VeOmni 更贴合当前视频生成领域（参考引导生成）的前沿需求，提升了项目在实际应用场景中的可用性。
- **生态兼容性**：对 MiniMax H3、LTX-2.3 等具体模型的支持表明项目正持续完善"配方库"，降低用户复现和微调前沿多模态模型的门槛。

## 4. 值得关注的技术点

- **Ulysses 序列并行的梯度归一化细节**：分布式训练中，损失/梯度是否按并行度缩放是常见陷阱，修复此类问题体现了项目对 SP 实现严谨性的重视。
- **音视频跨模态交叉注意力**：在统一的多模态架构中，不同模态 token 间的注意力 mask 和维度对齐容易出错，此修复对多模态融合训练具有通用参考价值。
- **CFG 校准训练**：在训练阶段引入 CFG 校准是一种精细的生成质量优化手段，值得关注其是否会在后续扩展到更多模态组合。

## 5. 结合项目背景的综合影响

VeOmni 的目标是提供"以模型为中心的分布式训练配方库"，支撑任意模态模型的规模化训练。本批提交从两个维度推进这一目标：一是**夯实基础设施正确性**——分布式并行（Ulysses SP）的梯度与 padding 修复确保配方在规模化扩展时保持数值可靠；二是**丰富配方多样性**——Ref2VA 功能让配方库覆盖参考引导的视频-音频生成这一新兴方向。两者结合，既巩固了项目作为分布式训练基础设施的可靠性，又增强了其作为前沿多模态训练方案集合的前瞻性，有助于吸引需要生产级分布式训练和最新生成任务支持的研究者与工程师采用该项目。

## 详细提交记录

### [8791a71](https://github.com/ByteDance-Seed/VeOmni/commit/8791a71f2ee2a732453b44392375e6a06aa00324)

- **作者**: Coach257
- **时间**: 2026-10-10T11:14:59Z
- **提交信息**: [model, dist, agent] fix: scale MiniMax H3 Ulysses gradients by SP size (#1281)

### [c40e135](https://github.com/ByteDance-Seed/VeOmni/commit/c40e13582d0c825714feeb9d5c2a0210a04de012)

- **作者**: Avaya Aggarwal
- **时间**: 2026-10-10T11:09:20Z
- **提交信息**: [model, ci] fix: LTX-2.3 Ulysses SP padding and audio-video cross-attention (#1252)

### [d5e8f6e](https://github.com/ByteDance-Seed/VeOmni/commit/d5e8f6e2a6d881ea5a44eef65d052edc964137d3)

- **作者**: murphyy
- **时间**: 2026-10-10T11:05:57Z
- **提交信息**: [model] feat: add H3 CFG-calibrated Ref2VA training (#1258)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2893
- **最后更新**: 2026-10-10T12:14:08Z

## 提交统计

- **昨日提交总数**: 4
- **提交者数量**: 3
- **主要提交者**: Bilang ZHANG, Zhuguanyu Wu, Yang Yong (雍洋)

## AI分析总结

## LightX2V 仓库昨日提交分析

### 1. 主要更新类型

本次共 4 次提交，涉及**重构**、**Bug修复**、**功能新增**三大类型。其中重构 1 次（推理配置与示例脚本简化），Bug 修复 2 次（训练精度基线相关问题），功能新增 1 次（Qwen-Image-2.1 VAE 分块推理支持）。同时训练相关的两次提交还带来了新功能：CFG 蒸馏训练器、STE rollout for DMD、on-policy CFG 蒸馏等。

---

### 2. 关键变更点及其与项目方向的关系

**推理侧（提交 #1592、#1588）：**
- **配置与脚本简化**：对推理配置和示例脚本进行重构，降低使用门槛，与 LightX2V "轻量推理框架" 的定位高度一致，目标是让用户更快上手、更简洁地调用推理能力。
- **Qwen-Image-2.1 VAE 分块推理**：新增对该模型的 tile 推理支持，直接提升了高分辨率图像/视频生成时的显存利用率和推理可行性，是框架兼容性和实用性的重要扩展。

**训练侧（提交 #1589、#1591）：**
- **训练精度基线修复**：修复了生成器/伪分数的精度问题以及 checkpoint 保存问题，表明项目正在稳步构建训练能力的稳定性基础。
- **CFG 蒸馏 + DMD STE rollout + on-policy CFG 蒸馏**：这些新增训练策略（尤其是 DMD 直接蒸馏模型的 STE rollout 和 on-policy CFG 蒸馏）表明项目正从纯推理框架向"训练+推理"一体化方向扩展，致力于通过蒸馏手段进一步压缩和加速视频生成模型。

---

### 3. 对项目的影响和潜在影响

- **易用性提升**：配置简化将直接降低新用户入门成本，有助于社区采纳和推广。
- **生态扩展**：Qwen-Image-2.1 的支持意味着 LightX2V 的适用范围从视频生成扩展到图像生成领域，覆盖面更广。
- **技术壁垒加深**：训练侧的 CFG 蒸馏和 DMD 相关能力是当前视频/图像生成领域的前沿方向，这些能力的内化将使 LightX2V 不仅是一个推理工具，更成为一个完整的生成模型优化平台，有助于在学术界和工业界形成差异化竞争力。
- **稳定性增强**：精度和 checkpoint 的 bug 修复为后续更大规模的训练任务打下基础，降低了长期维护风险。

---

### 4. 值得关注的技术点

- **STE (Straight-Through Estimator) rollout for DMD**：在直接蒸馏模型中引入 STE rollout，这是一个相对前沿的技巧，有助于在离散化或不可导操作下实现梯度回传。
- **On-policy CFG 蒸馏**：将无分类器引导（CFG）蒸馏从 off-policy 转向 on-policy 策略，通常意味着生成质量和训练稳定性有望提升。
- **训练精度与 checkpoint 的 bug 修复**：精度问题（生成器/伪分数）和 checkpoint 问题往往容易被忽视但影响深远，及早修复体现了团队对工程质量的重视。
- **推理配置的多轮迭代**（v3 版本）：说明团队在持续打磨用户体验，配置简化是一个渐进优化过程。

---

### 5. 基于项目背景的综合影响评估

LightX2V 的核心目标是构建**轻量级视频生成推理框架**。本次提交展示了两条并行的发展路径：**推理侧**通过简化配置和扩展模型兼容性持续提升框架的实用性和易用性；**训练侧**通过引入 CFG 蒸馏、DMD 等先进蒸馏技术，为未来"训练出更轻量的视频生成模型"这一目标做准备。

这种"推理框架 + 训练工具链"的双轮驱动策略，使 LightX2V 有望成为视频生成领域从**模型训练到高效推理部署**的全链路解决方案。短期内，用户将获得更简洁的使用体验和更广的模型支持；中长期来看，训练能力的完善将使项目在蒸馏加速视频生成这一关键赛道上占据更有利位置，与纯推理框架形成显著差异。

## 详细提交记录

### [4fe984c](https://github.com/ModelTC/LightX2V/commit/4fe984c07b1610338e97f8c7a268dceef8fd9966)

- **作者**: Bilang ZHANG
- **时间**: 2026-10-10T12:14:02Z
- **提交信息**: refactor: simplify inference configs and example scripts(v3) (#1592)

### [1f83487](https://github.com/ModelTC/LightX2V/commit/1f834878ce043fe76f177bfb01240a9e6751badf)

- **作者**: Zhuguanyu Wu
- **时间**: 2026-10-10T11:46:29Z
- **提交信息**: Fix/training precision baseline (#1591)

- add STE rollout for DMD
- support on-policy cfg distill
- bug fixed for a checkpointing problem

### [6101bff](https://github.com/ModelTC/LightX2V/commit/6101bff10b96754fe6c8ef80c0c33c85a307e7d8)

- **作者**: Zhuguanyu Wu
- **时间**: 2026-10-10T10:52:00Z
- **提交信息**: Fix/training precision baseline (#1589)

- bug fixed for generator / fake score precision
- bug fixed for a checkpointing problem
- add cfg distill trainer

### [42f6e6f](https://github.com/ModelTC/LightX2V/commit/42f6e6f854ad740fdee99bea890af6a9ad975598)

- **作者**: Yang Yong (雍洋)
- **时间**: 2026-10-10T10:29:05Z
- **提交信息**: support qwen-image-2.1 vae tile infer (#1588)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2289
- **最后更新**: 2026-10-10T20:28:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6585
- **最后更新**: 2026-10-10T23:55:59Z

## 提交统计

- **昨日提交总数**: 9
- **提交者数量**: 2
- **主要提交者**: eigen, Adrian

## AI分析总结

# FlashInfer 昨日提交总结（9项）

## 1. 主要更新类型

- **性能优化（6项）**：`kimi_k3_fp8_projection` 第8轮、`cake_dsv4` H64 tile成员、`minimax_h3` 第6轮、`deepgemm` 动态chunk调度、`ssd_combined` 第4轮、多为生成内核的调度/数据搬运层面优化。
- **功能新增（2项）**：Kimi-K3 W4A8 MXFP4 MoE的TP8长prefill链路、Cake后端对Rubin (sm_107a) 的支持。
- **Bug修复（2项，有重叠）**：`all_gather_matmul` 的proxy fence修复、GDN的int32/graph capture修复。
- **测试优化（1项）**：RoPE测试参数矩阵剪枝。

## 2. 关键变更点与项目方向的关系

- **Rubin平台移植（#6238）**：五个Cake生成后端在Rubin R200 (212 SM) 上可分发并通过测试，同时保证sm_100a/sm_103a内核源码字节级不变——这是项目"一套IR导出多架构"策略的关键扩展，为Blackwell之外的新硬件铺路。
- **生成式内核的持续迭代文化**：多个提交（#6154、#6217、#6258、#6291）均为同一算子族的第N轮"round"更新，坚持**bit-exact**（输出逐位一致）前提下的调度级优化，并附带严格的A/B配对测量证据。这体现了项目对性能可追溯性和数值稳定性的极高要求。
- **内存模型正确性（#6254）**：在TMA（async proxy）读取跨GPU写入的scratch buffer前补上 `fence.proxy.async.global`，修复PTX内存模型下的可见性竞态——多GPU通信内核的典型隐蔽bug。
- **长上下文与MoE覆盖（#6154）**：Kimi-K3 MoE补全T≥8192的TP8长prefill链路，直接服务长上下文推理场景。

## 3. 对项目的影响

- 扩大硬件覆盖面（Rubin）和算子覆盖面（长prefill、sparse-MLA H64、paged MQA动态调度），巩固FlashInfer作为**高性能推理内核枢纽**的定位。
- 持续的bit-exact性能迭代（GB300上geomean ~1.02，B200 ~1.04）说明项目已进入成熟的"微调榨取"阶段。
- 内存模型修复降低了多GPU场景下罕见但致命的 `unspecified launch failure` 风险。

## 4. 值得关注的技术点

- **Cluster退出 rendezvous**（#6154）：在cluster内核结束时增加 `barrier.cluster` arrive/wait，避免CTA提前退出释放TMEM导致的竞态。
- **2-CTA swap-AB GEMM** 与 **raster-vote finalize** 等SM100/SM103特定调度形式的选择器机制。
- **动态chunk scheduler**（#6118）：用原子计数器替代静态均分，解决长上下文下SM空转5-10%的问题。
- **CUDA Graph可捕获提交**（#6291）：将kernel间gap从2.6-3.2µs压缩到0.2µs，对decode延迟敏感场景意义显著。
- **Pairwise测试剪枝**（#5416）：用 `parametrize_product` 在常规CI中做两两覆盖、`--full` 保留全量矩阵，是大型测试矩阵瘦身的范式。

## 5. 对项目发展的意义

README表明FlashInfer的定位是"高性能GPU推理内核"。本批提交显示项目正在两条主线上推进：**(a)** 通过Cake生成器体系实现"一次建模、多后端多架构导出"的内核生产流水线日趋成熟（Rubin移植即是证明）；**(b)** 对核心算子族进行系统性的、可验证的多轮性能打磨。整体上，FlashInfer正从Blackwell单代优化走向**跨代硬件的统一推理内核平台**，同时以bit-exact纪律和完整测量证据建立起工业级的性能回归信任基础，对其作为主流推理框架（如vLLM/SGLang）底层依赖的长期采用至关重要。

## 详细提交记录

### [34bb66e](https://github.com/flashinfer-ai/flashinfer/commit/34bb66e4d0b420b5a03c99b2b6a1c0831dfaa738)

- **作者**: eigen
- **时间**: 2026-10-10T23:25:06Z
- **提交信息**: feat(cake_fused_moe): add the Kimi-K3 W4A8 MXFP4 SiTU TP8 long-prefill mixed192 chain (T >= 8192) to the Cake-exported backends (cake, cake_cute) (#6154)

## Summary

Re-renders the two Cake-exported Kimi-K3 W4A8 MXFP4 SiTU routed-MoE
backends (`flashinfer/fused_moe/cake_mxfp4_situ_moe/` for
`backend="cake"` and `cake_cute_mxfp4_situ_moe/` for
`backend="cake_cute"`) from Cake revision
`70198066696fd423e3a022709d54948602260d33` by the exporter's single
render command, so both manifests pin the same producer revision
(previously `2cfe62d25b0`, #5783). Export + evidence only: no FlashInfer
runtime code outside the two generated packages changes,
`.pre-commit-config.yaml` is untouched.

What the re-render brings over #5783 (from the Cake side, same IR
lowered to both backends):

- **tp8 long-prefill chain (`mixed192`, T ≥ 8192)**: the six TP8 rank-0
rows with T ∈ {8192, 16384, 32768} × {uniform, hot-set} that #5783
refused by name now execute their traced chain (dense row-group
zero-fill GEMM1 pair, 192-row 2-CTA swap-AB GEMM1, blocked chunk-major
192-row window finalize at 8192 tokens, raster-vote dense finalize pair
from 16384). The plan runtime's dense GEMM2 builder takes the
`raster_along_m` / `swizzle` form arguments and the swap-AB helper
exposes `form_config` from the generated route records (no re-trace in
FlashInfer); the launch wrapper exposes the co-resident cluster bound
the 2-CTA swap-AB grids are sized from, and the finalize-form selector
tells the blocked chunk-major n192 2-CTA window finalize
(`sched_chunk_major`, launched at 8192 tokens) from its row-group-major
sibling.
- **Cluster exit rendezvous on every cluster-launched kernel** (both
backends): a cluster (1, 2) finalize could retire one CTA while its peer
was still arriving on its mbarrier (one `unspecified launch failure` in
~10 full contract runs); every cluster kernel now ends with
`barrier.cluster` arrive/wait before the TMEM dealloc.
- CuTe DSL backend emits the kernel-teardown PDL trigger
(`griddepcontrol.launch_dependents`) that the generated DSL kernels were
missing.
- Paired TMEM epilogue loads behind one `tcgen05.wait::ld` on the 2-CTA
N256 dense finalize (per-element arithmetic and store order unchanged).
- 192-row 2-CTA swap-AB GEMM1 (tp8 T ≥ 8192 chain): the scheduler
tile-record ring runs 4 deep instead of 8 (hand-written: 8); the pair
forms at most two live tiles, so the shallower ring frees smem for the
operand stages. Measured on an isolated B300 (CUPTI-paired, 6 passes ×
20 replays): −1.2 % / −2.2 % on the tp8 T=8192 uniform / hot-set rows,
flat elsewhere; data movement and arithmetic unchanged.
- **Per-item MMA N on the 192-row 2-CTA swap-AB pair forms** (SiTU
GEMM1, window finalize and its chunk-major sibling): every K-block MMA
is issued with the instruction N taken from the window's valid rows
(rounded up to the pair's 16-row granularity) instead of the static 192,
and the gather warps split the window's valid rows evenly between the
two CTAs (the `cta_group::2` MMA reads N/2 B columns from each CTA). The
padding columns of a partially filled window are no longer computed; the
per-element K reduction of every valid row is unchanged and no stored
element changes. Same-GPU A/B/A/B on an isolated B300 (3 passes × 20
CUPTI replays): tp8 T=8192 uniform / hot-set −2.4 % / −4.3 % (`cake`)
and −3.1 % / −5.4 % (`cake_cute`), T=16384 −1.7 % / −1.5 %; rows without
partially filled windows flat within the 2 % A/A band. Both backends
lower the runtime MMA extent (the CUDA C++ lowering and the CuTe DSL
block-scaled MMA primitive patch the instruction descriptor's N field).

- **Dense GEMM1 weight-stream cache policy on the tp8 T=32768 rows**
(`mixed192` chain, both backends): from 32768 tokens the dense GEMM1
pair (the (128, 256) base launch and the 2-CTA (256, 256) alternate over
the compacted wide lists) loads its MXFP4 weight and scale tiles without
the EVICT_FIRST weight-stream hint, so an expert's weight slab stays
L2-resident for the other CTAs streaming it; below 32768 the pair keeps
the hint (hint-off costs +2.6…+3.3 % on the 16384 rows, so the rule is
keyed on the token count — a plan constant the rendered plan carries).
The two hint-less modules are new registry forms with the same kernel
bodies (cache policy only); the plan runtime's dense GEMM1 builder
selects the module by the form's `weight_l2_hint` field. Six-pass
same-GPU A/B/A against the hand-written chain on an isolated B300 (6 ×
20 CUPTI replays): T=32768 uniform −3.7 % / −4.2 % (`cake` /
`cake_cute`), hot-set −1.6 % / −0.7 %, empty −3.1 % / −2.8 %, no row
slower; T=8192 / 16384 rows unchanged (same modules as the previous
render).

Numerics are unchanged from #5783 (same reduction orders, same
tolerances); in the v29 contract run on the pinned revision the per-row
max abs error against the FP64 gate oracle is 0.0142 at most for
`backend="cake"` (87 oracle rows), and 0.0114 at most for
`backend="cake_cute"` (87 oracle rows).

## Evidence (B300, sm_103a, whole-GPU isolated steps, CUPTI-paired
timing)

- Render identity: `verify --flashinfer --revision 70198066696` clean (0
differences) after `ship-apply`; 196 launcher modules verified (104 cake
+ 92 cake_cute).
- FlashInfer host tests: 58 passed, 58 skipped (both packages);
FlashInfer GPU tests (both packages, incl. the executable-path
gate-oracle rows of every chain): 98 passed, 18 skipped (5:52 on one
B300; the 18 skips are the hand-written-wrapper comparison rows absent
from this FlashInfer build).
- Cake contract `eval_contract_kimi_k3_mxfp4_situ_cute_dsl_moe` v29 on
the pinned revision (kernels identical to the producer revision's; the
receipts were produced on the Cake tree of the previous commit of the
same branch, whose compiled forms are IR-identical): `backend="cake"`
91/91 rows correct (0 N/A, incl. the 6 optional ep8 long-prefill rows),
51/51 paired benchmark rows at or above 1.0x trtllm-gen (geomean 1.2485,
isolated B300; 0 paired rows slower than the previous render by more
than 1 %; tp8 T=16384 uniform −2.5 %, T=32768 uniform −2.1 %, T=32768
hot-set −0.7 %, every other paired row within +0.4 %);
`backend="cake_cute"` 91/91 rows correct (0 N/A), 51/51 paired rows at
or above 1.0x (geomean 1.2454, same isolated B300, 0 paired rows slower
than the previous render by more than 1 %; tp8 T=32768 uniform −1.7 %,
every other paired row within +0.2 %).
- compute-sanitizer synccheck + memcheck over the registered launchers:
all 54 launchers registered at the previous render (both backends) clean
(114 summaries incl. the 2-CTA re-check, 0 errors; receipt
`cake-763-sanitizer-log-v1` verdict clean, sha256 7f4fb0c0…, kernels
identical to this revision's except the two added launchers), and the
two hint-less dense GEMM1 launchers added by this render clean under
both tools (0 errors) together with their e2e GPU slice. Every compiled
kernel form of this revision is IR-identical to the measured one of the
previous render except those two additions (65/65 and 37/37 form
identity checks).
- Tracker: #4254.

## Test plan

- [x] `verify` render identity on the shipped tree
- [x] `pytest tests/moe/test_cake_mxfp4_situ_moe*.py` (host + GPU) on
B300
- [ ] CI (`/bot run`)

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [709949b](https://github.com/flashinfer-ai/flashinfer/commit/709949b6ddb539695c49bc9869d64f99ba3cea3e)

- **作者**: eigen
- **时间**: 2026-10-10T22:22:09Z
- **提交信息**: feat(cake_kernel_rubin): Cake backends on Rubin (sm_107a / CC 10.7) — routing, BGMV MoE, concat-MLA-K, GDN decode/prefill, packed KDA T=1 (#6238)

Fork `yyihuang/flashinfer`, branch `feat/cake-sm107-backends` (base:
upstream `main` at bcfa6539db8, merged in 21399f404). Related: #5467
(reference only — this PR is independent of it); #6131 (merged: the
standalone GDN layout this PR adds Rubin records to).

## What this PR does

Makes the five Cake-generated backends dispatch and pass on Rubin R200
(CC 10.7, 212 SMs), fixes what the Rubin bring-up found, and gives the
BF16-state T=1 GDN decode route its own sm_107a band table with the
records it routes to. The four non-concat backends (DSv3 routing, BGMV,
GDN decode/prefill, packed KDA) make no sm_100a/sm_103a kernel-source
change — their generated CUDA and manifests for those architectures are
byte-identical (cubin-identity gate on a GDN-decode representative on
B200 and GB300 at every round, plus source-diff scope). The concat-MLA-K
backend is re-exported here (new content-addressed body + v5 manifest);
its output stays bitwise-identical to the previous body.

| commit | change |
|---|---|
| d330816fb | tests(gdn): the raw-ABI invalid-slot route expectation
follows the arch's active cluster count (`dvsplit =
2·num_seqs·num_o_heads ≤ active clusters`; on R200 192 ≤ 212 → dvsplit);
adds a 4-sequence case so every architecture covers full-DV |
| e01331562 | tests(kda): drop the `arch_blackwell` marker from the 7
packed KDA T=1 tests (the fixture's exact-CC gate stays) |
| 8cc0bc7c2 | tests: CUDA-graph capture/replay coverage for the Cake
concat-MLA-K and DSv3 routing backends |
| 3ed59e67a | perf(cake-gdn): convert int64 prefill metadata
(`cu_seqlens`, `checkpoint_cu_starts`) to int32 once per tensor instead
of per call |
| 960b8ae90 | fix(cake-gdn): keep the int32 copies out of graph capture
(capture always records the cast; graph-private pool owns the copy),
never cache `state_indices` (converted per call), `record_stream` on
cross-stream hits |
| 57f59816b | style: ruff 0.12.8 (the repo's pre-commit version)
format/lint for the touched tests |
| 8760c6a8f | perf(cake-gdn): prefill per-call on-device slot validation
becomes opt-in (`FLASHINFER_CAKE_GDN_VALIDATE_SLOTS=1`), the same
default the decode adapter already has |
| d7246a4e6 | perf(cake-kda): packed T=1 selector bands keyed on compute
capability — (10,0)/(10,3) tables unchanged, new (10,7) table, unknown
capabilities raise |
| 6a88e6af3 | tests(cake-gdn): order the graph-ownership test's side
stream after its inputs (a test-only race seen once on B200) |
| 21399f404 | merge upstream `main` bcfa6539db8 (brings #6131); the only
conflict was `csrc/gdn/cake/manifest.json` |
| ea01d14e9 | perf(cake-gdn): sm_107a band table for the BF16-state T=1
decode route (`CAKE_GDN_BF16_T1_ROUTE_ARCH_BANDS["sm_107a"]`,
`cake_gdn_bf16_t1_route`) + the 10 sm_107a-only standalone records it
routes to (vec8occ TILE_V=16 for (H, HV) ∈ {(16,32), (8,16), (4,8),
(8,32), (4,16), (2,8)}; vec8 TILE_V=32 for {(16,32), (8,16), (8,32),
(4,16)}) with their host shims; sm_107a listed on a record only where
the sm_107a table routes to it (the 12 TILE_V=64 records are therefore
not sm_107a) |
| cafa5512d | style: ruff-format wraps two lines of the sm_107a band
table / route helper in `flashinfer/jit/cake_gdn.py`;
`CAKE_KDA_PACKED_T1_ALIGNED_BANDS` is keyed on `tuple[int, ...]` so
`.get(tuple(compute_capability))` type-checks (mypy). Both are
AST-neutral: the module ASTs equal the gated tree's except for that one
annotation (pre-commit findings of the first CI run) |
| bd144dc51 | fix(cake-gdn): a cached int32 metadata copy reused from
another stream now waits (CUDA event recorded after the cast) before
`record_stream` (review finding); the int64-metadata test gains a
side-stream reuse case; six source comments lose an internal reference
(comment-only) |
| 80426f524 | tests(cake-gdn): the graph-ownership test orders its
side-stream restore after the eager baseline clones — a write-after-read
race in the test's own choreography that showed only when the GPU was
time-shared with another process (sporadic `output_state` mismatch with
kernel output and replay correct); see Validation |
| 8537b404e | tests(gdn): `test_prefill_state_indices.py` skips the
`cake_gdn` CP arm on SM107 — the SM107 admission had also admitted the
CP parameters, which the dispatcher rejects there (54 failures on the
bot's Rubin NVL72 shard); the non-CP Cake arms keep running |
| 7335245d29f | perf(cake-kda): the SM107 B19–B63 packed T=1 band moves
to `cpasync_tile64_register_pipeline_early_publish` — the tile-64
register pipeline with the output row published before the terminal
state write-back and the state stored with an L2 evict-last hint (what
the tile-128 register pipeline already does); new frozen body exported
by Cake's device-profile exporter (body-local `CUtensorMap` typedef, as
this binding's macro renames require); bitwise identical to the tile-64
register pipeline on every row of the band on R200 and 1–3 % faster
(band geomean 0.987 of its time, no row slower); SM100/SM103 bands and
bodies untouched |
| 55dba6260 | concat_mla_k: re-export the two-phase register-staged copy
(v5 manifest loader + wrapper; non-contiguous host binding that accepts
the contract's strided rows). Six 16-byte vectors staged in registers
before the first store; two 1-byte tokens or one 2-byte token per CTA as
two statically-rolled schedules behind one `element_bytes` branch.
Byte-exact copy semantics unchanged. |
| 0637aa96d82 | perf(cake-gdn): the SM107a BF16 verify rows (TP=2
H=8/HV=16 T=7/T=8 at B≤4, TP=4 H=4/HV=8 T=4) take
`gdn_decode_pretranspose_t4_bf16state_tile16_vpre` — the shipped tile16
body with every draft token's v values staged in shared memory before
the barrier and the token loop unrolled (bitwise-identical output;
`cake_gdn_bf16_verify_tile16_schedule(arch)`, SM100a/SM103a keep the
shipped records and cubins); three SM107a-only records, two device
sources, three shims; resolver test + CUDA-graph rows |
| 8a2f1ff1a | perf(cake-gdn): the SM107a BF16 multi-token rows on the
wide body (T ≥ 2 rows that resolve to `..._mtp_t4_bf16state_wide128`:
TP=2 H=8/HV=16 T=7 at B≥5, H=16/HV=32 T=7/T=4/T=2, H=16/HV=64
T=2/T=3/T=4 verify/update/checkpoint) take
`gdn_decode_pretranspose_mtp_t4_bf16state_wide128_vpre` — the shipped
wide body with every draft token's v staged in shared memory before the
barrier and the token loop unrolled (bitwise-identical output;
`cake_gdn_bf16_wide_schedule(arch, seq_len)`, T=1 band rows and
SM100a/SM103a keep the shipped records and cubins); eight SM107a-only
records, four device sources, eight shims; resolver test + CUDA-graph
rows |
| 3ed24c66a | fix(cake_concat_mla_k): annotate the two expected-manifest
dict constants as `dict[str, Any]` so the pre-commit mypy hook accepts
the manifest loader's lookups (no behavioural change) |
| 3e54ab8dc | refactor(cake_gdn): drop the eight SM107a wide `_vpre`
records ahead of their re-derivation — the exporter adds records and
never re-points an existing record name to a new kernel symbol, so the
re-derivation needs the layout without them (manifest 176 → 168 in this
commit only; dispatch for those rows falls back to the shipped wide
records in between) |
| 9a7aff5fc | perf(cake_gdn): the SM107a wide multi-token rows' body
issues the first row quad's four state loads before the q/k precompute
at tile 32 (one quad per group) and consumes them after the barrier —
the ordering `gdn_wide_vec_kernel` uses at tile_v = 32 — so their DRAM
latency overlaps the precompute; the eight records re-derived through
the exporter under the same names (four new device sources, eight host
shims, manifest back to 176); output bitwise-identical (digests equal on
11 A/B rows × 2 seeds × 2 runs); on CC 10.7 the wide32 rows get 0–2.6 %
faster than with the previous body (in-tree A/B paired with the CuTe
kernel, two seeds × two runs; seed 17, second run: H=16/HV=32 T=4 B=8
10.18 → 9.95 µs with the CuTe kernel at 9.15 µs, CuTe ÷ Cake 0.899 →
0.920; H=16/HV=32 T=2 B=4 5.86 → 5.73 µs with the CuTe kernel at 5.25
µs, 0.896 → 0.916; TP=2 T=7 B=5/B=7 and TP=1 T=7 B=1 +0.6…+1.0 %), so
the H=16/HV=32 T=2 / T=4 rows remain slower than the CuTe kernel (ratio
< 1; > 1 = Cake faster); the wide64 rows keep the previous schedule |
| 3c31b45e4 | perf(cake_gdn): SM107a routes the fp32-state MTP update
row (B=4, T=4, intermediate-state cache) to a parallel-producer schedule
`gdn_decode_pretranspose_mtp_t4_splitv8_pro` — one warp per draft token
in the producer phase, every independent global load of the token issued
before the first reduction; same bf16 words, bit-exact conversions and
per-token arithmetic order, so the output is bitwise identical to the
shipped `mtp_t4_splitv8` body that SM100a / SM103a keep; one new
SM107a-only manifest record (177 variants), the resolver overlay mirrors
the per-architecture table, route ids unchanged; on the public
`gdn_decode` path the row's exported record goes 12.99 → 11.30 / 11.36
µs vs 9.86 µs CuTe-DSL (full 51-row table at seeds 17 / 29 against the
9a7aff5fc table at the same seeds; 0.759 / 0.761 → 0.873 / 0.868 of
CuTe); the commit message's 12.4 / 12.2 → 10.7 / 10.5 µs vs 9.8 µs are
the Cake-tree launcher A/B that selected the body (0.794 / 0.805 → 0.919
/ 0.935) |

## Behaviour notes reviewers should know

- **Inference-mode in-place mutation contract (c436/37da).**
`cu_seqlens` / `checkpoint_cu_starts` passed as int64 are converted to
int32 once per tensor identity+version. Under `torch.inference_mode()`
an in-place `copy_()` does not bump the version counter, so mutating one
of these tensors in place and reusing it now yields wrong kernel
offsets, not just stale launch parameters. This extends the existing
immutability contract of these host-int metadata tensors;
`state_indices` is deliberately *not* cached (converted per call)
because callers do mutate it in place.
- **Graph capture.** During capture the cast is always recorded into the
graph (the graph-private pool owns the int32 copy; the eager cache is
neither read nor written), so cache eviction after capture cannot free
memory a replay reads. Covered by
`test_public_cake_gdn_prefill_int64_metadata_graph_owns_its_copy` and
the in-place-slot bitwise test.
- **Prefill validation default (05de4b1).** The per-call device-side
slot validation (`_cake_gdn_assert_state_slots`: 3 elementwise kernels +
a reduction + `_assert_async`) cost 41–45 µs of launch gaps per call on
the bf16 indexed-state rows; it is now opt-in like the decode adapter.
Tests enable it.
- **Packed KDA selector (d7246a4e6).**
`select_cake_kda_packed_t1_variant(batch, *, compute_capability,
state_aligned, aux_vec4_aligned)`; bands for (10,7): ≤18
`register_tile16`, ≤63 `cpasync_tile64_register_pipeline_early_publish`
(7335245d29f; was `cpasync_tile64_register_pipeline`, to which it is
bitwise identical), else `cpasync_tile128_register_pipeline`. Every
shipped variant has the same max-abs error vs the fp32 reference per
batch; switching between bitwise classes changes bits (fp32 accumulation
order), as the existing B200 table already does across its bands.
- **sm_107a BF16 T=1 decode bands (ea01d14e9).** Keyed on state heads =
batch × HV: ≤192 vec8occ/16 · ≤256 vec8/32 · ≤368 vec8occ/32 · ≤416
vec8occ/16 · ≤768 vec8/32 · ≤3072 vec8occ/32 · wide/128. Derived on R200
from a 111-row interleaved cold-L2 sweep of the 10 admitted (body,
TILE_V) instances (every instance checked against the shared route's
output per row; 88/111 rows bitwise-equal, max |Δ| 1.2e-4 from fp32
accumulation order across TILE_V, as the shared table already has across
its bands): 1.0012× of the per-row fastest instance (shared table
1.064×, max 1.268× at 1536 heads); confirmed at a second seed (1.0013×).
The sm_100a/sm_103a tables and records are unchanged. The 10 new records
are derived from same-body siblings (same device source; the
specialization set, variant name, module ident, shim namespace and grid
factor follow the exporter's rules — the derivation reproduces all 32
existing same-family records byte-for-byte); the Cake export protocol's
measured admission was not run for sm_107a (see "Known gaps").

## Validation

All runs on allocated cluster compute; FI tree pinned per run (`fi=` in
each step header).

| what | where | result |
|---|---|---|
| the nine Cake test files + ruff 0.12.8 | R200 (CC 10.7), FI ea01d14e9
(fitest13) | 0 failing files: routing 675 passed / 4740 skipped (all
`Invalid configuration` parametrizations), bgmv 82, bgmv-jit 171, concat
71, gdn decode gpu 84 / 2 skipped, gdn prefill gpu 27 / 1 skipped
(mixed-device test needs 2 GPUs), gdn decode 40, packed kda 31, kda jit
91; ruff check/format clean on the changed files |
| five-family Cake tests | B200 (sm_100a), FI ea01d14e9 (nr10) | 1656
passed / 0 failed / 4359 skipped |
| five-family Cake tests | GB300 (sm_103a), FI ea01d14e9 (gb4) | 1656
passed / 0 failed / 4359 skipped |
| five-family Cake tests at the merge commit 21399f404 | B200 (nr9) /
GB300 (gb3) | 1650 passed / 0 failed; GB300: one failure of
`test_public_cake_gdn_prefill_int64_metadata_graph_owns_its_copy`
(`output_state` differed after replay, `output` equal) root-caused to a
write-after-read race in the test's own stream choreography (the eager
baseline clones on the default stream vs the side-stream restore of the
same buffers were unordered), reproduced under deliberate GPU contention
and fixed in 80426f524 — rows below |
| compute-sanitizer synccheck + memcheck, every Cake kernel of the five
families via the public wrappers | R200 | 0 errors (the only barrier
reports come from FI's own CuTe `chunk_gated_delta_rule_sm100` prefill
kernel, which is the baseline, not changed here); the re-routed BF16 T=1
row re-sanitized after the band table (0 errors); the 10 sm_107a-only
records each exercised through the public wrapper under synccheck +
memcheck (0 errors) |
| CUDA graph capture/replay | R200 + B200 + GB300 |
`*_is_cuda_graph_safe` + graph-ownership tests pass |
| sm_100a / sm_103a generated CUDA and cubins vs base | B200 + GB300
(cubin identity gate, every round) | IDENTICAL_CUBIN |
| pre-commit tools on the two modules touched by cafa5512d (ruff 0.12.8
check + format, mypy 1.17.1 with the repo config) | pinned tools, no GPU
| clean; the GPU gates above ran on the tree of ea01d14e9, which
cafa5512d changes only by formatting and one annotation (identical ASTs
otherwise) |
| re-gates at bd144dc51 (host-wrapper change in `_cake_gdn_i32`): the
nine Cake test files on R200, the five-family tests + cubin identity +
Cake e2e on B200 and GB300 | R200 (fitest14) / B200 (regate1) / GB300
(regate1 + the prefill file ×4) | R200 nine files 0 failing, ruff clean;
GB300 1656 passed / 0 failed / 4359 skipped, Cake e2e 283 / 31, cubin
identity, prefill file 4/4; B200 cubin identity, Cake e2e 313 / 1, FI
1655 passed / 1 failed — the graph-ownership test again (next rows) |
| the graph-ownership test under deliberate GPU contention (a second
process looping the Cake e2e suite on the same GPU) at bd144dc51 | B200
/ GB300 | fails 19/44 and 58/89 runs; in every failure the replayed
`output_state` is within 4.9e-4 of the fp32 reference while the eager
baseline equals the initial state: the baseline clones (default stream)
and the side-stream restore of the same buffers were unordered (only
visible under time-slicing) |
| the same contention probe at 80426f524 | B200 / GB300 | the test
passes 44/44 (B200) and 91/91 (GB300); the pre-fix-choreography control
probe alternating with it still raced once on GB300 (1/91), with the
same signature |
| re-gates at 80426f524: the nine Cake test files + ruff 0.12.8 on R200,
the five-family tests + cubin identity + Cake e2e on B200 and GB300 |
R200 (fitest15) / B200 (regate2) / GB300 (regate2) | R200: nine files 0
failing, ruff clean on 23 files; B200: cubin identity, Cake e2e 313
passed / 1 skipped, 1656 passed / 0 failed / 4359 skipped (twice);
GB300: cubin identity, Cake e2e 283 passed / 31 skipped, 1656 passed / 0
failed / 4359 skipped |
| the bot's Rubin NVL72 shard at 80426f524, then the PR-diff-derived FI
test files (the nine Cake files + every test file this PR changes) at
8537b404e | VR NVL72 CI / R200 (cpfix1) | CI: 54 `cake_gdn` CP nodes of
`test_prefill_state_indices.py` raised on SM107 (fixed by 8537b404e);
the remaining 26 failed nodes are cuDNN-KDA, pack-contract,
prims_ts/CuTe-DSL, import-isolation and trace tests this PR does not
touch; the follow-up bot pipeline skipped the Rubin shards (its plan job
died in 50 s). cpfix1: the nine family files 0 failing (fitest15
tallies), ruff 0.12.8 check/format clean on the 23 changed files;
PR-diff-derived files all green — `test_prefill_state_indices.py` 121
passed / 54 skipped (the 54 skips are exactly the CP nodes that failed
in CI, reason `Cake GDN CP prefill is not provided on SM107`),
`test_cake_gdn_decode_public_forwarding.py` 55 passed,
`test_flash_kda_packed_t1_jit.py` 22 passed,
`test_dsv3_fused_routing_backend_selection.py` 49 passed |
| re-gates at 7335245d29f (new packed-KDA variant + SM107 band): the
nine Cake test files + ruff 0.12.8 on R200; five-family tests + cubin
identity + Cake e2e on B200 and GB300 | R200 (fitest16, ruff16) / B200
(k7regate) / GB300 (k7regate) | R200: nine files 0 failing (kda jit 93 =
91 + the two new-variant parametrizations), ruff check + format clean;
B200: cubin identity IDENTICAL_CUBIN, 1658 passed / 0 failed / 4359
skipped, Cake e2e 314 passed / 1 skipped; GB300: IDENTICAL_CUBIN, 1658 /
0 / 4359, Cake e2e 284 passed / 31 skipped |
| the new body under compute-sanitizer synccheck + memcheck (forced onto
the variant through Cake's `cpasync_schedule` validation hook, B32,
aligned state) | R200 | 0 errors |
| concat re-export: loader resolves the v5 manifest, `test_concat_mla` +
sanitizer, export drift | R200, FI 55dba6260 | `test_concat_mla` 71
passed / 0 failed; synccheck + memcheck 0 errors; fresh render
byte-for-byte vs the checkout (0 differences) |
| re-gates at FI 55dba6260 (concat re-export): five-family tests + cubin
identity + Cake e2e | B200 (sm_100a) / GB300 (sm_103a) | 1658 passed / 0
failed / 4359 skipped each; IDENTICAL_CUBIN (concat is the only changed
TU); Cake e2e 314 passed / 1 skipped (B200), 284 passed / 31 skipped
(GB300) |
| re-gates at 0637aa96d82 (SM107a `tile16_vpre` verify body): the nine
Cake test files on R200; compute-sanitizer synccheck + memcheck over the
three new records through the public `gdn_decode` path;
sm_90a/sm_100a/sm_103a cubin identity vs base; the five-family tests +
cubin identity + Cake e2e on B200 and GB300 | R200 (r15fit, r15san,
r15bwid) / B200 (r15bw) / GB300 (r15bw) | R200 nine files 0 failing (gdn
decode gpu 87 / 2 skipped, gdn decode 43 — the new resolver and
CUDA-graph rows included); synccheck 0 / memcheck 0 (4/4 rows); 44/44
IDENTICAL_CUBIN; B200 and GB300 `all_pass`: IDENTICAL_CUBIN, FI 1664
passed / 0 failed / 4359 skipped, Cake e2e 314 / 1 (B200), 284 / 31
(GB300) |
| re-gates at 8a2f1ff1a / 3ed24c66a (SM107a `wide128_vpre` wide body;
mypy annotation): the nine Cake test files on R200; compute-sanitizer
synccheck + memcheck over all eight new records through the public
`gdn_decode` path; sm_90a/sm_100a/sm_103a cubin identity vs base; the
pinned pre-commit tools (ruff 0.12.8, mypy 1.17.1) over the PR's files;
the five-family tests + cubin identity + Cake e2e on B200 and GB300 |
R200 (r16fit, r16san2, r16bwid, r16lint) / B200 (r16bw) / GB300 (r16bw)
| R200 nine files 0 failing (gdn decode gpu 89 / 2 skipped, gdn decode
46 — the new resolver and CUDA-graph rows included); synccheck 0 /
memcheck 0 (8/8 rows); 44/44 IDENTICAL_CUBIN; ruff / mypy clean on the
PR's files; B200 and GB300 `all_pass`: IDENTICAL_CUBIN, FI 1669 passed /
0 failed / 4359 skipped, Cake e2e 314 / 1 (B200), 284 / 31 (GB300) |
| re-gates at 9a7aff5fc (SM107a wide body: first state quad before the
precompute at tile 32): Cake e2e `-k gdn_decode` at the matching Cake
tree; the nine Cake test files on R200; compute-sanitizer synccheck +
memcheck over the eight re-derived records through the public
`gdn_decode` path; sm_90a/sm_100a/sm_103a cubin identity vs base;
public-path route sweep of the eight wide rows vs CuTe at two seeds |
R200 (r16be2e2, r16bfit2, r16bsan2, r16bbwid3, r16brs17b/r16brs29b) |
Cake e2e 83 passed / 0 failed; nine files 0 failing (gdn decode gpu 89 /
2 skipped, gdn decode 46 — the resolver and CUDA-graph rows included);
synccheck 0 / memcheck 0 (8/8 rows, each resolving to its re-derived
`_vpre` record); 44/44 pairs IDENTICAL_CUBIN (sm_90a / sm_100a / sm_103a
vs base, the same 44-pair set as the 8a2f1ff1a re-gate); route sweep: 8
rows, 0 errors, default route = the re-derived `_vpre` records,
bitwise-equal to the forced shipped wide record on every row; vs CuTe
(s17 / s29) HV32 T4 B8 0.906 / 0.926 (R16 0.895 / 0.912), HV32 T2 B4
0.880 / 0.905 (0.876 / 0.895), TP2 T7 B5 1.038 / 1.054 (unchanged), TP1
T7 B1 1.060 / 1.083 (1.074 / 1.097, within run-to-run noise), the four
HV64 rows 0.82–0.90 unchanged. Blackwell: the five-family chain (cubin
identity vs base + FI five families + Cake e2e) at the matching Cake
tree, B200 (sm_100a) / GB300 (sm_103a) both all_pass — IDENTICAL_CUBIN,
FI 1669 passed / 0 failed / 4359 skipped, Cake e2e 314 passed / 1
skipped and 284 passed / 31 skipped (the same counts as the 8a2f1ff1a
re-gate). Full 51-row table at two seeds: 0.980 / 0.978, 18/42 / 18/42,
0 flips (table row below) |
| re-gates at 3c31b45e4 (SM107a fp32-state MTP parallel-producer body):
Cake e2e `-k 'gdn_decode and not bake_'` then `-k gdn_decode` at the
matching Cake trees; the nine Cake test files on R200; compute-sanitizer
synccheck + memcheck over the new record through the public `gdn_decode`
path; sm_90a/sm_100a/sm_103a cubin identity vs base; full 51-row decode
table at two seeds | R200 (two e2e runs, nine-file run, sanitizer run,
cubin-identity run, two full-table runs) | Cake e2e 83 passed / 0
failed, then 84 / 0 with the twin's own test entry; nine files 0 failing
(gdn decode gpu 89 / 2 skipped, gdn decode 49 — the three
per-architecture fp32 resolver rows included); synccheck 0 / memcheck 0
(1/1 row, resolving to the `_pro` record); 44/44 pairs IDENTICAL_CUBIN
(sm_90a / sm_100a / sm_103a vs base, the same 44-pair set as the
9a7aff5fc re-gate). Blackwell: the five-family chain (cubin identity vs
base + FI five families + Cake e2e) at the matching Cake tree, B200
(sm_100a) / GB300 (sm_103a) both all_pass — IDENTICAL_CUBIN, FI 1672
passed / 0 failed / 4359 skipped (+3 vs the 9a7aff5fc re-gate = the
three per-architecture fp32 resolver rows), Cake e2e 314 passed / 2
skipped and 284 passed / 32 skipped (one more skip per SKU than the
9a7aff5fc re-gate: the SM107a-only test entry of the new body). Full
51-row table at two seeds: 0.9904 / 0.9854, 19/42 / 18/42, one flip
between seeds, the parity row `bf16_sglang_qwen_tp2_verify_t7_b7` 1.014
/ 0.997 (table row below) |

## Performance on R200 (interleaved cold-L2 CUPTI, 3 counterbalanced
groups, seeds 17 and 29; speedup = fastest non-Cake FlashInfer backend
of the same public function / Cake)

| family | rows | geomean(min speedup) | rows faster than every baseline
|
|---|---|---|---|
| DSv3 fused routing | 37 | 1.536 | 37/37 |
| BGMV MoE | 19 | 2.771 | 19/19 |
| concat-MLA-K | 21 | 1.876 | 21/21 |
| GDN prefill (vs auto + non-CP) | 145 | 1.046 / 1.045 | 108/145 /
106/145 (vs non-CP alone: 145/145 and 143/145; the 37 losses are the CP
route at 16k–64k tokens, which Cake does not provide on sm_107a) |
| GDN decode (shipped Blackwell manifest, before ea01d14e9) | 42 | 0.888
/ 0.887 | 7/42 / 7/42 |
| GDN decode (with the sm_107a-only T=1 records, ea01d14e9) | 42 | 0.890
/ 0.897 | 8/42 / 8/42 (0 flips between seeds; vs the shipped manifest
exactly one row changes verdict: `bf16_packed_page_t1` 5.184 → 3.328 µs
vs FI 3.808 µs = 0.735 → 1.144; the FI-less
`bf16_sglang_qwen_tp4_decode_t1` row 3.777 → 2.752 µs; the other 34
losses are T ≥ 2 rows) |
| GDN decode (with the SM107a `tile16_vpre` verify body, 0637aa96d82) |
42 | 0.939 / 0.943 | 13/42 / 14/42 (the five tile16 verify rows with an
FI arm flip to wins — on the public path TP=2 T=7 B1 1.254 / 1.280, B2
1.134 / 1.161, B3 1.149 / 1.164, B4 1.031 / 1.044, T=8 B1 1.286 / 1.299,
bitwise-identical to the shipped body; one row flips between seeds at
parity, `tp4_verify_t4_b5_contiguous` 0.988 / 1.018; the 13 remaining
losses at 0.74–0.88 are the wide32 / wide64 / fp32-MTP T ≥ 2 rows) |
| GDN decode (with the SM107a `wide128_vpre` wide body as well,
8a2f1ff1a) | 42 | 0.969 / 0.974 | 17/42 / 18/42 (TP=2 T=7 B5 / B6 / B8
and TP=1 T=7 B1 flip to wins at 1.038–1.079 — on the public path TP=2
T=7 B5 1.038 / 1.054 and TP=1 T=7 B1 1.074 / 1.097, bitwise-identical to
the shipped wide body, which the new body beats by 1.27–1.35× on the T=7
rows and 1–8 % elsewhere; B7 0.980 / 0.990; the only flip between seeds
is `tp4_verify_t4_b5_contiguous` 0.994 / 1.012; the remaining losses are
the H=16/HV=64 packed rows and the H=16/HV=32 T=2 / T=4 rows at
0.82–0.92 and the two fp32-state MTP rows at 0.75–0.89; with 9a7aff5fc
the wide32 rows gain 0–2.6 % over the 8a2f1ff1a body in the in-tree A/B
at two seeds, bitwise-identical; on the public-path sweep the wide32 T2
/ T4 rows gain +0.5…+1.5 % (HV32 T4 B8 0.906 / 0.926, HV32 T2 B4 0.880 /
0.905), the T7 rows are unchanged within run-to-run spread (TP2 T7 B5
1.038 / 1.054, TP1 T7 B1 1.060 / 1.083 vs 1.074 / 1.097) and the HV64
rows do not move; the full table at 9a7aff5fc is the next row) |
| GDN decode (with the wide32 prologue reorder of the wide body,
9a7aff5fc) | 42 | 0.980 / 0.978 | 18/42 / 18/42 (0 flips between seeds,
median |drift| 0.30 %; against the 8a2f1ff1a table at the same seeds the
two H=16/HV=32 wide32 rows gain 1–3 % in Cake time — T=2 B=4 0.890 /
0.894 → 0.915 / 0.910, T=4 B=8 0.913 / 0.918 → 0.952 / 0.949 — the T=7 /
T=8 wins read 1.051–1.320, TP=2 T=7 B7 0.997 / 0.997, and the H=16/HV=64
packed rows (0.815–0.909) and the two fp32-state MTP rows (0.759–0.887)
are unchanged) |
| GDN decode (with the SM107a fp32-state MTP parallel-producer body,
3c31b45e4) | 42 | 0.9904 / 0.9854 | 19/42 / 18/42 (one flip between
seeds, the parity row `bf16_sglang_qwen_tp2_verify_t7_b7` 1.014 / 0.997;
median |drift| 0.63 %, max 1.51 % (table footer; the stability footer's
median reads 0.60 %); against the 9a7aff5fc table at the same seeds the
promoted fp32-MTP row `fp32mtp_b4_t4_update_cache` moves 12.99 → 11.30 /
12.99 → 11.36 µs (−13.1 % / −12.6 %; 0.759 → 0.873 / 0.761 → 0.868 of
CuTe on the public path; the in-tree launcher A/B reads 0.919 / 0.935,
the public path measuring 0.61 / 0.85 µs more on this row) and every
other FI-arm row stays within −1.8 … +0.5 % (the other 20 multi-token
rows within −1.7 … +0.4 %); Blackwell cubins identical, see the re-gate
row above) |
| packed KDA T=1 | 11 | 1.0574 / 1.0591 (bands of d7246a4e6; with
7335245d29f the B19–B63 band body is 1–3 % faster again: B24 0.928 →
0.957, B31 0.977 → 0.983, B32 0.964 → 0.975 of the CuTe kernel's time;
the 8 Cake wins are unchanged) | 8/11 (B24/B31/B32 trail the CuTe kernel
by 1.6–3.4 %; its B24–37 config has the same geometry — tile 64, 2 rows
per thread, 128 threads, 4-stage cp.async ring. Knock-out attribution on
the R200 (timing-only bodies with the state store / state loads /
arithmetic / prologue removed one at a time, occupancy-matched, two
seeds, 13 batches): the kernel's copy-through structure runs within
−8…+4 % of the measured d2d copy floor from B16 up, the remaining 16–22
% at B ≤ 64 is exposed non-copy work — prologue (q/k/gate/beta loads,
reductions, rsqrt/sigmoid, shuffles) 10–12 % and update
arithmetic/output 5–8 % at B24–B36 — while the state store is hidden and
loads are the dominant data path; CuTe exposes 0.1–0.2 µs less of the
same work on the same geometry. Issuing the prologue loads ahead of the
state prefetch (hoisted-load probe bodies, bitwise-identical output)
does not recover it: where the order really changes (the register
tile-16 band) the kernel is 11–20 % slower, on the cp.async bands the
compiler already issues the bulk stream first and a volatile-pinned
order is slower still; the exposed part is the prologue's dependent
chain past the first chunk's arrival, reducible only by a
reduction-structure change that the bitwise contract excludes. The CuTe
tile-64 kernel's SASS (dumped through the DSL's keep/dump options) has
808 instructions vs this body's 800 with the same load/store-stream and
FFMA2 skeleton and fewer scalar STG/FFMA/FADD, so the 1.6–3.4 % is a
schedule difference of the same work, not an instruction-count one.) |

## Known gaps (not fixed here)

- The Cake GDN export protocol (`tools/export-generated-programs run`:
measured admission of every row per architecture with attested receipts)
was not executed for sm_107a, so none of the 22 sm_107a-only records is
exporter-attested: the 10 T=1 records are hand-derived from its
naming/shim rules and the 12 later records (3 tile16 `_vpre`, 8 wide128
`_vpre`, 1 splitv8 `_pro`) are rendered through the exporter's own
discovery / render / integrate path for exactly those rows; all are
validated by the resolver tests, the e2e slice and the R200 A/B above.
Running the protocol for sm_107a is the follow-up that makes them
exporter-attested.
- GDN decode rows with T ≥ 2 on Rubin that run the wide (TILE_V_WIDE
32/64) or fp32-state MTP bodies: `wide128_vpre` (8a2f1ff1a) makes every
wide row faster than before (bitwise-identical), and TP=2 T=7 B=5 / B=6
/ B=8 and TP=1 T=7 B=1 now beat the CuTe baseline, but the H=16/HV=64
packed rows and the H=16/HV=32 T=2 / T=4 rows stay below it — with
9a7aff5fc the H=16/HV=64 packed rows read 0.82–0.90 on the public path
and 0.815–0.909 in the full table, the H=16/HV=32 T=2 / T=4 rows
0.88–0.93 on the public path and 0.910–0.952 in the full table — and
TP=2 T=7 B=7 reads 0.997 / 0.997 in that table; the fp32-state MTP rows
are unchanged (0.759–0.887). A tile-width study of the wide body
(TILE_V_WIDE 32 / 64 / 128 on the same rows, two seeds) found no width
that helps — the shipped band is within ±4 % of the best width on every
row — and a schedule study of the same rows against the CuTe baseline
(`gdn_wide_vec_kernel`, which shares the wide body's design) tested,
each bitwise-identical at two seeds, a rolled token loop, the first
state quad and the v window issued before the precompute (as f32 or as
packed words), that hoist at every tile width and a 64-register launch
bound: exactly one is a uniform gain — the first state quad before the
precompute at tile 32 (9a7aff5fc, +0…+2.6 % on the wide32 rows) — and
the rest lose or trade rows. The remaining 0.82–0.93 on these rows
(public path; 0.85–0.93 in the in-tree A/B) is the prologue's exposed
DRAM round trips (a T-sweep puts the whole gap in the per-launch
intercept: Cake's per-token slope is ≈ 25 % lower than CuTe's) under a
register budget the body already uses fully (64–80 registers vs the CuTe
kernel's 63–76); closing it needs a body with fewer live values per lane
through the prologue — a new kernel rather than a schedule knob.
- The CP prefill route is not provided on sm_107a (precision-neutral
Cake CP admission is a separate decision).

cc @Vinnie6167 (Vincent, author of #5467) — this is the independent
Rubin enablement that #5467 drafted; the two can be reconciled once
#5467 is rebased.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added support for NVIDIA Rubin R200 (SM107a) across selected GDN, KDA,
MoE, and MLA operations, including architecture-specific kernel
selection.
* Added SM107a support for additional BF16 GDN decode configurations.
Some architecture-specific features require CUDA 13.0 or newer.
* **Performance and Compatibility**
* Improved GDN prefill metadata handling to reuse conversions during
regular execution while preserving support for CUDA Graph capture.
  * Extended fused MoE routing to support SM107a devices.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1f28b95](https://github.com/flashinfer-ai/flashinfer/commit/1f28b952d8bd75e380e03d0c55e2c00055b527a5)

- **作者**: eigen
- **时间**: 2026-10-10T22:16:52Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): round 8 — bit-exact dispatch-cell convergence, K=128 GEMM operand hand-off, cached launch receipts, short-row TMA-store fix (SM100a, SM103a) (#6217)

## Summary

Round 8 of the Cake `kimi_k3_fp8_projection` generated-program export
(FP8 block-scaled projection GEMMs of the Kimi-K3 KDA / MLA families —
22 families: TP8 and TP1 of q_proj, fused_qkvg, in_proj_qkvgfab, f_a,
f_b, b_proj (KDA) and kv_a, fused_qkv_a, q_b, kv_b, o_proj (MLA) — on
SM100 + SM103). Output stays bit-identical to the package currently on
FlashInfer main (e77db996c, carrying the previous delivery #6146) on
every contract row — 352 rows per GPU, 352 equal / 0 differ on B200 and
on GB300, through this exact package (UE8M0 block-FP8 recipe, FP32
accumulation, no approximate algorithm; modules compiled with
`--use_fast_math` as before).

- **Kernel-level optimizations of the previous kernel of record,
bit-exact**: the dispatch tables converged under paired same-GPU A/B of
every runtime-selectable lever on every contract row — 34 SM100 and 42
SM103 cells (of 120 per architecture) carry round-8 adoptions: TMA-store
epilogue on 10 / 12 cells, a new K = 128 half-stage GEMM operand
hand-off form on 11 cells (6 / 5), the cluster split-K DSM exchange on 3
/ 1 more cells, per-cell quantization launch width on 1 / 7, decode
pipeline depth 3 on 3 SM100 cells, GEMM weight-prefetch depth and
192-wide N tiles, next-weight-stage prefetch, tensor-map descriptor
prefetch (3 SM103 cells), a second TMEM accumulator set (1 SM103 cell),
the fused in-CTA activation quantization form on the M = 2048 decode
cell of both architectures, plus one new M = 2048 GEMM-route cell per
architecture. Every lever moves data or schedules work; the FP32
accumulation order is unchanged. Sealed record-vs-new geomean over the
timed rows: 1.0222 (GB300, 198 rows, 73 ≥ +2 %) and 1.0359 (B200, 197
rows — the validity-gate row tp1_fused_qkvg_m2048 is compared by hand at
0.9406 / 0.9380 — 98 ≥ +2 %); paired same-GPU A/B against the previous
kernel of record geomean 1.0164 / 1.0177 with no row below 0.98 after
isolation (below).
- **Cached launcher** on top of pre-planned launch receipts: re-binds
the activation / output tensors per call, one host crossing per call
also for two-launch routes (packed receipt chain), interpreter-light
per-call path (five TP8 rows: 7-12 us per call on an x86 host with SM100
and 9-14 us on a Grace host with SM103 vs 15-19 / 21-25 us for the
previous launcher, measured on the launcher-development trees).
- **Short-row TMA-store fix**: the bucket-256 GEMM cells route every M
in 65..256 to the GEMM, and the TMA-store output descriptor (32-column x
128-row box over the `[M, n_valid]` view) was refused by the host for M
< 128 (`ValueError: TMA box (32, 128) exceeds resolved global dims for
'OUT'` at plan time, one-shot / cached launcher alike). The row axis of
the output map now opts into the hardware's out-of-bounds clipping,
exactly as the partial last tile of every TMA-store row with M not a
multiple of 128 already relies on. New rows in the test module: `kv_b`
M=100, `q_b` M=65, `q_proj` M=127 and
`test_launcher_short_rows_take_tma_store`.
- **Cached-launcher hardening**: activations below 16-byte alignment are
refused with a `ValueError` on all paths (previously an opaque
`cuTensorMapEncodeTiled` failure on the fused-decode rows and an
unchecked misaligned vector load in the quantization kernel on
GEMM-route rows); the cached launcher is tested bit-for-bit against the
one-shot path on the program classes the representative test rows reach
(stream-K / fix-up / 192-wide / prefetching / fused-decode TMA-store
receipts, two-unit quantization, column-8 output base);
register-epilogue GEMM programs keep their placeholder output descriptor
out of the per-call re-binds.
- **Package**: 162 content-hashed kernel / binding sources (81 programs;
49 in the previous render), 23 content-hashed shared device helpers plus
the device-common / host-common header pair, `cake_jit.py` registry,
`decode_table.py` with the round-8 key grammar (per-cell quantization
width `quant_units`, TMEM accumulator sets `acc_bufs`, epilogue warp
groups `epi_groups`, descriptor prefetch `dpf`, GEMM K tile `gemm_bk`,
…; the mirror refuses any table field it does not read), README, test
module (74 tests).

## Validation

- Sealed export receipts on this exact render (package hash identical on
both GPUs, 195 files) with paired same-GPU source-vs-export CUPTI timing
— 3 counterbalanced groups × 2000 samples per arm, 8 captured graph
instances per arm, cold L2 — plus bitwise parity and zero-budget
correctness on every row: SM103 352 / 353 rows passed; the one
non-passing row, `tp1_f_b_m1000_corr` (a correctness row), passed
correctness, parity, launch-count parity, directional disagreement and
endpoint drift and failed only the median-based source/export timing
gate at 0.9321 — both arms are bimodal with the same two modes (14.2 /
15.75 us; pooled mode-centre ratios 1.0052 / 1.0052; means within 0.8
%), the pooled medians sitting on different modes. SM100 351 / 353 rows
passed; the two non-passing rows, `tp1_fused_qkvg_m2048` and
`tp1_fused_qkvg_m513_corr`, failed only the endpoint-drift validity gate
(0.0293 / 0.0234 vs 0.02; re-measured once: 0.0218 / 0.0262) with
correctness, parity, source/export 0.9987-1.0000 and directional
disagreement ≤ 0.0003 passing and both arms moving together (for the M =
2048 row the SM clock fell 1965 → 1845 → 1807 MHz across the three
groups of the first attempt; the M = 513 row read 1965 / 1965 / 1942 MHz
with a transient slow episode in both arms; per-arm medians 483.23 vs
483.26 us and 174.50 vs 174.50 us in the re-measure). Whole-root
source/export: SM103 min 0.9321, p05 0.9932, geomean 0.9999; SM100 min
0.9502, p05 0.9954, geomean 1.0006.
- Current-main (e77db996c) vs round-8 bitwise parity through this
package on all 352 contract rows per GPU: 352 equal / 0 differ (B200),
352 equal / 0 differ (GB300); launcher path (first call: receipt planned
and launched) == one-shot == a second one-shot call on every row.
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py` on this
render: 74 passed on B200 and 74 passed on GB300 (run inside the
sealed-export deliveries); `ruff format --check` + `ruff check` (repo
config, ruff 0.12.8) clean on the shipped files — both also green on the
seed deliveries before the first sealed measurement.
- Paired same-GPU no-regression check vs the previous kernel of record
on both GPUs (198 timed rows, 5 shards × 3 alternating rounds, one GPU
per shard, A,B,A,B per-kernel isolation of every row below 0.98): GB300
geomean 1.0164 (one row read 0.9786 in its shard and 13.28 us on both
trees in all four isolation runs), B200 geomean 1.0177 (one row read
0.9604 in its shard and 1007.0 / 1008.6 / 1007.3 / 976.8 us A,B,A,B with
the same two kernels and per-kernel split) — no kernel regression.
- Versus the fastest FP8 chain that produced a timing in the measurement
container — FI CUTLASS groupwise (198 rows) and FI TRT-LLM groupwise
(180 rows; CUTLASS alone on the other 18 rows per GPU) — CUDA-graph
replay, CUPTI kernel time, one process per peer, on this render: SM100
198 / 198 timed rows, geomean 2.21x vs the fastest complete chain per
row, minimum 1.02x, no row below 1.00x (CUTLASS 2.43x, min 1.05x;
TRT-LLM 3.47x, min 1.02x); SM103 198 / 198, geomean 2.21x, minimum 1.04x
(worst per-set speedup vs CUTLASS 1.06x, vs TRT-LLM 1.04x). cuTile
groupwise compiled on 72 (SM100) and 24 of 66 per set (SM103) rows —
Cake ≥ 1.15x faster there — and failed on the rest
(`TileCompilerExecutionError: Return code 5`); the DeepGEMM chains (FI's
DeepGEMM port, deepgemm_ue8m0) produced no timing in the container
(cubin not registered / torch-interpreter assertion).
- Roofline fraction (per-row floor = max(bytes / 8 TB/s, FLOPs / 4500
TFLOPS) + the measured launch ramp): geomean over the timed rows 1.663 →
1.626 (GB300) and 1.782 → 1.721 (B200) from the previous kernel of
record to this render.
- End-to-end on two GB300 nodes (2 × 4 GB300, TP8, real Kimi-K3-NVFP4
weights, SGLang server using the package's cached launcher; one server
with the route toggled per request plus an independent engine-default
server), measured on the earlier round-8 render of this PR (same
launcher path, different dispatch cells): time-to-first-token with the
route on at or below the engine default in 13/13 pairs — batch 1 at
1024/128 tokens: medians 257.2 vs 264.0 ms over 5 pairs, median per-pair
ratio 0.973; batch 8 0.949, batch 32 0.939, 8192-token prompt 0.952;
decode throughput unchanged within 0.3 %. Latency only: the stock path
runs different GEMM kernels, and this run did not separate that from
server-instance nondeterminism.
- `compute-sanitizer` synccheck on this render: every kernel instance
new since the previous kernel of record executed under synccheck (SM100
27 / 27, SM103 28 / 28 keys), the 60 registered production sanitizer
rows and the two K = 128 GEMM rows per GPU: 0 errors on both GPUs (the
earlier round-8 render had also passed memcheck on its registered rows).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ee4de7d](https://github.com/flashinfer-ai/flashinfer/commit/ee4de7dfd6d66a872345eee6e371923e6425f4a5)

- **作者**: Adrian
- **时间**: 2026-10-10T18:28:30Z
- **提交信息**: test: prune RoPE parameter matrices (#5416)

## 📌 Description

Convert the Cartesian parameter matrix or matrices in
`tests/attention/test_rope.py` to `parametrize_product`. Regular pytest
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
* Updated rotary-position embedding test coverage to use pairwise
combinations of test parameters, including position-ID types,
interleaving, cache layouts, and page sizes.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [9df2bfe](https://github.com/flashinfer-ai/flashinfer/commit/9df2bfe23f45156dccdb6a5218729dc7df561642)

- **作者**: eigen
- **时间**: 2026-10-10T12:29:20Z
- **提交信息**: perf(cake_dsv4): add the H64 tile member to the NVFP4 sparse-MLA decode family (SM100/SM103) (#6262)

## Summary

Adds a seventh kernel member to the SM100 / SM103 DeepSeek-V4 NVFP4
sparse-MLA decode family (`backend="cake"`,
`kv_cache_format="nvfp4"`): the **H64 tile member**
`nvfp4_decode_tile_h64_oc{2,4}` (two generated programs, one kernel
template with the `o_chunks` knob). The host route sends the one-tile
rows with `H <= 64` heads whose split gives 2 or 4
CTAs per work item to it instead of the 128-row `tile` member; the 1-CTA
form and every other row keep their current
member, so the delivered set is now 17 programs (fifteen as before + the
two new ones) plus the shared headers.

- **What changes in the kernel.** The `tile` member stages a 128-row Q
box per head tile; for 64-head rows half of
every box is padding that still crosses the K/V operand zone, so the
compute warps wait on a `q_ready` rendezvous
before the first K tile can land. The H64 member stages 64-row Q boxes
that land directly in their final SMEM slots:
the landing copy and the rendezvous disappear, SMEM drops from 226848 B
to 192032 / 208416 B (oc4 / oc2), and the MMA,
softmax and epilogue program is byte-for-byte the tile member's — same
quantization points, same fp32 accumulation
order. Outputs are **bitwise identical** to the tile member's on every
validated shape and seed (member-pair and entry-pair
seed gates over 3 seeds: 12 / 12 and 78 / 78 bitwise checks per card);
compute-sanitizer synccheck + memcheck are clean on both cards.
- **Host route.** `flashinfer/mla/cake_dsv4.py`: `_nvfp4_plan` picks
`tile_h64` for `H <= 64` one-tile rows at 2 or 4
CTAs per work item (`TILE_H64_MAX_HEADS = 64`);
`tests/mla/test_cake_dsv4_nvfp4_route.py` covers the new rows.
Loader: two new registrations (`min_cuda_version` 13.4 like the other
NVFP4 programs); no other public API change.
- **Shared device helpers.** The exporter now emits the family's device
helpers (mbarrier, TMA, tcgen05, TMEM and
softmax primitives) as content-addressed shared headers under
`csrc/cake_device_helpers`: the kernels include 34
distinct helpers, 27 of them new in this PR and 7 reused unchanged from
the 9 already in `main` (the other 2 of those 9
serve other Cake families); the generated kernel sources include them by
content hash.
- **Why.** Measured with the same cold-L2 CUPTI paired protocol as the
previous deliveries, the seven re-routed rows
(64-head rows with 128 or 512 top-k candidates at 1–32 tokens) run
0.90–0.95x of their previous time on B200
(0.895–0.951, geometric mean 0.929) and 0.90–1.00x on GB300
(0.899–0.997, geometric mean 0.947; C-h64-k512-t8 is
unchanged within the same-code noise band there and C-h64-k128-t8 / -t32
read 0.957 / 0.974); rows that keep their
  route are unchanged within the same-code noise band.

| Row (DeepSeek-V4 decode shape; `oc` = CTAs per work item) | GB300 new
/ old (us) | B200 new / old (us) | same-code A/A GB300 | same-code A/A
B200 |
|---|---|---|---|---|
| C-h64-k128-t1 (oc4) | 0.899 (7.90 → 7.10) | 0.895 (8.83 → 7.90) |
0.984 | 0.998 |
| C-h64-k128-t8 (oc4) | 0.957 (8.86 → 8.48) | 0.910 (8.93 → 8.13) |
1.029 | 1.000 |
| C-h64-k128-t32 (oc2) | 0.974 (9.76 → 9.50) | 0.951 (9.79 → 9.31) |
1.013 | 1.000 |
| M-h64-k128-t12 (oc4) | 0.916 (9.29 → 8.51) | 0.918 (8.99 → 8.26) |
0.983 | 1.004 |
| C-h64-k512-t1 (oc4) | 0.942 (10.98 → 10.34) | 0.933 (11.04 → 10.30) |
0.997 | 0.990 |
| C-h64-k512-t8 (oc2) | 0.997 (11.97 → 11.94) | 0.951 (12.05 → 11.46) |
1.000 | 1.000 |
| H-04-num64-top128-ext132 (oc4) | 0.951 (11.07 → 10.53) | 0.948 (11.07
→ 10.50) | 1.006 | 1.003 |
| C-h128-k128-t1 (route unchanged, reference) | 1.002 (8.64 → 8.66) [1]
| 1.002 (9.52 → 9.54) | 1.117 [1] | 1.002 |
| C-h32-k128-t32 (route unchanged, reference) | 0.990 (8.14 → 8.06) |
1.004 (7.90 → 7.93) | 0.977 | 1.004 |
| C-h64-k512-t128 (route unchanged, reference) | 1.004 (23.95 → 24.05) |
0.990 (24.51 → 24.26) | 0.999 | 0.997 |

Ratios below 1.0 are faster. Each cell is the ratio of cold-L2 CUPTI
medians of the Cake `sparse_mla_decode` entry with the new planner
routing over the same entry with the previous routing, five
counterbalanced ABBA rounds in one process, with a same-code A/A twin in
the same run as the noise band (the FlashInfer host route `_nvfp4_plan`
mirrors that routing and was not A/B-timed itself; its source/export
parity on these rows is in the Measurement section below). The seven
re-routed rows are every `H = 64` one-tile row of the measured tables
routed at 2 or 4 CTAs per work item (the three 1-CTA rows
C-h64-k128-t128, C-h64-k512-t32 and M-h64-m128-e512p64-t12 keep `tile`)
plus the external H row; the three reference rows keep their route.
Geometric mean over the seven re-routed rows: 0.947 (GB300) / 0.929
(B200); the three reference rows are excluded from these means.
[1] The GB300 reference row's first run (the 10-row process) read 1.117
(8.77 → 9.79 us) in the A/B and 1.117 in its same-code A/A twin as well
— the same-code copy spread recorded for this node class (the second
copy of the unchanged program ran at 9.79 us in every slot of both
groups), not a kernel effect. The pre-registered single re-measure in a
fresh process (5 rounds) repeated only the A/B: 8.64 → 8.66 us, 1.002, A
== B bitwise; the A/A twin was not re-measured, so the GB300 same-code
noise band applied by the evaluator is 0.117 from that twin (B200 band
0.030). The geometric means above use the re-measured A/B value.

## CI coverage note

The PR CI has no SM100 / SM103 runner, so the `backend="cake"` NVFP4
decode tests skip there on the architecture guard;
the route test (`tests/mla/test_cake_dsv4_nvfp4_route.py`, CPU-only)
exercises the new plan rows in CI. GPU evidence is the
two-card run below (CUDA 13.4 toolchain). The `cake_dsv4` loader is
JIT-only (not part of the AOT build).

## Proof of identity

| Export run | Member | sm_100a SASS-equal | sm_103a SASS-equal |
Refinement rounds / widenings | nvcc compiles (prove / probe) |
|---|---|---|---|---|---|
| B200 export | `swap` | 6/6 (alpha 6, sched 6) | 6/6 (alpha 6, sched 6)
| 1 / 1 | 2 / 102 |
| B200 export | `tile` | 3/3 (alpha 3, sched 3) | 3/3 (alpha 3, sched 3)
| 1 / 1 | 2 / 11 |
| B200 export | `tile_h64` | 1/2 (alpha 1, sched 2) [2] | 2/2 (alpha 2,
sched 2) | 0 / 0 | 1 / 0 |
| B200 export | `pv` | 2/2 (alpha 2, sched 2) | 2/2 (alpha 2, sched 2) |
0 / 0 | 1 / 0 |
| GB300 export | `swap` | 6/6 (alpha 6, sched 6) | 6/6 (alpha 6, sched
6) | 1 / 1 | 2 / 102 |
| GB300 export | `tile` | 3/3 (alpha 3, sched 3) | 3/3 (alpha 3, sched
3) | 1 / 1 | 2 / 11 |
| GB300 export | `tile_h64` | 1/2 (alpha 1, sched 2) [2] | 2/2 (alpha 2,
sched 2) | 0 / 0 | 1 / 0 |
| GB300 export | `pv` | 2/2 (alpha 2, sched 2) | 2/2 (alpha 2, sched 2)
| 0 / 0 | 1 / 0 |

[2] The proof accepts an instantiation when its SASS is byte-equal to
the per-knob program's or schedule-equal (the same multiset of
instructions with register numbers erased and the same distinct-register
count; the rule of the previous deliveries). `decode_tile_h64<2>` on
sm_100a is the only instantiation accepted on schedule-equality alone
(the same cubin pair in both export runs): a cuobjdump comparison over
the full streams shows 5504 instructions each, identical opcode
histograms and immediates, 104 registers each, and 5500 / 5504 lines
identical after erasing register numbers; the 8 differing lines are 4
consecutive uniform-datapath instructions in which ptxas swapped the
roles of two uniform registers (UR10 / UR11) — the same instruction
sequence with a different physical register assignment.
`decode_tile_h64<4>` and both sm_103a instantiations are byte-equal.

## Measurement (same protocol as the previous deliveries: cold-L2 CUPTI,
counterbalanced interleaved groups, 76 shapes per card)

Each column is the geometric mean over shapes of Cake source-tree kernel
time over CAKE Exported Kernel time (source / export;
1.0 = parity), all rows and the per-table subsets C / D / M / O / X / H.

| Card | timed rows | correct | rows >= 0.97 (previous delivery #6215 in
parentheses) | source/export geomean all / C / D / M / O / X / H |
previous delivery #6215 (same geomeans) |
|---|---|---|---|---|---|
| B200 (sm_100a) | 76 | 76 | 74 (75) | 1.000 / 1.002 / 1.001 / 0.998 /
0.998 / 0.994 / 0.997 | 0.999 / 1.005 / 0.996 / 0.992 / 0.993 / 0.995 /
0.994 |
| GB300 (sm_103a) | 76 | 76 | 71 (69) | 1.001 / 1.005 / 1.009 / 0.985 /
1.007 / 0.996 / 0.999 | 0.996 / 1.001 / 0.991 / 0.990 / 0.972 / 0.999 /
0.996 |

Disclosed (per-row source/export floor 0.97 is informational, same
acceptance as the previous delivery #6215; the previous-delivery column
is that export's own compare receipt): B200 rows below the floor
C-h64-k512-t8 0.9397, X-h128-k256-t72 0.9630; GB300 rows below the floor
C-h64-k512-t8 0.9031, M-h64-m128-e512p64-t12 0.9408, C-h64-k512-t32
0.9529, M-h128-k128-t12 0.9672, X-h128-k256-t72 0.9698; rows whose three
measurement groups disagreed in direction (ratio not interpreted):
D-h16-m128-e512p64-t32 and D-h16-m512-e512p64-t32 on both cards,
X-h128-k256-t32 on GB300. All 76 rows per card are correct, timed and
source/export bitwise-identical.

## Tests

FlashInfer tests on the delivered tree, per card (CUDA 13.4 toolchain,
JIT): `tests/attention/test_sparse_mla_blackwell_dsv4_nvfp4.py`,
`tests/mla/test_cake_dsv4_nvfp4_route.py` and
`tests/mla/test_cake_dsv4.py` -- **B200: 439 passed, 0 failed; GB300:
439 passed, 0 failed** (previous delivery: 435 per card). Test changes:
`tests/mla/test_cake_dsv4_nvfp4_route.py` gains the plan rows for the
two new `tile_h64` programs (this is where the suite grows, 435 -> 439
cases per card), and `test_registered_compile_flags_are_public` in
`tests/mla/test_cake_dsv4.py` enumerates the kernel-template members and
gains `DECODE_TILE_H64` (allowlist entry and docstring only; no new
cases). Cake-side gates on the same tree: compile + static analysis 28
passed, GPU correctness 7 passed, planner 40 passed per card;
export-tool unit tests 348 passed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added NVFP4 decode options for 64-head workloads with two- and
four-way splits.
* The decode planner now selects these options for eligible workloads
while retaining existing choices for other head sizes and split
configurations.
* **Improvements**
* Expanded support for NVFP4 decode variants on supported GPU
architectures, including the new 64-head options.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c94c1a9](https://github.com/flashinfer-ai/flashinfer/commit/c94c1a9e4bf151e56080168ac880ebf0651af317)

- **作者**: eigen
- **时间**: 2026-10-10T09:01:40Z
- **提交信息**: perf(cake_minimax_h3_varlen_attention): round-6 SM100a single P barrier and tail-round Q-split planner (SM100a, SM103a) (#6258)

## Summary

`flashinfer.experimental.minimax_h3_varlen_attention` (Cake backend,
SM100a/SM103a BF16 packed-varlen attention), round 6 on top of #6062.
Two exact program changes, output bitwise identical to the delivered
program (same FP32 online softmax, bf16 P, FP32 accumulation, one final
BF16 rounding; no new intermediate rounding):

- **SM100a single P barrier per PV group**: the softmax publishes the
128-key probability tile once (one `tcgen05.wait::st` and one arrive
after the four 32-key stores) and the MMA warp runs each PV group as one
`k(0, 128)` call behind one wait. The SM103a program keeps the two-wait
form, which measured better there.
- **Tail-round Q-split (host planner, both architectures)**: when the
persistent-grid tail round leaves clusters idle,
`cached_bf16_segment_plan` halves the most expensive two-stage tail
units into two 256-row single-stage records (unit-table word 5 `q_half`)
whenever the simulated makespan improves by at least 1 %; the program
decodes the word. Only the slot-to-rows mapping changes: each row keeps
its K/V range and output path, and Q-split units never overlap KV-split
units. The plan cache key gains `q_split`.
- The generated programs under `csrc/cake_minimax_h3_varlen_attention/`
are regenerated from the round-6 Cake tree (the BF16 programs change;
program ids in `cake_jit.py`), replacing the round-5 set;
`cake_backend.py`, `README.md` and the test module are rendered by the
Cake exporter against this branch's base (`26f24189`).

## Measurements

CUPTI cold-L2 interleaved timing (paired A/B inside one process,
identical-program control arm within 0.99-1.01, two independent
sessions; ratio = previous program / this program):

- B200 (SM100a), single P barrier: >= 1.000 in both sessions on 39/42
rows, 33/37 FlashInfer-compared rows >= 1.005 in both; largest gains on
the long two-stage rows (center_10s_p2 1.022 / 1.019, center_15s_p2
1.014 / 1.029, center_6s_p1 1.028 / 1.010).
- Tail-round Q-split: every row whose plan changes >= 1.000 in both
sessions - B200 1.009-1.043 on the production rows (center_8s_p4 1.041 /
1.043, center_15s_p4 1.030 / 1.032, center_4s_p2 1.023 / 1.023,
center_5s_p2 1.025 / 1.021, tail_5s_p2 1.021-1.024, center_10s_p2 1.017
/ 1.009, center_6s_p2 1.010 / 1.009; smoke rows ~1.22), GB300
center_6s_p4 1.077 / 1.077, center_8s_p4 1.067 / 1.065, center_4s_p2
1.032 / 1.031, center_8s_p2 1.016 / 1.016. Rows without a tail round
keep their plan (identical launches).
- Standing against the fastest FlashInfer ragged route per row (fa2 /
cudnn / cutlass / cute-dsl / FA4, contract harness, single session):
B200 25 of 37 production rows >= 1.0, geomean 1.032, min 0.979; GB300 27
of 40 rows >= 1.0 (the dit_short_p1 fused view re-measured on the
delivery tree: 1.075), geomean 1.049, min 0.980; previously 26 of 39
measured rows >= 1.0, geomean 1.049, min 0.980.
- Generated-program export protocol: 120/120 protocol rows per
architecture pass at FlashInfer main `26f24189` for the delivered text
(B200: source/export ratio geomean 0.9994, min 0.976; GB300: geomean
0.9997, min 0.982; floor 0.97; measured in full for this delivery across
continuation rounds that carry completed receipts as read-only priors;
one 13 us B200 smoke row re-measured after reading 0.969).

## Validation

- Cake: 56/56 contract rows correct on both architectures (atol = rtol =
1e-2), FP32-oracle gate equal to the previous program on every row
(bitwise-identical output), compute-sanitizer synccheck + memcheck 0
errors on both architectures (registered launcher and a plan with split
units), e2e slice and bench-regression green, render identity recorded.
- FlashInfer:
`tests/experimental/test_cake_minimax_h3_varlen_attention.py` (644
passed, 0 failed on each architecture) on B200 and GB300, including the
new Q-split planner tests (mixed KV-split / Q-split exclusivity, default
plan path, sub-wave grid growth, half-record inheritance).

## Update: host planner constant `BF16_Q_SPLIT_MIN_GAIN` 0.01 -> 0.005

- **What changes**: `cake_backend.py` halves the most expensive
two-stage tail units of the persistent-grid tail round when the
simulated LPT makespan improves by at least 0.5 % (was 1 %). Generated
programs and program ids are unchanged (the split only re-partitions
rows across the same two-stage / single-stage kernels); the planner test
pins the new bar (an 81-wave case at 0.48 % stays whole, a 61-wave case
at 0.64 % is halved). A CPU census of the 56 contract rows at 74
clusters (B200) and 76 clusters (GB300) shows the plan changes only on
the four DiT rows (dit_t2va_p1, dit_2seg_p1 and their fused views, 3584
units each): on GB300 the 12 tail units are halved (3584 -> 3596 table
records), on B200 the 32 tail units are halved (3584 -> 3616); every
other row keeps its plan.
- **Measured effect of the constant alone** (paired same-process CUPTI
cold-L2 A/B of the 0.01 vs 0.005 plan, arms base / identical-program
control / 0.005, 3 rounds x 400 ms, one step per architecture; ratio =
0.01-plan time / 0.005-plan time): GB300 (SM103a) DiT rows 1.1-1.8 %
faster -- dit_t2va_p1 1.018, dit_2seg_p1 1.011, fused views 1.016 /
1.013, controls 0.994-0.999; B200 (SM100a) dit_2seg_p1 1.007 (control
within +/-0.13 %), dit_t2va_p1 inconclusive (its control left the
0.99-1.01 band). Output bitwise identical to the 0.01 plan on every A/B
row.
- **Standing against the fastest FlashInfer ragged route per row**
(contract harness, fastest route per row as in Measurements above; for
the DiT rows that is cudnn on GB300 and cute-dsl on B200), under the
stricter two-session rule used since the delivered program's
re-measurement (a row counts only when >= 1.000 in both of two
independent paired sessions, and a session whose identical-program
control leaves 0.99-1.01 is void and re-measured; the single-session
figures in Measurements above are 27 of 40 and 25 of 37): GB300 29 of 40
contract rows (26 for the delivered program under the same rule --
dit_2seg_p1 1.0142 / 1.0064 and both fused DiT views 1.0039 / 1.0042,
1.0115 / 1.0128 flip; dit_t2va_p1 reaches parity at 1.0035 / 0.9998),
B200 unchanged at 19 of 37 (dit_2seg_p1 1.0086 / 1.0018 stays passing).
- **Export protocol re-run** (source/export parity of the Cake
production launcher vs the exported program, same GPU, floor 0.97; the
delivered host hash changed, so no earlier receipt is reused): 120/120
rows (SM100a) pass, geomean 0.9992, min 0.9759; 120/120 rows (SM103a)
pass, geomean 1.0004, min 0.9841; at FlashInfer main `26f24189`. On B200
the first pass sealed 119 passing rows and `bf16__smoke_p8_513` at
0.9635; that one row was re-measured once through the exporter's
prior-retention round (the 119 receipts retained) and read 0.979 -- both
readings are kept in the receipts.
`tests/experimental/test_cake_minimax_h3_varlen_attention.py`: 644
passed (B200), 644 passed (GB300).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* BF16 attention planning can now split eligible Q units in a partial
tail round when the estimated execution time improves enough. The option
is configurable and included in plan caching.
* Attention kernels support the resulting half-unit plans while
preserving output accuracy.
* **Bug Fixes**
* Improved compatibility and reliability across supported GPU
architectures.
* **Tests**
* Added coverage for split selection, plan records, configuration
options, and output equivalence.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [5b55073](https://github.com/flashinfer-ai/flashinfer/commit/5b550737e6d8b698c0fb7a5026cce816a3f461e5)

- **作者**: eigen
- **时间**: 2026-10-10T08:23:43Z
- **提交信息**: fix(cake_all_gather_matmul): proxy fence after the readiness acquire (#6254)

Follow-up to #6153 ([review
thread](https://github.com/flashinfer-ai/flashinfer/pull/6153#discussion_r4201689188)).
Rebased on `main` after #6104
re-exported this family; the fix is delivered as a fresh export from the
same generator, so the
12 main kernels carry new names (kernel names are content hashes of the
generated program) and the
host-sequence sources / JIT loader reference those names.

## Summary

The `cake_all_gather_matmul` consumer stages each peer's `A_scratch`
rows into
shared memory with a TMA (`cp.async.bulk.tensor`, async proxy).
`A_scratch` is
written by a peer GPU in the generic proxy — the SM-push path
(`st.volatile.global` over NVLink) or the copy-engine push — and the
peer signals
arrival via the ready counter, which the consumer polls with
`ld.acquire.sys.global`.

The `sys`-scope acquire orders the counter read, but under the PTX
memory model
the peer's generic-proxy writes to `A_scratch` are not guaranteed
visible to the
async-proxy TMA without an explicit `fence.proxy.async` between them
(proxy-preserved causality). This adds that fence — in the same elected
thread,
after the acquire and before the first `A_scratch` TMA — using the
`.global` form,
because the hazard is the global peer scratch, not shared memory.

## Change

Per main kernel (12 kernels), inside the `peer_pass != 0` /
elected-thread block that
polls the peer's readiness word:

```
-  asm volatile("ld.acquire.sys.global.u32 %0, [%1];" : "=r"(_gca_v) : "l"(_gca_p));
+  asm volatile("ld.acquire.sys.global.u32 %0, [%1];"
+               : "=r"(_gca_v)
+               : "l"(_gca_p)
+               : "memory");
   ...
+  asm volatile("fence.proxy.async.global;" ::: "memory");
```

The `"memory"` clobber on the acquire asm keeps the dependent TMA from
hoisting
above the acquire. Against `main`, `git diff -M` shows the 12 kernels as
renames (98 %
similar) whose content differs by exactly these lines plus the kernel
symbol name; the 24
host-sequence `.cu` files and the JIT loader change only by those symbol
names (the
loader's per-kernel table is re-ordered by name, entries unchanged); the
push and the two
barrier kernels, `device_common.cuh`, the shared helpers, the Python
host module, docs and
tests are untouched.

## Validation

All runs below used the generator at the commit that produced the
kernels in this PR, on B300
(sm_103a) and B200 (sm_100a) nodes in the same pinned container on both.
The FlashInfer tests ran
on this PR's head; the compute-sanitizer, bitwise and timing runs drive
the same generated kernels
through the generator's multi-GPU harness (TP2/TP4 rows on 2/4 GPUs, TP8
rows on 8).

- Generated-CUDA diff vs `main`: fence + clobber lines only (12
kernels), as above.
- compute-sanitizer synccheck and memcheck report `ERROR SUMMARY: 0
errors` on every rank for all
four representative rows — TP2 1024×2048 and TP8 2048×1280 (copy-engine
push), TP4 512×2560 and
  TP8 125×2048 (SM-push) — on both architectures.
- Output is bitwise-identical to the unfenced kernels on every rank for
all 60 (TP, M, N, layout,
dtype) rows of the generator's validation shape list (12 TP2 / 24 TP4 /
24 TP8 rows) on both
architectures (correctness-only A/B against the unfenced generator
output).
- FlashInfer tests for this backend pass on 8×B300 and 8×B200:
  `tests/comm/test_all_gather_matmul_cake.py` (178 CPU cases) and
`tests/comm/test_all_gather_matmul_cake_e2e.py` (3 cases — bf16 and fp16
with the CUDA
symmetric-memory backend, bf16 with NVSHMEM; the test uses all visible
GPUs, i.e. world size 8 here).

### Fence cost

Rank-aligned CUPTI A/B through the generator's harness: two replicate
passes of 9 counterbalanced
ABBA groups each (the leading arm alternates every group; the passes
differ only in which arm leads
the first group), plus an identical-code control (unfenced vs unfenced)
through the same harness.
Per group, each arm's time is the median of its two bursts of the
per-iteration slowest-rank time;
the tabulated ratio is the median over the 9 groups of unfenced / fenced
(> 1 = fenced arm faster),
with the min–max of the 9 per-group ratios in parentheses. SM clocks
were not recorded; the
identical-code control is the noise reference.

| row | sm_103a pass 1 | sm_103a pass 2 | sm_103a control | sm_100a pass
1 | sm_100a pass 2 | sm_100a control |
|---|---|---|---|---|---|---|
| TP2 1024×2048 (copy-engine push) | 0.918 (0.86–1.07) | 1.006
(0.84–1.07) | 1.030 (0.93–1.11) | 0.960 (0.90–1.07) | 0.957 (0.91–1.10)
| 1.013 (0.83–1.04) |
| TP4 512×2560 (SM-push) | 0.956 (0.84–1.00) | 0.999 (0.87–1.10) | 0.976
(0.92–1.07) | 1.009 (0.95–1.10) | 1.002 (0.91–1.02) | 0.958 (0.89–1.07)
|
| TP8 125×2048 (decode, SM-push) | 1.004 (0.97–1.04) | 1.021 (0.98–1.07)
| 1.022 (0.97–1.06) | 1.004 (0.94–1.12) | 0.971 (0.84–1.04) | 1.015
(0.97–1.11) |

End-to-end, this harness cannot resolve a fence cost on these rows:
identical code scatters from
0.83 to 1.11 per group (standard deviation of the per-group log-ratio
3–8 %), the control's own
9-group median is up to 4 % from unity (0.958 on the sm_100a TP4 row),
and the two replicate passes
differ by up to 9 points (sm_103a TP2: 0.918 vs 1.006). All twelve
fenced/unfenced readings
(0.918–1.021) lie within that scatter, including the rows where the
fenced arm reads ≈4–5 % slower
(sm_100a TP2 in both passes, sm_103a TP4 in one pass), which is the size
of the control's own
deviation. The fastest rank's main-kernel span is only ≈13–25 % of each
iteration here (the rest is
the push and barrier kernels, in-kernel waiting for the peer's data and
inter-kernel gaps), so a
kernel-level cost is diluted further in the end-to-end ratio.

The direct measurement is the per-rank main-kernel span from the CUPTI
traces. On the TP8 decode
row the spans are 81–88 µs on every rank in every pass on both
architectures; the fenced-vs-unfenced
difference per rank is at most 4.6 µs (sm_103a) / 3.2 µs (sm_100a),
against up to 2.1 / 3.3 µs
between the two identical-code control arms, and the unfenced arm is the
slower one on 21 of the
32 rank-passes. On TP2 the rank whose peer data has already arrived runs
the main kernel in ≈52 µs
(sm_103a) / ≈56 µs (sm_100a) with and without the fence, equal to within
0.6 µs in both passes (the
other rank's 100–185 µs span is dominated by the in-kernel wait). Any
fence cost on the main kernel
is therefore below ≈2 % on these rows.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [68039cc](https://github.com/flashinfer-ai/flashinfer/commit/68039cc76da0b26140f457f345457f1c52a4a8c0)

- **作者**: eigen
- **时间**: 2026-10-10T08:06:07Z
- **提交信息**: perf(cake_deepgemm): dynamic chunk scheduler for the paged FP8 MQA logits; 64-head dense programs: early Q-stage release, short-KV one-split routes and a prologue prefetch; refreshed admission tables (SM100a, SM103a) (#6118)

## Summary

Re-export of the `deepgemm_dense_mqa` family (dense 32-head and 64-head
FP8 / FP4 MQA logits, paged FP8 MQA logits) from the producer tip that
closes the DeepSeek-V3.2 lightning-indexer performance round on SM100a /
SM103a. Rebased onto main after #6097 merged. Updated after the merge of
current `main` (resolving the two content-addressed device helpers that
#6104 also ships,
`csrc/cake_device_helpers/cake_elect_commit_8131fdc67daf4d23.cuh` and
`csrc/cake_device_helpers/cake_make_warp_uniform_26e432f3ff129648.cuh`,
with main's copies; header and indentation differences only): the
exported `deepgemm_dense_mqa` package and `flashinfer/dense_mqa.py` are
byte-identical to the previous head. The dense programs stay at the
producer tip described in this PR; the producer's later change to the
shared `relu_weighted_sum_f32x2` lowering (carried by the
`cake_dsa_indexer` re-export in #6195) is intentionally not reflected in
these programs and was not measured for them. The `cake_dsa_indexer`
programs regenerated at the same producer tips are delivered separately,
on top of the round-2 indexer programs of #6056.

### `deepgemm_dense_mqa`

1. **Paged FP8 MQA logits — dynamic chunk scheduler (`:dyn` routes).**
Every single-atom paged geometry (64 heads x next_n {1, 2}, 32 heads x
next_n 1) gains a second program whose KV-load warp claims 4-split
chunks of the (request, KV-split) sequence through an atomic counter
instead of the static equal-split partition; the static partition left
the median SM idle 5-10 % of the kernel on long contexts. Logits are
bitwise identical to the static program (whole splits per CTA, no
split-K). Both programs take a per-plan `sched_counters` u32[2] state
(allocated zeroed by `PagedMqaPlan`, reset by the dynamic program's last
CTA at the end of each launch, so CUDA-graph replays need no memset; the
static program never reads it). The runtime selects the dynamic program
from the call's batch (`policy.paged.dynamic_scheduler`: batch <= 384 ->
`paged:fp8:h<H>:p<page>:n<next_n>:dyn`, otherwise the static route). The
static programs also adopt a one-request-per-thread schedule prologue
(same partition, one coalesced load + scan instead of a per-thread
binary search).
2. **Paged admission** is now per (arch, route, batch, max_context_len)
for the dynamic routes too: SM103a admits `next_n = 1` dynamic routes at
every batch through 32768 context and at batch <= 128 beyond; SM100a
admits `n1` the same way and `n2` dynamic through 32768 context. Points
outside the table keep the stock fallback (`paged_route_available(...,
arch=, batch=, max_context_len=)`).
3. **64-head FP8 dense logits — early Q-stage release** in the
full-window program (the Q stage is released as soon as the last KV
block of a row window has been issued, letting the next row's Q TMA
overlap the tail). The partial-window program keeps the previous
schedule. Both admission tables move: `fp8:h64:full:any` is admitted on
SM103a and SM100a (13 denominator rows per arch, 9/9 sessions each above
the paired floor); `fp8:h64:partial:any` stays SM103a-only. Twelve tier
denominator rows (`full:le8`, `partial:le8`, `partial:le1024`) were
added to the export denominator.
4. **32-head FP8 / FP4 dense programs:** the 32-head text forms the
logits address with a 64-bit per-block row base and an unsigned 32-bit
element index (fixes the > 2^31-element logits window), the FP4 indexer
issues its scale-factor copy from one elected lane in the Q prologue,
and the weighted ReLU sum has one lowering (the folding abs-in-PTX
form). Outputs are bitwise identical to the previous programs on every
denominator row.

Provenance: first commit generated from the producer tip `add68ef13ee`
(adapter and host sources byte-identical to the sealing producer tree
`4dc9dec51e2`; the test template carries one later fix, `307ea8ef60d`);
second commit from the producer tip `092b21d4926` (round 2); third
commit from the producer tip `67d4ab7d5c2` (round 3: the producer merged
with its main). Target: this branch's base commit.

### Round 2 (dense family only; this branch's second commit)

**Paged FP8 MQA logits — dynamic programs re-generated.** The three
`:dyn` programs (64 heads x next_n {1, 2}, 32 heads x next_n 1) now
claim 8-split chunks (was 4) through the atomic counter and issue the KV
TMA loads with the `evict_first` L2 cache hint when the plan's maximum
context length is at least 16384 tokens (a CTA-uniform branch on the
plan parameter, so the same program serves both regimes). Logits stay
bitwise identical to the static programs; `sched_counters` layout,
launch parameters and the host runtime are unchanged — only the
generated dynamic templates, the catalog (admission table + statistics)
and the README statistics change. **Paged admission:** on SM100a the
`next_n = 2` dynamic route is now admitted at every batch and context
length (the 131072-context rows cleared their paired floors at batch 64
/ 128 / 148: 1.0553 / 1.0246 / 1.0227 vs floor 1.011, 9 sessions each;
every previously admitted row stays at or above the previous text).
SM103a tables are unchanged. The static paged programs and all dense
programs are byte-identical to the first commit.

Round-2 test plan: export protocol re-run on SM100a for the whole
`deepgemm_dense_mqa` family — 60/60 shapes (42 dense + 18 paged; bitwise
source/export parity 60/60, identical per-call kernel counts 60/60,
catalog source check OK, no duplicate program body);
`test_dense_mqa_admission.py`, `test_dense_mqa_generated.py` and
`test_paged_mqa_generated.py` on SM100a on the rebased branch. SM103a
confirmation of the round-2 dynamic programs (paired CUPTI, pinned
DeepGEMM 0.2.0, 18 paged rows, graph mode, three interleaved passes):
every one of the 18 rows clears its paired floor with every session
above 1.00 (9 sessions per row; the three rows under 20 us of DeepGEMM
time take three readings per session, 27/27); the delivered dynamic
programs read faster than the round-1 dynamic programs on 12 of the 14
dynamic-program rows, one row at parity, and one row slower -- the
batch-1 x 131072-context row at 1.02x the round-1 time (9.76 -> 9.95 us,
round-1/delivered time ratio 0.981; coarser 8-split claims on a single
request; it still reads 1.236 against DeepGEMM); geomean over all 18
rows 1.047 relative to the round-1 text (dynamic-program 32768-context
rows +5 to +12 %, dynamic-program batch-16 131072-context rows +12 to
+14 %); the four static-program rows read 0.998-1.005 (identical text).
The SM103a admission table is unchanged.

## Test plan

- Export protocol (bitwise source/export parity per shape, identical
per-call kernel counts, paired CUPTI timing of the CAKE Exported Kernel
launch plan against the CAKE Source production launcher): rounds 1-2
`deepgemm_dense_mqa` 60/60 shapes per arch (42 dense + 18 paged) on
SM103a and SM100a; round 3 (88 shapes per arch: 70 dense + 18 paged)
88/88 on SM100a and 88/88 on SM103a (SM103a source/export ratio min
0.9731, median 1.0000, geomean 1.0001, max 1.0603); round 4 (the same 88
shapes per arch at the producer tip of the `:short` routes) 88/88 on
SM100a and 88/88 on SM103a (source/export ratio SM103a min 0.9636,
median 1.0019, geomean 1.0107, max 1.1130; SM100a min 0.9589, median
1.0015, geomean 1.0092, max 1.0909; bitwise source/export parity 88/88;
identical per-call kernel counts 88/88; the delivered program set and
the frozen protocol content are byte-identical on both architectures);
re-run from the formatting-fixed producer (fifth commit) 88/88 on SM100a
and 88/88 on SM103a (source/export ratio SM100a min 0.9500, median
1.0012, geomean 1.0068, max 1.0902; SM103a min 0.9636, median 1.0023,
geomean 1.0104, max 1.1043; program manifests byte-identical to the
fourth commit's seal); catalog source check OK, no byte-identical
duplicate program.
- `tests/experimental/test_dense_mqa_admission.py`,
`tests/experimental/test_dense_mqa_generated.py`,
`tests/experimental/test_paged_mqa_generated.py` on both architectures
(round 4: the admission test pins the `:short` routes' per-route (Q, K)
points and served-route semantics).
- Paired CUPTI acceptance tables at the producer tip (9 sessions per
row, pinned DeepGEMM 0.2.0 baseline): every admitted paged (arch, route,
batch / context) region clears its floor on both architectures and
withheld paged regions keep stock DeepGEMM; for the 64-head dense tiers
admitted in round 3, at the round-3 producer tip every row with a
non-empty prefix was at or above 1.00 and the prefix-0 one-block rows (4
us, K = Q) read 0.949-0.992 against DeepGEMM on both architectures
(ratio = DeepGEMM time / Cake time; the 18 ms `partial:any` row 0.9963
on SM100a); those measured in the previous round were accepted as
performance-matched (round 3); the two new `full:le64` prefix-0 rows
(round 3: 0.962 / 0.969 on SM100a, 0.950 / 0.992 on SM103a) are served
by the `fp8:h64:full:short` route since round 4 and clear their floors
there (SM100a 1.0163 / 1.0245, SM103a 1.1102 / 1.0250; 9/9 sessions
above 1.00 on both architectures; see Round 4).

### Round 3 (this branch's third commit)

**64-head FP8 dense admission: every tier; sources regenerated from the
merged producer.** The catalog now admits `fp8:h64:full:*`,
`fp8:h64:partial:*` and `fp8:h64:q1` at every query tier on SM100a and
SM103a: 7 new route records (`full:le8`, `full:le64`, `full:le1024`,
`partial:le8`, `partial:le64`, `partial:le1024`, `q1`) served by the
existing 64-head logits programs, next to the previously published
`full:any` / `partial:any` records (previously `full:any` on both and
`partial:any` on SM103a only). The tier rows that read below the paired
floor are one-block launch-floor cases (about 4 us, K = Q): the rows
measured in the previous round (0.949-0.992 against DeepGEMM on both
architectures, ratio = DeepGEMM time / Cake time, the 18 ms
`partial:any` row at 0.9963 on SM100a; every other tier row at or above
1.00) were accepted as performance-matched and no 64-head tier keeps a
stock fallback. The two `full:le64` prefix-0 rows this commit adds to
the denominator read 0.962 / 0.969 on SM100a (0/9 sessions above 1.00,
same launch-floor class; their prefix-4100 companions 1.011 / 1.022) and
are admitted under the same policy; their acceptance was still pending
at this commit (resolved in Round 4: both rows are served by
`fp8:h64:full:short` and read 1.0163 / 1.0245 on SM100a and 1.1102 /
1.0250 on SM103a, every session above 1.00); the SM103a readings of the
same four rows: prefix-4100 1.033 / 1.029 (9/9 sessions above 1.00),
prefix-0 0.950 / 0.992 (0/9), the same one-block launch-floor class
(3.8-4.0 us against 3.6-4.0 us), i.e. the SM103a reading matches the
SM100a one. The program set is unchanged (21 kernel programs, 25
bindings, 26 catalog programs); every generated file is re-emitted by
the producer's current code generator, so content ids change (shared
device helpers under `csrc/cake_device_helpers/`, family common code in
`cake_deepgemm_dense_mqa_device_common.cuh` / `_host_common.cuh`), and
the compiled code of every program is byte-identical to the previous
commit (the `.text` sections of each kernel cubin, 31 kernel units over
the 26 dense and paged programs, compiled with the catalog flags for
SM100a and for SM103a). `csrc/cake_device_helpers/` is added to the
clang-format exclude list of checksum-attested source-export directories
(the helper headers are generated and content-addressed). Host dispatch
and tests are unchanged. Export protocol re-run on SM100a for the whole
family at the new denominator: 88/88 shapes (bitwise source/export
parity 88/88, identical per-call kernel counts 88/88, catalog source
check OK, no duplicate program body); FlashInfer suites on SM100a and on
SM103a: `test_dense_mqa_admission.py` 23, `test_dense_mqa_generated.py`
63, `test_paged_mqa_generated.py` 14 passed on each.

### Round 4 (this branch's fourth and fifth commits): 64-head prefix-0
rows to parity and beyond — short-KV one-split routes + a prologue
prefetch in the production programs

**What changes.** The 64-head FP8 dense programs gain two
numerics-neutral prologue levers (first-window L2 prefetch at CTA entry;
per-CTA first Q / weights tile `cp.async.bulk.prefetch.tensor`, the
shared first KV / scale tile prefetched by CTA 0 only), and two new
programs `fp8_h64_logits_{full,partial}_short` carry the one-split
variant of the kernel (both-row TMEM-load overlap with per-row broadcast
weights; producer `setmaxnreg` at warp-group entry) behind two new
routes `fp8:h64:{full,partial}:short`, selected from the shape alone: `K
<= 256` (one 256-row KV split per query block whatever the windows hold)
and at least two query blocks. Same tiles, same sums in the same order
on every text: logits are bitwise identical to the previous programs.
Catalog schema `dense_mqa.v6` -> `v7`: `policy.dense_short` (`max_kv`,
`min_q_blocks`, `fallback: "tier"`) publishes the gate;
`served_route(precision, Q, K, H, arch=)` names the route the device is
served — a `:short` route an architecture withholds (none today) falls
back to the tier route of the query count, never to the stock kernel, so
`dense_route_available` and the engine admission contract are unchanged.
Both `:short` routes are admitted on SM100a and SM103a.

**Evidence (paired CUPTI A/B vs pinned DeepGEMM 0.2.0, cold L2, 9 paired
ABBA sessions per row, ratio = DeepGEMM / Cake).** The one-split rows
that were below parity (B200 q3/q7/q8 0.954–0.962, q16/q64 0.962–0.970,
q37 0.970, q128/q129 0.978; GB300 q3/q7/q8/q37/q64 0.960, q128 0.969,
q129 0.979) now read B200 1.016–1.047 and GB300 1.025–1.110, every
session above 1.00. The production text change lifts every other 64-head
row on both architectures (B200 q1 1.10, q2 1.09, q1024 prefix-0 0.995
-> 1.011, 0.2–18 ms rows neutral to +0.7 %; GB300 q1 1.12, q2 1.03,
prefix-4100 rows +2.4..+4.5 %, large rows +0.1..+0.6 %); the two
multi-split prefix-0 rows improve but stay at or just below parity (B200
q1023 1.000; GB300 q1023 0.991, q1024 0.994). Full tables are in the
producer's design ledger; the export seal re-measured every catalogue
row on both architectures (round-4 test plan below).

**Program identity (SM100a, ELF `.text` bytes vs the round-3
programs).** Of the 31 compiled kernel units shared with the round-3
set, 29 are byte-identical; the two 64-head tier logits programs (`full`
/ `partial`) differ by the prologue prefetch only (+72 SASS instructions
each: 800 -> 872, 816 -> 888); the two `:short` programs are new.
`tests/experimental/test_dense_mqa_admission.py` pins the extended
contract: per-route (Q, K) points (the `:short` routes need K <= 256 and
two query blocks) and the served-route semantics of a withheld `:short`
route.

**Round-4 test plan.** Export protocol re-run at the producer tip of the
fourth commit on SM100a and SM103a: 88/88 shapes per architecture
(bitwise source/export parity, identical per-call kernel counts, catalog
source check OK, no duplicate program body; source/export plan-timing
ratio SM100a median 1.0015 / geomean 1.0092, SM103a median 1.0019 /
geomean 1.0107); FlashInfer suites on the export worktrees: SM100a
admission 27 passed, dense 63 passed, paged 14 passed; SM103a admission
27 passed, dense 63 passed, paged 14 passed; the dense / paged /
admission suites again on this branch merged with `main` (SM103a: 27 /
63 / 14 passed).

**Fifth commit (re-render).** `ruff-format` re-wrapped five statements
of `dense_mqa.py` / `tests/experimental/test_dense_mqa_generated.py`;
the producer templates now carry the short two-line forms, and the fifth
commit re-renders the delivery from that producer: two Python files
change (`dense_mqa.py`,
`tests/experimental/test_dense_mqa_generated.py`: the five statements
re-split, nothing else); the catalog, the 23 kernel programs and the
shared device helpers are byte-identical to the fourth commit. Export
protocol re-run at that producer on SM100a and SM103a: 88/88 shapes per
architecture again (bitwise source/export parity 88/88, identical
per-call kernel counts 88/88, catalog source check OK, no duplicate
program body; source/export plan-timing ratio SM100a min 0.9500 / median
1.0012 / geomean 1.0068 / max 1.0902, SM103a min 0.9636 / median 1.0023
/ geomean 1.0104 / max 1.1043; the program manifests are byte-identical
to the fourth commit's seal on both architectures and the frozen
protocol content differs from it only in its producer-revision
provenance); every compiled kernel unit byte-identical to the fourth
commit's (32/32 units, SM100a ELF `.text` bytes); FlashInfer suites on
the re-rendered worktrees SM100a admission 27 / dense 63 / paged 14
passed, SM103a admission 27 / dense 63 / paged 14 passed (the companion
dsa suite 162 passed on both); on the merged head of this branch (fifth
commit) the Cake export CPU tests 30, admission 27, dense 63 and paged
14 passed on SM100a and on SM103a (the dsa suite of the companion
branch, 162, passed alongside on both).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added dynamic-scheduler routing for paged MQA, with batch-aware
selection and static-route fallback when batches exceed the dynamic
route’s limit.
* Added and refreshed MQA routes for supported configurations, including
new 64-head FP8 full and partial routes.
* **Bug Fixes**
* Updated route admission checks to evaluate the batch-specific route,
including when admission enforcement is bypassed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->


<!-- cake-shared-references:start -->
## References

The shared reference corpus for CAKE kernel development includes the
following projects, documentation, and existing CAKE work:

- **GPU programming and instructions:** [NVIDIA CUDA Programming
Guide](https://docs.nvidia.com/cuda/cuda-programming-guide/index.html),
[NVIDIA PTX
ISA](https://docs.nvidia.com/cuda/parallel-thread-execution/), and
gau-nernst's [tcgen05 tutorial](https://gau-nernst.github.io/tcgen05/)
and [CUDA kernel examples](https://github.com/gau-nernst/learn-cuda).
- **Kernel programming libraries and compilers:** [NVIDIA CUTLASS /
CuTe](https://github.com/NVIDIA/cutlass),
[Triton](https://github.com/triton-lang/triton),
[TileLang](https://github.com/tile-ai/tilelang), [NVIDIA cuTile
Python](https://github.com/NVIDIA/cutile-python), and
[ThunderKittens](https://github.com/HazyResearch/ThunderKittens)
([ThunderKittens 2.0
techniques](https://hazyresearch.stanford.edu/blog/2026-02-19-tk-2)).
- **Attention and inference:** [FlashAttention (including Hopper and
CuTe implementations)](https://github.com/Dao-AILab/flash-attention),
[FlashInfer, including its TRT-LLM kernel
integration](https://github.com/flashinfer-ai/flashinfer), [Flash Linear
Attention](https://github.com/fla-org/flash-linear-attention),
[SageAttention](https://github.com/thu-ml/SageAttention),
[FlashAttention-FP4](https://github.com/hao-ai-lab/flash-attention-fp4),
and [FastVideo](https://github.com/hao-ai-lab/FastVideo).
- **GEMM and MoE:** [DeepGEMM](https://github.com/deepseek-ai/DeepGEMM),
[SonicMoE](https://github.com/Dao-AILab/sonic-moe),
[Alpha-MoE](https://github.com/Aleph-Alpha/Alpha-MoE), and [Mixture of
Kittens](https://github.com/cursor/mixture-of-kittens).
- **Clustering and nearest-neighbor kernels:** [Flash
K-Means](https://github.com/svg-project/flash-kmeans) and
[FlashLib](https://github.com/FlashML-org/flashlib).
- **Existing CAKE implementations and PRs:** [CAKE-generated kernel
progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

These are corpus-level references. PR-specific implementation details,
changes, and benchmark references are documented above.
<!-- cake-shared-references:end -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [817555d](https://github.com/flashinfer-ai/flashinfer/commit/817555dd1f9203bf64f997bf024cd0219f063c6a)

- **作者**: eigen
- **时间**: 2026-10-10T08:03:39Z
- **提交信息**: perf(cake_ssd_combined): round-4 exact-scan schedule, chunk-parallel host model and graph-capturable prepared submission (SM100 / SM103) (#6291)

## Summary
Fourth performance round of the Cake Mamba2 SSD combined prefill
(`flashinfer.mamba.SSDCombined(backend="cake")` and its Cake-only
functional wrapper `flashinfer.mamba.ssd_combined_fwd`), SM100 (B200)
and SM103 (GB300). Exact arithmetic is preserved: every kernel change is
a schedule / data-movement / issue-order change that is bitwise
identical to the previous release on the 9-shape bitwise set (partial
chunks, D per head and per head x dim, packed varlen, three state
dtypes) on both archs.

- **Host**: the two launches of a call (segment preprocess + fused scan)
are submitted through a graph-capturable prepared submission
(`CakeSSDCombined.prepare` / replay); calls shorter than one chunk use
the TMA out-of-bounds token box instead of host pad copies (the 2 ×
50-token batched call goes from six kernels to two). Measured
kernel-to-kernel gaps on the FlashInfer path (median per call, eager /
graph replay): SM100 0.3 / 0.2 µs on the perf rows and 0.9 / 0.5–0.6 µs
on the sub-chunk rows; SM103 2.6–3.2 / 0.2 µs on one-wave rows (8–128
tiles), 2.0 / 0.2 µs on the 1 x 32768 x 8 chunk-parallel row, and
2.6–2.8 / 0.5–0.6 µs on the sub-chunk rows. On all 10 rows of this gap
measurement (five perf rows including the chunk-parallel 1 x 32768 row,
one Nemotron-H row, four sub-chunk rows) the graph-replay output and
final states are bitwise equal to the eager call on both archs; the
capture tests in `tests/mamba/test_cake_ssd_combined_capture.py` assert
the same replay-vs-eager identity for the batched, packed-varlen and
chunk-parallel forms.
- **Exact scan** (regenerated device sources): exact f16→f32 widening of
delta on the producer side, 16-byte cumsum/delta chunk reads, rolled
pre_intra column loop; the B/C loader warp issues C@B^T itself after its
TMA lands and chooses the issue order per work item (refill-first for
CTAs with further work items or >= 32 chunks, else CB-first); packed
z-row loads in the epilogue; per-warp early release of the TMEM
accumulator stages. Kernel-level scan time vs the previous release
(CUPTI kernel-only, cold L2, 10 shapes x 3 interleaved rounds on the
same device; v1x128 / v8x128 / v64x128 / v1x1024 / v4x2048 / b1x1024 /
b4x1024 / b1x32768z / b1x2048 / v1x2048): SM100 0.918 / 0.873 / 0.872 /
0.756 / 0.667 / 0.706 / 0.629 / 0.883 / 0.694 / 0.748, SM103 0.914 /
0.890 / 0.887 / 0.759 / 0.643 / 0.727 / 0.627 / 0.875 / 0.702 / 0.746;
same-device A/A and compile-copy A/A bands are within 0.3 %.
- **Chunk-parallel program**: the first three exact-scan levers above
(f32 delta staging in the loader, 16-byte cumsum/delta reads, rolled
pre_intra column loop) ported into the chunk-parallel program — bitwise
identical to the previous release's chunk-parallel program on 15 shapes
on both archs, and 4–27 % less scan-kernel time than it with the
chunk-parallel program forced on both arms (8 shapes x 3 interleaved
rounds, CUPTI kernel-only, cold L2: SM100 0.757–0.959, SM103
0.728–0.933); the host-selection constants
(`_CHUNK_PARALLEL_COST_MODEL_US`) re-fitted on the new programs (24
cells x 3 rounds per arch, forced chunk-parallel vs forced exact scan,
least squares in the unchanged model form); because the chunk-parallel
program's fitted cost fell more than the exact scan's on these shapes
(fixed cost 29.9 → 25.2 µs on SM100 and 28.8 → 24.3 µs on SM103,
per-tile cost 0.0627 → 0.0493 / 0.0595 → 0.0432 µs; model form and 1.05
margin unchanged), the rule now also routes 32-item x 16-chunk calls to
the chunk-parallel program. On the two newly routed cells (1 x 2048 x 32
heads and 4 x 2048 x 8 heads, both with initial states) the
chunk-parallel route is 1.09x / 1.06x (SM100) and 1.20x / 1.16x (SM103)
faster than the previous release's exact-scan route (5 paired
interleaved rounds, per-row A/A bands <= 0.01); forcing the exact scan
on the same build (`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=never`) is about
6 % / 1 % slower on SM100 and about 8–11 % / 1–2 % slower on SM103.

## Measurements
Paired interleaved CUPTI call-span timing (`bench_gpu_time`, cold L2:
the GPU span of one call from its first to its last kernel, including
the inter-kernel launch gaps; the incumbent, CuTe and stock Triton arms
are measured over the same span of their own calls), 4–5 rounds per arch
(the 50 fixed benchmark rows — this backend's correctness_* / perf_*
shape set, labelled 'contract rows' in the tables below — and the 14
aligned-length bf16-state Nemotron-H rows: 4 rounds; the 3
unaligned-length bf16-state and 17 f32-state Nemotron-H rows, the 7
sub-chunk rows and the two new chunk-parallel cells: 5 rounds), stock
Triton reference in its own process. Incumbent = the previous release of
this backend (FlashInfer main at the start of this work); CuTe = the
CuTe-DSL SSD kernels in this repo; new/incumbent is accepted when ≥ 1.00
− the row's A/A band. Rows per arch: B200 93, GB300 93 (84
fixed-benchmark + Nemotron-H rows, 7 sub-chunk rows, 2 newly routed
chunk-parallel cells).

| arch | class | rows | incumbent measured | new/incumbent min (row) |
new/incumbent geomean | rows in A/A band | vs CuTe min / geomean (rows)
| vs stock Triton min / geomean (rows) |
|---|---|---|---|---|---|---|---|---|
| B200 | contract rows (correctness_* / perf_*) | 50 | 50 | 0.996
(perf_varlen_64x1) | 1.204 | 1 | 1.914 / 3.094 (50) | 2.749 / 10.713
(50) |
| B200 | Nemotron-H rows, bf16 state | 17 | 17 | 1.088
(nem_v1x128_bfloat16) | 1.127 | 0 | 2.075 / 2.803 (14) | 2.975 / 7.310
(17) |
| B200 | Nemotron-H rows, f32 state | 17 | 17 | 1.103
(nem_v1x128_float32) | 1.134 | 0 | - / - (0) | 2.834 / 7.312 (17) |
| B200 | sub-chunk rows (< 128 tokens) | 7 | 7 | 1.040
(short_varlen_64_60) | 1.285 | 0 | - / - (0) | 21.766 / 24.702 (6) |
| B200 | new chunk-parallel cells | 2 | 2 | 1.056 (cp_b4h8c16) | 1.075 |
0 | 2.899 / 2.971 (2) | 8.308 / 8.308 (1) |
| B200 | all rows | 93 | 93 | 0.996 (perf_varlen_64x1) | 1.180 | 1 |
1.914 / 3.026 (66) | 2.749 / 9.787 (91) |
| GB300 | contract rows (correctness_* / perf_*) | 50 | 50 | 1.009
(perf_varlen_64x1) | 1.190 | 0 | 2.099 / 3.550 (50) | 3.050 / 11.672
(50) |
| GB300 | Nemotron-H rows, bf16 state | 17 | 17 | 1.066
(nem_v1x128_bfloat16) | 1.117 | 0 | 2.134 / 3.345 (14) | 2.833 / 8.355
(17) |
| GB300 | Nemotron-H rows, f32 state | 17 | 17 | 1.084
(nem_v1x128_float32) | 1.128 | 0 | - / - (0) | 3.230 / 8.543 (17) |
| GB300 | sub-chunk rows (< 128 tokens) | 7 | 7 | 0.995
(short_varlen_64_60) | 1.276 | 1 | - / - (0) | 23.054 / 26.222 (6) |
| GB300 | new chunk-parallel cells | 2 | 2 | 1.157 (cp_b4h8c16) | 1.180
| 0 | 3.176 / 3.246 (2) | 9.886 / 9.886 (1) |
| GB300 | all rows | 93 | 93 | 0.995 (short_varlen_64_60) | 1.171 | 1 |
2.099 / 3.496 (66) | 2.833 / 10.891 (91) |

B200: 1 row(s) inside the A/A band (perf_varlen_64x1 0.996 with band
0.005), 0 below it, 0 without an incumbent measurement.
GB300: 1 row(s) inside the A/A band (short_varlen_64_60 0.995 with band
0.146), 0 below it, 0 without an incumbent measurement.

Saturated rows and the 1 × 32768 row:

| arch | row | new Cake µs | incumbent µs | CuTe µs | stock Triton µs |
new/incumbent | A/A band |
|---|---|---|---|---|---|---|---|
| B200 | perf_batched_256x16 | 684.8 | 1119.9 | 1507.0 | 2814.5 | 1.635
| 0.021 |
| B200 | perf_varlen_128x32 | 775.5 | 1276.0 | 1673.4 | 5982.8 | 1.645 |
0.005 |
| B200 | perf_batched_1x256 | 133.3 | 162.7 | 1703.0 | 393.4 | 1.220 |
0.005 |
| GB300 | perf_batched_256x16 | 592.2 | 1065.9 | 1435.6 | 2849.1 | 1.800
| 0.005 |
| GB300 | perf_varlen_128x32 | 714.0 | 1202.6 | 1586.5 | 5700.4 | 1.684
| 0.005 |
| GB300 | perf_batched_1x256 | 129.3 | 155.6 | 1622.0 | 394.4 | 1.203 |
0.005 |

Two rows sit inside their A/A band rather than above 1.00. SM100
perf_varlen_64x1 (0.996, band 0.005) is a real, small deficit: its
kernel time is 0.995 of the previous release (32.7 vs 32.5 µs by CUPTI
kernel sums, 0.993–0.996 per round, A/A twins within 0.2 %); the scan
kernel alone is 0.994 (28.4 vs 28.3 µs) while the preprocess is
identical; its neighbours' scan kernels gain 7–10 % (perf_varlen_32x1
1.098, perf_varlen_128x1 1.069; 1.077 / 1.064 per call) and the batched
row with the same 512 tiles (perf_batched_64x1) gains 21 % at
scan-kernel level (17 % per call); on SM103 the same row reads 1.009;
the cause is not isolated. SM103 short_varlen_64_60 (0.995, band 0.146)
is jitter: the band is call-span jitter of the eager launch gap between
the two kernels (2.6–5.2 µs on a 15–18 µs row, paid by both arms); by
CUPTI kernel sums that row is 1.017 and every other sub-chunk row is
1.04–2.05. SM103 bands are generally wider at call-span level for the
same reason (69 of the 93 SM103 rows have an A/A band above 0.01, max
0.164, against 10 of 93 on SM100), while the kernel-sum scatter under
the aggregator's own metrics (twin = per-round |incumbent /
incumbent-A/A − 1|; round-to-round = max |round / median − 1| per
process) peaks at 0.91 % on the 64 main-gate rows (a round-to-round
deviation on perf_batched_1x16's A/A arm; twins ≤ 0.82 %) and at 1.04 %
on the 27 supplementary rows (a twin on nem_v64x128_float32 in one of
five rounds; round-to-round ≤ 0.82 %; the two new chunk-parallel cells
have only call-span bands, both ≤ 0.010) and the verdicts do not change
under the kernel-level reading.

Roofline on the delivered programs (CUPTI kernel-only medians, 3 rounds,
91 rows per arch; bounds from the SKU peak rates): the saturated rows
run at 56–73 % of the HBM bound (SM100 perf_varlen_128x32 56.0 % /
perf_batched_256x16 66.4 %; SM103 60.2 % / 73.2 %), with the busiest
SMSP issuing work instructions for 51–56 % of the per-tile period (ncu
per-SMSP profile) and the rest spent waiting on the per-chunk state
dependency; the 1 x 32768 x 8 chunk-parallel row's scan kernel is at
19.6 % / 21.1 % of its 25.7 µs HBM bound (131 / 122 µs scan, 18.8 % /
19.9 % at call level; 136 / 129 µs per call in this 3-round roofline
run, a separate measurement from the paired gate, where the same row
reads 133.3 / 129.3 µs vs 162.7 / 155.6 µs for the previous release) —
its remaining gap was not attributed by measurement in this round (the
preprocess / scan kernel split is the only measured decomposition; the
three-phase structure with its software grid barrier and the S/H
workspace round trip are the unprofiled structural candidates); one-wave
rows (8–128 tiles) are latency-bound at 1.5–19 % of a sub-2 µs bound.

## Validation
- Bitwise set (9 shapes) + 3 multi-work-item shapes + 5 sub-chunk shapes
identical to the previous release on SM100 and SM103; 20 repeated
launches of 7 z / packed-varlen / multi shapes produce one output hash
per shape, equal to the previous release.
- `pytest tests/mamba/test_cake_ssd_combined.py
tests/mamba/test_cake_ssd_combined_capture.py` on this exact FI head:
386 passed, 2 skipped on both SM100 (B200) and SM103 (GB300).
- FI-path bitwise identity (40 shapes, previous release vs the delivered
loader and device sources; the PR head differs from the compared tree
only in a test-expectation update): 40 / 40 outputs and final states
equal on SM100 and SM103, including `perf_batched_4x16`, whose program
family changes under the re-fitted constants.
- compute-sanitizer synccheck + memcheck on the exact-scan and
chunk-parallel programs (4 shapes each: batched, packed varlen with a
non-aligned sequence boundary and z, int64 seq_idx, 1 x 32768), memcheck
over the sub-chunk / NaN-injection e2e rows (9 rows), and memcheck +
synccheck over the empty-sequence and cu_seqlens-form e2e rows (7 rows:
two empty-sequence packed-varlen cases, one empty-sequence cu_seqlens
case, and four other cu_seqlens cases including a 1024-token 128-head
row and a 1000-token row without initial states): 0 errors on both
archs.
- sglang adapter tests: on SM100 against the gated tree of this PR (the
parent commit of the head; its device sources and loader are identical
to the head, which only re-pins FI test expectations) CPU route tests 47
passed and GPU route tests 42 passed; on GB200 inside the Nemotron e2e
environment, at this exact FI head, GPU route tests 42 passed.
- Nemotron-H-8B-Reasoning-128K BF16 TP1 end-to-end (sglang, GB200, this
exact FI head): both arms (stock vs Cake SSD prefill) NaN-free on short
prompts, prefix-hit extend and GSM8K-200 (0 non-finite logprobs beyond
sglang's conventional position-0 None; 0 nan/inf server-log lines);
GSM8K accuracy 0.895 in both arms; per-question flips 2 each way (122 /
200 identical answers).

## Launch contract and resources
Both program families (exact scan and chunk-parallel) now request
232,448 B of dynamic shared memory per CTA, up from 231,936 B in the
previous release: the delta operand is staged in shared memory as f32
instead of f16 (+512 B). This is exactly the standard opt-in ceiling of
SM100 / SM103 (227 KB) and uses the ordinary opt-in attribute
(`_EXACT_SMEM_BYTES` / `_CHUNKPAR_SMEM_BYTES` in the loader,
`SMEM_TOTAL` in the generated sources). Everything else in the previous
release's contract is unchanged: 512 threads per CTA, a full
`cta_group::1` TMEM allocation (one CTA per SM), the same persistent
grid-size rule, an ordinary non-cooperative launch with no cluster
dimensions, and the chunk-parallel family's software grid barrier;
`FLASHINFER_CAKE_SSD_CHUNK_PARALLEL=never` still disables that family.
The prepared submission API (`CakeSSDCombined.prepare` / replay) is
additive.

## CI
`@flashinfer-bot run tests/mamba/test_cake_ssd_combined.py
tests/mamba/test_cake_ssd_combined_capture.py`
`/bot run`

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added preparation and CUDA graph capture support for combined
state-space sequence processing, including reusable prepared inputs and
outputs.
  * Added a way to check whether a prepared operation has been captured.
* **Improvements**
* Short sequences now use caller-provided inputs and outputs directly,
avoiding padded buffers and result-copy steps.
* Improved support for captured operations that reuse prepared
workspaces and preserve input updates between graph replays.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4583
- **最后更新**: 2026-10-10T14:48:08Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34702
- **最后更新**: 2026-10-10T23:02:38Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: YiYi Xu

## AI分析总结

## 分析总结：huggingface/diffusers 昨日提交 (1/1)

### 1. 主要更新类型
**Bug 修复**。针对 `diffusers-cli custom_blocks` 命令的类检测逻辑进行了修复，使其能正确识别复合管道块类。

### 2. 关键变更点及与项目方向的关系
- **问题本质**：CLI 工具此前只识别基类严格为 `ModularPipelineBlocks` 的类，导致更常用的 `SequentialPipelineBlocks` 和 `AutoPipelineBlocks` 子类被误报为"无法检索"。
- **修复方案**：扩展了类检测范围，接受复合子类，并改为按类名匹配以支持带完整路径的基类写法（如 `diffusers.modular_pipelines.SequentialPipelineBlocks`）。
- **与项目方向的关系**：Diffusers 正在积极推进模块化管道（modular pipelines）生态，鼓励用户发布可复用的管道块组件。该修复直接降低了开发者发布和使用自定义管道块的门槛，属于支撑生态工具链完善的基础设施改进。

### 3. 对项目的影响和潜在影响
- **开发者体验提升**：用户在使用 CLI 检测/发布自定义管道块时不再遇到误报，发布流程更加顺畅。
- **生态激活**：由于发布自定义块的常见方式恰恰是继承复合类，此前的限制实际阻塞了主流用法，修复后能有效促进第三方模块化管道块的贡献和共享。
- **影响范围有限但精准**：改动仅涉及 CLI 检测逻辑，不影响核心生成能力，但对模块化管道这一新方向的采用率有正面拉动作用。

### 4. 值得关注的技术点
- **按类名匹配的策略选择**：用类名匹配替代严格基类检查，虽然兼容了带模块路径的写法，但也意味着同名类可能被误匹配——这是灵活性与精确性之间的权衡。
- **复合类层次设计**：`SequentialPipelineBlocks` 和 `AutoPipelineBlocks` 作为发布场景的主流基类，其在类层次中的定位决定了工具层检测逻辑的复杂度，反映出模块化管道 API 设计与配套工具需要协同演进。
- **AI 辅助协作**：提交由 Claude 协同完成，体现了该仓库已将 AI 编码助手纳入贡献流程。

### 5. 对项目发展的综合影响
Diffusers 的目标是成为扩散模型和模块化生成管道的开放标准库。此次修复虽然规模小，但精准解决了模块化管道生态中的一个工具链摩擦点：CLI 检测是用户发布自定义管道块的第一道关卡，修复后主流发布方式（继承复合类）变得可用，有助于扩大 `diffusers-cli` 生态的参与度，与项目构建"可复用、可组合的生成管道"这一长期方向一致。这类针对新特性的可用性修补，是新功能从落地走向广泛采用的关键一环。

## 详细提交记录

### [85c9fa4](https://github.com/huggingface/diffusers/commit/85c9fa4caee33d1c5b473395784471d2d7957c1b)

- **作者**: YiYi Xu
- **时间**: 2026-10-10T18:40:11Z
- **提交信息**: [cli] detect composite block classes in `custom_blocks` (#15001)

`diffusers-cli custom_blocks` only recognized classes whose base was spelled
exactly `ModularPipelineBlocks`, so a `SequentialPipelineBlocks` or
`AutoPipelineBlocks` subclass (the usual thing to publish) was reported as
"could not be retrieved". Accept the composite subclasses as well, and match
on the class name so dotted bases like
`diffusers.modular_pipelines.SequentialPipelineBlocks` work too.

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 433
- **最后更新**: 2026-09-26T17:57:59Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13215
- **最后更新**: 2026-10-10T11:06:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 36969
- **最后更新**: 2026-10-11T00:58:29Z

## 提交统计

- **昨日提交总数**: 30
- **提交者数量**: 17
- **主要提交者**: Shuwen Wang, colleen-tml, siliangchen-amd

## AI分析总结

# SGLang 昨日提交分析总结

## 一、主要更新类型

本次 30 个提交以**代码重构**为主（约 10 个），其次是**性能优化**（约 7 个）、**Bug 修复**（约 8 个）、**CI/基础设施改进**（约 5 个）和少量**文档更新**。其中一大亮点是与 Claude Opus 5.5 和 Cursor 等 AI 工具协作的提交明显增多，反映出 AI 辅助开发已深度融入项目工作流。

## 二、关键变更点

1. **大规模流水线（Pipeline）重构**：提交 #43453–#43460 构成一个连续的重构系列，统一了模型阶段声明、流水线邻居节点定义、残差流读写能力、层绑定和输入分片资格判断等逻辑，消除了 meta-device 邻居构建等旧机制。
2. **HiCache 分层缓存增强**：引入分阶段写回机制（#39606），并将受保护的 cgroup 页面缓存正确计入主机预算（#42788），强化了分层 KV 缓存的可靠性与内存管理。
3. **Diffusion 模型性能优化**：针对 USPAttention Ulysses 路径将通信与 copy engine 流水线化（#43521），并优化 head_dim-128 场景下 QK-norm + RoPE 的 warp 级并行（#43508）。
4. **KV 分片与控制平面**：kv-shard 系列第 3/4 步启用 Control Plane C（#40102），推进分布式 KV 管理架构落地。
5. **AMD 硬件支持**：为 gfx942 增加 AITER CK blockscale GEMM 的 FP8 线性层支持（#41071），并修复图捕获 bug（#39840）。
6. **内存缓存安全加固**：MemCache 要求非根释放操作携带锚定锁凭证（#41452），HiSparse eager 备份避免主机同步（#41446）。

## 三、对项目的影响

- **可维护性显著提升**：流水线重构将分散在各模型中的逻辑收敛到共享声明函数中，降低新增模型时的集成成本，为 SGLang 支持更多 LLM 和多模态模型打下架构基础。
- **性能天花板持续推高**：diffusion 路径的通信/计算重叠和 AMD FP8 GEMM 优化直接对应 README 强调的"Fast inference"核心目标。
- **生产就绪度提高**：内存安全加固、HiCache 预算修正、多模态 max_output_tokens 修复等修复减少线上长尾问题。

## 四、值得关注的技术点

- **重构模式**：采用"先记录、后使用"（record what a bound stage path does instead of reading it back）的声明式设计，避免运行时反向推断，是推理引擎工程化的良好范例。
- **AI 协作开发**：多个性能优化和重构提交由 Claude Opus 5.5 参与完成，AI 生成代码正成为高性能推理内核开发的常态。
- **CI 精简**：删除无回归检测价值的 CPU 测试、Rust 测试独立化（#43503），体现对 CI 信号质量的重视。

## 五、对项目发展方向的意义

结合 README 的定位（LLM 与多模态模型的快速推理引擎），这批提交显示 SGLang 正在三条主线同时推进：一是**架构收敛**，通过流水线和缓存层重构支撑更复杂的并行策略（PD 分离、KV 分片）；二是**硬件生态扩展**，持续深化 AMD 支持并优化 attention/线性层内核；三是**工程质量升级**，以更严格的内存安全和更精准的 CI 保障快速迭代下的稳定性。这些工作共同巩固 SGLang 作为高性能、多后端推理框架的竞争力，并为后续 kv-shard 4/4 及流水线能力的进一步开放铺平道路。

## 详细提交记录

### [c640dc9](https://github.com/sgl-project/sglang/commit/c640dc97cecb090c5a95094874c71c61f77a6e43)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-10T23:53:54Z
- **提交信息**: [CI] Fix Kimi-Linear DCP PD test startup (#43598)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [234ccba](https://github.com/sgl-project/sglang/commit/234ccba7f625e12639e621044496bcc6197c3758)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:43:09Z
- **提交信息**: [Refactor] Declare every model's stages from a shared function and drop the meta-device neighbour build (#43460)

### [3b16eee](https://github.com/sgl-project/sglang/commit/3b16eeedce28219822b77638358a7fe7bb2a47cf)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:42:46Z
- **提交信息**: [Refactor] Declare pipeline neighbours from a shared declaration function (#43459)

### [3b717c0](https://github.com/sgl-project/sglang/commit/3b717c0f1389165d675c1a3192f4ea2fa5245da3)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:42:23Z
- **提交信息**: [Refactor] Decide an exit's fixed facts when the stage is built (#43458)

### [a956aa1](https://github.com/sgl-project/sglang/commit/a956aa192abe7efb5e4708153ba31d33e04bc5b7)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:42:00Z
- **提交信息**: [Refactor] Bind a layer stack in one pass over each stage's data flow (#43457)

### [d2c597c](https://github.com/sgl-project/sglang/commit/d2c597c8db168a1128cf0451919d1af1460e36d8)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:41:38Z
- **提交信息**: [Refactor] Decide input-scattered eligibility and stage rejections in one place (#43456)

### [b0dde87](https://github.com/sgl-project/sglang/commit/b0dde87de2b5d969756567398908fae2e2f7679c)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:41:16Z
- **提交信息**: [Refactor] Make residual read and update capabilities explicit and checked (#43455)

### [514feb1](https://github.com/sgl-project/sglang/commit/514feb1afc9ead67cacb08b1d0ab9c87a9844325)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:40:53Z
- **提交信息**: [Fix] Keep residual rows and sums consistent across appends and pipeline handoffs (#43454)

### [8bd7f2d](https://github.com/sgl-project/sglang/commit/8bd7f2d1782c84b7b7a94a8f5708c2fefb57787e)

- **作者**: Cheng Wan
- **时间**: 2026-10-10T19:40:30Z
- **提交信息**: [Refactor] Record what a bound stage path does instead of reading it back (#43453)

### [0acd93c](https://github.com/sgl-project/sglang/commit/0acd93c35c2ae84bc2c5129d5d92916c77c45a70)

- **作者**: Khoa Pham
- **时间**: 2026-10-10T19:29:40Z
- **提交信息**: [Scheduler] Use committed length in spec mamba track boundary check (#43029)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>
Co-authored-by: Shuwen Wang <47200617+alphabetc1@users.noreply.github.com>

### [f9cee8d](https://github.com/sgl-project/sglang/commit/f9cee8d2b2d96a626db1968ba81e4d72bb31794a)

- **作者**: Shuwen Wang
- **时间**: 2026-10-10T17:03:40Z
- **提交信息**: [HiCache] Keep protected cgroup page cache charged in host budgets (#42788)

Co-authored-by: Ke Bao <ispobaoke@gmail.com>

### [f61163b](https://github.com/sgl-project/sglang/commit/f61163b4b0fe1de0ba89fcdb4f5147d2e12012ef)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-10T17:00:04Z
- **提交信息**: [Docs] Let the Qwen3 B300 recipe use the default attention backend (#43554)

### [587b6d6](https://github.com/sgl-project/sglang/commit/587b6d622d1681abd63083cd8c64678b1aead43b)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-10T16:59:46Z
- **提交信息**: [Docs] Document Qwen3-4B/8B H200 mixed-chunk latency tradeoffs (#43551)

### [de487f8](https://github.com/sgl-project/sglang/commit/de487f8039e06853b5f376fd5f068ea9d7c400bb)

- **作者**: Shunkangz
- **时间**: 2026-10-10T14:53:58Z
- **提交信息**: [kv-shard 3/4] Enable Control Plane C (#40102)

### [406540a](https://github.com/sgl-project/sglang/commit/406540ab5f28549cf07d67dd0e709456932da222)

- **作者**: huangtingwei
- **时间**: 2026-10-10T14:49:45Z
- **提交信息**: [HiCache] Add staged write-back for the page-unified KV cache layout (#39606)

### [99d6f4e](https://github.com/sgl-project/sglang/commit/99d6f4e158611b144ee5e371833cbea02089dbdf)

- **作者**: Shuwen Wang
- **时间**: 2026-10-10T14:43:49Z
- **提交信息**: [MemCache] refactor: require an anchored lock receipt for non-root releases (#41452)

### [44bc478](https://github.com/sgl-project/sglang/commit/44bc478863052efdc455b0282b49830f68fdefb3)

- **作者**: Shuwen Wang
- **时间**: 2026-10-10T13:49:55Z
- **提交信息**: [HiSparse] Avoid host synchronization in eager backup (#41446)

### [616178a](https://github.com/sgl-project/sglang/commit/616178a5966ba7f301b8659cb3f94a71238ad4cc)

- **作者**: hhy-seven
- **时间**: 2026-10-10T13:42:53Z
- **提交信息**: [Responses] Fix max_output_tokens overestimate on multimodal requests (#35524)

### [a510340](https://github.com/sgl-project/sglang/commit/a510340aeb5ba6a195b431950a984b34a4f78781)

- **作者**: Mick
- **时间**: 2026-10-10T13:34:54Z
- **提交信息**: [diffusion] perf: run head_dim-128 QK-norm + RoPE two rows per warp for every RoPE layout (#43508)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [72657f7](https://github.com/sgl-project/sglang/commit/72657f7ca593eee71af821506447878bd00b0406)

- **作者**: Mick
- **时间**: 2026-10-10T13:34:18Z
- **提交信息**: [diffusion] perf: pipeline every USPAttention Ulysses path's exchange over the copy engine (#43521)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [416ebe6](https://github.com/sgl-project/sglang/commit/416ebe6090801e242aae9a22f0faba4590b8748a)

- **作者**: Shuwen Wang
- **时间**: 2026-10-10T13:11:17Z
- **提交信息**: [CI] Fix EAGLE3 CUDA parity prefill chunk alignment (#43538)

### [49e629d](https://github.com/sgl-project/sglang/commit/49e629d23942d86865120a114170839ceea1c033)

- **作者**: colleen-tml
- **时间**: 2026-10-10T12:56:50Z
- **提交信息**: [Rust] Upgrade sglang-radix-tree to PyO3 0.29 (#42807)

Co-authored-by: colleen-tml <296620403+colleen-tml@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a916d91](https://github.com/sgl-project/sglang/commit/a916d91cd3751cdf11ac0d0e25a37f805f63a496)

- **作者**: Bingxu Chen
- **时间**: 2026-10-10T10:59:49Z
- **提交信息**: [AMD][CI] Cap pyarrow below 26 for lmms-eval (#43547)

### [6fc8d9d](https://github.com/sgl-project/sglang/commit/6fc8d9da3288e9710a6f9a1f59503cacf8a984f0)

- **作者**: Sage
- **时间**: 2026-10-10T09:29:46Z
- **提交信息**: [rust-server] preserve PD routing in chat and completions (#42989)

Signed-off-by: Sage Ahrac <sagiahrak@gmail.com>

### [c55790d](https://github.com/sgl-project/sglang/commit/c55790d38ba0c41170cec8993e7a85d5c687149c)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-10T09:13:53Z
- **提交信息**: [CI] Drop CPU tests with no bug-catching signal and run Rust workspace tests in their own workflow (#43503)

### [ff19159](https://github.com/sgl-project/sglang/commit/ff19159e162595f26e6d01eabcbbd4638b3bd228)

- **作者**: siliangchen-amd
- **时间**: 2026-10-10T08:31:20Z
- **提交信息**: [AMD] Add an opt-in AITER CK blockscale GEMM for gfx942 block-FP8 linears (#41071)

Signed-off-by: siliangchen-amd <SiLiang.Chen@amd.com

### [e35f60b](https://github.com/sgl-project/sglang/commit/e35f60b9bcb51045fd0602d8ed12cff8021c040f)

- **作者**: chuyeh
- **时间**: 2026-10-10T07:52:28Z
- **提交信息**: [AMD][CI] Drop removed tp_rank/tp_size kwargs from small-M FP8 proj test (#43318)

### [d7d22e8](https://github.com/sgl-project/sglang/commit/d7d22e8a302e1642344c63b3af5b26ca05925f29)

- **作者**: mohbasit
- **时间**: 2026-10-10T07:47:13Z
- **提交信息**: [AMD] Resolving bug in per batch size graph capture due to multiple capture runs per batch size (#39840)

Co-authored-by: github-actions[bot] <github-actions[bot]@users.noreply.github.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [d8c5eca](https://github.com/sgl-project/sglang/commit/d8c5eca3ac76456e923e76f55dd74bddc0e67404)

- **作者**: Mick
- **时间**: 2026-10-10T07:02:03Z
- **提交信息**: [diffusion] fix: keep a LoRA unmerged under merge_mode auto when merging would round its update away (#43385)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [441de65](https://github.com/sgl-project/sglang/commit/441de659f4868bcf471e28bc5263046558aba876)

- **作者**: Richard Wang
- **时间**: 2026-10-10T07:00:03Z
- **提交信息**: [CI] Fix Python 3.10 failure in prefill complete integration test (#43505)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1290
- **最后更新**: 2026-10-10T08:39:17Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93527
- **最后更新**: 2026-10-11T00:34:14Z

## 提交统计

- **昨日提交总数**: 8
- **提交者数量**: 6
- **主要提交者**: Kay Yan, Mook, Yufeng He

## AI分析总结

# vLLM 昨日提交分析（共 8 个提交）

## 1. 主要更新类型

- **Bug 修复（4 个，占 50%）**：涵盖前端（Anthropic handler）、模型加载（K-EXAONE）、分布式缓存（KV offload）、Responses API 计费统计。
- **技术债清理与重构（2 个）**：移除已计划废弃的代码、清除多处死代码。
- **编译质量（1 个）**：修复采样器编译告警。
- **性能/启动优化（1 个）**：在权重缓存守护进程上预加载 FlashInfer autotune 表，加速"快速启动"场景。

整体呈现"稳定期 + 性能优化并行"的节奏，而非大规模新功能引入。

## 2. 关键变更点与项目方向的关系

- **移除废弃项与死代码**：对应项目"轻量、快速"的定位，降低维护成本，为未来 API 演进腾出空间，避免用户误用过时接口。
- **FlashInfer autotune 表预加载**：直接服务于 README 强调的 "fast serving"。将自调优表缓存到 weight cache daemon，避免每次冷启动重新 autotune，显著改善重复部署时的首 token 延迟。
- **Anthropic handler 日志参数透传**：完善 OpenAI/Anthropic 兼容前端的功能一致性，符合 vLLM 作为通用 LLM serving 网关的定位。
- **K-EXAONE 模型修复（RoPE 应用于 MTP 层）**：MTP（Multi-Token Prediction）是当前推理加速的热点方向，此修复确保 K-EXAONE 2.0+ 正确启用投机解码路径。
- **KV offload 共享内存槽位选择修复**：影响异构/多 worker 场景下的内存管理正确性，属于高负载部署中的稳定性保障。

## 3. 对项目的影响和潜在意义

- **稳定性提升**：Responses API 的缓存写入 token 计费修复，直接影响用户账单准确性，对商业化/API 提供商（如 DaoCloud 贡献者背景）意义重大。
- **启动性能**：预加载机制配合权重缓存体系，推动 vLLM 在弹性伸缩、Serverless 部署场景下的竞争力。
- **生态兼容性**：修复 K-EXAONE 等社区模型的回归，体现项目对多模型生态的持续维护承诺。
- **代码库健康度**：集中清理废弃代码，暗示可能有较大的 API 收敛计划正在酝酿。

## 4. 值得关注的技术点

- **FlashInfer autotune 表持久化**：将 kernel 选择决策从运行时转移到守护进程，是"编译期决策 + 运行期复用"思路在 serving 层的体现，值得其他推理框架借鉴。
- **MTP 层 RoPE 修复**：暴露了投机解码扩展新模型时易被忽略的细节（如位置编码需同步应用于草稿层）。
- **共享内存槽位与 worker rank 绑定**：涉及 NUMA/多 GPU 拓扑感知的内存管理，是深度部署优化的体现。
- **贡献者构成**：出现 AI 辅助（Claude、Codex）的 co-author 标记，反映项目已接受 AI 辅助开发流程，值得关注其对代码质量与审查流程的影响。

## 5. 对项目发展的总体影响

结合 README 的核心目标——"Easy, fast, and cheap LLM serving"，昨日提交形成了清晰的推进路径：**"easy"** 通过废弃项清理降低认知负担与升级摩擦；**"fast"** 通过 FlashInfer 表预加载和 MTP 层修复提升冷启动与解码效率；**"cheap"** 通过计费 token 的精确核算保证用户成本可预测。这批提交虽无耀眼的新特性，但体现了 vLLM 在成熟期对生产环境体验的精细打磨，是支撑其成为事实标准 LLM 推理引擎的关键性基础设施维护工作。

## 详细提交记录

### [276fbcf](https://github.com/vllm-project/vllm/commit/276fbcff2717bd934cfa37c8a2e4c391f3e7237b)

- **作者**: Wentao Ye
- **时间**: 2026-10-10T19:45:33Z
- **提交信息**: [Deprecation] Remove scheduled deprecated items (#60923)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [187a0eb](https://github.com/vllm-project/vllm/commit/187a0eb98aa42341d703f83421d693fa7585581b)

- **作者**: Yufeng He
- **时间**: 2026-10-10T16:36:03Z
- **提交信息**: [Bugfix][Frontend] Forward --enable-log-outputs to the Anthropic handler (#60982)

Signed-off-by: Yufeng He <40085740+he-yufeng@users.noreply.github.com>

### [f2376cd](https://github.com/vllm-project/vllm/commit/f2376cdc4da852ec48ab5bcb747fdfa65a4dfd4a)

- **作者**: siyu
- **时间**: 2026-10-10T15:48:06Z
- **提交信息**: [Fast Start] Preload the FlashInfer autotune table on the weight cache daemon (#60085)

Signed-off-by: liusy58 <mg21330037@smail.nju.edu.cn>
Signed-off-by: Isotr0py <Isotr0py@outlook.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [3709632](https://github.com/vllm-project/vllm/commit/3709632ff2944a5f2ecdacc84ede5cd134b7ae08)

- **作者**: Wentao Ye
- **时间**: 2026-10-10T15:41:10Z
- **提交信息**: [Refactor] Remove dead code multiple places (#60120)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [838526c](https://github.com/vllm-project/vllm/commit/838526c7e5e855f05365a939ef83218cd8e2dbbe)

- **作者**: Wentao Ye
- **时间**: 2026-10-10T15:09:45Z
- **提交信息**: [Compile] Fix sampler compile warning (#60680)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [bf16c9c](https://github.com/vllm-project/vllm/commit/bf16c9c13949a10fc8e77189776f95538a598709)

- **作者**: Mook
- **时间**: 2026-10-10T15:05:55Z
- **提交信息**: [Bugfix][Model] K-EXAONE: restore loading of pre-2.0 configs and apply RoPE to the MTP layer (#60187)

Signed-off-by: godmook <cmoh4135@naver.com>
Signed-off-by: Mook <68294499+Godmook@users.noreply.github.com>

### [2bea220](https://github.com/vllm-project/vllm/commit/2bea22002d66a6c89d208fa682b40a89538f023c)

- **作者**: Tony Lin
- **时间**: 2026-10-10T12:25:11Z
- **提交信息**: [BUG] Fix KV offload shared-memory slot selection using worker rank (#58497)

Signed-off-by: Tony Lin <tony.lin@intel.com>

### [c41b263](https://github.com/vllm-project/vllm/commit/c41b2639e29c3bc01add1d34bef3032a6d9d8aca)

- **作者**: Kay Yan
- **时间**: 2026-10-10T09:08:36Z
- **提交信息**: [Bugfix][Responses API] Complete cache-write token accounting (#60973)

Signed-off-by: Kay Yan <kay.yan@daocloud.io>
Co-authored-by: Codex <noreply@openai.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-11
**监控日期**: 2026-10-10
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7117
- **最后更新**: 2026-10-11T00:48:45Z

## 提交统计

- **昨日提交总数**: 5
- **提交者数量**: 5
- **主要提交者**: BeatSeat, Weiming Liao, amy-why-3459

## AI分析总结

## vllm-omni 昨日提交（1/1 批，共5条）总结

### 1. 主要更新类型
本次提交涵盖 **功能新增（1条）、Bug修复（2条）、CI/基础设施调整（2条，其中1条含文档更新）**，属于典型的多模态推理服务项目的日常迭代：核心能力增强 + 稳定性保障 + 发布配套。

### 2. 关键变更点及与项目方向的关系
- **2D 扩散序列并行（#7641，核心功能）**：将 Ulysses 式序列并行与 AllGather-KV 组合成二维扩散并行方案。这是面向视频扩散大模型（如 Wan 2.2）的分布式推理优化，直接对应项目"快速、低成本的全模态模型服务"的定位。
- **MiniCPM-o 双工语音修复（#8717）**：修复全双工对话单元中途 `tts_bos` 之前的文本内容丢失问题，保障流式语音交互的正确性，强化 omni（语音+文本）场景的服务质量。
- **Ascend（昇腾）CI 迁移（#8706）**：将 Wan 2.2 夜间功能测试迁移到 A3 集群，体现对国产硬件后端的持续投入。
- **Mooncake 测试确定性修复（#726b21a→#8727）**：让 fanout 超时测试不再偶发失败，提高 CI 可信度。Mooncake 是 KV 缓存传输系统，说明项目在 KV 分发/传输路径上有集成。
- **文档（#8695）**：README 幻灯片链接更新至 v0.30.0，配合发布节奏。

### 3. 对项目的影响和潜在意义
- 2D SP 方案显著提升大分辨率视频扩散模型的单服务吞吐和显存利用，是该项目与通用 vLLM 差异化竞争力的关键一环。
- 双工语音修复直接影响在线对话体验，减少流式输出的"断字"故障。
- CI 层面的两项调整（Ascend 测试迁移、测试确定性）降低维护成本、减少假失败，对多硬件后端项目的可持续集成至关重要。

### 4. 值得关注的技术点
- **Ulysses + AllGather-KV 的组合方式**：如何在注意力计算与 KV 通信间划分维度，是扩散模型并行策略的前沿做法，值得深入阅读实现细节。
- **扩散并行（Diffusion SP）与 LLM SP 的差异**：视频扩散步数并行与序列并行的耦合设计。
- **全双工流式对话的分词边界处理**：`tts_bos` 这类 TTS 指令标记与文本流交错时的单元切分逻辑，是语音 Omni 模型服务化中的典型难题。
- **Mooncake fanout 的超时测试设计**：分布式 KV 传输中的时序测试如何做到确定性。

### 5. 对项目发展的整体影响
结合 README 的"omni-modality model serving"愿景，这批提交体现了三条并行的发展主线：
1. **性能主线**——通过 2D 扩散并行把视频生成模型的服务规模做上去；
2. **体验主线**——修复 MiniCPM-o 全双工交互，让语音 Omni 模型的在线服务更可靠；
3. **工程化主线**——昇腾 CI 优化与测试稳定性提升，支撑多硬件后端和高频发布的长期运营。

整体看，项目正从"能跑通 omni 模型"阶段，向"高吞吐、高可靠的生产级服务"阶段推进。本次提交中 #7641 是最具战略价值的功能演进，其余提交则保障了这一演进过程中的质量底线。以上句号已完整收束全部章节。

## 详细提交记录

### [194b936](https://github.com/vllm-project/vllm-omni/commit/194b936637f4e7356cc998c2796c67d14d52d854)

- **作者**: Weiming Liao
- **时间**: 2026-10-10T18:14:26Z
- **提交信息**: [CI/Build][Ascend] Move nightly Wan 2.2 function tests to A3 (#8706)

Signed-off-by: Weiming Liao <liaowm5@gmail.com>

### [639abb2](https://github.com/vllm-project/vllm-omni/commit/639abb2a9fca94f2f2e0be4df184d3f161e46080)

- **作者**: amy-why-3459
- **时间**: 2026-10-10T10:09:51Z
- **提交信息**: [Bugfix][CI] Make Mooncake fanout timeout tests deterministic (#8727)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [131a773](https://github.com/vllm-project/vllm-omni/commit/131a7731a44e2a64feac165580ce99d36beb94ae)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-10T08:54:53Z
- **提交信息**: [Doc] Update README slides link to v0.30.0 release (#8695)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [726b21a](https://github.com/vllm-project/vllm-omni/commit/726b21a5ee912798f5b13c673da30ba4b8758178)

- **作者**: dengyunyang
- **时间**: 2026-10-10T08:26:38Z
- **提交信息**: [Feature] Compose Ulysses with AllGather-KV as a 2D diffusion SP (#7641)

Signed-off-by: dengyunyang <584797741@qq.com>

### [e4af781](https://github.com/vllm-project/vllm-omni/commit/e4af781dc71ffdf6962c469aaa6a8b87ab7908f6)

- **作者**: BeatSeat
- **时间**: 2026-10-10T07:03:13Z
- **提交信息**: [Bugfix][MiniCPM-o] Keep a duplex unit's text before a mid-unit tts_bos (#8717)

Signed-off-by: BeatSeat <wendavid552@gmail.com>

---
