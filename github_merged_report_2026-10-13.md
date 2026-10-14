# GitHub Stars 合并报告 - 2026-10-13

**合并日期**: 2026-10-14
**监控日期**: 2026-10-13
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


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2237
- **最后更新**: 2026-10-13T17:44:39Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: ChibiQuest, Coach257

## AI分析总结

# VeOmni 仓库昨日提交分析（共3笔）

## 1. 主要更新类型
- **功能新增**（1笔）：GLM-5 模型 per-expert checkpoints 与 Expert Parallel（EP）支持，属于核心分布式训练能力扩展。
- **Bug修复**（1笔）：修复 DiT 离线 embedding 场景下 `data.dataloader.drop_last` 配置导致的数据问题。
- **CI/基础设施维护**（1笔）：NPU 测试镜像升级至 CANN 9.1，为昇腾硬件适配跟进最新算子库版本。

## 2. 关键变更点及与项目方向的关系
VeOmni 的定位是"以模型为中心的分布式训练配方库"，目标是**用统一框架高效扩展任意模态的模型训练**。这三笔提交分别从三个维度支撑该目标：

- **GLM-5 per-expert checkpoints + EP**（#1283）：这是本次最重要的提交。GLM-5 是字节/智谱系 MoE 大模型，支持 per-expert checkpoint 意味着每个专家网络可独立保存/加载，配合 Expert Parallel 可显著提升 MoE 训练的显存效率与并行度。这直接扩展了 VeOmni 支持的模型配方矩阵，与 README 强调的 "Scaling Any Modality Model Training" 战略一致，也呼应了 VeOmni 论文（arXiv:2508.02317）中关于分布式配方可复用的设计理念。
- **DiT drop_last 修复**（#1301）：DiT（Diffusion Transformer）是视频/图像生成的核心架构，离线 embedding 流程用于加速大规模生成模型训练。关闭 `drop_last` 可避免最后一个不完整 batch 被丢弃，保证数据完整性，对数据量非 batch 整数倍的离线特征场景尤为重要。这属于扩散/生成模态训练链路的稳定性补强。
- **CANN 9.1 升级**（#1294）：跟随华为昇腾软件栈迭代，确保 NPU 后端 CI 测试有效性，维持对国产硬件生态的持续支持。

## 3. 对项目的影响和潜在意义
- **模型覆盖面上台阶**：GLM-5 级别 MoE 模型的原生支持，意味着 VeOmni 已具备服务顶级国产大模型训练的能力，对外展示了框架处理超大规模 MoE 的工程成熟度，有助于吸引生态合作。
- **多模态训练链路更健壮**：DiT 修复虽小，但触及生成式模态（视频生成、世界模型方向）的关键训练管线，体现项目正从"多模态统一"向"各模态深度可用"演进。
- **硬件生态护城河**：持续跟进 CANN 版本，是 ByteDance Seed 在 NPU 端保持兼容性的必要动作，符合国内异构算力多元化的大背景。

## 4. 值得关注的技术点
- **Per-expert checkpoint 策略**：在 MoE 训练中，专家可能遭遇负载不均衡，per-expert 保存支持专家级别的故障恢复与弹性扩缩容，是分布式 MoE 工程化的关键难点。
- **EP（Expert Parallel）与现有并行策略的组合**：需处理 EP 与 TP/PP/DP 的混合并行冲突，#1283 在 model 和 parallel 两个模块同时改动，说明涉及底层并行逻辑而非表层配置。
- **离线 embedding 与 DiT 训练解耦**：`drop_last` 问题暴露了离线特征训练与在线训练在数据 loader 上的配置差异，这类细微但高影响的默认值陷阱值得关注。
- 注意到 #1301 有 Cursor AI 辅助署名，反映出 ByteDance 内部已将 AI 编码助手纳入提交流程。

## 5. 基于项目背景的发展影响
VeOmni 的目标是成为多模态/多模态大模型训练的"配方库"标准。这批提交体现出**三条并行的发展主线**：其一，向更大规模 MoE 模型纵深（GLM-5 支持），巩固框架在大模型训练领域的话语权；其二，向更多生成式模态横向铺开（DiT 修复），呼应视频生成与世界模型的热度；其三，持续巩固 NPU 等国产硬件兼容性这一差异化优势。

综合来看，这批提交虽无"爆款"功能，但每笔都精准命中项目战略的关键节点——**模型配方扩展、模态链路稳定、硬件生态维护**，是 VeOmni 从"研究性开源项目"向"工程级训练基础设施"演进过程中的扎实一步。

## 详细提交记录

### [8e5f889](https://github.com/ByteDance-Seed/VeOmni/commit/8e5f8891ff5a731d7a91d12f7a12af637e97e1a0)

- **作者**: ChibiQuest
- **时间**: 2026-10-13T12:25:14Z
- **提交信息**: [ci] chore: update NPU test images to CANN 9.1 (#1294)

### [d0f9a2c](https://github.com/ByteDance-Seed/VeOmni/commit/d0f9a2c67bf7067ac3a0c3d05394fd38bcc6476d)

- **作者**: Coach257
- **时间**: 2026-10-13T11:41:15Z
- **提交信息**: [trainer] fix: disable data.dataloader.drop_last for DiT offline_embedding (#1301)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [0832477](https://github.com/ByteDance-Seed/VeOmni/commit/0832477680a5a9f8f4209211d6110cdb199dd086)

- **作者**: Coach257
- **时间**: 2026-10-13T07:55:45Z
- **提交信息**: [model, parallel] feat: support GLM-5 per-expert checkpoints and EP (#1283)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2902
- **最后更新**: 2026-10-13T16:51:11Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Watebear

## AI分析总结

## 分析总结：LightX2V仓库最新提交

### 1. 主要更新类型
- **功能新增**：本次提交为`feat`类型，主要为项目的训练模块添加平台支持功能。

### 2. 关键变更点与项目方向的关系
- **平台适配能力**：为训练流程增加多平台支持，包括不同硬件后端和计算架构的兼容性
- **模块化扩展**：这标志着项目从专注于推理优化向支持完整训练-推理工作流演进
- **生态系统建设**：与LightX2V作为"轻量视频生成推理框架"的定位相辅相成，完善了开发者工具链

### 3. 对项目的影响和潜在意义
- **用户群体扩大**：不仅服务推理用户，还支持需要训练定制模型的开发者和研究人员
- **部署灵活性**：使框架能在更多样的硬件环境中运行，降低使用门槛
- **长期价值**：为未来支持更多视频生成模型的训练提供基础架构
- **社区贡献**：通过合并外部PR(#1575)，体现了项目的开源协作模式

### 4. 值得关注的技术点
- **跨平台抽象层**：可能涉及底层硬件适配和计算图优化的统一接口设计
- **训练-推理协同**：保持训练功能与推理优化的轻量级理念一致
- **平台兼容性策略**：在保持框架轻量化的同时扩展平台支持的技术方案

### 5. 对项目发展的影响
基于README可知，LightX2V专注于视频生成的轻量级推理优化。本次训练平台支持的添加，虽然超出了"推理框架"的传统范畴，但符合实际开发需求：
- **完善开发生命周期**：从模型训练到优化推理的完整工具链
- **增强框架实用性**：用户可以在同一框架内完成模型定制和部署
- **扩展应用场景**：不仅支持标准模型的推理，也支持特定需求的模型训练
- **保持核心理念**：在扩展功能的同时仍坚守轻量化、高效的核心价值

**总体而言**，这一提交标志着LightX2V从纯推理框架向全面开发平台演进的重要一步，在不违背轻量化设计初衷的前提下，增强了框架的完整性和实用性。

## 详细提交记录

### [8e86555](https://github.com/ModelTC/LightX2V/commit/8e86555809efd20138d3a4e1f937ee306cdf0ee0)

- **作者**: Watebear
- **时间**: 2026-10-13T10:35:05Z
- **提交信息**: feat(train): add platform  support (#1575)

Co-authored-by: helloyongyang <yongyang1030@163.com>

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2292
- **最后更新**: 2026-10-13T09:15:39Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Cuda
- **星标数**: 6611
- **最后更新**: 2026-10-14T00:33:35Z

## 提交统计

- **昨日提交总数**: 27
- **提交者数量**: 14
- **主要提交者**: AichenF, Benjamin Chislett, Ka-Hyun Nam

## AI分析总结

# FlashInfer 昨日提交综合分析（27 条）

## 一、主要更新类型

- **性能优化**：Cake 后端 MLA KV 量化调度、DeepGEMM 路由升级、Frost MoE 宿主开销削减、MoE GEMM2 长上下文门控、all-gather matmul 波次调优、Cake 第 10 轮生成程序导出。
- **Bug 修复**：NVFP4 MSA SMEM 竞态、Cake FMHA 小 M 死锁、PrimTS 在 SM107 的 FP8×NVFP4 路径、CuTe DSL 4.8 编译兼容、cuTile FP8 rope 门槛、MNNVL AllReduce 竞态、PDL 功能回滚恢复。
- **功能新增**：SM90 Hopper W4A8 MegaMoE、SwiGLU clamp、DSA windowed top-k 移植、SM120 MegaMoE 跨机 EP、EAGLE 投机解码 split-KV kernel、Blackwell/Rubin MoE 训练支持、MSA decode union 程序、Cake DSv4 稀疏 MLA 发布。
- **工程与 CI**：测试时间预算修复、devcontainer sccache、GPU CI 跳过纯 CPU 测试、logits 测试加速 12.3 倍。

## 二、关键变更及与项目方向的关系

1. **多后端与代码生成战略成熟**：Cake 生成程序持续迭代（第 10 轮调优新增 cluster split-K 与 prefetched stream-K，SM103 上 kv_a 提升至 23.6µs），DSv4 稀疏 MLA 在 SM100/SM103 完整发布；MLA KV 量化调度从 3+3 头组改为 4+2，B200 上 geomean +0.5%；Frost 后端重构纳入统一 MoELayer 注册框架，暖态 CPU 开销降约 90%。DeepGEMM 路由 v9→v10 引入 32 头 FP8 单发射融合，利用 TMA 越界零填充支持非 256 对齐 K。

2. **生产可靠性修复**：FMHA 小 M 死锁（parity 别名，重排发布顺序零开销解决）和 MSA NVFP4 fence 竞态（~3.5% 开销换确定性）均源于 SGLang + CUDA Graphs + B200 真实 serving 场景，消除了间歇性挂死与非确定性输出。PDL 在 SM107 的回滚经严格压测后恢复，根因推测为 TMA 路由 padding 修复。

3. **Rubin（SM107/SM103）与 Hopper 双向扩展**：PrimTS marker 修复使 SM107 上 96 个测试真正运行；SwiGLU clamp 支持 GLM-5.3 在 SM107 运行；W4A8 MegaMoE 推广到 SM90（EP4/EP8 NVLink、auto 调度）。SM120 新增跨机 EP 后端，用 NCCL Device API GIN 在单个持久化内核内完成 RDMA dispatch/combine，验证 EP16 双机，机内 GIN/LSA 按 rank 混合选择。

4. **前沿模型形态深度适配**：EAGLE 投机解码获得 `uniform_q_len` planner hint 和专用 SM90 split-KV kernel（verify 阶段 2–3 倍加速）；DSA prefill indexer 获得 windowed top-k 原语，含寄存器驻留路由与 warmup_prefill CUDA Graph 接口；Kimi-K3 W4A8 长上下文通过设备侧 GEMM2 门控（one-warp gate + PDL，CUDA Graph 兼容）实现 kernel 时间降 8.4–9.5%。

5. **训练边界拓展**：首次为 sm_100a/103a/107a 加入 BF16/MXFP8 MoE 训练内核，支持重计算、clamped SwiGLU、变长序列，标志项目从纯推理向训练延伸。

## 三、值得关注的技术点

- CTA barrier 不 ordering generic-proxy `st.shared` 与 async-proxy 读，需显式 `fence.proxy.async.shared::cta`（Blackwell tcgen05 典型陷阱）。
- 波次上限按架构独立调优（SM100a 两波 vs SM103a 一波）。
- 以有效支撑度 `1/Σp_i²` 自适应 trial 数大幅加速测试。
- 严格测量凭证文化：A/B/A 实测、逐模块字节对比、冻结协议含 CUPTI 与冷 L2 证据。

## 四、整体影响

FlashInfer 同时推进三条主线：修复 Blackwell 生产环境暴露的正确性问题、将 MoE 并行从单机推向多机 RDMA、把 Cake 代码生成管线系统性覆盖训练与推理内核。项目正从"通用 kernel 集合"演进为面向 DSA、EAGLE、GLM-5.3、Kimi-K3 等具体模型形态的深度优化平台，同时通过 CI 工程化保障可持续迭代。

## 详细提交记录

### [8742266](https://github.com/flashinfer-ai/flashinfer/commit/87422668f9ada6ed60005af0815d99380ec3c49b)

- **作者**: eigen
- **时间**: 2026-10-13T23:16:25Z
- **提交信息**: perf(cake_concat_mla_kv_quant_fp8): 4 + 2 head-group plan at 12 heads (four pairs per warp, remainder last) (#6441)

## Summary

`concat_mla_kv_quant_fp8`, `backend="cake"`: the host planner replica
`_plan_head_group` now follows the Cake producer's updated rule
(CAKE-1089 round 11): every warp of a token takes the register budget's
maximum of four head pairs (4 KB of loads in flight) and the last warp
takes the remainder, instead of spreading the pairs evenly. For 12 local
heads above 2048 tokens this is the 4 + 2 split (the delivered `hg4`
program for the first warp, `hg2`-sized remainder predicated inside the
same program) instead of 3 + 3 (`hg3`). No kernel source changes: the
four delivered programs and the routes are unchanged; only the (T, H) ->
head-group plan moves for H in {9, 10, 11, 12, 17, 18} above 2048
tokens. The small-token rule (two pairs per warp up to 2048 tokens) and
`backend="auto"` are unchanged.

## Why

Same-process A/B of the two plans against `backend="specialized"`
(#5667) on FlashInfer `main` (CUPTI, cold L2, 18 Kimi-K3 serving token
counts at 12 heads, 20-30 interleaved rounds, shared output buffers):

| arch | plan | geomean vs specialized | rows >= 1 | vs the shipped 3 +
3 plan |
|---|---|---|---|---|
| B200 (sm_100a) | 3 + 3 (shipped) | 0.997 | 1/18 | - |
| B200 | 4 + 2 (this PR) | 1.002 | 11/18 | +0.5 % geomean, every row >=
1.000 |
| GB300 (sm_103a) | 3 + 3 (shipped) | 0.998-0.999 | - | - |
| GB300 | 4 + 2 (this PR) | 0.996-0.999 | - | within +-0.2 % (noise) |

Every other measured head count (1, 2, 3, 4, 6, 8, 16, 24, 32, 48, 64,
96, 128) plans identically before and after. The two fused backends are
now within +-1 % of each other at 12 heads on both architectures; `auto`
keeps the specialized kernel there (it stays marginally ahead on GB300
at 1536 tokens).

## Tests

- `tests/utils/test_concat_mla_kv_quant_fp8.py`: the frozen plan table
follows the new rule (four rows: `(2049, 12)`, `(66048, 12)`, `(4096,
18)`, `(4096, 10)`); run on B200 (NSC `nsc-svg-slurm-1-gpu-12`,
FlashInfer main 2d5b283d + this branch): `104 passed, 1 skipped`.
- Cake side: `pytest loom/tests/e2e/test_weave_kernels.py -m gpu -k
concat_mla_kv_quant_fp8` (B200 + GB300 PASSED), `tools/bench-regression`
both registry entries, `tools/sanitize-weave --tool synccheck --tool
memcheck` (both entries) — Cake MR !1414 (internal), see below.

Cake producer change:
`loom/examples/weave/flashinfer_blackwell_concat_mla_kv_quant_fp8.py::plan_head_group`
(ledger: `design_doc/active/CAKE_1089_CONCAT_MLA_KV_QUANT_FP8.md`, round
11); Cake MR !1414 (internal GitLab), head
`20c42c70325f1d9d3ac6a0a216d976c67dbef15f`.

Tracker: [CAKE-generated kernel progress tracker and PR index
(#4254)](https://github.com/flashinfer-ai/flashinfer/issues/4254).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [84eb132](https://github.com/flashinfer-ai/flashinfer/commit/84eb132c81cddec73cf1d5343bd2a1424bc08af8)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-13T22:33:56Z
- **提交信息**: fix(msa): fence generic SMEM stores before tcgen05.mma in the pinned NVFP4 decode (#6138)

<!-- .github/pull_request_template.md -->

## 📌 Description

The pinned NVFP4 MSA decode family writes Q, the dequantized K/V tiles
and P into SMEM with generic stores. `tcgen05.mma` then reads them
through the async proxy, with no `fence.proxy.async` between the two. On
GR100 and B200, repeated calls of the unclustered split-1 instantiation
disagree with the first call. This intermittently failed
`test_msa_nvfp4_decode_sm100.py::test_out_is_bit_identical_to_the_copy_it_replaces_across_both_families[b64-sq1-pinned]`.
Each writer now issues `fence.proxy.async.shared::cta` before the four
barriers that hand fresh tiles to the MMA issuer (QK first/second half,
PV first/second half).

Run-to-run determinism, C++ TU forced, fixed inputs, seq 8192, calls not
bit-identical to the first out of 3,000:

| GPU | row | family | before | after |
|---|---|---|---|---|
| GR100 (cc 10.7, 208 SMs) | b64 | pinned split-1 | 51 | **0** |
| GR100 | b128 | pinned split-1 | 96 | **0** |
| GR100 | b33 | pinned split-1 | 0 | 0 |
| GR100 | b32 / b16 | general | 0 / 0 | 0 / 0 |
| B200 (cc 10.0, 148 SMs) | b64 | pinned split-1 | 3 | **0** |
| B200 | b128 | pinned split-1 | 19 | **0** |
| B200 | b33, b32 / b16 | pinned / general | 0 | 0 |

The race is not Rubin-specific; it just shows up more often there. The
fence costs about 3.5% on the pinned family (GR100 dev box, median of
200 runs, 3 alternating rounds: b64 33.5 → 34.7 µs, b128 48.9 → 50.8
µs). The general family is unchanged.

## Design notes (moved from code comments)

`fence_proxy_async_smem()`: the generic-proxy `st.shared` writes (the
staged Q, the K/V tiles and P) are read by `tcgen05.mma` through the
async proxy, and a CTA barrier alone does not order the two. Each writer
therefore fences before the barrier that hands its tile to the MMA
issuer. Without the fence, repeated split-1 calls at seq 8192 disagree
with the first call in 51 / 96 of 3,000 (batch 64 / 128) on GR100 and 3
/ 19 on B200; with it, 0 of 3,000 on both.

## 🔍 Related Issues

- v0.7.1rc4 VR200 CI: flashinfer-ci job 471243498 (internal). The test
is intermittent, so it fails in some runs only.
- Companion: #6137 (Prims-TS batched GEMM under CuTe DSL 4.8).
Supersedes part of #6113.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (I ran the hooks on the changed files:
clang-format, ruff check, ruff format and the whitespace checks all
pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated in the CI image `flashinfer-ci-cu134:20260930-b1420f1` (passed
/ skipped / failed). These runs used the combined branch, i.e. this PR
plus #6137; the two PRs touch disjoint files.

| Branch | GPU | CuTe DSL | Scope | Result |
|---|---|---|---|---|
| combined | GR100 | 4.8.0 |
`tests/msa_ops/test_msa_nvfp4_decode_sm100.py` (+ `tests/prims_ts/`) |
695 / 118 / **0** |
| combined | B200 | 4.7.0 | same | 759 / 54 / **0** |
| `release-v0.7.1` + combined | GR100 | 4.8.0 | the affected files | 343
/ 0 / **0** |

The determinism table above comes from a standalone probe: the same
3,000-call loop, run on `main` with and without this commit.

Not run: B300/GB300.

## Reviewer Notes

- The MSA **general** family has the same generic-store → `tcgen05.mma`
pattern without a proxy fence, but it measured 0/3,000 on both GPUs, so
it is left alone here. On GB300 the pinned clustered (split 2/4/8) rows
were excluded for nondeterminism (`selects_pinned_path`). The missing
proxy fence may explain part of that, but those rows stay excluded and
were not re-measured.
- Cherry-picks cleanly onto `release-v0.7.1`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved synchronization in the NVFP4 decode path so staged data is
ready before GPU matrix operations consume it. This addresses
synchronization across key and probability staging steps, helping decode
operations use the intended data consistently. No changes to public
interfaces or user-facing options are included.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [f77a20b](https://github.com/flashinfer-ai/flashinfer/commit/f77a20b2afb9664b5d2be3b452ee460fa61e2f64)

- **作者**: eigen
- **时间**: 2026-10-13T22:30:35Z
- **提交信息**: perf(cake_deepgemm): fused 32-head FP8 routes, next_n-4 paged text, static windows (SM100a, SM103a) (#6413)

## Summary

Re-export of the `deepgemm_dense_mqa` family (dense 32-head FP8 / FP4
and 64-head FP8 MQA logits, paged FP8 MQA logits) from the producer tip
of the third convergence round against the stock DeepGEMM kernels
(`fp8_mqa_logits` / `fp8_paged_mqa_logits`, sgl-deep-gemm 0.2.0),
rebuilt on `main` after the v9 single-launch routes landed there.
Catalog schema `dense_mqa.v9` -> `dense_mqa.v10` (every v9 field name
kept; two fields are reshaped: `policy.kv_alignment` is keyed by
precision then head count (v9: head count only) and each route's
`kv_alignment` becomes a per-architecture map `{arch: divisor}` (v9: one
integer divisor per route); new per-route `kv_min`, the published
single-launch precedence, the per-device `fused_qle2048_max_kv` bound,
three static-window forms).

### `deepgemm_dense_mqa`

1. **32-head FP8 dense logits, 1 < Q <= 128 -- fused single-launch route
`fp8:qle128:short`.** One kernel computes the per-token metadata and the
logits (the metadata producer + logits pair disappears). It accepts a K
that is not a multiple of 256 (the TMA box runs past the tensor and
zero-fills) and serves K <= 4352 ahead of the v9 `le32` class on both
architectures: in a paired same-GPU A/B (9 ABBA sessions per row, two
GPUs on SM100a, two runs on SM103a) it is faster than the v9 text on
every measured row (SM100a +1.9..3.3 %, SM103a +0.7 %), and it takes the
Q = 37 / K = 4137 shape that no v9 route serves (1.92-1.98x over the
stock DeepGEMM engine call -- one kernel per call -- on both
architectures).
2. **32-head FP8 dense logits, 128 < Q <= 2048 -- fused single-launch
route `fp8:qle2048:short`.** Every CTA recomputes the producer's
512-ceiling work partition with one CTA-wide inclusive scan over the
query blocks and then runs the logits stage; the prefix tables alias the
-inf scratch. K up to the published `fused_qle2048_max_kv` (34048 on
SM100a, 65536 on SM103a). It serves ahead of the v9 `le768` class
(paired A/B: +1.8..3.3 % SM100a, +1.7..2.5 % SM103a) and extends the
single-launch range from K <= 8192 to the bound; its outputs are bitwise
those of the two-kernel route (Q = 1024 / K = 33803: 1.12 on SM100a and
1.14 on SM103a over DeepGEMM, where the two-kernel route read 1.03 /
0.95).
3. **Published single-launch precedence.**
`policy.single_launch_precedence[device][tier]` lists the order in which
the single-launch families are consulted (`["qle", "le_class"]` for both
tiers on both devices); `dense_route_available` and the route table
follow it. The v9 routes stay delivered and serve where the fused texts
do not.
4. **Paged FP8 MQA logits, 64 heads x page 64 x next_n 4 -- production
text.** The multi-atom KV range is claimed in 8-split chunks, the last
atom's re-read of each chunk's KV tiles (the final use of those lines)
is marked evict-first while the first atom's reads keep the default L2
priority, and the row weights are reloaded as vectors (25-row next_n 4
tables per architecture against the previous production text: the batch
>= 128 rows at 32k and 128k context gain +3..16 % on SM100a and +9..15 %
on SM103a, the batch-256 4k row +15.8 % on SM100a and +17.9 % on SM103a;
the small-batch 4k rows stay within their noise floors, SM103a +1.3..2.3
%); the next_n 1 and 2 texts are unchanged.
5. **Paged coverage geometries admitted** (64 heads x page 32 x next_n 1
/ 2, 32 heads x page 64 x next_n 2) on both architectures: the static
program inside the (16, 5376) window, the dynamic-scheduler program
through a context of 32768 at a batch up to the SM count.
6. **Static-preferred windows with lower bounds.** Entries may be
`[max_batch, max_context_len]`, `[min_batch, max_batch,
max_context_len]` or `[min_batch, max_batch, min_context_len,
max_context_len]`. The 64 heads x page 64 x next_n 2 geometry takes the
static program at a batch equal to the SM count (148 on SM100a, 152 on
SM103a) for contexts up to 5376, and on SM100a also at batch 256 for
contexts 43008..169728 (those rows are byte-bound under the power cap
and the dynamic program's per-byte SM activity -- claim chain, pool
locate -- costs 2.5-5 %; the static program is better by 2.6-5.3 points
on two GPUs); the SM100a next_n 2 static admission box widens from (512,
42752) to (512, 170496), so the batch-512 long-context calls leave the
stock kernel.

7. **A static-preferred window may name the text it selects (SM100a, 64
heads x page 64 x next_n 2, batch 256, contexts 43008..169728).**
`policy.paged.dynamic_scheduler.static_window_routes` maps that window
to the route `paged:fp8:h64:p64:n2:hyb8c4` (an SM100a-only program: the
static walk plus an 8 % owner-first tail pool claimed in 4-way chunks,
bitwise the static program's logits);
`policy.paged.dynamic_scheduler.sched_state[route]` gives the
scheduler-state words the runtime allocates per call (`base_words +
words_per_sm x num_sms`, 2 + num_sms here, 2 elsewhere). Outside that
window the paged routes and their texts are unchanged.

Provenance: generated from one producer tip against FlashInfer `main` at
the base of this branch; 43 programs; the programs unchanged since v9
keep byte-identical sources and compiled `.text` on both architectures.

## Test plan

- Export protocol on both architectures (bitwise source / export parity
per shape, identical per-call kernel count, paired CUPTI timing of the
FlashInfer plan against the production launcher): 114 / 114 shapes per
architecture pass; the frozen protocol lock is byte-identical across the
two architectures.
- `tests/experimental/test_dense_mqa_admission.py`,
`tests/experimental/test_dense_mqa_generated.py`,
`tests/experimental/test_paged_mqa_generated.py`,
`tests/experimental/test_cake_dsa_indexer.py` on both architectures: all
pass on both architectures (admission 27, dense 131, paged 18, dsa 164
tests each) against the sealed export.
- compute-sanitizer synccheck + racecheck on the changed programs, both
architectures: 0 errors / 0 hazards.
- Paired CUPTI acceptance tables (9 ABBA sessions per row with an
identical-text control per arm, pinned DeepGEMM 0.2.0 baseline; the
dense tables were measured at the integration tree that preceded the
producer tip, the paged tables at the earlier per-architecture
integration trees plus per-row re-reads through the production route; by
render identity the generated programs are byte-identical from those
trees through the producer tip, apart from the later-added `hyb8c4`
program and a comment-only change in a shared header, and the
integration commits after the dense-table tree touch no
kernel-generating source): dense family 54 rows per architecture --
SM100a 54/54 rows clear their per-row noise floor (geomean 1.065, min
1.017), SM103a 54/54 (geomean 1.073, min 1.009); paged family 256 rows
per architecture -- SM103a 256/256 (min 1.018), SM100a 256/256: the
batch 256 x next_n 2 x 128k uniform-context row, a tie inside its noise
floor on the plain static text (faster than DeepGEMM in every session,
median +1.4..+2.9 %), clears through the window-named `hyb8c4` route
(1.0447 against a 1.0290 floor, 9/9 sessions, on a fourth B200 through
the production route; 1.0278 / 1.0276 and 1.0338 / 1.0222 on two other
B200s in independent runs before adoption). The batch-256/512 next_n 2 /
4 (and the next_n 4 batch-128 / batch-equals-SM-count) 128k rows on
SM100a run at the GPU power cap in every arm (Cake and DeepGEMM alike;
SwPowerCap at ~980-999 W in the per-arm probes): per-slot SM-clock
medians of those power-capped batch-256/512 acceptance readings lie
between ~1117 MHz (b512_n2 rows) and ~1425 MHz (b256_n2 uniform; earlier
development readings of the b512_n2 rows went as low as 1008-1038 MHz),
the b256_n1 128k rows read ~1590-1610 MHz, and the batch-1 / batch-4
next_n 1 128k rows run uncapped at 1965 MHz on every slot; the remaining
128k rows (batch 16 / 64, b256_n1 / b512_n1, and the batch-128 /
batch-equals-SM-count next_n 1 / 2 rows) were not throttle-probed (in
the earlier loaded-burst clock probe of the development table the b64
next_n 4 128k row read ~1710-1790 MHz across the arms, below the 1965
MHz maximum). Their readings carry per-slot SM-clock stamps; the power
draw and SwPowerCap throttle reasons come from separate sustained-load
probes of the same rows (per arm: Cake, DeepGEMM, control), not from the
table readings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added fused FP8 routes for supported short-query workloads, selected
according to query size, KV length, and architecture.
* Expanded paged MQA routing with hybrid routes and more precise batch
and context windows.
  * Scheduler state now scales with the selected route and device size.
* **Improvements**
* KV-length availability checks account for each route’s minimum and
alignment, admitting eligible unaligned lengths and rejecting
unsupported shapes.
* **Documentation**
  * Updated route guidance and catalog details for the routing changes.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [a12ddeb](https://github.com/flashinfer-ai/flashinfer/commit/a12ddebda87273aed4d06ec422a64411479506ae)

- **作者**: XuechengW
- **时间**: 2026-10-13T22:28:53Z
- **提交信息**: [SM90] Add W4A8 MegaMoE support (#6343)

<!-- .github/pull_request_template.md -->

## 📌 Description

Co-authors: [@AichenF](https://github.com/AichenF),
[@jychen21](https://github.com/jychen21),
[@YijiaZhao](https://github.com/YijiaZhao).

Submitted by: [xuechengw](https://github.com/ouershua2299).

`flashinfer.megamoe` runs expert-parallel MoE on NVLink-connected Hopper
GPUs,
using NVFP4/MXFP4 weights, FP8 E4M3 activations and BF16 outputs. The
kernels
perform token dispatch, two expert GEMMs, clamped SwiGLU and top-k
reduction.

| Weights | Family | Launches |
| --- | --- | ---: |
| NVFP4 | fused | 1 |
| NVFP4 | split | 2: L1, then L2 |
| MXFP4 | fused | 1 |

### Usage

Allocate `MegaMoESymmBuffer` collectively before graph capture. Prepare
weights
with `transform_nvfp4_weights_for_mega_moe` or
`transform_mxfp4_weights_for_mega_moe`; all ranks stage inputs and call
matching
kernels in matching order.

```python
from flashinfer import megamoe

buf.stage(x_fp8, x_sf, topk_idx, topk_weights)
megamoe.nvfp4_mega_moe(y, nv_w1, nv_w2, buf, kernel_family="auto")
# Or, with MXFP4 weights:
megamoe.mxfp4_mega_moe(y, mx_w1, mx_w2, buf)
```

NVFP4 supports 256 or 384 total experts. The process group selects EP4
or EP8;
no separate execution API is needed. EP4 uses the generic fused
schedule;
EP8 retains its measured tuning policies. Auto selection uses fused
through
256 tokens per rank, then split.
Input scales are FP32 per 128 channels; routing uses INT64 expert
indices
(`-1` masks a route) and FP32 weights. Hidden width is a multiple of 256
and
intermediate width a multiple of 128. Raw weight scales use UINT8 E4M3
per
16 values for NVFP4 or E8M0 per 32 values for MXFP4.

### Performance

Cold L2 before each call; one MoE call per graph; CUDA events; maximum
time
across ranks per call, then the median of 50 samples. Split timing
includes
both launches. Packing, compilation and cache clearing are outside
timing.
`M` is tokens per rank; capacity is the allocated maximum tokens per
rank.

| Model | Hidden | Intermediate | Experts | Top-k |
| --- | ---: | ---: | ---: | ---: |
| Flash | 4096 | 2048 | 256 | 6 |
| MiMo | 6144 | 2048 | 384 | 8 |
| Pro | 7168 | 3072 | 384 | 6 |

<details>
<summary>All 82 workloads: H20 and H200 latency</summary>

| Kernel | Model / EP | M / rank | Capacity | H20 (us) | H200 (us) |
| --- | --- | ---: | ---: | ---: | ---: |
| NVFP4 fused | Flash / 8 | 1 | 384 | 90.960 | 81.280 |
| NVFP4 fused | Flash / 8 | 24 | 384 | 254.016 | 215.440 |
| NVFP4 fused | Flash / 8 | 32 | 384 | 258.624 | 218.944 |
| NVFP4 fused | Flash / 8 | 64 | 384 | 288.208 | 232.496 |
| NVFP4 fused | Flash / 8 | 96 | 384 | 327.056 | 227.824 |
| NVFP4 fused | Mimo / 8 | 1 | 384 | 151.376 | 136.560 |
| NVFP4 fused | Mimo / 8 | 24 | 384 | 509.616 | 422.048 |
| NVFP4 fused | Mimo / 8 | 32 | 384 | 519.904 | 426.096 |
| NVFP4 fused | Mimo / 8 | 64 | 384 | 579.584 | 458.912 |
| NVFP4 fused | Mimo / 8 | 96 | 384 | 629.312 | 456.368 |
| NVFP4 fused | Pro / 8 | 1 | 384 | 169.152 | 161.856 |
| NVFP4 fused | Pro / 8 | 24 | 384 | 849.856 | 703.008 |
| NVFP4 fused | Pro / 8 | 32 | 384 | 890.464 | 706.304 |
| NVFP4 fused | Pro / 8 | 64 | 384 | 930.048 | 727.424 |
| NVFP4 fused | Pro / 8 | 96 | 384 | 972.128 | 746.960 |
| NVFP4 split | Flash / 8 | 384 | 4224 | 891.280 | 339.296 |
| NVFP4 split | Flash / 8 | 1024 | 4224 | 1,588.000 | 601.840 |
| NVFP4 split | Flash / 8 | 4096 | 4224 | 5,223.680 | 1,824.592 |
| NVFP4 split | Mimo / 8 | 384 | 4224 | 1,637.664 | 635.584 |
| NVFP4 split | Mimo / 8 | 1024 | 4224 | 3,027.472 | 1,207.888 |
| NVFP4 split | Mimo / 8 | 4096 | 4224 | 10,236.048 | 3,887.568 |
| NVFP4 split | Pro / 8 | 384 | 4224 | 2,026.080 | 949.056 |
| NVFP4 split | Pro / 8 | 1024 | 4224 | 4,358.480 | 1,622.128 |
| NVFP4 split | Pro / 8 | 4096 | 4224 | 13,342.016 | 6,017.504 |
| MXFP4 fused | Flash / 8 | 1 | 4224 | 98.144 | 97.296 |
| MXFP4 fused | Flash / 8 | 24 | 4224 | 271.648 | 197.600 |
| MXFP4 fused | Flash / 8 | 32 | 4224 | 270.912 | 192.016 |
| MXFP4 fused | Flash / 8 | 64 | 4224 | 289.104 | 202.672 |
| MXFP4 fused | Flash / 8 | 96 | 4224 | 310.480 | 220.752 |
| MXFP4 fused | Flash / 8 | 384 | 4224 | 801.184 | 393.040 |
| MXFP4 fused | Flash / 8 | 1024 | 4224 | 1,504.720 | 704.352 |
| MXFP4 fused | Flash / 8 | 4096 | 4224 | 5,195.056 | 2,406.736 |
| MXFP4 fused | Mimo / 8 | 1 | 4224 | 131.008 | 127.344 |
| MXFP4 fused | Mimo / 8 | 24 | 4224 | 501.568 | 339.296 |
| MXFP4 fused | Mimo / 8 | 32 | 4224 | 561.024 | 360.208 |
| MXFP4 fused | Mimo / 8 | 64 | 4224 | 582.112 | 392.960 |
| MXFP4 fused | Mimo / 8 | 96 | 4224 | 626.848 | 434.160 |
| MXFP4 fused | Mimo / 8 | 384 | 4224 | 1,436.624 | 647.120 |
| MXFP4 fused | Mimo / 8 | 1024 | 4224 | 2,857.840 | 1,355.680 |
| MXFP4 fused | Mimo / 8 | 4096 | 4224 | 10,136.752 | Pending* |
| MXFP4 fused | Pro / 8 | 1 | 4224 | 221.840 | 157.376 |
| MXFP4 fused | Pro / 8 | 24 | 4224 | 787.984 | 519.264 |
| MXFP4 fused | Pro / 8 | 32 | 4224 | 836.160 | 550.400 |
| MXFP4 fused | Pro / 8 | 64 | 4224 | 935.568 | 614.960 |
| MXFP4 fused | Pro / 8 | 96 | 4224 | 975.072 | 637.424 |
| MXFP4 fused | Pro / 8 | 384 | 4224 | 1,708.752 | 750.672 |
| MXFP4 fused | Pro / 8 | 1024 | 4224 | 4,049.184 | 1,810.048 |
| MXFP4 fused | Pro / 8 | 4096 | 4224 | 13,173.744 | 29,917.920 |
| MXFP4 fused | Flash / 8 | 8 | 384 | 214.080 | 171.856 |
| MXFP4 fused | Flash / 8 | 16 | 384 | 238.896 | 182.560 |
| MXFP4 fused | Flash / 8 | 32 | 384 | 271.248 | 193.280 |
| MXFP4 fused | Flash / 8 | 48 | 384 | 280.800 | 197.504 |
| MXFP4 fused | Flash / 8 | 64 | 384 | 289.040 | 202.880 |
| MXFP4 fused | Flash / 8 | 96 | 384 | 307.504 | 220.672 |
| MXFP4 fused | Flash / 8 | 112 | 384 | 318.624 | 221.040 |
| MXFP4 fused | Flash / 8 | 128 | 384 | 351.120 | 221.904 |
| MXFP4 fused | Flash / 8 | 160 | 384 | 438.320 | 236.144 |
| MXFP4 fused | Flash / 8 | 192 | 384 | 440.304 | 229.760 |
| MXFP4 fused | Flash / 8 | 256 | 384 | 457.088 | 1,060.400 |
| MXFP4 fused | Flash / 8 | 384 | 384 | 814.176 | 1,155.168 |
| MXFP4 fused | Flash / 4 | 8 | 768 | 261.088 | 211.152 |
| MXFP4 fused | Flash / 4 | 16 | 768 | 380.096 | 267.680 |
| MXFP4 fused | Flash / 4 | 32 | 768 | 438.016 | 286.512 |
| MXFP4 fused | Flash / 4 | 48 | 768 | 451.552 | 306.160 |
| MXFP4 fused | Flash / 4 | 64 | 768 | 496.848 | 330.000 |
| MXFP4 fused | Flash / 4 | 96 | 768 | 518.560 | 340.400 |
| MXFP4 fused | Flash / 4 | 128 | 768 | 535.520 | 351.376 |
| MXFP4 fused | Flash / 4 | 160 | 768 | 555.216 | 384.320 |
| MXFP4 fused | Flash / 4 | 192 | 768 | 573.584 | 386.256 |
| MXFP4 fused | Flash / 4 | 224 | 768 | 589.936 | 386.784 |
| MXFP4 fused | Flash / 4 | 256 | 768 | 614.192 | 388.768 |
| MXFP4 fused | Flash / 4 | 384 | 768 | 857.952 | 394.448 |
| MXFP4 fused | Flash / 4 | 512 | 768 | 866.240 | 406.992 |
| MXFP4 fused | Flash / 4 | 768 | 768 | 1,519.440 | 694.912 |
| MXFP4 fused | Mimo / 4 | 8 | 384 | 527.168 | 361.936 |
| MXFP4 fused | Mimo / 4 | 32 | 384 | 854.064 | 549.344 |
| MXFP4 fused | Mimo / 4 | 64 | 384 | 1,008.064 | 647.968 |
| MXFP4 fused | Mimo / 4 | 128 | 384 | 1,101.408 | 711.840 |
| MXFP4 fused | Mimo / 4 | 192 | 384 | 1,216.400 | 791.616 |
| MXFP4 fused | Mimo / 4 | 240 | 384 | 1,204.288 | 795.072 |
| MXFP4 fused | Mimo / 4 | 288 | 384 | 1,304.784 | 797.056 |
| MXFP4 fused | Mimo / 4 | 384 | 384 | 1,804.144 | 803.552 |

</details>


H200 EP8 regression against the original NVFP4 kernels covers 12 points
(Flash/MiMo/Pro, M=1/32/96/384, capacity 384): latency changes range
from
-1.07% to +0.64%. Flash M96 is 227.808 us before and
227.440 us after.

### Validation

```bash
pytest tests/moe/test_megamoe_fp4_ep.py tests/moe/test_megamoe_fp4_weights.py tests/moe/test_megamoe_fp4_sm90.py
```

CPU plan/cache and weight-layout checks pass. EP4 numerical,
receive-count,
workspace-reuse and CUDA graph checks pass on H20 and H200, including
Flash,
MiMo and Pro shapes and both push-dispatch barrier modes. H200 EP8
regression
outputs match the original NVFP4 fused/split kernels bitwise.

The benchmark defaults to warm-cache repeated calls; pass `--cold-l2`
and
`--repeats 1` for one cold-L2 invocation per sample.

## 🔍 Related Issues

None linked.

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

CPU targets: 32 passed. GPU targets: 8 passed on H200 (EP4/EP8),
6 passed on H20 (EP4). Tests cover dense-reference numerics, receive
counts,
workspace reuse, graph replay, production shapes and push-dispatch
barrier modes.
H200 NVFP4 EP8 source comparisons are bitwise exact.

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


## Reviewer Notes

The test checkbox covers PR-related targets; upstream multi-architecture
CI
requires authorization. EP4 uses the generic fused schedule and has not
been
tuned independently. This run remeasured EP8 performance on H200; H20
had four
free GPUs and was used for EP4 correctness verification. The previously
accepted
H20 NVFP4 hot-routing M1 deviation matches the original EP8 output
bitwise.
The H200 timing point marked Pending is not a settled performance
result.
Root README is unchanged.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added SM90 MegaMoE support for NVFP4 and MXFP4, including fused
execution for both formats and split execution for NVFP4.
* Added APIs for managing shared buffers, preparing weights, and
selecting NVFP4 split plans.
  * Added guidance for using and benchmarking the new functionality.

* **Tests**
* Added correctness coverage for distributed execution, weight
preparation, and supported rank configurations.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: aichenf <aichenf@nvidia.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: ouershua2299 <180947746+ouershua2299@users.noreply.github.com>

### [2355145](https://github.com/flashinfer-ai/flashinfer/commit/2355145edf0c0b76548e0d080f82ac0b3e6fdab5)

- **作者**: Vincent
- **时间**: 2026-10-13T22:18:54Z
- **提交信息**: fix(prims-ts): run the PrimTS attention suites on SM107 and fix FP8 x NVFP4 decode there (#6089)

## What

Follow-up to #5478, which ported prims_ts to the CuTe DSL 4.8 Task API
and widened the PrimTS test guards to SM107. On SM107 most of those
suites still skipped, so CI never ran the 4.8 path there. This PR turns
them on and fixes the two things that surfaced.

1. **Run the PrimTS suites on SM107**
(`test_attention_ts_{mla_decode,decode,block_sparse,q_token_kv_block_sparse_metadata}.py`).
96 tests carried both their file's explicit arch `skipif` (which admits
SM100/SM103/SM107) and `@pytest.mark.arch_blackwell`. Since #5384,
`tests/conftest.py` resolves that marker to SM100/SM103 only, so on
SM107 they skipped with `needs sm_100/sm_103 (Blackwell)` — e.g. 115 MLA
and 382 FMHA-decode cases in the Rubin job of #5478's pipeline, which
does install `nvidia-cutlass-dsl` 4.8.0. The marker is redundant with
the explicit guard on these tests and is removed from them only; the
marker definition and `conftest.py` are unchanged.
2. **FP8-Q × NVFP4-KV decode on SM107** (`tmem_transformed_kv.py`). With
CUDA 13.4 the kernel uses the packed `mul.e4m3x4.e2m1p4x4.e4m3x4`
multiply, which ptxas accepts for `sm_100a`/`sm_103a` but rejects for
`sm_107a` (`Instruction 'mul.e4m3x4.e2m1p4x4.e4m3x4' not supported on
.target 'sm_107a'`, in every rounding/satfinite spelling). SM107 now
takes the existing f16x2 conversion path the kernel already uses on
older toolkits; detection follows the other SM107-aware CuTe DSL kernels
(`is_rubin_cute_dsl_available()` + `Arch.sm_107` range). SM100/SM103
codegen is unchanged.
3.
**`test_attention_ts_decode_packed_q_sliding_window_clc_persistent`**.
The scheduler correctly selects CLC persistence only when the direct
launch exceeds one SM wave; the test's fixed 22-request shape crosses
that line at 148 SMs but not on larger parts. The request count now
scales with the device SM count.

## Validation

SM107 part, cu134 nightly CI image, `nvidia-cutlass-dsl[cu13]==4.8.0`
(passed / failed / skipped):

| file | `main` | this PR |
|---|---|---|
| `test_attention_ts_mla_decode.py` | 29 / 0 / 115 | **144 / 0 / 0** |
| `test_attention_ts_decode.py` | 283 / 0 / 382 | **665 / 0 / 0** |
| `test_attention_ts_block_sparse.py` | 152 / 0 / 84 | **235 / 0 / 1** |
| `test_attention_ts_q_token_kv_block_sparse_metadata.py` | 120 / 0 / 2
| **122 / 0 / 0** |

Before the kernel and CLC-test fixes, removing the markers alone gave
615 / 50 / 0 on `test_attention_ts_decode.py` (49 FP8-Q × NVFP4-KV ptxas
failures + the CLC policy assertion). The remaining skip is the opt-in
fatal-device-assertion test.

Not run on SM100/SM103 here: the kernel change keeps their `const_expr`
path identical, and the CLC test keeps 22 requests on 148-SM parts.

## Notes

The CuTe DSL 4.8 failures in the PrimTS **batched GEMM** suites
(`tests/prims_ts/`) are fixed separately in #6137. This branch briefly
carried the same fix (reverted in the last three commits); on an SM107
part with DSL 4.8.0 it took those suites from 16 failures to 0 with no
new failures, which supports #6137.

`test_attention_ts_context.py` (41) and `test_attention_ts_sage.py` (2)
also use `arch_blackwell`, but under guards that are themselves
SM100/SM103-only, so they are left alone.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved attention decoding compatibility across CUDA versions and GPU
architectures, including alternate calculation paths for hardware that
does not support packed multiplication.
* **Tests**
* Expanded GPU attention test coverage across supported architectures.
Decode test workloads now scale with the GPU’s processing capacity.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [caae48e](https://github.com/flashinfer-ai/flashinfer/commit/caae48e18eb6e187f2d53bcc6a9b7557483fec69)

- **作者**: eigen
- **时间**: 2026-10-13T21:59:23Z
- **提交信息**: perf(cake_all_gather_matmul): 128-wide main tile for small decode shards and a wide SM push for 8 MiB peer payloads (SM100a, SM103a) (#6440)

Regenerated export of the Cake all-gather matmul backend from the same
generator as #6254, rebased on `main`.
Two routing changes for the small-shard shapes, with the
per-architecture constants they need in the JIT loader:

1. **128-wide main tile.** Every main program keeps its 256-wide tile;
the five (world size, dtype, weight layout)
classes with a routed inventory row also ship a 128-wide twin
(`main_n128`, six pipeline stages, the same
operand pool). A call uses the twin when the narrow tiles fill the SMs
with fewer idle slots and the call has at
most `N128_MAX_WAVES_BY_ARCH[arch]` 256-wide waves: **two on SM100a, one
on SM103a** (the one-wave rows carry the
gain on SM103a; the two-wave M=512 rows regressed there, so the cap
differs per architecture). The host sequence
takes the tile width as a positional `block_n` argument and rejects a
width its route class does not ship.
2. **Wide SM push.** The SM push launch is chosen per call from the
per-peer payload: below 4 MiB the existing
`peer_push` program (32 CTAs per peer, one 16-byte vector in flight per
lane) is launched exactly as before; at or
above it the new `peer_push_wide` program (8 CTAs per peer, eight
vectors in flight per lane) writes the same bytes.
   Both push programs are compiled into every host sequence.

## Kernel set and loader surface

- Programs: 15 → 21 (2 barrier + 12 main + 1 push → 2 barrier + 12 main
+ 5 `main_n128` twins + 2 push). Against
`main` the 15 existing kernel files are byte-identical (same
content-hash names); six kernel files are new.
- New loader tables and helpers
(`flashinfer/jit/cake_all_gather_matmul.py`): `N128_CLASSES` (per
architecture:
SM100a `(4, bf16, k_major) (4, fp16, k_major) (8, bf16, k_major) (8,
bf16, n_major) (8, fp16, k_major)`;
SM103a `(4, bf16, k_major) (8, bf16, k_major) (8, bf16, n_major)`),
`SM_COUNT_BY_ARCH = {148, 148}`,
`N128_MAX_WAVES_BY_ARCH = {"sm_100a": 2, "sm_103a": 1}`, `MAIN_BLOCK_NS
= (256, 128)`, `main_block_n(...)`,
`main_tiles(..., block_n)`, `main_program(...)`;
`PUSH_WIDE_CTAS_PER_PEER = 8`, `PUSH_WIDE_UNROLL = 8`,
`PUSH_PAYLOAD_THRESHOLD_BYTES = 4 MiB`, `PUSH_CARVEOUT = -1` (driver
default), `push_payload_bytes(...)`,
`push_launch(...)`, `peer_push_wide_program()`. `BLOCK_N = 256` stays
the public constant; `N` stays a positive
multiple of 256; the public `all_gather_matmul` /
`prepare_all_gather_matmul` entry points and the docs are unchanged.
- Host sequences (24, one per dtype × world size × layout ×
architecture): `block_n` parameter, `kHasMainN128`
per route class, both push programs; the backend module
(`cake_all_gather_matmul.py`) resolves the push launch
and the tile width per call; the CPU test covers the new route tables,
the tile-width rule and the push dispatch.

## Validation

All runs used the generator at the commit that produced these kernels,
on 8×B300 (SM103a) and 8×B200 (SM100a)
nodes in the same pinned container on both. FlashInfer tests ran on this
PR's head.

- **Exactness.** Every row's output is bitwise identical to the previous
delivery's output on every rank
(int16-view SHA-256 of the raw output, eager, prepared and
CUDA-graph-captured entries, two independent launches):
SM100a 64 rows / 0 failures, SM103a 68 rows / 0 failures (the
generator's inventory at world sizes 2/4/8 plus odd-M
ad-hoc rows); launch-to-launch determinism held on every row.
Skew-injection stress (≥ 1e4 iterations per path,
world sizes 8 and 4): 8 rows / 0 mismatching iterations per
architecture. The 128-wide twins add no floating-point
instruction beyond their 256-wide twins (SASS opcode census, both
architectures).
- **compute-sanitizer synccheck**: `ERROR SUMMARY: 0 errors` on every
rank for the four representative rows
(TP2 1024×2048 and TP8 2048×1280 copy-engine push, TP4 512×2560 and TP8
125×2048 SM push) on both architectures.
- **Generator source vs this export (same kernels, the generator's
launcher vs the FlashInfer launcher; CUPTI GPU span
after a cold-L2 flush, 3 counterbalanced groups, per-arm medians;
correctness checked before and after):**

  SM103a (13 rows, all correct; geomean 0.9998):

| shape (TP, M×N, layout, dtype, entry) | route | source ms | export ms
| source / export |
  |---|---|---:|---:|---:|
| TP8 1024×2048 n_major bf16 one-shot | copy-engine, 256-wide | 0.332242
| 0.332051 | 1.0006 |
| TP8 512×1280 n_major bf16 prepared | SM push (wide), 256-wide |
0.169345 | 0.167969 | 1.0082 |
| TP8 125×1280 k_major bf16 prepared | SM push, **128-wide** | 0.085697
| 0.085473 | 1.0026 |
| TP8 512×1280 k_major bf16 prepared | SM push (wide), 256-wide |
0.161921 | 0.162145 | 0.9986 |
| TP8 125×7168 k_major bf16 prepared | SM push, 256-wide | 0.153330 |
0.153218 | 1.0007 |
| TP8 512×1280 k_major fp16 prepared | SM push (wide), 256-wide |
0.162625 | 0.162113 | 1.0032 |
| TP8 125×2048 n_major bf16 one-shot | SM push, **128-wide** | 0.082849
| 0.082881 | 0.9996 |
| TP4 512×2560 n_major bf16 prepared | SM push (wide), 256-wide |
0.118913 | 0.118689 | 1.0019 |
| TP4 125×2560 k_major bf16 prepared | SM push, **128-wide** | 0.065920
| 0.065857 | 1.0010 |
| TP4 512×2560 k_major bf16 prepared | SM push (wide), 256-wide |
0.117313 | 0.118465 | 0.9903 |
| TP4 2048×2560 k_major bf16 prepared | copy-engine, 256-wide | 0.287811
| 0.288643 | 0.9971 |
| TP4 512×14336 k_major bf16 prepared | copy-engine, 256-wide | 0.400964
| 0.401733 | 0.9981 |
| TP4 512×2560 k_major fp16 prepared | SM push (wide), 256-wide |
0.119074 | 0.119617 | 0.9955 |

  SM100a (12 rows, all correct; geomean 1.0002):

| shape (TP, M×N, layout, dtype, entry) | route | source ms | export ms
| source / export |
  |---|---|---:|---:|---:|
| TP8 512×1280 k_major fp16 prepared | SM push (wide), **128-wide** |
0.171999 | 0.171295 | 1.0041 |
| TP8 125×1280 k_major bf16 prepared | SM push, **128-wide** | 0.075872
| 0.075808 | 1.0008 |
| TP8 512×1280 k_major bf16 prepared | SM push (wide), **128-wide** |
0.171104 | 0.170016 | 1.0064 |
| TP8 125×2048 n_major bf16 one-shot | SM push, **128-wide** | 0.087424
| 0.086463 | 1.0111 |
| TP8 512×1280 n_major bf16 prepared | SM push (wide), **128-wide** |
0.172832 | 0.172063 | 1.0045 |
| TP8 125×7168 k_major bf16 prepared | SM push, 256-wide | 0.155296 |
0.155424 | 0.9992 |
| TP8 1024×2048 n_major bf16 one-shot | copy-engine, 256-wide | 0.312799
| 0.313856 | 0.9966 |
| TP4 512×2560 k_major fp16 prepared | SM push (wide), **128-wide** |
0.122431 | 0.122880 | 0.9963 |
| TP4 125×2560 k_major bf16 prepared | SM push, **128-wide** | 0.067840
| 0.068159 | 0.9953 |
| TP4 512×2560 k_major bf16 prepared | SM push (wide), **128-wide** |
0.121568 | 0.123008 | 0.9883 |
| TP4 512×14336 k_major bf16 prepared | copy-engine, 256-wide | 0.434798
| 0.434686 | 1.0003 |
| TP4 2048×2560 k_major bf16 prepared | copy-engine, 256-wide | 0.320175
| 0.320287 | 0.9997 |

The rows above are the routes whose program set changed (128-wide twin
and/or wide push) plus four
identical-program control rows per architecture; the remaining inventory
rows launch the same programs with the
  same grids as the previous delivery.

- **Speedup vs the previous delivery (same harness, rank-aligned CUPTI
A/B, two replicate passes of nine
counterbalanced ABBA groups, pooled per node — three passes where the
protocol's extension applied; > 1 = this PR faster):**

SM103a (8×B300, two independent hosts A / B; each cell = pooled median
of the rank-aligned CUPTI A/B over 18 (ws8)
or 27 (ws4, a third protocol pass on host A) counterbalanced groups;
strict read-out: all nine changed rows are
significantly faster on both hosts, the same-code control arm shows no
significant difference):

  | row (changed program) | ws | host A | host B |
  |---|---|---|---|
| TP4 125×2560 k_major bf16 prepared (128-wide) | 4 | 1.2626 | 1.2410 |
| TP4 512×2560 k_major fp16 prepared (wide push) | 4 | 1.0304 | 1.0444 |
| TP4 512×2560 k_major bf16 prepared (wide push) | 4 | 1.0286 | 1.0463 |
| TP4 512×2560 n_major bf16 prepared (wide push) | 4 | 1.0562 | 1.0497 |
| TP8 125×1280 k_major bf16 prepared (128-wide) | 8 | 1.1881 | 1.1370 |
| TP8 125×2048 n_major bf16 one-shot (128-wide) | 8 | 1.1395 | 1.2141 |
| TP8 512×1280 k_major fp16 prepared (wide push) | 8 | 1.1146 | 1.1273 |
| TP8 512×1280 k_major bf16 prepared (wide push) | 8 | 1.1036 | 1.1088 |
| TP8 512×1280 n_major bf16 prepared (wide push) | 8 | 1.1401 | 1.0960 |
  | *identical-program controls (same 45-row pass)* | | | |
| TP4 512×14336 k_major bf16 prepared (copy-engine) | 4 | 0.9957 |
0.9999 |
| TP4 2048×2560 k_major bf16 prepared (copy-engine) | 4 | 1.0162 |
1.0078 |
| TP8 125×7168 k_major bf16 prepared (256-wide) | 8 | 1.0150 | 1.0080 |
| TP8 1024×2048 n_major bf16 one-shot (copy-engine) | 8 | 0.9991 |
1.0089 |

Same-code control arm (this PR's module with the previous delivery's
knobs, i.e. program-identical A/A) on the nine
  changed rows: 0.9846 … 1.0287, none significant.

SM100a (8×B200, two independent hosts C / D; pooled median over 18
counterbalanced groups per host; strict
read-out: the same-code control arm shows no significant difference, the
no-regression gate (all 45 rows
≥ exp(−delta_res)) passed on both hosts; rows marked † are faster on
both hosts but not statistically significant
  on one of them — reported as measured, not credited as a gain):

  | row (changed program) | ws | host C | host D |
  |---|---|---|---|
| TP4 125×2560 k_major bf16 prepared (128-wide) | 4 | 1.2115 | 1.2446 |
| TP4 512×2560 k_major fp16 prepared (128-wide + wide push) † | 4 |
1.0151 | 1.0347 |
| TP4 512×2560 k_major bf16 prepared (128-wide + wide push) † | 4 |
1.0173 | 1.0350 |
| TP8 125×1280 k_major bf16 prepared (128-wide) | 8 | 1.1769 | 1.1748 |
| TP8 125×2048 n_major bf16 one-shot (128-wide) | 8 | 1.1528 | 1.1651 |
| TP8 512×1280 k_major fp16 prepared (128-wide + wide push) | 8 | 1.0737
| 1.0576 |
| TP8 512×1280 k_major bf16 prepared (128-wide + wide push) | 8 | 1.0844
| 1.0776 |
| TP8 512×1280 n_major bf16 prepared (128-wide + wide push) † | 8 |
1.0529 | 1.0283 |
  | *identical-program controls (same 45-row pass)* | | | |
| TP4 512×14336 k_major bf16 prepared (copy-engine) | 4 | 1.0043 |
1.0009 |
| TP4 2048×2560 k_major bf16 prepared (copy-engine) | 4 | 1.0015 |
1.0070 |
| TP8 125×7168 k_major bf16 prepared (256-wide) | 8 | 1.0005 | 1.0227 |
| TP8 1024×2048 n_major bf16 one-shot (copy-engine) | 8 | 1.0394 |
0.9905 |

Same-code control arm on the eight changed rows: 0.9846 … 1.0287
(SM103a), 0.97 … 1.03 (SM100a), none significant.

- **FlashInfer tests on this head:**
`tests/comm/test_all_gather_matmul_cake.py` (225 CPU cases, 1 visible
GPU) and `tests/comm/test_all_gather_matmul_cake_e2e.py` (3 cases on 8
GPUs and 3 cases on 4 GPUs) pass on 8×B300
  and 8×B200.
- Pre-commit fixed points: the Python files are ruff 0.12.8 fixed
points; generated CUDA is formatted with the
  pinned clang-format 19.1.1; the shared device helpers are unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added automatic selection between 256- and 128-wide matrix tiles where
supported, with validation for compatible output shapes and launch
grids.
* Added payload-aware peer transfers that select a suitable transfer
strategy based on shard size.
* Expanded all-gather matrix multiplication support across additional
rank counts and data types.
* **Performance**
* Updated launch configuration to account for device architecture and
available streaming multiprocessors.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [887e930](https://github.com/flashinfer-ai/flashinfer/commit/887e93058d6d6074fe22124e202a90f6d0335bd2)

- **作者**: AichenF
- **时间**: 2026-10-13T21:58:50Z
- **提交信息**: Fix: cake fmha smallm hang and graph launch (#6061)

<!-- .github/pull_request_template.md -->

## 📌 Description

Two fixes for the Cake FMHA BF16 head-dim-256 small-M speculative decode
route
(`decode_native_bf16_hd256_smallm`, #5369), found while serving
Qwen3.5-35B-A3B (TP=2, DFlash-7 speculative decoding) in SGLang on B200
with
CUDA graphs.

### 1. `fix(cake_fmha): order small-M corr_scale publish after PV to fix
a decode deadlock`

The route can hang the GPU. The softmax warps published the rescale
factor
and arrived on the `corr_scale` mbarrier **before** waiting for
`p_empty`,
while QK(n+1) is issued without waiting on the correction warps. A
correction
warp that started late could therefore see softmax complete `corr_scale`
phases n **and** n+1 before executing its parity wait for phase n. The
parity
aliases, the correction warps never pass, `p_full` never completes, and
the
CTA deadlocks — so every other Split-KV CTA spins forever in the fused
merge
barrier.

Evidence: per-role progress probes in host-mapped memory, read while
hung
(q_len 7, 8 q heads / 1 KV head, kv 60177, page 64, 148 Split-KV CTAs):

| CTA 116 role | state |
|---|---|
| softmax (both warpgroups) | iteration 1, waiting on `p_empty` —
already arrived on `corr_scale` for iterations 0 **and** 1 |
| correction (4 warps) | iteration 0, waiting on `corr_scale` phase 0 |
| MMA | iteration 0, waiting on `p_full` |
| load | waiting on `kv_empty` (PV0) |

The other 147 CTAs had finished and were spinning in the merge barrier.
It
reproduces within a few hundred CUDA-graph replays when other GPU work
runs
between launches (as in a decode loop); back-to-back launches rarely hit
it.

Fix: publish `smem_scale` and arrive on `corr_scale` after the `p_empty`
wait.
PV(n-1) needs the correction warps' `p_full` arrival for n-1, so softmax
can
lead correction by at most one `corr_scale` phase. Correction already
waits on
`o_ready` (the same PV completion) before rescaling, so the move costs
nothing. Applied to all six generated bodies (n32/n64 × p16/p32/p64; one
arch-neutral body per variant since #5933).

### 2. `perf(cake_fmha): remove CUDA-graph launch overhead of the
small-M hd256 decode route`

In a CUDA-graph decode loop the route was ~12 us/layer faster than
trtllm-gen (26.3 vs 38.4 us) yet no faster end to end. Every launch
added a
counter-reset memset node, and the device-resident TMA descriptors
(which may
only be captured after an eager prewarm of the exact tensor binding)
forced
callers to copy Q into a stable buffer, adding a memcpy node. The extra
non-kernel graph nodes serialized ~25 us of launch latency in front of
each
attention kernel.

- Q/K/V TMA descriptors are now `__grid_constant__` kernel parameters.
CUDA
  graphs capture the descriptor bytes, so there are no device descriptor
slots, no prewarm, and no stable-address requirement on `query`/`out`.
The
slot pool is removed from the small-M JIT binding, and the global-memory
  tensormap acquire fences no longer apply.
- Merge tickets live in the caller's persistent, zero-initialized
`multi_ctas_kv_counter_buffer` (the trtllm-gen contract; the kernel's
last
CTA already resets them), so there is no per-launch memset. The
workspace
counters plus memset remain the fallback when that buffer is too small.

The kernel bodies are Cake-generated, so the same two changes should
also
land in the Cake generator so that the next export carries them. Rebased
onto
the #5932/#5933 layout (one arch-neutral body per variant,
`registry.json`
without artifact digests); those refactors leave both issues in place.

### Results (B200, re-measured on main f2794d589)

| | main | main + this PR |
|---|---|---|
| standalone small-M kernel, graph-warm (q_len 7, kv 60008, page 64;
trtllm-gen 33.0 us) | 27.0 us | **23.5 us** |
| per-layer attention window in SGLang's decode graph, TP0 / TP1 |
trtllm-gen 38.8 / 38.7 us (Cake: hangs; with Q-copy + memset nodes 41.1
us) | **24.9 / 24.2 us** |
| full attention per verify step (10 layers), TP0 / TP1 | trtllm-gen 388
/ 384 us | **249 / 241 us** |
| SGLang TPOT vs trtllm-gen, requests with identical outputs | — |
**−3.5%** (two runs; median −3.2% / −3.3%) |
| hang repro (interleaved reference, 400 replays; 2110-replay KV sweep;
eager sweep) | hangs | passes |

SGLang setup: Qwen3.5-35B-A3B, TP=2, DFlash-7, ISL 60000 / OSL 400 / BS
1, CUDA
graphs, 3 warmup + 20 formal requests, same node and session (trtllm-gen
and
Cake runs interleaved). TPOT is compared on the requests whose outputs
match
the trtllm-gen baseline, since ~1e-4 attention numerics change greedy
outputs
(and DFlash acceptance) on others. The same fixes on FlashInfer 0.7.1rc2
gave
−4.0% / −4.3%. Kernel outputs are bit-identical before and after these
changes
(max |Δ| vs an FP32 reference: 7.3e-5).

### Tests

`pytest tests/attention/test_cake_fmha.py -k "smallm or manifest or
registry or binding"`
→ 53 passed on B200 (SM100), including the new
`test_cake_decode_bf16_hd256_smallm_cuda_graph_without_prewarm` (capture
with
no prewarm and a transient query, replay over growing KV lengths with
other
GPU work between launches, dense reference check, merge tickets
self-reset).
All six small-M variants were run against the trtllm-gen reference
(n32_p16 and
n64_p32 out of tree, with the graph test). SM103 was not run (no
hardware).








<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved reliability of BF16 attention decoding, including CUDA graph
replay with changing sequence lengths and queries.
* Corrected synchronization around attention computation to ensure
updates occur in the proper order.
* Improved handling of multi-CTA merge counters, with workspace fallback
when the provided buffer is unsuitable.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ef39929](https://github.com/flashinfer-ai/flashinfer/commit/ef399292e89124952c210ee6b05c2963bba0d6e1)

- **作者**: Brandon Zhang
- **时间**: 2026-10-13T21:54:11Z
- **提交信息**: refactor(concat_mla_kv_quant_fp8): per-backend module registry, backend-neutral names (#6373)

<!-- .github/pull_request_template.md -->

## 📌 Description

Follow-up to #5667, addressing the post-merge review comment about the
`_specialized_module` global. No behaviour change; a naming and
structure cleanup of `flashinfer/mla_kv_pack.py`:

- **Per-backend module registry.** The specialized kernel's loaded
module lived in a bare module global with a `global` statement, while
the Cake modules lived in a dict keyed by target and head group. Both
now live in registries: `_backend_modules` keyed by backend name
(`"specialized"`), and `_cake_modules` for the Cake programs. A third
backend would add an entry, not another global.
- **Backend-neutral names where the thing is not backend-specific.**
`specialized_dispatches` counted every fused dispatch of either backend;
it is now `fused_dispatches`. `_specialized_supported` was the check
across backends; it is now `_fused_supported` (the per-backend check
`_specialized_backend_supported` keeps its name).
`specialized_module_loaded` becomes `backend_modules_loaded`, reporting
per backend.
- **No compatibility aliases.** These are private diagnostics
(`_concat_mla_kv_quant_fp8_stats()`) and private helpers; the tests that
read them are updated in the same commit.

The public API (`concat_mla_kv_quant_fp8(..., backend=...)`), the
backend names, the dispatch rules and the kernels are untouched.

## 🔍 Related Issues

- #5667 (the review comment this addresses)
- #6163

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

`tests/utils/test_concat_mla_kv_quant_fp8.py` updated for the renamed
stats key, check function and module registry (mechanical). RTX 5080 (SM
12.0, specialized backend live): 106 passed / 23 skipped across the
module tests, the trace reference test and the AOT inventory test. H100
(SM 9.0, both backends fall back): 44 passed. Pre-commit clean.

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

## Reviewer Notes

Pure refactor, 51 insertions / 52 deletions across two files. The
module-level names are private to `flashinfer/mla_kv_pack.py`; nothing
outside it imported them. AI assistance was used to prepare this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved fused MLA KV packing behavior across backend selection and
CUDA graph capture, including capture attempted before just-in-time
initialization.
* **Diagnostics**
* Dispatch reporting now includes aggregate fused-call counts alongside
per-backend counts, making it easier to see total fused activity as well
as how calls are distributed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Signed-off-by: Brandon Zhang <31413216+brandonfzhang@users.noreply.github.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [b3887a5](https://github.com/flashinfer-ai/flashinfer/commit/b3887a5ed6323743ed31d4cfd26f9347d1ee2a9a)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-13T21:37:47Z
- **提交信息**: fix(tests): keep cuTile groupwise-GEMM and block-sparse tests inside the CI time budget (#6110)

## Summary

Two test-only changes that bring two cuTile test files back inside the
CI time budget. Since the CUDA 13 CI images gained the `tileiras`
compiler (#4939), their cuTile cases are no longer skipped on
cu130/cu134, and they now dominate or exceed the per-batch and slurm
limits. No library code changes.

Both files share the same root cause: the cuTile kernels bake shapes
into `ct.Constant`, so nearly every parametrization is a fresh
`tileiras` JIT, and an exhaustive config search multiplies that.

### 1. `tests/gemm/test_groupwise_scaled_gemm_fp8.py`: reduce the cuTile
shape grid
- 749 cuTile cases that used to skip now run on cu13x. Counts go from
2081 passed / 1624 skipped (cu129, and rc3-era cu130) to 2830 / 875.
- The file went from ~4.5 min to 59-67 min per GB200/GB300 shard
(flashinfer-ci pipeline 71817031, v0.7.1rc4).
- cuTile now runs on a representative subset: 12 dense shapes (single
and multi K tile, small and large M) and 16 grouped cases covering both
group-config branches (`avg_m < 256` → swap_ab `BLOCK_M=64`; otherwise
`BLOCK_M=128`). The cutlass, trtllm and other backends keep the full
grid.
- Two cuTile paths that no grid reached now have cases in existing
tests. `test_fp8_groupwise_gemm_small_batch_size` (M = 1/4/16/32) also
runs `backend="cutile"`, which covers M below `BLOCK_M` and the `BLOCK_M
<= M` config prune. `test_fp8_groupwise_group_gemm_uneven_segments`
gains segments `(300, 0, 260, 500)`, where avg ≥ 256 selects
`BLOCK_M=128` and partial tiles spill into the next group.
- Expected file time is ~7-8 min.

### 2. `tests/attention/test_block_sparse_cutile.py`: validate one
config per case
- 660 cases × up to 10 autotune configs (3 on SM90) means up to 6600
compiles in one `solo` batch, and only the winning config's output is
ever checked.
- VR200 cu134 passed in 1h59m31s against the 2 h per-batch cap. The
GB200/GB300 shard-2 cu130/cu134 jobs were killed at the 4 h slurm limit
inside this file, with 0 failures before the kill.
- A module-scoped autouse fixture now sets
`fmha_prefill_bsr_cutile._AUTOTUNE_DISABLED` (the same switch as
`FLASHINFER_CUTILE_AUTOTUNE_DISABLED=1`). It clears
`_prefill_paged_lpt_tune_cache` on entry and exit, so single-config
results don't leak into later tests.
- Expected time is ~12-25 min on VR200 and ~25-50 min on Blackwell
(estimate). Autotuning for users is unchanged.

## Design notes (moved from code comments)

**`test_groupwise_scaled_gemm_fp8.py` cuTile grid.** The cuTile kernels
bake M/N/K (and TOTAL_M/Q for the group kernel) in as `ct.Constant`, so
every distinct shape is a fresh `tileiras` JIT, and the dense path also
runs a 24-config `exhaustive_search` per shape. On the full
cutlass/trtllm grids that is ~9 s/case (dense) and ~4 s/case (group),
i.e. ~60 min per file on SM100/SM103 once the CUDA 13 CI images ship
`tileiras` (#4939). The subset still covers a single K tile and multiple
K tiles, small and large M (swap_ab / `BLOCK_M` pruning), and both
group-config branches (`avg_m < 256` → swap_ab `BLOCK_M=64`; `avg_m >=
256` → `BLOCK_M=128`).

**`test_block_sparse_cutile.py` fixture.** Every case bakes its shape
(`NUM_BATCH`, `NUM_HEADS`, `MAX_SEQ_LEN`, `SWIZZLE`, ...) into cuTile
constants, so each case pays a fresh `exhaustive_search` that compiles
up to 10 configs (3 on SM90) and then checks only the winner: up to 6600
config compiles for 660 cases, ~2 h on VR200, nearly all spent on
configs whose output is never compared. The fixture uses the same switch
as `FLASHINFER_CUTILE_AUTOTUNE_DISABLED=1`, scoped to this module, and
clears `_prefill_paged_lpt_tune_cache` on exit so single-config results
don't leak into later tests in the same process.

## Follow-up (not in this PR)
Passing M (and the other shape params) to the cuTile GEMM and prefill
kernels at runtime, instead of as `ct.Constant`, would remove the
per-shape compile for users too.

## Test plan
- [x] pre-commit (ruff, mypy, format) passes
- [x] GPU run on B200 with the rc4 cu130 CI image
(`flashinfer-ci-cu130:20260930-b1420f1`, cold JIT cache, release-v0.7.1
+ this PR): `test_groupwise_scaled_gemm_fp8.py` 2142 passed / 1581
skipped / 0 failed in 14.8 min (was 65 min in rc4 CI);
`test_block_sparse_cutile.py` 660 passed / 0 failed in 26.5 min (rc4 CI
finished 0/660 in 2 h)
- [ ] flashinfer-ci GB/VR200 lanes complete within limits

This should also be cherry-picked to `release-v0.7.1`, since rc4 CI hits
both timeouts.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Tests**
* Updated cuTile GEMM coverage to focus on selected shape ranges, test
small-batch cases across supported backends, and include additional
uneven-segment sizes. Cases now account for backend support, scale-mode
compatibility, and compiler availability.
* Block-sparse prefill tests run with autotuning disabled, restore its
prior setting afterward, and clear the tuning cache before and after the
test module.
  * No exported or public interfaces changed.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [059e51e](https://github.com/flashinfer-ai/flashinfer/commit/059e51ea577a45c81d11053acad8855d4f7ee565)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-13T21:26:42Z
- **提交信息**: revert(moe): re-enable PDL in the trtllm-gen fused-MoE path on SM107 (Rubin) (#6271)

## 📌 Description

This reverts #4806, which forces `enable_pdl=False` at the six
trtllm-gen fused-MoE entry points on SM107 (Rubin), even when the caller
explicitly passes `True`.

#4806 was explicitly a mitigation for an intermittent `unspecified
launch failure` / hang in the renormalize-routing tests, and its
description asks for a revert once the launch-dependency chain is
cleared on Rubin. That failure no longer reproduces on current `main`:

- **Hardware:** GR100 (SM107, cc 10.7), CUDA 13.4, CuTe DSL 4.8. `main`
@ 461037fbf with this revert applied. Startup checks confirmed the guard
is gone and `enable_pdl` resolves to `True`.
- **Single pass, PDL on (all passed):**
  - `test_trtllm_gen_fused_moe_routing_renormalize_{bf16,fp4,fp8}.py`
  - `test_trtllm_gen_routed_fused_moe.py`
- **Repeated runs, PDL on:** each renormalize file that #4806 identified
(BF16 / MxInt4 and FP4) was run 25 times, each run in a fresh process
with a hang timeout. All 50 runs passed, with no crashes and no hangs.
#4806 reported roughly 4 crashes in 21 full-file runs, so a bug still
present at that rate would almost certainly have shown up.
- **Full `test_trtllm_gen_fused_moe.py`:** one complete run passed with
0 failures. Its main cases take PDL from `device_support_pdl`, so PDL is
on for SM107. A few tests parametrize `enable_pdl` over False/True.
- **`test_trtllm_gen_routed_fused_moe.py`:** run 10 more times; all
passed.

I have not pinned down a root cause for the original failure. The most
plausible candidate is #5444 (initialize TRT-LLM routing padding for TMA
gathers), which has landed since #4806 and changes what the routing
kernels write before the expert GEMMs consume it.

The CUTLASS MoE path was never gated and is unchanged. Hopper and
Blackwell are unaffected: the removed gate only returned `False` for cc
10.7.

## 🔍 Related Issues

Reverts #4806. Addresses #5473. Supersedes #5899, the narrower
NVFP4/SiTU-only opt-in, which becomes unnecessary.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [ ] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (Ruff lint/format on the changed file
only.)

## 🧪 Tests

- [ ] Tests have been added or updated as needed. (None. This removes a
dispatch clamp, and the existing MoE suite exercises the PDL-on path.)
- [x] All tests are passing (`unittest`, etc.). (MoE files on SM107,
listed above.)

## Reviewer Notes

`test_trtllm_gen_routing.py` skips on SM107 ("trtllm-gen routing is not
implemented on SM107"), so the standalone routing-kernel tests add no
SM107 coverage. Routing is exercised end to end through the fused-MoE
files above.

The repeated runs used one single-GPU Rubin dev node. A broader soak on
Rubin CI after merge would still be useful.

AI-assisted (Claude Code).

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Bug Fixes**
* TRT-LLM MoE operations on SM107 devices now follow the standard PDL
support check instead of having PDL disabled by a device-specific
override.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2d5b283](https://github.com/flashinfer-ai/flashinfer/commit/2d5b283d3ca2676c83fbfd746622b5c00c046044)

- **作者**: Yanqin Zhai
- **时间**: 2026-10-13T21:11:52Z
- **提交信息**: reduce-frost-host-overhead (#6309)

<!-- .github/pull_request_template.md -->

## 📌 Description

Refactor Frost’s host logic to follow the standard MoELayer backend
registration and dispatch path. Replace per-call candidate discovery
with shared eligibility checks and winner caching. Consolidate common
host code, cache compiler metadata and prepared execution state, reuse
compatible weight views, and preserve per-call launch state.

Warm eager CPU overhead drops by approximately 90% across BF16, MXFP8,
NVFP4, and MXFP8 × MXFP4 on the 76 paired cases where both versions
select Frost.

| Recipe | Before | After | Reduction |
|---|---:|---:|---:|
| BF16 | 400\.94 | 36\.49 | 90\.90% |
| MXFP8 | 572\.53 | 55\.67 | 90\.28% |
| NVFP4 | 591\.05 | 54\.46 | 90\.79% |
| MXFP8/MXFP4 | 1159\.02 | 99\.02 | 91\.46% |

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
## Summary by CodeRabbit

- **New Features**
- cuDNN Frost is now included in the default fused MoE backend
candidates, with unsupported inputs skipped during selection.
  - MXFP8 and mixed MXFP8/MXFP4 paths support per-group GEMM scaling.
- Added `refresh_backends()` to refresh backend selection after compiler
or artifact configuration changes.
- Frost supports reusable, token-bucketed preparation and graph replay
with in-place weight and scale updates when tensor pointers, shapes, and
layouts remain stable.
- **Bug Fixes**
- Improved handling of supported scale layouts and tensor strides across
Frost quantization paths.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [43d7e40](https://github.com/flashinfer-ai/flashinfer/commit/43d7e40881cf28cb72fb4f91b675531a8ad015eb)

- **作者**: Jimmy Zhou
- **时间**: 2026-10-13T21:04:08Z
- **提交信息**: fix(prims-ts): compile batched GEMM under CuTe DSL 4.8 (#6137)

<!-- .github/pull_request_template.md -->

## 📌 Description

Fixes 16 of the 17 failures in the VR200 (GR100, SM107) unit-test lane
on v0.7.1rc4 (flashinfer-ci jobs 471243498 / 471243499, CuTe DSL 4.8.0,
cu134). All 16 also reproduce on `main` with DSL 4.8.0. The 17th, an MSA
NVFP4 decode race, is fixed separately in #6138.

**1. Prims-TS batched GEMM under CuTe DSL 4.8** (`fix(prims-ts): compile
batched GEMM under CuTe DSL 4.8`). DSL 4.8 rejects two patterns that 4.7
accepted:
- `SmemDeepSeekSfAbResource.create_function_variables` bound the
epilogue accumulator state (`dsfp8_acc_rmem_state` / `_1_state`), and
both the load warps' and the epilogue warps' init hooks call it. 4.8
rejects the epilogue's rebind with `SCOPE_READ_NEVER_SET`, because the
load branch's vector does not dominate it. Now only the epilogue path
binds it, through the helper `reset_dequant_accumulator` already needed.
13 tests:
`test_batched_gemm_fp8_block.py::test_deepseek_fp8_fc{1,2}_correctness_small[*]`
and `test_batched_gemm_fp8.py::*_deepseek_*_tile8_small`.
- The BF16 kernel's early exit nested the whole body under a runtime `if
token_cta_idx < num_non_exiting_ctas`. The body appends to the
`SmemAllocator`'s Python lists, which 4.8 rejects inside a runtime
branch (`CONTAINER_LIST_SHAPE_MUTATED`). Inactive CTAs now
`prims.exit()` and the body runs unconditionally. The predicate is
CTA-uniform, no barrier has been touched yet, and nothing followed the
old branch. `prims.exit` exists in DSL 4.7.0 and 4.8.0. 2 tests:
`test_batched_gemm_bf16_fc2.py::TestBf16Fc2ReferenceCheck::test_early_exit_*`.

**2. Import-isolation test under DSL 4.8** (`test(prims-ts): …`). DSL
4.8 ships its own `WorkTileInfo` subclass in `task_scheduling.resources`
and no longer monkey-patches `cutlass.utils…WorkTileInfo`, so
`task_scheduling_scope()` correctly has nothing to swap. The test now
asserts the swap only when the installed DSL patches the class (4.7).
The restore and isolation assertions still run on both versions. This
change is test-only.

## 🔍 Related Issues

- v0.7.1rc4 VR200 CI: flashinfer-ci jobs 471243498 and 471243499
(internal).
- Follows #5478, which made Prims-TS **attention** work with DSL 4.8.
This PR covers batched GEMM.
- #6089 does not overlap: it changes only the Prims-TS attention suites.
- Companion: #6138 (MSA NVFP4 pinned decode race). Supersedes part of
#6113.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (I ran the hooks on the changed files:
clang-format, ruff check, ruff format and the whitespace checks all
pass.)

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

Validated in the CI image `flashinfer-ci-cu134:20260930-b1420f1` (passed
/ skipped / failed). These runs used the combined branch, i.e. this PR
plus #6138; the two PRs touch disjoint files.

| Branch | GPU | CuTe DSL | Scope | Result |
|---|---|---|---|---|
| `main` @16f0f22c8 (before) | GR100 | 4.8.0 | the 16 failing nodes |
**16 failed** |
| combined | GR100 | 4.8.0 | `tests/prims_ts/`,
`tests/test_prims_ts_import_isolation.py`,
`tests/msa_ops/test_msa_nvfp4_decode_sm100.py` | 695 / 118 / **0** |
| combined | B200 | 4.7.0 (image default) | same | 759 / 54 / **0** |
| `release-v0.7.1` + combined | GR100 | 4.8.0 | the affected files | 343
/ 0 / **0** |

Not run: B300/GB300, and DSL 4.8 on Blackwell.

## Reviewer Notes

- `prims.exit()` replaces a runtime `if` around the entire BF16 kernel
body. Please confirm that nothing should run for an exiting CTA. PDL: an
exiting CTA counts as having triggered dependents, the same as a CTA
that skipped the body and returned.
- Cherry-picks cleanly onto `release-v0.7.1`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Bug Fixes**
* Improved execution handling for batched GEMM kernels that use early
exits, including consistent handling of work that should not continue.
* Improved initialization and resetting of dequantization resources
during kernel execution.
* **Tests**
* Updated import-isolation checks to account for differences in CUTLASS
DSL behavior, verifying the appropriate behavior in either case.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [879202a](https://github.com/flashinfer-ai/flashinfer/commit/879202ac5ca4c2f2bf47004555682b0d5ec173f5)

- **作者**: eigen
- **时间**: 2026-10-13T20:40:39Z
- **提交信息**: feat(cake_msa): Cake NVFP4 MSA decode use_cache_hit union programs for sm_100a and sm_103a (#6387)

# feat(msa_ops): Cake NVFP4 MSA decode `use_cache_hit` union programs
for `sm_100a` and `sm_103a`

Tracker: #4254 (Cake generated-program deliveries). Target: `main` @
`b77de25d433ff5082247b8e306c3aa54857e3ed7`. This branch is based on
`ae312f7cc1723b06fda5168105ade0f328ee47d8` (the merge base); the 32
files changed on `main` since then do not overlap the 64 files in this
PR.

## What this PR delivers

1. **`use_cache_hit` for `prepare_msa_nvfp4_sparse_decode`**
(experimental `flashinfer/experimental/msa_nvfp4_decode`, public entry
`flashinfer/msa_ops/sparse_decode.py`): request-packed union decode
programs (`UNION_Q ∈ {2, 4}` × `UNION_SPLITS ∈ {1, 2, 4, 8}`) for
`sm_100a` and `sm_103a`. Semantics: `False` = the existing per-row
routes (unchanged bytes), `True` = the union program for a uniform
`seqlen_q` in [2, 4] (`ValueError` above 4, no-op at 1, must be built
before CUDA-graph capture), `"auto"` (default) = the `False` routes.
`sm_107a` keeps the existing programs (no union program is traced for
it). The stable `msa_sparse_decode_attention` API is unchanged; the
option is available only through the experimental entry.
2. Tests, benchmark and docs:
`tests/experimental/test_cake_msa_nvfp4_decode.py` (+
`tests/test_helpers/cake_msa_nvfp4_inputs.py`),
`benchmarks/bench_cake_msa_nvfp4_decode.py`, package README.

All generated sources are produced by the Cake exporter from the audited
kernel programs (constant-clone audit, review, apply); no third-party
proprietary source is included.

## Measurement receipts (frozen protocol, paired source/export arms,
CUPTI, cold L2, same-arm preconditioning, fixed sample counts; gates:
source/export ≥ 0.97, directional disagreement ≤ 0.08, endpoint drift ≤
0.02, FP32 oracle rel-L2 ≤ 0.004, atol = rtol = 1e-2)

| part | shapes | result |
|---|---|---|
| NVFP4 decode `sm_100a` (B200, 148 SMs) | 78 (16 per-row-route + 62
`uch`) | 78 / 78 PASS; source/export ratio mean 1.0026, min 0.9711, max
1.0407 |
| NVFP4 merged complete run (all three parts) | 172 | `complete = true`,
`all_passed = true`; source/export geomean 1.0019 |
| NVFP4 decode `sm_103a` (GB300, 152 SMs) | 78 | 78 / 78 PASS after one
closed-prior retry round: the first round read 76 / 78 (two `b1` `uch`
rows at 0.950 on the ≥ 0.97 source/export parity gate with every
validity gate passing); the retry re-measured only those two rows
(1.0156 / 1.0065) and retained the other 76; first-round receipts
preserved |
| NVFP4 decode `sm_107a` (R200, 212 SMs) | 16 | 16 / 16 PASS
(directional ≤ 0.0039) |

Representative `uch` rows (exported union program, CUPTI µs;
`route/export` = the FlashInfer packed-NVFP4 paged-KV route arm over the
export; source and export are bit-identical):

| row | B200 export µs | B200 route/export | GB300 export µs | GB300
route/export |
|---|---:|---:|---:|---:|
| `uch_tp2_q4_b1_kv8k_ov0` | 17.70 | 0.541 | 16.90 | 0.532 |
| `uch_tp2_q4_b8_kv8k_ov50` | 31.42 | 0.497 | 29.57 | 0.491 |
| `uch_cov_tp2_q2_b16_kv8k` | 15.55 | 1.014 | 14.53 | 1.018 |
| `uch_tp2_q4_b32_kv150k_ov100` | 25.63 | 1.507 | 23.74 | 1.515 |
| `uch_tp4_q4_b128_kv150k_ov100` | 27.52 | 2.657 | 24.45 | 2.775 |

Over the 62 `uch` rows per architecture the export is faster than the
route on 29 (B200) / 30 (GB300) rows (route/export geomean 0.876 /
0.896): the union program pays off at large batch and loses at
`b1`/`b8`, which is why `"auto"` keeps the per-row routes and
`use_cache_hit=True` is an explicit opt-in.

## Tests run
- B200, applied worktree: `pytest
tests/experimental/test_cake_msa_nvfp4_decode.py -k 'union or
use_cache_hit or split_factor or plan_rule'` → 74 passed, 1 skipped.
- GB300, applied worktree: same selection → 74 passed, 1 skipped.
- Full `tests/experimental/test_cake_msa_nvfp4_decode.py` on a
publication worktree whose files under this PR's paths are
byte-identical to this branch's head (the experimental ICP indexer
branch stacked on top of this one; its commit touches none of this PR's
files): 120 passed / 2 skipped on 4 × GB300, including
`test_matches_the_existing_nvfp4_route`, which builds the upstream
route.

## Notes
- The experimental ICP indexer chain (`prepare_msa_icp_indexer`) is not
part of this PR. It stays on a separate fork branch stacked on this one
and will be proposed on its own.
- CI: two comments per push as agreed on the tracker.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added an optional request-packed decode route for multi-token queries
that combines selected pages across tokens to reduce repeated page
loading. Queries of length 2–4 are supported; length 1 retains the
existing route, and longer queries are rejected when this option is
enabled.
* Added `"auto"` as a scheduling option, which currently uses the
existing per-token route.
* **Documentation**
* Expanded guidance and benchmarks for the new route, including
speculative decoding, selection overlap, and CUDA Graph requirements.
* **Tests**
* Added coverage for routing, numerical accuracy, selection isolation,
varied page layouts, and graph capture and replay.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [ea5f740](https://github.com/flashinfer-ai/flashinfer/commit/ea5f740951ac45f8a73aed036e28a5a9c7e57838)

- **作者**: eigen
- **时间**: 2026-10-13T20:11:55Z
- **提交信息**: perf(cake_kimi_k3_fp8_projection): round 10 — cluster split-K pair GEMM, prefetched stream-K, 128×384 pair-tile GEMM, interleaved confirm protocol and dispatch-table re-tune (SM100a, SM103a) (#6433)

## Summary

Round 10 of the Cake `kimi_k3_fp8_projection` generated-program export
(FP8 block-scaled projection GEMMs of the Kimi-K3 KDA / MLA families —
22 families, 352 contract rows per GPU: 198 perf rows = 22 (N, K)
families × M in {1, 8, 64, 256, 512, 1024, 2048, 4096, 16384} and 154
correctness rows at M 3 / 129 / 513 / 1000 / 1023 / 1025 / 4097 with
strided views — on SM100 + SM103). It builds on the round-9 package on
FlashInfer main `23dc1d595` (#6335) and, unlike round 9 (table + one
barrier), adds three new GEMM program forms, the host-mirror grammar
that selects them, the dispatch-table adoptions below, and two
exporter-side receipt changes. The round-9 record is the comparison
baseline of every number below ("record" = the round-9 package /
receipts).

- **New kernel forms (Weave programs; all 2-CTA `cta_group::2`, FP32
accumulation and BF16 output rounding unchanged; `_cs2` and `_n384` run
on the 128-K operand hand-off, `_skp4` on the record's 256-wide / 256-K
form — only the `_n192_k128_skp` twin is 128-K):**
- **Cluster split-K pair GEMM `_cs2`** (`gemm_tstore_n192_k128_cs2` /
`gemm_rstaged_n192_k128_cs2`; the S = 3 twins exist in the registry but
are not dispatched): a cluster of 2S CTAs = S pairs per output tile;
pair p streams the K iterations `[nk·p/S, nk·(p+1)/S)`; the finished
FP32 half-tiles travel through DSMEM (`cp.async.bulk`, `mapa`) into the
dead operand ring and the owning pair adds them in ascending pair =
ascending K order; no CLC ring. Adopted on SM103 for the narrow-N `kv_a`
family at M 1025..2048 (cell `5,28,2048`, decode `t128_p3(_tso)` -> GEMM
route): 24.432 -> 23.616 us.
- **Prefetched stream-K `_skp` / `_skp4`** (new table key `gemm_skp`,
host precedence `cs > sk > skp > skf`): the stream-K fix-up adds the
partner's TMEM pre-sum in fixed 16-column (bn 192) / 32-column (bn 256)
pieces with a register-staged, chunk-local prefetch; the regime-U
schedule declares `clc_unreached`. Adopted on SM100 `12,28,4096`
(`tp8:q_proj:4096`, replaces the ordered stream-K `_sk` +
`gemm_sk_ksplit 16`): 56.61 -> 53.152 us.
- **128×384 pair-tile GEMM `_n384`** (`gemm_tstore_n384_k128` /
`gemm_rstaged_n384_k128`, plus the `_g64` raster twins and
`gemm_tstore_g64` / `gemm_rstaged_g64`): a v2 operand ring of five
43,008-B half-slots and one shared 8,192-B staging tile, three MMAs per
slot (logical N 128 × cta_group 2), 384 accumulator columns, per-part
epilogue drains; `gemm_bn 384` forces `gemm_bk 128`, `ts_slots 1`, `pf
0`, plain CLC. Adopted on `96,28,512` on both GPUs (`tp1:q_proj:512`:
SM100 43.872 -> 42.688 us, SM103 40.928 -> 39.744 us), on SM103
`48,28,1024` (`tp8:fused_qkvg:1024`: 42.336 -> 38.336 us) and SM103
`12,28,4096` (`tp8:q_proj:4096`: 54.34 -> 48.576 us).
- **Dispatch-table convergence (strict two-pass rule, both GPUs):**
every runtime-selectable lever was re-measured on every open contract
row under paired same-GPU A/B (node alone, 3 × 1000 cold-L2 graph-replay
samples per screen; confirms under R8-3 — quiet run + two shared runs ≥
1.02 with A/A and no-op twin in [0.99, 1.01] — for rows above 20 us, and
under the new interleaved protocol below for rows at or below 20 us);
the table was frozen only after two consecutive clean full passes per
GPU found no gate-compliant win ≥ 2 %. SM103 converged after full passes
4 + 5 (clean), SM100 after full passes 5 + 6 (clean; 7 of the 9 pass-6
screen hits carried a prior verdict on an unchanged program, 2 confirmed
measured-not-adopted). Table-only adoptions (all bit-exact, Tier A):
SM100 — `192,2,256` gemm_bn 192 + gemm_bk 128 (1.078), `12,1,4096`
gemm_bn 192 + gemm_bk 128 (1.057), `1,28,512` quant_units 2
(1.025–1.028), `1,28,1024` pf 1 (1.024–1.027), `5,28,512` quant_units 2
(1.018–1.021), `144,6,256` gemm_bk 128 (1.024–1.026), `24,2,16384`
gemm_stages 2 + gemm_ts_slots 4 (quiet 1.024, shared 1.027 / 1.028) and
then gemm_bk 128 on top (quiet 1.026, shared 1.029 / 1.028; 35.392 ->
34.24 us). SM103 — `144,6,16384` gemm_bk 128 (quiet 1.021, shared 1.020
/ 1.019; 286.24 us) and `18,6,16384` gemm_bk 128 (1.017 / 1.017 / 1.018;
52.03 us), `50,28,512` gemm_bn 192 (quiet 1.053, shared 1.060 / 1.059;
29.696 -> 26.592 us), `192,2,2048` gemm_bk 128 (quiet 1.016, shared
1.023 / 1.022), `96,1,4096` gemm_bk 128 (1.017 / 1.029 / 1.028),
`144,6,256` gemm_bk 128 (1.025 / 1.027 / 1.027), `18,6,4096` gemm_pf 1
(1.0168 × 3). Three explicit record cells were added without a lever so
that every table key exists on both architectures (SM100 `18,6,16384`,
`5,28,2048`, `192,2,2048`).
- **Measured gains of the structural forms (paired same-GPU A/B ratios,
record / new; each unlabelled triple = quiet run, shared run 1, shared
run 2):** `_cs2` SM103 `5,28,2048` screen 1.0346 / 1.0352 (tp1 / tp8),
R8-3 quiet 1.0298 / 1.0285, shared 1.0342 / 1.0271; `_skp4` SM100
`12,28,4096` 1.0313 / 1.0295 / 1.0289; `_n384` SM100 `96,28,512` 1.0322
× 3, SM103 `96,28,512` quiet 1.0370 / shared 1.0370 / 1.0362, SM103
`48,28,1024` 1.0604 / 1.0751 / 1.0734, SM103 `12,28,4096` quiet 1.0357 /
shared 1.0349 / 1.0356.
- **Confirm protocol for timer-quantized rows (new, "S5 v2"):** CUPTI
timestamps are quantized to 128 ns (1.0–1.4 % of a 9–13 us row) and
successive CUDA-graph instances of the same program differ by an
additive 0.2–0.5 us, so the round-9 control arms invalidated every
shared run on four bit-exact candidates. Rows at or below 20 us are now
confirmed by an interleaved production, candidate, production (A,B,A)
run per row and round whose per-round statistic is median(production,
graph instance 0) / median(candidate, graph instance 1) on the process's
first three graph instances (production instance 2 = the embedded A/A
check), 3 rounds × ≥ 1000 cold-L2 samples, PASS = every round ≥ 1.015
with the A/A control in band and bit-exact output. The protocol was
validated on A/A first: 17/17 rows within ±0.0035 on both GPUs (the
first version, one fresh graph instance per measurement, failed its A/A
validation — only 1/17 rows on SM103 and 2/17 on SM100 passed — and was
discarded). Rows above 20 us keep R8-3 (13 rows ≥ 173 us showed
1282–1961 MHz clock drift between instances on SM100).
- **Host mirror (`cake_backend.py`):** the table grammar gains `gemm_cs`
(2 | 3; refuses `gemm_skp` / `gemm_sk*` on the same cell), `gemm_skp`
(prefetched stream-K form), `gemm_bn 384` with `gemm_gm` (raster group)
and the `N384` cell-conflict rule; plan precedence `cs_plan > sk_plan >
skp_plan > skf_plan`; kernel-symbol order
`[_n192|_n384][_g64][_k128][_cs<S>][_s<n>][_ts<n>][_sk|_skf<n>|_sks<n>|_skp<S>][_pf<D>]`;
the mirror still refuses any table field it does not read. Templates and
the test module are formatted with the repo's pinned ruff 0.12.8.
- **Export protocol / receipts (two exporter-side changes):** (a)
prior-results retention — the exporter now attests the whole delivered
closure before it retains a prior receipt, so a resumed or retried
export keeps every prior passing row (round 9 lost two retry rounds to a
silent drop); (b) every correctness receipt records the output digest
(`output_sha256` of the source and the exported program), and the
round's list of re-association rows is derived statically from the table
diff and confirmed from those digests after parity instead of from a
per-cell form rule (round 9's rule over-flagged 19–20 rows per GPU).
Measurement semantics are unchanged from round 9 (SM-clock trace +
clock-stability precondition, 3 counterbalanced groups × 2000 samples, 8
graph instances, cold L2, CUPTI; validity gates
`directional_disagreement ≤ 0.08`, `endpoint_drift ≤ 0.02`).
- **Package:** 224 files, 9,995,698 bytes, combined content hash
`5aef77861b5f9a4d` (SM103 parity run; the same hash from the
delivery-patch step: 77 files changed vs `23dc1d595`, 1,381,806-byte
patch, 136 status entries, 190 `.cu` files, 95 registry hashes, 0
unreferenced) ; the SM100 parity run and the SM100 delivery-patch step
report the identical hash (`5aef77861b5f9a4d`, 224 files, 9,995,698
bytes) and a byte-identical patch (same SHA-256, prefix
`fe76bb59521eee1f…`, 1,381,806 bytes). Delivery patch vs `23dc1d595`: 77
name-status entries — 10 added, 5 modified, 59 renamed, 3 deleted — over
136 paths, all under `flashinfer/experimental/kimi_k3_fp8_projection/`
or `tests/*kimi_k3_fp8*` (0 paths outside the owned prefixes); `git
apply --check` clean on `23dc1d595` (77 files, +11,939 / −4,021).

## Exactness and parity

- Two kinds of adopted levers, as in round 9. **Bit-exact (Tier A)**
levers — tile shape (`gemm_bn` 192 / 384, `gemm_bk` 128), pipeline depth
/ TMA-store slots (`gemm_stages`, `gemm_ts_slots`), prefetch depth
(`gemm_pf`), quantization width (`quant_units`) and the ordered stream-K
tail — leave every output bit-identical to the round-9 package.
**Re-association (Tier A′)** levers change only the order in which exact
FP32 partial sums are added; they ship only where an exactness packet
shows, on every touched row, that each output element is bit-identical
to the record's or differs by exactly 1 BF16 ulp (or, for near-zero
outputs, by at most 2^-24 × Σ|a_k b_k|, one FP32 rounding of the exact
dot product's magnitude scale), that max |err| vs the FP64-accumulated
dequantized reference did not grow by more than 1 BF16 ulp at that
element's magnitude, that the row's mean |err| is within 1e-3 relative,
and that eager and CUDA-graph replay are bit-identical. UE8M0 block-FP8
recipe, FP32 accumulation of every product and BF16 output rounding are
unchanged; no fast-math, no approximate or non-deterministic reductions,
no reduced-precision intermediates, no atomics into the accumulator (the
split-K tile counters are ordering counters, not reductions), no
tolerance change.
- **Tier A′ cells of this round (three):** SM103 `5,28,2048` (`_cs2`:
the two pairs' exact-order K-partials are added in ascending pair order
after a fixed-slot DSMEM exchange), SM103 `48,28,1024` (`_n384` replaces
the record's stream-K fix-up `_skf`), SM100 `12,28,4096` (`_skp4`
replaces the ordered stream-K `_sk`). Rows expected to differ from the
round-9 package: SM103 `tp1_kv_a_m2048`, `tp8_kv_a_m2048`,
`tp1_kv_a_m1025_corr`, `tp8_kv_a_m1025_corr`, `tp8_fused_qkvg_m1024` (5
rows); SM100 `tp8_q_proj_m4096` (1 row); every other adoption keeps the
re-association token of the record (verified by the derivation script on
all 352 rows per GPU), and the sealed parity's DIFFER set is
cross-checked against this list from the output digests: SM103:
`PARITY_CROSSCHECK differ=5 unlisted_differ=[] listed_but_equal=[]`,
`STATIC_VS_CONFIRM identical` (digest audit: 352 rows with a parity
digest, 5 labelled by digest, 5 published = 5 listed, 0 receipt-digest
inconsistencies; `ROWSAUDIT_DONE rc=0`); SM100: `PARITY_CROSSCHECK
differ=1 unlisted_differ=[] listed_but_equal=[]`, `STATIC_VS_CONFIRM
identical` (digest audit: 352 rows with a parity digest, 1 labelled by
digest, 1 published = 1 listed, 0 receipt-digest inconsistencies; the
round-9 per-cell form rule alone would have flagged 22 SM100 rows — the
digests label exactly the one listed row; `ROWSAUDIT_DONE rc=0`).
- **Packets** (tool `w2_exactness_r9.py` 2.5, refined rule 5(a), seed
622, graph replay on): `_cs2` SM103 `5,28,2048` — overall PASS, 20 (row,
arm) PASS in the levers' cells, 30 rows not bit-identical (within 1 ulp
/ the 5(a) bound), graph replay identical; `_n384` SM103 `48,28,1024` —
overall PASS (8 PASS, 2 NOOP): `tp8:fused_qkvg:1024` 594 elements at
exactly 1 BF16 ulp and 37 elements beyond 1 ulp, every one within the
refined 5(a) bound (max 0.178 of one FP32 rounding of the exact scale;
for 14 of the 37 the error vs the FP64 reference is above the record's +
1 ulp at that element, so they are admitted only by the near-zero
exception and are listed in the packet), max |err| vs the FP64 reference
unchanged on the worst row (0.0267 -> 0.0267), mean |err| relative
change 1.35e-8; `_skp4` SM100 `12,28,4096` — PASS 4/4 rows on the unit
tree (`tp8:q_proj:4096` instance `_skp4@g148`, 292 elements not
bit-identical, all within rule 5), eager = graph replay, repeat
identical.
- **Rejected by the exactness gate (disclosure):** the runtime-catalog
arm `gemm_bn 192` (with or without `gemm_bk 128`) on SM100
`tp8:f_b:16384` (cell `12,1,16384`, the two-stage / four-slot TMA-store
instance) had read 1.035–1.043× in the timing protocol but is NOT
bit-exact; its packet shows a wrong output (23,537 elements differ, max
abs error vs FP64 1.387 against the record's 0.0039) and
non-deterministic graph replay, so the arm is excluded
(measured-not-adopted under rule 5). No shipped instance combines the
192-wide tile with the stage / slot tokens; the combination is now a
known instance defect tracked on the Cake side (knob guard + harness
alarm follow-ups).
- **Bitwise checks on all 704 contract rows (352 per GPU)** — (a)
exported program vs Cake source on every receipt, (b) round-10 output vs
the round-9 package with every differing row a listed Tier A′ row: SM103
(delivered root, 352 rows): `PARITY_HASH_DONE rows=352 errors=0` for
both the round-9 package and this one; `record-vs-new bitwise parity
(sm_103a): {'total': 352, 'equal': 347, 'differ': 5, 'record_error': 0,
'new_error': 0, 'launcher_differ': 0, 'repeat_differ': 0, 'missing':
0}`; `PARITY_TIERAP differ=5 tierap_listed=5 unlisted_differ=0
other_nonequal=0` — the 5 differing rows are exactly the 5 SM103 rows
listed above; `PARITY_DONE record=0 new=0 compare=0 tierap_rule=0`.
SM100 (delivered root, 352 rows): `PARITY_HASH_DONE rows=352 errors=0`
for both packages; `record-vs-new bitwise parity (sm_100a): {'total':
352, 'equal': 351, 'differ': 1, 'record_error': 0, 'new_error': 0,
'launcher_differ': 0, 'repeat_differ': 0, 'missing': 0}`;
`tp8_q_proj_m4096: DIFFER`; `PARITY_TIERAP differ=1 tierap_listed=1
unlisted_differ=0 other_nonequal=0` — the one differing row is the one
SM100 row listed above; `PARITY_DONE record=0 new=0 compare=0
tierap_rule=0`.

## Validation

- Sealed export receipts on this exact render (protocol above, node
alone, 4 GPUs; `TARGET_REVISION` = FlashInfer `23dc1d595`). SM103 — the
programs and dispatch tables of this PR were first exported in full on
the previous tip (T8; identical programs / tables, test text only
differs): `receipts=353 passed=353 gate_fail=0 exception=0 unstable=0
no_trace=0 bitwise_ok=353 forms_changed=19 tierap=5 sm_counts=[152]
median_mhz=1560-2070`, `TARGET_REVISION_OK`, FI tests rc 0; that export
was interrupted once by a scheduler requeue after 279 of 353 shapes and
completed from its checkpoint on a second node of the same kind (279 +
69 + 6 receipts in three exporter roots, composed into one 353/353 root;
one correctness row, `tp1_f_b_m1000_corr`, re-measured once). The sealed
receipts of record are produced by a retention round on the final tip:
every receipt whose program identity reproduces byte-for-byte on the
final tip is retained by the exporter's identity check, every other row
is re-measured — result on the final tip: `prior results: retained 353
row(s) from 3 root(s); dropped 0 row(s)` (every receipt's program
identity reproduced exactly; nothing re-measured), `EXPORT_ROWS sm_103a
receipts=353 passed=353 gate_fail=0 exception=0 unstable=0 no_trace=0
bitwise_ok=353 forms_changed=19 tierap=5 sm_counts=[152]
median_mhz=1560-2070`, `TARGET_REVISION_OK`, `EXPORT_FULL_DONE … exrun=0
fi_tests=0`; the three roots composed into the delivered root:
`MERGE_ROWS sm_103a receipts=353 passed=353 failed=0 roots=3` (the once
re-measured `tp1_f_b_m1000_corr` taken from the later root). The
measurement allocation was preempted by the scheduler right after the
retention round finished; the receipts were already closed, and the
post-export checks (parity, hash audit, floors, A2, A3) ran on a
replacement allocation of the same GPU kind (all complete; results in
this section); the per-row audit on the delivered root re-read
`EXPORT_ROWS sm_103a receipts=353 passed=353 gate_fail=0 exception=0
unstable=0 no_trace=0 bitwise_ok=353 forms_changed=19 tierap=5
sm_counts=[152] median_mhz=1560-2070`, `TARGET_REVISION_OK`; the SM103
per-row summary of the delivered root reads `receipts 353 | passed 353 |
gate-fail 0 | exception 0 | clock-unstable 0 | no-trace 0 | Cake<->FI
bitwise ok 353 | forms changed vs record 19 | Tier A' flagged 5 (hash 5
on 352 hashed rows, form rule 4, over-flag 0)`. SM100 — the sealed run
on the final tip (`EXPORT_ROWS sm_100a receipts=353 passed=350
gate_fail=2 exception=1 unstable=0 no_trace=1 bitwise_ok=352`, FI tests
rc 0) refused three rows on environment validity (one SM-clock-trace
coverage gap; two endpoint-drift readings, 0.0529 and 0.0286, above the
0.02 gate with the directional gates passed); their single re-measure
under the round-8 Q7 rule (same protocol, node alone, shape-filtered;
the other receipts retained by the exporter's identity check — `prior
results: retained 350 row(s) from 1 root(s); dropped 3 row(s)
(failed_original=2, receipt_incomplete=1)`) passed all three:
endpoint_drift 0.0000 / 0.0021 / 0.0118 (gate 0.02), FI tests `75
passed`. The delivered SM100 root is the composition of the sealed
re-measured receipts over the first run (`MERGE_ROWS sm_100a
receipts=353 passed=353 failed=0 roots=2`; 3 receipts superseded by the
re-measure — the same Q7 composition round 9 disclosed for its one
re-measured row); on the composed root: `EXPORT_ROWS sm_100a
receipts=353 passed=353 gate_fail=0 exception=0 unstable=0 no_trace=0
bitwise_ok=353 forms_changed=29 tierap=1 sm_counts=[148]
median_mhz=1372-1965`, `TARGET_REVISION_OK`; its per-row summary reads
`receipts 353 | passed 353 | gate-fail 0 | exception 0 | clock-unstable
0 | no-trace 0 | Cake<->FI bitwise ok 353 | forms changed vs record 29 |
Tier A' flagged 1 (hash 1 on 352 hashed rows, form rule 22, over-flag
22)`.
- `tests/experimental/test_cake_kimi_k3_fp8_projection.py` on this
render: green inside the SM103 pre-measurement seed of the previous tip
(`FI_TESTS_RC=0`, same programs) and inside its full export
(`fi_tests=0`); on the final tip: SM103 pre-measurement seed
`EXPORT_SEED_DONE exrun=0 fi_tests=0 ruff=0` (`75 passed`,
`FI_TESTS_RC=0`) and the SM103 retention round `fi_tests=0` (`75
passed`); SM100 pre-measurement seed on the final tip `EXPORT_SEED_DONE
exrun=0 fi_tests=0 ruff=0` (`75 passed`, `FI_TESTS_RC=0`). The test
module gained the round-10 expectations (the `_cs2` cell on SM103, the
384-wide pair-tile cells, the `_skp4` kernel key, precedence `sk > skp >
skf` and persistent grid, the explicit record cells); three text defects
of the SM100 `_skp4` / SM103 `_n384` expectations were found by the
pre-measurement seeds of earlier tips and fixed before the sealed
receipts of record (the last one: the SM100 seed expected the
data-parallel grid 192 where the plan launches the persistent stream-K
grid 148). `ruff format --check` + `ruff check` (FlashInfer's pinned
ruff 0.12.8, run inside the FlashInfer tree): "All checks passed!" on
the templates and the delivered copies (the dedicated ruff steps of the
previous tips and the SM103 pre-measurement seeds of the previous and
final tip; SM100 seed of the final tip) ; on the final tip both seeds
(SM103 and SM100) report `ruff check` "All checks passed!" on both file
sets and `format --check` "3 files already formatted" / "4 files already
formatted", `FI_RUFF_RC=0`.
- GPU gates on the previous tip (identical programs / tables) on both
GPUs: `pytest -m gpu -k kimi_k3_fp8` 25 passed (13 record rows + the 12
new-form rows: `_cs2`/`_cs3` × tstore/rstaged, `_skp`/`_skp4`, `_n384` ±
`_g64` × tstore/rstaged, `_g64`) and the kimi bench-regression PASS on
SM103 and SM100; the exporter CPU test module
(`loom/tests/export/test_kimi_k3_fp8_projection_export.py`) 95 passed
and the FlashInfer-mirror CPU test 23 passed / 52 skipped; the same GPU
gates on the final tip: `25 passed` on both GPUs and the kimi
bench-regression PASS (SM100 2662 TFLOPS vs floor 2275, +17.0 %; SM103
2569 TFLOPS vs floor 2199, +16.8 %); the 0-GPU set on the integration
head of that run (the final tip merged onto the then-current Cake main
plus one exporter-side fix — a `receipt_unsupported` drop reason for
wrong-schema prior receipts; nothing in the exported programs):
FlashInfer-mirror CPU test `23 passed, 52 skipped`, repo ruff set
unchanged (3 pre-existing findings on both sides), export CPU set 95
passed, and a render census against the final tip of `IDENTICAL` on both
architectures (SM100 103 / SM103 107 programs identical, 0 differing, 0
new); the exporter + bench-harness CPU suites (`loom/tests/infra`,
`loom/tests/export`, `-m "not gpu"`) on the final Cake tip and on the
merge-request head, attributed against their bases by exact-id re-runs
and a same-composition re-check: 0 regressions attributable to this
change. One stale test pin in the Cake tree (the SM103 12,28,4096
planner-table cell after the `_n384` table adoption) was fixed by a
test-only commit; the pre-existing failure population of those suites is
identical on the bases.
- `compute-sanitizer` synccheck + racecheck on every new instance /
touched row at its adoption tip: `_cs2` rows synccheck 0 errors on both
GPUs; `_n384` adoption rows synccheck 0 errors and racecheck 0 hazards
on both GPUs (same counts on the record control); `_skp` rows synccheck
+ racecheck 0 errors, deadlock 0; the SM103 pf-1 and the SM100 bk-128
adoption tips synccheck + racecheck 0 errors. Known tool limitation
(disclosed, not a kernel finding): racecheck on the 128-K hand-off GEMM
family (including the record's own `_k128` rows) ends in `Internal
Sanitizer Error: The Sanitizer failed to handle a hardware exception`
with 0 "Race reported"; the record-tree control reproduces the identical
signature, so the `_cs` rows inherit it; on SM100 the racecheck of the
pf-1 adoption row timed out identically on tip and record
(deadlock-detector lines of the instrumented cluster decode), the
completed row was clean.
- Paired same-GPU no-regression check vs the round-9 kernel of record
(A3: 5 × 1-GPU 44-row shards × 3 rounds per GPU, every row below 0.98
re-measured A,B,A,B with kernel symbols): SM100 `AB3_COMBINED sm_100a
rows=198 geomean=1.0016 min=0.9548 (tp8:kv_b:512, ab3-a3r10f-s03)
below_0.98=2 FAIL`: `tp8:kv_b:512` 0.9548 (rounds 0.9548 / 0.9548 /
1.009) and `tp1:fused_qkvg:4096` 0.9612 (0.9612 / 0.9484 / 1.0227); the
A,B,A,B probe (node alone, one GPU, kernel symbols recorded) read
`tp8:kv_b:512` = 6.62 us in all four probes (`quant_act` 2.08 / 2.14 /
2.08 / 2.14 + `proj_decode_t128_p3_tso` 5.38 in every probe, same
symbols in both trees) and `tp1:fused_qkvg:4096` (`proj_gemm_tstore` in
both arms) 980.54 / 1007.94 / 1003.52 / 966.75 us — interleaved means
992.0 (record) vs 987.3 us (this PR), within-tree spread 2.3 % / 4.2 % =
the shard rounds' own run-to-run variance → both rows attributed to
measurement variance, no kernel change; after attribution geomean
1.0016, no attributable row below 0.98. SM103 `AB3_COMBINED sm_103a
rows=198 geomean=1.0012 min=0.9535 (tp8:o_proj:256, ab3-a3r10f-s01)
below_0.98=2 FAIL`: `tp8:o_proj:256` 0.9535 (1.0 / 0.9535 / 0.9535) and
`tp8:kv_b:256` 0.9617 (0.9617 × 3); the A,B,A,B probe read
`tp8:o_proj:256` = 9.22 us and `tp8:kv_b:256` = 5.82 us in all four arms
with identical kernel symbols (`quant_act` + `proj_decode_t128_p3_tso` /
`proj_decode_t64_p4_tso`) → quantized medians of tiny decode rows,
measurement artifact, no kernel regression; after attribution geomean
1.0012, no attributable row below 0.98. Weak-but-passing rows
(0.98–0.995): SM100 `tp8:fused_qkv_a:256` 0.9802, `tp1:o_proj:16384`
0.9819, `tp8:fused_qkvg:16384` 0.9848, `tp8:fused_qkvg:256` 0.9876;
SM103 `tp8:f_b:512` 0.9892, `tp8:kv_b:512` 0.9901,
`tp8:in_proj_qkvgfab:1024` 0.9906, `tp1:o_proj:16384` 0.9936.
- Versus the fastest FP8 chain that produced a timing in the measurement
container (FI CUTLASS groupwise, FI TRT-LLM groupwise, cuTile groupwise,
FI DeepGEMM grouped; DeepGEMM ue8m0 on SM103) on FlashInfer main
`23dc1d595`, CUDA-graph replay, CUPTI kernel time, one process per peer:
SM103 `A2_COMBINED sm_103a rows=198 measured=198
geomean_vs_fastest_complete=2.2384 min=1.0403 below_1x=0 PASS per_peer:
flashinfer_cutile_groupwise=n72/gm2.219/min1.159
flashinfer_cutlass_groupwise=n198/gm2.466/min1.070
flashinfer_trtllm_groupwise=n180/gm3.526/min1.040` — cuTile groupwise
produced a timing on 72 of the 198 rows (42 shapes per shard are
unsupported by that kernel and one of its 24 autotune configurations
fails with `TileCompilerExecutionError: Return code 5`, as in round 9);
DeepGEMM ue8m0 produced no timing on any row in the measurement
container (verbatim: `RuntimeError: interpreter INTERNAL ASSERT FAILED
at
"/opt/_internal/cpython-3.12.13/lib/python3.12/site-packages/torch/include/c10/core/impl/PyObjectSlot.h":30,
… cannot access PyObject for Tensor - no interpreter set`; same as round
9) and FI DeepGEMM grouped produced no timing on any row either (per
row: `ValueError: cubin not registered:
kernel.fp8_m_grouped_gemm.<kernel hash>`). SM100: `A2_COMBINED sm_100a
rows=198 measured=198 geomean_vs_fastest_complete=2.2299 min=0.9642
below_1x=1 FAIL per_peer:
flashinfer_cutile_groupwise=n72/gm2.179/min1.164
flashinfer_cutlass_groupwise=n198/gm2.461/min1.084
flashinfer_trtllm_groupwise=n180/gm3.501/min0.964` — cuTile groupwise
partial on 72 rows as on SM103 (same unsupported shapes, same failing
autotune configuration); FI DeepGEMM grouped produced no timing on any
row (`ValueError: cubin not registered:
kernel.fp8_m_grouped_gemm.<kernel hash>` per row; DeepGEMM ue8m0 is not
part of the SM100 peer set). The single below-1× reading,
`tp1_in_proj_qkvgfab_m8` at 0.964× vs TRT-LLM groupwise, is a
measurement outlier of this PR's arm in that one peer process (77.69 us
there, vs 71.1–73.2 us for the identical, unchanged kernel in the same
shard's other peer processes, in the sealed receipt, in both A3 arms and
in round 9's A2; the peer's 74.91 us matches its round-9 reading of
75.01 us). Three re-measures under the same A2 pairing — two independent
single-row processes and the whole 66-row shard — read 1.032× / 1.028× /
worst 1.021× (71.84 / 72.22 / 73.18 us vs 74.11 / 74.24 / 74.75 us for
the peer). After re-measure every SM100 perf row is above 1.00× vs the
fastest complete chain (CUTLASS groupwise n198 min 1.084; TRT-LLM
groupwise n180 min 1.021 after re-measure; cuTile partial n72 min
1.164); the original combined line above is kept verbatim as a
disclosure, together with the three re-measure artifacts.
- Roofline fraction (per-row floor = max(bytes / 8 TB/s, FLOPs / 4500
TFLOPS) + the measured launch ramp, re-measured this round: 3.872 us
SM103 / 4.096 us SM100; clock-normalized floor scales the compute term
by f_nominal / f_measured with f_nominal = 4.5e15 / (SM count × 16384) =
1807 MHz for 152 SMs / 1856 MHz for 148 SMs): the round-9 receipts
re-scored with this round's ramp read geomean 1.588 nominal / 1.628
clock-normalized on SM103 (class A ≤ 1.10×: 8 rows) and 1.659 / 1.644 on
SM100 (5 rows); after this round on SM103 (delivered root, 198 perf
rows, all with a clock trace): geomean 1.628 (round-9 receipts,
clock-normalized) -> 1.595 nominal / 1.636 clock-normalized, class A 7
rows (8 before); informational attainable fraction 1.501 (10 rows at or
below 1.10×; 1.545 / 9 rows with the HBM-read calibration); SM100
(delivered root, 198 perf rows, all with a clock trace): geomean 1.644
(round-9 receipts, clock-normalized) -> 1.673 nominal / 1.655
clock-normalized, class A 4 rows (`tp8_f_b_m1`, `tp8_f_b_m8`,
`tp8_f_b_m64`, `tp8_kv_b_m8`; 5 before); informational attainable
fraction 1.466 (18 rows at or below 1.10×; 1.533 / 16 rows with the
HBM-read calibration). The before -> after geomeans compare two sealed
sessions at their own clocks, not a paired A/B; the paired vs-record
verdict is the A3 check above. An informational attainable column (HBM
copy plateau 6.530 TB/s SM103 / 6.064 TB/s SM100; sustained dense FP8
GEMM of the record's own route 90.5 % / 85.5 % of the 16384 FLOP/clk/SM
peak at the measured clock) is reported next to the floors; it is not a
class rule.
- Host launcher per-call cost (the W4 bench, new launcher vs the round-9
launcher on the five W4 rows; the bench prints one JSON record per row —
field names verbatim below, two samples each, us rounded to 0.01 — and
an exit status, no separate verdict line): on the final tip both GPUs
completed with exit 0 and every row reports `bitexact=true
graph_bitexact=true r8_bitexact=true r8_plan_equal=true`. SM103
`receipt_same_out_us` / `r8_launcher_us` / `r7_launcher_us`: tp8:q_b:1
5.78, 5.53 / 10.61, 10.26 / 5.78, 5.62; tp8:q_b:64 7.54, 7.45 / 13.99,
13.74 / 7.68, 7.62; tp8:o_proj:1 5.58, 5.41 / 10.29, 9.96 / 5.75, 5.38;
tp8:q_proj:256 7.75, 7.68 / 13.81, 13.58 / 7.76, 7.49;
tp8:fused_qkv_a:1024 8.05, 7.81 / 14.51, 13.82 / 8.30, 7.97;
`chain_vs_r8_us` negative on all 7 samples of every row (−6.608 … −4.378
us). SM100 `receipt_same_out_us` / `r8_launcher_us` / `r7_launcher_us`:
tp8:q_b:1 4.63, 4.56 / 7.71, 7.67 / 4.81, 4.80; tp8:q_b:64 6.01, 5.98 /
10.46, 10.43 / 6.28, 6.27; tp8:o_proj:1 4.68, 4.64 / 7.80, 7.79 / 4.90,
4.89; tp8:q_proj:256 6.41, 6.35 / 11.09, 11.03 / 6.68, 6.53;
tp8:fused_qkv_a:1024 6.50, 6.38 / 10.92, 10.88 / 7.03, 6.95;
`chain_vs_r8_us` negative on all 7 samples of every row (−4.749 … −3.045
us).

## Checklist

- [x] ruff 0.12.8 `format --check` + `check` clean on the templates and
the delivered Python files (SM103 seed of the previous tip:
`FI_RUFF_RC=0`; pinned-ruff step on the previous tip: PASS; final tip:
SM103 and SM100 seeds `FI_RUFF_RC=0` (`ruff check`: "All checks passed!"
on the templates and on the delivered copies; `format --check`: "3 files
already formatted" / "4 files already formatted" on each); no separate
pinned-ruff step ran on the final tip — the two seeds' pinned-ruff pass
(check + format, both GPUs, `FI_RUFF_RC=0`) is the final-tip result, and
the repository-side ruff over the mirror sources on the test-only fix
tips reports "All checks passed!")
- [ ] `tests/experimental/test_cake_kimi_k3_fp8_projection.py` green on
SM100 and SM103 on the delivered package (SM103: green on the previous
tip's seed + full export; final tip: seed `75 passed` + retention round
`fi_tests=0` (`75 passed`); SM100: seed on the final tip `75 passed`;
sealed run `FI_TESTS_RC=0` and `75 passed` inside the Q7 re-measure run)
- [ ] Sealed export receipt summaries + 704-row bitwise parity reported
in this description (SM103 and SM100 receipts + 352-row parity per GPU
above; the per-row tables and the evidence manifest are kept with the
Cake-side delivery record)
- [x] `/bot run` + `run-ci` label cycled after every push (added at PR
creation; repeated after each later push)
- [x] Tracker #4254 bullet after #6335 (`- #6433`, added at PR creation)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [d14254a](https://github.com/flashinfer-ai/flashinfer/commit/d14254aff38f6e710292447e1e535b739766aab4)

- **作者**: Adrian
- **时间**: 2026-10-13T20:05:42Z
- **提交信息**: chore: add righthandabacus to code owners (#6432)

<!-- .github/pull_request_template.md -->

## 📌 Description

Add `@righthandabacus` to the catch-all code owners and add explicit
ownership rules for `scripts/test_sharding/` and `tests/test_sharding/`.
The sharding rules list `@righthandabacus`, `@dierksen`, `@bkryu`, and
`@yongwww`, plus the full-codebase approvers required by the CODEOWNERS
policy.

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

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- No runtime tests needed for an ownership configuration change.
- `pre-commit run --files .github/CODEOWNERS` and `git diff --check`
passed.
- Verified the sharding paths exist, both ownership rules include
`@righthandabacus`, and both retain all required full-codebase
approvers.

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

CODEOWNERS uses the last matching rule, so each new sharding rule
explicitly retains all full-codebase approvers listed in the file
header. The PR contains only the CODEOWNERS change.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Chores**
* Updated repository ownership coverage for general files and
test-related areas. These administrative changes do not affect product
features, workflows, or behavior, and no end-user-visible changes are
included in this pull request.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [01cd50c](https://github.com/flashinfer-ai/flashinfer/commit/01cd50cf725bf220b186eab9eeed1634681ce4ca)

- **作者**: Vincent
- **时间**: 2026-10-13T19:50:04Z
- **提交信息**: feat(moe): support swiglu_limit in the SM107 CuTe DSL NVFP4 MoE (#6374)

<!-- .github/pull_request_template.md -->

## 📌 Description

On Rubin (SM107), the CuTe DSL NVFP4 MoE rejected any non-default
`swiglu_alpha` / `swiglu_beta` / `swiglu_limit` with
`NotImplementedError`. As a result, clamped-SwiGLU models such as
GLM-5.3 (plain SiLU-and-mul with only `swiglu_limit` set) could not use
this backend on SM107.

This PR ports the SM107 SwiGLU clamp from TensorRT-LLM
(NVIDIA/TensorRT-LLM#19488) to FlashInfer's copy of the same Rubin
kernel
(`rubin/blockscaled_contiguous_gather_grouped_gemm_swiglu_fusion.py`):

- **Kernel:** adds a trace-time `swiglu_limit` constant. When it is
finite, the alpha-scaled gate is capped at `+limit` and the alpha-scaled
up branch is clipped to `[-limit, limit]` (`min.NaN.xorsign.abs.f32`)
before the activation, in both the vectorized and scalar epilogues. This
matches the existing Blackwell kernel. A limit of `+inf` emits no clamp
code.
- **Dispatcher
(`blockscaled_contiguous_gather_grouped_gemm_act_fusion.py`):**
- Only custom `swiglu_alpha` / `swiglu_beta` are still rejected on
SM107.
- `DEFAULT_SWIGLU_LIMIT` (fp32 max) is mapped to `+inf`, so unclamped
kernels are unchanged.
- A finite limit is accepted for plain SwiGLU only; SiTU and Relu2 still
raise `NotImplementedError`.
- `swiglu_limit` was already part of the kernel cache key and is
threaded through the tuner and the locality-domain path, so no further
plumbing is needed.

TRT-LLM's custom-op and `fused_moe_cute_dsl.py` changes in #19488 are
op-registration plumbing that FlashInfer's API already has from the
Blackwell path, so they are not ported.

Out of scope: custom `swiglu_alpha` / `swiglu_beta` (GPT-OSS-style
SwiGLU) on SM107.

## 🔍 Related Issues

Addresses the `swiglu_limit` part of #6075 (GLM-5.3 NVFP4 on SM107).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [ ] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (ruff check + ruff format 0.12.8 on the
changed files)

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

New test: `TestCuteDslFusedMoeFunctional::test_swiglu_limit_accuracy`,
plain SwiGLU with `swiglu_limit` in {0.05, 0.1}, for both w4a4 and
w4a16. The outputs in this configuration are small enough that
`check_accuracy`'s absolute tolerance floor would also accept an
unclamped kernel. The test therefore also asserts two things: that the
limit changes the reference, and that the kernel result is much closer
to the clamped reference than to the unclamped one.

Validated on a GR100 (SM107) host, using the CI nightly image with
`nvidia-cutlass-dsl[cu13]==4.8.0.dev0`. The run used `pytest
tests/moe/test_cute_dsl_fused_moe.py -k "TestCuteDslFusedMoeFunctional
or swiglu or situ or relu2 or TestKernelInputValidation or
TestRubinMultiCtaTacticRejected"`:

- **Result:** 181 passed, 90 skipped, 0 failed.
- **Skips:** existing SM107 feature gaps (per-token scale, unfused
finalize, GeGLU-tanh, custom alpha/beta).
- **Discrimination at `swiglu_limit=0.1`, w4a4:** the kernel's relative
error is 0.27 against the clamped reference and 0.76 against the
unclamped reference. The noise floor of the unclamped kernel against its
own reference is 0.22.

Not run locally on Blackwell. The Blackwell kernel already implements
`swiglu_limit`, and the new test exercises it there unchanged.

The SM107 skip messages for the GPT-OSS-style tests now name only
`swiglu_alpha/beta`.

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
```

## Reviewer Notes

- The kernel diff mirrors TRT-LLM #19488's kernel hunks verbatim, except
the constructor signature, which keeps FlashInfer's `enable_pdl` /
`ugpu_half_gemm` aliases. #19488 was approved but not yet merged when
this was opened.
- The clamp is a compile-time constant. Clamped and unclamped kernels
are distinct compilations, already separated by `swiglu_limit` in
`_gather_kernel_cache`'s key.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
- Added support for setting a clamp limit for SwiGLU on Rubin hardware.
The limit caps the gate and up activation values; the default preserves
unclamped behavior.
- Clamp limits are supported for plain SwiGLU only. Other activation
types and custom SwiGLU alpha or beta values remain unsupported.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6e72bc3](https://github.com/flashinfer-ai/flashinfer/commit/6e72bc363435199162525de339c0ee63e9384c27)

- **作者**: Dhiraj Reddy (cuDNN/FlashInfer)
- **时间**: 2026-10-13T19:48:55Z
- **提交信息**: feat(topk_varlen): windowed (prefill) mode for gvr_2: row_starts, register-family routing (max_seq_len), absolute_indices (TRT-LLM #18702 port) (#5304)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds windowed (prefill) top-k to `top_k_varlen` for the gvr_2 backend:
the DSA prefill-indexer layout, where every request's keys are packed
along the column axis and each query row ranks a causal window into its
own request's slice. Port of NVIDIA/TensorRT-LLM#18702 plus two
FlashInfer additions (register-family routing, fused absolute-column
output); consolidates the former stacked PRs #5307 and #5310.

**New API** (keyword-only, after `top_k`; the `top_k_varlen` docstring
is the contract: modes, per-parameter rules, backend constraints under
`backend`, examples that run as doctests):

- `row_starts=` switches to windowed (prefill) mode: row `r` ranks
`logits[r, row_starts[r] : row_starts[r] + seq_lens[r]]` and returns
window positions, `-1` padded. Hint-free; `next_n`, `compress_ratio` and
`pre_idx` are refused in this mode.
- `max_window_len=` is the caller's bound on the window lengths
(defaults to the logits width); a tight bound routes short windows to
the register-resident engines. Windowed mode only; refused in decode
mode.
- `absolute_indices=True` writes logits columns (the packed-KV position)
instead of window positions, fused into the index emit.
- `flashinfer.topk_varlen.warmup_prefill` and `prefill_ready` compile
and check the windowed launchers before CUDA-graph capture.
- The streaming main kernel skips its body for rows with `n <= K`
(identity rows). This applies to decode as well: identity-only decode
slabs get 2.9-3.7x faster, full slabs are unchanged.

**Breaking since the first push of this PR** (no release carries the old
forms): `max_seq_len` is renamed `max_window_len` and refused in decode
mode; windowed mode refuses `next_n`, `compress_ratio` and `pre_idx`
when passed, including the old defaults `next_n=1` / `compress_ratio=1`
(their defaults are now `None`, meaning 1 in decode mode).

### Performance summary

Causal prefill staircases (R prompts x L tokens), fp32, CUDA-graph
replay, min of 3 interleaved repetitions, every comparison on one node
in one job. Speedup = other kernel's time / ours (> 1: we are faster).
Per-cell tables are in the collapsed sections below.

| Comparison | B200 / B300 | Rubin |
|---|---|---|
| vs FlashInfer radix `top_k_ragged_transform(row_starts=)` | 2.5-4.8x |
2.4-4.8x |
| vs SGLang `topk_transform_ragged_v2` | current main (B200): K=512
1.19-1.84x, K=2048 0.93-1.68x (below parity only on ~8K-token windows) |
1.5-3.3x (Aug-26 build) |
| vs the TRT-LLM prefill kernel this ports (bit-identical results) |
1.0-4.6x | 1.0-4.0x |
| register routing via `max_window_len` vs the streaming slab (windows
<= 4K) | up to 1.68x | up to 1.42x |
| fused `absolute_indices` vs window-local kernel + a separate
offset-add | 1.3-1.7x (K=512), 1.9-6.8x (K=2048) | 1.5-1.9x (K=512),
2.5-8.8x (K=2048) |
| fused `absolute_indices` vs the window-local kernel alone | 0.97-1.01x
| 0.98-1.02x |
| vs SGLang's fused ragged kernel (`out_offsets`) | n/a | 1.4-2.5x |

<details>
<summary>Part 1 tables: windowed slab vs radix and SGLang (B200, B300,
Rubin) and vs the upstream kernel</summary>

SGLang-shaped staircase: R requests x L prompt tokens, causal windows,
fp32, graph replay, 3 interleaved repetitions, min, every column on the
same node in the same job. `radix_win` =
`top_k_ragged_transform(row_starts=)` (FlashInfer today), `sgl_v2` =
SGLang's default `topk_transform_ragged_v2`, `proxy` = the gvr_2 decode
engine on a column-0 layout of identical per-row work (control column).

Time in us, min of 3 interleaved repetitions, graph replay. R requests x
L prompt tokens, causal windows, fp32.

**B200 (148 SMs)**

| K | R x L | rows | radix_win | gvr2_win | sgl_v2 | speedup vs
radix_win | speedup vs sgl_v2 |
|---|---|---|---|---|---|---|---|
| 512 | 1 x 8192 | 8192 | 426.1 | 93.7 | 120.6 | 4.55x | 1.28x |
| 512 | 4 x 2048 | 8192 | 221.8 | 62.8 | 71.2 | 3.57x | 1.14x |
| 512 | 4 x 2047 | 8188 | 221.8 | 62.8 | 72.8 | 3.57x | 1.16x |
| 512 | 4 x 8192 | 32768 | 1690.6 | 358.1 | 473.1 | 4.76x | 1.32x |
| 512 | 8 x 4096 | 32768 | 1289.1 | 349.5 | 379.4 | 3.70x | 1.09x |
| 512 | 16 x 2048 | 32768 | 972.3 | 251.9 | 314.7 | 3.85x | 1.25x |
| 2048 | 1 x 8192 | 8192 | 375.8 | 124.4 | 109.2 | 3.03x | 0.88x |
| 2048 | 4 x 2048 | 8192 | 49.7 | 19.4 | 19.0 | 2.56x | 0.98x |
| 2048 | 4 x 2047 | 8188 | 49.5 | 19.2 | 18.8 | 2.56x | 0.98x |
| 2048 | 4 x 8192 | 32768 | 1485.5 | 477.4 | 425.5 | 3.12x | 0.89x |
| 2048 | 8 x 4096 | 32768 | 895.5 | 333.1 | 276.7 | 2.70x | 0.83x |
| 2048 | 16 x 2048 | 32768 | 239.9 | 86.2 | 107.5 | 2.78x | 1.25x |

**B300 (148 SMs)**

| K | R x L | rows | radix_win | gvr2_win | sgl_v2 | speedup vs
radix_win | speedup vs sgl_v2 |
|---|---|---|---|---|---|---|---|
| 512 | 1 x 8192 | 8192 | 412.4 | 90.6 | 115.7 | 4.55x | 1.28x |
| 512 | 4 x 2048 | 8192 | 212.2 | 60.2 | 68.1 | 3.57x | 1.14x |
| 512 | 4 x 2047 | 8188 | 212.2 | 60.3 | 69.8 | 3.57x | 1.15x |
| 512 | 4 x 8192 | 32768 | 1636.8 | 346.7 | 454.2 | 4.76x | 1.32x |
| 512 | 8 x 4096 | 32768 | 1243.3 | 337.1 | 364.3 | 3.70x | 1.08x |
| 512 | 16 x 2048 | 32768 | 934.6 | 242.5 | 301.5 | 3.85x | 1.25x |
| 2048 | 1 x 8192 | 8192 | 363.8 | 120.4 | 104.9 | 3.03x | 0.87x |
| 2048 | 4 x 2048 | 8192 | 46.0 | 18.6 | 18.5 | 2.50x | 0.99x |
| 2048 | 4 x 2047 | 8188 | 45.8 | 18.4 | 18.4 | 2.50x | 1.00x |
| 2048 | 4 x 8192 | 32768 | 1437.9 | 462.4 | 408.5 | 3.12x | 0.88x |
| 2048 | 8 x 4096 | 32768 | 861.9 | 320.7 | 264.3 | 2.70x | 0.83x |
| 2048 | 16 x 2048 | 32768 | 225.1 | 81.7 | 101.3 | 2.78x | 1.23x |

**Rubin (208 SMs)**

| K | R x L | rows | radix_win | gvr2_win | sgl_v2 | speedup vs
radix_win | speedup vs sgl_v2 |
|---|---|---|---|---|---|---|---|
| 512 | 1 x 8192 | 8192 | 254.6 | 57.4 | 128.5 | 4.35x | 2.22x |
| 512 | 4 x 2048 | 8192 | 130.6 | 38.4 | 72.1 | 3.45x | 1.89x |
| 512 | 4 x 2047 | 8188 | 129.6 | 38.4 | 72.9 | 3.33x | 1.89x |
| 512 | 4 x 8192 | 32768 | 1001.3 | 215.2 | 503.8 | 4.76x | 2.33x |
| 512 | 8 x 4096 | 32768 | 775.4 | 211.2 | 437.3 | 3.70x | 2.08x |
| 512 | 16 x 2048 | 32768 | 590.3 | 153.8 | 387.6 | 3.85x | 2.50x |
| 2048 | 1 x 8192 | 8192 | 226.2 | 77.8 | 119.0 | 2.94x | 1.54x |
| 2048 | 4 x 2048 | 8192 | 32.7 | 13.5 | 28.2 | 2.44x | 2.08x |
| 2048 | 4 x 2047 | 8188 | 32.3 | 13.1 | 28.1 | 2.44x | 2.13x |
| 2048 | 4 x 8192 | 32768 | 884.0 | 287.8 | 462.3 | 3.03x | 1.61x |
| 2048 | 8 x 4096 | 32768 | 547.7 | 202.2 | 339.0 | 2.70x | 1.67x |
| 2048 | 16 x 2048 | 32768 | 156.9 | 53.5 | 176.2 | 2.94x | 3.33x |

Speedups are the other kernel's time over ours (>1 = we are faster). The
remaining K = 2048 long-row cells where SGLang's kernel is 12-21% faster
on B200 / B300 are the streaming main kernel's per-row cost on
non-trivial rows (shared with upstream); Rubin has no losing cell.

Same-node A/B against the TRT-LLM gvr_v2 prefill kernel this was ported
from (`run_prefill` of the upstream standalone pair, identical plans,
bit-identical results on every cell; speedup = upstream time / ours, min
of 3 interleaved):

| K | R x L | B200 | B300 | Rubin |
|---|---|---|---|---|
| 512 | 1 x 8192 | 1.37x | 1.37x | 1.35x |
| 512 | 4 x 2048 | 1.79x | 1.79x | 1.72x |
| 512 | 4 x 2047 (misaligned) | 1.75x | 1.79x | 1.72x |
| 512 | 4 x 8192 | 1.39x | 1.39x | 1.39x |
| 512 | 8 x 4096 | 1.82x | 1.85x | 1.79x |
| 512 | 16 x 2048 | 1.72x | 1.72x | 1.69x |
| 512 | 1 x 32768 | 1.05x | 1.05x | 1.06x |
| 512 | 64 x 512 (all rows <= K) | 4.35x | 4.55x | 4.00x |
| 512 | 128 x 64 (all rows <= K) | 4.35x | 4.35x | 4.00x |
| 2048 | 1 x 8192 | 1.23x | 1.23x | 1.20x |
| 2048 | 4 x 2048 (all rows <= K) | 3.23x | 3.12x | 2.86x |
| 2048 | 4 x 2047 (all rows <= K) | 3.23x | 3.12x | 2.86x |
| 2048 | 4 x 8192 | 1.25x | 1.25x | 1.23x |
| 2048 | 8 x 4096 | 1.79x | 1.79x | 1.75x |
| 2048 | 16 x 2048 (all rows <= K) | 2.86x | 2.86x | 2.78x |
| 2048 | 1 x 32768 | 1.00x | 1.00x | 1.01x |
| 2048 | 64 x 512 (all rows <= K) | 2.86x | 2.94x | 2.78x |
| 2048 | 128 x 64 (all rows <= K) | 3.12x | 3.12x | 2.78x |

</details>

<details>
<summary>Decode effect of the short-row body skip (B200 A/B)</summary>

- **Decode is affected too, on purpose.** The short-row body skip is not
window-specific: it applies to every varlen compile of the streaming
kernel, decode included (output unchanged; the skipped pass wrote
nothing). Decode-mode A/B on the cells the router sends to the streaming
slab (hint-free gvr_2, fp32, graph replay, min of 3 interleaved reps,
B200, same job; `before` = the #5288 tree, `after` = this PR; µs):

  | scenario | K | rows | width | before | after | before/after |
  |---|---|---|---|---|---|---|
| all rows identity (len = K/2) | 512 | 256 | 32768 / 65536 | 6.43 /
6.45 | 2.16 / 2.23 | 2.98x / 2.90x |
| all rows identity | 2048 | 16 | 32768 / 65536 | 8.06 / 8.10 | 2.15 /
2.16 | 3.74x / 3.74x |
| all rows identity | 2048 | 64 | 32768 / 65536 | 6.77 / 6.75 | 2.16 /
2.15 | 3.13x / 3.13x |
| all rows identity | 2048 | 256 | 32768 / 65536 | 7.07 / 7.08 | 2.26 /
2.27 | 3.13x / 3.11x |
| 75% identity + 25% full | 512 | 256 | 32768 / 65536 | 9.75 / 14.37 |
9.12 / 13.83 | 1.07x / 1.04x |
| 75% identity + 25% full | 2048 | 16 / 64 / 256 | 32768 | 9.22 / 11.34
/ 15.13 | 9.21 / 11.29 / 14.62 | 1.00x / 1.00x / 1.03x |
| 75% identity + 25% full | 2048 | 16 / 64 / 256 | 65536 | 10.31 / 13.31
/ 13.45 | 10.28 / 13.23 / 12.96 | 1.00x / 1.01x / 1.04x |
| all rows full (control) | 512 | 256 | 32768 / 65536 | 12.38 / 17.11 |
12.20 / 17.10 | 1.02x / 1.00x |
| all rows full (control) | 2048 | 16 / 64 / 256 | 32768 | 9.73 / 11.78
/ 16.18 | 9.70 / 11.69 / 16.11 | 1.00x / 1.01x / 1.00x |
| all rows full (control) | 2048 | 16 / 64 / 256 | 65536 | 10.38 / 13.45
/ 21.84 | 10.35 / 13.43 / 21.67 | 1.00x / 1.00x / 1.01x |

Identity-only slabs lose the zero-work body pass (3-3.7x); full slabs
are unchanged (within 1.5%); mixed slabs gain by their identity share.

</details>

<details>
<summary>Part 2 tables: register-family routing (B200, B300,
Rubin)</summary>

#### Perf

Causal staircase (R prompts x L tokens), fp32, graph replay, min of 3
interleaved repetitions, every column on the same node in the same job.
`slab` = unhinted call (streaming engine, the Part 1 behaviour);
`hinted` = `max_seq_len=L`; `sgl_v2` = SGLang's default
`topk_transform_ragged_v2`; `upstream` = TRT-LLM #18702 `run_prefill`.
Speedups are the other kernel's time over `hinted` (> 1 = we are
faster). `fam` = engine the table picked. Rows with `L <= K` are
identity rows and stay on the slab.

**B200 (148 SMs)**

| K | R x L | rows | slab | hinted | fam | sgl_v2 | upstream | vs slab |
vs sgl_v2 | vs upstream |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | 63.2 | 38.8 | reg VPT1 | 73.5 | 112.9 | 1.63x
| 1.90x | 2.91x |
| 512 | 3 x 2048 | 6144 | 48.5 | 29.9 | reg VPT1 | 54.6 | 86.3 | 1.62x |
1.83x | 2.89x |
| 512 | 1 x 4096 | 4096 | 47.4 | 28.6 | reg VPT2 | 46.1 | 88.6 | 1.66x |
1.61x | 3.09x |
| 512 | 16 x 2047 | 32752 | 255.6 | 165.0 | reg VPT1 | 326.2 | 443.8 |
1.55x | 1.98x | 2.69x |
| 512 | 15 x 2048 | 30720 | 239.1 | 154.1 | reg VPT1 | 300.1 | 416.3 |
1.55x | 1.95x | 2.70x |
| 512 | 7 x 4096 | 28672 | 309.1 | 190.7 | reg VPT2 | 335.6 | 572.1 |
1.62x | 1.76x | 3.00x |
| 512 | 3 x 8192 | 24576 | 271.7 | 271.6 | slab | 360.6 | 380.3 | 1.00x
| 1.33x | 1.40x |
| 512 | 1 x 16384 | 16384 | 210.4 | 210.4 | slab | 324.6 | 243.8 | 1.00x
| 1.54x | 1.16x |
| 2048 | 4 x 2047 (all rows <= K) | 8188 | 19.2 | 19.2 | slab | 18.7 |
62.2 | 1.00x | 0.97x | 3.24x |
| 2048 | 3 x 2048 (all rows <= K) | 6144 | 14.9 | 14.9 | slab | 14.3 |
47.3 | 1.00x | 0.96x | 3.17x |
| 2048 | 1 x 4096 | 4096 | 46.0 | 27.8 | reg VPT2 | 33.1 | 84.0 | 1.65x
| 1.19x | 3.02x |
| 2048 | 16 x 2047 (all rows <= K) | 32752 | 86.1 | 86.2 | slab | 111.9
| 248.3 | 1.00x | 1.30x | 2.88x |
| 2048 | 15 x 2048 (all rows <= K) | 30720 | 81.4 | 81.3 | slab | 103.4
| 233.5 | 1.00x | 1.27x | 2.87x |
| 2048 | 7 x 4096 | 28672 | 293.1 | 192.4 | reg VPT2 | 244.8 | 528.7 |
1.52x | 1.27x | 2.75x |
| 2048 | 3 x 8192 | 24576 | 358.6 | 341.3 | reg VPT4 | 324.0 | 449.1 |
1.05x | 0.95x | 1.32x |
| 2048 | 1 x 16384 | 16384 | 313.0 | 312.9 | slab | 338.9 | 336.3 |
1.00x | 1.08x | 1.07x |

**B300 (148 SMs)**

| K | R x L | rows | slab | hinted | fam | sgl_v2 | upstream | vs slab |
vs sgl_v2 | vs upstream |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | 60.1 | 36.4 | reg VPT1 | 69.5 | 107.2 | 1.65x
| 1.91x | 2.95x |
| 512 | 3 x 2048 | 6144 | 46.2 | 28.0 | reg VPT1 | 51.7 | 81.9 | 1.65x |
1.85x | 2.93x |
| 512 | 1 x 4096 | 4096 | 45.2 | 26.9 | reg VPT2 | 43.9 | 84.1 | 1.68x |
1.63x | 3.12x |
| 512 | 16 x 2047 | 32752 | 243.9 | 156.5 | reg VPT1 | 309.2 | 421.8 |
1.56x | 1.98x | 2.70x |
| 512 | 15 x 2048 | 30720 | 228.2 | 146.1 | reg VPT1 | 284.3 | 395.8 |
1.56x | 1.95x | 2.71x |
| 512 | 7 x 4096 | 28672 | 295.8 | 178.8 | reg VPT2 | 318.0 | 543.2 |
1.65x | 1.78x | 3.04x |
| 512 | 3 x 8192 | 24576 | 260.9 | 260.9 | slab | 340.6 | 363.2 | 1.00x
| 1.31x | 1.39x |
| 512 | 1 x 16384 | 16384 | 203.8 | 203.8 | slab | 306.5 | 235.1 | 1.00x
| 1.50x | 1.15x |
| 2048 | 4 x 2047 (all rows <= K) | 8188 | 18.6 | 18.5 | slab | 18.1 |
59.0 | 1.01x | 0.98x | 3.18x |
| 2048 | 3 x 2048 (all rows <= K) | 6144 | 14.3 | 14.3 | slab | 13.8 |
45.0 | 1.00x | 0.97x | 3.15x |
| 2048 | 1 x 4096 | 4096 | 44.6 | 26.7 | reg VPT2 | 30.9 | 80.4 | 1.67x
| 1.16x | 3.01x |
| 2048 | 16 x 2047 (all rows <= K) | 32752 | 81.6 | 81.7 | slab | 105.6
| 236.8 | 1.00x | 1.29x | 2.90x |
| 2048 | 15 x 2048 (all rows <= K) | 30720 | 77.3 | 77.2 | slab | 96.8 |
222.6 | 1.00x | 1.25x | 2.88x |
| 2048 | 7 x 4096 | 28672 | 282.1 | 185.7 | reg VPT2 | 230.8 | 505.9 |
1.52x | 1.24x | 2.72x |
| 2048 | 3 x 8192 | 24576 | 346.8 | 327.1 | reg VPT4 | 305.9 | 432.0 |
1.06x | 0.94x | 1.32x |
| 2048 | 1 x 16384 | 16384 | 303.8 | 303.9 | slab | 319.9 | 325.8 |
1.00x | 1.05x | 1.07x |

**Rubin (208 SMs)** — final-tree A/B on an idle box (same columns as
above; the earlier Rubin run was co-tenanted and discarded).

| K | R x L | rows | slab | hinted | fam | sgl_v2 | upstream | vs slab |
vs sgl_v2 | vs upstream |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | 38.4 | 32.8 | reg VPT1 | 72.8 | 66.8 | 1.17x |
2.22x | 2.04x |
| 512 | 3 x 2048 | 6144 | 29.6 | 25.0 | reg VPT1 | 54.0 | 51.2 | 1.18x |
2.16x | 2.05x |
| 512 | 1 x 4096 | 4096 | 29.6 | 21.2 | reg VPT2 (MINB 2) | 42.9 | 52.9
| 1.40x | 2.02x | 2.49x |
| 512 | 16 x 2047 | 32752 | 155.0 | 155.0 | slab | 394.7 | 262.0 | 1.00x
| 2.55x | 1.69x |
| 512 | 15 x 2048 | 30720 | 144.2 | 144.2 | slab | 362.6 | 245.4 | 1.00x
| 2.51x | 1.70x |
| 512 | 7 x 4096 | 28672 | 184.7 | 187.7 | reg VPT2 (MINB 2) | 380.0 |
332.4 | 0.98x | 2.02x | 1.77x |
| 512 | 3 x 8192 | 24576 | 163.3 | 163.3 | slab | 378.1 | 224.9 | 1.00x
| 2.32x | 1.38x |
| 512 | 1 x 16384 | 16384 | 128.0 | 127.9 | slab | 311.5 | 147.7 | 1.00x
| 2.43x | 1.15x |
| 2048 | 4 x 2047 (all rows <= K) | 8188 | 13.1 | 13.0 | slab | 26.9 |
37.6 | 1.01x | 2.07x | 2.89x |
| 2048 | 3 x 2048 (all rows <= K) | 6144 | 10.0 | 10.1 | slab | 20.0 |
29.0 | 0.99x | 1.99x | 2.88x |
| 2048 | 1 x 4096 | 4096 | 31.2 | 21.9 | reg VPT2 (MINB 2) | 33.0 | 53.0
| 1.42x | 1.50x | 2.42x |
| 2048 | 16 x 2047 (all rows <= K) | 32752 | 53.3 | 53.5 | slab | 177.2
| 151.8 | 1.00x | 3.31x | 2.84x |
| 2048 | 15 x 2048 (all rows <= K) | 30720 | 50.3 | 50.2 | slab | 162.8
| 142.4 | 1.00x | 3.24x | 2.84x |
| 2048 | 7 x 4096 | 28672 | 177.6 | 172.6 | reg VPT2 (MINB 2) | 293.3 |
313.4 | 1.03x | 1.70x | 1.82x |
| 2048 | 3 x 8192 | 24576 | 218.0 | 214.9 | reg VPT4 | 347.8 | 267.9 |
1.01x | 1.62x | 1.25x |
| 2048 | 1 x 16384 | 16384 | 191.9 | 191.9 | slab | 321.5 | 204.7 |
1.00x | 1.68x | 1.07x |

Remaining cells behind SGLang's kernel: K = 2048 with 8K-token windows
on B200/B300 (0.94-0.95x; the VPT=4 register rung is the best of the
menu there), and the all-identity slabs at K = 2048 with L <= K
(0.96-0.98x, launch-floor territory: 14-19 us). Rubin is ahead of SGLang
on every cell (1.5-3.3x) and of upstream on every cell (1.07-2.9x); its
slab was already strong, so the register rungs add 17-42% at a few
thousand rows and are gated off where the slab wins.

</details>

<details>
<summary>Part 3 tables: fused absolute output (B200, B300, Rubin) and
register footprint</summary>

- compile-time variant (`prefill_abs` in the compile keys, persist names
`..._pf_abs`): the register footprint is unchanged across the decode,
window-local and absolute compiles (`cuobjdump --dump-resource-usage` on
the DSL dump_dir cubins, B200, 2026-10-02):

  | rung | compile | REG | STACK | SHARED |
  |---|---|---|---|---|
  | (512, 1, 4) K=512 | decode `_hf` | 32 | 24 | 1024 |
  | (512, 1, 4) K=512 | windowed `_hf_pf` | 32 | 16 | 1024 |
  | (512, 1, 4) K=512 | absolute `_hf_pf_abs` | 32 | 16 | 1024 |
  | (512, 2, 4) K=512 | decode `_hf` | 32 | 24 | 1024 |
  | (512, 2, 4) K=512 | windowed `_hf_pf` | 32 | 16 | 1024 |
  | (512, 2, 4) K=512 | absolute `_hf_pf_abs` | 32 | 16 | 1024 |

(so `lmask` and `ks` do not cost a register at the 32-register wall; the
windowed compiles even carry 8 bytes less stack than decode). The
prefill launcher cache, `warmup_prefill(..., absolute_indices=)` and
`prefill_ready(..., absolute_indices=)` key on it.

#### Perf

Fused absolute output vs the window-local kernel, and vs the un-fused
alternative a framework must run today (window-local kernel + a torch
offset-add finish). SGLang-shaped staircase (R prompts x L tokens),
fp32, CUDA graph, 3 interleaved reps, min; same node, one job. Speedups
> 1 favour the fused variant.

**B200 (computelab, 148 SMs)** (us, min of 3 interleaved reps; `local` =
window-local indices, `fused` = `absolute_indices=True`, `local+add` =
window-local kernel followed by the torch offset-add a framework runs
today)

| K | prompts x L | rows | engine | local | fused | local+add |
local/fused | (local+add)/fused |
|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | reg VPT1 | 37.8 | 38.5 | 63.2 | 0.982x | 1.64x
|
| 512 | 3 x 2048 | 6144 | reg VPT1 | 29.2 | 29.6 | 49.5 | 0.986x | 1.67x
|
| 512 | 1 x 4096 | 4096 | reg VPT2 | 27.7 | 27.8 | 41.8 | 0.996x | 1.50x
|
| 512 | 16 x 2047 | 32752 | reg VPT1 | 163.2 | 164.2 | 274.4 | 0.994x |
1.67x |
| 512 | 15 x 2048 | 30720 | reg VPT1 | 151.7 | 152.8 | 252.4 | 0.993x |
1.65x |
| 512 | 7 x 4096 | 28672 | reg VPT2 | 185.6 | 191.5 | 277.9 | 0.969x |
1.45x |
| 512 | 3 x 8192 | 24576 | slab | 271.1 | 271.0 | 344.7 | 1.000x | 1.27x
|
| 2048 | 4 x 2047 | 8188 | slab | 19.4 | 19.4 | 131.1 | 1.000x | 6.76x |
| 2048 | 3 x 2048 | 6144 | slab | 15.1 | 15.1 | 89.8 | 1.000x | 5.95x |
| 2048 | 1 x 4096 | 4096 | reg VPT2 | 27.8 | 27.8 | 71.7 | 1.000x |
2.58x |
| 2048 | 16 x 2047 | 32752 | slab | 87.7 | 87.6 | 528.8 | 1.001x | 6.04x
|
| 2048 | 15 x 2048 | 30720 | slab | 82.4 | 82.4 | 496.4 | 1.000x | 6.02x
|
| 2048 | 7 x 4096 | 28672 | reg VPT2 | 192.8 | 191.5 | 579.0 | 1.007x |
3.02x |
| 2048 | 3 x 8192 | 24576 | reg VPT4 | 340.9 | 346.6 | 672.4 | 0.984x |
1.94x |

**B300 (computelab, 148 SMs)** (us, min of 3 interleaved reps; `local` =
window-local indices, `fused` = `absolute_indices=True`, `local+add` =
window-local kernel followed by the torch offset-add a framework runs
today)

| K | prompts x L | rows | engine | local | fused | local+add |
local/fused | (local+add)/fused |
|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | reg VPT1 | 36.4 | 37.0 | 61.1 | 0.984x | 1.65x
|
| 512 | 3 x 2048 | 6144 | reg VPT1 | 28.2 | 28.4 | 47.7 | 0.993x | 1.68x
|
| 512 | 1 x 4096 | 4096 | reg VPT2 | 27.0 | 27.0 | 41.7 | 1.000x | 1.54x
|
| 512 | 16 x 2047 | 32752 | reg VPT1 | 157.1 | 158.1 | 266.3 | 0.994x |
1.68x |
| 512 | 15 x 2048 | 30720 | reg VPT1 | 145.9 | 147.1 | 245.0 | 0.992x |
1.67x |
| 512 | 7 x 4096 | 28672 | reg VPT2 | 179.2 | 185.4 | 271.7 | 0.967x |
1.47x |
| 512 | 3 x 8192 | 24576 | slab | 262.4 | 262.3 | 334.7 | 1.000x | 1.28x
|
| 2048 | 4 x 2047 | 8188 | slab | 18.6 | 18.6 | 127.2 | 1.000x | 6.84x |
| 2048 | 3 x 2048 | 6144 | slab | 14.5 | 14.5 | 87.2 | 1.000x | 6.01x |
| 2048 | 1 x 4096 | 4096 | reg VPT2 | 26.8 | 26.8 | 69.7 | 1.000x |
2.60x |
| 2048 | 16 x 2047 | 32752 | slab | 83.1 | 82.7 | 516.4 | 1.005x | 6.24x
|
| 2048 | 15 x 2048 | 30720 | slab | 78.0 | 77.8 | 484.8 | 1.003x | 6.23x
|
| 2048 | 7 x 4096 | 28672 | reg VPT2 | 185.6 | 184.6 | 566.0 | 1.005x |
3.07x |
| 2048 | 3 x 8192 | 24576 | reg VPT4 | 328.4 | 333.8 | 653.9 | 0.984x |
1.96x |

**Rubin GR100 (208 SMs; SGLang's kernel available there)** (us, min of 3
interleaved reps; `local` = window-local indices, `fused` =
`absolute_indices=True`, `local+add` = window-local kernel followed by
the torch offset-add a framework runs today)

| K | prompts x L | rows | engine | local | fused | local+add |
local/fused | (local+add)/fused | SGLang topk_v2 (out_offsets) |
SGLang/fused |
|---|---|---|---|---|---|---|---|---|---|---|
| 512 | 4 x 2047 | 8188 | reg VPT1 | 33.3 | 33.5 | 63.0 | 0.994x | 1.88x
| 70.7 | 2.11x |
| 512 | 3 x 2048 | 6144 | reg VPT1 | 25.5 | 25.5 | 45.5 | 1.000x | 1.78x
| 52.5 | 2.06x |
| 512 | 1 x 4096 | 4096 | reg VPT2 | 21.6 | 21.5 | 37.2 | 1.005x | 1.73x
| 42.0 | 1.95x |
| 512 | 16 x 2047 | 32752 | slab | 158.4 | 157.5 | 264.8 | 1.006x |
1.68x | 358.1 | 2.27x |
| 512 | 15 x 2048 | 30720 | slab | 147.5 | 146.5 | 246.5 | 1.007x |
1.68x | 329.5 | 2.25x |
| 512 | 7 x 4096 | 28672 | reg VPT2 | 190.7 | 189.7 | 283.4 | 1.005x |
1.49x | 350.9 | 1.85x |
| 512 | 3 x 8192 | 24576 | slab | 166.7 | 165.9 | 241.1 | 1.005x | 1.45x
| 352.2 | 2.12x |
| 2048 | 4 x 2047 | 8188 | slab | 13.4 | 13.4 | 118.0 | 1.000x | 8.81x |
26.7 | 1.99x |
| 2048 | 3 x 2048 | 6144 | slab | 10.3 | 10.4 | 82.1 | 0.990x | 7.89x |
18.5 | 1.78x |
| 2048 | 1 x 4096 | 4096 | reg VPT2 | 22.7 | 22.2 | 66.5 | 1.023x |
3.00x | 31.7 | 1.43x |
| 2048 | 16 x 2047 | 32752 | slab | 53.6 | 54.6 | 472.8 | 0.982x | 8.66x
| 137.0 | 2.51x |
| 2048 | 15 x 2048 | 30720 | slab | 50.5 | 51.3 | 445.3 | 0.984x | 8.68x
| 127.1 | 2.48x |
| 2048 | 7 x 4096 | 28672 | reg VPT2 | 175.7 | 175.9 | 542.8 | 0.999x |
3.09x | 262.5 | 1.49x |
| 2048 | 3 x 8192 | 24576 | reg VPT4 | 217.8 | 212.7 | 531.0 | 1.024x |
2.50x | 319.9 | 1.50x |

The fused variant is within 1% of the window-local kernel on every slab
cell and on the register rungs except two: K=512 windows of 4096 on 28K
rows (VPT=2 rung, 0.97x on B200/B300) and K=2048 windows of 8192 (VPT=4
rung, 0.98x). Against what a framework must run today (window-local
kernel + an offset-add pass) it is 1.3-1.9x faster at K=512 and 1.9-8.8x
at K=2048, where the add pass is comparable to the top-k itself.
SGLang's fused ragged kernel was importable on the Rubin box only:
1.4-2.5x slower than ours there.

</details>

<details>
<summary>SGLang baseline re-measured against upstream main
(2026-10-02)</summary>

The `sgl_v2` columns above were measured against SGLang's
`topk_transform_ragged_v2` at commit 7f27bf4708 (2026-08-26). Upstream
has since reworked `topk_v2.cuh` (dsv4.1 top-k, dual output,
cluster-fallback fix); same entry point and routing (`dsa_topk_backend`
RAGGED extend), but the current build (58f0d250ec, 2026-10-01) is 7-10%
faster on selection-heavy rows and slower on identity rows. Both builds
re-measured on one B200 in one job, both kernels called raw with
preallocated outputs (one kernel launch per call for every column,
profiler-verified), both emitting absolute packed columns (`out_offsets
== row_starts` / `absolute_indices=True`), every output validated before
timing, identical-kernel control within 0.6%. `ours` = hinted
(`max_seq_len` = the batch's longest window), the production call. µs;
speedup = SGLang / ours.

| K | prompts x L (prefix) | rows | max win | ours | SGLang v2 main |
SGLang v2 Aug-26 | main/ours | Aug-26/ours |
|---|---|---|---|---|---|---|---|---|
| 512 | 1 x 8192 | 8192 | 8192 | 100.2 | 119.0 | 129.6 | 1.19x | 1.29x |
| 512 | 4 x 2047 | 8188 | 2047 | 42.0 | 71.9 | 77.8 | 1.71x | 1.85x |
| 512 | 8 x 4096 | 32768 | 4096 | 240.2 | 368.9 | 400.8 | 1.54x | 1.67x
|
| 512 | 16 x 2048 | 32768 | 2048 | 172.2 | 308.3 | 329.8 | 1.79x | 1.92x
|
| 512 | 4 x 8192 | 32768 | 8192 | 381.8 | 465.2 | 506.8 | 1.22x | 1.33x
|
| 512 | 1 x 4096 chunk, prefix 12288 | 4096 | 16384 | 73.1 | 109.4 |
121.1 | 1.50x | 1.66x |
| 512 | 1 x 4096 chunk, prefix 28672 | 4096 | 32768 | 105.7 | 194.0 |
212.4 | 1.84x | 2.01x |
| 512 | 1 x 4096 chunk, prefix 61440 | 4096 | 65536 | 194.8 | 320.0 |
341.5 | 1.64x | 1.75x |
| 512 | 4 x 1024 chunk, prefix 0/8K/16K/32K | 4096 | 33792 | 70.6 |
116.4 | 124.6 | 1.65x | 1.76x |
| 2048 | 1 x 8192 | 8192 | 8192 | 116.6 | 108.8 | 116.9 | 0.93x | 1.00x
|
| 2048 | 4 x 2047 (all rows <= K) | 8188 | 2047 | 20.0 | 23.8 | 20.0 |
1.19x | 1.00x |
| 2048 | 8 x 4096 | 32768 | 4096 | 222.1 | 274.8 | 288.3 | 1.24x | 1.30x
|
| 2048 | 16 x 2048 (all rows <= K) | 32768 | 2048 | 86.9 | 115.3 | 104.9
| 1.33x | 1.21x |
| 2048 | 4 x 8192 | 32768 | 8192 | 454.5 | 424.1 | 455.3 | 0.93x | 1.00x
|
| 2048 | 1 x 4096 chunk, prefix 4096 | 4096 | 8192 | 76.1 | 74.9 | 81.1
| 0.98x | 1.07x |
| 2048 | 1 x 4096 chunk, prefix 12288 | 4096 | 16384 | 115.5 | 130.8 |
143.2 | 1.13x | 1.24x |
| 2048 | 1 x 4096 chunk, prefix 28672 | 4096 | 32768 | 157.4 | 246.0 |
268.4 | 1.56x | 1.70x |
| 2048 | 1 x 4096 chunk, prefix 61440 | 4096 | 65536 | 238.2 | 400.4 |
424.7 | 1.68x | 1.78x |
| 2048 | 4 x 1024 chunk, prefix 0/8K/16K/32K | 4096 | 33792 | 109.4 |
136.0 | 144.4 | 1.24x | 1.32x |
| 2048 | 8 x 512 chunk, prefix 4K..32K | 4096 | 33280 | 123.3 | 169.7 |
183.8 | 1.38x | 1.49x |

Against the current build: K = 512 ahead on every cell (1.19-1.84x); K =
2048 at or just below parity only on ~8K-token windows (0.93-0.98x,
SGLang's register<2> path), 1.13x at 16K windows, 1.56-1.68x at 32K-64K
windows, 1.24-1.38x on mixed batches. sgl-kernel's AOT
`fast_topk_transform_ragged_fused` (k = 2048 only) is 1.9-2.9x slower
than ours on every non-identity cell.

</details>

### Design notes

- Device: `prefill=True` variants of the streaming main kernel and the
register-resident kernel read the window from its float4-aligned base
and mask the up to three lead lanes in sampling, histogram, tail and
emit; indices are shifted back to the window frame (or to columns with
`absolute_indices`). The register variants keep one per-row value live
at their 32-register cap.
- Host: one launcher per (row-count tier, K, bound bucket), rows slabbed
at 32768; a per-part rung table (B200/B300 and Rubin differ) picks the
register engine from `max_window_len`; `warmup_prefill` compiles the
exact launcher keys a serving call looks up.
- API: `row_starts` validated (contiguous 1-D int32, one entry per row);
only gvr_2's checker admits windowed calls, so `auto` resolves to it;
mode-conflicting arguments raise `ValueError` before any launch, under
`auto`, explicit `gvr_2` and `skip_check=True` alike.

<details>
<summary>Full design notes per part (device, host, API)</summary>

_Written before the rename: `max_seq_len` below is today's
`max_window_len`._

### Part 1: windowed mode via `row_starts` (commit `feat(topk_varlen):
windowed (prefill) mode via row_starts`)

Row `r` ranks `logits[r, row_starts[r] : row_starts[r] + seq_lens[r]]`
and returns window-local indices (`-1` padded, identity for windows
shorter than K). This is the DSA prefill-indexer layout: every request's
keys packed along the column axis, one query row per prompt token with a
causal window into its own request's slice. No column before
`row_starts[r] & ~3` or at or after the window end is read; the up to
three columns between `row_starts[r] & ~3` and `row_starts[r]` are
loaded for 16-byte alignment and masked at every consumer, so cells
outside the window may be unwritten. Until now the only FlashInfer path
for that layout was the radix `top_k_ragged_transform(row_starts=)`.

#### What changed

- **Device**: `GvrMainKernel(prefill=True)` variant of the streaming
`main` family. The window is read from a float4-aligned base (`ks & ~3`)
with the `ks & 3` lead lanes masked in sampling, histogram, tail and
emit, and indices shifted back by the lead, so the row base stays
16-byte aligned for any `ks`. ABI: the `pre_idx` slot carries
`row_starts`, `seq_lens` keeps its per-row *length* meaning (upstream
passes ks/ke), so callers never materialize row ends. Hint-free only;
`next_n == 1`, `compress_ratio == 1`.
- **Host**: `run_varlen(..., row_starts=)` → `_launch_prefill`, one
engine per (row-count tier, K, pow2 envelope bucket), rows slabbed at
32768. `warmup_prefill(top_k, max_cols)` compiles the set (about six
slab engines plus the register rungs the per-arch table admits, per K)
for CUDA-graph capture; the reference engine copies each window into an
aligned `-inf`-padded row.
- **Main kernel, all varlen modes**: rows with `n <= K` now skip the
body outright and go straight to the identity epilogue (block-uniform
`short`). Upstream runs the body as a zero-work pass (every barrier and
the sample scan still execute, ~1 µs per CTA on B200). In a causal
prefill staircase the first K rows of every request are short, so this
matters (25% of rows at L = 8192, K = 2048; all rows at L ≤ K). The diff
of `gvr2_topk_decode.py` is large only because the body is re-indented
one level; `git diff -w` shows the real change. Also, the hint-free
identity bracket now samples from the first in-window lane (`base =
lead`) instead of the float4-rounded row base, whose ≤ 3 lead lanes
belong to the previous request; sampling them cost 50% on misaligned
windows at K = 512.

- **API**: `row_starts` validated (contiguous 1-D int32 CUDA, one entry
per row, no `pre_idx`, `next_n == 1`, `compress_ratio == 1`). Only
gvr_2's checker admits it, so `auto` picks gvr_2 and an explicit other
backend is refused at validation. The trace template gains the optional
input with a window-aware reference/check.

### Part 2: register-family routing via `max_seq_len` (commit
`perf(topk_varlen): route windowed (prefill) rows to the
register-resident gvr_2 family`)

Part 1's window engines existed only for the streaming `main` slab, so
every prefill row ran the slab, while the decode router sends rows of
the same length to the register-resident `reg` kernels, which are 1.6-2x
faster on windows up to 4K tokens. SGLang's prefill top-k kernel picks
its path per row by window length, which is exactly where it was still
ahead of us.

#### What changed

- **Device**: `GvrTopkRegKernel(prefill=True)`. The row is read from the
float4-rounded window base; the `ks & 3` lead lanes (thread 0's first
float4) are excluded from the bracket fold, the identity hint positions,
the histogram classify, the key-space escape and every emit by a 4-bit
lane mask; indices are shifted to the window frame. A row whose scan
extent exceeds the rung's register capacity (the caller's bound was
violated) is reported as all `-1`, never as a truncated ranking. The
slab engine is unchanged.
- **Host**: `_prefill_reg_route(rows, k, max_window)` — a per-part rung
table measured on the causal staircase (rows 2K-32K, K ∈ {512, 2048},
bounds 2045/4093/8189, BLK/VPT/MINB menu, same node vs sglang topk_v2).
B200 and B300 agree; Rubin differs: its slab is stronger at high row
counts and the decode router's VPT=2/MINB=4 rung is register-starved
there (the MINB=2 variant wins instead). `_reg_plan` mirrors `route()`'s
register-band constants for an explicit rung.
- **API**: `top_k_varlen(..., row_starts=, max_seq_len=)` — the caller's
bound on the window lengths (the longest prompt of the batch, host
knowledge in every serving framework) selects the engine. Without it the
logits width is the bound (always valid, since no window is wider than
its row, but loose for a packed multi-request batch, whose width sums
every request's keys), so a single-request chunk that fits a register
rung takes it with no hint; the review pass made this the default (the
first version ran the slab for every unhinted call, which is what the
`slab` columns below measure). A per-row split across two launches was
built, measured and dropped: the slab launch that only skips rows still
costs ~35 µs per 32K rows (one CTA per row at its smem occupancy), and
without the bound the register launch must take the largest capacity
class, the wrong kernel for short windows.

### Part 3: absolute-column output via `absolute_indices` (commit
`feat(topk_varlen): absolute-column output for windowed top-k`)

Windowed (prefill) `top_k_varlen` returns **window-local** indices
(`column - row_starts[r]`). The DSA prefill indexer's consumer wants the
**absolute column** of the packed key axis, i.e. the flattened-KV slot:
SGLang's `topk_transform_ragged_v2` produces exactly that by adding
`out_offsets` inside its kernel, so a FlashInfer caller today has to run
a separate offset-add over `num_rows x top_k` indices after every call
(an extra launch on the critical path of every prefill layer; ~256 MB
read-modify-write at 32K rows x K=2048).

This PR adds `top_k_varlen(..., row_starts=, absolute_indices=True)` and
fuses that add into the index emit of **both** windowed gvr_2 engine
families (streaming slab and register rungs):

- every emitted index already leaves the float4-rounded read frame
through one subtraction (`- lead`); the absolute frame is the same
single add with a different per-row constant (`+ col0`). No extra memory
traffic, no extra launch, no extra register.
- `-1` pads untouched; identity (short) windows shifted; out-of-window
columns never read; `return_values` gathers at the absolute columns.
- compile-time variant (`prefill_abs` in the compile keys, persist names
`..._pf_abs`): the register footprint is unchanged across the decode,
window-local and absolute compiles (`cuobjdump --dump-resource-usage` on
the DSL dump_dir cubins, B200, 2026-10-02):

(so `lmask` and `ks` do not cost a register at the 32-register wall; the
windowed compiles even carry 8 bytes less stack than decode). The
prefill launcher cache, `warmup_prefill(..., absolute_indices=)` and
`prefill_ready(..., absolute_indices=)` key on it.
- decode mode refuses the flag with a `ValueError` (its indices are
already columns of `logits`); non-bool values are refused.

Also fixes a `warmup_prefill` gap introduced with the register routing
of Part 2: the register table admits every hint of the mid buckets, so
the slab engine that an **unhinted** call of that width takes was never
compiled by warmup (`prefill_ready` False right after warmup; capture
would raise). Each bucket now also warms its slab tier at both promotion
edges.

</details>

<details>
<summary>Change log: review pass (2026-10-02) and API precision pass
(2026-10-12)</summary>

Fixes after the CodeRabbit pass and a full re-audit of the three
commits, one commit each:

- host `run_varlen`: the cross-device re-entry forwards
`absolute_indices` (it forwarded `row_starts` only; a windowed call with
logits on a non-current device returned window-local indices).
Two-device test added
(`test_prefill_absolute_indices_on_non_current_device`).
- API dispatch: the "row_starts needs gvr_2" refusal now runs right
after `backend` is resolved, so `skip_check=True` with
`backend="radix"`/`"gvr"` raises instead of ranking `[0, seq_len)`
(`test_prefill_skip_check_refuses_other_backends`).
- host: `top_k >= 4` in windowed mode (closes the only unmasked lane,
the scalar tail at `n4 == 0`, reachable only at `top_k <= 2` through the
host entry; the API admits 512/1024/2048).
- `warmup_prefill`: compiles and first-launches the exact launcher key
the serving call looks up (per 32768-row launch slab, both edges of
every bucket, hinted register rung + slab tier), on a one-row window,
instead of re-routing through `run_varlen` at a 297-row representative
(which could warm a different engine on Rubin and still mark done); the
done-key includes the stream; the no-op capacity-hint loop and the
unreachable `(512, 2, 4)` rung for `k == 2048` are gone. The default
workspace slab is resolved only for slab launches, so a hinted
register-rung capture on a fresh stream needs no eager call there;
`prefill_ready` takes the logits width, clamps the bound exactly as
`run_varlen` does, and checks the stream's slab for slab engines
(`test_prefill_warmup_custom_rows_cover_slabs_and_rungs`,
`test_prefill_hinted_capture_on_fresh_stream_needs_no_slab`, two
graph-replay tests).
- `max_seq_len` contract stated the same way in the API docstring, the
host docstrings and the route table: engine selection; register engine
-> exact or all `-1`, never truncated; slab -> exact.
- `max_seq_len` defaults to the logits width: a windowed call without a
bound now routes by the width exactly like a hinted call (the width is
always a valid bound; single-request chunks that fit a register rung no
longer fall to the slab); `warmup_prefill` and `prefill_ready` follow
the same rule. The `slab` columns of the Part 2 tables remain the
streaming-engine times.
- API description: a "Windowed (prefill) mode" section states that
`row_starts`, `max_seq_len` and `absolute_indices` exist for one layout
and have no effect on decode, and walks a toy chunk (two requests, one
cached token) through the layout, the two index frames and the engine
bound; each of the three parameter docstrings is marked "Windowed
(prefill) mode only".
- API: the windowed arguments `row_starts`, `max_seq_len`,
`absolute_indices` now follow `top_k` in the signature, the optional
hint `pre_idx` sits with the other optional knobs next to
`return_values`, and everything after `top_k` is keyword-only (no caller
in the repo or in the SGLang integration passed those positionally); the
checker and heuristic signatures mirror it. The three parameter
docstrings open with the plain-words meaning (where the request's keys
begin; an optional tighter bound that picks the engine; which address
frame the hits are written in).
- trace template: the width axis is `num_cols`; `max_seq_len` is
declared as an optional input so a trace dump keeps the bound; the check
rejects negative/out-of-window indices; `tests/trace/example.py` gained
a decode and a windowed `top_k_varlen` call
(`top_k_varlen_n8192_k1024.json`, `top_k_varlen_n4096_k512.json`).
- tests: 8192-bound fixture shrunk to one request (was 24576 x 24832
fp32, ~10 GB peak); `torch.where` poison; new cases for `next_n`
refusal, zero rows, `out_values` through the API, out-of-range
`row_starts`.
- comments: `row_ends` -> `row_starts` (2 sites), the `const_expr`
claim, the epilogue.

**API precision pass (2026-10-12).** `max_seq_len` -> `max_window_len`,
refused in decode mode (it bounds window lengths only). Windowed mode
refuses `next_n`, `compress_ratio` and `pre_idx` when passed, including
the old defaults; `next_n` and `compress_ratio` default to `None`
(meaning 1 in decode mode) so the body can tell "passed" from "omitted",
and the checkers and heuristic resolve the sentinel the same way. The
gvr_2 checker admits such calls so that `auto` reports the `ValueError`
instead of "no suitable backend". Docstring rewritten to the API
contract (opening paragraph per mode, per-parameter entries, backend
facts only under `backend`, admission precedence and `skip_check` in
Raises, examples for decode, decode with `next_n` + `compress_ratio`,
and windowed mode, run as doctests). Audit fixes, one commit each: trace
template clamps like the kernel and checks short windows;
`warmup_prefill` recreates the stream slab after a release; the warm-up
helpers probe the environment first; exact launcher-key assertions
(K=1024 added); explicit stream ordering in the graph tests; +inf inside
windows and all-(-inf) windows; tie-safe value comparisons; conflict
tests for every decode-only argument.

</details>

### Tests and gate

`tests/topk_varlen/test_topk_varlen_prefill.py` (115 tests: poisoned
out-of-window cells and lead lanes, causal ramps for K in {512, 1024,
2048}, ties and `-inf` masks, window-length edges, register rungs at
every capacity edge, bound handling, CUDA-graph replay, warm-up and
readiness, both index frames, API validation incl. every decode-only
argument under `auto`, explicit `gvr_2` and `skip_check=True`), plus
trace-template tests and the docstring examples as doctests. Decode
suites unchanged.

Gate at head 3dca1f7cd (full `tests/topk_varlen`, trace tests,
doctests):

| Leg | Result |
|---|---|
| B200 (SM100) | 469 passed / 6 skipped / 1 xfail; trace 8 passed;
doctest 29/29 |
| B100 + DRIVE P2021 visible together (two-GPU tests) | 472 passed / 2
skipped / 1 xfail + 1 pre-existing two-device failure in
`test_radix_filter.py::test_out_buffers_foreign_device_rejected`
(identical on main); doctest 29/29 |
| Rubin (SM107) | 470 passed / 5 skipped / 1 xfail; doctest 29/29 |
| H100, A100, L40S (no gvr_2) | 88 passed / 388 skipped each; doctest
14/14 (decode examples) |
| RTX 5080 (SM120) | 92 passed / 384 skipped; doctest 14/14 |

**Deferred to separate PRs** (pre-existing, not on this PR's path): the
`radix` backend does not clamp lengths beyond the row at
non-power-of-two widths and its checker admits padded views its kernel
refuses; the two-device `radix_filter` test expects an older error
message. The paged output frame of #5312 is decode-only.

## 🔍 Related Issues

Follow-up to #5288 (its "not ported: prefill window mode of #18702"
item). Upstream: NVIDIA/TensorRT-LLM#18702 (window mode; it has no
register-family prefill path and no absolute-index output, both reported
on the internal DKG tracker). Supersedes #5307 and #5310.

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

See "Tests and gate" above.

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

Part 1:
- Gate for the frame math: `test_prefill_packed_misaligned_ks` and
`test_prefill_neginf_masks_in_window`. The +inf poison directly before a
misaligned `ks` would become top-1 if any lead lane leaked; a missed
`-lead` correction shows up as a negative index.
- `seq_lens` meaning under `row_starts` (window length, not end) is
deliberate and documented in the API docstring; it keeps an SGLang-style
adapter to two tensors it already has (`ks`, `ke - ks`).

Part 2:
- `max_window_len` is deliberately a bound the caller vouches for, not
something the host derives (that would need a device-to-host read of
`seq_lens` and break CUDA-graph capture). A row is either ranked exactly
or, when its window plus the up-to-3 alignment lanes exceeds the
selected register engine's capacity (`BLK * VPT * 4 + 3`, part-dependent
via the per-arch table), reported as all `-1`, never a truncated
ranking. The streaming slab always ranks exactly.
- The per-part table lives in one function with the measurements in its
docstring; the Rubin branch keys on the arch token.

Part 3:
- The kernel diff is mechanical: in both engines every `idx - lead` emit
became `idx + ofs` with `ofs = -lead` (local) or `+col0` (absolute). The
slab keeps `col0` in a shared-memory word next to the existing lead-lane
slot (published once, read per emit); its identity epilogue re-reads
`row_starts[row]` because short rows skip the body and its barriers. The
register rungs run at a 32-register cap, so the absolute variant keeps
`ks` (= `col0 | lead`) as the ONE per-row value live through the
sampling ladder and recomputes `lead = ks & 3` (once per escape) and
`col0 = ks & -4` (per emit region). Alternatives measured on the VPT=1
rung and rejected: a second live register next to `lead` (3% slower), a
global re-read of `row_starts[row]` at emit (5%), a broadcast
shared-memory word (3%; the load gets hoisted back into a register).
- The default (window-local) compile is unchanged in register/stack
footprint (`cuobjdump --dump-resource-usage` identical); the local
column of the tables above matches the Part 2 numbers.
- Emit order of the engines is not fixed, so the tests compare row-wise
index sets (sorted), not raw tensors.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

- **New Features**
  - Added windowed prefill support for variable-length top-k selection.
- Added optional absolute-index output, allowing results to reference
original logits columns instead of window-local positions.
  - Added configurable row starts and maximum sequence lengths.
- Added prefill warmup and readiness support for efficient CUDA Graph
replay.
- Extended tracing and validation to cover windowed and absolute-index
workflows.

- **Bug Fixes**
- Improved handling of window boundaries, padding, masked values, and
short rows.
- Added clearer validation for unsupported backend and mode
combinations.

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [1ad1ed9](https://github.com/flashinfer-ai/flashinfer/commit/1ad1ed9245f0417cba0011ae85a43488129cca35)

- **作者**: Benjamin Chislett
- **时间**: 2026-10-13T19:26:34Z
- **提交信息**: fix(comm): synchronize LL clusters before peer shared-memory stores (#5652)

Co-authored-by: Codex

## 📌 Description

Fix a synchronization issue in the CUTEDSL MNNVL AllReduce kernel.

#### Codex Summary:

The LL residual/RMSNorm collective can access a peer CTA's distributed
shared memory before that CTA reaches the cluster rendezvous. Add an
initial cluster synchronization before the peer stores, retaining the
existing post-store and lifetime barriers.

Add numerical CUDA Graph replay coverage for the affected cluster
configurations, with changing rank-local inputs and both PDL modes. The
existing protocol tests retain their Blackwell architecture guard; the
new LL regression also runs on Rubin.


## 🔍 Related Issues

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

## Summary by CodeRabbit

* **Bug Fixes**
* Improved coordination during distributed RMSNorm reductions to support
reliable access to shared data across participating GPU blocks.

* **Tests**
* Expanded numerical contract coverage for LL all-reduce during CUDA
graph capture and replay, including varied cluster sizes, thread counts,
and PDL settings.
* Extended supported-device coverage to additional compute capabilities.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Benjamin Chislett <bchislett@nvidia.com>
Co-authored-by: Vincent Tombari <Vinnie6167@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [326f462](https://github.com/flashinfer-ai/flashinfer/commit/326f4628cfdaa11b447b3d982ee9d6855b657952)

- **作者**: eigen
- **时间**: 2026-10-13T18:35:00Z
- **提交信息**: perf(cake_sparse_mla): BF16 lever batch: online-softmax chunking, prologue rendezvous, split-KV reducer lane weights (SM100/SM103) (#6220)

## Summary

`backend="cake"` DSv4 sparse-MLA (SM100 / SM103) release. This PR's
branch now carries the cumulative re-export of the
Cake `cake_dsv4` programs from Cake `d6b11c4cec9` (Cake main
`1d3e37e570b`, the squash merge of the lever changes listed below, plus
the two
export-tool commits `ad0cd9e42d0` / `d6b11c4cec9` the loader render
needs; the kernel programs are identical to that main) on top of
upstream main `86da418ad50`; the previous content of the branch (the
single
`bf16_h128_swa128` two-chunk online-softmax change, head `1696866e1b0c`)
is kept on the fork branch
`backup/pr6220-round4-1696866e1` and is included in this release. Kernel
changes in this release:

- `bf16_h128_swa128` decode (4 export rows): two-chunk online softmax
over key halves (the 128-key window staged as two
64-key halves, QK of each half in its own TMEM S half, the softmax of
half 0 overlapping the K stages of half 1, exact
f32 merge: alpha0 = exp2(m0 c - m c), forced to 0 for an empty half 0;
the sink enters the max and the denominator once).
- `bf16_h8_swa128` (v43) and `bf16_h16` / `bf16_h32_swa128` (v44)
decode: the same two-chunk online softmax on the
384-thread single-CTA programs, plus an exact zero-row-sum guard on the
output normaliser (a query row with no attendable
column and no sink stores zeros instead of NaN, as the reference does;
no other output bit changes) with a lonely-row
  regression check in the registered validation entries.
- `bf16_h128_topk4x` and `bf16_h128_topk128x` (all schedules): the
authored prologue cluster sync is dropped and the
mbarrier/TMEM setup overlaps the collective TMEM allocation (three
prologue cluster barriers -> one); role bodies, masks,
  bytes, grid, signature and workspace unchanged.
- `bf16_h32_topk4x` / `bf16_h32_topk128x` (shared v48 body): two-chunk
online softmax by key halves (QK per half into two S
regions, the softmax of keys 0..63 overlapping the landing and QK of
keys 64..127, exact f32 online merge).
- split-KV reducers (`bf16_h64_compressed` reducer, the H128 split-4
warp-local reducer, the H128 topk4x lean / split-5
reducers): every lane loads the split lse values itself and sums the
split weights in the warp butterfly's exact order,
so the two warp butterflies and the shuffle broadcasts leave the
critical path; output bit-identical by construction.

Sparse-validity semantics and the host contract
(`flashinfer/mla/cake_dsv4.py`, `flashinfer/mla/_core.py`) are
unchanged. Precision classes are unchanged: f32 accumulation, exact exp2
/ rcp paths and the same masks everywhere; the two-chunk
online-softmax merges are exact f32 (alpha0 = exp2(m0 c - m c), fma
merges of l and O), so output bits of those programs
move only within the BF16 tolerance (atol = rtol = 1e-2) as recorded by
the per-row bit reports; the reducer change and the
prologue change are bit-identical by construction; the zero-row-sum
guard changes NaN -> 0 only on rows with no attendable
column and no sink.

## What changed
- `csrc/cake_dsv4/`: the unit sources of the programs listed above
regenerated from Cake `d6b11c4cec9`; every other unit
is re-rendered from the same tree (content-hash rename plus the current
generator output -- shared device-helper macros and formatting -- with
no intended kernel change). Per-architecture `*_kernel.cu` /
`*_binding.cu` units are
content-hashed (kernel symbol and host-shim namespace hashed over the
export identity, as in the previous releases);
no program folds into an architecture-neutral `common/` unit in this
release (0 units refreshed in place), so the previous
release's 26 `common/` units of this family (13 programs) are retired
together with its now-unreferenced hashed units (28 per
architecture, 82 retirements in total); the upstream NVFP4 units and
headers under `common/` are untouched. The upstream NVFP4 DSv4 decode
registrations of the loader are preserved verbatim.
- Shared headers:
`csrc/cake_dsv4/<arch>/cake_dsv4_{device,host}_common.cuh` per
architecture (each unit of that architecture
includes one of them by name: the 27 `*_kernel.cu` units the device
header, the 27 `*_binding.cu` units the host header;
the device header differs per architecture, the host header is
identical) and seven new content-addressed device helpers
under `csrc/cake_device_helpers/` (the helper directory shared with the
other Cake families; in this tree the seven new
files are included only by the per-architecture
`cake_dsv4_device_common.cuh`; existing helper files are untouched, none
  removed).
- `flashinfer/jit/cake_dsv4.py`: the `_ARCH_REGISTRATIONS` entries of
the exported programs are replaced; loader audit
against the base: 27 program entries per architecture replaced (the
exported families), 0 upstream NVFP4 entries touched (NVFP4 record diff
0 lines), all 34 `min_cuda_version` stamps unchanged; summary
passed_count 197/197 (sm_103a) and 196/197 (sm_100a, the documented
exception row).
- Export protocol unchanged (197 shapes per architecture, correctness +
source/export timing parity gates;
rows that fail only a timing gate are re-measured in place from the
closed prior, as in the previous releases; the
documented sm_100a measurement-gate exception - at most the two
`bf16_h64_prefill` hardening rows 000016 / 000036
failing only `directional_disagreement` with correct output after the
in-place re-measure - is accepted, the gate
itself is unchanged and every occurrence is recorded in the sm_100a
summary). sm_103a: 197/197 shapes passed (correctness 197/197). sm_100a:
196/197 shapes passed (correctness 197/197); the bf16_h64_prefill
hardening row 000036 fails only the directional-disagreement measurement
gate with correct output after the in-place single-worker re-measure
(recorded 000036: source_over_export 0.9768, ~46 us); documented
measurement-gate exception, gate not relaxed. Release commit:
`09d3435f6994` (sm_103a `e6f66513df57`, sm_100a `09d3435f6994`), two
commits on upstream main
  `86da418ad50`.

## Measured (paired CUPTI ABBA, kernel-sum medians, identical-text
control within +-0.5 %)
- GB300 (sm_103a), geomean B/A per change against the previous programs:
`bf16_h128_swa128` two-chunk online softmax (4
rows) 0.9936 (-0.6 %, 1/4 rows <= 0.99, 0 rows >= 1.01);
`bf16_h8_swa128` v43 (3 rows) 0.9821, `bf16_h16_swa128` v44 (3 rows)
0.9874,
`bf16_h32_swa128` v44 (2 rows) 0.9973 (neutral); `bf16_h128_topk4x`
prologue rendezvous (7 rows) 0.9429 (7/7 rows <= 0.99,
control 0.9984); `bf16_h128_topk128x` prologue rendezvous (11 rows)
about -2.9 % (10/11 rows <= 0.99, control 1.0027);
split-KV reducer lane weights: compressed H64 + reduce rows (14) 0.9635
(control 0.9987), H128 topk128x rows (11) 0.9878,
H128 topk4x rows (7) 0.9960; `bf16_h32` top-k two-chunk online softmax
(8 rows) 0.9786 (topk128x 0.9656, topk4x 0.9865,
  control 1.0016).
- B200 (sm_100a): `bf16_h128_swa128` (4 rows) 0.9592 (B2/A2 0.9593; -4.1
%, 4/4 rows <= 0.99); `bf16_h8_swa128` v43 (3 rows) 0.9452,
`bf16_h16_swa128` v44 (3 rows) 0.9401, `bf16_h32_swa128` v44 (2 rows)
0.9458; `bf16_h128_topk4x` (7 rows) 0.9307 (7/7
rows <= 0.99, control 1.0002); `bf16_h128_topk128x` (11 rows) about -2.9
% (11/11 rows <= 0.99, control 1.0034); split-KV
reducer lane weights: compressed H64 + reduce rows (14) 0.9677 (control
0.9995), H128 topk128x rows (11) 0.9857, H128
topk4x rows (7) 0.9854; `bf16_h32` top-k two-chunk online softmax (8
rows) 0.9730 (topk128x 0.9642, topk4x 0.9784,
  control 1.0009).
- The zero-row-sum guard is a correctness change, not a timing lever.
Export-time medians of this release against the
FlashInfer default trtllm-gen sparse-MLA path are in the export
summaries referenced above.

## Gates
- Per change, on its own tree before adoption (both architectures):
render diff against the base tree touching only the
targeted programs; dispatcher correctness on the 203 contract rows (94
canonical + 109 hardening) across the pad / sep / sepoff / allinv
mutation axes (check_rows, 839/839; the all-invalid-no-sink axis
targeted by the zero-row-sum guard was checked in the
guard's own chain, 24/24 on 6 SWA decode rows on both architectures);
bit-level output reports on the changed programs' rows (checksel:
bit-identical to the base tree for the reducer change (bits_sha256
152/152 rows, both
architectures) and for the prologue change on sm_100a (per-row output
hashes identical to the base, 35/35 topk4x and 47/47
topk128x rows; on sm_103a the prologue change passed checksel 35/35 and
47/47 within tolerance and is bit-identical by
construction), within the BF16 tolerance for the online-softmax
changes); compute-sanitizer synccheck and memcheck on those
rows (ERROR SUMMARY: 0 errors); the CPU rule tests of the exporter; the
ptxas spill gate (no new spills) for the split-KV reducer and `bf16_h32`
top-k changes only (the earlier
`bf16_h128_swa128`, v43 / v44 and prologue changes were adopted before
that gate existed; a later compile-only ptxas run of
the adopted `bf16_h128_swa128` program showed 0 spills / 0 stack on both
architectures); and the paired
  CUPTI ABBA above with an identical-text control pair in the same step.
- Release: loader audit against the base (`_ARCH_REGISTRATIONS` keys of
the exported programs replaced, upstream NVFP4
entries byte-identical): 27 program entries per architecture replaced
(the exported families), 0 upstream NVFP4 entries touched (NVFP4 record
diff 0 lines), all 34 `min_cuda_version` stamps unchanged; summary
passed_count 197/197 (sm_103a) and 196/197 (sm_100a, the documented
exception row); FlashInfer's pinned ruff (v0.12.8, FlashInfer's own
`[tool.ruff]` settings) on
  the released loader: clean.
- Fresh-clone FlashInfer DSv4 tests at the release commit: sm_103a
(GB300, fresh clone at `09d3435f6994`): 521 passed, 4 skipped, 0 failed
(163 s) / sm_100a (B200, fresh clone at `09d3435f6994`): 521 passed, 4
skipped, 0 failed (217 s).

## Changed files
```
     csrc/cake_device_helpers/cake_add_f32x2_inplace_a95ed15a53e197af.cuh                                                                  |   26 +
     csrc/cake_device_helpers/cake_elect_commit_cg2_multicast_18e7b4ad8e69c467.cuh                                                         |   32 +
     csrc/cake_device_helpers/cake_fma_f32x2_rn_noftz_e5a5b765e454e524.cuh                                                                 |   29 +
     csrc/cake_device_helpers/cake_index_318830c28ce182a7.cuh                                                                              |   35 +
     csrc/cake_device_helpers/cake_tma_4d_gmem2smem_cta2_85c32162ed442f8a.cuh                                                              |   30 +
     csrc/cake_device_helpers/cake_tma_gather4_gmem2smem_mc_cta2_b39cbf08703a66bf.cuh                                                      |   34 +
     csrc/cake_device_helpers/cake_tma_store_3d_a0d668161ec63906.cuh                                                                       |   29 +
     csrc/cake_dsv4/common/cake_dsv4_bf16_h128_swa128_kernel.cu                                                                            | 1073 --------------------------
     csrc/cake_dsv4/common/cake_dsv4_bf16_h16_h32_swa128_v44_kernel.cu                                                                     |  942 -----------------------
     csrc/cake_dsv4/common/cake_dsv4_bf16_h32_topk128x_early_v47_kernel.cu                                                                 | 1435 -----------------------------------
     csrc/cake_dsv4/common/cake_dsv4_bf16_h64_compressed_reduce_kernel.cu                                                                  |  261 -------
     csrc/cake_dsv4/{sm_103a/cake_dsv4_ac39da4cf9885a0981e8_binding.cu => sm_100a/cake_dsv4_155cefce7e1900a952c3_binding.cu}               |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_afe09a82c14f8bd895f4_kernel.cu => cake_dsv4_155cefce7e1900a952c3_kernel.cu}                         |  348 ++-------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_b3138c1168ef949b4019_binding.cu => cake_dsv4_1b4dfa2ab26fc784f640_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_b3138c1168ef949b4019_kernel.cu => cake_dsv4_1b4dfa2ab26fc784f640_kernel.cu}                         |  321 +-------
     csrc/cake_dsv4/{common/cake_dsv4_split_reduce_binding.cu => sm_100a/cake_dsv4_2b24cab15b398c9b420a_binding.cu}                        |   17 +-
     csrc/cake_dsv4/{common/cake_dsv4_split_reduce_kernel.cu => sm_100a/cake_dsv4_2b24cab15b398c9b420a_kernel.cu}                          |  106 +--
     csrc/cake_dsv4/{sm_103a/cake_dsv4_385acfbc8606f3d335b2_binding.cu => sm_100a/cake_dsv4_2cebeb2f2243d69b2827_binding.cu}               |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_fd59534f8fb24edd3529_kernel.cu => cake_dsv4_2cebeb2f2243d69b2827_kernel.cu}                         |  277 +------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_row_first_vsplit_binding.cu => sm_100a/cake_dsv4_3af1afa1871d27324303_binding.cu} |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_row_first_vsplit_kernel.cu => sm_100a/cake_dsv4_3af1afa1871d27324303_kernel.cu}   |  312 +-------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_compressed_q8_v38_binding.cu => sm_100a/cake_dsv4_58df983ae8026a009dab_binding.cu}          |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_compressed_q8_v38_kernel.cu => sm_100a/cake_dsv4_58df983ae8026a009dab_kernel.cu}            |  278 +------
     csrc/cake_dsv4/{sm_103a/cake_dsv4_7b76eac0776b050646fa_binding.cu => sm_100a/cake_dsv4_5d0c8e053e04ac001929_binding.cu}               |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_fp8_lowhead_h64_kernel.cu => sm_100a/cake_dsv4_5d0c8e053e04ac001929_kernel.cu}                       |  380 ++--------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_228778aae6bc72c4170d_binding.cu => cake_dsv4_61008e64c0c3bd2e1a83_binding.cu}                       |   44 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_61008e64c0c3bd2e1a83_kernel.cu                                                                       | 1277 +++++++++++++++++++++++++++++++
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_row_first_binding.cu => sm_100a/cake_dsv4_71e0baa44c61b948d82c_binding.cu}        |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_row_first_kernel.cu => sm_100a/cake_dsv4_71e0baa44c61b948d82c_kernel.cu}          |  312 +-------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_swa128_binding.cu => sm_100a/cake_dsv4_7abc1b8f5f3d1d936f1a_binding.cu}                    |   44 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_7abc1b8f5f3d1d936f1a_kernel.cu                                                                       | 1411 ++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_2beee9997128cc45a86b_binding.cu => cake_dsv4_820670a92a2bf9dfb2b0_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_2beee9997128cc45a86b_kernel.cu => cake_dsv4_820670a92a2bf9dfb2b0_kernel.cu}                         |  361 ++-------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_c602c3f805921b955ae5_binding.cu => cake_dsv4_860a0ac41a77c1305873_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_c602c3f805921b955ae5_kernel.cu => cake_dsv4_860a0ac41a77c1305873_kernel.cu}                         |  311 +-------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_d59492e451e80c110411_binding.cu => cake_dsv4_8a33d6688c16c25820e9_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_d59492e451e80c110411_kernel.cu => cake_dsv4_8a33d6688c16c25820e9_kernel.cu}                         |  303 +-------
     csrc/cake_dsv4/{common/cake_dsv4_fp8_lowhead_h64_binding.cu => sm_100a/cake_dsv4_9c5822db6c2739c63dc1_binding.cu}                     |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_0472b891257529a5f102_kernel.cu => cake_dsv4_9c5822db6c2739c63dc1_kernel.cu}                         |  333 ++------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_352cd296b2fa5c70f5f9_binding.cu => cake_dsv4_aa5800406f680b6ad9fc_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_746fa3d7b828ce3dd63c_kernel.cu => cake_dsv4_aa5800406f680b6ad9fc_kernel.cu}                         |  381 ++--------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_prefill_binding.cu => sm_100a/cake_dsv4_c85537d4ca6a34893cd1_binding.cu}                    |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_prefill_kernel.cu => sm_100a/cake_dsv4_c85537d4ca6a34893cd1_kernel.cu}                      |  276 +------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h32_topk128x_early_v47_binding.cu => sm_100a/cake_dsv4_c9156a2e9f65117a0900_binding.cu}         |   44 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_c9156a2e9f65117a0900_kernel.cu                                                                       | 1821 ++++++++++++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_4f1bc4343283f1ba5536_binding.cu => cake_dsv4_ca071620f07188f5ea22_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_4f1bc4343283f1ba5536_kernel.cu => cake_dsv4_ca071620f07188f5ea22_kernel.cu}                         |  348 ++-------
     csrc/cake_dsv4/sm_100a/{cake_dsv4_74706ad372b69a30483d_binding.cu => cake_dsv4_cc8f5e8152e47e5e566a_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_74706ad372b69a30483d_kernel.cu => cake_dsv4_cc8f5e8152e47e5e566a_kernel.cu}                         |  293 ++-----
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_guard_q_tma_batch_r25_binding.cu => sm_100a/cake_dsv4_cfa285ef8a408579ac99_binding.cu}      |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_guard_q_tma_batch_r25_kernel.cu => sm_100a/cake_dsv4_cfa285ef8a408579ac99_kernel.cu}        |  276 +------
     csrc/cake_dsv4/{common/cake_dsv4_fp8_h64_source_exact_binding.cu => sm_100a/cake_dsv4_d7c58d0212deccbcaf48_binding.cu}                |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_fp8_h64_source_exact_kernel.cu => sm_100a/cake_dsv4_d7c58d0212deccbcaf48_kernel.cu}                  |  298 +-------
     csrc/cake_dsv4/sm_100a/cake_dsv4_device_common.cuh                                                                                    |  112 +++
     csrc/cake_dsv4/{sm_103a/cake_dsv4_f1ee6630f05cf65f5f69_binding.cu => sm_100a/cake_dsv4_e1c7ffd7ad7de34b2096_binding.cu}               |   17 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_fa5539cb1afb7555dff5_kernel.cu => cake_dsv4_e1c7ffd7ad7de34b2096_kernel.cu}                         |  107 +--
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h16_h32_swa128_v44_binding.cu => sm_100a/cake_dsv4_e3b65d62b4db145adce7_binding.cu}             |   44 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_e3b65d62b4db145adce7_kernel.cu                                                                       | 1307 ++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_746fa3d7b828ce3dd63c_binding.cu => cake_dsv4_ee710a07143d70b73dc2_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_352cd296b2fa5c70f5f9_kernel.cu => cake_dsv4_ee710a07143d70b73dc2_kernel.cu}                         |  391 ++--------
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h64_compressed_reduce_binding.cu => sm_100a/cake_dsv4_efb864796f11291dc52c_binding.cu}          |   17 +-
     csrc/cake_dsv4/sm_100a/cake_dsv4_efb864796f11291dc52c_kernel.cu                                                                       |  330 ++++++++
     csrc/cake_dsv4/sm_100a/{cake_dsv4_c42c0d4632dca5f570a8_binding.cu => cake_dsv4_f98ac384c6e4f7fb86e4_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_100a/{cake_dsv4_c42c0d4632dca5f570a8_kernel.cu => cake_dsv4_f98ac384c6e4f7fb86e4_kernel.cu}                         |  293 ++-----
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_split4_sm100_binding.cu => sm_100a/cake_dsv4_fc73aade5a5f4f85a9e8_binding.cu}     |   42 +-
     csrc/cake_dsv4/{common/cake_dsv4_bf16_h128_topk128x_split4_sm100_kernel.cu => sm_100a/cake_dsv4_fc73aade5a5f4f85a9e8_kernel.cu}       |  321 +-------
     csrc/cake_dsv4/sm_100a/cake_dsv4_host_common.cuh                                                                                      |   52 ++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_c3cf2c612e13bf182910_binding.cu => cake_dsv4_06cdf778054cc6c67dc5_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_c3cf2c612e13bf182910_kernel.cu => cake_dsv4_06cdf778054cc6c67dc5_kernel.cu}                         |  311 +-------
     csrc/cake_dsv4/sm_103a/{cake_dsv4_a6efa79d7d8effe3fde4_binding.cu => cake_dsv4_14df2e7f409bd2c5c501_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_a6efa79d7d8effe3fde4_kernel.cu => cake_dsv4_14df2e7f409bd2c5c501_kernel.cu}                         |  385 ++--------
     csrc/cake_dsv4/sm_103a/{cake_dsv4_f4f571730c20919320eb_binding.cu => cake_dsv4_1dd9f772bf09c995842d_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_ac39da4cf9885a0981e8_kernel.cu => cake_dsv4_1dd9f772bf09c995842d_kernel.cu}                         |  348 ++-------
     csrc/cake_dsv4/{sm_100a/cake_dsv4_afe09a82c14f8bd895f4_binding.cu => sm_103a/cake_dsv4_25214a8d235e87a9cc33_binding.cu}               |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_f4f571730c20919320eb_kernel.cu => cake_dsv4_25214a8d235e87a9cc33_kernel.cu}                         |  348 ++-------
     csrc/cake_dsv4/sm_103a/cake_dsv4_2ada791761e6057628f6_binding.cu                                                                      |  318 ++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_2ada791761e6057628f6_kernel.cu                                                                       | 1629 +++++++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_985b70c1f95a44b1a915_binding.cu => cake_dsv4_34c0d39b1248c1010a15_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_985b70c1f95a44b1a915_kernel.cu => cake_dsv4_34c0d39b1248c1010a15_kernel.cu}                         |  293 ++-----
     csrc/cake_dsv4/sm_103a/{cake_dsv4_1a99f26bd105cfc54a61_binding.cu => cake_dsv4_3b2807f9cb6acd058bdf_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_1a99f26bd105cfc54a61_kernel.cu => cake_dsv4_3b2807f9cb6acd058bdf_kernel.cu}                         |  361 ++-------
     csrc/cake_dsv4/sm_103a/{cake_dsv4_a3e160c0c67071fa998a_binding.cu => cake_dsv4_3b4ec80fd59f1a59eb0d_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_a3e160c0c67071fa998a_kernel.cu => cake_dsv4_3b4ec80fd59f1a59eb0d_kernel.cu}                         |  317 +-------
     csrc/cake_dsv4/sm_103a/cake_dsv4_584c7f1bfa07e4783b08_binding.cu                                                                      |  323 ++++++++
     csrc/cake_dsv4/{sm_100a/cake_dsv4_228778aae6bc72c4170d_kernel.cu => sm_103a/cake_dsv4_584c7f1bfa07e4783b08_kernel.cu}                 |  858 ++++++++++-----------
     csrc/cake_dsv4/sm_103a/cake_dsv4_6a34a835c2b39424c20c_binding.cu                                                                      |  488 ++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_6a34a835c2b39424c20c_kernel.cu                                                                       | 1277 +++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_7383588b37366a763e1e_binding.cu                                                                      |  267 +++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_7383588b37366a763e1e_kernel.cu                                                                       | 1277 +++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_8543cb10ca15edd3a26b_binding.cu                                                                      |  318 ++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_8543cb10ca15edd3a26b_kernel.cu                                                                       | 1954 +++++++++++++++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/{sm_100a/cake_dsv4_fa5539cb1afb7555dff5_binding.cu => sm_103a/cake_dsv4_8b60cfd54a78d36864f4_binding.cu}               |   17 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_f1ee6630f05cf65f5f69_kernel.cu => cake_dsv4_8b60cfd54a78d36864f4_kernel.cu}                         |  107 +--
     csrc/cake_dsv4/sm_103a/{cake_dsv4_8c012a14f26c0b3fc996_binding.cu => cake_dsv4_8c2cf89e71be1ebbd233_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/cake_dsv4_8c2cf89e71be1ebbd233_kernel.cu                                                                       | 1335 ++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/{sm_100a/cake_dsv4_0472b891257529a5f102_binding.cu => sm_103a/cake_dsv4_914897d09f87971636b3_binding.cu}               |   42 +-
     csrc/cake_dsv4/sm_103a/cake_dsv4_914897d09f87971636b3_kernel.cu                                                                       | 3191 +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_9c1c6548071b6184d8e3_binding.cu                                                                      |  343 +++++++++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_7b76eac0776b050646fa_kernel.cu => cake_dsv4_9c1c6548071b6184d8e3_kernel.cu}                         |  333 ++------
     csrc/cake_dsv4/sm_103a/cake_dsv4_9c1ead828285aaa7f400_binding.cu                                                                      |  437 +++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_9c1ead828285aaa7f400_kernel.cu                                                                       | 1339 ++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a164ee5cbd7fc5b4d14d_binding.cu                                                                      |  267 +++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a164ee5cbd7fc5b4d14d_kernel.cu                                                                       | 1277 +++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a293c552f4c6f588106c_binding.cu                                                                      |  362 +++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a293c552f4c6f588106c_kernel.cu                                                                       |  745 ++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_a8b112bf2abd1a8ed848_binding.cu                                                                      |  437 +++++++++++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_8c012a14f26c0b3fc996_kernel.cu => cake_dsv4_a8b112bf2abd1a8ed848_kernel.cu}                         |  303 +-------
     csrc/cake_dsv4/sm_103a/cake_dsv4_aa6dd9bfdbb2d261b462_binding.cu                                                                      |   88 +++
     csrc/cake_dsv4/sm_103a/cake_dsv4_aa6dd9bfdbb2d261b462_kernel.cu                                                                       |  110 +++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_d8f0c13705d3d18d17b5_binding.cu => cake_dsv4_c09af191b368fc936d16_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_d8f0c13705d3d18d17b5_kernel.cu => cake_dsv4_c09af191b368fc936d16_kernel.cu}                         |  395 ++--------
     csrc/cake_dsv4/sm_103a/cake_dsv4_device_common.cuh                                                                                    |  112 +++
     csrc/cake_dsv4/sm_103a/{cake_dsv4_f3b968292b4c99769293_binding.cu => cake_dsv4_e875bc1d8a3b3ff27030_binding.cu}                       |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_f3b968292b4c99769293_kernel.cu => cake_dsv4_e875bc1d8a3b3ff27030_kernel.cu}                         |  293 ++-----
     csrc/cake_dsv4/sm_103a/cake_dsv4_e900f8c37ff1f0974a39_binding.cu                                                                      |   88 +++
     csrc/cake_dsv4/sm_103a/cake_dsv4_e900f8c37ff1f0974a39_kernel.cu                                                                       |  330 ++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_ebf2dfc077eb990f64fa_binding.cu                                                                      |  337 +++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_ebf2dfc077eb990f64fa_kernel.cu                                                                       | 1821 ++++++++++++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/{sm_100a/cake_dsv4_fd59534f8fb24edd3529_binding.cu => sm_103a/cake_dsv4_ee00a096a4346bd6ad78_binding.cu}               |   42 +-
     csrc/cake_dsv4/sm_103a/{cake_dsv4_385acfbc8606f3d335b2_kernel.cu => cake_dsv4_ee00a096a4346bd6ad78_kernel.cu}                         |  277 +------
     csrc/cake_dsv4/sm_103a/cake_dsv4_f52f0e6459ef0cca533b_binding.cu                                                                      |  287 -------
     csrc/cake_dsv4/sm_103a/cake_dsv4_f52f0e6459ef0cca533b_kernel.cu                                                                       |  942 -----------------------
     csrc/cake_dsv4/sm_103a/cake_dsv4_f918e4ac3c5b77c4514b_binding.cu                                                                      |  271 +++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_f918e4ac3c5b77c4514b_kernel.cu                                                                       | 1411 ++++++++++++++++++++++++++++++++++
     csrc/cake_dsv4/sm_103a/cake_dsv4_host_common.cuh                                                                                      |   52 ++
     flashinfer/jit/cake_dsv4.py                                                                                                           |  324 ++++----
     126 files changed, 31289 insertions(+), 15847 deletions(-)
```

## Tests
- `tests/mla/test_cake_dsv4.py`,
`tests/mla/test_cake_dsv4_hardening.py`: unchanged; run on a fresh clone
at the
  release commit on both architectures (results above).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [c04d681](https://github.com/flashinfer-ai/flashinfer/commit/c04d6811b7bcd4310262ebedd7b8c30e68e8698a)

- **作者**: Ka-Hyun Nam
- **时间**: 2026-10-13T17:11:17Z
- **提交信息**: fix(rope): require SM90 for cuTile FP8 rope quantization (#6378)

<!-- .github/pull_request_template.md -->

## 📌 Description

`rope_quantize_fp8(backend="cutile")` still fails on SM89 (L40S, L40,
L4, RTX 4090) with the same signature #6188 fixed for SM86: `ValueError:
No valid config found in search space` chained from
`UnsupportedFeatureError: float8_e4m3fn is not supported on sm_89`.

cuda.tile's FP8 floor is SM90, not SM89.
`cuda/tile/_passes/check_dtype_support.py` in cuda-tile 1.6.0 (current
latest) sets `_DTYPE_MIN_SM = {float8_e4m3fn: 90, float8_e5m2: 90, ...}`
with the note "Technically sm_89 (Ada Lovelace) supports FP8, but
tileiras doesn't have support for it yet", and the check compares only
the device SM number, so no tileiras version lowers it.

This moves the gate from #6188 to `(9, 0)` in the dispatcher and the
test skip, and parametrizes the CPU-safe regression test over SM86 and
SM89.

## 🔍 Related Issues

Follow-up to #6188. Fixes #6184 (the SM89 half of the same bug; nightly
SM86 is already green). Internal tracker: IKL-561.

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

`pytest tests/attention/test_rope.py::test_generalized_rope_quantize -k
cutile`, cuda-tile 1.6.0 / tileiras 13.3.36:

| GPU | main `03bd0aa68` | main + this PR |
|---|---|---|
| L40S (SM89) | FAIL, `float8_e4m3fn is not supported on sm_89` | 78
skipped "requires SM90 or newer; got SM89" |
| H100 NVL (SM90) | not run | 10 passed, 68 skipped by the existing MLA
/ e4m3fn / PDL guards |
| A10 (SM86) | 48 failed at pre-#6188 SHA `6dec771b1` (the nightly
signature); not re-run on pristine main | 78 skipped "requires SM90 or
newer; got SM86" |

`pytest tests/attention/test_rope.py -k cutile_rejects`: 5 passed
(`rejects_pre_sm90[(8,6)]`, `[(8,9)]`,
`rejects_unsupported[neox|multi_head_key|bad_backend]`).

Not verified: SM120 / SM100 cuTile runs are unchanged by this PR (the
gate only tightens for CC < 9.0), and I did not test a cuda-tile older
than 1.6.0.

## Reviewer Notes

The `No valid config found` wrapper is cuda.tile's `exhaustive_search`;
the real `UnsupportedFeatureError` is the chained cause in the
traceback. Nothing here changes that.

🤖 Generated with [Claude Code](https://claude.com/claude-code)


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Compatibility**
* The cuTile FP8 RoPE backend now requires SM90 or newer. Devices below
SM90 are rejected, and the requirement is documented.
* **Tests**
* Updated coverage verifies that SM86 and SM89 devices are treated as
unsupported.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [518f4c7](https://github.com/flashinfer-ai/flashinfer/commit/518f4c7f01b1b97fe57add94d46ddc1a80344e51)

- **作者**: BrianXDong
- **时间**: 2026-10-13T17:00:16Z
- **提交信息**: Introduce a local sccache MVP (#6268)

<!-- .github/pull_request_template.md -->

## 📌 Description

Adds a local sccache setup to the devcontainer, which transparently adds
compiler caching.
For the MVP, it's a 20gb docker managed volume.

## 🔍 Related Issues

None

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
## Summary by CodeRabbit

## New Features
* CUDA development containers now cache supported C++ and NVCC
compilation results in a persistent, per-container cache capped at 20
GB, which can help reduce rebuild times.
* The caching tool is available in the development image.

## Documentation
* Added guidance on checking cache statistics, configuring or disabling
NVCC caching, and understanding cache persistence, rebuilds, uncached
operations, and per-container cache limits.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [d6dd9f3](https://github.com/flashinfer-ai/flashinfer/commit/d6dd9f336dcd9e4820b1583d20077804fe61147c)

- **作者**: Adrian
- **时间**: 2026-10-13T16:34:34Z
- **提交信息**: ci: exclude sharding infrastructure tests from GPU jobs (#6431)

<!-- .github/pull_request_template.md -->

## 📌 Description

GPU CI currently collects the CPU-only tests under
`tests/test_sharding/` when running the full test tree. Add
`--ignore=tests/test_sharding` to `PYTEST_ADDOPTS` in the GPU branch of
`ci/bash.sh`, and forward it into the container by environment variable
name. Existing pytest options are preserved, including options
containing spaces.

Local pytest commands retain their existing collection behavior;
`pytest.ini` is unchanged.

## 🔍 Related Issues

None.

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

- [x] Validated with a temporary mocked Docker launcher and pytest
collection fixture; no permanent tests added for this shell
configuration change.
- [x] Focused checks passed: `bash -n ci/bash.sh`, `git diff --check`,
and `pre-commit run --files ci/bash.sh`.

The launcher checks cover unset and existing `PYTEST_ADDOPTS`,
forwarding by name, exclusion during broad GPU collection, unchanged
`--no-gpu` behavior, and local collection of both directories. GPU CI
was not run.

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

This change covers GPU jobs launched through `ci/bash.sh`. The internal
GitLab pipeline configuration is not present in this checkout, so
internal jobs that bypass this launcher are not covered.

Self-review found no defects requiring changes. Only `ci/bash.sh` is
included in this PR.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* GPU-mode test runs now exclude the sharding test path while preserving
other configured pytest options.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [a8e747c](https://github.com/flashinfer-ai/flashinfer/commit/a8e747c3c1f7dfe5d51fab3883824b15da6829b7)

- **作者**: Brandon Zhang
- **时间**: 2026-10-13T16:10:41Z
- **提交信息**: feat: uniform_q_len planner hint + specialized SM90 fp8-KV kernel for speculative-decoding target verify (#6144)

feat: uniform_q_len planner hint + specialized SM90 fp8-KV kernel for
speculative-decoding target verify
<!-- .github/pull_request_template.md -->

## 📌 Description

EAGLE speculative decoding verifies draft tokens with a prefill
attention call in which every request has exactly `draft_token_num`
query rows. FlashInfer's FA2 CUDA-graph planner cannot see that and
sizes its query tile for the ragged worst case, so on H200 with fp8 KV
it uses the 64-row tile for a 16-row problem. At long context each
verify launch runs 2-3x slower than it needs to, 15 times per decode
step.

Two changes:

1. **Planner hint.** `BatchPrefillWithPagedKVCacheWrapper.plan(...,
uniform_q_len=N)` (also the ragged wrapper and `workspace_size`) lets
the caller promise that every request has `N` query rows. The FA2
scheduler already supports this internally; the Python wrapper now
exposes it. The promise is checked against `qo_indptr` on the host and
dropped with a one-time warning if it does not hold. Trailing keyword,
default `None`; existing calls are unchanged; no C++ change.
2. **Specialized SM90 kernel.** A split-KV attention kernel plus fp32
merge for the EAGLE verify shape (4 query heads per KV head, head_dim
256, fp8 e4m3 KV, page size 1, custom mask, bf16 q/o), dispatched from
`run()` behind a strict eligibility check and falling back to the FA2
path on any miss. JIT only, SM90 only. Kill switch:
`FLASHINFER_DISABLE_EAGLE_VERIFY_FP8KV_SM90=1`.

### Scope

- The hint changes nothing unless a caller passes it. No caller in this
repo does. A serving framework enables it by passing
`uniform_q_len=draft_token_num` at its EAGLE verify plan, one keyword at
one call site (the SGLang change that does this is proposed separately).
- The kernel runs only when the shape above holds exactly, the caller
passed `uniform_q_len=4` and every request in the batch has 4 query rows
(checked on the host copy of `qo_indptr`, for eager and CUDA-graph plans
alike), compute capability is 9.0, and the call uses no LSE output,
attention sinks, KV scales, soft cap or sliding window. Everything else,
including every ordinary prefill, takes the stock path untouched.
- Wrappers built with custom `jit_args` are never routed to the kernel
(their attention variant is not the stock math), and the mask buffer
base must be 4-byte aligned because the kernel reads the mask as 32-bit
words; a misaligned caller-owned CUDA-graph buffer makes the plan
ineligible, a misaligned eager-mode buffer is re-allocated.
- Not a win at very short contexts (132 requests x 1k tokens: 0.97x of
the hinted FA2 path). Correct there, but outside the serving window.

### Results (Qwen3.5-397B-FP8, EAGLE, SGLang TP8, 8x H200)

Per verify launch, CUDA-graph replay with L2 flushed:

| running requests x KV tokens/request | production | hint only | hint +
kernel |
|---|---|---|---|
| 2 x 88k | 113 us | 76 us | 45 us (2.5x) |
| 4 x 169k | 364 us | 192 us | 106 us (3.4x) |
| 4 x 146k | 314 us | 169 us | 99 us (3.2x) |

End to end, agentic-coding trace at 10 concurrent sessions, one hour per
arm, production vs hint + kernel:

| | production | this PR |
|---|---|---|
| ITL p50 | 6.47 ms | 5.21 ms (-19.4 %) |
| ITL p90 | 9.83 ms | 7.96 ms (-19.0 %) |
| ITL p99 | 19.4 ms | 17.8 ms (-8.4 %) |
| output tok/s | 460 | 487 (+6.0 %) |
| normalized interactivity p50 | 115.5 tok/s per user | 136.1 (+17.8 %)
|
| normalized interactivity p90 | 65.9 | 73.6 (+11.7 %) |
| completed requests per hour | 1662 | 1748 (+5.2 %) |
| EAGLE accept length | 3.30 | 3.28 |
| errors | 0 | 0 |

Normalized interactivity is output tokens per second per user: each
request's end-to-end latency divided by its output tokens, then the
reciprocal of the p50 / p90 of that ratio across requests. p90 is
therefore the slow-tail user and sits below p50.

The hint alone gives ITL p50 -15 % and normalized interactivity p50
+15.0 % / p90 +11.6 %. An nsys capture confirms the verify launch goes
360 -> 185 -> 101 us at 4 running requests and that every verify site in
the captured graph uses the new kernel.

### Accuracy

Paired greedy GSM8K on the full test split (1319 questions, max 16384
tokens), same server with the kernel on vs off: 1273 vs 1274 correct
(McNemar p = 1.0; 11 questions flipped to wrong, 10 to right), median
response length identical, no repetition loops on either side. Output
lengths and accept length in the e2e run are unchanged. The kernel
changes the floating-point reduction order, so transcripts are not
byte-identical; at kernel level every output row is within cosine
0.99999 of an fp32 reference.

### Fixed during validation

Two CUDA-graph capture deadlocks were found and fixed before this
version: a programmatic-dependent-launch merge that held SM slots a
two-wave attention grid needed (the merge is now a plain stream-ordered
launch and the PDL path has been removed, not just disabled), and a
full-warp shuffle inside a half-warp loop that hung at odd split counts
(now a 16-lane mask, with a regression test at split counts 3, 7 and
29). The final kernel captured cleanly at all 51 graph batch sizes under
TP8.

## 🔍 Related Issues

None.

## 🚀 Pull Request Checklist

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [x] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues. (All hooks pass on every touched file:
pre-commit-hooks, tabs/CRLF, clang-format 19.1.1 on the `.cu`, mypy,
ruff check, ruff format.)

## 🧪 Tests

- [x] Tests have been added:
`tests/attention/test_prefill_uniform_q_len_plan.py` and
`tests/attention/test_eagle_verify_fp8kv_sm90.py` (CPU-side guards and
contracts, plus SM90 tests against the stock kernel and an fp32
reference, including the odd split counts).
- [x] All tests are passing. Run on an H100 (SM90, CUDA 13.0 container)
with this exact branch on top of `main`: the two new files 72 passed / 0
failed; `tests/attention/test_batch_prefill_kernels.py` 1348 passed, 214
skipped, 0 failed.

## Reviewer Notes

The kernel is SM90-only, JIT-only and gated to one geometry; nothing
changes for other architectures or shapes. The `uniform_q_len` keyword
is inert until a caller passes it.

Performance and accuracy were measured on the release-0.6.18 line, then
the change was rebased onto `main`; the device code is byte-identical (0
differing PTX lines). Running the tests on `main` and the first review
surfaced five issues that the third commit fixes (custom `jit_args`
wrappers were not excluded from the route; the mask buffer base
alignment was not checked; eager-mode plans never reached the kernel
because eligibility read the value forwarded to the FA2 planner, which
is 0 outside CUDA-graph mode; the one-time kernel init was recorded per
device rather than per module object, so a replaced module could launch
without its shared-memory opt-in; and the tests sized the mask buffer
from the total bit count although `segment_packbits` pads each request
to a byte boundary).

AI assistance was used to prepare this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Alex Yang <aleyang@nvidia.com>

### [74ca44b](https://github.com/flashinfer-ai/flashinfer/commit/74ca44b318a3be013649baabca698099d0862e3c)

- **作者**: Adrian
- **时间**: 2026-10-13T15:15:53Z
- **提交信息**: test(logits_processor): size trials by effective support (#5515)

<!-- .github/pull_request_template.md -->

## 📌 Description

Replace the fixed five-million-trial count in logits-processor frequency
tests with a count derived from each test distribution's effective
support, `1 / sum(p_i**2)`.

The helper sizes the sample count for the existing `0.99`
cosine-similarity check between two empirical distributions, applies a
`1.25` safety factor, and retains a minimum of 10,000 trials. Filtered
tests compute effective support after top-k, top-p, min-p, or joint
filtering, so concentrated distributions no longer pay the cost required
by the broadest distribution.

On one SM100 GPU (compute capability 10.0, 183,359 MiB), running

```bash
PYENV_VERSION=pt python -m pytest tests/utils/test_logits_processor.py -q --durations=20
```

produced:

- Before, estimated warm-cache pytest time: 180.51 s. This removes the
measured 65.05 s one-time cold-JIT delta from the 245.56 s cold-cache
run.
- After, measured warm-cache pytest time: 14.67 s.
- Result: 591 passed, 12 skipped.
- Improvement: 12.3x faster, or a 91.9% reduction in pytest time.

Cold JIT compilation is unchanged by this test-only change.

## 🔍 Related Issues

None.

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

The trial-count formula is a multinomial-variance approximation tailored
to the existing cosine-similarity assertion, not a formal
high-probability bound. A `1.10` safety factor exposed a deterministic
boundary failure (`0.98977`) for top-k=500 at vocabulary size 128,256;
`1.25` passed the complete matrix.

The math behind the function to determine the number of trials is as
follows:

Let $p = (p_1, \dots, p_V)^\top$ with $p_i \ge 0$ and $\sum_i p_i=1$ be
a categorical probability distribution over a vocabulary of size $V$. We
draw $N$ i.i.d. samples from $p$ to form the empirical probability
vector $\hat p$, which should be close to $p$. If we draw again, the two
empirical probability vectors should also be close. The closeness is
defined using cosine similarity.

Let $e_i$ be the $i$-th standard basis vector (one-hot), then the $t$-th
sample we draw can be represented by $Y_t \in \{e_1, \ldots, e_V\}$, in
which $\Pr[Y_t = e_i] = p_i$.

Then we have $\mathbb{E}[Y_t] = \sum_{i=1}^{V} p_i e_i = p$. The
(auto-)covariance matrix of random vector $Y_t$ is then

$$
  \mathrm{Cov}(Y_t)
  = \mathbb{E}\big[
      (Y_t-p)(Y_t-p)^\top
    \big]
  = \mathbb{E}[Y_tY_t^\top] - \mathbb{E}[2pY_t^\top] + pp^\top
  = \mathbb{E}[Y_tY_t^\top] - pp^\top.
$$

Because $Y_t$ is one-hot, $Y_tY_t^\top$ is diagonal, consequently,
$\mathbb{E}[Y_tY_t^\top] = \mathrm{diag}(p)$

and hence

$$
\begin{aligned}
  \mathrm{Cov}(Y_t) &= \mathrm{diag}(p) - pp^\top \\
  \mathrm{Cov}(Y_{t,i},Y_{t,j}) &= \begin{cases}
    p_i(1-p_i) & \text{if }i=j, \\
    -p_ip_j & \text{if }i\ne j.
  \end{cases}
\end{aligned}
$$

The negative entries off-diagonal is because selecting one category
excludes all other categories in the same trial.

The empirical distribution is

$$
  \hat p = \frac{1}{N}\sum_{t=1}^{N}Y_t.
$$

Since the sampling is i.i.d., we have $\mathbb{E}[\hat p] = p$ and
$\mathrm{Cov}(\hat p) = \frac{1}{N} (\mathrm{diag}(p)-pp^\top)$.

If $\hat p = p + \epsilon$ for $\epsilon$ the sampling error, and
$\mathbb{E}[\epsilon]=0$, its expected that the squared Euclidean
magnitude is the trace of its covariance:

$$
\begin{align}
  \mathbb{E}[\lvert\epsilon\rvert_2^2]
  &= \mathrm{tr}\big(\mathrm{Cov}(\hat p)\big) \\
&= \frac{1}{N}\big( \mathrm{tr}(\mathrm{diag}(p)) - \mathrm{tr}(pp^\top)
\big) \\
  &= \frac{1-\lvert p\rvert_2^2}{N}.
\end{align}
$$

We can consider this as the noise power. The signal power is trivially
$\lvert p \rvert_2^2$. Then the SNR is

$$
\text{SNR}
= \frac{\lvert p\rvert_2^2}{\mathbb{E}[\lvert \epsilon \rvert_2^2]}
= \frac{N\lvert p\rvert_2^2}{1-\lvert p\rvert_2^2}.
$$

Define the effective support of $p$ by $S_\text{eff} = 1/\sum_i p_i^2 =
1/\lvert p\rvert_2^2$, then we can write

$$
\text{SNR} = \frac{N}{S_\text{eff}-1}.
$$

If $p$ is concentrated like a one-hot, we have $S_\text{eff}=1$. If the
distribution $p$ is very diffused, we have $S_\text{eff}\gg 1$. In
particular when the distribution is uniform over $V'$ categories (in
which case $V-V'$ categories are always with probability zero),
$p_i=1/V'$ and $S_\text{eff}=V'$. In the diffuse scenarios,
$\text{SNR}\approx N/S_\text{eff}$.

Let $s = \lvert p\rvert_2^2$. The cosine similarity between $\hat
p=p+\epsilon$ and $p$ is exactly

$$
\begin{aligned}
  \cos(\widehat p,p)
  &= \frac{(p+\epsilon)^\top p}
          {\lvert p+\epsilon\rvert_2\cdot \lvert p\rvert_2} \\
  &= \frac{s+p^\top \epsilon}
{\sqrt{s+2p^\top \epsilon + \lvert\epsilon\rvert_2^2}\cdot\sqrt{s}} \\
  &= \frac{1+a}{\sqrt{1+2a+b}},
\end{aligned}
$$

where

$$
  a = \frac{p^\top\epsilon}{s},
  \qquad
  b = \frac{\lvert\epsilon\rvert_2^2}{s}.
$$

Since $\mathbb{E}[a]=0$, it can be ignored. And
$\mathbb{E}[b]=1/\text{SNR}$ (see the formula above),

$$
  \cos(\hat p,p) = c
  \approx \frac{1}{\sqrt{1+1/\text{SNR}}}
  = \frac{1}{
      \sqrt{1+(S_\text{eff}-1)/N}
    }
  \approx \frac{1}{
      \sqrt{1+S_\text{eff}/N}
    }.
$$

To meet a specified cosine similarity $c\in(0,1)$, solve

$$
\begin{aligned}
  c & \le \frac{1}{\sqrt{1+S_\text{eff}/N}} \\
  \frac{S_\text{eff}}{N} & \le \frac{1}{c^2} - 1 \\
  N & \ge S_\text{eff}\frac{c^2}{1-c^2}
\end{aligned}
$$

At $c=0.99$, that means $N$ is around $49.25 S_\text{eff}$.

Let's consider the case of having two empirical distribution vectors
sampled.

Let $\hat p_1 = p+\epsilon_1$ and $\hat p_2=p+\epsilon_2$ are sampled
from $p$ using the same i.i.d. process.

With zero mean error $\mathbb{E}[\epsilon_1]=\mathbb{E}[\epsilon_2]=0$
and i.i.d., we have $\mathbb{E}[\hat p_1\hat p_2]=\vert p\vert_2^2 = s$.

Also, we have

$$
\begin{align}
  \mathbb{E}[\lvert\hat p_j\rvert_2^2]
  &= s + \mathbb{E}[\lvert\epsilon_j\rvert_2^2] \\
  &= s + s/\text{SNR} \\
  &= s(1+1/\text{SNR}) \\
  \therefore\; \cos(\hat p_1, \hat p_2)
& \approx \frac{s}{\sqrt{s(1+1/\text{SNR})}\sqrt{s(1+1/\text{SNR})}} \\
  & = \frac{1}{1+1/\text{SNR}} \\
  & \approx \frac{1}{1+S_\text{eff}/N}
\end{align}
$$

with the threshold of $\cos(\hat p_1,\hat p_2)\ge c$, we get

$$
N \ge \frac{c}{1-c}S_\text{eff}.
$$

At $c=0.99$, that means $N$ is around $99 S_\text{eff}$. (More trials
required because we do not have the clean probability vector $p$ to
compare.)

Note that the $N$ computed is the required minimum to achieve cosine
similarity of $c$. Multiply it by a safe margin factor is always
preferred.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **Tests**
* Updated sampling-frequency test coverage to adjust trial counts based
on the probability distribution being tested, including filtered
sampling scenarios. This replaces a fixed trial count with a
distribution-sensitive approach.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

### [399b6c1](https://github.com/flashinfer-ai/flashinfer/commit/399b6c1d31a13f38dd827018f89c6a04c8487acb)

- **作者**: Zhong Zheng
- **时间**: 2026-10-13T10:42:48Z
- **提交信息**: feat(cake_mega_moe): [SM120] MXFP4 x MXFP8 MegaMoE through MoEEpLayer (sm120_mxfp4_mxfp8_bf16_cake) (#6346)

<!-- .github/pull_request_template.md -->

## 📌 Description

Co-authors: @jychen21 @AichenF

Submitted by: @GnohzZ.

Adds `sm120_mxfp4_mxfp8_bf16_cake` through `MoEEpLayer`: a
Cake-generated SM120 MegaMoE backend
(MXFP8 activations, MXFP4 routed weights, BF16 output) whose
expert-parallel traffic goes **over RDMA
with NCCL GPU-initiated networking (GIN), issued from inside one
persistent kernel**.

- **EP over RDMA from inside the kernel (NCCL GIN).** Dispatch, FC1 +
SwiGLU + FP8 requantization,
FC2, the expert-result return and the weighted combine run in one
cooperative persistent kernel.
Payloads between EP ranks are NCCL Device API GIN puts with signals,
issued by the kernel itself on
NCCL symmetric windows (NCCL 2.30.7) — no separate dispatch / combine
kernels. The same
kernel runs multi-host EP (EP16 over two hosts validated) and
single-host pairs that cross PCIe
sockets (EP8 below). The existing SM120 MegaMoE backend (#4632) moves
data through NVSHMEM peer
  pointers, i.e. within one host.
- **LSA, a by-product of the same transport design.** The transport is
chosen per EP-rank pair:
GIN, or LSA (load/store over peer mappings of the same symmetric
windows, streamed by dedicated
copier CTAs). LSA inside a host and GIN across hosts run in one launch.
On our PCIe host the LSA
tables are also faster than the existing PCIe-based paths (table below).
- Optional in-kernel FP8 shared expert, configurable SwiGLU clamp, EPLB
physical expert ids;
compile-time shape parameters (DeepSeek-V4-Flash, DeepSeek-V3 and
Qwen3-235B/30B geometries tested).
- No per-call host synchronization and CUDA-graph capture with a token
bucket, through the existing
`MoEEpMegaLayer.stage_inputs(t, compile_tokens_per_rank=...)` hook (the
one #4632 uses for its graph
  buckets). No shared moe_ep API changes.
- JIT per parameter set. `flashinfer/aot.py` packages the binding and
the DeepSeek-V4-Flash EP4 / EP8
  device instances (embedded-cubin JIT modules).

**Scope.** This PR targets prefill: it is tested and benchmarked from
512 tokens per rank upward.
Decode-size batches, other model families and serving-framework
integration are not part of this PR.

Requires SM120 (compute capability 12.0), CUDA 13 and NCCL 2.30.7 with
the Device API.
Kernel package: `flashinfer/moe_ep/kernel_src/sm120/cake_mxfp4_megamoe/`
(generated, manifest-sealed
`src/`, JIT loader `shim/`); backend:
`flashinfer/moe_ep/backends/mega/kernel/sm120/mxfp4_mxfp8_bf16_cake/`.
See the [kernel package
guide](https://github.com/GnohzZ/flashinfer/blob/cb344609d76767418ef1e2905eaad55c2b1721c9/flashinfer/moe_ep/kernel_src/sm120/cake_mxfp4_megamoe/README.md)
for configuration, supported shapes, CUDA graphs and
runtime requirements.

**CUDA graphs.** One graph per token bucket, after one eager call of the
layer on its workspace; every
rank replays the same bucket sequence:

```python
layer(warmup_inputs)                       # eager call: uploads the weights' TMA descriptors
for bucket in (512, 1024, 2048, 4096):     # same buckets on every rank
    with torch.cuda.graph(graphs[bucket]):
        layer.stage_inputs(static[bucket], compile_tokens_per_rank=bucket)
        out[bucket] = layer.compute_staged(output=None)
```

### Performance

RTX PRO 5000 Blackwell GPUs (72 GB each), PCIe, ConnectX-8 400G, CUDA
13.0, NCCL 2.30.7.
DeepSeek-V4-Flash layer 20: E256 / H4096 / I2048 / top-k 6, real MXFP4
weights,
captured activations and routing, routed experts only. Cold L2; 64
warmups + 21 timed calls.
FlashInfer timings cover prestaged `compute_staged` using CUPTI; DeepEP
+ DeepGEMM timings
cover dispatch through combine. Input staging and weight preprocessing
are excluded.
W4A4 requantizes dispatched FP8 activations to FP4 for the GEMMs; W4A8
uses MXFP8 activations.

**EP4 latency (ms, lower is better):**

| Implementation | 512 tokens/rank | 1024 | 2048 | 4096 | 8192 |
|---|---:|---:|---:|---:|---:|
| Cake, GIN (`all_gin`) | 1.43 | 1.97 | 2.88 | 5.27 | 10.01 |
| Cake, LSA (`all_lsa`: PCIe peer load/store, no NIC) | 1.44 | 2.00 |
2.94 | 5.39 | 10.36 |
| FlashInfer CuTeDSL (#4632) | 2.27 | 2.51 | 4.30 | 6.75 | 12.89 |
| DeepEP v2 + DeepGEMM, W4A4 | 1.89 | 2.60 | 4.14 | 7.58 | 14.48 |
| DeepEP v2 + DeepGEMM, W4A8 | 2.11 | 3.06 | 5.07 | 9.39 | 17.71 |

Over GIN, Cake is **1.27–1.59× faster than #4632**; over LSA it is
1.24–1.58× faster than #4632 and
1.30–1.41× faster than DeepEP v2 + DeepGEMM (W4A4) at these EP4 points.
The LSA row was measured on head
`cb344609` on a second host of the same type, where #4632 reproduced
within 1 % (2.29 / 13.04 ms at
512 / 8192 tokens per rank); its output matched the reference bit for
bit (rel-L2 0) on every rank.

**EP8 latency on one host spanning two PCIe sockets (ms), Cake over
GIN:**

| Implementation | 512 tokens/rank | 2048 | 8192 |
|---|---:|---:|---:|
| Cake, GIN (`all_gin`) | 1.57 | 3.80 | 14.10 |
| FlashInfer CuTeDSL (#4632) | 70.28 | 268.66 | 1109.67 |
| DeepEP v2 + DeepGEMM, W4A4 | 37.85 | 149.65 | 599.34 |

The EP8 gap is specific to this topology and transport configuration;
the baselines were not profiled
for root cause. FlashInfer uses the median of per-call maximum-rank
latency; DeepEP uses its harness's
maximum-rank total-stage median. The Cake GIN rows and the baselines
were measured before final
integration on the same device code; they were not rerun on this
revision, whose device cubins are byte-identical to the measured build.
The comparison harness and real-weight fixture are
not included in this PR.

**Included benchmark** (reproducible, synthetic inputs, CUDA events,
head `cb344609`):
`torchrun --nproc_per_node=<EP>
benchmarks/moe_ep/backends/mega/kernel/sm120/bench_moe_ep_sm120_w4a8_cake_mega.py`
(V4-Flash geometry, `all_gin`; max-rank median, µs). `forward` includes
the per-call routing all-gather;
`bucket` passes `compile_tokens_per_rank`; `graph` replays a captured
bucketed call.

| tokens/rank | EP4 kernel | EP4 forward | EP4 bucket | EP4 graph | EP8
kernel | EP8 forward | EP8 bucket | EP8 graph |
|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 512 | 1087 | 1450 | 1166 | 1141 | 899 | 1252 | 980 | 956 |
| 1024 | 1403 | 1796 | 1523 | 1499 | 1434 | 1830 | 1568 | 1545 |
| 2048 | 2334 | 2803 | 2543 | 2533 | 2588 | 3069 | 2764 | 2919 |
| 4096 | 4111 | 4835 | 4754 | 4549 | 4915 | 5676 | 5425 | 5330 |
| 8192 | 8641 | 10094 | 9939 | 9782 | 9684 | 11186 | 10744 | 10660 |

Routed experts only (`noshared`); the run also reports the `fp8shared`
variant.
EP8 = one host, eight GPUs over two PCIe sockets.

## 🔍 Related Issues

Related backend: #4632 (`sm120_mxfp4_mxfp8_bf16_cutedsl`).

## 🚀 Pull Request Checklist

Thank you for contributing to FlashInfer! Before we review your pull
request, please make sure the following items are complete.

### ✅ Pre-commit Checks

- [x] I have installed `pre-commit` by running `pip install pre-commit`
(or used your preferred method).
- [ ] I have installed the hooks with `pre-commit install`.
- [x] I have run the hooks manually with `pre-commit run --all-files`
and fixed any reported issues.

Repository-wide `pre-commit run --all-files` passed on `cb344609`.
Automatic commit hooks are not installed.

> If you are unsure about how to set up `pre-commit`, see [the
pre-commit documentation](https://pre-commit.com/).

## 🧪 Tests

- [x] Tests have been added or updated as needed.
- [x] All tests are passing (`unittest`, etc.).

This checkbox covers the PR-related tests below on head `cb344609`; the
repository-wide
multi-architecture GPU suite and upstream CI have not run. The GPU runs
used the same PR tree before its rebase
onto `f63b2e7c` (one unrelated GEMM commit); host tests and pre-commit
were re-run after the rebase.
GPU counts are **per rank**; EP16 uses two hosts.

| Suite | EP4 | EP8 | EP16 |
|---|---:|---:|---:|
| MegaMoE correctness, routing, token buckets, streams and CUDA graphs |
144 | 144 | 144 † |
| EPLB | 2 | 2 | 2 † |
| Feasible transport tables: bitwise parity + reference | 2 | 2 | 2 † |
| Real-weight fixture: bitwise parity with generator harness | 2 | 2 |
Not run |

† EP16 (two hosts) ran on the previous revision (`91c1f0c0`), whose
device code is byte-identical; the
token-bucket host path and the kernel-package move were not rerun at
EP16.

Host tests (no GPU): **36 passed**; without torchrun, sm_120, NCCL
2.30.7 or one GPU per local
rank the multi-rank files skip. The kernel tests compare against an
independent PyTorch reference
(relative L2 threshold: 2%, plus elementwise checks); transport, EPLB,
token-bucket and graph tests also
check bitwise equivalence (graphs: three buckets covering both row
schedules, replayed in a mixed order).
The generator harness also passed 12 synccheck runs, 22 EP4 all-LSA
racecheck runs, and 3,000
individually validated calls with launch skew.

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

- Layout follows the moe_ep kernel-drop convention
(`kernel_src/sm120/cake_mxfp4_megamoe/{src,shim}`, like
the SM90 Cake backend). The generated sources are manifest-checked
(SHA-256) and excluded from formatting;
the device source is split into parts below the 500 KB file limit. The
binding and the cubin carrier are
  hand-written and formatted.
- JIT / AOT: each device module embeds the cubins of one parameter set
(`embedded_cubin_factory`), so the
cache, locking and `FLASHINFER_DISABLE_JIT` behave as for other JIT
modules. `MOE_MAX_ROWS`
(`max_tokens_per_rank`) is a compile-time parameter, so AOT covers only
the default V4-Flash EP4 / EP8
instances at 4096 tokens per rank; other deployments compile on first
use (about 10 s per instance).
- NCCL is pinned to exactly 2.30.7 (repository floor: >= 2.30.7): the
device code inlines the Device API
(GIN / LSA) of the headers it is compiled against, and only 2.30.7 was
validated.
- Token buckets: a bucket above the true largest per-rank count is
correct (tested bitwise against the
routing exchange) but may pick the M128 schedule; the exact largest
count reproduces the exchanged schedule.
- Known limits: EP2 is untested; EP32 is compile-checked only. LSA was
tested over PCIe, not NVLink.
Pin `NCCL_TOPO_FILE` on multi-GPU PCIe hosts. Large same-host GIN calls
showed RoCE latency tails;
  LSA tables avoid that path.
- The 600 s device deadlines are not a universal timeout: some local CTA
waits and the initial NCCL
barrier are unbounded. `protocol_error(workspace)` is not checked by
forward; a nonzero flag means
  invalid output and the workspace should be discarded.
- Follow-ups (not in this PR): decode-size batches, other model
families, serving-framework integration.

<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a Blackwell SM120 MegaMoE backend for MXFP4 weights and MXFP8
activations, with optional FP8 shared-expert support.
* Added configurable transport selection, tuning and benchmarking tools,
and token-bucket execution for CUDA graph capture and replay.
* Added public APIs for backend configuration and weight preprocessing.
* **Documentation**
* Added setup, deployment, transport, and benchmarking guidance for the
new backend.
* **Tests**
* Added coverage for numerical results, transport options, distributed
execution, CUDA graph replay, and real-weight fixtures.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Co-authored-by: Zhong Zheng <zhongz@nvidia.com>
Co-authored-by: Zihao Ye <expye@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [b9c2335](https://github.com/flashinfer-ai/flashinfer/commit/b9c2335181c89844673937c2ff1c96aae49c7b57)

- **作者**: eigen
- **时间**: 2026-10-13T08:50:27Z
- **提交信息**: perf(cake_fused_moe): device-side GEMM2 path gate for the Kimi-K3 W4A8 MXFP4 SiTU mixed192 long-prefill chain (cake, cake_cute) (#6411)

## Summary

Re-renders the two Cake-exported Kimi-K3 W4A8 MXFP4 SiTU routed-MoE
backends (`flashinfer/fused_moe/cake_mxfp4_situ_moe/` for
`backend="cake"` and `cake_cute_mxfp4_situ_moe/` for
`backend="cake_cute"`) from Cake revision `acf3ba642c1` (manifests pin
`producer_revision` `acf3ba642c1039f44b4b86709b897ef4ab1a62cc`;
previously `9316cbf49bd21548735f2d9720f2375b883a5c69`). Export +
evidence only; no FlashInfer API change.

What the re-render brings (one Cake kernel-IR change lowered to both
backends):

- **Device-side GEMM2 path gate on the tp8 long-prefill chain (T ≥
16384)**: a one-warp gate kernel (`gemm2_gate`, PDL) launched right
after `moe_sort` replays the dense GEMM2 kernels' own raster vote over
the sort tables and selects the split or the dense GEMM2 path on the
device. The plan runs a fixed 12-launch chain with both finalize paths
bound to the gate words; the unselected path's launches exit with zero
items, so CUDA-graph capture keeps one launch list. Before this change
the path was fixed per row by the host.
- New modules per backend: `gemm2_gate` and the
`gemm2_dense_finalize_n192_c12_rg` / `_rg_rauto` wide-list forms
(host-forced instrument path, not selected by default).
- The 8192-token chain and every previously shipped kernel render
byte-identical (render pair vs the pristine FlashInfer main checkout:
`cake` 107 / 107 and `cake_cute` 95 / 95 previously shipped modules
identical in every field).

Measured effect (B300, whole-GPU isolated, CUPTI-paired graph replay vs
the trtllm-gen baseline, 51 paired rows per backend): the tp8 rank-0,
32768-token, hot-set routing row moves from the dense to the split path
and its kernel time drops 8.4 % (`cake`) / 9.5 % (`cake_cute`) in a
same-GPU A/B/A against the previous export (speedup vs trtllm-gen 1.096
→ 1.214 / 1.094 → 1.212); every other row keeps its kernels, grids and
work lists (within the run-to-run band). Both backends: 91 / 91 rows
correct, 51 / 51 paired rows ≥ 1.0, geomean 1.2536 (`cake`) / 1.2469
(`cake_cute`) (previous export 1.2506 / 1.2458).

Numerics: the moved row changes its bf16 reduce-add arrival class (split
instead of dense); agreement with the hand-written kernels stays in the
bf16 class, the FP64 oracle passes on every row (per-row max abs 0.0142
at most on both backends over 87 oracle rows), and 5-run error medians
of the gated chain stay within 1.10× of the same-GPU hand-written
control (18 / 18 statistics). Tolerances unchanged.

## Evidence (B300, sm_103a, whole-GPU isolated steps, CUPTI-paired
timing)

- Export base: FlashInfer main `86da418ad500` (render, `ship-apply`,
`verify` and the tests below ran on that tree); the branch is rebased
onto the current main `388e7a311e9f` (one newer commit, not touching the
export paths).

- Render identity: `verify --flashinfer --revision acf3ba642c1` clean
after `ship-apply`; 208 launcher modules rendered and verified (110 cake
+ 98 cake_cute; +3 per backend: `gemm2_gate`,
`gemm2_dense_finalize_n192_c12_rg`, `_rg_rauto`), 0 previously shipped
kernel sources changed, 91 / 91 executable rows per backend. Render pair
vs the pristine FlashInfer main checkout: every previously shipped
module pairs with identical module identity, schedule identity, argument
plan, closure, launch and compile flags (`cake` 107 / 107, `cake_cute`
95 / 95; 3 new modules per backend, 0 removed).
- FlashInfer host tests: 58 passed, 58 skipped (both packages);
FlashInfer GPU tests (both packages): 98 passed, 18 skipped (5:51 on one
B300; the 18 skips are the hand-written-wrapper comparison rows that
need the reference build).
- compute-sanitizer synccheck + memcheck: the gate kernel and the three
new `_rg_rauto` finalize forms 0 errors; whole gated 12-launch chain
(both backends) 0 errors; the exported row-group e2e slice + sanitizer
in the export step: passed, same error class as the reference, sanitizer
`ERROR SUMMARY: 0 errors`.
- CUDA-graph capture / replay + concurrent streams on the gated chain: 9
+ 4 rows × 2 backends, 0 mismatches, the split path witnessed through
the device gate words under graph replay.
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



<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->

## Summary by CodeRabbit

* **New Features**
* Added device-selected GEMM2 finalization for large mixed192 workloads,
choosing between split and dense processing based on runtime workload
characteristics.
* Added configurable gating rules and path overrides, with diagnostics
available outside stream capture.
* Added row-group and rasterization options for dense finalization at
selected tile widths.
* **Documentation**
* Updated the mixed192 execution guide to describe the gated path and
available finalization forms.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Yingyi Huang <averyh@nvidia.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [e44067b](https://github.com/flashinfer-ai/flashinfer/commit/e44067b1fbfce66f547d48c41976b1a57366b8f8)

- **作者**: Haozheng Fan
- **时间**: 2026-10-13T08:02:32Z
- **提交信息**: feat(cake_moe): BF16 and MXFP8 MoE training with recompute, clamped SwiGLU and variable sequence lengths on Blackwell and Rubin (#6053)

Related to #6052. Addresses #6165.

Adds experimental **Cake MoE training** with BF16 or native MXFP8 routed
experts and a BF16 shared expert, for Blackwell (`sm_100a`, `sm_103a`)
and Rubin (`sm_107a`). It includes:
- context-only recompute;
- clamped SwiGLU;
- 256- and 288-expert layouts;
- variable per-rank sequence lengths, including empty ranks.

This update reports two of the four (GPU, precision) combinations
against [MoK #17](https://github.com/cursor/mixture-of-kittens/pull/17):
**GB300 BF16** (EP4–EP64) and **Rubin MXFP8** (EP4; EP8 and EP16
pending). GB300 MXFP8 and Rubin BF16 are implemented and pass the same
correctness checks; their tables will follow.

## API

- **`flashinfer.mok.prepare_mok_bf16(..., clamped_swiglu=False,
fp32_wgrad=False)`** returns the adapter: scheduling, a fused forward, a
fused backward, and a context-only `recompute_forward_context`.
Recompute follows MoK's semantics: dispatch, the gate/up GEMMs and
SwiGLU, without the down projection, combine or output epilogue.
- **MXFP8 routed experts:** pass the routed weights as `(data, scale,
...)` tuples in MoK #17's layout; `quantize_mok_mxfp8_weights` produces
them, bitwise equal to the reference recipe. The fused kernels quantize
activations and gradients, in both operand orientations. The shared
expert, combine and outputs stay BF16.
- **Clamped SwiGLU:** `swiglu_limit` selects `silu(clamp(gate, max=L)) *
clamp(up, -L, L)`, with the matching backward, for routed and shared
experts.
- **FP32 weight-gradient accumulation:** `weight_grad_accumulators` adds
the weight gradients into caller-owned FP32 tensors.
- **Removed:** the saved routed output and the BF16 router-gradient dot
of 072340e2. The score gradient is MoK #17's again.
- **Real rows only:** the shared-expert GEMMs and the epilogues cover
only the real-row prefix, so cost and memory follow the actual tokens,
not the reserved capacity.
- **Capacity:** `create_mok_bf16_workspace` negotiates capacity from
each rank's actual input length, including empty ranks, as before.

The kernels are standalone generated CUDA with per-architecture
variants:
- `csrc/sm_100a/` serves sm_100a and sm_103a;
- `csrc/sm_107a/` uses Rubin's 576-column tensor memory and K=64
block-scaled MMA.

They build through FlashInfer's TVM-FFI JIT, with source hashes
verified. The backend is explicitly selected and JIT-only; it is
excluded from automatic routing and AOT registration.

## Benchmark: Cake adapter vs [MoK
#17](https://github.com/cursor/mixture-of-kittens/pull/17) — GB300 BF16
(EP4–EP64) and Rubin MXFP8 (EP4; EP8/EP16 pending)

The workload is the target geometry of this PR: 16384 source tokens per
rank, method as in the [GB200 benchmark
comment](https://github.com/flashinfer-ai/flashinfer/pull/6053#issuecomment-6026084025).

> **Measured at PR head `ea5cf0a4512d643375977292bf0791e1b9e272c3`.**
> - Timings come from the reference harness on the generator-side
adapter. Its exported kernels are this PR's sources, and the exported
package is bitwise identical to it on all nine outputs in the
cross-check (Validation, below).
> - The MoK baseline is
[cursor/mixture-of-kittens#17](https://github.com/cursor/mixture-of-kittens/pull/17)
at
[`d4a0cb4`](https://github.com/cursor/mixture-of-kittens/commit/d4a0cb4617a08e4657c873e19fd791bbc51e0fcc),
at its defaults.
> - Both run at default (unlocked) clocks and power, on the same GPUs,
interleaved.

### Summary

- **GB300 BF16:** the adapter is 1.12–1.18× faster per step than MoK #17
with uniform routing and 1.13–1.20× with imbalanced routing, at every EP
size from 4 to 64.
  - Forward: 1.19–1.29× faster.
  - Backward: 1.10–1.15× faster.
- **Rubin MXFP8** (EP4; EP8 and EP16 will be added in the next update):
**1.65×** faster with uniform routing and **1.87×** with imbalanced
routing.
  - Forward: 1.48× / 1.68×.
  - Backward: 1.73× / 1.99×.
- **Accuracy:** identical to MoK #17 to three digits for every tensor,
in both precisions.
  - In BF16 both are at or below naive BF16's error against FP32.
  - In MXFP8 both carry the same quantization error.
- **Memory:**
- At MoK #17's 262144-row macrobatch ring, the adapter's context and
peak are **identical to MoK #17's** at every EP size.
- The default 393216-row ring trades 3.0 GiB (BF16) / 1.5 GiB (MXFP8)
more context, and 7.5 / 8.2 GiB more peak, for fewer replays under
imbalanced routing.
- The capacity-sized saved routed output of 072340e2 (up to 58.9 GiB per
layer at EP32/64) is gone. Context no longer depends on the schedule
capacity.
- **Recompute:** forward + context-only replay + backward is 1.19×
faster than MoK #17 (GB300 BF16, EP64) and 1.59× / 1.81× (Rubin MXFP8,
EP4).
- **Unequal per-rank counts:** the adapter is faster on every layout,
including empty ranks and the counts of #6165. Doubling the reserved
capacity costs it 0–2%, against 8.5–9% for MoK #17 at EP64 on GB300.

### Setup

| | |
|---|---|
| Hardware | **GB300 NVL72**, 4 GPUs per node. **Rubin (VR NVL72)**, 4
GPUs per node. Every EP group sits inside one NVLink domain |
| Software | GB300: CUDA 13.3, PyTorch 2.13. Rubin: CUDA 13.x with
sm_107a support |
| Geometry | H 6144, routed and shared I 2048, 256 routed experts,
top-8, one shared expert, FP32 router scores, 16384 source tokens per
rank. MXFP8: routed experts in MXFP8 (E4M3, UE8M0 scale per 32 elements,
MoK #17's recipe); shared expert, combine and outputs BF16 |
| Adapter | GB300 BF16: comm SMs 24/24, minibatch 16384, macrobatch
393216. Rubin MXFP8: comm SMs 64/56, minibatch 32768, macrobatch 393216.
Schedule `3x` (`schedule_capacity_multiplier = 3 / EP`); skew tables use
the no-overflow schedule |
| [MoK #17](https://github.com/cursor/mixture-of-kittens/pull/17) |
[`d4a0cb4`](https://github.com/cursor/mixture-of-kittens/commit/d4a0cb4617a08e4657c873e19fd791bbc51e0fcc)
defaults: comm SMs 40/28, minibatch 4096, macrobatch 262144, no-overflow
schedule (factor EP+1) |
| Inputs | As in the validation driver. x ~ N(0,1), dy ~ N(0,1)/sqrt(H),
weights ~ N(0,1)/sqrt(fan_in), scores (U+0.125) normalized x2.5.
`uniform` = 8 distinct of 256 experts. `imbalanced` = 4 of the first 64
+ 4 of the other 192. MXFP8 weights are quantized from the same BF16
weights |
| Timing | Eager, no CUDA graphs. One step = schedule + forward +
backward, including each implementation's copies and resets. Median of
10 steps on the slowest rank (CUPTI GPU span), after warmup. Each cell
is the median of 2–3 interleaved rounds; differences under about 2% are
within noise |
| Memory | `ctx` = allocator bytes alive after forward. `peak` =
allocator peak over forward+backward above the pre-step baseline,
including weight gradients. Symmetric workspaces (3.4 GiB for both) are
outside the allocator |

### 1. Step time: uniform routing

Each cell is step ms (forward + backward); speedup = MoK #17 / adapter.

| EP | GB300 BF16 MoK #17 | GB300 BF16 adapter | speedup | Rubin MXFP8
MoK #17 | Rubin MXFP8 adapter | speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 4 | 27.9 (10.1 + 17.7) | 24.6 (8.3 + 15.8) | 1.14x | 16.0 (5.4 + 10.5)
| 9.7 (3.7 + 6.1) | **1.65x** |
| 8 | 26.6 (9.5 + 17.1) | 23.6 (7.9 + 15.3) | 1.13x | pending | pending
| pending |
| 16 | 26.1 (9.4 + 16.6) | 23.4 (7.9 + 15.1) | 1.12x | pending | pending
| pending |
| 32 | 26.8 (9.6 + 17.1) | 24.0 (7.9 + 15.6) | 1.12x | – | – | – |
| 64 | 28.3 (10.2 + 18.2) | 24.1 (7.9 + 15.8) | 1.18x | – | – | – |

### 2. Step time: imbalanced routing (hot ranks receive about 2x the
average rows)

| EP | GB300 BF16 MoK #17 | GB300 BF16 adapter | speedup | Rubin MXFP8
MoK #17 | Rubin MXFP8 adapter | speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 4 | 51.7 (18.0 + 33.2) | 43.3 (14.4 + 27.7) | 1.20x | 30.6 (10.6 +
20.0) | 16.4 (6.3 + 10.1) | **1.87x** |
| 8 | 49.9 (17.2 + 32.2) | 43.5 (14.8 + 28.3) | 1.15x | pending |
pending | pending |
| 16 | 50.0 (17.0 + 32.6) | 44.0 (14.4 + 28.2) | 1.14x | pending |
pending | pending |
| 32 | 50.5 (17.0 + 33.6) | 44.8 (14.6 + 29.2) | 1.13x | – | – | – |
| 64 | 52.5 (17.7 + 35.0) | 45.0 (14.6 + 29.8) | 1.17x | – | – | – |

Rubin EP32/EP64 are not measured; no allocation of that size was
available.

### 3. Memory per layer: uniform routing (GiB, `ctx` / `peak`)

| EP | GB300 BF16 MoK #17 (ring 262144) | GB300 BF16 adapter (ring
393216) | GB300 BF16 adapter (ring 262144) | Rubin MXFP8 MoK #17 | Rubin
MXFP8 adapter (393216) | Rubin MXFP8 adapter (262144) |
|---:|---:|---:|---:|---:|---:|---:|
| 4 | 6.4 / 20.5 | 9.4 / 28.0 | 6.4 / 20.5 | 3.5 / 21.6 | 5.0 / 29.8 |
3.5 / 21.6 |
| 8 | 6.4 / 18.3 | 9.4 / 25.8 | 6.4 / 18.3 | pending | pending | pending
|
| 16 | 6.4 / 17.1 | 9.4 / 24.6 | 6.4 / 17.1 | pending | pending |
pending |
| 32 | 6.4 / 16.6 | 9.4 / 24.1 | 6.4 / 16.6 | – | – | – |
| 64 | 6.4 / 16.3 | 9.4 / 23.8 | 6.4 / 16.3 | – | – | – |

- **At the matched 262144 ring the adapter's memory equals MoK #17's.**
In the allocator trace, every ring-sized buffer scales by 262144/393216:
  - forward context: x_routed, gate, up and hidden;
  - backward temporaries: dx_routed, dy_routed, dh, dg and du.
  
  That accounts for the whole difference at the default ring.
- **Latency against memory:**
- With uniform routing (133–141k rows per rank), the ring size does not
change the step (within 1%).
- With imbalanced routing, the most loaded ranks receive 264–272k rows.
At a 262144 ring both implementations then need a second macrobatch. The
adapter's step grows 3–8% (GB300 BF16) to 16% (Rubin MXFP8, EP4: 18.9
against 16.4 ms), and it remains 1.07–1.14× (GB300 BF16, EP4–EP64) and
1.62× (Rubin MXFP8) faster than MoK #17.
- **Before this update** (072340e2 on GB200): `ctx` was 13.9 GiB with
the 3x schedule, and up to 58.9 GiB with the no-overflow schedule at
EP32/64. Context no longer depends on the schedule.

### 4. Accuracy

Global relative L2 against a naive FP32 per-expert reference with TF32
disabled. Naive BF16 is the same computation with BF16 GEMM outputs and
a single rounding of the FP32 SwiGLU.

| | y | d_x | d_scores | routed dW (gate / up / down) | shared dW (gate
/ up / down) |
|---|---|---|---|---|---|
| GB300 BF16 (EP64), naive BF16 | 3.88e-3 | 4.37e-3 | 3.51e-3 | 3.76 /
3.88 / 3.88e-3 | 3.37 / 3.50 / 3.50e-3 |
| GB300 BF16 (EP64), MoK #17 | 3.88e-3 | 3.98e-3 | 3.50e-3 | 3.76 / 3.88
/ 3.88e-3 | 3.37 / 3.50 / 3.50e-3 |
| GB300 BF16 (EP64), adapter | 3.88e-3 | 3.98e-3 | 3.50e-3 | 3.76 / 3.88
/ 3.88e-3 | 3.37 / 3.50 / 3.50e-3 |
| Rubin MXFP8 (EP4), MoK #17 | 4.21e-2 | 4.95e-2 | 7.81e-2 | 7.48 / 7.34
/ 6.60e-2 | 3.37 / 3.46 / 3.48e-3 |
| Rubin MXFP8 (EP4), adapter | 4.21e-2 | 4.95e-2 | 7.81e-2 | 7.48 / 7.34
/ 6.60e-2 | 3.37 / 3.46 / 3.48e-3 |

- **Strict gate (|a-b| ≤ 1e-2 + 1e-2|b|):**
- BF16: the adapter and MoK #17 fail on 0 elements against naive BF16.
Against FP32 they fail on the same elements to within 80 per tensor
(shared gate dW).
- MXFP8: both fail on most routed elements and on y, because of
quantization. The counts agree to within a few hundred elements out of
millions.
- **Bitwise behaviour:**
  - Both implementations are bitwise repeatable.
- Context-only recompute followed by backward is bitwise equal to the
saved-context path.
- BF16 is bitwise equal to MoK #17 except d_x (rel-L2 2.6e-5) and shared
gate dW (5.8e-5).
- **FP32 weight-gradient accumulation:** routed dW error drops 10% and
shared dW error 12–13% (GB300 BF16). In MXFP8, shared dW reaches
2.9–3.1e-3.

### 5. Skew: rank 0 receives s x the average routed rows (no-overflow
schedule for both)

Each cell is step ms / rank-0 allocator peak GiB.

| s | GB300 BF16 MoK #17 (EP64) | GB300 BF16 adapter (EP64) | speedup |
Rubin MXFP8 MoK #17 (EP4) | Rubin MXFP8 adapter (EP4) | speedup |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 28 / 16.3 | 25 / 23.8 | 1.14x | 15.9 / 21.6 | 9.8 / 29.8 | 1.62x |
| 2 | 51 / 16.3 | 45 / 23.8 | 1.14x | 30.8 / 21.6 | 16.5 / 29.8 | 1.87x
|
| 4 | 118 / 16.3 | 95 / 23.8 | 1.24x | 74.9 / 21.6 | 37.4 / 29.8 | 2.00x
|
| 8 | 258 / 16.3 | 230 / 23.8 | 1.12x | pending (EP16) | | |

Memory is flat across s for both implementations. At EP4 a rank can
receive at most 4x the average, so the Rubin s = 8 row comes from EP16.

### 6. Unequal per-rank token counts (capacity 32768 except `fixed`;
step ms)

| layout (mean 16384) | GB300 BF16 MoK (EP64) | GB300 BF16 adapter
(EP64) | Rubin MXFP8 MoK (EP4) | Rubin MXFP8 adapter (EP4) |
|---|---:|---:|---:|---:|
| all 16384, capacity 16384 | 28.3 | 23.8 | 15.9 | 9.8 |
| all 16384, capacity 32768 | 30.7 | 24.3 | 16.2 | 9.8 |
| near (16384 ± 17 x (2r − EP + 1)) | 30.8 | 24.5 | 16.2 | 9.9 |
| random in [8192, 24576] | 32.8 | 26.3 | 15.4 | 9.8 |
| every fourth rank empty | 31.9 | 25.5 | 16.8 | 10.6 |
| strong (0..32768) | 33.7 | 28.4 | 17.9 | 12.1 |
| #6165 counts (8191, 16172, 16231, 32767) | – | – | 19.4 | 12.7 |

Reserving 2x capacity at the same real tokens costs the adapter 0–2%,
against 1.4–9.1% for MoK #17.

### 7. Recompute under activation checkpointing

Forward replay cost when a checkpointed layer is recomputed before its
backward, in ms, with the ratio to that implementation's forward:

| | GB300 BF16 EP64 uniform | GB300 BF16 EP64 8x skew | Rubin MXFP8 EP4
uniform | Rubin MXFP8 EP4 imbalanced | Rubin MXFP8 EP16 8x skew |
|---|---:|---:|---:|---:|---:|
| [MoK #17](https://github.com/cursor/mixture-of-kittens/pull/17)
`recompute_forward_context` | 5.3 (0.52x) | 9.8 (0.16x) | 3.9 (0.71x) |
7.0 (0.66x) | pending |
| adapter `recompute_forward_context` | 4.7 (0.59x) | 13.1 (0.21x) | 2.7
(0.74x) | 4.5 (0.71x) | pending |

Per-layer forward + replay + backward:

| | GB300 BF16 EP64 uniform | GB300 BF16 EP64 imbalanced | GB300 BF16
EP64 8x skew | Rubin MXFP8 EP4 uniform | Rubin MXFP8 EP4 imbalanced |
|---|---:|---:|---:|---:|---:|
| MoK #17 | 34.0 | 63.5 | 270.6 | 19.8 | 37.6 |
| adapter | 28.6 | 53.3 | 241.5 | 12.4 | 20.8 |
| speedup | 1.19x | 1.19x | 1.12x | 1.59x | 1.81x |

With 8x skew, rank 0 receives 1,048,832 rows. Both implementations'
context-only replay rebuilds only the resident first macrobatch: 262144
rows for MoK #17 and 393216 rows for the adapter's default ring. The
adapter's replay is therefore longer in that column even though it is
about 10% faster per replayed row (33.4 against 37.3 ns).

### 8. GLM-5.3-Flash (H 4096, I 2048, 288 experts, top-8, SwiGLU limit
10)

GB300 BF16; each cell is iteration ms (forward + backward):

| EP | routing | MoK #17 | adapter | speedup |
|---:|---|---:|---:|---:|
| 8 | uniform | 18.9 (7.0 + 12.2) | 16.7 (5.8 + 10.8) | 1.13x |
| 8 | imbalanced | 35.3 (12.4 + 23.0) | 29.9 (10.2 + 19.7) | 1.18x |
| 32 | uniform | 19.1 (7.0 + 12.3) | 16.9 (5.8 + 11.1) | 1.13x |
| 32 | imbalanced | 35.0 (12.2 + 22.9) | 31.2 (10.3 + 20.5) | 1.12x |

- **Bitwise equality:** all nine tensors are bitwise equal to MoK #17 at
EP8 and EP32, including clamped-SwiGLU recompute.
- **Strict gate against naive BF16:** both implementations fail on the
same d_scores and gate-dW elements.

## Validation

Validated on GB300 (sm_103a) and Rubin (sm_107a). sm_100a sources are
compiled, but not run on hardware here.

- **Sources:**
- Regenerating the generated CUDA on each architecture reproduces the
committed files byte for byte, all 48 roles.
- `sources.json` hashes verify. The changed-file public-material scan
and pre-commit (ruff, mypy) pass.
- **Single-GPU:** `test_mok_bf16.py` 25/25 and `test_mok_mxfp8.py` 25/25
on both architectures.
- The MXFP8 tests check forward and backward against a
quantization-aware reference.
- They check shared-expert dW against a BF16 shared-MLP reference,
including FP32 weight-gradient accumulation from nonzero accumulators.
  - Recompute is checked against the saved context, bitwise.
- **EP4 distributed, on both architectures:** the toy, unequal-length,
capacity and tolerance tests pass, as does
`test_mok_training_distributed.py`, which covers:
  - BF16 clamped;
  - BF16 recompute;
  - BF16 and MXFP8 FP32 weight-gradient accumulation;
  - MXFP8;
  - MXFP8 clamped + recompute.
- **EP8 across two nodes, GB300, GLM-5.3-Flash (288 experts, 36 per
rank):** the feature test passes, as does a full-scale run with clamp 10
and unequal counts.
- **Cross-check against the reference adapter used for the timings
above:** all nine outputs are bitwise identical on every rank for BF16,
BF16 clamped + recompute, BF16 FP32-wgrad, MXFP8, MXFP8 FP32-wgrad and
MXFP8 clamped + recompute, on both architectures.
- **Score gradient:** it follows MoK #17's semantics (`dot(d_hidden,
hidden) / score`).
- Isolated elements can fail the strict BF16 gate at full scale, as MoK
#17's do.
  - Against FP32 its error is unchanged.

```experimental-tests
tests/experimental/test_mok_bf16.py
tests/experimental/test_mok_bf16_distributed.py
tests/experimental/test_mok_bf16_unequal.py
tests/experimental/test_mok_bf16_capacity.py
tests/experimental/test_mok_bf16_tolerance.py
tests/experimental/test_mok_mxfp8.py
tests/experimental/test_mok_training_distributed.py
```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Zihao Ye <expye@outlook.com>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 4599
- **最后更新**: 2026-10-13T22:48:15Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34713
- **最后更新**: 2026-10-13T23:45:58Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
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


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 13234
- **最后更新**: 2026-10-13T21:27:13Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Yao Xin, Hong Zhang

## AI分析总结

# DiffSynth-Studio 近期提交分析

## 一、主要更新类型
- **Bug修复**：DeepSpeed 与 gradient checkpointing 的兼容性修复
- **文档更新**：在 README 中新增第三方框架/项目展示
- 整体为小规模、常规迭代型提交，未涉及核心功能新增或重大重构。

## 二、关键变更点与项目方向的关系

1. **DeepSpeed 关键字参数保存（fix/checkpoint）**
   - 修复了在使用 DeepSpeed 训练时，`gradient_checkpoint.py` 中 keyword arguments 未被正确传递/保留的问题。这直接影响大规模扩散模型训练的正确性和稳定性。
   - 该修复属于基础设施层面的鲁棒性改进，与 DiffSynth-Studio 作为多模型统一训练/推理平台的定位高度相关——训练管线的可靠性是其核心卖点。

2. **README 新增 entropack 展示及 VDN 示例**
   - 将 entropack 加入 "Innovative Achievements" 板块，说明项目正在积极追踪和整合社区中的创新生态。
   - 新增 VDN（Value-Decomposition Networks）示例，可能指向多智能体/强化学习与扩散模型结合的新探索方向。

## 三、对项目的影响和潜在意义

- **稳定性提升**：DeepSpeed 修复降低了用户在大模型训练场景下遇到的隐蔽 bug 风险，有助于减少 issue 反馈，提升社区口碑。
- **生态建设**：README 更新虽不改代码，但体现了项目对社区贡献者的认可机制，有助于吸引第三方开发者接入 DiffSynth 生态。
- **探索新方向**：VDN 示例的加入暗示项目可能在探索多智能体协作或 RLHF 类的扩散模型训练范式，值得持续关注。

## 四、值得关注的技术点

- **DeepSpeed + Gradient Checkpointing 的交互**：keyword arguments 在 checkpoint 函数中被意外丢弃是 PyTorch 生态中常见但隐蔽的 bug 模式，修复涉及对 autograd checkpoint 内部机制的理解。
- **VDN 示例**：Value-Decomposition Networks 传统上用于多智能体强化学习；出现在扩散模型项目中可能意味着 DiffSynth 在探索将分布式价值分解思想引入并行生成或多步去噪的优化。

## 五、基于项目背景的综合评估

DiffSynth-Studio 是 ModelScope 生态下的统一扩散模型训练/推理框架，支持多模态（图像、视频等）生成任务。本次两笔提交虽然体量小，但反映了项目的健康维护状态：

- **修复类提交**确保了其作为"生产可用"训练框架的可靠性承诺，这在与 HuggingFace Diffusers 等竞品的差异化竞争中至关重要。
- **文档/示例类提交**体现了项目持续扩展技术影响力和社区生态的策略，特别是通过引入跨领域（RL/多智能体）的创新示例来拓展应用场景。

总体而言，这些提交属于常规维护周期内的低风险更新，不会改变项目路线图，但对用户实际使用体验和社区活跃度有正向贡献。建议用户在升级后验证 DeepSpeed 训练流程的兼容性。

## 详细提交记录

### [cf6d843](https://github.com/modelscope/DiffSynth-Studio/commit/cf6d843e27eba3f761ab0df84e7883c0413f062f)

- **作者**: Yao Xin
- **时间**: 2026-10-13T09:20:39Z
- **提交信息**: fix(checkpoint): preserve keyword arguments with DeepSpeed (#1699)

* fix(checkpoint): preserve keyword arguments with DeepSpeed

* Update gradient_checkpoint.py

* chore: remove added source file headers

### [459629d](https://github.com/modelscope/DiffSynth-Studio/commit/459629d5691877d98432381e4416e19ecd3ec277)

- **作者**: Hong Zhang
- **时间**: 2026-10-13T08:45:02Z
- **提交信息**: add entropack in Innovative Achievements & add vdn example (#1746)

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 37099
- **最后更新**: 2026-10-14T01:10:05Z

## 提交统计

- **昨日提交总数**: 47
- **提交者数量**: 31
- **主要提交者**: Po-Han Huang (NVIDIA), Zhaoyi Li, amote-i

## AI分析总结

# SGLang 昨日提交分析（47 条）

## 1. 主要更新类型
- **性能优化**（约 30%）：CUDA Graph 捕获、FlashInfer 启动自调优、fast-math JIT 激活、GDN 卷积网格紧凑化、LoRA fused kernel 优化等
- **功能新增**（约 25%）：DSA 稀疏 Prefill、HiSparse 投机解码、Aaronson-Gumbel 文本水印、top logprobs base64 返回、LoRA 支持新模型家族
- **Bug 修复**（约 20%）：OpenAI 兼容层多处修复（tool_calls 缺省、时间戳稳定性、缓存统计）、多模态灰度图转 RGB、CPython fork 死锁规避
- **重构与基础设施**：Rust 前端持续演进、HiCache 生命周期管线化、gRPC 绑定升级、CI 矩阵调整

## 2. 关键变更点与项目方向的关系
- **新硬件/新模型深度适配是核心主线**：DeepSeek-V4.1 的 SWA bounded replay、DP attention、零行批次跳过，GLM-5.2/5.3 的 DSA Indexer 回退与 DCP 解码上下文并行，均服务于 SGLang "多模型、多硬件高效推理" 的定位。AMD 分支专门为 kimik26 和 glm52 的 2p1d-ep16 场景启用 decode CUDA Graph，说明大 MoE 部署性能是当前重点。
- **分层缓存（HiCache）持续深化**：多条提交围绕 buffer 模式预取管线化、块组池命中、SWA 回收配额、DSA index-K 剔除展开，标志着 HiCache 从功能可用走向生产级精细调优。
- **Rust 前端进入可用化阶段**：支持任意模型名路由、多模态模型前置校验、embedding 包装 HTTP 应用，表明 Python 前端之外的高性能 Rust 服务层正在成熟。
- **多模态与扩散模型扩展**：ComfyUI 集成 Qwen-Image 2.1、MiniMax H3 Ref2VA 引用图缩放、NemotronH Omni 修复，印证 README 中"多模模态模型推理"的多模态方向。

## 3. 对项目的影响与潜在意义
- DeepSeek-V4.1 与 GLM-5.x 系列的大量优化会显著提升这两个旗舰国产模型在 SGLang 上的部署吞吐，增强其作为首选推理引擎的竞争力。
- 投机解码 + KV cache 交换（HiSparse）与 DCP 并行的结合，为长上下文高负载场景提供了新的可扩展性路径。
- OpenAI 兼容层的系列小修复提升了 API 语义正确性，降低第三方客户端接入摩擦。
- 注意到多条提交由 Claude/GPT 系列 AI 代理联合署名，反映出项目已大规模采用 AI 辅助开发流程。

## 4. 值得关注的技术点
- **0-row/fully-masked 批次的短路优化**：DP-idle 批次跳过 mHC 融合、滑动窗口注意力跳过全掩码 KV tile，是 DP + 混合注意力架构下容易被忽视的浪费点。
- **CUDA IPC 池化 GPU embedding 传递**：用于评分场景的堆叠 embedding 覆盖，对多进程协作的显存零拷贝是通用模式。
- **Q8KV8 FP8 稀疏 Prefill + BF16 KV Cache**（GLM-5.3-Flash）：量化与稀疏注意力的组合方案，值得后续性能对比关注。
- **top logprobs 以扁平 base64 数组返回**：减少 JSON 开销，是高吞吐 logprob 场景的合理设计。
- **优先级限制在 int64 范围内**（radix cache）：暴露了此前可能存在的数值溢出隐患，修复具有防御性价值。

## 5. 对项目发展的总体影响
基于 README 中"SGLang 专注 LLM 与多模态模型快速推理"的目标，这批提交体现了三条发展脉络：一是以 DeepSeek-V4.1、GLM-5.x 为代表的旗舰模型持续吃透底层硬件特性（CUDA Graph、DP/DCP、稀疏注意力）；二是 HiCache 分层缓存与 PD 分离架构向生产级稳健性演进；三是 Rust 服务层与 OpenAI 兼容性打磨，拓宽部署与集成场景。整体上，项目正从"功能覆盖"阶段迈向"旗舰模型极致性能 + 生产可靠性"的深耕阶段。

## 详细提交记录

### [684fea8](https://github.com/sgl-project/sglang/commit/684fea8af3b11a5b51ec9966c02959a32ad3421c)

- **作者**: shyeh25
- **时间**: 2026-10-13T23:36:15Z
- **提交信息**: [DSV4.1] Skip Mega mHC fusion on 0-row (DP-idle) batches (#43993)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [2ebdf93](https://github.com/sgl-project/sglang/commit/2ebdf9360b35208ce39e760c1071188294ad63cf)

- **作者**: Liangsheng Yin
- **时间**: 2026-10-13T23:31:57Z
- **提交信息**: [Fix] Work around a CPython fork deadlock in the CPU preprocess pool (#44143)

### [b3991b5](https://github.com/sgl-project/sglang/commit/b3991b53dadfb93677d4b8c293b15606ac0cdd30)

- **作者**: Shu Wang
- **时间**: 2026-10-13T23:27:33Z
- **提交信息**: GLM5.2 DSA Indexer Fallback (#32947)

Co-authored-by: Shu Wang <shuw@login-hecate03.hecate.clusters.nvidia.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [5917604](https://github.com/sgl-project/sglang/commit/5917604a95777460b8c7ba4b95f5b49e15e870c7)

- **作者**: Khoa Pham
- **时间**: 2026-10-13T23:10:57Z
- **提交信息**: [DSV4.1] Support decoder SWA bounded replay with CUDA DP attention (#43812)

### [a832609](https://github.com/sgl-project/sglang/commit/a832609b9276ad8dcab0d43b01622b32e84cadf2)

- **作者**: HEJIAN SANG
- **时间**: 2026-10-13T22:58:31Z
- **提交信息**: [Feature] Return output top logprobs as flat base64 arrays on request (#42890)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [baa632b](https://github.com/sgl-project/sglang/commit/baa632b04970742e7622afe308f270c86720de84)

- **作者**: Chuanrui Zhu
- **时间**: 2026-10-13T22:46:50Z
- **提交信息**: [Score] Send stacked GPU embedding overrides through a CUDA IPC pool (#39730)

Co-authored-by: Sundara Raman Ramachandran <sundar24295@gmail.com>
Co-authored-by: hnyls2002 <lsyincs@gmail.com>

### [08550ac](https://github.com/sgl-project/sglang/commit/08550acc281a12b986018fd62aa74268741f5093)

- **作者**: Andrew Briand
- **时间**: 2026-10-13T22:08:52Z
- **提交信息**: Mark FP32 redux asm volatile (#44137)

### [5569b14](https://github.com/sgl-project/sglang/commit/5569b14d26ffd94a8326889eca15a153e8f1b68b)

- **作者**: Jiaqi Li
- **时间**: 2026-10-13T21:31:45Z
- **提交信息**: fix(benchmark): request token IDs when counting OpenAI prompts (#34511)

Co-authored-by: Zijie Xia <zijie.xia@radixark.ai>

### [2341e64](https://github.com/sgl-project/sglang/commit/2341e647d36f7e3b588b9711012faf5236bf228b)

- **作者**: Yizheng Jiao
- **时间**: 2026-10-13T20:55:09Z
- **提交信息**: [DeepSeek-V4.1] Run decoder SWA bounded replay inside the breakable prefill CUDA graph (#43736)

### [79af3df](https://github.com/sgl-project/sglang/commit/79af3df346197b24ff3f1334262ee7d769df8c62)

- **作者**: Kan Wu
- **时间**: 2026-10-13T20:46:15Z
- **提交信息**: [gRPC] Move runtime.v1 bindings to tonic 0.14, report OpenAI status codes, return text on request (#42673)

Co-authored-by: Kan Wu <kan.wu@radixark.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [18210ed](https://github.com/sgl-project/sglang/commit/18210ed849f2146c821c164c09bfb6bdfc3ddfc9)

- **作者**: huangtingwei
- **时间**: 2026-10-13T20:38:31Z
- **提交信息**: [HiSparse] Add speculative decoding support with multi-step KV cache swapping (#37771)

### [7dc2930](https://github.com/sgl-project/sglang/commit/7dc2930585782c09630d617a510bec08c1724845)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-13T19:47:50Z
- **提交信息**: [Feature] Add Aaronson-Gumbel text watermarking (#37577)

Co-authored-by: Nihar Patel <nihpat95@gmail.com>

### [5eda6b7](https://github.com/sgl-project/sglang/commit/5eda6b7e674458c0c01f93801012b6ff6c15064e)

- **作者**: Xinyuan Tong
- **时间**: 2026-10-13T19:04:47Z
- **提交信息**: docs: add MiniCPM-V 4.7 cookbook (#43829)

### [ce5352a](https://github.com/sgl-project/sglang/commit/ce5352a81473ce9b159ec19eeac9a852e773379d)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:58:57Z
- **提交信息**: [Rust] Serve any `model` name on the OpenAI chat and completions routes (#43923)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [01f3ed1](https://github.com/sgl-project/sglang/commit/01f3ed18a5f330885cf69a69f56f11f244defc4e)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:58:24Z
- **提交信息**: [unified memory pool] Prefer SWA reclaim quotas with a HiCache storage backend or on PD decode (#43919)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: ZYHowell <ZYHowell@users.noreply.github.com>

### [7e3da1b](https://github.com/sgl-project/sglang/commit/7e3da1b7842d054a12a13c0d9bb53f39d4328a45)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:51:44Z
- **提交信息**: [HiCache] Extract the buffer-mode prefetch and load-back lifecycle into pipeline operations (#43870)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [5bcaf0f](https://github.com/sgl-project/sglang/commit/5bcaf0f8ede9fccbe63ffa1e29f51239e384460a)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:45:52Z
- **提交信息**: [Core] Add request-level customized_info keys and mark Full prefill capture batches (#43772)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: jiayisuse <jiayisuse@users.noreply.github.com>

### [149ef7d](https://github.com/sgl-project/sglang/commit/149ef7d1b780093a1ff3e4cbeea63321198af18d)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:44:43Z
- **提交信息**: [Rust] Let an embedding package wrap the frontend HTTP app (#43924)

Co-authored-by: hanminglu <hanminglu@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [a8381d7](https://github.com/sgl-project/sglang/commit/a8381d73be98bedc79d1a058fdcf3863103769a8)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:39:48Z
- **提交信息**: [HiCache] Block-group pool hits, caller-owned load destinations, allocation-target FULL eviction (#43868)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [8bf145d](https://github.com/sgl-project/sglang/commit/8bf145d119033dfd37c54c19b794b5e60b391fe3)

- **作者**: Khoa Pham
- **时间**: 2026-10-13T18:35:34Z
- **提交信息**: [DCP] Decode context parallelism for DSA (GLM-5.2 / GLM-5.3) with MTP (#43735)

Co-authored-by: vincentzed <207368749+vincentzed@users.noreply.github.com>

### [6ade236](https://github.com/sgl-project/sglang/commit/6ade23696d86855cf69ddb1e2409ec76e141682c)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:33:26Z
- **提交信息**: [Core] Keep request priority within the signed 64-bit range in radix caches (#43920)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: qandrew <qandrew@users.noreply.github.com>

### [7f9f742](https://github.com/sgl-project/sglang/commit/7f9f7425358e1a197c6e6730d5697e74f26bbab3)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:30:43Z
- **提交信息**: [Rust] Refuse an unsupported multimodal model before the Rust listener binds (#43925)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: shodoco <shodoco@users.noreply.github.com>

### [2a8e9db](https://github.com/sgl-project/sglang/commit/2a8e9db3b09f260ce7b381c989063a199303cbb5)

- **作者**: elvischenv
- **时间**: 2026-10-13T18:29:48Z
- **提交信息**: [lora] Support LoRA for the NemotronH_Nano_VL_V2 model family (#39798)

Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>
Co-authored-by: Po-Han Huang <pohanh@nvidia.com>
Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>

### [ff3f8c3](https://github.com/sgl-project/sglang/commit/ff3f8c348c0ec9ad0d2bfe85558403e908f4a172)

- **作者**: metamergebot
- **时间**: 2026-10-13T18:13:01Z
- **提交信息**: [Observability] Report per-request storage prefetch and staging waits in meta_info (#43946)

Co-authored-by: Hanming Lu <69857889+hanming-lu@users.noreply.github.com>
Co-authored-by: xiezhq-hermann <xiezhq-hermann@users.noreply.github.com>

### [e98c6d7](https://github.com/sgl-project/sglang/commit/e98c6d7b251ac79627efe30c41ff56c59106b706)

- **作者**: Rain Jiang
- **时间**: 2026-10-13T18:07:42Z
- **提交信息**: Rainj me/rust bench (#43950)

### [c0584cf](https://github.com/sgl-project/sglang/commit/c0584cf9afefdb4a3004a57af8b1aec501d44a4a)

- **作者**: Kailash Ranganathan
- **时间**: 2026-10-13T17:16:14Z
- **提交信息**: [perf] [multi-lora] remove empty CTAs from fused LoRA expand and add split-K to shrink (#41951)

Co-authored-by: Yanbin Jiang <jybsuper@gmail.com>

### [e9400c5](https://github.com/sgl-project/sglang/commit/e9400c5a8f3a0d0312a37aecef694f5edfd69341)

- **作者**: Zhaoyi Li
- **时间**: 2026-10-13T15:46:53Z
- **提交信息**: [AMD][DI][CI] kimik26 2p1d-ep16: capture CUDA graph on decode (eager decode is slow) (#43985)

### [96f519e](https://github.com/sgl-project/sglang/commit/96f519e4fa6c8e8f92f2b4821599597ad38754bb)

- **作者**: Zhaoyi Li
- **时间**: 2026-10-13T15:45:46Z
- **提交信息**: [AMD][DI][CI] glm52 2p1d-ep16: capture CUDA graph on decode (eager decode is too slow) (#43977)

### [11cd270](https://github.com/sgl-project/sglang/commit/11cd2701a8aad67c31ee2f2489e9c9b74582c8ab)

- **作者**: ai-jz
- **时间**: 2026-10-13T15:29:19Z
- **提交信息**: fix(openai): preserve zero cached tokens when cache reporting is enabled (#43005)

Co-authored-by: ai-jz <ai-jz@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [3f1e185](https://github.com/sgl-project/sglang/commit/3f1e185f6e83ca02ec19498aa2917ccaa0f0fd43)

- **作者**: ai-jz
- **时间**: 2026-10-13T14:43:33Z
- **提交信息**: fix(openai): keep chat stream created timestamp stable (#43026)

Co-authored-by: ai-jz <ai-jz@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <115166877+JustinTong0323@users.noreply.github.com>

### [4c5ed05](https://github.com/sgl-project/sglang/commit/4c5ed0597eefac21948348730e63374dcea4ffbf)

- **作者**: jiaqiang-dot-liu
- **时间**: 2026-10-13T14:40:53Z
- **提交信息**: Skip fully-masked KV tiles in sliding-window extend attention (#39769)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [27b6830](https://github.com/sgl-project/sglang/commit/27b68303d043ddbddf9861c55c26bc8617ea7c35)

- **作者**: ai-jz
- **时间**: 2026-10-13T12:56:58Z
- **提交信息**: fix(openai): omit absent tool_calls from chat responses (#43027)

Co-authored-by: ai-jz <ai-jz@users.noreply.github.com>
Co-authored-by: Xinyuan Tong <xinyuantong.cs@gmail.com>

### [8e37c6c](https://github.com/sgl-project/sglang/commit/8e37c6cf372427af12e8ed2c1d56b6196ea681d7)

- **作者**: Po-Han Huang (NVIDIA)
- **时间**: 2026-10-13T12:39:02Z
- **提交信息**: [CI] Run test_pi05_modelopt_fp8_cuda in the kernel-unit lane (#44055)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [5100f8d](https://github.com/sgl-project/sglang/commit/5100f8d11d1d69a702deb9e26da26815423a4453)

- **作者**: Ho-Ren (Jack) Chuang
- **时间**: 2026-10-13T12:30:13Z
- **提交信息**: [DSA] Q8KV8 FP8 Sparse Prefill on GLM-5.3-Flash with BF16 KV Cache (#41790)

Co-authored-by: Xiaoyu Zhang <1182563586@qq.com>

### [29974d5](https://github.com/sgl-project/sglang/commit/29974d543ee874a80975165fe3f61abbf5765c93)

- **作者**: amote-i
- **时间**: 2026-10-13T12:27:26Z
- **提交信息**: [NPU] [DOC] update kimi k3 cookbook and supported features on NPU (#44052)

### [74e0a47](https://github.com/sgl-project/sglang/commit/74e0a47863a2830d017b81ed5d830c8557c30051)

- **作者**: jlqibm
- **时间**: 2026-10-13T12:10:31Z
- **提交信息**: Fix/compressed tensors nvfp4 hopper (#40022)

Co-authored-by: Claude Opus 5 <noreply@anthropic.com>

### [5727f08](https://github.com/sgl-project/sglang/commit/5727f089322cc350c671e341397e58918ec4d00a)

- **作者**: LittleNyima
- **时间**: 2026-10-13T11:48:18Z
- **提交信息**: [diffusion] feat: add configurable reference image resizing for MiniMax H3 Ref2VA (#35839)

Co-authored-by: Mick Qian <mickqian@users.noreply.github.com>

### [85254b5](https://github.com/sgl-project/sglang/commit/85254b5a8fda7436474a3b7f21788fa64bfb78a6)

- **作者**: WenhaoZhang
- **时间**: 2026-10-13T11:47:02Z
- **提交信息**: [diffusion] comfyui: run Qwen-Image 2.1 in SGLD integrated mode (#43581)

### [991a29d](https://github.com/sgl-project/sglang/commit/991a29d0ad2b711bfd32415e7d85c465c431e5ee)

- **作者**: Yunhao Zhou
- **时间**: 2026-10-13T11:03:48Z
- **提交信息**: fix(multimodal): convert grayscale tensors to RGB in PIL backend (#42127)

Co-authored-by: 周云昊 <zhouyunhao@zhouyunhaodeMacBook-Pro.local>

### [4b5b727](https://github.com/sgl-project/sglang/commit/4b5b7271454f4f63334e61759244730f00f4b6d3)

- **作者**: elvischenv
- **时间**: 2026-10-13T10:59:00Z
- **提交信息**: Fix EVS for NemotronH_Omni_Reasoning_V3 (#42933)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [aa15b06](https://github.com/sgl-project/sglang/commit/aa15b06abe654fbfed4aa555b4f9714e9c5ee7d1)

- **作者**: Michael
- **时间**: 2026-10-13T09:45:58Z
- **提交信息**: [AMD][CI] Run test_tracing.py in the extra tier, matching CUDA (#43928)

Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [4e0fa52](https://github.com/sgl-project/sglang/commit/4e0fa525302165845a5b6a0950ea633527487f31)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-10-13T09:45:06Z
- **提交信息**: [Perf] Compact GDN causal-conv grids for skewed prefill batches (#43570)

### [01f6840](https://github.com/sgl-project/sglang/commit/01f684069351bfeeec5d877b7420e55fafb7df84)

- **作者**: Ziang Li
- **时间**: 2026-10-13T09:30:31Z
- **提交信息**: [FlashInfer] Add startup autotuning for MegaMoE (#43789)

### [195cb7a](https://github.com/sgl-project/sglang/commit/195cb7afb49f61e6d2daa58f1927fe8d9debb22c)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-10-13T09:26:50Z
- **提交信息**: [CI] Use sgl-eval for GLM-5.3-Flash GSM8K tests (#43975)

Co-authored-by: Mohammad Angkad <mohammad.angkad@radixark.ai>

### [e0c957e](https://github.com/sgl-project/sglang/commit/e0c957e22259cef81587b26d0a9a15ca630dcadf)

- **作者**: Shu Wang
- **时间**: 2026-10-13T09:07:54Z
- **提交信息**: [HiCache][PD] Allow DSA index-K elision under HiCache and disaggregation (#41769)

Co-authored-by: Anish Shanbhag <ashanbhag@nvidia.com>

### [27be99a](https://github.com/sgl-project/sglang/commit/27be99ae73a4035587ae91cfa851b4928ba48b1f)

- **作者**: Shu Wang
- **时间**: 2026-10-13T09:00:24Z
- **提交信息**: [NVIDIA][MegaMoE] Fix the default spec decoding moe backend when the target model uses flashinfer megamoe (#40772)

Co-authored-by: Po-Han Huang (NVIDIA) <53919306+nvpohanh@users.noreply.github.com>

### [7ff3a11](https://github.com/sgl-project/sglang/commit/7ff3a112846a3fcc12a27bba09d644885a226e4d)

- **作者**: Chunan Zeng
- **时间**: 2026-10-13T07:18:05Z
- **提交信息**: [Perf] Enable fast-math for JIT activations on Blackwell (#43236)

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1291
- **最后更新**: 2026-10-13T09:34:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: Windyskr, chengyaoxue64-lab

## AI分析总结

## 昨日提交分析总结（vipshop/cache-dit）

### 1. 主要更新类型
两次提交均为 **Bug 修复**，无新功能或重构，属于稳定性与兼容性维护。

### 2. 关键变更点与项目方向的关系
- **量化修复（#1118）**：修复 torchao int8 量化在 Ampere GPU（A100/A800）和 torchao 0.18 下完全不可用的问题。原因有二：一是 `QuantizeAOContext` 作为默认参数在模块导入时就断言需要 SM89+ 的 FP8 支持，导致 Ampere 甚至纯 CPU 环境导入即失败；二是 int8 配置使用了 tuple 形式的 granularity，与 torchao 0.18 仅接受 `Granularity` 或二元素 list 的接口不兼容。修复将 `quant_ctx` 改为必填参数（通过已有的 `functools.partial` 调用路径传递），并统一传入单一 granularity。
- **缓存修复（#1114）**：修复 DiT 推理缓存中连续命中统计（streak）在计算步之后未正确重置的问题，将 streak 重置逻辑提前到每步评估前，并按时间步应用 DBPrune 的 streak 上限，同时简化了命中计数逻辑。

### 3. 对项目的影响
- 量化修复显著**扩大了硬件兼容范围**：此前 int8/int4 量化在非 Ada 架构 GPU 上全部失效，如今 Ampere 用户（大模型推理场景中非常普遍）和 CPU-only 环境可以正常使用量化功能。
- 缓存修复提升了 **cache 复用判定的正确性**，直接影响推理加速效果和 DBPrune 剪枝策略的有效性，回归测试覆盖了 warmup、动态计算掩码、CFG 两种顺序等复杂场景。

### 4. 值得关注的技术点
- **Python 可变默认参数陷阱的变体**：默认参数在模块导入时求值，导致设备断言提前触发——这是一个典型的导入期副作用问题，修复思路（改为必填参数）干净且低风险。
- **torchao API 兼容性**：granularity 参数在 0.17 与 0.18 间的类型要求差异，说明对上游库版本需有明确测试矩阵。
- 测试策略得当：导入级测试用伪造设备能力 `(8,0)`，量化测试对照 bf16 输出验证数值正确性。

### 5. 对项目发展的意义
cache-dit 的定位是 PyTorch 原生的 DiT 推理引擎，核心卖点正是 README 强调的 Cache、并行、量化与 CPU Offload。这两个修复分别保障了**量化**（int8 在主流数据中心 GPU 上可用）和**缓存**（streak 统计正确才能量化 cache 命中率、驱动剪枝决策）两大核心能力的可靠性，属于"打地基"式维护，对项目在生产环境的可用性和用户信任度有直接正面影响。

## 详细提交记录

### [1400519](https://github.com/vipshop/cache-dit/commit/14005196725ca5e5f5976fbe24c9f0edb766e929)

- **作者**: Windyskr
- **时间**: 2026-10-13T09:21:28Z
- **提交信息**: fix(quantization): make torchao int8 quantization work on Ampere GPUs and torchao 0.18 (#1118)

* fix(quantization): import the torchao backend on pre-Ada GPUs

_basic_filter_fn and _fallback_filter_fn took
`quant_ctx: QuantizeAOContext = QuantizeAOContext()`. The default is built
when the module is imported, and its default quant_type is float8_per_row,
so __post_init__ asserts an sm89+ GPU at import time. On A100/A800 and other
Ampere GPUs every torchao quant_type, including int8 and int4, failed with
"FP8 requires Ada or newer GPUs (>=sm89), but got (8, 0)"; on CPU-only
hosts the import raised a bare NotImplementedError.

Every caller already passes quant_ctx through functools.partial, so make it
a required argument. Requesting an FP8 type on such GPUs still fails with the
same assertion. Add a test that imports the backend with the device
capability reported as (8, 0).

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* fix(quantization): pass a single granularity to torchao int8 configs

int8_per_row and int8_per_tensor built
Int8DynamicActivationInt8WeightConfig(granularity=(PerRow(), PerRow())).
torchao 0.18 only accepts a Granularity or a two-element list there and
rejects the tuple with "Invalid granularity type", so both quant types
failed on every device. A single granularity applies to both activation and
weight in torchao 0.17 and 0.18, so pass PerRow() / PerTensor().

Add a test that quantizes a small MLP with both types and checks the output
against bf16.

Co-Authored-By: Claude Opus 5.5 <noreply@anthropic.com>

* Update CUDA requirement for TorchAO INT8 tests

Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

---------

Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: DefTruth <31974251+DefTruth@users.noreply.github.com>
Co-authored-by: Copilot Autofix powered by AI <175728472+Copilot@users.noreply.github.com>

### [170e3ab](https://github.com/vipshop/cache-dit/commit/170e3abb179e572fe56ced4786c973e0a35fe4da)

- **作者**: chengyaoxue64-lab
- **时间**: 2026-10-13T08:45:49Z
- **提交信息**: fix(cache): restart continuous cache streak after compute steps (#1114)

* fix(cache): restart continuous cache streak after compute steps

* fix(cache): reset cache streaks before evaluating each step

Reset per-branch streaks when the previous step was not cached.
Remove redundant cap resets and simplify hit counting.

Cover interleaved warmup, dynamic computation masks, both CFG
orders, and repeated cache checks in regression tests.

* fix(cache): apply DBPrune streak limits per timestep

---------

Co-authored-by: xuechengyao <xuechengyao@bytedance.com>
Co-authored-by: NgZiXin <ngzixin02@gmail.com>

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 93734
- **最后更新**: 2026-10-14T01:16:35Z

## 提交统计

- **昨日提交总数**: 61
- **提交者数量**: 49
- **主要提交者**: Aditya Ganesh Kumar, Tim002, Wenbin Chen

## AI分析总结

# vLLM 近期提交综合分析（61 条）

## 一、主要更新类型分布
性能优化占比居首，覆盖注意力内核（FA4、CUTLASS MSA、MLA）、量化（FP8 KV Cache、W4A16、per-token group quant）与 MoE（DeepGEMM 布局直载、MegaMoE、DeepEP-v2 内核融合）等核心路径。Bug 修复次之，涉及 CUDA graph 兼容性、批不变性、多模态预填充切分、结构化输出校验与安全边界。功能新增包括 OpenAI Decisions API MVP、离线固定长度晚分块池化、worker 生命周期钩子、IQ2_XS 等量化格式，以及 Kolibri 1、Qwen4 实验模型接入。另有约 8 条 CI/基础设施更新（测试自动分片、ROCm 镜像与 NIXL/CUDA 版本升级），以及 chat_utils 模块拆分、Transformers AOT 缓存迁移为图缓存（含一次 revert）等重构工作。

## 二、关键变更与项目方向
所有变更紧扣 "Easy, fast, and cheap LLM serving for everyone" 主线。Fast 方面，FA4 在 Blackwell（SM100/SM121）启用稀疏 MQA 解码，GLM5.3 端到端吞吐提升 9.8%，并持续压低 ITL。Cheap 方面，FP8 KV Cache 默认化并下放至 Ampere 架构，配合 W4A16、IQ2 系列与 Q8_0 进一步压缩显存与算力成本。Easy 方面，Transformers 后端接入新模型、OpenAPI schema 暴露、测试自动分片显著降低维护门槛。AMD/ROCm、Intel XPU、NIXL/Mooncake 等多后端提交密集，硬件多元化战略清晰。

## 三、对项目的影响
批不变性正成为质量基线：多条提交修复 `VLLM_BATCH_INVARIANT` 下 GateLinear、wNa16 与压缩张量层的问题，系统性保证分批推理结果一致，对生产环境可复现性至关重要。CUDA graph 覆盖面同步扩大，FA4、DSv4 压缩器等路径均可享受图捕获带来的固定开销降低；下载媒体的字节数与解码量上限、文法中特殊 token 掩码等修复，提升了开放网络环境下的服务健壮性。将 FP8 KV Cache 从 Hopper 下放到 A100/A10 等存量主流硬件，使企业用户无需升级设备即可获得近乎减半的 KV Cache 显存占用与更高批处理并发，扩大了用户覆盖面并巩固其量化技术民主化的领先地位。

## 四、值得关注的技术点
- **MoE 推理栈处于快速演进期**：专家权重直载 DeepGEMM 布局、服务前内核预热，以及 Stable ABI 迁移的一次 revert，提示构建稳定性存在风险，此类迁移需要更审慎的灰度验证。
- **跨架构量化适配**：Ampere 原生不支持 FP8 运算，实现上可能采用 FP8 存储配合 FP16 计算的软件路径，其量化误差控制策略值得持续跟踪；QSA 与主 KV Cache 的联合量化是推理引擎中的关键工程难点。
- **多模态与语音能力扩张**：Nemotron Super 视觉 LayerNorm 修复、Qwen3_ASR 参差音频批次处理、离线晚分块池化等，扩展了 Pooling 与多模态服务边界。
- **cuteDSL FP32 路由器**：NVIDIA 新式 DSL 在 vLLM 内核层的落地尝试。

## 五、总体影响
vLLM 正同时推进三条主线：硬件前沿（Blackwell、ROCm、Intel XPU）的性能挖掘与内核成熟化；生产级可靠性（批不变性、CUDA graph、安全限额、结构化输出校验）的系统性收敛；服务面（新 API、新后端、多模态与语音）的持续铺开。此外，Codex、Claude 等 AI 作为共同署名者的提交频现，表明 AI 辅助开发已深度融入该仓库的工程流程。整体而言，项目在保持高频迭代的同时，正更关注底层一致性与稳定性，为走向更广泛的生产部署奠定基础。

## 详细提交记录

### [f43d7e1](https://github.com/vllm-project/vllm/commit/f43d7e1a0f79eb0a19ca04710503d7b03e8f05a6)

- **作者**: Ryan Rock
- **时间**: 2026-10-13T23:55:19Z
- **提交信息**: [CI][AMD] Gate Aiter MHA FA on dtype (#60679)

Signed-off-by: Ryan Rock <ryan.rock@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [7a9d3db](https://github.com/vllm-project/vllm/commit/7a9d3db896a51dac31d08ae3a8b9eccadbd23689)

- **作者**: josh-schell-amd
- **时间**: 2026-10-13T23:55:09Z
- **提交信息**: [ROCm] Bump ROCm base images to AITER v1.25.0 (#61230)

Signed-off-by: josh schell <josh.schell@amd.com>
Co-authored-by: Micah Williamson <micah.williamson@amd.com>

### [c923e77](https://github.com/vllm-project/vllm/commit/c923e7769b46f2746d1218af1ad1395354c0e509)

- **作者**: Francisco Javier Arceo
- **时间**: 2026-10-13T23:51:08Z
- **提交信息**: [Feat] Add text-only OpenAI Decisions API MVP (#60465)

Signed-off-by: Francisco Javier Arceo <4163062+franciscojavierarceo@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [ad8d39c](https://github.com/vllm-project/vllm/commit/ad8d39cbabfd5349acfa567892742c8661cf7b15)

- **作者**: Chauncey
- **时间**: 2026-10-13T23:49:52Z
- **提交信息**: [Bugfix] Fix DSpark graph-padding handling in the DeepSeek-V4.1 MoE fused top-k (#59166)

Signed-off-by: chaunceyjiang <chaunceyjiang@gmail.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [791f921](https://github.com/vllm-project/vllm/commit/791f92135a1429b3fdacffebf33c67c35188a76e)

- **作者**: Giancarlo Delfin
- **时间**: 2026-10-13T23:22:52Z
- **提交信息**: [Attention] Set ALWAYS cudagraph support for FA4 (#60908)

Signed-off-by: Giancarlo Delfin <gdelfin@inferact.ai>
Co-authored-by: Woosuk Kwon <woosuk@inferact.ai>

### [6a03954](https://github.com/vllm-project/vllm/commit/6a03954b45bfa7cccc0f890b22b46eaf6e249d44)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-13T23:15:30Z
- **提交信息**: [CI] Shard quantization, pooling, multimodal APIs, core kernels and PCP eval automatically (#61477)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [0da66a6](https://github.com/vllm-project/vllm/commit/0da66a6e468653cd8294d5fe16831bb3d7367284)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-13T23:14:18Z
- **提交信息**: [CI] Shard batch invariance, Kimi prefix cache, EP eval and generate APIs automatically (#61474)

Signed-off-by: Kevin Luu <51931015+khluu@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>

### [8082b62](https://github.com/vllm-project/vllm/commit/8082b62f3202539e969b090b53723257ca409607)

- **作者**: Wei Zhao
- **时间**: 2026-10-13T23:13:58Z
- **提交信息**: [Mooncake] Allow Mamba cache mode `none` for capacity-only workers (#60712)

Signed-off-by: Wei Zhao <51183510+wzhao18@users.noreply.github.com>
Signed-off-by: wzhao18 <wzhao18.sz@gmail.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [96fc2da](https://github.com/vllm-project/vllm/commit/96fc2da3159b51edc29b6cca31284db4915291e8)

- **作者**: Tim002
- **时间**: 2026-10-13T22:58:44Z
- **提交信息**: [Perf][Qwen4Exp] Add SM121 TP=2 merged QSA projection plans (#61437)

Signed-off-by: TimRen01 <HolaTim@hotmail.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [78b32b3](https://github.com/vllm-project/vllm/commit/78b32b3fdc47cbf097d982aed012fa9874431836)

- **作者**: Nick Hill
- **时间**: 2026-10-13T22:33:50Z
- **提交信息**: Revert "[Build] DeepGEMM migration to torch Stable ABI (#59482)" (#61510)

Signed-off-by: Nick Hill <nickhill123@gmail.com>
Co-authored-by: Claude Opus 5.5 (1M context) <noreply@anthropic.com>

### [6463d04](https://github.com/vllm-project/vllm/commit/6463d0460133f150298ef19a1b81e088c516a8d4)

- **作者**: Wenbin Chen
- **时间**: 2026-10-13T22:17:14Z
- **提交信息**: Fix write-after-write hazard in xpu KV RoPE triton kernel (#46685)

Signed-off-by: Wenbin Chen <wenbin.chen@intel.com>
Co-authored-by: Misha Goin <mgoin64@gmail.com>

### [698e79f](https://github.com/vllm-project/vllm/commit/698e79f3bdbbe4fe7d6be6d91b358a7f430753ab)

- **作者**: Luca Motz
- **时间**: 2026-10-13T21:17:52Z
- **提交信息**: [Model] Kolibri 1 via the Transformers modeling backend (#60827)

Signed-off-by: Luca Motz <luca.motz@icloud.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [e90158d](https://github.com/vllm-project/vllm/commit/e90158d912107b1ad688ec1d42377bf3e0a04d3b)

- **作者**: Anirudh Ravichandran
- **时间**: 2026-10-13T21:02:17Z
- **提交信息**: [Bugfix][MoE] Clamp BLOCK_SIZE_K to the FP8 quantization block in the batched Triton MoE (#60733)

### [292da21](https://github.com/vllm-project/vllm/commit/292da21f9d887e7cbd511a648971c7627d83c246)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-13T20:40:20Z
- **提交信息**: [HiSparse] Read GPU-resident KV directly for mixed and BF16 prefills (#60417)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c19c263](https://github.com/vllm-project/vllm/commit/c19c263ac8ea3fd6e1d2d689f0e4e725855d89cf)

- **作者**: Wentao Ye
- **时间**: 2026-10-13T20:06:41Z
- **提交信息**: [GLM 5.3 Perf] Handle two elements at the same time for per token group quant, 2.8% E2E ITL improvement (#60927)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [67516b6](https://github.com/vllm-project/vllm/commit/67516b6c42ba6740d6e263893bfa5e42263f3f1a)

- **作者**: Andreas Karatzas
- **时间**: 2026-10-13T19:55:57Z
- **提交信息**: [Bugfix][ROCm][Kimi-K3] Stage fused KDA decode weights after loading (#61207)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [93d0bd9](https://github.com/vllm-project/vllm/commit/93d0bd9d5089c2cfa90d60fea8d990057aefca8d)

- **作者**: djramic
- **时间**: 2026-10-13T19:49:30Z
- **提交信息**: [ROCm][CI] Drop the -inf padding check from the AITER MQA logits test (#61420)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [a31054f](https://github.com/vllm-project/vllm/commit/a31054f5ef5fcdee6d9ef1a04ca73e305fcbe992)

- **作者**: Itay Etelis
- **时间**: 2026-10-13T19:47:41Z
- **提交信息**: [NIXL] Bump CUDA 12 NIXL to 1.5.0 (#60428)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [68fc395](https://github.com/vllm-project/vllm/commit/68fc395554d2ff16f91457bc031334006339f77c)

- **作者**: yifanFengg
- **时间**: 2026-10-13T19:43:54Z
- **提交信息**: [Bugfix] Keep GateLinear batch invariant under VLLM_BATCH_INVARIANT (#59985)

Signed-off-by: yifanFengg <evanfengff@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>
Co-authored-by: Wentao Ye <44945378+yewentao256@users.noreply.github.com>

### [b33cb81](https://github.com/vllm-project/vllm/commit/b33cb8123707977aed605937a772bf0bc5d2a92d)

- **作者**: yifanFengg
- **时间**: 2026-10-13T19:43:40Z
- **提交信息**: [Bugfix] Keep compressed-tensors wNa16 linear layers batch invariant (#60524)

Signed-off-by: yifanFengg <evanfengff@gmail.com>
Co-authored-by: Claude Fable 5.1 <noreply@anthropic.com>

### [2f18d13](https://github.com/vllm-project/vllm/commit/2f18d13cf083c4db8a6d140d8475fbfcffc084fd)

- **作者**: Wentao Ye
- **时间**: 2026-10-13T19:29:17Z
- **提交信息**: [GLM5.3 Perf] Enable fp8 kv cache for GLM5.3 Flash by default, 9.8% E2E Throughput Improvement (#61228)

Signed-off-by: yewentao256 <zhyanwentao@126.com>

### [483e0c2](https://github.com/vllm-project/vllm/commit/483e0c24c757094df710fc3da3170a5f2ebf0b8d)

- **作者**: Itay Etelis
- **时间**: 2026-10-13T19:18:56Z
- **提交信息**: [KV Offload] Split replicated-layout pre-faulting across workers (#59545)

Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Robert Shaw <114415538+robertgshaw2-redhat@users.noreply.github.com>
Co-authored-by: Codex <noreply@openai.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [c068db0](https://github.com/vllm-project/vllm/commit/c068db0e1d8e302219b9bc4bec72474af2de5f8a)

- **作者**: Taimys
- **时间**: 2026-10-13T19:17:29Z
- **提交信息**: [Bugfix][Compile] Replace Transformers AOT caching with graph caching (#58918)

Signed-off-by: fangyao fan <2281693949@qq.com>
Signed-off-by: Taimys <ffy2281693949@gmail.com>
Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Taimys <ffy2281693949@gmail.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [3f55012](https://github.com/vllm-project/vllm/commit/3f550129e8a3cc93bf33e8e6d304ec9c19d8e415)

- **作者**: Anish Shanbhag
- **时间**: 2026-10-13T19:05:28Z
- **提交信息**: [Perf][Attention][MiniMax-M3] Select CUTLASS MSA by EAGLE3 decode shape (#55838)

Signed-off-by: Anish Shanbhag <ashanbhag@nvidia.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [6d1daa9](https://github.com/vllm-project/vllm/commit/6d1daa9fe53f39a7b494cf6c8e433a73eec78a76)

- **作者**: GuanLuo
- **时间**: 2026-10-13T18:54:06Z
- **提交信息**: [Bugfix][Frontend] Expose completion response schemas in OpenAPI (#60926)

Signed-off-by: Guan Luo <gluo@nvidia.com>
Signed-off-by: sfeng33 <4florafeng@gmail.com>
Co-authored-by: sfeng33 <4florafeng@gmail.com>

### [c5bda65](https://github.com/vllm-project/vllm/commit/c5bda658d20b8fd187cfc8049e964ab39fe2f7f3)

- **作者**: aoshen02
- **时间**: 2026-10-13T18:52:08Z
- **提交信息**: [Model][MoE] Load MegaMoE experts directly into the DeepGEMM layout (#60096)

Signed-off-by: aoshen02 <aoshen@inferact.ai>
Signed-off-by: Aaron Hao <hao-aaron@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Aaron Hao <hao-aaron@users.noreply.github.com>

### [624a5dd](https://github.com/vllm-project/vllm/commit/624a5ddafd96df23fe2b9f6d4b8f52a08b9fe9ea)

- **作者**: Matthew Bonanni
- **时间**: 2026-10-13T17:25:03Z
- **提交信息**: [Attention] Fetch MLA prefill workspace at use instead of init (#60654)

Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [e832223](https://github.com/vllm-project/vllm/commit/e83222396f6c9ceb72f80c0d82782071bbd8317c)

- **作者**: Robert Esclapez
- **时间**: 2026-10-13T17:21:30Z
- **提交信息**: [ROCm][Perf] W4A16: speed up skinny GEMM decode, including speculative batches (#57199)

Signed-off-by: Robert Esclapez Garcia <robert.garcia@amd.com>
Co-authored-by: Claude Opus 4.7 <noreply@anthropic.com>
Co-authored-by: Douglas Lehr <91553416+dllehr-amd@users.noreply.github.com>

### [7fad7db](https://github.com/vllm-project/vllm/commit/7fad7db3309347a9d6288a09ed0993728e474a34)

- **作者**: Roberto L. Castro
- **时间**: 2026-10-13T16:38:46Z
- **提交信息**: [Perf][Feat] Add generic cuteDSL LL FP32 router (GEMM) (#44343)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [6849ca6](https://github.com/vllm-project/vllm/commit/6849ca696ac9fbecec29a8a8c47f6ee18aea1ee9)

- **作者**: Andrii Skliar
- **时间**: 2026-10-13T16:06:33Z
- **提交信息**: [Quantization] Add ModelOpt IQ2_XS, IQ2_XXS, and Q8_0 support via b12x (#59604)

Signed-off-by: Andrii Skliar <askliar@nvidia.com>
Signed-off-by: Luke Alonso <lalonso@gmail.com>
Co-authored-by: Andrii Skliar <askliar@nvidia.com>
Co-authored-by: Luke Alonso <lalonso@gmail.com>

### [ac71b17](https://github.com/vllm-project/vllm/commit/ac71b175172f2c092d7141f41f0777b914788cfb)

- **作者**: Woosuk Kwon
- **时间**: 2026-10-13T15:54:24Z
- **提交信息**: [Model Loader] Keep norm layers neutral under dummy weight init (#61323)

Signed-off-by: Woosuk Kwon <woosuk@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [12b005e](https://github.com/vllm-project/vllm/commit/12b005eefa06f97eeebfae3e14bcac5fa3b81197)

- **作者**: Taksh Kothari
- **时间**: 2026-10-13T15:32:38Z
- **提交信息**: [Bugfix] Don't split a multimodal item that a prefill chunk starts exactly on (#52412)

Signed-off-by: Taksh <takshkothari09@gmail.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [b9b401b](https://github.com/vllm-project/vllm/commit/b9b401b2ef1db3148d480a1520d95c95eff9c528)

- **作者**: Elvir Crnčević
- **时间**: 2026-10-13T15:10:38Z
- **提交信息**: [Kernel] Fuse DeepEP-v2 decode globalize+align into one launch (#53911)

Signed-off-by: Elvir Crncevic <elvircrn@gmail.com>

### [669f85e](https://github.com/vllm-project/vllm/commit/669f85e686ae533a761362c919d213a87e0e807c)

- **作者**: wang.yuqi
- **时间**: 2026-10-13T15:08:07Z
- **提交信息**: [Misc] Break chat_utils into more maintainable modules. (#60972)

Signed-off-by: wang.yuqi <yuqi.wang@daocloud.io>

### [f395a6b](https://github.com/vllm-project/vllm/commit/f395a6b1ad49458ea5b0366805c3814c51d6b02b)

- **作者**: Rishabh Agarwal
- **时间**: 2026-10-13T15:03:48Z
- **提交信息**: [ROCM][Bugfix] Deferring to TRITON_ATTN backend for Prefix lm models instead of ROCM_ATTN and fixed minor bug in Gemma3 Multimodal code (#46754)

Signed-off-by: GodRishUniverse <rishabh.agarwal@amd.com>
Signed-off-by: Rishabh Agarwal <risagarw@amd.com>
Signed-off-by: GodRishUniverse <risagarw@amd.com>

### [f5fefbf](https://github.com/vllm-project/vllm/commit/f5fefbffe51e1cc91e0d6507d272f337473989b3)

- **作者**: Chris Leonard
- **时间**: 2026-10-13T15:01:44Z
- **提交信息**: [Build] DeepGEMM migration to torch Stable ABI (#59482)

Signed-off-by: Chris Leonard <chleonar@redhat.com>
Signed-off-by: Shengqi Chen <harry-chen@outlook.com>
Co-authored-by: Shengqi Chen <harry-chen@outlook.com>

### [61d9c77](https://github.com/vllm-project/vllm/commit/61d9c777bfdef66efbf017c7c363d2bdca5db8ee)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-13T14:42:53Z
- **提交信息**: [CI] Run the Clef pooler test on GPU (#61409)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [de8291e](https://github.com/vllm-project/vllm/commit/de8291e24f1312da0239605e33a89fe9cc901e47)

- **作者**: Dakai An
- **时间**: 2026-10-13T13:51:05Z
- **提交信息**: [Core] Add lifecycle hooks for worker extensions (#59463)

Signed-off-by: Dakai An <dakaian108@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: aoshen02 <aoshen@inferact.ai>

### [0fae39a](https://github.com/vllm-project/vllm/commit/0fae39a0142c5d296f7938fa753e8f00b5d80171)

- **作者**: Thien Tran
- **时间**: 2026-10-13T13:37:10Z
- **提交信息**: [Perf] per_token_group_quant_8bit: multiply by reciprocal instead of dividing per element (#61343)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [31e90ac](https://github.com/vllm-project/vllm/commit/31e90ac3705e7415e4061d72c640c6c01737af15)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-13T13:31:37Z
- **提交信息**: [Attention] Enable FA4 sparse MQA decode on Blackwell (#55866)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Lucas Wilkinson <lwilkins@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Lucas Wilkinson <LucasWilkinson@users.noreply.github.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [0838cd6](https://github.com/vllm-project/vllm/commit/0838cd6593ba751aa215c9ecd44048bb29dcff1b)

- **作者**: Nathan Sala
- **时间**: 2026-10-13T12:42:29Z
- **提交信息**: [Bugfix] Load and apply Nemotron Super final vision LayerNorm (#61401)

Signed-off-by: Shaun Kotek <skotek@nvidia.com>
Co-authored-by: Shaun Kotek - Nvidia <skotek@nvidia.com>

### [7342dc0](https://github.com/vllm-project/vllm/commit/7342dc0317c02af21aa15109f147f98982cb8c4f)

- **作者**: Hexiang Wang
- **时间**: 2026-10-13T12:19:53Z
- **提交信息**: [MoRIIO] Require pending remote prefill for READ cache hits (#60638)

Signed-off-by: whx-sjtu <xiaowang990929@gmail.com>

### [253e02b](https://github.com/vllm-project/vllm/commit/253e02b95e9c9deaebdc507f2eb26b29daf3fdf3)

- **作者**: simon-veitner-redhat
- **时间**: 2026-10-13T12:17:48Z
- **提交信息**: [Perf] Warm up DeepGEMM MegaMoE kernels before serving (#60468)

Signed-off-by: Simon Veitner <sveitner@redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [d9a543c](https://github.com/vllm-project/vllm/commit/d9a543c500e9014045d7ae769df0ca7782e31870)

- **作者**: Aditya Ganesh Kumar
- **时间**: 2026-10-13T12:01:59Z
- **提交信息**: [Bugfix][Frontend] Forward --enable-log-outputs to the Cohere Chat v2 (#61089)

Signed-off-by: Aditya Ganesh Kumar <adty910@gmail.com>

### [818f70c](https://github.com/vllm-project/vllm/commit/818f70c295137ddf9d2ba63262adb6f12e954b58)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-13T11:38:23Z
- **提交信息**: [Bugfix] Mask special added tokens in xgrammar JSON, regex and EBNF grammars (#60749)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Signed-off-by: Artem Perevedentsev <aperevedents@nvidia.com>
Co-authored-by: Claude <noreply@anthropic.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [cd7517f](https://github.com/vllm-project/vllm/commit/cd7517fb17bc26f5e63b348a73cc0dab70be8d48)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-13T11:31:53Z
- **提交信息**: [Bugfix] Fix ReplaySSM ring shape assertion when TP does not divide Mamba2 n_groups (#60704)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [e6e84f3](https://github.com/vllm-project/vllm/commit/e6e84f350c647c6e76dad2e39b08cb85e17f1272)

- **作者**: Linze Shi
- **时间**: 2026-10-13T11:16:21Z
- **提交信息**: [Feature][Pooling] Add offline fixed-length late chunking (#60164)

Signed-off-by: Linze-Shi <linzeshi0@gmail.com>

### [426f3bd](https://github.com/vllm-project/vllm/commit/426f3bd36b941c34ad183e10cf2c30ebd62a4755)

- **作者**: noone-zhhh
- **时间**: 2026-10-13T10:49:39Z
- **提交信息**: [Bugfix][Model][Rust Frontend] Qwen3_ASR: Handle ragged Qwen audio batches from Rust frontend (#60979)

Signed-off-by: zh98 <workallday.zhh@gmail.com>
Co-authored-by: Isotr0py <Isotr0py@outlook.com>

### [54db759](https://github.com/vllm-project/vllm/commit/54db759eea66729faa6d41e8cdaceb02833cef7c)

- **作者**: samayp01
- **时间**: 2026-10-13T10:27:34Z
- **提交信息**: [Bugfix][Structured Output] Reject structural_tag and unhandled specs in backend validation (#58862)

Signed-off-by: Samay <samay.piduru@gmail.com>
Co-authored-by: Artem Perevedentsev <aperevedents@nvidia.com>

### [7173c64](https://github.com/vllm-project/vllm/commit/7173c64e2ec8763c6d8ddd5c3ff9cb6fc92e2da8)

- **作者**: Juan Pérez de Algaba
- **时间**: 2026-10-13T10:17:14Z
- **提交信息**: [Security] Bound decoded and downloaded media per request (#61226)

Signed-off-by: juanpas97 <juan.perezalgaba@gmail.com>
Signed-off-by: Juan Pérez de Algaba <jperezde@redhat.com>
Co-authored-by: OpenAI Codex <codex@openai.com>

### [877f6df](https://github.com/vllm-project/vllm/commit/877f6df889176f056713ac30919153b9dacc0cf1)

- **作者**: JackRao123
- **时间**: 2026-10-13T10:15:11Z
- **提交信息**: [Bugfix][DSv4] Don't bake the C128 compressor skip into CUDA graphs (#59709)

Signed-off-by: Jack Rao <jack.rao@baseten.co>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [c7a305e](https://github.com/vllm-project/vllm/commit/c7a305ec10f3ec06c2784f1258162483c5fc8d73)

- **作者**: sungsoo ha
- **时间**: 2026-10-13T10:09:17Z
- **提交信息**: [Bugfix][Mamba] Store conv_kernel - 1 inputs in Mamba2 prefill checkpoints (#60797)

Signed-off-by: Sungsoo Ha <sungsooh@nvidia.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: tomeras91 <57313761+tomeras91@users.noreply.github.com>

### [206e45d](https://github.com/vllm-project/vllm/commit/206e45d47009447001e9080d430e64c90fba21a6)

- **作者**: Kevin H. Luu
- **时间**: 2026-10-13T09:24:06Z
- **提交信息**: [CI] Shard V1 Attention automatically instead of by fixed pytest shards (#61200)

Signed-off-by: khluu <khluu000@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [656d0d4](https://github.com/vllm-project/vllm/commit/656d0d4506052a23d100c56e148c7b984828d637)

- **作者**: Thien Tran
- **时间**: 2026-10-13T09:01:12Z
- **提交信息**: [Perf] Tune Triton GDN decode tiles on SM100-family GPUs (#61355)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: OpenAI Codex <noreply@openai.com>

### [183625d](https://github.com/vllm-project/vllm/commit/183625d4f9f49968218ffbe43242877ead72d569)

- **作者**: Vadim Gimpelson
- **时间**: 2026-10-13T08:48:13Z
- **提交信息**: [Bugfix] Fall back to auto for unquantized MoE layers when --moe-backend is marlin (#60219)

Signed-off-by: Vadim Gimpelson <vadim.gimpelson@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [6f11c22](https://github.com/vllm-project/vllm/commit/6f11c220b5b0f3b45b2a14c49ebbca2df12d1c80)

- **作者**: Harry Mellor
- **时间**: 2026-10-13T08:41:23Z
- **提交信息**: [Transformers backend] Fuse MoE routers that score after the top-k (#57410)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>
Co-authored-by: Claude Opus 5 (1M context) <noreply@anthropic.com>

### [24aa119](https://github.com/vllm-project/vllm/commit/24aa1191f433638722178fed646f0fd52e96a587)

- **作者**: stefankoncarevic
- **时间**: 2026-10-13T08:35:57Z
- **提交信息**: [ROCm][Bugfix] Run the AITER AR+RMSNorm fallback test on the platform… (#61350)

Signed-off-by: Stefan Koncarevic <stefan.koncarevic@amd.com>
Signed-off-by: Stefan Koncarevic <Stefan.Koncarevic@amd.com>

### [ff30593](https://github.com/vllm-project/vllm/commit/ff305934f1c6f98edf7c499464a3c2be5f6e3f04)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-13T08:15:47Z
- **提交信息**: [Tests][Mamba] Wait for accepted counts in fake MTP proposer (#61342)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>

### [3ad096f](https://github.com/vllm-project/vllm/commit/3ad096faf81b4734ae995aa66f4ca0c904cea978)

- **作者**: zhouyou
- **时间**: 2026-10-13T07:59:48Z
- **提交信息**: [Bugfix][EC Connector] Don't create hash directories on cache-miss lookups in ECExampleConnector (#60826)

Signed-off-by: zhouyou9505 <zhouyou9505@gmail.com>

### [2cc2e68](https://github.com/vllm-project/vllm/commit/2cc2e68d1c5652a5bc7ae10422697308e2193359)

- **作者**: Jiangyun Zhu
- **时间**: 2026-10-13T07:58:59Z
- **提交信息**: [Core][Mamba] Remove leftovers of mamba_cache_mode="all" (#60043)

Signed-off-by: zjy0516 <riverclouds.zhu@qq.com>
Signed-off-by: Jiangyun Zhu <zhujiangyun@inferact.ai>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [bc3ddb1](https://github.com/vllm-project/vllm/commit/bc3ddb198a0d5eb864bf484c4719864b671cc93b)

- **作者**: trienebutdiene
- **时间**: 2026-10-13T07:30:19Z
- **提交信息**: [Model][Qwen4Exp] FP8 QSA main KV cache on Ampere (sm_80, sm_86) (#60602)

Signed-off-by: kimseunghyun <hellonypcteam@gmail.com>
Signed-off-by: kimseunghyun <incongnito12@gmail.com>
Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>
Co-authored-by: kimseunghyun <hellonypcteam@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>
Co-authored-by: Thien Tran <gau.nernst@yahoo.com.sg>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-10-14
**监控日期**: 2026-10-13
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 7156
- **最后更新**: 2026-10-14T01:12:31Z

## 提交统计

- **昨日提交总数**: 19
- **提交者数量**: 14
- **主要提交者**: Hongsheng Liu, lazariv, haic0

## AI分析总结

# vllm-omni 昨日提交分析

## 1. 主要更新类型

| 类型 | 数量 | 占比 |
|------|------|------|
| CI/构建改进 | 5 | 26% |
| Bug修复 | 5 | 26% |
| 模型/功能新增 | 3 | 16% |
| 性能优化 | 2 | 11% |
| 前端/接口 | 2 | 11% |
| 文档/重构 | 2 | 11% |

**特征**：本次提交批次以 **CI稳定性和Bug修复为主**，同时穿插了重要的引擎级性能优化和新模型支持，体现了项目在"高速迭代+夯实质量"两线并行的策略。

---

## 2. 关键变更点及与项目方向的关系

**引擎核心优化**
- **事件驱动编排成为默认**（#8675）：这是最重大的变更之一，将事件驱动的流水线编排设为所有 pipeline 的默认模式，直接契合项目"Fast"的核心目标。
- **减少异步 chunk 快照开销**（#8833）：降低请求处理中的内存/计算开销，提升吞吐。
- **前缀缓存管理器重构**（#8835）：明确了写任务所有权和资源清理边界，为后续缓存策略演进奠定基础。

**多模态能力扩展**
- **ABot-World 实时 AR-Diffusion 支持**（#6392）：扩展了扩散模型+实时语音的融合能力。
- **FLUX.1-dev 文本编码器 FP8 在线量化**（#3997）：降低文生图模型的显存和延迟。
- **MiniMax H3 视频时间线接口**（#8838）：向 `/v1/videos` 端点暴露视频生成时间线信息，完善视频 serving API。

**硬件生态拓展**
- **Qwen3-TTS 和 Audio8 eager 模式支持 Intel XPU**（#8853）：扩展到 Intel 加速器硬件。
- **ROCm 复用未掩码 BF16 AITER MHA 模块**（#8848）、**缩短 YuE2 采样器一致性测试**（#8851）：持续优化 AMD GPU 的支持。

---

## 3. 对项目的影响和潜在意义

- **默认事件驱动编排**标志着引擎架构的一次重要转型，长期来看会简化调度逻辑、降低排队延迟，对实时多模态场景（如语音对话、视频生成）的响应速度有显著提升。
- **前缀缓存重构**解决了潜在的所有权模糊问题，降低了内存泄漏和竞态风险，对生产环境稳定性有直接帮助。
- **硬件适配**（XPU + ROCm）的持续投入，表明项目正积极构建跨厂商硬件生态，降低用户对 NVIDIA 的单一依赖。
- **Qwen3-TTS/Omni 相关 CI 修复**（#8837、#8826）说明 TTS 和 Omni 模型已成为项目的重点测试对象，预示其作为标杆用例的地位日益突出。

---

## 4. 值得关注的技术点

- **AI 辅助开发的规模化应用**：多个提交出现 `Co-authored-by: Cursor` 或 `Claude Opus 5.5` 署名，反映出该项目已深度采用 AI 编码代理参与核心开发流程。
- **实时扩散模型（AR-Diffusion）**：ABot-World 的实现将自回归与扩散模型结合用于实时生成，是多模态 serving 的前沿方向。
- **事件驱动 vs 传统批处理**：这一架构转变在 LLM serving 领域具有示范意义，值得关注其性能对比数据。
- **在线 FP8 量化**：FLUX.1 的文本编码器在线量化展示了"量化即服务"的趋势，用户无需离线预处理即可获得加速。

---

## 5. 对项目发展的综合影响

结合 README 定位——"Easy, fast, and cheap omni-modality model serving for everyone"——本次提交批次在三个维度上直接推动了项目目标：

1. **Fast**：事件驱动编排默认化 + 异步 chunk 开销削减，从架构层面提升性能上限。
2. **Easy**：前缀缓存重构、视频取消清理加固、CI 稳定性提升，降低了运维和调试的复杂度。
3. **Cheap**：FP8 在线量化和 AutoRound 量化修复，帮助用户以更低的硬件成本运行多模态模型。
4. **Omnity**：新增 AR-Diffusion、MiniMax H3 视频接口、XPU/ROCm 适配，持续扩展模态覆盖和硬件兼容范围。

总体而言，这是一个**成熟的项目进入"质量深耕+性能突破"阶段**的典型提交批次，既有架构级重构，也有大量细节修复，体现了团队在功能推进和工程稳定性之间的平衡能力。

## 详细提交记录

### [2d99095](https://github.com/vllm-project/vllm-omni/commit/2d9909525a8a805ed9c3a56a5287a48687654270)

- **作者**: Joshna-Medisetty
- **时间**: 2026-10-13T22:14:14Z
- **提交信息**: Run Qwen3-TTS and Audio8 eager on XPU (#8853)

Signed-off-by: Joshna Medisetty <joshna.medisetty@intel.com>
Co-authored-by: Cursor <cursoragent@cursor.com>

### [fa8b419](https://github.com/vllm-project/vllm-omni/commit/fa8b4199c6cece6f61dc5d8d990817d3555c70bc)

- **作者**: haic0
- **时间**: 2026-10-13T19:06:18Z
- **提交信息**: [CI/Build][ROCm] Shorten YuE2 full-vocabulary sampler agreement (#8851)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [697151e](https://github.com/vllm-project/vllm-omni/commit/697151e71db7b39de364c7b8bf6188a5f8a56035)

- **作者**: lazariv
- **时间**: 2026-10-13T18:55:38Z
- **提交信息**: [Bugfix] Realtime: use response_cancel_not_active for cancels with nothing to cancel (#8840)

Signed-off-by: lazariv <lazariv.taras@gmail.com>

### [9fe5504](https://github.com/vllm-project/vllm-omni/commit/9fe550428dba177cd606c38ec446dbdd3f5a06b8)

- **作者**: Guanzhe Huang
- **时间**: 2026-10-13T18:55:03Z
- **提交信息**: [Quantization] FLUX.1-dev text encoder FP8 online quantization (#3997)

Signed-off-by: guanzheh <masugchds@gmail.com>

### [549965b](https://github.com/vllm-project/vllm-omni/commit/549965b94a1aeb9ace43b4713ccc4871f5bbc0bc)

- **作者**: Yueqian Lin
- **时间**: 2026-10-13T17:56:09Z
- **提交信息**: [Perf][Engine] Make event-driven orchestration the default for all pipelines (#8675)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [e42fc7b](https://github.com/vllm-project/vllm-omni/commit/e42fc7b6a4fdc0b8953c264973781cd40a18aff2)

- **作者**: Hongsheng Liu
- **时间**: 2026-10-13T17:45:48Z
- **提交信息**: [Doc] PR merge loop bible (maintainer ops) (#8897)

Signed-off-by: Hongsheng Liu <liuhongsheng4@huawei.com>

### [4234f95](https://github.com/vllm-project/vllm-omni/commit/4234f951525b7dc5b4f4a3587cf60f992530d439)

- **作者**: haic0
- **时间**: 2026-10-13T17:09:14Z
- **提交信息**: [CI/Build][ROCm] Reuse the unmasked BF16 AITER MHA module (#8848)

Signed-off-by: haic0 <149741444+haic0@users.noreply.github.com>
Signed-off-by: andyluo7 <andy.luo@amd.com>
Co-authored-by: Cursor <cursoragent@cursor.com>
Co-authored-by: andyluo7 <andy.luo@amd.com>

### [37f094a](https://github.com/vllm-project/vllm-omni/commit/37f094a388ba1c79f83c129fda39797c1ebfc2a4)

- **作者**: shykoe
- **时间**: 2026-10-13T15:32:41Z
- **提交信息**: [Frontend] Expose MiniMax H3 timeline guides on /v1/videos (#8838)

Signed-off-by: shykoe <shykoe@gmail.com>
Signed-off-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: princepride <wangzhipeng628@gmail.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [ad38a57](https://github.com/vllm-project/vllm-omni/commit/ad38a575a6f8952aabc2bc88553a601c11fea686)

- **作者**: Zheng Wengang
- **时间**: 2026-10-13T15:15:03Z
- **提交信息**: [Refactor][Core] Refactor the prefix-cache manager/controller boundary to make write-task ownership and resource cleanup explicit (#8835)

Signed-off-by: ZhengWG <zwg0606@gmail.com>

### [296e113](https://github.com/vllm-project/vllm-omni/commit/296e1138cf92843829517a9a42373283807a427c)

- **作者**: To-sang
- **时间**: 2026-10-13T14:39:43Z
- **提交信息**: [Bugfix] Fix AutoRound layer resolution after INC config upgrade (#8870)

Signed-off-by: Taoxy <tibbersnightmares@outlook.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [a1c3348](https://github.com/vllm-project/vllm-omni/commit/a1c334877ac788c9522fb7807976093a2c8cb19a)

- **作者**: psv666
- **时间**: 2026-10-13T12:07:01Z
- **提交信息**: [Core] Reduce async chunk request snapshot overhead (#8833)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [b463516](https://github.com/vllm-project/vllm-omni/commit/b463516ff4cfe6d3c3e46aaad07f58e6ce63ac40)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-13T10:50:49Z
- **提交信息**: [Bugfix] Fix Cosmos3 transfer resize and cropping (#8844)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [b6edd66](https://github.com/vllm-project/vllm-omni/commit/b6edd6698ea60a3c3931008f1887d2b1b97b4d76)

- **作者**: amy-why-3459
- **时间**: 2026-10-13T10:44:37Z
- **提交信息**: [CI/Build] Diagnose cancellation collective worker startup failures (#8861)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [4625c69](https://github.com/vllm-project/vllm-omni/commit/4625c697b06cc820daef7b4e380e901a5053bde2)

- **作者**: amy-why-3459
- **时间**: 2026-10-13T10:44:14Z
- **提交信息**: [CI/Build] Stabilize Qwen3-TTS model setup and 8 kHz ASR validation (#8837)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

### [2ac2cb3](https://github.com/vllm-project/vllm-omni/commit/2ac2cb3ba9816933442cab73b671a9409857a838)

- **作者**: MaciejBalaNV
- **时间**: 2026-10-13T09:52:03Z
- **提交信息**: [Bugfix] Harden video job cancellation and cleanup (#8843)

Signed-off-by: Maciej Bala <mbala@nvidia.com>

### [db92784](https://github.com/vllm-project/vllm-omni/commit/db9278431f00cf4d38c130b87f2d91c92b163872)

- **作者**: psv666
- **时间**: 2026-10-13T08:59:32Z
- **提交信息**: [CI/Build] Pin Qwen3-Omni multi-replica speaker and retire audio baselines (#8826)

Signed-off-by: psv666 <2693925048@qq.com>
Co-authored-by: wangyu <53896905+yenuo26@users.noreply.github.com>

### [2ec5f26](https://github.com/vllm-project/vllm-omni/commit/2ec5f265c69520cdd5e5f0a19db485d38885843e)

- **作者**: psv666
- **时间**: 2026-10-13T07:59:58Z
- **提交信息**: [Frontend][Benchmark] Add Seed-TTS Realtime turn-trigger perf test for Qwen3-Omni (#8060)

Signed-off-by: psv666 <2693925048@qq.com>

### [43226aa](https://github.com/vllm-project/vllm-omni/commit/43226aab9dbc84df6cb674b5c5c43800e6dfff23)

- **作者**: xiangrong zhong
- **时间**: 2026-10-13T07:50:36Z
- **提交信息**: [Bugfix][Diffusion] Preserve client errors across request execution (#8713)

Signed-off-by: zack <huixindaddy@yahoo.com>
Co-authored-by: Claude Opus 5.5 <noreply@anthropic.com>

### [4a910f2](https://github.com/vllm-project/vllm-omni/commit/4a910f2390790034323239d4bccc23bde8c28390)

- **作者**: tsinghua-code
- **时间**: 2026-10-13T07:36:55Z
- **提交信息**: [Model] Add ABot-World realtime AR-Diffusion support (#6392)

Signed-off-by: tsinghua-code <zr-liu25@mails.tsinghua.edu.cn>

---
