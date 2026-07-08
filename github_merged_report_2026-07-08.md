# GitHub Stars 合并报告 - 2026-07-08

**合并日期**: 2026-07-09
**监控日期**: 2026-07-08
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


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [ByteDance-Seed/VeOmni](https://github.com/ByteDance-Seed/VeOmni)

## 仓库信息

- **描述**: VeOmni: Scaling Any Modality Model Training with Model-Centric Distributed Recipe Zoo
- **语言**: Python
- **星标数**: 2071
- **最后更新**: 2026-07-08T19:38:00Z

## 提交统计

- **昨日提交总数**: 2
- **提交者数量**: 2
- **主要提交者**: zhangxin.zzzzz, Coach257

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增**：分布式场景下的每-rank 额外并行（ExtraParallel）切片流式权重加载器。
- **Bug 修复**：FSDP2（全分片数据并行版本2）构建问题修复。
- **性能优化/重构**：MoE（混合专家）中散射索引（scatter-index）计算从两次排序优化为 O(N) 算法。

#### 2. 关键变更点及其与项目方向的关系
- **提交 `380147e`**  
  - 新增 `per-rank ExtraParallel-slice streaming weight loader`，支持在额外并行维度（如模型并行或流水线并行）下，按 rank 流式加载权重。  
  - 修复 FSDP2 构建兼容性问题。  
  - **与项目方向**：VeOmni 致力于“缩放任何模态模型训练”，分布式训练是其核心。该提交增强了模型在复杂并行策略下的权重加载效率与鲁棒性，直接支撑更大规模、更多样化并行配置的训练。

- **提交 `425229c`**  
  - 重构 MoE 路由中的散射索引计算，将复杂度从两次排序（`O(N log N)`）降低至线性时间（`O(N)`）。  
  - **与项目方向**：MoE 是大规模多模态模型常用的稀疏激活架构，该优化可大幅减少训练中路由部分的计算开销，提升整体吞吐，符合项目“高效扩展”的目标。

#### 3. 对项目的影响和潜在意义
- **流式权重加载器**：使跨 rank 的权重分片能够按需流式加载，避免全量加载的内存瓶颈，尤其对超大规模模型（如 >100B 参数）的分布式训练至关重要。
- **FSDP2 修复**：确保与较新 PyTorch 分布式原语的兼容性，维护项目对前沿框架的支持。
- **MoE 散射索引优化**：降低 MoE 层的时间占比，直接加速训练过程，且算法简化易于维护。

#### 4. 值得关注的技术点
- **ExtraParallel-slice**：可能指在数据并行之外（如张量并行、序列并行）的额外并行维度，流式加载需考虑不同 rank 间的权重切片映射。
- **O(N) 散射索引算法**：避免两次排序的常用技巧是用计数排序或哈希表，具体实现值得查阅源码。
- **FSDP2 构建修复**：提示项目活跃跟进 PyTorch 更新，确保与最新分布式 API 兼容。

#### 5. 对项目发展的影响（基于 README 背景）
- 项目愿景是“任何模态模型训练的可扩展配方库”，这些提交直接填充了 **分布式配方** 和 **MoE 性能配方** 的关键模块。
- 流式加载有助于支持更大规模的 checkpoint 管理和动态加载策略，为多模态混合训练（如视频+文本）的灵活调度奠定基础。
- MoE 优化使 VeOmni 在处理专家模型时更具竞争力，吸引使用稀疏模型的研究与工业团队。

## 详细提交记录

### [380147e](https://github.com/ByteDance-Seed/VeOmni/commit/380147eba1bc0d0ca01acf9cde5cd187fcec9c60)

- **作者**: Coach257
- **时间**: 2026-07-08T19:37:52Z
- **提交信息**: [dist] feat: per-rank ExtraParallel-slice streaming weight loader + FSDP2 build fixes (#889)

Co-authored-by: Cursor <cursoragent@cursor.com>

### [425229c](https://github.com/ByteDance-Seed/VeOmni/commit/425229c07d3b4a5003b5a6443dcddd1aff6b19c0)

- **作者**: zhangxin.zzzzz
- **时间**: 2026-07-08T13:38:10Z
- **提交信息**: [ops, perf] refactor: compute MoE scatter-index in O(N) instead of two sorts (#888)

---

<a id="ModelTC-LightX2V"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [ModelTC/LightX2V](https://github.com/ModelTC/LightX2V)

## 仓库信息

- **描述**: Lightweight Image Video Action Generation Inference Framework
- **语言**: Python
- **星标数**: 2477
- **最后更新**: 2026-07-08T12:03:14Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: Shiqiao Gu (谷石桥)

## AI分析总结

好的，根据您提供的项目背景和唯一的提交记录，我为您总结如下：

### 1. 主要更新类型
**功能新增** — 明确增加了对“WAN 14B”模型的训练支持。

### 2. 关键变更点及其与项目整体方向的关系
- **变更点**：在 `LightX2V` 框架中引入了 `wan 14b train` 功能（通过 PR #1211 合并）。
- **与项目方向的关系**：项目定位是“轻量视频生成推理框架”，此前主要聚焦于**推理**。本次更新拓展到**训练**能力，且支持的是14B（140亿参数）量级的大模型，这与“轻量”看似矛盾，实则可能通过优化训练策略（如分布式、混合精度、模型并行等）在保持较高效率的同时支持更大模型，从而提升框架在高质量视频生成任务中的实用性。

### 3. 对项目的影响和潜在意义
- **直接影响**：从纯推理框架向“训练+推理”一体化平台迈进，用户可直接在该框架内完成大规模视频生成模型的训练。
- **潜在意义**：降低用户使用WAN 14B模型的训练门槛，可能吸引更多研究者或开发者基于该框架进行视频生成模型的二次开发或微调，增强社区生态。
- **竞争态势**：相比其他仅支持推理的轻量化框架，此更新提供了更完整的模型生命周期支持，提升了竞争力。

### 4. 值得关注的技术点
- **WAN 14B**：推测“WAN”可能是某种特定视频生成架构或模型系列（如 Video Diffusion Transformer 的一种变体），14B参数规模要求显存和计算资源较高，因此提交中很可能包含了**分布式训练支持**、**激活重计算**、**模型并行**或**梯度累积**等优化技术。
- **训练适配**：在轻量框架中引入大模型训练，需要在代码层面做大量适配（如数据加载、算子优化、断点续训等），这可能是本次提交的核心工作。

### 5. 对项目发展的影响（基于README背景）
- **从推理到训练的演进**：README 明确强调“Light Video Generation **Inference** Framework”，本次更新直接打破了原有边界，使项目进入“训练+推理”双模式阶段，成为更全面的视频生成框架。
- **扩展模型覆盖**：支持14B模型意味着框架的兼容性上限被大幅提高，未来可能继续支持更大规模的模型（如30B、70B），从而覆盖从快速轻量生成到高保真长视频生成的完整光谱。
- **社区与贡献**：PR编号#1211表明项目活跃度较高，持续有外部贡献者参与，有助于框架的快速迭代和生态繁荣。

> **一句话总结**：昨日更新将 LightX2V 从纯推理框架扩展为支持WAN 14B模型训练的多功能视频生成平台，显著提升了框架的适用性和成长上限。

## 详细提交记录

### [90fefe7](https://github.com/ModelTC/LightX2V/commit/90fefe767f3ad3459038e29e2e995e338fc1a27f)

- **作者**: Shiqiao Gu (谷石桥)
- **时间**: 2026-07-08T07:26:01Z
- **提交信息**: support wan 14b train (#1211)

---

<a id="aigc-apps-VideoX-Fun"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [aigc-apps/VideoX-Fun](https://github.com/aigc-apps/VideoX-Fun)

## 仓库信息

- **描述**: 📹 A more flexible framework that can generate videos at any resolution and creates videos from images. 
- **语言**: Python
- **星标数**: 2161
- **最后更新**: 2026-07-08T16:08:27Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="flashinfer-ai-flashinfer"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [flashinfer-ai/flashinfer](https://github.com/flashinfer-ai/flashinfer)

## 仓库信息

- **描述**: FlashInfer: Kernel Library for LLM Serving
- **语言**: Python
- **星标数**: 5925
- **最后更新**: 2026-07-08T19:51:27Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 3
- **主要提交者**: Brayden Zhong, Schwinn Saereesitthipitak, Jiahan Chang (Cyrus)

## AI分析总结

### 昨日更新要点总结

#### 1. 主要更新类型
- **功能新增**（1个）：MoE all-to-all checkpoint恢复支持（#3727）
- **性能优化**（2个）：MXFP8 dense GEMM split-K kernel（#3847）、BF16 GEMM冷L2/CUDA graph优化（#3789）

#### 2. 关键变更点与项目方向的关系
| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| #3727 | MNNVL MoE all-to-all 添加 `checkpoint_prepare()` 和 `checkpoint_restore()`，进程checkpoint/restore时保留虚拟地址并重新映射handle | 增强分布式推理的容错能力，支持长服务场景下MoE路由恢复，直接服务FlashInfer的MoE EP/DEP推理 |
| #3847 | 为SM100 CuTe DSL添加MXFP8 split-K GEMM kernel，M≤32时自动调优split-K {2,4} | 提升低精度GEMM性能，尤其对低M（小batch）推理有显著加速（最高+70%），契合inference场景对低延迟的追求 |
| #3789 | `mm_bf16` API增加冷L2缓存和CUDA graph支持，修复SM100路径 | 优化BF16 GEMM的autotune稳定性和执行效率，补齐对SM100硬件优化支持 |

#### 3. 对项目的影响和潜在意义
- **可靠性提升**：MoE checkpoint恢复功能使得分布式推理服务可在节点故障/restore后保持通信状态，避免重启整个管线，提升生产可用性。
- **性能边界扩展**：MXFP8 split-K kernel使低精度推理在低batch时性能逼近上限，BF16优化则完善了sm100平台上的通用GEMM性能，两者共同缩小推理场景性能差距。
- **架构准备**：MNNVL虚拟地址保留机制为后续对称内存/all-reduce（如#3745）奠定基础，体现项目在multi-node通信上的持续演进。

#### 4. 值得关注的技术点
- **虚拟地址保留与handle重映射**：通过分离虚拟地址和物理handle生命周期，实现checkpoint/restore过程中CUDA资源无损迁移，避免地址泄漏或失效。
- **split-K自动调优**：根据M大小动态选择split-K策略（2、4或不拆分），在性能收益和额外开销间平衡，类似做法可推广到其他精度。
- **冷L2 bench**：引入冷L2缓存和CUDA graph来稳定autotune基准，避免缓存状态对性能评估的干扰，是工程化性能调优的最佳实践。
- **POSIX描述符关闭**：在handle交换路径中关闭exported/duplicated/pidfd描述符，防止资源泄漏。

#### 5. 结合项目背景：这些提交如何推动项目发展
- **FlashInfer定位**是高性能GPU推理内核库，**inference场景**强调低延迟、高吞吐、容错性。昨日更新从三个维度强化了这一定位：
  - **计算性能**：MXFP8 split-K使低精度GEMM在低M时达到更高

## 详细提交记录

### [715a915](https://github.com/flashinfer-ai/flashinfer/commit/715a9157bbb4d32efa8a6cc0de8fc010419e90da)

- **作者**: Schwinn Saereesitthipitak
- **时间**: 2026-07-08T19:31:31Z
- **提交信息**: feat(mnnvl): preserve MoE all-to-all graph VAs across checkpoint restore (#3727)

## Summary

- Preserve the existing MNNVL CUDA virtual-address reservation while
releasing and recreating its physical/imported handles across process
checkpoint/restore.
- Expose the lifecycle only at the owning `MoeAlltoAll` workspace as
`checkpoint_prepare()` and `checkpoint_restore(comm_backend)`.
- Require the restored rank-group backend to preserve the original rank
and size, then remap fresh handles at the existing virtual addresses and
reinitialize the MoE all-to-all workspace.
- Keep handle detach/reattach private.
- Treat repeated calls as successful no-ops once the workspace is
already in the requested state.
- Keep dispatch/combine state in each `_A2AState` and read handle
attachment from the shared `MnnvlMemory.mapped` state.
- Reject data operations while the MNNVL handles are detached.
- Close exported, duplicated, and pidfd descriptors in the POSIX
handle-exchange path.

## Scope

This PR is independent of the symmetric-memory/all-reduce work in #3745.
It covers the MNNVL MoE all-to-all DEP/EP path and does not add retry
semantics or a second public memory-level checkpoint API.

## Usage

```python
moe_alltoall.checkpoint_prepare()
moe_alltoall.checkpoint_restore(comm_backend)
```

Successful transitions are idempotent. A transition that raises is
terminal for that workspace; callers should abort the restored worker
rather than retrying the failed operation.

Both methods are collective: every rank must call them in the same
order, and `comm_backend` must reproduce the original rank and world
size.

## Validation

Rebased onto `flashinfer-ai/main` at
`2b150b39a7554fe73b5e1e8864b9f93030ebe2be`.

- `ruff format --check flashinfer/comm/mnnvl.py
flashinfer/comm/trtllm_moe_alltoall.py`
- `ruff check flashinfer/comm/mnnvl.py
flashinfer/comm/trtllm_moe_alltoall.py`
- `python -m py_compile flashinfer/comm/mnnvl.py
flashinfer/comm/trtllm_moe_alltoall.py`
- `git diff --check`

No GPU/MNNVL runtime test was run in this environment.


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added checkpoint lifecycle APIs for MoE all-to-all:
`checkpoint_prepare()` and `checkpoint_restore(comm_backend)` to support
CUDA checkpoint/restore with correct handle remapping, address
preservation, and metadata refresh.

* **Bug Fixes**
* Improved MNNVL handle lifecycle management during checkpoint
transitions, including safer workspace cleanup and stricter state
handling.
* Enforced fail-fast checks when required handles are not currently
mapped.

* **Documentation**
* Expanded API documentation with collective call ordering, communicator
matching requirements, idempotency behavior, and restart guidance after
exceptions.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: Schwinn Saereesitthipitak <schwinns@nvidia.com>

### [e7f305e](https://github.com/flashinfer-ai/flashinfer/commit/e7f305e6d5b7c90389bc4f6372cec1c4a0303df6)

- **作者**: Jiahan Chang (Cyrus)
- **时间**: 2026-07-08T19:12:36Z
- **提交信息**: [feat] Add cutedsl split K for MXFP8 dense gemm (#3847)

<!-- .github/pull_request_template.md -->

## 📌 Description

- Add a dedicated SM100 CuTe DSL MXFP8 split-K kernel for low-M cutedsl
dense GEMMs.
- Autotune split-K {2, 4} and no split K for M <= 32; larger M keeps the
existing base path.

## 🔍 Related Issues

<!-- Link any related issues here -->

## Perf benchmark
| M | N | K | No split (us) | Split-K (us) | Speedup | Gain |
| ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| 1 | 4608 | 6144 | 8.7376 | 7.4000 | 1.1808x | +18.08% |
| 2 | 4608 | 6144 | 8.7968 | 7.4288 | 1.1841x | +18.41% |
| 4 | 4608 | 6144 | 9.0256 | 7.9008 | 1.1424x | +14.24% |
| 8 | 4608 | 6144 | 9.0288 | 7.7920 | 1.1587x | +15.87% |
| 16 | 4608 | 6144 | 9.1776 | 7.9760 | 1.1507x | +15.07% |
| 32 | 4608 | 6144 | 9.7920 | 9.0160 | 1.0861x | +8.61% |
| 64 | 4608 | 6144 | 10.1888 | 10.2112 | 0.9978x | -0.22% |
| 1 | 2304 | 6144 | 8.2064 | 5.7248 | 1.4335x | +43.35% |
| 2 | 2304 | 6144 | 8.1760 | 5.7088 | 1.4322x | +43.22% |
| 4 | 2304 | 6144 | 8.1936 | 5.7248 | 1.4312x | +43.12% |
| 8 | 2304 | 6144 | 8.2048 | 5.7248 | 1.4332x | +43.32% |
| 16 | 2304 | 6144 | 8.3520 | 6.3152 | 1.3225x | +32.25% |
| 32 | 2304 | 6144 | 8.7840 | 7.5984 | 1.1560x | +15.60% |
| 64 | 2304 | 6144 | 9.4208 | 9.3952 | 1.0027x | +0.27% |
| 1 | 6144 | 4096 | 7.3856 | 7.3264 | 1.0081x | +0.81% |
| 2 | 6144 | 4096 | 7.5088 | 7.3152 | 1.0265x | +2.65% |
| 4 | 6144 | 4096 | 7.7488 | 7.3776 | 1.0503x | +5.03% |
| 8 | 6144 | 4096 | 7.6992 | 7.3344 | 1.0497x | +4.97% |
| 16 | 6144 | 4096 | 7.7616 | 7.7824 | 0.9973x | -0.27% |
| 32 | 6144 | 4096 | 8.0416 | 8.0000 | 1.0052x | +0.52% |
| 64 | 6144 | 4096 | 8.5776 | 8.5648 | 1.0015x | +0.15% |
| 1 | 6144 | 2048 | 5.5504 | 5.3056 | 1.0461x | +4.61% |
| 2 | 6144 | 2048 | 5.5328 | 5.3328 | 1.0375x | +3.75% |
| 4 | 6144 | 2048 | 5.5264 | 5.3120 | 1.0404x | +4.04% |
| 8 | 6144 | 2048 | 5.5632 | 5.3120 | 1.0473x | +4.73% |
| 16 | 6144 | 2048 | 5.5568 | 5.5088 | 1.0087x | +0.87% |
| 32 | 6144 | 2048 | 5.7344 | 5.7216 | 1.0022x | +0.22% |
| 64 | 6144 | 2048 | 6.1152 | 6.0976 | 1.0029x | +0.29% |
| 1 | 6144 | 6144 | 10.0480 | 9.1392 | 1.0994x | +9.94% |
| 2 | 6144 | 6144 | 10.0560 | 9.0656 | 1.1092x | +10.92% |
| 4 | 6144 | 6144 | 9.8688 | 9.0656 | 1.0886x | +8.86% |
| 8 | 6144 | 6144 | 10.0448 | 9.1344 | 1.0997x | +9.97% |
| 16 | 6144 | 6144 | 10.0704 | 9.4784 | 1.0625x | +6.25% |
| 32 | 6144 | 6144 | 10.4416 | 10.2688 | 1.0168x | +1.68% |
| 64 | 6144 | 6144 | 10.8224 | 10.8208 | 1.0001x | +0.01% |
| 1 | 6144 | 3072 | 6.7008 | 6.3360 | 1.0576x | +5.76% |
| 2 | 6144 | 3072 | 6.5536 | 6.1616 | 1.0636x | +6.36% |
| 4 | 6144 | 3072 | 6.6336 | 6.2928 | 1.0542x | +5.42% |
| 8 | 6144 | 3072 | 6.6896 | 6.2976 | 1.0622x | +6.22% |
| 16 | 6144 | 3072 | 6.6784 | 6.5312 | 1.0225x | +2.25% |
| 32 | 6144 | 3072 | 6.7744 | 6.9376 | 0.9765x | -2.35% |
| 64 | 6144 | 3072 | 7.4112 | 7.3856 | 1.0035x | +0.35% |
| 1 | 6144 | 1536 | 4.7024 | 4.3280 | 1.0865x | +8.65% |
| 2 | 6144 | 1536 | 4.6880 | 4.2912 | 1.0925x | +9.25% |
| 4 | 6144 | 1536 | 4.5184 | 4.4704 | 1.0107x | +1.07% |
| 8 | 6144 | 1536 | 4.6816 | 4.2368 | 1.1050x | +10.50% |
| 16 | 6144 | 1536 | 4.7136 | 4.5008 | 1.0473x | +4.73% |
| 32 | 6144 | 1536 | 4.7152 | 4.7072 | 1.0017x | +0.17% |
| 64 | 6144 | 1536 | 5.1072 | 4.8608 | 1.0507x | +5.07% |
| 1 | 6144 | 768 | 3.2128 | 3.2528 | 0.9877x | -1.23% |
| 2 | 6144 | 768 | 3.2512 | 3.2528 | 0.9995x | -0.05% |
| 4 | 6144 | 768 | 3.0736 | 3.1168 | 0.9861x | -1.39% |
| 8 | 6144 | 768 | 3.2112 | 3.1376 | 1.0235x | +2.35% |
| 16 | 6144 | 768 | 3.2592 | 3.2624 | 0.9990x | -0.10% |
| 32 | 6144 | 768 | 3.4368 | 3.0880 | 1.1130x | +11.30% |
| 64 | 6144 | 768 | 3.3920 | 3.2848 | 1.0326x | +3.26% |
| 1 | 5120 | 6144 | 9.1344 | 8.3040 | 1.1000x | +10.00% |
| 2 | 5120 | 6144 | 9.1888 | 8.1216 | 1.1314x | +13.14% |
| 4 | 5120 | 6144 | 9.1920 | 8.2336 | 1.1164x | +11.64% |
| 8 | 5120 | 6144 | 9.1840 | 8.2080 | 1.1189x | +11.89% |
| 16 | 5120 | 6144 | 9.3888 | 8.3872 | 1.1194x | +11.94% |
| 32 | 5120 | 6144 | 10.4016 | 9.4384 | 1.1021x | +10.21% |
| 64 | 5120 | 6144 | 10.4560 | 10.4192 | 1.0035x | +0.35% |
| 1 | 2560 | 6144 | 8.2336 | 5.7312 | 1.4366x | +43.66% |
| 2 | 2560 | 6144 | 8.2272 | 5.5568 | 1.4806x | +48.06% |
| 4 | 2560 | 6144 | 8.2480 | 5.5600 | 1.4835x | +48.35% |
| 8 | 2560 | 6144 | 8.1968 | 5.6544 | 1.4496x | +44.96% |
| 16 | 2560 | 6144 | 8.4016 | 6.5280 | 1.2870x | +28.70% |
| 32 | 2560 | 6144 | 8.8256 | 7.7600 | 1.1373x | +13.73% |
| 64 | 2560 | 6144 | 9.4432 | 9.4112 | 1.0034x | +0.34% |
| 1 | 12288 | 6144 | 14.4272 | 14.3040 | 1.0086x | +0.86% |
| 2 | 12288 | 6144 | 14.4736 | 14.3008 | 1.0121x | +1.21% |
| 4 | 12288 | 6144 | 14.4784 | 14.3360 | 1.0099x | +0.99% |
| 8 | 12288 | 6144 | 14.5328 | 14.5760 | 0.9970x | -0.30% |
| 16 | 12288 | 6144 | 14.7680 | 14.7440 | 1.0016x | +0.16% |
| 32 | 12288 | 6144 | 15.0992 | 14.9440 | 1.0104x | +1.04% |
| 64 | 12288 | 6144 | 15.6064 | 15.5568 | 1.0032x | +0.32% |
| 1 | 6144 | 6144 | 10.0480 | 9.0560 | 1.1095x | +10.95% |
| 2 | 6144 | 6144 | 9.7952 | 9.0688 | 1.0801x | +8.01% |
| 4 | 6144 | 6144 | 9.6576 | 9.0304 | 1.0695x | +6.95% |
| 8 | 6144 | 6144 | 9.8032 | 9.0880 | 1.0787x | +7.87% |
| 16 | 6144 | 6144 | 10.0320 | 9.4496 | 1.0616x | +6.16% |
| 32 | 6144 | 6144 | 10.4144 | 10.2688 | 1.0142x | +1.42% |
| 64 | 6144 | 6144 | 10.8160 | 10.8272 | 0.9990x | -0.10% |
| 1 | 3072 | 6144 | 8.3792 | 6.3072 | 1.3285x | +32.85% |
| 2 | 3072 | 6144 | 8.3840 | 6.3168 | 1.3273x | +32.73% |
| 4 | 3072 | 6144 | 8.5824 | 6.2704 | 1.3687x | +36.87% |
| 8 | 3072 | 6144 | 8.3744 | 6.3360 | 1.3217x | +32.17% |
| 16 | 3072 | 6144 | 8.5680 | 6.9520 | 1.2325x | +23.25% |
| 32 | 3072 | 6144 | 9.0368 | 8.0256 | 1.1260x | +12.60% |
| 64 | 3072 | 6144 | 9.7616 | 9.7648 | 0.9997x | -0.03% |
| 1 | 1536 | 6144 | 7.9904 | 4.7168 | 1.6940x | +69.40% |
| 2 | 1536 | 6144 | 7.8288 | 4.7760 | 1.6392x | +63.92% |
| 4 | 1536 | 6144 | 7.9888 | 4.6912 | 1.7029x | +70.29% |
| 8 | 1536 | 6144 | 7.9712 | 4.8720 | 1.6361x | +63.61% |
| 16 | 1536 | 6144 | 7.9504 | 5.4064 | 1.4706x | +47.06% |
| 32 | 1536 | 6144 | 8.1696 | 7.1600 | 1.1410x | +14.10% |
| 64 | 1536 | 6144 | 8.8224 | 8.8032 | 1.0022x | +0.22% |

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

<!-- Optional: anything you'd like reviewers to focus on, concerns, etc.
-->


<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **New Features**
* Added a new MXFP8 GEMM benchmark entry in the overview documentation.
* Expanded GEMM support to include more efficient split-K execution for
larger workloads.
* Improved backend handling so one MXFP8 tuning path now works
consistently across supported implementations.

* **Bug Fixes**
* Fixed layout selection for certain GEMM paths to better match backend
behavior.
* Improved kernel selection and execution for small and large matrix
shapes, reducing fallback issues.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

---------

Signed-off-by: jiahanc <173873397+jiahanc@users.noreply.github.com>

### [3fd5c55](https://github.com/flashinfer-ai/flashinfer/commit/3fd5c55bc84bc00b27bed5099031fa3aab8a4fb2)

- **作者**: Brayden Zhong
- **时间**: 2026-07-08T14:37:40Z
- **提交信息**: Add cold-L2 and CUDA graph to mm_bf16 API (#3789)

Add cold L2 + CUDA graph, which is needed for autotune stability:

https://github.com/bzhng-development/flashinfer/commit/c76ca31fbfe87ee514bc928c9ebb935c1e7846d9

<img width="2400" height="900" alt="image"
src="https://github.com/user-attachments/assets/afda0689-fcad-4bd3-ac8c-db192fb2e2d0"
/>
<!-- This is an auto-generated comment: release notes by coderabbit.ai
-->
## Summary by CodeRabbit

* **Performance Improvements**
* Improved BF16 GEMM execution on supported SM100 hardware by enabling
optimizations that can reduce overhead and improve cache behavior.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

Co-authored-by: Brayden Zhong <brayden@radixark.ai>

---

<a id="hao-ai-lab-FastVideo"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [hao-ai-lab/FastVideo](https://github.com/hao-ai-lab/FastVideo)

## 仓库信息

- **描述**: A unified inference and post-training framework for accelerated video generation.
- **语言**: Python
- **星标数**: 3811
- **最后更新**: 2026-07-08T11:49:01Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="huggingface-diffusers"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [huggingface/diffusers](https://github.com/huggingface/diffusers)

## 仓库信息

- **描述**: 🤗 Diffusers: State-of-the-art diffusion models for image, video, and audio generation in PyTorch.
- **语言**: Python
- **星标数**: 34021
- **最后更新**: 2026-07-08T22:16:17Z

## 提交统计

- **昨日提交总数**: 3
- **提交者数量**: 2
- **主要提交者**: David El Malih, Sayak Paul

## AI分析总结

好的，我们来分析一下 `huggingface/diffusers` 仓库昨日（基于提供的提交记录推断）的更新。

### 1. 主要更新类型
- **文档更新**：`[208704a]` 改进了 `scheduling_scm.py` 的 docstring。
- **功能废弃与回滚**：`[b3545f9]` 废弃了 `dduf`，但紧接着 `[b8905b9]` 又**立即恢复**了该废弃操作。这属于**紧急撤销**行为，很可能因为废弃决定引发争议或发现不成熟。

### 2. 关键变更点及其与项目整体方向的关系
- **`scheduling_scm.py` 文档改进**：该文件属于调度器（Scheduler）模块，是扩散模型推理的核心组件。改进 docstring 有助于开发者理解调度算法参数，提升库的可维护性与社区贡献体验，符合 HuggingFace 一贯重视文档和易用性的方向。
- **`dduf` 废弃与恢复**：`dduf` 在 Diffusers 上下文中可能指 “Diffusion Dataset Unified Format” 或类似的数据格式工具。废弃它表明团队曾考虑移除该功能以简化核心库、减少维护负担。然而立即回滚说明：要么 `dduf` 仍有较多用户依赖，要么废弃的方案还不够成熟。**这一对提交反映了项目在“精简核心 vs 保持兼容性”之间的权衡**，最终选择了保守路线。

### 3. 对项目的影响和潜在意义
- **文档更新**：低影响，但积极。改善代码可读性，降低新手贡献门槛。
- **dduf 操作**：影响较大。如果废弃生效，使用 `dduf` 加载数据的用户将收到弃用警告，需要迁移代码。回滚则意味着用户无需立即更改，但 `dduf` 未来命运仍存不确定性。**潜在意义**：团队可能外部压力下暂缓了废弃，但长期仍可能寻找替代方案重构数据接口。

### 4. 值得关注的技术点
- **调度器文档**：关注 `scheduling_scm.py` 的具体参数说明，可能涉及新调度算法（如 DPMSolver、LCM）的配置。
- **dduf 的定位**：检查 `dduf` 在 Diffusers 代码库中的引用范围。它是否与 `dataset`、`load_dataset` 等功能深度耦合？废弃它是否意味着 HuggingFace 希望统一使用 `datasets` 库而非自建格式？
- **回滚模式**：`revert` 提交通常意味着决策仓促，后续可能会重新评估并在更合适时机再次废弃。

### 5. 基于项目背景，这些提交如何影响项目发展
- **文档改进**：助力项目标准化，符合 HuggingFace 作为“开源 AI 基建”的角色要求——文档越清晰，生态越稳固。
- **dduf 事件**：体现了成熟开源项目在功能迭代中的谨慎态度。Diffusers 正快速扩张（持续集成新模型和调度器），保留 `dduf` 可避免分裂社区，但核心库体积和复杂度会持续增加。**从发展角度看**，团队可能需要在“推出专用数据工具”与“复用已有生态工具（如 `datasets`）”之间达成共识，本次回滚为这一争议提供了缓冲期。

### 总结
昨日更新以**文档优化**和**一次紧急的功能废弃回滚**为主。最值得关注的是 `dduf` 的废弃-回滚过程，它揭示了项目在维护兼容性与精简架构之间的真实拉扯。整体上，更新偏向保守，稳定性优先，社区反馈在其中起了关键作用。

## 详细提交记录

### [208704a](https://github.com/huggingface/diffusers/commit/208704a27a6f362b67cd1a04fa1db0b98036d26f)

- **作者**: David El Malih
- **时间**: 2026-07-08T16:23:05Z
- **提交信息**: docs: improve docstring scheduling_scm.py (#14136)

Improve docstring scheduling scm

### [b8905b9](https://github.com/huggingface/diffusers/commit/b8905b9b0f01d2df8738ae967d5c02c502f0d3e5)

- **作者**: Sayak Paul
- **时间**: 2026-07-08T07:21:41Z
- **提交信息**: Revert "deprecate dduf."

This reverts commit b3545f9c57969b60a998e077b6f85735cdcb1a6d.

### [b3545f9](https://github.com/huggingface/diffusers/commit/b3545f9c57969b60a998e077b6f85735cdcb1a6d)

- **作者**: Sayak Paul
- **时间**: 2026-07-08T07:20:40Z
- **提交信息**: deprecate dduf.

---

<a id="modelscope-DiffSynth-Engine"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [modelscope/DiffSynth-Engine](https://github.com/modelscope/DiffSynth-Engine)

## 仓库信息

- **描述**: None
- **语言**: Python
- **星标数**: 423
- **最后更新**: 2026-07-03T19:24:31Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="modelscope-DiffSynth-Studio"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [modelscope/DiffSynth-Studio](https://github.com/modelscope/DiffSynth-Studio)

## 仓库信息

- **描述**: Enjoy the magic of Diffusion models!
- **语言**: Python
- **星标数**: 12678
- **最后更新**: 2026-07-08T13:43:07Z

## 提交统计

- **昨日提交总数**: 0

## AI分析总结

昨日无提交

---

<a id="sgl-project-sglang"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [sgl-project/sglang](https://github.com/sgl-project/sglang)

## 仓库信息

- **描述**: SGLang is a high-performance serving framework for large language models and multimodal models.
- **语言**: Python
- **星标数**: 30077
- **最后更新**: 2026-07-08T23:07:19Z

## 提交统计

- **昨日提交总数**: 20
- **提交者数量**: 17
- **主要提交者**: shuwenn, amote-i, Mohammad Miadh Angkad

## AI分析总结

以下是对 `sgl-project/sglang` 仓库昨日（2025-03-12）提交记录的要点总结：

---

### 1

## 详细提交记录

### [cc13e2e](https://github.com/sgl-project/sglang/commit/cc13e2eae75d9725f3176e26a83e011f05fecdd0)

- **作者**: Cheng Wan
- **时间**: 2026-07-08T23:07:08Z
- **提交信息**: [CI] Move piecewise CUDA graph (pcg) tests to nightly (#30563)

Co-authored-by: Claude Opus 4.8 <noreply@anthropic.com>

### [8f93077](https://github.com/sgl-project/sglang/commit/8f9307736ac3a569cb2cec7004c74de79001fa7c)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-08T22:29:53Z
- **提交信息**: [misc] Add CI-only guards for the FutureMap seq_lens relay (#30471)

### [096551e](https://github.com/sgl-project/sglang/commit/096551eed649c21a273d816ecf51ceef346ee9d0)

- **作者**: cctry
- **时间**: 2026-07-08T22:08:22Z
- **提交信息**: Make CUDA graph disabling PD-role-aware (prefill/decode) (#30409)

### [07ef650](https://github.com/sgl-project/sglang/commit/07ef650ef7b066f8bab81d531acb1edc8231902d)

- **作者**: wangjiaxin99
- **时间**: 2026-07-08T21:57:10Z
- **提交信息**: [AMD] Fix GLM-5.2 MTP Quark excludes (#30265)

Co-authored-by: zhaolin <zhaolin@amd.com>
Co-authored-by: Raiden-Makoto <Raiden-Makoto@users.noreply.github.com>
Co-authored-by: HAI <hixiao@gmail.com>

### [cc7d665](https://github.com/sgl-project/sglang/commit/cc7d6659fd68694797892d0d863b2549a5b61b69)

- **作者**: Connor Carpenter
- **时间**: 2026-07-08T21:53:56Z
- **提交信息**: feat(grpc): support disaggregated generation requests (#30440)

Signed-off-by: Connor Carpenter <connorc@nvidia.com>
Co-authored-by: Ishan Dhanani <ishandhanani@gmail.com>

### [ca8f15c](https://github.com/sgl-project/sglang/commit/ca8f15cd70f50e54b45be505be19249980824ff4)

- **作者**: Lianmin Zheng
- **时间**: 2026-07-08T21:34:49Z
- **提交信息**: Fix FlashInfer A2A IMA by DP-synchronizing the decode graph bucket (#30242) (#30450)

### [c55190a](https://github.com/sgl-project/sglang/commit/c55190a63838957822da7483cad5df8f03ab0083)

- **作者**: Michael
- **时间**: 2026-07-08T21:04:23Z
- **提交信息**: [AMD] Register 2 CPU-bound 1-GPU tests (phase_checker, scripted_runtime_core) for AMD PR CI (#30446)

### [10e7f29](https://github.com/sgl-project/sglang/commit/10e7f2925f09e3f70bf2d582a387cba432706025)

- **作者**: Liangsheng Yin
- **时间**: 2026-07-08T20:43:09Z
- **提交信息**: [Fix] Chain the seq_lens publish event records so prebuilt seeding keeps the forward fence (#30435)

### [47a6dfd](https://github.com/sgl-project/sglang/commit/47a6dfd708b5587b7ba487f46150fb029b970634)

- **作者**: Michael
- **时间**: 2026-07-08T20:38:17Z
- **提交信息**: [AMD] Register 3 ROCm-portable JIT kernel tests for AMD CI (#30212)

### [45019b5](https://github.com/sgl-project/sglang/commit/45019b56ce0804f734f7361e182226c0e5445765)

- **作者**: Xinyuan Tong
- **时间**: 2026-07-08T19:19:44Z
- **提交信息**: [Bugfix] Map reasoning_effort=low to Nemotron-3 Super low_effort + warn on unsupported levels (#30463)

Co-authored-by: EazyReal <8047065+EazyReal@users.noreply.github.com>

### [8d2b66f](https://github.com/sgl-project/sglang/commit/8d2b66fd9071f29434f5f0a149be1f6829907c2f)

- **作者**: sonle5
- **时间**: 2026-07-08T17:55:09Z
- **提交信息**: Fix gfx95 bpreshuffle FP8 activation scale layout (#29275)

Co-authored-by: sunxxuns <126995791+sunxxuns@users.noreply.github.com>

### [fc378f8](https://github.com/sgl-project/sglang/commit/fc378f843e259bf8d7a3e922f6291148214dd5e2)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-08T16:30:59Z
- **提交信息**: [AMD] Temporarily reduce AMD scheduled test frequency to save resource (#30534)

### [04e4fad](https://github.com/sgl-project/sglang/commit/04e4fadff3108cd042b6a0cbce8e4c72cfdcc378)

- **作者**: Mohammad Miadh Angkad
- **时间**: 2026-07-08T15:43:45Z
- **提交信息**: Use FP32 logits in MoEGate fallbacks (#30323)

### [b8ca06f](https://github.com/sgl-project/sglang/commit/b8ca06fdad415238959593be5c4ec45e234e04d4)

- **作者**: Xiaoyu Zhang
- **时间**: 2026-07-08T13:23:25Z
- **提交信息**: Fix zero expert routed ids for MoE backends (#30387)

### [108a183](https://github.com/sgl-project/sglang/commit/108a183f6bdd2035e649f6812c17ddb3193ebd65)

- **作者**: shuwenn
- **时间**: 2026-07-08T12:12:52Z
- **提交信息**: [mem_cache][6/N] refactor: move MHA host-pool into pool_host/mha.py (#30249)

### [4c5fe42](https://github.com/sgl-project/sglang/commit/4c5fe42be4c93a77dcf9d1d9a6e1381171fb2f29)

- **作者**: Jimmy Shong
- **时间**: 2026-07-08T11:49:26Z
- **提交信息**: [DSA] Fix IMA in fused top-k v2: write all output slots on tie overflow (#30512)

Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [3d96bb9](https://github.com/sgl-project/sglang/commit/3d96bb97211f7f74fc08c38c124354c404f67abe)

- **作者**: HuangJi
- **时间**: 2026-07-08T11:06:44Z
- **提交信息**: [diffusion] chore: rename lingbot world v2 (#30518)

### [042228a](https://github.com/sgl-project/sglang/commit/042228a1951b2e45e55a0807b5ab5823b1863ea3)

- **作者**: amote-i
- **时间**: 2026-07-08T09:35:06Z
- **提交信息**: [NPU] [DOC] Remove unsupported options of features on Ascend NPU (#30504)

### [96368a5](https://github.com/sgl-project/sglang/commit/96368a5f77bccd6f3560366dcefe809b48731595)

- **作者**: jacky.cheng
- **时间**: 2026-07-08T09:34:20Z
- **提交信息**: [AMD] Fuse shared-expert sigmoid + bf16->fp32 cast into the MoE append kernel (3 kernels -> 1) (#28658)

### [669b4bc](https://github.com/sgl-project/sglang/commit/669b4bc72b052ec9389b34fe755b237c9795ae1d)

- **作者**: YC Yen-Ching Tseng
- **时间**: 2026-07-08T07:41:21Z
- **提交信息**: [AMD] Gate stage-c on stage-b-test-1-gpu-large-amd (#30496)

---

<a id="vipshop-cache-dit"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [vipshop/cache-dit](https://github.com/vipshop/cache-dit)

## 仓库信息

- **描述**: A PyTorch-native inference engine with cache, parallelism, quantization and cpu offload for DiTs.
- **语言**: Python
- **星标数**: 1222
- **最后更新**: 2026-07-08T09:49:59Z

## 提交统计

- **昨日提交总数**: 1
- **提交者数量**: 1
- **主要提交者**: DefTruth

## AI分析总结

根据您提供的仓库 `vipshop/cache-dit` 的 README 摘要和提交记录，以下是昨日更新的分析与总结：

---

### 1. 主要更新类型
- **性能优化 / 功能改进**（针对低比特量化推理的硬件适配）

### 2. 关键变更点及其与项目整体方向的关系
- **变更内容**：将 `svdq linear` 层的输入/输出维度填充（pad）为 128 的倍数，以支持 w4a4（权重和激活均为 4-bit）量化模式。
- **与项目方向的关系**：项目核心目标是构建一个**高性能、支持量化和缓存**的 DiT（Diffusion Transformers）推理引擎。本次提交直接服务于**4-bit 量化后线性层的计算效率**，通过内存对齐优化来适配底层硬件（如 GPU Tensor Core 或 CPU SIMD 指令集）的访存与计算要求。

### 3. 对项目的影响和潜在意义
- **影响**：提升 w4a4 量化模式下 `svdq` 线性层的推理速度，减少因非对齐访存导致的额外开销。
- **潜在意义**：
  - 使项目在低比特量化场景下具备更强的实用性和竞争力，符合“推理引擎”的定位。
  - 为后续支持更多量化位宽（如 w4a8、w8a8）或其他矩阵运算（如注意力机制）的 padding 对齐策略提供参考。

### 4. 值得关注的技术点
- **SVQD 线性层**：可能是项目自定义的**尺度向量量化（Scale-Vector Quantization?）** 线性层实现，用于 4-bit 原始精度计算。
- **padding 到 128 倍数**：常见于**NVIDIA Tensor Core 对 w4a4 矩阵乘法的对齐约束**（例如 cuBLAS 或 CUTLASS 中要求 M/N/K 为 16/32/128 的倍数），或**CPU AVX-512 位宽**（512-bit = 64 bytes，128 的倍数对应 128 元素 × 4-bit = 64 bytes，恰好对齐缓存行？）。
- **仅修改单一文件**：推测该 padding 逻辑被封装在 `svdq` 模块内部，不影响用户接口。

### 5. 对项目发展的影响（结合 README 背景）
- README 强调项目是 **PyTorch-native 引擎**，且具备**量化、并行化、CPU 卸载**等特性。本次提交强化了**量化**维度的硬件适配，使项目能更好地在**低比特（4-bit）** 场景下发挥性能优势，吸引对显存/内存敏感的社区用户（如在边缘设备或大模型部署中）。
- 该 commit 未涉及文档或用户接口变更，属于内部实现优化，但能**间接提升项目发布的 PyPI 版本（v0.x）的推理效率**，有利于拉新与留存。

---

**总结**：昨日更新聚焦于 w4a4 量化下线性层的内存对齐优化，是一项典型的性能增强型 commit，巩固了项目在低比特推理领域的工程化能力。

## 详细提交记录

### [d74b89b](https://github.com/vipshop/cache-dit/commit/d74b89bf619145e275a619ebca5942315650dd1a)

- **作者**: DefTruth
- **时间**: 2026-07-08T09:49:55Z
- **提交信息**: w4a4: pad svdq linear to multiple of 128 (#1084)

* w4a4: pad svdq linear to multiple of 128

* w4a4: pad svdq linear to multiple of 128

* w4a4: pad svdq linear to multiple of 128

---

<a id="vllm-project-vllm"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [vllm-project/vllm](https://github.com/vllm-project/vllm)

## 仓库信息

- **描述**: A high-throughput and memory-efficient inference and serving engine for LLMs
- **语言**: Python
- **星标数**: 85733
- **最后更新**: 2026-07-08T23:15:37Z

## 提交统计

- **昨日提交总数**: 37
- **提交者数量**: 30
- **主要提交者**: djramic, rasmith, Nick Hill

## AI分析总结

分析生成失败

## 详细提交记录

### [56da398](https://github.com/vllm-project/vllm/commit/56da398dac3d86de643f7c12b2bdf68e4cec6d33)

- **作者**: Harry Mellor
- **时间**: 2026-07-08T23:14:33Z
- **提交信息**: Fix embed scaling + CUDA graphs in Transformers modelling backend (#48010)

Signed-off-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [2683194](https://github.com/vllm-project/vllm/commit/26831949b48a0d81fba379dcaf7e378206fd9087)

- **作者**: Andreas Karatzas
- **时间**: 2026-07-08T22:59:50Z
- **提交信息**: [ROCm] Fix pooling startup workspace lock (#47912)

Signed-off-by: Andreas Karatzas <akaratza@amd.com>

### [6cf7b26](https://github.com/vllm-project/vllm/commit/6cf7b26bd4bff60bf378e1af14044280ac0d214c)

- **作者**: Martin Hickey
- **时间**: 2026-07-08T22:47:22Z
- **提交信息**: [docs] Fix the docs build (#48008)

Signed-off-by: Martin Hickey <martin.hickey@ie.ibm.com>
Co-authored-by: Harry Mellor <19981378+hmellor@users.noreply.github.com>

### [5f85975](https://github.com/vllm-project/vllm/commit/5f8597562467d3b0495e300ebd902ba1aa781914)

- **作者**: Roberto L. Castro
- **时间**: 2026-07-08T22:11:28Z
- **提交信息**: [Feat] Add runtime monitor for post-warmup TileLang compilation (#46718)

Signed-off-by: LopezCastroRoberto <rocastro@redhat.com>
Signed-off-by: Roberto L. Castro <38211239+LopezCastroRoberto@users.noreply.github.com>

### [dcdd756](https://github.com/vllm-project/vllm/commit/dcdd756d75a9a2cdc9ff257c7d44c67b9b9fee68)

- **作者**: Tyler Michael Smith
- **时间**: 2026-07-08T21:59:48Z
- **提交信息**: [CI] GSM8K eval integration test for KV offloading (#46893)

Signed-off-by: Tyler Michael Smith <tyler@tylermsmith.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Signed-off-by: Itay Etelis <itay.etelis@ibm.com>
Signed-off-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Signed-off-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: Claude Opus 4.6 (1M context) <noreply@anthropic.com>
Co-authored-by: Itay Etelis <92247226+Etelis@users.noreply.github.com>
Co-authored-by: Itay Etelis <itay.etelis@ibm.com>
Co-authored-by: Or Ozeri <oro@il.ibm.com>
Co-authored-by: mergify[bot] <37929162+mergify[bot]@users.noreply.github.com>

### [0d2f4e7](https://github.com/vllm-project/vllm/commit/0d2f4e7c9c88d27fdfbb46dc4e2458d615102cb5)

- **作者**: Thien Tran
- **时间**: 2026-07-08T21:58:39Z
- **提交信息**: Allow FlashInfer A2A backends for TRTLLM FP8 MoE Modular (#46661)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [49abada](https://github.com/vllm-project/vllm/commit/49abadaedba2d88c6f35216ebef235edac8c1e82)

- **作者**: djramic
- **时间**: 2026-07-08T21:58:36Z
- **提交信息**: [ROCm][Bugfix] Fix empty-tensor .max() crash in AITER FA (#47894)

Signed-off-by: Djordje Ramic <djoramic@amd.com>

### [089e412](https://github.com/vllm-project/vllm/commit/089e41287824763fc2024c715f2e2c5b4276f8e3)

- **作者**: Kaihang Jiang
- **时间**: 2026-07-08T21:36:14Z
- **提交信息**: [Perf] Integrate TRTLLM BF16 MoE Modular Kernel  (#45182)

Signed-off-by: Kaihang Jiang <kaihangj@login-lyris02.lyris.clusters.nvidia.com>

### [a5d19cb](https://github.com/vllm-project/vllm/commit/a5d19cbb95872c4b426c06735733568542fa33db)

- **作者**: Nick Hill
- **时间**: 2026-07-08T18:30:11Z
- **提交信息**: [Core] Move MRV1 `late_interaction_runner.py` out of MRV2 subtree (#48014)

Signed-off-by: Nick Hill <nickhill123@gmail.com>

### [8347c6e](https://github.com/vllm-project/vllm/commit/8347c6e6e18abae2e9bfb97001720b4ca1a75c22)

- **作者**: Chris Leonard
- **时间**: 2026-07-08T17:56:29Z
- **提交信息**: updated flash_attn GIT_TAG to point to torch Stable ABI FA3 commit (#47995)

Signed-off-by: Chris Leonard <chleonar@redhat.com>

### [b2cf70e](https://github.com/vllm-project/vllm/commit/b2cf70ea3a29870ab720dd3162cadec3d79a63fe)

- **作者**: Ilya Markov
- **时间**: 2026-07-08T17:00:56Z
- **提交信息**: [CI] BugFix Eval Small Models Distributed test for DiffusionGemma (#47980)

Signed-off-by: Markov Ilya <markovilya19@gmail.com>
Co-authored-by: Markov Ilya <markovilya19@gmail.com>

### [d1f1d86](https://github.com/vllm-project/vllm/commit/d1f1d86797ad2f4cccfe441451ba320583c87cd2)

- **作者**: almayne
- **时间**: 2026-07-08T16:19:26Z
- **提交信息**: [Bugfix] Re-enable benchmarking of librispeech dataset. (#47033)

Signed-off-by: Anna Mayne <anna.mayne@arm.com>

### [f05603f](https://github.com/vllm-project/vllm/commit/f05603fa287ab020acc5faafd49c5decf0762533)

- **作者**: shawn
- **时间**: 2026-07-08T15:41:26Z
- **提交信息**: [Bugfix][DCP] Cast LSE to fp32 in a2a combine to fix bf16 bitcast crash (#47801)

Signed-off-by: Shawn Tsai <shawnyht@gmail.com>

### [c2ecd0f](https://github.com/vllm-project/vllm/commit/c2ecd0f888228f6583ac56392b79cfbe3626ed5e)

- **作者**: Martin Vit
- **时间**: 2026-07-08T15:22:20Z
- **提交信息**: Fix FlashAttention MLA prefill V unpadding (#42642)

Signed-off-by: Martin Vit <martin@voipmonitor.org>
Signed-off-by: Matthew Bonanni <mbonanni@redhat.com>
Co-authored-by: Matthew Bonanni <mbonanni@redhat.com>

### [0d12618](https://github.com/vllm-project/vllm/commit/0d12618e98ff2d21d36081e0e9b4eb23573b6d38)

- **作者**: Michael Goin
- **时间**: 2026-07-08T15:12:45Z
- **提交信息**: [Spec Decode] Support hybrid (SWA + full attention) DFlash drafters (#47914)

Signed-off-by: mgoin <mgoin64@gmail.com>
Co-authored-by: Claude Opus 4.8 (1M context) <noreply@anthropic.com>

### [68b4a1d](https://github.com/vllm-project/vllm/commit/68b4a1d582818e67adc903bf1b8fc5a5447da2fa)

- **作者**: Tyler Michael Smith
- **时间**: 2026-07-08T13:07:44Z
- **提交信息**: Fix NVML capability lookup for visible devices (#47892)

Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>

### [572b25b](https://github.com/vllm-project/vllm/commit/572b25b03ea5893305d4b25a25150ef129717605)

- **作者**: Robert Shaw
- **时间**: 2026-07-08T13:05:03Z
- **提交信息**: [Bug] Fix Batched DeepGEMM (#47884)

Signed-off-by: Robert Shaw <robertgshaw2-redhat@dgx-b200-02.mgmt.accl-001.lab.rdu2.dc.redhat.com>
Co-authored-by: Robert Shaw <robertgshaw2-redhat@dgx-b200-02.mgmt.accl-001.lab.rdu2.dc.redhat.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [9f2b3b0](https://github.com/vllm-project/vllm/commit/9f2b3b093cf5f1ce5af8081f72294e0846139801)

- **作者**: Vivek Sharma
- **时间**: 2026-07-08T13:01:14Z
- **提交信息**: Improvement of Docker image build for IBM Power using prebuilt wheels from IBM published devpi index (#46017)

Signed-off-by: vivek sharma <vivsharm@redhat.com>
Signed-off-by: puneetsharma21 <puneet.sharma21@ibm.com>
Signed-off-by: Puneet Sharma <puneet.sharma21@ibm.com>
Co-authored-by: vivek sharma <vivsharm@redhat.com>
Co-authored-by: Puneet Sharma <puneet.sharma21@ibm.com>
Co-authored-by: depthfirst-app[bot] <184448029+depthfirst-app[bot]@users.noreply.github.com>

### [cd0de48](https://github.com/vllm-project/vllm/commit/cd0de48d0883ecb8e1ef350a99baa0c158f58e82)

- **作者**: Saddss
- **时间**: 2026-07-08T12:34:19Z
- **提交信息**: [Bugfix][V1] Free out-of-window blocks on the processed-token basis under async scheduling (#47728)

Signed-off-by: Saddss <28726669061@qq.com>
Signed-off-by: Nick Hill <nickhill123@gmail.com>
Signed-off-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Yifan Qiao <yifanqiao@inferact.ai>
Co-authored-by: Saddss <28726669061@qq.com>
Co-authored-by: Nick Hill <nickhill123@gmail.com>

### [934eeae](https://github.com/vllm-project/vllm/commit/934eeaecfb13c4e5d5aa5a4a420cff35f5bd9821)

- **作者**: rasmith
- **时间**: 2026-07-08T12:12:54Z
- **提交信息**: [CI/Build][BugFix][The Rock] Fix get_ssm_device_name to return sanitized, usable filename (#47781)

Signed-off-by: Randall Smith <Randall.Smith@amd.com>

### [2cae98d](https://github.com/vllm-project/vllm/commit/2cae98dfa59bc58d939f526465ff025670d002f0)

- **作者**: Bugen Zhao
- **时间**: 2026-07-08T11:57:04Z
- **提交信息**: [Rust Frontend] Handle `continue_final_message` with renderer sentinel (#47844)

Signed-off-by: Bugen Zhao <i@bugenzhao.com>

### [db39d60](https://github.com/vllm-project/vllm/commit/db39d60010f8c72580dacd26bbaa3c2f72307cd9)

- **作者**: vanshbhatia-amd
- **时间**: 2026-07-08T11:41:26Z
- **提交信息**: Add tuned selective_state_update float32 config for AMD Instinct MI355 (#47943)

Signed-off-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>
Co-authored-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>

### [a1ab51a](https://github.com/vllm-project/vllm/commit/a1ab51afb61e8120d0f36a730eac45969ea81503)

- **作者**: aoright
- **时间**: 2026-07-08T11:25:53Z
- **提交信息**: [Bugfix] Allocate HY V3 expert_bias in float32 to prevent silent downcasting (#47797)

Signed-off-by: 辰言 <oncwnuIWp30GguOyJ615Fqj8H-yc@git.weixin.qq.com>
Signed-off-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: 辰言 <oncwnuIWp30GguOyJ615Fqj8H-yc@git.weixin.qq.com>
Co-authored-by: Jee Jee Li <jeejeelee@inferact.ai>
Co-authored-by: Jee Jee Li <pandaleefree@gmail.com>

### [e7b3853](https://github.com/vllm-project/vllm/commit/e7b3853bac9de3d0b6fd35619f5ca1dc32853e07)

- **作者**: Thien Tran
- **时间**: 2026-07-08T11:19:10Z
- **提交信息**: Remove router weight upcast for DSv2-related models (#47970)

Signed-off-by: Thien Tran <gau.nernst@yahoo.com.sg>

### [eeaf231](https://github.com/vllm-project/vllm/commit/eeaf23107fce233d38f4f8f9f031619054ef57ca)

- **作者**: vanshbhatia-amd
- **时间**: 2026-07-08T11:09:02Z
- **提交信息**: [ROCm] Add tuned selective_state_update float32 config for AMD Instinct MI300X (#47947)

Signed-off-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>
Co-authored-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>

### [285c08c](https://github.com/vllm-project/vllm/commit/285c08c036880d404e35b175008934a6aeeb4832)

- **作者**: Canlin Guo
- **时间**: 2026-07-08T11:05:45Z
- **提交信息**: [Model] Support MOSS-Transcribe-Diarize (#47729)

Signed-off-by: gcanlin <canlinguosdu@gmail.com>

### [1f4ad05](https://github.com/vllm-project/vllm/commit/1f4ad059d156654fd2b85cde18ddf134a07ae9b3)

- **作者**: vanshbhatia-amd
- **时间**: 2026-07-08T11:03:58Z
- **提交信息**: [ROCm] Add tuned selective_state_update float16 config for AMD Instinct MI300X (#47945)

Signed-off-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>
Co-authored-by: vanshbhatia-amd <210711135+vanshbhatia-amd@users.noreply.github.com>

### [04a703e](https://github.com/vllm-project/vllm/commit/04a703e397a310d397bb15cc4d15365312782ff3)

- **作者**: sungbin1015
- **时间**: 2026-07-08T09:51:17Z
- **提交信息**: [Frontend] Support bad_words in the /v1/completions endpoint (#46793)

Signed-off-by: sungbin1015 <sbin@solbox.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [bd3bb4e](https://github.com/vllm-project/vllm/commit/bd3bb4eb2635dc93749ef22c2558b98fa0519823)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-08T09:43:34Z
- **提交信息**: [Misc][Docs]  Add human-readable integer support for more cli-args (#47608)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [4400025](https://github.com/vllm-project/vllm/commit/440002552e794d7a4770a270c1f532d30540bd2b)

- **作者**: Chaojun Zhang
- **时间**: 2026-07-08T09:23:06Z
- **提交信息**: [XPU] [Fusion passes] Disable fuse_rope_kvcache_cat_mla & qk_norm_rope_ fusion on XPU (#47962)

Signed-off-by: Chaojun Zhang <chaojun.zhang@intel.com>

### [99a8561](https://github.com/vllm-project/vllm/commit/99a85617bf4e65ef0ddd4241fa2d4b637fe5106a)

- **作者**: Tyler Michael Smith
- **时间**: 2026-07-08T08:46:03Z
- **提交信息**: [Test] Skip DeepEP MoE layer tests without P2P access (#47946)

Signed-off-by: Tyler Michael Smith <tyler@tylermsmith.com>
Signed-off-by: Tyler Michael Smith <tlrmchlsmth@gmail.com>
Co-authored-by: Claude <noreply@anthropic.com>

### [7c67da9](https://github.com/vllm-project/vllm/commit/7c67da967f5f9a744fc5f6260918523fc4777417)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-08T08:18:03Z
- **提交信息**: Remove unused _get_kv_cache_config_deepseek_v4 alias (#47969)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [d79855e](https://github.com/vllm-project/vllm/commit/d79855eaacfd284689fe4ff6eefc280e1bb2473c)

- **作者**: Nicolò Lucchesi
- **时间**: 2026-07-08T08:17:46Z
- **提交信息**: [Docs] `kv_sharing_fast_prefill` correction (#47044)

Signed-off-by: NickLucche <nicolo.lucchesi@mistral.ai>

### [51e5372](https://github.com/vllm-project/vllm/commit/51e5372f3d8b2eb8cf96e20120af4de78b924fba)

- **作者**: manayang
- **时间**: 2026-07-08T07:58:23Z
- **提交信息**: [Model][HunyuanVL] Use native transformers processor and adapt to transformers 5.13 (#47872)

Co-authored-by: manayang <manayang@tencent.com>

### [7cc2e8e](https://github.com/vllm-project/vllm/commit/7cc2e8e74fa06401b7cb060950f4b682be641e09)

- **作者**: Ace Eldeib
- **时间**: 2026-07-08T07:36:30Z
- **提交信息**: fix: hash speculative draft model config (#47911)

Signed-off-by: Ace Eldeib <aeldeib@coreweave.com>
Signed-off-by: Ace Eldeib <alexeldeib@gmail.com>

### [2c64b4c](https://github.com/vllm-project/vllm/commit/2c64b4c1cc18bc25ff98f1835993d7545a8b394c)

- **作者**: Hongxia Yang
- **时间**: 2026-07-08T07:26:17Z
- **提交信息**: [ROCm] fixed aiter master flag and expert parallelism compatibility on minimax-m3-mxfp8 (#47158)

Signed-off-by: Hongxia Yang <hongxia.yang@amd.com>

### [d35eba3](https://github.com/vllm-project/vllm/commit/d35eba302f7c4c7c995a2b0ef172d5171d4de13d)

- **作者**: Muhammad Fawaz
- **时间**: 2026-07-08T07:00:59Z
- **提交信息**: [Bugfix] Avoid leaking Pydantic repr in tool_choice error message (#47028)

Signed-off-by: muhammadfawaz1 <135441198+muhammadfawaz1@users.noreply.github.com>
Co-authored-by: Mahad Durrani <114791389+mahadrehmann@users.noreply.github.com>

---

<a id="vllm-project-vllm-omni"></a>


**报告日期**: 2026-07-09
**监控日期**: 2026-07-08
**仓库地址**: [vllm-project/vllm-omni](https://github.com/vllm-project/vllm-omni)

## 仓库信息

- **描述**: A framework for efficient model inference with omni-modality models
- **语言**: Python
- **星标数**: 5484
- **最后更新**: 2026-07-08T21:47:40Z

## 提交统计

- **昨日提交总数**: 6
- **提交者数量**: 4
- **主要提交者**: amy-why-3459, Yueqian Lin, Alex Brooks

## AI分析总结

好的，以下是对仓库 `vllm-project/vllm-omni` 昨日提交记录的分析总结，结合项目“易用、快速、廉价的全模态模型服务”的背景进行解读。

---

### 1. 主要更新类型

- **性能优化**：2 项（针对 Qwen3-TTS）
- **Bug 修复**：3 项（含 1 项核心/通用机制，2 项针对 Qwen3-TTS、Voxtral TTS）
- **文档更新**：1 项（针对 MiniCPM-o 4.5）

---

### 2. 关键变更点及其与项目方向的关系

| 提交 | 关键变更 | 与项目方向的关系 |
|------|----------|------------------|
| 3a64da1 | Qwen3-TTS: 移除默认 seed 以恢复**批量 MTP 采样** | 提升 TTS 推理吞吐，符合“快速/廉价”目标 |
| 6d50348 | Qwen3-TTS: 跳过每步隐藏状态的 D2H 传输（通过 hidden pooler payload 选择退出） | 减少设备-主机间数据拷贝，降低延迟，优化性能 |
| da15a4c | Qwen3-TTS: 从 `min_tokens` 掩码中剔除**词表外停止 ID**，修复引擎崩溃 | 消除 TTS 服务中的崩溃 bug，提升稳定性，保障“易用” |
| 267b49b | Voxtral TTS: 修复反馈逻辑与短 ASR 检查 | 增强另一 TTS 模型的正确性与鲁棒性，扩展多模态覆盖 |
| b7d08fe | **核心/Bugfix**: 新增**端点拒绝机制**（Endpoint Rejection） | 提升服务器安全性与可控性，适用于生产部署 |
| 7d4decc | 文档: 修复 MiniCPM-o 4.5 的 curl TTS 示例，澄清 `chat_template_kwargs` | 降低用户上手门槛，改善文档体验，促进社区采用 |

---

### 3. 对项目的影响和潜在意义

- **性能提升**：Qwen3-TTS 的批量 MTP 采样恢复和隐藏状态传输优化，可显著提高单

## 详细提交记录

### [3a64da1](https://github.com/vllm-project/vllm-omni/commit/3a64da194c0a0b3af7448bc6b09aede36cc270eb)

- **作者**: Yueqian Lin
- **时间**: 2026-07-08T19:25:18Z
- **提交信息**: [Perf][Qwen3-TTS] Drop default seed from qwen3_tts.yaml to restore batched MTP sampling (#4970)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [6d50348](https://github.com/vllm-project/vllm-omni/commit/6d50348ef19444f06cd1293f8afa235c385f2b0f)

- **作者**: Yueqian Lin
- **时间**: 2026-07-08T18:59:41Z
- **提交信息**: [Perf][Qwen3-TTS] Skip per-step hidden-state D2H via hidden pooler payload opt-out (#4879)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [da15a4c](https://github.com/vllm-project/vllm-omni/commit/da15a4cb1cfeae3ca02bc075bbe64fe64de59820)

- **作者**: Yueqian Lin
- **时间**: 2026-07-08T18:24:31Z
- **提交信息**: [Bugfix] Drop out-of-vocabulary stop ids from min-tokens masking (qwen3-tts min_tokens engine crash) (#4971)

Signed-off-by: Yueqian Lin <linyueqian@outlook.com>

### [267b49b](https://github.com/vllm-project/vllm-omni/commit/267b49b88001e17204515e7483d168caea482fd0)

- **作者**: leo
- **时间**: 2026-07-08T16:52:48Z
- **提交信息**: Fix Voxtral TTS feedback and short ASR checks (#4954)

Signed-off-by: leo <yaoliu548926@gmail.com>

### [b7d08fe](https://github.com/vllm-project/vllm-omni/commit/b7d08fe5f6b1306eee44172c6589e3225de6897e)

- **作者**: Alex Brooks
- **时间**: 2026-07-08T15:00:47Z
- **提交信息**: [Core / Bugfix] Add Mechanism for Endpoint Rejection (#4762)

Signed-off-by: Alex Brooks <albrooks@redhat.com>

### [7d4decc](https://github.com/vllm-project/vllm-omni/commit/7d4decc1d826076337438987ba11801d5e3b1699)

- **作者**: amy-why-3459
- **时间**: 2026-07-08T09:45:02Z
- **提交信息**: docs(recipe): fix MiniCPM-o 4.5 curl TTS example and clarify chat_template_kwargs usage (#4950)

Signed-off-by: amy-why-3459 <wuhaiyan17@huawei.com>

---
